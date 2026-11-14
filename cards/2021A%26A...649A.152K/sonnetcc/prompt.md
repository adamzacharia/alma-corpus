# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...649A.152K\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...649A.152K",
 "title": "The ALPINE-ALMA [CII] survey. Obscured star formation rate density and main sequence of star-forming galaxies at z &gt; 4",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Khusanova, Y.",
 "n_authors": 33,
 "arxiv_id": "2007.08384",
 "doi": "10.1051/0004-6361/202038944",
 "alma_projects_linked_by_archive": [
  "2017.1.00428.L"
 ]
}
```

Paper text:
<paper>
# The ALPINE-ALMA \[CII\] Survey: Obscured Star Formation Rate Density and Main Sequence of star-forming galaxies at z\>4

# Introduction

## Star formation rate density at z\>4

The evolution of the star formation rate density (SFRD) is one of the fundamental elements for properly describing the history of the Universe. This measure provides information about the *in situ* growth of galaxies, provides an inference for the number of ionizing photons produced by galaxies, and, hence, can help to place constraints on the history of the reionization (cite: madau_cosmic_2014; bouwens_reionization_2015; Robertson2015).

The SFRD is generally measured by converting the dust-corrected FUV luminosity density of galaxies (cite: madau_cosmic_2014). Since a fraction of the far-ultraviolet (FUV) light emitted by massive short-lived stars can be absorbed by dust, when present, the total SFRD consists of two components: the $SFRD_{FUV,uncorr}$ measured from the rest-frame FUV luminosity density, and the dust-hidden component $SFRD_{IR}$ measured from the rest-frame infrared (IR) luminosity density.

The ratio between these two components changes with time and, hence, redshift. The obscured fraction, $SFRD_{IR}$, dominates at low redshifts; it is 3 to 10 times higher than $SFRD_{FUV,uncorr}$ at z\<3 (cite: Sanders2003; Takeuchi2003; Magnelli2011; Magnelli2013; Burgarella2013). At higher redshift, the $SFRD_{IR}$ is poorly constrained. However, since metals are produced by stars, the first galaxies should have very low dust content, slightly enriched only by Population III stars. Therefore, in these galaxies, $SFRD_{FUV,uncorr}$ should be well in excess of the dust-hidden fraction $SFRD_{IR}$. As star formation continues, stars internal to the galaxy begin to generate more dust. While the survival of dust grains is regulated by a series of constructive and destructive processes (cite: Calura2017), the net result is an increase of the $SFRD_{IR}$ in respect to the $SFRD_{FUV,uncorr}$, but it is still unknown how fast the $SFRD_{IR}$ increases at early times and when it overcomes $SFRD_{FUV,uncorr}$, mainly due to the lack of large, statistically-representative galaxy populations observed and selected both in the FUV and far-infrared (FIR) at high redshift.

Only a few attempts to constrain the $SFRD_{IR}$ at high redshifts exist in literature and their results remain inconclusive. (cite: Gruppioni2013) measured $SFRD_{IR}$ up to z$\sim$4 using Herschel selected galaxies and found that the $SFRD_{IR}$ decreases rapidly at z\>3. (cite: Rowan-Robinson2016) used the 500 μm sources from Herschel and found that the $SFRD_{IR}$ at z=3-6 is even higher than the estimates from the rest-frame UV, although these results still have significant uncertainty. The measurements of (cite: Koprowski2017) using SCUBA-2 data at redshift up to z$\sim$5, on the other hand, suggest a very steep decrease of $SFRD_{IR}$, steeper than (cite: Gruppioni2013) (cite: Gruppioni2019), so that $SFRD_{IR}$ at z\>4 is even lower than $SFRD_{FUV,uncorr}$. This may be difficult to reconcile with (cite: Rowan-Robinson2016) estimates as well as with individual detections of very dusty galaxies at redshifts $z\simeq7$ (cite: Strandet2017; bowler_obscured_2018), $z=8.312$ (cite: Tamura2019) and $z=8.38$ (cite: Laporte2017), where the IR contribution should be extremely low if the $SFRD_{IR}$ continues to decrease rapidly with an increasing redshift. As the discoveries of individual highly dust-obscured objects are not from volume-complete samples, it is difficult to determine whether such objects are common in the early Universe. However, the recent study using a volume-complete sample from CO Luminosity Density at High Redshift (COLDz) survey by (cite: Riechers2020) resulted in detection of three massive dusty starburst galaxies over $\sim200,000$ Mpc$^3$, indicating a high space density of such dusty objects at z\>5. Since this study was limited to luminous starburst galaxies, this is only a lower limit and less luminous galaxies can contribute even more to $SFRD_{IR}$. On the other hand, the previously mentioned studies based on measuring IR LFs (cite: Gruppioni2013; Rowan-Robinson2016; Koprowski2017) suffered from several deficiencies at the high-redshift end ($3.0 < z < 4.2$). At these redshifts, the observations were found to be considerably incomplete, and, furthermore, those galaxies that were observed were mostly brighter than typical galaxies at these redshifts. As such, conclusions related to the relative contribution of unobscured and obscured star formation at these epochs were limited in nature.

To overcome the difficulty of computing IR LFs at z\>4, the measurements of the cosmic infrared background (CIB) produced by dusty galaxies can be used together with the modeling of dusty galaxy clustering, from which the $SFRD_{IR}$ can be then derived. (cite: Maniyar2018) did this analysis using the CIB anisotropy measurements and their cross-correlation with cosmic microwave background (CMB) lensing (cite: Planck_CIB_2014). The results turned out to be consistent with a shallower evolution of the $SFRD_{IR}$ at high redshifts compared to the results by (cite: Gruppioni2013) and (cite: Koprowski2017). At z\>4, the $SFRD_{IR}$ does not drop below $SFRD_{FUV,uncorr}$ but approaches it up to z$\sim$6.

Due to the difficulty in constraining the $SFRD_{IR}$ at redshifts z\>4, the measurements of the total SFRD rely mostly on the rest-frame FUV part of the spectrum. To account for the obscured fraction, the relation between the infrared excess (IRX) and the UV spectral slope ($\beta$) (cite: Meurer1999) is often used. However, stacking analysis (cite: Fudamoto2017), as well as individual observations of high redshift galaxies with ALMA revealed significant scatter of dust properties. Most galaxies show a deficit of FIR flux compared to local galaxies with the same $\beta$ slopes (cite: Capak2015; Bouwens2016; Fudamoto2020), which can be partially explained by higher dust temperatures (cite: Faisst2017). The measurements of dust temperatures are scarce but indeed higher than in local galaxies (30-43 K at z$\sim$5) (cite: Faisst2020). Since measurements of the SFRs at high redshifts are based on dust corrections coming from the IRX-$\beta$ relation, the scatter in the relation induces uncertainties on these measurements. For this reason, rest-frame FIR observations at z\>4 remain important to constrain the IR luminosities independently.

## Main sequence and sSFR at z\>4

It is well established in the literature that star-forming galaxies form a so-called main sequence, a relationship between the amount of stellar mass in situ ($M_*$) and the SFR (cite: Noeske2007; Daddi2007; whitaker_star-formation_2012; speagle_highly_2014; Salmon2015; tasca_evolving_2015; schreiber_herschel_2015; Tomczak2016; santini_star_2017; pearson_main_2018; Khusanova2020VUDS). However, the measurements of the SFRs of individual galaxies at z\>4 suffer from the uncertainty of the IRX-$\beta$ relation and/or the dust temperature of the galaxies (see Sect. [1.1](#intro1)), hence, lower number of detection in the rest-frame FIR than expected assuming local IRX-$\beta$ (cite: Capak2015; Bouwens2016). Besides, getting a wide volume in the rest-frame FIR at z\>4 is expensive observationally. Therefore, the constraints on the main sequence of galaxies are limited and are mostly based on the rest-frame FUV data.

Only a few attempts have been made to constrain the main sequence using sub-mm observations, mainly using data from Herschel (cite: schreiber_herschel_2015; pearson_main_2018). At z\>4, however, the measurements are limited by confusion noise (cite: Nguyen2010), which makes it difficult to observe individual sources without careful and well-informed de-blending schemes. Therefore, these works primarily are limited to only the high mass end of the main sequence ($\log(M_*/M_{\odot})>10.5$). Star-forming galaxies with such high masses are rather rare, and it remains unclear if the slope of the main sequence remains the same over the whole range of masses.

The main sequence evolution with redshift is linked to the sSFR evolution defined as $SFR/M_*$, although the sSFR evolution can vary depending on the mass if the slope of the main sequence is not unity, as claimed in several studies (cite: Salmon2015; schreiber_herschel_2015; tasca_evolving_2015; Khusanova2020VUDS). In that case, the measurements from UV selected samples, which probe galaxies with lower stellar masses ($\log(M_*/M_{\odot})\lesssim 10$) are not comparable with FIR samples probing higher stellar masses (cite: schreiber_herschel_2015). The sSFR constraints at high redshifts are inconclusive: while many studies find a shallower evolution at high redshifts (cite: Bouwens_uv_2012; Gonzalez2014; tasca_evolving_2015; Faisst2016; santini_star_2017), some find higher sSFR, consistent with steeper evolution, as at lower redshifts (cite: stark_keck_2012; deBarros2014).

The ALMA Large Program to INvestigate \[CII\] at Early times (ALPINE) was designed with a goal of measuring the dust-hidden SFR in galaxies at z\>4 from a representative UV selected sample (cite: Bethermin2020; lefevre_alpine_2019; Faisst2020). In this paper, we use a large sample of 118 galaxies observed in the rest-frame FIR with ALMA to determine the $SFRD_{IR}$ at z\>4 from ALPINE. We also determine their average and individual SFRs and constrain the main sequence over the stellar mass range $9\lesssim\log(M_*/M_{\odot})\lesssim11$. The combination of the rest-frame FUV and FIR data allows estimating SFRs without relying on IRX-$\beta$ relation and by directly measuring the total infrared luminosities. We present the ALPINE data in Sect. [2](#data_section). In Sect. [3](#methods_section), we describe the stacking code and the methods to measure the SFRD. In Sect [4](#sfrd_meas_sect), we present and discuss our SFRD measurements. Sect. [5](#alp_ms_sect) is dedicated to a discussion about the main sequence and the sSFR evolution with redshift. In Sect. [6](#concl_section) we summarize our results.

Throughout the paper, we use a $\Lambda$CDM cosmology with $\Omega_{\Lambda}=0.70$, $\Omega_m=0.30$ and $h=0.7$. All magnitudes are given in the AB system. We assume a (cite: Chabrier2003) initial mass function (IMF) to convert luminosities to SFRs.

# Data

ALPINE was designed to observe \[CII\] emission and the rest-frame FIR continuum of a representative sample of star-forming galaxies in the redshift range $4.4<z<5.$8 with a gap at redshifts 4.65\<z\<5.05, where the \[CII\] 158 μm emission line falls into the low transmission window (cite: lefevre_alpine_2019). The selection of galaxies covers a wide range of stellar masses $9\lesssim\log(M_*/M_{\odot})\lesssim11$ and star formation rates derived from the rest-frame FUV with SED fitting $1\lesssim \log(SFR [M_{\odot}/yr])\lesssim3$ (cite: Faisst2020). The targets are “normal” star-forming galaxies and, based on observations in the rest-frame FUV, populate the main sequence. We use stacking of both detections and non-detections to derive the average properties of the sample (see Sect. [3](#methods_section)). In this way, we avoid bias towards Luminous Infrared Galaxies (LIRGs) and Ultra Luminous Infrared Galaxies (ULIRGs), compared to other observations of samples selected in the rest-frame FIR at these redshifts.

In total, 118 galaxies were observed in the period from May 2018 to January 2019 (cite: Bethermin2020). The targets were primarily selected from two large spectroscopic surveys: VIMOS UltraDeep Survey (cite: lefevre_vimos_2015; Tasca2017) and DEep Imaging Multi-Object Spectrograph (cite: Faber2003) 10K Spectroscopic Survey (cite: DEIMOS_release_paper_2018). All targets have secure spectroscopic redshifts from the rest-frame UV spectra and are imaged with both space and ground-based instruments (cite: Grogin2011; koekemoer_candels:\_2011; Laigle2016; Skelton2014). The secure spectroscopic redshift ensures that \[CII\], if present, will fall within the relatively narrow observed ALMA bandpass.

The ALMA data were calibrated with the standard ALMA pipeline. The CASA software was used for the data reduction (cite: McMullin2007). To produce continuum maps, we excluded all the channels that correspond to the position of the \[CII\] line. In case of non-detections of the \[CII\] emission, we used spectroscopic redshifts from VUDS or DEIMOS 10K and excluded data within 500 km/s around the expected position of \[CII\] line. For galaxies with detected \[CII\] emission, we manually defined the window around the detected emission line. We then produced the continuum maps, using the task `tclean`. We used natural weighting to maximize SNR. More detail on data reduction can be found in (cite: Bethermin2020).

The surveys was optimized to detect \[CII\] line emission. Therefore, the expected SNR for the rest-frame FIR continuum varies in the range from 0.5 to 3 for most targets based on the SED models of (cite: Bethermin2017). We reached a sensitivity of 50 μJy/beam at 4.4\<z\<4.6 and 28μJy/beam at 5.1\<z\<5.8. We found that the 95% purity is reached with a SNR=3.5 cut for targeted galaxies. Only 23 out of 118 (19%) of the ALPINE targets are detected with such significance. However, given the known positions of the targets, we can extract the average continuum flux of non-detected galaxies using stacking, as described in Sect. [3.1](#stacking_section).

The galaxies in ALPINE are chosen in the two well-studied fields, Cosmic Evolution Survey (cite: Scoville2007_cosmos_overview) and Extended Chandra Deep Field-South Survey (cite: Giacconi2002) that is covered by CANDELS (cite: koekemoer_candels:\_2011; Grogin2011). (cite: Faisst2020) analyzed the multi-wavelength ancillary data in both fields and derived the physical properties of galaxies using SED fitting (stellar masses, SFRs, rest-frame FUV luminosities, etc). The SED fitting is performed with the LePhare package (cite: Arnouts1999; ilbert_accurate_2006), using (cite: bruzual_stellar_2003) models. The model parameters are outlined in Table [1](#sedfit_params). The photometry from the public COSMOS catalog (cite: Laigle2016) was used for targets in the COSMOS field, and the 3D-HST catalog (cite: Skelton2014) was used for the ECDFS. The fitting was performed in flux density space and emission lines are included. More detail about the SED fitting of ALPINE galaxies can be found in (cite: Faisst2020).

+----------------------------------------------------------------------------+
| Input parameters                                                           |
+:================+:=========================================================+
| IMF             | (cite: Chabrier2003)                                     |
+-----------------+----------------------------------------------------------+
| SFH             | Exponentially declining ($\tau=0.1,0.3,1.0,3.0$ Gyr)     |
+-----------------+----------------------------------------------------------+
|                 | Delayed exponential ($\tau=0.1,0.5,1.0,3.0$ Gyr)         |
+-----------------+----------------------------------------------------------+
|                 | Constant                                                 |
+-----------------+----------------------------------------------------------+
| Attenuation law | Calzetti starburst                                       |
+-----------------+----------------------------------------------------------+
| E(B-V)$_s$      | 0, 0.05, 0.1, 0.15, 0.2, 0.25, 0.3, 0.35, 0.4, 0.45, 0.5 |
+-----------------+----------------------------------------------------------+
| Metallicities   | 0.2 $Z_{\odot}$ and 1.0 $Z_{\odot}$                      |
+-----------------+----------------------------------------------------------+

: SED fitting model parameters

# Methods

## Stacking of the rest-frame FIR continuum images

As mentioned above, for $\sim$81% of the ALPINE targets, the observed continuum flux cannot be measured since it falls below the 3.5$\sigma$ limits. Therefore, we used stacking to measure the average flux of galaxies with similar physical properties. We use all the targeted galaxies including both detections and non-detections, since our goal is to get the average flux of the whole population of galaxies in each bin.

Here we use the mean stacks of continuum images. We only use the targeted galaxies and their UV-positions for alignment. Since the targets are not perfectly aligned on stacks due to uncertainties in astrometry or real physical offsets, the flux is measured using an aperture of 3 arcsec diameter. (cite: Bethermin2020) has tested three other methods of continuum flux measurements in addition to aperture photometry: Gaussian fitting on a continuum map and on the *UV* plane, and peak flux. They all were proven to be consistent with each other, except for the peak flux. This is because the sources are not point-like. The other methods give equivalent results. However, on the stacks only aperture photometry can be used, since we cannot align the non-detected sources and their sizes are possible also different. Therefore, their mean profile will not be Gaussian. The aperture photometry, on the other hand, makes it possible to measure the flux without any assumption on the profile shape. Since the beam sizes in ALPINE do not exceed 1.6 arcsec, the 3 arcsec aperture is large enough to include all the flux from the targets if the sources are significantly extended. (cite: Fujimoto2020), examined the radial surface brightness profiles of ALPINE targets and found that the sources are compact in the rest-frame FIR.

We use bootstrapping analysis to ensure the robustness of the measurements of the flux and to estimate the uncertainties coming from both the noise and the sample variance. Each stack is produced from a set of continuum images. To measure the average flux and its uncertainty, we randomly draw a new sample of images without withdrawal from the initial set and produce a new stack image, from which the continuum flux is remeasured. We repeat the procedure 1000 times and find the average and standard deviation of the measurement – $\sigma_{boot}$.

We also measure the flux in the field with the same aperture at each step. We mask the positions of the serendipitously detected objects and the center beforehand, to ensure that the flux measured in the field is not contaminated. The apertures are then placed at random positions, away from serendipitous sources. The variance of the field flux is an estimate of the photometric noise on the stacked image and is on average $\sigma_{phot}=0.05$ mJy for the typical number of stacked images (8). The average flux in the field is compatible with zero as expected ($F_{field}=0.1\pm50.0$ μJy).

As discussed in (cite: Bethermin2012), the bootstrap uncertainty $\sigma_{boot}$ and the photometric noise $\sigma_{phot}$ are related as:

$$\begin{equation}
\label{sigma_boot_eq}
\sigma_{boot}=\frac{\sqrt{\sigma^2_{phot}+\sigma^2_{pop}}}{\sqrt{N_{stack}}},
\end{equation}$$ where $N_{stack}$ is the number of images in the stack and $\sigma_{pop}$ is the intrinsic population variance. The uncertainties derived using the bootstrap method are thus including both the photometric noise and the sample variance coming from the finite size and the possible large heterogeneity of the stacked samples.

![](test_stacking)

In order to test reliability of the flux measurement on the stacks, we generated a number of fake sources on the images avoiding the center with fluxes drawn from a Gaussian distribution with a known mean $F_{in}$ and variance $\sigma_{in}$. The sources are Gaussian and their FWHM were allowed to vary from 0.8 to 1.6 arcsec (cite: Bethermin2020). We used the procedure described above to stack images with the fake sources, but in order to simulate position uncertainties of real targets, we added random offsets sampled from a Gaussian with $\sigma=0.12$ arcsec (cite: Faisst2020). Then we measured the average flux $F_{out}$ and the bootstrap uncertainty $\sigma_{out}$. We performed the procedure 250 times, varying the $F_{in}$ flux value in the range from 0.01 to 0.18 mJy or $\sim$0.25-3.5$\sigma_{phot}$ and the number of images from 6 to 13 (as we used later for the stacks).

Fig. [1](#test_fig) shows the distribution of $\Delta{F}/\sigma_{out}=(F_{out}-F_{in})/\sigma_{out}$. The mean of the distribution is -0.03 and the standard deviation is 1.13. The mean is compatible with zero. The standard deviation of the distribution can be reduced to $\sim1$, if we limit the analysis to stacks with a high number of images (\>20), however, this is not feasible given the number of objects in the sample. We, therefore, make stacks with the number of objects in range from 6 to 13, but divide them in smaller bins to be able to constrain the $L_{IR}-M_*$ or $L_{IR}-M_{FUV}$ relation.

In conclusion, the average fluxes on stacks are well recovered within the error bars if the sources are not significantly extended or offset. This is the case for the detected targets (cite: Bethermin2020), and stacking, therefore, can be safely used to recover the average continuum fluxes.

## SFRD measurement: method description

The total SFRD can be defined as (cite: madau_cosmic_2014): $$\begin{equation}
\label{sfrd_eq}
\begin{split}
SFRD=SFRD_{FUV,uncorr} + SFRD_{IR}=\\  \kappa_{FUV}\rho_{FUV}+\kappa_{IR}\rho_{IR},
\end{split}
\end{equation}$$ where $SFRD_{FUV,uncorr}$ is derived from the FUV luminosity density ($\rho_{FUV}$) not corrected for dust attenuation, and $SFRD_{IR}$ is derived from the IR luminosity density ($\rho_{IR}$). The conversion factors are $\kappa_{FUV}=1.5*10^{-10}M_{\odot}year^{-1}L_{\odot}^{-1}$ and $\kappa_{IR}=10^{-10}M_{\odot}year^{-1}L_{\odot}^{-1}$ for (cite: Chabrier2003) IMF (cite: kennicutt_global_1998).

### Measuring IR luminosity density

Since ALPINE is not a volume-limited sample, it is rather difficult to determine the IR LF from the target sample (cite: Gruppioni2020). We use, therefore, a different approach to obtain the IR luminosity density, which can then be converted to the $SFRD_{IR}$. The method is based on using some physical property as a proxy of the infrared luminosity - $L_{IR}$ and convolving the volume density distribution of this proxy with the mean LIR-proxy relation as:

$$\begin{equation}
\label{LDIR_formula}
\rho _{IR}=\int{ \langle L_{IR}\rangle(x)\phi(x)dx},
\end{equation}$$ where $x$ is a proxy ($M_{FUV}$ or $M_{*}$, see Sect. [3.2.2](#proxy_choice_section)), $\langle L_{IR}\rangle$ is the total infrared luminosity and $\phi(x)$ is either the FUV luminosity function (UVLF) or the galaxy stellar mass function (GSMF). The total IR luminosity is derived from the SED templates scaled to the 158 μm flux measured on stacks and then integrated from 8 to 1000 μm. We use average conversion factors $\langle f_{temp, z\sim4.5} \rangle = 0.13 \pm 0.02$ and $\langle f_{temp, z\sim5.5} \rangle = 0.12 \pm 0.03$ derived from a set of templates from the literature, which are consistent with the stacked Herschel data (see Appendix [7](#sect:seds) for more detail on the templates and conversion factor). A summary of the method is presented in Fig. [2](#method_illustation_fig_1).

![](method_illustration.pdf)

The volume density distribution can be derived, for example, from the parent surveys, from which ALPINE targets were selected (VUDS or DEIMOS 10K) or from the literature measurements of the proxy density functions (UVLF or GSMF in our case).

### The choice of proxy

The method described above relies on the assumption that there is a relation between the proxy and the IR luminosity. To first order, this is true for stellar masses ($M_{*}$, we will refer to "stellar mass" as "mass" hereafter) of star-forming galaxies, which sit on the main sequence. Their SFR increases with the mass (cite: whitaker_star-formation_2012; whitaker_constraining_2014; tasca_evolving_2015; Salmon2015; santini_star_2017; pearson_main_2018; Khusanova2020VUDS). While it is still unclear what fraction of SFR is hidden by dust, we expect that there is a relation between the masses and the IR dust emission (see Sect. [5](#alp_ms_sect) for more discussion on the main sequence). Also the FUV-magnitudes are linked to SFR to first order. If we assume that more star-forming galaxies have higher IR luminosities, the FUV-magnitudes should correlate with the $L_{IR}$. Each proxy, however, has its own sources of uncertainty, which are discussed below. Therefore, we use both of them and compare the results.

![](mass_fuv.png)

The accuracy of the mass is limited, since it is derived from SED fitting and it is, therefore, model-dependent.

The caveat in using the mass as a proxy is the fact that the sample of galaxies in ALPINE is selected to have FUV luminosities above $0.6L^*$. Hence, the galaxies selected at lower masses are not representative of typical galaxies at these masses, since they are biased towards higher UV luminosities at fixed mass. We show in Fig. [3](#mass_fuv) the median values of the $M_*-M_{FUV}$ relation from (cite: Salmon2015) and the fit of this relation. This relation agrees well with the $M_*$ and $M_{FUV}$ measurements for ALPINE targets. We find the mass at which the 1$\sigma$ envelope around the best fit crosses the FUV luminosity selection limit, where $\sigma$ is the scatter around the fit. As shown in Fig. [3](#mass_fuv), the mass limit is $\log M_{lim}/M_{\odot}=9.6$ at both redshifts. Below this limit we are likely to miss galaxies with faint FUV magnitudes, biasing SFR towards higher values.

The FUV magnitudes are not affected by this bias. Since the spectroscopic redshifts are known, they are not model-dependent and can be derived with high accuracy given well-measured photometry (cite: Faisst2020). We do not correct the derived FUV magnitudes for dust attenuation in order to keep them model-independent. However, the more dust is in the galaxy, the more FUV radiation is absorbed for a given SFR/IMF combination. Therefore, even if majority of faint in FUV galaxies have low dust content, very dust rich galaxies can contaminate FUV faint bins. In that case, the population will be heterogeneous in each bin and the relation may have larger scatter. This will make it more difficult to constrain the relation between FUV magnitude and IR luminosity. We determine the population variance with the bootstrapping procedure described in Sect. [3.1](#stacking_section) (see Eq. [\[sigma_boot_eq\]](#sigma_boot_eq)). The impact of the population variance is then propagated to the uncertainties on the SFRD. However, if the population variance is intrinsically too large, the use of FUV magnitudes as a proxy can be challenging to analyze small samples.

### Integration limits

ALPINE probes only a range of masses ($9\lesssim\log(M_*/M_{\odot})\lesssim11$) or FUV-magnitudes ($-19\lesssim\log(M_*/M_{\odot})\lesssim-23$), used as a proxy (this range is schematically shown as shaded region in Fig. [2](#method_illustation_fig_1)). In this range, we have measurements of the rest-frame FIR flux directly from the stacks of ALPINE images. The proxy density is known from observations. The $SFRD_{IR}$ measured from integration in this range is, hence, the most robust lower limit of the dust-hidden fraction of SFRD. However, more infrared luminosity can be contained in FUV faint or low mass galaxies. While these galaxies are expected to have low dust content, they can still affect the results due to their high density in the Universe. Galaxies with high masses or bright in FUV are rare, but could also contribute to the total SFRD budget. Therefore, we need to extrapolate the observed in ALPINE $L_{IR}-proxy$ relation and the proxy density functions to obtain the estimate of the total $SFRD_{IR}$.

We determine, first, the lower limit ($SFRD_{IR,min}$) by integrating the Eq. [\[LDIR_formula\]](#LDIR_formula) within the observed in ALPINE mass of FUV-magnitude range. Then, for the extrapolation, we use the integration limits corresponding to $0.03L^*$ [^1] and $100L^*$. These are $M_{FUV}=-17$ and $M_{FUV}=-26$, respectively. In order to define integration limits for masses, we convert these limits to SFRs. Then we use the relation between SFR and mass from the main sequence fit in (cite: Khusanova2020VUDS) to find the corresponding masses: $\log(M_*/M_{\odot})=6.0$ for the lower limit and $\log(M_*/M_{\odot})=12.4$ for the upper limit. With these limits, we can make a meaningful comparison between the $SFRD_{FUV,uncorr}$ derived in the literature from UV LFs and the $SFRD_{IR}$ measured here.

We note that even after extrapolation, we can still be missing galaxies with high IR luminosity, but too faint in the rest-frame FUV to be detected in current photometric surveys (cite: Caputi2014; Franco2018; Williams2019; Wang2019; Gruppioni2020). Their contribution will be discussed in the Sect. [4.3.3](#subsection_total_SFRD).

# SFRD measurement results

## Proxy number density

First, we need to define the proxy number density: UVLF or GSMF. Their measurements are widely available in the literature (cite: bouwens_uv_2015; Finkelstein2015; Ono2018; Pello2018; Khusanova2020VUDS; Song2016; Davidzon2017; Wright2018) but are still affected by many uncertainties. In particular, the faint and low mass end slopes are still not well constrained. Another uncertainty is the shape of the UVLF. While most authors assume the Schechter function form, some recent works found that at high redshift the double power law (DPL) is preferable form (cite: bowler_galaxy_2015; Ono2018; Khusanova2020VUDS). We do not favor any particular UVLF or GSMF, but use several of them to show how the uncertainties on their parameters and functional form propagate into our SFRD estimates.

For the UVLF, we use the (cite: bouwens_uv_2015; Finkelstein2015; Ono2018; Pello2018) and (cite: Khusanova2020VUDS) results. The (cite: bouwens_uv_2015; Finkelstein2015) and (cite: Pello2018) UVLFs are based on large samples with photometric redshifts. The UVLF is represented with a Schechter function. (cite: Ono2018) uses a dropout selection partially confirmed by spectroscopic redshifts and (cite: Khusanova2020VUDS) uses the sample with spectroscopic redshifts. These studies probe the bright end of the UVLF and find a DPL form of UVLF.

We use (cite: Song2016; Davidzon2017) and (cite: Wright2018) measurements of GSMFs. (cite: Song2016) GSMFs are based on samples selected from CANDELS-GOODS field, (cite: Davidzon2017) used photometric selection of galaxies in COSMOS field, and (cite: Wright2018) used a joint analysis of GAMA, COSMOS, and 3D-HST data. We note that the physical parameters derived for ALPINE galaxies in COSMOS field were compared with the COSMOS15 catalogue and found to be consistent (cite: Faisst2020). Therefore, the uncertainties of mass measurements, which are more affected by the choice of the IMF and SFH in SED fitting compared to FUV magnitudes, should not have impact on our results, when we combine the COSMOS-based GSMF with LIR-mass relation from ALPINE.

## $\langle L_{IR}\rangle$-proxy relation

![](lir-proxy.png)

As discussed in Sect. [3.2.2](#proxy_choice_section), we use two proxies in this work: masses and the FUV magnitudes derived using the SED fitting as described in detail in (cite: Faisst2020). The bin sizes are chosen to be small enough to reduce the heterogeneity of the underlying population but to include enough galaxies (6-13) in the bin to have robust average flux measurements. As was discussed in Sect. [3.1](#stacking_section), even faint fluxes on the stacks give us information on the average flux of the underlying population of galaxies. Therefore, we use 3.5$\sigma_{phot}$ upper limits only when the measured fluxes of the stack have negative values. In all the remaining cases, we use the average flux measured with bootstrapping (the SNR in these cases is \>0.5$\sigma_{phot}$, see Fig. [4](#lir-proxy-fig)). When stacking by mass bins, we consider the results as upper limits in bins below $\log M_{lim}/M_{\odot}=9.6$, for the reasons discussed in Sect. [3.2.2](#proxy_choice_section) (bias towards higher SFR because of the FUV selection of ALPINE). The upper limits are the sum of the flux measured on stacks and 3$\sigma$.

We converted the average rest-frame 160 μm fluxes to $\langle L_{IR}\rangle$ and found the $\langle L_{IR}\rangle$-proxy relation. We show the resulting relations in Fig. [4](#lir-proxy-fig). The $\langle L_{IR}\rangle$ is clearly well correlated with both proxies. We fit this relation with a power law using the MCMC method with `emcee` package in python and checking at each step that the fit does not go above upper limits. The results are shown in Fig. [4](#lir-proxy-fig). The slope is well constrained, and the normalization lies within the error bars. We use the MCMC chains later when deriving the $SFRD_{IR}$. This allows us to derive the uncertainty of the $SFRD_{IR}$ measurements, which relies on the precision of our $\langle L_{IR}\rangle$-proxy relation.

In Fig. 4, we show the photometric errors and population variance computed as described in Sect. [3](#methods_section) (see Eq. [\[sigma_boot_eq\]](#sigma_boot_eq)) and SNR in each stack. The population variance at $z\sim4.5$ is $\sim0.91$ dex on average and at $z\sim5.5$ it is $\sim0.47$ dex, almost two times lower. As discussed in Sect. [3.2.2](#proxy_choice_section), if the underlying population is heterogeneous, the scatter of its FIR properties will be large. This is what we observe at z$\sim$4.5. This makes the $L_{IR}-M_{FUV}$ relation particularly difficult to constrain at $z\sim4.5$.

We note that the two points below $M_{lim}$, which were excluded from the fit due to a possible bias (see Sect. [3.2.2](#proxy_choice_section)), are in a very good agreement with the power law fit to the points above $M_{lim}$. Therefore, we trust these two points and use them later, when we derive the main sequence.

Interestingly, we observe a stronger evolution with redshift of the $L_{IR}-M_*$ relation than the $L_{IR}-M_{FUV}$ relation. As the redshift decreases, the $L_{IR}$ on average increases for galaxies with the same mass, which means the dust attenuation increases in these galaxies.

## Infrared contribution to SFRD

We present the results of our measurements of $SFRD_{IR}$ in Fig. [5](#hist_z4) and [6](#hist_z5) for redshifts z$\sim$4.5 and z$\sim$5.5 respectively, and in Table [2](#sfrd_table). Although the results depend on the choice of the proxy density parameters, in most cases they agree with each other within the error bars.

The choice of the proxy also plays a role in the constraining power of our method. At redshift z$\sim$4.5, the population variance in FUV bins is larger as we noted before. Hence, although we find a fit to the measured points, these constraints should be interpreted with caution. At z$\sim$5.5, on the contrary, we have weaker constraints when using the mass as a proxy. Due to the bias towards higher $FUV$ magnitudes in low mass bins, we had to exclude them from the fitting of the $L_{IR}-M_{*}$ relation. The remaining points have larger uncertainties at z$\sim$5.5. Hence, the fit of the $L_{IR}-M_{*}$ relation has larger uncertainties, which propagate into uncertainties of the SFRD estimates.

The measurements obtained with FUV as well as $M_*$ as a proxy agree well with each other within the errors in both redshift bins. The fact that the measurements obtained with different proxies are consistent with each other gives us on robustness of our constraints of the IR contribution to the SFRD. In the next section, we discuss our measurements in the context of the SFRD evolution and describe the results in more detail.

![](histograms-4.png)

![](histograms-5.png)

| z$\sim$4.5 |      GSMF      |       Lower limit       |      Extrapolated       |
|:----------:|:--------------:|:-----------------------:|:-----------------------:|
|            |  Davidzon+17   | $-1.53_{-0.17}^{+0.16}$ | $-0.87_{-0.25}^{+0.18}$ |
|            |    Song+16     | $-1.41_{-0.16}^{+0.16}$ | $-1.19_{-0.15}^{+0.17}$ |
|            |   Wright+18    | $-1.43_{-0.17}^{+0.16}$ | $-1.06_{-0.18}^{+0.17}$ |
|            |    Combined    |         $-1.64$         | $-1.07_{-0.23}^{+0.28}$ |
|            |      UVLF      |                         |                         |
|            |   Bouwens+15   | $-2.05_{-0.20}^{+0.18}$ | $-1.44_{-0.21}^{+0.17}$ |
|            | Finkelstein+15 | $-2.24_{-0.20}^{+0.18}$ | $-1.64_{-0.21}^{+0.17}$ |
|            |     Ono+18     | $-1.97_{-0.20}^{+0.18}$ | $-1.34_{-0.21}^{+0.17}$ |
|            |    Combined    |         $-2.44$         | $-1.48_{-0.25}^{+0.24}$ |
| z$\sim$5.5 |      GSMF      |                         |                         |
|            |  Davidzon+17   | $-2.24_{-0.31}^{+0.26}$ | $-1.27_{-0.32}^{+0.26}$ |
|            |    Song+16     | $-1.81_{-0.31}^{+0.26}$ | $-1.45_{-0.29}^{+0.26}$ |
|            |   Wright+18    | $-2.11_{-0.31}^{+0.26}$ | $-1.72_{-0.30}^{+0.26}$ |
|            |    Combined    |         $-2.54$         | $-1.50_{-0.39}^{+0.38}$ |
|            |      UVLF      |                         |                         |
|            |   Bouwens+15   | $-2.20_{-0.20}^{+0.21}$ | $-1.56_{-0.23}^{+0.22}$ |
|            |    Pello+18    | $-2.47_{-0.20}^{+0.21}$ | $-1.80_{-0.23}^{+0.22}$ |
|            |  Khusanova+20  | $-2.32_{-0.20}^{+0.21}$ | $-1.73_{-0.23}^{+0.22}$ |
|            |    Combined    |         $-2.67$         | $-1.64_{-0.24}^{+0.23}$ |
| z$\sim$4.5 |   UVLF+GSMF    |          -2.44          | $-1.28_{-0.36}^{+0.38}$ |
| z$\sim$5.5 |   UVLF+GSMF    |          -2.67          | $-1.60_{-0.28}^{+0.36}$ |

: Infrared SFRD ($\log{SFRD_{IR} M_{\odot}yr^{-1}Mpc^{-3}}$): Results obtained with various UVLFs and GSMFs from the literature.

### The lower limit

First, we obtained the lower limit on $SFRD_{IR}$. For that, we integrated the $\langle L_{IR}\rangle$-proxy relation with the proxy density function in the range where both of them are known from the observations. Hence, this estimate is free from the uncertainties induced by extrapolations. The integration limits are $8.35\leq\log(M_*/M_{\odot})\leq10.5$ for masses and $-23.3\leq M_{FUV}\leq-20.0$ for FUV magnitudes.

As described in Sect. [4.1](#proxy-density_section) and [4.2](#lir-proxy_section), each power law function describing $L_{IR}$-proxy relation is fitted with the MCMC (see Eq. [\[LDIR_formula\]](#LDIR_formula)). To derive the $SFRD_{IR}$ and its uncertainty, we use the MCMC chains of fit parameters to produce a resulting $SFRD_{IR}$ chain. In this way, we obtain a probability distribution function (PDF) of $SFRD_{IR}$, which is a normalized distribution of individual $SFRD_{IR}$ measurements at each step. These PDFs are shown in the left panel of Fig. [5](#hist_z4) and [6](#hist_z5) for both proxies. Depending on the choice of the proxy density function, the PDFs differ but remain consistent within the error bars for each proxy. In Fig. [8](#sfrd_uv_ir_fig), we show the lowest value minus 1$\sigma$ as our lower limits for the IR contribution to SFRD.

These are the most robust lower limits of the $SFRD_{IR}$ as they are obtained with a large and representative sample of galaxies at $4.4<z<5.8$ and only using the proxy range, where actual observations are available. Given this lower limit, the infrared contribution to the total SFRD is already at least 8-13% at $z>4$ as compared to the total SFRD from the (cite: madau_cosmic_2014) curve. While this is seemingly a small amount, these results are in severe disagreement with the results by (cite: Koprowski2017). They fitted the evolution of $SFRD_{IR}$ with redshift by the Gaussian function. The extrapolation of this curve gives $\log (SFRD_{IR} M_{\odot}yr^{-1}Mpc^{-3}) =-3.95$ at z$\sim$5.5, which is much lower than the ALPINE lower limit at this redshift $\log (SFRD_{IR} M_{\odot}yr^{-1}Mpc^{-3}) =-2.67$. Although, the agreement between ALPINE lower limits and $SFRD_{IR}$ measurements by (cite: Koprowski2017) could be reached by a shallower function at z\>4, we note that we only considered a small range of masses or FUV magnitudes for computing the $SFRD_{IR}$ and our sample is UV-selected. Hence, the real values at both redshifts are even higher and in even stronger tension with (cite: Koprowski2017). Due to the fact that the work of (cite: Koprowski2017) is based on the infrared luminosity functions and in the high redshift bins, the observations barely cover the faint end slope of the IR LF, whose uncertainty could be one of the source of this discrepancy.

### Extrapolated $SFRD_{IR}$

![](sfrd_uvuncorr.png)

The total $SFRD_{IR}$ is higher than the lower limit derived above. To derive the total $SFRD_{IR}$, we assume that the $\langle L_{IR}\rangle-proxy$ relation is the same at all FUV-magnitudes and masses and extrapolate the $\langle L_{IR}\rangle-proxy$ relation as well as the proxy number density function to the integration limits, corresponding to $0.03L_*$ and $100L_*$ or $\log(M_*/M_{\odot})=6.0$ and $\log(M_*/M_{\odot})=12.4$ for masses, as mentioned in Sect. [3.2](#methods_sfrd_section). We obtain the PDFs in the same way as above and show the results on the right panels in Fig. [5](#hist_z4) and [6](#hist_z5). To place the results in the context of the SFRD evolution, we combine the PDFs obtained with different proxy density functions from the literature. Since the lengths are the same for all chains, combining them does not favor any particular proxy density function. We obtain an average estimate of the SFRD and our uncertainties naturally include the systematics coming from the GSMF and UVLF.

Fig. [7](#uv_uncor_ir_fig) illustrates the evolution with redshift of $SFRD_{IR}$ and the uncorrected for dust estimate from FUV luminosity density - $SFRD_{FUV,uncorr}$. We observe a gradual decrease of the $SFRD_{IR}$, which only starts to intersect with the $SFRD_{FUV,uncorr}$ at z\>5. Even at such high redshifts, the $SFRD_{FUV,uncorr}$ does not overcome the $SFRD_{IR}$. It remains an open question, however, at which redshift the $SFRD_{FUV,uncorr}$ overcomes the $SFRD_{IR}$, since at z\>4 the $SFRD_{IR}$ is only gradually approaching the $SFRD_{FUV,uncorr}$. If the evolution is flatter at higher redshifts, then the dust contribution becomes negligible compared to $SFRD_{FUV,uncorr}$ only at very high redshifts. This trend is consistent with the extrapolation of the (cite: Maniyar2018) model of $SFRD_{IR}$ evolution, which is based on CIB anisotropies. Our results agree well with this model at both redshifts. However, if the contribution from ultra-dusty objects, which are missing from the optical and near-infrared (NIR) catalogs is significant, the $SFRD_{IR}$ evolution can be even flatter.

In this paper, we only use the target sources from ALPINE. Recently, (cite: Gruppioni2020) determined the $SFRD_{IR}$ using the non-target ALPINE sources. Our results are in good agreement with the results by (cite: Gruppioni2020) being higher. This is not surprising, since these sources were not selected from the surveys probing rest-frame UV. Therefore, they are better suited for tracing the the star formation contribution coming from ultra-dusty galaxies.

### The total SFRD

![](sfrd_tot.png)

We now define the total SFRD at z$\sim$4.5 and z$\sim$5.5 by summing the $SFRD_{UV,uncorr}$ with the $SFRD_{IR}$ from ALPINE. We plot our results in Fig. [8](#sfrd_uv_ir_fig). The results are in agreement with the FUV based estimates corrected for dust attenuation from the literature within the error bars at both redshifts. They are also in agreement with the measurements based on non-target sources from ALPINE (cite: Gruppioni2020) and with the measurement based on the \[CII\] luminosity function of non-target sources of the field sample (cite: Loiacono2020). However, our results obtained by a combination of two proxies (see Table [2](#sfrd_table)) are 0.5 dex and 0.3 dex higher than the fit of SFRD evolution by (cite: madau_cosmic_2014) or in 1.4$\sigma$ and 1.2$\sigma$ tension at z$\sim$4.5 and z$\sim$5.5 respectively. Although, given the uncertainty on the $SFRD_{IR}$ measurement, it is not possible to reach firm conclusions, the evolution of the total SFRD at z\>4 is possibly shallower than the best fit in (cite: madau_cosmic_2014).

![](fraction)

In Fig. [9](#fig_fraction), we show the evolution of the dust obscured fraction of SFRD with redshift. We use all the points from the literature together with our measurements shown in Fig. [7](#uv_uncor_ir_fig) and [8](#sfrd_uv_ir_fig) to calculate the average $SFRD_{IR}$ and $SFRD_{UV,uncorr}$ in each redshift bin and the ratio of $SFRD_{IR}$ to the total SFRD. We find the infrared contribution to the total SFRD equal to $68_{-25}^{+18}\%$ and $61_{-25}^{+20}\%$ at z$\sim$4.5 and z$\sim$5.5 respectively. Although significant uncertainties remain, our results show that the dust obscured fraction of SFRD is significant even at z\>4. Our results are consistent with semi-analytical model (SAM) by (cite: Cousin2019), which predict that $\sim70\%$ of UV radiation is absorbed by dust at z=5, and with the best fit model by (cite: Zavala2018), which predicts 35%-85% at z$\sim$4-5.

Since we used a sample of galaxies detected in FUV, we did not take into account the contribution from highly obscured and purely IR galaxies, which remains unknown at these redshifts, mainly due to the difficulties in detecting such galaxies. The low number counts of the most massive galaxies makes it difficult to make a statistical census. No sources with z\>5 were found by the deep ALMA observations of the Hubble Ultra-Deep Field (cite: Aravena2016; Dunlop2017; Gonzalez-Lopez2019). Only recently, a few sources with no optical or NIR counterparts were discovered with ALMA at z$\sim$4 and z$\sim$5 (cite: Franco2018; Williams2019) and even z$\sim$6.9 (cite: Strandet2017; Marrone2018). The largest sample up to date was assembled by (cite: Wang2019). It contains 39 Hband dropouts at z\>3 observed with ALMA. Given their results, such galaxies could have an additional contribution of $\sim11\%$ to the total SFRD at $z>4$. Since their sample is restricted to massive H-band dropouts, this is only a lower limit. The lower mass H-band dropouts could contribute to it significantly. Indeed, given the most recent results by (cite: Riechers2020), the dust obscured SFRD is $\log (SFRD_{IR} M_{\odot}yr^{-1}Mpc^{-3}) =-2.02$ or 22% of the total SFRD (based on the space density of two sources detected by CO (J=2$\rightarrow$1) and not detected in the rest-frame UV and optical).

Another uncertainty comes from the fact that the conversion from the 160 μm flux to $L_{IR}$ in this work is based only on one point in the infrared SED. Therefore, our measurement of the total IR luminosity are dependent on the choice of the dust SED template. The infrared SED in high redshift galaxies is uncertain due to poorly constrained dust temperatures (cite: Pavesi2016; Bouwens2016; Faisst2017; Faisst2020). We tested a number of templates against the stacking of Herschel data and only used the ones, which are compatible with the Herschel stacks at redshift range of ALPINE (see Appendix). The best fit of modified black body to these stacks gives the dust temperature $T_{dust}=41\pm1$ K at $z\sim4.5$ and $T_{dust}=43\pm5$ K at $z\sim5.5$ consistent with most recent measurements by (cite: Faisst2020) ($T_{dust}=38\pm8$ at $z\sim5.5$). Although some uncertainties on the dust temperature and the rest-frame FIR part of the SED remain, we incorporate them into the uncertainty of our SFRD measurement by using an average conversion factor between the templates compatible with the stacks of Heschel data and taking into account the uncertainty of the conversion factor. Nevertheless, more observations are needed to better constrain the dust temperatures and SED of galaxies at z\>4.

# Star-forming main sequence and sSFR evolution

![](ms_alpine.png)

![](ssfr_evolution.png)

In Sect. [4.2](#lir-proxy_section), we derived the $\langle L_{IR}\rangle-M_*$ relation. Here we use this relation to derive the main sequence, i.e. the relation between the mass and SFR for these galaxies. In each mass bin, we derive average SFR as $\langle SFR\rangle=\kappa_{FUV}\langle L_{1600}\rangle+\kappa_{IR}\langle L_{IR}\rangle$. The average $\langle L_{1600}\rangle$ is computed from FUV absolute magnitudes, determined with the SED fitting, and the average $\langle L_{IR}\rangle$ from stacks. As discussed in Sect. [3.2.2](#proxy_choice_section), we consider the results from the stacks as upper limits at masses below the completeness limits.

We derived the main sequence in the two redshifts bins: 4.4\<z\<4.7 and 5.1\<z\<5.8. We show the results in Fig. [10](#ms_alpine_fig). The main sequence is well-defined and is in very good agreement with previous results from the literature (cite: santini_star_2017; tasca_evolving_2015; Heinis2013; Khusanova2020VUDS). We fitted the relation between SFR and mass with a power law and found a slope $\alpha=0.99\pm0.08$ at z$\sim$4.5. We find an excellent agreement with the (cite: schreiber_herschel_2015) parametrization of the main sequence evolution at z$\sim$4.5 based on Herschel data, even if we measure the SFRs at lower masses compared to (cite: schreiber_herschel_2015).

At z$\sim$5.5, we obtain a shallower slope $\alpha=0.66\pm0.21$. The difference with the slope at z$\sim$4.5 is only $1.5\sigma$, providing no evidence for an evolution of the slope between the two redshift bins. We note that at z$\sim$5.5, we could only provide FIR flux upper limits at lower masses due to the selection effects (see Sect. [3.2.2](#proxy_choice_section)). Therefore, we only used three points to fit our data and the fit is subject to larger uncertainties. The slope of the main sequence found with Herschel data (cite: pearson_main_2018) at the same redshift but at larger masses is steeper than found with ALPINE data, but still consistent with our data on stacks within the error bars.

In Fig. [10](#ms_alpine_fig), we also plot the individual measurements for galaxies with continuum detections. As expected, most of them are above the main sequence since they represent the brightest galaxies with high SFRs. This confirms that it is necessary to use stacking to obtain unbiased measurements of the average SFR as a function of $M_*$ and fit the main sequence.

We measured the sSFR in the mass range $9.6<\log(M_*/M_{\odot})<9.8$ as in (cite: santini_star_2017). The average sSFR is $\log{sSFR}(Gyr^{-1})=-8.4\pm0.18$ and $\log{sSFR}(Gyr^{-1})=-8.45\pm0.16$ at z$\sim$4.5 and z$\sim$5.5 respectively. We present a comparison with results from the literature in Fig. [11](#ssfr_evol_fig). We find good agreement within the error bars with the results from (cite: Khusanova2020VUDS) at z\>5 and with Herschel data at z$\sim$4 (cite: Bethermin2015; schreiber_herschel_2015), although we note that these works only probe the high mass end ($\log(M_*/M_{\odot})>10.0$) at z$\sim$4. The results are clearly against a steep increase of sSFR at z\>4 and even indicate a possible decrease in sSFR at high redshift. More observations at higher redshifts are necessary to explore this trend.

If the growth of galaxies is regulated mainly by gas accretion through cold streams, the sSFR evolves as $\sim(1+z)^{2.25}$ (cite: dekel_cold_2009; dave_galaxy_2011; sparre_star_2015). This is not the case at high redshifts. Therefore, another mechanism may play a role in the growth of galaxies, such as major and minor mergers (cite: Faisst2016). Another possible explanation could be the suppression of star formation by stronger stellar feedback at high redshifts and reduced star formation efficiency (cite: Weinmann2011). Future studies will place constraints on the role of different mechanisms regulating star formation and the growth of galaxies at high redshifts.

# Conclusions

In this paper, we explored the SFRD, sSFR and main sequence evolution at z\>4 with ALPINE. Using the stacking technique, we constrained the average properties of galaxies even with low number of individual detections.

We determined the robust lower limits $\log SFRD_{IR} (M_{\odot}yr^{-1}Mpc^{-3}) =-2.44$ and $\log SFRD_{IR} (M_{\odot}yr^{-1}Mpc^{-3}) =-2.67$ at z$\sim$4.5 and 5.5 respectively, which indicate that the dust plays an important role at high redshift and that dust build-up happens quite rapidly during and just after epoch of reionization.

We then extrapolated the density functions and found the total dust-hidden IR contribution to SFRD using either masses or FUV magnitudes as a proxy of infrared luminosity. Using the masses, we obtain $\log SFRD_{IR,tot} (M_{\odot}yr^{-1}Mpc^{-3}) = -1.07^{+0.28}_{-0.23}$ and $\log SFRD_{IR,tot} (M_{\odot}yr^{-1}Mpc^{-3}) = -1.48^{+0.24}_{-0.25}$ at z$\sim$4.5 and 5.5 respectively. Using the FUV magnitudes, we obtain $\log SFRD_{IR,tot} (M_{\odot}yr^{-1}Mpc^{-3}) = -1.50^{+0.38}_{-0.39}$ and $\log SFRD_{IR,tot} (M_{\odot}yr^{-1}Mpc^{-3}) = -1.64^{+0.23}_{-0.24}$ at z$\sim$4.5 and 5.5 respectively. The results agree with each other within the error bars and suggest that $68_{-25}^{+18}\%$ and $61_{-25}^{+20}\%$ of the star formation is hidden by dust at z$\sim$4.5 and z$\sim$5.5 respectively. While at z\<4 the $SFRD_{IR}$ component dominates over the $SFRD_{FUV,uncorr}$, at z\>4 their contribution is comparable. The $SFRD_{IR}$ approaches and possibly crosses the $SFRD_{FUV,uncorr}$ at z\>5 but this is yet to be confirmed with future observations.

The evolution of the total SFRD at redshifts higher than the peak of SFRD at z$\sim$2.5 may be shallower than previously measured. Further observations leading to reduced uncertainties are needed to confirm this conclusion.

We also provided robust measurements of SFRs of galaxies at z\>4 and used them to determine the main sequence at z$\sim$4.5 and z$\sim$5.5. We found that the observed main sequence is in good agreement with the previous results based on the rest-frame UV and optical data, as well as the IR data for the most massive galaxies. The main sequence has a slope $\alpha=0.99\pm0.08$ at z$\sim$4.5 and $\alpha=0.66\pm0.21$ at z$\sim$5.5, and no signs of turn-over at high masses. No significant evolution is observed from z$\sim$4.5 to z$\sim$5.5.

We used the SFR and mass measurements to determine the average sSFR of galaxies at z\>4. The results support a shallower or non-existent sSFR evolution at high redshifts than predicted from models of cold gas accretion, or no evolution. Other mechanisms should play an important role in governing the growth of galaxies.

# Acknowledgements

This paper is dedicated to the memory of Olivier Le Fèvre, PI of the ALPINE survey. This work is based on data products made available at the CESAM data center, Laboratoire d’Astrophysique de Marseille, France. YK acknowledges the support by funding from the European Research Council Advanced Grant ERC–2010–AdG–268107–EARLY. AC, CG, FL, FP and MT acknowledge the support from grant PRIN MIUR 2017 - 20173ML3WW_001. GL acknowledges support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (project CONCERTO, grant agreement No 788212) and from the Excellence Initiative of Aix-Marseille University-A\*Midex, a French “Investissements d’Avenir” programme. D.R. acknowledges support from the National Science Foundation under grant numbers AST-1614213 and AST-1910107. D.R. also acknowledges support from the Alexander von Humboldt Foundation through a Humboldt Research Fellowship for Experienced Researchers. G.C.J. acknowledges ERC Advanced Grant 695671 “QUENCH” and support by the Science and Technology Facilities Council (STFC). ST acknowledges support from the ERC Consolidator Grant funding scheme (project ConTExt, grant number No. 648179). The Cosmic Dawn Center is funded by the Danish National Research Foundation under grant No. 140. RA acknowledges support from FONDECYT Regular Grant 1202007.

103 natexlab

(ref: AlvarezMarquez2019) Álvarez-Márquez, J., Burgarella, D., Buat, V., Ilbert, O., & Pérez-González, P. G. 2019, A&A, 630, A153

(ref: AlvarezMarquez2016) Álvarez-Márquez, J., Burgarella, D., Heinis, S., et al. 2016, A&A, 587, A122

(ref: Aravena2016) Aravena, M., Decarli, R., Walter, F., et al. 2016, ApJ, 833, 68

(ref: Arnouts1999) Arnouts, S., Cristiani, S., Moscardini, L., et al. 1999, MNRAS, 310, 540

(ref: Bethermin2015) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113

(ref: Bethermin2012) Béthermin, M., Daddi, E., Magdis, G., et al. 2012, ApJ, 757, L23

(ref: Bethermin2020) Bethermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, arXiv e-prints, arXiv:2002.00962

(ref: Bethermin2017) Béthermin, M., Wu, H.-Y., Lagache, G., et al. 2017, A&A, 607, A89

(ref: Bouwens2016) Bouwens, R. J., Aravena, M., Decarli, R., et al. 2016, ApJ, 833, 72

(ref: bouwens_reionization_2015) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015a, ApJ, 811, 140

(ref: Bouwens_uv_2012) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2012, ApJ, 754, 83

(ref: bouwens_uv_2015) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015b, ApJ, 803, 34

(ref: bowler_obscured_2018) Bowler, R. A. A., Bourne, N., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2018, MNRAS, 481, 1631

(ref: bowler_galaxy_2015) Bowler, R. A. A., Dunlop, J. S., McLure, R. J., et al. 2015, MNRAS, 452, 1817

(ref: bruzual_stellar_2003) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Burgarella2013) Burgarella, D., Buat, V., Gruppioni, C., et al. 2013, A&A, 554, A70

(ref: Calura2017) Calura, F., Pozzi, F., Cresci, G., et al. 2017, MNRAS, 465, 54

(ref: Capak2015) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455

(ref: Caputi2014) Caputi, K. I., Michałowski, M. J., Krips, M., et al. 2014, ApJ, 788, 126

(ref: Casey2018) Casey, C. M., Zavala, J. A., Spilker, J., et al. 2018, ApJ, 862, 77

(ref: Chabrier2003) Chabrier, G. 2003, Publications of the Astronomical Society of the Pacific, 115, 763

(ref: Cousin2019) Cousin, M., Buat, V., Lagache, G., & Bethermin, M. 2019, A&A, 627, A132

(ref: Cucciati2012) Cucciati, O., Tresse, L., Ilbert, O., et al. 2012, A&A, 539, A31

(ref: Daddi2007) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156

(ref: Dahlen2007) Dahlen, T., Mobasher, B., Dickinson, M., et al. 2007, ApJ, 654, 172

(ref: Davidzon2017) Davidzon, I., Ilbert, O., Laigle, C., et al. 2017, A&A, 605, A70

(ref: dave_galaxy_2011) Davé, R., Oppenheimer, B. D., & Finlator, K. 2011, Monthly Notices of the Royal Astronomical Society, 415, 11

(ref: deBarros2014) de Barros, S., Schaerer, D., & Stark, D. P. 2014, A&A, 563, A81

(ref: DeRossi2018) De Rossi, M. E., Rieke, G. H., Shivaei, I., Bromm, V., & Lyu, J. 2018, ApJ, 869, 4

(ref: dekel_cold_2009) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: Dunlop2017) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861

(ref: Faber2003) Faber, S. M., Phillips, A. C., Kibrick, R. I., et al. 2003, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4841, The DEIMOS spectrograph for the Keck II Telescope: integration and testing, ed. M. Iye & A. F. M. Moorwood, 1657–1669

(ref: Faisst2016) Faisst, A. L., Capak, P., Hsieh, B. C., et al. 2016, ApJ, 821, 122

(ref: Faisst2017) Faisst, A. L., Capak, P. L., Yan, L., et al. 2017, ApJ, 847, 21

(ref: Faisst2020) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: Finkelstein2015) Finkelstein, S. L., Ryan, Russell E., J., Papovich, C., et al. 2015, ApJ, 810, 71

(ref: Franco2018) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152

(ref: Fudamoto2020) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, arXiv e-prints, arXiv:2004.10760

(ref: Fudamoto2017) Fudamoto, Y., Oesch, P. A., Schinnerer, E., et al. 2017, MNRAS, 472, 483

(ref: Fujimoto2020) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, arXiv e-prints, arXiv:2003.00013

(ref: Giacconi2002) Giacconi, R., Zirm, A., Wang, J., et al. 2002, ApJS, 139, 369

(ref: Gonzalez2014) González, V., Bouwens, R., Illingworth, G., et al. 2014, ApJ, 781, 34

(ref: Gonzalez-Lopez2019) González-López, J., Decarli, R., Pavesi, R., et al. 2019, arXiv e-prints, arXiv:1903.09161

(ref: Grogin2011) Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, The Astrophysical Journal Supplement Series, 197, 35

(ref: Gruppioni2020) Gruppioni, C., Bethermin, M., Loiacono, F., et al. 2020, arXiv e-prints, arXiv:2006.04974

(ref: Gruppioni2019) Gruppioni, C. & Pozzi, F. 2019, MNRAS, 483, 1993

(ref: Gruppioni2013) Gruppioni, C., Pozzi, F., Rodighiero, G., et al. 2013, MNRAS, 432, 23

(ref: DEIMOS_release_paper_2018) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77

(ref: Heinis2013) Heinis, S., Buat, V., Béthermin, M., et al. 2013, MNRAS, 429, 1113

(ref: ilbert_accurate_2006) Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A, 457, 841

(ref: kennicutt_global_1998) Kennicutt, Robert C., J. 1998, ApJ, 498, 541

(ref: Khusanova2020VUDS) Khusanova, Y., Le Fèvre, O., Cassata, P., et al. 2020, A&A, 634, A97

(ref: koekemoer_candels:\_2011) Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, The Astrophysical Journal Supplement Series, 197, 36

(ref: Koprowski2017) Koprowski, M. P., Dunlop, J. S., Michałowski, M. J., et al. 2017, MNRAS, 471, 4155

(ref: Laigle2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24

(ref: Laporte2017) Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJL, 837, L21

(ref: lefevre_alpine_2019) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2019, arXiv e-prints, arXiv:1910.09517

(ref: lefevre_vimos_2015) Le Fèvre, O., Tasca, L. A. M., Cassata, P., et al. 2015, A&A, 576, A79

(ref: Loiacono2020) Loiacono, F., Decarli, R., Gruppioni, C., et al. 2020, arXiv e-prints, arXiv:2006.04837

(ref: madau_cosmic_2014) Madau, P. & Dickinson, M. 2014, Annual Review of Astronomy and Astrophysics, 52, 415

(ref: Magdis2012) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: Magnelli2011) Magnelli, B., Elbaz, D., Chary, R. R., et al. 2011, A&A, 528, A35

(ref: Magnelli2013) Magnelli, B., Popesso, P., Berta, S., et al. 2013, A&A, 553, A132

(ref: Maniyar2018) Maniyar, A. S., Béthermin, M., & Lagache, G. 2018, A&A, 614, A39

(ref: Marrone2018) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meurer1999) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64

(ref: Nguyen2010) Nguyen, H. T., Schulz, B., Levenson, L., et al. 2010, A&A, 518, L5

(ref: Noeske2007) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43

(ref: Ono2018) Ono, Y., Ouchi, M., Harikane, Y., et al. 2018, PASJ, 70, S10

(ref: Pavesi2016) Pavesi, R., Riechers, D. A., Capak, P. L., et al. 2016, ApJ, 832, 151

(ref: pearson_main_2018) Pearson, W. J., Wang, L., Hurley, P. D., et al. 2018, A&A, 615, A146

(ref: Pello2018) Pelló, R., Hudelot, P., Laporte, N., et al. 2018, A&A, 620, A51

(ref: Planck_CIB_2014) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2014, A&A, 571, A30

(ref: Reddy2009) Reddy, N. A. & Steidel, C. C. 2009, ApJ, 692, 778

(ref: Riechers2020) Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020, ApJ, 895, 81

(ref: Robertson2015) Robertson, B. E., Ellis, R. S., Furlanetto, S. R., & Dunlop, J. S. 2015, ApJ, 802, L19

(ref: Rowan-Robinson2016) Rowan-Robinson, M., Oliver, S., Wang, L., et al. 2016, MNRAS, 461, 1100

(ref: Salmon2015) Salmon, B., Papovich, C., Finkelstein, S. L., et al. 2015, ApJ, 799, 183

(ref: Sanders2003) Sanders, D. B., Mazzarella, J. M., Kim, D. C., Surace, J. A., & Soifer, B. T. 2003, AJ, 126, 1607

(ref: santini_star_2017) Santini, P., Fontana, A., Castellano, M., et al. 2017, The Astrophysical Journal, 847, 76

(ref: Schenker2013) Schenker, M. A., Robertson, B. E., Ellis, R. S., et al. 2013, ApJ, 768, 196

(ref: Schreiber2018) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: schreiber_herschel_2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74

(ref: Scoville2007_cosmos_overview) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1

(ref: Skelton2014) Skelton, R. E., Whitaker, K. E., Momcheva, I. G., et al. 2014, ApJS, 214, 24

(ref: Song2016) Song, M., Finkelstein, S. L., Ashby, M. L. N., et al. 2016, ApJ, 825, 5

(ref: sparre_star_2015) Sparre, M., Hayward, C. C., Springel, V., et al. 2015, Monthly Notices of the Royal Astronomical Society, 447, 3548

(ref: speagle_highly_2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: stark_keck_2012) Stark, D. P., Schenker, M. A., Ellis, R., et al. 2013, ApJ, 763, 129

(ref: Strandet2017) Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017, ApJL, 842, L15

(ref: Takeuchi2003) Takeuchi, T. T., Yoshikawa, K., & Ishii, T. T. 2003, ApJL, 587, L89

(ref: Tamura2019) Tamura, Y., Mawatari, K., Hashimoto, T., et al. 2019, ApJ, 874, 27

(ref: tasca_evolving_2015) Tasca, L. A. M., Le Fèvre, O., Hathi, N. P., et al. 2015, A&A, 581, A54

(ref: Tasca2017) Tasca, L. A. M., Le Fèvre, O., Ribeiro, B., et al. 2017, A&A, 600, A110

(ref: Tomczak2016) Tomczak, A. R., Quadri, R. F., Tran, K.-V. H., et al. 2016, ApJ, 817, 118

(ref: Wang2019) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211

(ref: Weinmann2011) Weinmann, S. M., Neistein, E., & Dekel, A. 2011, MNRAS, 417, 2737

(ref: whitaker_constraining_2014) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104

(ref: whitaker_star-formation_2012) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29

(ref: Williams2019) Williams, C. C., Labbe, I., Spilker, J., et al. 2019, arXiv e-prints, arXiv:1905.11996

(ref: Wright2018) Wright, A. H., Driver, S. P., & Robotham, A. S. G. 2018, MNRAS, 480, 3491

(ref: Zavala2018) Zavala, J. A., Casey, C. M., da Cunha, E., et al. 2018, ApJ, 869, 71

# Conversion of FIR flux to IR luminosity

To convert the rest-frame 160 μm flux to IR luminosity, we scale our flux measurement to the dust SED template and then integrate it from 8 to 1000 μm. Since we use stacks of galaxies, which are not on the same redshift, we use the mean redshift of galaxies in stacks for that conversion. Since we only obtain a measurement of one point in SED, our conversion to IR luminosity will depend on dust SED templates.

There are numerous dust SED templates available in the literature (cite: Magdis2012; Bethermin2017; AlvarezMarquez2016; Casey2018; Schreiber2018; DeRossi2018; AlvarezMarquez2019). Some of them were already discussed and tested by (cite: Bethermin2020). (cite: Bethermin2020) made stacks of Herschel data for galaxies at z\>4 selected via photometric redshifts. They then compared the SED templates to these stacks. We define the conversion factor $f_{temp}$ for each template and the $\chi^2$ from comparison to *Herschel* stacks at both redshifts (see Table [\[table_templates\]](#table_templates)). The conversion factor is defined as $f_{temp} = \nu L_{\nu = 158 \mu m} / L_{IR}$. We discard the templates with reduced $\chi^2$ \> 1.5 in at least one of the redshift bins (see Fig. [14](#fig_templates_discarded)). We define the mean conversion factors from the remaining templates $\langle f_{temp, z\sim4.5} \rangle = 0.13 \pm 0.02$ and $\langle f_{temp, z\sim5.5} \rangle = 0.12 \pm 0.03$ for redshift bins 4\<z\<5 and 5\<z\<6 respectively. These are the values we use to convert the monochromatic flux to the infrared luminosity and propagate their uncertainties into our SFRD measurements.

We note that although the (cite: DeRossi2018) template passes our $\chi^2$ criteria, it goes above the upper limits in redshift bin 4\<z\<5, but is perfectly consistent at 5\<z\<6. Therefore, we use this template only for 5\<z\<6 redshift bin.

| Reference | $f_{temp}$ | $SFRD_{IR, z=4.5}$ | $\chi^2_{z=4.5}$ | $SFRD_{IR, z=5.5}$ | $\chi^2_{z=5.5}$ |
|:--:|:--:|:--:|:--:|:--:|:--:|
| (cite: Bethermin2017) | 0.133 | $-1.37_{-0.27}^{+0.21}$ | 1.61 | $-1.71_{-0.17}^{+0.21}$ | 3.40 |
| (cite: AlvarezMarquez2019) L1 | 0.105 | $-1.47_{-0.27}^{+0.21}$ | 1.16 | $-1.81_{-0.17}^{+0.21}$ | 3.19 |
| (cite: AlvarezMarquez2019) L2 | 0.152 | $-1.31_{-0.27}^{+0.21}$ | 4.69 | $-1.65_{-0.17}^{+0.21}$ | 5.36 |
| (cite: AlvarezMarquez2019) L3 | 0.123 | $-1.40_{-0.27}^{+0.21}$ | 1.89 | $-1.74_{-0.17}^{+0.21}$ | 3.81 |
| (cite: AlvarezMarquez2019) M2 | 0.119 | $-1.42_{-0.27}^{+0.21}$ | 1.04 | $-1.76_{-0.17}^{+0.21}$ | 3.35 |
| (cite: AlvarezMarquez2019) M3 | 0.148 | $-1.32_{-0.27}^{+0.21}$ | 1.97 | $-1.66_{-0.17}^{+0.21}$ | 4.28 |
| (cite: AlvarezMarquez2019) M4 | 0.152 | $-1.31_{-0.27}^{+0.21}$ | 2.20 | $-1.65_{-0.17}^{+0.21}$ | 4.46 |
| (cite: AlvarezMarquez2019) M5 | 0.153 | $-1.31_{-0.27}^{+0.21}$ | 2.28 | $-1.65_{-0.17}^{+0.21}$ | 4.52 |
| (cite: Schreiber2018), z=4.5 | 0.093 | $-1.53_{-0.27}^{+0.21}$ | 2.12 | $-1.86_{-0.17}^{+0.21}$ | \- |
| (cite: Schreiber2018), z=5.5 | 0.073 | $-1.63_{-0.27}^{+0.21}$ | \- | $-1.97_{-0.17}^{+0.21}$ | 3.98 |
| (cite: DeRossi2018) | 0.067 | $-1.67_{-0.27}^{+0.21}$ | 4.65 | $-2.01_{-0.17}^{+0.21}$ | 3.76 |
| Discarded templates |  |  |  |  |  |
| (cite: AlvarezMarquez2016) | 0.189 | $-1.22_{-0.27}^{+0.21}$ | 9.74 | $-1.56_{-0.17}^{+0.21}$ | 7.05 |
| (cite: AlvarezMarquez2019) L4 | 0.229 | $-1.13_{-0.27}^{+0.21}$ | 12.89 | $-1.47_{-0.17}^{+0.21}$ | 8.54 |
| (cite: AlvarezMarquez2019) M1 | 0.354 | $-0.94_{-0.27}^{+0.21}$ | 35.84 | $-1.28_{-0.17}^{+0.21}$ | 16.14 |
| (cite: Casey2018) A | 0.244 | $-1.11_{-0.27}^{+0.21}$ | 11.71 | $-1.45_{-0.17}^{+0.21}$ | 9.00 |
| (cite: Casey2018) B | 0.036 | $-1.94_{-0.27}^{+0.21}$ | 12.99 | $-2.23_{-0.17}^{+0.21}$ | 7.74 |

![](SED_z_4_5_stack_1.pdf)

![](SED_z_4_5_stack_2.pdf)

![](SED_z_5_6_stack_1.pdf)

![](SED_z_5_6_stack_2.pdf)

![](SED_z_4_5_stack_3.pdf)

![](SED_z_5_6_stack_3.pdf)

[^1]: This is a commonly used value in the literature (cite: bouwens_uv_2015; madau_cosmic_2014; Khusanova2020VUDS)

</paper>

Write the methods card for this paper.