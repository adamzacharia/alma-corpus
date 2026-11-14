# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1002....9L\sonnetcc\reply.txt

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
 "bibcode": "2026ApJ..1002....9L",
 "title": "COSMOS-3D: Dense Circumnuclear Gas Across Black Hole Growth Phases at z ∼ 3",
 "year": 2026,
 "journal": "The Astrophysical Journal",
 "first_author": "Li, Zi-Jian",
 "n_authors": 28,
 "arxiv_id": "2512.02093",
 "doi": "10.3847/1538-4357/ae587b",
 "alma_projects_linked_by_archive": [
  "2016.1.01001.S",
  "2016.1.01012.S",
  "2021.1.00225.S",
  "2021.1.01328.S",
  "2023.1.00180.L"
 ]
}
```

Paper text:
<paper>
# COSMOS-3D: Dense Circumnuclear Gas across Black Hole Growth Phases at $z\sim3$

## Abstract

We report the discovery of two broad-line X-ray AGNs (`cid_414` and `cid_947`) at $z\sim3$ identified in the JWST Cycle 3 COSMOS-3D program using NIRCam F444W grism spectroscopy. Both exhibit prominent He i$\lambda$10830+Pa$\gamma$ emission and absorption, indicative of circumnuclear dense gas that is traced in these systems. Complementary UV and optical spectroscopy in the COSMOS field provides Ly$\alpha$, Si iv, and C iv measurements. Both sources are detected in MIRI F1000W, and `cid_414` is also detected in F2100W, indicating hot dust emission.

The two AGNs show distinct black hole and obscuration properties. The source `cid_414` displays little red dots (LRD)-like V-shape spectra energy distribution (SED) shape with a turnover near the Balmer 4000 Å break, and a narrow Ly$\alpha$ line with $\log L_{\rm Ly\alpha}=42.49\pm0.01 \mathrm{erg\ s^{-1}}$, with no additional metal lines detected. In contrast, `cid_947` exhibits a higher He i$\lambda$10830 absorption column density, larger X-ray–inferred $N_{\rm H}$, lower intrinsic 2–10 keV luminosity, and strong blueshifted features in He i, Si iv, and C iv absorption with velocity offsets exceeding $5000~\mathrm{km\ s^{-1}}$. Photoionization modeling implies gas densities of $\sim10^{9-10} \mathrm{cm^{-3}}$ and sizes comparable to the broad-line region, consistent with dense gas envelopes predicted for LRDs. Together with previous detections of He i$\lambda$10830 absorption in compact little red dots, these results suggest that dense circumnuclear gas is likely prevalent at high redshift and may regulate obscuration and black hole–host co-evolution across AGN types.

# Introduction

The growth of supermassive black holes and the evolution of their host galaxies are closely connected through the presence and dynamics of dense gas in the circumnuclear region. Obscuration represents a key phase in this co-evolution, where gas and dust surrounding the active nucleus attenuate the emergent radiation and generate characteristic absorption and emission signatures in the spectrum (see the reviews of (cite: hickox2018; alex25) and references therein). However, the physical processes that govern the structure and evolution of the obscuring gas, and how this gas regulates both black hole accretion and star formation in the host galaxy, remain poorly understood.

Theoretical models suggest that obscuration is closely tied to luminosity-dependent AGN demographics (cite: gilli07; lizijian2024), with circumnuclear hydrogen volume densities reaching $n_{\rm H}\gtrsim10^{8},\mathrm{cm^{-3}}$ (cite: 1995ApJ...455L.119B; wuqiaoya25). Observationally, X-ray surveys have established that obscuration is common among AGNs across cosmic time. In the COSMOS field, $\sim$60% of X-ray AGNs are obscured (cite: marchesi16), while local Swift–BAT observations indicate an obscured fraction of $\sim$70% (cite: 2017ApJ...850...74K; cricci17). Deep Chandra observations further reveal that the obscured fraction increases with redshift and includes a substantial Compton-thick population (cite: buchner15; liu17), with hard X-ray observations from NuSTAR confirming the prevalence of heavily obscured AGNs (cite: alex13; arevalo17; peca25).

He i$\lambda$10830 absorption offers distinct advantages for probing the physical conditions of the circumnuclear absorbing gas. The He i$\lambda$10830 transition arises from recombination of He$^{+}$ to the metastable $2^{3}$S level (ionization potential of 24.56 eV). Because the diffuse stellar radiation field is weak above 24.56 eV (cite: ji15), the presence of He i$\lambda$10830 absorption is a robust indicator of AGN ionization. Moreover, its large oscillator strength ($f=0.5392$) provides a wider dynamic range in column density compared to commonly used UV resonant lines such as C iv and Si iv (cite: leighly14). However, because He i$\lambda$10830 lies outside the typical optical spectral window, reported detections remain limited. (cite: liu15) compiled only 11 quasars with He i$\lambda$10830 absorption known at the time, most at $z<1$. The first data release of NIR spectroscopy from the BASS survey identified 7 out of 102 local X-ray AGNs with possible He i$\lambda$10830 absorption, and the number continues to grow in later releases (see, e.g., Figure 2 in (cite: ricci22)).

The advent of JWST has enabled higher sensitivity and broader wavelength coverage in the near- and mid-infrared. One of the most intriguing discoveries from JWST is a population of compact, red sources known as “little red dots” (LRDs), which exhibit a characteristic V-shaped spectral energy distribution, with rest-frame UV continua that are bluer than the optical ones and a turnover near the Balmer break. The $z>4$ LRDs are frequently detected with broad Balmer emission lines (cite: matthee24; kocevski25), indicative of AGN-like activity. Their physical nature is still under debate, with the main discussion focusing on the relative contribution from host galaxies versus AGN emission. Several studies interpret LRDs as dust-reddened AGNs at early cosmic times (cite: harikane23; kocevski23; maiolino23; matthee24) or stellar light from its host galaxy (cite: greene24). Another scenario is that LRDs are AGN embedded in dense gas envelopes (cite: kohei25; degraaff25), which is supported by LRD observations with Balmer absorption lines at $z>4$ and a small number of He i$\lambda$10830 absorption at $z\sim3$ (cite: juodzbalis24; wang25; naidu25; kokorev25; loiacono25; graff25). Interestingly, (cite: lin25) identified three local analogs of LRDs in SDSS, all of which also show He i$\lambda$10830 absorption.

Most LRDs are found to be both X-ray and radio weak (cite: yue24). Recently, two sources reported by (cite: shuqi25) (with Forge-II corresponding to `cid_414` in this work) were identified as LRDs with V-shape SEDs and compact morphologies and interpreted as transitioning into quasars. In addition, an “X-ray dot” reported by (cite: xraydot) exhibits Balmer absorption, an LRD-like SED, and a $2$–$10~$ keV X-ray luminosity of $10^{44.18}~\mathrm{erg~s^{-1}}$, but is mid-infrared faint at $z\sim3$. These observations suggest that linking gas phases across different stages of AGN growth is a promising approach to understanding the role of obscuration in black hole growth and host galaxy evolution at high redshift. Motivated by this, comparing X-ray–bright, LRD-like AGNs with the broader AGN population is essential for clarifying the nature of LRDs, high-redshift red quasars, and the role of gas and dust in their growth.

In this letter, we report the detections of two AGNs at $z\sim3$ in the COSMOS field with both X-ray and MIRI observations. Both sources exhibit broad He i$\lambda$10830 emission (full width at half maximum, FWHM $>$ 2000 km s$^{-1}$) and prominent absorption features, indicating the presence of dense gas surrounding the broad-line region. The He i$\lambda$10830 spectra and MIRI data are drawn from the JWST GO 3 large program COSMOS-3D (hereafter C3D, PID #5893; PI: K. Kakiichi), which provides F444W NIRCam grism spectroscopy along with MIRI F1000W and F2100W imaging. The data come from observations conducted between December 2024 and May 2025. An overview of the program and its major science goals will be presented in Kakiichi et al., in prep. In Section [2](#sec:target_selection), we describe the target selection and ancillary datasets. Section [3](#sec:proper) presents measurements of the AGN properties, including stellar mass ($M_*$), black hole mass ($M_{\rm BH}$), and star formation rate (SFR). In Section [4](#sec:discussion), we discuss the role of dense gas traced by He i$\lambda$10830 absorption in obscuration and black hole growth. Section [4.1](#sec:cloudy) models the photoionization state of this gas, and Section [4.3](#sec:dndz) compares these two AGNs with other populations, including LRDs.

Throughout the paper, we adopt a standard $\Lambda$CDM cosmology with $H_0 = 70\ {\rm km}\ {\rm s}^{-1}\ {\rm Mpc}^{-1}$, $\Omega_{M}$ = 0.3 and $\Omega_{\lambda}$ = 0.7. The initial mass function (IMF) adopted in this paper is from (cite: chabrier).

# Target Selection and Observations

## Target selection

The two AGNs were first selected from the X-ray catalog of the Chandra COSMOS-Legacy (CCL) Survey (cite: civano16), which is a 4.6 Ms *Chandra* program covering 2.2 deg$^{2}$ of the COSMOS field. (cite: marchesi16b) reported X-ray properties for 1,855 sources with $>$30 net counts and derived intrinsic hydrogen absorption column density ($N_{\rm H}$) and rest-frame 2 to 10 keV luminosities ($L_{\rm X,2-10 keV}$). Among the 1,238 X-ray AGNs (log $L_{\rm X,2-10 keV}  > 42$, AGN selection criteria from (cite: alexander05)) with secure spectroscopic redshifts, 342 fall within the C3D NIRCam imaging footprint, and 106 of these 342 are covered by C3D MIRI observations (either 1000W or 2100W). We visually inspected the F444W grism spectra of these 106 AGNs, and two of them, `cid_414` and `cid_947`, show prominent He i$\lambda$10830 absorption features. The information and measured properties of these two AGNs described in Section [3](#sec:proper) are listed in Table [1](#table:prop). We refer to (cite: shuqi25), who report `cid_414` and another X-ray AGN as two LRDs transitioning into quasars at $z\sim3$, providing detailed rest-frame UV data and discussion. In this work, we focus on investigating the roles of absorbing gas and hot dust at different stages of black hole growth.

## JWST NIRCam and MIRI imaging

These two targets are covered by both C3D and the GO1 treasury program COSMOS-Web (PI: C. Casey, PID #1727). In C3D, we conducted NIRCam grism spectroscopy using F444W filter, with the F200W filter simultaneously employed in the short-wavelength (SW) channel during the WFSS observations. Direct imaging was obtained with the F115W and F356W filters, providing a total NIRCam coverage of $\sim1151~{\rm arcmin^2}$. COSMOS-Web have NIRCam imaging in four filters (F115W, F150W, F277W, F444W) and MIRI F770W in parallel. We obtained the COSMOS-Web data from their DR1 data and catalog release 1 (cite: shuntov25)[^1]. All images (both NIRCam and MIRI) are drizzled to a $0.03^{\prime\prime}$ pixel scale. For C3D, we performed the NIRCam and MIRI imaging reduction on F115W, F200W and F356W bands using the JWST pipeline version 1.16.1 (cite: jwst_pipeline), with the CRDS calibration reference file context `jwst_1303.pmap`.

The C3D MIRI data (F1000W and F2100W) were processed following the approach adopted in the Systematic Mid-infrared Instrument Legacy Extragalactic Survey (SMILES; (cite: Lyu24)). During Stage 2 reduction, we implemented a customized external background subtraction module from the Rainbow Database JWST pipeline, which constructs a super-background model to suppress cosmic-ray–induced artifacts (cite: alvarez23).

## JWST Grism spectra

The WFSS spectra were taken in the F444W filter with Grism R. The $5\sigma$ line flux limit is $4\times10^{-18}~{\rm erg~s^{-1}~cm^{-2}}$ at $\sim4.5~\mu{\rm m}$ (i.e., $m_{\rm F444W}\lesssim27.5$) within the C3D NIRCam coverage. The spectral resolution is $R\sim1600$ at $\sim4~\mu$m. We reduced the grism data following the method described in (cite: sun23)[^2]. We briefly describe the procedure as follows: the Stage 1 data were processed with the standard JWST pipeline. The data were flat fielded using imaging flats taken with the same filter and module, and the sky background was removed using sigma-clipped median grism frames. The wavelength and spectral tracing solutions were derived from commissioning calibrations and refined using field dependent grism trace and dispersion models. Flux calibration was performed using spectra of the standard star P330-E, and the calibrated 2D spectra were extracted and combined for all F444W grism exposures.

+---------------------------------------------------------------------------------------------------------+
| **`cid_414` **                                                                                          |
+:============================================================================+:==========================+
| RA, DEC                                                                     | 149.89197, 2.28509        |
+-----------------------------------------------------------------------------+---------------------------+
| Redshift                                                                    | 2.933                     |
+-----------------------------------------------------------------------------+---------------------------+
| log L$_{\rm X,2-10\ keV}$ (erg s$^{-1}$)                                    | 45.17                     |
+-----------------------------------------------------------------------------+---------------------------+
| log L$_{\rm bol}$ (erg s$^{-1}$)                                            | 46.69                     |
+-----------------------------------------------------------------------------+---------------------------+
| log $N_{\rm H}$ (cm$^{-2}$)                                                 | 22.50$^{+0.33}_{-1.16}$   |
+-----------------------------------------------------------------------------+---------------------------+
| log M$_{\ast}$/M$_{\odot}$                                                  | 10.92$^{+0.29}_{-0.29}$   |
+-----------------------------------------------------------------------------+---------------------------+
| log SFR (M$_{\odot}$ yr$^{-1}$)                                             | 2.55$^{+0.19}_{-0.19}$    |
+-----------------------------------------------------------------------------+---------------------------+
| log M$_{\rm BH}$/M$_{\odot}$                                                | 9.15$^{+0.4}_{-0.4}$      |
+-----------------------------------------------------------------------------+---------------------------+
| $\lambda_{\rm Edd}$                                                         | 0.28$_{-0.18}^{+0.41}$    |
+-----------------------------------------------------------------------------+---------------------------+
| $f_{\mathrm{HeI\lambda10830}}$ emission (10$^{-17}$ erg s$^{-1}$ cm$^{-2}$) | 5.94$^{+0.15}_{-0.15}$    |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\mathrm{HeI\lambda10830}}$ broad (km s$^{-1}$)                       | 3591$^{+78}_{-78}$        |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\mathrm{HeI\lambda10830}}$ narrow (km s$^{-1}$)                      | 1193$^{+32}_{-32}$        |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\mathrm{HeI\lambda10830}}$ emission broad (Å)                          | 135$^{+2}_{-2}$           |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\mathrm{HeI\lambda10830}}$ emission narrow (Å)                         | 16$^{+1}_{-1}$            |
+-----------------------------------------------------------------------------+---------------------------+
| $f_{\rm Pa\gamma}$ emission (10$^{-17}$ erg s$^{-1}$ cm$^{-2}$)             | 1.66$^{+0.04}_{-0.04}$    |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\rm Pa\gamma}$ broad (km s$^{-1}$)                                   | 2553$^{+55}_{-55}$        |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\rm Pa\gamma}$ narrow (km s$^{-1}$)                                  | 1195$^{+33}_{-33}$        |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\rm Pa\gamma}$ emission broad (Å)                                      | 42$^{+1}_{-1}$            |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\rm Pa\gamma}$ emission narrow (Å)                                     | 1$^{+1}_{-1}$             |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\mathrm{HeI\lambda10830}}$ absorption (Å)                              | 31$^{+6}_{-6}$            |
+-----------------------------------------------------------------------------+---------------------------+
| log$N$(He i$\lambda$10830) (cm$^{-2}$)                                      | 13.9$^{+0.1}_{-0.1}$      |
+-----------------------------------------------------------------------------+---------------------------+
| **`cid_947` **                                                                                          |
+-----------------------------------------------------------------------------+---------------------------+
| RA, DEC                                                                     | 150.29725, 2.14884        |
+-----------------------------------------------------------------------------+---------------------------+
| Redshift                                                                    | 3.328                     |
+-----------------------------------------------------------------------------+---------------------------+
| log L$_{\rm X,2-10\ keV}$ (erg s$^{-1}$)                                    | 44.62                     |
+-----------------------------------------------------------------------------+---------------------------+
| log L$_{\rm bol}$ (erg s$^{-1}$)                                            | 46                        |
+-----------------------------------------------------------------------------+---------------------------+
| log $N_{\rm H}$ (cm$^{-2}$)                                                 | 23.47$^{+0.29}_{-0.47}$   |
+-----------------------------------------------------------------------------+---------------------------+
| log M$_{\ast}$/M$_{\odot}$                                                  | 11.01$^{+0.19}_{-0.20}$   |
+-----------------------------------------------------------------------------+---------------------------+
| log SFR (M$_{\odot}$ yr$^{-1}$)                                             | 1.49$^{+0.20}_{-0.20}$    |
+-----------------------------------------------------------------------------+---------------------------+
| log M$_{\rm BH}$/M$_{\odot}$                                                | 9.84$^{+0.28}_{-0.28}$    |
+-----------------------------------------------------------------------------+---------------------------+
| $\lambda_{\rm Edd}$                                                         | 0.013$_{-0.006}^{+0.006}$ |
+-----------------------------------------------------------------------------+---------------------------+
| $f_{\mathrm{HeI\lambda10830}}$ emission (10$^{-17}$ erg s$^{-1}$ cm$^{-2}$) | 1.90$^{+0.06}_{-0.06}$    |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\mathrm{HeI\lambda10830}}$ broad (km s$^{-1}$)                       | 2473$^{+49}_{-49}$        |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\mathrm{HeI\lambda10830}}$ narrow (km s$^{-1}$)                      | 1198$^{+38}_{-38}$        |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\mathrm{HeI\lambda10830}}$ emission broad (Å)                          | 75$^{+2}_{-2}$            |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\mathrm{HeI\lambda10830}}$ emission narrow (Å)                         | 5$^{+1}_{-1}$             |
+-----------------------------------------------------------------------------+---------------------------+
| $f_{\rm Pa\gamma}$ emission (10$^{-17}$ erg s$^{-1}$ cm$^{-2}$)             | 0.67$^{+0.02}_{-0.02}$    |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\rm Pa\gamma}$ broad (km s$^{-1}$)                                   | 4353$^{+140}_{-140}$      |
+-----------------------------------------------------------------------------+---------------------------+
| FWHM$_{\rm Pa\gamma}$ narrow (km s$^{-1}$)                                  | 1196$^{+38}_{-38}$        |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\rm Pa\gamma}$ emission broad (Å)                                      | 24$^{+1}_{-1}$            |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\rm Pa\gamma}$ emission narrow (Å)                                     | 6$^{+1}_{-1}$             |
+-----------------------------------------------------------------------------+---------------------------+
| EW$_{\mathrm{HeI\lambda10830}}$ absorption (Å)                              | 33$^{+10}_{-10}$          |
+-----------------------------------------------------------------------------+---------------------------+
| log$N$(He i$\lambda$10830) (cm$^{-2}$)                                      | 14.1$^{+0.2}_{-0.2}$      |
+-----------------------------------------------------------------------------+---------------------------+
| $v_{max}$ (km s$^{-1}$)                                                     | $\sim$12000               |
+-----------------------------------------------------------------------------+---------------------------+

: Physical properties of the two AGNs. Stellar masses and SFRs are derived with `CIGALE`. The outflow velocity $v_{max}$ is taken from (cite: science).

## Ancillary data

The COSMOS field provides extensive multiwavelength ancillary observations, allowing a detailed characterization of these two targets from X-ray to radio. Below we summarize the datasets used in this work.

### X-ray

We use the reduced archival X-ray data from the CCL survey and its X-ray catalog (cite: marchesi16b) in this work (see Figure [7](#fig:xray_data)). CCL survey has a hard-band 2-10 keV flux limit of $1.5\times10^{-15}~\mathrm{erg~s^{-1}~cm^{-2}}$. The data were reduced with CIAO 4.5 (cite: ciao) and CALDB 4.5.9. The intrinsic 2–10 keV X-ray luminosity $L_{2\text{–}10,\mathrm{keV}}$ and the absorbing column density $N_{\rm H}$ are derived from spectral fits using an absorbed power–law model and the photon index $\Gamma$ is fixed at 1.9 in the fitting.

Details of the X-ray spectral fitting are provided in (cite: marchesi16b). The $L_{2-10~\mathrm{keV}}$ of `cid_414` is $L_{2-10~\mathrm{keV}}=10^{45.17}~\mathrm{erg~s^{-1}}$ with a hydrogen column density $N_{\mathrm{H}}=10^{22.5}~\mathrm{cm^{-2}}$. For `cid_947`, the $L_{2-10~\mathrm{keV}}$ is $10^{44.62}~\mathrm{erg~s^{-1}}$ and the column density is $N_{\mathrm{H}}=10^{23.47}~\mathrm{cm^{-2}}$. Both sources are therefore classified as Compton-thin ($N_{\mathrm{H}}<10^{24}~\mathrm{cm^{-2}}$) obscured AGN based on their hard X-ray detections and X-ray inferred hydrogen column densities.

### UV–mid-IR

For the bands not covered by the JWST imaging data, we collect the UV-to-mid-IR photometry using the Kron AUTO measurements from the COSMOS2020 Classic catalog `COSMOS2020` (cite: cosmos2020), spanning from the *GALEX*/FUV band to the *Spitzer*/IRAC channel 4.

The $u$ band photometry is from the CFHT Large Area U band Deep Survey (CLAUDS) program (cite: clauds). The ongoing HSC Subaru Strategic Program (HSC-SSP) survey provides imaging from $g$ band to $y$ band (cite: hscssp). Besides, we include the HST/F814W photometry from (cite: hst814). The HST/F814W AB magnitudes are 24.49$\pm$0.05 and 20.50$\pm$0.01 for `cid_414`  and `cid_947`, respectively. The $YJHK_{s}$ data is from the fourth data release of the UltraVISTA survey (cite: ultravista). For mid-IR photometry, we use the magnitudes from the Spitzer Large Area Survey with Hyper Suprime-Cam (SPLASH; (cite: splash)). Neither of the two objects are detected in the $GALEX$/FUV or NUV bands.

### submm–FIR–radio

The `cid_414` has been observed in multiple ALMA programs, including #2016.1.01001.S (PI: J. Kartaltepe; 887 s integration time in Band 3), #2021.1.01328.S (PI: W. Rujopakarn; 60 s in Band 7), #2021.1.00225.S (PI: C. Casey; 45 s in Band 4), and #2023.1.00180.L (CHAMPS; PI: A. Faisst; Faisst et al., in prep.; 54 s in Band 6). There is no $>3\sigma$ dust continuum detection in the Band 3, 6 and 7 observation for `cid_414`. The `cid_947` has a reliable (S/N $\sim$ 7.5) ALMA Band 6 (1.1 mm) detection from program #2016.1.01012.S (PI E. Treister). We retrieved the reduced data from the latest public release of the A3COSMOS program (cite: a3cosmos).

We match the FIR photometry of these two sources using the super-deblended catalog (cite: superdeblended), which combines FIR to (sub)millimeter measurements in the COSMOS field. The Herschel/PACS 100 and 160 $\mu$m data are from the PEP program (PI D. Lutz; (cite: pep)), and the SPIRE 250, 350, and 500 $\mu$m data are from the Herschel Multi-tiered Extragalactic Survey (PI: S. Oliver; (cite: hermes)). Since the super-deblended catalog is based on NIR prior positions, we adopt a matching radius of 1 arcsec. Neither source has S/N $>$ 3 detections at 100 or 160 $\mu$m.

At radio wavelengths, we search the VLA-COSMOS 1.4 GHz (cite: vla1.4ghz) and 3 GHz (cite: vla3ghz) catalogs. The `cid_414` is detected with high significance (S/N $>$ 10) at both 1.4 GHz and 3 GHz, while `cid_947` shows no radio detection.

### Ground-based spectroscopy

We find that `cid_414` has archival Keck/LRIS (exptime = 2h, $R\sim$ 1100) spectroscopy from the COSMOS Lyman-Alpha Mapping and Tomography Observations (CLAMATO) survey (cite: clamato; clamato2), covering 3200–5500 Å, and Keck/DEIMOS (exptime = 1800s) spectroscopy from the DEIMOS 10k survey (cite: deimos), covering 5500–9800 Å and spectral resolution $R\sim$ 2000. The two parts of the spectra are shown in the Appendix Figure [8](#fig:optical_spec). A clear Ly$\alpha$ emission line is detected at $z = 2.933$ with a signal-to-noise ratio of $\sim45$, while no C iv or C iii\] lines are detected. This is further confirmed by DESI spectra presented in (cite: shuqi25). The Ly$\alpha$ line is well fitted by a Gaussian profile with a FWHM of 744.90$\pm$32.52 km s$^{-1}$. The apparent Ly$\alpha$ luminosity is 10$^{42.49}$ erg s$^{-1}$. This value is similar to that detected in a sample of 23 $z\sim2$ type II AGN selected from SDSS, part of which show both narrow Ly$\alpha$ and broad Balmer lines (cite: wangben25).

The `cid_947` was observed in the zCOSMOS-bright survey (cite: zcosmos), showing significant ($\sim12000$ km s$^{-1}$) blueshifted outflow features in the Si iv, C iv, and Al iii absorption lines (see the right panel of Figure [8](#fig:optical_spec)). (cite: science) also obtained a $K$-band (1.9–2.4 $\mu$m) spectrum of this target with Keck/MOSFIRE. The spectrum shows a broad H$\beta$ line with FWHM $=11330$ km s$^{-1}$, yielding a black hole mass estimate of $6.91\times10^{9}\ M_{\odot}$ from the broad-line virial method.

# Measurements and Properties

## Emission and absorption line measurements

We present the NIRCam F444W imaging, and the 2D (without conitinuum subtraction) and 1D grism spectra of `cid_414` and `cid_947` in Figure [1](#fig:spec). For the two targets, we first fit the He i+Pa$\gamma$ line structure using Gaussian profiles for both the emission and absorption components. A linear continuum is fitted around the emission lines in the rest-frame wavelength ranges 1.02–1.05 $\mu$m and 1.11–1.14 $\mu$m. We fit the He i$\lambda$10830 and Pa$\gamma$ emission lines using three models: broad only, narrow only, and broad+narrow components, and we find that the resulting $\chi^{2}$ values are similar. In Figure [1](#fig:spec), we present the fitting results for the two targets using a model with one broad and one narrow component. We describe the details of the emission and absorption line measurements of the two targets below and in Table [1](#table:prop).

### `cid_414`

For `cid_414`, we fix the center of the He i$\lambda$10830 and Pa$\gamma$ lines to the redshift determined from the Ly$\alpha$ line ($z = 2.933$, vertical dashed line in Figure [1](#fig:spec)). The FWHM of the broad (narrow) component of `cid_414` is 3591$\pm$78 (1193$\pm$32) km s$^{-1}$ for the He i$\lambda$10830  line. The line widths for the Pa $\rm \gamma$ are 2553$\pm$55 and 1195$\pm$33 km s$^{-1}$ for the broad and narrow components, respectively. We correct the line instrumental broadening based on the NIRCam grism line-spread function (cite: greene17). The equivalent widths (EWs) of the He i$\lambda$10830 and Pa$\gamma$ broad emission lines are 135$\pm$2 Å and 16$\pm$1 Å, respectively.

We use the apparent optical depth (AOD) method to estimate the column density of the He i$\lambda$10830 absorption line. The optical depth is defined as $\tau(v) = -\ln \left( I(v)/I_{\rm c}(v) \right)$, where $I(v)$ and $I_{\rm c}(v)$ are the observed spectral intensity and the interpolated absorption–free continuum, respectively. The column density is then calculated by integrating the optical depth over the velocity range of the absorption: $$\begin{equation}
N = \frac{m_{e} c}{\pi e^{2} \lambda f} \int_{v_{\rm min}}^{v_{\rm max}} \tau(v)~dv ,
\end{equation}$$ where $m_{e}$ and $e$ are the electron mass and charge, $c$ is the speed of light, $\lambda$ is the rest-frame transition wavelength, and $f$ is the oscillator strength. We obtain for `cid_414` a column density of log $N$(He i$\lambda$10830)/cm$^{-2}$ = 13.9 $\pm$ 0.1.

### `cid_947` 

Different from `cid_414`, where the He i$\lambda$10830 absorption does not show a significant velocity offset from the emission-line center, the object `cid_947` is a BAL quasar exhibiting a significant velocity offset ($> 5000$ km s$^{-1}$) in the absorption features in both the rest-frame UV lines and He i$\lambda$10830. The fluxes of He i$\lambda$10830 and Pa $\rm \gamma$ emission lines for `cid_947` are $(1.90 \pm 0.06) \times 10^{-17}$ and $(0.67 \pm 0.02) \times 10^{-17}$ erg s$^{-1}$ cm$^{-2}$, respectively. From the right panel of Figure [8](#fig:optical_spec), we see that the He i$\lambda$10830 line profile shares a similar velocity width with the rest-frame UV absorption lines. We fit the He i$\lambda$10830 absorption with three major components (as C1,2 and 3) in Figure [1](#fig:spec), and list the corresponding measured equivalent widths and the total column density in Table [1](#table:prop). There is likely a fourth subcomponent at a velocity offset of $\Delta v\sim -12{,}000$ km s$^{-1}$, but since it is not detected above $3\sigma$ in the 2D spectra, we do not include it when calculating the He i$\lambda$10830 absorption-line column density. The total He i$\lambda$10830 absorption-line column density, integrated over the three subcomponents shown in Figure [1](#fig:spec), is 10$^{14.1 \pm 0.2}$ $\mathrm{cm^{-2}}$.

## JWST photometry

For all JWST NIRCam and MIRI bands used in this study, we performed photometric measurements using SEP for source detection and SE++ for photometry (cite: bertin20). SEP was applied to the square root of a positive $\chi^2$ detection image constructed from all available broadband images within each tile. It was run in both “hot” and “cold” modes, which were later merged to optimize the detection of bright, extended galaxies and deblended faint, compact sources. Automatic Kron photometry was carried out using “small Kron” (k=1.2, R=1.6) and “default Kron” (k=2.5, R=3.5) apertures with SEP and `photutils`, and the ratio of these fluxes was used for aperture correction. The images are not point-spread-function (PSF)-matched; however, the Kron shape parameters are derived from the $\chi^2$ image. SE++ was subsequently run in ASSOC mode to compute fixed-aperture photometry for the SEP-detected sources. The complete C3D photometry details and catalog will be described in Champagne et al., in prep.

## Point-Spread Function Construction and Image Decomposition

In order to measure the host galaxy (if present) properties, we perform careful imaging decomposition. Previous studies usually adopt two components to model the light distribution: a PSF profile for the AGN and a Sérsic profile for the host galaxy (cite: ding20; li2021; zhuang24b). The PSF is constructed from stars within a $2^{\prime\prime}$ radius around the targets. We use 11 stars for `cid_414` and 5 for `cid_947`. The stellar cutouts are oversampled by a factor of three, recentered, and median stacked to generate the final PSF.

We use `SExtractor` to identify stellar candidates in each tile and band, excluding sources near image edges or affected by bad pixels. From the remaining objects, we select stars with consistent half-light radii and extract $6\ensuremath{''}$ cutouts, within which $\sim98\%$ of the stellar light is enclosed (cite: zhuang24). The `SExtractor` segmentation map masks unrelated sources.

We then perform the image decomposition using the code `GALFITS` (cite: galfits). Different from traditional single-band decomposition tools, `GALFITS` simultaneously fits images taken in multiple bands and incorporates physically motivated SED models into the fitting process. This enables the simultaneous extraction of the physical properties of both the AGN and the host galaxy. As shown in Figure [9](#fig:galfits), `cid_947` appears morphologically consistent with a point source, while `cid_414` exhibits asymmetric structures in the JWST F115W, F150W, and F200W bands. About $\sim51\%$ of the total flux is enclosed within a $0.18\ensuremath{''}$ aperture in F200W ($82\%$ for `cid_947`). The F200W emission extends to $\sim7.9$ pkpc to the north. This extension may trace H$\beta$+\[O iii\] emission in F200W and Mg ii+\[O ii\] emission in F115W/F150W (cite: shuqi25). For `cid_947`, a single Sérsic plus PSF model yields a stellar mass of $10^{10.94}\ M_{\odot}$. We find that if we include the extended region and fit `cid_414` with a single Sérsic component, the derived stellar mass is $10^{11.83}\ M_{\odot}$, comparable to that of a very massive quiescent galaxy in the local universe. We therefore adopt two Sérsic components to model the host galaxy emission of `cid_414`, without imposing constraints on the Sérsic index or effective radius because of its asymmetric morphology. We exclude the flux from the second Sérsic component when estimating the host galaxy mass and in the subsequent SED fitting in Section [3.4](#sec:sed). The stellar mass derived from the primary Sérsic component is $10^{11.12\pm0.33}\ M_{\odot}$. For a detailed decomposition of the two components, we refer to (cite: shuqi25), where the second component is interpreted as nebular emission.

## SED fitting and host galaxy properties

To measure the host galaxy and black hole properties of the two targets, we perform multiwavelength spectral energy distribution (SED) fitting using UV–to–radio photometry introduced in Section [2](#sec:target_selection). To mitigate systematics arising from the assumptions built into any single SED fitting tool (choices of AGN and stellar components, dust treatment, and star formation history etc), we use two independent codes, `CIGALE` (cite: cigale) and `AGNfitter` (cite: agnfitter). `CIGALE` fits the SED with energy balance, adopting BC03 stellar models (cite: bc03), a Chabrier IMF (cite: chabrier), a delayed-exponential star formation history (SFH), the (cite: calzetti00) attenuation law, (cite: draine14) dust emission, and the SKIRTOR AGN model (cite: skirtor1; skirtor2). `AGNfitter` uses the same stellar and attenuation models but does not enforce energy balance; it models dust emission with (cite: schreiber18) templates and decomposes AGN emission into an accretion-disk big blue bump (BBB) component (cite: temple21) and a dusty torus described by the CAT3D library (cite: cat3dwind).

The best-fit SEDs from `CIGALE` and `AGNfitter` are shown in black and blue in Figure [2](#fig:sed), respectively. We note that the UV optical SED of `cid_414` shows a turnover around the Balmer break (see the zoom in window in the left panel together with the LRD stacking SED template from (cite: akins)). Combined with its compact morphology and the absence of UV metal lines, `cid_947` exhibits LRD like features, except for the presence of X ray and MIRI detections. In the `AGNfitter` results, the rest-frame UV to mid-IR emission of both targets is dominated by the AGN. In the `CIGALE` results, `cid_947` is AGN-dominated, while `cid_414` shows a non-negligible contribution from stellar emission. In particular, if we include the fluxes from both Sérsic components for `cid_414`, the derived stellar masses are $10^{12.09}\ M_{\odot}$ and $10^{12.08}\ M_{\odot}$ from `CIGALE` and `AGNfitter`, respectively, which are unrealistically high for a typical star-forming galaxy at $z\sim3$. We therefore adopt only the Sérsic 1 component in the SED fitting, resulting in a stellar mass of $\sim10^{11.12\pm0.33}M_{\odot}$. We further use the F200W (rest frame $V$ band) Sérsic 1 flux and the mass–to–light ratio from (cite: faber79), varying the $M/L$ from 2 to 7.6 as a consistency check, yielding a stellar mass of $10^{10.92\pm0.29}M_{\odot}$, as listed in Table [1](#table:prop).

For both the `CIGALE` and `AGNfitter` fitting results, `cid_414` shows a relatively higher star formation rate (SFR) than `cid_947`, as listed in Table [1](#table:prop). We plot the star-forming main sequence in the $M_{*}$–SFR plane in Figure [3](#fig:sfr_bh_stellar). Our measurements reveal that `cid_414` lies on the star-forming main sequence at $z\sim3$, while `cid_947` is slightly below the relation.

## Black hole mass and Eddington ratio measurements

. Three additional AGNs with He i$\lambda$10830 absorption from the literature are also shown: RUBIES 40579 (cite: kocevski25), W25 (cite: wang25), and J25 (cite: juodzbalis24).

Since we do not have archival observations of broad Balmer lines or Mg ii for `cid_414`, which are typically used to estimate the black hole mass in type I AGNs at similar redshifts in the literature, we instead adopt an indirect empirical scaling relation based on the He i and H$\beta$ lines, as calibrated from the local BASS sample (cite: ricci17). With our measured FWHM of the He i$\lambda$10830 emission line and the X-ray luminosity, we obtain a black hole mass of `cid_414`, $\log(M_{\rm BH}/M_{\odot}) = 9.15 \pm 0.40$. The uncertainty arises from the measurement errors in the He i$\lambda$10830 FWHM and the intrinsic scatter of the calibration. For `cid_947`, we adopt the black hole mass $\log(M_{\rm BH}/M_{\odot}) = 9.84 \pm 0.28$ estimated from the broad H$\beta$ line, following the method described in (cite: science). The bolometric luminosities of the two targets are converted from the 2 to 10 keV luminosity using the bolometric correction from (cite: duras20). The resulting Eddington ratios are $\lambda_{\rm Edd} = 0.28_{-0.18}^{+0.41}$ for `cid_414` and $\lambda_{\rm Edd} = 0.013_{-0.01}^{+0.01}$ for `cid_947`. Since we do not have archival observations of broad Balmer lines or Mg ii for `cid_414`, which are typically used to estimate the black hole mass in type I AGNs at similar redshifts in the literature, we instead adopt an indirect empirical scaling relation based on the He i and H$\beta$ lines, as calibrated from the local BASS sample (cite: ricci17). With our measured FWHM of the He i$\lambda$10830 emission line and the X-ray luminosity, we obtain a black hole mass of `cid_414`, $\log(M_{\rm BH}/M_{\odot}) = 9.15 \pm 0.40$. The uncertainty arises from the measurement errors in the He i$\lambda$10830 FWHM and the intrinsic scatter of the calibration. For `cid_947`, we adopt the black hole mass $\log(M_{\rm BH}/M_{\odot}) = 9.84 \pm 0.28$ estimated from the broad H$\beta$ line, following the method described in (cite: science). The bolometric luminosities of the two targets are converted from the 2 to 10 keV luminosity using the bolometric correction from (cite: duras20). The resulting Eddington ratios are $\lambda_{\rm Edd} = 0.28_{-0.18}^{+0.41}$ for `cid_414` and $\lambda_{\rm Edd} = 0.013_{-0.01}^{+0.01}$ for `cid_947`.

# Discussion

## Dense Gas in Different SMBH Growth Phase

Given the distinct SED shapes, spectral features, and physical properties of the two targets, we tentatively examine the role of dense absorbing gas in AGN obscuration and in the growth of black holes and their host galaxies.

We compare the stellar and black hole masses of the two targets with other AGN populations, including X-ray AGNs at $z = 1$–$2.5$ (cite: merloni10; suh20), LRDs with He i$\lambda$10830 absorption at $z\sim3$ (cite: wang25; kocevski25; juodzbalis24), JWST-detected AGNs (cite: jones25), and quasars at $z\sim4$–$7$ (cite: ruancun25). Figure [3](#fig:sfr_bh_stellar) shows the $M_{\rm BH}$–$M_\star$ relation derived from local AGNs (cite: zhuang23; kormendy13). We find that our two targets, though exhibiting relatively different SED shapes and black hole masses, lie above the empirical relation derived from local AGN samples. Their black hole masses are higher than those of AGNs at $z\sim1$–$2.5$ and are comparable to those of $z\sim5$ quasars, indicative of rapid black hole growth. Between the two targets, `cid_947` has a relatively higher black hole mass but a lower $\lambda_{\rm Edd}$, which may indicate that `cid_947` has already undergone a period of black hole growth and that its current activity is suppressed by relatively denser gas (higher $N_{\rm H}$ and $N_{\rm HeI}$). The source `cid_414`, on the other hand, as suggested by (cite: shuqi25), may represent a later phase of LRD growth and is rapidly accreting material to build up its black hole toward a quasar.

To probe the role of dense gas in obscuration and black hole growth, we place the two targets on the $\lambda_{\rm Edd}$–$N_{\rm H}$ relation from (cite: riccinature17) (Figure [4](#fig:nh_edd)), derived from 836 local X-ray AGNs (cite: cricci17b; koss17). In this framework, $\lambda_{\rm Edd}$ regulates nuclear obscuration, with AGNs evolving from an obscured growth phase to a short, unstable blowout phase and finally to an unobscured quasar stage.

We find that `cid_414` lies in the “forbidden region" where radiation pressure is expected to clear the obscuring gas, yet its He i$\lambda$10830 absorption feature does not show a significant velocity offset. Because absorption lines probe only gas along the line of sight, this does not necessarily imply the absence of outflows. Instead, the high-velocity shell may already have been cleared from our viewing direction, leaving behind dense clumps that are more resistant to radiative acceleration or newly infalling material that produces near-systemic absorption. Alternatively, the main outflow may be oriented away from our line of sight, such that the high Eddington ratio drives blowout but no blueshifted absorption is detected in projection.

In contrast, `cid_947` remains obscured despite its larger black hole mass, suggesting that its main growth phase likely occurred earlier. Strong outflows have also been observed in AGN that remain in the obscured phase (cite: alonso21), indicating that powerful winds can be launched before the obscuring material is fully cleared. The persistence of obscuration therefore suggests a time delay between the onset of outflows and the removal of the surrounding gas.

We further model the nuclear absorber using `CLOUDY` C25.00 (cite: c25), adopting an AGN continuum plus the UV background (cite: mf87). We vary $\log U$ ($-4$ to $2$), $\log n_{\rm H}$ ($2$ to $10$), and metallicity, fixing $N_{\rm H}$ to the observed value. The best-fit parameters that reproduce the observed He i$\lambda$10830 column densities are $\log U = -1.0_{-0.5}^{+0.2}$ and $\log n_{\rm H} = 10.0_{+1.0}^{-0.8}$ for `cid_414`, and $\log U = 0.0_{-1.0}^{+0.3}$ and $\log n_{\rm H} = 9.0_{+2.0}^{-0.8}$ for `cid_947`. The results are insensitive to metallicity between 0.1 and 1 $Z_\odot$. The inferred high gas densities are consistent with predictions for LRDs (cite: kohei25).

## Dust torus and dense absorbing gas geometry

Given the MIRI detections at $\geq10$–$20~\mu$m and the constraints from the photoionization modelling, we tentatively explore the geometry of the AGN-heated dust and the dense absorbing gas. In the SED fitting (Figure [2](#fig:sed)), we include dust components modeled as blackbodies with temperatures of 1500 K. For `cid_414`, the MIRI fluxes between 10 and 21 $\mu$m are well reproduced by a $\sim1500$ K component. Together with the prominent outflow signatures, these results suggest that `cid_414` is experiencing strong AGN feedback associated with rapid SMBH growth.

The geometry of the dense absorbing gas is likely complex, and our discussion below provides only a simplified estimate. Under a single-slab assumption, the absorber thickness is $l = N_{\rm H}/n_{\rm H}$, giving $l \sim 1.0\times10^{-7}-6.5\times10^{-6}$ pc for `cid_414` and $l \sim 9.5\times10^{-7}-6.0\times10^{-4}$ pc for `cid_947`. The distance between the absorber and the ionizing source is estimated using the ionization parameter: $$\begin{equation}
r = \sqrt{\frac{L_{\rm bol} f_{\rm ion}}{4\pi n_{\rm H} c U \langle h\nu_{\rm ion} \rangle}},
\end{equation}$$ where $f_{\rm ion}$ and $\langle h\nu_{\rm ion} \rangle$ are determined by the AGN SED (cite: mf87). Using our best-fitting values of $U$, we obtain $r \sim 0.007-0.027$ pc for `cid_414` and $r \sim 0.002-0.037$ pc for `cid_947`. Combined with the ionization parameter and density inferred from the CLOUDY modelling, the dense gas in `cid_414` likely resides very close to the nucleus with a small covering factor. This dense material remains in the line of sight, producing absorption on top of the emission lines even as the system enters a blowout phase. For `cid_947`, the absorbing gas probably resides near the outer BLR, tracing multiple outflowing clumps. These clouds are strongly heated by the AGN radiation field, which lowers the total hydrogen density and produces a higher ionization parameter.

Assuming thermal equilibrium, the inner radius of the dusty torus is $$\begin{equation}
R_{\rm torus} = \sqrt{\frac{L_{\rm bol}}{4\pi\sigma T^{4}}},
\end{equation}$$ where $\sigma$ is the Stefan–Boltzmann constant and we adopt a dust sublimation temperature of $T = 1500$ K (cite: zhang15), yielding $R_{\rm torus} \approx 1.19$ pc for `cid_414` and $R_{\rm torus} \approx 0.54$ pc for `cid_947`. Considering the uncertainty in $L_{\rm bol}$ converted from the X-ray $\,2$–$10$ keV luminosity, we also adopt the $L_{\rm bol}$ estimated from the SED fitting described in Section [3.4](#sec:sed). This yields $R_{\rm torus} = 0.86$–$1.19$ pc for `cid_414` and $0.54$–$0.96$ pc for `cid_947`. The absorber thickness and distance are smaller than the torus scale and comparable to the BLR size (cite: juodzbalis24), implying that the absorbing gas lies at BLR-like radii, shares the BLR kinematics, and is influenced by the obscuration geometry of the hot dust torus.

## Luminosity function and comparison with other AGN populations 

We further compare this population of X-ray and MIRI bright AGNs with dense absorbing gas to other populations, including type I quasars, X-ray selected AGNs, and LRDs.

With the F444W grism spectral coverage, we are able to detect He i$\lambda$10830 at redshifts $z = 2.7$–$3.6$. Besides the two targets analyzed in this work, there are two additional sources in the C3D coverage that exhibit He i$\lambda$10830 absorption and MIRI detections (one reported in (cite: shuqi25), and another with very weak He i$\lambda$10830 absorption, $\log N_{\rm He\textsc{i}}<12.0$). We do not present them in this work because they did not have secure spectroscopic redshifts prior to the C3D observations, which excludes them based on our selection criteria described in Section [2](#sec:target_selection). We plot the loosely constrained luminosity function (LF) of the two AGNs at $z \sim 3$ in Figure [6](#fig:lf), and the LF including the two additional sources is indicated by the black dashed line. We estimate the luminosity density $\Phi$ following (cite: sun23) as $\Phi = N_{\rm src}/(V_{\rm max},\mathrm{d}\log L)$, where $N_{\rm src}$ is the number of objects in the luminosity bin, $\mathrm{d}\log L$ is the bin width, and $V_{\rm max}$ is the comoving volume (in Mpc$^{-3}$) within the redshift interval $z=2.7$–3.6 and the 0.14 deg$^{2}$ C3D MIRI coverage area. Since no previous He i$\lambda$10830 absorption X-ray AGN LF exists at $z\sim3$ and our selection in this work is not strictly complete, we do not apply any completeness correction. Instead, we treat the resulting LF as a lower limit and plot it in Figure [6](#fig:lf). The abundance of AGNs with He i$\lambda$10830 absorption and mid-IR detections is about 0.7 dex lower than the predicted abundance of quasars with similar luminosities at $z=3$ (black dashed line; (cite: shen20)), and about one dex lower than the LRD population at $z=$5–7 (cite: akins).

In the pre-JWST era, broad absorption line (BAL) quasars accounted for 10–30% of the total quasar population (cite: balfrac_radio; balfrac_xray; balfrac), and most identified BAL systems showed absorption in high-ionization transitions such as C iv and Si iv. JWST has now revealed more AGNs exhibiting He i$\lambda$10830 and/or Balmer-line absorption at high redshift (cite: maiolino23; matthee24). The fraction of LRDs with Balmer absorption at $z = 4$-$6$ can reach 10–20% (cite: lin+24). We note that most current JWST spectra of LRDs with He i$\lambda$10830 absorption have been obtained using the low–resolution prism, and the fraction of AGNs exhibiting such absorption may increase as higher–resolution spectroscopy becomes more widely available.

We note that our estimate is based on only two objects, and a larger sample is required to place stronger constraints on the luminosity function of absorption-line AGNs at this epoch.

# Summary

In this letter, we present two AGNs (`cid_414` and `cid_947`) at $z\sim3$ in the COSMOS field that are detected in X-rays and the mid-infrared and exhibit prominent He i$\lambda$10830 absorption. The objects are selected from the COSMOS X-ray AGN catalog (cite: marchesi16b) and are required to be covered by the MIRI observations in the COSMOS-3D survey. The two sources show distinct rest-frame UV–optical SEDs: `cid_414` displays an LRD-like V-shaped SED, while `cid_947` has a flatter UV–optical slope. A strong Ly$\alpha$ emission line is detected in `cid_414` with no accompanying UV metal emission, whereas `cid_947` shows blueshifted He i$\lambda$10830 absorption consistent with outflows traced by C iv and Si iv. These properties suggest that the two AGNs may probe different black hole growth stages or AGN types, while both are embedded in dense gas and luminous in X-rays and the mid-infrared.

We investigate the role of dense absorbing gas in AGN obscuration and black hole growth in these two systems. The source `cid_414` has a higher X-ray luminosity, $\lambda_{\rm Edd}$ and lower gas obscuration fraction.

The $N_{\rm H}$ and $\lambda_{\rm Edd}$ values suggest that `cid_414` is in an unstable blowout phase, in which radiation pressure is clearing the obscuring gas, whereas `cid_947` remains in a more obscured phase. Photoionization modeling further indicates that the dense absorbing gas is much smaller in scale than the dusty torus and likely resides near the outer regions of the broad-line region. Together with the He i$\lambda$10830 absorbing gas in LRDs detected at $z \sim 3$, we suggest that dense absorbing gas is plausibly common during periods of rapid black hole growth and may play a critical role in regulating AGN obscuration and the co-evolution of black holes and their host galaxies. A larger sample is needed to better constrain the luminosity function and to establish a more complete evolutionary picture of such absorption-line AGNs, including LRDs, at high redshift.

# Acknowledgements

This work is sponsored by the National Key R&D Program of China (MOST) with grant no.2022YFA1605300. ZJL and SZ acknowledge support from the Chinese Academy of Sciences (no. E5295401). JBC acknowledges funding from the JWST Arizona/Steward Postdoc in Early galaxies and Reionization (JASPER) Scholar contract at the University of Arizona. ZJL, SZ, J-S.H anc C.C. acknowledges support from the National Natural Science Foundation of China (NSFC, grant No. 12273051) and the Chinese Academy of Sciences (no. E52H540101). C.C. acknowledges NSFC grant No. 12173045, China Manned Space Program with grant no. CMS-CSST-2025-A07 and Chinese Academy of Sciences South America Center for Astronomy (CASSACA) Key Research Project no. E52H540301. J.-T.S. is supported by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - Project number 518006966.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with programs #5893. Support for program #5893 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127. Some/all of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via . We acknowledge the strong support provided by the program coordinator Alison Vick and instrument reviewers Brian Brooks and Jonathan Aguilar. Support for this work was provided by NASA through grant JWST-GO-01727 awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-26555. This research employs a list of Chandra datasets, obtained by the Chandra X-ray Observatory, contained in 

# Facilities

JWST, HST, Chandra, Keck:I (LRIS), Keck:II (DEIMOS), ALMA, Herschel, VLA

natexlab

(ref: hscssp) Aihara, H., Armstrong, R., Bickerton, S., et al. 2018, PASJ, 70, S8, doi: [`10.1093/pasj/psx081`](http://doi.org/10.1093/pasj/psx081)

(ref: akins) Akins, H. B., Casey, C. M., Lambrides, E., et al. 2025, ApJ, 991, 37, doi: [`10.3847/1538-4357/ade984`](http://doi.org/10.3847/1538-4357/ade984)

(ref: alexander05) Alexander, D. M., Bauer, F. E., Chapman, S. C., et al. 2005, ApJ, 632, 736, doi: [`10.1086/444342`](http://doi.org/10.1086/444342)

(ref: alex13) Alexander, D. M., Stern, D., Del Moro, A., et al. 2013, ApJ, 773, 125, doi: [`10.1088/0004-637X/773/2/125`](http://doi.org/10.1088/0004-637X/773/2/125)

(ref: alex25) Alexander, D. M., Hickox, R. C., Aird, J., et al. 2025, New A Rev., 101, 101733, doi: [`10.1016/j.newar.2025.101733`](http://doi.org/10.1016/j.newar.2025.101733)

(ref: alonso21) Alonso-Herrero, A., Garcı́a-Burillo, S., Hönig, S. F., et al. 2021, A&A, 652, A99, doi: [`10.1051/0004-6361/202141219`](http://doi.org/10.1051/0004-6361/202141219)

(ref: alvarez23) Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2023, A&A, 671, A105, doi: [`10.1051/0004-6361/202245400`](http://doi.org/10.1051/0004-6361/202245400)

(ref: arevalo17) Arévalo, P., Bauer, F. E., Puccetti, S., et al. 2014, ApJ, 791, 81, doi: [`10.1088/0004-637X/791/2/81`](http://doi.org/10.1088/0004-637X/791/2/81)

(ref: 1995ApJ...455L.119B) Baldwin, J., Ferland, G., Korista, K., & Verner, D. 1995, ApJL, 455, L119, doi: [`10.1086/309827`](http://doi.org/10.1086/309827)

(ref: bertin20) Bertin, E., Schefer, M., Apostolakos, N., et al. 2020, in Astronomical Society of the Pacific Conference Series, Vol. 527, Astronomical Data Analysis Software and Systems XXIX, ed. R. Pizzo, E. R. Deul, J. D. Mol, J. de Plaa, & H. Verkouter, 461

(ref: cigale) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103, doi: [`10.1051/0004-6361/201834156`](http://doi.org/10.1051/0004-6361/201834156)

(ref: bc03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: buchner15) Buchner, J., Georgakakis, A., Nandra, K., et al. 2015, ApJ, 802, 89, doi: [`10.1088/0004-637X/802/2/89`](http://doi.org/10.1088/0004-637X/802/2/89)

(ref: jwst_pipeline) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2025, JWST Calibration Pipeline, 1.19.1 Zenodo, doi: [`10.5281/zenodo.6984365`](http://doi.org/10.5281/zenodo.6984365)

(ref: calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: chabrier) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: civano16) Civano, F., Marchesi, S., Comastri, A., et al. 2016, ApJ, 819, 62, doi: [`10.3847/0004-637X/819/1/62`](http://doi.org/10.3847/0004-637X/819/1/62)

(ref: degraaff25) de Graaff, A., Hviding, R. E., Naidu, R. P., et al. 2025a, arXiv e-prints, arXiv:2511.21820, doi: [`10.48550/arXiv.2511.21820`](http://doi.org/10.48550/arXiv.2511.21820)

(ref: graff25) de Graaff, A., Hviding, R. E., Naidu, R. P., et al. 2025b, arXiv e-prints, arXiv:2511.21820, doi: [`10.48550/arXiv.2511.21820`](http://doi.org/10.48550/arXiv.2511.21820)

(ref: ding20) Ding, X., Silverman, J., Treu, T., et al. 2020, ApJ, 888, 37, doi: [`10.3847/1538-4357/ab5b90`](http://doi.org/10.3847/1538-4357/ab5b90)

(ref: draine14) Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172, doi: [`10.1088/0004-637X/780/2/172`](http://doi.org/10.1088/0004-637X/780/2/172)

(ref: duras20) Duras, F., Bongiorno, A., Ricci, F., et al. 2020, A&A, 636, A73, doi: [`10.1051/0004-6361/201936817`](http://doi.org/10.1051/0004-6361/201936817)

(ref: faber79) Faber, S. M., & Gallagher, J. S. 1979, ARA&A, 17, 135, doi: [`10.1146/annurev.aa.17.090179.001031`](http://doi.org/10.1146/annurev.aa.17.090179.001031)

(ref: fabian09) Fabian, A. C., Vasudevan, R. V., Mushotzky, R. F., Winter, L. M., & Reynolds, C. S. 2009, MNRAS, 394, L89, doi: [`10.1111/j.1745-3933.2009.00617.x`](http://doi.org/10.1111/j.1745-3933.2009.00617.x)

(ref: ciao) Fruscione, A., McDowell, J. C., Allen, G. E., et al. 2006, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 6270, Observatory Operations: Strategies, Processes, and Systems, ed. D. R. Silva & R. E. Doxsey, 62701V, doi: [`10.1117/12.671760`](http://doi.org/10.1117/12.671760)

(ref: shuqi25) Fu, S., Zhang, Z., Jiang, D., et al. 2025, arXiv e-prints, arXiv:2512.02096. [`https://arxiv.org/abs/2512.02096`](https://arxiv.org/abs/2512.02096)

