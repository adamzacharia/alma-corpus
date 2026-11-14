# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1003..206S\sonnetcc\reply.txt

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
 "bibcode": "2026ApJ..1003..206S",
 "title": "The Identification of Two JWST/NIRCam-dark Starburst Galaxies at z = 6.6 with ALMA",
 "year": 2026,
 "journal": "The Astrophysical Journal",
 "first_author": "Sun, Fengwu",
 "n_authors": 24,
 "arxiv_id": "2506.06418",
 "doi": "10.3847/1538-4357/ae66e3",
 "alma_projects_linked_by_archive": [
  "2017.1.00139.S",
  "2017.1.01532.S",
  "2019.1.00147.S",
  "2021.1.00443.S",
  "2022.1.01077.L"
 ]
}
```

Paper text:
<paper>
#  The Identification of Two JWST/NIRCam-Dark Starburst Galaxies at $z=6.6$ with ALMA

## Abstract

We analyze two dusty star-forming galaxies at $z=6.6$. These galaxies are selected from the ASPIRE survey, a JWST Cycle-1 medium and ALMA Cycle-9 large program targeting 25 quasars and their environments at $z\simeq6.5 - 6.8$. These galaxies are identified as companions to UV-luminous quasars and robustly detected in ALMA continuum and \[C II\] emission, yet they are extraordinarily faint at the NIRCam wavelengths (down to $>28.0$ AB mag in the F356W band). They are more obscured than galaxies like Arp220, and thus we refer to them as “NIRCam-dark” starburst galaxies (star formation rate $\simeq 80 - 250$ M yr^−1^). Such galaxies are typically missed by (sub)-millimeter blank-field surveys. From the star-formation history (SFH), we show that the NIRCam-dark galaxies are viable progenitors of massive quiescent galaxies at $z\gtrsim4$ and descendants of UV-luminous galaxies at $z>10$. Although it is hard to constrain their number density from a quasar survey, we conclude that NIRCam-dark galaxies can be as abundant as $n\sim10^{-5.5}$ Mpc$^{-3}$ assuming a light halo occupation model. If true, this would equal to $\sim$30% of the number densities of both the quiescent galaxies at $z\gtrsim4$ and UV-luminous galaxies at $z>10$. We further predict that analogs at $z\sim8$ should exist according to the SFH of early massive quiescent galaxies. However, they may fall below the current detection limits of wide JWST and ALMA surveys, thus remaining “JWST-dark”. To fully trace the evolution of massive galaxies and dust-obscured cosmic star formation at $z\gtrsim8$, wide-field JWST/NIRCam imaging and slitless spectroscopic surveys of early protoclusters are essential.

# Introduction

Dust plays a pivot role in obscuring the majority of the cosmic star formation at redshift $z\simeq1-4$ (see a review by (cite: md14)). Since the end of the last century, dusty star-forming galaxies (DSFGs) with IR luminosities resembling those of local ultra-luminous infrared galaxies (ULIRGs; $L_\mathrm{IR}\simeq 10^{12} - 10^{13}$ L) have been found in abundance across the bulk of the cosmic history (e.g., (cite: smail97; hughes98; vieira10; oliver12) and reviews by, e.g., (cite: hodge20)). These galaxies, also known as submillimeter galaxies (SMGs), undergo vigorous starbursts with star formation rates (SFR) greater than 100 M yr^−1^, while only emitting a very small fraction of their light in the rest-frame UV/optical because of the strong dust obscuration. When they exhaust their cold molecular gas reservoirs, DSFGs are believed to evolve into massive quiescent galaxies at lower redshifts (cite: toft14).

Among all DSFGs discovered at (sub)-millimeter wavelengths, the optically faint DSFG population has been of particular interest. Simply placing the same DSFG from $z=0.5$ to higher redshifts, the brightness of the galaxy will drop quickly in the optical–IR, but remain almost unchanged at millimeter wavelengths because of the strong negative K correction. Therefore, a low flux density ratio between the rest-frame optical and far-IR is indicative of a high photometric redshift. Indeed, one of the first DSFGs discovered at 850 $\mu$m, HDF850.1 (cite: hughes98), remains undetected with HST from the optical to near-IR. The redshift of HDF850.1 is confirmed at $z=5.18$ through CO and \[C II\] spectroscopy with millimeter interferometry (cite: walter12). After more than two decades since its discovery, the stellar component of HDF850.1 was finally detected at 1–5 $\mu$m with JWST/NIRCam (cite: sunf24; hd25).

Similar galaxies have been referred to as “HST-dark”, “near-IR-dark”, “H-dropout”, or “H-faint” galaxies in a plethora of literature. These galaxies are found to have a wide range of redshift ($z \simeq 2-6$), stellar age and dust attenuation distribution, and they consist of 15-20% of DSFGs selected through ALMA millimeter observations (cite: chenc15; simpson15; franco18; wangt19; yamaguchi19; gomez22a; fujimoto24b).

So far, the vast majority of DSFGs selected through (sub-)millimeter surveys in blank fields are at $z\lesssim6$ (cite: simpson19; aravena20; dudzevic20; gomez22a; bingl23; fujimoto24b; long24b). At $z \gtrsim 6$, the Epoch of Reionization (EoR), the detections of DSFGs frequently rely on gravitational lensing (cite: riechers13; watson15; strandet17; zavala18; laporte21) and pointed ALMA observations of known luminous galaxies and quasars (cite: decarli17; mazzucchelli19; venemans19; hashimoto19; tamura19; harikane20; inami22; hygate23), especially through the Cycle-7 ALMA large program REBELS (cite: bouwens22). Many of these pointed observations succeeded in detecting the dust-obscured star formation not only in the targeted galaxies, but also their companions that could be totally obscured in the HST bands, and sometimes even Spitzer/IRAC 3.6/4.5 $\mu$m (cite: fudamoto21; fujimoto24b).

These studies highlight the importance of dust-obscured star formation even in the EoR, although the measurements of obscured SFR densities based on these pointed (and thus biased) observations remain highly challenging (cite: algera23; vanleeuwen24). If heavily obscured galaxies frequently exist at these redshifts but below the detection limit of wide-field imaging surveys, our understanding of massive galaxy assembly would be highly incomplete. In fact, JWST imaging and spectroscopic observations of early massive quiescent galaxies frequently imply the existence of starburst progenitors at $z \simeq 6 - 10$ with SFR above 100 M yr^−1^ (cite: carnall23a; glazebrook24; degraaff25a; baker25a). Some of these progenitors may have undergone highly efficient starbursts, converting the majority of accreted baryons to stars (cite: carnall24; turner25a). Associated with the starburst, these galaxies may be heavily dust-obscured and thus remain as an undetected population with JWST wide-field imaging surveys (cite: williams24; glazebrook24).

In this work, we present the identification and analyses of two NIRCam-dark galaxies at $z=6.6$ with ALMA. These two dusty starburst galaxies are selected through the ASPIRE JWST and ALMA survey (cite: wangf23; wangfprep). In Section [2](#sec:02_obs), we describe the observations and data processing techniques. We present the source selection, photometry and SED modeling in Section [3](#sec:03_res). We discuss the implications of these galaxies to the overall picture of massive galaxy evolution in Section [4](#sec:04_disc). Our conclusions are summarized in Section [5](#sec:05_sum). Throughout this work, we assume a flat $\Lambda$CDM cosmology with $H_0= 70$ km s^−1^ Mpc^−1^ and $\Omega_\mathrm{M} = 0.3$. AB magnitude system (cite: oke83) is adopted to describe source brightness in the optical and near-IR. We also assume a (cite: chabrier03) initial mass function. We define the IR luminosity ($L_\mathrm{IR}$) as the integrated luminosity over a rest-frame wavelength range from 8 to 1000 $\mu$m.

# Observation and Data Processing

## JWST/NIRCam

JWST/NIRCam (cite: rieke23) three-band imaging data of 25 luminous quasars at $z=6.5-6.8$ were obtained through the Cycle-1 ASPIRE program (GO-2078; PI: F. Wang; (cite: wangf23)). The exposure time with each filter is 1417 s (F115W), 2834 s (F200W) and 1417 s (F356W), respectively. The NIRCam data processing has been described in detail with previous papers from the ASPIRE collaboration (cite: wangf23; yangj23). Briefly, the data were processed through a modified JWST calibration pipeline (cite: jwst) with the reference file `jwst_1080.pmap` (including JWST Cycle-1 NIRCam flux calibrations). This includes a few commonly adopted customized treatments, for example, $1/f$ noise subtraction, iterative sky background removal and WCS alignment to Gaia DR3 (cite: gaiadr3) or the DESI Legacy Imaging Survey (cite: dey19) if not enough Gaia stars are found within the Field of View (FoV).

We also note that ASPIRE also obtained NIRCam wide-field slitless spectroscopy (WFSS) of the targeted quasar fields in the F356W band. These data were not directly used in our analyses (but see Section [4.2](#ss:04b_number)).

## ALMA

ALMA 1.2 mm mosaics of all 25 ASPIRE quasar fields were obtained through a 100-hr ALMA Cycle-9 large program (PI: F. Wang; Program ID: 2022.1.01077.L). In each quasar field, we map the 1.2$'$$\times$1.1$'$ region centered on the quasar at the \[C II\] 158 $\mu$m wavelength, and therefore search for companion galaxies at the quasar redshifts (within a velocity offset of $\Delta v \sim \pm2200$ km s^−1^).

The ALMA data reduction has been described in detail by (cite: sunf25a) through a standard CASA `v6.4.1.12` pipeline (cite: casa22). To avoid the artificial boost of continuum flux densities from \[C II\] emitters at quasar redshifts, we first flagged the spectral channels that have a velocity offset smaller than 500 km   s^−1^ from the quasar \[C II\] line center. To optimize the detection of sources with both compact and extended dust continuum or \[C II\] emissions, we produced ALMA mosaics at both native resolution (Briggs weighting `robust=0.5`, no *uv* tapering) and tapered resolution (`robust=2.0`, uv tapered with a Gaussian kernel of FWHM=1$''$0). The synthesized beam FWHM is 0.65$''$$\pm$0.05$''$ and 1.34$''$$\pm$0.05$''$ for native and tapered continuum image mosaics, respectively. The typical continuum rms noises (before primary beam response correction) of our ALMA mosaics are 0.031$\pm$0.004 mJy beam$^{-1}$ and 0.034$\pm$0.004 mJy beam$^{-1}$ at native and tapered resolution, respectively.

We also include archival ALMA measurements of our targets at Band 3, 4, 5 and 7. Band-3, 4, 5 observations were obtained through program 2017.1.00139.S, 2017.1.01532.S and 2019.1.00147.S (cite: venemans19; pensabene21; lij22). We directly use these published photometric measurements. Band 7 observations were obtained through 2021.1.00443.S (PI: J. Spilker), and the data were processed through a similar routine as that of the ASPIRE-ALMA data.

![](figures/fig1_jw_dark_img.pdf)

# Results

## The identification of NIRCam-dark galaxies

(cite: sunf25a) reported the detection of 117 continuum sources at primary beam response $\geq0.25$ (over 35 arcmin$^2$) through the ASPIRE-ALMA survey. Among these 1.2-mm continuum sources, 23 sources are quasars and the remaining sources are classified as DSFGs at cosmological distances. Six of these DSFGs are at $z>6$, all confirmed as quasar companions through ALMA \[C II\] detection or JWST/NIRCam grism spectroscopy of the \[O III\] doublets.

Among all ASPIRE-ALMA continuum sources, we identify two galaxies detected at 1.2 mm at high significance ($8.7$ and $26.4\sigma$) but lacking obvious NIRCam counterparts. The NIRCam and ALMA images of these two galaxies are shown in Figure [1](#fig:img). Both galaxies are spectroscopically confirmed as companions to quasars at $z\sim6.6$ through ALMA \[C II\] spectroscopy. The first source, J0305m3150.C05 ($z=6.606$), was known as a companion galaxy to quasar J0305–3150 at $z=6.614$ through previous ALMA studies (cite: venemans19; venemans20; lij22; wangf23) with a velocity offset of $\Delta v = -290\pm30$ km s^−1^ and angular offset of 6.9$''$. The second source, J1526m2050.C02 ($z=6.590$), was also known as a companion galaxy to quasar J1526–2050 (or PSO J231–20, $z=6.587$) through previous ALMA studies (cite: decarli17; mazzucchelli19; pensabene21) with a velocity offset of $\Delta v = +137\pm30$ km s^−1^ and angular offset of 1.6$''$. The detections with multiple ALMA datasets at various frequencies validate the fidelity of these sources.

We conduct photometry of the two sources in available JWST/NIRCam and ALMA data. Because J1526m2050.C02 is close to the luminous quasar, we subtract a point spread function (PSF) model from the quasar image. The PSF model is constructed using a PSF star library in the ASPIRE fields.

The detailed method and validation of the PSF model and subtraction will be presented in a forthcoming paper from the ASPIRE collaboration (cite: yangjprep). The quasar-subtracted NIRCam images in the F200W and F356W bands are shown in the third row of Figure [1](#fig:img).

Compared with the ALMA continuum contours, we find faint diffuse emission (diameter $\sim1\ensuremath{''}$) at the location of J1526m2050.C02 in the F356W band. This is somewhat expected, because the surface brightness dimming is as a function of $(1+z)^{-4}$, and DSFGs at lower redshifts are known to host more extended stellar continuum (attenuated) than the dust continuum (cite: chenc15; hodge16). Therefore, to avoid substantial flux loss of diffuse emission, we obtain photometry using a circular aperture of radius $r=0.5\ensuremath{''}$. The photometric uncertainties are estimated using random apertures in source-free regions within 10$''$ from the targets. We find that J0305m3150.C05 remains undetected in all NIRCam images ($>$28.0 AB mag in F356W, $3\sigma$ limit), and the residuals of J1526m2050.C02 are only detected in the F356W band (26.5$\pm$0.1 AB mag).

These two DSFGs are extraordinarily faint at the NIRCam wavelengths. For comparison, all 289 DSFGs in (cite: mcKinney25a) that fall in COSMOS-Web footprint (cite: casey23) are brighter than 26 AB mag in the F444W band if measured with the same $r=0.5\ensuremath{''}$ aperture size. To our knowledge, DSFGs similar to J0305m3150.C05 or J1526m2050.C02 do not exist in ALMA blank-field surveys in the Hubble Ultra-Deep Field (HUDF) / GOODS-S region either (cite: dunlop17; hatsukade18; franco18; gl20; gomez22a), as all secure ($>6\sigma$) ALMA continuum sources have been detected by NIRCam (cite: boogaard24; hill24) as long as they fall in the JADES footprints (cite: eisenstein23a). Therefore, we refer to these galaxies as “NIRCam-dark” ($S_\mathrm{3.6\,\mu m}/S_\mathrm{1.2\,mm} < 10^{-4}$) starburst galaxies in this paper.

ALMA Band-6/7 flux densities are measured from the peak of the *uv*-tapered images as described by (cite: sunf25a). ALMA flux densities in other bands are taken from literature (cite: pensabene21; lij22). We also measure the ALMA 1.17 mm continuum sizes using CASA IMFIT function in the image plane with synthesized beam deconvolved. Both sources have compact dust continuum emission with circularized effective radius $R_\mathrm{e,circ} \sim 0.19\ensuremath{''}$ ($\sim1$ kpc at $z=6.6$). Table [1](#tab:01_phot) summarizes the JWST and ALMA photometry of the two NIRCam-dark DSFGs.

|                                             | J0305m3150.C05 | J1526m2050.C02 |
|:--------------------------------------------|---------------:|---------------:|
| R.A \[deg\]                                 |       46.31826 |      231.65781 |
| Decl. \[deg\]                               |      –31.84859 |      –20.83397 |
| $z_\mathrm{spec}$                           |          6.606 |          6.590 |
| Offset from quasar \[$''$\]                 |            6.9 |            1.6 |
| $R_\mathrm{e,circ}$ \[$''$\]                |  0.19$\pm$0.08 |  0.19$\pm$0.05 |
| NIRCam F115W \[nJy\]                        |        $<$56.4 |        $<$81.6 |
| NIRCam F200W \[nJy\]                        |        $<$24.6 |        $<$40.8 |
| NIRCam F356W \[nJy\]                        |   11.6$\pm$7.7 |   87.8$\pm$8.7 |
| ALMA 0.893 mm \[mJy\]                       |  0.64$\pm$0.04 |  1.71$\pm$0.04 |
| ALMA 1.17 mm \[mJy\]                        |  0.32$\pm$0.04 |  1.04$\pm$0.04 |
| $\log[M_\mathrm{star} / \si{M_\odot}]$      |   10.0$\pm$0.5 |   10.5$\pm$0.5 |
| $\log[\mathrm{SFR} / \si{M_\odot.yr^{-1}}]$ |    1.9$\pm$0.1 |    2.4$\pm$0.1 |
| $A_V$ \[mag\]                               |    7.5$\pm$3.7 |    3.5$\pm$0.4 |
| $\log[L_\mathrm{IR} / \si{L_\odot}]$        |   11.9$\pm$0.1 |   12.4$\pm$0.1 |
| $\log[M_\mathrm{gas} / \si{M_\odot}]$       |    9.5$\pm$0.2 |   10.4$\pm$0.2 |
| $\log[M_\mathrm{dust} / \si{M_\odot}]$      |    7.6$\pm$0.3 |    8.3$\pm$0.1 |
| $T_\mathrm{dust}$ \[K\]                     |  44.7$\pm$10.9 |   36.5$\pm$2.4 |

: The properties of the two NIRCam-dark galaxies.

![image](figures/J0305m3150.C05_SED.pdf) ![image](figures/J1526m2050.C02_SED.pdf)

## SED modeling and physical properties

We model the spectral energy distributions (SED) of the two NIRCam-dark galaxies with CIGALE, an energy-balance parametric SED-fitting software (cite: cigale09; cigale19). We assume a commonly used delayed-$\tau$ star-formation history (SFH), in which $\mathrm{SFR}(t) \propto t \exp(-t / \tau)$ and $\tau$ is the peak time of star formation. We allow the age of main stellar population to be 20–500 Myr and $\tau$ to be 20–2000 Myr. An optional late starburst is allowed in the last 20 Myr of SFH, which could produce up to 10% of the total stellar mass. We use (cite: bc03) stellar population synthesis models, and assume a solar metallicity ($Z_{\odot}$) given the strong presence of dust. We adopt a modified (cite: calzetti00) attenuation curve, and allow the variation of the power-law slope by $\pm$0.2 and $A_V$ effectively at 0–15. Nebular emission is included assuming an electron density of $n_e = 100$ cm^−3^ and ionization parameter $\log U=-4 \sim -2$. For simplicity, we assume a mid-to-far-IR dust continuum model from (cite: casey12), parameterized by the dust temperature ($T_\mathrm{dust}$; 30–60 K), dust emissivity ($\beta_\mathrm{em}$; 1.6–2.0) and mid-IR power-law slope ($\alpha_\mathrm{MIR}$, fixed at 2.0). Although the (cite: casey12) model does not include mid-IR polycyclic aromatic hydrocarbon (PAH) features, the inclusion of a mid-IR power-law slope can well reproduce the luminosity excess from PAHs from a comparison of widely used empirical SED templates (cite: chary01; rieke09) as tested by (cite: sunf25a).

We note that an active galactic nucleus (AGN) component is not included in our SED modeling. Both sources remain undetected in the X-ray with Chandra (cite: connor20; wangf21), disfavoring the presence of unobscured AGNs. The AGN contributions to the ALMA flux densities are also likely insignificant (see the discussion in (cite: sunf25a)).

Figure [2](#fig:sed) shows the best-fit SED models of the two NIRCam-dark galaxies. For comparison, we also plot the SED templates of () the nearby starburst galaxy Haro 11 ((cite: lyuj16), whose far-IR SED may resemble those of luminous DSFGs at $z\gtrsim6$ as argued by (cite: derossi18)), () the nearby ULIRG Arp 220 (cite: Silva98) and () the optically faint DSFGs at $z\sim3$ selected through the ALESS survey (cite: dacunha15), all normalized to the ALMA 1.2-mm flux densities. We find that the two NIRCam-dark galaxies appear to be more obscured in rest-frame optical even compared with Arp 220 or $z\sim3$ optically faint DSFGs. In particular, $z\sim3$ optically faint DSFGs in (cite: dacunha15) will remain above our F200W and F356W detection limit if they are redshifted to $z=6.6$. The SED fitting implies a substantial $V$-band dust attenuation ($A_V$ up to 7.5$\pm$3.7 mag for J0305m3150.C05) for these NIRCam-dark DSFGs.

The multiple-wavelength ALMA observations offer useful constraints to the far-IR SEDs. With IR luminosities $L_\mathrm{IR}\simeq10^{11.9} - 10^{12.4}$ L, we infer a dust-obscured SFR of 80–250 M yr^−1^ for the two sources (cite: ke12). These are consistent with the SFR inferred from the \[C II\] luminosities (cite: pensabene21; lij22). In contrast, the constraints on their stellar mass are rather poor. We infer stellar mass $\log(M_\mathrm{star}/M_\mathrm{\odot})$ of 10.0$\pm$0.5 and 10.5$\pm$0.5 for both targets respectively, and the large errors are natural consequence of poor constraints in the rest-frame UV/optical through Bayesian inference. The inferred physical properties of the two galaxies are also presented in Table [1](#tab:01_phot).

The molecular gas masses ($M_\mathrm{gas}$) of the two galaxies have been studied through \[C I\] and CO observations by (cite: pensabene21) and (cite: lij22). We find comparable $M_\mathrm{gas}$ and $M_\mathrm{star}$ for the two galaxies, indicating high gas fractions associated with the starbursts. We further model the far-IR SEDs of the two galaxies with a modified blackbody model assuming a dust absorption coefficient as $\kappa = 0.40 \times (\nu / 250)^{\beta_\mathrm{em}}$ in unit of cm^2^ g^−1^, where $\nu$ is the rest-frame frequency in GHz and $\beta_\mathrm{em}$ is fixed at 1.8 following previous works (cite: ds17; sunf22a). We also consider the CMB heating effect following (cite: dacunha13), which is found to be small at the derived $T_\mathrm{dust}$. The derived dust masses and temperatures are also presented in Table [1](#tab:01_phot). Although the constraints are poor for J0305m3150.C05 because of limited ALMA coverage, both sources exhibit normal dust temperature and gas-to-dust ratio $\delta_\mathrm{GDR}$ around 100.

# Discussion

![](figures/SFR_Mstar_vs_t.pdf)

## Placing NIRCam-dark starbursts in the context of massive galaxy evolution

These two NIRCam-dark galaxies are among the highest-redshift ALMA continuum sources selected by the ASPIRE-ALMA survey. The redshifts of our targets are also higher than the vast majority of DSFGs selected from millimeter surveys in blank fields ($z\lesssim6$; see references in Section [1](#sec:01_intro)). Therefore, a low flux density ratio of $S_\mathrm{3.6\ensuremath{\mu}m}/S_\mathrm{1.2\,mm}$ is somewhat expected at such high redshifts (cite: yamaguchi19), leading to the faintness of these galaxies at NIRCam wavelengths.

However, from the viewpoint of massive galaxy evolution, the identification of NIRCam-dark galaxies in the EoR could be particularly important. Figure [3](#fig:sfh) shows the stellar mass and SFR of NIRCam-dark galaxies compared with () the SFH of massive quiescent galaxies at $z\gtrsim4$ that have been frequently confirmed with JWST spectroscopy (cite: carnall23a; glazebrook24; baker25a; degraaff25a), and () $z>10$ luminous galaxies with low dust content confirmed by JWST (e.g., (cite: arrabalharo23; bunker23; carniani24; castellano24; kokorev25a; naidu25b; zavala25); also known as “blue monsters”, e.g., (cite: ziparo23)). From the SFH modeled from JWST spectrophotometry, it is evident that many of the massive quiescent galaxies at $z\gtrsim4$ are expected to be massive ($M_\mathrm{star}\gtrsim10^{9}$ M) star-forming (SFR $\gtrsim$ 10 M yr^−1^) galaxies at $z\sim12$, matching the observables of the “blue monsters” at this epoch. The inferred SFH of these early quiescent galaxies typically peak at $z\simeq 6 - 8$, with SFR at $\gtrsim100$ M yr^−1^.

We find that the stellar mass and SFR of NIRCam-dark DSFGs at $z\sim7$ exactly match the starburst progenitors of massive quiescent galaxies at $z\sim4$ (Figure [3](#fig:sfh)). The compact sizes of their dust continuum emission (and therefore the molecular gas reservoir; $R_\mathrm{e,circ} \sim$1 kpc) also resemble the compact stellar sizes of massive quiescent galaxies at $z\sim4$ (cite: jiz24b). We therefore argue that NIRCam-dark DSFGs are likely the progenitors of $z\sim4$ massive quiescent galaxies and descendants of $z>10$ “blue monsters”, or at least representing one viable intermediate galaxy population that can bridge the two massive galaxy populations before and after the EoR.

From cosmological simulations, it is also clear that the progenitors of $z\gtrsim4$ massive quiescent galaxies should be massive gas-rich starburst galaxies at $z\sim7$, matching the $M_\mathrm{star}$ and SFR of NIRCam-dark galaxies in our sample (e.g., see the SFHs in Figure [3](#fig:sfh) simulated by FLARES, (cite: lovell23); IllustrisTNG, (cite: pillepich18; nelson19), see also (cite: hartley23); THESAN, (cite: kannan22; chittenden25)).

However, we also note that many starburst galaxies with SFR $\gtrsim100$ M yr^−1^ at $z\sim7$ may quench at later epochs (e.g., $z\sim3$ from TNG100), possibly depending on the quenching physical mechanisms. The obscuration of starbursts at $z\sim7$ also depends on complicated physics of dust production (cite: lesniewska19; choban25), geometry and sometimes viewing angles (cite: cochrane24), many of which are not clear from either observational or theoretical perspectives. Specifically, the observed high dust-to-stellar mass ratio $\log(M_\mathrm{dust} / M_\mathrm{star}) \sim -2.3 \pm 0.5$ as observed for the two galaxies are perhaps particularly interesting. The observed $M_\mathrm{dust} / M_\mathrm{star}$ approaches the expectation from the “maximal dust model” at $z\sim7$ through core-collapse supernovae dust production by (cite: dayal22), and match the (cite: popping17b) model prediction at solar metallicity. Nevertheless, future deeper JWST imaging observations, in particular with multi-band MIRI imaging, are needed to provide tighter constraints on the $M_\mathrm{star}$ of the two objects and thus models of dust production (and destruction) for massive starburst galaxies in the EoR.

![image](figures/hmf_dark.pdf) ![image](figures/n_z_dark.pdf)

## The number density of NIRCam-dark starbursts

To assess whether NIRCam-dark starbursts are possible progenitors of $z\gtrsim4$ massive quiescent galaxies and descendants of $z>10$ blue monsters, we analyze the number densities of these galaxy populations. The number density of massive quiescent galaxies at $z\gtrsim4$ has been observed at $n \simeq 10^{-5} - 3\times10^{-5}$ Mpc^−3^ (cite: carnall23b; valentino23; long24a; baker25a). On the other hand, JWST also measures the number density of luminous Lyman-break galaxies (absolute UV magnitude $M_\mathrm{UV} \sim -21$, corresponding to a SFR $\sim$ 10 M yr^−1^) at $z\sim12$ as $n \sim 10^{-5}$ Mpc^−3^ (cite: donnan24; finkelstein24; robertson24; harikane25; naidu25b; whitler25). Therefore, if the abundance of NIRCam-dark DSFGs is also found to be $\sim10^{-5}$ Mpc^−3^, it would provide strong evidence to the evolutionary connection.

However, it is not easy to constrain the number density of NIRCam-dark galaxies because they are selected as companions of luminous quasars. Luminous quasars at $z\gtrsim6$ are now confirmed to generally reside in massive dark matter halos thanks to JWST/NIRCam observations, in particularly with WFSS (cite: kashino23; wangf23; eilers24; champagne25; pudoka25). Through the galaxy auto-correlation function, quasar-galaxy cross-correlation function and comparison with dark-matter-only simulations, the host halo masses of quasars are measured as $\log(M_\mathrm{halo})\gtrsim12.30$ from the EIGER survey (cite: eilers24) and similarly with the ASPIRE survey (cite: wangfprep). Such massive halos are rare at $z\sim6.6$ ($n<10^{-7}$ Mpc^−3^ based on the halo mass function, HMF model of (cite: murray13)), although the number density is still much higher than that of quasars at this epoch ($n=0.39\pm0.11$ Gpc^−3^; (cite: wangf19a)).

(cite: pizzati24a) developed an empirical quasar population model that successfully reproduces the clustering properties and luminosity functions (LF) of quasars based on N-body simulations. Following this model, the luminosity of a quasar (or galaxy) is dependent on the halo mass, and the probability distribution function that a halo could host a detectable quasar (or galaxy), $P(M_\mathrm{halo})$, can be approximated as a Gaussian function: $$\begin{equation}
    P(M_\mathrm{halo}) = P_\mathrm{max} \exp\{-\frac{[\log (M_\mathrm{halo}/ M_c)]^2}{2 \sigma_m^2}\}
    \label{eq:p_qso}
\end{equation}$$ where $P_\mathrm{max}$ is the maximum likelihood of halo occupation, $M_c$ is the characteristic halo mass, and $\sigma_m$ is the mass dispersion. Taking the HMF at $z=6.6$ (cite: murray13) and the shape of quasar-host HMF (RMS of $M_\mathrm{halo}$) inferred by (cite: pizzati24a) for EIGER quasars (cite: eilers24), we reproduce the observed quasar number density at $z\sim6.6$ with the parameter set $P_\mathrm{max} = 0.02$, $\log (M_c / M_\odot) = 12.73$, $\sigma_\mathrm{m} = 0.22$, and the resultant quasar host HMF is shown as the solid red line in Figure [4](#fig:n) (left panel). At the median $\log(M_\mathrm{halo}/M_\odot)\sim12.3$ of quasars, the fraction of halos that host a detectable quasar is very low ($\sim3\times10^{-3}$).

Quasars are already rare objects residing in these massive halos, which likely indicates a low duty cycle in the UV-bright phase (cite: eilers24; pizzati24a; wangfprep). With ASPIRE, we identify two NIRCam-dark galaxies in 25 massive halo environments at $z\simeq6.5 - 6.8$. Therefore, we conclude that the occurrence rate of NIRCam-dark galaxies ($f = 2/25=0.08_{-0.05}^{+0.10}$; error from Poisson statistics) must be much higher than that of the quasars, otherwise we would not be able to identify any NIRCam-dark galaxies with ASPIRE.

We explore the possible halo occupation models of NIRCam-dark galaxies in Figure [4](#fig:n) (left panel). The first model, dubbed “heavy model”, assumes that NIRCam-dark galaxies share the same halo characteristics ($M_c$ and $\sigma_m$, Equation [\[eq:p_qso\]](#eq:p_qso)) but with much larger $P_\mathrm{max}$ and thus higher occurrence rate. We note that the large halo mass of a quasar also implies a virial radius $R_{200} \sim 50$ proper kpc, large enough to encompass the observed NIRCam-dark companions. We simulate the $M_\mathrm{halo}$ mass distribution of quasars from the aforementioned quasar host HMF, apply $P(M_\mathrm{halo})$ and match the observed NIRCam-dark occurrence rate as observed by ASPIRE. We obtain $P_\mathrm{max} = 0.37_{-0.23}^{+0.46}$ from this heavy model, suggesting a high occupation fraction of NIRCam-dark galaxies in the most massive halos at this epoch. According to this model, the predicted number density of NIRCam-dark galaxies is $n = 8_{-5}^{+10} \times 10^{-9}$ Mpc^−3^, about 20$\times$ of that of UV-bright quasars but still much lower than that of $z\gtrsim4$ massive quiescent galaxies or $z>10$ blue monsters (Figure [4](#fig:n), right panel).

We also test an alternative model, dubbed “light model”, in which the occupation fraction of NIRCam-dark galaxies is constant above certain $M_\mathrm{halo}$ threshold. Based on TNG100, we find that most of the $z\sim6.5$ halos that host galaxies at SFR $>50$ M yr^−1^ have a “cutoff” halo masses at $\log(M_\mathrm{halo}/M_\odot) \geq {11.4}$, and thus we adopt the threshold. The halo occupation fraction is therefore the observed NIRCam-dark occurrence rate ($0.08_{-0.05}^{+0.10}$). At above the halo mass threshold, the expected number density of NIRCam-dark galaxy is $n = 3_{-2}^{+4} \times 10^{-6}$ Mpc^−3^. Under such a light model, the number density of NIRCam-dark galaxies will be about $30_{-20}^{+40}\%$ of those of $z\gtrsim4$ massive quiescent galaxies and $z>10$ blue monsters (Figure [4](#fig:n), right panel).

We conclude that the number density of NIRCam-dark galaxies at $z \sim 7$ remains highly unconstrained: it may be as low as $n \sim 10^{-8.1}$ Mpc^−3^, but could also be as high as $\sim 10^{-5.5}$ Mpc^−3^. From an abundance-matching perspective, this implies that a substantial fraction of the progenitors of massive quiescent galaxies at $z \gtrsim 4$, as well as the descendants of $z > 10$ blue monsters, could be NIRCam-dark at $z \sim 7$. This hypothesis will need to be tested through both observations and simulations, including studies of dust production and obscuration mechanisms.

We also emphasize that our models assume independent halo occupations for quasars and NIRCam-dark galaxies. If the two populations are correlated or anti-correlated, the number density estimates could be even more uncertain. We argue that the large $M_\mathrm{dust}$, high $A_v$ and high $M_\mathrm{dust}/M_\mathrm{star}$ of NIRCam-dark galaxies imply efficient dust production over extended period (e.g., $\sim300$ Myr; (cite: tamura19))–significantly longer than both the Salpeter timescale of quasar and the major merger timescale predicted by cosmological simulations, which are $\sim$ 50 Myr at this epoch (cite: snyder17). Therefore, while interactions between quasar host galaxies and NIRCam-dark galaxies may occur in the present or upcoming epoch, their halo occupations can still be treated as independent.

We also note that, according to the IRLF at $z \sim 7$ from (cite: fujimoto24b), the integrated number density of $z \sim 7$ DSFGs with SFR $\simeq 50$–$500$ M yr^−1^ is $n \sim 2 \times 10^{-5}$ Mpc^−3^. This exceeds the number density of $n \sim 5 \times 10^{-6}$ Mpc^−3^ derived from the $z \sim 7$ IRLF of (cite: barrufet23a) over the same SFR range, which is based on REBELS-ALMA observations of the $L_\mathrm{IR}$ of UV-luminous galaxies and the UVLF as a proxy. Although caution should be taken given the substantial uncertainties in the IRLFs at $z > 7$, if NIRCam-dark galaxies follow a “light model” of halo occupation, they may represent a substantial fraction (likely $\gtrsim 30\%$) of the (U)LIRG population and the obscured cosmic star formation rate density at $z \sim 7$. These galaxies are likely to be missed in most blank-field surveys due to their rarity and faintness in the near-IR. Indeed, the NIRCam-dark fraction of quasar companion DSFGs detected by ASPIRE-ALMA is 2/6 = 33%, consistent with the fraction inferred above.

Finally, we note that NIRCam-dark galaxies at $z\simeq6 - 7$ may reside above the detection limit of wide ALMA surveys like GOODS-ALMA 2.0 (cite: gomez22a), but the expected number of detections is only $N\sim0.5$ (and $N\sim1.5$ for general DSFGs with SFR $\simeq50-500$ M yr^−1^). Therefore, a non-detection so far is fully consistent with the cosmic shot noise.

![](figures/z8_predict.pdf)

## Multi-wavelength detectability

We further investigate the multi-wavelength detectability of NIRCam-dark galaxies in wide-area infrared and millimeter surveys, to assess whether NIRCam-dark galaxies are indeed a population missed by most of the high-redshift galaxy surveys obtained so far. The NIRCam imaging depth of the ASPIRE survey is slightly shallower than the average depth of CEERS (cite: finkelstein25), but is deeper than wider surveys like COSMOS-Web (cite: casey23) and COSMOS-3D (JWST-GO-5893, PI: Kakiichi, K.; cf. (cite: linx25b)). At $z = 6.6$, the F356W brightness of J1526m2050.C02 (and likely J0305m3150.C05) can be detected by surveys like JADES-medium (cite: eisenstein23a; deugenio25a) down to $\sim29$ AB mag with aperture size of $r=0.4\ensuremath{''}$ ($5\sigma$).

Indeed, a NIRCam-dark MIRI-only source was reported by (cite: pg24a) in the HUDF, and two heavily reddened NIRCam-faint MIRI sources at photometric redshifts $z \sim 8$ have also been reported by (cite: akins23a) in the COSMOS field. We note that these MIRI sources are rather compact, making them resembling reddened AGNs instead of DSFGs (similar to *Virgil* at $z=6.6$, (cite: rinaldi25a) and other HST-dark MIRI sources at $z>6$ in (cite: williams24)). NIRCam-dark ALMA-only sources have also been reported by (cite: fujimoto23a) through a deep 1.2-mm survey in the Abell 2744 lensing cluster field and (cite: bakx24) as \[C II\] emitters in quasar fields (cite: venemans20). However, we caution the relatively low S/N of these sources ($\lesssim5$ for continuum and $\lesssim6$ for emission-line scan within the ALMA spectral cubes). Further deeper imaging and spectroscopic confirmation are necessary to confirm the fidelity, redshifts and nature of these sources. We also remark that SPT0311-58, a extraordinarily luminous lensed DSFG at $z=6.90$ (cite: strandet17) can be classified as a NIRCam-dark galaxy according to the MIRI 10-$\mu$m detection (cite: am23a) but non-detection at $\leq5$$\mu$m with NIRSpec (cite: arribas24), although the contamination from the foreground lens may complicate the interpretation.

At higher redshifts, the IR detectability of NIRCam-dark galaxies (and DSFGs in general) may rapidly decrease because of the surface brightness dimming and K correction. Figure [5](#fig:z8) shows the SED model of J0305m3150.C05 but redshifted to $z=8$, scaled to a SFR of 60 M yr^−1^. The existence of galaxies with such SFR at $z\sim8$ is expected from the SFH of massive quiescent galaxies at $z\gtrsim4$, while most of the galaxies at $z\gtrsim8$ are observed at $M_\mathrm{UV} \lesssim -22$ mag (one of the brightest is EGSz8p7 at z=8.68; (cite: zitrin15; finkelstein24; harikane24a)), corresponding to unobscured SFR $\lesssim30$ M yr^−1^. In other words, dust-obscured star-forming galaxies at $z>8$ are clearly missing from the current JWST observations (or at least spectroscopic confirmation); one example of such a galaxy is MACS0416_Y1 at $z=8.31$ where the majority of the SFR is dust-obscured (cite: tamura19). We also note that MACS0416_Y1 likely resides in a complex galaxy overdensity (and thus massive halo) at $z\simeq8.3-8.5$ in and around the MACS0416 cluster field (cite: maz24; fudamoto25a).

We compare with the detection limits of multiple surveys at the JWST wavelengths and also far-infrared to millimeter wavelengths. At NIRCam wavelengths, the $z=8$ galaxy template will fall below the $5\sigma$ detection limit of wide surveys like JADES-medium (assuming $r=0.4\ensuremath{''}$ aperture), not to mention shallower surveys like CEERS (cite: finkelstein25), PRIMER (JWST-GO-1837, PI: J. Dunlop) and COSMOS-web (cite: casey23). At MIRI wavelengths, the galaxy will fall below the $5\sigma$ detection limit of wide surveys like SMILES (cite: alberts24a; riekeg24) and MEGA (cite: backhaus25), which is also the case for other wide surveys including PRIMER, COSMOS-Web and MEOW (JWST-GO-5407; PI: G. Leung). In these existing wide-area surveys, these galaxies will even appear “JWST-dark”.

In the far-IR, by considering realistic confusion noise limit, such a “JWST-dark” galaxy at $z=8$ will fall below the detection limit of Herschel/PACS and SPIRE at 70–500 $\mu$m (e.g., (cite: nguyen10; lutz11)), JCMT/SCUBA-2 at 450 and 850 $\mu$m (e.g., (cite: limc20a)) and even the planned PRIMA/PRIMAger at 47–235 $\mu$m (cite: donnan24). It will also fall below the confusion limit of single-dish millimeter facilities like IRAM30m/NIKA2 at 1.2 and 2 mm (cite: bingl23), and also wide-field ALMA Band-6 continuum surveys like GOODS-ALMA v2.0 (cite: gomez22a), not to mention shallower surveys like (Ex)-MORA (cite: casey21; long24b) and Cycle-10 large program CHAMPS (2023.1.00180.L; PI: A. Faisst). Therefore, we conclude that current wide-area extragalactic surveys are generally insensitive to “JWST-dark” galaxies at $z\sim8$.

If “JWST-dark” galaxies do exist at such an early epoch, how could we detect and confirm these galaxies? In fact, from Figure [5](#fig:z8), it is evident that the galaxy brightness is not far from the current detection limits in certain bands, specifically NIRCam F444W, MIRI F1000W$\sim$F1500W and ALMA Band-6/7. With a few hours of JWST integration and probably less than an hour of ALMA integration (especially with the upcoming wideband sensitivity upgrade; (cite: carpenter23)), these “JWST-dark” galaxies can be detected and studied with JWST and ALMA. We argue that the key is to locate the targets prior to the MIRI and ALMA follow-up observations with relatively small FoVs. This requires the selection of massive dark matter halos at $z\sim8$ in the first place (similar to the ASPIRE approach), possibly through wide-field NIRCam photometry and slitless spectroscopy of emission-line galaxies at $z\gtrsim8$ as protocluster tracers (cite: helton24b; maz24; fudamoto25a; liq25).

Through the JWST Cycle-3 large NIRCam WFSS campaigns like SAPPHIRES (cite: sunf25b), NEXUS (cite: sheny24), COSMOS-3D, and POPPIES (JWST-GO-5398, PI: Kartaltepe, J. & Rafelski, M.), more protocluster candidates will be selected at $z\gtrsim8$. The pure-parallel NIRCam WFSS programs (e.g., SAPPHIRES and POPPIES) are particularly important because they could overcome the strong cosmic variance through multiple independent sightlines (see (cite: sunf25b)). Combined with pointed NIRCam WFSS observations of massive galaxies (e.g., JWST-GO-6480, PI: Schouws, S.), these surveys will further unveil the existence of NIRCam-dark or even JWST-dark galaxies, measuring their clustering properties and halo occupation fraction (e.g., differentiating the light versus heavy model in Section [4.2](#ss:04b_number)), and thus providing key insights into the evolution history of massive galaxies and the dust-obscured cosmic star-formation history deeply into the EoR.

# Summary

We present a study of two NIRCam-dark dusty star-forming galaxies at $z=6.6$. These two galaxies are identified as companions to quasars through the ASPIRE JWST and ALMA survey, which targeted 25 UV-luminous quasars and their environments at $z \simeq 6.5 - 6.8$. The main results are summarized as follows:

1.  We securely detect ($>8\sigma$) the dust continuum emissions of the two galaxies through multiple ALMA bands, and the redshifts are confirmed through \[C II\] line spectroscopy, placing them as quasar companions at $z=6.6$. In contrast to the vast majority of DSFGs found through ALMA surveys in blank fields, these two sources are extraordinarily faint at the NIRCam wavelengths (F356W $>$ 28.0 mag for J0305m3150.C05 and 26.5$\pm$0.1 mag for J1526m2050.C02). We refer to them as NIRCam-dark galaxies because of their near-IR faintness ($S_\mathrm{3.6\,\mu m} / S_\mathrm{1.2\,mm} < 10^{-4}$).

2.  We obtain physical SED modeling of the two NIRCam-dark galaxies. These galaxies are undergoing starbursts (SFR $\simeq 80 - 250$ M yr^−1^), appear more obscured than Arp 220 (whole galaxy) and optically faint DSFGs at $z\sim3$ selected through the ALESS survey (cite: dacunha15). The stellar masses are poorly constrained ($\log(M_\mathrm{star}/M_\odot)\simeq 10.0 - 10.5$ with an error of 0.5 dex) because of the near-IR faintness.

3.  Given the mass, SFR and redshifts, we show that the NIRCam-dark galaxies are viable progenitors of massive quiescent galaxies at $z\gtrsim4$ according to their star formation histories. They could also be the descendants of certain UV-luminous galaxies at $z>10$ (“blue monsters”), bridging the two populations of massive galaxies before and after the epoch of reionization through an evolutionary perspective.

4.  We show that the number density of NIRCam-dark galaxies is highly unconstrained from biased surveys like ASPIRE ($n\simeq10^{-8.1} \sim 10^{-5.5}$ Mpc^−3^). However, based on a light halo occupation model that could match the ASPIRE observations, the number density of NIRCam-dark galaxies at $z\sim6.6$ could reach $n = 3_{-2}^{+4} \times 10^{-6}$ Mpc^−3^. If true, this will equal to $\sim30$% of the number density of massive quiescent galaxies at $z\gtrsim4$ and blue monsters at $z>10$, suggesting a substantial contribution to the dust-obscured cosmic star-formation rate density at $z\sim7$ through the “NIRCam-dark” population.

5.  From the SFH of massive quiescent galaxies at $z\gtrsim4$, galaxies with similar SFR should also exist at $z\sim8$. If a substantial fraction of them share a similar SED to that of J0305m3150.C05, these galaxies will reside below the detection limits of most wide-area JWST, ALMA and other single-dish (sub)-millimeter surveys obtained so far, and thus remaining “JWST-dark”. To study these “JWST-dark” galaxies, large-area JWST/NIRCam imaging and WFSS surveys of early galaxy protoclusters ($z\gtrsim8$) are essential. Deep JWST and ALMA follow-up observations of these protoclusters will likely detect such galaxies, offering deep insight to the dust-obscured cosmic star formation in the Epoch of Reionization.

# Acknowledgment

F.S. acknowledges funding from JWST/NIRCam contract to the University of Arizona, NAS5-02105 and support for JWST program #2883, 4924, 5105, 6434 provided by NASA through grants from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127. F.W. acknowledges support from NSF award AST-2513040. D.J.E’s contributions were supported by JWST/NIRCam contract to the University of Arizona, NAS5-02015, and as a Simons Foundation Investigator. S.E.I.B. is supported by the Deutsche Forschungsgemeinschaft (DFG) under Emmy Noether grant number BO 5771/1-1. L.C. acknowledges support by grant PIB2021-127718NB-100 from the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by “ERDF A way of making Europe” C.M. acknowledges support from Fondecyt Iniciacion grant 11240336 and the ANID BASAL project FB210003. F.S. thanks Tiger Hsiao and James Trussler for helpful discussions.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00139.S, 2017.1.01532.S, 2019.1.00147.S, 2021.1.00443.S and 2022.1.01077.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program #2078. Support for program #2078 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127.

FS led the ALMA data processing, analyses of the targets and the paper writing. JY led the NIRCam imaging data processing. FW led the JWST and ALMA observing programs. All co-authors contributed to the scientific interpretation of the results and helped to write the manuscript.

# Facilities

ALMA, JWST(NIRCam)

# Software

ASTROPY (cite: 2013A&A...558A..33A; 2018AJ....156..123A), CASA (cite: casa22), CIGALE (cite: cigale09; cigale19), JWST (cite: jwst), PHOTUTILS (cite: photutils)

natexlab

(ref: akins23a) Akins, H. B., Casey, C. M., Allen, N., et al. 2023, ApJ, 956, 61, doi: [`10.3847/1538-4357/acef21`](http://doi.org/10.3847/1538-4357/acef21)

(ref: alberts24a) Alberts, S., Lyu, J., Shivaei, I., et al. 2024, ApJ, 976, 224, doi: [`10.3847/1538-4357/ad7396`](http://doi.org/10.3847/1538-4357/ad7396)

(ref: algera23) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142, doi: [`10.1093/mnras/stac3195`](http://doi.org/10.1093/mnras/stac3195)

(ref: am23a) Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2023, A&A, 671, A105, doi: [`10.1051/0004-6361/202245400`](http://doi.org/10.1051/0004-6361/202245400)

(ref: aravena20) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, arXiv e-prints, arXiv:2006.04284. [`https://arxiv.org/abs/2006.04284`](https://arxiv.org/abs/2006.04284)

