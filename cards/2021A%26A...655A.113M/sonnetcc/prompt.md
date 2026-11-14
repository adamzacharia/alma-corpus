# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...655A.113M\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...655A.113M",
 "title": "EMISSA (Exploring Millimeter Indicators of Solar-Stellar Activity). I. The initial millimeter-centimeter main-sequence star sample",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Mohan, A.",
 "n_authors": 5,
 "arxiv_id": "2110.13339",
 "doi": "10.1051/0004-6361/202142095",
 "alma_projects_linked_by_archive": [
  "2012.1.00238.S",
  "2012.1.00385.S",
  "2013.1.00170.S",
  "2013.1.00359.S",
  "2013.1.00645.S",
  "2016.1.00441.S",
  "2016.A.00013.S",
  "2017.1.00698.S",
  "2017.1.01583.S",
  "2018.1.00470.S",
  "2018.1.01149.S"
 ]
}
```

Paper text:
<paper>
#  EMISSA - Exploring Millimeter Indicators of Solar-Stellar Activity

Due to their wide wavelength coverage across the millimeter to centimeter (mm – cm) range and their increased sensitivity, modern interferometric arrays facilitate observations of the thermal and non-thermal radiation that is emitted from different layers in the outer atmospheres of stars.

We study the spectral energy distribution ($S_\mathrm{obs}(\nu)$) of main-sequence stars based on archival observations in the mm – cm range with the aim to study their atmospheric stratification as a function of stellar type.

The main-sequence stars with significant detection in mm bands were identified in the ALMA Science Archive.

These data were then complemented with spectral flux data in the extreme ultraviolet (EUV) to cm range as compiled from various catalogues and observatory archives. We compared the resultant $S_\mathrm{obs}(\nu)$ of each star with a photospheric emission model ($S_\mathrm{mod}(\nu)$) calculated with the PHOENIX code.

The departures of $S_\mathrm{obs}(\nu)$ from $S_\mathrm{mod}(\nu)$ were quantified in terms of a spectral flux excess parameter ($\Delta S/S_{mod}$) and studied as a function of stellar type.

The initial sample consists of 12 main-sequence stars across a broad range of spectral types from A1 to M3.5 and the Sun-as-a-star as reference. The stars with $T_\mathrm{eff}$ $= 3000 - 7000$ K (F – M type) showed a systematically higher $S_\mathrm{obs}(\nu)$ than $S_\mathrm{mod}(\nu)$ in the mm – cm range. Their $\Delta S/S_{mod}$ exhibits a monotonic rise with decreasing frequency. The steepness of this rise is higher for cooler stars in the $T_\mathrm{eff}$ = 3000 – 7000 K range, although the single fully convective star ($T_\mathrm{eff}$ $\sim$ 3000 K) in the sample deviates from this trend. Meanwhile, $S_\mathrm{obs}(\nu)$ of the A-type stars agrees with $S_\mathrm{mod}(\nu)$ within errors.

The systematically high $\Delta S/S_{mod}$ in F – M stars indicates hotter upper atmospheric layers, that is, a chromosphere and corona in these stars, like for the Sun. The mm – cm $\Delta S/S_{mod}$ spectrum offers a way to estimate the efficiency of the heating mechanisms across various outer atmospheric layers in main-sequence stars, and thereby to understand their structure and activity. We emphasise the need for dedicated surveys of main-sequence stars in the mm – cm range.

# Introduction

The millimeter to centimeter (mm–cm) waveband ($\approx 10 -- 1000$ GHz) offers a unique but so far not systematically used way to explore the atmospheric structure of main-sequence stars. As the activity of a star is closely linked to the physical state and dynamics of the plasma in its atmospheric layers (cite: Noyes84_RHK; Pace13_RHK_Drastic_variability), the mm–cm waveband thus provides complementary means of assessing stellar activity. Because it is so far the only spatially resolved main-sequence star with a large wealth of data and because it consequently is the star we understand best theoretically, the Sun is a good template star that provides insight into the most relevant emission mechanisms in the mm – cm band. The results for the Sun may be transferred to other Sun-like stars of spectral type (FGK type) (cite: 2004NewAR..48.1319W) with possible implications for a wider range along the main sequence.

In the Sun, the mm continuum ($\approx$ 30 – 1000 GHz) is primarily produced by thermal free-free emission,

whereas non-thermal contributions are only expected to become significant under extreme conditions like strong magnetic field enhancements and flares. The height of the layer above the photosphere from which the continuum emission originates increases with decreasing observing frequency (cite: 2016SSRv..200....1W). Like for the Sun, the emission in the mm–cm waveband can be expected to originate primarily from different (optically thick) atmospheric layers at different heights in the chromosphere to transition region in Sun-like stars (FGK type).

A recent study of $\alpha$ Cen A&B (G2V & K1V) across 17 – 600 GHz revealed a brightness temperature $T_\mathrm{B}(\nu)$ for both stars that decreased with frequency and is thus consistent with a chromospheric temperature rise as expected for these spectral types (cite: 2018MNRAS.481..217T).

For high-mass main-sequence stars (OBA type), the outer atmospheric structure is expected to be quite different from that of Sun-like stars. It is expected that the average temperature rise as seen in the chromosphere and corona of Sun-like stars is absent in high-mass stars.

This is primarily because unlike Sun-like stars, OBA stars are not expected to have an outer convection zone that generates and drives dynamic phenomena

that play a vital role in generating the hot outer atmospheric layers in Sun-like stars (cite: Donati09_Rev_Bfield). Observations of $\alpha$ CMa (A1V) (cite: 2019ApJ...875...55W) and $\alpha$ PsA (cite: 2016ApJ...818...45S) (A4V) show indeed no significant chromospheric emission. Rather, the mm flux as observed with the Atacama Large Millimeter/submillimeter Array (ALMA)

seems to be consistent with purely photospheric emission

(cite: 2019ApJ...875...55W).

Using the Rayleigh-Jeans approximation, the spectral flux density, $S_\nu$, can be converted into the brightness temperature $T_\mathrm{B}$, as described by $$\begin{equation}
S_\nu = \frac{2\ k\ T_B\ \nu^2}{c^2}\ \Omega_s \quad,
\end{equation}$$ where $k$ is the Boltzmann constant and $\Omega_s$ is the solid angle subtended by the star. The latter is given as $\Omega_s = \pi R_*^2/D^2$, where $R_*$ is the radius of the star and $D$ is the distance to it. Because the emission primarily originates from optically thick layers in the mm range, the brightness temperature spectrum, $T_\mathrm{B}(\nu)$, is closely related to the temperature in the continuum-forming layer at a height $z\,(\nu)$ in the atmosphere. Consequently, the observable brightness temperature spectrum ($T_B\,(\nu)$) is a proxy to the atmospheric temperature stratification, $T\,(z\,(\nu))$ (cite: 1981ApJS...45..635V). Systematic mm – cm observations of main-sequence stars of different spectral types and ages

will therefore provide important constraints for the evolution of stellar atmospheric structure and activity.

Comparing these observations with magnetic field properties will help to better understand the connection between atmospheric structure, activity, and magnetic field as predicted by various models (cite: 1996ApJ...457..340K; 2018ApJ...862...90G) and inferred from multi-parameter studies of stars in different surveys (cite: Donati09_Rev_Bfield; Vidotto14_B_Vs_age_n_rot; Lund20_stelar_helicity; 2020AJ....160..219F).

However, only a few main-sequence stars have been detected in the mm – cm range so far compared to the wealth of detections in the IR to X-ray range.

The low detection rate so far is a direct consequence of the low

expected flux densities of even the nearest Sun-like stars, which are lower than $\sim 100$ $\mathrm{\mu}$Jy (1 Jy $= 10^{-26}\,$Wm$^{-2}$Hz$^{-1}$) in mm bands and well below 100 $\mathrm{\mu}$Jy at cm wavelengths (cite: 2004NewAR..48.1319W). A reliable detection at a single frequency therefore requires an instrument capable of providing a sensitivity of about a few tens of $\mu$Jy within a reasonable integration time of a few hours at most and over a spectral bandwidth of typically $\sim$10 GHz.

In addition, a significant fraction of main-sequence stars belong to binary systems with separations that can be as small as a few arcseconds and/or have debris disks with an inner edge close to the star (cite: 2014ApJ...788L..37G; 2007ApJ...655L.109M; 2007ApJ...658..584L).

An example of the former case is the $\alpha$ Cen A&B

system at a distance of 1.3 pc with an angular separation of just 4$^{\prime\prime}$ (cite: 2016A&A...594A.109L). $\epsilon$ Eri

at a distance of 3.2 pc is an example of a star with a debris disk that has an inner edge at $\sim10^{\prime\prime}$ from the star.

Consequently, in order to measure the stellar flux without contamination from a companion or a disk, the angular resolution of an observation must be high enough to separate the star from these potential components.

The required angular resolution for observations in the mm – cm bands warrants the use of interferometric arrays.

Because it is the most sensitive telescope with the largest number of baselines and a large collecting area in mm bands, ALMA[^1] is currently the only telescope that meets the requirements in the mm range.

In the cm bands, the Australia Telescope Compact Array[^2] (ATCA) and the Expanded Very Large Array (JVLA, (cite: Perley11_EVLA)) are examples of new-generation arrays that can provide such data.

Most of the studies of main-sequence stars in radio wavebands used frequencies below 10 GHz so far, much of which have been on active M dwarfs (cite: 2002ARA&A..40..217G). This is because the flares, especially in active M dwarfs and Sun-like stars, cause coherent radio emissions brighter by several orders of magnitude than the background free-free emission at low radio frequencies (cite: 1994SSRv...68..261B; Lim96_Proxima_ATCA; 2018ApJ...856...39C; 2019ApJ...871..214V; 2020MNRAS.494.4848D; Zic20_typeIV_ProximaCen). At high frequencies, the flaring rates are low and the emission $T_\mathrm{B}$ is also much lower, requiring sensitivity limits that are hard to achieve with earlier-generation arrays even for the nearby stars (cite: 1990SoPh..130..265B; 2004NewAR..48.1319W).

However, a few M dwarfs were detected close to 10 GHz by the VLA, namely UV Cet and EV Lac (cite: 2005ApJ...621..398O; 2006astro.ph..9389G). More recently, the quiescent and flare emission from the nearby M dwarf Proxima Cen was studied with ALMA (cite: AngladaEscude12; MacGregor18_proxima_flares; 2021ApJ...911L..25M). (cite: Villadsen14_First_detect_SLS_inRadio_VLA) presented the first detection of thermal emission in the cm band using JVLA from Sun-like stars, $\tau$ Cet, $\eta$ Cas A, and 40 Eri A. $\tau$ Cet was also observed with ALMA by (cite: 2016ApJ...828..113M), but the emission was partly contaminated by the edge-on disk emission. Using high-resolution ALMA observations, (cite: 2017MNRAS.469.3200B) were able to distinguish the emission from the K-dwarf $\epsilon$Eri from its debris disk unlike the IR-band observations of the star (cite: 2015A&A...576A..72L; ChavezDagostino16). (cite: Bastian18_EpsEri), (cite: 2019ApJ...871..172R), and (cite: suresh20_EpsEri_RadioSEDmodel) extended this up to 2 GHz using the EVLA. The closest binary system $\alpha$ Cen A&B is another repeatedly observed pair of stars that has been observed across all available bands of ALMA, except band 10. The observations were carried out during two different observing cycles separated by 2 yr (cite: 2013A&A...549L...7L; 2015A&A...573L...4L; 2016A&A...594A.109L; 2019arXiv190403043L).

A recent study by (cite: 2021AJ....162...14A) at $\approx$ 340 GHz reported similar flux for the binary stars as (cite: 2016A&A...594A.109L). (cite: 2018MNRAS.481..217T) modelled the mm – cm spectrum of $\alpha$ Cen A&B using various scaled solar atmospheric models and demonstrated the existence of a solar-like chromosphere that becomes hotter with increasing distance from the surface. The authors also added 17 GHz flux data points from ATCA to the existing spectra. Following a similar modelling approach as (cite: White20_MESAS), they modelled their observations of F-type stars, $\gamma$ Lep and $\gamma$ Vir A& B, at $\approx$ 233 and 344 GHz. Other F dwarfs that have reliable detection in the mm band are 61 Vir (cite: 2017MNRAS.469.3518M) and $\eta$Crv (cite: 2017MNRAS.465.2595M). Of the more massive stars, the closest A-type stars, $\alpha$ CMa and $\alpha$ PSa, are the most frequently studied. The former was studied across the $\approx$30 – 210 GHz range and the spectrum was modelled by (cite: 2019ApJ...875...55W). The latter garnered more interest primarily due to its circumstellar disk, which was well resolved with ALMA (cite: 2016ApJ...818...45S; 2017MNRAS.466.4201W; 2017ApJ...842....8M; 2017ApJ...842....9M).

We present an initial version of a database of mm – cm fluxes for main-sequence stars detected by ALMA supplemented with other observations from the extreme ultraviolet (EUV) to the radio band. The Sun is included as a fundamental reference. The resulting observed spectral energy distribution (SED) for each star is then compared to the SED calculated with the PHOENIX model (cite: 1999JCoAM.109...41H) to reveal possible chromospheric contributions. The method and initial data set are described in Sect. [2](#sec:method). The resulting SEDs and and $T_\mathrm{B}(\nu)$ are presented in Sect. [3](#sec:analysis). Section [4](#sec:discussion) presents the inferences from a comparison of the model and observed SEDs for stars of different types, followed by our conclusions and outlook in Sect. [5](#sec:conclus).

# Method and data sets

![](sirius_imgs.pdf)

[TABLE]

| **ID** | **SIMBAD ID** | **Age** | **B-V** | **Vsini** | **L$_\mathrm{bol}$** | **Log R$^\prime_\mathrm{HK}$** | **Log L$_\mathrm{X}$** | **Log R$_\mathrm{X}$** | **\|B$_\mathrm{lon}$\|** | **Period** | **R$_\mathrm{o}$** |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| 3-6 |  | Myr |  | km/s | L$_\odot$ |  | erg/s |  | G | d |  |
| A | Alf CMa | 242 \[43\] | 0.0 \[5\] | 16 \[45\] | 25.4 \[44\] | – | 28.82 \[58\] | – | – | 5.37\[\*\] | – |
| B | Alf PsA | 400 \[46\] | 0.094 \[5\] | 93 \[37\] | 16.63 \[36\] | – | – | – | – | 1 \[\*\] | – |
| C | Gam Vir A | 1140 \[23\] | 0.36 \[34\] | 36 \[60\] | 4.37 \[60\] | -4.4789 \[50\] | 29.03 \[63\] | -5.21 \[63\] | 15.5$\pm$10.2 \[20\] | 2.04 \[\*\] | – |
| D | Gam Vir B | 1140 \[23\] | 0.36 \[59\] | 23 \[60\] | 4.63 \[60\] | -4.2984 \[50\] | 29.03 \[63\] | -5.24 \[63\] | 21$\pm$16 \[20\] | 3.19 \[\*\] | – |
| E | Eta Crv | 1012 \[22\] | 0.38 \[24\] | 68 \[39\] | 4.679 \[48\] | -4.959 \[23\] | 28.68 \[18\] | -5.62 \[23\] | – | 1.1 \[\*\] | – |
| F | Gam Lep | 1300 \[57\] | 0.5 \[24\] | 10 \[40\] | 2.291 \[41\] | -4.77 \[11\] | 28.3 \[13\] | -5.71 \[23\] | – | 6 \[41\] | – |
| G | Alf Cen A | 4850 \[30\] | 0.71 \[16\] | 2.7 \[31\] | 1.519 \[30\] | -5.059 \[16\] | 27.7 \[13\] | -6.96 \[\*\] | 28.7 \[\*\] | 22 \[31\] | 2.223 \[\*\] |
| H | 61 Vir | 6300 \[47\] | 0.709 \[16\] | 3.9 \[27\] | 0.821 \[42\] | -5.04 \[16\] | 26.87 \[13\] | -6.9 \[10\] | 30.6 \[\*\] | 12.8 \[27\] | 2.186 \[\*\] |
| I | Alf Cen B | 4850 \[30\] | 0.85 \[26\] | 1.1 \[31\] | 0.5 \[30\] | -4.94 \[33\] | 27.06 \[10\] | -6.61 \[\*\] | 51.8 \[\*\] | 36 \[32\] | 1.989 \[\*\] |
| J | Eps Eri | 400 \[15\] | 0.881 \[2\] | 2.4 \[57\] | 0.381 \[14\] | -4.51 \[2\] | 28.32 \[8\] | -4.78 \[8\] | 8.3$\pm$4.9 \[20\] | 11.8 \[21\] | 0.366 \[8\] |
| K | GJ 2006 A | 6 \[35\] | 1.5 \[6\] | 6.2 \[7\] | 0.046 \[14\] | – | 29.53 \[7\] | -2.68 \[9\] | – | 3.94\[19\] | – |
| L | Proxima Cen | 4850 \[30\] | 1.82 \[65\] | 2.7 \[66\] | 0.003 \[14\] | –4.29 \[67\] | 26.82 \[68\] | -3.98 \[68\] | 200 \[69\] | 89.8\[69\] | 0.63 \[69\] |
| S |  | 4600 \[21\] | 0.65 \[52\] | 1.7 \[21\] | 1 | -4.9$^{+0.15}_{-0.2}$ \[53\] | 27.2$_{-0.61}^{+0.39}$ \[55\] | -6.39$^{+0.61}_{-0.49}$ \[56\] | 5 | 25 \[21\] | 2 |

| **ID** | **SIMBAD ID** | **ALMA Obs. frequency** | **Other bands** | **Refs** | **$\beta$** |
|:--:|:--:|:--:|:--:|:--:|:--:|
| 3-4 |  | (GHz) | Array: (GHz) |  |  |
| A | Alf CMa | 94, 106, 144,156 196, 210 | VLA: 33, 45; GBT: 90 | 11 | 1.8$^*$ |
| B | Alf PsA | 233, 344 | — | 9 | 2.07$^*$ |
| C | Gam Vir A | 233, 344 | — | 1 | 1.87$^*$ |
| D | Gam Vir B | 233, 344 | — | 1 | 1.87$^*$ |
| E | Eta Crv | 341 | — | 10 | — |
| F | Gam Lep | 232, 345 | — | 1 | 1.87$^*$ |
| G | Alf Cen A | 98, 145, 233, 344, 405, 679 | ATCA: 17 | 3, 4 | 1.76$^3$ |
| H | 61 Vir | 341 | — | 2 | — |
| I | Alf Cen B | 98, 145, 233, 344, 405, 679 | ATCA: 17 | 3, 4 | 1.71$^3$ |
| J | Eps Eri | 228 | VLA: 6, 10, 15, 33; ATCA: 44 | 5, 6 7, 8 | — |
| K | GJ 2006 A | 341 | — | — | — |
| L | Proxima Cen | 233 | – | 12 | — |
| S | Sun | 92-108, (190-206), 229-249, (339-355) | VLA: 10; NoRH: 17, 34 | 13, 14 | – |

In this section, we will first describe the compilation of ALMA detected stellar sample and the subsequent search for their flux densities reported at different frequencies. We will then present the derivation of their expected flux densities across the electromagnetic spectrum using a photospheric emission model. The model flux densities are compared with the observed values by defining a suitable parameter.

## Compilation of the initial stellar sample

### Archival data in the mm–cm band ($\approx$ 10 – 1000 GHz)

As a starting point for the ALMA main-sequence star sample, the ALMA Science Archive[^3] was searched for significant detections of main-sequence stars.

A detection was deemed significant if (i) the flux density of the target star was beyond at least three times the root mean square (RMS) flux of the background sky in the image, and (ii) there was no nearby or background source within the synthesised beam or close enough to contaminate the observed stellar flux.

The primary criterion for a significant detection placed a strong constraint on the distance to the stars, making it a collection of nearby main-sequence candidates. We refer to Sect. [4.3](#sec:disc_samplesize) for a discussion of the current limitations of the sample size and future possibilities to expand it.

ALMA observations are generally classified under various science categories[^4] according to their intended primary scientific goal. Here, data sets under the following categories were searched for detectable main-sequence stars: ‘Debris disks’, ‘Exoplanets’, ‘Disks around low-mass stars’, ‘Disks around high-mass stars’, and ‘Main-sequence stars’. In total, publicly available data sets for 104 main sequence stars were identified. From these, 8 stars with unknown spectral type or luminosity class and 4 stars in spectroscopic binaries were removed. This led to a reduced sample of 92 stars. The various observed and derived physical information of these stars was tabulated using an automated search routine written in Python, which queried the Vizier and SIMBAD databases.

After this preliminary sample was ready, the first-look images of these stars from the various observation campaigns were downloaded from the ALMA Virtual Observatory (VO) through the Japanese Virtual Observatory[^5] (JVO) website. The signal-to-noise ratio (S/N) of each image was noted, and those with a significant stellar detection were downloaded. Out of the 92 candidate stars, data for many were found to have contamination from nearby sources, which was visible from the shape of the stars, which was significantly different from that of the synthesised beam. In many other cases, there was either no detection of the star itself or data were poor. The final sample of stars with a significant detection in at least one ALMA band consists of 12 sources. The sample is complete for ALMA data that are publicly made available through JVO until 31 December 2020 since the beginning of observations. Figure [1](#fig:Sirius_imgs) shows a sample collage of JVO-supplied ALMA images of $\alpha$ CMa (Sirius A).

The flux densities of different ALMA bands for each star were determined by fitting a two-dimensional Gaussian function to each image downloaded from the JVO. A detailed search in the VLA data archive [^6] was also carried out to identify archival data sets for the stars in the sample. All the identified data sets were imaged using an automated pipeline that we developed based on routines in Common Astronomy Software Applications (CASA; (cite: casa)). Every sample star except for GJ 2006 A was found to have publications using at least a few of the mm – cm band detections we found from the archival search.

ALMA flux values from publications were preferred over values derived from JVO images because the latter are based on a standard pipeline, while flux values in publications are typically the result of more refined data-processing optimised for an individual star. However, the published fluxes from stellar observations with the VLA match our pipeline values quite well. A few stars had published ATCA observations as well, which are incorporated in our database.

### Archival data at higher frequencies

The 10 – 1000 GHz band information (see Sect. [2.1.1](#sec:archive_radiomm)) were complemented with data at higher frequencies ranging from the infrared (IR) to the EUV. For this purpose, the Strasbourg Data Centre[^7] (CDS)

was searched for each star in the sample. When provided the RA and DEC of a target source and a search radius, the CDS server looks for sources detected within the radius across the different astronomical catalogues and reports their fluxes as a function of frequency. We used this tool to obtain the SEDs of the stars of interest. A caveat in this procedure is the choice of an optimal search radius. CDS by default sets a radius of 5$^{\prime\prime}$. Three criteria that determine this choice are the source density in the region of interest, the presence of known associated sources of emission, such as binary companions and disks near the stars of interest, and to have sufficient data points in the SED given the typical pointing offsets of various telescopes.

The default search radius of $5^{\prime\prime}$ is well justified considering all three aforementioned criteria for all pre-selected stars except for $\gamma$ Vir A&B, which are separated by just 2$\stackrel {\prime \prime}{_{\bf \cdot}}$6 (cite: 1999A&A...341..121S) or less, depending on the time of observation during the past decades.

Most of the data points provided by CDS were obtained with instruments with an angular resolution $\gtrsim 2^{\prime\prime}$. Especially in the far-IR bands ($\sim 10^3 - 10^4$ GHz), the data were obtained with instruments at a resolution $>5^{\prime\prime}$. For instance, Spitzer (MIPS[^8] ) offers resolution 6$^{\prime\prime}$, 20$^{\prime\prime}$, and 40$^{\prime\prime}$ at wavelengths of 24 $\mu$m, 70 $\mu$m, and 160 $\mu$m (corresponding to frequencies of $\approx 12.5$ THz, 4.3 THz, and 1.8 THz), respectively. The surveys at frequencies between $\approx 10^4$ – $4\times 10^5$ GHz, namely 2MASS[^9] and Spitzer (cite: 2004ApJS..154...10F), offer $\approx$ 2 – $\mbox{2$\stackrel {\prime \prime}{_{\bf \cdot}}$5}$ pixel scales. As a result, flux contamination is inevitable in the CDS SED data for $\gamma$ Vir A and B at frequencies below $10^5$ GHz. However, for frequencies above $5\times 10^5$ (optical to UV), the angular resolution of the available data, which mostly stems from catalogues like Gaia (cite: Gaia18_DR2_catalog), is about a few to sub-arcseconds. Consequently, we used a CDS search radius of size $\mbox{1$\stackrel {\prime \prime}{_{\bf \cdot}}$5}$ for both $\gamma$ Vir A & B and then corrected the fluxes in the range from $\nu = 10^3$ GHz to $\nu =  5\times 10^5$ GHz. For this frequency range, it is assumed that both stars contribute to the measured fluxes. Separate fluxes for $\gamma$ Vir A and B were then derived according to the ratio of their $T_\mathrm{eff}$ values as obtained from (cite: Soubiran16_Ref3) (see Table [\[tab:prop\]](#tab:prop)). Details of the SED data processed by this approach are discussed in detail in the following section.

## PHOENIX model atmospheres

A one-dimensional local thermal equilibrium (LTE) model atmosphere and the corresponding synthetic spectrum were calculated for each star in the sample using the PHOENIX code (cite: 1999JCoAM.109...41H) with the model grid taken from (cite: 2013A&A...553A...6H) as the starting points with current spectral line and thermodynamic data. For the stellar parameters, rounded literature values were used (see Sect. [\[sec:results\]](#sec:results)). The model atmospheres feature a photosphere in radiative + convective equilibrium for the stellar parameters using the current production version of PHOENIX (version 18.05). Consequently, none of the models includes a chromospheric temperature rise. The synthetic spectrum covers a wavelength range from 0.01 nm to 3.0 cm, corresponding to frequencies from $3.0\,10^{10}$ to 10 GHz. Towards the lower frequencies, the synthetic SEDs ($S_\mathrm{mod}\,(\nu)$) follow the Rayleigh-Jeans tail. In this study, the PHOENIX spectra are compared to the observed SEDs, which will then expose additional contribution due to a chromosphere and/or possible circumstellar disks (see Sect. [\[sec:results\]](#sec:results)). The resulting SEDs are presented in Fig. [2](#fig:SED_fits).

All considered stars were compared to corresponding PHOENIX models that do not include a chromospheric temperature rise. Deviations between the PHOENIX model SED ($S_\mathrm{mod}(\nu)$) and the observed values ($S_\mathrm{obs}(\nu)$) are discussed with the help of the *spectral flux excess* parameter, which is defined as $$\begin{equation}
    \Delta S(\nu)/S_\mathrm{mod} = \frac{S_\mathrm{obs}(\nu)- S_\mathrm{mod}(\nu)}{S_\mathrm{mod}(\nu)} \ . 
    \label{Eqn:DelS}
\end{equation}$$ A significant spectral flux excess in the mm – cm range would potentially indicate a chromospheric temperature rise because the

PHOENIX model lacks atmospheric layers above photosphere.

![](SED_paper1_V3.pdf)

![](SED_paper2_V3.pdf)

![image](SED_paper3_V3.pdf) ![image](SED_paper4_V3.pdf) ![image](SED_paper5_V3.pdf)

# Results

![](p21emissa1_hrd.pdf)

The resulting initial ALMA main-sequence star sample is comprised of 12 stars that satisfy our selection criteria plus the Sun as a reference star. A future expansion of this list is foreseen (see Sect. [4.3](#sec:disc_samplesize)). Figure  [3](#fig:hrd) presents the covered parameter ranges across the main sequence and stellar age versus mass. An overview of the physical parameters and activity indicators for each star in the sample and the Sun is given in Table [\[tab:prop\]](#tab:prop)-[\[tab:activityprops\]](#tab:activityprops). In Table [\[tab:Radio_band_info\]](#tab:Radio_band_info), the observation frequencies in the mm – cm range are presented for which reliable data exist for each star. For the stars with reliable flux estimates $S_\mathrm{obs}(\nu)$ at more than one frequency, a spectral index, $\beta$ was computed, assuming $S_\mathrm{obs}(\nu)$ $\propto \nu^{\,\beta}$.

The results of this analysis for each star are discussed here starting with our template star, the Sun.

## Sun as a star.

The Sun is an intermediate-age ($\approx$ 4.6 Gyr) main-sequence G2V star with an effective photospheric blackbody temperature of 5772 K (cite: 2014MNRAS.444.3517M). The Sun has an activity cycle of 11 yr and a (equatorial) rotation period of about 25 days. The $R^\prime_\mathrm{HK}$ index of the Sun is known to fluctuate by about 60% during its activity cycle (see Table [\[tab:activityprops\]](#tab:activityprops)). This level of fluctuation is common for a star at the age of the Sun, as demonstrated by (cite: Pace13_RHK_Drastic_variability).

![](Sunasstar.pdf)

Despite the wealth of data across spectral bands, still comparatively little data are available in mm – cm bands. The full-disk averaged SED data in the spectral range from $\approx 10^3$ GHz to $2\times 10^6$ GHz ($\approx 150$ nm – 0.5 mm) for the Sun shown in Fig. [4](#fig:SolarSED_fits) are taken from (cite: Thekaekara69). Despite being a relatively old SED data set, it provides data over a very wide spectral range compared to other more recent data sets. Using an archival solar irradiance data set compiled over several decades, (cite: 2019E&SS....6.2525C) found that the relative variance in the spectral irradiance is lower than 0.1% in the spectral range from $400$ – 2000 nm and lower than 0.7% in the 200 – 400 nm range. Consequently, the spectrum provided by (cite: Thekaekara69) still serves as a valid reference for the disk-averaged solar photospheric spectrum.

(cite: 2017SoPh..292...88W) provided the fluxes based on ALMA total power solar maps in bands 3 and 6, that is, at 92-108 and 229-249 GHz, respectively.

Fluxes at $\nu < 30$ GHz were estimated based on the disk-averaged fluxes computed by (cite: 2004NewAR..48.1319W) using archival data from the Nobeyama Radio Heliograph[^10]. The author provided a Sun-as-a-star spectrum for the maximum and minimum phases of the solar activity cycle based on data collected during December 2001 and May 1996, respectively. The data presented in Fig. [4](#fig:SolarSED_fits) are mean values computed from the two phases, and the bars mark the flux range arising from variations, within $\sim$ 1 – 20%, due to solar activity. Updated fluxes for the Sun at millimeter wavelengths will be addressed in a forthcoming paper in this series. The lower subplot of Fig. [4](#fig:SolarSED_fits) shows the spectral flux excess, $\Delta S/S_{mod}$, for the Sun as a star. The PHOENIX model for the Sun is overlaid.

$\Delta S/S_{mod}$ steadily increases with decreasing frequency in the mm – cm band, while it remains relatively close to 0 at high frequencies between 10$^3$ GHz and 10$^6$ GHz, where the emission primarily originates from the photosphere. The rise in spectral flux excess with decreasing frequency in the mm – cm range indicates that these frequencies are sensitive to atmospheric layers of varying heights above the photosphere, extending across the chromosphere to corona. The solar observations in the sub-mm – far-IR range ($\approx$ 300 – 10$^4$ GHz) show that the solar spectrum has a $T_\mathrm{B}$ minimum of $\approx$ 4100 K at $\sim \nu \approx$ 2000 GHz ($\sim 150~\mu$m) (cite: 1981ApJS...45..635V; 1997ApJ...484..960G). The early millimeter observations were mostly solar fluxes measured at the disk centre or scans across the disk centre. In some cases, these measurements were obtained with airborne instruments. However, these measurements had significant uncertainties compared to modern interferometric observations. The average flux values derived from measurements for which only parts of the Sun and not the full disk were observed would have been more susceptible to contributions from structures on the solar surface during the observation time. In this work, we compiled only data from more sensitive mm – cm band interferometric observations and full-disk scans/total power maps (cite: 2017SoPh..292...88W).

## Stellar sample

Short descriptions of the individual stars are provided below. The stars are presented in the decreasing order of their $T_\mathrm{eff}$.

![image](Tb_profile_V2_p1_log.pdf) ![image](Tb_profile_V2_p2_log.pdf)

#### A — $\alpha$ CMa (Sirius A, HD 48915A)

is a main-sequence star of spectral type A0 and part of a binary system. The companion is a white dwarf (spectral type DA). Sirius is observed spatially separated from its companion at $\approx$ 6$^{\prime\prime}$ – 8$^{\prime\prime}$ (cite: 2017ApJ...840...70B), and with a distance of 2.6 pc, it is one of the closest stars to the Sun. It has an age of 242 Myr and a mass of 2.15 M$_\odot$. Available ALMA observations cover bands 3, 4, and 5 (see Table [\[tab:Radio_band_info\]](#tab:Radio_band_info)).

The SED at mm wavelengths (see Fig. [2](#fig:SED_fits) top right panel for $\nu< 300$ GHz) is well reproduced with the PHOENIX model, which confirms the results by (cite: 2018ApJ...859..102W). Like the flux values, the corresponding $T_\mathrm{B}$values (see Fig. [5](#fig:tbprofile)) can also be explained with a temperature stratification that features a monotonic decrease with height, as already demonstrated by (cite: 2018ApJ...859..102W). As expected for an A0 star, there is no indication of a chromospheric temperature rise. The $T_\mathrm{B}$data indicate some potential deviation from a monotonic temperature stratification between $\sim40$ GHz and $\sim80$ GHz in the form of an unexpected dip, but more flux data are needed before firm conclusions can be drawn.

#### B — $\alpha$ PsA (Fomalhaut, HD 216956)

is an A4V star situated at a distance of 7.7 pc. It has a mass of 1.97 M$_\odot$ and an age of 0.44 Gyr. $\alpha$ PsA forms a trinary system with HD 216803 and the distant LP 876-10, both more than a few degrees away (cite: Mamajek13_fomalhaut_3rd_companionDiscovery). ALMA has resolved the thick elliptical debris ring around $\alpha$ PsA. The inner edge of the closest ring to the star is located at about 3$^{\prime\prime}$ away from the star (cite: 2017ApJ...842....8M). The ring has a thickness of $\sim$ 2$^{\prime\prime}$. The available ALMA observations are in bands 6 and 7. These two data points (see frequencies lower than 400 GHz in Fig. [2](#fig:SED_fits) and Fig. [5](#fig:tbprofile)) match the fluxes (and $T_\mathrm{B}$) predicted by the PHOENIX model. An increased flux is found between 400 GHz and $<10$ THz. These data come from the HERSCHEL SPIRE spectrograph, which has a resolution of $\approx$ 20$^{\prime\prime}$. So the observed flux excess could be attributed to contamination from the debris disk. However, 70 $\mu$m Herschel PACS image of the star with an angular resolution of $\mbox{5$\stackrel {\prime \prime}{_{\bf \cdot}}$6}$ could barely distinguish the emission from outer regions of the debris ring, despite the contamination to starlight from the inner regions (cite: 2012A&A...540A.125A). As expected for an A-star, the SED for $\alpha$ PsA does indicate the lack of a chromosphere and thus no temperature increase in the outer layers.

#### C+D — $\gamma$ Vir A & B (HD 110379, HD 110380)

are two very similar F0V stars forming a close binary system at a distance of 11.62 pc. Almost all their important physical properties match within the respective measurement errors. Their binary orbit is inclined at 148$^\circ$, has a semi-major axis extent of $\mbox{3$\stackrel {\prime \prime}{_{\bf \cdot}}$68,}$ and a period of $\approx$ 169 days (cite: 1999A&A...341..121S). During the ALMA observations in bands 6 and 7, the relative separation of the two stars was $\approx$ $\mbox{2$\stackrel {\prime \prime}{_{\bf \cdot}}$6}$, so that they were resolved (cite: White20_MESAS). However, as mentioned in Sect. [2.1.2](#sec:archive_highfreq), the binary separation of $\gamma$ Vir A&B is either smaller than or comparable to the angular resolution scale of various instruments or surveys providing data to CDS, so that only the combined flux of both stars is measured. The individual fluxes for A and B, which were here derived according to their $T_\mathrm{eff}$ ratio in the IR/optical range, agrees well with the PHOENIX models (see Fig. [2](#fig:SED_fits)).

Because ALMA separates the two stars well, individual fluxes and corresponding brightness temperatures were derived for the two observed bands. For both stars, the ALMA fluxes significantly exceed the fluxes predicted by the PHOENIX model. The corresponding brightness temperatures exceed 8000 K for $\gamma$ Vir A and 7000 K for $\gamma$ Vir B, which is in line with chromospheric temperatures expected for F-type stars (see Fig. [5](#fig:tbprofile)). However, it is important to emphasise that uncertainties for the stellar radii, effective temperatures, and to a lesser extent, for their distance, result in a notable flux uncertainty, we show in Fig. [5](#fig:tbprofile) and Fig. [6](#fig:DS_by_S_spectrum). In this case, further observations at higher and lower frequencies are also required to determine the average temperature stratification and the properties of a temperature minimum therein.

#### E — $\eta$ Corvi (HD 109085)

is an F2V type star at a distance of 17.96 pc with a mass of 1.48 M$_\odot$ and an age of 1.01 Gyr. The star possesses a disk with a semi-major axis width of $\approx$ 17$^{\prime\prime}$, which is well resolved by ALMA in band 7. A detailed modelling of the observed stellar SED assuming multi-thermal emission contributions from the photosphere and a variety of possible hypothetical cold debris disks and rings was carried out by (cite: 2014ApJ...784..148D). The $\Delta S/S_{mod}$ plot for $\eta$ Corvi shown in Fig. [2](#fig:SED_fits) indicates excess flux between 1 – $10$ THz. These data come from HERSCHEL SPIRE observations with an angular resolution of about $20^{\prime\prime}$. This should hence be contaminated by the disk emission. In addition to the outer disk, (cite: 2014ApJ...784..148D) also argued for the existence of an inner disk within $\mbox{0$\stackrel {\prime \prime}{_{\bf \cdot}}$6}$ to explain the excess flux observed in the SED at 70 $\mu$m ($\nu \approx$ 4300 GHz). However, the contribution from this proposed inner ring to the observed flux is expected to fall below the stellar contribution in the ALMA bands. The ALMA observations resolve the extended outer disk structure from the star quite well. The flux measured with ALMA at 341 GHz, on the other hand, is well reproduced with the PHOENIX model, as is shown by $\Delta S/S_{mod}$ ($\nu=341\,\mathrm{GHz}$) $\approx\,0$ in Fig. [2](#fig:SED_fits). While this finding implies that no chromospheric temperature rise is detected at this frequency, no firm conclusions regarding a potentially existing chromosphere or a lack thereof can be drawn without additional measurements at lower frequencies.

#### F — $\gamma$ Lep (HD 38393)

is an F6V type star at a distance of 8.97 pc with a mass of 1.22 M$_\odot$ and an age of 1.3 Gyr. It has a companion at a distance of about 100$^{\prime\prime}$ (cite: White20_MESAS). ALMA observations are available in bands 6 and 7 and provide fluxes that are higher than those predicted by the PHOENIX model. The $\Delta S/S_{mod}$ plot in Fig. [2](#fig:SED_fits) shows that the deviation from the PHOENIX model increases slightly with decreasing frequency below $\nu \sim 400$ GHz. Despite the involved uncertainties, this trend could be interpreted as an indication for a chromospheric temperature rise in $\gamma$ Lep, as would be expected for an F6V type star. This is also seen in the $T_\mathrm{B}(\nu)$ in Fig. [5](#fig:tbprofile). However, additional observations at frequencies below 230 GHz (e.g. in band 3) are needed in order to reliably investigate the thermal stratification of a potentially existing chromosphere.

#### G — $\alpha$ Cen A (HD 128620J)

is of spectral type G2V at a distance of 1.35 pc with a mass of 1.11 M$_\odot$ and an age of 4.85 Gyr. It has a binary companion, $\alpha$ Cen B, in an orbit with a semi-major axis width of $\mbox{17$\stackrel {\prime \prime}{_{\bf \cdot}}$8}$ and a period of 80 years. The $\alpha$ Cen A&B system was proposed to host a thin disk with a semi-major axis $\approx 4^{\prime\prime}$ based on the observed excess flux density at 24 $\mu$m (cite: Wiegert14). However, the sub-mm/mm observations in ALMA bands 3, 4, 6, 7, 8, and 9 (ALMA observation cycle 2; C2) presented by (cite: 2015A&A...573L...4L) and (cite: 2016A&A...594A.109L), and the ATCA observations presented by (cite: 2018MNRAS.481..217T) showed no signs of a circumbinary disk. The ALMA C2 observations had a flux calibration issue that was corrected by (cite: 2019arXiv190403043L), who also presented a new set of observations (Cycle 4; C4) across all the ALMA bands in which the star was previously detected. The C4 observations performed during 2017 showed that the flux of the star increased since the C2 observations in 2014. The resulting time-averaged SED at $\nu < 10^3$ GHz deviates from the PHOENIX model, with $\Delta S/S_{mod}$ increasing with decreasing frequency (see Fig. [2](#fig:SED_fits)). The bars on the ALMA data points correspond to the variation in the observed flux between C2 and C4 data. The ATCA flux at 17 GHz is consistent with this trend, which is indicative of a chromospheric temperature rise in this G-type star (cite: 2018MNRAS.481..217T).

By comparing and complementing their ALMA measurements with brightness temperatures derived from single-dish observations (cite: 2013A&A...549L...7L), already (cite: 2015A&A...573L...4L) and (cite: 2016A&A...594A.109L) clearly showed a chromospheric temperature increase and a temperature minimum at a frequency of $\sim 1900$ GHz ($160\,\mu$m) with a value of $(3920 \pm 375)$ K (cite: 2013A&A...549L...7L). This result still stands even with the re-calibrated ALMA data. Figure [5](#fig:tbprofile) shows the $T_\mathrm{B}(\nu)$ in mm – cm band with re-calibrated ALMA C2 and C4 data marked differently. The C2 data point at 230 GHz seems to still have some calibration issues, as it is significantly deviant from the C4 value and the general trend. In general, it is clear that the stellar $T_\mathrm{B}$ shows a systematic rise in 2017 C4 observations, provided the re-calibration procedure is now precise. There is a need for more data with better calibration applied to cross-verify this inference and also to confirm the flux level at 230 GHz. However, a hot thermally stratified chromosphere can be inferred, as expected for this Sun-like star.

#### H — 61 Vir (HD 115617)

is a G6.5V star with a mass of 0.92 M$_\odot$ at a distance of 8.5 pc. The star has a thin debris disk with a semi-major axis width of $\approx$ 22$^{\prime\prime}$ and an inclination of 77$^\circ$ , as inferred from Spitzer and Herschel data (cite: Bryden06; Wyatt12).

It is a multi-planet system with three known planets with estimated masses of 5, 18, and 23 M$_\oplus$ revolving in orbits with semi-major axis widths of 0.05, 0.22, and 0.49 AU, respectively (cite: Vogt10). The first resolved millimeter ALMA band 7 observations of 61 Vir was presented by (cite: 2017MNRAS.469.3518M). The extended disk structure is unseen in ALMA bands, revealing the stellar flux. Figure  [2](#fig:SED_fits) presents the SED of the 61 Vir overlaid with the PHOENIX model with an effective temperature of $T_{\rm eff}=5618$ K. The excess emission seen in the IR bands above the SED model is likely a result of the disk emission.

#### I — $\alpha$ Cen B (HD 128621)

is the companion to $\alpha$ Cen A (see above) and has a spectral type of K1V. $\alpha$ Cen B has an age of 4.85 Gyr and a mass of 0.90 M$_\odot$. As $\alpha$ Cen A (see above), $\alpha$ Cen B has been observed repeatedly with ALMA in almost all so far available receiver bands (cite: 2015A&A...573L...4L; 2016A&A...594A.109L; 2019arXiv190403043L). The observed SED for this star (see Fig. [2](#fig:SED_fits)) shows a deviation from the PHOENIX model SED that increases monotonically towards lower frequencies at $\nu \lesssim 400$ GHz. This effect can be better seen from $\Delta S/S_{mod}$ plotted at the bottom of the panel. Like for its companion, the plotted SED data are the average of ALMA C2 and C4 observations, and the bars on the data points reflect the spread in the values between the two observation epochs. The corresponding brightness temperatures are presented in Fig. [5](#fig:tbprofile) and confirm the results of (cite: 2016A&A...594A.109L), who discussed the brightness temperatures in much detail. They concluded that the data for $\alpha$ Cen B can be matched by a modified solar model that is altered to take into account that $\alpha$ Cen B is of spectral type K1V. As for $\alpha$ Cen A, (cite: 2015A&A...573L...4L) and (cite: 2016A&A...594A.109L) compared and complemented the ALMA measurements with brightness temperatures derived from single-dish observations. The data show a temperature minimum at $\sim 1900$ GHz with a value of $\sim 3000$ K for the K-type star $\alpha$ Cen B, which is thus lower than for the hotter G-type star $\alpha$ Cen A. Fig. [5](#fig:tbprofile) shows that the ALMA observations clearly present a chromospheric temperature rise towards values that are indicative of a transition region.

#### J — $\epsilon$ Eri (HD 22049)

has a spectral type of K2V and is located at a distance of 3.22 pc. It has a dusty ring with an inner edge around $15^{\prime\prime}$, extending up to $25^{\prime\prime}$ and is well mapped by ALMA (cite: 2017MNRAS.469.3200B).

Figure  [2](#fig:SED_fits) presents the SED of the $\epsilon$ Eri overlaid with the PHOENIX model with an effective temperature $T_{\rm eff}=5100$ K. The VLA and ATCA data provide stellar fluxes between 6 and 45 GHz (cite: Bastian18_EpsEri; 2019ApJ...871..172R).

This star has also been observed in the 217-233 GHz range using the SMA at an angular resolution of $\mbox{9$\stackrel {\prime \prime}{_{\bf \cdot}}$2}$ $\times$ $\mbox{8$\stackrel {\prime \prime}{_{\bf \cdot}}$7}$ (cite: 2015ApJ...809...47M), at 210-290 GHz using IRAM at an angular resolution of $\mbox{10$\stackrel {\prime \prime}{_{\bf \cdot}}$7}$ (cite: 2015A&A...576A..72L), and at 245-295 GHz using the LMT at a resolution of $\mbox{10$\stackrel {\prime \prime}{_{\bf \cdot}}$9}$ (cite: ChavezDagostino16). The fluxes reported by these works are significantly higher than the ALMA value at $\approx$ 230 GHz, likely due to contamination from the disk emission.

The flux excess in the range $\nu > 2000$ GHz to $\nu < 10^4$ GHz is also a possible result of contamination from the stellar disk, which is unresolved or barely resolved by the telescopes, as was mentioned in the case of $\alpha$ PsA data. However, ALMA achieves a higher angular resolution of $\mbox{1$\stackrel {\prime \prime}{_{\bf \cdot}}$6}$ $\times$ $\mbox{1$\stackrel {\prime \prime}{_{\bf \cdot}}$1}$ and is capable of separating the stellar flux from contributions of the disk. At the lowest frequencies, the deviation $\Delta S/S_{mod}$ increases with decreasing frequency, which implies a chromospheric temperature rise. The available data, however, suggest that a temperature minimum would be mapped at a much lower frequency than what is seen for the Sun, $\alpha$ Cen A, and $\alpha$ Cen B.

#### K — GJ 2006A

is part of a common proper motion visual binary (cite: 2014AJ....147...85R; 2017ApJ...840...87R) at a distance of 34.8 pc. Both components are of spectral type M3.5Ve, with A being brighter than B with respective magnitudes $B_A=14.33$ and $B_B=14.66$ (cite: 2012yCat.1322....0Z). The two components have a separation of $\mbox{17$\stackrel {\prime \prime}{_{\bf \cdot}}$8}$ (cite: 2020ApJS..246....4T). GJ 2006A has an age of only 6 Myr and a mass of 0.55 M$_\odot$. We note that for $\nu < 3\times 10^5$ GHz, the modelled SED from PHOENIX predicts fluxes that are significantly lower than the observed values. This mismatch might be caused by uncertainties in the literature values for the stellar radius, distance, or less likely, the effective temperature and/or by increased flux due to a flare on GJ 2006A during the time of the observations.

The star was detected with ALMA in band 7, while GJ 2006B remained undetected in that observation. From the SED data in Fig. [2](#fig:SED_fits), it is clear that the ALMA flux at $\nu = 341$ GHz is about two orders of magnitude higher than the fluxes predicted by the PHOENIX model. The ALMA flux corresponds to a brightness temperature of $1.6 \times 10^5$ K, which may indicate the presence of a chromosphere. The corresponding excess flux at UV wavelengths seems to support the existence of a hotter upper atmosphere as well. This interpretation would be consistent with the observed high X-ray luminosity of $\log R_\mathrm{x} = -2.68$ (see Table [\[tab:activityprops\]](#tab:activityprops)). However, the excess seems to be much higher than what would be expected from the average (quiescent) state of a chromosphere. Rather, the high values at lower frequencies, the UV excess, and even the mismatch at optical wavelengths might be caused by flares during the individual observations. In addition to potential uncertainties in the stellar parameters and its distance, a consistent increase in observed flux with respect to the modelled SED would require frequent flares, which might be possible for an M3.5Ve star like GJ 2006A. The explanation that the star was in an active phase during the observations would be in line with the results of a long-term VRI photometric study on the GJ 2006AB system, which suggested that either both or one of the stars in the system exhibit long-term variability (cite: 2003AJ....125..332J). We conclude that further flux measurements in the mm-cm range are needed to determine the atmospheric temperature stratification and to confirm the existence of a chromosphere for GJ 2006A and possible flaring. It is therefore necessary to establish both the quiescent and active states from repeated observations. In addition, IR observations would allow us to detect or reject possible contributions to a potentially yet unknown disk around this young star.

#### L — Proxima Cen

is an M5.5V star that is gravitationally bound to the $\alpha$ Cen system (cite: 2017A&A...598L...7K). It is

estimated to be 4.85 Gyr old with a mass of 0.12 M$_\odot$. It is expected to be a fully convective star, unlike the other stars in the sample, because its mass is below the theoretical core transition threshold of 0.35 M$_\odot$(cite: 2000ARA&A..38..337C). The star was detected with ALMA by (cite: AngladaEscude12), who proposed the existence of an extended and unresolved disk around the star. However, reanalysis of the same data by (cite: MacGregor18_proxima_flares) showed that the supposed disk was in fact an imaging artefact. (cite: MacGregor18_proxima_flares) also reported the discovery of a short-duration flare that lasted for a few minutes. The pre-flare flux was about 20% higher than the value derived from the photospheric SED modelling based on optical to IR fluxes by (cite: Ribas17_ProximaCenSED). This slight excess in flux is most likely due to a hot chromosphere. Another flare observed in 2019 lasted for a few seconds in ALMA band 6, along with simultaneous flaring in the optical to far-UV bands (cite: 2021ApJ...911L..25M).

Moreover, the reduction of the SED fluxes in the 10$^5$ – 10$^6$ GHz range is noteworthy. This is unlike the case for GJ 2006 A, which is a much younger M dwarf, although it is more massive and expected to be less active than a fully convective star such as Proxima Cen.

![](dSmod_Vs_Teff_band6n7.pdf)

# Discussion

## Thermal versus non-thermal emission in the mm-cm range

Observations of the Sun at mm wavelengths have testified that the emission is optically thick thermal radiation from various atmospheric layers with brightness temperatures ($T_\mathrm{B}$) of 21000 K, 9000 K, 7300 K, and 5900 K at 34 GHz, 85 GHz, 93 GHz, and 233 GHz, respectively (cite: 2006A&A...456..697W; 2008A&A...488.1079S; 2017SoPh..292...88W).

The formation height of the continuum radiation in the solar atmosphere increases with decreasing frequency in the mm range (cite: 2016SSRv..200....1W), which allows determining the temperature stratification from measurements as listed above. The effect is also clearly seen from the detailed contribution functions for the solar emission in the entire mm – cm band based on the 1D atmospheric model by (cite: 2008ApJS..175..229A) as presented by (cite: 2011SoPh..273..309S). We note that the contribution functions by (cite: 2011SoPh..273..309S) can span rather extended height ranges in the mm range, which is in line with results from 3D simulations of the solar atmosphere (cite: Loukitcheva15_mmRad_model). However, it should be mentioned that the precise formation heights of the solar continuum radiation at millimeter wavelengths are still debated (cite: 2016SSRv..200....1W). For the 10 – 30 GHz range, that is, at cm wavelengths, the contribution functions by (cite: 2011SoPh..273..309S) show that the radiation originates from a compressed height range in the upper chromosphere and transition region. Observations of the Sun in a quiescent state at 10 GHz revealed a mean $T_\mathrm{B}$ of 20,000 K that is typically seen in the transition region (cite: 1991ApJ...370..779Z).

During strong flares, however, gyro-resonance and gyro-synchrotron emission from supra-thermal electrons has been observed close to the 10 GHz range in coronal active regions (cite: Nindos00_SXR_gyroresonance_Sunspots; 2006PASJ...58...11V). The highest frequency at which gyro-resonance emission has been conclusively detected so far from solar active regions is 17 GHz (cite: 2020FrASS...7...57N). In this regard, it should be noted that gyro-resonance or gyro-synchrotron emission sources are observed less frequently at $\nu > 10$ GHz than in the $\nu \sim$ 1 – 5 GHz range, which is more sensitive to such emission. Analysing the number of active regions detected in daily solar images at 17 GHz archived during 1993 – 2013 by the Nobeyama Radio Heliograph, (cite: Selhorst14_NoRH_SSN_3GHz_srcCount) showed that the annual mean counts of active regions during that period lie in the range $\approx$ 0 – 4. Even during the period of maximum solar activity, the annual mean counts were just within 3 – 4, when the average annual counts of sunspots and gyro-resonance sources at $\approx$ 3 GHz varied around 100 – 130 and 160 – 180, respectively. A physical reason behind this dearth of sources is that the gyro-frequency ($\nu_B$) for a given magnetic field strength, $B$, is given by

$$\begin{equation}
    \nu_\mathrm{B} = 2.9\times \left( \frac{B}{1\,G}\right)\, \mathrm{MHz}.
    \label{Eqn:nuB}
\end{equation}$$

Typically, the gyro-resonance emission is observed up to the third$^{}$ harmonic of $\nu_\mathrm{B}$ (cite: 1997SoPh..174...31W). Consequently, gyro-resonance emission beyond 10 GHz can only be detected for coronal magnetic field strengths of at least $\approx$ 1150 G. Typical magnetic field strengths at coronal active regions, however, range within $\approx$ 100 – 500 G (cite: 1978SoPh...57..279D; 1999ApJ...515..842A). Unusually large field strengths over 1000 G have been reported occasionally in flaring coronal active regions near sunspots with photospheric field strengths close to 2500 G (cite: 1991ApJ...366L..43W; 1994SSRv...68..217S), however. We therefore conclude that in the Sun, non-thermal contributions above 10 GHz are expected only in extreme situations such as flares. The situation might differ in other stars depending on their magnetic field strengths and topology and on the resulting level of activity. For low-mass M dwarf stars with stronger photospheric magnetic field concentrations in the 2000 – 5000 G range, (cite: 2010MNRAS.407.2269M) could show gyro-synchrotron emission even above 20 GHz in the upper atmospheric layers, depending on which harmonic is observed. Based on archival observations of M dwarfs in microwave bands ($\nu < 10$ GHz), it has been concluded that they show signatures of gyro-synchrotron emission even during their quiescent phase up to about 20 GHz (cite: 1990SoPh..130..265B). From this discussion, we conclude that to model the mm – cm $T_\mathrm{B}(\nu)$ of low-mass M dwarfs, non-thermal contributions cannot be neglected even for the emission during non-flaring times. In the case of Sun-like stars, it is important to observe the star for a longer period so that a light curve can be obtained and any occasional high-energy non-thermal contributions from flares can be systematically filtered out to robustly detect the quiescent thermal emission. This would then mean that any inference about the emission mechanism behind the detected fluxes from Sun-like stars close 10 GHz should be made with caution unless the temporal variation and occurrence of flares can be deduced from an observed light curve.

## Dependence on spectral type

This section focuses on the derived spectral flux excess ($\Delta S/S_{mod}$) for stars with a sufficient amount of data across a wider spectral range. Stellar $\Delta S/S_{mod}$ spectra are compared against that for the Sun as a star. As defined in Sect. [\[sec:fluxexcessparameter\]](#sec:fluxexcessparameter), $\Delta S/S_{mod}$, describes the deviations of the observed fluxes from those predicted by a model that features a photosphere, but lacks a chromosphere with a notable temperature rise. This parameter could also be interpreted as a proxy for the additional thermal energy content in the upper stellar atmospheric layers that is connected to the presence of a stellar chromosphere. A positive (negative) deviation in the $S_\mathrm{obs}(\nu)$, from the PHOENIX model prediction, $S_\mathrm{mod}(\nu)$, could translate into an additional heating (cooling) or emission (absorption) mechanism operating in those atmospheric layers. These emission sources could be inherent to the stellar atmosphere or dissociated from it, but spatially unresolved by the telescope, such as disks or companions. The $\Delta S/S_{mod}$ spectrum can give indications about the nature of this additional mechanism or source. For instance, at frequencies close to 10 GHz, non-thermal gyro-synchrotron emission from energetic particles in active regions could contribute significantly to $S_\mathrm{obs}(\nu)$, resulting in a positive $\Delta S/S_{mod}$ for FGKM stars. $\Delta S/S_{mod}$ can thus be a proxy to the excess combined thermal and non-thermal energy content across the upper atmospheric layers. However, to determine the fractional contribution from thermal emission and gyro-synchrotron emission to $S_\mathrm{obs}(\nu)$, a detailed atmospheric emission modelling with input from magnetic field measurements for the star is needed. We would also require stellar flux data sampled more densely and uniformly in the mm – cm range because the stellar upper atmospheric layers for Sun-like stars are expected to have strong gradients in their thermal and magnetic stratification

(cite: 1981ApJS...45..635V; gary2001; 2013A&A...549L...7L). The $\Delta S/S_{mod}$ spectrum derived from such a well-sampled spectrum can demonstrate the changes in the dominant emission mechanism at different atmospheric layers probed because these changes often cause deviations in the spectral shape. In this case, $\Delta S/S_{mod}$ in the $10 - 100$ GHz range for M dwarfs should show signs of deviations from its high-frequency spectral structure owing to the expected significance of gyro-synchrotron emission.

Using Eqn. [\[Eqn:DelS\]](#Eqn:DelS),

we derived the spectral flux excess for the stars in the sample, ranging from 0.5 - 2.1 M$_\odot$(A1 - M3.5). The $\Delta S/S_{mod}$ spectra for stars are provided in the bottom panel of the SED plots in Fig. [2](#fig:SED_fits). The $\Delta S/S_{mod}$ values fluctuate around zero for the A-type star $\alpha$ CMa. For the F6 star $\gamma$ Lep, however, we find that $\Delta S/S_{mod}$ shows a tendency to rise with decreasing frequency. This rising trend is even clearer for the G-type stars, the Sun and $\alpha$ Cen A, owing to the better spectral sampling of data. It is notable that the rate of increase of $\Delta S/S_{mod}$ with decreasing frequency, becomes steeper for stars with lower $T_\mathrm{eff}$. A similar effect is seen in the $T_\mathrm{B}(\nu)$ of G – K dwarfs in Fig. [5](#fig:tbprofile) as well.

Figure [6](#fig:DS_by_S_spectrum) shows the variation of $\Delta S/S_{mod}$ as a function of $T_\mathrm{eff}$ for the stars in the sample for ALMA bands 7 and 6. $\Delta S/S_{mod}$ shows a sign of an increasing trend with decreasing $T_\mathrm{eff}$ in band 6 for stars with $T_\mathrm{eff}$ within 4000 – 10000 K. The single fully convective cool star, Proxima Cen, showed a $\Delta S/S_{mod}$ value lower than the K-type star $\epsilon$ Eri, deviating from this trend. For the hottest star, $\alpha$ CMa (A), $\Delta S/S_{mod}$$\approx 0$ in band 6, which means that the observed flux is well reproduced by the corresponding PHOENIX model without a chromosphere. Because the stellar sample was chosen to have no contamination from any companion or disk in the mm–cm band range, the excess flux can be attributed to the excess thermal and/or non-thermal energy content that is connected to the presence of a stellar chromosphere. All the stars except for those with ID A and B belong to F, G, K, or M spectral type, which are expected to have a hot chromosphere. The $\Delta S/S_{mod}$ values of C and D ($\gamma$ Vir A&B) appear to significantly deviate from the general trend, but are still in line with the trend within the considerable error bars. In the plot for band 7, we find that all the FGK stars show a $\Delta S/S_{mod}$ $\sim$ 0 – 1, whereas the M dwarf, GJ 2006 A (ID: K), has a significantly higher value (12000%) in its atmospheric layer probed by band 7. This could be the result of additional non-thermal contributions or even a flare. As already mentioned in Sect. [3.2](#sec:stellarsample), this explanation is plausible because M dwarfs are known to be frequently flaring (cite: Lacy76_Flare_stats_Mstars; 2020MNRAS.494.4848D). With just one $T_\mathrm{B}$ point in the whole mm – cm band, however, it is hard to draw any robust conclusion. On the other hand, it is quite intriguing that the $\Delta S/S_{mod}$ of Proxima Cen is much lower than for GJ 2006 A, even though it belongs to a class of more active fully convective stars. They have much stronger and topologically quite different magnetic field structure than other stars (cite: Donati09_Rev_Bfield; Lund20_stelar_helicity). By virtue of this, Proxima Cen could possess a very different atmospheric structure, emission mechanism and optical depth at different spectral bands compared to GJ 2006 A. Light curves at different mm – cm wavelengths are required to better understand the emission characteristics of these M dwarfs. This would help us to systematically isolate flaring and non-flaring fluxes in the time domain and study their quiescent spectra. Performing such a study across FGKM dwarfs of masses distributed around the theoretical core transition threshold of 0.35M$_\odot$ can help understand the differences in their atmospheric stratification, if any, as a result of the internal transition. In addition to mass, age is another crucial factor that determines the physical structure and properties of a star (cite: Barnes03_Rot_Vs_age_Vs_Activity; Lund20_stelar_helicity). The fact that Proxima Cen is 4.8 Gyr old while GJ 2006 A is just 6 Myr old could play an important role in the observed large difference in their $\Delta S/S_{mod}$ values.

This study demonstrates the importance of carrying out a systematic $\Delta S/S_{mod}$ spectral evolution study for stars belonging to different types and ages. The mm – cm band could help us understand how the atmospheric excess energy budget and corresponding atmospheric heating varies for these stars as function of spectral type and age.

## Possible extension of the sample size

The sample presented in this study is intended to be a starting point to illustrate the potential scientific value of a larger sample. To understand the possibilities of extending the sample, it is import to have an estimate of the largest distance up to which ALMA can detect a main-sequence star. Consider an observation at $240$ GHz($\approx 1.25\,$mm), which lies within band 6, one of the most sensitive and widely used ALMA receiver bands. An observation in this band using all available antennas of ALMA with full spectral averaging and an integration time of 1 hour can provide a $3 \sigma$ source detection threshold of around $50\,\mu$Jy. Assuming a typical temperature of $5900$ K for the Sun in band 6 (cite: 2017SoPh..292...88W), with the aforementioned detection threshold ALMA will detect a Sun-like star located within $10$ pc. The recent most extensive catalogue of stars, Gaia DR2 ((cite: Gaia18_DR2_catalog)), reports about $1675$ potential main-sequence stars of type F, G, K in this volume. In addition, because F stars are hotter and because KM stars can have higher $T_\mathrm{B}$ than the Sun in band 6 owing to their relatively steeper $T_\mathrm{B}(\nu)$ compared to G-type stars in the $\sim$ 10 – 300 GHz band (see, Fig. [5](#fig:tbprofile)), they could be detected at distances even farther out than 10 pc.

# Conclusions and outlook

The emission of main-sequence stars in the millimeter to centimeter wavelength range (10 – 1000 GHz) originates from their outer atmospheric layers, such that the height of the emitting layer increases with decreasing frequency. In the case of Sun-like stars with an outer convective zone, the emission is expected to originate from the chromosphere and corona. This work analysed the features of 10 – 1000 GHz spectra of main-sequence stars with the aim to characterise the corresponding thermal stratification in their atmospheres including the presence of a chromospheric temperature rise and potential non-thermal contributions at the lowest frequencies. A search of archives and the literature for significant detections of main-sequence stars with ALMA resulted in a sample of 12 stars across a broad range of spectral types from A1 to M3.5.

The centimeter band spectra of these stars were also compiled to obtain the spectrum in the 10 – 1000 GHz range. We then defined a spectral flux excess parameter, $\Delta S/S_{mod}$, as the ratio of the difference between the observed and the PHOENIX model spectral flux density to the respective model values. Because the stars were chosen so that no known disks, companions, or other emission sources contaminated the detected stellar emission at mm – cm wavelengths, the resulting $\Delta S/S_{mod}$ spectrum in the mm – cm range is purely star-borne. We find a systematic rise in the $\Delta S/S_{mod}$ of the FGKM stars with decreasing observation frequency. For the stars within $T_\mathrm{eff} = 4000 - 10000$ K, the rate of the rise becomes steeper as the effective temperature ($T_\mathrm{eff}$) of the star decreases.

The $\Delta S/S_{mod}$ values as function of $T_\mathrm{eff}$ were studied at two representative ALMA bands (bands 6 and 7). The A-type stars were found to show $\Delta S/S_{mod}$ $\sim$ 0 in both bands, whereas the FGKM stars showed a systematic spectral flux excess. This demonstrates that the spectral flux densities of A-type stars can be matched with models without a chromosphere, as expected for this stellar type. The positive $\Delta S/S_{mod}$ for cooler stars implies significant outer atmospheric heating and thus the existence of a hot chromosphere. For the single fully convective star in our sample, $\Delta S/S_{mod}$ was greater than 0, although the value was significantly lower than what would be expected from the apparent trend for the FGKM stars. In band 7, GJ 2006 A showed a flux excess of $\sim$ 1100%. With data available for this star in only one time and frequency point in the mm – cm band, it is hard to draw any inferences about the nature of the energy source that powered this emission. It is also possible that this flux was associated with a transient flare because M dwarfs are known to be frequently flaring.

This study thus demonstrated the unique potential of mm – cm band long-term observations of main-sequence stars to better understand the energy budget and temperature across their different outer atmospheric layers. Such periodic observation campaigns over years can help understand the nexus between the stellar activity cycles or variations and the atmospheric structure. By analysing the observations using detailed thermal and non-thermal emission models, the physical state of the plasma, its dynamics, and the nature of activity can be better understood.

# Acknowledgments

This work is supported by the Research Council of Norway through its Centres of Excellence scheme, project number 262622 (“Rosseland Centre for Solar Physics”). AM and SP acknowledge support from the EMISSA project funded by the Research Council of Norway (project number 286853). SW and MS were supported by the SolarALMA project, which has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 682462).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00238.S, ADS/JAO.ALMA#2012.1.00385.S, ADS/JAO.ALMA#2013.1.00170.S, ADS/JAO.ALMA#2013.1.00359.S, ADS/JAO.ALMA#2013.1.00645.S, ADS/JAO.ALMA#2016.A.00013.S, ADS/JAO.ALMA#2016.1.00441.S, ADS/JAO.ALMA#2017.1.00698.S, ADS/JAO.ALMA#2017.1.01583.S, ADS/JAO.ALMA#2018.1.00470.S, ADS/JAO.ALMA#2018.1.01149.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. SW and PHH acknowledge fruitful discussions of the International Team 265 (*Magnetic Activity of M-type Dwarf Stars and the Influence on Habitable Extra-Solar Planets*) supported by the International Space Science Institute, Bern, Switzerland. Some of the calculations presented here were performed at the RRZ of the Universität Hamburg, at the Höchstleistungs Rechenzentrum Nord (HLRN), and at the National Energy Research Supercomputer Center (NERSC), which is supported by the Office of Science of the U.S. Department of Energy under Contract No. DE-AC03-76SF00098. We thank all these institutions for a generous allocation of computer time. PHH gratefully acknowledges the support of NVIDIA Corporation with the donation of a Quadro P6000 GPU used in this research.

162 natexlab

(ref: 2012A&A...540A.125A) Acke, B., Min, M., Dominik, C., et al. 2012, A&A, 540, A125

(ref: 2021AJ....162...14A) Akeson, R., Beichman, C., Kervella, P., Fomalont, E., & Benedict, G. F. 2021, AJ, 162, 14

(ref: Prieto99_Ref4) Allende Prieto, C. & Lambert, D. L. 1999, A&A, 352, 555

(ref: 2012A&A...542A.116A) Ammler-von Eiff, M. & Reiners, A. 2012, A&A, 542, A116

(ref: AngladaEscude12) Anglada-Escudé, G. & Butler, R. P. 2012, ApJS, 200, 15

(ref: 1997MNRAS.284..202A) Anstee, S. D., O’Mara, B. J., & Ross, J. E. 1997, MNRAS, 284, 202

(ref: 1999ApJ...515..842A) Aschwanden, M. J., Newmark, J. S., Delaboudinière, J.-P., et al. 1999, ApJ, 515, 842

(ref: 2008ApJS..175..229A) Avrett, E. H. & Loeser, R. 2008, ApJS, 175, 229

(ref: Barnes03_Rot_Vs_age_Vs_Activity) Barnes, S. A. 2003, The Astrophysical Journal, 586, 464

(ref: 1990SoPh..130..265B) Bastian, T. S. 1990, Sol. Phys., 130, 265

(ref: 1994SSRv...68..261B) Bastian, T. S. 1994, Space Sci. Rev., 68, 261

(ref: Bastian18_EpsEri) Bastian, T. S., Villadsen, J., Maps, A., Hallinan, G., & Beasley, A. J. 2018, ApJ, 857, 133

(ref: 2007A&A...470..295B) Bazot, M., Bouchy, F., Kjeldsen, H., et al. 2007, A&A, 470, 295

(ref: 2017ApJ...840...70B) Bond, H. E., Schaefer, G. H., Gilliland, R. L., et al. 2017, ApJ, 840, 70

(ref: 2017MNRAS.469.3200B) Booth, M., Dent, W. R. F., Jordán, A., et al. 2017, MNRAS, 469, 3200

(ref: 2018A&A...616A.108B) Boro Saikia, S., Marvin, C. J., Jeffers, S. V., et al. 2018, A&A, 616, A108

(ref: Bryden06) Bryden, G., Beichman, C. A., Trilling, D. E., et al. 2006, ApJ, 636, 1098

(ref: 2009MNRAS.394.1338B) Bychkov, V. D., Bychkova, L. V., & Madej, J. 2009, MNRAS, 394, 1338

(ref: 2001A&A...373..159C) Cayrel de Strobel, G., Soubiran, C., & Ralite, N. 2001, A&A, 373, 159

(ref: 2000ARA&A..38..337C) Chabrier, G. & Baraffe, I. 2000, ARA&A, 38, 337

(ref: ChavezDagostino16) Chavez-Dagostino, M., Bertone, E., Cruz-Saenz de Miera, F., et al. 2016, MNRAS, 462, 2285

(ref: 2019E&SS....6.2525C) Coddington, O., Lean, J., Pilewskie, P., et al. 2019, Earth and Space Science, 6, 2525

(ref: 2018ApJ...856...39C) Crosley, M. K. & Osten, R. A. 2018, ApJ, 856, 39

(ref: 2015ApJ...804..146D) David, T. J. & Hillenbrand, L. A. 2015, ApJ, 804, 146

(ref: 2020MNRAS.494.4848D) Davis, I., Taylor, G., & Dowell, J. 2020, MNRAS, 494, 4848

(ref: 2010ApJ...722..343D) DeWarf, L. E., Datin, K. M., & Guinan, E. F. 2010, ApJ, 722, 343

(ref: DiFolco04) Di Folco, E., Thévenin, F., Kervella, P., et al. 2004, A&A, 426, 601

(ref: Donati09_Rev_Bfield) Donati, J. F. & Landstreet, J. D. 2009, ARA&A, 47, 333

(ref: 2014ApJ...784..148D) Duchêne, G., Arriaga, P., Wyatt, M., et al. 2014, ApJ, 784, 148

(ref: 1978SoPh...57..279D) Dulk, G. A. & McLean, D. J. 1978, Sol. Phys., 57, 279

(ref: 2002A&A...384..180F) Fabricius, C., Høg, E., Makarov, V. V., et al. 2002, A&A, 384, 180

(ref: 2004ApJS..154...10F) Fazio, G. G., Hora, J. L., Allen, L. E., et al. 2004, ApJS, 154, 10

(ref: 2020AJ....160..219F) Feinstein, A. D., Montet, B. T., Ansdell, M., et al. 2020, AJ, 160, 219

(ref: 2018A&A...614A.125F) Freund, S., Robrade, J., Schneider, P. C., & Schmitt, J. H. M. M. 2018, A&A, 614, A125

(ref: 2007AN....328.1037F) Fröhlich, H. E. 2007, Astronomische Nachrichten, 328, 1037

(ref: 2017ApJ...836..139F) Fuhrmann, K., Chini, R., Kaderhandt, L., & Chen, Z. 2017, ApJ, 836, 139

(ref: Gaia18_DR2_catalog) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: 2014ApJ...788L..37G) Gao, S., Liu, C., Zhang, X., et al. 2014, ApJL, 788, L37

(ref: 2018ApJ...862...90G) Garraffo, C., Drake, J. J., Dotter, A., et al. 2018, ApJ, 862, 90

(ref: gary2001) Gary, G. A. 2001, Sol. Phys., 203, 71

(ref: 2016ApJ...826..171G) Gáspár, A., Rieke, G. H., & Ballering, N. 2016, ApJ, 826, 171

(ref: 1980AcA....30..453G) Glebocki, R., Musielak, G., & Stawikowski, A. 1980, , 30, 453

(ref: 1992PASP..104.1035G) Gray, D. F. 1992, PASP, 104, 1035

(ref: Gray03) Gray, R. O., Corbally, C. J., Garrison, R. F., McFadden, M. T., & Robinson, P. E. 2003, AJ, 126, 2048

(ref: Grether06_Ref1) Grether, D. & Lineweaver, C. H. 2006, ApJ, 640, 1051

(ref: 1997ApJ...484..960G) Gu, Y., Jefferies, J. T., Lindsey, C., & Avrett, E. H. 1997, ApJ, 484, 960

(ref: 2002ARA&A..40..217G) Güdel, M. 2002, ARA&A, 40, 217

(ref: 2006astro.ph..9389G) Guedel, M. 2006, arXiv e-prints \[\]

(ref: Gunther20_Ref19) Günther, M. N., Zhan, Z., Seager, S., et al. 2020, AJ, 159, 60

(ref: 1999JCoAM.109...41H) Hauschildt, P. H. & Baron, E. 1999, Journal of Computational and Applied Mathematics, 109, 41

(ref: 1996AJ....111..439H) Henry, T. J., Soderblom, D. R., Donahue, R. A., & Baliunas, S. L. 1996, AJ, 111, 439

(ref: 2012A&A...537A.147H) Herrero, E., Ribas, I., Jordi, C., Guinan, E. F., & Engle, S. G. 2012, A&A, 537, A147

(ref: 2014AJ....148...54H) Hinkel, N. R., Timmes, F. X., Young, P. A., Pagano, M. D., & Turnbull, M. C. 2014, AJ, 148, 54

(ref: 2000A&A...355L..27H) Høg, E., Fabricius, C., Makarov, V. V., et al. 2000, A&A, 355, L27

(ref: 2009A&A...501..941H) Holmberg, J., Nordström, B., & Andersen, J. 2009, A&A, 501, 941

(ref: 2013A&A...553A...6H) Husser, T.-O., Wende-von Berg, S., Dreizler, S., et al. 2013, A&A, 553, A6

(ref: 2003AJ....125..332J) Jao, W.-C., Henry, T. J., Subasavage, J. P., et al. 2003, AJ, 125, 332

(ref: 2014AJ....147...21J) Jao, W.-C., Henry, T. J., Subasavage, J. P., et al. 2014, AJ, 147, 21

(ref: 2017A&A...598L...7K) Kervella, P., Thévenin, F., & Lovis, C. 2017, A&A, 598, L7

(ref: 1996ApJ...457..340K) Kim, Y.-C. & Demarque, P. 1996, ApJ, 457, 340

(ref: 2021MNRAS.500.1844K) Klein, B., Donati, J.-F., Hébrard, É. M., et al. 2021, MNRAS, 500, 1844

(ref: Lacy76_Flare_stats_Mstars) Lacy, C. H., Moffett, T. J., & Evans, D. S. 1976, ApJS, 30, 85

(ref: 2009ApJ...705...89L) Lawler, S. M., Beichman, C. A., Bryden, G., et al. 2009, ApJ, 705, 89

(ref: 2015A&A...576A..72L) Lestrade, J.-F. & Thilliez, E. 2015, A&A, 576, A72

(ref: Liebert05) Liebert, J., Young, P. A., Arnett, D., Holberg, J. B., & Williams, K. A. 2005, ApJL, 630, L69

(ref: Lim96_Proxima_ATCA) Lim, J., White, S. M., & Slee, O. B. 1996, ApJ, 460, 976

(ref: 2019arXiv190403043L) Liseau, R. 2019, arXiv e-prints, arXiv:1904.03043

(ref: 2016A&A...594A.109L) Liseau, R., De la Luz, V., O’Gorman, E., et al. 2016, A&A, 594, A109

(ref: 2013A&A...549L...7L) Liseau, R., Montesinos, B., Olofsson, G., et al. 2013, A&A, 549, L7

(ref: 2015A&A...573L...4L) Liseau, R., Vlemmings, W., Bayo, A., et al. 2015, A&A, 573, L4

(ref: 2007ApJ...658..584L) Lisse, C. M., Beichman, C. A., Bryden, G., & Wyatt, M. C. 2007, ApJ, 658, 584

(ref: Loukitcheva15_mmRad_model) Loukitcheva, M., Solanki, S. K., Carlsson, M., & White, S. M. 2015, A&A, 575, A15

(ref: Luck17) Luck, R. E. 2017, AJ, 153, 21

(ref: Lund20_stelar_helicity) Lund, K., Jardine, M., Lehmann, L. T., et al. 2020, MNRAS, 493, 1003

(ref: 2016ApJ...828..113M) MacGregor, M. A., Lawler, S. M., Wilner, D. J., et al. 2016, ApJ, 828, 113

(ref: 2017ApJ...842....8M) MacGregor, M. A., Matrà, L., Kalas, P., et al. 2017, ApJ, 842, 8

(ref: 2021ApJ...911L..25M) MacGregor, M. A., Weinberger, A. J., Loyd, R. O. P., et al. 2021, ApJL, 911, L25

(ref: MacGregor18_proxima_flares) MacGregor, M. A., Weinberger, A. J., Wilner, D. J., Kowalski, A. F., & Cranmer, S. R. 2018, ApJL, 855, L2

(ref: 2015ApJ...809...47M) MacGregor, M. A., Wilner, D. J., Andrews, S. M., Lestrade, J.-F., & Maddison, S. 2015, ApJ, 809, 47

(ref: Magaudda20_XrayActivity_dMs) Magaudda, E., Stelzer, B., Covey, K. R., et al. 2020, A&A, 638, A20

(ref: Malo14_Ref7) Malo, L., Artigau, É., Doyon, R., et al. 2014, ApJ, 788, 81

(ref: Mamajek12) Mamajek, E. E. 2012, ApJL, 754, L20

(ref: Mamajek13_fomalhaut_3rd_companionDiscovery) Mamajek, E. E., Bartlett, J. L., Seifahrt, A., et al. 2013, ApJ, 146, 154

(ref: Mamajek08_Ref11) Mamajek, E. E. & Hillenbrand, L. A. 2008, ApJ, 687, 1264

(ref: 2017MNRAS.469.3518M) Marino, S., Wyatt, M. C., Kennedy, G. M., et al. 2017, Monthly Notices of the Royal Astronomical Society, 469, 3518–3531

(ref: 2017MNRAS.465.2595M) Marino, S., Wyatt, M. C., Panić, O., et al. 2017, MNRAS, 465, 2595

(ref: 2014MNRAS.444.3517M) Marsden, S. C., Petit, P., Jeffers, S. V., et al. 2014, MNRAS, 444, 3517

(ref: 2017ApJ...842....9M) Matrà, L., MacGregor, M. A., Kalas, P., et al. 2017, ApJ, 842, 9

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mermilliod92_Ref5) Mermilliod, J. C. 1992, Highlights of Astronomy, 9, 725

(ref: Messina17_Ref6) Messina, S., Millward, M., Buccino, A., et al. 2017, A&A, 600, A83

(ref: 2011ApJ...734...67M) Millan-Gabet, R., Serabyn, E., Mennesson, B., et al. 2011, ApJ, 734, 67

(ref: 2007ApJ...655L.109M) Moerchen, M. M., Telesco, C. M., Packham, C., & Kehoe, T. J. J. 2007, ApJL, 655, L109

(ref: Montesinos16) Montesinos, B., Eiroa, C., Krivov, A. V., et al. 2016, A&A, 593, A51

(ref: Mora01) Mora, A., Merı́n, B., Solano, E., et al. 2001, A&A, 378, 116

(ref: 2010MNRAS.407.2269M) Morin, J., Donati, J. F., Petit, P., et al. 2010, MNRAS, 407, 2269

(ref: 2017MNRAS.469.3042N) Netopil, M. 2017, MNRAS, 469, 3042

(ref: 1975A&AS...22..239N) Nicolet, B. 1975, A&AS, 22, 239

(ref: 2020FrASS...7...57N) Nindos, A. 2020, Frontiers in Astronomy and Space Sciences, 7, 57

(ref: Nindos00_SXR_gyroresonance_Sunspots) Nindos, A., Kundu, M. R., White, S. M., Shibasaki, K., & Gopalswamy, N. 2000, ApJS, 130, 485

(ref: Noyes84_RHK) Noyes, R. W., Hartmann, L. W., Baliunas, S. L., Duncan, D. K., & Vaughan, A. H. 1984, ApJ, 279, 763

(ref: 2005ApJ...621..398O) Osten, R. A., Hawley, S. L., Allred, J. C., Johns-Krull, C. M., & Roark, C. 2005, ApJ, 621, 398

(ref: Pace13_RHK_Drastic_variability) Pace, G. 2013, A&A, 551, L8

(ref: Perley11_EVLA) Perley, R. A., Chandler, C. J., Butler, B. J., & Wrobel, J. M. 2011, ApJL, 739, L1

(ref: Raghavan10_Ref16) Raghavan, D., McAlister, H. A., Henry, T. J., et al. 2010, ApJS, 190, 1

(ref: 2013ApJ...764...78R) Ramı́rez, I., Allende Prieto, C., & Lambert, D. L. 2013, ApJ, 764, 78

(ref: Ramirez12_Ref15) Ramı́rez, I., Fish, J. R., Lambert, D. L., & Allende Prieto, C. 2012, ApJ, 756, 46

(ref: Riaz06_Ref9) Riaz, B., Gizis, J. E., & Harvin, J. 2006, AJ, 132, 866

(ref: Ribas17_ProximaCenSED) Ribas, I., Gregg, M. D., Boyajian, T. S., & Bolmont, E. 2017, A&A, 603, A58

(ref: 2017ApJ...840...87R) Riedel, A. R., Alam, M. K., Rice, E. L., Cruz, K. L., & Henry, T. J. 2017, ApJ, 840, 87

(ref: 2014AJ....147...85R) Riedel, A. R., Finch, C. T., Henry, T. J., et al. 2014, AJ, 147, 85

(ref: 2019ApJ...871..172R) Rodrı́guez, L. F., Lizano, S., Loinard, L., et al. 2019, ApJ, 871, 172

(ref: Royer02) Royer, F., Grenier, S., Baylac, M. O., Gómez, A. E., & Zorec, J. 2002, A&A, 393, 897

(ref: Schmitt04_Ref13) Schmitt, J. H. M. M. & Liefke, C. 2004, A&A, 417, 651

(ref: 2007A&A...475..677S) Schröder, C. & Schmitt, J. H. M. M. 2007, A&A, 475, 677

(ref: Selhorst14_NoRH_SSN_3GHz_srcCount) Selhorst, C. L., Costa, J. E. R., de Castro, C. G. G., et al. 2014, The Astrophysical Journal, 790, 134

(ref: 2008A&A...488.1079S) Selhorst, C. L., Silva-Válio, A., & Costa, J. E. R. 2008, A&A, 488, 1079

(ref: 2011SoPh..273..309S) Shibasaki, K., Alissandrakis, C. E., & Pohjolainen, S. 2011, Sol. Phys., 273, 309

(ref: 1994SSRv...68..217S) Shibasaki, K., Takano, T., Enome, S., et al. 1994, Space Sci. Rev., 68, 217

(ref: 1999A&A...341..121S) Söderhjelm, S. 1999, A&A, 341, 121

(ref: Soubiran16_Ref3) Soubiran, C., Le Campion, J.-F., Brouillet, N., & Chemin, L. 2016, A&A, 591, A118

(ref: Sreejith20_RHK_indices) Sreejith, A. G., Fossati, L., Youngblood, A., France, K., & Ambily, S. 2020, A&A, 644, A67

(ref: Satssun19_Ref12) Stassun, K. G., Oelkers, R. J., Paegert, M., et al. 2019, AJ, 158, 138

(ref: stepien94_Defn_Rx+Ro_Vs_activity_n_manyCorCurves) Stepien, K. 1994, A&A, 292, 191

(ref: 2016ApJ...818...45S) Su, K. Y. L., Rieke, G. H., Defrére, D., et al. 2016, ApJ, 818, 45

(ref: Suchkov03_Ref18) Suchkov, A. A., Makarov, V. V., & Voges, W. 2003, ApJ, 595, 1206

(ref: suresh20_EpsEri_RadioSEDmodel) Suresh, A., Chatterjee, S., Cordes, J. M., Bastian, T. S., & Hallinan, G. 2020, ApJ, 904, 138

(ref: Takeda07_Ref17) Takeda, G., Ford, E. B., Sills, A., et al. 2007, ApJS, 168, 297

(ref: 2010PNAS..107.7158T) Testa, P. 2010, Proceedings of the National Academy of Science, 107, 7158

(ref: Thekaekara69) Thekaekara, M. P., Kruger, R., & Duncan, C. H. 1969, Appl. Opt., 8, 1713

(ref: 2002A&A...392L...9T) Thévenin, F., Provost, J., Morel, P., et al. 2002, A&A, 392, L9

(ref: 2020ApJS..246....4T) Tian, H.-J., El-Badry, K., Rix, H.-W., & Gould, A. 2020, ApJS, 246, 4

(ref: 2006A&A...460..695T) Torres, C. A. O., Quast, G. R., da Silva, L., et al. 2006, A&A, 460, 695

(ref: 2018MNRAS.481..217T) Trigilio, C., Umana, G., Cavallaro, F., et al. 2018, MNRAS, 481, 217

(ref: 2015A&A...577L...3T) Tu, L., Johnstone, C. P., Güdel, M., & Lammer, H. 2015, A&A, 577, L3

(ref: Ujjwal20) Ujjwal, K., Kartha, S. S., Mathew, B., Manoj, P., & Narang, M. 2020, AJ, 159, 166

(ref: 2007A&A...474..653V) van Leeuwen, F. 2007, A&A, 474, 653

(ref: 1981ApJS...45..635V) Vernazza, J. E., Avrett, E. H., & Loeser, R. 1981, ApJS, 45, 635

(ref: 2012AJ....143..135V) Vican, L. 2012, AJ, 143, 135

(ref: Vidotto14_B_Vs_age_n_rot) Vidotto, A. A., Gregory, S. G., Jardine, M., et al. 2014, MNRAS, 441, 2361

(ref: 2019ApJ...871..214V) Villadsen, J. & Hallinan, G. 2019, ApJ, 871, 214

(ref: Villadsen14_First_detect_SLS_inRadio_VLA) Villadsen, J., Hallinan, G., Bourke, S., Güdel, M., & Rupen, M. 2014, ApJ, 788, 112

(ref: Vogt10) Vogt, S. S., Wittenmyer, R. A., Butler, R. P., et al. 2010, ApJ, 708, 1366

(ref: 2006PASJ...58...11V) Vourlidas, A., Gary, D. E., & Shibasaki, K. 2006, PASJ, 58, 11

(ref: 2016SSRv..200....1W) Wedemeyer, S., Bastian, T., Brajša, R., et al. 2016, Space Sci. Rev., 200, 1

(ref: 2019ApJ...875...55W) White, J. A., Aufdenberg, J., Boley, A. C., et al. 2019, ApJ, 875, 55

(ref: 2018ApJ...859..102W) White, J. A., Aufdenberg, J., Boley, A. C., et al. 2018, ApJ, 859, 102

(ref: 2017MNRAS.466.4201W) White, J. A., Boley, A. C., Dent, W. R. F., Ford, E. B., & Corder, S. 2017a, MNRAS, 466, 4201

(ref: White20_MESAS) White, J. A., Tapia-Vázquez, F., Hughes, A. G., et al. 2020, ApJ, 894, 76

(ref: 2004NewAR..48.1319W) White, S. M. 2004, New A Rev., 48, 1319

(ref: 2017SoPh..292...88W) White, S. M., Iwai, K., Phillips, N. M., et al. 2017b, Sol. Phys., 292, 88

(ref: 1997SoPh..174...31W) White, S. M. & Kundu, M. R. 1997, Sol. Phys., 174, 31

(ref: 1991ApJ...366L..43W) White, S. M., Kundu, M. R., & Gopalswamy, N. 1991, ApJL, 366, L43

(ref: 2006A&A...456..697W) White, S. M., Loukitcheva, M., & Solanki, S. K. 2006, A&A, 456, 697

(ref: Wiegert14) Wiegert, J., Liseau, R., Thébault, P., et al. 2014, A&A, 563, A102

(ref: Wright04_Ref2) Wright, J. T., Marcy, G. W., Butler, R. P., & Vogt, S. S. 2004, ApJS, 152, 261

(ref: Wright11_Ref10) Wright, N. J., Drake, J. J., Mamajek, E. E., & Henry, G. W. 2011, ApJ, 743, 48

(ref: Wyatt12) Wyatt, M. C., Kennedy, G., Sibthorpe, B., et al. 2012, MNRAS, 424, 1206

(ref: 2012yCat.1322....0Z) Zacharias, N., Finch, C. T., Girard, T. M., et al. 2012, VizieR Online Data Catalog, I/322A

(ref: Zic20_typeIV_ProximaCen) Zic, A., Murphy, T., Lynch, C., et al. 2020, ApJ, 905, 23

(ref: 1991ApJ...370..779Z) Zirin, H., Baumert, B. M., & Hurford, G. J. 1991, ApJ, 370, 779

(ref: 2012A&A...537A.120Z) Zorec, J. & Royer, F. 2012, A&A, 537, A120

[^1]: <https://almascience.nrao.edu/about-alma/alma-basics>

[^2]: [https://www.narrabri.atnf.csiro.au/observing/users_guide/](https://www.narrabri.atnf.csiro.au/observing/users_guide/html/atug.html)

[^3]: <https://almascience.eso.org/asax/>

[^4]: <https://almascience.eso.org/alma-science>

[^5]: <https://jvo.nao.ac.jp/portal/alma.do>

[^6]: <https://archive.nrao.edu/archive/advquery.jsp>

[^7]: <http://vizier.unistra.fr/vizier/sed/>

[^8]: [https://irsa.ipac.caltech.edu/data/SPITZER/docs/mips/](https://irsa.ipac.caltech.edu/data/SPITZER/docs/mips/mipsinstrumenthandbook/3/)

[^9]: [https://irsa.ipac.caltech.edu/data/2MASS/docs](https://irsa.ipac.caltech.edu/data/2MASS/docs/supplementary/seeing/seesum.html)

[^10]: <http://solar.nro.nao.ac.jp/norh/>

</paper>

Write the methods card for this paper.