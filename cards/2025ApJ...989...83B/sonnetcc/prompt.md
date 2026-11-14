# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989...83B\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989...83B",
 "title": "CO Emission and Absorption-line Survey of the M87 Nucleus Using Archival ALMA Imaging",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Boizelle, Benjamin D.",
 "n_authors": 8,
 "arxiv_id": "2503.03249",
 "doi": "10.3847/1538-4357/adea52",
 "alma_projects_linked_by_archive": [
  "2012.1.00661.S",
  "2013.1.00073.S",
  "2013.1.01022.S",
  "2015.1.00030.S",
  "2015.1.01170.S",
  "2015.1.01352.S",
  "2016.1.00021.S",
  "2016.1.01154.V",
  "2017.1.00608.S",
  "2017.1.00841.V",
  "2017.1.00842.V",
  "2019.1.00807.S",
  "2021.1.01398.S"
 ]
}
```

Paper text:
<paper>
# CO Emission and Absorption-line Survey of the M87 Nucleus Using Archival ALMA Imaging

## Abstract

We present an M87 molecular line search from archival Atacama Large Millimeter/sub-millimeter Array (ALMA) imaging, covering the circumnuclear disk (CND) as well as ionized gas filaments and dusty cloud regions. We find no evidence for CO emission in the central $\sim$kpc and place an upper limit of $M_\mathrm{H_2} < 2.3\times 10^5$ $M_\odot$ in the atomic gas CND region, a factor of 20$\times$ lower than previous surveys. During this search, we discovered extragalactic CO absorption lines in the $J$ = 1$-$0, 2$-$1, and 3$-$2 transitions against the bright (Jy-scale) active nucleus. These CO lines are narrow ($\sim$5 km s$^{-1}$) and blueshifted with respect to the galaxy’s systemic velocity by $-$75 to $-$84 km s$^{-1}$. This CO absorber appears to be kinematically distinct from outflowing atomic gas seen in absorption. Low integrated opacities ranging from $\tau_\mathrm{CO} \sim 0.02-0.06$ km s$^{-1}$ and a column density $N_\mathrm{CO} \approx (1.2\pm0.2)\times 10^{15}$ cm$^{-2}$ translate to $N_\mathrm{H_2} \sim (1-2) \times 10^{20}$ cm$^{-2}$. CO excitation temperatures spanning $T_\mathrm{ex} \sim 8$ K to $\sim$30 K do not follow local thermodynamic equilibrium (LTE) expectations, and non-LTE `radex` radiative transfer modeling of the CO absorber is consistent with a number density $n_\mathrm{H_2} \sim 5000$ cm$^{-3}$ embedded in a $\sim$60 K environment. Taken together, the observed CO absorption lines are most consistent with a thin, pressure-confined filament seen slightly off-center from the M87 nucleus. We also explore the impact of residual telluric lines and atmospheric variability on narrow extragalactic line identification and demonstrate how bandpass calibration limitations may introduce broad but very low S/N and spurious absorption and emission signatures.

# Introduction

Ongoing gas accretion onto supermassive black holes (BHs; with masses $\ensuremath{M_\mathrm{BH}}\sim 10^5 - 10^{10}$ $M_\odot$) powers active galactic nuclei (AGN) at the centers of galaxies. In extreme cases, highly efficient central engines are visible across the observable universe. A wide range of AGN phenomena – including broad and/or narrow emission lines, a very hot accretion disk, and large-scale jets of relativistic plasma – are explained in the AGN standard model primarily by different viewing angles and accretion rates (cite: tadhunter08; trump11; bianchi12; heckman14). A subset of these AGN are radio bright with collimated jet features, typically classified as either type I (centrally dominant or edge-darkened continuum emission) or type II (edge-brightened) Fanaroff-Riley galaxies (cite: fanaroff74).

M87 (NGC 4486) is one of the most well-studied luminous early-type galaxies (cite: devauc91), in large part due to its close proximity in the Virgo cluster and as the brightest galaxy of the Virgo A subgroup. This FR I galaxy is also well studied due to its central narrow-lined, low-ionized nuclear emission-line region (cite: ho97; dopita97). The active nucleus is bright across mm to radio wavelengths (with central flux density $S_\nu \gtrsim 1$ Jy) and launches jets seen primarily on the approaching side across radio to X-ray wavelengths (cite: marshall02; kim18), connecting to radio lobes that extend out to a projected $\sim$3 kpc (cite: chiaberge99). The mass accretion rate of M87 is very low, between $\dot{M}_\mathrm{BH}<10^{-3} - 10^{-2}$ $M_\odot$ yr$^{-1}$ or an Eddington fraction $\dot{M}_\mathrm{BH}/\dot{M}_\mathrm{Edd} \lesssim (0.15-1.5)\times 10^{-3}$ (cite: kuo14; inayoshi20). Together with many other radio galaxies, M87 lies in a transition region between cold, thin disk accretion and radiatively inefficient accretion flows.

M87 garnered significant additional attention during the Event Horizon Telescope (EHT) very large baseline interferometry (VLBI) campaigns that imaged its BH shadow on $\sim$25 $\mu$as scales and also connected gas accretion and magnetic field structures very close to the BH and the jet launching region (cite: event19; event21a; event21b). Modeling of both the EHT visibilities and separate stellar kinematics returned a consistent BH mass ranging between $(5.4-6.5)\times 10^9$ $M_\odot$ (cite: gebhardt09; event19; liepold23; simon24). Earlier gas-dynamical modeling efforts had preferred an $M_\mathrm{BH}$ only half as massive (cite: harms94; macchetto97; walsh13), although recent work has brought the gaseous results into good agreement (cite: osorno23).

Early ground-based and Hubble Space Telescope (HST) imaging revealed filaments of ionized gas extending out several kpc from the M87 nucleus (cite: sparks93; ford94; pogge00). It is unclear if this gas is related to known merger activity (cite: longobardi15), or even if the gas in the central few kpc is infalling towards the BH (cite: gaspari13) or is being disturbed by rising bubbles or the radio jet (cite: Olivares2019). In some massive elliptical or cD galaxies like M87, spectral energy distribution (SED) fitting (cite: yuan14) suggests hot-mode accretion dominates most of the time, even if a gaseous circumnuclear disk (CND) is clearly detected.

Many FR I galaxies host morphologically regular, geometrically thin disks with relatively small radii (cite: dekoff00; saripalli12). These CNDs are often identified by dusty disks or lanes, and molecular line surveys have revealed modest cospatial H$_2$ mass reservoirs (cite: ocana10; prandoni10; boizelle17; boizelle21; ruffa19; tadhunter24). Unfortunately, the bright optical AGN and jet of M87 prevent any definitive conclusions about dust absorption on the smallest scales (cite: pogge00). On larger scales, its filamentary gas appears to connect to an ionized-gas CND with well-ordered rotation out to $R\sim0.5\ensuremath{''}$ (cite: sparks93; ford94; walsh13; boselli19; osorno23). Atomic gas line-of-sight (LOS) speeds ($v_\mathrm{LOS}$) for this rotation reach roughly $\pm 500$ km s$^{-1}$ in the inner $R\lesssim 0.1\ensuremath{''}$ from the galaxy’s systemic velocity $\ensuremath{v_\mathrm{sys}}\equiv cz_\mathrm{obs} = 1284\pm 5$ km s$^{-1}$ from stellar absorption-line fits with a heliocentric $z_\mathrm{obs} = 0.004283$ (cite: cappellari11).

Despite the mostly ordered central velocity field, maps of the atomic emission-line dispersion $\ensuremath{\sigma_\mathrm{LOS}}$ show asymmetries in the northwest direction that suggest a bi-conical outflow with intrinsic speeds reaching out to $\sim$400 km s$^{-1}$ along a position angle PA $\sim -45\ensuremath{^\circ}$ (cite: sparks93; boselli19; osorno23). Further support for an outflow comes from UV/optical absorption lines detected against the bright nucleus, although this may reveal a kinematically distinct component. These atomic tracers show blueshifted absorption lines with $\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}\sim -131\pm 19$ km s$^{-1}$ and moderate intrinsic FWHM $\lesssim 300$ km s$^{-1}$ (cite: tsvetanov99b; sabra03). Absorption-line measurements as well as modeling of the central X-ray spectrum both support hydrogen column densities in the $N_\mathrm{H} \sim 10^{19} - 10^{20.7}$ cm$^{-2}$ range (cite: wilson02; dimatteo03; sabra03).

![](m87_hst_almaco_display.pdf)

Within the central few kpc of M87 (out to at least $\sim$40$''$), molecular gas is best traced in the optical by discrete, low-extinction filaments and clouds. Similar dusty features are observed in the inner $\sim$kpc of most luminous elliptical galaxies in high-density environments (cite: mathews03; temi18; tremblay18; Olivares2019), often following ionized atomic emission-line filaments (cite: sparks93; ferrarese06; madrid07; boselli19; taylor20). For M87, no central extinction is detected down to $R\sim 0.15\ensuremath{''}$ (cite: prieto21). Evidence for the corresponding thermal dust continuum is ambiguous and global SED fits are often interpreted as showing no evidence for diffuse dust and limited support for circumnuclear dust (cite: perlman01; xilouris04; buson09; baes10). However, a couple of elevated SED points or mid-IR spectra (cite: shi07; perlman07) have been tied to a cold dust component with characteristic temperature $T_\mathrm{dust} \sim 25-55$ K with mass $M_\mathrm{dust} < 7\times 10^4$ $M_\odot$ (cite: baes10).

Molecular gas that is expected to accompany the filamentary dust has remained elusive. Single-dish mm/sub-mm imaging of this target did not detect global $^{12}$CO (hereafter CO) emission in the $J=1-0$ transition across a velocity range of a few hundred km s$^{-1}$, first with an initial 1$\sigma$ line flux upper limit of $S_\mathrm{CO(1-0)}\Delta v < 20$ Jy km s$^{-1}$ (cite: bieging81; jaffe87; braine93) and later a 3$\sigma$ upper limit of 10.2 Jy km s$^{-1}$ (cite: combes07; salome08). From interferometric observations with the Submillimeter Array (SMA), (cite: tan08) reported a tentative $S_\mathrm{CO(2-1)}\Delta v \approx 8.8\pm2.2(\mathrm{stat})\pm1.8(\mathrm{sys})$ Jy km s$^{-1}$ detection (with separate 1$\sigma$ statistical and systematic uncertainties) in an $\sim$80 pc-diameter aperture about the nucleus. If correct, the corresponding total H$_2$ mass $M_\mathrm{H_2} \lesssim 5\times 10^6$ $M_\odot$ could be detected using the Atacama Large Millimeter/submillimeter Array (ALMA), which provides an order-of-magnitude improvement in both angular resolution and limiting sensitivity over previous mm-wavelength interferometers.

In this paper, we present a detailed mm/sub-mm wavelength molecular line search of the M87 nucleus using ALMA archival data. In a more brief study, (cite: ray24) analyzed the earliest two of these ALMA data sets and purport to detect and resolve central CO emission with $S_\mathrm{CO(1-0)}\Delta v = 3.85\pm0.4$ Jy km s$^{-1}$. The corresponding $M_\mathrm{H_2} \sim 10^7$ $M_\odot$ is claimed to originate in a CND that extends out to at least $R\sim 100$ pc. They also identify absorption-line features against the bright nucleus. We cannot recover similar emission-line results, and nor do we support their absorption-line measurements. In our data calibration description and spectral measurements, we will reference their claims as needed.

This paper is structured as follows. In Section [2](#sec:data_overview), we introduce archival HST and ALMA data sets and imaging processes. Section [3](#sec:line) describes the CO emission-line search and CO absorption-line detection. We constrain molecular gas properties in Section [4](#sec:disc) and conclude in Section [5](#sec:conc). In the extensive appendices, we provide more in-depth analysis concerning extragalactic spectral line identification with ALMA, including the impact of atmospheric (ozone) variability and the possibility of spurious broad line detection due to bandpass calibration limitations.

Throughout, we assume a standard $\Lambda$CDM cosmology with $H_0 = 67.8$ km s$^{-1}$ Mpc$^{-1}$ along with $\Omega_\mathrm{m} = 0.308$ and $\Omega_\Lambda = 0.692$ (cite: planck2016). We adopt a distance modulus $m-M = 31.11\pm0.08$ mag for M87 from surface brightness fluctuation methods corresponding to a luminosity distance $D_L \sim 16.7\pm0.6$ Mpc (cite: blakeslee09). After correcting the observed redshift $z_\mathrm{obs} = 0.004283$ for infall towards the Virgo cluster (cite: mould00), this $D_L$ translates to an angular size scale of 80.5 pc arcsec$^{-1}$. We employed the optical velocity definition and referenced kinematic quantities in the barycentric frame by default.

# Data

## Optical Imaging

To create integration regions for this ALMA CO line search, we employed pipeline-calibrated HST images retrieved from the Mikulski Archive for Space Telescopes (DOI: ). To isolate dust features, we used drizzled Wide Field Camera 3 (cite: dressel22) F475W imaging from program GO-14256 (PI: Biretta). To map out filamentary H$\alpha$+\[N II\] emission, we used a series of Advanced Camera for Surveys (cite: ryon22) F660N polarized images from program GO-12271 (PI: Sparks) that we aligned before combining into a single Stokes $I$ image. In each case, we modeled and subtracted the stellar continuum using a concentric Multi-Gaussian Expansion (cite: emsellem94) with uniform PAs using `GALFIT` (cite: peng02). Following (cite: davidson24), we iteratively expanded a pixel mask containing non-stellar features (gas and dust, the optical jet, and central AGN) to avoid contaminating the stellar fit. Figure [1](#fig:hst) shows the final gas emission and dust absorption maps. In Section [3.1](#sec:narrowem), we describe the regions created for the CO emission-line search.

## Archival ALMA Imaging

We obtained archival ALMA 12-m imaging from eleven single-pointing data sets taken between 2013 December 1 and 2018 September 25 whose phase centers coincided with the M87 nucleus (see Appendix [6](#app:cont) and Table [3](#tbl:sample) for additional details). In this nearly five-year window, one semipass program (2016.1.000415.S; PI: Marti-Vidal) was not included due to pipeline calibration difficulties arising from changing polarization calibrators between Execution Blocks (cite: goddi21). Another program (2013.1.00862.S; PI: Simionescu) was centered $\sim$40$''$ south-east of the nucleus to image CO(2$-$1) in a dust and gas complex (cite: simionescu18), and the field of view does not cover the M87 nucleus.

We also retrieved and analyzed ALMA Compact Array (ACA) 7-m observations in programs 2019.1.00807.S and 2021.1.01398.S. Due to large average FWHM of the synthesized beam $\overline{\theta}_\mathrm{FWHM} \gtrsim 5\ensuremath{''}$ and poorer limiting sensitivity compared to the ALMA 12-m data, these 7-m observations are only used for an analysis of the peak SED and to construct a light curve of the bright nucleus. We briefly discuss the ACA data sets, their calibration processes, and results in Appendix [7](#app:specslope) and Table [4](#tbl:aca_cont).

### ALMA Data Properties

The majority of the programs listed in Table [3](#tbl:sample) were explicitly designed to probe nuclear continuum properties, although not all of these programs were obtained in time division mode (TDM). These heterogeneous data cover Bands 3, 4, 6, and 7 with $\overline{\theta}_\mathrm{FWHM}$ ranging from $\sim$0.03$''$ to 2.3$''$. The chosen spectral setups resulted in spectral resolutions from $\sim$1 to 63 MHz (after online Hanning smoothing). Both TDM-only and frequency division mode (FDM) data included dual and full polarization setups. For continuum-focused programs, a few redshifted atomic or molecular transitions (including low-$J$ CO) coincidentally lie within the spectral ranges, albeit at coarse spectral resolution ($\sim$20–100 km s$^{-1}$) at the native binning. Primary spectral windows (spws) for CO-line focused programs typically have velocity resolutions of $\sim$1–3 km s$^{-1}$. Calibrator observations of M87 were not included due to generally short integrations (cite: doi13).

![](m87_alma_archive_contmod_combinedfigure.pdf)

### Calibration Processes

In general, we applied standard pipeline calibrations to the 12-m data using the appropriate `Common Astronomy Software Application` (cite: mcmullin07) pipeline version for each data set in order to construct Measurement Sets (MSs). Below, we discuss limited improvements to the standard pipeline calibration processes. Appendices [8](#app:peak) and [11](#app:constraints) contain additional discussion of the bandpass calibration.

In adjacent or overlapping spws, peak continuum spectra show mismatches at the 1–3% level, which is roughly consistent with relative flux calibration errors (cite: francis20b). For projects 2015.1.00030.S and 2016.1.00021.S, these slight discrepancies complicated the $uv$-plane continuum subtraction for channel ranges with overlapping spws. Residual mismatches at the $\sim$0.1% level impacted the search for very broad absorption or emission (see Figure [9](#fig:contabs) and Appendix [11.2](#app:broademission)). We manually re-scaled their flux calibrator `fluxdensity` Stokes $I$ levels in the `setjy` task for individual spws by up to 2% to ensure more continuous flux densities in image-plane spectral cubes.

We applied phase (and usually amplitude) self-calibration with final solution intervals that were per integration (per scan). In two cases in member OUSs A001/X12f/X20d and A002/X6444ba/X1b0, amplitude self-calibration was not adopted when the multi-frequency synthesis (MFS) image peak/rms dynamic range (DR) decreased noticeably compared to the final phase-only products. DRs spanned from several hundred up to $\sim$9000, far exceeding the more typical $\sim$100 without improved phase solutions (cite: richards22; privon24). The highest $\mathrm{DRs} \gtrsim 5000$ were all obtained in Band 3. For certain other ALMA programs with bright continuum sources, higher DRs have been achieved with more careful, per-scan analysis (cite: komugi22), especially when using brighter bandpass calibrators. However, those typically used for M87 are at the $>$2 Jy-level in Bands 3–7, effectively forestalling improved bandpass solution approaches (cite: oosterloo24). The CO data cubes discussed in Section [2.2.4](#sec:data_imaging) have spectral dynamical ranges (SDRs) that exceed $\sim$2000 per native (unbinned) channel in Band 3, although the bandpass stability limit imposes an effective SDR $< 1000$ limit over large frequency ranges (see Appendix [11.3](#app:bandpass)).

Three programs (2016.1.01154.V, 2017.1.00841.V, and 2017.1.00842.V) were obtained as a part of EHT+ALMA VLBI campaigns and most of their MSs coincidentally cover the redshifted CO(2$-$1) line. From the ALMA archive, the available .V datasets only contain columns and calibration tables pertaining to the phased (APP) observing mode. As is shown in Figure [9](#fig:contabs), APP-mode spectra show a characteristic scalloping pattern due to sets of 16 native channels (with individual binning $\Delta \nu_\mathrm{obs} = 7.81$ MHz) being used for coarse frequency-dependent phase solutions. We adopted the APP-mode results since other projects covered redshifted CO(2$-$1) and because reconstructing the ALMA interferometric-mode calibration tables is beyond the scope of this archival project (cite: goddi19). Without interferometric-mode calibration tables, phase self-calibration is not possible, and the peak (core) flux densities reported in Table [3](#tbl:sample) are lower by about 30% (cite: event21c; event24). The scalloping spectral behavior prevents their inclusion in studies of broader line features ($\Delta v \gtrsim 50$ km s$^{-1}$), although some .V program data do reveal narrow absorption near redshifted $\nu_\mathrm{CO(2-1)}$.

### Manual Flagging

For dual polarization data obtained during ALMA Early Science, or for full polarization data when that was still a non-standard observing mode, calibration scripts from the archive often included manual flagging of the science target as well as the flux and bandpass calibrators. We manually flagged a limited number of additional visibilities based on high antenna temperature, amplitude disagreement, and poor bandpass calibration near spw edges. For the MS from member Observing Unit Set A001/X12f/X20f (hereafter X20f and likewise for other member OUS), the pipeline script manually flagged a moderately strong and variable atmospheric line in the bandpass calibrator as extragalactic in origin. This introduced a spurious and deep absorption feature in the peak continuum spectrum of M87 that was coincidentally very close to redshifted $\nu_\mathrm{CO(2-1)}$ (cite: ray24). Removing these manually-flagged channels, re-calibrating the raw visibilities, and re-imaging a new MS resulted in more consistent spectral behavior. Appendix [9](#app:atm) contains more discussion about atmospheric line identification and variability.

### MFS and Spectral Imaging

As a part of the self-calibration loops, we imaged each MS into a Stokes $I$ MFS map using Briggs weighting (cite: briggs95) in the `CASA` `tclean` deconvolution process. This weighting approach balanced sensitivity and angular resolution considerations. Some of these data were also deconvolved into MFS images using uniform (natural) weighting for greater resolution (sensitivity). Primary imaging results are given in Table [3](#tbl:sample) while Figure [2](#fig:mfs) shows MFS imaging for a representative sample of this archival project. Additional MFS imaging details and a brief continuum analysis are found in Appendices [6](#app:cont) and [7](#app:specslope). A more detailed analysis of the nuclear and extended continuum properties is beyond the scope of this paper but is covered in recent ALMA studies of the inner accretion flow and jet behavior (cite: lu23) as well as core and jet polarization (cite: goddi21; event21b; event21a; event21c). Recent radio interferometric and VLBI studies have revealed detailed jet motion and internal structure (cite: hada16; hada17b; hada17a; pasetto21).

High spectral resolution ALMA imaging of AGN have also revealed both Galactic and extragalactic narrow molecular absorption lines (cite: klitsch19; rose19b; rose24). To that end, we first imaged each spw (or set of overlapping spws) using `tclean` with Briggs ($r=0.5$) weighting at the native channel binning given in Table [3](#tbl:sample), resulting in 72 continuum-dominated spectral cubes with a common restoring beam for each spectral setup. Peak flux densities are plotted in Figure [9](#fig:contabs) across all unflagged frequencies for the entire sample. Absolute flux calibration uncertainties for MFS images and spectral cubes is about 5% in Band 3 and 10% in Bands 6 and 7 (cite: fomalont14; francis20b; privon24). For most spws in the archival sample, channels are coarsely binned ($\Delta v \sim 20-100$ km s$^{-1}$). Only four projects (2012.1.00661.S, 2013.1.00073.S, 2015.1.00030.S, and 2016.1.00021.S) have sufficiently fine FDM channels ($\Delta \nu_\mathrm{obs} \sim 0.6-3$ km s$^{-1}$) to enable detection of narrow molecular lines.

Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions. In the first and second cases, we excluded channels corresponding to either $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 500$ km s$^{-1}$ to probe more standard velocity ranges for extragalactic gas or $<$1000 km s$^{-1}$ for higher-amplitude rotation or outflow scenarios. Given the truncated CO(3$-$2) velocity coverage in program 2012.1.00661.S, for the second case we only excluded the range $-1000 < \ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}< 400$ km s$^{-1}$ when subtracting the Band 7 continuum. In a third case for CO(1$-$0) only, we excluded the ranges $100 < |\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 2200$ km s$^{-1}$ to test for possible broad emission-line features that may originate from a pc-scale molecular CND. In this final case, including channels where $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 100$ km s$^{-1}$ helped to anchor the continuum subtraction near $v_\mathrm{sys}$ where any integrated CO emission is often minimal (cite: boizelle17; smith21). We imaged the continuum-subtracted data into spectral cubes at both the native frequency spacing and at more coarse binning ($\sim$20$-$40 km s$^{-1}$) to increase the signal-to-noise ratio (S/N). In Sections [3](#sec:line) and [4](#sec:disc), we explore relatively narrow emission and absorption-line results derived using the first `uvcontsub` case. In Appendix [11](#app:constraints), we explore the second and third `uvcontsub` cases that produce very faint (and likely spurious) spectral deficits or excesses near redshifted CO transitions.

![](m87_alma_archive_emission_lineprofiles.pdf)

# Spectral Line Properties

Here, we focus on a spectral line search for extragalactic CO near the redshift of M87. ALMA spectra extracted against and around the M87 nucleus are remarkably featureless, confirming previous mm-wavelength studies in finding no strong extragalactic molecular lines in the inner $\sim$kpc (cite: braine93; tan08). Integrated line profiles and peak continuum spectra in spws covering redshifted CO result primarily in $S_\mathrm{CO} \Delta v$ upper limits and low CO opacities. Additional dense gas tracers (e.g., SiO, CS, and HCN) are covered in certain data sets. Unfortunately, the expected low abundance of isotopologues or more exotic molecules relative to CO (cite: crocker12) and coarse spectral binning for those spws only allows for a CO line search. The ALMA 12-m spectra also show no evidence for Galactic CO(1$-$0) emission or absorption more directly about the M87 nucleus, even in spectra with binning $\Delta \nu_\mathrm{obs} < 3$ MHz that could resolve narrow Galactic lines (cite: davies75; rugel18).

A detailed mm/sub-mm line search is somewhat complicated by atmospheric lines that are not always fully removed during calibration (cite: shangguan20). The residual impact is typically over a narrow frequency range and at the percent level or less, but it does affect extragalactic CO(2$-$1) detection for M87. In Appendix [9](#app:atm), we employ atmospheric transmission models to confirm the location and strength of telluric lines to avoid missing or misclassifying extragalactic lines.

## CO Emission-line Constraints

For any detectable molecular gas in M87 accompanying the CND or individual filamentary features, we expected CO emission line speeds to be similar to those of the cospatial atomic gas. Within the CND, atomic gas speeds reach about $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 500$ km s$^{-1}$. For filamentary structures out to a couple kpc, the gas speeds span $\pm$400 km s$^{-1}$ (cite: boselli19; osorno23). To conduct an efficient emission-line search, we extracted profiles from the X5 and Xa1 spectral cubes that had excluded channels with $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 500$ km s$^{-1}$ during continuum subtraction. These had the best combination of sensitivity and angular resolution to detect and isolate possible emission. Visibilities had been imaged with 20 km s$^{-1}$ channels to better match the observed CO widths of other resolved cloud structures (cite: simionescu18). We note, however, that no CO data cubes from other member OUS showed clear evidence for CO emission. (cite: ray24) highlight one channel in the X1b0 data cube that shows an apparently unresolved excess with a peak of 4.6 mJy beam$^{-1}$ (S/N $\sim 7$). In Appendix [10](#app:channel), we demonstrate that this excess is likely spurious and not part of a larger-scale CND.

+:------------+:-------------------:+:-------------------------:+:-----------------------:+:----------------:+:------------------------:+:--------------------------------------------------------------------:+:----------------:+
| Region      | Area                | $\overline{\mathrm{rms}}$ | Peak $\nu_\mathrm{obs}$ | Peak Excess      | $\nu_\mathrm{obs}$ Range | min, max($\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}$) | Range Excess     |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| Name        | ($N_\mathrm{beam}$) | (mJy)                     | (GHz)                   | (Jy km s$^{-1}$) | (GHz)                    | (km s$^{-1}$)                                                        | (Jy km s$^{-1}$) |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| \(1\)       | \(2\)               | \(3\)                     | \(4\)                   | \(5\)            | \(6\)                    | \(7\)                                                                | \(8\)            |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| **Atomic Gas Regions**                                                                                                                                                                                                          |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| 1-8 W1      | 433.5               | 4.85                      | 114.780                 | 0.380 (0.113)    | $114.741 - 114.858$      | $-205.2 , + 102.1$                                                   | $<$0.414         |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| W2          | 515.2               | 5.60                      | 114.678                 | 0.295 (0.109)    | $114.670 - 114.819$      | $-102.8 , + 286.8$                                                   | 0.639 (0.519)    |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| bar         | 595.5               | 7.57                      | 114.834                 | 0.383 (0.129)    | $114.678 - 114.788$      | $-20.9 , + 266.3$                                                    | $<$0.633         |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| loop        | 253.3               | 4.46                      | 114.741                 | 0.230 (0.073)    | $114.756 - 114.889$      | $-409.7 , + 61.1$                                                    | 0.883 (0.464)    |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| jet         | 150.0               | 4.23                      | 114.827                 | 0.276 (0.105)    | $114.741 - 114.858$      | $-205.2 , + 102.1$                                                   | 1.193 (0.355)    |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| 1-8         |                     |                           |                         |                  |                          |                                                                      |                  |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| 1-8 W1 dust | 45.9                | 2.32                      | ...                     | ...              | $114.741 - 114.858$      | $-205.2 , + 102.1$                                                   | $<$0.191         |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| filament    | 20.9                | 1.44                      | ...                     | ...              | $114.717 - 114.842$      | $-164.3 , + 163.6$                                                   | 0.502 (0.123)    |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| dense       | 10.1                | 1.00                      | ...                     | ...              | $114.717 - 114.842$      | $-164.3 , + 163.6$                                                   | $<$0.085         |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| 1-8         |                     |                           |                         |                  |                          |                                                                      |                  |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| 1-8 nucleus | 12.9                | 0.69                      | ...                     | ...              | $114.585 - 114.976$      | $-514.0 , + 510.6$                                                   | $<$0.109         |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+
| annulus     | 10.8                | 0.68                      | ...                     | ...              | $114.585 - 114.976$      | $-514.0 , + 510.6$                                                   | $<$0.085         |
+-------------+---------------------+---------------------------+-------------------------+------------------+--------------------------+----------------------------------------------------------------------+------------------+

: M87 CO(1$-$0) Emission-line Constraints

Table notes: CO(1$-$0) emission upper limits near the center of M87 from the Xa1 spectral cube with 20 km s$^{-1}$ binning and typical rms $\sim 0.4$ mJy beam$^{-1}$ per channel. Regions listed in col. (1) are shown in Figure [1](#fig:hst) with corresponding beam-unit areas in col. (2). Col. (3) is the rms within each integration region averaged over the entire line profile. Cols. (4) and (5) give frequencies and integrated fluxes for the single channel with the highest flux density (if above S/N $\gtrsim 3$) in each region. Cols. (6) and (7) give the channel frequency ranges and velocity endpoints corresponding to $\pm$100 km s$^{-1}$ from the observed spread of atomic gas $v_\mathrm{LOS}$ in each region or $\pm$150 km s$^{-1}$ about $v_\mathrm{sys}$ for the dust-dominated regions. Col. (8) reports the possible CO fluxes (or upper limits) in these regions. Note that the peak excess in the integrated CO profile in Figure [3](#fig:lineprof) does not always fall within the velocity integration ranges. Estimated 1$\sigma$ uncertainties (parentheses) were calculated by Monte Carlo resampling of the background noise using the same region shapes.

In Figure [1](#fig:hst), we trace broad regions of diffuse ionized atomic gas emission and higher H$\alpha$/H$\beta$ decrement (cite: sparks04; osorno23) as well as more compact regions that cover higher dust opacities (cite: taylor20). A final region in the jet (covering clumps A, B, and C; Figure [2](#fig:mfs)) probes molecular gas in the shocked, higher-pressure ISM (cite: bicknell96). From the F475W residual image, the dense dust region has an estimated intrinsic (deconvolved) maximum length of $\lesssim$65 pc; without the filamentary structure connecting on the east, however, the deepest absorption is more consistent with a width of $\sim$20 pc. The neighboring dusty filament and those in the W1 and loop regions appear to have intrinsic diameters of up to a few pc. Another dusty filament not covered in these apertures appears to span from the dense cloud to the west side of the loop region and comes close to the nucleus (cite: event21c).

In Figure [3](#fig:lineprof) and Table [1](#tbl:narrowem), we present integrated CO(1$-$0) line profiles and fluxes for the intermediate-resolution Xa1 data set ($\overline{\theta}_\mathrm{FWHM} \sim 0.21\ensuremath{''}$). These line profiles reveal no unambiguous CO emission in any region, and the higher-resolution X5 data yields $\sim$2$\times$ poorer constraints due to the larger number of beams in each integration area. In regions where there is cospatial atomic gas seen in the F660N filter, we integrated line profiles over the range of atomic gas $v_\mathrm{LOS}$ observed in (or around) these regions with an additional $\pm$100 km s$^{-1}$ buffer. In dust-dominated regions seen primarily in the F475W filter, line profiles were integrated over a $\sim$300 km s$^{-1}$ range centered on $v_\mathrm{sys}$. To encompass the entire atomic gas CND, we integrated over a circular aperture with a radius $R = 0.5\ensuremath{''}$ ($\sim$40 pc). An additional annulus integration between $0.2\ensuremath{''}<R<0.5\ensuremath{''}$ avoided larger nuclear residuals while still covering most of the ionized gas emission observed by (cite: osorno23).

To estimate uncertainties, we followed a Monte Carlo (MC) resampling technique that iteratively shifted each region by a random amount before re-integrating (cite: boizelle17). After 200 iterations, we adopted the standard deviation of these “blank” flux densities in each channel as a good proxy for the true uncertainty spectrum (cite: tsukui23). In some cases, the spread in “blank” flux densities is slightly higher (by at most 10%) due to the impact of the primary beam correction further from the ALMA phase center, but this does not materially affect the analysis.

Based on the estimated noise spectra, the highest S/N candidate for CO emission is in the outer jet feature with an integrated $S_\mathrm{CO(1-0)}\Delta v \approx 1.19 \pm 0.36$ Jy km s$^{-1}$ that just exceeds the 3$\sigma$ threshold. However, a channel-by-channel inspection of the integration over the velocity range shows no clear features. The dust filament and loop regions show positive features near $v_\mathrm{sys}$ at $2\sigma-3\sigma$ confidence, but the bulk of the signal being contained in 1$-$2 channels is not altogether convincing. Channel inspection did not reveal any likely discrete sources at those corresponding velocities (or elsewhere). A global CO(1$-$0) line profile integrated over the inner $\sim$2 kpc returns only an $S_\mathrm{CO(1-0)}\Delta v < 4.8$ Jy km s$^{-1}$ 1$\sigma$ upper limit over the entire $\pm$500 km s$^{-1}$ range.

The nuclear and annulus spectra also show no support for CO(1$-$0) emission. From typical rms uncertainties of 0.68 mJy beam$^{-1}$ in a 20 km s$^{-1}$ channel, we estimated nuclear $S_\mathrm{CO(1-0)} \Delta v < 0.109$ Jy km s$^{-1}$ (1$\sigma$ uncertainty) in a broad $|\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}| < 500$ km s$^{-1}$ range to match the extraction region and velocity range of the previous SMA CO(2$-$1) study (cite: tan08). The annulus region spectrum is better behaved than the composite nuclear spectrum, which shows excesses at large velocity offsets ($|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| \gtrsim 800$ km s$^{-1}$) due to higher continuum residuals directly at the nucleus location. In Appendix [11](#app:constraints), we discuss the anomalous spectral behavior when excluding an even broader channel range in the `uvcontsub` process.

## CO Absorption-line Properties

Despite the lack of any CO detection in emission, close inspection of the peak continuum spectra across 6 data sets in Figure [4](#fig:colineabsfit) reveals blueshifted CO(1$-$0), CO(2$-$1), and CO(3$-$2) absorption features between $-84 < \ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}< -75$ km s$^{-1}$. Only one CO spw with narrow $\Delta \nu_\mathrm{obs} \lesssim 1$ MHz binning from the X1b0 data set returns a non-detection, and its more complicated spectral response shown in Figure [9](#fig:contabs) is ameliorated by using just the lowest-rms data from the second EB[^1] However, this more selective spectrum still appears featureless (see Figure [4](#fig:colineabsfit)) due to a sensitivity limit that exceeds the expected opacity spectrum in the common definition:

$$\begin{equation}
    \tau_\nu = -\ln \left(\frac{T_\nu}{T_{\nu,\mathrm{cont}}}\right)\,.
\end{equation}$$

Here, the peak continuum spectrum $T_\nu \propto S_\nu/\theta_\mathrm{maj}\theta_\mathrm{min}$ is measured in K units and $T_{\nu,\mathrm{cont}}$ is the fitted linear continuum level about the CO line feature. For the most confident cases, the measured peak $\tau_0 \lesssim 0.004$ values are much lower than for CO absorption lines observed in other ETGs (cite: boizelle17; ruffa19; klitsch19; rose19b; rose19a; rose20; rose24; kameno20). No other potential extragalactic CO or dense gas absorption lines are seen at a consistent $\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}$ across multiple data sets or transitions, including at the same $\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}\sim -131$ km s$^{-1}$ for the atomic-gas absorber.

From these opacity spectra, we also calculated upper limits of the integrated line opacity

$$\begin{equation}
    \tau_\mathrm{CO} = \int \tau_\nu dv
\end{equation}$$

for CO absorption in km s$^{-1}$ units. Across these three transitions, the $\tau_\mathrm{CO} \sim 0.02-0.05$ km s$^{-1}$ range (with a median $\mathrm{S/N} \sim 4$) is very low and better matches the bottom end of the $\tau_\mathrm{CO}$ distribution for Galactic diffuse molecular clouds (cite: liszt98; liszt12; liszt19).

![image](m87_alma_archive_cont_absfit.pdf) ![image](m87_coabs_kin_Xa1.pdf)

CO(2$-$1) absorption lines are detected less confidently than are those for CO(1$-$0), with an extreme case from the X20d data that has just S/N $\sim 1.4$ for its $\tau_\mathrm{0,CO(2-1)}$ measurement. The $\tau_\mathrm{CO(2-1)}$ values may be suppressed by $\sim$20$-$30% due to difficulty in fully removing the neighboring ozone line contamination (see Appendix [9](#app:atm)). Two APP-mode programs cover the redshifted $\nu_\mathrm{CO(2-1)}$, but these peak spectra display frequency-dependent fluctuations due to phasing all elements together into a single array. Some of these .V program spectra appear to show CO(2$-$1) absorption (see Figure [9](#fig:contabs)), but we only utilize spectral fits to the most regular Xb data set from program 2016.1.01154.V when calculating CO absorber properties.

+:----------------------+:-----------------:+:------------------:+:---------------------------------------------------------:+:-------------:+:-------------:+:-------------------:+:------------------:+
| Member                | rms               | $\nu_\mathrm{LOS}$ | $\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}$ | $\sigma_\mathrm{LOS}$         | $\tau_0$            | $\tau_\mathrm{CO}$ |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| OUS                   | (mJy beam$^{-1}$) | (GHz)              | (km s$^{-1}$)                                             | (MHz)         | (km s$^{-1}$) |                     | (km s$^{-1}$)      |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| \(1\)                 | \(2\)             | \(3\)              | \(4\)                                                     | \(5\)         | \(6\)         | \(7\)               | \(8\)              |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| **CO(1$-$0)**                                                                                                                                                                                         |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| 1-8 A002/X6444ba/X1b0 | 2.61              | ...                | ...                                                       | ...           | ...           |                     | $<0.056$           |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| A001/X2d8/X5          | 0.91              | 114.808 (0.000287) | $-$78.45 (0.75)                                           | 1.204 (0.317) | 3.13 (0.82)   | 0.002286 (0.000785) | 0.0220 (0.0059)    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| A001/X899/Xa1         | 1.15              | 114.807 (0.000468) | $-$76.38 (1.22)                                           | 2.275 (0.526) | 5.92 (1.37)   | 0.002483 (0.000735) | 0.0361 (0.0068)    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| 1-8                   |                   |                    |                                                           |               |               |                     |                    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| 1-8 A001/X12f/X20d    | 2.38              | 229.609 (0.001600) | $-$75.29 (2.08)                                           | 3.012 (1.977) | 3.92 (2.57)   | 0.002989 (0.002185) | 0.0325 (0.0078)    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| A001/X12f/X20f        | 1.89              | 229.610 (0.000533) | $-$76.31 (0.69)                                           | 4.259 (0.527) | 5.54 (0.69)   | 0.003904 (0.000677) | 0.0438 (0.0053)    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| A002/Xbee37d/Xb       | 0.85              | 229.612 (0.001210) | $-$78.94 (1.57)                                           | 3.211 (1.340) | 4.18 (1.73)   | 0.005798 (0.003290) | 0.0461 (0.0109)    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| 1-8                   |                   |                    |                                                           |               |               |                     |                    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+
| 1-8 A002/X6444ba/X1b4 | 0.95              | 344.412 (0.003276) | $-$83.58 (2.84)                                           | 7.119 (3.592) | 6.17 (3.11)   | 0.003418 (0.002263) | 0.0574 (0.0174)    |
+-----------------------+-------------------+--------------------+-----------------------------------------------------------+---------------+---------------+---------------------+--------------------+

: M87 Narrow CO Absorption-line Properties

Table notes: CO absorption-line properties measured from the M87 peak continuum spectra. Col. (2) gives the typical rms noise per channel. Cols. (3) to (6) are best-fit velocity and line width parameter values from Gaussian fitting with the $\ensuremath{\sigma_\mathrm{LOS}}$ values being intrinsic widths before any online Hanning smoothing. Cols. (7) and (8) report the peak and integrated CO opacities after continuum fitting and normalization. Uncertainties in these fitted Gaussian parameters and opacities (in parentheses) were estimated using a Monte Carlo resampling technique.

To better characterize these line properties, we fit each CO absorption feature with a Gaussian line profile and a linear continuum to recover the line centroid ($\nu_\mathrm{LOS}$, $v_\mathrm{LOS}$), line width ($\sigma_\mathrm{LOS}$), and peak opacity ($\tau_0$). Results are presented in Figure [4](#fig:colineabsfit) and Table [2](#tbl:narrowabs). These fits incorporated Hanning smoothing[^2] to recover intrinsic $\sigma_\mathrm{LOS}$. We estimated parameter uncertainties by an MC resampling technique that adds random noise to the best-fitting model spectrum before refitting. The noise was drawn from a normal distribution with a standard deviation equal to that of line-free portions of each spectrum. During this process, we also explored channelization effects by randomly shifting the bin centers by a uniform fraction of a channel width when constructing the model spectrum. These frequency shifts were also drawn from a normal distribution with standard deviation equal to a quarter of the corresponding $\Delta \nu_\mathrm{obs}$ value in Table [3](#tbl:sample). This final step helps to provide more realistic line-width uncertainties in cases where the measured width $\sigma_\mathrm{LOS} \lesssim \Delta\nu_\mathrm{obs}$. Incorporating Hanning smoothing also better accounts for correlated spectral noise, although it cannot explain apparently coherent spectra features over frequency ranges $\gtrsim$3$\Delta \nu_\mathrm{obs}$ (e.g., see the X5 spectrum in Figure [4](#fig:colineabsfit)). Broader uncertainties on $\tau_\mathrm{CO}$ were also determined in this way. We note that bandpass calibration limitations are liable to introduce pattern noise in the peak continuum spectrum over larger frequency ranges (at the $\sim$0.1% level, or $\sim$1$-$2 mJy; see Figure [9](#fig:contabs)). This may create low-level structure in the spectral response over the model fitting region that is not represented in the linear $T_\mathrm{\nu,cont}$ fit. This appears most clearly in the CO(3$-$2) spectrum (see Figure [9](#fig:contabs)). However, we do not attempt to quantify here the bandpass calibration effects on $\tau_0$ and $\tau_\mathrm{CO}$ values and simply refer the reader to Appendix [11.1](#app:broadabs) for additional discussion.

The ratio of centroid frequencies (or weighted-average $\overline{\nu}$ when multiple observations exist) is redshift independent, and the observed ratios are broadly consistent with expectations:

$$\begin{equation*}
    \begin{aligned}
        \frac{\nu_\mathrm{CO(3-2)}}{\overline{\nu}_\mathrm{CO(1-0)}} -3  & = (-8.96\pm 2.67) \times 10^{-5} \\
        \frac{\overline{\nu}_\mathrm{CO(2-1)}}{\overline{\nu}_\mathrm{CO(1-0)}} -2 & = (-4.15\pm 0.58)\times 10^{-5}\,.
    \end{aligned}
\end{equation*}$$

Deviations from the expected zero values beyond the standard error propagation may result from low-S/N CO(2$-$1) detection. We note that including the APP-mode value in Table [2](#tbl:narrowabs) when calculating $\overline{\nu}_\mathrm{CO(2-1)}$ does not contribute appreciably to the measured $\overline{\nu}_\mathrm{CO(2-1)}/\overline{\nu}_\mathrm{CO(1-0)}-2$ offset from zero. As shown in Figure [4](#fig:colineabsfit), the faint CO(2$-$1) absorption and neighboring O$_3$ line would not have allowed for a confident CO detection without support from the CO(1$-$0) transition. For the other ratio, the $\nu_\mathrm{CO(3-2)}$ value appears to be anomalously high. In velocity units, these fits give consistent (intrinsic) line widths of $\sim$3$-$6 km s$^{-1}$ and typical $\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}\sim -75$ to $-$79 km s$^{-1}$, although the CO(3$-$2) feature has a more blueshifted central velocity that is discrepant by $\sim$3$\sigma$ from the weighted-average CO(1$-$0) and CO(2$-$1) centroid values.

For use later when constraining molecular gas properties, we also constructed final weighted-average peak opacities $\overline{\tau}_\mathrm{0,CO(1-0)} = 0.00239\pm 0.00054$ and $\overline{\tau}_\mathrm{0,CO(2-1)} = 0.00390\pm 0.00063$. If ignoring the APP-mode results from the Xb data set, $\overline{\tau}_\mathrm{0,CO(2-1)}$ only changes by $\sim$2%. The integrated opacity $\overline{\tau}_\mathrm{CO(1-0)} = 0.0281 \pm 0.0045$ km s$^{-1}$ is moderately lower than measured for $\tau_\mathrm{CO(3-2)}$ while the latter is formally consistent with $\overline{\tau}_\mathrm{CO(2-1)} = 0.0410 \pm 0.0041$ km s$^{-1}$. We note that these $\tau_\mathrm{CO}$ are an order-of-magnitude lower than those reported by (cite: ray24).

The core continuum source at the center of M87 is very compact, with the brightest component having a radial size of $\sim$25 $\mu$as (cite: event19) that is expected to probe a very narrow line of sight through the CO absorber. At high resolution (cite: acciari09), this very compact core brightness may account for only $\sim$25$-$50% of the integrated flux density that remains unresolved in these ALMA data after extrapolating the flat-spectrum core and synchrotron jet behavior below 3.5 mm (cite: doi13; lu23). As discussed in Appendix [6.1](#app:mfs), the next brightest compact synchrotron source (the N2 clump) lies $<$2 pc in projection from the nucleus with an integrated mm-wavelength core-to-N2 flux density ratio of $\sim$25. On smaller scales at radio wavelengths, the synchrotron core-to-jet flux density ratio approaches $\sim$100 (cite: cheung07; walker18).

The question is whether the continuum emission from the approaching synchrotron jet emission (oriented at a $\mathrm{PA}\sim -65\ensuremath{^\circ}$ from the core) passes through sufficiently distinct lines of sight to probe a possible absorption-line velocity gradient in the CO absorber. We attempted to answer this by refitting the CO(1$-$0) absorption feature from the Xa1 data set across the central beam area ($\overline{\theta}_\mathrm{FWHM} \sim 0.21\ensuremath{''}$ or $\sim$15 pc). Spectra in adjacent spatial pixels were combined together using Voronoi tessellation (cite: cappellari03) prior to refitting to achieve roughly uniform continuum S/N per bin. Figure [4](#fig:colineabsfit) shows the velocity gradient to be no more than 3 km s$^{-1}$ across $\sim$10 pc, with the putative gradient being oriented in a mostly N–S direction. While not unphysical for emission-line clouds in luminous ETGs (cite: utomo15), residual calibration issues erode support for a rotating cloud scenario (for additional details, see Appendix [11.2](#app:broademission)). Individual uncertainties were estimated using the same MC resampling approach. The other CO(1$-$0) continuum cube from the X5 data set had much higher angular resolution but insufficient S/N in binned spectra to measure opacities across the central beam area.

![](m87_alma_narrowco_tex.pdf)

## Temperature and Column Densities

The relative level occupation defines an excitation temperature $T_\mathrm{ex}$ for two different transitions. Given the higher confidence in the lower-$J$ $\tau_\mathrm{CO}$, we first solved column density equations that relate integrated CO(2$-$1) and CO(1$-$0) opacities with a common $T^{21}_\mathrm{ex}$ (cite: godard2010; rose19b) by

$$\begin{equation}
    \frac{\tau_\mathrm{CO(2-1)}}{\tau_\mathrm{CO(1-0)}} \left[\frac{\nu_\mathrm{CO(2-1)}}{\nu_\mathrm{CO(1-0)}}\right]^3 \frac{g_{1}A_{10}}{g_{2}A_{21}} = \frac{1-e^{-h\nu_\mathrm{CO(2-1)}/kT^{21}_\mathrm{ex}}}{e^{h\nu_\mathrm{CO(1-0)}/kT^{21}_\mathrm{ex}}-1} \,.
\end{equation}$$

A similar equation relates a common $T^{32}_\mathrm{ex}$ for adjacent CO(3$-$2) and CO(2$-$1) transitions. Here, $g_u = 2 J_u +1$ is the upper-level degeneracy for that radiative transition and $A_{ul}$ is the corresponding Einstein coefficient for spontaneous decay[^3]. This assumes a single-zone system in local thermodynamic equilibrium (LTE) where adjacent transitions (e.g., $J = 0\rightarrow1$ and $1\rightarrow2$) originate under the same conditions. We have ignored beam filling factors and also considered the impact of the CMB background to be negligible at this redshift and for the measured $T^{21}_\mathrm{ex}$ and $T^{32}_\mathrm{ex}$ values. Individual $\tau_\mathrm{CO}$ have lower S/N, so we employed weighted-average values to recover more confident $T_\mathrm{ex}$.

In Figure [5](#fig:tex_plot), we compare measured opacity ratios with theoretical values assuming the absorbing medium is in LTE with $T^{32}_\mathrm{ex} = T^{21}_\mathrm{ex}$. However, the relatively large depth of the CO(3$-$2) feature and/or low CO(2$-$1) depth as evidenced by $\tau_\mathrm{CO(3-2)}/\overline{\tau}_\mathrm{CO(2-1)} \approx \overline{\tau}_\mathrm{CO(2-1)}/\overline{\tau}_\mathrm{CO(1-0)}$ is not consistent with LTE expectations. This may indicate an elevated $J=2$ population, possibly arising from absorption-line contributions by gas in distinct spatial or energetic regions (cite: rose24). Unfortunately, neither $\tau_\mathrm{CO(3-2)}$ or $\overline{\tau}_\mathrm{CO(2-1)}$ values are as reliable as is $\overline{\tau}_\mathrm{CO(1-0)}$, and we do not attempt any reconciliation in the LTE framework. In Section [4.2.3](#sec:disc_temp), we use radiative transfer modeling to better account for possible deviations from LTE.

To determine a total column density $N_\mathrm{CO}$, we primarily considered CO(1$-$0) absorption and an excitation temperature for the lowest-$J$ transitions:

$$\begin{equation}
    N_\mathrm{CO} = Q_\mathrm{rot} \left(\frac{8 \pi v_{ul}^3}{c^3}\right) \frac{g_0}{g_1} \frac{1}{A_{10}} \frac{1}{1-e^{-h\nu_\mathrm{CO(1-0)}/kT^{21}_\mathrm{ex}}} \tau_{\mathrm{CO(1-0)}} \,.
\end{equation}$$

This relationship assumes detailed balancing and the temperature-dependent $^{12}$CO rotational partition function $Q_\mathrm{rot}$ (cite: Mangum2015). Assuming LTE, the kinetic temperature $T_K = T_\mathrm{ex}$. Here, we used $\overline{\tau}_\mathrm{CO(1-0)}$ for more confident $N_\mathrm{CO}$ determination.

We recovered more reliable error bars in a series of trials by drawing individual $\tau_\mathrm{CO}$ randomly from normal distributions centered on their measured value with standard deviations equal to their 1$\sigma$ uncertainties in Table [2](#tbl:narrowabs). After calculating weighted-average opacities at each iteration, we used the newly-fit $T_\mathrm{ex}$ to find a new $Q_\mathrm{rot}$ and $N_\mathrm{CO}$. After $10^5$ iterations, we used the 15.9 to 84.1 (0.14 to 99.87) percentile levels of the $T^{21}_\mathrm{ex}$ distribution to find a median $T^{21}_\mathrm{ex} = 7.77^{+1.34}_{-1.94}\left(^{+14.88}_{-2.90}\right)$ K and $N_\mathrm{CO}/10^{15}\,\mathrm{cm}\ensuremath{^{-2}}= 1.16^{+0.21}_{-0.28}\left(^{+3.55}_{-0.47}\right)$ with 1$\sigma$ (3$\sigma$) error bars. Calculated separately for the higher-$J$ lines, we find higher median $T^{32}_\mathrm{ex} = 28.6^{+26.7}_{-14.9}$ K with $N_\mathrm{CO} \sim 10^{16}$ cm$^{-2}$ whose high 1$\sigma$ error bars arise from relatively large $\tau_\mathrm{CO(3-2)}$ uncertainty. Coincidentally, (cite: ray24) report similar $T_\mathrm{ex}^{21}$ while their $N_\mathrm{CO}$ is $\sim$5$\times$ lower using the X1b0 data set.

# Discussion

## CO Emission

Based on line profile upper limits in Table [1](#tbl:narrowem), these archival ALMA data do not support any CO emission-line detection from dusty clumps or atomic gas filaments. Integrated line profiles for the larger-scale W1, W2, bar, and loop regions have individual detection thresholds at the $\sim$0.4$-$0.6 Jy km s$^{-1}$ level. For a standard CO(1$-$0)-to-H$_2$ conversion factor $\alpha_\mathrm{CO} = 3.1$ $M_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: Sandstrom2013), this translates to $M_\mathrm{H_2} \lesssim (0.8-1.3)\times 10^6$ $M_\odot$ upper limits. In the nucleus ($R<0.5\ensuremath{''}$), we find a limiting $S_\mathrm{CO(1-0)} \Delta v < 0.109$ Jy km s$^{-1}$ with a 20% lower value for the annulus region. The resulting $M_\mathrm{H_2} < 2.3\times 10^5$ $M_\odot$ is $\sim$20$\times$ lower than any previous upper limit (cite: tan08). Both this $M_\mathrm{H_2}$ limit and the corresponding (deprojected) surface mass density $\overline{\Sigma}_\mathrm{H_2} < 45$ $M_\odot$ pc$^{-2}$ averaged over the atomic CND extent are lower than for many CO-detected molecular CNDs in other massive elliptical galaxies (cite: boizelle17; ruffa19; smith21). Such a tight $M_\mathrm{H_2}$ constraint is in stark contrast to the estimated $\sim$10$^7$ $M_\odot$ within the inner $\sim$200 pc reported by (cite: ray24).

The single-channel ($\Delta v = 20$ km s$^{-1}$) CO line profile excesses in the W1 and bar regions and an integrated excess ($\Delta v = 100$ km s$^{-1}$) in the jet region over clumps A–C *may* hint at CO emission. However, the low estimated S/N $\sim 3$ and a lack of clear compact or diffuse CO emission at the corresponding locations and frequencies disfavor that interpretation. For broad detection, the only possible candidate is the dust filament found $\sim$2$''$ to the southeast of the nucleus, although its integrated line profile only reaches S/N $\sim 4$ in the $0 < \ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}< 320$ km s$^{-1}$ range. Again, a channel-by-channel inspection of this region does not show any potential features above a 4$\times$rms threshold.

Unfortunately, new ALMA 12-m CO imaging would likely not result in CO(1$-$0) detection from either the known dusty regions or the CND. To achieve just a 3$\times$ improvement in noise over the Xa1 results (reaching an rms $\sim 0.225$ mJy beam$^{-1}$ in a 20 km s$^{-1}$ channel), the ALMA `Observing Tool` (cite: immer24) suggests a needed on-source (total) time of 8 hrs (12.5 hrs). Further improvement with SDR $\gtrsim 3000$ in a 20 km s$^{-1}$ channel is likely beyond the current ALMA Band 3 capabilities. Unless the CND has an $M_\mathrm{H_2} \sim (0.75-2)\times 10^5$ $M_\odot$, future ALMA CO line surveys of the M87 nucleus are not likely to detect any molecular gas in emission.

HST imaging of the dense and filament regions adjacent to the nucleus in projection provide some additional constraints on possible CO emission. Assuming close proximity to the M87 midplane, this dust should obscure $\sim$half of the stellar light along those lines of sight (cite: ferrarese96; viaene17; boizelle19). In this scenario, observed fractional deficits in the F475W data (see Figure [1](#fig:hst)) correspond to peak *intrinsic* $A_\mathrm{F475W} = 0.75$ mag and 0.25$-$0.4 mag for the dense and filamentary regions, respectively. Since the M87 dust-to-gas ratio is estimated to be close to MW values (cite: sparks93), an expected $A_V / A_\mathrm{F475W} \sim 0.84$ (cite: cardelli89) and standard dust-to-extinction correlations (cite: draine14) return a peak dust surface mass density $\Sigma_\mathrm{dust} \sim 0.1$ $M_\odot$ pc$^{-2}$ and suggest an average of $\sim$0.05 $M_\odot$ pc$^{-2}$ over the inner portion of the dense cloud region. Taking an intrinsic (deconvolved) radius ($\lesssim$20 pc; see Section [3.1](#sec:narrowem)) for the obscuration as a proxy for the cloud size and a standard dust-to-gas mass of $\sim$0.015 (cite: Sandstrom2013), the expected $\overline{\Sigma}_\mathrm{H_2} \lesssim 3$ $M_\odot$ pc$^{-2}$ and a total $M_\mathrm{H_2} \lesssim 4200$ $M_\odot$ is consistent with ALMA CO non-detection. Assuming the same $\alpha_\mathrm{CO}$ value, the corresponding integrated $S_\mathrm{CO(1-0)}\Delta v$ would be about 75$\times$ lower than the upper limit found for the dense dust aperture.

Cool-core BCGs frequently host rotation-dominated CNDs and/or extended filaments with CO-derived total molecular gas masses $M_\mathrm{H_2} \sim 10^8$ $M_\odot$ (cite: Olivares2019; Baek2022), and CO surveys of galaxies like M87 have found a positive correlation between integrated H$\alpha$ luminosity $L_\mathrm{H\alpha}$ and total $M_\mathrm{H_2}$ (cite: edge01; salome03; pulido18). Among these massive elliptical galaxies, M87 has a low but confident[^4] $L_\mathrm{H\alpha}\sim (0.8-1.1)\times 10^{40}$ erg s$^{-1}$, and the $L_\mathrm{H\alpha} - M_\mathrm{H_2}$ correlation suggests there should be a global $M_\mathrm{H_2} \sim (0.8-9)\times 10^8$ $M_\odot$. Previous low-$J$ CO observations of M87 found a global $M_\mathrm{H_2}<10^8$ $M_\odot$ (cite: jaffe87). Adding together all the emission-line search regions in Figure [1](#fig:hst), we place a more strict $M_\mathrm{H_2} \lesssim 3\times 10^6$ $M_\odot$. When using a circular aperture with 2 kpc radius, we find a similar $<$4$\times$10$^6$ $M_\odot$ global upper limit. This ALMA CO search suggests that M87 is either a clear outlier in the $L_\mathrm{H\alpha} - M_\mathrm{H_2}$ correlation for cool-core galaxies or that there is much wider scatter about this correlation.

## CO Absorption

Here, we discuss the properties of extragalactic CO absorption seen against the M87 nucleus. Based on both CO opacities and kinematics, this CO absorption appears more consistent with a narrow filament instead of a gravitationally bound cloud. We place the observed kinematics, density estimates, and temperatures in context with circumnuclear gas seen both in absorption and emission in other luminous ETGs.

![](m87_coabs_compkinematics.pdf)

### Kinematics

In a few radio galaxies, CO absorption signatures appear to arise from chance alignment of dense CND molecular clouds and the bright nucleus, especially for cases where molecular CNDs are detected with higher inclination angles (cite: boizelle17; ruffa19; rose19b; rose24). In these cases, absorption-line centroids tend to be close to $v_\mathrm{sys}$ (within $\pm$50 km s$^{-1}$) as clouds oriented along the disk minor axis have little if any LOS motion. As is shown in Figure [6](#fig:coabs_comp), the weighted-average $\overline{v}_\mathrm{LOS} - \ensuremath{v_\mathrm{sys}}= -77.21 \pm 0.44$ km s$^{-1}$ for the M87 CO(1$-$0) and CO(2$-$1)transitions are therefore not consistent with clouds in low-ellipticity orbits, although the observed $\overline{\sigma}_\mathrm{LOS} = 4.65\pm0.47$ km s$^{-1}$ is typical of disk-like clouds. The CO emission-line search provided no convincing support for a molecular phase of the atomic gas disk (cite: osorno23), making disk-like obscuration implausible. Compared to clouds not connected with a clear molecular-gas CND, the narrow CO features in M87 reside at the extreme edge of detected features. It may be that such blueshifted clouds with $\tau_\mathrm{CO}\ll 1$ km s$^{-1}$ are more common generally but only detected for M87 at present due to the uncommon ALMA imaging depth and large number of data sets to reproduce faint absorption.

On kpc scales, cool-core BCGs often host multiple molecular gas clumps and filaments whose gas velocities range between about $\pm$200 km s$^{-1}$ from the BCG rest frame. Outside of strongly rotationally-broadened regions like the nucleus, CO emission FWHM are typically 30$-$60 km s$^{-1}$. A good example is Abell 1644-S, whose arching CO emission spans $\sim$15 kpc with speeds shifting from about $-$140 to +30 km s$^{-1}$ relative to its $v_\mathrm{sys}$, with larger-scale flows possibly connecting down to a multi-phase CND. In the most isolated regions, moderate-resolution CO imaging shows narrow emission-line FWHM $\sim 20$ km s$^{-1}$ with minimal velocity gradients (cite: Baek2022), although beam smearing of adjacent clouds likely still appreciably broadens the line intrinsic FWHM (cite: Olivares2019; ganguly23). In NGC 1275, multiple streamers connect CO emission to the CND in a complex fashion (cite: oosterloo24). In cool-core BCGs, such patchy and filamentary multi-phase gas structures are typical of chaotic cooling of the galactic and circumgalactic medium that greatly increases $\dot{M}_\mathrm{BH}/\dot{M}_\mathrm{Edd}$ in episodic accretion (cite: babyk19; gaspari20; pasini21). The case of Abell 1644-S is also similar to the atomic gas filaments in M87 (cite: osorno23) as the blueshifted clouds connecting to the CND from behind appear to continue in front of the nucleus to be seen in blueshifted absorption (cite: Baek2022; rose24).

For M87 specifically, (cite: simionescu18) used ALMA imaging to map out CO emission from the dense SE molecular cloud that is embedded within a broader filamentary atomic gas complex $\sim$40$''$ from the nucleus with projected $\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}\sim -129$ km s$^{-1}$. The SE cloud shows a modest gradient of at least a couple $\times$10 km s$^{-1}$ across the brightest emission-line clump that extends over a projected $\sim$150 pc. At an angular resolution of $\theta_\mathrm{FWHM}\sim 1.4\ensuremath{''} \times 0.7\ensuremath{''}$ (average $\sim$85 pc), the gas cloud with $S_\mathrm{CO(2-1)} \Delta v = 0.56\pm0.06$ Jy km s$^{-1}$ and $\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}\sim -129$ km s$^{-1}$ is resolved into a spherical clump with a diameter of $\sim$100 pc and $\sigma_\mathrm{LOS} \sim 30$ km s$^{-1}$ together with a smaller, filamentary component with a narrower line width. The latter better matches the observed line widths and low velocity gradient from the CO absorption shown in Figure [4](#fig:colineabsfit). Based on the relative distribution of ionized gas and X-ray emission, those authors argue the SE cloud is falling into M87 from behind, with the observed molecular gas surviving passage through the moderately cool-core X-ray gas in this part of the Virgo cluster (cite: shibata01; forman07) only to be destroyed at closer radii either by shocks or by relativistic particles associated with the radio lobes.

The primary UV/optical absorption lines that are connected to a central outflow are more blueshifted ($\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}\sim -131\pm19$ km s$^{-1}$) and much broader (cite: tsvetanov99a; sabra03) than is the CO absorption[^5]. The velocity centroids of narrow absorption-line gas in AGN winds or outflows may vary by a few km s$^{-1}$ over several-year timescales (cite: misawa14; grier16; misawa19; rose19a; dehghanian24). If entrained in the same gaseous outflow, the atomic and molecular absorption-line properties for M87 should be more similar (cite: margulis89). Additionally, two faint optical absorption-line systems were reported at $\ensuremath{v_\mathrm{LOS}}\sim 980$ and 1300 km s$^{-1}$ (cite: carter92; carter97) without any coincident CO absorption.

### Column Densities

The estimated $N_\mathrm{CO} \sim 10^{15}$ cm$^{-2}$ is below the detection threshold for many extragalactic ALMA programs, although it is reached by certain Galactic line surveys (cite: liszt98). A standard CO/H$_2$ abundance ratio of $3.2\times 10^{-4}$ (cite: sofia04; bolatto2013) would result in a very low $N_\mathrm{H_2} \sim 1.5\times 10^{18}$ cm$^{-2}$. That conversion factor is typically applied to systems with peak $N_\mathrm{H_2} \gtrsim 10^{21}$ cm$^{-2}$ while such a low $N_\mathrm{CO}$ better comports with more diffuse Galactic lines of sight that have CO/H$_2$ abundances of $\sim$2$\times$10$^{-6}$ (cite: liszt19) to $\sim$8$\times$10$^{-7}$ (cite: pineda10) due to easier CO destruction. These ratios result in our preferred range $N_\mathrm{H_2}/10^{20}\,\mathrm{cm\ensuremath{^{-2}}} = 0.92^{+0.68}_{-0.36} - 2.3^{+1.7}_{-0.9}$ or $\Sigma_\mathrm{H_2} \sim 0.6-1.4$ $M_\odot$ pc$^{-2}$ that matches an estimated total $N_\mathrm{H} \sim (2-5)\times 10^{20}$ cm$^{-2}$ towards the M87 nucleus from X-ray spectroscopy (cite: wilson02; dimatteo03).

Simulations suggest CO is created (or persists in an equilibrium state) for gas with $n_\mathrm{H_2} \gtrsim 1000$ cm$^{-3}$ where dust, H$_2$, and line self-shielding prevents CO dissociation (cite: safranek17). The low $N_\mathrm{H_2}$ and $A_V \sim 0.04-0.10$ mag estimate (cite: guver09) suggests more limited shielding against interstellar radiation (cite: gnedin14). Similar to the SE complex, the CO-absorbing gas may be physically located far from the nucleus and be evolving (further) towards atomic gas dominance. The low molecular gas fraction inferred from this $A_V$ range (cite: snow06) would make C II and not C I or CO the dominant reservoir of gas-phase carbon (cite: gerin24). Far-IR spectroscopy centered about the M87 nucleus does reveal faint \[C II\] 158 $\mu$m and \[O I\] 63 $\mu$m fine-structure lines (cite: brauher08), but the $\sim$1.7$'$ aperture diameter (and possible 1$'$ offset from the nucleus) prevents any clear connection to any specific gaseous structure. Adding neutral atomic gas would only give an estimated $N(\mathrm{H}) = 2N(\mathrm{H}_2) \times (1-f_\mathrm{H_2})/f_\mathrm{H_2} \sim (2-4)\times 10^{21}$ cm$^{-2}$ $\sim15-30$ $M_\odot$ pc$^{-2}$.

![](m87_alma_radex_sim.pdf)

### Temperatures and Densities

The measured $T^{21}_\mathrm{ex} \sim 8\pm2$ K is similar to excitation temperatures found for diffuse Galactic (cite: liszt04; roman10) and extragalactic molecular gas. Some massive galaxies have diffuse obscurers with $T_\mathrm{ex} \sim 20-40$ K (cite: israel92; lim17; rose19b; rose19a) while outflow CO line ratios or warmer molecular tracers suggest $T_\mathrm{ex} \sim 30-100$ K and $T_K \sim 400$ K, respectively (cite: dasyra16; cashman21; ruffa22). Because of the intense interstellar radiation field and cosmic ray environment, the CO absorber is likely to be out of LTE. Indeed, both the measured $\tau_\mathrm{CO(3-2)}$ and inferred $T^{32}_\mathrm{ex} \sim 30\pm 20$ K are elevated over LTE predictions from lower-$J$ CO measurements.

To probe more realistic cloud conditions, we employed the one-dimensional non-LTE radiative transfer code `radex` (cite: ferland98; van07) to reproduce the observed peak opacities $\overline{\tau}_\mathrm{0,CO(1-0)}$, $\overline{\tau}_\mathrm{0,CO(2-1)}$, and $\tau_\mathrm{0,CO(3-2)}$. `radex` models excitation of molecular lines in a uniform, isothermal, and homogeneous medium, employing the large velocity gradient approximation to compute photon escape. We assumed the gas is organized in a uniform sphere, although different geometries and escape probabilities give similar results for low-$J$ CO transitions. Radiative transfer modeling typically relies on multiple molecular line tracers and/or isotopologues to probe dense gas conditions. In this case, however, the very low opacity $\tau_\mathrm{0,CO} \ll 1$ simplifies the analysis and allows $^{12}$CO to trace the entire cloud. To be consistent with observations, we adopted $N_\mathrm{CO} = 10^{15}$ cm$^{-2}$ from LTE measurements and fixed the CO line FWHM to 10 km s$^{-1}$. The level of gas turbulence is not known, but we assumed a cold gas distribution and tested $T_K = 10$ K and 30 K in turn. During `radex` modeling, we explored $n_\mathrm{H_2} = 10^2-10^5$ cm$^{-3}$ and background temperature $T_\mathrm{bg} = 30-300$ K.

In Figure [5](#fig:tex_plot), we compare measured and `radex` model $\tau_0$ values and present $\chi^2$ contours over a grid of $n_\mathrm{H_2}$ and $T_\mathrm{bg}$ points. These results show strong preference for a very cold distribution ($T_K = 10$ K) with best-fitting $n_\mathrm{H_2} \sim 5100$ cm$^{-3}$ and $T_\mathrm{bg} \sim 62$ K that is much higher than the $\sim$23 K suggested by the mean interstellar radiation field (cite: baes10), providing additional support for a more nuclear location for the CO absorption. While the 1$\sigma$ contours do not close for reasonable $n_\mathrm{H_2}$ and $T_\mathrm{bg}$, they provide $n_\mathrm{H_2} > 1100$ cm$^{-3}$ and $T_\mathrm{bg} > 45$ K lower limits. A warmer $T_K = 30$ K gives best-fit $n_\mathrm{H_2} \approx 3.5\times 10^4$ cm$^{-3}$ and $T_\mathrm{bg} \sim 71$ K with 7$\times$ higher $\chi^2$; still, lower-bound parameter limits are similar to the $T_K = 10$ K case. Based on these `radex` bounds, the current CO absorption-line data appear more consistent with central $n_\mathrm{H_2} > 1000$ cm$^{-3}$ for a thin filament ($r_\mathrm{c} < 0.1$ pc) instead of a more diffuse filament or spherical cloud.

Additional higher-frequency ALMA 12-m imaging may break the degeneracy between $n_\mathrm{H_2}$ and $T_\mathrm{bg}$ and help to better constrain $T_K$ (cite: vankempen16). We tested two cases: one that improved the existing $\tau_\mathrm{0,CO(3-2)}$ measurement and the other that obtained new Band 8 imaging to detect $\tau_\mathrm{0,CO(4-3)}$. In both cases, we assumed that the new peak opacity reached the same fractional precision as the Xa1 $\tau_\mathrm{0,CO(1-0)}$ measurement (S/N $\sim 3.4$). In Figure [7](#fig:radex_sim_plot), these `radex` results show closed 1$\sigma$ confidence intervals in both cases, although adding in the CO(4$-$3) measurement to the values in Table [2](#tbl:narrowabs) provides much tighter constraints. In the best case, $n_\mathrm{H_2}$ and $T_\mathrm{bg}$ could be known to within $\sim$0.3 dex and 10$-$20 K, respectively. Using the `OT`, we estimate these new $\tau_0$ measurements would require a minimum on-source (total) time of 56 min (112 min) for the Band 7 imaging while for Band 8 the require time would be up to 6.25 hrs (12.1 hrs).

### Origin of the CO Absorption

Now, we employ the measured CO line kinematics, the estimated column densities, and non-LTE modeling results to explore both gravitationally bound, spherical cloud and filament origins for the CO absorption features. Based on an isolated absorption line and narrow widths, we discount any interpretation of spatially diffuse molecular gas. We appeal to both Galactic and extragalactic observations for comparison but do not find a fully coherent explanation for the measured $\ensuremath{\sigma_\mathrm{LOS}}$ and inferred $T_K$, $N_\mathrm{H_2}$ and $n_\mathrm{H_2}$ values.

A cloud is often considered virialized when parameter $\alpha_\mathrm{vir} \equiv 5\sigma^2/\pi GR\Sigma \approx 1$, although real clouds in luminous galaxy centers are centered on $\alpha_\mathrm{vir} \approx 1.7$ (cite: choi24). Correlations between cloud size $R$ and emission-line width for gravitationally-bound clouds give a range of justifiable results. From the fitted absorption-line $\overline{\sigma}_\mathrm{LOS}$, Galactic or LMC studies (cite: solomon87; wong22) are consistent with a cloud radius $r_\mathrm{cloud} \sim 20-40$ pc while rescaled relations in large-scale CNDs in luminous ETGs suggest $r_\mathrm{cloud} \sim 10-20$ pc (cite: utomo15; rosolowsky21). From turbulent clouds in the Galactic center (using dense-gas tracers), the observed $\sigma_\mathrm{LOS}$ cloud be matched to an $r_\mathrm{cloud} \sim 2-4$ pc (cite: shetty12). We note that absorption probes only a thin line through the cloud, so a CO emission-line width would likely be broader. Assuming $\alpha_\mathrm{vir} \approx 1.7$, the $r_\mathrm{cloud} \sim 4-30$ pc range and the measured $\overline{\sigma}_\mathrm{LOS}$ would require an implausibly high gas surface mass density $\Sigma_\mathrm{H_2} \sim 400-7000$ $M_\odot$ pc$^{-2}$ considering the CO emission-line non-detection discussed in Section [4.1](#sec:disc_em) and the absorption-line $\Sigma_\mathrm{H_2} \sim 1$ $M_\odot$ pc$^{-2}$ estimate. If the absorbing cloud is well centered on the AGN and uniformly distributed, the $N_\mathrm{H_2}$ would correspond to $\overline{n}_\mathrm{H_2} \sim 0.5-9$ cm$^{-3}$ with a total $M_\mathrm{H_2} \sim 50-7000$ $M_\odot$. For comparison, the more compact region of the SE cloud has an estimated $\overline{n}_\mathrm{H_2} \sim 50$ cm$^{-3}$. Adopting typical cloud radial density profiles and small core sizes (cite: csengeri17; andre22) relative to the $r_\mathrm{cloud}$ range above, the expected *central* densities of 100$-$1800 cm$^{-3}$ would be lower than typical dense gas cores as well as the CO(1$-$0) critical density (cite: scoville12).

More likely, this CO absorption originates in a foreground filament. Simulations suggest that accreting clouds like those composing the SE complex or the dense dusty clump are preferentially drawn into narrow filaments by magnetic fields that thread massive galaxies (cite: fournier24). The $N_\mathrm{H_2}$ range is much lower than typical Galactic filament peak values (cite: arzoumanian11; arzoumanian18; konyves20) but better matches properties of extragalactic filamentary structures (cite: sancisi08; blok14). In Galactic systems, resolved filamentary structures seen in emission have typical line widths $\lesssim$1 km s$^{-1}$ and narrow core widths $r_\mathrm{c} \lesssim 0.1$ pc (cite: arzoumanian11; koch15; panopoulou16; rivera16; indebetouw20). For the measured $\overline{\sigma}_\mathrm{LOS}$, filament size-emission-line width relations would be consistent with an effective $r_\mathrm{c} \sim 0.5$ pc or more, which is at the very upper limit for Galactic filaments. However, the MW filament environment is very different than for the M87 nucleus, and the latter has ionized gas filament intrinsic widths of $\sim$200$-$300 pc (cite: sparks93; sparks09; forman07). We note that within and around radio galaxies, even more diffuse filaments reaching $\sim$kpc widths have been observed (cite: yusef22).

Calculating $\overline{n}_\mathrm{H_2}$ through the center of a Plummer filament model with matching $N_\mathrm{H_2}$ (cite: rivera16), the peak H$_2$ densities should reach *at least* 1000$-$2500 cm$^{-3}$, which is consistent with simulations of filament formation (cite: hennebelle13). If $r_\mathrm{c} \sim 0.1$ pc, the corresponding linear mass $M_\mathrm{H_2}/\ell \sim 0.5-1$ $M_\odot$ pc$^{-1}$ would be at the very bottom of the linear mass distribution for Galactic systems associated with star formation (cite: sancisi08), although it does match more diffuse extragalactic filaments associated with accretion (cite: blok14). In any case, the M87 absorber would be in a very distinct region of the $\sigma_\mathrm{LOS}$ vs. $M_\mathrm{H_2}/\ell$ or $N_\mathrm{H_2}$ parameter space. The observed $\overline{\sigma}_\mathrm{LOS}$ is an order-of-magnitude higher than line widths for Galactic systems while having two orders of magnitude lower $N_\mathrm{H_2}$ (cite: arzoumanian13; chen24). If positioned slightly off-center from the M87 nucleus, such a filament would allow for higher peak $n_\mathrm{H_2}$ and $M_\mathrm{H_2}/\ell$ values.

The estimated $\Sigma_\mathrm{H_2} \sim 1$ $M_\odot$ pc$^{-2}$ is far below the threshold needed to reconcile the measured $\overline{\sigma}_\mathrm{LOS}$ with a virialized, compact filament. Instead, interactions with the hot interstellar medium or an envelope of warm, partially ionized gas may provide sufficient pressure to confine the CO absorber. In the first case for an isothermal X-ray-emitting distribution, the upper-bound electron density $n_e \sim 0.5$ cm$^{-3}$ in the region of large-scale filaments (cite: olivares25) and temperature $kT_e \sim 1.5-2$ keV (cite: sparks04; forman07) give rise to a pressure $P \gtrsim (1-2)\times 10^{-9}$ dynes cm$^{-2}$. Pressure from the X-ray emission of filament regions is a only factor of 2$-$3 lower (cite: olivares25). In the second case, warm ionized gas with $T_e \sim 10^4$ K could provide similar pressure if $n_e \sim 1600$ cm$^{-3}$ ((cite: ford79); see also (cite: heckman89)). For comparison, the cloud or filament scenarios with their corresponding $\overline{n}_\mathrm{H_2}$ and a $T_K$ reaching as high as $\sim$25$-$50 K results in internal $P \ll 10^{-10}$ dynes cm$^{-2}$, leading to pressure confinement of the diffuse molecular gas. Without more extensive line measurements and full radiative transfer modeling, it is not clear how a thin filament embedded in such an extreme environment could retain a low $T_K \sim 10$ K.

# Conclusion

We conducted a CO line search of M87 using archival ALMA 12-m imaging, focusing on the CND and the dusty clouds and filaments seen in optical imaging in the inner $\sim$kpc. Despite the deep ALMA imaging and multiple spws containing redshifted CO transitions, we did not clearly identify any CO emission. Over the atomic gas CND, the upper limit $M_\mathrm{H_2} < 2.3\times 10^5$ $M_\odot$ is $\sim$20$\times$ lower than achieved in previous CO surveys. In other regions containing atomic gas filaments and dust, we placed upper limits of $M_\mathrm{H_2} \lesssim 10^5 - 10^6$ $M_\odot$ with a global $<$4$\times$10$^6$ $M_\odot$ limit for a circular aperture with $R<2$ kpc. In narrow gaseous regions, potential CO emission-line signatures in extracted line profiles do not arise from compact sources.

During this search, we confidently detected molecular gas in absorption against the bright nucleus in the CO(1$-$0), CO(2$-$1), and CO(3$-$2) transitions. The absorber has very low opacity with average peak $\overline{\tau}_\mathrm{0,CO(1-0)} = 0.00239 \pm 0.00054$ and integrated $\overline{\tau}_\mathrm{CO(1-0)} = 0.0281 \pm 0.0045$ km s$^{-1}$. Measured opacities are slightly higher for the higher-$J$ absorption lines. Line fitting showed a consistently narrow, slightly blueshifted feature with average $\overline{v}_\mathrm{LOS} - \ensuremath{v_\mathrm{sys}}\sim -77.2\pm 0.4$ km s$^{-1}$ and $\overline{\sigma}_\mathrm{LOS} \sim 4.7\pm 0.5$ km s$^{-1}$. From multiple low-S/N CO absorption lines we calculated column densities $N_\mathrm{CO} = \left(1.16^{+0.21}_{-0.28}\right) \times 10^{15}$ cm$^{-2}$ and $N_\mathrm{H_2}/10^{20}\,\mathrm{cm}\ensuremath{^{-2}}= 0.92^{+0.68}_{-0.36} - 2.3^{+1.7}_{-0.9}$ (1$\sigma$ uncertainties) assuming the gas is in a diffuse molecular phase. These molecular absorption features appear inconsistent with blueshifted atomic gas absorption detected in UV/optical spectroscopy at a relative speed of about $-$130 km s$^{-1}$ with line FWHM $\lesssim 300$ km s$^{-1}$, and we disfavor interpreting this CO absorber as arising from molecular gas entrained in an outflow.

Instead, the CO absorption-line properties are more consistent with a filament in a chance alignment with the AGN core, like those seen close in projection to the nucleus. Based on opacity measurements, LTE relations suggest the molecular gas is cold with excitation temperatures $T^{21}_\mathrm{ex} = 7.77^{+1.34}_{-1.94}$ K (1$\sigma$) and $T^{32}_\mathrm{ex} \sim 30$ K, hinting at a $J=2$ population that is elevated over LTE predictions. Non-LTE radiative transfer modeling finds much better agreement with the observed $\tau_0$ values, and `radex` prefers a low kinematic temperature $T_K \sim 10$ K and more dense $n_\mathrm{H_2} \sim 5000$ cm$^{-3}$ that is not consistent with a spherical, gravitationally bound cloud for the measured $\overline{\sigma}_\mathrm{LOS}$. The surrounding background radiation field with best-fit $T_\mathrm{bg} \sim 60$ K is hotter than expected from the mean ISRF, suggesting the CO absorber lies close to the AGN. This (uniform) $n_\mathrm{H_2}$ estimate better matches expectations for a thin, pressure-confined filament, perhaps viewed slightly offset from the compact core location.

We thank the anonymous reviewer for helpful suggestions. We also thank Aaron Barth, Andrew Baker, Jeremy Darling, and Luis Ho for advice and encouragement. We are grateful for advice from Ivan Marti-Vidal, Ciriaco Goddi, and Hiroshi Nagai, together with the ALMA NAASC, in dealing with APP-mode ALMA data sets and bandpass calibration limitations.

Partial support for this work was provided by the NSF through award SOSPADA-003 from the NRAO. XL, NL, BJD, and JD thank the Brigham Young University College of Computational, Mathematical, and Physical Sciences and the Department of Physics and Astronomy for additional research funding.

This research is based, in part, on observations made with the NASA/ESA Hubble Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-26555. These observations are associated with programs GO-12271, GO-13731, and GO-14256. This paper makes use of the following ALMA data in ADS/JAO.ALMA# codes: 2011.0.00001.CAL, 2012.1.00661.S, 2013.1.00073.S, 2013.1.01022.S, 2015.1.00030.S, 2015.1.01170.S, 2015.1.01352.S, 2016.1.00021.S, 2016.1.01154.V, 2017.1.00608.S, 2017.1.00841.V, 2017.1.00842.V, 2019.1.00807.S, and 2021.1.01398.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

HST (ACS,WFC3), ALMA, ACA

# Software

`CASA` (cite: mcmullin07), `GALFIT` (cite: peng02), `radex` (cite: van07), ALMA `OT` (cite: immer24), `PlotDigitizer` (cite: plotdig)

+:-----------:+:------------:+-------------------:+-------------------------:+:-------------:+:-----------------------------------------------:+:-----------:+:-----------:+:------------:+:-----------------:+:-----------:+:-----------:+
| Obs.        | Member       | $\nu_\mathrm{obs}$ | $\Delta\nu_\mathrm{obs}$ | Baselines     | $\theta_\mathrm{maj}\times\theta_\mathrm{min}$  | MRS         | Time        | Peak $S_\nu$ | MFS rms           | PWV         | Pol.        |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| Date        | OUS          | (GHz)              | (MHz)                    | (km)          | $\theta_\mathrm{PA}$                            | (arcsec)    | (hrs)       | (Jy)         | (mJy beam$^{-1}$) | \(mm\)      |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| \(1\)       | \(2\)        | \(3\)              | \(4\)                    | \(5\)         | \(6\)                                           | \(7\)       | \(8\)       | \(9\)        | \(10\)            | \(11\)      | \(12\)      |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| **2012.1.00661.S** (PI: Vlahakis)                                                                                                                                                                                                       |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 99.90$-$101.89     | 15.63                    | 0.015$-$0.423 |                                                 | 12.5        | 1.71        | 2.10         | 1.81              | 1.41        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2014        | A002/X6444ba | 101.78$-$103.76    | 15.63                    |               | $2.03\ensuremath{''}\times1.42\ensuremath{''}$  |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 7 Mar       | /X1b0        | 111.92$-$113.91    | 15.63                    |               | $60.2^\circ$                                    |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 113.85$-$115.72    | 0.49                     |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 331.50$-$333.48    | 15.63                    | 0.015$-$0.347 |                                                 | 6.04        | 1.89        | 1.01         | 0.104             | 0.97        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2014        | A002/X6444ba | 333.30$-$335.29    | 15.63                    |               | $1.16\ensuremath{''}\times0.60\ensuremath{''}$  |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 28 Jan      | /X1b4        | 343.41$-$345.28    | 9.77                     |               | $-$83.7$^\circ$                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 345.30$-$347.29    | 15.63                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 213.00$-$214.99    | 15.63                    | 0.021$-$0.784 |                                                 | 4.04        | 0.25        | 1.75         | 1.10              | 0.69        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2015        | A001/X12f    | 215.00$-$216.99    | 15.63                    |               | $0.54\ensuremath{''}\times0.44\ensuremath{''}$  |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 14 Jun      | /X20f        | 228.63$-$230.50    | 0.49                     |               | $-$47.8$^\circ$                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 230.57$-$232.56    | 15.63                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 213.00$-$214.99    | 15.63                    | 0.043$-$1.574 |                                                 | 1.88        | 0.50        | 0.93         | 1.99              | 0.74        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2015        | A001/X12f    | 215.00$-$216.99    | 15.63                    |               | $0.27\ensuremath{''}\times0.22\ensuremath{''}$  |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 16 Aug      | /X20d        | 228.63$-$230.50    | 0.49                     |               | 14.3$^\circ$                                    |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 230.57$-$232.56    | 15.63                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 89.51$-$91.48      | 31.25                    | 0.041$-$2.070 |                                                 | 23.8        | 3.32        | 2.47         | 0.27              | 1.56        |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             +-------------+
| 2015        | A001/X13a    | 91.45$-$93.42      | 31.25                    |               | $0.46\ensuremath{''}\times0.38\ensuremath{''}$  |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             +-------------+
| 19 Sep      | /Xbe         | 101.51$-$103.48    | 31.25                    |               | 30.0$^\circ$                                    |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 103.51$-$105.48    | 31.25                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 99.88$-$101.86     | 15.63                    | 0.085$-$16.20 |                                                 | 0.97        | 0.66        | 1.96         | 0.51              | 0.96        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2015        | A001/X2d8    | 101.87$-$103.86    | 15.63                    |               | $0.10\ensuremath{''}\times0.046\ensuremath{''}$ |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 8 Nov       | /X5          | 112.28$-$114.16    | 0.98                     |               | $-$56.5$^\circ$                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 113.85$-$115.72    | 0.98                     |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 89.50$-$91.47      | 31.25                    | 0.085$-$16.20 |                                                 | 0.88        | 2.29        | 1.94         | 0.34              | 1.34        |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             +-------------+
| 2015        | A001/X2df    | 91.44$-$93.41      | 31.25                    |               | $0.07\ensuremath{''}\times0.05\ensuremath{''}$  |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             +-------------+
| 11 Nov      | /X135        | 101.50$-$103.47    | 31.25                    |               | 34.8$^\circ$                                    |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 103.50$-$105.47    | 31.25                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 89.50$-$91.48      | 15.63                    | 0.253$-$16.20 |                                                 | 0.90        | 0.034       | 1.75         | 0.69              | 0.97        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2015        | A001/X2d6    | 91.43$-$93.42      | 15.63                    |               | $0.06\ensuremath{''}\times0.05\ensuremath{''}$  |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 27 Oct      | /X2ba        | 101.50$-$103.48    | 15.63                    |               | 39.3$^\circ$                                    |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 103.50$-$105.48    | 15.63                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 136.99$-$138.98    | 15.63                    | 0.068$-$15.24 |                                                 | 0.72        | 0.36        | 1.72         | 0.35              | 1.81        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2015        | A001/X2d6    | 138.93$-$140.91    | 15.63                    |               | $0.06\ensuremath{''}\times0.05\ensuremath{''}$  |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 31 Oct      | /X2be        | 148.99$-$150.98    | 15.63                    |               | $-$37.2$^\circ$                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 150.99$-$152.98    | 15.63                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 222.99$-$224.98    | 15.63                    | 0.068$-$15.24 |                                                 | 1.34        | 0.22        | 1.25         | 0.47              | 1.24        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 2015        | A001/X2d6    | 224.99$-$226.98    | 15.63                    |               | $0.03\ensuremath{''}\times0.03\ensuremath{''}$  |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
| 31 Oct      | /X2c2        | 238.98$-$240.97    | 15.63                    |               | $-$35.1$^\circ$                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +-------------------------------------------------+             |             |              |                   |             |             |
|             |              | 240.98$-$242.97    | 15.63                    |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                 |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+-------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+

: M87 ALMA 12-m Observations and Imaging Properties

Table notes: Properties of ALMA 12-m interferometric and phased-array (APP-mode; .V) data sets that were centered on the M87 nucleus, with the project code and Principle Investigator listed above each synopsis. Cols. (1) and (2) give the UT observation date for each member OUS, respectively, while cols. (3) and (4) give the frequency coverage of each spectral window (spw) along with the associated channel binning. For FDM spws, online Hanning smoothing decreases the effective spectral resolution by a factor of up to two. Unprojected baseline ranges in col. (5) give rise to the corresponding synthesized beam parameters from the final MFS image in col. (6) and the maximum recoverable scale (MRS; adopted from the ALMA Science Archive) in col. (7). Col. (8) reports the on-source integration times, including latencies. Cols. (9) and (10) give the peak continuum flux density and rms of the MFS image at the average frequency for the four spws after applying self-calibration loops, if possible. Col. (11) gives the average precipitable water vapor (PWV; adopted from the ALMA Science Archive) over that time interval. Col. (12) reports the dual (XX YY) or cross-polarization (XY YX) setup.

+:-----------:+:------------:+-------------------:+-------------------------:+:-------------:+:----------------------------------------------:+:-----------:+:-----------:+:------------:+:-----------------:+:-----------:+:-----------:+
| Obs.        | Member       | $\nu_\mathrm{obs}$ | $\Delta\nu_\mathrm{obs}$ | Baselines     | $\theta_\mathrm{maj}\times\theta_\mathrm{min}$ | MRS         | Time        | Peak $S_\nu$ | MFS rms           | PWV         | Pol.        |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| Date        | OUS          | (GHz)              | (MHz)                    | (km)          | $\theta_\mathrm{PA}$                           | (arcsec)    | (hrs)       | (Jy)         | (mJy beam$^{-1}$) | \(mm\)      |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| \(1\)       | \(2\)        | \(3\)              | \(4\)                    | \(5\)         | \(6\)                                          | \(7\)       | \(8\)       | \(9\)        | \(10\)            | \(11\)      | \(12\)      |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| **2016.1.00021.S** (PI: Vlahakis)                                                                                                                                                                                                      |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 112.00$-$113.99    | 15.63                    | 0.021$-$3.64  |                                                | 3.16        | 1.59        | 1.73         | 0.37              | 0.57        | XX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             |             |
| 2017        | A001/X899    | 112.62$-$114.49    | 0.98                     |               | $0.22\ensuremath{''}\times0.21\ensuremath{''}$ |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             |             |
| 15 Aug      | /Xa1         | 113.85$-$115.72    | 0.98                     |               | $-$64.8$^\circ$                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             |             |
|             |              | 114.04$-$115.91    | 0.98                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 212.17$-$214.04    | 7.81                     | 0.015$-$0.375 |                                                | 12.87       | 1.22        | 1.18         | 1.02              | 0.81        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2017        | A001/X11a7   | 214.17$-$216.04    | 7.81                     |               | $2.10\ensuremath{''}\times0.98\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 5 Apr       | /X3a         | 226.17$-$228.04    | 7.81                     |               | $-$82.0$^\circ$                                |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 228.17$-$230.04    | 7.81                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 212.17$-$214.04    | 7.81                     | 0.015$-$0.279 |                                                | 9.95        | 0.89        | 1.14         | 0.54              | 0.69        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2017        | A001/X11a7   | 214.17$-$216.04    | 7.81                     |               | $2.17\ensuremath{''}\times1.50\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 6 Apr       | /X3c         | 226.17$-$228.04    | 7.81                     |               | $-$76.0$^\circ$                                |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 228.17$-$230.04    | 7.81                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 212.17$-$214.04    | 7.81                     | 0.015$-$0.161 |                                                | 12.90       | 1.69        | 1.32         | 1.14              | 1.11        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2017        | A002/Xbee37d | 214.17$-$216.04    | 7.81                     |               | $1.18\ensuremath{''}\times0.80\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 11 Apr      | /Xb          | 226.17$-$228.04    | 7.81                     |               | 70.5$^\circ$                                   |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 228.17$-$230.04    | 7.81                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 211.51$-$213.48    | 31.25                    | 0.015$-$1.398 |                                                | 3.70        | 0.58        | 0.93         | 1.68              | 0.77        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2018        | A001/X129e   | 213.51$-$215.48    | 31.25                    |               | $0.41\ensuremath{''}\times0.26\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 25 Sep      | /X1d         | 227.51$-$229.48    | 31.25                    |               | $-$53.1$^\circ$                                |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 229.51$-$231.48    | 31.25                    |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 212.17$-$214.04    | 7.81                     | 0.015$-$0.418 |                                                | 7.66        | 1.78        | 0.709        | 2.95              | 2.06        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2018        | A001/X12d1   | 214.17$-$216.04    | 7.81                     |               | $0.89\ensuremath{''}\times0.79\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 20 Apr      | /X25         | 226.17$-$228.04    | 7.81                     |               | 46.1$^\circ$                                   |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 228.17$-$230.04    | 7.81                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 212.17$-$214.04    | 7.81                     | 0.015$-$0.418 |                                                | 7.66        | 1.29        | 0.72         | 3.15              | 2.10        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2018        | A001/X12d1   | 214.17$-$216.04    | 7.81                     |               | $0.95\ensuremath{''}\times0.75\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 21 Apr      | /X27         | 226.17$-$228.04    | 7.81                     |               | 40.6$^\circ$                                   |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 228.17$-$230.04    | 7.81                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
|             |              | 212.17$-$214.04    | 7.81                     | 0.015$-$0.418 |                                                | 7.66        | 1.68        | 0.84         | 2.27              | 2.67        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2018        | A001/X12d1   | 214.17$-$216.04    | 7.81                     |               | $0.88\ensuremath{''}\times0.82\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 24 Apr      | /X255        | 226.17$-$228.04    | 7.81                     |               | 11.0$^\circ$                                   |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 228.17$-$230.04    | 7.81                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              |                    |                          |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+
| 1-12        |              | 85.34$-$87.20      | 7.81                     | 0.015$-$0.372 |                                                | 19.39       | 1.51        | 1.38         | 0.73              | 2.88        |             |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 2018        | A001/X12d0   | 87.34$-$89.20      | 7.81                     |               | $2.57\ensuremath{''}\times1.99\ensuremath{''}$ |             |             |              |                   |             | XX XY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
| 14 Apr      | /Xe          | 97.40$-$99.26      | 7.81                     |               | 4.3$^\circ$                                    |             |             |              |                   |             | YX YY       |
+-------------+--------------+--------------------+--------------------------+               +------------------------------------------------+             |             |              |                   |             +-------------+
|             |              | 99.34$-$101.20     | 7.81                     |               |                                                |             |             |              |                   |             |             |
+-------------+--------------+--------------------+--------------------------+---------------+------------------------------------------------+-------------+-------------+--------------+-------------------+-------------+-------------+

: M87 ALMA 12-m Observations and Imaging Properties

Table notes: cont.

# Continuum Properties

We summarize ALMA 12-m sample properties in Table [3](#tbl:sample), including the peak continuum intensity $S_\nu$ and MFS rms for each member OUS. In this section, we provide a brief description of the continuum-only data products and an upper limit to the dust thermal contributions at mm/sub-mm wavelengths.

## MFS imaging

Representative ALMA 12-m MFS imaging in Figure [2](#fig:mfs) captures the approaching jet and the double radio lobes in compact configurations while the extended configuration data resolve the central continuum from the collimated jet that is prominent in both lower-frequency VLBI and HST imaging (cite: reid89; biretta99; walker18). High-resolution Band 6 imaging isolates features M (sometimes referred to as L) and N1 that lie closer to the nucleus while N2 seen in VLBI data is only detected by ALMA as a slight elongation from the core when using uniform weighting. Notably, these data do not reveal (or are not sufficiently sensitive to detect) diffuse non-thermal emission beyond M that leads into the superluminal HST-1 clump at a distance of $\sim$1$''$ (cite: giroletti12; park19). From intermediate-resolution MFS imaging, we identify clumps A–F and I in the approaching jet.

We fit the X2c2 MFS image (with uniform weighting; $\theta_\mathrm{maj} \times \theta_\mathrm{min} = 27 \times 21$ mas$^2$ or a FWHM $\sim 2$ pc) using the `CASA` `imfit` task with a nuclear source and an additional, offset elliptical Gaussian to characterize the N2 clump. In the image-plane fit, the dominant source distribution is identical to the synthesized beam while the N2 component has observed FWHM axes of 49.5$\times$18.5 mas$^2$, appearing to be resolved only in the jet direction along a $\mathrm{PA} = -75.6\ensuremath{^\circ}$. While heavily affected by beam smearing, the N2 component centroid is offset from the nucleus by ($\Delta$R.A.,$\Delta$decl.) = ($-$20.0,+5.3) mas, which is consistent within the formal `imfit` uncertainties to its location in 22 GHz imaging taken just a few months later (cite: park19). The `imfit` components fitted to the core and the N2 clump have *integrated* flux densities of 1.220 Jy and 50.3 mJy, respectively, at 232.98 GHz. `imfit` residuals do not support any additional sources within the inner 50 mas with a background rms of $\sim$0.83 mJy beam$^{-1}$. The residual noise only marginally improves after *uv*-plane subtraction of the central point source using the `CASA` `uvmodelfit` task.

## Circumnuclear Dust

The high-resolution ALMA MFS imaging modeled previously in Section [6.1](#app:mfs) and shown in Figure [2](#fig:mfs) were hoped to provide additional constraints on heretofore unconfirmed circumnuclear thermal dust emission. The Band 6 `imfit` residuals do not support any resolved excess in the inner 50 mas ($\sim$4 pc), so we estimated a flux density upper limit for any extended thermal source by shifting a circular ($R = 0.05\ensuremath{''}$) aperture randomly to 100 continuum-free regions of the residual X2c2 MFS image to sample the noise, taking the standard deviation $\delta S_\mathrm{ext} = 0.75$ mJy as an effective 1$\sigma$ limit (cite: tsukui23). The enclosed dust mass limit

$$\begin{equation}
    M_\mathrm{dust} < \frac{\delta S_\mathrm{ext} D_L^2}{\kappa_\nu B_\nu(T_\mathrm{dust})}
\end{equation}$$

assumes a standard dust absorption coefficient $\kappa_\mathrm{850\,\mu m}$ and emissivity index $\beta = 2$ in the opacity relationship $\kappa_\nu = \kappa_\mathrm{850\,\mu m} (\nu/352.7\,\mathrm{GHz})^\beta$ (cite: draine03). For $T_\mathrm{dust} = 25$ K and a standard dust-to-gas mass ratio of $\sim$0.015 (cite: Sandstrom2013), this modified black body $M_\mathrm{dust} < 1.1\times 10^4$ $M_\odot$ would correspond to a total gas mass $M_\mathrm{gas} \lesssim 7.5\times10^5$ $M_\odot$. A hotter $T_\mathrm{dust} \sim 100$ K that follows the upper dust temperature distribution in ETGs (cite: kokusho19) would result in $M_\mathrm{dust} < 2.3\times 10^3$ $M_\odot$ and $M_\mathrm{gas} < 1.5\times 10^5$ $M_\odot$. These $M_\mathrm{dust}$ upper limits are between 6$-$30$\times$ more constraining than is the SED fitting of mid-IR flux densities at much more coarse resolution (cite: baes10) and the lower $M_\mathrm{gas}$ limit for hotter dust abuts against CO(1$-$0)-derived upper limits presented in Section [4.1](#sec:disc_em). Higher-frequency ALMA continuum imaging would better probe thermal emission up the Rayleigh-Jeans tail even as the synchrotron nucleus intensity decreases as $\nu^{-0.6}$ (see Appendix [7](#app:specslope)). However, DR limitations would dilute these improvements with nominal Bands 7 and 8 $\mathrm{DR}\sim 400$ and 250, respectively. Good observing conditions and standard self-calibration practices regularly allow for a factor of 2$\times$ higher DR (cite: privon24) reaching up to $\sim$2500 in Band 7 (cite: komugi22). Even in this best-case scenario, an estimated $\delta S_\mathrm{ext,\,Band\,7} \lesssim 0.5$ mJy limit would only probe 6$\times$ lower $M_\mathrm{dust}$ than above.

# Light Curves and Spectral Slopes

![](m87_alma_archive_cont_sed.pdf)

In addition to ALMA 12-m observations taken between 2014 to 2019, we retrieved additional ACA 7-m imaging in projects 2019.1.00807.S and 2021.1.01398.S ($\overline{\theta}_\mathrm{FWHM} \sim 5\ensuremath{''}$ in Band 6), which monitored the Band 3 and 6 variability of M87 around EHT campaigns in 2021 and 2022. We obtained these archival data and applied standard pipeline calibration followed by phase-only self-calibration prior to MFS imaging with typical limiting sensitivities of 60–80 mJy beam$^{-1}$. To construct more complete light curves shown in Figure [8](#fig:cont_sed), we joined together ALMA 12 and 7-m peak flux densities with Submillimeter Array (SMA) monitoring of M87 over this time frame (cite: event21c; event24).

From adjacent ACA observations in program 2021.1.01398.S that span $\sim$100$-$400 GHz, we measured an apparent mm/sub-mm spectral index $\alpha^{\prime} = -0.60\pm0.07$ from roughly contemporaneous data taken between 2022 April 2$-$3. Fit errors include both rms and absolute flux scaling uncertainties. More separate ALMA 12-m imaging in programs 2012.1.00661.S and 2015.1.01352.S covering $\sim$95$-$340 GHz were obtained between 2014 Jan 28 and 2015 October 27$-$31 and result in a best-fit $\alpha^{\prime} = -0.47\pm0.11$. Both spectral indices are consistent with a predominately synchrotron origin for the radio-continuum data for the core and jet regions (cite: biretta91; event21c). The more contemporaneous ALMA 12-m peak flux densities hint at a flattening spectral slope at longer wavelengths (cite: doi13), although we do not detect a transition to $\alpha > 0$ for $\lambda \gtrsim 3$ mm that is seen in VLBI data (cite: prieto16).

+:-----:+:------:+:---------------:+:-----------------------------:+:---------------------------------:+:-----:+:------------:+:-------:+:------:+
| Obs.           | Member          | $\overline{\nu}_\mathrm{obs}$ | $\overline{\theta}_\mathrm{FWHM}$ | Time  | Peak $S_\nu$ | MFS rms | PWV    |
+----------------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| Date           | OUS             | GHz                           | (arcsec)                          | (min) | (Jy)         | (mJy)   | \(mm\) |
+----------------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| \(1\)          | \(2\)           | \(3\)                         | \(4\)                             | \(5\) | \(6\)        | \(7\)   | \(8\)  |
+----------------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| **2019.1.00807.S** (PI: Ramakrishnan)                                                                                                          |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| 1-9   | Apr 11 | A001/X1527/X2bc | 221.10                        | 6.94$''$                          | 7.55  | 1.58         | 83.1    | 1.62   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 15 | A001/X1527/X2bf | 221.10                        | 6.95$''$                          | 7.55  | 1.55         | 80.4    | 1.14   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| 2021  | Apr 17 | A001/X1527/X2c2 | 221.10                        | 6.96$''$                          | 7.55  | 1.52         | 79.7    | 0.69   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 18 | A001/X1527/X2c5 | 221.10                        | 6.77$''$                          | 7.55  | 1.50         | 80.3    | 0.81   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 19 | A001/X1527/X2c8 | 221.10                        | 8.65$''$                          | 7.55  | 1.47         | 85.8    | 0.81   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| 1-9   |        |                 |                               |                                   |       |              |         |        |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| 1-9   | Mar 23 | A001/X15bc/X6a5 | 221.10                        | 6.05$''$                          | 7.55  | 1.17         | 59.1    | 1.00   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Mar 24 | A001/X15bc/X6a8 | 221.10                        | 4.69$''$                          | 7.55  | 1.47         | 76.8    | 0.26   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Mar 26 | A001/X15bc/X6ae | 221.10                        | 6.95$''$                          | 7.55  | 1.20         | 65.8    | 0.81   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Mar 27 | A001/X15bc/X6b1 | 221.10                        | 6.03$''$                          | 5.02  | 1.23         | 67.4    | 0.76   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Mar 28 | A001/X15bc/X7f8 | 97.50                         | 14.68$''$                         | 7.55  | 1.90         | 106.1   | 2.16   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Mar 28 | A001/X15bc/X6b4 | 221.97                        | 6.34$''$                          | 7.55  | 1.23         | 62.2    | 2.11   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Mar 29 | A001/X15bc/X6b7 | 221.10                        | 6.64$''$                          | 7.55  | 1.23         | 63.8    | 2.27   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| 2022  | Mar 30 | A001/X15bc/X6ba | 221.10                        | 6.31$''$                          | 7.55  | 1.23         | 62.4    | 1.19   |
|       +--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Mar 31 | A001/X15bc/X6bd | 221.10                        | 6.72$''$                          | 7.55  | 1.23         | 62.9    | 1.36   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 1  | A001/X15bc/X6c0 | 221.10                        | 6.76$''$                          | 7.55  | 1.22         | 62.0    | 0.30   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 2  | A001/X15bc/X26a | 203.00                        | 6.11$''$                          | 5.02  | 1.13         | 58.1    | 1.47   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 2  | A001/X15bc/X278 | 343.50                        | 4.19$''$                          | 5.84  | 0.73         | 79.6    | 0.80   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 2  | A001/X15bc/X6c3 | 221.10                        | 6.45$''$                          | 7.55  | 1.22         | 61.8    | 0.87   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 3  | A001/X15bc/X7fb | 95.70                         | 16.49$''$                         | 5.02  | 1.83         | 107.0   | 1.22   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 3  | A001/X15bc/X6c6 | 221.10                        | 6.72$''$                          | 7.55  | 1.23         | 63.2    | 1.36   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
|       | Apr 4  | A001/X15bc/X271 | 233.00                        | 7.36$''$                          | 5.02  | 1.27         | 67.5    | 0.64   |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+
| 1-9   |        |                 |                               |                                   |       |              |         |        |
+-------+--------+-----------------+-------------------------------+-----------------------------------+-------+--------------+---------+--------+

: M87 ACA 7-m Observations and Imaging Properties

Table notes: Continuum properties of archival ACA 7-m data sets. Cols. (3) and (4) give the average frequency of the final MFS image across all spws and average synthesized beam FWHM from Briggs ($r=0.5$) imaging. Col. (5) gives the on-source integration time while cols. (6) and (7) report the peak and rms intensities of each MFS image. Col. (8) reports average PWV conditions. Each project used the same $\Delta\nu_\mathrm{obs} = 15.6$ MHz TDM channel binning with dual polarization set-up.

At radio to mm wavelengths, the M87 nucleus light curve has been (visually) consistent with a damped-random walk (DRW) over the past decade or so with $\sim$50% variability on $\sim$few month timescales (cite: acciari09; hess11; hada14; bower15) preceded by a larger flaring event in 2005 spanning a few years (cite: abramowski12). Strong, persistent variability may introduce large uncertainties in the SED slope measured from non-contemporaneous data across a relatively narrow frequency range. We tested the impact for the above $\alpha^\prime$ by creating mock light curves in ALMA Bands 3, 6, and 7 whose variability was defined by the power spectral density (PSD) fits to other radio galaxies (cite: zhang20). Following the methodology outlined by (cite: emmanoulopoulos13), we simulated an ALMA Band 6 peak light curve spanning 2 yrs with a one-day cadence. Additional Bands 3 and 7 light curves were then created using a consistent (intrinsic) $\alpha_\mathrm{intr} = -0.6$ at each time epoch. We evaluated the change in recovered $\alpha^{\prime}$ relative to $\alpha_\mathrm{intr}$ when the Bands 3 and 7 measurements were drawn from days to months separate from the Band 6 values. For each synthetic measurement, we added random, realistic noise drawn from a normal distribution following standard absolute flux calibration uncertainties (cite: fomalont14). We then collected these $\alpha^{\prime}$ for a given time separation across the entire synthetic light curve and take the standard deviation of the $\alpha_\mathrm{intr} - \alpha^{\prime}$ values as a proxy for the total uncertainty $\delta\alpha^{\prime}$ when using non-contemporaneous ALMA measurements. When synthetic measurements are separated by at most a few days, we find a standard deviation $\delta \alpha^{\prime}\sim 0.05$; for few-week to few-month separations, $\delta\alpha^{\prime}$ increases from $\sim$0.15 until flattening around $\sim$0.35. As a result, the ALMA 12-m $\alpha^\prime = -0.47\pm0.11$ that includes an $S_\mathrm{\nu,Band\,7}$ point taken over 1.5 years before the remaining closely-sampled Bands 3–6 data underestimates the true uncertainty by at least a factor of 3. We note that $\alpha^{\prime}$ measured across broad radio (or radio-to-mm) frequency ranges will be less susceptible to uncertainty introduced by DRW variability.

# Peak Continuum Spectra

In Figure [9](#fig:contabs), we present peak flux density spectra of all member OUS listed in Table [3](#tbl:sample). The spectra show no strong molecular line features except for residual contamination from atmospheric ozone, which we discuss in Appendix [9](#app:atm). Spectral shapes are not always consistent across all spws in a single setup or as a function of time. We attribute this to either limitations in the standard pipeline calibration process or assumptions about the calibrator spectral index.

ALMA bandpass and flux calibrations typically rely on week to few-month cadence monitoring of bright AGN ($S_\nu\sim0.1-2$ Jy) that are tied to Solar System standards (cite: bonato19). For point-source AGN, mm-wavelength flux densities have a median $\sim$10% variability amplitude over $\sim$year timescales (cite: sadler08; bonato19). Calibrator flux densities are updated in the ALMA Calibrator Source Catalogue (CSC) and recorded in pipeline files for MS reconstruction. This approach does not always account for the power-law spectral index of a calibrator (reflected by the `spix` parameter in the `setjy` task) or `spix` variability. Bandpass and flux calibrators are overwhelmingly selected from radio quasars and BL Lac-type objects that show approximately flat spectral shapes as measured in L to C radio bands. In ALMA Bands, however, the mm/sub-mm spectral index $\alpha$ is often more characteristic of classical synchrotron radiation, (cite: bonato18). In some cases, the pipeline calibration process adopted a non-zero `spix` based on a roughly contemporaneous spectral index measurement, but this was not uniform in the earlier ALMA Cycles.

![](m87_alma_archive_contabs_fig1.pdf)

![](m87_alma_archive_contabs_fig2.pdf)

Within a single sideband, `spix` discrepancies led to inconsistencies in the relative M87 flux densities in individual spws at the 1–2% level. For adjacent EBs separated by just an hour, even when using the same calibrators, the inter-spw $\alpha$ value changes by up to $\sim$10% (see Figure [14](#fig:bandpass)). The main outlier is the X20d data set, whose inter-spw $\alpha$ is much steeper than roughly contemporaneous ALMA Band 6 observations and SED slopes in Figure [8](#fig:cont_sed). We attribute this discrepancy to poor spw-dependent phase solutions during self-calibration. Over all spws for a given spectral setup, the typical inter-spw $\alpha$ after standard pipeline and self-calibration processes spans a broad range of $-$0.1 to $-$1.0. Some of this scatter for Band 3 data may be attributable to the apparent $S_\nu$ flattening for $\nu \lesssim 100$ GHz (cite: prieto16). Intra-spw slopes are particularly unreliable (cite: francis20a), in part due to bandpass calibration limitations (see Appendix [11.3](#app:bandpass)).

# Atmospheric Modeling

The deepest atmospheric absorption features (primarily water vapor) often set the frequency ranges for mm/sub-mm Bands. For Band 3, an O$_2$ line ($N=1-1$ $J=1-0$; $\nu_\mathrm{sky} = 118.750$ GHz) limits coverage in practice to a topocentric $\nu_\mathrm{sky} < 115.93$ GHz. As we demonstrate in Appendix [11.3](#app:bandpass), this impacts the continuum subtraction reliability near CO(1$-$0) and may contribute to the spurious broad absorption or emission-line features. Pipeline calibration does correct for most of the transmission drop due to broad H$_2$O and O$_2$ absorption. However, in the X1b4 peak continuum spectrum the spw nearest the broad H$_2$O feature centered at $\nu_\mathrm{sky} = 325.15$ GHz shows some residual spectral curvature in the first EB (see Figure [10](#fig:ozone_var)) as the relative humidity decreases rapidly after the initial calibration scans.

From the continuum spectral cubes, we identified several absorption and emission features that could not be matched to Galactic or extragalactic lines but that did coincide with various telluric ozone (O$_3$) transitions in the topocentric frame. (cite: hunter18) demonstrated that the coarse TDM atmospheric calibration used for these ALMA 12-m data may over/undercorrect for atmospheric ozone, resulting in either positive/negative residuals, respectively. These lines have been further studied by the PHANGS-ALMA team in Band 6 around redshifted CO(2$-$1) in their total-power array imaging, primarily as a function of elevation or airmass (cite: usero19; leroy21) while assuming that atmospheric conditions (e.g., relative humidity, ambient temperature, and O$_3$ concentration) are stable over 1$-$2 EBs (1$-$2 hours). Here, we focus on atmospheric variability on these timescales as well as the impact of calibrator offset on the correction of telluric line features. Since the O$_3$ transitions do not generally interfere with most of the extragalactic line transitions at the redshift of M87, we did not attempt to mitigate their impact by constructing $T_\mathrm{sys}$ spectra in FDM mode during manual calibration in `CASA` (cite: hunter18). In Figure [9](#fig:contabs) and elsewhere, we indicate the frequencies of the ozone and water vapor transitions that have CDMS/JPL logarithmic intensities[^6] (cite: pickett98; muller05) brighter than $-$5.3, the limiting depth down to which ozone lines have been detected in these ALMA 12-m data. Fractional depths are only a fraction of a percent in the highest-SDR data sets.

To aid in identifying and characterizing faint ozone features, we employed the `am` atmospheric modeling tool (cite: paine18) to calculate an atmospheric transmission curve for each continuum spectrum. This approach adopts column densities for select molecules and approximates the vertical structure with layers of varying pressure and temperature. Without detailed conditions above the Atacama plateau, we borrowed the realistic `am` manual model for Mauna Kea at nearly the same altitude after adjusting for the average PWV, target elevation, and ground-layer temperature for each MS. Using the same spectral ranges and binning, we constructed final transmission curves for each spw and shifted them to barycentric frame to more easily compare to $S_\nu$ plots in Figure [9](#fig:contabs). These `am` model results are close to those from the `Atmospheric Transmission at Microwaves` model (cite: pardo01; pardo19) used during `CASA` calibration, especially after `ATM` included additional minor lines and was tuned for both observed seasonal and diurnal O$_3$ concentration and altitude changes (cite: frith20; pardo24).

These ozone features are typically distinct from major molecular transitions at a barycentric $z_\mathrm{obs} = 0.004283$, although one O$_3$ transition \[23(5,19)$-$24(4,20); $\nu_\mathrm{sky} = 229.575$ GHz\] lies close to the CO(2$-$1) frequency for low redshift targets. For the X20f data set, the archival calibration script manually flagged a narrow range of channels for the bandpass calibrator (J1229+0203; 3C 273), misidentifying an atmospheric ozone line as extragalactic in origin. The result was a sharp, moderately deep (cite: ray24), spurious absorption feature in the corresponding calibrated M87 spectral window near redshifted $\nu_\mathrm{CO(2-1)}$. During pipeline calibration, the wings of this ozone feature remain apparent as slight excesses due to $T_\mathrm{sys}$ calculations being carried out in TDM mode. After inspecting the relevant frequency range when this calibrator was a science target in project 2019.1.00807.S, we could not identify a line feature or possible molecular gas candidate at the calibrator’s redshift ($z_\mathrm{obs} = 0.15834$). We removed these flags before re-calibrating the raw data and re-imaging the X20f MS. This removed nearly all of the ozone line contamination and revealed the faint CO(2$-$1) absorption feature. None of the other data sets appear to have similar flagging issues.

Atmospheric phase differences between baselines vary with characteristic timescales of minutes. While many studies of water vapor or O$_3$ column densities tend to track differences on hour timescales or longer (cite: rappengluck14; zhang14; maud23), rapid changes decrease the coherence time for high-frequency observations (cite: matsushita17) and increase phase fluctuations, especially for extended ALMA configurations (cite: privon24). Regular WVR measurements correct for smaller-scale, more rapidly-varying PWV changes, and phase self-calibration works to remove residual path length discrepancies. Due to the bright mm/sub-mm continuum source at the center of M87, clean phase solutions can generally be obtained through iterative self-calibration by using the `CASA` `gaincal` task on timescales as short as the scan length. We find that these phase self-calibration loops mitigate nearly all path length fluctuations that arise due to tropospheric turbulence, even on the longest ALMA baselines. However, for two exceptions – the X20d data set and the first EB of X1b0 (see Figure [4](#fig:colineabsfit)) – the standard self-calibration process never produced sufficiently clean phase solutions regardless of the choice of `refant` or `solint`. The resulting spectra were less reliable due to poorer rms sensitivity or much lower flux scaling as well as high `CLEAN` residuals.

Good bandpass calibrators are not always found close to the science target on the sky, but those that are significantly removed in time or obtained along a far-removed line of sight have the potential to leave imprints of atmospheric lines on calibrated science data (cite: meena10; frith20). In Figure [10](#fig:ozone_var), we show peak $S_\mathrm{\nu,Band\,7}$ spectra obtained in the X1b4 data set during Cycle 1, showing residual O$_3$ absorption \[in the 11(2,10)$-$11(1,11) and 2(2,0)$-$1(1,1) transitions; $\nu_\mathrm{sky} = 332.705$ and 332.882 GHz, respectively\]. The `am` model with matching observing conditions shows a fractional depth of $\sim$0.18 for the deeper O$_3$ line compared to the neighboring continuum. In this member OUS, the bandpass calibrators for the first (J1058+0133) and second (J1229+0203) EB were separated by 25.3$^\circ$ and 10.3$^\circ$ from M87, respectively, and `ATM` models removed about 55% and 90% of the expected ozone absorption towards M87 during the standard `CASA` pipeline calibration. For the second EB, the bandpass calibrator appears to have been observed through a more similar $N_\mathrm{O_3}$, enabling a better telluric correction. We note that PWV or relative humidity trends are not mirrored by the residual O$_3$ line strengths as the molecules originate from different altitudes (O$_3$ primarily at $\sim$15$-$40 km while the H$_2$O scale height is 1$-$2 km). Variable $N_\mathrm{O_3}$ is suggested by other data sets with both distant and close bandpass calibrators, especially in projects 2013.1.00073.S and 2013.1.01022.S (both using J1229+0203), and the very strong residuals in 2016.1.01154.V (using B1730-130 and 4C 01 28, with separations of 79.1$^\circ$ and 25.3$^\circ$, respectively). Positive O$_3$ line features in the target spectral cube suggest a higher $N_\mathrm{O_3}$ towards the bandpass calibrator than towards the science target. Assuming that $N_\mathrm{O_3}$ scales linearly with the depth of unsaturated O$_3$ absorption lines, the residual depths shown in Figure [10](#fig:ozone_var) for a single EB suggest that either stratospheric or ground-layer $N_\mathrm{O_3}$ along the line of sight changed by up to $\sim$6% over just 30 min.

# Channel Maps

While most CO emission in other nearby cool-core galaxies is resolved on sub-arcsecond scales, the Xa1 data set with MRS $\gtrsim 3\ensuremath{''}$ cannot entirely rule out diffuse emission spread out over a couple of the larger regions with $\sim$5$''$ extent. Line profiles shown in Figure [3](#fig:lineprof) do not show any strong support for CO(1$-$0) emission in the CND or the other regions. However, (cite: ray24) purport to find evidence for a CND traced by CO(1$-$0) with a $\sim$200-pc extent. Their work relies on the X1b0 data set ($\overline{\theta}_\mathrm{FWHM} \sim 1.7\ensuremath{''}$; MRS $\sim 12\ensuremath{''}$) from ALMA Cycle 1 with $\sim$40 km s$^{-1}$ channel binning. In Figure [11](#fig:comp_channels), we present circumnuclear channel maps from continuum-subtracted cubes in the X1b0, Xa1, and X20f data sets with similarly broad binning. For the X1b0 data set, we include maps made from either of the two adjacent EBs. We find that phase self-calibration and continuum subtraction for the first EB (rms = 0.95 mJy beam$^{-1}$ per channel) was less successful at removing the continuum contributions than for the second EB (rms = 0.42 mJy beam$^{-1}$), resulting in sidelobe features at the $\sim$2% level that appear around the removed central source (see Figure [9](#fig:contabs)). Channel maps for the second EB of the X1b0 data set as well as the Xa1 and X20f data show no clear CO(1$-$0) or CO(2$-$1) sources near the center of M87.

In the case of unresolved CO emission, the H$_2$ surface mass density in $M_\odot$ pc$^{-2}$ over a single beam area is:

$$\begin{equation}
    \Sigma_\mathrm{H_2,\,limit} \approx 1220 \left[\frac{\alpha_\mathrm{CO}}{\nu^2 \theta_\mathrm{maj}\theta_\mathrm{min}}\right]\Delta v \times \mathrm{rms} \,,
\end{equation}$$

where $\nu$ is in GHz, the synthesized beam FWHM are in arcseconds, the point-source sensitivity rms is in mJy, and the channel width $\Delta v$ is in km s$^{-1}$. Using the same $\alpha_\mathrm{CO(1-0)}$ as in Section [3.1](#sec:narrowem), the composite X1b0 data (rms = 0.57 mJy beam$^{-1}$ per channel) should give a $\Sigma_\mathrm{H_2,\,limit} \sim 2.3$ $M_\odot$ pc$^{-2}$ in each beam. Over the putative $R\sim 200$ pc extent for a slightly flattened CND, this $\Sigma_\mathrm{H_2}$ 1$\sigma$ limit would translate to $M_\mathrm{H_2,\,limit}\sim 2\times 10^5$ $M_\odot$, similar to the limit from non-detection in the more physically-motivated CND or annulus regions in Table [1](#tbl:narrowem). Near the redshifted CO transition, the Xa1 data (rms = 0.34 mJy beam$^{-1}$ per channel; $\overline{\theta}_\mathrm{FWHM} \sim 0.21\ensuremath{''}$) should be sensitive to $\sim$84 $M_\odot$ pc$^{-2}$ while the X20f data (rms = 0.44 mJy beam$^{-1}$; $\overline{\theta}_\mathrm{FWHM} \sim 0.49\ensuremath{''}$) and an $R_{21} \sim 0.7$ ratio of CO(2$-$1) to CO(1$-$0) luminosities gets down to $\sim$7.5 $M_\odot$ pc$^{-2}$.

# Constraints on Broad CO Features

Here, we present broad but very low-amplitude spectral deficits or excesses about redshifted CO when excluding wide channel ranges during continuum subtraction. To aid in future line studies, we detail evidence that they arise naturally from the inherent limitations of ALMA bandpass calibration instead of broad CO absorption or emission.

## Broad CO Absorption

The $\pm$500 km s$^{-1}$ range used before to explore CO emission or absorption may be too narrow to study possible molecular outflows (cite: cicone14). After excluding channels with $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 1000$ km s$^{-1}$ in the `uvcontsub` task, we imaged the deeper X1b0, X5, and Xa1 data sets (Band 3) as well as those from X20d and X20f (Band 6) covering redshifted CO(1$-$0) and CO(2$-$1) into spectral cubes with $\sim$40 km s$^{-1}$ channel binning. For the X1b4 data set (Band 7), we excluded a narrower channel range with $-1000 < \ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}< 400$ km s$^{-1}$ due to more limited frequency coverage when constructing a CO(3$-$2) cube. Line profiles integrated over their central beam areas (Figure [12](#fig:broadabs)) show apparent deficits in the $-1000 < \ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}< 100$ km s$^{-1}$ range. In Band 3, these broad spectral deficits translate to apparent peak opacities $\tau_\mathrm{0,CO(1-0)} \sim 0.002 - 0.004$ with S/N $\sim 5-25$ relative to the rms of the continuum-fitting channels. Over that velocity range, the corresponding integrated $\tau_\mathrm{CO(1-0)} \sim 0.1-0.3$ km s$^{-1}$ with S/N $> 10$ would far exceed the narrow CO absorption in Table [2](#tbl:narrowabs). This apparent CO(1$-$0) opacity signature is not replicated in the higher-frequency Bands.

If real, these deficits would seem to trace a molecular outflow that is much faster than the blueshifted atomic outflows suggested by optical emission-line studies (cite: osorno23) or narrow absorption (cite: tsvetanov99b; sabra03). Molecular ouflows have been detected in absorption against ultraluminous infrared galaxy nuclei and AGN at a few $\times$100 km s$^{-1}$ to $\sim$1000 km s$^{-1}$ (cite: veilleux13; stone16; nagai19; herrera20). Such molecular outflows are also detected in emission with blueshifts reaching similar terminal speeds (cite: cicone14; garciaburillo14; riffel20; bolatto2021). In LINERs like M87, however, the core luminosity is well below the expected threshold to drive a broad outflow (cite: veilleux13; prieto16). The primary arguments against a fast-outflow interpretation are the inconsistent spectral behavior and the low amplitude. First, the velocity extremes vary by up to $\sim$600 km s$^{-1}$ for the CO(1$-$0) transition. Second, peak fractional deficits $1-\exp^{-\tau_0} \approx 0.00025$ are at or below the level of the bandpass stability.

![](m87_alma_co_broadabs.pdf)

## Broad CO Emission

When first exploring continuum subtraction and CO line profiles for these M87 data sets, we noticed hints of CO excess reaching out to $\pm$2000 km s$^{-1}$, which could be attributed to a pc-scale disky structure. To explore this possibility, we excluded channels with $100 < |\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 2200$ km s$^{-1}$ in the `uvcontsub` task (with `fitorder` = 1) and imaged redshifted CO(1$-$0) in the X5 and Xa1 data sets into cubes with 40 km s$^{-1}$ bins. Care was taken to avoid channels at spw edges that showed poor response or whose flux densities were discrepant with those in overlapping spws. Unfortunately, higher-$J$ transitions did not have sufficient frequency coverage (or spw overlap) to allow for reliable continuum subtraction following these $|\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}|$ exclusions. In Figure [13](#fig:emission), we show CO(1$-$0) position-velocity diagrams (PVDs) extracted in a N–S direction with a width matching the beam average FWHM. The putative excesses are roughly centered around $\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}= -2200$ and +1000 km s$^{-1}$, with spatial centroids separated by as little as 0.015$''$ ($\sim$1 pc). Because this excess appeared to be almost unresolved in either case, we constructed line profiles by integrating over the central region with a circular $R=\overline{\theta}_\mathrm{FWHM}$ aperture.

![](m87_coemission_kin_Xa1_X5_sma.pdf)

From the more symmetrical Xa1 CO line profile, the integrated excess of 4.5 Jy km s$^{-1}$ would be contained within the X5 beam ($R<4$ pc) and correspond to $M_\mathrm{H_2} \sim 3\times 10^6$ $M_\odot$ and $\overline{\Sigma}_\mathrm{H_2} \gtrsim 2\times 10^4$ $M_\odot$ pc$^{-2}$, far exceeding central molecular gas surface mass densities on similar scales in similar targets (cite: garciaburillo16). A measured CO(1$-$0) map for the Xa1 data set is inconsistent with the ionized gas disk orientation; also, the putative CO(1$-$0) emission is much smaller than $\overline{\theta}_\mathrm{FWHM}$ for the Xa1 data set, so a rotating disk cannot explain the moment 1 map gradient in the N–S direction[^7] in Figure [13](#fig:emission). The bulk of the Xa1 line profile excess would be inconsistent with the essentially unresolved excesses in the X5 data set.

In addition to the above, detection of a CND traced by CO(1$-$0) on such scales is improbable based on the spectral behavior. Positive features in the X5 and Xa1 line profiles are not sufficiently consistent or symmetrical, and nor are they well centered about $v_\mathrm{sys}$. Some of that problem may arise from limited frequency coverage for $\nu>115.5$ GHz ($\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}< -1900$ km s$^{-1}$) and plausible overcorrection of the deep O$_2$ absorption. Finally, the maximum excess flux densities in the integrated line profiles reach only $\sim$0.15% of the continuum levels, matching the $\sim$0.1% amplitude variation seen when testing bandpass stability over larger frequency ranges (cite: kameno14).

## Bandpass Calibration Accuracy

The maximum SDR $\sim 2000$ measured in individual channels for the Band 3 data sets corresponds to $\mathrm{min}(\tau_0) \sim 0.0002$, enabling the narrow CO absorption-line detection discussed in Section [3.2](#sec:narrowcoprops). The larger frequency response is set by the bandpass calibration, so broad line signatures are impacted by the bandpass calibration accuracy. (cite: kameno14) demonstrated that cross-correlation bandpass calibration remained stable at the 0.2% level over short time frames ($\sim$1 hr for Bands 3 and 6), producing a mostly flat spectral response with a lower effective SDR $\sim 500$ or $\min(\tau_0) \sim 0.002$ over an entire spw. Below this threshold, noticeable spectral structure arises above the white-noise predictions for frequency separations $\Delta\nu \gtrsim 250$ MHz (100$-$200 MHz and $\gtrsim$500 MHz) in Band 3 (cite: kameno14). This means that fully calibrated spectra may have very low-amplitude fluctuations imprinted on velocity scales of $\Delta v \gtrsim 650$ km s$^{-1}$ (130$-$160 km s$^{-1}$ and $\gtrsim$650 km s$^{-1}$).

In Figure [14](#fig:bandpass), we compare the spectral behavior for individual spws in a single sideband from all standard ALMA programs covering redshifted CO(1$-$0) and CO(2$-$1) transitions. For Band 3 peak spectra, both the CO-centered and adjacent spws show similar fluctuations reaching the 0.1$-$0.3% level relative to the spw channel outskirts. In the lower sideband, adjacent spws also show similar spectral response (e.g., for the X5 and X2be data; see Figure [9](#fig:contabs).) The downward fluctuation between 0$-$0.5 GHz relative to the spw center coincides with the apparent spectral deficits seen in Figure [12](#fig:broadabs). Such fluctuations arising from bandpass amplitude calibration may mimic faint, broad absorption for a fast outflow. For very low-amplitude, broad spectral features, we find a more appropriate SDR $\sim 300-1000$ limit across an entire Band 3 spw using the standard bandpass calibration. Because these Band 3 spectra abut a strong O$_2$ absorption feature, the higher-frequency spw may also be negatively impacted by the $T_\mathrm{sys}$ undercorrection in the line wings as well as slight changes in $N_\mathrm{O_2}$ between the bandpass and science scans, either due to temporal variations or angular separation. In Band 6, the spectral shape appears more consistent with fluctuations at or below the 0.05% level, matching its native SDR. However, the small sample size of deep Band 6 imaging with fine FDM binning prevents any clear conclusions.

![](m87_bandpass_accuracy.pdf)

We find further support for a bandpass calibration origin for these low-amplitude spectral features in the peak $S_\nu$ spectra in roughly contemporaneous observations shown in Figure [9](#fig:contabs). For example, the $S_\nu$ behavior over 102$-$104 GHz in the X5 data set is inconsistent with those covering the same spectral range in Xbe and X135 data sets, which were obtained just weeks apart. While the latter two member OUS used a different bandpass calibrator (J1229+0203) than the former (J1256–0547), differences in the calibrated, intra-spw shape is still within the quoted limitations for bandpass calibration (cite: privon24). For these reasons, we view the very low amplitude spectral deficits or excess features in Figures [12](#fig:broadabs) and [13](#fig:emission) as spurious and arising from a patterned response in the bandpass amplitude calibration for adjacent basebands. The mostly regular shape and extent of the seemingly broad CO(1$-$0) absorption in Figure [12](#fig:broadabs) would then be a product of spw placement relative to the redshifted CO transition and proximity to the O$_2$ line that defines the end of the Band coverage.

natexlab

(ref: abramowski12) Abramowski, A., Acero, F., Aharonian, F., et al. 2012, ApJ, 746, 151, doi: [`10.1088/0004-637X/746/2/151`](http://doi.org/10.1088/0004-637X/746/2/151)

(ref: acciari09) Acciari, V. A., Aliu, E., Arlen, T., et al. 2009, Science, 325, 444, doi: [`10.1126/science.1175406`](http://doi.org/10.1126/science.1175406)

(ref: event24) Algaba, J. C., Baloković, M., Chandra, S., et al. 2024, A&A, 692, A140, doi: [`10.1051/0004-6361/202450497`](http://doi.org/10.1051/0004-6361/202450497)

(ref: andre22) André, P. J., Palmeirim, P., & Arzoumanian, D. 2022, A&A, 667, L1, doi: [`10.1051/0004-6361/202244541`](http://doi.org/10.1051/0004-6361/202244541)

(ref: arzoumanian13) Arzoumanian, D., André, P., Peretto, N., & Könyves, V. 2013, A&A, 553, A119, doi: [`10.1051/0004-6361/201220822`](http://doi.org/10.1051/0004-6361/201220822)

(ref: arzoumanian18) Arzoumanian, D., Shimajiri, Y., Inutsuka, S.-i., Inoue, T., & Tachihara, K. 2018, PASJ, 70, 96, doi: [`10.1093/pasj/psy095`](http://doi.org/10.1093/pasj/psy095)

(ref: arzoumanian11) Arzoumanian, D., André, P., Didelon, P., et al. 2011, A&A, 529, L6, doi: [`10.1051/0004-6361/201116596`](http://doi.org/10.1051/0004-6361/201116596)

(ref: babyk19) Babyk, I. V., McNamara, B. R., Tamhane, P. D., et al. 2019, ApJ, 887, 149, doi: [`10.3847/1538-4357/ab54ce`](http://doi.org/10.3847/1538-4357/ab54ce)

(ref: Baek2022) Baek, J., Chung, A., Edge, A., et al. 2022, ApJ, 932, 64, doi: [`10.3847/1538-4357/ac6de6`](http://doi.org/10.3847/1538-4357/ac6de6)

(ref: baes10) Baes, M., Clemens, M., Xilouris, E. M., et al. 2010, A&A, 518, L53, doi: [`10.1051/0004-6361/201014555`](http://doi.org/10.1051/0004-6361/201014555)

(ref: bianchi12) Bianchi, S., Maiolino, R., & Risaliti, G. 2012, Advances in Astronomy, 2012, 782030, doi: [`10.1155/2012/782030`](http://doi.org/10.1155/2012/782030)

(ref: bicknell96) Bicknell, G. V., & Begelman, M. C. 1996, ApJ, 467, 597, doi: [`10.1086/177636`](http://doi.org/10.1086/177636)

(ref: bieging81) Bieging, J. H., Blitz, L., Lada, C. J., & Stark, A. A. 1981, ApJ, 247, 443, doi: [`10.1086/159052`](http://doi.org/10.1086/159052)

(ref: biretta99) Biretta, J. A., Sparks, W. B., & Macchetto, F. 1999, ApJ, 520, 621, doi: [`10.1086/307499`](http://doi.org/10.1086/307499)

(ref: biretta91) Biretta, J. A., Stern, C. P., & Harris, D. E. 1991, AJ, 101, 1632, doi: [`10.1086/115793`](http://doi.org/10.1086/115793)

(ref: blakeslee09) Blakeslee, J. P., Jordán, A., Mei, S., et al. 2009, ApJ, 694, 556, doi: [`10.1088/0004-637X/694/1/556`](http://doi.org/10.1088/0004-637X/694/1/556)

(ref: boizelle17) Boizelle, B. D., Barth, A. J., Darling, J., et al. 2017, ApJ, 845, 170, doi: [`10.3847/1538-4357/aa8266`](http://doi.org/10.3847/1538-4357/aa8266)

(ref: boizelle19) Boizelle, B. D., Barth, A. J., Walsh, J. L., et al. 2019, ApJ, 881, 10, doi: [`10.3847/1538-4357/ab2a0a`](http://doi.org/10.3847/1538-4357/ab2a0a)

(ref: boizelle21) Boizelle, B. D., Walsh, J. L., Barth, A. J., et al. 2021, ApJ, 908, 19, doi: [`10.3847/1538-4357/abd24d`](http://doi.org/10.3847/1538-4357/abd24d)

(ref: bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: bolatto2021) Bolatto, A. D., Leroy, A. K., Levy, R. C., et al. 2021, ApJ, 923, 83, doi: [`10.3847/1538-4357/ac2c08`](http://doi.org/10.3847/1538-4357/ac2c08)

(ref: bonato18) Bonato, M., Liuzzo, E., Giannetti, A., et al. 2018, MNRAS, 478, 1512, doi: [`10.1093/mnras/sty1173`](http://doi.org/10.1093/mnras/sty1173)

(ref: bonato19) Bonato, M., Liuzzo, E., Herranz, D., et al. 2019, MNRAS, 485, 1188, doi: [`10.1093/mnras/stz465`](http://doi.org/10.1093/mnras/stz465)

(ref: boselli19) Boselli, A., Fossati, M., Longobardi, A., et al. 2019, A&A, 623, A52, doi: [`10.1051/0004-6361/201834492`](http://doi.org/10.1051/0004-6361/201834492)

(ref: bower15) Bower, G. C., Dexter, J., Markoff, S., et al. 2015, ApJL, 811, L6, doi: [`10.1088/2041-8205/811/1/L6`](http://doi.org/10.1088/2041-8205/811/1/L6)

(ref: braine93) Braine, J., & Wiklind, T. 1993, A&A, 267, L47

(ref: brauher08) Brauher, J. R., Dale, D. A., & Helou, G. 2008, ApJS, 178, 280, doi: [`10.1086/590249`](http://doi.org/10.1086/590249)

(ref: briggs95) Briggs, D. S. 1995, PhD thesis, New Mexico Institute of Mining and Technology

(ref: buson09) Buson, L., Bressan, A., Panuzzo, P., et al. 2009, ApJ, 705, 356, doi: [`10.1088/0004-637X/705/1/356`](http://doi.org/10.1088/0004-637X/705/1/356)

(ref: cappellari03) Cappellari, M., & Copin, Y. 2003, MNRAS, 342, 345, doi: [`10.1046/j.1365-8711.2003.06541.x`](http://doi.org/10.1046/j.1365-8711.2003.06541.x)

(ref: cappellari11) Cappellari, M., Emsellem, E., Krajnović, D., et al. 2011, MNRAS, 413, 813, doi: [`10.1111/j.1365-2966.2010.18174.x`](http://doi.org/10.1111/j.1365-2966.2010.18174.x)

(ref: cardelli89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245, doi: [`10.1086/167900`](http://doi.org/10.1086/167900)

(ref: carter92) Carter, D., & Jenkins, C. R. 1992, MNRAS, 257, 7P, doi: [`10.1093/mnras/257.1.7P`](http://doi.org/10.1093/mnras/257.1.7P)

(ref: carter97) Carter, D., Johnstone, R. M., & Fabian, A. C. 1997, MNRAS, 285, L20, doi: [`10.1093/mnras/285.3.L20`](http://doi.org/10.1093/mnras/285.3.L20)

(ref: cashman21) Cashman, F. H., Fox, A. J., Savage, B. D., et al. 2021, ApJL, 923, L11, doi: [`10.3847/2041-8213/ac3cbc`](http://doi.org/10.3847/2041-8213/ac3cbc)

(ref: chen24) Chen, M. C.-Y., Di Francesco, J., Friesen, R. K., et al. 2024, ApJ, 977, 135, doi: [`10.3847/1538-4357/ad88e8`](http://doi.org/10.3847/1538-4357/ad88e8)

(ref: cheung07) Cheung, C. C., Harris, D. E., & Stawarz, Ł. 2007, ApJL, 663, L65, doi: [`10.1086/520510`](http://doi.org/10.1086/520510)

(ref: chiaberge99) Chiaberge, M., Capetti, A., & Celotti, A. 1999, A&A, 349, 77. [`https://arxiv.org/abs/astro-ph/9907064`](https://arxiv.org/abs/astro-ph/9907064)

