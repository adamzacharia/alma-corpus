# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...988...19S\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025ApJ...988...19S",
 "title": "Detection of [O III]<SUB>88 μm</SUB> in JADES-GS-z14-0 at z = 14.1793",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Schouws, Sander",
 "n_authors": 16,
 "arxiv_id": "2409.20549",
 "doi": "10.3847/1538-4357/adbf1b",
 "alma_projects_linked_by_archive": [
  "2023.A.00037.S"
 ]
}
```

Paper text:
<paper>
# Detection of \[OIII\]$_{88\mu m}\,$in JADES-GS-z14-0 at z=14.1793

## Abstract

We report the first successful ALMA follow-up observations of a secure $z > 10$ JWST-selected galaxy, by robustly detecting ($6.6\sigma$) the \[OIII\]$_{88\mu m}\,$ line in JADES-GS-z14-0 (hereafter GS-z14). The ALMA detection yields a spectroscopic redshift of $z=14.1793\pm0.0007$, and increases the precision on the prior redshift measurement of $z=14.32_{-0.20}^{+0.08}$ from NIRSpec by $\gtrsim$180$\times$. Moreover, the redshift is consistent with that previously determined from a tentative detection ($3.6\sigma$) of CIII\]$_{1907,1909}$ ($z=14.178\pm0.013$), solidifying the redshift determination via multiple line detections. We measure a line luminosity of $L_\mathrm{[OIII]88} = (2.1 \pm 0.5)\times10^8\,L_\odot$, placing GS-z14 at the lower end, but within the scatter of, the local $L_\mathrm{[OIII]88}$-star formation rate relation. No dust continuum from GS-z14 is detected, suggesting an upper limit on the dust-to-stellar mass ratio of $< 2 \times 10^{-3}$, consistent with dust production from supernovae with a yield $y_d < 0.3\,M_\odot$. Combining a previous JWST/MIRI photometric measurement of the \[OIII\]$\lambda\lambda$4959,5007Å  and H$\beta$ lines with Cloudy models, we find GS-z14 to be surprisingly metal-enriched ($Z\sim0.05 - 0.2\,Z_\odot$) a mere $300\,\mathrm{Myr}$ after the Big Bang. The detection of a bright oxygen line in GS-z14 thus reinforces the notion that galaxies in the early Universe undergo rapid evolution.

# Introduction

The discovery and spectroscopic confirmation of galaxies at $z>10$ has recently become possible due to the groundbreaking capabilities offered by the James Webb Space Telescope (*JWST*) (cite: Curtis-Lake_2022; Robertson_2023; Bunker_2023; carniani2024; Finkelstein_2023; zavala2024). In particular JADES-GS-z14-0 (hereafter GS-z14) was recently spectroscopically confirmed to be the most distant known galaxy at $z_\mathrm{spec}= 14.32_{-0.20}^{+0.08}$, less than 300 Myr after the Big Bang (cite: carniani2024). Notably GS-z14 is also very luminous with $M_{UV}=-20.81\pm0.16$, which makes it the second most luminous $z>8$ galaxy with a spectroscopic redshift; only GN-z11 (cite: Oesch_2016; bunker2023) is more luminous by a factor $\sim$2$\times$.

Moreover, in contrast to other $z>10$ galaxies, the rest-frame UV morphology of GS-z14 is extended and not highly concentrated. This implies that the luminosity is dominated by a spatially extended stellar population as opposed to an active galactic nucleus (AGN). The existence of objects like GS-z14 suggests a much more rapid build-up of galaxies in the very early universe than previously expected (cite: carniani2024). GS-z14 enables a unique opportunity to study this rapid build-up in detail (cite: Ferrara2024a).

The high luminosity of GS-z14 makes it an exceptional target for multi-wavelength follow-up observations capable of revealing its physical conditions. Here we present new observations of GS-z14 targeting the luminous \[OIII\]$_{88\mu m}\,$far-infrared line with the the Atacama Large Millimeter/submillimeter Array (ALMA).

The \[OIII\] 88-micron fine-structure line is one of the dominant coolants of the ISM. It originates from ionized gas in HII regions (cite: Cormier2015), where ionizing radiation from young, massive stars has stripped electrons from oxygen atoms. Both semi-analytical models (cite: Yang_2020; vallini2021; vallini2024) and radiative transfer post-processed large box (cite: Moriwaki_2018), cosmological zoom-in (cite: katz2017; arata2020; katz2022; pallottini2022; kohandel2023; nakazato2023) hydrodynamical simulations have been employed to predict and interpret \[OIII\]$_{88\mu m}\,$emission in high redshift sources. The consensus is that bright \[OIII\]$_{88\mu m}\,$emission is generally associated with hard ionisation fields (cite: Yang_2020; pallottini2022), high ionization parameters (cite: Moriwaki_2018; arata2020; vallini2024; nakazato2023), and low metallicities (cite: Katz_2019; vallini2024). These physical properties are likely to be ubiquitous in very actively star-forming galaxies at high redshifts, making this line the ideal target for ALMA follow-up observations of JWST-selected $z>10$ galaxies.

In the last two years, ALMA follow-up observations have been performed for several high-redshift galaxy candidates. GHZ2 (cite: castellano2022; naidu2022; Donnan_2022; harikane2022; bouwens2023), with a photometric redshift of $z = 11.96-12.42$, was targeted with an ALMA Band 6 search for \[OIII\]$_{88\mu m}\,$by (cite: bakx2023), who determined a $5\sigma$ upper limit of $\log (L_{\rm [O III]} / L_\odot) < 1.7 \times 10^8$ (see also (cite: Popping_2023)). GHZ2 was later spectroscopically confirmed at $z=12.34$ (cite: castellano2024), with (cite: zavala2024) estimating an SFR of $9\pm3\,M_\odot\,\mathrm{yr}^{-1}$ from the H$\alpha$ line. Following its spectroscopic confirmation, (cite: zavala2024) re-examined the ALMA observations of GHZ2 presented in (cite: bakx2023), but were not able to identify a plausible $>$5$\sigma$ \[OIII\]$_{88\mu m}\,$detection at the expected frequency.

An ALMA line scan was also performed on GHZ1, with a photometric redshift of $z\approx10.6$ (cite: Treu_2023), SFR of $36.3^{+54.5}_{-26.8} \ M_{\odot} \ \mathrm{yr}^{-1}$ and stellar mass $\log (M_\star / M_\odot) = 9.1^{+0.3}_{-0.4}$ (cite: Santini_2023), yielding a marginal \[OIII\]$_{88\mu m}\,$signal near its JWST position (cite: Yoon_2023) and an upper limit of $L_{\rm [OIII]} < 2.2 \times 10^8 \ L_\odot$ (5$\sigma$). Another high-redshift candidate, HD1 at $z = 13.3$ (cite: Harikane_2023) was observed in ALMA Bands 4 and 6 targeting \[CII\]$_{158\mu m}$ and \[OIII\]$_{88\mu m}$, respectively, but the lines were not detected (cite: kaasinen2023). HD1 was later shown to be a low-redshift interloper at $z=4.0$ (cite: harikane2024). Finally, S5-z17-1, identified in JWST ERO data, showed a potential 5.1$\sigma$ detection at 338.726 GHz, possibly corresponding to \[OIII\]$_{52\mu m}$ at $z = 16$ (cite: Fujimoto_2022), suggesting an SFR $<$ 120 $M_\odot \ \mathrm{yr}^{-1}$. However, the high-redshift nature of this galaxy has not been conclusively established.

Overall, these upper limits and non-detections indicate possible lower redshift solutions or insufficient sensitivity in the requested observations (cite: bakx2023; Furlanetto_2023; kaasinen2023). However, the burstiness of SF in such high-redshift galaxies, as well as the impact of feedback processes on galaxy spectra and visibility, have also been suggested as physical motivations for the lack of ALMA detections at $z>10$ (cite: nakazato2023; kohandel2023).

Throughout this paper we assume a standard $\mathrm{\Lambda}$CDM cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_m=0.3$ and $\Omega_{\Lambda}=0.7$. Magnitudes are presented in the AB system (cite: oke_gunn_1983ApJ...266..713O). For star formation rates and stellar masses we adopt a Chabrier IMF (cite: chabrier2003). Error-bars indicate the $68\%$ confidence interval unless specified otherwise. All measured and derived physical quantities are corrected for gravitational lensing by a factor of 1.17$\times$ (cite: carniani2024). Logarithms use base 10 unless specified otherwise.

# Observations and Data-Reduction

## JWST

GS-z14 was discovered in deep imaging of the GOODS-South field obtained by the JWST Advanced Deep Extragalactic Survey (cite: Eisenstein_2023) and the First Reionization Epoch Spectroscopic COmplete Survey (cite: Oesch_2023). GS-z14 was initially flagged as a likely low redshift interloper (cite: Hainline_2023; Williams_2023) due to a nearby foreground galaxy at $z=3.475$ with a separation of only 0.4” and due to its high luminosity. However, further analysis including additional medium-band observations favored a high redshift solution (cite: Robertson_2023).

Deep follow-up spectroscopy with NIRSpec presented in (cite: carniani2024) shows a strong break at $\sim$1.85$\mu$m, consistent with a Lyman break at $z\sim14$. The profile of the Lyman break is sensitive to absorption of hydrogen along the line of sight, neutral gas in the galaxy and environment, velocity offsets, the presence of Lyman alpha emission and possible ionized bubbles. Accounting for these effects, (cite: carniani2024) determined a spectroscopic redshift of z = 14.32$^{+0.08}_{-0.20}$.

In contrast to other $z>10$ sources, the spectrum of GS-z14 does not contain strong rest-frame UV emission lines. Only CIII\]$\lambda\lambda$1907,9Å  is tentatively detected with a significance of 3.6$\sigma$ at $z=14.178\pm0.013$, consistent with the redshift obtained from the Lyman Break. (cite: carniani2024) discuss a number of mechanisms that could be responsible for the lack of strong emission lines in the rest-frame UV, ranging from a sudden quenching of the star formation, very low or high metallicities (Z$<$0.05Z$_{\odot}$ or Z$\sim$Z$_{\odot}$), a high escape fraction of ionizing photons and a difference in the dominant ionizing flux.

Interestingly, GS-z14 is also detected by MIRI in the F770W filter (cite: helton2024). This filter covers the rest-frame optical emission of GS-z14, corresponding to wavelengths of 4.4 to 5.7$\mu$m. This part of the spectrum contains the strong \[OIII\]$\lambda\lambda$4959,5007Å  and H$\mathrm{\beta}$  emission lines, and indeed the observed flux is significantly stronger than observed in the adjacent F444W filter, implying a significant contribution from the emission lines (constituting about $1/3$ of the total F770W flux).

SED fitting of GS-z14 performed by (cite: helton2024) shows that the photometry is consistent with a stellar mass of log(M$_{*}$/M$_{\odot}$)=$8.7_{-0.4}^{+0.5}$. The models estimate that most of this stellar mass was formed relatively recently, with a mass-weighted age of $\sim$20 Myr. (cite: helton2024) determine the current ($<10\,\mathrm{Myr}$) star formation rate of GS-z14 to be 25$^{+6}_{-5}$ M$_{\odot}$ yr$^{-1}$—consistent with the measurement of $22\pm6\,M_\odot$ yr$^{-1}$ from (cite: carniani2024). Combined with the measured size of 260$\pm$20 pc, this implies a high star formation rate surface density of $\sim$64 M$_{\odot}$ yr$^{-1}$ pc$^{-2}$, comparable to intense starbursting galaxies in the local universe (cite: Genzel_2010). The UV slope $\beta_{UV} =- 2.20 \pm 0.07$ indicates the presence of a moderate amount of dust in addition to the very young stellar population, with a visual extinction of A$_{V}$=0.31$^{+0.14}_{-0.07}$ (cite: carniani2024). Finally, the metallicity is poorly constrained owing to a lack of detected emission lines but is expected to be low (Z = 0.014$^{+0.052}_{-0.012}$ Z$_{\odot}$; (cite: carniani2024)).

## ALMA

The ALMA Band 6 follow-up observations targeting the \[OIII\]$_{88\mu m}\,$line were obtained as part of a Cycle 10 Director’s Discretionary Time (DDT) program (#2023.A.00037.S, PI: Schouws). An observing set-up using two tunings with three spectral windows each was utilized to maximize the coverage of the redshift likelihood distribution derived from the spectroscopic Lyman break. This results in a continuous frequency coverage ranging from 218.70 GHZ to 229.45 GHz, corresponding to a redshift range of $z=13.79$ to 14.51. We show in Figure [1](#fig:scan) that the observing strategy covers 98% of the P(z).

The observations for Tuning 2 were carried out between 15 and 16 August 2024 in good weather conditions (PWV=0.67mm), achieving the requested sensitivity in 2.8 hours. Tuning 1 was observed between 7 and 8 September 2024 for 2.8 hours in excellent conditions (PWV=0.30mm). Both tunings were observed with different array configurations due to scheduling constraints. Tuning 1 was observed in C-4 and Tuning 2 in C-5 with baselines of 15$-$500 and 15$-$919 m, resulting in synthesized beams of $1.09''\times 0.81''$ and $0.57''\times 0.49''$ respectively when using natural weighting.

The ALMA data were reduced and calibrated following the standard ALMA pipeline procedures with the Common Astronomy Software Applications (v6.5.4-9) (cite: Hunter_2023). The amplitude and phase calibrations were performed using J0334-4008 and J0348-2749, respectively. Both calibrators are part of the ALMA Calibrator Source Catalogue and are therefore considered reliable for Band 6 observations. Under typical conditions, the absolute flux calibration accuracy for Band 6 is 5–10% (cite: ALMA_Tech_Handbook_C10). The data were well behaved, with no bad antennas or channels requiring flagging.

The resulting calibrated measurement sets were time-averaged in bins of 30 seconds to reduce the data-size, after carefully verifying that time-average smearing does not impact our results (cite: thompson2017).

Imaging of the calibrated visibilities was performed with natural weighting using the TCLEAN task in CASA, cleaning to a depth of 2$\sigma$ using automasking (cite: kepley2020). We use a pixel scale of 0.076$''$ to properly sample the synthesized beam, which has a FWHM of $1.08''\times 0.80''$ at the frequency of the \[OIII\]$_{88\mu m}\,$line.

## Line Search

We perform a blind search for emission lines using an algorithm similar to the one used by (cite: bethermin2020) for the ALPINE survey (cite: lefevre2020; faisst2020) and Schouws et al. in prep. for the REBELS survey (cite: bouwens2022). The algorithm loops over all channels and collapses moment maps over a range of 75 to 350 km s$^{-1}$ in steps of 1 channel ($\sim$10 km s$^{-1}$). For each moment map, we identify the significant ($>$3$\sigma$) peaks and add the results to a large list of features. This list is then pruned by removing duplicates within 2$\times$FWHM and 1.5$\times$ the beamsize. We also perform the search on the negative moment map, which is useful to characterize the noise properties. In Figure [1](#fig:scan), we show a blind extraction of the ALMA spectrum at the location of GS-z14 using a 0.5" aperture.

The most significant line candidate we extract within a 0.5" radius of the JWST position of GS-z14 is detected with a peak significance of 6.6$\sigma$ and separation of 0.12". The candidate line is consistent with being spatially coincident with GS-z14 in the JWST/NIRCam observations given expected 0.18" positional uncertainties following from a 6.6$\sigma$ line detection and 1.08$"$ beam.[^1]

# Results

## \[OIII\]$_{88\mu m}\,$in GS-z14

We have identified an emission line with a signal-to-noise of $6.6\sigma$ within $0.12''$ of GS-z14 at 223.528$\pm$0.009 GHz. This corresponds to \[OIII\]$_{88\mu m}\,$at $z=14.1793\pm0.0007$, consistent with both the redshift derived from the Lyman break observed by JWST and also the tentative 3.6$\sigma$ detection of CIII\]$_{1907,1909}$ at 2.89$\mu$m (cite: carniani2024). In particular, the consistency of our new redshift determination from \[OIII\]$_{88\mu m}\,$$\,$ with the earlier redshift estimate $z=14.178\pm0.003$ from the tentative CIII\]$_{1907,1909}$ doublet (cite: carniani2024) greatly increases our confidence in the robustness of the current redshift determination given the availability of multiple line detections. We show the contours of the \[OIII\]$_{88\mu m}\,$emission overlaid on an RGB image based on F150W, F200W and F400W imaging and a S/N-optimized extraction of the spectrum in Figure [2](#fig:detail).

We measure the integrated line flux using the moment-zero map of the emission line, including all channels that fall within 2$\times$ the FWHM of the line. The FWHM is determined in an iterative process; starting from an estimate of the FWHM we collapse a moment-zero map and extract a 1d spectrum, which is extracted by including all pixels with S/N$>$3$\sigma$ on the moment-zero map. A new FWHM is then measured using this 1d spectrum by fitting a Gaussian. This new FWHM is then used to collapse a new moment-zero map for the next iteration. A stable FWHM is achieved in less than 10 steps (cite: schouws2022).

The final FWHM we measure is 136$\pm$31 km s$^{-1}$. Assuming that GS-z14 is dispersion-dominated and r$_\mathrm{[OIII]}$ = r$_e$ = 260 pc, this implies a dynamical mass of (1.0$\pm$0.5)$\times$10$^9$ M$_{\odot}(\mathrm{sin}\, i)^2$. At the current resolution we do not see evidence for a velocity gradient.

We measure an integrated flux of 39$\pm$10 mJy$\cdot$km s$^{-1}$ this corresponds to a \[OIII\]$_{88\mu m}\,$luminosity of $(2.1\pm0.5)\times10^8\,$L$_{\odot}$ (cite: Solomon_1992) (after correction for lensing magnification; (cite: carniani2024)). This places GS-z14 a factor of $\sim2\times$ below the local relation between L$_\mathrm{[OIII]}$ and SFR for metal-poor dwarf galaxies from (cite: delooze2014), albeit nearly within the scatter (Figure [3](#fig:OIII-sfr)). The general consistency with the $z=0$ relation for a galaxy a mere $\sim300\,$Myr after the Big Bang suggests that GS-z14 has undergone rapid evolution, as discussed in detail in Section [4.1](#sec:ism_constraints).

## Dust Continuum

We do not detect the dust continuum from GS-z14, with a formal 90$\mu$m continuum limit of $< 15.1\,\mu\mathrm{Jy\,beam}^{-1}$ (3$\sigma$). We provide an upper limit on its dust mass assuming an optically thin modified black body with a dust temperature of $T_\mathrm{d} = 60\,\mathrm{K}$ and $\beta_\mathrm{IR} = 2.03$ for the dust SED. The assumed temperature is consistent with extrapolations from theoretical models (e.g., (cite: liang2019; sommovigo2022)) and observational trends (e.g., (cite: schreiber2018; faisst2020_tdust; sommovigo2021; sommovigo2022; sommovigo2022b; Witstok23_dust)) to $z\approx14$. We note that the precise evolution of dust temperature is still uncertain and debated (cite: sommovigo2022b). However, our assumption of a relatively high dust temperature is also supported by the inverse correlation between metallically and dust temperature noted by (cite: sommovigo2022b) and increasing temperature of the CMB background at high redshift[^2].

We follow (cite: Ferrara2024b) by adopting the (cite: weingartner2001) dust model with $\kappa_{88} = 34.15\,\mathrm{cm}^{-2}\,\mathrm{g}^{-1}$ at rest-frame $88\,\mu\mathrm{m}$. This yields a (lensing-corrected) upper limit on the dust mass and infrared luminosity (integrated across $8-1000\,\mu\mathrm{m}$) of $\log(M_\mathrm{d} / M_\odot) < 6.0$ and $\log(L_\mathrm{IR} / L_\odot) < 11.1$, respectively. The latter corresponds to an obscured SFR of $\mathrm{SFR}_\mathrm{IR} < 14\,M_\odot\,\mathrm{yr}^{-1}$ which, combined with the unobscured SFR of GS-z14 inferred by (cite: carniani2024), implies an obscured fraction of $f_\mathrm{obs} < 0.66$. Finally, using the stellar mass of GS-z14 inferred by (cite: helton2024), we infer a dust-to-stellar mass ratio $\xi_d \equiv M_\mathrm{d} / M_\star < 1.9 \times 10^{-3}$.

The above estimates require the assumption of a dust temperature. Assuming a lower temperature of $T_\mathrm{d} = 45\,\mathrm{K}$, which would imply no significant evolution of the dust temperature from $z\sim4$ (cite: faisst2020_tdust), results in a dust mass of $\log(M_\mathrm{d} / M_\odot) < 6.8$. Meanwhile, a significantly higher temperature temperature of $T_\mathrm{d} = 100\,\mathrm{K}$ would result in a dust mass of $\log(M_\mathrm{d} / M_\odot) < 5.3$. In Section [4.2](#sec:dust_formation), we discuss this in further detail, focusing on the Attenuation Free Model by (cite: Ferrara2024b) which self-consistently predicts a dust temperature for GS-z14 based on the observed V-band attenuation and the spatial extent of the dust.

# Discussion

## Constraints on the ISM of GS-z14

Luminosity ratios of emission lines are invaluable diagnostic tools to probe the conditions of the ISM in galaxies. Although the NIRSpec spectroscopy of GS-z14 does not show significant emission lines, its detection in the MIRI F770W band places a constraint on the combined \[OIII\]$\lambda\lambda$4959,5007Å+H$\mathrm{\beta}$  flux. Following (cite: helton2024) we assume that the flux excess in F770W is 27.5$\pm$5.6 nJy based on a flat underlying continuum emission.

The \[OIII\]$\lambda$5007Å  luminosity (hereafter \[OIII\]) can subsequently be calculated based on an assumed \[OIII\]/H$\mathrm{\beta}$  ratio and be compared to the luminosity of OIII as measured by ALMA. We repeat this calculation 10$^6\times$, drawing random \[OIII\]/H$\mathrm{\beta}$  ratios from probability distribution from the SED fitting by (cite: helton2024), where we combine the probability distributions from the three star formation history assumptions. This distribution has a median ratio of 2.5$^{+0.9}_{-0.6}$. As noted by (cite: helton2024), this is lower than the median \[OIII\]/H$\mathrm{\beta}$  at $z\sim8.0$ which is 6.0$^{+2.4}_{-2.9}$ in JADES (cite: helton2024), 6.4$\pm$0.9 in FRESCO (cite: meyer2024) and 7.2$^{+2.6}_{-2.4}$ in PRIMAL (cite: Heintz2025).

In this process we also account for the uncertainty in the line luminosities from ALMA and JWST by drawing random values from a Gaussian error distribution.

The resulting constraints on the \[OIII\]/\[OIII\]$_{88\mu m}\,$  versus \[OIII\]/H$\mathrm{\beta}$  line ratios are shown in Figure [4](#fig:ISM). For context we show a grid of ISM models for a large range of conditions based on Cloudy models (cite: ferland2017). The models consist of an HII region that smoothly transitions to a Photo Dissociation Region (PDR) until a fixed optical depth (A$_V$=10) in a plane parallel geometry. For more details on the model we refer to (cite: Witstok_2022). We note that the ionization parameter of GS-z14 has been loosely constrained by (cite: helton2024) to be $\log(U_\mathrm{ion}) = -2.5 \pm 0.5$, and we therefore show two sets of Cloudy models bracketing this range, at a fixed $\log(U_\mathrm{ion}) \in (-3.0, -2.0)$. We focus on the grid with an ionization parameter $\log(U_\mathrm{ion}) = -2$, as (cite: kohandel2023) predict the most \[OIII\]$_{88\mu m}\,$-luminous galaxies at $z \gtrsim 10$ have high ionization parameters. Moreover, if the assumed \[OIII\]/H$\mathrm{\beta}$  is underestimated, the observed line ratios can only be reproduced by higher values of the ionization parameter.

While the uncertainties are substantial, given the existence of only a photometric detection of the \[OIII\]$\lambda\lambda$4959,5007Å  line, the (cite: Witstok_2022) models suggest a relatively high metallicity of $Z \sim 0.1\,Z_\odot$, in combination with a moderate-to-low electron density ($\log N \lesssim 10^{2.5}$). This is on the low end of, albeit still consistent with, the distribution of electron densities found for $z\gtrsim5$ galaxies, which typically show values of $\log(N) \sim 2 - 3$ (e.g., (cite: isobe2023)). However, for more accurate constraints on the ISM conditions of GS-z14, direct spectroscopic detections of additional oxygen lines are crucial, for example through MIRI spectroscopy.

Intriguingly, the detection of \[OIII\]$_{88\mu m}\,$at $z=14.1793\pm0.0007$ is consistent within 1$\sigma$ with the tentative detection of CIII\]$\lambda\lambda$1907,9Å$\,$ reported by (cite: carniani2024) at $z=14.178\pm0.013$. (cite: carniani2024) derive a CIII\]$\lambda\lambda$1907,9Å$\,$ rest-frame equivalent width (EW$_0$) of 8.0$\pm$2.3 Å, which is relatively high compared to the EW$_0$(\[OIII\]+H$\mathrm{\beta}$) of 370$^{+360}_{-130}$ Å$\,$ estimated by (cite: helton2024), albeit consistent with the distribution found for galaxies at $z\sim0-4$ (cite: Maseda2017; Ravindranath_2020; Tang2021), see Figure [5](#fig:OIII_CIII_EW). The measured equivalent widths are in agreement with predictions from Cloudy at a metallicity of $Z\sim0.05-0.2\,Z_\odot$, and with an ionization parameter of $\log(U) \sim -2.5$, in agreement with (cite: helton2024).

Moreover, (cite: JonesTucker2020) derive a calibration for the oxygen abundance using the \[OIII\]$_{88\mu m}\,$ line and star-formation rate. Using their calibration we derive 12 + $\log{\rm O^{++}/H^+}$=7.66$_{- 0.21}^{+0.19}$ ($\sim$6-14% solar metallicity, using the solar abundance from (cite: asplund2009)). In Figure [6](#fig:loiii_sfr) we use a Cloudy grid with a 1Myr old input stellar population to estimate the \[OIII\]$_{88\mu m}\,$/SFR ratio as a function of ionisation parameter, for models with different metallicity and gas density. For modest gas density the measurements are consistent with 10% solar oxygen abundance, however, higher gas densities or older ages for the input stellar population will give higher metallicity estimates (up to solar metallicity).

The detection of both carbon and oxygen lines thus reinforce the notion that GS-z14 is already moderately chemically enriched. Adopting a fiducial $Z\sim0.05 - 0.2\,Z_\odot$ in combination with the stellar mass from (cite: helton2024), GS-z14 falls onto the high-redshift mass-metallicity relation, which has been mapped out to $z\sim10$, and appears to show only mild evolution beyond $z\gtrsim 3$ (e.g., (cite: curti2024)).

## Constraints on Dust Formation Processes

The build-up of dust in galaxies is a complex process involving multiple mechanisms of dust production and destruction, operating on different timescales. Supernova explosions (SNe) produce dust quickly, on timescales similar to the lifecycle of massive stars ($\sim$10 Myr), whilst Asymptotic Giant Branch (AGB) stars contribute to dust production on significantly longer timescales ($\sim$300 Myr, (cite: schneider2024)). The contribution from grain growth in the ISM depends on the physical conditions, but is expected to be sub-dominant at extremely high redshifts and low gas-phase metallicities (cite: ferrara2016; Dayal_2022; Witstok23_dust; Markov_2024).

At lower redshifts it is difficult to disentangle the impact of different contributions (e.g., (cite: delooze2020; galliano2021)), but GS-z14 has formed sufficiently early in cosmic history that dust production through SNe is likely the dominant formation process. This makes GS-z14 an ideal test-bed for dust formation models in the early universe.

The efficiency of dust production from SNe can be inferred by measuring the dust-to-stellar mass ratio ($\xi_d$). This parameter is hard to interpret as it depends on both the expected number of SNe per unit of formed stellar mass ($\nu$), which in turn depends on the assumed Initial Mass Function (IMF), and on the net dust yield per SN event ($y_d$), $\xi_d = y_d \times \nu$. In local SN remnants $y_d$ values varying in the wide range from 0.01 to 1.1 M$_{\odot}$ have been directly measured (cite: Milisavljevic_2024). Such values are broadly in agreement with most indirect high-z measurements based on dust-to-stellar mass ratios (cite: sommovigo2022; sommovigo2022b).

Utilizing the continuum non-detection of GS-z14, we can attempt to place an upper limit on $y_d$. Following (cite: michalowski2015) and adopting a Salpeter IMF, the limit of $\xi_d < 2 \times 10^{-3}$ suggests a yield of $y_d < 0.24\,M_\odot/$SN. This is consistent with a commonly adopted yield of $y_d\sim0.1\,M_\odot$/SN (e.g., (cite: sommovigo2022; dayal2022)).

If we rely on such a value for $y_d\sim0.1\,M_\odot$/SN and assume that dust follows a similar spatial distribution as the stellar component, GS-z14 should be largely obscured (A$_{V}$$\sim$9.5, see also (cite: Ferrara2024b)) and would not have been detected with JWST. However, the JWST data only reveal a relatively low visual extinction of A$_V$=0.31, implying a much (1 dex) lower dust mass of 5$\times$10$^4$ M$_{\odot}$ with $\xi_d$ $<$ 10$^{-4}$ and $y_d < 0.015\,M_\odot/$SN (cite: Ferrara2024b).

Clearly, SNe (and later on growth in the ISM) do produce tangible amounts of dust, as less than $500\,\mathrm{Myr}$ later, at $z\approx7$, dust appears widespread (cite: inami2022; Schouws_2022; Witstok23_dust; algera2023) – both puzzlingly high dust-to-stellar mass ratios ($M_{\rm d}/M_{\star}\sim 0.01$; (cite: algera2024)) and fully dust-obscured sources (cite: fudamoto2021) are observed at this epoch. In addition, features of the attenuation curve associated with the carbonaceous dust grains produced by SNe are observed at $z\sim 6.7$ (cite: Witstok2023_JWST).

The discrepancy between what is observed by JWST versus what is expected based on dust production from past SNe can be resolved by assuming that the majority of the dust has been removed from star-forming regions by radiation pressure-driven outflows. Such a scenario had been suggested in the Attenuation Free Model (AFM) presented in (cite: Ferrara2024b).

In their fiducial model, (cite: Ferrara2024b) suggest the dust in GS-z14 to have a typical extent of $1.4\,\mathrm{kpc}$, as a more compact size would be inconsistent with the visual extinction measured by JWST. We note that, given the resolution of our data, dust of this extent would not be resolved across multiple ALMA beams. Combined with a fiducial yield of $0.1\,M_\odot$/SN, the AFM predicts a continuum flux density for GS-z14 of $F_{88} = 14.9\,\mu\mathrm{Jy}$. This is just below the sensitivity limit of our observations, which yield an upper limit of $F_{88} < 15.1\,\mu\mathrm{Jy\,beam}^{-1}$. However, if the assumed dust yield is 0.5 dex lower ($0.1\,M_\odot$/SN), then the expected flux density would be $F_{88} \sim 8\,\mu\mathrm{Jy}$, well below the current limit. As such, a conclusive investigation of the dust content of GS-z14, as well as further testing of the AFM model predictions, requires deeper and high-resolution ALMA continuum observations.

| **Parameter** | **Value** |
|:---|:---|
| RA | 03:32:19.9049 |
| Dec | $-$27:51:20.265 |
| Redshift | $z=14.1793(7)$ |
| M$_{UV}$ | $-20.81\pm0.16$ |
| Stellar Mass ($\log(M_\odot)$) | $8.7_{-0.4}^{+0.5}$ |
| Star Formation Rate (M$_{\odot}$/yr) | $25_{-5}^{+6}$ |
| $_{88\mu m}\,$Luminosity ($10^8\,$L$_{\odot}$) | 2.1$\pm$0.5 |
| FWHM \[OIII\]$_{88\mu m}\,$(km s$^{-1}$) | 136$\pm$31 |
| Dynamical Mass (M$_{\odot}$ ($\mathrm{sin}\, i)^2$) | (1.0$\pm$0.5)$\times$10$^9$ |
| 90-$\mu$m continuum flux ($\mu$Jy/beam) | $<15.1$ ($3\sigma$) |
| Dust Mass ($\log(M_\odot)$) | $<6.0$ |

: Properties of GS-z14

*Notes:* $M_\mathrm{UV}$ from (cite: carniani2024); stellar mass and SFR from (cite: helton2024). Values have been corrected for a lensing magnification of 1.17$\times$ (cite: carniani2024).

# Summary

We report the robust detection of a 6.6$\sigma$ \[OIII\]$_{88\mu m}\,$ line of JADES-GS-z14-0 at 223.528$\pm$0.009 GHz, providing us with a precise spectroscopic redshift measurement of $z=14.1793\pm0.0007$. This represents a substantial jump in redshift over the previous high-redshift \[OIII\]$_{88\mu m}\,$-detection from MACS1149-JD1 at $z=9.1096$ (cite: hashimoto2018). The \[OIII\]$_{88\mu m}\,$line was identified using data from an ALMA Cycle-10 DDT program (2023.A.00037.S, PI: Schouws) providing a spectral scan from 218.70 to 229.45 GHz (10.75 GHz baseline), covering the redshift range z=13.79 to 14.51. The precision of the current redshift measurement represents $\gtrsim180$$\times$ gain over the prior redshift measurement of $z=14.32_{-0.20}^{+0.08}$ from NIRSpec.

The redshift we find for the source is consistent with the redshift (cite: carniani2024) derive ($z=14.178\pm0.013$) based on their tentative 3.6$\sigma$ detection of CIII\]$_{1907,1909}$ doublet at 2.89$\mu$m, providing strong evidence the earlier line detection is real. As such, we now have multiple line detections of GS-z14-0, CIII\]$_{1907,1909}$ (3.6$\sigma$) with JWST and \[OIII\]$_{88\mu m}\,$$\,$ (6.6$\sigma$) with ALMA, providing rather definitive evidence for the robustness of the redshift determination of GS-z14-0. Of note, the detection of \[OIII\]$_{88\mu m}\,$$\,$ with ALMA was achieved with less integration time (2.8 hours) than was required for the 3.6$\sigma$ tentative detection of CIII\]$_{1907,1909}$ with JWST (9.3 hours), providing a rather dramatic illustration of the discovery potential of ALMA.

We find no detection of the dust continuum from JADES-GS-z14-0 based on the DDT observations, with a $<$ $3\sigma$ upper limit of $<$15.1$\,\mu$Jy beam$^{-1}$. This suggests a low dust-to-stellar mass ratio of $M_\mathrm{d}/M_\star < 1.9 \times 10^{-3}$, consistent with supernova dust production yields $y_d < 0.24\,M_\odot$/SN.

Combining a previous JWST/MIRI photometric measurement of the \[OIII\]$\lambda\lambda$4959,5007Å  and H$\beta$ lines with Cloudy models, we find GS-z14 to be surprisingly metal-enriched ($Z\sim 0.05$-0.2 Z$_{\odot}$) a mere 300 Myr after the Big Bang, with moderate to low density $\log(N) < 3.0\,\textrm{cm}^{-3}$.

Thanks to the precise spectroscopic redshift measurement and \[OIII\]$_{88\mu m}\,$line detection we now have for GS-14-0 using just 2.8 hours, it is clear that additional follow-up of GS-z14-0 with ALMA would be highly fruitful and should include (1) higher spatial resolution observations of \[OIII\]$_{88\mu m}\,$to improve constraints on dynamical masses and state of GS-z14-0 and deeper constraints on the dust continuum, (2) observations of the \[CII\]$_{158\mu m}$ line in band 4, lying just 0.2 GHz above the low-frequency boundary, to better probe the ionization parameter $U$ and build-up of metals, and (3) JWST/MIRI observations of \[OIII\]$\lambda\lambda$4959,5007Å  and H$\mathrm{\beta}$  to place tighter constraints on the electron density and metallicity of GS-z14-0.

## Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA 2023.A.00037.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We are greatly appreciative to our ALMA program coordinator Violette Impellizzeri for support with our ALMA program and Allegro, the European ALMA Regional Center node in the Netherlands. We are grateful to J. Witstok for providing the Cloudy models from (cite: Witstok_2022) for the analysis conducted in this paper. We thank M. Kohandel and A. Pallottini for simulated data analysis. This work was supported by NAOJ ALMA Scientific Research Grant Code 2021-19A (HA). AF acknowledges support from the ERC Advanced Grant INTERSTELLAR H2020/740120 and support from the grant NSF PHY-2309135 to the Kavli Institute for Theoretical Physics (KITP). 

natexlab

(ref: akins2022) Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64, doi: [`10.3847/1538-4357/ac795b`](http://doi.org/10.3847/1538-4357/ac795b)

(ref: algera2023) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142, doi: [`10.1093/mnras/stac3195`](http://doi.org/10.1093/mnras/stac3195)

(ref: algera2024) Algera, H. S. B., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 6867, doi: [`10.1093/mnras/stad3111`](http://doi.org/10.1093/mnras/stad3111)

(ref: ALMA_Tech_Handbook_C10) ALMA Technical Handbook. 2024, ALMA Cycle 10 Technical Handbook, ALMA Observatory

(ref: arata2020) Arata, S., Yajima, H., Nagamine, K., Abe, M., & Khochfar, S. 2020, MNRAS, 498, 5541, doi: [`10.1093/mnras/staa2809`](http://doi.org/10.1093/mnras/staa2809)

(ref: asplund2009) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481, doi: [`10.1146/annurev.astro.46.060407.145222`](http://doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: bakx2020) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294, doi: [`10.1093/mnras/staa509`](http://doi.org/10.1093/mnras/staa509)

(ref: bakx2023) Bakx, T. J. L. C., Zavala, J. A., Mitsuhashi, I., et al. 2023, MNRAS, 519, 5076, doi: [`10.1093/mnras/stac3723`](http://doi.org/10.1093/mnras/stac3723)

(ref: bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2, doi: [`10.1051/0004-6361/202037649`](http://doi.org/10.1051/0004-6361/202037649)

(ref: bouwens2023) Bouwens, R., Illingworth, G., Oesch, P., et al. 2023, MNRAS, 523, 1009, doi: [`10.1093/mnras/stad1014`](http://doi.org/10.1093/mnras/stad1014)

(ref: bouwens2022) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160, doi: [`10.3847/1538-4357/ac5a4a`](http://doi.org/10.3847/1538-4357/ac5a4a)

(ref: Bunker_2023) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, Astronomy & Astrophysics, 677, A88, doi: [`10.1051/0004-6361/202346159`](http://doi.org/10.1051/0004-6361/202346159)

(ref: bunker2023) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, A&A, 677, A88, doi: [`10.1051/0004-6361/202346159`](http://doi.org/10.1051/0004-6361/202346159)

(ref: carniani2020) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136, doi: [`10.1093/mnras/staa3178`](http://doi.org/10.1093/mnras/staa3178)

(ref: carniani2024) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024, Nature, 633, 318, doi: [`10.1038/s41586-024-07860-9`](http://doi.org/10.1038/s41586-024-07860-9)

(ref: castellano2022) Castellano, M., Fontana, A., Treu, T., et al. 2022, ApJL, 938, L15, doi: [`10.3847/2041-8213/ac94d0`](http://doi.org/10.3847/2041-8213/ac94d0)

(ref: castellano2024) Castellano, M., Napolitano, L., Fontana, A., et al. 2024, ApJ, 972, 143, doi: [`10.3847/1538-4357/ad5f88`](http://doi.org/10.3847/1538-4357/ad5f88)

(ref: chabrier2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Cormier2015) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, A&A, 578, A53, doi: [`10.1051/0004-6361/201425207`](http://doi.org/10.1051/0004-6361/201425207)

(ref: curti2024) Curti, M., Maiolino, R., Curtis-Lake, E., et al. 2024, A&A, 684, A75, doi: [`10.1051/0004-6361/202346698`](http://doi.org/10.1051/0004-6361/202346698)

(ref: Curtis-Lake_2022) Curtis-Lake, E., Carniani, S., Cameron, A., et al. 2023, Nature Astronomy, 7, 622, doi: [`10.1038/s41550-023-01918-w`](http://doi.org/10.1038/s41550-023-01918-w)

(ref: Dayal_2022) Dayal, P., Ferrara, A., Sommovigo, L., et al. 2022, Monthly Notices of the Royal Astronomical Society, 512, 989–1002, doi: [`10.1093/mnras/stac537`](http://doi.org/10.1093/mnras/stac537)

(ref: dayal2022) Dayal, P., Ferrara, A., Sommovigo, L., et al. 2022, MNRAS, 512, 989, doi: [`10.1093/mnras/stac537`](http://doi.org/10.1093/mnras/stac537)

(ref: delooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62, doi: [`10.1051/0004-6361/201322489`](http://doi.org/10.1051/0004-6361/201322489)

(ref: delooze2020) De Looze, I., Lamperti, I., Saintonge, A., et al. 2020, MNRAS, 496, 3668, doi: [`10.1093/mnras/staa1496`](http://doi.org/10.1093/mnras/staa1496)

(ref: Donnan_2022) Donnan, C. T., McLeod, D. J., Dunlop, J. S., et al. 2022, Monthly Notices of the Royal Astronomical Society, 518, 6011–6040, doi: [`10.1093/mnras/stac3472`](http://doi.org/10.1093/mnras/stac3472)

(ref: Eisenstein_2023) Eisenstein, D. J., Willott, C., Alberts, S., et al. 2023a, arXiv e-prints, arXiv:2306.02465, doi: [`10.48550/arXiv.2306.02465`](http://doi.org/10.48550/arXiv.2306.02465)

(ref: Eisenstein_2023_JOF) Eisenstein, D. J., Johnson, B. D., Robertson, B., et al. 2023b, arXiv e-prints, arXiv:2310.12340, doi: [`10.48550/arXiv.2310.12340`](http://doi.org/10.48550/arXiv.2310.12340)

(ref: faisst2020_tdust) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, Monthly Notices of the Royal Astronomical Society, 498, 4192, doi: [`10.1093/mnras/staa2545`](http://doi.org/10.1093/mnras/staa2545)

(ref: faisst2020) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61, doi: [`10.3847/1538-4365/ab7ccd`](http://doi.org/10.3847/1538-4365/ab7ccd)

(ref: ferland2017) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385. [`https://arxiv.org/abs/1705.10877`](https://arxiv.org/abs/1705.10877)

