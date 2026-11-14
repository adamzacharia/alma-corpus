# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...693A.190J\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...693A.190J",
 "title": "ALMA Lensing Cluster Survey: Dust mass measurements as a function of redshift, stellar mass, and star formation rate from z = 1 to z = 5",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Jolly, Jean-Baptiste",
 "n_authors": 17,
 "arxiv_id": "2411.11212",
 "doi": "10.1051/0004-6361/202346239",
 "alma_projects_linked_by_archive": [
  "2013.1.00999.S",
  "2015.1.01425.S",
  "2018.1.00035.L"
 ]
}
```

Paper text:
<paper>
# ALMA Lensing Cluster Survey: Dust mass measurements as a function of redshift, stellar-mass and star formation rate, from $z=1$ to $z=5$

Understanding the dust content of galaxies, its evolution with redshift and its relationship to stars and star formation is fundamental for our understanding of galaxy evolution. Dust acts as both a catalyst of star formation and as a shield for star light. State-of-the-art millimeter ground-based facilities like ALMA have made dust observation ever more accessible, even at high redshift. However dust emission is typically very faint, making the use of stacking techniques instrumental in the study of dust in statistically sound samples.

Using the ALMA Lensing Cluster Survey (ALCS) wide-area band-6 continuum dataset ($\sim\,$110 arcmin$^2$ across 33 lensing clusters), we aimed at constraining the dust mass evolution with redshift, stellar mass and star formation rate (SFR).

After binning sources according to redshift, SFR and stellar mass –extracted from an HST-IRAC catalog– we performed a set of continuum stacking analyses in the image domain using LINESTACKER on sources between $z=1$ and $z=5$, further improving the depth of our data. The large field of view provided by the ALCS allows us to reach a final sample of $\sim4000$ galaxies with known coordinates and SED-derived physical parameters. We stack sources with SFR between $10^{-3}$ and $10^{3}$ M$_\odot$ per year, and stellar mass between $10^{8}$ and $10^{12}$ M$_\odot$, splitting them in different stellar mass and SFR bins. Through stacking we retrieve the continuum 1.2 mm flux, a known dust mass tracer, allowing us to derive the dust mass evolution with redshift and its relation with SFR and stellar mass.

We observe clear continuum detections in the majority of the subsamples. From the non detections we derive 3-$\sigma$ upper limits. We observe a steady decline in the average dust mass with redshift. Moreover, sources with higher stellar mass or SFR have higher dust mass on average, allowing us to derive scaling relations. Our results are mostly in good agreement with models at $z\sim1$ – $3$, but indicate typically lower dust-mass than predicted at higher redshift.

# Introduction

Dust impacts both the direct evolution of galaxies as well as their observations in multiple ways. It is thought to be the main catalyst of H$_2$ formation (cite: Wakelam2017), one of the main components of the molecular clouds in the interstellar medium (ISM) and hence one of the principal drivers of star formation (cite: Scoville2013). In addition to the direct effect on the physical properties of galaxies, dust also plays a critical role in astrophysical observations. The dust grains attenuating the starlight are consequently heated, and in turn re-radiate the energy at longer wavelengths, this is the so-called dust-obscured star formation (cite: Casey2014; Hodge2020; Zavala2021). As a consequence, the light coming from star-forming regions is typically dominated by dust continuum emission. The relationship between dust mass and other physical characteristics of galaxies have been intensely studied, for example, by studying dust-to-gas (atomic and molecular) or dust-to-metal ratios (cite: Hunt2005; Draine2007; Engelbracht2008; Galametz2011; Magrini2011; Saintonge2013; Remy-Ruyer2014; Combes2018; Li2019; Shapley2020; Tacconi2020; Birkin2021; Popping2022; Popping2023), or dust mass versus star formation rate (SFR) (cite: DaCunha2010; Casey2012; Santini2014; Dudzeviciute2020; Dudzeviciute2021).

Recent studies have shown that the proportion of dust-obscured star formation has evolved with redshift (cite: Bouwens2020). It has been estimated to be a dominant fraction during the peak of the cosmic star formation history. However, it appears to have accounted for only $\sim$ 20% – 25% of the total star formation at redshift $z=6$ – $7$ (cite: Zavala2021). Similarly, the overall cosmic dust density has been evidenced to peak around $z\sim 1-2$ with a rapid decline at higher redshift (cite: Driver2018; Magnelli2020; Pozzi2020; Dudzeviciute2021). Furthermore, massive dust reservoirs have been detected in massive high-redshift galaxies (cite: Bertoldi2003; Valiante2009; Venemans2012; Watson2015; Laporte2017; Tamura2019; Tamura2023). While this is probably not the case for more typical, less massive high-redshift galaxies, it highlights the importance of studying the evolution of dust mass with redshift.

Millimeter or sub-millimeter emission has been proposed to be a tracer of dust mass (cite: Scoville2014; Scoville2016; Scoville2017), with the assumption that the emission is optically thin and measured far from the peak of the dust spectral energy distribution. The Atacama Large Millimeter/Submillimeter Array (ALMA) has become instrumental in the quest to study dust mass in lower-mass galaxies and its evolution in the mm and sub-mm bands. With large surveys and high-redshift single target observations becoming progressively more accessible (cite: Knudsen2016; Walter2016; Gonzalez-Lopez2017; Gonzalez-Lopez2020; Laporte2017; Bethermin2020; Aravena2020) the evolution of dust is studied in increasingly statistically sound samples.

However, observations of high-redshift galaxies are typically biased by construction towards the observation of the brightest sources (Malmquist bias). To draw a complete picture of dust evolution with redshift it is necessary to also study galaxies with lower intrinsic luminosities. Gravitational lensing can be used as a tool to enhance the signal from faint galaxies without the need for excessive integration time. Similarly, tools like stacking can statistically improve the signal-to-noise ratio (S/N) drastically when studying large samples. With the help of both gravitational lensing and stacking, it is hence possible to push the limit of observations toward sources with lower intrinsic dust luminosity.

In this paper we present the stacking analysis of 10386 gravitationally lensed galaxies from the ALMA Lensing Cluster Survey (ALCS) at $z>1$ (cluster and field sources at $z\lesssim1$ are studied in a separate paper: (cite: Guerrero). By binning galaxies by redshift, and further splitting them according to their stellar mass or SFR, we study the evolution of the dust mass with redshift, and its scaling relation with stellar mass and SFR. Besides, we also integrate the contribution from all galaxies –in each redshift bin– to assess the evolution of the cosmic dust density.

In Section [2](#sec:data) we describe the overall data set, the catalog and the different subsamples. In Section [3](#sec:method) we describe both the stacking method, performed using LINESTACKER (cite: Jolly2020), as well as the processes involved in the dust mass calculation. In Section [4](#sec:results) we present our results and discuss them in Section [5](#sec:discussion). Finally in Section [6](#sec:summary) we present a summary of this paper. In the appendix we show alternative stacking procedures as well as some extra details on the main analysis.

Throughout the paper, we assume a $\Lambda$CDM cosmology with $\Omega_m = 0.3$, $\Omega_\lambda = 0.7$ and $H_0=70$  km s$^{-1}$Mpc$^{-3}$. All magnitudes are quoted in the AB system, such that M$_{\mathrm{AB}}$ = 23.9-2.5 log$_{10}$ (S$_\nu$ \[$\mu$Jy\]).

# Data and sample

## ALCS

The ALMA Lensing Cluster Survey (ALCS) is a large ALMA program accepted in cycle 6 (Project ID: 2018.1.00035.L; PI: K. Kohno). It observed 33 lensing clusters in band 6 ($\lambda\sim1.2\,$mm), spanning $\sim$ 110 arcmin$^2$ (primary beam (PB) $>0.5$). The clusters are distributed as follow: 16 from RELICS (cite: Coe2019), 12 from CLASH (cite: Postman2012), and 5 from the Frontier Fields survey (cite: Lotz2017). Observations were carried out between December 2018 and December 2019 (cycles 6 and 7) in compact array configurations C43-1 and C43-2, in a double frequency window setup, observing both from 250.0 to 257.5 GHz and from 265.0 to 272.5 GHz, for a total bandwidth of 15 GHz. When available, the ALCS data were concatenated with existing ALMA data, notably the ALMA Frontier Fields Survey (Project ID: 2013.1.00999.S, PI: Bauer and Project ID; 2015.1.01425.S: PI: Bauer). The data were reduced and calibrated using the Common Astronomy Software Applications (cite: CASA) package version 5.4.0 for the 26 clusters observed in cycle 6 and v5.6.1 for the remaining clusters observed in cycle 7. Throughout this paper, we use natural-weighted, primary-beam-corrected, and *uv*-tapered continuum maps, with a tapering parameter of 2 arcsec (the full width at half maximum of the synthesized beam is 2 arcsec; with a corresponding pixel size of 0.16 arcsec). *uv*-tapered maps have been chosen over natural resolution maps to ensure beam-size homogeneity of the different images when stacking. The average RMS of the maps is $\sim63\, \mathrm{\mu}$Jy/beam, see Table [1](#tab:cluster_sources) for the detailed RMS of each map. Full description of the survey can be found in (cite: KohnoALCS).

## Source catalogue

We extracted the positions, redshifts, physical characteristics (SFRs and stellar masses) as well as lensing magnifications of galaxies at $1\leq z \leq 5$ from the HST-IRAC catalog presented in (cite: Kokorev2022). When available, spectroscopic redshifts are used in place of photometric redshifts. While the SFRs and stellar masses extracted from the (cite: Kokorev2022) catalog are not corrected for magnification, the SFRs and stellar masses presented in this paper are always the intrinsic ones, i.e. corrected for magnification.

From the full catalog we select only the sources that (the number of remaining sources is indicated in italic after each step): (i) have defined redshifts and magnifications, and are not tagged with bad photometry (bad_phot $\neq 1$) – *1888977* (ii) have redshift uncertainties ($|z_{160}-z_{840}|$) below 0.4 – *76728* (iii) have $10^8 \leq \mathrm{M}_* / \mathrm{M}_\odot \leq 10^{12}$ and $0.001 \leq \mathrm{SFR} / ( \mathrm{M}_\odot  / \mathrm{year}) \leq 10^3$ – *51355* (iv) have H-band magnitudes above 24, to avoid contamination from blue faint galaxies – *50983* (v) have associated PB values higher than 0.5 – *13403* (vi) have a $z<5$ – *12980* (vii) have a magnification factor below 100 – *12967* (viii) have a $z\geq 1$ – *4103*, as lower redshift sources as well as cluster sources were presented in a separate paper, (cite: Guerrero). In total, our full sample finally adds up to a total of 4103 sources. Table [1](#tab:cluster_sources) presents the distribution of sources in the 33 clusters observed in the ALCS as well as the RMS of each map.

Figure [1](#fig:distrib) shows the distributions of stellar mass, SFR, magnification and redshift in the final sample. Figure [2](#fig:dMS) shows the distance of each galaxy from the galaxy main sequence (MS) as a function of redshift – $\Delta({\mathrm{MS}}) = \mathrm{log}(\mathrm{SFR}_{\mathrm{MS}}) - \mathrm{log}(\mathrm{SFR})$ with $\mathrm{SFR}_{\mathrm{MS}}$ the expected SFR for a galaxy with the same stellar mass and on the MS (cite: Speagle2014), and SFR the actual SFR of the galaxy. The sample shows an over-density of quiescent galaxies (cite: Guerrero). To assess the impact of quiescent galaxies on the stack we also stacked every sample after first excluding galaxies with $\Delta$MS $<-0.5$, see Appendix.

![image](sfr_all.pdf) ![image](m_all.pdf) ![image](mag_all.pdf) ![image](z_all.pdf)

![](speagle_sSFR_scatter_ALCS.pdf)

To further evaluate the completeness and reliability of the sample we compare its stellar mass function (SMF) to the one derived in the COSMOS2020 sample (cite: Weaver2022; Weaver2023). To derive the SMF of our sample we count –for each cluster separately– the number of galaxies in a given redshift bin and divide by the corresponding volume, corrected for the mean magnification of the sources in the studied bin. The comparison is shown on Figure [3](#fig:SMF). The studied sample seems to present an over-density of sources at $z>4$, and an under-estimation of sources in the $2<z \leq3$ bin, especially at high-masses. This might be due to the miss-identification of low redshift sources as high-redshift ones, as also discussed in (cite: Guerrero). (cite: Kokorev2022) compared the spectroscopic redshifts, known for $\sim7000$ galaxies, to the photometric redshifts they derived: while $\sim80\%$ of the redshifts agree reasonably well, the remaining $\sim20\%$ present large to sometimes catastrophic ($\Delta z >3$) errors, mainly due to the confusion of the Lyman, Balmer, and 4000 $\AA$ breaks. In addition, an under-evaluation of the survey volume (coming from an over-evaluation of the corresponding magnification) might also artificially boost the source density. The potential impact of the derived SMF are further discussed in Section [5](#sec:discussion).

![](SMF_04_24.pdf)

|                   |                           |                |
|:------------------|:-------------------------:|:--------------:|
| Cluster name      | Number of stacked sources |    Maps RMS    |
|                   |                           | ($\mu$Jy/beam) |
| HFF clusters:     |                           |                |
| Abell2744         |            418            |       51       |
| Abell370          |            346            |       47       |
| AbellS1063        |            369            |       53       |
| MACSJ0416.1-2403  |            473            |       55       |
| MACSJ1149.5+2223  |            325            |       64       |
| CLASH clusters:   |                           |                |
| Abell209          |            74             |       63       |
| Abell383          |            63             |       61       |
| MACS0329.7-0211   |            62             |       71       |
| MACS0429.6-0253   |            37             |       92       |
| MACS1115.9+0129   |            51             |       63       |
| MACS1206.2-0847   |            127            |       53       |
| MACS1311.0-0310   |            38             |       62       |
| MACS1423.8+2404   |            101            |       65       |
| MACS1931.8-2635   |            80             |       56       |
| MACS2129.4-0741   |            116            |       47       |
| RXJ1347-1145      |            95             |       53       |
| RXJ2129.7+0005    |            31             |       40       |
| RELICS clusters:  |                           |                |
| Abell2163         |            11             |       50       |
| Abell2537         |            52             |       69       |
| Abell3192         |            91             |       73       |
| AbellS295         |            39             |       74       |
| ACTCLJ0102-49151  |            253            |       72       |
| MACSJ0035.4-2015  |            72             |       52       |
| MACSJ0159.8-0849  |            69             |       63       |
| MACSJ0257.1-2325  |            67             |       83       |
| MACSJ0417.5-1154  |            135            |       84       |
| MACSJ0553.4-3342  |            157            |       65       |
| PLCKG171.9-40.7   |            28             |       73       |
| RXCJ0032.1+1808   |            81             |       71       |
| RXCJ0600.1-2007   |            66             |       57       |
| RXCJ0949.8+1707   |            38             |       62       |
| RXCJ2211.7-0350   |            52             |       78       |
| SMACSJ0723.3-7327 |            86             |       66       |
|                   |        Total: 4103        |  Average: 63   |

: Number of stacked sources in each cluster, and maps RMS.

## Subsamples

To study the evolution of dust mass across redshift we separated the sources in four redshift bins: $1\leqslant z<2$, $2\leqslant z<3$, $3\leqslant z<4$ and $4\leqslant z<5$. We additionally split sources according to either their SFRs or stellar masses in the following bins: (i) SFR, (upper and lower limits in  M$_\odot$ yr$^{-1}$): $0.001\leqslant$ SFR $\leqslant1$, $1<$ SFR $\leqslant10$, $10<$ SFR $\leqslant50$, $50<$ SFR $\leqslant100$ and $100<$SFR $\leqslant1000$; (ii) stellar mass, (M$_*$, upper and lower limits in  M$_\odot$): $10^8\leqslant M_* \leqslant 10^9$, $10^9< M_* \leqslant\,10^{10}$, $10^{10}< M_* \leqslant 10^{11}$ and $10^{11}< M_* \leqslant 10^{12}$. The total number of sources in each subsample can be found on Table [\[tab:subsample_sources\]](#tab:subsample_sources). Further, the distribution of SFR and stellar mass in each subsample can be found in the appendix, on Figures [16](#fig:mass_subsample_hist) and [17](#fig:sfr_subsample_hist).

One should note that sources individually detected in the ALCS data are not excluded from the samples. We decided to discriminate solely on the properties mentioned above to derive average properties of the population, and, in that regard, the 1.2 mm continuum flux density of individual sources should not be a criterion of exclusion from our samples. To assess the impact of the 1.2 mm flux distribution in our samples, we perform median stacking as well as bootstrapping analyses, alongside the main mean-stacking analyses, see Sections [3.4](#sec:errors) and [4.2](#sec:median_stacking).

|  | $1\leqslant z<2$ | $2\leqslant z<3$ | $3\leqslant z<4$ | $4\leqslant z<5$ | Total |
|:---|:--:|:--:|:--:|:--:|:--:|
| 8$\leqslant$log($M_*$)$\leqslant$9 | 1004 | 521 | 432 | 375 | 2332 |
| 9\<log($M_*$)$\leqslant$10 | 508 | 295 | 309 | 256 | 1368 |
| 10\<log($M_*$)$\leqslant$11 | 154 | 43 | 84 | 60 | 341 |
| 11\<log($M_*$)$\leqslant$12 | 27 | 4 | 11 | 20 | 62 |
| 0.001$\leqslant$SFR$\leqslant$1 | 1046 | 441 | 306 | 250 | 2043 |
| 1\<SFR$\leqslant$10 | 529 | 377 | 455 | 394 | 1755 |
| 10\<SFR$\leqslant$50 | 113 | 43 | 67 | 58 | 281 |
| 50\<SFR$\leqslant$100 | 5 | 1 | 1 | 5 | 12 |
| 100\<SFR$\leqslant$1000 | \- | 1 | 7 | 4 | 12 |

# Methods

## Stacking

Stacking was done using LINESTACKER (cite: Jolly2020), in single channel mode (to perform continuum stacking), on *uv*-tapered images (see Section [2.1](#sec:ALCS)). Sources were stacked pixel to pixel using mean stacks without weights (median stacks are also performed, see Section [4.2](#sec:median_stacking)). Stacking was operated with stamp sizes of 9.76 $\times$ 9.76 arcsec$^2$ (61 $\times$ 61 pixels). Sources were spatially aligned using the position extracted from the (cite: Kokorev2022) catalog. Stacked flux in Jy was retrieved by integrating the continuum flux in a central circular region of the stack stamp, with a radius $R_{\rm integ}=2''$ (12.5 pixels), corresponding to the synthesized beam size, and dividing it by the beam size in pixel units.

To compute the RMS associated to each stacked cube a random set of source-free coordinates are drawn for each stacking position. An empty stack is then generated from the set of random coordinates (cite: Jolly2020) with the same characteristics as the normal stacks (i.e. stamp size and number of targets). This process is performed 1000 times for each subsample. The standard deviation across all stack stamps is then computed and used to derive the RMS associated to each stack cube.

When the flux in the central region of the stack stamp is lower than 3 times its associated RMS, a $3 \sigma$ upper limit is used in place of the integrated flux to compute $M_{\mathrm{dust}}$.

## Magnification corrections

The averaged 1.2 mm fluxes extracted from each stack maps are corrected for the mean magnification of sources in the stack subsample, the final flux is hence computed as: $F_{final} = \frac{F_{stack} }{\overline{\mu}}$, where $F_{final}$ is the final flux used to compute the dust mass (see Section [3.3](#sec:dust)), $F_{stack}$ is the flux obtained from the stacked map, and $\overline{\mu}$ is the average magnification of each source in the subsample. Alternatively, each source could be corrected for its magnification before stacking: $F_{final} = F_{\mathrm{corrected\ stack}}$, where $F_{\mathrm{corrected\ stack}}$ is the flux obtained from the stack of the individually magnification-corrected maps: $\mathrm{Map}_{\mathrm{stack}} = \sum_{i=1}^n \frac{\mathrm{Stamp}_{i}}{\mu_{i}}$, where $\mathrm{Map}_{\mathrm{stack}}$ is the stacked map obtained from individually magnification-corrected stamps (from which $F_{\mathrm{corrected\ stack}}$ is obtained), $n$ is the number of sources in the subsample, $\mathrm{Stamp}_{i}$ is the map-stamp associated to source $i$ and $\mu_i$ is the magnification associated to source $i$. The reason why we decided to correct for the average magnification of the sample after stacking is the following: the signal in each stack stamp consists of both the flux from the source, which is gravitationally magnified, and some noise, which is independent of the magnification. By correcting each stack stamp for its associated magnification, one corrects both the flux from the source and the foreground noise. The efficiency of stacking is based on the fact that the noise is random and approximately similar in every stack stamp. By down-scaling the noise in each stamp by a different number (unrelated to the noise properties), one might effectively reduce the efficiency and reliability of the stacking analysis. However, by correcting the final stack with the average magnification, the analysis would be biased toward high-magnification sources. Correcting each stamp individually pre-stacking should avoid this bias, we hence repeated our analysis with this correction method. The 1.2 mm fluxes derived in both cases are very consistent, with values overlapping within the error margins.

## Measuring $M_{\rm dust}$

To derive dust masses using the 1.2 mm continuum flux extracted from each stacking stamp, we use a single modified blackbody curve, under the approximation of an optically thin regime, following (cite: Kovacs2010) and (cite: Magnelli2020) we define $M_{\rm dust}$ as:

$$\begin{equation}
 \label{eq:dust}
    M_{\rm dust}=\frac{5.03 \times 10^{-31} ( S_{\nu_{\rm obs}} / f_{\mathrm{CMB}}) D_{\rm L}^2 }{(1+z)^4 B_{\nu_{\rm obs}}(T_{\rm obs})  \kappa_{\nu_0}}  \left(\frac{\nu_0}{\nu_{\rm rest}}\right)^{\beta},
\end{equation}$$

where $M_{\rm dust}$ is the dust mass in  M$_\odot$, $S_{\nu_{\rm obs}}$ is the flux at the observed frequency in Jy (and corrected for the average magnification, as explained in Section [3.2](#sec:magnif)), $\nu_{\rm obs}=\nu_{\rm rest}/(1+z)$ is the observed frequency, $f_{\mathrm{CMB}}$ is the correction factor to account for the cosmic microwave background (CMB, see details further in the text), $D_{\rm L}$ is the luminosity distance in meter at redshift $z$, $B_{\nu_{\rm obs}}(T_{\rm obs})$ is Planck’s blackbody function in Jy sr$^{-1}$ at the observed temperature $T_{\rm obs}$ ($T_{\rm obs}=T_{\rm rest}/(1+z)$), $\kappa_{\nu_0}$ is the photon cross section to mass ratio of dust in m$^2$ kg$^{-1}$ and $\beta$ is the dust emissivity index. $S_{\nu_{obs}}$ is obtained by integrating over a fixed circular region in the center of the stack stamp (see Section [3.1](#sec:stacking)).

Following (cite: Magnelli2020) and (cite: Pozzi2021) we decided to use a single cold component to account for the dust temperature, and used a mass weighted dust temperature of $T_{\rm rest}=25$ K. While the total dust in galaxies is thought to consist of a warmer ($20<T<60$ K) and a colder ($T<30$ K) component, studies of local galaxies have shown that the cold component is responsible for most of the dust budget (cite: Orellana2017) and for the majority of the Rayleigh-Jeans emission (cite: Shivaei2022). (cite: Scoville2014; Scoville2016; Scoville2017) argue that this approximation should still be valid in higher redshift galaxies. We decided to adopt $T_{\rm rest}=25$ K at all redshifts probed by our analyses, but one should note that dust masses go as $T^{-1}$, meaning that our dust mass results are effectively highly dependent on the estimated dust temperature, and that the masses derived in our analyses could be off by factors of a few if the assumed dust temperature is not correct (see Section [5](#sec:discussion)).

While choosing an evolving dust temperature with redshift could seem more appropriate, we decided to stick to a fixed value to allow easier comparison with similar previous studies. We used $\beta=1.8$, the Galactic dust emissivity index measurement from the *Planck* data (cite: Planck2011) which also correlates well with values observed in high-redshift galaxies (cite: Chapin2009; Magnelli2012a; Faisst2020). Theoretical studies predict values for $\beta$ ranging from 1.5 to 2.0 (cite: Draine2011), similarly observational studies such as (cite: Faisst2020) find $\beta$ values between 1.6 and 2.4 (with a median value of 2.0). The effect of $\beta$ is however less impactful than the choice of dust temperature and we find that choosing $\beta=1.5$ (or 2.0) would only modify our results by $\sim 9$% at $z=1.5$ and $\sim 15$% at $z=5.5$. We used $\kappa_{\nu_0}$=0.0431 m$^2$ kg$^{-1}$ with ${\nu_0}=352.6$ GHz (cite: Li2001; Magnelli2020). See Section [5](#sec:discussion) for a more complete discussion of the choice of parameters for the dust mass computation.

Following (cite: DaCunha2013) we corrected our flux measurements for the effect of CMB. First, we correct our dust temperature for the extra heating due to the CMB (cite: DaCunha2013). This effect is minor, as the dust temperature is only increased by $\sim 3\%$ at $z=6$ (the effect being even less important at lower redshift). Second, and most importantly, the CMB acts as a bright observing background, leading to an underestimation of the total flux. This is corrected by following Equation 18 of (cite: DaCunha2013). This effect is much more important, as it yields an upward measurement to our results ranging from $\sim1.03$ at $z\sim1$ to $\sim1.31$ at $z\sim6$.

## Uncertainty computation

To compute the overall uncertainties associated to our measurements, we combined different sources of uncertainties. The first is the direct RMS from each stack analysis (computed from source-free stacks of each subsample, see Section [3.1](#sec:stacking)). In addition, in stacking analyses one should account for the intrinsic flux distribution of the sources in the sample. To do so, we perform a bootstrapping analysis for each subsample. In each subsample, the dust mass is re-computed 1000 times, each time with a different sample, randomized from the original subsample without replacement (see (cite: Jolly2020) for a detailed description of the bootstrapping routine included in LINESTACKER). The distribution of the dust masses computed in this manner are shown on Figures [18](#fig:boot_mass) and [19](#fig:boot_sfr), where we also show the dust mass obtained from the original subsample (black vertical line). The peaks and shapes of the distributions are overall consistent with the values derived from the original samples. However, one can note that the peak of the distributions are, in most of the subsamples, slightly lower than the original stacks. Similarly, some distributions present a faint tail toward higher dust masses. These 2 informations combined hint for a skewed distribution, which can be easily explained from the presence of individual detections in the samples. These effects are small however, and should be well represented by the associated uncertainties on dust mass measurements.

From the distributions derived from of each bootstrapping analyses we extract the 16$^{\mathrm{th}}$ to 84$^{\mathrm{th}}$ percentile (see Figures [18](#fig:boot_mass) and [19](#fig:boot_sfr)) that we sum quadratically with the stack RMS[^1]. In addition, given that the redshift is used multiple times in equation [\[eq:dust\]](#eq:dust), its 16$^{\mathrm{th}}$ to 84$^{\mathrm{th}}$ percentile in each subsample is used to propagate the associated uncertainty on the dust mass computation. Finally, following (cite: Sun2022) and (cite: Fujimoto2023) we use a magnification uncertainty of 20% of the magnification associated to each subsample, and propagate it to the aforementioned errors.

The $16^{\mathrm{th}}$ and $84^{\mathrm{th}}$ percentile of the (magnification corrected) SFRs and stellar masses in each subsample are used to compute the error associated to the SFRs and stellar masses.

The combination of these measurements uncertainties are used to plot the error bars on the different figures shown in this work. However, only the RMS associated to each cube is used to qualify a detection or an upper limit (as stated in section [3.1](#sec:stacking)).

# Results

## Mean stacking results, dust continuum detection

The standard deviation in stack stamps reaches levels as low as $\sim4.3 \times 10^{-3}$ mJy per beam, in the $z=1-2$ bin, of the lowest stellar mass and SFR subsamples (both containing $\sim1000$ sources). The total flux in the central circular aperture of 2 arcsec radius varies between $\sim1.78 \times 10^{-2}$ mJy and $\sim1.04$ mJy for stack detections (flux above 3 $\sigma$, not corrected for magnification). Securely extracted dust masses (with S/N above 3 $\sigma$) range from $\sim2.8 \times 10^6$ M$_{\odot}$ to $\sim2.56 \times 10^8$ M$_{\odot}$ (after magnification correction). Figures [7](#fig:stamps_mstar) and [8](#fig:stamps_sfr) show the stacked maps obtained for each of the subsamples, from which the results presented below are extracted.

![image](mdust_mass_z.pdf) ![image](z_evo.pdf)

![](z_evo_ratio.pdf)

![image](mdust_mass_z_sfr.pdf) ![image](z_evo_sfr.pdf)

The evolution of dust mass with stellar mass and redshift is shown on Figure [4](#fig:mdust_mstar), and tabulated on Table [\[tab:stack_res_mstar\]](#tab:stack_res_mstar). While detections in the lowest redshift bin ($1<z<2$) indicate a clear linear relationship between log(M$_{\mathrm{dust}}$) and log(M$_*$), the other redshift bins are less regular (see left panel of Figure [4](#fig:mdust_mstar)). When comparing to other works (cite: Santini2014; DaCunha2015; Kirkpatrick2017; Shivaei2022), our data points are typically below other measurements (individual detections and stacks). This behavior is however strongly reduced when excluding quiescent galaxies from the stacks (see Appendix), highlighting that quiescent galaxies might have lower dust masses at the same stellar mass.

The log($M_{\mathrm{dust}}$) – log(SFR) relation seems to follow a similar trend of increasing dust mass with increasing SFR, but with a clearer linear relation across redshift (though there is a higher number of non-detection, see left panel of Figure [6](#fig:mdust_sfr) and stacking results tabulated in Table [\[tab:stack_res_sfr\]](#tab:stack_res_sfr)). Hinting that SFR might be a better suited than stellar mass to trace the dust mass. When comparing to previous works (cite: Santini2014; DaCunha2015; Kirkpatrick2017; Shivaei2022) one can see that our measurements follow a similar trend as the one already observed, reaching however so far mostly unexplored regimes.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| \<$z$\> | log$($\<$|M_*|$\>$/M_\odot)$ | \<Dust Mass\> | Flux | RMS | \<$\mu$\>$^{(a)}$ |
|  |  | ( M$_\odot$) | (mJy) | (mJy) |  |
| $1.42$ | $8.48$ | \<$2.49\times10^{6}$ | – | $4.28\times10^{-3}$ | $3.43$ |
| $2.51$ | $8.53$ | \<$1.82\times10^{6}$ | – | $5.64\times10^{-3}$ | $5.41$ |
| $3.45$ | $8.54$ | \<$1.27\times10^{6}$ | – | $6.51\times10^{-3}$ | $7.83$ |
| $4.47$ | $8.56$ | \<$9.43\times10^{5}$ | – | $6.98\times10^{-3}$ | $10.55$ |
| $1.42$ | $9.43$ | $1.61\times10^{7}$ $\pm$ $4.33\times10^{6}$ | $7.84\times10^{-2}$ | $6.67\times10^{-3}$ | $3.24$ |
| $2.54$ | $9.39$ | $3.89\times10^{6}$ $\pm$ $2.54\times10^{6}$ | $2.54\times10^{-2}$ | $8.25\times10^{-3}$ | $3.78$ |
| $3.41$ | $9.41$ | $4.96\times10^{6}$ $\pm$ $2.61\times10^{6}$ | $4.49\times10^{-2}$ | $9.12\times10^{-3}$ | $4.64$ |
| $4.44$ | $9.42$ | \<$2.19\times10^{6}$ | – | $9.12\times10^{-3}$ | $5.95$ |
| $1.41$ | $10.42$ | $6.95\times10^{7}$ $\pm$ $1.84\times10^{7}$ | $0.28$ | $1.27\times10^{-2}$ | $2.67$ |
| $2.46$ | $10.33$ | $5.57\times10^{7}$ $\pm$ $1.78\times10^{7}$ | $0.3$ | $2.37\times10^{-2}$ | $3.16$ |
| $3.43$ | $10.35$ | $3.57\times10^{7}$ $\pm$ $1.32\times10^{7}$ | $0.33$ | $1.96\times10^{-2}$ | $4.71$ |
| $4.46$ | $10.37$ | $1.7\times10^{7}$ $\pm$ $1.01\times10^{7}$ | $0.2$ | $2.02\times10^{-2}$ | $5.67$ |
| $1.41$ | $11.2$ | $1.02\times10^{8}$ $\pm$ $4.17\times10^{7}$ | $0.39$ | $2.88\times10^{-2}$ | $2.53$ |
| $2.56$ | $11.22$ | \<$3.58\times10^{7}$ | – | $9.51\times10^{-2}$ | $4.6$ |
| $3.55$ | $11.38$ | \<$3.21\times10^{7}$ | – | $4.93\times10^{-2}$ | $2.33$ |
| $4.46$ | $11.39$ | $1.55\times10^{7}$ $\pm$ $1.11\times10^{7}$ | $0.16$ | $4.03\times10^{-2}$ | $4.87$ |

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| \<$z$\> | \<SFR\> | \<Dust Mass\> | Flux | RMS | \<$\mu$\> |
|  | ( M$_\odot$/ yr) | ( M$_\odot$) | (mJy) | (mJy) |  |
| $1.39$ | $0.15$ | $3.72\times10^{6}$ $\pm$ $1.82\times10^{6}$ | $1.95\times10^{-2}$ | $4.28\times10^{-3}$ | $3.51$ |
| $2.51$ | $0.81$ | \<$1.94\times10^{6}$ | – | $6.17\times10^{-3}$ | $5.55$ |
| $3.45$ | $0.99$ | \<$1.14\times10^{6}$ | – | $7.17\times10^{-3}$ | $9.62$ |
| $4.47$ | $0.53$ | \<$6.72\times10^{5}$ | – | $7.05\times10^{-3}$ | $14.94$ |
| $1.45$ | $2.84$ | $1.78\times10^{7}$ $\pm$ $4.96\times10^{6}$ | $8.13\times10^{-2}$ | $6.47\times10^{-3}$ | $3.04$ |
| $2.53$ | $1.79$ | \<$3.17\times10^{6}$ | – | $7.19\times10^{-3}$ | $3.95$ |
| $3.43$ | $2.16$ | $6.43\times10^{6}$ $\pm$ $2.94\times10^{6}$ | $5.51\times10^{-2}$ | $7.36\times10^{-3}$ | $4.38$ |
| $4.45$ | $4.68$ | \<$2.21\times10^{6}$ | – | $7.72\times10^{-3}$ | $4.97$ |
| $1.47$ | $24.56$ | $7.06\times10^{7}$ $\pm$ $1.83\times10^{7}$ | $0.26$ | $1.38\times10^{-2}$ | $2.5$ |
| $2.52$ | $19.66$ | $3.4\times10^{7}$ $\pm$ $1.23\times10^{7}$ | $0.2$ | $2.29\times10^{-2}$ | $3.49$ |
| $3.4$ | $31.67$ | $2.64\times10^{7}$ $\pm$ $1.05\times10^{7}$ | $0.22$ | $2.37\times10^{-2}$ | $4.23$ |
| $4.46$ | $10.55$ | $2.72\times10^{7}$ $\pm$ $1.78\times10^{7}$ | $0.19$ | $2.29\times10^{-2}$ | $3.4$ |
| $1.76$ | $86.71$ | $2.56\times10^{8}$ $\pm$ $1.26\times10^{8}$ | $1.04$ | $7.88\times10^{-2}$ | $2.64$ |
| $2.09$ | $60.65$ | $1.8\times10^{8}$ $\pm$ $4.46\times10^{7}$ | $0.65$ | $9.54\times10^{-2}$ | $2.25$ |
| $3.87$ | $81.75$ | \<$6.56\times10^{7}$ | – | $0.1$ | $2.35$ |
| $4.58$ | $53.34$ | \<$3.55\times10^{7}$ | – | $6.11\times10^{-2}$ | $2.45$ |
| $2.84$ | $1.33\times10^{2}$ | $2.54\times10^{8}$ $\pm$ $7.27\times10^{7}$ | $1.0$ | $0.2$ | $2.17$ |
| $3.5$ | $1.51\times10^{2}$ | \<$4.71\times10^{7}$ | – | $6.67\times10^{-2}$ | $2.16$ |
| $4.44$ | $3.52\times10^{2}$ | \<$4.89\times10^{7}$ | – | $0.1$ | $2.93$ |

When looking at the evolution of dust mass with redshift (see the right panels of Figures [4](#fig:mdust_mstar) and [6](#fig:mdust_sfr) and Figure [5](#fig:mdust_mstar_ratio)), one can see a relatively clear linear trend, indicating a decrease in dust mass with increasing redshift.

By fitting quadratic functions to the data shown on Figures [4](#fig:mdust_mstar) and [6](#fig:mdust_sfr), we derive scaling relations between: $M_{\mathrm{dust}}$ and $M_*$ at fixed $z$; $M_{\mathrm{dust}}$ and $z$ at fixed $M_*$; $M_{\mathrm{dust}}$ and SFR at fixed $z$; and $M_{\mathrm{dust}}$ and $z$ at fixed SFR. Fits are performed using detections only (ignoring upper limits), and only when the number of data points is $\geq 3$. The results from the fits are summarized in Table [\[tab:fit\]](#tab:fit), and plotted on Figures [14](#fig:mdust_mass_fit) and [15](#fig:mdust_sfr_fit)

|  |  |  |  |
|:---|:--:|:--:|:--:|
| $M_{\mathrm{dust}}$(SFR) (fixed $z$) |  |  |  |
| $z$ range | a | b | Range of applicability |
| $1\leq z<2$ | $7.2 \pm 1.2 \times 10^{6}$ | $7.8 \pm 0.7 \times 10^{-1}$ | $-1<$log(SFR)$<2$ |
| $2\leq z<3$ | $9.2 \pm 5.7 \times 10^{5}$ | $12.3 \pm 1.5 \times 10^{-1}$ | $1<$log(SFR)$<3$ |
| $M_{\mathrm{dust}}(z)$ (fixed SFR) |  |  |  |
| SFR range ($M_\odot$ per year) | a | b | Range of applicability |
| $10<\mathrm{SFR}<50$ | $10.5 \pm 1.6 \times 10^{7}$ | $-1.1 \pm 0.2$ | $1\leq z<5$ |
| $M_{\mathrm{dust}}(M_*)$ (fixed $z$) |  |  |  |
| $z$ range | a | b | Range of applicability |
| $1\leq z<2$ | $5.2 \pm 13.0 \times 10^{3}$ | $4.8 \pm 1.1 \times 10^{-1}$ | $8<$log(M$_*$/M$_\odot$)$<12$ |
| $M_{\mathrm{dust}}(z)$ (fixed $M_*$) |  |  |  |
| $M_*$ range ($M_\odot$) | a | b | Range of applicability |
| $10^9<\mathrm{M}_*<10^{10}$ | $3.0 \pm 1.3 \times 10^{7}$ | $-1.8 \pm 0.7$ | $1\leq z<4$ |
| $10^{10}<\mathrm{M}_*<10^{11}$ | $10.5 \pm 2.7 \times 10^{7}$ | $-1.0 \pm 0.3$ | $1\leq z<4$ |

![](stamps_plots_mstar.pdf)

![](stamps_plots_sfr.pdf)

## Median stacking analysis

To better assess the effect of the population distribution on the derived dust mass we also performed median-stacks, in the same way as the average stacks presented in Section [3.1](#sec:stacking). The overall median dust masses derived through our stacking analyses are systematically slightly lower than the mean dust masses (see Figure [9](#fig:stamps_median) for illustration and the appendix for detailed plots). While the median stellar mass and SFR of each subsample are also systematically lower than the mean (see Figures [16](#fig:mass_subsample_hist) and [17](#fig:sfr_subsample_hist)), the difference is not big enough to explain the offset dust mass observed between the mean and median stacks. This, again, hints to a possibly skewed distribution of dust mass in each subsample, resulting in offsets between mean and median dust masses. However, it should be however noted that the dust-mass trends observed in this analysis (with redshift, stellar mass and SFR) remain the same in the median stacking analyses.

![image](stamps_plots_mstar_median.pdf) ![image](stamps_plots_sfr_median.pdf)

# Discussion

As our analysis focuses on galaxies spanning a large redshift range, and our observation remains at a fixed observed wavelength, it is important to question the assumption made here; that the continuum flux traces the same physical process at a rest wavelength $\lambda_{\mathrm{rest}}\sim0.5$ mm (corresponding to $z\sim1$) and $\lambda_{\mathrm{rest}}\sim0.18$ mm (corresponding to $z\sim5$). More specifically, the validity of the dust mass equation (see Section [3.3](#sec:dust)) comes from the assumption that the dust is optically thin, and that the flux measurement probes the Rayleigh-Jeans dust emission –thus the part of the SED that is dominated by the emission of the dust at T=25K, that dominates the dust mass budget. This is true at long wavelengths, where we effectively probe the Rayleigh-Jeans tail of the dust emission (cite: Magdis2012; Scoville2016). However, the higher the redshift observed the closer one gets to the peak of dust emission, more sensitive to temperature and total luminosity. This could explain the low detection rate in the high-$z$ subsamples, even when the number of stack sources is high –and hence the corresponding RMS in the stack maps is low.

While numerous studies show an evolution of dust temperature with redshift, it is important to distinguish between the peak temperature, which is thought from both theoretical and observational works to increase with redshift (cite: Magdis2012; Magnelli2014; Bethermin2015; Ferrara2017; Narayanan2018; Schreiber2018; Liang2019; Ma2019; Sommovigo2020), and the mass-weighted temperature, probing the Rayleigh-Jeans tail, which can be directly used to measure the dust mass as stated above. Unlike the peak temperature, the mass-weighted temperature is thought to be mostly constant with redshift (cite: Scoville2016; Liang2019). It should be noted however, that the mass-weighted temperature still exhibits a small range in possible values, typically from 15 to 45 K (cite: Liang2019), and a small increase with redshift may exist. On the other hand, (cite: Dudzeviciute2020) argue that the previously observed evolution of the dust temperature is likely due to the luminosity evolution in the samples employed, and suggest a dust temperature of $30.4 \pm 0.3$, constant with redshift. In any event, to ease comparison with studies similar to ours and to limit complexity, we decided to keep a fixed temperature at all redshifts for dust mass computations. Consequently, one should note that using $T=40$ K (instead of 25) in dust masses computation would change our results by $\sim$ 50% in the highest redshift bin.

When comparing our results to the semi-analytical modeling from (cite: Popping2017; Shark; Vijayan2019; Triani2020)[^2] we can see an overall decent agreement in dust mass predictions as a function of stellar mass at $z\sim1$. However, all models but the one presented in (cite: Vijayan2019) predict an overall increase of dust mass with redshift while our analysis shows the opposite. In addition the dust mass derived in the high-mass end of our subsamples is typically smaller than predicted by the models (though this flattening might be due to the presence of quiescent galaxies in our sample, as shown in the appendix). In addition, one should note that the method used for computing the average dust mass in the SHARK model (cite: Shark) differs to the one used in this work. To highlight this difference we show, on Figures [10](#fig:mdust_mstar_simu) and [11](#fig:mdust_sfr_simu), both the average dust masses predicted by the SHARK model and the dust masses computed, using equation [\[eq:dust\]](#eq:dust), from the band 6 continuum (S6) predicted by SHARK. It is interesting to note that at $z\sim3$ and at $z\sim5$ the dust mass derived using the predicted S6 differs by almost one dex from the dust mass otherwise predicted. As mentioned above, this might be a direct consequence of the evolution of the rest-wavelength with redshift, moving observation closer to the peak of dust emission. Surprisingly however, our results seem in better agreement with the direct dust mass measurements compared to the ones obtained from S6.

As the analysis relies on photometric redshifts for a large fraction of the catalog, it is important to consider the potential impact this could have on the results. In particular, it should be noted that the bins at $z>3$ appear overpopulated. This can be seen on Figure [3](#fig:SMF), when comparing the SMF of our sample to the SMF of the COSMOS2020 sample (cite: Weaver2022; Weaver2023). As a consequence the dust content at $z>3$ is likely over-estimated. This is probably due to the miss-classification of some lower redshift sources to higher redshift, as suggested in (cite: Kokorev2022) and mentioned in Section [2.2](#sec:cat).

It should also be noted that, because the catalog used was generated using *HST* and *Spitzer* photometry, some of the most dusty galaxies may be missing, biasing the analysis toward lower averaged dust masses. Indeed, as pointed out in (cite: Kokorev2022), from the 180 sources individually detected with a SNR $>4$ in the ALCS data, only 145 are identified in their catalog, indicating that some of the most dusty galaxies may be missed from our analysis. This bias could be strongest in the high-redshift bins, where only the UV-brightest galaxies (i.e. typically less dust-obscured) might be observed. The use of James-Webb Space Telescope (JWST)-based catalogs could help to include more of the missed dusty galaxies, especially at high-$z$, and to improve the SED fitting routines.

![](mdust_mass_z_simu.pdf)

![](mdust_mass_z_sfr_models.pdf)

As shown in the appendix (Figures [12](#fig:mdust_mass_dMS) and [13](#fig:mdust_sfr_dMS)), the inclusion of quiescent galaxies in the stacks biases the analysis toward lower dust masses, especially in the samples split through stellar-mass. This highlights that some sources included in the high-mass subsamples have low SFR and also low dust masses. The higher average dust mass observed in the mass-selected samples when excluding sources with $\Delta\mathrm{MS}<-0.5$, and on the other hand, the relatively stable average dust mass in SFR selected samples, implies that SFR should be a better dust mass tracer. It shows in addition that quiescent galaxies will have a typically lower dust content than their star forming counterparts at similar stellar mass.

As in (cite: Magnelli2020), we use the dust opacities from (cite: Li2001) to derive the dust masses. Those values have been constrained from observations of the diffuse interstellar medium (ISM) and therefore these properties are representative for dust in the diffuse ISM. However, some studies in nearby galaxies (cite: galliano_interstellar_2018) showed that the opacity from (cite: Li2001) has perhaps been underestimated by a factor of $2-3$. One must emphasise that larger values of opacities in galaxies does not mean that the values of (cite: Li2001) are wrong. Their values have been constrained for the diffuse interstellar medium and are therefore well adapted for galaxies only if the bulk of dust emission emerges from the diffuse interstellar medium of galaxies. The underestimation of the dust opacity might indicate that the majority of the dust emission does not emerge from diffuse regions but from denser regions where dust grains are likely to be larger.

In dense regions of the ISM, dust grains grow through accretion and coagulation which triggers an increase in the dust opacity by a factor $2-3$ (cite: kohler_dust_2015). The underestimation of the dust opacities in some nearby galaxies could therefore mean that the bulk of the dust emission arises from dense regions where dust grains are larger than in the diffuse ISM. This seems to be also the case in high-redshift galaxies as (cite: Magnelli2020) claim that the bulk of the dust emission in their galaxy sample emerges from the molecular phase and therefore dense regions where dust differs from the diffuse ISM. They also stated that there could be a significant increase in the dust emissivity from diffuse to denser regions which can be explained in terms of grain growth (cite: kohler_dust_2015).

There is for now no consensus on the dust properties one must consider, neither in nearby nor in high-redshift galaxies. Moreover, dust grains are unlikely to be the same within galaxies and from one galaxy to another, which adds to the complexity. Although diffuse ISM-like dust grains might not be responsible for the majority of the dust emission in galaxies, these dust models have the advantage of being thoroughly developed and extensively used. We therefore use those dust properties from the diffuse ISM until we have more constraints on the dust grains responsible for the emission in these galaxies.

# Summary

We used deep ALMA band 6 data, over 33 lensing clusters, to perform a set of stacking analyses on a large sample of 4103 lensed sources, whose positions and physical parameters were extracted from the HST/IRAC catalog presented in (cite: Kokorev2022). Spanning redshifts from $z=1$ to $z=5$, SFRs from $0.001 \, \mathrm{M}_{\odot} \, \mathrm{yr}^{-1}$ to $1000 \, \mathrm{M}_{\odot}\,\mathrm{yr}^{-1}$ and stellar masses from $10^{8}\, \mathrm{M}_{\odot}$ to $10^{12}\, \mathrm{M}_{\odot}$. To study the evolution of the dust mass through cosmic time, we binned the sources in five different redshifts bins, and further also grouped sources according to their SFR and stellar mass, respectively. We performed continuum stacking on each of the subsamples using LINESTACKER (cite: Jolly2020).

Using the mean continuum stacked flux, we computed average dust masses. From the non detections we derive $3\sigma$ upper limits. Using both detections and upper limits we study the evolution trend of dust mass with redshift. We see clear indications for average dust mass diminution with redshift. Similarly we study the evolution of dust mass with stellar mass and SFR, in both cases we see a positive correlation. From our detections we derived relationships between dust mass and SFR or stellar mass in different redshift range. The results from our study are mostly consistent with results from modeling (at least at $z\sim1$) and from other similar studies. Our analysis allows us to probe regimes of stellar mass and SFR unexplored so far. The highest redshift bin shows mostly non-detections, and the corresponding upper limits indicate low average dust masses –even though the overall RMS is low– when compared to other studies. This could be due to the different rest-wavelength probed at high-$z$, lying closer to the peak of dust emission. Or to the tendency of individual high-$z$ dust measurements to be biased towards very dust-bright objects.

The linear trends observed between stellar mass and dust mass confirm that as galaxies evolve and form more stars, they also accumulate more dust. These dust grains play a vital role in catalyzing the formation of H$_2$, thus influencing the overall gas reservoir available for future star formation. Dust becomes an integral component of a self-perpetuating cycle, accumulating throughout the stars’ life cycle and subsequently bolstering the SFR. In addition the inverse trend observed between average dust-mass and redshift, implies that the build-up of dust in galaxies over cosmic-time is a gradual process, aligning with the overall evolution of the SFR density (cite: Magnelli2020). This further hints for a gradual increase of the average-metallicity in galaxies with cosmic time, as dust grains are known to be composed of heavy-elements produced in stars.

# Acknowledgements

The authors thank the anonymous reviewer for their thoughtful and constructive suggestions, which greatly helped improve this manuscript. This paper makes use of the ALMA data: ALMA #2018.1.00035.L, #2013.1.00999.S, and #2015.1.01425.S. ALMA is a partnership of the ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the ESO, AUI/NRAO, and NAOJ. JBJ thanks Ian Smail for the discussion. KK acknowledges support from the Swedish Research Council (2015-05580), and the Knut and Alice Wallenberg Foundation (KAW 2020.0081). K. Kohno acknowledges the JSPS KAKENHI Grant Number JP17H06130 and the NAOJ ALMA Scientific Research Grant Number 2017-06B. AG acknowledges funding from ANID-Chile NCN2023_002 and FONDECYT Regular 1171506. DE acknowledges support from a Beatriz Galindo senior fellowship (BG20/00224) from the Spanish Ministry of Science and Innovation, projects PID2020-114414GB-100 and PID2020-113689GB-I00 financed by MCIN/AEI/10.13039/501100011033, project P20_00334 financed by the Junta de Andalucía, project A-FQM-510-UGR20 of the FEDER/Junta de Andalucía-Consejería de Transformación Económica, Industria, Conocimiento y Universidades. FEB acknowledges support from ANID-Chile BASAL CATA FB210003, FONDECYT Regular 1200495 and 1190818, and Millennium Science Initiative Program – ICN12_009.

85 natexlab

(ref: Aravena2020) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, ApJ, 901, 79

(ref: Bertoldi2003) Bertoldi, F., Carilli, C. L., Cox, P., et al. 2003, A&A, 406, L55

(ref: Bethermin2015) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113

(ref: Bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: Birkin2021) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926

(ref: Bouwens2020) Bouwens, R., González-López, J., Aravena, M., et al. 2020, ApJ, 902, 112

(ref: Casey2012) Casey, C. M. 2012, MNRAS, 425, 3094

(ref: Casey2014) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Physics Reports, 541, 45–161

(ref: Chapin2009) Chapin, E. L., Pope, A., Scott, D., et al. 2009, MNRAS, 398, 1793

(ref: Coe2019) Coe, D., Salmon, B., Bradač, M., et al. 2019, ApJ, 884, 85

(ref: Combes2018) Combes, F. 2018, A&ARv, 26, 5

(ref: DaCunha2010) da Cunha, E., Eminian, C., Charlot, S., & Blaizot, J. 2010, MNRAS, 403, 1894

(ref: DaCunha2013) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: DaCunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110

(ref: Draine2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: Draine2007) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866

(ref: Driver2018) Driver, S. P., Andrews, S. K., da Cunha, E., et al. 2018, MNRAS, 475, 2891

(ref: Dudzeviciute2021) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2021, MNRAS, 500, 942

(ref: Dudzeviciute2020) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828

(ref: Engelbracht2008) Engelbracht, C. W., Rieke, G. H., Gordon, K. D., et al. 2008, ApJ, 678, 804

(ref: Faisst2020) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, 498, 4192

(ref: Ferrara2017) Ferrara, A., Hirashita, H., Ouchi, M., & Fujimoto, S. 2017, MNRAS, 471, 5018

(ref: Fujimoto2023) Fujimoto, S., Kohno, K., Ouchi, M., et al. 2023, arXiv e-prints, arXiv:2303.01658

(ref: Galametz2011) Galametz, M., Madden, S. C., Galliano, F., et al. 2011, A&A, 532, A56

(ref: galliano_interstellar_2018) Galliano, F., Galametz, M., & Jones, A. P. 2018, Annual Review of Astronomy and Astrophysics, 56, 673

(ref: Gonzalez-Lopez2017) González-López, J., Bauer, F. E., Romero-Cañizales, C., et al. 2017, A&A, 597, A41

(ref: Gonzalez-Lopez2020) González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91

(ref: Guerrero) Guerrero, A., Nagar, N., Kohno, K., et al. 2023, MNRAS, 526, 2423

(ref: Hodge2020) Hodge, J. A. & da Cunha, E. 2020, Royal Society Open Science, 7, 200556

(ref: Hunt2005) Hunt, L., Bianchi, S., & Maiolino, R. 2005, A&A, 434, 849

(ref: Jolly2020) Jolly, J.-B., Knudsen, K. K., & Stanley, F. 2020, MNRAS, 499, 3992

(ref: Kirkpatrick2017) Kirkpatrick, A., Pope, A., Sajina, A., et al. 2017, ApJ, 843, 71

(ref: Knudsen2016) Knudsen, K. K., Richard, J., Kneib, J.-P., et al. 2016, MNRAS, 462, L6

(ref: KohnoALCS) Kohno, K., Fujimoto, S., Tsujita, A., et al. 2023, arXiv e-prints, arXiv:2305.15126

(ref: Kokorev2022) Kokorev, V., Brammer, G., Fujimoto, S., et al. 2022, arXiv e-prints, arXiv:2207.07125

(ref: Kovacs2010) Kovács, A., Omont, A., Beelen, A., et al. 2010, ApJ, 717, 29

(ref: kohler_dust_2015) Köhler, M., Ysard, N., & Jones, A. P. 2015, Astronomy and Astrophysics, 579, A15

(ref: Shark) Lagos, C. d. P., Robotham, A. S. G., Trayford, J. W., et al. 2019, MNRAS, 489, 4196

(ref: Laporte2017) Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJL, 837, L21

(ref: Li2001) Li, A. & Draine, B. T. 2001, ApJ, 554, 778

(ref: Li2019) Li, Q., Narayanan, D., & Davé, R. 2019, MNRAS, 490, 1425

(ref: Liang2019) Liang, L., Feldmann, R., Kereš, D., et al. 2019, MNRAS, 489, 1397

(ref: Lotz2017) Lotz, J. M., Koekemoer, A., Coe, D., et al. 2017, ApJ, 837, 97

(ref: Ma2019) Ma, X., Hayward, C. C., Casey, C. M., et al. 2019, MNRAS, 487, 1844

(ref: Magdis2012) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: Magnelli2020) Magnelli, B., Boogaard, L., Decarli, R., et al. 2020, ApJ, 892, 66

(ref: Magnelli2014) Magnelli, B., Lutz, D., Saintonge, A., et al. 2014, A&A, 561, A86

(ref: Magnelli2012a) Magnelli, B., Lutz, D., Santini, P., et al. 2012, A&A, 539, A155

(ref: Magrini2011) Magrini, L., Bianchi, S., Corbelli, E., et al. 2011, A&A, 535, A13

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Narayanan2018) Narayanan, D., Davé, R., Johnson, B. D., et al. 2018, MNRAS, 474, 1718

(ref: Orellana2017) Orellana, G., Nagar, N. M., Elbaz, D., et al. 2017, A&A, 602, A68

(ref: Planck2011) Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2011, A&A, 536, A21

(ref: Popping2022) Popping, G. & Péroux, C. 2022, MNRAS, 513, 1531

(ref: Popping2023) Popping, G., Shivaei, I., Sanders, R. L., et al. 2023, A&A, 670, A138

(ref: Popping2017) Popping, G., Somerville, R. S., & Galametz, M. 2017, MNRAS, 471, 3152

(ref: Postman2012) Postman, M., Coe, D., Benı́tez, N., et al. 2012, ApJS, 199, 25

(ref: Pozzi2021) Pozzi, F., Calura, F., Fudamoto, Y., et al. 2021, arXiv e-prints, arXiv:2105.14789

(ref: Pozzi2020) Pozzi, F., Calura, F., Zamorani, G., et al. 2020, MNRAS, 491, 5073

(ref: Remy-Ruyer2014) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31

(ref: Saintonge2013) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2

(ref: Santini2014) Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A, 562, A30

(ref: Schreiber2018) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, A&A, 618, A85

(ref: Scoville2014) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84

(ref: Scoville2017) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150

(ref: Scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83

(ref: Scoville2013) Scoville, N. Z. 2013, Evolution of star formation and gas, ed. J. Falcón-Barroso & J. H. Knapen, 491

(ref: Shapley2020) Shapley, A. E., Cullen, F., Dunlop, J. S., et al. 2020, ApJL, 903, L16

(ref: Shivaei2022) Shivaei, I., Popping, G., Rieke, G., et al. 2022, ApJ, 928, 68

(ref: Sommovigo2020) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 497, 956

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Sun2022) Sun, F., Egami, E., Fujimoto, S., et al. 2022, ApJ, 932, 77

(ref: Tacconi2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: Tamura2023) Tamura, Y., C. Bakx, T. J. L., Inoue, A. K., et al. 2023, ApJ, 952, 9

(ref: Tamura2019) Tamura, Y., Mawatari, K., Hashimoto, T., et al. 2019, ApJ, 874, 27

(ref: Triani2020) Triani, D. P., Sinha, M., Croton, D. J., Pacifici, C., & Dwek, E. 2020, MNRAS, 493, 2490

(ref: Valiante2009) Valiante, R., Schneider, R., Bianchi, S., & Andersen, A. C. 2009, MNRAS, 397, 1661

(ref: Venemans2012) Venemans, B. P., McMahon, R. G., Walter, F., et al. 2012, ApJL, 751, L25

(ref: Vijayan2019) Vijayan, A. P., Clay, S. J., Thomas, P. A., et al. 2019, MNRAS, 489, 4072

(ref: Wakelam2017) Wakelam, V., Bron, E., Cazaux, S., et al. 2017, Molecular Astrophysics, 9, 1

(ref: Walter2016) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67

(ref: Watson2015) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327

(ref: Weaver2022) Weaver, J. R., Davidzon, I., Toft, S., et al. 2022a, arXiv e-prints, arXiv:2212.02512

(ref: Weaver2023) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022b, ApJS, 258, 11

(ref: Zavala2021) Zavala, J. A., Casey, C. M., Manning, S. M., et al. 2021, ApJ, 909, 165

# Stack excluding quiescent galaxies

As shown on Figure [2](#fig:dMS) the sample is biased toward sources below the main sequence. To make sure that quiescent galaxies do not bias our analysis and the derived average dust masses, we repeat our stacking analysis after removing all sources with $\Delta$MS $<-0.5$. In total, 2157 galaxies are removed from the sample, leading to a final size of 1946 after removing quiescent galaxies. The results are shown on Figures [12](#fig:mdust_mass_dMS) and [13](#fig:mdust_sfr_dMS).

![image](mdust_mass_z_dMS.pdf) ![image](z_evo_dMS.pdf)

![image](mdust_mass_z_sfr_dMS.pdf) ![image](z_evo_sfr_dMS.pdf)

The main difference appear on the stellar mass subsamples, where the derived dust masses are overall higher –especially in the high-stellar mass regime– after excluding quiescent galaxies (although some bins appear now undetected, likely due to the lower number of sources stacked). This suggest that quiescent galaxies may be overall more dust-poor at given stellar mass, driving the average down when included in the entire sample. In any event, the overall trends observed in the main analysis seem to be confirmed even when removing sources with $\Delta$MS$<-0.5$. One can note that our dust mass measurements are also in better agreement with previous individual results when quiescent galaxies are excluded from the stacks.

# Fit results

On Figures [14](#fig:mdust_mass_fit) and [15](#fig:mdust_sfr_fit) are shown the average dust mass recovered as function of stellar mass, SFR or redshift, superposed with the corresponding fit. Only the detections (i.e. S/N above $3\sigma$, see Section [3](#sec:method)) are shown and used in the fit. The coefficients of the fits are shown on Table [\[tab:fit\]](#tab:fit).

![image](mdust_mass_z_fit.pdf) ![image](z_evo_fit.pdf)

![image](mdust_mass_z_sfr_fit.pdf) ![image](z_evo_sfr_fit.pdf)

# Distribution of SFR and stellar mass in the subsamples

On Figures [16](#fig:mass_subsample_hist) and [17](#fig:sfr_subsample_hist) are shown the distribution of stellar mass and SFR in the different subsamples. The mean and median values for each subsamples are also shown as red and black vertical lines respectively.

![](hist_mass_distrib.pdf)

![](hist_sfr_distrib.pdf)

# Bootstrapping results

On Figures [18](#fig:boot_mass) and [19](#fig:boot_sfr) we show the distribution of the results from our bootstrapping analyses. For each subsample, 1000 new subsamples are randomly selected (cite: Jolly2020), and their stack values are collected. The distribution of these stack results (normalized to the original stack result of the corresponding subsample) are shown. Color coding is used to distinguish between the detected (in cyan) and not detected (in red) subsamples. A vertical line is placed at $x=1$ to guide the eye.

![](boot_res_mass.pdf)

![](boot_res_sfr.pdf)

# Dust mass inferred from median stacking

In addition to the mean stacking analyses we performed median stacking for each of the subsamples, in the same way as described in the main analysis. The median stacking stamps are shown on Figure [9](#fig:stamps_median) and here we show the dust mass evolution as a function of stellar mass and redshift (Figure [20](#fig:mdust_mass_median)) and as a function of SFR and redshift (Figure [21](#fig:mdust_sfr_median)), similar to Figures [4](#fig:mdust_mstar) and [6](#fig:mdust_sfr). While the median stacking analyses show typically lower dust masses (indicating possible skewed distributions) the results and trends are overall very consistent with the mean stacking analyses.

![image](mdust_mass_z_median.pdf) ![image](z_evo_median.pdf)

![image](mdust_mass_z_sfr_median.pdf) ![image](z_evo_sfr_median.pdf)

[^1]: One should note that the bootstrap analysis is also affected by the RMS of the stacked images. The two errors being hence correlated, one should in principle not add them quadratically. This is an approximation that should slightly over-estimate the error computation.

[^2]: One should note that the SHARK model (cite: Shark) does not directly track the buildup and destruction of dust. Instead, dust masses are estimated assuming an empirical $z=0$ relation between dust-to-gas ratio and gas-phase metallicity.

</paper>

Write the methods card for this paper.