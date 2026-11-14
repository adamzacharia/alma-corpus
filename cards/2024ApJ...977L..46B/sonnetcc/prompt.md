# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977L..46B\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977L..46B",
 "title": "[C II] Properties and Far-infrared Variability of a z = 7 Blazar",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Bañados, Eduardo",
 "n_authors": 10,
 "arxiv_id": "2408.12299",
 "doi": "10.3847/2041-8213/ad823b",
 "alma_projects_linked_by_archive": [
  "2021.A.00030.S"
 ]
}
```

Paper text:
<paper>
# \[CII\] properties and Far-Infrared variability of a $z=7$ blazar

## Abstract

We present millimeter observations of the host galaxy of the most distant blazar known, VLASS J041009.05$-$013919.88 (hereafter J0410–0139) at $z=7$, using ALMA and NOEMA observations. The ALMA data reveal a $(2.02\pm 0.36)\times 10^{42}$ erg s$^{-1}$ $\text{[C\,\textsc{ii]}}$ 158 $\mu$m emission line at $z=6.9964$ with a $\text{[C\,\textsc{ii]}}$-inferred star-formation rate of $58\pm 9\,M_\odot\,$yr$^{-1}$. We estimate a dynamical mass of $M_{\rm dyn,\ensuremath{\text{[C\,\textsc{ii]}}}}=(4.6\pm 2.0)\times 10^9\,M_\odot$, implying a black hole mass to host a dynamical mass ratio of $0.15^{+0.08}_{-0.05}$. The 238 GHz continuum (rest-frame IR) decreased by $\sim$$33\%$ from the NOEMA to the ALMA observations taken $\sim$10 months apart. The VLA 3–10 GHz radio flux densities showed a $\sim$$37\%$ decrease in a similar time frame, suggesting a causal connection. At face value, J0410–0139 would have the lowest $\text{[C\,\textsc{ii]}}$-to-IR luminosity ratio of a $z>5.7$ quasar reported to date ($\sim$$10^{-4}$). However, if only $<$$20\%$ of the measured IR luminosity were due to thermal emission from dust, the $\text{[C\,\textsc{ii]}}$-to-IR luminosity ratio would be typical of (U)LIRGS, and the star formation rates derived from $\text{[C\,\textsc{ii]}}$ and IR luminosities would be consistent. These results provide further evidence that synchrotron emission significantly contributes to the observed rest-frame IR emission of J0410–0139, similar to what has been reported in some radio-loud AGN at $z<1$.

# Introduction

Relativist jets have been well-established as a means for quasars to impact the properties of their host galaxies (cite: hardcastle2020; harrison2024). Associated with radio-loud quasars, these jets can uplift large amounts of gas, potentially promoting increased star formation in their hosts (cite: bieri2015), or quenching star formation (cite: comerford2020).

To date, the cold dust and gas of only seven galaxies hosting radio-loud quasars at $5.8\!<\!z\!<\!6.9$ have been investigated with the Atacama Large Millimeter/submillimeter Array (ALMA) and NOrthern Extended Millimeter Array (NOEMA), and none beyond $z>6.9$ (cite: rojas2021; khusanova2022; banados2023). Although the statistics are still limited, their $\text{[C\,\textsc{ii]}}$- and IR-derived star-formation properties are consistent with the ones reported for the much more common (cite: keller2024)—and thus more studied—radio-quiet quasars (c.f., (cite: decarli2018; venemans2020)). If galaxy properties are consistent between quasar hosts with and without jets at this epoch, then either the jets are not significantly impacting their galaxies or jets are common but sporadic (cite: connor2024). Fundamental to these arguments is the assumption that the $\text{[C\,\textsc{ii]}}$ and underlying continuum emissions are linked only to star formation and are not associated with the active galactic nucleus (AGN). However, this assumption might be flawed.

(cite: rojas2021), studying the $z=5.83$ radio-quasar P352–-15, found that a modified thermal black body model consistent with the quasar host’s 290 GHz flux under-predicted the observed 100 GHz flux. The interpretation of this discrepancy is that, at 100 GHz, the flux is being enhanced by contributions from the synchrotron emission from the jets observed at lower frequencies. (cite: khusanova2022), as part of a study of four $z>6$ quasars with NOEMA, further considered this possibility and described multiple ways that high-redshift radio-loud AGN might impact their observed $\text{[C\,\textsc{ii]}}$ emission, biasing estimates of star formation rate (SFR). Recently, (cite: li2024) studied several CO transitions of the $z=6.18$ radio-quasar J1429+5447, finding the lowest CO excitation among all published $z\sim 6$ quasars with similar data (all the others are radio-quiet).

Here, we report NOEMA and ALMA observations of a newly discovered radio-quasar at $z_{\rm \ensuremath{\text{Mg\,\textsc{ii}}}}=6.995\pm 0.001$, VLASS J041009.05$-$013919.88 (hereafter J0410–0139), powered by a black hole with the mass of $6.9^{+0.5}_{-0.4} \times 10^8$ $M_\odot$ (cite: banados2024a). Based on its rapid radio variability, X-ray properties, and compact radio emission on pc scales, (cite: banados2024a) suggests that J0410–0139 is a blazar. The new data—separated by 35 days in the quasar’s rest frame and matched with closely-timed archival 1–10 GHz radio observations—therefore enable a look at the properties of jet-affected high-redshift quasar host galaxy that accounts for the contributions of the jet emission itself.

Throughout this Letter, we adopt a standard flat $\Lambda$CDM cosmology with $H_0 = 70 \,\mbox{km\,s}^{-1}$ Mpc$^{-1}$, $\Omega_M = 0.30$.

# Observations

## NOEMA

To characterize the host galaxy of J0410–0139, we obtained NOEMA observations targeting the $\text{[C\,\textsc{ii]}}$ emission line ($\nu_{rest}=1900.5369$ GHz) and its underlying continuum emission. The observations were carried out on 16 November 2021 with ten antennae in band 3. The total on-source time was 5.2 hours under good weather conditions with low precipitable water vapor (PWV$\sim1$ mm). We used `clic` package for calibration, part of the GILDAS software. We used LKHA101 for flux density calibration, 3C84 for bandpass calibration, and 0420-014 for phase and amplitude calibrations. We produced an image cube with 50 km s$^{-1}$ resolution using natural weighting and HOGBOM cleaning down to the $2\sigma$ level. The data cover the $\sim220-243$ GHz range and the synthesized beam size is $\sim0.8\ensuremath{''}\times1.6\ensuremath{''}$ with a position angle PA=$9.2^\circ$.

We produced an image of continuum emission at 224 GHz by averaging all the channels in the lower side band (LSB). Similarly, we created a 239 GHz continuum emission image from the upper side band (USB), excluding the channels within $\pm1000$ km s$^{-1}$ from the expected frequency of the $\text{[C\,\textsc{ii]}}$ line. The continuum emission is well detected in both the LSB and USB images with signal-to-noise ratios S/N$>20$ (Fig. [1](#fig:alma_noema)). In both images, the continuum source is unresolved. The coordinates of the peak in the 224 GHz continuum emission are RA$=$04:10:09.05; DEC$=$$-$01:39:19.90. For the 239 GHz continuum peak emission, the coordinates are RA$=$04:10:09.05; DEC$=$$-$01:39:19.98. These continuum locations are consistent with the quasar’s optical position (see Fig. [1](#fig:alma_noema)). We extracted spectra centered on the brightest pixel of the USB continuum map, and no $\text{[C\,\textsc{ii]}}$ emission line is detected from the brightest pixel or a $1.5\ensuremath{''}$ radius aperture.

## ALMA

We also obtained ALMA observations of J0410–0139 in the C-4 configuration, using 45-46 antennas over three passes: On 28 August 2022 (PWV=2.5–3.0 mm), 29 August 2022 (PWV$\sim$2.8 mm), and 30 August 2022 (PWV$\sim$1.1 mm). The total on-source time is about 2.5 hours. The data were reduced using standard procedures with CASA (cite: mcmullin2007). We produced image cubes with 40 km s$^{-1}$ resolution using natural weighting and cleaning to the $2\sigma$ level. The synthesized beam is $0.49\ensuremath{''}\times 0.68\ensuremath{''}$ with PA=$-69^\circ$.

Both the continuum and $\text{[C\,\textsc{ii]}}$ line are clearly detected with S/N of 36 and 7, respectively (Fig. [1](#fig:alma_noema) and Table [1](#tab:properties)). The flux of the $\text{[C\,\textsc{ii]}}$ line is consistent with the noise of the continuum-subtracted NOEMA image, explaining the NOEMA non-detection. The peak of the 238 GHz continuum emission (RA$=$04:10:09.05; DEC$=$$-$01:39:19.91) coincides with the quasar’s optical position (see Fig. [1](#fig:alma_noema)). We fit a two-dimensional Gaussian to the 238 GHz continuum source with the CASA task `imfit`. The source is resolved, with a deconvolved size of $(0.57\pm 0.10)^{\prime\prime}\times (0.68\pm 0.10)^{\prime\prime}$ \[$(3.0\pm 0.5)\,\mathrm{kpc}\times (3.5\pm 0.5)\,\mathrm{kpc}$\], and a PA of $82^\circ\pm 59^\circ$. The centroid of the $\text{[C\,\textsc{ii]}}$ is offset by $0.35\ensuremath{''}$ (1.81  kpc) from the optical position. We used a curve of growth analysis to determine the optimal aperture radius to extract the spectrum. The cumulative flux density reaches a plateau at $1.5\ensuremath{''}$, independent of whether we use the optical or $\text{[C\,\textsc{ii]}}$ centroid; thus, all the flux density is recovered with this aperture radius. The total $\text{[C\,\textsc{ii]}}$ flux is $0.45\pm 0.08\,$Jy km s$^{-1}$ (see Table [1](#tab:properties)).

![](figures/f1.pdf)

# Results and discussion

## \[CII\] properties

$\text{[C\,\textsc{ii]}}$ is among the brightest emission lines in star-forming galaxies, the main coolant of the neutral interstellar medium, and a tracer of star formation (cite: herrera-camus2015). We fit the ALMA $\text{[C\,\textsc{ii]}}$ spectrum shown in Fig. [1](#fig:alma_noema) with one and two Gaussians. Both fits describe the data well, but neither functional form is preferred according to Bayesian Information Criterion. The fit with two Gaussian reveals a second component shifted by $\sim300$ km s$^{-1}$. We produced line images centered on each Gaussian by averaging the channels containing the line across 1.2$\times$FWHM, which maximizes the S/N for detecting a Gaussian line (see Appendix A in (cite: novak2020)). The image of the potential shifted component does not include any channel containing the main component. We did not find any signature above $3.5\sigma$ on the image of the shifted component. We conclude that the shifted component in the spectrum is consistent with noise. Therefore, we use the single Gaussian fit to derive the results presented in Table [1](#tab:properties) and produce the final $\text{[C\,\textsc{ii]}}$ emission line image averaging channels across 1.2$\times$FWHM (see Fig. [1](#fig:alma_noema)).

We also show continuum subtracted 40 km s$^{-1}$ $\text{[C\,\textsc{ii]}}$ channel images in Figure [2](#fig:chmaps30). The emission is highly concentrated in the central channels, although there is some evidence of multiple peaks and different substructures in separate channel images. While this could indicate a merging system, the evidence is not as compelling as what is found for other systems at similar redshifts (cite: banados2019a; neeleman2019; neeleman2021; decarli2017; decarli2019). Higher S/N data are required to provide conclusive kinematic results.

With our $\text{[C\,\textsc{ii]}}$ data we can make a rough estimate of the dynamical mass of the host galaxy, following (cite: decarli2018). We assume a dispersion-dominated system as there is no evidence of rotation in the channel maps of Fig. [2](#fig:chmaps30). Thus, the dynamical mass can be expressed as follows:

$$\begin{equation}
    M_{\rm dyn,\ensuremath{\text{[C\,\textsc{ii]}}}} = \frac{3}{2}\,\frac{R_{\ensuremath{\text{[C\,\textsc{ii]}}}}\, \sigma^2_{\ensuremath{\text{[C\,\textsc{ii]}}}}}{G},
\end{equation}$$ where $R_{\ensuremath{\text{[C\,\textsc{ii]}}}}$ is the major semi-axis of the Gaussian fit of the $\text{[C\,\textsc{ii]}}$ map ($1.75\pm 0.25\,$kpc), $\sigma_\ensuremath{\text{[C\,\textsc{ii]}}}$ is the velocity dispersion from the Gaussian fit of the $\text{[C\,\textsc{ii]}}$ line ($88\pm17\,$km s$^{-1}$) and $G$ is the gravitational constant. This results in $M_{\rm dyn,\ensuremath{\text{[C\,\textsc{ii]}}}}=(4.6\pm 2.0)\times 10^9\,M_\odot$. Assuming that the dynamical mass is comparable to the stellar mass, together with the $\text{[C\,\textsc{ii]}}$-derived SFR of $58\pm 9\,M_\odot\,$yr$^{-1}$, make the host of J0410–0139 consistent with a main-sequence galaxy (cite: schreiber2015; algera2023).

The ratios of the masses of the central supermassive black holes and their host galaxies across cosmic time can provide key insights on galaxy evolution models (cite: habouzit2022). The black hole to galaxy dynamical mass ratio for J0410–0139 is $0.15^{+0.08}_{-0.05}$. Assuming that the dynamical mass is comparable to stellar or bulge masses, J0410–0139 would be $\sim$$2$ dex above the local black hole-host mass relations (cite: kormendy2013). This result is consistent with the overmassive supermassive black holes of $z>6$ quasars identified with ALMA and JWST dynamical mass estimates (cite: neeleman2021; marshall2023).

## IR Continuum variability

The continuum emission from J0410–0139 is robustly detected in both NOEMA and ALMA observations. However, the measured flux densities are inconsistent by $\sim 33\%$ (see Table [1](#tab:properties) and Figs. [1](#fig:alma_noema) and [3](#fig:sed)). The ALMA observations were taken 285 days after the NOEMA ones, i.e., about 35 days in the quasar’s rest frame. Figure [3](#fig:sed) also shows the quasi-simultaneous VLA measurements of 2021 and 2022 (taken 39 rest-frame days apart; see Table E1 in (cite: banados2024a)). The VLA flux densities above 3 GHz show an average decrement of $\sim 37\%$. We note that the trend is inverted at observed $\sim$1.5 GHz, but the emission at frequencies lower than the radio SED peak can be affected by other physical processes, such as free-free absorption or synchrotron self-absorption (cite: gloudemans2023). The VLA 2021 (2022) and NOEMA (ALMA) data were observed just 6.5 (2.8) days apart in the quasar’s rest frame. We, therefore, interpret the differences measured at $\sim$240 GHz to be due to synchrotron variability. Indeed, to be able to measure this variability, the synchrotron radiation must be the dominant source in the rest-frame FIR of J0410–0139.

Extrapolating the measured synchrotron power law to rest-frame IR we would have expected an even brighter source (by a factor $2-3$) in the continuum detections (see Fig. [3](#fig:sed)). To explain the spectral energy distribution (SED), the synchrotron emission must have a break, steepening at frequencies in between our cm and mm measurements. Such a break is expected for young radio sources given that higher-energy electrons radiate their energy faster and therefore have shorter lifetimes (cite: carilli1991). Similar SED behavior has been observed in other powerful radio emitting $z\gtrsim 6$ quasars, and it has been used as an indirect argument that the synchrotron emission can affect the inferred FIR properties of the quasar host galaxies (cite: rojas2021; khusanova2022).

In the case of J0410–0139, we have direct evidence of the synchrotron emission affecting the IR properties. If we were to assume that the NOEMA/ALMA data trace cold dust from the host galaxies—as in most studies (cite: venemans2020; izumi2019)—we would obtain very different IR luminosities, cold dust masses (not reported to avoid confusion), and star-formation rates from one epoch to the other (Fig. [3](#fig:sed)). For example, the inferred SFR$_{\rm IR}$ following (cite: kennicutt1998) would be $400\pm 29\,M_\odot\,$yr$^{-1}$ and $295\pm 21\,M_\odot\,$yr$^{-1}$ in 2021 and 2022, respectively. That is 4–9 times larger than what is inferred from the $\text{[C\,\textsc{ii]}}$ line (see Table [1](#tab:properties)). The dust masses and star-formation rates do not change in a month. Thus, one must be careful of blindly interpreting rest-frame IR continuum emission as fully originating from dust, at least for quasars with evidence of relativistic jets.

## \[CII\] deficit

The observed trend of decreasing $\text{[C\,\textsc{ii]}}$ to total IR luminosity for galaxies with $L_{\rm IR}> 10^{11}\,M_\odot$ is known as the “$\text{[C\,\textsc{ii]}}$ deficit” (cite: malhotra2001; diaz-santos2013). The physical explanation for this trend is still an open question and possible explanations include the effects of AGN, the intensity of the radiation field, and optically thick $\text{[C\,\textsc{ii]}}$ emission (cite: casey2014; lagache2018).

In general, the $z>5.7$ quasars follow the $\text{[C\,\textsc{ii]}}$ deficit as shown in Figure [4](#fig:ciidefilcit). Based on its measured IR flux density, J0410–0139 would be the $z>5.7$ quasar with the lowest $\text{[C\,\textsc{ii]}}$-to-IR luminosity ratio reported to date, ranging from $\log  L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}/L_{\rm IR} = -3.7$ to $\log  L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}/L_{\rm IR} = -4.0$ (see Figure [4](#fig:ciidefilcit)). From Section [3.2](#sec:variability), we know that J0410–0139’s IR luminosity is not only due to cold dust but is also affected—and most likely dominated—by synchrotron emission. We can obtain an order-of-magnitude estimate of the synchrotron contribution to the IR luminosity, considering that the host galaxy contribution is not expected to vary in scales of months. Under the assumption that dust-obscured star formation dominates for massive galaxies (cite: ferrara2022; algera2023), to make the $\text{[C\,\textsc{ii]}}$- and IR-derived SFR compatible, the synchrotron contribution needs to be 85% and 80% in the mm observations from 2021 and 2022, respectively. Taking this into account, the host galaxy of J0410–0139 would comfortably be located in the expected region for local (U)LIRG galaxies in the $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}/L_{\rm IR}$ vs. $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ plane (Fig. [4](#fig:ciidefilcit)).

We can speculate that some synchrotron contribution to the IR luminosities could explain the “$\text{[C\,\textsc{ii]}}$ deficit” for some of the luminous quasars. However, if we separate the radio-loud quasars (and, therefore, the sources that are most likely affected by synchrotron radiation) in Figure [4](#fig:ciidefilcit), the picture is not that clear. The majority of the radio-loud quasars (although the statistics are still limited) do not seem to have particularly anomalous $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}/L_{\rm IR}$. The fraction of sources non-detected in $\text{[C\,\textsc{ii]}}$ and/or underlying continuum seems to be higher for radio-loud quasars. However, the current number statistics are limited, and therefore, a larger sample of radio-loud quasars with $\text{[C\,\textsc{ii]}}$ observations is required to robustly determine any potential differences with the measurements on radio-quiet quasars.

## Nearby continuum source

There is a continuum source in the ALMA data at R.A$=$04:10:10.01 and Decl.$=-$01:39.19.40 ($14.37\ensuremath{''}$ from J0410–0139). The continuum emission is marginally resolved, with a deconvolved size of $(0.66\pm 0.26)^{\prime\prime}\times (0.43\pm 0.26)^{\prime\prime}$. The integrated flux density is $S_{238\,\mathrm{GHz}}=0.20 \pm 0.04$ mJy. No line is detected in a spectrum extracted from the brightest pixel or a $1.5\ensuremath{''}$ radius aperture. The source is undetected in all the other existing multi-wavelength datasets in this field (see (cite: banados2024a)); thus, its nature and redshift remain unknown.

![](figures/f2.pdf)

![](figures/f3.pdf)

![](figures/f4.pdf)

# Summary and concluding remarks

Here, we presented NOEMA and ALMA observations of the highest redshift blazar currently known, J0410–0139. The main results can be summarized as:

- The $\text{[C\,\textsc{ii]}}$ emission line is detected in the ALMA data (Figure [1](#fig:alma_noema)), providing a systemic redshift of $z_{\ensuremath{\text{[C\,\textsc{ii]}}}} = 6.9964\pm 0.0005$, in good agreement with the redshift derived from the quasar’s broad line region ($z_{\ensuremath{\text{Mg\,\textsc{ii}}}}=6.995 \pm 0.001$ ; $\Delta v = 53 \pm 42\,{\rm km\,s}\ensuremath{^{-1}}$; (cite: banados2024a)). The $\text{[C\,\textsc{ii]}}$ measurements and derived properties are listed in Table [1](#tab:properties).

- The centroid of the $\text{[C\,\textsc{ii]}}$ emission is offset by 0.35$''$ (1.81 kpc) from the position of the quasar (Figure [1](#fig:alma_noema)). The $\text{[C\,\textsc{ii]}}$ emission reveals multiple peaks and different substructures in separate channel maps (Figure [2](#fig:chmaps30)).

  This could be evidence of an ongoing merger; however, with the current sensitivity of the observations, it is difficult to conclusively constrain the kinematics.

- We estimate a dynamical mass of $M_{\rm dyn,\ensuremath{\text{[C\,\textsc{ii]}}}}=(4.6\pm 2.0)\times 10^9\,M_\odot$. We obtain black hole mass to host a dynamical mass ratio of $0.15^{+0.08}_{-0.05}$, placing the quasar above the local relation and consistent with other $z\gtrsim 6$ quasars.

- We detect a decrease of $\sim33\%$ in the rest-frame IR continuum in about one month in the quasar’s rest-frame (Table [1](#tab:properties)). This decrease is strongly correlated with the variability measured at GHz frequencies by the VLA on a similar timeframe (Figure [3](#fig:sed)). At $z<1$, contamination of synchrotron to rest-frame IR continuum emission is frequently observed in radio-loud AGN (cite: weiss2008; dicken2023). We interpret J0410–0139’s variability in the IR as due to synchrotron emission, providing the first direct evidence of synchrotron radiation affecting the measured IR properties of $z\gtrsim 6$ quasars.

- J0410–0139 shows the lowest $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}/L_{\rm IR}$ among all $z>5.7$ quasars studied to date. We argue that this is because the synchrotron emission is dominating the IR luminosity ($\gtrsim 80\%$). The influence of synchrotron emission can help explain some of the sources showing the most extreme “$\text{[C\,\textsc{ii]}}$ deficit” (Section [3.3](#sec:ciideficit)). However, most of the radio-loud quasars studied to date are not extreme sources in the $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}/L_{\rm IR}$ vs. $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ plane, complicating this interpretation (Figure [3](#fig:sed)).

This work highlights the importance of having a well-sampled and, if possible, quasi-simultaneous SED for interpreting the properties of quasars with strong radio emission.

| Quantity | Value | Units |
|:---|:---|:---|
| $z_{\rm \ensuremath{\text{Mg\,\textsc{ii}}}}$ | $6.995\pm 0.001$ |  |
| $z_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ | $6.9964\pm 0.0005$ |  |
| FWHM$_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ | $206 \pm 40$ | km s$^{-1}$ |
| I$_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ | $0.45 \pm 0.08$ | Jy km s$^{-1}$ |
| $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ | $(2.02\pm 0.36)\times 10^{42}$ | erg s$^{-1}$ |
| SFR$_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}^a$ | $58\pm 9$ | $M_\odot\,$yr$^{-1}$ |
| $M_{\rm dyn,\ensuremath{\text{[C\,\textsc{ii]}}}}^b$ | $(4.6\pm 2.0)\times 10^9$ | $M_\odot$ |
| S$_{\rm 224\,GHz}$ (NOEMA2021) | $0.99\pm 0.07$ | mJy |
| S$_{\rm 239\,GHz}$ (NOEMA2021) | $1.11\pm 0.09$ | mJy |
| S$_{\rm 238\,GHz}$ (ALMA2022) | $0.84\pm 0.06$ | mJy |
| $L_{\rm IR}(2021)^c$ | $(1.53\pm 0.11)\times 10^{46}$ | erg s$^{-1}$ |
| $L_{\rm IR}(2022)^c$ | $(1.13\pm 0.08)\times 10^{46}$ | erg s$^{-1}$ |
|  |  |  |

: **Measured and derived properties of J0410–0139.**

\
$^a$ The SFR$_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ is calculated using $\log \mathrm{SFR}_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}=-6.09+0.90\times \log L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$, with $L_{\rm \ensuremath{\text{[C\,\textsc{ii]}}}}$ in solar luminosities (cite: delooze2014).\
$^b$ See Sect. [3.1](#sec:ciiprop) for the dynamical mass estimation.\
$^c$ The IR luminosities are integrated over $8-1000\,\mu$m assuming a modified black body with dust temperature of $T_d=47\,K$ and emissivity index $\beta=1.6$ (see Fig. [3](#fig:sed)).

We thank the staff of IRAM/NOEMA and ALMA for making these observations possible. YK thanks the support of the German Space Agency (DLR) through the program LEGACY 50OR2303. CM acknowledges support from Fondecyt Iniciacion grant 11240336 and ANID BASAL project FB210003. Based on observations carried out with the IRAM Interferometer NOEMA (program S21DK). IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.A.00030.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

NOEMA, ALMA

# Software

astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A), CASA (cite: mcmullin2007), GILDAS <https://www.iram.fr/IRAMFR/GILDAS>, interferopy (cite: interferopy), Matplotlib (cite: hunter2007)

natexlab

(ref: algera2023) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142, doi: [`10.1093/mnras/stac3195`](http://doi.org/10.1093/mnras/stac3195)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: banados2015b) Bañados, E., Decarli, R., Walter, F., et al. 2015, ApJL, 805, L8, doi: [`10.1088/2041-8205/805/1/L8`](http://doi.org/10.1088/2041-8205/805/1/L8)

(ref: banados2019a) Bañados, E., Novak, M., Neeleman, M., et al. 2019, ApJL, 881, L23, doi: [`10.3847/2041-8213/ab3659`](http://doi.org/10.3847/2041-8213/ab3659)

(ref: banados2023) Bañados, E., Schindler, J.-T., Venemans, B. P., et al. 2023, ApJS, 265, 29, doi: [`10.3847/1538-4365/acb3c7`](http://doi.org/10.3847/1538-4365/acb3c7)

(ref: banados2024a) Bañados, E., Momjian, E., Connor, T., et al. 2024, arXiv e-prints, arXiv:2407.07236. [`https://arxiv.org/abs/2407.07236`](https://arxiv.org/abs/2407.07236)