(ref: Ferrara2024a) Ferrara, A. 2024, A&A, 689, A310, doi: [`10.1051/0004-6361/202450944`](http://doi.org/10.1051/0004-6361/202450944)

(ref: Ferrara2024b) Ferrara, A., Carniani, S., di Mascia, F., et al. 2024. [`https://arxiv.org/abs/2409.17223`](https://arxiv.org/abs/2409.17223)

(ref: ferrara2016) Ferrara, A., Viti, S., & Ceccarelli, C. 2016, MNRAS, 463, L112, doi: [`10.1093/mnrasl/slw165`](http://doi.org/10.1093/mnrasl/slw165)

(ref: Finkelstein_2023) Finkelstein, S. L., Leung, G. C. K., Bagley, M. B., et al. 2024, ApJL, 969, L2, doi: [`10.3847/2041-8213/ad4495`](http://doi.org/10.3847/2041-8213/ad4495)

(ref: fudamoto2021) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489, doi: [`10.1038/s41586-021-03846-z`](http://doi.org/10.1038/s41586-021-03846-z)

(ref: Fujimoto_2022) Fujimoto, S., Finkelstein, S. L., Burgarella, D., et al. 2023, ApJ, 955, 130, doi: [`10.3847/1538-4357/aceb67`](http://doi.org/10.3847/1538-4357/aceb67)

(ref: fujimoto2024a) Fujimoto, S., Ouchi, M., Nakajima, K., et al. 2024, ApJ, 964, 146, doi: [`10.3847/1538-4357/ad235c`](http://doi.org/10.3847/1538-4357/ad235c)

(ref: Furlanetto_2023) Furlanetto, S. R., & Mirocha, J. 2023, Monthly Notices of the Royal Astronomical Society, 523, 5274–5279, doi: [`10.1093/mnras/stad1799`](http://doi.org/10.1093/mnras/stad1799)

(ref: galliano2021) Galliano, F., Nersesian, A., Bianchi, S., et al. 2021, A&A, 649, A18, doi: [`10.1051/0004-6361/202039701`](http://doi.org/10.1051/0004-6361/202039701)

(ref: Genzel_2010) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, Monthly Notices of the Royal Astronomical Society, 407, 2091–2108, doi: [`10.1111/j.1365-2966.2010.16969.x`](http://doi.org/10.1111/j.1365-2966.2010.16969.x)

(ref: Hainline_2023) Hainline, K. N., Johnson, B. D., Robertson, B., et al. 2024, ApJ, 964, 71, doi: [`10.3847/1538-4357/ad1ee4`](http://doi.org/10.3847/1538-4357/ad1ee4)

(ref: harikane2020) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93, doi: [`10.3847/1538-4357/ab94bd`](http://doi.org/10.3847/1538-4357/ab94bd)

(ref: harikane2022) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, ApJS, 265, 5, doi: [`10.3847/1538-4365/acaaa9`](http://doi.org/10.3847/1538-4365/acaaa9)

(ref: Harikane_2023) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, The Astrophysical Journal Supplement Series, 265, 5, doi: [`10.3847/1538-4365/acaaa9`](http://doi.org/10.3847/1538-4365/acaaa9)

(ref: harikane2024) Harikane, Y., Inoue, A. K., Ellis, R. S., et al. 2024, arXiv e-prints, arXiv:2406.18352, doi: [`10.48550/arXiv.2406.18352`](http://doi.org/10.48550/arXiv.2406.18352)

(ref: hashimoto2018) Hashimoto, T., Laporte, N., Mawatari, K., et al. 2018, Nature, 557, 392, doi: [`10.1038/s41586-018-0117-z`](http://doi.org/10.1038/s41586-018-0117-z)

(ref: Heintz2025) Heintz, K. E., Brammer, G. B., Watson, D., et al. 2025, A&A, 693, A60, doi: [`10.1051/0004-6361/202450243`](http://doi.org/10.1051/0004-6361/202450243)

(ref: helton2024) Helton, J. M., Rieke, G. H., Alberts, S., et al. 2024. [`https://arxiv.org/abs/2405.18462`](https://arxiv.org/abs/2405.18462)

(ref: Hunter_2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, Publications of the Astronomical Society of the Pacific, 135, 074501, doi: [`10.1088/1538-3873/ace216`](http://doi.org/10.1088/1538-3873/ace216)

(ref: inami2022) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126, doi: [`10.1093/mnras/stac1779`](http://doi.org/10.1093/mnras/stac1779)

(ref: isobe2023) Isobe, Y., Ouchi, M., Nakajima, K., et al. 2023, ApJ, 956, 139, doi: [`10.3847/1538-4357/acf376`](http://doi.org/10.3847/1538-4357/acf376)

(ref: JonesTucker2020) Jones, T., Sanders, R., Roberts-Borsani, G., et al. 2020, ApJ, 903, 150, doi: [`10.3847/1538-4357/abb943`](http://doi.org/10.3847/1538-4357/abb943)

(ref: kaasinen2023) Kaasinen, M., van Marrewijk, J., Popping, G., et al. 2023, A&A, 671, A29, doi: [`10.1051/0004-6361/202245093`](http://doi.org/10.1051/0004-6361/202245093)

(ref: katz2017) Katz, H., Kimm, T., Sijacki, D., & Haehnelt, M. G. 2017, MNRAS, 468, 4831, doi: [`10.1093/mnras/stx608`](http://doi.org/10.1093/mnras/stx608)

(ref: Katz_2019) Katz, H., Galligan, T. P., Kimm, T., et al. 2019, Monthly Notices of the Royal Astronomical Society, 487, 5902–5921, doi: [`10.1093/mnras/stz1672`](http://doi.org/10.1093/mnras/stz1672)

(ref: katz2022) Katz, H., Rosdahl, J., Kimm, T., et al. 2022, MNRAS, 510, 5603, doi: [`10.1093/mnras/stac028`](http://doi.org/10.1093/mnras/stac028)

(ref: kepley2020) Kepley, A. A., Tsutsumi, T., Brogan, C. L., et al. 2020, PASP, 132, 024505, doi: [`10.1088/1538-3873/ab5e14`](http://doi.org/10.1088/1538-3873/ab5e14)

(ref: kohandel2023) Kohandel, M., Ferrara, A., Pallottini, A., et al. 2023, MNRAS, 520, L16, doi: [`10.1093/mnrasl/slac166`](http://doi.org/10.1093/mnrasl/slac166)

(ref: lefevre2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1, doi: [`10.1051/0004-6361/201936965`](http://doi.org/10.1051/0004-6361/201936965)

(ref: liang2019) Liang, L., Feldmann, R., Kereš, D., et al. 2019, MNRAS, 489, 1397, doi: [`10.1093/mnras/stz2134`](http://doi.org/10.1093/mnras/stz2134)

(ref: Markov_2024) Markov, V., Gallerani, S., Ferrara, A., et al. 2024, arXiv e-prints, arXiv:2402.05996, doi: [`10.48550/arXiv.2402.05996`](http://doi.org/10.48550/arXiv.2402.05996)

(ref: Maseda2017) Maseda, M. V., Brinchmann, J., Franx, M., et al. 2017, A&A, 608, A4, doi: [`10.1051/0004-6361/201730985`](http://doi.org/10.1051/0004-6361/201730985)

(ref: meyer2024) Meyer, R. A., Oesch, P. A., Giovinazzo, E., et al. 2024, Monthly Notices of the Royal Astronomical Society, 535, 1067, doi: [`10.1093/mnras/stae2353`](http://doi.org/10.1093/mnras/stae2353)

(ref: michalowski2015) Michałowski, M. J. 2015, A&A, 577, A80, doi: [`10.1051/0004-6361/201525644`](http://doi.org/10.1051/0004-6361/201525644)

(ref: Milisavljevic_2024) Milisavljevic, D., Temim, T., Looze, I. D., et al. 2024, The Astrophysical Journal Letters, 965, L27, doi: [`10.3847/2041-8213/ad324b`](http://doi.org/10.3847/2041-8213/ad324b)

(ref: Moriwaki_2018) Moriwaki, K., Yoshida, N., Shimizu, I., et al. 2018, Monthly Notices of the Royal Astronomical Society: Letters, 481, L84–L88, doi: [`10.1093/mnrasl/sly167`](http://doi.org/10.1093/mnrasl/sly167)

(ref: naidu2022) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJL, 940, L14, doi: [`10.3847/2041-8213/ac9b22`](http://doi.org/10.3847/2041-8213/ac9b22)

(ref: nakazato2023) Nakazato, Y., Yoshida, N., & Ceverino, D. 2023, ApJ, 953, 140, doi: [`10.3847/1538-4357/ace25a`](http://doi.org/10.3847/1538-4357/ace25a)

(ref: Oesch_2016) Oesch, P. A., Brammer, G., Dokkum, P. G. v., et al. 2016, The Astrophysical Journal, 819, 129, doi: [`10.3847/0004-637x/819/2/129`](http://doi.org/10.3847/0004-637x/819/2/129)

(ref: Oesch_2023) Oesch, P. A., Brammer, G., Naidu, R. P., et al. 2023, MNRAS, 525, 2864, doi: [`10.1093/mnras/stad2411`](http://doi.org/10.1093/mnras/stad2411)

(ref: oke_gunn_1983ApJ...266..713O) Oke, J. B., & Gunn, J. E. 1983, ApJ, 266, 713, doi: [`10.1086/160817`](http://doi.org/10.1086/160817)

(ref: pallottini2022) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621, doi: [`10.1093/mnras/stac1281`](http://doi.org/10.1093/mnras/stac1281)

(ref: Popping_2023) Popping, G. 2023, Astronomy & Astrophysics, 669, L8, doi: [`10.1051/0004-6361/202244831`](http://doi.org/10.1051/0004-6361/202244831)

(ref: Ravindranath_2020) Ravindranath, S., Monroe, T., Jaskot, A., Ferguson, H. C., & Tumlinson, J. 2020, The Astrophysical Journal, 896, 170, doi: [`10.3847/1538-4357/ab91a5`](http://doi.org/10.3847/1538-4357/ab91a5)

(ref: Robertson_2023) Robertson, B. E., Tacchella, S., Johnson, B. D., et al. 2023, Nature Astronomy, 7, 611–621, doi: [`10.1038/s41550-023-01921-1`](http://doi.org/10.1038/s41550-023-01921-1)

(ref: Santini_2023) Santini, P., Fontana, A., Castellano, M., et al. 2023, The Astrophysical Journal Letters, 942, L27, doi: [`10.3847/2041-8213/ac9586`](http://doi.org/10.3847/2041-8213/ac9586)

(ref: schneider2024) Schneider, R., & Maiolino, R. 2024, A&ARv, 32, 2, doi: [`10.1007/s00159-024-00151-2`](http://doi.org/10.1007/s00159-024-00151-2)

(ref: schouws2022) Schouws, S., Stefanon, M., Bouwens, R., et al. 2022, ApJ, 928, 31, doi: [`10.3847/1538-4357/ac4605`](http://doi.org/10.3847/1538-4357/ac4605)

(ref: Schouws_2022) Schouws, S., Bouwens, R., Smit, R., et al. 2023, ApJ, 954, 103, doi: [`10.3847/1538-4357/ace10c`](http://doi.org/10.3847/1538-4357/ace10c)

(ref: schreiber2018) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30, doi: [`10.1051/0004-6361/201731506`](http://doi.org/10.1051/0004-6361/201731506)

(ref: Solomon_1992) Solomon, P. M., Downes, D., & Radford, S. J. E. 1992, ApJL, 387, L55, doi: [`10.1086/186304`](http://doi.org/10.1086/186304)

(ref: sommovigo2021) Sommovigo, L., Ferrara, A., Carniani, S., et al. 2021, MNRAS, 503, 4878, doi: [`10.1093/mnras/stab720`](http://doi.org/10.1093/mnras/stab720)

(ref: sommovigo2022) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022a, MNRAS, 513, 3122, doi: [`10.1093/mnras/stac302`](http://doi.org/10.1093/mnras/stac302)

(ref: sommovigo2022b) Sommovigo, L., Ferrara, A., Carniani, S., et al. 2022b, MNRAS, 517, 5930, doi: [`10.1093/mnras/stac2997`](http://doi.org/10.1093/mnras/stac2997)

(ref: Tang2021) Tang, M., Stark, D. P., Chevallard, J., et al. 2021, MNRAS, 501, 3238, doi: [`10.1093/mnras/staa3454`](http://doi.org/10.1093/mnras/staa3454)

(ref: thompson2017) Thompson, A. R., Moran, J. M., & Swenson, George W., J. 2017, Interferometry and Synthesis in Radio Astronomy, 3rd Edition, doi: [`10.1007/978-3-319-44431-4`](http://doi.org/10.1007/978-3-319-44431-4)

(ref: Treu_2023) Treu, T., Calabrò, A., Castellano, M., et al. 2023, The Astrophysical Journal Letters, 942, L28, doi: [`10.3847/2041-8213/ac9283`](http://doi.org/10.3847/2041-8213/ac9283)

(ref: vallini2021) Vallini, L., Ferrara, A., Pallottini, A., Carniani, S., & Gallerani, S. 2021, MNRAS, 505, 5543, doi: [`10.1093/mnras/stab1674`](http://doi.org/10.1093/mnras/stab1674)

(ref: vallini2024) Vallini, L., Witstok, J., Sommovigo, L., et al. 2024, MNRAS, 527, 10, doi: [`10.1093/mnras/stad3150`](http://doi.org/10.1093/mnras/stad3150)

(ref: weingartner2001) Weingartner, J. C., & Draine, B. T. 2001, ApJ, 548, 296, doi: [`10.1086/318651`](http://doi.org/10.1086/318651)

(ref: Williams_2023) Williams, C. C., Alberts, S., Ji, Z., et al. 2024, ApJ, 968, 34, doi: [`10.3847/1538-4357/ad3f17`](http://doi.org/10.3847/1538-4357/ad3f17)

(ref: Witstok23_dust) Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023a, MNRAS, 523, 3119, doi: [`10.1093/mnras/stad1470`](http://doi.org/10.1093/mnras/stad1470)

(ref: Witstok_2022) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751, doi: [`10.1093/mnras/stac1905`](http://doi.org/10.1093/mnras/stac1905)

(ref: Witstok2023_JWST) Witstok, J., Shivaei, I., Smit, R., et al. 2023b, Nature, 621, 267, doi: [`10.1038/s41586-023-06413-w`](http://doi.org/10.1038/s41586-023-06413-w)

(ref: Yang_2020) Yang, S., & Lidz, A. 2020, Monthly Notices of the Royal Astronomical Society, 499, 3417–3433, doi: [`10.1093/mnras/staa3000`](http://doi.org/10.1093/mnras/staa3000)

(ref: Yoon_2023) Yoon, I., Carilli, C. L., Fujimoto, S., et al. 2023, The Astrophysical Journal, 950, 61, doi: [`10.3847/1538-4357/acc94d`](http://doi.org/10.3847/1538-4357/acc94d)

(ref: zavala2024) Zavala, J. A., Castellano, M., Akins, H. B., et al. 2024, arXiv e-prints, arXiv:2403.10491, doi: [`10.48550/arXiv.2403.10491`](http://doi.org/10.48550/arXiv.2403.10491)

[^1]: https://help.almascience.org/kb/articles/what-is-the-absolute-astrometric-accuracy-of-alma

[^2]: For context, the CMB background at $z=14.2$ has a temperature of $T_{\mathrm{CMB}}=41.4$K.

</paper>

Write the methods card for this paper.