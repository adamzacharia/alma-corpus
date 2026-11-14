# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024AJ....168....5M\sonnetcc\reply.txt

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
 "bibcode": "2024AJ....168....5M",
 "title": "Hα Emission and H II Regions at the Locations of Recent Supernovae in Nearby Galaxies",
 "year": 2024,
 "journal": "The Astronomical Journal",
 "first_author": "Mayker Chen, Ness",
 "n_authors": 25,
 "arxiv_id": "2404.10762",
 "doi": "10.3847/1538-3881/ad3fb7",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00484.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S"
 ]
}
```

Paper text:
<paper>
# H$\alpha$ emission and H II regions at the locations of recent supernovae in nearby galaxies

## Abstract

We present a statistical analysis of the local, $\approx 50{-}100$ pc scale, H$\alpha$ emission at the locations of recent ($\leq125$ years) supernovae (SNe) in nearby star-forming galaxies. Our sample consists of 32 SNe in 10 galaxies that are targets of the PHANGS-MUSE survey. We find that 41% (13/32) of these SNe occur coincident with a previously identified H II region. For comparison, H II regions cover 32% of the area within $\pm 1$ kpc of any recent SN. Contrasting this local covering fraction with the fraction of SNe coincident with H II regions, we find a statistical excess of 7.6% $\pm$ 8.7% of all SNe to be associated with H II regions. This increases to an excess of 19.2% $\pm$ 10.4% when considering only core-collapse SNe. These estimates appear to be in good agreement with qualitative results from new, higher resolution *HST* H$\alpha$ imaging, which also suggest many CCSNe detonate near but not in H II regions. Our results appear consistent with the expectation that only a modest fraction of stars explode during the first $\lesssim 5$ Myr of the life of a stellar population, when H$\alpha$ emission is expected to be bright. Of the H II region associated SNe, 85% (11/13) also have associated detected CO (2–1) emission, indicating the presence of molecular gas. The H II region associated SNe have typical extinctions of $A_V \sim1$ mag, consistent with a significant amount of pre-clearing of gas from the region before the SNe explode.

# Introduction

In this paper we leverage new, high physical resolution, high sensitivity maps of H$\alpha$ emission from nearby galaxies to assess the coincidence between recent supernovae (SNe) and H II regions. This measurement can help constrain both the nature of SN progenitors and the environments into which SNe explode.

Bright regions of H$\alpha$ emission in galaxies are indicative of H II regions, where short-lived ($\lesssim 5$ Myr), massive ($>$10 $M_\odot$) stars ionize the gas through photons with energies higher than 13.6 eV. Therefore we would expect SNe in close proximity to H II regions to likely originate from massive, short-lived progenitors. Such proximity studies have been particularly useful for understanding if and how the different subtypes of core-collapse SNe (CCSNe), Types II, Ib, Ic, correspond to different progenitor mass and age ranges (cite: Anderson2015), something that has been challenging to infer from direct photometry/spectroscopic observations of the SNe (cite: Dessart2022).

SN environment studies attempt to constrain the delay time and progenitor populations for SNe by measuring the correlation of the different SN types with various stellar populations and tracers of star formation (cite: Anderson2015b). In a key early study, (cite: vanDyk1996) found $\sim70\%$ of CCSNe to be associated with H II regions. More recently, (cite: AudcentRoss2020) compared the radial distributions of 80 SNe with R-band, UV, and $H\alpha$ emission in the SINGG/SUNGG galaxy surveys. They found SNe Ia correlated with R-band light, an indicator of the presence of low mass progenitors; SNe II were correlated with FUV emission, consistent with moderately massive progenitors; and stripped-enveloped SNe (SESNe) were found to be the most associated with $H\alpha$ emission, suggestive of SESNe originating from the most massive progenitor systems. Recent studies expanded beyond only imaging to also leverage IFU data (cite: Anderson2014; Galbany2017). These studies consistently show that SNe Ia (white dwarf SNe) are the most weakly associated with tracers of star formation and instead associated with the older stellar population (cite: Pritchet2024). SNe Ib/c (stripped envelope core collapse SNe) are more associated with tracers of very recent star formation than SNe II (other core collapse SNe) (cite: Crowther2013; Galbany2014), but with subtle differences between SNe Ib and Ic (cite: James2006; Anderson2012). These results support a picture with an increasing progenitor mass sequence, SNe Ia $\rightarrow$ SNe II $\rightarrow$ SNe Ib $\rightarrow$ SNe Ic (cite: Kuncarayakti2013; Zapartas2017).

The coincidence (or not) of SNe and H II regions also has significant implications for the mechanisms and impact of stellar feedback in various contexts. A variety of observational evidence supports that cold, molecular gas is often substantially cleared from a star-forming region *before* H$\alpha$ fades (cite: Schruba2010; Kruijssen2019; Schinnerer2019; Chevance2020; Kim2022; Pan2022). Measurements of resolved H$\alpha$ emission around clusters with SED modeling-based ages also suggest that the ionized gas may be cleared on few Myr timescales, even before ionizing photon production stops (cite: Hannon2022). If SNe have an important role in this rapid gas clearing, then they must be present to some degree within H II regions. Arguments based on stellar evolution timescales ascribed most of this gas clearing to “pre-SN” feedback: stellar winds, radiation pressure, and ionized gas pressure (cite: Lopez2014; McLeod2019; McLeod2020; McLeod2021; Barnes2020; Olivier2021; Barnes2022; Chevance2022). Directly measuring the coincidence of SNe with H II regions provides an independent, empirical test.

Conversely, SNe explosions in galaxy disks are important to supporting the overall gas disk, launching galactic winds, and stirring turbulence (cite: Elmegreen2004; Ostriker2011; Walch2015; Girichidis2016; Veilleux2020). The environment where a SN explodes has a significant impact on its zone of influence, with explosions in denser environments exerting a more local influence both because the high density leads to a shorter cooling time and because the momentum injected by the supernova affects a smaller physical region at high density (cite: Walch2015; Gatto2017; Keller2020). Away from the dense gas of star-forming regions, SN explosions are free to impact a larger area and exert this “large-scale” feedback (cite: Barnes2023). Therefore demonstrating what fraction of these explosions in fact do occur away from dense gas represents an important avenue to quantitatively understand feedback in stellar disks. Recently both (cite: MaykerChen2023a) and (cite: Sarbadhicary2023) measured the cold gas content (CO and H I) at the sites of recent SNe or likely near-future SNe in nearby galaxies. They found evidence for substantial populations of SNe away from CO emission and well-positioned to explode into low density regions. Even SNe close to star-forming regions of galaxies can still go off in the low density environments found in bubbles carved out by stellar populations and previous SNe (cite: Bagetakos2011; Pokhrel2020; Barnes2023; Egorov2023; Watkins2023a; Watkins2023b).

Because SNe are rare, SN environment studies have often been forced to work with samples of distant objects with relatively coarse physical resolution. This can make it difficult to distinguish cases where a SN occurs *within* an H II region from cases in which the SN only occurs *near* the H II region. Studies at higher resolution are needed to directly measure the fraction of SNe that are actually occurring *within* H II regions and to place these explosions accurately within the multiphase interstellar medium (ISM).

In this work, we adopt a slightly different approach compared to these earlier studies. While they often characterize the sites of SN explosions after detecting them, we instead focus on identifying SNe and determining their locations within a uniquely well-studied set of nearby $\lesssim 20$ Mpc galaxies, the PHANGS surveys (cite: Leroy2021; Emsellem2022; Lee2022). Because PHANGS targets very nearby galaxies, even seeing-limited ground-based observations achieve physical resolution $\lesssim 100$ pc, up to ten times sharper than previous studies. This offers the prospect to better localize SNe relative to H II regions, and from the rich supporting data, we can construct a variety of careful controls using data at other wavelengths. This high physical resolution and multi-wavelength coverage offers the prospect to “zoom in” on individual SN sites to directly see the likely area of influence of the SN and so understand its future impact.

We took a first step towards this goal of characterizing the local sites of SNe in (cite: MaykerChen2023a), where we studied the CO (2–1) emission from SNe in the PHANGS–ALMA survey (cite: Leroy2021). In this paper we take the next logical step: comparing SNe to tracers of the ionized gas and young, massive stars using the PHANGS–MUSE survey (cite: Emsellem2022) and including a first look based on the PHANGS–H$\alpha$ HST survey (cite: Barnes2022). PHANGS–MUSE, our core comparison data set, provided spectroscopic optical mapping at $\lesssim 1\ensuremath{''}$ resolution for $19$ galaxies. This includes high quality maps of H$\alpha$ and H$\beta$ (cite: Belfiore2022; Belfiore2023) that have been used to identify and characterize $\sim 20,000$ individual nebular regions (cite: Groves2023). We identify 32 SNe that have occurred within 10 targets of PHANGS–MUSE and characterize their explosion sites, exploring implications for SN progenitors and stellar feedback.

In §[2](#sec:Methods) we describe our experimental design and data. In §[2.1](#Maps) we summarize the data used in this work. In §[2.2](#SNselection) we discuss how our SN sample is compiled. In §[2.3](#Analysis) we discuss the control measurements that we make to help interpret our results. In §[3](#sec:ResultsHa) we report on the H$\alpha$ emission at our SN sites: in §[3.1](#sec:HIIregions) we measure the fraction of SN sites coincident with an H II region, in §[3.2](#sec:types) we analyze our SN population by type, in §[3.3](#sec:SSP) we compare our findings with expectations of simple stellar population (SSP) models, in §[3.4](#sec:HIIregionsDist) we compare the distance to the nearest H II region from our real SN sample to three model populations of SNe, in §[3.5](#sec:HaEmission) we compare the distributions of H$\alpha$ emission present at the sites of the real SNe to our model populations, and then in §[3.6](#sec:Zooms) we zoom in to examine the local MUSE and HST H$\alpha$ emission from our SN sites. In §[4](#sec:ResultOther) we also consider other properties of the ISM at the sites of our SN sample. In §[4.1](#sec:HACO) we look at how the incidence of molecular gas relates to the presence of H II regions; in §[4.2](#sec:BD) we compare the extinction at each of our SN sites to that of the host galaxies overall; and in §[4.3](#sec:Additional) we report additional diagnostics at each of our SN sites, including velocity dispersion, metallicity, and BPT classifications. Finally, in §[5](#sec:Discussion) we summarize and discuss our results.

# Methods

## Data

![](MUSEGalaxies1.pdf)

![](MUSEGalaxies2.pdf)

The PHANGS–MUSE survey (cite: Emsellem2022) mapped 19 nearby, star-forming galaxies (distances $<$ 20 Mpc, inclinations $<$ $60^\circ$) using the Multi-Unit Spectroscopic Explorer (MUSE) instrument (cite: Bacon2010) on the ESO Very Large Telescope. For this work, we use attenuation-corrected H$\alpha$ emission maps (see Figures [1](#fig:MUSEGalaxies) and [2](#fig:MUSEGalaxies_cont)) produced by (cite: Belfiore2023) (cite: Pessa2021). We use the “copt” convolved and optimized standard products. These have resolution that varies from galaxy to galaxy ranging between 0.78$''$ and 1.25$''$, which translates to linear resolution of $33{-}104$ pc at the distance of our targets (see Table [\[tab:supernovaeTable\]](#tab:supernovaeTable)). The MUSE astrometry is calibrated against Gaia via a procedure detailed in (cite: Emsellem2022) and so is expected to be accurate to within a few tenths of an arcsecond.

The MUSE maps have high signal-to-noise, recovering H$\alpha$ emission almost everywhere. (cite: Emsellem2022) found that more than 95% of 0.2$''$ spaxels within 0.5 $R_{25}$ contain H$\alpha$ emission at a 3$\sigma$ level. However, much of this emission represents diffuse ionized gas, likely powered by photons leaked from H II regions (cite: Belfiore2022). To distinguish likely actual H II regions from this extended emission, we use the PHANGS nebular catalog (cite: Groves2023; Santoro2022) to determine where there is an H II region along the line of sight. These H II regions are identified using the HIIphot algorithm (cite: Thilker2000) adopting a single termination gradient of the H$\alpha$ surface brightness. For more information, see §3.1 of (cite: Groves2023).

In Table [\[tab:supernovaeTable\]](#tab:supernovaeTable), we report the nebular catalog’s BPT flags for three emission line diagnostics, \[N II\] $\lambda$6584, \[S II\] $\lambda$6717, \[O I\] $\lambda$6300, (cite: Groves2023). These diagnostics help determine whether the emission is more likely to arise from an H II region or another type of nebula, e.g., supernova remnant shocks, winds, or planetary nebulae. As we discuss further in section [4.3](#sec:Additional), all 13 SNe that are within the line of sight of nebular emission show diagnostics suggesting that the nebular emission is caused by star formation, and all have low H$\alpha$ velocity dispersions. Overall, the H$\alpha$ emission occurring within the line of sight to our SN sample is consistent with emission from H II regions. Because our sample consists of young SNe, we do not expect that they have had time to influence their environment and the BPT diganostics are unlikely to be affected by the SNe themselves. The one exception is SN2017gax which was observed by PHANGS–MUSE shortly after the SN and contains the spectrum of the explosion. As a result, we remove this object from our sample.

In addition to the MUSE data, we compare SN locations to new narrowband H$\alpha$ emission maps from the *Hubble Space Telescope* (P.I. R. Chandar; R. Chandar, A. Barnes et al. in preparation). These are similar to the map of NGC 1672 presented in (cite: Barnes2022) with similar processing applied. Because they are diffraction limited at $\approx 0.1\ensuremath{''}$ resolution (2.6-9 pc linear resolution), they offer a much sharper view of H$\alpha$ emission and H II regions than VLT-MUSE but with worse surface brightness sensitivity. Because these data are quite new and still in a preliminary state, we use them here primarily for a qualitative comparison to the MUSE results in §[3.6](#sec:Zooms).

We trace molecular gas surface density using CO (2–1) maps from the PHANGS–ALMA survey (cite: Leroy2021). These data have similar resolution to the MUSE H$\alpha$ maps and we use them to assess the presence of cold, molecular gas in the vicinity of H II regions where SNe are detected. CO (2–1) emission is a standard tracer for the cold, dense, star-forming phase of the ISM (cite: Bolatto2013). Here we primarily focus on the detection of CO emission, reporting if there is significant (signal-to-noise $>$ 3) CO (2–1) emission present. For a more detailed analysis of CO (2–1) emission at the sites of SNe explosions in the PHANGS galaxies, with more description of how we handle the PHANGS–ALMA CO (2–1) data, see (cite: MaykerChen2023a).

We also use near-infrared (near-IR) emission to trace the overall distribution of stellar mass in our targets. This allows us to construct control measurements that predict the amount of chance coincidence between SNe and H II regions expected for normal (not just massive) stars. We trace the surface density of stellar mass using near-IR ($3.6\mu$m) maps from the Infrared Array Camera (IRAC) on the *Spitzer Space Telescope*. These were mostly obtained or reprocessed as part of the S$^{4}$G survey (cite: Sheth2010) and details of their processing and origin in the context of PHANGS is described in (cite: Querejeta2021). We use the near-IR intensity for this purpose and do not make any corrections to account for local variations in the stellar mass-to-light ratio.

## SN selection

Following (cite: MaykerChen2023a), we gather a population of recent ($<$ 125 years) SNe using the Open Supernova Catalog (OSC)[^1] and the Transient Name Server (TNS)[^2] . We are interested in SNe that have exploded recently and therefore have not had enough time to influence their surrounding environment. A typical early-stage SN shock with velocity of $10^4$ km s$^{-1}$ (cite: Draine2011) will only have expanded $\sim$1 pc in 100 years, which is much smaller than the resolution of our data. The Open Supernova Catalog also records supernova remnants, which can confuse this selection. To avoid including these, we only select SNe that have a recorded discovery date.

We select a population of 32 SNe within 10 galaxies in the PHANGS–MUSE galaxy footprints. Table [\[tab:galaxyTable\]](#tab:galaxyTable) lists the SNe along with their host galaxy, type, right ascension and declination, whether they are included in our project sample, and the reference paper used for their type classification. A total of 36 SNe in 11 galaxies were originally identified, but we do not analyze two SNe (SN2013ej in NGC 0628 and SN1979C in NGC 4321) because they lie just outside of the map coverage. We remove SN2019krl in NGC 0628 because of uncertainty in its type classification and the likelihood that it is instead a non-terminal explosion (cite: Andrews2021), and finally we remove SN2017gax in NGC 1672 because it was imaged shortly after explosion and the SN’s light has dominated the spectrum. This reduces our working sample to 32 SNe within 10 galaxies, $19\%$ (6/32) are SNe Ia, $59\%$ 19/32 are SNe II, $13\%$ (4/32) are SESNe, and $9\%$ (3/32) are unclassified. We show their locations in Figure [1](#fig:MUSEGalaxies). In Table [\[tab:supernovaeTable\]](#tab:supernovaeTable) we report the type classification, native H$\alpha$ map resolution, H$\alpha$ intensity measured at the SN site, the velocity dispersion, extinction, H II region status, BPT diagnostic line classifications, presence of CO (2–1) emission, directly measured H II region metallicities (when available) and calculated metallicities using galaxy gradients, galactocentric radius, and effective radius of each SN site.

The measurement of the spatial coincidence of SNe and H$\alpha$ emission is limited by the resolution of the MUSE data and the positional accuracy of the SN location. The MUSE resolution usually represents the limiting factor for SNe detected in the last few decades, but for the older half of our sample the location of the SNe may also contribute uncertainty.

Assessing positional uncertainties in the SNe precisely is complicated because the OSC, TNS, and the vast majority of SN discovery papers do not report positional uncertainties. To estimate a typical positional uncertainty for our SNe, we examine a wide selection of individual SN discovery papers and observe the change in the reporting confidence from discoveries that took place in the mid-1900s and those that have occurred in the last few years. We find that SNe that have occurred in the last $\sim20$ years are more likely to report uncertainties in their position—ranging from 0.1 to 1$''$ (cite: Evans2003; Monard2008; Pignata2009) and recent SN discovery papers that do not report uncertainty, their position is reported to the nearest 0.1 to 1$''$ as well. Because of this, we assume that for modern SN searches like ASAS-SN (cite: Shappee2014; Kochanek2017), a typical positional uncertainty will be $\lesssim 1$$''$. However positional uncertainties for early SNe, such as SN1926A, could be as high as $\sim10$$''$.

Half (16/32) of our sample has occurred within the last 20 years. We consider that for these, the positional uncertainty is of the same order as the angular resolution of MUSE maps, while for the remaining half, the uncertainty in the astrometry is dominated by the uncertainty in the reported SN location.

## Relative positions of SNe, HII regions, and statistical controls

We measure whether each SN occurs inside a known H II region, note the distance to the nearest pixel in the H II region[^3] for SNe outside H II regions, and record the intensity of H$\alpha$ emission at each SN. Because our galaxies have extended H$\alpha$ emission and often have a large fraction of their area covered by H II regions, we also construct several control scenarios to assess the probability of random coincidence. Similar to (cite: MaykerChen2023a), we use several model populations as controls to help interpret our measurements for our real SN sample. We consider these cases:

1.  *Purely random:* In this case, SNe are equally likely to occur in each pixel of the map, leading to a purely random distribution.

2.  *Random within the local region around the SN:* We also consider a scenario where the SN occurs randomly at a position within a $500~\textrm{pc} \times 500~\textrm{pc}$ or $1~\textrm{kpc} \times 1~\textrm{kpc}$ box centered on the SN explosion. This is intended to capture that some other variable might cause SNe to explode in a general region of the galaxy and to test for chance small-scale coincidence between H II regions and SNe once the general SN location is set.

3.  *Following the H$\alpha$ distribution:* In this case, the likelihood for a SN to occur on any pixel is proportional to the intensity of H$\alpha$ emission at that location in the MUSE maps. We expect that our population of CCSNe to be better represented than the SNe Ia for this model due to the short delay-times of their progenitors.

4.  *Following the stellar disk traced by near-IR emission:* In this final control case, SNe are drawn based on the intensity of the near-IR maps described in §[2](#sec:Methods). This helps model SNe that trace the distribution of stellar masses, which should be appropriate for populations with longer delay times, e.g., SNe Ia (cite: Maoz2014; Anderson2015a; Cronin2021).

We generate 1,000 model SNe for each SN in our sample. This gives us a total of 32,000 model SNe from 10 galaxies generated for each model. We calculate the expected coincidence between these model distributions and the (cite: Groves2023) H II regions. Following (cite: MaykerChen2023a) we also calculate the expected overlap with CO emission and with both CO emission and the presence of an H II region in the line of sight for each case. Figure [3](#fig:Models) shows examples of these control distributions for one galaxy. Table [\[tab:types\]](#tab:types) reports the coincidence between SNe and H II regions expected for each of these models. We also compare the cumulative distributions of the models to our real SN sample in Figures [6](#fig:Distances) and [8](#fig:TypeIntensityCDFs).

![](NGC4303Models.png)

# Results comparing H$\alpha$ emission to SN location

In Figures [1](#fig:MUSEGalaxies) and [2](#fig:MUSEGalaxies_cont) we plot the PHANGS–MUSE H$\alpha$ maps for our sample of galaxies with SNe. We show the maps at their native resolution, which ranges from $0.78{-}1.16\ensuremath{''}$, and mark the locations of recent SNe in each galaxy. In this section we analyze the fraction of SNe that appear coincident with an H II region (§[3.1](#sec:HIIregions)) and compare these results with expectations from single stellar population (SSP) models (§[3.3](#sec:SSP)), measure the distance of SNe from H II regions (§[3.4](#sec:HIIregionsDist), [3.2](#sec:types)), the intensity of H$\alpha$ emission at the sites of SNe (§[3.5](#sec:HaEmission)), and the relative position of H$\alpha$ emission and SNe at high resolution (§[3.6](#sec:Zooms)).

## Fraction of SNe in H II regions

![](NGC4303.pdf)

As described in §[2](#sec:Methods), we use the (cite: Groves2023) nebular catalog to identify pixels where H II regions lie along the line of sight through the galaxies. Figure [4](#fig:4303HII) illustrates these H II region contours for one target, NGC 4303. It shows that H II regions cover a large area of the disk of the galaxy and encompass much of the bright H$\alpha$ emission. Across our sample, about $74\%$ of the total H$\alpha$ emission arises from pixels identified as H II regions in the native resolution maps. The rest of the emission is associated with the extended diffuse ionized gas component (cite: Belfiore2022).

Table [\[tab:types\]](#tab:types) summarizes our basic results. We find that 41% (13/32) of our SNe occur coincident with an H II region. For comparison, across our galaxy sample, 13.7% of map pixels are coincident with H II regions. This means that if assigned to pixels randomly, 1/7 (4.4/32) of all SNe would occur along a line of sight that intersects an H II region.

The PHANGS–MUSE images often cover a large portion of a galaxy, including both the dense, high surface density inner regions and spiral arms and the more extended, lower surface density regions. As a result, some of the observed coincidence between SNe and H II regions may result from the SNe simply occurring in denser parts of galaxies where both H II regions and stars are more common. To account for this, we also construct a set of more localized comparisons, in which we compare the fraction of SN locations with detected H II regions to only the fraction of area covered by H II regions in nearby pixels. Here we define “nearby” as boxes $500 \times 500$ pc or $1 \times 1$ kpc in size centered on each SN. The goal with this more stringent control is to test the idea that SNe occur specifically concentrated within HII regions.

Adopting this more stringent control, the results indicate that 32% of pixels within $1~{\rm kpc} \times 1~{\rm kpc}$ local regions centered on our SN sites belong to a (cite: Groves2023) H II region. This fraction increases to 36% if we instead consider fields of size $500~{\rm pc} \times 500~{\rm pc}$. This means that if we allow that SNe are occurring in a given part of the galaxy, then we expect that $\sim 32-36\%$ will occur along the line of sight to an H II region simply due to random chance.

As an alternative control, we also examine the fraction of total near-IR emission arising from within the H II regions. The near-IR traces the overall distribution of stellar mass. We find that 32% of near-IR emission emerges from regions coincident with H II regions. Similar to the “local region” control, treating the near-IR as a control distribution suggests that we would expect a third of our SN sample, or about 10 SNe, to lie within the H II regions just by coincidence alone.

Thus both the local region control or using the near-IR suggest that we might expect one-third of SNe to occur near an H II region by chance. We emphasize that this calculation is focused on coincidence *along the line of sight at the MUSE resolution*. The actual position of the SNe along the line of sight is uncertain and the MUSE sizes may represent overestimates of the true H II region sizes (cite: Barnes2022). On the other hand, it is still of physical interest that so many SNe appear to be located *near* (rather than in) H II regions by coincidence. This proximity provides an opportunity for interactions between SNe and ionized gas interactions during the SN remnant phase. SN explosions in or near H II regions, even if by coincidence, also represent locations where different modes of feedback potentially amplify one another, indicating places where multiple generations of SNe are able to clear out larger volumes of gas.

Our measured SNe-H II region coincidence of $\approx 41\%$ is higher than either the $\approx 32{-}36\%$ suggested by the local models or the $\approx 32\%$ suggested by the starlight distribution. This indicates that some SNe *do* preferentially occur in H II regions, but also that controlling for random coincidence is critical to estimate the rate. Using a binomial distribution we estimate the uncertainty due to stochasticity to be $\pm 8.7\%$.

Contrasting these local covering fractions with the fraction of SNe coincident with H II regions, we find a general excess of 7.6% $\pm$ 8.7% of all SNe to be associated with H II regions. In the next section, we separate our SN sample by type, specifically focusing on CCSNe which we expect to be more associated with star forming regions of galaxies.

## Breakdown by type

| Type | H II region | H II $+$ CO | CO only | Excess |
|:---|:--:|:--:|:--:|:--:|
| All SNe (32) | 41% (13) | 34% (11) | 22% (7) | 7.6% $\pm$ 8.7% |
| SESNe: IIb/Ib/Ic (4) | 100% (4) | 75% (3) | 0% (0) | 38% $\pm$ 23.5%$^{a}$ |
| SNe II (19) | 42% (8) | 37% (7) | 21% (4) | 10.5% $\pm$ 11.3% |
| SNe Ia (6) | 17% (1) | 17% (1) | 17% (1) |  |
| Unclassified (3) | 0% (0) | 0% (0) | 67% (2) |  |
| H$\alpha$ Emission | 73% | 69% | 16% |  |
| Near-IR (3.6$\mu$m) Emission | 32% | 23% | 28% |  |
| Random Map Pixel | 14% | 9% | 22% |  |
| Random Local (1 kpc) | 32% | 26% | 34% |  |
| Random Local (500 pc) | 36% | 30% | 31% |  |
|  |  |  |  |  |

Table [\[tab:types\]](#tab:types) shows the fraction of SNe coincident with H II regions broken down by type. We find that 20% (1/6) of SNe Ia, $42\%$ (8/19) of SNe II, and 100% (4/4) of our stripped envelope SNe (SESNe; Types II, Ib, & Ic) occur coincident to H II regions. The sense of these results are consistent with that found by previous lower resolution work (cite: Anderson2012; Anderson2014; Anderson2015; AudcentRoss2020), which identified that increasing progenitor mass leads to increasing association with bright H$\alpha$ emission. As a reminder the progenitor mass sequence from lowest to higher is believed to be SNe Ia $\rightarrow$ SNe II $\rightarrow$ SESNe .

The mild 6% excess of SN in H II regions becomes more prominent when we consider only CCSNe. CCSNe (II and SESNe) have an excess of 19.2% $\pm$ 10.4% coincident to an H II region, and when considering only SESNe we find an excess of 38% $\pm$ 23.5%. Although the SESNe sample is extremely small (only 4 SNe) the probability of our controls randomly placing SNe coincident to an H II region 4/4 times is only 1.2%. The physical association is also expected, because SESNe are thought to originate from the most massive stars. These will also be the earliest stars to explode. They may therefore be within or near to their birth sites, and likely to still be bright in $H\alpha$ emission.

Thus, with the caveat that our controls suggest that random overlap may explain some of our measured associations, the differences among types matches physical expectations. Because H II regions mark where young, massive stars have formed very recently, the SNe with the highest mass progenitors should be more likely to occur near these regions as they explode first. H II regions have lifetimes of $\lesssim 5{-}10$ Myr, similar to the lifetime of a single massive star. Lower mass CCSNe with delay times of $\sim 10{-}30$ Myr are more likely to outlive their birth H II region and will have more time to migrate away from the high density regions where they formed. We do not expect SNe Ias to have association with star-forming regions due to their long delay times, but we do expect that a fraction of SNe Ias will occur coincident with an H II region just because the H II regions cover an appreciable fraction of the galaxy.

We note that none of the unclassified SNe occur in H II regions. By contrast, (cite: MaykerChen2023a) found that most of the unclassified SNe occurred in regions that did have bright CO emission, but they worked with a sample about twice as large as the current work.

Finally, we note that our limited sample size might lead to a sample that does not accurately reflect the broad SN landscape. Of specific interest here, previous SN surveys find that SESNe make up 25-30% of CCSNe (cite: Smartt2009; Li2011a), while only 12.5% of our sample are SESNe. Given the high degree of association that we observe between the SESN and the H II regions here, a more representative sample with more SESN would likely show a somewhat higher overall coincidence between SNe and H II regions.

## Comparisons to expectations from SSP Models

![](SNtimescale.pdf)

Our analysis suggests that $\sim20\%$ of CCSNe preferentially explode in H II regions. How does this compare to expectations? In Figure [5](#fig:SNtime) we plot results for a simple stellar population (SSP) using the default assumptions from STARBURST99 (cite: Leitherer1999; Leitherer2014). We plot the cumulative distribution functions (CDFs) as a function of time for both number of SNe explosions and H ionizing photon production, which should map to H$\alpha$ emission.

In the SB99 model, the delay-time for CCSNe ranges from $3-37$ Myr, with the first $20\%$ of SNe occurring by 7.11 Myr. This is consistent with the H$\alpha$ brightness drop off which occurrs significantly by $\approx$7 Myr and the CDF of H$\alpha$ emission (or H ionizing photon production) shows that most of the H$\alpha$ has been produced before that time.

If star-forming regions in our targets are indeed accurately described by an ensemble of SSPs, then our inferred SNe associated with H$\alpha$ would likely need to be associated with high-mass progenitor stars with lifetimes shorter than $\approx$7 Myr or with a binary core collapse SN production channel that operates on a similar timescale. To be precise, the first $20\%$ of the SNe in this SSP calculation occur by $7.11$ Myr and represent stars with masses $>24.9$ M$_\odot$.

In reality, the picture will be more complex than this. Supernova explodability work by (cite: Sukhbold2016) shows that the most massive stars have a much lower frequency of exploding, although there is no clear-cut boundary between explosions and non-explosions, the probability of successful explosions is less as you go above $20~M_\odot$, with the most massive stars requiring significant mass loss in order to explode. On the other hand, binary star systems extend the H$\alpha$ emitting lifetime and open more complex mappings between progenitor mass and explodability and different evolutionary timescales (cite: Eldridge2011; Vartanyan2021; Nguyen2022; Patton2022). Likely, many of the regions we examine are also not SSPs, but host multi-generation or extended-duration star formation (cite: Rahner2017). Another caveat is that the Starburst99 models assume a fully-sampled IMF, which is likely valid for the galaxy as a whole but may not be true for many of the individual regions, depending on the mass of the powering star cluster.

## Distance from SNe to H II regions

Even when SNe are not directly associated with H II regions, we might expect those associated with very massive stars to be near such regions. To test this, we also calculate the distances to the nearest pixel tagged as an H II region in the (cite: Groves2023) catalog for each of our SNe.

The left panel of Figure [6](#fig:Distances) shows the kernel density estimation (KDE) of the distances from each SN to the nearest H II region, where the SN population is separated by type. Vertical color-and-style-coded lines mark the median distance value for each SN type. We shade the typical MUSE spaxel size in gray. The figure shows that our SESNe are always occurring coincident to H II regions, our SNe II are more frequently found away from H II regions than our SESNe, with a median distance of 10 pc. Although, our SNe Ia are often found farther away from H II regions with a median distance of 110 pc, they are still relatively close. The overall low distances even for SNe not directly associated with H II regions reflects that PHANGS-MUSE targets the actively star-forming parts of galaxies. As a result, H$\alpha$ emission is prevalent throughout the maps and even a SN associated with an older progenitor is still likely to occur close to an H II region.

Similar to (cite: MaykerChen2023a), we compare the measured SNe-H II region separations for our real SN sample to those produced for the model populations described in §[2.3](#Analysis). In the right panel of Figure [6](#fig:Distances) we show the cumulative distributions of the distances to the nearest H II region for both our real SN sample (32 SNe) and each of our four model SN populations (32,000 SNe generated for each model). We find that the distribution of our real SN population lies in between the model population that follows the distribution of H$\alpha$ emission and the model populations drawn from either the distribution of stellar mass or local regions around the real SN location. This reinforces the results above that while SNe are more associated with H II regions than the general stellar population, they do not directly trace the distribution of H$\alpha$ emission.

## Intensity of H$\alpha$ emission at the locations of recent SNe

![](resolutionNCR.png)

![](IntensityCDFs.pdf)

So far, we have considered only whether a sight line is coincident with an H II region. The intensity of H$\alpha$ emission provides additional information, tracking the production rate of ionizing photons and potentially conveying additional information on the distribution of massive, young stars within an individual H II region. To leverage this information, we also measure the intensity of H$\alpha$ emission at the site of each of our SNe and report the results in Table [\[tab:supernovaeTable\]](#tab:supernovaeTable).

Figure [7](#fig:resNCR) shows the normalized cumulative rank (NCR) of SNe relative to the distribution of H$\alpha$ emission at native, 150 pc, and 1 kpc resolutions. An excellent overview of the NCR method is given in (cite: James2006). Briefly, we sort the pixels in each H$\alpha$ map by H$\alpha$ intensity, assigning a percentile in the CDF to each. Then we note the percentile of the H$\alpha$ intensity CDF for the pixel at which each SN occurs and so construct the NCR of SNe relative to H$\alpha$. If the SNe occur in locations that track the distribution of H$\alpha$ intensity, then the measured curve will follow a line with slope unity. This analysis emphasizes coincidence between SN sites and H II regions and could be impacted if the SNe and stellar winds cleared the surroundings of ionized gas. Although we do not expect our SN sample to have had time to dramatically influence their local environments, we address this in § [3.6](#sec:Zooms) where we plot the local ($500~\times~500~pc$) environments of each SN and look for signs of shell-like morphology in the H$\alpha$ emission.

Consistent with the finding above that SNe appear in H$\alpha$-rich parts of galaxies, but not necessarily within H II regions themselves, Figure [7](#fig:resNCR) shows that our SNe sample tracks the H$\alpha$ emission more directly as the resolution becomes coarser. The fact that the lines are above and to the left of the one-to-one line means that actual SNe occur at lower $I_{H\alpha}$ on average than we would expect if the probability to find a SN tracked the distribution of H$\alpha$ emission exactly. The better agreement at coarser resolution reflects that at lower resolution, the beam of the telescope captures more of a region-average measurement of star formation activity, while at higher resolution we are able to better isolate individual H II regions, and we observe that SNe appear somewhat offset from these regions.

In Figure [8](#fig:TypeIntensityCDFs) we plot the CDF of H$\alpha$ intensities at the sites of our real SN sample (32 SNe), the CDF for all H$\alpha$ emission at the native (44–109 pc) resolution of the MUSE maps, and the CDF of H$\alpha$ intensity generated for each of the the three model populations described in §[2](#sec:Methods). In the top panel we show results for our whole SN sample, and in the bottom panel we separate the SNe by type. Shaded regions represent the $16^{\rm th}{-}84^{\rm th}$ percentile range covered by repeat realization of the models.

Similar to results with the distances from H II regions, we find that the distribution of H$\alpha$ intensities at the real SN sites falls somewhere between the distributions for the model SNe generated from the near-IR light and the model SNe generated from the H$\alpha$ intensity. We expect that the higher mass progenitors would have a closer association with the H$\alpha$ distribution, while the lower mass CCSNe and SNe Ia would have a distribution that more closely resembles that taken from the overall stellar population traced by near-IR emission.

When we separate the SNe by type, we find the SNe Ia to exhibit a similar distribution to the map pixels or the near-IR emission. This agrees well with the expected lower mass range and wide age range of SN Ia progenitors. As the progenitor mass increases, we find an increasing association with higher H$\alpha$ intensity values, reaffirming the results of previous works (cite: Anderson2012; Anderson2014; Anderson2015). Of particular note, the SESNe (SNe Ib/c) show a distribution very similar to the H$\alpha$ maps themselves, supporting a direct association with high mass progenitors.

## Zooming in on individual regions and comparison to *Hubble Space Telescope imaging*

![](HST_MUSE_Comp.png)

In the figures in Appendix [\[appendix\]](#appendix), we zoom in to each SN site, plotting $500~{\rm pc} \times 500~{\rm pc}$ cutouts of H$\alpha$ emission around each of the 32 SNe in our sample as well as marking the footprint of regions in the (cite: Groves2023) nebular catalog. We show an example of one such cutout in the left panel of Figure [9](#fig:example_zoom). These cutouts demonstrate that many of these SNe appear in or near regions rich in H$\alpha$ emission. They also show that, while many SNe occur within the footprint of the nebular regions, none are actually coincident with the local peak of H$\alpha$ emission. Instead, the SNe tend to lie off to the side, often near the edges of the regions, and are associated with lower intensity H$\alpha$ emission.

To test this hypothesis further, we take advantage of very new, high-resolution ($\sim$0.1$''$) narrowband H$\alpha$ imaging of these targets using the *Hubble* Space Telescope (P.I. R. Chandar; Chandar, Barnes et al., in preparation). As illustrated in the right panel of Fig. [9](#fig:example_zoom), these data have been processed following a scheme similar to that described in (cite: Lee2022) and (cite: Barnes2022). Here we use the data to provide a $\sim 10\times$ sharper view of the H II regions compared to MUSE. Though the surface brightness sensitivity of HST does not match MUSE, the resolution of these data ($\sim 5{-}15$ pc) more closely matches the physical sizes of H II regions seen in the Milky Way (cite: Anderson2014).

In Figure [14](#fig:HST) we remake the cutouts above using these HST H$\alpha$ data, again marking the locations of the (cite: Groves2023) H II regions and significant CO (2–1) emission. At the diffraction-limited, high resolution of HST, the H II regions seen by MUSE are significantly more resolved, appearing smaller and significantly better-defined. Many SNe located within the edges of H II regions in the MUSE maps (e.g., SN1995V and SN1983V) appear offset from the H II regions in the sharper HST maps. In fact, *none* of the SNe with HST H$\alpha$ coverage actually lie on a high resolution H$\alpha$ peak, though we caution that the astrometric precision with which the SNe are located makes it hard to draw a firm conclusion.

Examining these images, especially the HST images, reinforces the statistical finding above that a large fraction of the SNe coincident with the (cite: Groves2023) H II regions are likely to represent chance alignments. The overall active star-forming nature of the regions where the SNe occur and the relatively coarse physical resolution of the MUSE data lead to a large fraction of chance overlaps.

We might expect that pre-SN feedback would result in a shell-like morphology for the H$\alpha$, with lower densities of ionized gas surrounding the stellar population and near the site of the SN itself. However, such a morphology is not immediately clear from our images. We overwhelmingly see that our SN sites are off to the sides of the H II region, rather than enclosed at least partially by shells. It is possible that the shells are too small to show up at the MUSE resolution and the lower sensitivity of the HST data.

We caution that the positional uncertainty for the SNe represents a major limiting factor when comparing to the HST H$\alpha$ data. As Figure [14](#fig:HST) shows, even in nearby galaxies, the angular size of individual H II regions and nebulae is very small, so that placing the SNe precisely relative to these features requires astrometric precision of order 0.1$''$. Given this, future work that leverages HST and JWST to constrain the origin and impact of SNe will require high-quality astrometric positions. With this in mind, we are reassured that many of the SNe that show this characteristic near-but-not-in appearance have been recently discovered and have correspondingly secure astrometry. Our results suggest that SN feedback is not occurring at the centers of star-formation sites, and could have implications for clustered feedback simulations.

Finally, we note that in our previous work (cite: MaykerChen2023a), we found a similar result when comparing the SN sites to molecular gas emission. The SNe associated with CO emission often appeared displaced from the CO peaks and near the edges of the detected regions. Those ALMA CO data have resolution $\approx 1\ensuremath{''}$, similar to the MUSE data. It will be telling to see whether at higher resolution the relative location of the SNe and the CO-traced molecular clouds similarly separate.

# Results comparing to other properties at the SN location

In §[3](#sec:ResultsHa) we examined the coincidence of H$\alpha$ emission and recent SNe. We found a large fraction of SNe to occur along lines of sight that overlap H II regions, but also showed that much of this overlap is likely to be coincidental. Both higher resolution imaging and statistical analysis suggest that many SNe occur near but not necessarily within H II regions, with our best estimate that there is a $\approx 20\%$ excess of CCSNe associated with H II regions relative to the controls.

In this section, we expand our analysis to consider other properties near the SN sites, examining the coincidence of H$\alpha$ and CO emission at SN sites (§[4.1](#sec:HACO)), the extinction towards the ionized gas near SN sites (§[4.2](#sec:BD)), and a variety of other diagnostics available from the (cite: Groves2023) and (cite: Emsellem2022) analysis of the MUSE data (§[4.3](#sec:Additional)).

## H$\alpha$ and CO

Newly-formed stars can remain embedded within their parent molecular clouds, with the mass of molecular material commonly traced by CO emission. In recent models of molecular cloud evolution, star-forming regions go through early phases in which newly formed stars still lie within their parent molecular cloud with H$\alpha$ emission almost undetectable (cite: Lockman1989; Kim2021). Over time, the cloud is exposed to various forms of feedback which begin to disperse the natal cloud. This dispersal leads to phases in which the cloud is partially dispersed and H$\alpha$ and CO might be detected together and then as the cold gas becomes mostly dispersed, CO emission vanishes, but the H$\alpha$ emission remains fully visible (cite: Kawamura2009; Kruijssen2014; Kruijssen2018; Kim2022).

By combining the MUSE H$\alpha$ maps with CO (2–1) measurements from PHANGS–ALMA (see §[2](#sec:Methods)), we identify which SNe in our sample occur coincident with only CO (2–1) emission, an H II region, both, or neither. To do so, we repeat our control scenarios listed in §[2.3](#Analysis) and list our results in Table [\[tab:types\]](#tab:types). We also overplot the locations of CO (2–1) emission with a signal of 3 times the noise or higher in the zoom panels in Appendix [\[appendix\]](#appendix). Throughout, to count as a detection of CO (2–1) emission, we require a signal-to-noise ratio of 3 in the integrated intensity maps masked with a “broad” mask[^4]. Note that here we focus on the joint detection statistics for CO and H II regions in this MUSE sample; (cite: MaykerChen2023a) show a more extensive analysis considering only CO for the full PHANGS–ALMA sample.

We find that $34\%$ of all SN sites are coincident with both an H II region and CO (2–1) emission, while $22\%$ are not associated with an H II region yet are coincident with significant CO (2–1) emission. Contrasting these with the control calculations, the CO-only sightlines appear largely consistent with random coincidence; that is, the percentage of real CO-only sightlines resembles that in the local or near-IR controls. Both the overall H II region and the H II+CO detection rates show an excess relative to these controls.

Similar to the H II regions without CO (2–1) emission, there is an increasing association of progenitor mass with H II + CO (2–1), with $17\%$ SNe Ia, $37\%$ SNe II, and $75\%$ SESNe found in H II + CO (2–1). However, this association breaks down when we consider only CO (2–1) emission without a corresponding H II region, which occurs for $17\%$ of SNe Ia, $21\%$ of SNe II, and $0\%$ of SESNe. Of note, $67\%$ of our unclassified SNe are found in CO-only regions, while none appear associated with H II regions. This follows (cite: MaykerChen2023a) where the unclassified sample had a high correlation with dense CO (2–1) gas. It is possible that these unclassified SNe are exclusively going off in embedded star-forming regions, and the occurrence in high extinction areas might account for the difficulty in providing a classification for the SN, but it is worth noting that the discovery years for our three unclassified SNe range from 1901–1959, when both spectroscopic and localization data were more uncertain than for modern SNe.

Our calculations thus show that when a SN appears coincident with an H II region *it almost always also appears coincident with CO (2–1) emission*. Note that previous work on the CO-H$\alpha$ correlation has shown a significant de-correlation between these two tracers at high resolution (cite: Schruba2010; Kruijssen2019; Schinnerer2019; Pan2022; Leroy2023). Those observations helped to establish the picture described above and suggest an important role for pre-SN feedback in clearing gas (cite: Chevance2020; Chevance2022). The prevalence of CO detections coincident with SNe and H II regions in our results may seem to contradict this result. However, we note a few points. First, $59\%$ of our SNe are *not* detected coincident with H II regions and there does not appear to be any statistically significant excess of SNe associated with CO outside H II regions. So in good agreement with (cite: MaykerChen2023a), many SNe do appear unassociated with recent star formation or molecular gas. Second, our control calculation suggests that to some degree the correlation that we do see simply reflects that we are capturing SNe in higher SFR parts of galaxies. Finally, we note that the resolution used for this calculation is still coarse. As we saw in §[3.6](#sec:Zooms), H II regions are still small compared to the MUSE resolution, and the same is likely true of the molecular gas and ALMA. As a result, many of the joint H II region-CO detections likely reflect complex regions with multi-generational star formation blended together by the $\sim 50{-}150$ pc resolution of the VLT and ALMA. Even with these caveats, the result here seems intriguing to us and worth investigation using higher resolution CO as well as H$\alpha$ data.

## H$\alpha$ and the Balmer Decrement

![](ExtinctionHist.png)

The PHANGS-MUSE maps capture the extinction towards the ionized gas along each line of sight via the H$\beta$/H$\alpha$ ratio, the Balmer decrement. This allows us to assess the degree to which SNe preferentially occur in high extinction regions. This local extinction may impact the observability of SNe in surveys of more distant systems. Because gas and dust are mixed, the extinction also gives an alternative probe of the degree to which SNe explode near high column density gas. To test this, we measure extinction, expressed as $A_V$ values, based on the Balmer decrement along the line-of-sight towards each of our SNe. We adopt the calculations from (cite: Belfiore2023; Belfiore2022), which adopts $R_{\rm V} = 3.1$ and an (cite: Odonnell1994) extinction curve. Note that this measurement captures the extinction towards the ionized gas along the line of sight (assuming a foreground screen geometry), which may or may not be identical to the extinction towards the SN itself.

In Figure [10](#fig:ExtHist), we plot the resulting histograms of extinction, expressed as $A_V$, towards SN sites, separating those coincident with an H II region from those outside H II regions. For comparison, we also plot the KDE of all pixels in the MUSE maps for our targets. The figure shows that our SNe occur in regions with extinction values ranging from $A_V = 0{-}2.35$ mag. The sites that are not coincident with H II regions tend to have lower extinction, median $A_V=$ 0.33 mag with a $16{-}84\%$ range of 0–0.92 mag[^5], than the SN sites associated with H II regions, which have median $A_V=$ 1.03 mag with a $16{-}84\%$ range of $0.75-1.47$ mag. These values resemble typical values found in the MUSE maps overall. In those maps a mean $A_V$ outside H II regions is $A_V \approx 0.4$ mag and the mean $A_V$ associated with nebular regions is $A_V \approx 1.1$ mag. The lower extinction for non-H II regions is well-known (cite: Calzetti2001).

These results indicate that SNe appear associated with typical extinctions, providing no strong evidence that there is a large population of deeply embedded SNe. We note that, because we study very nearby galaxies (compared to the distance out to which SNe tend to be detected in modern broader SN searches), it would be reasonable to expect even quite embedded SNe to be detected in these targets. Despite this, the highest extinction value associated with any SN in our sample is $A_V =$ 2.35 mag.

The fact that we do not appear to find evidence for high extinction towards SNe in normal star-forming galaxies agrees with previous works that show the extinctions around SNe II to be generally small (cite: Pejcha2015). We note that the evidence for significant populations of hidden or high-extinction SNe comes primarily from studying U/LIRG or starburst systems (cite: Fox2021). In those systems, star-forming regions themselves are also found associated with high extinction and primarily visible in the radio or infrared (cite: Sanders1996). Thus a more general phrasing of our results might be: our measurements support the idea that SNe occur at typical extinctions for their host galaxies, and are not particularly concentrated towards the highest or lowest $A_V$.

The modest extinctions that we measure towards SNe also support the idea of significant pre-SN clearing of material. The typical extinction of $A_V \sim 1$ mag that we find towards H II regions with SNe corresponds to $\sim 20$ M$_\odot$ pc$^{-2}$ for a typical dust-to-gas ratio. For comparison, the surface densities associated with star formation tend to be $\sim 100$ M$_\odot$ pc$^{-2}$ (cite: Kennicutt2012). Thus, also judging by extinction, most of the SNe in our sample appear to occur in regions where the progenitor has separated from its natal cloud.

## Additional Diagnostics

![](MetallicitiesSwarm.png)

The (cite: Groves2023) catalog provides a treasure trove of information that can be used to further characterize the properties of ionized gas. We note several of these additional diagnostics for each of our SN sites in Table [\[tab:supernovaeTable\]](#tab:supernovaeTable):

1.  *BPT classifications (\[NII\], \[SII\], \[OI\])*:\
    The BPT emission line diagnostics (cite: Baldwin1981) are used to classify emission as coming from either star-forming regions, active galactic nuclei (AGN), low-ionization nuclear emission line regions (LINERs), or a composite of more than one (cite: Groves2023). We record the BPT emission line diagnostics for each of our SNe that occur along the line-of-sight to a nebular region. Of the 13 SNe associated with cataloged nebulae, all but two have all BPT diagnostics consistent with arising from star forming regions (i.e., reported as values of 0.0 in (cite: Groves2023)). SN1997bs & SN 2019ehk have two out of three emission line diagnostics consistent with star formation with the remaining line diagnostic indicative of a S/N ratio lower than 5 (non-informative, labeled as -1.0). This indicates that these are likely H II regions but also might have an additional source of emission within the nebula.

2.  *Metallicity (12 + log (O/H))*:\
    In Figure [11](#fig:met) we plot the estimated metallicity at each SN site. These estimates use the metallicity reported in (cite: Groves2023) based on “Scal” metallicity estimates (cite: Pilyugin:2016) for individual H II regions. We also plot the specific metallicity values estimated at individual H II regions for the subset of SNe within an H II region.

3.  *Velocity dispersion measured from ionized gas ($\sigma$)*:\
    The velocity dispersion estimated from the ionized gas may give clue as to whether H$\alpha$ emission is coming from an H II region or shocks, e.g., driven by winds or even the SN itself due to late-time CSM interactions. We therefore also record the velocity dispersion ($\sigma$) of the H$\alpha$ emission at each SN site. None of our SN sample show signs of broadening with $\sigma \gg 100$ km s$^{-1}$.

The nebulae coincident with our SNe appear consistent with normal H II regions. The metallicities that we record are informational and potentially of use in broader future studies, such as determining the metallicity dependence on the rates of individual SN types (cite: Pessi2023). Our own sample lacks a wide range in metallicity and the heterogeneous nature of our SN compilation makes it poorly suited to study SN rates.

# Discussion and Summary

We have analyzed the coincidence of recent ($\lesssim 125$ yr old) supernovae (SNe) with H$\alpha$ emission in the PHANGS–MUSE survey (cite: Emsellem2022). Within the $19$ PHANGS–MUSE targets, we identify $32$ SNe in $10$ galaxies that lie within the footprint of the MUSE observations and meet our criteria for being included within our sample.

1.  We find that $41\%$ (13/32) of the SNe within the PHANGS–MUSE footprint occur coincident with one of the H II regions identified by (cite: Groves2023) (see §[3.1](#sec:HIIregions) & Table [\[tab:types\]](#tab:types)). The majority of these SNe (11/13) are also coincident with CO (2–1) emission (§[4.1](#sec:HACO)).

We construct a series of models to test how much of this SNe-H II region overlap may result from chance alignment (§[2.3](#Analysis)).

2.  Based on controls using the near-IR emission from the galaxy or considering random placement within a $500{-}1,000$ pc-sized region around the SNe, many of the SNe found coincident with H II regions are likely to be associated by chance. Overall, by chance alone we would expect $\approx 1/3$ of SNe to appear associated with H II regions for our targets and the MUSE resolution. This reflects that core collapse SNe tend to occur in regions of galaxies with a high density of star formation activity (§[3.1](#sec:HIIregions)).

3.  Examining the SN locations in new high resolution HST narrowband H$\alpha$ imaging (Chandar, Barnes et al. in prep.) confirms that SNe tend to explode *near* but not directly *in* H II regions traced by H$\alpha$ (§[3.6](#sec:Zooms)).

4.  After accounting for this chance overlap, our best estimate is that $\approx 19.2 \pm 10.4\%$ of CCSNe occur within and are associated with an H II region (§[3.1](#sec:HIIregions)). Consistent with other recent work, this low percentage implies a large role for stellar winds, photoionized gas pressure, and radiation pressure (i.e., “pre-SN” feedback) in clearing gas away from young stellar populations. It also implies that SNe are more likely to explode into lower density regions and thus affect a larger physical area (cite: Chevance2020; MaykerChen2023a; Sarbadhicary2023).

We validate this result by analyzing intensity statistics and the distance from each SN to the nearest H II region (§[3.4](#sec:HIIregionsDist) and [3.5](#sec:HaEmission)). SNe Ia, which originate from older progenitors, show a closer association with the older stellar population compared to core collapse SNe. By contrast, stripped envelope SNe (SNe Ib/c), which are believed to originate from high mass stars, show the most direct association with H$\alpha$ emission and H II regions out of our sample (§[3.2](#sec:types)). These results by type are in good agreement with previous lower resolution work on larger samples (cite: James2006; Anderson2012; Crowther2013; Galbany2014).

In addition to H$\alpha$ intensity, we examine extinction and other properties of the nebular regions associated with SNe.

5.  The Balmer decrement implies extinctions towards the ionized gas near SNe of $A_V \approx 0{-}2.35$ mag. We find no strong differences between the overall $A_V$ values in the PHANGS–MUSE maps and those at the sites of SNe. This appears consistent with modest measured $A_V$ towards core collapse SNe in normal star-forming galaxies (§[4.2](#sec:BD)).

Thanks to ASAS-SN, ATLAS, ZTF, and the upcoming *Rubin* LSST, we are in the era of high completeness SNe discovery towards nearby galaxies. Therefore we expect the kind of detailed, high physical resolution studies presented here and in (cite: MaykerChen2023a) to become increasingly possible and informative. We note two conclusions relevant to such next steps:

6.  High physical resolution, of order $10$ pc, is needed to isolate SNe within individual clouds or H II regions. Given that core collapse SNe often occur in complex regions of galaxies with active star formation, coarser resolution risks significant chance accidental alignment. This is also of order the resolution needed to resolve the likely cooling radius (and so the zone of influence) of SN explosions (cite: Kim2015; Martizzi2015).

7.  To achieve such high resolution, correspondingly high accuracy in the localization of SNe is required. Practically, to make best use of space telescopes or ALMA for such studies, SNe must be localized to better than $\pm$0.1$''$.

With these caveats in mind, the future in this area looks bright. JWST, HST, ALMA, and soon *Euclid* and *Roman* offer amazing prospects to localize SNe in the nearest galaxies and better understand the impact and origin of these explosions.

# Acknowledgments

NMC thanks the Ohio State University’s Galaxy and Supernova groups, including Christopher Kochanek, for useful discussions at several stages of the project. This work was carried out as part of the PHANGS collaboration.

Support for this work was provided by the NSF through award SOSP SOSPADA-010 from the NRAO, which supported the work of NMC. The work of NMC and AKL was partially supported by the National Science Foundation (NSF) under Grants No. 1615105, 1615109, and 1653300.

The work of AKL is partially supported by the National Aeronautics and Space Administration (NASA) under ADAP grants NNX16AF48G and NNX17AF39G. KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship (project number DE220100766) funded by the Australian Government.

KK, JEMD, and OVE gratefully acknowledge funding from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) in the form of an Emmy Noether Research Group (grant number KR4598/2-1, PI Kreckel) and the European Research Council’s starting grant ERC StG-101077573 (“ISM-METALS").

M.C. gratefully acknowledges funding from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) through an Emmy Noether Research Group (grant number CH2137/1-1). COOL Research DAO is a Decentralised Autonomous Organisation supporting research in astrophysics aimed at uncovering our cosmic origins.

This paper makes use of the PHANGS–MUSE data, based on observations collected at the European Southern Observatory under ESO programmes 094.C-0623 (PI: Kreckel), 095.C-0473, 098.C-0484 (PI: Blanc), 1100.B-0651 (PHANGS-MUSE; PI: Schinnerer), as well as 094.B-0321 (MAGNUM; PI: Marconi), 099.B-0242, 0100.B-0116, 098.B-0551 (MAD; PI: Carollo) and 097.B-0640 (TIMER; PI: Gadotti).

This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA CO (2–1) survey:\
ADS/JAO.ALMA#2012.1.00650.S\
ADS/JAO.ALMA#2013.1.00803.S\
ADS/JAO.ALMA#2013.1.01161.S\
ADS/JAO.ALMA#2015.1.00121.S\
ADS/JAO.ALMA#2015.1.00782.S\
ADS/JAO.ALMA#2015.1.00925.S\
ADS/JAO.ALMA#2015.1.00956.S\
ADS/JAO.ALMA#2016.1.00386.S\
ADS/JAO.ALMA#2017.1.00392.S\
ADS/JAO.ALMA#2017.1.00766.S\
ADS/JAO.ALMA#2017.1.00886.L\
ADS/JAO.ALMA#2018.1.00484.S\
ADS/JAO.ALMA#2018.1.01321.S\
ADS/JAO.ALMA#2018.1.01651.S\
ADS/JAO.ALMA#2018.A.00062.S\
ADS/JAO.ALMA#2019.1.01235.S\
ADS/JAO.ALMA#2019.2.00129.S\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory (NRAO) is a facility of NSF operated under cooperative agreement by Associated Universities, Inc (AUI).

This research is based on observations made with the NASA/ESA Hubble Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with program 15654.

This work has made use of the Transient Name Server, provided by the IAU supernova working group, last accessed on 2023 December 30, which included observations and metadata for over 140,000 astronomical transients.

This work acknowledges the Open Supernova Catalog (OSC; (cite: Guillochon2017)), last accessed on 2022, January 26th, which included observations and metadata for $\sim$80,000 SNe & SNRs.

This work has made use of SAO/NASA Astrophysics Data System

, the NASA/IPAC Extragalactic Database (NED), which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration, the SIMBAD database, operated at CDS, Strasbourg, France, and the Central Bureau for Astronomical Telegrams (CBAT) and the International Astronomical Union Circulars (IAUC) catalog , operated at Harvard College Observatory, Cambridge, Massachusetts.

This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github).

natexlab

(ref: Adams2015) Adams, S. M., & Kochanek, C. S. 2015, MNRAS, 452, 2195, doi: [`10.1093/mnras/stv1409`](http://doi.org/10.1093/mnras/stv1409)

(ref: Anderson2014) Anderson, J. P. 2014, in Supernova Environmental Impacts, ed. A. Ray & R. A. McCray, Vol. 296, 121–125, doi: [`10.1017/S1743921313009344`](http://doi.org/10.1017/S1743921313009344)

(ref: Anderson2012) Anderson, J. P., Habergham, S. M., James, P. A., & Hamuy, M. 2012, MNRAS, 424, 1372, doi: [`10.1111/j.1365-2966.2012.21324.x`](http://doi.org/10.1111/j.1365-2966.2012.21324.x)

(ref: Anderson2015a) Anderson, J. P., James, P. A., Förster, F., et al. 2015a, MNRAS, 448, 732, doi: [`10.1093/mnras/stu2712`](http://doi.org/10.1093/mnras/stu2712)

(ref: Anderson2015) Anderson, J. P., James, P. A., Habergham, S. M., Galbany, L., & Kuncarayakti, H. 2015b, PASA, 32, e019, doi: [`10.1017/pasa.2015.19`](http://doi.org/10.1017/pasa.2015.19)

(ref: Anderson2015b) —. 2015c, PASA, 32, e019, doi: [`10.1017/pasa.2015.19`](http://doi.org/10.1017/pasa.2015.19)

(ref: Andrews2021) Andrews, J. E., Jencson, J. E., Van Dyk, S. D., et al. 2021, ApJ, 917, 63, doi: [`10.3847/1538-4357/ac09e110.48550/arXiv.2009.13541`](http://doi.org/10.3847/1538-4357/ac09e110.48550/arXiv.2009.13541)

(ref: Arcavi2014) Arcavi, I., Valenti, S., Hosseinzadeh, G., et al. 2014, The Astronomer’s Telegram, 6466, 1

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Price-Whelan2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: AudcentRoss2020) Audcent-Ross, F. M., Meurer, G. R., Audcent, J. R., et al. 2020, MNRAS, 492, 848, doi: [`10.1093/mnras/stz3282`](http://doi.org/10.1093/mnras/stz3282)

(ref: Ayani1999) Ayani, K., & Yamaoka, H. 1999, , 7336, 1

(ref: Bacon2010) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, ed. I. S. McLean, S. K. Ramsay, & H. Takami, 773508, doi: [`10.1117/12.856027`](http://doi.org/10.1117/12.856027)

(ref: Bagetakos2011) Bagetakos, I., Brinks, E., Walter, F., et al. 2011, AJ, 141, 23, doi: [`10.1088/0004-6256/141/1/23`](http://doi.org/10.1088/0004-6256/141/1/23)

(ref: Baldwin1981) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5, doi: [`10.1086/130766`](http://doi.org/10.1086/130766)

(ref: Barnes2020) Barnes, A. T., Longmore, S. N., Dale, J. E., et al. 2020, MNRAS, 498, 4906, doi: [`10.1093/mnras/staa2719`](http://doi.org/10.1093/mnras/staa2719)

(ref: Barnes2022) Barnes, A. T., Chandar, R., Kreckel, K., et al. 2022, A&A, 662, L6, doi: [`10.1051/0004-6361/202243766`](http://doi.org/10.1051/0004-6361/202243766)

(ref: Barnes2023) Barnes, A. T., Watkins, E. J., Meidt, S. E., et al. 2023, ApJL, 944, L22, doi: [`10.3847/2041-8213/aca7b9`](http://doi.org/10.3847/2041-8213/aca7b9)

(ref: Belfiore2022) Belfiore, F., Santoro, F., Groves, B., et al. 2022, A&A, 659, A26, doi: [`10.1051/0004-6361/202141859`](http://doi.org/10.1051/0004-6361/202141859)

(ref: Belfiore2023) Belfiore, F., Leroy, A. K., Sun, J., et al. 2023, A&A, 670, A67, doi: [`10.1051/0004-6361/202244863`](http://doi.org/10.1051/0004-6361/202244863)

(ref: Bessell2010) Bessell, M. S., & Schmidt, B. P. 2010, Central Bureau Electronic Telegrams, 2337, 1

(ref: Blondin2006) Blondin, S., Modjaz, M., Kirshner, R., Challis, P., & Berlind, P. 2006, Central Bureau Electronic Telegrams, 757, 1

(ref: Bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Calzetti2001) Calzetti, D. 2001, PASP, 113, 1449, doi: [`10.1086/324269`](http://doi.org/10.1086/324269)

(ref: Carney1980) Carney, B. W. 1980, PASP, 92, 56, doi: [`10.1086/130614`](http://doi.org/10.1086/130614)

(ref: Chevance2020) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS, 493, 2872, doi: [`10.1093/mnras/stz3525`](http://doi.org/10.1093/mnras/stz3525)

(ref: Chevance2022) Chevance, M., Kruijssen, J. M. D., Krumholz, M. R., et al. 2022, MNRAS, 509, 272, doi: [`10.1093/mnras/stab2938`](http://doi.org/10.1093/mnras/stab2938)

(ref: Ciatti1977) Ciatti, F., & Rosino, L. 1977, A&A, 56, 59

(ref: Cronin2021) Cronin, S. A., Utomo, D., Leroy, A. K., et al. 2021, ApJ, 923, 86, doi: [`10.3847/1538-4357/ac28a2`](http://doi.org/10.3847/1538-4357/ac28a2)

(ref: Crowther2013) Crowther, P. A. 2013, MNRAS, 428, 1927, doi: [`10.1093/mnras/sts145`](http://doi.org/10.1093/mnras/sts145)

(ref: De2021) De, K., Fremling, U. C., Gal-Yam, A., et al. 2021, ApJL, 907, L18, doi: [`10.3847/2041-8213/abd627`](http://doi.org/10.3847/2041-8213/abd627)

(ref: Dessart2022) Dessart, L., & Hillier, D. J. 2022, A&A, 660, L9, doi: [`10.1051/0004-6361/202243372`](http://doi.org/10.1051/0004-6361/202243372)

(ref: Draine2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: Egorov2023) Egorov, O. V., Kreckel, K., Glover, S. C. O., et al. 2023, A&A, 678, A153, doi: [`10.1051/0004-6361/202346919`](http://doi.org/10.1051/0004-6361/202346919)

(ref: Eldridge2011) Eldridge, J. J. 2011, in Astronomical Society of the Pacific Conference Series, Vol. 440, UP2010: Have Observations Revealed a Variable Upper End of the Initial Mass Function?, ed. M. Treyer, T. Wyder, J. Neill, M. Seibert, & J. Lee, 217

(ref: Elmegreen2004) Elmegreen, B. 2004, in Astronomical Society of the Pacific Conference Series, Vol. 323, Star Formation in the Interstellar Medium: In Honor of David Hollenbach, ed. D. Johnstone, F. C. Adams, D. N. C. Lin, D. A. Neufeeld, & E. C. Ostriker, 117, doi: [`10.48550/arXiv.astro-ph/0405555`](http://doi.org/10.48550/arXiv.astro-ph/0405555)

(ref: Emsellem2022) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: Evans2003) Evans, R., & McNaught, R. H. 2003, , 8150, 2

(ref: Evans1995) Evans, R. O., Jarman, J., Cragg, T., et al. 1995, , 6197, 2

(ref: Fairall1967) Fairall, A. P. 1967, Monthly Notes of the Astronomical Society of South Africa, 26, 148

(ref: Fox2021) Fox, O. D., Khandrika, H., Rubin, D., et al. 2021, MNRAS, 506, 4199, doi: [`10.1093/mnras/stab1740`](http://doi.org/10.1093/mnras/stab1740)

(ref: Galbany2014) Galbany, L., Stanishev, V., Mourão, A. M., et al. 2014, A&A, 572, A38, doi: [`10.1051/0004-6361/201424717`](http://doi.org/10.1051/0004-6361/201424717)

(ref: Galbany2017) Galbany, L., Mora, L., González-Gaitán, S., et al. 2017, MNRAS, 468, 628, doi: [`10.1093/mnras/stx367`](http://doi.org/10.1093/mnras/stx367)

(ref: Gatto2017) Gatto, A., Walch, S., Naab, T., et al. 2017, MNRAS, 466, 1903, doi: [`10.1093/mnras/stw3209`](http://doi.org/10.1093/mnras/stw3209)

(ref: Girichidis2016) Girichidis, P., Walch, S., Naab, T., et al. 2016, MNRAS, 456, 3432, doi: [`10.1093/mnras/stv2742`](http://doi.org/10.1093/mnras/stv2742)

(ref: github) github. 2020, GitHub. <https://github.com/>

(ref: Groves2023) Groves, B., Kreckel, K., Santoro, F., et al. 2023, MNRAS, 520, 4902, doi: [`10.1093/mnras/stad114`](http://doi.org/10.1093/mnras/stad114)

(ref: Guillochon2017) Guillochon, J., Parrent, J., Kelley, L. Z., & Margutti, R. 2017, ApJ, 835, 64, doi: [`10.3847/1538-4357/835/1/64`](http://doi.org/10.3847/1538-4357/835/1/64)

(ref: Hannon2022) Hannon, S., Lee, J. C., Whitmore, B. C., et al. 2022, MNRAS, 512, 1294, doi: [`10.1093/mnras/stac550`](http://doi.org/10.1093/mnras/stac550)

(ref: Harris2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Humason1962) Humason, M. L., Kearns, C. E., & Gomes, A. M. 1962, PASP, 74, 215, doi: [`10.1086/127790`](http://doi.org/10.1086/127790)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: James2006) James, P. A., & Anderson, J. P. 2006, A&A, 453, 57, doi: [`10.1051/0004-6361:20054509`](http://doi.org/10.1051/0004-6361:20054509)

(ref: Jha2017) Jha, S. W., Camacho, Y., Dettman, K., et al. 2017, The Astronomer’s Telegram, 10640, 1

(ref: Kasliwal2009) Kasliwal, M. M., Sahu, D. K., & Anupama, G. C. 2009, Central Bureau Electronic Telegrams, 1874, 2

(ref: Kawamura2009) Kawamura, A., Mizuno, Y., Minamidani, T., et al. 2009, ApJS, 184, 1, doi: [`10.1088/0067-0049/184/1/1`](http://doi.org/10.1088/0067-0049/184/1/1)

(ref: Keller2020) Keller, B. W., & Kruijssen, J. M. D. 2020, arXiv e-prints, arXiv:2004.03608. [`https://arxiv.org/abs/2004.03608`](https://arxiv.org/abs/2004.03608)