(ref: arrabalharo23) Arrabal Haro, P., Dickinson, M., Finkelstein, S. L., et al. 2023, Nature, 622, 707, doi: [`10.1038/s41586-023-06521-7`](http://doi.org/10.1038/s41586-023-06521-7)

(ref: arribas24) Arribas, S., Perna, M., Rodrı́guez Del Pino, B., et al. 2024, A&A, 688, A146, doi: [`10.1051/0004-6361/202348824`](http://doi.org/10.1051/0004-6361/202348824)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: backhaus25) Backhaus, B. E., Kirkpatrick, A., Yang, G., et al. 2025, arXiv e-prints, arXiv:2503.19078, doi: [`10.48550/arXiv.2503.19078`](http://doi.org/10.48550/arXiv.2503.19078)

(ref: baker25a) Baker, W. M., Lim, S., D’Eugenio, F., et al. 2025, MNRAS, 539, 557, doi: [`10.1093/mnras/staf475`](http://doi.org/10.1093/mnras/staf475)

(ref: bakx24) Bakx, T. J. L. C., Algera, H. S. B., Venemans, B., et al. 2024, MNRAS, 532, 2270, doi: [`10.1093/mnras/stae1613`](http://doi.org/10.1093/mnras/stae1613)

(ref: barrufet23a) Barrufet, L., Oesch, P. A., Bouwens, R., et al. 2023, MNRAS, 522, 3926, doi: [`10.1093/mnras/stad1259`](http://doi.org/10.1093/mnras/stad1259)

(ref: bingl23) Bing, L., Béthermin, M., Lagache, G., et al. 2023, A&A, 677, A66, doi: [`10.1051/0004-6361/202346579`](http://doi.org/10.1051/0004-6361/202346579)

(ref: boogaard24) Boogaard, L. A., Gillman, S., Melinder, J., et al. 2024, ApJ, 969, 27, doi: [`10.3847/1538-4357/ad43e5`](http://doi.org/10.3847/1538-4357/ad43e5)

(ref: cigale19) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103, doi: [`10.1051/0004-6361/201834156`](http://doi.org/10.1051/0004-6361/201834156)

(ref: bouwens22) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160, doi: [`10.3847/1538-4357/ac5a4a`](http://doi.org/10.3847/1538-4357/ac5a4a)

(ref: photutils) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2024, , 1.12.0 Zenodo, doi: [`10.5281/zenodo.10967176`](http://doi.org/10.5281/zenodo.10967176)

(ref: bc03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: bunker23) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, A&A, 677, A88, doi: [`10.1051/0004-6361/202346159`](http://doi.org/10.1051/0004-6361/202346159)

(ref: jwst) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2023, , 1.10.2 Zenodo, doi: [`10.5281/zenodo.7829329`](http://doi.org/10.5281/zenodo.7829329)

(ref: calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: carnall23a) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2023a, Nature, 619, 716, doi: [`10.1038/s41586-023-06158-6`](http://doi.org/10.1038/s41586-023-06158-6)

(ref: carnall23b) Carnall, A. C., McLeod, D. J., McLure, R. J., et al. 2023b, MNRAS, 520, 3974, doi: [`10.1093/mnras/stad369`](http://doi.org/10.1093/mnras/stad369)

(ref: carnall24) Carnall, A. C., Cullen, F., McLure, R. J., et al. 2024, MNRAS, 534, 325, doi: [`10.1093/mnras/stae2092`](http://doi.org/10.1093/mnras/stae2092)

(ref: carniani24) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024, Nature, 633, 318, doi: [`10.1038/s41586-024-07860-9`](http://doi.org/10.1038/s41586-024-07860-9)

(ref: carpenter23) Carpenter, J., Brogan, C., Iono, D., & Mroczkowski, T. 2023, in Physics and Chemistry of Star Formation: The Dynamical ISM Across Time and Spatial Scales, ed. V. Ossenkopf-Okada, R. Schaaf, I. Breloy, & J. Stutzki, 304, doi: [`10.48550/arXiv.2211.00195`](http://doi.org/10.48550/arXiv.2211.00195)

(ref: casa22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: casey12) Casey, C. M. 2012, MNRAS, 425, 3094, doi: [`10.1111/j.1365-2966.2012.21455.x`](http://doi.org/10.1111/j.1365-2966.2012.21455.x)

(ref: casey21) Casey, C. M., Zavala, J. A., Manning, S. M., et al. 2021, ApJ, 923, 215, doi: [`10.3847/1538-4357/ac2eb4`](http://doi.org/10.3847/1538-4357/ac2eb4)

(ref: casey23) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31, doi: [`10.3847/1538-4357/acc2bc`](http://doi.org/10.3847/1538-4357/acc2bc)

(ref: castellano24) Castellano, M., Napolitano, L., Fontana, A., et al. 2024, ApJ, 972, 143, doi: [`10.3847/1538-4357/ad5f88`](http://doi.org/10.3847/1538-4357/ad5f88)

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: champagne25) Champagne, J. B., Wang, F., Zhang, H., et al. 2025, ApJ, 981, 113, doi: [`10.3847/1538-4357/adb1bd`](http://doi.org/10.3847/1538-4357/adb1bd)

(ref: chary01) Chary, R., & Elbaz, D. 2001, ApJ, 556, 562, doi: [`10.1086/321609`](http://doi.org/10.1086/321609)

(ref: chenc15) Chen, C.-C., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 194, doi: [`10.1088/0004-637X/799/2/194`](http://doi.org/10.1088/0004-637X/799/2/194)

(ref: chittenden25) Chittenden, H. G., Glazebrook, K., Nanayakkara, T., et al. 2025, arXiv e-prints, arXiv:2504.19696, doi: [`10.48550/arXiv.2504.19696`](http://doi.org/10.48550/arXiv.2504.19696)

(ref: choban25) Choban, C. R., Salim, S., Kereš, D., Hayward, C. C., & Sandstrom, K. M. 2025, MNRAS, 537, 1518, doi: [`10.1093/mnras/staf118`](http://doi.org/10.1093/mnras/staf118)

(ref: cochrane24) Cochrane, R. K., Anglés-Alcázar, D., Cullen, F., & Hayward, C. C. 2024, ApJ, 961, 37, doi: [`10.3847/1538-4357/ad02f8`](http://doi.org/10.3847/1538-4357/ad02f8)

(ref: connor20) Connor, T., Bañados, E., Mazzucchelli, C., et al. 2020, ApJ, 900, 189, doi: [`10.3847/1538-4357/abaab9`](http://doi.org/10.3847/1538-4357/abaab9)

(ref: dacunha13) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13, doi: [`10.1088/0004-637X/766/1/13`](http://doi.org/10.1088/0004-637X/766/1/13)

(ref: dacunha15) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: dayal22) Dayal, P., Ferrara, A., Sommovigo, L., et al. 2022, MNRAS, 512, 989, doi: [`10.1093/mnras/stac537`](http://doi.org/10.1093/mnras/stac537)

(ref: degraaff25a) de Graaff, A., Setton, D. J., Brammer, G., et al. 2025, Nature Astronomy, 9, 280, doi: [`10.1038/s41550-024-02424-3`](http://doi.org/10.1038/s41550-024-02424-3)

(ref: derossi18) De Rossi, M. E., Rieke, G. H., Shivaei, I., Bromm, V., & Lyu, J. 2018, ApJ, 869, 4, doi: [`10.3847/1538-4357/aaebf8`](http://doi.org/10.3847/1538-4357/aaebf8)

(ref: decarli17) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: deugenio25a) D’Eugenio, F., Cameron, A. J., Scholtz, J., et al. 2025, ApJS, 277, 4, doi: [`10.3847/1538-4365/ada148`](http://doi.org/10.3847/1538-4365/ada148)

(ref: dey19) Dey, A., Schlegel, D. J., Lang, D., et al. 2019, AJ, 157, 168, doi: [`10.3847/1538-3881/ab089d`](http://doi.org/10.3847/1538-3881/ab089d)

(ref: ds17) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32, doi: [`10.3847/1538-4357/aa81d7`](http://doi.org/10.3847/1538-4357/aa81d7)

(ref: donnan24) Donnan, C. T., McLure, R. J., Dunlop, J. S., et al. 2024, MNRAS, 533, 3222, doi: [`10.1093/mnras/stae2037`](http://doi.org/10.1093/mnras/stae2037)

(ref: donnellan24) Donnellan, J. M. S., Oliver, S. J., Béthermin, M., et al. 2024, MNRAS, 532, 1966, doi: [`10.1093/mnras/stae1539`](http://doi.org/10.1093/mnras/stae1539)

(ref: dudzevic20) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: dunlop17) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861, doi: [`10.1093/mnras/stw3088`](http://doi.org/10.1093/mnras/stw3088)

(ref: eilers24) Eilers, A.-C., Mackenzie, R., Pizzati, E., et al. 2024, ApJ, 974, 275, doi: [`10.3847/1538-4357/ad778b`](http://doi.org/10.3847/1538-4357/ad778b)

(ref: eisenstein23a) Eisenstein, D. J., Willott, C., Alberts, S., et al. 2023, arXiv e-prints, arXiv:2306.02465, doi: [`10.48550/arXiv.2306.02465`](http://doi.org/10.48550/arXiv.2306.02465)

(ref: finkelstein24) Finkelstein, S. L., Leung, G. C. K., Bagley, M. B., et al. 2024, ApJL, 969, L2, doi: [`10.3847/2041-8213/ad4495`](http://doi.org/10.3847/2041-8213/ad4495)

(ref: finkelstein25) Finkelstein, S. L., Bagley, M. B., Arrabal Haro, P., et al. 2025, ApJL, 983, L4, doi: [`10.3847/2041-8213/adbbd3`](http://doi.org/10.3847/2041-8213/adbbd3)

(ref: franco18) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152, doi: [`10.1051/0004-6361/201832928`](http://doi.org/10.1051/0004-6361/201832928)

(ref: fudamoto21) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489, doi: [`10.1038/s41586-021-03846-z`](http://doi.org/10.1038/s41586-021-03846-z)

(ref: fudamoto25a) Fudamoto, Y., Helton, J. M., Lin, X., et al. 2025, arXiv e-prints, arXiv:2503.15597, doi: [`10.48550/arXiv.2503.15597`](http://doi.org/10.48550/arXiv.2503.15597)

(ref: fujimoto23a) Fujimoto, S., Bezanson, R., Labbe, I., et al. 2023, arXiv e-prints, arXiv:2309.07834, doi: [`10.48550/arXiv.2309.07834`](http://doi.org/10.48550/arXiv.2309.07834)

(ref: fujimoto24b) Fujimoto, S., Kohno, K., Ouchi, M., et al. 2024, ApJS, 275, 36, doi: [`10.3847/1538-4365/ad5ae2`](http://doi.org/10.3847/1538-4365/ad5ae2)

(ref: gaiadr3) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: glazebrook24) Glazebrook, K., Nanayakkara, T., Schreiber, C., et al. 2024, Nature, 628, 277, doi: [`10.1038/s41586-024-07191-9`](http://doi.org/10.1038/s41586-024-07191-9)

(ref: gomez22a) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 658, A43, doi: [`10.1051/0004-6361/202141615`](http://doi.org/10.1051/0004-6361/202141615)

(ref: gl20) González-López, J., Novak, M., Decarli, R., et al. 2020, arXiv e-prints, arXiv:2002.07199. [`https://arxiv.org/abs/2002.07199`](https://arxiv.org/abs/2002.07199)

(ref: harikane24a) Harikane, Y., Nakajima, K., Ouchi, M., et al. 2024, ApJ, 960, 56, doi: [`10.3847/1538-4357/ad0b7e`](http://doi.org/10.3847/1538-4357/ad0b7e)

(ref: harikane20) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93, doi: [`10.3847/1538-4357/ab94bd`](http://doi.org/10.3847/1538-4357/ab94bd)

(ref: harikane25) Harikane, Y., Inoue, A. K., Ellis, R. S., et al. 2025, ApJ, 980, 138, doi: [`10.3847/1538-4357/ad9b2c`](http://doi.org/10.3847/1538-4357/ad9b2c)

(ref: hartley23) Hartley, A. I., Nelson, E. J., Suess, K. A., et al. 2023, MNRAS, 522, 3138, doi: [`10.1093/mnras/stad1162`](http://doi.org/10.1093/mnras/stad1162)

(ref: hashimoto19) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71, doi: [`10.1093/pasj/psz049`](http://doi.org/10.1093/pasj/psz049)

(ref: hatsukade18) Hatsukade, B., Kohno, K., Yamaguchi, Y., et al. 2018, PASJ, 70, 105, doi: [`10.1093/pasj/psy104`](http://doi.org/10.1093/pasj/psy104)

(ref: helton24b) Helton, J. M., Sun, F., Woodrum, C., et al. 2024, ApJ, 974, 41, doi: [`10.3847/1538-4357/ad6867`](http://doi.org/10.3847/1538-4357/ad6867)

(ref: hd25) Herard-Demanche, T., Bouwens, R. J., Oesch, P. A., et al. 2025, MNRAS, 537, 788, doi: [`10.1093/mnras/staf030`](http://doi.org/10.1093/mnras/staf030)

(ref: hill24) Hill, R., Scott, D., McLeod, D. J., et al. 2024, MNRAS, 528, 5019, doi: [`10.1093/mnras/stae346`](http://doi.org/10.1093/mnras/stae346)

(ref: hodge20) Hodge, J. A., & da Cunha, E. 2020, Royal Society Open Science, 7, 200556, doi: [`10.1098/rsos.200556`](http://doi.org/10.1098/rsos.200556)

(ref: hodge16) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: hsiao24a) Hsiao, T. Y.-Y., Álvarez-Márquez, J., Coe, D., et al. 2024, ApJ, 973, 81, doi: [`10.3847/1538-4357/ad6562`](http://doi.org/10.3847/1538-4357/ad6562)

(ref: hughes98) Hughes, D. H., Serjeant, S., Dunlop, J., et al. 1998, Nature, 394, 241, doi: [`10.1038/28328`](http://doi.org/10.1038/28328)

(ref: hygate23) Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS, 524, 1775, doi: [`10.1093/mnras/stad1212`](http://doi.org/10.1093/mnras/stad1212)

(ref: inami22) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126, doi: [`10.1093/mnras/stac1779`](http://doi.org/10.1093/mnras/stac1779)

(ref: jiz24a) Ji, Z., Williams, C. C., Rieke, G. H., et al. 2024a, arXiv e-prints, arXiv:2409.17233, doi: [`10.48550/arXiv.2409.17233`](http://doi.org/10.48550/arXiv.2409.17233)

(ref: jiz24b) Ji, Z., Williams, C. C., Suess, K. A., et al. 2024b, arXiv e-prints, arXiv:2401.00934, doi: [`10.48550/arXiv.2401.00934`](http://doi.org/10.48550/arXiv.2401.00934)

(ref: kannan22) Kannan, R., Garaldi, E., Smith, A., et al. 2022, MNRAS, 511, 4005, doi: [`10.1093/mnras/stab3710`](http://doi.org/10.1093/mnras/stab3710)

(ref: kashino23) Kashino, D., Lilly, S. J., Matthee, J., et al. 2023, ApJ, 950, 66, doi: [`10.3847/1538-4357/acc588`](http://doi.org/10.3847/1538-4357/acc588)

(ref: ke12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: kokorev25a) Kokorev, V., Chávez Ortiz, Ó. A., Taylor, A. J., et al. 2025, arXiv e-prints, arXiv:2504.12504, doi: [`10.48550/arXiv.2504.12504`](http://doi.org/10.48550/arXiv.2504.12504)

(ref: laporte21) Laporte, N., Zitrin, A., Ellis, R. S., et al. 2021, MNRAS, 505, 4838, doi: [`10.1093/mnras/stab191`](http://doi.org/10.1093/mnras/stab191)

(ref: lesniewska19) Leśniewska, A., & Michałowski, M. J. 2019, A&A, 624, L13, doi: [`10.1051/0004-6361/201935149`](http://doi.org/10.1051/0004-6361/201935149)

(ref: lij22) Li, J., Venemans, B. P., Walter, F., et al. 2022, ApJ, 930, 27, doi: [`10.3847/1538-4357/ac61d7`](http://doi.org/10.3847/1538-4357/ac61d7)

(ref: liq25) Li, Q., Conselice, C. J., Sarron, F., et al. 2025, MNRAS, 539, 1796, doi: [`10.1093/mnras/staf543`](http://doi.org/10.1093/mnras/staf543)

(ref: limc20a) Lim, C.-F., Wang, W.-H., Smail, I., et al. 2020, ApJ, 889, 80, doi: [`10.3847/1538-4357/ab607f`](http://doi.org/10.3847/1538-4357/ab607f)

(ref: linx25b) Lin, X., Fan, X., Wang, F., et al. 2025, arXiv e-prints, arXiv:2504.08039, doi: [`10.48550/arXiv.2504.08039`](http://doi.org/10.48550/arXiv.2504.08039)

(ref: long24b) Long, A. S., Casey, C. M., McKinney, J., et al. 2024a, arXiv e-prints, arXiv:2408.14546, doi: [`10.48550/arXiv.2408.14546`](http://doi.org/10.48550/arXiv.2408.14546)

(ref: long24a) Long, A. S., Antwi-Danso, J., Lambrides, E. L., et al. 2024b, ApJ, 970, 68, doi: [`10.3847/1538-4357/ad4cea`](http://doi.org/10.3847/1538-4357/ad4cea)

(ref: lovell23) Lovell, C. C., Roper, W., Vijayan, A. P., et al. 2023, MNRAS, 525, 5520, doi: [`10.1093/mnras/stad2550`](http://doi.org/10.1093/mnras/stad2550)

(ref: lutz11) Lutz, D., Poglitsch, A., Altieri, B., et al. 2011, A&A, 532, A90, doi: [`10.1051/0004-6361/201117107`](http://doi.org/10.1051/0004-6361/201117107)

(ref: lyuj16) Lyu, J., Rieke, G. H., & Alberts, S. 2016, ApJ, 816, 85, doi: [`10.3847/0004-637X/816/2/85`](http://doi.org/10.3847/0004-637X/816/2/85)

(ref: maz24) Ma, Z., Sun, B., Cheng, C., et al. 2024, ApJ, 975, 87, doi: [`10.3847/1538-4357/ad7b32`](http://doi.org/10.3847/1538-4357/ad7b32)

(ref: md14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: mazzucchelli19) Mazzucchelli, C., Decarli, R., Farina, E. P., et al. 2019, ApJ, 881, 163, doi: [`10.3847/1538-4357/ab2f75`](http://doi.org/10.3847/1538-4357/ab2f75)

(ref: mcKinney25a) McKinney, J., Casey, C. M., Long, A. S., et al. 2025, ApJ, 979, 229, doi: [`10.3847/1538-4357/ada357`](http://doi.org/10.3847/1538-4357/ada357)

(ref: murray13) Murray, S. G., Power, C., & Robotham, A. S. G. 2013, Astronomy and Computing, 3, 23, doi: [`10.1016/j.ascom.2013.11.001`](http://doi.org/10.1016/j.ascom.2013.11.001)

(ref: naidu25b) Naidu, R. P., Oesch, P. A., Brammer, G., et al. 2025, arXiv e-prints, arXiv:2505.11263. [`https://arxiv.org/abs/2505.11263`](https://arxiv.org/abs/2505.11263)

(ref: nelson19) Nelson, D., Springel, V., Pillepich, A., et al. 2019, Computational Astrophysics and Cosmology, 6, 2, doi: [`10.1186/s40668-019-0028-x`](http://doi.org/10.1186/s40668-019-0028-x)

(ref: nguyen10) Nguyen, H. T., Schulz, B., Levenson, L., et al. 2010, A&A, 518, L5, doi: [`10.1051/0004-6361/201014680`](http://doi.org/10.1051/0004-6361/201014680)

(ref: cigale09) Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793, doi: [`10.1051/0004-6361/200912497`](http://doi.org/10.1051/0004-6361/200912497)

(ref: oke83) Oke, J. B., & Gunn, J. E. 1983, ApJ, 266, 713, doi: [`10.1086/160817`](http://doi.org/10.1086/160817)

(ref: oliver12) Oliver, S. J., Bock, J., Altieri, B., et al. 2012, MNRAS, 424, 1614, doi: [`10.1111/j.1365-2966.2012.20912.x`](http://doi.org/10.1111/j.1365-2966.2012.20912.x)

(ref: pensabene21) Pensabene, A., Decarli, R., Bañados, E., et al. 2021, A&A, 652, A66, doi: [`10.1051/0004-6361/202039696`](http://doi.org/10.1051/0004-6361/202039696)

(ref: pg24a) Pérez-González, P. G., Rinaldi, P., Caputi, K. I., et al. 2024, ApJL, 969, L10, doi: [`10.3847/2041-8213/ad517b`](http://doi.org/10.3847/2041-8213/ad517b)

(ref: pillepich18) Pillepich, A., Nelson, D., Hernquist, L., et al. 2018, MNRAS, 475, 648, doi: [`10.1093/mnras/stx3112`](http://doi.org/10.1093/mnras/stx3112)

(ref: pizzati24a) Pizzati, E., Hennawi, J. F., Schaye, J., et al. 2024, MNRAS, 534, 3155, doi: [`10.1093/mnras/stae2307`](http://doi.org/10.1093/mnras/stae2307)

(ref: popping17b) Popping, G., Somerville, R. S., & Galametz, M. 2017, MNRAS, 471, 3152, doi: [`10.1093/mnras/stx1545`](http://doi.org/10.1093/mnras/stx1545)

(ref: pudoka25) Pudoka, M., Wang, F., Fan, X., et al. 2025, arXiv e-prints, arXiv:2505.07932, doi: [`10.48550/arXiv.2505.07932`](http://doi.org/10.48550/arXiv.2505.07932)

(ref: riechers13) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329, doi: [`10.1038/nature12050`](http://doi.org/10.1038/nature12050)

(ref: riekeg24) Rieke, G. H., Alberts, S., Shivaei, I., et al. 2024, ApJ, 975, 83, doi: [`10.3847/1538-4357/ad6cd2`](http://doi.org/10.3847/1538-4357/ad6cd2)

(ref: rieke09) Rieke, G. H., Alonso-Herrero, A., Weiner, B. J., et al. 2009, ApJ, 692, 556, doi: [`10.1088/0004-637X/692/1/556`](http://doi.org/10.1088/0004-637X/692/1/556)

(ref: rieke23) Rieke, M. J., Kelly, D. M., Misselt, K., et al. 2023, PASP, 135, 028001, doi: [`10.1088/1538-3873/acac53`](http://doi.org/10.1088/1538-3873/acac53)

(ref: rinaldi25a) Rinaldi, P., Pérez-González, P. G., Rieke, G. H., et al. 2025, arXiv e-prints, arXiv:2504.01852, doi: [`10.48550/arXiv.2504.01852`](http://doi.org/10.48550/arXiv.2504.01852)

(ref: robertson24) Robertson, B., Johnson, B. D., Tacchella, S., et al. 2024, ApJ, 970, 31, doi: [`10.3847/1538-4357/ad463d`](http://doi.org/10.3847/1538-4357/ad463d)

(ref: sheny24) Shen, Y., Zhuang, M.-Y., Li, J., et al. 2024, arXiv e-prints, arXiv:2408.12713, doi: [`10.48550/arXiv.2408.12713`](http://doi.org/10.48550/arXiv.2408.12713)

(ref: Silva98) Silva, L., Granato, G. L., Bressan, A., & Danese, L. 1998, ApJ, 509, 103, doi: [`10.1086/306476`](http://doi.org/10.1086/306476)

(ref: simpson15) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 807, 128, doi: [`10.1088/0004-637X/807/2/128`](http://doi.org/10.1088/0004-637X/807/2/128)

(ref: simpson19) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43, doi: [`10.3847/1538-4357/ab23ff`](http://doi.org/10.3847/1538-4357/ab23ff)

(ref: smail97) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5, doi: [`10.1086/311017`](http://doi.org/10.1086/311017)

(ref: snyder17) Snyder, G. F., Lotz, J. M., Rodriguez-Gomez, V., et al. 2017, MNRAS, 468, 207, doi: [`10.1093/mnras/stx487`](http://doi.org/10.1093/mnras/stx487)

(ref: strandet17) Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017, ApJL, 842, L15, doi: [`10.3847/2041-8213/aa74b0`](http://doi.org/10.3847/2041-8213/aa74b0)

(ref: sunf22a) Sun, F., Egami, E., Fujimoto, S., et al. 2022, ApJ, 932, 77, doi: [`10.3847/1538-4357/ac6e3f`](http://doi.org/10.3847/1538-4357/ac6e3f)

(ref: sunf24) Sun, F., Helton, J. M., Egami, E., et al. 2024, ApJ, 961, 69, doi: [`10.3847/1538-4357/ad07e3`](http://doi.org/10.3847/1538-4357/ad07e3)

(ref: sunf25a) Sun, F., Wang, F., Yang, J., et al. 2025a, ApJ, 980, 12, doi: [`10.3847/1538-4357/ad9d0e`](http://doi.org/10.3847/1538-4357/ad9d0e)

(ref: sunf25b) Sun, F., Fudamoto, Y., Lin, X., et al. 2025b, arXiv e-prints, arXiv:2503.15587, doi: [`10.48550/arXiv.2503.15587`](http://doi.org/10.48550/arXiv.2503.15587)

(ref: tamura19) Tamura, Y., Mawatari, K., Hashimoto, T., et al. 2019, ApJ, 874, 27, doi: [`10.3847/1538-4357/ab0374`](http://doi.org/10.3847/1538-4357/ab0374)

(ref: toft14) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68, doi: [`10.1088/0004-637X/782/2/68`](http://doi.org/10.1088/0004-637X/782/2/68)

(ref: turner25a) Turner, C., Tacchella, S., D’Eugenio, F., et al. 2025, MNRAS, 537, 1826, doi: [`10.1093/mnras/staf128`](http://doi.org/10.1093/mnras/staf128)

(ref: valentino23) Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023, ApJ, 947, 20, doi: [`10.3847/1538-4357/acbefa`](http://doi.org/10.3847/1538-4357/acbefa)

(ref: vanleeuwen24) van Leeuwen, I. F., Bouwens, R. J., van der Werf, P. P., et al. 2024, MNRAS, 534, 2062, doi: [`10.1093/mnras/stae2171`](http://doi.org/10.1093/mnras/stae2171)

(ref: venemans19) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJL, 874, L30, doi: [`10.3847/2041-8213/ab11cc`](http://doi.org/10.3847/2041-8213/ab11cc)

(ref: venemans20) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130, doi: [`10.3847/1538-4357/abc563`](http://doi.org/10.3847/1538-4357/abc563)

(ref: vieira10) Vieira, J. D., Crawford, T. M., Switzer, E. R., et al. 2010, ApJ, 719, 763, doi: [`10.1088/0004-637X/719/1/763`](http://doi.org/10.1088/0004-637X/719/1/763)

(ref: walter12) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233, doi: [`10.1038/nature11073`](http://doi.org/10.1038/nature11073)

(ref: wangf19a) Wang, F., Yang, J., Fan, X., et al. 2019, ApJ, 884, 30, doi: [`10.3847/1538-4357/ab2be5`](http://doi.org/10.3847/1538-4357/ab2be5)

(ref: wangf21) Wang, F., Fan, X., Yang, J., et al. 2021, ApJ, 908, 53, doi: [`10.3847/1538-4357/abcc5e`](http://doi.org/10.3847/1538-4357/abcc5e)

(ref: wangf23) Wang, F., Yang, J., Hennawi, J. F., et al. 2023, ApJL, 951, L4, doi: [`10.3847/2041-8213/accd6f`](http://doi.org/10.3847/2041-8213/accd6f)

(ref: wangfprep) Wang, F., Yang, J., Hennawi, J. F., et al. in prep.,

(ref: wangt19) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211, doi: [`10.1038/s41586-019-1452-4`](http://doi.org/10.1038/s41586-019-1452-4)

(ref: watson15) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327, doi: [`10.1038/nature14164`](http://doi.org/10.1038/nature14164)

(ref: whitler25) Whitler, L., Stark, D. P., Topping, M. W., et al. 2025, arXiv e-prints, arXiv:2501.00984, doi: [`10.48550/arXiv.2501.00984`](http://doi.org/10.48550/arXiv.2501.00984)

(ref: williams24) Williams, C. C., Alberts, S., Ji, Z., et al. 2024, ApJ, 968, 34, doi: [`10.3847/1538-4357/ad3f17`](http://doi.org/10.3847/1538-4357/ad3f17)

(ref: yamaguchi19) Yamaguchi, Y., Kohno, K., Hatsukade, B., et al. 2019, ApJ, 878, 73, doi: [`10.3847/1538-4357/ab0d22`](http://doi.org/10.3847/1538-4357/ab0d22)

(ref: yangj23) Yang, J., Wang, F., Fan, X., et al. 2023, ApJL, 951, L5, doi: [`10.3847/2041-8213/acc9c8`](http://doi.org/10.3847/2041-8213/acc9c8)

(ref: yangjprep) Yang, J., Wang, F., Hennawi, J. F., et al. in prep.,

(ref: zavala18) Zavala, J. A., Montaña, A., Hughes, D. H., et al. 2018, Nature Astronomy, 2, 56, doi: [`10.1038/s41550-017-0297-8`](http://doi.org/10.1038/s41550-017-0297-8)

(ref: zavala25) Zavala, J. A., Castellano, M., Akins, H. B., et al. 2025, Nature Astronomy, 9, 155, doi: [`10.1038/s41550-024-02397-3`](http://doi.org/10.1038/s41550-024-02397-3)

(ref: ziparo23) Ziparo, F., Ferrara, A., Sommovigo, L., & Kohandel, M. 2023, MNRAS, 520, 2445, doi: [`10.1093/mnras/stad125`](http://doi.org/10.1093/mnras/stad125)

(ref: zitrin15) Zitrin, A., Labbé, I., Belli, S., et al. 2015, ApJL, 810, L12, doi: [`10.1088/2041-8205/810/1/L12`](http://doi.org/10.1088/2041-8205/810/1/L12)

</paper>

Write the methods card for this paper.