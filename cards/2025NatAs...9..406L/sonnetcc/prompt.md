# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9..406L\sonnetcc\reply.txt

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
 "bibcode": "2025NatAs...9..406L",
 "title": "Inadequate turbulent support in low-metallicity molecular clouds",
 "year": 2025,
 "journal": "Nature Astronomy",
 "first_author": "Lin, Lingrui",
 "n_authors": 19,
 "arxiv_id": "2501.07636",
 "doi": "10.1038/s41550-024-02440-3",
 "alma_projects_linked_by_archive": [
  "2013.1.00652.S",
  "2015.1.00581.S",
  "2019.1.01641.S",
  "2021.2.00175.S"
 ]
}
```

Paper text:
<paper>
# Inadequate turbulent support in low-metallicity molecular clouds

Larson’s relations(cite: 1981MNRAS.194..809L) have been well established both in the Milky Way (cite: 1981MNRAS.194..809L; 1987ApJ...319..730S; 2009ApJ...699.1092H; 2017ApJ...834...57M) and in external galaxies (cite: 2008ApJ...686..948B; 2010ARA&A..48..547F; 2010MNRAS.406.2065H; 2017ApJ...835..278S; 2019ApJ...885...50W; 2023A&A...672A.153S). They consist of power-law relations among the size, velocity dispersion, and mass of molecular clouds. Such relations are often considered as the outcome of virial equilibrium (cite: 1981MNRAS.194..809L; 1989ApJ...338..178E) (or energy equipartition (cite: 2006MNRAS.372..443B); Methods) between the turbulent kinetic energy ($E_{\rm k}$) and the self-gravitational energy ($E_{\rm g}$) of a molecular cloud, which is characterized by the virial parameter ($\alpha_{\rm vir} = 2E_{\rm k}/|E_{\rm g}|$)(cite: 1992ApJ...395..140B) that is typically near unity(cite: 1981MNRAS.194..809L; 1987ApJ...319..730S; 2009ApJ...699.1092H). Molecular clouds resolved in the Galactic Centre and in some external galaxies seem to have a slight preference towards supervirial states ($\alpha_{\rm vir}>$1), possibly due to external pressure on cloud boundaries (cite: 2018ApJ...860..172S) or tidal shear around the cloud envelopes (cite: 2016ApJ...832..143F; 2021MNRAS.505.4048L; 2023MNRAS.525..962P). The virial equilibrium assumption has been used in a variety of contexts, such as for calibrating the standard value of the so-called CO-to-H$_{2}$ conversion factor ($X_{\rm CO}$) (cite: 2013ARA&A..51..207B), for estimating the average turbulent gas pressure in high-redshift galaxies (cite: 2011ApJ...742...11S) and for setting the initial conditions of star formation in numerical simulations (cite: 2003ApJ...585..850M; 2017A&A...605A..97V).

Nevertheless, most previous studies on the dynamic states of molecular clouds were based solely on the more luminous but optically thick low-$J$ $^{12}$CO transitions (cite: 1987ApJ...319..730S; 2017ApJ...834...57M). The uncertainty of $X_{\rm CO}$ values (cite: 2013ARA&A..51..207B), the opacity broadening (cite: 2016A&A...591A.104H) and the radiative trapping of $^{12}$CO lines (Methods; the latter can keep $^{12}$CO lines luminous even for low-density outer-cloud envelope gas, which may not be gravitationally bound) undoubtedly complicate $\alpha_{\rm vir}$ estimates for molecular clouds.

Rotational transitions of the rarer $^{13}$CO molecule (cite: 1994ARA&A..32..191W), on the other hand, are optically thin for the bulk of the mass in molecular clouds in most cases (cite: 2009ApJS..182..131R). Therefore, the low-$J$ $^{13}$CO lines can more faithfully trace H$_2$ mass and velocity dispersion (cite: 2009ApJ...699.1092H) than the $^{12}$CO lines. However, because of their faintness, studies of cloud dynamics based on $^{13}$CO lines are mostly limited to within a Galactocentric radius ($R_{\rm gc}$) of less than 12 kpc (refs. ), which includes the solar neighbourhood (cite: 1981MNRAS.194..809L) and the inner Galaxy (cite: 2009ApJ...699.1092H; 2010ApJ...723..492R; 2019A&A...632A..58R) but leaves the Galactic outer disk less explored.

The Galactic outer disk, namely, the portion of the disk beyond the solar circle ($R_{\rm gc}>R_{\rm gc,\odot} \approx 8$ kpc)(cite: knapen2017outskirts), features very different physical conditions, such as low midplane pressure(cite: 2003ApJ...587..278W), a low turbulence injection level (cite: 2017ApJ...834...57M) and low gas-phase metallicity ($Z$, routinely traced by the oxygen abundance, O/H)(cite: 2022MNRAS.510.4436M). Such environments reflect not only the early formation stage of the Galactic thin disk(cite: chiappini2008chemical) but also the general properties of gas-rich, metal-poor galaxies (cite: 2014Natur.514..335S; 2014A&A...561A..49H).

In this work, we performed mapping observations of the $^{13}$CO $J=1\rightarrow0$ and $J=2\rightarrow1$ transitions for a sample of molecular clouds in the Galactic outer disk ($9<R_{\rm gc}<25$ kpc), using the Institut de radioastronomie millimétrique (IRAM) 30 m telescope, the single-dish telescope (Total Power (TP) Array) of the Atacama Large Millimeter/submillimeter Array (ALMA) and the Submillimeter Telescope (SMT). Figure [1](#fig: Main_Fig1) shows the spatial distribution of our samples on the Galactic plane.

![](fig/Main_Fig1.pdf)

We first derived the surface density of $^{13}$CO ($N_{\rm ^{13}CO}$) from the $^{13}$CO emission and then obtained the H$_2$ surface density ($N_{\rm H_{2}}$) with the H$_2$/$^{13}$CO abundance ratio estimated from the Galactic radial gradients of $^{12}$C/$^{13}$C (ref. ) and O/H (ref. ; Methods). For each cloud, we measured the equivalent cloud radius ($R_{\rm cloud}$), the velocity dispersion ($\sigma_{\rm v}$) and the molecular gas mass ($M_{\rm mol}$), all within the half-peak isophote of $N_{\rm H_{2}}$ (Methods). Cloud distances were estimated based on the Galactic rotation curve model from the Bar and Spiral Structure Legacy (BeSSeL) survey (cite: 2019ApJ...885..131R).

For comparison, we retrieved archival $^{13}$CO $J=1\rightarrow0$ and $J=2\rightarrow1$ data from the inner Galaxy (cite: 2009ApJ...699.1092H) and nearby metal-poor dwarf galaxies, namely, the Large Magellanic Cloud (cite: 2019ApJ...885...50W) (LMC; $Z\approx0.5$ Z$_{\odot}$; ref. ), the Small Magellanic Cloud (cite: 2018ApJ...853..111J) (SMC; $Z\approx0.2$ Z$_{\odot}$; ref. ) and NGC 6822 ($Z\approx0.2$ Z$_{\odot}$) (cite: 2016A&A...586A..59G). We also took the physical properties of molecular clumps from an extremely metal-poor dwarf galaxy DDO 70 ($Z\approx0.07$ Z$_{\odot}$) from the literature(cite: 2020ApJ...892..147S).

Figure [2](#fig: Main_Fig2)a shows that the velocity dispersion $\sigma_{\rm v}$ of the Galactic molecular clouds decreases from $R_{\rm gc}=5$ kpc to 15 kpc, with this trend becoming flat at $R_{\rm gc}>15$ kpc. This is consistent with the results from a low-resolution $^{12}$CO $J=1\approx0$ survey on a tens of parsecs scale (cite: 2017ApJ...834...57M) and may be related to the decreasing kinetic energy injection towards the outer Galaxy (Methods). Figure [2](#fig: Main_Fig2)b presents $\sigma_{\rm v}$ versus $R_{\rm cloud}$, showing that, although molecular clouds at $R_{\rm gc}<$ 15 kpc roughly follow the classical Larson’s $\sigma_{\rm v}$ versus $R_{\rm cloud}$ relation (cite: 1981MNRAS.194..809L), those at $R_{\rm gc}>$ 15 kpc and those from metal-poor dwarf galaxies have a lower $\sigma_{\rm v}$ than what would be expected from Larson’s relation. Such a discrepancy has also been revealed by $^{12}$CO line observations of metal-poor dwarf galaxies, including the Magellanic Clouds (cite: 2008ApJ...686..948B; 2023ApJ...949...63O).

![image](fig/Main_Fig2a.pdf) ![image](fig/Main_Fig2b.pdf)

Figure [3](#fig: Main_Fig3) shows that the $\alpha_{\rm vir}$ of molecular clouds, from both the Milky Way and metal-poor dwarf galaxies, systematically varies as a function of the gas-phase metallicity. The gas-phase metallicities of the Galactic clouds were estimated using the Galactic radial gradient of O/H (ref. ). $\alpha_{\rm vir}$ decreases from supervirial states ($\alpha_{\rm vir}>1$) in the metal-rich inner Galaxy to subvirial states ($\alpha_{\rm vir}<1$) towards the metal-poor outer Galaxy with $R_{\rm gc}>15$ kpc ($Z<0.5$ Z$_{\odot}$). The slope of this correlation is sensitive to the adopted H$_2$/$^{13}$CO abundance ratio gradient. Nevertheless, the overall trend is robust due to the monotonically decreasing Galactic radial gradients for both $^{12}$C/$^{13}$C and the gas-phase metallicity. Molecular clouds from metal-poor dwarf galaxies, that is, the LMC ($Z\approx0.5$ Z$_{\odot}$)(cite: 1992ApJ...384..508R), the SMC ($Z\approx0.2$ Z$_{\odot}$)(cite: 2003ASPC..304..187P), NGC 6822 ($Z \approx 0.2$ Z$_{\odot}$)(cite: 2016A&A...586A..59G) and DDO 70 ($Z \sim 0.07$ Z$_{\odot}$)(cite: 2020ApJ...892..147S), extend the $\alpha_{\rm vir}$versus $Z$ trend to the extremely low-metallicity end, despite that these systems have a variety of stellar contents, star-formation properties and galactic dynamic conditions. Consequently, we found that the classical virial equilibrium between $E_{\rm k}$ and $E_{\rm g}$ of molecular clouds is not universal.

![](fig/Main_Fig3.pdf)

Although by definition $\alpha_{\rm vir}$ includes only $E_{\rm k}$ and $E_{\rm g}$, the general virial theorem (cite: spitzer2008physical; 1989ApJ...338..178E; 1992ApJ...395..140B) (Methods) also contains terms dependent on the volumetric magnetic field ($B$) and the cloud-boundary pressure ($P_{\rm e}$). These other mechanisms can support and confine molecular clouds, respectively (cite: 1989ApJ...338..178E; 1992ApJ...395..140B).

The subvirial clouds found at $Z<0.5$ Z$_{\odot}$ ($R_{\rm gc}>15$ kpc) indicate that the turbulent velocity fields alone are not sufficient to counterbalance the cloud self-gravity in such low-metallicity conditions. To sustain the survival of the clouds, another mechanism is necessary. The most plausible mechanism appears to be the magnetic field (Methods).

Using the general virial theorem and assuming efficient momentum transfer between ions and neutral species (cite: 1998ApJ...503..689W), we found that the $B$-field strengths required to support subvirial clouds are consistent with expectations. These are based on the $B$ versus $n_{\rm H}$ relation benchmarked in the solar neighborhood and the inner Galaxy (cite: 2010ApJ...725..466C) ($n_{\rm H}$, volume density of hydrogen nuclei; Methods). Therefore, the subvirial clouds in metal-poor conditions do not require a stronger $B$ field than those in the metal-rich inner Galaxy. At low metallicities, the same $B$-field strength can overtake turbulence in balancing the self-gravity of a cloud.

The conditions necessary for such subvirial states may arise from the distinct physical properties typical of low-metallicity environments (Methods). These include reduced turbulence in atomic gas (cite: 2023ApJ...954...38K) and a higher ionization fraction in molecular gas. The latter would enhance the coupling between $B$-field lines and gas(cite: lequeux2004interstellar), allowing the magnetic field to play a more dominant role in counteracting self-gravity compared to high-metallicity regimes.

The supervirial molecular clouds from the metal-rich inner Galaxy, on the other hand, are probably the result of enhanced gas pressures at cloud boundaries ($P_{\rm e}/k\approx10^{4}-10^{7}$ K cm$^{-3}$), as previously proposed in the literature (cite: 2011MNRAS.416..710F). Other factors, such as cloud-boundary magnetic fields, tidal effects (cite: 2016ApJ...832..143F; 2021MNRAS.505.4048L; 2023MNRAS.525..962P) and even embedded stellar objects (cite: 2022MNRAS.515.2822R), can all drive $\alpha_{\rm vir}$ above unity (Methods).

Regardless of the detailed mechanisms driving the supervirial and subvirial conditions, the dynamic states of molecular clouds seem to depend strongly on the ambient environments. This will inevitably impact all star formation theories, given that the dynamic states of molecular clouds are crucial aspects of the initial conditions for star formation in galaxies. The subvirial states found in low-$Z$ molecular clouds, in particular, are expected to be consequential for star formation in several environments, such as the outskirts of main-sequence galaxies (still metal-poor), dwarf galaxies and galaxies at cosmic dawn (cite: 2023NatAs...7..622C).

# Methods

## Observations towards the Galactic outer disk clouds

**$\bullet$ IRAM 30 m telescope observations.** Observations with the IRAM 30 m telescope were executed from 29 August to 5 September 2017 (Project ID 031-17, principal investigator (PI) Z.-Y. Zhang) and from 3 to 30 Janunary 2023 (Project ID 102-22, PI T. Bisbas). The targets were selected from the literature (cite: 1989A&AS...80..149W; 2015ApJ...798L..27S; 2016RAA....16...47L; 2017ApJS..230...17S), based on both their $^{12}$CO brightness and Galactocentric radius.

In Project 031-17, we performed on-the-fly (OTF) mapping observations towards 14 molecular clouds in the outer Galactic disk. We used the Eight MIxer Receiver (EMIR) at 3 mm (E0), which was equipped with the fast Fourier transform spectrometer in FTS200 mode, to target the $^{13}$CO $J=1\rightarrow0$ transition. The spectral resolution was 195 kHz, corresponding to a velocity resolution of $\sim 0.53 \; \rm km\;s^{-1}$ at the rest frequency of $^{13}$CO $J=1\rightarrow0$ (110.20135430 GHz). The mapping area towards each target was $2.5'\times2.5'$ along both right ascension and declination. The step between each OTF scan of rows and columns was $9''$, and the separation between each integration was $4.8''$, enabling a super-Nyquist sampling of the half power beam-width ($\theta_{\rm beam}\approx23.5''$).

The OTF mapping data were reduced with `GILDAS/CLASS`. Platforming effects were firstly removed by separately fitting and subtracting the baselines of each FTS200 unit. We extracted a velocity interval centred at the $^{13}$CO $J=1\rightarrow0$ line with a width of $\sim18$ times the full width of half maximum linewidth. We used the `xy_map` task to build regular $^{13}$CO spectral cubes with pixel sizes of 4$''\times$4$''$. Given a main beam efficiency ($\eta_{\rm beam}$) of 0.78 (<https://publicwiki.iram.es/Iram30mEfficiencies>), the typical root-mean-square (r.m.s.) main beam temperature ($T_{\rm mb,rms}$) was $\sim$ 0.13 K.

In Project 102-22, we mapped ten outer disk molecular clouds, covering the $J=1\rightarrow0$ lines of $^{12}$CO and $^{13}$CO using the E0 receiver. The step between each OTF scan of rows and columns was $4.5''$ and the separation between each integration was $2.6''$. We reduced the data and built the spectral cubes following the same procedure used for Project 031-17. The typical $T_{\rm mb,rms}\approx0.08$ K. Two of the ten targets were excluded in this work due to their low signal-to-noise ratio ($S/N$).

**$\bullet$ ALMA TP Array observations.** The ALMA observations (Project ID 2021.2.00175.S, PI L. Lin) were executed during ALMA cycle 8 from 29 January to 28 September 2022. The $J=2\rightarrow1$ transitions of $^{12}$CO and $^{13}$CO were covered. The targets were selected from the literature (cite: 1989A&AS...80..149W). We obtained $4'\times4'$ OTF maps towards 26 outer-disk molecular clouds in the third Galactic quadrant ($180^{\circ}<l<270^{\circ}$ where $l$ is the Galactic longitude) with the ALMA TP Array. The data were reduced with the standard pipeline. The $\theta_{\rm beam}$ and the velocity resolution at the rest frequency of $^{13}$CO $J=2\rightarrow1$ (220.39868420 GHz) were $\sim29.5''$ and 0.16 $\rm \;km\;s^{-1}$, respectively. The typical $T_{\rm mb,rms}\approx0.04$ K.

**$\bullet$ SMT observations.** The SMT observations (Project ID Lin_L_22B_1, PI L. Lin) were executed from 29 October to 1 November 2022. We obtained $4'\times4'$ OTF maps towards 13 outer-disk molecular clouds(cite: 1989A&AS...80..149W; 2015ApJ...798L..27S), nine of which had $^{13}$CO $J=1\rightarrow0$ observations made by IRAM 30 m telescope. Therefore, only four targets are included in this work. The $J=2\rightarrow1$ transitions of $^{12}$CO and $^{13}$CO were covered. The step between each OTF scan of rows/columns was $10''$, and the separation between each integration was $\sim1.3''$, enabling a super-Nyquist sampling of $\theta_{\rm beam}\approx36''$. The velocity resolution was 0.34 $\rm \;km\;s^{-1}$. Given $\eta_{\rm beam}=0.70$, the typical $T_{\rm mb,rms}\approx0.14$ K.

The numbers of molecular clouds observed by us at 9 kpc $\leq R_{\rm gc}<$ 15 kpc, 15 kpc $\leq R_{\rm gc}<$ 20 kpc, and $R_{\rm gc}\geq$ 20 kpc are 33, 13, and six, respectively.

## Archival data

**$\bullet$ Galactic Ring Survey $^{13}$CO $J=1\rightarrow0$ data from the inner Galaxy.** We retrieved the $^{13}$CO $J=1\rightarrow0$ data for a sample of inner disk molecular clouds (cite: 2009ApJ...699.1092H) studied by the Galactic Ring Survey (GRS)(cite: 2006ApJS..163..145J). The spatial sampling step of GRS was $22''$, enabling a Nyquist sampling of the telescope beam ($\theta_{\rm beam}=46''$)(cite: 2006ApJS..163..145J). Given a main beam efficiency $\eta_{\rm mb}=0.46$, the typical r.m.s. main beam temperature is 0.27 K at the velocity resolution of 0.21 km s$^{-1}$. We visually excluded clouds suffering from severe line-of-sight (LoS) cloud blending. Our measurements are consistent with previous work (cite: 2009ApJ...699.1092H).

**$\bullet$ ALMA archival data of nearby galaxies.** With the capability of the ALMA 12-m array, molecular clouds in the nearby galaxies can be resolved on parsec scales.

- **LMC.** We used the $^{13}$CO cubes provided in the literature(cite: 2019ApJ...885...50W) for several regions in the LMC. Specifically, we included the $^{13}$CO $J=1\rightarrow0$ cubes (ALMA 12 m only) for N59C, A439, GMC104 and GMC1, and the $^{13}$CO $J=2\rightarrow1$ cube (ALMA 12 m plus the TP Array) for the Planck cold cloud. All cubes have a restored $\theta_{\rm beam}=3.5''$, corresponding to a physical resolution of 0.8 pc at the distance of the LMC. The r.m.s noise of the brightness temperature was $\sim0.2$ K at a velocity resolution of 0.2 km s$^{-1}$.

- **SMC.** We retrieved ALMA $^{13}$CO $J=2\rightarrow1$ data from the ALMA archival system (Project IDs 2013.1.00652.S and 2015.1.00581.S)(cite: 2018ApJ...853..111J). Four regions in the SMC (N22, SWBarN, SWBarS and SWDarkPK) were observed using the Atacama Compact Array (7 m array plus the TP Array; 2013.1.00652.S) and the ALMA 12 m array (2015.1.00581.S). The interferometry data (12 m plus 7 m arrays) were calibrated with the CASA pipeline (v4.5.2-r36115 and v4.2.2-r30986). The imaging was done by `tclean` in CASA v6.5.3. The ideal angular resolution of these observations was $\sim1''$. For consistency, however, we imaged the interferometry data with $weighting=`briggs$’ ($robust=2.0$), $cell=0.4''$ and $restoringbeam=2.0''$. The channel width of the cleaned cubes was 0.2 km s$^{-1}$. The interferometry cubes were combined with the product TP cubes using the `feather` task. The typical r.m.s. brightness temperature was $\sim0.4$ K ($\sim$ 0.06 Jy per beam).

