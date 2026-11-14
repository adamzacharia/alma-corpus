# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024PASJ...76..437Y\sonnetcc\reply.txt

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
 "bibcode": "2024PASJ...76..437Y",
 "title": "ALMA 2D super-resolution imaging of Taurus-Auriga protoplanetary disks: Probing statistical properties of disk substructures",
 "year": 2024,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Yamaguchi, Masayuki",
 "n_authors": 9,
 "arxiv_id": "2404.13570",
 "doi": "10.1093/pasj/psae022",
 "alma_projects_linked_by_archive": [
  "2013.1.00105.S",
  "2013.1.00498.S",
  "2013.1.01070.S",
  "2015.1.00889.S",
  "2015.1.01207.S",
  "2015.1.01268.S",
  "2016.1.00724.S",
  "2016.1.00846.S",
  "2016.1.01164.S",
  "2016.1.01205.S",
  "2016.1.01370.S",
  "2016.A.00026.S",
  "2017.1.00940.S",
  "2017.1.01151.S",
  "2017.1.01404.S",
  "2017.1.01460.S",
  "2017.1.01631.S",
  "2018.1.00945.S",
  "2018.1.01230.S",
  "2018.1.01255.S",
  "2018.1.01631.S",
  "2018.1.01755.S",
  "2018.1.01829.S",
  "2019.1.00579.S",
  "2019.1.01108.S"
 ]
}
```

Paper text:
<paper>
# ALMA 2D Super-resolution Imaging of Taurus-Auriga Protoplanetary Disks: Probing Statistical Properties of Disk Substructures

## Abstract

In the past decade, ALMA observations of protoplanetary disks revealed various substructures including gaps and rings. Their origin may be probed through statistical studies on the physical properties of the substructures. We present the analyses of archival ALMA Band 6 continuum data of 43 disks (39 Class II and 4 Herbig Ae) in the Taurus-Auriga region. We employ a novel 2D super-resolution imaging technique based on sparse modeling to obtain images with high fidelity and spatial resolution. As a result, we have obtained images with spatial resolutions comparable to a few au ($0''.02 - 0''.1$), which is two to three times better than conventional CLEAN methods. All dust disks are spatially resolved, with the radii ranging from 8 to 238 au with a median radius of 45 au. Half of the disks harbor clear gap structures, whose radial locations show a bimodal distribution with peaks at $\lesssim20$ au and $\gtrsim30$ au. We also see structures indicating weak gaps at all the radii in the disk. We find that the widths of these gaps increase with their depths, which is consistent with the model of planet-disk interactions. The inferred planet mass-orbital radius distribution indicates that the planet distribution is analogous to our Solar System. However, planets with Neptune mass or lower may exist in all the radii.

Institute of Astronomy and Astrophysics, Academia Sinica, 11F of AS/NTU Astronomy-Mathematics Building, No.1, Sec. 4, Roosevelt Rd, Taipei 10617, Taiwan Department of Astronomy, Graduate School of Science, The University of Tokyo, 7-3-1 Hongo, Bunkyo-ku, Tokyo 113-0033, Japan National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan Division of Liberal Arts, Kogakuin University, 1-24-2 Nishi-Shinjuku, Shinjuku-ku, Tokyo 163-8677, Japan Leiden Observatory, Leiden University, P.O. Box 9513, NL-2300 RA Leiden, The Netherlands Department of Earth and Planetary Sciences, Tokyo Institute of Technology, 2-12-1 Oh-okayama, Meguro-ku, Tokyo 152-8551, Japan Division of Systems and Information Engineering, Ashikaga University, 268-1 Omae-cho, Ashikagashi, Tochigi 326-8558, Japan Department of Astronomical Science, School of Physical Sciences, Graduate University for Advanced Studies, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan The Institute of Statistical Mathematics, 10-3 Midori-cho, Tachikawa, Tokyo 190-8562, Japan Department of Statistical Science, School of Multidisciplinary Sciences, Graduate University for Advanced Studies, 10-3 Midori-cho, Tachikawa, Tokyo 190-8562, Japan Astrobiology Center, National Institutes of Natural Sciences, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan

# Introduction

Planets are believed to be formed in protoplanetary disks around young stars (e.g., (cite: Hayashi1985; Shu1987)). Recent Atacama Large Millimeter/Submillimeter Array (ALMA) observations have revealed that many disks around Class II stars have small-scale structures such as gaps, rings, and asymmetries, through both survey programs and individual target studies (cite: Andrews2018a; Tsukagoshi2019; Hashimoto2021dmtau; Cieza2021; Orihara2023).

Various mechanisms have been proposed as the origins of the disk substructures: gravitational disk instabilities (cite: Youdin2011; Takahashi2014), magneto-hydrodynamics (cite: Flock2015), planet-disk interaction (cite: Takeuchi1996; Zhu2012), and chemical processes (cite: Zhang2015; Okuzumi2016). The recent discovery of protoplanets in the central cavity of PDS 70 (cite: Keppler2018; Benisty2021) and AB Aur (cite: Currie2022) might indicate some cavity structures may be caused by embedded planet(s). However, we do not yet have firm evidence of what the major process is to produce substructures in protoplanetary disks.

Higher spatial resolution is crucial in capturing the substructures in disks. If the substructures are of dynamical origin, disk scale height ($\sim$ sound crossing time over one Keplerian orbit) becomes a key length scale. It is typically $10\%$ of the radial distance from the central star (see (cite: Andrews2020), and references therein). At the distance of 140 pc (e.g., Taurus-Auriga region; (cite: Galli2018)), the observations with $\sim 0''.1$ or better resolution are required, and indeed, the observations with this level of spatial resolution have found substructures in Taurus-Auriga Region (cite: ALMAPartnership2015; Tang2017; Clarke2018; Long2018; Long2019; Ubeira2019; Facchini2020; Huang2020; Ueda2022). Many of them are annular gaps residing at $10-100$ au from the central star. Yet, no clear statistical trends of gap properties have been reported so the origin of the substructure is controversial. The samples may still be biased towards mm-bright disks that can be easily resolved with a high signal-to-noise ratio. Furthermore, an observational framework of disk structure analyses is still being developed (e.g., (cite: Huang2018; Marel2019; Bae2022)). In this regard, increasing the sample of disks resolved with spatial resolution of $0''.1$ or better can provide us with valuable insights into the origin of disk substructures.

The increase in spatial resolution does not necessarily require new observations. Recently, we have shown that imaging using sparse modeling (SpM) can yield high-fidelity images with spatial resolution improved by a factor of $\sim 2-3$, using the data of protoplanetary disks taken by ALMA (cite: Yamaguchi2020; Yamaguchi2021). In the analyses of the disk around T Tau, we achieved the spatial resolution of $0''.04$, which is a factor of three higher than that of the reconstructed with conventional CLEAN, $0''.12$. Therefore, it is natural to extend the analyses to data of other disks with the nominal CLEAN beam size larger than $0''.1-0''.2$. In this paper, we apply SpM to the archival ALMA Band 6 continuum data of 43 young stellar objects (39 Class II objects and four Herbig stars) in the Taurus-Auriga region (age of $\sim 1-3$ Myr; (cite: Luhman2023), a distance of $\sim 140$ pc; (cite: Galli2018)). With the SpM technique, we obtain higher spatial resolution images ($0''.02-0''.1$) improved by a factor of $2-3$. We compare the images obtained by SpM and CLEAN and then search for substructures in high-resolution images obtained with SpM. We also show statistical analyses of quantities that characterize the substructures.

This paper is constructed as follows. We describe sample selection in Section [2](#sec:source_selection). Section [3](#sec:datadeduction_imaging) outlines the data reduction processes and imaging methods, including both CLEAN and SpM. We address the quality of SpM images in Section [4](#sec:images) and discuss the total flux values of ALMA observations in Section [5](#sec:totalflux). We define the categorization of disk substructures in Section [6](#sec:categorize_ra) and then discuss the statistical properties of gaps in Sections [7](#sec:radialdistribution_gap) and [8](#sec:corr_disksub). Section [9](#sec:discussion) is devoted to a discussion of the origin of structures and Section [10](#sec:conclusion) is for conclusions.

# Source Selection

![](taurus_flux_plot.pdf)

We first describe the source selection in this study. We select targets from those in the Taurus-Auriga region that are identified as Class II YSOs or Herbig Ae stars (cite: Rebull2010; Luhman2010; Vioque2018) with existing ALMA Band 6 data at spatial resolutions higher than $0''.2$. We further impose the following criteria:

1.  The spectral type of M3 to A1 (cite: Mora2001; Herczeg2014): Stars with $\rm M9-M4$ are excluded because the majority of them are binary disks having significantly faint flux densities (a few mJy) at 1.3 mm (cite: Andrews2013) and have not been observed with ALMA.

2.  Single stars or the primary stars of binary/multiple systems with separation larger than $0''.4$ ($\sim$50 au): With the latter condition, the tidal interaction effect from the companion (e.g., (cite: Ichikawa2021)) may not be very significant on the size and the structures of the disk.

3.  The ALMA data should have Signal-to-Noise Ratios (SNRs) better than 30 in the CLEAN image domain: This is because the data lower than this SNR made it difficult to reconstruct a high-fidelity image [^1] with the SpM imaging in our analysis.

In addition, we have added two circumbinary disk systems around spectroscopic binaries (UZ Tau E and DQ Tau) and one companion star of a binary system (RW Aur B). The former is included because the binary separation is very close (orbital period less than ten days; (cite: Jensen2007; Czekala2016)) so the binarity should not affect the outer disk structures significantly. The latter is included because there is a substantial separation from the primary star with a distance of $\sim 1''.5$ ($\sim 245$ au) and we find the presence of substructures within the disk.

Consequently, we have in total 43 YSOs that comprise 29 single stars, 12 stars within binary or multiple systems with large ($> 50$ au) separation, and two spectroscopic binaries (see Table [\[tab:stellar_properties\]](#tab:stellar_properties) for a complete list). This corresponds to $20\%$ in Taurus-Auriga surveyed by the Submillimeter Array (SMA) (cite: Andrews2013). The total flux density at Band 6 (1.1-1.3 mm) spans the wide range of $10-300$ mJy. Figure [1](#fig:disk_spt_vs_flux) compares the total sub-mm flux density of our sample and the entire objects in (cite: Andrews2013). In terms of stellar mass, our sample comprises 38 low-mass stars ($M_{*} \simeq 0.3-1.5~M_{\odot}$, M-K type stars), and five intermediate-mass stars ($M_{*} \simeq 1.5-2.5~M_{\odot}$, F-A types), of which four are Herbig Ae stars (cite: Vioque2018).

**Note.** Column Description: (1) Name of the host star. (2) Distance adopted from $Gaia$ DR2 parallax (cite: Gaia2016; Gaia2018). (3) Stellar property; “S”, “B”, “SB”, and “T” indicate single, binary, spectroscopic binary, and triple, respectively. (4) Spectral type. (5) Stellar mass. We use dynamical stellar masses. For stars not measured dynamical masses, we use stellar masses derived from an evolutionary track model. (6) Stellar luminosity. (7) Dust disk radius measured with curve growth method (see Appendix [11](#appendix:dust_disk_size)). (8) Disk inclination (Inc). $0^{\circ}$ is face-on, and $90^{\circ}$ is edge-on. The measurements without uncertainties are marked with “$\sim$”. (9) Position Angle (P.A.) of a disk (east of north). (10) Method used to deproject the disk structure: “E” indicates the ellipse-fitting for a ring structure, and “G” indicates the 2D Gaussian fitting for encircling a disk. “R” indicates the use of references taken from Keplerian rotation with molecular line observations; AB Aur (cite: Tang2017), MWC 758 (cite: Isella2010mwc758; Boehler2018), and CQ Tau (cite: Ubeira2019). (11) References order: Stellar property, spectral type, stellar mass, and luminosity. (a) (cite: Vioque2018), (b) (cite: Herczeg2014), (c) (cite: Kenyon2008), (d) (cite: Simon2019), (e) (cite: Akeson2019), (f) (cite: Braun2021), (g) (cite: Long2019), (h) (cite: Vieira2003), (i) (cite: Podio2013), (j) (cite: Kraus2009), (k) (cite: Mora2001). : the RW Aur system may be a triple star (as RW Aur A may be a spectroscopic binary; (cite: Gahm1999; Petrov2001)). : the UY Aur system may be a triple system (as UY Aur A may be a close binary; (cite: Tang2014)).

# Data Reduction and Imaging

In this Section, we describe methods of data reduction and imaging. We produce CLEAN and SpM images for all the objects in the same manner as detailed below. The complete list of datasets is presented in Table [\[tab:summary_obs\]](#tab:summary_obs).

|             |       |            |          |       |                |
|:------------|:-----:|:----------:|:--------:|:-----:|:--------------:|
| Name        | Freq  |     BL     |   MRS    |  OST  |    Project     |
|             | (GHz) |   \(m\)    | (arcsec) | (min) |      IDs       |
| \(1\)       | \(2\) |   \(3\)    |  \(4\)   | \(5\) |     \(6\)      |
| AB Aur      |  226  | $15-16196$ |   5.1    | 107.2 | 2015.1.00889.S |
|             |       |            |          |       | 2019.1.00579.S |
| GM Aur      |  261  | $15-14851$ |   2.1    | 117.4 | 2017.1.01151.S |
|             |       |            |          |       | 2018.1.01230.S |
| CI Tau      |  230  | $15-12145$ |   4.4    | 104.2 | 2016.1.01164.S |
|             |       |            |          |       | 2016.1.01370.S |
|             |       |            |          |       | 2018.1.01631.S |
| DL Tau      |  226  | $17-3638$  |   2.4    | 13.2  | 2015.1.01207.S |
|             |       |            |          |       | 2016.1.01164.S |
| DM Tau      |  224  | $15-15238$ |   1.9    | 143.2 | 2013.1.00498.S |
|             |       |            |          |       | 2018.1.01755.S |
| LkCa 15     |  224  | $15-13894$ |   3.0    | 88.4  | 2018.1.01255.S |
|             |       |            |          |       | 2018.1.00945.S |
| AA Tau      |  241  | $41-16196$ |   1.0    | 203.5 | 2013.1.01070.S |
|             |       |            |          |       | 2016.1.01205.S |
|             |       |            |          |       | 2018.1.01829.S |
| GO Tau      |  226  | $17-3638$  |   2.2    | 13.3  | 2015.1.01207.S |
|             |       |            |          |       | 2016.1.01164.S |
| Haro 6-37 C |  238  | $41-2125$  |   2.0    |  1.8  | 2013.1.00105.S |
| MWC 480     |  225  | $19-3638$  |   2.4    | 42.6  | 2016.1.00724.S |
|             |       |            |          |       | 2016.1.01164.S |
| MWC 758     |  226  | $15-16196$ |   2.2    | 361.7 | 2017.1.00940.S |
| IQ Tau      |  225  | $21-3638$  |   1.9    |  1.4  | 2016.1.01164.S |
| CQ Tau      |  225  | $21-8548$  |   1.3    | 73.8  | 2016.A.00026.S |
|             |       |            |          |       | 2017.1.01404.S |
| UZ Tau E    |  225  | $21-3697$  |   1.6    |  8.5  | 2016.1.01164.S |
| DS Tau      |  225  | $21-3697$  |   1.7    |  9.7  | 2016.1.01164.S |
| RY Tau      |  225  | $21-16196$ |   1.3    |  8.7  | 2016.1.01164.S |
|             |       |            |          |       | 2017.1.01460.S |

|            |       |            |          |       |                |
|:-----------|:-----:|:----------:|:--------:|:-----:|:--------------:|
| Name       | Freq  |     BL     |   MRS    |  OST  |    Project     |
|            | (GHz) |   \(m\)    | (arcsec) | (min) |      IDs       |
| \(1\)      | \(2\) |   \(3\)    |  \(4\)   | \(5\) |     \(6\)      |
| CY Tau     |  225  | $43-2270$  |   2.0    |  7.7  | 2013.1.00498.S |
| CIDA 9 A   |  225  | $21-3697$  |   1.6    |  8.5  | 2016.1.01164.S |
| DN Tau     |  226  | $15-3638$  |   2.8    | 12.8  | 2015.1.01207.S |
|            |       |            |          |       | 2016.1.01164.S |
| DG Tau     |  233  | $17-16196$ |   1.2    | 329.5 | 2015.1.01268.S |
|            |       |            |          |       | 2016.1.00846.S |
| DR Tau     |  225  | $21-3638$  |   1.6    |  7.7  | 2016.1.01164.S |
| UX Tau A   |  238  | $41-2125$  |   2.0    |  1.8  | 2013.1.00105.S |
| CW Tau     |  233  | $70-8283$  |   1.1    | 91.3  | 2019.1.01108.S |
| FT Tau     |  225  | $21-3697$  |   1.6    |  8.5  | 2016.1.01164.S |
| V710 Tau A |  225  | $21-3638$  |   1.7    |  8.2  | 2016.1.01164.S |
| V409 Tau   |  225  | $21-3697$  |   1.6    |  8.5  | 2016.1.01164.S |
| HO Tau     |  225  | $21-3697$  |   1.6    |  8.4  | 2016.1.01164.S |
| DQ Tau     |  225  | $21-3638$  |   1.6    |  7.7  | 2016.1.01164.S |
| BP Tau     |  225  | $21-3697$  |   1.6    | 10.1  | 2016.1.01164.S |
| IP Tau     |  225  | $21-3697$  |   1.6    | 10.1  | 2016.1.01164.S |
| DO Tau     |  225  | $21-3638$  |   1.8    |  3.9  | 2016.1.01164.S |
| Haro 6-13  |  225  | $21-3638$  |   1.7    |  4.0  | 2016.1.01164.S |
| V836 Tau   |  225  | $21-3697$  |   1.6    |  8.5  | 2016.1.01164.S |
| HK Tau A   |  225  | $21-3697$  |   1.6    |  8.4  | 2016.1.01164.S |
| HP Tau     |  225  | $21-3638$  |   1.7    |  4.0  | 2016.1.01164.S |
| GI Tau     |  225  | $21-3697$  |   1.6    |  8.5  | 2016.1.01164.S |
| RW Aur     |  225  | $21-16196$ |   1.2    | 136.7 | 2016.1.01164.S |
|            |       |            |          |       | 2017.1.01631.S |
| T Tau N    |  225  | $21-3638$  |   1.7    |  8.2  | 2016.1.01164.S |
| DH Tau A   |  225  | $21-3697$  |   1.6    |  9.9  | 2016.1.01164.S |
| HN Tau A   |  225  | $21-3638$  |   1.7    |  8.2  | 2016.1.01164.S |
| DK Tau A   |  225  | $21-3697$  |   1.6    |  8.4  | 2016.1.01164.S |
| UY Aur A   |  225  | $21-3697$  |   1.8    |  9.6  | 2016.1.01164.S |

**Note.** Column Description: (1) Target name. (2) Observing central frequency in GHz. All target sources are taken from Band 6 observations. (3) Range of baseline lengths (BL) in meters from minimum to maximum lengths. (4) Maximum recoverable scale (MRS) in arc-second of data sets. The calculation is based on the definition of the ALMA technical handbook. (5) Total on-source time (OST) in minutes. (6) ALMA project IDs.

## Data Reduction and CLEAN Imaging

We used the Common Astronomy Software Applications package ($\tt CASA$; (cite: CASA2022)) for the calibration. The data were initially calibrated with the $\tt CASA$ pipeline reduction scripts provided by the ALMA Regional Centers. Given that the data were obtained over a period of several years, different versions of $\tt CASA$ were used for these calibrations. We check the maximum recoverable scale (MRS) given by $=0.983~\lambda/D_{5}$ for long baseline data, where $\lambda$ is the observing wavelength and $D_{5}$ is the 5th percentile of $uv$-distance (see ALMA Technical Handbook in (cite: Cortes2023)). If MRS is smaller than the radii of the known gap and ring features of the objects, we combine the data of the compact array configuration.

When combining the data, sets from different observations, the position offset between the phase center and the target source was adjusted as follows. We use the CLEAN images of each dataset and determine the phase center as the local peak of the emission around the center of the image. For disks with ring-like structures (so that there is no local peak), we determine the phase center as the center of the ellipse structure. After the phase center for each dataset is shifted by the $\tt CASA$ task $\tt fixvis$, the datasets from different observations are assigned to a common phase center using task $\tt fixplanets$. After the coordinates of each dataset were corrected, the visibility of long baseline data was re-scaled using the DSHARP $\tt rescale \_ flux$ function[^2] (cite: Andrews2018a).

We then applied self-calibration to improve SNR (cite: Richards2022) using a CLEAN model as a reference calibrator in the $\tt CASA$ version 6.1.0 environment. The CLEAN model was generated through the $\tt tclean$ task (hereafter referred to as CLEAN). We consistently employed multi-frequency synthesis ($\tt nterm = 1$; (cite: Rau2011)) and applied Briggs weighting with $\tt robust = 0.5$. Here, we used different CLEAN algorithms based on the disk structure: the Cotton–Schwab algorithm (cite: Schwab1984) for disks lacking substructures, such as gaps or rings, and a multi-scale approach (cite: Cornwell2008) with scale parameters of $[0, 1, 3] \theta_{\rm cl}$ (where $\theta_{\rm cl}$ represents the CLEAN beam size) for disks with substructures.

For the data with an initial SNR higher than 100 on the CLEAN image, we conducted two rounds of phase calibration ($\tt calmode = p$) with different integration times: $\tt solint = inf$ and $\tt solint =$ OST/5, where OST indicates on-source time We then performed one round of amplitude and phase calibration ($\tt calmode = ap$) with an integration time of $\tt solint$=OST/5. For data with initial SNR less than 100, we applied one round of phase calibration with an integration time of $\tt solint = inf$, followed by one round of amplitude and phase self-calibration with an integration time of $\tt solint =$ OST/5. We choose the image with the best SNR among those obtained in the course of self-calibration processes as the final CLEAN image.

After self-calibration, we have seen an improvement of SNR with a factor of $\sim 1.5$ (for data with the maximum baseline of $\sim 10~\rm M\lambda$) to several (for data with the maximum baseline of $\sim 2~\rm M\lambda$). We see that the self-calibration process mitigated patchy artifacts outside the region of source emission. The final CLEAN beam size $\theta_{\rm cl}$, peak intensity, and RMS noise level $\sigma_{\rm cl}$ (collected noise value from the dust emission-free area) are listed in Table [\[tab:fullsample\]](#tab:fullsample).

**Note.** Column description: (1) Name of the host star. The names are ordered by decreasing au-scale size of the disks from top to bottom. (2) CLEAN beam $\theta_{\rm cl}$. $\texttt{Briggs~robust}$ parameters are fixed to be 0.5 for all images. (3) SpM beam $\theta_{\rm eff}$. The value is obtained by the point source injection method (see Section [3.2](#sec:imaging_spm)). (4) RMS noise $\sigma_{\rm cl}$ of the CLEAN image in the unit of $\rm \mu Jy~beam^{-1}$ and $\rm mJy~arcsec^{-2}$ (denoted in the parentheses). The value is calculated from the emission-free area. (5) Detection threshold $I_{\rm DT}$ of the SpM image. The value is the maximum value of the emission-free area. (6) and (7) Peak intensity of each CLEAN and SpM image, respectively. The unit of the CLEAN value is expressed in both $\rm \mu Jy~beam^{-1}$ and $\rm mJy~arcsec^{-2}$ (denoted in the parentheses). (8) Flux density $F_{\nu}$ of SpM image. The value is obtained by the curve-growth method (see Appendix [11](#appendix:dust_disk_size)). The uncertainty is the $10\%$ absolute calibration error for ALMA observations. (9) The employed two hyper-parameters of SpM image ($\Lambda_l$, $\Lambda_{tsv}$) in logarithmic scale.

## Imaging with Sparse Modeling

We apply SpM to produce an image from the self-calibrated visibility data. We use $\tt PRIISM$ [^3], ver. 0.7.2 (cite: Nakazato2020) in conjunction with $\tt CASA$ to perform $\ell _1$+TSV imaging and the cross-validation (CV) scheme as illustrated in (cite: Yamaguchi2021). The image was reconstructed by minimizing a cost function, which is the weighted chi-square error between the visibility model derived by the model image and observed visibility, accompanied by two regularization terms, namely $\ell_1$-norm and the total squared variation (TSV). Each regularization term is multiplied by hyper-parameters ($\Lambda_{l}$ for $\ell_1$ norm and $\Lambda_{tsv}$ for TSV), which control the relative weighting of the regularization terms to the observations. The SpM algorithm does not involve the beam convolution processes to obtain the final image, unlike the CLEAN algorithm. This potentially leads to images with higher spatial resolution compared to beam-convoluted CLEAN images, i.e., “super-resolution” images.

The $\ell _1$ norm (so-called LASSO regression; (cite: Tibshirani1996)) serves as a sparse regularization function in the image domain, regulating the total flux density in the brightness distribution and simultaneously adjusting low-brightness noise intensity in the emission-free region (e.g., (cite: Honma2014)). $\Lambda_{l}$ controls the degree of sparsity of the image. The image with larger $\Lambda_{l}$ is more sparse, that is, lower noise level in the background while the total flux is lower.

The TSV regularization controls the smoothness of the brightness distribution and uses the $\ell _2$ norm (so-called Ridge regression; (cite: Hoerl1970)) in the gradient domain. This regularization suppresses steep brightness variation and thus prefers edge-smoothed distribution (cite: Akiyama2017ApJ; Kuramochi2018). This regularization and the hyper-parameter $\Lambda_{tsv}$ also play an important role in determining the effective spatial resolution of the reconstructed images. With higher values of $\Lambda_{tsv}$, smoother (smaller gradient), or low spatial resolution, images are reconstructed.

We obtain one model image that minimizes the cost function for a given set of $(\Lambda_{l}, \Lambda_{tsv})$, and we have a set of model images with a range of values of $(\Lambda_{l}, \Lambda_{tsv})$. If the weights of the regularization terms are either excessively strong or weak, the model visibility derived from the reconstructed image deviates from the observed one. To select a pair of $(\Lambda_{l}, \Lambda_{tsv})$ for the optimal image, we employ the 10-fold cross-validation (CV) approach (see Equation 2 in (cite: Yamaguchi2021)). This approach explores the optimal hyper-parameters by considering the errors between the model and observations. We first find a set of hyper-parameters $(\Lambda_{l,\min}, \Lambda_{tsv,\min})$ which give the minimum cross-validation error (CVE). In most cases, we judge that the image reconstructed with $(\Lambda_{l,\min}, \Lambda_{tsv,\min})$ is the one with the highest fidelity (cite: Akiyama2017ApJ). However, in some cases, we find that the image with the minimum CVE exhibits artificial patchy structures. In such cases, we visually inspect a set of images obtained by hyper-parameters with $\Delta \log \Lambda_{l}\leq 1$ and $\Delta \log \Lambda_{tsv}\leq 1$, where $\Delta \log \Lambda$ stands for $|\log \Lambda - \log \Lambda_{\min}|$. For five objects (DM Tau, GO Tau, DS Tau, DN Tau, and RW Aur), we conservatively choose the image with $\Lambda_{tsv}$ one order of magnitude larger than $\Lambda_{tsv, \min}$ as optimal. The total fluxes of those SpM images are consistent with those of CLEAN images within $5-10\%$ errors. The final values for $(\Lambda_{l}, \Lambda_{tsv})$ are summarized in Table [\[tab:fullsample\]](#tab:fullsample).

We assess the effective spatial resolution $\theta_{\rm eff}$ of the SpM image by the “point-source injection” method outlined in (cite: Yamaguchi2021). We inject an artificial point source into the visibility data using the $\tt CASA$ task $\tt addcomponent$, $\tt ft$, and $\tt uvsub$. The artificial point source is placed in an emission-free area north of the central star but at the distance within MRS (Table [\[tab:summary_obs\]](#tab:summary_obs)) and its flux is set to be $5\%$ of the total flux density of the target. Then, SpM imaging was performed for the point-source injected data using the same set of regularization parameters employed for generating the optimal image of non-injected data. The injected point source exhibits a Gaussian-like distribution in the reconstructed image. We fit it with an elliptical Gaussian function to obtain the Full Width at Half Maximum (FWHM), which is used as a measure of the effective spatial resolution $\theta_{\rm eff}$ of the SpM image. We have checked that the measured spatial resolution is altered only at the level of a few percent if we inject the point source in the east, west, or south of the central star and the total flux density of the point source is recovered within a $10\%$ error range. The effective spatial resolutions $\theta_{\rm eff}$ of SpM images are summarized in Table [\[tab:fullsample\]](#tab:fullsample).

Here, we briefly describe our motivation for choosing SpM over the Maximum Entropy Method (MEM; (cite: Narayan1986)), which is another regularization method. MEM uses a relative entropy function that requires a “prior image” (e.g., a noise map derived from a dirty map or a circular Gaussian model; (cite: Carcamo2018; EHT2019)). However, incorporating prior information may introduce biases into the reconstructed image. In contrast to MEM, SpM does not impose such prior information. We also note that MEM simultaneously imposes a similar sparsity and smoothness constraint as the $\ell _1$ norm and TSV regularizations in a single regularization term (see Equation 27 in (cite: EHT2019)). SpM has the advantage of imposing them separately so that it is easier to control the balance between the sparsity and smoothness constraints.

# Reconstructed Images and SpM Imaging Performances

Figures [2](#fig:clean_image) and [3](#fig:spm_image) show the images of 43 disks of our targets using the CLEAN and SpM methods, respectively. Note that all images show the surface brightness distribution in units of $\rm Jy~asec^{-2}$ for consistency. We clearly see many more disk substructures in the SpM images. Distinct structures, such as gaps, rings, and crescents are seen in most of the disks.

Before going into details of analyses in Sections [4](#sec:images) to [8](#sec:corr_disksub), we define the terms “compact” and “large” disks used in this study. Figure [4](#fig:diskradius) shows the distribution of dust disk radii $r_{\rm disk}$ taken from the SpM images (see Appendix [11](#appendix:dust_disk_size) for the definition of disk radius). The disk radii span a wide range from 8 to 238 au, with a median radius of 45 au. We set this median radius as a boundary of the “compact” and “large” disks. In the following subsections in Section [4](#sec:images), we analyze the technical aspects of imaging methods: spatial resolution, goodness of visibility fit, and image fidelity.

![](gallary_cleanim.pdf)

![](gallary_spmim.pdf)

![](dustdiskradius.pdf)

## Spatial Resolution

![](resolution_ratio.pdf)

![](resoratio_disksize.pdf)

Figure [5](#fig:resolution_ratio) shows the spatial resolution of SpM images and the ratio of SpM image resolution and CLEAN beam, that is, SpM/CLEAN = $\theta_{\rm eff}/\theta_{\rm cl}$ for each disk. 18 out of 43 targets show a factor of two to three improvement in spatial resolution compared to the conventional CLEAN method. All but three images show spatial resolution better than $0''.1$, with the highest achieved resolution reaching $0''.01 - 0''.02$.

In the left panel of Figure [6](#fig:resraatio_disksize), we find a robust relationship between the improvement of spatial resolution and the SNR (peak/RMS away from emission) of the CLEAN image. The left panel of Figure [6](#fig:resraatio_disksize) shows a clear trend of decreasing resolution ratio as increasing SNR (Pearson correlation coefficient $\rho = -0.65$, $p$-value $< 0.01$). Using Bayesian linear regression in logarithmic space, this trend can be described as $$\begin{equation}
\label{eq:resolution_snr}
\log \left(\frac{\theta_{\rm eff}/\theta_{\rm cl}}{\%}\right)= (2.30\pm 0.11) - (0.24\pm0.05) \log \mathrm{SNR}
\end{equation}$$ with a Gaussian scatter perpendicular to this regression with a standard deviation of $0.13\pm0.01$ dex. We have used $\tt Linmix$[^4] (cite: Kelly2007) for fitting. The resolution can be improved by a factor of two if the SNR reaches $\sim 100$ on the CLEAN image. It remains similar to that of the CLEAN image if the SNR is $\sim30$.

In the right panel of Figure [6](#fig:resraatio_disksize), we also find a robust relationship ($\rho = 0.78$ and $p-$value $< 0.01$) between the improvement in spatial resolution and the disk size $\theta_{\rm disk}$ (= $2 \times r_{\rm disk}$) (arcsec) normalized by the CLEAN beam size $\theta_{\rm cl}$ (arcsec). We note that the sizes of these disks are measured on the SpM images, and all disks are spatially resolved. Using the Bayesian linear regression, we obtain $$\begin{equation}
\label{eq:resolution_disksize}
\log \left(\frac{\theta_{\rm eff}/\theta_{\rm cl}}{\%}\right)= (1.55\pm 0.03) + (0.22\pm0.03) \log \left( \frac{\theta_{\rm disk}}{\theta_{\rm cl}} \right)
\end{equation}$$ with a Gaussian scatter of $0.11\pm0.01$ dex. The resolution can be improved by a factor of two when the disk size is $2-10$ times larger than the CLEAN beam size. It remains similar to that of the CLEAN image when the disk size is larger than the CLEAN beam size by more than 30 times.

From the two empirical relationships for SpM resolution improvement, we see that this improvement is more significant for higher SNR data or more compact disks close to the CLEAN beam size. This is because the visibility data of compact disks tend to have higher SNR at the longest baseline lengths. The large disk data are in many cases constructed with more than two antenna configurations, where the SNRs in the long baseline data are relatively low compared to those in the short baselines. With a better SNR of visibility at long baselines, it is possible to recover structures at smaller spatial scales and thus obtain better spatial resolution. The beam size of the CLEAN method, on the other hand, is determined by the array configuration, and the SNR is not taken into account (see ALMA Technical Handbook). Therefore, data with better SNR at long baselines tend to show more improvement in spatial resolution when SpM is applied. These two empirical relationships would provide an estimate of the required SNR or source size for SpM to be effective in improving spatial resolution.

In Appendix [12](#appendix:vis_profile_objects), we elaborate more on how the resolution is improved with the disk size by using the data of two disks with different sizes. In Appendix [13](#appendix:noislevel_spm), we evaluate how the noise level of images is related to the improvement of spatial resolution.

## Goodness of Visibility Fits

![](resolutionratio_chisquare.pdf)

We assess the performance of SpM and CLEAN imaging by investigating how well the Fourier transform of the reconstructed images can fit the visibility. We use the reduced chi-square $\rm Red\chi^2$ as a measure of goodness-of-fit. We calculate $\rm Red\chi^2$ that compares the observed visibility and the model visibility that is obtained as the Fourier transform of the model image (see Appendix [14](#appendix:vis_profile)). For CLEAN images, we use “CLEAN” to indicate the image obtained after beam convolution while “CLEAN model” to indicate the one before the beam convolution, or a collection of clean components.

The top left panel of Figure [7](#fig:resolutionratio_chisquare) shows the histogram of the ratio of the reduced chi-square values obtained for CLEAN and SpM $(\rm Red\chi^{2}_{\rm cl}/ Red\chi^{2}_{\rm spm})$. SpM produces a better fit in $95\%$ of the cases (40/42). The remaining $5\%$ (2 cases) show comparable performance between SpM and CLEAN. The top right panel of Figure [7](#fig:resolutionratio_chisquare) shows the ratio of the reduced chi-square values for the CLEAN model and SpM $(\rm Red\chi^{2}{\rm clmodel}/ Red\chi^{2}{\rm spm})$. In this case, SpM shows better performance for $69\%$ (29/42), so we consider SpM and CLEAN models to be of comparable performance in terms of goodness-of-fit. In both CLEAN vs SpM and CLEAN model vs SpM comparisons, we find that the ratio of reduced chi-square values and the improvement of spatial resolution may be correlated. Further description is given in Appendix [15](#appendix:chisq_resolution).

The difference in performance between the CLEAN and CLEAN model is due to beam convolution. In the CLEAN algorithm, clean components are placed in a way that the “CLEAN model” matches observed visibility. Then, the “CLEAN model” image is convolved with a restoring beam to obtain the “CLEAN” image. This process acts as a low-pass filter and causes the visibility amplitude to deviate from the original, especially in the long baselines.

Although the goodness-of-fit is comparable in the CLEAN model and SpM images, the quality of the actual 2D image is very different. The CLEAN model image is a collection of point sources (or multi-scale Gaussian distributions; (cite: Schwab1984; Rau2011)). The SpM image can better reproduce complex and smooth structures compared to the CLEAN model images. Therefore, we consider that the SpM images are more plausible for scientific analyses compared to the CLEAN model images. We note, however, that the CLEAN model can capture some of the features such as the gradient of the outer edge of a disk if the model is azimuthally averaged. Further discussion is given in Appendix [16](#appendix:utility_clmodel).

## Image Fidelity

The fidelity of SpM images is assessed with the “cross-check method” (cite: Yamaguchi2020), wherein a comparison is made between the CLEAN image derived from the visibility data including the long baseline observations and the SpM image generated from those of the short baseline observations (refer to Appendix [17](#appendix:eval_spm) for a comprehensive description of this procedure). We have analyzed three bright and large disks that already have the necessary data: DG Tau, RY Tau, and CI Tau. We confirm that those images reconstructed from the shorter-baseline data using the SpM match those obtained with the longer-baseline data using CLEAN. Furthermore, azimuthally averaged radial intensity profiles of the SpM image and the CLEAN image with long baseline data in three disks agree within $10\%$ error.

However, we note that SpM imaging can introduce artificial clumped/speckled features, especially for disks with the brightest emission in the central part (i.e., an inner disk) surrounded by the faint emission area (i.e., a ring skirt). We observe these features in several samples, including DQ Tau, DR Tau, FT Tau, GO Tau, GI Tau, Haro 63-C, UZ Tau E, and MWC 480 (see Figure [3](#fig:spm_image)). The possible cause is the intrinsic bias of the SpM imaging. This imaging preferentially fits the bright and compact part (e.g., inner disk) of the target, but this bias could introduce similar “compact” features such as clumps and speckles to the surrounding extended area (e.g., a ring or its surrounding).

These artifacts can be suppressed by taking the azimuthal average and extracting the radial intensity profile. In this way, the image is “smoothed” in the azimuthal direction while the spatial resolution in the radial direction is unaffected (see Appendix [17](#appendix:eval_spm)). We thus employ the radial profile when extracting the physical properties of the disks.

# Total Flux and Disk Size

In this Section, we present the measurements of total flux and disk sizes. We compare the measurements with other telescopes and discuss the correlation between the flux and disk size. Methods of measuring the flux and size are outlined in Appendix [11](#appendix:dust_disk_size).

## Comparison with Other Telescopes 

We compare our measurements of total flux with those taken by other telescopes. First, we consider data taken by other interferometers. We take the total fluxes taken by the SMA (cite: Andrews2013) for 41 Class II disks and those by the Plateau de Bure Interferometer (cite: Chapillon2008) for the two Herbig disks of CQ Tau and MWC 758. The total flux densities taken at different wavelengths (AA Tau at 1.2 mm and GM Aur at 1.1 mm) in ALMA data sets are modified for those at 1.3 mm, by applying spectral indices $\alpha_{\rm mm}$ of 1.6 for AA Tau (cite: Andrews2005) and 2.7 for GM Aur (cite: Huang2020). These spectral indices are derived from the relationship in $F_{\nu}\propto \nu^{\alpha_{\rm mm}}$. These compact interferometers have larger maximum recoverable scales than the ALMA and have beam sizes ranging from $2''-5''$, corresponding to $130-350$ au from the central star at a distance of 140 pc. In the top left panel of Figure [8](#fig:totalfluxratio), we show the ratio of total flux measured with ALMA and other interferometers. We see that most of the flux values measured with ALMA are consistent with those obtained from other compact interferometers. The top right panel shows the probability histogram of the flux ratios generated by a Monte Carlo routine, which uses random sampling of iterative 5000 calculations by incorporating the errors associated with each flux ratio measurement. The average of the histogram is $110\%\pm25\%$, where the error indicates the standard deviation. Therefore we consider that ALMA observations, in general, have detected dust emission signals all the way to the outer edge of the disk and do not resolve out large-scale structures. However, the total fluxes of DK Tau A and V710 Tau A are $\sim 50\%$ higher than those obtained with SMA. Since SMA has a shorter maximum baseline than ALMA, spatial filtering of the SMA data cannot explain this discrepancy. We actually find other ALMA observations at the same observing wavelength but 1.5 times higher sensitively and $\sim 2$ times lower resolution have obtained the total flux values that are consistent with our results within $10\%$ for the two disks (cite: Rota2022). Therefore we consider that there may have been some calibration issues at the time of SMA observations or there is some time variability of mm flux for the two objects.

Next, we compare the total flux density with those obtained by the IRAM 30m single-dish telescope, which has a beam size of $11''$, corresponding to the area of 770 au in radius at the distance of 140 pc (cite: Beckwith1990; Osterloh1995). Here, we use the data only for 21 disks with single-star systems to avoid contamination by dust emission from companions. The bottom panels of Figure [8](#fig:totalfluxratio) show the flux ratio and the probability histogram. The average flux ratio is $79\%\pm19\%$, suggesting that the ALMA observations drop $\sim 20\%$ of the total flux density taken by a single-dish telescope. This discrepancy may be accounted for as the contribution from the emission at the envelope scale surrounding the star and disk system. Further discussion on this interpretation is given in Section [9.1](#sec:envelope_remnants).

![](Totalflux_Ratio.pdf)

## Relation of Flux and Disk Size

![](diskradius_mmluminosity.pdf)

The correlation between millimeter luminosity (total flux density re-scaled to a common distance) and the disk size in a nearby star-forming region has been suggested using 0.9 mm data from SMA and medium-resolution ($0''.1-0''.2$) ALMA observations (cite: Tazzari2017; Tripathi2017; Barenfeld2017; Andrews2018b; Long2019; Hendler2020; Tazzari2021). Here, we explore if there is a similar trend in our dataset. In previous studies, disk sizes were constrained by parametric modeling of disk shapes and fitting in the visibility domain. In our dataset, it is possible to measure the disk size directly in the image domain since all 43 disks are spatially resolved with SpM. Therefore, our approach provides a model-independent assessment of the disk size-luminosity relation. Figure [9](#fig:size_lumi_relation) presents the millimeter luminosity $L_{\rm mm}$ as a function of disk radii $r_{\rm dust}$. We see a strong correlation with $\rho = 0.63$ and a $p-$value of $<0.01$. Linear regression on the logarithmic scale gives $$\begin{equation}
\log \left(\frac{r_{\rm disk}}{\mathrm{au}}\right)= (2.32_{-0.13}^{+0.13})+ (0.50_{-0.10}^{+0.10}) \log \left[F_{v}\left(\frac{d}{140 \mathrm{pc}}\right)^{2}\right]
\end{equation}$$ with a scattering of $0.36 \pm 0.04$ dex. Also seen in Figure [9](#fig:size_lumi_relation) is that single-star disks primarily occupy the upper right region, or larger and brighter disks, while binary- and triple-star disks dominate the lower left region or smaller and fainter disks.

The correlation can be written as $L_{\rm {mm}} \propto r_{\rm {disk}}^2$. The same correlation is found by 0.9 mm data of disks in Taurus-Auriga-Ophiuchus regions (cite: Tripathi2017; Hendler2020). This relationship also suggests that the surface brightness intensity $\left\langle I_{\nu}\right\rangle$ (or temperature $\left\langle T_{\rm b} \right\rangle$) averaged over the area inside the dust disk is approximately constant (cite: Tripathi2017). For our data in Band 6, the averaged surface brightness is $\left\langle I_{\nu}\right\rangle \simeq 0.14~\rm Jyasec^{-2}$ and the corresponding brightness temperature is $\left\langle T_{\rm b} \right\rangle \simeq 8$ K. This brightness temperature is similar to what is obtained by (cite: Tripathi2017) despite the difference of observing wavelengths (1.3 mm vs 0.9 mm).

(cite: Tazzari2021) discussed the influence of optical thickness on the size-luminosity relation. Following their approach, we checked the correlation between the disk size and the luminosity re-scaled by $\cos i$ where $i$ is the inclination angle. Employing the Bayesian linear regression, we have obtained $$\begin{equation}
\log \left(\frac{r_{\rm disk}}{\mathrm{au}}\right) = (2.32_{-0.11}^{+0.11}) + (0.58_{-0.10}^{+0.10}) \log \left[\frac{F_{v}}{\cos i}\left(\frac{d}{140 \mathrm{pc}}\right)^{2}\right]
\end{equation}$$ with the scattering of $0.30 \pm 0.02$ dex. We observe a slightly smaller scatter in the correlation when the $\cos i$ effect is considered. The correlation is improved by $\sim10\%$ ($\rho = 0.69$ with a $p-$value of $<0.01$) compared to the case without the $\cos i$ term, while the slope and intercept (normalization) remain statistically consistent within $1\sigma$ uncertainty.

# Categorization of Radial Structures

In this section, we investigate the radial intensity profile of disks. Gaps and rings have been identified by the analyses of radial intensity profiles of disks and the statistical trends of disk substructures have been discussed (e.g., (cite: Pinilla2018; Huang2018; Long2018)). Here, we perform analyses based on the newly obtained images with SpM that recover disk structures at smaller scales compared to CLEAN (see Section [4](#sec:images)). We define fundamental disk substructures such as gaps and rings and suggest categorizations of the disks based on the substructures they have.

## Methods of Extracting Radial Profiles

![](radialprofile_1.pdf)

![](radialprofile_2.pdf)

Figure [10](#fig:radialprofile_1) and [11](#fig:radialprofile_2) show the azimuthally averaged radial intensity profiles $I_{\nu}(r)$. Here, we briefly describe how those profiles are obtained. We first deproject the SpM images shown in Figure [3](#fig:spm_image) to a face-on view. The methods for deriving the geometric parameters for deprojection (inclination and position angle) are outlined in Appendix [11](#appendix:dust_disk_size).

The uncertainty $\hat{\sigma}_{I}$ of the radial intensity profiles is computed as the standard error of the mean at each radius $r_{i}$, considering one beam size as the smallest independent unit. It is given by $\hat{\sigma}_{I}=\sigma_{I}/\sqrt{N_{B}}$, where $\sigma_{I}$ is the standard deviation of the brightness within the concentric ring at $r=r_{i}$ and $N_{B}= 2\pi r_{i}/ \left\langle\theta_{\mathrm{eff}}\right\rangle$ is the number of beams within the ring. Here, the beam size $\left\langle\theta_{\mathrm{eff}}\right\rangle$ is given by the geometric mean of the effective spatial resolution of the SpM image.

We determine the range for azimuthal averaging of the deprojected disks. For 24 disks not listed below, we average all over the azimuth as they show almost axisymmetric structures. For four highly inclined disks with $i \geq 60^{\circ}$ (AA Tau, CW Tau, IQ Tau, and V409 Tau), the azimuthal average is taken in the range from $20^{\circ}$ to $40^{\circ}$ relative to the semi-major axis since the substructures around the minor axis are not well spatially resolved. For disks with gaps and rings that are not identified over full azimuthal angles due to insufficient spatial resolution, low SNRs, or radial asymmetry (GM Aur, GO Tau, GI Tau, DG Tau, DL Tau, DN Tau, DQ Tau, DR Tau, HK Tau A, HO Tau, HP Tau, and RY Tau), we take average over the position angles where we can visually see the gaps and rings. For MWC758, we exclude the range of PA with $290-10^{\circ}$ due to the presence of a significant blob at $r=0''.4$. This blob produces an artificial ring-gap structure in the radial intensity profile. The ranges of the azimuthal angles for averaging for each disk are summarized in Table [1](#tab:disk_substructure).

+:------------+:---------------+:-----------------+:--------------------+:--------------+:---------------+:--------------+:-----------------------+:-----------------+:-----------------+:---------------------------------:+---------:+
| Name        | Rings-Gaps     | Inflection       | Label               | Gap           | Ring           | Inflection    | Gap Width              | Norm Width       | Gap Depth        | Avg Range                         | Method   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Type           | Type             |                     | $r_{\rm gap}$ | $r_{\rm ring}$ | $r_{\rm Inf}$ | $\Delta_{\rm I, unit}$ | $\Delta_{\rm I}$ | $\delta_{\rm I}$ |                                   |          |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             |                |                  |                     | (au, mas)     | (au, mas)      | (au, mas)     | (au)                   |                  |                  | (degree)                          |          |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| \(1\)       | \(2\)          | \(3\)            | \(4\)               | \(5\)         | \(6\)          | \(7\)         | \(8\)                  | \(9\)            | \(10\)           | \(11\)                            | \(12\)   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| Name        | Rings-Gaps     | Inflection       | Label               | Gap           | Ring           | Inflection    | Gap Width              | Norm Width       | Gap Depth        | Avg Range                         | Method   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Type           | Type             |                     | $r_{\rm gap}$ | $r_{\rm ring}$ | $r_{\rm Inf}$ | $\Delta_{\rm I, unit}$ | $\Delta_{\rm I}$ | $\delta_{\rm I}$ |                                   |          |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             |                |                  |                     | (au, mas)     | (au, mas)      | (au, mas)     | (au)                   |                  |                  | (degree)                          |          |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| \(1\)       | \(2\)          | \(3\)            | \(4\)               | \(5\)         | \(6\)          | \(7\)         | \(8\)                  | \(9\)            | \(10\)           | \(11\)                            | \(12\)   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| *Continued on next page*                                                                                                                                                                                                             |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             |                |                  |                     |               |                |               |                        |                  |                  |                                   |          |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| AB Aur      | Pre-Transition | $\cdots$         | D62/B160$^{\dag}$   | 61.6(378)     | 160.0(982)     | $\cdots$      | $116.10\pm2.01$        | $0.90\pm0.01$    | $<40$            | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| GM Aur      | Pre-Transition | $\cdots$         | D14/B40$^{\dag}$    | 14.2(89)      | 39.7(249)      | $\cdots$      | $19.63\pm1.28$         | $0.82\pm0.03$    | $23.94\pm2.56$   | $110 \leq \theta \leq 300$        | case 2   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D69/B84$^{\dag}$    | 68.8(431)     | 84.4(529)      | $\cdots$      | $17.72\pm0.16$         | $0.22\pm0.01$    | $3.67\pm0.09$    | $110 \leq \theta \leq 300$        | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I111                | $\cdots$      | $\cdots$       | 110.6(693)    | $\cdots$               | $\cdots$         | $\cdots$         | $110 \leq \theta \leq 300$        | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D152/B174           | 152.1(953)    | 173.6 (1088)   | $\cdots$      | $\sim 20$              | $\sim 0.1$       | $\sim 2$         | $110 \leq \theta \leq 300$        | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| CI Tau      | Ring-Gap       | $\cdots$         | D16/B24$^{\dag}$    | 15.6(98)      | 23.8(150)      | $\cdots$      | $6.51\pm0.48$          | $0.34\pm0.02$    | $4.22\pm0.52$    | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I28                 | $\cdots$      | $\cdots$       | 27.8(175)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D48/B60$^{\dag}$    | 48.4(305)     | 59.8(377)      | $\cdots$      | $9.36\pm0.63$          | $0.18\pm0.01$    | $1.48\pm0.02$    | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I86                 | $\cdots$      | $\cdots$       | 86.5(545)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D126/B149           | 125.8(793)    | 148.9(938)     | $\cdots$      | $\sim 20$              | $\sim 0.2$       | $\sim 2$         | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DL Tau      | $\cdots$       | Shoulder         | I26                 | $\cdots$      | $\cdots$       | 25.6(161)     | $\cdots$               | $\cdots$         | $\cdots$         | $\theta = 50-140, 320-359$        | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D67/B80$^{*}$       | 66.9(420)     | 79.8(501)      | $\cdots$      | $10.99\pm0.48$         | $0.15\pm0.0$     | $1.82\pm0.05$    | $\theta = 50-140, 320-359$        | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D98/B117$^{* \dag}$ | 97.8(614)     | 116.6(732)     | $\cdots$      | $21.82\pm0.8$          | $0.2\pm0.01$     | $1.82\pm0.04$    | $\theta = 50-140, 320-359$        | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I133                | $\cdots$      | $\cdots$       | 133.3(837)    | $\cdots$               | $\cdots$         | $\cdots$         | $\theta = 50-140, 320-359$        | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DM Tau      | Central Hole   | $\cdots$         | B3                  | $\cdots$      | 2.8(19)        | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Pre-Transition | $\cdots$         | D14/B24$^{\dag}$    | 13.6(94)      | 23.9(165)      | $\cdots$      | $11.17\pm0.15$         | $0.58\pm0.01$    | $51.79\pm15.15$  | $0 \leq \theta \leq 359$          | case 2   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I58                 | $\cdots$      | $\cdots$       | 58.2(401)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D103/B112           | 102.9(709)    | 112.3(774)     | $\cdots$      | $\sim 10$              | $\sim 0.1$       | $\sim2$          | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| LkCa 15     | Pre-Transition | $\cdots$         | D17/B69$^{\dag}$    | 17.3(109)     | 68.8(433)      | $\cdots$      | $14.14\pm0.16$         | $0.56\pm0.01$    | $<110$           | $0 \leq \theta \leq 359$          | case 2   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Inner Disk-Skirt | I49                 | $\cdots$      | $\cdots$       | 48.6(306)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D87/B101$^{\dag}$   | 87.4(550)     | 101.4(639)     | $\cdots$      | $12.87\pm0.64$         | $0.14\pm0.01$    | $1.61\pm0.04$    | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I117                | $\cdots$      | $\cdots$       | 117.3(738)    | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| AA Tau      | Pre-Transition | $\cdots$         | D14/B43$^{\dag}$    | 13.7(100)     | 42.7(311)      | $\cdots$      | $29.5\pm0.14$          | $0.90\pm0.01$    | $<110$           | $|\theta - \mathrm{PA} |\leq30$   | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D66/B73$^{\dag}$    | 66.0(481)     | 73.1(533)      | $\cdots$      | $8.09\pm1.1$           | $0.12\pm0.02$    | $2.72\pm0.26$    | $|\theta - \mathrm{PA} |\leq30$   | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D81/B95$^{\dag}$    | 80.9(590)     | 94.8(691)      | $\cdots$      | $13.03\pm2.33$         | $0.15\pm0.02$    | $3.97\pm0.35$    | $|\theta - \mathrm{PA} |\leq30$   | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I104                | $\cdots$      | $\cdots$       | 103.6(755)    | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} |\leq30$   | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| GO Tau      | $\cdots$       | Shoulder         | I18                 | $\cdots$      | $\cdots$       | 18.1(125)     | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} |\leq20$   | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D56/B72$^{\dag}$    | 56.0(387)     | 72.4(501)      | $\cdots$      | $19.67\pm0.43$         | $0.3\pm0.0$      | $14.49\pm1.4$    | $|\theta - \mathrm{PA} |\leq30$   | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D89/B99$^{*}$       | 88.8(614)     | 99.3(687)      | $\cdots$      | $7.95\pm0.14$          | $0.09\pm0.01$    | $1.78\pm0.17$    | $|\theta - \mathrm{PA} |\leq20$   | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D105/B116$^{*}$     | 104.8(725)    | 116.1(803)     | $\cdots$      | $5.35\pm3.47$          | $0.05\pm0.03$    | $2.23\pm0.12$    | $|\theta - \mathrm{PA} |\leq20$   | case 2   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| Haro 6-37 C | $\cdots$       | Shoulder         | I32                 | $\cdots$      | $\cdots$       | 31.7(162)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D79/B109$^{*}$      | 79.4(406)     | 109.3(559)     | $\cdots$      | $18.2\pm2.94$          | $0.2\pm0.03$     | $1.26\pm0.05$    | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| MWC 480     |                | Shoulder         | I20                 | $\cdots$      | $\cdots$       | 20.4(126)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D77/B98$^{\dag}$    | 77.2(477)     | 98.5(609)      | $\cdots$      | $29.93\pm0.16$         | $0.33\pm0.01$    | $7.08\pm0.3$     | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I120                | $\cdots$      | $\cdots$       | 120.1(742)    | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| MWC 758     | Pre-Transition | $\cdots$         | D15/B51$^{\dag}$    | 14.6(91)      | 50.8(317)      | $\cdots$      | $39.73\pm0.8$          | $0.93\pm0.01$    | $47.73\pm15.72$  | $20 \leq \theta \leq 290$         | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Inner Disk-Skirt | I28                 | $\cdots$      | $\cdots$       | 28.2(176)     | $\cdots$               | $\cdots$         | $\cdots$         | $20 \leq \theta \leq 290$         | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I64                 | $\cdots$      | $\cdots$       | 63.9(399)     | $\cdots$               | $\cdots$         | $\cdots$         | $20 \leq \theta \leq 290$         | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| IQ Tau      | $\cdots$       | Shoulder         | I39                 | $\cdots$      | $\cdots$       | 38.7(295)     | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} |\leq40$   | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I68                 | $\cdots$      | $\cdots$       | 68.3(520)     | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} |\leq40$   | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| CQ Tau      | Pre-Transition | $\cdots$         | D12/B55$^{* \dag}$  | 12.2(75)      | 54.8(336)      | $\cdots$      | $13.21\pm0.49$         | $0.72\pm0.02$    | $9.76\pm0.4$     | $0 \leq \theta \leq 359$          | case 2   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I79                 | $\cdots$      | $\cdots$       | 79.1(485)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| UZ Tau E    | Central Hole   | $\cdots$         | B10                 | $\cdots$      | 10.2(78)       | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I25                 | $\cdots$      | $\cdots$       | 24.8(189)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D70/B80$^{* \dag}$  | 69.5(530)     | 80.3(612)      | $\cdots$      | $9.71\pm1.84$          | $0.13\pm0.02$    | $1.17\pm0.04$    | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DS Tau      | Pre-Transition | $\cdots$         | D32/B55$^{\dag}$    | 32.1(202)     | 55.4(348)      | $\cdots$      | $22.75\pm0.48$         | $0.51\pm0.01$    | $7.72\pm0.71$    | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| RY Tau      | Pre-Transition | $\cdots$         | D5/B15$^{\dag}$     | 5.4(42)       | 15.3(119)      | $\cdots$      | $5.64\pm0.51$          | $0.68\pm0.05$    | $2.6\pm0.2$      | $-50 \leq\rm PA\leq220$           | case 2   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I22                 | $\cdots$      | $\cdots$       | 21.9(171)     | $\cdots$               | $\cdots$         | $\cdots$         | $-50 \leq\rm PA\leq220$           | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D44/B52$^{\dag}$    | 44.1(344)     | 51.7(403)      | $\cdots$      | $6.15\pm2.05$          | $0.13\pm0.04$    | $1.09\pm0.03$    | $-50 \leq\rm PA\leq220$           | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I71                 | $\cdots$      | $\cdots$       | 71.0(554)     | $\cdots$               | $\cdots$         | $\cdots$         | $-50 \leq\rm PA\leq220$           | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| CY Tau      | $\cdots$       | Shoulder         | I28                 | $\cdots$      | $\cdots$       | 27.6(214)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| CIDA 9 A    | Transition     | $\cdots$         | B37                 | $\cdots$      | 37.0(215)      | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I53                 | $\cdots$      | $\cdots$       | 52.9(308)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DN Tau      | Ring-Gap       | $\cdots$         | D24/B31$^{*}$       | 23.7(185)     | 30.9(241)      | $\cdots$      | $5.38\pm1.41$          | $0.2\pm0.04$     | $1.1\pm0.04$     | $230 \leq \rm PA\leq 310$         | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I46                 | $\cdots$      | $\cdots$       | 45.9(358)     | $\cdots$               | $\cdots$         | $\cdots$         | $230 \leq \rm PA\leq 310$         | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DG Tau      | $\cdots$       | Shoulder         | I4                  | $\cdots$      | $\cdots$       | 4.0(33)       | $\cdots$               | $\cdots$         | $\cdots$         | $60 \leq \theta\leq 320$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Shoulder         | I16                 | $\cdots$      | $\cdots$       | 16.4(135)     | $\cdots$               | $\cdots$         | $\cdots$         | $60 \leq \theta\leq 320$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I26                 | $\cdots$      | $\cdots$       | 26.1(215)     | $\cdots$               | $\cdots$         | $\cdots$         | $60 \leq \theta\leq 320$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DR Tau      | $\cdots$       | Shoulder         | I13                 | $\cdots$      | $\cdots$       | 13.3(68)      | $\cdots$               | $\cdots$         | $\cdots$         | $60 \leq\theta \leq160$           | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D36/B42             | 35.8(183)     | 42.3(216)      | $\cdots$      | $5.68\pm0.20$          | $0.15\pm0.01$    | $1.16\pm0.02$    | $60 \leq\theta \leq160$           | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| UX Tau A    | Transition     | $\cdots$         | B35                 | $\cdots$      | 35.1(251)      | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| CW Tau      | Ring-Gap       | $\cdots$         | D20/B25$^{*}$       | 20.0(151)     | 24.9(188)      | $\cdots$      | $3.84\pm0.13$          | $0.17\pm0.01$    | $1.13\pm0.01$    | $|\theta - \mathrm{PA} | \leq40$  | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| FT Tau      | $\cdots$       | Shoulder         | I11                 | $\cdots$      | $\cdots$       | 11.4(89)      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | Ring-Gap       | $\cdots$         | D27/B34$^{*}$       | 27.1(212)     | 34.4(269)      | $\cdots$      | $7.41\pm1.15$          | $0.24\pm0.03$    | $1.26\pm0.03$    | $0 \leq \theta \leq 359$          | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| V710 Tau A  | $\cdots$       | Shoulder         | I17                 | $\cdots$      | $\cdots$       | 17.4(122)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| V409 Tau    | $\cdots$       | Shoulder         | I16                 | $\cdots$      | $\cdots$       | 15.5(118)     | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} |\leq20$   | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| HO Tau      | $\cdots$       | Shoulder         | I20                 | $\cdots$      | $\cdots$       | 19.7(122)     | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} |\leq20$   | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DQ Tau      | $\cdots$       | Shoulder         | I16                 | $\cdots$      | $\cdots$       | 16.2(82)      | $\cdots$               | $\cdots$         | $\cdots$         | $200 \leq\theta \leq 360$         | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Shoulder         | I36                 | $\cdots$      | $\cdots$       | 36.0(182)     | $\cdots$               | $\cdots$         | $\cdots$         | $200 \leq\theta \leq 360$         | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| BP Tau      | Central Hole   | $\cdots$         | B10                 | $\cdots$      | 9.7(75)        | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I24                 | $\cdots$      | $\cdots$       | 23.9(185)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| IP Tau      | Transition     | $\cdots$         | B27                 | $\cdots$      | 27.4(210)      | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DO Tau      | $\cdots$       | Shoulder         | I16                 | $\cdots$      | $\cdots$       | 16.3(117)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| Haro 6-13   | $\cdots$       | Shoulder         | I14                 | $\cdots$      | $\cdots$       | 14.0(107)     | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| V836 Tau    | $\cdots$       | $\cdots$         | $\cdots$            | $\cdots$      | $\cdots$       | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq359$           | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| HK Tau A    | $\cdots$       | Shoulder         | I14                 | $\cdots$      | $\cdots$       | 14.0(105)     | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} | \leq20$  | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| HP Tau      | $\cdots$       | Shoulder         | I11                 | $\cdots$      | $\cdots$       | 11.0(62)      | $\cdots$               | $\cdots$         | $\cdots$         | $\theta = 30-110, 210-290$        | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| GI Tau      | Ring-Gap       | $\cdots$         | D9/B14$^{*}$        | 9.1(70)       | 14.1(108)      | $\cdots$      | $4.44\pm0.39$          | $0.38\pm0.03$    | $1.12\pm0.01$    | $|\theta - \mathrm{PA} |\leq20$   | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| RW Aur A    | $\cdots$       | Shoulder         | I6                  | $\cdots$      | $\cdots$       | 6.4(39)       | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| T Tau N     | Ring-Gap       | $\cdots$         | D12/B16$^{*}$       | 11.6(81)      | 15.7(109)      | $\cdots$      | $3.88\pm0.43$          | $0.28\pm0.02$    | $1.22\pm0.06$    | $0 \leq    \theta \leq 359$       | case 1   |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DH Tau A    | $\cdots$       | $\cdots$         | $\cdots$            | $\cdots$      | $\cdots$       | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| HN Tau A    | $\cdots$       | $\cdots$         | $\cdots$            | $\cdots$      | $\cdots$       | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} |\leq20$   | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| DK Tau A    | $\cdots$       | Shoulder         | I7                  | $\cdots$      | $\cdots$       | 7.4(58)       | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| RW Aur B    | Central Hole   | $\cdots$         | B6                  | $\cdots$      | 6.4(39)        | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} | \leq 40$ | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
|             | $\cdots$       | Outer Disk-Skirt | I12                 | $\cdots$      | $\cdots$       | 11.8(72)      | $\cdots$               | $\cdots$         | $\cdots$         | $|\theta - \mathrm{PA} | \leq 40$ | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+
| UY Aur A    | $\cdots$       | $\cdots$         | $\cdots$            | $\cdots$      | $\cdots$       | $\cdots$      | $\cdots$               | $\cdots$         | $\cdots$         | $0 \leq \theta \leq 359$          | $\cdots$ |
+-------------+----------------+------------------+---------------------+---------------+----------------+---------------+------------------------+------------------+------------------+-----------------------------------+----------+

: Properties of Disk Structures.

## Definition of Rings, Gaps, and Inflections

![](definition_ringgap.pdf)

From the radial profiles obtained in the previous subsection, we identify characteristic substructures in the profile. We define rings, gaps, and inflections based on the derivative of the radial intensity profile with respect to the radial coordinate. We define this derivative $\mathcal{D}(r)$ as $$\begin{equation}
\mathcal{D}(r) = \frac{1}{I_{\nu}(r)}\frac{d I_{\nu}(r)}{dr}.
\end{equation}$$ The following describes the definition of the disk substructures we consider in this study.

**Ring ($r_{\rm ring}$).** Rings are defined as the local maximum of the radial intensity profile, i.e., $\mathcal{D}(r_{\rm ring}) = 0$ and $\mathcal{D^{\prime}}(r_{\rm ring}) < 0$, where $\prime$ denotes the derivative with respect to $r$. Following the notation of (cite: ALMAPartnership2015), we label the ring features with “B” (Bright) followed by a number indicating their location in astronomical units.

**Gap ($r_{\rm gap}$).** Gaps are defined as the local minimum of the radial intensity profile, i.e., $\mathcal{D}(r_{\rm gap}) = 0$ and $\mathcal{D^{\prime}}(r_{\rm gap}) > 0$. We label the gap features with “D” (Dark) followed by a number indicating the location in astronomical units.

**Inflection ($r_{\rm inf}$).** Inflections are defined as $\mathcal{D}^{\prime\prime}(r_{\rm inf})=0$, $\mathcal{D}^{\prime}(r_{\rm inf})>0$, and $\mathcal{D}(r_{\rm inf}) < 0$. We label the inflections with “I” followed by a number indicating the location in astronomical units. Intuitively, this is a small “dip” in a decreasing profile of radial intensity, as shown in the left panel of Figure [12](#fig:definition_substructre). Such features may be caused by beam smearing of a narrow gap-like structure in a decreasing intensity profile. This feature has been visually identified in previous studies due to numerical difficulties in specifying the higher-order derivative of intensity profiles (e.g., (cite: Cieza2021)). In our analysis, this feature is more rigorously identified using the consecutive local minima and maxima of $\mathcal{D}(r)$ that exist in the region $\mathcal{D}(r)<0$. As shown in the left panel of Figure [12](#fig:definition_substructre), the radial location of the inflection $r_{\rm inf}$ can be determined as the point at which the maximum deviation occurs between the linear line $\ell(r)$ connecting the local minimum and maximum of $\mathcal{D}(r)$ and the intensity profile $I_{\nu}(r)$, $$\begin{equation}
\label{eq:inflection}
r_{\rm inf} = \mathop{\rm argmax}\limits_{r} [\ell(r) - I_{\nu}(r)] ~ \mathrm{subject~to} ~ \ell(r) \geq I_{\nu}(r)
\end{equation}$$ To identify the location of $r_{\rm inf}$, we partially use the $\tt Kneed$[^5], a Python package that identifies the inflection point to fit the data based on Equation [\[eq:inflection\]](#eq:inflection).

### Gap Width and Depth

At the location of gap features, we measure the gap width $\Delta_{\rm I, unit}$, normalized gap width $\Delta_{\rm I}$, and gap depth $\delta_{\rm I}$. To determine the width and the depth of the gap, we first need to define the inner and the outer edges, $r_{\rm in}$ and $r_{\rm out}$, of the gap. In our samples, we find that any gap at $r=r_{\rm gap}$ is associated with a ring at $r=r_{\rm ring,1}$ just outside the gap.

In previous studies (e.g., (cite: Huang2018; Zhang2018)), the location of the outer gap edge $r_{\rm out}$ is defined as the largest value satisfying the criteria $I_{\rm edge}= I_{\nu}(r_{\rm out})$ and $r_{\rm gap} < r < r_{\rm ring}$ and that of the inner gap edge $r_{\rm in}$ is defined as the smallest value satisfying the criteria $I_{\rm edge}= I_{\nu}(r_{\rm in})$ and $r < r_{\rm gap}$. Here, $I_{\rm edge}$ is defined as $$\begin{equation}
I_{\rm edge} \equiv 0.5 \left\{ I_{\nu}\left(r_{\rm ring}\right)+I_{\nu}\left(r_{\rm gap}\right) \right\}.
\end{equation}$$ This definition is illustrated as Case 1 in the middle panel of Figure [12](#fig:definition_substructre).

In some cases, we find that this definition of gap edge locations fails because the brightness inside the gap location is too weak for $r_{\rm in}$ to be well-defined. We consider that there is still a “gap” if there is a local peak at $r=r_{\rm peak} < r_{\rm gap}$. This situation is illustrated in the right panel of Figure [12](#fig:definition_substructre) as Case 2. We define $r_{\rm in}$ and $r_{\rm out}$ as in Case 1 but with $$\begin{equation}
I_{\rm edge} \equiv 0.5 \left\{ I_{\nu}\left(r_{\rm peak}\right)+I_{\nu}\left(r_{\rm gap}\right) \right\}.
\end{equation}$$ We also apply Case 2 when the system has a localized emission at the position of the central star (i.e., inner disk) surrounded by a gap structure. In this case, we set $r_{\rm peak} = 0$ to define the inner and the outer edges of the gap. The targets that have gaps around a central emission are GM Aur (D14), DM Tau (D14), CQ Tau (D12), and RY Tau (D5).

Once we have obtained the location of the gap edges, it is possible to define the width and the depth of the gap. We define the gap width in units of length $\Delta_{\rm I, unit}$ and normalized gap width $\Delta_{\rm I}$ as $$\begin{equation}
\Delta_{\rm I, unit}= r_{\rm out}-r_{\rm in}, \rm ~ and ~\Delta_{\rm I}=\frac{\left(r_{\rm out}-r_{\rm in}\right)}{r_{\rm out}},
\end{equation}$$ respectively. For the gap depth $\delta_{\rm I}$, we define $$\begin{equation}
\delta_{\rm I} = \frac{I_{\nu}\left(r_{\rm ring}\right)}{ I_{\nu}\left(r_{\rm gap}\right)}.
\end{equation}$$ It should be noted that the measurements of the gap depth can be significantly affected by the faint emission at the gap location. Specifically, when the width of the gap is larger than the spatial resolution by a factor of several, the emission at the gap location $I_{\nu}\left(r_{\rm gap}\right)$ can easily reach the noise level. This effect is prominent in three disks: AB Aur (D62), LkCa 15 (D17), and AA Tau (D14). Therefore, we consider these to be upper limits of depth and exclude them from our analyses when we use $\delta_{\mathrm{I}}$.

We have detected 33 gap–ring pairs in 21 disks and have been able to measure the widths, depths, and uncertainties for $90\%$ (30/33) of all gaps. We have failed to accurately measure the properties of three gaps located at very large distances ($r_{\rm gap}>100$ au; GM Aur (D152), CI Tau (D126), and DM Tau (D103)) since the emission at these locations are too faint. While presenting their approximations, we regard them as spatially unresolved gaps and exclude them from our analyses involving depths or widths of the gaps.

Among the gaps with measurements of widths and depths, Case 1 accounts for $80\%$ (27/33), while Case 2 represents $20\%$ (6/33). Out of all the gaps studied, $60\%$ (20/33) show $\Delta_{\rm I, unit}$ being larger than the geometric mean of the effective spatial resolution so they are considered to be spatially resolved. The remaining $40\%$ (13/33) of the gaps have not been fully spatially resolved. Their widths and contrasts appear narrower and lower than the spatially resolved ones, although we should be careful in drawing more quantitative conclusions. The measurements of gap properties are summarized in Table [1](#tab:disk_substructure).

## Categorization of Disk Structures

In the previous Section, we have defined three characteristic axisymmetric structures seen in the radial intensity profiles: rings, gaps, and inflections. The combination(s) of these structures as well as some asymmetric structures appear in actual observations. From the investigations of the morphology of the 43 disks, we have found that the disk substructures can be grouped into nine categories: eight types of axisymmetric structures and asymmetry.

Figure [13](#fig:disk_clasification) presents the flowchart of categorization. We start with three large categories: “Rings-Gaps”, “Inflections”, and “Others”. Then, each of the large categories is subdivided into small groups. Some disks have two or more substructures. The morphological category for each disk is summarized in Table [1](#tab:disk_substructure).

![](flowchart.pdf)

### Rings-Gaps

As mentioned in Section [6.2](#sec:ra_extraction), there is always a ring outside a gap. We denote this pair of a ring and a gap as the “Rings-Gaps” feature. This is subdivided into “Ring Gap”, “Ring-Cavity”, and “Central Hole” depending on the gap width and location. The “Ring-Cavity” is further divided into “Transition Disk” and “Pre-transition Disk”.

**Ring-Gap.** We denote a narrow gap with the width of $\Delta_{\rm I} < 0.5$ as “Ring-Gap”. This is a structure where we observe “a concentric, axisymmetric pattern of alternating intensity enhancements (rings) and depletions (gaps)” as noted by (cite: Andrews2020). This pattern appears most frequently in our sample. We find a total of 24 narrow gap/ring structures in 17 disks. The improvement of spatial resolution by SpM has enabled us to detect 12 gap/ring structures that were not previously identified in the conventional CLEAN images (see Table [1](#tab:disk_substructure)). It is worth noting that the substructure within the T Tau N disk had been reported in our earlier studies (cite: Yamaguchi2021) and ring-gap features in several other disks were also identified using a non-parametric one-dimensional fitting approach with $\tt frank$ (cite: Jennings2022taurus). The consistency or difference in the obtained disk substructure between $\tt frank$ and the SpM approach is described in Appendix [18](#appendix:comparison_other_imaging).

**Ring-cavity.** We use “Ring-Cavity” to denote either a wide gap with $\Delta_{\rm I} > 0.5$ or a ring at $r_{\rm ring} > 10$ au. We further sub-categorize the former as “Transition Disk” (TD) and the latter as “Pre-transition Disk” (PTD). The Ring-cavity structure is present in 12 disks, comprising three TDs and nine PTDs (see Table [1](#tab:disk_substructure)).

All TDs in our sample (CIDA 9A, IP Tau, and UX Tau) show only one ring structure and no additional ring-gap features are found. To further investigate the ring structures in TDs, we measure the ring width by fitting the radial intensity profile with a Gaussian function. We use $\tt optimize.leastsq$ within $\tt Scipy$ that employs the Levenberg-Marquardt algorithm for a nonlinear least-squares problem. We determine the ring width $\Delta_{\rm ring}$ as the FWHM of the best-fit Gaussian function. The widths are $0''.13$ (22 au), $0''.11$ (14 au), and $0''.11$ (15 au) for CIDA 9A, IP Tau, and UX Tau, respectively and the error is at the negligible level with $\pm 0''.01$. All of the ring widths are found to be spatially resolved compared to the effective spatial resolutions (i.e., $\Delta_{\rm ring} > \theta_{\rm eff}$) and, interestingly, the ratio of the ring location to the ring width is $\sim 2$ for all the three TDs.

TD and PTD are conventionally categorized based on the excess emissions in the near-infrared (e.g., (cite: Espaillat2014; Pessah2017)), which is an indicator of the close to the central star. However, our TDs/PTDs do not exactly match with those determined by near-infrared excess. For example, GM Aur and AA Tau are classified as PTD in our study while those are classified as TD from infrared, and vice versa for IP Tau and UX Tau. Here, we have used the TD/PTD classification based on infrared presented in (cite: Francis2020). Such discrepancies may be attributed to different distributions between $\mu$m-size grains (traced by near-infrared observations) and mm-size grains (traced by sub-mm observations), as noted by (cite: Marel2023).

**Central Hole.** We denote disks with a local minimum at the central star and with a small inner ring of $r_{\rm ring} < 10$ au as “Central Hole”. This structure is seen in four disks: DM Tau, UZ Tau E, BP Tau, and RW Aur B. There could be a small-scale inner disk at the central star (e.g., (cite: Perez2018; Hashimoto2021dmtau)), but the interpretation of this structure is difficult due to limited spatial resolutions. We note that the SpM image indicates that the inner ring of UZ Tau E is potentially asymmetric. The emission in the west is $\sim 10\%$ brighter than in the east.

### Inflections

The Inflection feature is subdivided into two groups, “Shoulder” and “Disk Skirt”, based on the presence of adjacent ring features.

**Disk-skirt.** We denote the structure of a combination of an inflection point and a ring that are separated by 40 au or less as “Disk-skirt”. If the inflection point is located inside the ring, we use “Inner Disk-skirt” while if it is outside the ring, we use “Outer Disk-skirt”. The radial intensity profiles with this “Disk-Skirt” feature tend to zero slower than in the case of just a “Ring” as the distance from the ring increases.

We have observed Disk-skirt features in 15 of our targets. Two of them (LkCa 15 and MWC 758) show both the inner and outer Disk-skirt features while the other disks show only outer Disk-skirt features. In addition, visual inspection of the radial intensity profiles at the outer radii of DG Tau (I26) and IQ Tau (I68) show very similar behavior to the outer Disk-skirt although they do not show a clear ring structure. We add these two disks as exceptional cases having outer Disk-skirt. In total, we have observed the Disk-skirt features in $40\%$ (17/43) of all disks, with two disks having inner Disk-Skirt and all 17 disks having outer Disk-skirt. Interestingly, Disk-skirt is found in $70\%(15/21)$ of the large disks while only $10\%(2/22)$ of the small disks have Disk-skirt. The large difference in the number of inner and outer Disk-skirt might indicate that they are actually of different origins. The outer Disk-skirt feature may be created by drifting dust particles that will be trapped in a pressure bump at an inner radius (e.g., (cite: Cieza2021; Leiendecker2022)). The inner Disk-skirt, on the other hand, may just be caused by limited spatial resolution. Two narrow rings that are not spatially resolved could produce a structure that resembles the inner Disk-skirt.

**Shoulder.** We denote the inflections that are not associated with any ring as “Shoulder”, except for DG Tau(I26) and IQ Tau(I68), which are included in the outer Disk-skirt. The number of disks showing Shoulder features amounts to 19, which is $40\%$ (19/43) of our sample. The shoulder features are typically found at $5-40$ au from the central star. Most of the compact disks harbor shoulder features and do not show other disk features in radial intensity profiles. The shoulder feature can be caused by insufficient spatial resolution for narrow and shallow gaps. Therefore, more sensitive and higher spatial resolution observations are needed to judge if the actual structure is gap-like or shoulder-like.

### Other Types

As disk structures that do not fall into either “Rings-Gaps” or “Inflections”, we define “Smooth” and “Asymmetry”.

**Smooth Disk.** We denote disks without rings, gaps, or inflections as “Smooth”. Four ($=9\%$) disks of our 43 samples, V836 Tau, DH Tau A, HN Tau A, and UY Aur A, are categorized into this group. Three out of four of these disks are associated with the primary stars of binary systems and all of them have disk radii less than 40 au. The disks are spatially resolved only by $2-3$ beams even with SpM imaging. Therefore, disk structures, if exist, may have been smeared out.

In the disk around V836 Tau, we see a hint of some substructures. A dual blob-like feature at the center of the disk is seen in the SpM image, whose spatial resolution is improved by a factor of $\sim 3$ compared to the CLEAN image. The peaks of the blobs are at $\sim 0''.03$ from the central star and are only $\sim 2\%$ brighter than the center of the image. This feature could indicate the presence of a small cavity but we conservatively categorize the disk around V833 Tau as “Smooth”.

**Asymmetry.** Finally, we denote “Asymmetry” for disks with asymmetric structures on 2D SpM images. In this paper, we only identify the asymmetric structures with visual inspection since we mainly focus on the structures that appear in azimuthally averaged radial profiles. We identify five disks as having obvious asymmetric structures: AB Aur, CQ Tau, RY Tau, MWC 758, and CIDA 9A. Except for CIDA 9A in the M-type star, they are intermediate-mass stars of the F-A type ($M_{*} = 1.5-2.2~M_{\odot}$). Their disks are of Ring-cavity type in common. We will explore the implications of these substructures in the asymmetric disks in more detail in future investigations by treating each case as an individual study.

# Distribution of Gap Radii

In this Section, we investigate the distribution of the radial location of gaps. Figure [14](#fig:radialgap_location) shows the location of gaps and gap candidates, which are identified as Shoulder, as a function of disk radius $r_{\rm disk}$. We use different symbols for spatially resolved gaps (gap width larger than spatial resolution; 20 gaps), spatially unresolved gaps (gap width smaller than spatial resolution; 13 gaps), and the structures identified as Shoulder (19 in total). The histograms of the locations of all the gaps and candidates are shown in the top right panel of Figure [14](#fig:radialgap_location). We find a broad distribution of gap locations, ranging from 5 au to 100 au from the central host stars, with a notable concentration around 10-20 au. The absence of gaps located at 10 au or less may be due to observational difficulty. Spatial resolution may not be enough to identify small-scale structures at the innermost radii. Moreover, the inner region of the disk is likely to be optically thick so it is hard to observe surface density structures.

The gaps in compact disks (size less than 45 au) are predominantly located at 10-20 au from the central star, but they are all either spatially unresolved or gap candidates. Therefore, again, the statistical properties of gaps in compact disks may be affected by insufficient spatial resolution. The gaps and gap candidates around large disks, on the other hand, show qualitatively different distributions. They are distributed at all the range of 5-100 au from the central star. Interestingly, however, the gap candidates (Shoulders) and the gaps are distributed differently. The gap candidates are mainly at 20-30 au from the central star while the gaps are located either inside the outside of the region dominated by the candidates.

In the middle and bottom panels of Figure [14](#fig:radialgap_location), we dropped the gap candidates (Shoulders) from the plot. We now clearly see the bimodality of gap distribution. The gaps are located either in the inner ($r\lesssim 20$ au) or the outer ($r\gtrsim 30$ au) part of the disk, and the region in between may be considered a “gap desert”. We find that the classification of the disks (discussed in Section [6.3](#sec:categorize_radialdisk)) is different for disks having gaps in the inner region and in the outer region. Disks bearing gaps in the outer region include both Ring-Gap (nine disks) and PTDs (two disks), while $90\%(=7/8)$ of disks having gaps in the inner region are PTDs. The difference in disk types may be connected to the bimodality of clear gaps that can be observed. Weak gaps that may be observed as “gap candidates” may exist all over the disk.

![](RadialGapLocation.pdf)

# Correlation of Disk Substructures

In this Section, we explore the relationships of ring and gap properties. We consider 20 spatially resolved gaps listed in Figure [14](#fig:radialgap_location) and investigate the correlation among their locations of the gaps and the rings associated with them, widths, and depths. We note that it is not possible to obtain reliable measurements of depths for three of the wide gaps (i.e., AB Aur (D62), LkCa 15 (D17), and AA Tau (D14)) so we exclude them when calculating the correlation between the depth and other properties.

## Overview of Correlations

Figure [15](#fig:correlation_matrix) shows the correlations among gap and ring quantities. We also calculate the correlation between quantities of disk substructures and stellar properties or disk size. In this analysis, we have found correlations in (1) the radial positions of gaps and rings, (2) the gap locations and their widths, and (3) the gap widths and depths. Meanwhile, we do not observe a robust correlation ($\rho < 0.3$) between stellar mass and disk substructure properties. We discuss each of the correlations in subsequent sections in more detail.

![](correlation_matrix.pdf)

## Ring and Gap Radii

We investigate the relationship between the radial location of gaps and rings that are associated with the gaps. The left panel of Figure [16](#fig:ring-gap_relation) shows that these two quantities are tightly correlated. There are, however, a few outliers. We find all of the outliers are in the Ring-cavity type (see Section [6.3.1](#sec:ring-gap_feature)). The Pearson correlation coefficient after removing these outliers is $\rho = 0.994$ with the $p$-value falling below the significance threshold ($p$-value $< 0.01$). Bayesian linear regression in a linear-space results in the relation: $$\begin{equation}
\left( \frac{r_{\rm ring}}{\mathrm{au}} \right)= 7.58^{+2.59}_{-2.62} + 1.09^{+0.04}_{-0.04} \left( \frac{r_{\rm gap}}{\mathrm{au}} \right),
\end{equation}$$ with a scatter of $3.65\pm 1.02$ au. For our samples, most of the gaps are located at $>10$ au ($\gg 1.09$ au) from the central star, so we conclude that the rings associated with narrow gaps (not a cavity-like structure) are located at $\sim 10\%$ larger distance from the central star compared to the gap. We need higher spatial resolution data to investigate if this holds for gaps and rings at a few au scales from the central star.

In the right panel of Figure [16](#fig:ring-gap_relation), we show a histogram of the residual of the linear regression model. All the samples used for fitting show residuals less than 10 au. The ring locations of the outliers (not used for fitting), in contrast, exhibit substantial deviations ranging from 10 to 70 au from the model.

![](Rring_Rgap_relation.pdf)

## Gap Width and Gap location

![](Gapwidth_Rgap_relation.pdf)

Figure [17](#fig:gapwidth_rgap_relation) shows the correlation between the gap location and widths. We investigate both the gap width in units ($\Delta_{\rm I,unit}$, left panel) and the normalized one ($\Delta_{\rm I}$, right panel). We exclude the “outliers” in the $r_{\rm ring}-r_{\rm gap}$ correlation and we obtain positive correlation between $\log \Delta_{\rm I,unit}$ and $\log r_{\rm gap}$ ($\rho = 0.62$, $p$-value $= 0.02$) while negative correlation between $\log \Delta_{\rm I}$ and $\log r_{\rm gap}$ ($\rho = -0.79$, $p$-value $>0.01$). Bayesian linear regression in the logarithmic plane results in the relationship $$\begin{equation}
\log\left(\frac{\Delta_{\rm I, unit}}{\mathrm{au}} \right) = 0.47^{+0.27}_{-0.27}+0.37^{+0.16}_{-0.16}\log \left(\frac{r_{\rm gap}}{\mathrm{au}} \right) ,
\end{equation}$$ with a scatter of $0.24\pm 0.12$ dex for the width with units while $$\begin{equation}
\log \Delta_{\rm I} = 0.21^{+0.22}_{-0.23}-0.51^{+0.13}_{-0.13}\log \left(\frac{r_{\rm gap}}{\mathrm{au}} \right),
\end{equation}$$ with a scatter of $0.17\pm 0.05$ dex for the normalized width. If a gap is created by a planet, $\Delta_{\rm I}$ is larger if the mass of the planet in the gap is larger (e.g., (cite: Kanagawa2015; Zhang2018)). The negative correlation between $\Delta_{\rm I}$ and $r_{\rm gap}$ may suggest that the planet mass is low at the outer radii. We discuss further the implication of planet formation in Section [9.3](#sec:inferred_planetmass).

## Gap Width and Gap Depth

Figure [18](#fig:gapwidthdepth_relation) presents the distribution of gap widths and depths on a logarithmic scale. We use $\delta_{\rm I}-1$ rather than $\delta_{\rm I}$ for gap depth so that the value is zero when there is no gap as in the case of $\Delta_{\rm I}$, and we consider two measurements of gap width: one with units $\Delta_{\rm I, unit}$ and the normalized one $\Delta_{\rm I}$. We find a significant positive correlation ($\rho\ge 0.5$, $p-$value $\le 0.02$) between gap width and depth. Interestingly enough, the correlations are even stronger ($\rho>0.7$, $p-$value $<0.01$) if we restrict the gaps in the outer region with $r_{\rm ring}>30$ au. The inner region samples ($r_{\rm ring}<20$ au) also indicate some correlation. However, the $p-$value of $\geq 0.05$ is not small enough due to the small sample size and we do not further explore a trend for the gaps at the inner region. The Bayesian linear regression in the logarithmic plane is performed for the full sample and the samples at outer radii. The linear model is given by $$\begin{equation}
\label{eq:SL_gapwidth_depth}
\log \Delta = \mathcal{A} + \mathcal{B} \log (\delta_{\rm I}-1) + \varepsilon,
\end{equation}$$ where $\Delta$ is either $\Delta_{\rm I, unit}$ or $\Delta_{\rm I}$, $\mathcal{A}$ is the intercept, $\mathcal{B}$ is the slope, and $\varepsilon$ is the Gaussian scatter along the vertical axis. The regression parameters and correlation coefficients are summarized in Table [\[table:gapwidthdepth_relation\]](#table:gapwidthdepth_relation).

**Note**. Linear regression model is given by Equation [\[eq:SL_gapwidth_depth\]](#eq:SL_gapwidth_depth). The values quoted for $\mathcal{A}$ (intercept) and $\mathcal{B}$ (slope) are the medians of their posterior distribution, and the uncertainties are the $68\%$ confidence interval. $\sigma$ represents the standard deviation of Gaussian scatter around the linear regression. $\rho$ and $p-$val are the Pearson correlation coefficient and the corresponding $p-$value, respectively.

![](GapWidthDepth_Relation.pdf)

# Discussion

## Remnants of Dust Envelope

In Section [5.1](#sec:totalflux_comparison), we find that the flux density observed with single-dish telescopes may be $\sim 20\%$ larger than that with ALMA. This excess may be due to the emission at the envelope scale, which is resolved out in interferometric observations. (cite: Federman2023) studied the 0.9 mm continuum flux density of Orion protostars using ALMA (disk-scale) and Atacama Compact Array (ACA; envelope-scale). The survey revealed that the ALMA/ACA flux ratio shows an evolutionary trend. The ratio is below 0.5 for Class 0 protostars, which are predominantly envelope-dominated, whereas it ranges from 0.5 to 1.0 for Class I stars. This indicates that there is a transition from envelope-dominated to disk-dominated phase at the Class 0/I stage, and our derived flux ratio of $\sim 0.8$ for Class II disks is also in line with this evolutionary sequence.

We estimate the envelope mass $M_{\rm env}$ (gas + dust) from the envelope flux density $F_{\nu,\rm env}$, which is the flux density of IRAM 30m subtracted by that of ALMA. Under the assumption that the envelope is isothermal and optically thin, the total mass is given by:

$$\begin{equation}
M_{\rm env} = \frac{F_{\nu,\rm env} d^{2}}{\kappa_{\nu} B_{\nu}(T)},
\end{equation}$$

where $d$ is the distance toward the source, $B_{\nu}(T)$ is the Planck function at the dust temperature $T_{\rm dust}$ and $\kappa_{\nu}$ is the opacity per unit gas mass at the observed frequency. Assuming that the gas and dust are at the same temperature of $T = 15$ K (cite: Federman2023) and the opacity of $\kappa_{\nu} = 0.023$ cm$^{2}$ g$^{-1}$ (cite: Beckwith1991), average envelope masses over the 21 single-star targets is derived to be $M_{\rm env} = 10 \pm 8$ $M_{\rm Jup}$. This estimate has an uncertainty of a factor of several due to the assumed opacity values (e.g., $\kappa_{\nu} = 0.009$ cm$^{2}$ g$^{-1}$; (cite: Ossenkopf1994)) but is an order of magnitude smaller than the envelope masses of Class I YSOs (cite: Federman2023). Yet, our results indicate that there is still enough material to form Jupiter-mass planets if all the envelope material accretes onto the disk.

The presence of envelope remnants around the disks with typical ages of $1-5$ Myr (cite: Long2019) poses a question on conventional models that predict that most envelope materials dissipate within $0.5-1.0$ Myr since the onset of envelope collapse (cite: Young2005; Dunham2010). One possible explanation for the remaining envelope is the ashfall phenomenon (cite: Wong2016; Tsukamoto2021; Tsukamoto2023). In this scenario, an active outflow driven by a magnetic field entrains the dust particles grown to $\gtrsim 0.1$ mm that reside in the inner region of the disk. The dust particles are scattered all over at the envelope scale of $\sim 1000$ au and then fall back to the disk to replenish it with large grains. The grown dust within the envelope remnants can still be present during the Class II stage. The presence of grown dust in envelopes of Class 0/I stages has been suggested by several studies (cite: Kwon2009; Chiang2012; Miotello2014; Galametz2019). To identify the grown dust even in the envelope of the Class II stage, the multi-band ACA observations, along with spectral energy distribution fitting (cite: Li2017), would be desired.

## Possible Origin of Gap Formation

![](compare_planetdiskmodel.pdf)

![](estimate_planetmass.pdf)

In Section [8.4](#sec:gap_widthdepth_relation), we have found that the gap width is correlated with the gap location and the depth. Intriguingly, we find that the derived power-law index of $\mathcal{B}={0.23 \pm 0.09}$ in the $\delta_{\rm I}-\Delta_{\rm I}$ relationship (Equation [\[eq:SL_gapwidth_depth\]](#eq:SL_gapwidth_depth)) for the outer region sample (gaps at $30-100$ au from the central star) is consistent with the power-law indices predicted by planet-disk interaction models, which are 0.25 in (cite: Kanagawa2015; Kanagawa2016) and $\sim 0.23$ in (cite: Zhang2018).

In comparison with other gap-opening mechanisms, there is a theoretical prediction given by secular gravitational instability (SGI; (cite: Takahashi2014; Tominaga2019)). SGI generates annular ring structures for producing planetary embryos even at large orbital separations ($r>10$ au). (cite: Tominaga2019) proposed that the narrowness of observable dust ring systems can be explained by SGI. When the distance between the peaks of adjacent rings $\Delta r_{\rm ring}$ normalized by the gap scale height $h_{\rm gap}$ at the gap location falls below a threshold of 3.6 (i.e., $\Delta r_{\rm ring} / h_{\rm gap} < 3.6$), SGI becomes a plausible mechanism for shaping these rings. We compute $h_{\rm gap}$ using the dust temperature $T_{\rm d}(r)$ assumed by $$\begin{equation}
\label{eq:disk_temperature}
T_{\rm d}(r)=\left(\frac{\phi L_{*}}{8 \pi r^{2} \sigma_{\rm SB}}\right)^{1 / 4},
\end{equation}$$ where $\sigma_{\rm SB}$ is the Stefan-Boltzmann constant, $L_{*}$ is the stellar luminosity (given in Table [\[tab:stellar_properties\]](#tab:stellar_properties)), $\phi$ and is the flaring angle (cite: Chiang1997; Dullemond2001). The flaring angle is assumed to be constant at 0.02 except for DM Tau and GM Aur, for which we use 0.05 since low $\phi$ results in the dust temperature below the observed brightness temperature. Examining the double (or multiple) gaps/rings in eight disks (see Table [1](#tab:disk_substructure)), the sources except for GO Tau do not appear to be induced by the SGI model, as the derived ratios range from 4.0 to 14.9 with an average of 8.6. The GO Tau disk has three narrow gaps/rings (D56/B72, D89/B99, and D105/B116), and their derived ratios (3.6 for B72-B99 and 1.8 for B99-B116) are either equal to or below the threshold. It should be noted that these gap structures of D89 and D105 (and perhaps nearby areas) in GO Tau are not fully spatially resolved ($\Delta_{\rm I, unit} \leq \theta_{\rm eff}$), and it is too early to conclude that they are caused by SGI. Observations with higher spatial resolutions ($\theta < 0''.1$) are needed to determine the origin of these narrow gaps in the GO Tau disk.

The comparison with other gap-opening mechanisms, such as dust processes including ice lines and streaming instability, remains unclear because their theoretical predictions on gap morphology have not yet been established. Therefore, we focus our attention on the comparison of our results with the predictions of the planet-disk interaction model proposed by (cite: Zhang2018).

The planet-disk interaction model outlined in (cite: Zhang2018) predicts the relationship between the gap depth $\delta_{\rm I}$ and normalized width $\Delta_{\rm I}$ in the surface brightness profile $I_{\nu}(r)$. The relationship can be derived from Equations (22)-(24) of (cite: Zhang2018) and reads $$\begin{eqnarray}
\label{eq:zhang_theory}
\Delta_{\mathrm{I}}=\mathrm{A}
\left[
0.635
\left(\frac{h_{\mathrm{gap}}}{r_{\mathrm{gap}}}\right)^{2.63}
\left(\frac{\alpha_{\mathrm{vis}}}{10^{-3}}\right)^{0.07} \left(\frac{\delta_{\mathrm{I}}-1}{\mathrm{C}}\right)^{\frac{1}{D}} 
\right]^{\mathrm{B}},
\end{eqnarray}$$ where $h_{\mathrm{gap}} / r_{\mathrm{gap}}$ and $\alpha_{\rm vis}$ indicate aspect ratio at a planet location and viscous parameter, respectively. The constants $A$, $B$, $C$, and $D$ depend on the gas surface density $\Sigma_{\rm g}$ and the maximum grain size $s_{\rm max}$.

Figure [19](#fig:compare_planetdiskmodel) shows the comparison between the observations (for the spatially resolved gap samples) and the model prediction on the $\Delta_{\rm I}- \delta_{\rm I}$ relation. We consider the cases with gas surface density $\Sigma_{\rm g}$ of 10 and 100 $\rm g~cm^{-2}$ (see also Section [9.3](#sec:inferred_planetmass)) and various disk aspect ratios at the location of gap $h_{\rm gap}/r_{\rm gap}$ from 0.05 to 0.1. We fix the maximum grain size $s_{\max}$ to be 0.1 mm (DSD1 model for (cite: Zhang2018)) based on ALMA observations by (cite: Bacciotti2018) and the viscous parameter $\alpha_{\rm vis}$ to be $10^{-3}$. In this case, $\Delta_{\rm I}$ scales with $(\delta_{\rm I}-1)^{0.25}$.

We find that $65\%$ (11 out of 17) of the total sample falls in the range predicted by the model. Nine of them are gaps located in the outer region ($r_{\rm gap}>30$ au), while only two (DM Tau (D14) and CI Tau (D16)) are located in the inner region. Four of the six gaps that deviate from the model are wide ($\Delta_{\rm I} > 0.6$; MWC 758 (D15), GM Aur (D14), CQ Tau (D12), and RY Tau (D5)). A possible origin of these gaps may be a giant planet or a brown dwarf, which is out of the range of the model by (cite: Zhang2018), in a disk (cite: Ubeira2019; Calcino2020).

The model actually has large uncertainty in the parameter space when a Jupiter-mass planet opens a very wide gap ($\Delta_{\rm I} \sim 1$; see (cite: Zhang2018)) and therefore more refined model of planet-disk interaction is desired. When a planet is sufficiently massive ($>3~M_{\rm jup}$) and opens a wide gap, it may induce eccentricity in the gap edge (cite: Kley2006; Tanaka2022). Such effects may need to be taken into account to construct models that are applicable to a wider range of planet mass and disk parameters.

Two adjacent gaps in the AA Tau disk (D66 and D81) show a narrower gap width than the range of model prediction. This disk has a large cavity feature (PTD) and narrow rings similar to the other disk around HD 169142 (cite: Perez2019). One possible interpretation of this particular structure is the presence of a super-Earth planet ($\sim 10~M_{\rm \oplus}$) that induces multiple gaps in a low-viscosity ($\alpha_{\rm vis}<10^{-4}$) environment (cite: Dong2018_multigap). The widths of the gaps are narrower than those models predicted in (cite: Zhang2018), which is qualitatively consistent with observations. We note that such a low-viscous model is outside the scope of the models in (cite: Zhang2018).

## Inferred Planet Mass in Gap Structure

For the 11 gaps that lie within the range of the planet-disk interaction model, we derive the planet mass. We follow the methods outlined in (cite: Zhang2018), and use the following empirical relationship between the planet mass and the normalized gap widths $\Delta_{\mathrm{I}}$: $$\begin{eqnarray}
\label{eq:zhang_theory_gapwidth}
\frac{M_{\mathrm{p}}}{M_{*}} = 0.115 \left(\frac{\Delta_{\mathrm{I}}}{A}\right)^{1 / B} \left(\frac{h_{\mathrm{gap}}}{r_{\mathrm{gap}}}\right)^{0.18} \left(\frac{\alpha_{\mathrm{vis}}}{10^{-3}}\right)^{0.31},
\end{eqnarray}$$ where the parameters $A$ and, $B$ are the parameters that appear in Equation [\[eq:zhang_theory\]](#eq:zhang_theory) and tabulated in (cite: Zhang2018). The three physical parameters, the averaged gas surface density $\Sigma_{\mathrm{g}}$, the aspect ratio at the gap location $h_{\mathrm{gap}}/r_{\mathrm{gap}}$, and the maximum grain size $s_{\mathrm{max}}$ are needed to determine $A$ and $B$. We assume $s_{\mathrm{max}}$ to be 0.1 mm as stated in Section [9.2](#sec:origin_gapformation).

To estimate $\Sigma_{\mathrm{g}}$, we use the relationship between $\Sigma_{\mathrm{g}}$ and $\Sigma_{\mathrm{d}}$ presented in Figure 18 of (cite: Zhang2018), where $\Sigma_{\mathrm{d}}$ is the averaged dust surface density taken from 1.1 to 2.0 $r_{\rm gap}$. To obtain $\Sigma_{\mathrm{d}}$, we derive the radial dust surface density profile $\Sigma_{\mathrm{d}}(r)$ using the simple radiative transfer equation $\Sigma_{\mathrm{d}}(r)=-\ln \left\{ 1-I_{v}(r) / B_{v}[T_{d}(r)] \right \} / \kappa_{v}$, where $B_{\nu}$, $T_{\rm d}(r)$, and $\kappa_{\nu}$ denote the Planck function, the dust temperature in Equation [\[eq:disk_temperature\]](#eq:disk_temperature), and the dust absorption opacity, respectively. The opacity $\kappa_{\nu}$ is assumed to be $0.43~\mathrm{cm}^{2}~\mathrm{g}^{-1}$ which is the value of DSHARP opacity model (cite: Birnstiel2018) with $s_{\mathrm{max}} = 0.1$ mm at $\lambda=1.3$ mm. With $T_{\mathrm{d}}(r)$, we can compute the disk aspect ratio at the gap location $h_{\mathrm{gap}}/r_{\mathrm{gap}}$ as well as the dust surface density. The values of planet mass and disk physical parameters ($h_{\mathrm{gap}}/r_{\mathrm{gap}}$, $\Sigma_{\mathrm{d}}$, $\Sigma_{\mathrm{g}}$, and $M_{\mathrm{p}}$) are summarized in Table [\[tab:estimate_planetmass\]](#tab:estimate_planetmass).

All of our estimates of planet mass for the eleven gaps are in the range of $\sim$Neptune to $\sim$Jupiter mass. The derived planet mass does not vary much if we change the viscosity parameter $\alpha_{\rm vis}$ from $10^{-4}$ to $10^{-2}$. Figure [20](#fig:estimate_planetmass) shows the distribution in the plane of planet mass versus orbital radius. Interestingly, Saturn- to Jupiter-mass planets seem to be expected in the inner region ($r\sim 10$ au) and the Neptune-mass planets are in the outer region ($r\sim 40-100$ au). This trend is consistent with the results obtained for DSHARP samples that consist of bright and large disks (cite: Zhang2018).

We note that (cite: Zhang2023) reanalyzed the continuum datasets of (cite: Long2019) and estimated planet masses for single-star systems within the Taurus-Auriga region. They used parametric fitting of azimuthally averaged visibilities to identify gaps and rings and estimated the planet masses using the same methods as ours. The measurements of $\Delta_{\rm I}$ for eight large disks in their analysis are consistent with ours within the uncertainties of 0.1 to 0.2, while the number of the gap/ring in GO Tau and DL Tau disks are not consistent with our results. This is probably due to the difference in the methods of ring/gap identification. We do not assume any prescribed function for gap profiles while we work in the image plane rather than the visibility plane. The qualitative results of planet mass distribution, that is, larger mass for smaller orbital distance, are consistent in both works.

## Implication of planet formation

The inferred planet mass for the eleven gaps is in the range of $\sim$Neptune to $\sim$Jupiter mass. The Saturn- to Jupiter-mass planets seem to be located in the inner region ($r\sim 10$ au), while the Neptune-mass planets are in the outer region ($r\sim 40-100$ au). As shown in Figure [20](#fig:estimate_planetmass), this distribution is similar to the architecture of our Solar System, while the orbital radii of the inferred planets in protoplanetary disks are larger than those of the planets in our Solar System. The formation of giant planets at large orbital radii suffers from the problem of timescale in the traditional core accretion scenario. This is a bottom-up framework in which a planetary embryo of a few Earth masses accretes surrounding gas to form a gas giant (e.g., (cite: Mizuno1980; Pollack1996; Ida2013)). The planetary embryo formed at $5-10$ au from the central star can be massive enough to form a gas giant (e.g., (cite: Helled2014)). However, this process takes longer than the disk lifetime when planets are formed at larger orbital radii (e.g., (cite: Rafikov2004; Levison2010)). The pebble accretion scenario has been proposed as a way to solve the issue (e.g., (cite: Lambrechts2012)) but numerical simulations still show that this mechanism does not really produce the cold giant planets (Neptune-Jupiter masses) at larger orbital radii (cite: Bitsch2015).

The gravitational instability scenario is a top-down framework that can potentially form gas giants at large radii from a massive disk (e.g., (cite: Vorobyov2013)). However, we do not see conspicuous asymmetric structures that indicate the presence of turbulence due to instability. Another possible scenario is the combination of the ashfall phenomenon that replenishes grown dust into the large radii (see Section [9.1](#sec:envelope_remnants)) and subsequent SGI (e.g., (cite: Takahashi2016)). This may qualitatively explain the annular ring/gap formation by the cold giant planet at the large radii (cite: Tsukamoto2021). However, the distribution of rings and gaps is not consistent with the prediction of those predicted by SGI (see Section [8.4](#sec:gap_widthdepth_relation)). The distribution of rings during the formation of planets and that of already formed planets may be different due to, for example, planet-planet interaction. The prediction of this scenario should be explored in more detail.

We note that the inferred population of planets may actually be different when we interpret that the shoulder feature, which is a candidate for a weak gap structure is formed by a lower-mass planet. The shoulder features appear at many places in the disks; this might indicate the presence of an additional population of planets distributed all over the orbital radii from 5 to 40 au (see Figure [14](#fig:radialgap_location)).

The upper limit of the planet mass for the 21 shoulder features can be estimated by the empirical relationship between planet mass and gap width (Equation 5 in (cite: Kanagawa2016)), $$\begin{equation}
\label{eq:upper_planetmass}
\frac{M_{p}}{M_{*}}=0.19\left(\frac{\Delta_{\rm I, unit }}{r_{\rm{p }}}\right)^{2}\left(\frac{h_{\rm p}}{r_{\rm p}} \right)^{1.5} \left(\frac{\alpha_{\mathrm{vis}}}{10^{-3}}\right)^{0.5}.
\end{equation}$$ Here, we assume that the dust is well coupled with the gas. This gives a large upper limit since dust particles tend to move to the pressure maximum at the edges of the gap. We estimate the upper limit of the planet mass by assuming that this gap width to be smaller than the effective spatial resolution, with $\Delta_{\rm I, unit}\leq\theta_{\rm eff}$ and $r_{\rm p} = r_{\rm inf}$. We fix the disk scale height $h_{\rm p}/r_{\rm p}$ and viscous parameter $\alpha_{\mathrm{vis}}$ to be 0.05 and $10^{-3}$, respectively, and apply this formula to the 21 shoulder features. We have obtained the average upper limit of $M_{p} = 0.6\pm0.5~M_{\rm Jup}$ at the spatial resolutions of $66\pm32$ mas, where the errors represent standard deviations. This suggests that Neptune (or lower) mass planets may exist anywhere in the disk but the gaps in the inner part of the disks are not clearly detected.

It may be possible to form low-mass planets through core accretion or pebble accretion without suffering timescale problems. The prevalence of planets with masses lower than Jupiter might indicate that these are the main mechanisms of planet formation. The giant planets at larger orbital radii may be formed in exceptionally massive disks and/or there might be other (relatively minor) mechanisms to accelerate massive planet formation.

To verify this argument, it is crucial to conduct observations that can measure the shape of the candidates of the weak gap structures more accurately. From Equation [\[eq:upper_planetmass\]](#eq:upper_planetmass), we need an extremely high resolution of $24 \pm 17$ mas to resolve the gaps carved by Neptune mass planets, respectively. Long baseline observations at higher frequencies than the current Band 6 observations (e.g., (cite: Asaki2020)) may provide new insights, and it is necessary to have better gap models that take into account optical depth effects that are crucial in analyzing high-resolution observations.

# Conclusion

We present ALMA 2D Super-resolution imaging of Taurus-Auriga protoplanetary disks for probing statistical properties of disk substructures. We use archival ALMA Band 6 continuum data from 43 disks, comprising 39 disks around Class II objects and four disks around Herbig Ae stars. To enhance the fidelity and spatial resolution of the images, we employ a novel 2D super-resolution imaging technique based on sparse modeling (SpM). Our main findings with the SpM images are summarized as follows:

1.  All dust disks are successfully spatially resolved. By applying super-resolution imaging, 18 out of 43 targets show the improvement of spatial resolution by a factor of two to three compared to the conventional CLEAN method. All but three images show spatial resolution better than $0''.1$, with the highest achieved resolution reaching $0''.02$. The radii of the disks range from 8 to 238 au with a median radius of 45 au.

2.  We find two empirical relationships on spatial resolution improvement. One is the relationship with the image SNR and the other is with the disk size normalized by the synthesized beam size. The improvement of spatial resolution is more significant for higher SNR data or more compact disks whose size is close to the beam size.

3.  We assess the performance of SpM and CLEAN imaging by investigating how well the Fourier transform of the reconstructed images can fit the observed visibility. SpM produces a better fit in $95\%$ of cases (40/42). The remaining $5\%$ (2 cases) show comparable performance between SpM and CLEAN.

4.  The fidelity of SpM images is assessed with the “cross-check method” (cite: Yamaguchi2020), wherein a comparison is made between the CLEAN image derived from long baseline observations and the SpM image generated from short baseline observations. Employing three bright and large disks for the evaluation, we confirm that the image reconstructed from the shorter-baseline data using the SpM matches well with that obtained by the longer-baseline data using CLEAN. However, we note that SpM imaging can produce artificial features such as clumps and speckles on an extended faint emission, especially for disks with the brightest emission in the central part surrounded by the extended area of faint emission.

5.  The flux densities observed with the IRAM 30m single-dish telescope are $\sim 20\%$ larger than that with ALMA. This discrepancy may be accounted for as the contribution from the emission at the envelope scale surrounding the star and disk system. It is indicated that there are still enough materials to form Jupiter-mass planets if all the envelope material accretes onto the disk eventually.

6.  We confirm the correlation between millimeter luminosity and the disk size $L_{\rm {mm}} \propto r_{\rm {disk}}^2$ on the analysis of image domain, which is suggested based on the 0.9 mm data of disks in Taurus-Auriga-Ophiuchus regions (cite: Tripathi2017; Hendler2020). The correlation is improved by $\sim10\%$ if the luminosity is re-scaled by the inclination angle.

7.  We identify three characteristic structures in the azimuthally averaged radial intensity profiles: rings, gaps, and inflections. The combination(s) of these structures as well as some asymmetric structures appear in actual observations. From the investigations of the morphology of the 43 disks, we suggest nine categories of disk morphology (Figure [13](#fig:disk_clasification)): eight types of axisymmetric structures and asymmetry.

8.  We find the bimodality in the distribution of gaps whose width and depth are measurable. The gaps are located either in the inner ($r\lesssim 20$ au) or the outer ($r\gtrsim 30$ au) part of the disk. We find that the classification of the disks is different for disks having gaps in the inner region and in the outer region. The difference in disk types may be connected to the bimodality of the gap distribution.

9.  All the gaps have a ring outside of them. We find correlations in the properties of gaps and rings that are associated with gaps. The correlations are in (1) the radial positions of gaps and rings, (2) the gap locations and their widths, and (3) the gap widths and depths. Meanwhile, we do not observe a robust correlation between stellar mass and disk substructure properties.

10. The power-law index in the correlation between the gap depth $\delta_{\rm I}$ and normalized gap width $\Delta_{\rm I}$ is of $0.23 \pm 0.09$ for the outer region sample ($r\gtrsim 30$ au). This is consistent with the power-law indices predicted by planet-disk interaction models (cite: Kanagawa2015; Kanagawa2016; Zhang2018).

11. We estimate the planet mass for each gap with clear measurements of depths and widths, assuming that these gaps are formed by planet-disk interaction. The messes of putative planets are in the range of $\sim$Neptune to $\sim$Jupiter mass. Saturn- to Jupiter-mass planets seem to be expected in the inner region ($r\sim 10$ au) and the Neptune-mass planets are in the outer region ($r\sim 40-100$ au). Questions remain open about the formation of such cold giant planets.

12. We note that the inferred population of planets may actually be different when we interpret that the shoulder features, which are a candidate for weak gap structures, are formed by lower-mass planets (Neptune mass or lower). The shoulder features appear at many places in the disks and therefore, our results indicate that there is an additional population of planets distributed all over the orbital radii from 5 to 40 au.

The authors thank the anonymous referee for all of the comments and advice that helped improve the manuscript and the contents of this study. The authors thank Sai Jinshi for valuable discussions, and Takahiro Ueda for giving us the ALMA data of CW Tau. This work was financially supported by JSPS KAKENHI Grant Numbers 18H05441,18H05442, 20H01951, and 23K03463. T.M. is supported by Yamada Science Foundation Overseas Research Support Program. N.H. acknowledges support from the National Science and Technology Council (NSTC) of Taiwan with grant NSTC 111-2112-M-001-060. This study uses the following ALMA data: 2015.1.00889.S, 2019.1.00579.S, 2017.1.01151.S, 2018.1.01230.S, 2016.1.01164.S, 2016.1.01370.S, 2018.1.01631.S, 2015.1.01207.S, 2013.1.00498.S, 2018.1.01755.S, 2018.1.01255.S, 2018.1.00945.S, 2013.1.01070.S, 2016.1.01205.S, 2018.1.01829.S, 2013.1.00105.S, 2016.1.00724.S, 2017.1.00940.S, $2016.\mathrm{A}.00026.\mathrm{S}$ 2017.1.01404.S, 2017.1.01460.S, 2015.1.01268.S, 2016.1.00846.S, 2019.1.01108.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. Data analysis was in part carried out on the multi-wavelength data analysis system operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan. This study used data from the European Space Agency (ESA) mission $\it Gaia$ (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the $\it Gaia$ Multilateral Agreement.

# Software

AnalysisUtilities (<https://casaguides.nrao.edu/index.php?title=Analysis_Utilities>), Astropy (cite: Astropy2022), CASA (cite: CASA2022), kneed (<https://github.com/arvkevi/kneed>), Linmix (cite: Kelly2007), matplotlib (cite: Hunter2007), PRIISM (cite: Nakazato2020), SciPy (cite: Virtanen2020), NumPy (cite: Harris2020)

# Disk Size and Total Flux Density

We use the curve of growth method (e.g., (cite: Ansdell2016)) to measure the dust disk radius $r_{\rm disk}$ on each SpM image. We first derive the inclination and position angle of each disk on the image domain. For disks showing clear ring structures in the outer region, we fit the shape of the ring with an ellipse. For disks that do not show clear ring structures or with low SNR for ellipse fitting, we fit the surface brightness distribution around the central star with an elliptical Gaussian function. The measurements of the inclination and position angle for each source, as well as the methods to derive them listed in Table [\[tab:stellar_properties\]](#tab:stellar_properties). The average of measured disk inclination is $42^{\circ} \pm 15^{\circ}$. We deproject the images to produce the face-on view using the inclination and the position angle. Then, we define the incremental flux density $F_{\nu}(r)$ from the radial surface brightness distribution $I_{\nu}(r)$: $$\begin{equation}
  F_{\nu}(r)= 2 \pi \int_{0}^{r} I_{v}\left(r^{\prime}\right)  r^{\prime} \mathrm{d} r^{\prime},
\end{equation}$$ where the total flux density $F_{\nu}$ is the limiting value of $F_{\nu}(r)$ at $r\to\infty$. In practice, we use successively larger photometric apertures to obtain $F_{\nu}(r)$ and find the values where $F_{\nu}(r)$ becomes constant. The disk radius $r_{\rm disk}$ is then measured by $0.95~F_{\nu} =  F_{\nu}(r)$. We estimate the uncertainty $\sigma_r$ of the disk radius using the effective spatial resolution. We assume $\sigma_{\mathrm{r}}=\left\langle\theta_{\mathrm{eff}}\right\rangle /2 \sqrt{2 \ln 2}$, where $\left\langle\theta_{\mathrm{eff}}\right\rangle$ indicates the geometric mean of the spatial resolution. The derived disk radii are summarized in Table [\[tab:stellar_properties\]](#tab:stellar_properties).

# Improvement of Spatial Resolution by Sparse Modeling

![](radialvisibilityprofile_ref.pdf)

![](resolutionratio_noiseratio.pdf)

Figure [21](#fig:radialvisprofile) shows azimuthally averaged radial visibility profiles of two disks of different sizes: T Tau N and DL Tau. The data of the compact disk T Tau N show consistently high SNRs of $\gtrsim10$ up to the longest baseline. SpM is particularly effective in improving spatial resolution in such cases, and indeed the effective spatial resolution is $30\%$ less than the CLEAN beam size in the case of T Tau N observations. On the other hand, the data of the large disk DL Tau show low SNRs of less than 10 at baselines longer than $\gtrsim \rm 1~M\lambda$, mainly due to the low visibility amplitudes ($\lesssim1$ mJy). In this case, the SpM model data tend to deviate from the observed data at long baselines, and we obtain a moderate improvement in spatial resolution. The effective spatial resolution is $70\%$ of the CLEAN beam size for DL Tau. This behavior can be attributed to the TSV term in the SpM equation (cite: Yamaguchi2020). This suppresses small-scale rapid spatial variations in the image and thus avoids over-fitting the visibility data, while the spatial structure is smeared by the TSV term. Therefore, the improvement in spatial resolution is moderate for low SNR data at large $uv$ distances.

# Evaluation of Noise Levels in Images

We investigate the relationship between the noise level of the images and the improvement of the spatial resolution. As a measure of noise levels, we use the detection threshold $I_{\rm DT}$ for SpM images and the RMS noise level $\sigma_{\rm cl}$ for CLEAN images. We note that the two measurements have different definitions: $I_{\rm DT}$ is the maximum intensity on the emission-free area, while $\sigma_{\rm cl}$ is the RMS value in the emission-free area (see Table [\[tab:fullsample\]](#tab:fullsample) for actual values for each target). The reason why we do not use the RMS noise in the SpM images is the non-negative constraints in the imaging processes. The SpM image has only positive intensity in the off-source area, and its noise distribution is biased towards the positive side with a longer tail than that of a Gaussian distribution (see Figure 6 in (cite: Yamaguchi2020)).

Figure [22](#fig:resolutionratio_noiseratio) shows the relationship between the resolution ratio (SpM/CLEAN) and its noise ratio ($I_{\rm DT}/\sigma_{\rm cl}$). We find a clear trend of decreasing resolution ratio as increasing noise ratio in logarithmic space (Pearson correlation coefficient $\rho = -0.88$, $p$-value $< 0.01$). Using Bayesian linear regression, this trend can be described as $$\begin{equation}
\label{eq:resolution_snr}
\log \left(\frac{\theta_{\rm eff}/\theta_{\rm cl}}{\%}\right)= (2.08\pm 0.03) - (0.31\pm0.03) \log \mathrm{ \left(\frac{I_{\rm DT}}{\sigma_{\rm cl}} \right)}
\end{equation}$$ with a scatter of $0.062\pm0.004$ dex. This indicates that the detection threshold of SpM images $I_{\rm DT}$ strongly depends on the resolution ratio: $I_{\rm DT} \propto (\theta_{\rm eff}/\theta_{\rm cl})^{-3}$.

With the data sample in this study, we find that the brightness distribution in the emission-free area of SpM images is similar to that of positive values in the CLEAN images. This suggests that the brightness distribution in SpM images consists of real dust emission and artificial positive noise patterns. Assuming that any noise can be characterized as a fine structure significantly smaller than the spatial resolution, the noise intensity (or $I_{\rm DT}$) expressed in a unit of $\rm Jy~arcsec^{-2}$ should increase with improved spatial resolution. We see that the situation is reflected in the above relationship.

Here we perform a sensitivity calculation using the point source injection method to determine the correspondence between $I_{\rm DT}$ and $\sigma_{\rm cl}$. We focus on the T Tau data, where the noise ratio ($I_{\rm DT}$/$\sigma_{\rm cl} \sim 100$) is the highest in our sample. We first inject a point source into the observed visibility of T Tau, setting the total flux of this point source to $100\sigma_{\rm cl}$ (4.0 mJy) and locating it at $0''.6$ north of the phase center. We then reconstruct the visibility data in both the SpM and CLEAN images and measure the peak ($I_{\rm p}$) of the reconstructed point source structure. The image sensitivity results show that $I_{\rm p, spm} / I_{\rm DT} = 40$ and $I_{\rm p, cl} / \sigma_{\rm cl} = 100$. Given the SNR relationship of $(I_{\rm p, cl} / \sigma_{\rm cl}) = X (I_{\rm p, spm} / I_{\rm DT})$, the factor $X$ is 2.5, indicating that the point source sensitivity of SpM imaging can be worse by up to several factors. For the T Tau N data, $(I_{\rm DT} / \sigma_{\rm cl})\sim100$, but the peak intensity of the point source in SpM is larger by a factor of $\sim 40$ probably due to the improvement in spatial resolution. Therefore, the point source sensitivity is not as bad as a factor of 100.

# Radial Visibility Profile

We describe methods to derive an azimuthally averaged visibility profile using a reconstructed image (e.g., an SpM image, a CLEAN model, and a CLEAN image) and to evaluate the goodness of fit with the reduced $\chi^{2}$.

In a preprocessing step, we set the observed visibility data $O$ by applying full-channel averaging (i.e., one channel per spectral window) to all spectral windows in the self-calibrated visibility data. Next, we obtain the model visibility data $M$ in the same $uv$ sampling as the observations from the Fourier transform of the reconstructed image, using the Fast Fourier Transform algorithm $\tt fft$ in $\tt NumPy$ (cite: Harris2020) and the bivariate spline approximation $\tt RectBivariateSpline$ in $\tt Scipy$ (cite: Virtanen2020).

The observation $O$ and the model $M$ are deprojected in the $uv$ plane (cite: Butler1999) using the disk inclination and position angle (see Table [\[tab:stellar_properties\]](#tab:stellar_properties)). We then bin the visibility data every $30~k\lambda$ on the deprojected $uv$ plane and take the average of the data in the interval. The real part of the visibility is used to calculate the weighted average $\hat V_{Re}$ within the bin: $\hat V_{Re} = \sum_{j=1}^K (V_{Re,j}  w_{j})/\sum_{j=1}^K w_{j}$, where $V_{Re}$ is the real part of the visibility data, and $w$ is visibility weight, and $K$ is the number of data within the bin. The corresponding error $\hat\sigma$ is obtained from the error propagation of $w$ as follows $\hat\sigma = (\sum_{j=1}^K w_{j})^{-0.5}$.

To quantify the difference between the model and the observed visibility of the $i$-th bin, we define the normalized error (NR) as $\mathrm{NR}_{i} = (| \hat V_{Re,O, i} - \hat V_{Re,M,i}|/| \hat V_{Re,O, i}|)^{0.5}$. On the other hand, to evaluate the goodness of fit between the model and the observation, we apply the reduced $\chi^{2}$ ($\chi_{red}^{2}$) with the weighted visibility data. The formula is given by $$\begin{equation}
\chi_{red}^{2}=\frac{1}{N} \sum_{i=1}^{N}\frac{f_{i}\left|\hat V_{Re,O, i} - \hat V_{Re,M,i} \right|^{2}}{\hat\sigma^{2}_{i}},
\end{equation}$$ where $N$ is the total number of binned visibility data points and $f$ is the re-weighting factor, which is the ratio between the weight and the standard deviation (stddev) of the real part of the visibility data. Specifically, $f_i = \mathrm{stddev}^{-2}_{i} / \bar{w}_{i}$, where $\mathrm{stddev}_{i}$ and $\bar{w}_{i}$ are the standard deviation and the averaged weight of the data in the $i$-th bin. This approach ensures that the reduced $\chi^{2}$ converges to $\sim 1$ when the model correctly matches the observations. The re-weighting factors vary with the observed data and typically fall in the range of $0.1-0.3$, consistent with values reported in other disk observations ($0.2-0.3$; (cite: Hashimoto2021zztau; Hashimoto2021dmtau)).

# Relationship between the goodness of fit and the improvement of spatial resolution

We find that the goodness of fit of the visibility data measured by reduced $\chi^{2}$ values (Section [4.2](#sec:goodness_visfit)) shows a correlation with the improved spatial resolutions. Figure [7](#fig:resolutionratio_chisquare) shows the spatial resolution ratio between SpM and CLEAN as a function of the ratio of the reduced chi-square values of the two imaging methods. For CLEAN, we show two cases with CLEAN image and CLEAN model. In the case of CLEAN image versus SpM, the distribution has a high Pearson correlation ($\rho = -0.82$, $p-$value $<0.01$) in the logarithmic plane. We obtain the empirical relationship by linear regression as $$\begin{eqnarray}
\log \left(\frac{\theta_{\rm eff}/\theta_{\rm cl}}{\%}\right) &=&  (1.95 \pm 0.03) \nonumber \\ &-&(0.14\pm0.02) \log \left(\frac{\rm Red\chi^{2}_{\rm cl}}{\rm Red\chi^{2}_{\rm spm}} \right),
\end{eqnarray}$$ with a scatter of $0.09 \pm 0.01$ dex. In the case of the CLEAN model versus SpM, the correlation is marginal ($\rho = -0.51$, $p-$value $<0.01$). The empirical relation by linear regression is$$\begin{eqnarray}
\log \left(\frac{\theta_{\rm eff}/\theta_{\rm cl}}{\%}\right) &=& (1.78 \pm 0.02) \nonumber \\
&-& (0.20 \pm 0.06) \log \left(\frac{\rm Red\chi^{2}_{\rm clmodel}}{\rm Red\chi^{2}_{\rm spm}} \right),
\end{eqnarray}$$ with a scatter of $0.12\pm0.01$ dex.

# Radial Profiles Derived from CLEAN Model

The CLEAN algorithm generates a model consisting of a group of point sources (or multi-scale Gaussian distributions) that fit the observed visibility data. This “CLEAN Model” image has, by definition, a lot of artificial bumpy structures and does not resemble an actual disk. Therefore, it is smoothed with a beam to obtain a final “CLEAN Image”. However, this smoothing process changes the visibility of the image, resulting in a visibility profile that does not match the observations. Here, we note that it is possible to consider azimuthal averaging as another way of “smoothing”. The “beam” in this case is extended all over the azimuth while we do not convolve the image in the radial direction. The azimuthal average in the image therefore does not alter the radial visibility profile so it is possible to obtain the radial profile that matches with observed visibility from the CLEAN model.

The radial profiles produced by the CLEAN model are presented in Figures [10](#fig:radialprofile_1) and [11](#fig:radialprofile_2). In many cases, we see that the radial profiles produced by CLEAN models and SpM match each other. We see better matches in the outer part of the disks because the larger area is covered when averaging, making it possible to get rid of artificial bumpy structures. Additionally, the locations of gaps and rings in the outer region of large disks are consistent with those obtained from the SpM images, while the widths and depths of the gaps are not always consistent. Therefore, the radial profiles obtained from the CLEAN model have the potential to constrain the structures in the outer part of the disks and identify substructure candidates.

# Evaluation of Sparse Modeling with Three Disks

**Note.** Column description: (1) Name of the host star and data set. (2) observed frequency. (3) maximum baseline length $D_{\rm max}$ of observed visibilities. (4) CLEAN beam size $\theta_{\rm cl}$. $\tt{Brigss robust}$ parameter is set to be 0.5. (5) SpM beam size $\theta_{\rm eff}$. The beam size (effective spatial resolution) of each image is taken from a point source simulation. (6) RMS noise $\sigma_{\rm cl}$ of the CLEAN image. The value is derived from the emission-free area. (7) Detection threshold $I_{\rm DT}$ of the SpM image. The value is derived from the peak value of the emission-free area. (8, 9) Total flux $F_{\rm nu }$ of each CLEAN and SpM image. The flux is taken from the total value above $5\sigma_{\rm cl}$ for CLEAN or $I_{\rm DT}$ for SpM. (10) Two regularization parameters ($\log\Lambda_l$, $\log\Lambda_{tsv}$) adopted for each SpM image.

ALMA project IDs.\
RY Tau Data 1: 2016.1.01164.S. Data2: 2016.1.01164.S, 2017.1.01460.S.\
DG Tau Data 1: 2016.1.00846.S. Data 2: 2015.1.01268.S, 2016.1.00846.S.\
CI Tau Data 1: 2016.1.01164.S, and 2018.1.01631.S. Data 2: 2016.1.01164.S, 2016.1.01370.S, and 2018.1.01631.S.

![](spm_vs_clean_imagedomain.pdf)

![](spm_performance_radialintensity.pdf)

In this section, we evaluate the validity of SpM super-resolution imaging. Following the methods in (cite: Yamaguchi2020), we use two data sets of short and long baselines on the same object. We compare the SpM image of the short baseline data and the CLEAN image of the long baseline data to investigate whether the substructures in the SpM image are real. For this purpose, we use data from three objects: RY Tau, DG Tau, and CI Tau (see Table [\[tab:appendix_spmclean\]](#tab:appendix_spmclean)). We call the short baseline data set “Data 1” and the long baseline data set “Data 2”.

The left panels of Figure [23](#fig:spm_vs_clean_imagedomain) show the $uv-$coverages of each data set, and the maximum baseline lengths between Data 1 and Data 2 differ by a factor of $\sim 3-4$ for all objects. The middle panels of Figure [23](#fig:spm_vs_clean_imagedomain) show the images obtained with SpM and CLEAN. The total flux density of the Data 1 SpM image is scaled to that of the Data 2 CLEAN image to minimize the effects of errors in the flux calibration. The spatial resolutions of Data 1 SpM are $35\%$, $39\%$, and $86\%$ of the CLEAN beam sizes for RY Tau, DG Tau, and CI Tau, respectively. We have verified that these spatial resolution improvement factors are consistent with the SNR at long baselines, as discussed in Section [4.1](#sec:spatial_resolution). In the case of RY Tau and CI Tau disks, the Data 1 SpM images successfully reveal substructures such as gaps, inner holes, and asymmetries that appear in the Data 2 CLEAN images. We also note that SpM does not create artificial gaps or rings, as shown in the DG Tau disk, which had no gap.

Figure [24](#fig:spm_performance_radialintproflie) shows the azimuthally averaged radial intensity profiles for each image. The profiles of the Data 1 SpM image and the Data 2 CLEAN image agree within $\sim 10\%$, except in the inner cavity of the RY Tau disk, where the difference reaches $\sim 30\%$. This is because the Data 2 CLEAN image of RY Tau shows a faint inner disk at 30 mas spatial resolution, which is not present in Data 1 due to the lack of long baseline data.

# Comparison with Frankenstein approach 

(cite: Jennings2022taurus) present non-parametric one-dimensional (1D) fitting by the software Frankenstein ($\tt frank$) to the azimuthally average visibility data to derive the radial intensity profiles for 24 disks around single stars. Part of the targets are from the Taurus survey by (cite: Long2019) and overlap with ours. The $\tt frank$ approach utilizes a Gaussian process to optimize the model of the deprojected real-part visibility profile and has the potential to reconstruct substructures that are not recognized in standard CLEAN methods (cite: Jennings2020).

From visual inspection, the published radial visibility and intensity profiles for several disks from their study qualitatively agree with our results. The gap/ring features (DS Tau, DR Tau, MWC 480, and UZ Tau E), inflections (DO Tau, Haro 6-13, IQ Tau, and V409 Tau), isolated rings (CIDA 9A and IP Tau), and inner dips (BP Tau) are consistent in many targets. However, there are some inconsistent results. For instance, the $\tt frank$ approach reveals additional gap structures in the inner region of large disks (CI Tau, DL Tau, GO Tau, FT Tau). Conversely, some gaps and inflections are seen only in our analyses (DQ Tau, GI Tau, HP Tau, and V836 Tau). The different approaches to fitting visibility may result in different results, especially for weak features. We plan to make thorough comparisons between different techniques in a future publication.

1 natexlab

(ref: ALMAPartnership2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3. doi:10.1088/2041-8205/808/1/L3

(ref: Andrews2013) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., et al. 2013, ApJ, 771, 129. doi:10.1088/0004-637X/771/2/129

(ref: Andrews2005) Andrews, S. M. & Williams, J. P. 2005, ApJ, 631, 1134. doi:10.1086/432712

(ref: Andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483. doi:10.1146/annurev-astro-031220-010302

(ref: Akeson2019) Akeson, R. L., Jensen, E. L. N., Carpenter, J., et al. 2019, ApJ, 872, 158. doi:10.3847/1538-4357/aaff6a

(ref: Ansdell2016) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46. doi:10.3847/0004-637X/828/1/46

(ref: Andrews2018a) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018a, ApJL, 869, L41. doi:10.3847/2041-8213/aaf741

(ref: Andrews2018b) Andrews, S. M., Terrell, M., Tripathi, A., et al. 2018b, ApJ, 865, 157. doi:10.3847/1538-4357/aadd9f

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167. doi:10.3847/1538-4357/ac7c74

(ref: Asaki2020) Asaki, Y., Maud, L. T., Fomalont, E. B., et al. 2020, AJ, 160, 59. doi:10.3847/1538-3881/ab9101

(ref: Akiyama2017ApJ) Akiyama, K., Kuramochi, K., Ikeda, S., et al. 2017, ApJ, 838, 1. doi:10.3847/1538-4357/aa6305

(ref: Bitsch2015) Bitsch, B., Lambrechts, M., & Johansen, A. 2015, A&A, 582, A112. doi:10.1051/0004-6361/201526463

(ref: Bae2022) Bae, J., Isella, A., Zhu, Z., et al. 2022, arXiv:2210.13314. doi:10.48550/arXiv.2210.13314

(ref: Bacciotti2018) Bacciotti, F., Girart, J. M., Padovani, M., et al. 2018, ApJL, 865, L12. doi:10.3847/2041-8213/aadf87

(ref: Benisty2021) Benisty, M., Bae, J., Facchini, S., et al. 2021, ApJL, 916, L2. doi:10.3847/2041-8213/ac0f83

(ref: Boehler2018) Boehler, Y., Ricci, L., Weaver, E., et al. 2018, ApJ, 853, 162. doi:10.3847/1538-4357/aaa19c

(ref: Beckwith1990) Beckwith, S. V. W., Sargent, A. I., Chini, R. S., et al. 1990, AJ, 99, 924. doi:10.1086/115385

(ref: Beckwith1991) Beckwith, S. V. W. & Sargent, A. I. 1991, ApJ, 381, 250. doi:10.1086/170646

(ref: Butler1999) Butler, B. J. & Bastian, T. S. 1999, Synthesis Imaging in Radio Astronomy II, 180, 625

(ref: Barenfeld2017) Barenfeld, S. A., Carpenter, J. M., Sargent, A. I., et al. 2017, ApJ, 851, 85. doi:10.3847/1538-4357/aa989d

(ref: Birnstiel2018) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45. doi:10.3847/2041-8213/aaf743

(ref: Braun2021) Braun, T. A. M., Yen, H.-W., Koch, P. M., et al. 2021, ApJ, 908, 46. doi:10.3847/1538-4357/abd24f

(ref: Cortes2023) Cortes, P., Vlahakis, C., Hales, A., Carpenter, J., Dent, B., Kameno, S., Loomis, R., Vila Vilaro, B., Biggs, A., Miotello, A., Rosen, R., Stoehr, F., & Saini, K. (2023). ALMA Cycle 10 Technical Handbook (Cycle 10; Doc. 10.3; version 1.1). Zenodo. https://doi.org/10.5281/zenodo.7822943

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Currie2022) Currie, T., Lawson, K., Schneider, G., et al. 2022, Nature Astronomy, 6, 751. doi:10.1038/s41550-022-01634-x

(ref: Cieza2021) Cieza, L. A., González-Ruilova, C., Hales, A. S., et al. 2021, MNRAS, 501, 2934. doi:10.1093/mnras/staa3787

(ref: Czekala2016) Czekala, I., Andrews, S. M., Torres, G., et al. 2016, ApJ, 818, 156. doi:10.3847/0004-637X/818/2/156

(ref: Chapillon2008) Chapillon, E., Guilloteau, S., Dutrey, A., et al. 2008, A&A, 488, 565. doi:10.1051/0004-6361:200809523

(ref: Clarke2018) Clarke, C. J., Tazzari, M., Juhasz, A., et al. 2018, ApJL, 866, L6. doi:10.3847/2041-8213/aae36b

(ref: Cornwell2008) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793. doi:10.1109/JSTSP.2008.2006388

(ref: Chiang2012) Chiang, H.-F., Looney, L. W., & Tobin, J. J. 2012, ApJ, 756, 168. doi:10.1088/0004-637X/756/2/168

(ref: Chiang1997) Chiang, E. I. & Goldreich, P. 1997, ApJ, 490, 368. doi:10.1086/304869

(ref: Calcino2020) Calcino, J., Christiaens, V., Price, D. J., et al. 2020, MNRAS, 498, 639. doi:10.1093/mnras/staa2468

(ref: Carcamo2018) Cárcamo, M., Román, P. E., Casassus, S., et al. 2018, Astronomy and Computing, 22, 16. doi:10.1016/j.ascom.2017.11.003

(ref: Dong2018_multigap) Dong, R., Li, S., Chiang, E., et al. 2018, ApJ, 866, 110. doi:10.3847/1538-4357/aadadd

(ref: Dunham2010) Dunham, M. M., Evans, N. J., Terebey, S., et al. 2010, ApJ, 710, 470. doi:10.1088/0004-637X/710/1/470

(ref: Dullemond2001) Dullemond, C. P., Dominik, C., & Natta, A. 2001, ApJ, 560, 957. doi:10.1086/323057

(ref: Espaillat2014) Espaillat, C., Muzerolle, J., Najita, J., et al. 2014, Protostars and Planets VI, 497. doi:10.2458/azu_uapress_9780816531240-ch022

(ref: EHT2019) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019, ApJL, 875, L4. doi:10.3847/2041-8213/ab0e85

(ref: Facchini2020) Facchini, S., Benisty, M., Bae, J., et al. 2020, A&A, 639, A121. doi:10.1051/0004-6361/202038027

(ref: Federman2023) Federman, S., Megeath, S. T., Tobin, J. J., et al. 2023, ApJ, 944, 49. doi:10.3847/1538-4357/ac9f4b

(ref: Francis2020) Francis, L. & van der Marel, N. 2020, ApJ, 892, 111

(ref: Flock2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68. doi:10.1051/0004-6361/201424693

(ref: Galli2018) Galli, P. A. B., Loinard, L., Ortiz-Léon, G. N., et al. 2018, ApJ, 859, 33. doi:10.3847/1538-4357/aabf91

(ref: Gahm1999) Gahm, G. F., Petrov, P. P., Duemmler, R., et al. 1999, A&A, 352, L95

(ref: Gaia2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1. doi:10.1051/0004-6361/201629272

(ref: Gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1. doi:10.1051/0004-6361/201833051

(ref: Galametz2019) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5. doi:10.1051/0004-6361/201936342

(ref: Hayashi1985) Hayashi, C., Nakazawa, K., & Nakagawa, Y. 1985, Protostars and Planets II, 1100

(ref: Hashimoto2021zztau) Hashimoto, J., Dong, R., & Muto, T. 2021, AJ, 161, 264. doi:10.3847/1538-3881/abf431

(ref: Hashimoto2021dmtau) Hashimoto, J., Muto, T., Dong, R., et al. 2021, ApJ, 911, 5. doi:10.3847/1538-4357/abe59f

(ref: Huang2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42

(ref: Huang2020) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2020, ApJ, 891, 48. doi:10.3847/1538-4357/ab711e

(ref: Herczeg2014) Herczeg, G. J. & Hillenbrand, L. A. 2014, ApJ, 786, 97. doi:10.1088/0004-637X/786/2/97

(ref: Hendler2020) Hendler, N., Pascucci, I., Pinilla, P., et al. 2020, ApJ, 895, 126. doi:10.3847/1538-4357/ab70ba

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90. doi:10.1109/MCSE.2007.55

(ref: Helled2014) Helled, R., Bodenheimer, P., Podolak, M., et al. 2014, Protostars and Planets VI, 643. doi:10.2458/azu_uapress_9780816531240-ch028

(ref: Honma2014) Honma, M., Akiyama, K., Uemura, M., et al. 2014, PASJ, 66, 95. doi:10.1093/pasj/psu070

(ref: Harris2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357. doi:10.1038/s41586-020-2649-2

(ref: Hoerl1970) Hoerl, A. E., & Kennard, R. W., et al. 1970, Technometrics, 12, 55. doi.org/10.2307/1267351.

(ref: Ida2013) Ida, S., Lin, D. N. C., & Nagasawa, M. 2013, ApJ, 775, 42. doi:10.1088/0004-637X/775/1/42

(ref: Ichikawa2021) Ichikawa, T., Kido, M., Takaishi, D., et al. 2021, ApJ, 919, 55. doi:10.3847/1538-4357/ac0dc3

(ref: Isella2010mwc758) Isella, A., Natta, A., Wilner, D., et al. 2010, ApJ, 725, 1735. doi:10.1088/0004-637X/725/2/1735

(ref: Jennings2022taurus) Jennings, J., Tazzari, M., Clarke, C. J., et al. 2022b, MNRAS, 514, 6053. doi:10.1093/mnras/stac1770

(ref: Jennings2020) Jennings, J., Booth, R. A., Tazzari, M., et al. 2020, MNRAS, 495, 3209. doi:10.1093/mnras/staa1365

(ref: Jensen2007) Jensen, E. L. N., Dhital, S., Stassun, K. G., et al. 2007, AJ, 134, 241. doi:10.1086/518408

(ref: Keppler2018) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44. doi:10.1051/0004-6361/201832957

(ref: Kanagawa2015) Kanagawa, K. D., Muto, T., Tanaka, H., et al. 2015, ApJL, 806, L15. doi:10.1088/2041-8205/806/1/L15

(ref: Kanagawa2016) Kanagawa, K. D., Muto, T., Tanaka, H., et al. 2016, PASJ, 68, 43. doi:10.1093/pasj/psw037

(ref: Kley2006) Kley, W. & Dirksen, G. 2006, A&A, 447, 369. doi:10.1051/0004-6361:20053914

(ref: Kelly2007) Kelly, B. C. 2007, ApJ, 665, 1489. doi:10.1086/519947

(ref: Kenyon2008) Kenyon, S. J., Gómez, M., & Whitney, B. A. 2008, Handbook of Star Forming Regions, Volume I, 405. doi:10.48550/arXiv.0810.1298

(ref: Kraus2009) Kraus, A. L. & Hillenbrand, L. A. 2009, ApJ, 704, 531. doi:10.1088/0004-637X/704/1/531

(ref: Kwon2009) Kwon, W., Looney, L. W., Mundy, L. G., et al. 2009, ApJ, 696, 841. doi:10.1088/0004-637X/696/1/841

(ref: Kuramochi2018) Kuramochi, K., Akiyama, K., Ikeda, S., et al. 2018, ApJ, 858, 56. doi:10.3847/1538-4357/aab6b5

(ref: Levison2010) Levison, H. F., Thommes, E., & Duncan, M. J. 2010, AJ, 139, 1297. doi:10.1088/0004-6256/139/4/1297

(ref: Li2017) Li, J. I.-H., Liu, H. B., Hasegawa, Y., et al. 2017, ApJ, 840, 72. doi:10.3847/1538-4357/aa6f04

(ref: Luhman2023) Luhman, K. L. 2023, AJ, 165, 37. doi:10.3847/1538-3881/ac9da3

(ref: Long2018) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17. doi:10.3847/1538-4357/aae8e1

(ref: Long2019) Long, F., Herczeg, G. J., Harsono, D., et al. 2019, ApJ, 882, 49. doi:10.3847/1538-4357/ab2d2d

(ref: Lambrechts2012) Lambrechts, M. & Johansen, A. 2012, A&A, 544, A32. doi:10.1051/0004-6361/201219127

(ref: Luhman2010) Luhman, K. L., Allen, P. R., Espaillat, C., et al. 2010, ApJS, 186, 111. doi:10.1088/0067-0049/186/1/111

(ref: Leiendecker2022) Leiendecker, H., Jang-Condell, H., Turner, N. J., et al. 2022, ApJ, 941, 172. doi:10.3847/1538-4357/aca32d

(ref: Mora2001) Mora, A., Merı́n, B., Solano, E., et al. 2001, A&A, 378, 116. doi:10.1051/0004-6361:20011098

(ref: Miotello2014) Miotello, A., Testi, L., Lodato, G., et al. 2014, A&A, 567, A32. doi:10.1051/0004-6361/201322945

(ref: Marel2023) van der Marel, N. 2023, European Physical Journal Plus, 138, 225. doi:10.1140/epjp/s13360-022-03628-0

(ref: Mizuno1980) Mizuno, H. 1980, Progress of Theoretical Physics, 64, 544. doi:10.1143/PTP.64.544

(ref: Nakazato2020) Nakazato, T. & Ikeda, S. 2020, Astrophysics Source Code Library. ascl:2006.002

(ref: Narayan1986) Narayan, R. & Nityananda, R. 1986, ARA&A, 24, 127. doi:10.1146/annurev.aa.24.090186.001015

(ref: Osterloh1995) Osterloh, M. & Beckwith, S. V. W. 1995, ApJ, 439, 288. doi:10.1086/175172

(ref: Orihara2023) Orihara, R., Momose, M., Muto, T., et al. 2023, PASJ, 75, 424. doi:10.1093/pasj/psad009

(ref: Okuzumi2016) Okuzumi, S., Momose, M., Sirono, S.-. iti ., et al. 2016, ApJ, 821, 82. doi:10.3847/0004-637X/821/2/82

(ref: Ossenkopf1994) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: Pollack1996) Pollack, J. B., Hubickyj, O., Bodenheimer, P., et al. 1996, Icarus, 124, 62. doi:10.1006/icar.1996.0190

(ref: Petrov2001) Petrov, P. P., Pelt, J., & Tuominen, I. 2001, A&A, 375, 977. doi:10.1051/0004-6361:20010883

(ref: Pinilla2018) Pinilla, P., Tazzari, M., Pascucci, I., et al. 2018, ApJ, 859, 32. doi:10.3847/1538-4357/aabf94

(ref: Perez2018) Pérez, L. M., Benisty, M., Andrews, S. M., et al. 2018, ApJL, 869, L50. doi:10.3847/2041-8213/aaf745

(ref: Perez2019) Pérez, S., Casassus, S., Baruteau, C., et al. 2019, AJ, 158, 15. doi:10.3847/1538-3881/ab1f88

(ref: Pessah2017) Pessah, M. & Gressel, O. 2017, Formation, Evolution, and Dynamics of Young Solar Systems, 445. doi:10.1007/978-3-319-60609-5

(ref: Podio2013) Podio, L., Kamp, I., Codella, C., et al. 2013, ApJL, 766, L5. doi:10.1088/2041-8205/766/1/L5

(ref: Rafikov2004) Rafikov, R. R. 2004, AJ, 128, 1348. doi:10.1086/423216

(ref: Rebull2010) Rebull, L. M., Padgett, D. L., McCabe, C.-E., et al. 2010, ApJS, 186, 259. doi:10.1088/0067-0049/186/2/259

(ref: Rau2011) Rau, U. & Cornwell, T. J. 2011, A&A, 532, A71. doi:10.1051/0004-6361/201117104

(ref: Richards2022) Richards, A. M. S., Moravec, E., Etoka, S., et al. 2022, arXiv:2207.05591. doi:10.48550/arXiv.2207.05591

(ref: Rota2022) Rota, A. A., Manara, C. F., Miotello, A., et al. 2022, A&A, 662, A121. doi:10.1051/0004-6361/202141035

(ref: Schwab1984) Schwab, F. R. 1984, AJ, 89, 1076. doi:10.1086/113605

(ref: Shu1987) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23. doi:10.1146/annurev.aa.25.090187.000323

(ref: Simon2019) Simon, M., Guilloteau, S., Beck, T. L., et al. 2019, ApJ, 884, 42. doi:10.3847/1538-4357/ab3e3b

(ref: Tanaka2022) Tanaka, Y. A., Kanagawa, K. D., Tanaka, H., et al. 2022, ApJ, 925, 95. doi:10.3847/1538-4357/ac3af5

(ref: Takeuchi1996) Takeuchi, T., Miyama, S. M., & Lin, D. N. C. 1996, ApJ, 460, 832. doi:10.1086/177013

(ref: Takahashi2014) Takahashi, S. Z. & Inutsuka, S.-. ichiro . 2014, ApJ, 794, 55. doi:10.1088/0004-637X/794/1/55

(ref: Takahashi2016) Takahashi, S. Z. & Inutsuka, S.-. ichiro . 2016, AJ, 152, 184. doi:10.3847/0004-6256/152/6/184

(ref: Tazzari2017) Tazzari, M., Testi, L., Natta, A., et al. 2017, A&A, 606, A88. doi:10.1051/0004-6361/201730890

(ref: Tazzari2021) Tazzari, M., Clarke, C. J., Testi, L., et al. 2021, MNRAS, 506, 2804. doi:10.1093/mnras/stab1808

(ref: Tang2014) Tang, Y.-W., Dutrey, A., Guilloteau, S., et al. 2014, ApJ, 793, 10. doi:10.1088/0004-637X/793/1/10

(ref: Tang2017) Tang, Y.-W., Guilloteau, S., Dutrey, A., et al. 2017, ApJ, 840, 32. doi:10.3847/1538-4357/aa6af7

(ref: Tsukamoto2021) Tsukamoto, Y., Machida, M. N., & Inutsuka, S.-. ichiro . 2021, ApJL, 920, L35. doi:10.3847/2041-8213/ac2b2f

(ref: Tsukamoto2023) Tsukamoto, Y., Machida, M. N., & Inutsuka, S.-. ichiro . 2023, PASJ, 75, 835. doi:10.1093/pasj/psad040

(ref: Tripathi2017) Tripathi, A., Andrews, S. M., Birnstiel, T., et al. 2017, ApJ, 845, 44. doi:10.3847/1538-4357/aa7c62

(ref: Tsukagoshi2019) Tsukagoshi, T., Muto, T., Nomura, H., et al. 2019, ApJL, 878, L8. doi:10.3847/2041-8213/ab224c

(ref: Tominaga2019) Tominaga, R. T., Takahashi, S. Z., & Inutsuka, S.-. ichiro . 2019, ApJ, 881, 53. doi:10.3847/1538-4357/ab25ea

(ref: Tibshirani1996) Tibshirani, R.  1996 Journal of the Royal Statistical Society, 58, 267. http://www.jstor.org/stable/2346178

(ref: Ubeira2019) Ubeira Gabellini, M. G., Miotello, A., Facchini, S., et al. 2019, MNRAS, 486, 4638. doi:10.1093/mnras/stz1138

(ref: Ueda2022) Ueda, T., Kataoka, A., & Tsukagoshi, T. 2022, ApJ, 930, 56. doi:10.3847/1538-4357/ac634d

(ref: Vioque2018) Vioque, M., Oudmaijer, R. D., Baines, D., et al. 2018, A&A, 620, A128. doi:10.1051/0004-6361/201832870

(ref: Vieira2003) Vieira, S. L. A., Corradi, W. J. B., Alencar, S. H. P., et al. 2003, AJ, 126, 2971. doi:10.1086/379553

(ref: Virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261. doi:10.1038/s41592-019-0686-2

(ref: Marel2019) van der Marel, N., Dong, R., di Francesco, J., et al. 2019, ApJ, 872, 112. doi:10.3847/1538-4357/aafd31

(ref: Vorobyov2013) Vorobyov, E. I. 2013, A&A, 552, A129. doi:10.1051/0004-6361/201220601

(ref: Wong2016) Wong, Y. H. V., Hirashita, H., & Li, Z.-Y. 2016, PASJ, 68, 67. doi:10.1093/pasj/psw066

(ref: Yamaguchi2021) Yamaguchi, M., Tsukagoshi, T., Muto, T., et al. 2021, ApJ, 923, 121

(ref: Yamaguchi2020) Yamaguchi, M., Akiyama, K., Tsukagoshi, T., et al. 2020, ApJ, 895, 84

(ref: Young2005) Young, C. H. & Evans, N. J. 2005, ApJ, 627, 293. doi:10.1086/430436

(ref: Youdin2011) Youdin, A. N. 2011, ApJ, 731, 99. doi:10.1088/0004-637X/731/2/99

(ref: Zhu2012) Zhu, Z., Nelson, R. P., Dong, R., et al. 2012, ApJ, 755, 6. doi:10.1088/0004-637X/755/1/6

(ref: Zhang2015) Zhang, K., Blake, G. A., & Bergin, E. A. 2015, ApJL, 806, L7. doi:10.1088/2041-8205/806/1/L7

(ref: Zhang2018) Zhang, S., Zhu, Z., Huang, J., et al. 2018, ApJL, 869, L47

(ref: Zhang2023) Zhang, S., Kalscheur, M., Long, F., et al. 2023, ApJ, 952, 108. doi:10.3847/1538-4357/acd334

[^1]: “Fidelity” is a measure of how faithfully the brightness distribution on a reconstructed image matches an expected astronomical object. Based on previous ALMA high-sensitivity observations of disk structures, we regard the high-fidelity image of the disks to be that having smooth axisymmetric (e.g., circular rings and gaps) or non-axisymmetric (e.g., spirals or local blobs larger than the spatial resolution) structures. Images having random structures such as many small dot-like structures are considered as low fidelity.

[^2]: $\tt rescale \_ flux$ function is publicly available at <https://almascience.eso.org/almadata/lp/DSHARP/scripts/reduction_utils.py>

[^3]: $\tt PRIISM$ (Python Module for Radio Interferometry Imaging with Sparse Modeling) is an imaging tool for ALMA based on the sparse modeling technique, and is publicly available at <https://github.com/tnakazato/priism>

[^4]: $\tt Linmix$ is a Bayesian approach to linear regression and is publicly available at <https://github.com/jmeyers314/linmix>. Hereafter we apply this method when employing the linear regression to data sets.

[^5]: The $\tt Kneed$ approach detects the knee point on a radial profile and is publicly available at <https://github.com/arvkevi/kneed>

</paper>

Write the methods card for this paper.