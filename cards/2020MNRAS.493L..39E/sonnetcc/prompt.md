# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.493L..39E\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.493L..39E",
 "title": "The ALMaQUEST survey - III. Scatter in the resolved star-forming main sequence is primarily due to variations in star formation efficiency",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Ellison, Sara L.",
 "n_authors": 9,
 "arxiv_id": "1911.11887",
 "doi": "10.1093/mnrasl/slz179",
 "alma_projects_linked_by_archive": [
  "2015.1.01225.S",
  "2017.1.01093.S",
  "2018.1.00541.S",
  "2018.1.00558.S"
 ]
}
```

Paper text:
<paper>
# The ALMaQUEST Survey: III. Scatter in the resolved star forming main sequence is primarily due to variations in star formation efficiency.

## Abstract

Using a sample of 11,478 spaxels in 34 galaxies with molecular gas, star formation and stellar maps taken from the ALMA-MaNGA QUEnching and STar formation (ALMaQUEST) survey, we investigate the parameters that correlate with variations in star formation rates on kpc scales. We use a combination of correlation statistics and an artificial neural network to quantify the parameters that drive both the absolute star formation rate surface density ($\Sigma_{\rm SFR}$), as well as its scatter around the resolved star forming main sequence ($\Delta \Sigma_{\rm SFR}$). We find that $\Sigma_{\rm SFR}$ is primarily regulated by molecular gas surface density ($\Sigma_{\rm H_2}$) with a secondary dependence on stellar mass surface density ($\Sigma_{\star}$), as expected from an ‘extended Kennicutt-Schmidt relation’. However, $\Delta \Sigma_{\rm SFR}$ is driven primarily by changes in star formation efficiency (SFE), with variations in gas fraction playing a secondary role. Taken together, our results demonstrate that whilst the absolute rate of star formation is primarily set by the amount of molecular gas, the variation of star formation rate above and below the resolved star forming main sequence (on kpc scales) is primarily due to changes in SFE.

Galaxies: ISM, galaxies: star formation, galaxies: evolution, galaxies: general

# Introduction

It has been known for over a decade that a galaxy’s total star formation rate (SFR) correlates with its total stellar mass (e.g. Brinchmann et al. 2004; Noeske et al. 2007; Salim et al. 2007), a relation that has become widely known as the star forming main sequence (SFMS). Although tight, there is real scatter around the SFMS, as star formation in low $z$ galaxies is modulated around its equilibrium value by a range of mechanisms such as bars and mergers (e.g. Ellison et al. 2011; Scudder et al. 2012). Whilst the potential triggers of galactic starbursts are relatively well understood, the physics of this transformation are less clear and it remains a matter of considerable debate whether galaxies above the SFMS are there due to higher molecular gas fractions ($f_{\rm H_2}$=$\Sigma_{\rm H_2}$/$\Sigma_{\star}$, e.g. Scoville et al. 2016; Lee et al. 2017), or enhanced star formation efficiencies (SFE=$\Sigma_{\rm SFR}$/$\Sigma_{\rm H_2}$, e.g. Saintonge et al. 2011; Genzel et al. 2015; Silverman et al. 2015, 2018), or a combination of both (Saintonge et al. 2012, 2016; Lin et al. 2017; Piotrowska et al. 2019), depending on whether the galaxy is located on or above the star forming main sequence (Sargent et al. 2014; Elbaz et al. 2018).

A more recent discovery, that has been established from large integral field unit (IFU) surveys of low redshift galaxies, is that the global SFMS is due to the ensemble effect of a ‘resolved’ SFMS on kpc scales (rSFMS, e.g. Sánchez et al. 2013; Cano-Díaz et al. 2016; Hsieh et al. 2017). In turn, Lin et al. (2019) have shown that the rSFMS is likely not fundamental, but rather due to the combination of two other more base relationships, one which regulates the amount of molecular gas in the interstellar medium (i.e. the molecular gas main sequence: $\Sigma_{\star}$ – $\Sigma_{\rm H_2}$) and the other that describes the conversion of the molecular gas into stars (i.e. the Kennicutt-Schmidt relation: $\Sigma_{\rm H_2}$ – $\Sigma_{\rm SFR}$).

Despite the strong correlation between $\Sigma_{\star}$ and $\Sigma_{\rm SFR}$, significant galaxy-to-galaxy variations (Gonzalez-Delgado et al. 2016; Hall et al. 2018; Vulcani et al. 2019) contribute to scatter in the rSFMS. The resolved scaling relations established by IFU surveys, complemented by spatially matched CO observations, provide excellent baselines from which to investigate the physics behind this scatter and hence understand star formation regulation on kpc scales (e.g. Bolatto et al. 2017; Utomo et al. 2017). By defining enhancements in $\Sigma_{\rm SFR}$ relative to $\Sigma_{\rm H_2}$ (i.e. a boost in SFE) and a $\Sigma_{\rm H_2}$ enhancement relative to $\Sigma_{\star}$ (i.e. a boost in $f_{\rm H_2}$), we can quantify whether deviations from the rSFMS are more closely related to changes in SFE or gas fraction.

Using kpc-scale data to study the regulation of star formation has a further important advantage over previous studies that use global quantities. There is clear evidence that there can be significant internal variations in SFE within a given galaxy (e.g. Leroy et al. 2013; Utomo et al. 2017; Tomicic et al. 2019), and that the regulation of star formation happens on local, not global scales (Dey et al. 2019; Bluck et al. 2019b). Studies that investigate correlations in global data will average over these internal differences, blurring the underlying physical relationships.

In this paper, we use the ALMA-MaNGA QUEnching and STar formation (ALMaQUEST) survey (Lin et al. in prep), containing 46 galaxies with kpc-scale maps of molecular gas, stellar mass and SFR. The ALMaQUEST sample includes galaxies located both on (Lin et al. 2019), above (Ellison et al. 2019) and below (Lin et al. 2017; Pan et al. in prep) the global star forming main sequence. This broad range of global properties translates to a broad range of local $\Sigma_{\rm SFR}$ values, making it an ideal sample for investigating the mechanisms that regulate star formation.

# Data

The ALMaQUEST survey contains 46 galaxies with 10 $<$ $\log$ (M$_{\star}$/M$_{\odot}$) $<$ 11.5 selected from the Mapping Nearby Galaxies at Apache Point Observatory (MaNGA; Bundy et al. 2015) survey and followed up with Atacama Large Millimeter Array (ALMA) CO (1-0) observations that are matched in spatial resolution (FWHM $\sim$ 2.5 arcsec) and mapped to the same grids of 0.5 arcsec pixels (0.3 kpc at the median redshift of the sample, $z$=0.03). A full description of the ALMA observations, data reduction and molecular gas maps, which typically extend to 1-2 R/R$_e$, are presented in Lin et al. (in prep). CO luminosities are converted to molecular gas surface densities ($\Sigma_{\rm H_2}$) via a constant conversion factor $\alpha_{CO}$ = 4.3 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ (an assumption that we will demonstrate does not affect our results), with a requirement that the S/N of the CO line intensity exceeds 3.

Stellar mass surface densities ($\Sigma_{\star}$) are taken from the public MaNGA Data Release 15 (DR15) data cubes, as processed by PIPE3D (Sánchez et al. 2016), with a minimum log $\Sigma_{\star}$ $>$ 7 M$_{\odot}$ kpc$^{-2}$ imposed (below which the rSFMS is poorly defined in our sample). We compute de-projected galactocentric radii in units of the effective radius ($R_e$), which typically extend to 1.5-2 R/R$_e$, using the Sersic fit axial ratio from the NASA Sloan Atlas. All radii quoted in this paper adopt these de-projected values. Emission line fluxes are taken from the PIPE3D data cubes and corrected for internal extinction by assuming an intrinsic H$\alpha$/H$\beta$=2.85 and a Milky Way extinction curve (Cardelli, Clayton & Mathis 1989). Only spaxels classified as star-forming according to the diagnostic criterion of Kauffmann et al. (2003), with S/N $>$3 in the requisite emission lines and H$\alpha$ equivalent width $>$ 6 Å are used for the current study. Star formation rate surface densities ($\Sigma_{\rm SFR}$) are computed from H$\alpha$ luminosities, a technique that has been shown to reproduce the UV and IR SFRs well in IFU data (Catalan-Torrecilla et al. 2015). Gas-phase metallicities (O/H) are determined using the O3N2 calibration of Marino et al. (2013). Finally, we require the galaxy inclination to be less than 70 degrees ($b/a >$0.34), which removes 12 galaxies from the full ALMaQUEST sample. All surface densities in this paper are inclination corrected. In total, 11,478 spaxels in 34 galaxies fulfill all of the above criteria.

![image](MS_resolved_dfgas.pdf) ![image](MS_resolved_dks.pdf)

In order to quantify how discrepant a given spaxel is from normal scaling relations, we follow Ellison et al. (2018, 2019) and compute a series of offsets from a set of control spaxels:

- $\Delta \Sigma_{\rm SFR}$ is the offset of a given spaxel’s $\Sigma_{\rm SFR}$ from the rSFMS of all ($\sim$ 1.2 million) star forming spaxels in the MaNGA DR15 at fixed $\Sigma_{\star}$ (matched within 0.1 dex). $\Delta \Sigma_{\rm SFR}$ is therefore a measure of the ‘starburstiness’ of a given spaxel, and encapsulates the scatter around the rSFMS.\

- $\Delta$SFE is the offset of a given spaxel’s $\Sigma_{\rm SFR}$ from the resolved Kennicutt-Schmidt relation relative to a set of control spaxels with normal SFRs ($-0.5 <$ $\Delta \Sigma_{\rm SFR}$ $<0.5$) that are matched in $\Sigma_{\rm H_2}$ (within 0.1 dex), $R/R_e$ (within 0.1 $R/R_e$), O/H (within 0.1 dex) and total stellar mass (within 0.1 dex). Matching in O/H and $R/R_e$ mitigates metallicity and radius dependent $\alpha_{CO}$ variations (e.g. Sandstrom et al. 2013). $\Delta$SFE is therefore a measure of how efficient a given spaxel is at converting gas into stars, relative to the norm.\

- $\Delta f_{\rm H_2}$ is the offset of a given spaxel’s $\Sigma_{\rm H_2}$ from the molecular gas main sequence ($\Sigma_{\star}$ – $\Sigma_{\rm H_2}$, e.g. Wong et al. 2013; Lin et al. 2019) relative to a set of control spaxels with normal SFRs ($-0.5 <$ $\Delta \Sigma_{\rm SFR}$ $<0.5$) that are matched in $\Sigma_{\star}$ (within 0.1 dex), $R/R_e$ (within 0.1 $R/R_e$), O/H (with 0.1 dex) and total stellar mass (within 0.1 dex). $\Delta f_{\rm H_2}$ is therefore a measure of how much extra gas, per unit stellar mass, is present in a given spaxel.\

# Results

In Fig. [1](#ms_resolved_fig) we show the rSFMS for the 11,478 star-forming spaxels (0.5 arcsec in size, sampling the 2.5 arcsec resolution) in the ALMaQUEST sample, colour coded by $\Delta f_{\rm H_2}$ (top panel) and $\Delta$SFE (lower panel). The relatively large scatter in this figure is a direct result of our sample selection, which contains a high fraction of both greeen valley and starburst galaxies. Whilst this large dynamic range is advantageous for the study presented here (since our goal is to study the source of the scatter), it is not a representative (e.g. in mass or volume) sample, hence we do not report a fit to the rSFMS for comparison to other studies. Fig. [1](#ms_resolved_fig) shows that the scatter in the rSFMS is clearly correlated with variations in a spaxel’s gas fraction and SFE, in qualitative agreement with low redshift studies of global gas properties (e.g. Saintonge et al. 2012).

![image](KS_resolved.pdf) ![image](MHMs_resolved.pdf)

An alternative way to visualize the dependence of $\Delta \Sigma_{\rm SFR}$ on gas fraction and SFE is shown in Fig. [2](#ks_resolved_fig), where we plot the distribution of $\Sigma_{\rm H_2}$ vs. $\Sigma_{\rm SFR}$ (upper panel) and $\Sigma_{\star}$ vs. $\Sigma_{\rm H_2}$ (lower panel), both colour-coded by $\Delta \Sigma_{\rm SFR}$. The upper panel of Fig [2](#ks_resolved_fig) shows the expected strong correlation between molecular gas and star formation (the Kennicutt-Schmidt relation). To first order, a constant depletion time (the inverse of SFE) is a good representation of the data, consistent with studies of nearby star-forming disk galaxies (e.g. Bigiel et al. 2008, 2011; Leroy et al. 2008, 2013; Schruba et al. 2011). However, the colour-coding reveals that a spaxel’s SFE (i.e. its vertical position at fixed $\Sigma_{\rm H_2}$) depends on its enhancement relative to the rSFMS. The lower panel of Fig. [2](#ks_resolved_fig) shows that the gas fraction of a given spaxel also depends on $\Delta \Sigma_{\rm SFR}$, but the correlation is (visually) weaker than the relation between SFE and $\Delta \Sigma_{\rm SFR}$ (upper panel of Fig [2](#ks_resolved_fig)).

In order to more rigourously quantify the relative importance of various parameters in affecting $\Sigma_{\rm SFR}$ (the absolute surface density of star formation) and $\Delta \Sigma_{\rm SFR}$ (the scatter around the rSFMS), we perform two complementary ranking analyses. First, we perform a simple correlation assessment in which we compute the Pearson correlation coefficient ($\rho$) between $\Sigma_{\rm SFR}$ and $\Delta \Sigma_{\rm SFR}$ and a list of input variables. Since Bluck et al. (2019b) have recently shown that global parameters have relatively little impact on kpc-scale star formation rates, we restrict our analysis to spaxel-based variables. Specifically, we quantify $\rho$ for $\Sigma_{\star}$, $\Sigma_{\rm H_2}$, $f_{\rm H_2}$, SFE, $\Delta$SFE and $\Delta f_{\rm H_2}$. $\Delta$SFE and $\Delta f_{\rm H_2}$ are included in this list of variables as they capture subtly different information than the raw values of SFE and $f_{\rm H_2}$. Fundamentally, these offset metrics quantify deviations from normal values, but here they have the additional power of accounting for dependences of $\alpha_{CO}$ on O/H and $R$.

To complement the correlation analysis, we also apply a machine learning approach, which has the benefit of being able to recognize more complex patterns in the data than can be captured by $\rho$. Specifically, we perform a non-linear regression with an artificial neural network (ANN), utilising MLPregresser from the scikit-learn package (Pedregosa et al. 2011), adopting an identical architecture as in Bluck et al. (2019b). To test the stability of the network, we train on five randomly selected input samples (containing 50% of the data) and validate on the remainder of the sample in each case. We quantify the performance of the network with each individual parameter via the improvement over random (IOR) statistic (defined in Bluck et al. 2019a). Briefly, the mean square error of the network-predicted values to the truth values are computed in each case, and the improvement in performance over a random variable is quantified. In this manner parameters may be ranked in terms of how effective they are at predicting either $\Sigma_{\rm SFR}$ or $\Delta \Sigma_{\rm SFR}$. We use the same six parameters as in the correlation analysis, all of which yield a highly stable result, with a typical variance of only $\sim$ 1%.

Fig. [3](#bar_fig) shows the results from the correlation (upper panel) and ANN (lower panel) analyses of the six input variables in predicting either $\Sigma_{\rm SFR}$ (blue columns) or $\Delta \Sigma_{\rm SFR}$ (orange columns) as the target variable, where a higher number ($\rho$ or IOR) indicates that a given variable is better at predicting the target variable. Both analyses find that the single most important variable in predicting a spaxel’s $\Sigma_{\rm SFR}$ (of those we have tested) is $\Sigma_{\rm H_2}$, i.e. the Kennicutt-Schmidt relation. Variations in SFE (i.e $\Delta$SFE) and $\Sigma_{\star}$ play equally important secondary roles. The former of these two variables captures the scatter around the Kennicutt-Schmidt relation, and accounts for variations in O/H and radius. The equally important role of $\Sigma_{\star}$ is consistent with expectations from an ‘extended Kennicutt-Schmidt’ law in which $\Sigma_{\rm SFR}$ $\propto$ $\Sigma_{\rm H_2}$$^n$$\Sigma_{\star}$$^m$, where observations find $m<n$ (e.g. Shi et al. 2011).

A subtly different question, and the main objective of the current paper, is assessed by the orange bars in Fig. [3](#bar_fig), in which the target variable is now set not to be $\Sigma_{\rm SFR}$, but its offset from the rSFMS, $\Delta \Sigma_{\rm SFR}$. The results from this test tell us which factors correlate with a spaxel’s SFR deviation from the norm, causing it to be either enhanced, or suppressed, in its star formation. Again, the results of the correlation analysis are in good qualitative agreement with the ranks obtained from the more complex ANN approach. Both analyses find that, in contrast to predicting the absolute $\Sigma_{\rm SFR}$, $\Sigma_{\rm H_2}$ plays a minor role in predicting $\Delta \Sigma_{\rm SFR}$. Instead, $\Delta$SFE is found to be the most important parameter for driving $\Sigma_{\rm SFR}$ away from the rSFMS, with a secondary dependence on $f_{\rm H_2}$, indicating that the scatter around the rSFMS is primarily driven by by changes in the SFE. The correlation between $\Delta \Sigma_{\rm SFR}$ and $\Delta$SFE is shown explicitly in Fig. [4](#corr_fig). We repeated our ANN regression analysis separating spaxels into those on ($-0.5 <$ $\Delta \Sigma_{\rm SFR}$ $<0.5$) and above ($\Delta \Sigma_{\rm SFR}$$>$ 0.5) the rSFMS and found that $\Delta$SFE remains the most important parameter for predicting $\Delta \Sigma_{\rm SFR}$ in both cases.

![image](correlations_bar.pdf) ![image](ANN_bar.pdf)

![](dsfr_dks.pdf)

# Summary and Discussion

The key result of the work presented here is that, on kpc-scales, the enhancement of star formation away from its equilibrium value (as defined by the rSFMS) is primarily driven by changes in SFE, with a secondary, weaker, dependence on gas fraction. This conclusion is based on (1) assessment of Pearson correlation coefficients and (2) an artificial neural network analysis. Furthermore, we find that $\Delta$SFE drives $\Delta \Sigma_{\rm SFR}$ both within and above the rSFMS.

Throughout this work we have adopted a constant $\alpha_{CO}$ conversion factor to determine $\Sigma_{\rm H_2}$. In practice, $\alpha_{CO}$ is likely to be lower for spaxels with enhanced $\Delta \Sigma_{\rm SFR}$, leading to a decrease in $\Sigma_{\rm H_2}$. In turn, a decrease in $\Sigma_{\rm H_2}$ would lead to an increased SFE (and $\Delta$SFE) and a decrease in $f_{\rm H_2}$ (and $\Delta f_{\rm H_2}$). Our correlation analysis already identifies a strong positive correlation between $\Delta \Sigma_{\rm SFR}$ and $\Delta$SFE; increasing $\Delta$SFE would further strengthen that correlation, e.g. steepening the correlation in Fig. [4](#corr_fig). Likewise, in the ANN analysis we see that $\Delta \Sigma_{\rm SFR}$ is better predicted by $\Delta$SFE than absolute SFE, probably because O/H and $R$ (which both affect $\alpha_{CO}$) are controlled for in the former and hence $\Delta$SFE better captures variations in the conversion factor. On the other hand, the reduction in $\Delta f_{\rm H_2}$ that would result from a lower $\alpha_{CO}$ would reduce the strength of the positive correlation with $\Delta \Sigma_{\rm SFR}$ and indeed we see that $\Delta f_{\rm H_2}$ performs less well than $f_{\rm H_2}$ in the ANN analysis. Our conclusion that $\Delta \Sigma_{\rm SFR}$ is more correlated with $\Delta$SFE than $\Delta f_{\rm H_2}$ would therefore only be strengthened if we explicitly used a variable conversion factor.

Previous studies of *global* quantities have also concluded that there is a correlation between the position of a galaxy relative to the main sequence ($\Delta$SFR) and its total SFE (Genzel et al. 2015; Silverman et al. 2015, 2018; Tacconi et al. 2018). Our results agree with this primary dependence, but show a secondary depedence on gas fraction (e.g. Saintonge 2012, 2016). However, global studies average over the considerable internal variations known to exist within a given galaxy (e.g. Tomicic et al. 2019; Vulcani et al. 2019), which will induce scatter into relations and obscure the underlying scale which governs the physics. Our sample also has the significant advantage of being drawn from a single dataset with continuous selection function (rather than focused on high SFR or CO-bright samples), single redshift epoch, homogeneous data reduction and consistent assumptions on, for example, definition of main sequence offset and treatment of $\alpha_{CO}$. Any correlations in our data are therefore unlikely to be due to combining data from different sources, different redshifts (where different physical mechanisms may be at play) with very different properties and analysis methods.

Whereas $\Delta \Sigma_{\rm SFR}$ is set primarily by changes in SFE, our ANN analysis shows that $\Sigma_{\rm SFR}$ is governed mainly by $\Sigma_{\rm H_2}$, consistent with expectations from the Kennicutt-Schmidt relation, with a secondary dependence on $\Sigma_{\star}$ (as well as a on $\Delta$SFE which is essentially the scatter around the Kennicutt-Schmidt relation). Two other works have also recently used complementary machine learning methods to quantify the primary driver of $\Sigma_{\rm SFR}$. First, Bluck et al. (2019b) have applied the same ANN approach used herein to MaNGA data and find several conclusions in common with us: that $\Sigma_{\star}$ is the most important parameter in determining $\Sigma_{\rm SFR}$, and that $R$ and O/H play a negligible role. However, Bluck et al. (2019b) do not have direct measurements of gas surface densities amongst their available parameters. Our results are therefore consistent with those of Bluck et al. (2019b) in that of the non-gas parameters in our sample, we also find $\Sigma_{\star}$ as the highest ranked parameter in predicting $\Sigma_{\rm SFR}$.

Second, Dey et al. (2019) combine IFU data from the Calar Alto Legacy Intergral Field Area (CALIFA, Sánchez et al. 2012) survey, with interferometric observations of CO, to achieve a dataset that is similar in its range of physical variables to the ALMaQUEST sample studied herein. Even with the inclusion of molecular gas maps, Dey et al. (2019) agree with the conclusion of Bluck et al. (2019b) on the primary importance of $\Sigma_{\star}$ in determining $\Sigma_{\rm SFR}$, ranking it above $\Sigma_{\rm H_2}$. Dey et al. (2019)’s result therefore contrasts with the conclusions of our study, and imply that, at kpc-scales, the rSFMS is more fundamental than the Kennicutt-Schmidt law. The results of Dey et al. (2019) are surprising in light of the well-established link between gas and star formation and are also in conflict with Lin et al. (2019), who conclude that the rSFMS is largely due to the more fundamental $\Sigma_{\star}$– $\Sigma_{\rm H_2}$ and $\Sigma_{\rm H_2}$ – $\Sigma_{\rm SFR}$ relations.

Although we have concluded that variations in SFE are responsible for variations in $\Sigma_{\rm SFR}$ on kpc-scales, a potentially important omission in our study is the role of dense molecular gas. Gao & Solomon (2004) showed that a linear relationship exists between the global abundance of dense gas (as traced by HCN) in galaxies and their SFR, implying a constant SFE in the dense gas (see also Wu et al. 2005; Lada et al. 2010). These works have supported a so-called ‘threshold model’ of star formation, whereby the abundance of dense gas is a direct indicator of how much star formation takes place. However, more recent work, that has mapped dense gas on kpc-scales, has found that there is real scatter in the relation between dense gas and SFR within a given galaxy (e.g. Usero et al. 2015; Bigiel et al. 2016). Contrary to a threshold star formation model, these works demonstrate that the star formation efficiency of dense gas is very sensitive to local parameters, such as $\Sigma_{\star}$ (Gallagher et al. 2018; Jimenez-Donaire et al. 2019). Including measurements of the dense gas surface density in an ANN analysis is likely to yield further insights into the primary regulators of star formation on kpc scales.

# Acknowledgements

We gratefully acknowledge grant MOST 107-2119-M-001-024 for funding travel to ASIAA (SLE and MDT) and ERC Advanced Grant 695671 ‘QUENCH’ (AFLB). SLE thanks Erik Rosolowsky and Brenda Matthews for discussions and ALMA advice. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01225.S, ADS/JAO.ALMA#2017.1.01093.S, ADS/JAO.ALMA#2018.1.00558.S, ADS/JAO.ALMA#2018.1.00541.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

(ref: big11) Bigiel, F., et al., 2011, ApJ, 730, L13

(ref: big16) Bigiel, F., et al. 2016, ApJ, 822, L26

(ref: big08) Bigiel, F., Leroy, A., Walter, F., Brinks, E., de Blok, W. J. G., Madore, B., Thornley, M. D., 2008, AJ, 136, 2846

(ref: bl19a) Bluck, A. F. L., et al., 2019a, MNRAS, 485, 666

(ref: bl19b) Bluck, A. F. L., Maiolino, R., Sanchez, S. F., Ellison, S. L., Thorp, M. D., Piotrowska, J., Teimoorinia, H., Bundy, K. A., MNRAS, 2019b, submitted

(ref: bol17) Bolatto, A. D., et al. 2017, ApJ, 846, 159

(ref: bri04) Brinchmann, J., Charlot, S., White, S. D. M., Tremonti, C., Kauffmann, G., Heckman, T., Brinkmann, J.,2004, MNRAS, 351, 1151

(ref: bun15) Bundy, K., et al., 2015, ApJ, 798, 7

(ref: cd16) Cano-Diaz, M., et al., 2016, ApJ, 821, L26

(ref: ccm89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S., 1989, ApJ, 345, 245

(ref: cat15) Catalan-Torrecilla, C., et al., 2015, A&A, 584, 87

(ref: dey19) Dey, B., et al., 2019, MNRAS, 488, 1926

(ref: elb18) Elbaz, D., et al., 2018, A&A, 616, 110

(ref: bars) Ellison, S. L., Nair, P., Patton, D. R., Scudder, J. M., Mendel, J. T., Simard, L., 2011, MNRAS, 416, 2182

(ref: manga) Ellison, S. L., Sanchez, S. F., Ibarra-Medel, H., Antonio, B., Mendel, J. T., Barrera-Ballesteros, J., 2018, MNRAS, 474, 2039

(ref: aq3) Ellison, S. L., Thorp, M. D., Pan, H.-A., Lin, L., Scudder, J. M., Bluck, A. F. L., Sanchez, S. F., Sargent, M., 2019, MNRAS, submitted

(ref: gal18) Gallagher, M. J., et al., 2018, ApJ, 858, 90

(ref: gs04) Gao, Y., & Solomon, P. M., 2004, ApJ, 606, 271

(ref: gen15) Genzel, R., et al., 2015, ApJ, 800, 20

(ref: gd16) Gonzalez-Delgado, R., et al., 2016, A&A, 590, 44

(ref: Hall18) Hall, C., Courteau, S., Jarrett, T., Cluver, M., Meurer, G., Carignan, C., Audcent-Ross, F., 2018, ApJ, 865, 154

(ref: hs17) Hsieh, B. C., et al., 2017, ApJ, 851, L24

(ref: jd19) Jimenez-Donaire, M. A., et al., 2019, ApJS, in press

(ref: lla10) Lada, C. J., Lombardi, M., & Alves, J. F., 2010, ApJ, 724, 687

(ref: lee17) Lee, N., et al., 2017, MNRAS, 471, 2124

(ref: ler08) Leroy, A. K., Walter, F., Brinks, E., Bigiel, F., de Blok, W. J. G., Madore, B., Thornley, M. D., 2008, AJ, 136, 2782

(ref: ler13) Leroy, A. K., et al., 2013, AJ, 146, 19

(ref: lin19) Lin, L., et al., 2019, ApJ, 884, L33

(ref: lin17) Lin, L., et al., 2017, ApJ, 851, 18

(ref: mar13) Marino, R. A., et al., 2013, A&A, 559A, 114

(ref: noe07) Noeske, K. G., et al., 2007, ApJ, 660, L43

(ref: scikit) Pedregosa, F., et al., 2011, JMLR, 12, 2825

(ref: piot) Piotrowska J. M., Bluck A. F. L., Maiolino R., Concas A., Peng Y., 2019, MNRAS, submitted

(ref: sain11b) Saintonge, A., et al., 2011, MNRAS, 415, 61

(ref: sain12) Saintonge, A., et al., 2012, ApJ, 758, 73

(ref: sain16) Saintonge, A., et al., 2016, MNRAS, 462, 1749

(ref: sal07) Salim, S., et al, 2007, ApJS, 173, 267

(ref: s12) Sánchez, S. F., et al., 2012, A&A, 538, 8

(ref: s13) Sánchez, S. F., et al., 2013, A&A, 554, 58

(ref: pipe16b) Sánchez, S. F., et al., 2016, RMxAA, 52, 171

(ref: sand11) Sandstrom, K. M., et al., 2013, ApJ, 777, 5

(ref: sar14) Sargent, M. T., et al., 2014, ApJ, 793, 19

(ref: sch11) Schruba, A., et al., 2011, AJ, 142, 37

(ref: sco16) Scoville, N., et al., 2016, ApJ, 820, 83

(ref: \[pairs) Scudder, J. M., Ellison, S. L., Torrey, P., Patton, D. R., Mendel, J. T., 2012, MNRAS, 426, 549

(ref: shi2011) Shi, Y., Helou, G., Yan, L., Armus, L., Wu, Y., Papovich, C., Stierwalt, S., 2011, ApJ, 733, 87

(ref: sil15) Silverman, J.D., et al., 2015, ApJ, 812, L23

(ref: sil18) Silverman, J.D., et al., 2018, ApJ, 867, 92

(ref: tac18) Tacconi, L. J., et al., 2018, ApJ, 853, 179

(ref: tom19) Tomicic, B., et al., 2019, ApJ, 873, 3

(ref: us15) Usero, A., et al., 2015, AJ, 150, 115

(ref: uto17) Utomo, D., et al., 2017, ApJ, 849, 26

(ref: vul19) Vulcani, B., et al., 2019, MNRAS, in press

(ref: wong13) Wong, T., et al., 2013, ApJ, 777, L4

(ref: wu05) Wu, J., Evans, N. J., Gao, Y., Solomon, P. M., Shirley, Y. L., Vanden Bout, P. A., 2005, ApJ, 635, 173

</paper>

Write the methods card for this paper.