(ref: Kennicutt2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Kim2015) Kim, C.-G., & Ostriker, E. C. 2015, ApJ, 802, 99, doi: [`10.1088/0004-637X/802/2/99`](http://doi.org/10.1088/0004-637X/802/2/99)

(ref: Kim2021) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2021, MNRAS, 504, 487, doi: [`10.1093/mnras/stab878`](http://doi.org/10.1093/mnras/stab878)

(ref: Kim2022) —. 2022, arXiv e-prints, arXiv:2206.09857. [`https://arxiv.org/abs/2206.09857`](https://arxiv.org/abs/2206.09857)

(ref: Kirshner1985) Kirshner, R., Schild, R., Wilson, I. R. G., Buta, R., & Meurer, G. 1985, , 4143, 1

(ref: Klotz2012) Klotz, A., Maury, A., Childress, M., et al. 2012, Central Bureau Electronic Telegrams, 3275, 1

(ref: Kluyver2016) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in IOS Press, 87–90, doi: [`10.3233/978-1-61499-649-1-87`](http://doi.org/10.3233/978-1-61499-649-1-87)

(ref: Kochanek2017) Kochanek, C. S., Shappee, B. J., Stanek, K. Z., et al. 2017, PASP, 129, 104502, doi: [`10.1088/1538-3873/aa80d9`](http://doi.org/10.1088/1538-3873/aa80d9)

(ref: Kruijssen2014) Kruijssen, J. M. D. 2014, Classical and Quantum Gravity, 31, 244006, doi: [`10.1088/0264-9381/31/24/244006`](http://doi.org/10.1088/0264-9381/31/24/244006)

(ref: Kruijssen2018) Kruijssen, J. M. D., Schruba, A., Hygate, A. P. S., et al. 2018, MNRAS, 479, 1866, doi: [`10.1093/mnras/sty1128`](http://doi.org/10.1093/mnras/sty1128)

(ref: Kruijssen2019) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019, Nature, 569, 519, doi: [`10.1038/s41586-019-1194-3`](http://doi.org/10.1038/s41586-019-1194-3)

(ref: Kuncarayakti2013) Kuncarayakti, H., Doi, M., Aldering, G., et al. 2013, AJ, 146, 30, doi: [`10.1088/0004-6256/146/2/30`](http://doi.org/10.1088/0004-6256/146/2/30)

(ref: Lee2022) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022, ApJS, 258, 10, doi: [`10.3847/1538-4365/ac1fe5`](http://doi.org/10.3847/1538-4365/ac1fe5)

(ref: Leitherer2014) Leitherer, C., Ekström, S., Meynet, G., et al. 2014, ApJS, 212, 14, doi: [`10.1088/0067-0049/212/1/14`](http://doi.org/10.1088/0067-0049/212/1/14)

(ref: Leitherer1999) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3, doi: [`10.1086/313233`](http://doi.org/10.1086/313233)

(ref: Leonard2013) Leonard, P. b. D. C., Pignata, G., Dessart, L., et al. 2013, The Astronomer’s Telegram, 5275, 1

(ref: Leroy2021) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, arXiv e-prints, arXiv:2104.07739. [`https://arxiv.org/abs/2104.07739`](https://arxiv.org/abs/2104.07739)

(ref: Leroy2023) Leroy, A. K., Sandstrom, K., Rosolowsky, E., et al. 2023, ApJL, 944, L9, doi: [`10.3847/2041-8213/acaf85`](http://doi.org/10.3847/2041-8213/acaf85)

(ref: Li2022) Li, L., Cai, Y., Zhai, Q., Zhang, J., & Wang, X. 2022, Transient Name Server Classification Report, 2022-3549, 1

(ref: Li2011a) Li, W., Leaman, J., Chornock, R., et al. 2011, MNRAS, 412, 1441, doi: [`10.1111/j.1365-2966.2011.18160.x`](http://doi.org/10.1111/j.1365-2966.2011.18160.x)

(ref: Lockman1989) Lockman, F. J. 1989, ApJS, 71, 469, doi: [`10.1086/191383`](http://doi.org/10.1086/191383)

(ref: Lopez2014) Lopez, L. A., Krumholz, M. R., Bolatto, A. D., et al. 2014, ApJ, 795, 121, doi: [`10.1088/0004-637X/795/2/121`](http://doi.org/10.1088/0004-637X/795/2/121)

(ref: Maoz2014) Maoz, D., Mannucci, F., & Nelemans, G. 2014, ARA&A, 52, 107, doi: [`10.1146/annurev-astro-082812-141031`](http://doi.org/10.1146/annurev-astro-082812-141031)

(ref: Martizzi2015) Martizzi, D., Faucher-Giguère, C.-A., & Quataert, E. 2015, MNRAS, 450, 504, doi: [`10.1093/mnras/stv562`](http://doi.org/10.1093/mnras/stv562)

(ref: Marvin1989) Marvin, H., Perlmutter, S., Seal, D., et al. 1989, , 4727, 1

(ref: MaykerChen2023a) Mayker Chen, N., Leroy, A. K., Lopez, L. A., et al. 2023, ApJ, 944, 110, doi: [`10.3847/1538-4357/acab00`](http://doi.org/10.3847/1538-4357/acab00)

(ref: McLeod2019) McLeod, A. F., Dale, J. E., Evans, C. J., et al. 2019, MNRAS, 486, 5263, doi: [`10.1093/mnras/sty2696`](http://doi.org/10.1093/mnras/sty2696)

(ref: McLeod2020) McLeod, A. F., Kruijssen, J. M. D., Weisz, D. R., et al. 2020, ApJ, 891, 25, doi: [`10.3847/1538-4357/ab6d63`](http://doi.org/10.3847/1538-4357/ab6d63)

(ref: McLeod2021) McLeod, A. F., Ali, A. A., Chevance, M., et al. 2021, MNRAS, 508, 5425, doi: [`10.1093/mnras/stab2726`](http://doi.org/10.1093/mnras/stab2726)

(ref: Monard2008) Monard, L. A. G. 2008, Central Bureau Electronic Telegrams, 1315, 1

(ref: Nguyen2022) Nguyen, C. T., Costa, G., Girardi, L., et al. 2022, A&A, 665, A126, doi: [`10.1051/0004-6361/202244166`](http://doi.org/10.1051/0004-6361/202244166)

(ref: Ochner2014) Ochner, P., Tomasella, L., Benetti, S., et al. 2014, Central Bureau Electronic Telegrams, 4011, 2

(ref: Odonnell1994) O’Donnell, J. E. 1994, ApJ, 422, 158, doi: [`10.1086/173713`](http://doi.org/10.1086/173713)

(ref: Olivier2021) Olivier, G. M., Lopez, L. A., Rosen, A. L., et al. 2021, ApJ, 908, 68, doi: [`10.3847/1538-4357/abd24a`](http://doi.org/10.3847/1538-4357/abd24a)

(ref: Ostriker2011) Ostriker, E. C., & Shetty, R. 2011, ApJ, 731, 41, doi: [`10.1088/0004-637X/731/1/41`](http://doi.org/10.1088/0004-637X/731/1/41)

(ref: Pan2022) Pan, H.-A., Schinnerer, E., Hughes, A., et al. 2022, arXiv e-prints, arXiv:2201.01403. [`https://arxiv.org/abs/2201.01403`](https://arxiv.org/abs/2201.01403)

(ref: Patton2022) Patton, R. A., Sukhbold, T., & Eldridge, J. J. 2022, MNRAS, 511, 903, doi: [`10.1093/mnras/stab3797`](http://doi.org/10.1093/mnras/stab3797)

(ref: Pejcha2015) Pejcha, O., & Prieto, J. L. 2015, ApJ, 799, 215, doi: [`10.1088/0004-637X/799/2/215`](http://doi.org/10.1088/0004-637X/799/2/215)

(ref: Pennypacker1986) Pennypacker, C., Burns, S., Crawford, F., et al. 1986, , 4219, 1

(ref: Perley2020) Perley, D., Barbarino, C., Sollerman, J., et al. 2020, Transient Name Server AstroNote, 100, 1

(ref: Pessa2021) Pessa, I., Schinnerer, E., Belfiore, F., et al. 2021, A&A, 650, A134, doi: [`10.1051/0004-6361/202140733`](http://doi.org/10.1051/0004-6361/202140733)

(ref: Pessi2023) Pessi, T., Prieto, J. L., Anderson, J. P., et al. 2023, A&A, 677, A28, doi: [`10.1051/0004-6361/202346512`](http://doi.org/10.1051/0004-6361/202346512)

(ref: Pignata2009) Pignata, G., Maza, J., Hamuy, M., et al. 2009, Central Bureau Electronic Telegrams, 1902, 1

(ref: Pilyugin:2016) Pilyugin, L. S., & Grebel, E. K. 2016, MNRAS, 457, 3678, doi: [`10.1093/mnras/stw238`](http://doi.org/10.1093/mnras/stw238)

(ref: Pokhrel2020) Pokhrel, N. R., Simpson, C. E., & Bagetakos, I. 2020, AJ, 160, 66, doi: [`10.3847/1538-3881/ab9bfa`](http://doi.org/10.3847/1538-3881/ab9bfa)

(ref: Porter1993) Porter, A. C. 1993, PASP, 105, 1250, doi: [`10.1086/133303`](http://doi.org/10.1086/133303)

(ref: Pritchet2024) Pritchet, C., Thanjavur, K., Bottrell, C., & Gao, Y. 2024, arXiv e-prints, arXiv:2401.13826, doi: [`10.48550/arXiv.2401.13826`](http://doi.org/10.48550/arXiv.2401.13826)

(ref: Querejeta2021) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: Quimby2006) Quimby, R., Brown, P., Gerardy, C., Odewahn, S. C., & Rostopchin, S. 2006, Central Bureau Electronic Telegrams, 393, 1

(ref: Rahner2017) Rahner, D., Pellegrini, E. W., Glover, S. C. O., & Klessen, R. S. 2017, MNRAS, 470, 4453, doi: [`10.1093/mnras/stx1532`](http://doi.org/10.1093/mnras/stx1532)

(ref: Rosino1972) Rosino, L. 1972, , 2472, 1

(ref: Sanders1996) Sanders, D. B., & Mirabel, I. F. 1996, ARA&A, 34, 749, doi: [`10.1146/annurev.astro.34.1.749`](http://doi.org/10.1146/annurev.astro.34.1.749)

(ref: Santoro2022) Santoro, F., Kreckel, K., Belfiore, F., et al. 2022, A&A, 658, A188, doi: [`10.1051/0004-6361/202141907`](http://doi.org/10.1051/0004-6361/202141907)

(ref: Sarbadhicary2023) Sarbadhicary, S. K., Wagner, J., Koch, E. W., et al. 2023, arXiv e-prints, arXiv:2310.17694, doi: [`10.48550/arXiv.2310.17694`](http://doi.org/10.48550/arXiv.2310.17694)

(ref: Schinnerer2019) Schinnerer, E., Hughes, A., Leroy, A., et al. 2019, ApJ, 887, 49, doi: [`10.3847/1538-4357/ab50c2`](http://doi.org/10.3847/1538-4357/ab50c2)

(ref: Schruba2010) Schruba, A., Leroy, A. K., Walter, F., Sandstrom, K., & Rosolowsky, E. 2010, ApJ, 722, 1699, doi: [`10.1088/0004-637X/722/2/1699`](http://doi.org/10.1088/0004-637X/722/2/1699)

(ref: Shappee2014) Shappee, B. J., Prieto, J. L., Grupe, D., et al. 2014, ApJ, 788, 48, doi: [`10.1088/0004-637X/788/1/48`](http://doi.org/10.1088/0004-637X/788/1/48)

(ref: Sheth2010) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397, doi: [`10.1086/657638`](http://doi.org/10.1086/657638)

(ref: Siebert2022) Siebert, M., & Foley, R. 2022, Transient Name Server Classification Report, 2022-170, 1

(ref: Siebert2020) Siebert, M. R., Kilpatrick, C. D., Foley, R. J., & Cartier, R. 2020, The Astronomer’s Telegram, 13393, 1

(ref: Smartt2009) Smartt, S. J. 2009, ARA&A, 47, 63, doi: [`10.1146/annurev-astro-082708-101737`](http://doi.org/10.1146/annurev-astro-082708-101737)

(ref: Smartt2001) Smartt, S. J., Kilkenny, D., & Meikle, P. 2001, , 7704, 1

(ref: Sukhbold2016) Sukhbold, T., Ertl, T., Woosley, S. E., Brown, J. M., & Janka, H. T. 2016, ApJ, 821, 38, doi: [`10.3847/0004-637X/821/1/38`](http://doi.org/10.3847/0004-637X/821/1/38)

(ref: Thilker2000) Thilker, D. A., Braun, R., & Walterbos, R. A. M. 2000, AJ, 120, 3070, doi: [`10.1086/316852`](http://doi.org/10.1086/316852)

(ref: Tsvetkov1993) Tsvetkov, D. Y., & Bartunov, O. S. 1993, Bulletin d’Information du Centre de Donnees Stellaires, 42, 17

(ref: Valenti2021) Valenti, S., Sand, D. J., Wyatt, S., et al. 2021, Transient Name Server Discovery Report, 2021-3864, 1

(ref: VanDerWalt2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: vanDyk1996) van Dyk, S. D., Hamuy, M., & Filippenko, A. V. 1996, AJ, 111, 2017, doi: [`10.1086/117937`](http://doi.org/10.1086/117937)

(ref: Vartanyan2021) Vartanyan, D., Laplace, E., Renzo, M., et al. 2021, ApJL, 916, L5, doi: [`10.3847/2041-8213/ac0b42`](http://doi.org/10.3847/2041-8213/ac0b42)

(ref: Veilleux2020) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2, doi: [`10.1007/s00159-019-0121-9`](http://doi.org/10.1007/s00159-019-0121-9)

(ref: Virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Walch2015) Walch, S., Girichidis, P., Naab, T., et al. 2015, MNRAS, 454, 238, doi: [`10.1093/mnras/stv1975`](http://doi.org/10.1093/mnras/stv1975)

(ref: Waskom2017) Waskom, M., Botvinnik, O., O’Kane, D., et al. 2017, mwaskom/seaborn: v0.8.1 (September 2017), v0.8.1, Zenodo, doi: [`10.5281/zenodo.883859`](http://doi.org/10.5281/zenodo.883859)

(ref: Watkins2023a) Watkins, E. J., Barnes, A. T., Henny, K., et al. 2023a, ApJL, 944, L24, doi: [`10.3847/2041-8213/aca6e4`](http://doi.org/10.3847/2041-8213/aca6e4)

(ref: Watkins2023b) Watkins, E. J., Kreckel, K., Groves, B., et al. 2023b, A&A, 676, A67, doi: [`10.1051/0004-6361/202346075`](http://doi.org/10.1051/0004-6361/202346075)

(ref: McKinney2010) Wes McKinney. 2010, in Proceedings of the 9th Python in Science Conference, ed. Stéfan van der Walt & Jarrod Millman, 56 – 61, doi: [`10.25080/Majora-92bf1922-00a`](http://doi.org/10.25080/Majora-92bf1922-00a)

(ref: Wheeler1987) Wheeler, J. C., Harkness, R. P., Barker, E. S., Cochran, A. L., & Wills, D. 1987, ApJL, 313, L69, doi: [`10.1086/184833`](http://doi.org/10.1086/184833)

(ref: Yamaoka2014) Yamaoka, H., Itagaki, K., Guido, E., et al. 2014, Central Bureau Electronic Telegrams, 3795, 2

(ref: Zapartas2017) Zapartas, E., de Mink, S. E., Izzard, R. G., et al. 2017, A&A, 601, A29, doi: [`10.1051/0004-6361/201629685`](http://doi.org/10.1051/0004-6361/201629685)

(ref: Zhang2016) Zhang, J., Zheng, X., Wang, X., & Rui, L. 2016, The Astronomer’s Telegram, 9093, 1

| Galaxy | Supernova | Type | R.A. | Dec | In Sample | Reference |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| NGC0628 | SN2013ej | II | 24.2007 | 15.7586 | \- | (cite: Leonard2013) |
| NGC0628 | SN2019krl | IIn/LBV | 24.2068 | 15.7795 | \- | (cite: Andrews2021) |
| NGC1087 | SN1995V | II | 41.6115 | \- 0.4988 |  | (cite: Evans1995) |
| NGC1300 | SN2022acko | II | 49.9125 | -19.3952 |  | (cite: Li2022) |
| NGC1365 | SN1957C | Unclassified | 53.3835 | -36.1177 |  | HAC 1383 |
| NGC1365 | SN1983V | Ib | 53.3819 | -36.1486 |  | (cite: Wheeler1987) |
| NGC1365 | SN2001du | II | 53.3713 | -36.1421 |  | (cite: Smartt2001) |
| NGC1365 | SN2012fr | Ia | 53.4006 | -36.1268 |  | (cite: Klotz2012) |
| NGC1433 | SN1985P | II | 55.5264 | -47.21 |  | (cite: Kirshner1985) |
| NGC1566 | ASASSN-14ha | II | 65.0059 | -54.9381 |  | (cite: Arcavi2014) |
| NGC1566 | SN2010el | Ia-02cx | 64.9951 | -54.944 |  | (cite: Bessell2010) |
| NGC1566 | SN2021aefx | Ia | 64.9725 | -54.9481 |  | (cite: Valenti2021) |
| NGC1672 | SN2017gax | Ib/c | 71.4561 | -59.2451 | \- | (cite: Jha2017) |
| NGC1672 | SN2022aau | II | 71.424 | -59.2454 |  | (cite: Siebert2022) |
| NGC3627 | SN1973R | II | 170.0481 | 12.9977 |  | (cite: Ciatti1977) |
| NGC3627 | SN1989B | Ia | 170.058 | 13.0053 |  | (cite: Marvin1989) |
| NGC3627 | SN1997bs | IIn | 170.0593 | 12.9721 |  | (cite: Adams2015) |
| NGC3627 | SN2009hd | II | 170.0707 | 12.9796 |  | (cite: Kasliwal2009) |
| NGC3627 | SN2016cok | II P | 170.0796 | 12.9824 |  | (cite: Zhang2016) |
| NGC4254 | SN1967H | II | 184.7184 | 14.414 |  | (cite: Fairall1967) |
| NGC4254 | SN1972Q | II | 184.7107 | 14.4443 |  | (cite: Rosino1972) |
| NGC4254 | SN1986I | II | 184.7169 | 14.4123 |  | (cite: Pennypacker1986) |
| NGC4254 | SN2014L | Ic | 184.7029 | 14.4121 |  | (cite: Yamaoka2014) |
| NGC4303 | SN1926A | II | 185.4754 | 4.4934 |  | IAUC 111 |
| NGC4303 | SN1961I | II | 185.5018 | 4.4704 |  | (cite: Humason1962) |
| NGC4303 | SN1964F | II | 185.4698 | 4.4738 |  | IAUC 1868 |
| NGC4303 | SN1999gn | II P | 185.4876 | 4.4627 |  | (cite: Ayani1999) |
| NGC4303 | SN2006ov | II | 185.4804 | 4.488 |  | (cite: Blondin2006) |
| NGC4303 | SN2014dt | Ia Pec | 185.4899 | 4.4718 |  | (cite: Ochner2014) |
| NGC4303 | SN2020jfo | II P | 185.4602 | 4.4817 |  | (cite: Perley2020) |
| NGC4321 | SN1901B | I | 185.6971 | 15.8238 |  | (cite: Tsvetkov1993) |
| NGC4321 | SN1959E | I | 185.7454 | 15.817 |  | (cite: Porter1993) |
| NGC4321 | SN1979C | II | 185.7442 | 15.7978 | \- | (cite: Carney1980) |
| NGC4321 | SN2006X | Ia | 185.7249 | 15.809 |  | (cite: Quimby2006) |
| NGC4321 | SN2019ehk | Ib | 185.7339 | 15.8261 |  | (cite: De2021) |
| NGC4321 | SN2020oi | Ic | 185.7289 | 15.8236 |  | (cite: Siebert2020) |

: Supernovae in MUSE Galaxies

| Supernova | Type | Resolution | Distance | H$_{\alpha}$ | $\sigma$ | $A_V$ | H II | NII | SII | OI | CO | Metallicity | $R_{\rm gal}$ | $R_{\rm eff}$ |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:---|:--:|:--:|
| ASASSN-14ha | II | 0.8 (80) | 17.69 | 621 | 57 | 0.86 | Yes (877) | 0.0 | 0.0 | 0.0 | Yes | 8.56 (8.61) | 0.05 | 1.31 |
| SN1901B | I | 1.16 (43) | 15.21 | 211 | 53 | 0.92 | No (-1) | \- | \- | \- | Yes | 8.38 | 0.57 | 7.67 |
| SN1926A | II | 0.78 (73) | 16.99 | 82 | 67 | 0.0 | No (-1) | \- | \- | \- | No | 8.34 | 0.35 | 8.42 |
| SN1957C | Unclassified | 1.15 (76) | 19.57 | 294 | 63 | 0.38 | No (-1) | \- | \- | \- | No | 8.52 | 0.81 | 43.17 |
| SN1959E | I | 1.16 (43) | 15.21 | 361 | 55 | 1.07 | No (-1) | \- | \- | \- | Yes | 8.48 | 0.3 | 3.98 |
| SN1961I | II | 0.78 (73) | 16.99 | 415 | 58 | 0.35 | Yes (373) | 0.0 | 0.0 | 0.0 | No | 8.3 (8.56) | 0.4 | 9.73 |
| SN1964F | II | 0.78 (73) | 16.99 | 29 | 59 | 0.0 | No (-1) | \- | \- | \- | No | 8.49 | 0.16 | 3.85 |
| SN1967H | II | 0.89 (96) | 13.1 | 1435 | 63 | 1.65 | No (-1) | \- | \- | \- | Yes | 8.47 | 0.16 | 4.24 |
| SN1972Q | II | 0.89 (96) | 13.1 | 362 | 56 | 0.78 | No (-1) | \- | \- | \- | Yes | 8.27 | 0.43 | 11.34 |
| SN1973R | II | 1.05 (96) | 11.32 | 1118 | 59 | 1.17 | Yes (433) | 0.0 | 0.0 | 0.0 | Yes | 8.56 (8.52) | 0.29 | 4.39 |
| SN1983V | Ic | 1.15 (76) | 19.57 | 1485 | 66 | 0.95 | Yes (385) | 0.0 | 0.0 | 0.0 | Yes | 8.58 (8.57) | 0.48 | 25.77 |
| SN1985P | II | 0.91 (69) | 18.63 | 25 | 67 | 0.24 | No (-1) | \- | \- | \- | No | 8.47 | 0.35 | 7.37 |
| SN1986I | II | 0.89 (96) | 13.1 | 515 | 62 | 0.52 | No (-1) | \- | \- | \- | Yes | 8.48 | 0.15 | 4.08 |
| SN1989B | Ia | 1.05 (96) | 11.32 | 1257 | 66 | 0.81 | Yes (390) | 0.0 | 0.0 | 0.0 | Yes | 8.55 (8.54) | 0.17 | 2.58 |
| SN1995V | II | 0.92 (84) | 15.85 | 884 | 52 | 1.28 | Yes (731) | 0.0 | 0.0 | 0.0 | Yes | 8.24 (8.45) | 0.14 | 3.4 |
| SN1997bs | IIn | 1.05 (96) | 11.32 | 99 | 55 | 0.78 | Yes (961) | 1.0 | 0.0 | 0.0 | Yes | 8.56 (nan) | 0.24 | 3.66 |
| SN1999gn | II P | 0.78 (73) | 16.99 | 1285 | 61 | 0.41 | Yes (58) | 0.0 | 0.0 | 0.0 | Yes | 8.43 (8.64) | 0.24 | 5.76 |
| SN2001du | II | 1.15 (76) | 19.57 | 135 | 68 | 0.18 | No (-1) | \- | \- | \- | No | 8.53 | 0.79 | 41.99 |
| SN2006X | Ia | 1.16 (43) | 15.21 | 37 | 60 | 0.54 | No (-1) | \- | \- | \- | No | 8.5 | 0.24 | 3.17 |
| SN2006ov | II | 0.78 (73) | 16.99 | 331 | 68 | 0.33 | No (-1) | \- | \- | \- | No | 8.41 | 0.26 | 6.19 |
| SN2009hd | II | 1.05 (96) | 11.32 | 3081 | 68 | 1.03 | Yes (396) | 0.0 | 0.0 | 0.0 | Yes | 8.56 (8.53) | 0.2 | 3.0 |
| SN2010el | Ia | 0.8 (80) | 17.69 | 38 | 68 | 0.26 | No (-1) | \- | \- | \- | Yes | 8.49 | 0.13 | 3.39 |
| SN2012fr | Ia | 1.15 (76) | 19.57 | 9 | 68 | 0.0 | No (-1) | \- | \- | \- | No | 8.61 | 0.31 | 16.54 |
| SN2014L | Ic | 0.89 (96) | 13.1 | 3366 | 63 | 1.47 | Yes (1309) | 0.0 | 0.0 | 0.0 | Yes | 8.53 (8.55) | 0.08 | 2.08 |
| SN2014dt | Ia Pec | 0.78 (73) | 16.99 | 90 | 71 | 0.28 | No (-1) | \- | \- | \- | No | 8.46 | 0.19 | 4.69 |
| SN2016cok | II P | 1.05 (96) | 11.32 | 518 | 62 | 1.36 | No (-1) | \- | \- | \- | Yes | 8.57 | 0.35 | 5.22 |
| SN2019ehk | Ib | 1.16 (43) | 15.21 | 104 | 76 | 1.47 | Yes (1722) | 1.0 | 0.0 | 0.0 | No | 8.55 (nan) | 0.12 | 1.59 |
| SN2020jfo | II P | 0.78 (73) | 16.99 | 220 | 57 | 0.92 | No (-1) | \- | \- | \- | No | 8.35 | 0.35 | 8.37 |
| SN2020oi | Ic | 1.16 (43) | 15.21 | 5473 | 66 | 1.01 | Yes (1693) | 0.0 | 0.0 | 0.0 | Yes | 8.58 (8.58) | 0.02 | 0.28 |
| SN2021aefx | Ia | 0.8 (80) | 17.69 | 13 | 73 | 0.0 | No (-1) | \- | \- | \- | No | 8.26 | 0.35 | 9.59 |
| SN2022aau | II | 0.96 (104) | 19.4 | 9695 | 76 | 2.35 | Yes (803) | 0.0 | 0.0 | 0.0 | Yes | 8.55 (8.61) | 0.05 | 1.32 |
| SN2022acko | II | 0.89 (83) | 18.99 | 34 | 66 | 0.3 | No (-1) | \- | \- | \- | No | 8.19 | 0.38 | 5.35 |

: Measurements from the Supernovae Sample

Table notes: Resolution in arcseconds (pc), distance in Mpc, extinction-corrected H$_{\alpha}$ intensity in flux units of $10^{37} {\rm erg/s/kpc}^{2}$, $\sigma$ ($H_\alpha$ velocity dispersion, corrected for instrumental broadening) in units of km/s, $A_V$ derived using the Balmer decrement (cite: Groves2023), adopting $R_{\rm V} = 3.1$ and an (cite: Odonnell1994) extinction curve, H II regions identified in (cite: Groves2023), N II, S II, O I BPT emission line diagnostics taken from (cite: Groves2023), CO (2-1) detection assigned when signal-to-noise $\geq$ 3 from PHANGS–ALMA broad moment-0 maps (cite: Leroy2021), metallicity in \[12+log(O/H) (dex)\] calculated using the galactic metallicity gradient, determined using Scal metallicities, and the galactocentric radius of each SN (empirical values from (cite: Groves2023) when available), $R_{\rm gal}$ in kpc.

![](Zooms1.pdf)

.

![](Zooms2.pdf)

![](Zooms3.pdf)

![](MUSE_HST_Zooms_500pc_1.png)

![](MUSE_HST_Zooms_500pc_2.png)

![](MUSE_HST_Zooms_500pc_3.png)

![](MUSE_HST_Zooms_500pc_4.png)

![](MUSE_HST_Zooms_500pc_5.png)

![](MUSE_HST_Zooms_500pc_6.png)

[^1]: Accessed on 26 January, 2022, but no longer accessible online.

[^2]: https://www.wis-tns.org/ (accessed December 30, 2023)

[^3]: The borders of H II regions correspond to HIIphot masks.

[^4]: We are only considering CO (2-1) detections in this work and not accounting for $\alpha_{CO}$ variations. See (cite: MaykerChen2023a) for a more detailed discussion of CO (2-1) and SNe.

[^5]: In the (cite: Belfiore2022; Belfiore2023) maps, regions without detected H$\beta$ are set to $A_V = 0$ mag. The diffuse gas has lower overall intensity than H II regions so some of these very low $A_V$ may be biased low due to the faintness of the lines.

</paper>

Write the methods card for this paper.