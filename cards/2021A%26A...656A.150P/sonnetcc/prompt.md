# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...656A.150P\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...656A.150P",
 "title": "Constraining the properties of the potential embedded planets in the disk around HD 100546",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Pyerin, Max Ackermann",
 "n_authors": 6,
 "arxiv_id": "2110.03373",
 "doi": "10.1051/0004-6361/202141998",
 "alma_projects_linked_by_archive": [
  "2015.1.00806.S",
  "2016.1.00497.S"
 ]
}
```

Paper text:
<paper>
# Constraining the properties of the potential embedded planets in the disk around HD 100546

The protoplanetary disk around the star HD 100546 displays prominent substructures in the form of two concentric rings. Recent observations with the Atacama Large Millimeter/sub-millimeter Array (ALMA) have revealed these features with high angular resolution and have resolved the faint outer ring well. This allows us to study the nature of the system further. Our aim is to constrain some of the properties of potential planets embedded in the disk, assuming that they induce the observed rings and gaps. We present the self-calibrated $0.9\,$mm ALMA observations of the dust continuum emission from the circumstellar disk around HD 100546. These observations reveal substructures in the disk that are consistent with two rings, the outer ring being much fainter than the inner one. We reproduced this appearance closely with a numerical model that assumes two embedded planets. We varied planet and disk parameters in the framework of the planet-disk interaction code [`FARGO3D`](http://fargo.in2p3.fr/) and used the outputs for the gas and dust distribution to generate synthetic observations with the code [`RADMC-3D`](https://www.ita.uni-heidelberg.de/~dullemond/software/radmc-3d/index.php). From this comparison, we find that an inner planet located at $r_1 = 13\,$au with a mass $M_1 = 8 M_{\rm{Jup}}$ and an outer planet located at $r_2 = 143\,$au with a mass $M_2 = 3 M_{\rm{Jup}}$ leads to the best agreement between synthetic and ALMA observations (deviation less than $3\sigma$ for the normalized radial profiles). To match the very low brightness of the outer structure relative to the inner ring, the initial disk gas surface density profile needs to follow an exponentially tapered power law (self-similar solution), rather than a simple power-law profile.

# Introduction

The formation of planets in protoplanetary disks is one of the main subjects of study in modern astrophysics. A very intriguing part of this topic is how newborn planets interact and actively shape the disk they are embedded in. This idea of planet-induced substructures is currently driven by recent observations with advanced telescopes, which have revealed that circumstellar disks can exhibit various prominent substructures, such as rings, gaps, asymmetries, or spirals (e.g., (cite: alma_2015; long2018; Andrews_2018; andrews2020; cieza2021)). Some of these substructures are thought to be indeed created by planet-disk interactions, rendering the observed features indicators of planet formation (e.g., (cite: pi1; pi2; zu3)), and may be used to constrain the properties of an embedded planet candidate, such as the mass and the orbital separation (e.g., (cite: ri)).

The subject of this study is the circumstellar disk surrounding the Herbig star HD 100546. This target is found at a distance of $108.1\pm 0.5\,$pc ((cite: gaia_edr3_2021)), with a right ascension of $11^h\, 33^m\, 25.3^s$ and a declination of $-70^\circ\, 11'\, 41.2''$ ((cite: gaia_edr3_2021)). Observations at multiple different wavelengths detected this disk, which spans $390\pm20\,$au outward from the star in CO emission and $230\pm20\,$au in continuum emission ((cite: w14)). The following substructures were revealed: a ring of emission with a radius of $27\,$au (Hubble Telescope, (cite: a7)), and a second very faint ring at $200\,$au (Atacama Large Millimeter/sub-millimeter Array - ALMA, (cite: w14)).

While several other mechanisms have been proposed to produce ring-like substructures in protoplanetary disks, such as the dead-zone outer edge mechanism ((cite: Pinilla_2016)), particle growth by condensation near ice lines ((cite: Zhang_2016; st17)), and magnetic disk winds ((cite: su193d)), in this work we assume the planet-disk interaction to be the main driver for the observed substructures of HD 100546. In this mechanism, an embedded planet creates a pressure trap outward of its orbit that triggers an accumulation of dust by preventing the material from moving inward. This has been motivated in previous works, where simulations were executed to prove the similarity between structures created by planets and the observed structures of HD 100546 ((cite: w14; montesinos2015; q15; p15; fedele2021)). For example, (cite: p15) estimated that a model with two high-mass planets can qualitatively reproduce the two rings observed in this disk. The inner planet is located at $10\,$au and the outer planet at $70\,$au. Furthermore, planet candidates were previously identified in this system by direct imaging ((cite: q13; q15)), but could not be confirmed because of confusion with disk features (cite: currie2014; currie2015).

In this study, our aim is to further constrain the properties of the potential embedded planets in the HD 100546 circumstellar disk. Particularly, we wish to determine whether one or two planets are required to explain the observed substructures and to obtain their masses and distances from the central star. To do this, we calibrated and analyzed recent ALMA observations of the system to identify the main features and focused on resolving the outer ring that was suggested in (cite: w14; p15). On the numerical side, we carried out hydrodynamic multifluid simulations (gas and dust) with `FARGO3D` ((cite: b16; m0)), and then generated synthetic observations from the outputs using `RADMC3D` ((cite: d12)). In this way, we tested different planet setup scenarios until we reached the best possible agreement between the synthetic and real observations by comparing their respective images and radial profiles.

The layout of this paper is as follows. In Sect. [2](#obs) we present the self-calibrated $0.9\,$mm ALMA observations of HD 100546. In Sect. [3](#sim) we describe the method of our hydrodynamic models and planet setups and also describe how synthetic observations can be obtained from them. In Sect. [4](#psac) we present the synthetic observations that we compare with the ALMA observations. In Sect. [5](#discussions) we discuss what can be inferred about the HD 100546 system from these comparisons. Finally, Sect. [6](#conclusions) summarizes our main findings.

# ALMA Observations

## Calibration

The data sets studied in this work include ALMA observations of HD 100546 at $0.9$ mm wavelength (ALMA Band 7) under ALMA projects 2016.1.00497.S. (PI: A. Pohl) and 2015.1.00806.S (PI: J. Pineda), to which we refer as short-baseline dataset (SB) and long-baseline dataset (LB), respectively. For the SB dataset, the project aimed to measure linear polarization in the emission, and therefore the correlator was configured to observe dust continuum in its four spectral windows centered at $336.495\,$GHz, $338.432\,$GHz, $348.494\,$GHz, and $350.494\,$GHz, each with a bandwidth of $2\,$GHz. The polarization setup of this project was tuned to measure the polarizations (XX, XY, YX, and YY), but we only used the total intensity information. For the LB dataset, the correlator was configured to observe two spectral windows with dust continuum at $331.988\,$GHz and $343.488\,$GHz, and the two remaining windows were aimed at the molecular lines $^{12}$CO ($J:3-2$) and $^{13}$CO ($J:3-2$). The bandwidth of the dust continuum spectral windows in the LB dataset was also $2\,$GHz and $0.469\,$GHz for the remaining windows. The details of all the data are summarized in Table [\[tab:obs_log\]](#tab:obs_log).

After ALMA standard pipeline calibration, we used [`CASA 5.6.2`](https://casa.nrao.edu/index.shtml) to handle and self-calibrate the datasets. In order to extract the dust continuum emission from the spectral windows with molecular line emission, we flagged the channels located at $\pm 25\,$km s$^{-1}$ from each targeted spectral line. Similarly to the calibration of the DSHARP sources (cite: andrews2018), the remaining channels from all spectral windows were averaged into 125 MHz channels.

The self-calibration of the SB data was made in two stages: First, we self-calibrated the shortest baseline observations, taken in April 2017, with solution intervals of $360\,$s, $150\,$s, $60\,$s, and $24\,$s for the phase calibration and $150\,$s for the amplitude calibration. This calibrated dataset was joined with the remaining observations from SB taken on October 2016 and was again self-calibrated by repeating the same solution intervals. The LB data were self-calibrated independently from the SB data, with solution intervals of $360\,$s and $150\,$s for the phase calibration and $360\,$s for the amplitude.

Before combining the datasets, we corrected their phase centers such that the center of all observations was the center of the LB dataset. After self-calibration, we reduced the data volume by averaging the continuum emission into one channel per spectral window and $30$ s of time binning. Finally, we applied the JvM correction to the images generated from the self-calibrated datasets. This correction accounts for the volume ratio $\epsilon_v$ between the point spread function of the images and the restored Gaussian of the `CLEAN` beam, as described in (cite: jorsater1995) and also used in (cite: andrews2021). We find $\epsilon_v=0.69$ for the SB and LB images and $\epsilon_v=0.88$ for the images with SB and LB combined.

## Observational results: Outer ring

The inclusion of the different baselines allowed us to cover and resolve all the relevant scales of the disk. As shown in Fig. [1](#im), we detect the bright compact disk around HD100546 (cite: perez_2020), as well as an extended faint ring that is only detectable when the SB information is included in the image reconstruction. When the disk is deprojected using the geometry from (cite: casassus_2019), with an inclination of $45^\circ$ and a position angle (PA) of $150^\circ$, we find that the outer disk peaks at $\approx1.85''\pm0.1''\,$ from the disk center, which is $200\pm11\,$au at the distance of the source. Alternatively, we also imaged the outer structure after subtracting the contribution to the visibilities from the inner disk emission, in an attempt to reduce the high brightness dynamic range between the rings. This image is shown in panel c of Fig. [1](#im).

To measure the flux from the outer ring, we calculated the flux density from the image generated using only the SB dataset with an elliptical mask with the inclination and position angle of the source, and we integrated the emission between $1.1''-2.5''$, which effectively masked the inner disk emission. We detect the ring to be $4.5\pm0.2\,$mJy, which does not include the $10\%$ ALMA flux uncertainty.

We also estimated the optical depth $\tau$ of the emission to estimate the dust mass content in this region. We assumed that $\tau=-\ln(1 - T_{\text{bright}}/T_{\text{phys}})$, where $T_{\text{bright}}$ is the brightness temperature of a blackbody, and $T_{\text{phys}}$ is the physical temperature of the midplane, which we assumed to be $T_{\text{phys}}=20\,$K constant. The temperature profile of the outer ring peaks at $0.1\,$K, and this very low temperature translates into an equally low estimated optical depth of $\tau_{\text{peak}}=0.005$. This is highly uncertain, however, because the underlying estimate of $T_{\text{phys}}$ has a high level of uncertainty.

The dust mass of the model was estimated by assuming optically thin emission and assuming that the flux ($F_\nu$) received at $0.9\,$mm is being emitted by dust with a constant temperature of $T=20\,$K (cite: ansdell2016; pinilla2018). We followed (cite: h83), $$\begin{equation}
            M_{\text{dust}} = \frac{d^2\,F_\nu}{\kappa_\nu\,B_\nu(T)} \text{,}
        \label{eq:mdust}
        
\end{equation}$$ where $d$ is the distance to the star, $\nu$ is the observed frequency, $B_\nu$ is the Planck function, and $\kappa_\nu=2.3 \times (\nu/230\,\rm{GHz})^{0.4}\,\rm{cm}^{2}\rm{g}^{-1}$ is the frequency-dependent mass absorption coefficient (cite: andrews2013).

By using this $F_\nu = 4.5\,$mJy for the faint outer ring in Eq. [\[eq:mdust\]](#eq:mdust), we obtained a dust mass of $0.7\pm0.07\,M_\oplus$, where we assumed a conservative uncertainty of $10\%$. The error of this estimate is, in addition to the uncertainty of the ALMA flux, mainly caused by the mass absorption coefficient, because this parameter depends on the dust grain size distribution and composition, which are unknown for protoplanetary disks.

![](HD100546_obs_summary_v3.pdf)

![](obs_rp.pdf)

# Numerical simulations

In this section we describe our numerical approach and the underlying assumptions we used to model the HD 100546 system. First, we derive estimates for the locations and masses of the potential embedded planets in Sect. [3.1](#planet_parameters). Second, we describe our hydrodynamic simulations in Sect. [3.2](#fargo_sim), with the two initial conditions we explored and our modifications of the code to manually taper the mass of the planets over time (Sects.  [3.2.1](#init) and [3.2.2](#timing_setup), respectively). Third, we describe how synthetic observations can be obtained from the multifluid FARGO3D simulations in Sect. [3.3](#radmc_synth_obs). Finally, we outline our exploration of the parameter space in Sect. [3.4](#parameterSEARCH).

| Parameter                 | Symbol/Units                         | Value       |
|:--------------------------|:-------------------------------------|:------------|
| Star mass                 | $M_\star[M_{\odot}]$                 | 2.13        |
| Dust settling factor      | $\chi$                               | $3\%$       |
| Inner disk boundary       | $r_{\rm{min}}[\rm{au}]$              | 2.6         |
| Outer disk boundary       | $r_{\rm{max}}[\rm{au}]$              | 500         |
| Radial grid resolution    | $n_r$                                | 540         |
| Azimuthal grid resolution | $n_\phi$                             | 1024        |
| Critical radius           | $R_c\,$\[au\]                        | 80          |
| Intrinsic dust density    | $\rho_{\rm{bulk}}[\rm{g}/\rm{cm}^3]$ | 1.5         |
| Dust grain sizes          | $a_{\rm{dust}}\,[\mu\rm{m}]$         | 0.1, 4.6,   |
|                           |                                      | 220, $10^4$ |
| Dust to gas mass ratio    | $\epsilon$                           | 1%          |
| Gas disk mass             | $M_{\rm{disk}}[M_{\rm{Jup}}]$        | 21          |
| Dust disk mass            | $M_{\rm{dust}}[M_\oplus]$            | 66          |

: List of parameters used in the various simulations.

## Planet parameters

### Planet locations

We deduce the orbit of the planet candidates by analyzing the radial profile of the combined ALMA image. To do this, we need to first understand how a massive planet affects the disk emission.

If a planet is massive enough, it can open a gap in the gas distribution along its orbit. This creates a dust trap at the outer edge of the gap, where inward-drifting dust grains accumulate. This accumulation can then be observed as a ring (e.g., (cite: p15)). This ring is located outward of the planetary orbit. Additionally, the gas surface density decreases toward the position of the planet, and hence it is expected that the planetary orbit should correspond to the local minimum in the radial profile of the observed flux.

From this assumption and the radial profile of our combined ALMA observations (Fig. [2](#rp)), we find two promising locations for embedded planets: (1) The first location is such that it can explain the prominent inner substructure peaking at $27\,$au. Because we were unable to resolve the corresponding local minimum, we reverted to the estimated planet position from previous studies, specifically (cite: p15; w14), suggesting that the inner planet is located at $13\,$au. (2) Our combined ALMA image also reveals a ring with a peak at radius $200\,$au, which suggests that another planet is needed to explain the observed emission. We estimate the orbital separation of the outer planet to be at $143\,$au, corresponding to the local minimum in the observed intensity profile.

It is important to note that the assumption that exactly one planet is responsible for each gap is a simplification. Multiple planets with orbits close to each other could open a shared gap (e.g., as examined in the PDS70 disk, (cite: Bae_2019)). Furthermore, the behavior of opening a gap along the orbit and one ring being located outwards per planet is motivated by simulations of this specific disk. However, under different circumstances, a more complex behavior such as multiple rings induced by one planet and the planet positions coinciding with a dust ring has been found ((cite: Dong_2017; Dong_2018)).

### Planet mass estimates

The planet mass has a strong effect on the width of the induced gap. The precise relation of gap width and planet mass was studied by ((cite: Dodson_Robinson_2011; Pinilla_2012; rosotti2016; Fung_2016; 2018facchini)), yielding the dependence

$$\begin{equation}
            M_K = 3M_\star \left( \frac{D}{Kr} \right)^3\text{,} \label{mass_K_range_formula}
        
\end{equation}$$

where $M_K$ is the planet mass estimate, which depends on the dimensionless parameter $K$, the stellar mass $M_\star$, the orbit of the planet $r$, and the gap width in the millimeter dust continuum $D$ (defined following (cite: l19) as the minimum to peak radial distance), obtained from observations. $K$ describes how many Hill radii $R_{\rm{Hill}}=r\sqrt[3]{M/3M_\star}$ of the planet correspond to the continuum gap width. *K* has been found to lie within the interval $7\leq K \leq 10$. This allows us to find mass estimates directly from the radial profile of the dust continuum emission (Fig. [2](#rp)). We inferred the continuum gap width as the radial distance of the local flux peak of the substructure to the corresponding estimate of the planet position. This yields $D_1=14$ au for the inner and $D_2=79$ au for the outer gap, which corresponds to the mass estimates $8\,M_{\rm{Jup}}\leq M_{K,1} \leq 24\,M_{\rm{Jup}}$ for the inner and $1.1\,M_{\rm{Jup}} \leq M_{K,2} \leq 3.3\,M_{\rm{Jup}}$ for the outer planet.

We also took the minimum planet mass $M_{\rm{min}}$ into account that is required to open a gap at all, following the studies of (cite: c6) and (cite: l19). First, there is the model of (cite: c6). This model is a balance between the pressure and viscosity torque from the disk with the gravitational torque from the planet. The authors estimated the minimum mass to be

$$\begin{equation}
            M^{\rm{\,Crida}}_{\rm{min}} = \left\{ qM_\star \left| \frac{3 \sqrt[3]{3} H }{4 r} q^{-1/3} + \frac{50 \alpha c_s H}{\sqrt{\frac{G M_\star}{r^3}} r^2} q^{-1} = 1 \right.\right\}\text{,}
            \label{CridaFormula}
        
\end{equation}$$

where $c_s=\sqrt{\frac{k_B T}{\mu m_H}}$ is the isothermal sound speed, $H = \frac{c_s}{\Omega_K}$ is the disk pressure scale height, $q$ is the planet mass in units of the stellar mass, and $\alpha$ is the disk viscosity from the $\alpha$-disk model ((cite: s73)). Then there is the model of (cite: l19), which is based on hydrodynamical simulations that include dust dynamics. It finds a minimum mass of

$$\begin{equation}
            M^{\rm{\,Lodato}}_{{\,min}} = 
                \begin{cases}
                    \, 0.3 M_\star \left(\frac{H}{r}\right)^3 & \text{for} \, \text{St} < 1 \\
                    \, 3 M_\star \left( \frac{H}{5.5 r \sqrt{\text{St}}} \right)^3 & \text{for} \, \text{St} \geq 1\text{,}
                \end{cases}
                \label{LodatoFormula}
        
\end{equation}$$

where St corresponds to the the Stokes number, defined by

$$\begin{equation}
            \text{St} = \frac{\pi \, a_{\rm{dust}} \, \rho_{\rm{bulk}} }{2\, \Sigma_{g}}\text{,}
        
\end{equation}$$

with $a_{\rm{dust}}$ being the dust grain size, $\rho_{\rm{bulk}}$ the intrinsic dust density, and $\Sigma_{g}$ the gas surface density.

From these two criteria, we estimated the minimum planet mass by choosing the maximum of the two models,

$$\begin{equation}
            M_{\rm{min}} = \rm{max}\left(M^{\rm{Crida}}_{\rm{min}}, M^{\rm {Lodato}}_{{\,min}}\right).
        
\end{equation}$$

For $\alpha=10^{-4}$, we obtain $M_{\rm{min},1}=0.3\,M_{\rm{Jup}}$ for the inner and $M_{\rm{min},2}=1.7\,M_{\rm{Jup}}$ for the outer planet. For $\alpha=10^{-3}$, the minimum mass estimates are $M_{\rm{min},1}=0.7\,M_{\rm{Jup}}$ for the inner and $M_{\rm{min},2}=3\,M_{\rm{Jup}}$ for the outer planet.

We took the lowest possible mass for each of the planets for our simulations because planets have not directly been observed in this disk, and thus a lower-mass companion is more likely to exist. Therefore we determine the planet masses $M$ for the `FARGO3D` setups as

$$\begin{equation}
            M = \rm{max}\left(\rm{min}_K\left(M_K\right), M_{{\,min}}\right)\text{,}
            \label{mass_master_model_eq}
        
\end{equation}$$

which returns an estimate of $M_1=8\,M_{\rm{Jup}}$ for the inner planet mass. For the outer companion, we obtain different estimates depending on $\alpha$: $\alpha=10^{-4}$ leads to $M_2=1.7\,M_{\rm{Jup}}$, and $\alpha=10^{-3}$ implies $M_2=3\,M_{\rm{Jup}}$.

## Hydrodynamic simulations with `FARGO3D`

We modeled this disk with the numerical hydrodynamics solver [`FARGO3D`](http://fargo.in2p3.fr/) ((cite: b16; m0; 2019fargomulti; 2019diffusionfargo)), which is designed to simulate planet-disk interactions. This code evolves a numerical fluid over time that is described with a grid of densities, velocities, and energies.

We used a multifluid approach and model the gaseous dusty disk around HD 100546 as five fluids: one fluid represents the gas, and the four remaining fluids describe the dust, where each of them corresponds to a specific grain size $a_{\rm{dust}} \in \left\{0.1\,\mu\rm{m}, 4.6\,\mu\rm{m}, 0.22\,\rm{mm},\text{ and } 1\,\rm{cm} \right\}$.

The `FARGO3D` simulations were performed in two dimensions on a polar grid $(r,\varphi)$, extending azimuthally from $0$ to $2\pi$ and radially from $r_{\rm{min}}$ to $r_{\rm{max}}$. The radial extent was determined in order to enclose the orbits of all planet candidates as well as the induced substructures without any potential boundary effects. They were calculated based on the planet Hill radius $R_H$ as $r_{\rm{min}}=(r_1-3 R_{H,1})/3 =2.6\,$au and $r_{\rm{max}}=3(r_2+3 R_{H,2})=500\,$au. For the radial simulation boundaries, we used a power-law extrapolation as the boundary condition for the densities and standard Keplerian speed/antisymmetric boundaries for the velocities in the $r$/$\varphi$ direction (`KEPLERIAN2DDENS` and `KEPLERIAN2DVAZIM`/`ANTISYMMETRIC` in the `FARGO3D` setup, respectively). The grid resolution was chosen such that one grid cell corresponded to one-tenth of the pressure scale height H at the two planet locations $r_1 = 13\,$au and $r_2 = 143\,$au, which equates to an azimuthal resolution of $n_\phi = 1024$ cells and a radial resolution of $n_r = 540$ cells.

To determine the duration of the simulations, we need to consider the age of the HD 100546 system, which has been estimated to be $4.8\,\rm{Myr}$ ((cite: Wichittanakom_2020)). However, a simulation of such a duration is computationally unfeasible because we need to choose a high grid resolution to resolve the disk at the locations of the two planet candidates. We instead ran our simulations for $0.74\,$Myr (corresponding to $2.3\times 10^4$ orbits of the inner planet or $6.3\times 10^2$ orbits of the outer planet), assuming that, qualitatively, the disk reaches a quasi-steady state within this time. We discuss this assumption in Appendix [8](#conv_behav).

### Initial conditions

To model the initial distribution of the gas surface density $\Sigma_{g}$ of the disk for the `FARGO3D` simulations, we used two approaches. The first approach was a simple power-law profile,

$$\begin{equation}
                \Sigma_g (r,\varphi) = \Sigma_0 \left(\frac{r}{r_1}\right)^{-1}\text{,}
                \label{pow_eq}
            
\end{equation}$$

where $r_1=13$ au is the orbit of the innermost planet, which was used as a length scale by `FARGO3D`, and $M_{\rm{disk}}$ is the total gas disk mass enclosed between $r_{\rm{min}}$ and $r_{\rm{max}}$. The normalization constant $\Sigma_0$ is obtained such that $M_{\rm{disk}} = \int_{r_{\rm{min}}}^{r_{\rm{max}}} \; 2 \pi r \Sigma_{g}(r) \; dr$, where we assumed the total gas disk mass to be $M_{\rm{disk}} = M_{\rm{dust}}/\epsilon$. Here, $\epsilon = 10^{-2}$ corresponds to the dust-to-gas mass ratio, taken to be equal to the interstellar value, and $M_{\rm{dust}}=66\,M_\oplus$ is the total dust disk mass obtained from the total observed flux of our combined ALMA dust continuum emission of $435$ mJy (see Eq. [\[eq:mdust\]](#eq:mdust)).

The other initial condition used in this work is the self-similar solution from (cite: lynden-bell_pringle_1974),

$$\begin{equation}
                \Sigma_g (r,\varphi) = \Sigma_0 \left(\frac{r}{R_c}\right)^{-1} \exp\left(-\frac{r}{R_c}\right)\text{.}
                \label{exp_eq}
            
\end{equation}$$

This profile is a power law combined with an exponential decay to reduce the amount of material in the outer disk. Here, $R_c = 80\,$au is the critical radius, and $\Sigma_0$ is chosen analogously to the above.

The initial dust surface densities were set following $\Sigma_{d}(a_{\rm{dust}}) = f(a_{\rm{dust}}) \epsilon \Sigma_{g}$, such that the dust-to-gas ratio radial profile was radially constant and equal to $\epsilon$. The factor $f(a_{\rm{dust}})$ determines the mass distribution across the different dust sizes, and it was set such that the number density of the dust behaves as $n(a_{\rm{dust}}) \,da_{\rm{dust}} \propto a_{\rm{dust}}^{-3.5}\, da_{\rm{dust}}$, following an MRN distribution ((cite: mathis_1977)).

### Mass-tapering model

To mimic the fact that planets grow over time and avoid any numerical artifacts right at the beginning of the simulations by introducing the whole planet mass, we used the following mass-tapering approach. This formula is a variation of the mass-tapering algorithm that is included in `FARGO3D`. We changed the code because we needed to be able to set a different taper for each planet individually in order to study the effect of planet formation timescales. We also added a new offset parameter. Our model reads

$$\begin{equation}
                \frac{m_i(t)}{M_i} = 
                    \begin{cases}
                        \,0 & \text{for } t<\Delta_i\\
                        \,\frac{1}{2} \left(   1 - \cos \left(  \pi\, \frac{t-\Delta_i}{\tau_i} \right)  \right) & \text{for } \Delta_i\leq t<\Delta_i+\tau_i \\
                        \,1 & \text{for } t \leq \Delta_i+\tau_i \text{,}
                    \end{cases}
            \label{masstaper}
            
\end{equation}$$

where $m_i(t)$ is the effective mass of the planet $i$ at a given time $t,$ and $M_i$ is the final planetary mass. This model has two parameters, which we refer to as the "timing parameters": (1) $\Delta_i$, the time at which the planet is introduced into the simulation; and (2) $\tau_i$, the formation timescale after the planet is introduced. We fiducially set the delays $\Delta_1$ and $\Delta_2$ to zero and the tapers $\tau_1$ and $\tau_2$ to $16\,$Kyr. We chose $16\,$Kyr, corresponding to $1000$ orbits of the inner planet, as an arbitrary timescale that is small compared to the simulated duration, but still long enough to prevent numerical artifacts by introducing the full planet mass from the beginning of the simulation.

We note that while our approach does increase the planet mass over time, the actual physical accretion process is ignored in this present work, that is, there is no mass transfer from the dust or gas fluids onto the planet. We also fixed the planets orbit and neglected its potential migration.

## Synthetic observations with `RADMC-3D`

To directly compare the density distributions from `FARGO3D` with our self-calibrated ALMA image, we performed a radiative transfer simulation and rendered a synthetic observation, using the code [`RADMC-3D`](https://www.ita.uni-heidelberg.de/~dullemond/software/radmc-3d/index.php) ((cite: d12)). This requires expanding the two-dimensional dust surface density distributions into three dimensions, which we did by using a Gaussian distribution along the vertical ($z$) axis, assuming hydrostatic equilibrium in this direction,

$$\begin{equation}
            \rho_{d}(r,\varphi,z) = \Sigma_{d} (r,\varphi) \frac{1}{\sqrt{2\pi}H_{\rm{dust}}(r)}\exp\left(-\frac{z^2}{2 H_{\rm{dust}}(r)^2}\right) \text{,}
        
\end{equation}$$

with the disk height model of (cite: d4),

$$\begin{equation}
            H_{\rm{dust}}(r) =
            \begin{cases}
                \,\chi\,H(r) & \text{for } a_{\rm{dust}} > 1\,\rm{\mu m} \\
                \,H(r) & \text{otherwise} \text{,}
            \end{cases}
            \label{diskheightmodel}
        
\end{equation}$$

where $H = \frac{c_s}{\Omega_K}$ is the disks pressure scale height, and $\chi=3\%$ is the scale height reduction factor encoding the effect of dust settling, which is more prominent for the larger grain sizes. It therefore results in a shorter dust scale height compared to the one for smaller grain sizes that roughly follow the gas.

We assumed the disk to be composed of silicates ((cite: d95)) and used corresponding optical constants from the [Jena database](http://www.astro.uni-jena.de/Laboratory/Database/databases.html). To match our combined ALMA observations, the wavelength was fixed at $\lambda=0.9\,$mm, and all synthetic observations are convolved with a $0.3''$ Gaussian beam similar to the actual observations.

## Parameter space exploration

| Model setup | I | II | III | IV | V | VI | VII |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Initial Density Model | pow (Eq. [\[pow_eq\]](#pow_eq)) | exp (Eq. [\[exp_eq\]](#exp_eq)) | pow (Eq. [\[pow_eq\]](#pow_eq)) | exp (Eq. [\[exp_eq\]](#exp_eq)) | exp (Eq. [\[exp_eq\]](#exp_eq)) | exp (Eq. [\[exp_eq\]](#exp_eq)) | exp (Eq. [\[exp_eq\]](#exp_eq)) |
| Disk Viscosity $\alpha$ | $10^{-4}$ | $10^{-4}$ | $10^{-4}$ | $10^{-4}$ | $10^{-4}$ | $10^{-4}$ | $10^{-3}$ |
| Inner Planet? |  |  |  |  |  |  |  |
| Planet mass $M_1$ \[$M_{\rm{Jup}}$\] | $8$ | $8$ | $8$ | $8$ | $8$ | $8$ | $8$ |
| Delay Time $\Delta_1$ \[Kyr\] | $0$ | $0$ | $0$ | $0$ | $0$ | $0$ | $0$ |
| Mass Taper $\tau_1$ \[Kyr\] | $16$ | $16$ | $16$ | $16$ | $16$ | $16$ | $16$ |
| Outer Planet? |  |  |  |  |  |  |  |
| Planet mass $M_2$ \[$M_{\rm{Jup}}$\] | \- | \- | $1.7$ | $1.7$ | $1.7$ | $1.7$ | $3$ |
| Delay Time $\Delta_2$ \[Kyr\] | \- | \- | $0$ | $0$ | $600$ | $0$ | $0$ |
| Mass Taper $\tau_2$ \[Kyr\] | \- | \- | $16$ | $16$ | $16$ | $600\,$ | $16\,$ |

In order to find a model that reproduces the ALMA observations, we ran multiple simulations with different parameters (see Table [\[model_setup_table\]](#model_setup_table)). We started by testing how models with a single planet compare to the observation, and ran a simulation for both the initial gas surface density profiles we introduced in Sect. [3.2.1](#init) (model I with the power law, and model II with the self-similar solution). Then, we executed simulations with two planets for both initial conditions (model III with the power law, and model IV with the self-similar solution). In all of these four simulations, we introduced the planet(s) right from the beginning of the run and used the fiducial taper of $\tau=16\,$Kyr as well as a fiducial viscosity of $\alpha=10^{-4}$.

Then, we explored the effect of different planet formation timescales. Because the ALMA observation reveals that the inner ring is much brighter than the outer ring, the inner pressure trap must exist very early in order to trap as much material as possible. For this reason, we always introduced the inner planet immediately at the beginning of the simulations, that is, we always set the offset $\Delta_1 = 0$ and chose a fiducial mass taper of $\tau_1=16\,$Kyr, and we only varied the timing parameters for the second planet. In model V we set $\Delta_2 = 6\times 10^5\,$yr while keeping $\tau_2 =16\,$Kyr, while in model VI, we kept $\Delta_2 = 0$ and set $\tau_2 = 6\times 10^5\,$yr. This means that in models V and VI, the outer planet reaches its final mass on a timescale comparable to the duration of the entire simulation ($7.4\times 10^5\,$yr). In these simulations, the viscosity remained the same as for the previous ones for comparability ($\alpha=10^{-4}$), and the initial profile is the self-similar solution in both of them because we show below that such a profile is required to reach the best agreement between synthetic and real observations.

Finally, we simulated a disk with a different viscosity $\alpha$. We chose a higher viscosity of $\alpha=10^{-3}$ in model VII. This simulation used the fiducial timing setup, that is, it introduced both planets from the start of the simulation with the fiducial taper ($\Delta_1=\Delta_2=0$, $\tau_1=\tau_2=16\,$Kyr) and used the the self-similar solution initial profile. It therefore directly compares to model IV. In this model, the mass estimate for the outer planet increases to $3\,M_{\rm{Jup}}$.

The parameters that are common in all simulations are listed in table [1](#parametertable). An overview of the exact values of the parameters that differed between the seven different simulations is given in table [\[model_setup_table\]](#model_setup_table).

# Results

The main results we obtained for the different planet setups and disk parameters are shown in Figs. [3](#im_1p)-[6](#im_a3). For each setup, we present the corresponding synthetic observation and the combined ALMA image, both normalized to their respective maximum, and using the same color map. In addition, we display the azimuthally averaged normalized radial profiles as a metric to compare the two images quantitatively.

![](1p.pdf)

Figure [3](#im_1p) shows models I and II, which solely include the inner planet, with different initial density profiles (Eqs. [\[pow_eq\]](#pow_eq) and [\[exp_eq\]](#exp_eq), respectively). Both of these models induce a ring in the synthetic observation that matches the inner ring of the real observation in the image and the radial profile. However, these models do not create an outer ring because there is no second planet that might induce an outer trap. Comparison of the radial profiles reveals how strongly the synthetic observations deviate from the observation. Model I reaches its largest deviation at $110\,$au with $133\sigma$, while it is $4\sigma$ at $200\,$au for model II.

![](stf.pdf)

In Fig. [4](#im_stf) we show simulations including two planets (models III and IV) with different initial density models. In contrast to the one-planet models (I and II), both of these models create two rings. The location of these rings matches the ALMA observation, and the radial profiles show a similar shape. We therefore continued our parameter search with two planets.

In model III the outer structures are relatively bright compared to the inner ring, which is strongly overestimated: in the model, the relative peak intensity of the outer ring is $86$ times higher than in the ALMA observation. This issue does not arise with model IV, which reproduces the relative peak intensity of the two substructures properly. Model IV is within a $3\sigma$ range around the observation in the normalized radial profile. We therefore continued our parameter search using two planets and the self-similar solution as initial condition.

However, model IV presents an issue regarding the symmetry of the outer features: the ring is mainly concentrated in one point and is much fainter and thinner along the remaining structure in the azimuthal direction. This differs from the observed outer ring, which is evenly bright and symmetric. To resolve this issue, we conducted further tests to quantify the potential effect of different model parameters, specifically, the timing parameters and the disk viscosity $\alpha$.

![](time.pdf)

Figure [5](#im_time) shows the results with different planet-mass tapering. The models are identical to model IV, except for one of the parameters of the mass-tapering model. In model V, the outer planet is introduced $\Delta_2 = 6\times10^5\,$yr after the inner one. This reduces the relative strength of the outer substructure by $\sim 80\%$ compared to model IV. In model VI, the outer planet mass is tapered over $\tau_2 = 6\times10^5\,$yr. This reduces the outer rings flux by $\sim 40\%$ relative to the base model IV. Both of these models are within $3\sigma$ around the ALMA detection. However, the outer ring is not more symmetrical in either one of them.

![](a3.pdf)

Finally, we present the result for a higher disk viscosity of $\alpha=10^{-3}$ in Fig. [6](#im_a3) (model VII). Motivated by the previous results, model VII used the self-similar solution initial profile and the fiducial mass tapering setup ($\Delta_{1,2}=0,\,\tau_{1,2}=16$ Kyr). This model produces an azimuthally symmetric ring. This can be explained as follows: While vortices can live long at the edge of a gap opened by a massive planet due to the Rossby wave instability in a disk with a low viscosity of $\alpha=10^{-4}$, they dissipate earlier with the higher viscosity $\alpha=10^{-3}$ ((cite: Lin_2011)). However, the minimum planetary mass needs to be increased in order to open a comparable gap in this higher-viscosity scenario. We find the mass estimate for the outer planet to be $3 M_{\rm{Jup}}$ (see Eq. [\[mass_master_model_eq\]](#mass_master_model_eq)). The mass of the inner planet remains unchanged ($8 M_{\rm{Jup}}$).

The outer substructure in the synthetic observation of model VII agrees well with the ALMA observation because it does not display the asymmetry seen in previous models. Its normalized radial profile resides within a frame of $3\sigma$ around the detection. Consequently, model VII leads to the best agreement between our synthetic observation and the real one.

To mimic how ALMA would see the disk that model VII generates, we took corresponding synthetic observation given by `RADMC-3D` and used the package `galario` to calculate the visibilities with the same uv-coverage as the observations. Fig. [6](#im_a3)b shows the synthetic image obtained through radiative transfer and convolved with a Gaussian beam in the image space, as we did for all the other synthetic observation, and Fig. [6](#im_a3)c shows the simulated observation using the visibilities, imaged with the same conditions as the observations. Both images are consistent with each another and reproduce the observed radial profile, proving the observability of the structures generated in our simulations.

# Discussion

From the results above, it is clear that two planets are needed to explain the newly resolved outer ring in addition to the inner feature. None of the one-planet models of the disk (I and II) reproduce any strong visible substructures that would resemble the appearance of the outer ring, while the two-planet models feature two rings (e.g., VII). This conclusion is confirmed quantitatively by analyzing the errors of the normalized radial profiles: the models with a single planet have an above-significant deviation ($>3\sigma$) from the observation, while the models with two planets IV-VII have a deviation of less than $3\sigma$ in the radial profile. This finding is consistent with the results of (cite: p15; fedele2021), who both concluded that the outer substructure is likely an indicator of a second companion.

Additionally, we find that the initial density profile needs to have a stronger radial fall-off than the commonly assumed power law (Eq. [\[pow_eq\]](#pow_eq)) in order to model the flux ratio of the inner and outer ring correctly. We have achieved this by using the self-similar solution from (cite: lynden-bell_pringle_1974) as initial condition.

Our study also shows that changing the formation timing of the outer planet does affect the resulting radial profile and synthetic image (models IV, V, and VI), but all three models still reside within a $3\sigma$ range around the observation in the normalized radial profile. This means that the outer planets mass of $1.7 M_{\rm{Jup}}$ in model V, where the planet started to form very recently ($140\,$Kyr before the end of the simulation), is sufficient to successfully induce the outer substructure. This is much lower than previously estimated: (cite: p15) estimated that if the outer planet is much younger than the inner planet (1 Myr younger), it should be more massive ($\gtrsim15\,M_{\rm{Jup}}$). This difference probably arises from the two different methods. (cite: p15) assumed an analytical solution to introduce the gaps in the gas surface density profile and ran dust evolution models considering that the gas density remains constant over time. In our current approach, however, we modeled gas and dust evolution simultaneously, but we neglected dust growth.

Our study favors a (cite: s73) disk viscosity of $\alpha\gtrsim10^{-3}$ because we searched for an $\alpha$ that avoids asymmetric accumulations in the outer ring, which is successfully achieved in model VII (Fig. [6](#im_a3)). Models of a disk with a lower viscosity ($\alpha=10^{-4}$) induce an asymmetric outer feature with a strong density accumulation that is absent in the ALMA image, and they also feature an accumulation of material around the position of the outer planet (see Fig. [4](#im_stf)c). However, from the study of (cite: b20), we suspect that this accumulation is an artifact of not simulating the accretion of the surrounding material onto the planet. This poses the question whether the shape of the outer ring itself would be as strongly affected by including accretion in the simulation as the gap. If this were the case, a simulation with a low viscosity $\alpha=10^{-4}$ might be able to produce a symmetrical feature with the outer planet mass estimate as low as $1.7\,M_{\rm{Jup}}$. Further simulations including the planet accretion process are thus needed to address this question. This lies beyond the scope of this paper, however.

In a recent study, (cite: fedele2021) examined the HD 100546 disk planet setup with smooth particle hydrodynamics (SPH) simulations. They qualitatively reproduced the disk appearance with an inner planet of final mass of $3.1\,M_{\rm{Jup}}$ at $15\,$au and an outer planet that reached $8.5\,M_{\rm{Jup}}$ at $110\,$au. While the number of planets and the positions are consistent with what we derived from the radial profile in Sect. [3.1.1](#planet_setups) (inner planet: $13\,$au; outer planet: $143\,$au), the mass estimates differ from our results (inner planet: $8\,M_{\rm{Jup}}$; outer planet: $3\,M_{\rm{Jup}}$ for $\alpha=10^{-3}$, or $1.7\,M_{\rm{Jup}}$ for $\alpha=10^{-4}$). The origin of these differences is unclear. One possible explanation is that for the outer planet mass, (cite: fedele2021) reported an estimate based on the the gap width with the same model as we used (Eq. [\[mass_K_range_formula\]](#mass_K_range_formula)), but fixed the proportionality constant to an average value while we chose the minimum possible mass; and they have a higher estimate of $100\,$au for the dust gap width than we do ($79\,$au). As a consequence, their estimated planet mass ($5.5\,M_{\rm{Jup}}$) is a higher than our estimate ($3\,M_{\rm{Jup}}$).

The results we deduced from submillimeter ALMA observations compare well to findings from observations at other wavelengths. (cite: Brittain_2014) hypothesized the presence of a planet in the HD 100546 system with an orbit of  15 AU from molecular emission line observations. This companion appears consistent with the inner planet of our best model (13 AU). Furthermore, (cite: Follette_2017) analyzed scattered-light observations of HD 100546, revealing multiple spiral arms. They proposed that a planet of a few Jupiter masses at  100 AU could explain these observed spiral structures. This planet roughly matches the outer planet from our model (at 143 AU).

# Conclusions

We aimed to constrain some of the properties of potential planets embedded in the HD100546 circumstellar disk from the observed substructures. In particular, we were interested in constraining their masses and orbits. To do this, we analyzed recent ALMA observations of the system, and then matched them as closely as possible with our numerical model, iteratively improving the fit by systematically varying disk and planet parameters. In our numerical model, we first simulated the gas and dust in a protoplanetary disk with the multifluid code `FARGO3D`, and then rendered a synthetic observation from the results with `RADMC-3D`.

Thereby, we showed that the recent ALMA observations of HD 100546 can be reproduced by a protoplanetary disk model hosting two companions orbiting at separations of $13\,$au and $143\,$au. The best agreement between synthetic and real observations is reached with model VII, which uses the self-similar solution as initial condition and value of $\alpha = 10^{-3}$. This model matches the observation within $3\sigma$ of certainty in the normalized radial profile, and the resulting outer ring does not show azimuthal asymmetries. From the observed intensity profile, we estimate a mass of $8\,M_{\rm{Jup}}$ for the inner planet. This agrees with the results of other studies ((cite: p15): $\sim 10\,M_{\rm{Jup}}$), but it is higher than suggested by (cite: fedele2021) ($3.1\,M_{\rm{Jup}}$).

In contrast to previous results, we conclude that the outer planets mass can be as low as $3\,M_{\rm{Jup}}$ for a disk viscosity of about $\alpha=10^{-3}$, and $1.7\,M_{\rm{Jup}}$ for a lower viscosity ($\alpha=10^{-4}$). Our results show that this companion can successfully reproduce the outer substructure, both in a model were it formed early in the disks lifetime and in a model where it formed very recently (as young as $140$ Kyr), equally well. This estimate for the outer planet mass is low in comparison to the previous studies of (cite: p15) ($\gtrsim15\,M_{\rm{Jup}}$ for a young planet, and $\lesssim 5\,M_{\rm{Jup}}$ for an older planet) and (cite: fedele2021) ($8.5\,M_{\rm{Jup}}$). We further find that to properly reproduce the brightness ratio of the inner and outer ring, the disks initial gas surface density profile needs to be modeled as a self-similar solution profile.

Finally, the planet mass estimates need to be evaluated in terms of whether companions this massive might be directly visually detected by current instrumentation capabilities. (cite: p20) have deduced a lower limit for this in ALMA observation, depending on the star age. They found that the planets of this system would have to be more massive than $33\,M_{\rm{Jup}}$ for an age of $4\,$Myr to be detected by ALMA. This means that the detection of the proposed planets with $8\,M_{\rm{Jup}}$ and $3\,M_{\rm{Jup}}$ is still beyond our current ALMA capabilities. In addition, they are very difficult to directly image with instruments like SPHERE at the VLT ((cite: boccaletti2020sphere)). Future high-resolution observations are therefore needed to prove or rule out the existence of embedded planets in the HD 100546 protoplanetary disk.

# Acknowledgements

We would like to thank Camille Bergez-Casalou, Cornelis Dullemond and Marcelo Barraza for helpful discussions and technical insights. The Computational resources of the Max Planck Computing and Data Facility made this project possible and are gratefully acknowledged. We are also thankful for the support provided by the Alexander von Humboldt Foundation in the framework of the Sofja Kovalevskaja Award endowed by the Federal Ministry of Education and Research. We further acknowledge the efforts of Adriana Pohl, Akimasa Kataoka, and Cornelis Dullemond to motivate and propose the observation of the HD 100546 system with ALMA. We thank Ruobing Dong for revising this manuscript and providing constructive feedback and suggestions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00497.S., and ADS/JAO.ALMA#2015.1.00806.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

59 natexlab

(ref: alma_2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, The Astrophysical Journal, 808, L3

(ref: andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483

(ref: andrews2021) Andrews, S. M., Elder, W., Zhang, S., et al. 2021, ApJ, 916, 51

(ref: andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: Andrews_2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, The Astrophysical Journal, 869, L41

(ref: andrews2013) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129

(ref: ansdell2016) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46

(ref: a7) Ardila, D. R., Golimowski, D. A., Krist, J. E., et al. 2007, The Astrophysical Journal, 665, 512

(ref: Bae_2019) Bae, J., Zhu, Z., Baruteau, C., et al. 2019, The Astrophysical Journal, 884, L41

(ref: 2019fargomulti) Benı́tez-Llambay, P., Krapp, L., & Pessah, M. E. 2019, ApJS, 241, 25

(ref: b16) Benitez-Llambay, P. & Masset, F. S. 2016, The Astrophysical Journal Supplement Series, 223, 11

(ref: b20) Bergez-Casalou, C., Bitsch, B., Pierens, A., Crida, A., & Raymond, S. N. 2020, Astronomy & Astrophysics, 643, A133

(ref: boccaletti2020sphere) Boccaletti, A., Chauvin, G., Mouillet, D., et al. 2020, SPHERE+: Imaging young Jupiters down to the snowline

(ref: Brittain_2014) Brittain, S. D., Carr, J. S., Najita, J. R., Quanz, S. P., & Meyer, M. R. 2014, The Astrophysical Journal, 791, 136

(ref: gaia_edr3_2021) Brown, A. G. A., Vallenari, A., Prusti, T., et al. 2021, Astronomy & Astrophysics, 650, C3

(ref: casassus_2019) Casassus, S. & Pérez, S. 2019, ApJL, 883, L41

(ref: cieza2021) Cieza, L. A., González-Ruilova, C., Hales, A. S., et al. 2021, MNRAS, 501, 2934

(ref: c6) Crida, A., Morbidelli, A., & Masset, F. 2006, Icarus, 181, 587–604

(ref: currie2015) Currie, T., Cloutier, R., Brittain, S., et al. 2015, ApJL, 814, L27

(ref: currie2014) Currie, T., Muto, T., Kudo, T., et al. 2014, ApJL, 796, L30

(ref: Dodson_Robinson_2011) Dodson-Robinson, S. E. & Salyk, C. 2011, The Astrophysical Journal, 738, 131

(ref: Dong_2017) Dong, R., Li, S., Chiang, E., & Li, H. 2017, The Astrophysical Journal, 843, 127

(ref: Dong_2018) Dong, R., Li, S., Chiang, E., & Li, H. 2018, The Astrophysical Journal, 866, 110

(ref: d95) Dorschner, J., Begemann, B., Henning, T., Jaeger, C., & Mutschke, H. 1995, A&A, 300, 503

(ref: d4) Dullemond, C. P. & Dominik, C. 2004, Astronomy & Astrophysics, 421, 1075–1086

(ref: d12) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool

(ref: 2018facchini) Facchini, S., Pinilla, P., van Dishoeck, E. F., & de Juan Ovelar, M. 2018, A&A, 612, A104

(ref: fedele2021) Fedele, D., Toci, C., Maud, L., & Lodato, G. 2021, ALMA 870 $\mu$m continuum observations of HD 100546. Evidence of a giant planet on a wide orbit

(ref: Follette_2017) Follette, K. B., Rameau, J., Dong, R., et al. 2017, The Astronomical Journal, 153, 264

(ref: Fung_2016) Fung, J. & Chiang, E. 2016, The Astrophysical Journal, 832, 105

(ref: h83) Hildebrand. 1983, Quarterly Journal of the Royal Astronomical Society, 24, 267

(ref: jorsater1995) Jorsater, S. & van Moorsel, G. A. 1995, AJ, 110, 2037

(ref: Lin_2011) Lin, M.-K. & Papaloizou, J. C. B. 2011, MNRAS, 415, 1445

(ref: l19) Lodato, G., Dipierro, G., Ragusa, E., et al. 2019, Monthly Notices of the Royal Astronomical Society, 486, 453–461

(ref: long2018) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17

(ref: lynden-bell_pringle_1974) Lynden-Bell, D. & Pringle, J. E. 1974, MNRAS, 168, 603

(ref: m0) Masset, F. 2000, Astronomy and Astrophysics Supplement Series, 141, 165–173

(ref: mathis_1977) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: montesinos2015) Montesinos, M., Cuadra, J., Perez, S., Baruteau, C., & Casassus, S. 2015, ApJ, 806, 253

(ref: perez_2020) Pérez, S., Casassus, S., Hales, A., et al. 2020, ApJL, 889, L24

(ref: p20) Pérez, S., Casassus, S., Hales, A., et al. 2020, The Astrophysical Journal, 889, L24

(ref: pi1) Pinilla, P., Benisty, M., & Birnstiel, T. 2012, A&A, 545, A81

(ref: Pinilla_2012) Pinilla, P., Benisty, M., & Birnstiel, T. 2012, Astronomy & Astrophysics, 545, A81

(ref: p15) Pinilla, P., Birnstiel, T., & Walsh, C. 2015, Astronomy & Astrophysics, 580, A105

(ref: pi2) Pinilla, P., de Juan Ovelar, M., Ataiee, S., et al. 2015, A&A, 573, A9

(ref: Pinilla_2016) Pinilla, P., Flock, M., Ovelar, M. d. J., & Birnstiel, T. 2016, Astronomy & Astrophysics, 596, A81

(ref: pinilla2018) Pinilla, P., Natta, A., Manara, C. F., et al. 2018, A&A, 615, A95

(ref: q15) Quanz, S. P., Amara, A., Meyer, M. R., et al. 2015, The Astrophysical Journal, 807, 64

(ref: q13) Quanz, S. P., Amara, A., Meyer, M. R., et al. 2013, The Astrophysical Journal, 766, L1

(ref: ri) Rice, W. K. M., Armitage, P. J., Wood, K., & Lodato, G. 2006, MNRAS, 373, 1619

(ref: rosotti2016) Rosotti, G. P., Juhasz, A., Booth, R. A., & Clarke, C. J. 2016, Monthly Notices of the Royal Astronomical Society, 459, 2790

(ref: s73) Shakura, N. I. & Sunyaev, R. A. 1973, A&A, 500, 33

(ref: st17) Stammler, S. M., Birnstiel, T., Panić, O., Dullemond, C. P., & Dominik, C. 2017, A&A, 600, A140

(ref: su193d) Suriano, S. S., Li, Z.-Y., Krasnopolsky, R., Suzuki, T. K., & Shang, H. 2019, MNRAS, 484, 107

(ref: w14) Walsh, C., Juhász, A., Pinilla, P., et al. 2014, The Astrophysical Journal, 791, L6

(ref: 2019diffusionfargo) Weber, P., Pérez, S., Benı́tez-Llambay, P., et al. 2019, ApJ, 884, 178

(ref: Wichittanakom_2020) Wichittanakom, C., Oudmaijer, R. D., Fairlamb, J. R., et al. 2020, Monthly Notices of the Royal Astronomical Society, 493, 234–249

(ref: Zhang_2016) Zhang, K., Bergin, E. A., Blake, G. A., et al. 2016, The Astrophysical Journal, 818, L16

(ref: zu3) Zhu, Z. & Stone, J. M. 2014, ApJ, 795, 53

# Observation details

In table [\[tab:obs_log\]](#tab:obs_log) we present the details of the Atacama Large Millimeter/sub-millimeter Array (ALMA) observations that were used in this work.

|                |            |           |           |                |               |
|:---------------|:----------:|:---------:|:---------:|:--------------:|:-------------:|
| Program ID     | Obs. Date  | Exp. Time | N$^\circ$ |   Baselines    | Configuration |
|                |            |   (min)   | Antennas  |     \(m\)      |               |
| 2015.1.00934.S | 2015-12-02 |   27.8    |    36     | 17.4 - 10803.7 | Extended (LB) |
| 2016.1.01511.S | 2016-10-26 |   69.4    |    43     | 15.1 - 1124.3  | Compact (SB)  |
|                | 2017-04-23 |   104.1   |    44     |  15.1 - 460.0  | Compact (SB)  |

# Convergence and resolution tests

Our `FARGO3D` simulations were run for a shorter time than the age of the HD 100546 system (simulation time: $0.74\,$Myr, estimated system age: $4.8\,\rm{Myr}$, (cite: Wichittanakom_2020)). This was done under the assumption that the disk model reaches a quasi-steady state within the simulated time. To confirm this assumption, we illustrate the temporal convergence behavior in the gap formation process of our model in Fig. [7](#cp) and show that our gas surface density does not vary significantly from $200\,$Kyr.

![](conv.pdf)

Furthermore , we carried out all of our `FARGO3D` simulations on a two-dimensional grid that resolved one-tenth of the pressure scale height. The consequent dimensions of the grid were $n_r=540$ radial and $n_\phi=1024$ azimuthal cells. To show that this resolution is sufficient and does not affect the results, we present a comparison of model VII and a simulation with the identical setup, but resolving one-twentieth scale height ($n_r=1080$, $n_\phi=2048$) in Fig. [8](#restest_gas). The result does not change significantly by the higher resolution. The strongest deviation arises with the nonphysical material accumulation at the location of the inner planet (13 au), where the peak is higher.

![](reslution_comparison.pdf)

</paper>

Write the methods card for this paper.