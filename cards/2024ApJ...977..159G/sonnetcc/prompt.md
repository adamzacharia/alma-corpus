# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977..159G\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977..159G",
 "title": "Complex Kinematics of Nebular Gas in Active Galaxies Centered in Cooling X-Ray Atmospheres",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Gingras, Marie-Joëlle",
 "n_authors": 9,
 "arxiv_id": "2404.02212",
 "doi": "10.3847/1538-4357/ad822a",
 "alma_projects_linked_by_archive": [
  "2011.0.00374.S",
  "2012.1.00837.S",
  "2015.1.00598.S",
  "2016.1.01269.S"
 ]
}
```

Paper text:
<paper>
# Complex Velocity Structure of Nebular Gas in Active Galaxies Centred in Cooling X-ray Atmospheres

## Abstract

\[OII\] emission maps obtained with the Keck Cosmic Web Imager (KCWI) are presented for four galaxies centered in cooling X-ray cluster atmospheres. Nebular emission extending tens of kpc is found in systems covering a broad range of atmospheric cooling rates, cluster masses, and dynamical states. Abell 262’s central galaxy hosts a kpc-scale disk. The nebular gas in RXJ0820.9+0752 is offset and redshifted with respect to the central galaxy by $10-20$ kpc and 150 km s$^{-1}$, respectively. The nebular gases in PKS 0745-191 and Abell 1835 are being churned to higher velocity dispersion by X-ray bubbles and jets. The churned gas is enveloped by larger scale, lower velocity dispersion (quiescent) nebular emission. The mean line-of-sight speeds of the churned gas, quiescent gas, and the central galaxy each differ by up to $\sim 150$ km s$^{-1}$; nebular speeds upward of $800$ km s$^{-1}$ are found. Gases with outwardly-rising speeds upward of several hundred km s$^{-1}$ are consistent with being advected behind and being lifted by the rising bubbles. The peculiar motion between the galaxy, nebular gas, and perhaps the hot atmosphere from which it presumably condensed is affecting the bubble dynamics, and may strongly affect thermally unstable cooling, the dispersal of jet energy, and the angular momentum of gas accreting onto the galaxies and their nuclear black holes.

# Introduction

Clusters of galaxies host the largest and most luminous elliptical galaxies at their centres. These galaxies are often referred to as Brightest Cluster Galaxies (BCGs) or central dominant galaxies. They also lie at the bases of hot X-ray atmospheres with luminosities of 10$^{43}-10^{45}$ erg s$^{-1}$ and temperatures between 10$^7$ to 10$^8$ K. Gas densities surrounding central galaxies are often upwards of $10^{-2}$ cm$^{-3}$. At these densities atmospheres are expected to cool and condense into molecular clouds and form stars (cite: Fabian1994; Cavagnolo2008; Rafferty2008). Star formation is observed in central galaxies, as in the systems studied here; however, the star formation rates are more than an order of magnitude lower than those expected by unimpeded cooling (cite: Fabian1994; Peterson2006). This discrepancy between cooling models and the products of cooling suggests that one or more heating mechanisms are suppressing cooling.

Energetic feedback from active galactic nuclei (AGN) is a likely heating mechanism due to the prevalence of radio jets with sufficient power to compensate for radiative cooling losses (cite: McNamara2007; McNamara2012). AGN-driven jets and radio lobes also displace $10^7$ to $10^{10}$ M$_{\odot}$ of hot gas surrounding them, carving X-ray cavities or bubbles that rise buoyantly through the atmosphere (cite: Birzan2004; Rafferty2006; Pope2010). Several processes, including enthalpy released by rising bubbles (cite: McNamara2007), turbulence (cite: Scannapieco2008; Gaspari2012), shocks (cite: Heinz1998; David2001), sound waves (cite: Fabian2003a; Ruszkowski2004a; Ruszkowski2004b; Voit2005; Nulsen2013) and cosmic rays (cite: Ruszkowski2008; Guo2008; Mathews2008), contribute to the propagation and thermalization of energy from AGN feedback throughout hot atmospheres (cite: Donahue2022).

A spectrum of gas phases is observed surrounding central galaxies, including cold molecular gas with temperatures of a few tens of Kelvins (cite: Edge2001; SC2003), warm molecular gas with temperatures less than 400 K (cite: Johnstone2007), warm ionized nebular gas with $\sim10^4$ K temperatures, coronal gas at $10^6$ K (cite: Canning2011), and hot $10^7-10^8$ K X-ray emitting gas. The discovery of bright nebular line emission surrounding galaxies and often extending tens of kpc into the bright X-ray atmospheres was the earliest evidence of atmospheric cooling (cite: Heckman1981; Hu1985; Heckman1989; Crawford1999; Hatch2007; McDonald2010; Fabian1977). The brightest systems are associated with $10^9-10^{11}~\rm M_\odot$ of molecular gas, often associated with star formation at rates of tens of solar masses per year (cite: Rafferty2008; Fogarty2019; Russell2019; Olivares2019).

Observations of gas cooling through all phases place strong constraints on thermally unstable cooling models. Bright nebular emission and star formation in central cluster galaxies and giant ellipticals are generally associated with systems with atmospheric cooling times lying below 1 Gyr. Other cooling indicators include central entropy lying below 30 keV cm$^2$ (cite: Cavagnolo2008; Rafferty2008) and ratios of cooling time to free-fall time (t$_{\textrm{cool}}$/t$_{\textrm{ff}}$) below $\sim 35$. These thresholds are believed to be closely related to the onset of thermal instabilities (cite: Nulsen1986; Pizzolato2005; McCourt2012; Sharma2012; Gaspari2012; Voit2015; McNamara2016; Hogan2017; Pulido2018; Donahue2022). Thermally unstable cooling from hot atmospheres fuels star formation and could provide a continual fuel source to maintain the feedback cycle.

In addition to heating the atmosphere, buoyantly rising radio bubbles and jets may enhance thermally unstable cooling by lifting cooling parcels of gas to higher altitudes (cite: Revaz2008; McNamara2016; Donahue2022). In this scenario, as X-ray cavities rise through the hot atmosphere, they entrain low entropy gas from the center of the galaxy to higher altitudes, mixing the gas and transporting high metallicity material outside the cluster core (cite: Churazov2001; Simionescu2009; Pope2010; Kirkpatrick2011; Gitti2011). Uplift may accelerate thermally unstable cooling by increasing the infall time of the gas, lowering t$_{\textrm{cool}}$/t$_{\textrm{ff}}$ below the threshold required for thermal instabilities to occur.

Observations of nebular emission are central to understanding the conditions under which thermally unstable cooling proceeds, the forms of ionization and heating, and the relationships between cooling inflows and AGN-driven outflows that regulate the growth of galaxies. While nebular emission is sensitive to a negligible fraction of the cooling mass, its high surface brightness probes the full extent of the unstable cooling region as well as the gas dynamics with respect to the central galaxy and its radio jets and lobes. To investigate the behaviour of the warm nebular gas in and around the central galaxies and its connection to both multiphase gas and AGN feedback, we undertook new observations of four cooling cluster cores using the Keck Cosmic Web Imager (cite: Morrissey2018). The integral field spectroscopy (IFS) capabilities of KCWI provide high sensitivity and high spectral and spatial resolution over a large field of view (FOV). From our observations, we obtain detailed maps of the fluxes and the kinematics of various emission lines, such as \[OII\]3726,9 Å, \[OIII\]4959 Å, \[OIII\]5007 Å, H$_{\beta}$, H$_{\gamma}$, \[NeIII\]3869 Å, and of the central galaxy’s stellar population. Combined with previous studies and archival observations from the Atacama Large Millimeter/submillimeter Array (ALMA), Very Large Array (VLA) and Chandra X-ray Observatory, we study the dynamics of different phases of the intracluster medium (ICM) and their interactions with the central galaxy, radio jets and X-ray cavities.

In this paper we analyze IFS observations of the central regions of Abell 262, RXJ0820.9+0752, Abell 1835 and PKS 0745-191 focusing on the morphology and kinematics of the \[OII\]3726,9 Å emission line doublet. The \[OII\]3726,9 Å emission doublet is the brightest emission line in the KCWI data for these targets. Its high contrast against the declining U-band stellar continuum below the 4000 Å  break adds sensitivity to the imagery. The high sensitivity images presented here trace the nebular emission to larger radii than earlier studies. Its relatively high spectral and spatial resolutions permit detailed studies of nebular gas velocities with respect to stellar velocities in the central galaxy. Our targets are part of a pilot program on Keck chosen for their range of properties and their complex structures.

In Section [2](#sec:Observations and data reduction) we provide a comprehensive account of our observations, data reduction techniques, and fitting methodology. We also discuss the complementary archival observations that are used throughout the paper and describe the analysis of the complementary data. In Section [3](#sec:Results) we present flux and kinematic maps for each of our targets (Abell 262: Section [3.1](#sec:Results:A262), RXJ0820.9+0752: Section [3.2](#sec:Results:RXJ0820), Abell 1835: Section [3.3](#sec:Results:A1835), PKS 0745-191: Section [3.4](#sec:Results:PKS0745)). In Section [4](#sec:Discussion), we discuss the implications of our results and compare them to AGN feedback models. Finally, in Section [5](#sec:Summary), we summarize the key takeaways. Throughout this paper we use a flat $\Lambda$CDM cosmology with H$_0 = 70$ km s$^{-1}$ Mpc$^{-1}$ and $\Omega_{\textrm{m}} = 0.3$.

# Observations and data reduction

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | Date | Central wavelength | Blue filter | \# of pointings | Total observing time | Seeing | Total FOV | Total extent |
|  | (DD/MM/YYYY) | (Å) |  |  | (hrs) | ($''$) | ($\ensuremath{''} \times \ensuremath{''}$) | ($\textrm{kpc} \times \textrm{kpc}$) |
| Abell 1835 | 19/03/2021 | 5300 | None | 6 | 2 | 0.8 | $35 \times 33$ | $141 \times 134$ |
| PKS 0745-191 | 12/02/2021 | 4650 | KBlue | 11 | 3.67 | 1.2 | $26 \times 31$ | $52 \times 61$ |
| Abell 262 | 14/01/2022 | 4300 | None | 10 | 2.5 | 0.9 | $30 \times 32$ | $10 \times 11$ |
| RXJ0820.9+0752 | 14/01/2022 | 4650 | None | 9 | 2.25 | 0.9 | $21 \times 24$ | $44 \times 50$ |

: KCWI Observations

Table notes: Columns: (1) Target name. (2) Date of KCWI observation. (3) Central wavelength. (4) Blue filter used. (5) Number of pointings. (6) Total observing time. (7) Seeing. (8) Total FOV obtained from the different pointings in arcseconds. (9) Same as previous column in units of kpc.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | R.A. | Dec. | z | R$_{2500}$ | M$_{2500}$ | t$_{\textrm{cool}}$ | L$_{\text{x}}$ | r(L$_{\text{x}}$) | L$_{\text{\textrm{H}}_{\alpha}}$ | L$_{\text{radio}}$ | M$_{\text{mol}}$ | M$_{*}$ | SFR$_{\text{IR}}$ | Cooling rate | \# of X-ray cavities | $E_{cav}$ | $P_{cav}$ |  |
|  | (J2000) | (J2000) |  | (kpc) | ($10^{13} M_{\odot}$) | (Gyr) | (erg s$^{-1}$) | (kpc) | (erg s$^{-1}$) | (erg s$^{-1}$) | (M$_{\odot}$) | (M$_{\odot}$) | (M$_{\odot}$ yr$^{-1}$) | (M$_{\odot}$ yr$^{-1}$) |  | ($10^{57}$erg) | ($10^{43}$erg s$^{-1}$) |  |
| Abell 1835 | 14:01:02.1 | +02:52:43 | 0.2514 | 711 | $61.0_{-2.5}^{+2.5}$ | $0.39_{-0.03}^{+0.04}$ | $1.6\times10^{44}$ | 20 | $1.7\times10^{42}$ | $3.71\times10^{41}$ | $5\times10^{10}$ | $6\times10^{11}$ | $125\pm25$ | 1175 | 2 | $156^{+62}_{-43}$ | $165^{+102}_{-55}$ |  |
| PKS 0745-191 | 07:47:31.3 | $-$19:17:40 | 0.1024 | 614 | $36.5_{-2.8}^{+2.9}$ | $0.35_{-0.02}^{+0.02}$ | $4\times10^{43}$ | 14 | $1.75\times10^{42}$ | $3.87\times10^{42}$ | $(4.6\pm0.3)\times10^{9}$ | $5\times10^{11}$ | 17.2 | $776\pm18$ | 2 | $69^{+29}_{-21}$ | $51_{-16}^{+25}$ |  |
| Abell 262 | 01:52:46.5 | +36:09:07 | 0.0160 | 286 | $3.40_{-0.10}^{+0.10}$ | $0.37^{+0.02}_{-0.02}$ | $1.69\times10^{41}$ | 3.5 | $3.16\times10^{39}$ | $2.77\times10^{39}$ | $3.4\times10^{8}$ | $3.3\times10^{11}$ | 0.54 | $\sim 3$ | 2 | $2.5^{+1.0}_{-0.7}$ | $1.6^{+1.2}_{-0.6}$ |  |
| RXJ0820.9+0752 | 08:21:02.3 | +07:51:47 | 0.1103 | 357 | $6.9_{-1.3}^{+1.4}$ | $0.42^{+0.04}_{-0.04}$ | $6.5\times10^{42}$ | 15 | $4.00\times10^{41}$ | $7.28\times10^{39}$ | $3.9\times10^{10}$ | $1.4\times10^{11}$ | 37 | $34\pm10$ | 1 | $1.1^{+0.6}_{-0.4}$ | $1.1^{+0.9}_{-0.5}$ |  |

: Targets properties

Table notes: Columns: (1) Galaxy name. (2) Right ascension (RA). (3) Declination (Dec). (4) Redshift obtained from stellar absorption lines. Heliocentric correction has been applied. (5) $R_{2500}$, radius within which the mean density is 2500 times the critical density ($\rho_c$). (6) $M_{2500}$, where M$_{2500}=4\pi \bar{\rho}\textrm{R}_{2500}^3/3$ and $\bar{\rho}=2500\rho_c$. (7) Cooling time within $0.02R_{2500}$. (8) X-ray luminosity within the radius listed in column 9. (9) Radius chosen for the X-ray luminosity listed in the previous column such that it covers a similar extent as the detected \[OII\] emission. (10) H$_{\alpha}$ luminosity. (11) Radio luminosity between 10 MHz and 5 GHz. (12) Molecular gas mass. (13) Stellar mass. (14) Star formation rate from infrared luminosity. (15) Cooling rate obtained from X-ray (Chandra) observations. (16) Number of known X-ray cavities. (17) Total energy required to inflate known X-ray cavities. (18) Total AGN power required to inflate the cavities.\
References: (5)-(9), (17)-(18): (cite: Hogan2017; Pulido2018). (10): (cite: Crawford1999), (cite: Hamer2016). (11): (cite: Pulido2018). (12): (cite: McNamara2014), (cite: Russell2016), (cite: Olivares2019), (cite: Edge2001). (13): (cite: Olivares2019), (cite: Donahue2011), (cite: Main2017). (14) (cite: Egami2006), (cite: ODea2008). (15) (cite: McDonald2018), (cite: Vantyghem2018). (16): (cite: McNamara2006), (cite: Sanders2014; Russell2019), (cite: Clarke2009), (cite: Vantyghem2019).

## Observations

Our four cluster targets were observed with KCWI (cite: Morrissey2018), which is installed on the Keck II telescope. For all targets we used the blue low-dispersion (BL) grating with the medium slicer, which results in a FOV of $16.5 \ensuremath{''} \times 20.4 \ensuremath{''}$ for each pointing. It has a spaxel scale of $0.29 \ensuremath{''} \times 0.69 \ensuremath{''}$, and a spectral resolution of $\rm R=1800$. We used a detector binning of $2 \times 2$ for all targets. Table [1](#tab:Observation_parameters) lists additional observational parameters for each target. The exposure time for each pointing is between $15-20$ minutes. The number of pointings and the total area covered for each object were chosen based on published observations of nebular gas extent and morphology, when available, to focus on regions of interest. Abell 262 did not have a published nebular gas map, so we used an archival cold molecular gas distribution map instead. Previous observations of similar central galaxies have shown that detected nebular gas and molecular gas distributions often spatially overlap, with nebular emission being more extended than for the molecular gas (cite: Olivares2019; Russell2019).

## Data reduction

We reduced the data using the KCWI Data Extraction and Reduction Pipeline (KDERP) in IDL. This pipeline applies various corrections, including bias subtraction, gain corrections and cosmic-ray rejections, and executes sky subtraction. We manually masked any source emission from our images to create blank sky images which we subtracted from our observations. In cases where the source covered the entire pointing such that obtaining a blank sky image was not possible, we used the sky image of a nearby pointing. The pipeline also corrects for differential refraction. To resample our data on a $0.29\ensuremath{''} \times 0.29 \ensuremath{''}$ spaxel grid and create a mosaic for each target, we used the IFSR_KCWIRESAMPLE and IFSR_MOSAIC routines from the IFSRED library (cite: Rupke2014a). Table [1](#tab:Observation_parameters) lists the resulting dimensions of each mosaic. As Abell 262 is at a much lower redshift than the other targets, a smaller central region is observed ($\sim$100 kpc$^2$), whereas for the other targets we observed areas at least 25 times larger. On the other hand, the low redshift of Abell 262 provides exquisite spatial resolution with spaxel sizes of less than $0.1~\rm kpc \times 0.1~kpc$.

## Stellar continuum and emission line fitting

From the reduced mosaics, we used the IFSFIT IDL library (cite: Rupke2014b) to fit the spectrum in each spaxel. This library uses the Penalized Pixel-Fitting method (PPXF) (cite: PPXF) and MPFIT (cite: MPFIT) to fit the stellar continuum and the emission lines, respectively. The fitting procedure followed five steps:

1.  **Creating a spatially-integrated spectrum:**\
    To obtain a high quality spectrum of the stellar component of the BCG, we first summed the spectra in the spaxels with strong stellar continuum emission.

2.  **Spatially-integrated Stellar Population Synthesis (SPS) model:**\
    Using IFSFIT on the spatially-integrated spectrum, we obtain a SPS best fit model for the stellar continuum at the very center of the galaxy. First the emission lines are masked from the spectrum, which is then fitted using the PPXF method of (cite: PPXF). The fit is a linear combination of SPS models from (cite: SSP2005) and Legendre polynomials. The SPS models are allowed to vary in age, but their metallicity is fixed to that of the sun. The SPS models are then summed over all stellar templates to obtain the stellar continuum model fit. A linear combination of Legendre polynomials are used to account for issues in data reduction such as scattered light, atmospheric effects, and/or residual features in the stellar continuum. We used Legendre polynomials of order 15.

    From this fit, we obtain the stellar velocity in the centermost region of the galaxy, which is then used as the systemic velocity of the system.

3.  **Fitting each spaxel:**\
    For each spaxel, the emission lines are masked and the starlight spectrum is fitted, using the same method as in the previous step. MPFIT (cite: MPFIT) is then used to fit the emission lines in the continuum-substracted spectrum. Before fitting, the model line profiles are convolved with the spectral resolution. Each emission line is fit with 1 or 2 Gaussian profiles, as needed. All emission lines are fit simultaneously with the same number of velocity components. The gaussian components of the different emission lines are all tied in redshift and linewidth to those of the \[OIII\]5007 emission line. The ratios of the different emission lines are free to vary, except for the ratio of \[OII\]3729/3726 which is fixed to 1.2, assuming an electron density of 400 cm$^{-3}$ (cite: Pradhan2006).

4.  **Determining the number of emission line velocity components:**\
    For each target, IFSFIT is run twice, allowing one or two Gaussian components for the emission lines. If the addition of a second Gaussian component does not improve the fit, a one component fit is returned. The two velocity component fits are used when: a) the flux for each component is positive and has a $\text{S/N} \geq 2$, b) both components have velocity dispersions of $\sigma < 500$ km s$^{-1}$, c) the flux ratio of the components is less than 10, and d) the addition of a second component significantly improves the fit. This last criterion is evaluated using the Bayesian Information Criterion (BIC): $$\begin{equation}
            \text{BIC} = \chi^2+k\text{ln}(n)
            
    \end{equation}$$ where $k$ is the number of parameters ($k = 3$ for 1 component and $k = 6$ for 2 components) and $n$ is the number of data points. A second component is used when the BIC of the two components fit is smaller than the BIC of the one component fit. Finally, we assume that spaxels requiring two Gaussian components should be spatially clustered together and not distributed randomly across the mosaic. Two component fits are used when neighbouring spaxels also use two component fits. Of the four galaxies observed, Abell 1835 and PKS 0745 have regions where the fits require a second component. Abell 262 and RXJ0820 can be modelled using only one kinematic component.

## Archival observations

Complimentary archival observations are used to compare the properties of the ionized gas in the ICM with the other gas phases, as well as to study the interactions between AGN feedback and gas dynamics. Table [2](#tab:target_properties) lists various properties of our targets obtained from multi-wavelength observations.

Cold molecular gas maps showing CO emission were obtained from ALMA archival observations for all four targets. Table [\[tab:ALMA:info\]](#tab:ALMA:info) gives the details of the ALMA observations. Maps of the CO fluxes were measured by integrating over the targeted CO emission lines. The resulting CO contours are consistent with results from previous papers (cite: McNamara2014; Russell2016; Vantyghem2017; Russell2019; Olivares2019; Vantyghem2019).

Detected X-ray bubbles are also shown in the maps presented in this paper. As discussed in Section [1](#sec:intro), X-ray cavities are believed to play an important role in determining ICM dynamics. Combining previous cavity detections (cite: McNamara2006; Rafferty2006; Sanders2014; Vantyghem2019) with nebular gas flux and kinematics maps, we can study how cavities impact nebular gas dynamics as well as investigate whether different AGN feedback models are consistent with our observations.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | Date of observation | Observing time | CO line | $\nu_{\textrm{obs}}$ | Beam size | Reference |
|  |  | (min) |  | (GHz) | $\ensuremath{''} \times \ensuremath{''}$ |  |
| Abell 1835 | 2012-03-28 | 59.5 | J$= 3-2$ | 276.190 | $0.60 \times 0.48$ | (cite: McNamara2014) |
| PKS 0745-191 | 2014-08-19 | 56.4 | J$= 3-2$ | 313.562 | $0.27 \times 0.19$ | (cite: Russell2016) |
| Abell 262 | 2016-06-27 | 11.1 | J$= 2-1$ | 226.863 | $0.95 \times 0.61$ | (cite: Olivares2019) |
| RXJ0820.9+0752 | 2016-10-01 | 22.7 | J$= 3-2$ | 311.248 | $0.21 \times 0.165$ | (cite: Vantyghem2017) |

: ALMA observations

# Results

Using KCWI integral field spectroscopy, we study the morphology and kinematics of the warm ionized gas in four cooling cluster cores. While various emission lines are detected, including \[OII\], \[NeIII\], \[OIII\], and numerous hydrogen lines, the \[OII\]3726,9 Å doublet is the most prominent line in our data and is therefore the focus of this paper. The analysis of other emission lines will be the focus of a future paper. For all flux and kinematics maps of the \[OII\]3726,9 Å doublet, a $\textrm{S/N} \geq 5$ flux is applied for every spaxel.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Target | L$_{[OII]}$ | $\textnormal{M}_{\textnormal{ion}}$ | Area \[OII\] | Area CO |
|  | erg s$^{-1}$ | M$_{\odot}$ | kpc$^2$ | kpc$^2$ |
| Abell 1835 | $4.0 \times 10^{42}$ | $1.1\times10^8$ | 1467 | 84 |
| PKS 0745-191 | $4.6 \times 10^{41}$ | $1.3\times10^7$ | 547 | 3.2 |
| Abell 262 | $1.4 \times 10^{40}$ | $4.2\times10^5$ | 24 | 1 |
| RXJ0820.9+0752 | $1.8 \times 10^{41}$ | $5.2\times10^6$ | 266 | 27 |

: \[OII\]3726+\[OII\]3729 integrated luminosity

Table notes: Columns: (1) Target name. (2) Total \[OII\] luminosity observed with $\text{S/N} \geq 5$. (3) Ionized gas mass inferred from total \[OII\] luminosity. (4) Total area with \[OII\] emission where $\text{S/N} \geq 5$ for the \[OII\] flux. (5) Total area with detected CO emission, using a flux cut of 10% of the peak CO flux.

## Abell 262

The central galaxy in Abell 262 has the lowest redshift and the lowest mass in our sample (see Table [2](#tab:target_properties)). Abell 262 is different than our other targets as it hosts a molecular circumnuclear disk with a radius of 1.5 kpc (cite: SC2003; Russell2019) embedded in a more extended disk of ionized gas (cite: Hatch2007). Circumnuclear disks in the core of central galaxies are rare, but not unheard of (cite: Rose2019).

The central galaxy in Abell 262 has well-known AGN jets oriented to the east and west, both with linear sizes of $\sim 11~\rm kpc$ by $\sim 4$ kpc (cite: Clarke2009). Extended radio lobes and jet inflated X-ray cavities (cite: Blanton2004; Birzan2008; Clarke2009) are found between 8 to 29 kpc from the core of the central galaxy. Due to the low redshift of the source, our FOV is too small to include the X-ray cavities, the closest of which are $8-10$ kpc east and west of the nucleus.

### Abell 262: Morphology

![](A262_flux.pdf)

Abell 262 has the lowest redshift in our sample such that the KCWI FOV only covers the inner part of the central galaxy. The KCWI spectra cover rest-frame wavelengths between $\rm 3445~\AA$ and $\rm 5118~\AA$. The left panel of Fig. [1](#fig:flux:A262) shows the stellar flux map for Abell 262.

For our analysis the “nucleus" of the central galaxy, which is the origin in the various flux and velocity maps, is taken to be the spaxel with the brightest stellar emission. However, the central galaxy in Abell 262 has a well-known dust lane, which can be seen in the left panel of Fig. [1](#fig:flux:A262) cutting vertically through the center of the galaxy. Absorption from the central dust lane causes a decrease of the flux in the central region. Therefore, contrary to the other targets in our sample, the brightest stellar continuum spaxel does not provide an accurate position of the nucleus in this case. Instead, the location of the nucleus is defined by the spaxel with the largest stellar velocity dispersion.

The stellar map shown in Fig. [1](#fig:flux:A262) uses a threshold for the stellar flux per spaxel of $1.5 \times 10^{-15}$ erg s$^{-1}$ cm$^{-2}$. Overall, we detect a total stellar luminosity of $3.6 \times 10^{42}$ erg s$^{-1}$ in a roughly circular region with a radius of 2.5 kpc. Half of the total stellar flux is emitted within a radius of 1.43 kpc around the nucleus.

The middle and right panels of Fig. [1](#fig:flux:A262) show the continuum-subtracted \[OII\] flux map, with S/N $\geq 5$. Stellar emission and CO(2-1) emission are shown by magenta and red contours, respectively. While X-ray cavities have been detected in this system, they are not shown in Fig. [1](#fig:flux:A262) as they lie beyond the FOV of our maps. The two closest X-ray cavities are roughly $8-10$ kpc from the nucleus along the E-W axis.

Within our FOV we measure a total \[OII\] luminosity of $1.4 \times 10^{40}$ erg s$^{-1}$. From the \[OII\] luminosity, we can estimate the mass of ionized gas ($\textnormal{M}_{\textnormal{ion}}$) using: $$\begin{equation}
\label{eq:Mion}
    \textnormal{M}_{\textnormal{ion}} = \frac{\mu \textrm{m}_{\textrm{H}} \textrm{L}_{\textrm{[OII]}}}{\gamma_{\textrm{[OII]}} \textrm{n}_\textrm{e}}
\end{equation}$$ where $\mu$ is the mean mass per hydrogen atom which we set to $\mu=1.4$, m$_{\textrm{H}}$ is the mass of the hydrogen atom, n$_{\textrm{e}}$ is the electron density number and $\gamma_{\textrm{[OII]}}$ is the effective line emissivity (cite: Osterbrock2006). Assuming an electron temperature of $\sim 10 000$ K and an electron density of $\sim 400$ cm$^{-3}$, we obtain an effective line emissivity for the \[OII\] doublet of $\sim 10^{-25}$ cm$^3$ erg s$^{-1}$ (cite: PyNeb). It corresponds to an ionized gas mass of $\sim 4 \times 10^5$ M$_{\odot}$ (see Table [\[tab:OII_lum\]](#tab:OII_lum)).

Half of the \[OII\] emission comes from a central region with a radius of 1.32 kpc. The detected \[OII\] emission spans 5.45 kpc in RA and 8.58 kpc in Dec. The \[OII\] emission is highly spatially asymmetric. Fig. [1](#fig:flux:A262) shows prominent filaments extending to the SW and NW of the nucleus, with another small filament to the SE. The nebular gas is more extended along the north-south axis, which is perpendicular to the axis of the cavities.

The middle panel of Fig. [1](#fig:flux:A262) shows that most (64%) of the area with detected \[OII\] emission also has detected stellar emission. The stellar continuum and the \[OII\] emission have different morphologies. The asymmetry of the nebular gas is not present in the stellar continuum map. The upper half of the NW filament and the bottom half of the SW filament are the main regions where nebular gas is detected without a stellar counterpart. Since the regions with the brightest stellar continuum and brightest \[OII\] emission overlap, only 20% of the \[OII\] flux is emitted from regions without detectable starlight.

The right panel of Fig. [1](#fig:flux:A262) superimposes CO(2-1) contours, in red, onto the \[OII\] flux map (cite: ALMA_A262). Most of the detected molecular gas ($> 70\%$) lies very close to the nucleus, in a roughly elliptical region with major and minor axes of $\sim 2$ kpc and $\sim 1$ kpc, respectively. Previous studies of the dynamics of the molecular gas in this system concluded that it is consistent with a rotating circumnuclear disk (cite: Russell2019; Olivares2019).

The spatial distributions of molecular gas and nebular gas are consistent with each other. CO(2-1) emission is detected where the nebular gas is the brightest. As detailed in Table [\[tab:OII_lum\]](#tab:OII_lum), \[OII\] emission is much more extended than CO(2-1) emission, spanning a projected area 24 times larger. The morphologies of the nebular gas and the cold gas in this system are consistent with models where molecular gas cools out of its warmer surroundings.

### Abell 262: Kinematics

![](A262_kinematics.pdf)

![](A262_radio_sig.pdf)

. The black dotted ellipses show the position of the X-ray cavities (cite: Blanton2004; Clarke2009).

Fig. [2](#fig:kinematics:A262) presents the line-of-sight (LOS) kinematics of the \[OII\] emission at each spaxel in the innermost region of the central galaxy of Abell 262. The panels shown are the median velocity (upper left), the velocity dispersion (upper right), the maximum redshifted velocity, $v_{02}$, (lower left), and the maximum blueshifted velocity, $v_{98}$, (lower right). Positive velocities are redshifted with respect to the systemic redshift, and negative velocities are blueshifted. The maximum redshifted (blueshifted) velocities are obtained by determining the velocity at 2% (98%) of the cumulative velocity distribution; these values probe the most extreme velocities of the ionized gas. The definitions of v$_{02}$ and v$_{98}$ are explained more in depth in Appendix [8.1](#appendix:v02_v98). As discussed in Section [2.3](#sec:Observations and data reduction: Data analysis: Fitting), we attempted to fit the emission lines using both the one kinematic component model and the two kinematic component model. For this system, the emission lines are fitted using only one kinematic component. While the spectral fits hint to the possibility of a second kinematic component, especially for the more disturbed gas, we cannot robustly detect it using our current data. Additional observations are needed to further study the possibility of multiple kinematic components in this nebula.

To assess overall velocities over multiple spaxels, we define \[OII\] flux-weighted mean velocities as: $$\begin{equation}
\label{eq:flux-weighted_mean}
    \bar{\textrm{v}}=\frac{\sum_{\textrm{i}} \textrm{v}_{\textrm{i}} \times \textrm{f}^{\textrm{[OII]}}_{\textrm{i}}}{\sum_{\textrm{i}} \textrm{f}^{\textrm{[OII]}}_{\textrm{i}}}
\end{equation}$$ where v is velocity (e.g. v$_{50}$, $\sigma$, v$_{02}$ or v$_{98}$), and $\textrm{f}^{\textrm{[OII]}}_{\textrm{i}}$ is the \[OII\] flux within the i*th* spaxel of any given region. We use the flux-weighted mean velocity to obtain an average velocity within a spatial region as if analyzing it as a single spaxel.

The high spectral resolution of our data allows us to measure both nebular emission lines and absorption lines from the starlight of the central galaxy. The systemic redshift of the stars surrounding the nucleus is used to determine the zero point of the velocity plots, as discussed in Section [2.3](#sec:Observations and data reduction: Data analysis: Fitting). We observe a discrepancy between the systemic velocity and the central velocity of the nebular gas. Within a radius of $1 \ensuremath{''}$ around the nucleus, the nebular gas has a mean \[OII\] flux-weighted v$_{50}$ of $+105$ km s$^{-1}$, with median velocities in each spaxel ranging between $+10$ km s$^{-1}$ and $+172$ km s$^{-1}$. However, the \[OII\] flux-weighted v$_{50}$ across our entire FOV is closer to the systemic velocity, with a relative velocity of only $+39$ km s$^{-1}$.

The v$_{50}$, v$_{02}$ and v$_{98}$ maps (Fig. [2](#fig:kinematics:A262)) show a clear gradient in velocities along the north-south axis. The nebular gas is redshifted in the north and blueshifted in the south, indicating ordered motion in a nascent disk. This is consistent with the molecular gas dynamics previously observed by (cite: Russell2019). Median velocity values range from $-314$ km s$^{-1}$ to $+422$ km s$^{-1}$. In addition to the main velocity gradient along the N-S axis, the northern ionized gas filament has an east-west gradient of $\sim 150$ km s$^{-1}$.

The top right panel of Fig. [2](#fig:kinematics:A262) shows the LOS velocity dispersion of the ionized gas. The majority of the gas is fairly quiescent, with more than 50% of the \[OII\] flux being emitted from gas with $\sigma < 100$ km s$^{-1}$. There is a high $\sigma$ region roughly centered on the nucleus and extending $\sim 25^{\circ}$ north of east. The gas is highly disturbed, with velocity dispersions up to 200 km s$^{-1}$. This region, where $\sigma \geq 140$ km s$^{-1}$, has a length of $\sim 2.5$ kpc and a width of $\sim 0.64$ kpc, emitting roughly one fifth of the total \[OII\] flux. The velocity dispersion gradually decreases away from the high $\sigma$ region. Most of the remaining gas is quiescent, with few slightly more disturbed knots of gas with $\sigma$ between 80 km s$^{-1}$ and 125 km s$^{-1}$.

Fig. [3](#fig:sig_radio:A262) shows VLA 1.4 GHz radio emission contours (cite: Clarke2009) superimposed onto the \[OII\] LOS velocity dispersion map. The dotted ellipses indicate the position of two detected X-ray cavities. Fig. [3](#fig:sig_radio:A262) shows that the central high $\sigma$ region roughly extends along the axis of the radio jets, with the highest $\sigma$ nebular gas spatially coinciding with the brightest 1.4 GHz emission. This is consistent with the high $\sigma$ gas being disturbed by powerful AGN-driven jets. Fig. [3](#fig:sig_radio:A262) shows that the maximum extent of the 1.4 GHz radio emission coincides with the position of the X-ray cavities. This is also consistent with mechanical AGN feedback models where AGN-driven jets inflate X-ray cavities which rise buoyantly in the surrounding atmosphere.

## RXJ0820.9+0752

This system is known for the significant offset between its central galaxy and its molecular and nebular gas reservoirs, which lie nearly 20 kpc NW of the galaxy’s core (cite: Bayer-Kim2002; Salome&Combes2004; Vantyghem2017; Olivares2019). (cite: Vantyghem2019) detected a possible X-ray cavity, which has yet to be confirmed from radio observations, located 6.4 kpc to the west of the nucleus (see Fig. [4](#fig:flux:RXJ0820), middle and right panels). With an estimated power of $1.14 \times 10^{43}$ erg s$^{-1}$, its cavity power is insufficient to produce the galaxy’s massive cold gas reservoir solely through stimulated cooling of uplifted gas (cite: Vantyghem2019). The $10^{10}$ M$_{\odot}$ molecular gas reservoir (see Table [2](#tab:target_properties)) likely results from sloshing caused by galaxy interactions. Based on the presence of a secondary galaxy $\sim 8$ kpc away from the main galaxy and the significant offset of the molecular and nebular gas reservoirs, galaxy interactions are believed to play a crucial role in the dynamics of multiphase gas in the core of RXJ0820.9+0752.

### RXJ0820.9+0752: Morphology

![](RXJ0820_flux.pdf)

The left panel of Fig. [4](#fig:flux:RXJ0820) shows the stellar continuum map between $3300-5100$ Å . This map only includes spaxels with observed continuum flux of at least $6 \times 10^{-16}$ erg s$^{-1}$ cm$^{-2}$. The continuum emission spans $\sim 14$ kpc in RA and Dec, roughly in the shape of an ellipse with major and minor axes of 17 kpc and 11 kpc, respectively. The total stellar luminosity is $2.3 \times 10^{43}$ erg s$^{-1}$. Half of the continuum flux is emitted within a central circular region with a radius of 3.6 kpc.

This system has a secondary galaxy projected $\sim$7.8 kpc to the SE of the central galaxy. It is seen in Fig. [4](#fig:flux:RXJ0820) as a secondary peak in the stellar continuum map. The stellar flux of the central galaxy is $\sim 3$ times greater than that of the secondary galaxy, with stellar luminosities within 5 kpc of their respective peaks of $1.7 \times 10^{43}$ erg s$^{-1}$ and $6.0 \times 10^{42}$ erg s$^{-1}$. The two galaxies have a relative velocity of almost 100 km s$^{-1}$, with the secondary galaxy being more redshifted. The proximity of the galaxies and their relative velocity indicate that they are likely interacting.

The middle and right panels of Fig. [4](#fig:flux:RXJ0820) show the \[OII\] continuum-subtracted flux maps. Stellar continuum contours are overlaid onto the \[OII\] map in magenta for the middle panel, highlighting the spatial offset of the nebula. Similarly, the CO(3-2) emission, seen as red contours in the rightmost panel of Fig. [4](#fig:flux:RXJ0820), is significantly offset from the stellar peak.

The central galaxy has a total \[OII\] luminosity of $1.82 \times 10^{41}$ erg s$^{-1}$, half of which is emitted within a radius of 7.3 kpc from the \[OII\] peak. As listed in Table [\[tab:OII_lum\]](#tab:OII_lum), an ionized gas mass of $\sim 5 \times 10^6$ M$_{\odot}$ can be inferred from the total \[OII\] luminosity, assuming T$_{\textrm{e}} = 10 000$ K and n$_{\textrm{e}} = 400$ cm$^{-3}$.

The \[OII\] flux map shows extended nebular gas spanning roughly 24 kpc in RA and 15 kpc in Dec. The nebular gas distribution is asymmetrical about the peak in \[OII\] emission, extending mostly to the NW of the peak. Contrary to the other systems presented here, the nebular gas extends beyond the X-ray cavity. The nebular gas is extended roughly along the major axis of the cavity.

The middle panel of Fig. [4](#fig:flux:RXJ0820) demonstrates the significant morphological differences between the stellar continuum and the nebular emission. Less than 30% of the area with detected \[OII\] emission also has detected stellar emission. Although most of the nebular gas is offset from the stellar continuum, the \[OII\] flux peak is fairly close to the stellar peak, located $\sim 3.3$ kpc NNW of the nucleus.

For the molecular gas, most of the CO(3-2) emission lies in a region spanning $\sim 8.7$ kpc in RA and $\sim 6.3$ kpc in Dec. The molecular gas reservoir, which is not centered on the nucleus, mostly consists of a single filament, with two denser gas clumps. The brighter clump is located $\sim 3$ kpc NNW of the nucleus, while the fainter clump is $\sim 3.5$ kpc east of the brighter clump. The CO(3-2) emission is slightly east of the X-ray cavity, partially overlapping with it.

As observed in our previous targets, the morphology of the CO(3-2) emission is quite similar to that of the nebular gas, although spanning a much smaller area. As detailed in Table [\[tab:OII_lum\]](#tab:OII_lum), the projected area of the \[OII\] nebula is ten times greater than for the CO(3-2) emission. This central galaxy, which is known for its extensive molecular gas reservoir, has the smallest \[OII\] detection area to CO detection area ratio of the four objects studied in this paper.

### RXJ0820.9+0752: Kinematics

![](RXJ0820_kinematics.pdf)

Fig. [5](#fig:kinematics:RXJ0820) displays the LOS kinematic maps of the nebular gas in the central galaxy of RXJ0820.9+0752, which has a redshift of $z=$0.1103 (see Table [2](#tab:target_properties)). As shown in the top left panel of Fig. [5](#fig:kinematics:RXJ0820), the nebular gas is substantially redshifted with respect to the systemic velocity. The \[OII\] median velocities range between $-12$ km s$^{-1}$ and $+286$ km s$^{-1}$, with a flux weighted mean v$_{50}$ of $\sim 150$ km s$^{-1}$.

The v$_{50}$ map shows interesting dynamics for the gas with large v$_{50}$ ($\geq +150$ km s$^{-1}$). The two regions with largest v$_{50}$, located $\sim3.7$ kpc north and $\sim 16.9$ kpc north-west of the nucleus, are connected by a slightly lower velocity filament ($+146$ km s$^{-1} \leq$ v$_{50} \leq +174$ km s$^{-1}$). The gas with lowest v$_{50}$ is located $\sim 14$ kpc west of the nucleus.

The top right panel of Fig. [5](#fig:kinematics:RXJ0820) shows that the gas is generally undisturbed. Almost 80% of the nebular gas has $\sigma$ less than 100 km s$^{-1}$. The most disturbed gas lies in a small region located $\sim 1.6$ kpc south-west of the nucleus. The few regions where $\sigma \geq 100$ km s$^{-1}$ lie on the edge of the detected \[OII\] nebula. Appendix [8.4](#appendix:RXJ0820) describes more in depth the properties of five regions of interest identified from the kinematic maps.

The bottom panels of Fig. [5](#fig:kinematics:RXJ0820), which show the most-redshifted and most-blueshifted velocities, do not reveal extreme velocities in this nebula. These velocity maps, as well as the $\sigma$ map, support a quiescent scenario for the nebular gas, even though it is substantially offset from the center of the main galaxy.

## Abell 1835

Abell 1835 is an archetype cool core cluster whose central galaxy is experiencing powerful radio-mechanical (radio-mode) feedback. Its powerful mechanical AGN feedback, with power greater than $1.5\times10^{45}$ erg s$^{-1}$, is capable of offsetting the system’s impressive 1175 M$_{\odot}$/yr of cooling (cite: McDonald2018) (see Table [2](#tab:target_properties)). Despite the formidable jet power released over the past several tens of Myr, the current radio source is relatively faint and amorphous, with a flux density of 2.3 mJy at 4.76 GHz (cite: ODea2010). (cite: ODea2010) detected a 1.5 arcsecond jet in the core of the central galaxy. Starting from the nucleus, the jet initially points to the west and then gradually bends in the NW direction.

### Abell 1835: Morphology

![](A1835_flux.pdf)

The left panel of Fig. [6](#fig:flux:A1835) shows the observed KCWI stellar continuum integrated over the rest-frame wavelength range of $3435-5035$ Å. The central galaxy is flanked in projection by several fainter galaxies. Eight neighboring galaxies are observed within our full KCWI FOV. Apart from one galaxy, the projected galaxies’ stellar velocities relative to the central galaxy differ by thousands of km s$^{-1}$. These high relative velocities are inconsistent with interactions with the central galaxy. Only one projected galaxy has a similar velocity as the central galaxy, although their projected separation of more than 60 kpc makes interactions between the two galaxies very unlikely. Therefore, we do not expect the projected galaxies to be interacting with the central galaxy or the surrounding gas.

Above a flux of $2.5 \times 10^{-16}$ erg s$^{-1}$cm$^{-2}$ per spaxel, the stellar continuum is detected up to a radius of $\sim 20$ kpc from the nucleus of the central galaxy. Half of the total stellar flux is contained within a radius of $\sim 9$ kpc ($2.2 \ensuremath{''}$).

The middle and right panels of Fig. [6](#fig:flux:A1835) show the detected \[OII\] flux in and around the central galaxy. Half of the \[OII\] flux is emitted within a radius of 7.3 kpc (1.8$''$) from the nucleus of the central galaxy. The \[OII\] detected spans more than 45 kpc in RA and 50 kpc in Dec. The total \[OII\] luminosity is $4 \times 10^{42}$ erg s$^{-1}$; this is the most \[OII\] luminous object in our sample (see Table [\[tab:OII_lum\]](#tab:OII_lum)). We estimate more than $10^8$ M$_{\odot}$ of nebular gas in the inner region of Abell 1835 (see Table [\[tab:OII_lum\]](#tab:OII_lum)).

Fig. [6](#fig:flux:A1835) shows that the peak of the stellar continuum, \[OII\] flux, and CO(3-2) flux all coincide. The stellar continuum and the \[OII\] emission overlap spatially. Approximately 90% of the stellar continuum flux coincides with 96% of the \[OII\] flux. Little nebular gas is detected outside of the region with detectable starlight.

Most of the observed molecular gas in Abell 1835 is concentrated around the nucleus, with the remaining molecular gas extending in roughly three filaments (cite: McNamara2014), a prominent northern filament, and smaller eastern and western filaments. The N and W filaments appear to be trailing the NW X-ray cavity, while the E filament seems to be trailing the SE cavity. The distribution of nebular gas generally follows the distribution of cold molecular gas but the nebular gas is far more extended, with a detected area 17 times greater than that of the detected cold gas (see Table [\[tab:OII_lum\]](#tab:OII_lum)). The \[OII\] morphology observed in the core of Abell 1835 provides compelling evidence for the impact of X-ray cavities on gas dynamics. The right panel of Fig. [6](#fig:flux:A1835) shows that the nebular gas is extended along the direction of the two X-ray cavities. The detected \[OII\] emission spans 53 kpc along the axis of the bubbles, compared to 32 kpc in the perpendicular direction.

### Abell 1835: Kinematics

![](A1835_kinematics.pdf)

![](A1835_Components_kinematics_noregions.pdf)

Fig. [7](#fig:kinematics:A1835) presents the LOS kinematics of the \[OII\] emission at each spaxel in Abell 1835. As detailed in Table [2](#tab:target_properties), the systemic redshift of this system is $z = 0.2514$. It is the most distant object in the sample.

Fig. [7](#fig:kinematics:A1835) reveals the complex gas dynamics surrounding the central galaxy. The median velocites of the nebular gas range between $-30$ and $+286$ km s$^{-1}$, with respect to the systemic velocity. It is worth noting that overall, the nebular gas is redshifted with respect to the systemic velocity, which is defined as the central stellar velocity. On average, the nebular gas is redshifted by an additional 150 km s$^{-1}$.

The gas with highest v$_{50}$ and $\sigma$ lies 8 kpc east of the nucleus. Analogously, on the other side of the nucleus, there is a low v$_{50}$ region. This could potentially indicate a bipolar outflow of gas caused by AGN activity. This system has two detected X-ray cavities, one on each side of the center along the SE-NW axis. The NW cavity partially overlaps with an extended low velocity filament while the SE cavity is projected onto substantially redshifted nebular gas with large $\sigma$.

A sizable low $\sigma$ region is seen along the eastern and northern edges of the \[OII\] emission. This region which contributes 20% of the total \[OII\] flux and spans a length of 75 kpc, has a velocity dispersion of less than 100 km s$^{-1}$. This gas is not being significantly disturbed. Finding undisturbed gas far from the nucleus implies that the main mechanism disrupting gas dynamics emanates from within the galaxy.

Regions of interest in the kinematic maps are discussed in Appendix [8.2](#appendix:A1835). Properties of the regions, including flux-weighted mean velocities, are listed in Table [\[tab:A1835:regions\]](#tab:A1835:regions).

Abell 1835 is one of the two targets in our sample where two distinct kinematic components are detected, with most of the \[OII\] emission (82%) coming from regions with two components. Fig. [8](#fig:kinematics:A1835:Components) shows the v$_{50}$ and $\sigma$ separately for the first and second kinematic components of the regions requiring at least two components in the emission line fits. For Fig. [8](#fig:kinematics:A1835:Components), the spaxels included in the velocity maps were chosen using softer criteria than for the total kinematic maps. To maximize the area where two kinematic components can be studied, we only require that each component of the resulting fit has a $\text{S/N} \geq 3$. The second component is defined such that its velocity dispersion is always greater than that of the first component.

Showing the kinematics of the two components separately clearly results in a different physical picture for each component. This is also shown in Fig. [23](#fig:kinematics:A1835:regions:spectra) in Appendix [8.2](#appendix:A1835) where significant differences between the first and second kinematic components are seen in the \[OII\] emission line fits. The top row of Fig. [8](#fig:kinematics:A1835:Components) shows that substantial variations in gas velocities are mostly reflected in the second component of the fits. The main features of the v$_{50}$ map for the first component are a slight increase in velocities $\sim 8$ kpc east of the nucleus and lower velocities NW of the nucleus. The v$_{50}$ map of the second component (upper right panel) is very similar to the v$_{50}$ map of the total \[OII\] emission line. As seen in Fig. [8](#fig:kinematics:A1835:Components), the median velocity of the (broader) second component varies the most between different regions. The gradients in total median velocities, both the one along the E-W axis and the one along the axis of the cavities, are also observed in the v$_{50}$ map for the second component.

The bottom row of Fig. [8](#fig:kinematics:A1835:Components) shows the velocity dispersion of the nebular gas associated with each kinematic component. By definition, the second component has larger $\sigma$. The velocity dispersion map of the first component (left panel) shows a slight increase in $\sigma$ in the highest v$_{50}$ region, with $\sigma \sim 100$ km s$^{-1}$, compared to the surrounding gas. We discussed above the NE region with low $\sigma$ on the outskirts of the detected \[OII\] emission. This low $\sigma$ region is due to the relatively quiescent gas in the first component, as a second component is not used when fitting this region.

The bottom right panel, showing the velocity dispersion of the second component, varies more substantially. The region slightly east of the nucleus is particularly disturbed, with large v$_{50}$, $\sigma$ and v$_{02}$ values (see Fig. [7](#fig:kinematics:A1835)). Another region with large velocity dispersion is located roughly 5 kpc east and 8 kpc north of the center. However, due to the low flux of the second component in this region, it is not seen as one of the prominent features on the total kinematics maps. Actually, when applying the method described in Section [2.3](#sec:Observations and data reduction: Data analysis: Fitting) to choose the optimal number of components, a one component fit is preferred for this region. Deeper observations are needed to thoroughly investigate the potentially complex gas dynamics obscured by the more quiescent gas.

The use of two kinematic component fits is required for this galaxy’s structure with the most complex dynamics being fitted by the second component. The second component is much more disturbed that the first, as shown by the second component’s large $\sigma$ and wide v$_{50}$ range. Both components contribute similarly to the total \[OII\] flux, with the second component emitting 55% of the \[OII\] emission for spaxels using two kinematic components. The kinematics in Fig. [8](#fig:kinematics:A1835:Components) are consistent with the galaxy having a quiescent gas component and a churned component which are modelled by the first and second kinematic components of our fits, respectively.

## PKS 0745-191

PKS 0745-191 is a strong cool core cluster known for its powerful radio emission. First discovered as a radio source, this object has a radio luminosity (between 10 MHz and 5000 GHz) of $3.87 \times 10^{42}$ erg s$^{-1}$ (cite: Pulido2018), more than ten times higher than the other objects in our sample (see Table [2](#tab:target_properties)). The radio emission is diffuse and amorphous, showing no clear jets or radio lobes. Based on the lack of radio jets and other structures in the radio emission, jets, which inflated the detected X-ray cavities, may have been disrupted by the dense environment of the galaxy’s core (cite: Russell2016). (cite: Baum_ODea1991) suggested that a merger may have disrupted the jet by changing its orientation.

### PKS 0745-191: Morphology

![](PKS0745_flux.pdf)

The left panel of Fig. [9](#fig:flux:PKS0745) shows the stellar flux at rest-frame wavelengths between $3356-5017$ Å. Above a stellar flux per spaxel of $2.5 \times 10^{-16}$ erg s$^{-1}$ cm$^{-2}$, the stellar continuum is detected in a roughly circular region with a radius of 8.3 kpc around the brightest stellar spaxel. This target has a total stellar luminosity of $1.78 \times 10^{43}$ erg s$^{-1}$, half of which is emitted within an inner region of 4.1 kpc in radius.

This target has one projected galaxy within the FOV shown in Fig. [9](#fig:flux:PKS0745), which is located 8.5 kpc SW of the nucleus of the central galaxy. The projected galaxy and the central galaxy may be interacting as they have similar stellar velocities, with a difference of only 34 km s$^{-1}$. The stellar flux map shown in the left panel of Fig. [9](#fig:flux:PKS0745) does not show any obvious sign of interactions between the two galaxies. These dynamics will be discussed in depth in a future paper focused on the stellar properties of our targets.

The middle and right panels of Fig. [9](#fig:flux:PKS0745) show the continuum-subtracted \[OII\] flux map. The total \[OII\] luminosity is $4.7 \times 10^{41}$ erg s$^{-1}$, corresponding to $\sim 10^7$ M$_{\odot}$ of nebular gas (for $T_e \sim 10 000$ K and $n_e \sim 400$ cm$^{-3}$) as shown in Table [\[tab:OII_lum\]](#tab:OII_lum). Half of the \[OII\] flux is emitted within a radius of 3.8 kpc (1.96$''$) from the nucleus of the central galaxy. The \[OII\] emission spans over 33 kpc in RA and 30 kpc in Dec, covering a total area of 542 kpc$^2$ (see Table [\[tab:OII_lum\]](#tab:OII_lum)). The \[OII\] morphology is related to the position of the X-ray cavities. As previously observed in many galaxies (cite: Russell2016; Olivares2019), the \[OII\] emission extends from the nucleus towards and around the edges of the two X-ray cavities. The cavities, which are roughly aligned along the SE-NW axis, are not at the same distance from the nucleus. The NW cavity is more than three times as far from the center of the galaxy as the SE cavity. This asymmetry is reflected in the \[OII\] distribution. Along the SE-NW axis, the detected \[OII\] emission extends slightly past the inner edge of each cavity. Therefore, the different cavity heights are reflected in the asymmetric nebular gas distribution along the cavities’ axis. This shows a clear relation between X-ray cavities and nebular gas morphology.

Fig. [9](#fig:flux:PKS0745) shows that the peaks in stellar, \[OII\] and CO(3-2) emission roughly coincide spatially. The peak of CO(3-2) is 2.5 kpc east of our nucleus. This corresponds to a small offset at the scale studied. The central panel of Fig. [9](#fig:flux:PKS0745) highlights the significant differences in the extent of the \[OII\] emission and the stellar continuum. The nebular emission is much more extended than the stellar emission towards the NW. Only 37% of the area with \[OII\] emission also has detectable stellar emission. However, since most of the \[OII\] flux is emitted near the bright galaxy center, 82% of the \[OII\] emission comes from regions with detected stellar emission. While we observe nebular emission to be more than twice as extended as the stellar continuum, most of the nebular gas coincides with starlight from the central galaxy.

The right panel of Fig. [9](#fig:flux:PKS0745) shows contours of the CO(3-2) emission superimposed on the \[OII\] flux map. Most of the cold gas is located within a radius of 5 kpc from the nucleus. The molecular gas is mostly contained in three filaments (cite: Russell2016). As we observed for the nebular gas, the cold gas filaments are extended in the direction of the cavities, one filament trailing the SE cavity and two filaments trailing the NW cavity.

The detected CO(3-2) emission spans a much smaller area than the nebular gas. The detected \[OII\] emission covers a projected area 45 times larger than that of the CO(3-2) emission (Table [\[tab:OII_lum\]](#tab:OII_lum)). The distribution of molecular gas coincides with the brightest nebular gas, as shown by previous observations (cite: Russell2019; Olivares2019). Deeper observations of the CO emission at the center of this galaxy may reveal a much larger cold gas reservoir.

### PKS 0745-191: Kinematics

![](PKS0745_kinematics.pdf)

![](PKS0745_Components_kinematics_noregions.pdf)

Fig. [10](#fig:kinematics:PKS0745) shows the LOS kinematics of the \[OII\] emitting gas with maps of the median velocities (upper left panel), velocity dispersion (upper right), most-redshifted velocities (lower left) and most-blueshifted velocities (lower right). From the continuum absorption lines in the core of the galaxy, we measure a systemic redshift of 0.1024 (see Table [2](#tab:target_properties)). As is the case for other targets in our sample, the nebular gas is redshifted with respect to the systemic velocity. On average, the nebular gas is redshifted by $\sim 135$ km s$^{-1}$. As shown in the top left panel of Fig. [10](#fig:kinematics:PKS0745), the total median velocities observed are mostly redshifted, with v$_{50}$ values between $-74$ km s$^{-1}$ and 402 km s$^{-1}$.

The gas with the most redshifted total median velocities, with v$_{50}>225$ km s$^{-1}$, lies in a 20 kpc filament roughly 8.5 kpc from the center of the galaxy. The lowest v$_{50}$ gas is observed in the westernmost part of the detected emission.

Of the four central galaxies in our sample, PKS 0745-191 has the broadest emission lines observed. As seen in the top right panel of Fig. [10](#fig:kinematics:PKS0745), the nebular gas in the core of PKS 0745-191 has $\sigma$ values up to 400 km s$^{-1}$, which is almost twice that of our other targets.

Two lines of high $\sigma$ nebular gas are seen in the right upper panel of Fig. [10](#fig:kinematics:PKS0745), forming a yellow cross roughly centered on the nucleus. The two regions with largest total velocity dispersion are located at the eastern end of the high $\sigma$ cross. They are located roughly 5 kpc NE and SE of the nucleus. The gas within these areas of the nebula is highly disturbed, having a total velocity dispersion greater than any other object in our sample. The lower left panel of Fig. [10](#fig:kinematics:PKS0745) shows that some of the gas in the NE high $\sigma$ region is extremely redshifted. With v$_{02}$ greater than 1250 km s$^{-1}$, there may be an extremely powerful outflow in this region.

This system has two known cavities within our FOV, roughly along the SE-NW axis, which are shown as dotted ellipses in the top right panel of Fig. [10](#fig:kinematics:PKS0745). The SE high $\sigma$ region is located within the SE cavity, while the upper part of the high v$_{50}$ filament partially overlaps with the NW cavity.

While the core of PKS 0745-191 has a large reservoir of nebular gas with $\sigma > 200$ km s$^{-1}$, the top right panel of Fig. [10](#fig:kinematics:PKS0745) also shows low $\sigma$ gas in the outermost regions. While these low $\sigma$ regions are quite extended, with a total area of $\sim 200$ kpc$^2$, they are also quite faint such that gas with total $\sigma \leq 100$ km s$^{-1}$ contributes to only 5.5% of the total \[OII\] flux. Other regions of interest are discussed more in depth in Appendix [8.3](#appendix:PKS0745).

Fig. [11](#fig:kinematics:PKS0745:Components) shows v$_{50}$ and $\sigma$ for each of the kinematic components. For PKS 0745-191, we use a combination of the amplitude, position and width of each fitted gaussian component to differentiate between the first and second kinematic component. To be consistent with the analysis done for Abell 1835, we defined the more quiescent gas as the first component and the more churned-up and disturbed gas as the second component. The v$_{50}$ and $\sigma$ maps for the total emission lines (Fig. [10](#fig:kinematics:PKS0745)) are different than the ones for the first and second components. While v$_{50}$ for the second kinematic component (top right panel Fig. [11](#fig:kinematics:PKS0745:Components)) does not look like the total v$_{50}$ map (top left panel Fig. [10](#fig:kinematics:PKS0745)), it does share similarities with the total $\sigma$ map (top right panel Fig. [10](#fig:kinematics:PKS0745)). This indicates that the broadening of the \[OII\] emission line is predominantly caused by significant differences in the v$_{50}$ of the first and second components. This is clearly seen in the integrated spectra shown in Fig. [25](#fig:kinematics:PKS0745:regions:spectra) in Appendix [8.3](#appendix:PKS0745).

The significant differences in the v$_{50}$ and $\sigma$ maps for the total \[OII\] line (Fig. [10](#fig:kinematics:PKS0745)) and the v$_{50}$ and $\sigma$ maps for each of the kinematic components (Fig. [11](#fig:kinematics:PKS0745:Components)) highlights the importance of disentangling the different kinematic components.

The top right panel of Fig. [11](#fig:kinematics:PKS0745:Components) shows the second components’ v$_{50}$. It highlights the redshifted gas observed NE, NW and SE of the nucleus. In comparison, the median velocities of the first kinematic component, seen in the upper left panel, show little variation.

The bottom right panel of Fig. [11](#fig:kinematics:PKS0745:Components), which maps $\sigma$ for to the second kinetic component, shows the distribution of the most disturbed gas in the central galaxy. The gas with the largest $\sigma$ lies around the nucleus and extends in the NE direction. This picture is consistent with a central mechanism, such as an AGN, disturbing gas around the nucleus. Comparing the v$_{50}$ and $\sigma$ second component maps, some of the central high $\sigma$ gas also has v$_{50} > 500$ km s$^{-1}$. The dynamics of the churned gas are consistent with an AGN driven outflow.

The complex dynamics in the core of PKS 0745-191 requires the use of two component fits to properly model the \[OII\] emission lines. Fig. [11](#fig:kinematics:PKS0745:Components) highlights the contrasting dynamics of the quiescent (first) component and the churned (second) component. A significant fraction of the nebular gas is churned, accounting for $\sim 39$ % of the total \[OII\] emission and $\sim 49$ % of the \[OII\] flux in spaxels with two kinematic components.

# Discussion

## Nebular Gas Structures: Peculiar Velocities With Respect to the Central Galaxy

The v$_{50}$ maps, shown in the top left panel of Fig. [2](#fig:kinematics:A262), [5](#fig:kinematics:RXJ0820), [7](#fig:kinematics:A1835), and [10](#fig:kinematics:PKS0745), reveal little blueshifted gas in three of our four targets. Surprisingly, most of the nebular gas in Abell 1835, PKS 0745-191 and RXJ0820.9+0752 is redshifted by $\sim +140$ km s$^{-1}$ with respect to the central galaxy. Assuming that the nebular gas is bound to the central galaxy, we would expect its mean velocity to be close to that of the stars.

The relative velocities indicate that the nebular gas and the central galaxies are, to some degree, dynamically decoupled.

Although initially surprising, velocity and positional offsets between nebular gas and central galaxies in the sky plane have been observed in many systems such as RXJ0820.9+0752, Abell 1991, Abell 3444 and Ophiuchus (cite: Hamer2012). Therefore, velocity offsets of this magnitude are likely common.

The nebular and molecular gas in RXJ0820.9+0752 (cite: Vantyghem2017) are spatially offset from the central galaxy indicating relative motion in the sky plane. Its LOS velocity offset of $\sim 150 ~\rm km~s^{-1}$ indicates redshifted motion similar to Abell 1835 and PKS 0745-191.

A displacement of one kpc can be achieved in approximately $\sim 10$ Myr assuming a relative velocity of $100 ~\rm km~s^{-1}$. Therefore, the event that triggered the gas displacement would have occurred between a few tens to 100 Myr ago. Phenomena leading to galaxy oscillations include sloshing induced by infalling galaxies and halos (cite: Markevitch2007; Zuhone2016), AGN outbursts, and larger scale dynamical oscillations (cite: vandenBosch2005; DePropris2021).

This motion could lead to several interesting effects. For example, cooling and star formation may be offset from the center of the galaxy. Motion of the central galaxy would distribute the energy released by the AGN more broadly throughout the atmosphere. This added heat circulation may help circumvent a potential problem with anisotropic heating models (cite: Heinz2006; Vernaleo2006; Babul2013). The relative motion may explain why radio bubbles are often misoriented with respect to the active radio source (cite: Fabian2006; Ubertosi2021) and are frequently amorphous rather than double-lobed.

The peculiar motion of the galaxy with respect to the gas may have significant consequences for thermally unstable cooling and the observed gas kinematics. Assuming that the quiescent nebular gas recently cooled from the hot atmosphere and is precipitating onto the galaxy in the forms of atomic and molecular clouds, the gas and stars should acquire angular momentum with respect to the central galaxy. Moreover, the change in gravitational acceleration of cooling gas parcels will alter the conditions required for thermally unstable cooling (cite: Godon1994; Pizzolato2005; McCourt2012; Gaspari2013; Voit2015), and will almost certainly enhance cooling. We expect peculiar motions with respect to the cooling X-ray atmospheres to be observed with X-Ray Imaging and Spectroscopy Mission (XRISM) calorimeter spectroscopy of hot atmospheres. Our understanding of thermally unstable cooling will require significant revision in light of these motions.

## Powerful Feedback Systems with Complex Velocity Fields

Abell 1835 and PKS 0745-191 were chosen to examine the impact of powerful radio AGN on their central galaxies. Both systems are home to some of the largest star formation rates known in central galaxies. Their nebular gas structures are similar. The total $\sigma$ maps reveal larger values in the inner regions indicating disturbed gas. The nebular gas at larger radii is more quiescent apart from regions near X-ray cavities or jets. The inner gas is apparently churned-up by the radio AGN. These disturbances are likely not the result of larger scale processes such as sloshing or mergers.

Abell 1835 and PKS 0745-191 require two kinematic component fits. The second component is sensitive to high $\sigma$ and extreme LOS velocities. regions with two distinct kinematic components roughly coincide with the inner regions where churned gas is found. The total v$_{50}$ and $\sigma$ can be misleading when multiple kinematic components are present. Large total $\sigma$ values may indicate broad emission lines from disturbed gas or two narrow kinematic components with different median velocities. Where two components are required, v$_{02}$ maps, v$_{98}$ maps and individual component maps enable us to disentangle kinematic components. This in turn permits mapping of the distribution of disturbed gas which is sensitive to potential inflows and outflows.

The v$_{50}$ of quiescent and churned gas along the same LOS can differ by hundreds of km s$^{-1}$. Furthermore, the median velocities of the churned and quiescent gases in the brightest spaxels, which contain the majority of nebular gas, also differ significantly. For Abell 1835, $\bar{\textrm{v}}_{50}$ is $+121$ km s$^{-1}$ and $+175$ km s$^{-1}$ for the quiescent and the churned gas, respectively. For PKS 0745-191, $\bar{\textrm{v}}_{50}$ is $+126$ km s$^{-1}$ and $+161$ km s$^{-1}$ for the quiescent and the churned gas, respectively.

![](A1835_quiescent_sigma.pdf)

Fig. [8](#fig:kinematics:A1835:Components) and [11](#fig:kinematics:PKS0745:Components) show the spaxels where two kinematic components can be disentangled along the LOS. Low velocity dispersion gas is associated with the first kinematic component while gas associated with the second component is significantly more disturbed and represents the churned part of the nebular gas.

Generally, for spaxels where only one kinematic component is observed, the nebular gas has low $\sigma$ and has kinematics similar to the quiescent component of the two component fits as seen in Fig. [12](#fig:A1835_v50_1comp). The region enclosed by the solid black line in Fig. [12](#fig:A1835_v50_1comp) shows the velocity dispersion of the quiescent gas for the inner region where two kinematic components are observed. Beyond this region, where only one kinematic component is observed, Fig. [12](#fig:A1835_v50_1comp) shows the velocity dispersion from the one component fit. We see a smooth transition in the $\sigma$ map between the inner and outer region. This shows that when only one kinematic component is detected in the outer regions of the \[OII\] emission, the gas dynamics are consistent with those of the quiescent component.

Our observations are consistent with a model where extended quiescent nebular gas surrounds embedded churned-up gas which lies closer to the central AGN. A schematic representation of this configuration is shown in Fig. [13](#fig:diagram). Our model includes quiescent nebular gas (shown in blue) which extends to the outer parts of the nebula. This gas may have recently cooled from the X-ray atmosphere. If so, we expect it to have kinematics similar to the hot atmosphere.

As the outer gas moves into the inner regions, it may be lifted back out by the outward motion of the radio jets and bubbles.

Similar velocity structures are observed in the Perseus cluster nebula, where churned-up gas is present in the inner 10 kpc near the radio bubbles, while quiescent low velocity dispersion gas extends out to 50 kpc (cite: Vigneron2024).

This model will be further examined by XRISM high resolution spectroscopy which will reveal the velocity dispersion and LOS speed of the hot atmosphere to precision similar to the Keck data.

## Velocity Structures Near the Radio Lobes and X-ray Bubbles

X-ray observations from the Chandra X-ray Observatory have played a pivotal role in our understanding of AGN mechanical feedback. Jets inflate massive X-ray cavities that rise through the atmosphere propelled primarily by buoyancy as they lift gas in their updrafts (cite: Birzan2004; McNamara2007). However, the outward speeds of the bubbles and X-ray gas advected into their wakes have only been inferred (cite: Churazov2001; Pope2010) and could be measured directly using XRISM X-ray spectroscopy with great difficulty and only for nearby systems. Here, we use velocity profiles of the nebular emission to infer bubble speeds by measuring the motion of the nebular gas in the bubbles’ wakes.

### Abell 1835

![](Dynamics_plot.pdf)

![](A1835_dist_v50_cavities_err.pdf)

![](A1835_dist_v50_horizontal.pdf)

![](PKS0745_dist_v50_SE_NW_errors.pdf)

We focus on the second kinematic component of the emission line fits for Abell 1835. Using the second component v$_{50}$ maps (see the top right panel of Fig. [8](#fig:kinematics:A1835:Components)), we searched for ordered motion and looked for signs of interactions between the \[OII\] gas and the AGN feedback process. We identified possible inflows and outflows by searching for velocity gradients in the churned v$_{50}$ maps. Once an axis is defined along some velocity gradient, we extracted the v$_{50}$ values along the projected axis and analyzed the evolution of nebular gas velocities along the chosen axis.

Different scenarios may be considered when testing possible gas inflows and outflows. First, as nebular gas is observed in projection, clouds may lie on the near side or the far side of the central galaxy. Whether the gas associated with the observed velocity gradient, or filament, is an inflow or an outflow depends on whether the filament is in front or behind the core of the central galaxy. Similarly, the choice of rest-frame for the nebular gas, usually either the gas located at the nucleus or at the other end of the filament, impacts the inferred model. Therefore, we will generally consider four possible scenarios, with either 1) the velocity centered on the nucleus, or centered on the end of the filament and 2) the filament either in front of the central galaxy or behind it. Discarding unphysical models, we can identify possible inflows and outflows of nebular gas in our systems.

Fig. [14](#fig:A1835:dist_vs_v50_cavities) shows the median velocities of the churned nebular gas in the central galaxy of Abell 1835 projected along the X-ray cavity axis, shown by the black solid line. The grey error bars show the uncertainty on the v$_{50}$ values obtained from the emission line fits. The v$_{50}$ map of the churned component is embedded in the bottom left of Fig. [14](#fig:A1835:dist_vs_v50_cavities). The median velocities are plotted as a function of their distance along the projected axis. The zero distance is defined as the projected position of the nucleus onto the cavities’ axis, which is where the grey dashed line and the solid black line intersect.

Fig. [14](#fig:A1835:dist_vs_v50_cavities) shows a gradient in the velocity of the churned nebular gas along the cavities’ axis. From the SE to the NW cavity, the gas velocity decreases from $+350$ km s$^{-1}$ to $-30$ km s$^{-1}$, with a central velocity of roughly $+165$ km s$^{-1}$. Centering the rest-frame velocity on the nebular gas velocity at the nucleus, the filament extending towards the SE cavity is redshifted, while the one extending towards the NW cavity is blueshifted with respect to the central galaxy.

For the negative distances in Fig. [14](#fig:A1835:dist_vs_v50_cavities) that correspond to the gas SE of the nucleus, the projected v$_{50}$ increase linearly towards the SE cavity. This velocity gradient indicates that the gas is moving with a speed proportional to the distance from the nucleus. This velocity profile is inconsistent with infall where speeds should increase toward the nucleus. The profile may indicate gas accelerating away from the nucleus over time being pushed by a central force, perhaps due to a jetted outflow or gas being advected into the bubble wakes and being lifted out from the nucleus. While both Abell 1835 and PKS 0745 have powerful radio sources, jets are not observed. We therefore consider the latter model.

The velocity profiles shown in Fig. [14](#fig:A1835:dist_vs_v50_cavities)

are consistent with bubbles moving away from the galaxy nearly along the LOS, with the NW bubble located in front (blueshifted) and the SE bubble located behind (redshifted) the central galaxy.

A similar analysis was applied to the axis perpendicular to the cavity axis shown in Fig. [14](#fig:A1835:dist_vs_v50_cavities) to verify that the gas is indeed flowing along the bubble trajectory. As expected, the v$_{50}$ of the churned nebular gas show no correlation with distance along the axis orthogonal to the X-ray cavities.

Fig. [15](#fig:A1835:dist_vs_v50:x) shows a velocity gradient running from $\sim 13$ kpc east to $\sim 13$ kpc west of the nucleus. The east-west v$_{50}$ decrease from $+380$ km s$^{-1}$ to $+15$ km s$^{-1}$. The scatter in the trend increases dramatically at 7 kpc to the east and to a lesser degree at a similar distance to the west. The eastern increase in scatter roughly occurs at the region with a v$_{50}$ peak, identified as Region B in Appendix [8.2](#appendix:A1835). This region corresponds approximately to the location of known molecular clouds seen with ALMA (cite: McNamara2014). The amplitude of the velocity scatter exceeds $600 ~\rm km ~s^{-1}$ far from the nucleus, indicating a strong interaction or high impact event. The ALMA early science data are too crude to clearly interpret this apparent interaction, which must await deeper ALMA imaging.

The gas locations, velocity profiles, and speeds in Abell 1835 are consistent with gas lifted outward in the updraft of the rising X-ray bubbles at a low inclination angle with respect to the LOS. The highest speed gases nearest to the bubbles are presumably moving close to the bubble speeds, while the gas further from the bubbles was advected into the wake more recently and is moving outward with slower speeds. Adopting this model, we infer cavity velocities of about $185-195$ km s$^{-1}$. Depending on the inclination angle of the system, this corresponds to cavity speeds of less than 300 km s$^{-1}$.

Empty bubbles are expected to rise at their maximum terminal speeds

(cite: Churazov2001; Birzan2004; Rafferty2006). A detailed study of M87’s bubble dynamics inferred speeds of roughly half the local sound speed (cite: Churazov2001). Using atmospheric temperatures surrounding the bubbles from (cite: Hogan2017) and (cite: Pulido2018), we find sound speeds of $840-910$ km s$^{-1}$. We therefore expect Abell 1835’s bubbles to rise at roughly 450 km s$^{-1}$. After correcting for inclination, the implied bubble speeds lie below half the local sound speed, suggesting that mass loading by material dragged outward is slowing down the bubbles.

### PKS 0745-191

The second component v$_{50}$ map for PKS 0745-191,

shown in the top right panel of Fig. [11](#fig:kinematics:PKS0745:Components), appears to have two velocity gradients. We will focus on the velocity gradient which is closest to the cavities’ axis which is shown in Fig. [16](#fig:PKS0745:dist_vs_v50:SE_NW). It shows the evolution of the median velocities of the churned nebular gas when roughly projected onto the SE-NW axis, shown by the solid black line in Fig. [16](#fig:PKS0745:dist_vs_v50:SE_NW). The embedded figure shows the v$_{50}$ map of the second component, as in the top right panel of Fig. [11](#fig:kinematics:PKS0745:Components). The symbols and lines overlaid on the velocity map are analogous to the ones in Fig. [14](#fig:A1835:dist_vs_v50_cavities) and [15](#fig:A1835:dist_vs_v50:x).

Fig. [16](#fig:PKS0745:dist_vs_v50:SE_NW) shows the median velocity of the nebular gas as a function of projected distance along the axis of the SE and NW X-ray cavities. Fig. [16](#fig:PKS0745:dist_vs_v50:SE_NW) shows two (V-shaped) velocity gradients whose vertex lies $2.4$ kpc in projection NW of the nucleus. The gas velocity at the vertex is close to 0 km s$^{-1}$. The median velocities of the nebular gas along the SE cut increase smoothly away from the vertex from $-20$ km s$^{-1}$ to $+200 ~\rm km ~s^{-1}$ at $-3$ kpc.

At larger negative distances, the scatter in v$_{50}$ dramatically increases, with values lying between $+625$ km s$^{-1}$ and $-100$ km s$^{-1}$. The explanation for this large increase in scatter near the bubble is unknown.

North-west of the vertex, the projected gas velocities increase from $-20$ km s$^{-1}$ to $+300$ km s$^{-1}$ at $+7$ kpc NW of the nucleus.

Beyond $\sim 7$ kpc NW of the projected centroid, the scatter in median velocities again significantly increases, with v$_{50}$ between $+250$ km s$^{-1}$ and $+625$ km s$^{-1}$. The origin of this large scatter is also unknown.

Several scenarios were considered to explain the position of the X-ray cavities with respect to the central galaxy and the V-shaped velocity profile. They include cavities launched at different epochs, and bubbles launched in different directions due to jet precession. None of these scenarios explain all aspects of the data.

However, when combining the effects of the central galaxy’s peculiar velocity along the LOS with a lifting model similar to the one proposed for Abell 1835 but with the bubbles being launched nearly in the sky plane rather than nearly along the LOS, we naturally obtain a V-shaped velocity profile.

![](PKS0745_diagram1.pdf)

Fig. [17](#fig:PKS0745:diagram:fig22) shows a diagram of the motion of X-ray cavities, inflated in the plane of the sky, and their associated gas in a system with significant peculiar motion of the central galaxy.

The top panel describes the dynamics in the core of PKS 0745-191 initially at time $t=0$ when the jet inflates the cavities. The lower panel shows the cavity trajectories governed by buoyancy and ram pressure vectors at a later time $\Delta$t. The red dots represent cool \[OII\] gas which, we assume, has been advected into the bubbles’ paths and drawn outward beneath the bubbles creating the observed velocity gradients. As seen in the lower panel of Fig. [17](#fig:PKS0745:diagram:fig22), both cavities are located behind the central galaxy, which is consistent with our observations. This model can explain how two cavities, which were inflated at the same time and by the same bipolar jet, can both lie behind the central galaxy. Fig. [17](#fig:PKS0745:diagram:fig22) shows that the SE cavity appears closer to the nucleus in the sky plane than the NW cavity, which is consistent with observations (cite: Sanders2014).

Using the LOS nebular gas speed closest to the cavities as an estimate of the cavities’ speed, the NW and SE cavities have LOS velocities of $\sim 320$ km s$^{-1}$ and $\sim 220$ km s$^{-1}$, respectively. The sound speed near the cavities in PKS 0745-191 based on temperatures from (cite: Hogan2017) and (cite: Pulido2018) are $800-930$ km s$^{-1}$, depending on the cavities’ position. The bubble velocities inferred in this paper for Abell 1835 and PKS 0745-191 lie well below half their sound speeds. Unreasonably large inclination angles would be required to explain this by projection.

A simple explanation consistent with observations is that the cavities are mass loaded and thus are moving more slowly.

## Molecular Gas Masses

The targets presented here have been observed with ALMA for CO(1-0), CO(2-1), or CO(3-2), or a combination.

Throughout the result section, we have highlighted similarities in the spatial distributions of nebular and molecular gases. The CO emission is significantly less extended than the \[OII\] emission. However, in regions where both CO and \[OII\] emission are detected, the regions with brightest CO emission also have the brightest \[OII\] emission.

As \[OII\] is a more sensitive indicator of molecular and atomic gasses, we use \[OII\] as a proxy for CO and allow for the possibility that the molecular gas is more extended than observed but too faint to detect.

To do so, we determine the ratio of the \[OII\] luminosity to M$_{\textrm{mol}}$ within the region where the CO integrated flux is at least 10% of its peak value. This region corresponds to the areas enclosed by the CO contours in the right panel of Fig. [1](#fig:flux:A262), [4](#fig:flux:RXJ0820), [6](#fig:flux:A1835), and [9](#fig:flux:PKS0745). Using this ratio and the total \[OII\] luminosity within the FOV, we scale the observed molecular gas mass to estimate the total M$_{\textrm{mol}}$ that may be located in the extended nebula. Tables [2](#tab:target_properties) and [\[tab:OII_lum\]](#tab:OII_lum) list the values used in our calculations. Under the assumption that the ratio of \[OII\] luminosity to molecular gas mass within an object is constant, we infer molecular gas masses of $1.3 \times 10^{11}$ M$_{\odot}$, $3.0 \times 10^{10}$ M$_{\odot}$, $1.3 \times 10^{9}$ M$_{\odot}$ and $1.1 \times 10^{11}$ M$_{\odot}$ for Abell 1835, PKS 0745-191, Abell 262, and RXJ0820.9+0752, respectively. These values indicate total gas reservoirs that may be several times more massive than inferred from direct CO observations.

## Molecular & Nebular Gas Kinematics 

Our attempt to compare the nebular and molecular gas velocities is complicated by differences in spatial resolution and velocity reference frame. This study uses the central galaxy’s LOS speed as the reference velocity, which represents the best measure of the local rest-frame. However, lacking reliable stellar absorption line velocities, the ALMA studies of Abell 1835 (cite: McNamara2014), PKS 0745-191 (cite: Russell2016), and RXJ0820.9+0752 (cite: Vantyghem2018) used the central LOS velocity of either the molecular or nebular gas as the systemic velocity of the system.

This resulted in rest-frame velocity differences of approximately 192 km s$^{-1}$, 111 km s$^{-1}$, 64 km s$^{-1}$ and 156 km s$^{-1}$ for Abell 1835, PKS 0745-191, Abell 262 and RXJ0820.9+0752.

(cite: McNamara2014) reported a possible bipolar flow of $10^{10} ~M_\ensuremath{\odot}$ of molecular gas to the north-west and east of Abell 1835’s nucleus. Similar outflows to the ones depicted in Fig. [14](#fig:A1835:dist_vs_v50_cavities) and [15](#fig:A1835:dist_vs_v50:x) are observed in CO(1-0) (see Fig.5 in (cite: McNamara2014)). General velocity trends observed in the molecular gas maps are also seen in the nebular gas maps. The eastern high velocity gas clump and the NW lower velocity clump shown here were observed in the molecular gas by (cite: McNamara2014). However, the increase in velocity in the eastern gas clump is more pronounced for the CO(1-0) map than for the \[OII\] map. Overall, similarities between the kinematics of molecular and nebular gas seem to indicate that the dynamics of the molecular gas are generally consistent with the nebular gas but not in detail. They do not move in lockstep.

PKS0745-191 contains almost $5\times10^9$ M$_{\odot}$ of molecular gas distributed in three filaments, N, SE and SW of the nucleus (cite: Russell2016). The \[OII\] emission is much more extended than the CO emission, resulting in only a small area where nebular and molecular gas velocities can be compared. In these regions we find no clear clear relationship between the molecular and nebular gas velocities although they share similar magnitudes. This differentiation would indicate that the nebular gas is not solely composed of the ionized skins of molecular clouds in the churning region.

The molecular gas systemic velocity of RXJ0820.9+0752 (cite: Vantyghem2018) in CO(1-0) and CO(3-2) align closely to the nebular velocity maps.

The rotating disk of nebular and molecular gas in Abell 262 were easily registered about the zero velocity and their speeds closely align.

However, the nebular gas disk is more extended than the molecular disk and appears dynamically disturbed in its outer regions.

Estimates of the gas kinetic energy indicate the fraction of the jet’s power dissipated into motion of the surrounding gas. As the gas mass is dominated by the molecular gas, molecular gas dominates the energy budget. Typically only a few percent or less of the jet power is dissipated in lifting the molecular gas (cite: Tamhane2022). The sizes, approximate locations, and speeds of the molecular gas flows in PKS 0745-191 and Abell 1835 (cite: Tamhane2022) are similar to the outwardly-rising velocity profiles of the nebular gas between the X-ray bubbles found here. However, the nebular gas with velocities exceeding $300 ~\rm km$ s$^{-1}$ and upward of $600~ \rm km$ s$^{-1}$ are not detected in CO. This very high speed gas involves a small fraction of the mass and thus would have little impact on the kinetic energy budget.

# Summary

We investigated the dynamics of the warm nebular gas in and around the central galaxies of four clusters, Abell 1835, PKS 0745-191, Abell 262 and RXJ0820.9+0752, using KCWI observations. We explore both the morphology and the dynamics of these four galaxies, focusing on the \[OII\] nebular emission. We combine our observations with previous multiwavelength studies, including radio and X-ray observations, delving into the dynamics of the multiphase gas in clusters cores.

- We detect significant line-of-sight velocity differences, roughly $+150$ km s$^{-1}$, between the nebular gas and the stars in the core of the central galaxy in three of our four targets: Abell 1835, PKS 0745-191 and RXJ0820.9+0752. Comparing the morphology and the kinematics of the central galaxy and its nebular gas, we conclude that the central galaxy has a peculiar velocity with respect to its surroundings. Peculiar motion of central cluster galaxies in the plane of the sky have been inferred to explain spatial offsets between central galaxies and their associated nebular gas as is seen here in RXJ0820.9+0752. The LOS velocity offsets measured here are consistent with inferred velocities in the sky plane required to explain spatial offsets and asymmetries in galaxy morphologies.

- Two distinct velocity components are found in the nebular gas surrounding the Abell 1835 and PKS 0745-191 central galaxies. Higher velocity dispersion churned gas is found towards and behind X-ray cavities surrounded by lower velocity dispersion quiescent gas extending to higher altitudes. Median velocities of the quiescent and churned-up nebulae differ by $\sim 45$ km s$^{-1}$. Energy input from the AGN is likely churning up the gas.

- Molecular and nebular gas in central galaxies are spatially correlated such that the brightest CO and \[OII\] emission are coincident. However, the detected \[OII\] gas is much more extended by tens of kpc. Three to six times the molecular gas mass of the bright centrally located molecular clouds may lie in a diffuse state. The velocity structures of the molecular and nebular gas are broadly similar but do not match in detail.

- Coherent motions are observed beneath X-ray cavities in Abell 1835 and PKS 0745-191. The velocites are consistent with gas being lifted behind the X-ray bubbles whose kinematics are governed by buoyancy and ram pressure produced by the peculiar motion of the central galaxy with respect to the surrounding atmosphere. The speeds of the advected gas nearest to the X-ray cavities imply cavity speeds of several hundred kilometers per second, but below the buoyancy speeds of empty bubbles. The slower speeds imply mass loading of gas lifted by the cavities.

- High velocity dispersion nebular gas (Fig. [3](#fig:sig_radio:A262)) is observed along the radio jets in the central galaxy of Abell 262, indicating a strong interaction between the jets and the surrounding gas. The jets are emerging along the angular momentum axis of a disturbed, possibly nascent circumnuclear disk.

The data presented herein were obtained at the W. M. Keck Observatory, which is operated as a scientific partnership among the California Institute of Technology, the University of California, and the National Aeronautics and Space Administration. The observatory was made possible by the financial support of the W. M. Keck Foundation. We wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortunate to have the opportunity to conduct observations from this mountain. We thank Prathamesh Tamhane and Adrian Vantyghem for generously providing us with CO detection maps. We thank Tom Rose for the helpful discussions. B.R.M acknowledges support from the Natural Sciences and Engineering Council of Canada and the Canadian Space Agency Space Science Enhancement Program. A. L. C. acknowledges support from the Ingrid and Joseph W. Hibben endowed chair at UC San Diego. Finally, we thank the anonymous referee who graciously took the time to review our paper and give us constructive comments which improved our paper.

# Software

Astropy (cite: Astropy1; Astropy2; Astropy3), Python (cite: Python3), Numpy (cite: Numpy1; Numpy2), Matplotlib (cite: Matplotlib), Scipy (cite: SciPy),

# Systemic Velocity Measurements

![](A1835_systemic_velocity.pdf)

![](PKS0745_systemic_velocity.pdf)

![](RXJ0820_systemic_velocity.pdf)

The measurement of systemic velocities followed the procedure outlined in Section [2.3](#sec:Observations and data reduction: Data analysis: Fitting). In our approach, we employ stellar absorption lines and stellar population models to derive the stellar velocity of the systems, operating under the assumption that these stars are gravitationally bound to the central galaxy, with the central stellar velocity reflecting the velocity of the central galaxy. Spaxels surrounding the peak of the stellar emission are spatially-integrated, yielding a high quality central spectrum. Then, masking the emission lines, the stellar continuum is fitted using a combination of stellar templates. The mean stellar velocity in the core of the galaxy is obtained from this fit and used as the systemic velocity. Heliocentric corrections are then applied to these velocities to obtain the corrected redshifted listed in column 4 of Table [2](#tab:target_properties). The uncorrected systemic redshifts are 0.25131, 0.10245, 0.01606, and 0.11033 for Abell 1835, PKS 0745-191, Abell 262 and RXJ0820.9+0752, respectively.

The top panels of Fig. [18](#fig:appendix:A1835:zsys), [19](#fig:appendix:PKS0745:zsys) and [20](#fig:appendix:RXJ0820:zsys) show the central stellar fits obtained for Abell 1835, PKS 0745-191 and RXJ0820.9+0752, respectively. For Abell 1835 and PKS 0745-191, the stellar continuum shows strong Balmer absorption lines which are caused by a strong intermediate age stellar population. This raised concern that this population, if kinematically distinct from the older stellar population, may bias our systemic velocity and not properly represent the velocity of the central galaxy. To verify that the older stellar population, which is expected to be strongly bounded to the core of the central galaxy, is correctly fitted by our stellar model, we looked at the goodness of the fit for the Ca H & K lines, which originate primarily from old stars. The figures embedded in the upper panels of Fig. [18](#fig:appendix:A1835:zsys), [19](#fig:appendix:PKS0745:zsys) and [20](#fig:appendix:RXJ0820:zsys) show that the Ca H & K lines are correctly fitted by the model, showing that the intermediate age stellar population is not biasing our systemic velocities.

Fig. [18](#fig:appendix:A1835:zsys), [19](#fig:appendix:PKS0745:zsys) and [20](#fig:appendix:RXJ0820:zsys) show velocity differences of $\sim 150$ km s$^{-1}$ between the central nebular gas and the systemic velocities in three out of our four target systems, as discussed in Section [4.1](#sec:Velocity_galaxies). The lower panels of Fig. [18](#fig:appendix:A1835:zsys), [19](#fig:appendix:PKS0745:zsys) and [20](#fig:appendix:RXJ0820:zsys) show the stellar continuum models shifted to the central nebular gas velocity. In all instances, the shifted stellar models do not fit the observed spectrum as well as the non-shifted one, thus confirming the reality of the peculiar nebular velocities.

# Notes on uncertainties

Throughout this paper, for the emission line maps, S/N cuts for the \[OII\] doublet are used as the main criterion to determine which spaxels are included in the flux and kinematic maps as described in Section [2.3](#sec:Observations and data reduction: Data analysis: Fitting). S/N cuts are also used when deciding between the one or two kinematic component fits and as a threshold for the spaxels to include in the two component kinematic maps (Fig. [8](#fig:kinematics:A1835:Components) and Fig. [11](#fig:kinematics:PKS0745:Components)).

The precision of the fits obtained can also be assessed from the errors on v$_{50}$ and $\sigma$, both measured for the one and two kinematic component fits. Generally, the regions with higher flux have smaller uncertainties, with errors of only a few km s$^{-1}$. The uncertainties in v$_{50}$ and $\sigma$ increase away from the brightest spaxels, with the largest uncertainties being around the edges of the detected \[OII\] emission. This increase in uncertainties can be seen on the edges of the v$_{50}$ and $\sigma$ maps for Fig. [8](#fig:kinematics:A1835:Components) and [11](#fig:kinematics:PKS0745:Components), where the velocity variations between adjacent spaxels is larger. While spaxels on the edges of the detected \[OII\] emission can have larger uncertainties, reaching values of $20-50$ km s$^{-1}$, consistent motion seen over multiple neighbouring spaxels can be trusted and is very unlikely to be caused by uncertainties in the velocities. For example, the higher $\sigma$ region around the origin in the $\sigma$ map of RXJ0820.9+0752 (top right panel of Fig. [5](#fig:kinematics:RXJ0820)) is believed to be physical and not caused by an increase in uncertainties on the edges of the nebula. However, the individual $\sigma$ values for the dark red spaxels in this region, $\sigma > 170$ km s$^{-1}$, are more uncertain, with errors between $16-47$ km s$^{-1}$.

# Additional comments on kinematics

## v$_{02}$ and v$_{98}$

![](v02_v98_explain.pdf)

When visualizing the kinematics for our four targets as in Fig. [2](#fig:kinematics:A262), [5](#fig:kinematics:RXJ0820), [7](#fig:kinematics:A1835) and [10](#fig:kinematics:PKS0745), we map four velocities for the total \[OII\] doublet emission line: the median velocity v$_{50}$, the velocity dispersion $\sigma$, the 2% most-redshifted velocity v$_{02}$ and the 2% most-blueshifted velocity v$_{98}$. Fig. [21](#fig:v02_v98) shows examples of emission line fits for a one kinematic component fit (on the top panel) and for a two kinematic component fit (on the bottom panel) to visualize the meaning of the v$_{02}$ and v$_{98}$ parameters. The shaded blue (or red) area under the curve corresponds to 2% of the total area under the fitted curve. Only 2% of the fitted emission line’s flux has a velocity greater than v$_{02}$. Similarly, only 2% of the fitted emission line’s flux has a velocity lower than v$_{98}$. As seen in the lower panel of Fig. [21](#fig:v02_v98), v$_{02}$ and v$_{98}$ are especially useful for systems with two kinematic components, where they highlight asymmetries in emission lines. v$_{02}$ and v$_{98}$ maps are critical for identifying highly blueshifted and redshifted tails in nebular emission.

## Abell 1835

![](A1835_kinematics_regions.pdf)

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Region | v$_{50}$ | $\sigma$ | v$_{02}$ | v$_{98}$ | Fraction L$_{\rm[OII]\rm}$ | Dist | $\theta$ | Area |
|  | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (%) | (kpc) | ($^{\circ}$) | (kpc$^2$) |
| A | 165 | 136 | 482 | $-102$ | 21.08 | 0.0 | 0 | 52 |
| B | 227 | 164 | 633 | $-61$ | 12.61 | 8.3 | 0 | 83 |
| C | 224 | 150 | 536 | $-83$ | 2.82 | 13.2 | 297 | 122 |
| D | 51 | 111 | 312 | $-236$ | 15.73 | 13.5 | 52 | 201 |
| E | 87 | 125 | 352 | $-175$ | 5.51 | 10.7 | 264 | 88 |
| F | 211 | 100 | 416 | 5 | 0.42 | 25.1 | 45 | 39 |

: Abell 1835 regions

Table notes:\
(1) Region identified in Fig. [22](#fig:kinematics:A1835:regions).\
(2) \[OII\] flux weighted mean of the median velocity within the region.\
(3) \[OII\] flux weighted mean of the velocity dispersion within the region.\
(4) \[OII\] flux weighted mean of the v$_{02}$ within the region.\
(5) \[OII\] flux weighted mean of the v$_{98}$ within the region.\
(6) Fraction of the total \[OII\] luminosity observed from the spaxels included in the region.\
(7) Distance between the central point of the region and the nucleus.\
(8) Average angle between the center of the galaxy and the region. The angle is 0$^{\circ}$ when pointing east and increases clockwise.\
(9) Area of the region.\

![](A1835_summed_spectra1_2col.pdf)

Fig. [22](#fig:kinematics:A1835:regions) shows the same panels as in Fig. [7](#fig:kinematics:A1835) using different color scale bars to emphasize differences. Six regions, A-F, are identified on the velocity maps as regions of interest. Various properties of these regions are listed in Table [\[tab:A1835:regions\]](#tab:A1835:regions), including position, size, flux-weighted mean velocities (see equation [\[eq:flux-weighted_mean\]](#eq:flux-weighted_mean)), and relative contribution to \[OII\] luminosity.

To get a clear picture of the kinematics in each region, Fig. [23](#fig:kinematics:A1835:regions:spectra) shows the \[OII\] line doublet and the best-fit model for each of the regions identified in Fig. [22](#fig:kinematics:A1835:regions). It is worth noting that since \[OII\]3726,9 is a doublet, each component is comprised of two Gaussians, one for each doublet line. The higher signal-to-noise in the spatially-integrated spectra can reveal a second kinematic component within a region which is not always robustly detected in the individual spaxels.

Region A is a circle with a radius of $1 \ensuremath{''}$ centered on the nucleus. The ionized gas at the very center of the galaxy does not share the same velocity as its projected stellar population. The central gas is overall redshifted by 165 km s$^{-1}$ with respect to the systemic velocity.

The nebular gas in region B has the largest v$_{50}$, $\sigma$ and v$_{02}$ values observed in this system. Region B is located just north of the edge of the SE cavity, although it is not located along the axis of the cavities. The high velocity dispersion, $\geq 150$ km s$^{-1}$, indicates that the gas is disturbed. Fig. [23](#fig:kinematics:A1835:regions:spectra) shows the two component fit for region B. The second component (shown in blue) is significantly more redshifted ($\Delta \textrm{v}_{50} > +130$ km s$^{-1}$) and broader ($\Delta \sigma \sim 95$ km s$^{-1}$) than the first component (shown in red).

Region E is located on the opposite side of the nucleus, roughly at the same distance from the center as region B. While the gas in region B is redshifted with respect to the gas in the nucleus, the gas in region E is blueshifted. The spectral fits of regions A, B and E in Fig. [23](#fig:kinematics:A1835:regions:spectra) show that both kinematic components are redshifted from region A to region B, and conversely are blueshifted from region A to region E. The second, broader kinematic component has the most significant velocity differences, of order of hundreds of km s$^{-1}$. The dynamics of the nebular gas in regions A, B and E seem to indicate motion of the nebular gas along the E-W axis passing through the center.

Regions C and D are another interesting pair of regions which spatially overlap with the SE and NW X-ray cavities, respectively. Both regions are roughly 13 kpc from the nucleus. The nebular gas in region C is redshifted with respect to the central nebular gas, while the nebular gas in region D is blueshifted. The spectral fits of the \[OII\] doublet for regions A, C and D (see Fig. [23](#fig:kinematics:A1835:regions:spectra)) show significant shifts in velocities, especially for the second component with v$_{50}$ differences of more than 150 km s$^{-1}$. Additionally, there is substantial broadening of the second component in region C compared to region A, and slight broadening of the second component in region D compared to region A. The spatial overlap with X-ray cavities and the substantial velocity shifts and line broadenings are consistent with the cavities playing an important role in the nebular gas dynamics of regions C and D.

The nebular gas in region F has higher v$_{50}$ and slightly higher $\sigma$ than the surrounding gas. While this region overlaps partially with one of the projected galaxies, it is not expected to significantly affect the gas dynamics in this region, as the velocity difference of almost 1000 km s$^{-1}$ between the projected galaxy and the nebular gas argues against any interaction between them. Region F also overlaps with the northern edge of the NW cavity. However, as the edges of X-ray cavities are particularly challenging to precisely define, we cannot confidently ascertain a relation between the NW cavity and this region.

## PKS 0745-191

![](PKS0745_kinematics_regions.pdf)

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Region | v$_{50}$ | $\sigma$ | v$_{02}$ | v$_{98}$ | Fraction L$_{\rm[OII]\rm}$ | Dist | $\theta$ | Area |
|  | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (%) | (kpc) | ($^{\circ}$) | (kpc$^2$) |
| A | 130 | 267 | 889 | $-597$ | 22.81 | 1.1 | 0 | 11 |
| B | 166 | 309 | 1145 | $-350$ | 1.78 | 4.3 | 148 | 6 |
| C | 189 | 304 | 814 | $-439$ | 0.63 | 5.6 | 315 | 9 |
| D | 246 | 222 | 718 | $-187$ | 9.69 | 8.7 | 23 | 39 |
| E | 304 | 99 | 509 | 99 | 0.32 | 9.9 | 257 | 16 |
| F | 81 | 146 | 429 | $-260$ | 9.56 | 9.7 | 69 | 53 |

: PKS 0745-191 regions

Table notes:\
(1) Region identified in Fig. [24](#fig:kinematics:PKS0745:regions).\
(2) \[OII\] flux weighted mean of the median velocity within the region.\
(3) \[OII\] flux weighted mean of the velocity dispersion within the region.\
(4) \[OII\] flux weighted mean of the v$_{02}$ within the region.\
(5) \[OII\] flux weighted mean of the v$_{98}$ within the region.\
(6) Fraction of the total \[OII\] luminosity observed from the spaxels included in the region.\
(7) Distance between the central point of the region and the nucleus.\
(8) Average angle between the center of the galaxy and the region.\
(9) Area of the region.\

![](PKS0745_summed_spectra_v2.pdf)

Fig. [24](#fig:kinematics:PKS0745:regions) defines six regions of interest in the LOS kinematics map, shown as black solid ellipses. Otherwise, Fig. [24](#fig:kinematics:PKS0745:regions) is identical to Fig. [10](#fig:kinematics:PKS0745). Following the same method as in Appendix [8.2](#appendix:A1835), Table [\[tab:PKS0745:regions\]](#tab:PKS0745:regions) lists some properties of the highlighted regions and Fig. [25](#fig:kinematics:PKS0745:regions:spectra) shows the best-fit model of the spatially-integrated spectrum around the \[OII\] doublet for each region.

Region A is the central region with high velocity dispersion gas and large v$_{02}$ and v$_{98}$ values. This region includes the center of the galaxy, defined using the stellar flux. The center of region A is offset $\sim 1$ kpc east of the nucleus. The nebular gas in this central region is redshifted by +130 km s$^{-1}$. Fig. [25](#fig:kinematics:PKS0745:regions:spectra) shows that the gas associated with the second component of the fit is very disturbed, with a velocity dispersion $\sim 420$ km s$^{-1}$. Even the narrow component of the fit for region A is quite broad, with $\sigma = 162$ km s$^{-1}$. The most-redshifted gas velocities of almost $+900$ km s$^{-1}$ and the most-blueshifted velocities of almost $-600$ km s$^{-1}$ result from the extreme velocities attained by the very disturbed central gas.

Region B has the nebular gas with the largest total velocity dispersion and the most-redshifted velocities observed in this galaxy. Fig. [25](#fig:kinematics:PKS0745:regions:spectra) shows that the large $\sigma$ and v$_{02}$ values are caused by the broad and redshifted second kinematic component. The nebular gas modelled by the second kinematic component, which emits 40% of the total flux in region B, has v$_{50}$ and $\sigma$ values greater than 450 km s$^{-1}$. These dynamics are consistent with a very powerful outflow.

The gas in region C has $\sigma$ values similar to the gas in region B. However, the most-redshifted gas in region C is not as redshifted as in region B, with flux-weighted mean v$_{02}$ of $+814$ km s$^{-1}$ and $+1145$ km s$^{-1}$, respectively. Fig. [25](#fig:kinematics:PKS0745:regions:spectra) shows similarities in the integrated spectra of regions B and C. The gas associated with the first component have similar kinematics. In both regions, the second kinematic component is significantly redshifted, with v$_{50} \sim +518$ km s$^{-1}$ for region C. The main difference in the gas kinematics of regions B and C is the velocity dispersion of the second component. The gas associated with the second component in region C is disturbed, with $\sigma = 183$ km s$^{-1}$, albeit significantly less than the high velocity gas in region B where the velocity dispersion is more that 2.5 times larger. The large gas velocities of the second kinematic component in region C are consistent with an inflow or outflow of gas. The significant difference in the velocity dispersion of the high velocity gas in regions B and C hint to different mechanisms responsible for the gas dynamics in each region, with a more gentle process occurring in region C. Region C lies within the SE cavity, which may be disturbing surrounding gas and causing the several hundred km s$^{-1}$ gas motions.

Regions D and E encompass the large v$_{50}$ filament as seen in the top left panel of Fig. [24](#fig:kinematics:PKS0745:regions). The $\sigma$, v$_{02}$ and v$_{98}$ maps in Fig. [24](#fig:kinematics:PKS0745:regions) show clear differences between the upper and lower regions of the $\sim +280$ km s$^{-1}$ filament. Region D corresponds to the northern, more disturbed, part of the filament while region E represents the southern more quiescent part.

Region D encompasses the northernmost section of the redshifted filament. The gas in region D is quite disturbed, with $\sigma > 200$ km s$^{-1}$. Most of the gas in region D is modelled by the second component of the fit as shown in Fig. [25](#fig:kinematics:PKS0745:regions:spectra). The majority of the nebular gas in region D is redshifted by $\sim +300$ km s$^{-1}$ and significantly disturbed. Part of region D lies within and on the edge of the NW cavity. The large v$_{50}$ filament lies south of the NW cavity. It does not align with the nucleus-cavity axis where we would expect gas entrained by X-ray cavities to lie.

Region E contains the southern, more quiescent, part of the high v$_{50}$ filament. Fig. [25](#fig:kinematics:PKS0745:regions:spectra) shows that region E is the only region whose spatially-integrated spectrum is fitted using a single kinematic component. In region D, the first kinematic component (red) is quite faint. It becomes too faint to be detected in region E. Region E has the most redshifted total median velocities, although the gas associated with the second kinematic component in regions B and C is more redshifted. Interestingly, the gas in region E has large v$_{50}$ but low $\sigma$, such that while the nebular gas is moving at a speed of $\sim 300$ km s$^{-1}$, it is not being significantly disturbed.

Region F is the region NW of the nucleus which has low v$_{50}$ (see Fig. [24](#fig:kinematics:PKS0745:regions), upper left panel) and low $\sigma$ compared to surrounding gas (see Fig. [24](#fig:kinematics:PKS0745:regions), upper right panel). Region F partially overlaps with the NW cavity. Although the edges of the cavities are quite uncertain, the edge of the NW cavity roughly coincides with the place where the low v$_{50}$ filament separates into two filaments. The gas in region F has low velocity dispersion compared to the gas in regions A, B, C and D. However, as seen in Fig. [25](#fig:kinematics:PKS0745:regions:spectra), the broad component of the \[OII\] emission line fit in region F has $\sigma > 200$ km s$^{-1}$. A significant fraction of the nebular gas in region F is disturbed, albeit not as much as some of the other regions studied. The NW cavity may be playing an important role in the kinematics of region F, although we cannot confidently establish a link between the two structures.

## RXJ0820.9+0752

![](RXJ0820_kinematics_regions.pdf)

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Region | v$_{50}$ | $\sigma$ | v$_{02}$ | v$_{98}$ | Fraction L$_{\rm[OII]\rm}$ | Dist | $\theta$ | Area |
|  | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (%) | (kpc) | ($^{\circ}$) | (kpc$^2$) |
| A | 139 | 122 | 391 | $-114$ | 9.65 | 0.6 | 0 | 28 |
| B | 210 | 74 | 362 | 57 | 24.47 | 3.7 | 81 | 50 |
| C | 170 | 112 | 400 | $-61$ | 7.81 | 16.9 | 38 | 28 |
| D | 160 | 79 | 324 | $-4$ | 22.30 | 10.8 | 38 | 41 |
| E | 47 | 104 | 262 | $-168$ | 12.28 | 14.1 | 7 | 45 |

: RXJ0820.9+0752 regions

Table notes:\
(1) Region identified in Fig. [26](#fig:kinematics:RXJ0820:regions).\
(2) \[OII\] flux weighted mean of the median velocity within the region.\
(3) \[OII\] flux weighted mean of the velocity dispersion within the region.\
(4) \[OII\] flux weighted mean of the v$_{02}$ within the region.\
(5) \[OII\] flux weighted mean of the v$_{98}$ within the region.\
(6) Fraction of the total \[OII\] luminosity observed from the spaxels included in the region.\
(7) Distance between the central point of the region and the nucleus.\
(8) Average angle between the center of the galaxy and the region. The angle is 0$^{\circ}$ pointing east and increases clockwise.\
(9) Area of the region.\
Fig. [26](#fig:kinematics:RXJ0820:regions) depicts the same kinematic maps as in Fig. [5](#fig:kinematics:RXJ0820), using a different colormap to highlight differences in velocity. The ellipses identify five regions of interest whose properties are detailed in Table [\[tab:RXJ0820:regions\]](#tab:RXJ0820:regions).

Region A is one of two regions where the stellar continuum is detected. This region encompasses the nebular gas closest to the nucleus. With a \[OII\] flux-weighted mean v$_{50}$ of $+139$ km s$^{-1}$, region A reiterates the significant differences in kinematics between the nebular gas and the stellar continuum. This region has the largest velocity dispersion. The few spaxels with $\sigma > 150$ km s$^{-1}$ are only $\sim 1.9$ kpc SW of the nucleus.

Region B is the second region where stellar continuum is observed. Region B has the gas with the largest median velocities. Although the gas in region B has, on average, velocities greater than $+200$ km s$^{-1}$, the gas is quiescent with the lowest mean velocity dispersion ($\sigma = 74$ km s$^{-1}$) of the five regions examined. Therefore, there is either a process displacing almost 25% of the observed nebular gas at $\sim 200$ km s$^{-1}$ while barely disrupting it, and/or the stellar population in the core of the system, from which we measure the systemic velocity, is moving at $\sim 200$ km s$^{-1}$ with respect to the nebular gas in region B.

Region C is another region with large median velocities, located roughly 15 kpc away from region B. Contrary to region B, the gas in region C is somewhat disturbed, with $\sigma = 112$ km s$^{-1}$. Region B and C, the two highest v$_{50}$ regions, appear to be connected through a $\sim 160$ km s$^{-1}$ filament, which is identified in Fig. [26](#fig:kinematics:RXJ0820:regions) as region D. The velocity dispersion in region D is below 80 km s$^{-1}$, indicating that the nebular gas in region D is fairly quiescent. This “filament" contains $\sim 22\%$ of the observed nebular gas.

Region E contains the nebular gas with the smallest velocities with respect to the systemic velocity. The gas is slightly disturbed, with $\sigma \sim 104$ km s$^{-1}$. The $\sim 100$ km s$^{-1}$ change in velocities between the gas in region E and the surrounding gas may explain the increase in velocity dispersion.

natexlab

(ref: Astropy1) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy2) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy3) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Babul2013) Babul, A., Sharma, P., & Reynolds, C. S. 2013, ApJ, 768, 11, doi: [`10.1088/0004-637X/768/1/11`](http://doi.org/10.1088/0004-637X/768/1/11)

(ref: Baum_ODea1991) Baum, S. A., & O’Dea, C. P. 1991, MNRAS, 250, 737, doi: [`10.1093/mnras/250.4.737`](http://doi.org/10.1093/mnras/250.4.737)

(ref: Bayer-Kim2002) Bayer-Kim, C. M., Crawford, C. S., Allen, S. W., Edge, A. C., & Fabian, A. C. 2002, MNRAS, 337, 938, doi: [`10.1046/j.1365-8711.2002.05969.x`](http://doi.org/10.1046/j.1365-8711.2002.05969.x)

(ref: Birzan2008) Bı̂rzan, L., McNamara, B. R., Nulsen, P. E. J., Carilli, C. L., & Wise, M. W. 2008, ApJ, 686, 859, doi: [`10.1086/591416`](http://doi.org/10.1086/591416)

(ref: Birzan2004) Bı̂rzan, L., Rafferty, D. A., McNamara, B. R., Wise, M. W., & Nulsen, P. E. J. 2004, ApJ, 607, 800, doi: [`10.1086/383519`](http://doi.org/10.1086/383519)

(ref: Blanton2004) Blanton, E. L., Sarazin, C. L., McNamara, B. R., & Clarke, T. E. 2004, ApJ, 612, 817, doi: [`10.1086/422677`](http://doi.org/10.1086/422677)

(ref: Canning2011) Canning, R. E. A., Fabian, A. C., Johnstone, R. M., et al. 2011, MNRAS, 411, 411, doi: [`10.1111/j.1365-2966.2010.17693.x`](http://doi.org/10.1111/j.1365-2966.2010.17693.x)

(ref: PPXF) Cappellari, M., & Emsellem, E. 2004, PASP, 116, 138, doi: [`10.1086/381875`](http://doi.org/10.1086/381875)

(ref: Cavagnolo2008) Cavagnolo, K. W., Donahue, M., Voit, G. M., & Sun, M. 2008, ApJL, 683, L107, doi: [`10.1086/591665`](http://doi.org/10.1086/591665)

(ref: Churazov2001) Churazov, E., Brüggen, M., Kaiser, C. R., Böhringer, H., & Forman, W. 2001, ApJ, 554, 261, doi: [`10.1086/321357`](http://doi.org/10.1086/321357)

(ref: Clarke2009) Clarke, T. E., Blanton, E. L., Sarazin, C. L., et al. 2009, ApJ, 697, 1481, doi: [`10.1088/0004-637X/697/2/1481`](http://doi.org/10.1088/0004-637X/697/2/1481)

(ref: Crawford1999) Crawford, C. S., Allen, S. W., Ebeling, H., Edge, A. C., & Fabian, A. C. 1999, MNRAS, 306, 857, doi: [`10.1046/j.1365-8711.1999.02583.x`](http://doi.org/10.1046/j.1365-8711.1999.02583.x)

(ref: David2001) David, L. P., Nulsen, P. E. J., McNamara, B. R., et al. 2001, ApJ, 557, 546, doi: [`10.1086/322250`](http://doi.org/10.1086/322250)

(ref: ALMA_A262) Davis, T. A., Bureau, M., Onishi, K., et al. 2017, MNRAS, 468, 4675, doi: [`10.1093/mnras/stw3217`](http://doi.org/10.1093/mnras/stw3217)

(ref: DePropris2021) De Propris, R., West, M. J., Andrade-Santos, F., et al. 2021, MNRAS, 500, 310, doi: [`10.1093/mnras/staa3286`](http://doi.org/10.1093/mnras/staa3286)

(ref: Donahue2011) Donahue, M., de Messières, G. E., O’Connell, R. W., et al. 2011, ApJ, 732, 40, doi: [`10.1088/0004-637X/732/1/40`](http://doi.org/10.1088/0004-637X/732/1/40)

(ref: Donahue2022) Donahue, M., & Voit, G. M. 2022, Phys. Rep., 973, 1, doi: [`10.1016/j.physrep.2022.04.005`](http://doi.org/10.1016/j.physrep.2022.04.005)

(ref: Edge2001) Edge, A. C. 2001, MNRAS, 328, 762, doi: [`10.1046/j.1365-8711.2001.04802.x`](http://doi.org/10.1046/j.1365-8711.2001.04802.x)

(ref: Egami2006) Egami, E., Misselt, K. A., Rieke, G. H., et al. 2006, ApJ, 647, 922, doi: [`10.1086/504519`](http://doi.org/10.1086/504519)

(ref: Fabian1994) Fabian, A. C. 1994, ARA&A, 32, 277, doi: [`10.1146/annurev.aa.32.090194.001425`](http://doi.org/10.1146/annurev.aa.32.090194.001425)

(ref: Fabian1977) Fabian, A. C., & Nulsen, P. E. J. 1977, MNRAS, 180, 479, doi: [`10.1093/mnras/180.3.479`](http://doi.org/10.1093/mnras/180.3.479)

(ref: Fabian2003a) Fabian, A. C., Sanders, J. S., Allen, S. W., et al. 2003, MNRAS, 344, L43, doi: [`10.1046/j.1365-8711.2003.06902.x`](http://doi.org/10.1046/j.1365-8711.2003.06902.x)

(ref: Fabian2006) Fabian, A. C., Sanders, J. S., Taylor, G. B., et al. 2006, MNRAS, 366, 417, doi: [`10.1111/j.1365-2966.2005.09896.x`](http://doi.org/10.1111/j.1365-2966.2005.09896.x)

(ref: Fogarty2019) Fogarty, K., Postman, M., Li, Y., et al. 2019, ApJ, 879, 103, doi: [`10.3847/1538-4357/ab22a4`](http://doi.org/10.3847/1538-4357/ab22a4)

(ref: Gaspari2013) Gaspari, M., Ruszkowski, M., & Oh, S. P. 2013, MNRAS, 432, 3401, doi: [`10.1093/mnras/stt692`](http://doi.org/10.1093/mnras/stt692)

(ref: Gaspari2012) Gaspari, M., Ruszkowski, M., & Sharma, P. 2012, ApJ, 746, 94, doi: [`10.1088/0004-637X/746/1/94`](http://doi.org/10.1088/0004-637X/746/1/94)

(ref: Gitti2011) Gitti, M., Nulsen, P. E. J., David, L. P., McNamara, B. R., & Wise, M. W. 2011, ApJ, 732, 13, doi: [`10.1088/0004-637X/732/1/13`](http://doi.org/10.1088/0004-637X/732/1/13)

(ref: Godon1994) Godon, P., Soker, N., White, Raymond E., I., & Regev, O. 1994, AJ, 108, 2009, doi: [`10.1086/117213`](http://doi.org/10.1086/117213)

(ref: SSP2005) González Delgado, R. M., Cerviño, M., Martins, L. P., Leitherer, C., & Hauschildt, P. H. 2005, MNRAS, 357, 945, doi: [`10.1111/j.1365-2966.2005.08692.x`](http://doi.org/10.1111/j.1365-2966.2005.08692.x)

(ref: Guo2008) Guo, F., & Oh, S. P. 2008, MNRAS, 384, 251, doi: [`10.1111/j.1365-2966.2007.12692.x`](http://doi.org/10.1111/j.1365-2966.2007.12692.x)

(ref: Hamer2012) Hamer, S. L., Edge, A. C., Swinbank, A. M., et al. 2012, MNRAS, 421, 3409, doi: [`10.1111/j.1365-2966.2012.20566.x`](http://doi.org/10.1111/j.1365-2966.2012.20566.x)

(ref: Hamer2016) —. 2016, MNRAS, 460, 1758, doi: [`10.1093/mnras/stw1054`](http://doi.org/10.1093/mnras/stw1054)

(ref: Numpy2) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hatch2007) Hatch, N. A., Crawford, C. S., & Fabian, A. C. 2007, MNRAS, 380, 33, doi: [`10.1111/j.1365-2966.2007.12009.x`](http://doi.org/10.1111/j.1365-2966.2007.12009.x)

(ref: Heckman1981) Heckman, T. M. 1981, ApJL, 250, L59, doi: [`10.1086/183674`](http://doi.org/10.1086/183674)

(ref: Heckman1989) Heckman, T. M., Baum, S. A., van Breugel, W. J. M., & McCarthy, P. 1989, ApJ, 338, 48, doi: [`10.1086/167181`](http://doi.org/10.1086/167181)

(ref: Heinz2006) Heinz, S., Brüggen, M., Young, A., & Levesque, E. 2006, MNRAS, 373, L65, doi: [`10.1111/j.1745-3933.2006.00243.x`](http://doi.org/10.1111/j.1745-3933.2006.00243.x)

(ref: Heinz1998) Heinz, S., Reynolds, C. S., & Begelman, M. C. 1998, ApJ, 501, 126, doi: [`10.1086/305807`](http://doi.org/10.1086/305807)

(ref: Hogan2017) Hogan, M. T., McNamara, B. R., Pulido, F. A., et al. 2017, ApJ, 851, 66, doi: [`10.3847/1538-4357/aa9af3`](http://doi.org/10.3847/1538-4357/aa9af3)

(ref: Hu1985) Hu, E. M., Cowie, L. L., & Wang, Z. 1985, ApJS, 59, 447, doi: [`10.1086/191081`](http://doi.org/10.1086/191081)

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Johnstone2007) Johnstone, R. M., Hatch, N. A., Ferland, G. J., et al. 2007, MNRAS, 382, 1246, doi: [`10.1111/j.1365-2966.2007.12460.x`](http://doi.org/10.1111/j.1365-2966.2007.12460.x)

(ref: Kirkpatrick2011) Kirkpatrick, C. C., McNamara, B. R., & Cavagnolo, K. W. 2011, ApJL, 731, L23, doi: [`10.1088/2041-8205/731/2/L23`](http://doi.org/10.1088/2041-8205/731/2/L23)

(ref: PyNeb) Luridiana, V., Morisset, C., & Shaw, R. A. 2013, PyNeb: Analysis of emission lines, Astrophysics Source Code Library, record ascl:1304.021. [`http://ascl.net/1304.021`](http://ascl.net/1304.021)

