# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A..85K\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...701A..85K",
 "title": "Early galaxy evolution: The complex interstellar medium distribution of the z ∼ 7 galaxy A1689-zD1",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Knudsen, Kirsten K.",
 "n_authors": 15,
 "arxiv_id": "2509.19475",
 "doi": "10.1051/0004-6361/202453229",
 "alma_projects_linked_by_archive": [
  "2015.1.01406.S",
  "2017.1.00775.S"
 ]
}
```

Paper text:
<paper>
# Early galaxy evolution: The complex interstellar medium distribution of the $z\sim7$ galaxy A1689-zD1

We observed the gravitationally lensed ($\mu = 9.6\pm0.19$) galaxy A1689-zD1 at $z = 7.1$ in bands 3, 6, and 8 of the Atacama Large Millimeter/submillimeter Array. These high-resolution observations ($\approx
200$ pc) enabled us to separate the source into five components in the \[C ii\]$\,158\mu$m and \[O iii\]$\,88\mu$m emission lines within a projected distance of 2 kpc. Even though these components appear to vary strongly from one another in both their line, continuum, and optical characteristics, the assembly of components do not show ordered rotation and appear consistent with simulations of a galaxy system undergoing the process of assembly. The total dynamical mass of the galaxy ($2\times10^{10}$ M$_\odot$) is an order of magnitude larger than the spectrally estimated stellar mass, suggesting a near-complete optical obscuration of the bulk of the stellar component. Comparing the line ratios as well as the line properties to other properties such as the star formation rate, we find that A1689-zD1 is consistent with the relations derived from local star-forming galaxies. Even though A1689-zD1 lies on local star formation scaling relations and has a high dust and stellar mass estimate, the kinematics suggest it is in an early assembly stage, which could lead to it becoming a disk galaxy at a later stage.

# Introduction

Galaxies at redshifts of $z>6$ represent the early stages of galaxy formation and evolution, often referred to as cosmic dawn. Discovering these galaxies and determining their physical properties is key to understanding the further phases of galaxy evolution (cite: bouwens22b; finkelstein23; rieke23). Furthermore, these galaxies are essential for understanding the galaxy-scale processes that gave rise to the epoch of reionization (cite: hutter21). The gradual change of a steeper slope of the faint end of the ultraviolet (UV) luminosity function with increasing redshift (cite: mclure13; finkelstein15; oesch18; bouwens22a) implies an increased relative importance of the sub-$L*$ population’s contribution to the overall production of the UV light responsible for reionization. However, mapping galaxies at redshifts $z>6$ is challenged by the enormous distances resulting in faint appearance, the redshifting of the rest-frame UV/optical/near-infrared (NIR) light into wavelengths with low atmospheric transmission, and the varying morphologies (i.e., clumpiness; e.g., (cite: gullberg18)) of galaxies in the early Universe might be more difficult to resolve with sensitive interferometers.

An efficient way to study the sub-$L*$ $z>6$ galaxy population is through gravitational lens studies. The gravitational lensing magnification aids the time expensive observations of the low-luminosity galaxy population enabling detailed studies of individual sources. Using submillimeter wavelength observations to resolve emission lines is a necessary means for determining physical properties and characterizing the dynamical state of such galaxies. The far-infrared (FIR) fine-structure lines of ionized carbon and oxygen has proven essential for this (cite: hashimoto19; harikane20). For local galaxies, even dwarf galaxies, relations between the star formation rate (SFR) and the line luminosity of the FIR fine-structures lines have been established (cite: delooze14; cormier15). However, the growing number of \[C ii\] observations of $z>6$ sub-$L*$ galaxies have yielded a more complicated result for the early epoch (cite: capak15; knudsen16; bradac17; carniani17; hashimoto18; tamura19; laporte19; bakx20; jolly21; fujimoto21; molyneux22); for example, some of those early \[C ii\] observations yielded several non-detections or line luminosities lower than initially predicted. With the combination of high sensitivity and sub-arcsecond resolution of modern submillimeter interferometric observatories, it has become possible to resolve line emission even for $z>6$ galaxies. This makes it possible to conduct dynamical studies (cite: carniani13; litke19; spilker22; rowland24); however, without gravitational lensing, reaching sub-kpc scales remains challenging. Numerical zoom-in simulations of $z>6$ galaxies show that the kinematics can be very complex. For example, (cite: kohandel19) demonstrate that the same galaxy over the course of hundred million years can change appearance from a merging system to a rotating disk. The same simulations, as well as those of (cite: katz22), also reveal how the predicted observations are dependent on the orientation, showing the difficulty of distinguishing different dynamical states with only low angular resolution.

The galaxy A1689-zD1 was reported as a $z>7$ candidate with a photometric redshift of $z = 7.6$ (cite: bradley08) and this was confirmed with X-shooter spectroscopy that showed a break in the continuum emission at a redshift of $z=7.5\pm0.2$ (cite: watson15). A1689-zD1 was also the first sub-$L*$ with a dust-detection with the Atacama Large Millimeter/submillimeter Array (ALMA), revealing not only a dust mass similar to that of the Milky Way interstellar medium (ISM), but also a complex distribution that could be interpreted as a potentially interacting system (cite: watson15; knudsen17).

Some of the brightest FIR fine-structure lines are \[C ii\] 158$\mu$m and \[O iii\] 88$\mu$m in star-forming galaxies. As carbon has an ionization potential of 11.2 eV, which is below that of hydrogen, the \[C ii\] line is used for both tracing neutral and ionized gas. Ionized oxygen has an ionization potential of 35.1 eV and, thus, it is only observed in the ionized medium (e.g., H ii regions). Thus, while each of these two bright emission lines can be used to resolve the properties of the ISM, when used in combination, they also provide insights to the ionization state of the ISM in early galaxies (cite: harikane20; killi23).

Here, we present deep imaging of the two FIR fine-structure lines \[C ii\] 158$\mu$m and \[O iii\] 88$\mu$m for A1689-zD1. Some of these data were recently analyzed and the results have begun shedding light on different aspects about FIR properties (cite: bakx21; akins22; Wong2022; killi23). While the original goal of the \[C ii\] observations was to determine the redshift, the \[C ii\] and \[O iii\] data enable imaging of sub-kpc scales thanks to the gravitational lensing amplification (thereby enabling multi-component decomposition). Furthermore, we present detection limits from molecular gas observations. The paper is structured as follows. Section [2](#sect:obs) presents the ALMA observations and data, along with Green Bank Telescope (GBT) observations of CO(3–2). Section [3](#sect:res) gives the results including an analysis of the complex gas kinematics. A discussion is given in Sect. [4](#sect:disc) and our conclusions are summarized in Sect. [5](#sect:concl). We assume a $\Lambda$ cold dark matter cosmology, with $H_0~=~67.7$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M = 0.307$, and $\Omega_\Lambda =
0.693$ (cite: planck15).

# Observations

## ALMA data

Observations of A1689-zD1 were obtained with ALMA to search for the \[C ii\]$\,158\mu$m and subsequently to follow-up the \[O iii\]$\,88\mu$m line (ALMA projects 2015.1.01406.S and 2017.1.00775.S). The \[C ii\] observations were tuned to match frequencies of candidate emission lines found in previous data (cite: knudsen17). The receivers were tuned to 217.19–220.94 and 231.98–235.74 GHz, where the line was predicted to be in the former frequency range. The calibrators used were J1337$-$1257 for flux calibration, J1256$-$0547 for bandpass, and J1319$-$0049 for gain calibration. Data were calibrated using the ALMA pipeline; we verified the observatory delivered calibration with only the need for limited additional flagging, however, three out of ten executions needed the absolute flux calibration redone as the pipeline had not included the correct values for the flux calibrator. After this correction, the uncertainty of the absolute flux calibration is estimated to be about 5% [^2]. Combining the data from all ten executions, we reached an overall depth of 0.18–0.2 mJy/beam in a 5 km s$^{-1}$ channel[^3] when imaging using a Briggs weighting with a robust parameter of 0.5; the angular resolution is $0.29''\times0.27''$ and the position angle (PA) is $-80.8^\circ$. When combining the lower frequency band with the continuum data from (cite: knudsen17), we obtained a root mean square (rms) flux uncertainty of about 6.3 $\mu$Jy/beam.

The emission line in the upper frequency band was detected at $\nu = 233.3$ GHz and identified as the \[C ii\]$\,158\mu$m emission line corresponding to a redshift of $z_{\rm [CII]} = 7.133$. Using this redshift ALMA band 8 observations were obtained for the \[O iii\]$\,88\mu$m line. The receivers were tuned to 404.40–408.21 and 416.33–420.09 GHz. Calibration was performed using J1229+0203 for flux and bandpass calibration, and J1256$-$0547 for gain calibration. The observatory-delivered calibrated data were checked and considered sufficient, and no further treatment was done. The data were imaged, yielding a continuum map with rms of 29 $\mu$Jy/beam and an line cube with an rms of 0.39–0.44 mJy/beam in $\sim$11 km s$^{-1}$ (15.625 MHz) channels. The resulting images have an angular resolution of $0.33''\times0.28''$, PA=$-87.3^\circ$, which is similar to the resolution of \[C ii\] and band 6 maps. A conservative estimate on the absolute flux calibration is 10%. A continuum subtraction was performed for both the \[C ii\] and \[O iii\] data cubes using the CASA task uvcontsub where the continuum was estimated using the line-free channels.

ALMA band 3 observations of the CO(6–5) and CO(7–6) lines were obtained using a receiver setup of 84.07–87.83 GHz and 96.16–99.94 GHz (ALMA project 2017.1.00775.S). The calibrator J1256$-$0547 was used for flux and bandpass calibration, while J1319$-$0049 was used for gain calibration. The observatory-delivered, calibrated data were of sufficient quality. The data were imaged using natural weighting and also using *uv*-tapering with a circular Gaussian profile of 0.5 arcsec resulting in an angular resolution of $0.92''\times0.80''$ (PA=64$^\circ$). The rms in the continuum map is 11 $\mu$Jy/beam, and in the spectral cube near the frequency of redshifted CO(6–5) \[CO(7–6)\] the rms is 0.23 \[0.20\] mJy/beam in a 15.625 MHz channel (corresponding to a 55 \[47\] km s$^{-1}$ channel width).

## GBT data

Using the GBT[^4] observations, we carried out a search for the redshifted CO(3–2) emission with the Q-band (40–50 GHz) receiver. Six observing sessions (AGBT14A_565) were undertaken in September-October 2014 and an additional eight sessions (AGBT18A_230) were carried out in February-September 2018. In total, 64 hours of telescope time were used for searching for CO(3–2) emission. The data were collected with the VEGAS spectrometer using the wide bandwidth modes 1 and 3. The observations were done using the sub-reflector nodding (“SubBeamNod") observing mode with a six-second switching period between the two Q-band beams that are separated by 58 arcsec on the sky. At the central observed frequency of 42.5 GHz, the full width at half maximum (FWHM) resolution of the GBT beam is about 17 arcsec. The bright nearby quasar 3C279 was used for pointing and focus, while 3C286 was used for absolute flux calibration (cite: perley17). After correcting for atmosphere, pointing drifts, and calibration, the uncertainty on the final flux density scale is approximately 15%.

## HST data

We reprocessed all available *Hubble* Space Telescope (HST) and *Spitzer* data in archive in the A1689 field as a part of the Complete Hubble Archive for Galaxy Evolution (CHArGE; Brammer, in prep), which aims to perform uniform processing and analysis of all archival HST and *Spitzer* data taken away from the Galactic midplane (cite: fujimoto2022). We aligned all of the HST exposures to sources in the *Gaia* DR2 catalog (cite: gaia2018) and created final mosaics in a common pixel frame with 50 mas and 100 mas pixels for the Advanced Camera for Surveys (ACS) Wide Field Channel (WFC) and Wide Field Camera 3 (WFC3) IR filters, respectively. We aligned the individual *Spitzer* exposures to the same astrometric frame as the HST frame and generated final drizzled IRAC mosaics with $0.5\ensuremath{''}$ pixels. Further details of the HST (*Spitzer*) image processing with the `grizli` (`golfir`) software is presented in (cite: kokorev22).

# Results

![image](A1689zD1_cii_imm01_all_new2.png)![image](A1689zD1_oiii_imm01_all_new2.png)

## \[C ii\] and \[O iii\]

Emission lines are detected in both ALMA data sets consistent with \[C ii\]$\,158\mu$m and \[O iii\]$\,88\mu$m. Both lines show a complex line profile as well as complex surface brightness distribution. Similarly, the continuum emission shows a complex structure consistent with the integrated emission line distribution. In Fig. [1](#fig:momentmaps), we show the moment-0 and moment-1 maps, while in Figs. [2](#fig:ciimosaic) and [3](#fig:oiiimosaic), we show the line emission per 40 km s$^{-1}$ channel for both lines. The integrated line intensity along with continuum flux densities are given in Table [1](#tab:fluxresults). The band 6 and band 8 continuum results are consistent with the photometric results from (cite: knudsen17) and (cite: inoue20).

![](a1689zd1-cii_mosaic_withcolorbar.png)

![](a1689zd1-oiii-mosaic_withcolorbar.png)

| Line | $I_{\rm line}$ (Jy km s$^{-1}$) | $L_{\rm line}$ |  |
|:---|---:|---:|:---|
|  | $4.4\pm 0.1$ | $(5.8\pm0.1)\times 10^{8}$ | L$_\odot$ |
|  | $5.3\pm 0.1$ | $(1.3\pm0.02)\times10^9$ | L$_\odot$ |
| CO(3–2) | $<$0.034 | $< 6.2\times 10^{8}$ | K km s$^{-1}$ pc$^2$ |
| CO(6–5)$^{a}$ | $<0.68$ | $<3.1\times10^9$ | K km s$^{-1}$ pc$^2$ |
| CO(7–6)$^{a}$ | $<0.64$ | $<2.1\times10^9$ | K km s$^{-1}$ pc$^2$ |
| $^{a}$ | $<0.64$ | $<3.8\times10^7$ | L$_\odot$ |
|  |  |  |  |
| Continuum | $S_{\nu}$ (mJy) |  |  |
| 417 GHz | $1.5\pm0.13$ |  |  |
| 233 GHz | $0.49\pm0.032$ |  |  |
| 91 GHz$^a$ | $<47$ |  |  |

: Integrated line intensity and continuum flux density.

Table notes: The line luminosity is corrected for gravitational lensing magnification.\

## Redshift

The \[C ii\]$\,158\mu$m and \[O iii\]$\,88\mu$m lines suggest central redshifts of 7.1329 and 7.1334, respectively, based on a single Gaussian profile fit. Taking the mean of these as the systemic redshift and the difference as the uncertainty, we find A1689-zD1 is at $z=7.1332\pm0.0005$. This is significantly ($\sim13\,000$ km s$^{-1}$) offset from the redshift derived from the NIR spectrum of the Lyman-break in (cite: watson15), which was $7.5\pm0.2$. This is similar to the 11 000km s$^{-1}$ difference seen in redshift determination using optical/NIR spectroscopy and ALMA spectroscopy for MACSJ1149-JD at $z = 9.11$ in \[O iii\] emission (cite: hashimoto18) and the photometric redshift of 9.51 (cite: hoag18), as well as for GNz11 of $z_{\rm grism} = 11.1$ versus $z_{\rm spec} = 10.6$ confirmed with the JWST (cite: oesch16; bunker23). As bright Lyman-alpha emission or other UV emission lines have not been detected in the spectra, the optical redshift has been derived based on the continuum break. However, given the potential large column of HI along the line of sight as well as the relative faintness of these distant galaxies provides a challenge for obtaining redshifts. A detailed analysis of this will be provided in Watson et al. (in prep.).

## Molecular gas

Figure [4](#fig:gbtco32) shows the result of the GBT observations. The CO(3-2) line was not detected, and the $3\sigma$ limit is given in Table [1](#tab:fluxresults) assuming a linewidth of 300 km s$^{-1}$. To mitigate residual baseline structures high-pass filtering methods were applied to the individual SubBeamNod data scans. These filtering methods would remove any underlying broad features ($>1000$ km s$^{-1}$), while preserving emission for the expected line width of about 300 km s$^{-1}$ and, thus, resulting in a flat spectrum (Fig. [4](#fig:gbtco32)). Although the line was not detected, if we were to smooth the data further, there is a weak, nearly $2\sigma$ bump (with a width of about $200\pm100$ km s$^{-1}$ at $z=7.13$ when fit by a Gaussian) at the expected frequency. Hundreds of hours of additional GBT time would be required to test whether this ”bump” is real.

![](co32gbt.png)

![image](ALL_spectrum_CII.pdf) ![image](ALL_spectrum_OIII_2.pdf)

The CO(6–5), CO(7–6), and the \[C i\](1-0) 492 GHz lines were not detected in the ALMA band 3 data. Assuming a linewidth of 300 km s$^{-1}$ and an area similar to the \[O iii\] detection, we estimated $3\sigma$ upper limits for all three transitions. These are given in Table [1](#tab:fluxresults). We note that detection of moderately high-$J$ CO transitions is a challenge of $z>6$ galaxies (cite: hashimoto23).

## Gravitational lensing

We used a parametric model of the Abell 1689 mass distribution to estimate the magnification and distortions at the location of A1689-zD1, as well as across the source. Our reference mass model is constructed with the `Lenstool` software (cite: jullo07) and described in (cite: limousin07).

At the measured spectroscopic redshift of $z = 7.133$ this model predicts a single image at this location with a total magnification of 9.6, involving an angular magnification of $\sim$6$\times$, along a specific direction at ${\rm PA}=85$ degrees (roughly east-to-west), and $1.6\times$ perpendicular to it. The amplification factor and shear directions do not vary by more than 10% and $5\ensuremath{^\circ}$, respectively, across the 1.5$''$ extent of the source (Table [2](#tab:comp_mu)). This is due to the fact that there is no significant cluster substructure or cluster member identified in the vicinity of A1689-zD1, which could locally affect the mass distribution and magnification.

To estimate the errors on the magnification factor, we used the best-fit mass model and the range of Markov chain Monte Carlo samples from the optimisation performed in `Lenstool` by (cite: limousin07). We obtain a statistical relative error of 19% (Table [2](#tab:comp_mu)). In addition, we make use of additional existing mass models of the same cluster (e.g., (cite: Xue)) where a different value is used for the relative contribution of the cluster-scale and galaxy-scale distribution of the mass model, to estimate the systematic uncertainty on the average magnification of the source. We estimate a systematic relative error of 10%.

The angular magnification implies an angular resolution in the \[C ii\] map of $\sim0.037''\times0.15''$, which correspond to $0.2\,\mathrm{kpc}\times 0.78\,$kpc. Correcting the sensitivity for the magnification, this implies a spectroscopic rms of $\sim20\,\mu$Jy/beam per 5 km s$^{-1}$ channel and a continuum sensitivity of 0.67 $\mu$Jy/beam for the band 6 data, making this some of the deepest data obtained for a single high-$z$ galaxy with ALMA.

For the \[O iii\] data, the magnification-corrected resolution is $\sim 0.051''\times 0.18''$ corresponding to $0.27\,\mathrm{kpc}\times0.95\,$kpc. The spectroscopic sensitivity corresponds to 42–47 $\mu$Jy/beam in a $\sim11$ km s$^{-1}$ channel and the continuum sensitivity is $3.1\,\mu$Jy/beam.

|           |               |
|:----------|:-------------:|
| Component |     $\mu$     |
|           |               |
| *Violet*  | 9.44$\pm$1.79 |
| *Blue1*   | 9.44$\pm$1.79 |
| *Blue2*   | 9.38$\pm$1.78 |
| *Green*   | 9.62$\pm$1.83 |
| *Yellow*  | 9.84$\pm$1.87 |
| *Red1*    | 9.34$\pm$1.77 |
| *Red2*    | 9.48$\pm$1.80 |

: Individual magnification factors for the different components.

## Decomposition into galaxy components

When stepping through the continuum-subtracted ALMA line datacubes, both \[C ii\](Fig. [2](#fig:ciimosaic)) and \[O iii\](Fig. [3](#fig:oiiimosaic)) show emission peaking at different spatial locations in the source as a function of velocity. This complex structure is dominated by three main spatial components with a maximum flux at $\sim-80$ ("blue"), $\sim0$ ("green"), and $\sim+160$ km s$^{-1}$ ("red") and present in both emission lines. This multi-component structure was already evident from the complexity seen in previous continuum results (cite: knudsen17). However, emission lines at a high S/N now provide us with a better possibility for disentangling this scenario.

First, as made clear from the relative spatial locations of the main components, as well as the moment-1 map derived from the cube (Fig. [1](#fig:momentmaps)), they do not follow a regular structure (as seen, e.g., in regular rotating disk galaxies). Therefore, we identified and model each component from the datacubes using an iterative process: (1) we produce a narrowband image from the line data comprising the main channels of emission in each component; (2) we fit this image with a 2D elliptical Gaussian model for the line flux distribution (including the central location, total flux, full width at half maximum (FWHM) along major and minor axes, and PA of the major axis); (3) we extracted the corresponding spectrum of this component and fit line parameters with a 1D Gaussian (central velocity, $v_0$, velocity dispersion, $\sigma_0$); and (4) we subtracted a 3D model of line emission for this component combining the spatial and spectral model.

Due to the proximity of some components (both spatially and in velocity space), this fit is performed three times iteratively, subtracting all other components from the datacube before a new fit. In addition to the three main components mentioned above, two fainter components peaking at $\sim +80$ ("yellow") and $\sim-220$ ("violet") km s$^{-1}$ were added, and more complex spatial distributions of the flux were used when necessary from the residuals. A few extended components also revealed a spatial variation of the line peak, which we fit using an empirical velocity gradient model (arctan model with a truncation velocity, $v_t$, and a truncation radius, $r_t$). We summarize the decomposition into five components below and we provide the full model parameters in Tables [\[tab:CIIcomponents\]](#tab:CIIcomponents) and [\[tab:OIIIcomponents\]](#tab:OIIIcomponents). We note that we originally identified the components from the \[C ii\] data, but we recovered the same structure in the \[O iii\] data, where we followed similar narrowband images and spatial distributions for the fit of each component.

Violet: The faintest of the five components. It was fit with a single non-rotating component and for \[C ii\], the fit was made challenging by empty channels between the spectral windows.

Blue: Modeled with two elliptical Gaussian components. One is extended with rotation (denoted "blue1") and one compact with only weak rotation ("blue2"). Their central positions are close but not identical.

Green: Broad component modeled with a single extended source, which has weak rotation.

Yellow: Single compact component with no measurable rotation.

Red: Combination of two individual elliptical Gaussian profiles with weak rotation, extended in the WSW-ENE direction.

Combining these five components, we recovered 95 and 97% of the total emission measured in the \[C ii\] and \[O iii\] line data, respectively, (Fig. [5](#fig:cii_spec_model)) in the inner region (not the extended region studied in (cite: akins22)). Some extra emission, somewhat diffuse, appears to be present but cannot easily be modeled as individual components. It is worth noting that the choice of decomposition (number of components and their parametrization), while somewhat arbitrary, is driven by the complexity and the high signal-to-noise ratio (S/N) of the data. Correcting the data for gravitational magnification, the extracted components are found to have sizes in the range 0.1–1 kpc.

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Component | $x_c$ | $y_c$ | FWHM$_1$ | FWHM$_2$ | $\theta$ | Flux | $v_0$ | $\sigma_0$ | $v_t$ | $r_t$ | $i$ | $\theta_v$ |
|  | \["\] | \["\] | \["\] | \["\] | \[deg\] | \[Jy km s$^{-1}$\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] | \["\] | \[deg\] | \[deg\] |
| *Violet* | -0.4 | 0.2 | $<$0.13 | $<$0.31 | \[0.0\] | 0.06$\pm$0.01 | -235 | 40 | 10 | 0.5 | \[30\] | 180 |
| *Blue1* | 0.2 | 0.1 | 0.61 | 1.32 | 80.8 | 0.85$\pm$0.02 | -90 | 75 | 60 | 2.4 | \[30\] | -20 |
| *Blue2* | 0.4 | 0.1 | $<$0.14 | $<$0.34 | \[0.0\] | 0.10$\pm$0.01 | -50 | 40 | 10 | 0.5 | \[30\] | 180 |
| *Green* | -0.3 | -0.3 | 0.38 | 0.57 | 96.3 | 0.55$\pm$0.02 | 20 | 90 | 40 | 2.8 | \[30\] | 200 |
| *Yellow* | -0.6 | -0.6 | $<$0.08 | $<$0.24 | \[0.0\] | 0.04$\pm$0.01 | 76 | 60 | 0 | 0.1 | \[30\] | -35 |
| *Red1* | 0.1 | 0.3 | 0.23 | 0.60 | 75.4 | 0.42$\pm$0.02 | 160 | 60 | 5 | 0.5 | \[30\] | -20 |
| *Red2* | -0.6 | 0.2 | 0.45 | 0.45 | 0.0 | 0.13$\pm$0.02 | 160 | 60 | 5 | 0.5 | \[30\] | -20 |

Table notes: Central position is provided from the location $\alpha=$197.8747351 $\delta=-$1.3218751. The FWHM values are corrected for the beam, but not for the gravitational magnification. Values in square brackets are fixed parameters. Correcting the data for gravitational magnification, the extracted components are found to have sizes in the range 0.1–1 kpc.

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Component | $x_c$ | $y_c$ | FWHM$_1$ | FWHM$_2$ | $\theta$ | Flux | $v_0$ | $\sigma_0$ | $v_t$ | $r_t$ | $i$ | $\theta_v$ |
|  | \["\] | \["\] | \["\] | \["\] | \[deg\] | \[Jy km s$^{-1}$\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] | \["\] | \[deg\] | \[deg\] |
| *Violet* | -0.3 | 0.1 | 0.23 | 0.23 | 0.0 | 0.20$\pm$0.01 | -235 | 40 | 10 | 0.5 | \[30\] | 180 |
| *Blue1* | 0.2 | 0.0 | 0.46 | 0.84 | 57.4 | 1.66$\pm$0.03 | -60 | 90 | 60 | 2.4 | \[30\] | -20 |
| *Blue2* | 0.4 | 0.2 | $<$0.14 | $<$0.39 | \[0.0\] | 0.28$\pm$0.01 | -50 | 40 | 10 | 0.5 | \[30\] | 180 |
| *Green* | -0.2 | -0.2 | 0.31 | 0.41 | 83.4 | 2.36$\pm$0.02 | 20 | 90 | 40 | 2.8 | \[30\] | 200 |
| *Yellow* | -0.6 | -0.6 | $<$0.1 | $<$0.39 | \[0.0\] | 0.20$\pm$0.01 | 76 | 50 | 0 | 0.1 | \[30\] | -35 |
| *Red1* | 0.1 | 0.3 | 0.14 | 0.54 | 81.0 | 0.78$\pm$0.03 | 160 | 50 | 5 | 0.5 | \[30\] | -20 |
| *Red2* | -0.5 | 0.1 | 0.32 | 0.32 | 0.0 | 0.38$\pm$0.01 | 160 | 50 | 5 | 0.5 | \[30\] | -20 |

Table notes: Central position is provided from the location $\alpha=$197.8747351 $\delta=-$1.3218751. The FWHM values are corrected for the beam, but not for the gravitational magnification. Values in square brackets are fixed parameters.

For comparison of the derived model to the data, we show the moment-0 and moment-1 maps of both the observations and the model in Fig. [6](#fig:cii_model_res) for both \[C ii\] and \[O iii\]. The residual maps indicate that the models effectively reproduce the observations. We note that for \[C ii\] there could be a small offset and that this could be due to the \[C ii\] emission having an additional extended component (cite: akins22), which adds to the complexity of the source.

![image](imm01_all_v2_pres_new_v2.png) ![image](imm01_all_v2_pres_o3_new_v2.png)

In Fig. [7](#fig:cii_HST) we show the contours of the individual components from \[C ii\] and \[O iii\] overlaid on the HST images. The relative astrometry of the HST and ALMA images should be correct to $0.^{\prime\prime}03$ allowing us to make a robust comparison of the galaxy’s UV and the ALMA results. As the HST data show no significant systematic color change across the galaxy, we used a stacked image combining the data from observations using the F125W, F140W, and F160W HST filters to increase the S/N of the rest-frame UV data. For further illustration of the data, we show the decomposed components in the 3D in Fig. [8](#fig:3d), using an approach to showing 3D data similar to that of (cite: spilker22) and showing the emission of each component above S/N of 3.

The clearest difference between the UV and FIR data is the number of components, with two components seen in the UV and the five components of the \[C ii\] and \[O iii\] data. Both the violet and yellow components have no obvious UV-counterpart. Given the apparent offsets between the green, blue, and red components, we cannot unambiguously associate the components with the UV-components. One possible interpretation is that green is associated with the SW UV-component and blue is associated with the NE UV-component. In contrast, the violet and yellow components do not show HST counterparts, while dust continuum emission is detected from these components. This suggests that completely dust-obscured regions exist in this system, consistent with the highly ($\simeq80-90$%) obscured SFR fraction of A1689-zD1 (cite: bakx21; akins22). This is also reminiscent of the recent identification of completely dust-obscured HST-dark galaxies at $z>7$ (cite: fudamoto21). We further discuss the possible origins of these components in Sect. [4](#sect:disc) below.

![image](new_HSTstack_componentscontours_Cp.png) ![image](new_HSTstack_componentscontours_O3.png)

![](3D_plots.pdf)

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Comp. | $S_{\rm 88 \mu m, ap}$ | $S_{\rm 158 \mu m, ap}$ | $S_{\rm 88 \mu m, mod}$ | $S_{\rm 158 \mu m, mod}$ | $T_{\rm dust, ap}$ | $L_{\rm IR, ap}$ | $T_{\rm dust, mod}$ | $L_{\rm IR, mod}$ | $L_{\rm IR, 41K}$ |
|  | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] | \[K\] | \[$10^{10}L_{\odot}$\] | \[K\] | \[$10^{10}L_{\odot}$\] | \[$10^{10}L_{\odot}$\] |
| *Violet* | $0.15\pm0.02$ | $0.03\pm0.01$ | $0.20\pm0.04$ |   $0.01\pm0.01$$^{a}$ | 68$_{-23}^{+46}$ | 4.9$_{-3.3}^{+16}$ | – | – | 1.1$_{-0.6}^{+1.8}$ |
| *Blue* | $0.30\pm0.01$ | $0.09\pm0.02$ | $0.57\pm0.10$ | $0.16\pm0.04$ | 47$_{-7}^{+8}$ | 3.7$_{-1.0}^{+1.5}$ | 53$_{-13}^{+17}$ | 8.9$_{-4.9}^{+11}$ | 5.0$_{-2.1}^{+6.2}$ |
| *Green* | $0.38\pm0.01$ | $0.10\pm0.02$ | $0.68\pm0.13$ | $0.18\pm0.03$ | 56$_{-9}^{+11}$ | 7.0$_{-4.7}^{+12}$ | 56$_{-13}^{+19}$ | 13$_{-6}^{+17}$ | 5.3$_{-2.5}^{+7.8}$ |
| *Yellow* | $0.22\pm0.02$ | $0.06\pm0.01$ | $0.25\pm0.02$ | $0.07\pm0.02$ | 55$_{-12}^{+16}$ | 3.8$_{-1.1}^{+4.0}$ | 49$_{-10}^{+13}$ | 3.3$_{-1.2}^{+2.8}$ | 2.4$_{-0.5}^{+2.4}$ |
| *Red* | $0.15\pm0.02$ | $0.04\pm0.01$ |   $0.14\pm0.08$$^{a}$ | $0.06\pm0.01$ | 62$_{-21}^{+38}$ | 3.6$_{-2.2}^{+14}$ | – | – | 1.5$_{-0.7}^{+2.2}$ |

Table notes: Infrared luminosity, $L_{\rm IR}$, and SFR estimates are corrected for gravitational lensing.\

+:---------+:-------------------------:+:-------------------------:+:--------------------------:+:--------------------------:+:-------------------------:+:-------------------------:+:--------------------------:+:--------------------------:+:----------------------------------------------------:+:----------------------------------------------------:+
| Comp-    | $I^{\rm obs}_{\rm [CII]}$ | $I^{\rm mod}_{\rm [CII]}$ | $I^{\rm obs}_{\rm [OIII]}$ | $I^{\rm mod}_{\rm [OIII]}$ | $L^{\rm obs}_{\rm [CII]}$ | $L^{\rm mod}_{\rm [CII]}$ | $L^{\rm obs}_{\rm [OIII]}$ | $L^{\rm mod}_{\rm [OIII]}$ | $L^{\rm obs}_{\rm [OIII]}$/$L^{\rm obs}_{\rm [CII]}$ | $L^{\rm mod}_{\rm [OIII]}$/$L^{\rm mod}_{\rm [CII]}$ |
+----------+---------------------------+---------------------------+----------------------------+----------------------------+---------------------------+---------------------------+----------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+
| onent    | ------------------------------------------------------------------------                                        | ------------------------------------------------------------------------                                        |                                                      |                                                      |
|          |                                                                                                                 |                                                                                                                 |                                                      |                                                      |
|          | height 0.7ex depth -0.7ex \[Jy km s$^{-1}$\]                                                                    | height 0.7ex depth -0.7ex \[$10^8$ L$_\odot$\]                                                                  |                                                      |                                                      |
|          |                                                                                                                 |                                                                                                                 |                                                      |                                                      |
|          | ------------------------------------------------------------------------                                        | ------------------------------------------------------------------------                                        |                                                      |                                                      |
|          |                                                                                                                 |                                                                                                                 |                                                      |                                                      |
|          | height 0.7ex depth -0.7ex                                                                                       | height 0.7ex depth -0.7ex                                                                                       |                                                      |                                                      |
+----------+---------------------------+---------------------------+----------------------------+----------------------------+---------------------------+---------------------------+----------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+
| *Violet* | $0.068\pm0.0082$          | 0.044                     | $0.12\pm0.034$             | 0.13                       | $0.093\pm0.011$           | 0.059                     | $0.30\pm0.083$             | 0.31                       | $3.2\pm 0.97$                                        | $5.2\pm  1.7$                                        |
+----------+---------------------------+---------------------------+----------------------------+----------------------------+---------------------------+---------------------------+----------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+
| *Blue*   | $1.5\pm0.043$             | 1.5                       | $1.7\pm 0.11$              | 1.7                        | $2.1\pm0.058$             | 2.1                       | $4.1\pm 0.26$              | 4.1                        | $1.9\pm 0.13$                                        | $2\pm 0.14$                                          |
+----------+---------------------------+---------------------------+----------------------------+----------------------------+---------------------------+---------------------------+----------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+
| *Green*  | $0.95\pm0.032$            | 1.0                       | $2.1\pm  0.1$              | 2.2                        | $1.3\pm0.043$             | 1.4                       | $5.2\pm 0.24$              | 5.4                        | $4.0\pm 0.23$                                        | $4.0\pm 0.22$                                        |
+----------+---------------------------+---------------------------+----------------------------+----------------------------+---------------------------+---------------------------+----------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+
| *Yellow* | $0.13\pm0.0096$           | 0.11                      | $0.17\pm0.035$             | 0.15                       | $0.18\pm0.013$            | 0.15                      | $0.41\pm0.084$             | 0.36                       | $2.3\pm 0.49$                                        | $2.4\pm 0.59$                                        |
+----------+---------------------------+---------------------------+----------------------------+----------------------------+---------------------------+---------------------------+----------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+
| *Red*    | $0.66\pm0.024$            | 0.66                      | $1.0\pm0.077$              | 0.95                       | $0.90\pm0.033$            | 0.90                      | $2.4\pm 0.19$              | 2.3                        | $2.7\pm 0.23$                                        | $2.6\pm 0.23$                                        |
+----------+---------------------------+---------------------------+----------------------------+----------------------------+---------------------------+---------------------------+----------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+

Table notes: Line luminosities are corrected for lensing magnification.

## Disentangling the dust continuum

![](cont_decompose_v1.pdf)

We also estimated the flux densities of the continuum emission in band 6 and band 8 for each component. We first performed a forced-aperture photometry. Given that \[O iii\]$\,88\mu$m shows a better correlation than \[C ii\]$\,158\mu$m with the SFR (cite: delooze14; olsen17), we optimized spatial positions and shapes of the apertures following the five components of the \[O iii\] model. In the left panel of Figure [9](#fig:cont_model), we show the five aperture positions and shapes and summarize the extracted flux densities in Table [\[tab:dustcomponents\]](#tab:dustcomponents). In this approach, the apertures do not overlap with each other; however, we cannot rule out the possibility that some measurements within the aperture are affected by contributions from other components.

Next, we modeled and decomposed each contribution by using CASA imfit. From the observed morphology, we assumed four components. The violet (red) component was not included in the fitting for the band 6 (band 8) maps, but we extracted its photometry with a radius of $0.2\ensuremath{''}$ aperture on the residual map. We fixed the spatial positions of the faint components of red and violet when they are included in the model. We kept the flux density as a free parameter, while we fixed some of the other parameters (size, axis ratio, and PA) in a routine process to obtain stable results. In Table [\[tab:dustcomponents\]](#tab:dustcomponents), we summarize the flux density estimates in the both bands for each component. By assuming a single modified blackbody and a spectral index of $\beta=1.7$ in a spatially averaged manner (cite: akins22), we also derived the dust temperature ($T_{\rm dust}$) and IR luminosity ($L_{\rm IR}$). Due to the low S/N for the violet and red components, we derived their $L_{\rm IR}$ values by fixing their $T_{\rm dust}=41$ K taken from the spatially integrated best-fit value presented in (cite: akins22). These estimates are also listed in Table [\[tab:dustcomponents\]](#tab:dustcomponents). The sum of the five components gives $0.45\pm0.20$ mJy and $1.71\pm0.58$ mJy in bands 6 and 8, respectively. The band 8 continuum is comparable to the total flux estimate in Table [\[tab:OIIIcomponents\]](#tab:OIIIcomponents), while the band 6 continuum model underestimates the total flux by $\sim50\%$. This indicates that the diffuse continuum emission, significant in band 6 (cite: akins22), is not fully recovered by this decomposition analysis. The continuum model and residuals are shown in Fig. [9](#fig:cont_model). We note that we here use a higher resolution weighting scheme compared to (cite: akins22) and thus the difference is less evident in the residuals.

# Discussion

## Resolved and overall physical properties

Based on the component analysis from the previous subsections, we estimate the line luminosity and the continuum properties of each component. The line luminosity is estimated both using the observations and the model results. In Table [\[tab:resolved_linelum\]](#tab:resolved_linelum) we provide the line luminosity derived for each component. The uncertainty is estimated from the observed data, but does not include the uncertainty on the absolute flux calibration.

Based on our resolved line and continuum estimates, we can evaluate physical properties of the full source and the individual components. While blue and red are further decomposed into two subcomponents in Sect. [3.5](#subsect:linecontdecomp), here we focus on the physical properties of the brighter component that dominates their total emission.

### Total SFR

We calculated the total SFR by summing the obscured (SFR$_{\rm IR}$) and unobscured SFR (SFR$_{\rm UV}$) based on the ALMA and HST observations. We measured the UV luminosity $L_{\rm UV}$ for blue and green components with a $0.2\ensuremath{''}$-radius circular aperture placed at the peak positions of the two blobs observed in the HST maps. Because of the lack of the HST counterparts, we obtained a 3$\sigma$ upper limit with the same size aperture for the other components. We used the same conversions from IR and UV luminosity to SFR as (cite: akins22) based on the calibration presented in (cite: murphy11) and obtain a total SFR of $16.5_{-6.8}^{+22}\,M_{\odot}$ yr$^{-1}$. We did not account for the calibration uncertainty in the error estimate.

We confirm consistency with previous measurements (cite: bakx21; akins22) given the recovery fraction of the total dust continuum in our measurement (Sect. [4.1](#sec:decomp2)). We found that the obscured fraction $f_{\rm obs}$ is $\sim80$% in the blue and green components, respectively, and more than $\sim90$% in the other components, indicating the high obscuration in every part of the system. We summarize SFR$_{\rm IR}$, SFR$_{\rm UV}$, and $f_{\rm obs}$ for the individual components in Table [3](#tab:comp_dynamical_mass).

### SFR–$L_{\rm line}$ relation

In Fig. [10](#fig:linesfr) we show SFR–$L_{\rm [CII]}$ and SFR–$L_{\rm [OIII]}$ relations for the individual components and the entire system of A1689-zD1. We also show for comparison results obtained in local galaxies and $z>6$ galaxies without active galactic nuclei (AGNs) from the literature. For A1689-zD1, we find that the relation in both lines is consistent with previous results for $z>6$ galaxies, where the \[C ii\] line is slightly below the relation from local galaxies, but within its 1$\sigma$ range; whereas the \[O iii\] line agrees well with it. For individual components, we find that the relation has a little scatter, but still falls within the 1$\sigma$ range of the local galaxies. These results are consistent also with ALMA results for $z>6$ lensed galaxies (cite: knudsen16; fujimoto21; molyneux22).

Given that the emission is resolved, it is also natural to compare this to local galaxies. For example, the SHINING survey of nearby star-forming galaxies extensively studied FIR fine-structure lines and compared this to continuum properties (cite: herreracamus18). Comparing line luminosity to the FIR luminosity and the FIR surface brightness, $\Sigma_{\rm FIR}$, of A1689-zD1 to the results from the SHINING, we note that \[C ii\] results are within the scatter and consistent with that of SHINING results, while the \[O iii\] line appear about a factor two brighter than the brightest \[O iii\] detections in the SHINING survey.

In a compilation of $z=5-7$ galaxies with \[C ii\] detections, (cite: carniani18) find that "normal" star-forming galaxies deviate from the local empirical relation of $\Sigma_{\rm SFR}-\Sigma_{\rm [CII]}$ with a typically lower \[C ii\] surface brightness. Comparing the SFR-$L_{\rm [CII]}$ relation from the ALPINE survey (cite: schaerer20), assuming average extended emission of 8 kpc$^{2}$ (cite: posses25), it is positioned between the relation from (cite: carniani18) and the local relation from (cite: herreracamus15). Differences between the different populations (e.g., local vs. high-redshift galaxies) could be caused by heating mechanisms, effects of metallicity, or the ionization parameter (cite: carniani18). In Fig. [11](#fig:sigSFR_sigCII), we compare the resolved \[C ii\] emission of A1689-zD1 with those relations and with recent results of the two resolved high-$z$ galaxies REBELS-25 (cite: rowland24) and CRISTAL-05 (cite: posses25). For REBELS-25, we estimated $\Sigma_{\rm SFR}$ and $\Sigma_{\rm [CII]}$ assuming a 2D Gaussian distribution and the effective radius from (cite: rowland24) for estimating the area. For the A1689-zD1 components, we also assumed a 2D Gaussian distribution with the model FWHM from Table [\[tab:CIIcomponents\]](#tab:CIIcomponents). We note that the plotted errors do not include the uncertainties of the sizes. Given the large uncertainties on the SFR estimates, the individual components of A1689-zD1 are comparable to the high-redshift results of REBELS-25, CRISTAL-05, and the relation from ALPINE. The red component appears partly consistent with the local relation from (cite: herreracamus15), which could be indicative of a more efficient heating (cite: herreracamus15).

![image](Lcii_SFR-A1689zD1.png) ![image](Loiii_SFR_a1689zd1_v2.png)

### SFR–$L_{\rm [OIII]}/L_{\rm [CII]}$ relation

We also compared the line luminosity ratio of \[C ii\] and \[O iii\] to the SFR for $z>6$ galaxies, shown in Fig. [12](#fig:lineratio). While the estimates of the line ratios of the components span a range of a factor two, they are relatively consistent with the overall result for A1689-zD1. It has been found that $L_{\rm [OIII]}/L_{\rm [CII]}$ is typically above 2 for $z>6$ galaxies, however, this is based on a relatively small number of sources so far (cite: harikane20; Carniani2020). High $L_{\rm [OIII]}/L_{\rm [CII]}$ ratios have also been found in local low-metallicity dwarf galaxies (cite: cormier15). However for local luminous IR galaxies, the ratio tends to be $\leq 1$ (cite: howell10; diazsantos17).

Using a compilation of new data and literature results, (cite: harikane20) modeled the line ratios. They use simple photoionization models and discuss how several different physical effects impact the ratio; for example, the metallicity, ionization parameter, gas density, C/O ratio, and cosmic microwave background (CMB) attenuation. They find different properties can explain this, in particular very high ionization parameters or low photo-dissociation region coverage. Extensive modeling using cosmological radiation-hydrodynamics simulation have been published by (cite: katz22). Those simulations show that several effects, such as ionization parameter, CMB attenuation, and the ISM gas density, can play a significant role; however, in order to reproduce the observed results, the C/O abundance need to be lower than the solar value (cite: bakx24).

Comparing to the line ratios of the SHINING survey for local star-forming galaxies (cite: herreracamus18), we note that the \[O iii\]-to-\[C ii\] luminosity ratio is about a factor two higher. Given the relatively well-sampled global spectral energy distribution (cite: bakx21), we estimate the continuum ratio $S_{\rm 63\mu m}/S_{\rm 122\mu m} \sim 1.2-1.7$. In the SHINING sample, the sources with $S_{\rm 63\mu m}/S_{\rm 122\mu m} > 1$ are typically also the sources with $L_{\rm [OIII]}/L_{\rm [CII]} > 1$; however, we note that SHINING only has few sources with such high line ratios.

![](SigmaSFR_SigmaCII.pdf)

![](LoiiiLcii_sfr_all_v2.pdf)

### Size-velocity relation

In Fig. [13](#fig:vel_radius) we also compare the relation between size and velocity dispersion of the individual components with other spatially-resolved measurements from local to high-redshift galaxies. For size, we adopted the effective radius for the comparison, assuming for the Gaussian profiles that the half-width-at-half-maximum is comparable with the effective radius. By assuming virialized clouds in the same manner as (cite: spilker22), we also calculated the expected size and velocity dispersion at given mass surface density (illustrated by the dotted lines in Fig. [13](#fig:vel_radius)).

We find that the individual components are different from the distribution of the clumps observed in the local galaxies, but fall between the parameter spaces observed in the high-redshift, lensed, star-forming galaxies of the “Cosmic Snake” at $z=1.036$ (cite: dessauges19) and SPT 0311$-$58 at $z=6.900$ (cite: spilker22). The distribution of the individual components are aligned with the dotted line, showing that their mass surface densities are comparable with those of the star-forming clumps observed in the other high-redshift lensed galaxies. This might indicate that the internal star-forming mechanisms resemble each other, even though there is a large difference in the total SFRs of these high-redshift lensed galaxies, from a few tens to thousands of solar masses per year.

![](velocity_radius-crop.pdf)

### Kinematics

To analyze the kinematics of each component, we created a fiducial 3D data cube for each component by subtracting the 3D models of the other components (Sect. [3.5](#subsect:linecontdecomp)) and produced moment-0 and moment-1 maps. In Fig. [14](#fig:components_imm01), we show the moment-0 and moment-1 maps of both the \[C ii\] and \[O iii\] lines for each component. The moment-0 maps are shown in terms of their S/N, with the rms indicated in the figure caption. Two versions of the moment-1 are displayed: one showing the velocity relative to the overall galaxy ($z=7.133$) and one with zero velocity centered in the component.

We find in the \[C ii\] moment-1 map that blue component shows a symmetric velocity structure, from blueshifted in NE to redshifted in SW around its intensity peak. Apart from the blue component, we do not find clear velocity gradients in the moment-1 maps of any other component in the \[C ii\] or \[O iii\]. We thus regarded blue as a potential rotator and the other components as dispersion-dominated systems. We note, however, that blue does not show a similar velocity gradient in the \[O iii\] moment-1 map. As discussed in (cite: rizzo21), this may be explained by the difference in the motions between ionized and cold neutral gases, where the ionized gas is more likely tracing turbulent motions affected by stellar feedback for example, although the rotation has been seen in \[O iii\] at $z \sim 9$ (cite: tokuoka22). In fact, (cite: akins22) report different line profiles between \[C ii\] and \[O iii\] at the highest SFR surface density region, mostly corresponding to green, which may be explained by the outflow of the ionized gas.

![image](a1689zd1-cp_sources_imm01.png) ![image](a1689zd1-o3_sources_imm01.png)

### Dynamical masses

We also estimated the dynamical masses, $M_{\rm dyn}$, of the individual components. For blue, we assumed a disk-like gas distribution, given the potential rotation (Sect. [4.1.5](#sec:kin)), and followed Equation 4 in (cite: dessauges20): $$\begin{eqnarray}
\left (\frac{M_{\rm dyn}}{M_{\odot}} \right) &=& 1.16\times10^{5} \left(\frac{v_{\rm circ}}{\rm km\,s^{-1}}\right)^{2} \left(\frac{2r_{\rm e}}{\rm kpc} \right),  
\end{eqnarray}$$ where $r_{\rm e}$ is the effective radius, $v_{\rm circ}$ is the circular velocity of the gaseous disk, including the inclination correction, given by $v_{\rm circ}=1.763\sigma_{0}/{\rm sin}(i)$ and $i={\rm cos^{-1}({\rm FWHM_{2}/FWHM_{1}})}$.

For the other components, we assume dispersion-dominated systems and virialized bodies, following Equation 10 of (cite: bothwell13), as $$\begin{eqnarray}
\left (\frac{M_{\rm dyn}}{M_{\odot}} \right) &=& 1.56\times10^{6} \left(\frac{\sigma_{\rm 0}}{\rm km\,s^{-1}}\right)^{2} \left(\frac{r_{\rm e}}{\rm kpc} \right) , 
\end{eqnarray}$$ where $\sigma$ is the line-of-sight velocity dispersion and $r_e$ is the effect radius of the sources as described from the fitting above, and thus giving the dynamical mass within the effective radius. Because the \[C ii\] and \[O iii\] lines could trace different gas motions and regions, we estimated two $M_{\rm dyn}$ values for each component separately — \[C ii\]($M_{\rm dyn, [CII]}$) and \[O iii\] ($M_{\rm dyn, [OIII}$). We note that given the complicated morphology and kinematics of the system, each component might not be virialized. Nonetheless, the estimates provide a meaningful estimate of the dynamical mass. We summarize the various estimates of $M_{\rm dyn}$ in Table [3](#tab:comp_dynamical_mass).

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Comp- | SFR$_{\rm IR}$ | SFR$_{\rm UV}$ | $f_{\rm obs}$ | ${
        \rm M}_{\rm dyn, [OIII]}$ | ${\rm M}_{\rm dyn, [CII]}$ |
| onent | \[M$_\odot$ yr$^{-1}$\] | \[M$_\odot$ yr$^{-1}$\] | \[%\] | \[10$^{9}$M$_\odot$\] | \[10$^{9}$M$_\odot$\] |
|  |  |  |  |  |  |
| *Violet* | 1.2$_{-0.6}^{+2.0}$ | $<0.2$ | $> 86$ | 0.5 | – |
| *Blue* | 5.4$_{-2.3}^{+6.7}$ | 1.7 $\pm$ 0.1 | 76 | 5.9 | 5.7 |
| *Green* | 5.7$_{-2.7}^{+8.4}$ | 1.7 $\pm$ 0.1 | 77 | 4.3 | 6.0 |
| *Yellow* | 2.6$_{-0.5}^{+2.5}$ | $<0.2$ | $> 93$ | – | – |
| *Red* | 1.6$_{-0.7}^{+2.4}$ | $<0.2$ | $> 89$ | 1.8 | 2.9 |
|  |  |  |  |  |  |
| Sum | 16.5$_{-3.7}^{+11.4}$ | 3.4 $\pm$ 0.1 | 83 | 12.5 | 14.6 |

: Intrinsic physical properties for the different components.

## Mass of A1689-zD1

While A1689-zD1 was originally discussed as a modest, star-forming galaxy (cite: bradley08; watson15), there are now several lines of evidence that indicate the galaxy is much larger and more massive than the stellar and gas mass derived from the continuum emission. The 12 kpc extent of the \[C ii\] emission (cite: akins22) as well as the increased IR SFR (cite: bakx21; akins22) point to a bigger system. Furthermore, the dynamical mass estimates of the clumps (Sect. [3](#tab:comp_dynamical_mass)) indicate that the galaxy may be much more massive than originally believed, with a summed dynamical mass about $1.5\times10^{10}\,M_\odot$. This is an order of magnitude larger than the estimated stellar mass based on SED modeling including *Spitzer*-IRAC $3.6\,\mu$m and $4.5\,\mu$m detections. This implies an unfeasible high gas mass fraction given the approximately solar metallicity inferred from the FIR emission line ratios (cite: killi23). The total metal mass of the galaxy would then exceed what could be produced the core collapse supernovae in a Chabrier initial mass function. On this basis, the gas mass fraction of this large dynamical mass is unlikely to be more than about 50%. There is certainly sufficient dust in the galaxy: a screen of half the estimated dust mass in A1689-zD1 distributed uniformly across 2 kpc$^2$ would result in an $A_V\sim40$ mag using the Milky Way dust extinction to column density ratio (cite: watson2011). Since the star-formation obscuration fraction is about 90% (cite: akins22), the stellar mass is unlikely to be underestimated by more than this, namely, by more than an order of magnitude. The stellar mass is therefore likely to be about 1–2$\times10^{10}\,M_\odot$. These issues are discussed in greater depth in (cite: killi23).

## Considering the physical origin of A1689-zD1

The complex gas structure and kinematics of A1689-zD1 revealed by the ALMA observations are different and exhibit a higher degree of irregularity compared to other $z>7$ galaxies, where the multiplicity is often characterized by two or three \[C ii\] components (cite: matthee17; carniani17; hashimoto19), with separations on scales of 2–7 kpc. Other observations show either \[C ii\] that is separated from other components (e.g., \[O iii\]) and extended (cite: maiolino15; marrone18). Single-components at scales of about 3 kpc with some degree of rotation have also been claimed in UV-bright galaxies at $z>6.5$ (cite: smit18; tokuoka22). Other \[C ii\] detections either do not have sufficient S/N or angular resolution to resolve the emission (cite: knudsen16; bradac17; pentericci16).

Many recent results for galaxies at $z>4$, particularly from ALMA observations, show very clear velocity gradients (cite: jones17; smit18; neeleman20; tokuoka22; rowland24; posses25). In many cases, the observed velocity gradients are interpreted as gas rotation and, in some cases, this can also be aptly described by rotational models (cite: carniani13; litke19; jones21; rizzo21). These results are based both on non-lensed sources and gravitationally lensed galaxies and also across a range of different luminosities and masses. Certainly, the same system can change appearance due simply to inclination angle or evolution over a relatively short time. Only a few hundred million years separating $z=7$ from $z=5-6$ would be sufficient for a system to change from disk rotation to merger-dominated, according to the simulations of (cite: kohandel19).

It is worth noting that our angular resolution is about 5-20 times better than galaxies studied by (cite: smit18) and (cite: matthee17) due to the observational setup and the gravitational lensing magnification, which allows us to clearly rule out a simple ordered rotation for A1689-zD1. While a somewhat lower resolution would likely be sufficient to demonstrate that A1689-zD1 is not fully explained based on simple rotation, the sensitivity of data we have here, combined with a factor $\sim$9.6 in gravitational magnification reveal structures that are rarely detected in galaxies at high redshifts. Our conclusion here is somewhat at odds with (cite: Wong2022), who argued for a clear velocity SE-NW across the galaxy, with the NW being more dust-obscured. However, the presence of the violet component co-spatial with the redder part of the galaxy complicates a simple merger picture, as does the possible rotation and extent of the blue component. The results for the lensed galaxy SPT 0311$-$58 at $z=6.9$ observed with ALMA, has a comparable S/N and sub-kiloparsec resolution and also displays a clumpy structure (cite: spilker22). This suggests that a high S/N combined with spatial resolution significantly below the kpc scale may be important in fully exploring the dynamical state of at least some $z>6$ galaxies.

### An early galaxy assembly possibly consisting of five small clumps

One possible interpretation of the detection of several components within projected distances of $\sim3$ kpc and the detection of extended \[C ii\] emission is that we are witnessing the early assembly of the inner kiloparsec-scale region of a galaxy. In such a scenario each of the components would represent ISM/mass substructure, possibly as (super)giant molecular clouds or young stellar clusters in the assembly of the bulge region. Given the large relative offsets and velocities, the ordered motion seen in disk galaxies would not have been established thus far. The extended \[C ii\] detection (cite: akins22), would either be halo gas or possibly part of extended ISM, part of a bound system. If this was the case, we might expect an extended stellar component following the structure of the extended \[C ii\], which could be detectable with JWST. As argued above, the stellar mass may be much larger than indicated by the *Spitzer* observations. However, simulations of early galaxies suggest that they are unlikely to have effective radii larger than 2–3 kpc (cite: roper22), indicating that such an extended galaxy interpretation is less favored. This suggests that if A1689-zD1 has a large obscured stellar mass, it is most likely concentrated in the inner few kiloparsecs.

### Galaxy merger interpretation

The blue, green, and red components dominate the galaxy’s emission. As discussed above (and essentially indicated by (cite: Wong2022)), it is possible that the blue and green components could be associated with the two rest-frame UV components detected with HST. Given the velocity difference of 80 km s$^{-1}$ and projected physical separation of 0.8–1.4 kpc between these two (the range is given by the slightly different positions in the \[C ii\] and \[O iii\] data), one interpretation could be interaction and merger. The red component shows an extended tail-like structure, which could suggest that this is an additional component being pulled towards the green and blue, while the elongated structure represents a tidal tail of the gas. The red component is separated by 0.7–1 kpc in projection and 220 km s$^{-1}$ from the blue component and by 1.8-2.1 kpc in projection and 140 km s$^{-1}$ from the green. This could suggest a scenario of a merger event between green and blue, with red being a gas-rich structure or a scenario of a triple-merger, where the red component contains a more dust-obscured stellar population and a tidal disruption of the gas distribution. The sizes and distribution could be consistent with the ‘merger’ phase observed in the simulations of (cite: kohandel19). However, without the spatial information from the radial direction, such merger scenarios are difficult to constrain.

### Combined scenario

In the two subsections above, we describe the assembly of the inner few kiloparsecs of a galaxy or a merger scenario of two or three galaxies. A third plausible interpretation could be a combination of the two. Given the complex, almost chaotic structure, blue, green, and yellow appear to align in one direction and could represent the inner region of a galaxy, while red and violet could comprise more galaxy components that are interacting and possibly being accreted onto the main galaxy structure. The much higher dust obscuration of these NW components may support such a scenario.

Even though the ALMA data is of exceptional quality and reveals substructure so far unmatched in high-$z$ galaxies, two pieces of information are missing: the radial spatial distribution, which cannot be measured, and the distribution of the stellar mass. This latter may well be obtained through deep observations with JWST. Zoom-in numerical simulations are necessary to provide additional constraints, similar to those of (cite: kohandel19).

## Different star-formation indicators in the galaxy

With an ionization potential of 35 eV, double ionized oxygen is typically seen in only in Hii regions of young massive stars (or near AGNs), so the \[O iii\] 88 $\mu$m line traces ionized gas (H II regions) and is vastly less dust extinguished than optical or UV tracers (e.g., \[O iii\] 5007Å). Thus, it should serve as an excellent tracer of recent star-formation. The first ionization potential of carbon is only 11.26 eV, below atomic hydrogen and well below that of double ionized oxygen, but just above the lowest Lyman-Werner band energy of 11.15 eV required to two-step photo-dissociate molecular hydrogen. Furthermore, C$^+$ is thus both found in the ionized and neutral gas phases. Recent work using absorption spectroscopy suggests that \[C ii\] can be used to trace the neutral atomic gas component when metallicity is accounted for (cite: madden20; heintz21). The lines of \[C ii\] and \[O iii\] can thus be used to trace different parts of the gas associated with the star-forming regions and the diffuse ISM. At $z>6,$ a few detections of both lines have been obtained (cite: inoue16; laporte17; carniani17; hashimoto18; hashimoto19; tamura19; laporte19; harikane20), revealing a large scatter in the ratios. While it is not possible with these data alone to estimate the density and metallicity of the gas, with sufficient additional data, such estimates may be made from ISM models (cite: killi23).

|     |     |     |
|:----|:----|:----|
|     |     |     |
|     |     |     |
|     |     |     |

To compare the projected UV emission with the FIR emission in detail, we plot in Fig. [15](#fig:ratio_plots) ratio maps of the \[O iii\], \[C ii\] lines, as well as the continua near these lines, and the combined UV emission from the sum of the F125W, F140W, and F160W HST filter images. This gives us nine ratio maps showing the resolved, normalized line ratios across the galaxy.

Three star-forming tracers are present: the \[O iii\] line, the UV continuum, and the dust continuum emission. The UV continuum is susceptible to dust extinction. However, the tracers also have different overall lifetimes, with the \[O iii\] emission being the most immediate, requiring 35 eV photons to ionize the gas, while the UV emission is longer lived, and the dust heating even longer. The most notable feature of these ratio maps is that the UV emission comes only from the eastern side of the galaxy, while the dust and FIR line emission is much more extended, revealing an entire half of the galaxy to the west that has no detectable UV emission. Secondly, the \[C ii\] emission also clearly comes from a much more extended area than the other FIR emission, a point explored in more detail in (cite: akins22). As noted above, the dusty, FIR-dominated side of the galaxy seems to correspond to the red and yellow velocity components in the emission line data. The yellow component is particularly unusual in that it is dust-continuum dominated; namely, the dust continuum dominates over all other emission components, including \[C ii\]. This component, however, is mixed in $88\,\mu$m and $158\,\mu$m continuum emission, indicating that it is not clearly colder or warmer, for example, than the dust in the rest of the galaxy. It does, however, also have relatively weak \[O iii\] emission. At first glance, this could suggest that the oldest star-forming population in the galaxy does in fact reside here.

While we have argued that the two major components observed in the HST data seem to correspond primarily to the blue and green components identified from the ALMA line emission, it is not a precise match and suggests a greater complexity than what can be resolved with the current data (see Fig. [7](#fig:cii_HST)). The central green component emits strongly in all four tracers, suggesting a young star-forming knot, while the blue component appears to be more UV dominated, suggesting that this component is somewhat older and is least dust-rich at its northern-most extent.

Finally, the comparison with the high-resolution data of (cite: spilker22) and (cite: dessauges19) show that A1689-zD1 has a very high mass surface density. We have argued that the majority of the inferred mass in these surface densities must be stellar mass rather than gas mass, so these results are not quite comparable. However, we expect that a significant fraction of the mass is made up of gas. The high surface density and the range of clump sizes, from unresolved to nearly kiloparsec scale, indicate that A1689-zD1 has some aspects in common with the most massive star-forming galaxies at high-$z$. None of our data so far show any indication of AGN activity in the galaxy (cite: Wong2022).

# Conclusions

We present GBT band Q and ALMA band 3, 6, and 8 observations of the gravitationally lensed, epoch of reionization galaxy, A1689-zD1. The deep ALMA observations combined with the large gravitational magnification, provides some of the deepest high angular resolution data for a $z>7$ galaxy to date, enabling us to resolve the ISM kinematics down to scales of 200pc.

- Two emission lines have been detected and identified as \[C ii\]$\,158\mu$m and \[O iii\]$\,88\mu$m, consistent with a redshift of $z=7.1332\pm0.0005$. The spectroscopic redshift is offset by about 13 000$\pm7,000$ km s$^{-1}$ from the continuum break identified in previous X-shooter data.

- The line luminosities are $L_{\rm [CII]} = (5.8 \pm 0.1)\times10^{8}$ L$_\odot$ and $L_{\rm [OIII]} = (1.3 \pm 0.02)\times10^{9}$ L$_\odot$ after correcting for gravitational magnification. The line luminosities relative to the SFR are consistent with Local Universe galaxies, suggesting the ISM excitation conditions are normal.

- The galaxy system is complex with at least five individual components. Based on iterative modeling we estimate the structure and kinematical properties of each component. The components appear to be interacting, hinting at a galaxy in its early assembly. The complex kinematics and morphology do not show signs of a single rotating disk. The complexity is in agreement with predictions of early galaxy assembly from recent numerical zoom-in simulations.

- Several components of the galaxy are entirely obscured in the rest-frame UV and might also be similarly obscured in the optical. This could significantly affect the stellar mass estimate, indicating that A1689-zD1 might be significantly more massive than previously believed. Deep rest-frame NIR observations are the most direct route to resolving this question.

Overall, A1689-zD1 still appears to be something of a mystery, with kinematics and gas surface densities that indicate it is in the process of assembly, but the dust and stellar properties argue for a much older system, with major discrepancies between its dynamical and stellar masses and between its Ly$\alpha$ break and FIR line redshifts, along with a small, compact core, especially in the UV emission; in addition, there is the vast \[C ii\], and to a lesser extent, dust halo to consider. JWST is certain to resolve at least some of these issues and discrepancies.

The resolved \[C ii\] and \[O iii\] kinematics imply a more complex diversity among $z>6$ galaxies. High-angular-resolution observations of other similar galaxies are needed to improve our understanding of early assembly and fully characterize the early evolutionary stages of normal galaxies.

# Acknowledgements

We thank the anonymous referee for their helpful comments and suggestions. We acknowledge support from the Nordic ALMA Regional Centre (ARC) node based at Onsala Space Observatory. The Nordic ARC node is funded through Swedish Research Council grant No 2019-00208. We thank the Nordic ARC node staff for very helpful discussions. KK acknowledges support from the Swedish Research Council (2015-05580) and the Knut and Alice Wallenberg Foundation (KAW 2017.0292). DW, SF, and NB are supported in part by Independent Research Fund Denmark grant DFF-7014-00017. The Cosmic Dawn Center is funded by the Danish National Research Foundation under grant number 140. TB acknowledges support from the Knut and Alice Wallenberg Foundation (KAW 2020.0081). A.K.I. is supported by NAOJ ALMA Scientific Research grant No.2020-16B. MJM acknowledges the support of the National Science Centre, Poland through the SONATA BIS grant 2018/30/E/ST9/00208. This research was funded in part by the National Science Centre, Poland, grant number 2023/49/B/ST9/00066. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01406.S and 2017.1.00775.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

92 natexlab

(ref: akins22) Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64

(ref: algera24) Algera, H. S. B., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 6867

(ref: bakx24) Bakx, T. J. L. C., Algera, H. S. B., Venemans, B., et al. 2024, MNRAS, 532, 2270

(ref: bakx21) Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021, MNRAS, 508, L58

(ref: bakx20) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294

(ref: binggeli20) Binggeli, C., Inoue, A. K., Hashimoto, T., et al. 2021, A&A, 646, A26

(ref: Bolatto2008) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, in Low-Metallicity Star Formation: From the First Stars to Dwarf Galaxies, ed. L. K. Hunt, S. C. Madden, & R. Schneider, Vol. 255, 274–277

(ref: bothwell13) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047

(ref: bouwens22a) Bouwens, R. J., Illingworth, G., Ellis, R. S., Oesch, P., & Stefanon, M. 2022a, ApJ, 940, 55

(ref: bouwens22b) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022b, ApJ, 931, 160

(ref: bradac17) Bradač, M., Garcia-Appadoo, D., Huang, K.-H., et al. 2017, ApJL, 836, L2

(ref: bradley08) Bradley, L. D., Bouwens, R. J., Ford, H. C., et al. 2008, ApJ, 678, 647

(ref: bunker23) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, A&A, 677, A88

(ref: capak15) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455

(ref: Carniani2020) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136

(ref: carniani18) Carniani, S., Maiolino, R., Amorin, R., et al. 2018, MNRAS, 478, 1170

(ref: carniani17) Carniani, S., Maiolino, R., Pallottini, A., et al. 2017, A&A, 605, A42

(ref: carniani13) Carniani, S., Marconi, A., Biggs, A., et al. 2013, A&A, 559, A29

(ref: cormier15) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, A&A, 578, A53

(ref: delooze14) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: dessauges20) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5

(ref: dessauges19) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2019, Nature Astronomy, 3, 1115

(ref: diazsantos17) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32

(ref: ferrara22) Ferrara, A., Sommovigo, L., Dayal, P., et al. 2022, MNRAS, 512, 58

(ref: finkelstein23) Finkelstein, S. L., Bagley, M. B., Ferguson, H. C., et al. 2023, ApJL, 946, L13

(ref: finkelstein15) Finkelstein, S. L., Ryan, Russell E., J., Papovich, C., et al. 2015, ApJ, 810, 71

(ref: fudamoto21) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489

(ref: fujimoto2022) Fujimoto, S., Brammer, G. B., Watson, D., et al. 2022, Nature, 604, 261

(ref: fujimoto21) Fujimoto, S., Oguri, M., Brammer, G., et al. 2021, ApJ, 911, 99

(ref: gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: gullberg18) Gullberg, B., Swinbank, A. M., Smail, I., et al. 2018, ApJ, 859, 12

(ref: harikane20) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93

(ref: hashimoto19) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71

(ref: hashimoto23) Hashimoto, T., Inoue, A. K., Sugahara, Y., et al. 2023, ApJ, 952, 48

(ref: hashimoto18) Hashimoto, T., Laporte, N., Mawatari, K., et al. 2018, Nature, 557, 392

(ref: heintz21) Heintz, K. E., Watson, D., Oesch, P. A., Narayanan, D., & Madden, S. C. 2021, ApJ, 922, 147

(ref: herreracamus15) Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1

(ref: herreracamus18) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 94

(ref: Heyer2009) Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, ApJ, 699, 1092

(ref: hoag18) Hoag, A., Bradač, M., Brammer, G., et al. 2018, ApJ, 854, 39

(ref: howell10) Howell, J. H., Armus, L., Mazzarella, J. M., et al. 2010, ApJ, 715, 572

(ref: hutter21) Hutter, A., Dayal, P., Yepes, G., et al. 2021, MNRAS, 503, 3698

(ref: inoue20) Inoue, A. K., Hashimoto, T., Chihara, H., & Koike, C. 2020, MNRAS, 495, 1577

(ref: inoue16) Inoue, A. K., Tamura, Y., Matsuo, H., et al. 2016, Science, 352, 1559

(ref: jolly21) Jolly, J.-B., Knudsen, K., Laporte, N., et al. 2021, A&A, 652, A128

(ref: jones17) Jones, G. C., Carilli, C. L., Shao, Y., et al. 2017, ApJ, 850, 180

(ref: jones21) Jones, G. C., Vergani, D., Romano, M., et al. 2021, MNRAS, 507, 3540

(ref: jullo07) Jullo, E., Kneib, J.-P., Limousin, M., et al. 2007, New Journal of Physics, 9, 447

(ref: katz22) Katz, H., Rosdahl, J., Kimm, T., et al. 2022, MNRAS, 510, 5603

(ref: killi23) Killi, M., Watson, D., Fujimoto, S., et al. 2023, MNRAS

(ref: knudsen16) Knudsen, K. K., Richard, J., Kneib, J.-P., et al. 2016, MNRAS, 462, L6

(ref: knudsen17) Knudsen, K. K., Watson, D., Frayer, D., et al. 2017, MNRAS, 466, 138

(ref: kohandel19) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2019, MNRAS, 487, 3007

(ref: kokorev22) Kokorev, V., Brammer, G., Fujimoto, S., et al. 2022, ApJS, 263, 38

(ref: laporte17) Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJL, 837, L21

(ref: laporte19) Laporte, N., Katz, H., Ellis, R. S., et al. 2019, MNRAS, 487, L81

(ref: laporte21) Laporte, N., Zitrin, A., Ellis, R. S., et al. 2021, MNRAS, 505, 4838

(ref: Xue) Li, X., Hjorth, J., & Richard, J. 2012, JCAP, 2012, 015

(ref: limousin07) Limousin, M., Richard, J., Jullo, E., et al. 2007, ApJ, 668, 643

(ref: litke19) Litke, K. C., Marrone, D. P., Spilker, J. S., et al. 2019, ApJ, 870, 80

(ref: madden20) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141

(ref: maiolino15) Maiolino, R., Carniani, S., Fontana, A., et al. 2015, MNRAS, 452, 54

(ref: marrone18) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51

(ref: matthee17) Matthee, J., Sobral, D., Boone, F., et al. 2017, ApJ, 851, 145

(ref: mclure13) McLure, R. J., Dunlop, J. S., Bowler, R. A. A., et al. 2013, MNRAS, 432, 2696

(ref: molyneux22) Molyneux, S. J., Smit, R., Schaerer, D., et al. 2022, MNRAS, 512, 535

(ref: murphy11) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: neeleman20) Neeleman, M., Prochaska, J. X., Kanekar, N., & Rafelski, M. 2020, Nature, 581, 269

(ref: oesch18) Oesch, P. A., Bouwens, R. J., Illingworth, G. D., Labbé, I., & Stefanon, M. 2018, ApJ, 855, 105

(ref: oesch16) Oesch, P. A., Brammer, G., van Dokkum, P. G., et al. 2016, ApJ, 819, 129

(ref: olsen17) Olsen, K., Greve, T. R., Narayanan, D., et al. 2017, ApJ, 846, 105

(ref: pentericci16) Pentericci, L., Carniani, S., Castellano, M., et al. 2016, ApJL, 829, L11

(ref: perley17) Perley, R. A. & Butler, B. J. 2017, ApJS, 230, 7

(ref: planck15) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13

(ref: posses25) Posses, A., Aravena, M., González-López, J., et al. 2024, arXiv e-prints, arXiv:2403.03379

(ref: rieke23) Rieke, M. J., Robertson, B., Tacchella, S., et al. 2023, ApJS, 269, 16

(ref: rizzo21) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952

(ref: roper22) Roper, W. J., Lovell, C. C., Vijayan, A. P., et al. 2022, MNRAS, 514, 1921

(ref: Rosolowsky2005) Rosolowsky, E. & Blitz, L. 2005, ApJ, 623, 826

(ref: rowland24) Rowland, L. E., Hodge, J., Bouwens, R., et al. 2024, MNRAS

(ref: schaerer20) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3

(ref: smit18) Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178

(ref: sommovigo22) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS

(ref: spilker22) Spilker, J. S., Hayward, C. C., Marrone, D. P., et al. 2022, ApJL, 929, L3

(ref: tamura19) Tamura, Y., Mawatari, K., Hashimoto, T., et al. 2019, ApJ, 874, 27

(ref: tokuoka22) Tokuoka, T., Inoue, A. K., Hashimoto, T., et al. 2022, ApJL, 933, L19

(ref: vallini15) Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36

(ref: walter18) Walter, F., Riechers, D., Novak, M., et al. 2018, ApJL, 869, L22

(ref: watson2011) Watson, D. 2011, A&A, 533, A16

(ref: watson15) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327

(ref: witstok22) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751

(ref: Wong2022) Wong, Y. H. V., Wang, P., Hashimoto, T., et al. 2022, ApJ, 929, 161

[^1]: E-mail: kirsten.knudsen@chalmers.se

[^2]: In line with the technical handbook: [https://almascience.eso.org/
    documents-and-tools/cycle10/alma-technical-handbook](https://almascience.eso.org/
    documents-and-tools/cycle10/alma-technical-handbook)

[^3]: The range in rms reflects the variation between different channels of the data cube.

[^4]: The Green Bank Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc.

</paper>

Write the methods card for this paper.