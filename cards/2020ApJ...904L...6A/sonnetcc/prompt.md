# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...904L...6A\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...904L...6A",
 "title": "A Case of Simultaneous Star and Planet Formation",
 "year": 2020,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Alves, Felipe O.",
 "n_authors": 7,
 "arxiv_id": "2010.15135",
 "doi": "10.3847/2041-8213/abc550",
 "alma_projects_linked_by_archive": [
  "2013.1.00291.S"
 ]
}
```

Paper text:
<paper>
# A case of simultaneous star and planet formation

## Abstract

While it is widely accepted that planets are formed in protoplanetary disks, there is still much debate on when this process happens. In a few cases protoplanets have been directly imaged, but for the vast majority of systems, disk gaps and cavities – seen especially in dust continuum observations – have been the strongest evidence of recent or on-going planet formation. We present ALMA observations of a nearly edge-on ($i = 
75^{\circ}$) disk containing a giant gap seen in dust but not in $^{12}$CO gas. Inside the gap, the molecular gas has a warm (100 K) component coinciding in position with a tentative free-free emission excess observed with the VLA. Using 1D hydrodynamic models, we find the structure of the gap is consistent with being carved by a planet with 4-70 $M_{\rm Jup}$. The coincidence of free-free emission inside the planet-carved gap points to the planet being very young and/or still accreting. In addition, the $^{12}$CO observations reveal low- velocity large scale filaments aligned with the disk major axis and velocity coherent with the disk gas that we interpret as ongoing gas infall from the local ISM. This system appears to be an interesting case where both a star (from the environment and the disk) and a planet (from the disk) are growing in tandem.

# Introduction

One of the compelling aspects for our understanding of planet formation is the link between the synthesis of planetesimals, the growth of pebbles, and the emergence of gaps (cite: Chiang10; Johansen17), where the latter seems to be a common feature in current observations of protoplanetary disks (cite: Andrews11; Andrews18; Francis20). While planets are not the only explanation for gaps, they seem to be hard to avoid, especially for highly structured disks and particularly wide gaps. Models show that protoplanets can open wide gaps, tens of astronomical units across, with depleted dust and gas inside of them (cite: Zhu11). Gaps are also now being observed in younger, Class I sources, and thus there is reinvigorated debate about *when* the process of planet formation starts (cite: Long17; Sheehan18; SCox20).

In the present paper, we report Atacama Large Millimeter/submillimeter Array (ALMA) continuum and molecular line observations of a unique system, \[BHB2007\] 1, a K7 young stellar object (YSO) with a bolometric luminosity of $\sim1.7$ L$_{\odot}$, effective temperature of 4060 K and a flat spectral energy distribution from near-infrared to mid-infrared bands (spectral class I $\rightarrow$ II) (cite: Brooke07; Forbrich09; Covey10)[^1]. This indicates a source not older than 1 Myr, with most of the surrounding envelope dissipated and thermal emission arising from the circumstellar disk. \[BHB2007\] 1 (BHB1, from now on) is located in Barnard 59 (cite: Dzib18)[^2], the only site of active star-formation in the overall quiescent Pipe nebula. The core harbors a small cluster of YSOs (cite: Brooke07), with BHB1 in a region with low interstellar extinction ($A_V\sim4$ magnitudes), about 5’ ($\sim 0.24$ pc) west of the B59 core (cite: Roman12).

As described in this paper, the system presents a complex morphology, with a clean and wide gap in the dust millimeter continuum, surprising for such a young object. Within the gap, there appears to be gas, and some kind of localized warm emission, seen also with the Karl G. Jansky Very Large Array (VLA). Furthermore, this system does not appear to be “finished” with accretion from the molecular cloud environment, as we see large scale, velocity-coherent filaments in the ALMA $^{12}$CO data. This paper presents the ALMA and VLA observations of this intriguing source, along with models to speculate on the nature of its hidden companion.

# Observations

## ALMA data

BHB1 was observed with ALMA at 226 GHz as part of project code 2013.1.00291.S (PI: Alves). The total continuum-dedicated bandwidth is 2.4 GHz. CASA 4.5 was used for calibration and imaging, where details of the calibration can be found in (cite: Alves17). These observations used 44 antennae with baseline ranging from 15 to 1460 m. In this configuration, the maximum recoverable angular scale is $\sim$ 21$''$. We performed self-calibration of the *uv* visibilities by interpolating over decreasing solution intervals the phase gains (scan and integration time intervals) and amplitude gains (scan intervals). The reprocessed image has an *rms* noise of 0.095 mJy beam$^{-1}$, intensity peak of 19.5 mJy beam$^{-1}$ and flux density of 0.16 $\pm$ 0.02 Jy. The continuum map was produced using Briggs robust parameter 0.5 and has a synthesized beam of $0.24\ensuremath{''} \times 0.20\ensuremath{''}$ and position angle (PA) of 77$^\circ$ (East of North).

$^{12}$CO and C$^{18}$O $J=2\rightarrow1$ were simultaneously observed covering the source and its surroundings. The spectral line data have velocity resolution of 0.35 km s$^{-1}$ ($\sim 270$ kHz) and peaks at channel $-0.95$ km s$^{-1}$ , where intensity reaches 200 mJy beam$^{-1}$. Images were produced using a 0.5 Briggs robust parameter. The final map has an rms noise of 3.5 mJy beam$^{-1}$ and a synthesized beam of $0.25\ensuremath{''} \times0.20\ensuremath{''}$ (PA $\sim 72\ensuremath{^\circ}$). Both continuum and spectral line maps were primary beam corrected, important since the source is offset by $\sim 4.6\ensuremath{''}$ from the phase center.

## VLA data

We have used the VLA in its most extended configuration to observe the 22.2 GHz continuum (K-band, $\lambda = 1.35$ cm). A detailed description of the correlator setup is found in (cite: Alves19), who reports on a distinct source with the same set of VLA observations used for BHB1. The VLA image was obtained using CASA clean and a robust weighting of 1, yielding a synthesized beam of $0.197''\times0.087''$ ($\simeq 21$ au) with a PA of 10.3$^\circ$ and an *rms* noise of 7.5 $\mu$Jy beam$^{-1}$.

![](bhb_data_large_v4.png)

# Results

## Dust substructure in the disk

The disk appears clearly in the millimeter data, with a quasi-symmetric morphology and three distinctive peaks, interpreted as an edge-on view of a gapped disk (Fig. [1](#mainfig)a). The disk has a radius of 107 au and is oriented $\sim 15\ensuremath{^\circ}$ East-of-North. The inner and outer disk are separated by a gap with $\sim70$ au width. The mm dust brightness temperature peaks at $\sim10$ K.

## Disk CO observations

The disk’s molecular gas traced by $^{12}$CO is more extended than the mm emission (Fig. [1](#mainfig)b and d). The spatial distribution of the $^{12}$CO and C$^{18}$O velocity components show a clear Keplerian rotation pattern and a flared morphology. The $^{12}$CO has cloud contamination in the central channels; however, the C$^{18}$O (Fig. [1](#mainfig)c) has less contamination and we find that the source velocity is consistent with previous estimates of 3.6 km s$^{-1}$ (cite: Onishi99). Using the uncontaminated channels and following the prescription of (cite: SSW16), we fit a Keplerian model to the position-velocity diagram of the CO emission and find a mass of 2.23 $\pm$ 0.04 M$_{\odot}$ for the embedded protostar.

## Large-scale filamentary CO emission 

Molecular emission reveals large scale ($\sim4000$ au) and narrow ($\sim80-300$ au) bipolar filaments connecting the ambient gas and the source (Fig. [1](#mainfig)d). These structures are distributed in a north-south orientation, similar to the major axis of the disk. The northern (red-shifted) and southern (blue-shifted) filaments exhibit a velocity shift of $\sim\pm2-3$ km s$^{-1}$ with respect to the source ambient velocity.

No clear velocity gradients are seen along the filaments, whose entire structures are visible over a $\sim1$ km s$^{-1}$ velocity range in each lobe. This low velocity width implies we are likely seeing the filament along the plane of the sky. Interestingly, the pair of filamentary structures have global red and blue shifts. The northern filament is red shifted as the disk is with a similar velocity. The same is true for the southern filament, which is largely blue shifted, consistent with the disk rotation on the southern side of the disk.

If these features are indeed filaments, they appear to be orbiting the system like large propellers or gas streamers accreting into the disk (§[5.1](#subsec:fil)). Alternatively, we could be seeing a limb-brightened large ($>1000$ au) scale outer disk or flattened envelope, where the central channels are too optically thin to observe in emission. Additional observations of higher critical density tracers with deeper observations would be needed to disentangle a filament or remnant flattened envelope. What we can say with certainty is that we see large scale emission associated with the disk based on its velocities that is moving too slowly to be an outflow, and is oriented parallel to the disk plane rather than along a conventional outflow axis.

![](Fig2_pvplot_v2.pdf)

## Localized emission in the south-east gap

The VLA data show a compact radio source at the protostellar position with a flux density of $103\pm12$ $\mu$Jy (we refer to this source as VLA 1). In addition, the data reveal a marginal second peak in the southern gap at a separation of $0.3\ensuremath{''}$ ($\sim49$ au) from the star. This tentative source has a flux density of $30\pm8$ $\mu$Jy (for simplicity we refer to it as VLA 1b). The northern and southern gaps seen in the ALMA continuum map show intensity minima (5.21 and 5.28 mJy beam$^{-1}$) that within uncertainties (0.10 mJy beam$^{-1}$) are the same , i. e., there are no traces of VLA 1b at 1.3 mm. This puts an upper limit for the spectral index of VLA 1b of $\ensuremath{\lesssim} 0.8$ (assuming a 2-$\sigma$ upper limit at 1.3 mm), indicating that VLA 1b traces ionized gas.

Interestingly, VLA 1b coincides with a bright ($\sim 100$ K) and compact $^{12}$CO emission hot spot (Fig. [2](#figplanet)a,b). This spot is probably localized in the southern gap and VLA 1b since (1) it is spatially compact and with a narrow velocity width - both features indicate that it is truly compact in 3 dimensions - and (2) the peak velocity of this feature is close to the highest velocity at the projected radius (see Fig. [2](#figplanet)c,d), i. e. the spot arises at a radius similar to the projected radius on the plane-of-the-sky.

# Analysis

## Radiative transfer analysis

To estimate the size of the gap seen at mm-wavelengths, we explore parametric axisymmetric models using the TORUS radiative transfer code (cite: harriestorus2014). Since the goal of this is to approximately constrain the size of the gap, we have adjusted the model parameters until we achieve a good fit by eye to the mm data and leave more complex modeling to a future analysis.

The functional form of the disk model follows the (cite: lyndenbell1974) formalism for a viscously evolving disk, where $$\begin{equation}
\label{eq:sig}
\Sigma_{g} (R) = \Sigma_{c} \left( \frac{R}{R_c}  \right) ^{-\gamma} \exp{ \left[ -\left( \frac{R}{R_c} \right)^{2-\gamma} \right]}.
\end{equation}$$ For the gas, $\Sigma_{c} = 15$ g cm$^{-2}$, $R_c = 100$ au, and $\gamma = 1$, and we do not include gas gaps. We assume a vertically Gaussian density distribution with a scale-height $h$ of 12 au at 100 au, and a flaring parameter of $\psi=1.2$ where $h=h_{100}\frac{R_{\rm au}}{100}^{\psi}$ and $h$ is in au. For the dust, we assume a global gas to dust ratio of 100, however the local gas/dust ratio in surface densities varies radially. The dust is split into two MRN population distributions with sizes up to 1 micron and 1 mm (cite: cleeves2016), and both adopt pure astrosilicate compositions (cite: draine84). The small dust grains follow the gas and contain 1% of the dust mass. The mm-grains have the same functional form as Eq. [\[eq:sig\]](#eq:sig), but have a power law of $\gamma=0.2$ and an $R_c$ of 1000 au, well beyond the physical disk edge such that the mm dust surface density has a truncated power law behavior. The large grains’ scale- height is 10% of the gas/small dust to approximate settling. The inner disk edge is set to 0.1 au and extends to 20 au. We model an empty gap, and then an outer disk component starting at 93 au extending out to 160 au where it is truncated. We do not vary the depth of the gap as we only have one thermal continuum wavelength, and thus it is challenging to make accurate constraints on both the dust optical properties and the minimum dust mass in the gap, especially given its near edge-on nature. Instead we emphasize that this analysis is aimed to estimate the size of the gap, which we use to estimate possible companion masses for a range of uncertain physical properties (Section [4.2](#hydromod)).

Based on this structure and the stellar parameters described in Sections [1](#sec:intro) and [3.2](#sec:gas), TORUS computes a synthetic image at 1.287 mm, which we convolve with the observed beam. We explored just over 100 models and arrived at a reasonable fit as shown in Figure [3](#fig:dustmod). To arrive at this fit, we varied all parameters except the $\gamma$ value of the gas, $R_c$ for the gas, the inner edge of the inner disk from 0.1 au, the relative dust mass between small and large grains, and the relative scale height of the large grains compared to the small. We find that within our grid of models, the inner edge of the outer ring can reasonably reproduce the structure qualitatively within $\pm5$ au. The gas+dust mass of this disk model is 0.1 M$_\odot$.

Taking this structure, we have additionally run a few non-LTE LIME (cite: Brinch10) models with our TORUS-derived structure to qualitatively investigate how much gas could be missing in the gap but not be clearly seen in the optically thick $^{12}$CO. Given the lower signal to noise of the C$^{18}$O observations, we do not try to compare simulations with these data. We assume a simple uniform CO abundance of $10^{-4}$ relative to H above dust temperatures of 20 K and $10^{-10}$ per H below similar to the approach of (cite: qi2006) to approximate CO freeze-out and photodissociation. We have artificially decreased the gas inside of the gap by varying factors. We find that a gap in the gas distribution is only visible when the gap depth is higher than a factor 100, otherwise it remains hidden due to the high optical depth of the $^{12}$CO emission. We emphasize that the true gap depth would require more detailed fitting, ideally with thermo- chemical models, as the physical properties of gas in the gaps can be different depending on the gas to dust ratio in the gap, the presence or absence of small grains in the gap, the stellar UV heating of gas, and many more parameters (cite: bruderer12; bruderer13; bruderer14; vandermarel15; vandermarel16; vandermarel18; facchini18), which are not constrained here. Instead, these simple models tell us that there is some amount of gas still in the gap and it is not fully cleared. Future deeper observations combined with thermo-chemical simulations should be conducted to better constrain the degree of gas depletion in the gap, if it exists.

![](bhb_dust_mod_V2.png)

## The Mass of the potential planet

Such a wide gap in the dust may indicate the presence of a single or multiple planets. To estimate the mass of the potential planet, we adopt the approach used in DSHARP survey (cite: Zhang2018). First, based on the gap profile, we estimate the relative width of the gap ($\Delta$ parameter in (cite: Zhang2018), which is the gap width over the radius of the outer gap edge) as 0.78. If we adopt DSD1 dust size distribution in DSHARP (dust size follows a power law distribution from 0.005 $\mu$m to 0.1 mm with a power law index of -3.5) and the gas surface density derived above, the Stokes number of the biggest dust particle at $50$ au is 8.6$\times 10^{-4}$ and the derived K’ parameter through the width-mass fitting (defined in Table 1 of (cite: Zhang2018)) is 0.40. Thus, with $(h/r)_{50 au}$=0.1, we can derive that the planet-to-star mass ratio is 0.031 if the disk viscosity coefficient is $\alpha=10^{-3}$ and 0.015 if $\alpha=10^{-4}$. If we adopt DSD2 dust size distribution (dust size follows a power law distribution from 0.005 $\mu$m to 1 cm with a power law index of -2.5), the Stokes number at $50$ au is 0.086 and the derived K’ parameter is 0.05. The planet-to-star mass ratio is 0.0039 if $\alpha=10^{-3}$, and 0.0019 if $\alpha=10^{-4}$.

Taking into account all of these uncertain disk physical parameters, the possible planet-to-star mass ratio spans a wide range of \[0.0019, 0.031\]. Adopting the stellar mass computed in §[3.2](#sec:gas), the mass of the planet ranges between $\sim 4$ and 70 M$_{\mathrm{Jup}}$. We note that the dominant uncertainty in this determination is the maximum particle size and disk viscosity, rather than the details of the fit in Section [4.1](#sec:gapmeasure). While the range is large, all masses point to a super-Jupiter sized companion, which would be consistent with the mass needed to launch jets capable of producing substantial free-free radio emission (cite: Zhu18), see also §[3.4](#subsec:local). .

# Discussion

## Accretion filaments

The large scale filaments are aligned with the disk major axis and coherent with the Keplerian velocity of the protostellar disk seen in CO. In addition, no evidence of acceleration at along the filament makes it unlikely that the observed gas traces outflowing material.

A more plausible explanation is that the filaments are streamers between the bulk of gas in the B59 core in the southeast and BHB1. The lack of a clear velocity gradient along the filaments suggests that the gas motion occurs mostly in the plane-of-sky. Correspondingly, it is hard to assess which direction the gas flows; however, such low velocity gas is typical of infalling streamers observed toward accreting protostars (cite: Mottram13). In this context, the filaments could be molecular gas nurturing the disk and the YSO, which is consistent with single-dish observations of B59 showing dust and molecular patches protruding from the core toward the west, where BHB1 is located (cite: Duarte12).

![](Figinfall+fullmodel.pdf)

Figure [4](#figinfall) displays the line-of-sight (LOS) velocity of CO gas as a function of distance to the protostar. At larger distances, the LOS velocity increases from $\sim 2000$ to 1750 au at the red-shifted lobe, and from $\sim 1650$ to 1500 au at the blue-shifted lobe. The LOS component then either decreases or becomes nearly constant at shorter distances. This velocity shift can be interpreted as material initially falling along the LOS, changing its direction and finally moving toward the source along the plane-of-sky. The region of increasing velocity is seen in Fig. [1](#mainfig)d as bends in the endpoints of the filaments in both lobes. The bend is especially clear in the less filtered red-shifted lobe. Infalling gas parcels departing from rest with no energy dissipation have their LOS velocities determined as $V_{LOS} = \sqrt{2GM_{\star}/d}\times\cos{\alpha}$, where $d$ is the distance to the protostar, $\alpha$ is the angle between the velocity vector and the LOS and $M_{\star}$ is the protostellar mass (Fig. [4](#figinfall), inset). Large-scale accretion streamers have been recently reported by (cite: Pineda20), who presented a scaled-up version of our filaments feeding a protostellar core. This indicates that the filamentary accretion streamers are the natural process in accreting objects regardless their age, as also indicated by time- dependent multi-scale simulations (cite: Kuffmeier17).

## A giant planet hidden in the cavity?

While the feature still must be confirmed, we find three intriguing lines of evidence that point to the possibility of a single “dominant” planetary or potentially brown dwarf companion in the disk. The first is the very broad disk gap apparent in the mm-emission. With a width of over 70 au centered around approximately 50 au, a massive gas giant or low mass brown dwarf would be necessary to clear such a gap. Based on the estimates presented in Section [4.2](#hydromod), its mass must be greater than 4 M$_{\rm Jup}$ up to 70 M$_{\rm Jup}$. How such a massive object forms at this distance remains uncertain. Although there are cases of wide orbit giant exoplanets (cite: Marois10), the relative occurrence is not significant, and they are almost as rare as wide orbit brown Dwarfs (cite: Nielsen19).

In addition to the disk morphology, there are two lines of evidence indicating preferential structure *inside* the southern gap. The first is the presence of a CO “hot spot” at a position coinciding with the gap. Given that young planets are expected to be luminous and thereby heat their surroundings, this may be a sign of such localized heating (cite: wolf2005; Cleeves15). The second line of evidence is the presence of marginal radio emission, VLA 1b, inside the southern gap. No such source is seen in the ALMA data, suggesting that the emission originates from ionized gas (see Section [3.4](#subsec:local)). It is common to see radio emission associated with strong winds and/or jets from protostellar objects (cite: Hull16; Anglada18). There is a known correlation between radio luminosity and a YSO’s bolometric luminosity. If VLA 1b is of the same kind, its radio flux would be consistent with a substellar object (cite: Morata15; Rodriguez17; Ricci17). If confirmed, VLA 1b would be a signpost that there is a substellar object significantly accreting gas from the disk. Alternatively, the radio emission could be produced by the a strong magnetosphere of a fast rotating (sub)stellar object. However, the radio luminosities observed in old brown dwarfs are $1-2$ orders of magnitudes lower than the flux detected here (cite: Berger01; Kao18). Yet, these non-thermal mechanism possibilities can be variable, and so repeat follow up observations would likely be necessary in ascertaining the nature of VLA 1b. Near- infrared observations from scattered light produced by the stellar radiation are also being analysed in order to constrain the nature of the companion (Zurlo et al. in preparation).

# Conclusions

We report the discovery of a disk with a wide gap, even though the disk itself still appears to be fed by extended filaments detected in molecular gas. As a result, this system asks the question, can planets form before the disk itself is fully formed? Furthermore, these data put new time constraints on the giant planet formation process, if indeed they form so early ($<1$ Myr). Our observations present a detailed view of a circumstellar disk, with bright thermal emission from the inner and the outer disk and a large zone of depleted dust between them. Locally, compact and warm gas is detected within the dust gap, coinciding in position with centimeter-wavelength radio emission. Our data are well represented by a model of a protoplanetary disk carved by a giant planet or brown dwarf from which bright non-thermal emission is produced.

# Acknowledgments

The authors thank the anonymous referee for the very insightful report. F.O.A. and P.C. acknowledge financial support from the Max Planck Society. L.I.C. acknowledges support from the David and Lucille Packard Foundation and NASA ATP 80NSSC20K0529. J.M.G. is supported by the grant AYA2017-84390-C2-R (AEI/FEDER, UE). G.A.P.F. acknowledges support from CNPq and FAPEMIG (Brazil). A.Z. acknowledges support from the FONDECYT *Iniciación en investigación* project number 11190837. This paper makes use of the following ALMA and VLA data: DS/JAO.ALMA#2013.1.00291.S, VLA/16B-290. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

ALMA, VLA

natexlab

(ref: Alves19) Alves, F. O., Caselli, P., Girart, J. M., et al. 2019, Science, 366, 90, doi: [`10.1126/science.aaw3491`](http://doi.org/10.1126/science.aaw3491)

(ref: Alves17) Alves, F. O., Girart, J. M., Caselli, P., et al. 2017, A&A, 603, L3, doi: [`10.1051/0004-6361/201731077`](http://doi.org/10.1051/0004-6361/201731077)

(ref: Andrews11) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42, doi: [`10.1088/0004-637X/732/1/42`](http://doi.org/10.1088/0004-637X/732/1/42)

(ref: Andrews18) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Anglada18) Anglada, G., Rodrı́guez, L. F., & Carrasco-González, C. 2018, A&ARv, 26, 3, doi: [`10.1007/s00159-018-0107-z`](http://doi.org/10.1007/s00159-018-0107-z)

(ref: Berger01) Berger, E., Ball, S., Becker, K. M., et al. 2001, Nature, 410, 338. [`https://arxiv.org/abs/astro-ph/0102301`](https://arxiv.org/abs/astro-ph/0102301)

