# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...690A.171P\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...690A.171P",
 "title": "No evidence of active galactic nucleus features in the nuclei of Arp 220 from JWST/NIRSpec IFS",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Perna, Michele",
 "n_authors": 15,
 "arxiv_id": "2403.13948",
 "doi": "10.1051/0004-6361/202450094",
 "alma_projects_linked_by_archive": [
  "2015.1.00113.S",
  "2017.1.00042.S"
 ]
}
```

Paper text:
<paper>
# No evidence of AGN features in the nuclei of Arp 220 from JWST/NIRSpec IFS

Arp 220 is the nearest ultra-luminous infrared galaxy; it shows evidence of 100 pc-scale molecular outflows likely connected with galaxy-scale outflows traced by ionised and neutral gas. The two highly obscured nuclei of Arp 220 are the site of intense star formation, with extreme (far-infrared based) star-formation rate surface densities, $\Sigma_{SFR} \gtrsim 10^3$ M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$. Despite extensive investigations searching for active galactic nucleus (AGN) activity in the Arp 220 nuclei, direct evidence remains elusive.

We present JWST/NIRSpec IFS observations covering the $0.9-5.1\ \mu$m wavelength range of the innermost ($5\ensuremath{''} \times 4\ensuremath{''}$, i.e. $1.8\times 1.5$ kpc) regions of Arp 220. The primary goal is to investigate the potential presence of AGN signatures in the nuclear regions by analysing the spectra extracted from circular apertures of radius 55 pc (0.15$''$) around each of the two nuclei.

The analysis aims to identify highly ionised gas emission lines (with ionisation potential $> 54$ eV) and other spectral features indicative of AGN activity. Ionised and molecular gas kinematics are also taken into account to study the outflow signatures at $< 60$ pc scales.

We identify $\sim 70$ ionised and $\sim 50$ molecular emission lines in the nuclear spectra of Arp 220. We use recombination line ratios to measure optical extinctions in the range A$_V \sim 11-14$ mag. High ionisation lines are not detected, except the \[Mg \] line at 4.49 $\mu$m which we interpret as due to shocks rather than to AGN ionisation. We identify broadening and multiple kinematic components in the H  and H$_2$ lines caused by outflows and shocks, with velocities up to $\sim 550$ km s$^{-1}$. Significantly higher velocities (up to $\sim 900$ km s$^{-1}$) are detected in the off-nuclear regions; however, they do not conclusively represent evidence for AGN activity.

Even with the unprecedented sensitivity of JWST/NIRSpec IFS, achieving an unambiguous identification or exclusion of the presence of an AGN in the Arp 220 system remains challenging, because of its extreme dust obscuration.

# Introduction

Arp 220 is the closest ultra-luminous infrared galaxy (ULIRG), with a distance of $\sim 78$ Mpc and log $L_{IR}/L_\odot$ = 12.2 (e.g. (cite: Pereira2021)). This late-stage merger shows several tidal structures in the outskirts (e.g. (cite: Arp1966; Arribas2001; Perna2020)) and contains two compact ($< 150$ pc), highly obscured nuclei separated by $\sim 370$ pc (1$''$) that dominate the infrared luminosity (e.g. (cite: Scoville2007)).

The nuclear region of Arp 220 is the site of an intense star formation, with a star formation rate SFR $\sim 200 - 250$ M$_{\odot}$ yr$^{-1}$(e.g. (cite: Nardini2010; Varenius2016)) and incredibly high star formation rate surface densities ($\Sigma_{SFR} \sim 10^3-10^4$ M$_{\odot}$ yr$^{-1}$ kpc$^2$, from radio and far-infrared observations; e.g. (cite: BarcosMunoz2015; Pereira2021)). Long-term monitoring with very long baseline interferometry has revealed dozens of supernovae and supernova remnants resulting from the extreme star formation occurring in the compact nuclei (e.g. (cite: Varenius2019)). The off-nuclear regions appear to have post-starburst properties, with weak star formation produced in a few young and low-mass clusters (e.g. (cite: Perna2020; Chandar2023)), as expected for a late-stage merger.

Although Arp 220 has been extensively studied from radio to hard X-ray and $\gamma$-ray wavelengths, there is still no convincing direct evidence for the presence of active galactic nucleus (AGN) activity in either of the two nuclei;

however, indirect arguments provide suggestive indications (e.g. (cite: Teng2015; Paggi2017; Yoast2019)). Accreting super-massive black holes (SMBHs) could be buried in Compton-thick absorbers (i.e. $N_H > 1.5\times 10^{24}$ cm$^{-2}$) at the position of the two nuclei ((cite: Teng2015; Sakamoto2021a)) and, for instance, explain the excess of $\gamma$-ray flux in comparison to all other diagnostics of star-forming activity ((cite: YoastHull2017)).

Evidence of multi-phase (i.e. molecular, neutral, and ionised) outflows in Arp 220 have been inferred from the analysis of multi-wavelength observations. Collimated outflows have been discovered in both nuclei on scales of $\sim 100$ pc using, for instance, ALMA observations of carbon monoxide transitions (e.g. (cite: Wheeler2020; Ueda2022; Lamperti2022)); large-scale outflows have also been identified with optical integral field instruments (IFS; e.g. (cite: Arribas2001; Colina2004; Perna2020)) and associated with extended soft X-ray emission (e.g. (cite: McDowell2003)). The possible connection between these multi-phase and multi-scale outflows has not yet been investigated in detail. Consequently, the mechanisms at the origin of these outflows, and hence whether they are due to starburst or AGN winds, are still debated.

In this work, we revisit Arp 220 and its nuclear regions taking advantage of JWST observations performed with the IFS unit of the NIRSpec instrument ((cite: Jakobsen2022; Boker2022)); these data cover the near-infrared (NIR) wavelength range between 0.95 and 5.1 $\mu$m. The observations were taken as part of the JWST/NIRSpec IFS Guaranteed Time Observations (GTO) survey “Resolved structure and kinematics of the nuclear regions of nearby galaxies” (program lead: Torsten Böker). The analysis presented in this paper aims to identify AGN signatures in the Arp 220 nuclei, as the presence of highly ionised gas and extreme kinematics unambiguously associated with accreting SMBHs.

The rest of this paper is organised as follows. Section [2](#sec:reduction) presents the NIRSpec IFS observations and data reduction. Section [3](#sec:analysis) describes the spectral fitting analysis and the identification of emission line species. Section [4](#sec:results) reports a qualitative description of the nuclear spectra as well as that of a nearby bright stellar cluster, and some general properties of the interstellar medium (ISM). The multi-phase outflow properties, the absence of highly ionised species, and the comparison between H  and far-IR SFR tracers are discussed in Section [5](#sec:discussion). Finally, Section [6](#sec:conclusions) summarises our conclusions. Throughout this work, we assume $\Omega_m=0.286$ and $H_0=69.9$ km/s/Mpc (cite: Bennett2014). With this cosmology, $1''$ corresponds to a distance of 0.368 kpc at $z=0.018$.

# Observations and data reduction

Arp 220 was observed in NIRSpec IFS mode as part of the programme 1267 (PI: D. Dicken). The present observations were combined in a single proposal with independent MIRI acquisitions of the same target, with the aim of saving the telescope slew overhead. The observations were collected on 6 March 2023, using the NIRSpec IFS mode ((cite: Boker2022)).

The dataset consists of two distinct sets of four-point medium cycling dithering pattern with 15 groups per exposure. The first set is centred at the mid-point between the coordinates of the western (W) and the eastern (E) nuclei; the second set is offset $\sim 1\ensuremath{''}$ towards the north-west to cover the shell of H$\alpha$ and \[N \] emission (e.g. (cite: Lockhart2015; Perna2020)). The total integration time is 933 seconds per set, in each of the three high resolution (R $\sim 2700$) grating settings, to cover the spectral range from 0.95 to 5.1 $\mu$m.

## Data reduction

We used the STScI pipeline v1.8.2 with CRDS context 1063. A patch was included to correct some important bugs that affect this specific version of the pipeline (cite: Perna2023a). In particular, we corrected the count-rate images for $1/f$ noise by fitting a polynomial. During stage 2, we masked pixels at the edge of the slices (one pixel wide) to conservatively exclude pixels for which the correction for the throughput of the spectrograph optics (contained in the SFLAT reference files) is unreliable. We also implemented the outlier rejection of (cite: DEugenio2023). The combination of the eight dithers (with drizzle weighting) allowed us to sub-sample the detector pixels, resulting in cube spaxels with a size of 0.05$''$ (corresponding to $\sim 20$ pc per spaxel).

The resulting data cubes are known to show sinusoidal modulations in single spaxel spectra, caused by the undersampling of the point-spread function (PSF). To correct these so-called “wiggles”, we applied the methodology presented in (cite: Perna2023a), and adapted to the Arp 220 dataset as reported in (cite: Uliviinprep). However, we note that these wiggles do not affect the results presented in this work, because we use spatially integrated spectra, which are much less affected by PSF undersampling (e.g. (cite: Law2023)).

In addition to the Arp 220 dataset, in this manuscript we present the JWST/NIRSpec observations of another extra-galactic source, the nearby LIRG VV114 (programme 1328, PI: L. Armus; e.g. (cite: Rich2023)). They were reduced following the same procedure reported above.

Therefore, for both Arp 220 and VV114 we obtained three data cubes, corresponding to the grating settings G140H/F100LP (referred to as band1 hereinafter), G235H/F170LP (band2), and G395H/F290LP (band3), covering the wavelength range 0.95 – 5.1 $\mu$m.

![]({images/Arp220_3colours})

## Astrometric registration

Before analysing the Arp 220 data-cubes, we tested whether they are aligned with each other. We extracted NIRSpec equivalent narrow-band images from the wavelength range $1.85-1.87\ \mu$m covered by both band1 and band2 cubes; these images are perfectly aligned in the pixel space, although a small discrepancy in the WCS coordinates registration of the reference pixel introduces an offset of $\delta$RA $=-0.0047\ensuremath{''}$ and $\delta$DEC $= -0.0141\ensuremath{''}$. Similarly, we obtained additional narrow-band images covering the range $3.00-3.02\ \mu$m from the band2 and band3 cubes; also in this case, the images are perfectly aligned in the pixel space, but present a discrepancy in WCS registrations, with $\delta$RA $=+0.0017\ensuremath{''}$ and $\delta$DEC $= 0.0071\ensuremath{''}$. Therefore, we corrected the WCS registrations of the band2 and band3 cubes to match the coordinates in band1.

The absolute astrometric registration is performed using the ALMA 0.1$''$  resolution maps of continuum emission at 2.6 mm presented by (cite: Scoville2017), and the 0.03$''$  resolution map of 1.3 mm continuum (project 2017.1.00042.S). We matched the central position of the two nuclei in the NIRSpec narrow-band image, obtained by collapsing the band3 cube in the range $5.1-5.12\mu$m, and in the ALMA images. The narrow wavelength range used to identify the nuclei in the NIR has been preferred to those at shorter wavelengths, as the latter are significantly more affected by dust extinction (see Sect. [3](#sec:analysis)). The astrometry corrections we applied to the three NIRSpec cubes are $\delta$RA $=-0.3028\ensuremath{''}$ and $\delta$DEC $= -0.0209\ensuremath{''}$. This offset is consistent with the expected accuracy of JWST pointing without a dedicated target acquisition procedure ((cite: Boker2023)).

# Analysis

The two Arp 220 nuclei separated by $\sim 1$$''$ are visible in the infrared (e.g. (cite: Scoville1998)), millimetre (e.g. (cite: Scoville2017; Lamperti2022)), radio (e.g. (cite: Baan1995)), and X-ray (e.g. (cite: Lockhart2015)). Figure [1](#fig:fig1) shows the composite near-infrared image of Arp 220 obtained from the combination of three NIRSpec narrow-band images extracted from the reduced data-cube at $\sim 1\mu$m (blue), $3\mu$m (green) and $5\mu$m (red), covering a Field of View (FoV) of $5\ensuremath{''} \times 4\ensuremath{''}$. The position of the W and E nuclei are marked for visual purposes.

The Arp 220 nuclear morphology is strongly influenced by dust extinction, even in the NIR (see also Fig. [7](#fig:figA1)).

The continuum emission appears as a crescent arc above the W nucleus at $\sim 1\mu$m and $\sim 3\mu$m. The E nucleus is barely visible at these wavelengths, but a few bright, clumpy regions likely associated with clusters can be identified (see also (cite: Scoville1998)). Among them, we marked with a box-circle the position of the brightest clump at the north of the E nucleus; hereinafter, we refer to it as the NE cluster, although it may be part of a more extended structure connecting the blue clumps in the regions between the nuclei in Fig. [1](#fig:fig1). The emission at $\sim 5\ \mu$m is mostly dominated by the two unresolved nuclei, marked in the figure with two crosses.

![]({images/Arp220_nuclearspectra.pdf})

## Spectral extraction

We extracted the spectra of the two nuclei and the NE cluster shown in Fig. [1](#fig:fig1) for each of the three NIRSpec gratings. We used apertures of three spaxels in radius, corresponding to $0.15\ensuremath{''}$ or $55$ pc. This aperture size broadly corresponds to two NIRSpec spatial resolution elements at 5 $\mu$m (FWHM $\sim 0.15\ensuremath{''}$; (cite: DEugenio2023)), thus ensuring that the entire point-source flux is captured at all wavelengths.

The three spectra are reported in Fig. [2](#fig:totalspectra); they are shown in rest-frame, taking into account their relative redshifts: $z_W = 0.01774$, $z_E = 0.01839$, and $z_{NE} = 0.01870$ (see Table [\[tab:properties\]](#tab:properties)). These values are obtained by measuring the centroid of the brightest hydrogen lines, and are comparable with those inferred from sub-mm/mm ALMA spectroscopy at angular resolutions similar to those of NIRSpec (see Sect. [4.1](#sec:zspec)).

The spectra show a few gaps in wavelength coverage in the middle of the three bands, due to the gap between the two NIRSpec detectors. The overlapping wavelength ranges at $\sim 1.85\ \mu$m and $\sim 3\ \mu$m show a perfect match between the different bands, demonstrating a consistent flux calibration. We note that no aperture corrections are taken into account in this work.

|  | W nucleus | E nucleus | NE cluster |
|:---|:--:|:--:|:--:|
| RA (J2000) | 15:34:57.224 | 15:34:57.294 | 15:34:57.309 |
| DEC (J2000) | +23:30:11.515 | +23:30:11.353 | +23:30:11.698 |
| redshift (H ) | 0.01774 $\pm$ 0.00001 | 0.018396 $\pm$ 0.00001 | 0.018704 $\pm$ 0.00001 |
| redshift (stars) | $0.0179\pm 0.0003$ | $0.0183\pm 0.0002$ | $0.0186\pm0.0001$ |
| SFR(radio/far-IR) \[M$_{\odot}$ yr$^{-1}$\] | 110 – 150 | 60 – 80 | – |
| SFR(Pa$\alpha$$_{corr}$) \[M$_{\odot}$ yr$^{-1}$\] | $0.52_{-0.06}^{+0.16}$ | $0.17\pm 0.02$ | $0.94\pm 0.02$ |
| SFR(PAH $3.3\ \mu$m) \[M$_{\odot}$ yr$^{-1}$\] | $3.4\pm 0.2$ | $1.5\pm 0.2$ | $1.9\pm 0.2$ |
| A$_v$ \[mag\] | $10.6_{-0.5}^{+1.7}$ | $14.1_{-0.3}^{+0.6}$ | $11.2\pm 0.1$ |
| log ($n_e$/\[cm$^{-3}$\] | $3.7\pm 0.1$ | $4.5\pm 0.4$ | $3.6\pm 0.1$ |

Notes: SFR measurements are corrected for dust extinction using the A$_V$ reported in the table; the latter are obtained from Eq. [\[eq:EBVBr\]](#eq:EBVBr), assuming $R_V = 3.1$. Radio and far-IR based SFR measurements come from (cite: Varenius2016) and (cite: Pereira2021), respectively.

## Identification of the lines

The identification of the multitude of emission lines detected in NIRSpec spectra of Arp 220, and marked in Fig. [2](#fig:totalspectra) with vertical lines, was performed using compilations of NIR features in star-forming and active galaxies from the literature (e.g. (cite: Lutz2000; Koo2016; Lamperti2017; Lee2017; Riffel2019)). We also use the NIST atomic spectra database[^2] ((cite: Ralchenko2005)) and the HITRAN (high-resolution transmission molecular absorption database[^3], (cite: Rothman2021)) to provide probable identifications of faint lines that, to our knowledge, have not previously been reported in the literature.

Figures [8](#fig:portion1)-[13](#fig:portion6) report all species identified in the spectra of the Arp 220 nuclei and the NE cluster, in comparison with those in the nuclear regions of another nearby interacting LIRG observed with NIRSpec, VV114 (e.g. (cite: Rich2023)). Firmly detected line transitions are indicated with solid vertical lines, and are also reported in Table [\[tab:linelist\]](#tab:linelist). Probable identifications are marked in the figures in the Appendix with dotted vertical lines. All emission lines are well visible in the spectra of the south-west nucleus of VV114 (named SWc2 by (cite: GonzalezAlfonso2023)), at higher signal-to-noise and with narrower profiles than in Arp 220.

All three nuclear regions of VV114, namely NE, SW, and SWc2, have been suggested to harbor deeply obscured AGN (e.g. (cite: Rich2023; GonzalezAlfonso2023)). Hence, they serve as an optimal benchmark for comparison with the nuclei of Arp 220, which are also presumed to contain obscured AGN.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| line | $\lambda_{vac}$ | $f_W$ | $f_E$ | $f_{NE}$ |
|  | ($\mu$m) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) |
| \[S \] | 0.953321 | 598.0$_{-0.4}^{+0.4}$ | 54.9$_{-1.2}^{+1.1}$ | 438.0$_{-1.0}^{+1.8}$ |
| Pa$\epsilon$ | 0.954865 | 87.9$_{-1.0}^{+1.5}$ | 7.8$_{-0.8}^{+1.0}$ | 41.7$_{-0.8}^{+1.9}$ |
|  | 0.982412 | 11.3$_{-1.1}^{+1.2}$ | 3.3$_{-0.6}^{+0.8}$ | 8.8$_{-0.9}^{+1.8}$ |
|  | 0.985295 | 63.7$_{-0.5}^{+1.2}$ | 15.5$_{-0.9}^{+1.4}$ | 28.8$_{-0.3}^{+0.0}$ |
| Pa$\delta$ | 1.005219 | 112.0$_{-1.5}^{+1.4}$ | 15.8$_{-1.0}^{+1.2}$ | 67.6$_{-0.8}^{+1.6}$ |
|  | 1.028955 | 48.3$_{-2.7}^{+5.2}$ | 5.7$_{-1.5}^{+4.2}$ | 11.6$_{-1.6}^{+2.5}$ |
|  | 1.032332 | 62.6$_{-2.2}^{+2.5}$ | 0.9$_{-0.0}^{+0.0}$ | 13.6$_{-1.6}^{+2.7}$ |
|  | 1.033924 | 63.1$_{-1.0}^{+2.6}$ | 5.3$_{-1.9}^{+2.4}$ | 17.2$_{-1.4}^{+2.6}$ |
|  | 1.037334 | 39.3$_{-0.3}^{+0.1}$ | 0.9$_{-0.0}^{+4.4}$ | 11.1$_{-2.7}^{+6.1}$ |
| $[$N \] | 1.040059 | 42.8$_{-0.0}^{+0.1}$ | 4.2$_{-3.2}^{+2.9}$ | 3.8$_{-2.8}^{+2.5}$ |
| He  | 1.083331 | 628.0$_{-1.1}^{+2.2}$ | 41.2$_{-0.4}^{+1.3}$ | 185.0$_{-0.7}^{+1.0}$ |
| Pa$\gamma$ | 1.094116 | 167.0$_{-1.6}^{+1.7}$ | 25.5$_{-0.6}^{+1.1}$ | 205.0$_{-1.9}^{+1.7}$ |
|  | 1.147134 | 101.0$_{-0.9}^{+1.4}$ | 9.4$_{-0.5}^{+1.0}$ | 45.7$_{-0.7}^{+1.2}$ |
|  | 1.188605 | 328.0$_{-0.7}^{+1.3}$ | 27.8$_{-0.3}^{+0.7}$ | 126.0$_{-0.8}^{+0.9}$ |
| $[$Ni \] | 1.191000 | 31.5$_{-0.6}^{+1.3}$ | 5.0$_{-0.7}^{+0.6}$ | 19.6$_{-0.8}^{+1.1}$ |
|  | 1.257021 | 711.0$_{-4.3}^{+10.6}$ | 78.0$_{-1.8}^{+3.6}$ | 371.0$_{-3.8}^{+7.2}$ |
|  | 1.270690 | 44.5$_{-2.2}^{+5.1}$ | 0.8$_{-0.0}^{+1.7}$ | 10.8$_{-3.6}^{+6.6}$ |
|  | 1.278789 | 75.6$_{-1.6}^{+3.7}$ | 3.3$_{-2.5}^{+6.0}$ | 26.7$_{-3.1}^{+5.5}$ |
| Pa$\beta$ | 1.282167 | 1170.0$_{-7.0}^{+6.7}$ | 124.0$_{-2.6}^{+4.6}$ | 822.0$_{-4.1}^{+6.5}$ |
|  | 1.294453 | 71.7$_{-2.5}^{+6.6}$ | 7.1$_{-2.0}^{+2.8}$ | 24.6$_{-2.0}^{+5.3}$ |
|  | 1.320911 | 289.0$_{-4.5}^{+7.0}$ | 26.9$_{-2.0}^{+3.2}$ | 130.0$_{-3.8}^{+4.6}$ |
| $[$O I\] | 1.316871 | 94.2$_{-2.5}^{+5.3}$ | 4.0$_{-2.4}^{+3.0}$ | 22.6$_{-2.2}^{+5.3}$ |
|  | 1.372200 | 185.0$_{-4.3}^{+6.1}$ | 25.0$_{-1.2}^{+2.9}$ | 102.0$_{-2.0}^{+4.3}$ |
| Br 13 | 1.611378 | 51.6$_{-3.6}^{+6.9}$ | 9.2$_{-3.0}^{+3.5}$ | 54.0$_{-3.8}^{+5.2}$ |
| Br 12 | 1.641174 | 71.3$_{-4.2}^{+6.6}$ | 11.0$_{-4.5}^{+2.9}$ | 7.6$_{-3.8}^{+4.0}$ |
|  | 1.644002 | 1340.0$_{-5.7}^{+11.1}$ | 209.0$_{-3.9}^{+8.5}$ | 787.0$_{-8.6}^{+9.6}$ |
|  | 1.677300 | 160.0$_{-5.2}^{+6.6}$ | 20.3$_{-2.7}^{+6.4}$ | 67.3$_{-5.1}^{+5.8}$ |
| Br 11 | 1.681118 | 166.0$_{-7.0}^{+7.2}$ | 27.7$_{-2.5}^{+5.1}$ | 117.0$_{-3.3}^{+5.5}$ |
| H$_2$ | 1.714881 | 14.9$_{-11.3}^{+72.8}$ | 2.6$_{-0.1}^{+40.5}$ | 2.5$_{-0.0}^{+0.0}$ |
| H$_2$ | 1.714958 | 88.8$_{-59.5}^{+4.6}$ | 30.3$_{-20.1}^{+12.3}$ | 29.4$_{-7.0}^{+5.0}$ |
| H$_2$ | 1.748101 | 176.0$_{-8.6}^{+5.6}$ | 43.8$_{-8.3}^{+18.9}$ | 66.1$_{-5.9}^{+1.2}$ |
| Br  | 1.736692 | 202.0$_{-6.4}^{+6.3}$ | 17.4$_{-2.5}^{+4.5}$ | 111.0$_{-7.2}^{+6.9}$ |
| Br$\epsilon$ | 1.817916 | 245.0$_{-5.7}^{+11.5}$ | 34.0$_{-4.5}^{+8.3}$ | 168.0$_{-4.5}^{+12.7}$ |
| H$_2$ | 1.834123 | 23.1$_{-4.2}^{+11.9}$ | 57.8$_{-22.0}^{+12.6}$ | 37.6$_{-7.0}^{+8.2}$ |
| H$_2$ | 1.835913 | 370.0$_{-6.9}^{+12.4}$ | 109.0$_{-13.4}^{+39.8}$ | 145.0$_{-3.7}^{+10.8}$ |

Notes: This list comprises all emission lines detected in band1; see Tables [\[tab:linelist2\]](#tab:linelist2) and [\[tab:linelist3\]](#tab:linelist3) for the ones in band2 and band3, respectively. The reported fluxes are obtained within apertures of 0.3$''$  in diameter from single Gaussian fits, without dust- and aperture-corrections.

## Modelling of the continuum emission

To fit the stellar continuum, we used the penalised-pixel-fitting routine pPXF ((cite: Cappellari2017)). We used the MARCS synthetic library of stellar spectra to model the stellar continuum ((cite: Gustafsson2008)); these templates have a constant spectral resolution $\Delta\lambda/\lambda$ = 20 000 ($\sigma \sim 6$ km s$^{-1}$) and cover the range $0.13-20\ \mu$m with wavelengths in vacuum. Although not as reliable as an empirical stellar library, MARCS templates were preferred to E-MILES ((cite: Vazdekis2016)), which have lower spectral resolution than our NIRSpec data, and XSL ((cite: Verro2022)), which have narrower wavelength coverage and are affected by telluric features.

We also adopted a sixth-order multiplicative polynomial to better reproduce the spectral continuum shape. In addition, we used a set of gas emission line templates (parametrised with Gaussian profiles) together with the stellar ones to guide the fit. We conducted separate fits for the band1 ($0.95-1.86 \mu$m) and band2 ($1.63-3.11\ \mu$m) cubes, with the latter restricted to wavelengths below 2.4 $\mu$m, corresponding to the cutoff of the detector gap. For band1, the wavelengths falling within the NIRSpec detector gap were appropriately masked during the fit procedure.

Since no prominent stellar features are observed at wavelengths above $2.4\ \mu$m, and because of the presence of dust emission and ice absorption (e.g. (cite: Donnan2024)), we preferred to model the pseudo-continuum with a Savitzky–Golay filter after masking all prominent emission and absorption features.

In Figs. [8](#fig:portion1)-[10](#fig:portion3) we report the reconstructed pPXF best-fit continuum emission, while Figs. [11](#fig:portion4)-[13](#fig:portion6) show the pseudo-continuum shape in the two Arp220 nuclei and the NE cluster. We used the (pseudo-)continuum-subtracted spectra to model the emission lines, and hence derive the ISM kinematic and physical properties in these three regions.

## Modelling of the emission lines

After subtracting the (pseudo-)continuum, we modelled the most relevant gas emission lines using a combination of Gaussian profiles. In particular, we modelled a set of H  recombination lines - Paschen (Pa), Brackett (Br), Pfund (Pf), and Humphreys (Hu) series - and molecular hydrogen features, as well as singly ionised iron transitions.

The sets of H , H$_2$ and \[Fe \] transitions are modelled using independent fits, to account for the fact that these three species can trace different gas phases and can have therefore different systemic velocities and line widths (e.g. (cite: May2017)). All transitions were fitted using the Levenberg–Markwardt least-squares fitting code CAP-MPFIT ((cite: Cappellari2017)).

The transitions of a given species were fitted simultaneously (e.g. (cite: Perna2015a)), as it allows to better constrain the properties of the transitions associated with lower S/N. Namely, we constrained the wavelength separation between emission lines in accordance with atomic physics (considering their vacuum wavelengths); moreover, we fixed their widths (in km s$^{-1}$) to be the same for all the emission lines. Some emission lines are covered by two cubes (e.g. Br$\epsilon$ at $\sim 1.82\ \mu$m, in band1 and band2 spectra); for these lines we obtained an average profile by considering the errors from individual cubes as weights.

For each species we performed two fits, with one and two Gaussian components per emission line respectively. The number of Gaussian sets (i.e. distinct kinematic components) used to model the lines of a specific species was determined on the basis of the Bayesian information criterion (BIC; (cite: Schwarz1978)).

The measured fluxes of all identified emission line transitions are reported in Tables [\[tab:linelist\]](#tab:linelist), [\[tab:linelist2\]](#tab:linelist2) and [\[tab:linelist3\]](#tab:linelist3). To streamline the presentation, all tabulated fluxes are derived from single Gaussian fits; detailed Gaussian decomposition of bright line profiles is discussed in Sect. [4](#sec:results).

# Results

In this section, we report the general characterisation of the nuclei and the NE cluster, in terms of spectral shape, extinction, electron density, and presence of outflows. These properties are discussed in Sect. [5](#sec:discussion) to investigate the possible presence of AGN signatures.

## Systemic redshift of the two nuclei

The comparison of the three selected regions in Arp 220 was performed after reporting the individual spectra in luminosity ($\lambda L_\lambda$) as a function of the rest-frame wavelength in vacuum. We used the centroid of the H  lines to determine the redshifts for the three spectra. In fact, these lines are quite symmetric and narrow and, therefore, are likely less affected by outflows and perturbed motions than other lines (see (cite: Perna2020; Wheeler2020)). In contrast, the brightest H$_2$ and \[Fe \] lines show prominent blue wings and are blue-shifted by a few 10s km s$^{-1}$ with respect to the H  lines (Table [\[tab:kinematics\]](#tab:kinematics)).

The redshifts inferred from the atomic hydrogen lines are reported in Table [\[tab:properties\]](#tab:properties). These values are consistent with those obtained from the stellar continuum modelling, within the uncertainties (see Table [\[tab:properties\]](#tab:properties)). Moreover, our measurements match the ones obtained from the study of sub-mm/mm molecular line transitions as reported in (cite: Sakamoto2021b), $z_W \sim 0.01768$ and $z_E \sim 0.01808$, and (cite: Pereira2021), $z_W \sim 0.01765$ and $z_W \sim 0.01797$. In particular, for the W nucleus, all measurements are consistent within $\sim 20$ km s$^{-1}$. The molecular lines in the E nucleus are quite asymmetric (see Fig. 1 in (cite: Sakamoto2021b)), resulting in slightly larger discrepancies compared to our NIR redshift. However, all measurements remain consistent within $\lesssim 100$ km s$^{-1}$, suggesting minimal relative motions between the various components.

## Qualitative comparison between Arp 220 nuclear regions and the bright cluster

The spectra of the two nuclei and the NE cluster contain a high number of emission lines: among them hydrogen lines (from the Pa, Br, Pf, and Hu series), as well as helium, iron, and molecular hydrogen transitions. Notably, H  lines appear a few times fainter in the E spectrum compared to the W and NE spectra, likely due to higher extinction levels (see Sect. [4.3](#sec:extinction)) and lower SFR (Sect. [5.1](#sec:SFR)). The W nucleus displays the most intense H$_2$ lines, approximately $2\times$ stronger than those in the E and NE spectra.

At 3.3 $\mu$m, all three spectra show a broad emission feature produced by polycyclic aromatic hydrocarbons (PAHs); the 3.4 $\mu$m aliphatic features are also present in all three locations. PAHs and aliphatic transitions are stronger in the W nucleus, by a factor of $\sim 3$ (2) with respect to the E nucleus (NE cluster; see Sect. [5.1](#sec:SFR)). This suggests that the SFR is higher in the W nucleus (as PAHs trace recent star formation activity; Sect. [5.1](#sec:SFR)).

The prominent CO absorption bands at $\sim 1.6\  \mu$m and between 2.3 $\mu$m and 2.4 $\mu$m, produced in the atmospheres of giant and supergiant stars ((cite: Oliva1995)) are clearly visible in the two nuclei as well as in the NE cluster.

Various other broad-band absorption features are visible as well, mostly produced by solid state molecules of water-ice (H$_2$O, at 3 and 4.5 $\mu$m), and carbon monoxide (CO, at 4.67 $\mu$m) transitions. These absorption features are stronger in the nuclear regions than in the nearby cluster; the $3.3-3.8 \mu$m “ice band wing” ((cite: Gibb2004)) is observed only in the two nuclei. The strength of these absorption bands is therefore likely correlated with the abundance of dust, given that the two nuclear regions are the most obscured in the mm range ((cite: Sakamoto2021a)). Conversely, the carbon dioxide ice transitions $^{12}$CO$_2$ at 4.27 $\mu$m and $^{13}$CO$_2$ at 4.38 $\mu$m have rather peculiar shapes in the three spectra: the former is stronger in the E nucleus, but more asymmetric in the W nucleus (with a prominent blue shoulder), while the NE cluster shows intermediate strength with respect to the nuclei. The $^{13}$CO$_2$ is deeper and narrower in the W nucleus.

The W and E nuclei of Arp 220 show $^{12}$CO ro-vibrational lines up to J$_{low}$ = 23 (Fig. [13](#fig:portion6)), indicating the presence of high excitation gas. Such transitions could provide a further indirect evidence of AGN activity. Detailed modelling is required to infer the CO gas properties, and hence test the more likely mechanisms responsible for such high excitation (e.g. (cite: Baba2022; GonzalezAlfonso2023; Buiten2023; GarciaBernete2024; Pereira2024a)). This analysis will be presented in a forthcoming paper (Buiten, van der Werf et al., in prep.).

Differences in the three spectra can also be appreciated from a qualitative comparison between their continuum shapes. Going from the shortest wavelengths to $\sim 1.8\ \mu$m, all three sources show a pronounced steepening in their spectra, likely dominated by the diminishing effect of dust obscuration with increasing wavelength (see also (cite: Engel2011)). In the range $1.8-2.3\ \mu$m the W and NE spectra flatten, while the E spectrum still shows the same steepening observed at shortest wavelengths; this could suggest an higher extinction at the position of the E nucleus, due to the dust lane visible in reddish colours in Fig. [1](#fig:fig1). Between 2.3 and 5$\mu$m, the nuclear regions show a mild increase in luminosity while NE is almost constant. At $\sim 5\mu$m, the spectrum of the NE cluster reveals a modest rise in luminosity, while the two nuclei exhibit a much more pronounced increase likely due to the presence of warm dust ((cite: Armus2007)). It is possible therefore that dust-absorbed light is re-emitted at wavelengths $\gtrsim 2\ \mu$m in the two nuclei; the higher dilution of CO bands at $\sim 2.3 - 2.4\ \mu$m in the nuclei compared to the NE cluster (Fig. [10](#fig:portion3)) also supports this possibility, as suggested by (cite: Engel2011).

In the next sections, we will briefly discuss the general properties of some of these components. We do not pursue the full spectral energy distribution modelling further in this work, but instead will use a subsequent paper to focus on a more detailed investigation.

## Extinction

Extinction can have an important effect on the estimated source luminosity and SFR, and we therefore consider different methods for deriving its value. We compared pairs of emission lines at wide wavelength separation, for which the intrinsic ratio of line strengths is known. We calculated the colour excess in terms of Pa$\beta$ and Br$\gamma$,

$$\begin{equation}
\label{eq:EBVBr}
\begin{split}
E(B-V) & = \frac{2.5}{k(Pa\beta) - k(Br\gamma)} \ log_{10} \left( \frac{\left(Pa\beta/Br\gamma\right)_{obs}}{\left(Pa\beta/Br\gamma\right)_{int}} \right)\\ & = 5.22 \ log_{10} \left( \frac{\left(Pa\beta/Br\gamma\right)_{obs}}{5.88} \right)
\end{split}
\end{equation}$$

where the intrinsic ratio Pa$\beta$/Br$\gamma$ is set to 5.88 assuming an electron temperature and a density of 10$^4$ K and 10$^3$ cm$^{-3}$ respectively (e.g. (cite: Osterbrock2006)). We also used the Pf$\gamma$ and Br$\delta$ to obtain an independent estimate for the colour excess

$$\begin{equation}
\label{eq:EBVPf}
\begin{split}
E(B-V) & = \frac{2.5}{k(Br\delta) - k(Pf\gamma)} \ log_{10} \left( \frac{\left(Br\delta/Pf\gamma\right)_{obs}}{\left(Br\delta/Pf\gamma\right)_{int}} \right)\\ & = 8.95 \ log_{10} \left( \frac{\left(Br\delta/Pf\gamma\right)_{obs}}{1.71} \right)
\end{split}
\end{equation}$$

where the intrinsic ratio Br$\delta$/Pf$\gamma$ is set to 1.71 (with the same assumptions as reported above). The coefficients in Eqs. [\[eq:EBVBr\]](#eq:EBVBr) and [\[eq:EBVPf\]](#eq:EBVPf) were derived assuming a (cite: Cardelli1989) extinction law.

We derived an additional estimate of the colour excess from the flux ratio of \[Fe \] at 1.257 and 1.644 $\mu$m (e.g. (cite: Riffel2014)), which are the two strongest iron lines in the NIR regime,

$$\begin{equation}
\label{eq:EBVfe}
E(B-V) = 8.95 \ log_{10} \left( \frac{1.34}{\left([Fe II]_{1.257}/[Fe II]_{1.644}\right)_{obs}} \right)
\end{equation}$$

where 1.34 is the intrinsic ratio (we note, however, that this is still a matter of some debate, and different values are reported in the literature, from 1.04 to 1.49, see (cite: Eriksen2009)).

We measured a colour excess of the order of a few magnitudes ($\sim 3-5$) in the three regions of interest, corresponding to A$_V \sim 10-14$ (assuming R$_V = 3.1$). We do not observe significant differences in the measurements obtained from the three diagnostic ratios above mentioned (Eqs. [\[eq:EBVBr\]](#eq:EBVBr), [\[eq:EBVPf\]](#eq:EBVPf), [\[eq:EBVfe\]](#eq:EBVfe)). Therefore, hereinafter we will refer to the results obtained from Eq. [\[eq:EBVBr\]](#eq:EBVBr). The most extreme extinction is associated with the E nucleus, with A$_V \sim 14$, consistent with the presence of the strongest steepening in continuum emission at wavelengths $\lesssim 2\ \mu$m with respect to the W nucleus and the NE cluster (with A$_V \sim 11$, see Table [\[tab:properties\]](#tab:properties)).

In previous studies, an extinction of $\approx 6$ mag in the innermost nuclear regions of Arp 220 was reported, employing diagnostics such as the H  flux ratios H$\alpha$/H$\beta$((cite: Perna2020)), H$\alpha$/Pa$\beta$((cite: Gimenez2022)), and Pa$\alpha$/Br$\gamma$((cite: Engel2011)). More extreme measurements were obtained from mid-infrared diagnostics: for instance, (cite: Haas2001) reported an extinction of a few tens of magnitudes.

This suggests that NIRSpec observations may only probe the outer gaseous layers, and that the total extinction towards the core of these dusty regions can be much higher than $A_V \sim 10-14$.

## Electron density

We derived the electron density in the line-emitting regions surrounding the E, W, and NE regions of Arp 220 via the comparison of observed line strength ratios of \[Fe \] transitions with theoretical values.

We used the ratio \[Fe \] 1.677 $\mu$m/1.644 $\mu$m to infer electron densities in the range log n$_e$ $\approx 3.5- 4.5$ cm$^{-3}$ for the three regions of interest (from Eq. 6 in (cite: Koo2016)). For the two nuclei, for which two kinematic components are required to fit the total profiles, we consider the narrow components (as the broad one is undetected in the faint \[Fe \] 1.677 $\mu$m). These measurements, reported in Table [\[tab:properties\]](#tab:properties), are discussed in the context of previous measurements in Sect. [5.2](#sec:density_discussion).

![image]({images/Arp220_nuclearspectra_fit_linesPaa_b2._4paper.pdf}) ![image]({images/Arp220_nuclearspectra_fit_linesFe2_1644_b1._4paper.pdf}) ![image]({images/Arp220_nuclearspectra_fit_linesH2_2.120_b2._4paper.pdf})

## Nuclear outflows

A distinctive feature of Arp 220’s nuclear environment is the presence of powerful and complex outflows. Compact and collimated cold molecular outflows, with velocities of a few 100s km s$^{-1}$, a bipolar morphology and an extension of $\sim 120$ pc, are observed in both nuclei (e.g. (cite: Wheeler2020)). Broader line profiles are instead observed in the ionized and atomic gas: for instance, (cite: Perna2021) reported $W80$ velocities (defined as the difference between the 90th- and 10th-percentile velocities of the fitted line profile) of $\sim 800$ km s$^{-1}$. However, these measurements have been obtained from observations at lower spatial resolution ($\sim 200$ pc), and likely cannot be used to properly resolve the outflow kinematics on smaller scales.

Figure [3](#fig:outflows) shows the integrated spectra in the vicinity of the Pa$\alpha$(top), \[Fe \] 1.644 $\mu$m (centre), and H$_2$ 2.12$\mu$m (bottom) lines for the three regions of interest. The NE cluster shows symmetric and narrow profiles; conversely, broad and asymmetric (preferentially blue-shifted) line shapes are observed in both nuclear regions, with outflowing gas at velocities up to $-500$ km s$^{-1}$. In this work, we consider as outflow velocity $v_{max} = \Delta V_{broad} + 2\sigma_{broad}$, where $\sigma_{broad}$ is corrected for instrumental resolution (e.g. (cite: Fluetsch2021)). In Table [\[tab:kinematics\]](#tab:kinematics) we report the best-fit kinematic parameters, considering both non-parametric (e.g. $W80$), and parametric outflow velocity measurements (e.g. $v_{max}$; see caption of Table [\[tab:kinematics\]](#tab:kinematics) for details).

A more detailed discussion about the presence of AGN winds possibly responsible for the broad and asymmetric profiles observed in the Arp 220 nuclei is presented in Sect. [5.3](#sec:outflow_discussion).

lcccc

c W nucleus\
& H & H$_2$ & \[Fe \]& \[Mg \]\
$\Delta V_1$ & $0\pm 1$ & $-1_{-4}^{+26}$ & $0_{-1}^{+2}$ & $-111\pm 3$\
FWHM$_1$ & $238\pm 2$ & $250_{-6}^{+24}$ & $242_{-4}^{+6}$ & $234_{-10}^{+6}$\
$\Delta V_2$ & $-72\pm 2$ & – & $-110_{-8}^{+16}$ & –\
FWHM$_2$ & $480_{-4}^{+6}$ & – & $525_{-9}^{+24}$ & –\
$W80$ & $370 \pm 3$ & $270\pm 20$ & $380\pm 3$ & $260\pm 10$\
$V10$ & $-250 \pm 2$ & $-180\pm 15$ & $-270\pm 6$ & $-265\pm 10$\
$V_{max}$ & $-480_{-4}^{+9}$ & $-220_{-3}^{+30}$ & $-560\pm 25$ & $-309\pm 8$\

\
c E nucleus\
& H & H$_2$ & \[Fe \]& \[Mg \]\
$\Delta V_1$ & $0_{-2}^{+10}$ & $-40\pm 5$ & $-8_{-3}^{+8}$ & $-130_{-8}^{+14}$\
FWHM$_1$ & $205_{-27}^{+9}$ & $230 \pm 3$ & $180_{-70}^{+45}$ & $370_{-14}^{+20}$\
$\Delta V_2$ & $-70_{-10}^{+60}$ & $-201_{-7}^{+13}$ & $-60\pm 30$ & –\
FWHM$_2$ & $425_{-60}^{+50}$ & $405\pm 10$ & $420_{-60}^{+120}$ & –\
$W80$ & $370 \pm 30$ & $440\pm 50$ & $380\pm 42$ & $400\pm 30$\
$V10$ & $-250 \pm 20$ & $-370\pm 30$ & $-250 \pm 42$ & $-370\pm 20$\
$V_{max}$ & $-430_{-45}^{+70}$ & $-540_{-10}^{+20}$ & $-430_{-90}^{+140}$ & $-440\pm 20$\

\
c NE cluster\
& H & H$_2$ & \[Fe \]& \[Mg \]\
$\Delta V_1$ & $0_{-3}^{+4}$ & $-40\pm 5$ & $-14_{-8}^{+7}$ & $-81_{-3}^{+6}$\
FWHM$_1$ & $260_{-3}^{+30}$ & $225_{-60}^{+10}$ & $210\pm 30$ & $260\pm 10$\
$\Delta V_2$ & – & – & $11_{-6}^{+33}$ & –\
FWHM$_2$ & – & – & $340_{-40}^{+170}$ & –\
$W80$ & $250\pm 10$ & $270_{-50}^{+10}$ & $290\pm 40$ & $305\pm 40$\
$V10$ & $-160\pm 10$ & $-180_{-30}^{+10}$ & $-170\pm 30$ & $-240\pm 30$\
$V_{max}$ & $-230_{-3}^{+25}$ & $-230_{-60}^{+10}$ & $-190\pm 20$ & $-300\pm 6$\

\
c NW outflow\
& H & H$_2$ & \[Fe \]& \[Mg \]\
$\Delta V_1$ & $-175_{-10}^{+30}$ & $-180_{-7}^{+16}$ & $-290_{-10}^{+15}$ &-\
FWHM$_1$ & $130_{-20}^{+80}$ & $80_{-45}^{+20}$ & $640_{-30}^{+50}$ &-\
$\Delta V_2$ & $-340_{-30}^{+40}$ & $-260_{-30}^{+70}$ & – &–\
FWHM$_2$ & $650_{-50}^{+105}$ & $650_{-70}^{+60}$ &– &–\
$\Delta V_3$ & – & $85_{-6}^{+11}$ &– &–\
FWHM$_3$ & – & $210_{-30}^{+50}$ &– &–\
$W80$ & $680_{-30}^{+90}$& $715\pm 10$ & $715\pm 40$ &–\
$v10$ & $-690\pm 30$& $-590\pm 15$ & $-670 \pm 35$ &–\
$v_{max}$ & $-890_{-45}^{+130}$ & $-820\pm 35$ & $-810_{-45}^{+120}$ &–\

Notes: all kinematic parameters are given in km s$^{-1}$. Velocity shifts $\Delta V_i$ and line widths FWHM$_i$ refer to the individual Gaussian components ($i =$ 1 to 3, at maximum) required to model the emission line profiles. $V10$ is defined as 10th-percentile velocity of the fitted line profile, while $W80$ is defined as the difference between the 90th- and 10th-percentiles. $v_{max}$ is defined as $\Delta V_{broad} + 2\sigma_{broad}$.

# Discussion

We used the aperture-extracted spectra of the obscured nuclei E and W and the bright cluster NE to identify all gas emission line features in the NIRSpec spectral range, as well as the main absorption features due to dust and stars. We identified $\sim 70$ ionised gas and $\sim 50$ molecular emission lines; Tables [\[tab:linelist\]](#tab:linelist), [\[tab:linelist2\]](#tab:linelist2), and [\[tab:linelist3\]](#tab:linelist3) give the (vacuum) wavelengths and fluxes for all the firmly identified features in Arp220, while Table [\[tab:kinematics\]](#tab:kinematics) displays the kinematic parameters of the main optical lines discussed in this paper. We note that a few well detected emission lines are not tabulated, as (i) their modelling would require detailed deblending from other lines, or (ii) their observed wavelengths are very close to the edges of the NIRSpec detector gaps.

In this section we discuss the main spectral features observed in the spectra reported in Fig. [2](#fig:totalspectra) in relation with the possible presence of intense episodes of starburst activity and AGN accretion in the two nuclei.

## Star-formation tracers

We derived the instantaneous ($\sim 10$ Myr) SFR from the Pa$\alpha$ dust corrected luminosity, following (cite: Gimenez2022):

$$\begin{equation}
\label{eq:SFR}
\begin{split}
SFR\ [M_\odot \ yr^{-1}] & = 4.4\times 10^{-42} \times \left( 
\frac{H\alpha}{Pa\alpha} \right)_{int} \times L(Pa\alpha)_{corr}\ [erg s^{-1}]\\ & = 3.7 \times 10^{-41} \times L(Pa\alpha)_{corr}\ [erg s^{-1}]
\end{split}
\end{equation}$$

where the dust-corrected Pa$\alpha$ luminosity can be obtained with A(Pa$\alpha$) $= k($Pa$\alpha$$)\times$ E(B-V). In deriving Eq. [\[eq:SFR\]](#eq:SFR) we assumed electron density of 10$^3$ cm$^{-3}$ (the dependence from n$_e$ is very weak) and temperature of 10$^4$ K. Moreover, for the E and W nuclear emission we consider only the narrow components (dashed blue Gaussian lines in Fig. [3](#fig:outflows)), thus excluding the contribution of outflowing material.

The use of E(B-V) inferred from Pa$\beta$/Br$\gamma$ imply dust corrections of $\sim 5-8\times$ factors for the Pa$\alpha$ flux, resulting in a SFR $\sim 0.5$ M$_{\odot}$ yr$^{-1}$ for the W nucleus, $\sim 0.2$ M$_{\odot}$ yr$^{-1}$ for the E nucleus, and $\sim 0.9$ M$_{\odot}$ yr$^{-1}$ for the NE cluster. Therefore, these three regions account for a total SFR(Pa$\alpha$) $\sim 2$ M$_{\odot}$ yr$^{-1}$. Considering the extraction regions of $\sim 0.01$ kpc$^2$, these values would be translated in star-formation surface densities $\Sigma_{SFR} \sim 20-100$ M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$.

We also use the calibration of SFR for the 3.3 $\mu$m PAH from (cite: Kim2012) to convert the measured luminosities (L(PAH) $\sim 2\times 10^{40}$ erg s$^{-1}$ for the W, L(PAH) $7\times 10^{39}$ erg s$^{-1}$ for the E, and L(PAH) $10^{40}$ erg s$^{-1}$ for NE) in L(IR), and then the (cite: Kennicutt2012)[^4] relation to derive dust-corrected SFR(PAH) in the range $\sim 1.5-3.4$ M$_{\odot}$ yr$^{-1}$(see Table [\[tab:properties\]](#tab:properties)).

In previous optical and NIR studies of Arp 220, slightly higher SFR measurements were obtained when integrating over the whole galaxy: (cite: Perna2020) reported SFR(H$\alpha$) $\lesssim 10$ M$_{\odot}$ yr$^{-1}$(using the Balmer decrement to correct for extinction), while (cite: Gimenez2022) obtained SFR(Pa$\beta$) $\sim 19$ M$_{\odot}$ yr$^{-1}$ from HST narrow-band images (using Pa$\beta$/H$\alpha$ for the dust-correction). (cite: Gimenez2022) also reported the total SFR inferred from the 24 $\mu$m luminosity, 76 M$_{\odot}$ yr$^{-1}$; this value is significantly less affected by dust (A$_V \sim 90$ would imply a correction of a factor 2 at 24 $\mu$m). This value is more consistent with the total SFR(PAH) $\sim 40$ M$_{\odot}$ yr$^{-1}$ we measure from NIRSpec data using an integrated spectrum extracted over a very large aperture ($r = 1.5\ensuremath{''}$, i.e. 0.56 kpc).

Therefore, our NIRSpec-based outcomes are definitely in line with previous estimates obtained from optical, NIR, and mid-infrared bands. However, it is worth noting that the SFR inferred from the radio and sub-mm/mm regime appears to be several times higher, reaching 200-250 M$_{\odot}$ yr$^{-1}$(e.g. (cite: Varenius2016; Pereira2021)). In particular, these authors reported SFR $\sim 60-80$ M$_{\odot}$ yr$^{-1}$ and $\sim 110-150$ M$_{\odot}$ yr$^{-1}$ for the E and W nuclei separately, hence significantly higher than our NIR-based nuclear measurements. This discrepancy may stem from a combination of factors: (i) The far-IR and radio emission might not be solely attributable to star formation, but could also include contributions from AGN, which are totally extinguished in the NIR. (ii) The SFR derived from FIR measurements traces the star formation history over a longer period (up to 100 Myr) compared to the Pa$\alpha$ and PAH features ($\lesssim 10$ Myr).

Summarising, the NIRSpec-based SFR measurements do not offer a solution to the existing discrepancy among various star-formation tracers identified in previous studies.

## High electron densities

The \[Fe \]-based electron densities at the position of the two nuclei and the NE cluster (log (n$_e$/cm$^{-3}$) $\sim 3.7-4.5$) consistently exceed those inferred from optical \[S \] 6718, 32 $\AA$ lines, which are of the order of 200 cm$^{-3}$ ((cite: Perna2020)). This suggests that \[Fe \] lines, having critical densities higher than \[S \](n$_{\rm crit}\sim 1600$ cm$^{-3}$ for \[S \] 6716 $\AA$; n$_{\rm crit}\sim 10^4$ cm$^{-3}$ for iron lines), trace post-shock regions with higher compression. An alternative explanation might be that the higher spatial resolution of NIRSpec data ($\sim 0.1\ensuremath{''}$ at the wavelengths of the n$_e$-sensitive \[Fe \] lines) compared to the MUSE observations ($\sim 0.6\ensuremath{''}$) enables a better isolation of regions with higher degree of ionisation.

At higher redshift (up to $z\sim 9$), \[S \] and \[O \] 3727, 30 $\AA$ line ratios are systematically used to measure the ISM electron densities; values in the range $\sim 300-1000$ cm$^{-3}$ are generally reported for both AGN (e.g. (cite: Perna2017b; Cresci2023)) and star-forming galaxies (e.g. (cite: Schreiber2019; Davies2021; RodriguezdelPino2023; Isobe2023)). Significant correlations between $\Sigma_{SFR}$ and n$_e$ have been reported in the literature (e.g. (cite: Shimakawa2015)), although they cover relatively narrow ranges in both $\Sigma_{SFR}$ ($\sim$ 0.1 – 1 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$) and n$_e$ ($\sim$ 10 – 10$^3$ cm$^{-3}$). From the extrapolation of these relations (e.g. Eq. 3 in (cite: Reddy2023)) to the very high $\Sigma_{SFR}$ measured in Arp 220 (see Sect. [5.1](#sec:SFR)), we would expect log(n$_e$/cm$^{-3}$) $\sim 3$. However, this value stands roughly 30 times lower than the one measured at the position of the Arp 220 W nucleus using \[Fe \] lines. Instead, our measurements more closely resemble electron densities observed in supernova remnants (e.g., (cite: Lee2017)) and at the bases of protostar jets (e.g., (cite: Davis2011)), with \[Fe \]-based densities spanning log (n$_e$/cm$^{-3}$) $\approx 3.5-4.5$.

Therefore, on the basis of available information, we cannot discriminate between the two above mentioned scenarios: the extremely high electron densities we measured in the nuclei and the NE cluster could be due to

higher levels of compression and/or ionisation with respect to \[S \] gas emitting in the optical. We can definitely exclude any potential contamination from high-density AGN Broad Line Region (BLR) in the \[Fe \]-based electron densities obtained for the Arp 220 nuclei, as the forbidden \[Fe \] line transitions cannot originate from BLR high-density regions ($N_{\rm e} ({\rm BLR}) \gg  N_c$(\[Fe \])).

## Presence of multi-phase outflows

The NIRSpec nuclear spectra of Arp220 show ionised and molecular gas transitions with broad profiles and prominent blue wings associated with outflows. In particular, high-velocity components are detected in Pa$\alpha$ and \[Fe \] 1.644 $\mu$m at the position of the E and W nuclei. Prominent H$_2$ blue wings are solely observed in the E nucleus. This suggests that the high-velocity gas in the W nucleus is sufficiently hot (because of shocks, or intense ultraviolet radiation by hot stars or AGN) to disassociate the H$_2$ molecules.

The nuclear material can reach velocities of up to $v_{max} \sim 550$ km s$^{-1}$(Fig. [3](#fig:outflows)). We anticipate here that such outflows reach distances of $\sim 1$ kpc and velocities of $-900$ km s$^{-1}$ in the off-nuclear regions covered by NIRSpec (Ulivi et al., in prep.). Figure [4](#fig:fastoutflow) shows the Pa$\alpha$ and H$_2$ 2.12 $\mu$m line profiles extracted from a circular aperture of $r = 0.15\ensuremath{''}$ at a distance of $\sim 1.3\ensuremath{''}$ to the west from the W nucleus, as defined in Fig. [1](#fig:fig1) (cyan diamond); at this position, both ionised and molecular gas have outflow velocities up to $900$ km s$^{-1}$(Table [\[tab:kinematics\]](#tab:kinematics)). Similar velocities have also been observed in the ionised and atomic gas phases at kpc-scales in the optical regime (e.g. (cite: Perna2020)).

Nuclear outflows in NIR H , H$_2$ and iron lines have been observed in nearby ULIRGs and active galaxies. While sources lacking an active SMBH typically exhibit less extreme outflow velocities (on the order of a few hundred km s$^{-1}$), AGN can manifest outflows across a broad velocity range, from a few hundred to over a thousand km s$^{-1}$(e.g. (cite: Emonts2017; Perna2021; Speranza2022; Villar2023)). Consequently, distinguishing between starburst- and AGN-driven outflows in Arp 220, based solely on velocity estimates, proves to be a challenging task. A more comprehensive analysis of the multi-phase and multi-scale outflows will be necessary to elucidate whether the outflow energetics in Arp 220 are more consistent with AGN or starburst launching mechanisms; this work will be presented in a forthcoming paper, Ulivi et al., in prep..

![image]({images/Arp220_nuclearspectra_fit_outflow_linesPaa_b2._4paper.pdf}) ![image]({images/Arp220_nuclearspectra_fit_outflow_linesH2_2.120_b2._4paper.pdf})

## Absence of high-ionisation lines

High excitation emission lines with ionisation potentials IP $> 54$ eV (the He$^+$ ionisation energy) can be formed either in gas photoionised by hard ultraviolet radiation or in very hot, collisionally ionised plasma. Therefore, they can be used as sign for AGN activity (e.g. (cite: Oliva1994; Moorwood1997)).

Most of these highly ionised lines have previously been identified in ground-based (e.g. (cite: RodriguezArdila2011; Lamperti2017; Cerqueira2021; denBrok2022)) and space-based (e.g. (cite: Lutz2000; Sturm2002)) NIR spectra of some nearby Seyfert galaxies (Table [1](#tab:highion)). No quantitative studies of the coronal lines prevalence in the AGN population have been made yet; however, there are indications for a more likely presence of such lines in unobscured type-1 sources rather than in obscured sources. This is consistent with the fact that some coronal lines have been recently detected with NIRSpec in the nearby Seyfert 1.5 nucleus of NGC7469 ((cite: Bianchin2023)) but not in the highly obscured active nuclei of VV114 (see Appendix [8](#sec:app2); but see also (cite: Speranza2022; Alvarez2023)). The lack of high ionisation lines in AGN sources may reflect an AGN ionising continuum lacking photons below a few keV: this could explain the absence of such line emission in obscured sources (e.g. (cite: RodriguezArdila2011)).

High ionisation lines are not detected in the nuclear spectra of Arp 220. However, we note the presence of a bright feature near $\sim 4.488\mu$m, hence close to expected wavelength of the \[Mg \] line (IP $\sim 80$ eV). Previous studies reported the detection of the \[Mg \] line in a few nearby active galaxies alongside other highly ionised species; for instance, (cite: Sturm2002) reported \[Mg \]/\[Ar \] $\sim 0.5$ in Circinus and NGC1068; (cite: Bianchin2023) obtained \[Mg \]/\[Ar \] $\sim 1.5$. Notably, \[Ar \] is not detected in Arp 220. Given its similar IP to \[Mg \](see Table [1](#tab:highion)), the observed feature at the expected wavelength of \[Mg \] may involve alternative transitions. For instance, the low-ionisation line SI ($\lambda 4.4855$ in vacuum, IP $\sim 10$ eV) could be responsible of the line features in the Arp 220 spectra.

Figure [5](#fig:mgiv) shows the emission line at the wavelength position of the \[Mg \] in the three spectra of interest: these features are broad (FWHM $\sim 300$ km s$^{-1}$) and blue-shifted ($\Delta V\sim -100$ km s$^{-1}$) with respect to the \[Mg \] expected wavelength (grey solid line at $v=0$ km/s). Moreover, their peaks are not at the systemic of the SI transition neither. Pereira-Santaella et al. (subm.) show that this feature can be associated with shocked \[Mg \] emission due to supernova explosions. In support of this explanation we note that this line feature is bright at the position of intense clusters in Arp 220, but it is faint in the surroundings of the two nuclei.

In Table [1](#tab:highion), we report the main high ionisation lines in the range covered by our NIRSpec spectra; for all but \[Mg \] we report the $3\sigma$ upper limits inferred from NIRSpec data. These upper limits, and in particular the \[Si \] one, can be used to compare the NIRSpec measurements with those from the literature. In fact, \[Si \] is detected in the largest number of AGN spectra ((cite: Lamperti2017; denBrok2022)).

Figure [6](#fig:SiVI), top panel, shows the distribution of L(\[Si \]) as a function of the redshift for a sample of nearby active galaxies selected in the hard X-ray band (14-195 keV) from the *Swift*/Burst Alert Telescope (BAT) survey, as part of the BASS sample ((cite: Koss2017; Ricci2017)). We display both \[Si \] detections and 3$\sigma$ upper limits, alongside the Arp 220 non detections. It is evident that NIRSpec enables us to obtain more stringent upper limits compared to previous observations of other systems at $z \sim 0.018$ (by $\sim 1$ dex).

Figure [6](#fig:SiVI), bottom panel, shows the correlation between intrinsic X-ray and \[Si \] luminosity (e.g. (cite: RodriguezArdila2011; Lamperti2017)) for the same sources. The upper limits for \[Si \] in Arp 220 nuclei are indicated at the intrinsic X-ray (2–10 keV) luminosities of $<1\times 10^{42}$ erg s$^{-1}$(W) and $<4\times 10^{41}$ erg s$^{-1}$(E), computed by (cite: Paggi2017) from the $3\sigma$ upper limits on the neutral Fe–K$\alpha$ line.

The Arp 220 \[Si \] upper limits are approximately 1 dex below the L(\[Si \]) – L$_{\rm 2-10 \ keV}$ relation (dashed magenta line). However, it should be noted that measuring intrinsic X-ray luminosity for highly obscured sources can be highly uncertain, and that the Arp 220 X-ray luminosities are merely upper limits. Consequently, it is possible that the nuclei of Arp 220 may not exhibit notable distinctions from other AGN with undetected \[Si \] reported in the figure, for which the presence of accreting SMBHs is confirmed in the hard X-ray band.

To conclude, there is no obvious highly ionised line emission associated with AGN from either nucleus of Arp 220, despite the many bright H , He , H$_2$, and low excitation \[Fe \] lines detected at very high signal-to-noise. Moreover, the very stringent upper limits derived from NIRSpec observations cannot be used to discard the presence of AGN in Arp 220 nuclei when we take into account the extremely high nuclear extinction (Sect. [4.3](#sec:extinction)).

|           |                 |      |               |                     |
|:----------|:---------------:|:----:|:--------------|:-------------------:|
| line      | $\lambda_{vac}$ |  IP  | ref           |   log $L_{line}$    |
|           |    ($\mu$m)     | (eV) |               |   (erg s$^{-1}$)    |
| (1)       |       (2)       | (3)  | (4)           |         (5)         |
| $[$S \]   |     0.9916      | 281  | L17, C21      |       $<$37.0       |
| Cr        |     1.0109      | 160  |               |       $<$36.9       |
| $[$Fe \]  |     1.0750      | 331  | L17, C21      |       $<$37.0       |
| $[$Fe \]  |     1.0801      | 331  | L17, C21      |       $<$37.0       |
| $[$S \]   |     1.2523      | 329  | B23, C21      |       $<$36.9       |
| $[$Si \]  |     1.4305      | 351  | C21           |          –          |
| Ti        |     1.7156      |  99  |               |       $<$37.3       |
| $[$S \]   |     1.9201      | 448  | L17, C21      |       $<$37.1       |
| $[$Si \]  |     1.9327      | 401  | L17, C21      |       $<$37.1       |
|           |     1.9646      | 167  | L17, C21, B23 |       $<$37.1       |
| $[$Al \]  |     2.0450      | 285  | C21           |       $<$37.1       |
| Sc        |     2.3118      |  73  |               |       $<$37.0       |
| $[$Ca \]  |     2.3211      | 127  | C21,R06       |       $<$37.0       |
| $[$Si \]  |     2.4810      | 205  | B23           |       $<$37.0       |
| $[$Si $]$ |     2.5850      | 303  | S02, L00      |       $<$37.1       |
| Al        |     2.9050      | 120  |               |       $<$37.0       |
| $[$Mg $]$ |     3.0280      | 225  | S02,B23, L00  |       $<$37.0       |
| $[$Ca \]  |     3.2070      |  51  | L00           |       $<$36.7       |
| $[$Al \]  |     3.6603      | 154  |               |       $<$36.9       |
| $[$Al $]$ |     3.6900      | 242  |               |       $<$36.9       |
| $[$Si \]  |     3.9290      | 303  | S02, L00      |       $<$37.0       |
| $[$Ca \]  |     4.1585      |  67  |               |       $<$37.0       |
|           |     4.4880      |  80  | S02, B23, L00 | $38.03\pm 0.01$ (W) |
|           |                 |      |               | $37.72\pm 0.02$ (E) |
|           |     4.5292      |  75  | B23, L00      |       $<$37.0       |

: High ionisation lines

Notes: references of papers reporting the detection of high ionisation lines: (cite: Sturm2002), (cite: Lamperti2017), (cite: Bianchin2023), (cite: Cerqueira2021), (cite: Lutz2000). \[Mg \] luminosities are reported for both E and W nuclei; for all other high ionisation lines we report 3$\sigma$ upper limits for the luminosities, assuming FWHM $= 250$ km s$^{-1}$. \[Si \] is not covered by NIRSpec observations (it falls in detector gap).

![]({images/Arp220_nuclearspectra_fit_linesmgiv_b3._4paper.pdf})

![]({images/SiVIplots.pdf})

## Near-infrared emission line diagnostic diagrams

We used the diagnostic diagrams presented by (cite: Riffel2013), (cite: Colina2015), and (cite: Calabro2023), to investigate the ionisation mechanisms responsible of the emission line ratios observed in the nuclei and the NE cluster. Prior to analysis, all fluxes required for the diagnostics were corrected for dust extinction, using the $A_V$ values reported in Table [\[tab:properties\]](#tab:properties).

According to the diagram presented by (cite: Riffel2013), based on the H$_2$ 2.12$\mu$m/Br$\gamma$ vs. \[Fe \] 1.26$\mu$m/Pa$\beta$ line ratios, both nuclei and the NE cluster are in the AGN region; the NE cluster has slightly lower line ratios and it is therefore closer to the ‘star-forming’ region of the diagram. In the diagram proposed by (cite: Colina2015), based on the H$_2$ 2.12$\mu$m/Br$\gamma$ vs. \[Fe \] 1.64$\mu$m/Br$\gamma$, the two nuclei and NE cluster are in the region dominated by AGN and supernovae.

Therefore, a similar ionisation mechanism should be present in the W, E, and NE regions of Arp 220 according to both (cite: Riffel2013) and (cite: Colina2015).

We also explored the diagnostic diagram recently proposed by (cite: Calabro2023), that use combinations of ratios of the \[S \], \[Fe \], \[P \] and \[C \] lines over hydrogen recombination lines. In all the diagrams, the two nuclei are slightly above the maximum starburst line (by 0.1 – 0.5 dex). The NE clump lies on (or just below) the maximum starburst line. We note that the two nuclei are well above the maximum starburst line in the \[C \]/Pa$\beta$ diagram, compatible with both AGN and shock ionisations (cite: Calabro2023).

In summary, these diagnostics do not allow us to distinguish between supernovae and AGN ionisation mechanisms.

More detailed investigations of the flux ratios in the circum-nuclear region of Arp 220 will be presented in a future work.

# Conclusions

This paper provides an overview of the JWST/NIRSpec IFS observations of Arp 220. It introduces the data reduction, and the continuum and emission line data modelling. It shows the near-infrared spectra of the E and W nuclei, in comparison with that of a bright stellar cluster at $\sim 0.4\ensuremath{''}$ (0.15 kpc) north-east from the E nucleus. These spectra are extracted using circular apertures of radius 55 pc (0.15$''$) for each region. In the following, we summarise our main findings.

We identify broadening and multiple kinematic components in H , H$_2$ and \[Fe \] lines caused by outflows (Fig. [3](#fig:outflows)). The emission line features show maximum velocities of up to $\sim 550$ km s$^{-1}$ in the nuclear spectra. Even higher velocities ($\sim 900$ km s$^{-1}$) are detected in the off-nuclear regions (Fig. [4](#fig:fastoutflow)). However, they do not conclusively represent a direct evidence of AGN activity. A companion paper will report the spatially resolved gas kinematics, and the outflow energetics will be used to test the theoretical predictions for both starburst- and AGN-driven winds (Ulivi et al., in prep.).

High ionisation lines associated with AGN activity are not detected in the nuclear spectra of Arp 220. We observe the presence of bright \[Mg \] 4.488 $\mu$m lines (80 eV) in the two nuclear spectra and the NE stellar cluster (Fig. [5](#fig:mgiv)). However, no other high ionisation lines are detected; in particular the \[Ar \] 4.529 $\mu$m line, which has an IP and wavelength close to those of \[Mg \], is not detected. The \[Mg \] lines are broader (FWHM $\sim 300$ km s$^{-1}$) and blue-shifted ($\Delta V \sim -100$ km s$^{-1}$) compared to those of the H  lines; moreover, \[Mg \] is bright at the position of clusters, but it is faint in the surroundings of the two nuclei. These arguments suggest that this emission line is not produced by an AGN, but rather due to stellar activity. This result is in line with recent findings of Pereira-Santaella et al. (subm.), who recently reported the presence of \[Mg \] in other nearby ULIRGs not hosting accreting SMBHs, with kinematic properties similar to those in Arp 220; they also provided grids of photoionization and shock models to determine the conditions where \[Mg \] originates, concluding that shocks by supernova explosions can explain the observed \[Mg \] lines.

The luminosity upper limits inferred for the high ionisation (IP $= 167$ eV) \[Si \] emission line at the position of the Arp 220 nuclei are $\sim 1$ dex below the L(\[Si \]) – L$_{2-10\ keV, int}$ observed for X-ray AGN ((cite: RodriguezArdila2011; Lamperti2017)), but still broadly consistent with other sources hosting accreting SMBHs but missing \[Si \] emission (Fig. [6](#fig:SiVI)).

We also report the presence of high excitation $^{12}$CO gas transitions (up to J$_{low} = 23$) in the Arp 220 nuclei (Fig. [13](#fig:portion6)), possibly due to AGN activity (e.g. (cite: GonzalezAlfonso2023)). A companion paper (Buiten et al., in prep.) will provide detailed modelling of CO gas conditions to assess which mechanism among star formation and AGN contributes to the observed high excitation CO lines.

To conclude, an unambiguous identification of the presence of AGN in the Arp 220 system remains elusive. At the same time, we cannot exclude the presence of accreting SMBHs, because of the extremely high extinction measured at the position of the two nuclei, with recombination lines-based A$_V\sim 11-14$. NIRSpec observations may only probe the outer gaseous layers, and the total extinction towards the core of the Arp 220 nuclear regions could be much higher (see e.g. (cite: Haas2001; Sakamoto2021a)). This could explain the absence of highly ionised gas transitions, as also reported in previous works on obscured AGN (e.g. (cite: RodriguezArdila2011; Lamperti2017)).

# Acknowledgements

We are grateful to Paul van der Werf, Victorine Buiten, and Angèle Taillard for discussing various aspects of this work

MP, SA, and BRP acknowledge support from the research project PID2021-127718NB-I00 of the Spanish Ministry of Science and Innovation/State Agency of Research (MCIN/AEI/10.13039/501100011033). IL acknowledges support from PID2022-140483NB-C22 funded by AEI 10.13039/501100011033 and BDC 20221289 funded by MCIN by the Recovery, Transformation and Resilience Plan from the Spanish State, and by NextGenerationEU from the European Union through the Recovery and Resilience Facility. MPS acknowledges support from grant RYC2021-033094-I funded by MICIU/AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR. RM acknowledges support by the Science and Technology Facilities Council (STFC), by the ERC Advanced Grant 695671 “QUENCH”, and by the UKRI Frontier Research grant RISEandFALL; RM is further supported by a research professorship from the Royal Society.

GC, MP, and LU acknowledge the support of the INAF Large Grant 2022 "The metal circle: a new sharp view of the baryon cycle up to Cosmic Dawn with the latest generation IFU facilities".

95 natexlab

(ref: Alvarez2023) Álvarez-Márquez, J., Labiano, A., Guillard, P., et al. 2023, A&A, 672, A108

(ref: Armus2007) Armus, L., Charmandaris, V., Bernard-Salas, J., et al. 2007, ApJ, 656, 148

(ref: Arp1966) Arp, H. 1966, ApJS, 14, 1

(ref: Arribas2001) Arribas, S., Colina, L., & Clements, D. 2001, ApJ, 560, 160

(ref: Baan1995) Baan, W. A. & Haschick, A. D. 1995, ApJ, 454, 745

(ref: Baba2022) Baba, S., Imanishi, M., Izumi, T., et al. 2022, ApJ, 928, 184

(ref: BarcosMunoz2015) Barcos-Muñoz, L., Leroy, A. K., Evans, A. S., et al. 2015, ApJ, 799, 10

(ref: Bennett2014) Bennett, C. L., Larson, D., Weiland, J. L., & Hinshaw, G. 2014, ApJ, 794, 135

(ref: Bianchin2023) Bianchin, M., U, V., Song, Y., et al. 2023, arXiv e-prints, arXiv:2308.00209

(ref: Boker2022) Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82

(ref: Boker2023) Böker, T., Beck, T. L., Birkmann, S. M., et al. 2023, PASP, 135, 038001

(ref: Buiten2023) Buiten, V. A., van der Werf, P. P., Viti, S., et al. 2023, arXiv e-prints, arXiv:2312.01945

(ref: Calabro2023) Calabrò, A., Pentericci, L., Feltre, A., et al. 2023, A&A, 679, A80

(ref: Cappellari2017) Cappellari, M. 2017, MNRAS, 466, 798

(ref: Cardelli1989) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245

(ref: Cerqueira2021) Cerqueira-Campos, F. C., Rodrı́guez-Ardila, A., Riffel, R., et al. 2021, MNRAS, 500, 2666

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Chandar2023) Chandar, R., Caputo, M., Linden, S., et al. 2023, ApJ, 943, 142

(ref: Colina2004) Colina, L., Arribas, S., & Clements, D. 2004, ApJ, 602, 181

(ref: Colina2015) Colina, L., Piqueras López, J., Arribas, S., et al. 2015, A&A, 578, A48

(ref: Cresci2023) Cresci, G., Tozzi, G., Perna, M., et al. 2023, arXiv e-prints, arXiv:2301.11060

(ref: Davies2021) Davies, R. L., Förster Schreiber, N. M., Genzel, R., et al. 2021, ApJ, 909, 78

(ref: Davis2011) Davis, C. J., Cervantes, B., Nisini, B., et al. 2011, A&A, 528, A3

(ref: denBrok2022) den Brok, J. S., Koss, M. J., Trakhtenbrot, B., et al. 2022, ApJS, 261, 7

(ref: DEugenio2023) D’Eugenio, F., Perez-Gonzalez, P., Maiolino, R., et al. 2023, arXiv e-prints, arXiv:2308.06317

(ref: Donnan2024) Donnan, F. R., Garcı́a-Bernete, I., Rigopoulou, D., et al. 2024, MNRAS \[\]

(ref: Emonts2017) Emonts, B. H. C., Colina, L., Piqueras-López, J., et al. 2017, A&A, 607, A116

(ref: Engel2011) Engel, H., Davies, R. I., Genzel, R., et al. 2011, ApJ, 729, 58

(ref: Eriksen2009) Eriksen, K. A., Arnett, D., McCarthy, D. W., & Young, P. 2009, ApJ, 697, 29

(ref: Fluetsch2021) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2021, MNRAS, 505, 5753

(ref: Schreiber2019) Förster Schreiber, N. M., Übler, H., Davies, R. L., et al. 2019, ApJ, 875, 21

(ref: GarciaBernete2024) Garcı́a-Bernete, I., Pereira-Santaella, M., González-Alfonso, E., et al. 2024, A&A, 682, L5

(ref: Gibb2004) Gibb, E. L., Whittet, D. C. B., Boogert, A. C. A., & Tielens, A. G. G. M. 2004, ApJS, 151, 35

(ref: Gimenez2022) Giménez-Arteaga, C., Brammer, G. B., Marchesini, D., et al. 2022, ApJS, 263, 17

(ref: GonzalezAlfonso2023) González-Alfonso, E., Garcı́a-Bernete, I., Pereira-Santaella, M., et al. 2023, arXiv e-prints, arXiv:2312.04914

(ref: Gustafsson2008) Gustafsson, B., Edvardsson, B., Eriksson, K., et al. 2008, A&A, 486, 951

(ref: Haas2001) Haas, M., Klaas, U., Müller, S. A. H., Chini, R., & Coulson, I. 2001, A&A, 367, L9

(ref: Isobe2023) Isobe, Y., Ouchi, M., Nakajima, K., et al. 2023, ApJ, 956, 139

(ref: Jakobsen2022) Jakobsen, P., Ferruit, P., de Oliveira, C. A., et al. 2022, A&A, 661, A80

(ref: Kennicutt2012) Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531

(ref: Kim2012) Kim, J. H., Im, M., Lee, H. M., et al. 2012, ApJ, 760, 120

(ref: Koo2016) Koo, B.-C., Raymond, J. C., & Kim, H.-J. 2016, Journal of Korean Astronomical Society, 49, 109

(ref: Koss2017) Koss, M., Trakhtenbrot, B., Ricci, C., et al. 2017, ApJ, 850, 74

(ref: Lamperti2017) Lamperti, I., Koss, M., Trakhtenbrot, B., et al. 2017, MNRAS, 467, 540

(ref: Lamperti2022) Lamperti, I., Pereira-Santaella, M., Perna, M., et al. 2022, A&A, 668, A45

(ref: Law2023) Law, D. D., Morrison, J. E., Argyriou, I., et al. 2023, AJ, 166, 45

(ref: Lee2017) Lee, Y.-H., Koo, B.-C., Moon, D.-S., Burton, M. G., & Lee, J.-J. 2017, ApJ, 837, 118

(ref: Lockhart2015) Lockhart, K. E., Kewley, L. J., Lu, J. R., et al. 2015, ApJ, 810, 149

(ref: Lutz2000) Lutz, D., Sturm, E., Genzel, R., et al. 2000, ApJ, 536, 697

(ref: May2017) May, D. & Steiner, J. E. 2017, MNRAS, 469, 994

(ref: McDowell2003) McDowell, J. C., Clements, D. L., Lamb, S. A., et al. 2003, ApJ, 591, 154

(ref: Moorwood1997) Moorwood, A. F. M., Marconi, A., van der Werf, P. P., & Oliva, E. 1997, Ap&SS, 248, 113

(ref: Nardini2010) Nardini, E., Risaliti, G., Watabe, Y., Salvati, M., & Sani, E. 2010, MNRAS, 405, 2505

(ref: Oliva1995) Oliva, E., Origlia, L., Kotilainen, J. K., & Moorwood, A. F. M. 1995, A&A, 301, 55

(ref: Oliva1994) Oliva, E., Salvati, M., Moorwood, A. F. M., & Marconi, A. 1994, A&A, 288, 457

(ref: Osterbrock2006) Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei (University Science Books)

(ref: Paggi2017) Paggi, A., Fabbiano, G., Risaliti, G., et al. 2017, ApJ, 841, 44

(ref: Pereira2021) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2021, A&A, 651, A42

(ref: Pereira2024a) Pereira-Santaella, M., González-Alfonso, E., Garcı́a-Bernete, I., Garcı́a-Burillo, S., & Rigopoulou, D. 2024, A&A, 681, A117

(ref: Perna2020) Perna, M., Arribas, S., Catalán-Torrecilla, C., et al. 2020, A&A, 643, A139

(ref: Perna2023a) Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679, A89

(ref: Perna2021) Perna, M., Arribas, S., Pereira Santaella, M., et al. 2021, A&A, 646, A101

(ref: Perna2015a) Perna, M., Brusa, M., Cresci, G., et al. 2015, A&A, 574, A82

(ref: Perna2017b) Perna, M., Lanzuisi, G., Brusa, M., Cresci, G., & Mignoli, M. 2017, A&A, 606, A96

(ref: PiquerasLopez2016) Piqueras López, J., Colina, L., Arribas, S., Pereira-Santaella, M., & Alonso-Herrero, A. 2016, A&A, 590, A67

(ref: Ralchenko2005) Ralchenko, Y. 2005, Memorie della Societa Astronomica Italiana Supplementi, 8, 96

(ref: Reddy2023) Reddy, N. A., Sanders, R. L., Shapley, A. E., et al. 2023, ApJ, 951, 56

(ref: Ricci2017) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017, ApJS, 233, 17

(ref: Rich2023) Rich, J., Aalto, S., Evans, A. S., et al. 2023, ApJL, 944, L50

(ref: Riffel2013) Riffel, R., Rodrı́guez-Ardila, A., Aleman, I., et al. 2013, MNRAS, 430, 2002

(ref: Riffel2019) Riffel, R., Rodrı́guez-Ardila, A., Brotherton, M. S., et al. 2019, MNRAS, 486, 3228

(ref: Riffel2014) Riffel, R. A., Vale, T. B., Storchi-Bergmann, T., & McGregor, P. J. 2014, MNRAS, 442, 656

(ref: RodriguezArdila2011) Rodrı́guez-Ardila, A., Prieto, M. A., Portilla, J. G., & Tejeiro, J. M. 2011, ApJ, 743, 100

(ref: RodriguezdelPino2023) Rodrı́guez Del Pino, B., Perna, M., Arribas, S., et al. 2023, arXiv e-prints, arXiv:2309.14431

(ref: Rothman2021) Rothman, L. S. 2021, Nature Reviews Physics, 3, 302

(ref: Sakamoto2021a) Sakamoto, K., González-Alfonso, E., Martı́n, S., et al. 2021a, ApJ, 923, 206

(ref: Sakamoto2021b) Sakamoto, K., Martı́n, S., Wilner, D. J., et al. 2021b, ApJ, 923, 240

(ref: Schwarz1978) Schwarz, U. J. 1978, A&A, 65, 345

(ref: Scoville2007) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1

(ref: Scoville2017) Scoville, N., Murchikova, L., Walter, F., et al. 2017, ApJ, 836, 66

(ref: Scoville1998) Scoville, N. Z., Evans, A. S., Dinshaw, N., et al. 1998, ApJL, 492, L107

(ref: Shimakawa2015) Shimakawa, R., Kodama, T., Steidel, C. C., et al. 2015, MNRAS, 451, 1284

(ref: Speranza2022) Speranza, G., Ramos Almeida, C., Acosta-Pulido, J. A., et al. 2022, A&A, 665, A55

(ref: Sturm2002) Sturm, E., Lutz, D., Verma, A., et al. 2002, A&A, 393, 821

(ref: Teng2015) Teng, S. H., Rigby, J. R., Stern, D., et al. 2015, ApJ, 814, 56

(ref: Ueda2022) Ueda, J., Michiyama, T., Iono, D., Miyamoto, Y., & Saito, T. 2022, PASJ, 74, 407

(ref: Uliviinprep) Ulivi et al., . in prep., –, –,

(ref: Varenius2019) Varenius, E., Conway, J. E., Batejat, F., et al. 2019, A&A, 623, A173

(ref: Varenius2016) Varenius, E., Conway, J. E., Martı́-Vidal, I., et al. 2016, A&A, 593, A86

(ref: Vazdekis2016) Vazdekis, A., Koleva, M., Ricciardelli, E., Röck, B., & Falcón-Barroso, J. 2016, MNRAS, 463, 3409

(ref: Verro2022) Verro, K., Trager, S. C., Peletier, R. F., et al. 2022, A&A, 660, A34

(ref: Villar2023) Villar Martı́n, M., Castro-Rodrı́guez, N., Pereira Santaella, M., et al. 2023, A&A, 673, A25

(ref: Wheeler2020) Wheeler, J., Glenn, J., Rangwala, N., & Fyhrie, A. 2020, ApJ, 896, 43

(ref: YoastHull2017) Yoast-Hull, T. M., Gallagher, John S., I., Aalto, S., & Varenius, E. 2017, MNRAS, 469, L89

(ref: Yoast2019) Yoast-Hull, T. M. & Murray, N. 2019, MNRAS, 484, 3665

# NIRSpec narrow-band images

![image]({images/Arp220fig1panels.pdf})

# Integrated spectra

![]({images/Arp220_nuclearspectra_VV114_1.pdf})

![]({images/Arp220_nuclearspectra_VV114_2.pdf})

![]({images/Arp220_nuclearspectra_VV114_3.pdf})

![]({images/Arp220_nuclearspectra_VV114_4.pdf})

![]({images/Arp220_nuclearspectra_VV114_5.pdf})

![]({images/Arp220_nuclearspectra_VV114_6.pdf})

# Arp 220 emission line list (band2 and band3 cubes)

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| line | $\lambda_{vac}$ | $f_W$ | $f_E$ | $f_{NE}$ |
|  | ($\mu$m) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) |
| He  | 1.869044 | 273.0$_{-3.3}^{+6.8}$ | 62.3$_{-2.8}^{+4.7}$ | 193.0$_{-3.9}^{+5.0}$ |
| He  | 1.870234 | 112.0$_{-3.5}^{+5.8}$ | 35.1$_{-2.9}^{+4.6}$ | 36.7$_{-3.3}^{+6.3}$ |
| Pa$\alpha$ | 1.875627 | 7260.0$_{-2.9}^{+5.4}$ | 1510.0$_{-2.6}^{+2.1}$ | 6390.0$_{-4.0}^{+5.8}$ |
| H$_2$ | 1.892094 | 253.0$_{-5.0}^{+5.1}$ | 77.7$_{-11.9}^{+32.3}$ | 85.6$_{-1.0}^{+0.8}$ |
| Br$\delta$ | 1.945095 | 455.0$_{-5.7}^{+4.5}$ | 77.2$_{-2.8}^{+4.5}$ | 334.0$_{-3.2}^{+6.6}$ |
| He  | 1.954840 | 27.2$_{-1.8}^{+3.1}$ | 46.6$_{-3.1}^{+2.7}$ | 30.5$_{-2.7}^{+2.1}$ |
| H$_2$ | 1.957722 | 659.0$_{-5.4}^{+6.9}$ | 243.0$_{-45.6}^{+86.2}$ | 278.0$_{-3.3}^{+8.8}$ |
| H$_2$ | 2.033927 | 268.0$_{-3.4}^{+3.4}$ | 149.0$_{-3.4}^{+5.1}$ | 116.0$_{-3.1}^{+3.8}$ |
| He  | 2.058600 | 247.0$_{-1.3}^{+1.4}$ | 62.6$_{-0.6}^{+1.3}$ | 215.0$_{-1.1}^{+2.2}$ |
| H$_2$ | 2.065756 | 81.7$_{-0.7}^{+0.5}$ | 28.9$_{-2.0}^{+4.7}$ | 33.3$_{-4.2}^{+4.2}$ |
| H$_2$ | 2.073655 | 126.0$_{-4.6}^{+3.0}$ | 69.6$_{-3.4}^{+4.0}$ | 59.1$_{-4.3}^{+3.1}$ |
| H$_2$ | 2.122011 | 901.0$_{-5.1}^{+7.9}$ | 427.0$_{-3.6}^{+6.0}$ | 345.0$_{-5.4}^{+6.6}$ |
| Br$\gamma$ | 2.166129 | 762.0$_{-4.1}^{+5.5}$ | 156.0$_{-4.9}^{+9.2}$ | 686.0$_{-2.8}^{+5.9}$ |
| H$_2$ | 2.223475 | 263.0$_{-5.5}^{+3.4}$ | 123.0$_{-4.1}^{+4.2}$ | 100.0$_{-2.8}^{+5.5}$ |
| H$_2$ | 2.247903 | 147.0$_{-3.3}^{+2.4}$ | 76.2$_{-3.5}^{+3.0}$ | 69.6$_{-0.9}^{+1.0}$ |
| H$_2$ | 2.406793 | 1010.0$_{-5.6}^{+9.7}$ | – | – |
| H$_2$ | 2.413640 | 402.0$_{-3.9}^{+8.0}$ | – | – |
| H$_2$ | 2.423932 | 940.0$_{-4.7}^{+9.2}$ | – | – |
| H$_2$ | 2.454956 | 633$_{-3.0}^{+5.4}$ | 375$_{-4.4}^{+5.0}$ | 223$_{-3.8}^{+5.3}$ |
| H$_2$ | 2.475765 | 173.0$_{-1.8}^{+3.1}$ | 124.0$_{-4.0}^{+3.0}$ | 62.4$_{-0.8}^{+1.0}$ |
| H$_2$ | 2.500174 | 332.0$_{-2.1}^{+4.0}$ | 207.0$_{-3.1}^{+4.4}$ | 106.0$_{-2.6}^{+4.9}$ |
| H$_2$ | 2.501650 | 50.9$_{-2.4}^{+3.0}$ | 19.4$_{-2.7}^{+5.0}$ | 39.0$_{-3.1}^{+2.9}$ |
| H$_2$ | 2.528247 | 87.8$_{-1.2}^{+0.6}$ | 58.6$_{-1.7}^{+3.9}$ | 34.6$_{-1.7}^{+3.9}$ |
| H$_2$ | 2.551198 | 103.0$_{-1.6}^{+5.0}$ | 72.7$_{-1.7}^{+4.1}$ | 33.8$_{-2.9}^{+4.1}$ |
| H$_2$ | 2.558725 | 96.0$_{-2.7}^{+4.6}$ | 61.4$_{-3.7}^{+5.3}$ | 54.8$_{-1.7}^{+2.2}$ |
| H$_2$ | 2.560064 | 193.0$_{-2.6}^{+3.3}$ | 121.0$_{-2.6}^{+5.4}$ | 48.9$_{-2.1}^{+3.0}$ |
| H$_2$ | 2.570043 | 124.0$_{-2.7}^{+4.5}$ | 89.6$_{-2.7}^{+3.3}$ | 44.8$_{-2.5}^{+2.8}$ |
| H$_2$ | 2.585185 | 31.3$_{-1.6}^{+2.5}$ | 20.1$_{-3.6}^{+4.1}$ | 1.76$_{-0.7}^{+3.6}$ |
| H$_2$ | 2.604197 | 66.5$_{-2.4}^{+3.7}$ | 46.1$_{-3.0}^{+4.8}$ | 25.5$_{-3.1}^{+4.1}$ |
| Pf 14 | 2.612655 | 121.0$_{-0.1}^{+0.3}$ | 70.9$_{-2.3}^{+4.7}$ | 84.6$_{-2.2}^{+6.0}$ |
| Br$\beta$ | 2.625878 | 1840.0$_{-3.9}^{+6.2}$ | 749.0$_{-4.4}^{+6.5}$ | 1610.0$_{-4.8}^{+5.9}$ |
| H$_2$ | 2.635329 | 103.0$_{-3.0}^{+2.9}$ | 89.8$_{-3.2}^{+4.0}$ | 45.8$_{-3.8}^{+3.5}$ |
| H$_2$ | 2.654084 | 80.5$_{-4.3}^{+3.1}$ | 65.1$_{-2.6}^{+3.7}$ | 24.2$_{-1.6}^{+5.8}$ |
| Pf 13 | 2.675139 | 58.9$_{-6.0}^{+5.1}$ | 17.1$_{-3.5}^{+4.0}$ | 51.4$_{-2.5}^{+6.4}$ |
| H$_2$ | 2.710478 | 48.9$_{-3.0}^{+0.4}$ | 19.7$_{-1.4}^{+5.4}$ | 12.7$_{-2.7}^{+3.6}$ |
| H$_2$ | 2.718847 | 1.19$_{-0.004}^{+0.006}$ | 2.29$_{-0.74}^{+5.5}$ | 4.55$_{-2.2}^{+1.6}$ |
| H$_2$ | 2.720371 | 103.0$_{-0.94}^{+2.4}$ | 81.3$_{-2.2}^{+4.9}$ | 26.4$_{-1.9}^{+3.7}$ |
| H$_2$ | 2.726984 | 87.1$_{-2.6}^{+1.0}$ | 59.6$_{-1.5}^{+3.4}$ | 33.2$_{-1.5}^{+3.0}$ |
| H$_2$ | 2.731438 | 17.3$_{-2.6}^{+5.4}$ | 10.0$_{-2.1}^{+2.9}$ | 14.8$_{-1.6}^{+3.6}$ |
| H$_2$ | 2.748299 | 32.0$_{-3.4}^{+4.0}$ | 20.3$_{-2.8}^{+3.4}$ | 11.2$_{-3.9}^{+2.5}$ |
| Pf 12 | 2.758276 | 110.0$_{-1.9}^{+6.3}$ | 48.0$_{-2.7}^{+4.6}$ | 109.0$_{-3.0}^{+4.3}$ |
| H$_2$ | 2.786396 | 12.5$_{-2.0}^{+4.4}$ | 13.6$_{-2.8}^{+4.0}$ | 6.99$_{-2.4}^{+3.7}$ |
| H$_2$ | 2.802750 | 601.0$_{-3.8}^{+3.6}$ | 313.0$_{-1.3}^{+4.3}$ | 244.0$_{-1.7}^{+3.2}$ |
| H$_2$ | 2.804052 | 1.25$_{-0.004}^{+0.007}$ | 1.41$_{-0.02}^{+0.03}$ | 1.08$_{-0.01}^{+0.01}$ |
| Pf 11 | 2.873004 | 58.7$_{-2.4}^{+5.7}$ | 8.35$_{-1.8}^{+3.2}$ | 74.4$_{-2.6}^{+3.5}$ |
| H$_2$ | 2.974311 | 54.0$_{-2.5}^{+2.5}$ | 22.7$_{-2.4}^{+2.7}$ | 27.2$_{-2.2}^{+2.9}$ |
| H$_2$ | 3.004118 | 132.0$_{-2.8}^{+3.7}$ | 48.5$_{-2.1}^{+2.7}$ | 53.5$_{-1.9}^{+3.5}$ |
| Pf$\epsilon$ | 3.039211 | 128.0$_{-2.9}^{+7.3}$ | 21.3$_{-4.1}^{+3.5}$ | 110.0$_{-3.3}^{+6.6}$ |

Notes: This list comprises all emission lines detected in band2; see Tables [\[tab:linelist\]](#tab:linelist) and [\[tab:linelist3\]](#tab:linelist3) for those in band1 and band3, respectively. The reported fluxes are obtained from single Gaussian fits, without dust- and aperture-corrections.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| line | $\lambda_{vac}$ | $f_W$ | $f_E$ | $f_{NE}$ |
|  | ($\mu$m) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) | ($10^{-18}$ erg s$^{-1}$ cm$^{-2}$) |
| H$_2$ | 3.164034 | 15.2$_{-2.4}^{+2.1}$ | 8.13$_{-1.6}^{+2.0}$ | 13.4$_{-2.3}^{+3.0}$ |
| H$_2$ | 3.190077 | 28.2$_{-1.8}^{+2.4}$ | 13.4$_{-1.4}^{+1.1}$ | 11.9$_{-2.2}^{+2.6}$ |
| H$_2$ | 3.235257 | 310.0$_{-2.2}^{+3.3}$ | 117.0$_{-1.1}^{+2.8}$ | 117.0$_{-2.2}^{+2.2}$ |
| Pf$\delta$ | 3.297001 | 409.0$_{-0.6}^{+0.8}$ | 74.3$_{-3.5}^{+5.5}$ | 293.0$_{-2.3}^{+1.7}$ |
| H$_2$ | 3.626469 | 152.0$_{-2.7}^{+3.5}$ | 70.4$_{-1.6}^{+2.5}$ | 47.6$_{-1.4}^{+4.1}$ |
| H$_2$ | 3.663464 | 23.2$_{-2.6}^{+2.8}$ | 29.0$_{-1.7}^{+1.9}$ | 12.2$_{-1.0}^{+3.2}$ |
| Hu 18 | 3.692642 | 30.2$_{-1.6}^{+2.3}$ | 9.63$_{-0.8}^{+2.1}$ | 23.5$_{-1.9}^{+2.8}$ |
| H$_2$ | 3.723999 | 5.49$_{-4.7}^{+4.8}$ | 0.898$_{-0.006}^{+0.021}$ | 3.75$_{-2.2}^{+4.8}$ |
| H$_2$ | 3.724736 | 110.0$_{-4.0}^{+4.7}$ | 59.3$_{-1.2}^{+2.6}$ | 30.4$_{-4.3}^{+3.8}$ |
| Pf$\gamma$ | 3.740568 | 414.0$_{-3.3}^{+3.8}$ | 111.0$_{-3.5}^{+4.7}$ | 398.0$_{-1.7}^{+2.6}$ |
| Hu 17 | 3.749402 | 12.6$_{-2.1}^{+3.2}$ | 2.87$_{-2.0}^{+2.9}$ | 19.5$_{-2.4}^{+3.1}$ |
| H$_2$ | 3.807736 | 215.0$_{-2.7}^{+2.1}$ | 93.5$_{-16.9}^{+33.1}$ | 70.6$_{-1.6}^{+2.2}$ |
| Hu 16 | 3.819460 | 16.9$_{-2.0}^{+3.3}$ | 3.96$_{-2.1}^{+3.2}$ | 25.4$_{-2.3}^{+2.7}$ |
| C I (?) | 3.841473 | 24.2$_{-0.9}^{+1.7}$ | 26$_{-1.6}^{+2.4}$ | 13.3$_{-1.3}^{+1.9}$ |
| H$_2$ | 3.846434 | 349.0$_{-2.6}^{+3.1}$ | 186.0$_{-2.4}^{+2.9}$ | 99.6$_{-1.2}^{+3.4}$ |
| Hu 15 | 3.907557 | 41.7$_{-2.5}^{+4.3}$ | 23.6$_{-1.7}^{+3.2}$ | 36.7$_{-1.8}^{+2.7}$ |
| H$_2$ | 4.162772 | 63.1$_{-2.5}^{+5.4}$ | 47.0$_{-2.2}^{+3.5}$ | 24.1$_{-1.5}^{+1.7}$ |
| Hu 13 | 4.170803 | 26.8$_{-3.6}^{+3.6}$ | 77.4$_{-10.3}^{+18.8}$ | 45.0$_{-1.9}^{+3.4}$ |
| H$_2$ | 4.181426 | 941.0$_{-2.6}^{+5.4}$ | 580.0$_{-3.3}^{+4.8}$ | 248.0$_{-1.7}^{+3.0}$ |
| Hu 12 | 4.376464 | 78.1$_{-3.0}^{+3.7}$ | 33.0$_{-1.6}^{+3.4}$ | 59.5$_{-1.2}^{+3.4}$ |
| H$_2$ | 4.410159 | 454.0$_{-2.0}^{+2.1}$ | 292.0$_{-1.3}^{+4.9}$ | 117.0$_{-1.2}^{+2.2}$ |
| H$_2$ | 4.416979 | 142.0$_{-1.8}^{+2.8}$ | 71.2$_{-2.3}^{+3.7}$ | 41.4$_{-1.0}^{+1.4}$ |
| H$_2$ | 5.053536 | 972.0$_{-4.8}^{+7.1}$ | 644.0$_{-5.8}^{+5.7}$ | 289.0$_{-1.9}^{+4.5}$ |
| Hu$\delta$ | 5.128669 | 148.0$_{-3.6}^{+6.7}$ | 120.0$_{-3.5}^{+5.3}$ | 183.0$_{-2.7}^{+2.1}$ |

Notes: This list comprises all emission lines detected in band3; see also Tables [\[tab:linelist\]](#tab:linelist) and [\[tab:linelist2\]](#tab:linelist2) for those in band1 and band2, respectively. The reported fluxes are obtained from single Gaussian fits, without dust- and aperture-corrections.

[^1]: e-mail: mperna@cab.inta-csic.es

[^2]: <https://www.nist.gov/pml/atomic-spectra-database>

[^3]: <https://hitran.org/>

[^4]: Slightly smaller (but consistent) values would be obtained using the (cite: PiquerasLopez2016) relation.

</paper>

Write the methods card for this paper.