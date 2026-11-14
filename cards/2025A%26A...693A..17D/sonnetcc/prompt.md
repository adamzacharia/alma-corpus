# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...693A..17D\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...693A..17D",
 "title": "Unveiling dust, molecular gas, and high star-formation efficiency in extremely UV bright star-forming galaxies at z ∼ 2.1─3.6",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Dessauges-Zavadsky, M.",
 "n_authors": 7,
 "arxiv_id": "2410.11121",
 "doi": "10.1051/0004-6361/202451832",
 "alma_projects_linked_by_archive": [
  "2018.1.00932.S",
  "2021.1.01438.S"
 ]
}
```

Paper text:
<paper>
# Unveiling dust, molecular gas, and high star-formation efficiency in extremely UV bright star-forming galaxies at $z\sim 2.1-3.6$

# Introduction

The census of star-forming galaxies at high redshifts ($z>2$) has been ongoing for decades, and different observational techniques have been developed to identify galaxies either as Lyman break galaxies (LBGs) or Lyman-$\alpha$ emitters (LAEs). Large volumes of space have been probed to investigate their space density as a function of their ultraviolet luminosity through luminosity functions (cite: ReddySteidel09; Sobral+18a). The bright end of the luminosity function (LF) of the UV and Ly$\alpha$ emission corresponds to massive star formation and high production of ionising photons. However, the identification of the most UV- or Ly$\alpha$-luminous star-forming galaxies remains challenging for three possible reasons: vigorous episodes of star formation are simply rare phenomena; galaxies with high star-formation rates (SFRs) consume their gas quickly, implying short timescales for their UV- or Ly$\alpha$-luminous phases; or galaxies at the bright end of the LF produce significant quantities of dust during their intense star formation so that these most vigorous and intrinsically luminous star-forming galaxies quickly have their emission at UV wavelengths heavily obscured by dust (cite: Casey+14).

Probing the bright end of UV and Ly$\alpha$ LFs thus requires wide-area surveys. Several dedicated surveys at $z\sim 2-3$ covering a few square degrees ($1-4~\rm deg^2$) have searched for extremely UV-luminous galaxies but failed to discover galaxies more luminous than two times the typical luminosity ($L^{\star}$) of UV and Ly$\alpha$ of LBGs and LAEs, which corresponds to the unobscured absolute magnitude $M^{\star}_{\rm UV} = -20.7$ and $\log(L^{\star}_{\rm Ly\alpha}/\rm erg~s^{-1}) = 42.8$, respectively (cite: Ouchi+08; Zheng+16; Sobral+18b). The Baryon Oscillation Spectroscopic Survey Emission-Line Lens Survey for the GALaxy-Ly$\alpha$ EmitteR sYstems (cite: Shu+16) led to the discovery of

five LAEs at $2<z<3$ with intrinsic $M_{\rm UV}$ above $M^{\star}_{\rm UV}$, with two of them being brighter than $M_{\rm UV} < -23$ and having $L_{\rm Ly\alpha} > 2\times L^{\star}_{\rm Ly\alpha}$, and this was without the need to invoke an active galactic nucleus (AGN) component (cite: Marques+17; Marques+20a). Additionally, five strongly lensed UV-luminous non-active LBGs with $-23.5 < M_{\rm UV} < -21.1$ were also reported in the literature but with, on average, strongly suppressed Ly$\alpha$ lines, higher metallicities, stronger interstellar medium (ISM) absorption lines, and redder slopes, suggesting higher dust attenuation than the extremely UV-bright LAEs (cite: Pettini+00; Quider+09; Quider+10; Dessauges+10; Dessauges+11; Patricio+16; Marques+18).

Remarkably, UV-luminous galaxies above $M^{\star}_{\rm UV}$ are also detected at $z>6$ (cite: Sobral+15; Matsuoka+18; Hashimoto+19; Endsley+21; Bouwens+22a), and recent works now include the highest redshift sources known at the epoch of reionisation (EoR) discovered with the James Webb Space Telescope (JWST), leading to important and unexpected implications (cite: Bouwens+23; Atek+23; Bunker+23; Casey+23; Castellano+24; Carniani+24). The volume density inferred for these UV-luminous sources with $M_{\rm UV}$ reaching $-22.5$ is much higher by factors of $\sim 10-100$ than that predicted by models (cite: Mason+18), implying steeper UV LFs than predicted such that the bright end of the LFs does not significantly evolve between $8<z<16$ (cite: Naidu+22; Finkelstein+24; Chemerynska+24). The excess of these UV-bright sources at the EoR, which still needs to be confirmed with spectroscopic redshift assessments, currently puts strain on the standard $\Lambda$CDM cosmology unless new concepts in our understanding of star-formation processes and baryon physics are invoked (cite: Boylan23). Different scenarios have thus been proposed to explain the extremely UV-luminous and massive galaxies detected at the EoR and their excess, including a feedback-free starburst yielding a very high star-formation efficiency, namely a very efficient conversion of accreted gas into stars within a very short free-fall timescale (cite: Dekel+23; Li+24); a temporary removal of dust as a consequence of radiation-driven outflows that yields very low dust attenuation and makes the galaxies appear brighter (cite: Ferrara+23; Ziparo+23; Ferrara24); a top-heavy IMF boosting the UV radiation and the luminosity to mass ratio (cite: BekkiTsujimoto23; Trinca+24); and a stochastic variability of the SFR (cite: Mirocha+23; Gelli+24). Which of these scenarios holds now needs to be determined. Finally, although AGN contamination could possibly also explain the excess of these UV-bright sources at the EoR, this scenario was discarded by (cite: FinkelsteinBagley22) and only the exceptionally UV-luminous galaxy GN-z11 at $z=10.6$ potentially hosts an AGN (cite: Maiolino+24).

The recent search for extremely UV-luminous galaxies with $M_{\rm UV} < -23$ undertaken at $z\gtrsim 2$ within the $\sim 9000~\rm deg^2$-wide extended Baryon Oscillation Spectroscopic Survey (cite: Abolfathi+18) of the Sloan Digital Sky Survey (cite: Eisenstein+11) delivered about 70 galaxies at the very bright end of the UV LF, and they are among the most UV-bright galaxies known at cosmic noon (Marques-Chaves et al. in prep.). The first detailed studies of 13 of these galaxies are presented in (cite: Marques+20b), (cite: Alvarez+21), (cite: Marques+21), (cite: Marques+22), and (cite: Upadhyaya+24). We selected 12 of the most UV-luminous galaxies with $M_{\rm UV}$ ranging from $-23.4$ to $-24.5$

at $z=2.08-3.61$, accessible for observations with ALMA. They are characterised by unattenuated starlight with steep UV spectral slopes ranging from $-2.62$ to $-1.84$ and are dominated by young stellar populations with average ages of $\sim 10$ Myr, as testified by their rest-frame UV spectra revealing pure stellar features. Powered by powerful starbursts with very high specific SFRs ($\sim 100~\rm Gyr^{-1}$), the corresponding stellar masses are in the range of $(1.47-4.59)\times 10^9~M_{\odot}$, and they have sub-solar metallicities. Evidence of outflows, and even inflows, is found for some of these galaxies, as well as signatures of very massive stars (VMSs) with masses of $100~M_{\odot}-400~M_{\odot}$. Two galaxies are identified as very strong Lyman continuum (LyC) leakers. Considering these physical properties altogether, the galaxies are interpreted as being in an intense starburst phase with the bulk of their stellar mass being formed in a few millions of years.

Globally, most of the physical properties of these galaxies resemble the recently discovered galaxies at the EoR. Therefore, the scenarios proposed to explain the UV brightness and excess of galaxies out at $z>8$ could also explain the tremendous UV luminosities of these vigorous starburst galaxies at cosmic noon. The ALMA observations we acquired in the far-infrared (FIR) dust continuum at 1.3 mm (band 6) and in the CO(3–2) or CO(4–3) line emission (band 3) are key to inferring their dust and cold molecular gas masses – two physical parameters that are essential to fully probe the star-formation process ongoing in the galaxies and bring answers to the questions as to how much dust was produced within the $\sim 10$ Myr burst timescale, where dust is located so that it is reconciled with the steep UV spectral slopes, how much obscured star formation contributes to the whole SFR budget in these highly star-forming galaxies, how much molecular gas mass is available to feed their star formation, what are the subsequent molecular gas mass depletion timescale and star-formation efficiency, with the latter expected to be higher with respect to that of nearby galaxies given the high stellar mass build-up achieved within 10 Myr only. Efficiencies higher than 20% are indeed advocated by different studies to explain diverse observational findings at very high redshifts (cite: Xiao+24; deGraaff+24; Weibel+24) and make them compatible with simulations (cite: Kannan+23; Boylan23). These answers are helpful to determine whether the molecular gas mass reservoir is consumed rapidly so that galaxies quench by starvation or, on the contrary, the molecular gas mass reservoir is massive enough to produce high amounts of dust so that galaxies turn into luminous dusty star-forming galaxies.

In Sect. [2](#sect:targets) we describe the selection and the physical properties of the 12 UV-bright star-forming galaxies at $z = 2.08-3.61$ studied in this work. In Sect. [3](#sect:observations) we present their ALMA and Very Large Telescope (VLT) HAWK-I observations and the corresponding data reduction and imaging. We then analyse the CO line, the FIR dust continuum, and the rest-frame UV or optical emission, and we measure CO luminosities, molecular gas masses, IR luminosities, dust masses, and FIR dust continuum as well as the rest-frame UV/optical sizes. Section [4](#sect:results) discusses the derived measurements in the general context of main sequence (MS) star-forming galaxies and starburst galaxies at similar and higher redshifts. We focus on the dust-obscured star formation in Sect. [4.1](#sect:obscured-SFR), the molecular gas mass content and depletion timescale in Sect. [4.2](#sect:Mgas-tdepl), the star-formation efficiency in Sect. [4.3](#sect:SFE), the dust mass content in Sect. [4.4](#sect:Mdust), the FIR dust continuum and rest-frame UV/optical sizes in Sect. [4.5](#sect:sizes), and the rest-frame UV/optical morphology and spatial offsets in Sect. [4.6](#sect:UVmorphology). In Sect. [5](#sect:discussion) we try to obtain a complete understanding of these extremely UV-luminous galaxies, considering all of their physical properties. Finally, in Sect. [6](#sect:conclusions) we summarize our results.

Throughout the paper, we assume the $\Lambda$CDM cosmology with $\Omega_{\rm m} = 0.3$, $\Omega_{\Lambda} = 0.7$, and $H_0 = 70~\rm km~s^{-1}~Mpc^{-1}$. We adopt the (cite: Chabrier03) initial mass function (IMF).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | $z_{\rm nebular}$$^{a}$ | $M_{\rm UV}$ | $\beta_{\rm UV}$ | $L_{\rm UV}$ | $\rm SFR_{UV}$$^{b}$ | $M_{\rm stars}$$^{c}$ | sSFR$^{d}$ |
|  |  |  |  | $(10^{11}~L_{\odot})$ | $(\rm M_{\odot}~yr^{-1})$ | $(10^9~M_{\odot})$ | ($\rm Gyr^{-1}$) |
| J1322+0423 | 2.0800 | $-23.49$ | $-2.06\pm 0.12$ | $5.64\pm 0.12$ | $154\pm 7$ | $3.42\pm 0.40$ | $52\pm 7$ |
| J0146–0220 | 2.1595 | $-23.68$ | $-1.98\pm 0.12$ | $6.76\pm 0.06$ | $127\pm 6$ | $3.41\pm 0.43$ | $61\pm 23$ |
| J1415+2036 | 2.2435 | $-23.53$ | $-3.49\pm 0.11^{\dagger}$ | $5.87\pm 0.12$ | $188\pm 11$ | $1.88\pm 0.20$ | $118\pm 14$ |
| J1249+1550 | 2.2928 | $-23.41$ | $-1.84\pm 0.12$ | $5.24\pm 0.11$ | $118\pm 5$ | $4.25\pm 0.53$ | $48\pm 18$ |
| J0006+2452 | 2.3796 | $-24.17$ | $-2.30\pm 0.10$ | $10.6\pm 0.2$ | $232\pm 7$ | $3.16\pm 0.31$ | $163\pm 59$ |
| J0850+1549 | 2.4235 | $-23.76$ | $-2.62\pm 0.14$ | $7.21\pm 0.17$ | $189\pm 8$ | $1.89\pm 0.26$ | $131\pm 49$ |
| J1220–0051 | 2.4269 | $-23.50$ | $-2.43\pm 0.11$ | $5.68\pm 0.12$ | $144\pm 5$ | $1.47\pm 0.16$ | $163\pm 59$ |
| J0950+0523 | 2.4548 | $-23.69$ | $-2.41\pm 0.15$ | $6.80\pm 0.18$ | $179\pm 9$ | $1.91\pm 0.29$ | $191\pm 73$ |
| J1220+0842 | 2.4698 | $-24.36$ | $-2.36\pm 0.09$ | $12.6\pm 0.2$ | $302\pm 7$ | $3.60\pm 0.32$ | $100\pm 9$ |
| J1157+0113 | 2.5450 | $-23.40$ | $-2.15\pm 0.34$ | $5.19\pm 0.16$ | $104\pm 8$ | $1.94\pm 0.68$ | $126\pm 62$ |
| J0121+0025 | 3.2445 | $-24.11$ | $-2.19\pm 0.20$ | $10.0\pm 0.1$ | $269\pm 18$ | $4.59\pm 0.92$ | $74\pm 27$ |
| J1316+2614 | 3.6122 | $-24.65$ | $-2.59\pm 0.05$ | $16.4\pm 0.2$ | $415\pm 16$ | $4.15\pm 1.15$ | $118\pm 47$ |

Table notes:

# Target sample and their properties

This work presents ALMA and VLT HAWK-I observations of 12 extremely UV-bright star-forming galaxies at $z=2.08-3.61$. These sources are part of a large sample of about 70 UV-luminous galaxies (Marques-Chaves et al. in prep.) selected from the $\sim 9000~\rm deg^2$-wide eBOSS/SDSS survey (cite: Abolfathi+18) to have high UV absolute magnitudes and narrow Ly$\alpha$ emission profiles in their BOSS spectra (covering the spectral range $\lambda \simeq 3600-10000$ Å with a resolving power $R\simeq 2000$). The targets studied here were selected for ALMA and HAWK-I observations with declinations $\leq 30^{\circ}$ and other properties that are representative of the parent sample. They show extremely bright $M_{\rm UV}$ ranging from $-23.4$ to $-24.6$, Ly$\alpha$ luminosities of $\log(L_{\rm Ly\alpha}/\rm erg~s^{-1}) = 42.9-44.1$, and Ly$\alpha$ rest-frame equivalent widths of $EW_{\rm Ly\alpha} = 12-55~\AA$. The rest-frame UV and optical properties of a fraction (7/12) of these targets were analysed in detail in previous works through deep spectroscopy with the 10.4 m Gran Telescopio Canarias (cite: Marques+20b; Marques+21; Marques+22; Marques+24; Alvarez+21; Upadhyaya+24), and for the remaining targets through shallow SDSS spectroscopy. We measured steep UV spectral slopes ($\beta_{\rm UV}$) from $-2.62$ to $-1.84$, suggesting residual/low dust attenuations $E(B-V) \leq 0.1$ when assuming the (cite: Calzetti+00) extinction law with an intrinsic $\beta_0 = -2.44$.

In the references listed above it is also shown that the rest-frame UV spectra of the galaxies studied here reveal pure stellar features, such as wind lines and photospheric absorption, known to be produced only by the atmospheres of the most massive stars; as such, they are characterised by very young stellar populations with an average age of $\sim 10$ Myr for the whole sample (but some galaxies are even younger and some slightly older). They have metallicities in the range of $12+\log({\rm O/H}) = 8.13-8.49$, with a mean of 8.36, that is, $Z/Z_{\odot}\simeq 0.5$.

Using their UV luminosities ($L_{\rm UV}$), we measured high unobscured star-formation rates ${\rm SFR_{UV}} = 104-415~M_{\odot}~\rm yr^{-1}$ by applying the specific $L_{\rm UV}$–$\rm SFR_{UV}$ conversion factor $\kappa_{\rm UV} = 1.3\times 10^{-28}~M_{\odot}~\rm yr^{-1}/(erg~s^{-1}~Hz^{-1})$, derived using the Binary Population and Spectral Synthesis (BPASS) binary models (cite: Eldridge+17; StanwayEldridge18; Byrne+22), and assuming a continuous star formation over 10 Myr, a metallicity of $0.5~Z_{\odot}$, and the (cite: Chabrier03) IMF. However, one needs to keep in mind that $\kappa_{\rm UV}$ is strongly dependent on the burst age for 10 Myr and below, such that $\rm SFR_{UV}$ gets more than twice higher for a two times shorter continuous star formation, as explained in (cite: Marques+24). The stellar masses of the young stellar population were then derived following

$M_{\rm stars} = {\rm SFR_{UV}}\times 10~\rm Myr$, where $\rm SFR_{UV}$ were corrected for the dust attenuation using the observed $\beta_{\rm UV}$;

we obtained $M_{\rm stars} = (1.47-4.59)\times 10^9~M_{\odot}$. Analysing the spectral energy distributions (SEDs) of the galaxies, (cite: Marques+20b; Marques+21; Marques+22) find that the SEDs are dominated by a young and intense burst of star formation, and could only infer loose upper limits on the mass of the old stellar population $\log (M_{\rm stars}^{\rm old}/M_{\odot}) < 9.8-10.2$ ($3\sigma$). The new Hubble Space Telescope (HST) photometry recently acquired for J1316+2614 provides a more stringent upper limit on $\log (M_{\rm stars}^{\rm old}/M_{\odot}) < 9.46$ ($3\sigma$), yielding a fraction of the starburst mass to the total (young+old) stellar mass $>62\%$ (cite: Marques+24). The absence of relevant old stellar population in these galaxies

is interpreted as indicating that the galaxies are in an intense starburst phase with the bulk of their stellar mass being formed in a few millions of years. Table [\[tab:restUV-properties\]](#tab:restUV-properties) summarizes all the rest-frame UV physical properties derived for our galaxies.

The galaxies studied here also appear as very strong producers of ionising radiation given their extreme $M_{\rm UV}$, and two are confirmed to be strong LyC leakers (cite: Marques+21; Marques+22), with J1316+2614 at $z=3.6122$ reaching a LyC escape fraction as high as $f_{\rm esc}({\rm LyC}) \simeq 90$%. Moreover, they have complex gas kinematics, showing signatures of outflows from the weak ISM absorption lines having blueshifted centroids with respect to the systemic redshift (cite: Alvarez+21; Marques+21), and even signatures of inflow for J1316+2614 from the blue-dominated Ly$\alpha$ emission with respect to the systemic redshift (cite: Marques+22).

![image](LBG3contB6.pdf) ![image](J1322HAWKI.pdf) ![image](LBG3CO32B3mom0.pdf)

![image](SDSS0146contB6.pdf) ![image](J0146contB6HAWKI.pdf) ![image](SDSS0146CO32B3mom0.pdf) ![image](SDSS0146CO32spec.pdf)

![image](LBG4contB6.pdf) ![image](J1415HAWKI.pdf) ![image](LBG4CO32B3mom0.pdf) ![image](LBG4CO32spec.pdf)

![image](LBG7contB6.pdf) ![image](J1249contB6HAWKI.pdf) ![image](LBG7CO32B3mom0.pdf) ![image](LBG7CO32spec.pdf)

# Observations and data analysis

## ALMA data reduction and imaging

The 12 targets are part of two ALMA observing programmes. The first programme 2018.1.00932.S (PI: R. Marques-Chaves) includes J0146–0220, J0850+1549, J1220+0842, and J1157+0113, and was observed in Cycle 6 in bands 3 and 6 in the configurations C43-4 and C43-3, respectively, with short on-source integration times per target between 5 and 35 minutes. The second programme 2021.1.01438.S (PI: R. Marques-Chaves) includes J1322+0423, J1415+2036, J1249+1550, J0006+2452, J1220–0051, J0950+0523, J0121+0025, and J1316+2614, and was observed in Cylcle 8 also in bands 3 and 6 in the configurations C43-5 and C43-1 (C43-2 for J0950+0523), respectively, with on-source integration times of about 40 minutes per target. The band 3 observations were tuned to the CO(3–2) emission line, except for the 2 highest redshift targets at $z>3$, J1316+2614 and J0121+0025, that were tuned to the CO(4–3) emission line. The band 6 observations were aimed for the 240 GHz (1.3 mm) FIR dust continuum solely and therefore were not tuned to a specific frequency. The spectral resolution was set to $31.25~\rm MHz$ (i.e. $\sim 45~\rm km~s^{-1}$) for both band 3 and 6 observations.

The ALMA data were calibrated with the standard observatory pipeline, and imaged using the Common Astronomy Software Application (cite: McMullin+07). We imaged the band 6 calibrated visibilities of continuum over the four spectral windows with the multi-frequency synthesis, applying a pixel size of $0.1\ensuremath{''}$ (for the 2018.1.00932.S targets) or $0.15\ensuremath{''}$ (for the 2021.1.01438.S targets), and the natural weighting. The clean was repeated down to the threshold of $4\times$ the RMS noise level of the dirty images using the `tclean` routine in CASA. We then applied the primary beam correction on the cleaned continuum emission maps. The corresponding FIR continuum maps are shown in Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3) (left panels).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | $z_{\rm CO}$$^{a}$ | CO | Synthesised beam | RMS | $I_{\rm CO}$$^{c}$ | FWHM$^{d}$ | $L^{\prime}_{\rm CO}$ |
|  |  | line | Size $(\ensuremath{''})$ / PA $(^\circ)$ | (  $^{b}$) | $(\rm mJy~km~s^{-1})$ | $(\rm km~s^{-1})$ | $(10^9~\rm K~km~s^{-1}~pc^2)$ |
| J1322+0423 | 2.0800$^{e}$ | 3–2 | $1.86\times 1.22$ / $-50$ | 59 | $<236$ | – | $< 5.82$ |
| J0146–0220 | $2.1596\pm 0.0002$ | 3–2 | $1.01\times 0.63$ / $+59$ | 71 | $373\pm 25$ | $358\pm 61$ | $9.82\pm 0.66$ |
| J1415+2036 | $2.2448\pm 0.0004$ | 3–2 | $0.87\times 0.62$ / $+17$ | 25 | $<304\pm 62$$^{g}$ | $332\pm 47$ | $<8.57\pm 1.75$ |
| J1249+1550 | $2.2926\pm 0.0009$ | 3–2 | $0.74\times 0.51$ / $+36$$^{f}$ | 28 | $193\pm 12$ | $446\pm 115$ | $5.64\pm 0.35$ |
| J0006+2452 | $2.3800\pm 0.0003$ | 3–2 | $0.81\times 0.52$ / $+30$$^{f}$ | 45 | $906\pm 51$ | $546\pm 107$ | $28.3\pm 1.6$ |
| J0850+1549 | 2.4235$^{e}$ | 3–2 | $0.98\times 0.76$ / $+30$ | 45 | $<180$ | – | $< 5.78$ |
| J1220–0051 | $2.4271\pm 0.0001$ | 3–2 | $0.77\times 0.61$ / $+34$ | 28 | $240\pm 25$ | $295\pm 46$ | $7.74\pm 0.81$ |
| J0950+0523 | $2.4538\pm 0.0006$ | 3–2 | $0.50\times 0.36$ / $+34$$^{f}$ | 36 | $470\pm 29$ | $524\pm 138$ | $15.4\pm 1.0$ |
| J1220+0842 | 2.4698$^{e}$ | 3–2 | $0.95\times 0.77$ / $-35$ | 65 | $<260$ | – | $< 8.63$ |
| J1157+0113 | $2.5459\pm 0.0003$ | 3–2 | $0.83\times 0.80$ / $-71$ | 25 | $237\pm 21$ | $394\pm 95$ | $8.29\pm 0.73$ |
| J0121+0025 | 3.2445$^{e}$ | 4–3 | $0.60\times 0.57$ / $-45$ | 30 | $<225\pm 65$$^{g}$ | – | $<6.63\pm 1.92$ |
| J1316+2614 | 3.6122$^{e}$ | 4–3 | $0.94\times 0.61$ / $+10$ | 27 | $<108$ | – | $< 3.79$ |

Table notes:

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | Synthesised beam | RMS | $S_{\rm 1.3mm}$$^{b}$ | $L_{\rm IR}$$^{c}$ | $R_{\rm eff,FIR}$$^{d}$ | HAWK-I | PSF | $R_{\rm eff,UV/opt}$$^{e}$ |
|  | Size $(\ensuremath{''})$ / PA $(^\circ)$ | (  $^{a}$) | $(\mu \rm Jy)$ | $(10^{11}~L_{\odot})$ | (kpc) | band | ($\ensuremath{''}$) | (kpc) |
| J1322+0423 | $1.59\times 1.39$ / $-89$ | 12 | $<48$ | $< 2.59$ | – | $H$ | 0.49 | $2.01\pm 0.10$ |
| J0146–0220 | $0.63\times 0.56$ / $-74$ | 15 | $148\pm 10$ | $8.06\pm 2.90$ | – | $K_s$ | 0.37 | $2.59\pm 0.10^{\dagger}$ |
| J1415+2036 | $1.71\times 1.38$ / $+24$ | 15 | $<64$ | $<3.40$ | – | $K_s$ | 0.38 | $1.24\pm 0.68$ |
| J1249+1550 | $1.65\times 1.54$ / $+56$ | 17 | $155\pm 10$ | $8.54\pm 3.01$ | $5.0\pm 2.0$ | $K_s$ | 0.28 | $1.04\pm 0.05$ |
| J0006+2452 | $1.70\times 1.30$ / $+9$ | 18 | $510\pm 30$ | $28.3\pm 9.8$ | $3.5\pm 0.9$ | $K_s$ | 0.39 | $2.23\pm 0.35^{\dagger}$ |
| J0850+1549 | $0.72\times 0.59$ / $-3$ | 13 | $106\pm 20$ | $5.90\pm 2.04$ | $1.8\pm 0.5$ | $R^f$ | 0.71 | $1.46\pm 0.18$ |
| J1220–0051 | $1.60\times 1.33$ / $-80$ | 16 | $172\pm 12$ | $9.57\pm 3.30$ | $2.4\pm 1.0$ | $H$ | 0.61 | $1.51\pm 0.22$ |
| J0950+0523 | $1.07\times 0.76$ / $+57$ | 14 | $331\pm 20$ | $18.5\pm 6.3$ | $2.0\pm 0.7$ | $K_s$ | 0.36 | $<0.74$ |
| J1220+0842 | $0.62\times 0.61$ / $-27$ | 25 | $<102$ | $<5.69$ | – | $H$ | 0.44 | $1.64\pm 0.24$ |
| J1157+0113 | $0.63\times 0.58$ / $-89$ | 11 | $251\pm 40$ | $14.1\pm 4.8$ | – | $H$ | 0.38 | $1.07\pm 0.14$ |
| J0121+0025 | $1.57\times 1.14$ / $+63$ | 10 | $122\pm 30$ | $7.12\pm 2.15$ | $3.6\pm 0.8$ | $R^g$ | 0.55 | $0.79\pm 0.15$ |
| J1316+2614 | $1.70\times 1.33$ / $+8$ | 11 | $124\pm 20$ | $7.37\pm 2.09$ | $1.7\pm 0.8$ | $K_s$ | 0.30 | $<0.55$ |

Table notes:

For the CO(3–2) and CO(4–3) emission imaging we used the pixel size of $0.1\ensuremath{''}$ (for the 2018.1.00932.S targets) or $0.05\ensuremath{''}$ (for the 2021.1.01438.S targets). The Briggs weighting with the robust factor of 1.0 was applied for the few galaxies with a high S/N CO detection, otherwise we applied the natural weighting. Similarly to the continuum maps, we cleaned all channels with the `tclean` routine down to the threshold of $4\times$ the RMS noise level of the dirty cubes, and a primary beam correction was applied. Finally, we also imaged the band 3 calibrated visibilities of continuum over the four spectral windows, excluding channels contaminated by the CO emission. No band 3 (100 GHz) continuum was detected in any target. The resulting band 3 (CO emission) and band 6 (continuum emission) synthesised beam sizes and RMS noise levels for the 12 targets are listed in Tables [\[tab:COdata\]](#tab:COdata) and [\[tab:FIRdata\]](#tab:FIRdata), respectively.

The CO moment-0 maps, that is, the velocity-integrated CO line intensity maps, were obtained by averaging the cleaned cube over the spectral channels where the CO emission is detected, using the `immoments` routine in CASA. We adopted the optimum channel range as the one that is maximising the S/N of the 1D spectrum of the CO emission line by iteratively testing different channel ranges (cite: Daddi+15; Zanella+18). For each channel range tested, the CO emission was extracted within a custom (polygonal) aperture including all the flux above the RMS noise level and typically bigger than the synthesised beam size. No band 3 continuum was subtracted beforehand, since undetected. The corresponding CO moment-0 maps and the CO line spectra are shown in Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3) (middle-right and right panels).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | $z_{\rm nebular}$$^{a}$ | $\rm SFR_{IR}$$^{b}$ | $M_{\rm molgas}$$^{c}$ | $M_{\rm dust}$$^{d}$ | $t_{\rm depl}$$^{e,f}$ | $f_{\rm molgas}$$^{f}$ | $\epsilon_{\rm SF}$$^{f}$ |
|  |  | $(\rm M_{\odot}~yr^{-1})$ | $(10^{10}~M_{\odot})$ | $(10^7~M_{\odot})$ | (Myr) |  | (%) |
| J1322+0423 | 2.0800 | $< 26$ | $<0.76$ | $<1.09$ | $<42$ | $<0.69$ | $>31$ |
| J0146–0220 | 2.1595 | $81\pm 29$ | $1.28\pm 0.09$ | $3.32\pm 1.78$ | $61\pm 23$ | $0.79\pm 0.11$ | $21\pm 3$ |
| J1415+2036 | 2.2435 | $<34$ | $<1.11\pm 0.23$ | $<1.38$ | $<50\pm 11$ | $<0.86\pm 0.20$ | $>14\pm 3$ |
| J1249+1550 | 2.2928 | $85\pm 30.$ | $0.73\pm 0.05$ | $3.42\pm 1.79$ | $36\pm 13$ | $0.63\pm 0.09$ | $37\pm 5$ |
| J0006+2452 | 2.3796 | $283\pm 98$ | $3.67\pm 0.21$ | $11.1\pm 5.7$ | $71\pm 25$ | $0.92\pm 0.11$ | $8\pm 0.9$ |
| J0850+1549 | 2.4235 | $59\pm 20$ | $<0.75$ | $2.30\pm 1.18$ | $<30$ | $<0.80$ | $>20$ |
| J1220–0051 | 2.4269 | $96\pm 33$ | $1.01\pm 0.10$ | $3.73\pm 1.90$ | $42\pm 15$ | $0.87\pm 0.13$ | $13\pm 2$ |
| J0950+0523 | 2.4548 | $185\pm 63$ | $2.01\pm 0.12$ | $7.15\pm 3.63$ | $55\pm 19$ | $0.91\pm 0.15$ | $9\pm 1$ |
| J1220+0842 | 2.4698 | $<57$ | $<1.12$ | $<2.20$ | $<31$ | $<0.76$ | $>24$ |
| J1157+0113 | 2.5450 | $141\pm 48$ | $1.08\pm 0.10$ | $8.97\pm 2.68$ | $44\pm 16$ | $0.85\pm 0.31$ | $15\pm 6$ |
| J0121+0025 | 3.2445 | $71\pm 22$ | $<1.11\pm 0.32$ | $3.75\pm 1.08$ | $<32\pm 14$ | $<0.71\pm 0.25$ | $>29\pm 10$ |
| J1316+2614 | 3.6122 | $74\pm 21$ | $<0.63$ | $3.53\pm 1.01$ | $<13$ | $<0.60$ | $>40$ |

Table notes:

## From the CO emission line to molecular gas masses

The CO emission is successfully detected close to the phase centre and at the expected frequency for eight targets. J0146–0220, J1249+1550, J0006+2452, J1220–0051, J0950+0523, and J1157+0113 show robust CO detections above $5\sigma$, while J1415+2036 and J0121+0025 show patchy CO emission peaks at $4-5\sigma$ significance level spread over $< 3\ensuremath{''}$ (i.e. $< 25~\rm kpc$) around the phase centre (Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3), middle-right panels). Four of the robust CO detections in J0006+2452, J1220–0051, J0950+0523, and J1157+0113 are spatially resolved, while J0146–0220 and J1249+1550 are unresolved/marginally resolved with their CO emission being comparable to the ALMA synthesised beam size. All the CO line profiles are complex, most are characterised by double-peaks and J1157+0113 even shows a triple-peak (Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3), right panels). They are difficult to interpret (between rotation/mergers) with the current data which do not allow us to perform a detailed kinematic analysis via velocity (moment-1) and dispersion (moment-2) maps given that all our galaxies are not sufficiently resolved.

We measured the CO velocity-integrated intensities ($I_{\rm CO}$) from the CO moment-0 maps integrating all the signal located around the phase centre, above the surrounding RMS noise level. No aperture correction was needed as the customised apertures used were all bigger than the synthesised beam.

The derived $I_{\rm CO}$ agree very well with those determined from the Gaussian fitting of the CO line profiles. To fit the complex CO line profiles, we performed multi-component Gaussian fitting using the nonlinear $\chi^2$ minimisation and the Levenberg-Marquardt algorithm. Errors on the values of CO redshifts ($z_{\rm CO}$), full-width half maximum ($\rm FWHM_{CO}$), and $I_{\rm CO}$ were estimated using the Monte Carlo approach by perturbing the observed spectrum with 1000 random realisations. For the CO non-detections, upper limits on $I_{\rm CO}$ were derived from the $4\sigma$ RMS noise level of moment-0 maps integrated over $\sim 350~\rm km~s^{-1}$, the typical FWHM measured for the detected CO emission lines of our targets. We then used Eq. (3) from (cite: Solomon+97) to derive the CO luminosities ($L^{\prime}_{\rm CO}$) from the respective $I_{\rm CO}$. The resulting measurements can be found in Table [\[tab:COdata\]](#tab:COdata).

The molecular gas mass ($M_{\rm molgas}$) is then expressed as $$\begin{equation}
M_{\rm molgas} = \alpha_{\rm CO} \frac{L^{\prime}_{{\rm CO}~J\rightarrow J-1}}{r_{J,1}},
\end{equation}$$ where $L^{\prime}_{{\rm CO}~J\rightarrow J-1}$ in $\rm K~km~s^{-1}~pc^2$ is the luminosity of a given CO transition, $r_{J,1}$ is the CO luminosity correction for this transition to the fundamental CO(1–0) transition, and $\alpha_{\rm CO}$ in $M_{\odot}~\rm (K~km~s^{-1}~pc^2)^{-1}$ is the conversion factor between the CO(1–0) luminosity and the H$_2$ gas mass.

To convert the CO(3–2) and CO(4–3) luminosities to the fundamental CO(1–0) luminosity, which ultimately gives the total H$_2$ molecular gas mass, we applied the CO luminosity correction factors $r_{3,1} = 0.77\pm 0.14$ and $r_{4,1} = 0.61\pm 0.13$, respectively, derived by (cite: Boogaard+20) from the stacking of CO-flux-limited star-forming galaxies at $z\sim 2.5$ from the ALMA SPECtroscopic Survey (ASPECS). Overall, the adopted CO excitation (i.e. CO spectral line energy distribution) is comparable to the one of a lensed star-forming galaxy at $z\sim 3.6$ with a similar IR luminosity to our targets (cite: Dessauges+17) and $z\sim 2.5$ starburst galaxies (cite: Xiao+22). It is also comparable to the recently derived CO excitation of IR-luminous sub-mm galaxies (SMGs) at $z=2-5$ (cite: Castillo+23), in contrast with the initially higher CO excitation derived for SMGs at $z=1-4$ (cite: Bothwell+13).

As for the CO-to-H$_2$ conversion factor, hereafter we favour the value derived for nearby starburst galaxies, $\alpha_{\rm CO}^{\rm SB} = 1~M_{\odot}~\rm (K~km~s^{-1}~pc^2)^{-1}$, given the starburst nature of our targets (Sect. [2](#sect:targets)).

The corresponding $M_{\rm molgas}$ measurements are summarised in Table [\[tab:COdust-properties\]](#tab:COdust-properties). In Sects. [4.2](#sect:Mgas-tdepl) and [4.3](#sect:SFE) we discuss the impact of $\alpha_{\rm CO}$ values between $\alpha_{\rm CO}^{\rm SB}$ and the Milky Way value $\alpha_{\rm CO}^{\rm MW} = 4.36~M_{\odot}~\rm (K~km~s^{-1}~pc^2)^{-1}$ (cite: Bolatto+13).

## From the FIR dust continuum to IR luminosities and dust masses

The 1.3 mm (240 GHz) band 6 FIR dust continuum emission is robustly detected at the phase centre for nine targets: J0146–0220, J1249+1550, J0006+2452, J0850+1549, J1220–0051, J0950+0523, J1157+0113, J0121+0025, and J1316+2614 (Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3), left panels). All the continuum detections are spatially resolved, except in J0146–0220 whose continuum emission is comparable to the ALMA synthesised beam size.

We measured the FIR fluxes ($S_{\rm 1.3mm}$) from the 1.3 mm (240 GHz) continuum emission maps using customised apertures big enough to include for each emission all the signal located around the phase centre, above the surrounding RMS noise level (no aperture correction was needed as the apertures used were all bigger than the synthesised beam). The derived $S_{\rm 1.3mm}$ agree very well with those determined from the fitting of the continuum emission in the *uv* plane by adopting the Fourier transform of the elliptical Gaussian 2D model. The fits were done using the `UV_FIT` routine from the GILDAS software package (cite: Guilloteau+00), leaving the centre coordinates, flux, $\rm FWHM_{major}$, $\rm FWHM_{minor}$, and position angle of the Gaussian 2D model as free parameters. The fit in the *uv* plane did not converge for one target J1157+0113, certainly because of the complex shape of its emission in the continuum map that could not be approximated by the elliptical Gaussian 2D model. For the continuum non-detections, we considered $4\sigma$ upper limits estimated from the RMS noise level of the continuum dirty images. The resulting $S_{\rm 1.3mm}$ measurements are listed in Table [\[tab:FIRdata\]](#tab:FIRdata).

We used the results of the *uv* fits to derive the deconvolved FIR dust continuum sizes of the spatially resolved targets (except for J1157+0113). We computed the effective radius ($R_{\rm eff,FIR}$), defined as the radius enclosing half of the total emission, following $R_{\rm eff,FIR} = \sqrt{\rm FWHM_{major} \times FWHM_{minor}}/2$, where the square root of the product of the deconvolved full-width half maximum along the major and minor axes of the Gaussian 2D most precise fits of the FIR continuum emission corresponds to the circularised $\rm FWHM$ radius. The resulting $R_{\rm eff,FIR}$ are listed in Table [\[tab:FIRdata\]](#tab:FIRdata).

Since our galaxies have a low dust attenuation $E(B-V)\leq 0.1$ (Sect. [2](#sect:targets)), we assumed that the emission models for these galaxies should be optically thin. Therefore, to determine the IR luminosity ($L_{\rm IR}$) we scaled the optically thin modified black-body (MBB) function (cite: Casey12) to the measured 1.3 mm (240 GHz) continuum flux of each target, and integrated over the wavelength range between $8~\mu \rm m$ and $1000~\mu \rm m$. We derived the dust mass ($M_{\rm dust}$) from $S_{\rm 1.3mm}$ in Jy by following (cite: Casey12) $$\begin{equation}
M_{\rm dust} = \frac{D_{\rm L} S_{\rm 1.3mm}}{\kappa B_{\nu}(T_{\rm dust})},
\end{equation}$$ where $D_{\rm L}$ in m is the luminosity distance, and $B_{\nu}(T_{\rm dust})$ in $\rm Jy~sr^{-1}$ is the Planck function at the dust temperature ($T_{\rm dust}$) and the observer-frame frequency ($\nu = 240~\rm GHz$). We assumed $T_{\rm dust} = 40~\rm K$ for the dust associated with the starburst regions of our targets at $z\sim 2.1-3.6$ (cite: Schreiber+18; Sommovigo+22; Viero+22; Witstok+23). For the dust mass absorption coefficient $\kappa = \kappa_0 (\frac{\nu}{\nu_0})^{\beta}$, where $\beta$ is the dust emissivity index and $\kappa_0$ the dust opacity at $\nu_0$ ($\lambda_0$), we assumed $\beta = 1.4$, $\kappa_0 = 40~\rm cm^2~g^{-1}$, and $\lambda_0 = 100$ $\mu$m (cite: BianchiSchneider07). We then derived the uncertainties on $L_{\rm IR}$ and $M_{\rm dust}$ as the median absolute deviations (mad) obtained when averaging over $T_{\rm dust} = 30$ K, 35 K, 40 K, and 45 K and seven different $\kappa$ models of dust composition listed in (cite: Ginolfi+19), each of them providing a combination of parameters $\beta$, $\kappa_0$, and $\lambda_0$ selected from the literature (cite: WeingartnerDraine01; Bertoldi+03; Robson+04; Beelen+06; BianchiSchneider07; Galliano+11; Jones+17). The resulting uncertainties are big but allow us to place our $L_{\rm IR}$ and $M_{\rm dust}$ estimates on the conservative side given the poorly constrained FIR SED with one single band continuum measurement. They are also big enough to encompass the $\gtrsim 5-10\%$ correction factor potentially needed to derive the intrinsic dust emission detected against the cosmic microwave background at the redshift of our galaxies (which we have not applied) computed by (cite: daCunha+13).

In Table [\[tab:FIRdata\]](#tab:FIRdata) we summarize the derived $L_{\rm IR}$, and $M_{\rm dust}$ can be found in Table [\[tab:COdust-properties\]](#tab:COdust-properties).

## VLT HAWK-I data reduction and analysis

The near-IR imaging was obtained in $H$- and $K_{\rm s}$-bands for 10 targets with HAWK-I on the VLT UT4. These observations were conducted between March 2023 and February 2024 in service mode as part of the programme 111.251K.001 (PI: R. Marques-Chaves). The $H$-band observations were taken under very good seeing conditions of $0.4\ensuremath{''} - 0.6\ensuremath{''}$ (FWHM). The $K_{\rm s}$-band observations were obtained with the GRound layer Adaptive optics system Assisted by Lasers (GRAAL), enhancing the final image quality down to $0.3\ensuremath{''} - 0.4\ensuremath{''}$ (FWHM). For each target, the total on-source exposure times were 560 seconds and 1350 seconds in the $H$- and $K_{\rm s}$-bands, respectively. Data were reduced using the standard ESO pipeline version 2.4.12[^1] and were flux calibrated against 2MASS stars in the field. The astrometry was calibrated using the GAIA DR3 catalogue (cite: Gaia+23) yielding an RMS precision of $0.10\ensuremath{''} - 0.13\ensuremath{''}$, which is roughly similar to the HAWK-I native pixel-scale ($0.107\ensuremath{''}$ per pixel).

Given the very good HAWK-I image quality, we investigated the morphology and sizes of the galaxies[^2]. We used GALFIT (cite: Peng+02) to fit the light distribution of each galaxy with the 2D Gaussian function convolved to the instrumental point spread function (PSF) that was measured from bright stars in the HAWK-I field-of-view. The fitting process was performed on $10\ensuremath{''} \times 10\ensuremath{''}$ background-subtracted cutouts centred on each target, shown in Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3) (middle-left panels). Overall, a single 2D Gaussian profile fitted well the observed light profiles for most of our galaxies, except for J0146–0220 and J0006+2452 that required an additional component. We find that eight galaxies are resolved in the HAWK-I images, for which we derived the rest-frame UV or optical effective radius ($R_{\rm eff,UV/opt}$) measurements.

The two remaining galaxies, J0950+0523 and J1316+2614, are unresolved with effective radii as small as $R_{\rm eff,UV} < 0.55$ kpc for J1316+2614. J0146–0220 and J0006+2452 show a bright and unresolved component beside the extended and resolved component.

For the two targets with no HAWK-I observations, J0850+1549 and J0121+0025, we used, respectively, the public CFHT MegaCam and Subaru seeing-limited $R$-band images to infer their sizes, following the same methodology as described for HAWK-I images. The rest-frame UV or optical effective radii of our 12 UV-bright galaxies are summarised in Table [\[tab:FIRdata\]](#tab:FIRdata).

# Results

## Dust-obscured star formation

As summarised in Sect. [2](#sect:targets), our galaxies are intense starburst galaxies with very high unobscured star-formation rates for their $M_{\rm stars}$ and redshifts, ranging between $\rm SFR_{UV} = 104~M_{\odot}~\rm yr^{-1}$ and $415~M_{\odot}~\rm yr^{-1}$ (uncorrected for dust attenuation; Table [\[tab:restUV-properties\]](#tab:restUV-properties)). The measured $L_{\rm IR}$ (Table [\[tab:FIRdata\]](#tab:FIRdata)), moreover, show that most of these UV-bright galaxies reside in the regime of luminous IR galaxies (LIRGs; $10^{11} < L_{\rm IR}/L_{\odot} < 10^{12}$) and 3 galaxies reside at the faint end of ultra-luminous IR galaxies (ULIRGs; $10^{12} < L_{\rm IR}/L_{\odot} < 10^{13}$). They provide a measure of the obscured star-formation rates, defined as ${\rm SFR_{IR}}  =  L_{\rm IR} /10^{10}$, following the calibration of (cite: Kennicutt98) for the (cite: Chabrier03) IMF. They reach $\rm SFR_{IR} = 59~M_{\odot}~\rm yr^{-1}$ to $283~M_{\odot}~\rm yr^{-1}$, with three upper limits below $57~M_{\odot}~\rm yr^{-1}$ (Table [\[tab:COdust-properties\]](#tab:COdust-properties)). The resulting total SFR ($\rm SFR_{UV+IR} = SFR_{UV}+SFR_{IR}$) place our galaxies well above the MS of star-forming galaxies at similar $z\sim 2.5$ and with similar stellar masses, with very high MS offsets of $\rm \Delta MS = SFR_{UV+IR}/\langle SFR_{\rm MS}\rangle \sim 30$ (cite: Speagle+14; Leslie+20). Obviously, the offsets could be lower in presence of old, yet currently poorly evidenced, stellar populations (Sect. [2](#sect:targets)).

![](SFRIR-SFRUV.pdf)

In Fig. [2](#fig:SFRIR-SFRUV) we show the comparison of the unobscured $\rm SFR_{UV}$ and obscured $\rm SFR_{IR}$ of our galaxies. The bulk of these extreme starbursts are dominated by the unobscured $\rm SFR_{UV}$ and have obscured fractions of star formation ($f_{\rm obscured} = \rm SFR_{IR}/SFR_{UV+IR}$) ranging between $\lesssim 14$% and 42%. Only three galaxies, J0006+2452, J0950+0523, and J1157+0113, have $f_{\rm obscured}$ moderately above 50%, with at most 57%. Based on different galaxy samples and exploring the possible effects of the assumed FIR SED template in the determination of $\rm SFR_{IR}$ values, (cite: Whitaker+17) showed that $f_{\rm obscured}$ is highly mass dependent but redshift independent for galaxies at $0<z<2.5$. Half of our extreme starburst galaxies follows their $f_{\rm obscured}$–$M_{\rm stars}$ relation, while the other half of galaxies with $f_{\rm obscured} < 25$% is located a factor of two below the empirical relation. The latter galaxies have among the lowest $f_{\rm obscured}$ measurements known at their $M_{\rm stars}$, and this even in comparison to stacks of UV-selected galaxies at $z\sim 5$ (cite: Fudamoto+20b) and $z\sim 7$ (cite: Algera+23). The deviation from the mean $f_{\rm obscured}$–$M_{\rm stars}$ relation would be all the more significant if the stellar masses of our galaxies are underestimated (see Sect. [2](#sect:targets)). Among these low $f_{\rm obscured}$ galaxies, we find the two strong LyC leaking galaxies, J0121+0025 and J1316+2614, at $z>3$ (cite: Marques+21; Marques+22), both with FIR dust continuum detections.

In Fig. [3](#fig:IRX-betaUV) we show the IR excess (${\rm IRX} = L_{\rm IR}/L_{\rm UV}$) as a function of the UV spectral slope of our galaxies. This is another empirical relation commonly studied for star-forming galaxies used to evaluate their dust attenuation, which does not evidence significant redshift evolution at least for galaxies at $z\lesssim 4$ (cite: Meurer+99; Whitaker+14; Bouwens+16; Fudamoto+17; Alvarez+16; Alvarez+19). In comparison to the existing galaxy samples around the cosmic noon era, our galaxies are characterised by very blue $\beta_{\rm UV} < -1.8$ and low $\rm IRX < +0.5$ because of their particularly high $L_{\rm UV}$ dominating over the LIRG/ULIRG regime. These two characteristics are more typical of very high redshift UV-selected galaxies at $z\sim 4.5-7.7$ (cite: Fudamoto+20b; Inami+22; Bowler+24); in particular, mean $\beta_{\rm UV}$ between $-2.2$ and $-2.6$ were derived from about a thousand of $5 < z <13$ galaxies (cite: RobertsBorsani+24; Heintz+24). As a result, similarly to the $z\sim 4.5-7.7$ galaxies, most of our galaxies deviate from the canonical IRX–$\beta_{\rm UV}$ relation derived by (cite: Meurer+99) for nearby starburst galaxies with an intrinsic UV continuum slope $\beta_0 = -2.23$ (solid line in Fig. [3](#fig:IRX-betaUV)). (cite: Reddy+18) computed IRX–$\beta_{\rm UV}$ relations assuming a constant star formation with an age of 100 Myr and including nebular continuum emission for a low stellar metallicity of $Z= 0.14~Z_{\odot}$, assumed to better characterise high redshift galaxies expected to have different physical conditions from nearby starburst galaxies with younger stellar populations and lower metallicities, yielding bluer $\beta_0 = -2.62$ relative to the canonical relation of (cite: Meurer+99). The resulting IRX–$\beta_{\rm UV}$ predictions with $\beta_0 = -2.62$ were found to agree with stacks of UV-selected galaxies at $z>4.5$ (cite: Fudamoto+20b). In Fig. [3](#fig:IRX-betaUV) we show the corresponding IRX–$\beta_{\rm UV}$ predictions obtained for the Small Magellanic Cloud (cite: Gordon+03) extinction curve (dashed line) and the (cite: Calzetti+00) attenuation curve (dotted line). For three of our galaxies we observe a good match with the SMC and $\beta_0 = -2.62$ prediction, although the (cite: Meurer+99) IRX–$\beta_{\rm UV}$ relation remains consistent within the measurement uncertainties. Six galaxies are clearly offset to bluer $\beta_{\rm UV}$ values, and are most precisely reproduced by the (cite: Calzetti+00) and $\beta_0 = -2.62$ prediction.

![](IRX-betaUV.pdf)

Another well-studied empirical relation that links dust attenuation and stellar masses of galaxies is the IRX–$M_{\rm stars}$ relation, which is expected because $M_{\rm stars}$ is the outcome of past star-formation activity responsible for producing dust in supernovae (SNe) and pulsating moderate-mass asymptotic giant branch (AGB) stars, and is also suggested by simulations (cite: Graziani+20). Different parametrisations are reported for samples of MS galaxies at $z\sim 1.5-4$, showing, on average, that MS galaxies follow a relatively tight and shallow IRX–$M_{\rm stars}$ correlation with small variations from one sample to another (cite: Heinis+14; Bouwens+16; Alvarez+16; Koprowski+18), with the exception of the study of (cite: Fudamoto+20a) where they report a significantly steeper IRX–$M_{\rm stars}$ relation for their sample of $z=2.5-4.0$ MS galaxies. Starburst galaxies at similar redshifts are found above the IRX–$M_{\rm stars}$ relation of MS galaxies with $\sim +0.5$ dex higher IRX values, indicating that starbursts are more dust extinct at a fixed $M_{\rm stars}$ (cite: Fudamoto+20a). Our extreme starburst galaxies are among the few galaxies known with individual IRX measurements at stellar masses as low as $\log(M_{\rm stars}/M_{\odot}) = 9.17-9.66$. Half of them follows more or less the shallow IRX–$M_{\rm stars}$ parametrisation, and the other half lies in between, that is, above the steep (cite: Fudamoto+20a) parametrisation and below the shallow parametrisation, and even below the parametrisation from (cite: Heinis+14) specifically derived from stacks of high $L_{\rm UV}$ MS galaxies ($\log L_{\rm UV}/L_{\odot} = 10.64-10.94$, which, nevertheless, are lower than the UV luminosities of our galaxies). Consequently, the currently still debated IRX–$M_{\rm stars}$ relation of MS galaxies, particularly for low stellar masses ($M_{\rm stars}/M_{\odot}<10^{10}$), makes it difficult to bring definitive conclusions on the dust attenuation of our extreme starburst galaxies with respect to MS galaxies with similar $M_{\rm stars}$. Globally, our galaxies populate the IRX and $M_{\rm stars}$ parameter space encompassed by the relations extrapolated from individual measurements and stacks of different samples of more massive MS galaxies at comparable redshifts. Nevertheless, they seem to agree particularly well with the new IRX–$M_{\rm stars}$ parametrisation recently derived by (cite: Bowler+24) for the very high redshift galaxies ($z\sim 4.5-7.7$).

## Molecular gas mass content and depletion timescale

The measurements (and upper limits) of the molecular gas masses of our galaxies, derived from the CO(3–2) or CO(4–3) luminosities, range between $M_{\rm molgas} <0.63\times 10^{10}~M_{\odot}$ and $3.67\times 10^{10}~M_{\odot}$ when derived with $\alpha_{\rm CO}^{\rm SB}$ (Table [\[tab:COdust-properties\]](#tab:COdust-properties)).

As shown in Fig. [4](#fig:Mmol-SFR), whatever $\alpha_{\rm CO}$, our extreme starburst galaxies have significantly higher $\rm SFR_{UV+IR}$ than MS galaxies at comparable $M_{\rm molgas}$, or, inversely, have significantly lower $M_{\rm molgas}$ than MS galaxies at comparable $\rm SFR_{UV+IR}$ (if these latter exist). This is in line with the integrated Kennicutt-Schmidt (KS) star-formation law and its $M_{\rm molgas}$–SFR parametrisations determined by (cite: Sargent+14) for MS galaxies (solid line in Fig. [4](#fig:Mmol-SFR) derived from nearby and cosmic noon galaxies) and starburst galaxies (dashed line in Fig. [4](#fig:Mmol-SFR) derived from nearby and $z<0.1$ ULIRGs), as also reported by (cite: Daddi+10) and (cite: Genzel+10). Our galaxies actually represent the first sample of high redshift galaxies that shows an offset from MS galaxies high enough, when assuming $\alpha_{\rm CO}^{\rm SB}$, to lie on the starburst $M_{\rm molgas}$–SFR relation offset by more than 1 dex from the MS relation. Both the sample of massive starburst galaxies at $z\sim 1.6$ studied by (cite: Silverman+15; Silverman+18) and SMGs at $z\sim 1-5$ (cite: Bothwell+13; CalistroRivera+18; Liu+19; Castillo+23) do not reach the starburst star-formation regime even with $\alpha_{\rm CO}^{\rm SB}$ . On the other hand, our galaxies still satisfy the empirical relation defined between $L_{\rm IR}$ and $L^{\prime}_{\rm CO(1-0)}$ established for diverse galaxy types from nearby galaxies (disks, dwarfs, starbursts) to ULIRGs, MS galaxies, SMGs, and quasars at $z\sim 0-5$ (cite: CarilliWalter13; Dessauges+15). This means that, for their IR luminosities, our starburst galaxies have the expected CO luminosities. They thus end up in the extreme starbursting regime mostly because of their very high unobscured $\rm SFR_{UV}$ (see also Sect. [4.1](#sect:obscured-SFR)).

![](Mmol-SFR.pdf)

![image](tdepl-z.pdf) ![image](fmolgas-z.pdf)

The high $\rm SFR_{UV+IR}$ of our galaxies

yield very short molecular gas depletion timescales ($t_{\rm depl} = M_{\rm molgas}/\rm SFR_{UV+IR}$) with a mean of $\rm 49~Myr \pm 12~Myr$ for $\alpha_{\rm CO}^{\rm SB}$ (Table [\[tab:COdust-properties\]](#tab:COdust-properties)).

As shown in the left panel of Fig. [5](#fig:tdepl-fmol-z), these $t_{\rm depl}$ are significantly shorter by more than one order of magnitude than those measured in MS galaxies at any redshift (cite: Bethermin+15; Liu+19; Tacconi+20; Dessauges+20). They are also shorter than those reported for the massive starburst galaxies at $z\sim 1.6$ with their mean $t_{\rm depl} \sim 60~\rm Myr$ (cite: Silverman+15; Silverman+18) and for the SMGs with their mean $t_{\rm depl} \sim 200~\rm Myr$ (cite: Bothwell+13; CalistroRivera+18; Castillo+23), considering the same $\alpha_{\rm CO}^{\rm SB}$. The upper limit on $t_{\rm depl}$ derived for J1316+2614, our highest redshift galaxy, even suggests that all its molecular gas mass ($M_{\rm molgas} < 6.3\times 10^9~M_{\odot}$) is depleted in $<13$ Myr! This remains true despite the uncertain $L_{\rm IR}$ measurements (Sect. [3.3](#sect:continuum)) affecting $\rm SFR_{UV+IR}$: if $\rm SFR_{UV+IR}$ are underestimated the $t_{\rm depl}$ values would be even shorter, and if, on the other hand, $\rm SFR_{UV+IR}$ are overestimated they would need to be overestimated by a factor of more than 10 to bring our galaxies to the $t_{\rm depl}$ values of MS galaxies at similar redshifts, which is implausible as $\rm SFR_{UV+IR}$ are dominated by $\rm SFR_{UV}$ and not by the uncertain $\rm SFR_{IR}$. Consequently, our extreme starburst galaxies are really vigorously consuming their molecular gas mass reservoir and are rapidly building up their stellar mass.

In the right panel of Fig. [5](#fig:tdepl-fmol-z) we show the molecular gas mass fractions ($f_{\rm molgas} = M_{\rm molgas}/(M_{\rm molgas}+M_{\rm stars})$) of our galaxies as a function of redshift that we compare to MS galaxies. We observe that our galaxies have very high $f_{\rm molgas}$ with a mean of $82\%\pm 10\%$ for $\alpha_{\rm CO}^{\rm SB}$ (Table [\[tab:COdust-properties\]](#tab:COdust-properties)). This reveals that their baryonic mass is dominated by the cold molecular gas mass over the stellar mass, with the mean molecular gas mass to stellar mass ratio ($\mu_{\rm molgas} = M_{\rm molgas}/M_{\rm stars}$) of $6\pm 3$,

and this despite the observed very rapid molecular gas consumption timescales (Fig. [5](#fig:tdepl-fmol-z), left panel). This suggests that our extreme starburst galaxies are caught at the very beginning of their stellar mass build-up, or that cosmic gas inflows are actively feeding these galaxies. The measured $f_{\rm molgas}$ of our galaxies are in significant excess with respect to those of MS galaxies at similar redshifts, and still higher than those of MS galaxies with similar $M_{\rm stars}$ (and $z$) despite the existing steep $f_{\rm molgas}$–$M_{\rm stars}$ anticorrelation (cite: Bethermin+15; Liu+19; Tacconi+20; Dessauges+20). The stellar masses of our galaxies would need to be underestimated by, on average, a factor of $\sim 3-4$ to reach the upper end of the $f_{\rm molgas}$ distribution of MS galaxies at $z\sim 2.5$. The same is true for them to reach the mean $f_{\rm molgas} \sim 50\%$ of the massive starburst galaxies at $z\sim 1.6$ of (cite: Silverman+15; Silverman+18) and even more to reach the mean $f_{\rm molgas} \sim 40\%$ of SMGs (cite: Bothwell+13; CalistroRivera+18; Castillo+23), considering the same $\alpha_{\rm CO}$.

## Star-formation efficiency

Our extreme starburst galaxies are dominated by very young stellar populations of $\sim 10$ Myr, with the bulk of their stellar mass being assembled within this short timescale given the absence of relevant old stellar populations, as described in Sect. [2](#sect:targets). (cite: Upadhyaya+24), moreover, showed that their rest-frame UV spectra resemble those of nearby young star clusters (R136–(cite: Crowther+16) and SB179 (cite: Senchyna+17)) and the Sunburst star cluster at $z\simeq 2.4$ (cite: Mestric+23). As a result, in contrast to most of the galaxies at cosmic noon whose stellar populations are a mixed bag of young and old populations dominated by old populations, our galaxies represent rare objects whose stellar populations are dominated by young populations representing $> 30$% to 62% of the total stellar mass of our galaxies (cite: Marques+20b; Marques+21; Marques+22; Marques+24).

We can thus measure the star-formation efficiency ($\epsilon_{\rm SF}$) of our galaxies, defined as the fraction of molecular gas mass converted into the recently formed stellar mass, namely here over the past $\sim 10$ Myr, following $\epsilon_{\rm SF} = M_{\rm stars}^{\rm young}/(M_{\rm molgas}+M_{\rm stars}^{\rm young})$ (cite: Evans+09; Dessauges+19; Dessauges+23). We find $\epsilon_{\rm SF}$ ranging from 8% to 37% (Table [\[tab:COdust-properties\]](#tab:COdust-properties)), with a mean of $18\% \pm 9\%$ for $\alpha_{\rm CO}^{\rm SB}$. J1249+1550 has the highest measured $\epsilon_{\rm SF}$ approaching 40%, together with J1316+2614 with its lower limit $\epsilon_{\rm SF} > 40$%. They both are associated with very short molecular gas depletion timescales of 36 Myr and $<13$ Myr, respectively, among the shorter in our galaxy sample (Table [\[tab:COdust-properties\]](#tab:COdust-properties)). One needs to keep in mind that the derived $\epsilon_{\rm SF}$ likely are lower limits, as we do not know whether all the measured $M_{\rm molgas}$ is associated with the star formation taking place in the compact starburst UV-bright component of our galaxies revealed by the HST and HAWK-I rest-frame UV/optical images (see Sect. [4.6](#sect:UVmorphology)).

The derived $\epsilon_{\rm SF}$ of our extreme starburst galaxies are higher in comparison to those of a few percent only ($\lesssim 5$%) measured in nearby galaxies (cite: Schruba+19; Utomo+18; Kim+23). On the other hand, they agree with the $\epsilon_{\rm SF}$ values of $\sim 30$% inferred for two strongly lensed MS galaxies at $z\simeq 1$ from the analysis of giant molecular clouds and their association with star-forming regions (cite: Dessauges+19; Dessauges+23). These enhanced $\epsilon_{\rm SF}$ are comparable to those proposed in ultra-massive ($M_{\rm stars} > 10^{11}~M_{\odot}$) optically dark and quenched galaxies recently discovered at $z\sim 5-6$ (cite: Xiao+24; deGraaff+24), whose existence can be explained by invoking very high star-formation efficiencies ($\gtrsim20$% to 100%). Similarly, (cite: Weibel+24) suggested that an increasing $\epsilon_{\rm SF}$ with redshift, reaching values of $\epsilon_{\rm SF}\sim 30$% at $z\sim 7-8$, is required to explain the high-mass end of the stellar mass functions at $z\geq 4-9$ as determined with JWST observations. On the simulation side, MillenniumTNG simulations also find that $\epsilon_{\rm SF}$ of about $10\%-30$% are necessary in the early Universe to solve the observed excess of luminous/massive galaxies at $z\gtrsim 8$ discovered with JWST (cite: Kannan+23). Values of $\epsilon_{\rm SF}\geq 57$% are even invoked by (cite: Boylan23) to reconcile the standard $\Lambda$CDM cosmological model with the observed excess.

## Dust mass content

The detected dust continuum emission in the Rayleigh-Jeans tail of the FIR SED ($\lambda_{\rm rest}>230~\mu$m) was used to estimate the dust mass content of our galaxies, as described in Sect. [3.3](#sect:continuum). However, the derived $M_{\rm dust}$ ranging from $<1.1\times 10^7~M_{\odot}$ to $1.1\times 10^8~M_{\odot}$ (Table [\[tab:COdust-properties\]](#tab:COdust-properties)) have to be considered with some caution given their large uncertainties coming from the poorly constrained FIR SED with one single band continuum measurement and the large number of free parameters entering in the dust composition models. The corresponding dust-to-gas mass ratios ($\delta_{\rm DGR} = M_{\rm dust}/M_{\rm molgas}$) are spread out between $\log (\delta_{\rm DGR}) < -2.9$ and $-2.1$ for $\alpha_{\rm CO}^{\rm SB}$.

This spread is comparable to the dispersion of $\delta_{\rm DGR}$ measurements reported in the literature at a given metallicity and the various extrapolated $\delta_{\rm DGR}$–metallicity relations that diverge even more at $12+\log(\rm O/H) < 8$ (cite: Magdis+12; RemyRuyer+14; DeVis+19; Popping+23; Valentino+24). The observed $\delta_{\rm DGR}$–metallicity correlation is also found in semi-analytic models of galaxy formation that include the tracking of dust formation and destruction over cosmic time (cite: Popping+17). Globally, the inferred $\delta_{\rm DGR}$ of our galaxies lower than $10^{-2}$ (the typical $\delta_{\rm DGR}$ value measured around solar metallicity) favour sub-solar metallicities in agreement with the metallicity measurements of our galaxies ($12+\log(\rm O/H) = 8.13-8.49$; Sect. [2](#sect:targets)).

In Fig. [6](#fig:Mdust-Mstars) we compare the dust masses of our extreme starburst galaxies to different empirical $M_{\rm dust}$–$M_{\rm stars}$ relations presented in (cite: Kororev+21) for MS galaxies at similar redshifts but extrapolated from more massive galaxies ($\log(M_{\rm stars}/M_{\odot}) > 10$). Our galaxies agree with the $M_{\rm dust}$–$M_{\rm stars}$ relation derived by (cite: Magnelli+20) as shown by the solid black line, but are well below the relations of (cite: Liu+19) and (cite: Kororev+21) shown by the dotted and dashed black lines, respectively, which predict much higher $M_{\rm dust}$ for the low-$M_{\rm stars}$ MS galaxies at $z\sim 2.5$. The $M_{\rm dust}$ estimates of our extreme starburst galaxies in fact resemble those of $z\sim 4-7$ galaxies with comparable stellar masses (cite: Pozzi+21; Sommovigo+22; Witstok+23; Valentino+24).

![](Mdust-Mstars.pdf)

The efficiency of dust production of our galaxies can be assessed by comparing their $M_{\rm dust}$ and $M_{\rm stars}$ with dust production models. In Fig. [6](#fig:Mdust-Mstars) the grey shaded zone defines the SN dust production as predicted by the model of (cite: GallHjorth18), which assumes that the dust is produced during a star-formation episode lasting over $\Delta t$ with a mean SFR and with SNe (or their massive star progenitors[^3]) producing a fraction $\eta$ of solar masses of dust, with the rate of SNe being proportional to SFR with the proportionality factor $\gamma$; such that the produced dust mass can be expressed as $M_{\rm dust} = \gamma \eta {\rm SFR} \Delta t$. (cite: GallHjorth18) computed the dust productivity $\mu_{\rm dust} = \gamma \eta$ and derived $\mu_{\rm dust} = 0.004\pm 0.002$ for the (cite: Chabrier03) IMF. The product ${\rm SFR} \Delta t$ gives the stellar mass assembled during the star-formation episode, which for our galaxies is computed over a burst age of $\sim 10~\rm Myr$ as described in Sect. [2](#sect:targets). The SN dust production can hence be expressed as $M_{\rm dust} = (0.004\pm 0.002) M_{\rm stars}$. This simple model indicates that SNe (or massive stars) alone barely produce enough dust (without considering dust destruction) during the short burst timescale of our extreme starburst galaxies (see the grey shaded zone in Fig. [6](#fig:Mdust-Mstars)) to enable to reproduce their dust masses. For four galaxies, despite their big and conservative $M_{\rm dust}$ uncertainties (Sect. [3.3](#sect:continuum)), their $M_{\rm dust}$ measurements even clearly step outside the predicted SN dust production, unless a top-heavy IMF is invoked, or the (young) stellar masses of these galaxies are underestimated by a factor of up to $\sim 4$. On longer timescales, but relatively rapidly (for $\Delta t\gtrsim 40~\rm Myr$), AGB stars start to contribute to the dust production in addition to SNe (cite: SchneiderMaiolino24), as delimited by the thick dash-dotted green line in Fig. [6](#fig:Mdust-Mstars) derived by (cite: Witstok+23). With respect to other dust formation models, only those by (cite: Imara+18) and (cite: Vijayan+19) predict the formation of enough dust to reproduce $M_{\rm dust}$ of all the low-$M_{\rm stars}$ galaxies in our sample; models of (cite: Popping+17) at $z\sim 2-3$ globally follow the same trend as the SN dust production of (cite: GallHjorth18).

## FIR dust continuum and rest-frame UV/optical sizes

The FIR dust continuum sizes were measured in the *uv* plane for seven galaxies of our sample using the ALMA 1.3 mm band 6 observations (Sect. [3.3](#sect:continuum)). They range between $R_{\rm eff,FIR} = 1.7$ kpc and 5.0 kpc (Table [\[tab:FIRdata\]](#tab:FIRdata)), and are shown as a function of $L_{\rm IR}$ in Fig. [7](#fig:R-LIR). The dependence of the FIR dust sizes of high redshift galaxies ($1<z<6$) on $L_{\rm IR}$ is still debated between, on one hand, the positive correlation (plotted as the dark-grey shaded area) reported by (cite: Fujimoto+17) that is in line with the stellar rest-frame UV size–luminosity correlation for star-forming galaxies (cite: Shibuya+15), and, on the other hand, the anti-correlation (light-grey shaded area) proposed by (cite: Jin+22). In both studies, the big $R_{\rm eff,FIR}$ $1\,\sigma$ scatter ($\sim 0.3-0.5~\rm dex$) at a given $L_{\rm IR}$ weakens the significance of the respective correlations. We observe that $R_{\rm eff,FIR}$ of our galaxies, on average, better agree with the relation of (cite: Jin+22).

A dependence of $R_{\rm eff,FIR}$ on stellar mass was also reported for massive galaxies at $1.5<z<4.5$ by (cite: Gomez+22) as shown in Fig. [8](#fig:R-Mstars) by the solid and dashed black lines at $z<2.5$ and $z>2.5$, respectively. Its slope is comparable to the slope of the stellar rest-frame UV effective radius versus $M_{\rm stars}$ relation derived for late-type galaxies (LTG) at similar redshifts $z\sim 2.5$ (blue shaded area) but its normalisation is much lower by a factor of $\sim 3-4$ (cite: Wel+14). (cite: Fujimoto+17) also found that the FIR dust continuum sizes of high redshift galaxies are more compact than those at UV/optical wavelengths, albeit with a less different normalisation factor. Our galaxies have much higher $R_{\rm eff,FIR}$ (filled circles) with respect to the (cite: Gomez+22) relations, and in fact very much agree with the stellar rest-frame UV sizes of LTG at $z\sim 2.5$. TNG50 simulations from (cite: Popping+22) predict FIR dust continuum (850 $\mu$m rest-frame) sizes as a function of the stellar mass of MS galaxies from $z=1$ to $z=5$, which at $z\sim 2-3$ approximately match $R_{\rm eff,FIR}$ of our galaxies, but clearly overpredict the $R_{\rm eff,FIR}$–$M_{\rm stars}$ relations proposed by (cite: Gomez+22).

In Fig. [8](#fig:R-Mstars) we furthermore compare $R_{\rm eff,FIR}$ (filled circles) with the rest-frame UV or optical effective radii (filled stars) derived from our HAWK-I seeing-limited $H$-band or AO $K_{\rm s}$-band observations[^4], respectively (Sect. [3.4](#sect:HAWKI) and Table [\[tab:FIRdata\]](#tab:FIRdata)). We observe that half of our galaxies have $R_{\rm eff,UV/opt}$ in agreement with those of LTG at $z\sim 2.5$ (cite: Wel+14), and the other half is considerably more compact. However, globally, all our extremely UV-luminous galaxies have $R_{\rm eff,FIR}$ systematically higher than their $R_{\rm eff,UV/opt}$. As a result, the mean $R_{\rm eff,UV/opt}/R_{\rm eff,FIR} =0.43\pm 0.17$ ratio of our galaxies contrasts with what is reported in the literature for galaxies at comparable redshifts $1<z<4$, $R_{\rm eff,HST}/R_{\rm eff,ALMA} \sim 1.6$ and $\sim 2.4$ for, respectively, ALMA archival galaxies from (cite: Fujimoto+17) and massive galaxies from (cite: Franco+20). Our galaxies actually share one additional physical property in common with very high redshift UV-selected galaxies at $4.5<z<6$, because these latter are also characterised by relatively extended FIR dust continuum sizes with respect to the compact UV sizes ($\lesssim 1.5$ kpc) with $R_{\rm eff,HST}/R_{\rm eff,ALMA} = 0.39\pm 0.15$ as recently measured by (cite: Pozzi+24).

![](ReFIR-LIR.pdf)

## Rest-frame UV/optical morphology and spatial offsets

As shown in the middle-left panels of Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3), most of our extremely UV-luminous galaxies are characterised by a simple ‘roundish’ rest-frame UV or optical morphology with one main bright component with $R_{\rm eff,UV/opt}$ ranging from 0.79 kpc to 2.01 kpc (Table [\[tab:FIRdata\]](#tab:FIRdata)). Two galaxies, J0950+0523 and J1316+2614, are particularly compact with $R_{\rm eff,opt} < 0.74$ kpc and $< 0.55$ kpc, respectively, unresolved in the HAWK-I AO $K_{\rm s}$-band images. Only two galaxies, J0146–0220 and J0006+2452, show more complex rest-frame optical morphologies with one main bright and compact component with $R_{\rm eff,opt} < 0.8$ kpc (unresolved in HAWK-I AO $K_{\rm s}$-band observations), centred on the phase centre, and a more diffuse component extended over $>2$ kpc in radius and offset in one direction with respect to the main component. A second tiny component seems also to be present on top of the diffuse component in J0146–0220. The detected rest-optical diffuse emission can be interpreted as a possible signature of either a diffuse underlying old stellar population or diffuse outflowing gas as the HAWK-I $K_{\rm s}$-band emission can instead trace the nebular H$\alpha$ emission at the redshift of these two galaxies.

The recently acquired HST images of J1415+2036, J0850+1549, and J1316+2614 confirm that the rest-frame UV morphology of our extreme starburst galaxies is a mixed bag between one single component for J1316+2614 (cite: Marques+24) and multi-components with J1415+2036 and J0850+1549 showing, respectively, two and three very compact components (Marques-Chaves et al. in prep.) that are blended in ground-based observations (Figs. [1](#fig:contB6-CO_1) and [9](#fig:contB6-CO_2), middle-left panels).

The HST images also reveal that the extreme $L_{\rm UV}$ we measure mostly comes from a very compact component, which is barely resolved even at the HST resolution.

The galaxy J1316+2614 appears as the most extreme case in our sample, because it is composed of one single very compact HST component with an effective radius as small as $R_{\rm eff,UV}^{\rm HST} = 220\pm 12$ pc, co-spatial with the extended FIR dust continuum emission, and without any sign of underlying HST diffuse emission (cite: Marques+24).

![](ReFIR-ReHAWKI-Mstars.pdf)

In both J0146–0220 and J0006+2452 galaxies, the FIR dust continuum emission is co-spatial with the CO emission, but is offset from the main rest-optical component, whereas it aligns with the extended diffuse rest-optical emission. The offsets between the main rest-optical component and the FIR emission are $0.66\ensuremath{''}$ and $0.59\ensuremath{''}$, that is, about 5.5 kpc and 4.9 kpc, in J0146–0220 and J0006+2452, respectively. The possible origin of this offset is discussed in Sect. [5](#sect:discussion). J1249+1550 and J0850+1549 also seem to have their FIR emission slightly offset by $\lesssim 0.25-0.3\ensuremath{''}$ from the bright rest-optical and rest-UV emission, respectively, but these offsets remain within the synthesised beam and PSF uncertainties and need to be confirmed.

Thus, for seven out of nine galaxies one can assume that the UV/optical bright component is co-spatial with the more extended FIR emission and the CO emission (when detected) as shown in the middle-left and middle-right panels of Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3).

J1415+2036 and J0121+0025 show patchy CO emission peaks at $4-5\sigma$ significance level spread within $< 3\ensuremath{''}$ (i.e. $< 25$ kpc) around the phase centre (Figs. [1](#fig:contB6-CO_1) and [10](#fig:contB6-CO_3), middle-right panels). Their integrated CO line detections nevertheless seem relatively robust, especially for J1415+2036, as shown by their respective CO line spectra plotted in the right panels of Figs. [1](#fig:contB6-CO_1) and [10](#fig:contB6-CO_3). However, how this patchy CO emission with its relatively big spatial extent relates to the rest-frame UV/optical emission remains unclear, especially in J0121+0025 where the escaping LyC radiation (cite: Marques+21) needs to be reconciled with the presence of cold molecular gas. The other leaker, J1316+2614 (cite: Marques+22), is undetected in the CO emission with a stringent upper limit on its very depleted $M_{\rm molgas}<6.3\times 10^9~M_{\odot}$ (Fig. [4](#fig:Mmol-SFR)).

# Discussion

The studied sample consists of the 12 most UV-bright galaxies known at $z\simeq 2.1-3.6$ with $M_{\rm UV} = -23.40$ to $-24.65$ (Sect. [2](#sect:targets) and Table [\[tab:restUV-properties\]](#tab:restUV-properties)), surpassing by $2-3$ magnitudes the recently detected JWST UV-luminous galaxies at $7<z<16$ brighter than $M^{\star}_{\rm UV}$ (cite: Bouwens+23; Atek+23; Bunker+23; Casey+23; Castellano+24; Carniani+24). They also outshine by far the brightest stellar clusters known in the Sunburst ($M_{\rm UV} \sim -19$) at $z\simeq 2.4$ and Sunrise ($M_{\rm UV} \sim -18$) at $z\simeq 6$ galaxies (cite: Vanzella+22; Vanzella+23). They are dominated by very young stellar populations of $\sim 10$ Myr (as assessed from the rest-frame UV spectroscopy) and are powerful starbursts with a mean specific SFR (${\rm sSFR = SFR}/M_{\rm stars}$) of $\rm 112~Gyr^{-1}$ ($\pm 45~\rm Gyr^{-1}$), placing them $\sim 1.5$ dex above the MS for their redshifts and stellar masses ($M_{\rm stars} \sim (1.47-4.59)\times 10^9~M_{\odot}$). They show unattenuated starlight with blue UV spectral slopes between $\beta_{\rm UV} = -2.62$ and $-1.84$, similar to those observed in several UV-bright galaxies at $z>7$ (cite: RobertsBorsani+24; Heintz+24). They present complex gas kinematics showing signatures of outflows and inflows. Furthermore, they are not only very efficient at producing ionising radiation given their luminous $M_{\rm UV}$, but some of them leak high amounts of LyC photons (cite: Marques+21), including the record-holder J1316+2614 at $z=3.6122$ with a LyC escape fraction of $f_{\rm esc}{\rm (LyC)} \simeq 90\%$ (cite: Marques+22). In summary, our galaxies possibly experience very early stages of vigorous starbursts with a fast mode of stellar mass build-up, likely resembling the major bursts of star formation taking place in the UV-luminous galaxies recently discovered with JWST at the EoR.

The ALMA observations, analysed in this paper, furthermore reveal the relatively bright FIR dust continuum emission for nine of our galaxies, placing these extremely UV-luminous galaxies in the LIRG regime, and even the ULIRG regime for three galaxies, with $L_{\rm IR} = (5.9-28.3)\times 10^{11}~L_{\odot}$ (Table [\[tab:FIRdata\]](#tab:FIRdata)). All galaxies in the LIRG regime remain nevertheless dominated by the unobscured $\rm SFR_{UV}$, and half of them even have $f_{\rm obscured} < 25$%, much lower than UV-selected galaxies at $z\sim 4.5-7.7$ (Sect. [4.1](#sect:obscured-SFR)). The resulting IRX ratios together with the blue $\beta_{\rm UV}$ best match the IRX–$\beta_{\rm UV}$ relations determined for young stellar populations (Fig. [3](#fig:IRX-betaUV)), in line with their very young ages of $\sim 10$ Myr derived from rest-frame UV spectra.

Large amounts of CO molecular gas in eight of our galaxies are also shown by ALMA observations, with much higher (up to an order of magnitude) molecular gas masses than their stellar masses, yielding very high $f_{\rm molgas}$ between 63% and 92% (Table [\[tab:COdust-properties\]](#tab:COdust-properties) and Sect. [4.2](#sect:Mgas-tdepl)). In what follows we refer to the $M_{\rm molgas}$ measurements derived using the CO-to-H$_2$ conversion factor $\alpha_{\rm CO}^{\rm SB}$, but our conclusions do not change when considering the $\sim 4$ times higher $\alpha_{\rm CO}^{\rm MW}$ instead. $\epsilon_{\rm SF}$ reliably estimated for our galaxies thanks to their dominant very young ($\sim 10$ Myr) stellar populations, show that very efficient star formation is taking place in our galaxies with $\epsilon_{\rm SF}$ values reaching up to $\sim 40$% (Sect. [4.3](#sect:SFE)). Those are likely even higher if only part of the detected $M_{\rm molgas}$ is associated with the star formation ongoing in the compact UV-bright component of our galaxies. This can, in particular, be the case for galaxies showing spatial offsets between the main UV-bright component and CO emission, currently evidenced in J1415+2036 and J0121+0025

(Sect. [4.6](#sect:UVmorphology)). The high $\epsilon_{\rm SF}$ are a unique physical property characterising our galaxies together with their amazingly short $t_{\rm depl}$ between 36 Myr and 71 Myr (Table [\[tab:COdust-properties\]](#tab:COdust-properties) and Sect. [4.2](#sect:Mgas-tdepl)), which highlight a very efficient and fast conversion of gas into stars that can only result from the gas collapse within a very short free-fall time.

In their model, (cite: Dekel+23) suggest the formation of feedback-free starbursts (FFB) through the collapse of gas clouds within very short free-fall times, approaching the monolithic collapse model, in high density ($> 10^3~\rm cm^{-3}$ and $> 2\times 10^3~M_{\odot}~\rm pc^{-2}$) and low metallicity ($Z\leq 0.2~Z_{\odot}$) environments. This makes star formation very efficient, because the cloud collapse occurs before the onset of stellar winds and SNe feedback, allowing the formation of massive galaxies within a few millions of years; and this also makes galaxies appear blue with none to little dust attenuation. A significant fraction of gas mass ($\sim 80$%) is predicted to be in massive gas clouds shielded against feedback and which can hence participate in the FFB star formation.

More specifically, (cite: Li+24) showed that globally the star-formation history (SFH) in an FFB galaxy occurs in several generations separated by about 10 Myr, which consist of a peak of nearly simultaneous FFB starbursts lasting for about $2-5$ Myr and ending in low amounts of gas left over, followed by a period of gas accumulation until the onset of the following generation of bursts. The dispersion of the $f_{\rm molgas}$ and $\epsilon_{\rm SF}$ measurements could be linked to the different SFH evolutionary stages of our galaxies following this model.

The stellar mass surface densities of our galaxies, defined as $\Sigma M_{\rm stars} = M_{\rm stars}/(2\pi R_{\rm eff}^2)$, range between $\Sigma M_{\rm stars} = 80~M_{\odot}~\rm pc^{-2}$ and $1170~M_{\odot}~\rm pc^{-2}$ when measured with the ground-based rest-frame UV/optical effective radii listed in Table [\[tab:FIRdata\]](#tab:FIRdata). However, as discussed in Sect. [4.6](#sect:UVmorphology), the extreme $L_{\rm UV}$ of our galaxies emerge from a compact component which is unresolved in the HAWK-I images (even with AO; $R_{\rm eff,opt} < 0.8$ kpc) and is barely resolved in the recently acquired HST images with $R_{\rm eff,UV}^{\rm HST} = 220\pm 12$ pc measured in J1316+2614 (cite: Marques+24).

The derived $M_{\rm stars}$ also come from these compact UV-bright components (see Sect. [2](#sect:targets)), and represent $>30$% to $>62$% of the total stellar mass of our galaxies (cite: Marques+20b; Marques+21; Marques+22; Marques+24). As a result, the starbursting UV-bright components[^5], for an average $R_{\rm eff,UV}^{\rm HST} \sim 250$ pc, have very high $\Sigma M_{\rm stars} \sim (0.37-1.2)\times 10^4~M_{\odot}~\rm pc^{-2}$[^6] well in line with the surface density threshold required for an FFB to occur[^7] (cite: Dekel+23). Most of the physical properties of our extremely UV-bright galaxies at $z\sim 2.5$ actually seem to be naturally explained in the context of the FFB model, and this despite their $Z \sim 0.5~Z_{\odot}$ metallicities (cite: Upadhyaya+24) while the FFB model was so far validated at $Z\leq 0.2~Z_{\odot}$. However, the measured metallicities should reflect the chemical enrichment of the starbursts over the past $\sim 10$ Myr, potentially differing from the gas metallicity in the pre-FFB phase.

What furthermore needs to be understood is the relatively bright FIR dust continuum emission detected in nine of our galaxies (Sect. [4.4](#sect:Mdust)), and which we find co-spatial with the main rest-frame UV/optical component in seven galaxies (Sect. [4.6](#sect:UVmorphology)) in contrast with their very blue ($\beta_{\rm UV} < -1.84$) unattenuated starlight. A possible simple explanation could be geometrical, such that the UV-bright emission is located in front of the dust layer, hence appearing unaffected by dust obscuration. However, this specific geometrical alignment appears surprisingly too common given its high occurrence for seven out of nine galaxies.

Another interpretation could follow the (cite: Ferrara+23) model (cite: Ziparo+23; Ferrara24) which suggests a temporary removal of dust (and gas) cleared by radiation-driven outflows that develop when galaxy luminosities become super-Eddington, making galaxies appear UV brighter and bluer with very low dust attenuation ($A_{\rm V} \lesssim 0.02$), and having an impact on the occurrence of huge LyC leakage. All our galaxies (see Table [\[tab:restUV-properties\]](#tab:restUV-properties)) can potentially develop such radiation-driven outflows given their sSFR well above the super-Eddington $\rm sSFR > 25~Gyr^{-1}$ threshold[^8] computed by (cite: Ferrara24), in contrast to MS galaxies that reach this super-Eddington limit only at very high redshifts of $z>7$ (cite: Faisst+16; Bouwens+22b; Bradley+23; Stefanon+22; Stefanon+23).

Evidence of outflowing gas was reported in two of our galaxies so far, J1220+0842 (cite: Alvarez+21) and J0121+0025 (cite: Marques+21), from ISM absorption lines showing blueshifted centroids with respect to the systemic redshift by $-400~\rm km~s^{-1}$ and $-450~\rm km~s^{-1}$, respectively, in line with their Ly$\alpha$ profiles. The Ly$\alpha$ profiles of two other galaxies, J1249+1550 and J0850+1549, also support outflows. And, evidence of dust being possibly blown away in our galaxies

is maybe best highlighted in J0146–0220 and J0006+2452,

where the FIR emission is spatially offset from the main compact rest-optical component along with the diffuse rest-optical emission (Sect. [4.6](#sect:UVmorphology)). For the seven other galaxies with co-spatial FIR dust continuum emission, we can speculate that the dust is expelled out spherically creating a ‘hole’ in the FIR emission at the location of the UV-bright component and with a size of at least the UV-bright component’s radius ($R_{\rm eff,UV}^{\rm HST} \sim 250$ pc; see above), currently unresolved at the angular resolution of our ALMA observations. The recent discovery of the Ly$\alpha$ hole in J1316+2614 at the location of the stellar UV emission while the Ly$\alpha$ emission extends out to $\sim 6$ kpc (cite: Marques+24) provides support to a comparable FIR dust emission hole, because dust should follow the same distribution as the Ly$\alpha$ emission that is tracing neutral gas. Moreover, the particularly big $R_{\rm eff,FIR}>1.7$ kpc (higher than $R_{\rm eff,UV/opt}$) of the FIR dust emission of our galaxies (Table [\[tab:FIRdata\]](#tab:FIRdata)) are also in line with dust being pushed beyond the radius of $\sim 2-3$ kpc at which it becomes optically thin (cite: Ferrara24). Same is likely true for the gas that is also expected to be removed by outflows, and the CO emission is indeed found co-spatial with the FIR dust emission (Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3)). Nevertheless, we do not observe any evidence of outflowing molecular gas in any of the currently available CO line profiles (no broad CO line component is detected; see Figs. [1](#fig:contB6-CO_1), [9](#fig:contB6-CO_2), and [10](#fig:contB6-CO_3), right panels).

(cite: Menon+24) also demonstrated in their radiation hydrodynamical numerical simulations that localised starbursts can evacuate (local) surrounding dust/gas through radiation-driven outflows in very high stellar/gas surface density conditions ($\Sigma > 10^3~M_{\odot}~\rm pc^2$) in line with the $\Sigma M_{\rm stars}$ measured for our starbursting UV-bright components (see above). Their results are slightly different from the (cite: Ferrara+23) model which invokes a global galaxy-scale radiation-driven outflow, whereas their simulations suggest a picture where ‘localised’ outflows (at tens of parsecs scale) enable the UV-emitting stellar populations to be visible, while other regions can still be obscured, resulting in co-spatial UV/FIR emission when viewed with large apertures.

The origin of the dust detected in our galaxies remains to be explained. Dust could be produced by SNe at the end of the FFB phase, or have an independent origin before the onset of the FFB. As discussed in Sect. [4.4](#sect:Mdust), the inferred dust masses (Table [\[tab:COdust-properties\]](#tab:COdust-properties)) – however relatively uncertain since derived from single band continuum measurements at 1.3 mm – can barely be produced by SNe (or massive stars) during the $\sim 10$ Myr starburst phase (cite: GallHjorth18) for most of our galaxies and are clearly in excess in four galaxies,

at least with the standard (cite: Chabrier03) IMF. This suggests that some dust was probably already produced prior to the burst of star formation by an older stellar population (from AGB stars and previous SNe). However, the evidence of an old stellar population currently remains elusive. So far, the SED analysis supports the absence of significant old stellar populations in these galaxies (cite: Marques+20b; Marques+21; Marques+22; Marques+24), and the nature of the underlying diffuse rest-frame optical emission detected with HAWK-I in at least two galaxies, J0146–0220 and J0006+2452, still needs to be understood (Sect. [4.6](#sect:UVmorphology)).

Other dust production mechanisms can be invoked, such as the rapid grain growth in the galaxy ISM (cite: Graziani+20; Dayal+22; SchneiderMaiolino24) that would bypass the need of an old stellar population. Moreover, recently (cite: Higgins+23) reported that VMSs with masses of some $200~M_{\odot}$ can eject 100 times more heavy elements in their winds than $50~M_{\odot}$ stars and hence possibly produce more dust. Evidence of VMSs in some of our extreme starburst galaxies is obtained from the detection of intense and broad He ii $\lambda$1640 emission lines, with equivalent widths of $EW_0 = 3-5~\AA$ (cite: Upadhyaya+24; Marques+20b; Marques+21; Marques+22), that is, much stronger than that typically found in normal star-forming galaxies (cite: Shapley+03). Such high $EW_0$ are difficult to explain by standard stellar models with an IMF upper mass cut-off $M_{\rm upp} = 100~M_{\odot}$, but are reproduced well by evolutionary models and atmospheres of VMSs with masses from $100~M_{\odot}$ to $400~M_{\odot}$ (cite: Martins+22). If such populations including VMSs can produce sufficient amounts of dust as those observed in our galaxies remains to be worked out.

(cite: Marques+20b) speculated on the fate of these extreme starburst galaxies and proposed two scenarios. Either these are the progenitors of compact present-day ellipticals (cite: DekelBurkert14) in case the star formation quenches right after the starburst phase, or these are ultra-/hyper-luminous dusty star-forming galaxies (cite: Santini+10) caught in their very early evolutionary stage ($\sim 10$ Myr), before their dust-poor extremely UV-luminous phase gets obscured by dust, in case the intense SFR activity lasts over a few hundreds of millions of years if located in gas-rich environments. The $t_{\rm depl}$ measurements derived in this work now provide a constraint on the gas consumption timescales of our galaxies. They highlight that most of our galaxies have enough gas to sustain the SFR over a few dozens of millions of years, that is, a factor of around three to seven longer than the current $\sim 10$ Myr age of the burst. As a result, over these timescales they will more than triple their $M_{\rm stars}$, and produce large amounts of dust by more than tripling their $M_{\rm dust}$ just from the SN dust production (cite: GallHjorth18). They could hence turn into FIR-bright DSFGs, heavily obscured in the UV. On the other hand, galaxies with $t_{\rm depl}$ comparable to the burst age ($\sim 10$ Myr), and especially J1316+2614 with $t_{\rm depl} < 13$ Myr, are expected to quench rapidly by starvation even before reaching the SMG phase, likely representing the very initial phases in the evolution of massive quiescent galaxies.

# Summary and conclusions

In this study, we performed an analysis of the ALMA FIR 1.3 mm (240 GHz) dust continuum and the CO(3–2) or CO(4–3) emission of 12 starburst galaxies at $z=2.08-3.61$ selected for their extreme brightness in the rest-frame UV with absolute magnitudes $M_{\rm UV} = -23.4$ to $-24.7$.

We also analysed the HAWK-I seeing-limited $H$-band and AO $K_{\rm s}$-band images acquired for ten targets. The rest-frame UV and optical properties of seven of these targets have already been analysed in detail in previous works (cite: Marques+20b; Marques+21; Marques+22; Marques+24; Alvarez+21; Upadhyaya+24). All the galaxies are characterised by steep UV spectral slopes $\beta_{\rm UV}=-2.62$ to $-1.84$ and dominated by very young stellar populations of $\sim 10$ Myr, indicating that the bulk of their stellar mass $M_{\rm stars} = (1.47-4.59)\times 10^9~M_{\odot}$ was formed in an intense starburst phase over $\sim 10$ Myr given the absence of relevant old stellar populations. They have sub-solar metallicities ranging between $12+\log({\rm O/H}) = 8.13$ and 8.49. Signatures of very massive stars with masses from $100~M_{\odot}$ to $400~M_{\odot}$ are revealed in their rest-frame UV spectra (cite: Upadhyaya+24) from the strong and broad He ii $\lambda$1640 emission line (cite: Crowther+16; Martins+23; Schaerer+24), suggesting an IMF with possibly a higher upper mass cut-off and likely also boosting their $L_{\rm UV}$ (cite: Schaerer+24). Several targets in our sample present complex gas kinematics showing evidence of outflows and even inflows for one galaxy (J1316+2614). They are all strong producers of ionising radiation given their very luminous $M_{\rm UV}$, and two of them are identified as strong LyC leakers (J0121+0025 and J1316+2614). Placed at the EoR, these galaxies alone would be able to ionise their environment.

Detected in nine galaxies, the ALMA FIR dust continuum emission provides constraints on their IR luminosities, obscured $\rm SFR_{IR}$, and dust masses, and the CO emission detected in eight galaxies provides constraints on their molecular gas masses:

- With $L_{\rm IR} = (5.9-28.3)\times 10^{11}~L_{\odot}$ our galaxies populate the LIRG regime, and even the ULIRG regime for three galaxies. All the LIRG-type galaxies remain dominated by the unobscured $\rm SFR_{UV}$. For half of the galaxies, the obscured fractions of star formation are less than $25\%$, placing them a factor of two below the empirical $f_{\rm obscured}$–$M_{\rm stars}$ relation of (cite: Whitaker+17), that is, even below the UV-selected galaxies at $z\sim 4.5-7.7$ (cite: Fudamoto+20b; Algera+23).

- The resulting total $\rm SFR_{UV+IR}$ bring these UV-bright galaxies considerably above (a factor of $\sim 30$) the main sequence of star-forming galaxies for similar redshifts and stellar masses (cite: Speagle+14), confirming they are powerful starbursts with specific SFRs as high as $\rm sSFR = 48-191~Gyr^{-1}$.

- The blue UV spectral slopes and luminous $L_{\rm UV}$, implying $\rm IRX<+0.5$, shift our extreme starburst galaxies away from the canonical IRX–$\beta_{\rm UV}$ relation of (cite: Meurer+99) to relations expected for younger and lower metallicity stellar populations (cite: Reddy+18), in agreement with their $\sim 10$ Myr ages derived from rest-frame UV spectroscopy and sub-solar metallicities. Our galaxies are among the few with individual IRX measurements at their low stellar masses. They populate the IRX–$M_{\rm stars}$ parameter space between the relations found for main sequence galaxies at $z\sim 1.5-4$ when extrapolated to lower $M_{\rm stars}$ (cite: Bouwens+16; Fudamoto+20a) and agree best with the relation derived for very high redshift UV-selected galaxies at $z\sim 4.5-7.7$ (cite: Bowler+24), but they definitely disagree with starburst galaxies at comparable redshifts that have a much higher IRX at fixed $M_{\rm stars}$ (cite: Fudamoto+20a).

- The high dust masses $M_{\rm dust} = (2.3-11.1)\times 10^7~M_{\odot}$ of our galaxies (to be confirmed with a better FIR SED sampling) support an efficient dust production given their $\sim 10$ Myr ages. Indeed, SNe alone barely produce such dust amounts during this short timescale (cite: GallHjorth18) and even fail for four galaxies unless a top-heavy IMF is invoked. Other dust production mechanisms can be invoked, for instance the rapid grain growth in the ISM, VMSs, or AGB stars in the presence of an old stellar population that remains elusive (cite: SchneiderMaiolino24; Higgins+23).

- The dust-to-gas mass ratios of our UV-bright galaxies range between $<10^{-2.9}$ and $10^{-2.1}$ (for $\alpha_{\rm CO}^{\rm SB}$) and are consistent with different $\delta_{\rm DGR}$–$12+\log({\rm O/H})$ relations when extrapolated to their sub-solar metallicities (cite: Popping+23).

- Our extreme starburst galaxies are offset from the integrated KS $M_{\rm molgas}$–$\rm SFR_{UV+IR}$ relation of main sequence galaxies and match the starburst regime as defined by (cite: Sargent+14). Their high $\rm SFR_{UV+IR}$ with respect to their $M_{\rm molgas}$ give unprecedentedly short molecular gas depletion timescales between $t_{\rm depl} <13$ Myr and 71 Myr (for $\alpha_{\rm CO}^{\rm SB}$). On the other hand, their baryonic masses remain dominated by the cold molecular gas over stars, which results in very high molecular gas mass fractions between $f_{\rm molgas}  <60\%$ and 92% (for $\alpha_{\rm CO}^{\rm SB}$), in significant excess with respect to those of main sequence galaxies (cite: Tacconi+20). This suggests that these extreme starburst galaxies are caught at the very beginning of their intense starburst phase while vigorously consuming their still high molecular gas mass reservoir to build up their stellar mass.

- Dominated by very young stellar populations of $\sim 10$ Myr, we obtained direct star-formation efficiency measurements of our galaxies ranging from $\epsilon_{\rm SF} = 8$% to $>40\%$ (for $\alpha_{\rm CO}^{\rm SB}$); these are much higher than $\epsilon_{\rm SF} < 5$% measured in nearby galaxies (cite: Kim+23). The derived $\epsilon_{\rm SF}$ should even be considered as lower limits given that only a percentage of the detected CO gas may be involved in the ongoing star formation. These high $\epsilon_{\rm SF}$, together with very short $t_{\rm depl}$, highlight the amazingly efficient and fast conversion of gas into stars of these UV-bright galaxies.

- The FIR dust continuum effective radii of our galaxies range between $R_{\rm eff,FIR}=1.7$ kpc and 5 kpc, and are bigger than their $R_{\rm eff,UV/opt}$. The corresponding mean $R_{\rm eff,UV/opt}/R_{\rm eff,FIR} = 0.43\pm 0.17$ is in contrast to what is typically observed for galaxies at comparable redshifts (cite: Fujimoto+17) but in agreement with the size properties of very high redshift UV-selected galaxies at $4.5<z<6$ (cite: Mitsuhashi+24; Pozzi+24).

- Our extremely UV-luminous galaxies are mostly characterised by a simple rest-frame UV/optical morphology, as assessed from HAWK-I observations, composed of one main bright component with $R_{\rm eff,UV/opt} < 0.55$ kpc to 2.01 kpc.

  Only two galaxies, J0146–0220 and J0006+2452, have more complex rest-frame optical morphologies with one main bright compact component ($R_{\rm eff,opt} < 0.8$ kpc) and a diffuse component extended over $R_{\rm eff,opt} > 2$ kpc that is offset in one direction with respect to the main component. A second tiny component is also present in J0146–0220. The diffuse emission could either trace an underlying old stellar population or outflowing gas as the HAWK-I $K_{\rm s}$-band is contaminated by the nebular H$\alpha$ emission at the redshift of these two galaxies. HST images acquired for three of our galaxies confirmed the multi-component morphology (blended in the ground-based images) for two other galaxies, J1415+2036 and J0850+1549, whereas J1316+2614 remains composed of one single extremely UV-bright and compact component. All of these components are barely resolved even at the HST resolution (cite: Marques+24).

- For seven galaxies, the main rest-UV/optical bright component is co-spatial with the more extended FIR dust continuum emission and the CO emission (when detected). This is quite surprising given their very blue unattenuated starlight. Only two galaxies, J0146–0220 and J0006+2452, have their FIR and CO emissions offset from the main rest-optical component but aligned with the extended diffuse rest-optical emission.

The extremely UV-luminous galaxies studied in this paper are recognised as being among the brightest UV galaxies known with $M_{\rm UV} = -23.4$ to $-24.6$ and among the most powerful starbursts, harbouring very young stellar populations of about 10 Myr. Their high star-formation efficiencies and very short molecular gas depletion timescales, together with their still very high molecular gas masses dominating over their stellar masses, strongly suggest that these galaxies are caught at the very beginning of their stellar mass build-up in an incredibly intense, rapid, and efficient gas-to-stars conversion phase. We find that the feedback-free starburst model of (cite: Dekel+23) seems to be able to explain the unique physical properties of our galaxies through the collapse of gas clouds within very short free-fall times before the onset of stellar winds and SN feedback. However, in addition to this, our galaxies are characterised by a relatively bright FIR dust continuum emission that is found to be co-spatial with the main rest-UV/optical bright component in seven out of nine galaxies. This is in strong contrast with their blue unattenuated starlight, as one would rather expect the galaxy to be dust obscured. To reconcile these physical properties, the (cite: Ferrara+23) model of dust removal by radiation-driven outflows taking place above the super-Eddington threshold at the location of the starburst appears to be a viable option and would also explain the big FIR effective radii of our galaxies in comparison to their stellar effective radii (cite: Menon+24). Finally, the measured dust masses seem to require dust production mechanisms that are more rapid and efficient than SNe given the short 10 Myr timescale available for their formation.

While these extremely UV-luminous starburst galaxies are rare at $z = 2.1-3.6$, with only about 70 of them found in the $\sim 9000~\rm deg^2$-wide eBOSS survey, corresponding to a number density of $10^{-9}~\rm Mpc^{-3}$ (Marques-Chaves et al. in prep.), intrinsically they are certainly not so rare. The detection of some of them at $z>6$ (cite: Sobral+15; Matsuoka+18; Hashimoto+19) and, more recently, their unexpected overabundance discovered at $7<z<16$ with JWST, implying steeper UV luminosity functions than predicted (cite: Bouwens+23; Atek+23; Bunker+23; Casey+23; Castellano+24; Carniani+24), show that galaxies towards the EoR are more often experiencing such UV-luminous and still unobscured phases, with high sSFRs. As discussed in Sect. [1](#sect:introduction), different scenarios were invoked to explain the UV-luminous starburst galaxies at the EoR and their number excess. Among these scenarios are the very efficient star formation following the (cite: Dekel+23) model and the (cite: Ferrara+23) model of temporary dust removal as a consequence of radiation-driven outflows, for which the molecular gas and FIR dust continuum analysis of our galaxies provides some support. Alternatively, a modified IMF (towards a top-heavy one) boosting the UV radiation and the luminosity-to-mass ratio of galaxies was also proposed (cite: BekkiTsujimoto23; Trinca+24) as well as a stochastic variability of the SFR (cite: Mirocha+23; Gelli+24). Currently, we have no evidence supporting a modified IMF except possibly an IMF with a higher upper mass cut-off given that our galaxies host VMSs (cite: Upadhyaya+24) that can also lead to high UV luminosity increases (cite: Schaerer+24).

In summary, these galaxies show several similarities with the galaxies recently unveiled at the EoR with JWST. They hence possibly represent a sample of lower redshift ‘analogues’ that benefit from the advantage of a rich dataset and data to come that will be difficult to acquire for galaxies at $z>7$.

Our UV-bright galaxies at cosmic noon thus are ideal laboratories to test different scenarios proposed to explain what triggers the extreme UV luminosities and starbursts of galaxies and their number excess at the EoR.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00932.S and 2021.1.01438.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This paper is also based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programme 111.251K.001.

99

(ref: Abolfathi+18) Abolfathi, B., Aguado, D. S., Aguilar, G., et al. 2018, ApJS, 235, 42

(ref: Algera+23) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142

(ref: Alvarez+21) Álvarez-Márquez, J., Marques-Chaves, R., Colina, L., & Pérez-Fournon, I. 2021, A&A, 647, A133

(ref: Alvarez+19) Álvarez-Márquez, J., Burgarella, D., Buat, V., Ilbert, O., & Pérez-González, P. G 2019, A&A, 630, A153

(ref: Alvarez+16) Álvarez-Márquez, J., Burgarella, D., Heinis, S., et al. 2016, A&A, 587, A122

(ref: Atek+23) Atek, H., Shuntov, M., Furtak, L., et al. 2023, MNRAS, 519, 1201

(ref: Barro+17) Barro, G., Faber, M., Koo, D. C., et al. 2017 ApJ, 840, 47

(ref: Beelen+06) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694

(ref: BekkiTsujimoto23) Bekki, K., & Tsujimoto, T. 2023, MNRAS, 526, L26

(ref: Bertoldi+03) Bertoldi, F., Carilli, C. L., Cox, P., et al. 2003, A&A, 406, L55

(ref: Bethermin+15) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113

(ref: BianchiSchneider07) Bianchi, S., & Schneider, R. 2007, MNRAS, 378, 973

(ref: Bolatto+13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Boogaard+20) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109

(ref: Bouwens+22b) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022b, ApJ, 931, 160

(ref: Bouwens+22a) Bouwens, R. J., Illingworth, G. D., van Dokkum, P. G., et al. 2022a, ApJ, 927, 81

(ref: Bouwens+23) Bouwens, R. J., Stefanon, M., Brammer, G., et al. 2023, MNRAS, 523, 1009

(ref: Bouwens+16) Bouwens, R. J., Aravena, M., Decarli, R., et al. 2016, ApJ, 833, 72

(ref: Bothwell+13) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047

(ref: Bowler+24) Bowler, R. A. A., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 5808

(ref: Boylan23) Boylan-Kolchin, M. 2023, Nature Astron., 7, 731

(ref: Bradley+23) Bradley, L. D., Coe, D., Brammer, G., et al. 2023, ApJ, 955, 13

(ref: Bunker+23) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, A&A, 677, A88

(ref: Byrne+22) Byrne, C. M., Stanway, E. R., Eldridge, J. J., McSwiney, L., & Townsend, O. T. 2022, MNRAS, 512, 5329

(ref: CalistroRivera+18) Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56

(ref: Calzetti+00) Calzetti, D., Armus, L., Bohlin, R  C., et al. 2000, ApJ, 533, 682

(ref: CarilliWalter13) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105

(ref: Carniani+24) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024, Nature, 633, 318

(ref: Casey+23) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31

(ref: Casey+14) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: Casey12) Casey, C. M. 2012, MNRAS, 425, 3094

(ref: Castellano+24) Castellano, M., Napolitano, L., Fontana, A., et al. 2024, ApJ, 972, 143

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: Chemerynska+24) Chemerynska, I., Atek, H., Furtak, L. J., et al. 2024, MNRAS, 531, 2615

(ref: Claeyssens+23) Claeyssens, A., Adamo, A., Richard, J., Mahler G., Messa, M., & Dessauges- Zavadsky, M. 2023, MNRAS, 520, 2180

(ref: Crowther+16) Crowther, P. A., Caballero-Nieves, S. M., Bostroem, K. A., et al. 2016, MNRAS, 458, 624

(ref: daCunha+13) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: Daddi+15) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46

(ref: Daddi+10) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJL, 714, L118

(ref: Dayal+22) Dayal, P., Ferrara, A., Sommovigo, L., et al. 2022, MNRAS, 512, 989

(ref: deGraaff+24) de Graaff, A., Setton, D. J., Brammer, G., et al. 2024, \[arXiv:2404.05683\]

(ref: DekelBurkert14) Dekel, A., & Burkert, A. 2014, MNRAS, 438, 1870

(ref: Dekel+23) Dekel, A., Sarkar, K. C., Birnboim, Y., Mandelker, N., & Liet, Z. 2023, MNRAS, 523, 3201

(ref: Dessauges+23) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2023, MNRAS, 519, 6222

(ref: Dessauges+20) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5

(ref: Dessauges+19) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2019, Nature Astron., 3, 1115

(ref: Dessauges+17) Dessauges-Zavadsky, M., Zamojski, M., Rujopakarn, W., et al. 2017, A&A, 605, A81

(ref: Dessauges+15) Dessauges-Zavadsky, M., Zamojski, M., Schaerer, D., et al. 2015, A&A, 577, A50

(ref: Dessauges+11) Dessauges-Zavadsky, M., Christensen, L., D’Odorico, S., Schaerer, D., & Richard, J. 2011, A&A, 533, A15

(ref: Dessauges+10) Dessauges-Zavadsky, M., D’Odorico, S., Schaerer, D., et al. 2010, A&A, 510, A26

(ref: DeVis+19) De Vis, P., Jones, A., Viaene, S., et al. 2019, A&A, 623, A5

(ref: Cesare+23) Di Cesare, C., Graziani, L., Schneider, R., et al. 2023, MNRAS, 519, 4632

(ref: Eisenstein+11) Eisenstein, D. J., Weinberg, D. H., Agol, E., et al. 2011, AJ, 142, 72

(ref: Eldridge+17) Eldridge, J. J., Stanway, E. R., Xiao, L., et al. 2017, PASA, 34, 58

(ref: Endsley+21) Endsley, R., Stark, D. P., Chevallard, J., & Charlot, S. 2021, MNRAS, 500, 5229

(ref: Evans+09) Evans, N. J., II, Dunham, M. M., Jørgensen, J. K., et al. 2009, ApJS, 181, 321

(ref: Faisst+16) Faisst, A. L., Capak, P., Hsieh, B. C., et al. 2016, ApJ, 821, 122

(ref: Ferrara24) Ferrara, A. 2024, A&A, 684, A207

(ref: Ferrara+23) Ferrara, A., Pallottini, A., & Dayal, P. 2023, MNRAS, 522, 3986

(ref: Finkelstein+24) Finkelstein, S. L., Leung, G. C. K., Bagley, M. B., et al. 2024, ApJL, 969, L2

(ref: FinkelsteinBagley22) Finkelstein, S. L., & Bagley, M. B. 2022, ApJ, 938, 25

(ref: Castillo+23) Frias Castillo, M., Hodge, J., Rybak, M., et al. 2023, ApJ, 945, 128

(ref: Fudamoto+20b) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020b, A&A, 643, A4

(ref: Fudamoto+20a) Fudamoto, Y., Oesch, P. A., Magnelli, B., et al. 2020a, MNRAS, 491, 4724

(ref: Fudamoto+17) Fudamoto, Y., Oesch, P. A., Schinnerer, E., et al. 2017, MNRAS, 472, 483

(ref: Fujimoto+17) Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83

(ref: Franco+20) Franco, M., Elbaz, D., Zhou, L., et al. 2020, A&A, 643, A30

(ref: Gaia+23) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: GallHjorth18) Gall, C., & Hjorth, J. 2019, ApJ, 868, 62

(ref: Galliano+11) Galliano, F., Hony, S., Bernard, J.-P., et al. 2011, A&A, 536, A88

(ref: Gelli+24) Gelli, V., Mason, C., & Hayward, C. C. 2024, \[arXiv:2405.13108\]

(ref: Genzel+10) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091

(ref: Ginolfi+19) Ginolfi, M., Schneider, R., Valiante, R., et al. 2019, MNRAS, 483, 1256

(ref: Gomez+22) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 659, A196

(ref: Gordon+03) Gordon, K. D., Clayton, G. C., Misselt, K. A., Landolt, A. U., & Wolff, M. J. 2003, ApJ, 594, 279

(ref: Graziani+20) Graziani, L., Schneider, R., Ginolfi, M., et al. 2020, MNRAS, 494, 1071

(ref: Guilloteau+00) Guilloteau, S., & Lucas, R. 2000, in Astronomical Society of the Pacific Conference Series, Vol. 217, Imaging at Radio through Submillimeter Wavelengths, ed.s J. G. Mangum & S. J. E. Radford, 299

(ref: Hashimoto+19) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71

(ref: Heinis+14) Heinis, S., Buat, V., Béthermin, M., et al. 2014, MNRAS, 437, 1268

(ref: Heintz+24) Heintz, K. E., Brammer, G. B., Watson, D., et al. 2024, \[arXiv:2404.02211\]

(ref: Higgins+23) Higgins, E. R., Vink, J. S., Hirschi, R., Laird, A. M., & Sabhahit, G. N. 2023, MNRAS, 526, 534

(ref: Imara+18) Imara, N., Loeb, A., Johnson, B. D., Conroy, C., & Behroozi, P. 2018, ApJ, 854, 36

(ref: Inami+22) Inami, H., Algera, H. S. B, Schouws, S., et al. 2022, MNRAS, 515, 3126

(ref: Jin+22) Jin, S., Daddi, E., Magdis, G. E., et al. 2022, A&A, 665, A3

(ref: Jones+17) Jones, A. P., Köhler, M., Ysard, N., Bocchio, M., & Verstraete, L. 2017, A&A, 602, A46

(ref: Kannan+23) Kannan, R., Springel, V., Hernquist, L., et al. 2023, MNRAS, 524, 2594

(ref: Kennicutt98) Kennicutt, R. C. Jr. 1998, ARA&A, 36, 189

(ref: Kim+23) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2023, ApJL, 944, L20

(ref: Kororev+21) Kokorev, V. I., Magdis, G. E., Davidzon, I., et al. 2021, ApJ, 921, 40

(ref: Koprowski+18) Koprowski, M. P., Coppin, K. E. K., Geach, J. E., et al. 2018, MNRAS, 479, 4355

(ref: Leslie+20) Leslie, S. K., Schinnerer, E., Liu, D., et al. 2020, ApJ, 899, 58

(ref: Li+24) Li, Z., Dekel, A., Sarkar, K. C., et al. 2024, A&A, 690, A108

(ref: Liu+19) Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235

(ref: Magdis+12) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: Magnelli+20) Magnelli, B., Boogaard, L., Decarli, R., et al. 2020, ApJ, 892, 66

(ref: Maiolino+24) Maiolino, R., Scholtz, J., Witstok, J., et al. 2024, Nature, 627, 59

(ref: Marques+24) Marques-Chaves, R., Schaerer, D., Vanzella, E., et al. 2024, A&A, 691, A87

(ref: Marques+22) Marques-Chaves, R., Schaerer, D., Álvarez-Márquez, J., et al. 2022, MNRAS, 517, 2972

(ref: Marques+21) Marques-Chaves, R., Schaerer, D., Álvarez-Márquez, J., et al. 2021, MNRAS, 507, 524

(ref: Marques+20b) Marques-Chaves, R., Álvarez-Márquez, J., Colina, L., et al. 2020b, MNRAS, 499, L105

(ref: Marques+20a) Marques-Chaves, R., Pérez-Fournon, I., Shu, Y., et al. 2020a, MNRAS, 492, 1257

(ref: Marques+18) Marques-Chaves, R., Pérez-Fournon, I., Gavazzi, R., et al. 2018, ApJ, 854, 151

(ref: Marques+17) Marques-Chaves, R., Pérez-Fournon, I., Shu, Y., et al. 2017, ApJL, 834, L18

(ref: Martins+22) Martins, F., & Palacios, A. 2022, A&A, 659, A163

(ref: Martins+23) Martins, F., Schaerer, D., Marques-Chaves, R., & Upadhyaya, A. 2023, A&A, 678, A159

(ref: Mason+18) Mason, C. A., Treu, T., Dijkstra, M., et al. 2018, ApJ, 856, 2

(ref: Matsuoka+18) Matsuoka, Y., Onoue, M., Kashikawa, N., et al. 2018, PASJ, 70, S35

(ref: McMullin+07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Shaw R.A., Hill F., Bell D.J., eds, ASP Conf. Ser. Vol. 376, Astronomical Data Analysis Software and Systems XVI, Tucson, p. 127

(ref: Menon+24) Menon, S. H., Burkhart, B., Somerville, R. S., Thompson, T. A., & Sternberg, A. 2024, \[arXiv:2408.14591\]

(ref: Meurer+99) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64

(ref: Messa+24) Messa, M., Dessauges-Zavadsky, M., Adamo, A., Richard, J., & Claeyssens, A. 2024, MNRAS, 529, 2162

(ref: Mestric+23) Meštrić, U., Vanzella, E., Upadhyaya, A., et al. 2023, A&A, 673, A50

(ref: Mirocha+23) Mirocha, J., & Furlanetto, S. R. 2023, MNRAS, 519, 843

(ref: Mitsuhashi+24) Mitsuhashi, I., Tadaki, K.-i., Ikeda, R., et al. 2024, A&A, 690, A197

(ref: Naidu+22) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJL, 940, L14

(ref: Ouchi+08) Ouchi, M., Shimasaku, K., Akiyama, M., et al. 2008, ApJS, 176, 301

(ref: Patricio+16) Patrício, V., Richard, J., Verhamme, A. et al. 2016, MNRAS, 456, 4191

(ref: Peng+02) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266

(ref: Pettini+00) Pettini, M., Steidel, C. C., Adelberger, K. L., Dickinson, M., & Giavalisco, M. 2000, ApJ, 528, 96

(ref: Popping+23) Popping, G., Shivaei, I., Sanders, R. L., et al. 2023, A&A, 670, A138

(ref: Popping+22) Popping, G., Pillepich, A., Calistro Rivera, G., et al. 2022, MNRAS, 510, 3321

(ref: Popping+17) Popping, G., Somerville, R. S., & Galametz, M. 2017, MNRAS, 471, 3152

(ref: Pozzi+24) Pozzi, F., Calura, F., D’Amato, Q., et al. 2024, A&A, 686, A187

(ref: Pozzi+21) Pozzi, F., Calura, F., Fudamoto, Y., et al. 2021, A&A, 653, A84

(ref: Quider+10) Quider, A. M., Shapley, A. E., Pettini, M., Steidel, C. C., & Stark, D. P. 2010, MNRAS, 402, 1467

(ref: Quider+09) Quider, A. M., Pettini, M., Shapley, A. E., & Steidel, C. C. 2009, MNRAS, 398, 1263

(ref: ReddySteidel09) Reddy, N. A., & Steidel, C. C. 2009, ApJ, 692, 778

(ref: Reddy+18) Reddy, N. A., Oesch, P. A., Bouwens, R. J., et al. 2018, ApJ, 853, 56

(ref: RemyRuyer+14) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31

(ref: RobertsBorsani+24) Roberts-Borsani, G., Treu, T., Shapley, A., et al. 2024, \[arXiv:2403.07103\]

(ref: Robson+04) Robson, I., Priddey, R. S., Isaak, K. G., & McMahon, R. G. 2004, MNRAS, 351, L29

(ref: Santini+10) Santini, P., Maiolino, R., Magnelli, B., et al. 2010, A&A, 518, L154

(ref: Sargent+14) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19

(ref: Schaerer+24) Schaerer, D., Guibert, J., Marques-Chaves, R., & Martins, F. 2024, \[arXiv:2407.12122\]

(ref: SchneiderMaiolino24) Schneider, R., & Maiolino, R. 2024, A&ARv, 32, 2

(ref: Schreiber+18) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: Schruba+19) Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2

(ref: Senchyna+17) Senchyna, P., Stark, D. P., Vidal-García, A., et al. 2017, MNRAS, 472, 2608

(ref: Shapley+03) Shapley, A. E., Steidel, C. C., Pettini, M., & Adelberger, K. L. 2003, ApJ, 588, 65

(ref: Shibuya+15) Shibuya, T., Ouchi, M., & Harikane, Y. 2015, ApJS, 219, 15

(ref: Shu+16) Shu, Y., Bolton, A. S., Kochaneket, C. S., et al., 2016, ApJ, 824, 86

(ref: Silverman+18) Silverman, J. D., Rujopakarn, W., Daddi, E., et al. 2018, ApJ, 867, 92

(ref: Silverman+15) Silverman, J. D., Daddi, E., Rodighiero, G., et al. 2015, ApJL, 812, L23

(ref: Sobral+15) Sobral, D., Matthee, J., Darvish, B., et al. 2015, ApJ, 808, 139

(ref: Sobral+18b) Sobral, D., Matthee, J., Darvish, B., et al. 2018b, MNRAS, 477, 2817

(ref: Sobral+18a) Sobral, D., Santos, S., Matthee, J., et al. 2018a, MNRAS, 476, 4725

(ref: Solomon+97) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, ApJ, 478, 144

(ref: Sommovigo+22) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122

(ref: Speagle+14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Spilker+14) Spilker, J. S., Marrone, D. P., Aguirre, J. E., et al. 2014, ApJ, 785, 149

(ref: StanwayEldridge18) Stanway, E. R., & Eldridge, J. J. 2018, MNRAS, 479, 75

(ref: Stefanon+22) Stefanon, M., Bouwens, R. J., Labbé, I., et al. 2022, ApJ, 927, 48

(ref: Stefanon+23) Stefanon, M., Bouwens, R. J., Labbé, I., et al. 2023, ApJ, 943, 81

(ref: Tacconi+20) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: Trinca+24) Trinca, A., Schneider, R., Valiante, R., et al. 2024, MNRAS, 529, 3563

(ref: Upadhyaya+24) Upadhyaya, A., Marques-Chaves, R., Schaerer, D., et al. 2024, A&A, 686, A185

(ref: Utomo+18) Utomo, D., Sun, J., Leroy, A. K., et al. 2018, ApJL, 861, L18

(ref: Valentino+24) Valentino, F., Fujimoto, S., Giménez-Arteaga, C., et al. 2024, A&A, 685, A138

(ref: Valentino+20) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24

(ref: Wel+14) van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28

(ref: Vanzella+23) Vanzella, E., Claeyssens, A., Welch, B., et al. 2023, ApJ, 945, 53

(ref: Vanzella+22) Vanzella, E., Castellano, M., Bergamini, P., et al. 2022, A&A, 659, A2

(ref: Viero+22) Viero, M. P., Sun, G., Chung, D. T., Moncelsi, L., & Condon, S. S. 2022, MNRAS, 516, L30

(ref: Vijayan+19) Vijayan, A. P., Clay, S. J., Thomas, P. A., et al. 2019, MNRAS, 489, 4072

(ref: Weibel+24) Weibel, A., Oesch, P. A., Barrufet, L., et al. 2024, MNRAS, 533, 1808

(ref: WeingartnerDraine01) Weingartner, J. C., & Draine, B. T. 2001, ApJ, 548, 296

(ref: Whitaker+17) Whitekar, K. E., Alexandra Pope, A., Cybulski, R., et al. 2017, ApJ, 850, 208

(ref: Whitaker+14) Whitekar, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104

(ref: Witstok+23) Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023, MNRAS, 523, 3119

(ref: Xiao+24) Xiao, M.-Y., Oesch, P., Elbaz, D., et al. 2024, \[arXiv:2309.02492\]

(ref: Xiao+22) Xiao, M.-Y., Wang, T., Elbaz, D., et al. 2022, A&A, 664, A63

(ref: Zanella+18) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

(ref: Zheng+16) Zheng, Z.-Y., Malhotra, S., Rhoads, J. E., et al. 2016, ApJS, 226, 23

(ref: Ziparo+23) Ziparo, F., Ferrara, A., Sommovigo, L., & Kohandel, M. 2023, MNRAS, 520, 2445

# Figure 1 continued

![image](LBG1contB6.pdf) ![image](J0006contB6HAWKI.pdf) ![image](LBG1CO32B3mom0.pdf) ![image](LBG1CO32spec.pdf)

![image](SDSS0850contB6.pdf) ![image](J0850contB6CFHT.pdf) ![image](SDSS0850CO32B3mom0.pdf)

![image](LBG8contB6.pdf) ![image](J1220m0051contB6HAWKI.pdf) ![image](LBG8CO32B3mom0.pdf) ![image](LBG8CO32spec.pdf)

![image](LBG5contB6.pdf) ![image](J0950contB6HAWKI.pdf) ![image](LBG5CO32B3mom0.pdf) ![image](LBG5CO32spec.pdf)

![image](SDSS1220contB6.pdf) ![image](J1220p0842contB6HAWKI.pdf) ![image](SDSS1220CO32B3mom0.pdf)

![image](SDSS1157contB6.pdf) ![image](J1157contB6HAWKI.pdf) ![image](SDSS1157CO32B3mom0.pdf) ![image](SDSS1157CO32spec.pdf)

![image](LBG6contB6.pdf) ![image](J0121contB6Subaru.pdf) ![image](LBG6CO43B3mom0.pdf) ![image](LBG6CO43spec.pdf)

![image](LBG2contB6.pdf) ![image](J1316contB6HAWKI.pdf) ![image](LBG2CO43B3mom0.pdf)

[^1]: <https://www.eso.org/sci/software/pipelines/hawki/hawki-pipe-recipes.html>

[^2]: However, one needs to keep in mind that the HAWK-I images at the redshift of our galaxies are likely dominated by the strong rest-frame optical lines, \[O iii\]+H$\beta$ or H$\alpha$.

[^3]: The model of (cite: GallHjorth18) does not specify how exactly the dust is produced in SNe or in massive stars prior the SN explosion.

[^4]: For J0850+1549 and J0121+0025 we used the CFHT MegaCam and Subaru seeing-limited $R$-band observations, respectively.

[^5]: The corresponding $\rm SFR_{UV}$ surface densities of the UV-bright components are also huge with $\Sigma {\rm SFR_{UV}} \sim (0.27-1.1)\times 10^3~M_{\odot}~\rm yr^{-1}~kpc^{-2}$. Only a few massive stellar clusters at sub-10 pc scales, hosted in the Sunburst and Sunrise high redshift galaxies, have such extreme $\Sigma {\rm SFR_{UV}}$ (cite: Vanzella+22; Vanzella+23; Messa+24).

[^6]: Such high $\Sigma M_{\rm stars}$ were only reported for very few star-forming galaxies with similar $M_{\rm stars}$ and redshifts, and are more common for more massive compact star-forming galaxies (cite: Barro+17), as well as for young star-forming clumps at $1<z<3$ yet typically having two orders of magnitude lower stellar masses (cite: Claeyssens+23; Messa+24).

[^7]: For one of our galaxies, J1220+0842, (cite: Marques+20b) could even measure its density from the \[O ii\] $\lambda$3729/$\lambda$3726 and C iii\] $\lambda$1906/$\lambda$1908 line ratios that is $>10^3~\rm cm^{-3}$, namely in agreement with the FFB density threshold.

[^8]: The super-Eddington limit from (cite: Ferrara24) was reassessed by (cite: Li+24), who found that super-Eddington ejections potentially take place at $z>16$ only.

</paper>

Write the methods card for this paper.