(ref: Main2017) Main, R. A., McNamara, B. R., Nulsen, P. E. J., Russell, H. R., & Vantyghem, A. N. 2017, MNRAS, 464, 4360, doi: [`10.1093/mnras/stw2644`](http://doi.org/10.1093/mnras/stw2644)

(ref: Markevitch2007) Markevitch, M., & Vikhlinin, A. 2007, Phys. Rep., 443, 1, doi: [`10.1016/j.physrep.2007.01.001`](http://doi.org/10.1016/j.physrep.2007.01.001)

(ref: MPFIT) Markwardt, C. B. 2009, in Astronomical Society of the Pacific Conference Series, Vol. 411, Astronomical Data Analysis Software and Systems XVIII, ed. D. A. Bohlender, D. Durand, & P. Dowler, 251. [`https://arxiv.org/abs/0902.2850`](https://arxiv.org/abs/0902.2850)

(ref: Mathews2008) Mathews, W. G., & Brighenti, F. 2008, ApJ, 676, 880, doi: [`10.1086/527429`](http://doi.org/10.1086/527429)

(ref: McCourt2012) McCourt, M., Sharma, P., Quataert, E., & Parrish, I. J. 2012, MNRAS, 419, 3319, doi: [`10.1111/j.1365-2966.2011.19972.x`](http://doi.org/10.1111/j.1365-2966.2011.19972.x)

(ref: McDonald2018) McDonald, M., Gaspari, M., McNamara, B. R., & Tremblay, G. R. 2018, ApJ, 858, 45, doi: [`10.3847/1538-4357/aabace`](http://doi.org/10.3847/1538-4357/aabace)

(ref: McDonald2010) McDonald, M., Veilleux, S., Rupke, D. S. N., & Mushotzky, R. 2010, ApJ, 721, 1262, doi: [`10.1088/0004-637X/721/2/1262`](http://doi.org/10.1088/0004-637X/721/2/1262)

(ref: McNamara2007) McNamara, B. R., & Nulsen, P. E. J. 2007, ARA&A, 45, 117, doi: [`10.1146/annurev.astro.45.051806.110625`](http://doi.org/10.1146/annurev.astro.45.051806.110625)

(ref: McNamara2012) —. 2012, New Journal of Physics, 14, 055023, doi: [`10.1088/1367-2630/14/5/055023`](http://doi.org/10.1088/1367-2630/14/5/055023)

(ref: McNamara2016) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2016, ApJ, 830, 79, doi: [`10.3847/0004-637X/830/2/79`](http://doi.org/10.3847/0004-637X/830/2/79)

(ref: McNamara2006) McNamara, B. R., Rafferty, D. A., Bı̂rzan, L., et al. 2006, ApJ, 648, 164, doi: [`10.1086/505859`](http://doi.org/10.1086/505859)

(ref: McNamara2014) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2014, ApJ, 785, 44, doi: [`10.1088/0004-637X/785/1/44`](http://doi.org/10.1088/0004-637X/785/1/44)

(ref: Morrissey2018) Morrissey, P., Matuszewski, M., Martin, D. C., et al. 2018, ApJ, 864, 93, doi: [`10.3847/1538-4357/aad597`](http://doi.org/10.3847/1538-4357/aad597)

(ref: Nulsen1986) Nulsen, P. E. J. 1986, MNRAS, 221, 377, doi: [`10.1093/mnras/221.2.377`](http://doi.org/10.1093/mnras/221.2.377)

(ref: Nulsen2013) Nulsen, P. E. J., & McNamara, B. R. 2013, Astronomische Nachrichten, 334, 386, doi: [`10.1002/asna.201211863`](http://doi.org/10.1002/asna.201211863)

(ref: ODea2008) O’Dea, C. P., Baum, S. A., Privon, G., et al. 2008, ApJ, 681, 1035, doi: [`10.1086/588212`](http://doi.org/10.1086/588212)

(ref: ODea2010) O’Dea, K. P., Quillen, A. C., O’Dea, C. P., et al. 2010, ApJ, 719, 1619, doi: [`10.1088/0004-637X/719/2/1619`](http://doi.org/10.1088/0004-637X/719/2/1619)

(ref: Olivares2019) Olivares, V., Salome, P., Combes, F., et al. 2019, A&A, 631, A22, doi: [`10.1051/0004-6361/201935350`](http://doi.org/10.1051/0004-6361/201935350)

(ref: Osterbrock2006) Osterbrock, D. E., & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Peterson2006) Peterson, J. R., & Fabian, A. C. 2006, Phys. Rep., 427, 1, doi: [`10.1016/j.physrep.2005.12.007`](http://doi.org/10.1016/j.physrep.2005.12.007)

(ref: Pizzolato2005) Pizzolato, F., & Soker, N. 2005, ApJ, 632, 821, doi: [`10.1086/444344`](http://doi.org/10.1086/444344)

(ref: Pope2010) Pope, E. C. D., Babul, A., Pavlovski, G., Bower, R. G., & Dotter, A. 2010, MNRAS, 406, 2023, doi: [`10.1111/j.1365-2966.2010.16816.x`](http://doi.org/10.1111/j.1365-2966.2010.16816.x)

(ref: Pradhan2006) Pradhan, A. K., Montenegro, M., Nahar, S. N., & Eissner, W. 2006, MNRAS, 366, L6, doi: [`10.1111/j.1745-3933.2005.00119.x`](http://doi.org/10.1111/j.1745-3933.2005.00119.x)

(ref: Pulido2018) Pulido, F. A., McNamara, B. R., Edge, A. C., et al. 2018, ApJ, 853, 177, doi: [`10.3847/1538-4357/aaa54b`](http://doi.org/10.3847/1538-4357/aaa54b)

(ref: Rafferty2008) Rafferty, D. A., McNamara, B. R., & Nulsen, P. E. J. 2008, ApJ, 687, 899, doi: [`10.1086/591240`](http://doi.org/10.1086/591240)

(ref: Rafferty2006) Rafferty, D. A., McNamara, B. R., Nulsen, P. E. J., & Wise, M. W. 2006, ApJ, 652, 216, doi: [`10.1086/507672`](http://doi.org/10.1086/507672)

(ref: Revaz2008) Revaz, Y., Combes, F., & Salomé, P. 2008, A&A, 477, L33, doi: [`10.1051/0004-6361:20078915`](http://doi.org/10.1051/0004-6361:20078915)

(ref: Rose2019) Rose, T., Edge, A. C., Combes, F., et al. 2019, MNRAS, 485, 229, doi: [`10.1093/mnras/stz406`](http://doi.org/10.1093/mnras/stz406)

(ref: Rupke2014a) Rupke, D. S. N. 2014a, IFSRED: Data Reduction for Integral Field Spectrographs, Astrophysics Source Code Library, record ascl:1409.004. [`http://ascl.net/1409.004`](http://ascl.net/1409.004)

(ref: Rupke2014b) —. 2014b, IFSFIT: Spectral Fitting for Integral Field Spectrographs, Astrophysics Source Code Library, record ascl:1409.005. [`http://ascl.net/1409.005`](http://ascl.net/1409.005)

(ref: Russell2016) Russell, H. R., McNamara, B. R., Fabian, A. C., et al. 2016, MNRAS, 458, 3134, doi: [`10.1093/mnras/stw409`](http://doi.org/10.1093/mnras/stw409)

(ref: Russell2019) —. 2019, MNRAS, 490, 3025, doi: [`10.1093/mnras/stz2719`](http://doi.org/10.1093/mnras/stz2719)

(ref: Ruszkowski2004a) Ruszkowski, M., Brüggen, M., & Begelman, M. C. 2004a, ApJ, 611, 158, doi: [`10.1086/422158`](http://doi.org/10.1086/422158)

(ref: Ruszkowski2004b) —. 2004b, ApJ, 615, 675, doi: [`10.1086/424702`](http://doi.org/10.1086/424702)

(ref: Ruszkowski2008) Ruszkowski, M., Enßlin, T. A., Brüggen, M., Begelman, M. C., & Churazov, E. 2008, MNRAS, 383, 1359, doi: [`10.1111/j.1365-2966.2007.12659.x`](http://doi.org/10.1111/j.1365-2966.2007.12659.x)

(ref: SC2003) Salomé, P., & Combes, F. 2003, A&A, 412, 657, doi: [`10.1051/0004-6361:20031438`](http://doi.org/10.1051/0004-6361:20031438)

(ref: Salome&Combes2004) Salomé, P., & Combes, F. 2004, in SF2A-2004: Semaine de l’Astrophysique Francaise, ed. F. Combes, D. Barret, T. Contini, F. Meynadier, & L. Pagani, 505

(ref: Sanders2014) Sanders, J. S., Fabian, A. C., Hlavacek-Larrondo, J., et al. 2014, MNRAS, 444, 1497, doi: [`10.1093/mnras/stu1543`](http://doi.org/10.1093/mnras/stu1543)

(ref: Scannapieco2008) Scannapieco, E., & Brüggen, M. 2008, ApJ, 686, 927, doi: [`10.1086/591228`](http://doi.org/10.1086/591228)

(ref: Sharma2012) Sharma, P., McCourt, M., Quataert, E., & Parrish, I. J. 2012, MNRAS, 420, 3174, doi: [`10.1111/j.1365-2966.2011.20246.x`](http://doi.org/10.1111/j.1365-2966.2011.20246.x)

(ref: Simionescu2009) Simionescu, A., Werner, N., Böhringer, H., et al. 2009, A&A, 493, 409, doi: [`10.1051/0004-6361:200810225`](http://doi.org/10.1051/0004-6361:200810225)

(ref: Tamhane2022) Tamhane, P. D., McNamara, B. R., Russell, H. R., et al. 2022, MNRAS, 516, 861, doi: [`10.1093/mnras/stac2168`](http://doi.org/10.1093/mnras/stac2168)

(ref: Ubertosi2021) Ubertosi, F., Gitti, M., Brighenti, F., et al. 2021, ApJL, 923, L25, doi: [`10.3847/2041-8213/ac374c`](http://doi.org/10.3847/2041-8213/ac374c)

(ref: vandenBosch2005) van den Bosch, F. C., Weinmann, S. M., Yang, X., et al. 2005, MNRAS, 361, 1203, doi: [`10.1111/j.1365-2966.2005.09260.x`](http://doi.org/10.1111/j.1365-2966.2005.09260.x)

(ref: Numpy1) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: Python3) Van Rossum, G., & Drake, F. L. 2009, Python 3 Reference Manual (Scotts Valley, CA: CreateSpace)

(ref: Vantyghem2017) Vantyghem, A. N., McNamara, B. R., Edge, A. C., et al. 2017, ApJ, 848, 101, doi: [`10.3847/1538-4357/aa8fd0`](http://doi.org/10.3847/1538-4357/aa8fd0)

(ref: Vantyghem2018) Vantyghem, A. N., McNamara, B. R., Russell, H. R., et al. 2018, ApJ, 863, 193, doi: [`10.3847/1538-4357/aad2e0`](http://doi.org/10.3847/1538-4357/aad2e0)

(ref: Vantyghem2019) —. 2019, ApJ, 870, 57, doi: [`10.3847/1538-4357/aaf1b4`](http://doi.org/10.3847/1538-4357/aaf1b4)

(ref: Vernaleo2006) Vernaleo, J. C., & Reynolds, C. S. 2006, ApJ, 645, 83, doi: [`10.1086/504029`](http://doi.org/10.1086/504029)

(ref: Vigneron2024) Vigneron, B., Hlavacek-Larrondo, J., Rhea, C. L., et al. 2024, ApJ, 962, 96, doi: [`10.3847/1538-4357/ad0fd8`](http://doi.org/10.3847/1538-4357/ad0fd8)

(ref: SciPy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Voit2005) Voit, G. M., & Donahue, M. 2005, ApJ, 634, 955, doi: [`10.1086/497063`](http://doi.org/10.1086/497063)

(ref: Voit2015) Voit, G. M., Donahue, M., Bryan, G. L., & McDonald, M. 2015, Nature, 519, 203, doi: [`10.1038/nature14167`](http://doi.org/10.1038/nature14167)

(ref: Zuhone2016) Zuhone, J. A., & Roediger, E. 2016, Journal of Plasma Physics, 82, 535820301, doi: [`10.1017/S0022377816000544`](http://doi.org/10.1017/S0022377816000544)

</paper>

Write the methods card for this paper.