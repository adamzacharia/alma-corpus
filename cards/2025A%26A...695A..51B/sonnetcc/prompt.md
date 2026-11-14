# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...695A..51B\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...695A..51B",
 "title": "Hierarchical accretion flow from the G351 infrared dark filament to its central cores",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Beuther, H.",
 "n_authors": 5,
 "arxiv_id": "2502.13866",
 "doi": "10.1051/0004-6361/202452754",
 "alma_projects_linked_by_archive": [
  "2015.1.00496.S",
  "2016.1.01036.S"
 ]
}
```

Paper text:
<paper>
# Hierarchical accretion flow from the G351 infrared dark filament to its central cores

Quantifying the accretion flow from large cloud scales down to individual protostars is a central ingredient to the understanding of (high-mass) star formation.

We characterize and quantify this multi-scale flow for a prototypical high-mass star-forming region.

In a multi-scale analysis from parsec to $\sim$50 au scales, we combined multiple single-dish and interferometric observations to study the gas flow from large-scale sizes of several parsec (Mopra) via intermediate-scale filamentary gas flows (ALMA-IMF) to the central cores (ALMA DIHCA and configuration 10 data). The highest-resolution multi-configuration ALMA dataset achieved a spatial resolution of $0.027''\times 0.022''$ or 50 au.

This multi-scale study allows us to follow the gas from the environment of the high-mass star-forming region ($\sim$2 pc) via intermediate-scale ($\sim$0.25 pc) filamentary gas flows down to the innermost cores within the central few 1000 au. The intermediate-scale filaments connect spatially and kinematically to the larger-scale cloud as well as the innermost cores. We estimate a filamentary mass inflow rate around $10^{-3}$ M$_{\odot}$ yr$^{-1}$, feeding into the central region that hosts at least a dozen mm cores. While the flow from the cloud via the filaments down to 10$^4$ au appears relatively ordered, within the central 10$^4$ au the kinematic structures become much more complicated and disordered. We speculate that this is caused by the interplay of the converging infalling gas with feedback processes from the forming central protostars.

This multi-scale study characterises and quantifies the hierarchical gas flow from clouds down to the central protostars for a prototypical infrared dark cloud with several embedded cores at an unprecedented detail. While comparatively ordered gas flows are found over a broad range of scales, the innermost area exhibits more disordered structures, likely caused by the combination of inflow, outflow and cluster dynamical processes.

# Introduction

The formation of stars requires gas flowing from the parental large molecular cloud down to the central protostars. A quantification on how the gas flows over a broad range of spatial scales remains one of the major problems in observational star formation research. Cloud dynamics and mass flows have been studied separately toward molecular clouds (e.g., (cite: henshaw2013; peretto2013; barnes2018; beuther2020)), more filamentary cluster-forming structures (e.g., (cite: kirk2013; peretto2014; henshaw2014; liu2015; beuther2015b; chen2019; barnes2023; sandoval-garrido2024)), or more recently also the flows toward individual cores within high-mass star-forming regions (e.g., (cite: sanhueza2021; wells2024)) and even disks (e.g., (cite: maud2017; olguin2023)). In low-mass star-forming regions, recently the discussion focused a lot on gas streamers that may feed individual cores and disks (e.g., (cite: pineda2023; valdivia2023; gieser2024; kueffmeier2024)). Following slightly different approaches, statistical studies of larger samples of (high-mass) star-forming regions searching for asymmetric line profiles revealed evidence for global collapse in such environments (e.g., (cite: wu2003; fuller2005; jackson2019)). However, so far investigations are lacking for individual regions how the gas flows from the parsec-scale clouds toward the inner 50 au around the protostar.

Here, we are aiming at exactly that for the high-mass star-forming filament G351 that hosts at the very center a hot molecular core G351.77-0.54. To study the kinematics from the large-scale infrared dark filament, we combine single-dish data from the MALT90 survey (cite: jackson2013) with interferometric mosaic observations from the Atacama Large Millimeter/submillimeter Array (ALMA) covering the immediate environment of the central cluster (ALMA-IMF, (cite: motte2022; ginsburg2022; cunningham2023; sandoval-garrido2024)) to very-high-spatial-resolution ALMA data toward the central cores (cite: beuther2017b; beuther2019; olguin2021; taniguchi2023).

![](g351_large_v2.pdf)

The target of our investigation is the well-know high-mass star-forming region G351.77-0.54 (also known as IRAS 17233-3606) that is part of the larger-scale filamentary infrared dark cloud IRDC G351.77-0.53 (left panel of Fig. [1](#g351_large), e.g., (cite: leurini2011b)). The region is very line rich and hosts class II CH$_3$OH masers (e.g., (cite: norris1993; walsh1998; leurini2011; beuther2017b; beuther2019; cunningham2023; bonfand2024)). While the region drives strong outflows (e.g., (cite: leurini2009; leurini2013; klaassen2015; towner2024)), rotational motions have been identified in highly excited NH$_3$ and CH$_3$CN emission (cite: beuther2009c; beuther2017b). The absolute distance to the region has been debated, and values typically between 1.0 and 2.2 kpc have been reported (e.g., (cite: norris1993; leurini2011; motte2022)). A recent analysis of Gaia parallaxes of likely members of the region find a distance of $\sim$2.0$\pm 0.14$ kpc (cite: reyes2024). We use that distance in the following. Scaling the luminosity of the region estimated by (cite: urquhart2018) to 2 kpc distance, G351.77-0.54 has a luminosity of $\sim$8.2$\times10^4$ L$_{\odot}$. Similarly, if we scale the mass derived by (cite: urquhart2018) to this new distance, the main G351.77-0.54 star-forming region has a mass of $\sim$2065 M$_{\odot}$ over an area with radius $\sim$0.55 pc. For comparison, analysis of highly excited CH$_3$CN emission around the main central mm peak at $0.06''$ resolution shows that the data are consistent with a 10 M$_{\odot}$ central protostar (cite: beuther2017b). One should keep in mind that this region is forming a cluster and already within the central $\sim$10$^4$ au at least 12 mm cores have been resolved (cite: beuther2019).

# Data and observations

## Large-scale and single-dish data

For the largest spatial scales on the order of the parsec-long parental filament, we resorted to the mid-infrared and and submm Galactic plane surveys Spitzer-GLIMPSE (cite: churchwell2009) and ATLASGAL (cite: schuller2009). We used the Spitzer 8 $\mu$m image with a spatial resolution of $\sim$2$''$. The corresponding ATLASGAL 870 $\mu$m data have a beam size of $19''$.

Since we are interested in the kinematics, on scales of several parsec around the high-mass star-forming region G351 we used the Millimetre Astronomy Legacy Team 90 GHz (MALT90) survey that mapped with the Mopra 22 m telescope a $3'\times3'$ area around the central G351 region in several spectral lines (cite: foster2011; foster2013; jackson2013). We mainly used the datacubes in the HCO$^+(1-0)$ (89.188526 GHz) and N$_2$H$^+(1-0)$ (93.173772 GHz) lines with a spatial and spectral resolution of $38''$ and 0.11 km s$^{-1}$. The typical rms noise was 0.25 K ($T_A^*$) in a 0.11 km s$^{-1}$ channel. The original MALT90 N$_2$H$^+(1-0)$ map was shifted by roughly $23''$ to the east compared to the ATLASGAL 870 $\mu$m map. However, morphologically both maps agree well with the filamentary structure extending toward the northwest. Therefore, we shifted all MALT90 maps by 3 pixels or $22.9''$ to the west to account for this difference, most likely caused by pointing of the single-dish telescope.

## Atacama Large Millimeter/submm Array (ALMA) data

### ALMA-IMF mosaic

The ALMA-IMF program is an ALMA cycle 5 large program that observed 15 high-mass protoclusters covering a span of evolutionary stages. A program overview and data reduction details are presented in (cite: motte2022) and (cite: ginsburg2022). The regions were typically observed as mosaics in band 6 (1.3 mm) and band 3 (3 mm). For G351.77, the corresponding mosaic sizes were $132''\times 132''$ and $190''\times 180''$, respectively. From the many observed spectral lines, we focus only on two, in particular on the DCN(3–2) and H$_2$CO(3–2) lines. The spectral resolution for the two lines was 0.34 and 0.17 km s$^{-1}$, respectively. The 1.3 mm data were observed in one ALMA 12 m array configuration (C43-3) and the 7 m array to also cover larger spatial scales. For more details about the data reduction and imaging procedures, we refer to (cite: ginsburg2022). The spatial resolution and 1.3 mm continuum $1\sigma$ rms values are $1.1''\times 0.8''$ and 0.6 mJy beam$^{-1}$, respectively. The spectral line datacubes were recently released by (cite: cunningham2023). The $1\sigma$ rms values for the DCN(3–2) and H$_2$CO(3–2) lines were 14.4 and 15.8 mJy beam$^{-1}$ at 0.34 and 0.17 km s$^{-1}$ resolution, respectively (cite: cunningham2023).

![](continuum_v2.pdf)

### ALMA zoom toward the center

For the highest spatial resolution zoom into the central region of G351, we combined the data from two projects conducted with ALMA in the 1.3 mm band. The intermediate-spatial resolution observations in ALMA configurations 5 and 8 were conducted as part of the DIHCA project (Digging into the interior of hot cores with ALMA) led by PI P. Sanhueza (project ID: 2016.1.01036.S). Early results from DIHCA can be found in, for example, (cite: olguin2021; olguin2022), (cite: taniguchi2023), (cite: li2024), and (cite: ishihara2024). The corresponding highest-angular-resolution ALMA configuration 10 data, also in the 1.3 mm band, were observed in project ID 2015.1.00496.S and were published in (cite: beuther2019). While these very-high-resolution data (25 mas$\times$20 mas) resolve the small-scale structure of the region well, they clearly resolve out all extended emission (cite: beuther2019).

To overcome this extreme spatial filtering issue, we now combined the DIHCA configuration 5 and 8 data with the separately observed configuration 10 data. For details about the configuration 10 data calibration, self-calibration and imaging, we refer to (cite: beuther2019). The corresponding DIHCA configuration 5 and 8 data were observed with four spectral windows, two in the lower sideband (216.9–218.7 GHz and 219.0–221.0 GHz) and two in the upper sideband (231.0–233.0 GHz and 231.0–233.0 GHz). Calibration and imaging was conducted in CASA. Self-calibration was done separately for the configuration 5 and 8 data with four iterations of phase self-calibration for each configuration. The first iteration used the configuration 10 data as model for a better spatial alignment of the three datasets. Then phase-only self-calibration was done with three decreasing solution intervals: for the configuration 8 data the length of the scan (solint=’inf’), 30 and 15 sec, for the configuration 5 data 30, 20 and 10sec. The signal-to-noise ratio between the first and last self-calibration iterations improved from 145 to 200 and from 30 to 108 for the configuration 8 and 5 data, respectively. To evaluate the scales traced by each configuration, we first imaged all three datasets separately, and then conducted a joint deconvolution of all configurations together with a Briggs robust weighting of 0. Figure [2](#continuum) presents an overview of the individually and the jointly imaged datasets. Scientific details are discussed in section [3.3](#small-scale). The angular resolution of the individual configuration continuum datasets are $0.27''\times 0.23''$ (position angle PA=$-76^o$), $0.057''\times 0.034''$ (PA=$48^o$) and $0.021''\times 0.015''$ (PA=$-74^o$), respectively. The angular resolution of the jointly deconvolved continuum image in the bottom-right panel of Fig. [2](#continuum) is then $0.027''\times 0.022''$ (PA=$88^o$). This image now combines the high spatial resolution with the recovery of also the larger spatial scales (see also Section [3.3](#small-scale)). The $1\sigma$ rms of the continuum and spectral line data (we mainly focus on H$_2$CO$(3_{2,2}-2_{2,1})$ at 218.476 GHz, also the combination of all three configurations) is 60 $\mu$Jy beam$^{-1}$ and 0.7 mJy beam$^{-1}$ (in 1.0 km s$^{-1}$ channels). The synthesized beam of the H$_2$CO$(3_{2,2}-2_{2,1})$ line with a Briggs robust weighting of 0 is $0.035''\times 0.03''$.

# Results

![](almaimf_zoom.pdf)

## Large-scale structure and dynamics

Figure [1](#g351_large) (left panel) shows how the central G351 high-mass star-forming region is located in the middle of a filamentary infrared dark cloud (IRDC), typically considered as sites of early star formation (e.g., (cite: egan1998; pillai2006; peretto2009; beuther2020)). While the IRDC largely presents a pristine environment, the 8 $\mu$m image already shows localized ongoing star formation toward the central region that was discussed in Sect. [1](#intro). If one focuses more on the central region and the corresponding kinematics, the middle and right panels present the integrated emission and the 1st moment maps (intensity-weighted peak velocities) of the HCO$^+(1-0)$ and N$_2$H$^+(1-0)$ lines. While the integrated N$_2$H$^+$ emission recovers well the filamentary north-eastern structure also seen in the 870 $\mu$m emission (Fig. [1](#g351_large) left panel), the HCO$^+$ emission is less structured and more spherically shaped around the central region. These structural slightly different appearances may well be optical depth effects where HCO$^+$ has a higher optical depth and traces more of the diffuse environmental cloud emission whereas N$_2$H$^+$ as an optically thin high-density tracer follows better the dust continuum emission (e.g., (cite: sanhueza2012)). Independent of that, both spectral line data reveal a velocity gradient roughly in north-south direction across the region.

We will get back to that structure in the higher-resolution data discussed below.

## Intermediate-scale filamentary structure and kinematics

Zooming into the region more, the left and middle panels of Fig. [3](#ALMA-IMF) present the kinematics and spatial structure of the gas and dust at roughly 2000 au resolution for the H$_2$CO(3–2) and DCN(3–2) lines. While the central part appears elongated roughly in the east-west direction, one clearly identifies filamentary structures leading toward the central region from the northern and southern direction. More precisely, the blue-shifted gas connects to the central area at its north-eastern edge, whereas the red-shifted gas connects at the south-western side. Qualitatively speaking, these blue- and red-shifted filaments are the high-spatial-resolution counterparts to the large-scale blue-red velocity gradient across the entire star-forming region discussed in Sect. [3.1](#largescale) (see also Fig. [1](#g351_large)). While one can identify potentially even more gas feeding structures, for instance, the blue-shifted extension to the east (Fig. [3](#ALMA-IMF) left and middle panel), in the following we concentrate on the most pronounced filamentary structures to the north and south marked by the ellipses in the middle panel of Fig. [3](#ALMA-IMF).

Although the general inclination of the large- as well as small-scale filamentary structure is not known, the data are consistent with filamentary gas streams feeding the central $\sim$10$^4$ au of this star-forming region. In such a filamentary streaming picture, one can quantify mass flow rates $\dot{M}$ following, for example, (cite: kirk2013), (cite: henshaw2014), and (cite: wells2024):

$$\dot{M} = \frac{M_{\rm fil} \Delta v}{l_{\rm fil}} \times \frac{1}{{\rm tan}(i)}$$

with $M_{\rm fil}$ and $l_{\rm fil}$ the mass and length of the filament, and $\Delta v$ the velocity difference from one end of the filament to the central core region. The masses $M_{\rm fil}$ can be estimated from the 1.3 mm continuum data assuming optically thin dust emission following (cite: hildebrand1983) or (cite: schuller2009). The factor $\frac{1}{{\rm tan}(i)}$ reflects the unknown inclination angle $i$ of the filamentary structures. (cite: wells2024) investigated the influence of this inclination uncertainty on the estimated flow rates, and they find a spread in the distribution of flow rates of roughly 1 order of magnitude at full-width-half maximum.

For the mass estimates, we assume a dust opacity $\kappa = 0.9$ cm$^2$g$^{-1}$ ((cite: ossenkopf1994), MRN dust at $10^6$ cm$^{-3}$ and 1.3 mm), a gas-to-dust mass ratio of 150 (cite: draine2003) and a temperature of 30 K (cite: urquhart2018). The velocity differences $\Delta v$ are measured from the DCN 1st moment map between the northern and southern ends of the filaments (marked by the ellipses in Figure [3](#ALMA-IMF) middle panel) with respect to the central velocity of $\sim -3.6$ km s$^{-1}$ ($v_{\rm LSR}$ from (cite: leurini2011)). The filament lengths $l_{\rm fil}$ are also measured along the main long axis of the ellipses in Fig. [3](#ALMA-IMF). Table [1](#flowrates) lists the parameters used for our estimates. While all individual parameters are associated with their own uncertainties, the dominating systematic uncertainty appears to be the unknown inclination angle (see above). Hence, the flow rates are associated with an uncertainty of roughly 1 order of magnitude.

|  |  |  |  |  |
|:---|---:|---:|---:|---:|
| Filament | $M_{\rm fil}$ | $\Delta v$ | $l_{\rm fil}$ | $\dot{M}$ |
|  | (M$_{\odot}$) | (km s$^{-1}$) | (1000 au) | (10$^{-3}$M$_{\odot}$ yr$^{-1}$) |
| North | 86 | 2.2 | 52 | 0.77 |
| South | 39 | 3.3 | 32 | 0.86 |

: Masses and flow rates

Using these parameters, we find mass flow rates close to 10$^{-3}$ M$_{\odot}$ yr$^{-1}$ over scales of $\sim$0.25 pc for both filamentary structures. These filaments are feeding a central region of roughly 10$^4$ au size that harbors at least 12 cores (Fig. [2](#continuum)). Hence, these flow rates should be considered as cluster-feeding gas flow rates. A recent N$_2$H$^+$ study of the region also found inflow signatures with inflow rates around $\sim$10$^{-3}$  M$_{\odot}$ yr$^{-1}$ (cite: sandoval-garrido2024), similar to our findings here. For comparison, absorption line measurements toward one of the central mm peak positions revealed central infall rates onto that specific source mm2 between $10^{-4}$ and $10^{-3}$ M$_{\odot}$ yr$^{-1}$ (cite: beuther2017b; beuther2019).

If protostellar growth continues on comparably long (free-fall) timescales, the gas feeding the cores must be replenished at the rate it falls into those cores. For the G351 region, we find that the accretion flow onto the central region is high enough to re-fill the reservoir feeding the central accreting protostars.

We can estimate the free-fall time-scale of the region from the single-dish ATLASGAL data. Using the mass and size of the region (Sect. [1](#intro)), following (cite: stahler2005), the free-fall time-scale of the region is $\sim1.6\times 10^5$ yrs. A steady accretion flow of $10^{-3}$ M$_{\odot}$ yr$^{-1}$ over that time allows to channel roughly 160 M$_{\odot}$ toward the central regions which is reasonable for forming high-mass stars within a few hundred thousand years (e.g., (cite: mckee2003)).

Comparing our results with infall and accretion flow studies of high-mass star-forming regions, other investigations typically found global infall rates or flow rates along filamentary structures in the regime of $10^{-4}$ to $10^{-3}$ M$_{\odot}$ yr$^{-1}$ (e.g., (cite: fuller2005; peretto2013; henshaw2014; wyrowski2016; chen2019; sandoval-garrido2024; wells2024)), which is consistent with our finding for G351. These high-mass star-forming region flow rates are also considerably higher than streamer flow rates found around low-mass regions (typically around $10^{-6}$ M$_{\odot}$ yr$^{-1}$, e.g., (cite: pineda2020; valdivia2022)).

One may also ask whether this parsec-scale accretion flow may be driven by local gravity or whether large-scale convergent gas flows may contribute? To really study large cloud-scale converging gas flows, one would need to investigate even larger-scale data of less dense and also atomic gas which is beyond the scope of this paper. However, on sub-parsec scales as discussed here and shown in Fig. [3](#ALMA-IMF), the red- and blue-shifted filamentary structures north and south of the central cores clearly converge toward these central structures. In that sense, one may call these converging filamentary gas streams. Nevertheless, our data do not allow us to differentiate whether these converging gas streams are caused soley by the gravitational potential of the region or whether externally driven converging gas flows may contribute to the picture.

![](zoom_h2co.pdf)

## Small-scale kinematics around the central cores

Moving to the smallest scales and the inner $\sim$10$^4$ au of this high-mass star-forming region, the high-spatial-resolution study by (cite: beuther2019) identified 12 mm-continuum emission peaks within this central area (top-right panel of Fig. [2](#continuum)). If one compares that high-resolution image to the lower-resolution configuration 5 image (top-left panel in Fig. [2](#continuum)), all these sources can be re-identified, just now embedded in a larger-scale, almost filamentary environment. The configuration 8 image (top-middle panel of Fig. [2](#continuum)) shows as expected a mixture of the two extremes. Finally, the jointly deconvolved combined image of all three configurations reveals the best of the "three worlds" (bottom-big panel of Fig. [2](#continuum)). At almost the same very high spatial resolution ($0.027''\times 0.022''$) as the configuration 10-only image, one now finds all the small-scale structures embedded in the filamentary environment of the parental gas clump. These data are an excellent example of the power of combining multi-configuration interferometry data into final images and datacubes.

Since we are interested here mainly in the kinematics of the region, the right panel of Fig. [3](#ALMA-IMF) shows the velocity structure of the region via a 1st moment map of the H$_2$CO$(3_{2,2}-2_{2,1})$ line which is one of the lines the DIHCA and high-resolution data have in common. This line has an upper energy level $E_u/k$ of 68 K with a critical density of $\sim 3\times 10^{6}$ cm$^{-3}$. Hence, it is a good tracer of the gas dynamics in the inner center of this star-formation complex.

Inspecting this 1st moment map, one clearly sees that blue- and red-shifted emission are found at the eastern and western side of the central region, consistent with the kinematics of the intermediate-scale filaments discussed previously (Sect. [3.2](#intermediate-scale) and Fig. [3](#ALMA-IMF)). However, in addition to the velocity structure at the eastern and western edges, one does not identify a smooth velocity gradient across but one gets the impression of almost a velocity oscillation across the region varying regularly between blue- and redshifted gas (Fig. [3](#ALMA-IMF) right panel).

To have a closer look at this velocity structure, Fig. [4](#pv_h2co) presents H$_2$CO$(3_{2,2}-2_{2,1})$ integrated intensity maps over selected velocity regimes, and a position-velocity (pv) diagram in the east-west direction across this central region (marked by an arrow in Fig. [3](#ALMA-IMF) right panel and Fig. [4](#pv_h2co) the 2nd from left panel). The three velocity regimes cover the important blue- and red-shifted parts as well as velocities in a transition regime between the blue- and red-shifted flow. One clearly sees that significant fractions of the blue- and red-shifted gas are located in the east and west of the region, respectively (left and 3rd panel from left in Fig. [4](#pv_h2co)), corresponding to the inflow zones discussed in the previous section from the intermediate-scale inflowing gas (Fig. [3](#ALMA-IMF)). The velocities closer to the $v_{\rm LSR}\sim -3.6$ km s$^{-1}$ show less preferred orientation (2nd panel in Fig. [4](#pv_h2co)). Nevertheless, the blue- and red-shifted emission is not found exclusively in the east and west but also more distributed over the region.

A different way to visualize that is the position-velocity diagram conducted along a cut from east to west (right panel in Fig. [4](#pv_h2co)). The pv-diagram clearly confirms the complex velocity structure, also showing that moment analysis can partly be misleading in complex kinematic environments. While the 1st moment map in Fig. [3](#ALMA-IMF) exhibits structure mainly between $-9$ and plus a few km s$^{-1}$, the position-velocity diagram reveals a much broader velocity spread from $<-15$ km s$^{-1}$ to $>+8$km s$^{-1}$. Consistent with the 1st moment and integrated velocity maps, the position-velocity diagram again shows that the gas at the eastern side is largely blue-shifted and at the western side largely red-shifted. Around the two central cores mm1 and mm2 (marked by the dashed lines in Fig. [4](#pv_h2co)), all velocities are found. This may partly also be due to the molecular outflow driven by mm1 in northwest-southeast direction (Fig. [3](#ALMA-IMF) middle panel, (cite: beuther2017b; beuther2019)). Regarding the velocity oscillation indicated by the 1st moment map, that is less well identified in the position velocity diagram (nor in the three integrated velocity maps). While the transition from blue-shifted gas at the eastern edge to red-shifted gas close to the central mm cores mm1 and mm2 is also evident in the position-velocity diagram, moving further west there is always red-shifted gas around 0 km s$^{-1}$. There is just an additional more blue-shifted gas component between $-5$ and $-14$ km s$^{-1}$ at offsets $-3.5''$ to $-4.0''$ in the pv-diagram that gets weaker again going further to the west (labeled "transition" in Fig. [4](#pv_h2co) right panel).

Therefore, the gas structure within the central $\sim$10$^4$ au contains blue- and red-shifted gas at the eastern and western edges, most likely associated with the intermediate-scale gas stream. However, going closer to the center, we cannot identify clear velocity structures or gradients leading to one or the other core. It rather appears that the central area contains several different gas structures that interact. This interacting dynamics can be caused by several processes, in particular the infalling filamentary and converging gas streams, and feedback processes of the forming protostars, specifically from the main central molecular outflow around mm1. In addition to this, other cores in the region may also drive outflows, we just have not clearly identified them yet. While some studies in the past revealed accelerated motions toward central cores (e.g., OMC-1, (cite: hacar2017)), the more oscillatory and chaotic velocity structure of the innermost region discussed here does not allow us to infer any potential acceleration.

# Conclusions and summary

Combining a unique multi-scale dataset from single-dish parsec-scale cloud coverage (MALT90) via intermediate-scale 0.25 pc interferometric mosaic observations (ALMA-IMF) to the smallest-scale $<1000$ au high-resolution ALMA data (DIHCA plus configuration 10 data), we can follow the gas flow from the infrared dark filament around the G351 star-forming region down to the innermost cores.

While the large-scale data are only indicative of a gas flow, the intermediate-scale ALMA-IMF data clearly reveal filamentary structures leading from the north and south toward the central core. The red- and blue-shifted velocities of the gas are consistent with those from the largest spatial scales, hence indicating that indeed the flow starts on several parsec scales and continues toward the center. Assuming that the velocity gradients are due to infalling filamentary gas structures, we can infer gas flow rates around $10^{-3}$ M$_{\odot}$ yr$^{-1}$, consistent also with literature infall and accretion flow studies (section [3.2](#intermediate-scale)). Such high infall rates are needed to form high-mass stars within a few 100.000 yrs (e.g., (cite: mckee2003; bonnell2007; hoare2007; tan2014; motte2018)). This infalling gas is feeding a central region of roughly 10$^4$ au size that hosts at least a dozen mm cores. Hence, the infall rates measured here correspond to the combined infall rates feeding all central cores and protostars. These rates are consistent with infall rates measured toward one of the central cores by absorption lines on the order $10^{-4}$ to $10^{-3}$ M$_{\odot}$ yr$^{-1}$.

Going toward the central $\sim$10$^4$ au of the region, our combined multi-configuration very-high-angular-resolution dataset ($0.027''\times 0.022''$ or 50 au resolution) reveals filamentary structures connecting the many cores identified previously. While the blue- and red-shifted gas at the edges of this central area agree well with the velocity structures of the intermediate-scale filaments, going toward the very center of the region, the kinematics become less ordered exhibiting often several velocity components, even at individual positions. We assign this more complex velocity structure in the center to an interplay of the converging infalling gas streams and at the same time feedback processes like molecular outflows from the central cores.

In summary, this multi-scale kinematic study of the prototypical infrared dark cloud and hot core region G351 reveals and quantifies the hierarchical gas flow from the large-scale cloud down to the innermost cores. While we find a relatively ordered converging gas flow from parsec down to 0.05 pc scale, the innermost region reveals more complex velocity structures, likely caused by the combination of the converging gas flow with feedback processes from the central protostars.

# Acknowledgements

We like to thank the referee for the insightful comments improving the quality of the paper. PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP22H01271 and JP23H01221) of JSPS. PS was supported by Yoshinori Ohsumi Fund (Yoshinori Ohsumi Award for Fundamental Research). FO acknowledges the support of the NAOJ ALMA Joint Scientific Research Program grant No. 2024-27B, and from the National Science and Technology Council (NSTC) of Taiwan grants NSTC 112-2112-M-007-041 and NSTC 112-2811-M-007-048. AG acknowledges support from the NSF under grants AAG 2008101 and CAREER 2142300.

67 natexlab

(ref: barnes2018) Barnes, A. T., Henshaw, J. D., Caselli, P., et al. 2018, MNRAS, 475, 5268

(ref: barnes2023) Barnes, A. T., Liu, J., Zhang, Q., et al. 2023, A&A, 675, A53

(ref: beuther2019) Beuther, H., Ahmadi, A., Mottram, J. C., et al. 2019, A&A, 621, A122

(ref: beuther2015b) Beuther, H., Ragan, S. E., Johnston, K., et al. 2015, A&A, 584, A67

(ref: beuther2017b) Beuther, H., Walsh, A. J., Johnston, K. G., et al. 2017, A&A, 603, A10

(ref: beuther2009c) Beuther, H., Walsh, A. J., & Longmore, S. N. 2009, ApJS, 184, 366

(ref: beuther2020) Beuther, H., Wang, Y., Soler, J., et al. 2020, A&A, 638, A44

(ref: bonfand2024) Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, A&A, 687, A163

(ref: bonnell2007) Bonnell, I. A., Larson, R. B., & Zinnecker, H. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 149–164

(ref: chen2019) Chen, H.-R. V., Zhang, Q., Wright, M. C. H., et al. 2019, ApJ, 875, 24

(ref: churchwell2009) Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, PASP, 121, 213

(ref: cunningham2023) Cunningham, N., Ginsburg, A., Galván-Madrid, R., et al. 2023, A&A, 678, A194

(ref: draine2003) Draine, B. T. 2003, ARA&A, 41, 241

(ref: egan1998) Egan, M. P., Shipman, R. F., Price, S. D., et al. 1998, ApJL, 494, L199

(ref: foster2011) Foster, J. B., Jackson, J. M., Barnes, P. J., et al. 2011, ApJS, 197, 25

(ref: foster2013) Foster, J. B., Rathborne, J. M., Sanhueza, P., et al. 2013, PASA, 30, e038

(ref: fuller2005) Fuller, G. A., Williams, S. J., & Sridharan, T. K. 2005, A&A, 442, 949

(ref: gieser2024) Gieser, C., Pineda, J. E., Segura-Cox, D. M., et al. 2024, A&A, 692, A55

(ref: ginsburg2022) Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022, A&A, 662, A9

(ref: hacar2017) Hacar, A., Alves, J., Tafalla, M., & Goicoechea, J. R. 2017, A&A, 602, L2

(ref: henshaw2014) Henshaw, J. D., Caselli, P., Fontani, F., Jiménez-Serra, I., & Tan, J. C. 2014, MNRAS, 440, 2860

(ref: henshaw2013) Henshaw, J. D., Caselli, P., Fontani, F., et al. 2013, MNRAS, 428, 3425

(ref: hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: hoare2007) Hoare, M. G., Kurtz, S. E., Lizano, S., Keto, E., & Hofner, P. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 181

(ref: ishihara2024) Ishihara, K., Sanhueza, P., Nakamura, F., et al. 2024, arXiv e-prints, arXiv:2407.06845

(ref: jackson2013) Jackson, J. M., Rathborne, J. M., Foster, J. B., et al. 2013, PASA, 30, e057

(ref: jackson2019) Jackson, J. M., Whitaker, J. S., Rathborne, J. M., et al. 2019, ApJ, 870, 5

(ref: kirk2013) Kirk, H., Myers, P. C., Bourke, T. L., et al. 2013, ApJ, 766, 115

(ref: klaassen2015) Klaassen, P. D., Johnston, K. G., Leurini, S., & Zapata, L. A. 2015, A&A, 575, A54

(ref: kueffmeier2024) Kuffmeier, M. 2024, Frontiers in Astronomy and Space Sciences, 11, 1403075

(ref: leurini2013) Leurini, S., Codella, C., Gusdorf, A., et al. 2013, A&A, 554, A35

(ref: leurini2011) Leurini, S., Codella, C., Zapata, L., et al. 2011a, A&A, 530, A12

(ref: leurini2009) Leurini, S., Codella, C., Zapata, L. A., et al. 2009, A&A, 507, 1443

(ref: leurini2011b) Leurini, S., Pillai, T., Stanke, T., et al. 2011b, A&A, 533, A85

(ref: li2024) Li, S., Sanhueza, P., Beuther, H., et al. 2024, Nature Astronomy, 8, 472

(ref: liu2015) Liu, H. B., Galván-Madrid, R., Jiménez-Serra, I., et al. 2015, ApJ, 804, 37

(ref: maud2017) Maud, L. T., Hoare, M. G., Galván-Madrid, R., et al. 2017, MNRAS, 467, L120

(ref: mckee2003) McKee, C. F. & Tan, J. C. 2003, ApJ, 585, 850

(ref: motte2022) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8

(ref: motte2018) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41

(ref: norris1993) Norris, R. P., Whiteoak, J. B., Caswell, J. L., Wieringa, M. H., & Gough, R. G. 1993, ApJ, 412, 222

(ref: olguin2023) Olguin, F. A., Sanhueza, P., Chen, H.-R. V., et al. 2023, ApJL, 959, L31

(ref: olguin2022) Olguin, F. A., Sanhueza, P., Ginsburg, A., et al. 2022, ApJ, 929, 68

(ref: olguin2021) Olguin, F. A., Sanhueza, P., Guzmán, A. E., et al. 2021, ApJ, 909, 199

(ref: ossenkopf1994) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: peretto2009) Peretto, N. & Fuller, G. A. 2009, A&A, 505, 405

(ref: peretto2014) Peretto, N., Fuller, G. A., André, P., et al. 2014, A&A, 561, A83

(ref: peretto2013) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, A112

(ref: pillai2006) Pillai, T., Wyrowski, F., Carey, S. J., & Menten, K. M. 2006, A&A, 450, 569

(ref: pineda2023) Pineda, J. E., Arzoumanian, D., Andre, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 233

(ref: pineda2020) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158

(ref: reyes2024) Reyes-Reyes, S. D., Stutz, A. M., Megeath, S. T., et al. 2024, MNRAS, 529, 2220

(ref: sandoval-garrido2024) Sandoval-Garrido, N. A., Stutz, A. M., Álvarez-Gutiérrez, R. H., et al. 2024, arXiv e-prints, arXiv:2410.09843

(ref: sanhueza2021) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10

(ref: sanhueza2012) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012, ApJ, 756, 60

(ref: schuller2009) Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415

(ref: stahler2005) Stahler, S. W. & Palla, F. 2005, The Formation of Stars (ISBN 3-527-40559-3. Wiley-VCH)

(ref: tan2014) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, Protostars and Planets VI, 149

(ref: taniguchi2023) Taniguchi, K., Sanhueza, P., Olguin, F. A., et al. 2023, ApJ, 950, 57

(ref: towner2024) Towner, A. P. M., Ginsburg, A., Dell’Ova, P., et al. 2024, ApJ, 960, 48

(ref: urquhart2018) Urquhart, J. S., König, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059

(ref: valdivia2022) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2022, A&A, 667, A12

(ref: valdivia2023) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2023, A&A, 677, A92

(ref: walsh1998) Walsh, A. J., Burton, M. G., Hyland, A. R., & Robinson, G. 1998, MNRAS, 301, 640

(ref: wells2024) Wells, M. R. A., Beuther, H., Molinari, S., et al. 2024, A&A, 690, A185

(ref: wu2003) Wu, J. & Evans, II, N. J. 2003, ApJL, 592, L79

(ref: wyrowski2016) Wyrowski, F., Güsten, R., Menten, K. M., et al. 2016, A&A, 585, A149

</paper>

Write the methods card for this paper.