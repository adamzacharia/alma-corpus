# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021AJ....162..235Y\sonnetcc\reply.txt

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
 "bibcode": "2021AJ....162..235Y",
 "title": "A Radiatively Driven Wind from the η Tel Debris Disk",
 "year": 2021,
 "journal": "The Astronomical Journal",
 "first_author": "Youngblood, Allison",
 "n_authors": 8,
 "arxiv_id": "2108.11965",
 "doi": "10.3847/1538-3881/ac21d1",
 "alma_projects_linked_by_archive": [
  "2013.1.01147.S"
 ]
}
```

Paper text:
<paper>
# A Radiatively Driven Wind from the $\eta$ Tel Debris Disk

## Abstract

We present far- and near-ultraviolet absorption spectroscopy of the $\sim$23 Myr edge-on debris disk surrounding the A0V star $\eta$ Telescopii, obtained with the *Hubble Space Telescope* Space Telescope Imaging Spectrograph. We detect absorption lines from C I, C II, O I, Mg II, Al II, Si II, S II, Mn II, Fe II, and marginally N I. The lines show two clear absorption components at $-22.7\pm0.5$ km s$^{-1}$ and $-17.8\pm0.7$ km s$^{-1}$, which we attribute to circumstellar (CS) and interstellar (IS) gas, respectively. CO absorption is not detected, and we find no evidence for star-grazing exocomets. The CS absorption components are blueshifted by $-16.9\pm$2.6 km s$^{-1}$ in the star’s reference frame, indicating that they are outflowing in a radiatively driven disk wind. We find that the C/Fe ratio in the $\eta$ Tel CS gas is significantly higher than the solar ratio, as is the case in the $\beta$ Pic and 49 Cet debris disks. Unlike those disks, however, the measured C/O ratio in the $\eta$ Tel CS gas is consistent with the solar value. Our analysis shows that because $\eta$ Tel is an earlier type star than $\beta$ Pic and 49 Cet, with more substantial radiation pressure at the dominant C II transitions, this species cannot bind the CS gas disk to the star as it does for $\beta$ Pic and 49 Cet, resulting in the disk wind.

# Introduction

Debris disks are the end stage of planet formation, maintained by colliding planetesimals that persist beyond the gas-rich protoplanetary disk phase. The dust properties of these systems have been extensively observed, but their gas properties are woefully under-constrained (cite: Hughes:2018). Sub-mm CO emission has been detected in only about 20 debris disks to date (cite: Zuckerman:1995; Dent:2014; Moor:2017). Any gas within a debris disk is unlikely to be a remnant from the protoplanetary stage unless the system is especially young (cite: Kral:2019). Instead, the preferred explanation is that debris disk gas is continually replenished through various processes ultimately associated with destruction of planetesimals (cite: Beust:1990; Czechowski:2007; Grigorieva:2007; Zuckerman:2012). Thus, examining the gas in debris disks offers the chance to probe the chemical composition of the young extrasolar planetesimals themselves.

For edge-on debris disks, small amounts of circumstellar (CS) gas are detectable with line-of-sight absorption spectroscopy, where the central star serves as the background source. This method has been successfully applied to numerous debris disks in the optical (cite: Hobbs:1985; Montgomery:2012; Rebollido:2018; Rebollido:2020) and ultraviolet (cite: Roberge2006; Roberge2014; Jenkins2020_51Oph). The gas seen has low column densities ($N \gtrsim 10^{11}$ cm$^{-2}$) and appears to be primarily in atomic and ionic forms. The relative paucity of molecular gas is a consequence of the low dust densities (cite: Chen:2014) and the apparent lack of H$_2$ in debris disks (cite: LecavelierdesEtangs:2001; Chen:2007), which make them generally optically thin to dissociating interstellar radiation (cite: Matra:2017). However, in the few debris disks displaying substantial CO emission, ionization of neutral carbon may play a role in shielding the molecule from rapid dissociation (cite: Kral:2019).

In the case of $\beta$ Pic, the presence of a stable (i.e., unshifted with respect to the star) gas disk in Keplerian rotation was a puzzle, as many of the species observed should be rapidly blown out by radiation pressure from the central star (cite: Lagrange:1998). This mystery was resolved by incorporating Coulomb effects in dynamical models of the gas disk (cite: Fernandez:2006) and observing that the $\beta$ Pic gas was extremely overabundant in carbon relative to solar abundance (cite: Roberge2006; Cataldi:2014). The ionized gas is dynamically coupled into a single fluid with an abundance-weighted, effective radiation pressure coefficient. Since ionized carbon feels weak radiation pressure from an A5V star, the carbon overabundance lowers the fluid’s radiation pressure coefficient enough such that the whole fluid is bound to the star. Neutral species that feel strong radiation pressure are rapidly ionized and join the fluid. This is likely also the explanation for the presence of stable atomic/ionic gas in the 49 Cet debris disk (cite: Roberge2014). However, a comprehensive understanding of the coupled dynamics and composition of gas in debris disks remains elusive.

(HD 181296, HR 7329) is a young A0V star at 47.36 pc (cite: GaiaDR2) with a M7/8V companion $\sim$4$''$ away (cite: Lowrance2000; Guenther2001). A debris disk identified via infrared excess (cite: Backman1993; Mannings1998) surrounds the A0V star ($\eta$ Tel A). Hereafter we refer to $\eta$ Tel A as simply $\eta$ Tel. The star is a member of the $\beta$ Pic Moving Group and therefore its age is $23 \pm 3$ Myr (cite: Zuckerman2001; Mamajek2014). Other fundamental stellar properties of $\eta$ Tel include $T_\mathrm{eff} = 9500-10400$ K (cite: McCarthy2012; Rebollido:2018), $R = 1.61~ R_{\odot}$ (cite: Rhee2007), and $v \sin i = 230$ km s$^{-1}$ (cite: Rebollido:2018). The metallicity \[Fe/H\] appears to be consistent with solar (cite: Saffe2008).

*Spitzer* IRS spectroscopy of $\eta$ Tel revealed emission consistent with CS dust at two temperatures (115 and 370 K), indicating the presence of two different planetesimal belts, akin to the asteroid and Kuiper belts of the solar system (cite: Chen2006). (cite: Smith2009) resolved the debris disk with Gemini South T-ReCS imaging at 18.3 $\mu$m, discovering its edge-on orientation and confirming the presence of two distinct temperature components: a spatially resolved cold component at 24 au and an unresolved hot component at $\sim$4 au. Given the age of the system, the source of the infrared-emitting dust grains is likely collisions between planetesimals.

The only CS gas tracer definitively detected to date in $\eta$ Tel’s debris disk is far-IR C II emission seen with the *Herschel* PACS instrument (cite: RiviereMarichalar2014). With a system age of $\sim$23 Myr, the C II gas is not expected to be a remnant of the protoplanetary disk. No O I or H$_2$O emission from $\eta$ Tel was detected with *Herschel* (cite: Dent2013), and CO emission was not detected with APEX (cite: Hales2014). Optical Ca II and Na I absorption lines have been detected towards $\eta$ Tel (cite: Welsh2018; Rebollido:2018; Rebollido:2020), but their origin could not be definitively identified as CS or interstellar (IS). (cite: Welsh2018) searched for signs of exocomets in optical spectra of $\eta$ Tel; some weak time-variable Ca II absorption was seen but could not be confidently identified as arising from star-grazing exocomets.

In this paper, we present a sensitive search for CS absorption from $\eta$ Tel’s edge-on debris disk using two epochs of ultraviolet (UV) data obtained with the *Hubble Space Telescope* (*HST*) Space Telescope Imaging Spectrograph (STIS) instrument. Section [2](#sec:ObservationsReductions) describes the observations and data reduction. In Section [3](#sec:methods), we detail how we determined the physical properties of the detected UV absorption lines, including radial velocities and column densities, and identify the origins of the absorption components seen. Section [3](#sec:methods) also presents new upper limits on CO using data from both *HST* and the Atacama Large Millimeter/submillimeter Array (ALMA), and discusses an unidentified time-variable absorption feature seen in the *HST* spectra. Section [4](#section:velocity) discusses the velocity structure of the line of sight to $\eta$ Tel, including a determination of the stellar radial velocity. Our analyses of the elemental abundances in and the dynamics of the $\eta$ Tel CS gas appear in Sections [5](#section:abundances) and [6](#section:dynamics), respectively. Section [7](#section:discussion) discusses our interpretation of the CS gas and concluding remarks appear in Section [8](#sec:conclusion).

# Observations and Data Reduction

We observed the $\eta$ Tel debris disk with the *HST* STIS spectrograph on 2016-Oct-03 (Visit 1) and 2016-Oct-06 (Visit 2). The spectra were acquired in two visits to look for changes in CS absorption lines caused by star-grazing comets, which are observed in spectra of numerous young debris disks (cite: Rebollido:2020). The wavelength coverage of the STIS spectra is 1164–1951 Å and 2587–2851 Å; the complete spectrum combining both visits appears in Figure [1](#fig:all_spectra). The spectra were obtained with the E140H and E230H echelle gratings (grating settings i1271, c1416, c1598, i1813, and i2713), providing an average dispersion of $\Delta \lambda = \lambda / 228\,000$ Å pixel$^{-1}$. The data were calibrated with the default CALSTIS v3.4.2 pipeline. The relative wavelength accuracy within an exposure is better than $0.5~\mathrm{pixel} = 0.66 \ \mathrm{km} \ \mathrm{s}^{-1}$ and the absolute wavelength accuracy across exposures is better than $1~\mathrm{pixel} = 1.32 \ \mathrm{km} \ \mathrm{s}^{-1}$.[^1]

![](etaTel_all_spectra.png)

No significant variability in the spectra was seen, with the exception of one mysterious absorption feature (discussed in Section [3.4](#subsec:Mystery)) and a small $\sim$8% flux offset between the c1598 spectra (1497-1699 Å) from Visit 1 and Visit 2. As the spectra from the other grating settings did not show this flux variation between visits, this inter-visit variation in the c1598 spectra is very likely a calibration error, possibly due to time-dependent shifts in the echelle blaze function. We did not correct this flux offset, as our absorption line analysis is performed relative to the continuum flux.

We created a master $\eta$ Tel spectrum by combining the individual spectra from both visits, first interpolating all onto a common wavelength grid and then performing a weighted average. The first and last 10 grid points of each E140H echelle order were excised to avoid introduction of spurious features by edge effects; the edge effects in the E230H spectra were not as consistent from order to order so we manually determined the number of edge grid points to excise from each order. The error arrays were added in quadrature and divided by the number of spectra averaged at that wavelength. We manually estimated and subtracted additional inter-order scattered light for strongly saturated absorption features whose troughs should reach zero flux (O I 1302 Å and C II 1334 Å). The scattered light corrections are small and do not have a significant impact on the quality of our absorption feature modeling.

The spectra show many narrow absorption lines arising from gas along the line of sight to the central star. The species detected are: C I, C II, N I, O I, Mg II, Al II, Si II, S II, Mn II, and Fe II. For all lines analyzed, the rest wavelengths ($\lambda_0$) and the lower energy levels of the transitions ($E_l$) appear in Table [\[table:lines\]](#table:lines). With the exception of the aforementioned “mystery feature” (Section [3.4](#subsec:Mystery)), none of the absorption lines varied between the visits; thus, there is no clear evidence of star-grazing planetesimals in the data. We find no emission lines in the STIS spectra, indicating that $\eta$ Tel is chromospherically inactive, as expected for stars with spectral type earlier than $\sim$A5V (cite: Braithwaite2017).

lCRcCC $\lambda_0$ & $E_\mathrm{l}$ & $v_\mathrm{r}$ & Component & $\log_{10} N_l$ & $b$\
(Å) & cm$^{-1}$ & (km s$^{-1}$) & ID & (cm$^{-2}$) & (km s$^{-1}$)\
\
1560.3092 & 0.0 & $-24.06^{+2.12}_{-1.41}$ & CS & $11.71^{+0.23}_{-0.76}$ & $3.01^{+0.68}_{-1.08}$\
1560.6822, 1560.7090 & 16.40 & $-24.06^{+2.12}_{-1.41}$ & CS & $11.15^{+0.63}_{-2.09}$ & $3.01^{+0.68}_{-1.08}$\
1561.3402, 1561.3667, 1561.4384 & 43.40 & $-24.06^{+2.12}_{-1.41}$ & CS & $11.46^{+0.29}_{-2.09}$ & $3.01^{+0.68}_{-1.08}$\
& CS & $11.97^{+0.33}_{-1.01}$ &\

\
1334.5323 & 0.0 & $-22.53^{+1.33}_{-1.33}$ & CS & $16.16^{+0.18}_{-0.36}$ & $3.11^{+0.17}_{-0.16}$\
& & $-18.60^{+1.35}_{-1.30}$ & IS & $15.50^{+0.14}_{-0.13}$ & $5.88^{+0.19}_{-0.20}$\
**1335.6627,** 1335.7077 & 63.42 & $-22.53^{+1.33}_{-1.33}$ & CS & $13.05^{+0.02}_{-0.03}$ & $3.11^{+0.17}_{-0.16}$\
& CS & $16.17^{+0.18}_{-0.35}$ &\

\
1199.5496, 1200.2233, 1200.7098 & 0.0 & -21.06$^{+1.57}_{-1.64}$ & CS & $13.53-17.24$  $^{a}$ & $2.76^{+1.14}_{-0.69}$\
& CS & $13.53-17.24$  &\

\
1302.1685, 1355.5977 & 0.0 & $-25.27^{+1.33}_{-1.32}$ & CS & $16.17^{+0.21}_{-0.30}$ & $1.82^{+0.10}_{-0.12}$\
& & $-17.56^{+1.54}_{-1.45}$ & IS & $14.68^{+0.09}_{-0.07}$ & $7.97^{+0.41}_{-0.64}$\
& & $-0.76^{+2.25}_{-4.91}$ & unknown & $13.47^{+0.24}_{-0.19}$ & $8.17^{+3.51}_{-2.14}$\
1304.8576 & 158.27 & $-25.27^{+1.33}_{-1.32}$ & CS & $13.32^{+0.03}_{-0.03}$ & $1.82^{+0.10}_{-0.12}$\
1306.0286 & 226.98 & $-25.27^{+1.33}_{-1.32}$ & CS & $12.85^{+0.05}_{-0.05}$ & $1.82^{+0.10}_{-0.12}$\
& CS & $16.17^{+0.21}_{-0.30}$ &\

\
2796.352, 2803.531 & 0.0 & -21.19$^{+1.32}_{-1.32}$ & CS & 14.16$^{+0.08}_{-0.07}$ & 4.00$^{+0.10}_{-0.11}$\
& & -10.16$^{+1.31}_{-1.34}$ & IS & 12.26$^{+0.03}_{-0.02}$ & 2.71$^{+0.17}_{-0.15}$\
& CS & 14.16$^{+0.08}_{-0.07}$ &\

\
1670.7874 & 0.0 & $-22.56^{+1.36}_{-1.28}$ & CS & $12.44^{+0.04}_{-0.02}$ & $2.58^{+0.23}_{-0.13}$\
& & $-18.67^{+2.66}_{-1.28}$ & IS & $11.71^{+0.08}_{-0.23}$ & $6.20^{+0.85}_{-1.36}$\
& CS & $12.44^{+0.04}_{-0.02}$ &\

\
1304.3742, 1526.7066, 1808.0129 & 0.0 & $-22.26^{+1.31}_{-1.33}$ & CS & $14.04^{+0.03}_{-0.03}$ & $3.05^{+0.08}_{-0.09}$\
& & $-17.37^{+1.40}_{-1.38}$ & IS & $13.18^{+0.05}_{-0.05}$ & $6.05^{+0.24}_{-0.27}$\
& CS & $14.04^{+0.03}_{-0.03}$ &\

\
1425.0299, 1425.1877, 1425.2189 & 0.0 & & CS & $< 12.07$  $^{c}$ &\
& CS & $< 12.07^{ \ \, }$ &\

\
1250.578, 1253.805, 1259.518 & 0.0 & $-21.32^{+1.42}_{-1.37}$ & CS & $14.35^{+0.03}_{-0.06}$ & $3.19^{+0.24}_{-0.25}$\
& & $-17.37^{+4.99}_{-2.06}$& IS & $12.58^{+1.33}_{-3.15}$ & $4.75^{+6.75}_{-4.60}$\
& CS & $14.35^{+0.03}_{-0.06}$ &\

\
2594.499, 2606.462 & 0.0 & -22.69$^{+1.33}_{-1.33}$ & CS & 11.76$^{+0.03}_{-0.03}$ & 2.90$^{+0.27}_{-0.25}$\
& & & IS & $<$11.28  $^{d}$ &\
& CS & 11.76$^{+0.03}_{-0.03}$ &\

\
1608.4511, 2586.6500, 2600.1729 & 0.0 & $-22.79^{+1.32}_{-1.32}$ & CS & $13.48^{+0.01}_{-0.01}$ & $2.59^{+0.04}_{-0.04}$\
& & $-17.64^{+1.44}_{-1.38}$ & IS & $12.64^{+0.04}_{-0.04}$ & $6.99^{+0.35}_{-0.39}$\
& CS & $13.48^{+0.01}_{-0.01}$ &\

\
$J_l = 0$ & 0.0 & & CS & $<12.38$  $^{f}$ &\
$J_l = 1$ & 3.85 & & CS & $<12.47$  $^{f}$ &\
$J_l = 2$ & 11.53 & & CS & $<12.66$  $^{f}$ &\
$J_l = 3$ & 23.07 & & CS & $<12.95$  $^{f}$ &\
$J_l = 4$ & 38.45 & & CS & $<12.15$  $^{f}$ &\
$J_l = 5$ & 57.67 & & CS & $<12.09$  $^{f}$ &\
$J_l = 6$ & 80.74 & & CS & $<12.23$  $^{f}$ &\
Total & & & CS & $<13.05$  $^{g}$ &

Table notes: Uncertainties represent the 68% confidence interval. All radial velocities ($v_{\rm r}$) are in the heliocentric frame and have had the STIS absolute wavelength accuracy value (1.32 km s$^{-1}$) propagated into their confidence intervals. In the rows labeled “Total in all energy levels”, the column density listed is the total of the column densities in all the fine structure energy levels of the ground term. $^{a}$ Lower limit and upper limit (both $3\sigma$) reported. The marginalized posterior distribution for the column density parameter is wide and flat-topped with a median value of 15.41 and a $1\sigma$ range of $14.42-16.41$. $^{b}$ Lines arising from excited fine structure energy levels of the ground term not seen in the spectra. Total column density in all levels is assumed to be equal to the column density in the ground energy level. $^{c}$ Upper limit ($3\sigma$) computed with $v_{\rm r}$ allowed to vary between $-26$ and $-21$ km s$^{-1}$ and $b$ allowed to vary between 0.1 and 10 km s$^{-1}$. $^{d}$ Upper limit ($3\sigma$) computed with $v_{\rm r}$ allowed to vary between $-20$ and $-10$ km s$^{-1}$ and $b$ allowed to vary between 0.1 and 15 km s$^{-1}$. $^{e}$ See Table 3A of (cite: Morton1994) for a list of the CO transition wavelengths associated with each $J_l$ rotational level of the lowest vibrational state ($\nu$=0) of the ground electronic state ($X$). $^{f}$ Upper limit ($3\sigma$) on CO column density in each $J_l$ rotational level of the lowest vibrational state ($\nu = 0$) of the ground electronic state ($X$). $^{g}$ Upper limit ($3\sigma$) on total CO column density from fitting the $A-X \ (0-0)$ and $A-X \ (1-0)$ bands simultaneously assuming a Boltzmann distribution for the rotational energy levels. Excitation temperature was allowed to vary between 1 and 500 K.

# Fitting the absorption features

## Atomic and Ionic Species

To measure column densities and radial velocities of the CS absorbers, we created models of the observed absorption features in the following way. For each species listed in Table [\[table:lines\]](#table:lines) (C I, C II, O I, etc.), absorption lines arising from the different lower energy levels ($E_l$) were each modeled as a Voigt line profile. The parameters for each Voigt profile are radial velocity ($v_{\rm r}$), the line of sight column density in the lower energy level of the transition ($N_l$), and the Doppler broadening parameter ($b$). The vacuum rest wavelengths, oscillator strengths, and radiation damping constants used in constructing the Voigt profiles are from (cite: Morton1994) and (cite: Morton2003). For each transition that might contain an IS absorption component, an additional Voigt profile with an independent radial velocity was included.

The resulting ensemble of Voigt profiles was convolved with the instrumental line spread function for the appropriate grating and slit[^2], then multiplied by a model for the stellar continuum in the vicinity of the absorption feature (2nd order polynomial), the parameters of which were allowed to vary during fitting. The final models for each feature were fit to the master spectrum using a Markov Chain Monte Carlo (MCMC) affine-invariant ensemble sampler `emcee` (cite: Foreman-Mackey2013). Each species was fit separately, but all transitions listed in Table [\[table:lines\]](#table:lines) for an individual species were fit simultaneously. Lines arising from the same $E_l$ of each species were assumed to have the same $N_l$, and each velocity component was assumed to have the same $b$.

For the MCMC, we used $24-100$ walkers, depending on the number of free parameters, assumed a Gaussian likelihood and uniform priors for all parameters. We ran the chains for at least 50 autocorrelation times (10$^4-10^6$ steps) to approximate convergence, and removed an appropriate burn-in period based on the behavior of the walkers. Table [\[table:lines\]](#table:lines) lists the best fit (median) values and 68% confidence intervals for the parameters $v_{\rm r}$, $\log_{10} N_l$, and $b$, derived from these parameters’ marginalized posterior probability distributions. Note that in Table [\[table:lines\]](#table:lines) and throughout the paper, the radial velocities have the STIS absolute wavelength accuracy value (1.32 km s$^{-1}$) propagated into their confidence intervals unless otherwise stated. Figures [2](#fig:CI_bestfit) through [12](#fig:FeII_bestfit) show the data, best-fitting models, and residuals normalized by the data uncertainties.

![](etaTel_CI_both_bestfit.png)

![](etaTel_CII_both_bestfit.png)

![](etaTel_NI_bestfit.png)

![](etaTel_OI_all_bestfit.png)

![](etaTel_MgII_bestfit.png)

![](etaTel_AlII_1670_bestfit.png)

![](etaTel_SiII_three_fit_bestfit.png)

![](etaTel_SI_bestfit.png)

![](etaTel_SII_fit_all_three_at_once_bestfit.png)

![](etaTel_MnII_bestfit.png)

![](etaTel_FeII_bestfit.png)

Lines arising from ground energy levels of species present in the local interstellar medium (ISM; C II, O I, Mg II, Al II, Si II, S II, Mn II, and Fe II) show velocity components near $-23$ km s$^{-1}$ and $-18$ km s$^{-1}$. Lines arising from species not abundant in the local ISM or from excited energy levels show a single velocity component near $-23$ km s$^{-1}$. We therefore identify velocity components near $-23$ km s$^{-1}$ as originating in CS gas and components near $-18$ km s$^{-1}$ as originating in IS gas (indicated in Table [\[table:lines\]](#table:lines)). This suggests that the Ca II H & K and Na I D absorption detected at $-22$ km s$^{-1}$ by (cite: Rebollido:2018) and (cite: Welsh2018) are circumstellar in origin. Two exceptions to this trend arose, which are further discussed in later sections: O I has a third absorption component at around $-1$ km s$^{-1}$ (Section [3.2](#subsec:OI_unknown)) and Mg II’s redder velocity component (presumably IS in origin) appears at $-10$ km s$^{-1}$ rather than $-18$ km s$^{-1}$ (Section [4.1](#subsection:ism_vel)).

We note that the MCMC fit finds a non-zero probability that N(C II) = 0 cm$^{-2}$ for the CS component, but we present $\log_{10} N$(C II) = 16.16$^{+0.18}_{-0.36}$ in Table [\[table:lines\]](#table:lines). The shape of the marginalized distribution for the column density of C II in the ground energy level consists of a strong, narrow peak at $\log_{10} N$(C II) $\approx$ 16 and weak tail extending toward zero. This occurs because of degeneracy between the CS and IS absorbers in this heavily saturated line, which contains the bulk of the total reported C column density. Fortunately, the fit to the weaker C II\* absorption feature arising from the first excited fine structure level, which is uncontaminated by IS absorption, provides a strong constraint inconsistent with zero on $N$(C II\*). Since we expect the column density in the ground energy level to be greater than the first excited fine structure level, we restricted $\log_{10} N$(C II) to be greater than 14, two orders of magnitude lower than the value at the strong narrow peak in the marginalized distribution. This prevented the $N$(C II) confidence intervals from extending to arbitrarily small values and provides a better estimate of the error on the $N$(C II) measurement.

S I was not significantly detected (Figure [9](#fig:SI_bestfit)); therefore, a $3 \sigma$ upper limit on the CS column density was obtained assuming $v_{\rm r}$ between $-26$ and $-21$ km s$^{-1}$ and $b$ between 0.1 and 10 km s$^{-1}$. N I was marginally detected in the spectrum (Figure [4](#fig:NI_bestfit)); however, we were unable to obtain a robust measurement and instead determined upper and lower limits for the N I CS column density in the same way as for S I. The signal-to-noise ratio of the data is low around 1200 Å near the N I lines and the lower limit on the column density should be treated with caution.

For each species, Table [\[table:lines\]](#table:lines) also gives the total column density summing over all fine structure levels of the ground energy term. Note that N I, Mg II, Al II, S II, and Mn II have only a single fine structure level in the ground term. For Si II, S I, and Fe II, we did not see significant absorption arising from the excited fine structure levels of the ground term. For these species, the total column density was assumed to be equal to the column density in the ground energy level. Since very small column densities could have been detected in the spectrum, this assumption is unlikely to affect any results.

## Additional O I Absorption Component

In the saturated O I line arising from the ground energy level (1302.1685 Å), we found a third velocity component at $v_{\rm r} = -0.76^{+2.25}_{-4.91}$ km s$^{-1}$ not significantly detected in any other atomic absorption line (Figure [5](#fig:OI_bestfit)). The column density in the third O I component is smaller than the IS component’s column density by a factor of 15-20, but has a similar $b$ value. Since time-variable velocity components redshifted with respect to the star are a sign of star-grazing exocomets, we examined the O I feature in the two visits of STIS spectra taken $\sim3.5$ days apart, and find no significant variability near the velocity of the third component. Thus, we cannot confidently attribute this component to star-grazing exocomet activity. Neither can we rule out this explanation, as such activity may vary on timescales longer than the separation between the two visits.

## Carbon Monoxide with STIS and ALMA

No CO gas absorption lines are seen in the STIS spectra, despite the availability of multiple strong electronic transition bands. The wavelength ranges around the $A-X \ (0-0)$ band at 1510 Å and the $A-X \ (1-0)$ band at 1544 Å are shown in Figure [13](#fig:CO_both_bestfit). The apparent absorption feature extending from 1509.7-1509.9 Å is likely an instrument artifact despite its presence in all four spectra coadded to create the master spectrum in this region. If it were genuinely due to CO absorption, then signficant absorption would have been detected between 1509.5-1509.6 Å as well. The narrow feature centered at 1509.77 Å is present in only one of the four coadded spectra.

We calculated $3 \sigma$ upper limits on the line of sight CO column densities by producing models of the absorption bands similar to those for the atomic lines and fitting them to the data to determine confidence intervals. Upper limits were determined in two ways: 1. allowing the column densities in individual rotational energy levels ($J_l$) to independently vary and 2. assuming the population of the rotational energy levels follows a Boltzmann distribution. In both cases, only a single velocity component was included in the models. The free parameters in Case 1 were the CO column densities in the $J_l$ = 1–6 levels, the Doppler broadening parameter ($b$), and the radial velocity ($v_r$). The radial velocity was allowed to vary between $-26$ and $-21$ km s$^{-1}$ and $b$ was allowed to vary between 0.1 and 5 km s$^{-1}$. For Case 2, the free parameters were excitation temperature ($T_{\rm ex}$), total CO column density, $b$, and radial velocity. The radial velocity and $b$ were allowed to vary over the same ranges as in Case 1, and $T_{\rm ex}$ was allowed to vary between 1 and 500 K. All upper limits on the CO column densities are reported in Table [\[table:lines\]](#table:lines).

![](etaTel_CO_fit_all_temperature_bestfit.png)

$\eta$ Tel was observed with ALMA during Cycle 2 on 2015 July 23 and September 17 (2013.1.01147.S). We executed the associated reduction scripts in `CASA` (cite: McMullin:2007) on the raw visibilities in order to regenerate the calibrated visibilities. The first scheduling block (SB) executed on 2015 July 23 showed significantly better quality than the second, with 44 antennas in the array spanning baselines of 15.1 m to 1.6 km and good weather. The second SB had only 34 antennas with baselines between 41.4 m and 2.1 km, and contributes little to the overall signal-to-noise of the ALMA observations. Between the two SBs, the total on-source integration time was 14 min.

For these observations, the correlator was configured with one spectral window centered on the $^{12}$CO $J=2-1$ line at 230.5 GHz and a second centered at 220.4 GHz, both with 3840 channels covering 58593.8 kHz total bandwidth for a spectral resolution of 30.52 kHz. The remaining two spectral windows, centered at 218.5 and 233.0 GHz, were intended to detect only continuum emission at low spectral resolution (128 channels covering 2 GHz). All deconvolution and imaging was performed using the `clean` task in `CASA` (version 4.3.1).

Neither continuum emission nor $^{12}$CO line emission from $\eta$ Tel are detected in these ALMA data. With natural weighting, the continuum RMS is $0.051$ mJy beam$^{-1}$ for a beam size of $0.29\ensuremath{''}\times0.22\ensuremath{''}$. Assuming the $\eta$ Tel disk geometry inferred from imaging observations with T-ReCS on Gemini South at 11.7 and 18.3 $\mu$m (cite: Smith2009), we estimate that the disk emission would be spread over $\sim7$ beams given the angular resolution of these ALMA observations. Thus, the non-detection of continuum emission implies a $3 \sigma$ upper limit on the disk continuum flux of $<1.1$ mJy at 1.33 mm. We can use this upper limit to estimate an upper limit on the total dust mass in the disk using $M_{dust} = F_\nu d^2/(\kappa_\nu B_\nu(T_{dust}))$, where $F_\nu$ is the millimeter flux density, $d$ is the distance, $\kappa_\nu$ is the dust opacity, and $B_\nu$ is the Planck function at the dust temperature, $T_{dust}$. We use a dust opacity of $\kappa_\nu = 2.3$ cm$^2$ g$^{-1}$ as is common in the literature (cite: Beckwith1990), but note that the significant uncertainty on this value dominates the uncertainty in the resulting dust mass. (cite: Pollack1994) obtain dust opacities that are several orders of magnitude smaller ($10^{-2}-10^{-3}$ cm$^2$ g$^{-1}$), which would increase the calculated dust masses considerably. Assuming a dust temperature of 100 K (typical for a warm inner dust belt), yields a total dust mass of less than $7.22\times10^{25}$ g or 0.012 $M_\oplus$. This is consistent with the $T_{dust}$=162 K estimate from (cite: RiviereMarichalar2014) based on *Herschel* \[C II\] data. For a colder outer dust belt with a temperature of 40 K, the total dust mass would be less than $1.96\times10^{26}$ g or 0.033 $M_\oplus$.

The RMS for the $^{12}$CO line is $11$ mJy beam$^{-1}$ measured in channels with width $0.2$ km s$^{-1}$. Making the same assumptions about the disk geometry as before, this yields a $3\sigma$ upper limit on the integrated line intensity of $0.23$ Jy km s$^{-1} = 1.7\times10^{-21}$ W m$^{-2}$. This upper limit is high compared to $^{12}$CO gas emission measured with ALMA for other A-star debris disks (cite: Hughes2017; MacGregor2018). Since the inclination of the $\eta$ Tel disk is only constrained to be within $20^\circ$ of edge-on (cite: Smith2009), the sensitive upper limits from STIS on the line-of-sight CO column densities in the various rotational levels cannot reliably be used to estimate upper limits on pure rotational CO emission. Future targeted ALMA observations with lower resolution and deeper sensitivity limits will be able to detect smaller CO gas masses or place much more stringent upper limits.

## Mystery absorber at 1594 Å

We identify an absorption line at $\sim1594$ Å originating from an unknown species, which was also observed in STIS spectra of the 49 Cet debris disk (cite: Miles2016). In the 49 Cet spectra, the absorption was variable on the timescale of a few days, suggesting it originated from star-grazing comets. Similarly, the feature in the $\eta$ Tel data shows strong variability between the two visits (top panel of Figure [14](#fig:mystery_line)), with a narrow absorption feature at 1594.4 Å disappearing between the first and second visits. There also appear to be shallower transient features on either side of the narrow feature.

![](eta_Tel_A_star_comparison_1594_broadened.png)

During our attempts to identify the species responsible for this absorption feature, multiple databases of atomic and ionic transitions were searched. Unfortunately, the feature shows no clear stable, unvarying absorption component that could help identify the rest wavelength, as was also the case for 49 Cet. The most promising candidate species (e.g., O II, Si I, Fe II) produce additional absorption lines within the wavelength range of the STIS spectra that are not seen or do not vary between visits. Therefore, we found no solid identification for the mystery species.

Some absorption lines in the 49 Cet spectra (C II at 1335 Å and C IV at 1550 Å) showed variations characteristic of star-grazing comets, making it easier to associate the mystery feature with such activity. This explanation is more difficult to accept in the case of $\eta$ Tel, as no other variable features are seen in the spectra.

The deep absorption feature at 1594.4 Å in the Visit 1 spectrum is narrower than other stellar absorption lines in the $\eta$ Tel spectra, suggesting that the mystery feature does not arise in the atmosphere of this rapidly rotating star. To demonstrate this, we examined archival STIS spectra of early A stars without CS gas along the line of sight. The lower two panels in Figure [14](#fig:mystery_line) show the STIS spectra of HD 34203 (18 Ori), an A0V star not known to host a CS disk, and Vega (A0V), an A0V star hosting a well-known face-on debris disk. We convolved the HD 34203 and Vega spectra with a rotational kernel to visually match the rotationally-broadened features of $\eta$ Tel, which is viewed edge-on and therefore has maximal rotational broadening. We find no evidence of a similar narrow feature at 1594 Å in either spectrum, additionally indicating that it is not stellar in origin.

# Velocity structure of the line of sight

## Radial velocity of the ISM

The $\eta$ Tel STIS spectra provide new measurements of the local ISM in the direction of $\eta$ Tel, which we compare to a kinematic model of the ISM[^3] (cite: Redfield2008). According to the model, the $\eta$ Tel line of sight ($l=342.90^{\circ}$, $b=-26.21^{\circ}$, $d=47.36$ pc; (cite: Brown2018)) does not traverse any known ISM clouds. However, the boundaries of individual local clouds are not well sampled by current data sets, and the $\eta$ Tel sight line probably does traverse at least one cloud. The kinematic model indicates $\eta$ Tel’s sight line passes near the LIC, G, Aql, and Vel clouds, which have radial velocities of $-16.62 \pm 1.17$ km s$^{-1}$, $-18.51 \pm 1.51$ km s$^{-1}$, $-10.28 \pm 1.03$ km s$^{-1}$, and $-27.59 \pm 1.37$ km s$^{-1}$, respectively. The radial velocity of the absorption components identified as IS in Table [\[table:lines\]](#table:lines) have a weighted average radial velocity $v_{\rm r} = -17.8\pm0.7$ km s$^{-1}$ (excluding Mg II), which is consistent with the LIC and G cloud velocities. We conclude that these local IS clouds have a somewhat greater extent than previously thought.

The Mg II absorption lines are not well fit with an IS component near $-18$ km s$^{-1}$, but rather the IS component appears at $-10.16^{+1.31}_{-1.34}$ km s$^{-1}$. We created alternate models of the Mg II lines that contained different numbers of absorption components and fit them using various parameter restrictions to see if a model with a component at the regular CS velocity ($-20$ to $-25$ km s$^{-1}$) and a component at the regular IS velocity ($-20$ to $-15$ km s$^{-1}$) was consistent with the data. However, these fits were poorly constrained and an absorption component near $-10$ km s$^{-1}$ was still required. An IS absorber at $-10$ km s$^{-1}$ is consistent with the radial velocity of the Aql cloud. It appears that the Mg II IS absorption component arising in the LIC/G clouds is lost in the saturated CS Mg II absorption component, but absorption arising in the Aql cloud is detectable for this feature alone due to the high oscillator strengths of the Mg II transitions.

## Radial velocity of the star

The radial velocity of the central star is critical for interpreting the kinematics of the CS absorbers. $\eta$ Tel’s radial velocity is reported in the literature as $v_\star = +13.0 \pm 3.7$ km s$^{-1}$ (cite: Kharchenko2007), $-3.0\pm 3.0$ km s$^{-1}$ (cite: Rebollido:2018), and $-5.0 \pm 1.5$ km s$^{-1}$ (cite: Rebollido:2020). Measuring the radial velocity of a rapidly rotating young A star is notoriously difficult given the large width and blending of the photospheric lines. In order to clearly determine the stellar radial velocity, we fitted a rotationally broadened Gaussian model to a clean, single stellar photospheric absorption line in the STIS data (Al II at 1670 Å; Figure [15](#fig:RV)). We allowed all model parameters ($v_\star$, FWHM, $v \sin i$, and linear limb darkening) to vary within a range of reasonable values, and we find $v_\star = -5.6 \pm 2.8$ km s$^{-1}$ relative to the rest wavelength of Al II. Our measured radial velocity is consistent with (cite: Rebollido:2018) and (cite: Rebollido:2020). In the rest of this paper, we adopt the $v_\star$ value from our Al II analysis ($-5.6$ km s$^{-1}$) as the stellar radial velocity.

![](etaTel_RV_plot.png)

# Elemental Abundances

## Ionization Balance in the CS Gas

To determine the elemental abundances in the CS gas, we must consider how much gas is present in all the dominant ionization states. Ideally, the column density in every ionization state would be measured and summed to provide a total elemental column density; however, the necessary transitions are not all present in the wavelength range of our data. Therefore, we make use of ionization balance calculations for the circumstellar environment of an A0V star. The neutral fractions (${n_0}/{n_+}$) from (cite: Fernandez:2006) appear in Table [\[table:abundances\]](#table:abundances). Using these fractions, we can estimate the abundance of an element in an unseen ionization state from measurements of the column density in a different ionization state.

lCLcRR Element & ${n_0}/{n_+}$ $^{a}$ & $\log_{10} N_{\rm total}$ & Element & $\log_{10} \mathrm{ratio}$ & $\log_{10}$ ratio $^{b}$\
& & $\mathrm{cm}^{-2}$ & Pair & $\eta$ Tel & solar\
C & 0.01 & $16.17^{+0.18}_{-0.36}$  $^{c}$ & C/Fe & $2.69^{+0.18}_{-0.36}$ & $0.94 \pm 0.09$\
N & $\sim 1$  $^{d}$ & & N/Fe & $0.14 - 3.69$ & $0.38 \pm 0.14$\
O & $\sim 1$  $^{d}$ & $16.17^{+0.21}_{-0.30}$ & O/Fe & $2.69^{+0.21}_{-0.29}$ & $1.24 \pm 0.09$\
Mg & $6 \times 10^{-6}$ & $14.16^{+0.08}_{-0.07}$ & Mg/Fe & 0.69$^{+0.08}_{-0.07}$ & $0.10 \pm 0.08$\
Al & $1 \times 10^{-7}$ & $12.44^{+0.04}_{-0.02}$ & Al/Fe & $-1.03^{+0.03}_{-0.03}$ & $-0.98 \pm 0.11$\
Si & $2 \times 10^{-7}$ & $14.04^{+0.03}_{-0.03}$ & Si/Fe & $0.57^{+0.03}_{-0.03}$ & $0.09 \pm 0.09$\
S & $5 \times 10^{-4}$ & $14.35^{+0.03}_{-0.06}$ & S/Fe & $0.87^{+0.04}_{-0.05}$ & $-0.25 \pm 0.09$\
Mn & $\sim 6 \times 10^{-6}$  $^{d}$ & $11.76^{+0.03}_{-0.03}$ & Mn/Fe & $-1.72^{+0.03}_{-0.03}$ & $-1.95 \pm 0.09$\
Fe & $3 \times 10^{-6}$ & $13.48^{+0.01}_{-0.01}$ & C/O & $-0.03^{+0.35}_{-0.40}$ & $-0.30 \pm 0.06$

Table notes: $^{a}$ Calculated ionization fractions for CS gas around an A0V star from (cite: Fernandez:2006). $n_e$=100 cm$^{-2}$ and $d$=100 au are assumed. $^{b}$ From (cite: Lodders2003). $^{c}$ Total C column density measured via direct observation of C I and C II in the STIS data. $^{d}$ Assumed from gas ionization balance; see main text.

Calculated neutral fractions for N, O, and Mn do not appear in (cite: Fernandez:2006). However, we inferred the neutral fractions for these species given their ionization energies. The first ionization energies of N and O (14.53 eV and 13.62 eV) are greater that of H (13.60 eV). Therefore, the bulk of the N and O should be in their neutral states (N I and O I), and we adopted the measured N I and O I column densities as the total N and O column densities. The first ionization energy of Mn (7.43 eV) is similar to that of Mg (7.65 eV). Therefore, we adopted the calculated Mg neutral fraction value from (cite: Fernandez:2006) for Mn.

The neutral fractions show that the $\eta$ Tel CS gas is highly ionized, with only trace amounts of neutral Mg, Al, Si, S, Mn, and Fe. Our measurements of the CS column densities of C I and C II in all fine structure energy levels of the ground term provide a check on the ionization balance calculations. The total circumstellar C I column density in all fine structure energy levels is $9.43 \times 10^{11} \ \mathrm{cm}^{-2}$ and the total circumstellar C II column density in all fine structure levels is $1.48 \times 10^{16} \ \mathrm{cm}^{-2}$, giving a neutral fraction of $6 \times 10^{-5}$. This is smaller than the calculated ionization balance of 0.01 from (cite: Fernandez:2006), which was estimated assuming $n_e$=100 cm$^{-3}$ and a 100 au distance from the star, indicating that the $\eta$ Tel gas is closer to the star and/or less dense. However, this does not significantly affect our general conclusions about the relative elemental abundances in the CS gas.

## Total Elemental Column Densities

Using this information about the dominant ionization state for each element, we determined the total CS column densities for all studied elements, given in Table [\[table:abundances\]](#table:abundances). Since Mg, Al, Si, S, Mn, and Fe should be primarily in the first ionized state, the total column densities for these elements were taken to be equal to the total CS column densities of Mg II, Al II, Si II, S II, Mn II, and Fe II in all fine structure energy levels of the ground term (given in Table [\[table:lines\]](#table:lines)). Nitrogen and oxygen, on the other hand, should be primarily neutral; therefore, the total column densities for these elements were taken to be equal to the total CS column densities of N I and O I in all fine structure levels of the ground term. For carbon, the total elemental CS column density is the sum of the measured CS column densities in all fine structure levels for both the neutral and first ionized states.

Because the marginalized probability distributions for the fitted column densities are often not Gaussian, we determined the error bars for the total elemental column densities using a Monte Carlo routine. Using C as an example, 10$^6$ random draws were made from each of the probability distributions of $N$(C I), $N$(C I\*), $N$(C I\*\*), $N$(C II), and $N$(C II\*). The error bars for $N($C$)_{\mathrm{total}}$ were then taken as the 68% confidence interval of the distribution of the summed column densities.

## Relative Elemental Abundances

A similar Monte Carlo process was used to calculate the relative abundances C/Fe, N/Fe, O/Fe, Mg/Fe, Al/Fe, Si/Fe, S/Fe, Mn/Fe, and C/O in the $\eta$ Tel CS gas. 10$^6$ random draws were made from the marginalized probability distributions representing the total C, N, O, Mg, Al, Si, S, Mn, and Fe column densities to construct a probability distribution for each ratio. We report the best-fit (median) values and 68% confidence intervals in Table [\[table:abundances\]](#table:abundances), along with the solar relative elemental ratios from (cite: Lodders2003). Figure [16](#fig:abundances) shows our relative abundance measurements compared to solar. In the $\eta$ Tel CS gas, C, O, Mg, Si, S, and Mn all show super-solar abundances relative to Fe. On the other hand, the Al/Fe ratio is consistent with solar abundance. While N may also show super-solar abundance relative to Fe, the large limits on the N I column density allow the N/Fe ratio to be consistent with the solar value.

![](etaTel_abundances.png)

Given the critical role that C and O play in the formation of planetary material and the debate about the C/O ratio in the $\beta$ Pic CS gas (cite: Brandeker2016), we took a close look at this ratio for $\eta$ Tel. We derived the C/O ratio and 68% confidence interval ($\log_{10} \mathrm{C/O} = -0.03^{+0.35}_{-0.40}$) in the same manner described above. In contrast to $\beta$ Pic and 49 Cet, which show super-solar abundance of C relative to O in UV absorption spectra (cite: Roberge2006; Roberge2014), we find that the C/O ratio in the $\eta$ Tel CS gas is consistent with the solar C/O ratio. The final picture of the $\eta$ Tel CS gas is one that is enriched in lighter elements relative to iron, but does not show an abundance anomaly among the volatile elements. The fact that Al alone among the siderophile elements shows solar abundance relative to Fe appears puzzling, but may point to the mineralogy of the $\eta$ Tel CS dust.

# Gas Dynamics

## Radiation Pressure

To analyze the dynamics of the CS absorbers, we computed the ratio ($\beta$) of radiation pressure to gravitational force that CS atoms and molecules receive from the $\eta$ Tel central star. Particles experiencing $\beta > 0.5$ will be pushed onto hyperbolic orbits and ejected from the system. To compute the stellar radiation pressure, we modeled the flux from the star using a synthetic spectrum from the Castelli-Kurucz atlas[^4] (cite: Castelli2003) with solar metallicity and $T_\mathrm{eff} = 9750$ K. Assuming a stellar radius of 1.61 R$_{\odot}$ (cite: Rhee2007) and distance to $\eta$ Tel of 47.36 pc (cite: GaiaDR2), we find that the synthetic spectrum matches the STIS spectrum within 50% in the $>$1600 Å spectral regions where they overlap. However, at $<$1600 Å, the agreement is poorer with the synthetic spectrum deviating from the observed spectrum by factors up to 3$\times$.

For each species listed in Table [\[table:lines\]](#table:lines), we include transitions with $E_l = 0$ cm$^{-1}$ using the line lists from (cite: Kurucz2011)[^5], computing the total radiation pressure in the same manner as (cite: Beust1993):

$$\begin{equation}
 \label{eq:radiationpressure}
F_\mathrm{rad} = \frac{1}{4\pi \epsilon_0}\frac{\pi e^2}{m_e c^2 } \sum_{i=1} f_i F_{\nu,i},
\end{equation}$$

where $e$ is the elementary charge, $m_e$ is the electron mass, $c$ is the speed of light, $f_i$ is the oscillator strength of the $i^{th}$ transition, and $F_{\nu, i}$ is the stellar flux at the wavelength of transition $i$. The gravitational force is given by

$$\begin{equation}
 \label{eq:gravity}
F_\mathrm{grav} = \frac{GM_{*}m_\mathrm{atom}}{d^2},
\end{equation}$$

where G is the gravitational constant, $M_{*}$ is the stellar mass, $m_\mathrm{atom}$ is the atomic mass, and $d$ is the distance of the atom from the star. The expression for $\beta$ is simply the ratio of Equations [\[eq:radiationpressure\]](#eq:radiationpressure) and [\[eq:gravity\]](#eq:gravity):

$$\begin{equation}
 \label{eq:beta}
\beta = \frac{1}{4\pi \epsilon_0}\frac{\pi e^2}{m_e c^2 } \frac{d^2}{GM_{*}m_\mathrm{atom}} \sum_{i=1} f_i F_{\nu,i}.
\end{equation}$$

Because the synthetic spectrum gives surface flux and therefore has a radius-squared dependency, the stellar surface gravity provides sufficient information for the $\beta$ calculation. We assume log $g_* = 4.2$ based on expectations for A0V stars[^6] (cite: Pecaut2013), and note that this value is similar to the log $g_* = 4.3$ value derived from high-resolution optical spectra of $\eta$ Tel (cite: Rebollido:2018). We adopt the smaller value to be consistent with the methodology used for other spectral types in Section [7.2](#subsec:spectraltype_beta). Our calculated $\beta$ values for $\eta$ Tel are listed in Table [\[table:lines\]](#table:lines), in parentheses to the right of each species label. We find that all atomic species except N I and S II have $\beta > 0.5$; in contrast to the situation for the A5V star $\beta$ Pic, carbon and oxygen are not bound to the hotter A0V star $\eta$ Tel.

Note that in our presented $\beta$ values, we assume that only the $E_l = 0$ cm$^{-1}$ levels are populated, and our results are not sensitive to this assumption. In the limiting case where we assume all levels with $E_l <$ 500 cm$^{-1}$ are uniformly populated, the $\beta$ values of C I, C II, O I, Si II, S I, and Fe II increase by factors of 1.7-3$\times$. Under either assumption, $\beta$ $>$ 0.5 for these species.

Compared to the A0V $\beta$ calculations from (cite: Fernandez:2006) (see their Table 4), this work’s $\beta$ values for Fe II, Si II, Mg II, S I, S II, and Al II are 1.3-10$\times$ larger, and our C I and C II values are larger by 17$\times$ and 190$\times$, respectively. For C II, the braking agent in the $\beta$ Pic and 49 Cet debris disks, this difference is critically important as it is the only species where (cite: Fernandez:2006) finds $\beta < 0.5$ while this work finds $\beta \gg 0.5$. Differences in $\beta$ of 1.3-10$\times$ can be accounted for in the different synthetic spectra and atomic data used between the two works. The larger differences in the carbon $\beta$ values may be explained by where the dominant transitions lie in the stellar spectrum. For C II, we find that the 1334.5 Å transition dominates the radiation pressure by many orders of magnitude. The stellar flux densities between approximately 1200-1700 Å are highly sensitive to the stellar effective temperature in the 9000-10,000 K range, and so small changes between the stellar properties used in this work and (cite: Fernandez:2006) might explain the drastically different carbon $\beta$ values. Although we selected the Castelli-Kurucz synthetic spectrum that most closely matched our STIS spectrum over all observed wavelengths, the low spectral resolution of the synthetic spectrum does not account for the presence of deep photospheric C II absorption lines, even for a rapidly rotating star like $\eta$ Tel. In the vicinity of 1335 Å, the $T_{eff}$ = 9750 K synthetic spectrum overestimates the true flux density as measured at high spectral resolution by STIS by a factor of three. We do not correct for this because $\beta$ would remain $\gg$0.5 and we wished to remain consistent in our use of synthetic spectra for $\beta$ calculations for other spectral types (Section [7.2](#subsec:spectraltype_beta)).

To calculate $\beta$ for CO, we used molecular data from (cite: Morton1994) for UV transitions originating from the ground vibrational state ($v=0$) and HITRAN for transitons at $\lambda > 6000$ Å (cite: Gordon2017). Assuming thermal equilibrium, we calculated the fractional level populations and incorporated this into the calculation in Equation [\[eq:radiationpressure\]](#eq:radiationpressure). We found that $\beta$ is $\sim 11.6$ for temperatures below 20 K and decreases to 2.7 at $T = 500$ K, indicating any CO gas is not bound to the star.

## A Radiatively Driven Disk Wind

In Figure [17](#fig:beta_comparison), we compare the radial velocities of the CS absorbers (Table [\[table:lines\]](#table:lines)) to their corresponding $\beta$ parameter. We find that all of the species have a similar RV for their CS components ($-22.7\pm0.5$ km s$^{-1}$) despite a wide range of $\beta$ values from 0.05 for S II to 365.7 for Mg II. All of the CS absorbers are blueshifted with respect to the star by $-16.9\pm2.6$ km s$^{-1}$, indicating that they are not bound to the star and are escaping in a disk wind. Note that the CS absorbers’ average radial velocity in the stellar rest frame was computed with the STIS relative, rather than absolute, wavelength accuracy value propagated into the measured velocities from Table [\[table:lines\]](#table:lines) and Figure [15](#fig:RV). Even N I and S II, the only detected CS species with $\beta < 0.5$, are outflowing. This indicates that the $\eta$ Tel CS gas is acting as a single fluid with a mean abundance-weighted $\beta > 0.5$. This is similar to $\beta$ Pic (cite: Fernandez:2006), except in the case of $\beta$ Pic, the mean $\beta$ of the fluid is less than 0.5 and the CS gas is bound to the star.

![](beta_CS_rv_comparison.png)

The key to C II acting as a braking agent in the case of $\beta$ Pic is that Coulomb forces increase the effective collisional cross-section for ions enough that the ionized gas can couple into a single fluid. Since C II has $\beta < 0.5$ in the $\beta$ Pic CS environment, an overabundance of carbon can lower the mean abundance-weighted $\beta$ of the ionic fluid enough that it remains bound. Like $\beta$ Pic and 49 Cet, $\eta$ Tel is overabundant in carbon relative to Fe. However, unlike those systems, $\eta$ Tel has significantly more flux at the carbon transitions with the largest absorption oscillator strengths; this increases the C I $\beta$ value to 51.7 and the C II $\beta$ value to 19.3. Therefore, carbon is unable to reduce the mean abundance-weighted $\beta$ of the $\eta$ Tel CS fluid below 0.5; no amount of C in this gas will bind it to the star.

Since N I and S II have $\beta < 0.5$, we consider whether these species *could* act as a braking agent in the case of $\eta$ Tel, although they obviously do not. Ion-induced polarization of neutral particles increases their collisional cross section by orders of magnitude (cite: Beust1989; Fernandez:2006), enabling gases like N I to act as a braking agent. N I is outflowing with the rest of the CS gas, indicating that it is coupled to the ionic gas through Coulomb forces or simply because the CS gas density is high enough. What overabundance of N I or S II would be required for these species to brake the whole $\eta$ Tel fluid remains a question for future dynamical modeling.

# Discussion

## Dynamics & Composition in $\eta$ Tel, $\beta$ Pic, and 49 Cet

The A0V spectral type of the $\eta$ Tel central star has a strong impact on the dynamics of the CS gas in this debris disk, producing an outflowing disk wind instead of the stable, bound gas disk seen around the A5V star $\beta$ Pic and the A1V star 49 Cet. Ironically, an outflowing disk wind is actually what was expected for $\beta$ Pic and the stability of the gas disk was puzzling for many years (cite: Lagrange:1998). The extreme overabundance of carbon in the $\beta$ Pic and 49 Cet gas disks is necessary to bind them to the central stars.

This raises the question whether the overabundance of carbon in the $\beta$ Pic and 49 Cet CS gas reflects nature or nurture, meaning whether the gas is produced with some initial overabundance of carbon (preferential production) or whether the overabundance evolves from a gas with initial solar composition by radiative blow-out of heavier elements (preferential depletion). The detailed abundance pattern in the $\beta$ Pic gas tends to favor preferential production (cite: Xie:2013; Wilson2019). In the case of $\eta$ Tel, the fact that all observed gas species are entrained in the radiatively driven disk wind, with no apparent dependence on $\beta$, qualitatively favors preferential production to explain the overabundance of volatiles and lithophiles relative to Fe. Alternatively, under-production of iron and other siderophiles might be causing an apparent overabundance of other elements.

## Impact of Spectral Type on Debris Disk Winds

To examine the effect of spectral type on the presence or absence of a disk wind more closely, we calculated the radiation pressure coefficients for a range of species as a function of the stellar effective temperature (Figure [18](#fig:beta_Teff)), using the approach described in Section [6.1](#sub:rad). For this analysis, we only considered spectral types A5V and earlier, where radiative equilibrium synthetic spectra that do not include chromospheric emission generally agree with observed spectra at UV wavelengths. We estimate effective temperature, mass, and radius from (cite: Pecaut2013) [^7]. The plot shows that at $T_\mathrm{eff}$ above about 10 200 K (between A0V and B9V), all of the considered species have $\beta > 0.5$ and cannot brake a gaseous fluid, no matter how abundant. We should therefore not expect to see bound gas in debris disks around stars with earlier spectral types, but rather disk winds. This expectation is consistent with observation of a low-velocity wind from the debris disk around the B9V star $\sigma$ Herculis (cite: Chen:2003).

This is not to say that debris disks around stars with spectral types later than about A0V/B9V must have bound stable gas. The presence or absence of a radiatively driven disk wind critically depends on the exact gas composition, as demonstrated in the case of $\beta$ Pic. Furthermore, for stars with spectral types later than about A5V, non-photospheric emission from stellar activity will come into play. The radiation pressure on a particular species depends on the exact stellar fluxes at the wavelengths of the absorbing transitions. One might therefore think that discrete stellar emission lines will not significantly impact the radiation pressure on a particular species. However, stellar emission lines involve many of the same transitions as the CS gas absorption lines. It is likely that a strong absorption line for a particular species will in fact overlap in wavelength with a stellar emission line, greatly increasing $\beta$. Also, stellar wind pressure may dominate over radiation pressure for late-type stars (e.g., (cite: Sezestre2017)). Therefore, there may be a limited range of spectral types outside of which disk winds dominate, although estimating the range is beyond the scope of this work.

![](beta_Teff_multiple_species.png)

Figure [18](#fig:beta_Teff) also indicates that C II braking becomes ineffective at stellar effective temperatures above about 8800 K (A2V). This seems to indicate that C II braking cannot explain the presence of a bound stable gas disk around the A1V star 49 Cet. However, difficulties in accurately modeling fluxes from real stars at the critical UV wavelengths and uncertainties in the atomic data itself lead to uncertainty in the exact threshold spectral type. A better understanding of the dynamics of the 49 Cet gas disk awaits abundance measurements for additional species in the gas (S II appears critically important) and detailed dynamical modeling.

As is the case for C II, stellar radiation pressure begins to dominate over gravity for CO above stellar effective temperatures of 8800 K (A2V). (cite: Roberge2000) found that CO is bound to the $\beta$ Pic (A5V) debris disk. This is consistent with our calculations that show $\beta \sim 0.02$ for A5V stars. Stable CO does not require C II braking in the $\beta$ Pic disk, a process that is not as efficient as for the ions anyway (cite: Brandeker2011). For $\eta$ Tel, any CO molecules should be blown out by the star, but the high stellar luminosity responsible for increasing $\beta$ also decreases CO’s photoionization lifetime, meaning that detectable levels of CO cannot accumulate (cite: Kral2017).

# Conclusion

The *HST*/STIS UV spectra of $\eta$ Tel contribute to the growing inventory of atomic gas in debris disks and highlight the coupled effects of stellar type and composition on the gas dynamics. Here we summarize our key results.

- Absorption lines arising from C I, C II, N I, O I, Mg II, Al II, Si II, S II, Mn II, and Fe II are detected in the spectra. The bulk of the gas is circumstellar rather than interstellar.

- No CO absorption along the line of sight to the central star is detected in the UV spectra. A new upper limit on pure rotational CO emission in ALMA data is presented, but is relatively insensitive.

- The CS gas appears to be overabundant in volatiles and siderophiles relative to iron. However, the C/O ratio is consistent with the solar ratio.

- All the CS gas is blueshifted with respect to the central star and appears at a similar radial velocity regardless of the radiation pressure coefficient for each species. The CS gas dynamically behaves as a single fluid and is blowing out as a disk wind.

- Compared to $\beta$ Pic (A5V), the hotter $\eta$ Tel (A0V) increases the radiation pressure coefficient for C II and prevents this species from braking the fluid despite the overabundance of C relative to Fe.

- Calculations of radiation pressure coefficients as a function of stellar effective temperature suggest that above about 10 200 K (A0V to B9V) bound gas should not occur in debris disks, but rather disk winds.

This work points to several avenues for exploration while forwarding our general understanding of gas in debris disks. Detailed dynamical modeling of the $\eta$ Tel gas should reveal whether preferential production explains the non-solar abundances. Similar modeling for 49 Cet is needed to identify the exact mechanism keeping the gas bound to the central star. A comprehensive investigation of the effect of spectral type on debris gas dynamics, with careful treatment of the stellar fluxes including chromospheric emission, could reveal which stars should show disk winds and which can have bound gas disks. Finally, sensitive UV spectra of more edge-on debris disks is needed to shed light on the detailed gas abundance patterns and what they might mean for the composition of the planetary material being destroyed to produce the gas.

# Acknowledgments

A.Y. acknowledges support by an appointment to the NASA Postdoctoral Program at Goddard Space Flight Center, administered by USRA through a contract with NASA. M.A.M. acknowledges support from a National Science Foundation Astronomy and Astrophysics Postdoctoral Fellowship under Award No. AST-1701406. S.P. acknowledges support ANID/FONDECYT Regular grant 1191934. We thank Seth Redfield for helpful comments about the ISM analysis. This research is based on observations made with the NASA/ESA *Hubble Space Telescope* obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with program HST-GO-14207 (PI: A. Roberge). The specific observations analyzed can be accessed via . This paper also makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.01147.S (PI: S. Pérez). ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This research has made use of NASA’s Astrophysics Data System Bibliographic Services and the SIMBAD database, operated at CDS, Strasbourg, France.

# Facilities

HST, ALMA

# Software

astropy (cite: Robitaille2013), IPython (cite: Perez2007), Matplotlib (cite: Hunter2007), NumPy and SciPy (cite: VanderWalt2011), lyapy (cite: Youngblood2016), emcee (cite: Foreman-Mackey:2013), CASA (cite: McMullin:2007), PyAstronomy[^8] (cite: pya), molecular-hydrogen[^9].

natexlab

(ref: Backman1993) Backman, D. E., & Paresce, F. 1993, in Protostars and Planets III, ed. E. H. Levy & J. I. Lunine, 1253

(ref: Beckwith1990) Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. 1990, AJ, 99, 924, doi: [`10.1086/115385`](http://doi.org/10.1086/115385)

(ref: Beust1989) Beust, H., Lagrange-Henri, A. M., Vidal-Madjar, A., & Ferlet, R. 1989, A&A, 223, 304

(ref: Beust1993) Beust, H., & Tagger, M. 1993, Icarus, 106, 42, doi: [`10.1006/icar.1993.1157`](http://doi.org/10.1006/icar.1993.1157)

(ref: Beust:1990) Beust, H., Vidal-Madjar, A., Ferlet, R., & Lagrange-Henri, A. M. 1990, A&A, 236, 202

(ref: Braithwaite2017) Braithwaite, J., & Spruit, H. C. 2017, Royal Society Open Science, 4, 160271, doi: [`10.1098/rsos.160271`](http://doi.org/10.1098/rsos.160271)

(ref: Brandeker2011) Brandeker, A. 2011, ApJ, 729, 122, doi: [`10.1088/0004-637X/729/2/122`](http://doi.org/10.1088/0004-637X/729/2/122)

(ref: Brandeker2016) Brandeker, A., Cataldi, G., Olofsson, G., et al. 2016, A&A, 591, A27, doi: [`10.1051/0004-6361/201628395`](http://doi.org/10.1051/0004-6361/201628395)

(ref: Brown2018) Brown, A. G. A., Vallenari, A., Prusti, T., et al. 2018, Astronomy & Astrophysics, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: Castelli2003) Castelli, F., & Kurucz, R. L. 2003, in Modelling of Stellar Atmospheres, ed. N. Piskunov, W. W. Weiss, & D. F. Gray, Vol. 210, A20

(ref: Cataldi:2014) Cataldi, G., Brandeker, A., Olofsson, G., et al. 2014, A&A, 563, A66, doi: [`10.1051/0004-6361/201323126`](http://doi.org/10.1051/0004-6361/201323126)

(ref: Chen:2003) Chen, C. H., & Jura, M. 2003, ApJ, 582, 443, doi: [`10.1086/344589`](http://doi.org/10.1086/344589)

(ref: Chen:2014) Chen, C. H., Mittal, T., Kuchner, M., et al. 2014, ApJS, 211, 25, doi: [`10.1088/0067-0049/211/2/25`](http://doi.org/10.1088/0067-0049/211/2/25)

(ref: Chen2006) Chen, C. H., Sargent, B. A., Bohac, C., et al. 2006, ApJS, 166, 351, doi: [`10.1086/505751`](http://doi.org/10.1086/505751)

(ref: Chen:2007) Chen, C. H., Li, A., Bohac, C., et al. 2007, ApJ, 666, 466, doi: [`10.1086/519989`](http://doi.org/10.1086/519989)

(ref: Czechowski:2007) Czechowski, A., & Mann, I. 2007, ApJ, 660, 1541

(ref: pya) Czesla, S., Schröter, S., Schneider, C. P., et al. 2019, PyA: Python astronomy-related packages, 0.16.0. [`http://ascl.net/1906.010`](http://ascl.net/1906.010)

