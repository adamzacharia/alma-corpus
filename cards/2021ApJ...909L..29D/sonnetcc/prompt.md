# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...909L..29D\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...909L..29D",
 "title": "A CO Survey of SpARCS Star-forming Brightest Cluster Galaxies: Evidence for Uniformity in BCG Molecular Gas Processing across Cosmic Time",
 "year": 2021,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Dunne, Delaney A.",
 "n_authors": 8,
 "arxiv_id": "2103.02463",
 "doi": "10.3847/2041-8213/abeb6f",
 "alma_projects_linked_by_archive": [
  "2019.1.01529.S"
 ]
}
```

Paper text:
<paper>
# A CO Survey of SpARCS Star-Forming Brightest Cluster Galaxies: Evidence for Uniformity in BCG Molecular Gas Processing Across Cosmic Time

## Abstract

We present ALMA CO (2-1) detections of 24 star-forming Brightest Cluster Galaxies (BCGs) over $0.2<z<1.2$, constituting the largest and most distant sample of molecular gas measurements in BCGs to date. The BCGs are selected from the *Spitzer* Adaptation of the Red-Sequence Cluster Survey (SpARCS) to be IR-bright and therefore star-forming. We find that molecular gas is common in star-forming BCGs, detecting CO at a detection rate of 80% in our target sample of 30 objects. We additionally provide measurements of the star formation rate (SFR) and stellar mass, calculated from existing MIPS 24 $\mu$m and IRAC 3.6 $\mu$m fluxes, respectively. We find these galaxies have molecular gas masses of $0.7-11.0\times 10^{10}\ \mathrm{M}_\odot$, comparable to other BCGs in this redshift range, and specific star formation rates which trace the (cite: elbaz2011_ssfrMS) Main Sequence. We compare our BCGs to those of the lower-redshift, cooling-flow BCG sample assembled by (cite: edge2001detection) and find that at z $\lesssim 0.6$ the two samples show very similar correlations between their gas masses and specific SFRs. We suggest that, in this redshift regime, the $\sim10\%$ (cite: webb2015_SpARCS) of BCGs that are star-forming process any accreted molecular gas into stars through means that are agnostic to both their redshift and their cluster mass.

# Introduction

Galaxy clusters are extreme examples of hierarchical structure formation, forming the largest overdensities in the primordial universe. Brightest Cluster Galaxies (BCGs), as massive galaxies residing in the dense, violent centers of galaxy clusters, evolve through pathways that are a direct result of this environment.

In the latter stage of their evolution (after $\mathrm{z}\sim1$), the stellar mass of BCGs roughly doubles ((cite: lidman2012evidence)). While this is expected to be mostly a dry process, done primarily through gasless mergers of the BCG with infalling cluster galaxies ((cite: delucia_20017_SAMs)), some ($\sim$10%, based on a 24 $\mu$m flux $\geq$ 100$\mu$Jy; (cite: webb2015_SpARCS)) BCGs do show star formation at these redshifts. The mechanism driving this star formation is not clear. Possible scenarios include mergers, either major or minor, of the BCG with gas-rich infalling cluster galaxies, or large-scale ‘cooling flows’ of gas from the intracluster medium (ICM) onto the BCG.

Galaxy clusters themselves are not a homogeneous population, complicating the search for a star formation mechanism in their centers. Early X-ray observations revealed that some cluster cores contain an ICM dense enough to cool hydrostatically on timescales much shorter than the Hubble time (e.g. (cite: fabian1977subsonic)). As the ICM cools and compresses, hot gas from outer regions of the cluster flows in to replace it, causing a cooling flow. Located at the center of the cluster, the BCG is often the recipient of gas from the cooling flow. Indeed, some star-forming BCGs seem to have star formation attributable to cooling flows. Examples include the Phoenix cluster at z $=0.596$ ((cite: mcdonald2012_phoenixSFR); (cite: Russell_2017_phoenix)) and SpARCS104922.6+564032.5 (SpARCS1049; (cite: Webb_2017_1049); (cite: hlavaceklarrondo2020_1049CC)) at z $=1.709$.

![](sSFR_MS.png)

A key tool in deciphering star formation processes is cool molecular Hydrogen (H$_2$) gas, which acts as the fuel for future star formation in galaxies, and is commonly traced by the rotational transitions of CO (cite: solomon2005molecular). However, few studies have systematically measured the molecular gas content in BCGs over a range of redshifts. We aim to constrain the processes driving BCG mass growth by studying molecular gas in a large sample of BCGs spanning 6 Gyr of cosmic time.

In this paper, we present new ALMA measurements of the CO (2-1) transition in 30 BCGs, selected from the SpARCS survey (described in §[2.1](#ssec:parentSpARCS)). Our sample is large, containing 24 CO detections, and extends to much higher redshifts (z $\sim1.2$) than any previous statistical BCG survey. We introduce the SpARCS cluster sample, our ALMA observations, and our data reduction method in §[2](#sec:observations). In §[3](#sec:results), we contextualize our BCGs’ molecular gas with other field and cluster measurements. §[4](#sec:discussion) discusses the implications of these observations for BCG mass growth, and we present our conclusions in §[5](#sec:conclusion). We use standard cosmology ($\mathrm{H}_0 = 70$ km/s/Mpc; $\Omega_\mathrm{matter}=0.3$; $\Omega_\Lambda = 0.7$) throughout.

# Observations and Data Reduction

## The Parent SpARCS Sample

The BCGs studied here are drawn from clusters in the Spitzer Adaptation of the Red Sequence Cluster Survey (SpARCS; (cite: muzzin2009spectroscopic); (cite: wilson2009spectroscopic); (cite: demarco2010spectroscopic); (cite: muzzin2012gemini)). SpARCS employs the same technique as the Red Sequence Cluster Survey ((cite: gladders2005red)): it identifies regions of over-densities in Red Sequence (RS) galaxies by dual-filter imaging spanning the 4000Å-break. To do this SpARCS obtained wide-field $z^\prime$ imaging over the *Spitzer*-SWIRE Legacy Survey fields which, in combination with *Spitzer*-IRAC Channel 1 (3.6 $\mu$m) imaging, brackets the break above $z \raisebox{-0.13cm}{~\shortstack{$>$ \\[-0.07cm]$\sim$}}~1$. This simultaneously provides a reliable redshift estimate ($\delta z = (z_\mathrm{spec} - z_\mathrm{RS})/(1-z_\mathrm{spec})$ = 0.075, from $\sim$600 spectroscopic redshifts) through a fit to the location of the Red Sequence in color space. Note that though designed to be sensitive to $z> 1$ clusters, the SpARCS catalog additionally contains many clusters at $z < 1$. Brightest Cluster Galaxies were identified at 3.6 $\mu$m, by taking the brightest galaxy within $z - 3.6 \ \mu\mathrm{m}\pm0.5$ of the Red Sequence of the Cluster, and within 500 kpc of the centroid of the Red Sequence over-density.

## Target Selection

We select as ALMA targets BCGs which a) lie in the southern/equatorial SWIRE fields ELAIS-S1 (ES1), CDFS, and XMM-LSS (XMM), b) have a confirmed spectroscopic redshift from OzDES (the Australian Dark Energy Survey), taken using the AAOmega spectrograph and 2dF fibre positioner on the 4m Anglo-Australian Telescope (cite: lidman2020_newozdes), c) are IR-luminous ($>100\ \mu$Jy at $24 \ \mu$m) and therefore star-forming, d) come from SpARCS clusters with richness N$_\mathrm{gal} >$ 12[^1], or roughly M$_{200} > 1\times 10^{14}$M$_\odot$ ((cite: wen2010erratum); (cite: wen2012catalog); (cite: capozzi2012kcorr); (cite: andreon2014_ngalmass)), and e) have CO (2-1) lines which fall into an ALMA frequency band. These leaves us with a sample of 33 BCGs.

## Observations

Our observations were performed on the Atacama Large Millimeter Array (ALMA; Program ID 2019.1.01529.S, P.I. Webb) between November 22 and December 15, 2019. 30 BCGs were observed over a total of $\sim15$ hours. Three BCGs were not observed because of the ALMA COVID-19 shutdown. We used ALMA bands 3, 4, and 5 (chosen to measure the CO (2-1) line) and configurations C43-1, C43-2, and C43-3. Data were calibrated using ALMA reduction pipeline scripts in CASA version 5.4.0. The nominal flux density calibration uncertainty for ALMA sources in these bands is $\sim 5 - 10\%$ (cite: remijan2019alma). We cleaned the image cubes minimally with natural weighting and pixel sizes between 0.2$''$ and 0.4$''$, resulting in continuum-subtracted and primary beam-corrected images with 46$''$ $\ $to 90$''$ $\ $fields of view. We detected mostly unresolved CO emission at $\geq 3\sigma$ in 24 of 30 pointings, or at a detection rate of 80%. We chose the spectral resolution of each image cube individually, based on the strength of the detection. We show examples of 3 BCGs from our sample, spanning the observed redshift range and the observed S/N range, in Figure [2](#fig:postagestamps). A single BCG (CDFS-CO3) was additionally detected in radio continuum.

These observations were designed to be complete to a constant gas mass depth of $\mathrm{M}_\mathrm{gas} \ $$\geq 10^{10}$ M$_\odot$ at all redshifts. However, due to ALMA’s minimum on-source integration time for a single science goal, many of the lower-redshift objects (z $\lesssim$ 0.6) were observed for longer than necessary to achieve this molecular gas mass limit, resulting in 3$\sigma$ image RMS depths between 1.2 mJy/beam (z $\sim 0.2$) and 0.6 mJy/beam (z $\sim 1.2$) over 100 km/s channels. The sensitivity to low gas masses thus increases at lower redshifts (see Figure [3](#fig:mgas_vs_redshift)).

![](sample_postagestamps.png)

## CO (2-1) Molecular Gas Measurements

We determine galaxy gas masses in a three-step process. Firstly, we generate first-pass spectral profiles by placing an elliptical aperture with semi-major and semi-minor axes twice as large as those of the synthesized beam, and at the same orientation, at the center of each BCG. Spectra are fit with a single one-dimensional Gaussian profile. Secondly, we generate an integrated-intensity ‘Moment-0’ map by collapsing the image cube over the velocity channels with significant emission as determined by this Gaussian fit to the spectral profile. We keep channels within 2$\sigma$ (2 standard deviations) of the mean. We then fit potential signal in the Moment-0 map to a two-dimensional, elliptical Gaussian profile. Finally, we create a second one-dimensional spectral profile, extracted from an elliptical aperture with the parameters of the two-dimensional fitted profile; the new axis sizes are now three times the Gaussian full width at half maximum (FWHM).

We determine the mass of gas present in each galaxy by fitting the second-pass spectral profile to either single- or double-peaked Gaussians, depending on which gives the better fit according to its reduced $\chi^2$ statistic. We take the area under this fit as the total line flux, and we convert this flux to a CO luminosity using (cite: solomon2005molecular) Equation 3. We use galactic CO-to-$\mathrm{H}_2$ conversion factors ($\alpha_{CO}=4.36\ M_\odot (\mathrm{K}\ \mathrm{km}\ \mathrm{s}^{-1}\mathrm{pc}^2)^{-1}$, $r_{21}=0.8$), as these are typical of galaxies on the star-forming Main Sequence (ex. (cite: solomon1997molecular); (cite: freundlich2019phibss2)) and allow easy comparison with existing $\mathrm{H}_2$ masses in BCGs, such as those of (cite: edge2001detection) and (cite: castignani2020molecular). We note, however, that using different CO-to-$\mathrm{H}_2$ conversion factors (for example, $\alpha_\mathrm{CO} = 0.9$ and $\mathrm{r}_{21}=0.85$, typical of ultraluminous infrared galaxies; (cite: bolatto2013co)) does not affect the results of this paper.

We treat the RMS noise in line-free channels ($\sim 7\sigma$ from the mean) of the spectral profile as the uncertainty in each flux value, and account for it while performing the least-squares Gaussian fits. We also search for CO emission in our 6 non-detections by stacking their spectra, centering each around the expected position of the CO line using the OzDES redshifts. The stack shows no significant emission, down to 3$\sigma$.

We determine gas mass limits on the 6 non-detections by collapsing the image cubes over a bandwidth equivalent to the average FWHM of the detected CO peaks ($356\ \mathrm{km}\ \mathrm{s}^{-1}$) and taking the $3\sigma$ RMS value as an upper limit to the flux.

## Stellar Masses and Star Formation Rates

We calculate the stellar mass of each galaxy using existing IRAC $3.6 \ \mu m$ photometry from SWIRE (cite: lonsdale2003swire) to determine the rest-frame *K*-band luminosity. We use an SED template from (cite: bruzual2003stellar) to calculate the *K*-correction, adopting an 11 Gyr simple stellar population with solar metallicity and a Salpeter Initial Mass Function (IMF; (cite: salpeter_1955)). We note that adopting a template with a younger stellar population changes the average stellar mass values by at most 8%. This is within uncertainty and does not affect our results significantly, as they are primarily comparative. We determine a mass-to-light ratio of 0.83 by comparing our sample of $3.6\ \mu m$-based values to more accurate values from a *griz*/3.6$\mu$m/4.5$\mu$m ((cite: Abbott_2018_DES); (cite: lonsdale2003swire)) SED fit using FAST (cite: kriek2018FAST). We take the scatter in this relation (0.3 dex) as the uncertainty in the stellar masses.

We also calculate star formation rates (SFRs) from SWIRE-MIPS $24 \ \mu m$ flux values ((cite: lonsdale2003swire)), using (cite: kennicutt1998_SFR) Equation 4 based on the luminosity at $24\  \ensuremath{\mu}m$ ($L(24)$) from (cite: chary2001interpreting). We note that this method is known to overestimate SFRs, particularly at high redshifts, but this generally occurs above the redshifts covered by our sample, at z $\sim 1.5$ (cite: elbaz2011_ssfrMS). We achieve similar results with more modern SFR methods such as that of (cite: Rieke_2009). We take the scatter of 0.15 dex described in (cite: kennicutt1998_SFR) to be the uncertainty in the SFRs. Because of SWIRE’s 100 $\mu$Jy MIPS limit, our sample is not complete in SFR — we can detect galaxies significantly ($\sim 1 \sigma$) below the (cite: elbaz2011_ssfrMS) MS only to z $\sim$ 0.6, and only starbursting galaxies above z $\sim$ 1.

We present the properties of our BCG sample, including M$_*$ and SFR values, in Table [\[tab:results\]](#tab:results).

![](Mgas_v_z.png)

## A Low-Redshift BCG Comparison Sample

(cite: edge2001detection) introduces a sample of 34 BCGs at redshifts $\leq$ 0.45 in clusters selected from ROSAT to have cooling flows. Of these, 16 galaxies are detected in CO, through a combination of CO(3-2) measurements made using the A3i reciever on JCMT, and CO(1-0) measurements made using the IRAM 30m telescope. Additionally, 12 BCGs have available $3.6 \ \mu\mathrm{m}$ and $24\ \mu\mathrm{m}$ flux measurements. As the largest available sample of well-studied BCGs at low redshifts ($\mathrm{z}_\mathrm{mean} = 0.12 \pm 0.09$), belonging to clusters with known dynamical states, this is a convenient sample with which to compare our BCG detections.

We take the molecular gas masses from (cite: edge2001detection), correcting the values for $H_0 = 70\ \mathrm{km} \ \mathrm{s}^{-1} \ \mathrm{Mpc}^{-1}$. Stellar masses and SFRs have been published for the Edge sample ((cite: Rawle_2012); (cite: O_Dea_2008)); however, we choose to recalculate these values to allow for a homogeneous comparison between the Edge sample and our own. We therefore calculate both stellar masses and SFRs for these BCGs using the methods outlined in §[2.5](#ssec:stellarmass_SFR), including multiplying the SFR by the same FAST conversion factor, as the multiband photometry used in this SED fit is not available for the Edge galaxies. We take 3.6 $\mu$m flux values from (cite: quillen2008infrared), (cite: Yamagishi_2010), and (cite: landt_2010)), and MIPS 24 $\mu$m photometry from (cite: quillen2008infrared), (cite: Yamagishi_2010), (cite: shi_2005), and the Spitzer Science Source List ((cite: 2010ASPC..434..437T)).

## AGN Contamination

To check for AGN contamination, we compare the IRAC colours of both our sample (from SWIRE; (cite: lonsdale2003swire)) and the Edge sample ((cite: quillen2008infrared); (cite: Yamagishi_2010); (cite: landt_2010)) to the criteria described in (cite: Donley_2012). We find one CO-detected galaxy from each sample falls into the Donley AGN wedge, as well as the three nondetected galaxies at higher redshifts. These galaxies all show high sSFRs, and the $24 \ \mu m$ flux is likely dominated by the AGN; we thus exclude them from all further analysis but continue to show them on plots.

# Results

The molecular gas properties of our BCG sample are presented in Table [\[tab:results\]](#tab:results). With the largest and highest-$z$ sample of significant molecular gas detections in BCGs assembled, we can investigate the reservoirs fueling their in-situ star formation.

## Gas properties compared to the larger galaxy population

To place the gas in our BCGs in context, we compare in Figure [3](#fig:mgas_vs_redshift) the molecular gas reservoirs found in our sample to those of a range of other galaxy types[^2]. We pick out the (cite: edge2001detection) sample described in §[2.6](#ssec:edge) as our main comparison sample. We indicate also the two other BCGs selected from SpARCS with confident molecular gas detections — SpARCS1049 ((cite: Webb_2017_1049)), whose gas has recently been shown to be fed by a massive cooling flow ((cite: hlavaceklarrondo2020_1049CC)) and J0225-303 ((cite: noble2019_clustergalmgas)), which possibly represents a merging BCG based on rest-frame optical HST imaging, but whose cluster dynamical state has not been conclusively determined. The gap in coverage visible at $0.8\lesssim z \lesssim 1.0$ corresponds to the redshift range within which CO lines fall into the gap in the ALMA frequency coverage between bands 3 and 4.

Figure [3](#fig:mgas_vs_redshift) makes it immediately obvious that our sample reaches much higher redshift ranges than all previous BCG surveys. Few large-scale studies of molecular gas in BCGs have been undertaken, and those which do exist have been limited in distance by both CO instrument quality and the availability of cluster surveys at high redshifts. Above z $\sim 0.3$, most existing BCG gas masses come from targeted observations of known exceptional objects. These include the BCGs in Abell 1664 (z $=$ 0.128; (cite: russell_2014_abell1664bcg)), Abell 1835 (z $=$ 0.252; (cite: mcnamara2014_a1835bcg)), the Phoenix cluster (z $=$ 0.596; (cite: Russell_2017_phoenix)), and SpARCS 1049 (z $=$ 1.709; (cite: Webb_2017_1049)). Previous BCG studies include (cite: edge2001detection) (described in detail in §[2.6](#ssec:edge)), who detecteed 16 BCGs, (cite: salome_combes_2003), who detected 6 BCGs, with some overlap with the (cite: edge2001detection) sample, and (cite: castignani2020molecular), who detected 5 BCGs. Our sample of 24 BCGs is therefore large by comparison. Each of these studies had detection rates considerably lower than our own, likely because these studies either did not select their sample based on star formation ((cite: edge2001detection); (cite: salome_combes_2003)), or used a much weaker SFR criterion ((cite: castignani2020molecular)).

ccclhcchhhhhhcchcc SWIRE & RA & DEC & $z_\mathrm{OzDES}$ & & $v_\mathrm{CO}$ Offset & $S_\mathrm{CO}\Delta v$ & & & & & & & M$_\mathrm{gas}$ & FWHM & & SFR & $\mathrm{M}_*$\
Patch & \[deg\] & \[deg\] & & & \[km s$^{-1}$\] & \[Jy km s$^{-1}$\] & & & & & & & \[$\times 10^{10}, _{ \ } \mathrm{M}_\odot$\] & \[km s$^{-1}$\] & & \[$\mathrm{M}_\odot \ \mathrm{yr}^{-1}$\] & \[$\times 10^{10}, _{ \ }\mathrm{M}_\odot$\]\
XMM-CO1 & 33.65927 & -3.62736 & 1.0033 & $1.0058 \pm 0.0007$ & $187 \pm 100$ & $0.50 \pm 0.15$ & 1699.8 & 0.3 & 75.0 & 0.433 & 100 & $5.9\pm 2.5$ & $3.8 \pm 1.6$ & $147 \pm 84 \ $ & 1 & $670^{+280}_{-200}$ & $22.9^{+14.0}_{-8.7}$\
XMM-CO2 & 33.93287 & -4.41511 & 0.4566 & $0.4556 \pm 0.0003$ & -$150 \pm 150 \ $ & $0.51 \pm 0.20$ & 303.0 & 0.2 & 56.0 & 0.384 & 150 & $1.3 \pm 0.5$ & $0.8 \pm 0.3$ & $531 \pm 127$ & 1 & $27^{+11}_{-8}$ & $14.8^{+9.1 \ }_{-5.6}$\
XMM-CO3 & 34.64331 & -5.01232 & 0.6410 & $0.6513 \pm 0.0003$ & $162 \pm 75_{\ }$ & $1.09 \pm 0.26$ & 301.8 & 0.3 & 63.6 & 0.398 & 75 & $5.0 \pm 1.7$ & $3.3 \pm 1.1$ & $133 \pm 63 \ $ & 1 & $34^{+14}_{-10}$ & $14.5^{+8.8 \ }_{-5.5}$\
XMM-CO4 & 34.79386 & -3.72621 & 0.7634 & - & - & $<0.26$ & 516.0 & 0.3 & 67.2 & 0.779 & 300 & $< 0.5$ & $<0.9$ & - & - & $410^{+169}_{-120}$ & $17.4^{+8.7 \ }_{-5.8}$\
XMM-CO5 & 34.87044 & -4.11663 & 0.7826 & $0.7824 \pm 0.0001$ & -$17 \pm 25 \ $ & $2.36 \pm 0.30$ & 303.0 & 0.2 & 50.0 & 0.663 & 100 & $1.0 \pm 0.3$ & $11.0 \pm 1.3 \ $ & $271 \pm 21 \ $ & 2 & $140^{+60 \ }_{-40}$ & $13.4^{+8.2 \ }_{-5.1}$\
XMM-CO6 & 34.92392 & -4.00916 & 0.2043 & $0.2042 \pm 0.0001$ & -$27 \pm 100$ & $1.95 \pm 0.57$ & 303.0 & 0.2 & 50.0 & 0.663 & 100 & $1.0 \pm 0.3$ & $0.7 \pm 0.3$ & $473 \pm 84 \ $ & 1 & $3.0^{+1.2}_{-0.9}$ & $12.4^{+7.5 \ }_{-4.7}$\
XMM-CO7 & 35.22837 & -3.54931 & 1.0346 & - & - & $<0.28$ & 2001.0 & 0.4 & 86.4 & 0.248 & 300 & $< 0.9$ & $< 1.7$ & - & 1 & $420^{+168}_{-120}$ & $26.0^{+13.0}_{-8.6}$\
XMM-CO8 & 36.11233 & -5.60891 & 0.2120 & $0.2112 \pm 0.0001$ & -$164 \pm 50 \ \ $ & $3.88 \pm 0.67$ & 301.8 & 0.2 & 46.4 & 0.535 & 25 & $1.8 \pm 0.4$ & $1.2 \pm 0.3$ & $503 \pm 42 \ $ & 2 & $11^{+4 \ }_{-3}$ & $6.5^{+4.0}_{-2.5}$\
ES1-CO1 & 10.26937 & -44.50626 & 0.3446 & $0.3477 \pm 0.0003$ & $517 \pm 200$ & $0.65 \pm 0.55$ & 301.8 & 0.2 & 52.0 & 1.200 & 200 & $0.8 \pm 0.7$ & $0.6 \pm 0.5$ & $188 \pm 169$ & 1 & $6.1^{+2.5}_{-1.8}$ & $22.2^{+13.5}_{-8.4}$\
ES1-CO2 & 6.97816 & -43.27981 & 1.0881 & $1.0866 \pm 0.0006$ & -$103 \pm 75_{\ \ \ }$ & $0.97 \pm 0.20$ & 1483.8 & 0.3 & 81.0 & 0.193 & 75 & $10.3 \pm 2.2 \ $ & $8.7 \pm 1.7$ & $191 \pm 63 \ $ & 2 & $75^{+31}_{-22}$ & $6.6^{+4.1}_{-2.5}$\
ES1-CO3 & 7.03042 & -43.3448 & 0.8068 & $0.8059 \pm 0.0001$ & -$84 \pm 25 \ $ & $1.48 \pm 0.29$ & 576.0 & 0.3 & 75.0 & 0.330 & 75 & $11.2 \pm 2.2 \ $ & $7.3 \pm 1.4$ & $403 \pm 21 \ $ & 2 & $73^{+30}_{-21}$ & $9.8^{+6.0}_{-3.7}$\
ES1-CO4 & 8.26314 & -42.72425 & 0.7281 & $0.7296 \pm 0.0004$ & $147 \pm 100$ & $1.37 \pm 0.25$ & 516.0 & 0.3 & 67.2 & 0.334 & 100 & $8.9 \pm 1.9$ & $5.8 \pm 1.3$ & $541 \pm 84 \ $ & 1 & $42^{+17}_{-12}$ & $6.5^{+4.0}_{-2.5}$\
ES1-CO5 & 8.70355 & -42.23410 & 0.4776 & - & - & $<0.41$ & 301.8 & 0.25 & 62.5 & 1.074 & 300 & $< 0.4$ & $<0.7$ & - & - & $12^{+6 \ }_{-4}$ & $15.6^{+7.8 \ }_{-5.2}$\
ES1-CO7 & 8.81504 & -42.78926 & 0.6567 & $0.6538 \pm 0.0007$ & -$314 \pm 200 \ $ & $0.59 \pm 0.21$ & 301.8 & 0.3 & 75.0 & 0.400 & 200 & $3.1 \pm 1.2$ & $2.0 \pm 0.8$ & $394 \pm 169$ & 1 & $28^{+11}_{-8}$ & $9.4^{+5.7}_{-3.6}$\
ES1-CO8 & 8.81970 & -42.68564 & 0.5640 & $0.5630 \pm 0.0001$ & -$113 \pm 50 \ \ $ & $1.58 \pm 0.34$ & 301.8 & 0.3 & 75.0 & 0.430 & 50 & $5.6 \pm 1.0$ & $3.6 \pm 0.6$ & $253 \pm 42 \ $ & 2 & $38^{+15}_{-11}$ & $5.5^{+3.4}_{-2.1}$\
ES1-CO9 & 9.41918 & -43.65286 & 1.1937 & $1.1924 \pm 0.0002$ & -$83 \pm 25 \ $ & $0.83 \pm 0.11$ & 1272.0 & 0.3 & 90.0 & 0.225 & 25 & $13.8 \pm 1.7 \ $ & $8.9 \pm 1.1$ & $156 \pm 21 \ $ & 1 & $250^{+100}_{-70}$ & $7.6^{+4.8}_{-2.9}$\
ES1-CO10 & 9.76238 & -44.36451 & 0.7474 & $0.7472 \pm 0.0004$ & $\ $-$23 \pm 100$ & $1.13 \pm 0.39$ & 516.0 & 0.3 & 75.0 & 0.326 & 100 & $7.3 \pm 2.5$ & $4.8 \pm 1.6$ & $494 \pm 84 \ $ & 1 & $37^{+15}_{-10}$ & $15.2^{+9.3 \ }_{-5.8}$\
CDFS-CO1 & 52.26829 & -28.79808 & 0.2891 & $0.2888 \pm 0.0001$ & -$50 \pm 25 \ $ & $14.33 \pm 1.23$ & 303.0 & 0.2 & 50.0 & 0.620 & 50 & $13.0 \pm 1.0 \ $ & $8.4 \pm 0.7$ & $558 \pm 21 \ $ & 2 & $35^{+14}_{-10}$ & $15.8^{+9.6 \ }_{-6.0}$\
CDFS-CO2 & 52.90532 & -28.40428 & 0.2151 & $0.2159 \pm 0.0001$ & $170 \pm 25 \ $ & $4.41 \pm 0.27$ & 303.0 & 0.2 & 50.0 & 0.530 & 50 & $2.2 \pm 0.1$ & $1.42 \pm 0.09$ & $144 \pm 21 \ $ & 1 & $35^{+14}_{-10}$ & $4.9^{+3.0}_{-1.8}$\
CDFS-CO3 & 53.31982 & -26.89622 & 0.8076 & $0.810 \pm 0.001$ & $237 \pm 200$ & $0.18 \pm 0.39$ & 547.2 & 0.3 & 75.0 & 0.340 & 175 & $1.1 \pm 0.8$ & $0.7 \pm 0.5$ & $564 \pm 169$ & 1 & $54^{+22}_{-15}$ & $12.9^{+7.9 \ }_{-4.9}$\
CDFS-CO4 & 53.46281 & -27.33505 & 0.4511 & $0.4508 \pm 0.0002$ & -$53 \pm 75 \ $ & $1.59 \pm 0.49$ & 303.0 & 0.2 & 56.0 & 0.957 & 75 & $3.6 \pm 0.8$ & $2.4 \pm 0.5$ & $493 \pm 63 \ $ & 2 & $24^{+10}_{-7}$ & $20.6^{+12.6}_{-7.8}$\
CDFS-CO5 & 53.48398 & -27.25938 & 0.6948 & $0.6947 \pm 0.0004$ & -$13 \pm 100$ & $1.87 \pm 0.50$ & 303.0 & 0.3 & 75.0 & 0.360 & 100 & $10.3 \pm 2.2 \ $ & $6.7 \pm 1.4$ & $432 \pm 84 \ $ & 2 & $54^{+22}_{-15}$ & $11.5^{+7.1 \ }_{-4.4}$\
CDFS-CO6 & 53.55353 & -28.41692 & 0.6643 & - & - & $<0.23$ & 303.0 & 0.3 & 67.2 & 0.350 & 300 & $< 0.4$ & $<0.8$ & - & 1 & $180^{+69 \ }_{-50}$ & $20.1^{+10.0}_{-6.7}$\
CDFS-CO7 & 53.72804 & -27.09096 & 0.6760 & $0.6770 \pm 0.0008$ & $105 \pm 200$ & $0.55 \pm 0.18$ & 301.8 & 0.3 & 67.2 & 0.320 & 200 & $2.9 \pm 1.0$ & $1.9 \pm 0.6$ & $448 \pm 169 \ $ & 1 & $23^{+9 \ }_{-6}$ & $11.6^{+7.1 \ }_{-4.4}$\
CDFS-CO8 & 53.77638 & -29.26097 & 0.5950 & $0.5966 \pm 0.0006$ & $185 \pm 200$ & $1.18 \pm 0.39$ & 301.8 & 0.3 & 67.2 & 0.374 & 200 & $4.8\pm 1.6$ & $3.1 \pm 1.0$ & $471 \pm 169 \ $ & 1 & $73^{+30}_{-21}$ & $13.7^{+8.3 \ }_{-5.2}$\
CDFS-CO9 & 53.79709 & -27.77951 & 0.4428 & - & - & $<0.15$ & 301.8 & 0.2 & 56.0 & 0.366 & 300 & $< 0.2$ & $<0.4$ & - & - & $11^{+4 \ }_{-3}$ & $16.0^{+8.0 \ }_{-5.3}$\
CDFS-CO10 & 53.83965 & -29.61118 & 0.3079 & - & - & $<0.36$ & 301.8 & 0.2 & 54.0 & 0.511 & 300 & $< 0.2$ & $<0.3$ & - & - & $3.9^{+1.5}_{-1.1}$ & $14.8^{+7.4 \ }_{-4.9}$\
CDFS-CO11 & 53.86995 & -27.28562 & 0.3189 & $0.3190 \pm 0.0001$ & $\ 9 \pm 25$ & $1.23 \pm 0.19$ & 303.0 & 0.2 & 54.0 & 0.430 & 25 & $1.4 \pm 0.3$ & $0.9 \pm 0.1$ & $56 \pm 21$ & 1 & $9.5^{+3.9}_{-2.8}$ & $5.6^{+3.4}_{-2.1}$\
CDFS-CO12 & 53.89642 & -27.26368 & 0.3422 & $0.3427 \pm 0.0003$ & $\ 73 \pm 200$ & $0.90 \pm 0.46$ & 301.8 & 0.2 & 54.0 & 0.431 & 200 & $1.6 \pm 0.7$ & $1.0 \pm 0.5$ & $447 \pm 169$ & 1 & $6.1^{+2.5}_{-1.8}$ & $7.9^{+4.8}_{-3.0}$\
CDFS-CO13 & 54.07105 & -28.38037 & 0.3567 & $0.3562 \pm 0.0001$ & -$93 \pm 25 \ $ & $2.31 \pm 0.34$ & 301.8 & 0.2 & 54.0 & 0.370 & 25 & $3.3 \pm 0.5$ & $2.1 \pm 0.3$ & $327 \pm 21 \ $ & 2 & $36^{+15}_{-10}$ & $10.3^{+6.2 \ }_{-3.9}$

## Direct comparison with lower-redshift BCGs

![](sSFR_Mgas_2panel.png)

In the field, tight correlations are known to exist between a galaxy’s SFR, M$_*$, and gas mass (e.g. (cite: genzel2010_Scalingrelations)), suggesting a uniformity in baryon processing by field galaxies. To test if similar correlations exist in BCGs, we compare the sSFRs and molecular gas masses of our sample to those BCGs detected by (cite: edge2001detection) in Figure [4](#fig:mgas_vs_ssfr). Due to the sSFR depth limitations discussed in §[2.5](#ssec:stellarmass_SFR), we first analyze only the BCGs in our sample with redshifts below 0.6 (left panel). To determine if the two samples exhibit the same sSFR/$\mathrm{M}_\mathrm{gas} \ $properties, we fit a straight line to each sample separately in logarithmic space, using Orthogonal Distance Regression (ODR) to account for uncertainties existing in both axes. We show fits, and their 1$\sigma$ confidence regions, in Figure [4](#fig:mgas_vs_ssfr). With (logarithmic) slopes of $0.9 \pm 0.3$ and $0.9 \pm 0.2$ and offsets of $-10 \pm 3$ and $-10 \pm 2$, respectively, our sample of BCGs and the (cite: edge2001detection) sample display the same correlation below z $=0.6$. As the slope in this plot is log(SFR/M$_*$) / log(M$_\mathrm{gas}$), a quantity related to the star formation efficiency (SFR/M$_\mathrm{gas}$), this suggests the two samples are processing molecular gas through similar means.

In the right panel of Figure [4](#fig:mgas_vs_ssfr), we plot the complete sample over all redshifts. Much of our sample to z $\sim$ 1.0 falls into the $1\sigma$ confidence region of the fit to the (cite: edge2001detection) BCGs, suggesting that this similarity in gas processing could persist to higher redshifts, but this is inconclusive due to the small sample size and potential selection effects from limited sensitivity. The BCGs at redshifts above z $\sim$ 1.0 seem to fall above this relation, suggesting a possible change in gas processing, but this is again somewhat speculative due to the limits of the sample. In both panels the CO nondetections are included for comparison. We note the three nondetections which fall off the plotted correlation all have sSFRs which are likely inflated by the presence of AGN.

While we have worked to control for all potential systematic sSFR/$\mathrm{M}_\mathrm{gas} \ $differences between the two samples, there do remain several limitations. These include the different CO line transitions used in the $\mathrm{M}_\mathrm{gas} \ $values calculated by (cite: edge2001detection), the difficulty defining selection effects in this sample (which includes measurements from several different sources), and the incompleteness of our own sample. Additionally, while several large samples or field galaxies with molecular gas measurements do exist, such as ASPECS (cite: Decarli_2016_ASPECS), PHIBSS1 (cite: tacconi2013phibss), and PHIBBS2 (cite: freundlich2019phibss2), few of these galaxies have both the 3.6 $\mu$m and 24 $\mu$m measurements necessary for rigorous comparison with the BCGs in this work, and those that do tend to fall above the MS. Ultimately, more CO data is required, for BCGs and field galaxies, particularly at high redshifts.

# Discussion

We measure CO (2-1) in a sample of 30 star-forming BCGs, chosen from SpARCS. We find that 80% of our BCGs are detected in CO, suggesting that molecular gas is common in star-forming BCGs at high redshifts. While this is seemingly in contrast with the results of similar BCG surveys such as (cite: castignani2020molecular), we note that these previous studies imposed no SFR limit on their samples (see §[3.1](#ssec:gasproperties)). We specifically target star-forming galaxies, and new stars cannot form without fuel.

Semi-Analytic Models suggest that strangulation, ram-pressure stripping, and other cluster effects actively remove molecular gas from galaxies in dense environments (e.g. (cite: delucia_20017_SAMs); (cite: gavazzi2006_clustergasdef)), and therefore limit star formation. It is thus necessary to account for two different processes when analyzing BCG star formation — the process by which gas is deposited onto the BCG, and the mechanism by which the BCG converts that gas into stars. This distinction between gas feeding and processing in BCGs may have important implications, especially as similar theories have been proposed for the general galaxy population (c.f. (cite: behroozi2019_halomass)).

In Figure [4](#fig:mgas_vs_ssfr), we show that our BCG sample at z $\leq 0.6$ has a remarkably similar correlation between M$_\mathrm{gas}$ and sSFR to that of (cite: edge2001detection), with nearly identical slopes. This implies that the two BCG samples are both processing their in-situ molecular gas into stars with the same efficiency for a given stellar mass. This correlation exists at z $\leq 0.6$, and possibly to higher redshifts (z $\sim1.0$), although this is uncertain due to the limiting depth of the sample, suggesting that many star-forming BCGs at $0<z\leq0.6$ may regulate the formation of these stars from gas in the same way, independent of their redshift or cluster properties. This is a picture of galaxy star formation which has been proposed for non-BCGs (e.g. (cite: bouche2010gasregulator); (cite: dekel2014analytic)).

Similarities in star-formation processes between the (cite: edge2001detection) sample and our own have the potential to be very interesting, as the two samples differ in both selection method and cluster mass, in addition to the redshift difference discussed in §[2.6](#ssec:edge). The (cite: edge2001detection) sample contains only BCGs from known cool-core clusters. In fact, all previous large BCG studies have selected galaxies either explicitly from known cool-core clusters ((cite: edge2001detection); (cite: salome_combes_2003)), or from X-ray surveys ((cite: castignani2020molecular)). The parent, red-sequence selected SpARCS sample does not select clusters based on ICM state, and should therefore exhibit no cool-core selection effects. While the cool-core fraction varies depending on the selection criteria used, it should be $\lesssim 0.3$ in the redshift range we study (cite: McDonald_2013CCfraction).

We do note, however, that our BCG sample is selected on star formation, which may bias it towards cool-core clusters (e.g. (cite: Fogarty_2015_CLASHsf)). If our galaxies are all cool-core cluster BCGs, and therefore fed by cooling flows, this is an interesting result on its own, as additional confirmation that the star formation we see in BCGs at z $\lesssim 0.6$ may be the result of those BCGs being fed molecular gas principally by cooling flows, instead of other possible scenarios such as gas-rich mergers. Unfortunately, we lack the X-ray measurements necessary to confirm the dynamical state of our clusters.

These speculations should not affect our main result — $\mathrm{M}_\mathrm{gas} \ $is a measurement of the amount of gas already in the galaxy. However, the CO-to-H$_2$ conversion factor used to determine molecular gas mass depends, among other things, on gas density (e.g. (cite: bolatto2013co)). If some of our BCGs are dynamically unrelaxed post-mergers, this conversion factor could be affected, changing the relation. It is possible that we see this effect in Figure [4](#fig:mgas_vs_ssfr) at high redshifts, where BCGs tend to appear above the relation. This is in line with past work such as (cite: mcdonald2016star), which suggests that the mechanism fueling star formation changes from primarily cooling flows to gas-rich mergers in BCGs at z $\raisebox{-0.13cm}{~\shortstack{$>$ \\[-0.07cm]$\sim$}}~0.6$.

We cannot compare the cluster halo masses of our sample to those of (cite: edge2001detection) in depth, as we have no equivalent measurements to compare. We do, however, have cluster richnesses ($\mathrm{N}_\mathrm{gal}$) measured from SpARCS ((cite: webb2015_SpARCS)) for our sample, and halo masses based on SDSS DR7 ((cite: popesso2020_edgemcluster); (cite: yang2005galaxy)) for the (cite: edge2001detection) BCGs. As $\mathrm{N}_\mathrm{gal} \ $$=12$ is roughly equal to M$_{200} \sim 1\times10^{14}$ (e.g. (cite: andreon2014_ngalmass)), our clusters have an average cluster mass $\sim (1.5 \pm 0.7)\times10^{14} \ \mathrm{M}_\odot$, compared to an average cluster mass of $\sim (1.3 \pm 0.9)\times 10^{15}\ \mathrm{M}_\odot$ for the (cite: edge2001detection) sample. The clusters presented in (cite: edge2001detection) are therefore almost an order of magnitude more massive than ours.

It has been suggested that halo mass is directly related to central galaxy star formation, with the fraction of quenched central galaxies increasing with host halo mass (e.g. (cite: behroozi2019_halomass)). However, the star formation efficiency for galaxies at a given distance from the MS has been shown not to change with host halo mass (cite: popesso2020_edgemcluster). We select only star-forming galaxies (i.e., galaxies at a fixed distance from the MS; Figure [1](#fig:ssfrs)), so our values are unaffected by the fraction of quenched central galaxies at a given halo mass, and it is therefore unsurprising that the two BCG samples line up well despite their differing cluster masses.

# Conclusions

We present the largest and highest-redshift study of molecular gas in BCGs to date. Using ALMA bands 3, 4, and 5, we study CO (2-1) in 30 SpARCS BCGs. We summarize our results as follows:

1.  We find that molecular gas is common in star-forming BCGs at $0.2\leq \mathrm{z}\leq 1.2$, detecting gas reservoirs in 80% of our sample of 30 galaxies.

2.  We note a clear M$_\mathrm{gas}$-sSFR trend is apparent in our sample. Below z $=0.6$ this trend is consistent to $1\sigma$ with the sample of BCGs presented in (cite: edge2001detection). We therefore propose a scenario by which most BCGs below z $\sim0.6$ process molecular gas into stars at a rate dependent on stellar mass, through mechanisms independent of redshift, and likely independent of cluster mass and cluster dynamical state. This scenario appears to persist to higher redshifts, but we require a larger and more complete sample to determine this conclusively.

The process by which these BCGs obtain molecular gas is still not clear. We require X-ray observations of our clusters to confirm both their dynamical state and their total mass. Still, as a large, high-z, collection of BCGs selected homogeneously and detected in CO, our sample offers an exciting means by which to study cluster evolution as a whole.

# Acknowledgments

TMAW and DAD acknowledge the support of the Natural Sciences and Engineering Research Council of Canada (NSERC) and the Fonds de Recherche Nature et Technologies Quebec (FRQNT).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01529.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research has made use of the NASA/IPAC Infrared Science Archive, which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology. Based in part on data acquired at the Anglo-Australian Telescope, under program A/2013B/012. We acknowledge the traditional owners of the land on which the AAT stands, the Gamilaraay people, and pay our respects to elders past and present. GW gratefully acknowledges support from the National Science Foundation through grant AST-1517863, from HST program number GO-15294, and from grant number 80NSSC17K0019 issued through the NASA Astrophysics Data Analysis Program (ADAP). Support for program number GO-15294 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555.

This project used public archival data from the Dark Energy Survey (DES). Funding for the DES Projects has been provided by the U.S. Department of Energy, the U.S. National Science Foundation, the Ministry of Science and Education of Spain, the Science and Technology Facilities Council of the United Kingdom, the Higher Education Funding Council for England, the National Center for Supercomputing Applications at the University of Illinois at Urbana-Champaign, the Kavli Institute of Cosmological Physics at the University of Chicago, the Center for Cosmology and Astro-Particle Physics at the Ohio State University, the Mitchell Institute for Fundamental Physics and Astronomy at Texas A&M University, Financiadora de Estudos e Projetos, Fundação Carlos Chagas Filho de Amparo à Pesquisa do Estado do Rio de Janeiro, Conselho Nacional de Desenvolvimento Científico e Tecnológico and the Ministério da Ciência, Tecnologia e Inovação, the Deutsche Forschungsgemeinschaft, and the Collaborating Institutions in the Dark Energy Survey.

The Collaborating Institutions are Argonne National Laboratory, the University of California at Santa Cruz, the University of Cambridge, Centro de Investigaciones Energéticas, Medioambientales y Tecnológicas-Madrid, the University of Chicago, University College London, the DES-Brazil Consortium, the University of Edinburgh, the Eidgenössische Technische Hochschule (ETH) Zürich, Fermi National Accelerator Laboratory, the University of Illinois at Urbana-Champaign, the Institut de Ciències de l’Espai (IEEC/CSIC), the Institut de Física d’Altes Energies, Lawrence Berkeley National Laboratory, the Ludwig-Maximilians Universität München and the associated Excellence Cluster Universe, the University of Michigan, the National Optical Astronomy Observatory, the University of Nottingham, The Ohio State University, the OzDES Membership Consortium, the University of Pennsylvania, the University of Portsmouth, SLAC National Accelerator Laboratory, Stanford University, the University of Sussex, and Texas A&M University.

Based in part on observations at Cerro Tololo Inter-American Observatory, National Optical Astronomy Observatory, which is operated by the Association of Universities for Research in Astronomy (AURA) under a cooperative agreement with the National Science Foundation.

natexlab

(ref: sdssDR7) Abazajian, K. N., Adelman-McCarthy, J. K., Agüeros, M. A., et al. 2009, ApJS, 182, 543, doi: [`10.1088/0067-0049/182/2/543`](http://doi.org/10.1088/0067-0049/182/2/543)

(ref: Abbott_2018_DES) Abbott, T. M. C., Abdalla, F. B., Allam, S., et al. 2018, ApJS, 239, 18, doi: [`10.3847/1538-4365/aae9f0`](http://doi.org/10.3847/1538-4365/aae9f0)

(ref: sdssDR6) Adelman-McCarthy, J. K., Agüeros, M. A., Allam, S. S., et al. 2008, ApJS, 175, 297, doi: [`10.1086/524984`](http://doi.org/10.1086/524984)

(ref: andreon2014_ngalmass) Andreon, S., & Congdon, P. 2014, A&A, 568, A23

(ref: aravena2020_ASPECS) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, ApJ, 901, 79

(ref: Bauermeister_2013_EGNOG) Bauermeister, A., Blitz, L., Bolatto, A., et al. 2013, ApJ, 768, 132, doi: [`10.1088/0004-637x/768/2/132`](http://doi.org/10.1088/0004-637x/768/2/132)

(ref: behroozi2019_halomass) Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C. 2019, MNRAS, 488, 3143, doi: [`10.1093/mnras/stz1182`](http://doi.org/10.1093/mnras/stz1182)

(ref: bolatto2013co) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: boogaard2020alma) Boogaard, L. A., Werf, P. v. d., Weiss, A., et al. 2020, ApJ, 902, 109, doi: [`10.3847/1538-4357/abb82f`](http://doi.org/10.3847/1538-4357/abb82f)

(ref: bouche2010gasregulator) Bouché, N., Dekel, A., Genzel, R., et al. 2010, ApJ, 718, 1001

(ref: braun2011molecular) Braun, R., Popping, A., Brooks, K., & Combes, F. 2011, MNRAS, 416, 2600

(ref: brownson2020drives) Brownson, S., Belfiore, F., Maiolino, R., Lin, L., & Carniani, S. 2020, MNRAS: Letters, 498, L66

(ref: bruzual2003stellar) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000

(ref: capozzi2012kcorr) Capozzi, D., Collins, C. A., Stott, J. P., & Hilton, M. 2012, MNRAS, 419, 2821, doi: [`10.1111/j.1365-2966.2011.19895.x`](http://doi.org/10.1111/j.1365-2966.2011.19895.x)

(ref: castignani2020molecular) Castignani, G., Pandey-Pommier, M., Hamer, S. L., et al. 2020, A&A, 640, A65, doi: [`10.1051/0004-6361/202038081`](http://doi.org/10.1051/0004-6361/202038081)

(ref: chary2001interpreting) Chary, R., & Elbaz, D. 2001, ApJ, 556, 562

(ref: combes2013_polarringgalaxies) Combes, F., Moiseev, A., & Reshetnikov, V. 2013, A&A, 554, A11, doi: [`10.1051/0004-6361/201321385`](http://doi.org/10.1051/0004-6361/201321385)

(ref: delucia_20017_SAMs) De Lucia, G., & Blaizot, J. 2007, MNRAS, 375, 2, doi: [`10.1111/j.1365-2966.2006.11287.x`](http://doi.org/10.1111/j.1365-2966.2006.11287.x)

(ref: Decarli_2016_ASPECS) Decarli, R., Walter, F., Aravena, M., et al. 2016, ApJ, 833, 70, doi: [`10.3847/1538-4357/833/1/70`](http://doi.org/10.3847/1538-4357/833/1/70)

(ref: dekel2014analytic) Dekel, A., & Mandelker, N. 2014, MNRAS, 444, 2071

(ref: demarco2010spectroscopic) Demarco, R., Wilson, G., Muzzin, A., et al. 2010, ApJ, 711, 1185

(ref: Donley_2012) Donley, J. L., Koekemoer, A. M., Brusa, M., et al. 2012, ApJ, 748, 142, doi: [`10.1088/0004-637x/748/2/142`](http://doi.org/10.1088/0004-637x/748/2/142)

(ref: edge2001detection) Edge, A. 2001, MNRAS, 328, 762

(ref: elbaz2011_ssfrMS) Elbaz, D., Dickinson, M., Hwang, H. S., et al. 2011, A&A, 533, A119, doi: [`10.1051/0004-6361/201117239`](http://doi.org/10.1051/0004-6361/201117239)

(ref: fabian1977subsonic) Fabian, A., & Nulsen, P. 1977, MNRAS, 180, 479

(ref: Fogarty_2015_CLASHsf) Fogarty, K., Postman, M., Connor, T., Donahue, M., & Moustakas, J. 2015, ApJ, 813, 117, doi: [`10.1088/0004-637x/813/2/117`](http://doi.org/10.1088/0004-637x/813/2/117)

(ref: fogarty2019_MACS1931.8-2635bcg) Fogarty, K., Postman, M., Li, Y., et al. 2019, ApJ, 879, 103, doi: [`10.3847/1538-4357/ab22a4`](http://doi.org/10.3847/1538-4357/ab22a4)

(ref: freundlich2019phibss2) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2019, A&A, 622, A105

(ref: gavazzi2006_clustergasdef) Gavazzi, G., O’Neil, K., Boselli, A., & Van Driel, W. 2006, A&A, 449, 929

(ref: geach2011evolution) Geach, J. E., Smail, I., Moran, S. M., et al. 2011, ApJL, 730, L19

(ref: genzel2010_Scalingrelations) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091, doi: [`10.1111/j.1365-2966.2010.16969.x`](http://doi.org/10.1111/j.1365-2966.2010.16969.x)

(ref: gladders2005red) Gladders, M. D., & Yee, H. K. 2005, ApJS, 157, 1

(ref: SDSS_photometry_camera) Gunn, J. E., Carr, M., Rockosi, C., et al. 1998, ApJ, 116, 3040, doi: [`10.1086/300645`](http://doi.org/10.1086/300645)

(ref: hatsukade2020_GRBhosts) Hatsukade, B., Ohta, K., Hashimoto, T., et al. 2020, ApJ, 892, 42

(ref: hernancaballero2009_sparcsz) Hernán-Caballero, A., Pérez-Fournon, I., Hatziminaoglou, E., et al. 2009, MNRAS, 395, 1695, doi: [`10.1111/j.1365-2966.2009.14660.x`](http://doi.org/10.1111/j.1365-2966.2009.14660.x)

(ref: hlavaceklarrondo2020_1049CC) Hlavacek-Larrondo, J., Rhea, C. L., Webb, T., et al. 2020, ApJL, 898, L50, doi: [`10.3847/2041-8213/ab9ca5`](http://doi.org/10.3847/2041-8213/ab9ca5)

(ref: Jablonka_2013) Jablonka, P., Combes, F., Rines, K., Finn, R., & Welch, T. 2013, A&A, 557, A103, doi: [`10.1051/0004-6361/201321104`](http://doi.org/10.1051/0004-6361/201321104)

(ref: kennicutt1998_SFR) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189, doi: [`10.1146/annurev.astro.36.1.189`](http://doi.org/10.1146/annurev.astro.36.1.189)

(ref: kriek2018FAST) Kriek, M., van Dokkum, P. G., Labbé, I., et al. 2018, FAST: Fitting and Assessment of Synthetic Templates. [`http://ascl.net/1803.008`](http://ascl.net/1803.008)

