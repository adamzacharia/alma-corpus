# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...993..158S\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...993..158S",
 "title": "Cold Gas in a Post-starburst Pair in the z ∼ 1.4 HeavyMetal Survey: Major Mergers as a Pathway to Retain Gas in Quenched Galaxies",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Suess, Katherine A.",
 "n_authors": 15,
 "arxiv_id": "2506.14361",
 "doi": "10.3847/1538-4357/ae0933",
 "alma_projects_linked_by_archive": [
  "2016.1.01126.S",
  "2017.1.01109.S",
  "2019.1.01286.S"
 ]
}
```

Paper text:
<paper>
# Cold gas in a post-starburst pair at $z\sim1.4$: major mergers as a pathway to quenching in the HeavyMetal survey

## Abstract

Recent observations at low redshift have revealed that some post-starburst galaxies retain significant molecular gas reservoirs despite low ongoing star formation rates, challenging theoretical predictions for galaxy quenching. To test whether this finding holds during the peak epoch of quenching, here we present ALMA CO(2–1) observations of five spectroscopically confirmed post-starburst galaxies at $z\sim1.4$ from the HeavyMetal survey. While four galaxies are undetected in CO emission, we detect $M_{\rm H_2}\sim10^{9.7}~M_\odot$ of molecular gas in one system. The detected system is a close pair of massive ($M_* = 10^{11.1-11.2}M_\odot$) post-starburst galaxies with no clear tidal features, likely caught in the early stages of a major merger. These results suggest that mergers may be a key factor in retaining molecular gas while simultaneously suppressing star formation in quenched galaxies at high redshift, possibly by driving increased turbulence that decreases star formation efficiency. Unlike previous studies at $z<1$, we find no correlation between molecular gas mass and time since quenching. This may be explained by the fact that — despite having similar UVJ colors — all galaxies in our sample have post-burst ages older than typical gas-rich quenched systems at low redshift. Our results highlight the importance of major mergers in shaping the cold gas content of quiescent galaxies during the peak epoch of quenching.

[^1]

# Introduction

One of the most intriguing puzzles in galaxy formation is the quiescent nature of massive early-type galaxies. There should be plenty of fuel for star formation in these galaxies: gas from the intergalactic medium is continuously falling onto their dark matter halos, and their evolving stellar populations have substantial mass-loss rates. As a result, most cosmological simulations must resort to ad hoc models to heat or remove cold gas in order to halt the star formation in these massive galaxies. Feedback from active galactic nuclei (AGN) — where quasar outflows expel gas from the galaxy, then the radio mode maintains quenching by heating the gas — is one of the most popular of these models (cite: croton06; hopkins06). This AGN feedback and subsequent quenching can be triggered by major mergers (cite: springel05; wellons15). Mechanisms that make cold gas accretion inefficient — due to virial shocks (cite: dekel06) or the mass of the halo (cite: dave17; feldmann17) — have also been proposed to quench massive galaxies. The one aspect that these models all have in common though, is that recently-quenched galaxies should not retain substantial cold molecular gas reservoirs.

In contrast to these theoretical predictions, observations of recently-quenched “post-starburst" galaxies at $z<1$ have found that these quiescent galaxies can retain gas fractions of up to $\sim20\%$ — similar to star-forming galaxies of similar mass and redshift, and an order of magnitude higher than expected for galaxies with such suppressed star formation rates (cite: french15; suess17). Interestingly, the gas fraction in these galaxies appears to be a strong function of post-quenching age: the youngest post-starburst galaxies are often gas-rich, while galaxies which quenched $\gtrsim150$ Myr before observation are uniformly gas-poor (cite: french18; bezanson22). Given the low star formation rates in these galaxies, it would take far longer than 150 Myr to consume all of the residual gas. These observations raise several puzzles: how are these galaxies able to retain such large gas reservoirs after they quench? Why does this gas disappear so quickly after quenching? And what do these observations tell us about the mechanisms responsible for quenching?

One key caveat of these $z<1$ observational studies is that they have targeted unusual galaxies: most quiescent galaxies stop forming stars at higher redshifts of $z\sim1-3$ (cite: whitaker12; wild16; belli19) and may quench via different physical mechanisms than their low-redshift counterparts. To understand the processes responsible for creating the bulk of the quiescent population, we need to measure the molecular gas properties of post-starburst galaxies during the peak quenching epoch and compare their star-formation efficiencies to typical star-forming galaxies at similar redshifts.

To date, only a few studies have attempted to directly detect cold gas in $z>1$ quiescent galaxies. (cite: bezanson19) and (cite: williams21) placed limits of $f_{\rm{gas}}<2-7\%$ in seven massive quiescent galaxies at $z\sim1.5$; however, given the old stellar ages of these galaxies and the strong age-gas trend observed at lower redshift, these non-detections are unsurprising. (cite: belli21) finds $f_{\rm{gas}}\sim13-23\%$ in three young quiescent galaxies at $z\sim1$; however, these galaxies were specifically selected to have 24$\mu$m excesses, and may not be typical of the broader population of quenching galaxies. (cite: zanella23) targeted two slightly lower-mass young quiescent galaxies ($\log{M_*/M_\odot}\sim10.6$) and detected both, with gas fractions of $f_{\rm{gas}}\sim8-16\%$. Of these studies, only one of the (cite: zanella23) targets probes the youngest (light-weighted age $t_{50}\lesssim 200$Myr) post-starburst galaxies that $z<1$ studies imply may retain much larger gas reservoirs. In large part, this observational gap was due to historical difficulties spectroscopically-confirming quiescent galaxies at high redshifts: both redshifts and ages must be measured from relatively faint absorption features that are shifted into the rest-frame near-infrared at $z\gtrsim1$, which from the ground requires very long integrations with infrared spectrographs. JWST/NIRSpec has recently revolutionized this field, taking detailed spectra of dozens of quiescent galaxies from $1\lesssim z\lesssim 5$ (cite: carnall23; carnall25; glazebrook24; nanayakkara24; belli24; slob24; setton24; degraaff25; siegel25); however, most of these objects have yet to be observed in cold gas with ALMA.

In this Letter, we present ALMA observations of the molecular gas contents of five young post-starburst galaxies at $z\sim1.4$. This work is enabled by ultradeep Keck/LRIS+MOSFIRE observations which allow us to precisely confirm spectroscopic redshifts and young post-quenching ages in our sample. We find that four of these young quiescent galaxies at $z\sim1.4$ are undetected. We significantly detect one object, which is part of an ongoing major merger of two massive post-starburst galaxies. These results suggest that major mergers may play a key role in triggering quenching while retaining molecular gas at these early cosmic times.

Throughout this Letter, we assume a cosmology of $\Omega_m = 0.3$, $\Omega_\Lambda = 0.7$, and $h = 0.7$; we quote AB magnitudes.

# Data & Methods

The galaxy sample was drawn from the Heavy Metal survey (cite: kriek24), which obtained ultra-deep spectra of 21 quiescent galaxies at $z\sim1.4$ and $z\sim2.1$ with LRIS and MOSFIRE on the Keck I Telescope. The Heavy Metal survey was executed in the COSMOS/UltraVISTA field (cite: mccracken12) and thus deep multiwavelength photometry and high-resolution imaging are also available for all galaxies (cite: muzzin13; scoville07; mowla19). The galaxies span a range in stellar mass of ${\rm log} M_*/M_\odot = 10.8-11.9$. For more details on the survey design, sample selection, observations, data reduction and analysis, stellar population measurements, and sample characteristics, we refer to (cite: kriek24). Additionally, in (cite: beverage23) we present the stellar population ages, chemical compositions, and velocity dispersions for the Heavy Metal quiescent galaxies.

![](uvj_all.pdf)

## ALMA observations

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | RA | Dec | $z_{\rm{spec}}$ | Integration Time | Angular Resolution | Continuum Flux | SdvCO(2–1) | L$^\prime_{\rm{CO(2-1)}}$ | $\log{\rm{M}_{H_2}/\rm{M}_\odot}$ |
|  | \[hh:mm:ss\] | \[dd:mm:ss\] |  | \[s\] | \[$\ensuremath{''}$\] | \[$\mu$Jy\] | Jy km/s | $10^9$K km/s pc$^2$ |  |
| HM1-214340 | 10:00:37.094 | 02.34.10.284 | 1.418 | 8437 | 2.418 | $<14.43$ | $0.05\pm0.01$ | $1.38 \pm 0.28$ | $9.74 \pm 0.09$ |
| HM2-23351 | 10:00:48.4350 | 01.43.24.740 | 1.421 | 5625 | 2.436 | $<18.00$ | $<0.04$ | $<0.95$ | $<9.58$ |
| HM2-25702 | 10:00:49.197 | 01.45.27.470 | 1.419 | 8437 | 1.536 | $<18.91$ | $<0.06$ | $<1.55$ | $<9.79$ |
| HM2-213947 | 10:00:50.683 | 02.33.55.368 | 1.397 | 8346 | 1.523 | $<19.29$ | $<0.04$ | $<1.02$ | $<9.61$ |
| HM1-217249 | 10:00:45.622 | 02.36.19.297 | 1.377 | 7530 | 1.433 | $<18.62$ | $<0.10$ | $<2.55$ | $<10.01$ |

: Properties of the ALMA observations

Table notes: Upper limits for the undetected sources are 3$\sigma$, and assume an 800km s$^{-1}$ line width.

To understand the role of molecular gas in the quenching of star formation, we observed the five youngest $z\sim1.4$ quiescent galaxies from the HeavyMetal survey with ALMA. These galaxies were selected for ALMA observations by their rest-frame UVJ colors, as shown in Figure [1](#fig:1) (cite: williams09; whitaker12_psb; belli19). The galaxies have stellar masses around $\sim 10^{11} M_\odot$ and show multiple detected stellar absorption lines in their spectra. They all have wavelength coverage of the H$\alpha$ emission line, from which we derived (limits on) their star formation rates, as shown in Table 3 of (cite: kriek24).

For all five galaxies we targeted CO(2–1) in ALMA Band 3 as part of 2019.1.01286.S (PI Kriek). Observations were made in three ${\sim}80$-minute blocks, with total integration times ranging from 1.5-2.3hr, and angular resolution $\sim1.4-2.4"$ as shown in Table [\[table:alma\]](#table:alma). Data were reduced using the standard ALMA reduction pipeline.

We created $\sim2$mm continuum images using the full bandwidth of our observations (excluding the 500 km s$^{-1}$ around the CO(2-1) line). No continuum emission was detected in any of our primary targets, either at the naturally-weighted image or in a UV-tapered image (3$\sigma$ limiting fluxes $\lesssim20\mu$Jy; see Table [\[table:alma\]](#table:alma)). These continuum nondetections are consistent with the low ongoing SFRs inferred from H$\alpha$ by (cite: kriek24).

We extract CO(2-1) spectra for all targets at an effective velocity resolution of $\sim$200 km s$^{-1}$. We detect CO(2-1) emission at $\sim5\sigma$ in HM1-214340; no other targets are detected. For the four undetected sources, we extract spectra using CASA’s `imfit` task, fixing the centroid to the phase center and the size to 2". Following (cite: bezanson22), we conservatively estimate the upper limit on the CO(2-1) line flux using a 800 km s$^{-1}$ channel and report values in Table [\[table:alma\]](#table:alma). While HM1-214340 is clearly detected, we do not observe any evidence for velocity gradients or resolved structure at the depth and resolution of our observations. Therefore, we first fit for the source position and size in a single $\sim$1000 km s$^{-1}$ channel, then fix the position and size in `imfit` to extract a spectrum at $\sim$200 km s$^{-1}$ velocity resolution, allowing only the intensity to vary channel-to-channel. We fit a single gaussian to the spectrum to find the integrated CO(2-1) line flux and its uncertainty. For all objects we convert (limits on) CO(2-1) line flux to molecular gas mass assuming thermalized emission (cite: combes07; dannerbauer09; young11) and a Milky Way-like $\alpha_{CO}=4.0$ (see (cite: bolatto13) and references therein, as well as discussions in (cite: bezanson22) and (cite: spilker22)).

## Spectral modeling

One of our goals is to test whether the correlation between gas mass and time since quenching identified in (cite: bezanson22) (see also (cite: french18)) holds at higher redshift. This test requires that we calculate galaxy ages that are directly comparable to those used by (cite: bezanson22), which use the `Prospector` modeling framework described in detail in (cite: suess22).

We use `Prospector` v2 (cite: johnson20) to simultaneously fit UltraVISTA photometry (cite: muzzin13) and Keck/LRIS-R, Keck/MOSFIRE-J, and Keck/MOSFIRE-H spectroscopy (cite: kriek24). We calibrate each spectrum separately using a fifth-order polynomial. We adopt a 5% error floor for all photometric data points. Our model assumes a (cite: chabrier03) IMF, the (cite: kriek13) dust attenuation law with free dust index and normalization (with young stars fixed to be twice as attenuated as old stars), and the non-parametric post-starburst star-formation history from (cite: suess22). We include nebular emission, tying the gas-phase metallicity to the stellar metallicity and treating the ionization parameter as a free parameter. All parameters use uniform priors, except for stellar metallicity, which follows a prior approximating the stellar mass–metallicity relation of (cite: gallazzi05). We generate stellar populations using FSPS (cite: conroy09; conroy10), adopting the MILES spectral library (cite: falcon11) and MIST isochrones (cite: dotter16; choi16), computed with MESA (cite: paxton11). Posterior distributions are sampled using the dynamic nested sampling algorithm implemented in `dynesty` (cite: speagle20).

# Results

![](hm_detection.png)

We significantly detect ($\sim5\sigma$) molecular gas in one of our five primary targets, HM1-214340. Figure [2](#fig:detection) shows the ALMA CO spectrum and moment-0 map as well as the best-fit `Prospector` model to the photometry and Keck spectroscopy. Remarkably, our Keck observations serendipitously obtained a spectrum of UVISTA-214345, offset just $\sim1.76\ensuremath{''}$ ($\sim15$ kpc) to the west of HM1-214340. The combination of the UltraVista photometry and Keck spectroscopy confirm that *both* HM1-214340 and UVISTA-214345 are massive ($10^{11.0}$ and $10^{11.1}M_\odot$) post-starburst galaxies at very similar redshifts: at $z=1.418$ and $z=1.421$, the two systems are separated by just $\sim300$km/s. At the depth of existing HST/F814W and F160W imaging, no tidal features or significant asymmetries are present; however, as discussed in more detail below, there are several small offset clumps in the F814W image that may be associated with the system. Altogether, the imaging suggests that HM1-214340 and UVISTA-214345 are in the early stages of a near 1:1 major galaxy merger: they may or may not have had one or more close passes, but have not yet reached coalescence. No 2mm continuum emission is detected from the system at the depth of our observations.

While the angular resolution of the ALMA data ($\sim2.4"$; Table [\[table:alma\]](#table:alma)) is larger than the offset between the two galaxies, the data are consistent with the western source UVISTA-214345 being the primary source of the CO flux. We first fit a single 2D gaussian to the moment-0 map of the CO flux, allowing all fit parameters including the position to be free. The best-fit CO position is (10:00:36.99, +02:34:10.0) with $\sim0.5\ensuremath{''}$ uncertainty, consistent with the position of UVISTA-214345. As discussed in Section [2.1](#sec:alma), the CO emission is consistent with a point source at the resolution of our data. We then model the CO flux with two 2D gaussians, one fixed to the position of UVISTA-214345 and one fixed to the position of HM1-214340, fixing each gaussian to the size and position angle of the clean beam and leaving only the amplitude of each component free. In this two component fit, we find the best-fit flux for UVISTA-214345 is $0.105\pm0.021$ Jy km s$^{-1}$ and the best-fit flux for HM1-214340 is $0.031\pm0.021$ Jy km s$^{-1}$. We note that the sum of these two fluxes is in good agreement with the flux in the single-component fit. This fit indicates that $\gtrsim80\%$ of the CO flux is likely originating from UVISTA-214345, while HM1-214340 could contribute up to $\sim25\%$ of the CO flux but is not significantly detected. We additionally note that the HST/F814W imaging, shown in the bottom right of Figure [2](#fig:detection), shows several small offset clumps to the N/NW of both HM1-214340 and UVISTA-214345. These clumps are not visible in the HST/F160W imaging, which could either indicate that the clumps are relatively blue and associated with recent star formation, at a different redshift than our target system, or simply too faint for the shallow F160W imaging. While it is also possible the CO emission is partially associated with one of these clumps, the likeliest solution is that the CO emission is primarily coming from UVISTA-214345. Table [\[table:alma\]](#table:alma) reports the CO line flux for the HM1-214340 / UVISTA-214345 system from the single-component fit above. This line flux corresponds to $10^{9.74}M_\odot$ of molecular gas, or a gas fraction of $\sim4$%.

![](hm_nondetection.pdf)

Our other four primary targets are not detected in either CO(2-1) or 2mm continuum, as shown in Figure [3](#fig:nondetections). This allows us to place $3\sigma$ upper limits on their molecular gas mass of $\lesssim10^{9.5-10.0}M_\odot$ (see Table [\[table:alma\]](#table:alma)). We note that while our primary targets HM2-213947 and HM1-217249 are not detected, both have nearby neighbors that are significantly detected in CO(2-1), as shown in the right columns of Figure [3](#fig:nondetections). In the HM2-213947 cube we serendipitously detect UVISTA-214044 at $z\sim1.4$ and a projected separation of $\sim30$kpc; in the HM1-217249 cube we serendipitously detect 217299 at $z\sim1.38$ and a projected separation of $\sim70$kpc. Given the similar redshifts and close on-sky separations of these gas-rich galaxies from our primary targets, we infer that they are likely part of close pairs (with larger separations than the HM1-214340/UVISTA-214345 system) or the same overdense environment as our primary targets.

![](mgas_tq.pdf)

In Figure [4](#fig:analysis), we place our sample in the context of existing observations of gas in quiescent galaxies at $z>0.5$. The left panel shows star formation rate as a function of molecular gas mass for all $z>1$ quiescent galaxies with molecular gas measurements from (cite: williams21; belli21; zanella23; sargent15). Objects with detected gas are outlined in black to differentiate them from upper limits. We note that we associate our CO(2-1) detection with UVISTA-214345 (see Section [3](#sec:results)), and place HM1-214340 at the 3$\sigma$ upper limit implied by our two-component modeling. Our detection has an inferred depletion time $\sim1$Gyr, in good agreement with the bulk of the PHIBSS sample shown in grey contours (cite: tacconi13; freundlich19). Our nondetected galaxies have upper limits on their depletion times, consistent with long depletion times up to $10-100$Gyr.

The right panel of Figure [4](#fig:analysis) shows molecular gas mass as a function of time since quenching (cite: suess22). Galaxies from the SQuIGG$\vec{L}$E survey (cite: suess22_squiggle; bezanson22) at $z\sim0.7$ are shown in yellow, while our sample at $z\sim1.4$ is shown in red. Again, we outline all gas detections in black. Interestingly, the `Prospector` fits yield uniformly older $t_{\rm{quench}}$ ages for HeavyMetal than for SQuIGG$\vec{L}$E, despite the fact that the UVJ colors of the two samples are consistent (Fig [1](#fig:1)), indicating similar $t_{50}$ ages. While the SQuIGG$\vec{L}$E sample shows a clear trend that gas-rich galaxies have $t_{\rm{quench}}\lesssim150$ Myr and gas-poor galaxies have $t_{\rm{quench}}\gtrsim150$ Myr, all galaxies in our HeavyMetal sample have $t_{\rm{quench}}\gtrsim500$ Myr. No trend with age is apparent in the HeavyMetal sample: the detected system has similar $t_{\rm{quench}}$ as our non-detected systems.

# Discussion & Conclusions

In this Letter, we observed CO(2-1) as a tracer of molecular gas in five $z\sim1.4$ post-starburst galaxies with ultradeep spectroscopy from the HeavyMetal program. One of the five targets was detected, with an inferred molecular gas mass of $10^{9.74}M_\odot$; the other four targets were undetected in both CO(2-1) line emission and 2mm continuum. Our detected target HM1-214340 is in a close pair with UVISTA-214345, which we spectroscopically confirm to be a similarly-massive post-starburst galaxy at very similar redshift ($\Delta z=0.003$). No clear tidal features are detected and the galaxies have a projected separation of just $\sim15$kpc, implying that the two galaxies may be in the early stages of a major merger event. For two galaxies that were undetected in CO(2-1), HM2-213947 and HM1-217249, our ALMA data spectroscopically confirm nearby neighbors to both objects, with projected separations of $\sim30$ and $\sim70$ kpc, respectively. The remaining two undetected galaxies, HM2-23351 and HM2-25702, appear isolated in our ALMA cubes, though we note that the large number of massive quiescent galaxies in the HeavyMetal survey at $z\sim1.4$ indicates that all of the galaxies in this paper may preferentially live in an overdense environment.

The strong correlation between molecular gas mass and post-burst age observed both at $z\sim0$ (cite: french18) and $z\sim0.7$ (cite: bezanson22) is not clearly reproduced in our $z\sim1.4$ sample. While our four non-detections are consistent with the lower-redshift trend – galaxies with $t_{\rm{quench}}\gtrsim150$Myr lack substantial gas reservoirs – our detected system is an outlier: a relatively older system ($t_{\rm{quench}}\sim600$Myr) that retains $\sim10^{9.7}~M_\odot$ of molecular gas. Interestingly, recent work directly studying the HI (not CO) reservoirs of low-redshift post-starburst galaxies finds no significant trend between post-burst age and gas mass (cite: ellison25). Observations at a wider age range, particularly probing the youngest quiescent galaxies, are required to determine whether a trend between age and molecular gas mass persists at $z\gtrsim1$. Our detection of gas in an older system may also point to a distinct physical driver governing gas survival: perhaps *mergers*, not post-burst age, are the most important driver of whether a quenched galaxy is able to retain molecular gas. Merger signatures are more common for younger post-starburst galaxies (cite: verrico23; ellison24), and this correlation could partially explain the gas-age trend observed at low redshift.

In broad brush strokes, it is perhaps unsurprising that major mergers could play a key role in quenching and the retention of molecular gas in quiescent galaxies at $z\sim1.4$. Simulations have long suggested that mergers and quenching could be causally related, typically because mergers in the simulations are able to trigger enhanced star formation, black hole accretion, and subsequent AGN feedback and removal of molecular gas (cite: springel05; hopkins08; lotz21). Observations have largely corroborated this picture: post-starburst galaxies have high rates of disturbed morphologies indicating recent mergers (cite: pawlik18; sazonova21; wilkinson22; ellison22; verrico23; wu23). However, the details of the HM1-214340/UVISTA-214345 system differ from this classical picture: we observe a close pair where both galaxies have already quenched, not a single post-coalescence quenched remnant. This suppression of star formation in a close pair is in contrast with previous studies that typically find star-formation is *enhanced* in the close pair stage (cite: barton2000; patton13; ferreira25), with post-starburst signatures peaking $\sim500$Myr after coalescence (cite: ellison24).

Our gas-rich post-starburst pair may instead represent a system that already experienced first passage and an associated starburst before the time of observation, consistent with our modeled SFH where both galaxies experienced a recent starburst which ended ${\sim}500-600$Myr ago (Fig [4](#fig:analysis)), and the current ${\sim}15$ kpc on-sky separation. In this picture, turbulence (cite: vandevoort18; smercina22; spilker22) may have temporarily prevented the molecular gas in the system from forming stars, leading to both post-starburst stellar populations and detectable CO. While stellar feedback from the starburst may also have played a role in decreasing star formation efficiency in this system, it typically acts on shorter timescales (see, e.g., discussion in (cite: french21)). As the merger progresses, star formation may re-ignite and consume the remaining molecular gas, eventually leading to a gas-poor post-starburst remnant as in (cite: ellison24), or perhaps the merger will remove the molecular gas from the system and prevent further star formation at all (cite: spilker22). However, we cannot rule out the possibility that the process(es) that quenched HM1-214340 and UVISTA-214345 are entirely unrelated to their close separation.

Our spectroscopic analysis of these galaxies emphasizes discrepancies in different age indicators used for quiescent galaxies. Figure [1](#fig:1) shows that the SQuIGG$\vec{L}$E and HeavyMetal samples have broadly consistent UVJ colors. Previous work indicated that these similar UVJ colors imply they have similar light-weighted ages (cite: whitaker12_psb; belli19; cheng25). However, modeling the spectra with `Prospector` yields systematically older mass-weighted post-burst ages (cite: suess22) for the HeavyMetal sample than the SQuIGG$\vec{L}$E sample. The difference between the average $t_{\rm{quench}}$ values for SQuIGG$\vec{L}$E and HeavyMetal ($\sim400$Myr) is significantly larger than the typical error bars on the ages ($\lesssim100$Myr). A detailed comparison of the spectra suggests that this difference in age between the two samples is reasonable: typical SQuIGG$\vec{L}$E spectra (cite: suess22_squiggle) have larger asymmetries between their calcium H & K lines than our HeavyMetal sample, indicating younger ages because the calcium K line is blended with a deeper Balmer absorption feature. This discrepancy between UVJ color-based ages, $t_{50}$, and `Prospector`-inferred ages, $t_{\rm{quench}}$, may arise from differences in the SFHs of the two samples: SQuIGG$\vec{L}$E galaxies are at lower redshift, and have a combination of both young and old stars (cite: suess22_squiggle). The presence of these older stars reddens the $V-J$ colors and increases $t_{50}$. Meanwhile, the HeavyMetal galaxies are at higher redshifts and have a smaller fraction of old stars, making their $t_{\rm{50}}$ younger for the same $t_{\rm{quench}}$. But even at fixed redshift, UVJ $t_{50}$ and `Prospector` $t_{\rm{quench}}$ can differ: UVISTA-214345 has a younger $t_{\rm{quench}}$ than HM1-214340 (Fig [4](#fig:analysis)) but is located further up the UVJ quiescent sequence (Fig [1](#fig:1)) nominally indicating older $t_{50}$. In this case, the UVJ colors are likely reddened by moderate dust obscuration: `Prospector` indicates UVISTA-214345 has A$_v\sim0.4$ mag, while HM1-214340 has just A$_v\sim0.07$ mag. If dusty post-starburst galaxies are more common at higher redshift (cite: setton24), this may suggest that UVJ location alone is an imprecise age indicator for high-redshift quiescent galaxies (cite: cheng25; antwi-danso23). While differences between $t_{50}$ and $t_{\rm{quench}}$ are not necessarily unexpected, the fact that they yield wholly different conclusions — either the HeavyMetal galaxies are the same age as SQuIGG$\vec{L}$E galaxies, or they are systematically older — suggests that caution and careful methodology are required when computing and comparing the ages of quiescent galaxy samples, especially across different redshift ranges.

Our observations increase the total number of molecular gas measurements in quiescent galaxies at $z>1$ by a factor of $\sim$1.5 and emphasize the diversity of gas contents in these quenched systems; however, the physical mechanisms which quenched these galaxies and allow some but not all of them to retain gas remain unclear. While higher-resolution ALMA imaging that could pinpoint the spatial distribution of the molecular gas is likely out of reach for faint systems like HM1-214340/UVISTA-214345, deeper imaging with HST or JWST may reveal low surface-brightness tidal features and allow for a more extensive characterization of the merging system. Future observations of a larger sample of post-starburst galaxies may also allow us to disentangle the roles of merger history, environment, and internal feedback in the quenching process at cosmic noon. JWST spectroscopy offers a transformative path forward in terms of sample selection: while the HeavyMetal survey required nearly 100hr on-sky with Keck/MOSFIRE+LRIS to obtain ultradeep spectra of 20 massive quiescent galaxies, JWST/NIRSpec surveys like SUSPENSE (cite: slob24) can achieve similar multiplexing and higher SNR in dramatically shorter integration times of $\sim16$hrs, while surveys like EXCELS (cite: carnall24) extend our redshift lever arm to the beginning of the quenching epoch. These JWST/NIRSpec data will enable robust spectroscopic confirmation and age-dating of larger samples of post-starburst galaxies. If paired with additional deep ALMA observations, these data could unlock the ability to trace how molecular gas content evolves with time, environment, and merger history across cosmic noon.

# Acknowledgments

KAS, JSS, and VRD gratefully acknowledge support from NSF-AAG#2407954 and 2407955, and NRAO-SOSPA7-016. This paper makes use of the following ALMA data: ADS/JAO.ALMA #2019.1.01286.S, ADS/JAO.ALMA #2016.1.01126.S and ADS/JAO.ALMA #2017.1.01109.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Software

astropy (cite: astropy2013; astropy2018),

Seaborn (cite: waskom17),

natexlab

(ref: antwi-danso23) Antwi-Danso, J., Papovich, C., Leja, J., et al. 2023, ApJ, 943, 166, doi: [`10.3847/1538-4357/aca294`](http://doi.org/10.3847/1538-4357/aca294)

(ref: astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: barton2000) Barton, E. J., Geller, M. J., & Kenyon, S. J. 2000, ApJ, 530, 660, doi: [`10.1086/308392`](http://doi.org/10.1086/308392)

(ref: belli19) Belli, S., Newman, A. B., & Ellis, R. S. 2019, ApJ, 874, 17, doi: [`10.3847/1538-4357/ab07af`](http://doi.org/10.3847/1538-4357/ab07af)

(ref: belli21) Belli, S., Contursi, A., Genzel, R., et al. 2021, ApJL, 909, L11, doi: [`10.3847/2041-8213/abe6a6`](http://doi.org/10.3847/2041-8213/abe6a6)

(ref: belli24) Belli, S., Park, M., Davies, R. L., et al. 2024, Nature, 630, 54, doi: [`10.1038/s41586-024-07412-1`](http://doi.org/10.1038/s41586-024-07412-1)

(ref: beverage23) Beverage, A. G., Kriek, M., Suess, K. A., et al. 2023, arXiv e-prints, arXiv:2312.05307, doi: [`10.48550/arXiv.2312.05307`](http://doi.org/10.48550/arXiv.2312.05307)

(ref: bezanson19) Bezanson, R., Spilker, J., Williams, C. C., et al. 2019, ApJL, 873, L19, doi: [`10.3847/2041-8213/ab0c9c`](http://doi.org/10.3847/2041-8213/ab0c9c)

(ref: bezanson22) Bezanson, R., Spilker, J. S., Suess, K. A., et al. 2022, ApJ, 925, 153, doi: [`10.3847/1538-4357/ac3dfa`](http://doi.org/10.3847/1538-4357/ac3dfa)

(ref: bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: carnall23) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2023, Nature, 619, 716, doi: [`10.1038/s41586-023-06158-6`](http://doi.org/10.1038/s41586-023-06158-6)

(ref: carnall25) Carnall, A. C., Cullen, F., McLure, R. J., et al. 2024a, MNRAS, 534, 325, doi: [`10.1093/mnras/stae2092`](http://doi.org/10.1093/mnras/stae2092)

(ref: carnall24) —. 2024b, MNRAS, 534, 325, doi: [`10.1093/mnras/stae2092`](http://doi.org/10.1093/mnras/stae2092)

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: cheng25) Cheng, C. M., Kriek, M., Beverage, A. G., et al. 2025, arXiv e-prints, arXiv:2505.08858, doi: [`10.48550/arXiv.2505.08858`](http://doi.org/10.48550/arXiv.2505.08858)

(ref: choi16) Choi, J., Dotter, A., Conroy, C., et al. 2016, ApJ, 823, 102, doi: [`10.3847/0004-637X/823/2/102`](http://doi.org/10.3847/0004-637X/823/2/102)

(ref: combes07) Combes, F., Young, L. M., & Bureau, M. 2007, MNRAS, 377, 1795, doi: [`10.1111/j.1365-2966.2007.11759.x`](http://doi.org/10.1111/j.1365-2966.2007.11759.x)

(ref: conroy10) Conroy, C., & Gunn, J. E. 2010, ApJ, 712, 833, doi: [`10.1088/0004-637X/712/2/833`](http://doi.org/10.1088/0004-637X/712/2/833)

(ref: conroy09) Conroy, C., Gunn, J. E., & White, M. 2009, ApJ, 699, 486, doi: [`10.1088/0004-637X/699/1/486`](http://doi.org/10.1088/0004-637X/699/1/486)

(ref: croton06) Croton, D. J., Springel, V., White, S. D. M., et al. 2006, MNRAS, 365, 11, doi: [`10.1111/j.1365-2966.2005.09675.x`](http://doi.org/10.1111/j.1365-2966.2005.09675.x)

(ref: dannerbauer09) Dannerbauer, H., Daddi, E., Riechers, D. A., et al. 2009, ApJL, 698, L178, doi: [`10.1088/0004-637X/698/2/L178`](http://doi.org/10.1088/0004-637X/698/2/L178)

(ref: dave17) Davé, R., Rafieferantsoa, M. H., Thompson, R. J., & Hopkins, P. F. 2017, MNRAS, 467, 115, doi: [`10.1093/mnras/stx108`](http://doi.org/10.1093/mnras/stx108)

(ref: degraaff25) de Graaff, A., Setton, D. J., Brammer, G., et al. 2025, Nature Astronomy, 9, 280, doi: [`10.1038/s41550-024-02424-3`](http://doi.org/10.1038/s41550-024-02424-3)

(ref: dekel06) Dekel, A., & Birnboim, Y. 2006, MNRAS, 368, 2, doi: [`10.1111/j.1365-2966.2006.10145.x`](http://doi.org/10.1111/j.1365-2966.2006.10145.x)

(ref: dotter16) Dotter, A. 2016, ApJS, 222, 8, doi: [`10.3847/0067-0049/222/1/8`](http://doi.org/10.3847/0067-0049/222/1/8)

(ref: ellison24) Ellison, S., Ferreira, L., Wild, V., et al. 2024, The Open Journal of Astrophysics, 7, 121, doi: [`10.33232/001c.127779`](http://doi.org/10.33232/001c.127779)

(ref: ellison22) Ellison, S. L., Wilkinson, S., Woo, J., et al. 2022, MNRAS, 517, L92, doi: [`10.1093/mnrasl/slac109`](http://doi.org/10.1093/mnrasl/slac109)

(ref: ellison25) Ellison, S. L., Huang, Q., Yang, D., et al. 2025, arXiv e-prints, arXiv:2503.03066, doi: [`10.48550/arXiv.2503.03066`](http://doi.org/10.48550/arXiv.2503.03066)

(ref: falcon11) Falcón-Barroso, J., Sánchez-Blázquez, P., Vazdekis, A., et al. 2011, A&A, 532, A95, doi: [`10.1051/0004-6361/201116842`](http://doi.org/10.1051/0004-6361/201116842)

(ref: feldmann17) Feldmann, R., Quataert, E., Hopkins, P. F., Faucher-Giguère, C.-A., & Kereš, D. 2017, MNRAS, 470, 1050, doi: [`10.1093/mnras/stx1120`](http://doi.org/10.1093/mnras/stx1120)

(ref: ferreira25) Ferreira, L., Ellison, S. L., Patton, D. R., et al. 2025, MNRAS, 538, L31, doi: [`10.1093/mnrasl/slaf004`](http://doi.org/10.1093/mnrasl/slaf004)

(ref: french21) French, K. D. 2021, PASP, 133, 072001, doi: [`10.1088/1538-3873/ac0a59`](http://doi.org/10.1088/1538-3873/ac0a59)

(ref: french15) French, K. D., Yang, Y., Zabludoff, A., et al. 2015, ApJ, 801, 1, doi: [`10.1088/0004-637X/801/1/1`](http://doi.org/10.1088/0004-637X/801/1/1)

(ref: french18) French, K. D., Yang, Y., Zabludoff, A. I., & Tremonti, C. A. 2018, ApJ, 862, 2, doi: [`10.3847/1538-4357/aacb2d`](http://doi.org/10.3847/1538-4357/aacb2d)

(ref: freundlich19) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2019, A&A, 622, A105, doi: [`10.1051/0004-6361/201732223`](http://doi.org/10.1051/0004-6361/201732223)

(ref: gallazzi05) Gallazzi, A., Charlot, S., Brinchmann, J., White, S. D. M., & Tremonti, C. A. 2005, MNRAS, 362, 41, doi: [`10.1111/j.1365-2966.2005.09321.x`](http://doi.org/10.1111/j.1365-2966.2005.09321.x)

(ref: glazebrook24) Glazebrook, K., Nanayakkara, T., Schreiber, C., et al. 2024, Nature, 628, 277, doi: [`10.1038/s41586-024-07191-9`](http://doi.org/10.1038/s41586-024-07191-9)

(ref: hopkins08) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356, doi: [`10.1086/524362`](http://doi.org/10.1086/524362)

(ref: hopkins06) Hopkins, P. F., Somerville, R. S., Hernquist, L., et al. 2006, ApJ, 652, 864, doi: [`10.1086/508503`](http://doi.org/10.1086/508503)

(ref: johnson20) Johnson, B. D., Leja, J., Conroy, C., & Speagle, J. S. 2020, arXiv e-prints, arXiv:2012.01426. [`https://arxiv.org/abs/2012.01426`](https://arxiv.org/abs/2012.01426)

