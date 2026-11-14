# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...970L..40S\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...970L..40S",
 "title": "Direct Observational Evidence of Multi-epoch Massive Star Formation in G24.47+0.49",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Saha, Anindya",
 "n_authors": 22,
 "arxiv_id": "2407.01063",
 "doi": "10.3847/2041-8213/ad6144",
 "alma_projects_linked_by_archive": [
  "2019.1.00685.S"
 ]
}
```

Paper text:
<paper>
# Abstract

Using new continuum and molecular line data from the ALMA Three-millimeter Observations of Massive Star-forming Regions (ATOMS) survey and archival VLA, 4.86 GHz data, we present direct observational evidence of hierarchical triggering relating three epochs of massive star formation in a ring-like H II region, G24.47+0.49. We find from radio flux analysis that it is excited by a massive star(s) of spectral type O8.5V–O8V from the first epoch of star formation. The swept-up ionized ring structure shows evidence of secondary collapse, and within this ring a burst of massive star formation is observed in different evolutionary phases, which constitutes the second epoch. ATOMS spectral line (e.g., HCO$^+$(1–0)) observations reveal an outer concentric molecular gas ring expanding at a velocity of $\sim$ 9$\,\rm km\,s^{-1}$, constituting the direct and unambiguous detection of an expanding molecular ring. It harbors twelve dense molecular cores with surface mass density greater than 0.05$\,\rm g\,cm^{-2}$, a threshold typical of massive star formation. Half of them are found to be subvirial, and thus in gravitational collapse, making them third epoch of potential massive star-forming sites.

# Introduction

Massive stars ($M_{\star} \gtrsim 8\,\rm M_{\odot}$), with their powerful mechanical and radiative feedback, play a crucial role in regulating star formation within their natal environments. They can either initiate the formation of a subsequent

generation of stars (cite: Churchwell2006) or disperse the surrounding molecular gas, consequently inhibiting further star formation (cite: Walch2012; Pabst2019; Bonne2023). H II regions and their role in triggered star formation has been in focus, since the pioneering work by (cite: ElmegreenLada1977). Over the last decade or so, there has been a plethora of observational evidences linking the expansion of H II regions to triggered star formation (cite: Zavagno2006; Zavagno2007; Figueira2017). The peripheries of infrared dust bubbles (cite: Churchwell2006; Kendrew2012) have served as ideal sites to investigate triggered star formation through various competing mechanisms (cite: Deharveng2010; Thompson2012; Kendrew2012; Hongliliu2016; Swagat2017; Bhadari2021; Zhang2023ATOMSXIII). However, theoretically (cite: Dale2015; Semadeni2020) and observationally (cite: Cambresy2013), it is also seen that commonly used signposts of triggered star formation do not always lead to definite conclusions on positive feedback. Hence, these need to be cautiously interpreted to better constrain the impact of stellar feedback on triggering star formation.

![](f1-spitzer_vla_3mm_ha_horizontal_w1core_4PANELS_H13CO_v2revisit_v3_R1.pdf)

These observational studies have offered a comprehensive insight into triggered star formation, connecting two generations of stars. In comparison, observational evidence for hierarchical triggering and multi-generation star formation is still scarce (cite: Oey2005; Purcell2009; Areal2020). (cite: Oey2005) suggest a three-generation system of hierarchically triggered star formation in the W3/W4 complex, where expanding superbubbles and mechanical feedback from massive stars initiate later generations of star formation. Similarly, (cite: Purcell2009) report multi-generations of massive star formation in the NGC 3576, which is embedded in the center of an extended filamentary cloud. Here the expansion of the H II region into the ambient molecular cloud leads to the formation of high-mass stars along the dusty filament. In a recent work, based on the spatial and temporal correspondences derived in their analysis, (cite: Areal2020) propose three generations of star formation associated with a massive star LS II +26 8.

In this paper, we investigate the H II region, G24.47+0.49 (hereafter G24.47), likely ionized by an early O-type star (cite: Garay1993), to probe possible signatures of hierarchical triggering and multi-epoch star formation. Observed as part of several radio surveys (cite: Wink1982; Lockman1989; Churchwell1990; Garay1993; Becker1994; Walsh1998), G24.47 is associated with IRAS 18314–0720 and is located at a distance of 5.82 kpc (cite: Urquhart2018). This source is also associated with the massive (6095$\,\rm M_{\odot}$) ATLASGAL clump, AGAL024.471+00.487 (cite: Urquhart2018). The 4.5, 5.8, and 8.0 $\mu$m colour-composite *Spitzer*-IRAC[^1] image illustrated in Figure [1](#fig:RGB_vla_ha)(a) presents an interesting morphology, where G24.27 reveals as a bright ring located at the center of a complex region displaying bubble-like structures, pillars, and arcs.

The paper is organized as follows. Section [2](#sec:obs_data) discusses the ALMA observations carried out as part of the ALMA Three-millimeter Observations of Massive Star-forming Regions (ATOMS) survey and the other multi-wavelength archival data used in this study. Results obtained from the dust continuum, ionized emission, and molecular line analysis are presented in Section [\[sec:3mm-vla-mol\]](#sec:3mm-vla-mol). Discussion on the three observed epochs of star formation is presented in Section [\[sec:discussion\]](#sec:discussion), and the overall picture of hierarchical triggering and multi-epoch star formation in G24.47 is discussed in [\[sec:Hierarchical-trigger-multi-epoch\]](#sec:Hierarchical-trigger-multi-epoch). Section [\[sec:conclusion\]](#sec:conclusion) summarizes the results.

# Observations and archival data

For this study, we have utilized data from the ATOMS survey and other archival datasets. Brief descriptions of these are given in the following subsections.

## ALMA observations

G24.47 was observed as part of the ATOMS survey (Project ID: 2019.1.00685.S; PI: Tie Liu), which aims to study 146 massive star-forming clumps. Details of the survey can be found in (cite: Liu2020ATOMSI). The 12-m + 7-m combined data for continuum and line emission are used here. The maps have a field of view of  80$\ensuremath{''}$ or 2.26 pc at the distance of G24.47, and a maximum recoverable scale of 76$\ensuremath{''}$.2 or 2.15 pc. To probe the kinematics and dynamics of the associated ionized and dense gas, we use the H40$\alpha$ hydrogen radio recombination line (RRL) along with H$^{13}$CO$^+$ (1-0) and HCO$^+$ (1-0) molecular line transitions. The synthesized beam size for the continuum and H40$\alpha$ is 2$\ensuremath{''}$.1 $\times$ 1$\ensuremath{''}$.8. For molecular line observations, they are 2$\ensuremath{''}$.4 $\times$ 2$\ensuremath{''}$.1 and 2$\ensuremath{''}$.3 $\times$ 2$\ensuremath{''}$.0 for H$^{13}$CO$^+$ and HCO$^+$, respectively. The *rms* noise is $\sim$0.65 mJy $\rm beam^{-1}$ for the continuum, and $\sim$\[3.5, 8.5, 12\] mJy $\rm beam^{-1}$ for the \[H40$\alpha$, H$^{13}$CO$^+$, HCO$^+$\] lines at the native velocity resolution of \[1.5, 0.2, 0.1\] $\rm km\,s^{-1}$.

## Archival data

To probe the radio continuum emission associated with this region, we use VLA archival data at 4.86 GHz. The observations were conducted on 3 March 1988 using the VLA C configuration[^2] (Legacy ID: AB414; R. Becker). The image is retrieved from National Radio Astronomy Observatory VLA Archive Survey[^3] (NVAS) which has a beam size of 5$\ensuremath{''}$.9 × 3$\ensuremath{''}$.9 and a *rms* noise of 0.4 $\rm mJy\,beam^{-1}$. To identify the ionizing source associated with the H II region, G24.47, we use the near-infrared (NIR) *JHK* photometric data for point sources from the Two Micron All Sky Survey (cite: Skrutskie2006) and UKIRT Infrared Deep Sky Survey (cite: Lawrence2007), which were taken during the UKIDSS Galactic Plane Survey (cite: Lucas2008). The angular resolution of 2MASS and UKIDSS data are $\sim$2$''$ and 0.9$''$, respectively.

[^1]: Images taken from the archives of the Galactic Legacy Infrared Midplane Survey Extraordinaire (cite: Benjamin2003).

[^2]: <https://science.nrao.edu/facilities/vla/docs/manuals/propvla/array_configs>

[^3]: The NVAS can be browsed through <http://www.vla.nrao.edu/astro/nvas/>

# Results

## 4.86 GHz and 3 mm continuum emission

VLA 4.86 GHz and ATOMS 3 mm continuum maps are shown in Figure [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha). The VLA map displays a distinct ring morphology (radius $\sim$0.8 pc) of bright, ionized gas emission with prominent peaks, a low-emission inner region displaying an almost empty cavity like structure at the center, and extended faint emission beyond the ring. Such ring-like morphology of H II regions could be associated with flat, sheet-like parental cloud structures (cite: Beaumont2010; Kabanovic2022). The inner rim of the ring is observed to be dominated by 8.0 $\mu$m emission (see Figure [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(a)). This could be attributed to thermal dust emission from the forming hot massive stars in the ring or emission from polycyclic aromatic hydrocarbons (cite: Watson2008), which are indicative of photodissociation regions. The ATOMS 3 mm continuum and H40$\alpha$ line emission are also seen to closely trace the bright ring structure (see Figure [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(b) and (c)).

Both the 4.86 GHz and 3 mm maps reveal the presence of compact cores in the bright ring. To understand the nature of these cores, we implement the approach followed by (cite: Saha2022) and use a combination of the `DENDROGRAM` algorithm and the `CASA` imfit task to extract the cores. In total, six radio (R1 - R6) and ten 3 mm (MM1 - MM10) cores are identified. The retrieved core apertures and the corresponding peak positions are shown in Figures [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(b) and (c). The details of the procedure followed and parameters used are elaborated in Appendix [\[apndx:core_extract\]](#apndx:core_extract).

To characterize the radio cores, we calculate the physical parameters such as the emission measure ($EM$), number of Lyman continuum photons emitted per second ($N_{\rm Ly}$), and electron density ($n_{\rm e}$) using Equations 6-8 from (cite: Schmiedeke2016). For this, we assume the 4.86 GHz emission to be optically thin, and adopt the value of the electron temperature to be 6370 K from (cite: Quireza2006). The estimated parameters are tabulated in Table [\[tab:param-VLAcores\]](#tab:param-VLAcores).

Of the ten 3 mm cores identified in our study, only the brighter ones (MM1, MM5, and MM6) were detected by (cite: Liu2021ATOMSIII) using higher resolution 12-m array ATOMS data. Similar issue is also discussed in (cite: Sanhueza2019), where the inclusion of more extended emission from a more compact configuration results in 20% increase in the number of cores detected. None of these cores show any emission in the molecular line transitions of H$^{13}$CO$^+$ and HCO$^+$. This can be inferred from Figures [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(c) -(d), where the 3 mm ring is seen to be mostly devoid of H$^{13}$CO$^+$ emission and also similar distribution is seen for HCO$^+$ emission (see Figure [1](#fig:moment-maps) (a)). This suggests that the 3 mm continuum emission is predominantly free-free emission (cite: Keto2008; Zhang2023ATOMSXIV) with appreciably less contribution from cold dust emission. We verify this by following the method described in (cite: Liu2023) and find six of the 3 mm cores to have more than 50% contribution from free-free emission. However, the existence of hot dust associated with these cores is evident from the presence of MIR emission shown in Figure [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(a). Table [\[tab:parameter3mm\]](#tab:parameter3mm) lists the estimated core parameters.

## Molecular line emission

Figure [1](#fig:moment-maps)(a) shows the distribution of HCO$^+$ molecular line emission. The molecular line emission encircles the H40$\alpha$ and 3 mm ring. Henceforth, we refer to this as the molecular gas ring, the morphology of which is similar to the ionized gas ring as traced by radio 4.86 GHz emission. The molecular ring also shows the presence of bright, compact cores. Considering the H$^{13}$CO$^+$ (1-0) line to be optically thin (cite: sanhueza2012; Saha2022), we utilize the velocity integrated intensity (i.e., moment zero) map of this transition to extract the dense molecular cores. The same procedure as used for extraction of the radio and 3 mm cores is implemented (see Appendix [\[apndx:core_extract\]](#apndx:core_extract) for details) and ten molecular cores are identified. A careful visual inspection shows the presence of two additional cores that were not detected from this map. For these, we retrieve the parameters using the same approach on the column density map (see Appendix [\[apndx:column_density\]](#apndx:column_density)). The cores are labelled, M1 - M12 of which M1 and M10 are extracted from the column density map. The retrieved apertures are drawn in Figures [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(d) and [\[fig:cdmap_molcore\]](#fig:cdmap_molcore). Core masses are calculated from the generated hydrogen column density map using, $$\begin{equation}
    M = \mu_{\rm H_2} m_{\rm H} A \sum N({\rm H_{2}}), 
\end{equation}$$ where $\mu_{\rm H_2}$, $m_{\rm H}$ are the mean molecular weight and mass of the hydrogen atom, respectively, $A$ is the pixel area, and $\sum N(\rm H_{2})$ is the sum of the column density values for the pixels in the core area.

Next, to examine the gravitational stability of the cores, we estimate the virial parameter ($\alpha_{\rm vir}$), which represents the ratio of the virial mass ($M_{\rm vir}$) to the mass of the individual cores ($M_{\rm core}^{\rm mol}$). $M_{\rm vir}$ is given by (cite: Contreras2016) $$\begin{align}
    M_{\rm vir} &= \frac{5\ R_{\rm eff}^{\rm mol}\ \Delta V^2}{8\ {\rm ln}(2)\ a_1\ a_2\ G} \nonumber\\
    &\sim 209\ \frac{1}{a_1\ a_2} \left(\frac{\Delta V}{\rm km\ s^{-1}} \right)^2\ \left(\frac{r}{\rm pc}\right) \rm M_{\odot},
\label{eqn:M_vir}
\end{align}$$ where $R_{\rm eff}^{\rm mol}$ is the effective radius of the core and $\Delta V$ is the line width of the fitted Gaussian profiles to the observed H$^{13}$CO$^+$ spectra. In the presence of two velocity components, we calculated the average of the line widths obtained from fitting each component individually, following the approach used in (cite: Saha2022). The constant $a_1$ accounts for the correction for power-law density distribution. It is given as $a_1 = (1-p/3)/(1-2p/5)$ for $p < 2.5$ (cite: Bertoldi1992), where we adopt $p=1.8$ (cite: Contreras2016). The constant $a_2 = (arcsin\,e)/e$ takes into account the shape of the core, $e$ being the eccentricity. The estimated parameters of the molecular cores are listed in Table [\[tab:molcore-param\]](#tab:molcore-param).

## Velocity structure of G24.47

![](f2-all_composite_moment0_1_2compo_full_with_Ha_NOLINESv4.pdf)

![](f3-pv-EW-NS-hco-mom0_v4.pdf)

To inspect and compare the spatial distribution of molecular and ionized gas emission, we created separate moment zero maps of HCO$^{+}$ and H40$\alpha$ over three velocity extents, (i) full velocity range (ii) blue-shifted velocity range ($<102\,\rm km\,s^{-1}$ to 80 or 93$\,\rm km\,s^{-1}$) and (iii) red-shifted velocity range ($>102\,\rm km\,s^{-1}$ up to 113 or 130$\,\rm km\,s^{-1}$). The moment zero maps are shown in Figures [1](#fig:moment-maps)(a) - (c) and (e) - (g). The above velocity ranges are estimated from the average spectra plotted of these line transitions presented in Figure [2](#fig:pv-diag)(a). The H$^{13}$CO$^+$ and HCO$^+$ line profiles show prominent peaks around 101.0 and 104.5$\,\rm km\,s^{-1}$. On the other hand, the RRL shows a broader profile with a distinct peak at approximately 110.0$\,\rm km\,s^{-1}$. The systemic velocity of G24.47 is 101.5$\,\rm km\,s^{-1}$ (cite: Schlingman2011; Urquhart2018).

As seen from the HCO$^+$ moment zero maps, in the velocity range \[93, 102\]$\,\rm km\,s^{-1}$, the northern part of the molecular gas ring is visible, whereas in the 102 to 113$\,\rm km\,s^{-1}$ range, the emission traces the southern part of the ring. Channel maps (in 1$\,\rm km\,s^{-1}$ bins) are also presented in Appendix A, illustrating the above morphology. Similar morphology is also evident from the H$^{13}$CO$^+$ transition, where the diffuse emission is less pronounced. Figure [1](#fig:moment-maps)(d) presents the intensity-weighted mean velocity (i.e., moment one) map that conforms with the above velocity structure. The northern portion of the molecular ring is blue-shifted and the southern part red-shifted, suggesting expansion of the molecular gas ring. In comparison, the complete ring morphology can be discerned over the entire velocity range for the H40$\alpha$ emission, though the moment one map (Figure [1](#fig:moment-maps)(h)) reveals a distinct velocity gradient, similar to that seen in HCO$^{+}$.

To examine the velocity field in more detail, we construct position-velocity (PV) diagram of HCO$^{+}$ towards G24.47 along the east-west direction (offset increases from east to west direction). The PV diagram is shown in Figure [2](#fig:pv-diag)(b). The integrated intensity map is also included (Figure [2](#fig:pv-diag)(c)) for easy correlation with the location of the velocity components. Consistent with the moment one map, the PV diagram also displays signatures of expansion. Velocity differences are evident along the PV cut. Additionally, it displays an almost circular velocity pattern, that is in very good agreement with the results of simulations of expanding shells discussed in the literature (cite: Arce2011; Wang2016). The PV diagram along the north-south direction (not presented here), also shows evidence of expansion but not as prominent. Following the approach outlined in (cite: Arce2011), we obtain a rough estimate of the expansion velocity to be $\rm \sim9\,km\,s^{-1}$ by considering the maximum red- and blue-shifted velocities observed. This is consistent with the velocity shifts seen in the moment one map (see Figure [1](#fig:moment-maps)(d)). Given the lower velocity resolution and signal-to-noise ratio of the H40$\alpha$ emission, it was not possible to evaluate the expansion, if any, of the ionized ring.

# Discussion

In this section, we probe hierarchical triggering and multi-epoch massive star formation scenario in G24.47.

## H II region G24.47

In unveiling the multi-epoch star formation in G24.47, the first one is the massive star(s) responsible for the creation of the H II region. Based on their 1.5 GHz radio flux density, (cite: Garay1993) proposed a massive ionizing star of spectral type O5.5. We note here that these authors have used the far distance in their analysis. We re-visit this estimation using the 4.86 GHz VLA map. Integrating within the $3\sigma$ contour, and subtracting the contribution from the six detected compact radio cores, the flux density is calculated to be $\sim$0.9 Jy which translates to a Lyman-continuum photon flux, $N_{\rm Ly}$, of $\sim$3.4$\times\,10^{48}\,\rm s^{-1}$. Assuming a single star to be responsible for the ionization of G24.47, and comparing the calculated $N_{\rm Ly}$ with that of early type main-sequence stars tabulated in (cite: Panagia1973), we infer the spectral type to be O8.5V - O8V. However, this can only be considered as a lower limit, since dust absorption of Lyman continuum photons is not accounted for here, which can be significant as shown by many studies (cite: Paron2011). The central cavity of G24.47, which is observed to be mostly dust-free and devoid of molecular line emission, is likely to be carved out by the powerful radiation and wind of the massive star(s). We attempt to identify the ionizing star(s) by studying the stellar population located within the observed ionized gas emission. This is carried out using NIR colour-magnitude and colour-colour plots (cite: Potdar2022). For our study, we have used 2MASS and UKIDSS datasets. The detailed procedure is discussed in Appendix [\[apndx:Ionizing_star\]](#apndx:Ionizing_star). Following this, 12 candidate massive (with spectral type earlier than B3), Class III stars, namely, E1 - E12, are identified within the VLA radio emission. The location of these are shown in Figure [\[fig:cc-cm\]](#fig:cc-cm)(c). The positions and $JHK$ magnitudes of these sources are listed in Table [\[tab:ionisingstar-param\]](#tab:ionisingstar-param).

By a simple argument, the symmetry of the ionized ring morphology suggests a centrally located ionizing star or a group of ionizing stars. The sources, E10, E11, and E12 are located at the center of the cavity. However, their spectral types from the colour-magnitude plot lie between $\sim$ B3$-$B0.5. So the individual or the sum of their Lyman-continuum photon flux is not consistent with that calculated from the observed 4.86 GHz flux density. The other identified early type stars are mostly located on the bright, ionized ring. These could be bonafide ionizing sources, since it is possible that the ionizing star is displaced from the center due to its proper motion. Such a geometry is observed in the Orion Veil bubble, where the exciting massive star, $\rm \theta^1\,Ori\,C$ is seen offset from the center (cite: Pabst2019). Furthermore, simulations of expanding H II regions, discussed in (cite: Maclow2007) and (cite: Hunter2008), also show the possibility of formation of nearly spherical shells with off-center ionizing source. Under this scenario, sources E2, E3, E4, and E8 are potential candidates. The NIR spectral type inferred from the colour-magnitude diagram is reasonably consistent with the estimated radio spectral type. The above analysis, however, restricts any conclusive identification of the ionizing star of G24.47.

## The inner ring: radio and 3 mm continuum emission

Six radio cores are identified in this inner ring of ionized gas. Summarizing the results, we find the radius ($R_{\rm core}^{\rm VLA}$), $EM$, $n_{\rm e}$, and $M_{\rm ion}$ in the range of $\sim$ \[0.1, 0.2\] pc, \[1.6, 2.5\]$\times 10^6\,\rm cm^{-6}\,pc$, \[2.3, 3.0\]$\times 10^3\,\rm cm^{-3}$, and \[0.5, 1.2\]$\,\rm M_\odot$, respectively. In the same order, the median values are estimated to be 0.28 pc, $2.2\times 10^6\,\rm cm^{-6}\,pc$, 2.8$\times 10^3\,\rm cm^{-3}$, and 0.8$\,\rm M_\odot$. The derived radio properties of these compact VLA cores are consistent with those of UCH II/compact H II regions (cite: Kurtz2005; Martin2005; delaFuente2020; Yang2021). It is to be noted that the presence of extended, diffuse emission could possibly result in large extracted core sizes, leading to underestimation of $n_{\rm e}$ and $EM$. Except for the core R5 (due to poor signal-to-noise ratio), the H40$\alpha$ spectra of the other cores are fitted with a single Gaussian profile (see Figure [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(b)). The linewidths are estimated to be in the range $\sim$ \[19, 29\]$\,\rm km\,s^{-1}$, typical of UCH II/compact H II (cite: Hoare2007; Yang2021; Liu2021ATOMSIII).

The inference of the VLA cores representing the intermediate phase between an evolved UCH II region and an early compact H II region is further supported by the identification of radio counterparts from the *CORNISH* survey[^1]. Based on the derived radio properties and association with NIR and MIR emission, the classification of the sample of CORNISH UCH II regions is robust and reliable (cite: Kalcheva2018). VLA cores, R1, R4, and R5 are classified as UCH II regions, G024.4721+00.4877, G024.4736+00.4950, and G024.4698+00.4954 (cite: Kalcheva2018). Core R3 is also detected in the CORNISH survey, but not classified as it does not meet the criteria of flux density greater than $7 \sigma$.

From the ATOMS 3 mm continuum map, we identify ten cores. The estimated radii lie in the range $\sim$ \[3.7, 9.6\]$\times 10^{-2}$ pc with a median value of $7.4\times 10^{-2}$ pc. The cores, MM1, MM5, and MM10 are co-spatial with radio cores R1, R4, and R6, respectively. Radio core R4 is likely fragmented to MM5 and MM6 in the higher resolution ATOMS continuum map. The ATOMS cores, MM3, MM4, and MM9, that do not have radio counterparts, display single-component Gaussian H40$\alpha$ line profiles. The fitted linewidths are in the range $\sim$ \[19, 32\]$\, \rm km\,s^{-1}$. Given the absence of *cm* emission, these could be conjectured as very early stages of massive stars in the HC/UC H II region phase (cite: Liu2021ATOMSIII). The H40$\alpha$ spectra for cores MM2, MM7, and MM8 have poor signal-to-noise and hence, it is difficult to probe their nature.

With the detection of the ring of bright radio and 3 mm continuum emission harbouring HC, UC, and compact H II regions we are likely witnessing a burst of second epoch of massive star formation. The location of these regions broadly aligns with the theoretical predictions of (cite: Maclow2007). Here, the authors simulate the dynamical expansion of an H II region into turbulent, self-gravitating gas driven by the ionized gas’s overpressure, sweeping up a shell of gas. Theoretically, this shell expands in $\rm \sim 10^5\,yr$ to a radius of $\sim$ 1 pc, and subsequently, the ionized gas breaks out of the natal cloud. The results of this simulation show that an episode of secondary collapse ensues in the shell, where existing turbulent density fluctuations in the shell lead to collapse of self-gravitating cores. Consistent with these predictions, (cite: Hunter2008) presents a case study of the UCH II region G5.89-0.39, where they identified multiple $875\,\mu$m cores confined to the expanding shell formed in the process of secondary collapse.

The simulations of (cite: Maclow2007), however, showed the formation of externally ionized low-mass, transient cores in the shell, masquerading as UCH II regions. In our case, 75% of the VLA and ATOMS cores are inferred to be in the early phases of HC, UC, or compact H II regions. From the estimated Lyman continuum photon flux, the compact H II regions are likely ionized by ZAMS stars with spectral type B0$-$O8.5 (cite: Panagia1973) (see Table [\[tab:param-VLAcores\]](#tab:param-VLAcores)). Even though the $H-K$ uncertainty allows for the source E4 to be considered as a Class III source, in all likelihood it is a Class II YSO (Figure [\[fig:cc-cm\]](#fig:cc-cm)(b)) and located within $\sim$3$''$, is possibly the ionizing source of the compact H II region, R1.

## Expanding molecular ring

A molecular ring is clearly visible from the moment zero maps of H$^{13}$CO$^+$ (1-0) (see Figure 1(d)), HCO+ (see Figure 3(a) - (c)) and the column density map (see Figure [\[fig:cdmap_molcore\]](#fig:cdmap_molcore)), The expansion of this ring is evident from the investigation of the gas kinematics in Section [\[sec:vel-struc-ring\]](#sec:vel-struc-ring).

Twelve molecular cores are identified in this molecular gas ring. The radius, mass, surface mass density, and the virial parameter of the cores lie in the range \[0.05, 0.1\] pc, \[4.3, 30.1\] $\rm M_\odot$, \[0.1, 0.4\] $\rm g\,cm^{-2}$, and \[0.7, 3.8\], respectively. In the same order, the median values are estimated to be 0.06 pc, 8.8 $\rm M_\odot$, 0.2 $\rm g\,cm^{-2}$, and 1.8. For all the detected molecular cores, the estimated surface mass densities satisfy the threshold of 0.05$\,\rm g\,cm^{-2}$ proposed by (cite: Urquhart2014) for massive star formation. It is worth noting here that in the recent QUARKS (Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures) survey (cite: Liu2024), nearly half of the identified cores have dense 1.4 mm cold dust counterparts, thus confirming their tendency to form stars.

Gauging their gravitational stability, we find that 50% of the cores have $\alpha_{\rm vir} < 2$, indicating that these are supercritical and under gravitational collapse in the absence of other supporting mechanisms, such as magnetic fields (cite: Kauffmann2013; Tang2019). The other 50% are subcritical cores with $\alpha_{\rm vir} > 2$. These are gravitationally unbound and represent transient objects unless one considers other mechanisms, such as magnetic field or external pressure, that would confine these structures (cite: Kauffmann2013; Li2020). In the case of G24.47, feedback from the newly formed massive stars in the ionized ring and the evidence of the expansion suggest that external pressure will play a key role in confining these compact cores. We searched for infall signature using the H$^{13}$CO$^+$ (1-0) and HCO$^{+}$ spectra extracted toward these cores, but did not find any conclusive evidence. This could be attributed to the possibility that infall signatures are blended with complex dynamics in the molecular ring, including expanding motions and feedback from stellar winds. Further, in the interferometric observations, we may be missing the total power, which makes it difficult to identify absorption features. Supporting the active star formation activity, we have identified one 70$\mu$m point source within $\sim$ 2.5$''$ of M12 from the Herschel PACS point source catalog (cite: PACS2020). This finding serves as compelling evidence for the presence of an embedded protostar, as external heating cannot raise temperatures high enough to emit at this wavelength (cite: Stutz2013).

![](f4-schematic_v5_R1.pdf)

# Hierarchical triggering of multi-epoch massive star formation

Based on our detailed analysis, we propose an interesting picture of multi-epoch massive star formation observed in the G24.47 complex. Our hypothesis is illustrated in the schematic presented in Figure [1](#fig:schematic). The observed hierarchy is initiated with the birth of a massive star in a self-gravitating natal cloud forming an H II region. The thermal overpressure of the warm ionized gas then drives the expansion of the H II region. This leads to a swept-up ring where secondary collapse occurs, thus triggering the second epoch of star formation. In G24.47, we detect a very active high-mass star formation episode in this inner ionized ring with a host of newly formed stars in the early to intermediate evolutionary phases of HC, UC and compact H II regions with detected RRL and cm emission.

To support the above inference, we estimate the dynamical timescale of the expanding H II region, and compare the same with the typical ages of the HC, UC, and compact II regions, following the discussion outlined in (cite: Hongliliu2016) and (cite: Swagat2017). For an H II region expanding into a homogeneous medium, the dynamical age is given by (cite: DysonWilliams1980) $$\begin{equation}
t_{\rm{dyn}}=\frac{4}{7} \frac{R_{\rm{St}}}{C_{\rm{H} \rm{ II}}}\left[\left(\frac{R_{\rm{IF}}}{R_{\rm{St}}}\right)^{7 / 4}-1\right],
\end{equation}$$ where $$\begin{equation}
R_{\rm{St}}=\left(3 N_{\rm{Ly}} / 4 \pi n_{\rm 0}^2 \alpha_{\rm{B}}\right)^{1 / 3} \\
\end{equation}$$ In the above equations, ${C_{\rm{H}{II}}}$ is the isothermal sound speed (assumed to be 10$\rm\,km\,s^{-1}$), $R_{\rm{IF}}$ is the radius of the ionized ring ($\sim$0.8 pc), $\alpha_{\rm{B}}$ is the radiative recombination coefficient taken as 2.6$\times 10^{-13} (10^{4} \rm K/T)^{0.7}\, \rm cm^{3} s^{-1}$ (cite: kwan1997), and $n_{\rm 0}$ is the initial particle density of the ambient gas. We estimate $n_{\rm 0}\sim$ $10^4\,\rm cm^{-3}$ from the retrieved ATLASGAL map (see Appendix [\[apndx:number-density\]](#apndx:number-density)), with the assumption that the physical properties, like density, do not change over evolutionary stages (from quiescent to HII regions) in the star formation process (cite: Urquhart2022). Thus, the dynamical age of the H II region is calculated to be $\rm \sim 2 \times 10^5\,yr$. This ensures sufficient time for the formation of the identified UC and compact H II regions in the inner ionized ring, given the typical lifetimes of these to be $\rm \sim 10^4 - 10^5\,yr$ (cite: Churchwell2002; Davies2011).

[^1]: Co-Ordinated Radio ’N’ Infrared Survey for High-mass star formation (cite: Purcell2013).

In recent studies, evidence of expanding ionized (\[C II\]) shells has been found in wind-blown bubbles (e.g. Orion Veil; (cite: Pabst2019), RCW 120; (cite: Luisi2021)). Indication of such an expansion of the inner ionized ring in G24.47 is seen from the velocity structure probed with the H40$\alpha$ RRL emission. However, the picture that emerges from the investigation of the molecular gas kinematics reveals, perhaps for the first time, a direct and unambiguous signature of an expanding molecular ring in G24.47.

The total mass of the molecular ring ($M_{\rm shell}$) is estimated to be $\sim515\rm\,M_\odot$ from the column density map. Taking the expansion velocity ($v_{\rm exp}$) of $\sim9\rm\,km\,s^{-1}$, the kinetic energy ($0.5 M_{\rm shell} v^{2}_{\rm exp}$) of the expanding ring is calculated to be $\sim 4\times 10^{47} \rm erg$. Addressing the energy feedback from the H II region, we estimate the kinetic and thermal energies of the ionized gas to be $\sim6 \times 10^{46} \rm erg$ and $\sim3 \times 10^{46} \rm erg$, respectively, using the expressions from (cite: Xu2018) and (cite: Li2022). Individually, these are an order of magnitude lower than the kinetic energy of the molecular shell. Our results are similar to those seen in RCW 120 (cite: Luisi2021) and Orion Veil (cite: Pabst2019), where the authors attribute this to leakage of hot plasma into the surrounding. Indeed, the radio ring in G24.47 is observed to be broken towards the south-west (see Figure [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)), which was also reported by (cite: Garay1993).

Theoretical studies (cite: Haid2018) predict that the energy injection from ionized gas into the surrounding medium would dominate that of the stellar wind. To confront the energetics with the creation of the expanding molecular ring in G24.47, we further probe the efficiency of the wind power. Considering a single ionizing O8.5V - O8V star for G24.47, as inferred from the radio flux density, we determine the wind luminosity ($3.2\times 10^{35} \dot{M} v^{2}_{\rm w}$; $\dot{M}$ being the mass loss rate in $\rm M_\odot yr^{-1}$ and $v_{\rm w}$ the wind velocity in $\rm km\,s^{-1}$). Using the parameter values for these spectral types from (cite: Martins2017), we estimate the wind luminosity to be $(4-5)\times 10^{34} \rm erg\,s^{-1}$. This translates to mechanical energy $\sim 3 \times 10^{47} \rm erg$ injected by wind of the ionizing star over the dynamical age of the H II region. This is comparable to the kinetic energy of the molecular gas ring, thus indicating efficient conversion of the mechanical energy of the wind to kinetic energy of the ring driving its expansion. Note that in the above analysis, we have not considered the inclination angle, if any, of the molecular gas ring and the winds from newly formed stars in the ionized ring.

Summarizing the analysis of the energetics, we infer that the total energy budget from the ionizing radiation (both kinetic and thermal) and the stellar wind is sufficient for the creation and expansion of the molecular ring, with the wind kinetic power being possibly the most efficient player.

Furthermore, SO emission, a tracer of low-velocity shocks from H II regions (cite: Liu2020ATOMSI), is seen (not presented here) to be co-spatial with the observed H$^{13}$CO$^+$ (1-0) and HCO$^{+}$ (1-0) molecular ring. Coupled with the feedback from the newly formed massive stars, a third epoch of triggered massive star formation is observed in this expanding molecular ring, where potential high-mass star-forming molecular cores are identified. A scenario of ‘collect and collapse’ (CC) is evident, where gravitational instabilities result in the fragmentation of swept-up ring to molecular condensations which further fragment to the cores that are observed. Consistent with the prediction of the CC hypothesis (cite: Deharveng2003), these condensations, in the form of core clusters (i.e., M1–M3, M4–M5, M6–M7, M8–M9, M12, and M10–M11 apparently corresponding to six core clusters, see Figure [\[fig:RGB_vla_ha\]](#fig:RGB_vla_ha)(d)), are observed to be almost *regularly* spaced in the molecular gas ring enveloping the inner ionized ring.

# Conclusions

Evidence for triggered star formation linking several epochs of stars around H II regions is difficult to assemble. It is challenging to associate evolved massive stars with the next epoch of star-forming regions, each of which must show indications of ongoing star formation activity. Based on a detailed continuum and multispectral line study of G24.47 using data from the ATOMS survey and archival radio and infrared data, we provide evidence of hierarchical triggering of three epochs of massive star formation. The first is the massive star(s) responsible for forming the H II region G24.47. Using the 4.86 GHz VLA map, we propose the spectral type to be O8.5V–O8V. The inner ring of enhanced radio and 3 mm emission comprises the next epoch of massive stars, which formed due to secondary collapse of the swept-up material. We detected six radio and ten 3 mm cores showing signatures of various evolutionary phases, ranging from the initial stages of gravitational collapse to intermediate phases between UC and compact H II regions. The molecular gas kinematics analysis unveils direct evidence of an expanding molecular ring powered by the ionized radiation and the stellar wind kinetic energy. Furthermore, the molecular gas ring expanding at $\sim$ 9$\,\rm km\,s^{-1}$ hosts the third epoch of potential massive star-forming regions, where we identified twelve molecular cores. Virial analysis indicates that 50% of them are supercritical and in gravitational collapse. This observational evidence strongly advocates for more detailed case studies to address the exact influence of expanding H II regions in triggering further star formation. Detailed kinematic studies of the ionized and neutral material in a sample of promising candidates, utilizing high-resolution data, are essential to understand the underlying physical processes.

The authors thank the referee for insightful comments/suggestions which helped improve the manuscript. This work has been supported by the National Key R&D Program of China (No. 2022YFA1603101). H.-L. Liu is supported by National Natural Science Foundation of China (NSFC) through the grant No. 12103045, by Yunnan Fundamental Research Project (grant No. 202301AT070118, 202401AS070121), and by Xingdian Talent Support Plan – Youth Project. T.L. acknowledges the support by the National Key R&D Program of China (No. 2022YFA1603101), National Natural Science Foundation of China (NSFC) through grants No.12073061 and No.12122307, the international partnership program of Chinese Academy of Sciences through grant No.114231KYSB20200009, and the Tianchi Talent Program of Xinjiang Uygur Autonomous Region. G.G. and L.B. acknowledge support by the ANID BASAL project FB210003. This work was performed in part at the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration (80NM0018D0004). This work is sponsored (in part) by the Chinese Academy of Sciences (CAS), through a grant to the CAS South America Center for Astronomy (CASSACA) in Santiago, Chile. M.J. acknowledges support from the Research Council of Finland grant No. 348342. JOC acknowledges financial support from the South African Department of Science and Innovation’s National Research Foundation under the ISARP RADIOMAP Joint Research Scheme (DSI-NRF Grant Number 150551). This research made use of astrodendro, a Python package to compute dendrograms of Astronomical data (<http://www.dendrograms.org/>). This research made use of Astropy, a community-developed core Python package for Astronomy (cite: Astropy2018).

natexlab

(ref: Arce2011) Arce, H. G., Borkin, M. A., Goodman, A. A., Pineda, J. E., & Beaumont, C. N. 2011, ApJ, 742, 105, doi: [`10.1088/0004-637X/742/2/105`](http://doi.org/10.1088/0004-637X/742/2/105)

(ref: Areal2020) Areal, M. B., Buccino, A., Paron, S., Fariña, C., & Ortega, M. E. 2020, MNRAS, 496, 870, doi: [`10.1093/mnras/staa1543`](http://doi.org/10.1093/mnras/staa1543)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Beaumont2010) Beaumont, C. N., & Williams, J. P. 2010, ApJ, 709, 791, doi: [`10.1088/0004-637X/709/2/791`](http://doi.org/10.1088/0004-637X/709/2/791)

(ref: Becker1994) Becker, R. H., White, R. L., Helfand, D. J., & Zoonematkermani, S. 1994, ApJS, 91, 347, doi: [`10.1086/191941`](http://doi.org/10.1086/191941)

(ref: Benjamin2003) Benjamin, R. A., Churchwell, E., Babler, B. L., et al. 2003, PASP, 115, 953, doi: [`10.1086/376696`](http://doi.org/10.1086/376696)

(ref: Bertoldi1992) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140, doi: [`10.1086/171638`](http://doi.org/10.1086/171638)

(ref: Bessel1988) Bessell, M. S., & Brett, J. M. 1988, PASP, 100, 1134, doi: [`10.1086/132281`](http://doi.org/10.1086/132281)

(ref: Bhadari2021) Bhadari, N. K., Dewangan, L. K., Zemlyanukha, P. M., et al. 2021, ApJ, 922, 207, doi: [`10.3847/1538-4357/ac2a44`](http://doi.org/10.3847/1538-4357/ac2a44)

(ref: Bonne2023) Bonne, L., Kabanovic, S., Schneider, N., et al. 2023, A&A, 679, L5, doi: [`10.1051/0004-6361/202347721`](http://doi.org/10.1051/0004-6361/202347721)

(ref: Cambresy2013) Cambrésy, L., Marton, G., Feher, O., Tóth, L. V., & Schneider, N. 2013, A&A, 557, A29, doi: [`10.1051/0004-6361/201321235`](http://doi.org/10.1051/0004-6361/201321235)

(ref: Churchwell2002) Churchwell, E. 2002, ARA&A, 40, 27, doi: [`10.1146/annurev.astro.40.060401.093845`](http://doi.org/10.1146/annurev.astro.40.060401.093845)

(ref: Churchwell1990) Churchwell, E., Walmsley, C. M., & Cesaroni, R. 1990, A&AS, 83, 119

(ref: Churchwell2006) Churchwell, E., Povich, M. S., Allen, D., et al. 2006, ApJ, 649, 759, doi: [`10.1086/507015`](http://doi.org/10.1086/507015)

(ref: Contreras2016) Contreras, Y., Garay, G., Rathborne, J. M., & Sanhueza, P. 2016, MNRAS, 456, 2041, doi: [`10.1093/mnras/stv2796`](http://doi.org/10.1093/mnras/stv2796)

(ref: Dale2015) Dale, J. E., Haworth, T. J., & Bressert, E. 2015, MNRAS, 450, 1199, doi: [`10.1093/mnras/stv396`](http://doi.org/10.1093/mnras/stv396)

(ref: Swagat2017) Das, S. R., Tej, A., Vig, S., et al. 2017, MNRAS, 472, 4750, doi: [`10.1093/mnras/stx2290`](http://doi.org/10.1093/mnras/stx2290)

(ref: Davies2011) Davies, B., Hoare, M. G., Lumsden, S. L., et al. 2011, MNRAS, 416, 972, doi: [`10.1111/j.1365-2966.2011.19095.x`](http://doi.org/10.1111/j.1365-2966.2011.19095.x)

(ref: delaFuente2020) de la Fuente, E., Tafoya, D., Trinidad, M. A., et al. 2020, MNRAS, 497, 4436, doi: [`10.1093/mnras/staa2149`](http://doi.org/10.1093/mnras/staa2149)

(ref: Deharveng2003) Deharveng, L., Lefloch, B., Zavagno, A., et al. 2003, A&A, 408, L25, doi: [`10.1051/0004-6361:20031157`](http://doi.org/10.1051/0004-6361:20031157)

(ref: Deharveng2010) Deharveng, L., Schuller, F., Anderson, L. D., et al. 2010, A&A, 523, A6, doi: [`10.1051/0004-6361/201014422`](http://doi.org/10.1051/0004-6361/201014422)

(ref: DysonWilliams1980) Dyson, J. E., & Williams, D. A. 1980, Physics of the interstellar medium

(ref: ElmegreenLada1977) Elmegreen, B. G., & Lada, C. J. 1977, ApJ, 214, 725, doi: [`10.1086/155302`](http://doi.org/10.1086/155302)

(ref: Figueira2017) Figueira, M., Zavagno, A., Deharveng, L., et al. 2017, A&A, 600, A93, doi: [`10.1051/0004-6361/201629379`](http://doi.org/10.1051/0004-6361/201629379)

(ref: Garay1993) Garay, G., Rodriguez, L. F., Moran, J. M., & Churchwell, E. 1993, ApJ, 418, 368, doi: [`10.1086/173396`](http://doi.org/10.1086/173396)

(ref: Semadeni2020) González-Samaniego, A., & Vazquez-Semadeni, E. 2020, MNRAS, 499, 668, doi: [`10.1093/mnras/staa2921`](http://doi.org/10.1093/mnras/staa2921)

(ref: Haid2018) Haid, S., Walch, S., Seifried, D., et al. 2018, MNRAS, 478, 4799, doi: [`10.1093/mnras/sty1315`](http://doi.org/10.1093/mnras/sty1315)

(ref: PACS2020) Herschel Point Source Catalogue Working Group, Marton, G., Calzoletti, L., et al. 2020, VizieR Online Data Catalog: Herschel/PACS Point Source Catalogs (Herschel team, 2017), VizieR On-line Data Catalog: VIII/106. Originally published in: Herschel catalogs (2017)

(ref: Hoare2007) Hoare, M. G., Kurtz, S. E., Lizano, S., Keto, E., & Hofner, P. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 181, doi: [`10.48550/arXiv.astro-ph/0603560`](http://doi.org/10.48550/arXiv.astro-ph/0603560)

(ref: Hoq2013) Hoq, S., Jackson, J. M., Foster, J. B., et al. 2013, ApJ, 777, 157, doi: [`10.1088/0004-637X/777/2/157`](http://doi.org/10.1088/0004-637X/777/2/157)

(ref: Hunter2008) Hunter, T. R., Brogan, C. L., Indebetouw, R., & Cyganowski, C. J. 2008, ApJ, 680, 1271, doi: [`10.1086/588016`](http://doi.org/10.1086/588016)

(ref: Kabanovic2022) Kabanovic, S., Schneider, N., Ossenkopf-Okada, V., et al. 2022, A&A, 659, A36, doi: [`10.1051/0004-6361/202142575`](http://doi.org/10.1051/0004-6361/202142575)

(ref: Kalcheva2018) Kalcheva, I. E., Hoare, M. G., Urquhart, J. S., et al. 2018, A&A, 615, A103, doi: [`10.1051/0004-6361/201832734`](http://doi.org/10.1051/0004-6361/201832734)

(ref: Kauffmann2013) Kauffmann, J., Pillai, T., & Goldsmith, P. F. 2013, ApJ, 779, 185, doi: [`10.1088/0004-637X/779/2/185`](http://doi.org/10.1088/0004-637X/779/2/185)

(ref: Kendrew2012) Kendrew, S., Simpson, R., Bressert, E., et al. 2012, ApJ, 755, 71, doi: [`10.1088/0004-637X/755/1/71`](http://doi.org/10.1088/0004-637X/755/1/71)

(ref: Keto2008) Keto, E., Zhang, Q., & Kurtz, S. 2008, ApJ, 672, 423, doi: [`10.1086/522570`](http://doi.org/10.1086/522570)

(ref: Koornneef1983) Koornneef, J. 1983, A&A, 128, 84

(ref: Kurtz2005) Kurtz, S. 2005, in Massive Star Birth: A Crossroads of Astrophysics, ed. R. Cesaroni, M. Felli, E. Churchwell, & M. Walmsley, Vol. 227, 111–119, doi: [`10.1017/S1743921305004424`](http://doi.org/10.1017/S1743921305004424)

(ref: kwan1997) Kwan, J. 1997, ApJ, 489, 284, doi: [`10.1086/304773`](http://doi.org/10.1086/304773)

(ref: LadaAdams1992) Lada, C. J., & Adams, F. C. 1992, ApJ, 393, 278, doi: [`10.1086/171505`](http://doi.org/10.1086/171505)

(ref: Lawrence2007) Lawrence, A., Warren, S. J., Almaini, O., et al. 2007, MNRAS, 379, 1599, doi: [`10.1111/j.1365-2966.2007.12040.x`](http://doi.org/10.1111/j.1365-2966.2007.12040.x)

(ref: Li2022) Li, C.-X., Wang, H.-C., Ma, Y.-H., et al. 2022, Research in Astronomy and Astrophysics, 22, 045008, doi: [`10.1088/1674-4527/ac52a0`](http://doi.org/10.1088/1674-4527/ac52a0)

(ref: Li2020) Li, S., Zhang, Q., Liu, H. B., et al. 2020, ApJ, 896, 110, doi: [`10.3847/1538-4357/ab84f1`](http://doi.org/10.3847/1538-4357/ab84f1)

(ref: Hongliliu2016) Liu, H.-L., Li, J.-Z., Wu, Y., et al. 2016, ApJ, 818, 95, doi: [`10.3847/0004-637X/818/1/95`](http://doi.org/10.3847/0004-637X/818/1/95)

(ref: Liu2021ATOMSIII) Liu, H.-L., Liu, T., Evans, Neal J., I., et al. 2021, MNRAS, 505, 2801, doi: [`10.1093/mnras/stab1352`](http://doi.org/10.1093/mnras/stab1352)

(ref: Liu2022) Liu, H.-L., Tej, A., Liu, T., et al. 2022, MNRAS, 510, 5009, doi: [`10.1093/mnras/stab2757`](http://doi.org/10.1093/mnras/stab2757)

(ref: Liu2023) —. 2023, MNRAS, 522, 3719, doi: [`10.1093/mnras/stad047`](http://doi.org/10.1093/mnras/stad047)

(ref: Liu2020ATOMSI) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020, MNRAS, 496, 2790, doi: [`10.1093/mnras/staa1577`](http://doi.org/10.1093/mnras/staa1577)

(ref: Liu2024) Liu, X., Liu, T., Zhu, L., et al. 2024, Research in Astronomy and Astrophysics, 24, 025009, doi: [`10.1088/1674-4527/ad0d5c`](http://doi.org/10.1088/1674-4527/ad0d5c)

(ref: Lockman1989) Lockman, F. J. 1989, ApJS, 71, 469, doi: [`10.1086/191383`](http://doi.org/10.1086/191383)

(ref: Lucas2008) Lucas, P. W., Hoare, M. G., Longmore, A., et al. 2008, MNRAS, 391, 136, doi: [`10.1111/j.1365-2966.2008.13924.x`](http://doi.org/10.1111/j.1365-2966.2008.13924.x)

(ref: Luisi2021) Luisi, M., Anderson, L. D., Schneider, N., et al. 2021, Science Advances, 7, eabe9511, doi: [`10.1126/sciadv.abe9511`](http://doi.org/10.1126/sciadv.abe9511)

(ref: Maclow2007) Mac Low, M.-M., Toraskar, J., Oishi, J. S., & Abel, T. 2007, ApJ, 668, 980, doi: [`10.1086/521292`](http://doi.org/10.1086/521292)

(ref: Martin2005) Martı́n-Hernández, N. L., Vermeij, R., & van der Hulst, J. M. 2005, A&A, 433, 205, doi: [`10.1051/0004-6361:20042143`](http://doi.org/10.1051/0004-6361:20042143)

(ref: Martins2017) Martins, F., & Palacios, A. 2017, A&A, 598, A56, doi: [`10.1051/0004-6361/201629538`](http://doi.org/10.1051/0004-6361/201629538)

(ref: Meyer1997) Meyer, M. R., Calvet, N., & Hillenbrand, L. A. 1997, AJ, 114, 288, doi: [`10.1086/118474`](http://doi.org/10.1086/118474)

(ref: Oey2005) Oey, M. S., Watson, A. M., Kern, K., & Walth, G. L. 2005, AJ, 129, 393, doi: [`10.1086/426333`](http://doi.org/10.1086/426333)

(ref: Pabst2019) Pabst, C., Higgins, R., Goicoechea, J. R., et al. 2019, Nature, 565, 618, doi: [`10.1038/s41586-018-0844-1`](http://doi.org/10.1038/s41586-018-0844-1)

(ref: Panagia1973) Panagia, N. 1973, AJ, 78, 929, doi: [`10.1086/111498`](http://doi.org/10.1086/111498)

(ref: Paron2011) Paron, S., Petriella, A., & Ortega, M. E. 2011, A&A, 525, A132, doi: [`10.1051/0004-6361/201015312`](http://doi.org/10.1051/0004-6361/201015312)

(ref: Potdar2022) Potdar, A., Das, S. R., Issac, N., et al. 2022, MNRAS, 510, 658, doi: [`10.1093/mnras/stab3479`](http://doi.org/10.1093/mnras/stab3479)

(ref: Purcell2009) Purcell, C. R., Minier, V., Longmore, S. N., et al. 2009, A&A, 504, 139, doi: [`10.1051/0004-6361/200811358`](http://doi.org/10.1051/0004-6361/200811358)

(ref: Purcell2013) Purcell, C. R., Hoare, M. G., Cotton, W. D., et al. 2013, ApJS, 205, 1, doi: [`10.1088/0067-0049/205/1/1`](http://doi.org/10.1088/0067-0049/205/1/1)

(ref: Quireza2006) Quireza, C., Rood, R. T., Bania, T. M., Balser, D. S., & Maciel, W. J. 2006, ApJ, 653, 1226, doi: [`10.1086/508803`](http://doi.org/10.1086/508803)

(ref: Rosolowsky2008) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Saha2022) Saha, A., Tej, A., Liu, H.-L., et al. 2022, MNRAS, 516, 1983, doi: [`10.1093/mnras/stac2353`](http://doi.org/10.1093/mnras/stac2353)

(ref: sanhueza2012) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012, ApJ, 756, 60, doi: [`10.1088/0004-637X/756/1/60`](http://doi.org/10.1088/0004-637X/756/1/60)

(ref: Sanhueza2019) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102, doi: [`10.3847/1538-4357/ab45e9`](http://doi.org/10.3847/1538-4357/ab45e9)

(ref: Saral2017) Saral, G., Hora, J. L., Audard, M., et al. 2017, ApJ, 839, 108, doi: [`10.3847/1538-4357/aa6575`](http://doi.org/10.3847/1538-4357/aa6575)

(ref: Schlingman2011) Schlingman, W. M., Shirley, Y. L., Schenk, D. E., et al. 2011, ApJS, 195, 14, doi: [`10.1088/0067-0049/195/2/14`](http://doi.org/10.1088/0067-0049/195/2/14)

(ref: Schmiedeke2016) Schmiedeke, A., Schilke, P., Möller, T., et al. 2016, A&A, 588, A143, doi: [`10.1051/0004-6361/201527311`](http://doi.org/10.1051/0004-6361/201527311)

(ref: Skrutskie2006) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163, doi: [`10.1086/498708`](http://doi.org/10.1086/498708)

(ref: Stutz2013) Stutz, A. M., Tobin, J. J., Stanke, T., et al. 2013, ApJ, 767, 36, doi: [`10.1088/0004-637X/767/1/36`](http://doi.org/10.1088/0004-637X/767/1/36)

(ref: Tang2019) Tang, Y.-W., Koch, P. M., Peretto, N., et al. 2019, ApJ, 878, 10, doi: [`10.3847/1538-4357/ab1484`](http://doi.org/10.3847/1538-4357/ab1484)

(ref: Thompson2012) Thompson, M. A., Urquhart, J. S., Moore, T. J. T., & Morgan, L. K. 2012, MNRAS, 421, 408, doi: [`10.1111/j.1365-2966.2011.20315.x`](http://doi.org/10.1111/j.1365-2966.2011.20315.x)

(ref: Urquhart2014) Urquhart, J. S., Moore, T. J. T., Csengeri, T., et al. 2014, MNRAS, 443, 1555, doi: [`10.1093/mnras/stu1207`](http://doi.org/10.1093/mnras/stu1207)

(ref: Urquhart2018) Urquhart, J. S., König, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059, doi: [`10.1093/mnras/stx2258`](http://doi.org/10.1093/mnras/stx2258)

(ref: Urquhart2022) Urquhart, J. S., Wells, M. R. A., Pillai, T., et al. 2022, MNRAS, 510, 3389, doi: [`10.1093/mnras/stab3511`](http://doi.org/10.1093/mnras/stab3511)

(ref: Walch2012) Walch, S. K., Whitworth, A. P., Bisbas, T., Wünsch, R., & Hubber, D. 2012, MNRAS, 427, 625, doi: [`10.1111/j.1365-2966.2012.21767.x`](http://doi.org/10.1111/j.1365-2966.2012.21767.x)

(ref: Walsh1998) Walsh, A. J., Burton, M. G., Hyland, A. R., & Robinson, G. 1998, MNRAS, 301, 640, doi: [`10.1046/j.1365-8711.1998.02014.x`](http://doi.org/10.1046/j.1365-8711.1998.02014.x)

(ref: Wang2016) Wang, Y., Audard, M., Fontani, F., et al. 2016, A&A, 587, A69, doi: [`10.1051/0004-6361/201526637`](http://doi.org/10.1051/0004-6361/201526637)

(ref: Watson2008) Watson, C., Povich, M. S., Churchwell, E. B., et al. 2008, ApJ, 681, 1341, doi: [`10.1086/588005`](http://doi.org/10.1086/588005)

(ref: Wink1982) Wink, J. E., Altenhoff, W. J., & Mezger, P. G. 1982, A&A, 108, 227

(ref: Fengwei2023ATOMSXV) Xu, F.-W., Wang, K., Liu, T., et al. 2023, MNRAS, 520, 3259, doi: [`10.1093/mnras/stad012`](http://doi.org/10.1093/mnras/stad012)

(ref: Xu2018) Xu, J.-L., Xu, Y., Zhang, C.-P., et al. 2018, A&A, 609, A43, doi: [`10.1051/0004-6361/201629189`](http://doi.org/10.1051/0004-6361/201629189)

(ref: Yang2021) Yang, A. Y., Urquhart, J. S., Thompson, M. A., et al. 2021, A&A, 645, A110, doi: [`10.1051/0004-6361/202038608`](http://doi.org/10.1051/0004-6361/202038608)

(ref: Zavagno2006) Zavagno, A., Deharveng, L., Comerón, F., et al. 2006, A&A, 446, 171, doi: [`10.1051/0004-6361:20053952`](http://doi.org/10.1051/0004-6361:20053952)

(ref: Zavagno2007) Zavagno, A., Pomarès, M., Deharveng, L., et al. 2007, A&A, 472, 835, doi: [`10.1051/0004-6361:20077474`](http://doi.org/10.1051/0004-6361:20077474)

(ref: Zhang2023ATOMSXIV) Zhang, C., Zhu, F.-Y., Liu, T., et al. 2023a, MNRAS, 520, 3245, doi: [`10.1093/mnras/stad190`](http://doi.org/10.1093/mnras/stad190)

(ref: Zhang2023ATOMSXIII) Zhang, S., Wang, K., Liu, T., et al. 2023b, MNRAS, 520, 322, doi: [`10.1093/mnras/stad011`](http://doi.org/10.1093/mnras/stad011)

</paper>

Write the methods card for this paper.