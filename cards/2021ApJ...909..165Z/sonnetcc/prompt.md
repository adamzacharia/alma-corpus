# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...909..165Z\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...909..165Z",
 "title": "The Evolution of the IR Luminosity Function and Dust-obscured Star Formation over the Past 13 Billion Years",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Zavala, J. A.",
 "n_authors": 28,
 "arxiv_id": "2101.04734",
 "doi": "10.3847/1538-4357/abdb27",
 "alma_projects_linked_by_archive": [
  "2018.1.00231.S",
  "2018.1.00478.S",
  "2019.1.00838.S"
 ]
}
```

Paper text:
<paper>
# The Evolution of the IR Luminosity Function and Dust-obscured Star Formation in the Last 13 Billion Years

## Abstract

We present the first results from the 2 mm Mapping Obscuration to Reionization (MORA) survey, the largest ALMA blank-field contiguous survey to-date (184 arcmin$^2$) and the only at 2 mm to search for dusty star-forming galaxies (DSFGs). We use the 13 sources detected above $5\sigma$ to estimate the first ALMA galaxy number counts at this wavelength. These number counts are then combined with the state-of-the-art galaxy number counts at 1.2 mm and 3 mm and with a backward evolution model to place constraints on the evolution of the IR luminosity function and dust-obscured star formation in the last 13 billion years. Our results suggest a steep redshift evolution on the space density of DSFGs and confirm the flattening of the IR luminosity function at faint luminosities, with a slope of $\alpha_{\rm LF}=-0.42^{+0.02}_{-0.04}$. We conclude that the dust-obscured component, which peaks at $z\approx2-2.5$, has dominated the cosmic history of star formation for the past $\sim12$ billion years, back to $z\sim4$. At $z=5$, the dust-obscured star formation is estimated to be $\sim35\%$ of the total star formation rate density and decreases to $25\%-20\%$ at $z=6-7$, implying a minor contribution of dust-enshrouded star formation in the first billion years of the Universe. With the dust-obscured star formation history constrained up to the end of the epoch of reionization, our results provide a benchmark to test galaxy formation models, to study the galaxy mass assembly history, and to understand the dust and metal enrichment of the Universe at early times.\

\]

# Introduction

Mapping the cosmic history of star-formation is of fundamental importance in our understanding of galaxy formation and evolution not only because it contains the galaxy mass assembly history but also because it represents the footprint of the metal enrichment of the Universe.

A complete, unbiased determination of the star formation rate density (SFRD) requires a multi-wavelength approach to directly probe the stellar emission of new-born stars as well as the starlight that has been absorbed (then re-emitted) in dust-enshrouded regions. The former is efficiently measured using rest-frame ultraviolet (UV) observations and the latter using far-infrared (FIR) and (sub-)millimeter surveys that trace the dust re-processed emission from young stars (see (cite: Madau2014a) for a review).

The current UV census of star formation reaches out to $z\sim11$, close to the formation epoch of the first galaxies ((cite: Oesch2018a)). Nevertheless, despite some individual detections of dust in galaxies up to $z\sim8$ ((cite: Watson2015a; Laporte2017a)), studies of the global dust-obscured star formation rate density from FIR/sub-mm surveys are very limited at $z>3$.

The highest redshift estimations of the SFRD from FIR-to-mm surveys, at $z=4.5-5.5$, are uncertain even at the $\approx1.0-1.5\,$dex level ((cite: Rowan-Robinson2016a; Williams2019a; Loiacono2020a)) and differ by up to two order of magnitudes ((cite: Michalowski2017a) cf. (cite: Rowan-Robinson2016a)). This is mostly due to the low number statistics since most of the samples used to derive these measurements range from only one ((cite: Williams2019a; Loiacono2020a)) to a handful of objects ((cite: Dudzeviciute2020a; Gruppioni2020a)). This implies that the total amount of dust-enshrouded star formation in the earliest epochs of the Universe has remained unknown and, therefore, our current picture of the history of cosmic star formation remains incomplete.

This study aims at estimating the history of dust-obscured star formation back to $z\sim7$ by combining a backward galaxy evolution model of the dusty star-forming galaxy (DSFG) population ((cite: Casey2018b; Casey2018a)) with the state-of-the-art Atacama Large Millimeter/submillimeter Array (ALMA) surveys.

We infer constraints on the prevalence and characteristics of these galaxies through measurements of galaxy number counts at different wavelengths. Despite its relative conceptual simplicity, number counts have proven to be a very powerful tool to test and constrain galaxy formation models (e.g. (cite: Baugh2005a; Hayward2013a)), and consequently, represent an essential measurement in any long-wavelength survey.

The galaxy number counts used in this work include the first arcsecond-resolution interferometric number counts at 2 mm achieved with ALMA and the most recent estimations at 1.2 mm and 3 mm. The former is from our new 2 mm Mapping Obscuration to Reionization (MORA) survey described in §[2](#sec:MORA), the first ALMA large map at this wavelength with a total area of 184 arcmin$^2$ (an order of magnitude larger than previous interferometric blind surveys). At 3 mm, the measurements come from the $\sim200\,$arcmin$^2$ ALMA archival program reported in (cite: Zavala2018c), which we revise in this work after finding three false detections in their sample (see §[3](#secc:3mm_num_counts)). These number counts are also complemented with those from the 4.2 arcmin$^2$ deep ALMA large program ASPECS survey (at 1.2 mm and 3 mm; (cite: Gonzalez-Lopez2019a; Gonzalez-Lopez2020a)), in which 40 continuum sources were detected. All these surveys represent the state-of-the-art observations at long wavelengths, comprising not only the deepest measurements at those wavebands (beyond those assisted by gravitational amplification), but also the only interferometric surveys at 2 and 3 mm, which are crucial to constraining the infrared (IR) luminosity function (IRLF) at high-redshift (see discussion by (cite: Bethermin2015a; Casey2018b; Casey2018a; Zavala2018c), and (cite: Wilner1997a) for a pioneering $\sim3\,$mm survey).

The constraints provided by these surveys and by all the far-infrared and sub-millimeter data aggregated over the last two decades, allow us to infer the IR luminosity function and dust-obscured star formation in the last 13 billion years of the Universe, pushing the current redshift limits from $z\sim4-5$ to $z\sim7$. Our constraints are discussed in §[4](#secc4) and summarized in §[5](#secc:conclusions).

Trough this work we assume $H_0=67.7\,\rm km\,s^{-1}\,Mpc^{-1}$ and $\Omega_{\lambda}=0.69$ ((cite: Planck2016a)), and a Chabrier initial mass function ((cite: Chabrier2003a)) for SFR estimations.

# Mapping Obscuration to Reionization ALMA (MORA) Survey

The MORA survey (ALMA project code: 2018.1.00231.S, PI: C. Casey) was originally designed to cover a contiguous area of $\rm230\,$arcmin$^2$ in two different tunings in the 2 mm band (centered at 147.3 GHz and 139 GHz, respectively). The project was only partially observed, covering $\rm184\,$arcmin$^2$ in two separate mosaics of $\rm156\,$arcmin$^2$ and $\rm28\,$arcmin$^2$, respectively. The largest mosaic, which covers the positions 10 to 20 from the original design and so-called P10-P20, is centered at $\alpha\rm\approx10\,h\,00\,m\,17\,s$, $\delta\approx+02^\circ\,22'\,30''$ and covers an area of $6.6'\times23.6'$. The smaller one (P03) is centered at $\alpha\rm\approx10\,h\,00\,m\,44\,s$, $\delta\approx+02^\circ\,22'\,30''$ and has $1.2'\times23.6'$ dimensions (see Figure [1](#fig:map)). The deepest portion of the mosaics has an RMS of $\sigma_{\rm 2mm}=60\,\mu\rm Jy\,beam$, with $101\,$arcmin$^2$ covered at or below the proposed map depth of $90\,\mu\rm Jy\,beam$ (see Figures [1](#fig:map) and [2](#fig:area)), with a typical beamsize of $\theta_{\rm FWHM}\approx1.8''\times1.4''$. This project represents the largest ALMA blank-field survey to-date and the only at 2 mm to search for dusty star-forming galaxies.

![](mosiac_map_modified2.eps)

![](area_per_noise.eps)

The signal-to-noise ratio (SNR) maps are well modelled by Gaussian statistics within $-4.5\lesssim\rm SNR \lesssim 4.5$ (see Figure [3](#fig:pixels_histogram)). Above $4.5\sigma$ the excess of positive pixels comes from the detection of astronomical sources, as expected. Interestingly, there is also an excess of negative pixels with $\rm SNR<-5$. All these pixels (identified in orange in the figure) come from the same region and are associated with a single noise peak at $-6\sigma$ (plus the effect of beam smearing; see Figure [1](#fig:map)). Nevertheless, assuming Gaussian statistics, the probability of finding a $-6\sigma$ noise peak in our mapped area is $\lesssim0.5\%$. An alternative explanation might be the Sunayev-Zeldovich (SZ) effect ((cite: Sunyaev1970a)) since its peak decrement is expected close to the observed frequency of our maps ($\sim145\,$GHz). A thorough discussion of the nature of this negative detection will be presented in a future work, after carrying out the required follow-up observations.

Casey et al. (in preparation) will present further details of the survey along with a description of the source catalog and other physical characteristics of the 2 mm-selected galaxies. Briefly, we first create a noise map using two different approaches. In the first one, we measure the standard deviation of all the pixels with primary beam responses between 0.95 and 1, which give us the minimum noise in our mosaic (or maximum depth); then we multiply the inverse of the primary beam response map by this minimum noise vale, whose result is adopted as the noise map. In the second approach, we use a 2D boxcar-like function across the primary beam corrected flux mosaic (after applying a sigma clipping procedure to remove the bright sources) to estimate the noise in each pixel, measured as the standard deviation of the pixels within the squared region of the boxcar-like function. Both procedures give us consistent results within $\sim1$%. Once we have a noise map, we simply divide the primary beam corrected flux map by this noise mosaic in order to obtain a SNR map (which is shown in Figure [1](#fig:map)). This SNR map is then used to find source candidates by searching for pixels above a SNR threshold. Here, we use the sources detected at $>5\sigma$ (where the false detection rate is expected to be $\lesssim8\%$; see §[2.1](#secc:num_counts)) to calculate the first ALMA number counts at 2 mm, as described below.

![](noise_pixel_histogram.eps)

## The 2 mm number counts

The cumulative number counts – i.e. the number of galaxies above a certain flux density threshold, $S$, per unit area – can be directly estimated by counting the number of detected galaxies as a function of flux density and making the required corrections for contamination, completeness and flux boosting.

Previous blind ALMA surveys have estimated a minimum, close-to-zero, contamination fraction due to false detections (noise peaks) for SNR thresholds in the range of $\approx4-5$ (e.g. (cite: Fujimoto2016a; Oteo2016a)). Nevertheless, despite adopting a conservative threshold of $5\sigma$ in our analysis (see Figure [3](#fig:pixels_histogram)), a thorough characterization of the contamination rate is required given the large area covered by the MORA survey and the large number of independent beams in the maps.

The false detection rate of the MORA survey is characterized as follows: first, we create noise maps with the same dimensions as the original maps under the assumption that the noise in the ALMA observations is well represented by Gaussian statistics (as has been shown before for other ALMA data, e.g. (cite: Franco2018a), and demonstrated in Figure [3](#fig:pixels_histogram)). Second, the maps are convolved with a beam representative of the average synthesized beam in our observations. Then, to characterize the contamination rate as a function of SNR, the map is scaled such that the final standard deviation of the whole distribution of pixels is equal to one. This is equivalent to a SNR map with no astronomical sources. Finally, we simply quantify the number of peaks above the adopted detection threshold using the same algorithm used to find the real sources. This process is repeated 100 times in order to measure the expected number of false sources and its corresponding uncertainty. At our adopted threshold of $5\sigma$, the expected number of false detections in the MORA catalog is $0.8\pm0.2$. This is in good agreement with the findings in Casey et al. in preparation, who found near-IR counterparts for all the MORA detections with the exception of the lowest significance source in the catalog.

To take into account this false detection rate in the number counts calculation, a statistical approach is adopted in which the contamination fraction is distributed among the 13 sources according to their SNRs with a proportionality given by a normal probability distribution (i.e. estimating the probability that a normal random variable is greater than the sources’ SNRs). As expected, this procedure gives a higher probability of false detection to the sources with the lowest SNRs and an (almost) negligible probability to those detected at $\gtrsim5.5\sigma$.

The survey completeness is calculated in a similar fashion in which artificial sources are inserted in the real maps (after removing the bright detections) followed by computing the ratio between the recovered sources and inserted sources. The artificial sources are inserted, one at a time, at random positions around the whole mosaic and then they are recovered with the same source extraction procedure used to build the real source catalog. The survey completeness can be estimated as a function of input flux density, recovered flux density, detected SNR, local noise RMS, or a combination of these parameters. A source is considered recovered if it is detected within a synthesized beam from the input position ($\sim1.5''$). In each flux density bin of $25\,\rm\mu Jy$, we repeat this process 10,000 times in order to sample the noise variation across the maps.

The same set of simulations are used to examine the flux-boosting effects (meaning sources’ flux densities systematically biased upwards by noise and the presence of fainter undetected sources). This is done by estimating the average ratio between the sources’ intrinsic flux density and the recovered flux density in the simulations. Again, this value depends on the flux density and on the local noise of each source (or similarly, SNR), and therefore, several flux boosting factors can be derived as a function of these parameters. In average, we find flux boosting factors of around $5\%$ for those source detected just above our SNR threshold. These factors, which decrease with increasing SNR, are however much lower than the uncertainties on the measured flux densities ($\sim20\%$ for a $5\sigma$ detection).

The number counts can then be directly estimated by counting the number of detected galaxies as a function of flux density and making the appropriate corrections for contamination, completeness and flux boosting. We estimate the contribution of a source with a deboosted flux density, $S_i$, and measured SNR, $\sigma_i$, to the cumulative number counts to be: $$\begin{equation}
\eta_i(S_i,\sigma_i)=\frac{1-f_{\rm cont}(\sigma_i)}{\zeta(S_i)\,A_{\rm eff}},
\end{equation}$$ where $f_{\rm cont}(\sigma_i)$ is the estimated fraction of contamination at the measured SNR ($\sigma_i$) of the source, $\zeta$ is the corresponding completeness for a deboosted flux density $S_i$, and $A_{\rm eff}$ is the total area of the MORA maps used for source extraction (i.e. $184\,$sq. arcmin$^2$; see Figure [2](#fig:area)). Finally, the cumulative number counts, $N(>S)$, are estimated by the sum over all sources with a flux density higher than $S$, i.e. $N(>S)=\sum\limits_{i}\eta_i(S_i,\sigma_i)$.

![](2mm_num_counts.eps)

+:-------------:+:---------------:+:------------:+:------------:+:-------------:+:---------------:+:------------:+:------------:+
| Raw number counts                                             | Star-forming galaxies number counts                           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| $S_{\rm 2mm}$ | N($\rm >S_\nu$) | $\delta N^-$ | $\delta N^+$ | $S_{\rm 2mm}$ | N($\rm >S_\nu$) | $\delta N^-$ | $\delta N^+$ |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| ($\rm mJy$)   | (deg$^{-2}$)    | (deg$^{-2}$) | (deg$^{-2}$) | ($\rm mJy$)   | (deg$^{-2}$)    | (deg$^{-2}$) | (deg$^{-2}$) |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.33          | 440             | 120          | 60           | 0.33          | 380             | 110          | 150          |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.36          | 370             | 110          | 140          | 0.36          | 320             | 100          | 130          |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.39          | 310             | 90           | 130          | 0.39          | 270             | 80           | 110          |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.41          | 260             | 80           | 110          | 0.48          | 220             | 70           | 100          |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.48          | 220             | 70           | 100          | 0.52          | 185             | 64           | 91           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.52          | 185             | 64           | 91           | 0.54          | 157             | 59           | 85           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.54          | 157             | 59           | 85           | 0.57          | 131             | 53           | 79           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.57          | 131             | 53           | 79           | 0.61          | 106             | 47           | 72           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.61          | 106             | 47           | 72           | 0.68          | 83              | 41           | 65           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.68          | 83              | 41           | 65           | 0.78          | 60              | 34           | 59           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.78          | 60              | 34           | 59           | 0.88          | 41              | 27           | 53           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 0.88          | 41              | 27           | 53           | 1.03          | 21              | 17           | 47           |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+
| 1.03          | 21              | 17           | 47           |               |                 |              |              |
+---------------+-----------------+--------------+--------------+---------------+-----------------+--------------+--------------+

: MORA survey 2 mm number counts.

Table notes: The star-forming galaxy number counts are estimated after removing source MORA-10, whose flux density falls below our detection threshold after removing the contribution from synchrotron emission.

In order to take into account the uncertainties associated with the correction factors (completeness and false detection) and flux densities in the estimation of the number counts, we perform a Monte Carlo simulation. In each realization, the adopted measured flux density for each source, $S_i$, is extracted from a Gaussian distribution with a standard deviation equal to the measured error and centered at the observed value. Then, this new flux density is used to estimate a new SNR, $\sigma_i$, by dividing by the local noise. These SNRs are then used to update the contamination fraction and completeness accordingly, whose new values are drawn from Gaussian distributions.

This procedure is repeated 100 times, with the mean values representing the final number counts and the 16th and 85th percentiles their associated confidence interval. Finally, given the relatively small number of sources in our catalog, Poisson uncertainties are added in quadrature according to (cite: Gehrels1986a). The MORA 2 mm number counts derived in this work are reported in Table [1](#table:moras_num_counts) and are show in Figure [4](#fig:moras_num_counts).

Given that the 2 mm flux density of one of our sources, MORA-10, was found to be contaminated by synchrotron emission (at a $\sim40\%$ level; Casey et al. in preparation), we repeat all the process described above after removing this source, aiming at providing the 2 mm number counts of star-forming galaxies only (note that the source would have been fallen below our detection threshold without the synchrotron emission). This is particularly important since the model used in §[4.1](#secc:model) does no take into account non-thermal emission, nevertheless, we highlight that the difference between the two estimations is not significant (see Table [1](#table:moras_num_counts)).

At this wavelength, the only determinations of the number counts reported in the literature beyond our MORA survey measurements come from the GISMO/IRAM surveys reported in (cite: Staguhn2014a) and (cite: Magnelli2019a), covering $31\,$arcmin$^2$ and $250\,$arcmin$^2$, respectively. The latter are in very good agreement with our estimations while the former lie above by a factor of $\approx2.0-2.5$. This over-estimation is thought to be caused by the uncertainties in the flux deboosting factors in the confusion-limited map of (cite: Staguhn2014a), as discussed in (cite: Magnelli2019a), although cosmic variance might be also important given the relatively small mapped area. The predictions from the shark semi-analytic model of galaxy formation ((cite: Lagos2020)) are also plotted in the figure, which are indeed in very good agreement with our estimations.

# Revising the 3 mm number counts

(cite: Zavala2018c) compiled archival ALMA band 3 observations toward three extragalactic legacy fields: COSMOS, CDF-S, and the UDS, resulting in a total of 135 individual maps adding up a total area of $\approx200\,\rm arcmin^2$. After masking out the original targets of these observations and any galaxies that were potentially physically associated with them, they derived the first ALMA galaxy number counts at $3\,$mm using a total of 13 sources detected above $5\sigma$.

Our recent ALMA 2mm + 3mm follow-up observations on this sample (ALMA projects: 2018.1.00478.S and 2019.1.00838.S; PI: J. Zavala) show that three of these sources (ALMA-3mm.14, ALMA-3mm.15, and ALMA-3mm.16) are not recovered, meaning they are likely spurious detections. Two of these sources were indeed noted to have a spectral index which might be inconsistent with thermal emission in (cite: Zavala2018c), nevertheless, without further data at the time, the low SNRs ($5.0-5.2$) prevented a firm conclusion and therefore they were included in the previous number counts estimation.

Thus, we have revised the false detection rate to be higher than the value reported in the original work of (cite: Zavala2018c), for which only one source was expected to be false. This highlights the complexity of the interferometric data, particularly when using observations with different beamsizes, integration times, and array configurations, as is typical for datasets derived from archival projects.

|                |                 |              |              |
|:--------------:|:---------------:|:------------:|:------------:|
| $S_{\rm 3mm}$  | N($\rm >S_\nu$) | $\delta N^-$ | $\delta N^+$ |
| ($\rm \mu Jy$) |  (deg$^{-2}$)   | (deg$^{-2}$) | (deg$^{-2}$) |
|       33       |      4440       |     1200     |     1990     |
|       52       |      2140       |     640      |     1000     |
|       63       |      1420       |     470      |     710      |
|       79       |       990       |     360      |     540      |
|       98       |       750       |     290      |     450      |
|      109       |       550       |     230      |     370      |
|      117       |       410       |     190      |     320      |
|      127       |       290       |     150      |     280      |
|      137       |       170       |     110      |     230      |
|      167       |       74        |      55      |     170      |

: Revised ALMA archival 3 mm number counts.

Here, we revised the 3 mm number counts following exactly the same procedure as described in (cite: Zavala2018c) but removing the three spurious sources. Additionally, we updated the flux density of the source ALMA-3mm.03 (a.k.a. ASPECS-3mm.1) since the reported value in (cite: Zavala2018c) seems to be contaminated by a bright CO emission line ((cite: Gonzalez-Lopez2019a)); we thus adopt the flux density reported in the ASPECS catalog.

The revised 3 mm number counts are reported in Table [2](#table:revised_num_counts) and shown in Figure [5](#fig:num_counts). The new values are significantly different at the bright end ($S_{\rm 3mm}>0.2\,$mJy) since two of the false detections were the brightest galaxies in the sample[^1]. At fainter flux densities, the updated number counts are a factor of $\sim1.5\times$ lower, and thus, in better agreement with the ASPECS results ((cite: Gonzalez-Lopez2019a)), although still a factor of $\sim2\times$ higher. Nevertheless, the two number counts are consistent with each other within the uncertainties. The difference is thus not statistically significant.

# Constraining the IR luminosity function and dust-obscured star formation rate density

In this section we use a backward evolution model in combination with the state-of-the-art FIR/mm surveys to constrain the IR luminosity function. The model draws spectral energy distributions (SEDs) from the known breadth and characteristics of dusty galaxies, then works backward to discriminate between different luminosity function scenarios using the galaxy number counts as constraints. Finally, the dust-obscured star formation rate density is estimated by integrating the best-fit IR luminosity function (see (cite: Zavala2018c) for a similar analysis).

## Model description

The adopted backwards evolution model is described in detail in (cite: Casey2018b; Casey2018a), where the specifics of the model and the assumed values for each parameter can be found. A summary of the salient characteristics and assumptions follows.

The model combines a parameterized evolving galaxy IR luminosity function with the thermal SED properties of galaxies’ dust emission to make predictions for galaxy (sub-)millimeter surveys.

Galaxies’ SEDs are described by a modified black-body function of the form $S_\nu\propto(1-e^{-(\nu/\nu_0)^{\beta_{\rm em}}})B_\nu(T_{\rm dust})$ with an extra mid-infrared power law to account for hotter dust emission at $T\gg T_{\rm dust}$ (e.g. (cite: Casey2012a)). The SED library follows the well-known luminosity-temperature relationship in terms of $L_{\rm IR}-\lambda_{\rm peak}$ and takes into account the observed dispersion in this relation. We highlight that using the peak wavelength rather than dust temperature minimizes the impact of the assumed effective dust opacity in the model ($\tau=1$ at $\lambda_{\rm rest}=100\,\rm\mu m$), which could change the derived dust temperature but has a minor impact on the measured $\lambda_{\rm peak}$. Note that although this relation is not assumed to evolve with redshift (which is supported by the current data at least up to $z\sim4.5$ (cite: Casey2018a; Dudzeviciute2020a)), if one selects galaxies on the main sequence, a redshift evolution of $\lambda_{\rm peak}$ (proportionally to dust temperature) naturally arises. This evolution, which is driven by the underlying evolution of the main sequence of star-forming galaxies, is in line with recent results from the literature (e.g. (cite: Bethermin2015a; Schreiber2015a; Magdis2017a)).

As is common practice in the literature (e.g. (cite: Sanders2003a; Magnelli2011a; Magnelli2013a; Lim2020a)), the assumed IR luminosity function in the model is described by a double power law of the form:

$$\begin{equation}
\Phi(L,z) =
  \begin{cases} 
      \Phi_\star(z)\left(\frac{L}{L_\star(z)}\right)^{\alpha_{\rm LF}},               & \mbox{if } L<L_\star, \\
      \Phi_\star(z)\left(\frac{L}{L_\star(z)} \right)^{\beta_{\rm LF}},               & \mbox{if } L\ge L_\star,
  \end{cases}
\end{equation}$$ where $\alpha_{\rm LF}$ and $\beta_{\rm LF}$, represent the slopes at faint and bright luminosities, respectively, while $L_\star$ and $\Phi_\star$ are the characteristic galaxy luminosity and characteristic number density, two fundamental parameters that are allowed to evolve with redshift.

Following previous works from the literature, the characteristic number density is assumed to evolve as:

$$\begin{equation}
\Phi_\star \propto
  \begin{cases} 
       (1+z)^{\Psi_1},  & \mbox{if } z<z_{\rm turn}, \\
     (1+z)^{\Psi_2},   & \mbox{if } z\ge z_{\rm turn}.
  \end{cases}
\end{equation}$$

Significant observational efforts have provided good constraints on the evolution of $\Phi_\star$ at low redshifts, revealing a flat trend with $\Psi_1$ close to zero and a turnover redshift of $z_{\rm turn}\approx2$, in-line with the peak of the cosmic star formation rate density (CSFRD; (cite: Magnelli2011a; Gruppioni2013a; Lim2020a)). Although it is clear that at higher redshifts the evolution is significantly steeper, the current estimations are highly uncertain and limited to $z\lesssim4$, with values ranging from $\Psi_2\sim-6$ (or lower; (cite: Koprowski2017a)) to $-2$ (or even higher; (cite: Rowan-Robinson2016a)), with a few measurements in between. Indeed, (cite: Zavala2018c) found an intermediate value of $\Psi_2\approx-4.2$ using the initial 3 mm sample.

In this work, we aim to constrain two of the most important unknowns of the galaxy luminosity function: the faint-end slope, $\alpha_{\rm LF}$, and the redshift evolution of the characteristic number density at high redshift driven by $\Psi_2$ (since $\Phi_\star\propto(1+z)^{\Psi_2}$ for $z\gtrsim2$). We also explore different values of the dust emissivity index, $\beta_{\rm em}$, in order to minimize any possible bias and to test possible degeneracies between the different parameters.

For the rest of the model parameters, we adopt the same values as in (cite: Casey2018a) and (cite: Zavala2018c). We refer the reader to (cite: Casey2018a) ((cite: Casey2018a), and particularly to its appendix A.1) for a detail discussion about these choices and their impact on the model. In short, the bright-end slope of the luminosity function is fixed to be $\beta_{\rm LF}=-3.0$. This value is relatively well-constrained (at least up to $z\sim4$) with a measured dispersion of $1\sigma\approx0.15$.

The evolution of the characteristic luminosity, $L_\star$, follows $L_\star\propto(1+z)^{\gamma_1}$ for $z<z_{\rm turn}$ and $L_\star\propto(1+z)^{\gamma_2}$ for $z\ge z_{\rm turn}$. While the evolution at lower redshifts ($z<z_{\rm turn}$) is well-characterized (we adopt $\gamma_1=2.8$), the evolution of $L_\star$ beyond $z_{\rm turn}$ is more uncertain. The model adopts $\gamma_2=1.0$, implying that $L_\star$ continues to evolve upward toward higher redshifts, in line with expectations for hierarchical structure formation and cosmic downsizing. Additionally, adopting $\gamma_2=1.0$ makes the $L_\star$ evolution consistent with the $L_\star$ of the quasar luminosity function ((cite: Hopkins2007a)). Adopting a reversal evolution ($\gamma_2\le0$) under-predicts the number counts at wavelengths longer than $\sim850\rm\,\mu m$, regardless of the adopted number density (for any $\Psi_2<-1.5$), while a more rapid evolution with $\gamma_2\ge1.5$ would imply very bright values for $L_\star$ at $z\sim5$, which might even exceed the luminosity of the brightest DSGFs known to-date. Moreover, in order to match the contribution from LIRGs and ULIRGs to the cosmic SFRD at $z<2.5$ to those reported in the literature, a modest dependence of $z_{\rm turn}$ on $\Psi_2$ of the form $z_{\rm turn}=1.6-0.09\Psi_2$ has to be adopted (see (cite: Casey2018a) for details).

This model has some caveats that the reader should keep in mind. The exact values of $L_0$ and $\Phi_0$ are correlated with $\gamma_1$ and $\Psi_1$, respectively[^2]. As discussed in detailed by (cite: Casey2018a). The adopted values ($L_0=10^{11.1}\,L_\odot$, $\Phi_o=10^{-3.5}\rm\,Mpc^{-3}\,dex^{-1}$, $\gamma_1=2.8$, and $\Psi_1=0$) were chosen to simultaneously reproduce: *(i)* the IRLF at $z\lesssim2$; *(ii)* the reported values of $L_\star$ and $\Phi_\star$ from the literature; and *(iii)* the relative contribution from LIRGs and ULIRGs to the total SFRD within $0<z<2$. This combination of values are, however, not necessarily unique. Another caveat that the reader should keep in mind is the assumption of a fixed emissivity spectral index at all redshifts, and although several values were explored in the analysis (from $\beta=1.6$ to 2.6, see Figure [6](#fig:triangle_plot)), each realization adopts a single value across all redshifts for all sources. This is not necessarily in disagreement with previous literature, given the current limited data. Although a spread on $\beta$ has been found across different galaxies, these variations have not yet been shown to correlate with redshift or other galaxy characteristics that may impact the model. Indeed, there are clear examples of $\beta\sim1.5$ to $\sim2.0$ in both local galaxies (e.g. (cite: Remy-Ruyer2013a)) and high-redshift systems (e.g. (cite: Jin2019a)). The same is true for the adopted slopes of the luminosity function at both the faint and bright ends ($\alpha_{\rm LF}$ and $\beta_{\rm LF}$, respectively). Although a redshift evolution is possible given that we know similar parameters do evolve for the UV luminosity function (e.g. (cite: Finkelstein2015a)), the lack of samples of galaxies with spectroscopic redshifts covering a wide range of IR luminosities prevents its confirmation (or rejection). Indeed, non-evolving slopes have been been adopted in several works in the literature (e.g. (cite: Magnelli2011a; Magnelli2013a; Gruppioni2013a; Lim2020a)). Therefore, in the absence of more information, we choose to fix these quantities. The impact of these assumptions on our results are further discussed below.

## Fitting methodology and data constraints

To find the best-fit model parameters, first, the different evolutionary scenarios of the IRLF are combined with galaxies’ SEDs to create mock observations that resemble the real surveys in terms of wavelength, noise depth, and angular resolution, with the CMB heating effects taken into account (following (cite: daCunha2013a)). Second, the respective number counts are estimated in a similar fashion as in the real observational works. These simulated number counts are then compared to the measured number counts in a joint analysis that combines multiple observations at different wavelengths simultaneously. Finally, the best-fit model parameters that better reproduce all the observed number counts are derived.

The cumulative number counts are preferred over the differential number counts since the latter suffer from larger uncertainties due to the relative small number of sources in each flux density bin. Though we test that adopting the differential number counts instead do not change significantly our results.

As discussed in (cite: Casey2018b; Casey2018a), observations at long-wavelengths ($\lambda\gtrsim1\,$mm) are ideal to distinguish between the different scenarios of the model since the majority of constraining data sets at shorter wavelengths only inform about the evolution of the IRLF at $z\lesssim3.0$, where the model parameters are already relatively well understood. Therefore, here we only use number counts at 1.2 mm, 2 mm and 3 mm as constraints, which also reduces significantly the computational cost of the fitting analysis, which would be prohibitive otherwise. We adopt the MORA 2 mm number counts described above (see §[2.1](#secc:num_counts)), the updated 3 mm number counts reported in this work (see §[3](#secc:3mm_num_counts)), and the 1.2 mm and 3 mm number counts from the ASPECS survey ((cite: Gonzalez-Lopez2019a; Gonzalez-Lopez2020a)). Altogether, these surveys add a total of $\sim400\,$sq. arcmin surveyed area and around 60 detected galaxies. Note that AGN contribution or non-thermal emission (e.g. synchrotron emission) is expected to be negligible at these wavebands and at the flux density ranges explored here[^3] (see discussion in (cite: Casey2018b; Zavala2018c)).

Once the fiducial number counts have been defined, to derive the best-fit model parameters that better reproduce these number counts we use two different methods: a maximum likelihood approach and a multi-dimensional minimization algorithm.

The maximum likelihood approach is done in a similar fashion as reported by (cite: Zavala2018c). We create a three-dimensional grid, representing the parameter space formed by $\alpha_{\rm LF}$, $\Psi_2$, and $\beta_{\rm em}$, with values ranging from $\alpha_{\rm LF}: [-0.6,-0.2]$ in steps of 0.05, $\Psi_2: [-8.8,-2.2]$ in steps of 0.4, and $\beta_{\rm em}: [1.5,2.6]$ in steps of 0.05. For each combination of the parameters subset (corresponding to different points in the grid), the likelihood function of the measured cumulative number counts relative to the simulated number counts is estimated. Finally, the best-fit model is assumed to be the one with the highest probability, and the confidence intervals at 68%, 95%, and 99.7% are obtained by integrating the normalized likelihood distribution.

![](best_fit_number_counts_breakdown.eps)

The Nelder–Mead optimization method (a.k.a the Amoeba method; (cite: Nelder1965a; numerical_recipes)) relies on a downhill simplex algorithm to perform a multidimensional minimization of a given parameter, in this case, the square differences ($\chi^2$) between the real and the modeled cumulative number counts. In each realization, we randomly vary the initial starting point of the search, with each search limited to 100 evaluations. During this analysis, we introduce a fourth parameter, $z_{\rm cutoff}$, following (cite: Zavala2018c), which represents the redshift above which no more dusty galaxies exist (with a range of $z_{\rm cutoff}=5.5-9.0$). Nevertheless, we find that $z_{\rm cutoff}$ is not well constrained by the data and has a minor impact on the analysis.

As shown in Figure [5](#fig:num_counts), the best-fit number counts recovered from the model are in good agreement with the measured values, reproducing simultaneously not only the data used in the fitting but also the rest of measurements reported in the literature, as discussed below.

At 1.2 mm, beyond the ASPECS number counts, the model predictions nicely reproduce the number counts from the 1.6 deg$^2$ AzTEC surveys reported in (cite: Scott2012a) and those from the ALMA follow-up survey of SCUBA-2 galaxies detected over $\sim1\rm\,deg^2$ reported by (cite: Stach2018a)[^4], which probe the brightest flux densities. At fainter flux densities, the model also reproduces the more recent ALMA results from (cite: Dunlop2017a) and (cite: Umehata2017a). The number counts from the GOODS-ALMA survey ((cite: Franco2018a); covering the flux density range of $S_{\rm1.2mm}\approx0.5-2\,$mJy) are, however, lower than our estimations, and those reported by (cite: Fujimoto2016a) (which probe the faintest flux densities in the figure) lie above our estimations. Note, however, that the measurements reported by (cite: Fujimoto2016a) come from gravitationally lensed fields, and therefore, these discrepancies might be caused by the uncertainties in the magnification factors and small survey area (see discussion in (cite: Gonzalez-Lopez2020a)). The discrepancy with the (cite: Franco2018a) results is likely related to the relatively low completeness associated with their high angular resolution observations ($\theta_{\rm FWHM}=0.29''$ and $\theta_{\rm FWHM}=0.60''$ after filtering the data).

At 2 mm, the only determinations of the number counts reported in the literature beyond our MORA survey measurements come from the GISMO/IRAM surveys reported in (cite: Staguhn2014a) and (cite: Magnelli2019a), covering $31\,$arcmin$^2$ and $250\,$arcmin$^2$, respectively. The latter are in very good agreement with the model predictions while the former lie above by a factor of $\approx2.0-2.5$. This difference is thought to be caused by the uncertainties in the flux deboosting factors in the confusion-limited map of (cite: Staguhn2014a), as discussed in (cite: Magnelli2019a), plus the possible effects of cosmic variance (see §[2.1](#secc:num_counts)).

At 3 mm, the only measurement plotted in Figure [5](#fig:num_counts) which was not used in our analysis, is the brightest bin of the ASPECS survey, which represents only an upper limit. This value is, however, in good agreement with the model predictions.

The success of the model can also be illustrated by its predicting power at other wavelengths. The model does reproduce the number counts at shorter wavelengths, from $70\,\mu\rm m$ to $850\,\mu\rm m$ spanning over two decades of observations over hundreds of square degrees (see Appendix [6](#appendix)).

## The IRLF and best-fit parameters

As it is clearly shown in Figure [6](#fig:triangle_plot), both methods provide consistent results and good constraints on the model parameters governing the IRLF while successfully reproducing the observed number counts (see Figures [5](#fig:num_counts) and [9](#fig:num_counts_short_waves)).

![](triangle_plot_v2.eps)

The faint-end slope of the infrared luminosity function is found to be flat, with $\alpha_{\rm LF}=-0.42^{+0.02}_{-0.04}$. This is in line with recent studies based on the deepest single-dish observations and interferometric surveys (although those were limited to lower redshifts), with reported values of $\alpha_{\rm LF}=-0.4$ ((cite: Koprowski2017a)) and $-0.5\pm0.7$ ((cite: Lim2020a)), and with the observed flattening in the 1.1 mm luminosity function ((cite: Popping2020a)).

Although the faint-end slope is fixed for all redshifts in our model, we highlight that an evolution to steeper values with increasing redshift is inconsistent with our data and with the very low number of $z>4$ galaxies detected in the deepest ALMA surveys ((cite: Dunlop2017a; Hatsukade2018a; Aravena2020a)). Indeed, most of the sources in the ASPECS survey lie at $z<3$ ((cite: Aravena2020a)), in good agreement with our model predictions (see Figure [5](#fig:num_counts)). This IR flat slope contrasts with the steep faint-end slope of the UV luminosity function at high redshift, which ranges from $-1.6$ at $z\sim4$ to $-2.0$ at $z\sim7$ (e.g. (cite: McLure2013a; Finkelstein2015a)). As a consequence, deep pencil-beam observations at (sub-)mm wavelengths would not significantly increase the number of detected sources, as is commonly the case in the rest-frame UV/optical observations (e.g. (cite: Ferguson2000a)).

Regarding the evolution of the characteristic number density at high redshift, the best-fit $\Psi_2$ value of $-6.5^{+0.8}_{-1.8}$ implies a steep redshift evolution of the IR number density ($\Phi_\star\propto(1+z)^{-6.5^{+0.8}_{-1.8}}$), which disfavours the dust-rich hypothetical model discussed in (cite: Casey2018a), for which a value of $\Phi_\star\propto(1+z)^{-2.5}$ was adopted. This indicates that dusty star-forming galaxies are indeed *rare* at early epochs. This steep evolution is also in line with the rapid drop-off of the quasar luminosity function at high redshift ((cite: Hopkins2007a)) and similar to the number density evolution of UV-bright (M$_{\rm UV}=-$21) galaxies ($\propto(1+z)^{-5.9}$; (cite: Finkelstein2015a)), which might suggest that these galaxies occupy similar dark matter halos.

There is, though, a caveat related to the effective dust optical opacity of our SEDs that the reader should keep in mind. Although, as mentioned before, the SEDs are parameterized in term of $\lambda_{\rm peak}$ rather than dust temperature, incorporating the CMB effects on the heating and detectability of the sources requires an estimation of the dust temperature ((cite: daCunha2013a)). Assuming an optically thin opacity form would result in lower dust temperatures for the same $\lambda_{\rm peak}$ than those derived from the optically thick model, decreasing the contrast between the dust emission and the CMB. This implies that, in order to match the measured number counts, a higher number of galaxies would be required compared to the optically thick model, i.e. a higher $\Psi_2$ value (see discussion in (cite: Zavala2018c)). Nevertheless, this effect is only important if the number counts are dominated by very high-redshift ($z>6$) sources, which our results suggest is likely not the case.

Finally, Figure [6](#fig:triangle_plot) shows that the dust emissivity spectral index is well-constrained to be $\beta_{\rm em}=1.8\pm0.1$, in very good agreement with the values reported in the literature (e.g. (cite: Dunne2011a; Galliano2018a); although we note that measurements of this parameter at high redshifts are scarce). This figure also reveals, unsurprisingly, a mild correlation between $\beta_{\rm em}$ and $\Psi_2$ since higher values of $\beta_{\rm em}$ imply lower flux densities at long wavelengths (for a given IR luminosity, redshift, and dust temperature).

We highlight that despite the large range of values explored for the three different parameters and despite the caveats described above, $\alpha_{\rm LF}$ and $\beta_{\rm em}$ are well-constrained, and while the uncertainties on $\Psi_2$ seem large, our constrains rule out values grater than $\Psi_2\sim-4$, which would imply a significantly larger number of DSFGs at high-redshifts.

## The history of dust-obscured star formation

The star formation rate density as a function of redshift can now be calculated by integrating the best-fit infrared galaxy luminosity function[^5] and propagating the associated uncertainties.

An important source of uncertainty is the field-to-field variation due to the large scale structure of the Universe, which is known as cosmic variance. To infer its impact in our estimations, we adopt the results from a model for the dust continuum number counts of galaxies ((cite: Popping2020a)) that builds upon the UniverseMachine model ((cite: Behroozi2019a)), from which 1000 different light cones of 400 sq. arcmin (approximately the combined area the MORA, ASPECS, and the 3 mm archival surveys) are used to measure the variance in the number of detected sources. The cosmic variance is then defined following (cite: Moster2011a): $$\begin{equation}
\sigma^2 \equiv \frac{\langle N^2\rangle - \langle N\rangle^2}{\langle N\rangle^2} - \frac{1}{\langle N\rangle},
\end{equation}$$ where $\langle N^2\rangle$ and $\langle N\rangle$ are the variance and mean number of sources in the light cones. At the most critical redshifts of our work ($z>3$), the cosmic variance is estimated to be $\approx35\%$. At $z\approx7.0$, the cosmic variance increases significantly and our data-sets suffer a loss of constraining power. Furthermore, an increasing fraction of the star formation activity is expected to be in highly clustered structures (i.e. galaxy proto-clusters; (cite: Chiang2017a)) that might have been missed in our surveys. Therefore, the model predictions presented in this work are limited to $z\lesssim7.0$.

The inferred dust-obscured star-formation history and its associated uncertainty, including that from cosmic variance, is presented in Figure [7](#fig:sfrd). As can be seen, it is dominated by galaxies with $L_{\rm IR}\approx10^{11}-10^{13}$, a population that our surveys are particularly sensitive to (see Figure [10](#fig:lum_limits) in Appendix [7](#appendix2)). Figure [7](#fig:sfrd) also includes other determinations of the CSFRD from the literature, which are split in two groups: FIR/sub-mm and UV/optical-based measurements. The first set includes the works by (cite: Magnelli2011a; Gruppioni2013a; Magnelli2013a; Casey2012b; Swinbank2014a; Bourne2017a; Koprowski2017a; Liu2018a; Williams2019a; Magnelli2019a; Wang2019b; Lim2020a; Dudzeviciute2020a), and the second set the results reported in (cite: Wyder2005a; Schiminovich2005a; Robotham2011a; Cucciati2012a; Dahlen2007a; Reddy2009a; Bouwens2012a; Schenker2013a; Finkelstein2015a). We remind the reader that our model is not a fit to those data points but are shown as a mean for comparison.

![](sfrd_breakdown_luminosities_v2.eps)

The dust-obscured component traced by the FIR-to-mm surveys has dominated the cosmic history of star formation for the past $\sim12\,$billion years, with a peak era between $z=2-2.5$ ($\sim10-11\,$Gyr ago) and contributing around $\sim80\%$ of total SFRD (see middle panel in Figure [7](#fig:sfrd)). Beyond this peak redshift, the dust-obscured star formation rapidly decreases, following the strong evolution of the number density of the IR luminosity function (see §[4.3](#secc:lum_func)), with values that are comparable to the unobscured star formation traced by the rest-frame UV/optical surveys at $z\sim4$.

At higher redshifts, the dust re-processed star formation rate density becomes less dominant than the unobscured star formation. This is because of the combination of the flat faint-end slope of the IR luminosity function and the steep redshift evolution of its number density as compared to the UV luminosity function. At $z=5$, the dust-obscured star formation represents $35\%^{+10\%}_{-25\%}$ of the total SFRD and decreases to $25\%^{+15\%}_{-20\%}$ at $z=6$. Given that massive, IR bright galaxies dominate the obscured component (as shown in the top panel of Figure [7](#fig:sfrd)), the observed decline of the dust-obscured star formation likely reflects the dearth of massive galaxies at high redshifts.

### Comparison to other measurements and model predictions

The SFRD described above is in line with previous results from (sub-)mm surveys, although most of them were limited to $z\lesssim4-5$. For example, (cite: Dunlop2017a) reported a transition from unobscured-dominated star formation to obscured-dominated at $z\approx4$, in very good agreement with our results. Nevertheless, the small area of their survey ($\sim4.5\,$sq. arcmin) prevented them from deriving conclusions beyond this redshift. The results from the larger ALMA surveys presented by (cite: Hatsukade2018a) and (cite: Franco2018a), covering $26\rm\,arcmin^2$ and $69\rm\,arcmin^2$, respectively, also indicate a minor contribution from DSFGs in the $z\approx4-5$ range (see also (cite: Yamaguchi2019a)). More recently, (cite: Dudzeviciute2020a) used ALMA observations to investigate the properties of $\sim700$ DSFGs detected over $\sim1\,\rm deg^2$, and inferred a SFRD in the range of $\rho_{obs}\approx3\times10^{-3}$ at $z\approx4-5$ for galaxies with $S_{850\mu m}>1\,\rm mJy$ (see also (cite: Koprowski2017a)), in very good agreement with our results (particularly if we look at the contribution from $L_{\rm IR}>10^{12}\,L_\odot$ galaxies; see Figure [8](#fig:sfrd_models)).

The ‘wedding cake’ structure of all these surveys ensure that the contributions from the more abundant faint galaxies and the rare bright sources are accounted for (with the possible exception of the most extreme galaxies with ${\rm log}(L_{\rm IR}/L_\odot)\gtrsim13.5$; see Figure [10](#fig:lum_limits)), suggesting that we are not missing any significant population of galaxies. This is also supported by the fact that the number counts predicted by the model are in good agreement with the deepest ALMA observations achieved to-date and with the large-area single-dish telescope surveys (see Figures [5](#fig:num_counts) and [9](#fig:num_counts_short_waves)).

Other studies based on stacking analysis on (sub-)mm maps and using samples of UV/optically-selected galaxies have also concluded that the fraction of star formation that is obscured by dust decreases at high redshifts (e.g. (cite: Capak2015a; Bouwens2016a; Fudamoto2020a)). Indeed, (cite: Bouwens2020a) complemented previous results from the literature with their dust-corrected SFRs to estimate the obscured and unobscured components of the cosmic history of star formation, and found that the CSFRD transitions from being primarily unobscured to obscured at $z\sim5$, in relatively good agreement with our estimations[^6] from direct mm-selected samples.

Our results are also compatible with estimations from other tracers such as radio observations. For example, using the VLA-COSMOS 3 GHz radio survey, (cite: Novak2017a) inferred lower limits for the SFRD up to $z\sim5$ by integrating the radio luminosity function after converting the radio luminosities to SFRs. These VLA-COSMOS 3 GHz radio constraints are consistent with our measurements. The authors also provided a completeness-corrected estimation of this quantity by extrapolating the luminosity function to account for the faintest star-forming galaxies. Their estimates show good consistency with our total SFRD, with the possible exception of their last bin at $z\sim5$. Nevertheless, the large extrapolations involved in this process plus the systematic uncertainties that go into calculating SFRD from radio data introduce very large uncertainties in these measurements. The most recent estimates of SFRD from the VLA-COSMOS 3 GHz survey presented by (cite: Leslie2020a) are in better agreement with our results.

There are, however, a few other studies that have proposed a different picture, with the obscured component significantly dominating the CSFRD back to $z\sim5$. (cite: Rowan-Robinson2016a) estimated the obscured star formation rate density using a sample of *Herschel*-selected galaxies over $\sim20\,\rm deg^2$, finding values far higher than the UV estimations. Their constraints, however, cannot rule out the possibility that the UV-based measurements are dominant given the large uncertainties on their estimations, as mentioned by the authors. Additionally, it is possible that their calculations might be contaminated by the effect of gravitationally lensing or by overestimated *Herschel* flux densities (in view of their extreme SFRs which extend to $20,000\,M_\odot\,\rm yr^{-1}$).

More recently, (cite: Gruppioni2020a) derive the dust-obscured SFRD using the serendipitously detected sources in the ALPINE survey, finding values in excess to those derived from UV/optical surveys even at $z\sim5$. While the use of highly-confused *Herschel* observations might also overestimate the derived luminosities and SFRs, we think that the discrepancy is mainly due because of the possible clustering of serendipitous detections around the original targets. The clustering is expected since the observations’ original targets are massive galaxies (log($M/M_\star$)$\gtrsim10.5$) at $z\approx4-6$. In this case, their measurements would be more representative of an over-dense region in the large-scale structure of the Universe. We note, however, that a significant fraction of their estimates comes from the extrapolation of the IR luminosity function since the reported total SFRD is a factor of $\sim5$ greater than the SFRD estimated when using only the detected sources. Therefore, it is also possible that the assumptions on the extrapolation of the IRLF are responsible for part of the observed discrepancy.

In Figure [8](#fig:sfrd_models) we compare the SFRD derived in this work with results from galaxy evolution models, including the predictions from the cosmological hydrodynamical IllustrisTNG simulations ((cite: Pillepich2018a)), the shark semi-analytic model ((cite: Lagos2018a)), and the results from the SIDES simulations ((cite: Bethermin2017a)). Generally speaking, and taking into account the associated uncertainties in these values, our results are in good agreement with the aforementioned studies, pointing towards a convergence between galaxy evolution models and observations.

Finally, we include the density evolution of luminous ($M_{1450}<-26$) quasars ((cite: Wang2019c)) in Figure [8](#fig:sfrd_models) (scaled for visualization). The shape of the space density of bright quasar strongly resemble that from the bright DSFGs with $L_{\rm IR}>10^{12}\,L_\odot$ (shaded orange region in the figure), suggesting a connection between these two populations and, therefore, between the onset of star formation and the growth of their massive black holes (e.g. (cite: Wall2005a)).

![](sfrd_with_theoretical_predictions.eps)

# Discussion and Conclusions

Exploiting the far-infrared and sub-millimeter data aggregated over the last two decades, and particularly, the state-of-the-art ALMA blind surveys at 1.2 mm, 2 mm, and 3 mm, we have constrained the evolution of the IR luminosity function and dust-obscured star formation in the last 13 billion years, back to $z\sim7$. This is achieved by combining a model of the dusty star-forming galaxy population with those long-wavelength observations, inferring constraints on the prevalence and characteristics of these galaxies through measurements of galaxy number counts at different wavelengths.

By using a library of SEDs an assuming different evolutionary scenarios for the IR luminosity function, the model makes predictions for galaxy (sub-)millimeter surveys and then works backward to discriminate between the different luminosity function scenarios through the galaxy number counts. Finally, the dust-obscured star formation rate density is estimated by integrating the IR luminosity function (see also (cite: Casey2018b; Casey2018a; Zavala2018c)).

The model’s constraints used in this work include our 2 mm galaxy number counts derived as part of the 2 2 mm MORA survey, the largest ALMA survey to-date sensitive to detect DSFGs and dust-obscured star formation up to the epoch of reionization and the only one carried out at a 2 mm wavelength (see also Casey et al. in preparation). Additionally, we use the 3 mm number counts reported in §[3](#secc:3mm_num_counts), which are based on our ALMA follow-up observations on the sample of 3 mm-selected galaxies reported by (cite: Zavala2018c). Finally, we also include the number counts from the ASPECS survey ((cite: Gonzalez-Lopez2019a; Gonzalez-Lopez2020a)), a deep ALMA large program at 1.2 mm and 3 mm. Altogether, these surveys add a total of $\sim400\,$sq. arcmin. of deep observations with arcsecond-resolution, representing the state-of-the-art blind ALMA surveys to-date.

All these data provide good constraints on the model parameters, and thus, on the IR luminosity function and its evolution with redshift. Based on our best-fit model, which simultaneously reproduces the far-infrared and sub-millimeter data from single-dish telescopes and interferometric surveys, we constrained the faint-end slope of the infrared luminosity function to be flat, with a value of $\alpha_{\rm LF}=-0.42^{+0.02}_{-0.04}$ (see also (cite: Koprowski2017a; Lim2020a)). This implies that deep pencil-beam observations at (sub-)mm wavelengths would not significantly increase the number of detected sources, in line with previous results from the literature (e.g. (cite: Popping2020a)). The characteristic number density of the luminosity function, $\Phi_\star$, decreases as $\Phi_\star\propto(1+z)^{-6.5^{+0.8}_{-1.8}}$ at $z\gtrsim2$, in a similar fashion as the quasar luminosity function and the density evolution of UV-bright galaxies ((cite: Hopkins2007a; Finkelstein2015a)), which might suggest that these galaxies occupy similar dark matter halos.

Our constraints on the dust-obscured star formation indicate that the cosmic history of star formation had a peak at $z\approx2-2.5$, and has been dominated by the dust-obscured component during the last 12 billion years, back to $z\sim4$, when the unobscured and obscured contributions were comparable. Beyond this epoch, the dust re-processed star formation rate density was less dominant than the visible star formation, contributing around $35\%^{+10\%}_{-25\%}$ at $z=5$ and $25\%^{+15\%}_{-20\%}$ at $z=6$. This suggests that the bulk ($\gtrsim80\%$) of the star formation activity in the first billion years of the Universe was not dust enshrouded. Given the massive nature of DSFGs, this drop-off of the obscured component is in line with the decreasing number of high-mass galaxies with increasing redshift (see also (cite: Dunlop2017a; Bouwens2020a)).\
Our picture of the history of the cosmic star formation is consistent with previous results from long-wavelength (FIR-to-mm) surveys (e.g. (cite: Dunlop2017a; Bourne2017a; Hatsukade2018a; Dudzeviciute2020a)), although most of those were limited to $z\lesssim4$. Hence, our results represent a significant progress on our understanding of the prevalence of DSFGs during the first 1.5 billion years of the Universe, and complement the significant efforts carried out using UV/optically selected galaxies (e.g. (cite: Bouwens2020a)). The inferred SFRD is also in broad agreement with the most recent predictions from galaxy evolution models (like IllustrisTNG and shark; (cite: Pillepich2018a; Lagos2020)), which point towards a convergence between models and observations.

With estimations for both the obscured and unobscured components, the shape of the cosmic history of star formation is now constrained out to the end of the epoch of reionization. This measurement, which preserves the galaxy mass assembly history of the Universe, provides a benchmark against which to compare galaxy formation models and simulations, and a step forward in our understanding of the dust and metal enrichment of the early Universe.

# Acknowledgments

We thank the anonymous referee for a careful review of our manuscript and his/her valuable suggestions.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. The Dunlap Institute is funded through an endowment established by the David Dunlap family and the University of Toronto. JAZ and CMC acknowledge thank the University of Texas at Austin College of Natural Sciences for support. CMC also thanks the National Science Foundation for support through grants AST-1714528 and AST-1814034 and support from the Research Corporation for Science Advancement from a 2019 Cottrell Scholar Award sponsored by IF/THEN, an initiative of Lyda Hill Philanthropies. M.A. has been supported by the grant “CONICYT + PCI + INSTITUTO MAX PLANCK DE ASTRONOMIA MPG190030” and “CONICYT+PCI+REDES 190194”. KIC acknowledges funding from the European Research Council through the award of the Consolidator Grant ID 681627-BUILDUP. JH acknowledges support of the VIDI research programme with project number 639.042.611, which is (partly) financed by the Netherlands Organisation for Scientific Research (NWO). KK acknowledges support from the Knut and Alice Wallenberg Foundation. GEM acknowledges the Villum Fonden research grant 13160 “Gas to stars, stars to dust: tracing star formation across cosmic time” and the Cosmic Dawn Center of Excellence funded by the Danish National Research Foundation under then grant No. 140. E.T. acknowledges support from FONDECYT Regular 1190818, CONICYT PIA ACT172033 and Basal-CATA AFB170002 grants.

Finally, our deepest gratitude to all the people who continue to provide essential services during the COVID-19 pandemic.\
**Data and materials availability:** This paper makes use of the following ALMA data: ADS/JAO. ALMA#2018.1.00231.S, ADS/JAO.ALMA #2018.1.00478.S, and ADS/JAO.ALMA#22019.1.00838.S, archived at https://almascience.nrao.edu/alma-data/archive.

natexlab

(ref: Aravena2020a) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, arXiv e-prints, arXiv:2006.04284. [`https://arxiv.org/abs/2006.04284`](https://arxiv.org/abs/2006.04284)