(ref: gilli07) Gilli, R., Comastri, A., & Hasinger, G. 2007, A&A, 463, 79, doi: [`10.1051/0004-6361:20066334`](http://doi.org/10.1051/0004-6361:20066334)

(ref: greene24) Greene, J. E., Labbe, I., Goulding, A. D., et al. 2024, ApJ, 964, 39, doi: [`10.3847/1538-4357/ad1e5f`](http://doi.org/10.3847/1538-4357/ad1e5f)

(ref: greene17) Greene, T. P., Kelly, D. M., Stansberry, J., et al. 2017, Journal of Astronomical Telescopes, Instruments, and Systems, 3, 035001, doi: [`10.1117/1.JATIS.3.3.035001`](http://doi.org/10.1117/1.JATIS.3.3.035001)

(ref: c25) Gunasekera, C. M., van Hoof, P. A. M., Dehghanian, M., et al. 2025, arXiv e-prints, arXiv:2508.01102, doi: [`10.48550/arXiv.2508.01102`](http://doi.org/10.48550/arXiv.2508.01102)

(ref: harikane23) Harikane, Y., Zhang, Y., Nakajima, K., et al. 2023, ApJ, 959, 39, doi: [`10.3847/1538-4357/ad029e`](http://doi.org/10.3847/1538-4357/ad029e)

(ref: deimos) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77, doi: [`10.3847/1538-4357/aabacf`](http://doi.org/10.3847/1538-4357/aabacf)

(ref: hickox2018) Hickox, R. C., & Alexander, D. M. 2018, ARA&A, 56, 625, doi: [`10.1146/annurev-astro-081817-051803`](http://doi.org/10.1146/annurev-astro-081817-051803)

(ref: balfrac_xray) Hiremath, P., Rankine, A. L., Aird, J., et al. 2025, MNRAS, 542, 2105, doi: [`10.1093/mnras/staf1352`](http://doi.org/10.1093/mnras/staf1352)

(ref: cat3dwind) Hönig, S. F., & Kishimoto, M. 2017, ApJL, 838, L20, doi: [`10.3847/2041-8213/aa6838`](http://doi.org/10.3847/2041-8213/aa6838)

(ref: clamato2) Horowitz, B., Lee, K.-G., Ata, M., et al. 2022, ApJS, 263, 27, doi: [`10.3847/1538-4365/ac982d`](http://doi.org/10.3847/1538-4365/ac982d)

(ref: xraydot) Hviding, R. E., de Graaff, A., Liu, H., et al. 2026, arXiv e-prints, arXiv:2601.09778, doi: [`10.48550/arXiv.2601.09778`](http://doi.org/10.48550/arXiv.2601.09778)

(ref: kohei25) Inayoshi, K., & Maiolino, R. 2025, ApJL, 980, L27, doi: [`10.3847/2041-8213/adaebd`](http://doi.org/10.3847/2041-8213/adaebd)

(ref: ishibashi18) Ishibashi, W., Fabian, A. C., Ricci, C., & Celotti, A. 2018, MNRAS, 479, 3335, doi: [`10.1093/mnras/sty1620`](http://doi.org/10.1093/mnras/sty1620)

(ref: ji15) Ji, T., Zhou, H., Jiang, P., et al. 2015, ApJ, 800, 56, doi: [`10.1088/0004-637X/800/1/56`](http://doi.org/10.1088/0004-637X/800/1/56)

(ref: superdeblended) Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56, doi: [`10.3847/1538-4357/aad4af`](http://doi.org/10.3847/1538-4357/aad4af)

(ref: jones25) Jones, B. L., Kocevski, D. D., Pacucci, F., et al. 2025, arXiv e-prints, arXiv:2510.07376, doi: [`10.48550/arXiv.2510.07376`](http://doi.org/10.48550/arXiv.2510.07376)

(ref: juodzbalis24) Juodžbalis, I., Ji, X., Maiolino, R., et al. 2024, MNRAS, 535, 853, doi: [`10.1093/mnras/stae2367`](http://doi.org/10.1093/mnras/stae2367)

(ref: kocevski23) Kocevski, D. D., Barro, G., McGrath, E. J., et al. 2023, ApJL, 946, L14, doi: [`10.3847/2041-8213/acad00`](http://doi.org/10.3847/2041-8213/acad00)

(ref: kocevski25) Kocevski, D. D., Finkelstein, S. L., Barro, G., et al. 2025, ApJ, 986, 126, doi: [`10.3847/1538-4357/adbc7d`](http://doi.org/10.3847/1538-4357/adbc7d)

(ref: kokorev25) Kokorev, V., Chisholm, J., Naidu, R. P., et al. 2025, arXiv e-prints, arXiv:2511.07515. [`https://arxiv.org/abs/2511.07515`](https://arxiv.org/abs/2511.07515)

(ref: kormendy13) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511, doi: [`10.1146/annurev-astro-082708-101811`](http://doi.org/10.1146/annurev-astro-082708-101811)

(ref: 2017ApJ...850...74K) Koss, M., Trakhtenbrot, B., Ricci, C., et al. 2017a, ApJ, 850, 74, doi: [`10.3847/1538-4357/aa8ec9`](http://doi.org/10.3847/1538-4357/aa8ec9)

(ref: koss17) Koss, M., Trakhtenbrot, B., Ricci, C., et al. 2017b, ApJ, 850, 74, doi: [`10.3847/1538-4357/aa8ec9`](http://doi.org/10.3847/1538-4357/aa8ec9)

(ref: hst814) Leauthaud, A., Massey, R., Kneib, J.-P., et al. 2007, ApJS, 172, 219, doi: [`10.1086/516598`](http://doi.org/10.1086/516598)

(ref: clamato) Lee, K.-G., Krolewski, A., White, M., et al. 2018, ApJS, 237, 31, doi: [`10.3847/1538-4365/aace58`](http://doi.org/10.3847/1538-4365/aace58)

(ref: leighly14) Leighly, K. M., Terndrup, D. M., Baron, E., et al. 2014, ApJ, 788, 123, doi: [`10.1088/0004-637X/788/2/123`](http://doi.org/10.1088/0004-637X/788/2/123)

(ref: li2021) Li, J., Silverman, J. D., Ding, X., et al. 2021, ApJ, 918, 22, doi: [`10.3847/1538-4357/ac06a8`](http://doi.org/10.3847/1538-4357/ac06a8)

(ref: galfits) Li, R., Ho, L. C., & Chen, C.-H. 2025a, arXiv e-prints, arXiv:2505.12867, doi: [`10.48550/arXiv.2505.12867`](http://doi.org/10.48550/arXiv.2505.12867)

(ref: ruancun25) Li, R., Ho, L. C., & Chen, C.-H. 2025b, arXiv e-prints, arXiv:2505.12867, doi: [`10.48550/arXiv.2505.12867`](http://doi.org/10.48550/arXiv.2505.12867)

(ref: lizijian2024) Li, Z.-J., Dai, Y. S., Huang, J. S., Wuyts, S., & Cao, T.-W. 2024, ApJ, 963, 99, doi: [`10.3847/1538-4357/ad1b54`](http://doi.org/10.3847/1538-4357/ad1b54)

(ref: zcosmos) Lilly, S. J., Le Fèvre, O., Renzini, A., et al. 2007, ApJS, 172, 70, doi: [`10.1086/516589`](http://doi.org/10.1086/516589)

(ref: lin+24) Lin, X., Wang, F., Fan, X., et al. 2024, ApJ, 974, 147, doi: [`10.3847/1538-4357/ad6565`](http://doi.org/10.3847/1538-4357/ad6565)

(ref: lin25) Lin, X., Fan, X., Cai, Z., et al. 2025, arXiv e-prints, arXiv:2507.10659, doi: [`10.48550/arXiv.2507.10659`](http://doi.org/10.48550/arXiv.2507.10659)

(ref: a3cosmos) Liu, D., Lang, P., Magnelli, B., et al. 2019, ApJS, 244, 40, doi: [`10.3847/1538-4365/ab42da`](http://doi.org/10.3847/1538-4365/ab42da)

(ref: liu17) Liu, T., Tozzi, P., Wang, J.-X., et al. 2017, ApJS, 232, 8, doi: [`10.3847/1538-4365/aa7847`](http://doi.org/10.3847/1538-4365/aa7847)

(ref: liu15) Liu, W.-J., Zhou, H., Ji, T., et al. 2015, ApJS, 217, 11, doi: [`10.1088/0067-0049/217/1/11`](http://doi.org/10.1088/0067-0049/217/1/11)

(ref: loiacono25) Loiacono, F., Gilli, R., Mignoli, M., et al. 2025, arXiv e-prints, arXiv:2506.12141, doi: [`10.48550/arXiv.2506.12141`](http://doi.org/10.48550/arXiv.2506.12141)

(ref: pep) Lutz, D., Poglitsch, A., Altieri, B., et al. 2011, A&A, 532, A90, doi: [`10.1051/0004-6361/201117107`](http://doi.org/10.1051/0004-6361/201117107)

(ref: Lyu24) Lyu, J., Alberts, S., Rieke, G. H., et al. 2024, ApJ, 966, 229, doi: [`10.3847/1538-4357/ad3643`](http://doi.org/10.3847/1538-4357/ad3643)

(ref: maiolino23) Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2024, A&A, 691, A145, doi: [`10.1051/0004-6361/202347640`](http://doi.org/10.1051/0004-6361/202347640)

(ref: marchesi16) Marchesi, S., Civano, F., Elvis, M., et al. 2016a, ApJ, 817, 34, doi: [`10.3847/0004-637X/817/1/34`](http://doi.org/10.3847/0004-637X/817/1/34)

(ref: marchesi16b) Marchesi, S., Lanzuisi, G., Civano, F., et al. 2016b, ApJ, 830, 100, doi: [`10.3847/0004-637X/830/2/100`](http://doi.org/10.3847/0004-637X/830/2/100)

(ref: agnfitter) Martı́nez-Ramı́rez, L. N., Calistro Rivera, G., Lusso, E., et al. 2024, A&A, 688, A46, doi: [`10.1051/0004-6361/202449329`](http://doi.org/10.1051/0004-6361/202449329)

(ref: mf87) Mathews, W. G., & Ferland, G. J. 1987, ApJ, 323, 456, doi: [`10.1086/165843`](http://doi.org/10.1086/165843)

(ref: matthee24) Matthee, J., Naidu, R. P., Brammer, G., et al. 2024, ApJ, 963, 129, doi: [`10.3847/1538-4357/ad2345`](http://doi.org/10.3847/1538-4357/ad2345)

(ref: ultravista) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156, doi: [`10.1051/0004-6361/201219507`](http://doi.org/10.1051/0004-6361/201219507)

(ref: merloni10) Merloni, A., Bongiorno, A., Bolzonella, M., et al. 2010, ApJ, 708, 137, doi: [`10.1088/0004-637X/708/1/137`](http://doi.org/10.1088/0004-637X/708/1/137)

(ref: naidu25) Naidu, R. P., Matthee, J., Kramarenko, I., et al. 2024, arXiv e-prints, arXiv:2410.01874, doi: [`10.48550/arXiv.2410.01874`](http://doi.org/10.48550/arXiv.2410.01874)

(ref: hermes) Oliver, S. J., Wang, L., Smith, A. J., et al. 2010, A&A, 518, L21, doi: [`10.1051/0004-6361/201014697`](http://doi.org/10.1051/0004-6361/201014697)

(ref: peca25) Peca, A., Koss, M. J., Oh, K., et al. 2025, ApJ, 990, 3, doi: [`10.3847/1538-4357/adec9a`](http://doi.org/10.3847/1538-4357/adec9a)

(ref: cricci17) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017a, ApJS, 233, 17, doi: [`10.3847/1538-4365/aa96ad`](http://doi.org/10.3847/1538-4365/aa96ad)

(ref: riccinature17) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017b, Nature, 549, 488, doi: [`10.1038/nature23906`](http://doi.org/10.1038/nature23906)

(ref: cricci17b) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017c, ApJS, 233, 17, doi: [`10.3847/1538-4365/aa96ad`](http://doi.org/10.3847/1538-4365/aa96ad)

(ref: ricci17) Ricci, F., La Franca, F., Onori, F., & Bianchi, S. 2017, A&A, 598, A51, doi: [`10.1051/0004-6361/201629380`](http://doi.org/10.1051/0004-6361/201629380)

(ref: ricci22) Ricci, F., Treister, E., Bauer, F. E., et al. 2022, ApJS, 261, 8, doi: [`10.3847/1538-4365/ac5b67`](http://doi.org/10.3847/1538-4365/ac5b67)

(ref: clauds) Sawicki, M., Arnouts, S., Huang, J., et al. 2019, MNRAS, 489, 5202, doi: [`10.1093/mnras/stz2522`](http://doi.org/10.1093/mnras/stz2522)

(ref: vla1.4ghz) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, ApJS, 188, 384, doi: [`10.1088/0067-0049/188/2/384`](http://doi.org/10.1088/0067-0049/188/2/384)

(ref: schreiber18) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30, doi: [`10.1051/0004-6361/201731506`](http://doi.org/10.1051/0004-6361/201731506)

(ref: balfrac_radio) Shankar, F., Dai, X., & Sivakoff, G. R. 2008, ApJ, 687, 859, doi: [`10.1086/591488`](http://doi.org/10.1086/591488)

(ref: shen20) Shen, X., Hopkins, P. F., Faucher-Giguère, C.-A., et al. 2020, MNRAS, 495, 3252, doi: [`10.1093/mnras/staa1381`](http://doi.org/10.1093/mnras/staa1381)

(ref: shuntov25) Shuntov, M., Akins, H. B., Paquereau, L., et al. 2025, arXiv e-prints, arXiv:2506.03243, doi: [`10.48550/arXiv.2506.03243`](http://doi.org/10.48550/arXiv.2506.03243)

(ref: vla3ghz) Smolčić, V., Novak, M., Delvecchio, I., et al. 2017, A&A, 602, A6, doi: [`10.1051/0004-6361/201730685`](http://doi.org/10.1051/0004-6361/201730685)

(ref: skirtor1) Stalevski, M., Fritz, J., Baes, M., Nakos, T., & Popović, L. Č. 2012, MNRAS, 420, 2756, doi: [`10.1111/j.1365-2966.2011.19775.x`](http://doi.org/10.1111/j.1365-2966.2011.19775.x)

(ref: skirtor2) Stalevski, M., Ricci, C., Ueda, Y., et al. 2016, MNRAS, 458, 2288, doi: [`10.1093/mnras/stw444`](http://doi.org/10.1093/mnras/stw444)

(ref: splash) Steinhardt, C. L., Speagle, J. S., Capak, P., et al. 2014, ApJL, 791, L25, doi: [`10.1088/2041-8205/791/2/L25`](http://doi.org/10.1088/2041-8205/791/2/L25)

(ref: suh20) Suh, H., Civano, F., Trakhtenbrot, B., et al. 2020, ApJ, 889, 32, doi: [`10.3847/1538-4357/ab5f5f`](http://doi.org/10.3847/1538-4357/ab5f5f)

(ref: sun23) Sun, F., Egami, E., Pirzkal, N., et al. 2023, ApJ, 953, 53, doi: [`10.3847/1538-4357/acd53c`](http://doi.org/10.3847/1538-4357/acd53c)

(ref: temple21) Temple, M. J., Hewett, P. C., & Banerji, M. 2021, MNRAS, 508, 737, doi: [`10.1093/mnras/stab2586`](http://doi.org/10.1093/mnras/stab2586)

(ref: science) Trakhtenbrot, B., Urry, C. M., Civano, F., et al. 2015, Science, 349, 168, doi: [`10.1126/science.aaa4506`](http://doi.org/10.1126/science.aaa4506)

(ref: ueda14) Ueda, Y., Akiyama, M., Hasinger, G., Miyaji, T., & Watson, M. G. 2014, ApJ, 786, 104, doi: [`10.1088/0004-637X/786/2/104`](http://doi.org/10.1088/0004-637X/786/2/104)

(ref: balfrac) Vivek, M., & Wylezalek, D. 2025, A&A, 695, L22, doi: [`10.1051/0004-6361/202453352`](http://doi.org/10.1051/0004-6361/202453352)

(ref: wangben25) Wang, B., Ishikawa, Y., Hennawi, J. F., et al. 2025a, MNRAS, doi: [`10.1093/mnras/staf1730`](http://doi.org/10.1093/mnras/staf1730)

(ref: wang25) Wang, B., de Graaff, A., Davies, R. L., et al. 2025b, ApJ, 984, 121, doi: [`10.3847/1538-4357/adc1ca`](http://doi.org/10.3847/1538-4357/adc1ca)

(ref: cosmos2020) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11, doi: [`10.3847/1538-4365/ac3078`](http://doi.org/10.3847/1538-4365/ac3078)

(ref: whitaker12) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: wuqiaoya25) Wu, Q., Shen, Y., Guo, H., et al. 2025, ApJ, 980, 134, doi: [`10.3847/1538-4357/ada386`](http://doi.org/10.3847/1538-4357/ada386)

(ref: yue24) Yue, M., Eilers, A.-C., Ananna, T. T., et al. 2024, ApJL, 974, L26, doi: [`10.3847/2041-8213/ad7eba`](http://doi.org/10.3847/2041-8213/ad7eba)

(ref: zhang15) Zhang, S., Zhou, H., Shi, X., et al. 2015, ApJ, 815, 113, doi: [`10.1088/0004-637X/815/2/113`](http://doi.org/10.1088/0004-637X/815/2/113)

(ref: zhuang23) Zhuang, M.-Y., & Ho, L. C. 2023, Nature Astronomy, 7, 1376, doi: [`10.1038/s41550-023-02051-4`](http://doi.org/10.1038/s41550-023-02051-4)

(ref: zhuang24) Zhuang, M.-Y., Li, J., & Shen, Y. 2024, ApJ, 962, 93, doi: [`10.3847/1538-4357/ad1517`](http://doi.org/10.3847/1538-4357/ad1517)

(ref: zhuang24b) Zhuang, M.-Y., & Shen, Y. 2024, ApJ, 962, 139, doi: [`10.3847/1538-4357/ad1183`](http://doi.org/10.3847/1538-4357/ad1183)

# Figures

![image](414_xray.pdf) ![image](947_xray.pdf)

![image](cid_414_galfits_rev1.pdf) ![image](cid_947_galfits_rev1.pdf)

[^1]: https://cosmos2025.iap.fr/

[^2]: <https://github.com/fengwusun/nircam_grism>

</paper>

Write the methods card for this paper.