(ref: Dent2013) Dent, W. R. F., Thi, W. F., Kamp, I., et al. 2013, PASP, 125, 477, doi: [`10.1086/670826`](http://doi.org/10.1086/670826)

(ref: Dent:2014) Dent, W. R. F., Wyatt, M. C., Roberge, A., et al. 2014, Science, 343, 1490

(ref: Fernandez:2006) Fernandez, R., Brandeker, A., & Wu, Y. 2006, ApJ, 643, 509

(ref: Foreman-Mackey2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, Publications of the Astronomical Society of the Pacific, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Foreman-Mackey:2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: GaiaDR2) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: Gordon2017) Gordon, I., Rothman, L., Hill, C., et al. 2017, Journal of Quantitative Spectroscopy and Radiative Transfer, 203, 3, doi: [`10.1016/j.jqsrt.2017.06.038`](http://doi.org/10.1016/j.jqsrt.2017.06.038)

(ref: Grigorieva:2007) Grigorieva, A., Thébault, P., Artymowicz, P., & Brandeker, A. 2007, A&A, 475, 755, doi: [`10.1051/0004-6361:20077686`](http://doi.org/10.1051/0004-6361:20077686)

(ref: Guenther2001) Guenther, E. W., Neuhäuser, R., Huélamo, N., Brandner, W., & Alves, J. 2001, A&A, 365, 514, doi: [`10.1051/0004-6361:20000051`](http://doi.org/10.1051/0004-6361:20000051)

(ref: Hales2014) Hales, A. S., De Gregorio-Monsalvo, I., Montesinos, B., et al. 2014, AJ, 148, 47, doi: [`10.1088/0004-6256/148/3/47`](http://doi.org/10.1088/0004-6256/148/3/47)

(ref: Hobbs:1985) Hobbs, L. M., Vidal-Madjar, A., Ferlet, R., Albert, C. E., & Gry, C. 1985, ApJL, 293, L29, doi: [`10.1086/184485`](http://doi.org/10.1086/184485)

(ref: Hughes:2018) Hughes, A. M., Duchêne, G., & Matthews, B. C. 2018, ARA&A, 56, 541, doi: [`10.1146/annurev-astro-081817-052035`](http://doi.org/10.1146/annurev-astro-081817-052035)

(ref: Hughes2017) Hughes, A. M., Lieman-Sifry, J., Flaherty, K. M., et al. 2017, The Astrophysical Journal, 839, 86, doi: [`10.3847/1538-4357/aa6b04`](http://doi.org/10.3847/1538-4357/aa6b04)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Jenkins2020_51Oph) Jenkins, E. B., & Gry, C. 2020, ApJ, 896, 24, doi: [`10.3847/1538-4357/ab8bdd`](http://doi.org/10.3847/1538-4357/ab8bdd)

(ref: Kharchenko2007) Kharchenko, N. V., Scholz, R. D., Piskunov, A. E., Röser, S., & Schilbach, E. 2007, AN, 328, 889, doi: [`10.1002/asna.200710776`](http://doi.org/10.1002/asna.200710776)

(ref: Kral:2019) Kral, Q., Marino, S., Wyatt, M. C., Kama, M., & Matrà, L. 2019, MNRAS, 489, 3670, doi: [`10.1093/mnras/sty2923`](http://doi.org/10.1093/mnras/sty2923)

(ref: Kral2017) Kral, Q., Matrà, L., Wyatt, M. C., & Kennedy, G. M. 2017, MNRAS, 469, 521, doi: [`10.1093/mnras/stx730`](http://doi.org/10.1093/mnras/stx730)

(ref: Kurucz2011) Kurucz, R. L. 2011, Canadian Journal of Physics, 89, 417, doi: [`10.1139/p10-104`](http://doi.org/10.1139/p10-104)

(ref: Lagrange:1998) Lagrange, A. M., Beust, H., Mouillet, D., et al. 1998, A&A, 330, 1091

(ref: LecavelierdesEtangs:2001) Lecavelier des Etangs, A., Vidal-Madjar, A., Roberge, A., et al. 2001, Nature, 412, 706

(ref: Lodders2003) Lodders, K. 2003, The Astrophysical Journal, 591, 1220, doi: [`10.1086/375492`](http://doi.org/10.1086/375492)

(ref: Lowrance2000) Lowrance, P. J., Schneider, G., Kirkpatrick, J. D., et al. 2000, ApJ, 541, 390, doi: [`10.1086/309437`](http://doi.org/10.1086/309437)

(ref: MacGregor2018) MacGregor, M. A., Weinberger, A. J., Wilner, D. J., Kowalski, A. F., & Cranmer, S. R. 2018, The Astrophysical Journal, 855, L2, doi: [`10.3847/2041-8213/aaad6b`](http://doi.org/10.3847/2041-8213/aaad6b)

(ref: Mamajek2014) Mamajek, E. E., & Bell, C. P. M. 2014, MNRAS, 445, 2169, doi: [`10.1093/mnras/stu1894`](http://doi.org/10.1093/mnras/stu1894)

(ref: Mannings1998) Mannings, V., & Barlow, M. J. 1998, ApJ, 497, 330, doi: [`10.1086/305432`](http://doi.org/10.1086/305432)

(ref: Matra:2017) Matrà, L., Dent, W. R. F., Wyatt, M. C., et al. 2017, MNRAS, 464, 1415, doi: [`10.1093/mnras/stw2415`](http://doi.org/10.1093/mnras/stw2415)

(ref: McCarthy2012) McCarthy, K., & White, R. J. 2012, The Astronomical Journal, 143, 134, doi: [`10.1088/0004-6256/143/6/134`](http://doi.org/10.1088/0004-6256/143/6/134)

(ref: McMullin:2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miles2016) Miles, B. E., Roberge, A., & Welsh, B. 2016, The Astrophysical Journal, 824, 126, doi: [`10.3847/0004-637X/824/2/126`](http://doi.org/10.3847/0004-637X/824/2/126)

(ref: Montgomery:2012) Montgomery, S. L., & Welsh, B. Y. 2012, PASP, 124, 1042, doi: [`10.1086/668293`](http://doi.org/10.1086/668293)

(ref: Moor:2017) Moór, A., Curé, M., Kóspál, Á., et al. 2017, ApJ, 849, 123, doi: [`10.3847/1538-4357/aa8e4e`](http://doi.org/10.3847/1538-4357/aa8e4e)

(ref: Morton2003) Morton, D. C. 2003, The Astrophysical Journal Supplement Series, 149, 205, doi: [`10.1086/377639`](http://doi.org/10.1086/377639)

(ref: Morton1994) Morton, D. C., & Noreau, L. 1994, The Astrophysical Journal Supplement Series, 95, 301, doi: [`10.1086/192100`](http://doi.org/10.1086/192100)

(ref: Pecaut2013) Pecaut, M. J., & Mamajek, E. E. 2013, ApJS, 208, 9, doi: [`10.1088/0067-0049/208/1/9`](http://doi.org/10.1088/0067-0049/208/1/9)

(ref: Perez2007) Perez, F., & Granger, B. E. 2007, Computing in Science & Engineering, 9, 21, doi: [`10.1109/MCSE.2007.53`](http://doi.org/10.1109/MCSE.2007.53)

(ref: Pollack1994) Pollack, J. B., Hollenbach, D., Beckwith, S., et al. 1994, ApJ, 421, 615, doi: [`10.1086/173677`](http://doi.org/10.1086/173677)

(ref: Rebollido:2018) Rebollido, I., Eiroa, C., Montesinos, B., et al. 2018, A&A, 614, A3

(ref: Rebollido:2020) —. 2020, arXiv e-prints, arXiv:2003.11084

(ref: Redfield2008) Redfield, S., & Linsky, J. L. 2008, The Astrophysical Journal, 673, 283, doi: [`10.1086/524002`](http://doi.org/10.1086/524002)

(ref: Rhee2007) Rhee, J. H., Song, I., Zuckerman, B., & McElwain, M. 2007, ApJ, 660, 1556, doi: [`10.1086/509912`](http://doi.org/10.1086/509912)

(ref: RiviereMarichalar2014) Riviere-Marichalar, P., Barrado, D., Montesinos, B., et al. 2014, A&A, 565, A68, doi: [`10.1051/0004-6361/201322901`](http://doi.org/10.1051/0004-6361/201322901)

(ref: Roberge2000) Roberge, A., Feldman, P. D., Lagrange, A. M., et al. 2000, ApJ, 538, 904, doi: [`10.1086/309157`](http://doi.org/10.1086/309157)

(ref: Roberge2006) Roberge, A., Feldman, P. D., Weinberger, A. J., Deleuil, M., & Bouret, J.-C. 2006, Nature, 441, 724, doi: [`10.1038/nature04832`](http://doi.org/10.1038/nature04832)

(ref: Roberge2014) Roberge, A., Welsh, B. Y., Kamp, I., Weinberger, A. J., & Grady, C. A. 2014, The Astrophysical Journal, 796, L11, doi: [`10.1088/2041-8205/796/1/L11`](http://doi.org/10.1088/2041-8205/796/1/L11)

(ref: Robitaille2013) Robitaille, T. P., Tollerud, E. J., Greenfield, P., et al. 2013, Astronomy & Astrophysics, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Saffe2008) Saffe, C., Gómez, M., Pintado, O., & González, E. 2008, A&A, 490, 297, doi: [`10.1051/0004-6361:200810260`](http://doi.org/10.1051/0004-6361:200810260)

(ref: Sezestre2017) Sezestre, É., Augereau, J. C., Boccaletti, A., & Thébault, P. 2017, A&A, 607, A65, doi: [`10.1051/0004-6361/201731061`](http://doi.org/10.1051/0004-6361/201731061)

(ref: Smith2009) Smith, R., Churcher, L. J., Wyatt, M. C., Moerchen, M. M., & Telesco, C. M. 2009, A&A, 493, 299, doi: [`10.1051/0004-6361:200810706`](http://doi.org/10.1051/0004-6361:200810706)

(ref: VanderWalt2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science & Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: Welsh2018) Welsh, B. Y., & Montgomery, S. L. 2018, MNRAS, 474, 1515, doi: [`10.1093/mnras/stx2800`](http://doi.org/10.1093/mnras/stx2800)

(ref: Wilson2019) Wilson, P. A., Kerr, R., Lecavelier des Etangs, A., et al. 2019, A&A, 621, A121, doi: [`10.1051/0004-6361/201834346`](http://doi.org/10.1051/0004-6361/201834346)

(ref: Xie:2013) Xie, J.-W., Brandeker, A., & Wu, Y. 2013, ApJ, 762, 114, doi: [`10.1088/0004-637X/762/2/114`](http://doi.org/10.1088/0004-637X/762/2/114)

(ref: Youngblood2016) Youngblood, A., France, K., Loyd, R. O. P., et al. 2016, ApJ, 824, 101, doi: [`10.3847/0004-637X/824/2/101`](http://doi.org/10.3847/0004-637X/824/2/101)

(ref: Zuckerman:1995) Zuckerman, B., Forveille, T., & Kastner, J. H. 1995, Nature, 373, 494

(ref: Zuckerman:2012) Zuckerman, B., & Song, I. 2012, ApJ, 758, 77

(ref: Zuckerman2001) Zuckerman, B., Song, I., Bessell, M. S., & Webb, R. A. 2001, ApJL, 562, L87, doi: [`10.1086/337968`](http://doi.org/10.1086/337968)

[^1]: STIS Instrument Handbook, version 19.0: <https://hst-docs.stsci.edu/stisihb>.

[^2]: STIS Instrument Handbook, version 19.0: <https://hst-docs.stsci.edu/stisihb>.

[^3]: <http://lism.wesleyan.edu/LISMdynamics.html>

[^4]: <https://www.stsci.edu/hst/instrumentation/reference-data-for-calibration-and-tools/astronomical-catalogs/castelli-and-kurucz-atlas>

[^5]: <http://kurucz.harvard.edu/linelists/gfall>

[^6]: <http://www.pas.rochester.edu/~emamajek/EEM_dwarf_UBVIJHK_colors_Teff.txt>

[^7]: <https://www.pas.rochester.edu/~emamajek/EEM_dwarf_UBVIJHK_colors_Teff.txt>

[^8]: <https://github.com/sczesla/PyAstronomy>

[^9]: <https://github.com/keflavich/molecular_hydrogen>

</paper>

Write the methods card for this paper.