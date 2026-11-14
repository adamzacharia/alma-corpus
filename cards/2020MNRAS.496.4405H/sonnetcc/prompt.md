# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.496.4405H\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.496.4405H",
 "title": "Far-infrared star formation rates of six GRB host galaxies with ALMA",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Hsiao, Tiger Yu-Yang",
 "n_authors": 10,
 "arxiv_id": "2007.11874",
 "doi": "10.1093/mnras/staa1865",
 "alma_projects_linked_by_archive": [
  "2015.1.00927.S",
  "2016.1.00768.S"
 ]
}
```

Paper text:
<paper>
# Far-infrared star-formation rates of six GRB host galaxies with ALMA

## Abstract

Gamma-Ray Bursts (GRBs) can be a promising tracer of cosmic star-formation rate history (CSFRH). In order to reveal the CSFRH using GRBs, it is important to understand whether they are biased tracers or not. For this purpose, it is crucial to understand properties of GRB host galaxies, in comparison to field galaxies. In this work, we report ALMA far-infrared (FIR) observations of six $z\sim2$ IR-bright GRB host galaxies, which are selected for the brightness in IR. Among them, four host galaxies are detected for the first time in the rest-frame FIR. In addition to the ALMA data, we collected multi-wavelength data from previous studies for the six GRB host galaxies. Spectral energy distribution (SED) fitting analyses were performed with `CIGALE` to investigate physical properties of the host galaxies, and to test whether active galactic nucleus (AGN) and radio components are required or not. Our results indicate that the best-fit templates of five GRB host galaxies do not require an AGN component, suggesting the absence of AGNs. One GRB host galaxy, 080207, shows a very small AGN contribution. While derived stellar masses of the three host galaxies are mostly consistent with those in previous studies, interestingly the value of star-formation rates (SFRs) of all six GRB hosts are inconsistent with previous studies. Our results indicate the importance of rest-frame FIR observations to correctly estimate SFRs by covering thermal emission from cold dust heated by star formation.

gamma-ray burst: individual: GRB080207, GRB060814 GRB070306, GRB081221, GRB071021 and GRB050915A – galaxies: star-formation – submillimetre: galaxies

# Introduction

Compared to the Short Gamma-Ray Bursts which are believed to be associated with the merger of double compact objects (cite: Nakar2007), Long Gamma-Ray Bursts (hereafter GRBs) are believed to be associated with explosions of massive stars (cite: Paczynski1998; MacFadyen1999; Woosley2006). Due to their intense brightnesses and ability to penetrate dusty star-forming regions (cite: Djorgovski2001), they can be detected at the very distant Universe, i.e., $z \sim 8-9$ (cite: Tanvir2009; Salvaterra2009; Cucchiara2011). Therefore, GRBs can be a powerful tracer of cosmic star formation rate history (CSFRH hereafter) (cite: Wijers1998; Lamb2000; Porciani2001; Yuksel2008; Trenti2012; Goto2019). For this purpose, it is important to understand what kind of star-forming activities or galaxies are traced by GRBs.

More than 1,900 GRBs have been detected and well-localised to date [^1] (Note that the total number detected by The Burst And Transient Source Experiment (BATSE) and FERMI is several times larger). A number of efforts to observe GRB host galaxies have been made between UV and radio wavelengths over the past decade. For instance, (cite: Hjorth2012) surveyed a large sample of 69 galaxies of the optically unbiased GRB host galaxies (TOUGH) and provided the catalogue. (cite: Japelj2016) studied the influence of the environment on GRB formation and researched SFRs and metallicities of 14 bright GRBs with low-redshift ($z<1$) from *SWIFT*/BAT6. (cite: Perley2016) investigated in rest-frame NIR luminosities of 119 GRB host galaxies with a wide range of redshift ($0.03<z<6$). These researches carefully selected the GRB host galaxies in an unbiased way as much as possible. Multi-band flux densities of GRB host galaxies selected in this work are reported in previous literature (cite: Kuepcue2008; Cucchiara2008; Fugazza2008; Klotz2006; Malesani2006a; Malesani2006b; Ofek2006; Jaunsen2008; Kruhler2011; Hunt2011; Svensson2012; Hjorth2012; Perley2013a; Perley2013b; Hunt2014; Perley2015; Hatsukade2019; Hashimoto2019). Following these observations, physical properties of GRB host galaxies were investigated by fitting the observed spectral energy distributions (SEDs) of GRB host galaxies with galaxy templates (cite: Kruhler2011; Perley2013b; Hunt2014; Perley2015; Hashimoto2019).

In general, GRB host galaxies show some distinct characteristics compared to normal star-forming galaxies at least in the low-$z$ Universe. For instance, low-$z$ GRB host galaxies are found to be fainter, bluer, with higher specific star-formation rates and lower metallicities than galaxies that do not host GRBs (cite: Christensen2004). Based on the observation of GRB hosts, GRBs averse the environments with high metallicities (cite: Stanek2006; Levesque2010; Graham2013; Perley2016). Although these effects result in the GRBs occuring preferentially in faint galaxies, there are still some GRBs in luminous galaxies. (cite: Perley2016) investigated the physical properties such as NIR luminosities of the GRB host galaxies with a wide range of redshifts at $0.03<z<6.3$. Their results indicated that the GRB hosts occurred frequently in faint and low-mass galaxies, while luminous and massive GRB hosts are relatively rare. They also found that dust-obscured GRBs dominate the massive host population but are only rarely seen associated with low-mass hosts, reflecting that massive star-forming galaxies are universally and (to some extent) homogeneously dusty at high redshift, while low-mass star-forming galaxies retain little dust in their interstellar medium.

The stellar initial mass functions (IMFs) of GRB host galaxies could be different from that in normal star-forming galaxies (cite: Hashimoto2018).

However, a single IMF shape is conventionally assumed in SED fitting analyses of GRB host galaxies in previous studies (cite: Hashimoto2019). A flexibility in the assumed IMFs would be ideal in SED fitting analysis to better understand the physical properties of GRB host galaxies.

In terms of the requirement to gauge both extincted and unextincted star formation, dust extinction-free methods are especially important because abundant star-forming activity is hidden by dust in general (cite: Goto2010). In fact, some GRB host galaxies around $z\sim1-3$ have been localised in ultraluminous infrared galaxies (ULIRGs), indicating intense dust-obscured star formation (cite: Perley2017). These ULIRG host galaxies exhibited highly obscured SFR up to $\sim 10^{3}$ M$_{\odot}$ yr$^{-1}$ (cite: Perley2017),

probably because

the fraction of star formation density contributed by ULIRGs increases with redshift (cite: Goto2010).

After the emission of a gamma-ray burst, there is usually a fading emission in X-ray to radio wavelengths, the so-called ‘afterglow’.

Radio observation is one of the extinction-free methods that can be utilised to estimate SFRs. However, in GRB-host galaxies, long-living radio afterglows might contaminate radio fluxes of the GRB host galaxies

for several years after the bursts, which potentially causes overestimation of SFRs when the radio luminosity is used to estimate the star-formation rate

(cite: Murphy2011). To securely avoid this fundamental problem, radio observations have to be carried out over a longer period of time (cite: Perley2017).

Rest-frame FIR observations are also free from dust extinction. Afterglows in the rest-frame FIR are negligible after several years from the burst (cite: Hashimoto2019). The rest-frame FIR wavelength is sensitive to the thermal emission from cold dust heated by star-forming regions, which allows us to estimate the SFR more accurately than simply relying on UV to optical or radio data. However, most of the previous observations of GRB host galaxies do not include rest-frame FIR data, except for e.g.

(cite: Berger2003) and (cite: Tanvir2004) which presented the FIR observations of host galaxies.

Even with their efforts (cite: Berger2003; Tanvir2004), the signal-to-noise ratios in the rest-frame FIR are limited due to the sensitivities of previous telescopes. Therefore, SFRs of GRB host galaxies, especially for distant ones, have not been well constrained.

Does the existence of active galactic nucleus (AGN) activity affect the GRB? This has been a matter of debate among previous literature (cite: Hatsukade2019; Hashimoto2019). For example, molecular gas excitation of GRB080207 host galaxy is similar to that of excitations caused by AGNs (cite: Hatsukade2019). An optical emission-line diagnostic indicated that the host galaxy is located at a boundary between AGN and H II regimes (cite: Hatsukade2019). Moreover, the existence of AGN activity correlates with star-formation activity, which could enhance the AGN fraction amongst hosts. The presence of AGN affects not only estimates of stellar mass and SFR, but also the IR luminosity. Therefore, it is important to separate the contributions from AGN and SF through the SED fitting.

In this paper, we present rest-frame FIR detections of six IR-bright GRB host galaxies, as described in Section [2](#sample). The Atacama Large Millimeter/submillimeter Array (ALMA) bands covered the redshifted FIR continuum of the host galaxies. ALMA’s high sensitivity allowed us to detect the rest-frame FIR continuum of these distant GRB host galaxies. We measured the flux for each host galaxy at 343.48 GHz in average. The data including those at rest-frame FIR wavelengths provides a more reliable measurement of obscured SFRs than those without FIR. Our sample is divided into two categories, ‘Group A’ that has radio detection and ‘Group B’ that has no radio detection. In our SED fitting analyses, we tested with and without the AGN and radio components in configurations for Group A. Due to the lack of radio detection in Group B, we only tested with and without the AGN components in the configurations for Group B (i.e., no radio components for the group B). We used an SED fitting code, Code Investigating GALaxy Emission (cite: Burgarella2005; Noll2009; Boquien2019) which provided two options of IMF:

(cite: Salpeter1955) and (cite: Chabrier2003). In this work, we try both IMFs to select the better IMF.

The structure and outline of this paper are as follows. We briefly describe our samples in Section [2](#sample). In Section [3](#data), we present some configurations and conditions of ALMA archive data and the multi-wavelength photometry. We demonstrate the method and the results of physical parameters from SED fitting analyses using `CIGALE` in Section [4](#analysis_results). The best fit configurations are discussed and determined using two different IMFs: (cite: Salpeter1955) and (cite: Chabrier2003), in Section [5](#discussion). Lastly, we present all four different model settings, the difference, and consistency of physical parameters (SFR, stellar mass, and IR luminosity), in reference to previous works in Section [6](#conclusion).

# Sample

In this work, we investigate six IR-bright GRB host galaxies at $z \sim 2$ observed in ALMA band 7, including GRB080207 (cite: Kruhler2012), GRB060814 (cite: Kruhler2012), GRB070306 (cite: Jaunsen2008), GRB081221 (cite: Salvaterra2012), GRB071021 (cite: Kruhler2012) and GRB050915A (cite: Kruhler2012) host galaxies. These host galaxies were selected by ALMA projects

2015.1.00927.S and 2016.1.00768.S

, which aimed at investigating the physical properties of luminous GRB host galaxies at $z\sim2$. Although these galaxies are selected to be IR-bright at high-z , this work would be useful for exploring such population of GRB host galaxies. A thorough investigation by (cite: Perley2016) described that dust-obscured GRBs dominate the massive host population but are only rarely seen associated with low-mass hosts. We briefly summarise the previous studies on these individual host galaxies below.

## GRB080207 host

GRB080207 was first discovered by *Swift*/Burst Alert Telescope (BAT) on 2008 February 7 at 21:30:21 UT (cite: Racusin2008). The follow-up observations of deep optical and NIR were performed by (cite: Kuepcue2008), (cite: Cucchiara2008), and (cite: Fugazza2008) at about 9 hrs, 9.84 hrs, and 11.3 hrs after the triggers, respectively. No afterglow was detected in optical and near-infrared wavelengths (cite: Hunt2011). The host galaxy of GRB080207 was classified as an extremely red object (ERO) with $R-K=6.3$ and dust-obscured galaxy (DOG) with a flux ratio at $24\,\mu$m to $R-$ band flux $\sim1000$ (cite: Hunt2011).

The host galaxy has been intensively investigated with optical-to-infrared telescopes such as Keck, Very Large Telescope (VLT), Spitzer and Gemini (cite: Hunt2011; Rossi2012; Svensson2012; Hunt2014; Hashimoto2019). The SED fitting analyses of this host galaxy were performed in some previous works based on multi-wavelength photometries. (cite: Hunt2014) calculated the following quantities by the SED fitting analysis including the rest-frame FIR continuum detection by *Herschel*: star-formation rate of SFR$_{\rm SED}=170.1 ({\rm M}_{\odot} {\rm yr}^{-1})$, total infrared luminosity $\log L_{\rm IR}=12.25 (L_{\odot}),$ total stellar mass $\log M_{*}=11.17 (M_\odot)$, dust mass $\log M_{\rm dust}=8.15(M_\odot)$, dust temperature $T_{\rm dust}=61.3(\rm K)$. Additionally, (cite: Hashimoto2019) reported the following results by adding ALMA-detected continuum emission: SFR$_{\rm SED}=123.4^{+25.19}_{-21.78}({\rm M}_{\odot} {\rm yr}^{-1})$, $\log L_{\rm IR}=12.26^{+0.05}_{-0.06}(L_{\odot}),$ $\log M_{*}=11.23^{+0.02}_{-0.10}(M_\odot)$ $\log M_{\rm dust}=8.74^{+0.22}_{-0.18}(M_\odot)$, $T_{\rm dust}=39.86^{+1.10}_{-4.11}(\rm K)$. The SFRs between these two studies are consistent within uncertainties if $\sim$30% uncertainty on SFR$_{\rm SED}$ derived by (cite: Hunt2014) is assumed (cite: Hashimoto2019). The stellar masses and the IR luminosities are also consistent within uncertainties.

## GRB060814 host

Prompt emission of GRB060814 was detected by $\it{Swift}$ on 2006 August 14 at 23:02:19 UT (cite: Moretti2006). The afterglow was detected by several telescopes at different times after it was emitted: Télescope à Action Rapide pour les Objets Transitoires (TAROT) after a few minutes (cite: Klotz2006), VLT in the $R-$band after one hour (cite: Malesani2006a) and $g-$band of Sloan Digital Sky Survey (SDSS) after $\sim 6.7$ hours (cite: Ofek2006). The afterglow was also detected with the United Kingdom Infra-Red Telescope (UKIRT) in the $K-$band approximately 7 hours after the burst (cite: Levan2006). The redshift of GRB060814 host galaxy was measured by (cite: Kruhler2012) to be $z=1.923$ by analysing several nebular emission lines in the near-infrared. The host galaxy has been detected in many optical and infrared telescopes such as Keck, VLT, Hubble Space Telescope (HST), Spitzer and Very Large Array (VLA) (cite: Perley2013a; Hjorth2012).

Physical properties of this host galaxy were investigated in previous studies (cite: Hjorth2012; Jakobsson2012; Perley2013a; Perley2015). (cite: Perley2013a) and (cite: Perley2015) performed SED fitting analyses of the host galaxy. The estimated SFRs are 238 and 209 $M_{\odot}$ yr$^{-1}$, and stellar masses are $9.8\times10^{9}$ and $1.6\times10^{10}$ $M_{\odot}$, respectively.

## GRB070306 host

GRB070306 was first detected at 16:44:28.0 UT on 2007 March 06 (cite: Pandey2007) via *Swift*. The afterglow was not detected in optical band with Nordic Optical Telescope (NOT) (cite: Jaunsen2008). (cite: Rol2007) reported that there is a detection of NIR afterglow with William Herschel Telescope (WHT) 3.3 hours later.

The afterglow was also detected with WHT/Long-slit Intermediate Resolution Infrared Spectrograph (LIRIS) in the $K-$band, suggesting a highly extinguished afterglow (cite: Jaunsen2008).

This host galaxy was identified as a heavily obscured star-forming galaxy (cite: Jaunsen2008), and detected with telescopes such as Spitzer, VLT, *Herschel* and VLA (cite: Perley2013a; Hunt2014; Perley2015). The *Hershel* data covers the peak wavelength of thermal emission from cold dust in the host galaxy.

SED fitting analyses of the host galaxy were performed in previous studies. (cite: Kruhler2011) reported that $\log(\rm {SFR_{SED}})=1.1^{+0.3}_{-0.2} (M_{\odot}$ yr$^{-1})$ and stellar mass $\log(M_*)=10.39^{+0.19}_{-0.15} (M_\odot)$. With *Herschel* data in far-infrared, (cite: Hunt2014) revisited the SED fitting analysis of the host galaxy and derived ${\rm SFR_{SED}}$ $=144.1 (M_{\odot}$ yr$^{-1})$, $\log L_{IR}=12.18 \log L(L_{\odot})$, and $\log M_{*} (M_\odot)=10.05$. (cite: Perley2015) also performed the SED fitting analysis and reported $\rm SFR_{SED}$ $=17^{+7}_{-5} (M_{\odot}$ yr$^{-1})$ and stellar mass $M_{*}=5^{+0.1}_{-0.2}\times10^{10} (M_\odot)$.

## GRB081221 host

This gamma-ray burst was first detected at 16:21:11 UT on 2008 December 21 with the *Swift*/BAT (cite: Hoversten2008). In addition, the burst event was also detected by Konus-Wind (cite: Golenetskii2008) and the Fermi Gamma-ray Burst Monitor (GBM) (cite: Wilson-Hodge2008). (cite: Malesani2008) and (cite: Afonso2008b) reported that there was no afterglow in optical with

NOT and Gamma-Ray Burst Optical/Near-Infrared Detector (GROND) $\sim4$ hrs and 33 hrs after the GRB.

However the afterglow was detected in NIR by Gemini-N only in the $K-$band 12 hours after the burst was triggered (cite: Tanvir2008).

The redshift of the GRB was spectroscopically measured to be $z=2.260$ (cite: Salvaterra2012). Moreover, the host galaxy was successfully detected in the $B, V, g, I$ and $z$ bands of Keck-I/Low Resolution Imaging Spectrometer (LRIS) (cite: Perley2013a) and $g, r, i$ bands of GROND (cite: Afonso2008; Perley2013a). The host galaxy was also detected with HST, Gemini-N, Spitzer, and VLA (cite: Perley2013a; Perley2013b; Afonso2008).

For further analysis, (cite: Perley2013a) collected the photometric data of the host galaxy and performed SED fitting. They showed $\rm {SFR_{SED}}$ $=172.8^{+22.8}_{-30.1}(M_{\odot}yr^{-1})$ and $M_{*}=3.7^{+1.1}_{-1.2}\times10^{10}$($M_{\odot}$), respectively.

However their photometric data did not include any FIR data.

## GRB071021 host

GRB071021 at 09:41:33 UT on 2007 October 21 was first triggered by *Swift* (cite: Sakamoto2007). 11.25 hours after the burst, the afterglow was detected with Telescopio Nazionale Galileo (TNG) in the $H-$band and $K-$band, but not in the $J-$band (cite: Castro-Tirado2007).

The redshift of GRB071021 was spectroscopically measured to be $z=2.452$ (cite: Kruhler2012). The host galaxy of this GRB has been detected in, e.g., $B, V, g, I, z, K$ bands of Keck-I (cite: Perley2013a) and 100, 160, 250, 350, 500 $\mu$m of *Herschel* (cite: Hunt2014).

(cite: Perley2013a) performed SED fitting to obtain

$\rm {SFR_{SED}}$ $=190.3^{+25.6}_{-20.3}(M_{\odot}yr^{-1})$ and $M_*= 1.196^{+0.066}_{-0.088}\times10^{11}$($M_{\odot}$).

## GRB050915A host

The prompt emission was detected at 11:22:42 UT on 2005 September 15 by *Swift*-BAT (cite: Grupe2005a). It was followed up by Palomar’s 60-inch telescope (P60) and Peters Automated Infrared Imaging Telescope (PAIRITEL). P60 observed the position nine times; the first and last exposure was made 4 minutes and 40 minutes after the trigger, respectively. There was no any detection of the afterglow for all observations of P90 with filters: $R_{\rm C}$, $i$ and $z$ (cite: Cenko2009). However, the afterglow, which was actually faint, was detected 11 minutes after the burst by PAIRITEL in the $H-$band (cite: Bloom2005).

GRB050915A host galaxy was observed and detected by

e.g., Keck-I, VLT, and Spitzer (cite: Perley2013a; Hjorth2012). The host galaxy was not detected with the Australia Telescope Compact Array (ATCA) (cite: Michalowski2012).

SED fitting of GRB050915A host galaxy performed by (cite: Perley2013a) indicated that it is a dust-obscured galaxy with a high star-formation rate of $\rm SFR_{SED}$ $=135.8^{+63.1}_{-48.2}(M_{\odot}yr^{-1})$ and stellar mass of $M_*= 3.67^{+1.6}_{-1.04}\times10^{10}$($M_{\odot}$).

# Data

The host galaxies of GRB080207, GRB060814, GRB070306, GRB081221, GRB071021 and GRB050915A were observed with ALMA in projects entitled ‘Luminous, Dust-Enshrouded High-z Galaxies Selected by Gamma-Ray Bursts’ (Project code: 2015.1.00927.S for GRB080207, GRB060814 and GRB071021; and 2016.1.00768.S for GRB070306, GRB081221 and GRB050915A). In each project, three host galaxies were observed. These GRB hosts were observed with ALMA in the band 7 with four spectral windows. The bandwidth is 2 GHz for each spectral window. The host galaxy of GRB080207 was observed with ALMA on June 27, 2016; GRB060814 on June 28, 2016; GRB070306 on November 26, 2016; GRB081221 on December 14, 2016; GRB071021 on June 30, 2016; and GRB050915A on December 3, 2016. The continuum sensitivities are 0.04 $\mu$Jy and 0.02 $\mu$Jy for projects 2015.1.00927.S and 2016.1.00768.S, respectively.

The central frequencies of the spectral windows are 336.495, 338.432, 348.495, and 350.495 GHz. The average observed frequency is 343.47925 GHz corresponding to

$\lambda_{\rm obs} = 873\,\mu$m. The rest-frame wavelengths for GRB080207, GRB060814, GRB070306, GRB081221, GRB071021 and GRB050915A are 282.9, 298.7, 349.8, 267.8, 252.9 and 247.5 $\mu$m, respectively. In this work, we use the reduced data provided by the ALMA Science Center.

ALMA arranged these two projects to be observed by a 12-m antenna array.

The estimated average amounts of precipitable water vapour (PWV) are $\sim$ 1 mm during the observations of GRB080207 and GRB060814 host galaxies, and $\sim$ 0.5 mm for the rest of the host galaxies.

We detected the rest-frame FIR continuum fluxes of six host galaxies using $\it imfit$ task of CASA version 5.4.0, which allowed us to estimate fluxes, central positions, and their errors. These measurements are shown in Table [\[tab1\]](#tab1). The rest-frame FIR continuum images are also shown in Fig. [1](#fig1). The detection of GRB080207 (signal-to-noise ratio, S/N = 11), GRB060814 (S/N $\sim 16$) and GRB081221 (S/N $\sim 12$) are at the position of the host galaxies with strong detection. However, the host galaxies of GRB070306, GRB071021 and GRB050915A are marginally detected with S/Ns of $\sim5,\sim4$ and $\sim3.5$, respectively.

We collected UV-to-radio photometric data of six GRB host galaxies reported in previous studies. The multi-wavelength data with the new ALMA data of band 7 presented in this work and references are summarised in Tables [\[tab2\]](#tab2) to [\[tab7\]](#tab7).

| Parameters | GRB 080207 | GRB 060814 | GRB 070306 |
|:--:|:--:|:--:|:--:|
| Flux ($\mu$Jy) | 1430 | 145.3 | 50 |
| Uncertainty of flux ($\mu$Jy) | 130 | 9 | 11 |
| Position of detection (RA) (J2000) | $13:50:02.97 \pm 0.01$ | $14:45:21.31 \pm 0.01$ | $09:52:23.31 \pm 0.01$ |
| Position of detection (Dec) (J2000) | $+07:30:07.25 \pm 0.01$ | $+20:35:10.32 \pm 0.01$ | $+10:28:55.18 \pm 0.04$ |
| Clean beam size in major axis (arcsec) | $0.36$ | $0.35$ | $0.33$ |
| Clean beam size in minor axis (arcsec) | $0.30$ | $0.33$ | $0.31$ |
| Position angle (degree) | $83.72$ | $17.72$ | $50.50$ |

\

| Parameters | GRB 081221 | GRB 071021 | GRB 050915A |
|:--:|:--:|:--:|:--:|
| Flux ($\mu$Jy) | 735 | 422 | 308 |
| Uncertainty of flux ($\mu$Jy) | 62 | 107 | 87 |
| Position of detection (RA) (J2000) | $01:03:10.17 \pm 0.01$ | $22:42:34.3 \pm 0.1$ | $05:26:44.8 \pm 0.1$ |
| Position of detection (Dec) (J2000) | $-24:32:52.27 \pm 0.01$ | $+23:43:05.9 \pm 0.1$ | $-28:00:59.8 \pm 0.1$ |
| Clean beam size in major axis (arcsec) | $0.54$ | $0.39$ | $0.32$ |
| Clean beam size in minor axis (arcsec) | $0.38$ | $0.32$ | $0.28$ |
| Position angle (degree) | $89.97$ | $28.63$ | $34.39$ |

\
**Notes.** These measurements were calculated by $\it{imfit}$ task in CASA.

![image](080207.jpg) ![image](060814.jpg) ![image](070306.jpg) ![image](081221.jpg) ![image](071021.jpg) ![image](050915A.jpg)

+---------------------------------------------------------------------------------------------------------------------+
| GRB080207                                                                                                           |
+:=============================+:============:+:======================:+:====================:+:=====================:+
| Observed wavelength ($\mu$m) | Band         | Flux density ($\mu$Jy) | Telescope/Instrument | Reference             |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| $^{a}$                       | g            | 0.04$\pm$0.01          | Keck/LRIS            | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 0.63755$^{a}$                | R            | 0.093$\pm$0.026        | VLT/VIMOS            | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 0.75497$^{a}$                | I            | 0.17$\pm$0.05          | Keck/LRIS            | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 0.95716$^{a}$                | z$^{\prime}$ | 0.35$\pm$0.06          | Gemini/GMOS          | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 1.12037$^{a}$                | F110W        | 1.75$\pm$0.17          | HST/WFC3             | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 1.2                          | J            | 1.6$\pm$0.3            | VLT/SINFONI          | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 1.52791$^{a}$                | F160W        | 2.27$\pm$0.34          | HST/NICMOS (NIC3)    | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 2.1063$^{a}$                 | K$^{\prime}$ | 6.25$\pm$1.62          | Gemini/NIRI          | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 2.1521$^{a}$                 | Ks           | 7.3$\pm$1.0            | VLT/ISAAC            | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 3.5075$^{a}$                 | 3.6um        | 14.40$\pm$0.31         | Spitzer/IRAC         | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 4.4365$^{a}$                 | 4.5um        | 15.51$\pm$0.44         | Spitzer/IRAC         | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 5.6281$^{a}$                 | 5.7um        | 18.53$\pm$1.58         | Spitzer/IRAC         | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 7.5891$^{a}$                 | 7.9um        | 12.52$\pm$1.76         | Spitzer/IRAC         | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 23.21$^{a}$                  | 24um         | 92.43$\pm$6.50         | Spitzer/MIPS         | (cite: Hunt2011)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 97.903$^{a}$                 | 100um        | 2200$\pm$600           | *Herschel*/PACS      | (cite: Hunt2014)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 153.94$^{a}$                 | 160um        | 5900$\pm$1400          | *Herschel*/PACS      | (cite: Hunt2014)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 242.82$^{a}$                 | 250um        | $<$19500$^{c}$         | *Herschel*/SPIRE     | (cite: Hunt2014)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 340.89$^{a}$                 | 350um        | $<$20400$^{c}$         | *Herschel*/SPIRE     | (cite: Hunt2014)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 450                          | 450um        | $<$52483$^{c}$         | JCMT/SCUBA2          | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 481.38$^{e}$                 | band9        | 11900.0$\pm$1700.0     | ALMA                 | (cite: Hashimoto2019) |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 482.26$^{a}$                 | 500um        | $<$21900$^{c}$         | *Herschel*/SPIRE     | (cite: Hunt2014)      |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 642.43$^{e}$                 | band8        | 3370$\pm$180           | ALMA                 | (cite: Hashimoto2019) |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 850                          | 850um        | $<$13183$^{c}$         | JCMT/SCUBA2          | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 873$^{b}$                    | band7        | 1430$\pm$130           | ALMA                 | This work             |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 2103.4                       | band4        | 123.0$\pm$24           | ALMA                 | (cite: Hatsukade2019) |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 8137.7                       | 36.83GHz     | $<$22.4$^{c}$          | VLA                  | (cite: Svensson2012)  |
+------------------------------+--------------+------------------------+----------------------+-----------------------+
| 57322                        | 5.23GHz      | 17.1$\pm$2.5$^{d}$     | VLA                  | (cite: Perley2013b)   |
+------------------------------+--------------+------------------------+----------------------+-----------------------+

\
$^{a}$Effective wavelength retrieved from <http://svo2.cab.inta-csic.es/theory/fps3/index.php?mode=browse>.\
$^{b}$Central wavelength of the spectral windows used for the continuum image (see Fig. [1](#fig1)a).\
$^{c}$3$\sigma$ upper limit, which is not taken into account in the SED fitting analysis.\
$^{d}$NOT used in the model without radio emission in SED fitting analysis to avoid the possible contaminated flux from the long-lived afterglow.\
$^{e}$Central wavelength of the spectral windows calculated by (cite: Hashimoto2019).

+--------------------------------------------------------------------------------------------------------------------------------+
| GRB060814                                                                                                                      |
+:=============================+:======:+:======================:+:====================:+:======================================:+
| Observed wavelength ($\mu$m) | Band   | Flux density ($\mu$Jy) | Telescope/Instrument | Reference                              |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 0.54037$^{a}$                | V      | 2.27$\pm$0.22          | Keck/LRIS            | (cite: Perley2013a)                    |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 0.6550                       | R      | 2.46$\pm$0.26          | VLT/FORS2            | (cite: Perley2013a),(cite: Hjorth2012) |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 0.75497$^{a}$                | I      | 2.91$\pm$0.37          | Keck/LRIS            | (cite: Perley2013a)                    |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 1.23646$^{a}$                | F125W  | 5.32$\pm$0.79          | HST/WFC3             | (cite: Perley2013a)                    |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 1.52791$^{a}$                | F160W  | 7.28$\pm$1.08          | HST/WFC3             | (cite: Perley2013a)                    |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 2.1600                       | K      | 6.5$\pm$0.6            | VLT/ISAAC            | (cite: Perley2013a),(cite: Hjorth2012) |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 3.5075$^{a}$                 | 3.6    | 10.19$\pm$0.88         | Spitzer/IRAC         | (cite: Perley2013a)                    |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 4.4365$^{a}$                 | 4.5    | 12.25$\pm$0.82         | Spitzer/IRAC         | (cite: Perley2013a)                    |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 873$^{b}$                    | band7  | 145.3$\pm$9.0          | ALMA                 | This work                              |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 100000                       | S/3GHz | 11.34$\pm$3.12$^{d}$   | VLA                  | (cite: Perley2015)                     |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+
| 210000                       | 21cm   | $<430^{c}$             | WSRT                 | (cite: Michalowski2012)                |
+------------------------------+--------+------------------------+----------------------+----------------------------------------+

\
$^{a}$Effective wavelength retrieved from <http://svo2.cab.inta-csic.es/theory/fps3/index.php?mode=browse>.\
$^{b}$Central wavelength of the spectral windows used for the continuum image (see Fig. [1](#fig1)b).\
$^{c}$3$\sigma$ upper limit, which is not taken into account in the SED fitting analysis.\
$^{d}$NOT used in the model without radio emission in SED fitting analysis to avoid the possible contaminated flux from the long-lived afterglow.

+--------------------------------------------------------------------------------------------------------------------------------------+
| GRB070306                                                                                                                            |
+:=============================+:==========:+:======================:+:====================:+:========================================:+
| Observed wavelength ($\mu$m) | Band       | Flux density ($\mu$Jy) | Telescope/Instrument | Reference                                |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| $^{a}$                       | u          | 2.24$\pm$1.18          | SDSS                 | (cite: Perley2013a), (cite: Jaunsen2008) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.45045$^{a}$                | g          | 2.78$\pm$0.24          | GROND                | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.46404$^{a}$                | g          | 2.4$\pm$0.41           | SDSS                 | (cite: Perley2013a), (cite: Jaunsen2008) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.60980$^{a}$                | r          | 2.29$\pm$0.2           | GROND                | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.61223$^{a}$                | r          | 2.56$\pm$0.66          | SDSS                 | (cite: Perley2013a), (cite: Jaunsen2008) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.6550                       | R          | 2.46$\pm$0.21          | VLT/FORS2            | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.76047$^{a}$                | i          | 2.88$\pm$0.37          | GROND                | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.84669$^{a}$                | I          | 3.42$\pm$0.65          | NOT/ALFOSC           | (cite: Perley2013a), (cite: Jaunsen2008) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 0.89293$^{a}$                | z          | 2.71$\pm$0.46          | GROND                | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 1.23646$^{a}$                | F125W      | 6.4$\pm$0.18           | HST/WFC3             | (cite: Perley2013a)                      |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 1.2500                       | J          | 8.37$\pm$0.64          | VLT/ISAAC            | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 1.52791$^{a}$                | F160W      | 7.79$\pm$0.22          | HST/WFC3             | (cite: Perley2013a)                      |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 1.63302$^{a}$                | H          | 9.26$\pm$0.35          | GROND                | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 1.65                         | H          | 12.21$\pm$1.43         | VLT/ISAAC            | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 2.16                         | K          | 10.29$\pm$0.99         | VLT/ISAAC            | (cite: Perley2013a), (cite: Kruhler2011) |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 3.5075$^{a}$                 | 3.6        | 10.65$\pm$0.48         | Spitzer/IRAC         | (cite: Perley2013a)                      |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 4.4365$^{a}$                 | 4.5        | 12.28$\pm$0.59         | Spitzer/IRAC         | (cite: Perley2013a)                      |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 97.903$^{a}$                 | 100$\mu m$ | 4900$\pm$700           | *Herschel*/PACS      | (cite: Hunt2014)                         |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 153.94$^{a}$                 | 160$\mu m$ | 10700$\pm$2000         | *Herschel*/PACS      | (cite: Hunt2014)                         |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 873$^{b}$                    | band7      | 50$\pm$11              | ALMA                 | This work                                |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+
| 100000                       | S/3GHz     | 11.34$\pm$2.84$^{c}$   | VLA                  | (cite: Perley2015)                       |
+------------------------------+------------+------------------------+----------------------+------------------------------------------+

\
$^{a}$Effective wavelength retrieved from <http://svo2.cab.inta-csic.es/theory/fps3/index.php?mode=browse>.\
$^{b}$Central wavelength of the spectral windows used for the continuum image (see Fig. [1](#fig1)c).\
$^{c}$NOT used in the model without radio emission in SED fitting analysis to avoid the possible contaminated flux from the long-lived afterglow.

+--------------------------------------------------------------------------------------------------------------+
| GRB081221                                                                                                    |
+:=============================+:=======:+:======================:+:====================:+:===================:+
| Observed wavelength ($\mu$m) | Band    | Flux density ($\mu$Jy) | Telescope/Instrument | Reference           |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 0.43221$^{a}$                | B       | 0.24$\pm$0.03          | Keck-I/LRIS          | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 0.45045$^{a}$                | g       | 0.32$\pm$0.1           | GROND                | (cite: Afonso2008)  |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 0.47068$^{a}$                | g       | 0.36$\pm$0.06          | Keck-I/LRIS          | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 0.54037$^{a}$                | V       | 0.33$\pm$0.05          | Keck-I/LRIS          | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 0.60980                      | r       | 0.5$\pm$0.1            | GROND                | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 0.75497$^{a}$                | I       | 0.64$\pm$0.2           | Keck-I/LRIS          | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 0.76047$^{a}$                | i       | 0.65$\pm$0.29          | GROND                | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 1.03264$^{a}$                | z       | 0.96$\pm$0.14          | Keck-I/LRIS          | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 1.04317$^{a}$                | F105W   | 1.08$\pm$0.07          | HST/WFC3             | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 1.52791$^{a}$                | F160W   | 2.19$\pm$0.08          | HST/WFC3             | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 2.2003$^{a}$                 | K       | 3.66$\pm$0.46          | Gemini-N/NIRI        | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 3.5075$^{a}$                 | 3.6     | 8.02$\pm$0.77          | Spitzer/IRAC         | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 4.4365$^{a}$                 | 4.5     | 9.2$\pm$0.89           | Spitzer/IRAC         | (cite: Perley2013a) |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 873$^{b}$                    | band7   | 735$\pm$62             | ALMA                 | This work           |
+------------------------------+---------+------------------------+----------------------+---------------------+
| 57322                        | 5.23GHz | \<17.2$^{c}$           | VLA                  | (cite: Perley2013b) |
+------------------------------+---------+------------------------+----------------------+---------------------+

\
$^{a}$Effective wavelength retrieved from <http://svo2.cab.inta-csic.es/theory/fps3/index.php?mode=browse>.\
$^{b}$Central wavelength of the spectral windows used for the continuum image (see Fig. [1](#fig1)d).\
$^{c}$3$\sigma$ upper limit, which is not taken into account in the SED fitting analysis.

+----------------------------------------------------------------------------------------------------------------------------------+
| GRB071021                                                                                                                        |
+:=============================+:==========:+:======================:+:=====================================:+:===================:+
| Observed wavelength ($\mu$m) | Band       | Flux density ($\mu$Jy) | Telescope/Instrument                  | Reference           |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 0.43221$^{a}$                | B          | 0.13$\pm$0.03          | Keck-I/LRIS                           | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 0.47068$^{a}$                | g          | 0.21$\pm$0.02          | Keck-I/LRIS                           | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 0.54037$^{a}$                | V          | 0.33$\pm$0.06          | Keck-I/LRIS                           | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 0.75497$^{a}$                | I          | 0.71$\pm$0.14          | Keck-I/LRIS                           | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 1.03264$^{a}$                | z          | 0.49$\pm$0.16          | Keck-I/LRIS                           | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 1.04317$^{a}$                | F105W      | 0.75$\pm$0.07          | HST/WFC3                              | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 1.24581$^{a}$                | J          | $<1.35^{c}$            | Gemini-N/NIRI                         | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 1.52791$^{a}$                | F160W      | 1.93$\pm$0.07          | HST/WFC3                              | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 2.18186$^{a}$                | K          | 5.42$\pm$1.28          | Keck-I/NIRC2                          | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 3.5075$^{a}$                 | 3.6        | 10.33$\pm$0.4          | Spitzer/IRAC                          | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 4.4365$^{a}$                 | 4.5        | 12.26$\pm$0.47         | Spitzer/IRAC                          | (cite: Perley2013a) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 873$^{b}$                    | band7      | 422$\pm$107            | ALMA                                  | This work           |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 97.903$^{a}$                 | $100\mu m$ | \<6000$^{c,d}$         | *Herschel*/PACS                       | (cite: Hunt2014)    |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 153.94$^{a}$                 | $160\mu m$ | \<19700$^{c,d}$        | *Herschel*/PACS                       | (cite: Hunt2014)    |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 242.84$^{a}$                 | $250\mu m$ | $<$19800$^{c,d}$       | *Herschel*/SPIRE                      | (cite: Hunt2014)    |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 340.89$^{a}$                 | $350\mu m$ | $<$16200$^{c,d}$       | *Herschel*/SPIRE                      | (cite: Hunt2014)    |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 482.26$^{a}$                 | $500\mu m$ | $<$21900$^{c,d}$       | *Herschel*/SPIRE                      | (cite: Hunt2014)    |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 2861                         | 104.8GHz   | \<510$^{c}$            | Plateau de Bure Interferometer (PdBI) | (cite: Postigo2012) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 3486                         | 86GHz      | \<450$^{c}$            | PdBI                                  | (cite: Postigo2012) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+
| 57322                        | 5.23GHz    | \<25.4$^{c}$           | VLA                                   | (cite: Perley2013b) |
+------------------------------+------------+------------------------+---------------------------------------+---------------------+

\
$^{a}$Effective wavelength retrieved from <http://svo2.cab.inta-csic.es/theory/fps3/index.php?mode=browse>.\
$^{b}$Central wavelength of the spectral windows used for the continuum image (see Fig. [1](#fig1)e).\
$^{c}$3$\sigma$ upper limit, which is not taken into account in the SED fitting analysis.\
$^{d}$Indicate that the upper limits are too large values to be shown in the Fig. [2](#fig2).

+------------------------------------------------------------------------------------------------------------------------------------+
| GRB050915A                                                                                                                         |
+:=============================+:==========:+:======================:+:====================:+:======================================:+
| Observed wavelength ($\mu$m) | Band       | Flux density ($\mu$Jy) | Telescope/Instrument | Reference                              |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 0.47068$^{a}$                | g          | 0.33$\pm$0.06          | Keck-I/LRIS          | (cite: Perley2013a)                    |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 0.54037$^{a}$                | V          | 0.38$\pm$0.04          | Keck-I/LRIS          | (cite: Perley2013a)                    |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 0.6550$^{a}$                 | R          | 0.49$\pm$0.08          | VLT/FORS2            | (cite: Hjorth2012);(cite: Perley2013a) |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 0.75497$^{a}$                | I          | 0.73$\pm$0.06          | Keck-I/LRIS          | (cite: Perley2013a)                    |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 2.1600                       | K          | 3.57$\pm$0.87          | VLT/ISAAC            | (cite: Hjorth2012);(cite: Perley2013a) |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 3.5075$^{a}$                 | 3.6        | 7.86$\pm$0.76          | Spitzer/IRAC         | (cite: Perley2013a)                    |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 4.4365$^{a}$                 | 4.5        | 7.97$\pm$0.77          | Spitzer/IRAC         | (cite: Perley2013a)                    |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 873$^{b}$                    | band7      | 308$\pm$87             | ALMA                 | This work                              |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 33300                        | 4-cm band  | \<37$^{c}$             | ATCA                 | (cite: Michalowski2012)                |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 54500                        | 4-cm band  | \<44$^{c}$             | ATCA                 | (cite: Michalowski2012)                |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+
| 216000                       | 16-cm band | \<59$^{c}$             | ATCA                 | (cite: Michalowski2012)                |
+------------------------------+------------+------------------------+----------------------+----------------------------------------+

\
$^{a}$Effective wavelength retrieved from <http://svo2.cab.inta-csic.es/theory/fps3/index.php?mode=browse>.\
$^{b}$Central wavelength of the spectral windows used for the continuum image (see Fig. [1](#fig1)f).\
$^{c}$3$\sigma$ upper limit, which is not taken into account in the SED fitting analysis.

# SED Modelling and results

`CIGALE`[^2] (cite: Burgarella2005; Noll2009; Boquien2019) was designed to study the evolution of galaxies. `CIGALE` allowed us to investigate the physical properties such as SFR, stellar mass, IR luminosity, and dust mass of galaxies by comparing the SEDs of modelled galaxies to observed galaxies.

It provides a large number of different models with different star-formation histories, AGNs, nebular emissions and dust emissions.

We used `CIGALE` (version: 2018.0) to perform the SED fitting. The best fit models are shown in Fig. [2](#fig2). In this paper, we chose a single exponential star formation history (sfh2exp hereafter) and delayed SFH with optional exponential burst (sfhdelayed hereafter) to simulate star-formation history (SFH) model, (cite: Bruzual2003) (hereafter bc03) to model the single stellar populations (SSP), ‘nebular’ for nebular emission model, ‘dustatt_powerlaw’ for dust attenuation model, and ‘redshifting’ for redshift+IGM model. We used the module from (cite: Dale2014) for AGN and dust emission models except for GRB050915A because the reduced $\chi^2$ was too large for this host when this model was applied. For GRB050915A, we selected the model by (cite: Draine2014) for dust emission and (cite: Fritz2006) for the AGN component. The module we used and the parameters setting are shown in Tables [\[tab8\]](#tab8) and [\[tab9\]](#tab9).

The SFRH of sfh2exp is assumed in `CIGALE` as follows: $$\begin{equation}
    \label{eq1}
    \rm SFR( \it t)\propto \left\{
    \begin{aligned}
    \rm exp(\it -t/\tau_{0}) & \quad \rm if \quad \it t<t_{0}-t_{1}\\
    \rm exp(\it -t/\tau_{0})+k\times \rm exp(\it -t/\tau_{1}) & \quad \rm if \quad \it t\ge t_{0}-t_{1} \\
    \end{aligned}
    \right.
    
\end{equation}$$ where $t_0$ is the time when the galaxy started forming stars and $t_1$ is the time when the burst of star formation occurs. $k$ is the relative amplitude of the second exponential. $\tau_0$ and $\tau_1$ represent the e$-$folding times of the main stellar populations and the late starburst population model, respectively (cite: Boquien2019).

We also assumed delayed SFH in `CIGALE`: $$\begin{equation}
    \label{eq2}
    \rm SFR( \it t)\propto t/\tau^2 \times {\rm exp}(-t/\tau) \quad {\rm for} \quad 0\le t\le t_o, 
    
\end{equation}$$ where $t_o$ means the onset of star formation and $\tau$

is the time when SFR peaks (cite: Boquien2019).

Furthermore, stellar spectra were computed by `CIGALE` from both SFH model and SSP model. SSP($\lambda$,t) were calculated at the age $t$ and wavelength $\lambda$ as the spectrum of a single population. The spectrum S($\lambda$) of the object of interest is $\sum_{t} {\rm SSP}(\lambda,t)\times {\rm SFH}(t)$, where ${\rm SFH}(t)$ is the star-formation rate at age $t$.

We used nebular modules,

following (cite: Inoue2010) and (cite: Inoue2011), to deal with the emission line template.

Based on the model from (cite: Charlot2000), ‘dustatt_powerlaw’ module provides a single power law for both young and old stars.

`CIGALE` provided three types of modules to model dust emission. One of the newest is (cite: Dale2014), which can adjust the parameters such as AGN fraction and alpha slope. Based on (cite: Dale2002), the module (cite: Dale2014) in `CIGALE` presents the dust templates which are based on a sample of adjacent star-forming galaxies. The other option of dust emission we also selected is (cite: Draine2014) (dl2014 in `CIGALE`). This model is refined in detail from

(cite: Draine2007). This model tries to produce a galaxy with extinction curve by considering a mixture of amorphous silicate and graphitic grains in the galaxy.

The AGN model we applied for GRB050915A is (cite: Fritz2006). This model analyzes the thermal dust emission and scattered emission by dust in the toroidal structure surrounding the AGN.

We also used the redshifting module by `CIGALE`. Based on the previous study (cite: Meiksin2006), redshifting module not only redshifts the spectrum by multiplying the wavelengths by $1+z$ and dividing the spectrum with $z+1$, but also considers the absorption of the radiation in short wavelengths by the intergalactic medium.

We classified our GRB host galaxies into two groups: Group A with radio detection (GRB080207, GRB060814 and GRB070306) and Group B without radio detection (GRB081221, GRB071021 and GRB050915A). For all host galaxies, we selected two IMFs to model the best-fit spectrum: (cite: Salpeter1955) and (cite: Chabrier2003). We also used the four configurations of the model setting, with and without AGN component, and then with and without the radio data and radio emission for Group A. For Group B, we tested the condition with and without AGN component for best template. The results under these conditions with reduced $\chi^{2}$ are shown in Table [\[tab10\]](#tab10) for Group A and Table [\[tab11\]](#tab11) for Group B.

Based on the reduced $\chi^2$, we selected the best-fit galaxy template from the conditions mentioned in the previous paragraph. However, we caution readers that our terminology of “best" is in the sense that in some cases there exist other templates with similar reduced $\chi^2$ values. Therefore, in such a case, we do not strongly exclude physical properties derived from other configurations in the SED fittings. The photometry including the ALMA data were fitted successfully with reduced $\chi^2$ of 2.32, 1.00, 2.34, 0.94, 0.99 and 0.97 for GRB080207, GRB060814, GRB070306, GRB081221, GRB071021 and GRB050915A host galaxies, respectively.

We reproduced the observed SEDs with `CIGALE` and obtain the physical properties such as SFR, dust luminosity, and stellar mass. The derived physical properties are compared with previous works (cite: Hunt2014; Hashimoto2019; Perley2013a; Perley2015; Kruhler2011) in Table [\[tab12\]](#tab12) for Group A and Table [\[tab13\]](#tab13) for Group B.

![image](GRB080207_L.jpg) ![image](GRB060814_L.jpg) ![image](GRB070306_L.jpg) ![image](GRB081221_L.jpg) ![image](GRB071021_L.jpg) ![image](GRB050915A_L.jpg) ![image](legend.jpg)

+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
|                                     | GRB080207                 | GRB060814                                      | GRB070306                         |
+:===================================:+:=========================:+:==============================================:+:=================================:+
| Parameter                           | Value                                                                                                          |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
|                                     | SFH(sfh2exp)                                                                                                   |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
| $\tau_{\rm main}$                   | 2,4,5,8,10                | 250, 500, 1000, 2000, 4000, 6000, 8000         | 5000, 7000, 10000, 12000          |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
| $\tau_{\rm burst}$                  | 25,50,75                  | 50                                                                                 |
+-------------------------------------+---------------------------+------------------------------------------------------------------------------------+
| $f_{\rm burst}$                     | 0.01                                                                                                           |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
| age                                 | 2100,2125,2150            | 250, 500, 1000, 2000, 4000, 8000, 10000, 12000 | 1000, 2000, 3000, 5000            |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
| ${\rm burst}_{\rm age}$             | 20                                                                                                             |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| ${\rm SFR}_{0}$                     | 1.0                                                                                                            |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
|                                     | SSP(cite: Bruzual2003)                                                                                         |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| IMF                                 | (cite: Salpeter1955) and (cite: Chabrier2003)                                                                  |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Metallicity                         | 0.02                                                                                                           |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| ${\rm separation}_{\rm age}$        | 10                                                                                                             |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
|                                     | Nebular                                                                                                        |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| logU                                | -2.0                                                                                                           |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| $f_{\rm esc}$                       | 0.0                                                                                                            |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| ${f}_{\rm dust}$                    | 0.0                                                                                                            |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| ${\rm lines}_{\rm width}$           | 0.0                                                                                                            |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
|                                     | Dust attenuation                                                                                               |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| $\rm Av_{young}$                    | 0.0, 0.5, 1.0, 1.5, 2.0, 2.5, 3.0                                                                              |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| ${\rm Av\_old\_factor}$             | 0.44                                                                                                           |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| uv_bump_wavelength                  | 217.5                                                                                                          |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| uv_bump_width                       | 35.0                                                                                                           |
+-------------------------------------+----------------------------------------------------------------------------+-----------------------------------+
| uv_bump_amplitude                   | 0.0, 1.0, 2.0, 3.0                                                         | 0.0, 0.5, 1.0, 1.5, 2.0, 2.5, 3.0 |
+-------------------------------------+----------------------------------------------------------------------------+-----------------------------------+
| power_slope                         | -0.7                                                                       | -0.4, -0.7                        |
+-------------------------------------+----------------------------------------------------------------------------+-----------------------------------+
|                                     | Dust emission(cite: Dale2014)                                                                                  |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
| AGN fraction$^{a}$ ($\times 10000$) | 1, 5, 8, 10, 15, 20, 30   | 10, 20, 50, 100, 150, 200, 500, 1000           | 10, 20, 50, 100, 200, 500, 1000   |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
| $\alpha$ slope                      | 1.0, 1.25, 1.5, 1.75, 2.0 | 1.0, 1.5, 2.0, 2.5                             | 0.5, 1.0, 2.0, 3.0, 4.0           |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
|                                     | Radio$^{b}$                                                                                                    |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| $\alpha_{\rm radio}$                | 0.6, 0.7, 0.8, 0.9, 1.0                                                                                        |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------+
| qir                                 | 2.58                                                                                                           |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+
|                                     |                           |                                                |                                   |
+-------------------------------------+---------------------------+------------------------------------------------+-----------------------------------+

\
**Notes.** Detailed definition of these parameters are described in Appendix C of (cite: Boquien2019)\
$^{a}$In only radio emission condition and none of those two, AGN fraction set to 0.\
$^{b}$In only AGN condition and none of those two, we did not use radio module.

+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+
|                                     | GRB081221                                   | GRB071021                              | GRB050915A                    |
+:===================================:+:===========================================:+:======================================:+:=============================:+
| Parameter                           | Value                                                                                                                |
+-------------------------------------+---------------------------------------------+------------------------------------------------------------------------+
| SFH                                 | sfhdelayed                                  | sfh2exp                                                                |
+-------------------------------------+---------------------------------------------+------------------------------------------------------------------------+
| $\tau_{\rm main}$                   | 1000,1500,2000,2500                         | 250,400,500,750,1000                                                   |
+-------------------------------------+---------------------------------------------+------------------------------------------------------------------------+
| $\tau_{\rm burst}$                  | 50                                                                                                                   |
+-------------------------------------+---------------------------------------------+------------------------------------------------------------------------+
| $f_{\rm burst}$                     | 0.0                                         | 0.01                                                                   |
+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+
| age                                 | 1000,1500,2000,2500,3000,3500,4000          | 250, 500, 1000, 1500, 2000, 2500, 4000 | 250,500,750,100,1250,1500     |
+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+
| ${\rm burst}_{\rm age}$             | 20                                                                                                                   |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| ${\rm SFR}_{0}$                     | 1.0                                                                                                                  |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
|                                     | SSP(cite: Bruzual2003)                                                                                               |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| IMF                                 | (cite: Salpeter1955) and (cite: Chabrier2003)                                                                        |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
| Metallicity                         | 0.05                                                                                 | 0.0001                        |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
| ${\rm separation}_{\rm age}$        | 10                                                                                                                   |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
|                                     | Nebular                                                                                                              |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| logU                                | -2.0                                                                                                                 |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| $f_{\rm esc}$                       | 0.0                                                                                                                  |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| ${f}_{\rm dust}$                    | 0.0                                                                                                                  |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| ${\rm lines}_{\rm width}$           | 0.0                                                                                                                  |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
|                                     | Dust attenuation                                                                                                     |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| $\rm Av_{young}$                    | 0.0, 0.5, 1.0, 1.5, 2.0, 2.5, 3.0                                                                                    |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| ${\rm Av\_old\_factor}$             | 0.44                                                                                                                 |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| uv_bump_wavelength                  | 217.5                                                                                                                |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| uv_bump_width                       | 35.0                                                                                                                 |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| uv_bump_amplitude                   | 0.0, 1.0, 2.0, 3.0                                                                                                   |
+-------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| power_slope                         | -0.7                                                                                                                 |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
|                                     | Dust emission(cite: Dale2014)                                                        | (cite: Draine2014)            |
+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+
| AGN fraction$^{a}$ ($\times 10000$) | 9,10,11,50,100,1000                         | 50,100,200,500                         | none                          |
+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+
| $\alpha$ slope                      | 1.8750,1.9375,2.0,2.0625,2.1250,2.1875,2.25 | 1.25,1.375,1.5,1.625,1.75,2,2.25       | none                          |
+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+
| qpah                                | none                                                                                 | 0.47,1.12,1.77,2.5            |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
| umin                                | none                                                                                 | 0.1,1,2,3,4,5,10,15,20,25,30  |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
| $\alpha$                            | none                                                                                 | 2.2,2.3,2.4,2.5,2.6,2.7,2.8   |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
| $\gamma$                            | none                                                                                 | 0.1,0.2,0.3,0.4               |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
|                                     | AGN$^{a}$(cite: Fritz2006)                                                                                           |
+-------------------------------------+--------------------------------------------------------------------------------------+-------------------------------+
| AGN fraction ($\times 10000$)       | none                                                                                 | 10,90,100,300,350,400,450,500 |
+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+
|                                     |                                             |                                        |                               |
+-------------------------------------+---------------------------------------------+----------------------------------------+-------------------------------+

\
**Notes.** Detailed definition of these parameters are described in Appendix C of (cite: Boquien2019)\
$^{a}$This module is only present for the AGN configuration

# Discussion

We discuss the best-fit spectra in different model settings. The configurations contain on-off options of AGN and radio components for Group A. For Group B, we discuss the results with and without the AGN component. Here, we consider the AGN component because some GRB hosts actually indicate hints of AGNs (cite: Hatsukade2019). The options to include and exclude radio data are due to a possible contamination from a long-lived radio afterglow in the radio flux of the host galaxy (cite: Perley2013b). The physical parameters and results are shown in Tables [\[tab10\]](#tab10) and [\[tab11\]](#tab11) for each GRB host galaxy. In addition, we also compare our results with previous papers in Tables [\[tab12\]](#tab12) and [\[tab13\]](#tab13).

GRB host galaxies could have different stellar IMFs compared to a normal galaxy (cite: Hashimoto2019). As a result, it is important to model the IMF for each host galaxy. For this purpose, we tested different IMFs from (cite: Salpeter1955) and (cite: Chabrier2003). We simply decide the better fit by comparing the reduced $\chi^2$ between these two different IMFs. We caution readers that our testing scheme is very simple, and therefore, the IMF differences could be masked by the simplifications of the model.

For fair comparisons, we converted the derived physical properties of those with the same IMF in previous studies by the factor from (cite: Madau2014). The differences are shown in Tables [\[tab12\]](#tab12) and [\[tab13\]](#tab13) after the conversion of IMF.

## Group A (Radio detected hosts)

### GRB080207 host galaxy

We compare reduced $\chi^2$ derived from different configurations of the SED fitting for the GRB 080207 host. We found that the best-fit SED contains an AGN component excluding the radio emission with the smallest reduced $\chi^2$ value of 2.32. The flux upper limits reported in previous studies are consistent with the best-fit template (Fig. [2](#fig2)). The AGN fraction of the best-fit model is $0.0012\pm0.0007$. Comparing with the fitting of model which does not contain the AGN component, the best-fit template is better in the short wavelengths of observed data. If the radio data and model of radio emission are included in the fitting procedure, the reduced $\chi^2$ becomes larger. One possible reason is that a long-lived radio afterglow has contaminated the radio flux (cite: Perley2013b). The SFR of the best-fit template including the AGN component is $397\pm20 M_{\odot}$ yr$^{-1}$, which is slightly lower than SFRs of other models without AGN component (Table [\[tab10\]](#tab10)).

To check the SFRs derived by SED fittings, we use the empirical formula between IR luminosity and SFR in (cite: Kennicutt1998b):

$$\begin{equation}
    \label{eq3}
    {\rm SFR_{Kennicutt}} (M_{\odot} {\rm yr}^{-1})=4.5\times10^{-44}L_{\rm IR}({\rm ergs}^{-1}).
    
\end{equation}$$

This equation is equivalent to $$\begin{equation}
    \label{Kennicutt1998}
    {\rm SFR_{Kennicutt}}(M_{\odot} {\rm yr}^{-1})=1.722\times10^{-10}L_{\rm IR}(L_{\odot}).
    
\end{equation}$$

The IR luminosity in (cite: Kennicutt1998b) is defined as the luminosity integrated from 8 to 1000 $\mu$m. We defined the IR luminosity of our results as the luminosity emitted by dust, which is almost similar to $L_{IR}$ in most of the star-forming galaxies.

The SFRs derived from Eq. [\[Kennicutt1998\]](#Kennicutt1998) are 305, 313, and 310 $M_{\odot}$ yr$^{-1}$ for the models including AGN, radio emission, and both, respectively. The SFR of the best-fit template derived by `CIGALE`, $397\pm20 M_{\odot}$ yr$^{-1}$, is closer to these values than that of other templates in Table [\[tab10\]](#tab10).

In Table [\[tab10\]](#tab10), the Salpeter IMF (cite: Salpeter1955) fits the observed SED better for all of the four model configurations. The derived IR luminosities and stellar masses are consistent between all of the model settings.

We also demonstrate the fitting and results from (cite: Hunt2014) and (cite: Hashimoto2019) in Table [\[tab12\]](#tab12). In order to compare with previous works, we scale our estimations of SFR and stellar mass of GRB080207 host galaxy to (cite: Chabrier2003) IMF by using a conversion factor in (cite: Madau2014). After comparing our stellar mass value with previous works, we conclude that our stellar mass is closer to the estimation in (cite: Hashimoto2019).

Interestingly, all of the four different conditions suggest that this host galaxy is an ULIRG because its IR luminosity is larger than $10^{12}L_{\odot}$, which is consistent with both previous papers.

However, the SFR derived by the SED fitting in this work is much higher ($\sim 50\%$ to $\sim 100\%$) than that in both (cite: Hunt2014) and (cite: Hashimoto2019).

The IR luminosity of the best-fit template corresponds to $\rm{SFR}_{Kennicutt}=305(M_{\odot} yr^{-1})$ assuming Kennicutt’s law (Eq. [\[Kennicutt1998\]](#Kennicutt1998)). This value is much closer to the SFR derived from the SED fitting analysis in this work than that in previous papers. Our new SFR measurement is more reasonable than that in previous studies if GRB hosts follows the Kennicutt’s law. The reason for the difference is due to the new ALMA data. The ALMA data allowed us to cover the wavelength around the peak of the SED of dust thermal emission (Fig. [2](#fig2)), which results in a more reliable measurement of SFR.

### GRB060814 host galaxy

We present physical parameters of the best-fit SED template of the GRB060814 host galaxy in Table [\[tab10\]](#tab10). A comparison between this work and previous works is summarised in Table [\[tab12\]](#tab12). The physical parameters of the best-fit template are ${\rm SFR_{SED}}=56\pm9M_{\odot}$ yr$^{-1}$ and $M_{*}=(2.68\pm0.76)\times10^{10}M_{\odot}$. The reduced $\chi^2$ is 1.00 which is the closest to 1 in our four conditions.

The flux upper limits reported in previous studies are consistent with the best-fit template (Fig. [2](#fig2)). The models fit the observed SED better with the (cite: Chabrier2003) than (cite: Salpeter1955), except for the model including both AGN and radio components.

If the radio emission is not included in the SED-fitting, the reduced $\chi^2$ becomes smaller than 1.0, suggesting over-fitting. Including both AGN component and radio emission also seems to cause the over-fitting with a reduced $\chi^{2}$ of 0.53. Only the model with radio emission without AGN component provides the best-fit template with a reasonable reduced $\chi^{2}$.

In general, an ideal fitting should correspond to a reduced $\chi^2$ of 1.0 if all the errors are estimated perfectly.

However this is probably not the case in our analysis.

Therefore, we demonstrate all the results derived from the four different model configurations in Table [\[tab10\]](#tab10).

We also estimated SFRs of the host galaxy from the IR luminosity and Kennicutt’s law in the same manner as the GRB 080207 host galaxy.

The estimated SFRs are 54, 69, and 66 $M_{\odot}$ yr$^{-1}$ for model configurations including AGN, radio, and both, respectively.

We also compared the parameters derived from our best fit and from previous works.

In this work, the stellar mass of the best-fit template is $M_{*}=(2.68\pm0.76) \times 10^{10} M_{\odot}$.

This value is consistent with $M_{*}=1.6^{+1.4}_{-0.6}\times 10^{10} M_{\odot}$ in (cite: Perley2015), which is an updated value compared to

(cite: Perley2013a).

The SFR derived from the best-fit template is $56\pm9 M_{\odot}$ yr$^{-1}$, which

is much lower than ${\rm SFR_{SED}}=238.2^{+49.6}_{-24.0}$ and $209^{+27}_{-53} M_{\odot}$ yr$^{-1}$

from

(cite: Perley2013a; Perley2015).

Since the previous works lack the rest-frame FIR continuum data, they probably overestimated the SFR. The ALMA detection in the rest-frame FIR of the host galaxy enabled us to calculate the SFR more accurately.

The SFR derived from the SED fitting in `CIGALE` (${\rm SFR_{SED}}=56\pm9 M_{\odot}$ yr$^{-1}$) is closer to the estimation using Kennicutt’s law (SFR$_{\rm Kennicutt}=69 M_{\odot}$ yr$^{-1}$) compared to previous studies.

### GRB070306 host galaxy

The GRB070306 host galaxy is faint in the rest-frame FIR and marginally detected with ALMA. We performed SED fittings for the GRB070306 host galaxy. The physical properties are shown in Table [\[tab10\]](#tab10) including parameters from different model settings.

In all cases, the (cite: Chabrier2003) IMF performs better than the (cite: Salpeter1955) IMF.

The reduced $\chi^2$ values are almost the same for all configurations, but the smallest reduced $\chi^{2}$ value was attained in the model without AGN and radio component, which is 2.324.

Physical parameters of the best-fit template are ${\rm SFR_{SED}}=38\pm2 M_{\odot}$ yr$^{-1}$, $M_{*}=(3.05\pm0.44)\times 10^{10} M_{\odot}$, and $L_{\rm IR}=(2.59\pm0.26)\times 10^{11} L_{\odot}$. The stellar masses, SFRs and IR luminosities derived from all the four conditions are consistent within errors.

The derived IR luminosities for the four settings correspond to SFR$_{\rm Kennicutt}=44$ to $46 M_{\odot}$ yr$^{-1}$ assuming the Kennicutt’s law.

The best-fit template indicates SFR$_{\rm Kennicutt}=45 M_{\odot}$ yr$^{-1}$. This value is similar to the ${\rm SFR_{SED}}=38\pm2 M_{\odot}$ yr$^{-1}$ derived from our SED fitting analysis in contrast to ${\rm SFR_{SED}}=12.59^{+12.53}_{-4.65}, 144.1$, and $17^{+7}_{-5} M_{\odot}$ yr$^{-1}$ in previous works (cite: Kruhler2011; Hunt2014; Perley2015).

The SFR$_{\rm SED}=38 M_{\odot}$ yr$^{-1}$ is slightly larger than that in (cite: Perley2015), i.e., $SFR={\rm SFR_{SED}}17^{+7}_{-5} M_{\odot}$ yr$^{-1}$. The difference of SFR is probably due to the new ALMA data in this work.

## Group B (Radio non-detected hosts) 

For Group B, due to the non-detection of radio in previous studies, we did not include the radio emission in the procedure of SED fitting. We discuss the comparison of the remaining three GRB hosts: GRB081221, GRRB071021 and GRB050915A in Table [\[tab13\]](#tab13).

These three hosts have similar redshifts and optical faintnesses. They show higher stellar masses and SFRs in previous works (cite: Michalowski2012; Perley2013a; Hunt2014).

### GRB081221 host galaxy

Our results show that, if we consider the AGN component in our fitting process, the reduced $\chi^2$ becomes smaller, suggesting over-fitting. An ideal fitting should correspond to a reduced $\chi^2$ of 1.0 if all the errors are estimated perfectly. As a result, we show the results for the configuration with AGN component in Table [\[tab11\]](#tab11).

Our results show that (cite: Salpeter1955) IMF is better. In order to compare with previous work (cite: Perley2013a), we convert our stellar mass and SFR value from (cite: Salpeter1955) to (cite: Chabrier2003) by the factor from (cite: Madau2014). The stellar mass is consistent with that in (cite: Perley2013a) within the uncertainties. However, for the SFR values,

our value is lower than previous work. When we transform our $L_{\rm IR}$ to SFR through (cite: Kennicutt1998b),

we obtained approximately $\rm{SFR}_{Kennicutt}=52\pm3(M_{\odot}yr^{-1})$ which is very close to our estimation ${\rm SFR_{SED}}=56(M_{\odot}yr^{-1})$. The reason for the difference between our work and previous works is probably that no FIR detection was included in previous works, causing their SFR to be overestimated. Therefore, the new FIR detection from ALMA gives us more accurate SFR values if the host galaxy follows the Kennicutt law.

### GRB071021 host galaxy

Based on the reduced $\chi^2$, if we add the AGN component to this modelling, the resulting fit is also an over-fit.

The reduced $\chi^2$ with AGN is 0.68 and without AGN is 0.99. The results of two conditions with and without AGN component are summarised in Table [\[tab11\]](#tab11). The IMF configuration

of (cite: Chabrier2003) performed better in the two conditions.

Here we compare our results involving stellar mass, SFR, and dust luminosity to those in (cite: Hunt2014) and (cite: Perley2013a) in Table [\[tab13\]](#tab13). The stellar mass is consistent within the uncertainty between (cite: Perley2013a) and ours. The SFR values in the three previous works differ from each other, and comparing them with our result shows that our value ${\rm SFR_{SED}}=90\pm5(M_{\odot}yr^{-1})$ is the lowest. The SFR transformation of IR luminosity by (cite: Kennicutt1998b) indicates $\rm{SFR}_{Kennicutt}= 129\pm28(M_{\odot}yr^{-1})$ which is very close to our results compared with previous studies. Moreover, there was no FIR photometry included in previous works, which is probably the cause of over-estimation of SFR values.

### GRB050915A host galaxy

In this host galaxy, we found several candidates for the host galaxy (Fig. [1](#fig1)f). We chose the closest one between the candidate and the host position. The separation between the two is $0.17$ arcsec.

We performed again the setting for two configurations: with and without AGN component. The results show

an over-fit when we added the AGN component (reduced $\chi^2$ = 0.47). However, the reduced $\chi^2$ value is $0.97$ when we removed the AGN component. Physical parameters revealed by SED fitting using these two configurations are shown in Table [\[tab11\]](#tab11) with the better IMF configuration by (cite: Chabrier2003).

There are significant differences in stellar masses and SFRs between this work and (cite: Perley2013a). Also, the transformation by using (cite: Kennicutt1998b) shows that $\rm{SFR}_{Kennicutt}=148\pm7(M_{\odot}yr^{-1})$. This value is slightly larger compared to all the previous results and our results. In this work, the new photometry of the host galaxy with ALMA and previous upper limits are consistent with the best-fit template. The derived SFR including the rest-frame FIR data is likely to be more reliable than that in previous studies.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GRB 080207                                                                                                                                                            |
+:=================================:+:==============================:+:==============================:+:==============================:+:==============================:+
| Physical parameters               | AGN$^{a}$                      | Radio emission                 | Both                           | None of these two              |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | $(3.25\pm{0.16})\times10^{11}$ | $(3.32\pm{0.17})\times10^{11}$ | $(3.29\pm{0.17})\times10^{11}$ | $(3.29\pm{0.17})\times10^{11}$ |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $397\pm{20}$                   | $409\pm{20}$                   | $405\pm{20}$                   | $402\pm{20}$                   |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) | $(1.77\pm{0.09})\times10^{12}$ | $(1.82\pm{0.09})\times10^{12}$ | $(1.80\pm{0.09})\times10^{12}$ | $(1.80\pm{0.09})\times10^{12}$ |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Better IMF                        | (cite: Salpeter1955)           | (cite: Salpeter1955)           | (cite: Salpeter1955)           | (cite: Salpeter1955)           |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Reduced $\chi^2$                  | 2.32                           | 2.56                           | 2.46                           | 2.45                           |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+

\

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GRB 060814                                                                                                                                                            |
+:=================================:+:==============================:+:==============================:+:==============================:+:==============================:+
| Physical parameters               | AGN                            | Radio emission$^{a}$           | Both                           | None of these two              |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | $(3.02\pm{0.83})\times10^{10}$ | $(2.68\pm{0.76})\times10^{10}$ | $(4.44\pm{1.32})\times10^{10}$ | $(3.08\pm{0.81})\times10^{10}$ |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $48\pm{9}$                     | $56\pm{9}$                     | $85\pm{14}$                    | $47\pm{10}$                    |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) | $(3.15\pm{1.14})\times10^{11}$ | $(4.03\pm{1.07})\times10^{11}$ | $(3.85\pm{1.05})\times10^{11}$ | $(3.05\pm{1.16})\times10^{11}$ |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Better IMF                        | (cite: Chabrier2003)           | (cite: Chabrier2003)           | (cite: Salpeter1955)           | (cite: Chabrier2003)           |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Reduced $\chi^2$                  | 0.42                           | 1.00                           | 0.9                            | 0.53                           |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+

\

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GRB 070306                                                                                                                                                            |
+:=================================:+:==============================:+:==============================:+:==============================:+:==============================:+
| Physical parameters               | AGN                            | Radio emission                 | Both                           | None of these two$^{a}$        |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | $(2.99\pm{0.45})\times10^{10}$ | $(3.07\pm{0.46})\times10^{10}$ | $(3.02\pm{0.47})\times10^{10}$ | $(3.05\pm{0.44})\times10^{10}$ |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $38\pm{2}$                     | $39\pm{2}$                     | $38\pm{2}$                     | $38\pm{2}$                     |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) | $(2.58\pm{0.26})\times10^{11}$ | $(2.67\pm{0.20})\times10^{11}$ | $(2.66\pm{0.22})\times10^{11}$ | $(2.59\pm{0.26})\times10^{11}$ |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Better IMF                        | (cite: Chabrier2003)           | (cite: Chabrier2003)           | (cite: Chabrier2003)           | (cite: Chabrier2003)           |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+
| Reduced $\chi^2$                  | 2.34                           | 2.39                           | 2.40                           | 2.34                           |
+-----------------------------------+--------------------------------+--------------------------------+--------------------------------+--------------------------------+

\
$^{a}$Indicates that this model setting has the closest reduced $\chi^2$ value to 1, and further discussed in this paper.

+------------------------------------------------------------------------------------------------------+
| GRB 081221                                                                                           |
+:=================================:+:==============================:+:===============================:+
| Physical parameters$^{a}$         | AGN                            | No AGN$^{b}$                    |
+-----------------------------------+--------------------------------+---------------------------------+
| Stellar mass ($M_{\odot}$)        | $(6.54\pm{0.74})\times10^{10}$ | $(6.24\pm{0.31})\times10^{10}$  |
+-----------------------------------+--------------------------------+---------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $54\pm{3}$                     | $56\pm{3}$                      |
+-----------------------------------+--------------------------------+---------------------------------+
| Total IR luminosity ($L_{\odot}$) | $(2.95\pm{0.15})\times10^{11}$ | $(3.04\pm{+0.15})\times10^{11}$ |
+-----------------------------------+--------------------------------+---------------------------------+
| Better IMF                        | (cite: Salpeter1955)           | (cite: Salpeter1955)            |
+-----------------------------------+--------------------------------+---------------------------------+
| Reduced $\chi^2$                  | 0.82                           | 0.94                            |
+-----------------------------------+--------------------------------+---------------------------------+

\

+-----------------------------------------------------------------------------------------------------+
| GRB 071021                                                                                          |
+:=================================:+:==============================:+:==============================:+
| Physical parameters$^{a}$         | AGN                            | No AGN$^{b}$                   |
+-----------------------------------+--------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | $(2.24\pm{0.31})\times10^{11}$ | $(1.21\pm{0.15})\times10^{11}$ |
+-----------------------------------+--------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $133\pm{14}$                   | $90\pm{5}$                     |
+-----------------------------------+--------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) | $(6.89\pm{0.68})\times10^{11}$ | $(7.48\pm{1.63})\times10^{11}$ |
+-----------------------------------+--------------------------------+--------------------------------+
| Better IMF                        | (cite: Salpeter1955)           | (cite: Chabrier2003)           |
+-----------------------------------+--------------------------------+--------------------------------+
| Reduced $\chi^2$                  | 0.68                           | 0.99                           |
+-----------------------------------+--------------------------------+--------------------------------+

\

+-----------------------------------------------------------------------------------------------------+
| GRB 050915A                                                                                         |
+:=================================:+:==============================:+:==============================:+
| Physical parameters$^{a}$         | AGN                            | No AGN$^{b}$                   |
+-----------------------------------+--------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | $(9.73\pm{1.94})\times10^{10}$ | $(9.56\pm{0.48})\times10^{10}$ |
+-----------------------------------+--------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $77\pm{9}$                     | $77\pm{4}$                     |
+-----------------------------------+--------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) | $(5.99\pm{0.62})\times10^{11}$ | $(8.58\pm{0.43})\times10^{11}$ |
+-----------------------------------+--------------------------------+--------------------------------+
| Better IMF                        | (cite: Chabrier2003)           | (cite: Chabrier2003)           |
+-----------------------------------+--------------------------------+--------------------------------+
| Reduced $\chi^2$                  | 0.47                           | 0.97                           |
+-----------------------------------+--------------------------------+--------------------------------+

\
$^{a}$Notice that this GRB did not have radio detection, so here we do not include radio emission.\
$^{b}$Indicates that this model setting has the closest reduced $\chi^2$ value to 1, and further discussed in this paper.

+---------------------------------------------------------------------------------------------------------------------------------------+
| GRB 080207                                                                                                                            |
+:=================================:+:=====================:+:========================================:+:==============================:+
| Physical parameters               | (cite: Hunt2014)      | (cite: Hashimoto2019)                    | Best-fit(AGN)                  |
+-----------------------------------+-----------------------+------------------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | 1.48$\times 10^{11}$  | (1.70$^{+0.08}_{-0.35}$)$\times 10^{11}$ | $(1.98\pm{0.10})\times10^{11}$ |
+-----------------------------------+-----------------------+------------------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | 170.1                 | 123.40$^{+25.19}_{-21.78}$               | $250\pm{13}$                   |
+-----------------------------------+-----------------------+------------------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) | 1.78 $\times 10^{12}$ | (1.82$\pm{0.23}$) $\times 10^{12}$       | $(1.77\pm{0.09})\times10^{12}$ |
+-----------------------------------+-----------------------+------------------------------------------+--------------------------------+
| IMF                               | $S2C^{1.8}$           | (cite: Chabrier2003)                     | $S2C^{M}$                      |
+-----------------------------------+-----------------------+------------------------------------------+--------------------------------+

\

+-----------------------------------------------------------------------------------------------------------------------------------------------+
| GRB 060814                                                                                                                                    |
+:=================================:+:==================================:+:===================================:+:==============================:+
| Physical parameters               | (cite: Perley2013a)                | (cite: Perley2015)                  | Best-fit(Radio)                |
+-----------------------------------+------------------------------------+-------------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | $(9.8^{+0.9}_{-0.2})\times 10^{9}$ | $(1.6^{+1.4}_{-0.6})\times 10^{10}$ | $(2.68\pm{0.76})\times10^{10}$ |
+-----------------------------------+------------------------------------+-------------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $238.2^{+49.6}_{-24.0}$            | $209^{+27}_{-53}$                   | $56\pm{9}$                     |
+-----------------------------------+------------------------------------+-------------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) |                                    |                                     | $(4.03\pm{1.07})\times10^{11}$ |
+-----------------------------------+------------------------------------+-------------------------------------+--------------------------------+
| IMF                               | $S2C^{1.8}$                        | $S2C^{1.6}$                         | (cite: Chabrier2003)           |
+-----------------------------------+------------------------------------+-------------------------------------+--------------------------------+

\

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| GRB 070306                                                                                                                                           |
+:=================================:+:========================:+:===================:+:==============================:+:==============================:+
| Physical parameters               | (cite: Kruhler2011)      | (cite: Hunt2014)    | (cite: Perley2015)             | Best-fit(None of those two)    |
+-----------------------------------+--------------------------+---------------------+--------------------------------+--------------------------------+
| Stellar mass ($M_{\odot}$)        | $2.45\times10^{10}$      | $1.12\times10^{10}$ | $5^{+0.1}_{-0.2}\times10^{10}$ | $(3.05\pm{0.44})\times10^{10}$ |
+-----------------------------------+--------------------------+---------------------+--------------------------------+--------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | $12.59^{+12.53}_{-4.65}$ | 144.1               | $17^{+7}_{-5}$                 | $38\pm{2}$                     |
+-----------------------------------+--------------------------+---------------------+--------------------------------+--------------------------------+
| Total IR luminosity ($L_{\odot}$) |                          | $15.1\times10^{11}$ |                                | $(2.59\pm{0.26})\times10^{11}$ |
+-----------------------------------+--------------------------+---------------------+--------------------------------+--------------------------------+
| IMF                               | (cite: Chabrier2003)     | $S2C^{1.8}$         | $S2C^{1.6}$                    | (cite: Chabrier2003)           |
+-----------------------------------+--------------------------+---------------------+--------------------------------+--------------------------------+

\
S2C means that the original setting of IMF is (cite: Salpeter1955). But they use some factor to transform to (cite: Chabrier2003) for a fair comparison.\
$^{1.8}$Divided by a factor of 1.8 from (cite: Salpeter1955) to (cite: Chabrier2003)\
$^{1.6}$Divided by a factor of 1.6 from (cite: Salpeter1955) to (cite: Chabrier2003)\
$^M$Multiplied by a factor in (cite: Madau2014) (0.61 for stellar mass and 0.63 for SFR) from (cite: Salpeter1955) to (cite: Chabrier2003).

+--------------------------------------------------------------------------------------------------------------+
| GRB 081221                                                                                                   |
+:=================================:+:======================================:+:===============================:+
| Physical parameters               | (cite: Perley2013a)                    | Best-fit(No AGN)                |
+-----------------------------------+----------------------------------------+---------------------------------+
| Stellar mass ($M_{\odot}$)        | (3.70$^{+1.1}_{-1.2}$)$\times 10^{10}$ | ($3.81\pm0.19$)$\times 10^{10}$ |
+-----------------------------------+----------------------------------------+---------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | 172.8$^{+22.8}_{-30.1}$                | $35\pm2$                        |
+-----------------------------------+----------------------------------------+---------------------------------+
| Total IR luminosity ($L_{\odot}$) |                                        | $(3.04\pm{0.15})\times10^{11}$  |
+-----------------------------------+----------------------------------------+---------------------------------+
| IMF                               | $S2C^{1.8}$                            | $S2C^{M}$                       |
+-----------------------------------+----------------------------------------+---------------------------------+

\

+--------------------------------------------------------------------------------------------------------------------------------------------+
| GRB 071021                                                                                                                                 |
+:=================================:+:====================:+:===========================================:+:=================================:+
| Physical parameters               | (cite: Hunt2014)     | (cite: Perley2013a)                         | Best-fit(No AGN)                  |
+-----------------------------------+----------------------+---------------------------------------------+-----------------------------------+
| Stellar mass ($M_{\odot}$)        | 2.51$\times 10^{11}$ | (1.196$^{+0.066}_{-0.088}$)$\times 10^{11}$ | (1.21$\pm{0.15}$)$\times 10^{11}$ |
+-----------------------------------+----------------------+---------------------------------------------+-----------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | 288.2                | 190.3$^{+25.6}_{-20.3}$                     | $90\pm{5}$                        |
+-----------------------------------+----------------------+---------------------------------------------+-----------------------------------+
| Total IR luminosity ($L_{\odot}$) | $3.02\times10^{12}$  |                                             | $(7.48\pm{1.63})\times10^{11}$    |
+-----------------------------------+----------------------+---------------------------------------------+-----------------------------------+
| IMF                               | $S2C^{1.8}$          | $S2C^{1.8}$                                 | (cite: Chabrier2003)              |
+-----------------------------------+----------------------+---------------------------------------------+-----------------------------------+

\

+-----------------------------------------------------------------------------------------------------------------+
| GRB 050915A                                                                                                     |
+:=================================:+:=======================================:+:=================================:+
| Physical parameters               | (cite: Perley2013a)                     | Best-fit(No AGN)                  |
+-----------------------------------+-----------------------------------------+-----------------------------------+
| Stellar mass ($M_{\odot}$)        | (3.67$^{+1.6}_{-1.04}$)$\times 10^{10}$ | (9.56$\pm{0.48}$)$\times 10^{10}$ |
+-----------------------------------+-----------------------------------------+-----------------------------------+
| SFR ($M_{\odot}$ yr$^{-1}$)       | 135.8$^{+63.1}_{-48.2}$                 | $76\pm{4}$                        |
+-----------------------------------+-----------------------------------------+-----------------------------------+
| Total IR luminosity ($L_{\odot}$) |                                         | $(8.58\pm{0.43})\times10^{11}$    |
+-----------------------------------+-----------------------------------------+-----------------------------------+
| IMF                               | $S2C^{1.8}$                             | (cite: Chabrier2003)              |
+-----------------------------------+-----------------------------------------+-----------------------------------+

\
S2C means that the original setting of IMF is (cite: Salpeter1955). But they used some factor to transform to (cite: Chabrier2003) for a fair comparison.\
$^{1.8}$Divided by a factor of 1.8 from (cite: Salpeter1955) to (cite: Chabrier2003)\
$^M$Multiplied by a factor in (cite: Madau2014) (0.61 for stellar mass and 0.63 for SFR) from (cite: Salpeter1955) to (cite: Chabrier2003).

# Conclusion

With ALMA observations in the rest-frame FIR, we provide new estimates of SFRs for six GRB host galaxies.

The rest-frame FIR continuum were detected for the GRB080207 host with S/N=11, the GRB060814 host with S/N$\sim$16, the GRB070306 host with S/N$\sim$5, the GRB081221 host with S/N$\sim12$, the GRB071021 host with S/N$\sim$4, and the GRB050915A host with S/N$\sim$3.5.

The most notable difference in this work compared with previous estimations without ALMA data is the SFR values.

SFR with ALMA is $\sim2$ times larger than previous studies for the GRB080207 host. For host galaxies of GRB060814, GRB081221, GRB071021 and GRB050915A, the SFRs were overestimated in previous works, which are $\sim2$ to $\sim5$ larger than our estimations. The SED fitting analyses indicate SFRs of $397\pm20$, $56\pm9$, $38\pm2$, $56\pm3$, $90\pm5$ and $77\pm4$ $M_{\odot}$ yr$^{-1}$ for the GRB080207, GRB060814, GRB070306, GRB081221, GRB071021 and GRB050915A host galaxies, respectively. By adding ALMA data, this work derived a more reliable estimate of SFRs, which is important to understand GRB host galaxies

as a CSFR probe.

This change in SFR also leads to a more reliable estimate of the stellar population, and thereby, more reliable stellar masses of GRB host galaxies. For GRB050915A, $M_*$ is $\sim2.5$ larger than the values derived from previous paper. The star-formation rate and other physical parameters are compared with previous literature in Tables [\[tab12\]](#tab12) and [\[tab13\]](#tab13).

With ALMA data, we improved our knowledge on the host galaxies as follows. We found one ULIRG within our sample: GRB080207 host galaxy ($L_{\rm IR}=(1.77\pm0.09)\times10^{12}L_{\odot}$). The IR luminosity of the other five host galaxies are between $10^{11}L{\odot}$ and $10^{12}L_{\odot}$, suggesting that they may be luminous infra-red galaxies (LIRGs). The best IMFs for our GRB host galaxies are (cite: Salpeter1955) for GRB080207 and GRB081221 host galaxies, whereas (cite: Chabrier2003) for GRB060814, GRB070306, GRB071021 and GRB050915A host galaxies.

# Acknowledgements

We thank the anonymous referee for useful comments and constructive remarks on the manuscript. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00927.S and 2016.1.00768.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. TG acknowledges the support by the Ministry of Science and Technology of Taiwan through grant 108-2628-M-007-004-MY3. TH and AYLO are supported by the Centre for Informatics and Computation in Astronomy (CICA) at National Tsing Hua University (NTHU) through a grant from the Ministry of Education of the Republic of China (Taiwan). AYLO’s visit to NTHU was hosted by Prof. Albert Kong and supported through the Ministry of Science and Technology of the ROC (Taiwan) grant 105-2119-M-007-028-MY3. YYH is very grateful for the funding from The University Consortium of ALMA–Taiwan Summer Student Program. This research has made use of the SVO Filter Profile Service (<http://svo2.cab.inta-csic.es/theory/fps/>) supported from the Spanish MINECO through grant AYA2017-84089.

# Data availability

The data underlying this article will be shared on reasonable request to the corresponding author.

[^1]: <http://www.mpe.mpg.de/~jcg/grbgen.html>

[^2]: <https://cigale.lam.fr/about/>

</paper>

Write the methods card for this paper.