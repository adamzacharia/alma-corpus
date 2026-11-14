# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...961...71F\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...961...71F",
 "title": "The Extended [C II] under Construction? Observation of the Brightest High-z Lensed Star-forming Galaxy at z = 6.2",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Fudamoto, Yoshinobu",
 "n_authors": 30,
 "arxiv_id": "2303.07513",
 "doi": "10.3847/1538-4357/ad0f95",
 "alma_projects_linked_by_archive": [
  "2021.1.00143.S"
 ]
}
```

Paper text:
<paper>
# The Extended \[C ii\] under Construction? Observation of the brightest high-z lensed star-forming galaxy at z = 6.2

## Abstract

We present results of \[C ii\]$\,158\,\rm{\mu m}$ emission line observations, and report the spectroscopic redshift confirmation of a strongly lensed ($\mu\sim20$) star-forming galaxy, MACS0308-zD1 at $z=6.2078\pm0.0002$. The \[C ii\] emission line is detected with a signal-to-noise ratio $>6$ within the rest-frame UV bright clump of the lensed galaxy (zD1.1) and exhibits multiple velocity components; the narrow \[C ii\] has a velocity full-width-half-maximum (FWHM) of $110\pm20\,\rm{km/s}$, while broader \[C ii\] is seen with an FWHM of $230\pm20\,\rm{km/s}$. The broader \[C ii\] component is blueshifted ($-80\pm20\,\rm{km/s}$) with respect to the narrow \[C ii\] component, and has a morphology which extends beyond the UV-bright clump. We find that while the narrow \[C ii\] emission is most likely associated with zD1.1, the broader component is possibly associated with outflowing gas. Based on the non-detection of $\lambda_{\rm 158\,\mu m}$ dust continuum, we find that MACS0308-zD1’s star-formation activity occurs in a dust-free environment with the stringent upper limit of infrared luminosity $\lesssim9\times10^{8}\,{\rm L_{\odot}}$. Targeting this strongly lensed faint galaxy for follow-up ALMA and JWST observations will be crucial to characterize the details of typical galaxy growth in the early Universe.

# Introduction

Over the past decades, optical/near-infrared surveys using ground- and space-based telescopes have built large samples of high-redshift galaxies at $z > 6$, revealing star-formation activity and stellar mass buildup in the first Gyr of the Universe (cite: Madau2014; Stefanon2021; Weaver2022). Recently, our understanding of early galaxy buildup has been significantly advanced by unprecedented sensitivity and high-resolution observations of the Atacama Large Millimeter/submillimeter Array (ALMA). ALMA observations have built large samples of of high-redshift galaxies with strong far-infrared (FIR) emission lines (e.g., \[C ii\] $158\,\rm{\mu m}$, \[O iii\] $88\,\rm{\mu m}$) and dust continuum (cite: Hashimoto2018; Bethermin2020; Fudamoto2021; Bouwens2022), and ultimately revealing the interstellar medium (ISM) properties of these early-epoch galaxies.

ALMA \[C ii\] $158\,\rm{\mu m}$ emission line surveys have so far revealed ISM properties for $>100$ for galaxies at high redshift, including: galaxy-scale morpho-kinematics which suggest a large diversity of formation pathways among $z>4$ star-forming galaxies (cite: lefevre2020; Jones2021), $\sim$500–1000 $\rm{km/s}$ gas outflows velocities (cite: Maiolino2012; Ginolfi2020), and $\sim$30 $\rm{kpc}$ scale gas halos surrounding a dominant fraction of galaxies which imply a star-formation driven metal pollution of the circumgalactic medium (cite: Fujimoto2020; Fudamoto2022). A strong correlation between the neutral gas reservoir seen by \[C ii\] and SFR of galaxies (cite: Schaerer2020). Evolution of dust-obscured star-formation activities suggests an evolution of dust attenuation properties at $z>4$ (cite: Bouwens2020; Fudamoto2020). It has been proposed to use \[C ii\] $158\,\rm{\mu m}$ line as a tracer of star-forming neutral gas, which shows evolution of the neutral gas fraction of high-redshift galaxies (cite: Zanella2018; Dessauges2020; Heintz2021).

To date, these high-$z$ observations have been mostly limited to massive star-forming galaxies (e.g., $M_{\ast}>10^{10}\,\rm{M_{\odot}}$ and/or $\rm{SFR} > 10\,\rm{M_{\odot}\,yr^{-1}}$) and we only have small samples of less evolved, low-mass/low-SFR galaxies. This is because detailed ISM observations of relatively low-mass galaxies are still one of the major challenges even for ALMA as they are intrinsically faint. One method to push to fainter limits is to adopt strongly lensed galaxies to investigate the detailed properties of high-redshift, low-mass galaxies in a feasible observing time (cite: Coe2019; Treu2022; Vanzella2022). Such strongly magnified high-redshift sources are, however, relatively rare and only a handful of ALMA observations have been performed so far (cite: Knudsen2016; Bradac2017; Calura2021; Fujimoto2021). The study of the ISM properties of low-mass, high-$z$ galaxies is thus still in its nascent stages.

Here, we report an observation of a strongly lensed $\sim L^{\ast}$ star-forming galaxy: MACS0308-zD1 at $z\sim6.2$. We clearly detect a \[C ii\] $158\,\rm{\mu m}$ emission line and measures the spectroscopic redshift of MACS0308-zD1 for the first time (cite: Acebron2018; Salmon2020; Welch2023). Making use of high-resolution, high-sensitivity ALMA observations, we also study the velocity structure and morphology of the \[C ii\] emission. These suggest multiple components of \[C ii\] emission that are distinct in spatial and spectral directions.

This paper is organized as follows: in §[2](#sec:obs) we describe our target galaxy and the ALMA observations used in this study. In §[3](#sec:analysis), we present our data analysis and measurements for the \[C ii\] $\,158\,{\rm \mu m}$ emission line and $\lambda_{\rm rest}\sim158\,{\rm \mu m}$ dust continuum. In §[4](#sec:discussion), we compare to previous studies and discuss our results. Finally, we conclude with the summary in §[5](#sec:conclusion). Throughout this paper, we assume a cosmology with $(\Omega_m,\Omega_{\Lambda},h)=(0.3,0.7,0.7)$, and the Chabrier (cite: Chabrier2003) initial mass function (IMF), where applicable. With these cosmological parameters, 1 arcsec corresponds to $5.6\,\rm{kpc}$ at $z=6.2078$.

# Observation and Data Reduction

## Target: MACS0308-zD1

The target of the ALMA observations, MACS0308-zD1, was identified in the Reionization Lensing Cluster Survey (RELICS; (cite: Coe2019)) in the background of the lensing cluster MACS0308+26. The galaxy was first identified as one of the triply imaged galaxies in the field at $z>6$ (cite: Acebron2018), and our target is the brightest among the three images ($\rm{RA= 03:08:53.407}$, $\rm{Dec=+26:44:58.93}$, which originally given the ID of MACS0308-c4.3 in (cite: Acebron2018)). MACS0308-zD1 was found as the apparently UV-brightest $z>6$ galaxy having $m_{\rm AB}=23.0\,{\rm mag}$, and an estimated photometric redshift of $z_{\rm ph}\sim6.2 - 6.3$ (cite: Salmon2020). (cite: Welch2023) further analyzed MACS0308-zD1 by forward modeling of the galaxy in the source plane and found an updated robust photometric redshift of $z_{\rm ph}=6.21$, and that MACS0308-zD1 consists of a bright clump: MACS0308-zD1.1, and a faint diffuse component. The bright clump was found to have a radius of $r=27\,\rm{pc}$ in its source plane, and to have an extremely high star-formation rate surface density of $\Sigma_{\rm SFR}\sim900\,{\rm M_{\odot}\,yr^{-1}\,kpc^{-2}}$. This $\Sigma_{\rm SFR}$ is the highest value ever found at $z\sim6$ star-forming galaxies (cite: Kennicutt2012), suggesting that the clump could be an environment similar to the starburst galaxies.

## ALMA observations

MACS0308-zD1 has been observed in the ALMA program #2021.1.00143.S (PI: Fudamoto). The observation scanned to search the \[C ii\] $\,158\,\rm{\mu m}$ emission line at a sky frequency range between $245\,\rm{GHz}$ and $273\,\rm{GHz}$ that covers entire photometric redshift probability of the target (cite: Acebron2018; Salmon2020; Welch2023). To efficiently scan the frequency range, the observations used four separate spectral tunings (T1 to T4; see Fig. [1](#fig:wholespec)). The correlator was set up in dual polarization and frequency domain mode, covering 1.875 GHz band width having a native spectral resolution of $\sim9\,\rm{km/s}$.

All tunings were observed during multiple observing runs using the ALMA cycle-8 C43-3 configuration. The on-source time was $\sim$0.5, $\sim$1.6 ,$\sim$1.0, and $\sim$1.0 hrs, respectively. The precipitable water vapor (PWV) during the observations was $0.545$, $1.450$, $0.544$, $0.636\,\rm{mm}$ for tunings T1, T2, T3, and T4, respectively. The relatively large variations of the on-source time were mainly due to variations in the weather conditions.

For the data calibration, we asked EA-ARC for the data calibration support[^1] to deliver the calibrated data that are produced using the QA2 pipeline code (i.e., ). The observed data were analyzed using The Common Astronomy Software Application (CASA) version 6.2.1 (cite: Bean2022).

![](Whole_Spectrum.v2_mod.pdf)

## Imaging data cube and \[C ii\] $158\,\rm{\mu m}$ line detection

To search the \[C ii\] $\,158\,\rm{\mu m}$ emission line, we created a data cube combining all four tunings using CASA task using `NATURAL` weighting scheme, a spectral binning of $30\,\rm{km/s}$, a pixel scale of $0.1^{\prime\prime}$, and an image size of $30^{\prime\prime}\times30^{\prime\prime}$ (i.e., a large enough sky area that contains the primary beam attenuation $<50\%$). With CASA task `tclean`, we performed the synthesized beam deconvolution using a fixed stopping threshold of three times the pixel-by-pixel root mean square (RMS) for all channels and the maximum iteration of 500 times. The conservative deconvolution threshold does not affect the final data products as there are no bright sources in this velocity binning that could contaminate the resulting image products. The produced data cube has a synthesized beam full width at half maximum (FWHM) of $1.31^{\prime\prime}\times0.73^{\prime\prime}$, $0.94^{\prime\prime}\times0.68^{\prime\prime}$, $1.11^{\prime\prime}\times0.78^{\prime\prime}$, and $1.03^{\prime\prime}\times0.73^{\prime\prime}$ for tuning 1, 2, 3, and 4, respectively. The average pixel-by-pixel RMS was $0.27\,\rm{mJy/beam}$ for $30\,\rm{km/s}$ bin. The achieved sensitivity varies by a factor of up to $2.4$ from tuning to tuning. The variations in the sensitivity are due to the variations of the precipitable water vapor (PWV) under which each tuning was observed and also due to the weak atmospheric absorption features (see Fig. [1](#fig:wholespec)).

Using the location of the rest-frame UV emission as a prior of the spatial position of \[C ii\], we found the \[C ii\]$\,158\,\rm{\mu m}$ emission line from MACS0308-zD1 at a frequency of $263.6995\pm0.004\,{\rm GHz}$ (Fig. [1](#fig:wholespec)).

## Imaging continuum map

The $\lambda_{\rm rest}\sim158\,\rm{\mu m}$ continuum image of MACS0308-zD1 was created using CASA task with the multi frequency synthesis mode. During the continuum imaging, we conservatively excluded the whole spectral window that contains the entire \[C ii\] $\,158\,\rm{\mu m}$ emission line. Since we only excluded one spectral window out of the 16 total spectral windows from our four spectral setups, the exclusion does not affect the resulting sensitivity of the continuum map.

The synthesized beam deconvolution was performed using `NATURAL` weighting scheme, using a stopping threshold of $27\,\rm{\mu Jy/beam}$ (i.e., $3\times$ the pixel-by-pixel RMS of the dirty image) and by setting the maximum number of iteration to 500 times. Again, the deconvolution thresholds do not affect the result, as there are no bright sources in the continuum image. As a result, we obtained a dust continuum image of MACS0308-zD1 that has a final pixel-by-pixel RMS of $8.9\,\rm{\mu Jy/beam}$ (Fig. [2](#fig:continuum)).

# Analysis and Measurements

## Dust Continuum

![](HST_Continuum.v0_mod.pdf)

In the continuum image, there is only a $\sim2\,\sigma$ positive signal close to but offset from the rest-frame UV position of the MACS0308-zD1 (Fig. [2](#fig:continuum)). Several previous studies found that typically a significance of $>3.5\,\sigma$ is required to avoid contamination of noise signals (cite: Bethermin2020; Inami2022). Therefore, we conclude that the dust continuum of MACS0308-zD1 is not detected in the observations.

As the dust continuum is not detected, we estimated the $3\,\sigma$ upper limit of the rest-frame $158\,\rm{\mu m}$ continuum of MACS0308-zD1 as $<27\,\rm{\mu Jy}$, adopting $3\times$ the pixel-by-pixel RMS. Assuming a dust temperature of $\sim45\,\rm{K}$ and $\beta=1.8$ (cite: Bethermin2020; Sommovigo2022) for a modified black body emission, we estimated a $3\,\sigma$ upper limit of the observed infrared (IR) luminosity of $<1.9\times10^{10}\,\rm{L_{\odot}}$ in the image plane. This means $L_{\rm IR}<9.5\times10^{8}\,\rm{L_{\odot}}$ in the source plane assuming $\mu=20$.

## \[C ii\] $158\,\rm{\mu m}$ emission line

![](C2mom0_total.v2.pdf)

We extracted the \[C ii\] emission line and created the moment-0 map in an iterative way. First, we created a moment-0 map integrating over an arbitrary frequency range that clearly include the \[C ii\] emission line. Second, we extracted the \[C ii\] spectrum using the moment-0 maps as a mask. Namely, we used pixels that had $>2\,\sigma$ signals in the moment-0 map, and extracted integrated spectra that were again used to create moment-0 map using channels having continuous positive signals. The procedures are repeated until the channels used to create moment-0 map converged. A few iterations were enough to converge, with the final results shown in Fig [3](#fig:mom0_total).

In this way, we obtained the moment-0 image and the spectrum of the \[C ii\] emission line integrated over the whole galaxy component. Using the integrated moment-0 map, we measured the total \[C ii\] flux density using CASA task `imfit`; 2-dimensional Gaussian fitting. Measured quantities are summarized in Tab. [\[tab:measurements\]](#tab:measurements).

## Multi-Component Analysis of the \[C ii\] line

The \[C ii\] emission line of MACS0308-zD1 deviates from a single Gaussian profile, and shows a blueshifted excess (Fig. [3](#fig:mom0_total)). We separated these components and estimated the properties of each of the \[C ii\] lines. As a first step, we performed a least square fitting using a two component Gaussian function to the integrated 1-D spectrum of the \[C ii\] emission. This resulted in a reasonable fit with only small residuals that were consistent with random noise.

We found that the best fitting results arose from the combination of a narrow and a broader Gaussian (Left panel of Fig. [3](#fig:mom0_total)).

![](C2mom0_separate.v2.pdf)

We then created moment-0 maps for both the narrow and the broader \[C ii\] emission by integrating frequency ranges of $263.62$ to $263.72\,\rm{GHz}$ and $263.73$ to $263.92\,\rm{GHz}$, respectively. These frequency ranges were selected to separately image moment-0 maps of the two different components, and at the same time, to avoid contamination of different components.

Based on the results of the two component Gaussian fitting, we estimated the fractions of contamination for each maps. Using the above frequency range to integrate and the results of the two component Gaussian fitting, we estimated that $\sim7\,\%$ of the narrow \[C ii\] component contaminates the broad image, while $\sim8\%$ of the broader \[C ii\] component contaminates the narrow \[C ii\] moment-0 maps. Thus, the contamination from other components has only a minor impact on the moment-0 maps and measured fluxes for each component.

### The Narrow \[C ii\] Emission Component

The moment-0 image of the narrow \[C ii\] component shows a $6\,\sigma$ detection. The emission is co-spatial with the rest-frame UV emission of the bright clump (hereafter MACS0308-zD1.1) seen by the HST F160W filter (top panel of Fig. [4](#fig:mom0_separate)). The significant detection from the co-spatial location implies that the narrow component is associated with the UV-bright star-formation activity of the MACS0308-zD1.1. We extracted the narrow component of the \[C ii\] emission using the moment-0 map (top left panel of Fig. [4](#fig:mom0_separate)), which has a velocity FWHM of $110\pm19\,\rm{km/s}$. This line width leis at the lower bound of the FWHM of \[C ii\] emission lines thus far observed from high redshift galaxies (cite: Bethermin2020).

### The Broader \[C ii\] Emission Component

The moment-0 image of the broader \[C ii\] shows a $\sim$4.2 $\sigma$ detection. The emission appears somewhat offset from rest-frame UV emission of the MACS0308-zD1.1 (bottom panel of Fig. [4](#fig:mom0_separate)). The extracted emission of the broader \[C ii\] component has a velocity FWHM of $233\pm19\,\rm{km/s}$, roughtly two times broader than the narrow component. The broader component appears blueshifted by $\Delta v = -80\pm20\,\rm{km/s}$ with respect to the narrow component (Tab. [\[tab:measurements\]](#tab:measurements)).

|  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|
|  component | Redshift | \[C ii\] FWHM | $f_{\rm [CII]} \times \mu^{\dagger}$ | $L_{\rm [CII]}$ | $M_{\rm H_2}$ |  |
|  |  | $\rm{km/s}$ | ${\rm Jy\,km/s}$ | ${\rm L_{\odot}}$ | ${\rm M_{\odot}}$ |  |
| Total | $6.2078\pm0.0002$ | – | $0.62\pm0.18$ | $2.96\pm0.79\times 10^{7}$ | $9.05\pm0.81\times 10^{8}$ |  |
| Narrow | $6.2078\pm0.0002$ | $110\pm20$ | $0.37\pm0.10$ | $1.67\pm0.45\times10^{7}$ | $5.05\pm0.45\times 10^{8}$ |  |
| Broad | $6.2058\pm0.0005$ | $230\pm20$ | $0.30\pm0.09$ | $1.35\pm0.45\times10^{7}$ | $4.05\pm0.40\times 10^{8}$ |  |

We used the single component 2D Gaussian fits to measure integrated fluxes.\

$\dagger$ The measured values (except for the \[C ii\] flux densities) are corrected for gravitational lensing magnification of $\mu=22$.

# Discussion

## Dust-obscured Star-Formation Activity

We derive a $3\,\sigma$ upper limit to the observed IR luminosity of $<1.9\times10^{10}\,\rm{L_{\odot}}$ assuming a dust temperature of $45\,\rm{K}$. Assuming that the dust emission is co-spatial with MACS0308-zD1, the $3\,\sigma$ upper limit IR luminosity in the source plane is $\lesssim9\times10^{8}\,\rm{L_{\odot}}$, applying a magnification factor of $\mu\sim20$ (cite: Welch2023). The stringent upper limit on the IR luminosity implies an extremely low dust-obscured star-formation rate of ${\rm SFR_{IR}}<0.1\,\rm{M_{\odot}\,yr^{-1}}$ using the conversion of ${\rm SFR_{IR}}=1.2\times10^{-10}\,L_{\rm IR}\,{\rm M_{\odot}\,yr^{-1}\,L_{\odot}^{-1}}$ (cite: Madau2014; Inami2022). Given the extreme brightness of MACS0308-zD1 in the rest-frame UV ($SFR_{\rm UV}=3\pm1\,\rm{M_{\odot}\,yr^{-1}}$ for zD1.1 and $7\pm2\,\rm{M_{\odot}\,yr^{-1}}$ for diffuse component; (cite: Welch2023)), we derive a very low dust-obscured fraction of the star formation activity ($f_{\rm obs} = \rm{SFR_{IR}/\rm{SFR_{total}}}$) of only $\lesssim 1$ to $3\,\%$, meaning that the star formation activity of MACS0308-zD1 is almost completely dust-free.

The major uncertainty in estimating the IR luminosity from a single ALMA observation is the unknown dust temperature; increasing the assumed dust temperature can produce larger IR luminosities (cite: Faisst2020; Bakx2021; Fudamoto2022Td; Algera2023). We examined this effect and its impact on the dust-obscured SFR. For a high dust temperature case of $60\,\rm{K}$, the de-magnified $3\,\sigma$ upper limit IR luminosity is $5.5\times10^{9}\,\rm{L_{\odot}}$ which yields a $3\,\sigma$ upper limit SFR of ${\rm SFR_{IR}}<0.3\,\rm{M_{\odot}\,yr^{-1}}$. Even for an extreme dust temperature of $80\,\rm{K}$, we find $8.0\times10^{9}\,\rm{L_{\odot}}$ and $0.8\,\rm{M_{\odot}\,yr^{-1}}$ for de-magnified $3\,\sigma$ upper limit of IR luminosity and dust-obscured SFR, respectively. Although such extremely high dust temperatures are not yet confirmed in this redshift range (cite: Algera2023), even with these extreme assumptions, we still derived low obscured fractions of star-formation activity of $\lesssim10\,\%$ to $26\,\%$ for zD1.1 and the diffuse component, respectively. Thus, MACS0308-zD1 has relatively little dust-obscured activity, even after accounting for rather extreme uncertainties in the dust temperature.

This low $f_{\rm obs}$ contrasts strongly with the relatively high obscured fractions ($\sim50\,\%$) seen for massive $M_{\ast}>10^{9.5}\,\rm{M_{\odot}}$ galaxies at $z\gtrsim5$ (cite: Fudamoto2020; Schouws2022; Algera2023). Nonetheless, it is consistent with the very blue UV color of MACS0308-zD1.1 (cite: Welch2023). The nearly dust-free environment of the star-forming region is indicative of the metal-poor and young environment of the star-formation activity. In such an environment, strong \[O iii\] $88\,\rm{\mu m}$ emission line is expected . Further follow-up observations with ALMA will be important to characterize conditions of the interstellar medium of the star-forming region of the MACS0308-zD1.

## \[C ii\]$\,158\,\rm{\mu m}$ Emission Line

![](SFR_C2.v2_mod.pdf)

### SFR-\[C ii\] correlation

It is highly debated whether the correlation between star formation rates (SFRs) and $L_{\rm [CII]}$ evolves as a function of redshift. Previous studies have shown that galaxies with low SFRs or metallicities show extremely faint \[C ii\] emission, denoted “\[C ii\]-deficit” (cite: Matthee2019; Harikane2020), that are also predicted by theoretical studies (cite: Vallini2015; Liang2023). However, (cite: Schaerer2020) demonstrated that, based on large samples of galaxies obtained in the ALMA large program ALPINE (cite: lefevre2020; Bethermin2020; Faisst2020), there is no significant change of the observed $L_{\rm [CII]}$-SFR relation as a function of redshift, and pointed out that the previously obtained “\[C ii\]-deficit” is largely affected by the uncertain estimations of the dust-obscured SFRs of high-redshift galaxies.

With the measured \[C ii\] luminosity of MACS0308-zD1.1 and estimated SFR ($3\pm1\,\rm{M_{\odot}\,yr^{-1}}$), MACS0308-zD1.1 appears consistent with the SFR-$L_{\rm [CII]}$ relation derived in the local galaxies (cite: delooze2014) and for high-redshift galaxies where no-evolution of the relation is found (cite: Schaerer2020), but deviates from the “\[C ii\]-deficit” relation suggested in some of the previous studies (cite: Harikane2020; Liang2023). Here, we assume that the $\rm{SFR_{IR}}$ is negligible, given the faint IR luminosity upper limits and low SFR$_{\rm IR}$s found in §[4.1](#sec:continuum). Thus, our observation supports a non-evolving picture for the SFR-$L_{\rm [CII]}$ correlation in the star-forming clump-scale structure inside distant galaxies (Fig. [5](#fig:sfrc2)). This result suggests that the SFR-$L_{\rm [CII]}$ holds even for low SFR and potentially metal-poor galaxies at high redshift.

### Molecular Gas Mass

Previous studies showed that the \[C ii\]$\,158\,\rm{\mu m}$ emission line is an excellent indicator of star-forming molecular gas. In particular, (cite: Zanella2018) showed a tight correlation between molecular gas masses (${M_{\rm H2}}$) and $L_{\rm [CII]}$ in $z{\sim}2$ star-forming galaxies. Also, (cite: Dessauges2020) examined whether the ${M_{\rm H2}}$-$L_{\rm [CII]}$ relation is applicable to $4.5<z<5.5$ star-forming galaxies, and showed that the derived molecular gas masses are consistent with other methods. Using the method presented in (cite: Zanella2018), we estimated separately the molecular gas masses for the integrated, narrow \[C ii\] and broad \[C ii\] components of the MACS0308-zD1 (Tab. [\[tab:measurements\]](#tab:measurements)).

We also estimated the surface density of molecular gas mass $\Sigma_{\rm H2}$. However, with the $\rm{FWHM}\sim1^{\prime\prime}$ resolution of the observation, both components of the \[C ii\] emission are either unresolved or only marginally resolved. The most extreme case is found by assuming that the narrow \[C ii\] is associated with the UV-bright component MACS0308-zD1.1, and assuming the size of the star-forming region is $r=27\,\rm{pc}$ (cite: Welch2023). In this case, we found a remarkably dense surface gas mass density of ${\rm log}\,[\Sigma_{\rm H2}\,{\rm/(M_{\odot}\,pc^{2})}]=5.34\pm0.09$, which is $>6000$ times larger than that of giant molecular clouds in today’s ISM (cite: Leroy2008), and $\times100$ higher than the maximum value found in the recent simulation of galaxies at $z\sim8$ (cite: Garcia2022).

Combined with the extremely high surface star formation rate density of $\Sigma_{\rm SFR}\sim900\,{\rm M_{\odot}\,yr^{-1}\,kpc^{-2}}$ (cite: Welch2023), MACS0308-zD1.1 is located on the extreme edge of the Kennicutt-Schmidt relation (cite: Kennicutt2012). This might suggest that the UV-bright clump has a star formation environment similar to or more extreme than starburst galaxies.

## \[C ii\] outflow or another structure?

![](kinematics.v1_mod.pdf)

We found multiple velocity components in the \[C ii\] emission line: a narrow FWHM $\sim110\,\rm{km/s}$ \[C ii\] that is spatially coincident with the UV-bright star-forming region, and a broader FWHM $\sim230\,\rm{km/s}$ \[C ii\] that is spatially extended and potentially offset (Tab. [\[tab:measurements\]](#tab:measurements)). The offset both in centroid velocity and dispersion in the same region is difficult to explain with simple rotation (Fig. [6](#fig:kinematics)).

As the narrow emission is spatially coincident with the UV emission of the galaxy, we associate it with the star-formation activity of the UV-bright clump, MACS0308-zD1.1. Assuming a gas mass of $M_{\rm H2}\,{\rm/M_{\odot}}=5.1\times10^{8}$ and a radius of $r=27\,{\rm pc}$, the line-of-sight velocity dispersion of a gas cloud will be $\sqrt{{\rm G} M/3r} = 167\,\rm{km/s}$, assuming virial equilibrium, where $\rm{G}$ is the gravitational constant. This value is consistent with the measured line width of the narrow component, suggesting that the ISM is supported by internal turbulent motion of the gas cloud.

On the other hand, the origin of the broad \[C ii\] emission is less clear. The broad line width and the velocity offset suggest that the broad \[C ii\] emission line could arise from a physically distinct region from the narrow \[C ii\] line. Additionally, the spatial extent of the broad \[C ii\] component shows that the broad \[C ii\] is spatially offset from the UV-bright star-forming region and the \[C ii\] emission associated with the UV-bright clump. Although the estimated virial velocity of the cloud is uncertain without a confident size measurement, the fact that the linewidth of the broad component appears super-virial suggests that this component of the gas cloud might not be bound. Combined with the extremely high density of star formation activity ($\Sigma_{\rm SFR}\sim900\,{\rm M_{\odot}\,yr^{-1}\,kpc^{-2}}$), circumstantial evidence suggests that the broad \[C ii\] might arise from gas outflowing from the intense star-forming region.

An alternative interpretation of the broad \[C ii\] component would be gas clumps generated as a result of the fragmentation of cold gas streams (i.e., inflow). Previous studies predicted such fragmentation of the cold gas streams in the inner halo ($\sim0.2\,R_{\rm v}$), where $R_{\rm v}$ is the virial radius (cite: Pallottini2017; Mandelker2018). After the fragmentation of cold gas streams, the masses of each clump are predicted to be order of $\sim10^{5}$ to $10^{7}\,{\rm M_{\odot}}$. The estimated gas mass from our observation ($M_{\rm H2}\sim4\times10^{8}\,{\rm M_{\odot}}$) suggest that several clumps exist along the line of sight or the case that we are observing "down the barrel" of the stream, which increase observed gas mass and velocity width of the line.

More quantitative examination requires several follow-up observations, such as higher resolution and higher sensitivity ALMA \[C ii\] follow-up and JWST’s rest-frame optical emission to reveal the stellar distribution down to much deeper limits. Also, to examine the extremely dense environment of the star-forming ISM, ALMA observations using higher resolution or observations of a neutral dense gas indicator such as \[O i\] will be needed.

# Conclusion

In this paper, we presented results of \[C ii\]$\,158\,\rm{\mu m}$ emission line scan observations of a strongly lensed ($\mu=22$) star-forming galaxy at $z\sim6.2$. We detected the \[C ii\] emission line within the expected frequency range. Additionally, no dust continuum was detected. Based on the observations, we found the following:

$\bullet$ A spectroscopic redshift of $z=6.2078\pm0.0002$ was determined, and the result is consistent with previous photometric redshift estimates (cite: Salmon2020; Weaver2022).

$\bullet$ The non-detection of the dust continuum emission suggests that MACS0308-zD1 is an almost dust-free environment. In particular, the UV-bright clump, MACS0308-zD1.1 has little dust-obscured SFR of $<0.1\,\rm{M_{\odot}\,yr^{-1}}$, and a low dust-obscured fraction of $<3\%$. The low dust-obscured activity is in stark contrast compared with the observations of other relatively massive $M_{\ast}>10^{9.5}\,\rm{M_{\odot}}$ star-forming galaxies (cite: Fudamoto2020; Schouws2022), and suggest that the stellar populations in this galaxy are young and metal-poor.

$\bullet$ From the relatively bright detection of the \[C ii\] emission line, we found that MACS0308-zD1.1 is consistent with the non-evolving SFR-$L_{\rm [CII]}$ correlation (cite: delooze2014; Schaerer2020). Also, the bright \[C ii\] emission suggests that the star-forming region of the galaxy may have an extremely dense molecular gas environment of ${\rm log}\,[\Sigma_{\rm H2}\,{\rm/(M_{\odot}\,pc^{2})}]=5.34\pm0.09$. With the extremely high density of star formation activity of $\Sigma_{\rm SFR}\sim900\,{\rm M_{\odot}\,yr^{-1}\,kpc^{-2}}$, the UV-bright star-forming region of MACS0308-zD1.1 is located in the most extreme edge of the Kennicutt-Schmidt relation (cite: Kennicutt2012).

$\bullet$ We found that the \[C ii\] emission line can be decomposed into two components; the narrow line ($\rm{FWHM}=110\pm19\,\rm{km/s}$) and the broad line ($\rm{FWHM}=233\pm19\,\rm{km/s}$). The broad component is blueshifted with respect to the narrow component with a velocity offset of $\Delta v = -80\pm20\,\rm{km/s}$. Although higher spatial resolution (e.g., matched to the HST/JWST resolutions of $\sim0.16^{\prime\prime}$) and higher sensitivity observations are required to conclude, the narrow component is most likely associated with a gravitationally bound gas cloud with intense star forming activity, as seen by the UV-bright clump, and the broad component may belong to kinematically and spatially distinct activity in the galaxy (e.g., possibly outflowing gas).

This spectroscopic redshift confirmation of a strongly lensed $L^{\ast}$ star-forming galaxy MACS0308-zD1 at $z=6.2078$ demonstrates viability of the future follow-up ALMA observations. Furthermore, JWST’s NIRSpec IFU observation will be critical to understand the morphologically and kinematically complex structure of this galaxy. With the large magnification of $\mu\sim20$, MACS0308-zD1 will serve as a unique test case to study low-SFR and low-mas galaxy growths in great detail in the future observations.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA #2021.1.00143.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. In addition, publications from NA authors must include the standard NRAO acknowledgement: The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. YF, YS, and AKI acknowledge support from NAOJ ALMA Scientific Research Grant number 2020-16B. PAO acknowledges support from the Swiss National Science Foundation through project grant 200020_207349. The Cosmic Dawn Center (DAWN) is funded by the Danish National Research Foundation under grant No. 140. EZ acknowledges funding from the Swedish National Space Agency and grant 2022-03804 from the Swedish Research Council (Vetenskapsrådet). MB acknowledges support from the Slovenian national research agency ARRS through grant N1-0238. A.Z. acknowledges support by grant No. 2020750 from the United States-Israel Binational Science Foundation (BSF) and grant No. 2109066 from the United States National Science Foundation (NSF), and by the Ministry of Science & Technology, Israel. FEB acknowledges support from ANID-Chile BASAL CATA FB210003, FONDECYT Regular 1200495 and 1190818, and Millennium Science Initiative Program – ICN12_009.

# Facilities

HST(STIS), ALMA

# Software

astropy (cite: astropy2022)

natexlab

(ref: Acebron2018) Acebron, A., Cibirka, N., Zitrin, A., et al. 2018, ApJ, 858, 42

(ref: Algera2023) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142

(ref: astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: Bakx2021) Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021, MNRAS, 508, L58

(ref: Bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: Bouwens2020) Bouwens, R., González-López, J., Aravena, M., et al. 2020, ApJ, 902, 112

(ref: Bouwens2022) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160

(ref: Bradac2017) Bradač, M., Garcia-Appadoo, D., Huang, K.-H., et al. 2017, ApJL, 836, L2

(ref: Calura2021) Calura, F., Vanzella, E., Carniani, S., et al. 2021, MNRAS, 500, 3083

(ref: Bean2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Coe2019) Coe, D., Salmon, B., Bradač, M., et al. 2019, ApJ, 884, 85

(ref: delooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: Dessauges2020) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5

(ref: Faisst2020) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: Fudamoto2022Td) Fudamoto, Y., Inoue, A. K., & Sugahara, Y. 2022a, arXiv e-prints, arXiv:2206.01879

(ref: Fudamoto2020) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, A&A, 643, A4

(ref: Fudamoto2021) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489

(ref: Fudamoto2022) Fudamoto, Y., Smit, R., Bowler, R. A. A., et al. 2022b, ApJ, 934, 144

(ref: Fujimoto2020) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1

(ref: Fujimoto2021) Fujimoto, S., Oguri, M., Brammer, G., et al. 2021, ApJ, 911, 99

(ref: Gaia2022) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2022, arXiv e-prints, arXiv:2208.00211

(ref: Garcia2022) Garcia, F. A. B., Ricotti, M., Sugimura, K., & Park, J. 2022, arXiv e-prints, arXiv:2212.13946

(ref: Ginolfi2020) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90

(ref: Harikane2020) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93

(ref: Hashimoto2018) Hashimoto, T., Laporte, N., Mawatari, K., et al. 2018, Nature, 557, 392

(ref: Hashimoto2019) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71

(ref: Heintz2021) Heintz, K. E., Watson, D., Oesch, P. A., Narayanan, D., & Madden, S. C. 2021, ApJ, 922, 147

(ref: Inami2022) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126

(ref: Inoue2014) Inoue, A. K., Shimizu, I., Tamura, Y., et al. 2014, ApJL, 780, L18

(ref: Jones2021) Jones, G. C., Vergani, D., Romano, M., et al. 2021, MNRAS, 507, 3540

(ref: Kennicutt2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531

(ref: Knudsen2016) Knudsen, K. K., Richard, J., Kneib, J.-P., et al. 2016, MNRAS, 462, L6

(ref: lefevre2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: Leroy2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: Liang2023) Liang, L., Feldmann, R., Murray, N., et al. 2023, arXiv e-prints, arXiv:2301.04149

(ref: Madau2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Maiolino2012) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66

(ref: Mandelker2018) Mandelker, N., van Dokkum, P. G., Brodie, J. P., van den Bosch, F. C., & Ceverino, D. 2018, ApJ, 861, 148

(ref: Matthee2019) Matthee, J., Sobral, D., Boogaard, L. A., et al. 2019, ApJ, 881, 124

(ref: Pallottini2017) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2017, MNRAS, 465, 2540

(ref: Salmon2020) Salmon, B., Coe, D., Bradley, L., et al. 2020, ApJ, 889, 189

(ref: Schaerer2020) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3

(ref: Schouws2022) Schouws, S., Stefanon, M., Bouwens, R., et al. 2022, ApJ, 928, 31

(ref: Sommovigo2022) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122

(ref: Stefanon2021) Stefanon, M., Labbé, I., Oesch, P. A., et al. 2021, ApJS, 257, 68

(ref: Sugahara2022) Sugahara, Y., Inoue, A. K., Fudamoto, Y., et al. 2022, ApJ, 935, 119

(ref: Treu2022) Treu, T., Roberts-Borsani, G., Bradac, M., et al. 2022, ApJ, 935, 110

(ref: Vallini2015) Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36

(ref: Vanzella2022) Vanzella, E., Claeyssens, A., Welch, B., et al. 2022, arXiv e-prints, arXiv:2211.09839

(ref: Weaver2022) Weaver, J. R., Davidzon, I., Toft, S., et al. 2022, arXiv e-prints, arXiv:2212.02512

(ref: Welch2023) Welch, B., Coe, D., Zitrin, A., et al. 2023, ApJ, 943, 2

(ref: Zanella2018) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

[^1]: <https://www2.nao.ac.jp/~eaarc/DATARED/support_data_reduction_en.html>

</paper>

Write the methods card for this paper.