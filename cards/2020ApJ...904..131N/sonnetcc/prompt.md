# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...904..131N\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2020ApJ...904..131N",
 "title": "No Evidence for [C II] Halos or High-velocity Outflows in z ≳ 6 Quasar Host Galaxies",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "Novak, Mladen",
 "n_authors": 16,
 "arxiv_id": "2010.14875",
 "doi": "10.3847/1538-4357/abc33f",
 "alma_projects_linked_by_archive": [
  "2012.1.00240.S",
  "2012.1.00882.S",
  "2013.1.00273.S",
  "2015.1.00399.S",
  "2015.1.00606.S",
  "2015.1.00692.S",
  "2015.1.00997.S",
  "2015.1.01115.S",
  "2016.1.00544.S",
  "2016.A.00018.S",
  "2017.1.00396.S",
  "2017.1.01301.S",
  "2018.1.00908.S"
 ]
}
```

Paper text:
<paper>
# **No evidence for $\text{\textsc{[C ii]}}$ halos or high-velocity outflows in $z \gtrsim 6$ quasar host galaxies**

## Abstract

We study the interstellar medium in a sample of 27 high-redshift quasar host galaxies at $z\gtrsim6$, using the $\text{\textsc{[C ii]}}$ 158 $\mu$m emission line and the underlying dust continuum observed at $\sim1$ kpc resolution with ALMA. By performing $uv$-plane spectral stacking of both the high and low spatial resolution data, we investigate the spatial and velocity extent of gas, and the size of the dust-emitting regions. We find that the average surface brightness profile of both the $\text{\textsc{[C ii]}}$ and the dust continuum emission can be described by a steep component within a radius of 2 kpc, and a shallower component with a scale length of 2 kpc, detected up to $\sim$10 kpc. The surface brightness of the extended emission drops below $\sim$1% of the peak at radius of $\sim5$ kpc, beyond which it constitutes 10 – 20% of the total measured flux density. Although the central component of the dust continuum emission is more compact than that of the $\text{\textsc{[C ii]}}$ emission, the extended components have equivalent profiles. The observed extended components are consistent with those predicted by hydrodynamical simulations of galaxies with similar infrared luminosities, where the dust emission is powered by star formation. The $\text{\textsc{[C ii]}}$ spectrum measured in the mean $uv$-plane stacked data can be described by a single Gaussian, with no observable $\text{\textsc{[C ii]}}$ broad-line emission (velocities in excess of $\gtrsim 500$ $\text{km\,s}^{-1}$), that would be indicative of outflows. Our findings suggest that we are probing the interstellar medium and associated star formation in the quasar host galaxies up to radii of 10 kpc, whereas we find no evidence for halos or outflows.

# Introduction

Quasars and their hosts are ideal targets to probe the properties of massive high-redshift galaxies. Powered by the rapid accretion of material, near the Eddington limit, onto a supermassive black hole (cite: derosa11; derosa14; willott10a), quasars within the first Gyr of the Universe ($z>6$) are easily detected by current facilities. Several hundred quasars have now been identified at $z>5.5$, owing to both large surveys (cite: york00; arnaboldi07; lawrence07; chambers16), and improved selection methods with follow-up observations (cite: fan06; venemans07; willott10a; mortlock11; morganson12; banados16; jiang16; mazzucchelli17; matsuoka18; banados18; wangfeige18; yang20).

At $z\sim6$, the singly ionized carbon emission line at 158 $\mu$m, arising from the ${}^2P_{3/2} \rightarrow {}^2P_{1/2}$ transition (hereafter referred to as the $\text{\textsc{[C ii]}}$ line) falls conveniently within the atmospheric transition window of ground based interferometers such as the Atacama Large Millimeter Array (ALMA) and the NOrthern Extended Millimeter Array (NOEMA). This emission line is one of the brightest far-infrared (FIR) emission lines and can be used to trace the cold molecular gas of the interstellar medium (ISM, see (cite: carilliwalter13) for a review of high-redshift galaxies). The line predominantly arises from within the photodissociation regions (PDRs) found around newly formed stars, although it can also stem from ionized regions (cite: hollenbach99; vallini17; ferrara19). The $\text{\textsc{[C ii]}}$ line has been used to probe the gas distribution and kinematics on kpc scales for dozens of quasar host galaxies, simultaneously providing precise redshift measurements (cite: walter09; maiolino12; wang13; willott15; venemans17b; venemans17c; decarli18; neeleman19).

Detections of large-scale $\text{\textsc{[C ii]}}$ emission and outflows in a high-redshift quasar host galaxy were first reported for the $z=6.4$ system SDSS J1148+5251 (cite: maiolino12; cicone15). However, further statistical studies of $\text{\textsc{[C ii]}}$ outflows in various, partly overlapping, samples of $z>4.5$ quasar host galaxies remain without consensus. Some studies report tentative or strong evidence for outflows (cite: bischetti19; stanley19), whereas other studies reported no outflows (cite: decarli18). However, different image plane stacking techniques were used among the different studies.

We revisit this topic by using the deepest available ALMA data and novel analysis techniques. In this study, we conduct a multi-resolution analysis of 27 quasar host galaxies at $z \gtrsim 6$ observed with ALMA in order to search for signatures of extended $\text{\textsc{[C ii]}}$ emission and outflows. We require $\sim1\,$kpc imaging capability in order to accurately derive surface brightness profiles, but complement our data with lower spatial resolution observations of the same sources to minimize potential issues of missing flux and outresolving sources. For the spectral analysis, we use a novel technique of spectral $uv$-plane stacking. By directly averaging observed visibilities of the sample of galaxies, in velocity bins of interest, we circumvent various problems present in interferometric image-based stacking (e.g. dirty beam residuals and beam matching), simultaneously ensuring that emission on multiple spatial scales can be recovered in the imaging step.

This is the third paper in a series of studies, in which different aspects of the quasar host galaxies observed in $\text{\textsc{[C ii]}}$ at $\sim1$ kpc resolution are discussed. The first paper, (cite: venemans20), describes the sample in detail and provides the analysis of both the $\text{\textsc{[C ii]}}$ and the dust continuum emission of individual galaxies. The second paper, (cite: neeleman20b), capitalizes on the high resolution of these observations by modeling the gas kinematics of the host galaxies, yielding rotation and/or dispersion velocities, and estimates of the dynamical masses of the hosts. These two studies investigate properties of individual galaxies, making use of the brightest emitting regions, where there is sufficient signal. In this paper, we perform stacking and $uv$-plane analysis to constrain the amount of faint, but extended (both spatially and spectrally), emission, that is below the detection threshold of individual objects.

The paper is structured as follows. In Section [2](#sec:data), we present the sample of $z\gtrsim6$ quasar host galaxies along with the new and archival ALMA data. We also describe the data reduction steps, along with the details of the $uv$-stacking procedure. In Section [3](#sec:methods), we elaborate on the methods for accurately measuring fluxes, both from the image, and the $uv$-plane. In Section [4](#sec:res), we present the results in three subsections, focusing on the 1) spatial extent of the $\text{\textsc{[C ii]}}$ emission, 2) spatial extent of the dust continuum, and 3) spectral analysis of the $\text{\textsc{[C ii]}}$ line. We interpret and discuss our findings in the context of published studies in Section [5](#sec:disc), and summarize our main conclusions in Section [6](#sec:conc).

Throughout the paper we assume the concordance Lambda cold dark matter ($\Lambda$CDM) cosmology, defined by a Hubble constant $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, dark energy density $\Omega_\Lambda=0.7$, and matter density $\Omega_{\mathrm{m}}=0.3$. The mean redshift of our sample is $z=6.4$, at which an angular size of 1$\ensuremath{''}$ corresponds to a projected physical distance of 5.5 kpc.

# Data and samples

The main sample for our study consists of 27 quasar host galaxies[^1] at redshifts $z \gtrsim 6$ observed with ALMA in the $\text{\textsc{[C ii]}}$ emission at $\sim1$ kpc resolution ($\sim0.25\ensuremath{''}$). With the high-resolution criteria satisfied, we also supplemented the data with low-resolution archival observations of these sources, where available. Our sample spans the redshift range of $z=5.8 - 7.5$, and contains quasar host galaxies with $\text{\textsc{[C ii]}}$ luminosities in the range of $(0.8 - 9)\times10^{9}\,\ensuremath{\mathrm{L}_{\odot}}$, and FIR luminosities in the range of $(0.5 - 12)\times10^{12}\,\ensuremath{\mathrm{L}_{\odot}}$ (cite: venemans20).

## New and archival ALMA data

For our analysis, we consider all available 12 m and 7 m ALMA observations performed in cycles 1 through 6, which were obtained at a resolution of $0.1\ensuremath{''}$ or coarser. The bulk of the high spatial resolution data comes from our recent programs with IDs 2017.1.01301.S and 2018.1.00908.S. We have excluded cycle 0 data from our selection to avoid possibly lower quality data and known difficulties[^2] of combining these observations with subsequent cycles. We have also excluded higher resolution (sub-kpc) observations available for two of the quasar host galaxies, because there is insufficient overlap of available baseline lengths compared to our main data sample. Finally, we have excluded quasar host galaxies without $\sim1$ kpc observations from the analysis, in order to have a consistent sample across the paper series. These selection criteria yield a main sample of 27 quasar host galaxies, where all objects, by construction, have $\sim1$ kpc data available.

Although the high-resolution data resolve the gas and dust structure and the kinematics of the host galaxy, they may not be sensitive to large-scale emission, which may be either below the detection limit, or out-resolved due to the lack of shorter baselines. In order to quantify this effect and mitigate the issue as much as possible, we make use of all available archival data targeting the $\text{\textsc{[C ii]}}$ emission line in the galaxies of our sample. Datasets with lower spatial resolution observations, obtained across multiple ALMA observational cycles, are available for 20 objects in our sample.

In total, this work uses 54 different observations targeting 27 objects, as listed in Table [\[tab:data\]](#tab:data), where all datasets correspond to 12 m array observations, unless noted otherwise. The redshift, $\text{\textsc{[C ii]}}$ integrated line flux density, and the full width at half maximum (FWHM), reported in Table [\[tab:data\]](#tab:data), are all measured from the aperture-extracted $\text{\textsc{[C ii]}}$ spectra, whereas coordinates are measured from the $\text{\textsc{[C ii]}}$ intensity maps, as reported in (cite: venemans20). For each object we list used observation runs in various ALMA cycles, including their time on source (TOS), the synthesized beam size, and the maximum recoverable scale (MRS). The last two values are computed based on the baseline statistics following the ALMA Technical Handbook (Eqs. 7.4 and 7.7), i.e. $\theta_{\mathrm{beam}} [\mathrm{rad}]=0.574\lambda/L_{80}$ and $\theta_{\mathrm{MRS}} [\mathrm{rad}]=0.983\lambda/L_{5}$, where $\lambda$ is the observing wavelength, and $L_{5}$ and $L_{80}$ are the 5^th^ and the 80^th^ percentile of the available $uv$-distances, respectively. The MRS is defined as the largest angular size at which at least 10% of the total flux density of a uniform disk is recovered and should only be used to describe the data limitations to first order.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Quasar host | z$_{\text{[C\textsc{ii}]}}$ | RA (ICRS ) | Dec (ICRS) | $F_{\ensuremath{\text{\textsc{[C ii]}}}}$ | FWHM | Cycle | TOS | Beam[^3] | MRS | Project code | Member ObsUnitSet ID |
| galaxy |  | $\mathrm{{}^{\circ}}$ | $\mathrm{{}^{\circ}}$ | $\mathrm{Jy\,km\,s^{-1}}$ | $\mathrm{km\,s^{-1}}$ |  | $\mathrm{min}$ | $\mathrm{{}^{\prime\prime}}$ | $\mathrm{{}^{\prime\prime}}$ |  |  |
| P007+04 | 6.0015 | 7.02736 | 4.95706 | 1.7 $\pm$ 0.1 | 370 $\pm$ 22 | 3^[5](#fn:recal)^ | 7.4 | 0.44 | 5.0 | 2015.1.01115.S | uid://A001/X2fb/X3b8 |
|  |  |  |  |  |  | 5 | 29.1 | **0.23** | 3.2 | 2017.1.01301.S | uid://A001/X1273/X360 |
| P009–10 | 6.0040 | 9.73553 | -10.43168 | 9.6 $\pm$ 0.7 | 437 $\pm$ 33 | 3^[5](#fn:recal),\ [4](#fn:baduv)^ | 8.4 | 0.4 | 4.5 | 2015.1.01115.S | uid://A001/X2fb/X3bc |
|  |  |  |  |  |  | 5 | 25.7 | **0.23** | 3.3 | 2017.1.01301.S | uid://A001/X1273/X364 |
| J0100+2802 | 6.3268 | 15.05426 | 28.04051 | 3.7 $\pm$ 0.2 | 405 $\pm$ 20 | 3[^4] | 72.4 | **0.18** | 3.5 | 2015.1.00692.S | uid://A001/X2d6/X1a8 |
| J0109–3047 | 6.7904 | 17.47135 | -30.79065 | 1.7 $\pm$ 0.1 | 354 $\pm$ 34 | 1 | 15.4 | 0.27 | 4.0 | 2012.1.00882.S | uid://A002/X5a9a13/X53b |
|  |  |  |  |  |  | 2[^5] | 35.8 | 0.2 | 2.1 | 2013.1.00273.S | uid://A001/X148/X6b |
|  |  |  |  |  |  | 3 | 32.4 | **0.16** | 2.9 | 2015.1.00399.S | uid://A001/X5a3/X52 |
| J0129–0035[^6] | 5.7788 | 22.49381 | -0.59440 | 2.1 $\pm$ 0.1 | 206 $\pm$ 9 | 1^[5](#fn:recal),\ [4](#fn:baduv)^ | 76.5 | **0.18** | 2.0 | 2012.1.00240.S | uid://A002/X7fb989/X1c |
|  |  |  |  |  |  | 3 | 60.7 | 0.34 | 4.4 | 2015.1.00997.S | uid://A001/X2fb/X5de |
|  |  |  |  |  |  | 3 - 7m | 209.4 | 4.0 | 25.0 | 2015.1.00997.S | uid://A001/X2fb/X5e0 |
| J025–33 | 6.3373 | 25.68218 | -33.46264 | 5.5 $\pm$ 0.2 | 370 $\pm$ 16 | 3 | 7.9 | 0.61 | 5.8 | 2015.1.01115.S | uid://A001/X2fb/X3c4 |
|  |  |  |  |  |  | 5 | 24.2 | **0.23** | 3.2 | 2017.1.01301.S | uid://A001/X1273/X368 |
| P036+03 | 6.5405 | 36.50782 | 3.04979 | 3.2 $\pm$ 0.1 | 237 $\pm$ 7 | 3 | 75.5 | **0.13** | 1.6 | 2015.1.00399.S | uid://A001/X5a3/X4a |
| J0305–3150[^7]^,^[^8] | 6.6139 | 46.32052 | -31.84888 | 5.4 $\pm$ 0.3 | 225 $\pm$ 15 | 1 | 15.9 | 0.26 | 3.7 | 2012.1.00882.S | uid://A002/X5a9a13/X543 |
|  |  |  |  |  |  | 2^[5](#fn:recal)^ | 15.5 | 0.2 | 2.1 | 2013.1.00273.S | uid://A001/X148/X6f |
|  |  |  |  |  |  | 3 | 37.7 | **0.17** | 3.0 | 2015.1.00399.S | uid://A001/X5a3/X4e |
| P065–26 | 6.1871 | 65.40851 | -26.95432 | 1.7 $\pm$ 0.2 | 289 $\pm$ 31 | 3 | 15.8 | 0.74 | 7.3 | 2015.1.01115.S | uid://A001/X2fb/X3e4 |
|  |  |  |  |  |  | 5 | 24.7 | **0.23** | 3.3 | 2017.1.01301.S | uid://A001/X1273/X36c |
| J0842+1218 | 6.0754 | 130.62266 | 12.31402 | 0.8 $\pm$ 0.1 | 378 $\pm$ 52 | 3 | 7.4 | 0.98 | 9.2 | 2015.1.01115.S | uid://A001/X2fb/X3ec |
|  |  |  |  |  |  | 4 | 53.6 | **0.25** | 2.7 | 2016.1.00544.S | uid://A001/X885/X36b |
| J1044–0125^[6](#fn:c0)^ | 5.7846 | 161.13767 | -1.41724 | 1.8 $\pm$ 0.2 | 454 $\pm$ 60 | 1^[4](#fn:baduv)^ | 76.5 | **0.17** | 1.9 | 2012.1.00240.S | uid://A002/X7fb989/X20 |
|  |  |  |  |  |  | 3 | 60.7 | 0.57 | 5.0 | 2015.1.00997.S | uid://A001/X2fb/X5e4 |
|  |  |  |  |  |  | 3 - 7m | 179.4 | 3.9 | 24.0 | 2015.1.00997.S | uid://A001/X2fb/X5e6 |
| J1048–0109 | 6.6759 | 162.07949 | -1.16123 | 1.9 $\pm$ 0.1 | 299 $\pm$ 24 | 3 | 11.9 | 0.95 | 9.1 | 2015.1.01115.S | uid://A001/X2fb/X3f4 |
|  |  |  |  |  |  | 5 | 25.7 | **0.23** | 2.8 | 2017.1.01301.S | uid://A001/X1273/X370 |
| P167–13^[7](#fn:comp)^ | 6.5144 | 167.64160 | -13.49607 | 5.3 $\pm$ 0.3 | 519 $\pm$ 25 | 3 - CW^[4](#fn:baduv),^ [^9] | 42.8 | 0.61 | 5.4 | 2015.1.00606.S | uid://A001/X2d6/X7d |
|  |  |  |  |  |  | 3 - FW^[9](#fn:initials)^ | 7.9 | 0.88 | 8.5 | 2015.1.01115.S | uid://A001/X2fb/X3f8 |
|  |  |  |  |  |  | 4 | 42.7 | **0.25** | 3.7 | 2016.1.00544.S | uid://A001/X885/X367 |
| J1120+0641 | 7.0848 | 170.00611 | 6.68996 | 1.0 $\pm$ 0.1 | 416 $\pm$ 39 | 1 | 160.7 | **0.22** | 2.6 | 2012.1.00882.S | uid://A002/X5a9a13/X537 |
| P183+05 | 6.4386 | 183.11240 | 5.09266 | 6.8 $\pm$ 0.3 | 397 $\pm$ 19 | 3 | 8.4 | 0.92 | 8.9 | 2015.1.01115.S | uid://A001/X2fb/X408 |
|  |  |  |  |  |  | 4 | 47.1 | **0.25** | 2.7 | 2016.1.00544.S | uid://A001/X885/X363 |
| J1306+0356^[7](#fn:comp)^ | 6.0330 | 196.53441 | 3.94061 | 1.2 $\pm$ 0.1 | 246 $\pm$ 26 | 3 | 8.4 | 0.85 | 8.2 | 2015.1.01115.S | uid://A001/X2fb/X40c |
|  |  |  |  |  |  | 5 | 27.7 | **0.23** | 3.3 | 2017.1.01301.S | uid://A001/X1273/X374 |
| J1319+0950^[6](#fn:c0),\ [7](#fn:comp)^ | 6.1347 | 199.79701 | 9.84763 | 4.1 $\pm$ 0.4 | 532 $\pm$ 57 | 1^[4](#fn:baduv)^ | 50.4 | **0.22** | 2.0 | 2012.1.00240.S | uid://A002/X7fb989/X18 |
|  |  |  |  |  |  | 3 | 30.3 | 0.93 | 9.0 | 2015.1.00997.S | uid://A001/X2fb/X5d2 |
|  |  |  |  |  |  | 3 - 7m | 119.6 | 3.9 | 26.0 | 2015.1.00997.S | uid://A001/X2fb/X5d4 |
| J1342+0928^[7](#fn:comp)^ | 7.5400 | 205.53375 | 9.47736 | 1.0 $\pm$ 0.1 | 353 $\pm$ 27 | 5 | 114.1 | **0.16** | 3.0 | 2017.1.00396.S | uid://A001/X1296/X976 |
| P231–20^[7](#fn:comp)^ | 6.5869 | 231.65765 | -20.83354 | 3.3 $\pm$ 0.3 | 393 $\pm$ 35 | 3 | 7.4 | 0.87 | 8.5 | 2015.1.01115.S | uid://A001/X2fb/X440 |
|  |  |  |  |  |  | 4 | 43.1 | **0.17** | 2.1 | 2016.1.00544.S | uid://A001/X885/X35f |
| P308–21^[7](#fn:comp)^ | 6.2355 | 308.04167 | -21.23399 | 3.4 $\pm$ 0.2 | 541 $\pm$ 32 | 3 | 12.4 | 0.63 | 5.9 | 2015.1.01115.S | uid://A001/X2fb/X418 |
|  |  |  |  |  |  | 4 | 55.6 | **0.24** | 3.6 | 2016.A.00018.S | uid://A001/X11a4/Xf |
| J2054–0005 | 6.0389 | 313.52708 | -0.08735 | 3.2 $\pm$ 0.1 | 236 $\pm$ 12 | 6 | 84.9 | **0.11** | 2.1 | 2018.1.00908.S | uid://A001/X133d/X261d |
| J2100–1715 | 6.0807 | 315.22792 | -17.25610 | 1.4 $\pm$ 0.1 | 361 $\pm$ 41 | 3^[5](#fn:recal)^ | 7.9 | 0.57 | 5.2 | 2015.1.01115.S | uid://A001/X2fb/X41c |
|  |  |  |  |  |  | 5 | 25.2 | **0.22** | 3.2 | 2017.1.01301.S | uid://A001/X1273/X378 |
| P323+12 | 6.5872 | 323.13826 | 12.29865 | 1.3 $\pm$ 0.2 | 271 $\pm$ 38 | 6 | 42.9 | **0.1** | 1.7 | 2018.1.00908.S | uid://A001/X133d/X2621 |
| J2318–3113 | 6.4429 | 349.57651 | -31.22955 | 1.5 $\pm$ 0.1 | 344 $\pm$ 34 | 3^[5](#fn:recal)^ | 7.9 | 0.66 | 5.7 | 2015.1.01115.S | uid://A001/X2fb/X428 |
|  |  |  |  |  |  | 5 | 23.7 | **0.24** | 3.5 | 2017.1.01301.S | uid://A001/X1273/X37c |
| J2318–3029 | 6.1456 | 349.63792 | -30.49266 | 2.3 $\pm$ 0.1 | 293 $\pm$ 17 | 6 | 39.9 | **0.1** | 1.7 | 2018.1.00908.S | uid://A001/X133d/X2619 |
| J2348–3054^[8](#fn:uberres)^ | 6.9007 | 357.13895 | -30.90285 | 1.5 $\pm$ 0.2 | 457 $\pm$ 49 | 1 | 16.7 | 0.41 | 5.3 | 2012.1.00882.S | uid://A002/X5a9a13/X53f |
|  |  |  |  |  |  | 2^[5](#fn:recal)^ | 36.8 | 0.19 | 2.0 | 2013.1.00273.S | uid://A001/X148/X73 |
|  |  |  |  |  |  | 3 | 51.8 | **0.17** | 3.1 | 2015.1.00399.S | uid://A001/X5a3/X56 |
| P359–06 | 6.1719 | 359.13517 | -6.38313 | 2.7 $\pm$ 0.1 | 341 $\pm$ 18 | 3^[5](#fn:recal)^ | 7.9 | 0.66 | 6.3 | 2015.1.01115.S | uid://A001/X2fb/X430 |
|  |  |  |  |  |  | 5 | 25.7 | **0.22** | 3.1 | 2017.1.01301.S | uid://A001/X1273/X380 |

## Data reduction

To obtain the calibrated $uv$-visibilities for imaging, we reduced the raw data using the default pipeline restoration scripts executed in the appropriate version of the Common Astronomy Software Applications (CASA) package (cite: mcmullin07), i.e. the same version applied during the original calibration (CASA 4.1 to 5.4.0-68). Additional data quality checks and data manipulation were performed as described in the following section.

### Flux calibration accuracy

We combine data from multiple objects and ALMA observation cycles. Because the addition of visibilities at incorrect flux scales could translate into erroneous spatial structure in the image plane, we performed several quality assurance checks on the flux calibration. As noted by (cite: stanley19), several datasets required recalibration in a newer CASA version due to incorrect flux calibrator models present for Pallas and Ceres in CASA version 4.6 or lower. There are a total of nine datasets affected by this issue, as indicated in Table [\[tab:data\]](#tab:data). Flux scales after recalibration were $60 - 80\%$ of the original values, with the mean flux level reduction of 15% for these nine datasets.

As a precaution, we reran the full pipeline calibration process on each of the 54 datasets, using the latest CASA version at the time of writing (version 5.6.1-8), as described in the ALMA Science Pipeline User’s Guide for CASA 5.6.1 (Section 6.4). Additionally, we manually enabled the query to the online ALMA flux calibrator catalog. The goal of this approach was to check for the existence of additional significant flux calibration changes introduced in the CASA development and debugging process, as well as to get the most up-to-date flux calibrator model values. For most of the datasets, the process finished successfully[^10] and yielded no flux level changes beyond 10%, which is the usually reported calibration accuracy value. Because we found no further anomalies, we continued to use the calibrated visibilities provided by the default restoration scripts (except in the case of Pallas and Ceres calibrators as mentioned above).

### Data products per galaxy 

We have created several data products (measurement sets, maps and cubes) in CASA for every observational cycle of each of the studied quasar (see Table [\[tab:data\]](#tab:data)), as described in (cite: venemans20). We briefly summarize these here. We imaged the calibrated visibilities, using the CASA task tclean, with the Högbom deconvolver, and a channel spacing of 30 MHz (corresponding to 35 $\text{km\,s}^{-1}$ on average). We weighted the data with the Briggs[^11] algorithm (robust = 0.5) and cleaned (deconvolved) the maps down to $2\sigma$ level, within a cleaning mask radius of $2\ensuremath{''}$. We use these clean cubes to extract the $\text{\textsc{[C ii]}}$ spectrum including the continuum emission. With the knowledge of the line position, we performed the continuum subtraction using the uvcontsub task on the two spectral windows around the $\text{\textsc{[C ii]}}$ line, excluding channels in total width of $2.5\times\mathrm{FWHM}$ around the $\text{\textsc{[C ii]}}$ line (i.e. the total excluded bandwidth is on average 900 $\text{km\,s}^{-1}$), while allowing for a continuum slope (fitorder = 1). Using these datasets we imaged the continuum-free cube (same imaging parameters as above), as well as the $\text{\textsc{[C ii]}}$ intensity map by averaging channels across $1.2\times\mathrm{FWHM}$ of the line, chosen to optimize the signal-to-noise ratio (S/N). We justify this integration width in Appendix [7](#sec:app_optimalsn).

### Stacking the data in the $uv$-plane

Stacking can be performed in the image plane by either averaging the pixel/voxel values of maps or cubes, or by averaging extracted properties such as the spectra. Both methods are susceptible to several issues pertaining to the nature of interferometric data. I.e., the synthesized beam is not the same between datasets, and the faint stacked emission is usually uncleaned, which will yield ill-defined hybrid units in the stacked map (i.e., every pixel value will be a non-trivial combination of various cleaned and dirty beams). Another side-effect of image based stacking is that different spatial scales might be probed in different sources. In order to circumvent these issues, we aim to add all visibilities in the $uv$-plane and thus obtain the best estimate of the mean emission of the population. To this effect we have adapted the method described in e.g. (cite: fujimoto19), and extended it to be applicable to the whole spectrum. This method requires the data to be further reduced as follows.

For every individual cycle, starting from the continuum subtracted visibilities, the required channels were split out. Depending on the science goal, we either split out the equivalent of the $\text{\textsc{[C ii]}}$ intensity map ($1.2\times\mathrm{FWHM}$), or, a smaller chunk corresponding to a specific velocity bin (i.e. a channel map, and/or the resolution of our spectral extraction). We used the function im.advisechansel from the CASA toolkit to select the channels of interest in the kinematic local standard of rest frame (LSRK). Individual channels are selected based on the nearest neighbour algorithm. The data that we consider for $uv$-stacking were all observed at velocity resolutions of $\lesssim10\,\ensuremath{\text{km\,s}^{-1}}$, which is high enough to render any additional velocity-based data regridding or interpolation unnecessary. The data was further time-averaged inside 30 s bins to reduce the data volume[^12]. The coordinate reference system in the header was changed to the International Celestial Reference System (ICRS) as it was sometimes incorrectly written as J2000. The visibilities were phase-shifted to the centroid of the $\text{\textsc{[C ii]}}$ emission using the task fixvis[^13]. The header was modified further to artificially place the object at the $(0,0)$ coordinate[^14]. Finally, the data weights were recomputed with the statwt task using the same time and channels bin for all of the datasets. The calculation of the default weights is implemented differently across various CASA versions and can depend on the system temperature or gain factors. We manually checked that the ranges of recomputed weights are similar between all datasets, allowing the data to be co-added in a way that ensures the weighted average is not erroneously dominated by any single source. Several anomalous datasets were identified as having (at least) an order of magnitude larger data weights (they also have much lower observed velocity resolution of $\gtrsim30\,\ensuremath{\text{km\,s}^{-1}}$), and were excluded from any further $uv$-stacking analysis. These exclusions are noted in Table [\[tab:data\]](#tab:data).

We imaged the split, renormalized and re-centered data using the CASA task tclean, considering the full list of all sources and cycles. We imaged the data in the continuum mode (specmode = mfs) and applied the multi-scale deconvolver, with scales corresponding to 0 (delta-function), 1, 3, 5 and 10 synthesized beam sizes. Cleaning was performed within a 2$\ensuremath{''}$ radius mask down to a $2\sigma$ threshold. To obtain the $uv$-stacked cube we imaged every velocity bin individually. The velocity bin was either of fixed size, i.e. 30 $\text{km\,s}^{-1}$, or scaled with the width of the $\text{\textsc{[C ii]}}$ line, i.e. $0.2\sigma_{\mathrm{line}}$. We used both approaches in our analysis. These separately imaged velocity bin slices were further joined into a single cube using the CASA toolkit task ia.imageconcat.

The preparation of the data for $uv$-plane continuum stacking was performed in the same way as in the $\text{\textsc{[C ii]}}$ case, but instead of selecting the line emission channels, we flagged them. A total of width of $2.5\times\mathrm{FWHM}$ centered at $\text{\textsc{[C ii]}}$ was removed, and the remaining channels inside individual spectral windows were averaged together. All available continuum data were used (i.e. data from all four science spectral windows). We validated that our choice of excluded frequencies/velocities did not bias the dust continuum results by re-imaging the data, this time excluding a much broader bandwidth of $8\times\mathrm{FWHM}$ around the line ($\sim$2800 $\text{km\,s}^{-1}$ on average).

Spectral stacking will smooth any spatial and velocity structure of individual sources. The stack itself is only meaningful if the mean property of interest (e.g. extent of the faint emission, or the line shape) is well-defined for the sample, which we cannot know a priori, and deeper observations are necessary to confirm any potential structure in individual objects.

## Mergers and companions

Our aim is to measure extended structure and high-velocity outflows in quasar host galaxies. Thus, we take special care of objects exhibiting ongoing mergers, and of those that have a nearby companion galaxy. In both cases the accompanying source might bias our results, by either providing additional flux at larger distances from the quasar host, or at larger velocity separations. Where possible, we visually identified the presence of accompanying sources, distinct in terms of either their spatial, or velocity position ($\text{\textsc{[C ii]}}$ intensity maps are available in Appendix [13](#sec:app_sources); see also accompanying papers by (cite: venemans20) and (cite: neeleman20b)). Morphological details on sub-kpc scales cannot be recovered with these observations. What we consider as a single component source in this work might break into multiple sources upon a higher resolution follow-up. Thus, definitions such as a merger or a galaxy pair are, by construction, arbitrary, especially in the low S/N regime. With these limitations in mind, we classify these special cases based on visual inspection into four groups as follows (see also (cite: decarli17), (cite: decarli19), (cite: neeleman19) and (cite: banados19)):

I\) Merging system blended inside the aperture: These systems exhibit at least two clearly separated (spatially or in velocity) peaks at distances of less than $\sim 5$ kpc. In our data it is not possible to draw a clear line between the two sources or easily measure their individual fluxes due to a connecting bridge of $\text{\textsc{[C ii]}}$ emission or blending. We classify five of such systems: J1319+0950, J1342+0928, P167–13, P308–21 and J0305–3150.

II\) Nearby companion: These are defined as sources that have a spatial offset of $\sim 5 - 10$ kpc between the quasar host and its galaxy pair, such that an aperture flux can be obtained for both objects individually. However, the system will show increased flux on the smallest baselines that cover both sources simultaneously. We classify two such systems: J1306+0356 and P231–20.

III\) Distant companions: These are cases where there is a galaxy pair in the field, but at separations larger than 10 kpc. No significant amplitude increase can be seen on the smallest baselines due to this large separation (the primary beam response at the companion source position is also significantly lower). We classify two such systems: J0842+1218 and J2100–1715.

IV\) Complex morphologies: These systems show a surface brightness morphology that is more complex than a single component source, but its origin is unclear. It is possible that these objects have companions detectable only at higher resolution, or that they contain extended and more patchy gas emission. In the absence of conclusive companion or merger evidence, we do not exclude these objects from the stacking analysis. We classify three such systems: J0100+2802, J025–33 and P009–10.

Groups I and II are removed from some of our samples, as explained in the next section. Groups III and IV are always included in our stacking samples, with the latter containing potential candidates for follow-up observations.

## Data samples

Throughout the paper we refer to four different data samples, all drawn from Table [\[tab:data\]](#tab:data), as follows.

1\) High-resolution data sample: It contains all 27 quasar host galaxies, where each one is represented by a single high-resolution ($\sim1$ kpc) dataset. This corresponds to the data used in the accompanying papers (cite: venemans20; neeleman20b).

2\) High-resolution clean data sample: It is a subset of the previous sample, obtained by removing five objects classified as merging systems blended inside the aperture (group I from Section [2.3](#sec:comp)). This sample is used to stack aperture spectra extracted from individually imaged maps. Nearby companions (group II) will not contribute significantly to the aperture fluxes, and are therefore included in this sample.

3\) Full $uv$-stacking data sample: It contains all of the datasets (including low resolution data), except five observing runs that have outlying data weights, and one without a full line coverage (see Table [\[tab:data\]](#tab:data) footnote and Section [2.2.3](#sec:uvstackmethod)). This selection results in 26 quasar host galaxies (out of 27) and a total of 48 datasets (out of 54). The cumulative on source time is approximately 34 h (out of which 25.5 h were taken with the 12 m array). This sample is used to obtain the highest S/N in the $uv$-stack, while attempting to recover broad-line emission, which would be indicative of outflows.

4\) Clean $uv$-stacking data sample: It is a subset of the previous sample, obtained by further removing systems classified as mergers inside the aperture and near companions (groups I and II from Section [2.3](#sec:comp)), as well as any 7 m dataset (for details see Appendix [11](#sec:app_subsamples)). This selection results in 19 quasar host galaxies and a total of 32 datasets. The cumulative time on source is approximately 18 h. We consider this sample to be the least biased, and use it to derive our main stacking results.

# Methods

In the following sections we present different methods employed in our search for extended $\text{\textsc{[C ii]}}$ emission and outflows. We discuss flux measurements taken from the image and the $uv$-plane, and the applicability and shortcomings of each method. We also discuss the details of the stacking procedures. By applying various techniques we aim to reach a consensus on the measured galaxy properties (e.g. total flux and spatial extent). This is particularly relevant for detections of low S/N. Throughout this whole section we demonstrate various diagnostics on the source J1306+0356, which was chosen as a good example, due to it being a complex system (presence of a companion, see also (cite: neeleman19)), with data available from multiple cycles at different resolutions. Results for all individual quasar host galaxies are shown in Appendix [13](#sec:app_sources).

## Measuring the spatial extent of emission

### Analysis in the image plane

![]({methods.example.maps}.pdf)

![]({methods.example.aper}.pdf)

![]({methods.aper.j1306p0356}.pdf)

A common method of measuring the flux and source size from a map is by fitting a 2D Gaussian to the galaxy in the image plane. We do so by employing the imfit task included in CASA. The second approach that requires no priors on the source morphology is the aperture integration, for which we choose to apply circular apertures. In the remainder of this section we explore only the aperture integration, but the discussed systematics are applicable to any image based analysis (i.e. fitting a 2D Gaussian).

One problem present in image plane analysis is the non-trivial unit definition ($\text{Jy\,beam}^{-1}$). Due to the nature of the deconvolution (cleaning) process, the final cleaned map will contain hybrid units. Several maps from the cleaning process, shown in Figure [1](#fig:example_map), demonstrate this issue. The final cleaned map is obtained by summing the residual map (in units of Jy / dirty beam) and the clean components map (in units of Jy / clean beam), whose units differ due to the beam definition. The clean beam is obtained[^15] by fitting a 2D Gaussian to the peak of the point spread function (PSF; the dirty beam). It has a well defined volume (integral) equal to $\Omega_{\mathrm{beam}}=\pi/ (4\ln 2)\times\theta_{\mathrm{maj}}\theta_{\mathrm{min}}$, where $\theta_{\mathrm{maj}}$ and $\theta_{\mathrm{maj}}$ are major and minor axis FWHMs of the elliptical 2D Gaussian. On the other hand, the dirty beam is a sum of many sine/cosine waves, whose integral oscillates around zero. Therefore, the volume of the dirty beam is ill-defined and will depend on the integration limits (i.e. the aperture size).

The clean components map is defined as the cleaned sky model (i.e. point sources / delta functions, and, in case of the multi-scale algorithm, additional Gaussians of manually chosen sizes) convolved with the Gaussian clean beam. During the sky reconstruction, the clean algorithm does not distinguish between positive and negative peaks. The true emission is positive, therefore the cleaning should not progress too deep, in order to avoid cleaning both positive and negative noise peaks. After the sky model is subtracted from the visibilities, the residual remains. Any flux measured from the residual (i.e. flux below the cleaning threshold) will be incorrectly assigned the clean beam size (defined to be a Gaussian in the restoration process, and written in the image header of the final map).

To mitigate this issue we scale the flux collected from the residual map (cite: jorsater95; walter08; novak19). In practice, this is performed by measuring aperture fluxes from three maps: the dirty (D), the residual (R), and the clean components[^16] (C) map (see Figure [1](#fig:example_map)). The flux density measurement is obtained by summing the values of pixels contained within the aperture, and dividing the sum with the number of pixels in the clean beam: $F_\mathrm{aper} [\mathrm{Jy}]=\sum_{\mathrm{pixels}}\mathrm{map [\ensuremath{\text{Jy\,beam}^{-1}}]} / (\Omega_{\mathrm{beam}}/\mathrm{pixelsize}^2$), where the beam axes sizes and the pixel size are all expressed in the same units (e.g. arcseconds). Corrected flux inside an aperture can be obtained as $F_{\mathrm{correct}}=C +\epsilon R=\epsilon D$, where $\epsilon= C/(D-R)$ is the clean-to-dirty beam area ratio defined inside a specific aperture (see Appendix [8](#sec:app_residualscale)). The drawback of this method is that it requires some cleaned flux, and becomes numerically unstable when $R$ approaches $D$. The error on the aperture flux can be approximated by $\mathrm{rms}\times \sqrt{N}$, where $N$ is the number of beams contained inside the aperture, and the root-mean-square (rms) is the noise variation measured in the entire map.

The amount of the residual scaling depends on the exact shape of the dirty beam (defined by the $uv$-coverage, applied imaging weights, and any additional $uv$-tapering) and the aperture size, and can either boost or decrease the measured flux density. If the scaling is significant, not applying the correction is likely to produce larger systematic uncertainties in the case of extended sources that are resolved over multiple beams, sources with low surface brightness (where significant amount of emission remains in the residual), and in the case of a non-Gaussian dirty beam (more likely to happen with naturally weighted imaging). Image-based stacking is also likely to be affected, especially if maps with different dirty beams are being stacked, because the knowledge of the beam shape and the fraction of cleaned flux is lost in the stacking process. Furthermore, the units become increasingly non-trivial after 2D image convolution, often employed for beam matching[^17].

In the first panel of Figure [1](#fig:example_map), we show an example of a high-resolution $\text{\textsc{[C ii]}}$ intensity map, produced by imaging averaged channels in total width of $1.2\times\mathrm{FWHM}$ (range of $\pm1.4\sigma_{\mathrm{line}}$) from the continuum subtracted measurement set. The measured aperture flux density can be corrected for the missing tails beyond the $1.2\times\mathrm{FWHM}$, assuming a Gaussian profile, by multiplying by 1.19. In Figure [1](#fig:example_map), a second $4\sigma$ peak is apparent 5 kpc away (cite: neeleman19). Due to the large separation we are able to define an aperture containing the full source emission, with no significant contribution from the companion or the connecting bridge.

In Figure [2](#fig:example_aper_dirty) we show flux densities measured inside a growing aperture (hereafter referred to as the curves of growth) for all of the maps from Figure [1](#fig:example_map). The clean beam size can only be used to measure the emission in the clean components map. If used on other maps, it will introduce systematic errors if the clean-to-dirty beam ratio defined inside the aperture is different from one. In this example, the ratio is 0.65 at the chosen aperture of $0.5\ensuremath{''}$, therefore any uncleaned flux is being over-counted by a factor of $1/0.65\approx1.5$. Because of this, the corrected flux density is 85% of the one measured in the cleaned map without residual scaling.

In Figure [3](#fig:example_aper) we show measurements from two observation cycles of the same source, taken at different resolutions. The quasar host galaxy and its companion are blended together in the low resolution data (beam $\approx0.85\ensuremath{''}$). The total flux density of the system, i.e. the value at which the curves of growth flatten, are consistent within the errors. The residual scaling correction is smaller for the low resolution data.

### $uv$-plane analysis

![]({methods.uv.j1306p0356}.pdf)

Due to discrete and sparse $uv$-coverage, the map produced by the clean algorithm is not uniquely defined, i.e. missing Fourier components must be extrapolated. To avoid such issues altogether, the measurement can be directly performed in the $uv$-plane. Approaches vary from simpler ones, such as examining 1D amplitudes vs. $uv$-distance plots (cite: hodge16), to more complex ones, such as using specialized multi-component fitting software, e.g. uvmultifit (cite: uvmultifit), as demonstrated in e.g. (cite: rujopakarn19), or fitting morphology models based on Bayesian statistics (cite: pavesi16). We employ two techniques: 1) we attempt to fit a 2D Gaussian in the $uv$-plane using the uvmodelfit task in CASA, and 2) we analyze amplitudes in radially-averaged annuli of $uv$-distances (units of k$\lambda$). For high S/N data, a poor fit to the visibilities indicates a more complex source morphology (i.e. non-Gaussian), or it can imply additional sources/companions in the field (i.e. the second source is blended together with the main one on the shortest baselines only). One downside of this simple $uv$-plane analysis method is that it does not account for the complex morphology encoded in the visibilities’ phases, so it is best applied in parallel with the map analysis.

In Figure [4](#fig:example_uv) we show the flux densities measured at specific $uv$-distances (i.e. projected baseline lengths) of two different observation cycles. Only the real part of the complex visibilities is shown as a proxy for the visibility amplitude[^18]. For a source in the phase center, the imaginary part of the visibilities will always have a mean value of zero. We have confirmed that this to be the case for all of our datasets. Histograms in the lower panel show the number of visibilities from different cycles that depend on the number of antennas and the total integration time (all data was averaged to the same interval of 30 s, see Section [2.2.3](#sec:uvstackmethod)).

It is expected that a single Gaussian would be a poor representation of this system, which contains two galaxies at close ($\sim5$ kpc) separation. Therefore, an attempt to fit a single 2D Gaussian to the visibilities, using the uvmodelfit task in CASA, yields significantly different models and total fluxes (shown as squares in Figure [4](#fig:example_uv)) for the two cycles. The low-resolution data confirms the upturn in visibilities that is only hinted at in the high-resolution data below 100 k$\lambda$. In this example it is clear that there is a second galaxy that is causing this upturn. In a different scenario, where no such companion is obvious from the image plane analysis, the interpretation becomes more difficult, as the faint spatially extended emission can have the same signature.

### Comparing flux measurements

![](fluxCompare.pdf)

We apply the different methods of measuring the flux density, outlined above, to our high-resolution sample of quasars (sample 1 from Section [2.4](#sec:samples)), and compare the results in Figure [5](#fig:fluxcompare). Aperture sizes for individual sources were chosen manually (after visual inspection) to be at a radius where the curve of growth begins to flatten, approaching values consistent with short baseline $uv$-amplitudes. We limit the 2D Gaussian fitting in the image plane to a circle of a 2$\ensuremath{''}$ radius, and apply no additional constraints to $uv$-plane fits.

Disregarding the outlier with a nearby companion at $\sim1\,\ensuremath{\text{Jy\,km\,s}^{-1}}$ (in example source J1306+0356), all of the measurements are consistent within a factor of two, and generally consistent within the errors. Two tentative trends can be observed in Figure [5](#fig:fluxcompare). Compared to the aperture measurements, image plane fitting using imfit (circles in Figure [5](#fig:fluxcompare)) produces larger values at the fainter end (i.e. Gaussian tails apparently account for positive noise peaks), while both image plane based imfit fits (circles), and $uv$-plane based uvmodelfit (squares) single Gaussian fits, yield generally lower fluxes at the brighter end, possibly indicating the presence of more extended faint emission. In some of the cases, fitting a single 2D Gaussian is obviously a poor description of the observations, nevertheless we show this simple approach to demonstrate the resulting scatter.

Measurements of both the aperture flux density, and amplitudes at the shortest baselines, can be sensitive to large scale structure, whereas fitting a 2D Gaussian in the image plane will unlikely provide good estimates for the extended faint emission. For this reason we refrain from fitting 2D Gaussians in the image plane in the remainder of the paper.

## Measuring the spectrum

### Extracting aperture spectra

![]({methods.spec.j1306p0356}.pdf)

To measure the spectrum, we apply residual scaling on the aperture flux densities obtained from individual channels before a spectrum is extracted. The clean-to-dirty beam ratio, $\epsilon$, can be estimated from the channels with the highest S/N, and applied on the remaining channels, as the beam shape is not expected to vary significantly between neighboring channels. This is demonstrated in Figure [6](#fig:example_spec), where the factor $\epsilon$ exhibits the least scatter when measured across the line. If the continuum is absent, $\epsilon$ can be measured exclusively over the line (as it requires some clean flux $C$ to calculate). The value of $\epsilon=0.61$, obtained here, is slightly smaller compared to $\epsilon=0.65$, derived from the $\text{\textsc{[C ii]}}$ intensity map (see Figure [2](#fig:example_aper_dirty)), because the shape of the dirty beam will vary slightly due to different visibilities being averaged in both cases (varying frequency ranges are being averaged). The S/N of the emission is lower inside individual channels compared to a broader intensity map collapse, and with less cleaned emission in smaller velocity bins, the contribution of the residual (uncleaned) flux is larger. This results in a more significant residual-scaling effect, as the corrected value now corresponds to 78% of the non-corrected one (compared to the previous 85% in the intensity map). In this example, a single Gaussian plus a constant fit yields the $\text{\textsc{[C ii]}}$ line FWHM of 246 $\pm$ 26 $\text{km\,s}^{-1}$. The residual spectrum after the subtraction of the fit (the lower panel of Figure [6](#fig:example_spec)) is consistent with pure noise. There is no indication of an additional broad spectral component.

### Stacking spectra

To increase the S/N of the spectra and recover possible fainter emission we also perform spectral stacking. Due to the range of $\text{\textsc{[C ii]}}$ linewidths in our sample (see Table [\[tab:data\]](#tab:data)) it is necessary to rescale the spectra by their respective widths before stacking. This step ensures that we do not misinterpret the contribution from broader lines as potential outflows in the mean spectrum. Therefore, we resample all spectra before stacking, and present the stacked spectra in the units of velocity divided by $\sigma_{\mathrm{line}}$, which has an average value of 150 $\text{km\,s}^{-1}$.

We perform spectral stacking in two ways. First, we stack individually measured and residual-scaled aperture spectra from the data cube (aperture sizes were chosen manually), where we consider the underlying continuum to be flat, within the bandwidth of interest, and estimated from the fitting of a Gaussian plus constant profile. This constant value[^19] for the continuum is subtracted before the addition of the spectra. No additional weights to individual spectra are applied. Second, we perform spectral $uv$-stacking (as described in Section [2.2.3](#sec:uvstackmethod)). To obtain the full spectral cube, we selected velocity slices of $0.2\sigma_{\mathrm{line}}$ from individual datasets and imaged them together. This velocity corresponds to a width of 30 $\text{km\,s}^{-1}$ on average. The $uv$-data was continuum subtracted prior to stacking and, in contrast to the first method, this continuum subtraction allowed for a spectral slope in the fit. Having two different methods of continuum estimation largely mitigates any potential bias of subtracting a broad component as continuum.

# Results

In the following sections we present the recovered spatial extent of both $\text{\textsc{[C ii]}}$ and the dust continuum, as well as evidence for/against outflows.

## Spatial extent of the $\text{\textsc{[C ii]}}$ emission

![image]({uvstack.nocomp.remove7m.sig0.0.delta2.8.rob.scales.maps}.pdf)\
![image]({uvstack.nocomp.remove7m.sig0.0.delta2.8.rob.scales.epsflux}.pdf) ![image]({uvstack.nocomp.remove7m.sig0.0.delta2.8.rob.scales.profile}.pdf)\

Using the analysis template presented in the previous section, we performed a visual inspection for each of the 27 quasar host galaxies in our sample (for details see Appendix [13](#sec:app_sources)). We find that, in most cases, the full extent of the source is difficult to quantify. Our chosen aperture sizes have a mean radius of 4 kpc, but the curves of growth usually hint at additional larger scale emission. Most sources for which the amplitudes are well-fit by a single Gaussian exhibit slightly higher amplitudes at the lowest baselines that probe the largest spatial scales. Fluxes measured between different cycles of individual sources are usually consistent, although discrepancies can reach up to 50% in some cases. This may be attributed to the low S/N of the particular observation, but some remaining calibration issues may also be present. Unfortunately, the S/N available at short baselines is generally insufficient to make any significant claims regarding extended emission in individual sources. Three sources with additional 7 m data show at least 10% larger amplitudes on short baselines compared to the 12 m data. High-resolution imaging ($\sim$1 kpc), can still be successfully used to recover emission on significantly larger scales because the MRS (see Section [2.1](#sec:datalist)) is approximately an order of magnitude larger than the synthesized beam. In summary, visual inspection of individual sources show tentative evidence for extended emission, with apertures larger than the usual $2\sigma$ outlining contours necessary to collect this emission.

We investigate the mean extent of this $\text{\textsc{[C ii]}}$ emission via $uv$-stacking. The stack was created as described in Section [2.2.3](#sec:uvstackmethod) using the 19 quasar host galaxies in the clean sample (sample 4 from Section [2.4](#sec:samples), totaling 32 observation runs). In short, from each dataset, which was first continuum subtracted, we selected frequency channels that encompass a total of $1.2\times\mathrm{FWHM}$ of the $\text{\textsc{[C ii]}}$ line, and then imaged them all combined, thus obtaining a single $uv$-stacked $\text{\textsc{[C ii]}}$ intensity map. The results are presented in Figure [7](#fig:uvstackcii), where the maps highlight the quality of the combined data and the success of the deconvolution process. The anisotropic 2D structure is the result of stacking galaxies with random inclinations, that might also have faint undetected companions, and is therefore not meaningful.

From the curve of growth in Figure [7](#fig:uvstackcii), we conclude that the emission extends up to 10 kpc ($\sim2\ensuremath{''}$), beyond which we do not recover any significant additional flux. The value at which the cumulative flux saturates ($2.5\pm0.1$ $\text{Jy\,km\,s}^{-1}$), when corrected for missing tails, is consistent with the mean of the line fluxes measured individually from the spectra. The corrected and the non-corrected flux densities are consistent within the errors, because most of the flux was cleaned, and the clean-to-dirty beam ratio is 0.75–1, up to a radius of $3.5\ensuremath{''}$. The dirty beam sidelobes levels are 4% at most. We report a simple one parameter size estimate, the half-light radius, defined as the radius where the curve of growth equals to 50% of the value at 10 kpc (where the curve reaches saturation). The $\text{\textsc{[C ii]}}$ emission half-light radius is $1.6 \pm 0.1$ kpc, and the region within 2, 3, 4, 5 and 10 kpc contains 55%, 65%, 75%, 80% and 100% of the flux, respectively.

We also examine the surface brightness profile of the $\text{\textsc{[C ii]}}$ emission, shown in Figure [7](#fig:uvstackcii). The azimuthally-averaged profile measured in the cleaned map (red line) indicates the presence of two components of emission; a steep core, and a broad fainter component. The extended component is detected at $>3\sigma$ significance up to a radius of 5 kpc (and $>2\sigma$ up to 8 kpc), and is well described by an exponential function with a scale length of 2 kpc (also shown in Figure [7](#fig:uvstackcii)). The emission drops to 1% of the peak beyond 6 kpc. Here, we did not perform any residual scaling, but instead calculated the mean value of pixels within some annulus, as the corrections are negligible.

We ascertained to what extent the multi-scale cleaning algorithm may bias the shape of the profile by repeating the imaging process with a different and simpler algorithm. The results are presented in Appendix [9](#sec:app_ms), and show that, regardless of the clean procedure, we recover the same shape of the surface brightness profile. Furthermore, in Appendix [10](#sec:app_uvfit) we fit the brightness profile models directly to the $uv$-data. The results obtained with this method are in agreement with our conclusions drawn from the image plane analysis. We investigate further possible selection biases by repeating this analysis for several different subsamples in Appendix [11](#sec:app_subsamples) and find no systematics.

## Spatial extent of the dust continuum emission

![image]({uvstack.nocomp.remove7m.cont.rob.scales.maps}.pdf)\
![image]({uvstack.nocomp.remove7m.cont.rob.scales.epsflux}.pdf) ![image]({uvstack.nocomp.remove7m.cont.rob.scales.profile}.pdf)\

We investigate whether the extended emission is specific to the $\text{\textsc{[C ii]}}$ line by replicating the analysis for the dust-continuum emission. The stacking method is fully described in Section [2.2.3](#sec:uvstackmethod). In short, from each full dataset (no continuum subtraction performed) of the clean sample, we removed a total bandwidth of $2.5\times\mathrm{FWHM}$ around the $\text{\textsc{[C ii]}}$ line, and imaged the remaining channels together, thereby creating the $uv$-stacked dust continuum map. We show the results in Figure [8](#fig:uvstackcont). Based on the cumulative aperture flux, the total flux density saturates at 10 kpc, as was the case with the $\text{\textsc{[C ii]}}$ emission. The final value of $2.05 \pm 0.07$ mJy is consistent with the mean of individual continuum measurements (cite: venemans20) indicating that no object is biasing our stacked results at a significant level. The dirty beam sidelobes levels are 3% at most. The curve of growth is steeper in the core for the continuum, compared to the $\text{\textsc{[C ii]}}$. The dust continuum half-light radius, defined as in the previous section, is $0.86 \pm 0.03$ kpc, and the emission contained within 2, 3, 4, 5 and 10 kpc corresponds to 75%, 80%, 85%, 90% and 100% of the total, respectively.

The compactness of the dust continuum emission is evident in the surface brightness profile, shown in Figure [8](#fig:uvstackcont). The emission drops to 1% of the peak beyond 4 kpc (compared to 6 kpc in case of $\text{\textsc{[C ii]}}$). However, at radii beyond 2 kpc we also find an extended component with a significance of $>3\sigma$ up to a radius of 5 kpc (and $>2\sigma$ up to 7 kpc). The exponential function has a scale length consistent with the one we find for the $\text{\textsc{[C ii]}}$ emission.

In summary, both the $\text{\textsc{[C ii]}}$ and the dust continuum emission show two-component profiles, where the scale lengths of the extended components are consistent between the two. The central component, which dominates the half-light radius measurement, is more compact in the case of the dust continuum emission.

## High-velocity outflows

![]({spectra.stack.nocomp.sig}.pdf)

![image]({uvstack.nocomp.remove7m.sig.delta0.2.sig.eps_spectrum}.pdf) ![image]({uvstack.all.sig.delta0.2.sig.eps_spectrum}.pdf)\
![image]({uvstack.nocomp.remove7m.sig4.5.delta3.0.rob.scales.maps}.pdf) ![image]({uvstack.all.sig4.5.delta3.0.rob.scales.maps}.pdf)

We turn our attention to the $\text{\textsc{[C ii]}}$ spectra to investigate the possible presence of broad components that may be indicative of outflows.

A single Gaussian describes the $\text{\textsc{[C ii]}}$ spectrum well in all of the individual cases (see Appendix [13](#sec:app_sources)), except in a few that are known for hosting a merger or a companion system (see Section [2.3](#sec:comp)). The stacked spectrum is also well fit by a single Gaussian, as shown in Figure [9](#fig:aperspecstack). Here, the peak of the stacked $\text{\textsc{[C ii]}}$ line is detected at a S/N of 32 in velocity bins of $0.2\sigma_{\mathrm{line}}$. There is no evidence of any broad spectral component. Fitting two Gaussians would collect marginally more emission, only at velocities between $-6\sigma_{\mathrm{line}}$ and $-2\sigma_{\mathrm{line}}$, yielding 3% larger integrated line flux density. One caveat of this stacking approach is that it relies on manually-chosen aperture sizes, which means that all stacked objects do not contribute equally on all spatial scales. We further improve on the result by performing a $uv$-plane spectral stack next.

We also find no evidence for a broad spectral component, indicative of a high-velocity outflow, in the $\text{\textsc{[C ii]}}$ spectrum of the $uv$-stacked data. The $\text{\textsc{[C ii]}}$ spectrum drawn from the on the $uv$-stacked and imaged data cube of the clean sample (sample 4 from the Section [2.4](#sec:samples)) is presented in the left panels of Figure [10](#fig:uvspecstack). The spectral $uv$-stacking procedure is described in detail in Section [2.2.3](#sec:uvstackmethod). In short, from each continuum subtracted dataset we selected channels that accumulate to slices of $0.2\sigma_{\mathrm{line}}$. We then imaged together slices that correspond to the same offset from the line peak. There are 100 such slices, covering velocities between $\pm10\sigma_{\mathrm{line}}$.

The rms noise in the velocity range between $\pm6\sigma_{\mathrm{line}}$ is 60 $\mu\mathrm{Jy}\,\mathrm{beam}^{-1}$ per channel of $0.2\sigma_{\mathrm{line}}$ (which on average corresponds to 30 $\text{km\,s}^{-1}$). We measured the $2\ensuremath{''}$ radius aperture spectrum (residual corrected) from the $uv$-stack imaged cube, which should encompass the entire $\text{\textsc{[C ii]}}$ emission, according to our previous spatial scale analysis. Additionally, we performed a single beam (i.e. single pixel) measurement at the central $\text{\textsc{[C ii]}}$ peak position following (cite: decarli18). These two measurements are both necessary as we do not know the spatial scale of the potential broad spectral component. Outflows are more likely to be dominant at small angular offsets from the quasar, however this is not the case if the high velocity component is due to companion galaxies. The residuals that remain after subtracting a single Gaussian from the spectrum show no evidence of a broad spectral component, either in the core, or on large scales (see Figure [10](#fig:uvspecstack)). The total $\text{\textsc{[C ii]}}$ flux contained within the single Gaussian fit, taking the $\sigma_{\mathrm{line}}=150\,\ensuremath{\text{km\,s}^{-1}}$, is equal to $2.9 \pm 0.1\,\ensuremath{\text{Jy\,km\,s}^{-1}}$, consistent with the value measured from the $uv$-stacked intensity map (see Section [4.1](#sec:results_ciiextent)). The difference in the cumulative flux density across the spectrum between the observed data and the fit is less than 1%. If we measure the $\text{\textsc{[C ii]}}$ spectrum in an annulus between 1$\ensuremath{''}$ and 2$\ensuremath{''}$, the spectral shape is equivalent to the single beam and the full aperture measurement.

Even when maximising the available signal, we recover no broad component of emission. We therefore selected and stacked velocity ranges between $\pm (3~\mathrm{to}~6) \sigma_{\mathrm{line}}$ in the $uv$-plane. This velocity range corresponds to 450 – 900 $\text{km\,s}^{-1}$ on average. If a broad spectral component were to exist, its S/N would be maximized in such a map, which is shown in Figure [10](#fig:uvspecstack). This map has an rms noise level of $10.8\,\ensuremath{\mu\mathrm{Jy}\,\mathrm{beam}^{-1}}$, and can be considered as a collapse over 900 $\text{km\,s}^{-1}$. No significant emission is detected, i.e. the map is consistent with pure random noise. To be certain that we have not missed any fainter, more extended emission, we repeated the analysis on the full $uv$-stacking data sample (sample 3 from the Section [2.4](#sec:samples)). The spectrum and map of these wings are shown in the right panels of Figure [10](#fig:uvspecstack). The rms noise in the cube is 48 $\mu\mathrm{Jy}\,\mathrm{beam}^{-1}$ per channel, which is 20% lower compared to the more restricted clean sample. The final result remains the same.

We conclude that, on average, $z\gtrsim6$ quasar host galaxies do not show evidence of broad-linewidth $\text{\textsc{[C ii]}}$ outflow, in either the aperture spectrum, single beam spectrum, or the extended wings map. However, we cannot rule out the possibility of a very faint outflow, below our stack detection limit. For that purpose we define an upper limit on the outflow emission as follows. By taking the rms level of the wings map, and its bandwidth, we estimate a $3\sigma$ upper limit on the outflow in the very core (single $\sim1$ kpc beam) of 0.03 $\text{Jy\,km\,s}^{-1}$, which corresponds to less than 5% of the core peak emission. Alternatively, the spatially integrated $\text{\textsc{[C ii]}}$ line of average $\mathrm{FWHM}\sim 350\,\ensuremath{\text{km\,s}^{-1}}$ detected at peak $\mathrm{S/N}\sim30$ in velocity bins of $\sim30\,\ensuremath{\text{km\,s}^{-1}}$ shows no outflow signatures. If outflows are ubiquitous in high-redshift quasar host galaxies, the flux contained in such a broad component is negligible compared to the main narrow component. Although individual objects may exhibit significant outflows, these galaxies should then be considered as being outliers (we found no such object in our studied sample). We note that a secondary broad spectral feature can be obtained if one does not employ linewidth normalization, as discussed in Appendix [12](#sec:app_velstack).

# Discussion

In the following sections we interpret and discuss our results in the context of published work.

## Spatial extent of the $\text{\textsc{[C ii]}}$ and dust emission

![]({uvstack.ciicont.profile.main}.pdf)

![]({size_evol}.pdf)

We find that the dust continuum and the interstellar gas, traced by the $\text{\textsc{[C ii]}}$ emission, follow the same exponential surface brightness profiles extending between 2 and 10 kpc, as shown in Figure [11](#fig:profiles_compare), implying that the $\text{\textsc{[C ii]}}$-to-FIR ratio[^20] is constant at large radii. These similar extents imply that the $\text{\textsc{[C ii]}}$ emission is tracing the ISM of the galaxies, rather than halos or outflows.

The central ISM component dominates the dust and $\text{\textsc{[C ii]}}$ emission. The emission within 2 kpc contains 55% (75%) of the total $\text{\textsc{[C ii]}}$ (dust continuum) flux density with a 20% (10%) contribution from beyond 5 kpc. Such observations are rare for high-redshift quasar host galaxies. For the $z\sim6.4$ quasar SDSS J1148+5251 (cite: walter03; walter09) found a compact $\text{\textsc{[C ii]}}$ emission embedded in a more extended gas reservoir (traced by the CO line). However, these observations could not recover the faint component probed here via stacking due to sensitivity constraints. Recently, more high-resolution observations were conducted targeting additional quasar host galaxies. These showed that the dust emission is also centrally concentrated, even more so than the $\text{\textsc{[C ii]}}$ emission (cite: wang19; venemans19).

Although their properties differ from those of our $z\sim6$ quasar host galaxies, the majority of previously observed and simulated star-forming galaxies also appear to exhibit a dominant, compact component of $\text{\textsc{[C ii]}}$ and/or dust emission (cite: olsen15; hodge16; chen17; calistro-rivera18; gullberg18; gullberg19; cochrane19; rybak19). Some high-redshift observations also recover extended faint components of $\text{\textsc{[C ii]}}$ or dust emission (cite: rybak19; gullberg19; fujimoto19; fujimoto20).

The extent of the ISM in our quasar host galaxies, traced by $\text{\textsc{[C ii]}}$ and dust emission, appears to be consistent with the expected extent of the stellar component. For high-redshift quasar host galaxies, such as our sample, no stellar emission has been detected likely due to the presence of a strong central point source and dust obscuration (cite: mechtley12). We therefore compare the $\text{\textsc{[C ii]}}$ and dust sizes measured here to the predictions from the ZFOURGE survey, see Figure [12](#fig:size_evol). Based on the simulations of (cite: marshall19b), which probe the properties of quasar host galaxies, we assume that galaxies in our sample have stellar masses of $10^{10.5 - 11}$ $\mathrm{M}_{\odot}$. For galaxies of these stellar masses at $z\sim7$, the stellar mass - size evolution fit by (cite: allen17) indicates that our sample should have stellar half-light radii of 1 – 2 kpc, consistent with the $\text{\textsc{[C ii]}}$ and dust half-light radii. Note that for the $z\sim4.3$ star-forming galaxy, for which the $\text{\textsc{[C ii]}}$ was probed at high sensitivity, (cite: neeleman20) measure consistent $\text{\textsc{[C ii]}}$ and stellar half-light radii. Moreover, studies of local galaxies typically find consistent stellar and dust half-light radii, albeit with some scatter depending on the wavelength of the two tracers (cite: leroy09; hunt15; casasola17).

## Dust emission from the MassiveFIRE simulation

![image]({mfire_b}.pdf) ![image]({mfire_c}.pdf) ![image]({mfire_d}.pdf) ![image]({mfire_stack}.pdf)

We compare our observational data with predictions from the MassiveFIRE suite of cosmological zoom-in simulations (cite: feldmann16; feldmann17), which is a part of the Feedback in Realistic Environments (FIRE) project (cite: hopkins14). Galaxy formation simulations offer the prospect of studying the properties of massive, high-redshift galaxies with high spatial resolution and from multiple viewing angles.

All simulations start from cosmological initial conditions and account for star formation and various stellar feedback channels such as momentum injection from supernovae, stellar winds, photo-heating, and radiation pressure. Feedback from SMBHs is not included. The physical model employed by these FIRE simulations is described in detail in (cite: hopkins14). The spatially resolved UV-to-mm spectral energy distributions (SEDs) are calculated in post-processing via self-consistent dust radiative transfer calculations with the help of SKIRT (cite: baes11; baes15). A cosmic microwave background temperature floor is included in the calculation. ALMA broadband fluxes are computed by convolving the redshifted SEDs with the ALMA transmission functions. Further details are described in (cite: liang19).

In Figure [13](#fig:simul), we show several examples of galaxies from the D and E series of the MassiveFIRE suite at $z = 6$. These simulated galaxies reside in halos with virial masses of $(2-6)\times10^{12}\,\ensuremath{\mathrm{M}_{\odot}}$, have star-formation rates (SFRs) of 70 – 400 $\mathrm{M}_{\odot}\,\mathrm{yr}^{-1}$, and total IR luminosities (8 – 1000 $\mu$m) of about $10^{12}$ $\mathrm{L}_{\odot}$, comparable to our sample of quasar hosts. We calculate the radial profile of the sub-mm emission by stacking the predicted 1.2 mm ALMA flux density maps of five simulated galaxies, each viewed from 18 random directions, and by averaging the flux densities in radial annuli. As for the observational data, all intrinsic structure (different disk orientations etc.) are smoothed out by stacking the simulated galaxies’ emission. The stacked 1.2 mm flux density profile of MassiveFIRE galaxies closely follows both the SFR surface density as well as the dust column density profiles.

The radial dust profile of the stacked MassiveFIRE galaxies closely follows the radial profile of the dust and $\text{\textsc{[C ii]}}$ emission of our quasar host galaxies at radii beyond 2 kpc (shown in Figure [11](#fig:profiles_compare)), while the core emission differs, most likely due to selection bias. The observed sources host an actively accreting SMBH at their centers, which may be associated with enhanced levels of star formation activity, whereas the simulated galaxies do not, and are simply matched to our sample in FIR luminosity. Although the simulations and observations do not pertain to the same population of galaxies, we believe that the comparison of the extended profiles is valid, assuming that the feedback from the central SMBH does not severely affect the host (gas and dust) at radii beyond 2 kpc. Our findings suggest that the observation of extended sub-mm emission around IR-luminous, high-redshift galaxies may be a consequence of an extended distribution of dust, gas, and active star formation, partially due to the large but irregular morphology of some of these luminous objects. The agreement between simulations and observations suggests that the extended emission seen in the ALMA data are part of the main galaxy’s ISM. Furthermore, the lack of correlation between the quasar’s bolometric luminosity and the host’s FIR emission (cite: venemans20) suggests that the feedback from the active galactic nucleus is not dominating the FIR emission.

## Outflows

We find no evidence for a broad $\text{\textsc{[C ii]}}$ emission line component in the mean spectrum of either the clean or the full quasar host galaxy sample, using multiple analysis approaches, including a novel technique of spectral $uv$-stacking. Individual objects also show no evidence for broad-line outflows. The same spectral shape, consistent with a single Gaussian, is measured in the central beam ($<1$ kpc), the larger aperture spectrum ($<10$ kpc), and the extended annulus (5 – 10 kpc) (cite: neeleman20b). A single Gaussian collects 99% of the observed emission, based on the cumulative flux integral. Imaging a wider velocity range, where the broad feature may be expected, also yielded a non-detection. Our results therefore suggest that high-velocity outflows are atypical for $z>6$ quasar host galaxies. Objects in our sample are the brightest emitters at $z\gtrsim6$, and we may expect strong quasar feedback based on their bolometric luminosities. However, the lack of outflow signatures in our results suggest that the ISM is not significantly affected by the wind-like feedback in these systems.

The observational evidence for $\text{\textsc{[C ii]}}$ outflows in $z\sim6$ quasar host galaxies remains contested. (cite: decarli18) found no broad spectral feature in their spectral stack of 23 quasar host galaxy population, although only a relatively short $\sim 8$ min integration time was available per source. Another stacking analysis, utilizing 26 quasar host galaxies at $z\sim6$, was performed by (cite: stanley19). They normalized all line widths prior to stacking and report a broad component of $>700\,$$\text{km\,s}^{-1}$, albeit at less than $1.5\sigma$ significance, which reaches a maximum of $2.5\sigma$ from a favourably-selected subsample. Their result is therefore formally consistent with a non-detection, which is also supported by the deeper data used in our analysis.

(cite: maiolino12) and (cite: cicone15) performed a study of the quasar host galaxy SDSS J1148+5251 and presented evidence for a significant outflow identified as a broad spectral component of $\sim 900\,\ensuremath{\text{km\,s}^{-1}}$, extending out to spatial scales of 30 kpc. To date, these studies represent the only cases where such strong features are reported for a single high-redshift object, which makes SDSS J1148+5251 an outlier in the $z\gtrsim6$ quasar host galaxy population. A spectral stack of 48 quasar host galaxies beyond $z>4.5$, performed by (cite: bischetti19), also appears to reveal a very broad $\sim1730\,$$\text{km\,s}^{-1}$ mean spectral feature (ranging from 700 – 2500 $\text{km\,s}^{-1}$, depending on the subsample), with an integrated flux ratio between the broad and the narrow component of $\sim0.2$ (and 0.05 for the peak ratio).

Our findings appear to be in tension with the results of (cite: bischetti19), although the studies are of comparable depths. Given the high significance of their detection, and the large percentage of the total flux being in the broad component, we would also expect to see a broad line. This discrepancy could be explained by one or a combination of three factors. The first explanation is that stacking spectra of different linewidths in velocity space without witdth normalization may change the spectral shape. This effect could be exacerbated in the sample studied in (cite: bischetti19), as it contains additional objects at $4.5 < z < 6$ with much larger linewidths of up to a FWHM of 800 $\text{km\,s}^{-1}$ (other aforementioned studies limit themselves to $z\gtrsim6$ objects). In Appendix [12](#sec:app_velstack), we demonstrate that the broad wings are identified in the spectra stacked without line width renormalization. However, from the shape of the residual, we argue that this is, at least in part, an artifact resulting from the linear addition of Gaussians with various widths. The second explanation for the discrepancy is that faint or blended companion galaxies that are unresolved at the available resolution could contribute to the broadening of the $\text{\textsc{[C ii]}}$ line (with the recent addition of new high resolution data, three additional quasar host galaxies in their sample now have confirmed nearby companions, see Section [2.3](#sec:comp), besides those already considered by the authors). The third possible issue is that when computing the continuum for its subtraction, (cite: bischetti19) use a zeroth order polynomial on a quarter of the available bandwidth, which ensures that the $\text{\textsc{[C ii]}}$ line is properly excluded from the fit, but reduces the S/N of the fit.

The quasar host galaxy samples used in (cite: decarli18), (cite: bischetti19), and (cite: stanley19), largely overlap with our work (our studied sources constitute 15/27, 22/48, and 18/26 of the sample in the three mentioned papers, respectively), which makes the range of different reported results puzzling. We emphasize that our study is building upon the above mentioned studies by analyzing previously unavailable $\sim$1 kpc resolution data, which allows us to better identify merging or companion systems, as well as to resolve extended features, if present. However, a weak link of the analysis in all of the present studies lies in securely separating the continuum from the potential broad spectral component. The trade-off between selecting velocities far enough from the $\text{\textsc{[C ii]}}$ line, and the resulting S/N of the continuum fit is likely the greatest culprit causing inconsistent results. In this paper we employed two methods of continuum subtraction. The first one depends on extracting the spectrum from the full (line plus continuum) cube, and fitting it with a Gaussian plus a constant line. The second one relies on the uvcontsub task in CASA to fit the continuum component in the visibilities using a slope and disregarding on average $\sim900$ $\text{km\,s}^{-1}$ worth of data centered on the $\text{\textsc{[C ii]}}$ line. Both methods yielded the same result, i.e. a non-detection. The only way to properly address this issue would be to observe much wider bandwidths around the line. In addition, there are multiple effects inherent to interferometric data that could bias the measurements if not properly accounted for. Image plane based stacking will result in a beam that is difficult to interpret, and the final map will be a complex combination of dirty residuals, each with a different PSF, and cleaned components. We attempted to mitigate these issues by performing stacking in the $uv$-plane, and applying the residual scaling method to account for the subtleties (see Section [3.1.1](#sec:methods_aperture)) inherent to any cleaned map.

# Conclusions

We have investigated the extent of the interstellar gas and dust in $z\gtrsim6$ quasar host galaxies using ALMA observations of the $\text{\textsc{[C ii]}}$ emission line and the underlying continuum. Our sample consists of 27 objects observed at the high resolution of $\sim1$ kpc, with lower resolution archival data available for 20 objects. We apply the novel approach of $uv$-plane spectral stacking in order to mitigate the issue of beam matching and uncleaned flux, which can become a significant hindrance in image-based stacking methods. This improved the S/N and the fidelity of our analysis. Depending on the subsample under investigation, we can accumulate up to 34 h (with 25.5 h on the 12 m array) of on-source time. From the individual and stacked analysis we conclude the following.

1.  Quasar host galaxies at $z\gtrsim 6$ are characterized by a central ($<2\,$kpc) concentration of $\text{\textsc{[C ii]}}$ and dust emission, with mean half-light radii of $1.6 \pm 0.1$ kpc and $0.86 \pm 0.03$ kpc, respectively. By stacking we recover a region of fainter $\text{\textsc{[C ii]}}$ and dust emission that extends out to 10 kpc, which is well described by an exponential function with a scale length of 2 kpc. Beyond 5 kpc, the mean surface brightness is observed at values less than 1 – 2% of the peak, and contributes 10 – 20% to the total measured flux density.

2.  The large spatial extent of the dust continuum matches that of the $\text{\textsc{[C ii]}}$, suggesting that we are observing the gas and dust of the interstellar medium of the quasar host galaxies extending out to 10 kpc. The extended dust surface brightness profile follows the same trend as obtained from the simulations of massive galaxies (MassiveFIRE) at similar far-infrared luminosities as our sample, further strengthening our interpretation.

3.  We find no evidence of a high-velocity ($\gtrsim 500\,\ensuremath{\text{km\,s}^{-1}}$) $\text{\textsc{[C ii]}}$ component, that may be indicative of outflows, in our $z\gtrsim6$ quasar host galaxy sample. The mean velocity profile of the $\text{\textsc{[C ii]}}$ line is consistent with a single Gaussian, with less than 1% flux excess on both small ($<2\,$kpc), and large ($<10\,$kpc) spatial scales. This finding suggests that the ISM in these extremely active objects is not significantly affected by wind-like feedback.

Our findings imply that the extended emission is due to the extended ISM in the host galaxies, and that no additional component (e.g. a galaxy halo, or a broad-line outflow) needs to be invoked to interpret the measurements.

# Acknowledgments

We thank the anonymous referee for providing helpful suggestions that improved the clarity of the paper. Ml.N., B.P.V., F.W., Ma.N., and A.B.D. acknowledge support from the ERC Advanced Grant 740246 (Cosmic Gas). M.K. acknowledges support from the International Max Planck Research School for Astronomy and Cosmic Physics at Heidelberg University (IMPRS-HD). R.F. acknowledges financial support from the Swiss National Science Foundation (grant no 157591). MassiveFIRE simulations were run with resources provided by the NASA High-End Computing (HEC) Program through the NASA Advanced Supercomputing (NAS) Division at Ames Research Center, proposal SMD-14-5492. Additional computing support was provided by HEC allocations SMD-14-5189, SMD-15-5950, and NSF XSEDE allocations AST120025, AST150045.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00240.S,\
ADS/JAO.ALMA#2012.1.00882.S,\
ADS/JAO.ALMA#2013.1.00273.S,\
ADS/JAO.ALMA#2015.1.00399.S,\
ADS/JAO.ALMA#2015.1.00606.S,\
ADS/JAO.ALMA#2015.1.00692.S,\
ADS/JAO.ALMA#2015.1.00997.S,\
ADS/JAO.ALMA#2015.1.01115.S,\
ADS/JAO.ALMA#2016.1.00544.S,\
ADS/JAO.ALMA#2016.A.00018.S,\
ADS/JAO.ALMA#2017.1.00396.S,\
ADS/JAO.ALMA#2017.1.01301.S,\
ADS/JAO.ALMA#2018.1.00908.S.\
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This research makes use of CASA (cite: mcmullin07), Astropy,[^21] a community-developed core Python package for Astronomy (cite: astropy:2013; astropy:2018), Matplotlib (cite: Hunter:2007), and Topcat (cite: topcat) .

natexlab

(ref: allen17) Allen, R. J., Kacprzak, G. G., Glazebrook, K., et al. 2017, ApJL, 834, L11, doi: [`10.3847/2041-8213/834/2/L11`](http://doi.org/10.3847/2041-8213/834/2/L11)

(ref: arnaboldi07) Arnaboldi, M., Neeser, M. J., Parker, L. C., et al. 2007, The Messenger, 127, 28

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: banados16) Bañados, E., Venemans, B. P., Decarli, R., et al. 2016, ApJS, 227, 11, doi: [`10.3847/0067-0049/227/1/11`](http://doi.org/10.3847/0067-0049/227/1/11)

(ref: banados18) Bañados, E., Venemans, B. P., Mazzucchelli, C., et al. 2018, Nature, 553, 473, doi: [`10.1038/nature25180`](http://doi.org/10.1038/nature25180)

(ref: banados19) Bañados, E., Novak, M., Neeleman, M., et al. 2019a, ApJL, 881, L23, doi: [`10.3847/2041-8213/ab3659`](http://doi.org/10.3847/2041-8213/ab3659)

(ref: banados19b) Bañados, E., Rauch, M., Decarli, R., et al. 2019b, ApJ, 885, 59, doi: [`10.3847/1538-4357/ab4129`](http://doi.org/10.3847/1538-4357/ab4129)

(ref: baes15) Baes, M., & Camps, P. 2015, Astronomy and Computing, 12, 33, doi: [`10.1016/j.ascom.2015.05.006`](http://doi.org/10.1016/j.ascom.2015.05.006)

(ref: baes11) Baes, M., Verstappen, J., De Looze, I., et al. 2011, ApJS, 196, 22, doi: [`10.1088/0067-0049/196/2/22`](http://doi.org/10.1088/0067-0049/196/2/22)

(ref: bischetti19) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, A&A, 630, A59, doi: [`10.1051/0004-6361/201833557`](http://doi.org/10.1051/0004-6361/201833557)

(ref: calistro-rivera18) Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56, doi: [`10.3847/1538-4357/aacffa`](http://doi.org/10.3847/1538-4357/aacffa)

(ref: carilliwalter13) Carilli, C. L., & Walter, F. 2013, Annual Review of Astronomy and Astrophysics, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: casasola17) Casasola, V., Cassarà, L. P., Bianchi, S., et al. 2017, A&A, 605, A18, doi: [`10.1051/0004-6361/201731020`](http://doi.org/10.1051/0004-6361/201731020)

(ref: chambers16) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, arXiv e-prints, arXiv:1612.05560. [`https://arxiv.org/abs/1612.05560`](https://arxiv.org/abs/1612.05560)