(ref: choi24) Choi, W., Bureau, M., Liu, L., et al. 2024, MNRAS, 531, 4045, doi: [`10.1093/mnras/stae1394`](http://doi.org/10.1093/mnras/stae1394)

(ref: cicone14) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21, doi: [`10.1051/0004-6361/201322464`](http://doi.org/10.1051/0004-6361/201322464)

(ref: combes07) Combes, F., Young, L. M., & Bureau, M. 2007, MNRAS, 377, 1795, doi: [`10.1111/j.1365-2966.2007.11759.x`](http://doi.org/10.1111/j.1365-2966.2007.11759.x)

(ref: cortes24) Cortes, P. C., Vlahakis, C., Hales, A., et al. 2024, , 11.3, Zenodo Zenodo, doi: [`10.5281/zenodo.4511521`](http://doi.org/10.5281/zenodo.4511521)

(ref: crocker12) Crocker, A., Krips, M., Bureau, M., et al. 2012, MNRAS, 421, 1298, doi: [`10.1111/j.1365-2966.2011.20393.x`](http://doi.org/10.1111/j.1365-2966.2011.20393.x)

(ref: csengeri17) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 600, L10, doi: [`10.1051/0004-6361/201629754`](http://doi.org/10.1051/0004-6361/201629754)

(ref: dasyra16) Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016, A&A, 595, L7, doi: [`10.1051/0004-6361/201629689`](http://doi.org/10.1051/0004-6361/201629689)

(ref: davidson24) Davidson, J. R., Boizelle, B. D., Walsh, J. L., et al. 2024, ApJ, 972, 127, doi: [`10.3847/1538-4357/ad5be4`](http://doi.org/10.3847/1538-4357/ad5be4)

(ref: davies75) Davies, R. D., & Cummings, E. R. 1975, MNRAS, 170, 95, doi: [`10.1093/mnras/170.1.95`](http://doi.org/10.1093/mnras/170.1.95)

(ref: blok14) de Blok, W. J. G., Keating, K. M., Pisano, D. J., et al. 2014, A&A, 569, A68, doi: [`10.1051/0004-6361/201423880`](http://doi.org/10.1051/0004-6361/201423880)

(ref: dekoff00) de Koff, S., Best, P., Baum, S. A., et al. 2000, ApJS, 129, 33, doi: [`10.1086/313402`](http://doi.org/10.1086/313402)

(ref: devauc91) de Vaucouleurs, G., de Vaucouleurs, A., Corwin, Herold G., J., et al. 1991, Third Reference Catalogue of Bright Galaxies

(ref: dehghanian24) Dehghanian, M., Arav, N., Kriss, G. A., et al. 2024, ApJ, 972, 141, doi: [`10.3847/1538-4357/ad5ff4`](http://doi.org/10.3847/1538-4357/ad5ff4)

(ref: dimatteo03) Di Matteo, T., Allen, S. W., Fabian, A. C., Wilson, A. S., & Young, A. J. 2003, ApJ, 582, 133, doi: [`10.1086/344504`](http://doi.org/10.1086/344504)

(ref: doi13) Doi, A., Hada, K., Nagai, H., et al. 2013, in European Physical Journal Web of Conferences, Vol. 61, European Physical Journal Web of Conferences, 08008, doi: [`10.1051/epjconf/20136108008`](http://doi.org/10.1051/epjconf/20136108008)

(ref: dopita97) Dopita, M. A., Koratkar, A. P., Allen, M. G., et al. 1997, ApJ, 490, 202, doi: [`10.1086/304862`](http://doi.org/10.1086/304862)

(ref: draine03) Draine, B. T. 2003, ARA&A, 41, 241, doi: [`10.1146/annurev.astro.41.011802.094840`](http://doi.org/10.1146/annurev.astro.41.011802.094840)

(ref: draine14) Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172, doi: [`10.1088/0004-637X/780/2/172`](http://doi.org/10.1088/0004-637X/780/2/172)

(ref: dressel22) Dressel, L. 2022, in WFC3 Instrument Handbook for Cycle 30 v. 14, Vol. 14, 14

(ref: edge01) Edge, A. C. 2001, MNRAS, 328, 762, doi: [`10.1046/j.1365-8711.2001.04802.x`](http://doi.org/10.1046/j.1365-8711.2001.04802.x)

(ref: event19) EHT Collaboration, Akiyama, K., Alberdi, A., et al. 2019, ApJL, 875, L1, doi: [`10.3847/2041-8213/ab0ec7`](http://doi.org/10.3847/2041-8213/ab0ec7)

(ref: event21a) EHT Collaboration, Akiyama, K., Algaba, J. C., et al. 2021a, ApJL, 910, L12, doi: [`10.3847/2041-8213/abe71d`](http://doi.org/10.3847/2041-8213/abe71d)

(ref: event21b) EHT Collaboration, Akiyama, K., Algaba, J. C., et al. 2021b, ApJL, 910, L13, doi: [`10.3847/2041-8213/abe4de`](http://doi.org/10.3847/2041-8213/abe4de)

(ref: event21c) EHT MWL Science Working Group, Algaba, J. C., Anczarski, J., et al. 2021, ApJL, 911, L11, doi: [`10.3847/2041-8213/abef71`](http://doi.org/10.3847/2041-8213/abef71)

(ref: emmanoulopoulos13) Emmanoulopoulos, D., McHardy, I. M., & Papadakis, I. E. 2013, MNRAS, 433, 907, doi: [`10.1093/mnras/stt764`](http://doi.org/10.1093/mnras/stt764)

(ref: emsellem94) Emsellem, E., Monnet, G., & Bacon, R. 1994, A&A, 285, 723

(ref: fanaroff74) Fanaroff, B. L., & Riley, J. M. 1974, MNRAS, 167, 31P, doi: [`10.1093/mnras/167.1.31P`](http://doi.org/10.1093/mnras/167.1.31P)

(ref: ferland98) Ferland, G. J., Korista, K. T., Verner, D. A., et al. 1998, PASP, 110, 761, doi: [`10.1086/316190`](http://doi.org/10.1086/316190)

(ref: ferrarese96) Ferrarese, L., Ford, H. C., & Jaffe, W. 1996, ApJ, 470, 444, doi: [`10.1086/177876`](http://doi.org/10.1086/177876)

(ref: ferrarese06) Ferrarese, L., Côté, P., Jordán, A., et al. 2006, ApJS, 164, 334, doi: [`10.1086/501350`](http://doi.org/10.1086/501350)

(ref: fomalont14) Fomalont, E., van Kempen, T., Kneissl, R., et al. 2014, The Messenger, 155, 19

(ref: ford79) Ford, H. C., & Butcher, H. 1979, ApJS, 41, 147, doi: [`10.1086/190613`](http://doi.org/10.1086/190613)

(ref: ford94) Ford, H. C., Harms, R. J., Tsvetanov, Z. I., et al. 1994, ApJL, 435, L27, doi: [`10.1086/187586`](http://doi.org/10.1086/187586)

(ref: forman07) Forman, W., Jones, C., Churazov, E., et al. 2007, ApJ, 665, 1057, doi: [`10.1086/519480`](http://doi.org/10.1086/519480)

(ref: fournier24) Fournier, M., Grete, P., Brüggen, M., Glines, F. W., & O’Shea, B. W. 2024, arXiv e-prints, arXiv:2406.05044, doi: [`10.48550/arXiv.2406.05044`](http://doi.org/10.48550/arXiv.2406.05044)

(ref: francis20b) Francis, L., Johnstone, D., Herczeg, G., Hunter, T. R., & Harsono, D. 2020a, in Five Years After HL Tau: A New Era in Planet Formation (HLTAU2020), 23, doi: [`10.5281/zenodo.4300195`](http://doi.org/10.5281/zenodo.4300195)

(ref: francis20a) Francis, L., Johnstone, D., Herczeg, G., Hunter, T. R., & Harsono, D. 2020b, AJ, 160, 270, doi: [`10.3847/1538-3881/abbe1a`](http://doi.org/10.3847/1538-3881/abbe1a)

(ref: frith20) Frith, S. M., Bhartia, P. K., Oman, L. D., et al. 2020, Atmospheric Measurement Techniques, 13, 2733, doi: [`10.5194/amt-13-2733-2020`](http://doi.org/10.5194/amt-13-2733-2020)

(ref: ganguly23) Ganguly, S., Li, Y., Olivares, V., et al. 2023, Frontiers in Astronomy and Space Sciences, 10, 1138613, doi: [`10.3389/fspas.2023.1138613`](http://doi.org/10.3389/fspas.2023.1138613)

(ref: garciaburillo14) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125, doi: [`10.1051/0004-6361/201423843`](http://doi.org/10.1051/0004-6361/201423843)

(ref: garciaburillo16) Garcı́a-Burillo, S., Combes, F., Ramos Almeida, C., et al. 2016, ApJL, 823, L12, doi: [`10.3847/2041-8205/823/1/L12`](http://doi.org/10.3847/2041-8205/823/1/L12)

(ref: gaspari13) Gaspari, M., Ruszkowski, M., & Oh, S. P. 2013, MNRAS, 432, 3401, doi: [`10.1093/mnras/stt692`](http://doi.org/10.1093/mnras/stt692)

(ref: gaspari20) Gaspari, M., Tombesi, F., & Cappi, M. 2020, Nature Astronomy, 4, 10, doi: [`10.1038/s41550-019-0970-1`](http://doi.org/10.1038/s41550-019-0970-1)

(ref: gebhardt09) Gebhardt, K., & Thomas, J. 2009, ApJ, 700, 1690, doi: [`10.1088/0004-637X/700/2/1690`](http://doi.org/10.1088/0004-637X/700/2/1690)

(ref: gerin24) Gerin, M., Liszt, H., Pety, J., & Faure, A. 2024, A&A, 686, A49, doi: [`10.1051/0004-6361/202449152`](http://doi.org/10.1051/0004-6361/202449152)

(ref: giroletti12) Giroletti, M., Hada, K., Giovannini, G., et al. 2012, A&A, 538, L10, doi: [`10.1051/0004-6361/201218794`](http://doi.org/10.1051/0004-6361/201218794)

(ref: gnedin14) Gnedin, N. Y., & Draine, B. T. 2014, ApJ, 795, 37, doi: [`10.1088/0004-637X/795/1/37`](http://doi.org/10.1088/0004-637X/795/1/37)

(ref: godard2010) Godard, B., Falgarone, E., Gerin, M., Hily-Blant, P., & de Luca, M. 2010, A&A, 520, A20, doi: [`10.1051/0004-6361/201014283`](http://doi.org/10.1051/0004-6361/201014283)

(ref: goddi19) Goddi, C., Martı́-Vidal, I., Messias, H., et al. 2019, PASP, 131, 075003, doi: [`10.1088/1538-3873/ab136a`](http://doi.org/10.1088/1538-3873/ab136a)

(ref: goddi21) Goddi, C., Martı́-Vidal, I., Messias, H., et al. 2021, ApJL, 910, L14, doi: [`10.3847/2041-8213/abee6a`](http://doi.org/10.3847/2041-8213/abee6a)

(ref: grier16) Grier, C. J., Brandt, W. N., Hall, P. B., et al. 2016, ApJ, 824, 130, doi: [`10.3847/0004-637X/824/2/130`](http://doi.org/10.3847/0004-637X/824/2/130)

(ref: guver09) Güver, T., & Özel, F. 2009, MNRAS, 400, 2050, doi: [`10.1111/j.1365-2966.2009.15598.x`](http://doi.org/10.1111/j.1365-2966.2009.15598.x)

(ref: hess11) H. E. S. S. Collaboration, Abramowski, A., Acero, F., et al. 2011, A&A, 528, A143, doi: [`10.1051/0004-6361/201015381`](http://doi.org/10.1051/0004-6361/201015381)

(ref: hada17a) Hada, K. 2017, Galaxies, 5, 2, doi: [`10.3390/galaxies5010002`](http://doi.org/10.3390/galaxies5010002)

(ref: hada14) Hada, K., Giroletti, M., Kino, M., et al. 2014, ApJ, 788, 165, doi: [`10.1088/0004-637X/788/2/165`](http://doi.org/10.1088/0004-637X/788/2/165)

(ref: hada16) Hada, K., Kino, M., Doi, A., et al. 2016, ApJ, 817, 131, doi: [`10.3847/0004-637X/817/2/131`](http://doi.org/10.3847/0004-637X/817/2/131)

(ref: hada17b) Hada, K., Park, J. H., Kino, M., et al. 2017, PASJ, 69, 71, doi: [`10.1093/pasj/psx054`](http://doi.org/10.1093/pasj/psx054)

(ref: harms94) Harms, R. J., Ford, H. C., Tsvetanov, Z. I., et al. 1994, ApJL, 435, L35, doi: [`10.1086/187588`](http://doi.org/10.1086/187588)

(ref: heckman89) Heckman, T. M., Baum, S. A., van Breugel, W. J. M., & McCarthy, P. 1989, ApJ, 338, 48, doi: [`10.1086/167181`](http://doi.org/10.1086/167181)

(ref: heckman14) Heckman, T. M., & Best, P. N. 2014, ARA&A, 52, 589, doi: [`10.1146/annurev-astro-081913-035722`](http://doi.org/10.1146/annurev-astro-081913-035722)

(ref: hennebelle13) Hennebelle, P. 2013, A&A, 556, A153, doi: [`10.1051/0004-6361/201321292`](http://doi.org/10.1051/0004-6361/201321292)

(ref: herrera20) Herrera-Camus, R., Janssen, A., Sturm, E., et al. 2020, A&A, 635, A47, doi: [`10.1051/0004-6361/201936434`](http://doi.org/10.1051/0004-6361/201936434)

(ref: ho97) Ho, L. C., Filippenko, A. V., & Sargent, W. L. W. 1997, ApJS, 112, 315, doi: [`10.1086/313041`](http://doi.org/10.1086/313041)

(ref: hunter18) Hunter, T., Phillips, N., Broguiére, D., & Gonzalez, J. 2018, NRAO

(ref: immer24) Immer, K., et al. 2024,

(ref: inayoshi20) Inayoshi, K., Ichikawa, K., & Ho, L. C. 2020, ApJ, 894, 141, doi: [`10.3847/1538-4357/ab8569`](http://doi.org/10.3847/1538-4357/ab8569)

(ref: indebetouw20) Indebetouw, R., Wong, T., Chen, C. H. R., et al. 2020, ApJ, 888, 56, doi: [`10.3847/1538-4357/ab5db7`](http://doi.org/10.3847/1538-4357/ab5db7)

(ref: israel92) Israel, F. P. 1992, A&A, 265, 487

(ref: jaffe87) Jaffe, W. 1987, A&A, 171, 378

(ref: kameno14) Kameno, S. 2014, , Tech. rep., JAO/NAOJ

(ref: kameno20) Kameno, S., Sawada-Satoh, S., Impellizzeri, C. M. V., et al. 2020, ApJ, 895, 73, doi: [`10.3847/1538-4357/ab8bd6`](http://doi.org/10.3847/1538-4357/ab8bd6)

(ref: kim18) Kim, J. Y., Krichbaum, T. P., Lu, R. S., et al. 2018, A&A, 616, A188, doi: [`10.1051/0004-6361/201832921`](http://doi.org/10.1051/0004-6361/201832921)

(ref: klitsch19) Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2019, MNRAS, 490, 1220, doi: [`10.1093/mnras/stz2660`](http://doi.org/10.1093/mnras/stz2660)

(ref: koch15) Koch, E. W., & Rosolowsky, E. W. 2015, MNRAS, 452, 3435, doi: [`10.1093/mnras/stv1521`](http://doi.org/10.1093/mnras/stv1521)

(ref: kokusho19) Kokusho, T., Kaneda, H., Bureau, M., et al. 2019, A&A, 622, A87, doi: [`10.1051/0004-6361/201833911`](http://doi.org/10.1051/0004-6361/201833911)

(ref: komugi22) Komugi, S., Toba, Y., Matsuoka, Y., Saito, T., & Yamashita, T. 2022, ApJ, 930, 3, doi: [`10.3847/1538-4357/ac616e`](http://doi.org/10.3847/1538-4357/ac616e)

(ref: konyves20) Könyves, V., André, P., Arzoumanian, D., et al. 2020, A&A, 635, A34, doi: [`10.1051/0004-6361/201834753`](http://doi.org/10.1051/0004-6361/201834753)

(ref: kuo14) Kuo, C. Y., Asada, K., Rao, R., et al. 2014, ApJL, 783, L33, doi: [`10.1088/2041-8205/783/2/L33`](http://doi.org/10.1088/2041-8205/783/2/L33)

(ref: leroy21) Leroy, A. K., Hughes, A., Liu, D., et al. 2021, ApJS, 255, 19, doi: [`10.3847/1538-4365/abec80`](http://doi.org/10.3847/1538-4365/abec80)

(ref: liepold23) Liepold, E. R., Ma, C.-P., & Walsh, J. L. 2023, ApJL, 945, L35, doi: [`10.3847/2041-8213/acbbcf`](http://doi.org/10.3847/2041-8213/acbbcf)

(ref: lim17) Lim, J., Dinh-V-Trung, Vrtilek, J., David, L. P., & Forman, W. 2017, ApJ, 850, 31, doi: [`10.3847/1538-4357/aa9275`](http://doi.org/10.3847/1538-4357/aa9275)

(ref: liszt19) Liszt, H., Gerin, M., & Grenier, I. 2019, A&A, 627, A95, doi: [`10.1051/0004-6361/201935436`](http://doi.org/10.1051/0004-6361/201935436)

(ref: liszt04) Liszt, H., & Lucas, R. 2004, A&A, 428, 445, doi: [`10.1051/0004-6361:20041650`](http://doi.org/10.1051/0004-6361:20041650)

(ref: liszt98) Liszt, H. S., & Lucas, R. 1998, A&A, 339, 561

(ref: liszt12) Liszt, H. S., & Pety, J. 2012, A&A, 541, A58, doi: [`10.1051/0004-6361/201218771`](http://doi.org/10.1051/0004-6361/201218771)

(ref: longobardi15) Longobardi, A., Arnaboldi, M., Gerhard, O., & Mihos, J. C. 2015, A&A, 579, L3, doi: [`10.1051/0004-6361/201526282`](http://doi.org/10.1051/0004-6361/201526282)

(ref: lu23) Lu, R.-S., Asada, K., Krichbaum, T. P., et al. 2023, Nature, 616, 686, doi: [`10.1038/s41586-023-05843-w`](http://doi.org/10.1038/s41586-023-05843-w)

(ref: macchetto97) Macchetto, F., Marconi, A., Axon, D. J., et al. 1997, ApJ, 489, 579, doi: [`10.1086/304823`](http://doi.org/10.1086/304823)

(ref: madrid07) Madrid, J. P., Sparks, W. B., Harris, D. E., et al. 2007, Ap&SS, 311, 329, doi: [`10.1007/s10509-007-9528-2`](http://doi.org/10.1007/s10509-007-9528-2)

(ref: Mangum2015) Mangum, J., & Shirley, Y. 2015, Publications of the Astronomical Society of the Pacific, 127, doi: [`10.1086/680323`](http://doi.org/10.1086/680323)

(ref: margulis89) Margulis, M., & Snell, R. L. 1989, ApJ, 343, 779, doi: [`10.1086/167749`](http://doi.org/10.1086/167749)

(ref: marshall02) Marshall, H. L., Miller, B. P., Davis, D. S., et al. 2002, ApJ, 564, 683, doi: [`10.1086/324396`](http://doi.org/10.1086/324396)

(ref: mathews03) Mathews, W. G., & Brighenti, F. 2003, ARA&A, 41, 191, doi: [`10.1146/annurev.astro.41.090401.094542`](http://doi.org/10.1146/annurev.astro.41.090401.094542)

(ref: matsushita17) Matsushita, S., Asaki, Y., Fomalont, E. B., et al. 2017, PASP, 129, 035004, doi: [`10.1088/1538-3873/aa5787`](http://doi.org/10.1088/1538-3873/aa5787)

(ref: maud23) Maud, L. T., Pérez-Sánchez, A. F., Asaki, Y., et al. 2023, arXiv e-prints, arXiv:2304.08318, doi: [`10.48550/arXiv.2304.08318`](http://doi.org/10.48550/arXiv.2304.08318)

(ref: mcmullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: meena10) Meena, G. S. 2010, Journal of Earth System Science, 119, 249, doi: [`10.1007/s12040-010-0024-7`](http://doi.org/10.1007/s12040-010-0024-7)

(ref: misawa14) Misawa, T., Charlton, J. C., & Eracleous, M. 2014, ApJ, 792, 77, doi: [`10.1088/0004-637X/792/1/77`](http://doi.org/10.1088/0004-637X/792/1/77)

(ref: misawa19) Misawa, T., Eracleous, M., Charlton, J. C., & Kashikawa, N. 2019, ApJ, 870, 68, doi: [`10.3847/1538-4357/aaf0fe`](http://doi.org/10.3847/1538-4357/aaf0fe)

(ref: mould00) Mould, J. R., Huchra, J. P., Freedman, W. L., et al. 2000, ApJ, 529, 786, doi: [`10.1086/308304`](http://doi.org/10.1086/308304)

(ref: muller05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: nagai19) Nagai, H., Onishi, K., Kawakatu, N., et al. 2019, ApJ, 883, 193, doi: [`10.3847/1538-4357/ab3e6e`](http://doi.org/10.3847/1538-4357/ab3e6e)

(ref: ocana10) Ocaña Flaquer, B., Leon, S., Combes, F., & Lim, J. 2010, A&A, 518, A9, doi: [`10.1051/0004-6361/200913392`](http://doi.org/10.1051/0004-6361/200913392)

(ref: olivares25) Olivares, V., Picquenot, A., Su, Y., et al. 2025, Nature Astronomy, 9, 449, doi: [`10.1038/s41550-024-02473-8`](http://doi.org/10.1038/s41550-024-02473-8)

(ref: Olivares2019) Olivares, V., Salome, P., Combes, F., et al. 2019, A&A, 631, A22, doi: [`10.1051/0004-6361/201935350`](http://doi.org/10.1051/0004-6361/201935350)

(ref: oosterloo24) Oosterloo, T., Morganti, R., & Murthy, S. 2024, Nature Astronomy, 8, 256, doi: [`10.1038/s41550-023-02138-y`](http://doi.org/10.1038/s41550-023-02138-y)

(ref: osorno23) Osorno, J., Nagar, N., Richtler, T., et al. 2023, A&A, 679, A37, doi: [`10.1051/0004-6361/202346549`](http://doi.org/10.1051/0004-6361/202346549)

(ref: paine18) Paine, S. 2018, , 10.0, Zenodo Zenodo, doi: [`10.5281/zenodo.1193771`](http://doi.org/10.5281/zenodo.1193771)

(ref: panopoulou16) Panopoulou, G. V., Psaradaki, I., & Tassis, K. 2016, MNRAS, 462, 1517, doi: [`10.1093/mnras/stw1678`](http://doi.org/10.1093/mnras/stw1678)

(ref: pardo24) Pardo, J. 2024, , <https://www.eso.org/sci/facilities/alma/developmentstudies/20240703154158_20240703_FINAL_ESO_19-25417-HNE_REPORT-merged-1.pdf> ESO

(ref: pardo01) Pardo, J., Cernicharo, J., & Serabyn, E. 2001, IEEE Transactions on Antennas and Propagation, 49, 1683, doi: [`10.1109/8.982447`](http://doi.org/10.1109/8.982447)

(ref: pardo19) Pardo, J. R. 2019, in ALMA Development Workshop, 36, doi: [`10.5281/zenodo.3240379`](http://doi.org/10.5281/zenodo.3240379)

(ref: park19) Park, J., Hada, K., Kino, M., et al. 2019, ApJ, 887, 147, doi: [`10.3847/1538-4357/ab5584`](http://doi.org/10.3847/1538-4357/ab5584)

(ref: pasetto21) Pasetto, A., Carrasco-González, C., Gómez, J. L., et al. 2021, ApJL, 923, L5, doi: [`10.3847/2041-8213/ac3a88`](http://doi.org/10.3847/2041-8213/ac3a88)

(ref: pasini21) Pasini, T., Finoguenov, A., Brüggen, M., et al. 2021, MNRAS, 505, 2628, doi: [`10.1093/mnras/stab1451`](http://doi.org/10.1093/mnras/stab1451)

(ref: peng02) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266, doi: [`10.1086/340952`](http://doi.org/10.1086/340952)

(ref: perlman01) Perlman, E. S., Sparks, W. B., Radomski, J., et al. 2001, ApJL, 561, L51, doi: [`10.1086/324515`](http://doi.org/10.1086/324515)

(ref: perlman07) Perlman, E. S., Mason, R. E., Packham, C., et al. 2007, ApJ, 663, 808, doi: [`10.1086/518781`](http://doi.org/10.1086/518781)

(ref: pickett98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883, doi: [`10.1016/S0022-4073(98)00091-0`](http://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: pineda10) Pineda, J. L., Goldsmith, P. F., Chapman, N., et al. 2010, ApJ, 721, 686, doi: [`10.1088/0004-637X/721/1/686`](http://doi.org/10.1088/0004-637X/721/1/686)

(ref: planck2016) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13, doi: [`10.1051/0004-6361/201525830`](http://doi.org/10.1051/0004-6361/201525830)

(ref: pogge00) Pogge, R. W., Maoz, D., Ho, L. C., & Eracleous, M. 2000, ApJ, 532, 323, doi: [`10.1086/308567`](http://doi.org/10.1086/308567)

(ref: plotdig) Porbital. 2024, <https://plotdigitizer.com>

(ref: prandoni10) Prandoni, I., Laing, R. A., de Ruiter, H. R., & Parma, P. 2010, A&A, 523, A38, doi: [`10.1051/0004-6361/201015456`](http://doi.org/10.1051/0004-6361/201015456)

(ref: prieto16) Prieto, M. A., Fernández-Ontiveros, J. A., Markoff, S., Espada, D., & González-Martı́n, O. 2016, MNRAS, 457, 3801, doi: [`10.1093/mnras/stw166`](http://doi.org/10.1093/mnras/stw166)

(ref: prieto21) Prieto, M. A., Nadolny, J., Fernández-Ontiveros, J. A., & Mezcua, M. 2021, MNRAS, 506, 562, doi: [`10.1093/mnras/stab1704`](http://doi.org/10.1093/mnras/stab1704)

(ref: privon24) Privon, G., et al. 2024, ALMA Proposer’s Guide, ALMA Doc. 11.2, ver. 1.0, doi: [`10.5281/zenodo.4511961`](http://doi.org/10.5281/zenodo.4511961)

(ref: pulido18) Pulido, F. A., McNamara, B. R., Edge, A. C., et al. 2018, ApJ, 853, 177, doi: [`10.3847/1538-4357/aaa54b`](http://doi.org/10.3847/1538-4357/aaa54b)

(ref: rappengluck14) Rappenglück, B., Ackermann, L., Alvarez, S., et al. 2014, Atmospheric Chemistry and Physics, 14, 4909, doi: [`10.5194/acp-14-4909-2014`](http://doi.org/10.5194/acp-14-4909-2014)

(ref: ray24) Ray, M., & Hwang, C.-Y. 2024, ApJ, 974, 5, doi: [`10.3847/1538-4357/ad7090`](http://doi.org/10.3847/1538-4357/ad7090)

(ref: reid89) Reid, M. J., Biretta, J. A., Junor, W., Muxlow, T. W. B., & Spencer, R. E. 1989, ApJ, 336, 112, doi: [`10.1086/166998`](http://doi.org/10.1086/166998)

(ref: richards22) Richards, A. M. S., Moravec, E., Etoka, S., et al. 2022, arXiv e-prints, arXiv:2207.05591, doi: [`10.48550/arXiv.2207.05591`](http://doi.org/10.48550/arXiv.2207.05591)

(ref: riffel20) Riffel, R. A., Storchi-Bergmann, T., Zakamska, N. L., & Riffel, R. 2020, MNRAS, 496, 4857, doi: [`10.1093/mnras/staa1922`](http://doi.org/10.1093/mnras/staa1922)

(ref: rivera16) Rivera-Ingraham, A., Ristorcelli, I., Juvela, M., et al. 2016, A&A, 591, A90, doi: [`10.1051/0004-6361/201526263`](http://doi.org/10.1051/0004-6361/201526263)

(ref: roman10) Roman-Duval, J., Jackson, J. M., Heyer, M., Rathborne, J., & Simon, R. 2010, ApJ, 723, 492, doi: [`10.1088/0004-637X/723/1/492`](http://doi.org/10.1088/0004-637X/723/1/492)

(ref: rose19b) Rose, T., Edge, A. C., Combes, F., et al. 2019a, MNRAS, 489, 349, doi: [`10.1093/mnras/stz2138`](http://doi.org/10.1093/mnras/stz2138)

(ref: rose19a) Rose, T., Edge, A. C., Combes, F., et al. 2019b, MNRAS, 485, 229, doi: [`10.1093/mnras/stz406`](http://doi.org/10.1093/mnras/stz406)

(ref: rose20) Rose, T., Edge, A. C., Combes, F., et al. 2020, MNRAS, 496, 364, doi: [`10.1093/mnras/staa1474`](http://doi.org/10.1093/mnras/staa1474)

(ref: rose24) Rose, T., McNamara, B. R., Combes, F., et al. 2024, MNRAS, 533, 771, doi: [`10.1093/mnras/stae1831`](http://doi.org/10.1093/mnras/stae1831)

(ref: rosolowsky21) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218, doi: [`10.1093/mnras/stab085`](http://doi.org/10.1093/mnras/stab085)

(ref: ruffa22) Ruffa, I., Prandoni, I., Davis, T. A., et al. 2022, MNRAS, 510, 4485, doi: [`10.1093/mnras/stab3541`](http://doi.org/10.1093/mnras/stab3541)

(ref: ruffa19) Ruffa, I., Prandoni, I., Laing, R. A., et al. 2019, MNRAS, 484, 4239, doi: [`10.1093/mnras/stz255`](http://doi.org/10.1093/mnras/stz255)

(ref: rugel18) Rugel, M. R., Beuther, H., Bihr, S., et al. 2018, A&A, 618, A159, doi: [`10.1051/0004-6361/201731872`](http://doi.org/10.1051/0004-6361/201731872)

(ref: ryon22) Ryon, J. E. 2022, in ACS Instrument Handbook for Cycle 30 v. 21.0, Vol. 21, 21

(ref: sabra03) Sabra, B. M., Shields, J. C., Ho, L. C., Barth, A. J., & Filippenko, A. V. 2003, ApJ, 584, 164, doi: [`10.1086/345664`](http://doi.org/10.1086/345664)

(ref: sadler08) Sadler, E. M., Ricci, R., Ekers, R. D., et al. 2008, MNRAS, 385, 1656, doi: [`10.1111/j.1365-2966.2008.12955.x`](http://doi.org/10.1111/j.1365-2966.2008.12955.x)

(ref: safranek17) Safranek-Shrader, C., Krumholz, M. R., Kim, C.-G., et al. 2017, MNRAS, 465, 885, doi: [`10.1093/mnras/stw2647`](http://doi.org/10.1093/mnras/stw2647)

(ref: salome03) Salomé, P., & Combes, F. 2003, A&A, 412, 657, doi: [`10.1051/0004-6361:20031438`](http://doi.org/10.1051/0004-6361:20031438)

(ref: salome08) Salomé, P., & Combes, F. 2008, A&A, 489, 101, doi: [`10.1051/0004-6361:200810262`](http://doi.org/10.1051/0004-6361:200810262)

(ref: sancisi08) Sancisi, R., Fraternali, F., Oosterloo, T., & van der Hulst, T. 2008, A&ARv, 15, 189, doi: [`10.1007/s00159-008-0010-0`](http://doi.org/10.1007/s00159-008-0010-0)

(ref: Sandstrom2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: sankrit99) Sankrit, R., Sembach, K. R., & Canizares, C. R. 1999, ApJ, 527, 733, doi: [`10.1086/308115`](http://doi.org/10.1086/308115)

(ref: saripalli12) Saripalli, L. 2012, AJ, 144, 85, doi: [`10.1088/0004-6256/144/3/85`](http://doi.org/10.1088/0004-6256/144/3/85)

(ref: scoville12) Scoville, N. Z. 2013, in Secular Evolution of Galaxies, ed. J. Falcón-Barroso & J. H. Knapen (Cambridge University Press), 491, doi: [`10.48550/arXiv.1210.6990`](http://doi.org/10.48550/arXiv.1210.6990)

(ref: shangguan20) Shangguan, J., Ho, L. C., Bauer, F. E., Wang, R., & Treister, E. 2020, ApJS, 247, 15, doi: [`10.3847/1538-4365/ab5db2`](http://doi.org/10.3847/1538-4365/ab5db2)

(ref: shetty12) Shetty, R., Beaumont, C. N., Burton, M. G., Kelly, B. C., & Klessen, R. S. 2012, MNRAS, 425, 720, doi: [`10.1111/j.1365-2966.2012.21588.x`](http://doi.org/10.1111/j.1365-2966.2012.21588.x)

(ref: shi07) Shi, Y., Rieke, G. H., Hines, D. C., Gordon, K. D., & Egami, E. 2007, ApJ, 655, 781, doi: [`10.1086/510188`](http://doi.org/10.1086/510188)

(ref: shibata01) Shibata, R., Matsushita, K., Yamasaki, N. Y., et al. 2001, ApJ, 549, 228, doi: [`10.1086/319075`](http://doi.org/10.1086/319075)

(ref: simionescu18) Simionescu, A., Tremblay, G., Werner, N., et al. 2018, MNRAS, 475, 3004, doi: [`10.1093/mnras/sty047`](http://doi.org/10.1093/mnras/sty047)

(ref: simon24) Simon, D. A., Cappellari, M., & Hartke, J. 2024, MNRAS, 527, 2341, doi: [`10.1093/mnras/stad3309`](http://doi.org/10.1093/mnras/stad3309)

(ref: smith21) Smith, M. D., Bureau, M., Davis, T. A., et al. 2021, MNRAS, 500, 1933, doi: [`10.1093/mnras/staa3274`](http://doi.org/10.1093/mnras/staa3274)

(ref: snow06) Snow, T. P., & McCall, B. J. 2006, ARA&A, 44, 367, doi: [`10.1146/annurev.astro.43.072103.150624`](http://doi.org/10.1146/annurev.astro.43.072103.150624)

(ref: sofia04) Sofia, U. J., Lauroesch, J. T., Meyer, D. M., & Cartledge, S. I. B. 2004, ApJ, 605, 272, doi: [`10.1086/382592`](http://doi.org/10.1086/382592)

(ref: solomon87) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730, doi: [`10.1086/165493`](http://doi.org/10.1086/165493)

(ref: sparks04) Sparks, W. B., Donahue, M., Jordán, A., Ferrarese, L., & Côté, P. 2004, ApJ, 607, 294, doi: [`10.1086/383189`](http://doi.org/10.1086/383189)

(ref: sparks93) Sparks, W. B., Ford, H. C., & Kinney, A. L. 1993, ApJ, 413, 531, doi: [`10.1086/173022`](http://doi.org/10.1086/173022)

(ref: sparks09) Sparks, W. B., Pringle, J. E., Donahue, M., et al. 2009, ApJL, 704, L20, doi: [`10.1088/0004-637X/704/1/L20`](http://doi.org/10.1088/0004-637X/704/1/L20)

(ref: stone16) Stone, M., Veilleux, S., Meléndez, M., et al. 2016, ApJ, 826, 111, doi: [`10.3847/0004-637X/826/2/111`](http://doi.org/10.3847/0004-637X/826/2/111)

(ref: tadhunter08) Tadhunter, C. 2008, New A Rev., 52, 227, doi: [`10.1016/j.newar.2008.06.004`](http://doi.org/10.1016/j.newar.2008.06.004)

(ref: tadhunter24) Tadhunter, C., Oosterloo, T., Morganti, R., et al. 2024, MNRAS, 532, 4463, doi: [`10.1093/mnras/stae1745`](http://doi.org/10.1093/mnras/stae1745)

(ref: tan08) Tan, J. C., Beuther, H., Walter, F., & Blackman, E. G. 2008, ApJ, 689, 775, doi: [`10.1086/592592`](http://doi.org/10.1086/592592)

(ref: taylor20) Taylor, T. R., Chao, C.-T., & Chiou, J.-S. 2020, Applied Sciences, 10, doi: [`10.3390/app10113952`](http://doi.org/10.3390/app10113952)

(ref: temi18) Temi, P., Amblard, A., Gitti, M., et al. 2018, ApJ, 858, 17, doi: [`10.3847/1538-4357/aab9b0`](http://doi.org/10.3847/1538-4357/aab9b0)

(ref: tremblay18) Tremblay, G. R., Combes, F., Oonk, J. B. R., et al. 2018, ApJ, 865, 13, doi: [`10.3847/1538-4357/aad6dd`](http://doi.org/10.3847/1538-4357/aad6dd)

(ref: trump11) Trump, J. R., Impey, C. D., Kelly, B. C., et al. 2011, ApJ, 733, 60, doi: [`10.1088/0004-637X/733/1/60`](http://doi.org/10.1088/0004-637X/733/1/60)

(ref: tsukui23) Tsukui, T., Iguchi, S., Mitsuhashi, I., & Tadaki, K. 2023, Journal of Astronomical Telescopes, Instruments, and Systems, 9, 018001, doi: [`10.1117/1.JATIS.9.1.018001`](http://doi.org/10.1117/1.JATIS.9.1.018001)

(ref: tsvetanov99a) Tsvetanov, Z. I., Allen, M. G., Ford, H. C., & Harms, R. J. 1999a, in The Radio Galaxy Messier 87, ed. H.-J. Röser & K. Meisenheimer, Vol. 530, 301, doi: [`10.1007/BFb0106441`](http://doi.org/10.1007/BFb0106441)

(ref: tsvetanov99b) Tsvetanov, Z. I., Hartig, G. F., Ford, H. C., et al. 1999b, in The Radio Galaxy Messier 87, ed. H.-J. Röser & K. Meisenheimer, Vol. 530, 307, doi: [`10.1007/BFb0106442`](http://doi.org/10.1007/BFb0106442)

(ref: usero19) Usero, A., et al. 2019,

(ref: utomo15) Utomo, D., Blitz, L., Davis, T., et al. 2015, ApJ, 803, 16, doi: [`10.1088/0004-637X/803/1/16`](http://doi.org/10.1088/0004-637X/803/1/16)

(ref: van07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: vankempen16) van Kempen, T. A., Hogerheijde, M. R., van Dishoeck, E. F., et al. 2016, A&A, 587, A17, doi: [`10.1051/0004-6361/201424725`](http://doi.org/10.1051/0004-6361/201424725)

(ref: veilleux13) Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, ApJ, 776, 27, doi: [`10.1088/0004-637X/776/1/27`](http://doi.org/10.1088/0004-637X/776/1/27)

(ref: viaene17) Viaene, S., Sarzi, M., Baes, M., Fritz, J., & Puerari, I. 2017, MNRAS, 472, 1286, doi: [`10.1093/mnras/stx1781`](http://doi.org/10.1093/mnras/stx1781)

(ref: walker18) Walker, R. C., Hardee, P. E., Davies, F. B., Ly, C., & Junor, W. 2018, ApJ, 855, 128, doi: [`10.3847/1538-4357/aaafcc`](http://doi.org/10.3847/1538-4357/aaafcc)

(ref: walsh13) Walsh, J. L., Barth, A. J., Ho, L. C., & Sarzi, M. 2013, ApJ, 770, 86, doi: [`10.1088/0004-637X/770/2/86`](http://doi.org/10.1088/0004-637X/770/2/86)

(ref: wilson02) Wilson, A. S., & Yang, Y. 2002, ApJ, 568, 133, doi: [`10.1086/338887`](http://doi.org/10.1086/338887)

(ref: wong22) Wong, T., Oudshoorn, L., Sofovich, E., et al. 2022, ApJ, 932, 47, doi: [`10.3847/1538-4357/ac723a`](http://doi.org/10.3847/1538-4357/ac723a)

(ref: xilouris04) Xilouris, E. M., Madden, S. C., Galliano, F., Vigroux, L., & Sauvage, M. 2004, A&A, 416, 41, doi: [`10.1051/0004-6361:20034020`](http://doi.org/10.1051/0004-6361:20034020)

(ref: yuan14) Yuan, F., & Narayan, R. 2014, ARA&A, 52, 529, doi: [`10.1146/annurev-astro-082812-141003`](http://doi.org/10.1146/annurev-astro-082812-141003)

(ref: yusef22) Yusef-Zadeh, F., Arendt, R. G., Wardle, M., et al. 2022, ApJL, 925, L18, doi: [`10.3847/2041-8213/ac4802`](http://doi.org/10.3847/2041-8213/ac4802)

(ref: zhang20) Zhang, H.-M., Wang, Z.-J., Zhang, J., et al. 2020, PASJ, 72, 44, doi: [`10.1093/pasj/psaa029`](http://doi.org/10.1093/pasj/psaa029)

(ref: zhang14) Zhang, Q., Ye, J., Zhang, S., & Han, F. 2018, Journal of Sensors, 2018, 4909, doi: [`10.1155/2018/3428303`](http://doi.org/10.1155/2018/3428303)

[^1]: (cite: ray24) use both EBs and find a complex response that is qualitatively very similar to the peak spectrum in Figure [9](#fig:contabs). Their fitted absorption-line components have $\ensuremath{v_\mathrm{LOS}}-\ensuremath{v_\mathrm{sys}}= -527$ km s$^{-1}$ and $-$74 km s$^{-1}$ with $\sigma \sim 230$ km s$^{-1}$ and $\sim$46 km s$^{-1}$, respectively.

[^2]: In frequency space, Hanning smoothing operates as a convolution of the FDM data before on-line channel averaging. The triangular kernel consists of three channels with central and side amplitudes of 0.50 and 0.25, respectively. Finely-binned FDM data have frequency resolutions up to 2$\times$ larger due to Hanning smoothing. For those with the narrowest $\Delta\nu_\mathrm{obs} < 1$ MHz, the intrinsic line widths are $\sim$7% lower than the blurred values. For those with $\Delta\nu_\mathrm{obs}>5$ MHz, there is no change in frequency resolution.

[^3]: Obtained from Splatalogue: <https://splatalogue.online/#/advanced>

[^4]: Not all cool-core galaxies host CNDs that could contribute to the global $L_\mathrm{H\alpha}$. The atomic CND in M87 contributes 20$-$25% of its global $L_\mathrm{H\alpha}$ (cite: sparks93; walsh13; osorno23).

[^5]: Note that these atomic gas velocities were shifted upwards by up to $\sim$60 km s$^{-1}$ to match Galactic atomic absorption-line centroids (e.g., for S I or N II) with the primary H I centroid at $cz_\mathrm{obs} \sim -10$ km s$^{-1}$ (cite: davies75). While higher spectral resolution UV/optical data exist (cite: sankrit99), they do not have sufficient sensitivity to confirm the absorption-line velocity offset from CO and better characterize the line width.

[^6]: Identified using the Splatalogue database for astronomical spectroscopy <https://splatalogue.online/>

[^7]: We tentatively detect a similar small shift in continuum centroid (but not peak location) across a spw in both the X5 and Xa1 continuum cubes shown in Figure [9](#fig:contabs). We attribute this to residual frequency-dependent phase offsets that had not been fully removed during self-calibration, giving the appearance of a slight spatial shift of the continuum emission. This may also contribute to the very small velocity gradient shift in the CO(1$-$0) absorption-line centroid shown in Figure [4](#fig:colineabsfit).

</paper>

Write the methods card for this paper.