(ref: bieri2015) Bieri, R., Dubois, Y., Silk, J., & Mamon, G. A. 2015, ApJL, 812, L36, doi: [`10.1088/2041-8205/812/2/L36`](http://doi.org/10.1088/2041-8205/812/2/L36)

(ref: interferopy) Boogaard, L., Meyer, R. A., & Novak, M. 2021, Interferopy: analysing datacubes from radio-to-submm observations, doi: [`10.5281/ZENODO.5775603`](http://doi.org/10.5281/ZENODO.5775603)

(ref: carilli1991) Carilli, C. L., Perley, R. A., Dreher, J. W., & Leahy, J. P. 1991, ApJ, 383, 554, doi: [`10.1086/170813`](http://doi.org/10.1086/170813)

(ref: casey2014) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: comerford2020) Comerford, J. M., Negus, J., Müller-Sánchez, F., et al. 2020, ApJ, 901, 159, doi: [`10.3847/1538-4357/abb2ae`](http://doi.org/10.3847/1538-4357/abb2ae)

(ref: connor2024) Connor, T., Bañados, E., Cappelluti, N., & Foord, A. 2024, Universe, 10, 227, doi: [`10.3390/universe10050227`](http://doi.org/10.3390/universe10050227)

(ref: delooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62, doi: [`10.1051/0004-6361/201322489`](http://doi.org/10.1051/0004-6361/201322489)

(ref: decarli2017) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: decarli2018) —. 2018, ApJ, 854, 97, doi: [`10.3847/1538-4357/aaa5aa`](http://doi.org/10.3847/1538-4357/aaa5aa)

(ref: decarli2019) Decarli, R., Dotti, M., Bañados, E., et al. 2019, ApJ, 880, 157, doi: [`10.3847/1538-4357/ab297f`](http://doi.org/10.3847/1538-4357/ab297f)

(ref: diaz-santos2013) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68, doi: [`10.1088/0004-637X/774/1/68`](http://doi.org/10.1088/0004-637X/774/1/68)

(ref: dicken2023) Dicken, D., Tadhunter, C. N., Nesvadba, N. P. H., et al. 2023, MNRAS, 519, 5807, doi: [`10.1093/mnras/stac3465`](http://doi.org/10.1093/mnras/stac3465)

(ref: ferrara2022) Ferrara, A., Sommovigo, L., Dayal, P., et al. 2022, MNRAS, 512, 58, doi: [`10.1093/mnras/stac460`](http://doi.org/10.1093/mnras/stac460)

(ref: gloudemans2023) Gloudemans, A. J., Saxena, A., Intema, H., et al. 2023, A&A, 678, A128, doi: [`10.1051/0004-6361/202347582`](http://doi.org/10.1051/0004-6361/202347582)

(ref: habouzit2022) Habouzit, M., Onoue, M., Bañados, E., et al. 2022, MNRAS, 511, 3751, doi: [`10.1093/mnras/stac225`](http://doi.org/10.1093/mnras/stac225)

(ref: hardcastle2020) Hardcastle, M. J., & Croston, J. H. 2020, New A Rev., 88, 101539, doi: [`10.1016/j.newar.2020.101539`](http://doi.org/10.1016/j.newar.2020.101539)

(ref: harrison2024) Harrison, C. M., & Ramos Almeida, C. 2024, Galaxies, 12, 17, doi: [`10.3390/galaxies12020017`](http://doi.org/10.3390/galaxies12020017)

(ref: herrera-camus2015) Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1, doi: [`10.1088/0004-637X/800/1/1`](http://doi.org/10.1088/0004-637X/800/1/1)

(ref: hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: izumi2019) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2019, PASJ, 71, 111, doi: [`10.1093/pasj/psz096`](http://doi.org/10.1093/pasj/psz096)

(ref: keller2024) Keller, P. M., Thyagarajan, N., Kumar, A., Kanekar, N., & Bernardi, G. 2024, MNRAS, 528, 5692, doi: [`10.1093/mnras/stae418`](http://doi.org/10.1093/mnras/stae418)

(ref: kennicutt1998) Kennicutt, Jr., R. C. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: khusanova2022) Khusanova, Y., Bañados, E., Mazzucchelli, C., et al. 2022, A&A, 664, A39, doi: [`10.1051/0004-6361/202243660`](http://doi.org/10.1051/0004-6361/202243660)

(ref: kormendy2013) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511, doi: [`10.1146/annurev-astro-082708-101811`](http://doi.org/10.1146/annurev-astro-082708-101811)

(ref: lagache2018) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130, doi: [`10.1051/0004-6361/201732019`](http://doi.org/10.1051/0004-6361/201732019)

(ref: li2024) Li, J., Wang, R., Pensabene, A., et al. 2024, ApJ, 962, 119, doi: [`10.3847/1538-4357/ad1754`](http://doi.org/10.3847/1538-4357/ad1754)

(ref: luhman2003) Luhman, M. L., Satyapal, S., Fischer, J., et al. 2003, ApJ, 594, 758, doi: [`10.1086/376965`](http://doi.org/10.1086/376965)

(ref: malhotra2001) Malhotra, S., Kaufman, M. J., Hollenbach, D., et al. 2001, ApJ, 561, 766, doi: [`10.1086/323046`](http://doi.org/10.1086/323046)

(ref: marshall2023) Marshall, M. A., Perna, M., Willott, C. J., et al. 2023, A&A, 678, A191, doi: [`10.1051/0004-6361/202346113`](http://doi.org/10.1051/0004-6361/202346113)

(ref: mcmullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: neeleman2019) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10, doi: [`10.3847/1538-4357/ab2ed3`](http://doi.org/10.3847/1538-4357/ab2ed3)

(ref: neeleman2021) Neeleman, M., Novak, M., Venemans, B. P., et al. 2021, ApJ, 911, 141, doi: [`10.3847/1538-4357/abe70f`](http://doi.org/10.3847/1538-4357/abe70f)

(ref: novak2020) Novak, M., Venemans, B. P., Walter, F., et al. 2020, ApJ, 904, 131, doi: [`10.3847/1538-4357/abc33f`](http://doi.org/10.3847/1538-4357/abc33f)

(ref: rojas2021) Rojas-Ruiz, S., Bañados, E., Neeleman, M., et al. 2021, ApJ, 920, 150, doi: [`10.3847/1538-4357/ac1a13`](http://doi.org/10.3847/1538-4357/ac1a13)

(ref: schreiber2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74, doi: [`10.1051/0004-6361/201425017`](http://doi.org/10.1051/0004-6361/201425017)

(ref: venemans2020) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130, doi: [`10.3847/1538-4357/abc563`](http://doi.org/10.3847/1538-4357/abc563)

(ref: weiss2008) Weiß, A., Kovács, A., Güsten, R., et al. 2008, A&A, 490, 77, doi: [`10.1051/0004-6361:200809909`](http://doi.org/10.1051/0004-6361:200809909)

</paper>

Write the methods card for this paper.