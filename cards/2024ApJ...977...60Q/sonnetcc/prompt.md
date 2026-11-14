# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977...60Q\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977...60Q",
 "title": "Evidence for a Sharp CO Snow Line Transition in a Protoplanetary Disk and Implications for Millimeter-wave Observations of CO Isotopologues",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Qi, Chunhua",
 "n_authors": 2,
 "arxiv_id": "2410.23036",
 "doi": "10.3847/1538-4357/ad8d55",
 "alma_projects_linked_by_archive": [
  "2016.1.00884.S",
  "2018.1.01055.L"
 ]
}
```

Paper text:
<paper>
# Evidence for a Sharp CO Snowline Transition in a Protoplanetary Disk\
and Implications for Millimeter-wave Observations of CO Isotopologues

## Abstract

Observations of CO isotopologue emission from protoplanetary disks at millimeter wavelengths are a powerful tool for probing the CO snowline, an important marker for disk chemistry, and also for estimating total disk gas mass, a key quantity for planet formation. We use simple models to demonstrate that the vertical thickness of an isothermal layer around the disk midplane has important effects on the CO column density radial profile, with a thick layer producing a sharp CO snowline transition. We simulate ngVLA and ALMA images to show that this sharp change in CO column density can be detected in the derivative of the radial profile of emission from optically thin CO isotopologue lines. We apply this method to archival ALMA observations of the disk around the Herbig Ae star HD 163296 in the $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ J=1-0 and J=2-1 lines to identify a sharp CO snowline transition near $\sim80$ au ($0.8\ensuremath{''}$ at 101 pc), and show the CO column density decreases by more than a factor of 20. This finding is consistent with previous inferences from the steep rise of N$_2$H$^+$ emission, which marks the location where CO depletes. We also demonstrate that the disk’s thermal structure introduces significant systematic uncertainty to estimates of total disk gas mass derived from these lines. The substantial improvement in sensitivity envisioned for the ngVLA over ALMA for observations of ground-state lines of CO isotopologues has the potential to extend this approach to a much larger population of disks.

# Introduction

Planets form from dust and gas within protoplanetary disks surrounding young stars. In the cold disk midplane, temperatures are low enough that many molecules are frozen out onto grain mantles and depleted from the gas phase. The CO snowline, defined as the radius at which the midplane temperature is low enough for CO to freeze out onto dust grains, is an important feature of these disks. The CO snowline location is pivotal because of its effects on the chemical composition and physical properties of the disk. The locations of disk substructures relative to the snowlines (“condensation fronts”) of major volatile species, including H$_2$O, CO$_2$, CO, and N$_2$, are important for setting the chemistry in the disks (cite: Oberg+2023). Radial variations in the C/O ratio affect the composition of material accreted by forming planets, influencing the abundances in their atmospheres (cite: Oberg+2011). In addition, CO, and its less abundant isotopologues, are also commonly used as tracers of disk gas mass, essential for elucidating processes involved in planet building, as cold H$_2$ – the primary mass constituent – is impossible to observe directly. However, accurate conversion of CO emission to total gas mass requires accounting for CO that has frozen out of the gas phase, as well as photodissociation and potential chemical conversion processes (cite: Ansdell+2018; Bosman+2018; Krijt+2018).

The cold midplane and its proximity to chemically active layers in disks can be probed directly by observations of low excitation lines of trace species at millimeter wavelengths. The CO snowline is difficult to observe directly because of radial and vertical temperature gradients, leading to a warmer region above the “snow surface” where CO remains in the gaseous state throughout (cite: Qi+2011). While emission from the most abundant main isotopologue $^{12}$CO in disks is bright, it is also generally very optically thick and traces only an effective photospheric temperature high above the midplane. By contrast, emission from lower-abundance CO isotopologues ($^{13}$CO, C$^{18}$O, C$^{17}$O, $^{13}$C$^{18}$O) have lower optical depths and emerge from deeper in the disk. The high sensitivity and resolution of ALMA for observing low-$J$ lines of these rarer CO isotopologues, and other trace species of cold gas in disks, has revolutionized studies of CO snowlines (cite: Zhang+2017; Booth+2023). N$_2$H$^+$, a species whose abundance is greatly enhanced where freeze-out removes CO from the gas phase (cite: Bergin+2002) has shown promise as a chemical tracer of the CO snowline (cite: Qi+2013), although the interpretation of N$_2$H$^+$is complicated by the three-dimensional structure of the condensation front that arises from the details of the vertical temperature structure (cite: vantHoff+2017; Qi+2019). More directly, high-resolution observations of CO isotopologues, together with disk models, have been used to define the three-dimensional CO “snow surface” in disks, though this method is complicated by the fact that the most easily detected CO isotopologue lines can have substantial opacity (cite: Pinte+2018).

The temperature structure of protoplanetary disks is set by a balance of heating and cooling that depends sensitively on the effects of grain growth, and size-dependent radial drift and vertical settling (cite: Dalessio+2006). The interplay of these processes can have important effects on the location of the CO freeze-out region. For example, the models of (cite: Cleeves2016) predict that inward drift of millimeter-sized grains can result in a small radial temperature inversion that creates a second CO snowline. A more significant effect is predicted to stem from the relative scale heights of large and small grains that control the extent of a vertically isothermal region around the midplane (VIRaM) layer, where temperatures are nearly isothermal vertically at the CO freeze-out region. (cite: Qi+2019) showed that disks with a thick VIRaM layer exhibit bright, narrow N$_2$H$^+$ rings that peak in the slim radial zone between the CO and N$_2$ snowlines. While this chemical signature of a thick VIRaM layer is highly suggestive, direct evidence is still lacking.

In this paper, Section [2](#sec:toy) presents a generic disk model to show that a thick VIRaM layer leads to a sharp drop in the CO column density across the CO snowline, by more than an order of magnitude, and that direct detection of such a “sharp CO snowline transition” can be made using observations of low excitation rotational lines of rare CO isotopologues with high sensitivity, spatial resolution, and spectral resolution. Section [3](#sec:hd163296) applies the concepts from this model to archival ALMA observations of CO isotopologues from the large disk around the nearby Herbig Ae star HD 163296, hypothesized to possess a thick VIRaM layer from its N$_2$H$^+$ emission morphology, and provides strong evidence for the presence of a sharp CO snowline transition. Section [4](#sec:discussion) discusses the implications of this thermal structure, in particular for disk gas mass estimates obtained from observations of CO isotopologues. In this context, the next generation Very Large Array (cite: Murphy+2018) has the potential for substantially advancing this field as a result of its substantially higher sensitivity than ALMA for observations of rare CO isotopologue ground-state lines.

# Disk Vertical Thermal Structure Effects

To investigate the impact of the disk’s vertical thermal structure on the CO radial column density profile, we employ a simple parametric disk model similar to that used by (cite: Andrews+2009). We then simulate observations of the J=1–0 and J=2–1 line emission of rare CO isotopologues to demonstrate the observable consequences of the VIRaM layer thickness.

## Disk Model Prescriptions

We adopt a disk surface density ($\Sigma(r)$) that follows a power-law profile with an exponential taper and a characteristic radius ($r_c$): $$\begin{equation}
\Sigma(r) = \Sigma_0 \left( \frac{r}{r_c} \right)^{-\gamma} \exp \left[ -\left( \frac{r}{r_c} \right)^{2 - \gamma} \right],
\end{equation}$$ where ($\Sigma_0$) is a normalization constant, directly related to the disk gas mass ($M_{\mathrm{gas}}$), $$\begin{equation}
\Sigma_0 = (2 - \gamma) \frac{M_{\text{gas}}}{2 \pi {r_c}^2} \exp\left[ \left(\frac{r_{\text{in}}}{r_c}\right)^{2 - \gamma} \right].
\end{equation}$$ Given a specific temperature structure, the initial pressure at the disk midplane is calculated using the ideal gas law, and the vertical pressure profile is obtained by integrating the hydrostatic equilibrium equation. The density at each height is derived from the pressure using the ideal gas law and normalized to ensure that it integrates to the given surface density. This approach provides a self-consistent vertical density structure that reflects the combined effects of gravity, thermal pressure, and the specified temperature profile.

To explore the effect of the thickness of the VIRaM layer on the resulting CO isotopologue emission, we developed two disk models: one with a thick VIRaM layer and another with a thin one. Both models adopt the identical stellar and disk parameters listed in Table [1](#tab:modelsetup). These parameters were chosen to approximate the well-studied Herbig Ae system HD 163296 (see Section [3](#sec:hd163296)). The two models differ only in their prescribed vertical temperature structures:\
**1. Thin VIRaM Layer Model:** The vertical temperature structure follows the commonly adopted analytic profile from (cite: Dartois+2003), which approximates the physical models calculated by (cite: DAlessio+1999), i.e. $$T(r, z) =
   \begin{cases} 
   T_{\text{atm}} + \left( T_{\text{mid}} - T_{\text{atm}} \right) \cos^3 \left( \frac{\pi z}{4H} \right) & \text{if } z < 2H, \\
   T_{\text{atm}} & \text{if } z \geq 2H,
   \end{cases}$$ where $H$ is the gas scale height. In this model, the temperature increases rapidly from the midplane to the disk atmosphere, producing a thin VIRaM layer.\
**2. Thick VIRaM Layer Model:** The vertical temperature profile mimics the structure found by (cite: Qi+2011) from analyzing observations of the HD 163296 disk, $$T(r, z) =
   \begin{cases} 
   T_{\text{mid}} & \text{if } z < 2H, \\
   T_{\text{atm}} + \left( T_{\text{mid}} - T_{\text{atm}} \right) \cos^3 \left( \frac{\pi z}{12H} \right) & \text{if } 2H \leq z < 6H, \\
   T_{\text{atm}} & \text{if } z \geq 6H,
   \end{cases}$$ where the temperature is nearly isothermal up to 2$H$ and transitions more gradually up to 6$H$, creating an effectively thick VIRaM layer.\
For both models, the CO freeze-out temperature was assumed to be 24 K. The results are not sensitive to the exact choice of this parameter. For the thick VIRaM model, the corresponding CO snowline location is at 80 au. For the thin VIRaM layer model, which has all parameters the same other than the vertical temperature profile, the CO snowline is also 80 au. Adopting a distance of 100 pc, the snowline location lies at $0.8\ensuremath{''}$ radius. Figure [1](#fig:toymodels) presents the temperature and density distributions for the two disk models. The left panel shows the model with the thick VIRaM layer model, with temperature contours nearly vertical up to 2$H$. The middle panel shows the thin VIRaM layer model, which has a much steeper vertical temperature gradient from the midplane to the atmosphere.

| **Parameter** | **Value** |
|:---|:---|
| Stellar Mass ($M_*$) | $2 \, M_{\odot}$ |
| Disk Gas Mass ($M_{\text{gas}}$) | $0.04 \, M_{\odot}$ |
| Inner Radius ($r_{\text{in}}$) | 1 au |
| Characteristic Radius ($r_c$) | 150 au |
| Surface Density Gradient ($\gamma$) | 0.9 |
| Midplane Temperature Profile ($T_{\text{mid}}$) | $24 \left( \frac{R}{80\, \text{au}} \right)^{-0.4}$ |
| Atmosphere Temperature Profile ($T_{\text{atm}}$) | $700 \left( \frac{R}{1\, \text{au}} \right)^{-0.55}$ |

: Disk Model Parameters

![](toymodel.png)

We assume CO emission originates in a vertical layer of the disk with a constant abundance $f_{\mathrm{CO}} = 1 \times 10^{-4}$. The upper boundary of this layer, toward the disk surface, is constrained by CO photodissociation, which occurs above an H$_2$ surface column density of approximately $10^{21} \, \text{cm}^{-2}$ (cite: Qi+2011). The lower boundary, closer to the midplane, is defined by the CO freeze-out temperature, assumed to be 24 K. When the temperature drops below 24 K, the depletion factor -– the reduction in CO fractional abundance due to freeze-out -– is set to 320. In such regions, the CO abundance decreases to $3.1 \times 10^{-7}$. The right panel of Figure [1](#fig:toymodels) displays the resulting CO column density profiles for both models. The model with a thick VIRaM layer exhibits a very sharp radial drop in CO column density at the snowline (80 au), whereas the model with a thin VIRaM layer shows a more gradual decrease.

These models serve to illustrate that the disk’s vertical thermal structure significantly impacts the CO radial column density profile. For the thick VIRaM layer model, temperature contours in the disk region below the CO freeze-out temperature are nearly perpendicular to the density contours, which produces a very sharp drop in the CO column density across the snowline. In contrast, the thin VIRaM layer model shows a much smoother gradient in CO column density.

In this study, we focus on the impact of the vertical thermal structure and CO depletion across the snowline, while intentionally omitting the effects of disk substructures, such as rings or gaps, which are not included in our current models. Future work will need to incorporate these substructures to assess how the small-scale temperature changes induced by such features (cite: ZhangS+2021) may affect the sharpness of the CO snowline transition.

## CO Isotopologue Imaging Simulations

The CO snowline can be probed best using optically thin tracers sensitive to cold gas, such as the lowest excitation rotational lines of rare CO isotopologues, together with sufficiently high spatial resolution – in particular, a beam size smaller than half the CO snowline radius – to resolve the column density change within the beam. Low optical depth provides intrinsic sensitivity to changes in the CO column density with the radius, while high spatial resolution prevents the shape of the radial profile from being smoothed out.

Using the CO distributions from two models with thin and thick VIRaM layers and assuming local interstellar medium (ISM) ratios of CO/C$^\mathrm{17}$O = 2005 and CO/C$^\mathrm{18}$O = 557 (cite: Wilson1999), we simulated $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ 1-0 and 2-1 emission using the nonlocal thermodynamic equilibrium, two-dimensional accelerated Monte Carlo radiative transfer code RATRAN (cite: Hogerheijde+2000). The outputs of these simulations were then converted into synthetic visibility datasets using the `simobserve` task in the *Common Astronomy Software Application* package (cite: CASA+2022).

For the $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ 2-1 lines, we used ALMA for the imaging simulations. These simulations employed the configuration file `alma.cycle7.5.cfg`, which contains 43 antennas over baselines up to 2 km, resulting in a beam size of $0.3\ensuremath{''}$. This beam size is smaller than half the CO snowline radius ($0.8\ensuremath{''}$) in the models, providing sufficient resolution to detect the sharpness of the CO snowline transition in optically thin tracers. The simulated observations had an on-source integration time of 2 hours, aligning with the observations from the ALMA MAPS Large Program (cite: Oberg+2021).

For the weaker $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ 1-0 lines, we used the ngVLA for the imaging simulations due to its superior sensitivity at these frequencies compared to ALMA. The ngVLA simulations used the configuration file `ngvla-revD.core.cfg`, which includes 114 antennas with a diameter of 18 meters within a 4 km region, providing a beam size of about $0.3\ensuremath{''}$, comparable to that for the ALMA simulations. The simulated observations had an on-source integration time of 4 hours for ngVLA simulations. To add proper noise to the ngVLA simulations, we followed the recommendations from the CASA simulation guide[^1] and estimated the scaling parameter $\sigma\_{simple}$, then corrupted the simulated data using the `sm.setnoise` function of the `sm` toolkit. Note that ALMA would require an integration time of about 30 times longer than ngVLA to reach the same noise level for these lines at this resolution, according to the available online telescope sensitivity estimators for ALMA[^2] (for typical band 3 weather) and ngVLA[^3].

The detailed parameters for each simulated line are summarized in Table [\[tab:simulation_params\]](#tab:simulation_params). The source declination was assumed to be $-22$ degrees. The disk was assumed to be inclined by $45$ degrees oriented at a position angle of $90$ degrees (east from north). The simulations were conducted with 60 velocity channels of width 0.5 km $^{-1}$ for each line. Imaging was performed using the `tclean` task in CASA with Briggs weighting and a robust parameter of $2$, i.e. close to natural weighting for maximum sensitivity. Finally, we collapsed the spectral cubes into integrated intensity maps using the Python package `bettermoments` (cite: Teague+2018).

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | Frequency | Channel | Int. Time | Antenna | Beam | rms |
|   | (GHz) | (km s$^{-1}$) | (s) | Config. | (arcsec) | (mJy beam$^{-1}$) |
| $\mathrm{C^{17}O}$ 1-0 | 112.359 | 0.5 | 14,400 | `ngvla-revD.core.cfg` | $0.32 \times 0.20$ | 0.24 |
| $\mathrm{C^{17}O}$ 2-1 | 224.714 | 0.5 | 7200 | `alma.cycle7.5.cfg` | $0.33 \times 0.30$ | 1.03 |
| $\mathrm{C^{18}O}$ 1-0 | 109.782 | 0.5 | 14,400 | `ngvla-revD.core.cfg` | $0.32 \times 0.21$ | 0.18 |
| $\mathrm{C^{18}O}$ 2-1 | 219.560 | 0.5 | 7200 | `alma.cycle7.5.cfg` | $0.34 \times 0.31$ | 1.06 |

Figure [2](#fig:toy1021-maps) shows integrated intensity images of C$^{17}$O and C$^{18}$O 1-0 and 2-1 for the models with thin and thick VIRaM layers. The light blue dashed line indicates the location of the CO snowline. The radial extent of C$^{17}$O 1-0 emission appears smaller for the model with a thick VIRaM layer, as the intensity drops sharply beyond the CO snowline in this model. By contrast, the C$^{17}$O 1-0 emission extends much further beyond the CO snowline for the model with a thin VIRaM layer. Differences in emission extent are also apparent in the C$^{17}$O 2-1 and C$^{18}$O 1-0 images, albeit to a lesser extent in the latter as the optical depths of these lines are higher. Any differences in emission extent between the two models are effectively obscured in the C$^{18}$O 2-1 images, as this line is optically thick for both.

![image](toymap_c17o10.png) ![image](toymap_c18o10.png) ![image](toymap_c17o21.png) ![image](toymap_c18o21.png)

We extracted the deprojected and azimuthally averaged radial intensity profiles using the `radial_profile` function from the Python package GoFish (cite: Teague2019). Figure [3](#fig:toy1021-profs) (top panels) shows the radial profiles of the integrated intensity of the simulated C$^{17}$O and C$^{18}$O 1-0 and 2-1 emission for models with thick and thin VIRaM layers. While a sharp drop in the CO column density with the radius is not immediately evident from the radial profiles of the integrated emission intensity, it can be identified by analyzing the derivative of this radial profile. If the disk has a thick VIRaM layer, then the resulting sharp CO snowline will present a local minimum in the derivative, provided the emission is optically thin. Figure [3](#fig:toy1021-profs) (bottom panels) shows the derivatives of the radial profiles, with the location of the CO snowline indicated by a gray dashed line.

The derivatives for the thick VIRaM layer model show a clear minimum near the CO snowline for the J=1–0 lines, marking a significant change in the rate of CO column density decline with the radius. In contrast, the derivatives for the thin VIRaM layer model do not show a minimum clearly associated with the CO snowline. The minimum is less prominent in the C$^{17}$O 2-1 profile and is not visible at all in the C$^{18}$O 2-1 profile, as the emission from this more abundant isotopologue is optically thick throughout. This highlights that the “sharpness” of the CO snowline transition is best distinguished using the most optically thin tracers, particularly the ground-state lines. This radial profile derivative analysis provides an empirical way to determine the CO snowline location.

![image](toyprofile_c17o10.png) ![image](toyprofile_c18o10.png) ![image](toyprofile_c17o21.png) ![image](toyprofile_c18o21.png)

# Application to HD 163296

The Herbig Ae star HD 163296 is surrounded by a disk that has been a favorite target of detailed study with the improving capabilities of millimeter interferometry for more than 25 years (cite: Mannings+1997; Isella+2007; Qi+2011; Rosenfeld+2013; Oberg+2021). The N$_2$H$^+$ emission from this disk shows a characteristic bright, narrow ring with extended tenuous emission, which is well matched by the presence of a thick VIRaM layer (cite: Qi+2015) as found using the D’Alessio Irradiated Accretion Disk (DIAD) model (cite: Dalessio+2006) that provided a consistent fit to the spectral energy distribution and overall shape of resolved millimeter dust continuum emission. This model features a refined vertical structure where dust settling is regulated by the transition location between small and large grains, $z=z_{big}$ in units of the gas scale height $H$. This grain regulation enhances the temperature disparity between the disk surface and interior. Larger dust grains, with lower infrared opacities, are concentrated near the midplane, resulting in less efficient heating compared to smaller particles. Consequently, the HD 163296 disk has a cold midplane with large grains at a significant scale height ($z_{big}=2H$). Near the midplane, the temperature remains approximately constant with height, effectively creating a thick VIRaM layer. Given the known CO snowline location around 0.8$''$ (cite: Qi+2015), this disk serves as an ideal example to study the sharp drop in the CO column density across the CO snowline for a disk with a thick VIRaM layer.

## ALMA Observations of CO Isotopologues Toward HD 163296

We examined archival ALMA observations of $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ 1-0 and $\mathrm{C^{18}O}$ 2-1 lines in Bands 3 and 6 toward the disk of HD 163296 from the MAPS Large Program (project 2018.1.01055.L). The observational details can be found in (cite: Oberg+2021). The beam sizes for the $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ 1-0 observations are 0.27$''$$\times$0.21$''$, and for the $\mathrm{C^{18}O}$ 2-1 observations, 0.14$''$$\times$0.11$''$. We also retrieved $\mathrm{C^{17}O}$ 2-1 data from project 2016.1.00884.S (PI: V.V. Guzmán), with observational details provided in (cite: Carney+2019; Hernadez-vera+2024). The beam size for the $\mathrm{C^{17}O}$ 2-1 data is 0.52$''$$\times$0.37$''$. Figure [4](#fig:hdrad) shows the radial profiles of the integrated intensities and their derivatives. The derivatives of $\mathrm{C^{17}O}$ 1-0, $\mathrm{C^{18}O}$ 1-0, and $\mathrm{C^{17}O}$ 2-1 all display a local minimum near the CO snowline location determined by (cite: Qi+2015). The $\mathrm{C^{18}O}$ 2-1 emission, being optically thick, is not suitable for this analysis, as expected from the models in Section [2](#sec:toy).

![image](dataprofile_c17o10.png) ![image](dataprofile_c18o10.png) ![image](dataprofile_c17o21.png) ![image](dataprofile_c18o21.png)

## $\mathrm{C^{18}O}$ 1-0 in Other MAPS Disks

Since $\mathrm{C^{18}O}$ is detected toward all of the disks in the MAPS program in addition to HD 163296, while $\mathrm{C^{17}O}$ 1-0 is only marginal detected toward some of the MAPS disks, we present the $\mathrm{C^{18}O}$ radial profiles and derivatives in Figure [5](#fig:maps_radial) for these disks – GM Aur, AS 209, IM Lup, and MWC 480 – with 0.3$''$ beam size (archival images from the MAPS Large Program project 2018.1.01055.L).

The GM Aur disk, identified by (cite: Qi+2019) as possessing a thick VIRaM layer, exhibits a well-defined CO snowline at 48 au, equivalent to 0.3$''$. As shown in Figure [5](#fig:maps_radial) (GM Aur), despite the 0.3$''$ beam size being comparable to the snowline location, a clear dip in the derivative of the $\mathrm{C^{18}O}$ 1-0 profile aligns with the expected snowline radius. This feature supports the hypothesis that a thick VIRaM layer facilitates a distinct, observable transition in the CO column density across the snowline. Conversely, for the AS 209 and IM Lup disks, which were found to have thinner VIRaM layers, no evident dip can be seen in the $\mathrm{C^{18}O}$ 1-0 derivative profiles. The absence of this feature could result from CO snowlines that are comparable to, or smaller than, the 0.3$''$ beam size, smoothing out the transition in the observations.

For the MWC 480 disk, an intriguing feature is observed: a dip in the derivative of the C$^{18}$O 1-0 radial profile at a radius smaller than 0.3$''$. However, this dip cannot be associated with the CO snowline, as thermal-chemical modeling of the MWC 480 disk places the CO snowline beyond 125 au (0.8$''$) (cite: Zhang+2021). This discrepancy suggests that other physical processes, such as chemical evolution, substructures, or line opacity effects, similar to those that affect the C$^{18}$O 2-1 line for HD 163296, are influencing the emission profile in this disk.

![image](dataprofile_gmaurc18o10.png) ![image](dataprofile_as209c18o10.png) ![image](dataprofile_imlupc18o10.png) ![image](dataprofile_mwc480c18o10.png)

## CO Depletion Factor

To further investigate the effect of CO depletion across the snowline, we simulated the emission of CO isotopologues by varying the CO depletion factor ($df$). (cite: Qi+2015) derived a depletion factor of 5 ($df = 5$) to fit the ALMA $\mathrm{C^{18}O}$ 2-1 data toward the HD 163296 disk, which was the most optically thin tracer available at that time. In this work, we assess whether a higher depletion factor could better explain the observed flux changes across the snowline, particularly for optically thinner tracers such as $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ 1-0. We followed the methodology of (cite: Qi+2015), utilizing the RATRAN code to perform non-local thermodynamic equilibrium radiative transfer calculations and to generate synthetic CO data cubes. These synthetic data were sampled at the same spatial frequencies as the ALMA observations using the Python-based visibility sampling routine, `vis_sample` (cite: Loomis+2018). The deprojected and azimuthally averaged radial intensity profiles were then extracted using the `radial_profile` function from GoFish.

While (cite: Qi+2015) fit the $C^{18}O$ 2-1 data visibilities by varying both the CO freeze-out temperature (and, consequently, the location of the CO snowline) and the CO depletion factor ($df$), our study focuses on evaluating the local emission profile change across the CO snowline for the optically thinner CO isotopologues with various $df$, avoiding the need to account for potential CO photodesorption by nonthermal processes beyond 200 au (cite: Salinas+2017). Since the CO snowline location has already been identified through the local minima in the derivatives of the emission profiles, as shown in Section [3](#sec:hd163296), we explored models with depletion factors only, spanning a coarse logarithmic grid from 0.5 to 3.0 in steps of 0.5. To evaluate the relative flux change across the CO snowline, we normalized the flux profiles at a reference point near the snowline transition, specifically at 0.65$''$ (slightly interior to the snowline at 0.8$''$), to ensure sensitivity to the sharpness of the transition. Figure [6](#fig:hdnorm) shows the normalized flux profiles of $\mathrm{C^{17}O}$ and $\mathrm{C^{18}O}$ 1-0 and 2-1 emissions for models with a depletion factor of $df = 5$ (as derived by (cite: Qi+2015)) and $df = 10^{2.5}$ (i.e., 320), compared with the observations. The model with a depletion factor of 320 matches the data more closely than the model with a depletion factor of 5, particularly for the optically thinner tracers $\mathrm{C^{17}O}$ 1-0, 2-1, and $\mathrm{C^{18}O}$ 1-0. The similarity in the shapes of the $\mathrm{C^{18}O}$ 2-1 flux profiles in both models and the observations indicates that this emission line is optically thick and largely insensitive to the depletion factor.

![](hd163296_normprofiles.png)

These findings from the ALMA observations of rare CO isotopologues are consistent with the presence of a thick VIRaM layer in the disk around HD 163296 and a sharp CO snowline. Such a structure significantly influences the CO isotopologue emission, highlighting the critical role of the disk’s thermal structure.

# Discussion

We have shown that emission from rare CO isotopologues provides a useful probe for the presence of a sharp CO snowline transition in disks with a thick vertical isothermal layer. We provided direct evidence for this feature in the disk around the Herbig Ae star HD 163296 from low-$J$ CO isotopologue emission resolved by ALMA observations. We next discuss implications of this thermal structure for CO distribution models of HD 163296, the general use of CO isotopologue emission for estimating total disk gas masses, and the feasibility of future observations in more disks.

## Comparison of HD 163296 CO Distribution Models

The sensitivity of the low-$J$ CO isotopologue lines to the CO snowline structure is underscored by comparing the emission resulting from different disk models. Figure [7](#fig:hdcol) (left panel) shows the radial profile of the CO column density for three models of the disk around HD 163296: (1) the model with a depletion factor ($df$) of 5, as derived by (cite: Qi+2015); (2) the model with a higher $df$ of 320, which provides a better match to the data, as demonstrated in Section [3.3](#sec:df); and (3) the model from the ALMA MAPS program, where the analysis of CO isotopologues suggested an enhancement in CO abundance interior to the snowline (cite: Zhang+2021). The key region of interest in this comparison lies between 70 and 90 au, where the CO column density shows significant variations across the CO snowline. The model with $df = 320$ demonstrates a much steeper decline in the CO column density compared to either the $df = 5$ model or the MAPS model. In particular, the CO column density in the $df = 320$ model decreases by more than a factor of 20 between 70 and 90 au, while the $df = 5$ model shows a decrease by a factor of 5, and the MAPS model shows a decrease by only a factor of 2. This pronounced drop in the $df = 320$ model provides clear evidence of a sharp CO snowline transition in the disk of HD 163296.

![image](plot_col_hd163296CO.png) ![image](hd163296_c17oc18o10normprof.png)

Figure [7](#fig:hdcol) (left panel) also indicates reference CO column density values corresponding to optical depths ($\tau$) of 1 for the different CO isotopologue lines, as calculated using the RADEX code (cite: vanderTak+2007) and assuming interstellar medium ratios of CO/C$^{17}$O = 2005 and CO/C$^{18}$O = 557. The grey lines indicate the column densities at which the emission becomes optically thick: $2 \times 10^{20} \, \text{cm}^{-2}$ for $\tau = 1$ of C$^{17}$O 1-0, $7 \times 10^{19} \, \text{cm}^{-2}$ for $\tau = 1$ of C$^{17}$O 2-1, $5.5 \times 10^{19} \, \text{cm}^{-2}$ for $\tau = 1$ of C$^{18}$O 1-0, and $1.9 \times 10^{19} \, \text{cm}^{-2}$ for $\tau = 1$ of C$^{18}$O 2-1. From 70 to 90 au, all models predict CO column densities below the threshold for $\tau = 1$ of C$^{17}$O 1-0, indicating that this transition remains optically thin across the CO snowline. However, both the $df = 320$ and the $df = 5$ models predict CO column densities above the threshold for $\tau = 1$ of C$^{18}$O 1-0, indicating that this transition is optically thick; the MAPS model remains below this threshold, implying that C$^{18}$O 1-0 is optically thin.

Figure [7](#fig:hdcol) (right panel) shows the radial profile of the integrated flux of C$^{18}$O 1-0 compared to C$^{17}$O 1-0, normalized at 70 au to more clearly show the difference in profile shape. The steeper decline of emission from C$^{17}$O compared to C$^{18}$O aligns with the predictions of the models with $df=5$ and $df=320$ where C$^{18}$O 1-0 emission is indeed optically thicker than the C$^{17}$O 1-0 emission across the CO snowline, but contradicts the expectations of the MAPS model where both lines would remain optically thin and show a more similar decrease.

The good agreement between the ALMA data and the $df = 320$ model supports the validity of the approach taken here, providing a better fit to emission from the optically thinner CO isotopologues. This agreement suggests that the CO column density exhibits a sharp drop across the CO snowline, consistent with the presence of a thick VIRaM layer near the midplane of this disk. The sharp transition in this model provides a more accurate representation of the physical conditions.

Both the (cite: Qi+2011; Qi+2015) and (cite: Zhang+2021) modeling approaches rely on fitting the spectral energy distribution (SED), resolved millimeter dust continuum data, and multiple CO isotopologue emission lines in a consistent framework. However, the fundamental difference between these studies lies in how the vertical temperature structure near the disk midplane is modeled.

We employed the *DIAD* model adopted from (cite: Qi+2011; Qi+2015), which directly addresses the degeneracy in vertical temperature structure that arises when models are constrained by dust emission (e.g., the SED). The *DIAD* model accounts for the concentration of large grains near the midplane, enhancing the temperature gradient between the surface and interior layers. This configuration can result in a vertically isothermal region (VIRaM layer) near the midplane of some disks, influencing the CO distribution and its emission properties. In contrast, the (cite: Zhang+2021) analysis uses thermal-chemical models, such as RAC2D, to derive the dust temperature structure. While these models provide detailed chemical insights, they do not explicitly capture the vertically isothermal structure near the midplane. The difference in modeling approaches contributes to the different interpretations of the CO snowline transition in the HD 163296 disk across studies.

## Effect on Disk Mass Estimates

The emission from rare CO isotopologues remains one of the best methods for estimating total disk gas masses, a critical parameter for understanding many aspects of planet formation (cite: Bergin+2017; Miotello+2023). However, accurate disk mass estimates are challenging due to factors such as isotope-selective CO photodissociation, CO freeze-out, and the complex thermal structure of disks. Low CO masses observed in T Tauri disks (cite: Ansdell+2018) are often attributed to chemical reprocessing of CO into more complex ices (cite: Bosman+2018) or the sequestration of CO onto larger bodies (cite: Krijt+2018). These mechanisms are less significant in warmer Herbig Ae disks (cite: Kama+2020), where CO freeze-out is inefficient. However, discrepancies in disk mass estimates may also arise from structural differences within the disks.

As the models in Section [2](#sec:toy) demonstrate, the thickness of the VIRaM layer plays a critical role in shaping the vertical temperature distribution, which directly impacts the CO column density’s radial variation across the CO snowline. This, in turn, influences the emission of CO isotopologues and affects the derived disk mass.

![](toy2_diskmass.png)

To illustrate the impact of disk thermal structure on mass inferences, we compared two models: Model 1, with a thin VIRaM layer and a disk mass of 0.01 M$_\odot$, and Model 2, with a thick VIRaM layer and a disk mass of 0.04 M$_\odot$. Figure [8](#fig:diskmass) (left panel) shows the CO column density profiles for both models. In Model 2, the CO column density inside the CO snowline is higher than in Model 1, due to the larger disk mass (by a factor of 4). However, beyond the CO snowline, the CO column density in Model 2 drops sharply, resulting in a lower CO column density compared to Model 1. Figure [8](#fig:diskmass) (right panel) presents the C$^{17}$O 1-0 spectra for these models at $1.5\ensuremath{''}$ resolution, generated using the `integrated_spectrum` function from the Python package `GoFish` (cite: Teague2019). Despite Model 2 having a higher CO column density inside the CO snowline, its spectrum is lower than that of Model 1 because the emission beyond the CO snowline dominates the integrated flux in both models. In Model 2, the emission inside the CO snowline becomes optically thick, reducing its sensitivity to CO column density variations.

This analysis highlights how the thickness of the VIRaM layer significantly sharpens the CO snowline transition and alters CO isotopologue emission. If the detailed disk structure, particularly the VIRaM layer thickness, is not properly accounted for, disk mass estimates derived from CO isotopologue emission may be substantially inaccurate.

(cite: Williams+2014) used a grid of simple parametric disk models to argue that total disk gas masses could be reasonably estimated from unresolved integrated emissions of $\mathrm{^{13}CO}$ and $\mathrm{C^{18}O}$. Subsequent studies, such as (cite: Miotello+2016), incorporated more detailed chemistry and demonstrated that uncertainties of up to an order of magnitude could arise, especially for disks with masses greater than 0.001 M$_\odot$, due to optical depth effects. Our results extend these findings by showing that even the emission from low-abundance tracers like $\mathrm{C^{17}O}$ can be significantly influenced by assumptions about the disk’s physical conditions. Accounting for complex thermal structures, including the thickness of the VIRaM layer, is crucial for accurately interpreting CO isotopologue emissions and deriving disk masses.

To reliably detect a dip in the derivative over the CO snowline for the thick VIRaM case, three observational criteria must be met: (1) The tracer’s line optical depth must remain optically thin close within the CO snowline, ensuring sensitivity to the local column density changes; (2) The instrument must have sufficient sensitivity to detect the tracer emission even after the column density drops by more than an order of magnitude beyond the CO snowline; (3) The spatial resolution of the instrument must be high enough to resolve the sharp transition at the CO snowline, preventing the profile from being smoothed out by the beam size.

## Prospects with ngVLA

An important implication of our modeling is that high-resolution observations of optically thin CO isotopologue line emission are needed to locate CO snowlines in disks with different thermal structures and to confront associated predictions. The combination of resolution and sensitivity will become even more important for disks around pre-main-sequence stars of lower luminosity than HD 163296 – the T Tauri stars – where the CO snowline is located closer to the star, typically $\sim20 - 30$ au, and CO freeze-out is more significant. While it is clear that ALMA can effectively probe optically thin CO isotopologue lines in a large, warm, massive disk like the one around the Herbig Ae star HD 163296, even the relatively deep ($2-3$ hr) ALMA MAPS observations of disks around T Tauri stars resulted in tentative or modest detections of C$^{17}$O 1-0 emission at $\sim0.25\ensuremath{''}$ resolution (cite: Oberg+2021). Substantially better observational capabilities than currently available with ALMA will be needed to obtain sufficient signal-to-noise ratio to extend the study of CO snowlines to a broader population of disks.

For sharp CO snowlines, detecting radial C/O variations becomes easier, offering a clearer understanding of the abundance and location of molecules in disks and their role in the formation of planetesimals and icy planets. The ngVLA is envisioned to improve ALMA’s sensitivity by up to an order of magnitude for observations in the frequency range $35-116$ GHz where ngVLA and ALMA overlap. To date, most interest in ngVLA for protoplanetary disks has focused on milliarcsecond-resolution observations of thermal dust emission to image terrestrial planet formation zones of disks, to reveal substructures associated with young planets (cite: Ricci+2018). However, the upper end of the ngVLA frequencies includes the ground-state transitions of the suite of rare CO isotopologues that can provide optically thin tracers for a wide range of CO column densities at angular resolutions appropriate for CO snowlines in the large population of T Tauri stars located at the $\sim140$ pc distance of nearby star-forming regions. Deep, resolved ngVLA observations to exploit these diagnostics. For example, the ALMA MAPS detection of C$^{17}$O 1-0 in GM Aur at the $3.5\sigma$ level suggests the ngVLA could provide a resolved radial profile at sufficient signal-to-noise ratio to reveal the CO snowline location with a comparable investment of observing time. Observations of a large sample have the potential to provide a much more nuanced understanding of the factors that contribute to CO isotopologue emission from disks and the effects on inferred physical properties such as disk gas masses.

# Conclusions

We use simple models of protoplanetary disks to demonstrate the importance of accounting for the disk thermal structure on the CO column density distribution, in particular the vertical extent of an isothermal region at the midplane, and we investigate the implications for observations of low-$J$ rotational lines of CO isotopologues at millimeter wavelengths. The main findings are:

- A thick vertical isothermal layer produces a sharp drop in CO column density across the CO snowline. Simulated CO isotopologue images from the ngVLA (for J=1–0 lines) and ALMA (for J=2–1) lines demonstrate the importance of low line optical depth in revealing the location of the sharp CO snowline transition. We show that a local minimum in the derivative of the radial emission profile can serve to identify the CO snowline location.

- Applying the concepts from the models to archival ALMA observations of CO isotopologue emission from the Herbig Ae star HD 163296 system reveals a sharp CO snowline transition, with the CO column density decreasing by more than a factor of 20 between 70 and 90 au. This provides clear evidence of a distinct CO snowline near 80 au, consistent with the location previously inferred from chemical signatures of CO depletion. Our analysis also refines the constraints on the CO depletion fraction.

- The presence of a sharp CO snowline has implications on total disk gas estimates derived from CO isotopologue emission. Substantial, systematic, underestimates of the disk gas mass can result from this different thermal structure, even when the depletion due to CO freeze-out is considered.

The development of the ngVLA, which will provide a substantial sensitivity improvement over ALMA for high-resolution observations of the J=1–0 lines of CO isotopologues, will enable extending this approach to CO snowline studies to many more systems, in particular for a sample of the large population of T Tauri disks in nearby star-forming regions.

We thank the anonymous referee for a constructive report, which improved the paper. C.Q. thanks K. Öberg, S. Andrews, and C. Espaillat for helpful discussions about the results presented in this paper. C.Q. acknowledges support for this work from the NRAO ngVLA Community Study program. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S and ADS/JAO.ALMA#2018.1.01055.L. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc.

# Facilities

ALMA

# Software

Astropy (cite: Astropy2013; Astropy2018; Astropy2022), `bettermoments` (cite: Teague+2018), `CASA` (cite: CASA+2022), `GoFish` (cite: Teague2019), Matplotlib (cite: Hunter2007), NumPy (cite: vanderWalt2011), RADEX (cite: vanderTak+2007), SciPy (cite: Virtanen2020), vissample (cite: Loomis+2018).

natexlab

(ref: Andrews+2009) Andrews, S. M., Wilner, D. J., Hughes, A. M., Qi, C., & Dullemond, C. P. 2009, ApJ, 700, 1502, doi: [`10.1088/0004-637X/700/2/1502`](http://doi.org/10.1088/0004-637X/700/2/1502)

(ref: Ansdell+2018) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21, doi: [`10.3847/1538-4357/aab890`](http://doi.org/10.3847/1538-4357/aab890)

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bergin+2002) Bergin, E. A., Alves, J., Huard, T., & Lada, C. J. 2002, ApJL, 570, L101, doi: [`10.1086/340950`](http://doi.org/10.1086/340950)

(ref: Bergin+2017) Bergin, E. A., & Williams, J. P. 2017, in Astrophysics and Space Science Library, Vol. 445, Formation, Evolution, and Dynamics of Young Solar Systems, ed. M. Pessah & O. Gressel, 1, doi: [`10.1007/978-3-319-60609-5_1`](http://doi.org/10.1007/978-3-319-60609-5_1)

(ref: Booth+2023) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macı́as, E. 2023, A&A, 678, A146, doi: [`10.1051/0004-6361/202346974`](http://doi.org/10.1051/0004-6361/202346974)

(ref: Bosman+2018) Bosman, A. D., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 618, A182, doi: [`10.1051/0004-6361/201833497`](http://doi.org/10.1051/0004-6361/201833497)

(ref: Carney+2019) Carney, M. T., Hogerheijde, M. R., Guzmán, V. V., et al. 2019, A&A, 623, A124, doi: [`10.1051/0004-6361/201834353`](http://doi.org/10.1051/0004-6361/201834353)

(ref: CASA+2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Cleeves2016) Cleeves, L. I. 2016, ApJL, 816, L21, doi: [`10.3847/2041-8205/816/2/L21`](http://doi.org/10.3847/2041-8205/816/2/L21)

(ref: Dalessio+2006) D’Alessio, P., Calvet, N., Hartmann, L., Franco-Hernández, R., & Servı́n, H. 2006, ApJ, 638, 314, doi: [`10.1086/498861`](http://doi.org/10.1086/498861)

(ref: DAlessio+1999) D’Alessio, P., Calvet, N., Hartmann, L., Lizano, S., & Cantó, J. 1999, ApJ, 527, 893, doi: [`10.1086/308103`](http://doi.org/10.1086/308103)

(ref: Dartois+2003) Dartois, E., Dutrey, A., & Guilloteau, S. 2003, A&A, 399, 773, doi: [`10.1051/0004-6361:20021638`](http://doi.org/10.1051/0004-6361:20021638)

(ref: Hernadez-vera+2024) Hernández-Vera, C., Guzmán, V. V., Artur de la Villarmois, E., et al. 2024, ApJ, 967, 68, doi: [`10.3847/1538-4357/ad3cdb`](http://doi.org/10.3847/1538-4357/ad3cdb)

(ref: Hogerheijde+2000) Hogerheijde, M. R., & van der Tak, F. F. S. 2000, A&A, 362, 697, doi: [`10.48550/arXiv.astro-ph/0008169`](http://doi.org/10.48550/arXiv.astro-ph/0008169)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Isella+2007) Isella, A., Testi, L., Natta, A., et al. 2007, A&A, 469, 213, doi: [`10.1051/0004-6361:20077385`](http://doi.org/10.1051/0004-6361:20077385)

(ref: Kama+2020) Kama, M., Trapman, L., Fedele, D., et al. 2020, A&A, 634, A88, doi: [`10.1051/0004-6361/201937124`](http://doi.org/10.1051/0004-6361/201937124)

(ref: Krijt+2018) Krijt, S., Schwarz, K. R., Bergin, E. A., & Ciesla, F. J. 2018, ApJ, 864, 78, doi: [`10.3847/1538-4357/aad69b`](http://doi.org/10.3847/1538-4357/aad69b)

(ref: Loomis+2018) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018, AJ, 155, 182, doi: [`10.3847/1538-3881/aab604`](http://doi.org/10.3847/1538-3881/aab604)

(ref: Mannings+1997) Mannings, V., & Sargent, A. I. 1997, ApJ, 490, 792, doi: [`10.1086/304897`](http://doi.org/10.1086/304897)

(ref: Miotello+2023) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501, doi: [`10.48550/arXiv.2203.09818`](http://doi.org/10.48550/arXiv.2203.09818)

(ref: Miotello+2016) Miotello, A., van Dishoeck, E. F., Kama, M., & Bruderer, S. 2016, A&A, 594, A85, doi: [`10.1051/0004-6361/201628159`](http://doi.org/10.1051/0004-6361/201628159)

(ref: Murphy+2018) Murphy, E. J., Bolatto, A., Chatterjee, S., et al. 2018, in Astronomical Society of the Pacific Conference Series, Vol. 517, Science with a Next Generation Very Large Array, ed. E. Murphy, 3, doi: [`10.48550/arXiv.1810.07524`](http://doi.org/10.48550/arXiv.1810.07524)

(ref: Oberg+2023) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287, doi: [`10.1146/annurev-astro-022823-040820`](http://doi.org/10.1146/annurev-astro-022823-040820)

(ref: Oberg+2011) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, ApJL, 743, L16, doi: [`10.1088/2041-8205/743/1/L16`](http://doi.org/10.1088/2041-8205/743/1/L16)

(ref: Oberg+2021) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1, doi: [`10.3847/1538-4365/ac1432`](http://doi.org/10.3847/1538-4365/ac1432)

(ref: Pinte+2018) Pinte, C., Ménard, F., Duchêne, G., et al. 2018, A&A, 609, A47, doi: [`10.1051/0004-6361/201731377`](http://doi.org/10.1051/0004-6361/201731377)

(ref: Qi+2011) Qi, C., D’Alessio, P., Öberg, K. I., et al. 2011, ApJ, 740, 84, doi: [`10.1088/0004-637X/740/2/84`](http://doi.org/10.1088/0004-637X/740/2/84)

(ref: Qi+2015) Qi, C., Öberg, K. I., Andrews, S. M., et al. 2015, ApJ, 813, 128, doi: [`10.1088/0004-637X/813/2/128`](http://doi.org/10.1088/0004-637X/813/2/128)

(ref: Qi+2013) Qi, C., Öberg, K. I., Wilner, D. J., et al. 2013, Science, 341, 630, doi: [`10.1126/science.1239560`](http://doi.org/10.1126/science.1239560)

(ref: Qi+2019) Qi, C., Öberg, K. I., Espaillat, C. C., et al. 2019, ApJ, 882, 160, doi: [`10.3847/1538-4357/ab35d3`](http://doi.org/10.3847/1538-4357/ab35d3)

(ref: Ricci+2018) Ricci, L., Isella, A., Liu, S., & Li, H. 2018, in Astronomical Society of the Pacific Conference Series, Vol. 517, Science with a Next Generation Very Large Array, ed. E. Murphy, 147

(ref: Rosenfeld+2013) Rosenfeld, K. A., Andrews, S. M., Hughes, A. M., Wilner, D. J., & Qi, C. 2013, ApJ, 774, 16, doi: [`10.1088/0004-637X/774/1/16`](http://doi.org/10.1088/0004-637X/774/1/16)

(ref: Salinas+2017) Salinas, V. N., Hogerheijde, M. R., Mathews, G. S., et al. 2017, A&A, 606, A125, doi: [`10.1051/0004-6361/201731223`](http://doi.org/10.1051/0004-6361/201731223)

(ref: Teague2019) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: Teague+2018) Teague, R., & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173, doi: [`10.3847/2515-5172/aae265`](http://doi.org/10.3847/2515-5172/aae265)

(ref: vanderTak+2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: vanderWalt2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: vantHoff+2017) van ’t Hoff, M. L. R., Walsh, C., Kama, M., Facchini, S., & van Dishoeck, E. F. 2017, A&A, 599, A101, doi: [`10.1051/0004-6361/201629452`](http://doi.org/10.1051/0004-6361/201629452)

(ref: Virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Williams+2014) Williams, J. P., & Best, W. M. J. 2014, ApJ, 788, 59, doi: [`10.1088/0004-637X/788/1/59`](http://doi.org/10.1088/0004-637X/788/1/59)

(ref: Wilson1999) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143, doi: [`10.1088/0034-4885/62/2/002`](http://doi.org/10.1088/0034-4885/62/2/002)

(ref: Zhang+2017) Zhang, K., Bergin, E. A., Blake, G. A., Cleeves, L. I., & Schwarz, K. R. 2017, Nature Astronomy, 1, 0130, doi: [`10.1038/s41550-017-0130`](http://doi.org/10.1038/s41550-017-0130)

(ref: Zhang+2021) Zhang, K., Booth, A. S., Law, C. J., et al. 2021a, ApJS, 257, 5, doi: [`10.3847/1538-4365/ac1580`](http://doi.org/10.3847/1538-4365/ac1580)

(ref: ZhangS+2021) Zhang, S., Hu, X., Zhu, Z., & Bae, J. 2021b, ApJ, 923, 70, doi: [`10.3847/1538-4357/ac2c82`](http://doi.org/10.3847/1538-4357/ac2c82)

[^1]: <https://casaguides.nrao.edu/index.php/Simulating_ngVLA_Data-CASA5.4.1>

[^2]: <https://almascience.nrao.edu/proposing/sensitivity-calculator>

[^3]: <https://ngect.nrao.edu/>

</paper>

Write the methods card for this paper.