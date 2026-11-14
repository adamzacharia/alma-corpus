# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977L..22F\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977L..22F",
 "title": "ALMA Observations of the Gamma-Ray Binary System PSR B1259-63/LS 2883 during the 2024 Periastron Passage",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Fujita, Yutaka",
 "n_authors": 6,
 "arxiv_id": "2411.11950",
 "doi": "10.3847/2041-8213/ad93d1",
 "alma_projects_linked_by_archive": [
  "2017.1.01188.S",
  "2019.1.00320.S",
  "2023.1.00271.S"
 ]
}
```

Paper text:
<paper>
# ALMA observations of the gamma-ray binary system PSR B1259-63/LS 2883 during the 2024 periastron passage

## Abstract

We present observations of the gamma-ray binary PSR B1259-63/LS 2883 with the Atacama Large Millimeter/submillimeter Array (ALMA) at Bands 3 (97 GHz), 6 (233 GHz), and 7 (343 GHz). PSR B1259-63/LS 2883 consists of a pulsar in a highly eccentric orbit around a massive companion star, with the pulsar passing through the circumstellar disk near periastron. Our new data were obtained over several epochs, ranging from -61 to +29 days from the periastron passage in 2024. We report an increase in flux in all bands near the periastron. The significant change in Band 3 flux suggests synchrotron emission from the interaction between the pulsar wind and the stellar wind or disk. The Band 6 flux shows an increase around periastron and a transition from thermal emission from the circumstellar disk to synchrotron emission. The Band 7 observation +24 days after periastron shows a brightening, suggesting that the pulsar’s passage through the disk does not result in its immediate destruction. We discuss the implications of these results for the interaction between the pulsar wind and the circumstellar disk, such as the possible disk expansion after periastron.

# Introduction

Gamma-ray binaries are a rare and intriguing class of high-energy astrophysical systems characterized by strong gamma-ray emission (cite: 2013A&ARv..21...64D). Among these, PSR B1259-63/LS 2883 (hereafter B1259) stands out as a particularly interesting object, consisting of the pulsar PSR B1259-63 in an eccentric orbit around a massive late Oe-type companion star (LS 2883) with an equatorial decretion disk (cite: 2011ApJ...732L..11N). B1259 is located at a distance of $\sim 2.6$ kpc from Earth (cite: 2018MNRAS.479.4849M) and has an orbital period of about 3.4 years, with an eccentricity of 0.87 (cite: 2014MNRAS.437.3255S).

This system provides a unique laboratory for studying the interactions between pulsar winds and stellar environments, as well as the processes governing the acceleration and emission of high-energy particles in binary systems. The most dramatic events in this binary occur near periastron, when the pulsar PSR B1259-63 passes through or near the circumstellar disk of the companion star LS 2883. During and near these passages, complex interactions between the pulsar wind and the stellar environment lead to enhanced high-energy emission across the electromagnetic spectrum, from radio to gamma rays (e.g. (cite: 2021Univ....7..242C), and references therein). No pulsed flux was detected within $t_p\sim \pm 15$ days[^1] (cite: 1996MNRAS.279.1026J). The eclipse of the pulsar during this period is likely due to absorption and severe pulse scattering by the companion star’s disk (cite: 1996MNRAS.279.1026J). This eclipse of the pulsed emission is accompanied by an increase in the unpulsed radio flux, which begins at $t_p\sim -30$ days and reaches a maximum at $t_p\sim -10$ days. After the periastron passage, the flux decreases before climbing to a second peak at $t_p\sim +20$ days (cite: 1999MNRAS.302..277J; 2005MNRAS.358.1069J). We note that the radio light curve is highly variable from cycle to cycle. For example, the timing of the flux peaks and the rate of flux decline after the second peak change at each periastron passage (Figure 1 in (cite: 2021Univ....7..242C)).

Previous studies have extensively investigated the behavior of B1259 at various wavelengths, particularly focusing on the low-frequency ($\lesssim 10$ GHz) radio, X-ray and gamma-ray regimes (cite: 1996MNRAS.279.1026J; 2005A&A...442....1A; 2006MNRAS.367.1201C; 2009ApJ...698..911U; 2011ApJ...736L..11A; 2021Univ....7..472C; 2024MNRAS.528.5231C; 2024A&A...687A.219H). However, observations at millimeter and submillimeter wavelengths ($\sim 100$–300 GHz) have been comparatively limited.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Date | Day | Band | Freq.$^{\rm a}$ | $N_{\rm ant}^{\rm b}$ | $T_{\rm on}^{\rm c}$ | Bandpass/flux$^{\rm d}$ | Gain$^{\rm e}$ | Beam shape | PA$^{\rm f}$ | Image rms | Observed flux |
|  | (from $t_p$) |  | (GHz) |  | (min) |  |  | (arcsec) | (deg) | ($\rm\mu Jy\: bm^{-1}$) | (mJy) |
| 30-Apr | -61 | 3 | 97 | 44 | 6 | J1427-4206 | J1308-6707 | $2.0\times 1.7$ | 61 | 29 | $0.32\pm 0.06$ |
| 30-Apr | -61 | 6 | 233 | 44 | 5 | J1427-4206 | J1254-6111 | $0.86\times 0.81$ | 42 | 68 | $0.93\pm 0.18$ |
| 4-May | -57 | 7 | 343 | 42 | 5 | J1617-5848 | J1308-6707 | $0.57\times 0.50$ | 46 | 122 | $1.60\pm 0.27$ |
| 30-May | -31 | 6 | 233 | 45 | 5 | J1427-4206 | J1308-6707 | $0.41\times 0.30$ | -16 | 38 | $0.72\times 0.08$ |
| 2-Jun | -28 | 3 | 97 | 41 | 5 | J1617-5848 | J1308-6707 | $0.92\times 0.54$ | 43 | 32 | $0.26\pm 0.06$ |
| 29-Jun | -1 | 3 | 97 | 45 | 6 | J1617-5848 | J1308-6707 | $0.48\times 0.39$ | -31 | 39 | $3.17\pm 0.20$ |
| 29-Jun | -1 | 6 | 233 | 45 | 5 | J1617-5848 | J1308-6707 | $0.18\times 0.16$ | -19 | 48 | $2.48\pm 0.23$ |
| 24-Jul | +24 | 7 | 343 | 41 | 5 | J1617-5848 | J1308-6707 | $0.16\times 0.11$ | -11 | 130 | $3.11\pm 0.54$ |
| 29-Jul | +29 | 3 | 97 | 42 | 6 | J1427-4206 | J1308-6707 | $0.78\times 0.59$ | -23 | 31 | $1.34\pm 0.10$ |
| 29-Jul | +29 | 6 | 233 | 42 | 5 | J1427-4206 | J1308-6707 | $0.35\times 0.27$ | -31 | 44 | $1.89\pm 0.15$ |

: Summary of ALMA observations

Table notes: $^{\rm a}$Center frequency, $^{\rm b}$Number of antennas used for observation, $^{\rm c}$Total integration time of the target source, $^{\rm d}$Band pass and flux calibrator name, $^{\rm e}$Gain calibrator name, and $^{\rm f}$Beam position angle.

The advent of the Atacama Large Millimeter/submillimeter Array (ALMA) allowed us to study the emission at higher frequencies ($\gtrsim 100$ GHz) with excellent sensitivity. In 2017, we observed the binary in Band 3 (97 GHz) and Band 7 (343 GHz) from $t_p=+69$ to +84 days ((cite: 2019PASJ...71L...3F), hereafter Paper I). We found that the Band 3 flux is identical to an extrapolation of the unpulsed fluxes at lower frequencies, suggesting that the Band 3 emission is synchrotron, as is the low frequency emission. The emission is likely produced by electrons accelerated by pulsar wind shocks generated by the interaction between the pulsar wind and the circumstellar material of the companion star (cite: 2012ApJ...750...70T). In contrast to the Band 3 flux, the Band 7 flux at $t_p=+69$ days is much larger than the extrapolated value. The most plausible explanation is that this emission is thermal (blackbody and/or bremsstrahlung) and comes from the circumstellar disk (Paper I). This disk evidence provides an important clue to the origin of the non-thermal emission from the binary, since the gamma-ray emission can be produced by inverse Compton (IC) scattering of photons from the disk (cite: 2012MNRAS.426.3135V; 2019A&A...627A..87C).

In 2019, we observed the binary with ALMA when the pulsar was close to the apastron ((cite: 2020PASJ...72L...9F), hereafter Paper II) and found that both the Band 3 ($t_p=+771$ days) and 7 ($+776$ days) fluxes had decreased from those in 2017. The Band 3 flux is consistent with the extrapolation of pulsed fluxes at low frequencies. This means that while the unpulsed emission produced by the pulsar-companion star interaction had disappeared, the pulsed emission intrinsic to the pulsar was observed. The decrease in Band 7 flux indicates that the disk is not perfectly stationary, but is evolving even away from periastron.

In this study we present new observations of B1259 in 2024 with ALMA, covering three frequency bands. These observations were aimed at capturing for the first time the behavior of the system around the periastron passage.

# Observations and Data Reduction

We performed observations of B1259 with ALMA around the 2024 periastron passage (June 30). The observations were made in Band 3 (97 GHz), Band 6 (233 GHz), and Band 7 (343 GHz). The ALMA observations used ranged from 41 to 45 antennas, providing beam sizes from $\sim 0.2''$ to $2''$ depending on the frequency band and array configuration (Table [1](#tab:sum)). The total on-source integration time for each observation ranged from 5 to 6 minutes. The data were processed using the Common Astronomy Software Applications (CASA) package version 6.5.4.9 (cite: 2007ASPC..376..127M) and ALMA Pipeline version 2023.1.0.124 in a standard manner. The bandpass and gain calibrators are summarized in Table [1](#tab:sum). The flux scaling was derived on the bandpass calibrator using flux information provided by the Joint ALMA Observatory (JAO). The observing conditions with respect to weather and precipitable water vapor (PWV) were normal in the three bands.

After calibration, we created images for each observation using the CLEAN algorithm within CASA. We employed Briggs weighting with a robust parameter of 0.5, balancing between sensitivity and resolution. The resulting synthesized beam sizes are presented in Table [1](#tab:sum). The image size of B1259 is consistent with a point source and the upper limit is given by the beam sizes.

# Results

## Light Curves

Our ALMA observations of B1259 reveal significant variability in the millimeter and submillimeter emission across different orbital phases and frequency bands. The observed fluxes are listed in Table [1](#tab:sum) and the light curves for the three bands are shown in Figure [1](#fig:LC).

In Band 3 (97 GHz), the flux remains relatively low and constant during the early approach to periastron ($t_p=-61$ and -28 days). However, we observe a dramatic increase in flux as the system approaches periastron, with the emission peaking at $3.17\pm 0.20$ mJy at $t_p= -1$ days. This is a tenfold increase from pre-periastron levels. At $t_p=+29$ days the flux begins to decline, but remains elevated compared to the initial observations, measuring $1.34\pm 0.10$ mJy. The significant flux increase at $t_p\gtrsim -20$ days is similar to that at lower frequencies ($\lesssim 10$ GHz; (cite: 2005MNRAS.358.1069J)), suggesting synchrotron emission from relativistic electrons (cite: 1999ApJ...514L..39B; 2002MNRAS.336.1201C). We note that since the number of our ALMA observations is small, the double peaks found in the light curves for the low frequency radio and X-ray bands (cite: 2021Univ....7..242C), associated with the disk passage of the pulsar at $t_p\sim -10$ and $+20$ days, cannot be discussed for our observations.

The emission at Band 6 (233 GHz) shows a general increase as the system approaches periastron, similar to the trend observed in Band 3 (Figure [1](#fig:LC)). However, the relative amplitude of this increase is less pronounced, with the flux near periastron ($2.48 \pm 0.23$ mJy) being only about 2.7 times higher than the initial measurement ($0.93 \pm 0.18$ mJy at $t_p=-61$ days). Interestingly, the flux at $t_p=-1$ day from periastron ($2.48 \pm 0.23$ mJy) is lower than the corresponding measurement in Band 3 ($3.17 \pm 0.20$ mJy). This inversion of the spectrum suggests a transition in the dominant emission mechanism, from the thermal to the synchrotron emission, around these two frequencies (see Section [3.2](#sec:SED)). The post-periastron measurement at $t_p=+29$ days ($1.89 \pm 0.15$ mJy) shows a slower decay compared to Band 3, remaining at about 76% of the near-periastron value. This behavior hints at a possible contribution from thermal emission from the companion star’s circumstellar disk, which would be expected to vary more slowly than the synchrotron component.

Band 7 observations at 343 GHz provide insights into the system’s higher frequency behavior, despite fewer data points. The pre-periastron measurement at $t_p =-57$ days is higher than the corresponding measurements in Bands 3 and 6. This suggests a positive spectral index ($\alpha>0$), where the index is defined as $S_\nu \propto \nu^{\alpha}$, in the undisturbed state before the pulsar passes the disk. The post-periastron observation at $t_p =+24$ days shows a slight increase in flux to $3.11 \pm 0.54$ mJy.

For reference, we show the results of our 2017 (Paper I) and 2019 (Paper II) observations in Figure [1](#fig:LC), although the flux at a given $t_p$ can vary for each orbital period. While the flux in Band 3 varies significantly during an orbital period, the flux in Band 7 does not,

## Spectral Energy Distributions

To better understand the emission mechanisms at play, we constructed spectral energy distributions (SEDs) for the system at different orbital phases. Figure [2](#fig:spec) shows the SEDs at four key phases: early approach ($t_p =-61$ to -57 days), mid-approach (-31 to -28 days), near-periastron (-1 day), and post-periastron (+24 to +29 days).

When the pulsar is approaching periastron (Figures [2](#fig:spec)(a) and (b)), the spectrum rises with frequency. The fluxes are close to those at $t_p\sim +770$ days (Figure [1](#fig:LC)), suggesting that the Band 3 emission is the pulsed emission from the pulsar (dash-dotted red line in Figure [2](#fig:spec)), while the Band 6 and 7 emissions are the thermal radiation from the circumstellar disk (dashed black lines in Figure [2](#fig:spec); see Paper II).

Near periastron (Figure [2](#fig:spec)(c)), the emission, especially in the lower frequency (Band 3), increases dramatically, causing an inversion in the spectrum between Bands 3 and 6. This suggests the emergence of unpulsed synchrotron emission from electrons accelerated as the pulsar passes through the stellar wind and/or circumstellar disk (Papers I and II). The synchrotron emission appears to outshine the thermal emission at Band 6. However, the spectral index between Bands 3 and 6 is $\alpha\sim -0.3$. The slope is less steep compared to a typical unpulsed synchrotron emission ($\alpha\sim -0.75$; dotted green line in Figure [2](#fig:spec)), which could indicate a contribution of the disk emission to the Band 6 emission.

After periastron (Figure [2](#fig:spec)(d)), the spectrum rises again with frequency, although the absolute fluxes are larger than before periastron (Figures [2](#fig:spec)(a) and (b)). The emission seems to come from the disk again, especially in Bands 6 and 7. However, the spectrum between Bands 3 and 6 is less steep than that between Bands 6 and 7, suggesting that the unpulsed synchrotron emission may contribute to the Band 3 emission (dotted green line).

# Discussion

Our multi-band ALMA observations of B1259 reveal a complex and dynamic picture of the binary system’s millimeter and submillimeter emission.

The dramatic increase in the Band 3 flux near periastron (Figure [1](#fig:LC)) is strongly suggestive of synchrotron emission from relativistic electrons. This is because the behavior is consistent with observations at lower radio frequencies (cite: 2002MNRAS.336.1201C; 2005MNRAS.358.1069J). As the pulsar approaches periastron, it encounters increasingly dense regions of the stellar wind and/or circumstellar disk. The collision between the fast pulsar wind and the slower, denser stellar material creates a shock front where particles can be accelerated to relativistic energies (cite: 1997ApJ...477..439T). The strength of this interaction, and consequently the intensity of the synchrotron emission, peaks near periastron when the pulsar is closest to or possibly passing through the densest part of the disk. However, in detail the Band 3 flux at $t_p= +29$ days is smaller than that at $t_p=-1$ days, while they are comparable at lower frequencies (cite: 2021Univ....7..242C). Moreover, the X-ray emission, which is also considered to be synchrotron radiation, is much stronger at $t_p\sim +29$ days than at periastron (cite: 2021Univ....7..242C). This suggests that there are multiple electron components such as weakly and strongly shocked electrons (cite: 2020MNRAS.497..648C). The clumpiness of the stellar wind may also affect the synchrotron radiation (cite: 2020MNRAS.497..648C), although the details are beyond the scope of this study.

While the Band 3 observations are dominated by synchrotron emission, the positive slope $\alpha>0$ spectra at higher frequencies (Bands 6 and 7 in Figures [2](#fig:spec)(a), (b), and (d)) reveal a significant contribution from thermal emission from the companion’s circumstellar disk. The persistence and even enhancement of the emission at Band 7 after periastron passage (Figure [1](#fig:LC)) suggests that the circumstellar disk remains largely intact despite the pulsar’s close approach. This finding is consistent with hydrodynamical simulations, which predict that the disk may be perturbed but not completely disrupted by the pulsar’s passage (cite: 2011PASJ...63..893O). In fact, a comparison with the thermal emission model of (cite: 2011MNRAS.412.1721V) shows that the disk size is $\sim 20$–$30\: R_\star$, where $R_\star$ is the radius of the companion, well before periastron (Figure [2](#fig:spec)(a)), while it is $\sim 40\: R_\star$ at $t_p\sim +24$–29 days (Figure [2](#fig:spec)(d)). Note that the latter size is comparable to the binary separation at that epoch.

The observed increase in Band 7 flux after periastron could be due to disk expansion. (cite: 2021PASJ...73..545K) observed the variability of B1259 in the near infrared (NIR) bands with the IRSF (InfraRed Survey Facility) 1.4 m telescope. The observations were mainly performed for about a month around the periastron passages of 2010 and 2014. The NIR luminosity change in (cite: 2021PASJ...73..545K) is thought to be the result of the disk being stretched by the tidal interaction, but the resulting brightening is only $\lesssim 0.1$ mag ($\lesssim 10$%). In contrast, the change in luminosity at Band 7 was about 200%. The radio emission is emitted from a more outer region of the disk than the NIR emission (e.g. (cite: 2006ApJ...639.1081C); see also (cite: 2013A&ARv..21...69R)) and is therefore more subject to tidal interactions. However, even taking this into account, it would be difficult to explain the 2-fold brightening by tidal interactions alone. In view of these considerations, the brightening in Band 7 may be due to the effect of pulsar winds pushing the disk outward (cite: 2011PASJ...63..893O; 2012ApJ...750...70T).

Previous observations have shown that the H$\alpha$ equivalent width of B1259 also has a large ($\sim 30$%) post-periastron increase: It peaks at $t_p\sim +10$–$+20$ days and starts to decrease at $t_p\sim +30$ days (cite: 2021Univ....7..242C; 2024arXiv241102128C). This behavior is thought to be related to changes in the disk structure not directly associated with the so-called GeV flares (cite: 2016MNRAS.455.3674V; 2024MNRAS.528.5231C). If future Band 7 observations with higher cadence show a similar light curve, it will support the idea that the Band 7 emission comes from the part of the disk where the H$\alpha$ line arises, but is not related to GeV flares. Conversely, if a significant difference is observed between the Band 7 light curve and variations in the H$\alpha$ equivalent width, this will allow us to trace how disturbances in the disk evolve between the radio-emitting and H$\alpha$-emitting regions. Hydrodynamical simulations with radiative transfer could provide valuable insights into the detailed evolution of the disk.

In general, the Band 7 light curve, including the 2017 and 2019 observations (Figure [1](#fig:LC)), shows that the circumstellar disk is relatively stable. This stability is critical for understanding the high-energy phenomena observed in this system over several periastron passages. For example, GeV flares (cite: 2011ApJ...736L..11A) and X-ray ejecta (cite: 2011ApJ...730....2P; 2019ApJ...882...74H) could be associated with a partial destruction of the circumstellar disk. Indeed, GeV flares have been observed (cite: 2024arXiv241102128C) when the Band 7 flux increased (Figure [2](#fig:spec)(d)), which may be caused by the disk expansion with the partial destruction.

# Conclusions

Our multi-band ALMA observations of the gamma-ray binary B1259 have provided new insights into the complex interplay between the pulsar and the circumstellar disk of the companion star. The main results of our study are:

1\. Strong variability in the Band 3 (97 GHz) emission, peaking near periastron, consistent with synchrotron radiation from shock-accelerated electrons in the pulsar-stellar wind interaction.

2\. A more complex behavior in Band 6 (233 GHz), suggesting a transition between synchrotron and thermal emission mechanisms: the synchrotron emission becomes dominant at periastron ($t_p\sim -1$ days), whereas the thermal emission is the dominant emission mechanism at other phases.

3\. The post-periastron brightening in Band 7 (343 GHz) indicates the resilience of the circumstellar disk and possible expansion of the disk.

These results demonstrate the power of millimeter and submillimeter observations to probe the physical conditions and processes in gamma-ray binaries. The persistence of the circumstellar disk, as evidenced by our Band 7 data, has important implications for understanding the long-term stability and nature of the high-energy phenomena in B1259.

We thank the reviewer for helpful comments that improved the paper. We also thank the EA ALMA Regional Center (EA-ARC) for their support. This work was supported by NAOJ ALMA Scientific Research grant Code 2022-21A, and JSPS KAKENHI grant Nos. JP22H01268, JP22H00158, JP22K03624, JP23H04899 (Y.F.), JP21H01137, JP18K03709 (H.N.), and JP22K03686 (N.K.). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01188.S, 2019.1.00320.S, and 2023.1.00271.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan.

natexlab

(ref: 2011ApJ...736L..11A) Abdo, A. A., Ackermann, M., Ajello, M., et al. 2011, ApJL, 736, L11, doi: [`10.1088/2041-8205/736/1/L11`](http://doi.org/10.1088/2041-8205/736/1/L11)

(ref: 2005A&A...442....1A) Aharonian, F., Akhperjanian, A. G., Aye, K. M., et al. 2005, A&A, 442, 1, doi: [`10.1051/0004-6361:20052983`](http://doi.org/10.1051/0004-6361:20052983)

(ref: 1999ApJ...514L..39B) Ball, L., Melatos, A., Johnston, S., & Skjæ Raasen, O. 1999, ApJL, 514, L39, doi: [`10.1086/311928`](http://doi.org/10.1086/311928)

(ref: 2006ApJ...639.1081C) Carciofi, A. C., & Bjorkman, J. E. 2006, ApJ, 639, 1081, doi: [`10.1086/499483`](http://doi.org/10.1086/499483)

(ref: 2021Univ....7..472C) Chang, Z., Zhang, S., Chen, Y.-P., et al. 2021, Universe, 7, 472, doi: [`10.3390/universe7120472`](http://doi.org/10.3390/universe7120472)

(ref: 2019A&A...627A..87C) Chen, A. M., Takata, J., Yi, S. X., Yu, Y. W., & Cheng, K. S. 2019, A&A, 627, A87, doi: [`10.1051/0004-6361/201935166`](http://doi.org/10.1051/0004-6361/201935166)

(ref: 2020MNRAS.497..648C) Chernyakova, M., Malyshev, D., Mc Keague, S., et al. 2020, MNRAS, 497, 648, doi: [`10.1093/mnras/staa1876`](http://doi.org/10.1093/mnras/staa1876)

(ref: 2024MNRAS.528.5231C) Chernyakova, M., Malyshev, D., van Soelen, B., et al. 2024a, MNRAS, 528, 5231, doi: [`10.1093/mnras/stae265`](http://doi.org/10.1093/mnras/stae265)

(ref: 2006MNRAS.367.1201C) Chernyakova, M., Neronov, A., Lutovinov, A., Rodriguez, J., & Johnston, S. 2006, MNRAS, 367, 1201, doi: [`10.1111/j.1365-2966.2005.10039.x`](http://doi.org/10.1111/j.1365-2966.2005.10039.x)

(ref: 2021Univ....7..242C) Chernyakova, M., Malyshev, D., van Soelen, B., et al. 2021, Universe, 7, 242, doi: [`10.3390/universe7070242`](http://doi.org/10.3390/universe7070242)

(ref: 2024arXiv241102128C) —. 2024b, arXiv e-prints, arXiv:2411.02128, doi: [`10.48550/arXiv.2411.02128`](http://doi.org/10.48550/arXiv.2411.02128)

(ref: 2002MNRAS.336.1201C) Connors, T. W., Johnston, S., Manchester, R. N., & McConnell, D. 2002, MNRAS, 336, 1201, doi: [`10.1046/j.1365-8711.2002.05850.x`](http://doi.org/10.1046/j.1365-8711.2002.05850.x)

(ref: 2013A&ARv..21...64D) Dubus, G. 2013, A&ARv, 21, 64, doi: [`10.1007/s00159-013-0064-5`](http://doi.org/10.1007/s00159-013-0064-5)

(ref: 2019PASJ...71L...3F) Fujita, Y., Kawachi, A., Akahori, T., Nagai, H., & Yamaguchi, M. 2019, PASJ, 71, L3 (Papar I), doi: [`10.1093/pasj/psz085`](http://doi.org/10.1093/pasj/psz085)

(ref: 2020PASJ...72L...9F) Fujita, Y., Nagai, H., Akahori, T., Kawachi, A., & Okazaki, A. T. 2020, PASJ, 72, L9 (Papar II), doi: [`10.1093/pasj/psaa067`](http://doi.org/10.1093/pasj/psaa067)

(ref: 2024A&A...687A.219H) H. E. S. S. Collaboration, Aharonian, F., Ait Benkhali, F., et al. 2024, A&A, 687, A219, doi: [`10.1051/0004-6361/202449612`](http://doi.org/10.1051/0004-6361/202449612)

(ref: 2019ApJ...882...74H) Hare, J., Kargaltsev, O., Pavlov, G., & Beniamini, P. 2019, ApJ, 882, 74, doi: [`10.3847/1538-4357/ab3648`](http://doi.org/10.3847/1538-4357/ab3648)

(ref: 2005MNRAS.358.1069J) Johnston, S., Ball, L., Wang, N., & Manchester, R. N. 2005, MNRAS, 358, 1069, doi: [`10.1111/j.1365-2966.2005.08854.x`](http://doi.org/10.1111/j.1365-2966.2005.08854.x)

(ref: 1996MNRAS.279.1026J) Johnston, S., Manchester, R. N., Lyne, A. G., et al. 1996, MNRAS, 279, 1026, doi: [`10.1093/mnras/279.3.1026`](http://doi.org/10.1093/mnras/279.3.1026)

(ref: 1999MNRAS.302..277J) Johnston, S., Manchester, R. N., McConnell, D., & Campbell-Wilson, D. 1999, MNRAS, 302, 277, doi: [`10.1046/j.1365-8711.1999.02133.x`](http://doi.org/10.1046/j.1365-8711.1999.02133.x)

(ref: 2021PASJ...73..545K) Kawachi, A., Moritani, Y., Okazaki, A. T., Yoshida, H., & Suzuki, K. 2021, PASJ, 73, 545, doi: [`10.1093/pasj/psab019`](http://doi.org/10.1093/pasj/psab019)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2018MNRAS.479.4849M) Miller-Jones, J. C. A., Deller, A. T., Shannon, R. M., et al. 2018, MNRAS, 479, 4849, doi: [`10.1093/mnras/sty1775`](http://doi.org/10.1093/mnras/sty1775)

(ref: 2011ApJ...732L..11N) Negueruela, I., Ribó, M., Herrero, A., et al. 2011, ApJL, 732, L11, doi: [`10.1088/2041-8205/732/1/L11`](http://doi.org/10.1088/2041-8205/732/1/L11)

(ref: 2011PASJ...63..893O) Okazaki, A. T., Nagataki, S., Naito, T., et al. 2011, PASJ, 63, 893, doi: [`10.1093/pasj/63.4.893`](http://doi.org/10.1093/pasj/63.4.893)

(ref: 2011ApJ...730....2P) Pavlov, G. G., Chang, C., & Kargaltsev, O. 2011, ApJ, 730, 2, doi: [`10.1088/0004-637X/730/1/2`](http://doi.org/10.1088/0004-637X/730/1/2)

(ref: 2013A&ARv..21...69R) Rivinius, T., Carciofi, A. C., & Martayan, C. 2013, A&ARv, 21, 69, doi: [`10.1007/s00159-013-0069-0`](http://doi.org/10.1007/s00159-013-0069-0)

(ref: 2014MNRAS.437.3255S) Shannon, R. M., Johnston, S., & Manchester, R. N. 2014, MNRAS, 437, 3255, doi: [`10.1093/mnras/stt2123`](http://doi.org/10.1093/mnras/stt2123)

(ref: 2012ApJ...750...70T) Takata, J., Okazaki, A. T., Nagataki, S., et al. 2012, ApJ, 750, 70, doi: [`10.1088/0004-637X/750/1/70`](http://doi.org/10.1088/0004-637X/750/1/70)

(ref: 1997ApJ...477..439T) Tavani, M., & Arons, J. 1997, ApJ, 477, 439, doi: [`10.1086/303676`](http://doi.org/10.1086/303676)

(ref: 2009ApJ...698..911U) Uchiyama, Y., Tanaka, T., Takahashi, T., Mori, K., & Nakazawa, K. 2009, ApJ, 698, 911, doi: [`10.1088/0004-637X/698/1/911`](http://doi.org/10.1088/0004-637X/698/1/911)

(ref: 2011MNRAS.412.1721V) van Soelen, B., & Meintjes, P. J. 2011, MNRAS, 412, 1721, doi: [`10.1111/j.1365-2966.2010.18008.x`](http://doi.org/10.1111/j.1365-2966.2010.18008.x)

(ref: 2012MNRAS.426.3135V) van Soelen, B., Meintjes, P. J., Odendaal, A., & Townsend, L. J. 2012, MNRAS, 426, 3135, doi: [`10.1111/j.1365-2966.2012.21870.x`](http://doi.org/10.1111/j.1365-2966.2012.21870.x)

(ref: 2016MNRAS.455.3674V) van Soelen, B., Väisänen, P., Odendaal, A., et al. 2016, MNRAS, 455, 3674, doi: [`10.1093/mnras/stv2576`](http://doi.org/10.1093/mnras/stv2576)

[^1]: We refer to the day of each periastron passage as $t_p=0$ days.

</paper>

Write the methods card for this paper.