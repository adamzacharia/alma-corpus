# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...653A.111R\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...653A.111R",
 "title": "The ALPINE-ALMA [CII] survey. The contribution of major mergers to the galaxy mass assembly at z ∼ 5",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Romano, M.",
 "n_authors": 28,
 "arxiv_id": "2107.10856",
 "doi": "10.1051/0004-6361/202141306",
 "alma_projects_linked_by_archive": [
  "2017.1.00428.L"
 ]
}
```

Paper text:
<paper>
# The ALPINE-ALMA \[CII\] survey: The contribution of major mergers to the galaxy mass assembly at z$\sim$5

Galaxy mergers are thought to be one of the main mechanisms of the mass assembly of galaxies in the Universe, but there is still little direct observational evidence of how frequent they are at $z\gtrsim4$. Recently, many works have suggested a possible increase in the fraction of major mergers in the early Universe, reviving the debate on which processes (e.g., cold accretion, star formation, mergers) most contribute to the mass build-up of galaxies through cosmic time.

To estimate the importance of major mergers in this context, we make use of the new data collected by the ALMA Large Program to INvestigate \[CII\] at Early times (ALPINE) survey, which attempted to observe the \[CII\] 158 $\mu$m emission line from a sample of 75 main-sequence star-forming galaxies at $4.4<z<5.9$.

We used, for the first time, the morpho-kinematic information provided by the \[CII\] emission, along with archival multiwavelength data to obtain the fraction of major mergers ($f_{\text{MM}}$) at $z\sim5$. By combining the results from ALPINE with those at lower redshifts from the literature, we also studied the evolution of the merger fraction through cosmic time. We then used different redshift-evolving merger timescales ($T_{\text{MM}}$) to convert this fraction into the merger rate per galaxy ($R_{\text{MM}}$) and in the volume-averaged merger rate ($\Gamma_{\text{MM}}$).

We find a merger fraction of $f_{\text{MM}}\sim0.44$ (0.34) at $z\sim4.5$ (5.5) from ALPINE. By combining our results with those at lower redshifts, we computed the cosmic evolution of the merger fraction which is described by a rapid increase from the local Universe to higher redshifts, a peak at $z\sim3$, and a slow decrease toward earlier epochs. Depending on the timescale prescription used, this fraction translates into a merger rate ranging between $\sim0.1$ and $\sim4.0$ Gyr$^{-1}$ at $z\sim5$, which in turn corresponds to an average number of major mergers per galaxy between 1 and 8 in $\sim12.5$ Gyr (from $z=6$ to the local Universe). When convolved with the galaxy number density at different epochs, the merger rate density becomes approximately constant over time at $1<z<4$, including values from $10^{-4}$ to $10^{-3}$ Gyr$^{-1}$ Mpc$^{-3}$, depending on the assumed $T_{\text{MM}}$. We finally compare the specific star formation and star-formation rate density with the analogous quantities from major mergers, finding a good agreement at $z>4$ if we assume a merger timescale that quickly decreases with increasing redshift.

Our new constraints on the merger fraction from the ALPINE survey at $z\sim5$ reveal the presence of a significant merging activity in the early Universe. Whether this population of mergers can provide a relevant contribution to the galaxy mass assembly at these redshifts and through the cosmic epochs is strongly dependent on the assumption of the merger timescale. However, our results show that an evolving $T_{\text{MM}}\propto(1+z)^{-2}$ agrees well with state-of-the-art cosmological simulations, suggesting a considerable role of mergers in the build-up of galaxies at early times.

# Introduction

How galaxies grow their stellar mass through cosmic time is still one of the most puzzling questions of modern cosmology. During the last decades, two major physical mechanisms have been proposed to contribute or dominate the build-up of galaxies at different epochs of the Universe: the accretion of cold gas (both from the internal reservoir or from the outer environment of galaxies) and the merging of galaxies.

The first process requires the supply of new cold gas to the galaxy from the filaments of the cosmic web, refreshing and/or enhancing the star formation (e.g., (cite: Keres05; Dekel09)). Although this could be one of the main modes of galaxy assembly (e.g., (cite: Keres09; Bouche10)), direct observations of gas flowing through the filaments are tricky while indirect evidence has increased over the last years (cite: Bouche13; Bouche16; Zabl19). However, in situ star formation is observable through a variety of different proxies and up to the earliest epochs (e.g., (cite: Madau14) and references therein).

Galaxy mergers are also thought to play an important role in the stellar mass growth over cosmic time. They are relatively common through the history of the Universe and are observable with different methods and at different stages. The merging of galaxies is a natural prediction of the hierarchical structure formation model (cite: White91; Springel05; Klypin11) for which dark matter halos grow their mass and affect the build-up of galaxies in the Universe (cite: Kauffmann93; Khochfar05). Not only can mergers increase the stellar mass of galaxies (up to a factor of 2 for major mergers, i.e., for galaxies of nearly equal stellar mass; (cite: Lopez12; Oser12; Kaviraj14)), but they can also trigger starbursts and active galactic nuclei (AGN; (cite: Silk98; Kartaltepe12; Chiaberge15); see also (cite: Shah20) who found that galaxy interactions do not significantly enhance AGN activity up to $z\sim3$), in some cases blowing the gas out from the galaxy which arrests, at least temporarily, the formation of new stars (cite: Silk98; Fabian06; Cattaneo09). Therefore, observing mergers at different epochs is key to shed light on the relative contribution of the distinct processes that rule the assembly of galaxies in the Universe.

Depending on which phase the merger is passing through, there are two main ways to estimate the incidence of such events at a given epoch. On-going and post-mergers could lead to the formation of post-starburst (PSB) galaxies (at least in groups or clusters; e.g., (cite: Wu14; Lemaux17)) and leave morphological or kinematic imprint on the merging or coalesced system such as tails of stripped material, irregular shapes, disturbed velocity fields, and/or deep absorption lines in the spectra of PSBs (e.g., (cite: LeFevre00; Conselice03; Conselice08; Jogee09; Wild09; Casteels14)). However, observations of these features could be hampered by the spatial resolution needed to resolve the morphological details highlighting the presence of a merger (especially at high redshifts), or confused by diverse galaxy types that can mimic the kinematics or morphology of a merging system.

On the other hand, galaxy pairs that are going to merge in a certain timescale can also be identified based on some selection criteria regarding their spatial and velocity separation (e.g., (cite: LeFevre00; Patton2000; Lin2008; deRavel09; Lopez12; Ventou17; Mantha18; Duncan19)). Typically, close pairs must lie within a defined radius with a projected separation in the sky that could be as wide as 50 kpc and, in case of spectroscopic surveys, have a relative velocity not larger than $\Delta v=500$ km s$^{-1}$ (i.e., $\Delta z\sim0.0017$) which excludes those pairs that are not gravitationally bound (e.g., (cite: Patton2000)).

Both these methods can provide an estimate of the merger fraction through cosmic time but, as they probe different phases and timescales of the merging, they can lead to discordant results if not interpreted properly. However, even by adopting the same observational method, a large scatter is present in the literature for the merger fraction and the corresponding merger rate at all redshifts. This could be attributed to several reasons: i) the different criteria used for selecting galaxy pairs; ii) the distinction between major and minor mergers for which a dual uncertainty has to be taken into account, both in the pair ratio which can be obtained from the stellar mass (cite: Lopez13; Tasca14; Man16; Ventou17; Duncan19) or the flux (cite: Bluck12; Man12; Man16; Lopez15), and in the major (or minor) merger definition having a threshold in mass or flux ratio ranging between 2-6 (cite: Xu12; Ventou17; Ventou19); iii) the merger timescale used to convert the pair fraction into a merger rate, which in turn depends on the method used for characterizing mergers, on their selection criteria, and on the properties of the galaxies undergoing a merger (cite: Kitzbichler08; Jiang14; Snyder17).

Several studies tried to constrain the fraction of major mergers and the merger rate out to $z\lesssim2$ (e.g., (cite: deRavel09; Lopez11; Lopez13; Lotz11; Xu12)). During this time, the merger fraction is found to increase with redshift as $\propto (1+z)^m$, where $1\lesssim m \lesssim5$, depending on the luminosity, the stellar mass and the spectral type of galaxies, leading to a large scatter in the literature. Only a handful of works have extended these measurements to higher redshifts. For instance, (cite: Conselice09) used both pair counts and morphological studies to investigate the presence of mergers at $4<z<6$ and their contribution to the galaxy assembly, finding a possible peak in the merger fraction at $z\sim3$ followed by a decline which suggested a deviation from the power-law trend found at lower redshifts. However, the results by (cite: Conselice09) do not distinguish between major and minor mergers and could have been subject to large uncertainties due to photometric redshifts. A peak in the cosmic evolution of the merger fraction is also found at $1\lesssim z \lesssim 3$ by more recent observational studies (e.g., (cite: Mantha18; Duncan19)) which, however, do not provide conclusive statements given the large above-mentioned differences on the selection and definition of the mergers (see for example the results by (cite: Mantha18) for both stellar mass- or flux-selected pairs).

In this paper we take advantage of the recent data collected by the ALMA Large Program to INvestigate \[CII\] at Early times (ALPINE; (cite: Bethermin20; Faisst20; LeFevre20)) to further constrain the importance of major mergers to the galaxy mass assembly at the end of the Reionization epoch and through cosmic time. This survey allows us to add a key additional piece of information to the wealth of multiwavelength data already available for each targeted galaxy thanks to the ALMA observations of the ionized carbon \[CII\] at 158 $\mu$m rest-frame and the surrounding continuum. The 3D (i.e., RA, Dec, velocity) information enclosed in each ALPINE data cube is of great importance for identifying morphological and kinematic disturbances highlighting the presence of possible merging components. In particular, (cite: LeFevre20) made a first fundamental step in the morpho-kinematic classification of the ALPINE galaxies, finding a high fraction ($\sim40\%$) of mergers (both minor and major) at $z\sim5$ among the ALPINE sample. An in-depth analysis of two merging systems found in ALPINE at $z\sim4.6$ was made later by (cite: Jones20) and (cite: Ginolfi20), showing the strength of these observations in the identification and characterization of this kind of sources in the high-redshift Universe.

Previous works estimated the merger fraction by exploiting morphological information or direct pair counts obtained through rest-frame optical observations and photometric or spectroscopic redshifts, as derived from optical ionized gas tracers (e.g., (cite: Conselice09; Xu12; Ventou17)). Here, for the first time, we make use of the rest-frame FIR \[CII\] line to compute the major merger fraction in the early Universe. As this line is less affected by dust extinction than optical tracers, morphological and kinematic analysis of this emission can reveal the presence of mergers with dusty components that are partially or completely obscured in the optical bands. Following these previous studies, we thus refine the fraction of mergers at the redshifts explored by the ALPINE survey and analyze in detail their \[CII\] emission combined with optical data for estimating their incidence at $z>4$ and, along with other values in the literature, through cosmic time.

This paper is structured as follows: in Section 2 we describe the data used to estimate the merger fraction, and the previous works on the morpho-kinematic classification of the ALPINE galaxies on which we based our analysis. The criteria used for selecting mergers from the ALPINE sample, the methods employed for their characterization and the estimated parameters are stated in Section 3. The results on the merger fraction and merger rate, their evolution with the cosmic time and their contribution to the galaxy mass assembly are reported in Section 4. We discuss our results and summarize them in Section 5 and Section 6, respectively.

Throughout this work, we adopt a $\mathrm{\Lambda-CDM}$ cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\mathrm{\Omega_m}=0.3$ and $\mathrm{\Omega_\Lambda}=0.7$. Stellar masses are normalized to a (cite: Chabrier03) initial mass function (IMF).

# Data

The ALPINE survey was designed to detect the \[CII\] line at 158 $\mu$m rest-frame and the surrounding FIR continuum emission from a sample of 118 star-forming galaxies at $4.4<z<5.9$, avoiding the redshift range $4.6<z<5.1$ due to a low-transmission atmospheric window. The campaign took $\sim70$ hours of observation with ALMA in Band 7 (275-373 GHz) during cycles 5 and 6. The ALPINE targets are drawn from the Cosmic Evolution Survey (COSMOS; (cite: Scoville17a; Scoville17b)) and Extended Chandra Deep Field South (E-CDFS; (cite: Giavalisco04; Cardamone10)) fields and have secure spectroscopic redshifts from the VIMOS UltraDeep Survey (VUDS; (cite: LeFevre15; Tasca17)) and DEIMOS 10K Spectroscopic Survey (cite: Hasinger18). The rest-frame UV selection ($\mathrm{L_{UV}>0.6~L^{*}}$) ensures that these sources lie on the so-called main-sequence of star-forming galaxies (e.g., (cite: Noeske07; Rodighiero11; Tasca15)), being thus representative of the underlying star-forming, UV-detected galaxy population at $z\sim5$ (e.g., (cite: Speagle14)). Due to the location of the ALPINE targets in these well-studied fields, archival multiwavelength data are available from the UV to the near-IR (e.g., (cite: Koekemoer07; Sanders07; McCracken12; Guo13; Nayyeri17)), reaching the X-ray and radio bands (e.g., (cite: Hasinger07; Smolcic17)), allowing us to recover physical quantities such as stellar masses ($\mathrm{9\lesssim log(M_{*}/M_{\odot})\lesssim11}$) and star-formation rates (SFRs; $\mathrm{1\lesssim log(SFR/M_{\odot}yr^{-1})\lesssim3}$) through spectral energy distribution (SED)-fitting (cite: Faisst20).

The collected ALMA data were reduced and calibrated using the standard Common Astronomy Software Applications (CASA; (cite: McMullin07)) pipeline and each data cube was continuum-subtracted to obtain line-only cubes with channel width of $\sim25~\mathrm{km~s^{-1}}$ and beam size $\sim1''$ (with a pixel scale of $\sim0.15''$; (cite: Bethermin20)). A line search algorithm was then applied to each continuum-subtracted cube resulting in 75 \[CII\] detections (S/N$>$3.5) out of 118 ALPINE targets (of which 23 sources were also detected in continuum).

For a more in-depth description of the overall ALPINE survey, the observation and data processing, and the multiwavelength analysis see (cite: LeFevre20), (cite: Bethermin20) and (cite: Faisst20), respectively.

## Previous morpho-kinematic classifications

(cite: LeFevre20) performed a preliminary morphological and kinematic classification of the 75 ALPINE targets showing \[CII\] emission. In particular, the channel maps around the emission line, the intensity (moment-0) and velocity (moment-1) maps, the integrated \[CII\] spectra, the position-velocity diagrams (PVDs) along the major and minor axis of velocity maps, and the multiwavelength data at the position of the source were visually inspected by an internal team of the ALPINE collaboration that placed these galaxies in the following classes:

1.  *Rotators*. The galaxies in this class are characterized by a single source in the ancillary data and show a clear velocity gradient in the moment-1 maps which then implies a tilted (straight) PVD along the major (minor) axis. They can also exhibit a double-horned profile in the integrated spectra.

2.  *Mergers*. In case of interacting systems the presence of two or more components in the optical images within the ALMA field of view and/or in the moment-0 maps and PVDs is expected. A complex behavior in the channel maps and in the \[CII\] spectra could be visible.

3.  *Extended Dispersion Dominated*. These sources extend in \[CII\] emission over multiple ALMA beams and are typically characterized by straight PVDs along the major and minor axis and by a Gaussian line profile.

4.  *Compact Dispersion Dominated*. As opposed to the class 3 galaxies, these objects are unresolved in the moment-0 maps.

5.  *Weak*. These targets are too weak to be visually classified into one of the above classes.

(cite: LeFevre20) found that $\sim40\%$ of the ALPINE galaxies are undergoing a merging phase and that $\sim13\%$ of the targets are possibly forming an ordered disk at $z\sim5$. Extended and compact sources make up 20$\%$ and 11$\%$ of the sample, respectively, with the remaining galaxies (16$\%$) being too complex or weak to be classified. These results possibly suggest a large contribution of the mergers to the galaxy mass assembly at $z\sim5$. However, such a qualitative classification could be prone to different kinds of uncertainties arising from the subjectivity of the method.

On the other hand, (cite: Jones21) expanded this initial classification of the ALPINE targets by using the tilted ring fitting code $\mathrm{^{3D}Barolo}$ (3D-Based Analysis of Rotating Objects from Line Observations; (cite: DiTeodoro15)). Their selection criteria led to a successful fit of $39\%$ of the ALPINE parent sample (i.e., 29 out of 75 sources) and to a robust classification of 14 sources. This new quantitative analysis confirmed the morpho-kinematic diversity of the ALPINE galaxies found by (cite: LeFevre20) but resulted in a somewhat different statistics with $43\%$ of rotators, $36\%$ of mergers, and $21\%$ of dispersion-dominated galaxies.

As we aim to compute the contribution of mergers to the galaxy mass assembly in the early Universe, a robust estimate of the fraction of mergers at $z\sim5$ is required. We thus perform a further and in-depth morpho-kinematic investigation of the ALPINE \[CII\]-detected galaxies based on the same classification criteria used in (cite: LeFevre20) and on the results by (cite: Jones21).

# Methods

To examine the merger fraction at $z\sim5$, we take advantage of the continuum and \[CII\] emission maps of the targets from the ALPINE data release 1 (DR1; (cite: Bethermin20))[^3]. Briefly, for each source the CASA task `UVCONTSUB` was used to obtain line-only cubes. The continuum was first estimated in the uv-plane by masking the spectral channels containing line emission[^4] and fitting a model to the visibilities, and it was then subtracted to the data cubes. With the CASA `IMMOMENTS` task the spectral channels that included the emission line were summed up to produce the velocity-integrated intensity (moment-0) maps, that is $M_0(x,y) = \Delta v \sum_{i}I_i(x,y)$, where $I_i$ is the intensity of the $i$-th pixel at the position $(x,y)$, $\Delta v$ is the velocity width between two consecutive channels, and the sum is over all the channels containing the spectral line (cite: Bethermin20). By masking all the pixels below $3\sigma$ (where $\sigma$ is the rms estimated in the moment-0 map), we also compute the intensity-weighted velocity (moment-1) and velocity dispersion (moment-2) maps, defined as $M_1 = \sum_{i}I_i v_i/M_0$ and $M_2 = \sqrt{\sum_{i}I_i(v_i-M_1)^2/M_0}$, respectively. It is worth noting that in the analysis by (cite: LeFevre20) the morphology and kinematic of the \[CII\] line were inspected within the $2\sigma$ emission contours of the moment maps. In this work, we decide to select only the pixels above the $3\sigma$ level in order to be less affected by possible spurious emissions that could alter the effective morphology and velocity field of the targets (however, we find that this choice does not significantly change our final results).

With the CASA `IMFIT` task we fit one 2D Gaussian component to each source in the moment-0 map, retrieving best-fit parameters such as the peak intensity and integrated flux density, and morphological information like the coordinates of the \[CII\] emission peak, the full width at half maximum (FWHM) of the major and minor axis of the Gaussian and its position angle (PA). If the \[CII\] morphology shows the presence of different spatially-resolved components in the vicinity of the main ALPINE target (as in case of mergers), we fit an individual 2D Gaussian to each of them in order to retrieve the above morphological and kinematic information for all the observed sub-structures. We then make use of the morphological central position provided by the 2D Gaussian best-fit on each ALPINE target[^5] to produce the PVDs along the major and minor axis with the CASA `IMPV` task, with an averaging width of five pixels and a pseudo-slit length of $3''$ (if not otherwise stated). Conversely to the analysis made by (cite: LeFevre20) in which the major axis was aligned with the morphological PA, we decide to produce the two PVDs with the major axis oriented along the direction of major velocity gradient in the moment-1 map, and with the minor axis perpendicular to the major one. In this way, we increase the chances of identifying possible mergers or rotating galaxies in the ALPINE sample[^6].

Lastly, we extract the spatially-integrated 1D \[CII\] spectrum of each target within the $3\sigma$ contours at the position of the source from the moment-0 map using the CASA task `SPECFLUX`.

## Mergers characterization

Figure [1](#fig:merger_example) shows two examples of the data analyzed for each \[CII\]-detected source. Taking as a reference the left set of panels, we display at the top the \[CII\] morphology superimposed on the HST/ACS F814W (left) and UltraVISTA (UVista) $K_s$ (right) cutouts centered on the UV rest-frame coordinates of the ALPINE target. We also show the $>3\sigma$ emission contours from the optical images. In the second row, the moment-1 and moment-2 maps are reported color-coded for the velocity and velocity dispersion, respectively. In the velocity field map the major and minor axis used to produce the underlying PVDs (color-coded for the flux intensity in Jy/beam) are shown. The axis are centered on the coordinates retrieved from the 2D Gaussian fit on the intensity map and are represented with the direction along which the PVDs are computed. The PA of the major axis is measured from north through east. Both the moment-1 and moment-2 maps are smoothed by using a bilinear interpolation. Finally, the lower panel reports the \[CII\] spectrum (in black) extracted from the continuum-subtracted data cube and modeled with a single and a multiple-component Gaussian function (in this latter case, we show also the possible single components shaping the global spectral profile).

The described panels report the morpho-kinematic analysis of one of the sources classified as merger both by (cite: LeFevre20) and by the analysis undertaken in this work[^7], that is $\mathrm{DEIMOS\_COSMOS\_773957}$ ($\mathrm{DC\_773957}$) at $z_{\mathrm{[CII]}}=5.68$. There are many lines of evidence for considering this galaxy in a merging phase. First, the \[CII\] emission is elongated toward the East at $>3\sigma$, resulting in a clearly disturbed morphology. Furthermore, two peaks of emission at $3\sigma$ are resolved in the UVista $K_s$ band, which could indicate a close pair of objects or the presence of a dust screen. The velocity field is also quite disturbed, with the PVD along the major axis presenting two $3\sigma$ components (solid contours) separated in velocity by $\sim140~\mathrm{km~s^{-1}}$ and with a slight spatial offset. These two components are also visible in the \[CII\] spectrum with green and blue lines. A third minor component at $\sim-200~\mathrm{km~s^{-1}}$ could be instead due to a faint satellite nearby the ALPINE target and it is fairly visible in the PVDs within the $2\sigma$ contours. It is worth noting that, even though with a single Gaussian function we find an integrated flux of the line that is comparable with that obtained from the multicomponent fit, the above-mentioned three components are needed in order to reproduce the observed \[CII\] spectrum.

Moreover, to obtain a more robust sample of mergers we compute, for each of the analyzed merger candidate, the rms of the observed spectra and use it to compute the signal-to-noise ratio (S/N) of the possible merging components. In particular, we obtain the integrated \[CII\] fluxes of the two principal Gaussian components of each spectrum and divide them by the product between the rms and the corresponding FWHM. We thus consider as mergers only those systems for which the minor (in terms of the \[CII\] integrated flux) component has S/N$\geq3$. The S/N for the major and minor components of each system are reported in Table [\[tab:tab_mergers\]](#tab:tab_mergers).

Another example of merging galaxies is provided on the right of Figure [1](#fig:merger_example) by the morpho-kinematic analysis of $\mathrm{vuds\_cosmos\_5100822662}$ ($\mathrm{vc\_5100822662}$) at $z_{\mathrm{[CII]}}=4.52$. This source was classified as a merger both by (cite: LeFevre20) and (cite: Jones21). Indeed, two close and spatially resolved components are clearly visible in the moment-0 and optical maps. From the PVD along the major axis[^8], the two merging systems are at the same velocity but spatially separated by $\sim1.5''$ (i.e., $\sim10$ kpc at $z\sim4.5$). In such a case, it is not possible to compute the contribution supplied by each individual source to the global shape of the line directly from the \[CII\] spectrum. However, we can provide an estimate of the integrated flux from the spectrum of each single component by modeling the total \[CII\] emission in the moment-0 map with two 2D Gaussian functions. In this way, we can extract the spectrum of the resolved component from the continuum-subtracted data cube at the position and with the shape provided by the best-fit parameters from the model (i.e., centroid, major and minor FWHM). For this specific ALPINE target, the spectra of the two merging components are shown in the bottom row of the figure as the blue and green histograms. As can be seen, their sum is quite consistent with the shape of the original \[CII\] spectrum.

A complete description of each individual merging system found from this work in the ALPINE survey is reported in Appendix [7](#app:mergers).

## Comparison with previous classifications

With the methodology introduced in the previous section, we proceed for a new morpho-kinematic classification of the ALPINE targets. As the main aim of this work is to find the contribution of mergers to the galaxy mass assembly at $z\sim5$ from the ALPINE survey, we particularly focus on this class of sources, in order to obtain the final sample of mergers needed to estimate the major merger fraction in the early Universe.

As done by (cite: LeFevre20), we visually inspect the ancillary data, the intensity maps, the velocity and velocity dispersion fields presented in Section [3.1](#sec:mergers_charact) to search for the presence of multiple components or disturbed morphology near the position of the targets. The channel maps, the spectra and the PVDs are checked together searching for consistent emission features. By taking into account the results of the initial qualitative classification by (cite: LeFevre20) and of the more recent quantitative analysis of a subsample of the ALPINE targets by (cite: Jones21), we proceed with a more in-depth characterization of the \[CII\]-detected galaxies aimed at obtaining a robust merger fraction at $z\sim5$. Adopting the same criteria described in Section [2.1](#sec:initial_class) to differentiate the targets and considering the S/N of the minor merger component as described in Section [3.1](#sec:mergers_charact), we find a slightly lower fraction ($\sim31\%$, 23 out of 75 \[CII\]-detected sources) of mergers[^9] if compared to the $40\%$ found by (cite: LeFevre20), with 12, 20 and $7\%$ of the sample made by rotating, extended and compact dispersion dominated sources, respectively. To be more conservative in the classification of the galaxies (especially for obtaining a more robust merger statistics), we define the remaining $30\%$ of the sample as ‘uncertain’, a new category that includes the weak galaxies (as described in (cite: LeFevre20)) and also objects that, by visual inspection, present features that are intermediate to those of various classes. This category is similar to the ‘uncertain’ (UNC) class introduced in (cite: Jones21) that, based on the results of the $\mathrm{^{3D}Barolo}$ fits, contains sources they are unable to classify because of the low S/N and/or spectral resolution, or contrasting evidence in their classification criteria. Although the uncertain category is populated by a significantly larger fraction of sources with respect to the weak class ($\sim16\%$) in (cite: LeFevre20), we recover the same qualitative morpho-kinematic distribution of the previous analysis, confirming the high fraction of rotators and mergers at these early epochs.

+:-----------------+:------:+:------:+:---------------:+:-------:+:----------------------:+:-------:+:---------------:+:--------------:+:------:+:---------------:+:--------------:+:------:+
|                  |        |        |                 |         |                        |         | Minor                                     | Major                                     |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| Source           | $z_1$  | $z_2$  | $\Delta v$      | $r_p$   | $\mu_{\mathrm{[CII]}}$ | $\mu_K$ | FWHM            | $r_\mathrm{e}$ | S/N    | FWHM            | $r_\mathrm{e}$ | S/N    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
|                  |        |        | \[km s$^{-1}$\] | \[kpc\] |                        |         | \[km s$^{-1}$\] | \[kpc\]        |        | \[km s$^{-1}$\] | \[kpc\]        |        |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| \(1\)            | \(2\)  | \(3\)  | \(4\)           | \(5\)   | \(6\)                  | \(7\)   | \(8\)           | \(9\)          | \(10\) | \(11\)          | \(12\)         | \(13\) |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| CG$\_$38         | 5.5731 | 5.5698 | 152.3           | 2.7     | 1.8                    | \-      | 96.9            | 1.4            | 3.8    | 165.9           | 2.0            | 3.9    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$308643     | 4.5238 | 4.5221 | 92.3            | 3.0     | 1.2                    | \-      | 85.4            | 1.0            | 4.5    | 85.6            | 1.4            | 5.3    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$372292     | 5.1345 | 5.1374 | 144.0           | 1.8     | 2.7                    | 2.9     | 82.8            | 2.2            | 4.1    | 157.9           | 3.7            | 5.7    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$378903     | 5.4311 | 5.4293 | 94.5            | 0.9     | 1.9                    | \-      | 70.0            | 4.4$^{(*)}$    | 3.6    | 111.2           | 1.3            | 4.2    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$417567     | 5.6676 | 5.6700 | 106.7           | 5.3     | 2.1                    | \-      | 84.8            | 1.0            | 3.1    | 163.9           | 4.0            | 3.4    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$422677     | 4.4361 | 4.4378 | 92.8            | 0.0     | 1.4                    | \-      | 95.7            | 1.0            | 4.7    | 93.1            | 0.5            | 6.7    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$434239     | 4.4914 | 4.4876 | 206.1           | 5.5     | 6.9                    | \-      | 103.5           | 3.9            | 4.5    | 441.8           | 3.4            | 7.2    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$493583     | 4.5122 | 4.5141 | 103.4           | 1.0     | 4.7                    | \-      | 64.8            | 3.3            | 3.6    | 139.5           | 1.0            | 8.0    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$519281     | 5.5731 | 5.5765 | 158.0           | 0.9     | 4.5                    | \-      | 95.7            | 0.9            | 3.1    | 163.8           | 2.3            | 8.3    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$536534     | 5.6834 | 5.6886 | 234.6           | 4.4     | 2.7                    | \-      | 113.9           | 1.9            | 3.6    | 228.5           | 2.6            | 4.9    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$665509     | 4.5244 | 4.5261 | 95.9            | 1.0     | 2.0                    | \-      | 70.5            | 4.5$^{(*)}$    | 3.0    | 107.0           | 2.4            | 4.0    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$680104     | 4.5288 | 4.5308 | 106.4           | 0.0     | 1.0                    | \-      | 89.5            | 0.5            | 3.7    | 111.6           | 8.7$^{(*)}$    | 4.7    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$773957     | 5.6802 | 5.6770 | 141.2           | 3.0     | 1.6                    | 5.6     | 118.0           | 1.3            | 5.9    | 179.5           | 1.7            | 6.2    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$814483     | 4.5823 | 4.5796 | 145.5           | 7.9     | 2.4                    | \-      | 128.1           | 1.1            | 3.3    | 192.7           | 2.8            | 4.2    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$818760     | 4.5626 | 4.5609 | 92.3            | 9.9     | 1.3                    | 2.6     | 127.1           | 2.4            | 10.4   | 271.0           | 2.9            | 18.3   |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$834764     | 4.5076 | 4.5055 | 119.0           | 1.0     | 1.7                    | \-      | 96.2            | 1.4$^{(*)}$    | 5.1    | 143.8           | 3.1            | 5.8    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$842313     | 4.5547 | 4.5406 | 751.5           | 11.6    | 32.9                   | 1.5     | 229.9           | 4.3$^{(*)}$    | 5.1    | 1089.7          | 1.7            | 5.9    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$859732     | 4.5353 | 4.5315 | 205.2           | 4.9     | 3.9                    | \-      | 55.4            | 1.7$^{(*)}$    | 3.0    | 176.4           | 3.3$^{(*)}$    | 3.7    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| DC$\_$873321     | 5.1545 | 5.1544 | 4.5             | 6.5     | 1.2                    | 3.1     | 171.2           | 1.3            | 4.9    | 219.3           | 2.8            | 7.6    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| vc$\_$5100541407 | 4.5628 | 4.5628 | 1.9             | 13.8    | 1.6                    | 1.4     | 203.8           | 4.4$^{(*)}$    | 3.5    | 166.5           | 1.2            | 6.9    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| vc$\_$5100822662 | 4.5210 | 4.5205 | 22.3            | 10.9    | 1.6                    | 1.7     | 189.6           | 4.0            | 5.1    | 192.7           | 2.0            | 8.0    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| vc$\_$5101209780 | 4.5724 | 4.5684 | 217.3           | 10.8    | 4.1                    | 2.5     | 126.1           | 2.3            | 4.4    | 303.9           | 6.6            | 7.4    |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+
| vc$\_$5180966608 | 4.5294 | 4.5293 | 8.9             | 7.2     | 3.0                    | 3.7     | 243.6           | 1.8            | 3.4    | 231.6           | 4.3            | 10.9   |
+------------------+--------+--------+-----------------+---------+------------------------+---------+-----------------+----------------+--------+-----------------+----------------+--------+

**Notes.** The right side of the table shows the measurements of FWHM (in km s$^{-1}$), \[CII\] emission size (in kpc), and S/N for both the minor and major components, intended as such in terms of their integrated \[CII\] fluxes. The asterisk near the size of some of the sources indicates a bad $r_e$ estimate from the best-fit parameters of the 2D Gaussian fit on the moment-0 maps of the individual components.

![](plots/phase_space_final.png)

## Physical parameters estimate

For each source classified as merger we measure several physical quantities that help us to estimate the merger fraction at $z\sim5$. From the spectra, we compute the \[CII\] flux ratio between the major and minor components of the merger[^10], that is $\mu_\mathrm{[CII]} = F_\mathrm{1,[CII]}/F_\mathrm{2,[CII]}$, finding a good agreement with the corresponding ratio computed from the PVDs. To obtain the integrated fluxes of the individual galaxies, we use a Gaussian decomposition of the global \[CII\] spectrum, as described in Section [3.1](#sec:mergers_charact). When allowed by the resolution, we also take the UVista $K_s$-band flux ratio of the two merging sources, namely $\mu_{K}\equiv F_{1,K}/F_{2,K}$, where $F_{1,K}$ and $F_{2,K}$ are the integrated fluxes obtained by fitting a 2D Gaussian function to the major and minor components of the merger in the considered band, respectively. Then, from the spectral features, we also obtain the separation in velocity ($\Delta v$) between the intensity peaks of the merger components, and the FWHM both for the individual objects and single (overall spectrum) source.

We measure the projected distance ($r_p$) between the centers of the merger components as $r_p = \theta \times d_A(z_m)$, where $\theta$ is the angular separation in the sky (in arcsec) between the two galaxies and $d_A(z_m)$ is the angular diameter distance (in kpc arcsec$^{-1}$) computed at the mean redshift $z_m$ of the two sources. In case the two components are not spatially resolved in \[CII\], we consider the distance between the two best-fit centroids returned by the 2D Gaussian fit on their moment-0 maps. Similarly to what has been done in (cite: Ginolfi20), the latter maps are obtained by collapsing the channels including the emission of the individual components. Such a case is shown, for instance, in Figure [1](#fig:merger_example) for the target $\mathrm{DC\_773957}$. The shaded blue and green areas under the curves in the spectrum mark the collapsed channels used for building the \[CII\] intensity maps of the two components. As it can be seen, the velocity channels assigned to each component are not overlapping with each other. If instead the two objects are spatially resolved but at the same velocity (as for $\mathrm{vc\_5100822662}$), we are not able to create the \[CII\] moment-0 maps of the individual components (i.e., the two sources emit at the same frequency and we cannot disentangle their contribution in \[CII\]) and we measure the distance directly from the \[CII\] intensity map or from the PVDs.

Finally, we compute the size of the single components by fitting a simple 2D Gaussian model to the \[CII\] intensity maps obtained as described above. Following (cite: Fujimoto20), we refer to the merging component size as the circularized effective radius $r_{\mathrm{e}}$ defined as $r_{\mathrm{e}} \equiv \sqrt{a~b}$, where $a$ and $b$ are the best-fit semi-major and semi-minor axis, respectively. When the source is resolved, we use the best-fit beam-deconvolved $a$ and $b$ parameters, otherwise we take the beam-convolved sizes provided by the fit and correct them for the ALMA beam (the average beam minor axis of ALPINE is $\sim0.8''$). It is worth noting that (cite: Fujimoto20) measured the \[CII\] effective radii by fitting the line visibilities with the CASA task `UVMULTIFIT` and assuming an exponential-disk profile. However, by applying our more simplistic size measurements to the ALPINE galaxies analyzed by (cite: Fujimoto20) and considering the mergers as single components, we found a good agreement with their results. A larger scatter is found only for some of the objects classified as mergers whose size measurements are flagged as unreliable by (cite: Fujimoto20), likely because of the complicated \[CII\] morphology.

From now on, we refer to $r_{\mathrm{e}}$ when talking about the size of a source. All the information presented in this section is reported in Table [\[tab:tab_mergers\]](#tab:tab_mergers).

## Description of the merger sample

We show in Figure [2](#fig:phase_space) (upper panel) the difference in velocity between the merger components as a function of their projected distance $r_p$ for all the possible merging systems in ALPINE. In the upper-left corner, we report the uncertainties assumed for these data. The error on $\Delta v$ is obtained by the sum in quadrature of the average uncertainty on each spectral element (i.e., 25 km s$^{-1}$). To estimate the typical error on the projected distance, we consider two random centroids corresponding to the initial positions of the minor and major components of the merger. Then, we obtain the distribution of the errors on the centroids as provided by the 2D Gaussian best-fits on the intensity maps of the merging components, and extract from that $\mathrm{N}=1000$ values used to perturb the initial positions. At each iteration, we re-compute the projected distance between the perturbed positions of the two components. We thus estimate the average uncertainty on $r_p$ as the standard deviation of the distribution of the N projected separations (corresponding to $\sim0.3~$kpc).

To derive a robust major merger fraction ($f_\mathrm{MM}$), we decide to consider as mergers only those systems in which the components are separated by no more than $\mathrm{\Delta v\leq500~km~s^{-1}}$, assuming that this is the limit for a system to be gravitationally bound (e.g., (cite: Patton2000; Lin2008; Ventou17)). As shown, all the mergers in our sample satisfy this constraint except one source. As analyzed in detail in Appendix [7](#app:mergers), this system is composed by the ALPINE target $\mathrm{DC\_842313}$ and a peculiar neighbor source with a large FWHM and \[CII\] flux, and could even be a merger of three galaxies with a $\Delta v$ between the target and the further third component smaller than 500 km s$^{-1}$. We thus account for this object in the computation of the merger fraction.

Also, we consider as reliable mergers only those systems with a projected distance larger than the typical \[CII\] sizes of individual galaxies at these redshifts. Indeed, closer components could just represent clumps of star formation within the same galaxy, faking the presence of a merger by affecting the morphology and kinematics of the \[CII\] line. From the size measurements of the ALPINE galaxies we find an average \[CII\] size of $\sim2.1$ kpc, that is in good agreement with the median value found by (cite: Fujimoto20) and with the typical distance between galaxies and satellites or mergers (\>2 kpc) at $z>4$ (e.g., (cite: Carniani18; Whitney19; Zanella21)). Therefore, we use this value as a threshold to classify the secure merging systems.

The two selection criteria on the distance and velocity separations define the gray region in Figure [2](#fig:phase_space) which thus includes the sources that are classified as robust mergers. However, we cannot exclude a priori the systems with $r_p<2.1$ kpc as they could be structures in an advanced stage of merging that we are not able to resolve with ALMA because of their close proximity and observational limitations (i.e., large synthesized beam, limited sensitivity). It is worth noting that, in some cases, spatially close clumps are observed with HST within the typical ALPINE beam size. However, the lack of redshift information for these sources prevent us from considering them as associate galaxies experiencing a merging. This could have an impact on our results, possibly reducing the estimated major merger fraction (and, consequently, the merger rate) at $z\sim5$. For these reasons, we also show in Figure [2](#fig:phase_space) (bottom panels) the individual sizes of the minor and major components of each of the possible mergers as a function of their FWHM. The colors and marker symbols are the same as in the top panel, while the hatched markers highlight those objects with a bad $r_\mathrm{e}$ estimate from the fit, after a visual inspection of the residuals. We also show for comparison the data of the individual ALPINE galaxies (excluding the mergers) as light squares. As it can be seen, the sizes of the individual components lie, within the uncertainties, among those of the ALPINE targets. This suggests that all the individual components we are analyzing could be merging galaxies and that, with the current data, we cannot exclude them from the computation of the merger fraction at $z>4$.

Finally, we provide an estimate of the stellar mass range covered by our merger components. We only have information on the stellar mass of the merging system as a whole through SED-fitting measurements (cite: Faisst20) because the majority of the merger candidates are not resolved in most of the optical and near-IR bands. We make the assumption that $M_{*,1}+M_{*,2}=M_{*}$ and define the mass ratio as $\mu=M_{*,1}/M_{*,2}$, where $M_{*,1}$ and $M_{*,2}$ are the stellar masses of the primary and secondary galaxy (i.e., $M_{*,1}>M_{*,2}$) and $M_{*}$ is the total mass of the system from the SED-fitting. Then, we set $\mu=4$ as a threshold to separate major ($1\leq \mu \leq4$) from minor ($\mu>4$) mergers (e.g., (cite: Lotz11; Mantha18; Duncan19)) and use this value to solve the above equations for $M_{*,1}$ and $M_{*,2}$. With the assumptions above, we obtain a stellar mass distribution of the major components ranging between $\mathrm{log}(M_{*,1}/M_{\odot})\sim9.0$ and 10.7, with a mean value $\mathrm{log}(M_{*,1}/M_{\odot})\sim10$ (reducing by $\sim0.2$ dex if assuming $\mu=1$). We want to stress that this is just an exercise that is intended to provide an estimate of the stellar mass range of the merger components we are analyzing and that helps us in the comparison of our estimates with those of previous works. Indeed, we are not considering that some of the merger components are resolved in the $K_s$ band and have their own mass ratio (see Section [4.1](#sec:frac_derivation)). Therefore, following the above considerations, we can conclude that the close pairs of our sample are characterized by $r_p<20$ kpc, $\Delta v<500$ km s$^{-1}$, and average stellar masses $\mathrm{log}(M_{*}/M_{\odot})\sim10$.

## Accounting for completeness

When deriving the merger fraction, we have to consider the possibility of missing a certain number of mergers because of the faintness of the minor component. Indeed, mergers with a principal component near the threshold of the observable \[CII\] flux may imply the presence of a secondary component that could be lost by instrumental limitations. To account for this, we must correct for the incompleteness of our sample.

Previous works typically assumed corrections based on the limiting flux or stellar mass of the corresponding survey (e.g., (cite: Patton2000; Lopez11; Mundy17; Duncan19)). ALPINE is not a flux-limited survey as each individual ALMA pointing reaches different depths (e.g., (cite: Bethermin20)). For this reason, we adopt the classical completeness corrections found in the literature but considering for each object its limiting flux. In particular, we apply a weight to each minor component of our sample defined as $$\begin{equation}
    w_\mathrm{comp}(L,z) = \frac{\int_{L_2}^{L_1} \Phi(L,z) \,dL}{\int_{L_\mathrm{lim}}^{L_1} \Phi(L,z) \,dL},
    \label{eq:weight}
\end{equation}$$ where $\Phi(L, z)$ is the \[CII\] luminosity function derived from the UV-selected central ALPINE targets (cite: Yan20), $L_\mathrm{lim}$ is the luminosity corresponding to the limiting flux of each ALPINE pointing, $L_1$ is associated to the flux of the primary component $F_\mathrm{1,[CII]}$, and $L_2$ corresponds to $F_\mathrm{2,[CII]} = F_\mathrm{1,[CII]}/4$. We compute the \[CII\] luminosities by following (cite: Solomon92) with the relation $$\begin{equation}
L_\mathrm{[CII]} = 1.04 \times 10^{-3}~F_\mathrm{[CII]}~D^2_\mathrm{L}(z)~\nu_{obs}(z)~[L_{\odot}],
\label{eq:L_CII}
\end{equation}$$ where $F_\mathrm{[CII]}$ is the integrated flux (in Jy km s$^{-1}$), $D_\mathrm{L}(z)$ is the luminosity distance (in Mpc) at the redshift of the galaxy, and $\nu_\mathrm{obs}(z)$ is the observed frequency of the \[CII\] line (in GHz). We also assume that $w_\mathrm{comp}=1$ when $L_2 > L_\mathrm{lim}$. Such a correction corresponds to the ratio between the number density of galaxies with \[CII\] flux higher than $F_\mathrm{2,[CII]}$, and the number density of galaxies with a flux higher than the flux limit of each ALMA pointing.

# Results

## The fraction of major mergers in ALPINE

![](plots/CII_vs_K_ratio_distributions_new.png)

The aim of this work is to derive the fraction of galaxies undergoing a major merger at $z\sim5$ and to estimate their contribution to the galaxy mass assembly through cosmic time. Although the cosmic evolution of minor mergers is still poorly constrained at these redshifts, several studies suggest that they are more frequent in the nearby Universe showing a decreasing fraction for $z\gtrsim3$ (cite: Lopez11; Lotz11; Ventou19). We thus have to take into account a possible contamination from them in our sample.

First, as we do not have the stellar mass information for the majority of our merger components, we define as major mergers those candidates for which the $K_s$-band flux ratio is smaller than 4, that is $1<\mu_{K}<4$. The $K_s$ band is indeed a good tracer of the stellar mass of galaxies up to $z\sim4$ (e.g., (cite: Laigle16)). At higher redshifts, the rest-frame $K_s$ band samples the emission below the Balmer break ($K_s$-band corresponds to rest-frame $\sim3600~\AA$ at $z\sim5$, taking as a reference the mean wavelength of the filter) which is no more directly linked to the stellar mass of the galaxy. In these cases, mid-IR bands could be better tracers of the galaxy stellar masses than the $K_s$ filter, but their worst resolution do not allow us to spatially resolve the close galaxies for which we have the $K_s$ fluxes. For comparison, (cite: Lopez13) used the $i$-band ratios to identify major mergers. At the redshifts explored in their work ($0.9<z<1.8$), the observed $i$ band corresponds to $\sim3000-3500~\AA$ rest-frame (which is quite similar to the wavelength range covered by the $K_s$ band at the highest redshift of our sample). They compared these ratios with those obtained from the $K_s$ band (sampling the emission between 8000 and 10000 $\AA$ rest-frame, thus tracing better the stellar mass content of the galaxies), finding no significant changes in their major merger classification, and then supporting the $i$-band results. Therefore, following these arguments, we consider $\mu_{K}$ reasonably comparable to the stellar mass ratio of our sources, treating cautiously these estimates for those galaxies at the highest redshifts of our sample.

The $K_s$-band ratio is available for 9 out of 23 mergers, while for the remaining sources we only have the \[CII\] flux ratio, from which we cannot draw conclusions about the nature of the merger. These two ratios are shown in Figure [3](#fig:CII_K_ratio) where it is evident that the majority of the sources have both $\mu_{K}$ and $\mu_{\mathrm{[CII]}}$ smaller than 4. Furthermore, in the inset we compare the \[CII\] and $K_s$-band flux ratios for the objects having these two measures in common[^11]. There is a good agreement between the two ratios for some of the objects in the figure, but others show a large scatter from the 1:1 relation, suggesting that complex physical processes could take place in these systems. However, we find that 7 out of 8 sources (i.e., $\sim88\%$ of this subsample) have $\mu_K < 4$ while only one system shows a larger $K_s$-band flux ratio. Although a larger statistical sample would be needed, we can interpret this as an indication of the minor merger contamination of our sample. Indeed, if we consider that only the sources outside the green region contribute to the minor merger contamination (thus lying at $\mu_{K}>4$), we can assume that the 12% of all the objects having only the $\mu_{\mathrm{[CII]}}$ information is affected by minor mergers (or, equivalently, that only the 88% of that sample contains major mergers). We note that, when excluding from this statistics the sources at $z\sim5.5$ (whose $K_s$-band ratio is less reliable as a tracer of their stellar mass), all the objects in the inset of Figure [3](#fig:CII_K_ratio) have $\mu_K < 4$, raising the fraction of major mergers in this subsample to 100%. This is taken into account later, when estimating the uncertainty on the merger fraction.

We define the major merger fractions in the two ALPINE redshift bins (at mean redshift $z\sim4.5$ and 5.5, respectively) as

$$\begin{equation}
    f_{\text{MM}} = 0.88~\frac{\sum_{j=1}^{\mathrm{N_p}} w_\mathrm{comp}^{j}}{\mathrm{N_g}},
    \label{eq:fmm}
\end{equation}$$ where $\mathrm{N_p}$ represents the number of all the mergers in our sample, $\mathrm{N_g}$ is the number of ALPINE galaxies in the considered redshift bin, and $w_\mathrm{comp}^{j}$ is the weight associated to each merger to correct for incompleteness (see Section [3.5](#sec:completeness)). The factor 0.88 accounts for the statistical uncertainty on the real merger nature (the fact that the 12% of the $\mu_{\mathrm{[CII]}}$-only subsample could be affected by the presence of minor mergers). Note also that, as detailed in Section [3.4](#sec:size_mergers), we are not excluding any source with $r_p<2$ kpc because the individual sizes of these merger components are comparable with those of the ALPINE galaxies.

|                       |       $z\sim4.5$       |       $z\sim5.5$       |
|:---------------------:|:----------------------:|:----------------------:|
|    $\mathrm{N_g}$     |           46           |           29           |
|    $\mathrm{N_p}$     |           15           |           8            |
| $\mathrm{N_{p,corr}}$ |           23           |           11           |
|    $f_{\text{MM}}$    | $0.44^{+0.11}_{-0.16}$ | $0.34^{+0.10}_{-0.13}$ |

: Number of sources at $z\sim4.5$ and $z\sim5.5$ from the ALPINE survey used for the computation of the major merger fraction.

To attribute an uncertainty to $f_{\text{MM}}$ we consider two extreme cases. At first, as an upper limit to the major merger fraction, we count all the mergers in each redshift bin and divide them by $\mathrm{N_g}$, independently of their components projected distance and flux ratio. This uncertainty includes also the case in which our sample is not contaminated by minor mergers (i.e., all the analyzed mergers are major). As a lower limit instead, we only take the mergers whose components have $r_p>2$ kpc, assuming that all the individual components with a smaller projected separation are not major mergers (see discussion above). Then, given the small statistics on both the total number of ALPINE galaxies and the subsample of mergers, we compute the corresponding Poissonian errors and add them in quadrature to the above-mentioned uncertainties.

With these assumptions and from Equation [\[eq:fmm\]](#eq:fmm) we obtain $f_{\text{MM}}^{z_4} = 0.44^{+0.11}_{-0.16}$ and $f_{\text{MM}}^{z_5} = 0.34^{+0.10}_{-0.13}$, at $z\sim4.5$ and $z\sim5.5$, respectively. These results are shown in Figure [4](#fig:merger_frac) and reported in Table [1](#tab:fmm_info) along with the numbers used for their computation at both redshifts. We note that, by using Equation [\[eq:fmm\]](#eq:fmm), we recover a merger fraction $\sim30\%$ higher than obtained if not accounting for completeness corrections. It is also interesting that, assuming that 12% of the mergers are minor would imply a minor merger fraction of at least $\sim5\%$, in agreement with the estimates by (cite: Ventou19) at $z>3$ (i.e., $0.08^{+0.07}_{-0.05}$). It should be noted that this fraction could be even higher. Indeed, the relatively low spatial resolution of the ALPINE survey does not allow us to constrain the minor merger fraction at $z\sim5$ (cite: LeFevre20), as we are not able to detect faint satellites that are instead expected to be in the neighborhood of $z>4$ galaxies by simulations (e.g., (cite: Pallottini17; Kohandel19)).

Finally, it is worth mentioning that $\sim10\%$ of the ALPINE targets are part of a massive proto-cluster of galaxies (PCI J1001+0220) at $z\sim 4.57$ located in the COSMOS field (cite: Lemaux18). In principle, high-density environments like those in high-$z$ proto-clusters, or groups and low-mass clusters at lower redshift, could enhance the merging activity, resulting in a merger rate that could be several times larger than what expected in lower-density regimes (e.g., (cite: Lin10; Lotz13; Tomczak17; Pelliccia19)). To account for this possible caveat, we compare the ALPINE members of the proto-cluster with the mergers in Table [\[tab:tab_mergers\]](#tab:tab_mergers), finding that only two of them are part of the observed over-density. However, by removing these two sources from our analysis, we do not find any significant change in the merger fraction at $z\sim4.5$ and, consequently, in the estimate of the merger rate.

![](plots/merger_frac_conselice.png)

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Literature | Redshift range | Major/Minor separation | $\Delta v$ | $r_p$ | Primary Galaxy Mass |
|  |  |  | \[km s$^{-1}$\] | \[kpc\] |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) |
| (cite: deRavel09) | $0.5<z<0.9$ | $F_1/F_2\leq4.0$ | $\leq500$ | $<20$ | $\mathrm{log}(M_{*}/M_{\odot})\geq9.5$ |
| (cite: Xu12) | $0\leq z \leq0.6$ | $M_1/M_2\leq2.5$ | $\leq500^{(*)}$ | $5-20$ | $9.8<\mathrm{log}(M_{*}/M_{\odot})\leq10.2$ |
| (cite: Lopez13) | $0.9<z<1.8$ | $F_1/F_2\leq4.0$ | $\leq500$ | $<20$ | $9<\mathrm{log}(M_{*}/M_{\odot})<11$ |
| (cite: Tasca14) | $1.8\leq z \leq4.0$ | $M_1/M_2\leq4.0$ | $\leq500$ | $<25$ | $9<\mathrm{log}(M_{*}/M_{\odot})<11$ |
| (cite: Ventou17) | $0.2\leq z \leq4.0$ | $M_1/M_2\leq6.0$ | $\leq500$ | $<25$ | $\mathrm{log}(M_{*}/M_{\odot})\geq9.5$ |
| (cite: Duncan19) | $0.5\leq z <3.5$ | $M_1/M_2\leq4.0$ | $\leq500^{(*)}$ | $5-30$ | $9.7<\mathrm{log}(M_{*}/M_{\odot})<10.3$ |
| This work | $4.4\leq z <5.9$ | $M_1/M_2\leq4.0$ | $\leq500$ | $<20$ | $9\lesssim \mathrm{log}(M_{*}/M_{\odot})\lesssim11$ |

**Notes.** The asterisks in column 4 indicate the works in the literature that made use of photometric redshifts to define the selection criterion on the velocity separation between pairs.

## Cosmic evolution of the major merger fraction

During the last years, a large number of studies focused on the estimate of the merger fraction at different redshifts and on its evolution through cosmic time (e.g., (cite: LeFevre00; Conselice03; Conselice09; Lopez13; Mundy17; Ventou17; Mantha18; Duncan19)). However, the choice of various selection criteria on the spatial and velocity separation for the pair counts, the different mass ranges probed by each author and the diverse threshold in $\mu$ to distinguish between major and minor mergers make a direct comparison between the many results found in the literature quite problematic. Therefore, we now compare the major merger fraction found from this work at $4<z<6$ with those computed from samples of galaxies with similar stellar masses and merger selection criteria.

At $z<1$, (cite: Xu12) evaluated the major merger fraction from a sample of close pairs drawn from the COSMOS survey (cite: Ilbert09). From that work we select only the results in the stellar mass bin $9.8<\mathrm{log}(M_{*}/M_{\odot})\leq10.2$, to be consistent with the average stellar mass of our sample. At this epoch we also account for the merger fraction computed by (cite: deRavel09) who analyzed a sample of spectroscopically confirmed galaxy pairs from the VIMOS VLT Deep Survey (VVDS; (cite: LeFevre05)) with $\mathrm{log}(M_{*}/M_{\odot})>9.5$. At $1<z<4$, (cite: Lopez13) and (cite: Tasca14) exploited the VUDS, VVDS and the Mass Assembly Survey with SINFONI in VVDS (MASSIVE; (cite: Contini12)) surveys to estimate $f_{\text{MM}}$ from merging systems with spectroscopic measurements and average stellar masses $\mathrm{log}(M_{*}/M_{\odot})\sim10$. (cite: Ventou17) observed the *Hubble* Ultra Deep Field (cite: Beckwith06) and the *Hubble* Deep Field South (cite: Williams00) with the Multi Unit Spectroscopic Explorer (MUSE) to constrain the galaxy major merger fraction up to $z\sim6$. However, we take only their data points with $\mathrm{log}(M_{*}/M_{\odot})\geq9.5$ which extend up to $z\sim3$. Finally, we get the pair fraction computed by (cite: Duncan19) in a mass-selected ($9.7<\mathrm{log}(M_{*}/M_{\odot})<10.3$) sample of galaxies drawn from the CANDELS survey (cite: Grogin11; Koekemoer11) using a probabilistic approach based on their photometric redshifts. All these works assume a projected separation $r_p<30$ kpc between the merger components and a difference in velocity $\mathrm{\Delta v\leq500~km~s^{-1}}$. Most of them adopt $\mu<4$ to identify the major merger population, with $\mu$ computed either as the ratio between the stellar mass of the primary and secondary galaxy in the system or as the difference in magnitude between the two components. The only exceptions are from (cite: Xu12) and (cite: Ventou17) that make use of a mass ratio of 2.5 and 6, respectively (however, as stated by (cite: Ventou17), adopting a mass ratio limit of 4 implies the loss of only a few sources in their sample, not significantly altering the final statistics). Table [\[tab:literature\]](#tab:literature) summarizes the main features of the samples from which the observational data at $z<4$ introduced above are taken.

As shown in Figure [4](#fig:merger_frac), we combine these data with our measurements at $z\sim5$ to provide the cosmic evolution of the major merger fraction. Traditionally, this is parameterized with a power-law fitting formula of the form $$\begin{equation}
    f_{\text{MM}}(z) = f_0~(1+z)^m,
    \label{eq:fmm_powerlaw}
\end{equation}$$ where $f_0$ is the merger fraction at $z=0$ and $m$ is the index that rules the redshift evolution. Our data suggest a slight decline of the merger fraction at $z>4$, with a possible peak at lower redshift, as also previously found by other studies (e.g., (cite: Conselice09; Ventou17; Mantha18; Duncan19)). Therefore, we make use of a combined power-law and exponential function to fit our observational data, such as $$\begin{equation}
    f_{\text{MM}}(z) = \alpha~(1+z)^m~\mathrm{exp}(\beta(1+z)),
    \label{eq:fmm_evol}
\end{equation}$$ where $\beta$ controls the exponential side of the curve and $f_0=\alpha~\mathrm{exp}(\beta)$. By using a non linear least square algorithm, we fit our data both with Equation [\[eq:fmm_powerlaw\]](#eq:fmm_powerlaw) and Equation [\[eq:fmm_evol\]](#eq:fmm_evol). Taking advantage of the Bayesian information criterion (BIC), we find a significant statistical evidence ($\Delta \mathrm{BIC}>10$) in favor of the combined power-law and exponential form for describing the evolution of the merger fraction through cosmic time. These results are in contrast with those by (cite: Duncan19) who, also relying on the BIC, found that there was no strong statistical evidence in favor of one of the two above-described parameterizations. This difference could be attributed to the fact that, for stellar masses $\mathrm{log}(M_{*}/M_{\odot})\sim10$, they measured the major merger fraction up to $z\sim3$, while in this work our new ALPINE data allow us to constrain this quantity up to earlier epochs (i.e., $z\sim5$).

+-----------------------+-----------------+-----------------+------------------+
| $T_{\text{MM}}$       | $\alpha$        | $m$             | $\beta$          |
+:=====================:+:===============:+:===============:+:================:+
| Merger fraction $f_{\text{MM}}$                                              |
+-----------------------+-----------------+-----------------+------------------+
| \-                    | $0.024\pm0.003$ | $4.083\pm0.501$ | $-0.797\pm0.189$ |
+-----------------------+-----------------+-----------------+------------------+
|                       |                 |                 |                  |
+-----------------------+-----------------+-----------------+------------------+
| Merger rate $R_{\text{MM}}$                                                  |
+-----------------------+-----------------+-----------------+------------------+
| (cite: Kitzbichler08) | $0.020\pm0.003$ | $4.282\pm0.488$ | $-1.036\pm0.182$ |
+-----------------------+-----------------+-----------------+------------------+
| (cite: Jiang14)       | $0.015\pm0.002$ | $4.350\pm0.492$ | $-0.740\pm0.184$ |
+-----------------------+-----------------+-----------------+------------------+
| (cite: Snyder17)      | $0.010\pm0.001$ | $6.083\pm0.501$ | $-0.797\pm0.189$ |
+-----------------------+-----------------+-----------------+------------------+

For these reasons, we show in Figure [4](#fig:merger_frac) the best-fitting function to our data obtained through Equation [\[eq:fmm_evol\]](#eq:fmm_evol), and use the results from this parameterization for the rest of the work. In particular, the parameters of this fit are $\alpha = 0.024\pm0.003$, $m=4.083\pm0.501$ and $\beta = -0.797\pm0.189$ which are in good agreement with those found by (cite: Duncan19) when fitting the CANDELS data points for galaxies with stellar mass $9.7<\mathrm{log}(M_{*}/M_{\odot})<10.3$. For comparison, we also show the results obtained by (cite: Conselice09) exploiting morphological analysis and pair counts for a sample of Lyman-break drop-out galaxies at $4<z<6$ with masses $\mathrm{log}(M_{*}/M_{\odot})>9-10$. Their data points are lower than our results but still comparable to them within the uncertainties. Anyway, as they do not differentiate between major and minor mergers, we do not include them in the computation of the cosmic evolution of the merger fraction.

We show in Figure [4](#fig:merger_frac) the best-fit parameterization of the major merger fraction found by (cite: Qu17) for galaxies with $\mathrm{log}(M_{*}/M_{\odot})\geq9.5$ from the Evolution and Assembly of Galaxies and their Environments (EAGLE) hydrodynamical simulation (cite: Schaye15). They adopted a stellar mass ratio $\lesssim4$ to identify major mergers and the same parameterization as in Equation [\[eq:fmm_evol\]](#eq:fmm_evol), obtaining a cosmic evolution of $f_{\text{MM}}$ that is similar to ours up to $z\sim4$ (the higher redshift reached by the simulation). Extending their prediction to earlier epochs, a slightly milder redshift evolution with respect to our results is found. However, the two trends are still in good agreement with each other.

Finally, it is worth noting that we are recovering the cosmic evolution of the merger fraction by comparing galaxies with a constant stellar mass range at all redshifts. We are aware that, in this way, we are not necessarily tracing the same galaxy population through cosmic time, as instead achieved with constant cumulative comoving number density selections (cite: Papovich11; Conselice13; Ownsworth14; Mundy15; Torrey15)[^12]. Nevertheless, as the majority of the observational and theoretical works in the literature make use of the constant stellar mass selection to estimate the fraction and rate of major mergers through cosmic time, such a choice allows us to make a fair comparison to these works and provides a quite easily quantifiable observational benchmark for future studies.

## Galaxy major merger rate

The major merger fraction can be translated into the merger rate $R_{\text{MM}}$ (i.e., the number of mergers per galaxy and Gyr) as $$\begin{equation}
    R_{\text{MM}}(z) = \frac{C_{\text{merg}}~f_{\text{MM}}(z)}{T_{\text{MM}}(z)},
    \label{eq:Rmm_evol}
\end{equation}$$ where $f_{\text{MM}}(z)$ is the pair fraction at redshift $z$ estimated in Section [4.2](#sec:merger_frac), and $C_{\text{merg}}$ is the fraction of close pairs that will eventually merge into a single system in a typical timescale $T_{\text{MM}}(z)$. This last term represents the major source of uncertainty in the merger rate computation and is usually obtained through simulations based on the dynamical friction timescales affecting the merging components (e.g., (cite: Kitzbichler08; Lotz10; Jiang14; Snyder17)).

(cite: Kitzbichler08) applied a semi-analytic model to the Millennium simulation (cite: Springel05) outputs finding an average merging time that depends linearly on the redshift and projected distance of the pair and weakly on the stellar mass of the main galaxy, namely $T_{\text{MM}}\propto r_p~M_{*}^{-0.3}~(1+z/8)$. This relation is valid at $z\leq1$, while at higher redshift it becomes $$\begin{equation}
    T_{\text{MM}}^{-1/2} = T_0^{-1/2}+f_1z+f_2(\mathrm{log}M_{*}-10),
    \label{eq:Tmm_kitz}
\end{equation}$$ where $T_0$ is the merging time at $z=0$, $M_{*}$ is the stellar mass of the primary galaxy, while $f_1$ and $f_2$ are two coefficients of the parameterization. A mass dependence similar to the $z\leq1$ (cite: Kitzbichler08) timescale ($T_{\text{MM}}\sim M_{*}^{-0.2}$) was also found by (cite: Lotz10) for mergers in the stellar mass range $9.7<\mathrm{log}(M_{*}/M_{\odot})<10.7$ but in a smaller sample. More recent works explored a different redshift evolution of the merger timescale. For instance, (cite: Jiang14) took into account the mass loss due to dynamical friction of the virial masses of galaxies experiencing a merger and, by using a high-resolution $N-$body cosmological simulation, found $T_{\text{MM}}\propto H(z)^{-1/3}$, where $H(z)$ is the Hubble parameter at redshift $z$. An even stronger redshift evolution was found by (cite: Snyder17) by comparing mass-selected close pairs with the intrinsic galaxy merger rate from the Illustris simulations (cite: Genel14; Vogelsberger14). They found $T_{\text{MM}}=2.4~(1+z)^{-2}$ but for primary galaxies with stellar mass range $10.5<\mathrm{log}(M_{*}/M_{\odot})\leq11$. It is better to specify that, in the case of (cite: Snyder17), $T_{\text{MM}}$ does not correspond to the merger timescale of Equation [\[eq:Rmm_evol\]](#eq:Rmm_evol), rather it is the merger observability timescale which already includes the effects of the $C_{\text{merg}}$ term. Nevertheless, we refer to that as $T_{\text{MM}}$ for simplicity.

For the rest of this work, we compare the results obtained with the merger timescales provided by (cite: Kitzbichler08), (cite: Jiang14) and (cite: Snyder17), in order to highlight the large differences in the final outcome due to the choice of this parameter. About the probability for a pair to merge over a certain timescale (i.e., $C_{\text{merg}}$), it is usually fixed to 0.6 (e.g., (cite: Lotz11; Mantha18)). However, as in most cases this quantity is already included in the merger timescale prescriptions provided in different works (e.g., (cite: Duncan19)), we set $C_{\text{merg}}=1$ throughout.

With these assumptions, we present in Figure [5](#fig:merger_rate) (left panel) the cosmic evolution of the merger rate, as obtained by combining our new $z>4$ ALPINE data with those at lower redshifts from the literature. For each data point we compute $R_{\text{MM}}$ from Equation [\[eq:Rmm_evol\]](#eq:Rmm_evol), adopting the three different merger timescales defined above[^13] and fit the resulting data with the same functional form used for the merger fraction. We show the best-fitting functions to these data (and their $1\sigma$ uncertainties) in Figure [5](#fig:merger_rate) and report the corresponding parameters in Table [\[tab:fit_params\]](#tab:fit_params).

As evident, all the three functions show a steep increase of the merger rate from the local Universe to $z\sim1$. However, at higher redshifts they lead to large differences about the incidence of these sources at early epochs. When considering the (cite: Kitzbichler08) timescale, we find a redshift evolution which is similar to what obtained in Section [4.2](#sec:merger_frac) for the merger fraction, with a peak at $z\sim2.5$ and a quite fast decrease at higher redshifts. Both the merger rate evolutions obtained with $T_{\text{MM}}(z)$ by (cite: Jiang14) and (cite: Snyder17) show instead a milder redshift attenuation at $z\gtrsim4$. In particular, the increasingly smaller merger timescale found by (cite: Snyder17) involves a very large merger rate in the early Universe compared to the other functions, possibly implying a significant role of major mergers in the galaxy mass assembly at $z\sim5$.

We then compare our results with the cosmic evolution of several expected merger rates from simulations. At $z<3$, (cite: Hopkins10) found that $R_{\text{MM}}\propto (1+z)^{1.8}$ for galaxies with $\mathrm{log}(M_{*}/M_{\odot})>9$ and $\mu<3$. This redshift evolution is comparable to our best-fitting function with $T_{\text{MM}}(z)\propto H(z)^{-1/3}$ at $1\lesssim z \lesssim 3$. However, if we extrapolate their results up to $z\sim6$, we find that their predicted major merger rates could be larger (by $\sim0.5$ dex) with respect to our observations. A stronger and increasing redshift dependence was found by (cite: Rodriguez15) for the merger rate from the Illustris simulations. By exploiting their parametric fitting formula with a stellar mass[^14] of $\mathrm{log}(M_{*}/M_{\odot})=10$ and an average mass ratio $\mu=2$ over cosmic time (see Section [4.5](#sec:specific_mar)), the simulation tends to over-predict our observed merger rates at $z\sim0$, while it underestimates them at intermediate redshifts. We also show the merger rate predictions found by (cite: Oleary21) using the results from the Empirical ModEl for the foRmation of GalaxiEs (EMERGE; (cite: Moster18)). In particular, they modeled the merger fraction evolution as in Equation [\[eq:fmm_evol\]](#eq:fmm_evol) and then convolved it with a typical merger timescale to obtain $R_{\text{MM}}$ as a function of redshift. We consider their best-fit parameters describing $f_{\text{MM}}$ for galaxies with $\mathrm{log}(M_{*}/M_{\odot})\geq9.7$ and projected distance $r_p<30$ kpc. When convolving this $f_{\text{MM}}(z)$ with a merger timescale $T_{\text{MM}}\propto H(z)^{-1/3}$ and with a power-law scaling as $T_{\text{MM}}\propto (1+z)^{-2}$ we obtain a lower and milder $R_{\text{MM}}$ cosmic evolution with respect to our major merger rate results obtained with a (cite: Kitzbichler08) timescale, and a comparable trend with the (cite: Jiang14)-based evolution, respectively. Lastly, we show the predicted halo-halo merger rate by (cite: Dekel13) which over-predicts the observed merger rates at low redshifts but is in good agreement with the (cite: Snyder17)-based $R_{\text{MM}}$ at $z\sim6$.

We compute the average number of mergers a galaxy undergoes between $0<z<6$ by integrating the merger rate over time as $$\begin{equation}
    N_{\text{MM}} = \int_{z_1}^{z_2}{\frac{R_{\text{MM}}(z)}{(1+z)H_0E(z)}dz},
    \label{eq:Nmm}
\end{equation}$$ where $E(z)=\sqrt{\mathrm{\Omega_m}(1+z)^3+\mathrm{\Omega_\Lambda}}$, assuming a flat Universe (i.e., $\mathrm{\Omega_k}=0$). We show in Figure [5](#fig:merger_rate) (right panel) the cumulative number of major mergers as a function of redshift adopting three different timescales, with the 1$\sigma$ uncertainties derived from the errors on the major merger rate cosmic evolution. The average number of mergers computed with the (cite: Kitzbichler08) and (cite: Jiang14) prescriptions is low, ranging between 0.5 and 1.4 down to $z=0$. This is consistent, for instance, with the results by (cite: Mundy17) who found that galaxies with $\mathrm{log}(M_{*}/M_{\odot})>9.5$ at $z\sim3.5$ (selected at constant number densities, thus representing the progenitors of $\mathrm{log}(M_{*}/M_{\odot})>11$ galaxies at $z\sim0$) undergo $\sim0.5$ major mergers between $0<z<3.5$. However, if we assume an evolving merger timescale as $2.4~(1+z)^{-2}$ (cite: Snyder17), the average number of mergers since $z=6$ increases significantly, reaching $N_{\text{MM}}\sim8$ at the present day. Interestingly, this is similar to the result obtained by (cite: Conselice09) that found $N_{\text{MM}}\sim7$ by integrating Equation [\[eq:Nmm\]](#eq:Nmm) from $z=6$ to 0, and assuming a constant merger timescale $T_{\text{MM}}=0.35$ (which is equal to the average timescale by (cite: Snyder17) at $z<6$; see their Figure 15). When examining our results at higher redshifts, we find that the number of mergers diminishes quickly. In particular, at $z>4$, $N_{\text{MM}}\lesssim1$ if we consider the (cite: Kitzbichler08) and (cite: Jiang14) merger timescale evolution, suggesting that, in these scenarios, not every galaxy will undergo a merger during this epoch.

## Merger rate density

![](plots/merger_rate_density_davidzon.png)

As discussed in Section [4.3](#sec:merger_rate), the merger rate traces the number of merger events per galaxy at a given mass and redshift. A more informative quantity is the volume-averaged merger rate which is defined as $$\begin{equation}
    \Gamma_{\text{MM}}(z) = \frac{f_{\text{MM}}(z)~n(z)}{T_{\text{MM}}(z)},
    \label{eq:Gamma}
\end{equation}$$ where $f_{\text{MM}}$ and $T_{\text{MM}}$ are the previously defined merger fraction and merger timescale, and $n(z)$ is the number density of galaxies in Mpc$^{-3}$. The latter is computed by integrating the galaxy stellar mass function (GSMF) in a certain redshift bin and between a minimum and maximum stellar mass limit in the range $M_{*}^\text{min}<M_{*}<M_{*}^\text{max}$. In particular, we exploit the GSMFs best-fit parameters from (cite: Mortlock15), (cite: Santini12) and (cite: Davidzon17) at $z<3$, $3<z<4$ and $z>4$, respectively, after converting into a (cite: Chabrier03) IMF. However, it is worth noting that, as stated in (cite: Mundy17), making use of different GSMF parameterizations does not significantly change the final results. We thus integrate these functions from $\mathrm{log}(M_{*}/M_{\odot})=9$ to $\mathrm{log}(M_{*}/M_{\odot})=11$, in order to include the full possible range of galaxy masses for the considered data at different redshifts. We estimate the errors on $n(z)$ by perturbing the corresponding GSMF with the associated uncertainties on its best-fit parameters at each redshift. We repeat this procedure 10$^{4}$ times, recomputing the integrated number densities at each step. From the perturbed distributions we then obtain the 16th and 84th percentiles as the 1$\sigma$ errors on $n(z)$.

Figure [6](#fig:merger_rate_dens) shows the merger rate density computed with Equation [\[eq:Gamma\]](#eq:Gamma) for each of the data introduced in Section [4.2](#sec:merger_frac) and for the two $z>4$ ALPINE bins. For the sake of simplicity, in this case we report only the data points obtained by adopting the (cite: Kitzbichler08) prescription for the merger timescale. When using the $T_{\text{MM}}(z)$ redshift evolution from (cite: Jiang14) and (cite: Snyder17), we obtain similar trends but shifted to higher merger rate densities. The error bar on each point is computed by propagating the merger fraction and number density uncertainties on Equation [\[eq:Gamma\]](#eq:Gamma). At $1\lesssim z \lesssim 5$, (cite: Duncan19) found that the volume-averaged merger rate is quite constant. On the other hand, from our data we find a slight decrease both at $z<1$ and at $z>4$. At these early epochs, this difference could be caused by the poor constraints on the GSMFs adopted by (cite: Duncan19) which result in large uncertainties on their data, making it impossible to draw robust conclusions at $z\sim5$. Nevertheless, our derived merger rate densities are in agreement, within the uncertainties, with other results derived in the literature. For example, (cite: Mundy17) studied the evolution of the merger rate density up to $z\sim3.5$ for a large sample of $\mathrm{log}(M_{*}/M_{\odot})>10$ galaxies. They found that, for close pairs with projected separations $5<r_p<20~$kpc, the $\Gamma_{\text{MM}}(z)$ evolution is better described by a power-law of the form $\Gamma_0(1+z)^{\gamma}$, with $\Gamma_0 = 1.64^{+0.58}_{-0.41} \times 10^{-4}$ and $\gamma = {0.48}^{+1.00}_{-1.15}$. We report their results, along with the uncertainties, in Figure [6](#fig:merger_rate_dens) and extrapolate them to the redshifts explored by ALPINE. As evident, our data points are comparable with the results by (cite: Mundy17). If we also fit our merger rate densities (derived assuming the (cite: Kitzbichler08) merger timescale) with a power-law function we obtain $\Gamma_0 = (2.40\pm0.63) \times 10^{-4}$ and $\gamma = -0.16\pm0.23$, that are consistent with the above outcomes. The power-law fit on the data computed with the timescales by (cite: Jiang14) is in agreement with the (cite: Mundy17) findings, as well. If we instead consider the results obtained with the (cite: Snyder17) timescale, we find a rapid increase of the merger rate density with redshift, which departs from the upper envelope of (cite: Mundy17) already at $z\gtrsim1$.

Finally, we also show the results from the EMERGE simulation (cite: Oleary21) for galaxies in two different stellar mass bins. The two curves in the figure represent the intrinsic merger rate from the simulation for major mergers (i.e., $\mu<4$) selected basing on their main progenitor mass, thus describing a population of galaxies that will undergo a merger after a certain time. Galaxies with $\mathrm{log}(M_{*}/M_{\odot})>9$ are characterized by an increase of the merger rate density up to $z\sim1$, an almost constant $\Gamma_{\text{MM}}$ until $z\sim4$ and a slow decrease to the highest redshifts. At larger stellar masses, a slighter increase of $\Gamma_{\text{MM}}$ is present at low redshifts, while a steeper decrease in the early Universe is found. Both these trends are comparable to the one obtained in this work after exploiting data at different redshifts and including the new estimates at $z>4$ from the ALPINE survey. The fact that they are systematically smaller than our results could be ascribed to several factors, such as the lower merger fraction evolution found in their simulation or the measure of the intrinsic merger rate which is computed when the merging process is already happened (thus possibly enhancing the merger timescales with respect to our assumptions).

## The major merger specific mass accretion rate

By taking advantage of the merger rates and merger fraction deduced in the previous sections, we now provide an estimate of the average stellar mass gained by a galaxy during a merger event over cosmic time. To this aim, we compute the major merger specific mass accretion rate as $R_{\text{MM}}~\overline{\mu}^{-1}$, where $\overline{\mu}$ is the average mass ratio. We find that, for each data sample used to compute the merger rate at different redshifts, $\overline{\mu}^{-1}\sim0.5$, including the average mass ratio from our sample of major mergers for which we know $\mu_K$. Therefore, we just take the best-fitting functions to the cosmic evolution of the merger rate and multiply them by a factor $\sim0.5$ to obtain the specific mass accretion rate in Gyr$^{-1}$. Our results are reported in Figure [7](#fig:merger_ssfr) along with the specific star formation rate (sSFR) evolution obtained by different authors (cite: Dekel09; Speagle14; Tasca15; Khusanova21). As shown, star formation seems to be the dominant mode of mass growth at all epochs. However, if we assume a merger timescale $T_{\text{MM}}\propto (1+z)^{-2}$ (cite: Snyder17), the specific mass accretion rate reaches the sSFR at $z>3$, being comparable to it within the uncertainties. Therefore, we cannot exclude that major mergers may have significantly contributed to the galaxy mass assembly in the early Universe. In particular, if the galaxy growth is dominated by cold gas accretion, the sSFR should evolve with redshift as $(1+z)^{2.25}$ (e.g., (cite: Dekel09)). Some authors find instead a flattening of the trend or even a possible decrease with redshift as from the ALPINE data (cite: Tasca15; Faisst16; Khusanova21), leaving space to other mechanisms that could regulate the assembly of galaxies at high redshifts, such as major mergers (e.g., (cite: Tasca15; Faisst16)).

## The major merger mass accretion rate density

Similarly to what done in Section [4.5](#sec:specific_mar) for the specific mass accretion rate, we exploit here the major merger rate density to obtain an estimate of the mass accreted through major mergers per unit time and volume for galaxies in a given stellar mass range, $\rho_{\text{MM}}(z)$. This quantity can be compared to the other mechanisms of mass accretion, such as the mass gained through the process of star formation, and is then of fundamental importance to understand the role of mergers in the Universe.

Following (cite: Duncan19), we assume that the increase in stellar mass for each merger and at each redshift is given by $\overline{M}_{*}~\overline{\mu}^{-1}$, where $\overline{\mu}$ is the average mass ratio defined in Section [4.5](#sec:specific_mar) and $\overline{M}_{*}$ is the average stellar mass calculated through the GSMF. The latter is computed as $$\begin{equation}
    \overline{M}_{*}(z) = \frac{\int_{M_{*}^\text{min}}^{M_{*}^\text{max}}{\Phi(z,M_{*})~M_{*}~dM_{*}}}{\int_{M_{*}^\text{min}}^{M_{*}^\text{max}}{\Phi(z,M_{*})~dM_{*}}},
    \label{eq:average_M}
\end{equation}$$ where $\Phi(z,M_{*})$ represents the shape of the GSMF in a certain redshift bin. We estimate the uncertainties on $\overline{M}_{*}(z)$, as previously done for the number density, by recomputing it N times after perturbing the corresponding GSMF with its associated errors. At each redshift, we obtain a typical uncertainty of $\sim0.5~$dex. In this way, the stellar mass accretion rate density can be estimated as $$\begin{equation}
    \rho_{\text{MM}}(z) = \overline{\mu}^{-1}~\overline{M}_{*}~\Gamma_{\text{MM}}(z).
    \label{eq:rho_mm}
\end{equation}$$ We report the cosmic evolution of $\rho_{\text{MM}}$ in Figure [7](#fig:merger_ssfr) (right panel, on top). The dashed lines show the best-fitting curves to the data assuming a combined power-law and exponential function, as done for the merger fraction and merger rate, for different merger timescales. As shown, at $z>1$ the curves start to decrease quite rapidly to lower mass accretion rate densities.

Following (cite: Mundy17), we then provide the major merger accretion rate density computed with the results from the Illustris simulation, $\rho_{\text{ill}}(z)$. We convolve the specific mass accretion rate by (cite: Rodriguez16) with the number density of galaxies by (cite: Torrey15) as $$\begin{equation}
    \rho_{\text{ill}}(z) = \int_{M_{*}^\text{min}}^{M_{*}^\text{max}}\int_{\mu_\text{min}}^{\mu_\text{max}}
    \label{eq:rho_ill}{\Phi_{\text{ill}}(z,M_{*})~{\dot{m}}_\text{accr}(z,M_{*},\mu)~d\mu~dM_{*}},
\end{equation}$$ where $\Phi_{\text{ill}}$ is the shape of the GSMF at redshift $z$ and stellar mass $M_{*}$, and $\dot{m}_\text{accr}$ represents the average amount of mass accreted by a single galaxy when the merger occurs. As done for $\rho_{\text{MM}}$, we integrate the GSMF in the range $9<\mathrm{log}(M_{*}/M_{\odot})<11$ and the mass accretion rate for mass ratios between $1<\mu<4$, accounting for major mergers. The result of the integration is reported in Figure [7](#fig:merger_ssfr) as a function of redshift. As can be seen, the computed $\rho_{\text{ill}}$ is comparable with our findings, lying between the best-fit curves obtained by adopting the (cite: Kitzbichler08) and (cite: Snyder17) prescriptions for the merger timescale, respectively. Moreover, the shape of the curve is quite similar to those deduced by our analysis, with a fast decrease at high redshifts.

To compare the relative contribution of mergers and star formation to the mass assembly of galaxies through the cosmic time, we also show the star-formation rate density (SFRD) from (cite: Madau14), after converting for a Chabrier IMF[^15]. Moreover, we find that our data are also well fit by a double power-law of the form assumed by (cite: Madau14) for the SFRD, although we find no significant differences between the two functional forms when comparing them with a BIC statistics. The results of these fits are reported in the figure (solid lines), showing a flatter trend to the early Universe with respect to the combined power-law and exponential curves. In the bottom region of the figure we show the ratio between the major merger and star formation contributions to the stellar mass accretion in galaxies at different epochs. Looking at both curves, if we assume the merger timescales by (cite: Kitzbichler08) and (cite: Jiang14), major mergers seem to contribute less than $10\%$ to the galaxy mass assembly compared to the star formation mechanism at all redshifts. For comparison we also report, in the top panel, the total (UV+IR) SFRD obtained with the ALPINE data (cite: Khusanova21). These measurements indicate a possible $z>4$ evolution of the SFRD that is shallower than previously thought, further decreasing the importance of major mergers to the mass assembly of galaxies at these epochs. On the other hand, adopting the (cite: Snyder17) timescale prescription, a larger contribution of mergers in the early Universe is in place which becomes comparable to that provided by the star formation at $z\gtrsim6$.

# Discussion

## The importance of the merger timescale

As evidenced by the results presented in Section [4](#sec:results), one of the major sources of uncertainty in the investigation of the contribution of major mergers to the mass assembly of galaxies through cosmic time is the typical time needed for a pair of objects to coalesce with each other. Indeed, this parameter is critical for converting the pair fraction into a merger rate, affecting all the derived quantities as well. Because of this, it could represent the main reason of disagreement between models and observations noticed in many works.

Previous studies often assumed $T_{\text{MM}}$ as a constant over time. However, the emerging picture of a possibly decreasing (as found in this work) or nearly flat merger fraction through high redshifts (cite: Conselice09; Ventou17; Mantha18), compared to the increase of the merger rate found in most simulations over the same epoch (e.g., (cite: Hopkins10; Rodriguez15)), suggests that a redshift-dependent merger timescale is more suitable to reconcile models and observations. Here we show the results derived from three different merger timescales (cite: Kitzbichler08; Jiang14; Snyder17), as introduced in Section [4.3](#sec:merger_rate), and compare them with state-of-the-art simulations. (cite: Kitzbichler08) found a merger timescale which slightly depends on the primary galaxy mass and that increases with redshift, leading to lower values of the merger rate when moving to early epochs. On the other hand, (cite: Jiang14) and (cite: Snyder17) found a slow and fast decrease of $T_{\text{MM}}$ over time, respectively, implying a larger contribution from mergers to the galaxy mass assembly at $z>4$.

Looking at Figure [5](#fig:merger_rate) (left panel), the merger rates obtained from the (cite: Kitzbichler08) timescale prescription are not easily reproducible by models. In fact, although we find values of $R_{\text{MM}}$ comparable to those of the EMERGE simulation (cite: Oleary21) at $z\gtrsim5$, the latter are computed with a (cite: Jiang14)-like evolving timescale which can provide $T_{\text{MM}}$ values up to 5 times lower than the (cite: Kitzbichler08) ones at these epochs. A good agreement with the $T_{\text{MM}}\propto H(z)^{-1/3}$ merger rates is found by convolving the EMERGE pair fraction evolution with the decreasing (cite: Snyder17) timescale (again using smaller merging times in the simulation with respect to the observations) and with the outputs of the (cite: Hopkins10) simulations, at least at $z<3$ (indeed, they predicted larger merger rates with respect to our findings at earlier epochs). However, in this case, we note that the merger rates from (cite: Hopkins10) are properly computed up to $z\sim3$ and that the high-redshift extrapolation could be different from the real outputs of their simulation. Moreover, the observed shift between our findings and the EMERGE results due to the different choice of the merger timescale could be ascribed to the merger fraction evolution which, from their simulation, is smaller than ours. Finally, the fast-decreasing merger timescale by (cite: Snyder17) lead to merger rates which are more than an order of magnitude larger than those from the (cite: Kitzbichler08) and (cite: Jiang14) prescriptions. Adopting this formalism, we find that our merger rates are larger than those predicted by the Illustris simulations (cite: Rodriguez15) (with an average mass ratio $\sim2$) and comparable with the merger rates of $M_\text{halo}\sim10^{12}~M_{\odot}$ by (cite: Neistein08; Dekel13) at $z\sim6$.

(cite: Duncan19) found a good agreement between their observations and simulated merger rates from (cite: Rodriguez15) for galaxies with $\mathrm{log}(M_{*}/M_{\odot})>10.3$, while they also obtained higher values than those predicted for lower mass galaxies. However, the results of that simulation depend significantly on the adopted mass ratio. Indeed, assuming $\mu>2$, the Illustris simulation is able to reproduce our observations, at least at $z\gtrsim4$. Moreover, (cite: Mantha18) also found merger rates comparable to those predicted by (cite: Rodriguez15) up to $z\sim3$ by dividing their observed pair fraction by the (cite: Snyder17) merger timescale.

These results suggest that to reconcile observations and simulations, a redshift-evolving timescale should be employed when converting the pair fraction into a merger rate, with a $T_{\text{MM}}$ decreasing toward early epochs likely being the most suitable choice. However, many other factors can affect the $R_{\text{MM}}$ estimates, like the probability of merging $C_{\text{merg}}$ or the dependency of the merger timescale on several properties like the stellar mass of the galaxies, the on-going phase of the merger or the selection criteria of the close pairs. For these reasons, further investigation is needed in order to obtain more robust conclusions on the incidence of merger through cosmic time.

## The contribution of major mergers to the galaxy mass-assembly

The relative contribution of the different mechanisms driving the galaxy mass assembly through cosmic time has yet to be ascertained. The most favored scenario predicts cold accretion and in situ star formation as the principal sources of stellar mass increase in galaxies, with major mergers only playing a minor role in the galaxy build-up (e.g., (cite: Dekel09; Conselice13; Kaviraj13; Sanchez14)). However, during the last years several works started to suggest a prominent contribution of mergers within this context, opening again the debate on the importance of these events in the framework of galaxy evolution (e.g., (cite: Tasca14; Mantha18; Duncan19)).

Depending on the merger timescale adopted, with our new ALPINE data we can find large merger rates up to high redshifts which could imply a substantial contribution of these events to the galaxy mass accretion at early epochs. We find that the stellar mass accretion rate density due to major mergers has a similar redshift evolution as the cosmic SFRD (cite: Madau14) and that, assuming the (cite: Snyder17) merger timescale, they become comparable with each other at redshifts approaching the Reionization epoch. However, the lack of further constraints on the most suitable choice for the merger timescale prevent us from providing firm conclusions. Indeed, looking at Figure [7](#fig:merger_ssfr) (right panel), the importance of major mergers in the assembly of galaxies could be very different, especially at high redshifts, depending on all the above-mentioned caveats and also on the adopted fitting function. It is worth noting that the comparison between the SFRD and the mass accretion rate density in Figure [7](#fig:merger_ssfr) is not intended to provide the contribution of major mergers to the global star formation through cosmic time, rather it represents the relative importance of the two processes to the galaxy mass assembly at a given epoch.

Despite this, we can certainly affirm that major mergers are frequent processes in the early Universe and must be accounted for when considering the mechanisms of galaxy assembly across cosmic time.

# Summary and conclusions

In this work, we investigate the role of major mergers in the stellar mass assembly of galaxies at $z\sim5$. To this aim, we take advantage of the recent \[CII\] observations of a significant statistical sample of normal star-forming galaxies in the early Universe, as carried out by the ALMA large program ALPINE. The large amount of data (both spectroscopic and photometric) available for these sources combined with their new morphological and kinematic characterization made possible by the 3D \[CII\] information, allow us to put one of the first constraints on the fraction and rate of mergers shortly after the end of the Epoch of Reionization. Indeed, only a handful of works have been undertaken so far about the study of the mergers contribution to the build-up of galaxies at $z>4$, among which some are affected by large uncertainties due, for instance, to the lack of spectroscopic redshifts which properly identify close pairs. In the following, we summarize our major results:

$\bullet$

We identify 23 mergers, corresponding to $\sim31\%$ of the 75 ALPINE \[CII\]-detected galaxies, with an average stellar mass of the most massive galaxies of $\mathrm{log}(M_{*}/M_{\odot})\sim10$. We find major merger fractions $f_{\text{MM}}=0.44^{+0.11}_{-0.16}$ and $f_{\text{MM}}=0.34^{+0.10}_{-0.13}$ at $z\sim4.5$ and $z\sim5.5$, respectively, after taking into account the presence of minor mergers and correcting for completeness. These results are in good agreement with morphological studies by (cite: Conselice09) at the same redshifts and, when combined with previous works down to the local Universe, suggest a cosmic merger fraction evolution with a rapid increase from $z=0$ to $z\sim2$, a peak at $z\sim2-3$, and a possible slow decline for $z>3$. This trend is well described by a combined power-law and exponential function and is quite comparable with the outputs of the EAGLE hydrodynamical simulations from which (cite: Qu17) claim that major mergers contribute less than $10\%$ to the stellar mass gain in galaxies less massive than log$(M_{*}/M_{\odot})=10.5$, attributing a leading role to the in situ star formation.

We convert the merger fraction into the merger rate per galaxy by adopting different redshift scaling for the typical time of merging ($T_{\text{MM}}$). The results we obtain are strongly dependent on the choice of $T_{\text{MM}}$. For instance, (cite: Kitzbichler08) found a merger timescale evolution which diverges more and more from that of (cite: Snyder17) moving to high redshift. When using the first timescale prescription, we obtain $R_{\text{MM}}\sim0.09$ and $R_{\text{MM}}\sim0.07$ Gyr$^{-1}$ at $z\sim4.5$ and $z\sim5.5$, respectively. However, these numbers are more than an order of magnitude larger if $T_{\text{MM}}\propto(1+z)^{-2}$ is used. Accordingly, this uncertainty propagates to all our subsequent outcomes that involve the choice of a merger timescale.

By integrating the merger rate over time we obtain the average number of mergers a galaxy undertakes during its cosmic history from the early to the local Universe which goes from less than 1 to $\sim8$ mergers at $z=0$, depending on the adopted merger timescale prescription. Our results are quite in agreement with the outputs of several cosmological simulations, especially when adopting the redshift-dependent (cite: Snyder17) merger timescale with which we can match the large merger rates predicted at high redshifts by the Illustris simulations (cite: Rodriguez15) and the halo-halo merger rate by (cite: Dekel13).

Another important quantity we estimate is the volume-averaged merger rate $\Gamma_{\text{MM}}$, that is the merger rate $R_{\text{MM}}$ multiplied by the number density of galaxies at a given redshift and for a specific stellar mass range. We find a nearly constant $\Gamma_{\text{MM}}$ at intermediate redshifts in agreement with previous works in the literature (cite: Mundy17; Duncan19), and a possible decrease at both $z<1$ and $z>4$.

We take advantage of the two observationally-estimated merger rates to provide a constraint on the contribution of major mergers to the galaxy mass assembly through the cosmic epochs. From the merger rate per galaxy, we obtain the average stellar mass accreted per major merger per unit of mass and compare it with the sSFR computed from different authors. The latter seems to dominate over the specific mass accretion rate at all times. However, when considering a rapidly evolving merger timescale like $T_{\text{MM}}\propto(1+z)^{-2}$, the two quantities become comparable within the uncertainties at $z>4$. We then estimate the mass accretion rate density from $\Gamma_{\text{MM}}$ and compare this quantity to the well-known SFRD cosmic evolution (cite: Madau14). We note that the contribution of major mergers to the global star formation rate ranges between being approximately equal to the SFRD to less than 1% of it, depending on the exact choice of the merging timescale, the parametric form used to fit the data, and the redshift.

To conclude, major mergers could have played a significant role in the galaxy mass assembly through cosmic time, especially when merger timescales from recent literature, in which $T_{\text{MM}}$ decreases rapidly with increasing redshift, are taken into account. However, future investigation is needed in order to finally establish the importance of such events in the complex picture of the galaxy evolution. In particular, a larger statistical sample of spectroscopically confirmed galaxies, observed with deeper resolution, will allow us to confirm the large fraction of mergers at early times and their incidence at different redshifts, unveiling the relative contribution of each process to the build-up of galaxies through the Universe.

# Acknowledgements

We warmly thank the referee for her or his careful reading of the paper and constructive suggestions that contributed to improve the quality of this work. This paper is based on data obtained with the ALMA Observatory, under Large Program 2017.1.00428.L. ALMA is a partnership of ESO (representing its member states), NSF(USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. A.C. acknowledges the support from grant PRINMIUR 2017 - 20173ML3WW$\_$001. The Cosmic Dawn Center is funded by the Danish National Research Foundation under grant No. 140. G.C.J. acknowledges ERC Advanced Grant 695671 “QUENCH” and support by the Science and Technology Facilities Council (STFC). This work was supported by the Programme National Cosmology et Galaxies (PNCG) of CNRS/INSU with INP and IN2P3, co-funded by CEA and CNES. E.I. acknowledges partial support from FONDECYT through grant N$^\circ$ 1171710. This paper is dedicated to the memory of Olivier Le Fèvre, PI of the ALPINE survey.

129 natexlab

(ref: Beckwith06) Beckwith, S. V. W., Stiavelli, M., Koekemoer, A. M., et al. 2006, AJ, 132, 1729

(ref: Bethermin20) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: Bluck12) Bluck, A. F. L., Conselice, C. J., Buitrago, F., et al. 2012, ApJ, 747, 34

(ref: Bouche10) Bouché, N., Dekel, A., Genzel, R., et al. 2010, ApJ, 718, 1001

(ref: Bouche16) Bouché, N., Finley, H., Schroetter, I., et al. 2016, ApJ, 820, 121

(ref: Bouche13) Bouché, N., Murphy, M. T., Kacprzak, G. G., et al. 2013, Science, 341, 50

(ref: Capak08) Capak, P., Carilli, C. L., Lee, N., et al. 2008, ApJL, 681, L53

(ref: Cardamone10) Cardamone, C. N., van Dokkum, P. G., Urry, C. M., et al. 2010, ApJS, 189, 270

(ref: Carniani18) Carniani, S., Maiolino, R., Amorin, R., et al. 2018, MNRAS, 478, 1170

(ref: Casteels14) Casteels, K. R. V., Conselice, C. J., Bamford, S. P., et al. 2014, MNRAS, 445, 1157

(ref: Cattaneo09) Cattaneo, A., Faber, S. M., Binney, J., et al. 2009, Nature, 460, 213

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: Chiaberge15) Chiaberge, M., Gilli, R., Lotz, J. M., & Norman, C. 2015, ApJ, 806, 147

(ref: Conselice09) Conselice, C. J. & Arnold, J. 2009, MNRAS, 397, 208

(ref: Conselice03) Conselice, C. J., Bershady, M. A., Dickinson, M., & Papovich, C. 2003, AJ, 126, 1183

(ref: Conselice13) Conselice, C. J., Mortlock, A., Bluck, A. F. L., Grützbauch, R., & Duncan, K. 2013, MNRAS, 430, 1051

(ref: Conselice08) Conselice, C. J., Rajgor, S., & Myers, R. 2008, MNRAS, 386, 909

(ref: Contini12) Contini, T., Garilli, B., Le Fèvre, O., et al. 2012, A&A, 539, A91

(ref: Davidzon17) Davidzon, I., Ilbert, O., Laigle, C., et al. 2017, A&A, 605, A70

(ref: deRavel09) de Ravel, L., Le Fèvre, O., Tresse, L., et al. 2009, A&A, 498, 379

(ref: Dekel09) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: Dekel13) Dekel, A., Zolotov, A., Tweed, D., et al. 2013, MNRAS, 435, 999

(ref: DiTeodoro15) Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021

(ref: Duncan19) Duncan, K., Conselice, C. J., Mundy, C., et al. 2019, ApJ, 876, 110

(ref: Fabian06) Fabian, A. C., Celotti, A., & Erlund, M. C. 2006, MNRAS, 373, L16

(ref: Faisst16) Faisst, A. L., Capak, P., Hsieh, B. C., et al. 2016, ApJ, 821, 122

(ref: Faisst20) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: Fujimoto20) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1

(ref: Genel14) Genel, S., Vogelsberger, M., Springel, V., et al. 2014, MNRAS, 445, 175

(ref: Giavalisco04) Giavalisco, M., Ferguson, H. C., Koekemoer, A. M., et al. 2004, ApJL, 600, L93

(ref: Ginolfi20) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 643, A7

(ref: Grogin11) Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, ApJS, 197, 35

(ref: Guo13) Guo, Y., Ferguson, H. C., Giavalisco, M., et al. 2013, ApJS, 207, 24

(ref: Hasinger18) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77

(ref: Hasinger07) Hasinger, G., Cappelluti, N., Brunner, H., et al. 2007, ApJS, 172, 29

(ref: Hopkins10) Hopkins, P. F., Bundy, K., Croton, D., et al. 2010, ApJ, 715, 202

(ref: Ilbert09) Ilbert, O., Capak, P., Salvato, M., et al. 2009, ApJ, 690, 1236

(ref: Jiang14) Jiang, C. Y., Jing, Y. P., & Han, J. 2014, ApJ, 790, 7

(ref: Jogee09) Jogee, S., Miller, S. H., Penner, K., et al. 2009, ApJ, 697, 1971

(ref: Jones20) Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491, L18

(ref: Jones17) Jones, G. C., Carilli, C. L., Shao, Y., et al. 2017, ApJ, 850, 180

(ref: Jones21) Jones, G. C., Vergani, D., Romano, M., et al. 2021, arXiv e-prints, arXiv:2104.03099

(ref: Kartaltepe12) Kartaltepe, J. S., Dickinson, M., Alexander, D. M., et al. 2012, ApJ, 757, 23

(ref: Kauffmann93) Kauffmann, G., White, S. D. M., & Guiderdoni, B. 1993, MNRAS, 264, 201

(ref: Kaviraj13) Kaviraj, S., Cohen, S., Windhorst, R. A., et al. 2013, MNRAS, 429, L40

(ref: Kaviraj14) Kaviraj, S., Huertas-Company, M., Cohen, S., et al. 2014, MNRAS, 443, 1861

(ref: Keres09) Kereš, D., Katz, N., Fardal, M., Davé, R., & Weinberg, D. H. 2009, MNRAS, 395, 160

(ref: Keres05) Kereš, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2

(ref: Khochfar05) Khochfar, S. & Burkert, A. 2005, MNRAS, 359, 1379

(ref: Khusanova21) Khusanova, Y., Bethermin, M., Le Fèvre, O., et al. 2021, A&A, 649, A152

(ref: Kitzbichler08) Kitzbichler, M. G. & White, S. D. M. 2008, MNRAS, 391, 1489

(ref: Klypin11) Klypin, A. A., Trujillo-Gomez, S., & Primack, J. 2011, ApJ, 740, 102

(ref: Koekemoer07) Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172, 196

(ref: Koekemoer11) Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS, 197, 36

(ref: Kohandel19) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2019, MNRAS, 487, 3007

(ref: Laigle16) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24

(ref: LeFevre00) Le Fèvre, O., Abraham, R., Lilly, S. J., et al. 2000, MNRAS, 311, 565

(ref: LeFevre20) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: LeFevre15) Le Fèvre, O., Tasca, L. A. M., Cassata, P., et al. 2015, A&A, 576, A79

(ref: LeFevre05) Le Fèvre, O., Vettolani, G., Garilli, B., et al. 2005, A&A, 439, 845

(ref: Leja13) Leja, J., van Dokkum, P., & Franx, M. 2013, ApJ, 766, 33

(ref: Lemaux18) Lemaux, B. C., Le Fèvre, O., Cucciati, O., et al. 2018, A&A, 615, A77

(ref: Lemaux17) Lemaux, B. C., Tomczak, A. R., Lubin, L. M., et al. 2017, MNRAS, 472, 419

(ref: Lin10) Lin, L., Cooper, M. C., Jian, H.-Y., et al. 2010, ApJ, 718, 1158

(ref: Lin2008) Lin, L., Patton, D. R., Koo, D. C., et al. 2008, ApJ, 681, 232

(ref: Loiacono21) Loiacono, F., Decarli, R., Gruppioni, C., et al. 2021, A&A, 646, A76

(ref: Lopez15) López-Sanjuan, C., Cenarro, A. J., Varela, J., et al. 2015, A&A, 576, A53

(ref: Lopez11) López-Sanjuan, C., Le Fèvre, O., de Ravel, L., et al. 2011, A&A, 530, A20

(ref: Lopez12) López-Sanjuan, C., Le Fèvre, O., Ilbert, O., et al. 2012, A&A, 548, A7

(ref: Lopez13) López-Sanjuan, C., Le Fèvre, O., Tasca, L. A. M., et al. 2013, A&A, 553, A78

(ref: Lotz11) Lotz, J. M., Jonsson, P., Cox, T. J., et al. 2011, ApJ, 742, 103

(ref: Lotz10) Lotz, J. M., Jonsson, P., Cox, T. J., & Primack, J. R. 2010, MNRAS, 404, 575

(ref: Lotz13) Lotz, J. M., Papovich, C., Faber, S. M., et al. 2013, ApJ, 773, 154

(ref: Madau14) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Man12) Man, A. W. S., Toft, S., Zirm, A. W., Wuyts, S., & van der Wel, A. 2012, ApJ, 744, 85

(ref: Man16) Man, A. W. S., Zirm, A. W., & Toft, S. 2016, ApJ, 830, 89

(ref: Mantha18) Mantha, K. B., McIntosh, D. H., Brennan, R., et al. 2018, MNRAS, 475, 1549

(ref: McCracken12) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mortlock15) Mortlock, A., Conselice, C. J., Hartley, W. G., et al. 2015, MNRAS, 447, 2

(ref: Moster18) Moster, B. P., Naab, T., & White, S. D. M. 2018, MNRAS, 477, 1822

(ref: Mundy17) Mundy, C. J., Conselice, C. J., Duncan, K. J., et al. 2017, MNRAS, 470, 3507

(ref: Mundy15) Mundy, C. J., Conselice, C. J., & Ownsworth, J. R. 2015, MNRAS, 450, 3696

(ref: Nayyeri17) Nayyeri, H., Hemmati, S., Mobasher, B., et al. 2017, ApJS, 228, 7

(ref: Neistein08) Neistein, E. & Dekel, A. 2008, MNRAS, 388, 1792

(ref: Noeske07) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43

(ref: Oleary21) O’Leary, J. A., Moster, B. P., & Krämer, E. 2021, MNRAS, 503, 5646

(ref: Oser12) Oser, L., Naab, T., Ostriker, J. P., & Johansson, P. H. 2012, ApJ, 744, 63

(ref: Ownsworth14) Ownsworth, J. R., Conselice, C. J., Mortlock, A., et al. 2014, MNRAS, 445, 2198

(ref: Pallottini17) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2017, MNRAS, 465, 2540

(ref: Papovich11) Papovich, C., Finkelstein, S. L., Ferguson, H. C., Lotz, J. M., & Giavalisco, M. 2011, MNRAS, 412, 1123

(ref: Patton2000) Patton, D. R., Carlberg, R. G., Marzke, R. O., et al. 2000, ApJ, 536, 153

(ref: Pelliccia19) Pelliccia, D., Lemaux, B. C., Tomczak, A. R., et al. 2019, MNRAS, 482, 3514

(ref: Qu17) Qu, Y., Helly, J. C., Bower, R. G., et al. 2017, MNRAS, 464, 1659

(ref: Rodighiero11) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40

(ref: Rodriguez15) Rodriguez-Gomez, V., Genel, S., Vogelsberger, M., et al. 2015, MNRAS, 449, 49

(ref: Rodriguez16) Rodriguez-Gomez, V., Pillepich, A., Sales, L. V., et al. 2016, MNRAS, 458, 2371

(ref: Salpeter55) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: Sanchez14) Sánchez Almeida, J., Elmegreen, B. G., Muñoz-Tuñón, C., & Elmegreen, D. M. 2014, A&ARv, 22, 71

(ref: Sanders07) Sanders, D. B., Salvato, M., Aussel, H., et al. 2007, ApJS, 172, 86

(ref: Santini12) Santini, P., Fontana, A., Grazian, A., et al. 2012, A&A, 538, A33

(ref: Schaye15) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521

(ref: Schinnerer08) Schinnerer, E., Carilli, C. L., Capak, P., et al. 2008, ApJL, 689, L5

(ref: Scoville17a) Scoville, N., Abraham, R. G., Aussel, H., et al. 2007a, ApJS, 172, 38

(ref: Scoville17b) Scoville, N., Aussel, H., Brusa, M., et al. 2007b, ApJS, 172, 1

(ref: Shah20) Shah, E. A., Kartaltepe, J. S., Magagnoli, C. T., et al. 2020, ApJ, 904, 107

(ref: Silk98) Silk, J. & Rees, M. J. 1998, A&A, 331, L1

(ref: Smolcic17) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1

(ref: Snyder17) Snyder, G. F., Lotz, J. M., Rodriguez-Gomez, V., et al. 2017, MNRAS, 468, 207

(ref: Solomon92) Solomon, P. M., Downes, D., & Radford, S. J. E. 1992, ApJL, 398, L29

(ref: Speagle14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Springel05) Springel, V., White, S. D. M., Jenkins, A., et al. 2005, Nature, 435, 629

(ref: Tasca15) Tasca, L. A. M., Le Fèvre, O., Hathi, N. P., et al. 2015, A&A, 581, A54

(ref: Tasca14) Tasca, L. A. M., Le Fèvre, O., López-Sanjuan, C., et al. 2014, A&A, 565, A10

(ref: Tasca17) Tasca, L. A. M., Le Fèvre, O., Ribeiro, B., et al. 2017, A&A, 600, A110

(ref: Tomczak17) Tomczak, A. R., Lemaux, B. C., Lubin, L. M., et al. 2017, MNRAS, 472, 3512

(ref: Torrey15) Torrey, P., Wellons, S., Machado, F., et al. 2015, MNRAS, 454, 2770

(ref: Ventou17) Ventou, E., Contini, T., Bouché, N., et al. 2017, A&A, 608, A9

(ref: Ventou19) Ventou, E., Contini, T., Bouché, N., et al. 2019, A&A, 631, A87

(ref: Vogelsberger14) Vogelsberger, M., Genel, S., Springel, V., et al. 2014, MNRAS, 444, 1518

(ref: White91) White, S. D. M. & Frenk, C. S. 1991, ApJ, 379, 52

(ref: Whitney19) Whitney, A., Conselice, C. J., Bhatawdekar, R., & Duncan, K. 2019, ApJ, 887, 113

(ref: Wild09) Wild, V., Walcher, C. J., Johansson, P. H., et al. 2009, MNRAS, 395, 144

(ref: Williams00) Williams, R. E., Baum, S., Bergeron, L. E., et al. 2000, AJ, 120, 2735

(ref: Wu14) Wu, P.-F., Gal, R. R., Lemaux, B. C., et al. 2014, ApJ, 792, 16

(ref: Xu12) Xu, C. K., Zhao, Y., Scoville, N., et al. 2012, ApJ, 747, 85

(ref: Yan20) Yan, L., Sajina, A., Loiacono, F., et al. 2020, ApJ, 905, 147

(ref: Zabl19) Zabl, J., Bouché, N. F., Schroetter, I., et al. 2019, MNRAS, 485, 1961

(ref: Zanella21) Zanella, A., Pallottini, A., Ferrara, A., et al. 2021, MNRAS, 500, 118

# Individual description of mergers

We present here the characterization of the mergers analyzed in this work, as illustrated in Section [3.1](#sec:mergers_charact) and Figure [1](#fig:merger_example). For each source, we show the moment maps, the PVDs, and the integrated \[CII\] spectrum. Due to the peculiarity of these objects, we briefly comment on them in the following, also highlighting possible differences and similarities with the previous morpho-kinematic classifications.

**CG$\_$38**: (cite: LeFevre20) classified this galaxy as a merger. Although the low S/N and small spatial extent, we include this source in our analysis as it shows multiple peaks in the PVDs that are associated to different components in the \[CII\] spectrum.

**DC$\_$308643**: this source was classified as a merger by (cite: LeFevre20). The moment-1 map shows a clear velocity gradient suggesting the presence of a rotating disk. However, a similar velocity map could also be reproduced by two merging components in an advanced phase of merging. This is suggested by the two close components visible in the PVD along the major axis and by the shape of the \[CII\] line which deviates from that of a single Gaussian.

**DC$\_$372292**: we confirm the merger classification of this object by (cite: LeFevre20). As for DC$\_$308643, a possible velocity gradient is present in the moment-1 map. However, two components separated in velocity by $\sim200$ km s$^{-1}$ are clearly visible in the PVDs and in the spectrum.

**DC$\_$378903**: we classify this source as a merger as in (cite: LeFevre20). Despite the low S/N and spatial extent, we manage to decompose the \[CII\] spectrum in two guassian components that are also visible at $3\sigma$ in the PVDs and in the channel maps.

**DC$\_$417567**: this source was classified as a merger by (cite: LeFevre20) because of the disturbed \[CII\] morphology and the presence of multiple peaks in the PVDs. These are reproduced by different Gaussian components in the overall \[CII\] spectrum. This target was also analyzed by (cite: Jones21) which classified it as uncertain because of its low S/N. However, the poor $\mathrm{^{3D}Barolo}$ fit supports the merger classification for this object.

**DC$\_$422677**: as in (cite: LeFevre20), we classify this source as a merger, mainly because of the presence of multiple components in the PVDs and in the spectrum.

**DC$\_$434239**: this object was classified as a merger both by (cite: LeFevre20) and (cite: Jones21). The \[CII\] morphology is extended and disturbed, as well as that from the UVista $K_s$ band. The PVDs show multiple peaks and we need at least three components to reproduce the global shape of the \[CII\] spectrum.

**DC$\_$493583**: we classify this source as a merger as in (cite: LeFevre20). Two separate components are visible both in the PVDs and in the spectrum, with a fainter minor object emerging from the noise at $v\sim-200$ km s$^{-1}$.

**DC$\_$519281**: this source was classified as a merger by (cite: LeFevre20). The complex velocity map and PVDs sustain this interpretation. Further evidence for ongoing merging activity is provided by the analysis of (cite: Jones21) (even if they classify this object as uncertain because of the low S/N and spatial resolution).

**DC$\_$536534**: the \[CII\] emission from this galaxy is spatially resolved in different clumps, allowing (cite: LeFevre20) to classify it as a merger. The PVDs are clearly disturbed and multipeaked, and the integrated spectrum shows the presence of at least three different emitting components.

**DC$\_$665509**: previously classified as a merging system (cite: LeFevre20), this source shows multiple components both in the spectrum and in the PVDs with the two major emissions at $v\sim0$ and $v\sim150$ km s$^{-1}$.

**DC$\_$680104**: this object was classified as a merger by (cite: LeFevre20). It shows a faint secondary component at $3\sigma$ in the moment-0 map which is also visible in the PVD along the major axis at a spatial offset of $\sim-1$ arcsec with respect to the main target. Although the S/N of this source is low, we consider it as a merger, mainly because of two peaks of emission in the PVDs at the same spatial position but separated by $\sim150$ km s$^{-1}$ in velocity. These are also visible in the \[CII\] spectrum.

**DC$\_$814483**: the presence of multiple components in the optical images and the quite disturbed morphology of the \[CII\] emission led (cite: LeFevre20) to classify this galaxy as a merger. We confirm the previous classification also noting the complex velocity field and the multiple components in the spectrum, possibly associated to peaks of emission in the PVDs.

**DC$\_$818760**: this source was studied in detail by (cite: Jones20) and then further analyzed by (cite: Jones21). It is likely a triple merger, with the two main components visible in the optical maps and close in velocity (as shown by the PVD along the major axis), and another fainter source completely obscured in the optical and separated both in space and velocity from the other two objects. We thus confirm the previous merger classification by (cite: LeFevre20) and (cite: Jones21). In this analysis, we use a pseudo-slit 7.5 arcsec wide to recover the full \[CII\] emission, and we consider only the two close components with the larger \[CII\] fluxes and optical emission.

**DC$\_$834764**: this source was classified as an extended dispersion-dominated galaxy by (cite: LeFevre20). However, the peaks of emission in the PVDs, the shape of the emission line, and the quite disturb velocity field suggest the presence of multiple components. We thus classify this object as a merger.

**DC$\_$842313**: this galaxy is quite peculiar and was classified as a merger by (cite: LeFevre20). The optical maps show the presence of two or three components. Indeed, the ALPINE target is at the center of the maps, clearly visible in the HST F814W image, while a brighter and larger component also detected in \[CII\] is present toward the north, particularly visible in the UVista $K_s$-band map. This is the well-studied submillimeter galaxy J1000+0234 (e.g., (cite: Capak08; Schinnerer08; Jones17)), and it was serendipitously observed in ALPINE (cite: Loiacono21). This galaxy has a large line width (i.e., $\sim1000$ km s$^{-1}$) and is separated in velocity by $\sim750$ km s$^{-1}$ from the main ALPINE target. As we are considering only those systems with a velocity separation $\Delta v\leq500$ km s$^{-1}$ (assuming these components as gravitationally bound; (cite: Patton2000)), we should exclude it from our analysis. However, considering only the emission arising from the spectral channels associated to the main target DC$\_$842313, we find further evidence of an ongoing merging. In particular, we note a disturbed \[CII\] morphology elongated toward the extended $K_s$-band contours in the southwest region of the optical image, and peaks of emission in the PVDs coinciding with multiple components in the spectrum. For these reasons, we think that this could be a triple merging system, and we keep it in the analysis of the merger fraction. In this case, the moment maps and PVDs show the emission from both the main target and J1000+0234, obtained considering all the spectral channels including the \[CII\] emission from the two sources. The bottom panel displays instead the individual normalized integrated spectra of the two components.

**DC$\_$859732**: this galaxy was classified as a merger by (cite: LeFevre20). Two distinct components are present in the \[CII\] spectrum, partially visible in the PVDs due to the low S/N.

**DC$\_$873321**: this galaxy was classified as a merger both by (cite: LeFevre20) and (cite: Jones21). The \[CII\] emission is elongated toward the two bright sources visible in the UVista $K_s$ band. These two components are at the same velocity, being indistinguishable in the PVDs and their spectra are shown in the bottom panel of Fig. [18](#fig:merger_appendix11) (right).

**vc$\_$5100541407**: the extended \[CII\] morphology coincident with the two optical components visible in the maps, allowed (cite: LeFevre20) to characterize this source as a merger. (cite: Jones21) classified it as uncertain instead, mainly because of their adopted classification criteria. Given the morphological and kinematic information on this galaxy, we also consider it as a merger of two components emitting at the same velocity. A pseudo-slit 4.5 arcsec wide is used to compute the PVDs.

**vc$\_$5101209780**: this galaxy was classified as a merger both by (cite: LeFevre20) and (cite: Jones21), and it was the subject of a further and in-depth analysis by (cite: Ginolfi20). The \[CII\] moment-0 map clearly shows the presence of two major components, as also confirmed by the optical images. Two fainter components are also found in the spectrum and PVDs, which are computed by adopting a pseudo-slit 4.5 arcsec wide.

**vc$\_$5180966608**: (cite: LeFevre20) classified this object as a merger while (cite: Jones21) considered it as uncertain, mainly because of the \[CII\] spectrum which resembles that of a single, extended source. We find more evidence for a merging system. Indeed, at least two optical components are visible both from HST and UVista within the $3\sigma$ \[CII\] emission contours. The velocity gradient is quite disturbed and several peaks of emission are present in the PVDs, more visible along the minor axis (which is aligned with the two optical sources).

[^1]: E-mail: michael.romano@studenti.unipd.it

[^2]: Passed away.

[^3]: DR1 data are available at <https://cesam.lam.fr/a2c2s/data_release.php>.

[^4]: For a detailed description of the procedure used to estimate the range of spectral channels containing line emission for all the \[CII\]-detected galaxies, see Section 6.1 in (cite: Bethermin20).

[^5]: In case of multiple spatially-resolved \[CII\] emissions, we use the position provided by the Gaussian fit on the global system rather than the positions obtained by fitting individual 2D Gaussians to each of the observed components.

[^6]: Two merging systems with different velocity fields or a rotating galaxy with a clear velocity gradient would be ideally represented with separated components in the PVDs and with an ‘‘S-shape’’ in the PVD along the major axis, respectively.

[^7]: We note that (cite: Jones21) classified this target as ‘uncertain’, following their classification criteria.

[^8]: In this case, we use a pseudo-slight of 4” of length in order to cover all the $3\sigma$ emission from the velocity map.

[^9]: Some of the mergers found by (cite: LeFevre20) were also analyzed in terms of the tilted ring model fitting by (cite: Jones21) who found that the kinematic of those sources could be even compatible with rotating disks or dispersion dominated galaxies, or that the sensitivity and resolution of the data are too low for a conclusive classification (see Appendix [7](#app:mergers)).

[^10]: In the case the merging system is composed by more than two sources, we only consider the two major components in terms of their \[CII\] fluxes.

[^11]: Both in the main figure and in the inset we do not report the measure of the \[CII\] flux ratio for the merger $\mathrm{DC\_842313}$ (i.e., $\mu_{\mathrm{[CII]}}\sim33$). We also do not consider this source in the statistics described in the text because, as elaborated in Appendix [7](#app:mergers), this is a peculiar source.

[^12]: Although this is no more assured in case of major mergers or strong changes in star formation (e.g., (cite: Leja13; Ownsworth14)).

[^13]: When adopting the merger timescale by (cite: Jiang14), we just consider the $T_{\text{MM}}$ redshift evolution found in their work (i.e., $T_{\text{MM}}\sim H(z)^{-1/3}$) and normalize it to $T_{\text{MM}}(z=0)$ from (cite: Kitzbichler08). This is also similar to setting a constant merger timescale of $\sim1$ Gyr.

[^14]: It is worth noting that, as also stated by (cite: Snyder17) and (cite: Oleary21), the mass ratio defined by (cite: Rodriguez15) is evaluated at the time when the secondary galaxy has achieved its maximum stellar mass. This prevent us to make a direct comparison among the results of this and the other simulations.

[^15]: To convert SFRs from (cite: Salpeter55) to Chabrier IMF we multiply by 0.63 (e.g., (cite: Madau14)).

</paper>

Write the methods card for this paper.