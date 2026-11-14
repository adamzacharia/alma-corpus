# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...993..166J\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...993..166J",
 "title": "Puffed-up Inner Rings and Razor-thin Outer Rings in Structured Protoplanetary Disks",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Jiang, Haochang",
 "n_authors": 11,
 "arxiv_id": "2509.13122",
 "doi": "10.3847/1538-4357/ae089e",
 "alma_projects_linked_by_archive": [
  "2015.1.00118.S",
  "2016.1.00484.L",
  "2017.1.01151.S",
  "2017.1.01167.S",
  "2018.1.00945.S",
  "2018.1.01255.S",
  "2018.1.01829.S"
 ]
}
```

Paper text:
<paper>
# Puffed-up Inner Rings and Razor-thin Outer Rings in Structured Protoplanetary Disks

## Abstract

The vertical distribution of pebbles in protoplanetary disks is a fundamental property influencing planet formation, from dust aggregation to the assembly of planetary cores. In the outer region of protoplanetary disks, the intensity of the optically thin but geometrically thick dust ring decreases along the minor axis due to reduced line-of-sight optical depth. Multi-ring disks thus provide an excellent opportunity to study the radial variation of the vertical properties of dust. We investigate the vertical dust distribution in 6 protoplanetary disks with resolved double rings, using high-resolution ALMA Band 6 continuum observations. By modeling the azimuthal intensity variations in these rings, we constrain the dust scale heights for each ring. Our results reveal a dichotomy: inner rings exhibit puffed-up dust layers with heights comparable to the gas scale height, while outer rings are significantly more settled, with dust scale heights less than 20% of the gas scale height. This suggests a radial dependence in dust settling efficiency within the disks, potentially driven by localized planetary interactions or the global radial dependence of the Vertical Shear Instability (VSI). We discuss the implications of these findings for dust trapping, planet formation, and protoplanetary disk evolution. Our work highlights the importance of vertical dust distribution in understanding the early stages of planet formation and suggests that outer ($>80$ au), settled rings are preferred sites for planet formation over inner ($<80$ au), turbulent rings.

UTF8gbsn

# Introduction

Pebbles, typically (sub)millimeter-sized particles, are the fundamental building blocks of planetary cores in protoplanetary disks. Under the influence of the central star’s gravity, pebbles experience aerodynamic drag by the gas, leading to angular momentum loss and radial drift within the disk (cite: Weidenschilling1977a). Concurrently, they settle toward the disk’s midplane (cite: NakagawaEtal1986) while also diffusing due to turbulent gas mixing in the vertical direction (cite: OrmelCuzzi2007; YoudinLithwick2007).

The spatial distribution of pebbles directly impacts planet formation. The formation of planetesimals and their subsequent growth into planets are pivotal stages in the core accretion theory. Among the prevailing theories, streaming instability is regarded as a promising mechanism for planetesimal formation (cite: YoudinGoodman2005; JohansenEtal2009), while pebble accretion is recognized as an efficient pathway for the growth of newly formed planetesimals (cite: OrmelKlahr2010; LambrechtsJohansen2012). Both processes, however, critically depend on the accumulation of pebbles. Enhanced dust concentration in both radial and vertical directions is essential for increasing pebble accretion efficiency (cite: LiuOrmel2018; OrmelLiu2018; JiangOrmel2023) and promoting planetesimal formation via streaming instability (cite: XuBai2022a; LimEtal2024).

Thanks to the high angular resolution of ALMA, rings have been found ubiquitous in dust continuum emission in Class II disks across a wide range of stellar types (cite: LongEtal2018f; AndrewsEtal2018b; ShiEtal2024), with detailed studies suggesting radial dust trapping (cite: DullemondEtal2018; RosottiEtal2020b).

While the radial distribution of pebbles is relatively well-characterized, constraining their vertical distribution presents a greater challenge. Edge-on disks provide ideal conditions for directly measuring the vertical extent of pebbles. For instance, (cite: VillenaveEtal2020) analyzed 12 edge-on protoplanetary disks identified in HST observations using high-resolution ALMA data. They found that at least three of these disks exhibited remarkably thin millimeter dust layers, with scale heights of only a few au at $r = 100$ au. However, edge-on disks obscure the radial structure by definition, making it difficult to simultaneously investigate both radial and vertical distributions.

In contrast, inclined disks allow for a more comprehensive study of both spatial dimensions, though constraining the vertical structure remains indirect. One approach, pioneered by (cite: PinteEtal2016) following the release of ALMA’s high-resolution image of HL Tau (cite: ALMAPartnershipEtal2015), leverages the morphology of gaps. In the presence of a gap, dust above the midplane partially fills the line of sight, making gaps appear shallower along the minor axis than along the major axis. Using this method, they inferred that millimeter-sized dust in HL Tau is located in a geometrically thin layer, with a dust scale height of less than 1 au at the distance of 100 au. A similar technique applied to Oph 163131 (cite: VillenaveEtal2022) revealed an even thinner dust layer, under $0.5$au at 100 au. Expanding this method to the entire DSHARP sample, (cite: PizzatiEtal2023) found that most disks exhibit low dust scale heights ($<4$au at 100 au).

Another method, proposed by (cite: DoiKataoka2021) and applied to HD 163296, relies on azimuthal intensity variations in inclined, axisymmetric rings. For (sub)mm optically thin rings, the optical depth along the line of sight is maximized at the major axis due to projection effects, while it is minimized at the minor axis. Using this technique, (cite: DoiKataoka2021; DoiKataoka2023) found that the dust scale height at the 68 au ring in HD 163296 is almost comparable to the gas scale height, whereas it is an order of magnitude thinner at the 100 au ring, results independently confirmed by (cite: LiuEtal2022y).

Very recently, (cite: VillenaveEtal2025) combined the two approaches described above to perform radiative transfer modeling on a sample of 33 disks, constraining the vertical structure in 23 of them.

In optically thick regimes, a different radiative effect emerges in inclined disks. As noted by (cite: Guerra-AlvaradoEtal2024; Guerra-AlvaradoEtal2024b) and (cite: RibasEtal2024), the far side of an optically thick ring appears brighter due to its larger exposed emitting area. This effect, observed in HL Tau, CIDA 9, and RY Tau, provides an additional means of estimating dust scale heights, particularly in the very inner disk where rings tend to be optically thick.

Combining these observational constraints, a tentative trend emerges: the outer regions of disks, as inferred from edge-on systems, appear razor-thin, whereas the inner disks, indicated by geometrically and optically thick inner walls, are more vertically extended. This suggests a transition in dust scale height across disk radii, but a comprehensive characterization remains challenging due to the limitations of each observational method. To systematically constrain the vertical distribution of pebbles across different disk radii, we focus on modeling the azimuthal intensity variations in a sample of six protoplanetary disks with multiple narrow rings, using publicly available ALMA Band 6 continuum data. Our sample includes AA Tau, LkCa 15, GM Aur, AS 209, HD 163296, and V1094 Sco. As shown in Fig. [1](#fig:continuum_gallery), distinct azimuthal variations are visually identifiable along the major axes of some rings, indicative of a puffed-up geometry. This ring-based approach provides a powerful means of probing dust scale height variations across a large radial distance.

![](fig/continuum_gallery.pdf)

The structure of this manuscript is as follows. In Section [2](#sec:model), we present a simple dust ring model and demonstrate how the dust scale height can be constrained. In Section [3](#sec:data), we explain the target objects and observational data and fit the dust spatial distributions for each disk. The fitting results are presented in Section [4](#sec:results). In Section [5](#sec:discussions), we discuss the implications of our findings for dust trapping, planet formation, and protoplanetary disk evolution. We summarize our results in Section [6](#sec:conclusions).

# Model

The method employed in this work is largely based on the model proposed by (cite: DoiKataoka2021), who measured the vertical dust distribution in the moderately inclined protoplanetary disk HD 163296 by analyzing azimuthal intensity variations in optically thin dust rings. Their approach relies on the fact that an axisymmetric dust ring with finite radial and vertical extents exhibits varying optical depths along the line of sight when inclined. This results in maximum intensity along the major axis and minimum intensity along the minor axis. By comparing these observed azimuthal intensity variations with theoretical models, the dust scale height can be estimated.

To model the intensity variations in the observed rings, we adopt an empirical approach by representing the optical depth distribution with Gaussian profiles in the vertical direction. The distribution of the extinction coefficient $\chi(r, z) \equiv \rho(r, z) \kappa(r,z)$, the product of mass density and opacity, is expressed as: $$\begin{equation}
 \label{eq:dtau}
    \chi(r, z) = \frac{\tau_0 \cos{i}}{\sqrt{2\pi} H_{\mathrm{ring}}} \exp{\left(
    -\frac{(r-r_0)^2}{2 w_{\mathrm{ring}}^2}
    -\frac{z^2}{2 H_{\mathrm{ring}}^2}
    \right)},
\end{equation}$$ where $i$ is the inclination angle of the disk, $z$ is the distance above mid-plane, and $H_{\mathrm{ring}}$ is the dust scale height, representing the vertical extent of the dust layer. The radial distribution of the optical depth is modeled using two half-Gaussian profiles, with $r_0$ denoting the radial location of the ring center, $r$ the distance to the host star, and $w_{\mathrm{ring}}$ representing the ring’s radial width, defined as $$\begin{equation}
    w_{\mathrm{ring}} = \left\{
    \begin{array}{lr}
        w_i & \rm{for}~r < r_0 \\
        w_o & \rm{for}~r > r_0
    \end{array}
    \right.,
\end{equation}$$ to mimic a radially asymmetric ring like some in our sample.

We pragmatically assume that the optical depth at the top of the ring always satisfies $\tau_0 = 0.5$. This assumption is supported by observations from the DSHARP campaign, which found that narrow rings in the DSHARP program typically have optical depths close to this value, referred to as the "fine-tuned" optical depths of the rings (cite: DullemondEtal2018), potentially due to the self-regulation of planetesimal formation (cite: StammlerEtal2019) and/or the following pebble accretion inside the ring (cite: JiangOrmel2023). This choice ensures that our analysis remains within a parameter space where intensity variations are primarily due to the vertical expansion of the rings. Along with this assumption, we also neglect the contribution of scattering, which becomes more significant in the optically thick regime, and might be an alternative explanation for the "fine-tuned" optical depths if the albedo were generally as high as 0.9 (cite: ZhuEtal2019). However, the optically thick ring hypothesis is incompatible with line-of-sight optical depth variation because one never sees through the optically thick ring. Thus, it is beyond the scope of this work. We note that the specific choice of $\tau_0\lesssim1$ will not influence our fitting results on the ring scale height. In a test case, we allow both $\tau_0$ and $T$ to be free parameters, and the conclusions of this work remain unchanged, see Appendix [8](#app:tau_T).

Given the relatively narrow width of the rings, we assume that each ring has a single temperature, $T_{\rm ring}$. Using the optical depth distribution described above, the line-of-sight intensity can be calculated as $$\begin{equation}
    I_{\rm los} = (1-e^{-\tau_{\rm los}}) B_{\nu}(\nu,\,T_{\rm ring})
\end{equation}$$ where $B_{\nu}$ is the full Planck function, and $\tau_{\rm los}$ is the total optical depth-integrated along the line of sight using Eq. ([\[eq:dtau\]](#eq:dtau)). These formulations allow us to model a single ring with 5 free parameters, $T_{\rm ring}$, $r_0$, $w_{i,1}$, $w_{o,1}$, $H_d$, and thus measure the dust scale height of the rings by capturing the intensity variations across the rings, particularly along the major and minor axes.

# Data

We apply our methods to six moderately inclined ($i\simeq35\sim60\degree$) protoplanetary disks for which more than one ring is spatially well resolved in the ALMA Band 6 continuum archival data, see Table [\[tab:disk_parameters\]](#tab:disk_parameters). The 6 disks are the only sample (to our knowledge) with multiple rings, and the required inclination and angular resolution to conduct our analysis. Among these, the fits files for HD 163296 and AS 209 are publicly available from the DSHARP large program (cite: AndrewsEtal2018b; HuangEtal2018b). The data for GM Aur were obtained from (cite: HuangEtal2020j), while the data for LkCa 15 were collected from (cite: LongEtal2022b). For V1094 Sco and AA Tau, we reduced new continuum imaging based on publicly available archival data from programs 2017.1.01167.S (PI: S. Perez) and 2018.1.01829.S (PI: R. Loomis), respectively. V1094 Sco was observed twice with two different antenna configurations, spanning baselines from 15 m to 8.5 km, with a total integration time of $\sim$12 min. The AA Tau data include three long-baseline executions with baselines between 83 m and 16 km, each for $\sim$33 min on-source time, and one shorter-baseline observation for 13 min. After the initial data calibration following the provided pipeline, self-calibration was performed with CASA 6.4.1 starting from the short-baseline data and then for the combined dataset. For each disk, multiple executions were shifted to a common phase center before the combined self-calibration. The final images for V1094 Sco and AA Tau were produced with Briggs weighting parameters of 1 and 2, resulting in beam sizes of $0.074\ensuremath{''}\times0.096\ensuremath{''}$ and $0.061\ensuremath{''}\times0.068\ensuremath{''}$, respectively. The imaging used in this study does not apply primary beam or JvM corrections.[^1] Not applying primary beam correction ensures that the noise remains uniform across each image. This choice is justified because the disk continuum emission is much smaller than the primary beam, so the lack of correction has a negligible impact within the ring regions where our analysis is concentrated. The JvM correction is known to spuriously reduce the RMS noise and potentially overestimate the signal-to-noise ratio of the final image (cite: CasassusCarcamo2022). Therefore, we opted out of using it. See a comparison of analyses with and without the JvM correction for LkCa 15 in Appendix [9](#app:JvM). We measure the rms noise level in the emission-free regions of each image. Specifically, we divide each image into a series of concentric annuli centered on the disk, and calculate the rms deviation within each annulus to construct a radial profile of the rms deviation. We adopt the rms noise level as the median value measured in annuli beyond the emission region, where the radial profile of the rms deviation becomes flat with radius. The resulting rms noise levels are summarized in Table [\[tab:disk_parameters\]](#tab:disk_parameters).

We focus on rings that are radially resolved, have a fitted Gaussian width greater than the beam size, and are sufficiently sharp for our analysis. Specifically, we define a ring as "sharp" if its half-maximum profile can still be well approximated by a Gaussian-like shape in the radial direction. This criterion selects exactly two rings per disk for analysis (see Table [\[tab:best_fit\]](#tab:best_fit), and the images in the top panels of Fig. [2](#fig:continuum_gallery_mod)). To determine the center of each disk image, we apply a 180-degree rotation to the image and subtract the rotated version from the original one. The imaging center is then identified by minimizing the squared residuals of this subtraction. For the position angle (PA) and inclination ($i$), we adopt values from previous studies, as summarized in Table [\[tab:disk_parameters\]](#tab:disk_parameters). Using these geometric parameters, we extract the radial intensity profile for all targets with the *gofish* software package (cite: Teague2019). Our fitting procedure focuses on regions where the azimuthally averaged intensity exceeds half of the ring’s peak value, which defines the masks used in Fig. [2](#fig:continuum_gallery_mod) and the following analysis. The relevant disk geometry parameters are summarized in Table [\[tab:disk_parameters\]](#tab:disk_parameters).

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:---|
| **Target** | $M_\star$ \[$M_\odot$\] | $L_\star$ \[$L_\odot$\] | $d$ \[pc\] | PA \[deg\] | $i$ \[deg\] | $\Delta x$ \[mas\] | $\Delta y$ \[mas\] | $\theta_{\rm beam}$ \[mas\] | $\sigma$ \[K\] | References |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) |
| **AS 209** | 0.8 | 1.4 | 121.2 | 85.2 | 34.5 | -0.2 | -0.3 | $38\times 36$ | 0.29 | II, IV |
| **AA Tau** | 0.8 | 0.8 | 134.7 | 93.3 | 60.6 | -0.9 | 8.1 | $68\times 61$ | 0.11 | I |
| **V1094 Sco** | 0.8 | 1.7 | 154.8 | 109.0 | 55.2 | 3.5 | 7.6 | $96\times 74$ | 0.08 | III |
| **LkCa 15** | 1.2 | 1.1 | 157.2 | 61.9 | 50.2 | -2.8 | 2.5 | $50\times 50$ | 0.09 | VI |
| **GM Aur** | 1.3 | 1.4 | 158.1 | 57.2 | 53.2 | -3.5 | -4.3 | $45\times 25$ | 0.15 | V |
| **HD 163296** | 2.0 | 17 | 101.0 | 133.3 | 46.7 | -6.3 | 10.0 | $48\times 38$ | 0.29 | II, IV |

To estimate the model parameters and their uncertainties, we employ the Markov Chain Monte Carlo (MCMC) method. The log-likelihood function is defined as $$\begin{equation}
\ln \mathcal{L} = -\frac{1}{2} \sum_{\mathrm{mask}} \left( \frac{(I_{\rm obs} - I_{\rm los})^2}{\sigma_{\rm sample}^2} + \ln(2\pi\sigma_{\rm sample}^2) \right).
\end{equation}$$ with $\sigma_{\rm sample} = \sqrt{A_{\rm beam}/A_{\rm pixel}} \times \sigma$, in which $I_{\rm obs} - I_{\rm los}$ is differentials between the observation and the beam-convolved model, $A_{\rm pixel}$ is the pixel area in the sampled image, $A_{\rm beam}$ is the beam area, and $\sigma$ is the rms noise level measured in the emission-free region. Uniform priors are adopted for all parameters, with the additional constraint that all parameters are strictly positive. We utilize the `emcee` package (cite: Foreman-MackeyEtal2013) for MCMC sampling, initializing 32 walkers and running the chains until the autocorrelation time converges, ensuring robust sampling of the posterior distribution. Once convergence is achieved, we discard a number of steps equal to twice the maximum autocorrelation time as burn-in. The estimated parameter values are taken as the 50th percentile of the marginalized posterior distributions, with the 16th and 84th percentiles defining the 1 $\sigma$ uncertainty range, as shown in Table [\[tab:best_fit\]](#tab:best_fit). In addition to the posterior estimates, we compute the maximum likelihood estimator (MLE), which corresponds to the parameter set that maximizes the likelihood function. We note that for the dust scale height, particularly in the outer disk regions, the MLE is below the 16th percentile and close to zero, which happens in 8 out of 12 rings in the 6 disks. In such cases, we take the 84th percentile of the posterior distribution as the upper bound.

The corresponding corner plots are provided in Appendix [7](#app:corner_plot). The intensity profiles of the best-fit models and the corresponding residuals after subtracting the model from the image are shown in Fig. [2](#fig:continuum_gallery_mod).

+:--------------+:--------------------:+:---------------------:+:--------------------:+:--------------------:+:-------------------:+:--------------------:+:---------------------:+:--------------------:+:--------------------:+:----------------:+
|               | Inner Ring                                                                                                       | Outer Ring                                                                                                    |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| **Target**    | $T_1$ \[K\]          | $r_1$ \[au\]          | $w_{i,1}$ \[au\]     | $w_{o,1}$ \[au\]     | $H_{d,1}$ \[au\]    | $T_2$ \[K\]          | $r_2$ \[au\]          | $w_{i,2}$ \[au\]     | $w_{o,2}$ \[au\]     | $H_{d,2}$ \[au\] |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| \(1\)         | \(2\)                | \(3\)                 | \(4\)                | \(5\)                | \(6\)               | \(7\)                | \(8\)                 | \(9\)                | \(10\)               | \(11\)           |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| **AS 209**    | $15.5^{+0.2}_{-0.2}$ | $74.3^{+0.6}_{-0.6}$  | $3.3^{+0.6}_{-0.6}$  | $3.0^{+0.5}_{-0.5}$  | **$<0.8$**          | $13.0^{+0.1}_{-0.1}$ | $119.1^{+0.5}_{-0.5}$ | $2.8^{+0.5}_{-0.5}$  | $5.1^{+0.4}_{-0.4}$  | **$<0.8$**       |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| **AA Tau**    | $22.9^{+0.2}_{-0.1}$ | $42.9^{+0.5}_{-0.5}$  | $8.1^{+0.6}_{-0.6}$  | $10.5^{+0.5}_{-0.5}$ | **$<0.4$**          | $9.5^{+0.2}_{-0.2}$  | $92.9^{+1.4}_{-1.4}$  | $16.7^{+3.5}_{-2.6}$ | $10.1^{+2.2}_{-1.9}$ | **$<0.8$**       |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| **V1094 Sco** | $9.2^{+0.2}_{-0.2}$  | $140.7^{+2.0}_{-2.0}$ | $12.7^{+1.9}_{-1.8}$ | $9.8^{+1.9}_{-1.9}$  | $3.7^{+0.8}_{-1.2}$ | $6.8^{+0.0}_{-0.0}$  | $235.0^{+2.6}_{-2.5}$ | $40.1^{+6.1}_{-5.2}$ | $30.7^{+3.3}_{-3.1}$ | **$<4.3$**       |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| **LkCa 15**   | $23.3^{+0.1}_{-0.1}$ | $68.1^{+0.3}_{-0.3}$  | $6.1^{+0.3}_{-0.3}$  | $6.3^{+0.3}_{-0.3}$  | $1.5^{+0.3}_{-0.4}$ | $14.1^{+0.0}_{-0.0}$ | $99.3^{+0.3}_{-0.3}$  | $9.9^{+0.5}_{-0.5}$  | $11.7^{+0.3}_{-0.3}$ | **$<0.6$**       |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| **GM Aur**    | $38.8^{+0.1}_{-0.1}$ | $37.3^{+0.2}_{-0.2}$  | $4.0^{+0.2}_{-0.2}$  | $12.3^{+0.2}_{-0.2}$ | $1.6^{+0.2}_{-0.2}$ | $20.7^{+0.1}_{-0.1}$ | $84.1^{+0.2}_{-0.2}$  | $6.4^{+0.3}_{-0.3}$  | $6.8^{+0.2}_{-0.2}$  | **$<0.5$**       |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+
| **HD 163296** | $33.1^{+0.2}_{-0.2}$ | $66.5^{+0.3}_{-0.2}$  | $4.2^{+0.3}_{-0.3}$  | $6.0^{+0.2}_{-0.3}$  | $3.0^{+0.1}_{-0.1}$ | $21.0^{+0.2}_{-0.2}$ | $98.6^{+0.3}_{-0.4}$  | $3.0^{+0.4}_{-0.4}$  | $5.9^{+0.3}_{-0.3}$  | **$<0.7$**       |
+---------------+----------------------+-----------------------+----------------------+----------------------+---------------------+----------------------+-----------------------+----------------------+----------------------+------------------+

**Observed Continuum**\
![image](fig/continuum_gallery_mask.pdf)

**Best-Fit Model**\
![image](fig/continuum_gallery_mod.pdf)

**Residuals (Observation - Model)**\
![image](fig/continuum_gallery_res.pdf)

![](fig/az_gallery.pdf)

# Results

Our model achieves a good level of agreement with the observations, as shown Fig. [2](#fig:continuum_gallery_mod). For AS 209 and V1094 Sco, the residuals are overall less than 3 $\sigma$, where $\sigma$ is the rms noise measured in the sky regions far from the disks. In GM Aur and HD 163296 there is a small difference of 5 $\sigma$ between the two sides of the major axis. For HD 163296 this is more pronounced in the residual without modeling the vertical extent of the ring (cite: AndrewsEtal2021). A similar feature appears in LkCa 15, where there appears to be a $\sim\!5$ $\sigma$ intensity difference between the southern and northern halves of the ring. This residual pattern is also present in the Band 7 continuum of the previous observation (cite: LongEtal2022b) and the newly released exoALMA observation (cite: CuroneEtal2025). We speculate on the nature of this low level asymmetry in Sect. [5.1.1](#sec:planet_stir_dust). Finally, the residuals of AA Tau show a pair of nearly symmetrical blobs on either side of the disk, but not on the major axis, as would be expected from the geometry-induced radiative transfer effect we are focusing on. This suggests that this is most likely an intrinsic feature that could be related to the dipper-star nature of AA Tau (cite: BouvierEtal1999), e.g. the misaligned inner disk could potentially cast a shadow on the outer disk (cite: MarinoEtal2015b; BenistyEtal2017). Since the major-minor axis contrast of AA Tau is largely consistent with the beam-smearing effect due to beam convolution alone, suggesting settled dust, the offset axis asymmetries of AA Tau are beyond the scope of this work. Although our analysis is purely based on the 2D ring images, we also present the azimuthal intensity profiles at each ring in Fig. [3](#fig:az_gallery) for reference. Rings with non-zero dust scale height are shown in orange, while those with only upper limits are shown in blue. We note that an oscillatory pattern appears in some of the blue rings, but this is primarily due to non-negligible beam smearing—see, for example, Appendix B of (cite: DoiKataoka2021). We expect that such features would disappear with even higher-resolution observations.

Dust scale heights for the inner rings of four disks (V1094 Sco, LkCa 15, GM Aur, and HD 163296) are well constrained with $H_d/r$ from 0.025 to 0.045, while their corresponding outer rings only have upper limits that are lower than the values derived for the inner component (Table [\[tab:best_fit\]](#tab:best_fit)). Especially, our measurements on HD 163296 are consistent with previous studies by (cite: DoiKataoka2021; DoiKataoka2023) and (cite: LiuEtal2022y). For AS 209 and AA Tau, both the inner and outer rings only have upper limit constraints. And these two disks happened to have the lowest host stellar mass among our sample. In summary, 4 out of 6 disks in our sample show a geometrically thicker inner ring than the outer ring, which is fundamentally different from the usually expected flaring disk geometry (cite: ChiangGoldreich1997), where both the gas scale height and aspect ratio are expected to be higher at larger radii. To quantify the difference between the two rings, we estimate the dust vertical settling efficiency assuming that an equilibrium between dust vertical diffusion and settling has been reached, thus the dust scale height is (cite: YoudinLithwick2007) $$\begin{equation}
    H_d = \sqrt{\frac{\alpha_z}{{\rm St}+\alpha_z}} H_g
\end{equation}$$ where $H_g$ is gas scale height. If the dust is partially settled, i.e., the Stokes number St is larger than the diffusivity coefficient $\alpha_z$, the settling coefficient can be expressed as $$\begin{equation}
\label{eq:alpha_St}
    \frac{\alpha_z}{\rm St} = \left(\frac{H_d}{H_g}\right)^2.
\end{equation}$$ When ${\rm St} \ll \alpha_z$, the dust is fully coupled with gas, the dust scale height $H_d$ will be comparable with the local gas scale height $H_g$. We measure the $H_d$ directly from our modeling.

For gas scale height, assuming that the gas is isothermal and in hydrostatic equilibrium in the vertical direction, we calculate $H_g$ with $$\begin{equation}
    H_g = \frac{c_s}{\Omega_K}
\end{equation}$$ where $\Omega_K = \sqrt{{G M_{\star}}/{r^3}}$ is the Keplerian angular velocity, $G$ is the gravitational constant, and $M_{\star}$ is the stellar mass. And $$\begin{equation}
    c_s = \sqrt{\frac{k_B T}{\mu m_H}}
\end{equation}$$ is the sound speed, where $\mu = 2.3$ is the mean molecular weight, and $m_H$ is the proton mass. A caveat is the gas temperature estimation is very uncertain, therefore, we offer three different temperatures for reference. We firstly estimate the gas scale height $H_g$ using the temperature from our fitting by assuming same temperature for dust and gas. For reference, from a theoretical base, we also give the scale height $H_{g, \rm flaring}$ by assuming simple flaring disk geometry $$\begin{equation}
\label{eq:T_disk}
    T_{\text{disk}}(r) = \left( \frac{\phi L_{\star}}{8 \pi \sigma_{\text{SB}} r^2} \right)^{\frac{1}{4}}
\end{equation}$$ where $L_{\star}$ is the stellar luminosity, $\sigma_{\text{SB}}$ is the Stefan-Boltzmann constant and $\phi=0.02$ is the so-called flaring angle (cite: ChiangGoldreich1997). Meanwhile, driven by the CO isotopologues observation from ALMA, we calculate $H_{g, \rm CO}$ using the empirically estimated mid-plane temperature by fitting the CO isotopologues temperature (cite: LawEtal2021b; LawEtal2023b). Since the three temperatures are close to each other, therefore the differences among $H_g$, $H_{g, \rm flaring}$, and $H_{g, \rm CO}$ are within $30\%$ for all of the rings. The obtained $\alpha_z/{\rm St}$ for each ring is listed in Table [\[tab:cal_results\]](#tab:cal_results). In addition, beside the uncertainty of the gas scale height, it should also be noted the assumption that dust follows Gaussian distributions, in both radial and vertical direction, may not always hold (cite: FromangNelson2009; RiolsLesur2018), which may further complicate the calculation.

For simplicity, we always use $H_g$ in Table [\[tab:cal_results\]](#tab:cal_results) for our calculation. Two disks, GM Aur and HD 163296, stand out with the inner-ring dust scale height almost comparable to the gas scale height, resulting in $\alpha_z/{\rm St}$ estimated to be $\sim0.5$. The dust scale heights of the inner rings of V1094 Sco and LkCa 15 are smaller, but still make up a substantial fraction of the gas scale height, leading to $\alpha_z/{\rm St}~0.1$. Though only upper limits are obtained for the inner dust ring thickness in the remaining two disks AS 209 and AA Tau, their scale heights are smaller than the corresponding gas scale heights, thus $\alpha_z/{\rm St}<0.02$ is constrained for both.

The dust scale heights of the outer rings are $20\%$ of the gas scale height for V1094 Sco and less than $10\%$ of the gas scale height for others, suggesting strong settling with $\alpha_z/{\rm St}<0.04$. Taking a typical St = $0.01$-$0.1$, this implies the vertical diffusivity $\alpha_z<10^{-4}-10^{-3}$ in the outer region of these disks. Regardless of the exact values, in the 4 disks with well-quantified inner disk size heights, the settling coefficient in the inner rings is at least one order of magnitude higher than the outer rings.

We summarize the main results of Table [\[tab:cal_results\]](#tab:cal_results) in the more intuitive Figure [4](#fig:height_sche). where the dust scale heights and radial extents are plotted based on the 50th percentiles in Table [\[tab:best_fit\]](#tab:best_fit), with the well-constrained ring colored orange and the upper-bounded ring colored blue. The radial and vertical extents are scaled 1:1 in each box. A solid line corresponding to the gas scale height under the assumption of a simple flaring disk Eq. ([\[eq:T_disk\]](#eq:T_disk)) is plotted for reference.

**Both rings settled**\
![image](fig/as209_sche.pdf) ![image](fig/aatau_sche.pdf) **Inner rings puffed-up, outer rings settled**\
![image](fig/v1094sco_sche.pdf) ![image](fig/lkca15_sche.pdf) ![image](fig/gmaur_sche.pdf) ![image](fig/hd163296_sche.pdf)

+:--------------+:-------------------:+:------------:+:---------------------------:+:----------------------:+:-------------------:+:--------------:+:------------:+:---------------------------:+:----------------------:+:-------------------:+:-----:+
|               | Inner Ring                                                                                                      | Outer Ring                                                                                                 | $C$   |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+       |
| **Target**    | $H_{d}$ \[au\]      | $H_g$ \[au\] | $H_{g, \rm flaring}$ \[au\] | $H_{g, \rm CO}$ \[au\] | $\alpha_z/{\rm St}$ | $H_{d}$ \[au\] | $H_g$ \[au\] | $H_{g, \rm flaring}$ \[au\] | $H_{g, \rm CO}$ \[au\] | $\alpha_z/{\rm St}$ |       |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+
| \(1\)         | \(2\)               | \(3\)                                                               | \(4\)               | \(5\)          | \(6\)                                                               | \(7\)               | \(8\) |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+
| **AS 209**    | **$<0.8$**          | 5.7          | 5.7                         | 7.4                    | $<2\times10^{-2}$   | **$<0.8$**     | 10.5         | 10.3                        | 14.4                   | $<6\times10^{-3}$   | \-    |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+
| **AA Tau**    | **$<0.4$**          | 3.1          | 2.7                         | \-                     | $<2\times10^{-2}$   | **$<0.8$**     | 6.2          | 7.0                         | \-                     | $<2\times10^{-2}$   | \-    |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+
| **V1094 Sco** | $3.7^{+0.8}_{-1.2}$ | 11.5         | 13.0                        | \-                     | $1\times10^{-1}$    | **$<4.3$**     | 21.2         | 24.8                        | \-                     | $<4\times10^{-2}$   | $>3$  |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+
| **LkCa 15**   | $1.5^{+0.3}_{-0.4}$ | 5.0          | 4.0                         | 5.0                    | $9\times10^{-2}$    | **$<0.6$**     | 6.8          | 6.5                         | 8.3                    | $<8\times10^{-3}$   | $>12$ |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+
| **GM Aur**    | $1.6^{+0.2}_{-0.2}$ | 2.5          | 1.9                         | 1.8                    | $4\times10^{-1}$    | **$<0.5$**     | 6.2          | 5.1                         | 6.1                    | $<7\times10^{-3}$   | $>63$ |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+
| **HD 163296** | $3.0^{+0.1}_{-0.1}$ | 4.4          | 4.3                         | 3.9                    | $5\times10^{-1}$    | **$<0.7$**     | 6.4          | 7.0                         | 6.8                    | $<1\times10^{-2}$   | $>38$ |
+---------------+---------------------+--------------+-----------------------------+------------------------+---------------------+----------------+--------------+-----------------------------+------------------------+---------------------+-------+

# Discussions

## Potential origin for radial-varying dust scale heights

The radial variation in dust vertical distribution observed across V1094 Sco, LkCa 15, GM Aur, and HD 163296 reveals a consistent pattern: inner rings exhibit vertically extended dust layers comparable to the gas scale height, while outer rings show highly settled dust distributions with sub-au scale heights. This dichotomy implies a factor of 10–100 difference in vertical mixing efficiency between the two rings whose radii are roughly different only by a factor of 2.

Two explanations, or perhaps a combination of both can explain this dichotomy: (1) localized turbulence enhancement (increased $\alpha_z$) in inner rings, or (2) radial variation in pebble sizes (larger Stokes numbers $\rm St$ in outer rings could enhance settling). The latter is somehow not natural, as typically, one would expect grain growth to be more efficient at closer orbits (cite: BirnstielEtal2012). In addition, multi-wavelength studies show smooth grain size distributions across disk radii (cite: MaciasEtal2021; SierraEtal2021; GuidiEtal2022), with no significant growth gradients within rings (cite: JiangEtal2024). While higher gas surface densities in inner rings could reduce $\rm St$ for fixed grain sizes, existing gas density profiles from thermo-chemical modeling (cite: ZhangEtal2021k) lack the required factor of $\sim40–60$ variation to explain the observed settling differences in at least GM Aur and HD 163296.

To quantify these constraints, we consider a fragmentation limited regime of dust growth (cite: BirnstielEtal2011; JiangEtal2024) $$\begin{equation}
    {\rm St} = \frac{1}{3}\frac{v_{\rm frag}^2}{\delta_{\rm frag}c_s^2} = \frac{1}{3}\frac{v_{\rm frag}^2\mu m_H}{\delta_{\rm frag}k_BT}.
\end{equation}$$ where $v_{\rm frag}$ is the fragmentation velocity. Assuming constant $v_{\rm frag}$ between rings, and vertical diffusion dominate the mutual collision velocity among pebbles, $\delta_{\rm frag} = \alpha_z$, the ratio of diffusivities becomes $$\begin{equation}
    \frac{\alpha_{z,1}}{\alpha_{z,2}} = \sqrt{\frac{\alpha_{z,1}}{\alpha_{z,2}}\frac{\text{St}_2}{\text{St}_1}\frac{T_2}{T_1}} \equiv \sqrt{C\frac{T_2}{T_1}}, 
\end{equation}$$ where $C\equiv \frac{\alpha_{z,1}}{\alpha_{z,2}}\frac{\text{St}_2}{\text{St}_1}$. Our measurement constrain the lower limit of $C\gtrsim10-100$ (Table [\[tab:cal_results\]](#tab:cal_results)). The temperature ratio $T_2/T_1$ for outer/inner rings in our sample ranges from $0.5–0.7$, insufficient to explain the observed $C$ values if diffusivity constant. This strongly favors scenario where enhanced turbulent diffusion in inner rings is larger than the outer ring by at least one magnitude. In the following discussions, we discuss potential origin of such a radial-dependent dust diffusivity.

### Stirring up by planet

3D hydro-dynamical simulations have shown that the planet, as a perturber, can physically raise the dust scale height in its vicinity, leading to a puffed-up dust ring outside its orbit (cite: BiEtal2021; BinkertEtal2021; BinkertEtal2023), where the dust scale height can reach up to 70% of the gas scale height, equivalent to introducing a diffusion coefficient of $\delta\sim10^{-2}$ by the planet. This puffing-up is mainly due to planet-induced meridional gas flows (cite: SzulagyiEtal2014; FungChiang2016), thus the strength of the induced diffusion would depend on the mass of the potential planet, which is typically required to be larger than the thermal mass $M_{\rm th} = (H_g/r)^3 M_\star$. As the disk aspect ratio $H_g/r$ is 0.06 to 0.07 at the inner ring location for all four disks, this would suggest that a planet more massive than Saturn mass is responsible for stirring up the inner ring in these disks.

This explanation is particularly interesting for the transition disks of LkCa 15 and GM Aur, where the dust is depleted inside the inner ring, and the large dust cavity has long been thought to be related to planet-disk interactions (cite: ZhuEtal2011). For HD 163296, an arc-like feature appears in the gap immediately interior to the inner ring, which could be due to planet-induced vortex (cite: IsellaEtal2018; Garrido-DeutelmoserEtal2023). In addition, the three disks show low-level asymmetries in the residual map of Fig. [2](#fig:continuum_gallery_mod), after subtracting our best-fit model, as we noted in Sect. [3](#sec:data). In LkCa 15 and GM Aur, the south-west side, and HD 163296 the north-west side, of the disk show a slightly higher flux $\sim\!5-10\,\sigma$ with respect to the physically axisymmetric model. This could be due to either the planet-induced dust stirring being azimuthally asymmetric (cite: BinkertEtal2023), or the dust being concentrated differently in azimuth into small-scale vortex (cite: HammerEtal2021). Finally, we note that in LkCa 15, (cite: LongEtal2022b) proposed a protoplanet based on the potential dust trapping in its L4 and L5 Lagrange point; whether such a planet can reproduce all the above features would deserve further investigations.

### Second generation pebble by high inclination planetesimal collision

These puffed-up dust could also be secondary products of planetesimal-planetesimal collisions, as in debris disks, instead of being “primordial pebbles”. This scenario may not require the presence of a planet. In gas-rich protoplanetary disks, since the gas drag damping is still very strong for small bodies (cite: AdachiEtal1976), it would take too long to develop a detectable tilt based on planetesimal-planetesimal self-scattering within the disk age (cite: Ida1990). Yet, a plausible solution could again be planet-planetesimal stirring. That is, early formed planetesimals inside the ring can be dynamically perturbed by newly formed planets (cite: IdaMakino1993). The high aspect ratio observed in the ring could reflect a high mean inclination of unseen planetesimals (cite: Matr‘aEtal2019). However, a protoplanet leading to a mean inclination as high as 0.06 to 0.07 would have to be more massive than $\sim\!i^3 M_\star$, thus again in the range of Saturn to Jupiter mass. Whether such a planet could perturb the planetesimals secularly without destroying the circular ring remains as an open question.

Nevertheless, this scenario will be particularly interesting since (cite: TestiEtal2022) found that the disk millimeter flux seems to increase during the first 1-2 Myr of disk evolution. Following this, (cite: Bernab‘oEtal2022) have proposed that this trend could be explained by the early formation of planets, which dynamically stirs the nearby planetesimals, producing second-generation dust. If this were true, the difference between the inner and outer rings could be due to the difference in orbital dynamical timescales, since both planetesimal formation and inclination stirring take longer in larger orbital distances.

### Radially dependent turbulence activation

The fact that the observed feature of more puffed-up inner rings is common to 4 out of 6 disks in our sample could be an indication that they are not all due to potentially massive planets, which are inherently rare (cite: FernandesEtal2019; ZhuDong2021). Without invoking planets, an additional possibility would be that our results reflect the intrinsic radial variation in vertical turbulence of the disks.

Indeed, the vertical shear instability (VSI), as one of the most promising sources of turbulence in protoplanetary disks, can lift even large particles with St $\simeq0.1$-1 to a substantial fraction of the gas pressure scale height (cite: DullemondEtal2022). Meanwhile, the VSI is known to have a strong radial dependence due to its high sensitivity to the thermal relaxation timescale (cite: FukuharaEtal2021; PfeilEtal2023). Thus, within protoplanetary disks with typical parameters, the VSI is more likely to be activated in the inner disk. And it may never develop, or runaway settling may occur in the outer region of protoplanetary disks (cite: FukuharaOkuzumi2024; PfeilEtal2024; ZhangEtal2024s). In this context, for the 4 disks with puffed-up inner ring and settled outer ring, the inner ring will be VSI unstable, while the outer rings are all stable against VSI.

## Comparison with other works

Constraining the vertical extent of protoplanetary disks is an active area of research. As a direct comparison, several studies employing methods similar to ours have focused on HD 163296 (cite: DoiKataoka2021; DoiKataoka2023; LiuEtal2022y). Their results are in reasonable agreement with ours, consistently constraining the scale height of the inner ring to between 3 and 4.3au. Minor differences in the derived values may stem from the choice of fitting regions. For example, (cite: DoiKataoka2023) excluded the southern wedge of the disk—where a strong asymmetric arc is present—from their default model, which may have led to a higher inferred dust scale height. This is consistent with our observation that the northern side of the disk shows slightly higher contrast. For the outer ring, all works—including ours—only provide upper limits, consistently below 1 au.

Using a different approach based on the gap-filling effect first introduced by (cite: PinteEtal2016), (cite: PizzatiEtal2023) constrained the dust scale height for the full DSHARP sample, including HD 163296 and AS 209, for which the same ALMA datasets were used as our study. Rather than focusing on localized structures, their method models the global image residuals based on radial profiles derived from visibility fitting, assuming a flared disk geometry. As a result, they report an upper limit of $\sim$2 au for AS 209 and a scale height of $\sim$4 au for HD 163296 at 100 au. The constraint for AS 209 is broadly consistent with our findings (both rings $<$0.8 au), though their upper limit is less stringent. For HD 163296, their method does not account for local variations and may be biased by the puffed-up inner ring at 67 au, potentially leading to an overestimate of the scale height at 100 au.

More recently, (cite: VillenaveEtal2025) perform radiative transfer modeling on a larger sample of 33 disks and constrained the vertical structure in 23 of them, the majority of which resulted in upper limits. All six disks analyzed in our study are also included in theirs. However, due to the different modeling framework—e.g., (a) considering only four discrete levels of dust mixing, resulting in a sparse prior space; and (b) relying on multiple steps of visual inspection—their constraints are generally less stringent. For example, in GM Aur—which is included in both studies—our analysis reveals a non-zero scale height for the inner ring and a more settled outer ring, whereas they report only an upper limit of $<$1.6 au for the entire disk, despite using the same dataset. Similarly, for HD 163296, we provide precise constraints of $3.0^{+0.1}_{-0.1}$ au on the inner ring scale height, while their result spans a wide range from 0.4 to 4.5 au—this being the only case in which they report a range rather than an upper or lower limit. In cases where both studies report upper limits, ours are generally tighter.

We also note two discrepancies between our results and theirs for LkCa 15 and V1094 Sco. In both cases, they report a lower limit for the inner ring scale height and an upper limit for the outer ring. However, their lower limits exceed the scale heights we derive. Furthermore, the upper limit they report for the outer ring in LkCa 15 is an order of magnitude shallower than ours ($<4.9$ au v.s. $<0.4$ au in our work), while for V1094 Sco it is about twice shallower. The origin of these discrepancies is unclear, but may stem from a combination of lower data quality and model limitations in their analysis. Specifically, for instance, in the case of LkCa 15, the reconstructed image in (cite: VillenaveEtal2025) was produced using data from ALMA program 2018.1.01255.S (PI: M. Benisty) only, which covers baselines from 59 to 12,644 meters with a total on-source time of 105 minutes across three executions. In contrast, the image used in this work combines data from 11 executions—including the three used by (cite: VillenaveEtal2025)—for a total on-source time of 265 minutes and a broader baseline coverage from 15 to 13,894 meters (cite: LongEtal2022b). Meanwhile, (cite: VillenaveEtal2025) derive turbulence parameters by assuming fixed dust size distributions and gas-to-dust ratios. This approach facilitates direct physical interpretation, but is less flexible when it comes to quantifying dust scale heights. Our analysis, in contrast, constrains the vertical dust distribution directly from geometry without assuming specific physical parameters, while additional steps are needed to derive turbulence levels. Nonetheless, we emphasize that these two approaches are complementary. Our method requires very high-quality data to fully resolve the ring structures in order to achieve the accuracy needed for our MCMC-based framework, and lack of realistic radiative transfer modeling. In contrast, the radiative transfer modeling approach remains applicable even when rings are only partially resolved, and is capable of capturing features not only in the ring but also within the gap region.

## Double ring formation

To explore the radial variation of dust scale height, disks with multiple rings are selected. Whether multiple mechanisms are required to create those rings in each disk is still highly debated. If an inner companion is present in the disk, it will naturally carve a gap and form a puffed-up inner ring. Similarly, if the Vertical Shear Instability (VSI) is active within a certain radius but inactive beyond it, the resulting turbulence transition can facilitate dust accumulation, analogous to the inner edge of the dead zone (cite: UedaEtal2019). Once a puffed-up inner ring forms, it casts a shadow on the outer disk, leading to two key effects that promote the formation of a pressure bump outside the ring. First, the shadow induces a temperature drop. Second, the concentration of pebbles at the inner ring enhances radiative cooling at its location, which has been shown to generate a secondary pressure bump just beyond the primary ring (cite: ZhangEtal2021s). When combined with shadowing effects, this mechanism may become even more pronounced. Consequently, the formation of a settled outer ring could be a direct outcome of the puffed-up inner ring, potentially explaining the high occurrence rate of differential dust scale heights we observe. Interestingly, the near-IR polarized light of HD 163296, LkCa 15 and GM Aur is only observed up to their inner pebble ring locations, which is consistent with our results of puffed-up inner rings that shadow the outer disk region, see Appendix [10](#app:mm_nir).

## Planet formation

Both planetesimal formation and pebble accretion prefer more settled dust disks (cite: OrmelLiu2018; LimEtal2024). Although dust rings have been suggested to be a promising site for planet formation (cite: Morbidelli2020; JiangOrmel2023), the conditions for planetesimal formation have to be met in the first place. Indeed, combining the available gas properties from the CO isotopologue and jointly modeling the dust with the dust settling coefficient, (cite: ZagariaEtal2023) suggest that the inner ring of HD 163296 is stable against streaming instability (SI), while the clumping could take place under the effect of SI in the outer ring.

After the formation of the planetesimal, the growth of the planetesimals to the planetary core also depends on the settling of the pebbles. In the inner rings, core formation by pebble accretion could be largely suppressed due to the turbulent nature of the inner rings. It is therefore possible that instead of the inner region of the disks, the formation of giant planetary cores favors the outer VSI stable region.

The formation of giant planetary cores in the far-out regions will have several implications on planetary and disk compositions. First, planetary cores built in this environment will be composed of large amounts of volatile ices which are otherwise absent in the inner warm region of disks (cite: BosmanEtal2023). After the planetary cores migrate inward and grow, they will end up with a significantly different composition than if it was formed in-situ in the inner disk. Second, a core formed in the cold outer region can undergo sufficient gas accretion, which will raise the local temperature, causing the release of the icy volatiles in the outer disk. This could explain the elevated C/O in the outer disks (cite: JiangEtal2023). Finally, the preferred planetesimal formation in the outer disks would suggest that the left-over planetesimal belt, which serves as debris disk belt after the gas disk dissipates (cite: JiangOrmel2021; NajitaEtal2022), will statistically have an overall larger radii than rings in protoplanetary disks. Recently, such a trend is suggested based on a large sample of debris disks from the REsolved ALMA and SMA Observations of Nearby Stars (REASONS) program (cite: Matr‘aEtal2025).

# Conclusions

In this work, we have constrained the vertical distribution of pebbles in six double-ring protoplanetary disks, using high-resolution ALMA Band 6 continuum observations. By modeling the azimuthal intensity variations, we found that, in 4 out of 6 disks, inner rings tend to exhibit puffed-up dust layers, while outer rings are significantly more settled with dust scale heights less than 20% of the gas scale height. This dichotomy suggests a radial dependence in dust settling efficiency, which we attribute to localized planetary interactions with pebbles/planetesimals, global radial dependence of turbulence induced by VSI or a combination of both.

This radial variation in dust settling efficiency has important implications for planet formation. On the one hand, the puffed-up inner rings may indicate the presence of massive planets stirring the planetesimals and the dust. On the other hand, as regions where turbulence is suppressed, the highly settled outer rings potentially facilitate planetesimal formation through mechanisms such as streaming instability, providing favorable conditions for pebble accretion and the growth of planetary cores.

Furthermore, our results suggest that the formation of double-ring structures may be linked to the differential settling of dust, with inner rings acting as sources of shadows and exclusive cooling that influence the formation of outer rings. This has implications for the evolution of protoplanetary disks and the distribution of solids available for planet formation, and may reflect in scatter-light imaging.

As a pilot study, our analysis highlights the potential of studying vertical dust distribution in protoplanetary disks in a larger sample, and underscores the need for further observational and theoretical studies to unravel the complex interplay between dust dynamics, turbulence, and planet formation.

# Acknowledgements

We thank the anonymous referee for their time. H.J. acknowledges the support for his secondment to the University of Arizona provided by the EU Horizon 2020 research and innovation programme, Marie Sklodowska-Curie grant agreement NO 823 823 (Dustbusters RISE project). This project has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them. Support for F.L. was provided by NASA through the NASA Hubble Fellowship grant #HST-HF2-51512.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS5-26555. S.P. acknowledges support from FONDECYT 1231663 and ANID – Millennium Science Initiative Program – Center Code NCN2024_001. Support for S.Z. was provided by NASA through the NASA Hubble Fellowship grant #HST-HF2-51568 awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS5-26555.

This paper makes use of the following ALMA data: 2015.1.00118.S, 2016.1.00484.L, 2017.1.01151.S, 2017.1.01167.S, 2018.1.00945.S, 2018.1.01255.S, and 2018.1.01829.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

ALMA, VLT/SPHERE

# Software

`CASA` (cite: CASATeamEtal2022), `gofish` (cite: Teague2019) `numpy` (cite: HarrisEtal2020), `matplotlib` (cite: Hunter2007), `scipy` (cite: VirtanenEtal2020), `astropy` (cite: AstropyCollaborationEtal2013)

# MCMC

In this section, we present the corner plots derived from the MCMC sampling for all targets. The maximum likelihood estimators (MLE) of each parameter are indicated by solid lines, and the 16th, 50th, and 84th percentiles of the posterior distributions are marked by dashed lines. The MLEs of the dust scale height are close to zero in the outer rings for all targets, as well as in the inner rings of AA Tau and AS 209, for which, our fitting sets up the upper limit estimation.

![](fig/as209_band6_new_rr.pdf)

![](fig/aatau_band6_new_rr.pdf)

![](fig/v1094sco_band6_new_rr.pdf)

![](fig/lkca15_band6_new_rr.pdf)

![](fig/gmaur_band6_new_rr.pdf)

![](fig/hd163296_band6_new_rr.pdf)

natexlab

(ref: AdachiEtal1976) Adachi, I., Hayashi, C., & Nakazawa, K. 1976, Progress of Theoretical Physics, 56, 1756, doi: [`10.1143/PTP.56.1756`](http://doi.org/10.1143/PTP.56.1756)

(ref: ALMAPartnershipEtal2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: AndrewsEtal2018b) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: AndrewsEtal2021) Andrews, S. M., Elder, W., Zhang, S., et al. 2021, ApJ, 916, 51, doi: [`10.3847/1538-4357/ac00b9`](http://doi.org/10.3847/1538-4357/ac00b9)

(ref: AstropyCollaborationEtal2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: BenistyEtal2017) Benisty, M., Stolker, T., Pohl, A., et al. 2017, A&A, 597, A42, doi: [`10.1051/0004-6361/201629798`](http://doi.org/10.1051/0004-6361/201629798)

(ref: Bernab‘oEtal2022) Bernabò, L. M., Turrini, D., Testi, L., Marzari, F., & Polychroni, D. 2022, ApJL, 927, L22, doi: [`10.3847/2041-8213/ac574e`](http://doi.org/10.3847/2041-8213/ac574e)

(ref: BiEtal2021) Bi, J., Lin, M.-K., & Dong, R. 2021, ApJ, 912, 107, doi: [`10.3847/1538-4357/abef6b`](http://doi.org/10.3847/1538-4357/abef6b)

(ref: BinkertEtal2021) Binkert, F., Szulágyi, J., & Birnstiel, T. 2021, MNRAS, 506, 5969, doi: [`10.1093/mnras/stab2075`](http://doi.org/10.1093/mnras/stab2075)

(ref: BinkertEtal2023) —. 2023, MNRAS, 523, 55, doi: [`10.1093/mnras/stad1405`](http://doi.org/10.1093/mnras/stad1405)

(ref: BirnstielEtal2012) Birnstiel, T., Klahr, H., & Ercolano, B. 2012, A&A, 539, A148, doi: [`10.1051/0004-6361/201118136`](http://doi.org/10.1051/0004-6361/201118136)

(ref: BirnstielEtal2011) Birnstiel, T., Ormel, C. W., & Dullemond, C. P. 2011, A&A, 525, A11, doi: [`10.1051/0004-6361/201015228`](http://doi.org/10.1051/0004-6361/201015228)

(ref: BosmanEtal2023) Bosman, A. D., Appelgren, J., Bergin, E. A., Lambrechts, M., & Johansen, A. 2023, ApJL, 944, L53, doi: [`10.3847/2041-8213/acb651`](http://doi.org/10.3847/2041-8213/acb651)

(ref: BouvierEtal1999) Bouvier, J., Chelli, A., Allain, S., et al. 1999, A&A, 349, 619

(ref: CASATeamEtal2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: CasassusCarcamo2022) Casassus, S., & Cárcamo, M. 2022, MNRAS, 513, 5790, doi: [`10.1093/mnras/stac1285`](http://doi.org/10.1093/mnras/stac1285)

(ref: ChiangGoldreich1997) Chiang, E. I., & Goldreich, P. 1997, ApJ, 490, 368, doi: [`10.1086/304869`](http://doi.org/10.1086/304869)

(ref: CuroneEtal2025) Curone, P., Facchini, S., Andrews, S. M., et al. 2025, ApJL, 984, L9, doi: [`10.3847/2041-8213/adc438`](http://doi.org/10.3847/2041-8213/adc438)

(ref: CzekalaEtal2021) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2, doi: [`10.3847/1538-4365/ac1430`](http://doi.org/10.3847/1538-4365/ac1430)

(ref: DoiKataoka2021) Doi, K., & Kataoka, A. 2021, ApJ, 912, 164, doi: [`10.3847/1538-4357/abe5a6`](http://doi.org/10.3847/1538-4357/abe5a6)

(ref: DoiKataoka2023) —. 2023, ApJ, 957, 11, doi: [`10.3847/1538-4357/acf5df`](http://doi.org/10.3847/1538-4357/acf5df)

(ref: DullemondEtal2022) Dullemond, C. P., Ziampras, A., Ostertag, D., & Dominik, C. 2022, A&A, 668, A105, doi: [`10.1051/0004-6361/202244218`](http://doi.org/10.1051/0004-6361/202244218)

(ref: DullemondEtal2018) Dullemond, C. P., Birnstiel, T., Huang, J., et al. 2018, ApJL, 869, L46, doi: [`10.3847/2041-8213/aaf742`](http://doi.org/10.3847/2041-8213/aaf742)

(ref: FernandesEtal2019) Fernandes, R. B., Mulders, G. D., Pascucci, I., Mordasini, C., & Emsenhuber, A. 2019, ApJ, 874, 81, doi: [`10.3847/1538-4357/ab0300`](http://doi.org/10.3847/1538-4357/ab0300)

(ref: Foreman-MackeyEtal2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: FromangNelson2009) Fromang, S., & Nelson, R. P. 2009, A&A, 496, 597, doi: [`10.1051/0004-6361/200811220`](http://doi.org/10.1051/0004-6361/200811220)

(ref: FukuharaOkuzumi2024) Fukuhara, Y., & Okuzumi, S. 2024, PASJ, 76, 708, doi: [`10.1093/pasj/psae042`](http://doi.org/10.1093/pasj/psae042)

(ref: FukuharaEtal2021) Fukuhara, Y., Okuzumi, S., & Ono, T. 2021, ApJ, 914, 132, doi: [`10.3847/1538-4357/abfe5c`](http://doi.org/10.3847/1538-4357/abfe5c)

(ref: FungChiang2016) Fung, J., & Chiang, E. 2016, ApJ, 832, 105, doi: [`10.3847/0004-637X/832/2/105`](http://doi.org/10.3847/0004-637X/832/2/105)

(ref: GaiaCollaboration2020) Gaia Collaboration. 2020, VizieR Online Data Catalog: Gaia EDR3 (Gaia Collaboration, 2020), VizieR On-line Data Catalog: I/350. Originally published in: 2021A&amp;A...649A...1G, doi: [`10.26093/cds/vizier.1350`](http://doi.org/10.26093/cds/vizier.1350)

(ref: Garrido-DeutelmoserEtal2023) Garrido-Deutelmoser, J., Petrovich, C., Charalambous, C., Guzmán, V. V., & Zhang, K. 2023, ApJL, 945, L37, doi: [`10.3847/2041-8213/acbea8`](http://doi.org/10.3847/2041-8213/acbea8)

(ref: Guerra-AlvaradoEtal2024) Guerra-Alvarado, O. M., van der Marel, N., Di Francesco, J., et al. 2024a, A&A, 681, A82, doi: [`10.1051/0004-6361/202347685`](http://doi.org/10.1051/0004-6361/202347685)

(ref: Guerra-AlvaradoEtal2024b) Guerra-Alvarado, O. M., Carrasco-González, C., Macı́as, E., et al. 2024b, A&A, 686, A298, doi: [`10.1051/0004-6361/202349046`](http://doi.org/10.1051/0004-6361/202349046)

(ref: GuidiEtal2022) Guidi, G., Isella, A., Testi, L., et al. 2022, A&A, 664, A137, doi: [`10.1051/0004-6361/202142303`](http://doi.org/10.1051/0004-6361/202142303)

(ref: HammerEtal2021) Hammer, M., Lin, M.-K., Kratter, K. M., & Pinilla, P. 2021, MNRAS, 504, 3963, doi: [`10.1093/mnras/stab1079`](http://doi.org/10.1093/mnras/stab1079)

(ref: HarrisEtal2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: HuangEtal2018b) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: HuangEtal2020j) —. 2020, ApJ, 891, 48, doi: [`10.3847/1538-4357/ab711e`](http://doi.org/10.3847/1538-4357/ab711e)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Ida1990) Ida, S. 1990, Icarus, 88, 129, doi: [`10.1016/0019-1035(90)90182-9`](http://doi.org/10.1016/0019-1035(90)90182-9)

(ref: IdaMakino1993) Ida, S., & Makino, J. 1993, Icarus, 106, 210, doi: [`10.1006/icar.1993.1167`](http://doi.org/10.1006/icar.1993.1167)

(ref: IsellaEtal2018) Isella, A., Huang, J., Andrews, S. M., et al. 2018, ApJL, 869, L49, doi: [`10.3847/2041-8213/aaf747`](http://doi.org/10.3847/2041-8213/aaf747)

(ref: JiangEtal2024) Jiang, H., Macı́as, E., Guerra-Alvarado, O. M., & Carrasco-González, C. 2024, A&A, 682, A32, doi: [`10.1051/0004-6361/202348271`](http://doi.org/10.1051/0004-6361/202348271)

(ref: JiangOrmel2021) Jiang, H., & Ormel, C. W. 2021, MNRAS, 505, 1162, doi: [`10.1093/mnras/stab1278`](http://doi.org/10.1093/mnras/stab1278)

(ref: JiangOrmel2023) —. 2023, MNRAS, 518, 3877, doi: [`10.1093/mnras/stac3275`](http://doi.org/10.1093/mnras/stac3275)

(ref: JiangEtal2023) Jiang, H., Wang, Y., Ormel, C. W., Krijt, S., & Dong, R. 2023, A&A, 678, A33, doi: [`10.1051/0004-6361/202346637`](http://doi.org/10.1051/0004-6361/202346637)

(ref: JohansenEtal2009) Johansen, A., Youdin, A., & Mac Low, M.-M. 2009, ApJL, 704, L75, doi: [`10.1088/0004-637X/704/2/L75`](http://doi.org/10.1088/0004-637X/704/2/L75)

(ref: LambrechtsJohansen2012) Lambrechts, M., & Johansen, A. 2012, A&A, 544, A32, doi: [`10.1051/0004-6361/201219127`](http://doi.org/10.1051/0004-6361/201219127)

(ref: LawEtal2021b) Law, C. J., Teague, R., Loomis, R. A., et al. 2021, ApJS, 257, 4, doi: [`10.3847/1538-4365/ac1439`](http://doi.org/10.3847/1538-4365/ac1439)

(ref: LawEtal2023b) Law, C. J., Teague, R., Öberg, K. I., et al. 2023, ApJ, 948, 60, doi: [`10.3847/1538-4357/acb3c4`](http://doi.org/10.3847/1538-4357/acb3c4)

(ref: LimEtal2024) Lim, J., Simon, J. B., Li, R., et al. 2024, ApJ, 969, 130, doi: [`10.3847/1538-4357/ad47a2`](http://doi.org/10.3847/1538-4357/ad47a2)

(ref: LiuOrmel2018) Liu, B., & Ormel, C. W. 2018, A&A, 615, A138, doi: [`10.1051/0004-6361/201732307`](http://doi.org/10.1051/0004-6361/201732307)

(ref: LiuEtal2022y) Liu, Y., Bertrang, G. H. M., Flock, M., et al. 2022, Science China Physics, Mechanics, and Astronomy, 65, 129511, doi: [`10.1007/s11433-022-1982-y`](http://doi.org/10.1007/s11433-022-1982-y)

(ref: LongEtal2018f) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17, doi: [`10.3847/1538-4357/aae8e1`](http://doi.org/10.3847/1538-4357/aae8e1)

(ref: LongEtal2022b) Long, F., Andrews, S. M., Zhang, S., et al. 2022, ApJL, 937, L1, doi: [`10.3847/2041-8213/ac8b10`](http://doi.org/10.3847/2041-8213/ac8b10)

(ref: LoomisEtal2017) Loomis, R. A., Öberg, K. I., Andrews, S. M., & MacGregor, M. A. 2017, ApJ, 840, 23, doi: [`10.3847/1538-4357/aa6c63`](http://doi.org/10.3847/1538-4357/aa6c63)

(ref: LoomisEtal2025) Loomis, R. A., Facchini, S., Benisty, M., et al. 2025, ApJL, 984, L7, doi: [`10.3847/2041-8213/adc43a`](http://doi.org/10.3847/2041-8213/adc43a)

(ref: MaciasEtal2021) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33, doi: [`10.1051/0004-6361/202039812`](http://doi.org/10.1051/0004-6361/202039812)

(ref: MarinoEtal2015b) Marino, S., Perez, S., & Casassus, S. 2015, ApJL, 798, L44, doi: [`10.1088/2041-8205/798/2/L44`](http://doi.org/10.1088/2041-8205/798/2/L44)

(ref: Matr‘aEtal2019) Matrà, L., Wyatt, M. C., Wilner, D. J., et al. 2019, AJ, 157, 135, doi: [`10.3847/1538-3881/ab06c0`](http://doi.org/10.3847/1538-3881/ab06c0)

(ref: Matr‘aEtal2025) Matrà, L., Marino, S., Wilner, D. J., et al. 2025, A&A, 693, A151, doi: [`10.1051/0004-6361/202451397`](http://doi.org/10.1051/0004-6361/202451397)

(ref: Morbidelli2020) Morbidelli, A. 2020, A&A, 638, A1, doi: [`10.1051/0004-6361/202037983`](http://doi.org/10.1051/0004-6361/202037983)

(ref: NajitaEtal2022) Najita, J. R., Kenyon, S. J., & Bromley, B. C. 2022, ApJ, 925, 45, doi: [`10.3847/1538-4357/ac37b6`](http://doi.org/10.3847/1538-4357/ac37b6)

(ref: NakagawaEtal1986) Nakagawa, Y., Sekiya, M., & Hayashi, C. 1986, Icarus, 67, 375, doi: [`10.1016/0019-1035(86)90121-1`](http://doi.org/10.1016/0019-1035(86)90121-1)

(ref: OrmelCuzzi2007) Ormel, C. W., & Cuzzi, J. N. 2007, A&A, 466, 413, doi: [`10.1051/0004-6361:20066899`](http://doi.org/10.1051/0004-6361:20066899)

(ref: OrmelKlahr2010) Ormel, C. W., & Klahr, H. H. 2010, A&A, 520, A43, doi: [`10.1051/0004-6361/201014903`](http://doi.org/10.1051/0004-6361/201014903)

(ref: OrmelLiu2018) Ormel, C. W., & Liu, B. 2018, A&A, 615, A178, doi: [`10.1051/0004-6361/201732562`](http://doi.org/10.1051/0004-6361/201732562)

(ref: PfeilEtal2023) Pfeil, T., Birnstiel, T., & Klahr, H. 2023, ApJ, 959, 121, doi: [`10.3847/1538-4357/ad00af`](http://doi.org/10.3847/1538-4357/ad00af)

(ref: PfeilEtal2024) —. 2024, A&A, 687, L5, doi: [`10.1051/0004-6361/202449323`](http://doi.org/10.1051/0004-6361/202449323)

(ref: PinteEtal2016) Pinte, C., Dent, W. R. F., Ménard, F., et al. 2016, ApJ, 816, 25, doi: [`10.3847/0004-637X/816/1/25`](http://doi.org/10.3847/0004-637X/816/1/25)

(ref: PizzatiEtal2023) Pizzati, E., Rosotti, G. P., & Tabone, B. 2023, MNRAS, 524, 3184, doi: [`10.1093/mnras/stad2057`](http://doi.org/10.1093/mnras/stad2057)

(ref: RenEtal2023b) Ren, B. B., Benisty, M., Ginski, C., et al. 2023, A&A, 680, A114, doi: [`10.1051/0004-6361/202347353`](http://doi.org/10.1051/0004-6361/202347353)

(ref: RibasEtal2024) Ribas, Á., Clarke, C. J., & Zagaria, F. 2024, MNRAS, 532, 1752, doi: [`10.1093/mnras/stae1534`](http://doi.org/10.1093/mnras/stae1534)

(ref: RiolsLesur2018) Riols, A., & Lesur, G. 2018, A&A, 617, A117, doi: [`10.1051/0004-6361/201833212`](http://doi.org/10.1051/0004-6361/201833212)

(ref: RosottiEtal2020b) Rosotti, G. P., Teague, R., Dullemond, C., Booth, R. A., & Clarke, C. J. 2020, MNRAS, 495, 173, doi: [`10.1093/mnras/staa1170`](http://doi.org/10.1093/mnras/staa1170)

(ref: ShiEtal2024) Shi, Y., Long, F., Herczeg, G. J., et al. 2024, ApJ, 966, 59, doi: [`10.3847/1538-4357/ad2e94`](http://doi.org/10.3847/1538-4357/ad2e94)

(ref: SierraEtal2021) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14, doi: [`10.3847/1538-4365/ac1431`](http://doi.org/10.3847/1538-4365/ac1431)

(ref: StammlerEtal2019) Stammler, S. M., Drążkowska, J., Birnstiel, T., et al. 2019, ApJL, 884, L5, doi: [`10.3847/2041-8213/ab4423`](http://doi.org/10.3847/2041-8213/ab4423)

(ref: SzulagyiEtal2014) Szulágyi, J., Morbidelli, A., Crida, A., & Masset, F. 2014, ApJ, 782, 65, doi: [`10.1088/0004-637X/782/2/65`](http://doi.org/10.1088/0004-637X/782/2/65)

(ref: Teague2019) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: TestiEtal2022) Testi, L., Natta, A., Manara, C. F., et al. 2022, A&A, 663, A98, doi: [`10.1051/0004-6361/202141380`](http://doi.org/10.1051/0004-6361/202141380)

(ref: UedaEtal2019) Ueda, T., Flock, M., & Okuzumi, S. 2019, ApJ, 871, 10, doi: [`10.3847/1538-4357/aaf3a1`](http://doi.org/10.3847/1538-4357/aaf3a1)

(ref: vanTerwisgaEtal2018) van Terwisga, S. E., van Dishoeck, E. F., Ansdell, M., et al. 2018, A&A, 616, A88, doi: [`10.1051/0004-6361/201832862`](http://doi.org/10.1051/0004-6361/201832862)

(ref: VillenaveEtal2020) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164, doi: [`10.1051/0004-6361/202038087`](http://doi.org/10.1051/0004-6361/202038087)

(ref: VillenaveEtal2022) Villenave, M., Stapelfeldt, K. R., Duchêne, G., et al. 2022, ApJ, 930, 11, doi: [`10.3847/1538-4357/ac5fae`](http://doi.org/10.3847/1538-4357/ac5fae)

(ref: VillenaveEtal2025) Villenave, M., Rosotti, G., Lambrechts, M., et al. 2025, arXiv e-prints, arXiv:2503.05872, doi: [`10.48550/arXiv.2503.05872`](http://doi.org/10.48550/arXiv.2503.05872)

(ref: VirtanenEtal2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Weidenschilling1977a) Weidenschilling, S. J. 1977, MNRAS, 180, 57, doi: [`10.1093/mnras/180.1.57`](http://doi.org/10.1093/mnras/180.1.57)

(ref: XuBai2022a) Xu, Z., & Bai, X.-N. 2022, ApJ, 924, 3, doi: [`10.3847/1538-4357/ac31a7`](http://doi.org/10.3847/1538-4357/ac31a7)

(ref: YoudinGoodman2005) Youdin, A. N., & Goodman, J. 2005, ApJ, 620, 459, doi: [`10.1086/426895`](http://doi.org/10.1086/426895)

(ref: YoudinLithwick2007) Youdin, A. N., & Lithwick, Y. 2007, Icarus, 192, 588, doi: [`10.1016/j.icarus.2007.07.012`](http://doi.org/10.1016/j.icarus.2007.07.012)

(ref: ZagariaEtal2023) Zagaria, F., Clarke, C. J., Booth, R. A., Facchini, S., & Rosotti, G. P. 2023, ApJL, 959, L15, doi: [`10.3847/2041-8213/ad0c54`](http://doi.org/10.3847/2041-8213/ad0c54)

(ref: ZhangEtal2021k) Zhang, K., Booth, A. S., Law, C. J., et al. 2021a, ApJS, 257, 5, doi: [`10.3847/1538-4365/ac1580`](http://doi.org/10.3847/1538-4365/ac1580)

(ref: ZhangEtal2021s) Zhang, S., Hu, X., Zhu, Z., & Bae, J. 2021b, ApJ, 923, 70, doi: [`10.3847/1538-4357/ac2c82`](http://doi.org/10.3847/1538-4357/ac2c82)

(ref: ZhangEtal2024s) Zhang, S., Zhu, Z., & Jiang, Y.-F. 2024, ApJ, 968, 29, doi: [`10.3847/1538-4357/ad4109`](http://doi.org/10.3847/1538-4357/ad4109)

(ref: ZhuDong2021) Zhu, W., & Dong, S. 2021, ARA&A, 59, 291, doi: [`10.1146/annurev-astro-112420-020055`](http://doi.org/10.1146/annurev-astro-112420-020055)

(ref: ZhuEtal2011) Zhu, Z., Nelson, R. P., Hartmann, L., Espaillat, C., & Calvet, N. 2011, ApJ, 729, 47, doi: [`10.1088/0004-637X/729/1/47`](http://doi.org/10.1088/0004-637X/729/1/47)

(ref: ZhuEtal2019) Zhu, Z., Zhang, S., Jiang, Y.-F., et al. 2019, ApJL, 877, L18, doi: [`10.3847/2041-8213/ab1f8c`](http://doi.org/10.3847/2041-8213/ab1f8c)

# The degeneracy of ring optical depth and temperature

In the default analysis, we set the optical depth of the ring to be $\tau_0$ = 0.5. As noted in the main text, the physical motivation is the "fine-tuned" optical depth previously found in the DSHARP survey (cite: DullemondEtal2018), but see (cite: ZhuEtal2019). It should be acknowledged that this is a practical choice because, given our model assumptions, it is impossible to distinguish between the line of sight optical depth and the temperature of the ring. This is evident in our test analysis of GM Aur, in which we treated the line-of-sight optical depths of the ring peaks, ($\tau_1,\,\tau_2$) and the ring temperatures ($T_1,\,T_2$) as fit parameters. The corner plot of the corresponding MCMC sampling is shown in Fig. [11](#fig:corner7). The posterior distributions of the optical depth and temperature for each ring strictly follow the green curve, on which the values of the optical depth and temperature resemble the unconvolved peak intensity of the rings.

The disbutions of other parameters except $\tau$ and $T$, however, are almost identical to the default MCMC analysis with the optical depth fixed to 0.5. Therefore, we only present results with a fixed tau because varying tau does not contribute to our analysis.

![](fig/gmaur_band6_new_freeT_rr.pdf)

# The influence of JvM correction

Throughout the main text of this work, we use images without applying the so-called JvM correction (cite: CzekalaEtal2021). The JvM correction was originally introduced to more accurately recover the total flux. However, it is also known to introduce point-source artifacts and can affect the interpretation of point-source SNR by lowering the residual rms.

In this section, we apply our MCMC analysis to the LkCa 15 data using the JvM-corrected image, which was published alongside the non-corrected image we use in the main text (cite: LongEtal2022b). The data reduction process is detailed in the original paper, and both images are tapered to a circular beam of $0.05\ensuremath{''} \times 0.05\ensuremath{''}$. The rms noise decreases from 9.3 mJy/beam (0.09 K) to 4.3 mJy/beam (0.04 K) after applying the JvM correction.

The corner plot for the JvM-corrected data is shown in Fig. [12](#fig:corner8). All fitted parameters are nearly identical before and after JvM correction. Yet, due to the lower rms noise in the JvM-corrected image, the posterior distributions are narrower than those derived from the uncorrected data, including the pebble scale height for both rings. Importantly, the conclusion that the inner ring is more settled than the outer ring remains unchanged, and may even be more prominent thanks to the tighter posterior distributions, which yield an even smaller upper limit for the outer ring’s scale height.

+:-----------------------+:--------------------:+:--------------------:+:-------------------:+:-------------------:+:-------------------:+:--------------------:+:--------------------:+:-------------------:+:--------------------:+:----------------:+
|                        | Inner Ring                                                                                                    | Outer Ring                                                                                                  |
+------------------------+----------------------+----------------------+---------------------+---------------------+---------------------+----------------------+----------------------+---------------------+----------------------+------------------+
| **Target**             | $T_1$ \[K\]          | $r_1$ \[au\]         | $w_{i,1}$ \[au\]    | $w_{o,1}$ \[au\]    | $H_{d,1}$ \[au\]    | $T_2$ \[K\]          | $r_2$ \[au\]         | $w_{i,2}$ \[au\]    | $w_{o,2}$ \[au\]     | $H_{d,2}$ \[au\] |
+------------------------+----------------------+----------------------+---------------------+---------------------+---------------------+----------------------+----------------------+---------------------+----------------------+------------------+
| \(1\)                  | \(2\)                | \(3\)                | \(4\)               | \(5\)               | \(6\)               | \(7\)                | \(8\)                | \(9\)               | \(10\)               | \(11\)           |
+------------------------+----------------------+----------------------+---------------------+---------------------+---------------------+----------------------+----------------------+---------------------+----------------------+------------------+
| LkCa 15, **no JvM**    | $23.3^{+0.1}_{-0.1}$ | $68.1^{+0.3}_{-0.3}$ | $6.1^{+0.3}_{-0.3}$ | $6.3^{+0.3}_{-0.3}$ | $1.5^{+0.3}_{-0.4}$ | $14.1^{+0.0}_{-0.0}$ | $99.3^{+0.3}_{-0.3}$ | $9.9^{+0.5}_{-0.5}$ | $11.7^{+0.3}_{-0.3}$ | $<0.6$           |
+------------------------+----------------------+----------------------+---------------------+---------------------+---------------------+----------------------+----------------------+---------------------+----------------------+------------------+
| LkCa 15, **after JvM** | $23.2^{+0.1}_{-0.1}$ | $68.2^{+0.1}_{-0.1}$ | $6.1^{+0.1}_{-0.1}$ | $6.3^{+0.1}_{-0.1}$ | $1.7^{+0.1}_{-0.1}$ | $13.9^{+0.0}_{-0.0}$ | $99.3^{+0.2}_{-0.2}$ | $9.7^{+0.2}_{-0.2}$ | $11.6^{+0.1}_{-0.1}$ | $<0.4$           |
+------------------------+----------------------+----------------------+---------------------+---------------------+---------------------+----------------------+----------------------+---------------------+----------------------+------------------+

Since we are particularly interested in small-scale features rather than precise total flux recovery, we adopt a conservative and consistent approach by using the results from the non-JvM-corrected images as our preferred values. Accordingly, we report only these results for the other disks.

![](fig/lkca15_band6_JvM_rr.pdf)

# Comparison between ALMA continuum and scattered light images

The four disks where we found puffed-up inner rings are all observed with the star-hopping mode of the SPHERE instrument at the Very Large Telescope (cite: RenEtal2023b). We show the comparison between the ALAM continuum images used in this paper and the $K_s$ band $Q_\phi$ maps in Fig. [13](#fig:mm_nir). For all four disks, no polarized light from the outer ring is detected. For LkCa 15 and HD 163296, scattered light rings are detected at the same radii as the inner continuum rings, supporting that the inner ring is puffed-up in both mm and NIR, and that the outer rings are in the shadow of the inner rings.

![image](fig/mm_gallery.pdf) ![image](fig/nir_gallery.pdf)

[^1]: Among the previously published data, LkCa 15 is the only disk available with both JvM-corrected and uncorrected versions (cite: LongEtal2022b). For this work, we use the uncorrected version because our analysis focuses on small-scale intensity deviations rather than total flux recovery (cite: LoomisEtal2025); see Appendix [9](#app:JvM) for further discussion.

</paper>

Write the methods card for this paper.