- **NGC 6822.** For NGC 6822, we retrieved the $^{13}$CO $J=1\rightarrow0$ data observed by ALMA 12 m array (Project ID 2019.1.01641.S). We calibrated the data with the standard CASA pipeline. The imaging was done by `tclean` in CASA v6.5.3. For a compromise between angular resolution and sensitivity, we imaged the data with $weighting=`briggs$’ ($robust=2.0$), $cell=0.3''$ and $restoringbeam=2.4''$. The channel width was $\sim$ 2.7 km s$^{-1}$. The typical r.m.s. brightness temperature was $\sim0.01$ K ($\sim$ 0.6 mJy per beam).

  We visually identified molecular clouds in the LMC, SMC and NGC 6822. To exclude clouds that were mixed with several components along the LoS, we kept only those isolated clouds for which the half-peak isophote of $N_{\rm H_{2}}$ was a single closed contour. Clouds with radii smaller than half of the resolution beam were excluded.

- **DDO 70.** We included five molecular clumps detected in a local extremely metal-poor galaxy, DDO 70 ($Z\approx0.07$ Z$_{\odot}$, at a distance of 1.38 Mpc) (cite: 2020ApJ...892..147S). Even though these clouds were identified through the $^{12}$CO $J=2\rightarrow1$ emission, the cloud properties were measured independently of the uncertain $X_{\rm CO}$ (ref. (cite: 2020ApJ...892..147S)).

Supplementary Table [\[tab: ED_Table1\]](#tab: ED_Table1) summarizes the details of the above new observations and archival data.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Location | $R_{\rm gc}$ | $Z$ | $^{13}$CO transition | Number | $\Delta V_{\rm ins}$ | $\theta_{\rm beam}$ | $T_{\rm b,rms}$ | Phy. Res. |
|  | (kpc) | (Z$_{\odot}$) | ($J\rightarrow\,J-1$) |  | ($\rm \;km\;s^{-1}$) | ($''$) | \(K\) | (pc) |
| Outer Galaxy | 12.2 - 24.0 | 0.2 - 0.7 | $1\rightarrow0$ | 14 | 0.53 | 23.5 | 0.13 | 0.56 - 2.0 |
| Outer Galaxy | 16.1 - 23.0 | 0.2 - 0.4 | $1\rightarrow0$ | 8 | 0.53 | 23.5 | 0.08 | 1.1 - 1.9 |
| Outer Galaxy | 9.8 - 17.8 | 0.4 - 0.8 | $2\rightarrow1$ | 26 | 0.16 | 29.5 | 0.04 | 0.24 - 1.4 |
| Outer Galaxy | 15.7 - 16.6 | 0.4 - 0.5 | $2\rightarrow1$ | 4 | 0.34 | 36.0 | 0.14 | 1.7 - 1.8 |
| Inner Galaxy | 3.2 - 7.4 | 1.1 - 1.7 | $1\rightarrow0$ | 72 | 0.21 | 46.0 | 0.27 | 0.56 - 2.0 |
| LMC | — | 0.5 | $1\rightarrow0/2\rightarrow1$ | 62 | 0.20/0.50 | 3.5 | 0.2 | 0.85 |
| SMC | — | 0.2 | $2\rightarrow1$ | 37 | 0.20 | 2.0 | 0.6 | 0.60 |
| NGC 6822 | — | 0.2 | $1\rightarrow0$ | 6 | 2.7 | 2.4 | 0.01 | 5.5 |
| DDO 70 | — | 0.07 | — | 5 | 0.4 | 0.2 | 0.5 | 1.47 |

$^a$ IRAM 30-m (2017), $^b$ IRAM 30-m (2023), $^c$ ALMA Total Power (Cycle 8), $^d$ SMT (2022), $^e$ FCRAO 14-m (The Galactic Ring Survey)(cite: 2006ApJS..163..145J; 2009ApJ...699.1092H), $^f$ ALMA 12-m/7-m/Total Power LMC(cite: 2019ApJ...885...50W), $^g$ ALMA 12-m/7-m/Total Power SMC(cite: 2018ApJ...853..111J), $^h$ ALMA 12-m, $^i$ ALMA 12-m(cite: 2020ApJ...892..147S)

## Distances and Galactocentric radii

We derived the heliocentric distances ($d$) and Galactocentric radii ($R_{\rm gc}$) of the Galactic molecular clouds using the code provided by the BeSSeL survey (cite: 2019ApJ...885..131R). The Galactic rotation curve and spiral arm models were produced by measuring the trigonometric parallaxes and proper motions of $\sim 200$ molecular masers from the BeSSeL and the Japanese VLBI (very-long-baseline interferometry) Exploration of Radio Astrometry project. All Galactic molecular clouds studied in this work are close to the Galactic plane (Galactic latitude $|b|<4^{\circ}$), so the heights from the Galactic plane were negligible. The Galactocentric radius is, therefore, given by $$\begin{equation}
R_{\rm gc}=\sqrt{R_{\rm gc,\; \odot}^{2}+d^{2}-2R_{\rm gc,\; \odot}d{\rm cos}(l)},
\end{equation}$$ where $R_{\rm gc, \odot}=8.15$ kpc is the Galactocentric radius of the Sun (cite: 2019ApJ...885..131R).

The inputs for the code are the Galactic longitude ($l$), Galactic latitude ($b$) and the local standard of rest velocity ($V_{\rm LSR}$). The code calculates the probability density function (PDF) of cloud distance through a Bayesian approach (‘Data Availability’), from which the heliocentric distances ($d$) and their uncertainties were inferred. For each cloud, we used the most probable distance and the associated error given by the Bayesian inference.

The PDF for the cloud distance was calculated by multiplying PDFs of (1) the association with a spiral arm model, (2) the kinematic distance from the rotation curve and (3) the vicinity to parallax sources. Each of these was weighted to construct the final PDF. However, because the spiral arm model in the far outer Galaxy ($R_{\rm gc}\gtrsim15$ kpc) was poorly constrained (cite: 2019ApJ...885..131R), we excluded the spiral arm model for all Galactic molecular clouds. Our results were not influenced, regardless of whether the spiral arm models were implemented. For most outer-disk clouds, there were no nearby parallax sources. Consequently, we adopted their kinematic distances based on the Galactic rotation curve.

For molecular clouds in the LMC, the SMC and NGC 6822, we adopted $d_{\rm LMC}=49.59\pm0.63$ kpc (ref. ), $d_{\rm SMC}=62.44\pm1.28$ kpc (ref. ), and $d_{\rm NGC~6822}=474\pm13$ kpc (ref. ), respectively.

## H$_{2}$ surface density

We first generated source masks for each spectral cube using the source-finding algorithm embedded in $^{\rm 3D}$BAROLO (ref. ). For molecular clouds in the Galactic outer disk as well as the LMC, the SMC and NGC 6822, we set `MASK=Search`, `SNRCUT=3` and `GROWTHCUT=2.5`. Using this setting, signals in the line cube with $S/N>3$ were iteratively identified as real emission. Then, the source mask was grown to include surrounding signals with $S/N>2.5$. The data from the GRS for molecular clouds do not have enough line-free channels to estimate the spectral noise due to severe cloud blending. Therefore, we set `THRESHOLD=0.39` and `GROWTHTHRESHOLD=0.33`. With this setting, the algorithm searches for values larger than 0.39 K ($S/N=3$ in antenna temperature ($T_{\rm A}^{*}$)) and growth to 0.33 K ($S/N=2.5$ in $T_{\rm A}^{*}$) (cite: 2006ApJS..163..145J) in the line cube.

We calculated the surface density of $^{13}$CO ($N_{\rm ^{13}CO}$) under the assumption of local thermodynamic equilibrium (LTE). For molecular clouds with complementary $^{12}$CO data, we estimated the excitation temperature ($T_{\rm ex}$) by assuming (1) that the low-$J$ $^{13}$CO lines share the same $T_{\rm ex}$ with the $^{12}$CO lines and (2) that the $^{12}$CO lines are optically thick. Therefore, $T_{\rm ex}$ is related to the peak main beam temperature of the $^{12}$CO line ($T_{\rm 12,pk}$) through $$\begin{equation}
J(T_{\rm ex},\nu) = f_{\rm bm}^{-1}T_{\rm 12,pk}+J(T_{\rm bg},\nu),
\end{equation}$$ where $\nu$ is the rest frequency of the line. The background temperature ($T_{\rm bg}$) was taken as the brightness temperature of the cosmic microwave background ($T_{\rm CMB}=2.73$ K). The beam filling factor ($f_{\rm bm}$) was assumed to be unity. $J(T,\nu)$ is the Rayleigh-Jeans Equivalent Temperature (cite: 2015PASP..127..266M): $$\begin{equation}
    J(T,\nu)\equiv\frac{h\nu/k}{{\rm exp}(h\nu/kT)-1}.
\end{equation}$$ where $k$ is the Boltzmann constant and $h$ is the Planck constant. When no complementary $^{12}$CO data were available, we took $T_{\rm ex}=15$ K, which is the typical kinetic temperature ($T_{\rm k}$) of infrared dark clouds (cite: 2017A&A...598A..30T; 2013A&A...552A..40C) and Planck Galactic cold clumps(cite: 2022ApJS..258...17F).

The optical depth of $^{13}$CO ($\tau_{13}$) of each voxel in the line cube was solved by the radiative transfer equation: $$\begin{equation}
\label{equation:tau13}
\tau_{13}=-{\rm ln}\left\{1-\frac{T_{13}}{f_{\rm bm}[J(T_{\rm ex},\nu)-J(T_{\rm bg},\nu)]}\right\},
\end{equation}$$ where $T_{\rm 13}$ is the main beam temperature of the $^{13}$CO line. Therefore, $N_{\rm ^{13}CO}$ was found by integrating $\tau_{13}$ along the spectral axis, that is the velocity ($v$) (cite: 1991ApJ...374..540G): $$\begin{equation}
\label{eq:N13}
N_{\rm ^{13}CO} = \frac{3k}{8\pi^{3}B\mu^{2}}{\rm exp}\left[\frac{hBJ_l(J_l+1)}{kT_{\rm ex}}\right] \times \frac{T_{\rm ex}+hB/3k}{1-{\rm exp}(-h\nu/kT_{\rm ex})}\times \frac{\int \tau_{13}dv}{(J_l+1)},
\end{equation}$$ where $B$ ($\sim55.1$ GHz) is the rotational constant, $\mu$ ($\sim0.112$ D) is the dipole moment and $J_{l}$ is the lower energy level of the $^{13}$CO transition (for $^{13}$CO $J=1\rightarrow0$, $J_{l}$=0; for $^{13}$CO $J=2\rightarrow1$, $J_{l}$=1).

We converted $N_{\rm ^{13}CO}$ to $N_{\rm H_{2}}$ through the abundance ratios of $N_{\rm ^{12}CO}/N_{\rm ^{13}CO}$ (hereafter $^{12}$CO/$^{13}$CO) and $N_{\rm H_{2}}/N_{\rm ^{12}CO}$ (hereafter H$_{2}$/$^{12}$CO) for the Galactic molecular clouds: $$\begin{equation}
    N_{\rm H_{2}} = N_{\rm ^{13}CO}\times {\rm ^{12}CO/^{13}CO\times H_{2}/^{12}CO}.
    \label{eq:NH2}
\end{equation}$$ The underlying assumptions are as follows: (1) $\rm ^{12}CO/^{13}CO$ is represented by the $^{12}$C-to-$^{13}$C isotopic ratio ($^{12}$C/$^{13}$C$=5.87R_{\rm gc}+13.25$)(cite: 2020A&A...640A.125J) and (2) H$_{2}$/$^{12}$CO is inversely proportional to the gas-phase oxygen abundance (O/H$\propto10^{-0.044(R_{\rm gc}-R_{\rm gc,\odot})}$)(cite: 2022MNRAS.510.4436M). The H$_{2}$/$^{12}$CO value at $R_{\rm gc}=R_{\rm gc, \odot}$ is $6.0\times10^{3}$, measured by absorption lines in nearby clouds against background stars(cite: 2017ApJ...838...66L).

We assumed $\rm H_{2}/^{13}CO=3\times10^{6}$ (ref. ) for molecular clouds in the LMC. We adopted $\rm H_{2}/^{13}CO=7.5\times10^{6}$ for the SMC and NGC 6822, which was scaled from the LMC value through their metallicity ratio.

## Physical properties of molecular clouds

In this work, the equivalent radius ($R_{\rm cloud}$), the velocity dispersion ($\sigma_{\rm v}$) and the molecular gas mass ($M_{\rm mol}$) of molecular clouds were all measured within the half-peak isophote of $N_{\rm H_{2}}$. This enabled a consistent comparison among observations with different angular resolutions and sensitivities (‘Possible bias in measuring cloud properties’). The measured physical quantities for the Galactic molecular clouds are presented in Supplementary Tables [\[tab: Supp_Table1\]](#tab: Supp_Table1) and [\[tab: Supp_Table2\]](#tab: Supp_Table2).

$\bullet$ $R_{\rm cloud}$: The equivalent angular radius ($r_{\rm cloud}$) of a cloud was calculated by deconvolving the telescope beam from the observed angular area ($A$; within the half-peak isophote of $N_{\rm H_{2}}$): $$\begin{equation}
    r_{\rm cloud} = \sqrt{\frac{A}{\pi}-\frac{\theta_{\rm beam}^{2}}{4}}.
    \label{eq:rcloud}
\end{equation}$$

Theoretically, the fractional uncertainty of $r_{\rm cloud}$ is inversely proportional to the $S/N$ of the peak intensity(cite: 1997PASP..109..166C). Most clouds studied in this work have a peak $S/N$ much larger than 10. Therefore, we adopted a conservative uncertainty of $10\%$ for $r_{\rm cloud}$ (‘Possible bias in measuring cloud properties’) to include any unforeseen errors. The cloud physical radius is then given by $R_{\rm cloud} = r_{\rm cloud}d$.

$\bullet$ $\sigma_{\rm v}$: The intensity-weighted velocity dispersion ($\sigma_{\rm v}$) is given by $$\begin{equation}
        \sigma_{\rm v} = \sqrt{\sigma_{\rm v,obs}^{2}-\sigma_{\rm v,ins}^{2}},
        \label{equation:sigma_v}
\end{equation}$$ where $\sigma_{\rm v,obs} = \sqrt{\sum T_{\rm i}(v_{\rm i}-\bar v)^2/\sum T_{\rm i}}$ is the observed velocity dispersion and $\sigma_{\rm v,ins}=\Delta V_{\rm ins}/{\rm 2\sqrt{2ln(2)}}$ is the velocity dispersion led by the instrumental spectral broadening. $\bar v = \sum T_{\rm i}v_{\rm i}/{\sum T_{\rm i}}$ is the intensity-weighted mean velocity. $\Delta V_{\rm ins}$ is approximately the channel width. We also applied an uncertainty of $10\%$ for $\sigma_{\rm v}$.

$\bullet$ $M_{\rm mol}$: The $M_{\rm mol}$ of a molecular cloud at a distance of $d$ is $$\begin{equation}
    M_{\rm mol}=\mu m_{\rm H_{2}} d^{2}\int_{A} N_{\rm H_{2}}\delta x \delta y,
\end{equation}$$ where $m_{\rm H_{2}}\approx3.347115\times10^{-24}$ g is the mass of an H$_2$ molecule, $\delta x$ and $\delta y$ are the pixel angular sizes and $\mu\approx1.36$ is the mean molecular weight considering the mass of helium (cite: knapen2017outskirts). We adopted an uncertainty of $20\%$ for $M_{\rm mol}$, which is a conservative estimate for the flux calibration error for millimetre-wave observations. Systematic errors are not involved in error propagation.

The mean mass surface density ($\Sigma_{\rm mol}$) is $$\begin{equation}
    \Sigma_{\rm mol} = \frac{M_{\rm mol}}{\pi R_{\rm cloud}^{2}}.
\end{equation}$$

For molecular clouds in DDO 70, $\Sigma_{\rm mol}$ is related to the cloud-boundary surface density ($\Sigma_{\rm limit}=756\pm468\,M_{\odot}\,\rm pc^{-2}$, projection on the two-dimensional sky)(cite: 2020ApJ...892..147S) by $\Sigma_{\rm mol}=\frac{2}{-k+3}\Sigma_{\rm limit}$, for a radial density profile $\rho\propto r^{-k}$. We adopt $k=1.8$ for typical star forming clumps in the Milky Way (cite: 2002ApJS..143..469M).

## The virial parameter

The virial parameter ($\alpha_{\rm vir}$) is defined as(cite: 1992ApJ...395..140B): $$\begin{equation}
\alpha_{\rm vir} = \frac{5\sigma_{\rm v}^{2}R_{\rm cloud}}{GM_{\rm mol}}=a\frac{2E_{\rm k}}{|E_{\rm g}|},
\label{eq: alphavir}
\end{equation}$$ where $G$ is the gravitational constant. For a uniform-spherical cloud ($a=1$)(cite: 1992ApJ...395..140B), if the contributions of both the external pressure and the magnetic field are negligible, virial equilibrium ($2E_{\rm k}+E_{\rm g}=0$) and energy equipartition ($E_{\rm k}+E_{\rm g}=0$) lead to $\alpha_{\rm vir}=1$ and $\alpha_{\rm vir}=2$, respectively. Even though virial equilibrium and energy equipartition are conceptually different(cite: 2006MNRAS.372..443B), a factor of two in $\alpha_{\rm vir}$ is hard to measure due to the systematic uncertainties. Consequently, we could not distinguish them in this work. Molecular clouds with $\alpha_{\rm vir}>1$ and $\alpha_{\rm vir}<1$ are defined as supervirial and subvirial, respectively.

## Systematic errors in $M_{\rm mol}$ and $\alpha_{\rm vir}$

The uncertainties in $M_{\rm mol}$ and $\alpha_{\rm vir}$ come from the uncertainties in the cloud distance ($d$), the excitation conditions of $^{13}$CO and the abundance ratios. Among the parameters used to calculate $\alpha_{\rm vir}$ (Eq. [\[eq: alphavir\]](#eq: alphavir)), both $R_{\rm cloud}$ and $M_{\rm mol}$ depend on the cloud distance. $R_{\rm cloud}$ scales with $d$. $M_{\rm mol}$ scales with both $d^2$ and the H$_2$/$^{13}$CO abundance ratio. The H$_2$/$^{13}$CO abundance ratio was estimated through the Galactic $^{12}$C/$^{13}$C gradient and the O/H gradient, and is, therefore, a function of $R_{\rm gc}$. Therefore, $\alpha_{\rm vir}$$\propto d^{-1}({\rm H_{2}/^{13}CO})^{-1}$.

The distances of the Galactic outer-disk molecular clouds are well constrained with a fractional uncertainty of $\lesssim20\%$. For clouds at $R_{\rm gc}>15$ kpc, the distance uncertainty contributes $\lesssim40\%$ of the uncertainty in $M_{\rm mol}$ and $\lesssim20\%$ of the uncertainty in $\alpha_{\rm vir}$.

In the following, we assess the systematic errors arising from uncertainties in $^{13}$CO excitation conditions and abundance ratios.

- The excitation of $^{13}$CO. Depending on the specific excitation conditions(cite: 2009ApJ...699.1092H), assuming local thermodynamic equilibrium can deviate $N_{\rm ^{13}CO}$ from its intrinsic value. For the typical mean volume density of H$_2$ ($n_{\rm H_2}$) of the molecular clouds studied in this work ($\sim10^{3}-10^{4}$ cm$^{-3}$), the deviation from the theoretical mass was $\lesssim40\%$. The assumption of $T_{\rm ex}=15$ K may overestimate $N_{\rm ^{13}CO}$ by $\lesssim20\%$ for the $J=1\rightarrow0$ transition (Supplementary Fig. [4](#fig: Supp_Fig1)a). The overestimation is negligible for the $J=2\rightarrow1$ transition (Supplementary Fig. [4](#fig: Supp_Fig1)b). Therefore, the overall overestimation due to the assumptions on $^{13}$CO excitation is within 60%.

  ![image](fig/Supp_Fig1a.pdf) ![image](fig/Supp_Fig1b.pdf)

- The abundance ratios. Not only are the $^{12}$C/$^{13}$C ratios still poorly measured at $R_{\rm gc}>12$ kpc (ref. ) but the Galactic gas-phase O/H versus $R_{\rm gc}$ gradient is also still less constrained at $R_{\rm gc}>18$ kpc (ref. ). Depending on the depth into molecular clouds, the molecular ($^{12}$CO/$^{13}$CO) abundance ratio can be lower than the isotopic ($^{12}$C/$^{13}$C) abundance ratio due to isotopic-selective chemical reactions(cite: 2014MNRAS.445.4055S). This may have led to an overestimation of $N_{\rm ^{12}CO}$ as inferred from $N_{\rm ^{13}CO}$ by up to $50-60\%$ (ref. ). The H$_{2}$/$^{12}$CO ratios measured in the solar neighbourhood ($R_{\rm gc,\odot}$) also vary by a factor of two among different studies (cite: 1978ApJS...37..407D; 1982ApJ...262..590F; 2017ApJ...838...66L). Despite these uncertainties, the dependencies of $^{12}$CO/$^{13}$CO and H$_{2}$/$^{12}$CO on $R_{\rm gc}$ (or $Z$) are natural expectations of Galactic chemical evolution models (Supplementary Fig. [5](#fig: Supp_Fig2))(cite: 2019MNRAS.490.2838R) and astrochemistry(cite: 2012MNRAS.426..377G). Supplementary Fig. [6](#fig: Supp_Fig3) shows a test under an extreme condition, where $M_{\rm mol}$ is calculated with a constant H$_2$/$^{13}$CO abundance ratio (to simulate what would happen if we were to neglect any abundance gradients). In this case, the $\alpha_{\rm vir}$ trends become flatter. Given both the observational and theoretical evidence for the existence of gradients in both $^{12}$C/$^{13}$C and O/H with $R_{\rm gc}$, the $\alpha_{\rm vir}$ trends can be considered as solid, albeit the uncertainties in the gradient slopes.

  ![](fig/Supp_Fig2.pdf)
  ![](fig/Supp_Fig3.pdf)

## Possible bias in measuring cloud properties

Limited angular resolution and observational sensitivity may also have biased the measurement of $R_{\rm cloud}$ and $M_{\rm cloud}$. To examine to what extent these may have influenced our results, we generated a set of mock clouds to mimic real observations. First, we generated two-dimensional Gaussian models as the intrinsic cloud emissions. We then convolved the Gaussian models with the telescope beam and added Gaussian noise to the convolved models.

The peak values of the Gaussian models were scaled such that the final convolved maps have a peak $S/N=10$, which is approximately the worst $S/N$ of our sample of Galactic clouds. The major axes of the Gaussian models were set from 4$''$ to 100 $''$ (with a spacing of 0.5$''$) and the minor-to-major axis ratios (aspect ratios) were set from 0.2 to 1.0 (with a spacing of 0.2). We used a telescope beam of 23.5$''$ and a pixel size of 4$''$, the same as for our IRAM 30 m telescope observations. Similarly, we measured the cloud equivalent radii and fluxes within the half-peak isophote of the convolved models.

![image](fig/Supp_Fig4abc.pdf) ![image](fig/Supp_Fig4d.pdf)

Supplementary Fig. [7](#fig: Supp_Fig4)a shows the ratio between the measured radius ($r_{\rm M}$) and its true value ($r_{\rm T}$) as a function of $r_{\rm M}$. For clouds with an aspect ratio $\ge 0.4$ (roundish clouds) and $r_{\rm M}\gtrsim10''$ (clouds large enough to be marginally resolved), the difference between $r_{\rm M}$ and $r_{\rm T}$ is within 10%, consistent with the theoretical prediction(cite: 1997PASP..109..166C). In other cases, that is, elongated clouds and small clouds, the cloud radii are overestimated because the minor axes in the convolved models are not well sampled by the image pixel.

Supplementary Fig. [7](#fig: Supp_Fig4)b shows the ratio between the measured flux ($f_{\rm M}$) and its true value ($f_{\rm T}$) as a function of $r_{\rm M}$. In all cases, the difference between $f_{\rm M}$ and $f_{\rm T}$ is within 10%. Given that the flux ratio is representative of the mass ratio (Eq. [\[eq:N13\]](#eq:N13)) for optically thin, low-$J$ $^{13}$CO lines, the cloud masses in this work are insensitive to measurement bias.

Consequently, $\frac{r_{\rm M}/r_{\rm T}}{f_{\rm M}/f_{\rm T}}$ measures the ratio between the measured $\alpha_{\rm vir}$ and its true value. Supplementary Fig. [7](#fig: Supp_Fig4)c shows $\frac{r_{\rm M}/r_{\rm T}}{f_{\rm M}/f_{\rm T}}$ as a function of $r_{\rm M}$. The measured $\alpha_{\rm vir}$ was almost identical to its true value unless the cloud was too small to be sampled by the image pixel, where the $\alpha_{\rm vir}$ is overestimated. Given that most of the clouds in this work have peak $S/N>10$ and $r_{\rm M}>10''$, the angular resolution and the sensitivity do not bias the measurement of $\alpha_{\rm vir}$.

Given the wide range of cloud distances in the Milky Way, a specific telescope beam corresponds to different physical resolutions. We, thus, further tested to see whether this biased our measurements of the cloud $\alpha_{\rm vir}$. First, we smoothed all line cubes for the Galactic molecular clouds to the same physical resolution of 2 pc, where the smoothing kernels depend on the cloud distances. A few clouds were excluded due to their small (physical) mapping areas. Then, we followed the same procedures to measure the cloud $\alpha_{\rm vir}$. Supplementary Fig. [7](#fig: Supp_Fig4)d shows that the $\alpha_{\rm vir}$ trends are not affected by the downgraded physical resolution.

## Selection bias

A larger heliocentric distance could bias the sample to brighter (and, thus, more massive) molecular clouds, which tend to have smaller $\alpha_{\rm vir}$ in observations(cite: 2013ApJ...779..185K).

We examined whether the decreasing $\alpha_{\rm vir}$ trends were biased by such selection effects by comparing molecular clouds with different $R_{\rm gc}$ but similar heliocentric distances (Supplementary Fig. [8](#fig: Supp_Fig5)). At the distance range $\sim 15-20$ kpc, the sample contains two molecular clouds at $R_{\rm gc}\approx13$ kpc (G37.350 and G44.8 in the first Galactic quadrant) and five molecular clouds at $R_{\rm gc}>20$ kpc (SUN15_56, SUN15_57, SUN15_53, SUN15_55, and SUN15_59 in the second Galactic quadrant). The clouds at $R_{\rm gc}>$ 20 kpc have at least $\times$5 smaller $\alpha_{\rm vir}$ than those at $R_{\rm gc}\approx13$ kpc.

![](fig/Supp_Fig5.pdf)

Supplementary Fig. [9](#fig: Supp_Fig6)a,b show that for each $R_{\rm gc}$ bin, $\alpha_{\rm vir}$ barely varies with $M_{\rm mol}$ or $n_{\rm H_{2}}$. At comparable $M_{\rm mol}$, $\alpha_{\rm vir}$ becomes smaller for larger $R_{\rm gc}$ (reminiscent of predictions by analytic models on Giant Molecular Cloud scales (cite: 2018ApJ...854..100M)). Therefore, the distance bias to the $\alpha_{\rm vir}$ trends is not important.

![image](fig/Supp_Fig6a.pdf) ![image](fig/Supp_Fig6b.pdf)

## The general virial theorem

From the momentum equation, the general Virial Theorem in the presence of external pressure and magnetic fields can be derived (cite: spitzer2008physical; 1989ApJ...338..178E; 1992ApJ...395..140B) as: $$\begin{equation}
\frac{\ddot{I}}{2}=2(E_{\rm k}-E_{\rm k,0})+E_{\rm m}+E_{\rm g},
\label{eq:virial}
\end{equation}$$ where $E_{\rm k}=\frac{3}{2}M_{\rm mol}\sigma_{\rm v}^{2}$ is the kinetic energy and $E_{\rm g}=-a\frac{3GM_{\rm mol}^{2}}{5R_{\rm cloud}}$ is the self-gravitational energy ($a$ is of order unity and accounts for the non-sphericity and the non-uniformity of a molecular cloud). $E_{\rm k,0}=\frac{3P_{\rm e}V}{2}$ and $E_{\rm m}=\frac{1}{8\pi}\int(B^{2}-B^{2}_{\rm e})dV$ account for the external pressure ($P_{\rm e}$) and the magnetic field ($B$), surrounding and within the cloud volume ($V$), respectively. $B_{\rm e}$ is the magnetic field outside the cloud.

For the general virial equilibrium, the second-derivative of the moment of inertia ($\ddot{I}$) equals zero unless tidal fields are dominant within a cloud volume, which may be the case for clouds in the Galactic Centre. In Eq. [\[eq:virial\]](#eq:virial), only the volumetric $\frac{1}{8\pi} \int B^2 dV$ term inside $E_{\rm m}$ has the sign that allows it to serve as another support in the dynamic state of the cloud besides $E_{\rm k}$.

![](fig/ED_Fig1.pdf)

For the supervirial molecular clouds, the support from the $B$ field is often negligible due to the strong turbulence. If these clouds are in general virial-equilibrium, they are most probably bound by $P_{\rm e}$ (lines of constant pressures in Supplementary Fig. [10](#fig: ED_Fig1))(cite: 1989ApJ...338..178E; 1992ApJ...395..140B; 2011MNRAS.416..710F): $$\begin{equation}
    \frac{\sigma_{\rm v}^{2}}{R_{\rm cloud}}=\frac{\pi G \Sigma_{\rm mol}}{5}+\frac{4P_{\rm e}}{3\Sigma_{\rm mol}}.
    \label{eq:pressure-virial}
\end{equation}$$

Supervirial $\alpha_{\rm vir}$ values are often deduced for molecular clouds in the centres of galaxies and are thought to be responsible for the lower $X_{\rm CO}$ values found for them (cite: 2014A&A...568A.122Z; 1999ApJ...516..114P).

For the subvirial clouds, the $B$ field starts to dominate the support against cloud self-gravity. The supporting force from the $B$ field is indirectly exerted on the neutral molecular gas through ion-neutral collisions. Given the representative volume density ($n_{\rm H_{2}}\approx10^{3}-10^{4}$ cm$^{-3}$) of the outer-disk clouds and a typical cosmic-ray ionization rate ($\zeta_{\rm H_{2}}=10^{-17}$ s$^{-1}$) (cite: 1979ApJ...232..729E; 2023pcsf.conf..237P), the typical ionization fraction ($x_{\rm e}=n_{e}/n_{\rm H}$)(cite: 1998ApJ...503..689W) is $\sim10^{-7}$. This results in a magnetohydrodynamic cutoff wavelength of $\lesssim0.01$ pc (ref. (cite: 1998ApJ...503..689W)). Therefore, for the typical scale ($\sim1$ pc) of the outer-disk molecular clouds, the magnetic fields are well coupled with neutral particles. Neglecting the minor contribution from $P_{\rm e}$ in the outer Galaxy, we can derive (lines with constant $B$ fields in Supplementary Fig. [10](#fig: ED_Fig1)): $$\begin{equation}
    \frac{\sigma_{\rm v}^{2}}{R_{\rm cloud}}=\frac{\pi G \Sigma_{\rm mol}}{5}-\frac{B^{2}}{18\pi\Sigma_{\rm mol}}.
    \label{eq:B-field-virial}
\end{equation}$$ Here we neglect the external magnetic field $B_{\rm e}$ term as it is small ($\sim$10 $\mu$G)(cite: 2012ARA&A..50...29C) compared to the $B$ field required to support the subvirial clouds ($\sim$ 100 $\mu$G), as we show below.

![](fig/ED_Fig2.pdf)

Supplementary Fig. [11](#fig: ED_Fig2) compares the $B$ field required to support the subvirial clouds with the expectations from the $B$ versus $n_{\rm H}$ relation ($n_{\rm H}=2n_{\rm H_{2}}$) (cite: 2010ApJ...725..466C; 2022Natur.601...49C). This relation was established in the solar neighbourhood and the inner Galaxy by measuring Zeeman effects. A classical explanation of this relation is that the $B$-field line is coupled with the molecular gas through ion-neutral coupling (cite: lequeux2004interstellar) (which is solid at $>0.01$ pc scales). In denser regions ($n_{\rm H}>300$ cm$^{-3}$), the field lines are squeezed by the self-gravity of a cloud, so the $B$ field is enhanced (cite: 2010ApJ...725..466C). There are also other explanations (cite: 2023ApJ...946L..46C).

Supplementary Fig. [11](#fig: ED_Fig2) suggests that a similar $B$-field strength to those in the inner Galaxy is sufficient for supporting the subvirial clouds in the outer Galaxy. In nearby Milky Way-like spiral galaxies, the energy density of the $B$ field (proportional to $B^2$) on kiloparsec scales varies only a little from the inner to the outer galactic disk (except for the innermost regions) (cite: 2013MNRAS.433.1675B; 2015A&A...578A..93B). If this is also true for the Milky Way, we expect that the $B$ field in molecular clouds will be similar across the Galactic plane, provided that the mechanisms for enhancing the $B$ field with density are similar.

Possible deviations from a uniform-spherical cloud ($a>1$) would even further consolidate our results. This is because $\alpha_{\rm vir}$ defined by Eq. [\[eq: alphavir\]](#eq: alphavir) overestimates $2E_{\rm k}/|E_{\rm g}|$ by a factor of $a$. Given the typical density profiles of Galactic star-forming clouds(cite: 2002ApJS..143..469M), $a\sim1.4\pm0.3$. To properly measure $a$, high-angular-resolution observations are needed(cite: 2013ApJ...768L...5L).

## Contribution from cloud rotation and thermal motion in $E_{\rm k}$

In addition to the random turbulent motion, cloud rotation and thermal motion can also contribute to the $\sigma_{\rm v}$ of a molecular cloud. To evaluate the effect of cloud rotation, we first fitted the rotational velocity along each LoS with a planar function: $$\begin{equation}
v_{\rm rot}(x,y) = a(x-x_{0})+b(y-y_{0})+v_{0},
\end{equation}$$ where ($x_{0}$, $y_{0}$) is the centre coordinate and $v_{0}$ is the LoS velocity at ($x_{0}$, $y_{0}$). Then we subtracted the rotational velocity along each LoS in Eq. [\[equation:sigma_v\]](#equation:sigma_v) through $$\begin{equation}
        \sigma_{\rm v,obs}^{\rm non-rot} = \sqrt{\frac{\sum T_{\rm i}(v_{\rm i}-\bar v - v_{\rm rot})^2}{\sum T_{\rm i}}}.
\end{equation}$$ The contribution of cloud rotation in $E_{\rm k}$ is $\lesssim$ 10$\%$.

The thermal broadening of $^{13}$CO ($\sigma_{\rm v,thermal}^{\rm ^{13}CO}$) at $T_{\rm k}=15$ K is $\sim$ 0.07 $\rm km\;s^{-1}$, which is negligible in $\sigma_{\rm v}$. However, molecular clouds are composed mostly of H$_{2}$ molecules, which are lighter than $^{13}$CO molecules. Therefore, at the same temperature, the thermal velocity dispersion of H$_2$ should be larger than that of $^{13}$CO. For $T_{\rm k}=15$ K, $\sigma_{\rm v,thermal}^{\rm H_{2}} =$ 0.25 km s$^{-1}$ (Supplementary Fig. [12](#fig: Supp_Fig7)). For the outer-disk molecular clouds, the smallest $\sigma_{\rm v}$ is $\sim$ 0.30 km s$^{-1}$. Therefore, for the most extreme cases, including the thermal motion in the total $E_{\rm k}$ would increase $\alpha_{\rm vir}$ by $\lesssim70\%$.

![](fig/Supp_Fig7.pdf)

## Possible mechanisms for $B$-field-dominated cloud dynamics at low metallicities

Our results reveal that the dynamics of metal-poor clouds may be dominated by the $B$ field. However, the detailed underlying physical mechanisms are still unclear. Here we propose two speculations that may play a role.

First, as was revealed by magnetohydrodynamic simulations (cite: 2023ApJ...954...38K), the velocity dispersion of the cold neutral medium decreases towards low metallicity. As molecular clouds should inherit the dynamic properties from their parental ambient atomic gas (cite: 2022MNRAS.515.2822R), they are also expected to have low turbulence levels in low-metallicity conditions. This is in line with Fig. [2](#fig: Main_Fig2)b as well as the narrow CO linewidths found in the LMC and SMC (cite: 2008ApJ...686..948B; 2023ApJ...949...63O). The cold neutral medium surrounding metal-poor molecular clouds, which has a higher fraction under low-metallicity conditions, may allow turbulence to dissipate significantly enough before entering the molecular clouds. In this case, the $B$ field would take over the role of supporting clouds against self-gravity, resulting in a low $\alpha_{\rm vir}$ observed in metal-poor molecular clouds.

Second, the far-ultraviolet photons can penetrate deeper into molecular clouds in low-metallicity conditions, leading to a higher ionization fraction. This would allow stronger coupling between neutrals and ions regulated by the $B$ field(cite: lequeux2004interstellar) in such conditions. This could enhance the B-field contribution in supporting these clouds, thus decreasing $\alpha_{\rm vir}$.

Apart from the above mechanisms, the $^{13}$CO molecules could preferentially survive in regions with high column densities, under low-metallicity conditions. This may cause a bias towards the dense cores of molecular clouds, which are often found subvirial with high-volume-density gas tracers (cite: 2013ApJ...779..185K; 2024ApJ...974L...6W). However, the low-metallicity clouds in this work have a typical size of $\sim1$ pc, which is larger than dense cores in the solar neighbourhood. This indicates that the $B$ field is already important on cloud scales under low metallicities.

## Low turbulence injection and star-formation activities in the Galactic outer disk

![](fig/Supp_Fig8.pdf)

In the Milky Way, the turbulence-injection level is expected to decrease towards the outer Galaxy. Turbulence in molecular clouds can be driven by both global Galactic dynamics (cite: 2006ApJ...638..191K; 2018ApJ...854..100M; 2022MNRAS.515.2822R) and local stellar feedback (cite: 2006ApJ...641L.121T; 2016ApJ...822...11P). On galactic scales, both shear (Oort constant $A$) and vorticity (Oort constant $B$) induced by Galactic differential rotation decline with $R_{\rm gc}$ (Supplementary Fig. [13](#fig: Supp_Fig8)), leading to less kinetic energy (proportional to $2A^{2}+5B^{2}$) injected by cloud-cloud collisions (cite: 2020MNRAS.496.5211A). On the other hand, the surface density of the Galactic star formation rate ($\Sigma_{\rm SFR}$) decreases with $R_{\rm gc}$ (ref. ), so the effect of stellar feedback effect should also be weak in the outer Galaxy.

To examine the star-formation activities in the outer-disk clouds studied in this work, we compared mid-infrared (3.4, 4.6, 12 and 22 $\mu$m wavelength) continuum images from the Wide-field Infrared Survey Explorer archive and radio continuum images from the Very Large Array Sky Survey (3 GHz S-band) and the National Radio Astronomy Observatory’s Very Large Array Sky Survey (1.4 GHz L-band). Four clouds did not have archival radio data.

Although most of the outer-disk molecular clouds show obvious 22 $\mu$m emissions, only a few of them show obvious 3 and 1.4 GHz continuum emission (‘Data Availability’). Therefore, the outer-disk molecular clouds studied in this work are mostly star-forming clumps(cite: lada1987star) without strong massive stellar feedback (otherwise, the 3 and 1.4 GHz continua would show strong free-free emission from H ii regions and the velocity dispersion would be increased by the massive stellar feedback). Because the feedback from low-mass stars does not influence the overall cloud dynamics(cite: 2012ApJ...747...22H; 2015ApJS..219...20L), the $\alpha_{\rm vir}$ trends should also apply to non-star-forming clouds in general.

The subvirial outer-disk clouds at $R_{\rm gc}>15$ kpc used in this work are from ref. . A sensitive survey of H$_{2}$O, CH$_{3}$OH and OH masers was performed towards these clouds (cite: 2018ApJ...869..148S), but no detection was found. This is in line with the evidence that the outer-disk molecular clouds lack massive star formation and, therefore, the stellar feedback is weak.

## Caveats of studying $\alpha_{\rm vir}$ using low-$J$ $^{12}$CO lines

Low-$J$ $^{12}$CO lines, with the standard $X_{\rm CO}$ conversion factor, have been widely adopted to trace molecular gas conditions among H$_2$ clouds in both the Milky Way and external galaxies(cite: 2013ARA&A..51..207B). However, this method is strictly limited in large-scale studies (50 pc to kiloparsecs) (cite: 2013ARA&A..51..207B). For resolved studies of individual molecular clouds, radiative trapping becomes dominant in regulating the $^{12}$CO emission.

First, the optical depths are not uniformly distributed in the $^{12}$CO $J=1\rightarrow0$ emission (in both the spatial and velocity domains). A simple $X_{\rm CO}$ factor cannot properly trace the real distributions of mass and velocity of H$_2$ gas.

Second, the effective critical density of the $^{12}$CO $J=1\rightarrow0$ line is low. At a kinetic temperature of 20 K and under the optically thin limit (cite: 2015PASP..127..299S), the critical density $n_{\rm crit}$ of $^{12}$CO $J=1\rightarrow0$ is $\sim 3.5\times 10^2$cm$^{-3}$ (‘Code Availability’). This value is $\times$10 lower than that often seen in the literature (cite: 2013ARA&A..51..105C), which neglects that collisions do not follow any selection rules(cite: 2015PASP..127..299S).

However, the $^{12}$CO $J=1\rightarrow0$ line shows a high optical depth (with a mean value $\tau > 10$, by multiplying the $^{12}$C/$^{13}$C ratio with $\tau_{\rm ^{13}CO}$) (cite: 2009ApJS..182..131R) in Galactic giant molecular clouds, indicating strong local radiative trapping(cite: draine2010physics). This radiative trapping would lower the effective critical density $n_{\rm crit}^{\rm eff}$ by another factor of $\tau$ ($>$10): $n_{\rm crit}^{\rm eff} \approx n_{\rm crit}(1-e^{-\tau})/\tau$, where $(1-e^{-\tau})/\tau \approx 1/\tau$ represents the escape probability of the transition. This means that H$_2$ gas with a low density of a few $\times$ 10 cm$^{-3}$ could remarkably contribute to the $^{12}$CO $J=1\rightarrow0$ emission in both line flux and linewidth.

As a sanity check, we also collected $^{12}$CO measurements from the literature (cite: 2015ApJ...798L..27S; 2017ApJS..230...17S; 2001ApJ...562..348O). We corrected $M_{\rm mol}$ by implementing the metallicity-dependent $X_{\rm CO}$. We simply adopted $X_{\rm CO} \propto Z^{-1.0}$ as the dependency relation (cite: 2013ARA&A..51..207B). Supplementary Fig. [14](#fig: ED_Fig3) shows that the $\alpha_{\rm vir}$ measured using $^{12}$CO emission follows a similar trend $^{13}$CO: $\log(\alpha_{\rm vir}) = (1.5\pm0.1)\times\log(Z [Z_{\odot}])+(0.56\pm0.03)$. This correlation was fitted using ordinary least squares for the $^{13}$CO measurements of the Galactic molecular clouds (Fig. [3](#fig: Main_Fig3)). The slope of the $\alpha_{\rm vir}$ versus $Z$ trend is sensitive to the adopted H$_2$/$^{13}$CO abundance ratio, which may be better constrained by future observations.

![](fig/ED_Fig3.pdf)

# Data Availability

The following data and figures are available via figshare at <https://doi.org/10.6084/m9.figshare.27282924> (ref.): (1) reduced data cubes of the new observations presented in this work (subfolder GMPMC_line_fitscubes), (2) $^{13}$CO spectra and $N_{\rm H_2}$ maps (subfolder Supp_Figures/NH2_13CO_spectrum), (3) infrared and radio images (subfolder Supp_Figures/IR_Radio_outer_disk_clouds) and (4) distance PDFs of the Galactic molecular clouds (subfolder Supp_Figures/Distance_PDFs). This work is based on observations carried out under Projects 031-17 and 102-22 with the IRAM 30 m telescope, Projects ADS/JAO.ALMA#2013.1.00652.S, ADS/JAO.ALMA#2015.1.00581.S, ADS/JAO.ALMA#2019.1.01641.S and ADS/JAO.ALMA#2021.2.00175.S with ALMA, and Project Lin_L_22B_1 with SMT. Source data are provided with this paper.

# Code Availability

Code for calculating the critical densities can be obtained from GitHub (<https://github.com/ZhiyuZhang/critical_densities>).

# Acknowledgements

This work is supported by the National Key Research & Development (R&D) Programme of China (Grant No. 2023YFA1608204). Z.-Y.Z., L. Lin, Yichen Sun and G.L. acknowledge the support of the National Natural Science Foundation of China (NSFC; Grant Nos. 12173016 and 12041305), science research grants from the China Manned Space Project (Grant Nos. CMS-CSST-2021-A08 and CMS-CSST-2021-A07) and the Programme for Innovative Talents, Entrepreneur in Jiangsu. This work also benefited from the International Space Science Institute (ISSI/ISSI-BJ) in Bern and Beijing, thanks to funding for the team ‘Chemical abundances in the ISM: the litmus test of stellar IMF variations in galaxies across cosmic time’ (PIs D.R. and Z.-Y.Z.). J. Wang gives thanks for the support of the NSFC (Grant No. 12173067) and the Guangxi Talent Programme (Highland of Innovation Talents). Y.G. is supported by the Strategic Priority Research Programme of the Chinese Academy of Sciences (Grant No. XDB0800301). Yan Sun is supported by the Youth Innovation Promotion Association, CAS (Grant No. 2022085), and the Light of West China Programme (Grant No. xbzg-zdsys-202212). T.G.B. acknowledges support from the Leading Innovation and Entrepreneurship Team of Zhejiang Province of China (Grant No. 2023R01008). D.R. thanks the Italian National Institute for Astrophysics for funding the project ‘An in-depth theoretical study of CNO element evolution in galaxies’ through Finanziamento della Ricerca Fondamentale, Theory Grant Fu. Ob. 1.05.12.06.08. D.L. is a New Cornerstone investigator. H.B.L. is supported by the National Science and Technology Council of Taiwan (Grant Nos. 111-2112-M-110-022-MY3 and 113-2112-M-110-022-MY3). K.Q. acknowledges support from the NSFC (Grant Nos. 12425304 and U1731237) and the National Key R&D Programme of China (Grant Nos. 2023YFA1608204 and 2022YFA1603100). C.-W.T. is supported by the NSFC (Grant No. 11988101). J. Wu gives thanks for support from the NSFC (Grant No. 12041302) and the Tianchi Talent Programme of Xinjiang Uygur Autonomous Region. S.F. acknowledges support from the NSFC (Grant No. 12373023), a starting grant at Xiamen University and the presidential excellence fund at Xiamen University (Grant No. 20720220024). This work is based on observations carried out under Projects 031-17 and 102-22 with the IRAM 30 m telescope, Projects ADS/JAO.ALMA#2013.1.00652.S, ADS/JAO.ALMA#2015.1.00581.S, ADS/ JAO.ALMA#2019.1.01641.S and ADS/JAO.ALMA#2021.2.00175.S with ALMA, and Project Lin_L_22B_1 with SMT. IRAM is supported by INSU/ CNRS (France), MPG (Germany) and IGN (Spain). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The Heinrich Hertz SMT is operated by the Arizona Radio Observatory, which is part of Steward Observatory at the University of Arizona.

# Author Contributions statement

L. Lin led the project, conducted the data reduction and analyses, and drafted proposals and the paper. Z.-Y.Z. initiated and supervised the whole project and improved the paper. J. Wang helped with the data analysis and validating tests. P.P.P. instructed the general virial analysis and outlined the larger theoretical picture. Yong Shi helped extend this work to low-metallicity dwarf galaxies. Y.G. helped improve the paper and was involved in discussions. Yan Sun provided the initial catalogue and helped with calculating the cloud distances. Yichen Sun, T.G.B. and D.R. helped with the abundance ratios. D.L., H.B.L. and K.Q. helped with discussions on magnetic fields. B.Z. helped with validating the distance measurements. L. Liu, G.L., C.-W.T., J. Wu and S.F. helped with discussions and in improving the paper. All authors reviewed the paper and were involved in discussions, telescope proposals and observations on which the raw data and the analyses were based.

# Competing Interests Statement

The authors declare no competing interests.

100 url urlprefix

(ref: 1981MNRAS.194..809L) Larson, R. B. *Mon. Not. R. Astron. Soc.* **194**, 809–826 (1981).

(ref: 1987ApJ...319..730S) Solomon, P. M., Rivolo, A. R., Barrett, J. & Yahil, A. . *Astrophys. J.* **319**, 730 (1987).

(ref: 2009ApJ...699.1092H) Heyer, M., Krawczyk, C., Duval, J. & Jackson, J. M. . *Astrophys. J.* **699**, 1092–1103 (2009).

(ref: 2017ApJ...834...57M) Miville-Deschênes, M.-A., Murray, N. & Lee, E. J. . *Astrophys. J.* **834**, 57 (2017).

(ref: 2008ApJ...686..948B) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F. & Blitz, L. . *Astrophys. J.* **686**, 948–965 (2008).

(ref: 2010ARA&A..48..547F) Fukui, Y. & Kawamura, A. . *Annu. Rev. Astron. Astrophys.* **48**, 547–580 (2010).

(ref: 2010MNRAS.406.2065H) Hughes, A. *et al.* . *Mon. Not. R. Astron. Soc.* **406**, 2065–2086 (2010).

(ref: 2017ApJ...835..278S) Schruba, A. *et al.* . *Astrophys. J.* **835**, 278 (2017).

(ref: 2019ApJ...885...50W) Wong, T. *et al.* . *Astrophys. J.* **885**, 50 (2019).

(ref: 2023A&A...672A.153S) Saldaño, H. P. *et al.* . *Astron. Astrophys.* **672**, A153 (2023).

(ref: 1989ApJ...338..178E) Elmegreen, B. G. . *Astrophys. J.* **338**, 178 (1989).

(ref: 2006MNRAS.372..443B) Ballesteros-Paredes, J. . *Mon. Not. R. Astron. Soc.* **372**, 443–449 (2006).

(ref: 1992ApJ...395..140B) Bertoldi, F. & McKee, C. F. . *Astrophys. J.* **395**, 140 (1992).

(ref: 2018ApJ...860..172S) Sun, J. *et al.* . *Astrophys. J.* **860**, 172 (2018).

(ref: 2016ApJ...832..143F) Federrath, C. *et al.* . *Astrophys. J.* **832**, 143 (2016).

(ref: 2021MNRAS.505.4048L) Liu, L. *et al.* . *Mon. Not. R. Astron. Soc.* **505**, 4048–4085 (2021).

(ref: 2023MNRAS.525..962P) Petkova, M. A. *et al.* . *Mon. Not. R. Astron. Soc.* **525**, 962–968 (2023).

(ref: 2013ARA&A..51..207B) Bolatto, A. D., Wolfire, M. & Leroy, A. K. . *Annu. Rev. Astron. Astrophys.* **51**, 207–268 (2013).

(ref: 2011ApJ...742...11S) Swinbank, A. M. *et al.* . *Astrophys. J.* **742**, 11 (2011).

(ref: 2003ApJ...585..850M) McKee, C. F. & Tan, J. C. . *Astrophys. J.* **585**, 850–871 (2003).

(ref: 2017A&A...605A..97V) Völschow, M., Banerjee, R. & Körtgen, B. . *Astron. Astrophys.* **605**, A97 (2017).

(ref: 2016A&A...591A.104H) Hacar, A., Alves, J., Burkert, A. & Goldsmith, P. . *Astron. Astrophys.* **591**, A104 (2016).

(ref: 1994ARA&A..32..191W) Wilson, T. L. & Rood, R. . *Annu. Rev. Astron. Astrophys.* **32**, 191–226 (1994).

(ref: 2009ApJS..182..131R) Rathborne, J. M., Johnson, A. M., Jackson, J. M., Shah, R. Y. & Simon, R. . *Astrophys. Js* **182**, 131–142 (2009).

(ref: 2001ApJ...551..852H) Heyer, M. H., Carpenter, J. M. & Snell, R. L. . *Astrophys. J.* **551**, 852–866 (2001).

(ref: 2021A&A...654A.144B) Benedettini, M. *et al.* . *Astron. Astrophys.* **654**, A144 (2021).

(ref: 2010ApJ...723..492R) Roman-Duval, J., Jackson, J. M., Heyer, M., Rathborne, J. & Simon, R. . *Astrophys. J.* **723**, 492–507 (2010).

(ref: 2019A&A...632A..58R) Rigby, A. J. *et al.* . *Astron. Astrophys.* **632**, A58 (2019).

(ref: knapen2017outskirts) Knapen, J. H., Lee, J. C. & de Paz, A. G. *Outskirts of galaxies* (Springer, 2017).

(ref: 2003ApJ...587..278W) Wolfire, M. G., McKee, C. F., Hollenbach, D. & Tielens, A. G. G. M. . *Astrophys. J.* **587**, 278–311 (2003).

(ref: 2022MNRAS.510.4436M) Méndez-Delgado, J. E. *et al.* . *Mon. Not. R. Astron. Soc.* **510**, 4436–4455 (2022).

(ref: chiappini2008chemical) Chiappini, C. The chemical evolution of the galactic thick and thin disks. *Proceedings of the International Astronomical Union* **4**, 191–196 (2008).

(ref: 2014Natur.514..335S) Shi, Y. *et al.* . *Nature* **514**, 335–338 (2014).

(ref: 2014A&A...561A..49H) Hunt, L. K. *et al.* . *Astron. Astrophys.* **561**, A49 (2014).

(ref: 2020A&A...640A.125J) Jacob, A. M. *et al.* . *Astron. Astrophys.* **640**, A125 (2020).

(ref: 2019ApJ...885..131R) Reid, M. J. *et al.* . *Astrophys. J.* **885**, 131 (2019).

(ref: 1992ApJ...384..508R) Russell, S. C. & Dopita, M. A. . *Astrophys. J.* **384**, 508 (1992).

(ref: 2018ApJ...853..111J) Jameson, K. E. *et al.* . *Astrophys. J.* **853**, 111 (2018).

(ref: 2003ASPC..304..187P) Pagel, B. E. J. . In Charbonnel, C., Schaerer, D. & Meynet, G. (eds.) *CNO in the Universe*, vol. 304 of *Astronomical Society of the Pacific Conference Series*, 187 (2003).

(ref: 2016A&A...586A..59G) Garcı́a-Rojas, J., Peña, M., Flores-Durán, S. & Hernández-Martı́nez, L. . *Astron. Astrophys.* **586**, A59 (2016).

(ref: 2020ApJ...892..147S) Shi, Y. *et al.* . *Astrophys. J.* **892**, 147 (2020).

(ref: 2023ApJ...949...63O) Ohno, T. *et al.* . *Astrophys. J.* **949**, 63 (2023).

(ref: spitzer2008physical) Spitzer Jr, L. *Physical processes in the interstellar medium* (John Wiley & Sons, 2008).

(ref: 1998ApJ...503..689W) Williams, J. P., Bergin, E. A., Caselli, P., Myers, P. C. & Plume, R. . *Astrophys. J.* **503**, 689–699 (1998).

(ref: 2010ApJ...725..466C) Crutcher, R. M., Wandelt, B., Heiles, C., Falgarone, E. & Troland, T. H. . *Astrophys. J.* **725**, 466–479 (2010).

(ref: 2023ApJ...954...38K) Kobayashi, M. I. N. *et al.* . *Astrophys. J.* **954**, 38 (2023).

(ref: lequeux2004interstellar) Lequeux, J. *The interstellar medium* (Springer Science & Business Media, 2004).

(ref: 2011MNRAS.416..710F) Field, G. B., Blackman, E. G. & Keto, E. R. *Mon. Not. R. Astron. Soc.* **416**, 710–714 (2011).

(ref: 2022MNRAS.515.2822R) Ramı́rez-Galeano, L., Ballesteros-Paredes, J., Smith, R. J., Camacho, V. & Zamora-Avilés, M. . *Mon. Not. R. Astron. Soc.* **515**, 2822–2836 (2022).

(ref: 2023NatAs...7..622C) Curtis-Lake, E. *et al.* . *Nature Astronomy* **7**, 622–632 (2023).

(ref: 1989A&AS...80..149W) Wouterloot, J. G. A. & Brand, J. *Astron. Astrophys. Suppl.* **80**, 149–187 (1989).

(ref: 2015ApJ...798L..27S) Sun, Y. *et al.* . *Astrophys. J. Let.* **798**, L27 (2015).

(ref: 2016RAA....16...47L) Li, H.-K. *et al.* . *Research in Astronomy and Astrophysics* **16**, 47 (2016).

(ref: 2017ApJS..230...17S) Sun, Y. *et al.* . *Astrophys. Js* **230**, 17 (2017).

(ref: 2006ApJS..163..145J) Jackson, J. M. *et al.* . *Astrophys. Js* **163**, 145–159 (2006).

(ref: 2019Natur.567..200P) Pietrzyński, G. *et al.* . *Nature* **567**, 200–203 (2019).

(ref: 2020ApJ...904...13G) Graczyk, D. *et al.* . *Astrophys. J.* **904**, 13 (2020).

(ref: 2014ApJ...794..107R) Rich, J. A. *et al.* . *Astrophys. J.* **794**, 107 (2014).

(ref: 2012MNRAS.421.3242W) Whiting, M. T. . *Mon. Not. R. Astron. Soc.* **421**, 3242–3256 (2012).

(ref: 2015MNRAS.451.3021D) Di Teodoro, E. M. & Fraternali, F. . *Mon. Not. R. Astron. Soc.* **451**, 3021–3033 (2015).

(ref: 2015PASP..127..266M) Mangum, J. G. & Shirley, Y. L. . *Publ. Astron. Soc. Pac.* **127**, 266 (2015).

(ref: 2017A&A...598A..30T) Tang, X. D. *et al.* . *Astron. Astrophys.* **598**, A30 (2017).

(ref: 2013A&A...552A..40C) Chira, R. A. *et al.* . *Astron. Astrophys.* **552**, A40 (2013).

(ref: 2022ApJS..258...17F) Fehér, O. *et al.* . *Astrophys. Js* **258**, 17 (2022).

(ref: 1991ApJ...374..540G) Garden, R. P., Hayashi, M., Gatley, I., Hasegawa, T. & Kaifu, N. . *Astrophys. J.* **374**, 540 (1991).

(ref: 2017ApJ...838...66L) Lacy, J. H., Sneden, C., Kim, H. & Jaffe, D. T. . *Astrophys. J.* **838**, 66 (2017).

(ref: 2014ApJ...796..123F) Fujii, K. *et al.* . *Astrophys. J.* **796**, 123 (2014).

(ref: 1997PASP..109..166C) Condon, J. J. . *Publ. Astron. Soc. Pac.* **109**, 166–172 (1997).

(ref: 2002ApJS..143..469M) Mueller, K. E., Shirley, Y. L., Evans, I., Neal J. & Jacobson, H. R. . *Astrophys. Js* **143**, 469–497 (2002).

(ref: 1996A&AS..119..439W) Wouterloot, J. G. A. & Brand, J. *Astron. Astrophys. Suppl.* **119**, 439–457 (1996).

(ref: 2005ApJ...634.1126M) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M. & Wyckoff, S. . *Astrophys. J.* **634**, 1126–1132 (2005).

(ref: 2024MNRAS.527.8151S) Sun, Y. *et al.* . *Mon. Not. R. Astron. Soc.* **527**, 8151–8192 (2024).

(ref: 2014MNRAS.445.4055S) Szűcs, L., Glover, S. C. O. & Klessen, R. S. . *Mon. Not. R. Astron. Soc.* **445**, 4055–4072 (2014).

(ref: 1978ApJS...37..407D) Dickman, R. L. *Astrophys. Js* **37**, 407–427 (1978).

(ref: 1982ApJ...262..590F) Frerking, M. A., Langer, W. D. & Wilson, R. W. *Astrophys. J.* **262**, 590–605 (1982).

(ref: 2019MNRAS.490.2838R) Romano, D., Matteucci, F., Zhang, Z.-Y., Ivison, R. J. & Ventura, P. . *Mon. Not. R. Astron. Soc.* **490**, 2838–2854 (2019).

(ref: 2012MNRAS.426..377G) Glover, S. C. O. & Clark, P. C. . *Mon. Not. R. Astron. Soc.* **426**, 377–388 (2012).

(ref: 2013ApJ...779..185K) Kauffmann, J., Pillai, T. & Goldsmith, P. F. . *Astrophys. J.* **779**, 185 (2013).

(ref: 2018ApJ...854..100M) Meidt, S. E. *et al.* . *Astrophys. J.* **854**, 100 (2018).

(ref: 2014A&A...568A.122Z) Zhang, Z.-Y. *et al.* . *Astron. Astrophys.* **568**, A122 (2014).

(ref: 1999ApJ...516..114P) Papadopoulos, P. P. & Seaquist, E. R. . *Astrophys. J.* **516**, 114–126 (1999).

(ref: 1979ApJ...232..729E) Elmegreen, B. G. *Astrophys. J.* **232**, 729–739 (1979).

(ref: 2023pcsf.conf..237P) Padovani, M. . In *Physics and Chemistry of Star Formation: The Dynamical ISM Across Time and Spatial Scales*, 237 (2023).

(ref: 2012ARA&A..50...29C) Crutcher, R. M. . *Annu. Rev. Astron. Astrophys.* **50**, 29–63 (2012).

(ref: 2022Natur.601...49C) Ching, T. C. *et al.* . *Nature* **601**, 49–52 (2022).

(ref: 2023ApJ...946L..46C) Cao, Z. & Li, H.-b. . *Astrophys. J. Let.* **946**, L46 (2023).

(ref: 2013MNRAS.433.1675B) Basu, A. & Roy, S. . *Mon. Not. R. Astron. Soc.* **433**, 1675–1686 (2013).

(ref: 2015A&A...578A..93B) Beck, R. . *Astron. Astrophys.* **578**, A93 (2015).

(ref: 2013ApJ...768L...5L) Li, D., Kauffmann, J., Zhang, Q. & Chen, W. . *Astrophys. J. Let.* **768**, L5 (2013).

(ref: 2024ApJ...974L...6W) Wang, K., Wang, Y. & Xu, F. . *Astrophys. J. Let.* **974**, L6 (2024).

(ref: 2006ApJ...638..191K) Koda, J., Sawada, T., Hasegawa, T. & Scoville, N. Z. . *Astrophys. J.* **638**, 191–195 (2006).

(ref: 2006ApJ...641L.121T) Tan, J. C., Krumholz, M. R. & McKee, C. F. . *Astrophys. J. Let.* **641**, L121–L124 (2006).

(ref: 2016ApJ...822...11P) Padoan, P., Pan, L., Haugbølle, T. & Nordlund, Å. . *Astrophys. J.* **822**, 11 (2016).

(ref: 2020MNRAS.496.5211A) Aouad, C. J., James, P. A. & Chilingarian, I. V. . *Mon. Not. R. Astron. Soc.* **496**, 5211–5226 (2020).

(ref: 2016ApJ...833..229L) Lee, E. J., Miville-Deschênes, M.-A. & Murray, N. W. . *Astrophys. J.* **833**, 229 (2016).

(ref: 2022ApJ...941..162E) Elia, D. *et al.* . *Astrophys. J.* **941**, 162 (2022).

(ref: lada1987star) Lada, C. J. Star formation: from ob associations to protostars. In *Symposium-International astronomical union*, vol. 115, 1–18 (Cambridge University Press, 1987).

(ref: 2012ApJ...747...22H) Hansen, C. E., Klein, R. I., McKee, C. F. & Fisher, R. T. . *Astrophys. J.* **747**, 22 (2012).

(ref: 2015ApJS..219...20L) Li, H. *et al.* . *Astrophys. Js* **219**, 20 (2015).

(ref: 2018ApJ...869..148S) Sun, Y. *et al.* . *Astrophys. J.* **869**, 148 (2018).

(ref: 2015PASP..127..299S) Shirley, Y. L. . *Publ. Astron. Soc. Pac.* **127**, 299 (2015).

(ref: 2013ARA&A..51..105C) Carilli, C. L. & Walter, F. . *Annu. Rev. Astron. Astrophys.* **51**, 105–161 (2013).

(ref: draine2010physics) Draine, B. T. *Physics of the interstellar and intergalactic medium*, vol. 19 (Princeton University Press, 2010).

(ref: 2001ApJ...562..348O) Oka, T. *et al.* . *Astrophys. J.* **562**, 348–362 (2001).

(ref: Lin2024) Lin, L. . `https://doi.org/10.6084/m9.figshare.27282924` (2024).

