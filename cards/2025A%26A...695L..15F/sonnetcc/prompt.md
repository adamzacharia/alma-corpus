# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...695L..15F\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...695L..15F",
 "title": "Spatially resolved dust properties over 50 kpc in a hyperluminous galaxy merger at z = 4.6",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Fernández Aranda, Román",
 "n_authors": 22,
 "arxiv_id": "2502.10503",
 "doi": "10.1051/0004-6361/202453214",
 "alma_projects_linked_by_archive": [
  "2013.1.00576.S",
  "2015.1.00883.S",
  "2016.1.00668.S",
  "2017.1.00899.S",
  "2018.1.00119.S",
  "2018.1.00333.S",
  "2019.1.00219.S",
  "2021.1.00726.S"
 ]
}
```

Paper text:
<paper>
# Spatially resolved dust properties over 50 kpc in a hyperluminous galaxy merger at $z=4.6$

We present spatially resolved dust-continuum ALMA observations from rest-frame $\sim$ 60 to $\sim$ 600 $\upmu$m (bands 3–10) of the hyperluminous hot dust-obscured galaxy (hot DOG) *WISE* J224607.6–052634.9 (W2246–0526), at redshift $z=4.6$. W2246–0526 is interacting with at least three companion galaxies, forming a system connected by tidal streams. We model the multiwavelength ALMA observations of the dust continuum using a modified blackbody, from which we derive the dust properties (mass, emissivity index, area of the emitting region, and temperature) in the hot DOG and resolved structures across a region of nearly $\sim$50 kpc. The peak temperature at the location of the hot DOG, $\sim$ 110 K, is likely the consequence of heating by the central quasar. The dust temperature drops to $\sim$ 40 K at a radius of $\sim$ 8 kpc, suggesting that heating by the quasar beyond that distance is nondominant. The dust in the connecting streams between the host and companion galaxies is at temperatures between $30-40$ K, typical of starburst galaxies, suggesting it is most likely heated by recent, in-situ star formation. This is the first time dust properties are spatially resolved over several tens of kpc in a galaxy system beyond Cosmic Noon –this is more than six times the scales previously probed in galaxies at those redshifts.

# Introduction

Supermassive black holes (SMBHs) and their host galaxies assembled most of their mass in the early Universe ($z\sim\,1-6$), making it a critical epoch for galaxy evolution. During these periods of intense accretion and growth, SMBHs are expected to be active and obscured by dust and gas (cite: hickox2018), with active galactic nuclei (AGN) feedback likely shaping the properties of their interstellar medium (ISM) (cite: fiore2017; lammers2023). Consequently, the study of obscured quasars at high-redshift is critical for understanding the evolution of massive galaxies, and specifically obtaining spatially resolved observations is key to reveal the effect of AGN on their hosts.

Spatially resolved studies of dust properties in nearby galaxies are relatively common (cite: cooper2012; galametz2012; zhou2016; utomo2019). At high-redshift, however, the need for high resolution and sensitivity makes them very challenging. The Atacama Large Millimeter/submillimeter Array (ALMA) is one of the few facilities capable of reaching the necessary sensitivity to detect the lowest surface brightness emission of the coldest dust component in the far-infrared (FIR). However, mapping large areas and covering wide dynamic ranges at different frequencies remains very time consuming, even for bright objects. Only a few studies using ALMA have reported spatially resolved dust temperature measurements in high-redshift galaxies. (cite: litke2022) studied a tightly resolved starburst galaxy at $z=5.7$, finding a global temperature of 48.3 K over $\sim$ 4 kpc. (cite: akins2022) presented a $\sim$ 7 kpc resolved temperature map for a star-forming galaxy at $z=7.13$, with a global temperature of $T_d=41^{+17}_{-14}$ K. Among the literature, we identify only three other studies targeting quasar host galaxies with ALMA. (cite: shao2022) observed a FIR luminous quasar at $z=6.0$ and found a clear temperature gradient over $\sim$ 3 kpc radius toward the center, associated with the AGN. The dust temperature peaks at $\sim$ 70 K, and the global temperature is $T_d=53\pm4$ K. (cite: tsukui2023) reported a resolved dust temperature map for a quasar host galaxy at $z=4.4$, with a gradient peaking at $57.1\pm0.3$ K and outer temperatures of $\sim$ 38 K up to $\sim$ 4 kpc from the center. They associate the peak and gradient with warm dust heated by an AGN. Lastly, (cite: walter2022) targeted a quasar at $z=6.9$ and also found a temperature gradient ranging from over 130 K in the central resolution element (200 pc) to 30 K at 500 pc. These studies show how multiband, resolved ALMA observations can probe quasar-heated dust in galaxies at high-redshift.

In particular, hot dust-obscured galaxies (cite: eisenhardt2012; wu2012), among all obscured quasar populations, are unique sources to study the interplay between AGN and dust. Given their extreme luminosities (cite: tsai2015), strong SMBH accretion (cite: wu2018; li2024), and high ISM turbulence (cite: diazsantos2021), the ISM of hot DOGs is likely experiencing strong heating and feedback from the central quasar. In particular, WISE J224607.6–052634.9 (W2246–0526) is the most distant known hot DOG, at $z = 4.6$, only 1.3 Gyr after the Big Bang. Its extreme luminosity (cite: tsai2018) is mainly driven by its central quasar, which is likely undergoing super-Eddington accretion (cite: tsai2018) and most probably irradiating its surrounding ISM with intense X-ray emission (cite: fernandez2024). W2246–0526 is also undergoing a multiple merger, with dust tidal streams connecting the hot DOG with at least three minor galaxy companions, as shown by (cite: diaz2018) using ALMA Band 6 dust-continuum observations. The gas kinematics of W2246–0526 strongly suggests the presence of a large-scale turbulent outflow (cite: diaz2016), as well as several powerful and asymmetric nuclear outflows concentrated within the central $0.22\ensuremath{''}$ ($\sim1.5$  kpc) (Liao et al. in prep.).

In this letter, we present spatially resolved dust observations and properties for the entire W2246–0526 merging system over $\sim\,7.7\ensuremath{''}$ ($\sim$ 50 kpc). Throughout the paper, we assume a flat $\Lambda$CDM cosmology with $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$ and $\Omega_{\mathrm{M}}=0.3$.

# Observations and analysis

The W2246–0526 merger system was observed with the ALMA 12-m array during multiple cycles. The observations we compile in this letter are detailed in Table [\[tab:Obs\]](#tab:Obs). We reduced and calibrated the data using the Common Astronomy Software Applications (cite: mcmullin2007) with the standard data reduction procedures. To image the continuum using the `tclean` task of CASA v6.5, we ran the Hogbom cleaning algorithm (cite: 1974A&AS...15..417H) to a flux density threshold of two times the root mean square (rms) of each cube, with the Briggs weighting mode set to robustness = 2.0 (close to natural weighting), and with a uv-taper imaging weight equal to 0.8$\ensuremath{''}$ to enhance any extended emission. We further chose to homogenize all the datasets to the same resolution, matching the largest beam after the uv-tapering, by setting the restoring beam in `tclean` to a common circular beam of FWHM=1.0$\ensuremath{''}$. The cleaning was done using a circular mask with a radius of 7$\ensuremath{''}$, enough to cover the entire merging system. In each dataset, all emission line-free channels were combined to create the continuum intensity maps, which are shown in the Appendix [6](#appendix) (Fig. [5](#fig:A_mom0)). The entire resolved dust structures of the merger presented by (cite: diaz2018) are detected in four of the eight datasets used in this work, and are shown with the overlapped 2.5$\upsigma$ contours in Fig. [1](#fig:regions). The non-detection of the extended structures in the other four datasets may be due to smaller maximum recoverable scales in those observations, as shown in Table [\[tab:Obs\]](#tab:Obs).

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Central wavelength | Time on-source | Cont. depth | Native beam | MRS | ALMA Band | Project code |
| $[\upmu\mathrm{m}]$ | \[min\] | \[mJy beam$^{-1}$\] | $[\ensuremath{''}]$ | $[\ensuremath{''}]$ |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |
| 63 | 30 | 1.15 | $0.39\times0.32$ | 2.9 | 10 | 2017.1.00899.S |
| 88 | 172 | 1.36 | $0.36\times0.31$ | 3.4 | 9 | 2021.1.00726.S |
| 123 | 30 | 0.30 | $0.53\times0.38$ | 3.5 | 8 | 2016.1.00668.S |
| 149 | 124 | 0.040 | $0.44\times0.35$ | 4.5 | 7 | 2017.1.00899.S |
| 155 | 380 | 0.044 | $0.36\times0.30$ | 4.4 | 7 | 2018.1.00333.S |
| 211 | 148 | 0.017 | $0.54\times0.46$ | 5.1 | 6 | 2015.1.00883.S |
| 357 | 293 | 0.007 | $0.50\times0.39$ | 6.1 | 4 | 2019.1.00219.S |
| 572 | 31 | 0.019 | $0.35\times0.30$ | 4.0 | 3 | 2018.1.00119.S |

\

Notes: (1) Central rest-frame wavelength; (2) Integration time on-source; (3) Root mean square of the collapsed dataset; (4) Average size (FWHM) of the native beam, without uv-tapering; (5) Maximum recoverable scale; (6) ALMA receiver band; (7) ALMA project code

To characterize the FIR continuum emission in the system, we use a modified blackbody. Starting with the full radiative transfer equation, the flux density observed at frequency $\nu_{\mathrm{obs}}$ is $$\begin{equation}
    S_{\nu_{\mathrm{obs}}} = \frac{A}{D_L^2}[B_{\nu_{\mathrm{rest}}}(T_d)-B_{\nu_{\mathrm{rest}}}(T_{\mathrm{CMB}})][1-exp(-\tau_{\nu_{\mathrm{rest}}})](1+z)\ ,
    \label{eq:1}
\end{equation}$$ with $A$ being the physical area of emission, $D_L$ the luminosity distance, $T_d$ the temperature of the dust, $T_{\mathrm{CMB}}$ the cosmic microwave background (CMB) temperature at the redshift of the source, and with the blackbody emission being $$\begin{equation}
    B_{\nu}(T) = \frac{2h\nu^3}{c^2}\frac{1}{exp(\frac{h\nu}{k_B T})-1}\ ,
    \label{eq:2}
\end{equation}$$ and the optical depth of the dust being $$\begin{equation}
    \tau_{\nu} = \kappa_0 \left(\frac{\nu}{\nu_0}\right)^{\beta} \frac{M_d}{A}\ ,
    \label{eq:3}
\end{equation}$$ where $\beta$ is the dust emissivity index, $M_d$ is the dust mass, and $\kappa_0$ is the dust opacity at the reference frequency $\nu_0$. Following (cite: scoville2014) and assuming a gas-to-dust ratio of $\delta_{GDR}=200$, given that the metallicity in the hot DOG is $\sim0.5$ Z$_{\odot}$ (cite: fernandez2024), we adopt $\kappa_0=\kappa_{850\upmu\mathrm{m}}=0.0968\ \mathrm{kg}^{-1} \mathrm{m}^2$ and $\nu_0 = 352.7$ GHz (850$\upmu\mathrm{m}$). We note that $T_d$ is the dust temperature including the CMB heating, which at our redshift and for temperatures above 30 K (see Sect. [3](#sec:results)) is negligible (cite: dacunha2013).

We fit the modified blackbody of Eq. [\[eq:1\]](#eq:1) to every pixel with emission from the four spatially resolved datasets to derive the properties of the dust in the resolved structures. We use a Markov chain Monte Carlo approach using the `emcee` (cite: foreman2013) Python package, allowing $A$, $T_d$, $M_d$, and $\beta$ to vary freely using flat priors of $10^{-2}<A<33$ kpc$^2$, $12.6<T_d<300$ K, $10^6<M_d<10^{10}$ $M_{\odot}$, and $1<\beta<3$. The beam area limits the physical area of emission $A$, and the lower temperature limit corresponds to $T_{\mathrm{CMB}}$ at $z=4.601$. We also fit Eq. [\[eq:1\]](#eq:1) for the integrated central beam, corresponding to the hot DOG, for which we have emission from all eight datasets.

# Results

In Fig. [2](#fig:SED), we show the spectral energy distribution (SED) fit and the marginalized posterior distributions (PDFs) of the parameters for the integrated central beam, which contains the hot DOG, using all eight datasets. The corresponding fluxes are presented in Table [1](#tab:Fluxes) and the best fit dust parameters in Table [2](#tab:Params). The model parameters for the central beam are well constrained for a single modified blackbody, with $\beta=1.74\pm0.08$, $M_d=0.84_{-0.19}^{+0.20}\times10^8 M_{\odot}$, $T_d=109_{-15}^{+24}$ K, and $A=0.90_{-0.38}^{+0.60}$ kpc$^2$. The best-fit physical area of emission, $A$, is equivalent to that of a circle of diameter $\sim$ 1 kpc, or 0.15$\ensuremath{''}$, much smaller than the resolution of our observations (typically 0.4$\ensuremath{''}$, see Table [\[tab:Obs\]](#tab:Obs)) and consistent with a compact heating source. The area obtained from the fit is also consistent with the size of the region where the brightest fine-structure FIR emission lines are produced, with an upper limit on the radius of 800 pc from the central quasar (cite: fernandez2024). Also, our result for the temperature of the hot DOG is close to that obtained from the W2246–0526 SED fit using UV to submillimeter maps performed by (cite: sun2024), which found $T_d\sim$ 92 K, and higher than the estimates for the coldest dust component from (cite: diaz2018) and Tsai et al. (in prep.) of $\sim$ 70 K, which assume optically thin dust.

|                     |           |                 |
|:-------------------:|:---------:|:---------------:|
| Central wavelength  | ALMA Band |  Flux density   |
| $[\upmu\mathrm{m}]$ |           |     \[mJy\]     |
|         63          |    10     |  $51.0\pm0.8$   |
|         88          |     9     |  $29.6\pm0.6$   |
|         123         |     8     |  $12.5\pm0.3$   |
|         149         |     7     |   $7.4\pm0.2$   |
|         155         |     7     |   $7.3\pm0.2$   |
|         211         |     6     |   $2.7\pm0.1$   |
|         357         |     4     |  $0.40\pm0.04$  |
|         572         |     3     | $0.068\pm0.037$ |

: Central beam fluxes.

\

|          Parameter           |              Value               |    Unit     |
|:----------------------------:|:--------------------------------:|:-----------:|
|           $\beta$            |         $1.74 \pm 0.08$          |     ...     |
|            $M_d$             | $0.84_{-0.19}^{+0.20}\times10^8$ | $M_{\odot}$ |
|            $T_d$             |        $109_{-15}^{+24}$         |      K      |
|             $A$              |      $0.90_{-0.38}^{+0.60}$      |   kpc$^2$   |
| $\tau_{158\mathrm{\upmu m}}$ |      $0.39_{-0.18}^{+0.26}$      |     ...     |
| $L_{3-1100\mathrm{\upmu m}}$ |        $6.4\times10^{13}$        |  $L_\odot$  |

: Dust parameters for the hot DOG.

\

Notes: $\beta$, $M_d$, $T_d$, and $A$ are the best fit parameters for the central beam. $\tau_{158\mathrm{\upmu m}}$ is estimated using Eq. [\[eq:3\]](#eq:3), and $L_{3-1100\mathrm{\upmu m}}$ is the integral of the best fit modified blackbody.  

In Fig. [3](#fig:dustmaps) we present the spatially resolved maps of the best-fit parameters using the four datasets where extended emission is detected, from rest-frame 149 to 357 $\upmu$m. The temperature peaks at more than 100 K at the location of the quasar, and gradually descends to $\sim$ 40 K over a scale of $\sim$ 8 kpc, suggesting the quasar is heating the surrounding dust out to this distance. The dust temperature measured in the extended structures surrounding the hot DOG is relatively low, $\sim$ 30–40 K, and typical of star-forming galaxies at similar redshifts (cite: bethermin2020; cortzen2020; faisst2020). The dust mass distribution also peaks in the central region, and the combined dust mass of the whole system is $5.1\times10^8~M_{\odot}$. The dust emissivity index $\beta$ takes values between $\sim$ 1.4–2.0. The values for $M_d$ and $\beta$ are consistent with those from recent studies of various galaxy populations such as quasars, star-forming and submillimeter galaxies at $1<z<8$ (cite: dacunha2021; kaasinen2024). The physical areas of emission vary between $\sim$ 500 pc$^2$ and $\sim$ 1 kpc$^2$, much smaller than the $\sim$ 30 kpc$^2$ beam, implying areal filling factors of dust of 3$\%$ or smaller.

Fig. [4](#fig:dustmaps_derived) shows other derived dust properties. The optical thickness $\tau_{\nu}$ using Eq. [\[eq:3\]](#eq:3) is shown at rest-frame 158 ${\upmu\mathrm{m}}$, and indicates that even at these wavelengths there are some areas in the system displaying significant absorption. We also present the total IR luminosity ($3-1100 \upmu\mathrm{m}$) map derived by integrating the fitted modified blackbody of each pixel. $L_{3-1100\upmu\mathrm{m}}$ peaks at $\sim6\times10^{13}\ L_{\odot}$ beam$^{-1}$ in the central region, and gradually descends to $\sim10^{11}-10^{12}\ L_{\odot}$. Additionally, we estimate the star formation rate (SFR) surface density ($\Sigma_{SFR}$) as $\Sigma_{SFR}=\mathrm{SFR}/A$. The SFR is estimated from $L_{IR}$ as in (cite: kennicutevans2012), and $A$ is the intrinsic area derived from the modified blackbody fitting. Lastly, we show the star formation efficiency (SFE), calculated as $\mathrm{SFE=SFR}/M_{gas}$, with $M_{gas}=M_{d}\times\delta_{GDR}$. The SFE is enhanced in the north and the southeast of the system, reaching values as high as $10^{-7.25}$ yr$^{-1}$.

# Discussion

The temperature peak of $\sim$ 110 K measured in W2246–0526 is among the highest measured to date in galaxies at high-redshift, and is consistent with quasar heating. Integrating the modified blackbody fitted to the central beam results in a $L_{3-1100\upmu\mathrm{m}}=6.4\times10^{13}\ L_{\odot}$ (note that this does not include emission from hotter dust, which dominates the mid- and near-IR). To reproduce this luminosity we would require a $\Sigma_{SFR}\sim10^4\ M_{\odot}\ \mathrm{yr}^{-1}\ \mathrm{kpc}^{-2}$. This is well above the characteristic Eddington limit set by radiation pressure on dust grains in optically thick disks of $\Sigma_{SFR}\sim10^3\ M_{\odot}\ \mathrm{yr}^{-1}\ \mathrm{kpc}^{-2}$ (cite: thompson2005), suggesting that an obscured AGN is a more likely source of heating than an obscured, compact, extreme starburst. This agrees with other studies stating that a starburst is unlikely to be the dominant source of energy in extremely luminous hot DOGs (cite: eisenhardt2012; tsai2015).

Fig. [1](#fig:regions) shows that we resolve the dust emission over scales of 50 kpc. Theoretical models predict that sources with $L_{\mathrm{bol}}>10^{14}\ L_{\odot}$ can heat dust to temperatures of $30-40$ K at distances of tens of kpc if there are optically thin lines of sight (cite: scoville2013). In such cases, a temperature gradient would be expected, with dust being colder farther from the central quasar. However, our results show a fairly constant dust temperature across the tidal streams and companion galaxies. While we cannot entirely rule out quasar heating, especially if optical depth variations are present along the quasar’s line of sight, the uniformity of the temperatures suggests that the dust in these extended structures is predominantly heated by in-situ star formation. This indicates that stars are likely being formed within the dusty streams as they fly by or are accreted onto the central quasar and its host galaxy. We also estimate the SFR in the extended component to be $\sim800\ M_{\odot}\ \mathrm{yr}^{-1}$ by integrating the luminosity of the system outside the central 2 $\ensuremath{''}$ region displaying higher dust temperature. This is consistent with previous SFR estimations for W2246–0526 from total source integrated values (cite: sun2024), and lower and upper limits for the companions (cite: diaz2018). We speculate that the stellar mass being accreted into the central host during the merger process may include a contribution from star formation occurring in infalling, non-self-gravitating structures. In addition, a fraction of the stars formed in the dusty streams in the W2246–0526 system may end up as part of a future stellar halo.

Fig. [3](#fig:dustmaps) and Fig. [4](#fig:dustmaps_derived) show central anisotropies in $A$, $\beta$, and $\tau_{\nu}$. The area parameter has significant uncertainties (i.e., $A=0.90_{-0.38}^{+0.60}$ kpc$^2$ for the central beam), which makes the observed asymmetry in $A$ tentative. The fit to the $\beta$ parameter is much more robust, however, and we also observe an anisotropy, with higher $\beta$ values toward the southwest. The optical depth map shows the same anisotropy, but it virtually disappears if we fix $\beta$ in the fit. Therefore, higher optical depths are mainly driven by higher values of $\beta$.

Lastly, the high SFE regions coincide with the position of two companion galaxies detected in (cite: diaz2018), to the north and the southeast of the hot DOG (C2 and C3 in Fig. [1](#fig:regions)). Their $\Sigma_{SFR}\sim10^2\ M_{\odot}\ \mathrm{yr}^{-1}\ \mathrm{kpc}^{-2}$ is consistent with star formation, while their SFE correspond to molecular gas depletion times of less than 100 Myr, a relatively low value compared with starburst galaxies at low and high redshifts (cite: huang2014; elbaz2018; tacconi2018). Previous studies have suggested the SFE can be enhanced by ongoing mergers (cite: genzel2010; diazgarcia2020; sargent2024). Our result agrees with this interpretation, since W2246–0526 is experiencing multiple mergers. Although we cannot rule out the presence of additional obscured AGN in these companions, their contribution to the dust heating is likely minor, as suggested by their uniform temperature compared to the streams.

# Summary

We present spatially resolved ALMA multiband continuum observations of the W2246–0526 hot DOG merging system, at $z=4.6$. Fitting a modified blackbody to the data pixel-by-pixel, we derive for the first time the spatially-resolved dust properties over a scale of $\sim$ 50 kpc in a system only 1.3 Gyr after the Big Bang. The system contains an estimated total mass of dust of $5.1\times10^8M_{\odot}$. The dust temperature peaks at the position of the hot DOG at $\sim$ 110 K and decreases radially, suggesting dust is being heated by the central quasar up to a distance of $\sim$ 8 kpc. The dust in the tidal streams around the hot DOG and within the companion galaxies is at a relatively uniform temperature of 30–40 K with no evident gradients, suggesting the streams and companions are heated by obscured, recent star formation. These newly formed stars could contribute to the mass growth of the central galaxy and SMBH in W2246–0526 or eventually become part of a stellar halo, highlighting the potential role of extended structures in the mass assembly of high-redshift galaxies.

# Acknowledgements

This work is supported by the European Research Council under grant agreement No. 771282. MA acknowledges support from the ANID Basal Project FB210003 and ANID MILENIO NCN2024_112. RJA was supported by FONDECYT grant number 1231718 and by the ANID BASAL project FB210003. C.-W. T. is Supported by NSFC No. 11988101 and the International Partnership Program of the Chinese Academy of Sciences, Program No. 114A11KYSB20210010. RD acknowledges support from the INAF GO 2022 grant “The birth of the giants: JWST sheds light on the build-up of quasars at cosmic dawn” and from PRIN MUR “2022935STW” RFF M4.C2.1.1, CUP J53D23001570006 and C53D23000950006. Portions of this research were carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00576.S, ADS/JAO.ALMA#2015.1.00883.S, ADS/JAO.ALMA#2016.1.00668.S, ADS/JAO.ALMA#2017.1.00899.S, ADS/JAO.ALMA#2018.1.00119.S, ADS/JAO.ALMA#2018.1.00333.S, ADS/JAO.ALMA#2021.1.00726.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

42 natexlab

(ref: akins2022) Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64

(ref: bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: cortzen2020) Cortzen, I., Magdis, G. E., Valentino, F., et al. 2020, A&A, 634, L14

(ref: dacunha2013) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: dacunha2021) da Cunha, E., Hodge, J. A., Casey, C. M., et al. 2021, ApJ, 919, 30

(ref: diazgarcia2020) Dı́az-Garcı́a, S. & Knapen, J. H. 2020, A&A, 635, A197

(ref: diaz2018) Dı́az-Santos, T., Assef, R. J., Blain, A. W., et al. 2018, Science, 362, 1034

(ref: diaz2016) Dı́az-Santos, T., Assef, R. J., Blain, A. W., et al. 2016, ApJL, 816, L6

(ref: diazsantos2021) Dı́az-Santos, T., Assef, R. J., Eisenhardt, P. R. M., et al. 2021, A&A, 654, A37

(ref: eisenhardt2012) Eisenhardt, P. R. M., Wu, J., Tsai, C.-W., et al. 2012, ApJ, 755, 173

(ref: elbaz2018) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110

(ref: faisst2020) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, 498, 4192

(ref: fernandez2024) Fernández Aranda, R., Dı́az Santos, T., Hatziminaoglou, E., et al. 2024, A&A, 682, A166

(ref: fiore2017) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: foreman2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: galametz2012) Galametz, M., Kennicutt, R. C., Albrecht, M., et al. 2012, MNRAS, 425, 763

(ref: genzel2010) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091

(ref: hickox2018) Hickox, R. C. & Alexander, D. M. 2018, ARA&A, 56, 625

(ref: 1974A&AS...15..417H) Högbom, J. A. 1974, A&AS, 15, 417

(ref: huang2014) Huang, M.-L. & Kauffmann, G. 2014, MNRAS, 443, 1329

(ref: kaasinen2024) Kaasinen, M., Venemans, B., Harrington, K. C., et al. 2024, A&A, 684, A33

(ref: kennicutevans2012) Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531

(ref: lammers2023) Lammers, C., Iyer, K. G., Ibarra-Medel, H., et al. 2023, ApJ, 953, 26

(ref: li2024) Li, G., Assef, R. J., Tsai, C.-W., et al. 2024, ApJ, 971, 40

(ref: litke2022) Litke, K. C., Marrone, D. P., Aravena, M., et al. 2022, ApJ, 928, 179

(ref: mcmullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: cooper2012) Mentuch Cooper, E., Wilson, C. D., Foyle, K., et al. 2012, ApJ, 755, 165

(ref: sargent2024) Sargent, M. T., Ellison, S. L., Mendel, J. T., et al. 2024, arXiv e-prints, arXiv:2409.06572

(ref: scoville2014) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84

(ref: scoville2013) Scoville, N. Z. 2013, in Secular Evolution of Galaxies, ed. J. Falcón-Barroso & J. H. Knapen, 491

(ref: shao2022) Shao, Y., Wang, R., Weiss, A., et al. 2022, A&A, 668, A121

(ref: sun2024) Sun, W., Fan, L., Han, Y., et al. 2024, ApJ, 964, 95

(ref: tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: thompson2005) Thompson, T. A., Quataert, E., & Murray, N. 2005, ApJ, 630, 167

(ref: tsai2018) Tsai, C.-W., Eisenhardt, P. R. M., Jun, H. D., et al. 2018, ApJ, 868, 15

(ref: tsai2015) Tsai, C.-W., Eisenhardt, P. R. M., Wu, J., et al. 2015, ApJ, 805, 90

(ref: tsukui2023) Tsukui, T., Wisnioski, E., Krumholz, M. R., & Battisti, A. 2023, MNRAS, 523, 4654

(ref: utomo2019) Utomo, D., Chiang, I.-D., Leroy, A. K., Sandstrom, K. M., & Chastenet, J. 2019, ApJ, 874, 141

(ref: walter2022) Walter, F., Neeleman, M., Decarli, R., et al. 2022, ApJ, 927, 21

(ref: wu2018) Wu, J., Jun, H. D., Assef, R. J., et al. 2018, ApJ, 852, 96

(ref: wu2012) Wu, J., Tsai, C.-W., Sayers, J., et al. 2012, ApJ, 756, 96

(ref: zhou2016) Zhou, L., Shi, Y., Diaz-Santos, T., et al. 2016, MNRAS, 458, 772

# Intensity maps

\
\

</paper>

Write the methods card for this paper.