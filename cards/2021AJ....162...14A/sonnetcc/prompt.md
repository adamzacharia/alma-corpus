# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021AJ....162...14A\sonnetcc\reply.txt

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
 "bibcode": "2021AJ....162...14A",
 "title": "Precision Millimeter Astrometry of the α Centauri AB System",
 "year": 2021,
 "journal": "The Astronomical Journal",
 "first_author": "Akeson, Rachel",
 "n_authors": 5,
 "arxiv_id": "2104.10086",
 "doi": "10.3847/1538-3881/abfaff",
 "alma_projects_linked_by_archive": [
  "2018.1.00557.S"
 ]
}
```

Paper text:
<paper>
# Precision Millimeter Astrometry of the $\alpha$ Centauri AB System

## Abstract

$\alpha$ Centauri A is the closest solar-type star to the Sun and offers the best opportunity to find and ultimately to characterize an Earth-sized planet located in its Habitable Zone (HZ). Here we describe initial results from an ALMA program to search for planets in the $\alpha$ Cen AB system using differential astrometry at millimeter wavelengths. Our initial results include new absolute astrometric measurements of the proper motion, orbital motion, and parallax of the $\alpha$ Cen system. These lead to an improved knowledge of the physical properties of both $\alpha$ Cen A and B. Our estimates of ALMA’s relative astrometric precision suggest that we will ultimately be sensitive to planets of a few 10s of Earth mass in orbits from 1-3 AU, where stable orbits are thought to exist.

# Introduction

At a distance of 1.34 pc, $\alpha$ Cen A is an ideal target for exoplanet searches and is 2.7 times closer than the next most favorable G star, $\tau$ Ceti. $\alpha$ Cen A’s luminosity of 1.5 L$_\odot$ (cite: Thevenin2002) puts the center of its HZ at a physical separation of 1.2 AU which corresponds to an angular separation of 0.9$''$. $\alpha$ Cen A is thus an attractive target for direct imaging searches for planets using ground or space based observatories (cite: Kasper2019; Beichman2020; Wagner2020). Current precision radial velocity (PRV) observations (cite: Zhao2018) constrain the mass of any planet to be $M\, sin(i)<$ 53 M$_\oplus$ in the Habitable Zone (1.2 AU). Examination of their Figure 6, which includes their estimates for the effects of non-Gaussian noise sources (“red noise") suggests a limit between 50 and 100 M$_\oplus$. This limit applies to the near edge-on, 79$^o$, orientation of the $\alpha$ Cen AB system where dynamical studies indicate the presence of a stable zone $\lesssim$ 2.8 AU (or 2.1$''$) around $\alpha$ Cen A despite the presence of $\alpha$ Cen B (cite: Quarles2016; Holman1999; Quarles2018a; Quarles2018b).

Due to the proximity of the $\alpha$ Cen system, observations by (cite: Liseau2015; Liseau2016) with the Atacama Large Millimeter/submillimeter Array (ALMA) detected both stellar photospheres, allowing a unique opportunity to measure astrometric motion with ALMA. Recently, the first radio astrometric planetary detection was announced by (cite: Curiel2020) with the discovery of a planet around the M dwarf TVLM 513–46546 using the Very Long Baseline Array.

In this paper, we present results from an ALMA observing program designed both to test the astrometric capabilities of ALMA and to make initial measurements of the $\alpha$ Cen AB system. Section [2](#sec:obs) describes our ALMA observations, data reduction, astrometric measurements and the contribution of stellar activity to the astrometric noise. Section [3](#sec:results) includes our determination of the orbital and physical parameters for $\alpha$ Cen A and B, combining our new data with previous observations, and a discussion of future prospects for planet detection. Our conclusions are given in Section [4](#sec:conclusions) and Appendix A provides the ephemeris of $\alpha$ Cen A and B.

# Astrometry with ALMA

## Observations

The properties of $\alpha$ Cen A and B are well known from previous observations. At sub-mm wavelengths, the stellar fluxes range from 10 to 100 mJy (cite: Liseau2016), the angular sizes are 8.5 and 6.0 mas (cite: Kervella2017a), the orbital separation ranges from 2 to 21$''$ and the short term motion on the sky is 0.8 mas per hour. From these parameters and looking to balance the SNR, the angular resolution and the field of view, we selected to observe in band 7. As the astrometric precision scales directly with the angular resolution, observations when ALMA is in configurations with maximum baselines of 2 km or larger are most desirable, which limits the time sampling. Hence, observations were requested in three configurations, one in Fall 2018 and two in Summer 2019. We obtained a series of ALMA observations of $\alpha$ Cen in Cycle 6 between 2018 October and 2019 August at band 7, using the nominal continuum setup of four 1.9 GHz spectral windows at frequencies 336.5, 338.5, 348.5 and 350.5 GHz (Table [1](#tab:obs)). To keep both sources well within the primary beam, we placed the phase center for each 70-min observation at the center of mass of $\alpha$ Cen A and B.

To assist in the determination of systematics in the astrometric measurements, we designed the observations with two levels of repetition. Within a configuration, we requested two observation blocks separated by up to 14 days. Within an observation block, we executed two independently calibrated observations, with little or no time gap in between them. In 2018 October, we obtained only a single observational block, and one of the two observations within this block has issues (see Sec [2.2.1](#AbsA)) and is not included in the astrometric data results. Thus, our final observation set includes nine calibrated observations, from five blocks: one block in configuration 6 (max baseline 2.5 km), two blocks in configuration 8 (max baseline 8 km) and two blocks in configuration 7 (max baseline 3.6 km).

Each observation block consisted of the following: (1) The standard on-line calibrations: pointing, delay offset, and system temperature of each antenna; (2) a 2-min scan at the beginning of each observation of the bright quasar, J1427-4206, with a known flux density; (3) the main science target portion of the observation of about 55 observing cycles, each with an 18-sec scan on the phase calibrator J1452-6502, alternating with a 50-sec scan on $\alpha$ Cen ; (4) within the science portion, five of the $\alpha$ Cen target integrations were replaced by a check source, J1424-6807.

|  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|
| Observation Pair | Maximum | Beam | rms | A int. flux$^{a}$ | B int. flux$^{a}$ |
| Dates | Baseline (km) | (mas) | ($\mu$Jy) | (mJy) | (mJy) |
| 2018 Oct 14$^{b}$ | 2.5 | 160 x 83 | 38 | 20.77$\pm$0.15 | 9.07$\pm$0.15 |
| 2019 July 15-16 | 8.5 | 40 x 25 | 27 | 22.34$\pm$0.058 | 9.71$\pm$0.055 |
| 2019 July 19-20 | 8.5 | 35 x 21 | 30 | 21.19$\pm$0.081 | 9.83$\pm$0.081 |
| 2019 Aug 12-13 | 3.6 | 68 x 57 | 49 | 22.60$\pm$0.066 | 10.59$\pm$0.065 |
| 2019 Aug 25-26 | 3.6 | 69 x 55 | 50 | 26.08$\pm$0.051 | 11.91$\pm$0.051 |

: ALMA Observation Log

Table notes: $^{a}$ Integrated flux uncertainty from fit; does not include absolute flux error $^{b}$ Only one observation block observed in this configuration

## Data Reduction

We used the standard ALMA data calibration for all observations. The amplitude calibration for each antenna/spectral-window channel was determined from the 2-min scan of J1427-4206 and applied to the rest of the observation. The measured antenna/spectral-window scale factor is constant within 5% over the $\sim$hour observation duration. The phase difference between each antenna/spectral-window was essentially constant, and also obtained from the 2-min scan and applied to the entire observation. Thus, the eight data channels (four spectral windows times two polarizations) could be combined to give high SNR for the imaging, self-calibration and position determinations. The phase calibration for $\alpha$ Cen and the check source was obtained in the normal phase referencing method from the antenna-based phase from each of the fifty 18-sec scans on J1452-6502. $\alpha$ Cen and the check source field were then calibrated using the average of the antenna-based phase of J1452-6502 just before and after the relevant scan.

To provide an independent check of the absolute accuracy of these observations, we included five 20-sec scans of the quasar J1424-6807 near $\alpha$ Cen in each epoch as a check source. This quasar is in the International VLBI Service for Geodesy and Astrometry list, and has a celestial position accuracy $<$0.5 mas. Except for the integration time, which was about 3.5% of that of $\alpha$ Cen, the identical check source observation and analysis methods provide an independent confirmation of the absolute precision of the ALMA results.

From this calibrated data, we used the *tclean* program from the *casa* software package (cite: McMullin2007) to produce images for each of the calibrated observations, using the nominal data weighting (weighting=briggs, robust=0). The image size of 2048$\times$2048 pixels, with grid separation 5 mas, covered nearly all of the ALMA primary beam. The clean deconvolution algorithm removed the point spread function associated with the spatial frequency (uv) coverage of the observation. The image resolution varied from 20 mas to 150 mas, depending on the configuration. We derived all astrometric positions from the images; we did not use uv data analysis to obtain the source positions. Using the stellar radii and parallax from (cite: Kervella2017a), the angular diameters of $\alpha$ Cen A and B are 8.5 and 6.0 mas respectively. Thus, the individual photospheres are not resolved in these observations. For the J1424-6807 check source, we analyzed an image size of 512$\times$512 pixels.

The flux for $\alpha$ Cen A and B for each epoch is given in Table [1](#tab:obs). The integrated flux was determined using the *casa* routine *imfit* to fit a Gaussian to each star. The uncertainty reported is the fitting uncertainty and does not include the absolute flux error. As the focus of these observations was astrometry, no primary flux calibration standards were observed, thus the absolute calibration uncertainty is 10-15$\%$. Within this absolute uncertainty, our fluxes agree with those of (cite: Liseau2016).

### Absolute Astrometry

The images made for each one-hour observation of $\alpha$ Cen A and B are on the VLBI J2000.0 International Celestial Reference System (ICRS) because the phase reference calibrator, J1452-6502, and other interferometric parameters used for these ALMA calibrations and reductions are on this frame associated with very distant quasars. The measured positions from each one-hour observation of $\alpha$ Cen A and B are shown in Table [2](#tab:absastrom), as measured using the *casa* routine *jmfit*. The positional change of each science target star due to proper motion and parallax is less than 1 mas in one hour. Each hour-long observation can be combined into an average position with no significant loss of precision in the absolute position.

|  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|
| Date | Start Time | Star | RA | Dec | $\sigma_{\rm RA}$ cos(Dec)$^{a}$ | $\sigma_{\rm Dec}$ |
|  | UT hours |  | deg | deg | arcsec | arcsec |
| 14-Oct-2018 | 13:38:19.0 | A | 219.860763250 | -60.832171539 | 0.0039 | 0.0035 |
|  |  | B | 219.859663542 | -60.830951061 | 0.0040 | 0.0039 |
| 15-Jul-2019 | 23:14:41.3 | A | 219.858859933 | -60.832264944 | 0.0007 | 0.0010 |
|  |  | B | 219.857984904 | -60.830881649 | 0.0007 | 0.0010 |
| 16-Jul-2019 | 01:15:31.1 | A | 219.858854542 | -60.832262378 | 0.0019 | 0.0014 |
|  |  | B | 219.857979000 | -60.830879128 | 0.0018 | 0.0013 |
| 19-Jul-2019 | 23:31:14.5 | A | 219.858829571 | -60.832252293 | 0.0004 | 0.0007 |
|  |  | B | 219.857957646 | -60.830866720 | 0.0004 | 0.0007 |
| 20-Jul-2019 | 01:02:29.9 | A | 219.858827083 | -60.832253354 | 0.0005 | 0.0005 |
|  |  | B | 219.857955246 | -60.830867652 | 0.0006 | 0.0007 |
| 12-Aug-2019 | 23:10:35.2 | A | 219.858667583 | -60.832185858 | 0.0068 | 0.0057 |
|  |  | B | 219.857814792 | -60.830785642 | 0.0071 | 0.0061 |
| 13-Aug-2019 | 00:44:57.6 | A | 219.858669208 | -60.832186997 | 0.0049 | 0.0037 |
|  |  | B | 219.857817458 | -60.830787197 | 0.0047 | 0.0035 |
| 25-Aug-2019 | 23:33:45.5 | A | 219.858615833 | -60.832153722 | 0.0035 | 0.0020 |
|  |  | B | 219.857773917 | -60.830746378 | 0.0043 | 0.0024 |
| 26-Aug-2019 | 20:07:30.6 | A | 219.858613375 | -60.832152358 | 0.0016 | 0.0016 |
|  |  | B | 219.857772625 | -60.830744378 | 0.0018 | 0.0018 |

: Measured positions in IRCS

Table notes: $^{a}$ rms values given in table are the internal measurement uncertainties.

We obtain a further check of the experiment accuracy from analysis of the image position and stability of the check source J1424-6807. For the four highest resolution observations with a beam about 30 mas taken in 2019 July, the average offset of the check source between our measured ALMA position and its International Celestial Reference System (ICRS) position is about 2.5 mas. This displacement varied somewhat with the quality and variability of the atmospheric phase stability over each observation. We note that the angular separation between the check source and the phase calibrator is 4.1 degrees, similar to the 4.5 degrees between $\alpha$ Cen and the phase calibrator.

Extrapolating the absolute astrometric accuracy between the check source and $\alpha$ Cen requires scaling with the peak SNR for each source. The check source is roughly two times brighter than $\alpha$ Cen B, but with only 3.5% of the integration time, J1424-6807 will have a noise level $\sqrt(29)$ higher. Thus the SNR ratio between $\alpha$ Cen B and J1424-6807 is a factor of $\sim$3. In the absence of systematics, the best performance on $\alpha$ Cen would scale to $\sim$0.8 mas. As seen in Table [2](#tab:absastrom) the internal uncertainty for the best observation in 2019 July matches this performance. The final absolute astrometric uncertainty will also include contributions from uncorrected phase noise in the $\alpha$ Cen data. Based on variations in the absolute position of A and B using different calibrations and array sizes, we use a conservative value of 3 mas for the absolute astrometric uncertainty for the higher resolution configurations (2019 July and August) and 6 mas for the lower resolution (2018 October) data when fitting the orbital parameters in Section [3.1](#sec:orbital). Future ALMA observations with good phase calibration on long baselines could provide improved absolute astrometric accuracy of $<1$ mas, with internal uncertainties of 0.1 to 0.2 mas in Band 7.

|           |         |                 |          |         |
|:----------|:--------|:----------------|:---------|:--------|
| Avg Date  | RA meas | RA err cos(Dec) | dec meas | dec err |
| yr        | mas     | mas             | mas      | mas     |
| 2018.7853 | -6.6    | 3.3             | 28.2     | 3.0     |
| 2019.5371 | 6.1     | 1.0             | -6.1     | 1.0     |
| 2019.5480 | 2.3     | 0.4             | 2.5      | 0.6     |
| 2019.6138 | -0.7    | 1.4             | 3.1      | 1.0     |
| 2019.6505 | -2.7    | 2.2             | 3.7      | 1.3     |

: Absolute Position Difference of Star A for five Observation Pairs

An additional estimate of the absolute position accuracy of $\alpha$ Cen A and B can be obtained by the position difference between each of the five observation pairs in the experiment. Table [3](#tab:absdif) shows the RA and declination differences between the two position measurements in each pair, after correction for the proper motion. The $RA meas$ column gives the measured difference between the two observations separated by approximately one hour, and the $RA err$ column gives the uncertainty extrapolated from the image fitting errors given in Table 2. Similar entries are given for the declination. The measured differences are correlated with the tropospheric stability during the observation. The measured position differences between the observation pair positions are generally a factor of 3 larger than that expected from the internal position error based on the fitting of the star on each image alone. A similar scaling is obtained for $\alpha$ Cen B which is not shown. The one anomaly is for the observation on 2018 Oct 14 at 15.1h where both stars A and B declinations disagree between the observation pairs on 2018 Oct 14 at 13.6. This observation is discussed further below.

For the second observation block in October 2018, both $\alpha$ Cen A and B had an unexpected offset of 20 mas, while the check source position repeatability error was less than 4 mas. We continue to investigate this problem, and believe it was caused by an error in the ALMA celestial position tracking system of $\alpha$ Cen. Hence, this observation is not used in our analysis below.

### Differential Astrometry

The angular separation between $\alpha$ Cen A and B can be measured from the image for each of the observation eopchs. Although the image quality and absolute position offsets may differ, the atmospheric distortions act nearly identically on $\alpha$ Cen A and B. Thus, their angular separation is nearly independent of the quality of the image, but with an error consistent with the SNR of each star. An empirical relationship (cite: Monet2010) shows the dependence of astrometric precision, $\sigma$, on the Full Width at Half Maximum, FWHM, of the beam and SNR of the signal: $\sigma\sim$ FWHM/(2$\times$SNR). Our results are consistent with this expectation.

As the radio emission from the two stars is sufficiently bright and compact, we self-calibrate the $\alpha$ Cen data in order to remove most of the residual tropospheric phase errors (cite: Sch80). We used the self-calibration algorithm to improve the $\alpha$ Cen image quality, and the following paragraph describes how the initial model for $\alpha$ Cen assumed for self-calibration makes no significant difference on the A-B angular separation. Figure [1](#fig:ABimage) shows an image of $\alpha$ Cen A and B before and after phase self-calibration, compared with an image obtained with only normal phase referencing, for two observations with different spatial resolution. The improvement in the image quality is shown by the SNR, which increases by factor of $\sim$2 and by the significantly lower residuals. Except for the emission from the two stars, we find no emission in the field of view greater than 0.3% of the emission from $\alpha$ Cen A.

![](ALMA_panels.eps)

Because we obtain significantly improved image quality with self-calibration (Figure [1](#fig:ABimage)), the $\alpha$ Cen A to B separations measured from those images also have more precision and accuracy. To check the impact of the self-calibration, the A to B separation was measured for 3 cases: 1) no self-calibration, 2) self-calibration for A only and 3) self-calibration for A and B. The separations for these three methods agreed to within the uncertainties and Table [4](#tab:diffastrom) contains $\alpha$ Cen A to B separations measured from self-calibrated images for both sources. The angular separation and estimated error (using the casa routine *jmfit*) are given in Table [4](#tab:diffastrom), measured using self-calibrated method (3). The uncertainties in total separation are from the positional fitting and range from 0.3 to 0.6 mas. As absolute position information is not preserved during self-calibration, these data are only used for the A to B separation, not for the absolute positions given in Table [2](#tab:absastrom).

|  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|
| Date (UT) | Time (UT) | Decimal year | E-W separation cos(Dec) | $\sigma_{E-W}$ cos(Dec) | N-S separation | $\sigma_{N-S}$ |
|  | hours |  | arcsec | arcsec | arcsec | arcsec |
| 14-Oct-2018 | 13.6 | 2018.78520 | -1.9310 | 0.0004 | -4.3952 | 0.0003 |
| 15-Jul-2019 | 23.2 | 2019.53697 | -1.5355 | 0.0003 | -4.9799 | 0.0003 |
| 16-Jul-2019 | 01.3 | 2019.53720 | -1.5361 | 0.0005 | -4.9802 | 0.0003 |
| 19-Jul-2019 | 23.5 | 2019.54796 | -1.5295 | 0.0003 | -4.9884 | 0.0003 |
| 20-Jul-2019 | 01.0 | 2019.54813 | -1.5297 | 0.0003 | -4.9884 | 0.0003 |
| 12-Aug-2019 | 23.5 | 2019.61366 | -1.4953 | 0.0003 | -5.0392 | 0.0003 |
| 13-Aug-2019 | 01.0 | 2019.61385 | -1.4945 | 0.0003 | -5.0390 | 0.0003 |
| 25-Aug-2019 | 23.6 | 2019.64934 | -1.4761 | 0.0005 | -5.0662 | 0.0003 |
| 26-Aug-2019 | 20.1 | 2019.65168 | -1.4751 | 0.0003 | -5.0684 | 0.0003 |

: **Relative position of $\alpha$ Cen B with respect to A from ALMA.**

## Astrometric Noise due to Stellar Activity

(cite: Dumusque2018) discusses the effects of stellar variability in the context of PRV for planet detection, where changes in the shapes of spectral lines formed at different heights in stellar photospheres and chromospheres can adversely impact radial velocity precision at the $\sim 1$ m s$^{-1}$ level even for quiescent stars. A similar effect introduces spurious signals in astrometric observations. Time-variable spatial inhomogeneities on the surfaces of stars produce variations in their astrometric positions (cite: Makarov2009). In the astrometric case, the causes of the variability include surface features such as sunspots and active regions, which may appear as fainter or brighter than the surrounding photosphere depending on wavelength. As spots rotate across and then behind the face of the star, the intensity-weighted centroid of the stellar disk will shift.

Appropriate to their age, both $\alpha$ Cen stars are relatively quiescent with an activity index R$^\prime$HK= -5.15 and -4.97 for A and B, respectively (cite: Boro2018; Lisogorskyi2019). Spectroscopic studies and X-ray data (cite: Robrade2016) show $\alpha$ Cen B to be modestly more active than $\alpha$ Cen A, but both are similar in their activity levels to the Sun (cite: Mamajek2008). $\alpha$ Cen B is brighter at X-ray wavelengths (cite: Robrade2016) and shows a stronger chromospheric component (cite: Trigilio2018). Both stars show cyclical variations in X-ray brightness over almost a 20 year span (cite: Robrade2016).

$\alpha$ Cen A and B are strong sources at millimeter and sub-millimeter wavelengths. The spectral energy distribution in Figure [2](#photometry) spans observations from the Spitzer, Herschel, ALMA and the Australia Telescope Compact Array (ATCA) observatories as tabulated in (cite: Liseau2013; Trigilio2018) using ALMA values as updated with an improved calibration model (cite: Liseau2019). To assess the possible impact of variability in the positions of the two stars we first must determine the dominant source of emission at our ALMA wavelength (Band 7; 343 Ghz or 874 $\mu$m). For $\alpha$ Cen A, we fitted the absolute flux densities for a T$_{eff}=$5800 K B-T Settle model (cite: Baraffe2015) using R$_*=1.22R_\odot$ at 1.334 pc (cite: Kervella2017a) to the visible and NIR data listed in SIMBAD and (cite: Engels1981). The fitted “photospheric” component is shown as the red-dashed curve in Fig [2](#photometry) and has a normalization uncertainty of $9$% $(1\sigma)$. To account for the excess obvious at longer wavelengths, we combine the photospheric emission with a simplified representation of free-free chromospheric emission following (cite: Mezger1967) with an optical depth given by:

$$\tau=3.28\times10^{-7}\left(\frac{T_{gas}}{10^4K}\right)^{-1.35}\nu^{-2.1}\times EM$$ and the corresponding flux density $$F\nu=\frac{2 k_B T\nu^2}{c^2} \Omega (1-e^{-\tau})$$

where $\tau$ is the free-free optical depth, $T_{gas}$ is the temperature of the ionized gas, $\nu$ the frequency, $EM$ the Emission Measure in pc cm$^{-6}$, $k_B$ is the Boltzmann constant, and $\Omega$ the solid angle of the star.

We fit the free-free emission from $\alpha$ Cen A with a two parameter model, solving for gas temperature, T$_{gas}$, and emission measure, $EM$. The combination of photosphere (red-dashed line in Figure [2](#photometry)) and free-free (blue-dashed line) emission provides a good fit to the data (solid black line) with $T_{gas}$=5100$\pm$650 K and $EM=3.0\pm 0.4\times10^{10}$ pc cm$^{-6}$. The derived T$_{gas}$ and EM (which corresponds to a 500-1000 km emitting region with an electron density of $\sim3\times10^{10}$ cm$^{-3}$) are comparable to the values in (cite: Trigilio2018).

The fit has a $\chi^2$ of 62 with 24 degrees of freedom. The high value of $\chi^2$ may be related to either variability in the multiple epochs of submillimeter data or to an underestimate of the absolute calibration of the data. We estimate the fractional contributions of the photosphere and chromosphere, $\Phi_p$ and $\Phi_c$, respectively, using the combined photospheric vs. chromospheric model for Band 7. A Monte Carlo simulation varying $T_C$, $EM$ and the photospheric normalization, $1.02\pm0.09$, relative to their uncertainties gives a photospheric fraction of $\Phi_p=85\pm$1.3% photospheric vs. $\Phi_c=1-\Phi_p=15\pm$1.4% chromospheric. We performed a similar fit to the data for $\alpha$ Cen B (T$_{eff}$=5300 K) and derived $\Phi_p=69\pm$7% photospheric vs. $\Phi_c=31\pm$7% chromospheric.

![](AlphaCenAModel.pdf)

We are now in a position to assess the potential variability of the $\alpha$ Cen stars. A detailed analysis (cite: Makarov2009) suggests that a quiescent star like the Sun would have a photospheric jitter at visible wavelengths of 1 $\mu$AU or 0.75 $\mu$arcsec at distance of 1.34 pc. Their model was based on an evolving population of sunspots on a rotating star with the starspots having an average temperature of T$_{spot}\sim$4000 K vs a photospheric temperature of T$_{phot}\sim$5800 K. At 0.55 $\mu$m the difference in surface brightness between these two regions would be ${B_\nu(T_{spot}, 0.55\mu m)}/{B_\nu(T_{phot}, 0.55\mu m)}$=0.13 whereas in Band 7 (874 $\mu$m) the contrast would be much more muted, ${B_\nu(T_{spot}, 874\mu m)}/{B_\nu(T_{phot}, 874\mu m)}$=0.69, where $B_\nu$ is the Planck function. Thus, a contrast-driven spatial jitter due to starspots in $\alpha$ Cen A would be smaller by $0.69/0.13=5.3$, or only $\sigma_{phot}=0.14\, \mu$arcsec in the sub-millimeter. Unless $\alpha$ Cen A or B is unusually active, which is not indicated by their R$^\prime$HK values, the purely photospheric contribution to astrometric jitter will be negligible.

We must still take into account any jitter in the free-free emission which comprises perhaps 15% of the total emission from $\alpha$ Cen A in Band 7. To assess this source of spatial variability we draw on a series of 17 GHz maps of the Sun obtained with 5$''$ resolution taken daily by the Nobeyama Radio Interferometer (cite: Shibasaki2013). Illustrative maps around Solar Maximum (2001) and Solar Minimum (2010) are shown in Figure [3](#solar)a,b. We evaluated the shift between the intensity-weighted centroid and the nominal disk center by calculating the centroid of all chords across the solar disk in both the vertical and horizontal directions. We made this calculation for every day within 2001 (Solar Maximum) and 2010 (Solar Minimum) for which there were maps of suitable quality (244 in 2001 and 300 in 2010). Maps were subjected to visual examination to reject obvious artifacts.

Figure [3](#solar) shows the combined histogram of day-to-day shifts in the x and y centroids with a 1$\sigma$ standard deviation of 6.46$''$, or $\sigma_{\odot,active}=$0.36% of the solar disk during 2001, and less than half that amount, 2.64$''$ or $\sigma_{\odot,quiet}=0.15$% in 2010 (Table [5](#jitter)). Multiplying these centroid shifts by the angular diameters of $\alpha$ Cen A and B, $\theta_{A,B}$ (cite: Kervella2017a), gives estimates of the jitter arising in the chromosphere, $\sigma_{c}=\sigma_\odot\theta$ expected from each stars in active or quiescent phases.

However, the influence of the chromospheric jitter term on the ALMA measurement is reduced by the contribution of the chromospheric emission to the total, $\Phi_c=32\pm13$%. Propagating the Monte Carlo simulation of the photospheric vs. chromospheric faction into the jitter calculation yields the net amount of jitter expected for the two stars separately for the active and quiet states (Table [5](#jitter)). These terms dominate the purely photospheric component due to starspots.

Finally, the astrometric jitter in the measurement of the *s*eparation between the two stars is given by the root-mean-square sum of estimate for the two stars separately, $\sigma_{\rm tot}=\Phi_c \sqrt{\sigma_{c,\rm A}^2+\sigma_{c,\rm B}^2}$, and varies between 15 and 6 $\mu$arcsec in the active and quiet sun cases. This value represents only an order of magnitude estimate but suggests that for the purposes of astrometrically detecting planets significantly more massive than the Earth, stellar jitter terms are likely to be negligible in comparison with instrumental terms.

![](NobeyamaCentroid.pdf)

+---------------------------------------------------------------+----------------+----------------+
| Quantity                                                      | $\alpha$ Cen A | $\alpha$ Cen B |
+:==============================================================+:==============:+:==============:+
| Active Solar Jitter (Disk Fraction), $\sigma_{\odot,active}$  | 0.36%                           |
+---------------------------------------------------------------+---------------------------------+
| Quiet Solar Jitter (Disk Fraction),$\sigma_{\odot,quiet}$     | 0.15%                           |
+---------------------------------------------------------------+----------------+----------------+
| Chromospheric Fraction, $\Phi_c$                              | 15$\pm$1.4%    | 36$\pm7$       |
+---------------------------------------------------------------+----------------+----------------+
| Stellar Diameter, $\theta_{\rm A,B}$ (mas)$^{a}$              | 8.5            | 6.0            |
+---------------------------------------------------------------+----------------+----------------+
| Stellar jitter (Active, $\mu$arcsec),$\sigma_{\rm c,active}$  | 4.6            | 8.5            |
+---------------------------------------------------------------+----------------+----------------+
| Stellar jitter (Quiet, $\mu$arcsec),$\sigma_{\rm c,Quiet}$    | 1.9            | 3.5            |
+---------------------------------------------------------------+----------------+----------------+
| Total Jitter (Active, $\mu$arcsec), $\sigma_{\rm tot,Active}$ | 15$\pm$10                       |
+---------------------------------------------------------------+---------------------------------+
| Total Jitter (Quiet, $\mu$arcsec),$\sigma_{\rm tot,Quiet}$    | 6$\pm$4                         |
+---------------------------------------------------------------+---------------------------------+

: Estimates of Astrometric Jitter

Table notes: $^{a}$ (cite: Kervella2017a)

# Results

## Orbital and physical parameters of $\alpha$ Cen A and B

Our ALMA observations have particular value for the determination of the orbit and proper motion of the $\alpha$ Cen AB system. They are both the first precision absolute astrometric measurements of the positions of the two stars (referenced to the quasar frame) since *Hipparcos*, and the highest accuracy differential astrometric positions available to date. Due to the brightness and binarity of $\alpha$ Cen AB, Gaia standard processing is unavailable and custom data reductions may be limited in absolute accuracy. However, the third component of the system, Proxima (cite: Kervella2017b), is measured by Gaia with a high accuracy (cite: Kervella2020; Benedict2020). Our analysis includes thousands of RV measurements of both components. The constraint provided by the requirement that astrometry and RV describe the same physical system improves the accuracy of our results.

### Astrometry Data

To determine the orbital parameters of the system, we included archival *differential* astrometry of the AB pair (cite: Hart01) starting in the year 1940 (one full 80 yr orbit as of the year 2020). Measurements older than 1940 do not significantly improve the orbital parameters, due to their larger uncertainties and possible systematics. Our complete astrometric data set includes an *Hipparcos* measurement (from the data reprocessed by (cite: vanLeeuwen07)) combined with the new ALMA data points (Table [4](#tab:diffastrom)) and these archival data. The complete set of differential measurements, including our new ALMA data, is given in Table [6](#tab:diffastromall).

The only available high accuracy *absolute* astrometric measurements of $\alpha$ Cen A and B are the *Hipparcos* data and our new ALMA data points from 2018 and 2019. Our complete sample of absolute astrometric measurements includes a total of 10 points; 9 from our ALMA data as given in Table [2](#tab:absastrom) and 1 from Hipparcos (cite: vanLeeuwen07) UT = 1991-04-02T13:30:00.000, RA$_{\rm A}=219.92040813\pm0.00307$, dec$_{\rm A}=-60.83514522\pm0.00246$, RA$_{\rm B}=219.91412460\pm0.01915$, dec$_{\rm B}=-60.83948046\pm0.01424$. We assign a systematic uncertainty of $\sigma = 3$ mas to each absolute ALMA astrometric measurement, except for the lower resolution measurement from October 2018, which is assigned an uncertainty of 6 mas. These measurements determine the barycentric proper motion. Previous ALMA observations of alpha Cen from (cite: Liseau2015; Liseau2016) were designed for accurate flux measurements but not for accurate astrometric measurements and are not included in our analysis. In particular, the angular resolution is a factor of several worse than our highest resolution and cross checks using a check source or between adjacent observations are not possible with those observations. We do, however, use these data as part of the differential astrometric data.

|  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|
| Date (UT) | Position angle | Pos. angle unc. | Separation | Separation unc. | Reference |
| decimal yrs | deg | deg | arcsec | arcsec |  |
| 2019.6505 | 343.7729 | 0.0032 | 5.27869 | 0.00030 | this paper |
| 2019.6481 | 343.7560 | 0.0053 | 5.27686 | 0.00032 | this paper |
| 2019.6127 | 343.4803 | 0.0033 | 5.25595 | 0.00030 | this paper |
| 2019.6125 | 343.4726 | 0.0033 | 5.25637 | 0.00030 | this paper |
| 2019.5470 | 342.9519 | 0.0033 | 5.21767 | 0.00030 | this paper |
| 2019.5468 | 342.9539 | 0.0033 | 5.21761 | 0.00031 | this paper |
| 2019.5361 | 342.8581 | 0.0053 | 5.21172 | 0.00032 | this paper |
| 2019.5358 | 342.8634 | 0.0033 | 5.21125 | 0.00030 | this paper |
| 2018.7846 | 336.2542 | 0.0089 | 4.80434 | 0.00056 | this paper |
| 2016.1893 | 305.19 | 0.30 | 4.013 | 0.02 | K16 |
| 2015.3326 | 293.30 | 0.60 | 4.020 | 0.04 | K16/ALMA |
| 2014.9574 | 288.28 | 0.70 | 4.081 | 0.05 | K16/ALMA |
| 2014.5426 | 282.91 | 0.30 | 4.208 | 0.02 | K16/ALMA |
| 2014.5126 | 282.84 | 0.30 | 4.184 | 0.02 | K16/ALMA |
| 2014.2410 | 279.20 | 0.30 | 4.330 | 0.05 | An15 |
| 2012.7100 | 262.70 | 0.40 | 5.050 | 0.05 | An14 |
| $\cdots$ |  |  |  |  |  |

: **Relative astrometry of $\alpha$ Cen B with respect to A.**

Table notes: Table 6 is published in its entirety in the machine-readable format. A portion is shown here for guidance regarding its form and content. K16: (cite: Kervella2016); K16/ALMA: (cite: Kervella2016) measurements of data from (cite: Liseau2015); An15: (cite: Anton15); An14:(cite: Anton14)

### Radial Velocity Data

We adopted radial velocity (RV) data from the large series of HARPS measurements of $\alpha$ Cen A and B obtained since 2004, publicly available from the ESO archive. We tested incorporating additional radial velocity measurements from other spectrographs (in particular CES and UVES). However, the shifts in the RV zero point between these instruments result in additional variables in the orbital fit which degrade the quality and reliability. The extended time coverage provided by these instruments does not compensate for this drawback, and we therefore rely on the homogeneous set of HARPS measurements.

As noted by (cite: Lisogorskyi2019), a significant fraction of the spectra collected for $\alpha$ Cen A were processed using an incorrect cross-correlation mask of type K1V (corresponding in fact to $\alpha$ Cen B). We adopted the $\alpha$ Cen B RV from these authors, rejecting the points with the wrong masks from our sample. We also rejected the high cadence observations of 2013, known to be affected by a significant intra-night drift and possible systematics. The RV data of $\alpha$ Cen A are from the standard ESO pipeline. We could not recompute the $\alpha$ Cen A RV from the raw HARPS data, using a correct spectral-type mask and the standard ESO pipeline, because that pipeline is not publicly accessible.

We corrected the RV shift caused by the HARPS fiber exchange in 2015, as recommended by (cite: Trifonov2020). The applied shift is $\Delta V_A = +13.33$m s$^{-1}$ and $\Delta V_B = +11.53$m s$^{-1}$, which we subtract from the pipeline RVs for epochs later than $JD=2457163$. We then filtered out the RV measurements whose uncertainty is larger than 10 m s$^{-1}$, and cleaned the strongest outliers with a $5\sigma$ clipping with respect to the best fit preliminary solution. The latter step rejects only 0.9% of the measurements of A and 1.0% of B. Our final sample of RV measurements includes 5184 RV measurements for A and 12383 for B. A sample of the radial velocity data are shown in Table [7](#tab:radvel) and the complete table is available online. Finally, we checked that adopting the (cite: Trifonov2020) RV shift does not result in a significant change of the final orbital parameters.

Although the statistical uncertainties of the HARPS RV measurements are extremely small (a few 10 cm s$^{-1}$), the effective jitter is significantly larger due to stellar activity, crosstalk between the two stars or instrumental effects for these extremely bright targets. Therefore we added in quadrature a uniform uncertainty of 2 m s$^{-1}$ to all measurements. Following (cite: Pourbaix2016) (cite: Pourbaix2002; Kervella2016), we subtracted a constant velocity shift of $V_B = 314$ m s$^{-1}$ from the RV measurements of $\alpha$ Cen B, thereby accounting for its relative gravitational redshift and convective shift with respect to $\alpha$ Cen A, whose intrinsic shift is assumed to be zero.

|             |      |               |                    |
|:------------|:-----|:--------------|:-------------------|
| MJD         | Star | Radial Vel.   | Rad. Vel. $\sigma$ |
| days        |      | km sec$^{-1}$ | km sec$^{-1}$      |
| 53039.36288 | A    | -22.73789     | 0.00201            |
| 53039.36333 | A    | -22.73742     | 0.00201            |
| 53039.36376 | A    | -22.73696     | 0.00202            |
| 53139.06947 | A    | -22.70210     | 0.00200            |
| 53139.07017 | A    | -22.70149     | 0.00200            |
| $\cdots$    |      |               |                    |

: **Radial velocity measurements for $\alpha$ Cen A and B from the HARPS instrument**

Table notes: Table 7 is published in its entirety in the machine-readable format. A portion is shown here for guidance regarding its form and content.

### Orbital and proper motion fit procedure

To fit the orbital parameters and proper motion, we generally followed the same approach as (cite: Kervella2016). We first determined the orbital parameters (Keplerian orbital elements, dynamical parallax, total mass of the system, and mass ratio) for epoch 2019.5 based only on the RV and differential astrometry data and a simple Keplerian two-body model. In a second step, we adopted the dynamical parallax and mass ratio to determine the barycentric proper motion from the absolute Hipparcos and ALMA absolute astrometric positions of $\alpha$ Cen A and B. The position of the barycenter of the system was thus computed for each of the Hipparcos and ALMA measurement epochs. The space velocity of the barycenter of the AB system was then determined from this set of barycenter positions through a linear fit. For both steps, the determination of the best-fit parameters was obtained using a classical multi-parameter Levenberg-Marquardt least-squares fitting algorithm on the complete data set. It is based on the `scipy.optimize.leastsq` routine of the SciPy[^1] library.

Among binary stars, $\alpha$ Cen is peculiar due to its proximity to the Earth and fast motion across the sky. As a consequence, we implemented in our orbital and proper motion model a few second-order corrective terms that have an influence on the orbital parameters and proper motion estimates. First, the very fast motion of $\alpha$ Cen induces a significant change in perspective of its space velocity vector (that comprises the RV and tangential velocity components). This geometrical effect has been known for decades (cite: vandeKamp1977), but to our knowledge it was not taken into account in recent computations of the orbital parameters of the system. It affects the barycentric RV and the tangential proper motion, both changing with time. The RV geometrically increases with an acceleration of $\dot{V} = +0.421$ m s$^{-1}$yr$^{-1}$, while the tangential velocity is conversely decreasing with time.

Another effect of the space motion of $\alpha$ Cen is a perspective-induced change of the inclination of the orbit as seen from the Earth. This creates a time-dependent variation of the apparent relative position of B with respect to A. In addition, as the distance to the Earth is presently decreasing, the apparent separation of the two stars is increasing. At the *Hipparcos* epoch (1991.25) the perspective change results in a shift in relative position of B compared to epoch 2019.5 of approximately 30 mas, which is not completely negligible compared to the error bars.

We also corrected the differential and absolute astrometric measurements for the light time propagation effect, based on our initial estimates of the barycentric RV. Due to the $\approx -22$ km s$^{-1}$ approach velocity of the system, the light time aberration on its apparent position on the sky is evolving, compared to our 2019.5 reference epoch. In other words, as $\alpha$ Cen was farther to the Earth in the past, its apparent position was slightly more “lagging behind” on its trajectory compared to its true position in space than it is today.

For these different second order effects (perspective, light time), the changes are slow and can be considered linear over decades or even centuries. For this reason, we took them into account as a perturbation to our input data set. In practice, we computed an initial fit of the data without accounting for the perspective and light time effects. This resulted in an initial estimate of a mean value of the barycentric parallax, radial velocity and proper motion vector. Based on these results, we corrected the input differential and absolute astrometric positions as well as the RV values of the two stars to bring them to our reference epoch of 2019.5. This reference time was arbitrarily chosen to correspond to the majority of our ALMA measurements, in order to limit the correlations between the proper motion vector components. For these computations, we extensively used the `SkyCoord` class and celestial coordinate system transformation routines available in the `Astropy`[^2] library. We then computed a second round of orbital and proper motion fitting on these corrected observations, to determine the actual orbital parameters valid for our 2019.5 reference epoch. We checked that a third iteration of fitting did not result in a significant change of the derived parameters.

Finally, we emphasize that a complete astrometric solution is critical to removing the effects of the motions of $\alpha$ CenA and B individually and as a system before looking for differential motions due to a planet. The 30 year temporal baseline from Hipparcos and ALMA and the high precision of the example 5-yr observing ALMA program discussed in §[3.3](#planetdetection) would allow us to de-trend the effects of the 80-yr $\alpha$ CenAB orbit to identify the short period signatures of planets at the 10s of $\mu$as level in $\sim$ 1 yr orbit ($\S$[\[prospects\]](#prospects)).

### Orbital parameters, masses and barycentric proper motion

We list the best fit orbital parameters and masses of the $\alpha$ Cen AB system in Table [8](#tab:orbital), and present the corresponding orbital trajectory in Figure [4](#orbit). We obtain a satisfactory reduced $\chi^2$ for the best fit orbit model of 1.2. The radii are computed adopting the limb darkened angular diameters measured by (cite: Kervella2017a). The luminosities of A and B are computed adopting the bolometric flux by (cite: Boyajian2013) and $L_\odot = 3.828\ 10 ^{26}$ W.

We note differences between the Table [8](#tab:orbital) parallax and previous parallax determinations from (cite: Pourbaix2016) and (cite: Kervella2016). The main differences between these past analyses and the present work includes the selection of the RV data set and our new high accuracy ALMA differential astrometry. The radial velocity data used and the residuals of the fit are shown in Fig. [5](#RV_data). The acquisition of new RV measurements with HARPS, particularly of $\alpha$ Cen A, would certainly improve the orbital phase coverage. We plot the residuals of the Hipparcos and ALMA absolute astrometric measurements to the best-fit orbit in Figure [6](#diffastrom_residuals).

![image](AlfCen-Orbit.pdf) ![image](Residuals-AlfCen-diffAstrom-All.pdf)

![](AlfCen-RV-fit.pdf)

| Parameter |  | Present work | K16 | PB16 |
|:---|:--:|:---|:---|:---|
| Semi-major axis (arcsec) | $a$ | $17.4930 \pm 0.0096$ | $17.592 \pm 0.013$ | $17.66 \pm 0.026$ |
| Inclination (deg) | $i$ | $79.2430 \pm 0.0089$ | $79.320 \pm 0.011$ | $79.32 \pm 0.044$ |
| Arg. of periastron (deg) | $\omega$ | $231.519 \pm 0.027$ | $232.006 \pm 0.051$ | $232.3 \pm 0.11$ |
| Long. of asc. node (deg) | $\Omega$ | $205.073 \pm 0.025$ | $205.064 \pm 0.033$ | $204.85 \pm 0.084$ |
| Period (yr) | $P$ | $79.762 \pm 0.019$ | $79.929 \pm 0.013$ | $79.91 \pm 0.013$ |
| Ref. epoch | $T_0$ | $1955.564 \pm 0.015$ | $1955.604 \pm 0.013$ | $1955.66 \pm 0.014$ |
| Eccentricity | $e$ | $0.51947 \pm 0.00015$ | $0.5208 \pm 0.0011$ | $0.524 \pm 0.0011$ |
| Barycentric RV (km s$^{-1}$) | $V_0$ | $-22.3796 \pm 0.0020$ | $-22.3930 \pm 0.0043$ | $-22.390 \pm 0.0042$ |
| RV accel. (m s$^{-1}$ yr$^{-1}$) | $\dot{V_0}$ | $+0.421$ | $-$ | $-$ |
| Parallax (mas) | $\varpi$ | $750.81 \pm 0.38$ | $747.17 \pm 0.61$ | $743 \pm 1.3$ |
| Parallax var. ($\mu$as yr$^{-1}$) | $\dot{\varpi}$ | $+13.0$ | $-$ | $-$ |
| Mass fraction | $\frac{m_{\rm A}}{m_A+m_{\rm B}}$ | $0.54266 \pm 0.00011$ | $0.54116 \pm 0.00027$ | $0.5383 \pm 0.00044$ |
| Mass of A $(M_\odot)$ | $m_{\rm A}$ | $1.0788 \pm 0.0029$ | $1.1055 \pm 0.0039$ | $1.133 \pm 0.0050$ |
| Mass of B $(M_\odot)$ | $m_{\rm B}$ | $0.9092 \pm 0.0025$ | $0.9373 \pm 0.0033$ | $0.972 \pm 0.0045$ |
| Radius of A $(R_\odot)$ | $R_A$ | $1.2175 \pm 0.0055$ |  |  |
| Radius of B $(R_\odot)$ | $R_B$ | $0.8591 \pm 0.0036$ |  |  |
| Luminosity of A $(L_\odot)$ | $L_A$ | $1.5059 \pm 0.0019$ |  |  |
| Luminosity of B $(L_\odot)$ | $L_B$ | $0.4981 \pm 0.0007$ |  |  |

: Orbital elements, masses, parallax, position and proper motion of $\alpha$ Cen AB, for epoch 2019.5.

![image](Residuals-AlfCen-ALMA.pdf) ![image](Residuals-AlfCen-diffAstrom-ALMA.pdf)

Table [9](#tab:propermotion) lists the position and proper motion of the barycenter of the $\alpha$ Cen system for epoch 2019.5. The reduced $\chi^2$ of the best fit barycenter proper motion vector model is 1.6. For all the model fitting done for the present work, the uncertainties of the best-fit parameters are normalized to the data dispersion around the best-fit model. In practice, this means that the $1\sigma$ uncertainties of the derived parameters are scaled by a factor of $\approx \sqrt{1.6}$. Through this rescaling, we take into account in the uncertainties the residual dispersion of the data points with respect to the model, that may be induced by instrumental or astrophysical effects.

Due to the perspective acceleration, the proper motion vector, together with the radial velocity, changes with time. The sky trajectory of $\alpha$ Cen A, B, and their barycenter is shown in Fig. [7](#sky_trajectory). The apparent motion of A and B is the result of the combination of the proper motion of the barycenter, orbital motion of the two components, and the parallax. Figure [8](#barycenter_ellipse) displays the measured position of the AB barycenter compared to the parallactic ellipse derived from the orbital fit. Although the agreement is satisfactory between the measurements and the ellipse, this is not a fit. It is possible to derive the trigonometric parallax by fitting the observed Hipparcos and ALMA positions of the barycenter. But, due to relatively poor phase coverage of the parallactic ellipse because of our limited number of absolute measurements, the accuracy of the best fit trigonometric parallax ($\varpi_\mathrm{trig} = 747.1 \pm 5.2$ mas) is significantly worse than that of the orbital parallax ($\varpi_\mathrm{orb} =750.81 \pm 0.38$ mas). Both values are, however, statistically consistent.

| Parameter |  | Present work (J2019.5) | K16, K17 (J1991.25) |
|:---|:--:|:---|:---|
| RA (ICRS) | $\alpha_0$ | 14:39:26.1413 $\pm 1.50$ mas | 14:39:40.2068 $\pm 25$ mas |
|  |  | $219.85892215 \pm 8.6\,10^{-7}$ deg | $-$ |
| Dec. (ICRS) | $\delta_0$ | $-60$:49:53.875 $\pm 1.17$ mas | $-60$:50:13.673 $\pm 19$ mas |
|  |  | $-60.83163195 \pm 3.3\,10^{-7}$ deg | $-$ |
| PM RA (mas yr$^{-1}$) | $\mu_\alpha$ | $-3639.95 \pm 0.42$ | $-3619.9 \pm 3.9$ |
| PM Dec. (mas yr$^{-1}$) | $\mu_\delta$ | $+700.40 \pm 0.17$ | $+693.8 \pm 3.9$ |

: Position and proper motion (PM) of the barycenter of $\alpha$ Cen A and B. The parameters derived by (cite: Kervella2016) and (cite: Kervella2017b) are listed in the K16, K17 column for comparison.

![image](AlfCen-Barycenter-trajectory-Hip.pdf) ![image](AlfCen-Barycenter-trajectory.pdf)

![image](AlfCen-Barycenter-ellipse.pdf)\
![image](AlfCen-Barycenter-residuals.pdf)\
![image](AlfCen-Barycenter-residuals-ALMA.pdf)

## Prospects for Improved Stellar Properties

The $\alpha$ Cen AB system is a touchstone for stellar astrophysics because these two stars straddle the Sun in mass with similar age, activity level and metallicity. Because their physical properties can be determined with great precision due to their proximity to us, these stars are used for validation of stellar models and to check the predictions of techniques such as asteroseismology, e.g. (cite: Joyce2018; Nsamba2019).

$\alpha$ Cen is one of the Gaia mission benchmark systems selected as references for the determination of stellar parameters (cite: Heiter2015). In advance of those anticipated, possibly more precise results, we discuss briefly how our new ALMA measurements improve the precision of our knowledge of $\alpha$ Cen A and B.

The combination of asteroseismic frequencies and interferometric radius measurements has proven to powerfully constrain the internal structure of stars (cite: Cunha2007; Chaplin2013). $\alpha$ Cen A and B were among the first stars to have their oscillation spectra measured with high precision by (cite: Bouchy2001; Bouchy2002), using radial velocity measurements with the CORALIE spectrograph. The angular diameters of $\alpha$ Cen A and B were first measured interferometrically with the VLTI/VINCI instrument by (cite: Kervella2003), and later refined with the VLTI/PIONIER instrument (cite: Kervella2017a) at $\theta_\mathrm{LD}$(A) $= 8.502 \pm 0.038$ mas and $\theta_\mathrm{LD}$(B) $= 5.999 \pm 0.025$ mas. The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc) is larger by 0.49% compared to the value previously determined by (cite: Kervella2016) ($\varpi = 747.17$ mas). As a result, we revise the linear radii of the two stars to $R_{\rm A} = 1.2175 \pm 0.0055\,R_\odot$ and $R_{\rm B} = 0.8591 \pm 0.0036\,R_\odot$, a change of approximately $-1\,\sigma$. The masses and radii values are close to the theoretical values determined by (cite: Thevenin2002) and (cite: Yildiz2008) from the analysis of the asteroseismic frequencies of the two stars.

The determination of the age of stars is generally a complex enterprise (cite: Soderblom2010). In spite of the similarity of the physical properties of $\alpha$ Cen with the Sun and their well-determined masses, the estimate of their age (cite: Mamajek2008; Morel2018; Sahlholdt2019), core properties (cite: deMeulenaer2010; Bazot2016), and inner opacity (cite: Yildiz2011) remain a challenging task. For the evolutionary modeling of $\alpha$ Cen A and B, the treatment of convection is problematical, and the mixing-length parameter remains relatively uncertain (cite: Yildiz2007; Trampedach2014; Joyce2018; Spada2019).

For $\alpha$ Cen A and B, further progress on the modeling of structure and evolutionary status requires improvements to fundamental stellar parameters, both in higher precision and accuracy. (cite: Joyce2018) give the age of $\alpha$ Cen AB as 5.3$\pm$0.3 Gyr based on masses which are $\sim 3\%$ higher than those presented here. New models using these more precise values may result in revised ages for this touchstone system. While the uncertainties in the ages derived from the model fitting due to uncertainties in mixing length, etc, may remain the same, the centroid of the age estimates may shift significantly, especially as future ALMA observations reduce the parallax uncertainties by another factor of 2-3.

## Prospects for Planet Detection based on Differential Astrometry

Astrometric and PRV measurements have complementary selection biases. Astrometry favors planets more distant from the host star, and PRV planets closer-in. Figure [9](#compare) shows limits to planets in the planet mass vs. semi-major axis plane for the two techniques, each shown with three plausible levels of limiting sensitivity. PRV limits currently have a $\sim2\sigma$ value of 5 m s$^{-1}$ (cite: Zhao2018) which we show potentially improving to 2 and 1 m s$^{-1}$. For the ALMA-based astrometry we adopt three cases based on single measurement accuracy of 500, 250, 100 $\mu$as and a series of 20 observations spread over 5 years. The ALMA data presented here demonstrate a differential astrometric accuracy at the 300 $\mu$as level for our longest baseline configuration, that improves as expected with an increasing baseline length. The longest baselines available at ALMA are $\sim2.5$ times longer than the baselines used for the present observations, thus if the differential astrometry performance continues to scale with baseline length, single epoch observations at $\sim$100 $\mu$as are already feasible. To check our detection estimate, we compare with the astrometric data presented by (cite: Benedict2017). They used 31 HST/FGS measurements, spanning 2.9 years, having per observation precision of 800 $\mu$as to derive a semi-major axis of $760 \pm 110$ $\mu$as (2.4 AU at 46 pc) for HD 202206 c, a brown dwarf with a period of 3.45 yr, resulting in a $\sim 7\sigma$ detection. With a single measurement precision of $<$300 $\mu$as (Table [4](#tab:diffastrom)), an ALMA campaign with similar duration and cadence would yield a noise floor $<50 \,\mu$as. A 20 observation campaign would have a slightly higher noise floor $\sim 55$ $\mu$as, or a two sigma value of 110 $\mu$as and could lead to the identification of a 25 M$_\oplus$ planet with a 2 AU orbital semi-major axis (Figure [9](#compare)).

While such a program would be observationally challenging due to the ALMA configuration cycle and a higher SNR would be needed for the detection of a planet in the absence of PRV data, ALMA astrometric data are clearly relevant in the exoplanet phase space of $\alpha$ Cen. When combined with PRV data, these complementary dynamical measurements will probe the entire 3 AU region around each of the $\alpha$ CenA and B components where planetary orbits are expected to be stable (cite: Quarles2016).

![](ALMA-RVLimitsNEAR.pdf)

The mid-infrared direct imaging project NEAR (cite: Kasper2019; Wagner2020) has tentatively identified a candidate planet associated with $\alpha$ Cen A. While instrument artifacts cannot yet be ruled out, they find an object at 1.1 AU from $\alpha$ Cen A with a range of possible radii between 3.3 and 7 M$_\oplus$. Converting radius to mass is of course an uncertain process. Taking transiting planets in this radius range with masses measured with better than 20% accuracy[^3] we find an average mass of 30 M$_\oplus$, a minimum mass of 6 M$_\oplus$ and a maximum mass of 135 M$_\oplus$. While existing measurements would seem to rule out the largest possible masses, future observations of either type could determine the mass of this putative object.

## The orbit of Proxima Centauri and $\alpha$ Cen AB stellar conjunctions

Our accurate determination of the barycentric parallax, radial velocity, and proper motion of $\alpha$ Cen AB (Tables [8](#tab:orbital) and [9](#tab:propermotion)) enables us to improve our knowledge of the relative velocity between the inner AB system and the third component of the system, Proxima Centauri (cite: Kervella2017b). We adopt the Hipparcos-Gaia proper motion determined by (cite: Kervella2019) for Proxima ($\mu_\alpha = -3781.629 \pm 0.048$ mas a$^{-1}$; $\mu_\delta = +769.421 \pm 0.052$ mas a$^{-1}$) and the radial velocity from (cite: Kervella2017b) ($v_\mathrm{r,abs} = -22.204 \pm 0.032$ km s$^{-1}$. The improved parallax and masses of the AB system translate into an unbound differential velocity limit of $v_\mathrm{max} = 554 \pm 7$ m s$^{-1}$ for a gravitationally bound system. We obtain a differential space velocity of $\Delta v_{\alpha-\mathrm{Prox}} = 280 \pm 32$ m s$^{-1}$ between $\alpha$ Cen AB and Proxima, very significantly below the unbound velocity. The significance of the gravitational link between AB and Proxima has therefore increased over the last three years from $4.4\sigma$ in (cite: Kervella2017b), to $5.5\sigma$ in (cite: Kervella2019) to $8.3\sigma$ in the present work ($<10^{-15}$ false alarm probability). Proxima becomes a yet more valuable check on lower main sequence stellar modeling. We list the refined parameters for the orbit of Proxima in Table [10](#tab:proximaorbit).

| Parameter                       |           Value           | Unit   |
|:--------------------------------|:-------------------------:|:-------|
| Semi-major axis $a$             |    $8.2^{+0.4}_{-0.3}$    | kAU    |
| Excentricity $e$                | $0.497^{+0.057}_{-0.060}$ |        |
| Period $P$                      |     $511^{+41}_{-30}$     | kyr    |
| Inclination $i$                 |   $124.9^{+2.9}_{-3.2}$   | $\deg$ |
| Longitude of asc. node $\Omega$ |      $165^{+3}_{-3}$      | $\deg$ |
| Argument of periastron $\omega$ |   $151.0^{+5.7}_{-4.9}$   | $\deg$ |
| Epoch of periastron $T_0$$^a$   |    $+278^{+36}_{-28}$     | kyr    |
| Periastron radius               |    $4.1^{+0.7}_{-0.6}$    | kAU    |
| Apastron radius                 |   $12.3^{+0.2}_{-0.1}$    | kAU    |

: Orbital parameters of Proxima.

Table notes: $^{a}$ The epoch of periastron passage $T_0$ is relative to present.

Using the improved proper motion and orbital parameters of $\alpha$ Cen AB determined in the present work, it is possible to refine the predictions of the stellar conjunctions between $\alpha$ Cen AB and background field stars that were identified by K16. We took into account the positions and proper motions of stars S2, S4 and S6 (see Table 3; K16) that are listed in the Gaia DR3 catalog (cite: gaiadr3). For stars S1, S3 and S5, we adopted the uncertainties from K16, in particular an uncertainty on their proper motion of $\pm 10$ mas yr$^{-1}$. Thanks to the new ALMA astrometry, the trajectory of $\alpha$ Cen AB is significantly better constrained, resulting in a significant reduction of the uncertainties on the conjunction parameters in particular the minimum approach angular separation $\rho_\mathrm{min}$. The trajectory of S2 is shown in Figure [10](#S2) with a closest approach to $\alpha$ Cen A of 1.5$''$ in mid 2023. With $\Delta$K=12.6 mag, S2 will provide a well defined “test particle" for searches for Jovian-sized planets via infrared direct imaging experiments (cite: Beichman2020).

![](S2A-approach.pdf)

For stars S1, S3 and S5, the error budget is dominated by the uncertainty on the position and proper motion of these field stars, and the error bars on $\rho_\mathrm{min}$ are only moderately improved compared to K16 (their Table 3). The revised $\rho_\mathrm{min}$ and dates of closest approach are generally close to the previously determined values, except for the S3 event in 2023 that occurs about six months earlier than calculated in K16.

|              |                     |      |           |            |                |
|:------------:|:-------------------:|:----:|:---------:|:----------:|:--------------:|
| $\alpha$ Cen | $\rho_\mathrm{min}$ | Star | $\Delta$V |    Date    |      Date      |
|              |      (arcsec)       |      |    mag    |            | (decimal year) |
|      B       |  $0.088 \pm 0.131$  | S01  |   18.7    | 2021-04-20 |    2021.301    |
|      A       |  $1.509 \pm 0.002$  | S02  |   15.7    | 2023-04-13 |    2023.279    |
|      B       |  $1.484 \pm 0.074$  | S03  |   18.4    | 2023-12-12 |    2023.946    |
|      B       |  $2.283 \pm 0.004$  | S04  |   16.2    | 2024-10-26 |    2024.818    |
|      A       |  $0.170 \pm 0.131$  | S05  |   21.5    | 2028-04-20 |    2028.301    |
|      B       |  $0.294 \pm 0.006$  | S06  |   15.6    | 2031-05-23 |    2031.389    |

: Conjunctions of $\alpha$ Cen AB until 2031 with background stars S1 to S6 identified by (cite: Kervella2016) (their Table 3). The minimum separation $\rho_\mathrm{min}$, closest approach date and $\Delta$V magnitude (from K16) are listed.

# Conclusions

1.  We have demonstrated that ALMA produces for the nearby bright stars $\alpha$ Cen A and B absolute astrometric measures with precision and accuracy of order 3 mas and differential separation uncertainties of 300 to 600 $\mu$arcsec.

2.  By comparison with the Sun we establish an astrometric jitter due to stellar activity of less than 15 $\mu$arcsec.

3.  The combination of historical measurements of $\alpha$ Cen A-B position angle and separation, more recent PRV measurements from HARPS, and absolute astrometry from *Hipparcos*, and ALMA yields improved $\alpha$ Cen A and B orbital elements, system proper motion and parallax, and component masses.

4.  We find stellar parameters of $m_{\rm A} =1.0788 \pm 0.0029$ $M_\odot$ and $m_{\rm B} = 0.9092 \pm 0.0025$ $M_\odot$ and $R_{\rm A} =1.2175 \pm 0.0055$ $R_\odot$ and $R_{\rm B} = 0.8591 \pm 0.0036$ $R_\odot$. These masses and radii, now improved with a more precise and accurate parallax, will serve to further constrain stellar evolutionary models and provide ’ground truth’ for asteroseismological predictions.

5.  Our accurate determination of the $\alpha$ Cen AB system parallax, RV, and proper motion, when compared to those values for Proxima Centauri, confirms that the three stars constitute a bound system.

6.  Continued astrometric monitoring of the $\alpha$ Cen AB system with ALMA, particularly with longer baseline configurations and in combination with precision radial velocity measurements, should reduce planetary companion detection limits to the few 10’s of M$_\oplus$ range across the entire $<$3 AU region expected to be stable in the $\alpha$ Cen AB system.

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00557.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. Some of the research described in this publication was carried out in part at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration. GFB thanks McDonald Observatory for extending a Research Fellow position, allowing continued possession of an office and computing equipment. We thank the referees for a careful reading of the paper and for making many useful suggestions to clarify the material.

# Facilities

ALMA, ESO:3.6m(HARPS)

# Software

CASA (McMullin et al. 2007), astropy (The Astropy Collaboration 2013, 2018)

# Ephemeris of $\alpha$ Cen A and B

To help in the preparation of future observations of $\alpha$ Cen, we present in this section the coordinates of $\alpha$ Cen A and B as a function of time for the period between 2010 and 2050. Table [12](#tab:ephemAB) gives the positions of the AB center of mass, A and B in the ICRS frame. These coordinates take into account the proper motion, orbital motion and parallactic wobble of the two stars. The relative position of B with respect to A in Cartesian and spherical coordinates is also provided, and the evolution of the separation and position angle of $\alpha$ Cen B relative to A are shown in Fig. [11](#seppa).

![](AlfCen-Sep-PA.pdf)

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| Date | RA$_{\rm AB}$ | Dec$_{\rm AB}$ | RA$_{\rm A}$ | Dec$_{\rm A}$ | RA$_{\rm B}$ | Dec$_{\rm B}$ | dRA | dDec | $\rho$ | $\theta$ |
|  |  |  |  |  |  |  | arcsec | arcsec | arcsec | degrees |
| 2010.00 | 14:39:30.9533 | -60:50:00.386 | 14:39:31.3371 | -60:49:59.098 | 14:39:30.4978 | -60:50:01.913 | -6.136 | -2.815 | 6.751 | 245.357 |
| 2010.05 | 14:39:30.9404 | -60:50:00.527 | 14:39:31.3230 | -60:49:59.259 | 14:39:30.4865 | -60:50:02.032 | -6.115 | -2.774 | 6.715 | 245.600 |
| 2010.10 | 14:39:30.9180 | -60:50:00.665 | 14:39:31.2992 | -60:49:59.415 | 14:39:30.4656 | -60:50:02.148 | -6.094 | -2.733 | 6.679 | 245.845 |
| 2010.15 | 14:39:30.8857 | -60:50:00.782 | 14:39:31.2657 | -60:49:59.551 | 14:39:30.4349 | -60:50:02.243 | -6.073 | -2.692 | 6.643 | 246.093 |
| 2010.20 | 14:39:30.8445 | -60:50:00.863 | 14:39:31.2231 | -60:49:59.651 | 14:39:30.3953 | -60:50:02.302 | -6.052 | -2.651 | 6.607 | 246.344 |
| 2010.25 | 14:39:30.7961 | -60:50:00.897 | 14:39:31.1734 | -60:49:59.704 | 14:39:30.3484 | -60:50:02.313 | -6.031 | -2.610 | 6.571 | 246.598 |
| 2010.30 | 14:39:30.7429 | -60:50:00.878 | 14:39:31.1189 | -60:49:59.703 | 14:39:30.2968 | -60:50:02.272 | -6.010 | -2.569 | 6.536 | 246.855 |
| 2010.35 | 14:39:30.6877 | -60:50:00.805 | 14:39:31.0623 | -60:49:59.649 | 14:39:30.2431 | -60:50:02.176 | -5.988 | -2.528 | 6.500 | 247.114 |
| 2010.40 | 14:39:30.6334 | -60:50:00.682 | 14:39:31.0067 | -60:49:59.545 | 14:39:30.1904 | -60:50:02.031 | -5.967 | -2.487 | 6.465 | 247.376 |
| 2010.45 | 14:39:30.5828 | -60:50:00.519 | 14:39:30.9548 | -60:49:59.400 | 14:39:30.1414 | -60:50:01.846 | -5.946 | -2.446 | 6.429 | 247.641 |
| 2010.50 | 14:39:30.5382 | -60:50:00.327 | 14:39:30.9089 | -60:49:59.227 | 14:39:30.0984 | -60:50:01.632 | -5.925 | -2.405 | 6.394 | 247.909 |
| 2010.55 | 14:39:30.5015 | -60:50:00.121 | 14:39:30.8709 | -60:49:59.040 | 14:39:30.0633 | -60:50:01.404 | -5.903 | -2.364 | 6.359 | 248.180 |
| 2010.60 | 14:39:30.4739 | -60:49:59.918 | 14:39:30.8418 | -60:49:58.856 | 14:39:30.0372 | -60:50:01.178 | -5.882 | -2.322 | 6.324 | 248.454 |
| 2010.65 | 14:39:30.4555 | -60:49:59.733 | 14:39:30.8221 | -60:49:58.689 | 14:39:30.0204 | -60:50:00.971 | -5.861 | -2.281 | 6.289 | 248.730 |
| 2010.70 | 14:39:30.4459 | -60:49:59.580 | 14:39:30.8112 | -60:49:58.555 | 14:39:30.0124 | -60:50:00.795 | -5.839 | -2.240 | 6.254 | 249.010 |
| 2010.75 | 14:39:30.4437 | -60:49:59.471 | 14:39:30.8076 | -60:49:58.466 | 14:39:30.0118 | -60:50:00.665 | -5.818 | -2.199 | 6.219 | 249.294 |
| 2010.80 | 14:39:30.4468 | -60:49:59.415 | 14:39:30.8094 | -60:49:58.428 | 14:39:30.0165 | -60:50:00.586 | -5.796 | -2.158 | 6.185 | 249.580 |
| 2010.85 | 14:39:30.4525 | -60:49:59.413 | 14:39:30.8138 | -60:49:58.445 | 14:39:30.0239 | -60:50:00.562 | -5.775 | -2.117 | 6.150 | 249.869 |
| 2010.90 | 14:39:30.4579 | -60:49:59.464 | 14:39:30.8178 | -60:49:58.515 | 14:39:30.0308 | -60:50:00.591 | -5.753 | -2.075 | 6.116 | 250.162 |
| 2010.95 | 14:39:30.4597 | -60:49:59.560 | 14:39:30.8182 | -60:49:58.629 | 14:39:30.0342 | -60:50:00.663 | -5.731 | -2.034 | 6.082 | 250.458 |
| 2011.00 | 14:39:30.4552 | -60:49:59.686 | 14:39:30.8124 | -60:49:58.775 | 14:39:30.0314 | -60:50:00.768 | -5.710 | -1.993 | 6.048 | 250.758 |
| 2011.05 | 14:39:30.4424 | -60:49:59.827 | 14:39:30.7982 | -60:49:58.935 | 14:39:30.0201 | -60:50:00.887 | -5.688 | -1.952 | 6.014 | 251.061 |
| 2011.10 | 14:39:30.4199 | -60:49:59.965 | 14:39:30.7744 | -60:49:59.092 | 14:39:29.9993 | -60:50:01.002 | -5.666 | -1.911 | 5.980 | 251.367 |
| ... |  |  |  |  |  |  |  |  |  |  |

: Ephemeris of $\alpha$ Cen A and B between 2010 and 2050. The RA$_{\rm AB}$ and Dec$_{\rm AB}$ columns correspond to the center of mass position. dRA and dDec are the position offsets of B relative to A, expressed in arcseconds, $\rho$ is the $A-B$ separation, and $\theta$ the position angle of B with respect to A $(N=0, E=90\deg)$. These coordinates include the proper motion, orbital motion and parallactic wobble of the two stars, and the light time propagation delay. The full table is available in machine-readable format.

(ref: Akeson2013) Akeson, R. L., Chen, X., Ciardi, D., et al. 2013, PASP, 125,

(ref: Anton15) Anton, R. 2015, Journal of Double Star Observations, 11, 81

(ref: Anton14) Anton, R. 2014, Journal of Double Star Observations, 10, 232

(ref: astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Baraffe2015) Baraffe, I., Homeier, D., Allard, F., et al. 2015, A&A, 577, A42

(ref: Bazot2016) Bazot, M., Christensen-Dalsgaard, J., Gizon, L., & Benomar, O. 2016, MNRAS, 460, 1254

(ref: Beichman2020) Beichman, C., Ygouf, M., Llop Sayson, J., et al. 2020, PASP, 132, 015002

(ref: Benedict2017) Benedict, G. F. & Harrison, T. E. 2017, AJ, 153, 258. doi:10.3847/1538-3881/aa6d59

(ref: Benedict2020) Benedict, G. F., & McArthur, B. E. 2020, RNAAS, 4, 86

(ref: Boro2018) Boro Saikia, S., Marvin, C. J., Jeffers, S. V., et al. 2018, A&A, 616, A108

(ref: Bouchy2001) Bouchy, F., & Carrier, F. 2001, A&A, 374, L5-L8

(ref: Bouchy2002) Bouchy, F., & Carrier, F. 2002, A&A, 390, 205

(ref: Boyajian2013) Boyajian, T. S., von Braun, K., van Belle, G., et al. 2013, ApJ, 771, 40

(ref: Chaplin2013) Chaplin, W., & Miglio, A., 2013, ARA&A, 51, 353

(ref: Cunha2007) Cunha, M. S., Aerts, C., Christensen-Dalsgaard, J., et al. 2007, The Astronomy & Astrophysics Review, 14, 217

(ref: Curiel2020) Curiel, S., Ortiz-León, G. N., Mioduszewski, A. J., et al. 2020, AJ, 160, 97

(ref: deMeulenaer2010) de Meulenaer, P., Carrier, F., Miglio, A., et al. 2010, A&A, 523, A54

(ref: Dumusque2018) Dumusque, X. 2018, A&A, 620, A47

(ref: Engels1981) Engels, D., Sherwood, W. A., Wamsteker, W., et al. 1981, A&AS, 45, 5

(ref: gaiadr3) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2020, arXiv:2012.01533

(ref: Hart01) Hartkopf, William I. and Mason, Brian D. and Worley, Charles E. 2001, AJ, 122, 3472

(ref: Heiter2015) Heiter, U., Jofré, P., Gustafsson, B., et al. 2015, å, 582, A49

(ref: Holman1999) Holman, M. J., & Wiegert, P. A. 1999, AJ, 117, 621

(ref: Joyce2018) Joyce, M., & Chaboyer, B. 2018, ApJ, 864, 99

(ref: Kasper2019) Kasper, M., Arsenault, R., Käufl, U., et al. 2019, The Messenger, 178, 5

(ref: Kervella2003) Kervella, P., Thévenin, F., Ségransan, D., et al. 2003, A&A, 404, 1087

(ref: Kervella2016) Kervella, P., Mignard, F., Mérand, A., & Thévenin, F. 2016, A&A, 594, A107

(ref: Kervella2017a) Kervella, P., Bigot, L., Gallenne, A., et al. 2017, A&A, 597, A137

(ref: Kervella2017b) Kervella, P., Thévenin, F., & Lovis C. 2017b, A&A, 598, L7

(ref: Kervella2019) Kervella, P., Arenou, F., Mignard, F., & Thévenin F. 2019, A&A, 623, A72

(ref: Kervella2020) Kervella, P., Arenou, F., & Schneider, J. 2020, A&A, 635, L14

(ref: Liseau2013) Liseau, R., Montesinos, B., Olofsson, G., et al. 2013, A&A, 549, L7

(ref: Liseau2015) Liseau, R., Vlemmings, W., Bayo, A., et al. 2015, A&A, 573, L4

(ref: Liseau2016) Liseau, R., De la Luz, V., O’Gorman, E., et al. 2016, A&A, 594, A109

(ref: Liseau2019) Liseau, R. 2019, arXiv e-prints, arXiv:1904.03043

(ref: Lisogorskyi2019) Lisogorskyi, M., Jones, H. R. A, & Feng, F. 2019, MNRAS, 485, 4804

(ref: Makarov2009) Makarov, V. V., Beichman, C. A., Catanzarite, J. H., et al. 2009, ApJL, 707, L73

(ref: Mamajek2008) Mamajek, E. E., & Hillenbrand, L. A. 2008, ApJ, 687, 1264

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., et al. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: Mezger1967) Mezger, P. G., & Henderson, A. P. 1967, ApJ, 147, 471

(ref: Monet2010) Monet, D. G., Jenkins, J. M., Dunham, E. W., et al. 2010, arXiv:1001.0305

(ref: Morel2018) Morel, T. 2018, A&A, 615, A172

(ref: Nsamba2019) Nsamba, B., Campante, T. L., Monteiro, M. J. P. F. G., et al. 2019, Frontiers in Astronomy and Space Sciences, 6, 25

(ref: Pourbaix2002) Pourbaix, D., Nidever, D., McCarthy, C., et al. 2002, A&A, 386, 280

(ref: Pourbaix2016) Pourbaix, D. & Boffin, H. M. J. 2016, A&A, 586,A90

(ref: Quarles2016) Quarles, B. & Lissauer, J. J. 2016, AJ, 151, 111

(ref: Quarles2018b) Quarles, B., & Lissauer, J. J. 2018, AJ, 155, 130

(ref: Quarles2018a) Quarles, B., Lissauer, J. J., & Kaib, N. 2018, AJ, 155, 64

(ref: Robrade2016) Robrade, J., & Schmitt, J. H. M. M. 2016, *T*he 19$^{th}$ Cambridge Workshop on Cool Stars, Stellar Systems and the Sun, Edited by G. A. Feiden, arXiv e-prints, arXiv:1612.06570

(ref: Sahlholdt2019) Sahlholdt, C. L., Feltzing, S., Lindegren, L., and Church, R. P. 2019, MNRAS, 482, 895

(ref: Sch80) Schwab, F. R. 1980, Proc. of the SPIE, 231, 18

(ref: Shibasaki2013) Shibasaki, K. 2013, PASJ, 65, S17

(ref: Soderblom2010) Soderblom, D. 2010, ARA&A, 48, 581

(ref: Spada2019) Spada F., & Demarque P. 2019, MNRAS, 489, 4712

(ref: Thevenin2002) Thévenin, F., Provost, J., Morel, P., et al. 2002, A&A, 392, L9

(ref: Trampedach2014) Trampedach, H., Stein, R. F., Christensen-Dalsgaard, J., et al. 2014, MNRAS, 445, 4366

(ref: Trifonov2020) Trifonov, T., Tal-Or, L., Zechmeister, M., et al. 2020, A&A, 636, A74

(ref: Trigilio2018) Trigilio, C., Umana, G., Cavallaro, F., et al. 2018, MNRAS, 481, 217

(ref: vandeKamp1977) van de Kamp, P. 1977, Vistas in Astronomy, 21, 289

(ref: vanLeeuwen07) van Leeuwen, F. 2007, Hipparcos, the New Reduction of the Raw Data: Astrophysics and Space Science Library, Volume 350. ISBN 978-1-4020-6341-1. Springer Science

(ref: Wagner2020) Wagner, K., Boehle, A., Pathak, P., et al. 2021, Nature Communications, 12, 922. doi:10.1038/s41467-021-21176-6 (ref: Yildiz2007) Yildiz, M. 2007, MNRAS, 374, 1264

(ref: Yildiz2008) Yildiz, M. 2008, MNRAS, 388, 1143

(ref: Yildiz2011) Yildiz, M. 2011, MNRAS, 412, 2571

(ref: Zhao2018) Zhao, L., Fischer, D. A., Brewer, J., et al. 2018, AJ, 155, 24

[^1]: <https://scipy.org>

[^2]: <https://www.astropy.org>

[^3]: <https://exoplanetarchive.ipac.caltech.edu/index.html> (cite: Akeson2013)

</paper>

Write the methods card for this paper.