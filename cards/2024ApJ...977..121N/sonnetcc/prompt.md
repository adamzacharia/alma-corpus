# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977..121N\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977..121N",
 "title": "Exploring Magnetic Fields in a Merging Galaxy: Comparing Polarization and Velocity Gradient in the Centaurus Galaxy",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Nguyen, Quynh Lan",
 "n_authors": 3,
 "arxiv_id": "2406.04242",
 "doi": "10.3847/1538-4357/ad93a3",
 "alma_projects_linked_by_archive": [
  "2013.1.00803.S"
 ]
}
```

Paper text:
<paper>
# Exploring magnetic fields in merging galaxy: combining polarization and velocity gradient in the Centaurus Galaxy

## Abstract

In this study, we apply the Velocity Gradient Technique (VGT) to the merging Centaurus galaxy. We compare gradient maps derived from the PHANGS-ALMA survey using CO emission lines with magnetic field tracings from dust polarization data obtained via the HAWC+ instrument. Our analysis reveals a strong correspondence between the directions indicated by these two tracers across most of the galactic image. Specifically, we identify jet regions as areas of anti-alignment, consistent with previous reports that gradients tend to rotate 90 degrees in outflow regions. Statistically, we find that the alignment of magnetic fields, as revealed by polarization, is most accurate in regions with the highest signal-to-noise ratios. Our findings underscore the utility of velocity gradients as a valuable complementary tool for probing magnetic fields and dynamical processes in merging galaxies.

# Introduction

Merging plays an important role in the galaxy’s evolution, so tracing the magnetic field in the merging galaxy is interesting. It can provide valuable insight into the galaxy’s dynamic and evolution as well as the jet formation (cite: 2021MNRAS.506..229W). Through the interaction of the magnetic field in the merging galaxy and the magnetic field in the interstellar medium and other galaxies and cluster galaxies, we can understand better the forming and the shape of the large-scale structure of the universe (cite: 2016A&A...593A..89R; 2021Natur.593...47C; 2020ApJ...892..133P).

The observations in far-infrared and radio for galactic and extragalactic magnetic fields have significantly developed in the past decades (cite: P-Kronberg_1994; 2015A&ARv..24....4B; 2021NatAs...5..604L). Even if it has some initial results, it still has some limitations. Dust and synchrotron polarization can trace the plane of the sky (POS) magnetic field orientation. However, dust polarization is affected by dust alignment efficiency (cite: Lazarian_2007), and synchrotron polarization is subject to Faraday rotation (cite: 2015A&ARv..24....4B). Synchrotron polarization provides the method that can trace the magnetic fields in the warm and high temperatures of the gas (cite: Beck:2000dc; 2011MNRAS.412.2396F; 2015A&ARv..24....4B) and dust polarization contains contribution from different gas phases, including the one associated with diffuse atomic gas and dense molecular gas (cite: Lazarian_2007; 2015ARA&A..53..501A).

To separate the magnetic field associated with molecular gas, which is the most important fueling material for the galactic nuclei, (cite: 2022ApJ...941...92H) proposed the use of the Velocity Gradient Technique (VGT; (cite: 2017ApJ...835...41G; Lazarian_2018; 2018MNRAS.480.1333H)) and CO spectroscopic observations. Despite that, the study of VGT has been explored for six individual galaxies M51, NGC 1068, NGC 1097, NGC 3627, and NGC 4826 (cite: 2022ApJ...941...92H), NGC3627 (cite: 2023MNRAS.519.1068L), NGC 0628 (cite: 2024ApJ...967...18Z) but its application or test to galaxy merger has not been done yet. Centaurus galaxy, as one of the closest nuclear active galaxy mergers, is the best test-bed for VGT.

In this work, we trace the magnetic field of the Centaurus galaxy by using the VGT, particularly its branch, namely, Velocity Channel Gradients (VChGs; (cite: Lazarian_2018)) and $\rm ^{12}CO$ (J = 2–1) emission lines from the PHANGS-ALMA survey (cite: 2021ApJS..257...43L). On the other hand, the magnetic field in Centaurus has been studied by (cite: 2021NatAs...5..604L) using HAWC+ dust polarization at 89$\mu$m. Here we compare the magnetic field traced by VGT to the one inferred from HAWC+.

However, it should be noted that the dynamics of galaxy mergers are more complicated than normal galaxies. This makes the interpretation of the comparison more difficult. For instance, early applications (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L; 2024ApJ...967...18Z) of the VGT have conventionally set the turbulence injection scale, $L_{\rm inj}$, at approximately 100 pc, a measure derived from extensive turbulence studies within the Milky Way (cite: 1995ApJ...443..209A; 2010ApJ...710..853C; 2022ApJ...934....7H). This assumption aligns with the typical scale at which energy is injected into the interstellar medium via stellar feedback and other dynamic processes in relatively stable galactic environments. However, in scenarios involving galaxy mergers, the dynamics of turbulence injection can be substantially altered. Mergers not only impact galactic structure and star formation but also contribute to turbulence on a much larger scale (cite: 2021MNRAS.506..229W). The merging process itself can act as a significant driver of turbulence, likely extending the injection scale well beyond the 100 pc typically observed in more quiescent galaxies like the Milky Way. Given this context, it is reasonable to hypothesize that the injection scale $L_{\rm inj}$ in the Centaurus galaxy, which has experienced dynamic merger events, could be larger than 100 pc and we expect the $\rm ^{12}CO$ observation with an average spatial resolution of $145.5$ pc satisfies the VGT’s requirements for this pilot study.

The details of the archival data are shown in Section [2](#sec:data). Centaurus galaxy is one of the closest nuclear active galaxies and we want to use it as a test for VGT. In Section [3](#sec:method), we introduce the details theory of the VGT, velocity caustics, and VGT pipeline. In Section  [4](#sec:result), we will discuss some results about the mapping magnetic field of the Centaurus galaxy and compare it with dust polarization result. In Section  [5](#sec:conclusion), we will provide some conclusions about the magnetic fields of the Centaurus galaxy using VGT and some possibility of the galaxies merges scenarios.

# Observational Data

## Emission Lines

In this study, we utilized the $\rm ^{12}CO$ (J = 2–1) emission lines provided by the Physics at High Angular Resolution in Nearby Galaxies (PHANGS)–ALMA survey (cite: 2021ApJS..257...43L). The PHANGS-ALMA survey offers $\rm ^{12}CO$ (J = 1 - 0) emission line data at a spatial resolution of approximately $8.13''$ (about 145.5 pc) and a velocity resolution of 2.5 km s$^{-1}$ for the nearby galaxy Centaurus. This survey achieves a high signal-to-noise ratio, with an RMS brightness temperature noise level around $\sim0.30\pm0.13$ K km s$^{-1}$.

## Polarization measurement

For polarization measurements, we employed data from the High-resolution Airborne Wideband Camera Plus (HAWC+) archived in the HAWC+ database (cite: 2018JAI.....740008H; 2021NatAs...5..604L). Magnetic field orientations were determined using the relation $\phi_B=\phi+\pi/2$, where $\phi$ represents the polarization angle. Measurements were taken from band C (89 $\mu$m, FWHM $\approx7.8''$).

We limited our analysis to pixels where the polarization fraction ($p$) divided by its uncertainty ($\sigma_p$) exceeds 1 ($p/\sigma_p > 1$). To compare with the magnetic field measured with VGT, we smooth the polarization data to FWHM $\approx40''$ matching the spatial resolution of VGT.

# Methodology

## Theoretical consideration: Velocity Gradient Technique

The theoretical underpinning of the Velocity Gradient Technique (VGT) lies in the anisotropy inherent in MHD turbulence, a concept extensively developed by (cite: GS95) and (cite: LV99). This anisotropy suggests that turbulent eddies elongate along magnetic field lines, manifesting notably in local reference frames. (cite: LV99) formalized this anisotropy as follows: $$\begin{equation}
\label{eq.lv99}
l_\parallel = L_{\rm inj}\left(\frac{l_\bot}{L_{\rm inj}}\right)^{\frac{2}{3}}M_A^{-4/3},~~~M_A\le 1,
\end{equation}$$ where $l_\bot$ and $l_\parallel$ are the scales perpendicular and parallel to the local magnetic field, respectively. Here, $M_A = v_{\rm inj}/v_A$ represents the Alfvén Mach number, with $v_{\rm inj}$ being the injection velocity and $v_A$ the Alfvén speed.

This anisotropy has been demonstrated by numerical simulations (cite: CV20; 2001ApJ...554.1175M; CL03; 2010ApJ...720..742K; HXL21) and in situ measurements in the solar wind (cite: 2016ApJ...816...15W; 2020FrASS...7...83M; 2021ApJ...915L...8D; 2024ApJ...962...89Z). From Eq.[\[eq.lv99\]](#eq.lv99), we understand that $l_\parallel$ significantly exceeds $l_\bot$, leading to the dominance of the gradient of velocity fluctuations perpendicular to the local magnetic field: $$\begin{equation}
\label{eq.vg}
\nabla v_l \approx \frac{v_{l,\bot}}{l_{\bot}} = \frac{v_{\rm inj}}{L_{\rm inj}}M_A^{1/3}\left(\frac{l_{\bot}}{L_{\rm inj}}\right)^{-2/3}, M_A \le 1.
\end{equation}$$

This scaling relation ($\propto l_\bot^{-2/3}$) is crucial as it reveals that the amplitude of the turbulent velocity gradient increases at smaller scales, which is a characteristic not typically observed in non-turbulent velocity fields such as galactic differential rotation. For effective application to external galaxies, observations should resolve the scale at which turbulence’s anisotropy manifests prominently, typically at $L_{\rm inj}$ for sub-Alfvén and trans-Alfvén turbulence or $L_{\rm inj}M_A^{-3}$ for super-Alfvénic turbulence (cite: 2006ApJ...645L..25L).

![](VGT_CO.pdf)

![](VGT_hawc+.pdf)

## Velocity caustics

The anisotropic nature of MHD turbulence can be observed in velocity channel maps, $p(x, y, v_{\rm los})$, obtained from spectroscopic observations. This observation is primarily due to the velocity caustics effect, which posits that real density structures with different velocities may be sampled into the same velocity channel, thereby significantly altering the observed intensity structures within the spectroscopic channel maps (cite: LP00; LP04; 2016MNRAS.461.1227K; 2023MNRAS.524.2994H).

Mathematically, the intensity observed in a channel can be expressed as the sum of two terms (cite: 2023MNRAS.524.2994H): $$\begin{equation}
p(x,y,v_{\rm los})=p_{v}(x,y,v_{\rm los})+p_{d}(x,y,v_{\rm los}),    
\end{equation}$$ where $p_{v}$ represents fluctuations primarily caused by velocity—known as the velocity caustics effect—while $p_{dc}$ reflects the inhomogeneities within the actual density field. The relative contribution of these terms is dependent on the channel width, i.e., the velocity resolution of the observation. A narrower channel width enhances the contribution of $p_{v}$, leading to a scenario where intensity fluctuations in thin channels are predominantly due to velocity fluctuations. Specifically, when the channel width $\Delta v$ is narrower than the velocity dispersion of the turbulent eddies under observation, the intensity fluctuations within such a thin channel will be primarily driven by velocity fluctuations.

Turbulence studies within the Milky Way suggest that the velocity dispersion at a scale of 100 pc is approximately 10 km/s (cite: 1995ApJ...443..209A; 2010ApJ...710..853C; 2022ApJ...934....7H). This dispersion can be even higher in environments such as galaxy mergers. Given that the PHANGS-ALMA survey offers a velocity resolution of 2.5 km/s, this ensures that the velocity caustics dominate the observed intensity in the spectroscopic velocity channels.

## VGT pipeline

In this study, we employed the VGT, following a multi-step process detailed in (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L):\
**Step 1.** Each thin channel map, $p(x, y, v_{\rm los})$, undergoes convolution with 3$\times$3 Sobel kernels $G_x$ and $G_y$ to compute the gradients: $$\begin{equation}
\begin{aligned}
\nabla_{x} p(x, y, v_{\rm los}) &= G_x * p(x, y, v_{\rm los}), \\
\nabla_{y} p(x, y, v_{\rm los}) &= G_y * p(x, y, v_{\rm los}),
\end{aligned}
\end{equation}$$ where \* denotes convolution. These gradients are used to determine the pixelized gradient map $\psi_g (x, y, v_{\rm los})$: $$\begin{equation}
\psi_g (x, y, v_{\rm los}) = \tan^{-1}\left(\frac{\nabla_{y} p(x, y, v_{\rm los})}{\nabla_{x}p(x, y, v_{\rm los})}\right).
\end{equation}$$ Only pixels with a brightness temperature less than three times the RMS noise are retained for subsequent analysis.

**Step 2.** The pixelized map $\psi_g(x, y, v_{\rm los})$ is segmented into 20$\times$20 pixel sub-blocks—although other sizes have been tested (cite: YL17a; LY18a; 2020ApJ...905..129H) —and processed as follows:

1.  A histogram of gradient orientations within each sub-block is produced and fitted with a Gaussian distribution.

2.  The peak of this Gaussian distribution is taken as the dominant gradient orientation for that sub-block.

**Step 3.** Following sub-block averaging, the averaged gradient angle map $\psi_{gs}(x, y, v_{\rm los})$ is compiled for each velocity channel. Repeating the Steps 1 and 2 for every channel within the velocity range of interest, we can then construct the pseudo-Stokes parameters $Q_g(x,y)$ and $U_g(x,y)$: $$\begin{equation}
\label{eq.QU}
\begin{aligned}
Q_{\rm g} (x,y) &= \int_{v_{\rm los, min}}^{v_{\rm los, max}} p(x, y, v_{\rm los}) \cos(2\psi_{gs}(x,y,v_{\rm los})) dv_{\rm los},\\
U_{\rm g} (x,y) &= \int_{v_{\rm los, min}}^{v_{\rm los, max}} p(x, y, v_{\rm los}) \sin(2\psi_{gs}(x,y,v_{\rm los})) dv_{\rm los},
\end{aligned}
\end{equation}$$ where $v_{\rm los, max}$ and $v_{\rm los, min}$ represent the upper and lower levels of the velocity range used for integration. The POS magnetic field orientation is inferred from: $$\begin{equation}
\psi_{\rm B}(x,y) = \frac{1}{2} \tan^{-1}\left(\frac{U_{\rm g} (x,y)}{Q_{\rm g} (x,y)}\right) + \frac{\pi}{2}.
\end{equation}$$

To quantify the agreement between VGT and the magnetic field inferred from polarization, we utilize the Alignment Measure (AM; (cite: GL17)), expressed as: $$\begin{equation}
\begin{aligned}
{\rm AM} = 2 \left(\cos^2\theta_{\rm r} - \frac{1}{2}\right)
\end{aligned}
\end{equation}$$ Here, $\theta_{\rm r} = \vert\phi_{\rm B}-\psi_{\rm B}\vert$, where $\phi_{\rm B}$ is the magnetic field angle inferred from polarization. An AM value of 1 implies parallel alignment of $\phi_{\rm B}$ and $\psi_{\rm B}$, while -1 indicates perpendicularity.

![](AM.png)

# Result

![](AM_SNR.pdf)

Fig. [1](#fig:vgt) presents the magnetic fields of Centaurus as mapped by VGT-CO. The image captures the twisting of the magnetic field from the southeast and northwest filamentary structures, which resemble spiral-arm-like features, towards the molecular disk and into the nucleus. The magnetic field, as depicted by VGT-CO, primarily aligns with these two filamentary structures. However, it exhibits a twist across the central region of approximately 500 pc radius around the nucleus. Additionally, the magnetic fields inferred from HAWC+ polarization, illustrated in Fig. [2](#fig:hawc+), exhibit similar morphology and generally agree with the measurements from VGT-CO. Notably, near the southeast tail, the polarization-inferred magnetic field diverges from the galactic structure indicated by CO, instead crossing it. This specific pattern is absent in the VGT-CO measurements.

The misalignment between the magnetic fields traced by VGT-CO and those indicated by dust polarization is quantified by the AM, as shown in Fig. [3](#fig:am). The anti-alignment, indicated by negative AM values, is observed in the two tails, while a misalignment with AM $\approx 0$ is noted in the northwest of the central disk. A higher degree of the mean alignment is observed in several Seyfert galaxies and the Milky Way (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L; 2024ApJ...967...18Z). We attribute this effect to the fact that the Centaurus is a merging galaxy with much more complex dynamics of gas. Jets, shocks, and inflows affect the gradients, especially if the measurements. These effects were discussed at length in (cite: Lazarian_2018; 2019ApJ...886...17H; 2020ApJ...897..123H; 2024MNRAS.530.1066L). In particular, anti-alignment is present in the radio jet regions, which is expected for the outflow regions. Further studies of the origin of this discrepancy are required. This can elucidate the dynamics of gas in the merging galaxy.

Another source of the observed misalignment can be the difference in CO and dust distribution in these regions. Unlike CO, dust is well mixed with all interstellar phases, including molecular and atomic gas (cite: 2015ARA&A..53..501A). In Fig. [3](#fig:am), we see the central low-AM region is associated with strong HI absorption, suggesting the dust polarization in that region might be dominated by dust associated with H I rather than CO. In addition, HAWC+ dust polarization at $89~\mu$m is anticipated to trace magnetic fields in warmer media than CO. If magnetic fields in warm and cold gas are very different, there is a warmer phase preferentially traced by HAWC+; the morphology of magnetic fields with low-AM could reflect that the magnetic fields in warm and cold gas are different.

We also note that the most significant misalignment between VGT-CO and dust polarization measurements is in the low-density regions associated with poor signal-to-noise ratio. This is illustrated in Fig. [4](#fig:am_hist), where we observe that we do not observe a negative AM at the high signal-to-noise ratio regions.

Overall, the global agreement between the magnetic field orientations measured with VGT-CO and those inferred from dust polarization, especially in the central disk, underscores the coherence of magnetic fields across different gas phases. This includes the cold molecular phase traced by CO and warmer phases indicated by HAWC+. The observed coherence across these phases suggests that the magnetic fields threading the multiphase gas, spanning a range of densities, are integrally involved in the galactic dynamic evolution. This supports the notion that molecular clouds are part of a unified magnetic ecosystem in galaxies and that magnetic fields in multiphase gas maintain an overall coherent structure even in a merging galaxy. Additional input from synchrotron polarization could be useful for getting more information. In the aforementioned studies of Seyfert galaxies with VGT (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L; 2024ApJ...967...18Z), the alignment between the velocity gradients in CO and synchrotron could be better than the alignment with dust, which elucidated the 3D magnetic field structure.

# Conclusion

Velocity gradients have demonstrated efficacy in tracing magnetic fields within magnetohydrodynamic (MHD) turbulence environments. This capability has been validated across various regions of the Milky Way and several Seyfert galaxies. In this paper, we extend the application of velocity gradient techniques (VGT) to the more complex scenario of a merging galaxy. Specifically, we measure velocity gradients in the Centaurus galaxy and evaluate their effectiveness in tracing magnetic fields, using dust polarization as a comparative measure. Our findings indicate that VGT results generally concur with dust polarization on a statistical basis. Additionally, we identify localized regions of significant misalignment and anti-alignment. Drawing on prior studies, we hypothesize that outflows and the presence of shocked gas may account for these discrepancies. If corroborated, this comparison of gradients and polarization could elucidate the underlying physics of galactic mergers. Furthermore, our study aids in pinpointing regions within disturbed galaxies where velocity gradients can reliably map magnetic fields in the absence of other tracers. Future research, utilizing higher signal-to-noise data and incorporating synchrotron polarization, is essential to further explore these findings.

A.L. acknowledges the support of NASA ATP AAH7546, NSF grants AST 2307840, and ALMA SOSPADA-016. Financial support for this work was provided by NASA through award 09_0231 issued by the Universities Space Research Association, Inc. (USRA). Y.H. acknowledges the support for this work provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51557.001 awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. This work used SDSC Expanse CPU at SDSC through allocations PHY230032, PHY230033, PHY230091, and PHY230105 from the Advanced Cyberinfrastructure Coordination Ecosystem: Services & Support (ACCESS) program, which is supported by National Science Foundation grants #2138259, #2138286, #2138307, #2137603, and #2138296. Q.L.N. acknowledges the support in part by grant NSF PHY-1748958 to the Kavli Institute for Theoretical Physics (KITP), the Institute for Cosmic Ray Research-International University Research Program, Notre Dame College of Science Internal Grant.

# Software

Julia (cite: bezanson2012julia)

natexlab

(ref: 2015ARA&A..53..501A) Andersson, B. G., Lazarian, A., & Vaillancourt, J. E. 2015, ARA&A, 53, 501, doi: [`10.1146/annurev-astro-082214-122414`](http://doi.org/10.1146/annurev-astro-082214-122414)

(ref: 1995ApJ...443..209A) Armstrong, J. W., Rickett, B. J., & Spangler, S. R. 1995, ApJ, 443, 209, doi: [`10.1086/175515`](http://doi.org/10.1086/175515)

(ref: Beck:2000dc) Beck, R. 2001, Space Sci. Rev., 99, 243, doi: [`10.1023/A:1013805401252`](http://doi.org/10.1023/A:1013805401252)

(ref: 2015A&ARv..24....4B) Beck, R. 2015, A&ARv, 24, 4, doi: [`10.1007/s00159-015-0084-4`](http://doi.org/10.1007/s00159-015-0084-4)

(ref: bezanson2012julia) Bezanson, J., Karpinski, S., Shah, V. B., & Edelman, A. 2012, arXiv preprint arXiv:1209.5145

(ref: 2010ApJ...710..853C) Chepurnov, A., & Lazarian, A. 2010, ApJ, 710, 853, doi: [`10.1088/0004-637X/710/1/853`](http://doi.org/10.1088/0004-637X/710/1/853)

(ref: 2021Natur.593...47C) Chibueze, J. O., Sakemi, H., Ohmura, T., et al. 2021, Nature, 593, 47, doi: [`10.1038/s41586-021-03434-1`](http://doi.org/10.1038/s41586-021-03434-1)

(ref: CL03) Cho, J., & Lazarian, A. 2003, MNRAS, 345, 325, doi: [`10.1046/j.1365-8711.2003.06941.x`](http://doi.org/10.1046/j.1365-8711.2003.06941.x)

(ref: CV20) Cho, J., & Vishniac, E. T. 2000, ApJ, 539, 273, doi: [`10.1086/309213`](http://doi.org/10.1086/309213)

(ref: 2021ApJ...915L...8D) Duan, D., He, J., Bowen, T. A., et al. 2021, ApJL, 915, L8

(ref: 2011MNRAS.412.2396F) Fletcher, A., Beck, R., Shukurov, A., Berkhuijsen, E. M., & Horellou, C. 2011, MNRAS, 412, 2396, doi: [`10.1111/j.1365-2966.2010.18065.x`](http://doi.org/10.1111/j.1365-2966.2010.18065.x)

(ref: GS95) Goldreich, P., & Sridhar, S. 1995, ApJ, 438, 763, doi: [`10.1086/175121`](http://doi.org/10.1086/175121)

(ref: 2017ApJ...835...41G) González-Casanova, D. F., & Lazarian, A. 2017a, ApJ, 835, 41, doi: [`10.3847/1538-4357/835/1/41`](http://doi.org/10.3847/1538-4357/835/1/41)

(ref: GL17) —. 2017b, ApJ, 835, 41

(ref: 2022ApJ...934....7H) Ha, T., Li, Y., Kounkel, M., et al. 2022, ApJ, 934, 7, doi: [`10.3847/1538-4357/ac76bf`](http://doi.org/10.3847/1538-4357/ac76bf)

(ref: 2018JAI.....740008H) Harper, D. A., Runyan, M. C., Dowell, C. D., et al. 2018, Journal of Astronomical Instrumentation, 7, 1840008

(ref: 2023MNRAS.524.2994H) Hu, Y., Lazarian, A., Alina, D., Pogosyan, D., & Ho, K. W. 2023, MNRAS, 524, 2994, doi: [`10.1093/mnras/stad1924`](http://doi.org/10.1093/mnras/stad1924)

(ref: 2022ApJ...941...92H) Hu, Y., Lazarian, A., Beck, R., & Xu, S. 2022, ApJ, 941, 92, doi: [`10.3847/1538-4357/ac9df0`](http://doi.org/10.3847/1538-4357/ac9df0)

(ref: 2020ApJ...905..129H) Hu, Y., Lazarian, A., & Bialy, S. 2020a, ApJ, 905, 129, doi: [`10.3847/1538-4357/abc3c6`](http://doi.org/10.3847/1538-4357/abc3c6)

(ref: 2020ApJ...897..123H) Hu, Y., Lazarian, A., & Yuen, K. H. 2020b, ApJ, 897, 123, doi: [`10.3847/1538-4357/ab9948`](http://doi.org/10.3847/1538-4357/ab9948)

(ref: HXL21) Hu, Y., Xu, S., & Lazarian, A. 2021, ApJ, 911, 37, doi: [`10.3847/1538-4357/abea18`](http://doi.org/10.3847/1538-4357/abea18)

(ref: 2018MNRAS.480.1333H) Hu, Y., Yuen, K. H., & Lazarian, A. 2018, MNRAS, 480, 1333, doi: [`10.1093/mnras/sty1807`](http://doi.org/10.1093/mnras/sty1807)

(ref: 2019ApJ...886...17H) —. 2019, ApJ, 886, 17, doi: [`10.3847/1538-4357/ab4b5e`](http://doi.org/10.3847/1538-4357/ab4b5e)

(ref: 2016MNRAS.461.1227K) Kandel, D., Lazarian, A., & Pogosyan, D. 2016, MNRAS, 461, 1227, doi: [`10.1093/mnras/stw1296`](http://doi.org/10.1093/mnras/stw1296)

(ref: 2010ApJ...720..742K) Kowal, G., & Lazarian, A. 2010, ApJ, 720, 742, doi: [`10.1088/0004-637X/720/1/742`](http://doi.org/10.1088/0004-637X/720/1/742)

(ref: P-Kronberg_1994) Kronberg, P. P. 1994, Reports on Progress in Physics, 57, 325, doi: [`10.1088/0034-4885/57/4/001`](http://doi.org/10.1088/0034-4885/57/4/001)

(ref: 2006ApJ...645L..25L) Lazarian, A. 2006, ApJL, 645, L25, doi: [`10.1086/505796`](http://doi.org/10.1086/505796)

(ref: Lazarian_2007) Lazarian, A., & Hoang, T. 2007, The Astrophysical Journal, 669, L77, doi: [`10.1086/523849`](http://doi.org/10.1086/523849)

(ref: LP00) Lazarian, A., & Pogosyan, D. 2000, ApJ, 537, 720, doi: [`10.1086/309040`](http://doi.org/10.1086/309040)

(ref: LP04) —. 2004, ApJ, 616, 943, doi: [`10.1086/422462`](http://doi.org/10.1086/422462)

(ref: LV99) Lazarian, A., & Vishniac, E. T. 1999, ApJ, 517, 700, doi: [`10.1086/307233`](http://doi.org/10.1086/307233)

(ref: Lazarian_2018) Lazarian, A., & Yuen, K. H. 2018, The Astrophysical Journal, 853, 96, doi: [`10.3847/1538-4357/aaa241`](http://doi.org/10.3847/1538-4357/aaa241)

(ref: LY18a) Lazarian, A., & Yuen, K. H. 2018, ApJ, 853, 96, doi: [`10.3847/1538-4357/aaa241`](http://doi.org/10.3847/1538-4357/aaa241)

(ref: 2021ApJS..257...43L) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: 2024MNRAS.530.1066L) Liu, M., Hu, Y., & Lazarian, A. 2024, MNRAS, 530, 1066, doi: [`10.1093/mnras/stae863`](http://doi.org/10.1093/mnras/stae863)

(ref: 2023MNRAS.519.1068L) Liu, M., Hu, Y., Lazarian, A., Xu, S., & Soida, M. 2023, MNRAS, 519, 1068, doi: [`10.1093/mnras/stac3518`](http://doi.org/10.1093/mnras/stac3518)

(ref: 2021NatAs...5..604L) Lopez-Rodriguez, E. 2021, Nature Astronomy, 5, 604, doi: [`10.1038/s41550-021-01329-9`](http://doi.org/10.1038/s41550-021-01329-9)

(ref: 2001ApJ...554.1175M) Maron, J., & Goldreich, P. 2001, ApJ, 554, 1175, doi: [`10.1086/321413`](http://doi.org/10.1086/321413)

(ref: 2020FrASS...7...83M) Matteini, L., Franci, L., Alexandrova, O., et al. 2020, Frontiers in Astronomy and Space Sciences, 7, 83

(ref: 2020ApJ...892..133P) Paliya, V. S., Pérez, E., Garcı́a-Benito, R., et al. 2020, ApJ, 892, 133, doi: [`10.3847/1538-4357/ab754f`](http://doi.org/10.3847/1538-4357/ab754f)

(ref: 2016A&A...593A..89R) Rodenbeck, K., & Schleicher, D. R. G. 2016, A&A, 593, A89, doi: [`10.1051/0004-6361/201527393`](http://doi.org/10.1051/0004-6361/201527393)

(ref: 2010A&A...515A..67S) Struve, C., Oosterloo, T. A., Morganti, R., & Saripalli, L. 2010, A&A, 515, A67, doi: [`10.1051/0004-6361/201014355`](http://doi.org/10.1051/0004-6361/201014355)

(ref: 2016ApJ...816...15W) Wang, X., Tu, C., Marsch, E., He, J., & Wang, L. 2016, ApJ, 816, 15, doi: [`10.3847/0004-637X/816/1/15`](http://doi.org/10.3847/0004-637X/816/1/15)

(ref: 2021MNRAS.506..229W) Whittingham, J., Sparre, M., Pfrommer, C., & Pakmor, R. 2021, MNRAS, 506, 229, doi: [`10.1093/mnras/stab1425`](http://doi.org/10.1093/mnras/stab1425)

(ref: YL17a) Yuen, K. H., & Lazarian, A. 2017, ApJL, 837, L24, doi: [`10.3847/2041-8213/aa6255`](http://doi.org/10.3847/2041-8213/aa6255)

(ref: 2024ApJ...967...18Z) Zhao, M., Zhou, J., Baan, W. A., et al. 2024a, ApJ, 967, 18, doi: [`10.3847/1538-4357/ad3a62`](http://doi.org/10.3847/1538-4357/ad3a62)

(ref: 2024ApJ...962...89Z) Zhao, S., Yan, H., Liu, T. Z., Yuen, K. H., & Shi, M. 2024b, ApJ, 962, 89, doi: [`10.3847/1538-4357/ad132e`](http://doi.org/10.3847/1538-4357/ad132e)

</paper>

Write the methods card for this paper.