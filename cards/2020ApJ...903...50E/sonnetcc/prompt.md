# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...903...50E\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...903...50E",
 "title": "Super Star Clusters in the Central Starburst of NGC 4945",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "Emig, Kimberly L.",
 "n_authors": 15,
 "arxiv_id": "2009.05154",
 "doi": "10.3847/1538-4357/abb67d",
 "alma_projects_linked_by_archive": [
  "2016.1.01135.S",
  "2018.1.01236.S"
 ]
}
```

Paper text:
<paper>
# Super Star Clusters in the Central Starburst of NGC 4945

## Abstract

NGC 4945 is a nearby (3.8 Mpc) galaxy hosting a nuclear starburst and Seyfert Type 2 AGN. We use the Atacama Large Millimeter/submillimeter Array (ALMA) to image the 93 GHz (3.2 mm) free-free continuum and hydrogen recombination line emission (H40$\alpha$ and H42$\alpha$) at 2.2 pc (0.12$''$) resolution. Our observations reveal 27 bright, compact sources with FWHM sizes of 1.4–4.0 pc, which we identify as candidate super star clusters. Recombination line emission, tracing the ionizing photon rate of the candidate clusters, is detected in 15 sources, 6 of which have a significant synchrotron component to the 93 GHz continuum. Adopting an age of $\sim$5 Myr, the stellar masses implied by the ionizing photon luminosities are $\log_{10}$($M_{\star}$/M$_{\odot}$) $\approx$ 4.7–6.1. We fit a slope to the cluster mass distribution and find $\beta = -1.8 \pm 0.4$. The gas masses associated with these clusters, derived from the dust continuum at 350 GHz, are typically an order of magnitude lower than the stellar mass. These candidate clusters appear to have already converted a large fraction of their dense natal material into stars and, given their small free-fall times of $\sim$0.05 Myr, are surviving an early volatile phase. We identify a point-like source in 93 GHz continuum emission which is presumed to be the AGN. We do not detect recombination line emission from the AGN and place an upper limit on the ionizing photons which leak into the starburst region of $Q_0 < 10^{52}$ s$^{-1}$.

# Introduction

Many stars form in clustered environments (cite: Lada2003; Kruijssen2012). Bursts of star formation with high gas surface density produce massive ($>10^5$ M$_{\odot}$), compact (cite: Ryon2017) clusters, referred to as super star clusters. Super star clusters likely have high star-formation efficiencies . They may represent a dominant output of star-formation during the peak epoch of star-formation (cite: Madau2014). The process by which these massive clusters form now may also relate to the origin of globular clusters.

The earliest stages of cluster formation are the most volatile and currently, unconstrained . Characterizing properties of young ($<$10 Myr) clusters is a key step towards understanding their formation, identifying the dominant feedback processes at each stage of cluster evolution, determining which clusters survive as gravitationally bound objects, and linking all of these processes to the galactic environment.

While young clusters of mass $\sim$10$^4$ M$_{\odot}$ are found within our Galaxy (cite: Bressert2012; Longmore2014; Ginsburg2018a), the most massive, young clusters in the local universe are often found in starbursting regions and merging galaxies . Direct optical and even near-infrared observations of forming clusters are complicated by large amounts of extinction. Analyses of optically thin free-free emission and long wavelength hydrogen recombination lines of star clusters offer an alternative, extinction-free probe of the ionizing gas surrounding young star clusters . However, achieving a spatial resolution matched to the size of young clusters $\mathcal{O}$(1 pc) (cite: Ryon2017) in galaxies at the necessary frequencies and sensitivities has only recently become possible thanks to the Atacama Large Millimeter/submillimeter Array (ALMA).

We have recently analyzed forming super star clusters in the central starburst of the nearby (3.5 Mpc) galaxy NGC 253 at $\sim$2 pc resolution (cite: Leroy2018; Mills2020). NGC 4945 is the second object we target in a campaign to characterize massive star clusters in local starbursts with ALMA.

NGC 4945 is unique in that it is one of the closest galaxies (cite: Karachentsev2007) where a detected AGN and central starburst coexist. In the central $\sim$200 pc, the starburst dominates the infrared luminosity and ionizing radiation (cite: Spoon2000; Marconi2000), and an outflow of warm ionized gas has been observed (cite: Heckman1990; Moorwood1996; Mingozzi2019). Individual star clusters have not previously been observed in NGC 4945, due to the high extinction at visible and short IR wavelengths (cite: Spoon2000). Evidence for a Seyfert AGN comes from strong, variable X-ray emission, as NGC 4945 is one of the brightest sources in the X-ray sky and has a Compton thick column density of $3.8 \times 10^{24}$ cm$^{-2}$ (cite: Marchesi2018). A kinematic analysis of H$_2$O maser emission yields a black hole mass of $1.4 \times 10^6$ M$_{\odot}$ (cite: Greenhill1997).

In this article, we use ALMA to image the 93 GHz free-free continuum and hydrogen recombination line emission (H40$\alpha$ and H42$\alpha$) at 2.2 pc (0.12$''$) resolution. This emission allows us to probe photo-ionized gas on star cluster scales and thereby trace ionizing photon luminosities. We identify candidate star clusters and estimate properties relating to their size, ionizing photon luminosity, stellar mass, and gas mass.

Throughout this article, we plot spectra in velocity units with respect to a systemic velocity of $\mathrm{v_{sys}} = 580$ km s$^{-1}$ in the local standard of rest frame; estimates of the systemic velocity vary by $\pm 25$ km s$^{-1}$ (cite: Henkel2018; Chou2007; Roy2010). At the distance of 3.8 Mpc, 0.1$''$ corresponds to 1.84 pc.

# Observations

We used the ALMA Band 3 receivers to observe NGC 4945 as part of the project 2018.1.01236.S (PI: A. Leroy). We observed NGC 4945 with the main 12 m array telescopes in intermediate and extended configurations. Four spectral windows in Band 3 – centered at 86.2, 88.4, 98.4, and 100.1 GHz – capture the millimeter continuum primarily from free-free emission and cover the hydrogen recombination lines of principal quantum number (to the lower state) $\mathsf{n} = 40$ and $\mathsf{n} = 42$ from the $\alpha$ ($\Delta \mathsf{n} = 1$) transitions. The rest frequency of H$40\alpha$ is 99.0230 GHz and of H$42\alpha$ is 85.6884 GHz. In this article, we focus on the 93 GHz ($\lambda~\sim~3.2$ mm) continuum emission and the recombination line emission arising from compact sources in the starbursting region. We image the data from an 8 km extended configuration, which are sensitive to spatial scales of 0.07$''$–6$''$ (2–100 pc), in order to focus on the compact structures associated with candidate clusters. We analyze the observatory-provided calibrated visibilities using version 5.4.0 of the Common Astronomy Software Application (cite: McMullin2007).

When imaging the continuum, we flag channels with strong spectral lines. Then we create a continuum image using the full bandwidth of the line-free channels. We also make continuum images for each spectral window. For all images, we use Briggs weighting with a robust parameter of $r=0.5$.

When imaging the two spectral lines of interest, we first subtract the continuum in $uv$ space through a first order polynomial fit. Then, we image by applying a CLEAN mask (to all channels) derived from the full-bandwidth continuum image. Again, we use Briggs weighting with a robust parameter of $r=0.5$, which represents a good compromise between resolution and surface brightness sensitivity.

After imaging, we convolved the continuum and line images to convert from an elliptical to a round beam shape. For the full-bandwidth continuum image presented in this article, the fiducial frequency is $\nu = 93.2$ GHz and the final full-width half maximum (FWHM) beam size is $\theta = 0.12$$''$. The rms noise away from the source is $\approx$0.017 mJy beam$^{-1}$, equivalent to 0.2 K in Rayleigh-Jeans brightness temperature units. Before convolution to a round beam, the beam had a major and minor FWHM of 0.097$''$ $\times$ 0.071$''$.

For the H40$\alpha$ and H42$\alpha$ spectral cubes, the final FWHM beam size is 0.20$''$, convolved from 0.097$''$ $\times$ 0.072$''$ and from 0.11$''$ $\times$ 0.083$''$, respectively. The slightly lower resolution resulted in more sources with significantly detected line emission. We boxcar smoothed the spectral cubes from the native 0.488 MHz channel width to 2.93 MHz. The typical rms in the H40$\alpha$ cube is 0.50 mJy beam$^{-1}$ per 8.9 km s$^{-1}$ channel. The typical rms in the H42$\alpha$ cube is 0.48 mJy beam$^{-1}$ per 10.3 km s$^{-1}$ channel.

As part of the analysis, we compare the high resolution data with observations taken in a 1 km intermediate configuration as part of the same observing project. We use the continuum image provided by the observatory pipeline, which we convolve to have a circular beam FWHM of 0.7$''$; the rms noise in the full-bandwidth image is 0.15 mJy beam$^{-1}$. The spectral cubes have typical rms per channel of 0.24 mJy beam$^{-1}$ with the same channel widths as the extended configuration cubes. We do not jointly image the configurations because our main science goals are focused on compact, point-like objects. The extended configuration data on their own are well suited to study these objects and any spatial filtering of extended emission will not affect the analysis.

We compare the continuum emission at 3 mm with archival ALMA imaging of the $\nu = 350$ GHz ($\lambda \sim 850~\mu$m) continuum (project 2016.1.01135.S, PI: N. Nagar). At this frequency, dust emission dominates the continuum. We imaged the calibrated visibilities with a Briggs robust parameter of $r=-2$ (towards uniform weighting), up-weighting the extended baselines to produce a higher resolution image, suitable for comparison to our new Band 3 data. We then convolve the images to produce a circularized beam, resulting in a FWHM resolution of 0.12$''$ (from an initial beam size of 0.10$''$ $\times$ 0.064$''$), exactly matched to our 93 GHz continuum image. These data have an rms noise of 0.7 mJy beam$^{-1}$ (0.2 K).

We compare the ALMA data with Australian Long Baseline Array (LBA) imaging of $\nu = 2.3$ GHz continuum emission (cite: Lenc2009). At this frequency and resolution, the radio continuum is predominantly synchrotron emission. We use the Epoch 2 images (courtesy of E. Lenc) that have a native angular resolution slightly higher than the 3 mm ALMA data, with a beam FWHM of 0.080$''$ $\times$ 0.032$''$ and an rms noise of 0.082 mJy beam$^{-1}$.

# Continuum Emission

The whole disk of NGC 4945, as traced by *Spitzer* IRAC 8 $\mu$m emission (Program 40410, PI: G. Rieke), is shown in Figure [1](#fig:irac). The 8 $\mu$m emission predominantly arises from UV-heated polycyclic aromatic hydrocarbons (PAHs), thus tracing the interstellar medium and areas of active star formation. The square box indicates the 8$''$ $\times$ 8$''$ (150 pc $\times$ 150 pc) starburst region that is of interest in this article.

![](irafig_tmp2.png)

Figure [2](#fig:cont93) shows the 93 GHz ($\lambda \sim 3$ mm) continuum emission in the central starburst of NGC 4945. Our image reveals $\sim$30 peaks of compact, localized emission with peak flux densities 0.6–8 mJy (see Section [3.1](#sec:ps_id)). On average, the continuum emission from NGC 4945 at this frequency is dominated by thermal, free-free (bremsstrahlung) radiation (cite: Bendo2016). Free-free emission from bright, compact regions may trace photo-ionized gas in the immediate surroundings of massive stars. We take into consideration the point-like sources detected at 93 GHz as candidate massive star clusters, though some contamination by synchrotron-dominated supernova remnants or dusty protoclusters may still be possible. The morphology of the 93 GHz emission and clustering of the peaks indicate possible ridges of star formation and shells. The extended, faint negative bowls flanking the main disk likely reflect the short spacing data missing from this image. We do not expect that they affect our analysis of the point source-like cluster candidates.

![](cont93.pdf)

The large amount of extinction present in this high inclination central region (cite: Henkel2018) has previously impeded the direct observation of its star clusters. Paschen-$\alpha$ (Pa-$\alpha$) emission (cite: Marconi2000) of the $\mathsf{n} = 3$ hydrogen recombination line at 1.87 $\mu$m, shown in Figure [3](#fig:multifreq), reveals faint emission above and below the star-forming plane. Corrected for extinction, the clumps of ionized emission traced by Pa-$\alpha$ would give rise to free-free emission below our ALMA detection limit. Pa-$\alpha$ along with mid-infrared spectral lines give support for dust extinction of $A_{\mathrm{V}} > 160$ mag surrounding the AGN core and more generally $A_{\mathrm{V}} \gtrsim 36$ mag in the star-forming region (cite: Spoon2000).

A large fraction (18/29) of the 93 GHz sources coincide with peaks in dust emission at 350 GHz, as shown in Figure [3](#fig:multifreq). Overall there is a good correspondence between the two tracers. This indicates that candidate clusters are relatively young and may still harbor reservoirs of gas, though in Section [5.7](#sec:totalmass) we find that the fraction of the mass still in gas tends to be relatively small.

![image](source_locaps_r16SC4.pdf) ![image](contPa_93overlaysrc.pdf) ![image](cont350_hr_93overlaysrc.pdf) ![image](cont2_93overlaysrc.pdf)

In Figure [3](#fig:multifreq), the 93 GHz peaks without dust counterparts tend to be strong sources of emission at 2.3 GHz (cite: Lenc2009), a frequency where synchrotron emission typically dominates. As discussed in (cite: Lenc2009), the sources at this frequency are predominantly supernova remnants. The presence of 13 possible supernova remnants – four of which are resolved into shell-like structures with 1.1 to 2.1 pc in diameter – indicates that a burst of star-formation activity started at least a few Myr ago. (cite: Lenc2009) modeled SEDs of the sources spanning 2.3–23 GHz and found significant opacity at 2.3 GHz ($\tau = 5- 22$), implying the presence of dense, free-free plasma in the vicinity of the supernova remnants.

At 93 GHz, the very center of the starburst shows an elongated region of enhanced emission (about 20 pc in projected length, or $\sim$1$''$) that is also bright in 350 GHz emission. This region is connected to the areas of highest extinction. Higher column densities of ionized plasma are also present in the region; (cite: Lenc2009) observations reveal large free-free opacities at least up to 23 GHz. The brightest peak at 93 GHz, centered at $(\alpha, \delta)_{93} = (13\mathrm{h}\, 05\mathrm{m}\, 27.4798 \mathrm{s} \pm 0.004 \mathrm{s}, -49^{\circ}\, 28\ensuremath{'}\, 05.404\ensuremath{''} \pm 0.06\ensuremath{''})$, is co-located with the kinematic center as determined from H$_{2}$O maser observations $(\alpha, \delta)_{\mathrm{H_{2}O}} = (13\mathrm{h}\, 05\mathrm{m}\, 27.279\mathrm{s} \pm 0.02\mathrm{s}, -49^{\circ}\, 28\ensuremath{'}\, 04.44\ensuremath{''} \pm 0.1\ensuremath{''})$ (cite: Greenhill1997) and presumably harbors the AGN core. We refer to the elongated region of enhanced emission surrounding the AGN core as the circumnuclear disk. The morphological similarities between 93 GHz and 350 GHz, together with the detection of a synchrotron point source (likely supernova remnant; see Section [3.2](#sec:fluxextract) and Source 17) in the circumnuclear disk, indicate star-formation is likely present there.

## Point Source Identification

We identify candidate star clusters via point-like sources in the 93 GHz continuum image. Sources are found using `PyBDSF` (cite: Mohan2015) in the following way. Islands are defined as contiguous pixels above a threshold of seven times the global rms value of $\sigma \approx 0.017$ mJy beam$^{-1}$. Within each island, multiple Gaussians may be fit, each with a peak amplitude greater than the peak threshold, a threshold of ten times the global rms. We chose this peak threshold to ensure that significant emission can also be identified in the continuum images made from individual spectral windows. The number of Gaussians is determined from the number of distinct peaks of emission higher than the peak threshold and which have a negative gradient in all eight evaluated directions. Starting with the brightest peak, Gaussians are fit and cleaned (i.e., subtracted). A source is identified with a Gaussian as long as subtracting its fit does not increase the island rms.

Applying this algorithm to our 93 GHz image yielded $50$ Gaussian sources. We remove $5$ sources that fall outside of the star-forming region. We also removed $3$ sources that appeared blended, with an offset $<0.12$$''$ from another source. Finally we remove $13$ sources that do not have a flux density above ten times the global rms after extracting the 93 GHz continuum flux density through aperture photometry (see Section [3.2](#sec:fluxextract)). As a result, we analyze 29 sources as candidate star clusters. In Figure [3](#fig:multifreq), we show the location of each source with the apertures used for flux extraction. The sources match well with what we would identify by eye.

## Point Source Flux Extraction

For each source, we extract the continuum flux density at 2.3 GHz, 93 GHz, and 350 GHz through aperture photometry. Before extracting the continuum flux at 2.3 GHz, we convolve the image to the common resolution of 0.12$''$. We extract the flux density at the location of the peak source within an aperture diameter of 0.24$''$. Then we subtract the extended background continuum that is local to the source by taking the median flux density within an annulus of inner diameter 0.24$''$ and outer diameter 0.30$''$; using the median suppresses the influence of nearby peaks and the bright surrounding filamentary features. The flux density of each source at each frequency is listed in Table [\[tab:continuum\]](#tab:continuum). When the extracted flux density within an aperture is less than three times the global rms noise , we assign a three sigma upper limit to that flux measurement.

In Figure [4](#fig:fluxcomp), we plot the ratio of the flux densities extracted at 350 GHz and 93 GHz (S$_{350}$/S$_{93}$) against the ratio of the flux densities extracted at 2.3 GHz and 93 GHz (S$_{2.3}$/S$_{93}$). Synchrotron dominated sources, which fall to the bottom right of the plot, separate from the free-free (and dust) dominated sources, which lie in the middle of the plot. One exception is the AGN (Source 18) which, due to self-absorption at frequencies greater than 23 GHz, is bright at 93 GHz but not at 2.3 GHz and therefore has the lowest S$_{2.3}$/S$_{93}$ ratio.

From the continuum measurements we construct simple SEDs for each source. Examples of the SEDs of three sources are included in Figure [5](#fig:SED). We show an example of a free-free dominated source (Source 22), which represents the majority of sources, as well as a dust (Source 12) and a synchrotron (Source 14) dominated source. Of the sources nine also have the free-free absorption of their synchrotron spectrum modeled. We this information whenever possible. When a source identified by (cite: Lenc2009) lies within 0.06$''$ (half the beam FWHM) of the 93 GHz source, we associate the low-frequency modeling with the 93 GHz source. We take the model fit by (cite: Lenc2009) and normalize it to the 2.3 GHz flux that we extract as an example, see the solid purple curve in the middle panel of Figure [5](#fig:SED). The SEDs of all sources are shown in Figure [13](#fig:ap_sed) in Appendix [10](#ap:sed).

l r r R R R R R R R Source & RA & Dec & $S_{93}$ & $\alpha_{93}$ & $S_{2.3}$ $^{a}$ & $S_{350}$ $^{b}$ & $f_{\mathrm{ff}}$ & $f_{\mathrm{syn}}$ $^c$ & $f_{\mathrm{d}}$ $^c$\
& & & (mJy) & & (mJy) & (mJy) & & &\
& 13:05:27.761 & $-$49:28:02.83 & 1.28 & -0.80 & 2.3 & ... & 0.51 & 0.49 & ...\
02 & 13:05:27.755 & $-$49:28:01.97 & 1.01 & 0.80 & ... & 26.6 & 0.78 & ... & 0.22\
03 & 13:05:27.724 & $-$49:28:02.64 & 0.82 & -0.27 & ... & 14.8 & 0.89 & 0.11 & ...\
04 & 13:05:27.662 & $-$49:28:03.85 & 0.95 & -1.12 & ... & 16.0 & 0.27 & 0.73 & ...\
05 & 13:05:27.630 & $-$49:28:03.76 & 0.77 & -1.57 & ... & ... & 0.00 & 1.00 & ...\
06 & 13:05:27.612 & $-$49:28:03.35 & 1.73 & -1.11 & 7.1 & ... & 0.28 & 0.72 & ...\
07 & 13:05:27.602 & $-$49:28:03.15 & 0.98 & -0.61 & ... & 15.5 & 0.65 & 0.35 & ...\
08 & 13:05:27.590 & $-$49:28:03.44 & 1.89 & -0.40 & ... & 14.9 & 0.80 & 0.20 & ...\
09 & 13:05:27.571 & $-$49:28:03.78 & 1.76 & -1.01 & 12.2 & ... & 0.36 & 0.64 & ...\
10 & 13:05:27.558 & $-$49:28:04.77 & 2.41 & -1.10 & 9.5 & ... & 0.29 & 0.71 & ...\
11 & 13:05:27.557 & $-$49:28:03.60 & 0.76 & -0.59 & ... & 13.9 & 0.66 & 0.34 & ...\
12 & 13:05:27.540 & $-$49:28:03.99 & 1.28 & 1.47 & ... & 37.4 & 0.62 & ... & 0.38\
13 & 13:05:27.530 & $-$49:28:04.27 & 1.78 & -0.22 & ... & 20.8 & 0.93 & 0.07 & ...\
14 & 13:05:27.528 & $-$49:28:04.63 & 3.06 & -1.22 & 14.3 & 11.2 & 0.20 & 0.80 & ...\
15 & 13:05:27.522 & $-$49:28:05.80 & 0.83 & -0.71 & ... & ... & 0.57 & 0.42 & ...\
16 & 13:05:27.503 & $-$49:28:04.08 & 0.98 & 1.34 & ... & 23.9 & 0.65 & ... & 0.35\
17 & 13:05:27.493 & $-$49:28:05.10 & 3.69 & -0.61 & 5.3 & 47.1 & 0.65 & 0.35 & ...\
18 & 13:05:27.480 & $-$49:28:05.40 & 9.74 & -0.85 & ... & 39.0 & 0.47 & 0.53 & ...\
19 & 13:05:27.464 & $-$49:28:06.55 & 1.30 & -1.36 & 7.8 & ... & 0.10 & 0.90 & ...\
20 & 13:05:27.457 & $-$49:28:05.76 & 2.51 & -0.88 & ... & 22.4 & 0.45 & 0.55 & ...\
21 & 13:05:27.366 & $-$49:28:06.92 & 1.19 & -1.38 & 4.7 & ... & 0.09 & 0.91 & ...\
22 & 13:05:27.358 & $-$49:28:06.07 & 2.57 & -0.19 & ... & 34.8 & 0.95 & 0.05 & ...\
23 & 13:05:27.345 & $-$49:28:07.44 & 0.95 & -0.28 & ... & 9.7 & 0.88 & 0.12 & ...\
24 & 13:05:27.291 & $-$49:28:07.10 & 0.90 & -1.22 & 3.2 & ... & 0.20 & 0.80 & ...\
25 & 13:05:27.288 & $-$49:28:06.56 & 0.91 & -0.27 & 2.1 & 15.2 & 0.89 & 0.11 & ...\
26 & 13:05:27.285 & $-$49:28:06.72 & 1.13 & -0.33 & 1.4 & 18.5 & 0.85 & 0.15 & ...\
27 & 13:05:27.269 & $-$49:28:06.60 & 2.75 & -1.08 & 31.2 & ... & 0.30 & 0.70 & ...\
28 & 13:05:27.242 & $-$49:28:08.43 & 0.80 & -0.54 & ... & ... & 0.70 & 0.30 & ...\
29 & 13:05:27.198 & $-$49:28:08.22 & 1.43 & -0.29 & ... & 12.6 & 0.88 & 0.12 & ...

Table notes: RA and Dec refer to the center location of a Gaussian source identified in the 93 GHz continuum image, in units of hour angle and degrees, respectively. $S_{93}$ is the flux density in the 93 GHz full bandwidth continuum image. $\alpha_{93}$ is the spectral index at 93 GHz ($S\propto \nu^{\alpha}$), as determined from the best fit slope to the 85–101 GHz continuum emission. $S_{2.3}$ is the flux density extracted in the 2.3 GHz continuum image. $S_{350}$ is the flux density extracted in the 350 GHz continuum image. $f_{\mathrm{ff}}$, $f_{\mathrm{syn}}$, $f_{\mathrm{d}}$ are the free-free, synchrotron, and dust fractional contribution to the 93 GHz continuum emission, respectively, as determined from the spectral index. See Section [3.3](#sec:freefreefrac) for a description of how the errors on these fractional estimates are determined.\
$^a$ A 3$\sigma$ upper limit to the sources undetected in 2.3 GHz continuum emission is 1.2 mJy.\
$^b$ The error on the 350 GHz flux density measurement is 3.2 mJy. A 3$\sigma$ upper limit to the undetected sources is 9.6 mJy.\
$^c$ The error on the fractional contributions are the same as for $f_{\mathrm{ff}}$ unless otherwise noted.

![](flux_comp_indexcontrib2.pdf)

![](SEDs_r16SC4.pdf)

## Free-free Fraction at 93 GHz

The flux density of optically thin, free-free emission at millimeter wavelengths (cite: Draine2011) arises as $$\begin{equation}
    \begin{split}
    S_{\mathrm{ff}} = & (2.08~\mathrm{mJy} ) 
    \left( \frac{ n_e n_+ V }{ 5\times10^8~\mathrm{cm^{-6}~pc^3} } \right) \times \\
    & \left(  \frac{T_e}{ 10^4~\mathrm{K}} \right)^{-0.32} 
    \left( \frac{\nu}{ 100~\mathrm{GHz} } \right)^{-0.12}
    \left( \frac{ D }{ 3.8~\mathrm{Mpc} } \right)^{-2}
    \label{eq:Scont}
    \end{split}
\end{equation}$$ where $EM_{\mathrm{C}} = n_e n_+ V$ is the volumetric emission measure of the ionized gas, $D$ is the distance to the source, and $T_e$ is the electron temperature of the medium. Properties of massive star clusters (i.e., ionizing photon rate) can thus be derived through an accurate measurement of the free-free flux density and an inference of the volumetric emission measure. We will determine a free-free fraction, $f_{\mathrm{ff}}$, and let $S_{\mathrm{ff}} = f_{\mathrm{ff}} S_{93}$.

In this section we focus on determining the portion of free-free emission that is present in the candidate stars clusters at 93 GHz. To do this, we need to estimate and remove contributions from synchrotron emission and dust continuum. We determine an in-band spectral index across the 15 GHz bandwidth of the ALMA Band 3 observations. Using the spectral index[^1], we constrain the free-free fraction as well as the fractional contributions of synchrotron and dust (see Figure [4](#fig:fluxcomp) and Table [\[tab:continuum\]](#tab:continuum)). We found the in-band index because of the two decades difference in frequency coupled with the large optical depths already present at 2.3 GHz.

### Band 3 Spectral Index

We estimate an in-band spectral index at 93 GHz, $\alpha_{93}$, from a fit to the flux densities in the spectral window continuum images of the ALMA Band 3 data. The spectral windows span 15 GHz, which we set up to have a large fractional bandwidth. We extract the continuum flux density of each source in each spectral window using aperture photometry with the same aperture sizes as described in Section [3.2](#sec:fluxextract). We fit a first order polynomial to the five continuum measurements – four from each spectral window, one from the full bandwidth image. The fit to the in-band spectral index is listed in Table [\[tab:continuum\]](#tab:continuum) with the one sigma uncertainty to the fit. The median uncertainty of the spectral indices is 0.13. The spectral indices measured in this way were consistent for the brightest sources with the index determined by `CASA tclean`; however, we found our method to be more reliable for the fainter sources. Nonetheless, the errors are large for faint sources.

### Decomposing the fractional contributions of emission type

From the in-band spectral index fit, we estimate the fractional contribution of each emission mechanism — free-free, synchrotron, and (thermal) dust — to the 93 GHz continuum. To do this, we simulate how mixtures of synchrotron, free-free, and dust emission could combine to create the observed in-band index.

### Estimated free-free, synchrotron, and dust fractions to the 93 GHz continuum

Table [\[tab:continuum\]](#tab:continuum) and Figure [4](#fig:fluxcomp) summarize our estimated fractional contribution of each emission mechanism to the 93 GHz continuum of each source. We find, at this 0.12$''$ resolution, the median free-free fraction of sources is $f_{\mathrm{ff}} = 0.62$ . Most of the spectral indices are negative, and as a result, we find synchrotron emission can have a non-trivial contribution with a median fraction of $f_{\mathrm{syn}} = 0.36$ . On the other hand, three of the measured spectral indices are positive. $1\sigma$ limit on the fractional contribution of dust does not exceed $f_{\mathrm{d}} = 0.47$ for any source.

Additional continuum observations of comparable resolution at frequencies between 2 GHz and 350 GHz would improve the estimates of the fractional contribution of free-free, dust and synchrotron to the 93 GHz emission.

# Recombination Line Emission

Hydrogen recombination lines at these frequencies trace ionizing radiation ($E >13.6$ eV); this recombination line emission is unaffected by dust extinction. The integrated emission from a radio recombination line transition to quantum number $\mathsf{n}$, which we derive for millimeter wavelength transitions in Appendix [8.1](#ap:line), is described by $$\begin{equation}
    \begin{split}
    \int S_{{\mathsf{n}}}~\mathrm{dv} =  
    & \left( 65.13~\mathrm{mJy~km~s^{-1}}\right) \times \\
    & b_{\mathsf{n+1}} 
    \left( \frac{n_e n_p V }{ 5\times10^8~\mathrm{cm^{-6}~pc^3} }\right)
    \left( \frac{ D }{ 3.8~\mathrm{Mpc} }\right)^{-2} \times \\
    & \left( \frac{ T_e }{ 10^4~\mathrm{K} } \right)^{-1.5} 
    \left( \frac{\nu}{100~\mathrm{GHz}} \right)
    \label{eq:Sline}
    \end{split}
\end{equation}$$ where $b_{\mathsf{n+1}}$ is the LTE departure coefficient, $EM_{\mathrm{L}} = n_e n_p V$ is the volumetric emission measure of ionized hydrogen, $D$ is the distance to the source, $T_e$ is the electron temperature of the ionized gas, and $\nu$ is the rest frequency of the spectral line.

Figure [6](#fig:spectra) shows spectra of the 15 sources with detected radio recombination line emission. We extract H40$\alpha$ and H42$\alpha$ spectra at the location of each source with an aperture diameter of 0.4$''$, or twice the beam FWHM. We average the spectra of the two transitions together to enhance the signal-to-noise ratio of the recombination line emission. To synthesize an effective H41$\alpha$ profile, we interpolate the two spectra of each source to a fixed velocity grid with a channel width of 10.3 km s$^{-1}$, weight each spectrum by $\sigma_{\mathrm{rms}}^{-2}$ where $\sigma_{\mathrm{rms}}$ is the spectrum standard deviation, and average the spectra together lowering the final noise. The averaged spectrum has an effective transition of H41$\alpha$ at $\nu_{\mathrm{eff}} = 92.034$ GHz.

![](specrta_2trans_r16SC4.pdf)

We fit spectral features with a Gaussian profile. We calculate an integrated signal-to-noise ratio for each line by integrating the spectrum across the Gaussian width of the fit (i.e., $\pm \sigma_{\mathrm{Gaus}}$) and then dividing by the noise over the same region, $\sqrt{N} \sigma_{\mathrm{rms}}$, where $N$ is the number of channels covered by the region. We report on detections with an integrated signal of $>5\sigma_{\mathrm{rms}}$. Table [\[tab:line\]](#tab:line) summarizes the properties of the line profiles derived from the best-fit Gaussian. The median rms of the spectra is $\sigma_{\mathrm{rms}} = 0.34$ mJy.

c C C C C Source & V$_{cen}$ & Peak & FWHM & $\sigma_{\mathrm{rms}}$\
& (km s$^{-1}$) & (mJy) & (km s$^{-1}$) & (mJy)\
& 131.6 & 0.69 & 105.2 & 0.35\
03 & 117.4 & 1.26 & 37.2 & 0.36\
04 & 107.5 & 1.28 & 42.9 & 0.36\
06 & 79.4 & 1.33 & 31.1 & 0.33\
07 & 77.2 & 1.46 & 28.1 & 0.36\
08 & 87.5 & 2.24 & 38.7 & 0.33\
12 & 53.6 & 1.72 & 55.9 & 0.39\
13 & 45.7 & 2.68 & 34.8 & 0.31\
14 & 111.8 & 0.82 & 163.1 & 0.33\
15 & 5.6 & 1.62 & 28.2 & 0.37\
21 & -140.7 & 0.99 & 113.3 & 0.34\
22 & -80.6 & 1.61 & 58.4 & 0.34\
25 & -102.3 & 1.42 & 39.0 & 0.32\
26 & -107.6 & 1.86 & 30.9 & 0.33\
27 & -102.3 & 2.02 & 23.6 & 0.28

Table notes: V$_{\mathrm{cen}}$ is the central velocity of the best fit Gaussian. Peak is the peak amplitude of the Gaussian fit. FWHM is the full-width half maximum of the Gaussian fit. $\sigma_{\mathrm{rms}}$ is the standard deviation of the fit-subtracted spectrum.

In Figure [12](#fig:ap_allspec) of Appendix [9](#ap:spec), we show that the central velocities of our detected recombination lines are in good agreement with the kinematic velocity expected of the disk rotation. To do this, we overlay our spectra on H40$\alpha$ spectra extracted from the intermediate configuration observations (0.7$''$ resolution).

In sources, we detect relatively narrow features of $\mathrm{FWHM} \sim (24 - 58)$ km s$^{-1}$. Larger line-widths of $\mathrm{FWHM} \sim (105 - 163)$ km s$^{-1}$ are observed from bright sources which also have high synchrotron fractions, indicating that multiple components, unresolved motions (e.g., from expanding shells or galactic rotation), or additional turbulence may be present. Six sources with detected recombination line emission have considerable ($f_{\mathrm{syn}} \gtrsim 0.50$) synchrotron emission (i.e. Sources 1, 4, 6, 14, 21, 27) at 93 GHz.

In the top panel of Figure [7](#fig:totalspec), we show the total recombination line emission extracted from the starburst region in the 0.2$''$ resolution, “extended” configuration observations. The aperture we use, designated as region T1, is shown in Figure [8](#fig:totalap). Details of the aperture selection are described in Section [4.1.1](#sec:intermedtot). The spectrum consists of two peaks reminiscent of a double horn profile representing a rotating ring. We fit the spectrum using the sum of two Gaussian components. In Table [\[tab:totalline\]](#tab:totalline), we include the properties of the best fit line profiles. The sum total area of the fits is ($2.1\pm0.6$) Jy km s$^{-1}$.

![](spec_totalreg.pdf)

c c C C C C C C C Region & Config & v$_{\mathrm{cen},1}$ & Peak$_1$ & FWHM$_1$ & v$_{\mathrm{cen},2}$ & Peak$_2$ & FWHM$_2$ & H40$\alpha$ flux\
& & (km s$^{-1}$) & (mJy) & (km s$^{-1}$) & (km s$^{-1}$) & (mJy) & (km s$^{-1}$) & (mJy km s$^{-1}$)\
T1 & extend & -139 & 9.7 & 78 & 91 & 8.9 & 138 & 2100\
T1 & intermed & -117 & 16 & 99 & 66 & 16 & 186 & 4800\
T2 & intermed & -114 & 19 & 113 & 86 & 23 & 167 & 6400

## Line Emission from 0.7 $''$ resolution, Intermediate-configuration Observations

Figure [7](#fig:totalspec) also shows integrated spectra derived from intermediate-resolution (0.7$''$) data. We use these data as a tracer of the total ionizing photons of the starburst region. We expect that the intermediate-resolution data includes emission from both discrete, point-like sources and diffuse emission from any smooth component.

The total integrated emission in the intermediate-configuration data is about three times larger than the integrated emission in the extended-configuration data. Spectra representing the total integrated line flux are shown in Figure [7](#fig:totalspec). In Figure [8](#fig:totalap), we show the integrated intensity map of H40$\alpha$ emission from the intermediate-configuration (0.7$''$) data. In Table [\[tab:totalline\]](#tab:totalline), we include the best fit line profiles.

We also compare the line profiles of H40$\alpha$ and H42$\alpha$ in the intermediate-configuration (0.7$''$) data, see Table [\[tab:intermedline\]](#tab:intermedline) and Figures [9](#fig:B16ap) & [10](#fig:B16spec). We find that the integrated line emission of H42$\alpha$ is enhanced compared with H40$\alpha$, reaching a factor of 2 greater when integrated over the entire starburst region. Yet we see good agreement between the two lines at the scale of individual cluster candidates. Spectral lines (possibly arising from $c$-C$_3$H$_2$) likely contaminate the H42$\alpha$ line flux in broad, typically spatially unresolved, line profiles.

### Total Emission from the Starburst Region

In Figure [8](#fig:totalap) we show the integrated intensity map of H40$\alpha$ emission integrated between $\mathrm{v_{systemic}} \pm 170$ km s$^{-1}$, as calculated from the 0.7$''$ intermediate-configuration data. Diffuse emission is detected throughout the starburst region and up to 30 pc in apparent size beyond the region where we detect the bright point sources at high resolution.

![](lowres_mom0rrl_H40a_positions2.pdf)

Also shown in Figure [8](#fig:totalap) are the apertures used to extract spectra in Figure [7](#fig:totalspec). We fit a two dimensional Gaussian to the continuum emission in the 0.7$''$ resolution observations (see Figure [9](#fig:B16ap)). This results in a best fit centered at $(\alpha, \delta) = (13\mathrm{h}\, 05\mathrm{m}\, 27.4896\mathrm{s}, -49^{\circ}\, 28\ensuremath{'}\, 05.159\ensuremath{''})$, with major and minor Gaussian widths of $\sigma_{\mathrm{maj}} = 2.4$$''$ and $\sigma_{\mathrm{min}} = 0.58$$''$, and an angle of $\theta = 49.5^{\circ}$; we use this fit as a template for the aperture location, position angle, width and height. We independently vary the major and minor axes (in multiples of $0.5\sigma_{\mathrm{maj}}$ and $0.5\sigma_{\mathrm{min}}$, respectively) in order to determine the aperture which maximizes the total integrated signal in channels within $\pm 170$ km s$^{-1}$. With the extended-configuration cube, we find the largest integrated line emission with an aperture of 8.4$''$ $\times$ 1.5$''$, which we refer to as T1. With the intermediate-configuration cube, the largest integrated line emission arises with an aperture of 12.0$''$ $\times$ 2.9$''$, which we refer to as T2.

We extract the total H40$\alpha$ line flux from the intermediate-configuration (0.7$''$ resolution) cube using the T2 aperture (see bottom panel of Figure [7](#fig:totalspec)). The spectrum shows a double horn profile, indicating ordered disk-like rotation. We fit the features with two Gaussians. The sum total of their integrated line flux is ($6.4 \pm 1.0$) Jy km s$^{-1}$.

We also extract H40$\alpha$ line flux from the intermediate-configuration (0.7$''$ resolution) cube within the T1 aperture in order to directly compare the integrated line flux in the two different data sets using the same aperture regions. We find more emission in the intermediate-configuration data, a factor of $\sim$2.3 greater than the extended-configuration data. This indicates that some recombination line emission originates on large scales ($>$100 pc) to which the high-resolution, long baselines are not sensitive.

### H42$\alpha$ Contamination

In this section we compare the line profiles from H40$\alpha$ and H42$\alpha$ extracted from the 0.7$''$ intermediate configuration data. In principle, we expect the spectra to be virtually identical, which is why we average them to improve the signal-to-noise at high-resolution. Here we test that assumption . To summarize, we find evidence that a spectral line may contaminate the H42$\alpha$ measured line flux in broad (typically spatially unresolved) line profiles. Yet we see good agreement between the two lines at the scale of individual cluster candidates.

We extracted spectra in three apertures to demonstrate the constant velocity offset of the contaminants. We approximately matched the locations of these apertures to those defined in (cite: Bendo2016), in which H42$\alpha$ was analyzed at 2.3$''$ resolution; in this way we are able to confirm the flux and line profiles we extract at 0.7$''$ resolution with those at 2.3$''$. The non-overlapping circular apertures with diameters of 4$''$ designated as North (N), Center (C), and South (S) are shown in Figure [9](#fig:B16ap).

![](cont93_intermed_linear.pdf)

![](intspec_bendoreg2.pdf)

We used our intermediate-configuration data to extract an H40$\alpha$ and an H42$\alpha$ spectrum in each of the regions. We overplot the spectra of each region in Figure [10](#fig:B16spec). The total area of the fits are presented in Table [\[tab:intermedline\]](#tab:intermedline) as the integrated line flux.

Our line profiles of H42$\alpha$ are similar in shape and velocity structure as those analyzed in (cite: Bendo2016) and the integrated line emission is also consistent (within 2$\sigma$). This indicates that we are recovering the H42$\alpha$ total line flux and properties with our data.

On the other hand, the H40$\alpha$ flux we extract is about a factor of $\sim$1.6 lower than the H42$\alpha$ fluxes in these apertures (see Figure [10](#fig:B16spec) and Table [\[tab:intermedline\]](#tab:intermedline)). The discrepancy grows to a factor of 2 in the profile extracted from the total region.

c C C C Region & H42$\alpha$ flux & H40$\alpha$ flux & Ratio H42$\alpha$/H40$\alpha$\
& (Jy km s$^{-1}$) & (Jy km s$^{-1}$) &\
N & 2.1 & 1.5 & 1.4\
C & 5.9 & 3.7 & 1.6\
S & 1.9 & 0.96 & 2.0

The additional emission seen in the H42$\alpha$ spectrum at velocities +100 km s$^{-1}$ to +250 km s$^{-1}$ with respect to the bright, presumably hydrogen recombination line peak, is absent in the H40$\alpha$ profile. It is not likely to be a maser-like component of hydrogen recombination emission since the relative flux does not greatly vary in different extraction regions, and densities outside of the circumnuclear disk would not approach the emission measures necessary (e.g., $EM_v \gtrsim 10^{10}$ cm$^{-6}$ pc$^3$) for stimulated line emission.

We searched for spectral lines in the frequency range $\nu_{\mathrm{rest}} \sim 85.617$ – 85.660 GHz, corresponding to these velocities and find several plausible candidates, though we were not able to confirm any species with additional transitions in the frequency coverage of these observations. A likely candidate may be the $4_{32} - 4_{23}$ transition of $c$-C$_3$H$_2$. $c$-C$_3$H$_2$ has a widespread presence in the diffuse ISM of the Galaxy (cite: Lucas2000) and the $2_{20} - 2_{11}$ transition has been detected in NGC 4945 (cite: Eisner2019). As an example we plot the velocity of $c$-C$_3$H$_2$ $4_{32} - 4_{23}$ relative to H42$\alpha$ in Figure [10](#fig:B16spec).

# Physical Properties of the Candidate Star Clusters

In this section, we estimate properties of the candidate star clusters, summarized in Table [\[tab:props\]](#tab:props). We discuss their size and approximate age. Properties of the ionized gas content, such as temperature (see Table [\[tab:temp\]](#tab:temp)), metallicity, density and mass are derived from the continuum and recombination line emission. We estimate the ionizing photon rate of the candidate stars clusters and use it to infer the stellar mass (see Figure [11](#fig:cmf)). From the dust emission at 350 GHz, we estimate gas masses of the candidate star clusters. With a combined total mass from gas and stars, we estimate current mass surface densities and free-fall times.

We exclude Source 5 from the analysis since the free-free fraction is $f_{\mathrm{ff}} < 0.01$. We also remove the presumed AGN core (Source 18) from the analysis.

## Size

The sources identified through `PyBDSF` in the 93 GHz continuum image are fit with two dimensional Gaussians. The average of the major and minor (convolved) FWHM is listed in Table [\[tab:props\]](#tab:props) as the FWHM size of the source in units of pc. The Gaussian fits are all consistent with circular profiles within error. FWHM sizes of (1.4–4.0) pc are observed, consistent with typical sizes of young, massive star clusters (cite: Ryon2017; Leroy2018). However, the lower end may reflect the resolution limit of our beam, with a FWHM size of 2.2 pc. The uncertainties we report reflect the errors of the Gaussian fit.

Based on high-resolution imaging of embedded clusters in the nucleus of the Milky Way and NGC 253, some of these clusters might break apart at higher resolution (cite: Ginsburg2018a). If they follow the same pattern seen in these other galaxies, each source would have one or two main components potentially with several associated fainter components.

## Age

Throughout our analysis, we assume that the candidate star clusters formed in an instantaneous burst of star-formation roughly 5 Myr ago (with a likely uncertainty of $\sim$1 Myr). This (approximately uniform) age is supported through the coincident detection of RRLs and supernovae remnants, previous analyses of the global population of the burst (cite: Marconi2000; Spoon2000) and an orbital timescale of $\approx$3 Myr for the starburst region. We elaborate on this supporting evidence below.

As we discuss in Section [3.3](#sec:freefreefrac), dust does not significantly contribute to 93 GHz emission , but synchrotron emission does through supernova remnants. Supernova explosions begin from $\sim$3 Myr in the lifetime of a cluster and cease around $\sim$40 Myr when the most massive stars have died out; this puts the loosest bounds on the age of the candidate clusters we observe. The coincident detection of supernovae remnants in a third (6/15) of our recombination line detected sources implies that the burst is likely not at the earliest stage of the supernovae phase. However the ionizing photon rate changes dramatically over 3 Myr to 10 Myr, dropping by about two orders of magnitude (cite: Leitherer1999). As a result clusters are significantly harder to detect in radio recombination lines or free-free continuum emission after $\sim$5 Myr.

Properties of star-forming activity in the central starburst have been estimated by combining far-infrared (FIR) and optical/IR tracers. (cite: Marconi2000) discerned an age of 6 Myr and mass of $4\times 10^{7}$ M$_{\odot}$ by using Pa$\alpha$ and Br$\gamma$ to trace the energy distribution of the photon output of the population. However, the dust extinction was underestimated, complicated by the uncertainty in the AGN contribution. Mid-infrared (MIR) observations with the Infrared Space Observatory (cite: Kessler1996) of line ratios further constrained this scenario. (cite: Spoon2000) estimated an extinction of $A_{\mathrm{V}} = 36^{+18}_{-11}$, determined that the AGN is not dominating the ionizing radiation field, and found that the star-forming population is consistent with a burst of age $\geq$5 Myr.

As a sanity check on whether a synchronized burst might be expected, we calculate the orbital timescale associated with the the burst region. Taking the rotation velocity $\sim 170$ km s$^{-1}$ from the integrated spectrum and the radius $\sim 80$ pc associated with region T1, we estimate an orbital timescale of $\sim 3$ Myr. If we take this as roughly the timescale for the nuclear disk to react to changing conditions, a burst shutting off or turning on in a $\sim 5$ Myr timescale is reasonable.

## Temperature and Metallicity

The ratio of the integrated recombination line flux (Equation [\[eq:Sline\]](#eq:Sline)) to the free-free continuum flux density (Equation [\[eq:Scont\]](#eq:Scont)) allows the electron temperature to be determined. Dependencies on the distance, emission measure, and (possible) beam-filling effects cancel out under the assumption that the two tracers arise in the same volume of gas. We show in Appendix [8.3.1](#ap:temp), that when taking the ratio of the integrated line to continuum, $R_{\mathrm{LC}}$, and solving for the temperature, $T_e$, we arrive at $$\begin{equation}
\begin{split}
T_e = 10^4~\mathrm{K}
    \left[ b_{\mathsf{n+1}} \left( 1 + y \right)^{-1} 
    \left( \frac{ R_{\mathrm{LC}} }{ 31.31~\mathrm{km~s^{-1}} } \right)^{-1} \right. \times \\
    \left. \left( \frac{\nu}{100~\mathrm{GHz}} \right)^{1.12} \right]^{0.85}
\label{eq:temp}
\end{split}
\end{equation}$$ where $b_{\mathsf{n+1}}$ is the non-LTE departure coefficient, and $y$ is the abundance ratio of ionized helium to hydrogen number density, $y= n_{He+} / n_p$, which we fix as $y = 0.10$ (cite: DePree1996; Mills2020).

Table [\[tab:temp\]](#tab:temp) lists the temperatures we derive in the region. We focus on the 5 sources with bright (peak S/N $>4.7\sigma$) and well-fit recombination line emission. To derive the temperatures, we re-evaluate the continuum (fraction of) free-free emission at the resolution of 0.2$''$, since the free-free fraction may change with resolution. Therefore, we convolve the Band 3 continuum images to 0.2$''$ resolution. We extract the continuum from the full-bandwidth image through aperture photometry, using an aperture diameter of 0.4$''$. In order to exactly match the processing of the spectral line data, we do not subtract background emission within an outer annulus. Then, by extracting the continuum in each spectral window (using the same aperture diameters just described), we fit for the in-band spectral index. We use the procedure described in Section [3.3](#sec:freefreefrac) to constrain the free-free fraction from the spectral index fit.

c C C C C C Source & $\int S_{\mathrm{L}}\,\mathrm{dV}$ & $S_{93}$ & $f_{\mathrm{ff}}$ & $T_e$\
& (mJy km s$^{-1}$) & (mJy) & & (K)\
& 92 & 3.5 & 0.74 & 6000\
13 & 99 & 2.9 & 0.91 & 5600\
22 & 100 & 3.4 & 0.78 & 5600\
26 & 61 & 2.6 & 0.72 & 6400\
27 & 50 & 3.6 & 0.45 & 6500

Table notes: $\int S_{\mathrm{L}}\,\mathrm{dV}$ refers to the integrated line emission. $S_{93}$ is the continuum flux density extracted at 93 GHz in the 0.2$''$ resolution image. $f_{\mathrm{ff}}$ is the estimated free-free fraction at 0.2$''$ resolution. $T_e$ is the electron temperature derived using Equation [\[eq:temp\]](#eq:temp).

With the free-free fraction and measured fluxes, we plug in the line to continuum ratio into Equation [\[eq:temp\]](#eq:temp) and take $b_{\mathsf{n}} = 0.73$ (cite: Storey1995) to arrive at the temperature. The departure coefficient at $\mathsf{n} = 41$ is loosely ($<15$% variation) dependent on the temperature. We iterate (once) on the input $b_{\mathsf{n}}$ and output temperature. $b_{\mathsf{n}} = 0.73$ is the modeled value for this temperature and for typical densities of $n_e = (10^3 - 10^4)$ cm$^{-3}$ of ionized gas surrounding young, massive stars and consistent with the ionized gas densities we derive in Section [5.4](#sec:iongas).

The uncertainties in the electron temperatures we derive in Table [\[tab:temp\]](#tab:temp) are dominated by the uncertainties in the free-free fraction. We take the mean and standard deviation values of $T_e = (6000 \pm 400)$ K as a representative electron temperature of the ionized plasma in the candidate star clusters. This temperature is consistent with the temperature derived from a lower-resolution analysis of NGC 4945 at 2.3$''$ $\times$ 2.6$''$ resolution, which finds $T_e = (5400 \pm 600)$ K (cite: Bendo2016).

Our estimated temperature implies a thermal line width of $(16 \pm 4)$ km s$^{-1}$ (cite: Brocklehurst1972). Given that this is smaller than our observed line widths, non-thermal motions from bulk velocities (such as turbulence, inflow or outflow) must contribute to broadening the spectral line profiles.

The electron temperature of free-free plasma surrounding massive stars is related to the metallicity of the plasma, as the metals contribute to gas cooling. (cite: Shaver1983) established a relation, $$\begin{equation}
\begin{split}
12 + \log_{10}(\mathrm{O/H}) = (9.82 \pm 0.02) - \\ (1.49\pm 0.11) \frac{T_e}{10^4\,\mathrm{K}},
\end{split}
\end{equation}$$ with the temperatures and metallicities derived with (auroral) collisionally excited lines at optical wavelengths. Furthermore, they showed that these temperatures are consistent with electron temperatures derived from radio recombination lines. We find a representative O/H metallicity of $12 + \log_{10}(\mathrm{O/H}) = 8.9 \pm 0.1$. This value is in approximate agreement (within 2$\sigma$) with the average metallicity and standard deviation of $12 + \log_{10}(\mathrm{O/H}) = 8.5 \pm 0.1$ (cite: Stanghellini2015) determined in 15 star-forming regions in the galactic plane of NGC 4945 (and which is consistent with no radial gradient) using strong-line abundance ratios of oxygen, sulfur, and nitrogen spectral lines.

## Ionized Gas: Emission Measure, Density and Mass

We determine the volumetric emission measure of gas ionized in candidate stars clusters using Equations [\[eq:Scont\]](#eq:Scont) and [\[eq:Sline\]](#eq:Sline) together with the mean temperature derived in Section [5.3](#sec:temp). In Table [\[tab:props\]](#tab:props), we list the results for each candidate star cluster. Emission measures that we determine from the free-free continuum range from $\log_{10} (EM_{\mathrm{C}} / \mathrm{cm^{-6} \, pc^3}) \sim 7.3$ – 8.7, with a median value of 8.4. We also calculate the volumetric emission measure of ionized hydrogen as determined by the effective H41$\alpha$ recombination line when applicable, noting that $EM_{\mathrm{C}} = (1+y)\,EM_{\mathrm{L}}$. The line emission measures range from $\log_{10} (EM_{\mathrm{L}} / \mathrm{cm^{-6} \, pc^3}) \sim 8.4$ – 8.9, with a median value of 8.5. The uncertainty in the emission measures is $\sim$0.4 dex and is dominated by the errors of the free-free fraction.

Next, we solve for the electron density. We use the emission measure determined from the free-free continuum, assume $n_e = n_+$, and consider a spherical volume with $r = \mathrm{FWHM_{size}} / 2$. We arrive at densities between $\log_{10} (n_e/\mathrm{cm}^{-3})= 3.1$–3.9 with a median value of 3.5.

We matched (see Section [3.2](#sec:fluxextract)) five of the candidate star clusters that have recombination line emission detected – Sources 1, 6, 14, 21, 27 – with the 2.3 GHz objects of (cite: Lenc2009) which have the free-free optical depth modeled through their low-frequency turnovers. Although the 2.3 GHz objects have non-thermal indices, it is their radio emission which is opaque to free-free plasma. Using the optical depths derived in (cite: Lenc2009) and our fiducial electron temperature, we solve for the density through the relation, $\tau \approx 3.28 \times 10^{-7} \left( \frac{T_e}{10^4~\mathrm{K}} \right)^{-1.35} \left( \frac{\nu}{\mathrm{GHz}} \right)^{-2.1} \left( \frac{EM_{\ell}}{\mathrm{cm^{-6}~pc}} \right)$ (cite: Condon2016), where $EM_{\ell} = n_e n_+ \ell$ and for which a spherical region the pathlength $\ell$ translates as $\ell = \frac{3}{4}r$. We find densities in the range $\log_{10} (n_e/\mathrm{cm}^{-3})= 3.3$ – 3.6. This agrees well with the values we separately derive.

We convert the ionized gas density and source sizes to an ionized gas mass through, $$\begin{equation}
M_{+} = 1.36 m_{\mathrm{H}} \, n_+  \frac{4}{3}\pi r^3
\end{equation}$$ where we have assumed a 1.36 contribution of helium by mass and we let $r = \mathrm{FWHM_{size}} / 2$. The ionized gas masses of the candidate star clusters range from $\log_{10} (M_+$ / M$_{\odot}$) = 2.7 – 3.5 with a median value of 3.1. The ionized gas mass is a small fraction ($\lesssim 1$%) of the stellar mass (see Section [5.5](#sec:mass)).

## Ionizing Photon Production and Stellar Mass

c C C C C C C C C Source & FWHM & $\log{ (EM_{\mathrm{C}}) }$ $^{a}$ & $\log{ (EM_{\mathrm{L}}) }$ $^{a}$ & $\log{ (Q_0) }$ $^{a}$ & $\log{ (M_{\star}) }$ $^{a}$ & $\log{ (M_{\mathrm{gas}}) }$ $^{a}$ & $\log{ (\Sigma_{\mathrm{Tot}}) }$ $^{a}$ & $\log{ (t_{\mathrm{ff}}) }$ $^{a}$\
& (pc) & (cm$^{-6}$ pc$^3$) & (cm$^{-6}$ pc$^3$) & (s$^{-1}$) & (M$_{\odot}$) & (M$_{\odot}$) & (M$_{\odot}$ pc$^{-2}$) & (yr)\
& 3.0 & 8.1 & 8.6 & 51.2 & 5.1 & \<4.5 & 4.0 & 4.9\
02 & 2.6 & 8.2 & ... & 51.3 & 5.2 & 4.8 & 4.3 & 4.7\
03 & 3.1 & 8.2 & 8.4 & 51.2 & 5.2 & 4.8 & 4.1 & 4.9\
04 & 2.5 & 7.7 & 8.5 & 50.8 & 4.7 & 4.6 & 4.0 & 4.9\
06 & 2.9 & 8.0 & 8.4 & 51.1 & 5.0 & \<4.5 & 3.8 & 5.0\
07 & 2.7 & 8.1 & 8.4 & 51.2 & 5.1 & 4.6 & 4.2 & 4.8\
08 & 2.4 & 8.5 & 8.7 & 51.5 & 5.5 & 4.5 & 4.5 & 4.6\
09 & 2.4 & 8.1 & ... & 51.2 & 5.1 & \<4.3 & 4.1 & 4.8\
10 & 2.9 & 8.2 & ... & 51.2 & 5.1 & \<4.5 & 4.0 & 4.9\
11 & 1.4 & 8.0 & ... & 51.1 & 5.0 & 4.0 & 4.6 & 4.5\
12 & 2.7 & 8.2 & 8.7 & 51.3 & 5.2 & 5.0 & 4.4 & 4.7\
13 & 2.5 & 8.5 & 8.7 & 51.6 & 5.5 & 4.7 & 4.6 & 4.6\
14 & 2.2 & 8.1 & 8.9 & 51.2 & 5.1 & 4.4 & 4.3 & 4.7\
15 & 2.5 & 8.0 & 8.4 & 51.0 & 5.0 & \<4.4 & 4.0 & 4.9\
16 & 2.3 & 8.1 & ... & 51.2 & 5.1 & 4.7 & 4.3 & 4.7\
17 & 3.1 & 8.7 & ... & 51.7 & 5.7 & 5.2 & 4.6 & 4.6\
19 & 2.4 & 7.4 & ... & 50.5 & 4.4 & \<4.3 & 3.5 & 5.1\
20 & 3.7 & 8.4 & ... & 51.4 & 5.3 & 5.1 & 4.2 & 4.9\
21 & 3.1 & 7.3 & 8.8 & 50.4 & 4.3 & \<4.6 & 3.1 & 5.4\
22 & 2.4 & 8.7 & 8.7 & 51.8 & 5.7 & 4.9 & 4.8 & 4.5\
23 & 2.6 & 8.2 & ... & 51.3 & 5.2 & 4.4 & 4.3 & 4.7\
24 & 3.1 & 7.6 & ... & 50.6 & 4.6 & \<4.6 & 3.4 & 5.2\
25 & 3.9 & 8.2 & 8.5 & 51.3 & 5.2 & 5.0 & 4.0 & 5.0\
26 & 3.4 & 8.3 & 8.5 & 51.3 & 5.3 & 4.9 & 4.2 & 4.9\
27 & 2.2 & 8.2 & 8.4 & 51.3 & 5.2 & \<4.3 & 4.3 & 4.7\
28 & 4.0 & 8.0 & ... & 51.1 & 5.0 & \<4.8 & 3.6 & 5.1\
29 & 2.9 & 8.4 & ... & 51.5 & 5.4 & 4.6 & 4.3 & 4.7

Table notes: Source 5 is not included since its free-free fraction is $f_{\mathrm{ff}} < 0.01$; Source 18 is not included since it is the AGN core. FWHM is the source size as best fit from a Gaussian (to flux that has not been deconvolved); the errors reflect the fit of the Gaussian. $EM_{\mathrm{C}}$ is the free-free emission measure derived from the continuum as in Equation [\[eq:Scont\]](#eq:Scont). $EM_{\mathrm{L}}$ is the hydrogen free-free emission measure derived from effective H41$\alpha$ as in Equation [\[eq:Sline\]](#eq:Sline); we note $EM_{\mathrm{C}} = (1+y)\,EM_{\mathrm{L}}$. $Q_0$ is the ionizing photon rate derived from $EM_{\mathrm{C}}$ as in Equation [\[eq:Q\]](#eq:Q). M$_{\odot}$ is the stellar mass derived from $Q_0$ as in Equation [\[eq:M\]](#eq:M).\
$^{a}$ The error on these quantities is $\sim$0.4 dex.

We estimate the number of the ionizing photons needed per second to maintain the total free-free emitting content (see Table [\[tab:props\]](#tab:props)). From the emission measure of ionized gas and the temperature-dependent recombination coefficient for case B recombination, the rate of ionizing photons (see Appendix [8.3.2](#ap:q)) with $E>13.6$ eV is $$\begin{equation}
\begin{split}
Q_0 = \left( 3.8 \times 10^{51}~\mathrm{s}^{-1} \right) \left( \frac{ n_e n_+ V }{ 5 \times 10^8~\mathrm{cm^{-6}~pc^3} } \right) \times \\ \left( \frac{ T_e }{ 10^4~\mathrm{K} } \right)^{-0.83} .
\label{eq:Q}
\end{split}
\end{equation}$$ where $EM_{\mathrm{C}} = n_e n_+ V$ is the volumetric emission measure of the total ionized gas which we take from the continuum derived emission measure, and $T_e$ is the electron temperature of the ionized gas. Our candidate star clusters have ionizing photon rates in the range $\log_{10} (Q_0 / \mathrm{s}^{-1}) \sim 50.4$ – 51.8. The sum of the ionizing photon rate over all candidate, massive star clusters is $5.3 \times 10^{52}$ s$^{-1}$. In the top panel of Figure [11](#fig:cmf), the ionizing photon rates of the candidate clusters are plotted as complementary cumulative fractions.

We use Starburst99 calculations (cite: Leitherer1999) to infer the stellar mass from the ionizing photon output of a 5 Myr old stellar population, via $$\begin{equation}
    M_{\star} \approx \frac{ Q_0 }{ 4.7 \times 10^{45} } \mathrm{M_{\odot}}.
\label{eq:M}
\end{equation}$$ We arrive at this value by simulating a single $10^6$ M$_{\odot}$ stellar population, with the initial mass function (IMF) of (cite: Kroupa2001), a maximum stellar mass of 100 M$_{\odot}$, and the default stellar evolution tracks and tuning parameters. Then we divide the ionizing photon output at 5 Myr by the initial mass of the stellar population. We note that this is a rough approximation which has not accounted for the amount of ionizing photons absorbed by dust, mass ejected from the system, and/or enhanced emission from stellar binaries.

Our candidate star clusters have stellar masses in the range $\log_{10} ( M_{\star} / \mathrm{M_{\odot}} ) \sim$ 4.7–6.1 (see Table [\[tab:props\]](#tab:props)) with a median of 5.5. The error on the mass estimate is $\sim$0.4 dex. The sum of the stellar masses of the candidate stars clusters is $\approx 1.1 \times 10^7$ M$_{\odot}$. In the bottom panel of Figure [11](#fig:cmf), the estimated stellar masses of the candidate clusters are plotted as cumulative fractions.

![](stellar_l_m.pdf)

## Gas Mass from Dust

We estimate the mass of gas associated with each candidate star cluster (see Table [\[tab:props\]](#tab:props)) from dust emission at 350 GHz. We determine the dust optical depth by comparing the measured intensity with that expected from an estimate of the true dust temperature. Assuming a mass absorption coefficient, we convert the optical depth to a dust column density. We arrive at a gas mass by multiplying the dust column density with the measured source size and an assumed dust-to-gas mass ratio.

We assume a dust temperature of $T_{\mathrm{dust}} = 130$ K, as has been determined for the gas kinetic temperature in the forming super star clusters in NGC 253 (cite: Gorski2017). This is an approximation, though the uncertainty is linear. Then we convert the 350 GHz flux density into an intensity ($I_{350}$), and solve for the optical depth through $I_{350} \approx \tau_{350} B_{\nu}(T_{\mathrm{dust}})$ where $B_{\nu}(T_{\mathrm{dust}})$ is the Planck function evaluated at 350 GHz. We measure optical depths in the range $\tau_{350} \sim$ 0.02 – 0.10, with a median value of $\tau_{350} \sim 0.04$, justifying our optically thin assumption. We note that the $3\sigma$ upper limit of the sources which have not been detected at 350 GHz corresponds to $\tau_{350}< 0.02$.

Next, we convert the optical depth to a dust column density using an assumed mass absorption coefficient ($\kappa$). We adopt $\kappa = 1.9$ cm$^2$ g$^{-1}$ which should be appropriate for $\nu \sim 350$ GHz and dust mixed with gas at a density of $\sim 10^5 - 10^6$ cm$^{-3}$ (cite: Ossenkopf1994), but we do note the large (factor of 2) uncertainties on this value. Finally, we combine the dust surface density with an adopted dust-to-gas mass ratio (DGR) of 1-to-100, approximately the Milky Way value and similar to the value found for starburst galaxies by (cite: Wilson2008). Our estimate for the gas surface density is determined with: $$\begin{equation}
\Sigma_{\mathrm{gas}} = \frac{ \tau_{350} }{ \kappa \, \mathrm{DGR} } .
\end{equation}$$ We determine the gas mass by multiplying the gas surface density by the two dimensional area of the source size, $M_{\mathrm{gas}} = A\, \Sigma_{\mathrm{gas}}$.

The gas masses we estimate are included in Table [\[tab:props\]](#tab:props). We find values in the range of $\log_{10} (M_{\mathrm{gas}}$ / M$_{\odot}$) = 4.4 – 5.1 with a median value of 4.7. Upper limits for the sources which have not been detected in 350 GHz emission are included in the Table.

## Total Mass from Gas and Stars

We estimate the current total mass of each candidate star cluster as the sum of the gas and star masses, where $M_{\mathrm{Tot}} = M_{\mathrm{gas}} + M_{\star}$. The total mass is dominated by the stellar mass, as we find low gas mass fractions of $M_{\mathrm{gas}} / M_{\mathrm{Tot}} =$ 0.04 – 0.22 and a median of 0.13. When calculating the total mass of the 10 sources which are not detected at 350 GHz, we do not include the lower limit of the dust mass; we only consider the stellar mass.

We express the total mass of each source in terms of a surface density (in Table [\[tab:props\]](#tab:props)). This is calculated within the FWHM of the region; we thereby divide the total mass by 2 and divide by the 2D area of the FWHM. The values range from $\log{ (\Sigma_{\mathrm{Tot}}) } = 3.1$ – 4.8 M$_{\odot}$ pc$^{-2}$, or alternatively, $\Sigma_{\mathrm{Tot}} = 0.3$ –13 g cm$^{-2}$.

Using the total mass, we estimate the gravitational free fall time of the clusters, $t_{\mathrm{ff}} = \left( \frac{ \pi r^3 }{ 8 G M_{\mathrm{Tot}} } \right)^{1/2}$. The values we derive are included in Table [\[tab:props\]](#tab:props), and range from $\log_{10} (t_{\mathrm{ff}}$ / yr ) = 4.3 – 5.2 with a median of 4.6. This is the gravitational free fall time that would be experienced by gas with no support if all of the cluster mass were gas. The fact that the gas mass fractions are low and that the age appears longer than the free fall time adds support to the idea that these clusters have mostly already formed.

Summing all sources, we find a total mass within the candidate clusters of $M_{\mathrm{Tot}} \approx 1.5 \times 10^7$ M$_{\odot}$.

# Discussion

Having estimated properties of the candidate star clusters, we explore implications of the results and the role of the candidate clusters with respect to the starburst. Before elaborating on that, we discuss the two main sources of uncertainty in the properties of the candidate star clusters: the free-free fractions at 93 GHz and the age of the burst.

## Discussion of uncertainties

Both the free-free fractions at 93 GHz and the age of the burst could be better constrained using future observations, and this would result in more accurate estimates of almost all properties of the cluster candidates.

The first source of uncertainty that we discuss is the estimate of the free-free flux, by which we estimate a free-free fraction to the 93 GHz continuum.

Overall, the assumptions , especially regarding synchrotron emissions, likely affect individual clusters at the $\sim 30\%$ level. This is not enough to bias our overall results, but follow up observations at other frequencies would be extremely helpful.

The second uncertainty is the assumed age of the burst. We discuss in Section [5.2](#sec:age) how we arrive at an adopted age of the clusters of $\sim$5 Myr. The assumed age has a large impact on the stellar mass inferred from the ionizing photon rate. The ionizing photon output changes substantially (by a factor of 40 from a zero age main sequence to an age of 5 Myr) as the most massive stars explode as supernova. An uncertainty of $\sim$1 Myr about an age of 5 Myr of a star cluster results in an uncertainty in the inferred stellar mass by a factor of four. This is roughly included in the 0.4 dex uncertainty, though it would represent a systematic offset.

## Super Star Clusters

The estimated properties (mass, size, age; Table [\[tab:props\]](#tab:props)) that we derive for these candidate star clusters meet the criteria for young, massive clusters (cite: PortegiesZwart2010), and these sources can be considered super star clusters (SSCs). Stars clusters forming in high gas surface density environments may be able to acquire significant amounts of mass before feedback effects (likely radiation pressure) can disrupt and/or disperse the cluster (cite: Adamo2016). Super star clusters with stellar masses of $M_{\star} \gtrsim 10^5$ M$_{\odot}$ typically have high star formation efficiencies $(\varepsilon > 0.5)$ and therefore remain bound.

With the mass surface densities that we estimate and the age of the burst equaling many multiples of the free-fall times, these star clusters will likely remain bound, at least initially. They are being born into a violent environment and clusters often still experience significant mortality after forming. Estimates of the virial mass, escape velocity and momentum driving determined through molecular line observations will help quantity their mass and initial dynamical state.

## Cluster Mass Function

In Figure [11](#fig:cmf), we plot the cluster stellar-mass function of candidate SSCs in NGC 4945 and compare it with the cluster mass distributions in additional galaxies with SSC populations.

A power-law fit to the cluster mass distribution, of 22 sources down to $M_{\star} = 2.4 \times 10^5$ M$_{\odot}$, in NGC 4945 results in a slope of $\beta = -1.8 \pm 0.4$. Note that the fit to the data results in $\beta = -1.76 \pm 0.07$, but given the uncertainty in our mass estimates (0.4 dex), we adopt the conservative figure. We include the SSCs of NGC 253, with stellar mass properties determined on similar spatial scales ($\sim$2 pc resolution) and through H40$\alpha$ recombination lines for a zero-age main sequence population (cite: Leroy2018; Mills2020). A power-law fit to the cluster mass distribution of NGC 253, including 12 star clusters down to $M_{\star} = 7.9\times 10^4$ M$_{\odot}$, results in a slope of $\beta = -1.6 \pm 0.3$. We estimated the completeness limits by eye. The turn-off from power-law distributions likely includes non-physical effects, resulting from the depth/sensitivity of the observations as well as source confusion due to the high inclination in which we view the starburst regions (and which appears to be higher in NGC 253).

We also include recent results from a homogeneous analysis by (cite: Mok2020) of the cluster mass distributions of young ($\tau < 10$ Myr), massive clusters in six galaxies. As representative examples, we include the best fit power-laws from three systems: the Large Magellanic Clouds (LMC), M 51, and the Antennae System. A main result from (cite: Mok2020) is that the cluster mass functions across the six galaxies are consistent with slopes of $\beta = -2.0 \pm 0.3$. Our measurements for NGC 4945 and NGC 253 are consistent with these findings.

As we discuss in Section [6.6](#sec:sfr), we estimate the total stellar mass in the burst to be $8.5 \times 10^{7}$ M$_{\odot}$. Extending the best fit of our cluster mass function down to a cluster mass of $\sim 2 \times 10^4$ M$_{\odot}$ would account for the additional mass and correspondingly the additional ionizing photon luminosity. As we discuss in Section [6.4](#sec:dig), if these lower mass clusters are present they would need to be located in a more-extended region than the super star clusters. Therefore the cluster mass distribution may not reach down to $2 \times 10^4$ M$_{\odot}$ in the region where the SSCs are located, but perhaps $\sim 4 \times 10^4$ M$_{\odot}$ if a third of the additional recombination line emission results from diffuse ionized gas.

## Ionizing Photons and Diffuse Ionized Gas

*Total ionizing photon rate of the starburst.* We measure an H40$\alpha$ recombination line flux of ($6.4 \pm 1.0$) Jy km s$^{-1}$ integrated within the T2 aperture (see Figure [8](#fig:totalap)) in the intermediate-configuration (0.7$''$) data. Assuming the temperature of $T_e = (6000\pm400)$ K from Section [5.3](#sec:temp), the total ionized content, which accounts for the full star-formation rate of the starburst, yields an ionizing photon rate of $Q_{\mathrm{T2}} = (3.9 \pm 0.3) \times 10^{53}$ s$^{-1}$.

*Ionizing photon rate from candidate super star clusters.* The sum of the ionizing photon rate over all massive star clusters is $\approx 5.3 \times 10^{52}$ s$^{-1}$. The total integrated line flux of H40$\alpha$ in the extended-configuration (0.2$''$) data is $\int S\, \mathrm{dv} = (2.1 \pm 0.6)$ Jy km s$^{-1}$ within an aperture (T1) which covers the clusters in the starburst region. With the temperature of $T_e = (6000 \pm 400)$ K, the integrated line flux corresponds to an ionizing photon rate of $Q_{\mathrm{T1}} = (1.2 \pm 0.4) \times 10^{53}$ s$^{-1}$. Given the large uncertainties derived for individual clusters, we consider this value consistent with the sum over individual clusters. Therefore, we conclude that 20% to 44% of the total ionizing photons in the starburst can be attributed to the candidate super star clusters identified in NGC 4945.

*Low mass clusters.* The intermediate-configuration (0.7$''$) data are sensitive to emission on larger physical scales, but they also reach deeper sensitivities per unit area. Consequently, emission from a distribution of many compact, low mass clusters could be traced in these data, but not in the extended-configuration data.

We do not find it likely that the deficit of line emission in the extended-configuration data can be attributed primarily to low mass clusters. Focusing only on the low resolution (0.7$''$) observations, the integrated line flux is greater in the larger aperture (T2) than in the aperture covering only the star clusters (T1), indicating that additional line emission originates outside of the area where massive clusters are forming. In order for low mass clusters to account for the difference, these would need to form in a more extended region than the bright SSCs that we see.

*AGN and the circumnuclear disk.* The circumnuclear disk, including the AGN, could be an origin for ionizing photons observed only on larger scales. The strongest recombination line emission is seen at low-resolution in this region yet no significant line detections are obtained towards Sources 17, 18, and 20. We test this scenario by extracting spectra from the 0.7$''$ intermediate-configuration data and the 0.2$''$ extended-configuration data in 7 non-overlapping apertures of 3$''$ diameter consecutively distributed along the major axis of the starburst region. The ratios of the line flux in the intermediate- to extended-configuration data are all consistent within error; the ratios in the seven regions have a mean and standard deviation of $2.3 \pm 0.5$. This indicates that a deficit of line emission on the physical scales probed in the high resolution data is ubiquitous (and not unique to the region surrounding the AGN), and at most $\sim20$% may originate from the circumnuclear disk and AGN.

*Diffuse ionized gas on large-scales.* Summarizing the information above, we find that up to $\sim$70% of the total radio recombination line flux may originate on scales larger than $\sim$100 pc; this emission cannot be directly attributed to the AGN. Ionizing radiation may be escaping the immediate surroundings of massive stars and reaching larger scales. The approximate age of the burst indicates clusters have had time to shed their natal material, dust is not a significant contribution of their emission, low gas mass fractions have been determined, and the current free-fall times of the clusters indicate abundant time to expel gas. Despite these indicators, extinctions may still be considerable and patchy regions may help to leak ionizing photons. Note that if radiation is escaping from star clusters, this would also imply that the stellar masses (derived from the ionizing photon rates) are underestimated.

However, a missing 70% of line flux in the 0.2$''$ resolution data should be considered as an upper limit. Given the low signal-to-noise ratio of these lines, artifacts in both the image and spectral domains can impact the properties of the line profiles. For example, incomplete $uv$ coverage on the scales of the emission can result in incorrect deconvolution and thus systematic underestimates. Deeper observations at high resolution ($\sim$0.1$''$) would allow radio recombination lines to be mapped out with adequate signal-to-noise ratio and obtain sensitivities approaching that of the low-resolution (0.7$''$) observations.

## Role of the AGN

Although the Seyfert 2 AGN in NGC 4945 is one of the brightest in our sky at X-ray energies, obscuration by e.g., $A_{\mathrm{V}} \geq 160$ (cite: Spoon2000) has prevented its observation at virtually all other wavelengths (also given the spatial resolutions observed). Our observations at 93 GHz provide another piece of evidence for its existence.

We detect a point source in the 93 GHz image with a deconvolved size determined by `PyBDSF` of $\mathrm{FWHM} = 0.84 \pm 0.01$ pc. The flux of $9.7 \pm 1.0$ mJy that we extract from the source is $\sim10$% of the total continuum ($\sim$120 mJy) flux in the 0.12$''$ resolution data. The Band 3 spectral index we derive is $\alpha_{93} = -0.85 \pm 0.05$, which is consistent with freshly accelerated electrons emitting synchrotron radiation. However, we follow the procedure outlined in Section [3.3](#sec:freefreefrac), assuming free-free emission may also contribute, and place a limit on the ionizing photon rate. The spectral index at 93 GHz corresponds to $f_{\mathrm{ff}} \geq 0.47 \pm 0.03$. If we assume a temperature of $T_e = 6000$ (30 000) K this would correspond to $Q_0 = 1.1 \,(0.5) \times 10^{52}$ s$^{-1}$. The low level of escaping ionizing radiation is consistent with previous work from MIR line ratios (cite: Spoon2000).

We place a limit on the ionizing photons that could be leaking into medium. The bolometric luminosity estimated from the X-ray luminosity is $L_{\mathrm{bol}} \approx 6 \times 10^{43}$ erg s$^{-1}$, which we determined using the relation for Seyfert AGN of $L_{\mathrm{bol}} \sim 20 L_{\mathrm{X}}$ (cite: Hopkins2007). Given the bolometric luminosity, we can now estimate the total expected ionizing photon luminosity. We use the standard relation of (cite: Elvis1994), which posits $L_{\mathrm{bol}} / L_{\mathrm{ion}} \sim 3$ with an average ionizing photon energy of 113 eV. Therefore the expected ionizing photon luminosity of the AGN is $L_{\mathrm{ion}} \approx 2 \times 10^{43}$ erg s$^{-1} \approx 5 \times 10^{9}$ L$_{\odot}$, while our limit corresponds to $\approx 2 \times 10^{42}$ erg s$^{-1}$. This would imply that $<10$% of the ionizing photon luminosity of the AGN is escaping into the surrounding nuclear starburst and creating ionized gas.

## Total Burst of Star-formation

We can convert the total ionizing photon rate of the burst $Q_{\mathrm{T2}}$ (see Section [6.4](#sec:dig)), as measured in the T2 region, to a luminosity. Assuming an average ionizing photon energy of $\left<h\nu\right> \approx 17$ eV, the ionizing luminosity is $L_{\mathrm{T2}} \approx 1.1 \times 10^{43}$ erg s$^{-1} = 2.8 \times 10^{9}$ L$_{\odot}$. A ratio of bolometric luminosity to ionizing photon luminosity $L_{\mathrm{bol}}$/$L_0 \sim 14$ is predicted for a 5 Myr old population, using Starburst99 (cite: Leitherer1999). Thus, we can expect a bolometric luminosity of $4 \times 10^{10}$ L$_{\odot}$ which agrees within error to the bolometric luminosity derived from FIR observations, $L_{\mathrm{bol}} = (2.0 \pm 0.2) \times 10^{10}$ L$_{\odot}$ (cite: Bendo2016).

We note that, if we had adopted a lifetime for the burst of 4 Myr rather than 5 Myr, Starburst99 calculations expect a bolometric luminosity of $L_{\mathrm{bol}} \approx 2 \times 10^{10}$ L$_{\odot}$. Also, this calculation assumes the source of the additional recombination line emission in the intermediate-configuration data is also characterized by a 5 Myr old stellar population.

The ratio of bolometric luminosity to mass of a 5 Myr old burst is estimated at $\Psi \sim 470$ L$_{\odot}$/M$_{\odot}$. With an $L_{\mathrm{bol}} = 4 \times 10^{10}$ L$_{\odot}$, the inferred total stellar mass of the population is $\sim 8.5 \times 10^7$ M$_{\odot}$. The total stellar mass in our candidate clusters is $\approx 1.1 \times 10^7$ M$_{\odot}$, or $\sim$13% of the expected total stellar mass.

## Star Clusters and the Central Wind

An outflow of warm ionized gas in NGC 4945 has been modeled as a biconical outflow with a deprojected velocity of $\mathrm{v} \approx 525$ km s$^{-1}$ with emission out to 1.8 kpc (cite: Heckman1990). The outflow has been traced in \[NII\], \[SII\] and H$\alpha$ in multiple analyses (cite: Heckman1990; Moorwood1996; Mingozzi2019). (cite: Heckman1990) estimated a total energy of $2 \times 10^{55}$ erg and momentum flux of $9 \times 10^{33}$ dyne $= 1400$ M$_{\odot}$ km s$^{-1}$ yr$^{-1}$ (after correcting for the updated distance). These values do not include possible contributions by colder phases, which are likely associated with the NGC 4945 outflow (Bolatto et al., in prep.). While these values are uncertain, they are useful for an order of magnitude comparison with expected properties of the star clusters.

Gas reaching 1.8 kpc and moving at 525 km s$^{-1}$ would have been launched $\sim$3 Myr ago assuming a constant velocity, which is within the time-frame of the burst. A $\sim$3 Myr time-scale and a velocity of 525 km s$^{-1}$ would put $8 \times 10^6$ M$_{\odot}$ of warm ionized gas mass into the outflow. Using Starburst99 (cite: Leitherer1999), an estimated mechanical luminosity of $\sim 3 \times 10^{41}$ erg s$^{-1}$ from the clusters, fairly constant over the 5 Myr age, equates to an injected energy of $\approx6 \times 10^{55}$ erg. It would require 30% of the expected mechanical energy output of the clusters to drive the ionized outflow. From simulations, the total momentum supplied to the ISM per supernova is expected to be $2.8 \times 10^5$ M$_{\odot}$ km s$^{-1}$ (cite: Kim2015), with stellar winds contributing an additional 50% to the momentum. Starburst99 predicts the supernova rate to be fairly constant at $\sim$0.009 yr$^{-1}$ for these clusters. From these values, we estimate that the momentum supplied to the ISM by the candidate star clusters would be $\sim3800$ M$_{\odot}$ km s$^{-1}$ yr$^{-1}$. It would require about 40% of the expected momentum output of the clusters to drive the ionized outflow. Therefore, neither the energetics nor the inferred momentum of the outflow prevent it from being driven solely by the star clusters in NGC 4945, although there are very considerable uncertainties associated with this calculation.

## Comparison with NGC 253

NGC 253 is a nearly edge-on galaxy located nearby (cite: Rekola2005) with similar properties as NGC 4945. It hosts a central starburst spanning $\sim$200 pc with young, massive clusters (cite: Leroy2018; Mills2020). A major difference between these two galaxies is that NGC 4945 shows signatures of harboring an active super-massive black hole. Since NGC 4945 is just the second analysis we have undertaken with millimeter wavelength ALMA observations on scales which resolve the clusters, it is relevant to compare the properties of their super stars clusters.

Analyses of the cluster population of NGC 253 at $\sim$2 pc resolution with ALMA (cite: Leroy2018; Mills2020) revealed 18 sources as (proto-)super star clusters which are in the process of forming or close to a zero age main sequence ($\sim$1 Myr) (cite: Rico-Villas2020). Overall the properties of the clusters are strikingly similar as those in NGC 4945; they have a median stellar mass of $1.4\times10^{5}$ M$_{\odot}$ and FWHM sizes of 2.5–4 pc. The star clusters of NGC 253 boast slightly higher ionizing photon luminosities and larger gas fractions $M_{\mathrm{gas}} / M_{\mathrm{tot}} \sim 0.5$, reflecting a slightly younger age. The slopes of the cluster mass function we derive are also consistent (see Section [6.3](#sec:cmf)), just offset by a factor of $\sim$3.5 in mass. As in NGC 4945, at least 30% of the of the nuclear starburst of NGC 253 originates in a clustered mode of star-formation.

While we have not estimated some of the dynamical properties of NGC 4945, the presence of broad recombination line emission in four sources in NGC 253 indicates the star clusters are operating under similar processes. In NGC 253, the sources are young enough that feedback has not managed to unbind a large fraction of the gas from the clusters. The slightly higher total mass surface densities and smaller free-fall times in NGC 4945 indicate its clusters might be surviving a young, disruptive stage.

The concerted feedback of the young ($<10$ Myr), forming SSCs identified in NGC 253 (cite: Leroy2018) are likely not responsible for the starburst driven outflow, (cite: Bolatto2013; Krieger2019). Some (global) event may be initiating the active formation of star clusters. On the other hand, the star clusters in NGC 4945 could potentially influence the outflow of warm ionized gas; some event appears to be inhibiting the formation of new star clusters.

# Summary

Massive, clustered star-formation is an efficient and possibly common mode of star-formation in high gas density environments. Nearby galaxies with bursts of star-formation in the central $\mathcal{O}$(100 pc) are local laboratories to study this mode, and for NGC 4945, in the presence of a Seyfert AGN. High levels of dust extinction ($A_V \sim 40$) in the nearly edge-on ($i \sim 72^{\circ}$) central region of NGC 4945 have previously prevented the direct observation and characterization of its massive star clusters.

We identify 27 super star cluster candidates in the central starburst of NGC 4945. We derive properties of the candidate clusters through ALMA observations at 2.2 pc resolution of the 93 GHz (3 mm) free-free emission and hydrogen recombination line emission (H40$\alpha$ and H42$\alpha$) arising in photo-ionized gas. We also use and present high-resolution 350 GHz imaging of the dust continuum observed with ALMA, and supplement our analysis with 2.3 GHz continuum imaging which primarily traces synchrotron emission (cite: Lenc2009).

Our results are as follows:

- The 27 point sources identified ($\geq10\sigma$) in 93 GHz continuum emission as candidate super star clusters have FWHM sizes of 1.4–4.0 pc. The 93 GHz emission in these bright, compact regions is dominated by free-free emission, with a median free-free fraction of $f_{\mathrm{ff}} = 0.62$. Synchrotron emission from recent supernova remnants contributes to the 93 GHz emission with a median fraction of $f_{\mathrm{syn}} = 0.36$. Substantial dust emission is found in three sources.

- We average the spectra of the H40$\alpha$ and H42$\alpha$ recombination lines to synthesize an effective H41$\alpha$ profile. Recombination line emission is detected in 15 candidate clusters, generally with narrow (FWHM $\sim36$ km s$^{-1}$) line widths. Six of the detected sources have significant ($f_{\mathrm{syn}} \gtrsim 0.5$) synchrotron emission; three of those have broad line widths with FWHM $> 105$ km s$^{-1}$.

- We estimate an electron temperature of $T_e = (6000 \pm 400)$ K of the ionized gas using the flux ratio of the integrated line to free-free continuum. This electron temperature implies an average metallicity of $12 + \log_{10}(\mathrm{O/H}) = 8.9 \pm 0.1$ surrounding these young massive stars. The ionized gas densities of $\log_{10} (n_e/\mathrm{cm}^{-3})= 3.1$–3.9, that we derive are typical of classic H II regions. The ionized gas masses of the clusters are typically $<1$% of the estimated stellar mass.

- We determine ionizing photon rates of the candidate SSCs in the range $\log_{10} (Q_0 / \mathrm{s}^{-1}) \sim 50.4$ – 51.8. Adopting an age of $\sim$5 Myr, the stellar masses implied by the ionizing photon rates are $\log_{10} ( M_{\star} / \mathrm{M_{\odot}} ) \sim$ 4.7–6.1. The sum of the stellar masses of the candidate SSCs is $\approx 1 \times 10^7$ M$_{\odot}$. The uncertainties on these measurements are 0.4 dex. We discuss the age estimate in Section [5.2](#sec:age).

- We fit the cluster stellar-mass distribution and find a slope of $\beta = -1.8 \pm 0.4$. The slope of the fit is consistent with our fit to the candidate SSCs in the central starburst of NGC 253 (cite: Mills2020) and to recent findings in the LMC, M 51, and the Antennae system (cite: Mok2020).

- We estimate the gas mass of the candidate clusters from dust emission. The total mass, $M_{\mathrm{Tot}}$, is evaluated by the combined stellar and gas masses. Gas mass fractions range from $M_{\mathrm{gas}}/M_{\mathrm{Tot}}=0.04$–0.22, with a median value of 0.13. We calculate the total-mass surface density of the clusters and find a median value of $\Sigma_{\mathrm{Tot}} = 3 \times 10^{4}$ M$_{\odot}$ pc$^{-2}$. The median free-fall timescale is $0.04$ Myr.

- With low-resolution (0.7$''$) observations of the H40$\alpha$ recombination line, we measure a total ionizing photon rate of the burst of $Q_0 = (3.9 \pm 0.3) \times 10^{53}$ s$^{-1}$. The candidate star clusters that we analyze contribute 20–44% of the total ionizing photon rate. Additional recombination line emission present in the low-resolution data appears to be ubiquitous throughout the starburst region, cannot be directly attributed to the AGN, and is also found outside of the area where the SSCs are located. Diffuse ionized gas may be responsible for some of the additional emission, although low mass clusters and distributed star formation are expected to also contribute. This indicates that ionizing radiation may be escaping the immediate surroundings of massive stars and reaching the larger ($>100$ pc) scales traced at lower resolution.

- We compare the candidate SSCs in NGC 4945 with the (proto-)SSCs recently identified in the central starburst of NGC 253 (cite: Leroy2018; Mills2020). The age of the burst (1 Myr) is a bit younger in NGC 253, the gas mass fractions ($\sim$0.5) are a bit higher, and the stellar mass of the clusters are slightly smaller (factor of 3.5). While the actively forming clusters are not a major contributor to the starburst driven outflow in NGC 253, the slightly older population of the star clusters in NGC 4945 may contribute to driving a nuclear outflow of warm ionized gas.

- Strong, variable X-ray emission, which is Compton thick, provides evidence for a Seyfert AGN in NGC 4945. The bright, 93 GHz source which we presume to be the AGN is point-like in our 2.2 pc beam. We measure its in-band spectral index at 93 GHz to be $\alpha_{93} = -0.85 \pm 0.05$, likely dominated by synchrotron emission. We do not detect recombination line emission from this point source. Our observations support previous findings in which UV ionizing radiation from the AGN is heavily obscured in all directions. We estimate an upper limit for its escaping ionizing photon rate of $Q_0 < 1 \times 10^{52}$ s$^{-1}$, which is $\lesssim 10$% of the expected luminosity of ionizing photons for a typical Seyfert AGN.

- Lastly, we report on a shortcoming of H42$\alpha$ as a “low-resolution” tracer of ionizing radiation. When observed with low spatial resolution and/or from broad line components, we find this spectral line is likely contaminated by line emission from other species, resulting in the recombination line flux (and star-formation rates derived from it) being overestimated by a factor of $\sim$2, when compared to a similar analysis of H40$\alpha$.

# Acknowledgments

The authors thank the anonymous referee for the careful review of the article and helpful input. We also thank Emil Lenc for providing the Australian LBA 2.3 GHz data and Paul van der Werf for the HST Pa-$\alpha$ data.

KLE acknowledges financial support from the Netherlands Organization for Scientific Research (NWO) through TOP grant 614.001.351. KLE thanks the Laboratory for Millimeter Wave Astronomy and the Department of Astronomy at the University of Maryland and the Green Bank Observatory for hosting her during completion of this work. ADB and RCL acknowledge support from NSF through grants AST-1412419 and AST-1615960. AKL acknowledges support by the National Science Foundation (NSF) under Grants No.1615105, 1615109, and 1653300, as well as by the National Aeronautics and Space Administration (NASA) under ADAP grants NNX16AF48G and NNX17AF39G. EACM gratefully acknowledges support by the National Science Foundation under grant No. AST-1813765. ER acknowledges the support of the Natural Sciences and Engineering Research Council of Canada (NSERC), funding reference number RGPIN-2017-03987.

This article makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01236.S, and ADS/JAO.ALMA#2016.1.01135.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

ALMA, Australian LBA, HST

# Software

APLpy (cite: Robitaille2012), Astropy (cite: Astropy2018), CASA (cite: McMullin2007), CRRLpy (cite: Salas2016), Matplotlib (cite: Hunter2007), PyBDSF (cite: Mohan2015).

natexlab

(ref: Adamo2016) Adamo, A., & Bastian, N. 2016, in Orig Stellar Clust, ed. S. Stahler (Springer), 27. [`https://arxiv.org/abs/1511.08212`](https://arxiv.org/abs/1511.08212)