(ref: kriek13) Kriek, M., & Conroy, C. 2013, ApJL, 775, L16, doi: [`10.1088/2041-8205/775/1/L16`](http://doi.org/10.1088/2041-8205/775/1/L16)

(ref: kriek24) Kriek, M., Beverage, A. G., Price, S. H., et al. 2024, ApJ, 966, 36, doi: [`10.3847/1538-4357/ad2df9`](http://doi.org/10.3847/1538-4357/ad2df9)

(ref: lotz21) Lotz, M., Dolag, K., Remus, R.-S., & Burkert, A. 2021, MNRAS, 506, 4516, doi: [`10.1093/mnras/stab2037`](http://doi.org/10.1093/mnras/stab2037)

(ref: mccracken12) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156, doi: [`10.1051/0004-6361/201219507`](http://doi.org/10.1051/0004-6361/201219507)

(ref: mowla19) Mowla, L. A., van Dokkum, P., Brammer, G. B., et al. 2019, ApJ, 880, 57, doi: [`10.3847/1538-4357/ab290a`](http://doi.org/10.3847/1538-4357/ab290a)

(ref: muzzin13) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJS, 206, 8, doi: [`10.1088/0067-0049/206/1/8`](http://doi.org/10.1088/0067-0049/206/1/8)

(ref: nanayakkara24) Nanayakkara, T., Glazebrook, K., Jacobs, C., et al. 2024, Scientific Reports, 14, 3724, doi: [`10.1038/s41598-024-52585-4`](http://doi.org/10.1038/s41598-024-52585-4)

(ref: patton13) Patton, D. R., Torrey, P., Ellison, S. L., Mendel, J. T., & Scudder, J. M. 2013, MNRAS, 433, L59, doi: [`10.1093/mnrasl/slt058`](http://doi.org/10.1093/mnrasl/slt058)

(ref: pawlik18) Pawlik, M. M., Taj Aldeen, L., Wild, V., et al. 2018, MNRAS, 477, 1708, doi: [`10.1093/mnras/sty589`](http://doi.org/10.1093/mnras/sty589)

(ref: paxton11) Paxton, B., Bildsten, L., Dotter, A., et al. 2011, ApJS, 192, 3, doi: [`10.1088/0067-0049/192/1/3`](http://doi.org/10.1088/0067-0049/192/1/3)

(ref: sargent15) Sargent, M. T., Daddi, E., Bournaud, F., et al. 2015, ApJL, 806, L20, doi: [`10.1088/2041-8205/806/1/L20`](http://doi.org/10.1088/2041-8205/806/1/L20)

(ref: sazonova21) Sazonova, E., Alatalo, K., Rowlands, K., et al. 2021, ApJ, 919, 134, doi: [`10.3847/1538-4357/ac0f7f`](http://doi.org/10.3847/1538-4357/ac0f7f)

(ref: scoville07) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1, doi: [`10.1086/516585`](http://doi.org/10.1086/516585)

(ref: setton24) Setton, D. J., Khullar, G., Miller, T. B., et al. 2024, ApJ, 974, 145, doi: [`10.3847/1538-4357/ad6a18`](http://doi.org/10.3847/1538-4357/ad6a18)

(ref: siegel25) Siegel, J. C., Setton, D. J., Greene, J. E., et al. 2025, ApJ, 985, 125, doi: [`10.3847/1538-4357/adc7b7`](http://doi.org/10.3847/1538-4357/adc7b7)

(ref: skelton14) Skelton, R. E., Whitaker, K. E., Momcheva, I. G., et al. 2014, ApJS, 214, 24, doi: [`10.1088/0067-0049/214/2/24`](http://doi.org/10.1088/0067-0049/214/2/24)

(ref: slob24) Slob, M., Kriek, M., Beverage, A. G., et al. 2024, ApJ, 973, 131, doi: [`10.3847/1538-4357/ad65ff`](http://doi.org/10.3847/1538-4357/ad65ff)

(ref: smercina22) Smercina, A., Smith, J.-D. T., French, K. D., et al. 2022, ApJ, 929, 154, doi: [`10.3847/1538-4357/ac5d5f`](http://doi.org/10.3847/1538-4357/ac5d5f)

(ref: speagle20) Speagle, J. S. 2020, MNRAS, 493, 3132, doi: [`10.1093/mnras/staa278`](http://doi.org/10.1093/mnras/staa278)

(ref: spilker22) Spilker, J. S., Suess, K. A., Setton, D. J., et al. 2022, ApJL, 936, L11, doi: [`10.3847/2041-8213/ac75ea`](http://doi.org/10.3847/2041-8213/ac75ea)

(ref: springel05) Springel, V., Di Matteo, T., & Hernquist, L. 2005, ApJL, 620, L79, doi: [`10.1086/428772`](http://doi.org/10.1086/428772)

(ref: suess17) Suess, K. A., Bezanson, R., Spilker, J. S., et al. 2017, ApJL, 846, L14, doi: [`10.3847/2041-8213/aa85dc`](http://doi.org/10.3847/2041-8213/aa85dc)

(ref: suess22) Suess, K. A., Leja, J., Johnson, B. D., et al. 2022a, ApJ, 935, 146, doi: [`10.3847/1538-4357/ac82b0`](http://doi.org/10.3847/1538-4357/ac82b0)

(ref: suess22_squiggle) Suess, K. A., Kriek, M., Bezanson, R., et al. 2022b, ApJ, 926, 89, doi: [`10.3847/1538-4357/ac404a`](http://doi.org/10.3847/1538-4357/ac404a)

(ref: tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: vandevoort18) van de Voort, F., Davis, T. A., Matsushita, S., et al. 2018, MNRAS, 476, 122, doi: [`10.1093/mnras/sty228`](http://doi.org/10.1093/mnras/sty228)

(ref: verrico23) Verrico, M. E., Setton, D. J., Bezanson, R., et al. 2023, ApJ, 949, 5, doi: [`10.3847/1538-4357/acc38b`](http://doi.org/10.3847/1538-4357/acc38b)

(ref: waskom17) Waskom, M., Botvinnik, O., O’Kane, D., et al. 2017, Mwaskom/Seaborn: V0.8.1 (September 2017), v0.8.1, Zenodo, Zenodo, doi: [`10.5281/zenodo.883859`](http://doi.org/10.5281/zenodo.883859)

(ref: wellons15) Wellons, S., Torrey, P., Ma, C.-P., et al. 2015, MNRAS, 449, 361, doi: [`10.1093/mnras/stv303`](http://doi.org/10.1093/mnras/stv303)

(ref: whitaker12_psb) Whitaker, K. E., Kriek, M., van Dokkum, P. G., et al. 2012a, ApJ, 745, 179, doi: [`10.1088/0004-637X/745/2/179`](http://doi.org/10.1088/0004-637X/745/2/179)

(ref: whitaker12) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012b, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: wild16) Wild, V., Almaini, O., Dunlop, J., et al. 2016, MNRAS, 463, 832, doi: [`10.1093/mnras/stw1996`](http://doi.org/10.1093/mnras/stw1996)

(ref: wilkinson22) Wilkinson, S., Ellison, S. L., Bottrell, C., et al. 2022, MNRAS, 516, 4354, doi: [`10.1093/mnras/stac1962`](http://doi.org/10.1093/mnras/stac1962)

(ref: williams21) Williams, C. C., Spilker, J. S., Whitaker, K. E., et al. 2021, ApJ, 908, 54, doi: [`10.3847/1538-4357/abcbf6`](http://doi.org/10.3847/1538-4357/abcbf6)

(ref: williams09) Williams, R. J., Quadri, R. F., Franx, M., van Dokkum, P., & Labbé, I. 2009, ApJ, 691, 1879, doi: [`10.1088/0004-637X/691/2/1879`](http://doi.org/10.1088/0004-637X/691/2/1879)

(ref: wu23) Wu, P.-F., Bezanson, R., D’Eugenio, F., et al. 2023, ApJ, 955, 75, doi: [`10.3847/1538-4357/acf0bd`](http://doi.org/10.3847/1538-4357/acf0bd)

(ref: young11) Young, L. M., Bureau, M., Davis, T. A., et al. 2011, MNRAS, 414, 940, doi: [`10.1111/j.1365-2966.2011.18561.x`](http://doi.org/10.1111/j.1365-2966.2011.18561.x)

(ref: zanella23) Zanella, A., Valentino, F., Gallazzi, A., et al. 2023, arXiv e-prints, arXiv:2306.08120, doi: [`10.48550/arXiv.2306.08120`](http://doi.org/10.48550/arXiv.2306.08120)

[^1]: Brinson Prize Fellow

</paper>

Write the methods card for this paper.