(ref: 2023A&A...678A.208J) Jiao, Y. *et al.* . *Astron. Astrophys.* **678**, A208 (2023).

+:----------:+:------------:+:------------:+:-------------:+:------------:+:-----------:+:---------------:+:----------------:+:----------------------:+:--------------------:+:------------------:+
| Target     | $l$          | $b$          | $V_{\rm LSR}$ | $R_{\rm gc}$ | $d$         | $R_{\rm cloud}$ | $\sigma_{\rm v}$ | $M_{\rm cloud}$        | $n_{\rm H_{2}}$      | $\alpha_{\rm vir}$ |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
|            | ($^{\circ}$) | ($^{\circ}$) | (km s$^{-1}$) | (kpc)        | (kpc)       | (pc)            | (km s$^{-1}$)    | (10$^{3}$ $M_{\odot}$) | (10$^{4}$ cm$^{-3}$) |                    |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| IRAM 30-m (2016)                                                                                                                                                                                |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| G37.350    | 37.35        | 1.06         | -54.0         | 13.2$\pm$1   | 18.7$\pm$1  | 1.0$\pm$0.1     | 0.9$\pm$0.09     | 1.1$\pm$0.2            | 0.3                  | 1.0$\pm$0.3        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| G44.8      | 44.80        | 0.66         | -61.9         | 13.0$\pm$1   | 17.5$\pm$1  | 0.9$\pm$0.1     | 1.0$\pm$0.1      | 0.9$\pm$0.2            | 0.5                  | 1.1$\pm$0.3        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| IRAS0245   | 136.35       | 0.96         | -61.5         | 13.2$\pm$1   | 6.0$\pm$1   | 0.4$\pm$0.08    | 0.7$\pm$0.07     | 0.4$\pm$0.07           | 2                    | 0.7$\pm$0.3        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_14N  | 109.29       | 2.08         | -101.1        | 14.9$\pm$1   | 10.1$\pm$1  | 0.9$\pm$0.1     | 0.5$\pm$0.05     | 0.4$\pm$0.08           | 0.2                  | 0.7$\pm$0.2        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_18   | 109.79       | 2.71         | -99.1         | 14.7$\pm$0.9 | 9.8$\pm$1   | 0.7$\pm$0.1     | 0.4$\pm$0.04     | 0.3$\pm$0.07           | 0.4                  | 0.4$\pm$0.1        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_21\* | 114.34       | 0.79         | -101.0        | 15.4$\pm$1   | 10.1$\pm$1  | 1.4$\pm$0.2     | 0.5$\pm$0.05     | 0.8$\pm$0.2            | 0.1                  | 0.6$\pm$0.2        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_34   | 122.77       | 2.52         | -107.0        | 17.8$\pm$2   | 12.0$\pm$2  | 1.1$\pm$0.2     | 0.5$\pm$0.05     | 0.8$\pm$0.2            | 0.2                  | 0.4$\pm$0.1        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_56   | 137.77       | -0.97        | -103.1        | 24.1$\pm$4   | 17.4$\pm$4  | 2.7$\pm$0.6     | 0.7$\pm$0.07     | 13.6$\pm$3             | 0.3                  | 0.1$\pm$0.04       |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_57   | 137.78       | -1.07        | -102.2        | 23.7$\pm$3   | 17.0$\pm$4  | 1.4$\pm$0.3     | 0.6$\pm$0.06     | 3.2$\pm$0.6            | 0.4                  | 0.2$\pm$0.07       |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_7W   | 104.98       | 3.31         | -102.6        | 14.8$\pm$0.9 | 10.5$\pm$1  | 0.7$\pm$0.1     | 0.6$\pm$0.06     | 0.3$\pm$0.07           | 0.4                  | 0.9$\pm$0.3        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_380\* | 124.65       | 2.54         | -86.2         | 14.7$\pm$1   | 8.5$\pm$1   | 1.1$\pm$0.2     | 1.4$\pm$0.1      | 2.2$\pm$0.4            | 0.5                  | 1.2$\pm$0.4        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_391\* | 125.80       | 3.05         | -86.1         | 14.9$\pm$1   | 8.6$\pm$1   | 0.5$\pm$0.09    | 0.7$\pm$0.07     | 0.4$\pm$0.08           | 1                    | 0.7$\pm$0.2        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_437   | 135.28       | 2.80         | -71.8         | 13.4$\pm$0.6 | 6.3$\pm$0.6 | 0.5$\pm$0.07    | 1.2$\pm$0.1      | 0.5$\pm$0.1            | 1                    | 1.5$\pm$0.5        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_501   | 145.20       | 2.98         | -58.2         | 14.6$\pm$1   | 7.1$\pm$2   | 0.3$\pm$0.07    | 0.8$\pm$0.08     | 0.3$\pm$0.07           | 4                    | 0.7$\pm$0.3        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| IRAM 30-m (2023)                                                                                                                                                                                |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_23   | 116.72       | 3.54         | -107.2        | 16.6$\pm$1   | 11.3$\pm$1  | 0.7$\pm$0.1     | 0.6$\pm$0.06     | 0.4$\pm$0.07           | 0.4                  | 0.8$\pm$0.3        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_25   | 117.58       | 3.95         | -106.0        | 16.6$\pm$1   | 11.2$\pm$1  | 0.3$\pm$0.05    | 0.5$\pm$0.05     | 0.2$\pm$0.04           | 2                    | 0.5$\pm$0.2        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_30   | 121.81       | 3.05         | -104.1        | 17.0$\pm$1   | 11.3$\pm$2  | 0.8$\pm$0.1     | 0.6$\pm$0.06     | 0.5$\pm$0.1            | 0.3                  | 0.7$\pm$0.2        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_53   | 137.29       | -1.16        | -101.5        | 23.0$\pm$3   | 16.3$\pm$3  | 2.3$\pm$0.5     | 0.5$\pm$0.05     | 1.4$\pm$0.3            | 0.04                 | 0.4$\pm$0.2        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_55   | 137.62       | -1.23        | -98.8         | 22.1$\pm$3   | 15.4$\pm$3  | 1.1$\pm$0.2     | 0.5$\pm$0.05     | 0.9$\pm$0.2            | 0.2                  | 0.4$\pm$0.1        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_59   | 139.12       | -1.47        | -96.6         | 22.4$\pm$3   | 15.6$\pm$3  | 0.5$\pm$0.1     | 0.4$\pm$0.04     | 0.5$\pm$0.1            | 1                    | 0.2$\pm$0.06       |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_69   | 145.21       | -0.39        | -74.0         | 18.5$\pm$2   | 11.2$\pm$2  | 1.2$\pm$0.3     | 0.5$\pm$0.05     | 0.4$\pm$0.08           | 0.08                 | 0.8$\pm$0.3        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_72   | 146.06       | -1.65        | -77.4         | 20.3$\pm$3   | 13.1$\pm$3  | 1.9$\pm$0.5     | 0.5$\pm$0.05     | 0.9$\pm$0.2            | 0.05                 | 0.6$\pm$0.2        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SMT (2022)                                                                                                                                                                                      |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| SUN15_47   | 131.16       | 1.39         | -100.4        | 19.0$\pm$2   | 12.6$\pm$2  | 0.2$\pm$0.03    | 0.3$\pm$0.03     | 0.1$\pm$0.03           | 8                    | 0.2$\pm$0.06       |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_379   | 124.56       | 2.52         | -88.1         | 15.0$\pm$1   | 8.8$\pm$1   | 0.5$\pm$0.09    | 0.9$\pm$0.09     | 0.3$\pm$0.07           | 0.9                  | 1.5$\pm$0.5        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_434   | 135.99       | 0.67         | -78.0         | 15.7$\pm$1   | 8.8$\pm$2   | 0.5$\pm$0.09    | 0.5$\pm$0.05     | 0.1$\pm$0.01           | 0.3                  | 2.0$\pm$0.7        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_365   | 123.07       | 1.35         | -90.9         | 15.1$\pm$1   | 9.1$\pm$1   | 0.5$\pm$0.08    | 0.5$\pm$0.05     | 0.1$\pm$0.01           | 0.2                  | 2.6$\pm$0.8        |
+------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+

