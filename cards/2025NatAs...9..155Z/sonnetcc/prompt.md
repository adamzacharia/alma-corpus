# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9..155Z\sonnetcc\reply.txt

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
 "bibcode": "2025NatAs...9..155Z",
 "title": "A luminous and young galaxy at z = 12.33 revealed by a JWST/MIRI detection of Hα and [O III]",
 "year": 2025,
 "journal": "Nature Astronomy",
 "first_author": "Zavala, Jorge A.",
 "n_authors": 40,
 "arxiv_id": "2403.10491",
 "doi": "10.1038/s41550-024-02397-3",
 "alma_projects_linked_by_archive": [
  "2021.A.00020.S"
 ]
}
```

Paper text:
<paper>
# A luminous and young galaxy at $z=12.33$ revealed by a JWST/MIRI detection of H$\alpha$ and \[OIII\]

## Abstract

The James Webb Space Telescope (JWST) has discovered a surprising population of bright galaxies in the very early universe ($\lesssim$ 500 Myrs after the Big Bang) that is hard to explain with conventional galaxy formation models and whose physical properties remain to be fully understood. Insight into their internal physics is best captured through nebular lines but, at these early epochs, the brightest of these spectral features are redshifted into the mid-infrared and remain elusive. Using the JWST Mid-Infrared Instrument, MIRI, here we present the first detection of H$\mathbf{\alpha}$ and doubly-ionized oxygen (\[OIII\]4959,5007 Å) at $\mathbf{z>10}$. These detections place the bright galaxy GHZ2/GLASS-z12 at $\mathbf{z=12.33\pm0.04}$, making it the most distant astronomical object with direct spectroscopic detection of these lines. These observations provide key insights into the conditions of this primeval, luminous galaxy, which shows hard ionizing conditions rarely seen in the local Universe likely driven by compact and young ($\mathbf{\lesssim30\,}$Myr) burst of star formation. Its oxygen-to-hydrogen abundance is close to a tenth of the solar value, indicating a rapid metal enrichment. This study confirms the unique conditions of this remarkably bright and distant galaxy and the huge potential of mid-IR observations to characterize these objects.

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

,

, and

\

\

Following the confirmation of the first surprisingly bright galaxies at high-redshifts ($z\gtrsim10$)(cite: ArrabalHaro2023; Bunker2023; Harikane2024), research efforts must now shift towards gaining a deeper understanding of their physical properties. The detection and interpretation of emission-line spectra are pivotal in this topic, with well-studied calibrations and diagnostic diagrams based on rest-frame optical transitions and line ratios such as \[NII\]/H$\alpha$ vs \[OIII\]/H$\beta$. The advent of the JWST and, particularly, the sensitive Near Infrared Spectrograph (NIRSpec), has now unlocked access to some of these lines in very high-redshift galaxies, enabling detailed studies that were previously unreachable beyond $z\sim3$ (e.g.(cite: Trump2023; Sanders2023)). At redshifts above $z\sim7$, however, the H$\alpha$ transition, known as the gold standard to measure young star formation activity, is redshifted beyond the NIRSpec coverage. Similarly, the \[OIII\] and H$\beta$ lines, sensitive to metallicity and ionizing conditions, can only be observed up to $z\sim9.5$ with this instrument.

The MIRI instrument on board JWST is thus the only astronomical instrument with the required wavelength coverage to detect these spectral lines at higher redshifts, critical for characterizing the physical properties of the first galaxies in the universe. While early predictions suggested that their successful detection may require long observing times of several tens of hours(cite: Rieke2015), the combination of both the better-than-expected performance of JWST(cite: Rigby2023) and the remarkably high brightness of some od the JWST-discovered distant galaxies, might have improved the prospects for such studies, making the detection of $z>10$ rest-frame optical emission lines more feasible than previously anticipated.

Here, we report the results of the first MIRI spectroscopic observations on a $z>10$ galaxy candidate and test its efficiency for redshift confirmation and characterization of early galaxies via the detection of rest-frame optical nebular lines.

![](GHZ2_LRS_spectrum_new.pdf)

We target the galaxy GHZ2/GLASS-z12(cite: Castellano2022; Naidu2022) ($\rm RA=00^h13^m59.76^s$, $\rm DEC=-30^o19'29.11\ensuremath{''}$) with MIRI to search for the brightest rest-frame optical nebular emission lines redshifted into the mid-IR regime: \[OIII\]4959,5007Å, $H\alpha$, $H\beta$ (with the doublets \[NII\]6548,6583Å and \[SII\]6716,6731Å also covered but expected to be too faint to be detected). The target stands out as one of the brightest and most robust among the extremely distant galaxy candidates found in deep JWST NIRCam images, with a photometric redshift of $z\approx12.0-12.4$. It was found in the outskirts of the galaxy cluster Abell 2744, as part of the GLASS-JWST Early Release Science Program(cite: Treu2022a), with an absolute rest-frame UV magnitude of $M_{\rm UV} = -20.5$ mag(cite: Castellano2024) and a inferred stellar mass(cite: Naidu2022) close to $10^9\,M_\odot$, despite its compact morphology(cite: Ono2023) ($R_e\lesssim50\,$pc) and moderate gravitational amplification of(cite: Bergamini2023) $\mu\approx1.3$ (see Methods for a deeper discussion on the gravitational amplification).

The MIRI observations were conducted on October 25-29, 2023, using the low resolution spectrometer (LRS) slit mode (resolving power $R\approx50-200$), with a total integration on-source exposure time of 9 h (see details in the Methods). The main advantage of this mode relies on its large spectral coverage, which provides sensitive observations across $\approx5–12\,\mu$m, covering at least one of the aforementioned lines across $z\approx7-20$. Data reduction was performed using the standard JWST pipeline with some additional steps as described in the Methods.

Fig. [1](#fig:MIRI_spectrum) shows the MIRI one-dimensional (1D) and two-dimensional (2D) spectra of the source. Two spectroscopic features are clearly detected above the noise level ($>5\sigma$) in the 1D and 2D spectra. These spectral features are associated with the \[OIII\] doublet (4959Å and 5007Å) and with the H$\alpha$ recombination line, which constrain the redshift of this source to be $z_{\rm spec}=12.33\pm0.04$ (see also ref.(cite: Castellano2024)), making this object the most distant galaxy with detections of these nebular lines and one of the brightest early galaxies discovered to date. The JWST/NIRSpec spectra of the other five galaxies with similar spectroscopic redshifts(cite: Curtis-Lake2023; DEugenio2023; Wang2023; Carniani2024) ($z\approx12-14$) are distinguished by the lack of strong emission lines. In these cases, the spectroscopic redshifts are measured via the spectral break in continuum emission produced by absorption of neutral hydrogen, but extensive tests are needed to rule out lower-redshift solutions that can produce similar breaks. This demonstrates the unique use of MIRI to spectroscopically confirm the highest redshift galaxies via direct detection of rest-frame optical lines that can additionally provide direct information on the galaxy’s star formation rate and ionized gas properties, although these studies might be limited to the brightest systems.

The emission line around $6.6\,\ensuremath{\mu}m$, associated with the \[OIII\] doublet, was fitted with a double Gaussian function to infer the line flux densities (reported in Table 1). During this procedure we assume the same line-width for the two lines and fix the relative intensity ratio to the theoretical 1:3 value(cite: Storey2000). In the case of H$\alpha$, the line was fitted with a single Gaussian function. Although the \[NII\] doublet lines are blended with H$\alpha$, at the redshift of GHZ2, it is reasonable to assume that the flux contribution of \[NII\] is negligible due to the likely sub-solar metallicity(cite: Groves2006; Nakajima2022b). Negligible \[NII\] emission is seen even at lower redshifts ($z\approx4-7$) for galaxies(cite: Cameron2023; Sanders2023; Calabro2024; Topping2024) and AGN alike(cite: Kocevski2023; Harikane2023), an even for for nitrogen-enriched systems(cite: Topping2024). Hence, we can safely assume that this line is dominated by the H$\alpha$ emission. For the undetected emission lines, including H$\beta$ and the \[SII\] doublet, $2.5\sigma$ upper limits were derived by adopting the local noise r.m.s and a given line-width as described in the Methods. Note that the non-detection of H$\beta$ is still consistent with theoretical predictions and with zero dust attenuation. A more stringent upper limit on the H$\beta$ flux density can be inferred from the measured H$\alpha$ flux density, adopting a flux ratio of $\rm H\alpha/H\beta=2.85$ (based on the so-called case-B recombination scenario and under the typical physical conditions of galaxies’ ionized gas(cite: Osterbrock2006)). This ratio is valid in the case of negligible dust attenuation, but it increases in the presence of dust since the H$\beta$ line is more affected by dust extinction. Nevertheless, the dust attenuation is not expected to be significant in this galaxy (with inferred $\rm A_V$ values around or below 0.1-0.3 mag, as described in the Methods).

![](MZR_and_BPT_v2.png)

This record-breaking detection of H$\alpha$ provides a direct probe of the young star formation activity, tracing massive stars with ages around or below $10\,$Myr. This, combined with the detection of oxygen (revealing the presence of metals and thus of more evolved stars), provides a unique opportunity to study the stellar population of this distant galaxy and its ionizing photon production efficiency. We infer the average stellar age, and other properties like stellar mass and star formation rate, by conducting spectral energy distribution (SED) fitting to the NIRCam photometry jointly with the constraints from the H$\alpha$ and \[OIII\] emission lines (see details in the Methods and Supplementary materials). The photometry and the spectroscopic data are well reproduced with a model with a composite star formation history extending for $\sim$50 Myr, with a mass-weighted age of $28^{+10}_{-14}\,$Myr, and more than 60% of the total stellar mass formed during the past $30\,$Myr. The presence of young and massive stars implies a higher rate of ionizing photon production compared to typical values in galaxies at lower redshifts (see Figure [4](#fig:ion_efficiency)). The evidence that most of the stellar mass of GHZ2 formed recently is consistent with other results implying that early galaxies have more “bursty" star-formation histories(cite: endsley23; ciesla23; tacchella22; cole2023)). If the majority of early galaxies do indeed form the bulk of their visible mass in their recent past, it could explain not only the remarkable luminosity of this distant galaxy, but the overall surprising number of observed bright galaxies in this epoch(cite: finkelstein23; adams23).

The SED-based SFR (averaged on the last 10 Myr and taking into account the gravitational lensing amplification of(cite: Bergamini2023) $\mu=1.3$) of $5\pm2\rm\,M_\odot\,yr^{-1}$ is in good agreement with the SFR of $9\pm3\rm\,M_\odot\,yr^{-1}$ estimated directly from the H$\alpha$ luminosity assuming the calibration from ref.(cite: Reddy2022). This calibration is based on low-metallicity stellar population synthesis models that include the effects of massive stars in binary systems characterized by a high ionizing photon production efficiency. On the other hand, the widely-adopted calibration used for local and low-redshift galaxies(cite: Kennicutt2012) predicts a higher SFR of $\sim22\pm5\,\rm M\odot\,yr^{-1}$, mainly due to the absence of these low-metallicity and binary stars.

The JWST/MIRI data also constrain the R3 $\equiv \log(\rm[OIII]/H\beta)$ ratio, which is known to correlate with the gas-phase metallicity(cite: Nagao2006). The estimated line ratio and its associated uncertainty of $\rm [OIII]/H\beta=5.2\pm 1.5$ (when assuming directly the inferred H$\beta$ in the case of zero dust attenuation) implies a metallicity of $12+\log\rm(O/H)=7.40^{+0.52}_{-0.37}$ according to the relation presented by ref.(cite: Sanders2024), corresponding to $Z=0.05^{+0.12}_{-0.03}\,Z_\odot$ (where $Z_\odot$ is solar metallicity). A similar range of metallicities are obtained when using the theoretical calibrations(cite: Hirschmann2023) specifically designed for galaxies at $z>4$ (see details in the Methods). These values are in good agreement with the independent metallicity estimation of $12+\log\rm(O/H)=7.26^{+0.27}_{-0.24}$ based on the \[NeIII\]3868Å/\[OII\]3727Å index (with additional constraints from other lines), as reported in our parallel analysis of the NIRSpec data of this source(cite: Castellano2024).

Despite the young age derived for GHZ2, it is notable that its metallicity is already enriched to a few percent (or even up to $\sim10-15\%$) of the solar value, significantly above expectations for the primordial objects dominated by the first-generation stars (typically known as population-III stars). This implies a very rapid metal enrichment during the earliest phases of galaxy formation. The metallicity inferred for GHZ2 is higher than the metallicities of the four spectroscopically-confirmed galaxies at $z=10-13$ discovered in the JADES survey(cite: Curtis-Lake2023). This is not totally surprising since a correlation between stellar mass and metallicity is known to exist even up to $z\sim9$(cite: Nakajima2023), and the stellar mass of GHZ2 of $\log(M_\star/M_\odot)\approx8.6-9.0$ is around an order of magnitude larger than what was inferred for JADES galaxies. This might suggest that a similar relation exists even at these early redshifts, although shifted to lower metallicites. Actually, when compared with the so-called fundamental metallicity relation(cite: Curti2020), which involves the SFR as a third parameter, all these $z>10$ galaxies deviate significantly towards lower metallicity values. Confirming the existence of such scaling relations would require, however, larger samples of galaxies with similar spectroscopy data.

![](pyneb_revised.png)

To gain further insights into the physical conditions of the ionized gas in this galaxy, we show in Fig. [2](#fig:MZR) the well-studied $\rm [NII]/H\alpha$ vs $\rm [OIII]/H\beta$ BPT-diagram along with the predictions from a photoionization model powered by star formation(cite: Nakajima2022a). The R3 value of $5.2\pm 1.5$ derived above implies a high ionization parameter of $\log(U)\gtrsim-2.0$, as shown in Fig. [2](#fig:MZR). Note that this measurement is not affected by our assumption of a dust-free environment when calculating the H$\beta$ line since any dust attenuation will only increase the inferred \[OIII\]/H$\beta$ ratio. The high ionization conditions in this galaxy are also confirmed by the detection of NIV\]1488Å and HeII 1640Åin the NIRSpec spectrum(cite: Castellano2024), requiring ionizing photons with energy above $\sim54\,$eV. This might point towards the presence of X-ray binaries or very massive stars(cite: Schaerer2019; Lecroq2024; Upadhyaya2024) contributing to the hard ionizing radiation.

Alternatively, the high ionization conditions might be produced by AGN activity, although the higher ionization AGN tracers NeIV\]2424Å and \[NeV\]3426Å remain undetected(cite: Castellano2024). On the other hand, a morphological analysis of this object constrains its size to be very compact ($r_e\lesssim50\,$pc) but marginally resolved(cite: Ono2023), which favors the star-formation scenario as the source of the ionizing radiation or a composite AGN/star-forming galaxy system (rather than pure AGN).

It is now useful to put into context the upper limit on the \[OIII\]88$\mu$m line luminosity derived from previous ALMA observations(cite: Bakx2023). The line ratio between this and the \[OIII\]5007Å transition is sensitive to the electron density of the ionized gas with an extra milder dependency on temperature. Fig. [3](#fig:ALMA_constraints) shows the expected \[OIII\]5007Å-to-\[OIII\]88$\mu$m line ratio as a function of electron temperature and density (see Methods section for further details). As can be seen, at the typical \[OIII\] electron temperatures (e.g. 6,000-15,000 K), the constraints imposed by the ALMA and JWST observations imply a high electron density above $10^3\,\rm cm^{-3}$. This, again, contrasts with the typical conditions seen in the local Universe and lower redshift galaxies with average densities on the order of(cite: Kaasinen2017) $n_e\approx10^1-10^2\,\rm cm^{-3}$, but is in agreement with the recent results proving a redshift evolution towards higher electron densities at high redshifts(cite: Isobe2023) (see also Figure [5](#fig:ne_redshift)). This evolution might be driven by the higher star formation rate surface density ($\Sigma_{\rm SFR}$) measured in high-redshift galaxies(cite: Reddy2023; Calabro2024; Topping2024), which reaches an extreme value of $320\pm130\rm\,M_\odot\,yr^{-1}\,kpc^{-2}$ in GHZ2 (adopting the measured(cite: Ono2023) effective radius of 50 pc). The combination of these unique conditions, including high ionization parameters, high electron densities, and high star formation rate surface density might explain the brightness of the unique population of $z>10$ galaxies recently discovered by JWST, along with the young stellar ages and relatively low metallicities.

This study demonstrates the enormous potential of the Mid-Infrared Instrument, MIRI, on board JWST for the confirmation and characterization of the most distant galaxies in the Universe. Our observations make our target, GHZ2, the most distant galaxy with direct detection of several transitions from the ionized gas (see also ref.(cite: Castellano2024)) and one of the brightest spectroscopically-confirmed galaxy at this early epoch, with a robust spectroscopic redshift of $z=12.33\pm0.04$. The physical conditions of GHZ2, revealed directly by nebular emission lines, are extreme and rarely seen in the local Universe, with a low (but not pristine) metallicity, high ionization conditions, and high electron density. This emerging picture of compact galaxies with extreme conditions seems to be fairly common at high redshifts, particularly among the brightest systems, and might be associated with short bursts of young star formation with ages of a few tens of Myr and with the presence of massive, low-metallicity stars. Some of the properties of this early galaxy might also resemble the observed features of AGN, particularly the hard ionizing spectra inferred from the observations presented here and from the JWST/NIRSPec data(cite: Castellano2024). It is thus possible that this source might be, at least partially, powered by an active black hole. Further observations on this and other similar sources will significantly contribute to our understanding of early galaxy formation and black-hole growth, pushing the current frontiers into the formation epoch of the first massive objects in the Universe.\
**Data availability.** The JWST/MIRI data used in this paper will be publicly available through the Mikulski Archive for Space Telescopes server, under JWST program GO-3703. All other data generated throughout the analysis are available from the corresponding author, JAZ, on request.

**Acknowledgements.** This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program JWST-ERS-3703. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.A.00020.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST, ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. JAZ acknowledge funding from JSPS KAKENHI grant number KG23K13150. The GLASS-JWST team and other co-authors acknowledges support by NASA via grants JWST-ERS-1342 and JWST-GO-3703. C.G. acknowledges financial support through grant PRIN-MUR 2020SKSTHZ. Finally, we would like to thank Sarah Kendrew, Greg Sloan, and Milo Docher for their support during the preparation of the observations and their suggestions for data reduction.

**Author Contributions.** J.A.Z. led the JWST MIRI observing proposal, data analysis, and manuscript writing. M.C., A.C., A.F., P.S. and T.T. led the original JWST GLASS observations and the discovery study of GHz2, and contributed to the MIRI follow-up proposal. H.B.A and J.M. significantly contributed to the MIRI data reduction. T.J.L.C.B. and I.M. re-analyzed the ALMA data and the \[OIII\]88$\mu$m constraints. D.B., O.A.C.O., S.L.F., P.P.G., V.B. and P.S. modelled and interpreted the spectral energy distributions of our target. P.B., C.G., and P.R. performed the lensing analysis presented in the Methods. M.D., C.M.C., P.A.H., M.F., M.G., N.A.G., N.H., R.I., I.J., J.S.K, A.M.K., R.L.L. and C.P., contributed to the original JWST MIRI proposal, observing design, and to the scientific discussion in the proposal and manuscript. M.C., K.N., A.C., B.B., N.J.C., D.F.A., C.P., R.T., E.T. and T.S. focused on the interpretation of the observed lines and line ratios (and associated derived physical properties). K.N., M.H. and L.Y.A.Y. provided the theoretical grounds to infer some of the physical parameters and other predictions from simulations. All co-authors contributed to the editing and formatting of the manuscript.

**Competing interests.** The authors declare no competing interests.

------------------------------------------------------------------------

National Astronomical Observatory of Japan, 2-21-1, Osawa, Mitaka, Tokyo, Japan

INAF - Osservatorio Astronomico di Roma, Via Frascati 33, 00078, Monte Porzio Catone, Italy

Department of Astronomy, The University of Texas at Austin, 2515 Speedway Boulevard Stop C1400, Austin, TX 78712, USA

Department of Space, Earth, & Environment, Chalmers University of Technology, Chalmersplatsen 4, SE-412 96 Gothenburg, Sweden

Aix Marseille Univ, CNRS, CNES, LAM, Marseille, France

NSF’s National Optical-Infrared Astronomy Research Laboratory, 950 N. Cherry Avenue, Tucson, AZ 85719, USA

Department of Astronomy, The University of Tokyo, 7-3-1 Hongo, Bunkyo, Tokyo 113-0033, Japan

Centro de Astrobiología (CAB), CSIC-INTA, Ctra. de Ajalvir km 4, Torrejón de Ardoz, E-28850, Madrid, Spain

Dipartimento di Fisica, Università degli Studi di Milano, Via Celoria 16, I-20133 Milano, Italy

INAF – OAS, Osservatorio di Astrofisica e Scienza dello Spazio di Bologna, via Gobetti 93/3, I-40129 Bologna, Italy

Department of Physics, 196A Auditorium Road, Unit 3046, University of Connecticut, Storrs, CT 06269, USA

Department of Physics and Astronomy, Texas A&M University, College Station, TX 77843-4242 USA

George P. and Cynthia Woods Mitchell Institute for Fundamental Physics and Astronomy, Texas A&M University, College Station, TX 77843-4242 USA

Canada-France-Hawaii Telescope, Kamuela, HI 96743, USA

Instituto de Radioastronomía y Astrofísica, UNAM Campus Morelia, Apartado postal 3-72, 58090 Morelia, Michoacán, Mexico

INAF – IASF Milano, via A. Corti 12, I-20133 Milano, Italy

University of Massachusetts Amherst, 710 North Pleasant Street, Amherst, MA, 01003-9305, USA

Space Telescope Science Institute, 3700 San Martin Dr, Baltimore, MD 21218, USA

Institute for Physics, Laboratory for Galaxy Evolution and Spectral Modelling, Ecole Polytechnique Federale de Lausanne, Observatoire de Sauverny, Chemin Pegasi 51, 1290 Versoix, Switzerland

INAF, Osservatorio Astronomico di Trieste, Via Tiepolo 11, I-34131 Trieste, Italy

Department of Astronomy, School of Science, SOKENDAI (The Graduate University for Advanced Studies), 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan

Laboratory for Multiwavelength Astrophysics, School of Physics and Astronomy, Rochester Institute of Technology, 84 Lomb Memorial Drive, Rochester, NY 14623, USA

Dipartimento di Fisica e Scienze della Terra, Universit‘a degli Studi di Ferrara, via Saragat 1, I-44122 Ferrara, Italy

Instituto Nacional de Astrofísica, Óptica y Electrónica, Tonantzintla, 72840 Puebla, Mexico

Institute of Astronomy, University of Cambrige, Cambridge CB3 0HA, UK

Facultad de Astronomía y Geofísica, Universidad de La Plata, Paseo del Bosque s/n, B1900FWA La Plata, Argentina

Department of Physics and Astronomy, University of California, Los Angeles, 430 Portola Plaza, Los Angeles, CA 90095, USA

**Methods**

# Cosmology and other definitions

Throughout this paper, we assume a flat $\Lambda$CDM cosmology with $\Omega_\mathrm{m} = 0.29$, $\Omega_\mathrm{\Lambda} = 0.71$ and $\rm H_0=69.6\,\rm km\,s^{-1}\,Mpc^{-1}$; and a Solar abundance of $12+\log\rm(O/H)=8.69$(cite: Asplund2009).

# JWST/MIRI observations and data reduction

Observations were conducted as part of project GO-3703 (PI: J. Zavala) using the MIRI low resolution spectrometer (with the P750L filter) in slit mode. The target was observed in three different visits using the FASTR1 readout pattern and 121 groups per integration, 16 integration per exposure, and 1 exposure per specification with 2 dither positions ”along slit nod”. Each visit has an on-source time of 10828.26 s (summing 9 h in total). Target acquisition (TA) observations on a bright star (RA=00h13m58.3s; Dec=-30$^\circ$20$'$14.10$''$) were conducted before every visit to ensure the target is placed with subpixel accuracy ($<10\,$mas) at the nominal slit center location.

We reduce the MIRI data using the official *JWST* pipeline (Version 1.13.4), Calibration Reference Data System (CRDS) version 11.16.16 and CRDS context `jwst_1174.pmap` to assign the reference files. We adopt the stage 1 pipeline procedures unchanged, resulting in six count-rate images (2 dithers, 3 exposures each). Then, we run the `spec2pipeline` stage, which performs flux calibration and various instrument corrections, separately on the individual count-rate exposures, yielding six individual `s2d` images. Due to the presence of a bright nearby galaxy within the slit in one of the dither positions (see the top-left panel in Fig. 1), some residual emission is seen in half of the data. Therefore, we continue to treat each dither position separately, averaging the three exposures for each first and yielding one `s2d` file for each dither. Next, we perform a background subtraction on each dither, separately, rather than simply subtracting the two. This was done using the `Background2D` task in `photutils`, masking a $r=3.5$ pixel circular region around the detected emission lines. We estimate the median background using a box size of $2\times 2$ pixels. We then input these background-subtracted `s2d` files into the `spec3pipeline` stage, which performs outlier rejection via sigma clipping and combines the two dither positions into a single 2D spectrum. Finally, we perform 1D extraction manually using a boxcar filter with a width that scales with the MIRI PSF FWHM, as shown in the top panel of Fig. 1. Above $9\,$$\mu$m, where the noise r.m.s. per channel notably increases (due to the sensitivity of the detector and the higher spectral resolution), we re-bin the data with a 2-channel bin.

An alternative reduction following the standard steps in the pipeline, results in a similar spectrum but with a continuum baseline slightly offset towards negative values. After correcting this systematic offset, the \[OIII\] line luminosity is around 20% brighter than in our manual reduction, but with lower signal-to-noise ratio. Given that our modified reduction provides better r.m.s. noise across the whole spectrum, we adopt it for our analysis, but note that our results would not significantly change otherwise.

# Spectroscopic redshift and line measurements

A single Gaussian function was used to fit the H$\alpha$ line assuming negligible contribution from the \[NII\] doublet. In the case of the \[OIII\] doublet, we perform a simultaneous two-Gaussian fitting. During this procedure we assume the same line-width for the two lines (leaving it as a free parameter) and fix the 5007/4959 peak line ratio to 3. We use a Levenberg-Marquardt algorithm to perform non-linear least-square minimization (using the lmfit function). The measured line-widths are consistent with the instrumental resolution(cite: Kendrew2015) of $R\equiv\Delta\lambda/\lambda\approx81$ around the position of the \[OIII\] doublet (vs $R\approx83$ from the measured line-width) and 132 around H$\alpha$ (with a slightly wider measured line-width corresponding to $R\approx103$).

To infer an upper limit on the H$\beta$ line flux density, we assume the 2.5$\sigma$ r.m.s value as the upper limit for the line peak and the same line-width as the \[OIII\]5007Å line, which is determined by the line spread function of the instrument. This is a reasonable assumption since the lines are very close in wavelength space and thus the spectral resolution is expected to be very similar. This results in a H$\beta$ line flux upper limit of $\rm 2.0\times10^{-18}\,\rm\,erg\,s^{-1}\,cm^{-2}$. Alternatively, the H$\beta$ line flux density was inferred from the detected H$\alpha$ line. In the case of a dust-free environment and Case B recombination-line radiation (see details in ref.(cite: Osterbrock2006)), the expected H$\alpha$-to-H$\beta$ line ratio is 2.85 for $n_e=10^4\,\rm cm^{-3}$ and $T_e=10,000\,$K (note that this ratio does not change significantly for other values of density and temperature). Under these assumptions, we estimate an integrated line flux density of $\rm 0.9\times10^{-18}\,\rm\,erg\,s^{-1}\,cm^{-2}$. We adopt this value along the paper since we do not expect a significant dust attenuation for this galaxy (based on the SED fitting results, the dust continuum ALMA constraints(cite: Bakx2023), and the blue UV slope(cite: Castellano2024)). Actually, adopting the Calzetti attenuation law(cite: 2000ApJ...533..682C) and dust extinction values of $\rm A_V\approx0.1-0.3$ – similar to the SED fitting results described below – would decrease the estimated H$\beta$ line flux only by $\lesssim10\%$.

Finally, a $2.5\sigma$ upper limit for the \[SII\] doublet was derived using the local r.m.s value around $8.97\,\ensuremath{\mu}m$ and adopting a line-width 5% narrower than the H$\alpha$ line (following the expected spectral response of the instrument(cite: Kendrew2015)). All these measurements are reported in Table [\[tab:simple-table\]](#tab:simple-table).

The dominant uncertainty on the spectroscopic redshift comes from the current MIRI/LRS wavelength calibration. While the current calibration accuracy is estimated to be around $\pm20\,$nm[^1], this still can introduce a redshift offset of $\Delta z\sim0.04$. A recent calibration update (referenced as `jwst_1174.pmap` in the JWST pipeline), introduced a shift of about 50 nm at 6 microns and decreasing to nearly zero at the red end of the spectral range. A similar correction but a bit less extreme in the blue part was independently found by ref.(cite: Beiler2023) using observations of a Y Dwarf. Fitting the line with a single Gaussian component, we obtain $z_{\rm H\alpha}=12.36\pm0.02$ (random)$\pm0.04$ (systematic) with the updated 2024 JWST calibration. For comparison, adopting the calibration from ref.(cite: Beiler2023), we obtain $z_{\rm H\alpha}=12.37\pm0.02$ (random)$\pm0.04$ (systematic). In the case of the \[OIII\] doublet, and using a two-Gaussian simultaneous fitting as described above, we obtain $z_{\rm [OIII]}=12.29\pm0.01$ (random)$\pm0.04$ (systematic) using the most recent pipeline calibration, or $z_{\rm [OIII]}=12.33\pm0.01$ (random)$\pm0.04$ (systematic) using an alternative wavelength calibration(cite: Beiler2023). The differences between the inferred redshifts are mainly attributed to the current wavelength calibration uncertainty of $\sim20\,$nm. Across this paper we adopted the average of the redshifts obtained with the official pipeline calibration, resulting in $z=12.33\pm0.02$ (random)$\pm0.04$ (systematic) (or simply $z=12.33\pm0.04$, after taking the square root of the sum of the square of the two errors). Similar redshift constraints were derived from the NIRSpec observations(cite: Castellano2024) with a weighted redshift average between four different emission lines of $z=12.342\pm0.009$. A more precise MIRI/LRS wavelength calibration in the future will allow to derive spectroscopic redshifts with better than 1 % precision even with the low resolution spectrometer.

# Inferred parameters from the emission lines.

|  | H$\beta^\dag$ | \[OIII\]4959Å | \[OIII\]5007Å | H$\alpha$ | \[SII\]6717Å,6731Å | \[OIII\]88$\mu$m$^\ddag$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line flux \[erg/s/cm$^2$\]$\times10^{-18}$ | $<2.0$ OR $0.9\pm0.2$ | $1.6\pm0.2$ | $4.7\pm0.5$ | $2.5\pm0.7$ | $<2.6$ | $<0.25$ |

We adopted the recent calibration from ref.(cite: Sanders2024) based on a sample of 46 galaxies at $z\approx2-9$ observed with JWST/NIRspec and with multiple line detections (including temperature-sensitive lines), from which we derive $12+\log\rm(O/H)=7.40^{+0.52}_{-0.37}$ taking into account the uncertainty on the $\rm [OIII]$-to-$H\beta$ line ratio and the observed scatter in the calibration sample. This corresponds to $Z=0.05^{+0.12}_{-0.03}\,Z_\odot$. Using instead the calibration from ref.(cite: Nakajima2022a), calibrated using local analogs, results in a consistent metallicity of $\sim0.1\,Z_\odot$. We finally use the theoretical predictions for metallicity calibrations of ref.(cite: Hirschmann2023), based on the IllustrisTNG(cite: Pillepich2018) simulations connected to photo-ionisation models and focused only on galaxies at $z>4$. This theoretical calibration implies a metallicity of $Z=0.04\pm0.02\,Z_\odot$).

Note that our assumption of a negligible dust attenuation when estimating the H$\beta$ line luminosity does not bias the inferred metallicity. This is due to the turnover of the relation at higher metallicities where lower values of $\rm [OIII]$-to-$H\beta$ are expected (while dust attenuation would imply higher line ratios). This turnover implies, however, a second solution for GHZ2 of $Z\approx0.55\,Z_\odot$. This value is inconsistent with the independent constrains obtained from the NIRSpec data(cite: Castellano2024), with several diagnostic suggesting values around or below $0.1\,Z_\odot$. We can thus conclude that the gas-phase metallicity in GHZ2 is close to the aforementioned value of $Z=0.05^{+0.12}_{-0.03}\,Z_\odot$; relatively low compared to lower redshift galaxies, but not pristine despite its young age.

In the presence of dust, the $H\alpha$-to-H$\beta$ line ratio is expected to deviate from the theoretical value since the short-wavelength H$\beta$ transition is more susceptible to dust attenuation. However, while the upper limit on the H$\beta$ line luminosity is consistent with a dust-free scenario it does not rule out the possibility of dust attenuation. Deeper observations will be necessary to put any constraints on the presence (or absence) of dust in this galaxy via the Balmer decrement.

As mentioned in the main text, we estimate a SFR of $12\pm4$ M$_\odot$ yr$^{-1}$ (or $9\pm3$ M$_\odot$ yr$^{-1}$ after taking into account the gravitational magnification of $\mu=1.3$ estimated by ref.(cite: Bergamini2023)) using the calibration(cite: Reddy2022) $\rm SFR/L(H\alpha) = 10^{-41.67} (M_\odot\,yr^{-1})/(erg\,s^{-1})$. This calibration was derived from $Z=0.001$ BPASS population synthesis models with an upper-mass IMF cut of $100\,M_\odot$ and including the effects of stellar binaries. Using instead the relation of ref.(cite: Kennicutt2012), calibrated for lower redshift systems with close-to-solar metallicity, results in a higher SFR by a factor of $\sim2.5$. This difference is mainly attributed to the absence of low-metallicity stars and binary star interactions that produce higher ionization photons. In addition, we infer the SFR from the SED modelling as described below.

The H$\alpha$ line luminosity was also used to estimate the ionizing photon production efficiency, $\xi_{\rm ion}$, following ref.(cite: Matthee2017), which is related to the number of produced ionizing photons per UV luminosity (or SFR). To be conservative, during this calculation we assume an escape fraction of $f_{\rm esc}=0$ (any other value above zero will result in a higher $\xi_{\rm ion}$) and a dust attenuation of $\rm A(V)=0.3\,$mag (note that the attenuation of the young stellar population inferred from our fiducial SED modelling is $\rm A(V)=0.1\,$mag, with other models suggesting even lower values). Under these assumptions, we estimate an ionizing photon production efficiency of GHZ2 to be $\xi_{\rm ion}\gtrsim2\times10^{25}\rm\,Hz\,erg^{-1}$, as shown in Extended Data Fig. [4](#fig:ion_efficiency).

# Gravitational lensing modelling

A detailed strong-lensing model of the galaxy cluster Abell 2744 predicted(cite: Bergamini2023) a gravitational amplification of $\mu=1.3$ for GHZ2/GLASS-z12. Nevertheless, the presence of other bright galaxies along the line-of-sight (between the cluster and the target) might produce second-order effects. To test this, we modeled the total mass distribution of the closest galaxies as foreground lenses with one-component models, namely Singular Isothermal Sphere (SIS) profiles. Their redshifts and stellar masses were extracted from the GLASS catalog(cite: Paris2023), spanning $z\sim1.5-3.5$ and $M_\star= 8\times10^7 - 2\times10^9\,M_\odot$. The closest source is the most massive galaxy, with a spectroscopic redshift of $z=1.682$. We assume a conservative effective velocity dispersion value of $100\,\rm km/s$ for all the galaxies, corresponding to the highest expected value given their stellar masses(cite: Grillo2014). This was then used to estimate the associated Einstein angle for a source at the redshift of GHZ2 ($z=12.33$). Finally, to asses the potential effect of this secondary gravitational lensing amplification, this angle was compared with the angular separation between the corresponding perturber mass center (after correcting its position for the deflection of the lens cluster) and the position of GHZ2/GLASS-z12 on the perturber’s plane.

Based on the this analysis, we found that the angular separation between GHZ2 and the closest galaxy on its plane exceeds by more than five times ($\theta/\theta_{\rm E}\approx5.4$) the estimated Einstein angle (being 8-20x larger for the other foreground galaxies). While a simple SIS gravitational lens model would imply a magnification of $(1-1/5.4)^{-1}\approx 1.23$ from this close galaxy, the total magnification experienced by GHZ2 cannot simply be obtained by multiplying the magnification factor of the cluster by that of the galaxy (which would results in $\mu\approx1.6$). This can only be accurately quantified using a multiplane lensing approach which is beyond the scope of this paper. Therefore, to avoid introducing biases relative to this modelling, we decided to adopt the value of(cite: Bergamini2023) $\mu=1.3$, but notice that the uncertainties on this value allows for slightly larger magnification values with increments in the order of $\sim20-30\%$.

# SED fitting

The broad-band spectral energy distribution, jointly with the spectroscopic measurements of the H$\alpha$ and \[OIII\] emission lines, were fitted to stellar population and nebular gas emission models to estimate the stellar mass, SFR, and mass-weighted age of GHZ2. The NIRCam photometry is slightly different from previous estimations(cite: Castellano2022) since we include new observations obtained in July 2023 (see ref.(cite: Castellano2024) and Merlin et al. in prep. for further details). We used the synthesizer-AGN code (cite: 2003MNRAS.338..508P; 2008ApJ...675..234P; 2024arXiv240108782P), with the stellar populations models from ref.(cite: 2003MNRAS.344.1000B) and with a Chabrier(cite: 2003PASP..115..763C) initial mass function with stellar mass limits between 0.1 and 100 $\mathrm{M}_\odot$. We probed all sub-solar metallicity models. The star formation history was set to a double burst, each stellar population described by a delayed-exponential law with possible timescales ranging from 1 to 100 Myr, ages from 0.1 Myr to the age of the Universe at $z=12.36$. Each stellar population is allowed to be affected by independent dust attenuations described by Calzetti law(cite: 2000ApJ...533..682C), with A$_{\rm V}$ values ranging from 0 to 1 mag. Nebular continuum and line emission was modeled with Cloudy version c23.0.1 (cite: 1998PASP..110..761F; 2023RMxAA..59..327C), assuming 10,000 K gas with $10^4$ cm$^{-3}$ density and abundances linked to the stellar metallicity and ionizing photon flux provided by the stellar models. The main derived properties (without correcting for the gravitational amplification) are: stellar mass $\log\mathrm{M_\star/M}_\odot=9.03^{+0.13}_{-0.28}$, SFR$_\mathrm{10Myr}=7\pm2$ M$_\odot$ yr$^{-1}$, mass-weighted age $28^{+10}_{-14}~$Myr. The models also support the high ionization parameter inferred from the BPT diagram, with a best-fit value of $\log \mathrm{U}=-1.1\pm0.4$, and a consistent stellar metallicity of $\mathrm{Z/Z_\odot}=0.020^{+0.030}_{-0.015}$. The attenuation for older and younger star populations is constrained to be $\mathrm{A(V)}= 0.3^{+0.1}_{-0.2}~$mag and $0.1^{+0.2}_{-0.1}~$mag, respectively. The best-fit SED obtained from this analysis is presented in the Supplementary information.

Additionally, we use the bagpipes(cite: Carnall2018) and cigale(cite: Boquien2019) SED-fitting codes with the same stellar population models, IMF, and dust attenuation law. In the case of bagpipes we adopt a "bursty continuity" model for the star formation history and found a general good agreement in the age of the stellar population ($30^{+40}_{-20}~$Myr) with a very similar fraction of mass formed during the last 30$\,$Myr. Other parameters are also consistent within the error bars ($\log \mathrm{U}=-1.4^{+0.2}_{-0.3}$; SFR=$2^{+3}_{-1}$ M$_\odot$ yr$^{-1}$; $\log\mathrm{M_\star/M}_\odot=8.38^{+0.23}_{-0.18}$), with the major difference being the close-to-zero attenuation ($\mathrm{A(V)}= 0.01^{+0.02}_{-0.01}~$mag) and a slightly higher metallicity ($Z=0.22^{+0.06}_{-0.05}\,Z_\odot$). Similarly, the results with cigale implies a mass-weighted stellar age of $26\pm55\,$Myr, $\log\mathrm{M_\star/M}_\odot=8.3\pm0.3$, $\log \mathrm{U}=-2.1\pm0.5$, $\mathrm{A(V)}= 0.11^{+0.13}_{-0.11}~$mag, and SFR$_\mathrm{10Myr}=15\pm9$ M$_\odot$ yr$^{-1}$, with an even higher (but largely uncertain) metallicity of $Z=0.56\pm0.20\,Z_\odot$. Note that all these values are not corrected for gravitational amplification.

# Photoionization and line emissivity models

The photoionization models presented in Fig. [2](#fig:MZR), showing the ratio between \[OIII\]5007Å and H$\beta$ and between \[NII\]6583Å and H$\alpha$, are taken from ref.(cite: Nakajima2022b). They were calculated using the spectral synthesis code, cloudy(cite: Ferland2017), and assuming the stellar population models from BPASS, including binaries systems, with a Kroupa IMF with an upper mass cut of $300\,\rm M_\odot$ (although similar results are obtained for $M_{\rm up}=100\,\rm M_\odot$). In these models, the ionization parameter, defined as the ratio between the hydrogen-ionizing photons and the number density of hydrogen atoms, was varied from -3.5 to -1.0, while the gas electron density was fixed to $10^3\rm\,cm^{-3}$. As seen in Fig. [2](#fig:MZR), the \[OIII\]5007Å-to-H$\beta$ line ratio of GHZ2 is reproduced only by models with high ionization parameter above -2.0 (in the case of $Z\approx0.1-0.2\,Z_\odot)$. At lower metallicities ($Z\lesssim0.05\,Z_\odot$), the models predictions lie below the inferred value and would require harder ionizing radiation to explain the observational constraints. For instance, AGN-driven models show higher \[OIII\]5007Å-to-H$\beta$ ratios (by $\sim0.3\,$dex), when compared with the stellar-driven models at fixed metallicity(cite: Nakajima2022b).

On the other hand, the predicted line ratios between the two transitions of the double-ionized oxygen (\[OIII\]5007Å and \[OIII\]$88\ensuremath{\mu}m$) shown in Fig. [3](#fig:ALMA_constraints) were generated using the PyNeb getEmissivity package(cite: Luridiana2015), with the default atomic data. The ratio was calculated for different values of electron density and temperature ranging from $\log(n_e\rm[cm^{-3}])=0-10$ and $\log(T_e\rm[K])=3.7-4.5$. As can be seen in the figure, the ratio is highly sensitive to electron density with a milder dependency on electron temperature (given the significant different energy levels of the two transitions), but independent of metallicity since both transitions arise from the same ion.

# Revisiting the ALMA data and constraining the electron density

The initial investigation of GHZ2/GLASS-z12 at sub-mm wavelengths with ALMA only revealed a tentative line(cite: Bakx2023) at $258.7\,\rm GHz$, claimed to be \[OIII\]88$\mu$m at $z=12.117$. This is inconsistent with the MIRI and NIRSpec spectroscopic redshift, implying that the line was not real or, at least, not associated with GHZ2. With the updated redshift information, we visually inspect the 254.35 GHz region and fit the extracted spectrum using a single Gaussian function, centered at the peak channel. The best-fit implies a line flux of $\sim2.5\times10^{-19}\rm\,erg/s/cm^{-2}$ with $\rm FWHM\approx200\,\rm km\,s^{-1}$, which is consistent with the previously reported(cite: Bakx2023; Popping2023) upper limit, after taking into account the different line-widths (originally adopted to be $\approx100\,\rm km\,s^{-1}$ in the previous ALMA analysis(cite: Bakx2023)). Given the low statistical significance ($\sim3\sigma$) of this measurement, to be conservative, we treat it here only as an upper limit.

This implies a \[OIII\]5007Å-to-\[OIII\]88$\mu$m line ratio above $19$ (or $\log(\rm[OIII]_{5007A}/[OIII]_{88\mu m})\gtrsim1.3$) and is used in Fig. [3](#fig:ALMA_constraints) to obtain a conservative lower limit on the electron density of $n_e>100\,\rm cm^{-3}$, which varies as a function of electron temperature. Assuming the typical value of $T_e=10,000\,$K, the current constraints imply an extreme $n_e$ value above $1,000\,\rm cm^{-3}$. This is consistent with the picture of higher electron densities at high redshifts, as shown in Extended Data Fig. [5](#fig:ne_redshift).

High electron densities would naturally explain other non-detections of the \[OIII\]88$\mu$m line(cite: yoon2023) at $z>10$ given its relatively low critical density of(cite: Osterbrock2006) $n_c\approx5\times10^2\,\rm cm^{-3}$. Above this value, collisional deexcitation plays a significant role in gas cooling, diminishing the line luminosity produced by radiative cooling that is more efficient in the low density regime. Hence, future ALMA follow-up may be more successful by targeting the \[OIII\]52$\mu$m line thanks to its higher critical density of $n_c\approx3\times10^3\,\rm cm^{-3}$.\

10 url urlprefix

(ref: ArrabalHaro2023) Arrabal Haro, P. *et al.* . *Nature* **622**, 707–711 (2023).

(ref: Bunker2023) Bunker, A. J. *et al.* . *A&A* **677**, A88 (2023).

(ref: Harikane2024) Harikane, Y. *et al.* . *ApJ* **960**, 56 (2024).

(ref: Trump2023) Trump, J. R. *et al.* . *ApJ* **945**, 35 (2023).

(ref: Sanders2023) Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy, N. A. & Brammer, G. B. . *ApJ* **955**, 54 (2023).

(ref: Rieke2015) Rieke, G. H. *et al.* . *PASP* **127**, 584 (2015).

(ref: Rigby2023) Rigby, J. *et al.* . *PASP* **135**, 048001 (2023).

(ref: Castellano2022) Castellano, M. *et al.* . *ApJL* **938**, L15 (2022).

(ref: Naidu2022) Naidu, R. P. *et al.* . *ApJL* **940**, L14 (2022).

(ref: Treu2022a) Treu, T. *et al.* . *ApJ* **935**, 110 (2022).

(ref: Castellano2024) Castellano, M. *et al.* . *arXiv e-prints* arXiv:2403.10238 (2024).

(ref: Ono2023) Ono, Y. *et al.* . *ApJ* **951**, 72 (2023).

(ref: Bergamini2023) Bergamini, P. *et al.* . *ApJ* **952**, 84 (2023).

(ref: Curtis-Lake2023) Curtis-Lake, E. *et al.* . *Nature Astronomy* **7**, 622–632 (2023).

(ref: DEugenio2023) D’Eugenio, F. *et al.* . *arXiv e-prints* arXiv:2311.09908 (2023).

(ref: Wang2023) Wang, B. *et al.* . *ApJL* **957**, L34 (2023).

(ref: Carniani2024) Carniani, S. *et al.* . *arXiv e-prints* arXiv:2405.18485 (2024).

(ref: Storey2000) Storey, P. J. & Zeippen, C. J. . *MNRAS* **312**, 813–816 (2000).

(ref: Groves2006) Groves, B. A., Heckman, T. M. & Kauffmann, G. . *MNRAS* **371**, 1559–1569 (2006).

(ref: Nakajima2022b) Nakajima, K. & Maiolino, R. . *MNRAS* **513**, 5134–5147 (2022).

(ref: Cameron2023) Cameron, A. J. *et al.* . *A&A* **677**, A115 (2023).

(ref: Calabro2024) Calabrò, A. *et al.* . *arXiv e-prints* arXiv:2402.17829 (2024).

(ref: Topping2024) Topping, M. W. *et al.* . *arXiv e-prints* arXiv:2401.08764 (2024).

(ref: Kocevski2023) Kocevski, D. D. *et al.* . *ApJL* **954**, L4 (2023).

(ref: Harikane2023) Harikane, Y. *et al.* . *ApJ* **959**, 39 (2023).

(ref: Osterbrock2006) Osterbrock, D. E. & Ferland, G. J. *Astrophysics of gaseous nebulae and active galactic nuclei* (2006).

(ref: Nakajima2023) Nakajima, K. *et al.* . *ApJS* **269**, 33 (2023).

(ref: Ma2016) Ma, X. *et al.* . *MNRAS* **456**, 2140–2156 (2016).

(ref: Ucci2023) Ucci, G. *et al.* . *MNRAS* **518**, 3557–3575 (2023).

(ref: Torrey2019) Torrey, P. *et al.* . *MNRAS* **484**, 5587–5607 (2019).

(ref: endsley23) Endsley, R. *et al.* . *arXiv e-prints* arXiv:2306.05295 (2023).

(ref: ciesla23) Ciesla, L. *et al.* . *arXiv e-prints* arXiv:2309.15720 (2023).

(ref: tacchella22) Tacchella, S. *et al.* . *ApJ* **927**, 170 (2022).

(ref: cole2023) Cole, J. W. *et al.* . *arXiv e-prints* arXiv:2312.10152 (2023).

(ref: finkelstein23) Finkelstein, S. L. *et al.* . *arXiv e-prints* arXiv:2311.04279 (2023).

(ref: adams23) Adams, N. J. *et al.* . *arXiv e-prints* arXiv:2304.13721 (2023).

(ref: Reddy2022) Reddy, N. A. *et al.* . *ApJ* **926**, 31 (2022).

(ref: Kennicutt2012) Kennicutt, R. C. & Evans, N. J. . *ARA&A* **50**, 531–608 (2012).

(ref: Nagao2006) Nagao, T., Maiolino, R. & Marconi, A. . *A&A* **459**, 85–101 (2006).

(ref: Sanders2024) Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy, N. A. & Brammer, G. B. . *ApJ* **962**, 24 (2024).

(ref: Hirschmann2023) Hirschmann, M., Charlot, S. & Somerville, R. S. . *MNRAS* **526**, 3504–3518 (2023).

(ref: Curti2020) Curti, M., Mannucci, F., Cresci, G. & Maiolino, R. . *MNRAS* **491**, 944–964 (2020).

(ref: Kaasinen2017) Kaasinen, M., Bian, F., Groves, B., Kewley, L. J. & Gupta, A. . *MNRAS* **465**, 3220–3234 (2017).

(ref: Nakajima2022a) Nakajima, K. *et al.* . *ApJS* **262**, 3 (2022).

(ref: Schaerer2019) Schaerer, D., Fragos, T. & Izotov, Y. I. . *A&A* **622**, L10 (2019).

(ref: Lecroq2024) Lecroq, M. *et al.* . *MNRAS* **527**, 9480–9504 (2024).

(ref: Upadhyaya2024) Upadhyaya, A. *et al.* . *arXiv e-prints* arXiv:2401.16165 (2024).

(ref: Bakx2023) Bakx, T. J. L. C. *et al.* . *MNRAS* **519**, 5076–5085 (2023).

(ref: Isobe2023) Isobe, Y. *et al.* . *ApJ* **956**, 139 (2023).

(ref: Reddy2023) Reddy, N. A., Topping, M. W., Sanders, R. L., Shapley, A. E. & Brammer, G. . *ApJ* **952**, 167 (2023).

(ref: Asplund2009) Asplund, M., Grevesse, N., Sauval, A. J. & Scott, P. . *ARA&A* **47**, 481–522 (2009).

(ref: Kendrew2015) Kendrew, S. *et al.* . *PASP* **127**, 623 (2015).

(ref: 2000ApJ...533..682C) Calzetti, D. *et al.* . *ApJ* **533**, 682–695 (2000).

(ref: Beiler2023) Beiler, S. A. *et al.* . *ApJL* **951**, L48 (2023).

(ref: Pillepich2018) Pillepich, A. *et al.* . *MNRAS* **473**, 4077–4106 (2018).

(ref: Matthee2017) Matthee, J. *et al.* . *MNRAS* **465**, 3637–3655 (2017).

(ref: Paris2023) Paris, D. *et al.* . *ApJ* **952**, 20 (2023).

(ref: Grillo2014) Grillo, C. *et al.* . *ApJ* **786**, 11 (2014).

(ref: 2003MNRAS.338..508P) Pérez-González, P. G. *et al.* . *MNRAS* **338**, 508–524 (2003).

(ref: 2008ApJ...675..234P) Pérez-González, P. G. *et al.* . *ApJ* **675**, 234–261 (2008).

(ref: 2024arXiv240108782P) Pérez-González, P. G. *et al.* . *arXiv e-prints* arXiv:2401.08782 (2024).

(ref: 2003MNRAS.344.1000B) Bruzual, G. & Charlot, S. . *MNRAS* **344**, 1000–1028 (2003).

(ref: 2003PASP..115..763C) Chabrier, G. . *PASP* **115**, 763–795 (2003).

(ref: 1998PASP..110..761F) Ferland, G. J. *et al.* . *PASP* **110**, 761–778 (1998).

(ref: 2023RMxAA..59..327C) Chatzikos, M. *et al.* . **59**, 327–343 (2023).

(ref: Carnall2018) Carnall, A. C., McLure, R. J., Dunlop, J. S. & Davé, R. . *MNRAS* **480**, 4379–4401 (2018).

(ref: Boquien2019) Boquien, M. *et al.* . *A&A* **622**, A103 (2019).

(ref: Ferland2017) Ferland, G. J. *et al.* . **53**, 385–438 (2017).

(ref: Luridiana2015) Luridiana, V., Morisset, C. & Shaw, R. A. . *A&A* **573**, A42 (2015).

(ref: Popping2023) Popping, G. . *A&A* **669**, L8 (2023).

(ref: yoon2023) Yoon, I. *et al.* . *ApJ* **950**, 61 (2023).

(ref: Matthee2023) Matthee, J. *et al.* . *ApJ* **950**, 67 (2023).

(ref: Rinaldi24) Rinaldi, P. *et al.* . *arXiv e-prints* arXiv:2309.15671 (2023).

(ref: Alvarezmarquez23) Álvarez-Márquez, J. *et al.* . *A&A* **686**, A85 (2024).

(ref: Atek23) Atek, H. *et al.* . *Nature* **626**, 975–978 (2024).

(ref: Fujimoto23) Fujimoto, S. *et al.* . *ApJL* **949**, L25 (2023).

(ref: Hsiao24) Hsiao, T. Y.-Y. *et al.* . *arXiv e-prints* arXiv:2404.16200 (2024).

(ref: Lin23) Lin, Y.-H. *et al.* . *MNRAS* **527**, 4173–4182 (2024).

(ref: Stark15) Stark, D. P. *et al.* . *MNRAS* **454**, 1393–1403 (2015).

(ref: Stark17) Stark, D. P. *et al.* *MNRAS* **464**, 469–479 (2017).

(ref: Robertson2013) Robertson, B. E. *et al.* . *ApJ* **768**, 71 (2013).

(ref: Fujimoto2024) Fujimoto, S. *et al.* . *ApJ* **964**, 146 (2024).

**Extended Data Figures**

![](z_vs_xiion.png)

![](z_vs_ne.png)

**Supplementary Information**

![](sed_ghz2_synthesizer_v1.2.png)

[^1]: (<https://www.stsci.edu/contents/news/jwst/2024/updates-to-miri-low-resolution-spectrometer-reference-files>)

</paper>

Write the methods card for this paper.