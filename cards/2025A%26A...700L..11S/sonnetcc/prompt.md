# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...700L..11S\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...700L..11S",
 "title": "Stephenson 2 DFK 52: Discovery of an exotic red supergiant in the massive stellar cluster RSGC2",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Siebert, M. A.",
 "n_authors": 4,
 "arxiv_id": "2507.11609",
 "doi": "10.1051/0004-6361/202555975",
 "alma_projects_linked_by_archive": [
  "2023.1.01519.S",
  "2024.A.00018.S"
 ]
}
```

Paper text:
<paper>
# Stephenson 2 DFK 52: Discovery of an exotic red supergiant in the massive stellar cluster RSGC2

Atacama Large Millimeter/submillimeter Array (ALMA) observations at 1.3mm have recently revealed surprising complexity in the circumstellar environment of DFK 52, a red supergiant (RSG) located in the Stephenson 2 massive open cluster. We provide an initial characterisation of the star’s mass-loss properties by studying its circumstellar emission in continuum, $^{12}$CO, $^{13}$CO, and SiO rotational lines. We find that DFK 52 is surrounded by an extremely large outflow (up to 50,000 au in radius) that shows complex morphologies in both its molecular and dust emission. The size of the circumstellar medium is unprecedented, even when compared with other known extreme RSGs, and its lower luminosity indicates that its mass ejection mechanism may be unique among this population. The molecular emission can be partially reproduced by a two-component model consisting of a fast (27 km s$^{-1}$) detached equatorial component with $M{\sim}0.05$ $M_{\odot}$ and a slow (10 km s$^{-1}$) spherical envelope with $\dot{M}\sim3\times10^{-6}$ $M_{\odot}$ yr$^{-1}$. This suggests that DFK 52 underwent a dramatic mass-loss event $\sim$4000 years ago, but has since transitioned into having a slower more symmetric mass loss. We conservatively estimate a total mass of $0.1-1$ $M_{\odot}$ in the complex extended regions of the outflow. The uncertain nature of the dramatic mass loss warrants extensive follow-up of this likely supernova progenitor.

# Introduction

The mass loss of red supergiants (RSGs) is critical to their evolution and to the observed characteristics of Type II-p supernovae (SNe). The efficiency of these winds for the duration of the RSG phase can determine the amount of hydrogen stripped from the star, the density of interacting dust at the time of explosion, and the structure of SN remnants. Among well-studied RSGs, a morphological distinction has emerged between those exhibiting slower, traditional, approximately spherical mass loss (e.g. $\alpha$ Ori, $\alpha$ Sco; $10^{-7}-10^{-6}$$M_{\odot}$ yr$^{-1}$) and more luminous extreme RSGs, which show asymmetric outflows and mass-loss rates of order $10^{-4}$$M_{\odot}$ yr$^{-1}$(e.g. VY CMa, NML Cyg, VX Sgr). Neither the underlying physical mechanisms that produce these exotic objects nor their ubiquity among the red supergiant population is understood, despite their major relevance to evolutionary models of massive stars and core-collapse SNe.

Stephenson 2 (RSGC2) is a massive cluster of at least 26 RSGs located at the base of the Scutum-Crux spiral arm at a distance of $5.8^{+1.91}_{-0.76}$ kpc (cite: davies2007_rsgc2). It has been inferred that this was a site of recent starburst activity in the region where the arm intersects the galactic bulge. (cite: humphreys2020) investigated the mass-loss properties of cluster members from dust emission in their mid-infrared (IR) spectral energy distributions (SEDs), and noted its wide spread in luminosities, initial masses, and mass-loss rates when compared to other RSG clusters.

In these previous studies, the source DFK 52 appears as a rather ordinary RSG in the cluster. Its radial velocity and plane-of-sky position place it in the centre of RSGC2, the strength of its CO absorption band in the near-IR implies an M0-type supergiant (cite: davies2007_rsgc2), and its estimated luminosity ($2\times10^4$ $L_{\odot}$) is typical, though on the low end for RSGs. However, (cite: humphreys2020) noted that its $J$-band flux is too low to be reproduced with a stellar model and the average reddening factor for the cluster. This could either arise from variable line-of-sight extinction from the intervening interstellar medium (ISM), or from circumstellar dust.

In this letter we report the discovery of a surprising circumstellar environment toward DFK 52 based on recent observations with ALMA. Through its molecular line and continuum emission at millimetre wavelengths, we present the kinematics and spatial distribution of gas and dust surrounding this star, and compare them with other known extreme RSGs. With these constraints, we aim to provide starting insights into the evolutionary status and the mass-loss history of DFK 52 that will serve as a basis for future more detailed studies of this unique object.

# Observations

The millimetre-wavelength observations of DFK 52 were conducted as part of two ALMA programmes. The first (2023.1.01519.S) covered a sample of 13 RSGs in RSGC2. These observations were performed with two configurations of the main 12m array using the Band 6 receiver (cite: Ediss2004_Band6), achieving a spatial resolution of 0.35$''$ at 230 GHz and a maximum recoverable scale (MRS) of 12.5$''$. Four spectral windows were positioned in the $214-233$ GHz range targeting $^{12}$CO $J=2-1$ at 230.538 GHz and SiO $J=5-4$ at 215.596 GHz. The spectral resolution is 1.27 km s$^{-1}$, and the total bandwidth is 1.8 GHz. The follow-up project (2024.A.00018.S) targeted only DFK 52 with the Atacama Compact Array (ACA) to recover all of the extended emission. The spectral set-up for the ACA matches the resolution and line coverage of the 12m data, with the addition of the $^{13}$CO $J=2-1$ transition at 220.399 GHz.

Observations for both ALMA projects were reduced with the standard ALMA calibration pipeline (cite: Hunter2023_ALMApipeline), and visibilities from different configurations were combined in the *uv*-plane with antenna-specific weighting. Continuum subtraction was performed in the visibility plane, and imaging was done with the CASA task `tclean` using Briggs weighting and a robust parameter of 0.5. The final brightness sensitivities are 1 mJy/beam for spectral line data and 20 $\mu$Jy/beam for the continuum. A common feature across all ALMA observations of RSGC2 was a significant amount of contamination from the interstellar medium (ISM) in CO. To reduce its impact on our results, we identified the channels where ISM emission or absorption spatially overlaps with circumstellar CO, and did not consider them in our analysis. For continuum maps, line-free channels were used in the imaging process, and the $^{12}$CO spectral window was omitted entirely to ensure the ISM was excluded. Comparing images created with and without the supplementary ACA data, the total flux recovery is ${\sim}100$% for spectral lines and 80% for the continuum in the main-array dataset.

# Analysis and results

## Continuum

The 1.3 mm continuum toward DFK 52 is shown in Fig. [1](#fig:continuum). We observed emission in a variety of substructures, including a very low-brightness (${\sim}1$-$3\sigma$ unsmoothed) extended component that is elongated in the N–S direction and reaches a maximum radius of 8$''$. At shorter radii, more compact components are present, including two bright clumps in the NW and E directions (labelled A and B), and an arc structure to the SW (labelled C). Together, these structures account for ${\sim}$15% of the total flux. Notably, no centrally peaked continuum source is found at the position of the star (measured by unresolved SiO emission; Section [3.2](#sect:co)). The total continuum flux is $17.2\pm1.7$ mJy.

The continuum map appears similarly complex in shape to the extreme RSG VY CMa, where the millimetre emission is dominated by thermal radiation from asymmetrically ejected dust clumps (cite: kaminski_vycma_2019). However, the surrounding VY CMa are observed at projected distances of $250-800$ au (cite: Humphreys2024_VYCMa_clumps), whereas the A and B clumps around DFK 52 are found at $5,800$ and $12,000$ au, and the extended emission reaches a distance of $\sim50,000$ au (assuming the cluster distance of 5.8 kpc; see Appendix [9](#app:membership)). Following the methods of (cite: ogorman2015) and (cite: debeck2025_nmlcyg) for VY CMa and NML Cyg and using a dust grain emissivity of $\beta=0.9$, we derive dust temperatures $T_{\mathrm{A}}\approx102\pm9$ K, $T_{\mathrm{B}}\approx76\pm7$ K, and $T_{\mathrm{C}}\approx63\pm6$ K, and dust mass estimates $M_{\mathrm{A}}\approx(1.7\pm0.36)\times10^{-4}\,M_{\odot}$, $M_{\mathrm{B}}\approx(1.1\pm0.24)\times10^{-4}\,M_{\odot}$, and $M_{\mathrm{C}}\approx(4.4\pm0.95)\times10^{-4}\,M_{\odot}$. This assumes that the A, B, and C continuum components are situated at offsets of $\Delta_{\mathrm{A}}\approx1.0^{\prime\prime}$, $\Delta_{\mathrm{B}}\approx2.1^{\prime\prime}$, and $\Delta_{\mathrm{C}}\approx3.2^{\prime\prime}$ in the plane of the sky and that their emission is optically thin. These masses are comparable to the estimates for continuum dust clumps around VY CMa, which have $M\sim10^{-4}$ $M_{\odot}$(cite: Humphreys_2022).

![](DFK52_continuum_a.png)

Adding to the peculiarity of the continuum map, the spectral energy distribution (SED) shows a clear double-peaked shape (Appendix [4](#fig:sed)). This is different from VY CMa and NML Cyg, whose SEDs exhibit much higher fluxes in the mid-IR contributed by significantly warmer dust found close to the star (cite: kaminski_vycma_2019; Justtanont1996_NMLCyg). Considering the large physical scales in the ALMA image, the secondary peak in the SED, and the lack of mid-IR excess or millimetre emission at the stellar position, we suggest that the dust emission is dominated by a cold detached component. Using the same method as before, but for the total ALMA flux, and adopting an average dust temperature of 50 K (inferred from the far-IR SED peak). This gives $M_{\mathrm{d}}\approx(6.6\pm0.7)\times10^{-3}\,M_{\odot}$, or a total envelope mass of $1.3$ $M_{\odot}$ if a gas-to-dust ratio of 200 is assumed (cite: humphreys2020).

## Molecular emission

The spatial and kinematic morphology of rotational line emission seen toward DFK 52 is summarised in Fig. [2](#fig:morph_summary). We briefly present a number of important features.

- SiO $J=5-4$ is spatially unresolved, and parabolic in line shape. This is consistent with optically thick thermal emission at the stellar position, as is measured toward many AGB and RSG stars. From this, we measure the systemic velocity $v_{sys}=109\pm1.2$ km s$^{-1}$ and stellar position $\alpha_{\mathrm{J2000}}=18\mathrm{h}39\mathrm{m}23.406\mathrm{s}$, $\delta_{\mathrm{J2000}}=-06^{\circ}02'16.12''$.

- With a maximum radius of $\sim$7.5$''$, the integrated $^{12}$CO emission is significantly more extended than SiO. Moreover, the CO line width of $\Delta v_{10\%}\approx54$ km s$^{-1}$ traces gas that moves $\sim$2.5 times faster than SiO ($\Delta v_{10\%}\approx20$ km s$^{-1}$).

- The CO morphology is highly asymmetric, containing numerous arcs, loops, and roughly linear components. We identify a bar-like structure extending along position angle $\mathrm{PA}=143^{\circ}$ and across the stellar position. No local maximum is measured at the stellar position.

- The size and orientation of the integrated CO emission are in quite good agreement with the extended continuum. The C component is traced well by $^{12}$CO channel maps in the velocity range $130-138$ km s$^{-1}$, while the southward continuum extension is seen in the range $92.5-98$ km s$^{-1}$(Appendix [10](#app:chmaps)).

- Despite these correlations, the A and B dust clumps have no counterparts in CO. This may result from the missing channels contaminated by the ISM. We also find that some CO flux extends beyond the scales of the diffuse dust emission.

- The physical radial extent of $^{12}$CO $J=2-1$ structures is 45,000 au. This is roughly four times larger than the farthest components observed in this line for VY CMa (cite: singh2023) and NML Cyg (cite: debeck2025_nmlcyg).

Though no simple geometric prescriptions can explain the overall structure, the bar-like component in the integrated CO map (Fig. [\[fig:co_mom0\]](#fig:co_mom0)) shows a significant amount of coherence across velocity space. Figure [3](#fig:model_summary) shows the position-velocity (PV) diagram for $^{12}$CO taken along the bar, where a shell shape is clearly seen extending to $v_{\mathrm{sys}}\pm27$ km s$^{-1}$. This pattern suggests that the bar represents a detached disk-like structure viewed edge-on. The PV diagram also shows a bright smaller component with a total velocity width of $\sim$20 km s$^{-1}$, consistent with the SiO $J=5-4$ emission. This inner structure is also seen in a perpendicular cut, suggesting that it has more 3D extent than the bar.

To estimate their physical properties, we reproduced the two components outlined above using the radiative transfer (RT) software LIne Modeling Engine (LIME 1.9.5) (cite: Brinch2010_LIME). The model parametrises the two structures as a slow spherically symmetric present-day mass loss, and a faster detached equatorial density enhancement (EDE) viewed edge-on (Appendix [7](#app:lime)). A model with an equatorial mass of 0.05 $M_{\odot}$ centred at $r=4$$''$  (4000 yr age) and a central component with $\dot{M}=3\times10^{-6}$ $M_{\odot}$ yr$^{-1}$ is successful at reproducing the average surface brightness and radial distribution of emission both in the compact and extended regions along the position angle of the bar structure (Fig. [3](#fig:model_summary)). Furthermore, the derived mass-loss rate for the slow component is in agreement with the SED modelling of warm dust performed by (cite: humphreys2020). However, some shortcomings of the model are clear as well. First, the blueshifted side of the torus emission is largely missing from the observational data. No combination of optical depth and excitation conditions could reproduce this, so we conclude that there is an azimuthal density asymmetry in this structure. Furthermore, there is a substantial amount of CO emission between the two components that is not captured by the model.

Because the LIME model was constructed to fit only a small fraction of the observed outflow at a specific position angle, it reproduces 15% of the total line flux. Although the extended emission outside the position angle of the bar is extremely complex, we note that its velocity distribution is still quite similar to the EDE component (Appendix [7](#app:lime)). If we assume the excitation conditions of CO are common between the many extended density structures, then the model can be scaled to provide a very rough estimate of the cumulative mass in the detached high-velocity components surrounding DFK 52. Doing so offers a total mass of ${\sim}$0.35 $M_{\odot}$, which is within a factor of four agreement with the estimate obtained from the continuum flux in Section [3.1](#sect:cont).

![](DFK_52_12CO_SiO_pv143.png)

# Discussion

DFK 52 is a puzzling object for several reasons. The estimated physical extent of its molecular envelope is a factor of $3-4$ larger than the outflows of VY CMa and NML Cyg(cite: singh2023; debeck2025_nmlcyg), and many of the irregular geometries have no clear analogues in any observed evolved star. At the same time, the luminosity is a factor of 10 lower than the known extreme RSGs (cite: humphreys2020), and its present-day mass loss is estimated to be two orders of magnitude smaller. We find that both the molecular line and continuum emission require a significant mass of cold material at large radii ($>10^{17}$ cm) in the form of complex detached structures.

Given the high stellar density in the RSGC2 cluster and the strong ISM contamination in these observations, it is possible that the large-scale emission represents interactions between a stellar outflow and a quiescent local density structure in the intra-cluster medium. The maximum physical extent of the envelope is comparable to the smallest observed galactic clumps (cite: Uruquhart2021_ISM_ATLASGAL), and the smooth underlying continuum emission is more similar in size and shape to molecular cloud substructures than circumstellar envelopes (cite: Tokuda2019_LMC_filaments). However, comparison of the $^{13}$CO and $^{12}$CO emission across the high signal-to-noise ratio channels free of ISM contamination leads to $^{12}$CO/$^{13}$CO$\approx5$ (Fig. [\[fig:co_sio_spectra\]](#fig:co_sio_spectra)). This low ratio supports a stellar origin of the presented molecular emission as it requires stellar processing through the H-burning via the CNO cycle and dredge-up of the material to the surface (cite: Boothroyd1993_HBB). We also note that none of the other sources in the RSGC2 sample show morphology anywhere similar to this, supporting the idea that the morphological complexity is connected to the star rather than to a complex intra-cluster component.

To explain the light curves of Type II SNe, it has been suggested that RSGs explode into a very dense immediate circumstellar medium (CSM), built up by a superwind ($>10^{-3}$ $M_{\odot}$ yr$^{-1}$) in the $\sim$100 years prior to core collapse (cite: Moriya2017_RSGsuperwinds; davies2022). The CO emission around DFK 52 indicates that a period of dramatic mass loss with $\dot{M}>10^{-4}$ $M_{\odot}$ yr$^{-1}$ occurred $\sim4000$ years ago. If we assume constant radial expansion for the disk component in the RT model, this portion of the CSM would have had a peak gas density of $n\sim10^{10}$cm$^{-3}$, or $\rho\sim10^{-14}$g cm$^{-3}$ when it was at a distance of $10^{14}$ cm from DFK 52, which is comparable to the pre-SN CSM density required by (cite: Yaron2017_SN2013fs), for example. However, our analysis also suggests that this period was immediately followed by an ongoing slower mass loss with $\dot{M}\sim3\times10^{-6}$ $M_{\odot}$ yr$^{-1}$, and that the central gas density is lower at present. Therefore, if DFK 52 did experience a superwind, it ended without producing a SN.

Alternatively, an energetic interaction in a binary or multiple system could have contributed to the ejection of the extended material. Companion interactions and stellar mergers are known to produce bipolar, multipolar, equatorial, and complex morphologies (cite: Lagadec2011_pAGB_mIRimaging; olofsson2019; Kaminski2018_rnovae_submm), and common envelope evolution (CEE) is now considered to be widely responsible for rapid mass-loss events observed in AGB and post-AGB sources (cite: Khouri2021_CEEs). Furthermore, CEE in RSG systems has been invoked as an important channel to the progenitors of ultra-stripped SNe, as well as the compact binaries ($P<1$ day) responsible for gravitational wave events (cite: Wei2024_RSG_CEEmodels; Klencki2021_RSG_BH_CE). CE ejections are known to produce expanding equatorial rings similar to the partial one seen in DFK 52(cite: Gomez2018_I15103), but given the lack of bipolar symmetry and the absence of any high-velocity jet components ($>30$ km s$^{-1}$), this assignment cannot be made with the current observations. We still consider a multiple-star hypothesis to be strong here, as DFK 52’s comparably low luminosity would have required an additional source of energy to drive the massive detached components (Appendix [8](#app:momentum)).

# Conclusion

We have presented resolved emission from the circumstellar environment of the red supergiant DFK 52, revealing a dusty envelope spanning unprecedented physical scales. Both the continuum and CO imply the presence of a massive ($0.1\sim1$ $M_{\odot}$) asymmetric, equatorially enhanced, detached wind expanding at $v\approx27$ km s$^{-1}$. Additionally, compact emission near the stellar position implies that the mass-loss rate and expansion velocity have dropped significantly since the ejection of this component. With the available data, a full classification of DFK 52 and its history is not yet feasible; however, we consider a short-lived superwind period or an energetic companion interaction to be strong possibilities that explain the circumstellar structure. The exotic nature of DFK 52 makes it a useful candidate to study major mass-loss events that can occur during the RSG phase, so we emphasise the need for future multi-wavelength studies of this object.

# Acknowledgements

We thank the reviewer for their helpful comments on this letter. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2023.1.01519, ADS/JAO.ALMA#2024.A.00018.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We gratefully acknowledge the use of Director’s Discretionary Time at ALMA under project ADS/JAO.ALMA#2024.A.00018.S. G.Q. would like to thank funding support from Spanish Ministerio de Ciencia, Innovación, y Universidades through grant PID2023-147545NB-I00.

32 natexlab

(ref: Boothroyd1993_HBB) Boothroyd, A. I., Sackmann, I. J., & Ahern, S. C. 1993, ApJ, 416, 762

(ref: Brinch2010_LIME) Brinch, C. & Hogerheijde, M. R. 2010, A&A, 523, A25

(ref: val2001) Bujarrabal, V., Castro-Carrizo, A., Alcolea, J., & Sánchez Contreras, C. 2001, A&A, 377, 868

(ref: davies2007_rsgc2) Davies, B., Figer, D. F., Kudritzki, R.-P., et al. 2007, ApJ, 671, 781

(ref: davies2022) Davies, B., Plez, B., & Petrault, M. 2022, MNRAS, 517, 1483

(ref: debeck2025_nmlcyg) De Beck, E., Andrews, H., Quintana-Lacaci, G., & Vlemmings, W. H. T. 2025, A&A, 698, A179

(ref: Ediss2004_Band6) Ediss, G. A., Carter, M., Cheng, J., et al. 2004, in Fifteenth International Symposium on Space Terahertz Technology, ed. G. Narayanan, 181–188

(ref: Gomez2018_I15103) Gómez, J. F., Niccolini, G., Suárez, O., et al. 2018, MNRAS, 480, 4991

(ref: GonzalezFernandez2012_RSGC3) González-Fernández, C. & Negueruela, I. 2012, A&A, 539, A100

(ref: humphreys2020) Humphreys, R. M., Helmel, G., Jones, T. J., & Gordon, M. S. 2020, AJ, 160, 145

(ref: Humphreys_2022) Humphreys, R. M. & Jones, T. J. 2022, AJ, 163, 103

(ref: Humphreys2024_VYCMa_clumps) Humphreys, R. M., Richards, A. M. S., Davidson, K., et al. 2024, AJ, 167, 94

(ref: Hunter2023_ALMApipeline) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, PASP, 135, 074501

(ref: Justtanont1996_NMLCyg) Justtanont, K., de Jong, T., Helmich, F. P., et al. 1996, A&A, 315, L217

(ref: kaminski_vycma_2019) Kamiński, T. 2019, A&A, 627, A114

(ref: Kaminski2018_rnovae_submm) Kamiński, T., Steffen, W., Tylenda, R., et al. 2018, A&A, 617, A129

(ref: Khouri2021_CEEs) Khouri, T., Vlemmings, W. H. T., Tafoya, D., et al. 2021, Nature Astronomy, 6, 275

(ref: Klencki2021_RSG_BH_CE) Klencki, J., Nelemans, G., Istrate, A. G., & Chruslinska, M. 2021, A&A, 645, A54

(ref: Lagadec2011_pAGB_mIRimaging) Lagadec, E., Verhoelst, T., Mékarnia, D., et al. 2011, MNRAS, 417, 32

(ref: Marton2024_PACS_PSC) Marton, G., Gezer, I., Madarász, M., et al. 2024, A&A, 688, A203

(ref: Moriya2017_RSGsuperwinds) Moriya, T. J., Yoon, S.-C., Gräfener, G., & Blinnikov, S. I. 2017, MNRAS, 469, L108

(ref: negueruela2012) Negueruela, I., Marco, A., González-Fernández, C., et al. 2012, A&A, 547, A15

(ref: ogorman2015) O’Gorman, E., Vlemmings, W., Richards, A. M. S., et al. 2015, A&A, 573, L1

(ref: olofsson2019) Olofsson, H., Khouri, T., Maercker, M., et al. 2019, A&A, 623, A153

(ref: Sahai2022_VHya) Sahai, R., Huang, P. S., Scibelli, S., et al. 2022, ApJ, 929, 59

(ref: schneider2020_merger) Schneider, F. R. N., Ohlmann, S. T., Podsiadlowski, P., et al. 2020, MNRAS, 495, 2796

(ref: singh2023) Singh, A. P., Richards, A. M. S., Humphreys, R. M., Decin, L., & Ziurys, L. M. 2023, ApJL, 954, L1

(ref: Tokuda2019_LMC_filaments) Tokuda, K., Fukui, Y., Harada, R., et al. 2019, ApJ, 886, 15

(ref: Uruquhart2021_ISM_ATLASGAL) Urquhart, J. S., Figura, C., Cross, J. R., et al. 2021, MNRAS, 500, 3050

(ref: Wei2024_RSG_CEEmodels) Wei, D., Schneider, F. R. N., Podsiadlowski, P., et al. 2024, A&A, 688, A87

(ref: Yaron2017_SN2013fs) Yaron, O., Perley, D. A., Gal-Yam, A., et al. 2017, Nature Physics, 13, 510

(ref: Zapartas2025_Mdot_RSGmodels) Zapartas, E., de Wit, S., Antoniadis, K., et al. 2025, A&A, 697, A167

# Spectral energy distribution

We added the new ALMA 1.3 mm continuum flux and archival measurements from the Herschel/PACS point source catalogue (cite: Marton2024_PACS_PSC) to the photometry compiled by (cite: humphreys2020) to construct the SED for DFK 52 shown in (Fig. [4](#fig:sed)). This reveals a double-peaked shape, with a cold dust component maximum at $\sim70\,\mu$m, yielding a temperature of $\sim50$ K. Although the spectral indices of the individual continuum components are unavailable with the current ALMA observations, a linear interpolation from the total ALMA flux to the PACS 120 $\mu$m yields an estimate of $\alpha\approx3$, implying optically thin dust grains (cite: ogorman2015) and supporting this assumption made in our dust estimates in Section [3.1](#sect:cont).

![](DFK52_continuum_b.png)

# Details of the 3D radiative transfer model

In the two-component LIME model, the central component is treated as a spherically symmetric expanding wind with constant mass-loss rate. The extended component, similar to the set-up of (cite: Sahai2022_VHya), is modelled as an equatorial density enhancement (EDE) described as a 2D Gaussian in (spherical) radius and the $z$-coordinate: $$\begin{equation}
        n(r,z) \propto \exp\left(\frac{-\left(r-r_{\mathrm{EDE}}\right)^2}{2\sigma_{\mathrm{EDE}}^2}\right)\times\exp\left(\frac{-z^2}{2h^2}\right).
    
\end{equation}$$ Here $r_{\mathrm{EDE}}$ is the radius where the density peaks, $\sigma_{\mathrm{EDE}}$ is the standard deviation of the enhancement, and the vertical scale height $h$ is determined by the cylindrical radius coordinate $R$ and an opening angle, $\theta_{\mathrm{EDE}}$: $$\begin{equation}
        h(R) = R\tan\left(\theta_{\mathrm{EDE}}/2\right).
    
\end{equation}$$ The temperature profile for both structures is a power law in radius with log-slope $\alpha=1$, based on the stellar temperature and radius. A minimum kinetic temperature, $T_{\mathrm{min}}=15$ K, is also needed because this power law reaches unphysically low values at large radii where the torus is found.

Due to the very different radial density dependences of the two components, populations were simulated separately using $\log r$ grid-sampling for the central component, and uniform sampling for the equatorial component. The excitation is collisionally dominated, and the observations indicate that the components do not overlap spatially at any velocity, so we do not expect the central and equatorial components to interfere with each other in optical depth or rotational populations. The parameters of the final RT model are included in Table [1](#tab:lime_params).

A comparison between the observed and modelled normalised line profile shapes is shown in Fig. [5](#fig:lime_speccomp). We find that the fast EDE component and slow central component scale quite well to the total emission. While this suggests that material outside the equatorial regions may be comparable in its velocity distribution and optical depth properties, a full 3D model of the extended material is not yet possible due to the very high degree of geometrical complexity.

| Parameter | Value |
|:---|:--:|
| $^{12}$CO abundance w.r.t. H$_2$ | $2\times10^{-4}$ |
| Stellar temperature, $T_\star$ | 3800 K $^a$ |
| Stellar luminosity, $L_\star$ | $2.4\times10^{4}$ $L_{\odot}$$^a$ |
| Temperature, $T_{\mathrm{kin}}$ | $T_\star\left(\frac{r}{R_\star}\right)^{-\alpha}$ |
| **Central component** |  |
| Mass-loss rate, $\dot{M}$ | $3\times10^{-6}$ $M_{\odot}$ yr$^{-1}$ |
| Expansion velocity, $v_{\mathrm{sph}}$ | $10$ km s$^{-1}$ |
| **Equatorial component** |  |
| Total mass, $M_{\mathrm{EDE}}$ | 0.05 $M_{\odot}$ |
| Expansion velocity, $v_{\mathrm{EDE}}$ | 27 km s$^{-1}$ |
| Center radius, $r_{\mathrm{EDE}}$ | 23000 au |
| Radial width, $\sigma_{\mathrm{EDE}}$ | 6000 au |
| Opening angle, $\theta_{\mathrm{EDE}}$ | 10$^{\circ}$ |
|  |  |

: Physical parameters of the two-component RT model. $^a$Adapted from (cite: humphreys2020).

![](co_2-1_modelscaled_spectrum.png)

# Equatorial momentum analysis

The linear momentum estimated for the equatorial outflow, based on the derived parameters (see Table [1](#tab:lime_params)), is approximately $2.7 \times 10^{38}\,\mathrm{g\,cm\,s^{-1}}$. To evaluate whether radiation pressure could account for this value, we computed the momentum it can deliver over the acceleration timescale using the formulation by (cite: val2001), $P = F \cdot P_{\mathrm{rad}} = F \cdot L \cdot t_{\mathrm{acc}} / c$, where the efficiency factor $F$ describes the ability of dust to absorb and re-emit photons multiple times, enhancing momentum transfer. Assuming the current luminosity of $2 \times 10^4\,L_\odot$ and an acceleration time of 1000 years—which corresponds to the duration of the ejection of the EDE—the resulting radiative momentum is $P_{\mathrm{rad}} \approx 8.05 \times 10^{37}\,\mathrm{g\,cm\,s^{-1}}$ and the implied efficiency factor is $F \approx 3.35$.

In oxygen-rich massive post-AGB stars, the efficiency of momentum transfer from radiation pressure to the circumstellar gas is expected to be lower than in carbon-rich environments. This is primarily due to the reduced formation of carbonaceous dust grains, which are highly efficient at absorbing stellar radiation. Instead, oxygen-rich stars predominantly form silicate-based dust, which has lower opacity in the infrared, and thus couples less effectively with the radiation field. In environments with lower dust-to-gas ratios or less efficient dust species, this process is less effective and thus leads to reduced values of $F$. Additionally, in equatorial outflows, the geometry further limits the fraction of stellar radiation that can be redirected into the plane of the flow, so the $F$ calculated above for DFK 52 must be considered a lower limit. As a rough estimate, for a torus height of 4000 au ($\approx 10^{\circ}$) and a radius of 23000 au, the EDE could intercept only about 9% of the total stellar radiation.

(cite: val2001) scaled the value of the effective opacity with the mass loss; their value of $F$ is expected for mass losses of $\sim 10^{-4}$$M_{\odot}$ yr$^{-1}$. The average mass loss we obtained for the EDE is $\sim 5 \times 10^{-5}$$M_{\odot}$ yr$^{-1}$(=0.05$M_{\odot}$/1000 yr). Thus, if we expect only 9% of the total of the photons to reach the region of the EDE and a $\tau_\mathrm{eff}\,\sim 5$ times lower, we should reach (even assuming the same dust characteristics) a value of *F* of $9-17 \times 10^{-2}$, significantly smaller than the minimum efficiency derived. This supports the conclusion that an alternate ejection mechanism must be invoked to explain the formation of the EDE observed. If the equatorial component was indeed accelerated by radiation pressure, the stellar luminosity would have had to be 1–2 orders of magnitude higher than it is estimated now. Such a dramatic drop in luminosity over a timescale of a few $10^3$ yr is not consistent with any predictions of single-star RSG evolutionary models (cite: Zapartas2025_Mdot_RSGmodels); it is, however, consistent with the timescales and stellar parameter changes modelled for some merger products (cite: schneider2020_merger).

# Cluster membership

The interpretation of these data is reliant on the assumption that DFK 52 is a cluster member, and hence at the cluster distance of $5.8^{+1.91}_{-0.76}$ kpc (cite: davies2007_rsgc2). If DFK 52 were in the background, its luminosity could be more in line with other extreme RSGs, but the size of the gas and dust emitting regions would cover even larger spatial scales than currently derived, further complicating the question of how such an envelope can be formed. On the other hand, if DFK 52 were in the foreground, the physical scales of emission would decrease; however, its luminosity would be even lower than currently quoted, challenging the star’s classification as an RSG. In this case, the star would have a much later spectral type, due to the empirical relationship between $T_{\mathrm{eff}}$ and CO band head strength for non-supergiants (cite: GonzalezFernandez2012_RSGC3; davies2007_rsgc2), and because the corrected SED would be substantially more reddened (cite: negueruela2012). A very evolved foreground AGB star could be considered, but even at a distance of 1.5 kpc (where the envelope size would be comparable to VY CMa), the luminosity would then be small even for AGBs ($<2000$ $L_{\odot}$). The systemic velocity ($109$ km/s; measured with SiO) also lies comfortably within the cluster velocity range ($100-120$ km/s), and would be quite peculiar for a $d<2$ kpc star, as the galactic rotation curve in this sight line predicts $v_{\mathrm{lsr}}<30$km s$^{-1}$ in that case. For these reasons, we argue for the current assignment that DFK 52 is indeed a cluster member, but a more accurate distance measurement is needed to confirm this.

# $^{12}$CO channel maps

![](DFK52_chmaps_all_appendix.png)

The individual channel maps for $^{12}$CO are shown in Fig. [6](#fig:co_chmaps). We find that emission on the redshifted side of the line is characterised by two prominent bubble-like shapes extending in the NE and SW directions, as well as the bar structure discussed in Sect. [3.2](#sect:co). In contrast, the blueshifted emission is more irregular, showing both smooth components as well as southward filamentary structures that do not converge to the stellar position at the highest relative velocities. Near the stellar velocity, the compact CO component appears, and we see bright emission from three confined clumps located at a radial distance of 1$''$ (5800 au) from the stellar position.

</paper>

Write the methods card for this paper.