+:---------------:+:------------:+:------------:+:-------------:+:------------:+:-----------:+:---------------:+:----------------:+:----------------------:+:--------------------:+:------------------:+
| Target          | $l$          | $b$          | $V_{\rm LSR}$ | $R_{\rm gc}$ | $d$         | $R_{\rm cloud}$ | $\sigma_{\rm v}$ | $M_{\rm cloud}$        | $n_{\rm H_{2}}$      | $\alpha_{\rm vir}$ |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
|                 | ($^{\circ}$) | ($^{\circ}$) | (km s$^{-1}$) | (kpc)        | (kpc)       | (pc)            | (km s$^{-1}$)    | (10$^{3}$ $M_{\odot}$) | (10$^{4}$ cm$^{-3}$) |                    |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| ALMA Total Power (Cycle 8)                                                                                                                                                                           |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_766        | 193.43       | -1.17        | 22.3          | 14.4$\pm$3   | 6.4$\pm$3   | 0.6$\pm$0.3     | 1.1$\pm$0.1      | 0.4$\pm$0.07           | 0.5                  | 2.3$\pm$1          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_770\*      | 192.91       | -0.63        | 22.6          | 15.0$\pm$3   | 7.0$\pm$3   | 0.4$\pm$0.2     | 0.9$\pm$0.09     | 0.3$\pm$0.07           | 3                    | 1.0$\pm$0.5        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1086       | 245.93       | 1.17         | 63.5          | 11.6$\pm$0.6 | 5.6$\pm$0.8 | 0.8$\pm$0.1     | 0.7$\pm$0.07     | 0.3$\pm$0.06           | 0.2                  | 1.8$\pm$0.6        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_765\*      | 196.83       | -3.11        | 25.7          | 12.2$\pm$0.2 | 4.1$\pm$0.2 | 0.4$\pm$0.05    | 0.8$\pm$0.08     | 0.2$\pm$0.05           | 1                    | 1.5$\pm$0.5        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_771        | 193.69       | -1.06        | 22.9          | 14.5$\pm$3   | 6.4$\pm$3   | 0.7$\pm$0.3     | 0.9$\pm$0.09     | 0.2$\pm$0.04           | 0.3                  | 2.7$\pm$1          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1010       | 230.55       | 1.92         | 63.1          | 11.7$\pm$0.3 | 4.7$\pm$0.3 | 0.4$\pm$0.04    | 0.6$\pm$0.06     | 0.1$\pm$0.02           | 0.5                  | 2.1$\pm$0.6        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1049\*     | 241.54       | -0.60        | 70.5          | 11.9$\pm$0.4 | 5.6$\pm$0.5 | 0.9$\pm$0.1     | 0.8$\pm$0.08     | 0.3$\pm$0.07           | 0.2                  | 1.9$\pm$0.6        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1048\*     | 240.32       | 0.07         | 67.8          | 11.9$\pm$0.4 | 5.5$\pm$0.5 | 0.4$\pm$0.06    | 2.4$\pm$0.2      | 0.4$\pm$0.09           | 2                    | 6.5$\pm$2          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1158$\dag$ | 260.69       | -1.39        | 66.3          | 11.5$\pm$0.5 | 6.8$\pm$0.8 | 1.0$\pm$0.2     | 1.2$\pm$0.1      | 0.4$\pm$0.09           | 0.1                  | 3.8$\pm$1          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_782\*      | 196.46       | -1.68        | 17.1          | 12.2$\pm$0.2 | 4.1$\pm$0.2 | 0.6$\pm$0.07    | 1.5$\pm$0.2      | 0.7$\pm$0.1            | 1                    | 2.3$\pm$0.7        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_959        | 231.52       | -4.30        | 52.9          | 11.5$\pm$0.7 | 4.5$\pm$0.8 | 0.6$\pm$0.1     | 1.0$\pm$0.1      | 0.2$\pm$0.04           | 0.3                  | 3.5$\pm$1          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_886        | 212.06       | -0.74        | 44.6          | 11.9$\pm$0.2 | 4.2$\pm$0.2 | 0.3$\pm$0.04    | 1.6$\pm$0.2      | 0.1$\pm$0.03           | 1                    | 7.4$\pm$2          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_905        | 211.59       | 1.06         | 44.8          | 11.9$\pm$0.2 | 4.2$\pm$0.2 | 0.4$\pm$0.04    | 1.6$\pm$0.2      | 0.2$\pm$0.04           | 1                    | 5.7$\pm$2          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1236$\dag$ | 269.22       | -0.31        | 74.8          | 12.0$\pm$0.6 | 8.7$\pm$0.8 | 0.8$\pm$0.1     | 0.7$\pm$0.07     | 0.2$\pm$0.04           | 0.1                  | 2.2$\pm$0.7        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_762        | 190.97       | -0.06        | 11.0          | 11.1$\pm$3   | 3.0$\pm$3   | 0.5$\pm$0.5     | 0.5$\pm$0.05     | 0.1$\pm$0.01           | 0.2                  | 2.1$\pm$2          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_904        | 211.04       | 1.18         | 55.2          | 15.0$\pm$2   | 7.4$\pm$2   | 1.1$\pm$0.3     | 0.8$\pm$0.08     | 0.6$\pm$0.1            | 0.1                  | 1.6$\pm$0.6        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_864        | 210.24       | -1.33        | 37.0          | 12.0$\pm$1   | 4.2$\pm$1   | 0.3$\pm$0.09    | 0.8$\pm$0.08     | 0.0$\pm$0.01           | 0.6                  | 4.7$\pm$2          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_985N       | 229.57       | 0.15         | 53.2          | 11.6$\pm$0.2 | 4.6$\pm$0.3 | 0.5$\pm$0.06    | 1.4$\pm$0.1      | 0.2$\pm$0.05           | 0.6                  | 4.9$\pm$2          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_985S       | 229.57       | 0.15         | 53.2          | 11.6$\pm$0.2 | 4.6$\pm$0.3 | 0.5$\pm$0.06    | 1.0$\pm$0.1      | 0.2$\pm$0.04           | 0.5                  | 3.0$\pm$0.9        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_885        | 212.35       | -0.92        | 44.3          | 11.9$\pm$0.2 | 4.2$\pm$0.2 | 0.8$\pm$0.09    | 1.2$\pm$0.1      | 0.3$\pm$0.06           | 0.2                  | 4.3$\pm$1          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1145$\dag$ | 259.24       | -1.63        | 62.7          | 11.2$\pm$0.5 | 6.4$\pm$0.8 | 0.3$\pm$0.05    | 0.7$\pm$0.07     | 0.0$\pm$0.01           | 0.5                  | 4.1$\pm$1          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1245$\dag$ | 269.85       | -0.06        | 74.4          | 12.0$\pm$0.6 | 8.7$\pm$0.8 | 0.9$\pm$0.1     | 1.6$\pm$0.2      | 0.7$\pm$0.1            | 0.3                  | 4.0$\pm$1          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_920        | 215.19       | 0.81         | 48.7          | 12.8$\pm$1   | 5.2$\pm$1   | 0.9$\pm$0.2     | 0.8$\pm$0.08     | 0.4$\pm$0.08           | 0.2                  | 1.8$\pm$0.7        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_1057       | 242.94       | -0.45        | 63.6          | 11.7$\pm$0.6 | 5.5$\pm$0.8 | 0.6$\pm$0.1     | 1.6$\pm$0.2      | 0.2$\pm$0.04           | 0.3                  | 8.8$\pm$3          |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_758        | 193.31       | -1.45        | 28.7          | 18.5$\pm$4   | 10.5$\pm$4  | 0.7$\pm$0.3     | 0.7$\pm$0.07     | 0.3$\pm$0.07           | 0.3                  | 1.2$\pm$0.6        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+
| WB89_916        | 212.96       | 1.30         | 42.4          | 11.9$\pm$0.2 | 4.2$\pm$0.2 | 0.8$\pm$0.09    | 0.9$\pm$0.09     | 0.2$\pm$0.05           | 0.2                  | 2.9$\pm$0.9        |
+-----------------+--------------+--------------+---------------+--------------+-------------+-----------------+------------------+------------------------+----------------------+--------------------+

</paper>

Write the methods card for this paper.