(ref: Brinch10) Brinch, C., & Hogerheijde, M. R. 2010, A&A, 523, A25, doi: [`10.1051/0004-6361/201015333`](http://doi.org/10.1051/0004-6361/201015333)

(ref: Brooke07) Brooke, T. Y., Huard, T. L., Bourke, T. L., et al. 2007, ApJ, 655, 364, doi: [`10.1086/510115`](http://doi.org/10.1086/510115)

(ref: bruderer13) Bruderer, S. 2013, A&A, 559, A46, doi: [`10.1051/0004-6361/201321171`](http://doi.org/10.1051/0004-6361/201321171)

(ref: bruderer14) Bruderer, S., van der Marel, N., van Dishoeck, E. F., & van Kempen, T. A. 2014, A&A, 562, A26, doi: [`10.1051/0004-6361/201322857`](http://doi.org/10.1051/0004-6361/201322857)

(ref: bruderer12) Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A, 541, A91, doi: [`10.1051/0004-6361/201118218`](http://doi.org/10.1051/0004-6361/201118218)

(ref: Chiang10) Chiang, E., & Youdin, A. N. 2010, Annual Review of Earth and Planetary Sciences, 38, 493, doi: [`10.1146/annurev-earth-040809-152513`](http://doi.org/10.1146/annurev-earth-040809-152513)

(ref: Cleeves15) Cleeves, L. I., Bergin, E. A., & Harries, T. J. 2015, ApJ, 807, 2, doi: [`10.1088/0004-637X/807/1/2`](http://doi.org/10.1088/0004-637X/807/1/2)

(ref: cleeves2016) Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2016, ApJ, 832, 110, doi: [`10.3847/0004-637X/832/2/110`](http://doi.org/10.3847/0004-637X/832/2/110)

(ref: Covey10) Covey, K. R., Lada, C. J., Román-Zúñiga, C., et al. 2010, ApJ, 722, 971, doi: [`10.1088/0004-637X/722/2/971`](http://doi.org/10.1088/0004-637X/722/2/971)

(ref: draine84) Draine, B. T., & Lee, H. M. 1984, ApJ, 285, 89, doi: [`10.1086/162480`](http://doi.org/10.1086/162480)

(ref: Duarte12) Duarte-Cabral, A., Chrysostomou, A., Peretto, N., et al. 2012, A&A, 543, A140, doi: [`10.1051/0004-6361/201219240`](http://doi.org/10.1051/0004-6361/201219240)

(ref: Dzib18) Dzib, S. A., Loinard, L., Ortiz-León, G. N., Rodrı́guez, L. F., & Galli, P. A. B. 2018, ApJ, 867, 151, doi: [`10.3847/1538-4357/aae687`](http://doi.org/10.3847/1538-4357/aae687)

(ref: facchini18) Facchini, S., Pinilla, P., van Dishoeck, E. F., & de Juan Ovelar, M. 2018, A&A, 612, A104, doi: [`10.1051/0004-6361/201731390`](http://doi.org/10.1051/0004-6361/201731390)

(ref: Forbrich09) Forbrich, J., Lada, C. J., Muench, A. A., Alves, J., & Lombardi, M. 2009, ApJ, 704, 292, doi: [`10.1088/0004-637X/704/1/292`](http://doi.org/10.1088/0004-637X/704/1/292)

(ref: Francis20) Francis, L., & van der Marel, N. 2020, ApJ, 892, 111, doi: [`10.3847/1538-4357/ab7b63`](http://doi.org/10.3847/1538-4357/ab7b63)

(ref: harriestorus2014) Harries, T. 2014, TORUS: Radiation transport and hydrodynamics code. [`http://ascl.net/1404.006`](http://ascl.net/1404.006)

(ref: Hull16) Hull, C. L. H., Girart, J. M., Kristensen, L. E., et al. 2016, ApJL, 823, L27, doi: [`10.3847/2041-8205/823/2/L27`](http://doi.org/10.3847/2041-8205/823/2/L27)

(ref: Johansen17) Johansen, A., & Lambrechts, M. 2017, Annual Review of Earth and Planetary Sciences, 45, 359, doi: [`10.1146/annurev-earth-063016-020226`](http://doi.org/10.1146/annurev-earth-063016-020226)

(ref: Kao18) Kao, M. M., Hallinan, G., Pineda, J. S., Stevenson, D., & Burgasser, A. 2018, ApJS, 237, 25, doi: [`10.3847/1538-4365/aac2d5`](http://doi.org/10.3847/1538-4365/aac2d5)

(ref: Kuffmeier17) Kuffmeier, M., Haugbølle, T., & Nordlund, Å. 2017, ApJ, 846, 7, doi: [`10.3847/1538-4357/aa7c64`](http://doi.org/10.3847/1538-4357/aa7c64)

(ref: Long17) Long, F., Herczeg, G. J., Pascucci, I., et al. 2017, ApJ, 844, 99, doi: [`10.3847/1538-4357/aa78fc`](http://doi.org/10.3847/1538-4357/aa78fc)

(ref: lyndenbell1974) Lynden-Bell, D., & Pringle, J. E. 1974, MNRAS, 168, 603

(ref: Marois10) Marois, C., Zuckerman, B., Konopacky, Q. M., Macintosh, B., & Barman, T. 2010, Nature, 468, 1080, doi: [`10.1038/nature09684`](http://doi.org/10.1038/nature09684)

(ref: Morata15) Morata, O., Palau, A., González, R. F., et al. 2015, ApJ, 807, 55, doi: [`10.1088/0004-637X/807/1/55`](http://doi.org/10.1088/0004-637X/807/1/55)

(ref: Mottram13) Mottram, J. C., van Dishoeck, E. F., Schmalzl, M., et al. 2013, A&A, 558, A126, doi: [`10.1051/0004-6361/201321828`](http://doi.org/10.1051/0004-6361/201321828)

(ref: Nielsen19) Nielsen, E. L., De Rosa, R. J., Macintosh, B., et al. 2019, AJ, 158, 13, doi: [`10.3847/1538-3881/ab16e9`](http://doi.org/10.3847/1538-3881/ab16e9)

(ref: Onishi99) Onishi, T., Kawamura, A., Abe, R., et al. 1999, PASJ, 51, 871

(ref: Pineda20) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, doi: [`10.1038/s41550-020-1150-z`](http://doi.org/10.1038/s41550-020-1150-z)

(ref: qi2006) Qi, C., Wilner, D. J., Calvet, N., et al. 2006, ApJL, 636, L157, doi: [`10.1086/500241`](http://doi.org/10.1086/500241)

(ref: Ricci17) Ricci, L., Rome, H., Pinilla, P., et al. 2017, ApJ, 846, 19, doi: [`10.3847/1538-4357/aa81bf`](http://doi.org/10.3847/1538-4357/aa81bf)

(ref: Rodriguez17) Rodrı́guez, L. F., Zapata, L. A., & Palau, A. 2017, AJ, 153, 209, doi: [`10.3847/1538-3881/aa6681`](http://doi.org/10.3847/1538-3881/aa6681)

(ref: Roman12) Román-Zúñiga, C. G., Frau, P., Girart, J. M., & Alves, J. F. 2012, ApJ, 747, 149, doi: [`10.1088/0004-637X/747/2/149`](http://doi.org/10.1088/0004-637X/747/2/149)

(ref: SCox20) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228, doi: [`10.1038/s41586-020-2779-6`](http://doi.org/10.1038/s41586-020-2779-6)

(ref: SSW16) Seifried, D., Sánchez-Monge, Á., Walch, S., & Banerjee, R. 2016, MNRAS, 459, 1892, doi: [`10.1093/mnras/stw785`](http://doi.org/10.1093/mnras/stw785)

(ref: Sheehan18) Sheehan, P. D., & Eisner, J. A. 2018, ApJ, 857, 18, doi: [`10.3847/1538-4357/aaae65`](http://doi.org/10.3847/1538-4357/aaae65)

(ref: vandermarel16) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585, A58, doi: [`10.1051/0004-6361/201526988`](http://doi.org/10.1051/0004-6361/201526988)

(ref: vandermarel15) van der Marel, N., van Dishoeck, E. F., Bruderer, S., Pérez, L., & Isella, A. 2015, A&A, 579, A106, doi: [`10.1051/0004-6361/201525658`](http://doi.org/10.1051/0004-6361/201525658)

(ref: vandermarel18) van der Marel, N., Williams, J. P., Ansdell, M., et al. 2018, ApJ, 854, 177, doi: [`10.3847/1538-4357/aaaa6b`](http://doi.org/10.3847/1538-4357/aaaa6b)

(ref: wolf2005) Wolf, S., & D’Angelo, G. 2005, ApJ, 619, 1114, doi: [`10.1086/426662`](http://doi.org/10.1086/426662)

(ref: Zhang2018) Zhang, S., Zhu, Z., Huang, J., et al. 2018, ApJL, 869, L47, doi: [`10.3847/2041-8213/aaf744`](http://doi.org/10.3847/2041-8213/aaf744)

(ref: Zhu18) Zhu, Z., Andrews, S. M., & Isella, A. 2018, MNRAS, 479, 1850, doi: [`10.1093/mnras/sty1503`](http://doi.org/10.1093/mnras/sty1503)

(ref: Zhu11) Zhu, Z., Nelson, R. P., Hartmann, L., Espaillat, C., & Calvet, N. 2011, ApJ, 729, 47, doi: [`10.1088/0004-637X/729/1/47`](http://doi.org/10.1088/0004-637X/729/1/47)

[^1]: The age estimation reported by (cite: Covey10) is based on a pre-*Gaia* distance of 130 pc. In addition, the evolutionary models used by these authors lead to two widely separated ages. The estimated stellar luminosity of this source is likely underestimated in previous works since our data show for the first time a highly inclined disk (§[3.1](#almadust)).

[^2]: The bolometric luminosity reported by (cite: Covey10) and mentioned above is scaled with the distance estimation reported by (cite: Dzib18).

</paper>

Write the methods card for this paper.