# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...699A..22M\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...699A..22M",
 "title": "An accreting dwarf star orbiting the S-type giant star π<SUP>1</SUP> Gru",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Montargès, M.",
 "n_authors": 23,
 "arxiv_id": "2504.16845",
 "doi": "10.1051/0004-6361/202452587",
 "alma_projects_linked_by_archive": [
  "2018.1.00659.L"
 ]
}
```

Paper text:
<paper>
# An accreting dwarf star orbiting the S-type giant star $\pi^1$ Gru

At the end of their lives, low- to intermediate-mass stars reach the asymptotic giant branch (AGB), during which their photospheres expand by up to several hundred times and strong stellar winds develop. These changes lead to various interactions with celestial bodies in their close circumstellar environments, including mass- and angular-momentum transfer.

We aim to characterize the properties of the inner companion of the S-type AGB star $\pi^1$ Gru and to identify plausible future evolutionary scenarios for this triple system.

We observed $\pi^1$ Gru with the Atacama Large Millimeter/sub-millimeter Array (ALMA) and the Spectro-Polarimetric High-contrast Exoplanet REsearch (SPHERE) instrument of the Very Large Telescope (VLT), collected archival photometric data, and used the HIPPARCOS-*Gaia* proper motion anomaly. We derived the best orbital parameters using Bayesian inference.

In June-July 2019, the inner companion, $\pi^1$ Gru C, was located at $37.4 \pm 2.0$ mas from the primary (a projected separation of $6.05 \pm 0.55$ au at $161.7 \pm 11.7$ pc). The best orbital solution yields a companion mass of $0.86^{+0.22}_{-0.20}$ M$_\odot$ (using the derived mass of the primary) and a semi-major axis of $7.05^{+0.54}_{-0.57}$ au, corresponding to an orbital period of $11.0^{+1.7}_{-1.5}$ yr. The preferred solution is an elliptical orbit with eccentricity $e = 0.35^{+0.18}_{-0.17}$, although a circular orbit cannot be fully excluded. The close companion could be either a K1V$^\mathrm{F9.5V}_\mathrm{K7V}$ star or a white dwarf (WD). Ultraviolet and millimeter continuum photometry are consistent with the presence of an accretion disk around the close companion. The ultraviolet emission may originate from hot spots in an overall cooler disk, or from a hot disk if the companion is a WD.

Although the close companion and the AGB star are interacting and an accretion disk is observed around the companion, the mass-accretion rate is too low to trigger a Type Ia supernova, but it could produce novæ every $\approx 900$ yr. Short-wavelength, spatially resolved observations are required to further constrain the nature of the C companion. Searches for close-in companions similar to this system will improve our understanding of the physics of mass and angular momentum transfer, as well as orbital evolution during late evolutionary stages.

# Introduction

As they near the end of their existence, low- to intermediate-mass stars, i.e., stars with zero-age main sequence (ZAMS) mass (M~ZAMS~) lower than 8 M$_\odot$ (where M$_\odot$ is the solar mass) enter the asymptotic giant branch (AGB) phase. During this cool, evolved stage, the star expands significantly–from a few solar radii (R$_\odot$) to more than 1 au ($\sim 200-400$ R$_\odot$)– and develops a slow (terminal wind velocities $v_\infty \approx 3 - 30$ km s$^{-1}$; ) but strong stellar wind ($10^{-8}$ to $10^{-4}$ M$_\odot$ yr$^{-1}$; e.g., ). This wind originates from the photosphere, where material is levitated by a combination of convection and pulsations. The enhanced density resulting from the dynamical motion of the surface layers allows dust grains to nucleate and grow. These grains subsequently drive and accelerate the wind through radiation pressure. Ultimately, such winds contribute significantly to the chemical enrichment of the Universe (see reviews by and ).

Early optical and infrared observations of AGB stars did not spatially resolve the close circumstellar environment. Even with the Infrared Space Observatory (ISO, ), had to rely on spectra to characterize the molecular envelopes around these stars. The first spatially resolved studies, using speckle-masking interferometry, revealed the absence of spherical symmetry; instead, the circumstellar environments of AGB stars are inhomogeneous (or “clumpy”) . Long-baseline interferometric measurements, beginning with the Infrared-Optical Telescope Array (IOTA, ) and the University of California Berkeley Infrared Spatial Interferometer (ISI, and ), revealed the spatial distribution of various molecules in the circumstellar environment. These pioneering facilities have been succeeded by the Very Large Telescope Interferometer (VLTI). Initial observations with a limited number of telescopes (thus, modest $u, v$ coverage) only permitted geometrical fitting of the interferometric observables (e.g., , , ). In recent decades, image reconstructions have become feasible, revealing a 3D structure of the circumstellar material around AGB stars that is more complex and irregular than previously anticipated (e.g., , ). In addition to these individual studies, the MID-infrared Interferometric instrument (MIDI) of the VLTI was used to conduct a systematic observation of dust around 14 AGB stars, as part of the *Herschel* Mass-loss of Evolved StarS (MESS) key program . This MIDI large program detected asymmetries in the dusty envelopes of five of the 14 AGB stars observed. At the same time, the Atacama Large Millimeter/sub-millimeter Array (ALMA) revealed asymmetries and complex structures in the gaseous component of the circumstellar environment (e.g., for R Scl by , and R Aqr by ).

Close binaries have long been suspected of shaping the circumstellar environment and to be responsible for the various shapes of planetary nebulæ (PNe; ). This hypothesis was further supported by the ATOMIUM large program , where concluded that the rich morphology of AGB wind shapes seems most readily explained by the interaction of the AGB outflow with a close companion. Indeed, tens of such close companions have been detected and characterized around post-AGB stars (e.g., and references therein). However, only a few have been confirmed around AGB stars, including Mira (), L$_2$ Puppis (), R Aqr ( and ), and V Hya (). The interaction between the wind outflow and the companion may be radiative or gravitational in nature (see observations of W Aql by , and simulations from ). It may also significantly impact the chemistry of the companion, potentially revealing the binary nature of the system even after the AGB star has transitioned toward a well-hidden WD .

Here we focus on the S-type star $\pi^1$ Gru (161 Gru; HR 8521; HD 212087; HIP 110478). It has a parallax of $6.19 \pm 0.45$ mas , corresponding to a distance of $161.7 \pm 11.7$ pc. In the following, we refer to the primary AGB star as $\pi^1$ Gru A. The surface of this star has been imaged by interferometry with VLTI/PIONIER observations , revealing its granulation in exquisite detail. The AGB primary is known to have a distant G0V companion ($\pi^1$ Gru B) at a projected separation of 2.8 arcsec, as reported by , , and . The companion has been designated Gaia EDR3 6518817665842868352 in . first mapped the CO $J=1-0$ and $2-1$ emission toward $\pi^1$ Gru using the 15-m Swedish-ESI-Submillimeter Telescope (SEST) and discovered the presence of a high-velocity bipolar outflow. He argued that $\pi^1$ Gru B is too distant from $\pi^1$ Gru A to cause significant interaction, and therefore is unlikely to be the origin of this outflow. mapped the high-velocity outflow in CO emission with the Submillimeter Array (SMA) at higher angular resolution and suggested that it may result from interactions of the AGB wind with a second, closer companion, which may be responsible for shaping the inner AGB outflow. reinforced this hypothesis by observing asymmetries in molecular and dust shells with VLTI/MIDI. For a 2 M$_\odot$ AGB primary, they proposed a separation between 20.8 and 74.4 mas (3.2 to 11.4 au). Using a combination of *Herschel*/PACS, VLTI/AMBER, and HIPPARCOS observations, proposed an orbital solution covering an arc of the full orbit. The position of this second companion to $\pi^1$ Gru has been directly imaged by ALMA . suggest that $\pi^1$ Gru experienced a mass-loss eruption 100 years ago, for about 13 yr, ejecting $4.3 \times 10^{-5}$ M$_\odot$, the origin of which has yet to be explained. This would correspond to a mass-loss rate five times higher than before the eruption. They also provide constraints on the inner companion that should exhibit an orbital period of $\sim$ 330 yr, and a separation no greater than 70 au. An eccentricity as high as 0.8 may be required to explain the branching of the spiral arms observed in the $^{12}$CO $J=3-2$ emission line.

In this article, our objective is to determine the properties of this inner companion $\pi^1$ Gru C and its immediate ambient medium, as well as to identify possible scenarios for the future of the $\pi^{1}$ Gru system. The observations with VLT/SPHERE, ALMA and the archival photometry are presented in Sect. [2](#Sect:Obs). We perform data analysis in Sect. [3](#Sect:Data_Analysis). The companion characteristics and the future of the system are discussed in Sect. [4](#Sect:Discussion). Our concluding remarks are summarized in Sect. [5](#Sect:Conclusion).

# Observations and data reduction

## VLT/SPHERE ZIMPOL observations

SPHERE is the extreme adaptive optics instrument at the VLT operated by the European Southern Observatory (ESO). It is capable of observations in the visible and near-infrared domains. In this study, we used data obtained with the Zurich IMaging POLarimeter (ZIMPOL) subunit operating in the visible . The SPHERE adaptive optics system allows us to get close to the diffraction limit of 17 mas in the visible (V band). Several epochs of SPHERE observations of $\pi^1$ Gru have been obtained through various filters, each preceded or followed by a spatially unresolved star acting as a flux calibrator and estimator of the point spread function (PSF). These are summarized in Table [\[Tab:Log_SPHERE\]](#Tab:Log_SPHERE). The July 2019 data were acquired through the Target of Opportunity (ToO) program designed to observe the ATOMIUM sources during the ALMA long baseline campaign of 2019. The ZIMPOL data reduction procedure and a general overview of these data are presented in . The additional ZIMPOL datasets analyzed in this work were reduced (using esoreflex/SPHERE pipeline 0.45.1) and processed following the same procedure to ensure a homogeneous sample. Each observation provides four observables for each filter: the total intensity ($I$), the polarized flux ($P$), the degree of linear polarization (DoLP = $P/I$), and the polarization angle.

## ALMA observations

ALMA Band 6 data of $\pi^1$ Gru were obtained during the ATOMIUM large program observations. Details of the project, including the observations, data reduction, and calibration are presented in and . A summary of relevant parameters is provided in Table [2](#Tab:Log_ALMA) of this article. The ZIMPOL and ALMA extended-configuration observations are separated by at most 15 days, as was intended with the ToO request on VLT/SPHERE. This ensures that the data sets are contemporaneous with respect to the close circumstellar environment, given the pulsation period of $\pi^1$ Gru is $\sim 150$ days . This strategy provides comparable angular resolution across the spectrum at the same epoch.

## Archival optical photometry

We retrieved archival photometry from the VizieR service[^1], in an area of 5 arcsec around the $\pi^1$ Gru system. We manually removed obvious outliers, such as duplicated filter measurements that differed by orders of magnitude from values expected for an AGB star. Three short wavelengths (360, 450, and 550 nm) were retrieved using PySSED . The final photometry data are compiled in Table [3](#Tab:archive_photometry).

We also obtained time-series photometric observations of the $\pi^1$ Gru system from the American Association of Variable Star Observers (AAVSO[^2]).

## ISO spectra

$\pi^1$ Gru was observed by ISO in 1996. We retrieved the corresponding data from the ISO archive[^3].

# Data analysis

## Position of the companion from contemporaneous ALMA and VLT/SPHERE observations

Figure [1](#Fig:ALMA_cont_high) presents the ALMA continuum map in band 6, at an angular resolution of 25 mas. The noise level, derived as the standard deviation of the noise in the map, is $\sigma = 1.31 \times 10^{-5}$ Jy beam$^{-1}.$ Two sources were spatially resolved and detected at peak values of 736$\sigma$ and 112$\sigma$, respectively. We derived their characteristics using a 2D Gaussian fit. The position of the C companion, relative to $\pi^{1}$ Gru A, was (RA, Dec) = ($-12.3 \pm 0.1$, $-35.3 \pm 0.1$) mas. This corresponds to an apparent separation of $37.4 \pm 0.1 \pm 2.3$ mas, or a projected separation of $6.05 \pm 0.44 \pm 0.55$ au at $161.7 \pm 11.7$ pc. The first component of the uncertainty comes from the fitting process, while the second component comes from the signal-to-noise ratio (S/N). confirmed that the brightest component is the AGB star and the other is its suspected inner companion . The integrated flux density over a 3$\sigma$ area of the primary was $28.3 \pm 2.8$ mJy, and $3.3 \pm 0.3$ mJy for the secondary.

![](ALMA_cont_high)

Figure [2](#Fig:SPHERE_DoLP_companion) shows the degree of linear polarization (DoLP) of the ZIMPOL observations of $\pi^1$ Gru at each observation epoch, using one filter (images for all filters are shown in Fig. [11](#Fig:all_DoLP), and rms maps in Fig. [12](#Fig:all_DoLP_rms)). A tail is visible in the polarized signal, most prominently from July 2015 to July 2019, and appears to rotate around the primary AGB star. When the position of the companion from the ALMA continuum map of July 2019 is plotted onto the July 2019 ZIMPOL observation (Fig. [2](#Fig:SPHERE_DoLP_companion), third panel), the companion is slightly ahead of the tail, and closer to the star. We propose that this tail, which extends behind the companion and forms a spiral-like structure, results from the interaction with the stellar wind, concentrating dust and potentially accelerating its growth (similar to VLTI/MATISSE observations of V Hya; ). Dust is favored over gas in the polarized signal, as it is visible at multiple wavelengths . The variation in polarized signal strength over time can be explained by changes in the angle between Earth, the tail, and the primary along the orbit. showed that the polarized signal is best observed when dust is in the plane of the sky containing the light source.

![](SPHERE_dolp_companion)

## Dynamics and orbital characteristics of the system 

In addition to the above-described position astrometry analysis, we collect various indirect observations of the binary to constrain its orbital properties. They are described in the following sections.

### Constraints from the gas distribution observed with ALMA

By fitting the characteristics of the circumstellar wind from CO $J=3-2$ ALMA-ACA observations, demonstrated that the inclination of the inner gaseous torus is $40^\circ{}$. derived an inclination angle of $38 \pm 3^\circ{}$ using the CO ($J = 2 - 1$) higher angular resolution observations of the inner wind by the ALMA main array. In the following modeling, assuming co-planarity between the inner gaseous features and the orbital motion of the inner companion, we conservatively adopt an orbital inclination of $38 \pm 5 ^\circ{}$ with respect to the plane of the sky (with the southern part of the orbit toward Earth). We selected a broader confidence interval than that of to enable a wider exploration of the parameter space.

The moment 1 maps represent the mean velocity value on the line of sight at each pixel, relative to the star (assuming a local system of rest velocity for $\pi^1$ Gru of $v_\mathrm{LSR} = -12$ km s$^{-1}$; (cite: 2020A&A...644A..61H)), weighted by the brightness in each spectral channel. For the HCN $v = 0~J = 3 - 2$ and SiO $v = 0~J = 5 - 4$ emission lines (see Fig. 7 of and our Fig. [3](#Fig:PV_SiO)), the southeastern side appears blue-shifted, while the northwestern side is red-shifted. The 0 km s^-1^ line-of-sight velocity direction in these moment 1 maps corresponds to the direction where the gas motion is parallel to the plane of the sky. We assume that, near the inner companion, the bulk gas motion mainly follows the orbital motion due to the changing location of the primary star caused by its orbital motion (i.e., the radial outflow is negligible). The position-velocity (P-V) diagram for the SiO $v = 0$ $J=5-4$ line in the extended ALMA configuration is shown in Fig. [3](#Fig:PV_SiO). It demonstrates that the maximum projected velocity of the inner gas distribution follows a Keplerian velocity field, consistent with our hypothesis. In this scenario, the direction in which the gas and companion motions lie entirely within the plane of the sky is orthogonal to the orbital node direction. The orbital node direction corresponds to the intersection of the plane of the sky and the orbital plane. Orthogonal to this orbital node direction is the $X$ axis in Fig. [4](#Fig:system_sketch), where the line-of-sight velocity of the companion should therefore be 0 km s$^{-1}$ with respect to the primary. For HCN and SiO, found the direction of minimum line-of-sight velocity of the gas of $\sim 55^\circ{}$ and $\sim 50^\circ{}$ (position angle from north to east), respectively. We adopt the mean value of $52.5 \pm 5^\circ{}$ for the null radial velocity direction of the companion, and thus a longitude of the ascending node $\Omega = 322 \pm 5^\circ{}$. The uncertainty interval corresponds to the difference between the HCN and SiO derived values.

![](pv_diagram_SiO)

![image](pi1Gru_Deproj_asc_node_3D)\
![image](pi1Gru_Deproj_asc_node_sky)

### HIPPARCOS and *Gaia* proper motion anomaly

performed a survey of the proper motion anomaly (PMa) for the entire HIPPARCOS catalog. The PMa is defined as the difference between the *Gaia* short-term and HIPPARCOS-*Gaia* long-term proper motion. We used their result to constrain the properties of the new inner companion of $\pi^1$ Gru. In this analysis, we assumed that the photocenter only tracks the primary star, as confirmed by the non-detection of the companion in the visible with VLT/SPHERE (Sect. [\[SubSect:SEDs\]](#SubSect:SEDs)). Similar analyses have previously been performed by using the Tycho-2 catalog and the HIPPARCOS Intermediate Astrometric Data . The tangential velocity anomaly of the primary, measured between July 2014 and May 2017, is $6.07 \pm 0.33$ km s$^{-1}$, with a position angle of $358.00 \pm 1.38^\circ{}$. As stated in Sect. 2.3 of , the sensitivity function must be computed to determine what companion masses and separations can be detected. The PMa sensitivity is the result of the time smearing due to the finite observing window of both the HIPPARCOS and *Gaia* missions. For a 1.5 M$_\odot$ star at 162 pc, this sensitivity is illustrated in Fig. [5](#Fig:PMa_sens). As mentioned in Sect. [\[Sect:Intro\]](#Sect:Intro), $\pi^1$ Gru A already has a known companion, a G0V star ( and ) located at 2.8 arcsec in 2016 according to the Washington Double Star (WDS) catalog . This corresponds to a minimal physical separation of $453 \pm 33$ au. A G0V main-sequence (MS) star has a mass of 1.06 M$_\odot$ (, consistent with the 1.01 M$_\odot$ estimate of ), which is far below the sensitivity limit of $\sim 400$ M$_\odot$ at this separation (Fig. [5](#Fig:PMa_sens)). Consequently, the contribution of the G0V companion to the PMa is negligible. The maximum sensitivity is reached in the 4-20 au domain where the inner component, designated C, is detected. We therefore attribute the PMa entirely to the new C companion.

![](PMa_sensitivity)

### Derivation of orbital parameters

We used the formalism developed in to characterize the orbit. Figure [4](#Fig:system_sketch) illustrates the adopted parametrization of the $\pi^1$ Gru system. The $x$ and $y$ directions define the plane of the sky with $x$ corresponding to the right ascension and $y$ the declination. The $z$ axis is the line of sight away from Earth. $X$ and $Y$ define the orbital plane, with $Y$ the direction of the descending node and $X$ being orthogonal to it. The inclination $i$ is the inclination between the line of sight and the orbital plane (and corresponds to $i_\mathrm{Roy} - 90^\circ{}$, with $i_\mathrm{Roy}$ the definition of $i$ in ). The longitude of the ascending node, $\Omega$, is defined as $90^\circ{} - \Omega_\mathrm{Roy}$ to match the position angle convention. The argument of the periapsis is $\omega = 90^\circ{} - \omega_\mathrm{Roy}$. The true anomaly was denoted by $\theta$. We adopted the reference frame of the primary. The direct consequence is that the tangential velocity of the C companion ($v^t_{C/A}$) is related to the *Gaia* PMa of the primary $v^t_{A/\mathrm{bary}}$ through

$$\begin{equation}
        v^t_{C/A} = \left( 1 + \frac{M_A}{M_C} \right) v^t_{A/\mathrm{bary}},
\end{equation}$$

where $M_A$ and $M_C$ are the masses of the primary and the C companion, respectively. This simply reflects the conservation of momentum.

To solve the problem, we derived posterior probability distributions and Bayesian evidence using the nested sampling Monte Carlo algorithm `MLFriends` implemented in the `UltraNest`[^4] package . Bayesian inference uses Bayes’ theorem to determine the probability of hypotheses given evidence and/or observations. In other words, the prior distribution is used to derive the *a posteriori* probability. We use Python’s solver of the Kepler’s equation developed by Dan Foreman-Mackey[^5].

We explored the eight orbital parameters using the following flat prior distributions.

- $M_\mathrm{A}$ between 1.1 and 1.9 M$_\odot$ guided by a central mass estimate of 1.5 M$_\odot$ . The lower boundary ensures that the primary mass does not fall below the 1.1 M$_\odot$ derived by (cite: 2020A&A...644A..61H) for the C companion (and the upper boundary is chosen to be symmetric),

- $q= M_\mathrm{C}/M_\mathrm{A}$ between 0.2 and 0.8,

- $a$, the semi-major axis of the orbit, between 5 and 10 au (inferred from the separation in 2019, Sect. [\[SubSect:ALMA_SPHERE_pos\]](#SubSect:ALMA_SPHERE_pos)),

- $e$, the eccentricity, between 0 and 1,

- $\Omega$, the longitude of the ascending node, between 0 and 360$^\circ{}$,

- $\omega$, the argument of the periastron, between 0 and 360$^\circ{}$,

- $i$, the inclination, between 33 and 43$^\circ{}$ (Sect. [\[SubSect:ALMA_incli\]](#SubSect:ALMA_incli)),

- $\tau_0$, the epoch of the periastron between 2009 and 2024 (deduced from a period associated with the largest considered semi-major axis).

We allowed for a full parameter range exploration of $e$, $\Omega$, and $\omega$. The fit was constrained by several observations, namely the astrometry from the ALMA continuum 2019 observation (Sect. [\[SubSect:ALMA_SPHERE_pos\]](#SubSect:ALMA_SPHERE_pos)), the 0 km s$^{-1}$ radial velocity at PA = $52 \pm 5^\circ{}$ (Sect. [\[SubSect:ALMA_incli\]](#SubSect:ALMA_incli)), and the HIPPARCOS-*Gaia* PMa analysis (norm and direction) in the January 2016 epoch, which corresponds to the central epoch of the *Gaia* observations (Set. [\[SSect:Gaia_PMa\]](#SSect:Gaia_PMa)).

The uncertainty in the predictions guarantees that Bayesian fitting draws the prediction from the prior toward the observed data, resulting in a smaller in-sample error compared to the out-of-sample error, a phenomenon known as “overfitting”. By constraining the prior to plausible values, we limit the risk of obtaining an irrelevant posterior distribution, and thus mitigate overfitting. We used the step sampler with 1000 live points and a number of steps equal to twice the number of parameters.

The posterior probability distribution of the parameters is shown in the corner plot in Fig. [6](#Fig:corner_ultranest). The best-fit parameters listed in Table [1](#Tab:result_ultranest) correspond to the maximum likelihood, with the standard deviations obtained from the posterior probability distribution. As indicated by their relatively flat posterior distributions, the primary mass and inclination are poorly constrained. Runs with fixed values or Gaussian priors centered on literature values and their uncertainties for these parameters resulted in only marginal shifts of the other parameters within their error bars. We do not show the corner plot with these Gaussian priors as it might misleadingly suggest that the primary mass and inclination are constrained by the fitting algorithm. Using our flat priors, this would result in a C companion mass of $M_C = q . M_A = 0.86_{-0.20}^{+0.22}$ M$_\odot$ under the derived $M_A$. This value is below the upper limit of 1.1 M$_\odot$ reported by . The orbital period corresponding to our best orbital solution is $T = 11.0^{+1.7}_{-1.5}$ yr. These values are very close to those of the smoothed particle hydrodynamics model M17 from that predicts a spiral-shaped circumstellar environment. Such a structure has been observed around $\pi^1$ Gru by and . We note that the eccentricity converges toward an elliptical orbit ($e = 0.35^{+0.18}_{-0.17}$). However, the posterior distribution (Fig. [6](#Fig:corner_ultranest)) does not allow us to rule out a circular orbit. Our estimates of the orbital period and separation are compatible with the considerations of based on VLTI/MIDI observations of the molecular and dusty circumstellar environment. From the morphology of the gaseous environment, proposed an orbital period of 330 yr (semi-major axis of 70 au) for the C companion and an eccentricity of $\approx 0.8$. These estimates are excluded from our orbital solution. Within our best-fit solution, it is highly unlikely that the eruption they mention, which occurred 100 years ago, was caused by a direct interaction between the A and C components. Indeed, our periastron has a separation of $4.4^{+1.3}_{-1.3}$ au, i.e., $3.0^{+0.9}_{-0.9}$ times the radius of the primary . However, we cannot exclude more indirect interactions between the primary and companion near the periastron, such as the ejection of a convective plume of material by the AGB star, which triggers a localized interaction, producing an episode of enhanced mass loss.

The resulting best-fit orbit is shown in Fig. [7](#Fig:orbit_ultranest). We find good agreement between the 2019 ALMA detection and the model (top panel), as well as for the 0 km s$^{-1}$ line-of-sight velocity direction (bottom panel). For the *Gaia* PMa (middle panel), since we place ourselves in the reference frame of the primary, the primary itself has no motion. Nonetheless, we derived the modeled velocity of A in the barycentric frame for each epoch and plotted it at the companion’s position, to verify that the value of $6.07 \pm 0.33$ km s$^{-1}$ is reached for January 2016. We also reversed the direction of the PMa and plotted it on the orbit of the companion at the same epoch to ensure that it is tangential to the orbit. Figure [7](#Fig:orbit_ultranest) (middle panel) shows that both constraints are met.

In Table [4](#Tab:TrueAnom), we present the true anomaly for the best orbital solution at each observed epoch with both ALMA and ZIMPOL. Our best-fit model enabled us to locate the companion’s position on the VLT/SPHERE-ZIMPOL images (Fig. [2](#Fig:SPHERE_DoLP_companion)) without using them as constraints for the minimization. At each epoch where contemporaneous ALMA continuum detection is not available, the orbital solution predicts a C companion at the head of the polarized tail. This result both confirms that the dust tail is generated in the wake of the companion motion and validates the orbital solution.

observed $\pi^1$ Gru as part of their VLTI/MIDI large program and found an elongated dusty envelope along the PA direction $140^\circ$ ($\pm 180^\circ$, ). This PA is not consistent with the position of the companion relative to the primary at the corresponding epochs within our orbital solution (May 2011: PA of 277$^\circ$, September 2011: PA of 285$^\circ$), even accounting for a 180$^\circ$ degeneracy. The dusty tail observed with SPHERE is expected to trail the companion, which would imply an even smaller PA than that of the companion, and thus the inconsistency cannot be explained by a mismatch between the position of the dust tail and the companion. This discrepancy cannot be explained by the lower angular resolution of the MIDI data, which is $\sim 58$ mas (super-resolution $\lambda/2B$) and should be sufficient to resolve the dusty tail seen with SPHERE. To resolve this inconsistency, we propose that MIDI did not detect the dusty tail because it is sensitive to thermal emission from dust originating in a much larger region, which may be dominated by an asymmetric dust feature in the close circumstellar environment of $\pi^1$ Gru A. In contrast, the polarized light images from SPHERE-ZIMPOL are preferentially sensitive to scattered light from dust that lies mainly in the plane of the sky . However, this does not exclude the possibility that the material detected by MIDI interacts with the companion as it moves along its orbit.

![](ultranest_corner_ellipse_run3d)

![](ultranest_orbit_ellipse_run3d)

| Parameters     | Values                             |
|:---------------|:-----------------------------------|
| $M_\mathrm{A}$ | $1.54 - 2.19$ M$_\odot$            |
| $q$            | $0.48^{+0.08}_{-0.08}$             |
| $a$            | $7.05^{+0.54}_{-0.57}$ au          |
| $e$            | $0.35^{+0.18}_{-0.17}$             |
| $\Omega$       | $321.7^{+5.91}_{-5.67}~^\circ{}$   |
| $\omega$       | $359.00^{+7.87}_{-11.26}~^\circ{}$ |
| $i$            | $31.75 - 38.04~^\circ{}$           |
| $\tau_0$       | $2015.06^{+1.09}_{-1.14}$ yr       |

: Best-fit orbital parameters of $\pi^1$ Gru C from the `UltraNest` run.

Table notes: $M_\mathrm{A}$ ($M_\mathrm{C}$) : mass of the primary (close companion, resp.); q: mass ratio $M_\mathrm{C}/M_\mathrm{A}$; $a$: semi-major axis; $e$: eccentricity; $\Omega$: longitude of the ascending node; $\omega$: longitude of the periastron; $i$: inclination; $\tau_0$: epoch of periastron. Best-fit values correspond to the maximum likelihood of the posterior distribution; standard deviations correspond to the $68.3\%$ credible probability level from the posterior distribution. For $M_\mathrm{A}$ and $i$, only confidence intervals are given due to poor constraints from the `UltraNest` run. These three considerations combine with the uniform prior to produce an upper value for $M_A$ that exceeds the initial prior range.

## The nature of $\pi^1$ Gru C

We consider two scenarios for the nature of $\pi^1$ Gru C based on the parameters derived in Sect. [\[SubSect:Orbit\]](#SubSect:Orbit), particularly its mass $M_\mathrm{C} = 0.86^{+0.22}_{-0.20}$ M$_\odot$. The C companion could still be an MS star, specifically a yellow dwarf. Alternatively, the companion may be a compact remnant, such as a WD. We provide a justification for both scenarios.

According to , an MS star with the derived mass of the C component should be a yellow dwarf, corresponding to a spectral type between F9.5V and K7V. We focus on the central spectral type, K1V. Its parameters are determined by the same authors[^6] and are summarized in Table [\[Tab:caract_system\]](#Tab:caract_system).

Alternatively, the C component could be a WD. Considering the uncertainties in the mass of the C component, initial-final mass relations suggest an initial progenitor mass as high as 3 to 4 M$_\odot$. Given the estimate of the zero-age main-sequence mass of the present-day AGB star (of about 2 M$_\odot$), it is possible that both components A and C evolved toward their present state without any interaction. However, it is likely that this binary interaction has taken place during the system’s evolution. If so, in the WD scenario, the AGB progenitor of C may have transferred mass to the then main-sequence progenitor of $\pi^{1}$ Gru A through wind accretion and possibly Roche lobe overflow. The interaction could have reduced the mass of C more than in a single-star scenario, while increasing the mass of the current AGB star (e.g., and references therein). Such a scenario would allow for the C component to have evolved from a progenitor with a greater initial mass than in a noninteracting case (hence, with a shorter MS lifetime, allowing the WD to coexist with the present AGB).

| Parameter | A | B | C - MS scenario | C - WD scenario |
|:---|:---|:---|:---|:---|
| Spectral type | S5,7 (1) | G0V (2) | K1V$^\mathrm{F9.5V}_\mathrm{K7V}$ | D? |
| $R$ (R$_\odot$) | $319 \pm 23$ (3, 4) | 1.10 (5) | $0.80^{+0.34}_{-0.17}$ | $0.009 \pm 0.002$ |
| $L$ (L$_\odot$) | 7440 (6) | 1.35 (5) | $0.41^{+1.10}_{-0.31}$ | Unknown |
| $T_{\rm eff}$ (K) | 3200 (3) | 5930 (5) | $5170^{+820}_{-1070}$ | Unknown |
| $M$~ZAMS~ (M$_\odot$) | 2.0 (7) | 1.06 (5) | $0.86^{+0.22}_{-0.20}$ | $\sim 3 - 4$ |
| $M$~current~ (M$_\odot$) | 1.5 (7) | 1.06 (5) | $0.86^{+0.22}_{-0.20}$ | $0.86^{+0.22}_{-0.20}$ |
|  |  |  |  |  |

Table notes: $R$ and $L$ denote the radius and luminosity, respectively; $T_{\rm eff}$ is its effective temperature. For component C, the parameters are determined in this work. The MS spectral type, radius, luminosity, and effective temperature are taken from (5) using our derived mass. The WD radius is derived from (8) and its initial mass is inferred from (9).

## Variability of the $\pi^1$ Gru system in the visible

The AAVSO observations of $\pi^1$ Gru began in 1937. To search for a signature of the C companion, we looked for a periodic signal at the frequency corresponding to the orbital period. We selected only the visual observations because of their better time sampling and range. We analyzed the data with the `LombScargle` function implemented in `Astropy` . The light curve and the periodogram are shown in Fig. [8](#Fig:light_curve).

No significant periodic signal matching the best `UltraNest` orbital period is detected.

![](light_curve_periodogram)

## Photometry from the ultraviolet to the millimeter domain: scenarios for $\pi^1$ Gru C

To further investigate the nature of $\pi^1$ Gru, we used the photometry of the entire $\pi^1$ Gru system from the ultraviolet to the far-infrared, obtained from the VizieR database (Sect. [\[SubSect:VizieR_data\]](#SubSect:VizieR_data) and Table [3](#Tab:archive_photometry)), which includes GALEX ultraviolet observations . These data are plotted in Fig. [9](#Fig:SED). We note that ultraviolet spectra from the International Ultraviolet Explorer (IUE) satellite are also available[^7] for $\pi^1$ Gru. However, these spectra are very noisy, especially in the far-ultraviolet. Their levels are consistent with the GALEX measurements which, in contrast, have a much higher S/N. For this reason, we discard the IUE data in the following and rely only on the GALEX photometry for the ultraviolet. Fig [9](#Fig:SED) shows also the ISO spectra described in Sect. [\[SubSect:ISO_data\]](#SubSect:ISO_data).

![](pi1Gru_system_SED)

Furthermore, we deconvolved the ZIMPOL intensity observations (Stokes $I$) with the PSF images, using the `Pyraf` implementation of the Lucy-Richardson algorithm , with 10 iterations. The inner companion remains undetected after this additional image processing (Fig. [10](#Fig:ZIMPOL_intens_PSF)). Using the position of the companion from the contemporaneous ALMA continuum observations (Sect. [\[SubSect:ALMA_SPHERE_pos\]](#SubSect:ALMA_SPHERE_pos)), we estimated the detection limit by summing the brightness over a PSF surface area. In Fig. [9](#Fig:SED), we show these upper limits, along with the spectral flux density for both components from the ALMA Band 6 continuum. These limits do not account for the circumstellar material around the C companion. If it were possible to quantify this effect, the limits would likely be higher. However, providing such an estimate is not feasible due to the complex geometry of the material around $\pi^1$ Gru A and C.

![](ZIMPOL_intens_2019-07)

To reproduce the primary component SED, we used a MARCS model tuned to the S-type chemistry . To match the observed photometry, we adopted an angular diameter of 14.7 mas in place of the inferometric H band measurement of $18.37 \pm 0.18$ mas . To model $\pi^1$ Gru B and C in the yellow dwarf scenario, we retrieved PHOENIX spectra[^8] matching their characteristics from the literature and this work (Table [\[Tab:caract_system\]](#Tab:caract_system)). Both MARCS and PHOENIX SEDs were smoothed using a rectangular window spanning 4 Å. Beyond 5 $\mu$m, the SEDs were extrapolated using the Rayleigh-Jeans approximation. We note that both MARCS and PHOENIX models do not include circumstellar dust, are static (i.e., do not consider pulsations), and assume chemical equilibrium. The SED of the WD was obtained from , using a radius of 0.009 R$_\odot$ inferred from the mass through the relation described by . We selected an effective temperature of 15 000 K matching the far-ultraviolet photometry from GALEX.

We note ultraviolet and mid-infrared excesses from the full system photometry. Additionally, the integrated flux density of the C companion from the ALMA Band 6 continuum exceeds the expected values for either an MS yellow dwarf or a WD. These considerations are discussed in Sect. [\[SSect:Nature_Companion\]](#SSect:Nature_Companion).

# Discussion

## Comparison with the 2014 orbital solution

derived an orbital solution using the Tycho-2 observations combined with the HIPPARCOS Intermediate Astrometric Data. They found several solutions compatible with their dataset, with eccentricity ranging from 0.5 to 0.9 (best fit at 0.9) and orbital periods between 9.7 and 4.6 years (best fit at 6.3 years). This corresponds to a semi-major axis ranging from 6.3 to 3.5 au with best fit at 4.7 au (using their mid-interval mass ratio of 0.75). These values are just outside the range of our best orbital solution.

Using the `Dexter`[^9] tool, we recovered their orbital plot from Fig. 7 of their paper. We note that their right ascension axis is oriented east to the right, and that they plot the photocenter displacement. We assume that the photocenter traces the motion of the AGB (see the SED in Fig. [9](#Fig:SED)). To derive the companion’s proper motion, we used the barycenter of mass definition: $$\begin{equation}
        r  = - \left(1 + \frac{1}{q}\right) r_A.
\end{equation}$$

The resulting orbit is shown in the middle panel of Fig. [7](#Fig:orbit_ultranest) and again shows good qualitative agreement with our solution, particularly in orientation.

## The apparently inconsistent photometry of $\pi^1$ Gru C

If $\pi^1$ Gru C is a WD, and for most of the MS range, it is expected to escape detection from ZIMPOL visible observations. However, Fig. [9](#Fig:SED) shows that for the warmest MS solution, the C component could be detected. Our SEDs do not take into account the potential circumstellar extinction in the $\pi^1$ Gru system, either from the AGB wind or from around the C component in particular (accretion disk). Consequently, the coolest MS solutions are preferred, although warmer solutions cannot be ruled out.

The GALEX FUV (153 nm) and NUV (231 nm) photometry retrieved from the VizieR database show that the $\pi^1$ Gru system clearly exhibits an ultraviolet excess. This excess is not necessarily a signature of binarity, as it may originate within the chromospheric emission of the AGB star .

We therefore investigated whether chromospheric emission from the three components in the $\pi^1$ Gru system can produce the observed NUV and FUV fluxes observed with GALEX. For components B (a main-sequence star) and C, using empirical UV-to-total luminosity ratios from , we find that while their emission (dominated by B) can explain the observed NUV flux, their combined estimated FUV flux is significantly lower. To estimate the UV chromospheric contribution from A, we apply the results from , who analyzed a large GALEX sample of AGB stars with simple chromospheric models. They showed that if the FUV/NUV flux ratio, $R_{FUV/NUV}$, is less than 0.06, the UV emission can be explained by chromospheric and photospheric emission from an AGB star. However, if $R_{FUV/NUV}$, is significantly greater than 0.06, it must arise from accretion activity. For the comibined $\pi^1$ Gru system (A+B+C), $R_{FUV/NUV}=0.1$. Given that a substantial contribution of the NUV emission likely arises from B+C, the FUV/NUV flux ratio for $\pi^1$ Gru A is significantly greater than 0.1. This implies that the FUV emission seen toward $\pi^1$ Gru cannot be produced by chromospheric emission and instead results from accretion activity related to A and C.

The ALMA continuum imaging at the highest available angular resolution (19 mas) shows the presence of the C companion (Fig. [1](#Fig:ALMA_cont_high)). We argue that the observed millimeter-wave flux density (blue square in Fig. [9](#Fig:SED)) cannot originate directly from a stellar photosphere. For instance, to match the ALMA detection, we would need an M3III type star. However, this type of star (and other evolved late-type scenarios) would be well above the detection limit in the visible with ZIMPOL, which is not the case. We therefore conclude that the millimeter-wave emission toward $\pi^1$ Gru C arises in warm material surrounding the latter which likely resides in an accretion disk.

### Comparison with other close AGB binary systems

In Table [\[Tab:Other_systems\]](#Tab:Other_systems), we compile the characteristics of other confirmed relatively close AGB binary systems. These range from sub-stellar (L$_2$ Pup, ) to A-type MS companions (V Hya, ). The separations span from $1.96 \pm 0.16$ au (for L$_2$ Pup, ) and 150 au (W Aql, ), with eccentricities ranging between $0.024_{-0.017}^{+0.027}$ (V Hya, ) to $0.91 - 0.98$ (W Aql, ). Despite the small sample size, this parameter space covers a wide range of possibilities corresponding to those observed in post-AGB binaries . In terms of eccentricity and separation, W Aql represents an extreme case, exceeding the values observed so far in post-AGB systems. This is possibly because large periods are more difficult to measure. Of these five systems, R Aqr stand out with properties very similar to $\pi^1$ Gru. We therefore compared this system and the prototypical Mira ($o$ Ceti) to $\pi^1$ Gru.

|  | $o$ Ceti | L$_2$ Pup | R Aqr | V Hya | W Aql |
|:---|:---|:---|:---|:---|:---|
| $M_1$ (M$_\odot$) | $\sim 2$ (1) | $0.659 \pm 0.043$ (7) | $1.0 \pm 0.2$ (10) | $0.775^{+0.64}_{-0.37}$ (13) | $1.6 \pm 0.2$ (16, 17) |
| $M_2$ (M$_\odot$) | $\sim 0.7$ (1) | $(1.14 \pm 1.52) \times 10^{-2}$ (7) | $0.7\pm0.2$ (10) | $2.63^{+0.63}_{-0.69}$ (13) | $1.09 - 1.04$ (16) |
| Spec. typ. | M5-9IIIe+DA (2, 3) | M5IIIe+L/T (7, 8) | M7e+D (11) | C-N:6+A0 (14, 13) | S6/6e+ F8/G0 (18, 19) |
| a (au) | 70-95 (4, 5) | $\geq 1.96 \pm 0.16$ (7) | $14.5 \pm 2$ (10) | $11.2^{+1.2}_{-1.5}$ (13) | $149 - 150$ (16) |
| $e$ | $\sim 0.16$ (4) | Unknown | $0.45 \pm 0.01$ (10) | $0.024^{+0.027}_{-0.017}$ (13) | $0.91 - 0.98$ (16) |
| $\dot{M}$ (M$_\odot$ yr$^{-1}$) | $2.5 \times 10^{-7}$ (6) | $5 \times 10^{-7}$ (9) | $3 \times 10^{-6}$ (12) | $1.5 \times 10^{-5}$ (15) | $3.0 \times 10^{-6}$ (20) |

The emission at the position of $o$ Ceti B corresponds to $\sim 12$ mJy at $\sim 229$ GHz (cite: Vlemmings2015), which is 1.7 times brighter than the emission observed for $\pi^1$ Gru C after correcting for the smaller distance of the $o$ Ceti AB system. At wavelengths longer than 3.1 mm, the emission is expected to be dominated by free-free emission, while at shorter wavelengths, a nearly thermal and probably compact component is expected to dominate (cite: Planesas2016). For R Aqr B, free-free emission from ionized gas surrounding the WD is expected to dominate the emission at millimeter wavelengths. This is supported by the observed spectral index $\sim 1.0$ at 0.9 mm (cite: Bujarrabal2018) and the detection of the H30$\alpha$ recombination line (cite: Gomez-Garrido2024). The base of the jets observed in H$\alpha$ with SPHERE (cite: Schmid2017) at visible wavelengths is also detected in the continuum emission at 1.3 mm (cite: Gomez-Garrido2024). At the position of the companion, emission peaks near 5 mJy at 0.9 mm (cite: Bujarrabal2018). If the spectral index between 0.9 and 1.3 mm is 1.0 (similar to its value at 0.9 mm), a flux density $\sim 3.5$ mJy is expected at 1.3 mm. This is 2.7 times brighter than the continuum emission of $\pi^1$ Gru C when considering the larger distance to R Aqr. This points toward $\pi^1$ Gru C being a MS object, however, this remains a tentative conclusion.

### Considerations on the accretion disk surrounding $\pi^1$ Gru C

Given the differing nature of the emission observed at 1.3 mm toward $o$ Ceti B and R Aqr B, it is not possible to determine the source of the emission seen toward $\pi^1$  Gru based solely on these comparisons.

To address this, we investigate the two main physical mechanisms for producing millimeter-wave continuum emission from the vicinity of C: thermal dust emission and free-free emission from ionized gas. The spectral slope of the emission in the millimeter range can distinguish between these two mechanisms.

We first consider thermal dust emission from an accretion disk. This disk is expected to have an outer “hot” spot or annulus where the primary material impacts the disk, generating shocks. Additionally, the accretion disk will have a hot inner boundary layer. If the companion has a significant magnetic field, an inner hot spot may form where material is channeled along the magnetic field. However, the rest of the disk (i.e., most of its surface area) should be significantly cooler . The contributions of the hot spots to the optical and mm-wave photometry are likely to be negligible.

We can compute the radial temperature distribution if the disk is optically thick and in thermal equilibrium, using the equation below (cite: Pringle1981): $$\begin{equation}
        \sigma T_s(r)^4 = (G M / r^3) (3\,\mbox{$\dot{M}$}_{a} /8 \pi) [1 - (r_i/r)^{0.5}],
\end{equation}$$

where $\sigma$ is the Stefan-Boltzmann constant, $T_s(r)$ is the disk surface temperature at radius $r$, $r_i$ is the radius at the inner edge of the disk, $M$ is the mass of the accretor, and $\mbox{$\dot{M}$}_{a}$ is the rate of accretion. Assuming the disk emits as a blackbody, we compute the emission for various values of $\mbox{$\dot{M}$}_{a}$. We computed a large grid of models with $0.001 <r_i ({\rm au}) < 0.01$. The outer disk radius was conservatively set to $r_o ({\rm au}) \le 2$ because the continuum source is unresolved with a beam of $0.025''$. For the mass accretion rate, a typical maximum value would be $\sim$10% of the mass-loss rate of the wind from the primary A. However, assuming an accretion rate $\mbox{$\dot{M}$}_{a} \le 7.7\times10^{-8}$ $M_{\odot}$ yr$^{-1}$, given the mass-loss rate of A of $\mbox{$\dot{M}$}(A)=7.7\times10^{-7}$ $M_{\odot}$ yr$^{-1}$, we find that the resulting emission is significantly less than required. We find that the minimum accretion rate required to produce the observed 1.3 mm flux of 3.3 mJy is $\mbox{$\dot{M}$}_{a} \ge 3.2\times10^{-7}$ $M_{\odot}$ yr$^{-1}$, which corresponds to $\sim40$% of the primary’s mass-loss rate and is therefore very unlikely.

However, noting that C is located at an average distance of about 6 au from the primary A, the mid-point of the near-side (toward A) of this disk is likely to be only about 3.5 au from the surface of A, and the dust there will also be heated by the nearby primary star, A. With $L = 7244$ L$_\odot$, $T_\mathrm{eff}=3100$ K, we find that the dust reaches a temperature of about 1300 K at a distance of 3.9 (7.5) au from the primary for a dust emissivity $\kappa(\nu)\propto\lambda^{-p}$, where $p$ = 1.5 (0, respectively). We conclude that heating of the dust by the primary dominates over accretion, resulting in temperatures much higher than the average disk temperature due to accretion.

Assuming the dust in the accretion disk around the companion is at this temperature, then $M_d = 1.7\times10^{-7}$ (1 cm$^{2}$ g$^{-1}$/$\kappa$(1.3mm)) M$_\odot$, where $\kappa$(1.3mm) is the absolute dust emissivity at 1.3 mm. For a gas-to-dust ratio of 200, this corresponds to a gas mass of $3.4\times10^{-5}$ M$_\odot$. The average optical depth of this emitting region is much less than unity. The SED of this dust emission in the millimeter and submillimeter regime is expected to be $\lambda^{-(2+p)}$.

Recent Smoothed Particle Hydrodynamics (SPH) simulations of binary interactions between the wind of an AGB star and a low-mass companion reveal the formation of an accretion disk around the companion, with disk sizes of 0.5-0.9 au, consistent with the sizes discussed here. The disk temperatures predicted by these simulations can reach as high as 6000 K to 20 000 K, considerably higher than the thermal equilibrium situation assumed here. At such high temperatures, dust would rapidly evaporate, implying that the observed ALMA emission must originate from a different mechanism. We discuss free-free emission as a possible source below.

Free-free emission may also contribute to the observed 1.3 mm continuum emission toward $\pi^1$ Gru C if the gas in its vicinity is ionized by the radiation field from a WD or from accretion hot spots. For example, based on the constant density model presented by (cite: Olnon1975), a region of size $0.025''$ with an electron temperature between 3000 K and 10$^{4}$ K would produce a flux density of $\sim 3$ mJy for an electron density $\sim2\times10^{7}$ cm$^{-3}$, with a corresponding free-free optical depth (along the line of sight, measured from the center of the object) at 1.3 mm $\sim 0.02$. Given the AGB mass-loss rate $\mbox{$\dot{M}$}(A)=7.7\times10^{-7}$ $M_{\odot}$ yr$^{-1}$and assuming a value of 5 km s$^{-1}$ for the expansion velocity[^10], a density of about $1.5\times10^9$ cm$^{-3}$ is expected at a radius of 3.5 au. This would imply an ionization fraction $\sim 0.01$, which should be attainable in the vicinity of an ionizing source. The spectral index of this optically thin free-free emission in the millimeter and submillimeter regime should be $\sim 0$. The detection of recombination lines would also favor this scenario.\
The SEDs shown in Fig. [9](#Fig:SED) do not take into account dust extinction. $\pi^1$ Gru lies outside the Galactic plane (at Galactic latitude $< -55^\circ{}$), so the interstellar dust extinction should be minimal along a line of sight of 162 pc (which is supported by the agreement between the AGB SED and the photometry for wavelengths from the V band to about 5 $\mu$m on Fig. [9](#Fig:SED)). According[^11] to , $\pi^1$ Gru should have interstellar extinction $A_V = 0.005$. However, the mid-infrared excess in the SED indicates the presence of significant circumstellar dust. Further investigation of the UV excess is hindered by the lack of spatially resolved information on the 3D geometry of the dust in the $\pi^1$ Gru system, particularly within the accretion disk of $\pi^1$ Gru C. This prevents a clear discrimination between thermal dust emission and free-free emission scenarios.

## Future evolution of the system

With such a small separation ($a = 7.05^{+0.54}_{-0.57}$ au, see Sect. [\[SubSect:Astrometry\]](#SubSect:Astrometry)) between $\pi^1$ Gru A and C, the future evolution of the system warrants consideration. Since $\pi^1$ Gru B lies at a separation of $453 \pm 22$ au, and assuming it does not have a high eccentricity, it is unlikely to interact, through gravitation or radiation, with the inner pair beyond some possible weak shaping of the wind (cite: Maes2021).

If $\pi^1$ Gru C is an MS star, it will continue to accrete material from the wind of $\pi^1$ Gru A as the latter evolves through its AGB and post-AGB phases. This will slightly increase the mass of C and potentially alter its surface composition, producing chemical anomalies as observed in Ba dwarfs . $\pi^1$ Gru C will contribute to shaping of the planetary nebula (PN) resulting from the demise of $\pi^1$ Gru A. The importance of C in this process depends on its exact mass, orbital properties, and on the velocity and strength of A’s stellar wind at the position of C ( and (cite: Maes2021)). measured a terminal wind velocity of $10 - 13$ km s$^{-1}$, and a mass-loss rate of $7.7 \times 10^{-7}$ M$_\odot$ yr$^{-1}$. However, predicting the future evolution of these parameters remains challenging. Ultimately, $\pi^1$ Gru A will become a WD. After tens of billions of years, the presumed yellow dwarf $\pi^1$ Gru C will evolve toward the AGB stage or, if its mass is toward the lower range, enter the hypothetical blue dwarf stage, ultimately becoming a WD .

Alternatively, if $\pi^1$ Gru C is already a WD, assuming an accretion rate of 10% of the primary’s mass-loss rate, it may produce classical novæ with a period $\approx 900$ years (see Fig. 2 of ). However, the current accretion rate is insufficient to produce a Type Ia supernova. already concluded that the mass-loss eruption detected $\approx 100$ years ago was unlikely to have been caused by a nova event. As discussed in Sect. [\[SubSect:Orbit\]](#SubSect:Orbit), direct interactions between the primary and the C companion are unlikely. We propose that the enhanced mass-loss episode a century ago originated directly from the AGB, regardless of whether the C companion is an MS star or a WD.

Whether $\pi^1$ Gru C is an MS yellow dwarf or a WD, as long as the distant B component remains gravitationally bound, the $\pi^1$ Gru system will eventually evolve into a triple WD system (similar to ; (cite: 2019MNRAS.483..901P)).

# Conclusion

ALMA observations of $\pi^1$ Gru have directly detected the presence of an inner companion (separation of $37.4\pm 2.0$ mas in June-July 2019). This source appears in band 6 (1.3 mm) imaging at an angular resolution of 25 mas. The detection cannot represent the photosphere of a companion star as it would correspond to an M3 giant star that should be visible in contemporaneous VLT/SPHERE-ZIMPOL adaptive optics imaging in the visible. Combining ALMA detection with HIPPARCOS-*Gaia* PMa and constraints on the gas distribution, we derive an orbital solution leading to a mass of $0.86^{+0.22}_{-0.20}$ M$_\odot$ for this new inner companion, hereafter $\pi^1$ Gru C. The characteristics of the companion and the orbital solution are qualitatively in agreement with those derived by , who used a more limited dataset. Our result also agrees with the upper limit of 1.1 M$_\odot$ derived by . The mass of companion C corresponds to that of a K1V$^\mathrm{F9.6V}_\mathrm{K7V}$ main sequence star or a WD remnant evolved from a star with a ZAMS mass of at most $\sim 3 - 4$ M$_\odot$, assuming a noninteracting evolutionary path (the initial mass could be higher otherwise). Photometry in ultraviolet and millimeter wavelengths indicates that this companion has to be surrounded by a locally hot accretion disk, consistent with recent hydrodynamical simulations . The derived orbital solution is elliptical ($e = 0.35^{+0.18}_{-0.17}$), however the posterior distribution cannot totally exclude a circular solution. The corresponding orbital period we obtain is $T = 11.0^{+1.7}_{-1.5}$ yr. Both parameters lie outside the confidence interval of , excluding the hypothesis that the eruption they estimate to have occurred a century ago was caused by a direct interaction between the C companion and the primary AGB. However, an interaction near periastron with a plume of ejected material from the AGB star cannot be ruled out.

If the C companion is a main-sequence yellow dwarf, it will further evolve toward the AGB phase or the hypothetical blue dwarf stage, depending on its current mass, before becoming a WD. If the C companion is a WD, its low mass does not allow it to accrete enough mass from the AGB wind to produce a type Ia supernova, although it could produce classical nova events every $\approx 900$ years. Ultimately, within both the yellow dwarf and WD scenarios, all three components of the $\pi^1$ Gru system will end as WDs.

Further observations of the $\pi^1$ Gru system are required to better characterize the C companion and its environment. The brightness of the AGB dominates most of the spectrum, except in the ultraviolet for the WD scenario. Investigating the C companion will require high angular resolution through the longest baselines of ALMA, or with large single-dish telescopes such as the Extremely Large Telescope (ELT), although the infrared will be excessively dominated by the AGB star. In the longer term, the Habitable Worlds Observatory may enable further study. Expanding the sample of AGB systems with close-in companions will improve constraints on the physics of tides, mass and angular momentum transfer, and orbital evolution of such binary systems.

# Data availability

The reduced VLT/SPHERE-ZIMPOL data of the $\pi^1$ Gru system are only available at the CDS via anonymous ftp to [cdsarc.cds.unistra.fr](cdsarc.cds.unistra.fr) ([130.79.128.5](130.79.128.5)) or via <https://cdsarc.cds.unistra.fr/viz-bin/cat/J/A+A/671/A96> and <https://cdsarc.cds.unistra.fr/viz-bin/cat/J/A+A/699/A22>. The ALMA image cubes of the $\pi^1$ Gru system are available online at <https://almascience.eso.org/alma-data/lp/atomium>.

# Acknowledgements

The authors acknowledge the constructive comments from the anonymous referee that considerably improved the quality of the article. We are thankful to Dr. Léa Planquart for indicating an error in the inclination convention. Based on observations collected at the European Southern Observatory under ESO programme 095.D-0397(D), 095.D-0309(B), 0103.D-0772(A), and 1104.C-0416(F). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00659.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement. We acknowledge with thanks the variable star observations from the AAVSO International Database contributed by observers worldwide and used in this research. This research has made use of the Washington Double Star Catalog maintained at the U.S. Naval Observatory. This project has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Skłodowska-Curie Grant agreement No. 665501 with the research Foundation Flanders (FWO) (\[PEGASUS\]$^2$ Marie Curie fellowship 12U2717N awarded to M.M.). MM acknowledges funding from the Programme Paris Region fellowship supported by the Région Ile-de-France. This project has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Skłodowska-Curie Grant agreement No. 945298. MVdS acknowledges support from the Oort Fellowship at Leiden Observatory. R.S.’s contribution to the research described in this publication was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA. R.S. thanks NASA for financial support via GALEX GO and ADAP awards. A.B. acknowledges support from ANR PEPPER and ANR WATERSTARS. The research leading to these results has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program (projects CepBin, grant agreement 695099, and UniverScale, grant agreement 951549). KTW acknowledges support from the ERC under the European Union’s Horizon 2020 research and innovation programme (Grant agreement no. 883867, project EXWINGS). TD is supported in part by the Australian Research Council through a Discovery Early Career Researcher Award (DE230100183). This research was supported in part by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. IM acknowledges that this project has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004214, and acknowledges funding from UKRI/STFC through grants ST/T000414/1 and ST/X001229/1. SS would like to acknowledge the support of Research Foundation-Flanders (grant number: 1239522N). AAZ acknowledges funding from STFC under grant ST/T000414/1. Financial support from the Knut and Alice Wallenberg foundation is gratefully acknowledged through grant nr. KAW 2020.0081. This work is funded by the French National Research Agency (ANR) project PEPPER (ANR-20-CE31- 0002). LS is a senior research associate from F.R.S.- FNRS (Belgium). MS acknowledges support from NOVA. J.M. acknowledges support from the Research Foundation Flanders (FWO) grant G099720N. S.H.J.W. acknowledges support from the Research Foundation Flanders (FWO) through grant 1285221N. IEM acknowledges funding via the BASAL Centro de Excelencia en Astrofisica y Tecnologias Afines (CATA) grant PFB06/2007. This work has made use of the SPHERE Data Centre, jointly operated by OSUG/IPAG (Grenoble), PYTHEAS/LAM/CESAM (Marseille), OCA/Lagrange (Nice), Observatoire de Paris/LESIA (Paris), and Observatoire de Lyon. We used the SIMBAD and VIZIER databases at the CDS, Strasbourg (France, <http://cdsweb.u-strasbg.fr/>), and NASA’s Astrophysics Data System Bibliographic Services. This research made use IPython (cite: PER-GRA:2007), Numpy (cite: 5725236), Matplotlib (cite: Hunter:2007), SciPy (cite: 2020SciPy-NMeth), Pandas (cite: reback2020pandas; mckinney-proc-scipy-2010), Astropy (available at <http://www.astropy.org/>), a community-developed core Python package for Astronomy , corner (cite: corner) and Uncertainties (available at <http://pythonhosted.org/uncertainties/>): a Python package for calculations with uncertainties.\

145 natexlab

(ref: 2005AN....326..913A) Adams, F. C., Bodenheimer, P., & Laughlin, G. 2005, Astronomische Nachrichten, 326, 913

(ref: 1923PASP...35..323A) Aitken, R. G. 1923, PASP, 35, 323

(ref: 1992AAS...180.3708A) Ake, T. B. & Johnson, H. R. 1992, in American Astronomical Society Meeting Abstracts, Vol. 180, American Astronomical Society Meeting Abstracts #180, 37.08

(ref: 2023hsa..conf..190A) Alcolea, J., Mikolajewska, J., Gómez-Garrido, M., et al. 2023, in Highlights on Spanish Astrophysics XI, ed. M. Manteiga, L. Bellot, P. Benavidez, A. de Lorenzo-Cáceres, M. A. Fuente, M. J. Martı́nez, M. Vázquez Acosta, & C. Dafonte, 190

(ref: 2022ApJ...935..167A) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: 2022MNRAS.513.4405A) Aydi, E. & Mohamed, S. 2022, MNRAS, 513, 4405

(ref: 2002MNRAS.337...79B) Bedding, T. R., Zijlstra, A. A., Jones, A., et al. 2002, MNRAS, 337, 79

(ref: 2019A&A...631A.155B) Beuzit, J. L., Vigan, A., Mouillet, D., et al. 2019, A&A, 631, A155

(ref: 2017ApJS..230...24B) Bianchi, L., Shiao, B., & Thilker, D. 2017, ApJS, 230, 24

(ref: 1985ApJS...59..197B) Bidelman, W. P. 1985, ApJS, 59, 197

(ref: 2016S&C....26..383B) Buchner, J. 2016, Statistics and Computing, 26, 383

(ref: 2019PASP..131j8005B) Buchner, J. 2019, PASP, 131, 108005

(ref: 2021JOSS....6.3001B) Buchner, J. 2021, The Journal of Open Source Software, 6, 3001

(ref: 2021A&A...651A...4B) Bujarrabal, V., Agúndez, M., Gómez-Garrido, M., et al. 2021, A&A, 651, A4

(ref: Bujarrabal2018) Bujarrabal, V., Alcolea, J., Mikołajewska, J., Castro-Carrizo, A., & Ramstedt, S. 2018, A&A, 616, L3

(ref: 1985AbaOB..59...83B) Burnashev, V. I. 1985, Abastumanskaia Astrofizicheskaia Observatoriia Byulleten, 59, 83

(ref: 2006ApJ...645..605C) Chiu, P.-J., Hoang, C.-T., Dinh-V-Trung, et al. 2006, ApJ, 645, 605

(ref: 2018ApJ...866...21C) Cummings, J. D., Kalirai, J. S., Tremblay, P. E., Ramirez-Ruiz, E., & Choi, J. 2018, ApJ, 866, 21

(ref: 1994AJ....107.1469D) Danchi, W. C., Bester, M., Degiacomi, C. G., Greenhill, L. J., & Townes, C. H. 1994, AJ, 107, 1469

(ref: 2024NatAs...8..308D) Danilovich, T., Malfait, J., Van de Sande, M., et al. 2024, Nature Astronomy, 8, 308

(ref: 2015A&A...574A..23D) Danilovich, T., Olofsson, G., Black, J. H., Justtanont, K., & Olofsson, H. 2015, A&A, 574, A23

(ref: 2010A&A...523A..18D) De Beck, E., Decin, L., de Koter, A., et al. 2010, A&A, 523, A18

(ref: 2020A&A...642A..20D) De Beck, E. & Olofsson, H. 2020, A&A, 642, A20

(ref: 2017PASA...34....1D) De Marco, O. & Izzard, R. G. 2017, PASA, 34, e001

(ref: 2009ApJ...705.1298D) De Mello, A. B., Lorenz-Martins, S., de Araújo, F. X., Bastos Pereira, C., & Codina Landaberry, S. J. 2009, ApJ, 705, 1298

(ref: 2021ARA&A..59..337D) Decin, L. 2021, ARA&A, 59, 337

(ref: 2020Sci...369.1497D) Decin, L., Montargès, M., Richards, A. M. S., et al. 2020, Science, 369, 1497

(ref: 2017A&A...605A..28D) Doan, L., Ramstedt, S., Vlemmings, W. H. T., et al. 2017, A&A, 605, A28

(ref: 2020A&A...633A..13D) Doan, L., Ramstedt, S., Vlemmings, W. H. T., et al. 2020, A&A, 633, A13

(ref: 2001ApJ...558..309D) Ducati, J. R., Bevilacqua, C. M., Rembold, S. B., & Ribeiro, D. 2001, ApJ, 558, 309

(ref: 1996AJ....112.2862E) Egan, M. P. & Price, S. D. 1996, AJ, 112, 2862

(ref: 1997ESASP1200.....E) ESA. 1997, in ESA Special Publication, Vol. 1200, ESA Special Publication

(ref: 2020A&A...639A..24E) Escorza, A., Siess, L., Van Winckel, H., & Jorissen, A. 2020, A&A, 639, A24

(ref: 2002A&A...384..180F) Fabricius, C., Høg, E., Makarov, V. V., et al. 2002, A&A, 384, 180

(ref: 1953MNRAS.113..510F) Feast, M. W. 1953, MNRAS, 113, 510

(ref: corner) Foreman-Mackey, D. 2016, The Journal of Open Source Software, 1, 24

(ref: 2006OExpr..14.7515F) Fusco, T., Rousset, G., Sauvage, J. F., et al. 2006, Optics Express, 14, 7515

(ref: 2021A&A...649A...1G) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1

(ref: 2016A&A...595A...1G) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1

(ref: 2023A&A...674A...1G) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: 1999A&A...346..505G) Gauger, A., Balega, Y. Y., Irrgang, P., Osterbart, R., & Weigelt, G. 1999, A&A, 346, 505

(ref: 2011AJ....142...15G) Girard, T. M., van Altena, W. F., Zacharias, N., et al. 2011, AJ, 142, 15

(ref: Gomez-Garrido2024) Gómez-Garrido, M., Bujarrabal, V., Alcolea, J., et al. 2024, A&A, 689, A317

(ref: 2011AstL...37..707G) Gontcharov, G. A. 2011, Astronomy Letters, 37, 707

(ref: 2022A&A...660A..94G) Gottlieb, C. A., Decin, L., Richards, A. M. S., et al. 2022, A&A, 660, A94

(ref: 1879RNAO....1....1G) Gould, B. A. 1879, Resultados del Observatorio Nacional Argentino, 1, I

(ref: 2011A&A...526A.162G) Groenewegen, M. A. T., Waelkens, C., Barlow, M. J., et al. 2011, A&A, 526, A162

(ref: 2001ApJ...558..323H) Hachisu, I. & Kato, M. 2001, ApJ, 558, 323

(ref: 2016ARA&A..54..135H) Hartmann, L., Herczeg, G., & Calvet, N. 2016, ARA&A, 54, 135

(ref: 2015AAS...22533616H) Henden, A. A., Levine, S., Terrell, D., & Welch, D. L. 2015, in American Astronomical Society Meeting Abstracts, Vol. 225, American Astronomical Society Meeting Abstracts #225, 336.16

(ref: 1994AJ....107..280H) Hindsley, R. B. & Harrington, R. S. 1994, AJ, 107, 280

(ref: 2018A&ARv..26....1H) Höfner, S. & Olofsson, H. 2018, A&ARv, 26, 1

(ref: 2000A&A...355L..27H) Høg, E., Fabricius, C., Makarov, V. V., et al. 2000, A&A, 355, L27

(ref: 2020A&A...644A..61H) Homan, W., Montargès, M., Pimpanuwat, B., et al. 2020, A&A, 644, A61

(ref: Hunter:2007) Hunter, J. D. 2007, Computing In Science & Engineering, 9, 90

(ref: 2013A&A...553A...6H) Husser, T. O., Wende-von Berg, S., Dreizler, S., et al. 2013, A&A, 553, A6

(ref: 1975RMxAA...1..299J) Johnson, H. L. & Mitchell, R. I. 1975, , 1, 299

(ref: 1966CoLPL...4...99J) Johnson, H. L., Mitchell, R. I., Iriarte, B., & Wisniewski, W. Z. 1966, Communications of the Lunar and Planetary Laboratory, 4, 99

(ref: 2004agbs.book..461J) Jorissen, A. 2004, in Asymptotic Giant Branch Stars, ed. H. J. Habing & H. Olofsson, 461–518

(ref: 1998A&AS..129..363J) Jorissen, A. & Knapp, G. R. 1998, A&AS, 129, 363

(ref: 1997ApJ...482L.175K) Karovska, M., Hack, W., Raymond, J., & Guinan, E. 1997, ApJL, 482, L175

(ref: 1954ApJ...120..484K) Keenan, P. C. 1954, ApJ, 120, 484

(ref: 1980ApJS...43..379K) Keenan, P. C. & Boeshaar, P. C. 1980, ApJS, 43, 379

(ref: 2022A&A...657A...7K) Kervella, P., Arenou, F., & Thévenin, F. 2022, A&A, 657, A7

(ref: 2016A&A...596A..92K) Kervella, P., Homan, W., Richards, A. M. S., et al. 2016, A&A, 596, A92

(ref: 1996A&A...315L..27K) Kessler, M. F., Steinz, J. A., Anderegg, M. E., et al. 1996, A&A, 315, L27

(ref: 2012SPIE.8445E..1AK) Klotz, D., Sacuto, S., Paladini, C., Hron, J., & Wachter, G. 2012, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 8445, Optical and Infrared Interferometry III, ed. F. Delplancke, J. K. Rajagopal, & F. Malbet, 84451A

(ref: 1997A&A...326..318K) Knapp, G. R., Jorissen, A., & Young, K. 1997, A&A, 326, 318

(ref: 2010MmSAI..81..921K) Koester, D. 2010, Mem. Soc. Astron. Italiana, 81, 921

(ref: 2019A&A...625A.135L) Lallement, R., Babusiaux, C., Vergely, J. L., et al. 2019, A&A, 625, A135

(ref: 2008AJ....136..735L) Lasker, B. M., Lattanzi, M. G., McLean, B. J., et al. 2008, AJ, 136, 735

(ref: 1974AJ.....79..745L) Lucy, L. B. 1974, AJ, 79, 745

(ref: 2012Natur.490..232M) Maercker, M., Mohamed, S., Vlemmings, W. H. T., et al. 2012, Nature, 490, 232

(ref: Maes2021) Maes, S., Homan, W., Malfait, J., et al. 2021, A&A, 653, A25

(ref: 2024A&A...691A..84M) Malfait, J., Siess, L., Esseldeurs, M., et al. 2024, A&A, 691, A84

(ref: 1999ApJ...523..357M) Mastrodemos, N. & Morris, M. 1999, ApJ, 523, 357

(ref: 2014A&A...570A.113M) Mayer, A., Jorissen, A., Paladini, C., et al. 2014, A&A, 570, A113

(ref: 2024RASTI...3...89M) McDonald, I., Zijlstra, A. A., Cox, N. L. J., et al. 2024, RAS Techniques and Instruments, 3, 89

(ref: 1935ApJ....81..312M) Merrill, P. W. 1935, ApJ, 81, 312

(ref: 2016A&A...588A..25M) Miller Bertolami, M. M. 2016, A&A, 588, A25

(ref: 2000ApJ...543..861M) Monnier, J. D., Danchi, W. C., Hale, D. S., et al. 2000a, ApJ, 543, 861

(ref: 2000ApJ...543..868M) Monnier, J. D., Danchi, W. C., Hale, D. S., Tuthill, P. G., & Townes, C. H. 2000b, ApJ, 543, 868

(ref: 2023A&A...671A..96M) Montargès, M., Cannon, E., de Koter, A., et al. 2023, A&A, 671, A96

(ref: 2017ApJ...841...33M) Montez, Jr., R., Ramstedt, S., Kastner, J. H., Vlemmings, W., & Sanchez, E. 2017, ApJ, 841, 33

(ref: 1978A&AS...34..477M) Morel, M. & Magnenat, P. 1978, A&AS, 34, 477

(ref: 2015yCat.5145....0M) Myers, J. R., Sande, C. B., Miller, A. C., Warren, W. H., J., & Tracewell, D. A. 2015, VizieR Online Data Catalog, V/145

(ref: 2016MNRAS.463.4210N) Nascimbeni, V., Piotto, G., Ortolani, S., et al. 2016, MNRAS, 463, 4210

(ref: 1972ApJ...175..417N) Nauenberg, M. 1972, ApJ, 175, 417

(ref: 1975A&AS...22..239N) Nicolet, B. 1975, A&AS, 22, 239

(ref: 2008PASP..120.1128O) Ofek, E. O. 2008, PASP, 120, 1128

(ref: 2007A&A...466.1099O) Ohnaka, K., Driebe, T., Weigelt, G., & Wittkowski, M. 2007, A&A, 466, 1099

(ref: 2015A&A...581A.127O) Ohnaka, K., Schertl, D., Hofmann, K. H., & Weigelt, G. 2015, A&A, 581, A127

(ref: Olnon1975) Olnon, F. M. 1975, A&A, 39, 217

(ref: 2018A&A...620A..85O) Oomen, G.-M., Van Winckel, H., Pols, O., et al. 2018, A&A, 620, A85

(ref: 2018Natur.553..310P) Paladini, C., Baron, F., Jorissen, A., et al. 2018, Nature, 553, 310

(ref: 2017A&A...600A.136P) Paladini, C., Klotz, D., Sacuto, S., et al. 2017, A&A, 600, A136

(ref: reback2020pandas) pandas development team, T. 2020, pandas-dev/pandas: Pandas

(ref: 2013ApJS..208....9P) Pecaut, M. J. & Mamajek, E. E. 2013, ApJS, 208, 9

(ref: PER-GRA:2007) Pérez, F. & Granger, B. E. 2007, Computing in Science and Engineering, 9, 21

(ref: 2019MNRAS.483..901P) Perpinyà-Vallès, M., Rebassa-Mansergas, A., Gänsicke, B. T., et al. 2019, MNRAS, 483, 901

(ref: 1999A&A...345..221P) Perrin, G., Coudé du Foresto, V., Ridgway, S. T., et al. 1999, A&A, 345, 221

(ref: 2004A&A...418..675P) Perrin, G., Ridgway, S. T., Coudé du Foresto, V., et al. 2004, A&A, 418, 675

(ref: Planesas2016) Planesas, P., Alcolea, J., & Bachiller, R. 2016, A&A, 586, A69

(ref: 2024A&A...682A.143P) Planquart, L., Jorissen, A., Escorza, A., Verhamme, O., & Van Winckel, H. 2024a, A&A, 682, A143

(ref: 2024A&A...687A.306P) Planquart, L., Paladini, C., Jorissen, A., et al. 2024b, A&A, 687, A306

(ref: 2010A&A...514A...3P) Pollo, A., Rybka, P., & Takeuchi, T. T. 2010, A&A, 514, A3

(ref: 2010ApJS..190..203P) Price, S. D., Smith, B. J., Kuchar, T. A., Mizuno, D. R., & Kraemer, K. E. 2010, ApJS, 190, 203

(ref: Prieur2002) Prieur, J. L., Aristidi, E., Lopez, B., et al. 2002, ApJS, 139, 249

(ref: Pringle1981) Pringle, J. E. 1981, ARA&A, 19, 137

(ref: 2018A&A...616A..61R) Ramstedt, S., Mohamed, S., Olander, T., et al. 2018, A&A, 616, A61

(ref: 2017A&A...605A.126R) Ramstedt, S., Mohamed, S., Vlemmings, W. H. T., et al. 2017, A&A, 605, A126

(ref: 1972JOSA...62...55R) Richardson, W. H. 1972, Journal of the Optical Society of America (1917-1983), 62, 55

(ref: 2005ormo.book.....R) Roy, A. E. 2005, Orbital motion

(ref: 1988csmg.book.....R) Rufener, F. 1988, Catalogue of stars measured in the Geneva Observatory photometric system : 4 : 1988

(ref: 2008A&A...482..561S) Sacuto, S., Jorissen, A., Cruzalèbes, P., et al. 2008, A&A, 482, 561

(ref: 1992A&A...253L..33S) Sahai, R. 1992, A&A, 253, L33

(ref: 2022Galax..10...62S) Sahai, R., Sanz-Forcada, J., Guerrero, M., Ortiz, R., & Contreras, C. S. 2022, Galaxies, 10, 62

(ref: Schmid2017) Schmid, H. M., Bazzon, A., Milli, J., et al. 2017, A&A, 602, A53

(ref: 2018A&A...619A...9S) Schmid, H. M., Bazzon, A., Roelfsema, R., et al. 2018, A&A, 619, A9

(ref: 2018MNRAS.477.4200S) Snaid, S., Zijlstra, A. A., McDonald, I., et al. 2018, MNRAS, 477, 4200

(ref: 2010ApJ...723.1188S) Sokoloski, J. L. & Bildsten, L. 2010, ApJ, 723, 1188

(ref: 2009MNRAS.400.1945T) Tabur, V., Bedding, T. R., Kiss, L. L., et al. 2009, MNRAS, 400, 1945

(ref: 1997A&A...320L...1T) Tsuji, T., Ohnaka, K., Aoki, W., & Yamamura, I. 1997, A&A, 320, L1

(ref: 1998AJ....115.1212U) Urban, S. E., Corbin, T. E., Wycoff, G. L., et al. 1998, AJ, 115, 1212

(ref: 2019A&A...622A.120U) Uttenthaler, S., McDonald, I., Bernhard, K., Cristallo, S., & Gobrecht, D. 2019, A&A, 622, A120

(ref: 2022MNRAS.510.1204V) Van de Sande, M. & Millar, T. J. 2022, MNRAS, 510, 1204

(ref: 5725236) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science Engineering, 13, 22

(ref: 1998A&A...329..971V) Van Eck, S., Jorissen, A., Udry, S., Mayor, M., & Pernier, B. 1998, A&A, 329, 971

(ref: 2017A&A...601A..10V) Van Eck, S., Neyskens, P., Jorissen, A., et al. 2017, A&A, 601, A10

(ref: 2007A&A...474..653V) van Leeuwen, F. 2007, A&A, 474, 653

(ref: 2012cidu.conf...47V) VanderPlas, J., Connolly, A. J., Ivezic, Z., & Gray, A. 2012, in Proceedings of Conference on Intelligent Data Understanding (CIDU, 47–54

(ref: 2015ApJ...812...18V) VanderPlas, J. T. & Ivezić, Ž. 2015, ApJ, 812, 18

(ref: 2020SciPy-NMeth) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: 2020AJ....159..194V) Viswanath, G., Narang, M., Manoj, P., Mathew, B., & Kartha, S. S. 2020, AJ, 159, 194

(ref: Vlemmings2015) Vlemmings, W. H. T., Ramstedt, S., O’Gorman, E., et al. 2015, A&A, 577, L4

(ref: 2024A&A...681A..50W) Wallström, S. H. J., Danilovich, T., Müller, H. S. P., et al. 2024, A&A, 681, A50

(ref: 1998A&A...333L..51W) Weigelt, G., Balega, Y., Bloecker, T., et al. 1998, A&A, 333, L51

(ref: mckinney-proc-scipy-2010) Wes McKinney. 2010, in Proceedings of the 9th Python in Science Conference, ed. Stéfan van der Walt & Jarrod Millman, 56 – 61

(ref: 2008A&A...479L..21W) Wittkowski, M., Boboltz, D. A., Driebe, T., et al. 2008, A&A, 479, L21

(ref: 2017A&A...601A...3W) Wittkowski, M., Hofmann, K. H., Höfner, S., et al. 2017, A&A, 601, A3

(ref: 2004A&A...421..703W) Woodruff, H. C., Eberhardt, M., Driebe, T., et al. 2004, A&A, 421, 703

(ref: 2006AJ....132...50W) Wycoff, G. L., Mason, B. D., & Urban, S. E. 2006, AJ, 132, 50

(ref: 2009ASPC..418....3Y) Yamamura, I., Makiuti, S., Ikeda, N., et al. 2009, in Astronomical Society of the Pacific Conference Series, Vol. 418, AKARI, a Light to Illuminate the Misty Universe, ed. T. Onaka, G. J. White, T. Nakagawa, & I. Yamamura, 3

# Observation logs and photometry

This appendix regroups the observation logs of the data presented in the article. In Table [\[Tab:Log_SPHERE\]](#Tab:Log_SPHERE) we summarize the VLT/SPHERE-ZIMPOL observations used in the analysis.

|            |       |             |        |              |              |          |
|:-----------|:------|:------------|:-------|:-------------|:-------------|:---------|
| Date       | Time  | Object      | ND     | Filter 1     | Filter 2     | Seeing   |
|            | (UT)  |             |        |              |              | (arcsec) |
| 2015-07-08 | 02:28 | HD 121653   | OPEN   | CntH$\alpha$ | N_H$\alpha$  | 1.08     |
|            | 02:54 | HD 121653   | OPEN   | TiO_717      | Cnt748       | 1.30     |
|            | 03:16 | HD 121653   | OPEN   | Cnt820       | Cnt820       | 1.13     |
|            | 04:32 | $\pi^1$ Gru | ND_1.0 | Cnt820       | Cnt820       | 1.21     |
|            | 05:11 | $\pi^1$ Gru | OPEN   | CntH$\alpha$ | N_H$\alpha$  | 1.24     |
|            | 05:29 | $\pi^1$ Gru | ND_1.0 | TiO_717      | Cnt748       | 0.85     |
|            | 05:57 | $\pi^1$ Gru | ND_1.0 | TiO_717      | Cnt748       | 0.73     |
| 2015-09-22 | 04:40 | $\pi^1$ Gru | ND_1.0 | V            | N_R          | 1.02     |
|            | 04:54 | $\pi^1$ Gru | ND_1.0 | V            | N_R          | 0.95     |
|            | 05:20 | HD 220790   | ND_1.0 | V            | N_R          | 1.01     |
|            | 05:34 | HD 220790   | ND_1.0 | V            | N_R          | 0.94     |
| 2019-07-08 | 08:47 | $\pi^1$ Gru | OPEN   | CntH$\alpha$ | CntH$\alpha$ | 0.37     |
|            | 09:03 | HD 214987   | OPEN   | CntH$\alpha$ | CntH$\alpha$ | 0.43     |
|            | 09:20 | $\pi^1$ Gru | ND_1.0 | Cnt820       | Cnt748       | 0.49     |
|            | 09:51 | HD 214987   | ND_1.0 | Cnt820       | Cnt748       | 0.46     |
|            | 09:59 | HD 214987   | ND_1.0 | Cnt820       | Cnt748       | 0.43     |
| 2019-09-29 | 06:09 | $\pi^1$ Gru | OPEN   | CntH$\alpha$ | CntH$\alpha$ | 0.75     |
|            | 06:28 | HD 214987   | OPEN   | CntH$\alpha$ | CntH$\alpha$ | 0.32     |
| 2019-10-01 | 03:00 | $\pi^1$ Gru | ND_1.0 | Cnt820       | Cnt748       | 1.87     |
|            | 03:23 | HD 214987   | ND_1.0 | Cnt820       | Cnt748       | 1.80     |
| 2021-07-02 | 09:06 | $\pi^1$ Gru | OPEN   | CntH$\alpha$ | CntH$\alpha$ | 0.47     |
|            | 09:23 | HD 214987   | OPEN   | CntH$\alpha$ | CntH$\alpha$ | 0.62     |
| 2021-07-03 | 07:55 | $\pi^1$ Gru | ND_1.0 | Cnt820       | Cnt748       | 0.49     |
|            | 08:19 | HD 214987   | ND_1.0 | Cnt820       | Cnt748       | 0.25     |

Table notes: The characteristics of the ZIMPOL filters are available online: <https://www.eso.org/sci/facilities/paranal/instruments/sphere/inst/filters.html>

Table [2](#Tab:Log_ALMA) contains the simplified log of the ALMA observations.

|    Date    | Array configuration | Beam size (arcsec) |
|:----------:|:-------------------:|:------------------:|
| 2018-10-28 |    Intermediate     |   $0.24 - 0.25$    |
| 2018-10-31 |    Intermediate     |   $0.24 - 0.25$    |
| 2018-12-25 |       Compact       |   $0.77 - 0.87$    |
| 2019-03-19 |       Compact       |   $0.77 - 0.87$    |
| 2019-06-23 |      Extended       |       0.019        |
| 2019-07-06 |      Extended       |       0.019        |

: ALMA ATOMIUM observations of $\pi^1$ Gru.

Table notes: The extended configuration corresponds to ALMA configurations C43-8/C43-9, the intermediate groups C43-5/C43-6, and the compact configuration is the C43-2.

Finally, in Table [3](#Tab:archive_photometry), we list the archival photometry data used to characterize the $\pi^1$ Gru system, as well as their origin.

| Wavelength ($\mu$m) | Photometry (mJy)                 | References |
|:--------------------|:---------------------------------|:-----------|
| 0.55                | $1.29 \times 10^{4}$             | \(1\)      |
| 0.53                | $1.06 \times 10^{4}$             |            |
| 0.42                | $(9.63 \pm 0.12) \times 10^{2}$  |            |
| 101.95              | $2.33 \times 10^{4}$             | \(2\)      |
| 61.85               | $7.73 \times 10^{4}$             |            |
| 23.88               | $4.37 \times 10^{5}$             |            |
| 11.59               | $9.08 \times 10^{5}$             |            |
| 0.53                | $1.03 \times 10^{4}$             | \(3\)      |
| 0.42                | $8.55 \times 10^{2}$             |            |
| 0.53                | $(1.03 \pm 0.01) \times 10^{4}$  | \(4\)      |
| 0.42                | $(8.55 \pm 0.16) \times 10^{2}$  |            |
| 0.44                | $(9.23 \pm 0.17) \times 10^{2}$  | \(5\)      |
| 0.55                | $9.84 \times 10^{3}$             | \(6\)      |
| 0.44                | $1.48 \times 10^{3}$             |            |
| 0.53                | $(1.03 \pm 0.01) \times 10^{4}$  | \(7\)      |
| 0.42                | $(8.56 \pm 0.14) \times 10^{2}$  |            |
| 0.79                | $2.87 \times 10^{5}$             | \(8\)      |
| 0.76                | $5.58 \times 10^{5}$             |            |
| 0.76                | $1.97 \times 10^{5}$             |            |
| 0.65                | $5.57 \times 10^{4}$             |            |
| 0.62                | $2.19 \times 10^{4}$             |            |
| 0.55                | $8.06 \times 10^{3}$             |            |
| 0.55                | $8.19 \times 10^{3}$             | \(9\)      |
| 2.19                | $4.56 \times 10^{6}$             | \(10\)     |
| 1.25                | $2.96 \times 10^{6}$             |            |
| 0.88                | $1.39 \times 10^{6}$             |            |
| 0.69                | $1.54 \times 10^{5}$             |            |
| 0.55                | $8.19 \times 10^{3}$             |            |
| 0.44                | $1.50 \times 10^{3}$             |            |
| 0.55                | $1.21 \times 10^{4}$             | \(11\)     |
| 0.55                | $8.19 \times 10^{3}$             | \(12\)     |
| 0.55                | $1.21 \times 10^{4}$             |            |
| 0.55                | $8.19 \times 10^{3}$             |            |
| 0.55                | $8.81 \times 10^{3}$             |            |
| 0.55                | $2.19 \times 10^{4}$             |            |
| 0.55                | $8.73 \times 10^{3}$             | \(13\)     |
| 160.00              | $(5.55 \pm 1.15) \times 10^{3}$  | \(14\)     |
| 140.00              | $(9.31 \pm 0.83) \times 10^{3}$  |            |
| 90.00               | $(3.50 \pm 0.14) \times 10^{4}$  |            |
| 65.00               | $(6.39 \pm 0.63) \times 10^{4}$  |            |
| 0.23                | $2.68 \pm 0.03$                  | \(15\)     |
| 0.15                | $(2.77 \pm 0.12) \times 10^{-1}$ |            |
| 0.62                | $1.63 \times 10^{4}$             | \(16\)     |
| 0.55                | $7.38 \times 10^{3}$             |            |
| 0.48                | $2.74 \times 10^{3}$             |            |
| 0.44                | $1.10 \times 10^{3}$             |            |
| 0.55                | $1.10 \times 10^{4}$             | \(17\)     |
| 0.55                | $1.10 \times 10^{4}$             |            |
| 101.95              | $2.33 \times 10^{4}$             | \(18\)     |
| 61.85               | $7.73 \times 10^{4}$             |            |
| 23.88               | $4.37 \times 10^{5}$             |            |
| 11.59               | $8.90 \times 10^{5}$             |            |
| 11.59               | $9.08 \times 10^{5}$             |            |
| 0.55                | $8.19 \times 10^{3}$             | \(19\)     |
| 0.44                | $(1.95 \pm 0.02) \times 10^{3}$  | \(20\)     |

: Archival photometry of the $\pi^1$ Gru system.

| Wavelength ($\mu$m) | Photometry (mJy)                | References |
|:--------------------|:--------------------------------|:-----------|
| 4.89                | $(1.33 \pm 0.03) \times 10^{6}$ | \(21\)     |
| 3.52                | $(2.89 \pm 0.14) \times 10^{6}$ |            |
| 2.22                | $(4.44 \pm 0.17) \times 10^{6}$ |            |
| 1.26                | $(3.25 \pm 0.22) \times 10^{6}$ |            |
| 160.00              | $5.19 \times 10^{3}$            | \(22\)     |
| 140.00              | $7.66 \times 10^{3}$            |            |
| 90.00               | $3.47 \times 10^{4}$            |            |
| 65.00               | $3.12 \times 10^{4}$            |            |
| 61.85               | $7.73 \times 10^{4}$            | \(23\)     |
| 23.88               | $4.37 \times 10^{5}$            |            |
| 22.09               | $5.76 \times 10^{5}$            |            |
| 11.59               | $9.08 \times 10^{5}$            |            |
| 2.19                | $(5.69 \pm 1.47) \times 10^{6}$ |            |
| 2.19                | $4.21 \times 10^{6}$            | \(24\)     |
| 101.95              | $2.39 \times 10^{4}$            |            |
| 61.85               | $8.87 \times 10^{4}$            |            |
| 23.88               | $4.72 \times 10^{5}$            |            |
| 11.59               | $9.69 \times 10^{5}$            |            |
| 101.95              | $2.58 \times 10^{4}$            |            |
| 61.85               | $9.22 \times 10^{4}$            |            |
| 23.88               | $4.19 \times 10^{5}$            |            |
| 11.59               | $1.42 \times 10^{6}$            |            |
| 0.53                | $(1.03 \pm 0.01) \times 10^{4}$ | \(25\)     |
| 0.42                | $(8.55 \pm 0.16) \times 10^{2}$ |            |
| 2.19                | $4.73 \times 10^{6}$            | \(26\)     |
| 0.55                | $1.25 \times 10^{4}$            | \(27\)     |
| 0.44                | $1.40 \times 10^{3}$            |            |
| 0.53                | $(1.03 \pm 0.01) \times 10^{4}$ | \(28\)     |
| 0.42                | $(8.56 \pm 0.14) \times 10^{2}$ |            |
| 0.33                | $5.86 \times 10^{1}$            | (29, 31)   |
| 0.35                | $8.72 \times 10^{1}$            |            |
| 0.37                | $1.13 \times 10^{2}$            |            |
| 0.45                | $2.08 \times 10^{3}$            |            |
| 0.52                | $5.16 \times 10^{3}$            |            |
| 0.36                | $5.06 \times 10^{1}$            | (30, 31)   |
| 0.45                | $1.71 \times 10^{3}$            |            |
| 0.55                | $8.09 \times 10^{3}$            |            |

: Continued.

Table notes: For the line with blank references, the previous reference applies.

# Details of the SPHERE observations

Figure [11](#Fig:all_DoLP) (resp. Fig. [12](#Fig:all_DoLP_rms)) shows the complete set of observations of the $\pi^1$ Gru system with VLT/SPHERE-ZIMPOL for the DoLP (resp. DoLP rms).

![](all_ZIMPOL_DoLP)

![](all_ZIMPOL_DoLP_rms)

# True anomaly of the best fitted orbital solution at observed epochs

| Epoch (yr) | $\theta$ ($^{\circ}$) | Instrument |
|:-----------|:----------------------|:-----------|
| 2015.52    | 31.6                  | ZIMPOL     |
| 2015.73    | 44.7                  | ZIMPOL     |
| 2019.48    | 159.7                 | ALMA       |
| 2019.52    | 160.4                 | ZIMPOL     |
| 2021.51    | 193.5                 | ZIMPOL     |

: True anomaly for the best orbital solution of Sect. [\[SubSect:Orbit\]](#SubSect:Orbit), derived at the observation epochs of ALMA, and ZIMPOL.

[^1]: <http://vizier.cds.unistra.fr/vizier/sed/?submitSimbad=Photometry>

[^2]: <https://www.aavso.org>

[^3]: <https://nida.esac.esa.int/nida-cl-web/>

[^4]: <https://johannesbuchner.github.io/UltraNest/>

[^5]: <https://pypi.org/project/kepler.py/>

[^6]: <https://www.pas.rochester.edu/~emamajek/EEM_dwarf_UBVIJHK_colors_Teff.txt>

[^7]: <https://dx.doi.org/10.17909/5kem-8r51>

[^8]: <https://phoenix.astro.physik.uni-goettingen.de/>

[^9]: <http://dc.zah.uni-heidelberg.de/sdexter>

[^10]: Since C is likely to be located within the dust radiative-acceleration zone of A’s wind, we expect the latter’s expansion velocity in the vicinity of C to be a modest fraction of the wind’s terminal expansion velocity of 11 km s$^{-1}$.

[^11]: From the `G-Tomo` website: <https://explore-platform.eu/sda/g-tomo/> (login required, self-registration).

</paper>

Write the methods card for this paper.