(ref: Adamo2015) Adamo, A., Kruijssen, J. M. D., Bastian, N., Silva-Villa, E., & Ryon, J. 2015, MNRAS, 452, 246, doi: [`10.1093/mnras/stv1203`](http://doi.org/10.1093/mnras/stv1203)

(ref: Adamo2011) Adamo, A., Ostlin, G., Zackrisson, E., et al. 2011, MNRAS, 415, 2388, doi: [`10.1111/j.1365-2966.2011.18867.x`](http://doi.org/10.1111/j.1365-2966.2011.18867.x)

(ref: Bendo2015) Bendo, G. J., Beswick, R. J., D’Cruze, M. J., et al. 2015, Mon Not R Astron Soc Lett, 450, L80, doi: [`10.1093/mnrasl/slv053`](http://doi.org/10.1093/mnrasl/slv053)

(ref: Bendo2016) Bendo, G. J., Henkel, C., D’Cruze, M. J., et al. 2016, MNRAS, 463, 252, doi: [`10.1093/mnras/stw1659`](http://doi.org/10.1093/mnras/stw1659)

(ref: Bolatto2013) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013, Natur, 499, 450

(ref: Bressert2012) Bressert, E., Ginsburg, A., Bally, J., et al. 2012, ApJL, 758, L28, doi: [`10.1088/2041-8205/758/2/L28`](http://doi.org/10.1088/2041-8205/758/2/L28)

(ref: Brocklehurst1972) Brocklehurst, M., & Seaton, M. J. 1972, MNRAS, 157, 179

(ref: Chandar2017) Chandar, R., Fall, S. M., Whitmore, B. C., & Mulia, A. J. 2017, ApJ, 849, 128, doi: [`10.3847/1538-4357/aa92ce`](http://doi.org/10.3847/1538-4357/aa92ce)

(ref: Chou2007) Chou, R. C. Y., Peck, A. B., Lim, J., et al. 2007, ApJ, 670, 116, doi: [`10.1086/521351`](http://doi.org/10.1086/521351)

(ref: Condon1992a) Condon, J. J. 1992, ARAA, 30, 575, doi: [`10.1146/annurev.aa.30.090192.003043`](http://doi.org/10.1146/annurev.aa.30.090192.003043)

(ref: Condon2016) Condon, J. J., & Ransom, S. M. 2016, Essential Radio Astronomy (Prinston, NJ: Princeton University Press), 361. <https://ui.adsabs.harvard.edu/abs/2016era..book.....C/abstract>

(ref: Dale2015) Dale, J. E., Ercolano, B., Bonnell, I. A., et al. 2015, MNRAS, 451, 987, doi: [`10.1093/mnras/stv913`](http://doi.org/10.1093/mnras/stv913)

(ref: DePree1996) de Pree, C. G., Gaume, R. A., Goss, W. M., & Claussen, M. J. 1996, ApJ, 464, 788, doi: [`10.1086/177364`](http://doi.org/10.1086/177364)

(ref: Draine2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium (Princeton University Press), 510

(ref: Eisner2019) Eisner, B. A., Ott, J., Meier, D. S., & Cannon, J. M. 2019, ApJ, 882, 95, doi: [`10.3847/1538-4357/AB3854`](http://doi.org/10.3847/1538-4357/AB3854)

(ref: Elvis1994) Elvis, M., Wilkes, B. J., McDowell, J. C., et al. 1994, ApJSS, 95, 1, doi: [`10.1086/192093`](http://doi.org/10.1086/192093)

(ref: Ginsburg2018b) Ginsburg, A., & Kruijssen, J. M. D. 2018, ApJL, 864, L17, doi: [`10.3847/2041-8213/aada89`](http://doi.org/10.3847/2041-8213/aada89)

(ref: Ginsburg2016) Ginsburg, A., Goss, W. M., Goddi, C., et al. 2016, A&A, 595, 27, doi: [`10.1051/0004-6361/201628318`](http://doi.org/10.1051/0004-6361/201628318)

(ref: Ginsburg2018a) Ginsburg, A., Bally, J., Barnes, A., et al. 2018, ApJ, 853, 171, doi: [`10.3847/1538-4357/aaa6d4`](http://doi.org/10.3847/1538-4357/aaa6d4)

(ref: Ginsburg2020) Ginsburg, A., Anderson, L. D., Dicker, S., et al. 2020, ApJSS, 248, 24, doi: [`10.3847/1538-4365/ab8b5c`](http://doi.org/10.3847/1538-4365/ab8b5c)

(ref: Goddard2010) Goddard, Q. E., Bastian, N., & Kennicutt, R. C. 2010, MNRAS, 405, 857, doi: [`10.1111/j.1365-2966.2010.16511.x`](http://doi.org/10.1111/j.1365-2966.2010.16511.x)

(ref: Gordon2009) Gordon, M. A., & Sorochenko, R. L. 2009, Radio Recombination Lines. Their Physics and Astronomical Applications (Kluwer Academic Publishers, Dordrecht)

(ref: Gorski2017) Gorski, M., Ott, J., Rand, R., et al. 2017, ApJ, 842, 124, doi: [`10.3847/1538-4357/aa74af`](http://doi.org/10.3847/1538-4357/aa74af)

(ref: Greenhill1997) Greenhill, L. J., Moran, J. M., & Herrnstein, J. R. 1997, ApJ, 481, L23, doi: [`10.1086/310643`](http://doi.org/10.1086/310643)

(ref: Heckman1990) Heckman, T. M., Armus, L., & Miley, G. K. 1990, ApJSS, 74, 833, doi: [`10.1086/191522`](http://doi.org/10.1086/191522)

(ref: Henkel2018) Henkel, C., Muehle, S., Bendo, G., et al. 2018, A&A, 615, 155, doi: [`10.1051/0004-6361/201732174`](http://doi.org/10.1051/0004-6361/201732174)

(ref: Hopkins2007) Hopkins, P. F., Richards, G. T., & Hernquist, L. 2007, ApJ, 654, 731, doi: [`10.1086/509629`](http://doi.org/10.1086/509629)

(ref: Hunter2007) Hunter, J. D. 2007, Comput Sci Eng, 9, 90

(ref: Johnson2016) Johnson, L. C., Seth, A. C., Dalcanton, J. J., et al. 2016, ApJ, 827, 33, doi: [`10.3847/0004-637X/827/1/33`](http://doi.org/10.3847/0004-637X/827/1/33)

(ref: Karachentsev2007) Karachentsev, I. D., Tully, R. B., Dolphin, A., et al. 2007, AJ, 133, 504, doi: [`10.1086/510125`](http://doi.org/10.1086/510125)

(ref: Kessler1996) Kessler, M. F., Steinz, J. A., Anderegg, M. E., et al. 1996, A&A, 500, 493. [https://ui.adsabs.harvard.edu/abs/1996A%26A...315L..27K/abstract](https://ui.adsabs.harvard.edu/abs/1996A{%}26A...315L..27K/abstract)

(ref: Kim2015) Kim, C.-G., & Ostriker, E. C. 2015, ApJ, 802, 99, doi: [`10.1088/0004-637X/802/2/99`](http://doi.org/10.1088/0004-637X/802/2/99)

(ref: Klein2018a) Klein, U., Lisenfeld, U., & Verley, S. 2018, A&A, 611, 55, doi: [`10.1051/0004-6361/201731673`](http://doi.org/10.1051/0004-6361/201731673)

(ref: Krause2016) Krause, M. G. H., Charbonnel, C., Bastian, N., & Diehl, R. 2016, A&A, 587, 53, doi: [`10.1051/0004-6361/201526685`](http://doi.org/10.1051/0004-6361/201526685)

(ref: Krause2020) Krause, M. G. H., Offner, S. S. R., Charbonnel, C., et al. 2020, Space Sci Rev, 216, 64, doi: [`10.1007/s11214-020-00689-4`](http://doi.org/10.1007/s11214-020-00689-4)

(ref: Krieger2019) Krieger, N., Bolatto, A. D., Walter, F., et al. 2019, ApJ, 881, 43, doi: [`10.3847/1538-4357/ab2d9c`](http://doi.org/10.3847/1538-4357/ab2d9c)

(ref: Kroupa2001) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Kruijssen2012) Kruijssen, J. M. D. 2012, MNRAS, 426, 3008, doi: [`10.1111/j.1365-2966.2012.21923.x`](http://doi.org/10.1111/j.1365-2966.2012.21923.x)

(ref: Lada2003) Lada, C. J., & Lada, E. A. 2003, ARAA, 41, 57, doi: [`10.1146/annurev.astro.41.011802.094844`](http://doi.org/10.1146/annurev.astro.41.011802.094844)

(ref: Leitherer1999) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 3

(ref: Lenc2009) Lenc, E., & Tingay, S. J. 2009, AJ, 137, 537, doi: [`10.1088/0004-6256/137/1/537`](http://doi.org/10.1088/0004-6256/137/1/537)

(ref: Leroy2018) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2018, ApJ, 896, 126. [`https://arxiv.org/abs/arXiv:1804.02083v1`](https://arxiv.org/abs/arXiv:1804.02083v1)

(ref: Li2019) Li, H., Vogelsberger, M., Marinacci, F., & Gnedin, O. Y. 2019, MNRAS, 487, 364, doi: [`10.1093/mnras/stz1271`](http://doi.org/10.1093/mnras/stz1271)

(ref: Linden2020) Linden, S. T., Murphy, E. J., Dong, D., et al. 2020, ApJSS, 248, 25, doi: [`10.3847/1538-4365/ab8a4d`](http://doi.org/10.3847/1538-4365/ab8a4d)

(ref: Linden2017) Linden, S. T., Evans, A. S., Rich, J., et al. 2017, ApJ, 843, 91, doi: [`10.3847/1538-4357/aa7266`](http://doi.org/10.3847/1538-4357/aa7266)

(ref: Longmore2014) Longmore, S. N., Kruijssen, J. M. D., Bastian, N., et al. 2014, in Protostars Planets VI (University of Arizona Press), 291

(ref: Lucas2000) Lucas, R., & Liszt, H. S. 2000, A&A, 358, 1069. [https://ui.adsabs.harvard.edu/abs/2000A%26A...358.1069L/abstract](https://ui.adsabs.harvard.edu/abs/2000A{%}26A...358.1069L/abstract)

(ref: Madau2014) Madau, P., & Dickinson, M. 2014, ARAA, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Marchesi2018) Marchesi, S., Ajello, M., Marcotulli, L., et al. 2018, ApJ, 854, 49, doi: [`10.3847/1538-4357/aaa410`](http://doi.org/10.3847/1538-4357/aaa410)

(ref: Marconi2000) Marconi, A., Oliva, E., van der Werf, P. P., et al. 2000, A&A, 357, 24. [https://ui.adsabs.harvard.edu/abs/2000A%26A...357...24M/abstract](https://ui.adsabs.harvard.edu/abs/2000A{%}26A...357...24M/abstract)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astron Data Anal Softw Syst XVI ASP Conf Ser, Vol. 376 (Astronomical Society of the Pacific), 127

(ref: Mills2020) Mills, E. A. C., Gorski, M., Bolatto, A. D., et al. 2020, ApJ, submitted

(ref: Mingozzi2019) Mingozzi, M., Cresci, G., Venturi, G., et al. 2019, A&A, 622, 146, doi: [`10.1051/0004-6361/201834372`](http://doi.org/10.1051/0004-6361/201834372)

(ref: Mohan2015) Mohan, N., & Rafferty, D. 2015, PyBDSF: Python Blob Detection and Source Finder, doi: [`2015ascl.soft02007M`](http://doi.org/2015ascl.soft02007M)

(ref: Mok2020) Mok, A., Chandar, R., & Fall, S. M. 2020, ApJ. [`https://arxiv.org/abs/2004.02698`](https://arxiv.org/abs/2004.02698)

(ref: Moorwood1996) Moorwood, A. F. M., van der Werf, P. P., Kotilainen, J. K., Marconi, A., & Oliva, E. 1996, A&A, 308, L1. [https://ui.adsabs.harvard.edu/abs/1996A%26A...308L...1M/abstract](https://ui.adsabs.harvard.edu/abs/1996A{%}26A...308L...1M/abstract)

(ref: Murphy2018a) Murphy, E. J., Dong, D., Momjian, E., et al. 2018, ApJSS, 234, 24, doi: [`10.3847/1538-4365/aa99d7`](http://doi.org/10.3847/1538-4365/aa99d7)

(ref: Niklas1997) Niklas, S., Klein, U., & Wielebinski, R. 1997, A&A, 322, 19. [https://ui.adsabs.harvard.edu/abs/1997A%26A...322...19N/abstract](https://ui.adsabs.harvard.edu/abs/1997A{%}26A...322...19N/abstract)

(ref: Ossenkopf1994) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943. [https://ui.adsabs.harvard.edu/abs/1994A%26A...291..943O/abstract](https://ui.adsabs.harvard.edu/abs/1994A{%}26A...291..943O/abstract)

(ref: Oster1961) Oster, L. 1961, Rev Mod Phys, 33, 525

(ref: PortegiesZwart2010) Portegies Zwart, S. F., McMillan, S. L. W., & Gieles, M. 2010, ARAA, 48, 431, doi: [`10.1146/annurev-astro-081309-130834`](http://doi.org/10.1146/annurev-astro-081309-130834)

(ref: Rekola2005) Rekola, R., Richer, M. G., McCall, M. L., et al. 2005, MNRAS, 361, 330, doi: [`10.1111/j.1365-2966.2005.09166.x`](http://doi.org/10.1111/j.1365-2966.2005.09166.x)

(ref: Rico-Villas2020) Rico-Villas, F., Martín-Pintado, J., González-Alfonso, E., Martín, S., & Rivilla, V. M. 2020, MNRAS, 491, 4573, doi: [`10.1093/mnras/stz3347`](http://doi.org/10.1093/mnras/stz3347)

(ref: Robitaille2012) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python. <http://adsabs.harvard.edu/abs/2012ascl.soft08017R>

(ref: Roelfsema1992) Roelfsema, P. R., & Goss, W. M. 1992, Astron Astrophys Rev, 4, 161

(ref: Roy2010) Roy, A. L., Oosterloo, T., Goss, W. M., & Anantharamaiah, K. R. 2010, Astron Astrophys, 517, A82, doi: [`10.1051/0004-6361/200913926`](http://doi.org/10.1051/0004-6361/200913926)

(ref: Ryon2014) Ryon, J. E., Adamo, A., Bastian, N., et al. 2014, AJ, 148, 33, doi: [`10.1088/0004-6256/148/2/33`](http://doi.org/10.1088/0004-6256/148/2/33)

(ref: Ryon2017) Ryon, J. E., Gallagher, J. S., Smith, L. J., et al. 2017, ApJ, 841, 92

(ref: Salas2016) Salas, P., Morabito, L., Salgado, F., Oonk, J. B. R., & Tielens, A. G. G. M. 2016, CRRLpy: First Pre-release. <http://dx.doi.org/10.5281/zenodo.44598>

(ref: Shaver1983) Shaver, P. A., McGee, R. X., Newton, L. M., Danks, A. C., & Pottasch, S. R. 1983, MNRAS, 204, 53, doi: [`10.1093/mnras/204.1.53`](http://doi.org/10.1093/mnras/204.1.53)

(ref: Spoon2000) Spoon, H. W. W., Koornneef, J., Moorwood, A. F. M., Lutz, D., & Tielens, A. G. G. M. 2000, A&A, 357, 898

(ref: Stanghellini2015) Stanghellini, L., Magrini, L., & Casasola, V. 2015, Astrphysical J, 812, 39, doi: [`10.1088/0004-637X/812/1/39`](http://doi.org/10.1088/0004-637X/812/1/39)

(ref: Storey1995) Storey, P. J., & Hummer, D. G. 1995, MNRAS, 272, 41

(ref: Astropy2018) The Astropy Collaboration. 2018, AJ, 156, 123. [`https://arxiv.org/abs/1801.02634`](https://arxiv.org/abs/1801.02634)

(ref: Whitmore2010) Whitmore, B. C., Chandar, R., Schweizer, F., et al. 2010, AJ, 140, 75, doi: [`10.1088/0004-6256/140/1/75`](http://doi.org/10.1088/0004-6256/140/1/75)

(ref: Wilson2008) Wilson, C. D., Petitpas, G. R., Iono, D., et al. 2008, ApJSS, 178, 189, doi: [`10.1086/590910`](http://doi.org/10.1086/590910)

(ref: Zhang1999) Zhang, Q., & Fall, S. M. 1999, ApJL, 527, L81, doi: [`10.1086/312412`](http://doi.org/10.1086/312412)

# Millimeter wavelength emission from free-free continuum and recombination lines

In this section we present the relations for the recombination line intensity and free-free continuum applicable for millimeter wavelength emission, largely by bringing together information derived in (cite: Gordon2009) and (cite: Draine2011). We show how these relations can be used to estimate the temperature and ionizing photon rate of the emitting plasma.

At frequencies of $\mathcal{O}$(10 GHz), the electron temperature $T_e$ of the thermal emission from ionized gas accurately characterizes the relative populations of electrons in bound atomic levels, and the system is well approximated by local thermodynamic equilibrium (LTE). Collisions dominate and line emission is described by the Boltzmann distribution.

As the collisional cross section of a Bohr atom rapidly decreases ($\propto \mathsf{n}^{4}$) towards smaller principal quantum numbers, or higher frequencies of $\mathcal{O}$(100 GHz), collisions become less important, and the observed line intensity is not exactly set by the kinetic motion of the electrons. Radiative processes, which dominate the smallest principal quantum numbers, influence the level populations; smaller $\mathsf{n}$ are underpopulated as compared with a Boltzmann distribution. The population rates into an energy level are not exactly balanced by rates out of the level, and a correction coefficient ($b_{\mathsf{n}}$) for a departure from LTE is necessary.

## Recombination Line Intensity

Considering Kirchoff’s law of thermodynamics with no net change in intensity through the medium, the emission of a radio recombination line in LTE, $S_{\mathsf{n}} (\mathrm{LTE})$, is related to $\kappa_{\mathsf{n}}$, the fractional absorption per unit pathlength $\ell$, for small line optical depths by $$\begin{equation}
    S_{\mathsf{n}} (\mathrm{LTE}) \approx \kappa_{\mathsf{n}} \, \ell \, B_{\nu}(T_e) \, \Omega
\end{equation}$$ for a transition to final principal quantum number $\mathsf{n}$, where $B_{\nu}$ is the Planck function and $\Omega$ is the solid angle on the sky. For small optical depths of the line and the free-free continuum $\tau_{\mathrm{c}}$, the non-LTE line flux density is, by definition, $$\begin{equation}
    S_{\mathsf{n}} \approx S_{\mathsf{n}}(LTE) b_{\mathsf{n+1}}  \left( 1 + \frac{\tau_C}{2} \beta \right).
\end{equation}$$ Here, $b_{\mathsf{n+1}}$ is the departure coefficient, which is defined as $b_{\mathsf{n}} = n / n_{\mathrm{LTE}}$, the ratio of the actual number density of atoms with an electron in level $\mathsf{n}$ to the number which would be there if the population were in LTE at the temperature of the ionized gas, such that for LTE, $b_{\mathsf{n}} = 1$. $\beta$ is the departure coefficient which accounts for stimulated emission. The second term in parenthesis is usually negligible at millimeter wavelengths, such that $(1 + 0.5\tau_c \beta) \approx 1$. In Eq. [\[aeq:kappac\]](#aeq:kappac) of Section [8.2](#ap:cont), the absorption coefficient of the free-free continuum is given and the optical depth can be derived to show that typical parameters (e.g. $EM_l = 10^7$ cm$^{-6}$ pc and $T_e = 10^4$ K) of ionized regions around massive stars result in $\tau_c \lesssim 3 \times 10^{-6}$ at 100 GHz. Typical values of $\beta$ for $\mathsf{n} \gtrsim 40$ are $\left| \beta \right| \lesssim 40$ (cite: Storey1995).

In its expanded form, the LTE absorption coefficient of a radio recombination line can be expressed in terms of the Saha-Boltzmann distribution, oscillator strength, and line frequency as $$\begin{equation}
    \kappa_{\mathsf{n}} \approx 
    n_e n_+ \frac{2}{\sqrt{\pi}} \frac{e^2}{m_e} 
    \left( \frac{ h^2}{2 m_e k_B }\right)^{3/2} 
    \frac{h}{k_B }~T_e^{-2.5} R_H Z^2 \Delta \mathsf{n} 
    \left( 1 - \frac{3}{2} \frac{\Delta \mathsf{n}}{\mathsf{n}} \right) 
    \exp\left( \frac{ \chi_{\mathsf{n}} }{ k_B T_e} \right)
    M(\Delta \mathsf{n}) 
    \left( 1 + \frac{3}{2} \frac{\Delta \mathsf{n}}{\mathsf{n}} \right)
    \phi_{\nu}
\end{equation}$$ where $n_e$ and $n_+$ are the number densities of electrons and ions respectively; $R_H$ is the Rydberg constant for hydrogen; $Z$ is the effective nuclear charge; $\Delta \mathsf{n}$ is the change in energy levels of the given transition; $\chi_{\mathsf{n}}$ is the energy required to ionized the atom from state $\mathsf{n}$, but $\exp\left(\chi_{\mathsf{n}}/ k_{B}T_e \right)$ is small $(<1.02)$ for $\mathsf{n} \geq$ 40 and typical ionized gas temperatures; $M(\Delta \mathsf{n} = 1,2) = 0.190775, 0.026332$ is an approximation factor for the oscillator strength; and, $\phi_{\nu}$ is the line profile (normalization; in SI units, Hz$^{-1}$) such that $\int_{-\infty}^{\infty} \phi_{\nu}~\mathrm{d}\nu = 1$.

Bringing the above equations together, using the Rayleigh-Jeans approximation of the Planck function, and integrating over the line profile, we arrive at the expression for the integrated line flux density, $$\begin{equation}
    \int S_{\mathsf{n}} \, \mathrm{dv} =  
    \left( 65.13~\mathrm{mJy~km~s^{-1}}\right) 
    b_{\mathsf{n+1}} 
    \left( \frac{n_e n_p V }{ 5\times10^8~\mathrm{cm^{-6}~pc^3} }\right) 
    \left( \frac{ D }{ 3.8~\mathrm{Mpc} }\right)^{-2}
    \left( \frac{ T_e }{ 10^4~\mathrm{K} } \right)^{-1.5} 
    \left( \frac{\nu}{100~\mathrm{GHz}} \right)
\end{equation}$$ where we take $n_+ = n_p$, $Z = 1$, and $\Delta \mathsf{n} = 1$. For convenience and self consistency, we express the emission measure in terms of source volume, $V$, and the solid angle in terms of distance to the source, $D$. Let $\Omega = \frac{ \pi r^2 }{D^2}$, where $r$ is the radius of the region, and if we let $\ell = \frac{4}{3} r$, the volumetric emission measure is given as $EM_{V} = n_e n_p V$ where $V = \frac{4}{3} \pi r^3$.

## Continuum Intensity

The absorption coefficient for free-free continuum (cite: Oster1961) in the Rayleigh-Jeans limit is, as a function of frequency, $$\begin{equation}
    \kappa_{\mathrm{c}} =  \frac{ n_e n_+ }{ \nu^2 } \frac{ 8 Z^2 e^6 }{3 \sqrt{3} m_e^3 c} \left( \frac{ \pi }{ 2 } \right)^{1/2} \left( \frac{m_e}{k_B T_e} \right)^{3/2} g_{\mathrm{ff}} 
\label{aeq:kappac}
\end{equation}$$ where the gaunt free-free factor is (cite: Draine2011) $$\begin{equation}
    g_{\mathrm{ff}} \approx 13.91 \left( Z \frac{\nu}{ \mathrm{Hz} } \right)^{-0.118} \left( \frac{T_e}{\mathrm{K}} \right)^{0.177}
\end{equation}$$ valid for $\nu_p \ll \nu \ll kT_e/ h$ where the plasma frequency is $\nu_p = 8.98(n_e /\mathrm{cm}^{-3})^{1/2}$ kHz, and to within 10% when $1.4 \times 10^{-4} < Z \nu T_e^{-1.5} < 0.25$.

The continuum intensity for an optically thin medium is $$\begin{equation}
    S_{\mathrm{c}} \approx B_{\nu} \, \kappa_{\mathrm{c}} \, \ell \, \Omega .
\end{equation}$$ As we did for the line intensity, we can also express the above relation in terms of distance $D$ and the volumetric emission measure of the region $EM_V = n_e n_p V$ where $V = \frac{4}{3} \pi r^3$: $$\begin{equation}
    S_{c} = (2.080~\mathrm{mJy} ) 
    \, Z^{1.882}
    \left( \frac{ n_e n_+ V }{ 5\times10^8~\mathrm{cm^{-6}~pc^3} } \right) 
    \left( \frac{ D }{ 3.8~\mathrm{Mpc} } \right)^{-2} 
    \left(  \frac{T_e}{ 10^4~\mathrm{K}} \right)^{-0.323} 
    \left( \frac{\nu}{ 100~\mathrm{GHz} } \right)^{-0.118} 
\label{aeq:cont}
\end{equation}$$ evaluated in the Rayleigh-Jeans limit.

## Physical Properties

### Line to Continuum Ratio and Temperature

Using the previous expressions, the ratio between the RRL and continuum flux density is: $$\begin{equation}
\frac{ \int S_{\mathsf{n}}~\mathrm{dv} }{S_{\mathrm{c}}} = 
    \left( 31.31~\mathrm{km~s^{-1}} \right) 
    b_{\mathsf{n+1}} 
    \left( \frac{ T_e }{ 10^4~\mathrm{K} } \right)^{-1.177} 
    \left( 1 + y \right)^{-1}
    \left( \frac{\nu}{100~\mathrm{GHz}} \right)^{1.118}
\label{aeq:lc_ratio}
\end{equation}$$ where $y = n_{\mathrm{He^+}} / n_p$ is the ratio of singly ionized helium to hydrogen by number and $n_{\mathrm{He^+}}$ is the singly ionized helium number density. If we assume the emission region is composed of only hydrogen and singly ionized helium, then $$\begin{equation}
    \frac{ n_p }{ n_+} = \frac{ n_p }{ n_p + n_{\mathrm{He^+}} } = \left(  1 + \frac{ n_{\mathrm{He^+}} }{ n_p } \right)^{-1} = \left( 1 + y \right)^{-1}.
\end{equation}$$ We can rearrange the integrated RRL line to continuum ratio and solve for the electron temperature $T_e$ of the emission region, $$\begin{equation}
    T_e = 10^4~\mathrm{K}
    \left[ b_{\mathsf{n+1}} 
    \left( 1 + y \right)^{-1}
    \left( \frac{ R_{\mathrm{lc}} }{ 31.31~\mathrm{km~s^{-1}} } \right)^{-1}
    \left( \frac{\nu}{100~\mathrm{GHz}} \right)^{1.118} \right]^{0.85}
\label{aeq:temp}
\end{equation}$$ where we denote the integrated RRL line to continuum ratio as $R_{\mathrm{lc}} = \frac{ \int S_{\mathsf{n}}~\mathrm{dv} }{ S_{\mathrm{c}} }$.

### Ionizing Photon Rate

The rate of ionizing photons ($E>13.6 eV$) is given by, $$\begin{equation}
    Q_0 = n_e n_+ V \alpha_B
\end{equation}$$ where $\alpha_B$ is the case B recombination coefficient (cite: Draine2011), $$\begin{equation}
    \alpha_B =  2.59 \times 10^{-13} ~\mathrm{cm^3~s^{-1}} \left( \frac{ T_e }{ 10^4~\mathrm{K} } \right)^{-0.833 - 0.034 \ln{(T_e\,/\,10^4\,\mathrm{K})} }
\end{equation}$$ which is valid for 3000 K $< T_e <$ 30,000 K. Thus we have, $$\begin{equation}
    Q_0 = \left( 3.805 \times 10^{51}~\mathrm{s}^{-1} \right) \left( \frac{ n_e n_+ V }{ 5 \times 10^8~\mathrm{cm^{-6}~pc^3} } \right) \left( \frac{ T_e }{ 10^4~\mathrm{K} } \right)^{-0.833 - 0.034 \ln{(T_e\,/\,10^4\,\mathrm{K})} }.
\label{aeq:q}
\end{equation}$$

# Recombination Line Spectra of all Sources

In Figure [12](#fig:ap_allspec), we show that the central velocities of our detected recombination lines are in good agreement with the kinematic velocity expected of the disk rotation, though we include the recombination line spectra for all 29 sources (including those that are not significantly detected). The recombination line spectra from our sources are overlaid on H40$\alpha$ spectra extracted from the intermediate configuration observations (0.7$''$ resolution). High-resolution recombination line emission is coincident with emission from the intermediate configuration data.

![](specrta_lowres_overlay_r16SC4_app_v2_0.pdf)

![](specrta_lowres_overlay_r16SC4_app_v2_1.pdf)

# Spectral Energy distribution of all Sources

![](SEDs_all_r16SC4_v2_0.pdf)

![](SEDs_all_r16SC4_v2_1.pdf)

[^1]:

</paper>

Write the methods card for this paper.