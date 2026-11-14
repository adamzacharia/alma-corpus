# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A.156X\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...696A.156X",
 "title": "PANORAMIC: Discovery of an ultra-massive grand-design spiral galaxy at z ∼ 5.2",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Xiao, Mengyuan",
 "n_authors": 29,
 "arxiv_id": "2412.13264",
 "doi": "10.1051/0004-6361/202453487",
 "alma_projects_linked_by_archive": [
  "2023.1.00180.L"
 ]
}
```

Paper text:
<paper>
# PANORAMIC: Discovery of an Ultra-Massive Grand-Design Spiral Galaxy at $z\sim5.2$

We report the discovery of an ultra-massive grand-design red spiral galaxy, named Zhúlóng (Torch Dragon), at $z_{\rm phot} = 5.2^{+0.3}_{-0.2}$ in the JWST PANORAMIC survey, identified as the most distant bulge+disk galaxy candidate with spiral arms known to date. Zhúlóng displays an extraordinary combination of properties: 1) a classical bulge centered in a large, face-on exponential stellar disk (half-light radius of $R_{\rm e} = 3.7 \pm 0.1 \, \mathrm{kpc}$), with spiral arms extending across 19 kpc; 2) a clear transition from the red, quiescent core ($F150W-F444W=3.1$ mag) with high stellar mass surface density ($\log(\Sigma M_{\star}/M_{\odot} \, \mathrm{kpc}^{-2}) = 9.91_{-0.09}^{+0.11}$) to the star-forming outer regions, as revealed by spatially resolved SED analysis, which indicates significant inside-out galaxy growth; 3) an extremely high stellar mass at its redshift, with $\log (M_{\star}/M_{\odot})=11.03_{-0.08}^{+0.10}$ comparable to the Milky Way, and an implied baryon-to-star conversion efficiency ($\epsilon \sim 0.3$) that is 1.5 times higher than even the most efficient galaxies at later epochs; 4) despite an active disk, a relatively modest overall star formation rate ($\mathrm{SFR} =66_{-46}^{+89} ~M_{\odot} \, \mathrm{yr}^{-1}$), which is $>$0.5 dex below the star formation main sequence at $z \sim 5.2$ and $>$10 times lower than ultra-massive dusty galaxies at $z=5-6$. Altogether, Zhúlóng shows that mature galaxies emerged much earlier than expected in the first billion years after the Big Bang through rapid galaxy formation and morphological evolution. Our finding offers key constraints for models of massive galaxy formation and the origin of spiral structures in the early universe.

# Introduction

A remarkable revelation from early James Webb Space Telescope (JWST) observations is the rapid evolution of galaxies at early cosmic times (cite: Adamo2024). Three years into the mission (cite: Gardner2023), evidence for faster growth and maturity among galaxies continues to accumulate. By nearly all common evolutionary metrics (stellar mass, luminosity, stellar structure), galaxies have evolved faster than expected prior to JWST (cite: Naidu2022; Boylan-Kolchin2023; Donnan2023; Ferreira2023; Finkelstein2024; Casey2024; deGraaff2024; Glazebrook2024; Shapley2024). This raises questions about the physical processes that drive the inferred rapid timescales associated with the observed evolution, and/or points to an earlier onset of galaxy formation.

At the forefront of these discoveries are massive galaxies. Panchromatic JWST imaging and spectroscopy from the observed optical to mid-infrared have confirmed not only that ultra-massive galaxies existed in the early Universe ($\log (M_{\star}/M_{\odot})>11$ at $z>5$), but that they may also exist at unexpectedly high abundance (cite: Labbe2023a; Xiao2024; Weibel2024). They are so massive, with almost Milky Way (MW) mass only at $\sim$1 Gyr after the Big Bang, suggesting that galaxies are forming in a more efficient way than previously thought. Based on their existence in small survey areas (typical JWST imaging campaigns from Cycle 1 $<100$ sq arcmin per field), these ultra-massive galaxies, like the ones reported in (cite: Xiao2024), require on average about 50% of the baryons in their dark matter halos to be converted into stars – two to three times more than even the most efficient galaxies at later times (cite: Moster2013; Wechsler2018; Shuntov2022). While questions remain about incomplete data or modeling assumptions for photometric samples (cite: Wangbingjie2024; Williams2024_RED; Desprez2024), cosmic variance from small fields and sample sizes also complicate interpretation. This motivates studies of known massive candidates, because if true, these findings definitively raise new important questions about the theory of evolutionary drivers of early galaxies.

A key constraint on evolutionary drivers of rapid galaxy growth is galaxy morphology. On this front, JWST is again producing surprising revelations pointing to accelerated maturity timescales for galaxies, when compared to the morphological census using the Hubble Space Telescope (HST). Prior to JWST, HST imaging suggested the emergence of disks and spiral galaxies (perhaps the pre-cursors of grand-design spirals seen locally) was a late forming phenomenon, with the backbone of the Hubble Sequence appearing as late as $z\sim2$ (cite: BLee2013; Mortlock2013). However, with JWST, there is now accumulating evidence that stellar disks formed earlier than we expected, making up $\sim50\%$ of galaxies up to $z<6$ (cite: Ferreira2022; Ferreira2023; VegaFerrero2024; Robertson2023; Kartaltepe2023; Jacobs2023; HuertasCompany2024). This is a factor of 10$\times$ more stellar disks than were thought to exist at this redshift prior to JWST. In addition, a few stellar spiral galaxies have also been reported at $z>3$ (cite: jain2024; Wangweichen2024; Umehata2024; Costantin2023; Wu2023). These new findings contrast with theoretical predictions that large stellar disks should predominantly form later in cosmic history (cite: Dekel2020; Belokurov2022; Gurvich2023; McCluskey2024).

Morphological constraints are of particular interest regarding ultra-massive galaxies, where the stellar structure lends important clues to the highly efficient buildup that is implied by their high masses at early times. To date, numerous extremely compact, massive quiescent galaxies have been spectroscopically confirmed with stellar absorption features at $z\gtrsim5$, and are extremely compact (cite: Carnall2023Natur; Weibel2024b; deGraaff2024). These findings mirror the established compact sizes of quiescent galaxies at cosmic noon, which are typically a factor of $>3$ smaller in size at fixed mass compared to star-forming galaxies (cite: vandokkum2008; vanderwel2014; faisst2017; Kawinwanichakij2021; Mowla2019b; Cutler2022). However, their compact structures are not a universal feature: three extreme star-forming examples of ultra-massive galaxies presented in (cite: Xiao2024) exhibit larger and irregular morphologies, raising the question of whether dust obfuscates the stellar morphology or if there is diversity in the population. With relatively few ultra-massive galaxies known (identified from relatively small NIRCam blank-field areas), a systematic study to characterize the morphologies of representative samples has not yet been carried out, preventing general conclusions about formation pathways using morphology.

Here, we report on the serendipitous discovery of a unique ultra-massive galaxy at $z_\mathrm{phot}\sim5.2$ in the PANORAMIC[^2] Survey (cite: Williams2024). Unlike the other ultra-massive candidates described above, it has a striking evolved morphology: a quiescent-like classical bulge + star-forming stellar disk + grand-design spiral arms (defined as spiral structures spanning the whole galaxy, from the nucleus to outskirts, with spiral arms starting at diametrically opposite points; e.g. (cite: Binney2008; Dobbs2014; Sellwood2022)), already at 1 billion years after the Big Bang. More interestingly, it is very large in stellar size (19 kpc in diameter), extremely massive ($\log (M_{\star}/M_{\odot})>11$, indicating high baryon-to-star formation efficiency), with a modest star formation rate with red color ($\mathrm{SFR} =66_{-46}^{+89} ~M_{\odot} \, \mathrm{yr}^{-1}$; F150W$-$F444W$\,\sim2.7$ mag). Considering only a few stellar spiral galaxies have been identified at $z>3$ (cite: jain2024; Wangweichen2024; Umehata2024; Costantin2023; Wu2023), this source becomes the most distant massive spiral galaxies discovered so far, providing direct empirical evidence of the rapid dynamical evolution of massive galaxies at $z>5$. Given its unique red color, morphology, and stellar properties, we name it Zhúlóng[^3].

This paper is organized as follows: In Section [2](#Sec: 2) we present the datasets used to measure photometry and photometric redshift methods. In Section [3](#Sec: measure) we present our methodology for measuring morphologies and SED modeling. In Section [4](#Sec: disc) we interpret the properties of this remarkable galaxy in the context of both the formation pathway of ultra-massive galaxies, and as the highest redshift example of a large, spiral galaxy. Throughout this paper, we adopt a Chabrier initial mass function (cite: Chabrier2003) to estimate SFR and stellar mass. We assume Planck cosmology (cite: Planck2020). with $(\Omega_\mathrm{m},\, \Omega_\mathrm{\Lambda},\, h,\, \sigma_\mathrm{8})=(0.3,\, 0.7,\, 0.7, \,0.81)$. When necessary, data from the literature have been converted with a conversion factor of $M_{\star}$ (cite: Salpeter1955) = 1.7 $\times$ $M_{\star}$ (cite: Chabrier2003). All magnitudes are in the AB system (cite: Oke1983), such that $m_{\rm AB} = 23.9 - 2.5$ $\times$ log(S$_{\nu}$ \[$\mu$Jy\]).

# Observational data

Zhúlóng ($\alpha$, $\delta$ \[J2000\] = 150.124874, 2.092919) was serendipitously discovered in the field (association) named j100024p0208 in the recent data release of the JWST PANORAMIC survey (cite: Williams2024), a pure parallel extragalactic NIRCam imaging program. The source was originally identified by chance during a search for massive galaxy candidates that were color-selected to exhibit a strong Balmer break at $z>3$ (cite: Long2024). Its spiral structure was identified during visual inspection of those candidates, and was unique among the sample. Zhúlóng lies within the NIRCam imaging footprint of the COSMOS-Web field (cite: Casey2023), but is not covered by the COSMOS-PRIMER program (cite: PRIMER).

![](1_v3.png)

## HST and JWST NIRCam observations

We utilize imaging data from archival HST observations, including F606W and F814W from HST/ACS (cite: koekemoer2007; koekemoer2011; grogin2011), and F160W from HST/WFC3 (cite: Momcheva2017; Mowla2019). The spiral galaxy is not detected in any HST images, and was discovered in JWST/NIRCam (cite: Rieke2023) images with filters F115W, F150W, F200W, F277W, F356W, and F444W obtained as part of the PANORAMIC Survey. For the four filters obtained by COSMOS-Web (F115W, F150W, F277W, F444W), we combine the imaging from the two surveys. The typical 5$\sigma$ depths, measured within a circular aperture of 0.16$^{\prime\prime}$ radius, are 27.5, 27.7, 28.2, 28.4, 28.8, and 28.3 mags for F115W, F150W, F200W, F277W, F356W, and F444W, respectively.

Multi-wavelength photometric measurements are derived following the same procedure as outlined in (cite: Weibel2024). Briefly, we use `SExtractor` (cite: Bertin1996) in dual image mode with an inverse-variance weighted stack of the longest wavelength NIRCam wide filters, F277W+F356W+F444W, as the detection image. In this study, fluxes are measured in 0.16$''$, 0.35$''$, 0.5$''$, and 0.7$''$ radius circular apertures in images that are point spread function (PSF)-matched to the F444W band. Total fluxes are derived from the Kron AUTO aperture provided by `SExtractor` in the F444W band, in addition to a correction based on the encircled energy of the Kron aperture on the F444W PSF. Detailed descriptions of data reduction and photometric measurements are provided in (cite: Williams2024).

## Longer-wavelength observations

Although Zhúlóng lies within the COSMOS-Web field, it falls in a gap in the MIRI F770W footprints. Observations at longer wavelengths cover the location of Zhúlóng, but none return a detection, which include *Spitzer* MIPS 24 μm (cite: LeFloch2009), *Herschel* PACS (cite: Lutz2011) and SPIRE (cite: oliver2012), NIKA2 Cosmological Legacy Survey at 1.2mm and 2.0mm (cite: Bing2023), ALMA 2.0mm (rms of 0.12 mJy beam$^{-1}$; Project ID: 2021.1.00705.S), ALMA 3.0mm (rms of 0.06 mJy beam$^{-1}$; Project ID: 2021.1.01005.S), and VLA 3 GHz (cite: Smolcic2017) and 1.4 GHz (cite: Schinnerer2010). More recently, the ALMA large program CHAMPS (PI: A. Faisst; priv. comm.; Faisst et al. in prep) also covers Zhúlóng at 1.2 mm, but again it remains undetected. The local rms level is $\sim$0.2 mJy beam$^{-1}$ in the 1.2mm map of $0.959^{\prime\prime}\times 0.799^{\prime\prime}$ spatial resolution. The 3$\sigma$ upper limit at 1.2mm is 0.6 mJy, assuming the dust distribution is unresolved, indicating that Zhúlóng has low far-infrared luminosity.

We note that, with the exception of the ALMA 1.2 mm observations, the remaining long-wavelength observations are too shallow to significantly constrain the far-infrared SED shape of Zhúlóng (see Sect. [3.3](#Sec: mass)). Therefore, in this work, we only use data points from HST, JWST, and ALMA 1.2mm.

## Zhúlóng with robust photometric redshift: $z_{\rm phot} = 5.2^{+0.3}_{-0.2}$

The photometric redshift of Zhúlóng is estimated using the SED-fitting code `EAZY` (cite: Brammer2008), with the `blue_sfhz_13` template set which imposes redshift-dependent star formation histories (SFHs), excluding SFHs that start earlier than the age of the Universe at a given redshift[^4]. We apply an error floor of 5% prior to running `eazy` to account for possible remaining systematic uncertainties in the photometry and to allow for more flexibility in the SED-fitting. The redshift range for fitting is set to $z \in (0.01, 20)$. Additional details on the photometric redshift modeling are presented in (cite: Williams2024).

The `EAZY` best-fit results are shown in Fig. [1](#fig1). The redshift probability distribution $P(z)$ for Zhúlóng is strongly constrained by a prominent Balmer/4000 Å  break observed in the central region (0.16$^{\prime\prime}$ radius), resulting in narrow uncertainties with a single redshift solution $z_{\rm phot} = 5.2^{+0.3}_{-0.2}$. In addition, the neighboring south-west clump has evidence of strong emission lines, which boost the photometry in the F277W and F444W bands, leading to an even better constrained photometric redshift: $z_{\rm phot} = 5.15^{+0.04}_{-0.03}$. This consistency illustrates the $z_{\rm phot}$ reliability of Zhúlóng. Further tests and a detailed discussion of the robustness of the redshift are presented in Appendix [6](#low-z). Nevertheless, we underline that this is still a photometric redshift. It will be important to confirm the redshift through spectroscopy in the future, such as with the upcoming COSMOS-3D grism observations (GO-5893, (cite: COSMOS-3D)) or with NIRSpec spectra.

![](4_0)

![](3_v3)

| Total | $z_{\rm phot}$ | log $M_{\rm \star} [M_{\odot}$\] | SFR \[$M_{\odot}$yr$^{-1}$\] | $A_{\rm V}$ \[mag\] |  |
|:---|:--:|:--:|:--:|:--:|:--:|
|  | $5.2^{+0.3}_{-0.2}$ | 11.03$_{-0.08}^{+0.10}$ | 66$_{-46}^{+89}$ | 1.1$_{-0.2}^{+0.2}$ |  |
|  |  |  |  |  |  |
| Annulus radius | log $\Sigma M_{\rm \star} [M_{\odot}$ kpc$^{-2}$\] | log $\Sigma$SFR \[$M_{\odot}$yr$^{-1}$kpc$^{-2}$\] | log sSFR \[yr$^{-1}$\] | $A_{\rm V}$ \[mag\] | $\beta_{\rm UV}$ |
| $<0.16^{\prime\prime}$ | 9.91$_{-0.09}^{+0.11}$ | -5.85$_{-36.21}^{+5.98}$ | -15.76$_{-36.12}^{+5.86}$ | 0.8$_{-0.4}^{+0.4}$ | 0.18$\pm$0.48 |
| $0.16^{\prime\prime}-0.35^{\prime\prime}$ | 9.52$_{-0.10}^{+0.07}$ | 0.73$_{-0.15}^{+0.14}$ | -8.78$_{-0.06}^{+0.07}$ | 1.7$_{-0.2}^{+0.2}$ | -0.38$\pm$0.30 |
| $0.35^{\prime\prime}-0.5^{\prime\prime}$ | 8.94$_{-0.08}^{+0.10}$ | 0.14$_{-0.14}^{+0.15}$ | -8.80$_{-0.06}^{+0.05}$ | 1.2$_{-0.2}^{+0.2}$ | -0.97$\pm$0.20 |
| $0.5^{\prime\prime}-0.7^{\prime\prime}$ | 8.65$_{-0.09}^{+0.07}$ | -0.13$_{-0.15}^{+0.16}$ | -8.78$_{-0.06}^{+0.09}$ | 1.0$_{-0.2}^{+0.2}$ | -1.18$\pm$0.19 |

# Physical properties of Zhúlóng

## Appearance of bulge, disk, and spiral structures

We investigate the morphology of Zhúlóng with three deep JWST long-wavelength filters, F277W, F356W, and F444W, and their inverse-variance weighted stacked image. We fit our source with `PySersic` (cite: Pasha2023JOSS) using two different strategies: 1) a single Sérsic profile and 2) double Sérsic profiles. In both cases, we use PSFs for fitting which are derived from the WebbPSF software (cite: Perrin2014) and rotated to match the position angle of the observations. The single Sérsic fit returns the best-fit half-light radius ($R_{\rm e}$), which is used to quantify the galaxy size. The double Sérsic fit helps to distinguish between the contributions of the bulge and disk. In addition, comparing the best-fit results from single and double Sérsic profiles allows for an inspection of the underlying bulge in the core.

The fitting process is performed on $4^{\prime\prime}\times 4^{\prime\prime}$ background-subtracted cutouts centered on Zhúlóng. The bright neighboring foreground galaxy at $z\sim1.59$ is masked during the fitting. Additionally, we conduct tests comparing the results when masking the spiral arms, versus not masking them. We find that no matter whether masking them or not during the fitting process, for both single and double Sérsic fits, the best-fit results ($R_{\rm e}$, Sérsic index $n$, minor-to-major axis ratio $b/a$) remain consistent within the $1\sigma$ error. In this analysis, we focus on the results where the spiral arms are also masked during the fitting, as this approach enhances the visibility of the spiral arm structure in the residual plots, allowing us to more distinctly separate the disk, spiral arms, and the underlying bulge structure.

Fig. [2](#morphology_plot) shows the best-fit results of the stacked image. From the residual maps, Zhúlóng shows evidence for a grand-design spiral arm structure, with high contrast primary arms extending from the bulge pointing north and south (cite: Dobbs2014; Sellwood2022). The presence of the spiral arms is also indicated in the surface brightness profiles, which show the discrepancy between the observed points and the best-fit model. The single Sérsic fit yields $R_{\rm e}=2.9 \pm 0.1$ kpc, suggesting that Zhúlóng has a large stellar size. The large $n=4.9\pm0.1$ reveals that the stellar light is more concentrated at the galaxy center, indicating the potential existence of a bulge structure. Meanwhile, the significant inhomogeneity in the core of the residual map also suggests the need for an additional bulge component in the fitting process, which is mitigated in the residual map of the double Sérsic fit. On the other hand, the double Sérsic fit yields evidence for both bulge + disk structures, with spiral arms shown in the residual map. The bulge component has $n=3.7\pm0.2$, close to the shape of classical bulges in the local Universe ($n\sim4$), suggesting the existence of a well-evolved bulge even in the first Gyr after the Big Bang. The bulge-to-total (light) ratio is $B/T=0.44$. The disk component has $n=1.2\pm0.1$, $R_{\rm e}=3.7\pm0.1$ kpc, and $b/a=0.99 \pm 0.01$, indicating the existence of a large face-on exponential stellar disk. In addition, we note that both of the residual maps show clear evidence of stellar clumps along the spiral arms, as observed in galaxies at cosmic noon (cite: Rujopakarn2016; Claeyssens2023; Claeyssens2024) and as also found in numerical simulations (cite: Tamburello2015; Mandelker2017; FenschBournaud2021; Ceverino2023; Renaud2024). Furthermore, we also perform the morphological analysis for individual images, and the results remain the same (see Appendix [7](#fit)).

Overall, from the morphological analysis, it appears that the fit may be more in favor of the double Sérsic model. However, this alone does not constitute strong enough evidence to confirm the existence of a bulge and disk in Zhúlóng. As we will show in Sect. [3.2](#Sec: annulus), spatially resolved SED modeling reveals significant differences in the stellar populations between the inner and outer regions of the galaxy. The combination of the morphological analysis and the SED evidence suggests that the galaxy does indeed contain separate inner and outer structural components.

Given the extended nature of Zhúlóng, and the amount of flux present in spiral arms that are not well-accounted for by either Sérsic model, we also measure the size that encloses 80% of the light empirically, using the azimuthally-averaged light profile from the stacked image without any assumption on the parametric shape of the light distribution. Using this method, we find that these radii are larger than inferred assuming the parametric Sérsic (or double Sérsic) model. We measure R$_{80}$=9.5 kpc for the radii enclosing 80% of the light. R$_{80}$ is extremely large compared to its half-light radius (while better reflecting the overall extent of stellar light), reflecting the fact that the spatial extent of the stars in the galaxy reaches more than 19 kpc in diameter.

## A quiescent-like bulge and star-forming disk

We further analyze different annular regions to explore any variation in the stellar populations across Zhúlóng. Physical properties are estimated by fitting the UV-to-NIR SED from JWST and HST photometry using `Bagpipes` (cite: Carnall2018), with the $z_{\rm phot}$ fixed to that measured by `eazy`. We consider two different star formation histories (SFHs): a double-power-law and a delayed SFH, using (cite: Bruzual2003) stellar population models and the (cite: Calzetti2000) reddening law. We adopt a broad metallicity range of 0.1 to 2.5 $Z_{\odot}$, dust attenuation to the rest-frame V band ($A_{\rm V}$) values from 0 to 5 magnitudes, and ionization parameters log$U$ ranging from -4 to -2. For the double-power-law SFH, we adopt a falling slope $\alpha$ = \[0.01, 1000\], a rising slope $\beta$ = \[0.01, 1000\], and a turnover time $\tau$ = \[0.01, 5\] Gyr. For the delayed SFH, we apply broad uniform priors with age (i.e., the time since star formation began) ranging from 10 Myr to 1.2 Gyr and a logarithmic $\tau$ (timescale of decrease) ranging from 10 Myr to 10 Gyr. We obtain the main physical properties of $M_{\star}$, $A_{\rm V}$, and SFR, consistent within $1\sigma$ between the results assuming the two different SFHs. As an example, the best-fit SED results assuming a double-power-law SFH are shown in Fig. [3](#fig3) and Table [\[table1\]](#table1).

In Fig. [3](#fig3), from the central core to the outer region, the best-fit SED changes significantly from quiescent to star-forming populations. The core is dominated by old stellar populations with a red color ($F150W-F444W=3.1$ ABmag). The best-fit SED exhibits a strong Balmer/4000 Å break, very low $\log$(sSFR/yr$^{-1})=-15.76_{-36.12}^{+5.86}$, and a lack of emission lines. The observed colors are consistent with NIRCam-based photometric selections for $z>3$ quiescent galaxies (cite: Long2024). The rest-frame U-V and V-J colors as measured from `eazy` are 1.4 and 1.0 mag, respectively, consistent with a quiescent/post-starburst fading stellar population (cite: williams2009). The restframe colors are also consistent with extensions of UVJ color criteria for quiescent galaxies that have been adapted to $z>3-6$ to accommodate younger passively evolving galaxies (cite: AntwiDanso2023). In contrast, the disk measured in an annulus between 0.5$^{\prime\prime} - 0.7^{\prime\prime}$ is dominated by younger stellar populations with a relatively bluer color ($F150W-F444W=2.0$ ABmag) and, unlike the inner region, allows the presence of weak emission lines in the SED.

Furthermore, among all annular regions, the central core ($r<0.16^{\prime\prime}$) has the highest stellar mass surface density, with log($\Sigma M_{\rm \star}/M_{\odot}$ kpc$^{-2}) = 9.91_{-0.09}^{+0.11}$ (see Table [\[table1\]](#table1)), revealing the build-up of a dense stellar bulge. The absence of star formation activity in the core is consistent with the expectations of inside-out galaxy growth and quenching (cite: Tacchella2015).

Finally, we also calculate the stellar mass and stellar mass surface density of the bulge. Assuming the core is dominated by the bulge, with the mass-to-light ratio in the core and the best-fit bulge light profile (Fig. [2](#morphology_plot)), we derive $\log (M_{\star, \rm bulge}/M_{\odot})=10.71_{-0.09}^{+0.10}$ and log($\Sigma M_{\rm \star, \rm bulge}/M_{\odot}$ kpc$^{-2}) = 10.00_{-0.11}^{+0.09}$. Given the total mass of Zhúlóng (see Sect. [3.3](#Sec: mass)), its bulge-to-total mass ratio is $B/T=0.5$.

## Ultra-massive spiral galaxy with accelerated formation 

Here we focus on the integrated properties of Zhúlóng. The total $M_{\star}$, $A_{\rm V}$, and SFR are derived by fitting the UV-to-FIR SED from the JWST+HST+ALMA photometry, using `Bagpipes`. Similar to Sect. [3.2](#Sec: annulus), we use the (cite: Calzetti2000) reddening law, the (cite: Bruzual2003) stellar population models, and the (cite: Draine2007) dust emission model (with energy balance), assuming different SFH (double-power-law SFH and delayed SFH) and free metallicity. The derived main properties with delayed SFH are listed in Table [\[table1\]](#table1). To test the result, we also perform SED fitting with `CIGALE` (cite: Boquien2019), which produces very consistent values within the errors. The total stellar mass is also consistent with the sum of the individual masses obtained from the different annuli ($\log (M_{\star}/M_{\odot})=10.96_{-0.06}^{+0.05}$; see Sect. [3.2](#Sec: annulus)). In general, we find that Zhúlóng is extremely massive with $\log (M_{\star}/M_{\odot})=11.03_{-0.08}^{+0.10}$.

Such high stellar mass at $z\sim5.2$ indicates that Zhúlóng must have been forming stars very efficiently. In Fig. [4](#fig2), we compare its stellar mass to the maximum mass at which one would expect to find a galaxy within the PANORAMIC survey volume, given the prevailing halo mass function and cosmic baryon fraction (cite: Boylan-Kolchin2023; Lovell2023). Instead of taking the small coverage of PANORAMIC in the COSMOS field only, to be conservative, we consider the total PANORAMIC survey area of $\sim$ 432 arcmin$^{2}$. Under this paradigm, we derive the most massive dark matter halo mass ($M_\mathrm{halo}^\mathrm{max}$) at different redshifts within the corresponding survey volume ($\Delta z=1$; e.g., $\sim1.2\times10^{6}$ Mpc$^3$ at $z=4.7-5.7$) according to the halo mass function. The derived $M_\mathrm{halo}^\mathrm{max}$ at $z=5.2$ is log($M_{\rm halo}/M_{\odot}$) $=12.38$.

![](mass_z_model1dV_v2.pdf)

The maximum stellar mass is inferred from the maximum dark matter halo mass, based on $M_{\star}^\mathrm{max} = \epsilon f_{\rm b} M_\mathrm{halo}^\mathrm{max}$, with a cosmic baryon fraction $f_{\rm b} = \Omega_{\rm b}/\Omega_{\rm m} = 0.158$ (cite: Planck2020), and the maximum theoretical efficiency ($\epsilon$) of converting baryons into stars. Here, we consider two possible cases of $\epsilon$ in the PANORAMIC survey volume, as shown in Fig. [4](#fig2): the highest efficiency from observation-based phenomenological modeling, such as abundance matching and halo occupation distribution models (cite: Moster2013; Moster2018; Tacchella2018; Pillepich2018; Wechsler2018; Shuntov2022) and the maximum efficiency logically allowed ($\epsilon=1$; dashed line). As a reference, we also overplot the most extreme case of $\epsilon=1$ in the full sky (solid line).

By comparing the stellar mass of Zhúlóng with the predictions in Fig. [4](#fig2), it is clear that Zhúlóng requires an extremely efficient conversion of available baryons to stars of $\epsilon\sim0.3$ – about 1.5 times the highest efficiency observed at lower redshift ($\epsilon_{\rm max,obs} \simeq 0.2$). The ultra-massive properties and high efficiency make Zhúlóng another extreme source in addition to recently discovered massive galaxies (cite: Xiao2024; glazebrook2017; Glazebrook2024; Carnall2023Natur; Weibel2024b; deGraaff2024). In Fig. [4](#fig2), we show a direct comparison of Zhúlóng and three red monster galaxies at $z_{\rm spec}\sim5-6$ (cite: Xiao2024) as their efficiency is calculated within the similar survey volume. Together, these findings demonstrate the existence of ultra-massive galaxies that challenge our galaxy assembly models in the first billion years of the Universe (cite: White1978; Boylan-Kolchin2023; Labbe2023a).

In addition, in Fig. [4](#fig2), we compile all currently known examples from the literature of galaxies whose stellar structures are consistent with spiral arms at $z>3$, the highest redshift at which spiral structure has been detected in stars (rather than just gas) to date (cite: jain2024; Wangweichen2024; Umehata2024; Costantin2023; Wu2023). We note that while some other galaxies have been reported to show potential spiral-like structures in JWST images, they are not included in our figure due to the lack of comparable analyses and stellar mass estimates (cite: Ferreira2023). Thus, we caution that there may be more spiral galaxies at $z>3$ than those currently identified, and a systematic study of high-redshift spiral galaxies is necessary to confirm this. In addition, sources showing only stellar disks but without clear spiral arms are also not in our plot (cite: Yan2024). Compared with the literature-reported spiral galaxies, Zhúlóng appears to be the most distant spiral galaxy discovered so far.

## The location on the main sequence

Given the red, quiescent-like bulge, we investigate the location of our galaxy with respect to the star-formation main sequence (SFMS) at $z\sim5$. While previous ultra-massive galaxies are found to be in a rapid star-formation phase, Zhúlóng’s star-formation rate is significantly low. For example, the three sources from (cite: Xiao2024) S1, S2, and S3 are ultra-massive, dusty star-forming, sub-millimeter galaxies. They have SFRs of $\sim$1000 $M_{\odot}$yr$^{-1}$, large dust contents ($A_{\rm V}>3$ mag and detected by SCUBA2 observations), half-light radii of $R_{\rm e, F444W}\sim 1-2$ kpc. Due to heavy dust obscuration, they are barely detectable in the optical wavelength bands, and hence they are also called optically dark galaxies (cite: wangtao2019; Williams2019; Xiao2023; Williams2024_RED). By contrast, as shown in Fig. [5](#fig_ms), the SFR of Zhúlóng is 66$_{-46}^{+89}$ $M_{\odot}$yr$^{-1}$ (also in Table [\[table1\]](#table1)), more than 10 times lower than S1, S2, and S3. It is not detected in the deep ALMA observations at 1.2mm (3$\sigma$ upper limit of 0.6 mJy beam$^{-1}$) and other FIR observations, consistent with its low measured SFR (see Sect. [2.2](#alma)). With these properties, the galaxy is about 1 dex below the main sequence as characterized by (cite: Schreiber2015), and 0.5 dex below the relation of (cite: Popesso2023).

![](MS_2.pdf)

# Implications of the emergence of an ultra-massive grand-design spiral galaxy at 1 Gyr

## An outlier among massive galaxies at $z\sim5$ 

As discussed in Section [3.1](#Sec: morphology), the galaxy is large, extending over 19 kpc (based on the size enclosing 80% of the light). We also measure its half-light size based on 1- and 2-component Sérsic profiles, resulting in $\sim3$ and 3.9 kpc (for each model, respectively). By all metrics, Zhúlóng is large relative to comparable galaxies at similar redshifts. The typical average half-light size at $z\sim5$ at $\log M_*/M_\odot\sim10.7$ from recent studies range between 0.4-2 kpc (cite: Allen2024; Ito2024; Ormerod2024; Varadaraj2024; Ward2024), as estimated based on single-Sérsic models. These findings are in line with the expectation that galaxy size scales with dark matter halo size, which decreases with increasing redshift (cite: mo1998).

Unfortunately, JWST-derived mass-size relations, to date, are based almost entirely on galaxies one order of magnitude lower in mass, complicating direct comparison with this source. Compared to an extrapolation to the size-mass relation of SFGs at similar redshift, the half-light radius of Zhúlóng (Re$\sim$3 kpc; single-Sérsic) does fall within the extrapolated scatter from lower masses (cite: Allen2024; Miller2024).

However, in light of its low integrated sSFR ($\log$ sSFR$\sim-9.2$ yr$^{-1}$; $>$0.5 dex below the SFMS at these redshifts; see Fig. [5](#fig_ms)), such a large size is quite remarkable. Its red rest-frame U-V vs V-J colors in the core (see Section [3.2](#Sec: annulus)) are consistent with quiescent systems, perhaps making a comparison to that population more appropriate. Typically, UVJ-red galaxies follow a steeper mass-size relation leading to much smaller sizes at fixed stellar mass than SFGs (cite: vanderwel2014; Ito2024; Ji2024b). Quiescent galaxies with similarly high mass ($\log M_*/M_\odot>$10.3-11) at comparable redshifts (cite: Carnall2023Natur; deGraaff2024; Weibel2024b; Ji2024c; Ito2024), have Re $\sim 0.4-0.7$ kpc, a factor of $>4\times$ smaller than what we find here (using our single-Sérsic measurement for Zhúlóng, for consistency with other studies). Unfortunately, sample sizes of comparable galaxies at $\log M_*/M_\odot\sim11$ at $z\sim5$ remain small, regardless of sSFR, and preclude a robust conclusion in comparison to the population scatter.

Thus, we also compare to the R$_{80}$ sizes of very massive $\log M_*/M_\odot\sim11$ galaxies (across all sSFR) from larger-area HST surveys at $z\lesssim3$ (cite: Mowla2019). We find that R$_{80}$ for this galaxy is still 50$\%$ larger than the average R$_{80}$ among comparable mass galaxies that appear more than 1 Gyr later (cite: Mowla2019b). While a definitive comparison to typical co-eval massive galaxies is not possible without a more detailed analysis and data on larger JWST-based samples, collectively these first comparisons imply that Zhúlóng could be a notable outlier among massive galaxies, regardless of its location relative to the MS at $z>4$.

While it is a likely outlier due it its large size, its properties as a massive spiral galaxy at $z\sim 5.2$ are also unexpected. The fraction of visibly spiral galaxies is already known to drop down to 4% at $z\lesssim 3$, in part due to surface brightness dimming that impacts visibility as $(1+z)^4$ (cite: Kuhn2024), but remain rare even at cosmic noon (cite: Law2012; Yuan2017). The entire spiral disk is also quite red; even at $z\lesssim2$, where spirals are more prevalent (cite: Conselice2014), those with similarly red color (cite: Fudamoto2022) are rare, only making up 2$\%$ of the galaxy population (cite: Shimakawa2022). The rarity of similar sources later in cosmic time makes the existence of Zhúlóng at $z\sim5.2$ remarkable.

## A Milky Way analog with 1 Gyr formation time

While a potential outlier at $z\sim5$, this galaxy is instead remarkably comparable to massive evolved spirals like the MW at $z\sim0$. MW-like spirals are characterized by old bulges (thought to form early in the universe) but whose extended disks are thought to have built up slowly over the course of 10 Gyr (cite: vanDokkum2013; RixBovy2013). For context, current estimates indicate that the MW has a comparably massive core (bulge + bar) to Zhúlóng with $\log M_*/M_\odot \sim10$, total stellar mass of $\log M_*/M_\odot\sim10.8$ (even slightly lower than Zhúlóng), with comparable sSFR, consistent with our upper limit (cite: Licquia2015). Various estimates for the half-light radius of the MW suggest a scale length for the thin disk of $R_{e}=2.6\pm0.5$ kpc (cite: BlandHawthorn2016). The full extent of its stellar disk (diameter $\sim19$ kpc) is already of comparable size to mature MW-like spirals seen at $z\sim0$ (cite: BlandHawthorn2016; Lian2024).

Unlike typical co-eval galaxies, Zhúlóng has instead developed comparable structures (bulge mass and density, disk and spiral size, spatially segregated stellar populations) and comparable stellar mass, 10$\times$ faster than MW-like galaxies at $z\sim0$, demonstrating that such an advanced evolutionary stage in galaxy evolution can be reached in only 1 Gyr time. Moreover, in $\Lambda$CDM, the Universe is expected to be 6$^3$ denser at z$\sim$5 compared to today’s Universe, this makes it astonishing that Zhúlóng appears with a well-organized morphology with a similar z$\sim0$ MW’s size, despite this high merger rate in the early Universe (cite: Duan2024). How a morphologically mature galaxy that resembles nearby massive spirals can form in this environment remains an open question, but the discovery of this source is a first step and provides an important constraint on galaxy formation models.

## Implications for efficient growth of massive galaxies

The ultra-massive nature of Zhúlóng indicates an efficient mass build-up and a high star formation efficiency (see Fig. [4](#fig2)) in the past. Multiple minor mergers and/or major mergers may have driven this rapid growth. In addition, the presence of clumps also supports efficient growth; fragmentation of gas-rich disks into star-forming clumps may increase the star formation efficiency, helping galaxies grow more quickly to reach such masses (cite: Dessauges-Zavadsky2019; Dessauges-Zavadsky2023; Faisst2024; Fujimoto2024).

Although the galaxies described below have all been reported with high star formation efficiencies, the structure in the stellar populations of Zhúlóng clearly distinguishes it from other ultra-massive dusty star-forming galaxies (cite: Xiao2024) and early-forming massive quiescent galaxies (cite: glazebrook2017; Glazebrook2024; Carnall2023Natur; Weibel2024b; deGraaff2024). It is clear that Zhúlóng formed through an inside-out pathway (see Section [3.2](#Sec: annulus)), and only a handful of other galaxies at $z>4$ have been identified to have this stellar structure (cite: Baker2024; Ji2024c; Nelson2024).

Zhúlóng has now demonstrated that there must be broad diversity in morphology among ultra-massive galaxies. While an answer about the origin of the spiral structure awaits further spectroscopic information, it now seems clear that at least some ultra-massive galaxies exhibit large disks (in contrast to the other known examples, which are nearly all compact). This may reflect a diversity of formation pathways that must be factored into any theories about the physical processes that drive their early formation at high redshift. Larger sample sizes will be required to better understand the morphological diversity of ultra-massive galaxies, which will be enabled in the future by the continued accumulation of wide-area JWST imaging.

# Conclusions

In this paper, we present the serendipitous discovery of the most distant ultra-massive spiral galaxy candidate identified in the pure parallel imaging survey PANORAMIC (in the COSMOS field). It has $z_{\rm phot} = 5.2^{+0.3}_{-0.2}$ well-constrained by a strong Balmer/4000 Å break and consistent with the neighboring star-forming clump (Fig. [1](#fig1)). After combining the JWST/NIRCam, HST, and ALMA data, we find the following extremely intriguing properties:

**1. Quiescent bulge + large star-forming disk + spiral arms:** From the morphological analysis, Zhúlóng perfectly exhibits a classical bulge ($n=3.7\pm0.2$ and $R_{\rm e}=0.9\pm0.1$ kpc), a large face-on stellar disk ($n=1.2\pm0.1$, $R_{\rm e}=3.7\pm0.1$ kpc, and $b/a=0.99 \pm 0.01$) extending over 19 kpc, with spiral arms embedded in (Fig. [2](#morphology_plot)). The SED analysis on different annular regions shows Zhúlóng has a quiescent-like core and a star-forming stellar disk (Fig. [3](#fig3)). Compared to the stellar disk, the center core is $i$) red ($F150W-F444W=3.1$ mag); $ii$) has among the highest stellar mass surface densities measured among quiescent galaxies (log($\Sigma M_{\rm \star}/M_{\odot}$ kpc$^{-2}) = 9.91_{-0.09}^{+0.11}$; see Table [\[table1\]](#table1)) – revealing the build-up of the stellar bulge; and $iii$) and is quiescent – indicating an inside-out galaxy growth (or quenching). For the bulge, we derive $\log (M_{\star, \rm bulge}/M_{\odot})=10.71_{-0.09}^{+0.10}$, log($\Sigma M_{\rm \star, \rm bulge}/M_{\odot}$ kpc$^{-2}) = 10.00_{-0.11}^{+0.09}$, and $B/T=0.5$.

**2. Extremely massive:** Zhúlóng is extremely massive ($\log (M_{\star}/M_{\odot})=11.03_{-0.08}^{+0.10}$; Fig.[4](#fig2)), adding to a growing population of ultra-massive galaxies discovered in the first billion years. Assuming it is located in the most massive dark matter halo expected in the whole PANORAMIC survey volume, we infer that Zhúlóng must have been forming stars very efficiently, with the baryons-to-stars conversion efficiency of $\epsilon\sim0.3$ – about 1.5 times higher than even the most efficient galaxies at later epochs.

**3. Low star formation activity:** Although the disk is still forming stars, in total, Zhúlóng has SFR $=66_{-46}^{+89}$ $M_{\odot}$yr$^{-1}$ (Table [\[table1\]](#table1) and Fig.[5](#fig_ms)), $\gtrsim$0.5 dex below the SFMS at $z\sim5.2$ (cite: Schreiber2015; Popesso2023). The relatively modest SFR of Zhúlóng indicates that it is in the transformation phase from star-forming to quiescence.

**4. Most distant spiral galaxy discovered so far:** Compared to other recently reported stellar spiral galaxies at $z\sim3$, Zhúlóng appears to be the most distant spiral galaxy discovered so far. While the origin of the spiral structure is unknown, it represents an important example that demonstrates that a MW-like galaxy can evolve earlier in the universe than previously thought ($10\times$ faster than locally, $<1$Gyr after the Big Bang), while efficiently building enormous stellar mass.

Altogether, Zhúlóng at $z_{\rm phot}\sim5.2$ is potentially the highest-redshift, red, ultra-massive, grand-design spiral galaxy with a large stellar size. Overall, the galaxy sits below the main sequence, suggesting the star formation activity is ramping down. It contains a quiescent bulge + large star-forming disk + spiral arms. For a galaxy at $z>5$, having any of these relevant properties would be enough to make the galaxy special. The presence of all of these properties makes Zhúlóng very exceptional, indicating the rapid formation and morphological evolution of massive galaxies in the early universe. With future JWST IFU observations, combined with higher-resolution and deeper ALMA data, this galaxy will provide a unique window to unveil what triggers the rapid mass assembly together with the early disk formation.

# Acknowledgements

We are very grateful to the anonymous referee for instructive comments, which helped to improve the overall quality and strengthened the analyses of this work. We thank Boris Sindhu Kalita, Francoise Combes, and Maximilien Franco for valuable discussions and suggestions that improved this paper.

This work is based in part on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program 2514. Support for program JWST-GO-2514 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2023.1.00180.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This work has received funding from the Swiss State Secretariat for Education, Research and Innovation (SERI) under contract number MB22.00072, as well as from the Swiss National Science Foundation (SNSF) through project grant 200020_207349. The work of CCW is supported by NOIRLab, which is managed by the Association of Universities for Research in Astronomy (AURA) under a cooperative agreement with the National Science Foundation. The Cosmic Dawn Center (DAWN) is funded by the Danish National Research Foundation under grant DNRF140. PD acknowledges support from the NWO grant 016.VIDI.189.162 (“ODIN") and warmly thanks the European Commission’s and University of Groningen’s CO-FUND Rosalind Franklin program. AH acknowledges support by the VILLUM FONDEN under grant 37459. MVM acknowledges support from the National Science Foundation via AAG grant 2205519 and the Wisconsin Alumni Research Foundation via grant MSN251397. CCW, AC, ZJ and KEW acknowledge funding from program JWST-GO-2514 that was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127. ZJ also acknowledges funding from JWST/NIRCam contract to the University of Arizona NAS5-02015. I.L. acknowledges support from Australian Research Council Future Fellowship FT220100798. SL acknowledges support by the Science and Technology Facilities Council (STFC) and by the UKRI Frontier Research grant RISEandFALL. LB acknowledges funding from STFC through ST/T000473/1 and ST/X001040/1. K.G. and T.N. acknowledge support from Australian Research Council Laureate Fellowship FL180100060.

128 natexlab

(ref: Adamo2024) Adamo, A., Atek, H., Bagley, M. B., et al. 2024, arXiv e-prints, arXiv:2405.21054

(ref: Allen2024) Allen, N., Oesch, P. A., Toft, S., et al. 2024, arXiv e-prints, arXiv:2410.16354

(ref: AntwiDanso2023) Antwi-Danso, J., Papovich, C., Leja, J., et al. 2023, ApJ, 943, 166

(ref: Baker2024) Baker, W. M., Tacchella, S., Johnson, B. D., et al. 2024, Nature Astronomy \[\]

(ref: Belokurov2022) Belokurov, V. & Kravtsov, A. 2022, MNRAS, 514, 689

(ref: Bertin1996) Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393

(ref: Bing2023) Bing, L., Béthermin, M., Lagache, G., et al. 2023, A&A, 677, A66

(ref: Binney2008) Binney, J. & Tremaine, S. 2008, Galactic Dynamics: Second Edition

(ref: BlandHawthorn2016) Bland-Hawthorn, J. & Gerhard, O. 2016, ARA&A, 54, 529

(ref: Boquien2019) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: RixBovy2013) Bovy, J. & Rix, H.-W. 2013, ApJ, 779, 115

(ref: Boylan-Kolchin2023) Boylan-Kolchin, M. 2023, Nature Astronomy, 7, 731

(ref: Brammer2008) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503

(ref: Bruzual2003) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Calzetti2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Carnall2018) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379

(ref: Carnall2023Natur) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2023, Nature, 619, 716

(ref: Casey2024) Casey, C. M., Akins, H. B., Shuntov, M., et al. 2024, ApJ, 965, 98

(ref: Casey2023) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31

(ref: Ceverino2023) Ceverino, D., Mandelker, N., Snyder, G. F., et al. 2023, MNRAS, 522, 3912

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Claeyssens2024) Claeyssens, A., Adamo, A., Messa, M., et al. 2024, arXiv e-prints, arXiv:2410.10974

(ref: Claeyssens2023) Claeyssens, A., Adamo, A., Richard, J., et al. 2023, MNRAS, 520, 2180

(ref: Conselice2014) Conselice, C. J. 2014, ARA&A, 52, 291

(ref: Costantin2023) Costantin, L., Pérez-González, P. G., Guo, Y., et al. 2023, Nature, 623, 499

(ref: Cutler2022) Cutler, S. E., Whitaker, K. E., Mowla, L. A., et al. 2022, ApJ, 925, 34

(ref: deGraaff2024) de Graaff, A., Setton, D. J., Brammer, G., et al. 2024, arXiv e-prints, arXiv:2404.05683

(ref: Dekel2020) Dekel, A., Ginzburg, O., Jiang, F., et al. 2020, MNRAS, 493, 4126

(ref: Desprez2024) Desprez, G., Martis, N. S., Asada, Y., et al. 2024, MNRAS, 530, 2935

(ref: Dessauges-Zavadsky2023) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2023, MNRAS, 519, 6222

(ref: Dessauges-Zavadsky2019) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2019, Nature Astronomy, 3, 1115

(ref: Dobbs2014) Dobbs, C. & Baba, J. 2014, PASA, 31, e035

(ref: Donnan2023) Donnan, C. T., McLeod, D. J., Dunlop, J. S., et al. 2023, MNRAS, 518, 6011

(ref: Draine2007) Draine, B. T. & Li, A. 2007, ApJ, 657, 810

(ref: Duan2024) Duan, Q., Conselice, C. J., Li, Q., et al. 2024, arXiv e-prints, arXiv:2407.09472

(ref: PRIMER) Dunlop, J. S., Abraham, R. G., Ashby, M. L. N., et al. 2021, PRIMER: Public Release IMaging for Extragalactic Research, JWST Proposal. Cycle 1, ID. #1837

(ref: Faisst2024) Faisst, A. L., Brinch, M., Casey, C. M., et al. 2024, arXiv e-prints, arXiv:2405.09619

(ref: faisst2017) Faisst, A. L., Capak, P. L., Yan, L., et al. 2017, ApJ, 847, 21

(ref: FenschBournaud2021) Fensch, J. & Bournaud, F. 2021, MNRAS, 505, 3579

(ref: Ferreira2022) Ferreira, L., Adams, N., Conselice, C. J., et al. 2022, ApJL, 938, L2

(ref: Ferreira2023) Ferreira, L., Conselice, C. J., Sazonova, E., et al. 2023, ApJ, 955, 94

(ref: Finkelstein2024) Finkelstein, S. L., Leung, G. C. K., Bagley, M. B., et al. 2024, ApJL, 969, L2

(ref: Fudamoto2022) Fudamoto, Y., Inoue, A. K., & Sugahara, Y. 2022, ApJL, 938, L24

(ref: Fujimoto2024) Fujimoto, S., Ouchi, M., Kohno, K., et al. 2024, arXiv e-prints, arXiv:2402.18543

(ref: Gardner2023) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001

(ref: Glazebrook2024) Glazebrook, K., Nanayakkara, T., Schreiber, C., et al. 2024, Nature, 628, 277

(ref: glazebrook2017) Glazebrook, K., Schreiber, C., Labbé, I., et al. 2017, Nature, 544, 71

(ref: grogin2011) Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, ApJS, 197, 35

(ref: Gurvich2023) Gurvich, A. B., Stern, J., Faucher-Giguère, C.-A., et al. 2023, MNRAS, 519, 2598

(ref: HuertasCompany2024) Huertas-Company, M., Iyer, K. G., Angeloudi, E., et al. 2024, A&A, 685, A48

(ref: Ito2024) Ito, K., Valentino, F., Brammer, G., et al. 2024, ApJ, 964, 192

(ref: Jacobs2023) Jacobs, C., Glazebrook, K., Calabrò, A., et al. 2023, ApJL, 948, L13

(ref: jain2024) Jain, R. & Wadadekar, Y. 2024, A grand-design spiral galaxy 1.5 billion years after the Big Bang with JWST

(ref: Ji2024c) Ji, Z., Williams, C. C., Rieke, G. H., et al. 2024a, arXiv e-prints, arXiv:2409.17233

(ref: Ji2024b) Ji, Z., Williams, C. C., Suess, K. A., et al. 2024b, arXiv e-prints, arXiv:2401.00934

(ref: COSMOS-3D) Kakiichi, K., Egami, E., Fan, X., et al. 2024, COSMOS-3D: A Legacy Spectroscopic/Imaging Survey of the Early Universe, JWST Proposal. Cycle 3, ID. #5893

(ref: Kartaltepe2023) Kartaltepe, J. S., Rose, C., Vanderhoof, B. N., et al. 2023, ApJL, 946, L15

(ref: Kawinwanichakij2021) Kawinwanichakij, L., Silverman, J. D., Ding, X., et al. 2021, ApJ, 921, 38

(ref: koekemoer2007) Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172, 196

(ref: koekemoer2011) Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS, 197, 36

(ref: Kuhn2024) Kuhn, V., Guo, Y., Martin, A., et al. 2024, ApJL, 968, L15

(ref: Labbe2023a) Labbé, I., van Dokkum, P., Nelson, E., et al. 2023, Nature, 616, 266

(ref: Law2012) Law, D. R., Shapley, A. E., Steidel, C. C., et al. 2012, Nature, 487, 338

(ref: LeFloch2009) Le Floc’h, E., Aussel, H., Ilbert, O., et al. 2009, ApJ, 703, 222

(ref: BLee2013) Lee, B., Giavalisco, M., Williams, C. C., et al. 2013, ApJ, 774, 47

(ref: Lian2024) Lian, J., Zasowski, G., Chen, B., et al. 2024, Nature Astronomy, 8, 1302

(ref: Licquia2015) Licquia, T. C. & Newman, J. A. 2015, ApJ, 806, 96

(ref: Long2024) Long, A. S., Antwi-Danso, J., Lambrides, E. L., et al. 2024, ApJ, 970, 68

(ref: Lovell2023) Lovell, C. C., Harrison, I., Harikane, Y., Tacchella, S., & Wilkins, S. M. 2023, MNRAS, 518, 2511

(ref: Lutz2011) Lutz, D., Poglitsch, A., Altieri, B., et al. 2011, A&A, 532, A90

(ref: Mandelker2017) Mandelker, N., Dekel, A., Ceverino, D., et al. 2017, MNRAS, 464, 635

(ref: McCluskey2024) McCluskey, F., Wetzel, A., Loebman, S. R., et al. 2024, MNRAS, 527, 6926

(ref: Miller2024) Miller, T. B., Suess, K. A., Setton, D. J., et al. 2024, arXiv e-prints, arXiv:2412.06957

(ref: mo1998) Mo, H. J., Mao, S., & White, S. D. M. 1998, MNRAS, 295, 319

(ref: Momcheva2017) Momcheva, I. G., van Dokkum, P. G., van der Wel, A., et al. 2017, PASP, 129, 015004

(ref: Mortlock2013) Mortlock, A., Conselice, C. J., Hartley, W. G., et al. 2013, MNRAS, 433, 1185

(ref: Moster2013) Moster, B. P., Naab, T., & White, S. D. M. 2013, MNRAS, 428, 3121

(ref: Moster2018) Moster, B. P., Naab, T., & White, S. D. M. 2018, MNRAS, 477, 1822

(ref: Mowla2019b) Mowla, L., van der Wel, A., van Dokkum, P., & Miller, T. B. 2019a, ApJL, 872, L13

(ref: Mowla2019) Mowla, L. A., van Dokkum, P., Brammer, G. B., et al. 2019b, ApJ, 880, 57

(ref: Naidu2022) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJL, 940, L14

(ref: Nelson2024) Nelson, E., Brammer, G., Giménez-Arteaga, C., et al. 2024, ApJL, 976, L27

(ref: Oke1983) Oke, J. B. & Gunn, J. E. 1983, ApJ, 266, 713

(ref: oliver2012) Oliver, S. J., Bock, J., Altieri, B., et al. 2012, MNRAS, 424, 1614

(ref: Ormerod2024) Ormerod, K., Conselice, C. J., Adams, N. J., et al. 2024, MNRAS, 527, 6110

(ref: Pasha2023JOSS) Pasha, I. & Miller, T. B. 2023, The Journal of Open Source Software, 8, 5703

(ref: Perrin2014) Perrin, M. D., Sivaramakrishnan, A., Lajoie, C.-P., et al. 2014, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9143, Space Telescopes and Instrumentation 2014: Optical, Infrared, and Millimeter Wave, ed. J. Oschmann, Jacobus M., M. Clampin, G. G. Fazio, & H. A. MacEwen, 91433X

(ref: Pillepich2018) Pillepich, A., Springel, V., Nelson, D., et al. 2018, MNRAS, 473, 4077

(ref: Planck2020) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: Popesso2023) Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526

(ref: Renaud2024) Renaud, F., Agertz, O., & Romeo, A. B. 2024, A&A, 687, A91

(ref: Rieke2023) Rieke, M. J., Kelly, D. M., Misselt, K., et al. 2023, PASP, 135, 028001

(ref: Robertson2023) Robertson, B. E., Tacchella, S., Johnson, B. D., et al. 2023, ApJL, 942, L42

(ref: Rujopakarn2016) Rujopakarn, W., Dunlop, J. S., Rieke, G. H., et al. 2016, ApJ, 833, 12

(ref: Salpeter1955) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: Schinnerer2010) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, ApJS, 188, 384

(ref: Schreiber2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74

(ref: Sellwood2022) Sellwood, J. A. & Masters, K. L. 2022, ARA&A, 60 \[\]

(ref: Shapley2024) Shapley, A. E., Sanders, R. L., Topping, M. W., et al. 2024, arXiv e-prints, arXiv:2410.00110

(ref: Shimakawa2022) Shimakawa, R., Tanaka, M., Bottrell, C., et al. 2022, PASJ, 74, 612

(ref: Shuntov2022) Shuntov, M., McCracken, H. J., Gavazzi, R., et al. 2022, A&A, 664, A61

(ref: Smolcic2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1

(ref: Tacchella2018) Tacchella, S., Bose, S., Conroy, C., Eisenstein, D. J., & Johnson, B. D. 2018, ApJ, 868, 92

(ref: Tacchella2015) Tacchella, S., Carollo, C. M., Renzini, A., et al. 2015, Science, 348, 314

(ref: Tamburello2015) Tamburello, V., Mayer, L., Shen, S., & Wadsley, J. 2015, MNRAS, 453, 2490

(ref: Umehata2024) Umehata, H., Steidel, C. C., Smail, I., et al. 2024, arXiv e-prints, arXiv:2410.22155

(ref: vanderwel2014) van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28

(ref: vandokkum2008) van Dokkum, P. G., Franx, M., Kriek, M., et al. 2008, ApJL, 677, L5

(ref: vanDokkum2013) van Dokkum, P. G., Leja, J., Nelson, E. J., et al. 2013, ApJL, 771, L35

(ref: Varadaraj2024) Varadaraj, R. G., Bowler, R. A. A., Jarvis, M. J., et al. 2024, MNRAS, 533, 3724

(ref: VegaFerrero2024) Vega-Ferrero, J., Huertas-Company, M., Costantin, L., et al. 2024, ApJ, 961, 51

(ref: Wangbingjie2024) Wang, B., Leja, J., de Graaff, A., et al. 2024a, ApJL, 969, L13

(ref: wangtao2019) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211

(ref: Wangweichen2024) Wang, W., Cantalupo, S., Pensabene, A., et al. 2024b, arXiv e-prints, arXiv:2409.17956

(ref: Ward2024) Ward, E., de la Vega, A., Mobasher, B., et al. 2024, ApJ, 962, 176

(ref: Wechsler2018) Wechsler, R. H. & Tinker, J. L. 2018, ARA&A, 56, 435

(ref: Weibel2024b) Weibel, A., de Graaff, A., Setton, D. J., et al. 2024a, arXiv e-prints, arXiv:2409.03829

(ref: Weibel2024) Weibel, A., Oesch, P. A., Barrufet, L., et al. 2024b, MNRAS, 533, 1808

(ref: White1978) White, S. D. M. & Rees, M. J. 1978, MNRAS, 183, 341

(ref: Williams2024_RED) Williams, C. C., Alberts, S., Ji, Z., et al. 2024, ApJ, 968, 34

(ref: Williams2019) Williams, C. C., Labbe, I., Spilker, J., et al. 2019, ApJ, 884, 154

(ref: Williams2024) Williams, C. C., Oesch, P. A., Weibel, A., et al. 2025, ApJ, 979, 140

(ref: williams2009) Williams, R. J., Quadri, R. F., Franx, M., van Dokkum, P., & Labbé, I. 2009, ApJ, 691, 1879

(ref: Wu2023) Wu, Y., Cai, Z., Sun, F., et al. 2023, ApJL, 942, L1

(ref: Xiao2024) Xiao, M., Oesch, P. A., Elbaz, D., et al. 2024, Nature, 635, 311

(ref: Xiao2023) Xiao, M. Y., Elbaz, D., Gómez-Guijarro, C., et al. 2023, A&A, 672, A18

(ref: Yan2024) Yan, H., Sun, B., & Ling, C. 2024, ApJ, 975, 44

(ref: Yuan2017) Yuan, T., Richard, J., Gupta, A., et al. 2017, ApJ, 850, 61

# Robustness of the redshift solution for Zhúlóng.

In Fig. [1](#fig1), we show the narrow photometric redshift distribution $P(z)$ of Zhúlóng, derived using `EAZY` for the galaxy core (0.16$^{\prime\prime}$ radius aperture). To ensure the robustness of our results, we also perform SED fitting with `Bagpipes`, allowing the redshift to vary from 1 to 10. We assume different SFHs, including delayed SFH and double-power-law SFH, and the same settings as described in Sect. [3.2](#Sec: annulus). The resulting $P(z)$ shows a single strong peak, consistent with the `EAZY` results. Specifically, the photometric redshift is $z_{\rm phot} = 5.42^{+0.31}_{-0.45}$ for delayed SFH (Fig. [6](#lowz)-$a$) and $z_{\rm phot} = 5.59^{+0.29}_{-0.38}$ for the double-power-law SFH.

However, when a larger aperture (e.g., 0.7$^{\prime\prime}$ radius) is used, a second redshift solution at $z \sim 1.6$ emerges (Fig. [6](#lowz)-$b$). To further investigate this, we rerun the SED fitting for the galaxy core using `EAZY` with the redshift fixed to $z = 1.6$. The resulting fit, shown in Fig. [6](#lowz)-$c$, has a large chi-square value ($\chi^2 = 46$), indicating a very poor fit.

To explore the cause of this low-redshift solution with a large aperture, we further inspect the images and find a bright clump (clump 2, thereafter; Fig. [6](#lowz)-$d$) at F606W and F814W from HST/ACS. Clump 2 is located south-east of the $z_{\rm phot} = 5.15^{+0.04}_{-0.03}$ clump reported in Fig. [1](#fig1). The `EAZY` fitting results for clump 2 show a broad $P(z)$ distribution with $z_{\rm phot} = 1.65^{+2.11}_{-0.02}$, suggesting it may be a foreground clump. Thus, the second redshift peak in Fig. [6](#lowz)-$b$ is likely due to contamination from clump 2.

Overall, we perform SED fitting on the galaxy core using both `EAZY` and `Bagpipes`, and both methods consistently indicate that Zhúlóng is a strong spiral galaxy candidate at $z>5$. However, we identify the potential presence of foreground structure(s) that could contaminate the redshift measurements of Zhúlóng when larger apertures are used. We note here that clump 2 does not affect our main results, as the global properties of Zhúlóng are derived using the total flux measured within a 0.5$^{\prime\prime}$ radius aperture (with aperture corrections applied), with clump 2 not included. While clump 2 is included in the SED fitting for the annular radius of 0.5$^{\prime\prime}-0.7^{\prime\prime}$ and may influence the fitting results (see Fig. [3](#fig3)), we cannot confirm whether it is a low-$z$ clump without spectroscopic observations and thus did not remove it from the analysis. In any case, the key findings of inside-out galaxy growth and a quiescent-like galaxy core embedded in a star-forming stellar disk remain consistent even when considering only the remaining annuli. In addition, it does not affect our identification of spiral features. To confirm whether Zhúlóng is indeed a distant spiral galaxy at $z > 5$, follow-up JWST NIRSpec/IFU observations are necessary.

![](lowz)

# Morphological modeling of Zhúlóng.

![](4_1)

![](4_2)

[^1]: E-mail: mengyuan.xiao@unige.ch

[^2]: Parallel wide-Area Nircam Observations to Reveal And Measure the Invisible Cosmos (PANORAMIC)

[^3]: Zhúlóng (

    UTF8gkai烛龙

    , or Torch Dragon), which is a giant red solar dragon and god in Chinese mythology. It supposedly had a human’s face and snake’s body, created day and night by opening and closing its eyes, and created seasonal winds by breathing.

[^4]: <https://github.com/gbrammer/eazy-photoz/tree/master/templates/sfhz>

</paper>

Write the methods card for this paper.