(ref: Baugh2005a) Baugh, C. M., Lacey, C. G., Frenk, C. S., et al. 2005, MNRAS, 356, 1191, doi: [`10.1111/j.1365-2966.2004.08553.x`](http://doi.org/10.1111/j.1365-2966.2004.08553.x)

(ref: Beelen2008a) Beelen, A., Omont, A., Bavouzet, N., et al. 2008, A&A, 485, 645, doi: [`10.1051/0004-6361:200809500`](http://doi.org/10.1051/0004-6361:200809500)

(ref: Behroozi2019a) Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C. 2019, MNRAS, 488, 3143, doi: [`10.1093/mnras/stz1182`](http://doi.org/10.1093/mnras/stz1182)

(ref: Bethermin2010a) Béthermin, M., Dole, H., Cousin, M., & Bavouzet, N. 2010, A&A, 516, A43, doi: [`10.1051/0004-6361/200913910`](http://doi.org/10.1051/0004-6361/200913910)

(ref: Bethermin2012a) Béthermin, M., Le Floc’h, E., Ilbert, O., et al. 2012, A&A, 542, A58, doi: [`10.1051/0004-6361/201118698`](http://doi.org/10.1051/0004-6361/201118698)

(ref: Bethermin2015a) Bethermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113, doi: [`10.1051/0004-6361/201425031`](http://doi.org/10.1051/0004-6361/201425031)

(ref: Bethermin2017a) Béthermin, M., Wu, H.-Y., Lagache, G., et al. 2017, A&A, 607, A89, doi: [`10.1051/0004-6361/201730866`](http://doi.org/10.1051/0004-6361/201730866)

(ref: Bourne2017a) Bourne, N., Dunlop, J. S., Merlin, E., et al. 2017, MNRAS, 467, 1360, doi: [`10.1093/mnras/stx031`](http://doi.org/10.1093/mnras/stx031)

(ref: Bouwens2020a) Bouwens, R., Gonzalez-Lopez, J., Aravena, M., et al. 2020, arXiv e-prints, arXiv:2009.10727. [`https://arxiv.org/abs/2009.10727`](https://arxiv.org/abs/2009.10727)

(ref: Bouwens2012a) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2012, ApJL, 752, L5, doi: [`10.1088/2041-8205/752/1/L5`](http://doi.org/10.1088/2041-8205/752/1/L5)

(ref: Bouwens2016a) Bouwens, R. J., Aravena, M., Decarli, R., et al. 2016, ApJ, 833, 72, doi: [`10.3847/1538-4357/833/1/72`](http://doi.org/10.3847/1538-4357/833/1/72)

(ref: Capak2015a) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455, doi: [`10.1038/nature14500`](http://doi.org/10.1038/nature14500)

(ref: Casey2012a) Casey, C. M. 2012, MNRAS, 425, 3094, doi: [`10.1111/j.1365-2966.2012.21455.x`](http://doi.org/10.1111/j.1365-2966.2012.21455.x)

(ref: Casey2018b) Casey, C. M., Hodge, J., Zavala, J. A., et al. 2018a, ApJ, 862, 78, doi: [`10.3847/1538-4357/aacd11`](http://doi.org/10.3847/1538-4357/aacd11)

(ref: Casey2012b) Casey, C. M., Berta, S., Béthermin, M., et al. 2012, ApJ, 761, 140, doi: [`10.1088/0004-637X/761/2/140`](http://doi.org/10.1088/0004-637X/761/2/140)

(ref: Casey2013a) Casey, C. M., Chen, C.-C., Cowie, L. L., et al. 2013, MNRAS, 436, 1919, doi: [`10.1093/mnras/stt1673`](http://doi.org/10.1093/mnras/stt1673)

(ref: Casey2018a) Casey, C. M., Zavala, J. A., Spilker, J., et al. 2018b, ApJ, 862, 77, doi: [`10.3847/1538-4357/aac82d`](http://doi.org/10.3847/1538-4357/aac82d)

(ref: Chabrier2003a) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Chapman2002a) Chapman, S. C., Scott, D., Borys, C., & Fahlman, G. G. 2002, MNRAS, 330, 92, doi: [`10.1046/j.1365-8711.2002.05053.x`](http://doi.org/10.1046/j.1365-8711.2002.05053.x)

(ref: Chen2013a) Chen, C.-C., Cowie, L. L., Barger, A. J., et al. 2013, ApJ, 776, 131, doi: [`10.1088/0004-637X/776/2/131`](http://doi.org/10.1088/0004-637X/776/2/131)

(ref: Chiang2017a) Chiang, Y.-K., Overzier, R. A., Gebhardt, K., & Henriques, B. 2017, ApJL, 844, L23, doi: [`10.3847/2041-8213/aa7e7b`](http://doi.org/10.3847/2041-8213/aa7e7b)

(ref: Clements2010a) Clements, D. L., Rigby, E., Maddox, S., et al. 2010, A&A, 518, L8, doi: [`10.1051/0004-6361/201014581`](http://doi.org/10.1051/0004-6361/201014581)

(ref: Coppin2006a) Coppin, K., Chapin, E. L., Mortier, A. M. J., et al. 2006, MNRAS, 372, 1621, doi: [`10.1111/j.1365-2966.2006.10961.x`](http://doi.org/10.1111/j.1365-2966.2006.10961.x)

(ref: Cucciati2012a) Cucciati, O., Tresse, L., Ilbert, O., et al. 2012, A&A, 539, A31, doi: [`10.1051/0004-6361/201118010`](http://doi.org/10.1051/0004-6361/201118010)

(ref: daCunha2013a) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13, doi: [`10.1088/0004-637X/766/1/13`](http://doi.org/10.1088/0004-637X/766/1/13)

(ref: Dahlen2007a) Dahlen, T., Mobasher, B., Dickinson, M., et al. 2007, ApJ, 654, 172, doi: [`10.1086/508854`](http://doi.org/10.1086/508854)

(ref: Dudzeviciute2020a) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: Dunlop2017a) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861, doi: [`10.1093/mnras/stw3088`](http://doi.org/10.1093/mnras/stw3088)

(ref: Dunne2011a) Dunne, L., Gomez, H. L., da Cunha, E., et al. 2011, MNRAS, 417, 1510, doi: [`10.1111/j.1365-2966.2011.19363.x`](http://doi.org/10.1111/j.1365-2966.2011.19363.x)

(ref: Ferguson2000a) Ferguson, H. C., Dickinson, M., & Williams, R. 2000, ARA&A, 38, 667, doi: [`10.1146/annurev.astro.38.1.667`](http://doi.org/10.1146/annurev.astro.38.1.667)

(ref: Finkelstein2015a) Finkelstein, S. L., Ryan, Russell E., J., Papovich, C., et al. 2015, ApJ, 810, 71, doi: [`10.1088/0004-637X/810/1/71`](http://doi.org/10.1088/0004-637X/810/1/71)

(ref: Franco2018a) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152, doi: [`10.1051/0004-6361/201832928`](http://doi.org/10.1051/0004-6361/201832928)

(ref: Fudamoto2020a) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, arXiv e-prints, arXiv:2004.10760. [`https://arxiv.org/abs/2004.10760`](https://arxiv.org/abs/2004.10760)

(ref: Fujimoto2016a) Fujimoto, S., Ouchi, M., Ono, Y., et al. 2016, ApJS, 222, 1, doi: [`10.3847/0067-0049/222/1/1`](http://doi.org/10.3847/0067-0049/222/1/1)

(ref: Galliano2018a) Galliano, F., Galametz, M., & Jones, A. P. 2018, ARA&A, 56, 673, doi: [`10.1146/annurev-astro-081817-051900`](http://doi.org/10.1146/annurev-astro-081817-051900)

(ref: Geach2013a) Geach, J. E., Chapin, E. L., Coppin, K. E. K., et al. 2013, MNRAS, 432, 53, doi: [`10.1093/mnras/stt352`](http://doi.org/10.1093/mnras/stt352)

(ref: Gehrels1986a) Gehrels, N. 1986, ApJ, 303, 336, doi: [`10.1086/164079`](http://doi.org/10.1086/164079)

(ref: Gonzalez-Lopez2019a) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139, doi: [`10.3847/1538-4357/ab3105`](http://doi.org/10.3847/1538-4357/ab3105)

(ref: Gonzalez-Lopez2020a) González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91, doi: [`10.3847/1538-4357/ab765b`](http://doi.org/10.3847/1538-4357/ab765b)

(ref: Gruppioni2013a) Gruppioni, C., Pozzi, F., Rodighiero, G., et al. 2013, MNRAS, 432, 23, doi: [`10.1093/mnras/stt308`](http://doi.org/10.1093/mnras/stt308)

(ref: Gruppioni2020a) Gruppioni, C., Bethermin, M., Loiacono, F., et al. 2020, arXiv e-prints, arXiv:2006.04974. [`https://arxiv.org/abs/2006.04974`](https://arxiv.org/abs/2006.04974)

(ref: Hatsukade2018a) Hatsukade, B., Kohno, K., Yamaguchi, Y., et al. 2018, PASJ, 70, 105, doi: [`10.1093/pasj/psy104`](http://doi.org/10.1093/pasj/psy104)

(ref: Hayward2013a) Hayward, C. C., Narayanan, D., Kereš, D., et al. 2013, MNRAS, 428, 2529, doi: [`10.1093/mnras/sts222`](http://doi.org/10.1093/mnras/sts222)

(ref: Hopkins2007a) Hopkins, P. F., Richards, G. T., & Hernquist, L. 2007, ApJ, 654, 731, doi: [`10.1086/509629`](http://doi.org/10.1086/509629)

(ref: Hsu2016a) Hsu, L.-Y., Cowie, L. L., Chen, C.-C., Barger, A. J., & Wang, W.-H. 2016, ApJ, 829, 25, doi: [`10.3847/0004-637X/829/1/25`](http://doi.org/10.3847/0004-637X/829/1/25)

(ref: Jin2019a) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887, 144, doi: [`10.3847/1538-4357/ab55d6`](http://doi.org/10.3847/1538-4357/ab55d6)

(ref: Karim2013a) Karim, A., Swinbank, A. M., Hodge, J. A., et al. 2013, MNRAS, 432, 2, doi: [`10.1093/mnras/stt196`](http://doi.org/10.1093/mnras/stt196)

(ref: Knudsen2008a) Knudsen, K. K., van der Werf, P. P., & Kneib, J. P. 2008, MNRAS, 384, 1611, doi: [`10.1111/j.1365-2966.2007.12820.x`](http://doi.org/10.1111/j.1365-2966.2007.12820.x)

(ref: Koprowski2017a) Koprowski, M. P., Dunlop, J. S., Michałowski, M. J., et al. 2017, MNRAS, 471, 4155, doi: [`10.1093/mnras/stx1843`](http://doi.org/10.1093/mnras/stx1843)

(ref: Lagos2020) Lagos, C. d. P., da Cunha, E., Robotham, A. S. G., et al. 2020, arXiv e-prints, arXiv:2007.09853. [`https://arxiv.org/abs/2007.09853`](https://arxiv.org/abs/2007.09853)

(ref: Lagos2018a) Lagos, C. d. P., Tobar, R. J., Robotham, A. S. G., et al. 2018, MNRAS, 481, 3573, doi: [`10.1093/mnras/sty2440`](http://doi.org/10.1093/mnras/sty2440)

(ref: Laporte2017a) Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJL, 837, L21, doi: [`10.3847/2041-8213/aa62aa`](http://doi.org/10.3847/2041-8213/aa62aa)

(ref: Leslie2020a) Leslie, S., Schinnerer, E., Liu, D., et al. 2020, arXiv e-prints, arXiv:2006.13937. [`https://arxiv.org/abs/2006.13937`](https://arxiv.org/abs/2006.13937)

(ref: Lim2020a) Lim, C.-F., Wang, W.-H., Smail, I., et al. 2020, ApJ, 889, 80, doi: [`10.3847/1538-4357/ab607f`](http://doi.org/10.3847/1538-4357/ab607f)

(ref: Liu2018a) Liu, D., Daddi, E., Dickinson, M., et al. 2018, ApJ, 853, 172, doi: [`10.3847/1538-4357/aaa600`](http://doi.org/10.3847/1538-4357/aaa600)

(ref: Loiacono2020a) Loiacono, F., Decarli, R., Gruppioni, C., et al. 2020, arXiv e-prints, arXiv:2006.04837. [`https://arxiv.org/abs/2006.04837`](https://arxiv.org/abs/2006.04837)

(ref: Madau2014a) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Magdis2017a) Magdis, G. E., Rigopoulou, D., Daddi, E., et al. 2017, A&A, 603, A93, doi: [`10.1051/0004-6361/201731037`](http://doi.org/10.1051/0004-6361/201731037)

(ref: Magnelli2011a) Magnelli, B., Elbaz, D., Chary, R. R., et al. 2011, A&A, 528, A35, doi: [`10.1051/0004-6361/200913941`](http://doi.org/10.1051/0004-6361/200913941)

(ref: Magnelli2013a) Magnelli, B., Popesso, P., Berta, S., et al. 2013, A&A, 553, A132, doi: [`10.1051/0004-6361/201321371`](http://doi.org/10.1051/0004-6361/201321371)

(ref: Magnelli2019a) Magnelli, B., Karim, A., Staguhn, J., et al. 2019, ApJ, 877, 45, doi: [`10.3847/1538-4357/ab1912`](http://doi.org/10.3847/1538-4357/ab1912)

(ref: McLure2013a) McLure, R. J., Dunlop, J. S., Bowler, R. A. A., et al. 2013, MNRAS, 432, 2696, doi: [`10.1093/mnras/stt627`](http://doi.org/10.1093/mnras/stt627)

(ref: Michalowski2017a) Michałowski, M. J., Dunlop, J. S., Koprowski, M. P., et al. 2017, MNRAS, 469, 492, doi: [`10.1093/mnras/stx861`](http://doi.org/10.1093/mnras/stx861)

(ref: Moster2011a) Moster, B. P., Somerville, R. S., Newman, J. A., & Rix, H.-W. 2011, ApJ, 731, 113, doi: [`10.1088/0004-637X/731/2/113`](http://doi.org/10.1088/0004-637X/731/2/113)

(ref: Nelder1965a) Nelder, J. A., & Mead, R. 1965, Comput. J., 7, 308

(ref: Novak2017a) Novak, M., Smolčić, V., Delhaize, J., et al. 2017, A&A, 602, A5, doi: [`10.1051/0004-6361/201629436`](http://doi.org/10.1051/0004-6361/201629436)

(ref: Oesch2018a) Oesch, P. A., Bouwens, R. J., Illingworth, G. D., Labbé, I., & Stefanon, M. 2018, ApJ, 855, 105, doi: [`10.3847/1538-4357/aab03f`](http://doi.org/10.3847/1538-4357/aab03f)

(ref: Oliver2010a) Oliver, S. J., Wang, L., Smith, A. J., et al. 2010, A&A, 518, L21, doi: [`10.1051/0004-6361/201014697`](http://doi.org/10.1051/0004-6361/201014697)

(ref: Oteo2016a) Oteo, I., Zwaan, M. A., Ivison, R. J., Smail, I., & Biggs, A. D. 2016, ApJ, 822, 36, doi: [`10.3847/0004-637X/822/1/36`](http://doi.org/10.3847/0004-637X/822/1/36)

(ref: Patanchon2009a) Patanchon, G., Ade, P. A. R., Bock, J. J., et al. 2009, ApJ, 707, 1750, doi: [`10.1088/0004-637X/707/2/1750`](http://doi.org/10.1088/0004-637X/707/2/1750)

(ref: Pillepich2018a) Pillepich, A., Springel, V., Nelson, D., et al. 2018, MNRAS, 473, 4077, doi: [`10.1093/mnras/stx2656`](http://doi.org/10.1093/mnras/stx2656)

(ref: Planck2016a) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13, doi: [`10.1051/0004-6361/201525830`](http://doi.org/10.1051/0004-6361/201525830)

(ref: Popping2020a) Popping, G., Walter, F., Behroozi, P., et al. 2020, ApJ, 891, 135, doi: [`10.3847/1538-4357/ab76c0`](http://doi.org/10.3847/1538-4357/ab76c0)

(ref: numerical_recipes) Press, W. H., Teukolsky, S. A., Vetterling, W. T., & Flannery, B. P. 1992, Numerical Recipes in C (2nd Ed.): The Art of Scientific Computing (USA: Cambridge University Press)

(ref: Reddy2009a) Reddy, N. A., & Steidel, C. C. 2009, ApJ, 692, 778, doi: [`10.1088/0004-637X/692/1/778`](http://doi.org/10.1088/0004-637X/692/1/778)

(ref: Remy-Ruyer2013a) Remy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2013, A&A, 557, A95, doi: [`10.1051/0004-6361/201321602`](http://doi.org/10.1051/0004-6361/201321602)

(ref: Robotham2011a) Robotham, A. S. G., & Driver, S. P. 2011, MNRAS, 413, 2570, doi: [`10.1111/j.1365-2966.2011.18327.x`](http://doi.org/10.1111/j.1365-2966.2011.18327.x)

(ref: Rowan-Robinson2016a) Rowan-Robinson, M., Oliver, S., Wang, L., et al. 2016, MNRAS, 461, 1100, doi: [`10.1093/mnras/stw1169`](http://doi.org/10.1093/mnras/stw1169)

(ref: Sanders2003a) Sanders, D. B., Mazzarella, J. M., Kim, D. C., Surace, J. A., & Soifer, B. T. 2003, AJ, 126, 1607, doi: [`10.1086/376841`](http://doi.org/10.1086/376841)

(ref: Schenker2013a) Schenker, M. A., Robertson, B. E., Ellis, R. S., et al. 2013, ApJ, 768, 196, doi: [`10.1088/0004-637X/768/2/196`](http://doi.org/10.1088/0004-637X/768/2/196)

(ref: Schiminovich2005a) Schiminovich, D., Ilbert, O., Arnouts, S., et al. 2005, ApJL, 619, L47, doi: [`10.1086/427077`](http://doi.org/10.1086/427077)

(ref: Schreiber2015a) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74, doi: [`10.1051/0004-6361/201425017`](http://doi.org/10.1051/0004-6361/201425017)

(ref: Scott2012a) Scott, K. S., Wilson, G. W., Aretxaga, I., et al. 2012, MNRAS, 423, 575, doi: [`10.1111/j.1365-2966.2012.20905.x`](http://doi.org/10.1111/j.1365-2966.2012.20905.x)

(ref: Scott2006a) Scott, S. E., Dunlop, J. S., & Serjeant, S. 2006, MNRAS, 370, 1057, doi: [`10.1111/j.1365-2966.2006.10478.x`](http://doi.org/10.1111/j.1365-2966.2006.10478.x)

(ref: Stach2018a) Stach, S. M., Smail, I., Swinbank, A. M., et al. 2018, ApJ, 860, 161, doi: [`10.3847/1538-4357/aac5e5`](http://doi.org/10.3847/1538-4357/aac5e5)

(ref: Staguhn2014a) Staguhn, J. G., Kovács, A., Arendt, R. G., et al. 2014, ApJ, 790, 77, doi: [`10.1088/0004-637X/790/1/77`](http://doi.org/10.1088/0004-637X/790/1/77)

(ref: Sunyaev1970a) Sunyaev, R. A., & Zeldovich, Y. B. 1970, Comments on Astrophysics and Space Physics, 2, 66

(ref: Swinbank2014a) Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267, doi: [`10.1093/mnras/stt2273`](http://doi.org/10.1093/mnras/stt2273)

(ref: Umehata2017a) Umehata, H., Tamura, Y., Kohno, K., et al. 2017, ApJ, 835, 98, doi: [`10.3847/1538-4357/835/1/98`](http://doi.org/10.3847/1538-4357/835/1/98)

(ref: Wall2005a) Wall, J. V., Jackson, C. A., Shaver, P. A., Hook, I. M., & Kellermann, K. I. 2005, A&A, 434, 133, doi: [`10.1051/0004-6361:20041786`](http://doi.org/10.1051/0004-6361:20041786)

(ref: Wang2019c) Wang, F., Yang, J., Fan, X., et al. 2019a, ApJ, 884, 30, doi: [`10.3847/1538-4357/ab2be5`](http://doi.org/10.3847/1538-4357/ab2be5)

(ref: Wang2019b) Wang, L., Pearson, W. J., Cowley, W., et al. 2019b, A&A, 624, A98, doi: [`10.1051/0004-6361/201834093`](http://doi.org/10.1051/0004-6361/201834093)

(ref: Wang2017a) Wang, W.-H., Lin, W.-C., Lim, C.-F., et al. 2017, ApJ, 850, 37, doi: [`10.3847/1538-4357/aa911b`](http://doi.org/10.3847/1538-4357/aa911b)

(ref: Watson2015a) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327, doi: [`10.1038/nature14164`](http://doi.org/10.1038/nature14164)

(ref: Webb2003a) Webb, T. M., Eales, S. A., Lilly, S. J., et al. 2003, ApJ, 587, 41, doi: [`10.1086/368109`](http://doi.org/10.1086/368109)

(ref: Weiss2009a) Weiß, A., Kovács, A., Coppin, K., et al. 2009, ApJ, 707, 1201, doi: [`10.1088/0004-637X/707/2/1201`](http://doi.org/10.1088/0004-637X/707/2/1201)

(ref: Williams2019a) Williams, C. C., Labbe, I., Spilker, J., et al. 2019, ApJ, 884, 154, doi: [`10.3847/1538-4357/ab44aa`](http://doi.org/10.3847/1538-4357/ab44aa)

(ref: Wilner1997a) Wilner, D. J., & Wright, M. C. H. 1997, ApJL, 488, L67, doi: [`10.1086/310924`](http://doi.org/10.1086/310924)

(ref: Wyder2005a) Wyder, T. K., Treyer, M. A., Milliard, B., et al. 2005, ApJL, 619, L15, doi: [`10.1086/424735`](http://doi.org/10.1086/424735)

(ref: Yamaguchi2019a) Yamaguchi, Y., Kohno, K., Hatsukade, B., et al. 2019, ApJ, 878, 73, doi: [`10.3847/1538-4357/ab0d22`](http://doi.org/10.3847/1538-4357/ab0d22)

(ref: Zavala2018c) Zavala, J. A., Casey, C. M., da Cunha, E., et al. 2018, ApJ, 869, 71, doi: [`10.3847/1538-4357/aaecd2`](http://doi.org/10.3847/1538-4357/aaecd2)

(ref: Zavala2017a) Zavala, J. A., Aretxaga, I., Geach, J. E., et al. 2017, MNRAS, 464, 3369, doi: [`10.1093/mnras/stw2630`](http://doi.org/10.1093/mnras/stw2630)

# Number counts model predictions at shorter wavelengths

As discussed in (cite: Casey2018b; Casey2018a), the number counts at $\lambda\lesssim850\,\rm\mu m$ only inform about the evolution of the IRLF at $z\lesssim3.0$, where the model parameters are already relatively well understood. Given that our primary goal is to constrain the IRLF at earlier epochs, only the number counts at 1.2, 2 and 3 mm were used in our analysis. Additionally, incorporating all the available number counts in the fitting procedure, particularly those from single-dish telescope surveys, would increase the computational cost significantly since the simulated area would increase by two order of magnitudes. This would make our fitting analysis prohibitive.

Nevertheless, as mentioned in the main text, our best-fit model nicely reproduces the number counts at shorter wavelengths, from $\lambda=70\,\mu\rm m$ to $850\,\mu\rm m$, covering a large dynamic range of flux density. In Figure [9](#fig:num_counts_short_waves), three different examples are shown; the number counts at $250\,\mu\rm m$, $450\,\mu\rm m/500\,\mu\rm m$, and $850\,\mu\rm m$. The remaining number counts can be found in (cite: Casey2018a). Since most of the galaxies detected at these short wavelengths are relatively bright galaxies at $z\lesssim3$, the best-fit parameters studied in this work (which govern the faint and high-redshift population) do not significantly change the model predictions at those wavelengths compared to (cite: Casey2018a).

![](best_fit_number_counts_shorter_waves.eps)

# Luminosity limits of the adopted surveys

![](lum_limits.eps)

[^1]: Given the inhomogeneous observations in the archival data, a low signal-to-noise ratio does not necessary imply a low flux density since each map has a different noise r.m.s. depth. The two brightest false detections were indeed detected in areas with large r.m.s values.

[^2]: We refer the reader to equations 8 and 9 from (cite: Casey2018a) for the exact parametrization of the evolution of $L_\star$ and $\Phi_\star$ and the role of $L_0$ and $\Phi_0$.

[^3]: From all the sources used in this work, we found a non-negligible contamination from synchrotron emission only in one source, namely MORA-10. This source has been removed from our analysis (see §[2.1](#secc:num_counts)).

[^4]: The results from AzTEC observations and other ALMA surveys at 1.1 mm were scaled by a factor of 0.8 while those from the ALMA/SCUBA-2 survey at $850\,\rm\mu m$ were scaled by a factor of 0.4.

[^5]: The IR luminosity function is integrated over the interval log$(L/L_\odot):[9,13.8]$. A change of these limits has a minor impact on our results since the majority of the contribution arise from galaxies with luminosities in the range of $L_{\rm IR}=10^{11}-10^{13}\,L_\odot$ (see Figure [7](#fig:sfrd)).

[^6]: Note, however, that in (cite: Bouwens2020a) most of the dust-obscured star formation at $z>4$ is produced by faint (UV-selected) galaxies with $L_{\rm IR}<10^{12}\,L_\odot$. Nevertheless, those estimations were done assuming SED templates whose dust temperatures increase with redshift. If there is no significant evolution on the dust temperature (e.g. (cite: Dudzeviciute2020a)) then the SFRs derived for these galaxies would be lower by a factor of $\sim2.5$, as discussed by the authors. This would decrease the contribution of faint galaxies and bring our results into better agreement.

</paper>

Write the methods card for this paper.