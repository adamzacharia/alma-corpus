# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...901...71S\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...901...71S",
 "title": "Low-level Carbon Monoxide Line Polarization in Two Protoplanetary Disks: HD 142527 and IM Lup",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "Stephens, Ian W.",
 "n_authors": 5,
 "arxiv_id": "2008.04952",
 "doi": "10.3847/1538-4357/abaef7",
 "alma_projects_linked_by_archive": [
  "2015.1.00425.S",
  "2016.1.00712.S",
  "2018.1.01172.S"
 ]
}
```

Paper text:
<paper>
# Low Level Carbon Monoxide Line Polarization in two Protoplanetary Disks: HD 142527 and IM Lup

## Abstract

Magnetic fields are expected to play an important role in accretion processes for circumstellar disks. Measuring the magnetic field morphology is difficult, especially since polarimetric (sub)millimeter continuum observations may not trace fields in most disks. The Goldreich-Kylafis (GK) effect suggests that line polarization is perpendicular or parallel to the magnetic field direction. We attempt to observe CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1) line polarization toward HD 142527 and IM Lup, which are large, bright protoplanetary disks. We use spatial averaging and spectral integration to search for signals in both disks, and detect a potential CO(2–1) Stokes $Q$ signal toward both disks. The total CO(2–1) polarization fractions are 1.57 $\pm$ 0.18% and 1.01 $\pm$ 0.10% for HD 142527 and IM Lup, respectively. Our Monte Carlo simulations indicate that these signals are marginal. We also stack Stokes parameters based on the Keplerian rotation, but no signal was found. Across the disk traced by dust of HD 142527, the 3$\sigma$ upper limits for $P_{\text{frac}}$ at 0.5$\ensuremath{''}$ ($\sim$80 au) resolution are typically less than 3% for CO(2–1) and $^{13}$CO(2–1) and 4% for C$^{18}$O(2–1). For IM Lup  the 3$\sigma$ upper limits for these three lines are typically less than 3%, 4%, and 12%, respectively. Upper limits based on our stacking technique are up to a factor of $\sim$10 lower, though stacking areas can potentially average out small-scale polarization structure. We also compare our continuum polarization at 1.3 mm to observations at 870 $\mu$m from previous studies. The polarization in the northern dust trap of HD 142527 shows a significant change in morphology and an increase in $P_{\text{frac}}$ as compared to 870 $\mu$m. For IM Lup, the 1.3 mm polarization may be more azimuthal and has a higher $P_{\text{frac}}$ than at 870 $\mu$m.  \

# Introduction

Accretion from circumstellar disks is widely thought to be controlled by magnetohydrodynamic (MHD) turbulence driven by magnetorotational instability (cite: Balbus1998) and/or by a magnetically driven disk-wind (cite: Konigl2000). Despite their perceived importance, measuring the field morphology and strength in these disks has been quite difficult. The most common way to measure the magnetic field morphology in the interstellar medium is via (sub)millimeter dust polarization observations. Small grains ($\lesssim$10 $\mu$m) are expected to align their short axes with the magnetic field direction, which causes thermal emission from these grains to be polarized perpendicular with the magnetic field (cite: Andersson2015). However, the larger the grains, the more likely the will align with their long axes perpendicular to the radiation anisotropy (cite: LazarianHoang2007; Tazaki2017). Moreover, if grains are comparable to the wavelength, efficient dust self-scattering (i.e., emission from one grain scatters off another grain) can cause a polarization signal. High optical depths, such as those estimated for HL Tau at (sub)millimeter wavelengths (cite: Carrasco2016; Carrasco2019), will also increase the chance that polarization is from scattering rather than from aligned grains (cite: Yang2017).

Given that disks often have larger grains and higher optical depths compared to the interstellar medium, (sub)millimeter polarization observations in disks may not show the magnetic field morphologies. Indeed, polarimetric observations toward disks at 870 $\mu$m and 1.3 mm primarily show a mostly uniform polarization morphology parallel with the minor axis (cite: Stephens2014b; FL2016; Stephens2017c; Bacciotti2018; Hull2018; Dent2019; Sadavoy2019), which is a signature of dust scattering from grains that are $\sim$10–200 $\mu$m in size (cite: Kataoka2015; Yang2016a). Polarization from scattering at longer wavelengths is expected to be minimal since the largest grains are much smaller than the wavelength. Indeed, at 3 mm for the disks HL Tau, DG Tau, and Haro 6–13, the polarization is azimuthal, and thus is probably not from scattering nor from grains aligned with a (commonly expected) toroidal magnetic field (cite: Kataoka2017; Stephens2017c; Harrison2019). The polarization may be due to alignment with the radiation anisotropy (cite: Tazaki2017), but polarization from such mechanism for at least HL Tau has been seriously questioned (cite: Yang2019). Other studies also show polarization signatures that indicate polarized emission from aligned dust grains even at 870 $\mu$m (cite: Alves2018; Ohashi2018), but it is uncertain whether or not these grains are truly aligned with the magnetic field.

Magnetic fields also can be probed via polarimetric line observations, either through the Zeeman effect (cite: CrutcherKemball2019) or via the Goldreich-Kylafis effect (cite: Goldreich1981). The Zeeman effect measures the magnetic field strength along the line of sight and requires observations of circular polarization (Stokes $V$) of spectral lines. Additionally, the Zeeman effect is strongest only for paramagnetic molecular species (i.e., one with an unpaired electron), such as CN, H I, or OH. While this effect may have been detected toward the innermost region of an accretion disk of FU Orionis via lines in the optical (cite: Donati2005), it has yet to be detected in the bulk of the disk, despite recent attempts with the CN line at millimeter wavelengths ((cite: Vlemmings2019); R. Harrison submitted).

The GK effect suggests that linear polarization (Stokes $Q$ and $U$) from spectral lines measure the magnetic field morphology in the plane of the sky. This effect predicts that a molecule within a magnetic field has its rotational transition split into magnetic sublevels. Depending on the population imbalance of the $\pi$ or $\sigma$ transitions, polarization from the spectral lines are expected to be either parallel or perpendicular to the magnetic field. The fraction of polarized light, $P_{\text{frac}}$, is expected to be maximum when the magnetic field and velocity gradient is perpendicular along the line of sight (cite: Deguchi1984). Line polarization attributed to the GK effect has been detected in numerous star-forming regions, molecular clouds, and protostellar outflows (cite: Glenn1997b; Greaves1999; Girart1999; Greaves2001; Lai2003; Cortes2005; CortesCrutcher2006; Cortes2006; Cortes2008; Forbrich2008; Beuther2010; LiHenning2011; Vlemmings2012; Houde2013; Hezareh2013; LeeCF2014; Ching2016; LeeCF2018b; Hirota2020), evolved stars (cite: Glenn1997a; Girart2012; Vlemmings2017; Shinnaga2017; Chamma2018; Huang2020), and possibly a protoplanetary nebula (cite: Sabin2019). Resonant scattering (cite: Houde2013) of the linearly polarized signal can lead to circular polarization (Stokes $V$). Detections of resonant scattering has been suggested toward molecular clumps and an evolved star (cite: Houde2013; Hezareh2013; Chamma2018).

A spatially resolved detection of linear or circular polarized light from a molecular rotational transition in a disk has yet to be found. In this paper, we attempt to detect polarized emission from the $J = 2 \rightarrow 1$ rotational transitions of the molecular lines CO, $^{13}$CO, and C$^{18}$O in the disks HD 142527 and IM Lup. We primarily attempt to detect linear polarization (Stokes $Q$ and $U$) but we also present Stokes $V$ results. A polarized signal is not immediately obvious from the Stokes images, so we use stacking and spatial averaging over an integrated velocity range to look for a signal. In Section [2](#sec:obs) we describe the targets and the observations. In Section [3](#sec:results) we show the 1.3 mm polarized continuum images and line observations, and discuss the optical depth of each spectral line. In Section [4](#sec:search) we present our stacking and how we spatial average an integrated velocity range. In Section [5](#sec:constrain) we give constraints on $P_{\text{frac}}$, and in Section [6](#sec:summary) we summarize the results.

# Observations

## Targets

We selected the disks HD 142527 and IM Lup since they are large in the sky and are known to be bright for CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1) transitions (cite: PerezS2015; Cleeves2016). These two features are important because we need bright lines over a large solid angle to measure the field morphology. These two targets are among the largest and brightest known disks with simple CO morphologies. They are also close enough to each other that they can share the same phase calibrator, and thus both can be efficiently observed during a single observation run. These disks are also no longer embedded in their natal envelopes, so the molecular line emission should come solely from the disk. Moreover, HD 142527 is mostly face-on while IM Lup is at an intermediate inclination, which allows us to test how inclination affects the polarization.

HD 142527 is a close binary system located 157 pc away (cite: Arun2019). The primary is an Herbig star with a spectral type of F6–F7IIIe (cite: Malfait1998; vandenAncker1998), while the companion is an M-dwarf separated by $\sim$0.1$''$ (cite: Biller2012; Close2014; Lacour2016). HD 142527 is a well known transition disk with a very large central gap. It is highly asymmetric, with the majority of the dust emission detected toward the northern part of the disk.

IM Lup is a K5 Class II T Tauri star located 158 pc away (cite: Alcala2017; Gaia2018). High resolution ($\sim$5 au) 1.3 mm continuum observations reveal that the disk has spiral substructure (cite: Andrews2018).

## Observing Details and Data Reduction

Observations were conducted on 2019 April 29 using ALMA Band 6 (1.3 mm) under the project code 2018.1.01172.S (PI: I. Stephens). ALMA was using 46 antennas with baselines ranging between 15 and 704 m. Weather conditions were good for 1.3 mm, with the precipitable water vapor column of $\sim$0.85 mm and a system temperature oscillating between 60 and 120 K, depending on the spectral baseband and frequency. We chose Band 6 because this is the only ALMA band where the spectral lines CO, $^{13}$CO, and C$^{18}$O can be observed simultaneously. We tuned four ALMA basebands. One baseband was dedicated for the 1.3 mm dust continuum emission, and it was centered at 234.5 GHz and had a bandwidth of 2.0 GHz. The other three each had a bandwidth of 59 MHz and were centered on CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1). These basebands provided spectral resolutions of 0.079, 0.083, and 0.083 km s$^{-1}$, respectively. As typical with all ALMA observations, Hanning smoothing was applied by the correlator to reduce ringing in the spectra. We used the default correlator spectral averaging for each baseband, which is 2 channels averaged for the high spectral resolution basebands and no channels averaged for the continuum baseband. The observations toward HD 142527 and IM Lup were intertwined with periodic visits to the phase and polarization calibrators every $\sim$8 and $\sim$30 minutes, respectively. The total integrated time over each science target was 1 hour. For IM Lup, the phase center of the observations was errantly located 0.8$''$ west from the disk center.

Delivered data were manually calibrated by the North American ARC staff using the Common Astronomy Software Applications (CASA) package (cite: McMullin2007). J1427–4206 was used as the flux and bandpass calibrator, J1610–3958 was the phase calibrator, and J1517–2422 was the polarization calibrator. ALMA Band 6 observations have a typical absolute flux uncertainty of 10%, and the polarization uncertainties as determined by the D-terms were less than a 5%.

We imaged the continuum and spectral lines using CASA v5.6.0. To construct the continuum images, we combined the continuum baseband with the line-free channels of the other three basebands for a total bandwidth of 2.150 GHz. We ran three phase-only self-calibration iterations on the continuum Stokes $I$ data. The solution intervals used for the first, second, and third self-calibrations were infinite, 25 s, and 10 s, respectively. Self-calibration improved the continuum Stokes $I$ signal-to-noise ratio for HD 142527 and IM Lup by a factor of 6 and 3, respectively. The self-calibration solutions from the continuum Stokes $I$ were then applied to the continuum Stokes $QUV$ and the spectral line Stokes $IQUV$. For each spectral line, we subtracted the continuum emission by fitting the continuum using the baseband’s line-free channels. To clean the images, we use the CASA task `tclean` using Briggs weighting with a robust parameter of 0.5. The final continuum and line synthesized beams and noise levels are reported in Table [\[tab:obs\]](#tab:obs). All images in this paper have been corrected for the primary beam. The pixel size for our maps is 0.11$''$.

From the Stokes $IQU$ images, we constructed polarized intensity ($P_I$), $P_{\text{frac}}$, and position angle ($\chi$) maps where:

$$\begin{equation}
P_I = \sqrt{Q^2 + U^2}
\end{equation}$$ $$\begin{equation}
P_{\text{frac}} = P_I/I
\end{equation}$$ $$\begin{equation}
\chi = \frac{1}{2}\text{arctan}\left(\frac{U}{Q}\right) .
\end{equation}$$ Since $P_I$ can only be positive, it has an inherit bias toward positive values. We de-bias the values following (cite: Hull2015). In our images, we show the polarization as line segments. These segments are typically called “vectors." While we adopt this custom, we note that they are not true vectors because they have a 180$^\circ$ ambiguity in angle.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Image | Stokes | rms$^{a}$ | Channel Width | Synthesized beam |
|  |  | mJy bm$^{-1}$ | (km s$^{-1}$) | $\theta_{\text{maj}} \times \theta_{\text{min}}$; PA |
| *HD 142527* |  |  |  |  |
| 1.3 mm cont | $I$ | 0.037 | – | $0.51\ensuremath{''}\times0.45\ensuremath{''}$; $64.5\ensuremath{^\circ}$ |
| 1.3 mm cont | $QUV$ | 0.022 | – | $0.51\ensuremath{''}\times0.45\ensuremath{''}$; $64.5\ensuremath{^\circ}$ |
| CO(2–1) | $IQUV$ | 3.3 | 0.079 | $0.57\ensuremath{''}\times0.54\ensuremath{''}$; $71.3\ensuremath{^\circ}$ |
| $^{13}$CO(2–1) | $IQUV$ | 3.4 | 0.083 | $0.59\ensuremath{''}\times0.56\ensuremath{''}$; $74.2\ensuremath{^\circ}$ |
| C$^{18}$O(2–1) | $IQUV$ | 2.5 | 0.083 | $0.60\ensuremath{''}\times0.57\ensuremath{''}$; $69.7\ensuremath{^\circ}$ |
| *IM Lup* |  |  |  |  |
| 1.3 mm cont | $I$ | 0.022 | – | $0.51\ensuremath{''}\times0.44\ensuremath{''}$; $69.5\ensuremath{^\circ}$ |
| 1.3 mm cont | $QUV$ | 0.022 | – | $0.51\ensuremath{''}\times0.44\ensuremath{''}$; $69.5\ensuremath{^\circ}$ |
| CO(2–1) | $IQUV$ | 3.3 | 0.079 | $0.56\ensuremath{''}\times0.53\ensuremath{''}$; $75.2\ensuremath{^\circ}$ |
| $^{13}$CO(2–1) | $IQUV$ | 3.4 | 0.083 | $0.59\ensuremath{''}\times0.55\ensuremath{''}$; $79.3\ensuremath{^\circ}$ |
| C$^{18}$O(2–1) | $IQUV$ | 2.5 | 0.083 | $0.60\ensuremath{''}\times0.56\ensuremath{''}$; $74.9\ensuremath{^\circ}$ |

: Observational Parameters

Table notes: $^{a}$ For lines, this is per channel.

## Stokes $QUV$ Noise Characterization

In this paper, we will do extensive searches for a signal in CO(2–1) Stokes $QUV$. Therefore, it is important to understand the noise behavior of these Stokes parameters. We thus analyze the CO(2–1) Stokes $QUV$ noise on the maps before the primary beam correction.

For both HD 142527 and IM Lup, the noise across the entire CO(2–1) Stokes $QUV$ cubes are fit very well with a Gaussian, with an average value of 0.0 $\pm$ 3.3 mJy. We check for any spatial variation in each cube by creating a moment 6 maps (i.e., the root mean square of the spectrum). The average value in these maps are 3.3 $\pm$ 0.2 mJy, and the noise is once again Gaussian. The noise characteristics do not change for emission on and off the disk, nor for different velocity bins. As such, it appears the noise characteristics for these cubes are well behaved.

We checked the autocorrelation of our $QUV$ cubes to search for serial correlations for the noise along the spectral axis of these data. Correlation was found between consecutive channels, but no correlation was detected for the rest of the bandwidth (i.e., there was no periodic noise). This channel-to-channel correlation is due the Hanning smoothing applied by the ALMA correlator. As shown in (cite: Loomis2018), this Hanning smoothing plus a spectral averaging of 2 (i.e., the default averaging applied by the correlator to these data) provides a channel to channel covariance of 0.3 times the variance measured in a spectra.

# Results

## Continuum

![](hd142527_Band6pol_debiased_3sig.pdf)

![](imlup_Band6pol_debiased_3sig.pdf)

![](hd142527_polcomparisons.pdf)

![](imlup_polcomparisons.pdf)

We present the 1.3 mm continuum for HD 142527 and IM Lup in Figures [1](#fig:hd142527_cont) and [2](#fig:imlup_cont), respectively. ALMA polarization observations at 870 $\mu$m were previously presented for HD 142527 in (cite: Kataoka2016b) and (cite: Ohashi2018) and for IM Lup in (cite: Hull2018). Since the focus of this paper is on the line polarization, detailed multi-wavelength analysis is beyond the scope of this paper. We briefly comment on the results in this subsection.

For HD 142527, an analysis by (cite: Ohashi2018) suggested that two different polarization mechanisms create the polarization pattern observed at 870 $\mu$m. The northern part of the disk is optically thick, and the polarization morphologies show signatures of scattering (also see (cite: Kataoka2016b)). The southern part of the disk is optically thin, and the morphology and high values of $P_{\text{frac}}$ are suggestive of polarization due to aligned grains (cite: Ohashi2018). Since a radial polarization morphology is expected for a toroidal field (grains are expected to align with their short axes parallel with the magnetic field), (cite: Ohashi2018) attributes the southern morphology to grains aligned with a toroidal magnetic field.

To compare the dust continuum polarization observations for HD 142527 at 1.3 mm to those of archival 870 $\mu$m observations, we requested and downloaded calibrated data via the ALMA helpdesk (project code 2015.1.00425.S, PI: A. Kataoka). We re-imaged the calibrated data in the same manner as discussed in Section [2.2](#sec:datareduce). The final resolution was 0.27$''$ $\times$ 0.24$''$. We regridded the 1.3 mm observations to have the same pixel size used at 870 $\mu$m (0.06$''$), and we smoothed the 870 $\mu$m to have the same resolution as the 1.3 mm observations.

Figure [3](#fig:hd142527_comparisons) shows the comparisons of the polarization morphologies at the two wavelengths. The first two panels show the polarized intensity for each wavelength. Both have a strong peak toward the east. However, the 1.3 mm polarized intensity shows a strong peak toward the north, which is not seen at 870 $\mu$m. Moreover, the polarization vector direction changes substantially toward this northern region (i.e., toward the Stokes $I$ peak). The third panel shows the ratio of $P_{\text{frac}}$ between 1.3 mm and 870 $\mu$m, and the fourth shows the polarization position angle differences between 1.3 mm and 870 $\mu$m.

For both wavelengths, $P_{\text{frac}}$ and position angles toward the southern part of the disk are roughly identical, which is consistent with the aligned grain interpretation advocated by (cite: Ohashi2018). However, the ratio $P_{\rm{frac,1.3mm}}/P_{\rm{frac,870\mu m}}$ is slightly less than unity, which is unexpected since the emission at 1.3 mm is more optically thin than that at 870 $\mu$m and the polarization fraction is expected to increase with decreasing optical depth (cite: Yang2017), as seen with BHB07-11 (cite: Alves2018).

For the northern part of the disk, the polarization between wavelengths is substantially different, with $P_{\rm{frac,1.3mm}}/P_{\rm{frac,870\mu m}}$ reaching values as high as $\sim$5, and the difference in polarization angle is as large as $90^\circ$ (i.e., perpendicular). The Band 7 polarization was interpreted as coming from dust scattering, mainly because of the flip of the polarization orientations (from radial to azimuthal direction) across the horseshoe-shaped dust trap (cite: Ohashi2018). The flip is less prominent in Band 6 but is still present; it occurs at smaller radii compared to the Band 7 case. Whether it is still consistent with the scattering interpretation remains to be determined, and may require consideration of non-ideal polarization effects, such as large non-spherical grains polarizing emission beyond the Rayleigh regime (cite: Kirchschlager2020). Detailed modeling is needed but is beyond the scope of this paper.

For IM Lup, (cite: Hull2018) found that the detected 870 $\mu$m continuum polarization was mostly (but not completely) aligned with the minor axis, which is expected for scattering. To compare with these observations, we downloaded the polarization images provided in the online version of (cite: Hull2018), which have a resolution of 0.50$''$ $\times$ 0.40$''$. As above, we regridded the 1.3 mm observations to have the same pixel size that we used at 870 $\mu$m (0.1$''$), and we smoothed the 870 $\mu$m to have the same resolution as the 1.3 mm observations. We show the comparison in Figure [4](#fig:imlup_comparisons).

Along the major axis, (cite: Hull2018) detected polarization over an extent of $\sim$2$\ensuremath{''}$, while we detect it over $\sim$1.5$\ensuremath{''}$. Nevertheless, the 1.3 mm results show vectors less aligned with the minor axis than that found in (cite: Hull2018). The 1.3 mm polarization angles are suggestive of a more azimuthal morphology along the edges of the detected polarized emission, with the main differences at the northern and southern parts of the disk (right panel, Figure [4](#fig:imlup_comparisons)). This possible change in polarization morphology between the wavelengths of 870 $\mu$m and 1.3 mm was also found between these wavelengths for HL Tau (cite: Stephens2017c). This feature could possibly indicate two competing polarization mechanisms, such as scattering and alignment with the radiation anisotropy. Nevertheless, pure scattering models show that, while very optically thick regions show uniform vectors aligned with the minor axis, optically thinner regions have a significant azimuthal component (cite: Yang2017). Indeed, 1.3 mm dust emission is optically thinner than emission at 870 $\mu$m, so it is possible that the morphologies at both wavelengths can be explained by dust scattering.

Additionally $P_{\rm{frac,1.3mm}}/P_{\rm{frac,870\mu m}}$ is primarily larger than 1 for IM Lup. This feature is unexpected for optically thin dust grains of sizes $\sim$100 $\mu$m, as originally proposed by (cite: Hull2018). However, this might be explained via optical depth and beam smearing effects (cite: Lin2020b) or by grain sizes that are a few 100s of $\mu$m (cite: Kataoka2015; Kataoka2017).

## Line Observations

![image](hd142527_co_21_mom0.pdf) ![image](hd142527_13co21_mom0.pdf) ![image](hd142527_c18o21_mom0.pdf)

![image](imlup_co_21_mom0.pdf) ![image](imlup_13co21_mom0.pdf) ![image](imlup_c18o21_mom0.pdf)

We show integrated intensity (moment 0) maps of CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1) for HD 142527 and IM Lup in Figures [5](#fig:hd142527_mom0) and [6](#fig:imlup_mom0), respectively. Each image is overlaid with contours of the continuum emission. Compared to the continuum for both disks, CO(2–1) and $^{13}$CO(2–1) lines are detected over a larger extent than that seen for the continuum, while the C$^{18}$O(2–1) line is detected over roughly the same area. The measured dimensions of the major and minor axes over which CO(2–1) emission is detected are 11.2$\ensuremath{''}$ $\times$ 9.6$''$ (1760 $\times$ 1510 au) for HD 142527 and 12.0$\ensuremath{''}$ $\times$ 8.7$''$ (1900 $\times$ 1370 au) for IM Lup.

For HD 142527, the CO(2–1) moment 0 map (Figure [5](#fig:hd142527_mom0), left) indicates a spiral-like structure. The spiral structure is well known for this disk, as it was detected in the infrared (cite: Casassus2012; Rameau2012), in Near-IR $H$- and $K_{\text{s}}$-band polarimetric observations (cite: Canovas2013; Avenhaus2014), and in previous ALMA CO(2–1) and CO(3–2) observations (cite: Christiaens2014). The $^{13}$CO(2–1) and C$^{18}$O(2–1) emission is ring-like, with a local minimum of emission toward the center of the disk.

For IM Lup, a pinched pattern is seen in the CO(2–1) and $^{13}$CO(2–1) moment 0 maps, which indicates emission from gas above the midplane. CO(2–1) appears to be slightly asymmetric toward the northwest part of the disk. Like HD 142527, $^{13}$CO(2–1) and C$^{18}$O(2–1) line emission also have a local minimum toward the center of the disk. All of the above features were also mentioned in (cite: Cleeves2016).

## Optical Depth

Linear polarization due to the GK effect is largely affected by the optical depth of the spectral line (cite: Deguchi1984). The optical depth can be estimated from the ratio of brightness temperatures (cite: Lyo2011). Given the brightness temperature for the first and second line of $T_{B1}$ and $T_{B2}$, we can solve for the optical depth using the equation

$$\begin{equation}
\label{eq:opticaldepth}
R = \frac{T_{B1}}{T_{B2}} = \frac{1-e^{-\tau_1}}{1-e^{-\tau_2}}  = \frac{1-e^{-\tau_1}}{1-e^{-\tau_1/X}} .
\end{equation}$$

Since the conversion factor between flux and brightness temperature for each line in this study are roughly identical (vary by less than 1%), we instead use R = $F_{\nu 1}/F_{\nu 2}$. $X$ is the isotopic line ratio, which we adopt as \[$^{12}$CO\]/\[$^{13}$CO\] = 70 and \[$^{12}$CO\]/\[C$^{18}$O\] = 500. The optical depth was solved for numerically. We made optical depth maps (not shown) both channel by channel and from the integrated intensity maps of each line.

For HD 142527, the calculated optical depths at some locations are either highly uncertain or cannot be computed (i.e., the less abundant species is brighter, making Equation [\[eq:opticaldepth\]](#eq:opticaldepth) unsolvable), given that CO(2–1) emission has features of self-absorption and absorption against the continuum. We find that CO(2–1) optical depths are $>$30 for all locations except the center of the disk, where the optical depth is as low as 14. The optical depths of $^{13}$CO(2–1) across the disk, as calculated from its flux ratio with C$^{18}$O(2–1), range from $\sim$1 to 7, and the optical depth for C$^{18}$O(2–1) is between 0.1 and 1. When looking at optical depth maps channel by channel, CO(2–1) is optically thick at all velocities where both CO(2–1) and $^{13}$CO(2–1) are detected. At the highest velocities from systemic (at about 1 and 6.5 km s$^{-1}$), the CO(2–1) optical depths are $\sim$8–10.

For IM Lup, the optical depths could be calculated at all locations, though we note that there is likely some absorption against the continuum toward the center of the disk (cite: Cleeves2016). Based on the integrated intensity maps, we find that CO(2–1) optical depths are typically about 40, but range from about 10–100. Given the abundance ratios, $^{13}$CO(2–1) is just around the optically thick ($\tau$ = 1) regime, and C$^{18}$O(2–1) is optically thin. Again, when looking at optical depth maps channel by channel, CO(2–1) is optically thick at all velocities where both CO(2–1) and $^{13}$CO(2–1) are detected. At the highest velocities from systemic (at about 1.5 and 7.5 km s$^{-1}$), the CO(2–1) optical depths are $\sim$25.

Comprehensive models that show in detail how the values of $P_{\text{frac}}$ change with optical depth do not consider disks (the GK effect in disks is modeled in (cite: Lankhaar2020), which we will discuss in Section [6](#sec:summary)). These models simply consider molecules placed within a magnetic field, and may or may not have an additional external source of radiation. Without an external source of radiation, the GK effect is expected to be strongest at $\tau$ $\approx$ 1, and significantly reduced for high ($\gtrsim$10) and low ($\lesssim$0.1) optical depths (cite: Deguchi1984). In such a case, $^{13}$CO(2–1) is in the optimal optical depth range for a polarized signal detection, CO(2–1) is suboptimal, and C$^{18}$O(2–1) is mostly suboptimal (only toward select areas of HD 142527). However, when an external source is added (due to, for example, compact dust), CO emission is expected to be strongly polarized even at low optical depths and will be perpendicular to the polarization observed for $\tau$ $\approx$ 1 (cite: Cortes2005). Optically thick emission will again have very low values of $P_{\text{frac}}$. Given this model, we would expect the GK effect to be easier to detect for $^{13}$CO(2–1) and C$^{18}$O(2–1) rather than CO(2–1). However, as will be shown later in this paper, we only detect polarization for CO(2–1), albeit over a limited velocity range and area of the disk.

We stress that a disk is more complex than these models, as additional factors must be considered such as the disk’s inclination, density profile, and temperature profile. While these features are taken into account in the PORTAL software (cite: Lankhaar2020), the effect of optical depth on $P_{\text{frac}}$ was not discussed in detail, though it is mentioned that $P_{\text{frac}}$ is expected to be near 0 for high optical depths. Using PORTAL to show how optical depth changes the polarization of lines requires a detailed study that is beyond the scope of this paper.

Finally, it is worth mentioning that given the estimated densities for HD 142527 and IM Lup (cite: PerezS2015; Cleeves2016), the lines are certainly thermalized in the midplane. As such, collisions will dominate over the radiative rate, which causes no polarization from these spectral lines. However, polarized emission could potentially be emitted from less dense regions above the midplane.

# Searching for a Polarized Signal in Spectral Lines

In this section, we attempt a thorough search for the polarization in the CO isotopologues. When we mention Stokes parameters in this section, we specifically refer to the isotopologues and not the continuum.

For HD 142527 and IM Lup, Stokes $QUV$ maps appear to be pure noise if we integrate over the same velocity ranges as their respective Stokes $I$ images (i.e., those shown in Figures [5](#fig:hd142527_mom0) and [6](#fig:imlup_mom0)). Additionally, if we step through the Stokes $QUV$ images channel by channel, we see no strongly polarized signals at any velocity. In other words, any sort of polarization signal is not obvious for any of the observed spectral lines in both disks. We decided to do a deeper search for a polarized signal via spectral stacking and via spatial averaging over an integrated velocity range. We first motivate the stacking technique using a simple morphological model.

## Morphological Model

To motivate possible ways for stacking, we create model images of the expected Stokes $Q$ and $U$ maps for purely elliptical polarization for HD 142527 and IM Lup, which may be expected for a toroidal field. Along with measured quantities of the disks (e.g., inclinations and position angles), the only assumptions that go into the model is a surface density profile and a polarization morphology. This notably is not a model of the GK effect, as it ignores very important parameters such as the optical depth. The point of the model is to simply describe which quadrants of the disk we expect to see positive and negative values for Stokes $Q$ and $U$ based on an elliptical (and eventually radial; see below) polarization morphology.

Following (cite: Yang2019), we create an image of an elliptical polarization pattern for a disk with inclination, $i$. The polarization pattern is then rotated according to the position angle of the disk, PA. Each pixel of the image now has a polarization angle, $\theta_{\text{ell}}$, which is measured counterclockwise from north.

For HD 142527 we assume PA = 160$^\circ$ and $i$ = 28$^\circ$ (cite: PerezS2015), and for IM Lup we assume PA = 144$^\circ$ and $i$ = 48$^\circ$ (cite: Cleeves2016). We assume a surface density profile that follows the form in (cite: Andrews2011), and we assume the surface density is directly proportional to the Stokes $I$ flux such that $$\begin{equation}
\label{eq:surface}
I \propto \left(\frac{R}{R_c}\right)^{-\gamma} \text{exp}\left[-\left(\frac{R}{R_c}\right)^{2-\gamma}\right] ,
\end{equation}$$ where $R$ is the radius of the disk, $R_c$ is the characteristic radius, and $\gamma$ is the gas surface density exponent, which we assume to be 1. For HD 142527 and IM Lup, we assume $R_c$ is 200 and 100 au, respectively (cite: PerezS2015; Cleeves2016). From the Stokes $I$ and $\theta_{\text{ell}}$ maps, we can determine the Stokes parameters $Q$ and $U$ via

$$\begin{equation}
Q =  IP_{\text{frac}}\,\text{cos}(2\theta_{\text{ell}})
\end{equation}$$ $$\begin{equation}
U = IP_{\text{frac}}\,\text{sin}(2\theta_{\text{ell}}).
\end{equation}$$ For this model, we assume $P_{\text{frac}}$ to be constant across the disk. Then, $P_{\text{frac}}$ and the constant needed for the proportionality in Equation [\[eq:surface\]](#eq:surface) become a single constant, which we call $K$. We then smoothed each map to have the same resolution as our observations. For any value $K$ of these two disks, the Stokes $U$ peak ($U_{\text{max}}$) happens to be larger than that of Stokes $Q$. We then normalize both the Stokes $Q$ and $U$ maps by dividing by $U_{\text{max}}$ so that we can draw contours with respect to the maximum value in the Stokes images. Modeled polarization angles and Stokes $Q$ and $U$ contours for HD 142527 and IM Lup are shown in Figure [7](#fig:hd142527_model) and [8](#fig:imlup_model), respectively.

![](hd142527_polmod_arcsec.pdf)

![](imlup_polmod_arcsec.pdf)

Since the GK effect has an ambiguity with being perpendicular or parallel with the magnetic field, a radial polarization pattern is also possible for a toroidal field. In such a case, Figure [7](#fig:hd142527_model) and [8](#fig:imlup_model) would have to be modified by rotating all angles by 90$^\circ$ and by switching the Stokes $Q$ and $U$ contours with each other. Indeed, the GK disk model in (cite: Lankhaar2020) suggests that radial polarization would be seen for a face-on disk for both toroidal and radial magnetic fields.

It is also important to note that the angular extent of the gaseous disk goes substantially beyond what is shown in these models (Figures [5](#fig:hd142527_mom0) and [6](#fig:imlup_mom0)). The modeled Stokes $Q$ and $U$ emission declines rapidly with radius due to the exponential part of the assumed intensity profile (Equation [\[eq:surface\]](#eq:surface)). We note that the real Stokes $Q$ and $U$ contours levels could extend farther out if the polarized fraction is higher in the outer disk. A higher $P_{\text{frac}}$ in the outer disk indeed would be expected for CO(2–1) and $^{13}$CO(2–1), as the outer disk is less optically thick than the inner disk. Regardless of the assumptions about $P_{\text{frac}}$, we still expect the 4-petal daisy-like pattern in Stokes $Q$ and $U$ for elliptical and radial polarization patterns.

The 4-petal daisy-like pattern for the elliptical polarization model suggest four distinct disk wedges, where two wedges are positive and two wedges are negative. For Stokes $Q$, the intensity switches signs (e.g., from positive to negative) at around the major and minor axes of the disks. The four sign switches for Stokes $U$ are each located between two different sign switches for Stokes $Q$ (the $Q$ and $U$ maps are both 4-petal daisy-like patterns offset by $\sim$45$^\circ$). These transitions are at $\sim$45$^\circ$ from the major and minor axes when deprojected to the disk plane. Again, for a radial polarization pattern, Stokes $Q$ and $U$ contours are switched, so the separation between wedges would be at the same locations.

Since we want to make sure we avoid stacking areas of the disk with positive Stokes $Q$ and $U$ emission with those areas that are negative, these models motivate us to stack Stokes parameters spatially based on disk quadrants. These areas will be the basis of some of the stacking used in Section [4.2](#sec:gofish). We first stack based on deprojected disk quadrants starting at the major axis and binning for every 90$^\circ$. We then do 90$^\circ$ deprojected quadrants again, but this time starting at a deprojected angle 45$^\circ$ from the major axes. Moreover, for certain quadrants we cut out the central part of the disk to make sure we do not add positive with negative emission, which will be discussed in the next subsection.

We are binning based on 90$^\circ$ quadrants and start the binning for two separate position angles, which provides a fine probe in many areas of the disk. As such, the stacking method is likely to find polarization morphologies that are not elliptical or radial, if they exist.

## Stacking via `GoFish`

Spectral lines are Doppler shifted due to the rotational profile of the disk. A signal can be stacked for the Stokes parameters by aligning their spectra to common centroid velocities based on a disk’s deprojected Keplerian rotational profile. We do this by using the software package `GoFish` (cite: GoFish).

`GoFish` takes in a number of parameters to estimate the three-dimensional Keplerian rotational profile used for stacking. This includes the stellar mass, $M_\star$, the position angle of the major axis pointing to the most red-shifted side, PA$_{\text{red}}$, the inclination of the source, $i$, the distance to the source, $d$, and the emission scale height at 1$\ensuremath{''}$, $z_0$. We find estimates for most these parameters from disk models from (cite: PerezS2015) and (cite: Cleeves2016). For both disks we assume $z_0$ = 0.1$''$. For HD 142527, we assume $M_\star$ = 2.8 $M_\odot$, PA$_{\text{red}}$ = 160$^\circ$, $i$ = 28$^\circ$, and $d$ = 157 pc. For IM Lup, we assume $M_\star$ = 1 $M_\odot$, PA$_{\text{red}}$ = 144$^\circ$, $i$ = 48$^\circ$, and $d$ = 158 pc. For IM Lup, we also had to specify an x-offset of 0.8$\ensuremath{''}$ since the phase center was errantly offset to the disk center by this amount. Other input parameters for `GoFish` were all assumed to be their defaults.

![](hd142527_line=co_21_all_rmax=3.pdf)

![](imlup_line=co_21_all_rmax=4.pdf)

`GoFish` can also take in a minimum and maximum radius to apply the technique and can also integrate over user-specified disk wedges. We tried a vast mixture of wedges and radii for all 3 spectral lines. Nevertheless, we could not find a significant signal in Stokes $Q$, $U$, and $V$ via stacking. Here we present the stacking technique by first stacking each Stokes parameter across the entire disk, and then by stacking by the quadrants mentioned in Section [4.1](#sec:model). We first select the radius in the disk plane, $r_{\text{max}}$, over which we do the stacking. We choose a value where the Stokes $I$ flux drops to 90% of the peak value of the Stokes $I$ moment 0 map. Rounded to the nearest arcsecond for CO(2–1), $r_{\text{max}}$ is 3$\ensuremath{''}$ for HD 142527 and 4$\ensuremath{''}$ for IM Lup. The CO(2–1) results for HD 142527 and IM Lup are shown in Figures [9](#fig:hd142527_gofish_all) and [10](#fig:imlup_gofish_all). The results for $^{13}$CO(2–1) and C$^{18}$O(2–1) are shown in the Appendix.

![image]({hd142527_line=co_21_Qpanels_rmin=0.17_rmax=3.arches}.pdf) ![image]({hd142527_line=co_21_Upanels_rmin=0.17_rmax=3.arches}.pdf) ![image]({imlup_line=co_21_Qpanels_rmin=0.5_rmax=4.arches}.pdf) ![image]({imlup_line=co_21_Upanels_rmin=0.5_rmax=4.arches}.pdf) ![image]({hd142527_line=co_21_panels_rmin=0.17_rmax=3}.pdf) ![image]({imlup_line=co_21_panels_rmin=0.5_rmax=4}.pdf)

As mentioned in Section [4.1](#sec:model), for elliptical or radial polarization patterns, averaging polarization over the entire disk causes the fluxes of the Stokes $Q$ and $U$ parameters to be averaged out, as there are both positive and negative components (Figures [7](#fig:hd142527_model) and [8](#fig:imlup_model)). Therefore, we also use `GoFish` to stack for different quadrants (90$^\circ$ wedges) for each disk, as shown for CO(2–1) in Figure [11](#fig:gofish_everything). We choose four 90$^\circ$ quadrants, where each 90$^\circ$ quadrant is in reference to the disk’s axis rather than in projection. Since the Stokes $Q$ and $U$ contours each draw a 4-petal daisy-like pattern that offset from each other by $\sim$45$^\circ$ (Figure [7](#fig:hd142527_model) and [8](#fig:imlup_model)), we select four 90$^\circ$ quadrants where we start at PA$_{\text{red}}$, and another four where we start at PA$_{\text{red}}$ $-$ 45$^\circ$. Also, for elliptical polarization, the central region is expected to be negative for Stokes $Q$ and positive for Stokes $U$, which is especially evident for the inner 0.5$''$ for IM Lup (Figure [8](#fig:imlup_model)). As such, for alternating quadrants, we shift between $r_{\text{min}}$ = 0$\ensuremath{''}$ and 0.17$''$ for HD 142527, and $r_{\text{min}}$ = 0$\ensuremath{''}$ and 0.5$''$ for IM Lup. The quadrants with a non-zero $r_{\text{min}}$ are drawn in gray in Figure [11](#fig:gofish_everything). Once again, we select $r_{\text{max}}$ of 3$\ensuremath{''}$ for HD 142527 and 4$\ensuremath{''}$ for IM Lup.

No significant detection was found for any quadrant. Our attempts using other many other values for $r_{\text{min}}$ and $r_{\text{max}}$ (not shown) also did not detect any significant signal in any of the Stokes parameters. We also show the resulting non-detections for $^{13}$CO(2–1) and C$^{18}$O(2–1) in the Appendix. We discuss the constraints we can place on $P_{\text{frac}}$ from stacking (for the entire disk and for quadrants) in Section [5](#sec:constrain).

## Searching for Signal within an Aperture

For each spectral line, we also manually inspected the Stokes $Q$, $U$, and $V$ cubes for a signal. This search was done by looking at the average spectra within a circular aperture. The size and position of the circular aperture was changed, allowing us to carefully inspect Stokes $Q$, $U$, and $V$ spectra across the entire disk in which there is Stokes $I$ signal. Using this method, we found that for CO(2–1), there appears to be a signal in the Stokes $Q$ cube toward both disks.

We then developed a script that alters the size and position of the circular aperture to find the location with the highest signal to noise. Specifically, we found the location where SNR$_Q$ = $| \Sigma Q |$/$\sigma_{\Sigma Q}$ was maximum, where $| \Sigma Q |$ is the magnitude of the sum of Stokes $Q$ for $N$ consecutive channels and $\sigma_{\Sigma Q}$ is the error on the sum. As stated in Section [2.3](#sec:characterization), there exists a covariance between consecutive channels that is 0.3 times the variance in the spectrum. When accounting for these covariances, $\sigma_{\Sigma Q} = \sigma_{Q,ap} \sqrt{1.6N - 0.6}$, where $\sigma_{Q,ap}$ is the noise of Stokes $Q$ in a single channel for the spectra for an aperture. When searching for the highest SNR$_Q$ within a circular aperture, the aperture was centered on a pixel and radii had sizes that were integers.

![]({HD142527.detected}.pdf)

![]({imlup.detected_new}.pdf)

![](hd142527_IQUV_mom0cut.pdf)

![](imlup_IQUV_mom0cut_new.pdf)

Figures [12](#fig:hd142527_spectra_detected) and [13](#fig:imlup_spectra_detected) show the spectra of the four Stokes parameters where SNR$_Q$ is maximum for HD 142527 and IM Lup, respectively. These displayed spectra are the average spectra within the circular aperture, and the channels that were integrated to obtain the maximum SNR$_Q$ are shown in pink. For HD 142527 and IM Lup, the values for $\Sigma Q$ over the pink areas in Figures [12](#fig:hd142527_spectra_detected) and [13](#fig:imlup_spectra_detected) are 10.8 $\pm$ 1.2 mJy bm$^{-1}$ (SNR$_Q$ = 8.7) and 9.9 $\pm$ 1.0 mJy bm$^{-1}$ (SNR$_Q$ = 9.6), respectively. For HD 142527 and IM Lup, the values for $\Sigma U$ in the same areas are 2.7 $\pm$ 1.5 mJy bm$^{-1}$ and 3.7 $\pm$ 1.2 mJy bm$^{-1}$, respectively. At these locations for HD 142527 and IM Lup, the de-biased $P_{\text{frac}}$ is 1.56 $\pm$ 0.18% and 1.01 $\pm$ 0.10%, respectively. The position angles $\chi$ are 6.9$^\circ$ $\pm$ 3.9$^\circ$ and 10.1$^\circ$ $\pm$ 3.2$^\circ$, respectively.

We create moment 0 maps for each of the four CO(2–1) Stokes parameters integrated about the pink shaded velocity ranges. These maps are shown in Figures [14](#fig:hd142527_spectra_detected_IQUV) and [15](#fig:imlup_spectra_detected_IQUV) for HD 142527 and IM Lup, respectively. The circular aperture indicates the area where we show the average spectra in Figures [12](#fig:hd142527_spectra_detected) and [13](#fig:imlup_spectra_detected). For HD 142527, there is elevated emission across the major axis of the Stokes $Q$ image; given the sensitivity in the $QUV$ moment 0 maps is $\sigma$ = 0.78 mJy bm$^{-1}$ km s$^{-1}$, anything that is red-colored is above 2$\sigma$ and white-colored is above 3$\sigma$. While the $>$2$\sigma$ pixels are blotchy rather than a smooth cohesive structure, we note that for an image that is purely noise, only 2.3% of the area is expected to be above the 2$\sigma$ value. Since the Stokes $Q$ image of HD 142527 has a region where substantially more than 2.3% of the area is above 2$\sigma$, this is likely a robust detection. Similarly, the red and white colors for IM Lup (Figure [13](#fig:imlup_spectra_detected)) is above 2$\sigma$ and 3$\sigma$, respectively, as the $QUV$ moment 0 maps is $\sigma$ = 0.96 mJy bm$^{-1}$ km s$^{-1}$.

![image](hd142527_maxSNRQ.pdf)        ![image](imlup_maxSNRQ.pdf)

Since we used an algorithm that optimizes a circular aperture to have the best SNR as possible, we wanted to confirm that this algorithm does not create a false signal. We used a Monte Carlo simulation to find the typical SNR that one would expect at each pixel of our CO(2–1) Stokes $Q$ maps. As above, for each 0.11$''$ pixel, we searched for the highest SNR$_Q$ possible for a range of circular apertures and channels. We focused on pixels within a radius of 15$\ensuremath{''}$ from the center of the map, which allows us to probe well beyond the disks where Stokes $Q$ is expected to be pure noise. We tried circular apertures with integer radii sizes between 1 and 27 pixels (0.11$''$ $\times$ 3$\ensuremath{''}$). For every circular aperture, we looked for the highest SNR$_Q$ possible for 2 to 32 consecutive channels (i.e., a window of sizes between $\sim$0.16 and 2.5 km s$^{-1}$), restricting the search for a signal within a $v_{\text{lsr}}$ velocity range of 0 to 7 km s$^{-1}$ for HD 142527 and 1 to 8 km s$^{-1}$ for IM Lup. We chose a maximum window of 2.5 km s$^{-1}$ because this captures the majority of Stokes $I$ for any pixel, and we chose the $v_{\text{lsr}}$ ranges because they capture the vast majority of the Stokes $I$ emission across the entire map.

Figure [16](#fig:SNRQ) shows the maximum SNR$_Q$ at each pixel based on these Monte Carlo simulations. For HD 142527, the mean SNR$_Q$ for each pixel is 4.7 with a standard deviation of 0.9. The signal shown in Figure [12](#fig:hd142527_spectra_detected) is indeed the pixel with the highest SNR$_Q$ found (SNR$_Q$ = 8.7). However, there is a signal off the disk with comparable signal (SNR$_Q$ = 8.6). For IM Lup, the mean SNR$_Q$ for each pixel is 5.0 with a standard deviation of 1.0, and the signal shown in Figure [13](#fig:imlup_spectra_detected) (SNR$_Q$ = 9.6) is not the pixel with the highest SNR$_Q$. Instead, a few pixels off of the disk have slightly higher values of SNR$_Q$, with values up to 10.1. We note that the distribution of the maximum SNR$_Q$ for all pixels is not Gaussian, but rather positively skewed. Figure [16](#fig:SNRQ) shows that there exists high SNRs well outside of both disks.

Based on these results, we consider these Stokes $Q$ detections as marginal. While the signals in Figures [12](#fig:hd142527_spectra_detected) and [13](#fig:imlup_spectra_detected) appear to be robust by eye, and we have characterized the noise as well-behaved (Section [2.3](#sec:characterization)), our Monte Carlo simulations show that our methodology of finding this signal can find signals that are almost certainly false as well. If we repeat the same Monte Carlo simulations toward these disks for Stokes $U$, the highest values of SNR$_U$ within the areas of the gaseous disks are 6.9 and 8.0 for HD 142527 and IM Lup respectively. Since CO(2–1) Stokes $U$ maps share the same noise characteristics as Stokes $Q$ (Section [2.3](#sec:characterization)), these lower values indicate that the marginal detections of Stokes $Q$ could indeed be real. **Nevertheless, finding a marginal signal for each disk only for CO(2–1) Stokes $Q$ is peculiar and may indicate a more complex noise behavior that could not be found with our tests.**

As seen in Figures [12](#fig:hd142527_spectra_detected) and [13](#fig:imlup_spectra_detected), for both HD 142527 and IM Lup, there is also a negative dip in the Stokes $Q$ spectra at a velocity $\sim$1 km s$^{-1}$ higher than the pink shaded area. If we again search the nearby vicinity for the maximum SNR$_Q$ for different apertures at these negative dips, we find the maximum SNR$_Q$ for HD 142527 and IM Lup are 5.8 and 8.2 respectively. Based on our Monte Carlo simulations, these are marginal at best. However, the fact that the Stokes $Q$ spectra for both of these disks show a negative dip at the same relative velocity is intriguing, and perhaps indicates a flip in polarization angle at the higher velocity. Nevertheless, given these data, we cannot strongly support this conjecture.

While we detect positive Stokes $Q$ toward parts of the disk, which is suggestive of mostly north-south polarization, we do not detect polarized emission over a large enough area or velocity range to accurately discern any sort of disk polarization morphology. Moreover, trying to infer the magnetic field morphology from these observations is too difficult, given the ambiguity of the GK effect (polarization can be parallel or perpendicular to the magnetic field) and possible effects from resonant scattering (cite: Houde2013).

# Constraining the Polarization Percentage of the Observations

![](hd142527_upperlimits_cov.pdf)

![](imlup_upperlimits_cov.pdf)

Although our manual inspection method detected what seems to be a marginal signal in CO(2–1) for HD 142527 and IM Lup, the polarization is only detected for Stokes $Q$ and is only for select areas and velocities. To motivate future observations, it would make sense to put upper limits on the polarization percentage for each spectral line. Unlike continuum polarization, specifying the upper limit for $P_{\text{frac}}$ for disks is not straightforward, as it requires specifying both the integrated velocity range and location. The dominant Stokes $I$ emission of an inclined, rotating disk as a function of velocity will (1) start on the blue-shifted side of the major axis, (2) continue toward the minor axis, and (3) finish on the red-shifted side of the major axis. Thus, integrating emission over the entire disk makes less sense than integrating over finer velocity ranges since the entire range would add noise where little to no Stokes $I$ emission is detected.

For each spectral line, we make maps of the 3$\sigma$ upper limit for $P_{\text{frac}}$ by calculating these upper limits for each pixel for a variety of velocity intervals. We first mask out pixels where the moment 0 maps (Figures [5](#fig:hd142527_mom0) and [6](#fig:imlup_mom0)) are detected with a signal-to-noise of less than 10. This effectively masks out areas with high $P_{\text{frac}}$ upper limits, which aids in displaying the upper limit maps with a reasonable stretch. Then for the Stokes $I$ spectra of each remaining pixel, we find where the summation of $N$ channels is maximum ($\Sigma I$) Taking into account the correlation between channels, we determine the 3$\sigma$ upper limit to $P_{\text{frac}}$ to be

$$\begin{equation}
\label{eq:upper}

P_{\text{frac},3\sigma} = 3\sigma_{\text{PI}} \frac{\sqrt{1.6N - 0.6}}{\Sigma I} ,
\end{equation}$$

where the polarized intensity sensitivity $\sigma_{\text{PI}}$ = $\sigma_Q$ = $\sigma_U$. Since we choose the maximum $\Sigma I$ at each pixel, this method is effectively the “minimum" upper limit at each pixel for the given spatial resolution. Note that minimum upper limits could be reduced further if we did spatial smoothing.

We generate multiple 3$\sigma$ upper limit maps, each for $N$ channels spanning velocity intervals that are a factor of 0.5 km s$^{-1}$. We show the result for 0.5, 1, and 1.5 km s$^{-1}$ for HD 142527 and IM Lup in Figures [17](#fig:hd142527_upper) and [18](#fig:imlup_upper), respectively. Any higher velocity intervals (e.g., 2, 2.5, and 3 km s$^{-1}$) largely result in much worse upper limit sensitivities across the map. In general, the 0.5 km s$^{-1}$ interval performs better (i.e., lower upper limits) toward the outer part of the disk while the 1 and 1.5 km s$^{-1}$ intervals perform better for the inner part of the disk.

The upper limits vary drastically across the map for each disk, spectral line, and velocity bin. For the brightest continuum spots of HD 142527, the polarization 3$\sigma$ upper limits are typically less than 3% for CO(2–1) and $^{13}$CO(2–1), and 4% for C$^{18}$O(2–1). For the brightest continuum spots of IM Lup, the polarization 3$\sigma$ upper limits are typically less than 3% for CO(2–1), 4% for $^{13}$CO(2–1), and 12% for C$^{18}$O(2–1). While these are typical values, one can see from these Figures that toward some areas of the disks, the 3$\sigma$ upper limit can be over a factor of two lower.

+:---------------+:-----------:+:-----------:+:-----------:+:-----------:+
|                | HD 142527                 | IM Lup                    |
+----------------+-------------+-------------+-------------+-------------+
| Line           | Whole Disk  | Quadrants   | Whole Disk  | Quadrants   |
+----------------+-------------+-------------+-------------+-------------+
| CO(2–1)        | 0.2% – 0.3% | 0.3% – 0.9% | 0.2% – 0.3% | 0.3% – 0.5% |
+----------------+-------------+-------------+-------------+-------------+
| $^{13}$CO(2–1) | 0.3% – 0.4% | 0.4% – 0.9% | 0.3% – 0.5% | 0.6% – 1.0% |
+----------------+-------------+-------------+-------------+-------------+
| C$^{18}$O(2–1) | 0.4% – 0.5% | 0.5% – 1.1% | 1.1% – 1.4% | 1.9% – 3.3% |
+----------------+-------------+-------------+-------------+-------------+

: `GoFish` $P_{\text{frac}}$ 3$\sigma$ Upper Limits

Table notes: Stacking constraints using `GoFish` (Section [4.2](#sec:gofish)). Minimum and maximum 3$\sigma$ upper limits for windows of 0.5 km s$^{-1}$, 1.0 km s$^{-1}$, and 1.5 km s$^{-1}$ for the whole disk, and for repeating the analysis for different disk quadrants. The radii range used for the stacking is discussed in Section [4.2](#sec:gofish).

We can also constrain the upper limit to the $P_{\text{frac}}$ for the `GoFish` stacking methods presented in Section [4.2](#sec:gofish). We once again use Equation [\[eq:upper\]](#eq:upper) to calculate the “minimum" 3$\sigma$ upper limit for each stacked `GoFish` spectra for both the entire disk (Figures [9](#fig:hd142527_gofish_all) and [10](#fig:imlup_gofish_all) for CO(2–1); see Appendix for $^{13}$CO(2–1) and C$^{18}$O(2–1) transitions) and when stacking different disk quadrants (Figure [11](#fig:gofish_everything) for CO(2–1); also see Appendix for $^{13}$CO(2–1) and C$^{18}$O(2–1) transitions). We only report values for velocity intervals of 0.5, 1, and 1.5 km s$^{-1}$ because higher velocity spans do not result in better sensitivities. We take $\sigma_{\text{PI}}$ to be the noise of the Stokes $V$ stacked spectrum. The 3$\sigma$ upper limits are given as ranges in Table [\[tab:gofish\]](#tab:gofish). Ranges are given since the 3$\sigma$ upper limits vary significantly depending on the velocity interval and (for the quadrant analysis) the quadrant analyzed. We report the minimum and maximum 3$\sigma$ upper limit found for every permutation of velocity interval and quadrant. Compared to the pixel by pixel analysis, the stacking method performs better, having lower 3$\sigma$ upper limits by a factor of up to $\sim$10.

For each line and source, we executed one thousand Monte Carlo runs to test how the Table [\[tab:gofish\]](#tab:gofish) upper limits change with input parameters. In these runs, we randomly add Gaussian noise to the mass, inclination, and position angles because the Keplerian profile strongly depends on these parameters. For the mass, we assume that $\sigma$ of the Gaussian noise is 15% of the estimated masses of the disks. For the inclination and position angle, we assume that $\sigma$ of the Gaussian noise is 5$^\circ$. These runs showed that each value in Table [\[tab:gofish\]](#tab:gofish) is typical, as both the medians and means of these values over the one thousand runs were almost identical to their values. For each value in Table [\[tab:gofish\]](#tab:gofish), the typical standard deviation for the 1000 runs is $<$10% of its value.

Altering the radii range used for stacking slightly affects the upper limit values in Table [\[tab:gofish\]](#tab:gofish). For example, adding or subtracting an arcsecond to $r_{\text{max}}$ affects the upper limits by zero to three tenths of a percent.

# Summary and Discussion

We use ALMA to observe polarization toward HD 142527 and IM Lup in the 1.3 mm continuum and for the spectral lines CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1) at $\sim$0.5$\ensuremath{''}$ (80 au) resolution. We find the following results:

1.  While the 1.3 mm continuum images for HD 142527 and IM Lup show many similar features to the 870 $\mu$m images published in other studies, there are significant differences. The polarization toward the northern dust trap in HD 142527 shows a rapid change in the morphology and $P_{\text{frac}}$ with wavelength. Whether this wavelength dependence is consistent with the scattering interpretation previously proposed for the Band 7 polarization remains to be determined. The polarization toward the southern part of HD 142527 has typically been attributed to grain alignment, but $P_{\text{frac}}$ is surprisingly smaller at 1.3 mm than it is at 870 $\mu$m. The polarization morphology toward IM Lup appears more azimuthal at 1.3 mm than 870 $\mu$m. $P_{\text{frac}}$ decreases between 1.3 mm and 870 $\mu$m, which is the opposite of HL Tau. This could possibly be explained by optical depth effects or grains that are 100s of $\mu$m in size.

2.  For both disks, CO(2–1) is very optically thick ($\tau$ typically $>$30), while $^{13}$CO(2–1) is only moderately so ($\tau \sim 1$ to a few). C$^{18}$O(2–1) is typically optically thin, but still has significant optical depth ($\tau$ $\sim$ 0.1 – 1). Based on optical depth alone, we expect $^{13}$CO(2–1) and C$^{18}$O(2–1) to be optimal for probing the GK effect in these disks, while CO(2–1) is expected to be suboptimal. However, the lines are thermalized in the midplane, suggesting the detected line polarization would come from regions above the midplane.

3.  Despite the above expectations for optical depth, polarization is only detected for CO(2–1), and only for small parts of the disk. Such a detection requires spatial averaging and integrating over a velocity range. **The polarization signal for both disks is found for Stokes $Q$ only, and our Monte Carlo simulations suggest these are marginal detections.** $P_{\text{frac}}$ for HD 142527 and IM Lup are 1.56 $\pm$ 0.18% and 1.01 $\pm$ 0.10%, respectively. The polarization is detected for only small parts of the disks over a limited velocity range, and thus is insufficient for estimating a polarization or magnetic field pattern.

4.  We constrain the 3$\sigma$ upper limit for $P_{\text{frac}}$ at the resolution of the observations ($\sim$0.5$''$ or $\sim$80 au). Toward the brightest parts of HD 142527, the 3$\sigma$ upper limit is typically less than 3% for CO(2–1) and $^{13}$CO(2–1) and 4% for C$^{18}$O(2–1). Toward the brightest parts of IM Lup  the 3$\sigma$ upper limits are typically less than 3%, 4%, and 12%, respectively. Stacking based on Keplerian rotation has 3$\sigma$ upper limits that are up to a factor of $\sim$10 lower, but we note that the stacking method can potentially average out small-scale polarization structure.

So far, (cite: Lankhaar2020) has the only model that predicts line polarization for a disk. This paper primarily introduces PORTAL, which is a code for three-dimensional polarized line radiative transfer modeling. Their prescription for a disk is somewhat limited and it is only for CO(3–2), and they defer detailed analysis to a future paper. They showed predicted polarization morphologies for both a face-on disk and a 45$^\circ$ inclined disk, making them fairly analogous with HD 142527 and IM Lup, respectively. For the face-on disk, for both toroidal and radial fields, the polarization toward the center is expected to be near 0%, while toward the edges, it reaches values of $\sim$0.5%. For the 45$^\circ$ inclined disk, both toroidal and radial fields, polarization is near 0% for most of the disks. For the toroidal field, there are few locations along the major and minor axes where polarization can reach up to 0.5%. For radial fields, the polarization can even reach up to 9%, but the polarization is only significant for the central $\sim$40 au (i.e., about half our beam size) and only along the minor axis of the disk. Beaming smearing would reduce these levels considerably. (cite: Lankhaar2020) already predicts low polarization levels for CO(3–2), but they do not show detailed predictions for the $J = 2 \rightarrow 1$ CO isotopologues. Future modeling of line polarization tailored for disks may show why these two disks have low levels of polarization for emission for these CO isotopologue transitions.

These observations are the first published attempt to resolve linear line polarization for circumstellar disks. Polarization is undoubtedly low. Other transitions of CO isotopologues should be observationally explored. The polarization fraction largely depends on the optical depth and radiative rates, so observations of both higher and lower frequency CO isotopologue transitions should be attempted to search for a polarized morphology. Nevertheless, because the lines are thermalized in the midplane, any detection of CO polarization either comes from beyond the midplane or is from some other (possibly unknown) effect. Other molecules could also be observationally attempted, though most molecules are much less abundant, and it has been predicted that $P_{\text{frac}}$ decreases with the mass for a linear molecule (cite: Deguchi1984).

# Acknowledgments

We acknowledge an anonymous referee for giving useful comments on the paper. We thank Philip Myers, Patricio Sanhueza, and Haifeng Yang for a useful discussions, and Haifeng Yang for code that helped to generate some figures. ZYL acknowledges support from NASA 80NSSC18K1095 and 80NSSC20K0533 and NSF AST-1716259 and AST-1815784. LWL acknowledges support from NSF AST-1910364. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00425.S, #2016.1.00712.S, and #2018.1.01172.S, ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

NSF’s Atacama Large Millimiter/submillimeter Array (ALMA)

# Software

APLpy (cite: Robitaille2012), CASA v5.6.0, (cite: McMullin2007), GoFish (cite: GoFish), PySpecKit (cite: Ginsburg2011)

natexlab

(ref: Alcala2017) Alcalá, J. M., Manara, C. F., Natta, A., et al. 2017, A&A, 600, A20

(ref: Alves2018) Alves, F. O., Girart, J. M., Padovani, M., et al. 2018, A&A, 616, A56

(ref: Andersson2015) Andersson, B.-G., Lazarian, A., & Vaillancourt, J. E. 2015, ARA&A, 53, 501

(ref: Andrews2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: Arun2019) Arun, R., Mathew, B., Manoj, P., et al. 2019, AJ, 157, 159

(ref: Avenhaus2014) Avenhaus, H., Quanz, S. P., Schmid, H. M., et al. 2014, ApJ, 781, 87

(ref: Bacciotti2018) Bacciotti, F., Girart, J. M., Padovani, M., et al. 2018, ApJL, 865, L12

(ref: Balbus1998) Balbus, S. A., & Hawley, J. F. 1998, Reviews of Modern Physics, 70, 1

(ref: Beuther2010) Beuther, H., Vlemmings, W. H. T., Rao, R., & van der Tak, F. F. S. 2010, ApJL, 724, L113

(ref: Biller2012) Biller, B., Lacour, S., Juhász, A., et al. 2012, ApJL, 753, L38

(ref: Canovas2013) Canovas, H., Ménard, F., Hales, A., et al. 2013, A&A, 556, A123

(ref: Carrasco2016) Carrasco-González, C., Henning, T., Chandler, C. J., et al. 2016, ApJL, 821, L16

(ref: Carrasco2019) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71

(ref: Casassus2012) Casassus, S., Perez M., S., Jordán, A., et al. 2012, ApJL, 754, L31

(ref: Chamma2018) Chamma, M. A., Houde, M., Girart, J. M., & Rao, R. 2018, MNRAS, 480, 3123

(ref: Ching2016) Ching, T.-C., Lai, S.-P., Zhang, Q., et al. 2016, ApJ, 819, 159

(ref: Christiaens2014) Christiaens, V., Casassus, S., Perez, S., van der Plas, G., & Ménard, F. 2014, ApJL, 785, L12

(ref: Cleeves2016) Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2016, ApJ, 832, 110

(ref: Close2014) Close, L. M., Follette, K. B., Males, J. R., et al. 2014, ApJL, 781, L30

(ref: CortesCrutcher2006) Cortes, P., & Crutcher, R. M. 2006, ApJ, 639, 965

(ref: Cortes2006) Cortes, P. C., Crutcher, R. M., & Matthews, B. C. 2006, ApJ, 650, 246

(ref: Cortes2008) Cortes, P. C., Crutcher, R. M., Shepherd, D. S., & Bronfman, L. 2008, ApJ, 676, 464

(ref: Cortes2005) Cortes, P. C., Crutcher, R. M., & Watson, W. D. 2005, ApJ, 628, 780

(ref: CrutcherKemball2019) Crutcher, R. M., & Kemball, A. J. 2019, Frontiers in Astronomy and Space Sciences, 6, 66

(ref: Deguchi1984) Deguchi, S., & Watson, W. D. 1984, ApJ, 285, 126

(ref: Dent2019) Dent, W. R. F., Pinte, C., Cortes, P. C., et al. 2019, MNRAS, 482, L29

(ref: Donati2005) Donati, J.-F., Paletou, F., Bouvier, J., & Ferreira, J. 2005, Nature, 438, 466

(ref: FL2016) Fernández-López, M., Stephens, I. W., Girart, J. M., et al. 2016, ApJ, 832, 200

(ref: Forbrich2008) Forbrich, J., Wiesemeyer, H., Thum, C., Belloche, A., & Menten, K. M. 2008, A&A, 492, 757

(ref: Gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: Ginsburg2011) Ginsburg, A., & Mirocha, J. 2011, PySpecKit: Python Spectroscopic Toolkit, Astrophysics Source Code Library, , , ascl:1109.001

(ref: Girart1999) Girart, J. M., Crutcher, R. M., & Rao, R. 1999, ApJL, 525, L109

(ref: Girart2012) Girart, J. M., Patel, N., Vlemmings, W. H. T., & Rao, R. 2012, ApJL, 751, L20

(ref: Glenn1997a) Glenn, J., Walker, C. K., Bieging, J. H., & Jewell, P. R. 1997a, ApJL, 487, L89

(ref: Glenn1997b) Glenn, J., Walker, C. K., & Jewell, P. R. 1997b, ApJ, 479, 325

(ref: Goldreich1981) Goldreich, P., & Kylafis, N. D. 1981, ApJL, 243, L75

(ref: Greaves1999) Greaves, J. S., Holland, W. S., Friberg, P., & Dent, W. R. F. 1999, ApJL, 512, L139

(ref: Greaves2001) Greaves, J. S., Holland, W. S., & Ward-Thompson, D. 2001, ApJL, 546, L53

(ref: Harrison2019) Harrison, R. E., Looney, L. W., Stephens, I. W., et al. 2019, ApJL, 877, L2

(ref: Hezareh2013) Hezareh, T., Wiesemeyer, H., Houde, M., Gusdorf, A., & Siringo, G. 2013, A&A, 558, A45

(ref: Hirota2020) Hirota, T., Plambeck, R. L., Wright, M. C. H., et al. 2020, arXiv e-prints, arXiv:2005.13077

(ref: Houde2013) Houde, M., Hezareh, T., Jones, S., & Rajabi, F. 2013, ApJ, 764, 24

(ref: Huang2020) Huang, K. Y., Kemball, A. J., Vlemmings, W. H. T., et al. 2020, arXiv e-prints, arXiv:2007.00215

(ref: Hull2015) Hull, C. L. H., & Plambeck, R. L. 2015, Journal of Astronomical Instrumentation, 4, 1550005

(ref: Hull2018) Hull, C. L. H., Yang, H., Li, Z.-Y., et al. 2018, ApJ, 860, 82

(ref: Kataoka2017) Kataoka, A., Tsukagoshi, T., Pohl, A., et al. 2017, ApJL, 844, L5

(ref: Kataoka2015) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78

(ref: Kataoka2016b) Kataoka, A., Tsukagoshi, T., Momose, M., et al. 2016, ApJL, 831, L12

(ref: Kirchschlager2020) Kirchschlager, F., & Bertrang, G. H. M. 2020, arXiv e-prints, arXiv:2004.13742

(ref: Konigl2000) Konigl, A., & Pudritz, R. E. 2000, Protostars and Planets IV, 759

(ref: Lacour2016) Lacour, S., Biller, B., Cheetham, A., et al. 2016, A&A, 590, A90

(ref: Lai2003) Lai, S.-P., Girart, J. M., & Crutcher, R. M. 2003, ApJ, 598, 392

(ref: Lankhaar2020) Lankhaar, B., & Vlemmings, W. 2020, A&A, 636, A14

(ref: LazarianHoang2007) Lazarian, A., & Hoang, T. 2007, MNRAS, 378, 910

(ref: LeeCF2018b) Lee, C.-F., Hwang, H.-C., Ching, T.-C., et al. 2018, Nature Communications, 9, 4636

(ref: LeeCF2014) Lee, C.-F., Rao, R., Ching, T.-C., et al. 2014, ApJL, 797, L9

(ref: LiHenning2011) Li, H.-B., & Henning, T. 2011, Nature, 479, 499

(ref: Lin2020b) Lin, Z.-Y. D., Li, Z.-Y., Yang, H., et al. 2020, MNRAS, 496, 169

(ref: Loomis2018) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018, AJ, 155, 182

(ref: Lyo2011) Lyo, A. R., Ohashi, N., Qi, C., Wilner, D. J., & Su, Y.-N. 2011, AJ, 142, 151

(ref: Malfait1998) Malfait, K., Bogaert, E., & Waelkens, C. 1998, A&A, 331, 211

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Ohashi2018) Ohashi, S., Kataoka, A., Nagai, H., et al. 2018, ApJ, 864, 81

(ref: PerezS2015) Perez, S., Casassus, S., Ménard, F., et al. 2015, ApJ, 798, 85

(ref: Rameau2012) Rameau, J., Chauvin, G., Lagrange, A. M., et al. 2012, A&A, 546, A24

(ref: Robitaille2012) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library, , , ascl:1208.017

(ref: Sabin2019) Sabin, L., Zhang, Q., Vázquez, R., & Steffen, W. 2019, MNRAS, 484, 2966

(ref: Sadavoy2019) Sadavoy, S. I., Stephens, I. W., Myers, P. C., et al. 2019, ApJS, 245, 2

(ref: Shinnaga2017) Shinnaga, H., Claussen, M. J., Yamamoto, S., & Shimojo, M. 2017, PASJ, 69, L10

(ref: Stephens2014b) Stephens, I. W., Looney, L. W., Kwon, W., et al. 2014, Nature, 514, 597

(ref: Stephens2017c) Stephens, I. W., Yang, H., Li, Z.-Y., et al. 2017, ApJ, 851, 55

(ref: Tazaki2017) Tazaki, R., Lazarian, A., & Nomura, H. 2017, ApJ, 839, 56

(ref: GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632

(ref: vandenAncker1998) van den Ancker, M. E., de Winter, D., & Tjin A Djie, H. R. E. 1998, A&A, 330, 145

(ref: Vlemmings2012) Vlemmings, W. H. T., Ramstedt, S., Rao, R., & Maercker, M. 2012, A&A, 540, L3

(ref: Vlemmings2017) Vlemmings, W. H. T., Khouri, T., Martı́-Vidal, I., et al. 2017, A&A, 603, A92

(ref: Vlemmings2019) Vlemmings, W. H. T., Lankhaar, B., Cazzoletti, P., et al. 2019, A&A, 624, L7

(ref: Yang2016a) Yang, H., Li, Z.-Y., Looney, L., & Stephens, I. 2016, MNRAS, 456, 2794

(ref: Yang2017) Yang, H., Li, Z.-Y., Looney, L. W., Girart, J. M., & Stephens, I. W. 2017, MNRAS, 472, 373

(ref: Yang2019) Yang, H., Li, Z.-Y., Stephens, I. W., Kataoka, A., & Looney, L. 2019, MNRAS, 483, 2371

In this appendix, we show $^{13}$CO(2–1) and C$^{18}$O(2–1) images made using the `GoFish` stacking techniques used in Section [4.2](#sec:gofish). Constraints on the $P_{\text{frac}}$ based on these stacking techniques are given in Section [5](#sec:constrain). Figures [19](#fig:hd142527_gofish_all_ttco) and [20](#fig:hd142527_gofish_all_ceo) show the `GoFish` stacking technique across the entire disk for HD 142527 for $^{13}$CO(2–1) and C$^{18}$O(2–1), respectively. Figures [21](#fig:imlup_gofish_all_ttco) and [22](#fig:imlup_gofish_all_ceo) show the `GoFish` stacking technique across the entire disk for IM Lup for $^{13}$CO(2–1) and C$^{18}$O(2–1), respectively. Figures [23](#fig:gofish_everything_ttco) and [24](#fig:gofish_everything_ceo) show the `GoFish` stacking based on disk quadrants for $^{13}$CO(2–1) and C$^{18}$O(2–1), respectively, for both disks.

![](hd142527_line=13co21_all_rmax=3.pdf)

![](hd142527_line=c18o21_all_rmax=2.pdf)

![](imlup_line=13co21_all_rmax=3.pdf)

![](imlup_line=c18o21_all_rmax=3.pdf)

![image]({hd142527_line=13co21_Qpanels_rmin=0.17_rmax=3.arches}.pdf) ![image]({hd142527_line=13co21_Upanels_rmin=0.17_rmax=3.arches}.pdf) ![image]({imlup_line=13co21_Qpanels_rmin=0.5_rmax=3.arches}.pdf) ![image]({imlup_line=13co21_Upanels_rmin=0.5_rmax=3.arches}.pdf) ![image]({hd142527_line=13co21_panels_rmin=0.17_rmax=3}.pdf) ![image]({imlup_line=13co21_panels_rmin=0.5_rmax=3}.pdf)

![image]({hd142527_line=c18o21_Qpanels_rmin=0.17_rmax=2.arches}.pdf) ![image]({hd142527_line=c18o21_Upanels_rmin=0.17_rmax=2.arches}.pdf) ![image]({imlup_line=c18o21_Qpanels_rmin=0.5_rmax=3.arches}.pdf) ![image]({imlup_line=c18o21_Upanels_rmin=0.5_rmax=3.arches}.pdf) ![image]({hd142527_line=c18o21_panels_rmin=0.17_rmax=2}.pdf) ![image]({imlup_line=c18o21_panels_rmin=0.5_rmax=3}.pdf)

</paper>

Write the methods card for this paper.