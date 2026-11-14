# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...974L..25D\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...974L..25D",
 "title": "Asymmetric Dust Accumulation of the PDS 70 Disk Revealed by ALMA Band 3 Observations",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Doi, Kiyoaki",
 "n_authors": 8,
 "arxiv_id": "2408.09216",
 "doi": "10.3847/2041-8213/ad7f51",
 "alma_projects_linked_by_archive": [
  "2015.1.00888.S",
  "2018.A.00030.S",
  "2022.1.00893.S",
  "2022.1.01477.S"
 ]
}
```

Paper text:
<paper>
# Asymmetric dust accumulation of the PDS 70 disk revealed by ALMA Band 3 observations

## Abstract

The PDS 70 system, hosting two planets within its disk, is an ideal target for examining the effect of planets on dust accumulation, growth, and ongoing planet formation. Here, we present high-resolution ($0.07\ensuremath{''} = 8 \ \mathrm{au}$) dust continuum observations of the PDS 70 disk in ALMA Band 3 (3.0 mm). While previous Band 7 observations showed a dust ring with slight asymmetry, our Band 3 observations reveal a more prominent asymmetric peak in the northwest direction, where the intensity is 2.5 times higher than in other directions and the spectral index is at the local minimum with $\alpha_{\mathrm{SED}} \sim 2.2$. This indicates that a substantial amount of dust is accumulated both radially and azimuthally in the peak. We also detect point-source emission around the stellar position in the Band 3 image, which is likely to be free-free emission. We constrain the eccentricity of the outer ring to be $e<0.04$ from the position of the central star and the outer ring. From the comparison with numerical simulations, we constrain the mass of PDS 70c to be less than 4.9 Jupiter masses if the gas turbulence strength $\alpha_{\mathrm{turb}} = 10^{-3}$. Then, we discuss the formation mechanism of the disk structures and further planet formation scenarios in the disk.

UTF8ipxm

# Introduction

Recent high-resolution millimeter observations with ALMA have revealed substructures of dust emission in many disks, such as rings (cite: ALMA2015; Andrews2018) and non-axisymmetric structures (cite: vanderMarel2013; Casassus2013; Fukagawa2013), which may play an important role in dust growth and planet formation. Local dust trapping may halt the radial drift of dust grains (cite: Whipple1972). Furthermore, the local enhancement of dust density may promote the growth of dust grains by collisional sticking (cite: Brauer2008) or lead to the formation of planetesimals through streaming instability (cite: Youdin2005; Johansen2007) or gravitational instability (cite: Sekiya1983; Youdin2002). Despite the importance of these structures, their formation mechanism is still unclear.

One of the possible mechanisms for the formation of these structures is the influence of planets in the disk. Planets open gaps in the disk gas, and dust is trapped at the gas pressure maximum outside the planet, forming a dust ring (cite: Zhu2012; Pinilla2012a). If the gas gap is deep enough, vortices may form by the Rossby Wave Instability, and dust grains accumulate at the center of the vortex, leading to the formation of non-axisymmetric structures (cite: Lovelace1999; Ono2016). In addition, circumplanetary disks form around planets. These planets grow by mass accretion through the circumplanetary disks, and satellites are formed within these disks (cite: Ward2010; Tanigawa2012).

PDS 70 is an ideal target for examining the interaction between the disk and the planets. This object is a T Tauri star with an age of $5.4 \pm 1.0 \ \mathrm{Myr}$ (cite: Muller2018) at a distance of $112.39 \pm 0.24 \ \mathrm{pc}$ (cite: Gaia2023). Observations with the VLT/SPHERE and VLT/MUSE have discovered two accreting planets, PDS 70b and PDS 70c, at orbital radii of 22 and 34 au from the central star (cite: Keppler2018; Haffert2019; Hashimoto2020). ALMA Band 7 (0.87 mm) observations have detected continuum emission around PDS 70c and PDS 70b, possibly indicating circumplanetary disks (cite: Isella2019; Benisty2021; Casassus2022). Also, a wide dust ring at 74 au outside the planets’ orbit and a faint inner disk near the central star have been detected (cite: Keppler2019). The cavity has also been detected in infrared observations (cite: Hashimoto2012; Dong2012) and molecular line observations (cite: Keppler2019; Law2024; Rampinelli2024).

In this study, we characterize the dust distribution of PDS 70 using high-resolution ALMA Band 3 (3.0 mm) continuum observations. Previous high-resolution ALMA observations of PDS 70 have been limited to ALMA Band 7 (0.87 mm), which may be optically thick, making it difficult to characterize the disk dust properties. At these wavelengths, the disks are often optically thick (cite: Tripathi2017; Ansdell2018; Chung2024), and observations at longer wavelengths may reveal different structures from submillimeter observations (cite: Casassus2019; Liu2024). In this study, we present high-resolution observations at Band 3, which is likely more optically thin compared to Band 7, to reveal the detailed dust distribution of PDS 70 and characterize the dust properties.

The structure of this paper is as follows. First, in Section [2](#sec:PDS70_obs), we describe the observations and data analysis. In Section [3](#sec:PDS70_results), we present the observational images and the spectral index. In Section [4](#sec:PDS70_discussion), we discuss the central source, the circumplanetary disks, the mass of the planet in the disk, the dust mass in the ring, and the planet formation scenario. Finally, we summarize the results in Section [5](#sec:PDS70_summary).

# Observations

The ALMA Band 3 observations of PDS 70 were conducted in Cycle 10 as two projects, 2022.1.00893.S (PI: K. Doi) and 2022.1.01477.S (PI: H. Liu). The observations were performed in four configurations, C5, C6, C8 and C9, on March 26, May 4, July 2 and July 28, 2023, with on-source integration times of 2600, 756, 5334 and 3193 seconds, respectively. The maximum recoverable scale of the C5 observations is $9.83\ensuremath{''}$, which is sufficient to avoid missing flux. Four spectral windows were set at the central frequency of 90.5, 92.5, 102.5, and 104.5 GHz with a bandwidth of 1.875 GHz each to maximize the continuum sensitivity. The phase calibrator was J1407-4302, and the amplitude calibrator was J1427-4206 for all observations.

The pipeline calibration was performed with Common Astronomical Software Applications (CASA) version 6.4.1.12 and the subsequent reduction was performed with CASA modular version 6.6.3.22 (cite: CASA2022). We subtracted the line emission and then performed phase-only self-calibration for each EB on the line-subtracted data. The data were then combined and imaged using the `tclean` task. Imaging was performed with Multi-Frequency Synthesis (MFS) at a central frequency of 97.5 GHz, using `nterms = 2` and Briggs weighting with a robust parameter of 0.5. We did not apply self-calibration to the combined data because it did not improve SNR due to the insufficient peak SNR of 21. The resulting image has a beam size of $0.073\ensuremath{''} \times 0.066\ensuremath{''}$ with a position angle of $-64.2\ensuremath{^\circ}$, and the rms noise level measured in the emission free region is $4.94\ \mathrm{\mu Jy\ beam^{-1}}$.

The Band 7 data are those shown in the left panel of Fig. 1 in (cite: Benisty2021). These data were obtained by 2015.1.00888.S (PI: E. Akiyama) and 2018.A.00030.S (PI: M. Benisty). The data reduction is described in (cite: Benisty2021). We re-ran `tclean` on the calibrated data of (cite: Benisty2021) without applying the JvM correction (cite: JvM1995), which was applied in (cite: Benisty2021). The resulting image has a beam size of $0.046\ensuremath{''} \times 0.035\ensuremath{''}$ at a position angle of $-53.1\ensuremath{^\circ}$, and the rms noise level is $12.7\ \mathrm{\mu Jy\ beam^{-1}}$ at the central frequency of 350.6 GHz.

# Results

![](B3_B7_alpha.pdf)

The left and middle panels of Figure [1](#fig:PDS70_images) show the images of PDS 70 in Band 3 and Band 7, respectively. The Band 7 image shows three major structures: (1) a wide ring, (2) faint central emission, and (3) circumplanetary disks (cite: Keppler2019; Isella2019; Benisty2021; Casassus2022). In contrast, the Band 3 image shows a different morphology from that of Band 7. First, the ring exhibits more prominent asymmetric peak in the northwest direction (hereafter, the northwest peak). Second, the central emission shows a compact point-source emission, while it has a more extended structure in Band 7. Third, the circumplanetary disk is not detected in Band 3. We discuss the characteristics of these structures individually in Section [4](#sec:PDS70_discussion). To quantitatively estimate the distributions of these structures at each wavelength, we fit the ring and the central emission individually in Appendix [6](#app:ring_fit).

The right panel of Figure [1](#fig:PDS70_images) shows the spectral index between Band 7 and Band 3. The two images are aligned to match the center of the outer ring, which we derive by the fitting described in Appendix [6](#app:ring_fit). The Band 7 image is smoothed to match the resolution of the Band 3 beam. The rms noise level of the smoothed Band 7 image is $15.1 \ \mathrm{\mu Jy\ beam^{-1}}$. The spectral index is calculated as $$\begin{equation}
  \alpha_{\mathrm{SED}} = \frac{\log(I_{\nu_{\mathrm{B7}}}/I_{\nu_{\mathrm{B3}}})}{\log(\nu_{\mathrm{B7}}/\nu_{\mathrm{B3}})}.
\end{equation}$$ where $I_{\nu_{\mathrm{B7}}}$ and $I_{\nu_{\mathrm{B3}}}$ are the intensity at the frequency $\nu_{\mathrm{B7}}$ and $\nu_{\mathrm{B3}}$, respectively. The spectral index uncertainty between Band 7 and Band 3 resulting from absolute flux calibration uncertainties is $\Delta \alpha_{\mathrm{SED}} = 0.083$ when the absolute flux calibration error is 5% for Band 3 and 10% for Band 7 (ALMA Technical Handbook; (cite: ALMA_TH2023)). We note that flux calibration uncertainty affects the spectral index uniformly over the image but does not impact the difference in the spectral index between different regions. Therefore, unless otherwise noted, the spectral index uncertainty mentioned below only considers the uncertainty due to the rms noise, as we focus on the spatial variation of the spectral index.

The observed spectral index in the outer ring becomes a minimum at the northwest peak with $\alpha_{\mathrm{SED}} = 2.17 \pm 0.04$ with the rms error, and $\alpha_{\mathrm{SED}} = 2.17 \pm 0.09$ with flux calibration error. The spectral index of the central point source is $\alpha_{\mathrm{SED}} = 1.53 \pm 0.13$ with the rms error, and $\alpha_{\mathrm{SED}} = 1.53 \pm 0.15$ with flux calibration error.

# Discussion

We characterize the dust ring in Section [4.1](#sec:PDS70_ring), the central emission in Section [4.2](#sec:PDS70_central_source), and the circumplanetary disk in Section [4.3](#sec:PDS70_circumplanetary_disk). We estimate the planet mass from the eccentricity of the ring in Section [4.4](#sec:PDS70_planet_mass). Finally, we discuss the formation process of the disk structure and planets in the PDS 70 system in Section [4.5](#sec:PDS70_planet_formation).

## Ring

The ring shows a more prominent northwest peak in Band 3 than in Band 7. The spectral index takes a minimum value of $\alpha_{\mathrm{SED}} = 2.17 \pm 0.09$ at the northwest peak. Since the spectral index approaches $\alpha_{\mathrm{SED}} \sim 2$ when the dust is optically thick, the observed low spectral index at the northwest peak suggests that the dust emission is optically thick, at least marginally.

![](azimuthal_intensity.pdf)

We show the azimuthal intensity profile along the ring in Band 7 and Band 3 in Figure [2](#fig:PDS70_azimuthal) to examine the azimuthal intensity variation. To avoid the effect of the elliptical beam shape on the azimuthal variation of the intensity (cite: Doi2021), we further smoothed both images so that the beam became a circular Gaussian after deprojection with a beam size of $0.12\ensuremath{''}$. The rms noise level after the smoothing is $19.0 \ \mathrm{\mu Jy\ beam^{-1}}$ in Band 7 and $5.27 \ \mathrm{\mu Jy\ beam^{-1}}$ in Band 3. The azimuthal variation of the intensity shows a significant difference between the two bands. In Band 7, the intensity at the northwest peak is 1.3 times larger than in other directions, while it is 2.5 times larger in Band 3. The smaller azimuthal contrast in Band 7 than in Band 3 implies that the dust is optically thick in all directions in Band 7, and the intensity is saturated with respect to the surface density. On the other hand, the prominent azimuthal variation in Band 3 implies that the dust is optically thin in directions other than the northwest peak. Thus, the Band 3 observations reveal that the dust is accumulated in the azimuthal direction at the northwest peak.

The Band 3 image tentatively shows a double peak structure at the northwest peak, but the intensity dip between the peaks is less than $3 \sigma$, making it difficult to conclusively characterize this feature. This feature may suggest dust circulation around a vortex (cite: Hammer2021) or the azimuthal accumulation of dust grains of different sizes (cite: Baruteau2016).

![](spectral_index_1x2.pdf)

The upper panel of Figure [3](#fig:PDS70_radial) shows the azimuthally averaged radial profile of the intensity, and the lower panel shows the radial profile of the spectral index. To compare the profiles between the two bands, we smoothed the Band 7 image to have the same beam as Band 3 as in Section [3](#sec:PDS70_results). The orange dashed line in the upper panel is the Band 3 profile scaled to match the peak intensity of Band 7 for comparison of the radial morphology. The radial profile is averaged over all azimuthal angles, including the northwest peak. The radial profiles in the peak direction and the direction excluding the peak are shown in Appendix [7](#app:radial_profile). The error range is calculated as the rms noise level divided by the square root of the number of independent data points. Here, the number of independent data points is defined as the circumference divided by the geometric mean of the major and minor axes of the beam.

The upper panel shows that the dust ring width is narrower in Band 3 than in Band 7. The fitting results in Appendix [6](#app:ring_fit) confirm that the ring width is narrower in Band 3 than in Band 7, with $w = 8.45_{-0.21}^{+0.22}$ au in Band 3 and $w = 11.23_{-0.03}^{+0.03}$ au in Band 7. The lower panel shows that the spectral index has a minimum value of $\alpha_{\mathrm{SED}} = 2.69 \pm 0.01$ near the radial peak of the ring and increases toward the edge of the ring. One explanation is that larger dust grains, which are more sensitive to long-wavelength observations, are more efficiently accumulated at the center of the ring, making the ring appear narrower at longer wavelengths. The other explanation is that the peak intensity saturates due to the higher optical depth in Band 7 than in Band 3.

The shape of the ring is not symmetric between the inner and outer sides, and a structure called a shoulder is seen around $r \sim 0.5\ensuremath{''}$ in both wavelengths (cite: Keppler2019). Comparing the orange dashed line (scaled Band 3) and the blue line (Band 7) in Figure [3](#fig:PDS70_radial), the intensity at the inner shoulder relative to the peak intensity is weaker in Band 3 than in Band 7. Comparing the spectral index at $r = 0.511\ensuremath{''}$ and $r = 0.770\ensuremath{''}$, where the intensity is half of the peak intensity in Band 7, the spectral index is $\alpha_{\mathrm{SED}} = 3.12 \pm 0.05$ at the inner side and $\alpha_{\mathrm{SED}} = 2.81 \pm 0.03$ at the outer side. This suggests that the dust size is smaller at the inner shoulder than the outer side. (cite: Bi2024) show that the 3D gas flow induced by a planet forms a shoulder with small dust grains, but they predict the shoulder to be on the outer side, contrary to our observations. The inner shoulder structure can be explained if the dust grains leak inward from a loosely confined dust ring (cite: Jiang2021). Additionally, (cite: Pinilla2024) show that the shoulder may form if small dust grains leak from the ring over the gas gap.

We estimate the lower limit of dust mass in the ring from the Band 3 emission to discuss the possibility of further planet formation. We assumed a temperature of 16 K for the disk ring, based on the temperature model of (cite: Law2024). This is considered an upper limit model for the temperature, as it is derived from the upper layer of the gas, and the midplane temperature may be lower. We assumed the upper limit of the Band 3 dust opacity to be $\kappa_{\mathrm{abs}} = 0.47\ \mathrm{cm^2/g}$. Here, we used the DSHARP dust model for the dust opacity (cite: Birnstiel2018), assuming a power-law size distribution of $q= 3.5$ (cite: Mathis1977; Doi2023) from $0.1 \ \mathrm{\mu m}$ grains to $3.4 \ \mathrm{mm}$ grains, in which the maximum dust size was chosen to maximize the opacity for conservative mass estimates. We estimated the lower limit of the dust mass to be 28 $M_{\mathrm{Earth}}$ in the entire ring and 9.3 $M_{\mathrm{Earth}}$ even within the narrow range of $270^{\circ} < \phi < 360^{\circ}$ around the northwest peak. Thus, the dust mass in the ring is sufficient to form a gas giant core of 10 $M_{\mathrm{Earth}}$ even with conservative estimates (cite: Mizuno1980; Ikoma2000).

## Central Source

The central point source has a significantly different morphology depending on the wavelength. As mentioned in Section [3](#sec:PDS70_results), the spectral index of the central source has $\alpha_{\mathrm{SED}} < 2$, suggesting the contribution of the free-free emission (cite: Riviere-Marichalar2024; Rota2024). As shown in Figure [6](#fig:MCMC_B3_point), the size of the central point source in Band 3 has an upper limit below the beam size, indicating compact emission. On the other hand, the central emission in Band 7 is extended with a size of $\sim 8$ au in standard deviation as shown in Figure [7](#fig:MCMC_B7_point). Therefore, the compact central emission in Band 3 is dominated by free-free emission, while the extended emission in Band 7 suggests that it is dominated by dust thermal emission. The presence of such free-free emission implies that accretion onto the central star is occurring (cite: Pascucci2012) onto the weak line T-Tauri star (cite: Gregorio-Hetem2002) with the relatively old age of 5.4 $\pm$ 1.0 Myr, the clear gap in both dust and gas (cite: Law2024), and the disk wind (cite: Campbell-White2023).

The flux estimated from the peak intensity of the central source in Band 3 is 31.1 $\mu$Jy. (cite: Liu2024) analyzed multi-wavelength ALMA and JVLA data, and the spectral fit of the total flux showed that the emission from PDS 70 is dominated by dust emission at $> 30$ GHz and by Anomalous Microwave Emission (AME) due to spinning dust at $< 30$ GHz, and free-free emission is not dominant at any frequency. Although our study suggests that the central emission in Band 3 is dominated by free-free emission, it is much weaker than the total emission from the disk, which is consistent with the results of (cite: Liu2024).

## Circumplanetary Disk

The previous Band 7 observations have detected a circumplanetary disk around PDS 70 c, and tentatively detected it around PDS 70 b (cite: Isella2019; Benisty2021; Casassus2022). Since the growth of gas giants occurs through circumplanetary disks, and satellite formation also occurs through circumplanetary disks, it is important to characterize the circumplanetary disks from their spectrum.

Our Band 3 observations did not detect any point source emission around PDS 70 b or c. We put a lower limit on the spectral index of PDS 70 c as $\alpha_{\mathrm{SED}} > 1.5$, assuming the Band 7 intensity of PDS 70 c is $86 \pm 16$ $\mu$Jy (cite: Benisty2021) and the $3 \sigma$ upper limit in Band 3 is 15 $\mu$Jy. The non-detection of the circumplanetary disk in Band 3 observation is not surprising, since the spectral index of thermal dust emission is $\alpha_{\mathrm{SED}} > 2$.

## Eccentricity and Exoplanet Mass

The planetary mass is a key parameter in understanding planet formation and disk structure. The planet mass has been estimated from infrared observations, comparing the infrared photometry with planet evolution models. The mass of PDS 70 c $M_{p,c}$ has been estimated to be $4 M_{\mathrm{Jupiter}} < M_{p,c} < 12 M_{\mathrm{Jupiter}}$ by (cite: Haffert2019), $M_{p,c} < 5 M_{\mathrm{Jupiter}}$ by (cite: Mesa2019), $1 M_{\mathrm{Jupiter}} < M_{p,c} < 3 M_{\mathrm{Jupiter}}$ by (cite: Wang2020), and $M_{p,c} \sim 4 M_{\mathrm{Jupiter}}$ by (cite: Wahhaj2024). These estimates from infrared observations significantly depend on the assumptions of planet evolution models and the system age. (cite: Portilla-Revelo2023) estimated the planet mass to be $M_{p,c} \sim 4 M_{\mathrm{Jupiter}}$ by comparing the gas gap depth from ALMA CO isotopic observations and the numerical simulation by (cite: Duffell2015). Overall, the mass of PDS 70 c remains uncertain, and constraints from different perspectives are needed.

The disk eccentricity, derived from millimeter continuum emission, offers a new way to constrain the planet mass. More massive planets form deeper and wider gaps. In particular, when the gap created by the planet is very deep, the ring-gap structure becomes unstable and gives eccentricity to the outer ring (cite: Kley2006; Tanaka2022). (cite: Bae2019) simulated a disk mimicking the PDS 70 system with a viscosity of $\alpha_{\mathrm{turb}} = 10^{-3}$ and introduced planets corresponding to PDS 70 b and c. They showed that the ring becomes eccentric with the eccentricity $e = 0.2 - 0.4$ when the mass of PDS 70 c is 10 $M_{\mathrm{Jupiter}}$. (cite: Tanaka2022) investigated the eccentricity of the outer ring induced by a single planet and derived empirical criteria for the critical planet mass $M_{\mathrm{crit}}$ for the ring to be eccentric with $e \gtrsim 0.07$, depending on the aspect ratio $h/r$, the turbulent strength $\alpha_{\mathrm{turb}}$, and the central star mass $M_{\mathrm{star}}$. Using their equation (18)[^1], the critical planet mass to induce the eccentricity is $$\begin{equation}
  M_{\mathrm{crit}} =  4.9 M_{\mathrm{Jupiter}} \left( \frac{\alpha_{\mathrm{turb}}}{10^{-3}} \right)^{1/2}
\end{equation}$$ for the central star mass $M_{\mathrm{star}} = 0.85 M_{\odot}$ and the aspect ratio $h/r = 0.079$ (cite: Bae2019).

The Band 3 observations allow us to accurately estimate the eccentricity by detecting point-source free-free emission at the position of the central star, i.e., the focus, as well as the outer ring. We can estimate the eccentricity from the offset between the position of the central star and the center of the ring, $\delta r$, and the semi-major axis $r_0$ as $$\begin{equation}
  e = \frac{\delta r}{r_0}.
\end{equation}$$ As shown in Figure [8](#fig:MCMC_B3_center_shift) in Appendix [6](#app:ring_fit), the center of the point source and the outer ring are consistent, indicating that the ring is circular with the eccentricity $e < 0.04$. The offset between the center of the outer ring and the center of the central disk based on the Band 7 observations also shows that the centers are consistent, as shown in Figure [9](#fig:MCMC_B7_center_shift), and provides the eccentricity of $e < 0.02$. These low eccentricities put the mass of PDS 70 c below $4.9 M_{\mathrm{Jupiter}}$ for $\alpha_{\mathrm{turb}} = 10^{-3}$, which is proportional to the square root of the turbulent strength $\alpha_{\mathrm{turb}}$. Thus, we put a strong upper limit on the planet mass from the new perspective of the disk eccentricity. A caveat is that the simulation of (cite: Tanaka2022) is a 2D simulation assuming a single planet on a circular orbit, and the multiplicity or the eccentricity of the planets in PDS 70 or 3D effects may affect the eccentricity of the disk (cite: Wang2021; Li2023).

## Planet Formation Scenario

We discuss the formation scenario of the disk structure and possible further planet formation in the PDS 70 system. The presence of the planets and the disk morphologies are consistent with the following scenario of planet-induced dust accumulation and planet formation. First, the already-formed planets create the gap in the gas disk, trapping dust grains outside the gap (cite: Lau2024). The gas gap then induces vortices through the Rossby Wave Instability (cite: Lovelace1999; Ono2016), possibly aided by disk winds (cite: Wu2023). The pressure bump in the gas accumulates dust radially, and the vortex accumulates dust azimuthally, leading to the formation of an asymmetric ring structure, as observed in Band 3.

The accumulated dust grains by the planets promote further planet formation. As shown in the Band 3 image, the planets accumulate dust radially and azimuthally outside of the planets. Locally accumulated dust grains can lead to the formation of planetesimals through the streaming instability (cite: Youdin2005; Johansen2007) or the gravitational instability (cite: Sekiya1983; Sekiya1998; Youdin2002). Planetesimals grow into solid planets and can form gas giants through gas accretion, and the Band 3 observations show that there is enough dust to form a gas giant core in PDS 70. Thus, we suggest that inside-out planet formation may be occurring in PDS 70 (cite: Chatterjee2014; Tan2016). We note that these observations do not exclude other planet and structure formation scenarios (cite: Jiang2023).

# Summary

We performed high-resolution ALMA Band 3 (3 mm) observations of the PDS 70 system, a disk with planets. We characterized the dust properties and the planets within the disk from the morphology and the spectral index of the Band 3 and the previous Band 7 (0.87 mm) images. The main results are as follows:

1.  The dust ring has a clear northwest peak that is 2.5 times brighter than the rest of the azimuthal directions in Band 3, suggesting that dust accumulates not only radially but also azimuthally outside the planets.

2.  The lower limit of the dust mass is 28 $M_{\mathrm{Earth}}$ in the whole ring and 9.3 $M_{\mathrm{Earth}}$ in the northwest peak. This indicates that there is sufficient dust to form additional solid planets or a core of a gas giant.

3.  The central emission exhibits different morphologies: it is extended in Band 7, while it appears as a point source in Band 3. The low spectral index of $\alpha_{\mathrm{SED}} < 2$ suggests that the Band 3 emission is dominated by free-free emission, whereas the Band 7 emission is dominated by thermal dust emission.

4.  The circumplanetary disk found in Band 7 was not detected in Band 3. We put a lower limit of $\alpha_{\mathrm{SED}} > 1.5$.

5.  We estimated the eccentricity of the outer ring and found that the ring is circular. In comparison with numerical simulations, we constrained the mass of PDS 70 c to be less than $4.9 M_{\mathrm{Jupiter}}$, assuming the gas turbulence strength $\alpha_{\mathrm{turb}} = 10^{-3}$.

6.  The existence of the planets and the localized dust accumulation suggest that dust accumulates radially and azimuthally outside the planets, promoting inside-out planet formation.

# Acknowledgments

The authors thank the anonymous referee for the helpful comments and suggestions that significantly improved the manuscript. This paper makes use of the following ALMA data: ADS/JAO. ALMA#2015.1.00888.S, 2018.A.00030, 2022.1.00893.S, and 2022.1.01477.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/ NRAO, and NAOJ.

This work was supported by JSPS KAKENHI Grant Numbers JP22K03680, JP22KJ1435, JP23K03463, JP23KJ0636, and JP23KJ1008. H.B.L. is supported by the National Science and Technology Council (NSTC) of Taiwan (Grant Nos. 111-2112-M-110-022-MY3, 113-2112-M-110-022-MY3). MB received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188).

Facility: ALMA.

Software: *CASA* (cite: McMullin2007), *astropy* (cite: astropy2022), *emcee* (cite: Foreman-Mackey2013), *scipy* (cite: scipy2020),

# Image Fitting

We perform image fitting using `ring_fit` (cite: Doi2023) to examine the morphology of the continuum emission. Here, we fit the observed emission with two components, the ring and the central emission. We model the ring with a Gaussian ring given by $$\begin{equation}
 \label{eq:_PDS70_ring}
  I(r) = I_0 \exp\left(-\frac{(r-r_0)^2}{2w^2}\right),
\end{equation}$$ where $I_0$ is the peak intensity, $r_0$ is the distance of the ring, $w$ is the width of the ring. For the central source, we consider a Gaussian disk given by $$\begin{equation}
 \label{eq:_PDS70_point}
  I(r) = I_0 \exp\left(-\frac{r^2}{2w^2}\right),
\end{equation}$$ where $I_0$ is the peak intensity, $w$ is the width of the emission. In other words, equation ([\[eq:\_PDS70_point\]](#eq:_PDS70_point)) is the same as equation ([\[eq:\_PDS70_ring\]](#eq:_PDS70_ring)) with $r_0 = 0$. The caveat is that the emission of the object is not perfectly Gaussian, but the aim here is not to reproduce the emission shape perfectly but to quantitatively evaluate the position and the spatial distribution of the emission.

We created these model images, smoothed them with the beam, and minimized the residuals between models and observations using `emcee` (cite: Foreman-Mackey2013). The free parameters are the parameters of equations ([\[eq:\_PDS70_ring\]](#eq:_PDS70_ring)) or ([\[eq:\_PDS70_point\]](#eq:_PDS70_point)) and the center positions of these structures in the deprojected plane $(x_{\mathrm{cen}}, y_{\mathrm{cen}})$. We fixed the inclination $i = 51.7^{\circ}$ and the position angle PA = $160.4^{\circ}$ based on (cite: Keppler2019). We fitted the ring in the range of $35\ \mathrm{au} < r < 105\ \mathrm{au}$ and the central source in the range of $r < 15$ au. We performed fitting for the full azimuthal angle and also performed the fitting for the range of $0^{\circ} < \phi < 270^{\circ}$ excluding the northwest peak, since the non-axisymmetric nature of the northwest peak could affect the fitting. We perform MCMC fitting with 16 walkers and 20,000 steps, excluding the first 1,000 steps as burn-in. Figure [4](#fig:MCMC_B3_ring) and [5](#fig:MCMC_B7_ring) show the corner plots of the fitting results for the ring in Band 3 and Band 7, respectively, and Figure [6](#fig:MCMC_B3_point) and [7](#fig:MCMC_B7_point) show those for the central source in Band 3 and Band 7, respectively. The fitting results are summarized in Table [1](#tab:PDS70_fitted). The results excluding the northeast peak show a slight decrease in the peak intensity, but no significant difference in the center position. In the main discussion, we use the fitting results for full azimuthal angle, while the conclusions do not change depending on which results are used.

To determine the eccentricity of the ring, we calculated the difference of the center positions between the ring and the central source from the fitting results. We calculate the offset of the center positions as $$\begin{equation}
  \delta \{x, y\} = \{x, y\}_{\mathrm{cen,central}} - \{x, y\}_{\mathrm{cen,ring}},
\end{equation}$$ and show the corner plots of these differences in Figure [8](#fig:MCMC_B3_center_shift) and Figure [9](#fig:MCMC_B7_center_shift). These results show that the center of the ring and the central source is consistent, i.e., the ring is circular. Furthermore, we calculate the offset of the center positions between the ring and the central source as $\delta r = \sqrt{\delta x^2 + \delta y^2}$ and set the 84th percentile as the upper limit of the deviation of the ring center position. These results are summarized in Table [2](#tab:PDS70_fitting_center).

+:----:+:-------------------------:+:---------------------------:+:-----------------------:+:-----------------------:+:-----------------------:+:-----------------------:+
| Band | Component                 | $I_0$                       | $r_0$                   | $w$                     | $x_{\mathrm{cen}}$      | $y_{\mathrm{cen}}$      |
+------+---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|      |                           | \[mm\]                      | \[au\]                  | \[au\]                  | \[au\]                  | \[au\]                  |
+------+---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| B3   | ring                      | $1.26_{-0.02}^{+0.03}$      | $75.10_{-0.19}^{+0.19}$ | $8.45_{-0.21}^{+0.22}$  | $1.58_{-0.24}^{+0.27}$  | $-0.07_{-0.23}^{+0.25}$ |
|      +---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|      | $\mathrm{ring_{exclude}}$ | $1.03_{-0.03}^{+0.03}$      | $74.68_{-0.30}^{+0.30}$ | $9.50_{-0.30}^{+0.29}$  | $0.77_{-0.42}^{+0.41}$  | $-0.25_{-0.38}^{+0.39}$ |
|      +---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|      | center                    | $(58.23_{-47.24}^{+28.33})$ | \-                      | $<1.12$                 | $1.31_{-1.57}^{+1.50}$  | $0.60_{-1.18}^{+1.18}$  |
+------+---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| B7   | ring                      | $3.11_{-0.01}^{+0.01}$      | $73.12_{-0.03}^{+0.03}$ | $11.23_{-0.03}^{+0.03}$ | $-1.89_{-0.04}^{+0.04}$ | $2.32_{-0.03}^{+0.03}$  |
|      +---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|      | $\mathrm{ring_{exclude}}$ | $2.98_{-0.01}^{+0.01}$      | $73.45_{-0.04}^{+0.04}$ | $11.42_{-0.03}^{+0.03}$ | $-1.60_{-0.05}^{+0.05}$ | $2.80_{-0.05}^{+0.05}$  |
|      +---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|      | center                    | $0.65_{-0.07}^{+0.07}$      | \-                      | $7.03_{-0.54}^{+0.62}$  | $-1.93_{-0.66}^{+0.64}$ | $2.06_{-0.63}^{+0.65}$  |
+------+---------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+

: Fitted parameters for each component

Table notes: The results of the MCMC fitting. Since the width and intensity of the central point source in Band 3 are degenerate, we show the upper limit of the width, and the intensity has no useful constraints. $\mathrm{ring_{exclude}}$ is the fitting result of the ring excluding the range of $270-360^{\circ}$ where the northwest peak is located.

|      |                         |                         |            |
|:----:|:-----------------------:|:-----------------------:|:----------:|
| Band |       $\delta x$        |       $\delta y$        | $\delta r$ |
|      |         \[au\]          |         \[au\]          |   \[au\]   |
|  B3  | $-0.28_{-1.58}^{+1.54}$ | $0.66_{-1.20}^{+1.20}$  |  $< 2.88$  |
|  B7  | $-0.04_{-0.66}^{+0.64}$ | $-0.26_{-0.63}^{+0.65}$ |  $< 1.28$  |

: Offset of the center

Table notes: The offset of the center positions between the ring and the central source. This difference corresponds to the offset of the focus from the center, i.e., the eccentricity.

![](ring_corner_B3.pdf)

![](ring_corner_B7.pdf)

![](point_source_corner_B3.pdf)

![](point_source_corner_B7.pdf)

![](delta_center_corner_B3.pdf)

![](delta_center_corner_B7.pdf)

# Radial Profile

The radial profile shown in Figure [3](#fig:PDS70_radial) is the azimuthally averaged profile that includes emission from both the northwest peak and the other directions. Here, we show the radial profiles for the northwest peak direction and the rest directions separately. The left panel of Figure [10](#fig:radial_4panel) shows the radial profile in the northwest peak direction, PA = 309$^{\circ}$, and the right panel shows the azimuthally averaged profile in the directions other than the northwest peak, 0$^{\circ} < \mathrm{PA} < 270^{\circ}$. The upper panels show the radial profiles, and the lower panels show the spectral index profiles as in Figure [3](#fig:PDS70_radial).

The profile in the northwest peak direction has larger noise because it is not azimuthally averaged, but the peak intensity is higher in Band 3 than in the other directions. The intensity of the shoulder relative to the radial peak is smaller in Band 3 than in Band 7, but the noise in the shoulder region makes it difficult to quantitatively discuss the contrast between the peak and the shoulder. The spectral index shows a minimum at the center of the ring.

The radial profile in the directions other than the northwest peak also shows the ring and the inner shoulder, and the intensity of the shoulder relative to the radial peak is smaller in Band 3 than in Band 7. Thus, the discussion based on the radial profile in Section [4.1](#sec:PDS70_ring) is qualitatively valid for all azimuthal directions.

![](spectral_index_2x2.pdf)

natexlab

(ref: ALMA2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Ansdell2018) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21, doi: [`10.3847/1538-4357/aab890`](http://doi.org/10.3847/1538-4357/aab890)

(ref: astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bae2019) Bae, J., Zhu, Z., Baruteau, C., et al. 2019, ApJL, 884, L41, doi: [`10.3847/2041-8213/ab46b0`](http://doi.org/10.3847/2041-8213/ab46b0)

(ref: Baruteau2016) Baruteau, C., & Zhu, Z. 2016, MNRAS, 458, 3927, doi: [`10.1093/mnras/stv2527`](http://doi.org/10.1093/mnras/stv2527)

(ref: Benisty2021) Benisty, M., Bae, J., Facchini, S., et al. 2021, ApJL, 916, L2, doi: [`10.3847/2041-8213/ac0f83`](http://doi.org/10.3847/2041-8213/ac0f83)

(ref: Bi2024) Bi, J., & Lin, M.-K. 2024, arXiv e-prints, arXiv:2406.19438, doi: [`10.48550/arXiv.2406.19438`](http://doi.org/10.48550/arXiv.2406.19438)

(ref: Birnstiel2018) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45, doi: [`10.3847/2041-8213/aaf743`](http://doi.org/10.3847/2041-8213/aaf743)

(ref: Brauer2008) Brauer, F., Dullemond, C. P., & Henning, T. 2008, A&A, 480, 859, doi: [`10.1051/0004-6361:20077759`](http://doi.org/10.1051/0004-6361:20077759)

(ref: Campbell-White2023) Campbell-White, J., Manara, C. F., Benisty, M., et al. 2023, ApJ, 956, 25, doi: [`10.3847/1538-4357/acf0c0`](http://doi.org/10.3847/1538-4357/acf0c0)

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Casassus2022) Casassus, S., & Cárcamo, M. 2022, MNRAS, 513, 5790, doi: [`10.1093/mnras/stac1285`](http://doi.org/10.1093/mnras/stac1285)

(ref: Casassus2013) Casassus, S., van der Plas, G. M., Perez, S., et al. 2013, Nature, 493, 191, doi: [`10.1038/nature11769`](http://doi.org/10.1038/nature11769)

(ref: Casassus2019) Casassus, S., Marino, S., Lyra, W., et al. 2019, MNRAS, 483, 3278, doi: [`10.1093/mnras/sty3269`](http://doi.org/10.1093/mnras/sty3269)

(ref: Chatterjee2014) Chatterjee, S., & Tan, J. C. 2014, ApJ, 780, 53, doi: [`10.1088/0004-637X/780/1/53`](http://doi.org/10.1088/0004-637X/780/1/53)

(ref: Chung2024) Chung, C.-Y., Andrews, S. M., Gurwell, M. A., et al. 2024, ApJS, 273, 29, doi: [`10.3847/1538-4365/ad528b`](http://doi.org/10.3847/1538-4365/ad528b)

(ref: ALMA_TH2023) Cortes, P., Vlahakis, C., Hales, A., et al. 2023, ALMA Cycle 10 Technical Handbook, doi: [`10.5281/zenodo.7822943`](http://doi.org/10.5281/zenodo.7822943)

(ref: Doi2021) Doi, K., & Kataoka, A. 2021, ApJ, 912, 164, doi: [`10.3847/1538-4357/abe5a6`](http://doi.org/10.3847/1538-4357/abe5a6)

(ref: Doi2023) —. 2023, ApJ, 957, 11, doi: [`10.3847/1538-4357/acf5df`](http://doi.org/10.3847/1538-4357/acf5df)

(ref: Dong2012) Dong, R., Hashimoto, J., Rafikov, R., et al. 2012, ApJ, 760, 111, doi: [`10.1088/0004-637X/760/2/111`](http://doi.org/10.1088/0004-637X/760/2/111)

(ref: Duffell2015) Duffell, P. C., & Dong, R. 2015, ApJ, 802, 42, doi: [`10.1088/0004-637X/802/1/42`](http://doi.org/10.1088/0004-637X/802/1/42)

(ref: Foreman-Mackey2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Fukagawa2013) Fukagawa, M., Tsukagoshi, T., Momose, M., et al. 2013, PASJ, 65, L14, doi: [`10.1093/pasj/65.6.L14`](http://doi.org/10.1093/pasj/65.6.L14)

(ref: Gaia2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: Gregorio-Hetem2002) Gregorio-Hetem, J., & Hetem, A. 2002, MNRAS, 336, 197, doi: [`10.1046/j.1365-8711.2002.05716.x`](http://doi.org/10.1046/j.1365-8711.2002.05716.x)

(ref: Haffert2019) Haffert, S. Y., Bohn, A. J., de Boer, J., et al. 2019, Nature Astronomy, 3, 749, doi: [`10.1038/s41550-019-0780-5`](http://doi.org/10.1038/s41550-019-0780-5)

(ref: Hammer2021) Hammer, M., Lin, M.-K., Kratter, K. M., & Pinilla, P. 2021, MNRAS, 504, 3963, doi: [`10.1093/mnras/stab1079`](http://doi.org/10.1093/mnras/stab1079)

(ref: Hashimoto2020) Hashimoto, J., Aoyama, Y., Konishi, M., et al. 2020, AJ, 159, 222, doi: [`10.3847/1538-3881/ab811e`](http://doi.org/10.3847/1538-3881/ab811e)

(ref: Hashimoto2012) Hashimoto, J., Dong, R., Kudo, T., et al. 2012, ApJL, 758, L19, doi: [`10.1088/2041-8205/758/1/L19`](http://doi.org/10.1088/2041-8205/758/1/L19)

(ref: Ikoma2000) Ikoma, M., Nakazawa, K., & Emori, H. 2000, ApJ, 537, 1013, doi: [`10.1086/309050`](http://doi.org/10.1086/309050)

(ref: Isella2019) Isella, A., Benisty, M., Teague, R., et al. 2019, ApJL, 879, L25, doi: [`10.3847/2041-8213/ab2a12`](http://doi.org/10.3847/2041-8213/ab2a12)

(ref: Jiang2021) Jiang, H., & Ormel, C. W. 2021, MNRAS, 505, 1162, doi: [`10.1093/mnras/stab1278`](http://doi.org/10.1093/mnras/stab1278)

(ref: Jiang2023) —. 2023, MNRAS, 518, 3877, doi: [`10.1093/mnras/stac3275`](http://doi.org/10.1093/mnras/stac3275)

(ref: Johansen2007) Johansen, A., Oishi, J. S., Mac Low, M.-M., et al. 2007, Nature, 448, 1022, doi: [`10.1038/nature06086`](http://doi.org/10.1038/nature06086)

(ref: JvM1995) Jorsater, S., & van Moorsel, G. A. 1995, AJ, 110, 2037, doi: [`10.1086/117668`](http://doi.org/10.1086/117668)

(ref: Keppler2018) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44, doi: [`10.1051/0004-6361/201832957`](http://doi.org/10.1051/0004-6361/201832957)

(ref: Keppler2019) Keppler, M., Teague, R., Bae, J., et al. 2019, A&A, 625, A118, doi: [`10.1051/0004-6361/201935034`](http://doi.org/10.1051/0004-6361/201935034)

(ref: Kley2006) Kley, W., & Dirksen, G. 2006, A&A, 447, 369, doi: [`10.1051/0004-6361:20053914`](http://doi.org/10.1051/0004-6361:20053914)

(ref: Lau2024) Lau, T. C. H., Birnstiel, T., Drążkowska, J., & Stammler, S. M. 2024, A&A, 688, A22, doi: [`10.1051/0004-6361/202450464`](http://doi.org/10.1051/0004-6361/202450464)

(ref: Law2024) Law, C. J., Benisty, M., Facchini, S., et al. 2024, ApJ, 964, 190, doi: [`10.3847/1538-4357/ad24d2`](http://doi.org/10.3847/1538-4357/ad24d2)

(ref: Li2023) Li, Y.-P., Chen, Y.-X., & Lin, D. N. C. 2023, MNRAS, 526, 5346, doi: [`10.1093/mnras/stad3049`](http://doi.org/10.1093/mnras/stad3049)

(ref: Liu2024) Liu, H. B., Casassus, S., Dong, R., et al. 2024, arXiv e-prints, arXiv:2406.19843, doi: [`10.48550/arXiv.2406.19843`](http://doi.org/10.48550/arXiv.2406.19843)

(ref: Lovelace1999) Lovelace, R. V. E., Li, H., Colgate, S. A., & Nelson, A. F. 1999, ApJ, 513, 805, doi: [`10.1086/306900`](http://doi.org/10.1086/306900)

(ref: Mathis1977) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425, doi: [`10.1086/155591`](http://doi.org/10.1086/155591)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mesa2019) Mesa, D., Keppler, M., Cantalloube, F., et al. 2019, A&A, 632, A25, doi: [`10.1051/0004-6361/201936764`](http://doi.org/10.1051/0004-6361/201936764)

(ref: Mizuno1980) Mizuno, H. 1980, Progress of Theoretical Physics, 64, 544, doi: [`10.1143/PTP.64.544`](http://doi.org/10.1143/PTP.64.544)

(ref: Muller2018) Müller, A., Keppler, M., Henning, T., et al. 2018, A&A, 617, L2, doi: [`10.1051/0004-6361/201833584`](http://doi.org/10.1051/0004-6361/201833584)

(ref: Ono2016) Ono, T., Muto, T., Takeuchi, T., & Nomura, H. 2016, ApJ, 823, 84, doi: [`10.3847/0004-637X/823/2/84`](http://doi.org/10.3847/0004-637X/823/2/84)

(ref: Pascucci2012) Pascucci, I., Gorti, U., & Hollenbach, D. 2012, ApJL, 751, L42, doi: [`10.1088/2041-8205/751/2/L42`](http://doi.org/10.1088/2041-8205/751/2/L42)

(ref: Pinilla2012a) Pinilla, P., Benisty, M., & Birnstiel, T. 2012, A&A, 545, A81, doi: [`10.1051/0004-6361/201219315`](http://doi.org/10.1051/0004-6361/201219315)

(ref: Pinilla2024) Pinilla, P., Benisty, M., Waters, R., Bae, J., & Facchini, S. 2024, A&A, 686, A135, doi: [`10.1051/0004-6361/202348707`](http://doi.org/10.1051/0004-6361/202348707)

(ref: Portilla-Revelo2023) Portilla-Revelo, B., Kamp, I., Facchini, S., et al. 2023, A&A, 677, A76, doi: [`10.1051/0004-6361/202346607`](http://doi.org/10.1051/0004-6361/202346607)

(ref: Rampinelli2024) Rampinelli, L., Facchini, S., Leemker, M., et al. 2024, arXiv e-prints, arXiv:2407.06272, doi: [`10.48550/arXiv.2407.06272`](http://doi.org/10.48550/arXiv.2407.06272)

(ref: Riviere-Marichalar2024) Rivière-Marichalar, P., Macı́as, E., Baruteau, C., et al. 2024, A&A, 683, A141, doi: [`10.1051/0004-6361/202347464`](http://doi.org/10.1051/0004-6361/202347464)

(ref: Rota2024) Rota, A. A., Meijerhof, J. D., van der Marel, N., et al. 2024, A&A, 684, A134, doi: [`10.1051/0004-6361/202348387`](http://doi.org/10.1051/0004-6361/202348387)

(ref: Sekiya1983) Sekiya, M. 1983, Progress of Theoretical Physics, 69, 1116, doi: [`10.1143/PTP.69.1116`](http://doi.org/10.1143/PTP.69.1116)

(ref: Sekiya1998) —. 1998, Icarus, 133, 298, doi: [`10.1006/icar.1998.5933`](http://doi.org/10.1006/icar.1998.5933)

(ref: Tan2016) Tan, J. C., Chatterjee, S., Hu, X., Zhu, Z., & Mohanty, S. 2016, IAU Focus Meeting, 29A, 6, doi: [`10.1017/S1743921316002313`](http://doi.org/10.1017/S1743921316002313)

(ref: Tanaka2022) Tanaka, Y. A., Kanagawa, K. D., Tanaka, H., & Tanigawa, T. 2022, ApJ, 925, 95, doi: [`10.3847/1538-4357/ac3af5`](http://doi.org/10.3847/1538-4357/ac3af5)

(ref: Tanigawa2012) Tanigawa, T., Ohtsuki, K., & Machida, M. N. 2012, ApJ, 747, 47, doi: [`10.1088/0004-637X/747/1/47`](http://doi.org/10.1088/0004-637X/747/1/47)

(ref: Tripathi2017) Tripathi, A., Andrews, S. M., Birnstiel, T., & Wilner, D. J. 2017, ApJ, 845, 44, doi: [`10.3847/1538-4357/aa7c62`](http://doi.org/10.3847/1538-4357/aa7c62)

(ref: vanderMarel2013) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: scipy2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Wahhaj2024) Wahhaj, Z., Benisty, M., Ginski, C., et al. 2024, A&A, 687, A257, doi: [`10.1051/0004-6361/202349018`](http://doi.org/10.1051/0004-6361/202349018)

(ref: Wang2020) Wang, J. J., Ginzburg, S., Ren, B., et al. 2020, AJ, 159, 263, doi: [`10.3847/1538-3881/ab8aef`](http://doi.org/10.3847/1538-3881/ab8aef)

(ref: Wang2021) Wang, J. J., Vigan, A., Lacour, S., et al. 2021, AJ, 161, 148, doi: [`10.3847/1538-3881/abdb2d`](http://doi.org/10.3847/1538-3881/abdb2d)

(ref: Ward2010) Ward, W. R., & Canup, R. M. 2010, AJ, 140, 1168, doi: [`10.1088/0004-6256/140/5/1168`](http://doi.org/10.1088/0004-6256/140/5/1168)

(ref: Whipple1972) Whipple, F. L. 1972, in From Plasma to Planet, ed. A. Elvius, 211

(ref: Wu2023) Wu, Y., Chen, Y.-X., Jiang, H., et al. 2023, MNRAS, 523, 2630, doi: [`10.1093/mnras/stad1553`](http://doi.org/10.1093/mnras/stad1553)

(ref: Youdin2005) Youdin, A. N., & Goodman, J. 2005, ApJ, 620, 459, doi: [`10.1086/426895`](http://doi.org/10.1086/426895)

(ref: Youdin2002) Youdin, A. N., & Shu, F. H. 2002, ApJ, 580, 494, doi: [`10.1086/343109`](http://doi.org/10.1086/343109)

(ref: Zhu2012) Zhu, Z., Nelson, R. P., Dong, R., Espaillat, C., & Hartmann, L. 2012, ApJ, 755, 6, doi: [`10.1088/0004-637X/755/1/6`](http://doi.org/10.1088/0004-637X/755/1/6)

[^1]: (cite: Tanaka2022) present two equations (15) and (18) as critical planet masses, and state that it is currently unknown which one is better criteria from the current simulations. Here, as an upper limit of the PDS 70 c, we used the equation (18), which is a conservative one when using the aspect ratio assumed for PDS 70.

</paper>

Write the methods card for this paper.