(ref: chen17) Chen, C.-C., Hodge, J. A., Smail, I., et al. 2017, ApJ, 846, 108, doi: [`10.3847/1538-4357/aa863a`](http://doi.org/10.3847/1538-4357/aa863a)

(ref: cicone15) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14, doi: [`10.1051/0004-6361/201424980`](http://doi.org/10.1051/0004-6361/201424980)

(ref: cochrane19) Cochrane, R. K., Hayward, C. C., Anglés-Alcázar, D., et al. 2019, MNRAS, 488, 1779, doi: [`10.1093/mnras/stz1736`](http://doi.org/10.1093/mnras/stz1736)

(ref: derosa11) De Rosa, G., Decarli, R., Walter, F., et al. 2011, ApJ, 739, 56, doi: [`10.1088/0004-637X/739/2/56`](http://doi.org/10.1088/0004-637X/739/2/56)

(ref: derosa14) De Rosa, G., Venemans, B. P., Decarli, R., et al. 2014, ApJ, 790, 145, doi: [`10.1088/0004-637X/790/2/145`](http://doi.org/10.1088/0004-637X/790/2/145)

(ref: decarli17) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: decarli18) —. 2018, ApJ, 854, 97, doi: [`10.3847/1538-4357/aaa5aa`](http://doi.org/10.3847/1538-4357/aaa5aa)

(ref: decarli19) Decarli, R., Dotti, M., Bañados, E., et al. 2019, ApJ, 880, 157, doi: [`10.3847/1538-4357/ab297f`](http://doi.org/10.3847/1538-4357/ab297f)

(ref: fan06) Fan, X., Strauss, M. A., Becker, R. H., et al. 2006, AJ, 132, 117, doi: [`10.1086/504836`](http://doi.org/10.1086/504836)

(ref: farina19) Farina, E. P., Arrigoni-Battaia, F., Costa, T., et al. 2019, ApJ, 887, 196, doi: [`10.3847/1538-4357/ab5847`](http://doi.org/10.3847/1538-4357/ab5847)

(ref: feldmann16) Feldmann, R., Hopkins, P. F., Quataert, E., Faucher-Giguère, C.-A., & Kereš, D. 2016, MNRAS, 458, L14, doi: [`10.1093/mnrasl/slw014`](http://doi.org/10.1093/mnrasl/slw014)

(ref: feldmann17) Feldmann, R., Quataert, E., Hopkins, P. F., Faucher-Giguère, C.-A., & Kereš, D. 2017, MNRAS, 470, 1050, doi: [`10.1093/mnras/stx1120`](http://doi.org/10.1093/mnras/stx1120)

(ref: ferrara19) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1, doi: [`10.1093/mnras/stz2031`](http://doi.org/10.1093/mnras/stz2031)

(ref: fujimoto19b) Fujimoto, S., Oguri, M., Nagao, T., Izumi, T., & Ouchi, M. 2020a, ApJ, 891, 64, doi: [`10.3847/1538-4357/ab718c`](http://doi.org/10.3847/1538-4357/ab718c)

(ref: fujimoto19) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107, doi: [`10.3847/1538-4357/ab480f`](http://doi.org/10.3847/1538-4357/ab480f)

(ref: fujimoto20) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020b, arXiv e-prints, arXiv:2003.00013. [`https://arxiv.org/abs/2003.00013`](https://arxiv.org/abs/2003.00013)

(ref: gullberg18) Gullberg, B., Swinbank, A. M., Smail, I., et al. 2018, ApJ, 859, 12, doi: [`10.3847/1538-4357/aabe8c`](http://doi.org/10.3847/1538-4357/aabe8c)

(ref: gullberg19) Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, MNRAS, 490, 4956, doi: [`10.1093/mnras/stz2835`](http://doi.org/10.1093/mnras/stz2835)

(ref: hodge16) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: hollenbach99) Hollenbach, D. J., & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71, 173, doi: [`10.1103/RevModPhys.71.173`](http://doi.org/10.1103/RevModPhys.71.173)

(ref: hopkins14) Hopkins, P. F., Kereš, D., Oñorbe, J., et al. 2014, MNRAS, 445, 581, doi: [`10.1093/mnras/stu1738`](http://doi.org/10.1093/mnras/stu1738)

(ref: hunt15) Hunt, L. K., Draine, B. T., Bianchi, S., et al. 2015, A&A, 576, A33, doi: [`10.1051/0004-6361/201424734`](http://doi.org/10.1051/0004-6361/201424734)

(ref: Hunter:2007) Hunter, J. D. 2007, Computing In Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: jiang16) Jiang, L., McGreer, I. D., Fan, X., et al. 2016, ApJ, 833, 222, doi: [`10.3847/1538-4357/833/2/222`](http://doi.org/10.3847/1538-4357/833/2/222)

(ref: jorsater95) Jorsater, S., & van Moorsel, G. A. 1995, AJ, 110, 2037, doi: [`10.1086/117668`](http://doi.org/10.1086/117668)

(ref: lawrence07) Lawrence, A., Warren, S. J., Almaini, O., et al. 2007, MNRAS, 379, 1599, doi: [`10.1111/j.1365-2966.2007.12040.x`](http://doi.org/10.1111/j.1365-2966.2007.12040.x)

(ref: leroy09) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670, doi: [`10.1088/0004-6256/137/6/4670`](http://doi.org/10.1088/0004-6256/137/6/4670)

(ref: liang19) Liang, L., Feldmann, R., Kereš, D., et al. 2019, MNRAS, 489, 1397, doi: [`10.1093/mnras/stz2134`](http://doi.org/10.1093/mnras/stz2134)

(ref: maiolino12) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66, doi: [`10.1111/j.1745-3933.2012.01303.x`](http://doi.org/10.1111/j.1745-3933.2012.01303.x)

(ref: marshall19b) Marshall, M. A., Ni, Y., Di Matteo, T., et al. 2019, arXiv e-prints, arXiv:1912.03428. [`https://arxiv.org/abs/1912.03428`](https://arxiv.org/abs/1912.03428)

(ref: uvmultifit) Martı́-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563, A136, doi: [`10.1051/0004-6361/201322633`](http://doi.org/10.1051/0004-6361/201322633)

(ref: matsuoka18) Matsuoka, Y., Strauss, M. A., Kashikawa, N., et al. 2018, ApJ, 869, 150, doi: [`10.3847/1538-4357/aaee7a`](http://doi.org/10.3847/1538-4357/aaee7a)

(ref: mazzucchelli17) Mazzucchelli, C., Bañados, E., Venemans, B. P., et al. 2017, ApJ, 849, 91, doi: [`10.3847/1538-4357/aa9185`](http://doi.org/10.3847/1538-4357/aa9185)

(ref: mcmullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, Vol. 376, 127

(ref: mechtley12) Mechtley, M., Windhorst, R. A., Ryan, R. E., et al. 2012, ApJL, 756, L38, doi: [`10.1088/2041-8205/756/2/L38`](http://doi.org/10.1088/2041-8205/756/2/L38)

(ref: morganson12) Morganson, E., De Rosa, G., Decarli, R., et al. 2012, AJ, 143, 142, doi: [`10.1088/0004-6256/143/6/142`](http://doi.org/10.1088/0004-6256/143/6/142)

(ref: mortlock11) Mortlock, D. J., Warren, S. J., Venemans, B. P., et al. 2011, Nature, 474, 616, doi: [`10.1038/nature10159`](http://doi.org/10.1038/nature10159)

(ref: neeleman20) Neeleman, M., Prochaska, J. X., Kanekar, N., & Rafelski, M. 2020, Nature, 581, 269, doi: [`10.1038/s41586-020-2276-y`](http://doi.org/10.1038/s41586-020-2276-y)

(ref: neeleman20b) Neeleman, M., Venemans, B., Walter, F., & Novak, M. 2020, in prep.

(ref: neeleman19) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10, doi: [`10.3847/1538-4357/ab2ed3`](http://doi.org/10.3847/1538-4357/ab2ed3)

(ref: novak19) Novak, M., Bañados, E., Decarli, R., et al. 2019, ApJ, 881, 63, doi: [`10.3847/1538-4357/ab2beb`](http://doi.org/10.3847/1538-4357/ab2beb)

(ref: olsen15) Olsen, K. P., Greve, T. R., Narayanan, D., et al. 2015, ApJ, 814, 76, doi: [`10.1088/0004-637X/814/1/76`](http://doi.org/10.1088/0004-637X/814/1/76)

(ref: pavesi16) Pavesi, R., Riechers, D. A., Capak, P. L., et al. 2016, ApJ, 832, 151, doi: [`10.3847/0004-637X/832/2/151`](http://doi.org/10.3847/0004-637X/832/2/151)

(ref: astropy:2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: rujopakarn19) Rujopakarn, W., Daddi, E., Rieke, G. H., et al. 2019, ApJ, 882, 107, doi: [`10.3847/1538-4357/ab3791`](http://doi.org/10.3847/1538-4357/ab3791)

(ref: rybak19) Rybak, M., Calistro Rivera, G., Hodge, J. A., et al. 2019, ApJ, 876, 112, doi: [`10.3847/1538-4357/ab0e0f`](http://doi.org/10.3847/1538-4357/ab0e0f)

(ref: stanley19) Stanley, F., Jolly, J. B., König, S., & Knudsen, K. K. 2019, A&A, 631, A78, doi: [`10.1051/0004-6361/201834530`](http://doi.org/10.1051/0004-6361/201834530)

(ref: topcat) Taylor, M. B. 2005, Astronomical Society of the Pacific Conference Series, Vol. 347, TOPCAT & STIL: Starlink Table/VOTable Processing Software, ed. P. Shopbell, M. Britton, & R. Ebert, 29

(ref: vallini17) Vallini, L., Ferrara, A., Pallottini, A., & Gallerani, S. 2017, MNRAS, 467, 1300, doi: [`10.1093/mnras/stx180`](http://doi.org/10.1093/mnras/stx180)

(ref: venemans20) Venemans, B., Walter, F., Neeleman, M., et al. 2020, accepted, ApJ

(ref: venemans07) Venemans, B. P., McMahon, R. G., Warren, S. J., et al. 2007, MNRAS, 376, L76, doi: [`10.1111/j.1745-3933.2007.00290.x`](http://doi.org/10.1111/j.1745-3933.2007.00290.x)

(ref: venemans19) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJL, 874, L30, doi: [`10.3847/2041-8213/ab11cc`](http://doi.org/10.3847/2041-8213/ab11cc)

(ref: venemans17b) Venemans, B. P., Walter, F., Decarli, R., et al. 2017a, ApJ, 845, 154, doi: [`10.3847/1538-4357/aa81cb`](http://doi.org/10.3847/1538-4357/aa81cb)

(ref: venemans17c) —. 2017b, ApJ, 851, L8, doi: [`10.3847/2041-8213/aa943a`](http://doi.org/10.3847/2041-8213/aa943a)

(ref: walter08) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563, doi: [`10.1088/0004-6256/136/6/2563`](http://doi.org/10.1088/0004-6256/136/6/2563)

(ref: walter09) Walter, F., Riechers, D., Cox, P., et al. 2009, Nature, 457, 699, doi: [`10.1038/nature07681`](http://doi.org/10.1038/nature07681)

(ref: walter03) Walter, F., Bertoldi, F., Carilli, C., et al. 2003, Nature, 424, 406, doi: [`10.1038/nature01821`](http://doi.org/10.1038/nature01821)

(ref: wangfeige19) Wang, F., Wang, R., Fan, X., et al. 2019a, ApJ, 880, 2, doi: [`10.3847/1538-4357/ab2717`](http://doi.org/10.3847/1538-4357/ab2717)

(ref: wangfeige18) Wang, F., Yang, J., Fan, X., et al. 2018, ApJL, 869, L9, doi: [`10.3847/2041-8213/aaf1d2`](http://doi.org/10.3847/2041-8213/aaf1d2)

(ref: wang13) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44, doi: [`10.1088/0004-637X/773/1/44`](http://doi.org/10.1088/0004-637X/773/1/44)

(ref: wang19) Wang, R., Shao, Y., Carilli, C. L., et al. 2019b, ApJ, 887, 40, doi: [`10.3847/1538-4357/ab4d4b`](http://doi.org/10.3847/1538-4357/ab4d4b)

(ref: willott15) Willott, C. J., Bergeron, J., & Omont, A. 2015, ApJ, 801, 123, doi: [`10.1088/0004-637X/801/2/123`](http://doi.org/10.1088/0004-637X/801/2/123)

(ref: willott10a) Willott, C. J., Delorme, P., Reylé, C., et al. 2010, AJ, 139, 906, doi: [`10.1088/0004-6256/139/3/906`](http://doi.org/10.1088/0004-6256/139/3/906)

(ref: yang20) Yang, J., Wang, F., Fan, X., et al. 2020, ApJL, 897, L14, doi: [`10.3847/2041-8213/ab9c26`](http://doi.org/10.3847/2041-8213/ab9c26)

(ref: york00) York, D. G., Adelman, J., Anderson, John E., J., et al. 2000, AJ, 120, 1579, doi: [`10.1086/301513`](http://doi.org/10.1086/301513)

# Optimizing Gaussian line detection

In order to calculate the optimal bandwidth across which to integrate a line, we first assume that the emission line has a single Gaussian profile with a line width $\sigma_{\mathrm{line}}$, and that the noise in individual velocity bins is Gaussian and not correlated between neighboring channels. Integrating from the line peak outwards, the collected flux grows as $\mathrm{Signal}= F_{\mathrm{line}} \times \mathrm{erf}(n/\sqrt{2})$, where $F_{\mathrm{line}}$ is the total line flux and $n$ represents the number of $\sigma_{\mathrm{line}}$ to integrate over in both positive and negative velocity directions. The uncertainties from individual velocity channels are added in quadrature, therefore the noise increases with the number of channels in the sum as $\mathrm{Noise}=\sqrt{(2n\sigma_{\mathrm{line}})/ \Delta v} \times \sigma_{\mathbf{rms}}$, where $2n\sigma_{\mathrm{line}}$ is the total integration width and $\sigma_{\mathbf{rms}}$ is the noise measured in a velocity bin $\Delta v$ ($\text{km\,s}^{-1}$) wide. From this, it follows that $S/N \propto \mathrm{erf}(n/\sqrt{2})/\sqrt{n}$. Numerical evaluation of this function yields the maximum value at $n=1.4$, see Figure [14](#fig:optimalsn). Therefore, the total integration width that optimizes the S/N of a Gaussian line is equal to $2.8 \sigma_{\mathrm{line}}$. For a Gaussian, the $\mathrm{FWHM} = 2 \sqrt{2 \ln 2} \sigma_{\mathrm{line}}$, and the total width translates to $\approx1.2\times\mathrm{FWHM}$, which accounts for 84% of the line flux.

![]({optimalsn}.pdf)

# Residual scaling

The derivation of the residual scaling method is rooted in the fact that we should be able to measure the true emission independent of the cleaning threshold. We denote this true flux as $F$. If we clean the map down to two different thresholds, the following must hold $F=C+\epsilon R=C_2+\epsilon R_2$, where $C$ and $R$ refer to aperture fluxes measured in the clean components and the residual maps, respectively (the subscript refers to a different cleaning threshold). The factor $\epsilon$ is the clean beam to dirty beam volume ratio which ensures that the summands have equal units (hence the name residual scaling). A special case is obtained if no cleaning is applied, then $C_2=0$ and $R_2=D$, where $D$ is the aperture flux measured inside the dirty map (i.e. the residual after zero iterations of clean). Solving the two equations yields $\epsilon=C/(D-R)$ and $F=\epsilon D$. The essence of the method lies in measuring the proper dirty beam volume, valid only inside a specific aperture. Because the integral of the dirty beam approaches zero (sum of finite number of cosine waves over all area), its volume is only meaningful inside a finite spatial region. This is not the case with the clean beam, which is a 2D Gaussian whose integral always converges to a finite non-zero value.

# Cleaning without multi-scales

The process of deconvolution, i.e. cleaning, relies on extrapolating the sky model from available visibilities, where the missing Fourier components must be somehow filled in by the algorithm. Therefore, the final sky model is only one of many possible representations that are consistent with the observed data. Throughout this work we utilize the multi-scale clean algorithm as described in Section [2.2.3](#sec:uvstackmethod). If we are using extended source sky model components, the question arises whether we are actually forcing the algorithm to indeed create extended structures. To quantify this effect we re-imaged the $uv$-stack from Section [4.1](#sec:results_ciiextent) without multi-scales, using only delta functions to populate the sky model. The results are shown in Figure [15](#fig:cleancompare).

The final cleaned map shows no significant differences compared to the multi-scale version, and the dirty beam does not change as imaging weights were kept the same. However, the clean sky model is now comprised of individual pixel sources (delta functions), and there is considerably more flux in the residual on large scales (all below $2\sigma$). Nevertheless, both the curves of growth (after applying residual scaling correction) and surface brightness profiles are consistent between the two cleaning approaches.

![image]({uvstack.nocomp.remove7m.sig0.0.delta2.8.rob.maps}.pdf)\
![image]({uvstack.nocomp.remove7m.sig0.0.delta2.8.rob.cleancompare.epsflux}.pdf) ![image]({uvstack.nocomp.remove7m.sig0.0.delta2.8.rob.cleancompare.profile}.pdf)

# Fitting the stacked data in the uv-plane

We fit the $uv$-data of our clean $uv$-stacking sample using the software package uvmultifit (cite: uvmultifit). The fitting model was a linear combination of two radially symmetric exponential brightness profiles (Lorentzians in the $uv$-plane), each with four free parameters: two positional offsets, the total flux, and the major axis FWHM (related to the effective or half-light radius as $R_{\mathrm{eff}}=1.678\times l$, where $l$ is the scale length of the exponential profile, $l=\mathrm{FWHM}/(2\ln2)$). We compare the visibilities binned in $uv$-distances of 5 k$\lambda$ and the fitted model in Figure [16](#fig:uvfit). There is no spatial offset between the two fitted components, but they are both shifted by $\sim17$ mas with respect to the phase center, which was chosen to be the centroid position of the $\text{\textsc{[C ii]}}$ emission for each individual source during the $uv$-stacking process.

The fit yielded the following flux densities, $F$, and exponential scale lengths, $l$, for the compact and the extended components: $F_{\ensuremath{\text{\textsc{[C ii]}}}}^{\mathrm{comp.}} = 2.8 \pm 0.1$ mJy with $l=0.43 \pm 0.02$ kpc, $F_{\ensuremath{\text{\textsc{[C ii]}}}}^{\mathrm{ext.}} = 3.4 \pm 0.2$ mJy with $l=2.6 \pm 0.2$ kpc, $F_{\mathrm{dust}}^{\mathrm{comp.}} = 1.19 \pm 0.03$ mJy with $l=0.20 \pm 0.01$ kpc, and $F_{\mathrm{dust}}^{\mathrm{ext.}} = 0.76 \pm 0.03$ mJy with $l=1.3 \pm 0.1$ kpc. We fitted a second model with one less free parameter, by choosing to fix the scale length of one exponential function to 2 kpc, the value derived from image plane analysis (see Sections [4.1](#sec:results_ciiextent) and [4.2](#sec:results_dustextent)). This fit is shown in Figure [16](#fig:uvfit) with the dashed line, and is still consistent with the observed data points. Fitting in the $uv$-plane circumvents issues with the clean/dirty beam, and yields the conclusions consistent with those presented in the main text.

![image]({uvstack.cii.ampuv.big}.pdf)\
![image]({uvstack.cont.ampuv.big}.pdf)

# Subsamples and biases

![image]({uvstack.cii.ampuv}.pdf) ![image]({uvstack.cont.ampuv}.pdf)\
![image]({uvstack.ciicont.epsflux}.pdf) ![image]({uvstack.ciicont.profile}.pdf)

![image]({uvstack.nocomp.remove7m.teams.sig0.0.delta2.8.ampuv}.pdf) ![image]({uvstack.nocomp.remove7m.teams.sig0.0.delta2.8.rob.scales.epsflux}.pdf) ![image]({uvstack.nocomp.remove7m.teams.sig0.0.delta2.8.rob.scales.profile}.pdf)

In the main text, for $uv$-stacking, we have been using the clean sample, in which all systems with close companions and obvious mergers were removed, in addition to any 7 m array data. Here, we evaluate the robustness of our results by considering smaller and larger data samples.

We first enlarge our clean sample by considering systems with companion galaxies and available 7 m array observations. The 7 m array data are provided by the ALMA compact array (ACA), where smaller dishes allow for denser spacing of antennas, thus allowing measurements of visibilities on shorter baselines compared to the 12 m array. There are only three quasar host galaxies with such observations available in our sample, and one of them is designated as a companion system as well. Hence, the largest spatial scales data in the $uv$-stack will be provided by only two to three objects. Including them in the stack could potentially bias the mean emission measurement. To investigate this effect we define four different samples, which we analyze and present separately in Figure [17](#fig:uvsamples). The four tested samples are:

1.  Clean $uv$-stacking sample (19 objects, 32 datasets), as in the main text.

2.  Clean $uv$-stacking sample with 7 m data added (19 objects, 34 datasets).

3.  Clean $uv$-stacking sample with companion and merger systems added (26 objects, 45 datasets).

4.  Full dataset[^22] containing companion and merger systems, and all the 7 m data (26 objects, 48 datasets).

The two top panels of Figure [17](#fig:uvsamples) demonstrate that amplitudes cannot be described by a single Gaussian in any of the samples, for both $\text{\textsc{[C ii]}}$ and dust continuum emission. Between different samples, the dust continuum measurements show somewhat larger dispersion at short baselines than the $\text{\textsc{[C ii]}}$ values. The 7 m array data double the number of available visibilities below 30 k$\lambda$ (blue vs. black and red vs. yellow lines). The curves of growth shown in the lower left panel of Figure [17](#fig:uvsamples) differ for the four sets of data considered. The inclusion of companion systems increases the mean flux, as one would expect, but the value still saturates at $\sim$10 kpc. The inclusion of the 7 m data requires integration over larger radii to encompass the data from the shortest baselines and results in $\sim$20% larger flux densities of both the $\text{\textsc{[C ii]}}$ and the dust continuum. Because this contribution arises from three or fewer sources, it likely does not represent the mean behavior of full sample of observed $z\sim6$ quasar host galaxies. At small radii the residual scaling is numerically stable, but because of division with a small number (aperture flux densities measured in the residual and the dirty map approach each other), it becomes numerically unstable beyond 7$\ensuremath{''}$. The last panel of Figure [17](#fig:uvsamples) shows the surface brightness profiles, normalized at 2 kpc. All four samples exhibit similar functional forms.

For the remainder of this section we analyze smaller subsamples. Our full sample contains sources that span approximately one order of magnitude in $\text{\textsc{[C ii]}}$ line flux densities ($\sim$1 – 10 $\text{Jy\,km\,s}^{-1}$) and galaxies on the fainter end of this range could have intrinsically different properties from those on the brighter end. Also, the addition of objects at various flux levels in the $uv$-plane can translate into erroneous spatial structure. To quantify possible biases we split our clean sample into three smaller subsamples, based on the flux values measured at the lowest baselines (first available bin of 15 k$\lambda$):

1.  Bright subsample, $\text{\textsc{[C ii]}}$ flux density above 3 $\text{Jy\,km\,s}^{-1}$ (3 objects, 5 datasets).

2.  Medium bright subsample, between 2 – 3 $\text{Jy\,km\,s}^{-1}$ (8 objects, 14 datasets).

3.  Faint subsample, below 2 $\text{Jy\,km\,s}^{-1}$ (8 objects, 13 datasets).

These are presented in Figure [18](#fig:uvsubsamples). Because we are significantly reducing our sample size this way, the S/N becomes poorer. Nevertheless, all our main conclusions hold within the errors. The spatial structure is non-Gaussian, the total $\text{\textsc{[C ii]}}$ flux saturates at $\sim$10 kpc, and surface brightness profiles exhibit extended exponential tails. The bright subsample is composed of only three sources, namely J025–33, P009–10, and P183+05, which all show extended morphology and significant emission within 5 kpc (for details on individual objects see Appendix [13](#sec:app_sources)), thus the surface brightness profile at smaller radii is less steep then the remaining two subsamples.

As a final consistency check we ensured a consistent overlap in $uv$-coverage between all objects by selecting only the high-resolution cycles (sample 1 from Section [2.4](#sec:samples)). The analysis performed on such a selection yielded no new systematics. In summary, our main results regarding the spatial extent of $\text{\textsc{[C ii]}}$ and dust continuum emission remain unchanged across all considered samples.

# Velocity stacks

![image]({spectra.stack.nocomp.vel}.pdf)\
![image]({uvstack.all.vel.delta30.vel.eps_spectrum}.pdf)

Stacking spectra that are individually well described by single Gaussians of different linewidths will result in a spectral shape with at least one narrow and one broad component. To demonstrate this effect, we repeated the $\text{\textsc{[C ii]}}$ stacking from Section [4.3](#sec:results_outflow) without line-width renormalization, in velocity space, and present the results in Figure [19](#fig:aperspecstackvel). After subtracting a single fitted Gaussian from the stacked spectrum, positive residuals can be seen around velocities $\sim400$ $\text{km\,s}^{-1}$ in both the central beam and the larger aperture measurement. The total observed flux density excess compared to a single Gaussian fit remains low, less than 4%, as evident from the cumulative distribution in Figure [19](#fig:aperspecstackvel). The specific shape of the residuals (a peak at zero velocity, followed by one negative and one broader positive feature toward larger velocities) can also be reproduced by averaging pure Gaussian functions, one per object, that correspond to measured $\text{\textsc{[C ii]}}$ lines (in terms of their total fluxes and FWHMs), and then subtracting a single Gaussian fit from the average. The similar shape of the residual is also visible in Figure A.2 from (cite: bischetti19), indicating that at least some excess emission is potentially due to averaging spectra of various line widths.

# Individual source analysis

In this section we provide more details on individual objects. We presented multiple $\text{\textsc{[C ii]}}$ flux diagnostics throughout Section [3](#sec:methods). We show similar analysis for every object of our sample in Figure [20](#fig:individual). We also highlight several particular galaxies as potential interesting follow-up candidates. Three objects, listed in Section [2.3](#sec:comp) as having complex morphology, deserve a mention here. System J0100+2802 exhibits a factor of two increase in $\text{\textsc{[C ii]}}$ flux between 3 and 10 kpc. This source was excluded from our $uv$-stacking analysis and its interpretation is unclear. It was studied in detail by (cite: wangfeige19), and a possible lensing scenario was proposed by (cite: fujimoto19b). Systems J025–33 and P009–10[^23] are both among the brightest in our sample and show a non-Gaussian amplitude distribution in the $uv$-plane. However, it is unclear whether a companion is present, or whether we observe more of the underlying extended emission due to higher surface brightness. Another object where we observe a factor of $\sim2$ increase in flux densities between the central 3 kpc and extended 10 kpc is J0842+1218, as evident in two independent cycles. This system is already known for having a companion galaxy at a separation of 50 kpc (cite: decarli17) and a second, fainter companion at 31 kpc (cite: neeleman19). Similarly, J1044–0125 shows evidence for enhanced emission on large scales, which is particularly interesting as it is hinted at in the 7 m data.

Moreover, P359–06 shows some evidence of extended emission in two separate cycles, although the effect is not as pronounced as in the previous two sources. Finally, we note that P183+05 and P007+04 are identified as proximate damped Ly$\alpha$ absorption systems (cite: banados19b; farina19), which may have some effect on our measurements if the foreground galaxy is aligned with the quasar host.

![image]({appendix.p007p04}.pdf)\
![image]({appendix.p009m10}.pdf)

![image]({appendix.j0100p2802}.pdf)\
![image]({appendix.j0109m3047}.pdf)\
![image]({appendix.j0129m0035}.pdf)\
![image]({appendix.j025m33}.pdf)\
![image]({appendix.p036p03}.pdf)

![image]({appendix.j0305m3150}.pdf)\
![image]({appendix.p065m26}.pdf)\
![image]({appendix.j0842p1218}.pdf)\
![image]({appendix.j1044m0125}.pdf)\
![image]({appendix.j1048m0109}.pdf)

![image]({appendix.p167m13}.pdf)\
![image]({appendix.j1120p0641}.pdf)\
![image]({appendix.p183p05}.pdf)\
![image]({appendix.j1306p0356}.pdf)\
![image]({appendix.j1319p0950}.pdf)

![image]({appendix.j1342p0928}.pdf)\
![image]({appendix.p231m20}.pdf)\
![image]({appendix.p308m21}.pdf)\
![image]({appendix.j2054m0005}.pdf)\
![image]({appendix.j2100m1715}.pdf)

![image]({appendix.p323p12}.pdf)\
![image]({appendix.j2318m3113}.pdf)\
![image]({appendix.j2318m3029}.pdf)\
![image]({appendix.j2348m3054}.pdf)\
![image]({appendix.p359m06}.pdf)

[^1]: Although we happen to have the same number of galaxies, our sample is not the same as the one described in (cite: decarli18), as only 15 objects are shared between the two samples. For our study, we require data obtained at high resolution ($\sim0.25\ensuremath{''}$), in contrast to the $\sim1\ensuremath{''}$ used in (cite: decarli18).

[^2]: E.g., fewer antennas available, sometimes missing calibration data, no pipeline support.

[^3]: Synthesized beam obtained from baseline statistics (see main text), given in arcsec. Nominal high-resolution ($\sim$1 kpc) datasets are marked with boldface.

[^4]: Removed from uv stacking due to data weights outliers or partial line frequency coverage (in case of P009–10, cycle 3).

[^5]: Recalibrated due to wrong Ceres or Pallas flux calibrator models.

[^6]: Cycle 0 observations are also available, but are excluded from our study.

[^7]: Merger or nearby companion identified at $<$ 10  kpc.

[^8]: Higher resolution ($<$40  mas) also available, but discarded here (see main text).

[^9]: The letters refer to the PI initials distinguishing between same cycle observations.

[^10]: Due to data format changes, CASA task definition changes, and backward incompatibility, this process failed for some datasets.

[^11]: We note that we recover the same aperture flux densities in both natural and Briggs weighted maps using the residual scaling method explained in a later section.

[^12]: The value is large enough to accomodate all datasets, but small enough not to introduce any time smearing effects.

[^13]: The task uses small angle approximation, which is valid in our case as shifts are at most few arcseconds large, and less than an arcsecond in most of the cases.

[^14]: This was achieved by putting zeros into PHASE_DIR, DELAY_DIR, REFERENCE_DIR columns of the measurement set.

[^15]: This can be manually overridden by the restoringbeam parameter in tclean, but we made no such attempt.

[^16]: The clean components map can be obtained by either convolving the sky model map (units of Jy/pixel) with the clean beam, or by subtracting the residual map from the final map output by CASA.

[^17]: The convolution kernel is computed from the clean beam only, therefore making its effect on the dirty beam unknown, requiring further quantification.

[^18]: Using only the real part helps to see oscillations around zero flux densities at larger $uv$-distances, whereas amplitudes are by definition always positive.

[^19]: The dust continuum spectral energy distribution is not flat. However, in our case this slope would result in only a few percent difference in flux between the two ends of the observed bandwidth. In a single spectral setup, ALMA provides up to 3.75 GHz of a contiguous bandwidth coverage, which corresponds to $\sim$4000 $\text{km\,s}^{-1}$ at the observed frequency of $\sim$270 GHz, where the $\text{\textsc{[C ii]}}$ line of $z\sim6$ galaxies is redshifted.

[^20]: This refers to the surface-brightness ratio only. Computing the luminosity ratio would require assuming a dust SED, and a spatial dust temperature distribution, which is unknown for these sources (cite: venemans20).

[^21]: http://www.astropy.org

[^22]: Six datasets are always excluded from $uv$-stacking (see Table [\[tab:data\]](#tab:data)).

[^23]: We note that the large discrepancy between fluxes measured in two cycles is due to partial line coverage in the earlier cycle, where only half of the $\text{\textsc{[C ii]}}$ line is observed.

</paper>

Write the methods card for this paper.