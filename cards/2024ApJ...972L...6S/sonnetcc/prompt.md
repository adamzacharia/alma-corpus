# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...972L...6S\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...972L...6S",
 "title": "Magnetic Fields in Massive Star-forming Regions (MagMaR): Unveiling an Hourglass Magnetic Field in G333.46─0.16 Using ALMA",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Saha, Piyali",
 "n_authors": 36,
 "arxiv_id": "2407.16654",
 "doi": "10.3847/2041-8213/ad660c",
 "alma_projects_linked_by_archive": [
  "2013.1.00960.S",
  "2017.1.00101.S",
  "2018.1.00105.S"
 ]
}
```

Paper text:
<paper>
# Magnetic Fields in Massive Star-forming Regions (MagMaR): Unveiling an Hourglass Magnetic Field in G333.46$-$0.16 using ALMA

## Abstract

The contribution of the magnetic field to the formation of high-mass stars is poorly understood. We report the high-angular resolution ($\sim0.3^{\prime\prime}$, 870 au) map of the magnetic field projected on the plane of the sky (B$_{\mathrm{pos}}$) towards the high-mass star forming region G333.46$-$0.16 (G333), obtained with the Atacama Large Millimeter/submillimeter Array (ALMA) at 1.2 mm as part of the Magnetic Fields in Massive Star-forming Regions (MagMaR) survey. The B$_{\mathrm{pos}}$ morphology found in this region is consistent with a canonical “hourglass” which suggest a dynamically important field. This region is fragmented into two protostars separated by $\sim1740$ au. Interestingly, by analysing H$^{13}$CO$^{+}$ ($J=3-2$) line emission, we find no velocity gradient over the extend of the continuum which is consistent with a strong field. We model the B$_{\mathrm{pos}}$, obtaining a marginally supercritical mass-to-flux ratio of 1.43, suggesting a initially strongly magnetized environment. Based on the Davis–Chandrasekhar–Fermi method, the magnetic field strength towards G333 is estimated to be $5.7$ mG.

The absence of strong rotation and outflows towards the central region of G333 suggests strong magnetic braking, consistent with a highly magnetized environment. Our study shows that despite being a strong regulator, the magnetic energy fails to prevent the process of fragmentation, as revealed by the formation of the two protostars in the central region.

# Introduction

Star formation is a complex process controlled by several factors, among which gravity, turbulence, and magnetic field play a key role. Magnetic fields are believed to oppose the gravitational contraction and fragmentation of dense cores, thus delaying the formation of protostars (cite: 1999ASIC..540..305M; 2007ARA&A..45..565M; 2017NatAs...1E.158L; 2021ApJ...912..159P; 2022ApJ...941...51H). However, magnetic fields can also help to channel cloud material towards overdense regions, thus acting as a catalyst in the formation of protostars (cite: 2017A&A...607A...2S; 2019FrASS...6....5H).

In a strongly magnetic environment, the morphology of the magnetic field remains preserved up to scales of dense molecular cores of $0.01-0.1$ pc (cite: 2014ApJ...794L..18Q; 2015Natur.520..518L; 2021ApJ...923..204C). Another possible scenario shows the dragging of the frozen-in magnetic field along with the gas material towards the dense core by the gravitational collapse. This phenomenon creates a pinching effect in the magnetic field lines, leading to an “hourglass"-like appearance (cite: 2006Sci...313..812G; 2009Sci...324.1408G; 2009ApJ...707..921R; 2009ApJ...700..251T; 2013ApJ...769L..15S; 2014ApJS..213...13H; 2014ApJ...794L..18Q; 2018MNRAS.477.2760M; 2018ApJ...855...39K; 2019A&A...630A..54B; 2019ApJ...879...25K; 2021ApJ...923..204C; 2024ApJ...963L..31H). This specific structure may be partially due to projection and line-of-sight integration effects that lead to the observed dust polarization. It is of utmost importance to characterize hourglass patterns when observed, in order to better understand the initial conditions of star formation.

Despite being a significant regulator of star formation, the role of the magnetic field during the birth of massive stars is still poorly understood.

To make progress, a survey Magnetic fields in Massive star-forming Regions (MagMaR) has been carried out. In MagMaR, a total of 30 high-mass star-forming regions were observed at 1.2 mm with the Atacama Large Millimeter/ submillimeter Array (ALMA). A few detailed characteristics of some targets, such as G5.89$-$0.39, IRAS 18089$-$1732, and NGC 6334I(N), have been discussed by (cite: 2021ApJ...913...29F), (cite: 2021ApJ...915L..10S), and (cite: 2021ApJ...923..204C), respectively.

Out of the 30 targets, the magnetic field projected on the plane of the sky (B$_\mathrm{POS}$) towards the high-mass star-forming region G333.46$-$0.16 (hereafter, G333) shows the most extended hourglass morphology on a few 1000 au scale (cite: 2019A&A...631A..72L). This target was studied as a part of the ATLASGAL survey of massive clumps by (cite: 2014A&A...565A..75C) and (cite: 2019A&A...631A..72L). The bolometric luminosity of this target is of 4.4$\times$10$^{3}$ L$_{\odot}$ (cite: 2019A&A...631A..72L). Based on its spectral energy distribution, (cite: 2019A&A...631A..72L) estimated a dust temperature and mass of 25.2 K and 282 M$_{\odot}$, respectively for this region. Here, we aim to assess magnetic properties and to investigate the importance of the magnetic field, gravity and turbulence in the star-forming region G333.

![](G333.46-0.16_posangle_debias.pdf)

# Observations

ALMA polarimetric observations towards G333 were carried out on 2018 September 27 using ALMA Band 6 (1.2 mm) as a part of the MagMaR project (Project ID: 2017.1.00101.S and 2018.1.00105.S; PI: P. Sanhueza). The maximum recoverable scale (MRS) was $\sim4.5^{\prime\prime}$. During the observing runs, J1650-5044 was used as phase calibrator while J1427-4206 was used as a calibrator for bandpass, flux, and polarization. Details of the observational setup are discussed by (cite: 2021ApJ...913...29F), (cite: 2021ApJ...915L..10S), and (cite: 2021ApJ...923..204C).

Linearly polarized dust continuum emission is identified within the the inner one-third area of the primary beam (24$^{\prime\prime}$). Bright emission lines have been eliminated from the Stokes $I$ continuum following the method elaborated by (cite: 2021ApJ...909..199O). We used CASA 6.5.2 to perform self-calibration and imaging. Self-calibration of the Stokes $I$ was performed with three iterations in phase with a final solution interval of 10 seconds. The self-calibration solutions were applied to the respective spectral cubes. The imaging of each Stokes parameter was performed separately employing the CASA task *tclean* using Briggs weighting with a robust parameter of 1. The resulting Stokes $I$ image has an angular resolution of 0.318$^{\prime\prime}\times0.290^{\prime\prime}$ with a position angle of 49.4$^{\circ}$ (922$\times$841 au). The sensitivities of the images are 160 $\mu$Jy beam$^{-1}$ for the final Stokes $I$, and 29 $\mu$Jy beam$^{-1}$ for the final Stokes $Q$, and $U$. The source is bright in continuum Stokes $I$ emission making the image dynamic range limited. However, the polarized emission (Stokes $Q$ and $U$) is significantly weaker compared to the continuum Stokes $I$ and therefore, it is unlikely to be dynamic range limited, making them possible to reach the thermal noise. The debiased linear polarized intensity, polarization fraction and polarization angle images were constructed following (cite: 2006PASP..118.1340V).

The image of H$^{13}$CO$^{+} (J=3-2)$ line emission, also included in the spectral setup, was obtained by the automatic masking method *yclean* (cite: 2018ApJ...861...14C). The CASA task *tclean* was performed using Briggs weighting with a robust parameter of 1, leading to a noise level of 2.9 mJy beam$^{-1}$ (0.61 K) per 0.56 km s$^{-1}$ channel.

# Results

The ALMA 1.2 mm continuum emission with $\sim900$ au spatial resolution is shown in Figure [1](#fig:bpos) a and reveals details of the internal structure of G333. The dust continuum emission shows a flattened structure that is elongated in the northwest-southeast direction. The center of this flattened structure is fragmented into two more condensations with a separation of $\sim1740$ au along the major axis of the elongation. Both the condensations show presence of hot molecular core emission lines (cite: 2023ApJ...950...57T), suggesting that they are potential protostars. The peak flux at the position of the brightest component, located towards the south-east (MM1), is $53.5$ mJy beam$^{-1}$, while the fainter one located towards the north-west (MM2) has a peak flux of $38.8$ mJy beam$^{-1}$.

The direction of the B$_{\mathrm{pos}}$  is inferred by assuming the dust grains are aligned with respect to the magnetic fields (cite: 1982MNRAS.200.1169C; 1984ApJ...284L..51H; 1988QJRAS..29..327H; 2000ASPC..215...69L; 2015ARA&A..53..501A). The polarized emission detected in G333 suggests an hourglass-like geometry of the magnetic field aligned with the symmetry axis of the hourglass almost parallel to the minor axis of the flattened envelope. For our analysis, we focus on the circular area as marked in Figure [1](#fig:bpos) (a), that harbours the hourglass magnetic field. We chose this area to avoid the additional distortion of B$_{\mathrm{pos}}$ produced by other surrounding cores. The circle is centered at $\alpha=16:21:20.183$ and $\delta=-50:09:46.662$, with a radius of $1.5^{\prime\prime}$ (4350 au). As the diameter of the area of analysis ($3^{\prime\prime}$) is less than the MRS, the extended emission should not be significantly affected by filtering.

Being a cold dense gas tracer (upper energy level, $E_{u}$ of 25 K), the spatial distribution of H$^{13}$CO$^{+} (J=3-2)$ line emission towards G333 appears to be similar to that of the dust continuum emission (see Figure [2](#fig:mom_maps) a). Figure [2](#fig:mom_maps) (b) shows the H$^{13}$CO$^{+}$ distribution of the intensity-weighted velocity structure (moment 1 map) towards G333 with respect to the systemic velocity ($v_\mathrm{lsr}\sim-43$ km s$^{-1}$). No clear signature of large-scale velocity gradient is detected with a spectral resolution of 0.56 km s$^{-1}$, suggesting a quiescent environment at $\sim10000$ au scale. However, the velocity field over MM1 and MM2 is relatively more blueshifted than their immediate vicinities, which could be a sign of infall as suggested by (cite: 2019A&A...626A..84E) and (cite: 2021ApJ...909..199O).

![](mom0_spw1_H13CO_G333.46_1.png)

# Discussion

## Dust continuum emission and velocity dispersion

The flux density enclosed in the circular region is 493 mJy. The temperature of the region marked with a circle as in Figure [1](#fig:bpos), is determined using the CH$_{3}$CN ($J=14-13$) rotational transitions. We detected primarily 4 brightest K components (K = 0, 1, 2, 3) of the transition towards this area. We avoided the region very close to MM1 and MM2 to refrain the line contamination by radiation from MM1 and MM2. In Figure [4](#fig:ch3cn_temp), we present the average brightness distribution of the CH$_{3}$CN ($J=14-13$) transitions in black. The blue dashed line represents the fitted spectrum that is obtained by fitting the observed spectrum with XCLASS (cite: 2017A&A...598A...7M) resulting in a temperature of 50 K. Using this temperature, and assuming optically thin dust emission and a spherical geometry, the total gas mass is estimated using: $$\begin{equation}
    M=\Lambda\frac{F_{\nu}D^{2}}{\kappa_{\nu}B_{\nu}(T)}
\end{equation}$$ where $\Lambda$ is the gas-to-dust mass ratio, $F_{\nu}$ is the flux density of the source, $D$ is the distance to the target, $\kappa_{\nu}$ is the dust opacity per gram of dust, and $B_{\nu}$ is the Planck function with a dust temperature T. The gas-to-dust ratio is assumed to be 100:1. The dust opacity is assumed as 1.03 cm$^{2}$g$^{-1}$ (cite: 1994A&A...291..943O). Using a dust temperature of 50 K, the total mass is estimated as 23 M$_{\odot}$.

We estimate the mass density $\rho$ as $3.9\times10^{-17}$ gm cm$^{-3}$, using a volume ($V=\frac{4}{3}\pi R^{3}$, where, $R=1.5^{\prime\prime}$). The number density $n(\rm H_{2})$ is $\rho/\mu_{\rm H_{2}}m_{\rm H}$, where $\mu_{\rm H_{2}}(=2.86)$ is the mean molecular weight per hydrogen molecule (cite: 2013MNRAS.432.1424K) and $m_{\rm H}$ is the atomic mass of hydrogen. The $n(\rm H_{2})$ enclosed in the area of analysis is estimated as $8.4\times10^{6}$ cm$^{-3}$.

Using the *dendogram* technique (cite: 2008ApJ...679.1338R) adopted in the *astrodendro* Python package [^1], the flux densities of MM1 and MM2 are estimated as 59.5 mJy and 25.8 mJy, respectively. Assuming the similar temperature, MM1 is 2.3 times more massive than MM2. Table [1](#tab:dedro) lists the *dendogram* results for both protostars.

Considering a bolometric luminosity of $4.4\times10^{3}$ L$_{\odot}$ (cite: 2019A&A...631A..72L), and assuming that a single main-sequence star is responsible for the bolometric luminosity, the stellar mass would then be $\sim6$ M$_{\odot}$ (cite: 2011ApJ...730L..33M). However, there are two protostars at the center. At larger scale, based on the ALMA 7m array observations with an angular resolution of $3.7^{\prime\prime}$ (cite: 2017A&A...600L..10C), the mass of the structure containing MM1 and MM2 is determined as 120 M$_{\odot}$, suggesting that most of the clump mass (282 M$_{\odot}$) is concentrated in the central region of the clump. Thus, these protostars are potential candidates to becoming high-mass stars by accreting gas material from the available mass reservoir.

Using H$^{13}$CO$^{+}$ line emission, we derive the dispersion in the turbulent velocity along the line of sight, $\sigma v_\mathrm{los}(=\sqrt{\sigma_{\rm obs}^{2}-\sigma_{th}^{2}})$. The $\sigma_{\rm obs}$ and $\sigma_{th}$ are the total observed and thermal velocity dispersions, respectively. The $\sigma_{th}$ can be expressed as $\sqrt{k_{B}T/\mu m_{\rm H}}$, where $k_{B}$ is the Boltzmann constant, $\mu$ is the mean molecular weight per free particle (30). Assuming a temperature of 50 K, $\sigma_{th}$ and $\sigma v_\mathrm{los}$ are estimated as 0.12 and 1.21 km s$^{-1}$, respectively.

## Modeling of the hourglass-shaped magnetic field

In order to model the magnetic field pattern, we used the *DustPol* module included in the ARTIST package (cite: 2012A&A...543A..16P), which is based on the Line Modeling Engine (LIME) radiative transfer code (cite: 2010A&A...523A..25B). *DustPol* generates the synthetic Stokes $I$, $Q$, and $U$ images in FITS-format, which are used as an input for the *simobserve* and *simanalyze* tasks of CASA, considering the same antenna configuration of the observing runs in ALMA. In this way, polarization position angle maps are created and compared with the observations. The physical modeling of the 3D magnetic field is done by combining an axisymmetric singular toroid threaded by a poloidal field (cite: 1996ApJ...472..211L; 2011A&A...530A.109P). Based on (cite: 2013A&A...560A.114P), we added a toroidal force-free component of the magnetic field to represent the effects of rotation.

The model used in this work has four free parameters: (1) the mass-to-flux ratio normalized to its critical value, $\lambda$, defined as, $$\begin{equation}
    \lambda=\frac{(M/\Phi_{B})}{(M/\Phi_{B})_{cr}}=2\pi\sqrt{G}\frac{M}{\Phi_{B}}
    \label{eq:lambda}
\end{equation}$$ where $G$ is the gravitational constant, $\Phi_{B}$ is the magnetic flux ($=\pi R^{2}B$), and $M$ is the mass of the core; (2) the ratio of the strengths of the toroidal and the poloidal components of the magnetic field in the midplane of the source, $b_{0}$; (3) the orientation of the magnetic axis projected on the plane of sky, $\varphi$, starting from north and increasing eastward; (4) the inclination with respect to the plane of the sky, $i$, with an assumption to be positive/negative when the magnetic field in the northern part directs towards/away from us. A $\chi^{2}$-test is performed on the polarization angle residuals $(\Delta\psi)$ of the polarization angle $\psi$, obtained from the difference between the observed ($\psi_{\rm obs}$) and the modeled ($\psi_{\rm mod}$) polarization angles ($\Delta\psi=\psi_{\rm obs}-\psi_{\rm mod}$), enclosed within the circular area for each combination of the four free parameters. The $\chi^{2}$ is estimated accounting for regions lying above the 3$\sigma$ level ($\sigma=29 \mu$Jy beam$^{-1}$) of Stokes $Q$ and $U$ images. A constant temperature (50 K) has been adopted in the modelling as no temperature map of this region is available currently. On the other way, the region close to MM1 and MM2, is expected to be relatively hot and having more weight in estimating the Stokes parameters.

The best-fit model provides the minimum reduced $\chi^{2}$ value of 9.39 with the combination of model parameters: $\lambda=1.63$, $b_{0}=-0.1\pm0.1$, $i=45^{\circ+13^{\circ}}_{-6^{\circ}}$, and $\varphi=40^{\circ+1^{\circ}}_{-4^{\circ}}$. The errors are estimated following (cite: 1976ApJ...208..177L). A low value of $b_{0}$ in the best-fit model is consistent with no apparent rotation towards G333 as found in H$^{13}$CO$^{+}$. The value of $\lambda=1.63$ obtained from the model (see Equation [\[eq:lambda\]](#eq:lambda)) is relative to the mass enclosed in a flux tube, but observationally the mass is derived considering a spherical system. Therefore, the estimated $\lambda$ is transformed to an effective $\lambda$ of 1.43 (cite: 1996ApJ...472..211L), which is marginally supercritical.

![](G333_bestmodel_H125_i45_v3_paper.png)

![](G333_singlehistogram.png)

In Figure [3](#fig:bpos_fit) (a), we show a comparison between the observed and modeled magnetic field geometry, limited to the area within the circle shown in Figure [1](#fig:bpos) (a). Although the hourglass model reproduces quite well the observed magnetic field geometry, deviations can be seen around MM1, mainly towards its southern and eastern regions. Since MM1 is relatively more massive than MM2, it is possible that the gravity of MM1 might have dragged and distorted the magnetic field lines more effectively than MM2. In Figure [3](#fig:bpos_fit) (b), we show the histogram of the $\Delta\psi$. A Gaussian fit to the whole distribution of $\Delta\psi$ provides a mean value $\textless\Delta\psi\textgreater = -3.32^{\circ}$ and a standard deviation $\sigma_{\psi}=19.48^{\circ}$.

## Magnetic field strength

We estimate B$_\mathrm{POS}$ towards G333 using the well-known Davis–Chandrasekhar–Fermi (DCF) method (cite: 1951PhRv...81..890D; 1953ApJ...118..113C)[^2], which states: $$\begin{equation}
    B_\mathrm{POS} = Q\sqrt{4\pi\rho} \frac{\sigma v_\mathrm{los}}{\delta\psi_{int}}
\end{equation}$$ where Q is a correction factor, 0.5,[^3] adopted from simulations in turbulent clouds (cite: 2001ApJ...546..980O), $\rho$ is the mass density of the cloud, $\sigma v_\mathrm{los}$ is the dispersion in the turbulent velocity along the line of sight, and $\delta\psi_{int}$ is the intrinsic dispersion in the polarization angle $\psi$. The $\delta\psi_{int}$ can be obtained from $\sqrt{\sigma_{\psi}^{2}-\delta\psi_{\rm obs}^{2}}$. The average uncertainty in the observed $\psi$ within the circle of analysis is $\delta\psi_{\rm obs}=5.4^{\circ}$. The $\delta\psi_{int}$ obtained is $18.7^{\circ}$. Consequently, $B_\mathrm{pos}$ is estimated as 4.0 mG. Adopting $i=45^{\circ}$ from our model, we also estimate the total magnetic field strength $B=B_\mathrm{pos}/\mathrm{cos}~(i)=5.7$ mG. With a density of n(H$_{2})=8.4\times10^{6}$ cm$^{-3}$ this strength is consistent as found in the compilation of B-field strength with density by (cite: 2022ApJ...925...30L) using the DCF method.

The DCF method assumes the deviation of uniform magnetic field by turbulent gas motions, without considering gravity, which is most likely responsible for the hourglass shape. In this work gravity is taken into account while using the *dustPol* model and by considering the $\Delta\psi$, we eliminate the gravitational effect and the $\delta\psi$ is supposed to be the interplay between the turbulence and the magnetic field.

While computing $\lambda$ using Equation [\[eq:lambda\]](#eq:lambda), we assumed that all the mass is in the envelope, while the protostellar mass should also be added to the envelope mass. Therefore, the estimated $\lambda$ should be considered as a lower limit. As mentioned in [4.1](#subsec:mass), based on the luminosity, an additional stellar mass of $\sim6$ M$_{\odot}$ could be added to the envelope mass, making the total mass of 29 M$_{\odot}$, which leads to a mass-to-flux ratio of 1.22. The fact that the dust emission may be optically thick at the very central bright fragmented region, leads to underestimate the mass of the circular region can not be ignored. However, the estimated value of $\lambda$ is similar to the one obtained from the modelling (1.43).

We compute the Alfv$\mathrm{\acute{e}}$n speed $v_{\rm A}=B/\sqrt{4\pi\rho}=2.58$ km s$^{-1}$, through which we estimate the turbulent to magnetic energy $\beta_{t}=3(\sigma v_\mathrm{los}/v_{\rm A})^{2}=0.66$. This indicates that the magnetic energy dominates moderately over the turbulent energy in this region. Thus the magnetic field towards G333, in spite of being quite strong, could not prevent the fragmentation and eventually star formation.

Based on a non-ideal magnetohydrodynamic simulations of an initially subcritical core by (cite: 2020MNRAS.494..827M), the collapse happens after the core reaches a marginally supercritical mass-to-flux ratio, leaving behind a considerable amount of magnetic flux, which helps to transport out the angular momentum through strong magnetic braking. As a result, the protostar may harbour no disc or a very small one, with a very weak outflow signature. In G333, we do not find any evidence of rotation in the envelope region (Figure [2](#fig:mom_maps) b), nor in any of the protostars at the current angular resolution. Even in higher angular resolution ($\sim0.05^{"}$) observations of the same region obtained as part of the Digging into the Interior of Hot Cores with the ALMA (cite: 2022ApJ...929...68O; 2023ApJ...959L..31O; 2023ApJ...950...57T) survey (P. Sanhueza, private communication), no clear signature of rotation was found in any of the protostars, making the argument of strong magnetic braking more evident. Additionally, we found no significant outflow signature coming from the two protostars in G333 (see appendix [6](#app:mol_outflow)). This is consistent with overall physical scenario of very weak outflow and no disk when starting with strongly magnetized initial conditions (cite: 2020MNRAS.494..827M). This leads to the possibility that star formation in G333 started in an initially subcritical or transcritical cloud.

## Analysis of the Energy Balance

The current dynamical state towards G333 can be inferred from the virial parameter ($\alpha_\mathrm{vir}$), the ratio of the virial mass ($M_\mathrm{vir}$) to the total mass ($M$) of the system with considerations of both the turbulent and magnetic supports. While $\alpha_\mathrm{vir}\sim1$ indicates the equilibrium state, $\alpha_\mathrm{vir}\textgreater1$ implies expansion and conversely $\alpha_\mathrm{vir}\textless1$ signifies contraction under gravity. We estimate $\alpha_\mathrm{vir}$ as $1.3$ for a centrally peaked density profile (see Appendix [7](#app:virial_param)). This suggests that G333 is currently close to a quasi-equilibrium state or undergoing quasi-static evolution, which is further supported by the quiescent environment of G333 as implied by the velocity field traced by the H$^{13}$CO$^{+}$ line emission (Figure [2](#fig:mom_maps) b). A strongly magnetized environment exerts an adequate support against rapid gravitational collapse, although the magnetic field could not hinder the fragmentation. This is consistent with a second stage of fragmentation within an initial massive core that forms out of a transcritical cloud (cite: 2014ApJ...780...40B).

## Flattened envelope harbouring the hourglass magnetic field

Theoretical studies suggests that for a relatively strong magnetic field environment ($\lambda\leq3$), the core material is channeled primarily along the magnetic field lines by the gravitational pull, building a flattened pancake-like structure perpendicular to the field lines, and developing a small toroidal component of the magnetic field (cite: 2003ApJ...599..363A; 2007MNRAS.377...77P). As shown in Figure [1](#fig:bpos), the flattened structure where the fragmentation took place agrees well with the strong magnetic field case, which is further supported by a low $\lambda$ obtained from our best-fit model as well as the observations. Additionally a small contribution of the toroidal component of the field ($\sim10\%$ of the poloidal component) obtained from the best-fit model supports this phenomenon. This is consistent with some previous studies (cite: 2014ApJ...794L..18Q; 2019A&A...630A..54B; 2019ApJ...879...25K), which suggest a major contribution of magnetic field in the formation of high-mass protostars.

## Stability analysis of the central protostars

To investigate whether the central protostars MM1 and MM2 are gravitationally bound, we followed the methodology adopted in (cite: 2015Natur.518..213P) and (cite: 2024NatAs...8..472L). We estimate the gravitational potential energy ($V_{i}$) by\
$$\begin{equation}
    V_{i}=-\sum_{i\neq j} \frac{Gm_{i}m_{j}}{r_{ij}}
\end{equation}$$ where $m_{i}$ and $m_{j}$ are the masses of objects $i$ and $j$, respectively, and $r_{ij}$ is the separation between them. The kinetic energy ($E_{i}$) is given by, $$\begin{equation}
    E_{i}=\frac{1}{2}m_{i}(v_{i}-v_{com})^{2}
\end{equation}$$ where $v_{i}$ is the line-of-sight velocity of the object $i$, and $v_{com}$ is the velocity of the centre of mass of the system. We estimate $v_{com}$ by $$\begin{equation}
    v_{com}=\frac{\sum_{k}{m_{k}v_{k}}}{\sum_{k}{m_{k}}}
\end{equation}$$

The velocities of MM1 and MM2 are obtained from (cite: 2023ApJ...950...57T) as $-44.06$ and $-43.55$ km s$^{-1}$, respectively. Assuming that the measured velocity difference between MM1 and MM2 is in 1-D, the full velocity difference in 3-D is $\Delta v_{3D}=\sqrt{3}({v_{i}-v_{com}})$ along the line-of-sight. Also, the total separation between MM1 and MM2 is estimated by multiplying the measured projected separation (1740 au) with $4/\pi$, i.e., 2215 au, assuming a random orientation between them.

We measured the masses of MM1 and MM2 from the flux density obtained from the *astrodendro* task to estimate the $E_{i}/V_{i}$ for each of them. The $E_{i}/V_{i}$ for MM1 and MM2 are estimated as 0.08 and 0.17, respectively. As both MM1 and MM2 show $E_{i}/V_{i}\textless1$, they could be gravitationally bound in a binary system at the present stage.\
\

# Summary and Conclusions

The ALMA high-angular resolution ($\sim0.3^{\prime\prime}$) observations of linearly polarized 1.2 mm dust emission towards the high-mass star-forming region G333.46$-$0.16 revealed an hourglass-shaped pattern of B$_\mathrm{pos}$ at a scale of $\sim6000$ au. The hourglass shape is found to be more pinched towards MM1 than MM2, which might be because of the larger mass of MM1 compared to MM2. The protostars MM1 and MM2 are found to be gravitationally bound in a binary system at present with a separation of $1740$ au.

The H$^{13}$CO$^{+}$ line emission shows no strong velocity gradient that could hint any rotation towards G333. Also, none of the protostars show any clear signature of outflows, suggesting a strong magnetic braking.

The hourglass-shaped B$_{\mathrm{pos}}$  is well fitted with an axisymmetric semi-analytical magnetostatic model. The best fit model is primarily governed by a poloidal component tangled with a small toroidal component ($\sim10\%$ of the poloidal one). The best fit results also provide $\lambda=1.43$, $i=45^{\circ+13^{\circ}}_{-6^{\circ}}$ and $\phi=40^{\circ+1^{\circ}}_{-4^{\circ}}$.

Based on the DCF relation, the total magnetic field strength is estimated as $5.7$ mG. We also estimate the mass-to-flux ratio using the dispersion of polarization angle obtained from the model fitting, which results in $1.22$, consistent with same obtained from the best fit model ($\lambda=1.43$).

Our analysis of energy balance in this area suggests a quasi-equilibrium state, which is consistent with the current dynamic environment inferred by H$^{13}$CO$^{+}$ line emission. Our speculation based on this work is that the magnetic field towards G333 is strong enough to stabilize the environment towards the center. A low magnitude of turbulent-to-magnetic energy ratio indicates a suppression of the magnetic field over the turbulence in this region. However, both are ultimately overwhelmed by the gravity, responsible for the fragmentation and eventually star formation. This leads to a possible scenario that the star formation in G333 might have started in an initially subcritical core, when the very central peak density area reached the marginally supercritical mass-to-flux ratio.

We thank the anonymous referee for providing constructive suggestions which enriched the draft significantly. P.S. was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI numbers JP22H01271 and JP24K17100) of the Japan Society for the Promotion of Science (JSPS). P.S. was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Numbers JP22H01271 and JP23H01221) of the JSPS. J.M.G., acknowledges support by grant PID2020-117710GB-I00 (MCI-AEI-FEDER, UE). This work is also partially supported by the program Unidad de Excelencia María de Maeztu CEX2020-001058-M. J.L. is partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP23H01221) of JSPS. A.S.-M. acknowledges support from the RyC2021-032892-I grant funded by MCIN/AEI/10.13039/501100011033 and by the European Union ‘Next GenerationEU’/PRTR, as well as the program Unidad de Excelencia María de Maeztu CEX2020-001058-M, and support from the PID2020-117710GB-I00 (MCI-AEI-FEDER, UE). M.T.B. acknowledges financial support through the INAF Large Grant *The role of MAGnetic fields in MAssive star formation* (MAGMA). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00101.S. K.P. is a Royal Society University Research Fellow, supported by grant number URF$\setminus$R1$\setminus$211322. XL acknowledges support from the National Key R&D Program of China (No. 2022YFA1603101), the Natural Science Foundation of Shanghai (No. 23ZR1482100), the National Natural Science Foundation of China (NSFC) through grant Nos. 12273090 & 12322305, and the Chinese Academy of Sciences (CAS) ‘Light of West China’ Program (No. xbzgzdsys-202212). T.Cs. has received financial support from the French State in the framework of the IdEx Université de Bordeaux Investments for the future Program. Y.C. was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI number JP24K17103) of the JSPS. This paper makes use of the following ALMA data: ADS/JAO. Data analysis was \[in part\] carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research made use of astrodendro, a Python package to compute dendrograms of Astronomical data (<http://www.dendrograms.org/>).

ALMA

# Software

CASA (cite: 2007ASPC..376..127M; 2022PASP..134k4501C)

![](temp_map.png)

+:-----------:+:------------:+:----------------------------------------:+:-----------------:+:------------:+
| R.A.        | Dec.         | FWHM                                     | Peak Intensity    | Flux Density |
+-------------+--------------+------------------------------------------+-------------------+--------------+
| (ICRS)      | (ICRS)       | $(^{\prime\prime}\times^{\prime\prime})$ | (mJy beam$^{-1}$) | (mJy)        |
+-------------+--------------+------------------------------------------+-------------------+--------------+
| MM1                                                                                                      |
+-------------+--------------+------------------------------------------+-------------------+--------------+
| 16:21:20.20 | -50:09:46.91 | $0.31\times0.21$                         | 53.5              | 59.5         |
+-------------+--------------+------------------------------------------+-------------------+--------------+
| MM2                                                                                                      |
+-------------+--------------+------------------------------------------+-------------------+--------------+
| 16:21:20.17 | -50:09:46.41 | $0.23\times0.14$                         | 38.8              | 25.8         |
+-------------+--------------+------------------------------------------+-------------------+--------------+

: Results obtained from *astrodendro*$^{*}$

$^{*}$ $F_{min}=5\sigma$: the threshold above which the structures are defined.\
$\delta=1\sigma$: the minimum significance for separation of the structures.\
$S_{min}=$half of the beamsize: the minimum area to be allocated in the individual structure.

# Molecular outflows identified around G333

![](outflow_G333.46_test.png)

Several molecular outflows are identified around G333 using the $^{12}$CO ($J=3-2$) line emission observed by ALMA (Project ID: 2013.1.00960.S, PI: T. Csengeri). Using the CASA task *imregrid*, we match the phase-center of the $^{12}$CO line image and our 1.2 mm dust continuum image.

Figure [5](#fig:outflow) shows the $^{12}$CO molecular outflows overplotted on the dust continuum image. The $^{12}$CO line emission is integrated from $-106.1$ to $-65.3$ km s$^{-1}$ for the blueshifted lobe, and $-22.1$ to $0.7$ km s$^{-1}$ for the redshifted lobe. The sensitivities of the integrated images of the blueshifted and redshifted $^{12}$CO line emission are 0.14 and 0.10 Jy beam$^{-1}$, respectively. The outflow lobes in the north and south of the region enclosed by the hourglass-shaped magnetic field (shown as a cyan colored circle in Figure [5](#fig:outflow)) are highly collimated. Interestingly, it is noticeable that although there is a significant amount of redshifted $^{12}$CO line emission within the circle (which seems to be the redshifted lobe of the nearby dense core located south to the circular area of analysis), none of the outflow lobes is driven by any of the protostars but likely the low-mass protostars residing outskirts of the dense gas. There are some dust condensations that likely could host these protostars, marked with ‘X’ symbols in Figure [5](#fig:outflow).

The absence of outflows in any of the protostars makes it difficult to predict the of angular momentum direction. In a classical scenario of magnetized star formation, the angular momentum is efficiently lost by magnetic braking (cite: 1979ApJ...230..204M). Our speculation is that magnetic braking is relatively strong in the case of G333, because of which we do not find any observational signature of strong angular momentum.

# Virial parameter

The virial theorem can be expressed as below: $$\begin{equation}
    \frac{1}{2}\frac{d^{2}I}{dt^{2}}=2E_{k}+E_{G}+E_{B}
\end{equation}$$ where $I$ is the moment of inertia, $E_{k}$, $E_{G}$, and $E_{B}$ are the kinetic, gravitational, and magnetic energy, respectively. We consider a spherical cloud having a radial density profile $\rho\propto r^{-\alpha}$, where $\alpha=2$ imply the density profile to be centrally peaked (cite: 2013EAS....62...25B). The gravitational energy ($E_{G}$) can be expressed by: $$\begin{equation}
    E_{G} = -\frac{(3-\alpha)}{(5-2\alpha)}\frac{GM^{2}}{R}
\end{equation}$$ The magnetic energy ($E_{B}$) is given by: $$\begin{equation}
    E_{B} = \frac{B^{2}V}{8\pi}
\end{equation}$$

The kinetic energy ($E_{k}$) is derived by: $$\begin{equation}
    E_{k} = -\frac{3}{2}M\sigma_{\rm obs}^{2}
\end{equation}$$ The rotational energy ($E_{r}$) is expressed as: $$\begin{equation}
    E_{r} = \frac{1}{3}Mv_{\rm rot}^{2}\frac{(3-\alpha)}{(5-\alpha)}
\end{equation}$$ We do not find any evidence of rotation with a spectral resolution 0.56 km s$^{-1}$ in the area of analysis. If we assume this resolution as the upper limit of the velocity due to rotation ($v_{\rm rot}$), we estimate the ratio $E_{rot}/E_{G}$ to be 0.006 for a centrally peak density profile. With the same assumption of rotation, a ratio of $E_{rot}/E_{B}$ is estimated to be 0.013 for the same profile. Similarly, we estimate the ratio of $E_{rot}/E_{k}$ as 0.014. As the contribution of the rotational energy is negligible compared to the other energies, we do not account the upper limit of rotational term in the estimation of virial parameter.

Including both the kinetic and magnetic energies, a system can be in stable phase, when $2E_{k}+E_{B}+E_{G}\textless0$. The ratio between the virial mass $M_\mathrm{vir} (=M_{k+B})$ and the total mass $M$ can be defined as the virial parameter $\alpha_\mathrm{vir}$. Following (cite: 2020ApJ...895..142L), $\alpha_\mathrm{vir}$ is given below: $$\begin{equation}
    \alpha_\mathrm{vir} = \frac{M_\mathrm{k+B}}{M}=\frac{1}{M}\Biggr[\sqrt{M_\mathrm{B}^{2}+\Biggl(\frac{M_\mathrm{k}^{2}}{2}}\Biggr)+\frac{M_\mathrm{k}}{2}\Biggl]
\end{equation}$$ where $M_\mathrm{k+B}$ is the total virial mass considering the kinetic motion and magnetic field. The kinetic virial mass $M_\mathrm{k}$ is defined as, $$\begin{equation}
    M_\mathrm{k} = 3\Biggl(\frac{5-2\alpha}{3-\alpha}\Biggr)\frac{\sigma_\mathrm{los}^{2}R}{G}
\end{equation}$$\
\
The virial mass accounting for the ordered magnetic field $M_\mathrm{B}$ is expressed as: $$\begin{equation}
    
    M_\mathrm{B} = \frac{\pi R^{2}B}{\sqrt{\frac{6(3-\alpha)}{(5-2\alpha)}\pi^{2} G}}    
\end{equation}$$

We estimate the $\alpha_\mathrm{vir}$ to be $1.3$, which suggests an equilibrium state of G333, implying that magnetic field provides a significant support against gravity.

natexlab

(ref: 2003ApJ...599..363A) Allen, A., Li, Z.-Y., & Shu, F. H. 2003, ApJ, 599, 363, doi: [`10.1086/379243`](http://doi.org/10.1086/379243)

(ref: 2015ARA&A..53..501A) Andersson, B. G., Lazarian, A., & Vaillancourt, J. E. 2015, ARA&A, 53, 501, doi: [`10.1146/annurev-astro-082214-122414`](http://doi.org/10.1146/annurev-astro-082214-122414)

(ref: 2014ApJ...780...40B) Bailey, N. D., & Basu, S. 2014, ApJ, 780, 40, doi: [`10.1088/0004-637X/780/1/40`](http://doi.org/10.1088/0004-637X/780/1/40)

(ref: 2013EAS....62...25B) Belloche, A. 2013, in EAS Publications Series, Vol. 62, EAS Publications Series, ed. P. Hennebelle & C. Charbonnel, 25–66, doi: [`10.1051/eas/1362002`](http://doi.org/10.1051/eas/1362002)

(ref: 2019A&A...630A..54B) Beltrán, M. T., Padovani, M., Girart, J. M., et al. 2019, A&A, 630, A54, doi: [`10.1051/0004-6361/201935701`](http://doi.org/10.1051/0004-6361/201935701)

(ref: 2010A&A...523A..25B) Brinch, C., & Hogerheijde, M. R. 2010, A&A, 523, A25, doi: [`10.1051/0004-6361/201015333`](http://doi.org/10.1051/0004-6361/201015333)

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 1953ApJ...118..113C) Chandrasekhar, S., & Fermi, E. 1953, ApJ, 118, 113, doi: [`10.1086/145731`](http://doi.org/10.1086/145731)

(ref: 2018ApJ...861...14C) Contreras, Y., Sanhueza, P., Jackson, J. M., et al. 2018, ApJ, 861, 14, doi: [`10.3847/1538-4357/aac2ec`](http://doi.org/10.3847/1538-4357/aac2ec)

(ref: 2021ApJ...923..204C) Cortés, P. C., Sanhueza, P., Houde, M., et al. 2021, ApJ, 923, 204, doi: [`10.3847/1538-4357/ac28a1`](http://doi.org/10.3847/1538-4357/ac28a1)

(ref: 2014A&A...565A..75C) Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75, doi: [`10.1051/0004-6361/201322434`](http://doi.org/10.1051/0004-6361/201322434)

(ref: 2017A&A...600L..10C) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 600, L10, doi: [`10.1051/0004-6361/201629754`](http://doi.org/10.1051/0004-6361/201629754)

(ref: 1982MNRAS.200.1169C) Cudlip, W., Furniss, I., King, K. J., & Jennings, R. E. 1982, MNRAS, 200, 1169, doi: [`10.1093/mnras/200.4.1169`](http://doi.org/10.1093/mnras/200.4.1169)

(ref: 1951PhRv...81..890D) Davis, L. 1951, Physical Review, 81, 890, doi: [`10.1103/PhysRev.81.890.2`](http://doi.org/10.1103/PhysRev.81.890.2)

(ref: 2019A&A...626A..84E) Estalella, R., Anglada, G., Dı́az-Rodrı́guez, A. K., & Mayen-Gijon, J. M. 2019, A&A, 626, A84, doi: [`10.1051/0004-6361/201834998`](http://doi.org/10.1051/0004-6361/201834998)

(ref: 2021ApJ...913...29F) Fernández-López, M., Sanhueza, P., Zapata, L. A., et al. 2021, ApJ, 913, 29, doi: [`10.3847/1538-4357/abf2b6`](http://doi.org/10.3847/1538-4357/abf2b6)

(ref: 2009Sci...324.1408G) Girart, J. M., Beltrán, M. T., Zhang, Q., Rao, R., & Estalella, R. 2009, Science, 324, 1408, doi: [`10.1126/science.1171807`](http://doi.org/10.1126/science.1171807)

(ref: 2006Sci...313..812G) Girart, J. M., Rao, R., & Marrone, D. P. 2006, Science, 313, 812, doi: [`10.1126/science.1129093`](http://doi.org/10.1126/science.1129093)

(ref: 2019FrASS...6....5H) Hennebelle, P., & Inutsuka, S.-i. 2019, Frontiers in Astronomy and Space Sciences, 6, 5, doi: [`10.3389/fspas.2019.00005`](http://doi.org/10.3389/fspas.2019.00005)

(ref: 1988QJRAS..29..327H) Hildebrand, R. H. 1988, QJRAS, 29, 327

(ref: 1984ApJ...284L..51H) Hildebrand, R. H., Dragovan, M., & Novak, G. 1984, ApJL, 284, L51, doi: [`10.1086/184351`](http://doi.org/10.1086/184351)

(ref: 2024ApJ...963L..31H) Huang, B., Girart, J. M., Stephens, I. W., et al. 2024, ApJL, 963, L31, doi: [`10.3847/2041-8213/ad27d4`](http://doi.org/10.3847/2041-8213/ad27d4)

(ref: 2014ApJS..213...13H) Hull, C. L. H., Plambeck, R. L., Kwon, W., et al. 2014, ApJS, 213, 13, doi: [`10.1088/0067-0049/213/1/13`](http://doi.org/10.1088/0067-0049/213/1/13)

(ref: 2022ApJ...941...51H) Hwang, J., Kim, J., Pattle, K., et al. 2022, ApJ, 941, 51, doi: [`10.3847/1538-4357/ac99e0`](http://doi.org/10.3847/1538-4357/ac99e0)

(ref: 2013MNRAS.432.1424K) Kirk, J. M., Ward-Thompson, D., Palmeirim, P., et al. 2013, MNRAS, 432, 1424, doi: [`10.1093/mnras/stt561`](http://doi.org/10.1093/mnras/stt561)

(ref: 2018ApJ...855...39K) Koch, P. M., Tang, Y.-W., Ho, P. T. P., et al. 2018, ApJ, 855, 39, doi: [`10.3847/1538-4357/aaa4c1`](http://doi.org/10.3847/1538-4357/aaa4c1)

(ref: 2019ApJ...879...25K) Kwon, W., Stephens, I. W., Tobin, J. J., et al. 2019, ApJ, 879, 25, doi: [`10.3847/1538-4357/ab24c8`](http://doi.org/10.3847/1538-4357/ab24c8)

(ref: 1976ApJ...208..177L) Lampton, M., Margon, B., & Bowyer, S. 1976, ApJ, 208, 177, doi: [`10.1086/154592`](http://doi.org/10.1086/154592)

(ref: 2000ASPC..215...69L) Lazarian, A. 2000, in Astronomical Society of the Pacific Conference Series, Vol. 215, Cosmic Evolution and Galaxy Formation: Structure, Interactions, and Feedback, ed. J. Franco, L. Terlevich, O. López-Cruz, & I. Aretxaga, 69, doi: [`10.48550/arXiv.astro-ph/0003314`](http://doi.org/10.48550/arXiv.astro-ph/0003314)

(ref: 2017NatAs...1E.158L) Li, H.-B., Jiang, H., Fan, X., Gu, Q., & Zhang, Y. 2017, Nature Astronomy, 1, 0158, doi: [`10.1038/s41550-017-0158`](http://doi.org/10.1038/s41550-017-0158)

(ref: 2015Natur.520..518L) Li, H.-B., Yuen, K. H., Otto, F., et al. 2015, Nature, 520, 518, doi: [`10.1038/nature14291`](http://doi.org/10.1038/nature14291)

(ref: 2024NatAs...8..472L) Li, S., Sanhueza, P., Beuther, H., et al. 2024, Nature Astronomy, 8, 472, doi: [`10.1038/s41550-023-02181-9`](http://doi.org/10.1038/s41550-023-02181-9)

(ref: 1996ApJ...472..211L) Li, Z.-Y., & Shu, F. H. 1996, ApJ, 472, 211, doi: [`10.1086/178056`](http://doi.org/10.1086/178056)

(ref: 2019A&A...631A..72L) Lin, Y., Csengeri, T., Wyrowski, F., et al. 2019, A&A, 631, A72, doi: [`10.1051/0004-6361/201935410`](http://doi.org/10.1051/0004-6361/201935410)

(ref: 2022ApJ...925...30L) Liu, J., Qiu, K., & Zhang, Q. 2022a, ApJ, 925, 30, doi: [`10.3847/1538-4357/ac3911`](http://doi.org/10.3847/1538-4357/ac3911)

(ref: 2021ApJ...919...79L) Liu, J., Zhang, Q., Commerçon, B., et al. 2021, ApJ, 919, 79, doi: [`10.3847/1538-4357/ac0cec`](http://doi.org/10.3847/1538-4357/ac0cec)

(ref: 2022FrASS...9.3556L) Liu, J., Zhang, Q., & Qiu, K. 2022b, Frontiers in Astronomy and Space Sciences, 9, 943556, doi: [`10.3389/fspas.2022.943556`](http://doi.org/10.3389/fspas.2022.943556)

(ref: 2020ApJ...895..142L) Liu, J., Zhang, Q., Qiu, K., et al. 2020, ApJ, 895, 142, doi: [`10.3847/1538-4357/ab9087`](http://doi.org/10.3847/1538-4357/ab9087)

(ref: 2020MNRAS.494..827M) Machida, M. N., & Basu, S. 2020, MNRAS, 494, 827, doi: [`10.1093/mnras/staa672`](http://doi.org/10.1093/mnras/staa672)

(ref: 2018MNRAS.477.2760M) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760, doi: [`10.1093/mnras/sty574`](http://doi.org/10.1093/mnras/sty574)

(ref: 2007ARA&A..45..565M) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565, doi: [`10.1146/annurev.astro.45.051806.110602`](http://doi.org/10.1146/annurev.astro.45.051806.110602)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2017A&A...598A...7M) Möller, T., Endres, C., & Schilke, P. 2017, A&A, 598, A7, doi: [`10.1051/0004-6361/201527203`](http://doi.org/10.1051/0004-6361/201527203)

(ref: 2011ApJ...730L..33M) Mottram, J. C., Hoare, M. G., Davies, B., et al. 2011, ApJL, 730, L33, doi: [`10.1088/2041-8205/730/2/L33`](http://doi.org/10.1088/2041-8205/730/2/L33)

(ref: 1999ASIC..540..305M) Mouschovias, T. C., & Ciolek, G. E. 1999, in NATO Advanced Study Institute (ASI) Series C, Vol. 540, The Origin of Stars and Planetary Systems, ed. C. J. Lada & N. D. Kylafis, 305

(ref: 1979ApJ...230..204M) Mouschovias, T. C., & Paleologou, E. V. 1979, ApJ, 230, 204, doi: [`10.1086/157077`](http://doi.org/10.1086/157077)

(ref: 2022ApJ...929...68O) Olguin, F. A., Sanhueza, P., Ginsburg, A., et al. 2022, ApJ, 929, 68, doi: [`10.3847/1538-4357/ac5bd8`](http://doi.org/10.3847/1538-4357/ac5bd8)

(ref: 2021ApJ...909..199O) Olguin, F. A., Sanhueza, P., Guzmán, A. E., et al. 2021, ApJ, 909, 199, doi: [`10.3847/1538-4357/abde3f`](http://doi.org/10.3847/1538-4357/abde3f)

(ref: 2023ApJ...959L..31O) Olguin, F. A., Sanhueza, P., Chen, H.-R. V., et al. 2023, ApJL, 959, L31, doi: [`10.3847/2041-8213/ad1100`](http://doi.org/10.3847/2041-8213/ad1100)

(ref: 1994A&A...291..943O) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: 2001ApJ...546..980O) Ostriker, E. C., Stone, J. M., & Gammie, C. F. 2001, ApJ, 546, 980, doi: [`10.1086/318290`](http://doi.org/10.1086/318290)

(ref: 2011A&A...530A.109P) Padovani, M., & Galli, D. 2011, A&A, 530, A109, doi: [`10.1051/0004-6361/201116853`](http://doi.org/10.1051/0004-6361/201116853)

(ref: 2013A&A...560A.114P) Padovani, M., Hennebelle, P., & Galli, D. 2013, A&A, 560, A114, doi: [`10.1051/0004-6361/201322407`](http://doi.org/10.1051/0004-6361/201322407)

(ref: 2012A&A...543A..16P) Padovani, M., Brinch, C., Girart, J. M., et al. 2012, A&A, 543, A16, doi: [`10.1051/0004-6361/201219028`](http://doi.org/10.1051/0004-6361/201219028)

(ref: 2021ApJ...912..159P) Palau, A., Zhang, Q., Girart, J. M., et al. 2021, ApJ, 912, 159, doi: [`10.3847/1538-4357/abee1e`](http://doi.org/10.3847/1538-4357/abee1e)

(ref: 2015Natur.518..213P) Pineda, J. E., Offner, S. S. R., Parker, R. J., et al. 2015, Nature, 518, 213, doi: [`10.1038/nature14166`](http://doi.org/10.1038/nature14166)

(ref: 2007MNRAS.377...77P) Price, D. J., & Bate, M. R. 2007, MNRAS, 377, 77, doi: [`10.1111/j.1365-2966.2007.11621.x`](http://doi.org/10.1111/j.1365-2966.2007.11621.x)

(ref: 2014ApJ...794L..18Q) Qiu, K., Zhang, Q., Menten, K. M., et al. 2014, ApJL, 794, L18, doi: [`10.1088/2041-8205/794/1/L18`](http://doi.org/10.1088/2041-8205/794/1/L18)

(ref: 2009ApJ...707..921R) Rao, R., Girart, J. M., Marrone, D. P., Lai, S.-P., & Schnee, S. 2009, ApJ, 707, 921, doi: [`10.1088/0004-637X/707/2/921`](http://doi.org/10.1088/0004-637X/707/2/921)

(ref: 2008ApJ...679.1338R) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: 2021ApJ...915L..10S) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10, doi: [`10.3847/2041-8213/ac081c`](http://doi.org/10.3847/2041-8213/ac081c)

(ref: 2017A&A...607A...2S) Soler, J. D., & Hennebelle, P. 2017, A&A, 607, A2, doi: [`10.1051/0004-6361/201731049`](http://doi.org/10.1051/0004-6361/201731049)

(ref: 2013ApJ...769L..15S) Stephens, I. W., Looney, L. W., Kwon, W., et al. 2013, ApJL, 769, L15, doi: [`10.1088/2041-8205/769/1/L15`](http://doi.org/10.1088/2041-8205/769/1/L15)

(ref: 2009ApJ...700..251T) Tang, Y.-W., Ho, P. T. P., Koch, P. M., et al. 2009, ApJ, 700, 251, doi: [`10.1088/0004-637X/700/1/251`](http://doi.org/10.1088/0004-637X/700/1/251)

(ref: 2023ApJ...950...57T) Taniguchi, K., Sanhueza, P., Olguin, F. A., et al. 2023, ApJ, 950, 57, doi: [`10.3847/1538-4357/acca1d`](http://doi.org/10.3847/1538-4357/acca1d)

(ref: 2006PASP..118.1340V) Vaillancourt, J. E. 2006, PASP, 118, 1340, doi: [`10.1086/507472`](http://doi.org/10.1086/507472)

[^1]: <http://www.dendrograms.org/>

[^2]: also see (cite: 2022ApJ...925...30L; 2022FrASS...9.3556L)

[^3]: In (cite: 2001ApJ...546..980O) the size scale adopted is $\sim8$ pc, whereas (cite: 2021ApJ...919...79L) estimated Q to be $\sim0.28$ at a size scale of a $1-0.2$ pc, which is relatively closer to the size scale of the area of analysis. Adopting the later, the B$_{\mathrm{pos}}$  is estimated as $3.0-3.6$ mG, which is consistent with our estimated B$_{\mathrm{pos}}$.

</paper>

Write the methods card for this paper.