(ref: landt_2010) Landt, H., Buchanan, C. L., & Barmby, P. 2010, MNRAS, 408, 1982, doi: [`10.1111/j.1365-2966.2010.17264.x`](http://doi.org/10.1111/j.1365-2966.2010.17264.x)

(ref: lidman2012evidence) Lidman, C., Suherli, J., Muzzin, A., et al. 2012, MNRAS, 427, 550

(ref: lidman2020_newozdes) Lidman, C., Tucker, B. E., Davis, T. M., et al. 2020, MNRAS, 496, 19, doi: [`10.1093/mnras/staa1341`](http://doi.org/10.1093/mnras/staa1341)

(ref: lonsdale2003swire) Lonsdale, C. J., Smith, H. E., Rowan-Robinson, M., et al. 2003, PASP, 115, 897

(ref: mcdonald2012_phoenixSFR) McDonald, M., Bayliss, M., Benson, B. A., et al. 2012, Nature, 488, 349, doi: [`10.1038/nature11379`](http://doi.org/10.1038/nature11379)

(ref: McDonald_2013CCfraction) McDonald, M., Benson, B. A., Vikhlinin, A., et al. 2013, ApJ, 774, 23, doi: [`10.1088/0004-637x/774/1/23`](http://doi.org/10.1088/0004-637x/774/1/23)

(ref: mcdonald2016star) McDonald, M., Stalder, B., Bayliss, M., et al. 2016, ApJ, 817, 86

(ref: mcnamara2014_a1835bcg) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2014, ApJ, 785, 44, doi: [`10.1088/0004-637X/785/1/44`](http://doi.org/10.1088/0004-637X/785/1/44)

(ref: menzel2016_sparcsz) Menzel, M. L., Merloni, A., Georgakakis, A., et al. 2016, MNRAS, 457, 110, doi: [`10.1093/mnras/stv2749`](http://doi.org/10.1093/mnras/stv2749)

(ref: muzzin2009spectroscopic) Muzzin, A., Wilson, G., Yee, H., et al. 2009, ApJ, 698, 1934

(ref: muzzin2012gemini) —. 2012, ApJ, 746, 188

(ref: noble_2017) Noble, A. G., McDonald, M., Muzzin, A., et al. 2017, ApJL, 842, L21, doi: [`10.3847/2041-8213/aa77f3`](http://doi.org/10.3847/2041-8213/aa77f3)

(ref: noble2019_clustergalmgas) Noble, A. G., Muzzin, A., McDonald, M., et al. 2019, ApJ, 870, 56, doi: [`10.3847/1538-4357/aaf1c6`](http://doi.org/10.3847/1538-4357/aaf1c6)

(ref: O_Dea_2008) O’Dea, C. P., Baum, S. A., Privon, G., et al. 2008, ApJ, 681, 1035–1045, doi: [`10.1086/588212`](http://doi.org/10.1086/588212)

(ref: popesso2020_edgemcluster) Popesso, P., Concas, A., Morselli, L., et al. 2020, MNRAS, 496, 2531, doi: [`10.1093/mnras/staa1737`](http://doi.org/10.1093/mnras/staa1737)

(ref: quillen2008infrared) Quillen, A. C., Zufelt, N., Park, J., et al. 2008, ApJS, 176, 39

(ref: Rawle_2012) Rawle, T. D., Edge, A. C., Egami, E., et al. 2012, ApJ, 747, 29, doi: [`10.1088/0004-637x/747/1/29`](http://doi.org/10.1088/0004-637x/747/1/29)

(ref: remijan2019alma) Remijan, A., Biggs, A., Cortes, P., et al. 2019, ALMA doc, 7

(ref: Rieke_2009) Rieke, G. H., Alonso-Herrero, A., Weiner, B. J., et al. 2009, ApJ, 692, 556, doi: [`10.1088/0004-637x/692/1/556`](http://doi.org/10.1088/0004-637x/692/1/556)

(ref: russell_2014_abell1664bcg) Russell, H. R., McNamara, B. R., Edge, A. C., et al. 2014, ApJ, 784, 78, doi: [`10.1088/0004-637X/784/1/78`](http://doi.org/10.1088/0004-637X/784/1/78)

(ref: Russell_2017_phoenix) Russell, H. R., McDonald, M., McNamara, B. R., et al. 2017, ApJ, 836, 130, doi: [`10.3847/1538-4357/836/1/130`](http://doi.org/10.3847/1538-4357/836/1/130)

(ref: salome_combes_2003) Salomé, P., & Combes, F. 2003, A&A, 412, 657, doi: [`10.1051/0004-6361:20031438`](http://doi.org/10.1051/0004-6361:20031438)

(ref: salpeter_1955) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: shi_2005) Shi, Y., Rieke, G. H., Hines, D. C., et al. 2005, ApJ, 629, 88, doi: [`10.1086/431344`](http://doi.org/10.1086/431344)

(ref: solomon1997molecular) Solomon, P., Downes, D., Radford, S., & Barrett, J. 1997, ApJ, 478, 144

(ref: solomon2005molecular) Solomon, P., & Vanden Bout, P. 2005, Annu. Rev. Astron. Astrophys., 43, 677

(ref: swinbank2007_sparcsz) Swinbank, A. M., Edge, A. C., Smail, I., et al. 2007, MNRAS, 379, 1343, doi: [`10.1111/j.1365-2966.2007.12037.x`](http://doi.org/10.1111/j.1365-2966.2007.12037.x)

(ref: tacconi2013phibss) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: 2010ASPC..434..437T) Teplitz, H. I., Capak, P., Brooke, T., et al. 2010, in Astronomical Society of the Pacific Conference Series, Vol. 434, Astronomical Data Analysis Software and Systems XIX, ed. Y. Mizumoto, K. I. Morita, & M. Ohishi, 437

(ref: tremblay2016_abell2597bcg) Tremblay, G. R., Oonk, J. B. R., Combes, F., et al. 2016, Nature, 534, 218, doi: [`10.1038/nature17969`](http://doi.org/10.1038/nature17969)

(ref: vantyghem2016_2A0335+096) Vantyghem, A. N., McNamara, B. R., Russell, H. R., et al. 2016, ApJ, 832, 148, doi: [`10.3847/0004-637X/832/2/148`](http://doi.org/10.3847/0004-637X/832/2/148)

(ref: webb2015_SpARCS) Webb, T. M. A., Muzzin, A., Noble, A., et al. 2015, ApJ, 814, 96, doi: [`10.1088/0004-637X/814/2/96`](http://doi.org/10.1088/0004-637X/814/2/96)

(ref: Webb_2017_1049) Webb, T. M. A., Lowenthal, J., Yun, M., et al. 2017, ApJ, 844, L17, doi: [`10.3847/2041-8213/aa7749`](http://doi.org/10.3847/2041-8213/aa7749)

(ref: weedmanHouck2009_sparcsz) Weedman, D. W., & Houck, J. R. 2009, ApJ, 698, 1682, doi: [`10.1088/0004-637X/698/2/1682`](http://doi.org/10.1088/0004-637X/698/2/1682)

(ref: wen2010erratum) Wen, Z., Han, J., & Liu, F. 2010, ApJS, 187, 272

(ref: wen2012catalog) —. 2012, ApJS, 199, 34

(ref: wilson2009spectroscopic) Wilson, G., Muzzin, A., Yee, H., et al. 2009, ApJ, 698, 1943

(ref: Yamagishi_2010) Yamagishi, M., Kaneda, H., Ishihara, D., et al. 2010, PASJ, 62, 1085–1092, doi: [`10.1093/pasj/62.4.1085`](http://doi.org/10.1093/pasj/62.4.1085)

(ref: yang2005galaxy) Yang, X., Mo, H., Jing, Y., & Van Den Bosch, F. C. 2005, MNRAS, 358, 217

[^1]: N$_\mathrm{gal}$ is defined as the background-subtracted number of galaxies (of any color) within 500 kpc of the cluster centre brighter than (M$^*_{3.6\mu\mathrm{m}} + 1$).

[^2]: Non-BCG cluster galaxies are taken from (cite: noble2019_clustergalmgas), (cite: noble_2017) and (cite: Jablonka_2013). Field galaxies are taken from (cite: aravena2020_ASPECS), (cite: Bauermeister_2013_EGNOG), (cite: boogaard2020alma), (cite: braun2011molecular), (cite: brownson2020drives), (cite: combes2013_polarringgalaxies), (cite: Decarli_2016_ASPECS), (cite: freundlich2019phibss2), (cite: geach2011evolution), and (cite: hatsukade2020_GRBhosts). Other BCG detections are from (cite: castignani2020molecular), (cite: fogarty2019_MACS1931.8-2635bcg), (cite: mcnamara2014_a1835bcg), (cite: russell_2014_abell1664bcg), (cite: Russell_2017_phoenix), (cite: salome_combes_2003), (cite: tremblay2016_abell2597bcg), and (cite: vantyghem2016_2A0335+096).

</paper>

Write the methods card for this paper.