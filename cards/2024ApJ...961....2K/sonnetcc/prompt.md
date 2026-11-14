# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...961....2K\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...961....2K",
 "title": "PASSAGES: The Wide-ranging, Extreme Intrinsic Properties of Planck-selected, Lensed Dusty Star-forming Galaxies",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Kamieneski, Patrick S.",
 "n_authors": 14,
 "arxiv_id": "2301.09746",
 "doi": "10.3847/1538-4357/acf930",
 "alma_projects_linked_by_archive": [
  "2015.1.01518.S",
  "2017.1.01214.S",
  "2019.1.01197.S",
  "2019.1.01636.S"
 ]
}
```

Paper text:
<paper>
#  PASSAGES: the wide-ranging, extreme intrinsic properties of $\boldsymbol{\it Planck}$-selected, lensed dusty star-forming galaxies

## Abstract

The PASSAGES (*Planck* All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts) collaboration has recently defined a sample of 30 gravitationally-lensed dusty star-forming galaxies (DSFGs). These rare, submillimeter-selected objects enable high-resolution views of the most extreme sites of star formation in galaxies at Cosmic Noon.

Here, we present

the first major compilation of strong lensing analyses using LENSTOOL for PASSAGES, including 15 objects spanning $z=1.1-3.3$, using complementary information from $0.6^{\prime\prime}$-resolution 1 mm Atacama Large Millimeter/submillimeter Array (ALMA) and $0.4^{\prime\prime}$

5 cm Jansky Very Large Array continuum imaging, in tandem with

1.6$\ensuremath{\mu}m$ *Hubble* and optical imaging with Gemini-S.

Magnifications range from $\mu = {2 - 28}$ (median $\mu=7$), yielding

intrinsic infrared luminosities of $L_{\rm IR} = {0.2 - 5.9} \times 10^{13}~L_{\odot}$ (median ${1.4}\times10^{13}~L_{\odot}$) and inferred star formation rates of ${170-6300}~M_{\odot}~{\rm yr}^{-1}$ (median ${1500}~M_{\odot}~{\rm yr}^{-1}$).

These results suggest that the PASSAGES objects comprise

some of the most extreme known starbursts, rivaling the luminosities of even the brightest unlensed objects,

further amplified by lensing.

The intrinsic sizes of far-infrared continuum regions

are

large ($R_{\rm e} = {1.7 - 4.3}$ kpc; median $3.0$ kpc) but consistent with

$L_{\rm IR}-R_{\rm e}$ scaling relations for $z>1$ DSFGs, suggesting a widespread spatial distribution of star formation.

With modestly-high angular resolution, we explore if these objects might be

maximal starbursts.

Instead of

approaching Eddington-limited

surface densities, above which radiation pressure will disrupt further star formation, they are safely sub-Eddingtonat least on global, galaxy-integrated scales.

# Introduction

Dusty star-forming galaxies (DSFGs) host some of the most extreme infrared luminosities in the known Universe, often in excess of $10^{12-13}~L_{\odot}$, reflecting star formation rates $>100-1000$ $\rm M_{\odot}~yr^{-1}$. Observed mainly during the peak of the cosmic star formation history at $z=1-4$, they are fundamental to our understanding of stellar mass assembly in the last 10 billion years (see reviews by (cite: Blain:2002aa; Casey:2014aa)).

The current galaxy evolution paradigm favors that DSFGs are progenitors of massive, quiescent elliptical galaxies (e.g., (cite: Lilly:1999aa; Brodwin:2008aa; Tacconi:2008aa; Daddi:2009aa; Toft:2014aa)), in part because of their association with galaxy over-densities and mergers.

However, numerous questions remain regarding the rapid conversion of cold gas reservoirs into new stars, often at star formation surface densities approaching theoretical maxima. Beyond this Eddington-like limit, stellar feedback should hinder or even quench subsequent star formation (cite: Scoville:2001aa; Scoville:2003aa; Murray:2005aa; Thompson:2005aa; Andrews:2011ab; Hodge:2019aa). Galaxies that are sub-Eddington when integrated over star-forming regions may still have Eddington-limited clumps of star formation (e.g., (cite: Simpson:2015ab; Barcos-Munoz:2017aa)).

Moreover, the predominant triggering mechanism for fueling this star formation has lingering uncertainties.

There is now plentiful evidence (observational and theoretical) that major galaxy mergers play an important role ((cite: Ivison:2002aa; Narayanan:2006aa; Narayanan:2010ab; Tacconi:2008aa), among many others), but cold-mode accretion, in which star formation in massive galaxies is fed by smooth infall of gas, has also been put forward as a viable explanation (cite: Keres:2005aa; Dekel:2009ab; Dekel:2009aa).

Answering these open questions absolutely necessitates resolutions corresponding to sub-galactic physical scales.

The past decade has ushered in the discovery of a substantial number of DSFGs that are amplified in submillimeter flux by strong gravitational lensing. Due to the steep drop-off in submillimeter number counts for high-$z$ galaxies (cite: Blain:1996aa; Negrello:2007aa), lensed DSFGs can be efficiently identified using a simple flux threshold. This was first demonstrated with large-area surveys undertaken with *Herschel* (cite: Negrello:2010aa; Negrello:2017aa; Conley:2011aa; Wardlow:2013aa; Nayyeri:2016aa), the South Pole Telescope (SPT; (cite: Vieira:2010aa; Weiss:2013aa; Mocanu:2013aa; Vieira:2013aa)), the Atacama Cosmology Telescope (ACT; (cite: Marsden:2014aa)), and more recently with *Planck* (cite: Planck-Collaboration:2015aa; Canameras:2015aa; Harrington:2016aa; Berman:2022aa).

Such lens samples are invaluable for the study of star formation at sub-kpc scales in the early Universe, thanks to the magnification in angular size afforded by strong lensing. Without lensing, the angular resolution of *Hubble* and *JWST* is only sufficient to resolve physical sizes at $z>1$ of 1 kpc or greater, so the critical $10-100$pc scales where star-forming and feedback processes are most relevant remain inaccessible. These samples offer unique opportunities for statistical studies of the foreground lensing population (e.g., (cite: Eales:2015ab; Amvrosiadis:2018aa))with implications for the halo mass function and mass density profiles for individual halosas the selection function depends only on intrinsic flux and magnification. This stands in contrast to the complex biases of lens detection methods based on arc morphology and foreground halo masses.

DSFGs also benefit from a strongly negative $K$-correction in the submillimeter (e.g. (cite: Blain:1993aa)), owing to steep Rayleigh-Jeans tails in the rest-frame far-IR regime of the spectral energy distribution (SED) from dust emission.

Increasing the distance to a galaxy of fixed luminosity would dim its observable flux at a given wavelength, were it not also the case that the increased redshift results in capturing shorter-wavelength (and therefore brighter) parts of the SED.

For example, at 850$\ensuremath{\mu}m$ in the observer-frame, these effects roughly equilibrate, and the flux for an object of fixed luminosity appears uniform from $z\approx1-8$ (e.g., (cite: Casey:2014aa)).

It is for this reason that DSFGs can be efficiently identified in the submillimeter regime up to high redshifts (modulo their evolving number density), and this partially explains the preponderance of submillimeter-bright galaxies (SMGs; (cite: Smail:1997aa; Hughes:1998aa; Barger:1998aa); review by (cite: Blain:2002aa)), a term now largely synonymous with DSFGs.

![](figs/postage_stamps_incl_RGB_Kamieneski2022.png)

The *Planck* All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts (PASSAGES) sample was introduced in (cite: Harrington:2016aa) and (cite: Berman:2022aa), with the scientific aims of exploring the gas fueling and induced starbursting phases in some of the most apparently IR-luminous objects yet identified ($\mu L_{\rm IR}  = 0.1 - 3.1 \times 10^{14} ~ L_\odot$, median $1.2 \times 10^{14} ~ L_\odot$; also (cite: Harrington:2021aa)). Even assuming a fiducial magnification factor of $\mu \approx 10$, typical for galaxy-scale strong lenses (e.g. (cite: Negrello:2017aa)), they remain intrinsically hyper-luminous, an order of magnitude higher than local ultra-luminous infrared galaxies (ULIRGs, (cite: Sanders:1996aa; Lonsdale:2006aa)), which appear to be the closest low-$z$ analog for DSFGs in terms of observed $L_{\rm IR}$.

Such objects with IR luminosity in excess of $10^{13} L_\odot$ have typically been referred to as hyper-luminous infrared galaxies, or HyLIRGs (cite: Cutri:1994aa).

As suggested by (cite: Berman:2022aa), the selection from an all-sky facility like *Planck* can identify the rarest, most extreme

star-forming galaxies. On one hand, strong gravitational lensing may boost the flux of fainter populations that would otherwise be undetected by an observation (the well-known magnification bias, e.g., (cite: Turner:1980aa; Turner:1984aa); (cite: Scranton:2005aa); (cite: Hildebrandt:2009aa)), but it may also be the case that selection from *Planck* reveals objects that would be detected within flux limits even without the modulation by lensing.

A detailed understanding of the PASSAGES objects requires refined and meticulously-constructed gravitational lens models. As the null geodesics that light rays from distant objects follow on their path to Earth depend on all matterindiscriminate of luminous vs. dark matterit is impossible to perfectly describe the exact deformation caused by lensing. While luminous, baryonic matter can offer great insight into the total underlying mass distribution, most gravitational lens modeling techniques hinge on characterizing the distortion of the background and determining what foreground mass profile is required to induce this distortion. Fortunately, lensing is achromatic, as photons of all wavelengths follow the same null geodesics. Images of different wavelengths (which presumably originate in slightly disparate spatial distributions in the source plane) offer complementary information by piercing different locations in the foreground lens.

In this context, robust lens models of strongly-lensed sources enable investigations of $z>1$ galaxies at a (source-plane) spatial resolution that is currently possible only for local, nearby objects.

Therefore, in this paper, we derive our first multi-wavelength-based lens models for 15 (out of 30) members of PASSAGES (all with spectroscopically-confirmed background redshifts). In so doing, we use optical and near-infrared information from *Hubble* and Gemini, (sub-)millimeter information from the Atacama Large Millimeter/submillimeter Array, and radio information from the *Karl G. Jansky* Very Large Array.

This paper is organized as follows: in Section [2](#sec:observations), we introduce the subset of the *Planck* lens sample discussed in this work and the relevant near-IR, submillimeter, and radio observations from which our lens models are derived. In Section [3](#sec:lensing), we review our approach to gravitational lens modeling with LENSTOOL, and discuss the identified lensing features and constraints for each object.

In Section [4](#sec:discussion), we examine some of the overall properties of this PASSAGES subsample, including de-lensed luminosity and intrinsic source sizes. Finally, we summarize our conclusions in Section [5](#sec:conclusions).

In this work, we adopt a

flat cosmological model with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_m = 0.3$, and $\Omega_\Lambda = 0.7$.

At the median source redshift of this work, $z\approx 2.2$, $1^{\prime\prime}$ corresponds to a physical scale of 8.27 kpc; at the median lens redshift, $z \approx 0.5$, $1^{\prime\prime}= 6.10$ kpc (cite: Wright:2006aa).

# Data

## Sample selection

PASSAGES consists of 30 high-$z$ objects that were identified from the *Planck* Catalogue of Compact Sources (cite: Planck-Collaboration:2014ab) and cross-identified with *Herschel* and *WISE*, the details of which are provided in (cite: Harrington:2016aa) and (cite: Berman:2022aa).

Here, we select a subset of 15 members of the larger current sample, restricting our focus to primarily those objects with both a simpler lensing morphology, arising from galaxy-scale or small group-scale lens potentials (Fig. [1](#fig:postage_stamps)), and sufficient multi-wavelength information.

These lower-mass deflectors account for more than 75% of the total collection of lensed objects from PASSAGES.

All of the objects in this subsample have been imaged with high angular resolution with optical/near-IR, radio, and (in most cases) submillimeter telescopes.

These data were sufficient to identify the families of lensed arcs and images that were responsible for the large submillimeter fluxes in these fields, in addition to the foreground lensing galaxies (which are predominately very faint at longer wavelengths).

We summarize this subsample of objects in Table [1](#tab:sample), and provide further details on each source in Appendix [7](#sec:object_notes).

Lens models for the remaining objectsmost of which are cluster-scale lenses or fields lacking sub-arcsecond-resolution millimeter imagingwill be described in future works.

Some models have already been presented publicly for PASSAGES, including: PJ020941.3 (*9io9*; (cite: Geach:2015aa; Geach:2018aa; Rivera:2019aa; Liu:2022ad); and this work), PJ105322.6 (G145.2+50.9; (cite: Frye:2019aa)), PJ105353.0 (G244.8+54.9; (cite: Canameras:2017aa; Canameras:2017ab; Frye:2019aa); and this work), PJ112714.5 (G165.7+67.0; (cite: Frye:2019aa; Pascale:2022aa)), PJ132630.3 (NAv1.195; (cite: Bussmann:2013aa); and this work), PJ132934.2/PJ132935.3 (the “Cosmic Eyebrow;" (cite: Diaz-Sanchez:2017aa)), and PJ142823.9 (HBootes03; (cite: Borys:2006aa)).

For the 3 previously-modeled targets studied independently in this work (in addition to PJ113921.7, for which a magnification is given in (cite: Canameras:2018ab)), we will examine any inconsistencies in Appendix [10](#sec:lens_model_comparison).

In deriving the lens models in this work, we take advantage of multi-wavelength observations from the Large Millimeter Telescope, the *Hubble Space Telescope*, Gemini South Observatory, the *Karl G. Jansky* Very Large Array, and the Atacama Large Millimeter/submillimeter Array, which we outline in this section. These observations serve to spectroscopically identify source redshifts, pinpoint lensed arcs associated with the *Planck* DSFGs, provide priors on the foreground lensing mass structure, and offer multiple sightlines through the deflecting foreground for the purpose of constraining lens mass models. Expanded details on this workflow are given in Section [3](#sec:lensing).

|    ID    |   RA$^a$    |  Dec.$^a$   | $z_{\rm s}^b$ | $z_{\rm lens}^c$ | Ref. |
|:--------:|:-----------:|:-----------:|:-------------:|:----------------:|:----:|
| PJ011646 | 01:16:46.77 | -24:37:01.9 |     2.125     |    0.555$^d$     |  1   |
| PJ014341 | 01:43:41.20 | -01:47:26.0 |     1.096     |      0.594       |  2   |
| PJ020941 | 02:09:41.30 | 00:15:59.0  |     2.554     |      0.202       | 3, 4 |
| PJ022633 | 02:26:33.98 | 23:45:28.3  |     3.120     |       0.41       |  2   |
| PJ030510 | 03:05:10.62 | -30:36:30.3 |     2.263     |     0.5$^*$      |  2   |
| PJ105353 | 10:53:53.15 | 05:56:18.8  |     3.005     |      1.525       | 4, 5 |
| PJ112713 | 11:27:13.44 | 46:09:24.1  |     1.303     |       0.42       |  2   |
| PJ113805 | 11:38:05.53 | 32:57:56.9  |     2.019     |       0.52       |  2   |
| PJ113921 | 11:39:21.74 | 20:24:50.9  |     2.858     |       0.57       |  2   |
| PJ132630 | 13:26:30.25 | 33:44:07.4  |     2.951     |      0.786       |  2   |
| PJ133634 | 13:36:34.94 | 49:13:13.6  |     3.254     |       0.26       |  2   |
| PJ144653 | 14:46:53.20 | 17:52:33.3  |     1.084     |      0.493       |  2   |
| PJ144958 | 14:49:58.59 | 22:38:36.8  |     2.153     |     0.4$^*$      |  2   |
| PJ160722 | 16:07:22.77 | 73:47:02.2  |     1.482     |       0.65       |  4   |
| PJ231356 | 23:13:56.64 | 01:09:17.7  |     2.217     |      0.560       |  2   |
|          |             |             |               |                  |      |

: Summary of PASSAGES objects included in this lens modeling study. A brief description of each object is provided in Appendix [7](#sec:object_notes).

## Spectroscopic source redshifts

Spectroscopic redshifts of background objects are critical for deriving accurate lens models and inferring intrinsic properties in the source plane.

An initial follow-up of candidate lensed objects was performed with 1.1 mm AzTEC imaging and 3 mm Redshift Search Receiver (RSR) spectroscopy with the Large Millimeter Telescope (LMT), described in (cite: Harrington:2016aa) and (cite: Berman:2022aa).

The wide bandwidth of RSR ($73 - 111$ GHz) captures at least two CO transitions at $z > 3.15$, and also in a very narrow window around $z\approx 2.2$ (cite: Yun:2015aa), which accounts for 3 members of this subsample (PJ011646, PJ133634, and PJ144958).

The photometrically-supported redshifts of all other fields were later confirmed spectroscopically to high precision with the detection of more than 160 redshifted CO and 35 \[CI\] emission lines by single-dish facilitiesincluding the Green Bank Telescope (GBT), the IRAM 30 m telescope, and the Atacama Pathfinder Experiment (APEX)as summarized by (cite: Harrington:2021aa).

## HST WFC3/IR

All objects in this work were observed with the IR channel of the Wide Field Camera 3 (WFC3) on the *Hubble Space Telescope* (*HST*) during Cycle 24 (Program GO-14653, PI: J. Lowenthal), except for PJ105353, which was observed in Cycle 23 (Program GO-14223, PI: B. Frye; (cite: Frye:2019aa)).

Full details of the observation and reduction of the *HST* images are given in Lowenthal et al., in prep., but we provide a brief summary here.

The F160W wide-band filter ($\lambda_{\rm effective} = 1.54 \ensuremath{\mu}m$, $H$-band) was used to image each member of our sample for one orbit each (with an additional orbit in F110W, $1.15 \ensuremath{\mu}m$, for PJ105353). Each orbit was composed of a 5-point dithering pattern for 500 seconds each, which were combined during data reduction with *astrodrizzle* (`final_pixfrac` of 0.9). A fiducial $5\sigma$ sensitivity of $m_{AB} \approx 28.7$ was reached for an unresolved point source. Due to the sub-pixel dithering setup ($0.572^{\prime\prime}$ spacing), the native pixel scale was improved by a factor of 2 to $0.065^{\prime\prime}$ (with a point spread function FWHM = $0.2^{\prime\prime}$). Before combining, the individual exposures were pipeline-reduced, flat-fielded, and calibrated with standard Space Telescope Science Institute routines (e.g., (cite: Deustua:2016aa)).

The absolute astrometry of the drizzle-combined exposures was subsequently calibrated using the position of stars within the image frame from the *Gaia* Data Release 1 catalog (cite: Gaia-Collaboration:2016aa). For fields containing at least 3 *Gaia* objects detected within the *HST*/WFC3 field-of-view ($141^{\prime\prime}\times 125^{\prime\prime}$), we can apply a 3-dimensional astrometric solution. In fields with fewer matched *Gaia* detections, we apply only 2-dimensional shifts in RA/Dec.

## ALMA 1.1 mm continuum

We obtained

Band 6 ($1.1 - 1.4$ mm, $211 - 275$ GHz) observations with the Atacama Large Millimeter/submillimeter Array (ALMA) during Cycle 5 (Program 2017.1.01214.S, PI: M. Yun) for eleven of these 15 targets, executed between March 22 and May 5, 2018 (with the exception of one executed on August 24, 2018).

Additional details of the program are presented in (cite: Berman:2022aa), but we summarize relevant details here.

A default continuum setup was employed to target rest-frame FIR/sub-mm dust emission in the DSFGs, with a total bandwidth of 8 GHz ($250-254$ GHz and $266-270$ GHz).

A target angular resolution of $0.4 - 1.0^{\prime\prime}$ and largest resolvable angular scale of 6$^{\prime\prime}$ was requested, with a target sensitivity of 0.1 mJy over the full bandwidth.

The minimum baseline utilized was $15$ meters, and the maximum baselines ranged from $484 - 784$ meters, enabling natural-weighted synthesized beam sizes of $\sqrt{\theta_{\rm min} \theta_{\rm maj}} \approx 0.4 - 0.8^{\prime\prime}$.

Total on-source integration times ranged from 17 - 21 minutes, resulting in achieved sensitivities of $1\sigma \approx 0.07 - 0.33$ mJy.

Superb weather conditions were achieved for the observations, with the mean precipitable water vapor ranging between $0.7-1.7$ mm.

As one exception, PJ105353 was observed separately with Band 6 during Cycle 3 (Program 2015.1.01518.S, PI: N. Nesvadba)

and with Band 7 ($0.8 - 1.1$ mm, $275 - 373$ GHz) during Cycle 7 (Program 2019.1.01636.S, PI: M. Yun).

As the Band 7 observation had an angular resolution closer to that of our Cycle 5 program than the Band 6 observations (0.35$^{\prime\prime}$ vs. 0.07$^{\prime\prime}$; (cite: Canameras:2017aa; Canameras:2017ab)), we opt to use the Band 7 image for our analysis in this work

so as to mitigate the effects of highly disparate beams on derived magnifications. However, we refer to the Band 6 observation when deriving a lens model; see Appendix [7](#sec:object_notes).

The 1 mm fluxes from ALMA recovered those measured with the LMT/AzTEC bolometer camera, suggesting that the higher-resolution interferometric images do not resolve out significant flux at large angular scales (see Figure 8 and relevant discussion in (cite: Berman:2022aa)), ensuring a complete assessment of lensed arcs[^1].

This is important as, throughout this work, we use lensing magnifications at 1 mm as a proxy for the total infrared magnification, e.g. in tabulating intrinsic luminosities in Table [3](#tab:effective_radii).

In theory, source-plane structure (and in turn magnification) can vary continuously with infrared wavelength, but this is clearly not feasible to measure at high spectral resolution in practice.

## JVLA 6 GHz

All members of this sub-sample were observed with the *Karl G. Jansky* Very Large Array (JVLA)

(Program 18A-399, PI: P. Kamieneski).

The observations were carried out between March 29 and April 30, 2018 in 13 execution blocks totaling 38.9 hours, each targeting two PASSAGES objects.

All objects were observed at 5 cm with C-band ($4 - 8$ GHz) and full polarization for 1.5 hours each. With the WIDAR correlator configured to 3-bit sampling, the effective bandwidth of the two basebands is 4 GHz, centered at 6 GHz.

The targets were scheduled to be observed in pairs at similar right ascensions, alternating between the two during 3-hour tracks, to improve $uv$-coverage. The most extended A-configuration was used to provide optimal resolution ($\sqrt{\theta_{\rm min}\theta_{\rm maj}} \approx 0.3-0.7^{\prime\prime}$, median $0.4^{\prime\prime}$). With maximum and minimum baselines of 36.4 km and 0.68 km, the largest recoverable angular scale was 8.9$^{\prime\prime}$, which we assume to be larger than most PASSAGES objects.

The 6 GHz continuum data were reduced using the Common Astronomy Software Applications, CASA (cite: McMullin:2007aa). Basic flagging and calibration were performed with the VLA Calibration pipeline (version 2018.1). Each object was first imaged using natural weighting (maximal sensitivity at the expense of slightly degraded resolution). After creating a ‘dirty’ image with no deconvolution, the sky noise level is estimated, before using the CLEAN algorithm (cite: Hogbom:1974aa) to deconvolve down to a $2\sigma$ threshold.

Achieved sensitivities ranged from $1\sigma = 2.6 - 11.7~\mu$Jy (median 2.9 $\mu$Jy).

For fields where higher resolution is desired, we also created images with Briggs weighting (typically `robust` $= 0.5$).

Photometry for natural-weighted 6 GHz imaging of the background DSFGs is performed using the flood-filling source extraction software BLOBCAT (cite: Hales:2012aa). Gravitational lensing renders the majority of the PASSAGES sample to be resolved, extended sources, inconsistent with simple 2-dimensional Gaussian profiles. For this reason, we use the uncorrected integrated surface brightness when performing continuum photometry (see discussion in §3.3 of (cite: Hales:2012aa)). The total observed

6 GHz flux ($S_{\rm 6 GHz}$) is reported in Table [\[tab:effective_radii_VLA\]](#tab:effective_radii_VLA).

## Gemini $r'$ & $z'$

We have additionally obtained Gemini Multi-Object Spectrograph (GMOS) $r'$ and $z'$ imaging for eight (out of 15) of the members of this sample as part of Gemini-South programs GS-2018A-Q-216 (PI: J. Lowenthal; PJ011646, PJ014341, PJ144653, PJ231356), GS-2018B-Q-123 (PI: J. Lowenthal; PJ020941, PJ030510), and GS-2020A-Q-217 (PI: J. Lowenthal, PJ113921, PJ144958).

In tandem with our $H$-band images from *HST*, this three-color imaging (shown in Fig. [1](#fig:postage_stamps)) allows us to identify multiple images, separate foreground and background objects, and identify lensing groups and clusters with techniques such as the Red Cluster Sequence, which is effective to at least $z=1.4$ (cite: Gladders:2000aa; Gladders:2005aa). Each target was observed in the $r'$ filter for 1500s to achieve $S/N = 10$ for an object with $r'=25.0$, and in the $z'$ filter for 2100s to achieve $S/N=10$ for a $z'=23.0$ object. These limiting magnitudes are each chosen to be one magnitude fainter than a typical early-type L$^\star$ cluster member at $z\sim 0.5$ (cite: Gladders:2005aa), in order to capture the foreground objects most likely to be responsible for lensing. Each field was observed with dithered 300-second exposures to cover chip gaps within the GMOS $5.5^\prime\times5.5^\prime$ field-of-view. The observations have a pixel scale of 0.080$^{\prime\prime}$.

Observations were taken on July 13-14, 2018 for semester 2018A, on October 7, 2018 for semester 2018B, and on February 20, 2020 for semester 2020A.

Absolute image astrometry was corrected in the same manner as the *HST* images using Gaia catalog DR1 before creating RGB images (see Fig. [1](#fig:postage_stamps)).

Images were bias-subtracted and flat-fielded using the Data Reduction for Astronomy from Gemini Observatory North and South (DRAGONS[^2]) software, as will be described in Cooper et al., in prep.

# Gravitational lens modeling with LENSTOOL

All gravitational lens modeling in this work was performed with the publicly-available software, LENSTOOL[^3] (cite: Kneib:1993aa; Kneib:1996aa; Jullo:2007aa; Jullo:2009aa).

LENSTOOL uses parametric forms to model the foreground lens mass distribution that contributes sufficiently to deflect light from background objects.

This deflection is described by the simple lens equation, $$\begin{equation}
\boldsymbol{\beta} = \boldsymbol{\theta} - \frac{D_{LS}}{D_S} \boldsymbol{\hat{\alpha}(\xi)},
\end{equation}$$ where $\boldsymbol{\beta}$, $\boldsymbol{\theta}$, and $\boldsymbol{\hat{\alpha}(\xi)}$ are the vector quantities describing (respectively) the intrinsic angular position of the source, the observed angular position after deflection, and the deflection angle at impact parameter $\boldsymbol{\xi}$. $D_S$ and $D_{LS}$ are the angular diameter distances to the source plane and from the lens plane to the source plane, respectively.

The deflection angle itself is the integral of surface mass density in the lens plane: $$\begin{equation}
\boldsymbol{\hat{\alpha}(\xi)} = \frac{4G}{c^2} \int_{\mathds{R}^2} d^2 \xi' ~\Sigma(\boldsymbol{\xi'})\boldsymbol{\frac{\xi - \xi'}{|\xi - \xi'^2|}}
\end{equation}$$ where $G$ is the Newtonian gravitational constant and $c$ is the speed of light. $\Sigma$ is surface mass density evaluated at the location of the impact parameter $\xi$, after projecting the volumetric density distribution on to the lens plane (cite: Schneider:1992aa).

Thus, provided the locations $\boldsymbol{\theta}$ (and redshifts) of multiple images identified visually by the user, one can use this formalism to model the distribution of mass in the lens plane.

The process of isolating image families is usually iterative, where the model may predict unidentified image locations. When confirmed, these added images can be incorporated into the model for further refinement. However, for many of the lensed systems in this sample, which are predominantly galaxy-scale lenses, identifying image families can be straightforward. We describe this step in more detail in the following section, and label the image systems in Fig. [1](#fig:postage_stamps).

The only information included in the derived lens models for LENSTOOL are the multiple image catalogs supplied by the user, and the parametric mass models are likewise defined by the user. The input image catalogs we constructed are provided in Table [13](#tab:lensconstraints). For some lenses, this can grossly oversimplify the information provided by imaging itself, such as the extended ring-like features seen in ALMA and *HST* observations for many PASSAGES objects (e.g., Fig. [1](#fig:postage_stamps)). When these arcs and rings are clumpy, it may be possible to identify sub-images, or smaller-scale features that appear inside the broader multiple images. For interferometric imaging, this may be challenging, as certain spatial scales are filtered out, and correlated noise can introduce spurious point-like sources. As lens models for the PASSAGES sample are continually refined in the future, we will ideally incorporate information about extended rings, which often closely trace the critical curve.

Lens models for most cluster-scale members of the PASSAGES sample will be formulated using both parametric modeling (e.g. LENSTOOL) and light-traces-mass models, in an approach similar to (cite: Zitrin:2009aa; Zitrin:2015aa) and (cite: Frye:2019aa)[^4], the latter of which covers several members of the full PASSAGES sample that were identified independently by (cite: Canameras:2015aa). Here, we narrow our focus primarily to the galaxy-scale and group-scale lenses, which are more likely to be adequately described by simpler parametric mass models than larger, cluster-scale lenses.

|  |  |
|:---|:---|
| ![image](figs/PJ011646_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ011646_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ014341_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ014341_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ020941_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ020941_VLA_lens_model_SP_contours.png) |
|  | ![image](figs/PJ022633_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ030510_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ030510_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ105353_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ105353_VLA_lens_model_SP_contours.png) |

|  |  |
|:---|:---|
|  | ![image](figs/PJ112713_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ113805_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ113805_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ113921_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ113921_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ132630_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ132630_VLA_lens_model_SP_contours.png) |
|  | ![image](figs/PJ133634_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ144653_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ144653_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ144958_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ144958_VLA_lens_model_SP_contours.png) |

|  |  |
|:---|:---|
|  | ![image](figs/PJ160722_VLA_lens_model_SP_contours.png) |
| ![image](figs/PJ231356_ALMA_lens_model_SP_contours.png) | ![image](figs/PJ231356_VLA_lens_model_SP_contours.png) |

## Visual identification of multiple image families

Identifying multiple image families with long-wavelength, high-resolution radio/millimeter imaging can be easier than at shorter wavelengths, as the ubiquity of dust in the background DSFGs leads to strong obscuration in the optical regime and a much brighter rest-frame far-IR arising from the peak of the dust SED. Moreover, foreground galaxies are largely filtered out at longer wavelengths. There is a notable exception of radio AGN and jets propagating from the massive elliptical galaxies in the lens plane (e.g., (cite: Fanaroff:1974aa), (cite: Smith:1986aa)), which can contaminate image classification. For this reason, our method of identifying image families relies on the combined information of optical/near-IR imaging from *HST*, millimeter imaging

with ALMA, and radio imaging from the JVLA.

This coverage spanning 0.6 $\mu$m to 6 cm gives us a large number of unique sightlines through foreground mass distributions, which we use to constrain our models.

The interferometric observations by ALMA and the JVLA do not directly probe the sky brightness pattern, but rather the complex visibility, which is a 2-dimensional Fourier transform of the brightness pattern. Translating the visibilities into an image introduces correlated noise, which is a function of the sampling pattern of the interferometer. For this reason, a number of works have performed gravitational lens modeling in the visibility $uv$-plane instead of the surface brightness plane (including (cite: Bussmann:2012aa; Bussmann:2015aa; Hezaveh:2013aa; Spilker:2016aa)).

In this work, as we are merging information from traditional optical telescopes and radio interferometers, we apply lens modeling to the transformed image plane. This has the additional benefit of improved computational efficiency. As a proof of concept, (cite: Dye:2018aa) used both image-plane and visibility-plane lens modeling towards ALMA imaging of six *Herschel*-detected lenses for direct comparison, and found minimal difference in the derived parameters and source reconstructions, and derived total magnifications were in agreement within 1$\sigma$ uncertainties. (cite: Dye:2018aa) note that there might be greater disparities in cases where the visibility sampling is sparse, but we do not expect this to be a major concern in our case.

Both ALMA and JVLA observations make use of a large number of antennas and long integration times to maximize $uv$-coverage (and as mentioned previously, JVLA observations of fields were carried out in pairs during 3-hour tracks to ensure more distributed $uv$-sampling).

Each lensed image family of multiplicity $n$ provides $2(n-1)$ constraints to be used in the optimization[^5]. If relative fluxes (or equivalently, solid angle) of each family member are included, this adds an extra $n-1$ constraints (cite: Blandford:1992aa). For most models herein, we use only image positions, which helps to minimize the systematic uncertainty introduced in the model. However, some lensed systems on galaxy- or group-scales with few multiple image constraints are poorly suited for strong lens modeling (see e.g. (cite: Limousin:2009aa; Verdugo:2014aa)). In such cases, it may be necessary to include additional information in the model, which we discuss in the following section where applicable.

## Lens model mass profile optimization

LENSTOOL employs Bayesian Markov chain Monte Carlo (MCMC) methods to thoroughly explore the posterior distribution for each supplied parameter in order to find a best-fit solution. While this method is more impervious to local $\chi^2$ minima, it is more computationally expensive than other minimization techniques when the parameter space is complex. Because of the possible parameter degeneracies and non-Gaussian distributions that can arise in the underlying posterior, it is usually highly beneficial to employ MCMC. Performing this optimization in the source plane (i.e. minimizing separation between image family members once ray-traced to the source plane, rather than making the comparison in the image plane) can reduce the requisite computational time. However, this also results in lower precision and poorer estimation of model uncertainties. As the PASSAGES objects in this work are primarily galaxy-scale lenses, fewer free parameters are involved than cluster-scale systems, so we perform all optimization in the image plane unless otherwise noted. Another quantification of goodness-of-fit can be the root-mean-square of the image-plane observed vs. model-reconstructed image locations, as this is independent of the positional uncertainty, therefore facilitating an easier comparison of different lens models (e.g. (cite: Caminha:2016aa)).

One of the priors provided to LENSTOOL is the functional form of each mass potential, including the relevant free parameters (each of which has their own prior distribution, specified by the user).

For these models, we use a singular isothermal ellipsoid (SIE) potential as a basis for all mass profiles (cite: Kormann:1994aa). With this model, the normalized surface mass density, or convergence $\kappa$, takes the form $$\begin{equation}
\kappa(x_1, x_2) = 
\frac{
\sqrt{f}
}
{
2\sqrt{x_1^2 + f^2 x_2^2},
}
\end{equation}$$ where $f \equiv b/a$ is the axis ratio (for semi-major and semi-minor axes $a$ and $b$; $0 < f \leq 1$) and $x_1$ and $x_2$ are normalized Cartesian coordinates.

As noted by (cite: Treu:2010aa), the SIEa generalization of the singular isothermal sphere (SIS) where 3-dimensional density follows $\rho \sim r^{-2}$appears to be the simplest profile that effectively describes galaxy-scale strong lensing configurations (see also work by (cite: Treu:2004aa; Koopmans:2006aa; Koopmans:2009aa; Barnabe:2009aa)).

A number of studies of lensed DSFGs have had success using this profile, including

(cite: Fu:2012aa), (cite: Bussmann:2012aa; Bussmann:2015aa), (cite: Hezaveh:2013aa), (cite: Calanog:2014aa), and (cite: Spilker:2016aa).

The profile can be fully parameterized by position ($\alpha$ and $\delta$, or $x$ and $y$), projected 2-dimensional ellipticity $e = (a^2 - b^2) / (a^2 + b^2)$, position angle (PA or $\theta$; measured counterclockwise from east), and velocity dispersion, $\sigma_{\rm SIE}$. This velocity dispersion is generally in good agreement with observable stellar velocity dispersions for elliptical galaxy lenses (e.g., (cite: Bolton:2008ab) for $\sigma\approx 175 - 400$ km s$^{-1}$).

For the majority of the galaxy-scale lenses in the PASSAGES sample, the arcs and rings are visible in the intermediate range between core and cut radii (e.g., Table [2](#tab:lensproperties)), and so these parameters of pseudo-isothermal elliptical mass distributions (PIEMD; (cite: Kassiola:1993aa)) and dual pseudo-isothermal elliptical distributions (dPIE; (cite: Eliasdottir:2007aa)) would be poorly constrained.

As galaxy-scale systems have comparatively fewer constraints than clusters that are rich with multiply-imaged arcs, the number of available free parameters is usually quite limited. In some cases,

this necessitates a simple, single SIE potential, with free parameters including the location of the profile center, the velocity dispersion, and the ellipticity (and associated position angle). Where possible (and appropriate), a secondary singular isothermal ellipsoidal/spheroidal potential can be added to account for the effect of any secondary deflectors. This 2nd-order correction is similar to including an external shear field induced by underlying large scale structure (see review of weak lensing by (cite: Bartelmann:2001aa)), which is a common approach to modeling galaxy-scale lenses, including for a number of PASSAGES objects (e.g., (cite: Geach:2015aa; Geach:2018aa; Rivera:2019aa)). In some galaxy-scale cases, the location of the profile center is fixed to the centroid of the visible baryonic component revealed by *HST*, which reduces the number of free parameters[^6]. An upper limit is generally imposed on the ellipticity of $e < 0.75$, following (cite: Acebron:2017aa). Theoretical predictions by (cite: Despali:2017ac) indicate that $\approx 95\%$ of galaxy-scale, $10^{12}~M_{\odot}$ halos at $z\sim0.5$ will have a projected ellipticity less than $e = 0.5$.

In our sample, there are several cases where the optimized lens models have ellipticity values larger than expected (up to $e \sim 0.7$).

This suggests that these models may benefit from additional complexity and/or substructure (e.g. (cite: Johnson:2014aa)), but this is often limited by the small number of constraints presently available.

The results of our MCMC optimization are summarized in Table [6](#tab:lensmodels), including the positional center of each mass profile (relative to reference coordinates), and the ellipticity $e$, position angle $\theta$, and velocity dispersion $\sigma$ in km s$^{-1}$. For each lensing field, we provide at least two optimized solutions, labeled *median* and *best*. The *median* solution comprises the median values of the MCMC-sampled posterior for each parameter, with associated asymmetric uncertainties from the inner 68% confidence interval of the distribution, whereas the *best* solution is only those MCMC realizations with the highest likelihood (or lowest $\chi^2$). In some cases, the *mode* solution is also provided, comprising the peak of the probability density for each parameter. This latter solution may be preferable in situations where the posterior distribution is multimodal, for which the median may lie in troughs between multiple peaks in parameter space. Additionally, the mode solution can be useful when a parameter is only weakly constrained in the model, such that the choice of parameter bounds can have a strong impact on the distribution. Here, the median might be sensitive to these bounds, while the mode might be more resistant.

In general, we select the median of the posterior distribution, which is less prone to local likelihood maxima, where small perturbations to any parameter can drastically reduce the likelihood. However, in the ideal case, the median, mode, and best solutions would be in agreement within error, but this requires a parameter space that is sufficiently simple.

Altogether, the median $\chi^2$ value for all median solutions[^7] is $\tilde{\chi}_{\rm med}^2 = {1.9}$, and the median for the best solutions is $\tilde{\chi}_{\rm best}^2 = { 0.3}$. This suggests that the goodness-of-fit of our lens models are reasonable, in aggregate, although the individual $\chi^2$ values are influenced by the complexity of the foreground environment and the amount of lensing evidence available from current observations.

The lensing models we select for analysis are shown in Fig. [2](#fig:model_SP), which depicts the observed image-plane structure relative to the model-reconstructed image-plane and source-plane structure, the latter of which we discuss in the next section. Qualitatively, the image-plane reconstructions are in agreement with the observations, mainly in that they reproduce the correct number of multiple images.

## Source-plane reconstruction

With an optimized potential model in hand, we can invert the observed arcs to approximate the unlensed brightness distribution in the source plane using the `cleanlens` function of LENSTOOL. Fundamentally, this inversion can be quite trivial, in that it consists only of ray-tracing a (usually sub-sampled) image plane distribution to the lens plane, computing the deflection vectors based on the lens mass potential, and continuing until the source-plane redshift is reached. Typically, sub-pixel sampling is also used for the source plane. The direction and magnitude of the deflection are determined by a surface integral of the surface mass density, weighted by the distance from where each light ray intersects the lens potential (see e.g., (cite: Schneider:1992aa), (cite: Refsdal:1994aa)).

While the optimization and goodness-of-fit measurement with LENSTOOL is done in the image plane,

one of the tests that we use to evaluate the goodness-of-fit of a lens model is evaluating the spatial coincidence of the source plane reconstruction of individual multiple images. Every observation has an intrinsic point spread function (PSF) with which the image-plane structure is convolved, which is carried through as a distorted, non-uniform PSF in the source plane. This will be slightly different for each individual multiple image (or even dramatically different, in the case of a source near the lensing caustics; see e.g. (cite: Sharma:2018aa; Sharma:2021aa)).

These individual reconstructions are compared visually

to ensure that the total reconstruction of all image-plane light is appropriate and self-consistent.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Field | $\mu_{\rm 1mm}$ | $\mu_{\rm 6 GHz}$ | $\theta_{\rm Ein}$ | $M_{<\theta_{\rm E}}$ |  |
|  |  |  | \[$^{\prime\prime}$\] | \[$10^{11} M_{\odot}$\] |  |
|  |  |  |  |  |  |
| PJ011646 | $7.0^{+0.3}_{-0.3}$ | $7.0^{+0.4}_{-0.3}$ | $2.37^{+0.04}_{-0.03}$ | $15.4 \pm 0.3$ |  |
| PJ014341 | $7.1^{+2.2}_{-2.2}$ | $5.9^{+2.0}_{-1.4}$ | $0.53^{+0.07}_{-0.09}$ | $1.3 \pm 0.3$ |  |
| PJ020941 | $10.5^{+4.2}_{-3.2}$ | $12.0^{+3.7}_{-3.3}$ | $2.55^{+0.14}_{-0.20}$ | $6.6 \pm 0.6$ |  |
| PJ022633 |  | $28.2^{+10.7}_{-11.9}$ | $3.61^{+0.36}_{-0.30}$ | $24.7 \pm 3.2$ |  |
| PJ030510 | $2.2^{+0.6}_{-0.5}$ | $2.6^{+1.0}_{-1.0}$ | $0.58^{+0.12}_{-0.15}$ | $0.8 \pm 0.3^*$ |  |
|  |  |  |  | $[0.5-1.1]$ |  |
| PJ105353 | ${7.6^{+0.5}_{-0.8}}^{**}$ | $7.9^{+0.6}_{-0.8}$ | $0.71^{+0.03}_{-0.05}$ | $3.6 \pm 0.3$ |  |
| PJ112713 |  | $4.5^{+0.5}_{-0.6}$ | $0.58^{+0.07}_{-0.04}$ | $0.8 \pm 0.1$ |  |
| PJ113805 | $2.8^{+0.4}_{-0.3}$ | $4.4^{+1.2}_{-1.0}$ | $0.40^{+0.06}_{-0.04}$ | $0.4 \pm 0.1$ |  |
| PJ113921 | $4.8^{+1.3}_{-0.9}$ | $8.6^{+2.8}_{-2.6}$ | $0.71^{+0.47}_{-0.39}$ | $1.3 \pm 1.1$ |  |
| PJ132630 | $4.3^{+0.7}_{-0.5}$ | $11.4^{+4.5}_{-2.2}$ | $1.78^{+0.21}_{-0.14}$ | $11.0 \pm 1.5$ |  |
| PJ133634 |  | $8.3^{+4.2}_{-1.9}$ | $1.17^{+0.11}_{-0.08}$ | $1.7 \pm 0.2$ |  |
| PJ144653 | $3.9^{+0.6}_{-0.7}$ | $7.7^{+1.5}_{-2.0}$ | $0.82^{+0.05}_{-0.04}$ | $1.6 \pm 0.1$ |  |
| PJ144958 | $10.1^{+5.7}_{-4.7}$ | $13.6^{+15.7}_{-6.7}$ | $6.52^{+1.31}_{-1.16}$ | $84.0 \pm 22.5^*$ |  |
|  |  |  |  | $[43.3-126.0]$ |  |
| PJ160722 |  | $6.8^{+2.1}_{-1.3}$ | $1.00^{+0.11}_{-0.08}$ | $4.0 \pm 0.5$ |  |
| PJ231356 | $6.1^{+1.2}_{-1.2}$ | $^\dagger$ | $2.05^{+0.26}_{-0.23}$ | $11.5 \pm 1.9$ |  |
|  |  |  |  |  |  |
| *Literature* | $\mu_{870\mu {\rm m}}$ |  | $\theta_{\rm Ein}$ | $M_{<\theta_{\rm E}}$ |  |
|  |  |  | \[$^{\prime\prime}$\] | \[$10^{11} M_{\odot}$\] |  |
|  |  |  |  |  |  |
| PJ105322$^a$ | $7.6 \pm 0.5$ |  | $5.9$ | 120.3 |  |
| PJ112714$^b$ | $29.4 \pm 5.9$ |  | $13$ | 283.7 |  |
| PJ132302$^c$ | $11.2  \pm 0.7$ |  | $\lesssim 13$ | $\lesssim 380.1$ |  |
| PJ132934$^d$ | $11  \pm 2$ |  | $11.0 \pm0.4$ | $267.9 \pm 13.8$ |  |
| PJ142823$^e$ | $3.0  \pm 1.5$ |  | $0.10 \pm 0.03$ | $0.13 \pm 0.06$ |  |
| PJ154432$^f$ | $14.7  \pm 0.8$ |  | $7$ | 152.6 |  |
| PJ160918$^g$ | $15.4  \pm 1.0$ |  |  |  |  |

: Summary of strong lensing properties derived from the models described in Table [6](#tab:lensmodels), including weighted total magnification $\mu_{\rm tot}$ for different wavelengths and the equivalent Einstein radius $\theta_{\rm Ein, eq}$. Under the *Literature* heading, these values are listed for other PASSAGES objects not included in this study that have published lens models. Here, magnifications are derived for 870 $\mu$m, and Einstein radii are defined as the radius of the circle with equivalent area to that inside the critical curve (see discussion in Section [3.5](#sec:Einstein_radius)).

Table notes: $^*$ Only a preliminary photometric redshift measurement (see Table [1](#tab:sample)), so approximate bounds of enclosed masses are also given for a set of redshifts representative of the range of the full sample. $^{**}$ 870 $\mu$m (Band 7) measurement (see §[2.4](#sec:alma_cont)). The 1 mm magnification is $\mu \approx 11.8 \pm 2.1$ for the $0.07^{\prime\prime}$ image, but the 870 $\mu$m value is adopted for $\mu_{\rm dust}$ to more closely match the imaging limitations for the other targets.

$^\dagger$ 6 GHz image of PJ231356 is not resolved from a possible radio jet, so it is not currently possible to estimate magnification of the background DSFG. $^a$ Also known as PLCK_G145.2+50.9; (cite: Canameras:2018ab; Frye:2019aa). $^b$ Also known as PLCK_G165.7+67.0; (cite: Canameras:2018ab; Frye:2019aa).

$^c$ Also known as PLCK_G113.7+61.0; (cite: Canameras:2018ab). Einstein radius upper limit estimated from VLA FIRST survey image (cite: Becker:1995aa). $^d$ Also known as the Cosmic Eyebrow; (cite: Diaz-Sanchez:2017aa; Dannerbauer:2019aa). $^e$ Also known as HBoötes3; (cite: Bussmann:2013aa; Borys:2006aa). $^f$ Also known as PLCK_G080.2+49.8; (cite: Canameras:2018ab; Frye:2019aa). $^g$ Also known as PLCK_G092.5+42.9; (cite: Canameras:2018ab; Frye:2019aa).

## Total magnification factors

Total magnification of each lens is determined as the ratio of the total solid angle subtended in the image plane to that of the source plane (as reconstructed by our lens model). These measurements are wavelength-dependent, as the source-plane structure varies with wavelength.

To estimate model-dependent magnification uncertainties, we follow an approach similar to (cite: Sharon:2012aa). 300 samples are drawn from the full MCMC-sampled posterior distribution for each lens mass profile parameter optimized with LENSTOOL, and the observed image-plane arcs are ray-traced into the source plane for each realization, each resulting in a slightly different magnification, measured as the area above a $3\sigma$ signal-to-noise threshold (for both the source plane and image plane). The median of the distribution (and uncertainty in the form of 16th and 84th percentiles) are reported in Table [2](#tab:lensproperties) for each object.

However, we caution that these statistical values can underestimate larger systematic uncertaintiessuch as mis-identified multiple images and inappropriate choices of parameterized mass distributionswhich are difficult to properly take into account.

For example, (cite: Limousin:2016aa) considered the effect of using cored vs. non-cored cluster mass modelsi.e., where the isothermal mass profile of cluster members is modified within an inner core radius.

The authors found that systematic uncertainties in the magnification could be nearly an order of magnitude greater than statistical model-specific uncertainties.

Here, this is unlikely to have a strong impact on the predominantly galaxy-scale lenses, which are influenced more by mass at intermediate radii than the typical core radius ($\sim 100$ pc) or cut radius ($\sim 30 - 100$ kpc), as noted by (cite: Canameras:2017aa).

Regardless, this provides some motivation for model-independent characterizations, such as (cite: Wagner:2016aa) and (cite: Wagner:2018aa), as magnifications can vary across different works.

We reserve the discussion of the distribution in magnification factors in the PASSAGES sample for Section [4.1](#sec:discussion_magnifications).

## Measuring Einstein radii

The Einstein radius $\theta_E$ is a characteristic scale relating directly to the total enclosed mass of the foreground lens inside a projected circle in the sky $M(<\theta_E)$, with some additional dependence on the redshift geometry of the lens and source planes: $$\begin{equation}
\label{eqn:Eradius}
\theta_E = \sqrt{
\frac{4G M(<\theta_E) }{c^2} 
\frac{
D_{LS}
}{
D_L D_S
}
},
\end{equation}$$ where $D_L$, $D_S$, and $D_{LS}$ are the angular diameter distances to the lens plane, to the source plane, and from the lens to source plane, respectively (cite: Narayan:1996aa).

$\theta_E$ is usually quite consistent across different lens models (e.g., (cite: Kochanek:1991aa; Wambsganss:1994aa)), making it a valuable measurement. Observationally, the Einstein radius is comparable to half the typical separation between multiple images.

There are a number of

methods for deriving $\theta_E$ from lens models. Here, we opt for the *equivalent Einstein radius*, $\theta_{Ein, eq}$, defined as the radius enclosing an average surface mass density equal to the critical surface density (or equivalently, where the average convergence $\kappa$ is equal to 1; see (cite: Richard:2010aa; Zitrin:2011aa)). Other definitions include the *effective Einstein radius* (cite: Redlich:2012aa), or the radius enclosing an area equal to that interior to the tangential critical curve, and the *median Einstein radius*, defined as the median distance from points on the tangential critical to the lens centroid (cite: Meneghetti:2011aa; Meneghetti:2013aa). Since all definitions are more or less connected to the area interior to the critical curves, they are also related to the lensing cross section, which is the source-plane area inside the caustics (or sometimes defined as the area of the region where the magnification is greater than a certain threshold).

We report the Einstein radii $\theta_{\rm Ein}$ in Table [2](#tab:lensproperties), as the median value and asymmetric $1\sigma$ uncertainties. The Einstein radii are computed analogously to the magnification, where 100 samples are drawn from the modeling-derived posterior distribution, with a new convergence map created for each iteration. Centered on the peak pixel of each convergence map (the point of greatest surface mass density), the radius is increased linearly until the average convergence crosses below 1.

The distribution of Einstein radii for this sample is discussed in §[4.5](#sec:lens_mass).

## Source-plane size

As our lens-modeling algorithm does not assume a parametric form of the source-plane structure, the intrinsic size of the far-IR continuum-emitting region is measured from the source-plane reconstruction using CASA IMFIT.

As a caveat, this measurement is perhaps best made in the visibility-plane in order to deconvolve the effect of the synthesized beam. Since our source-plane reconstruction retains a distorted version of the beam that varies across the source, removing this is not trivial without a $uv$-based forward-modeling approach (e.g. VISILENS by (cite: Hezaveh:2013aa; Spilker:2016aa) or UVMCMCFIT by (cite: Bussmann:2012aa; Bussmann:2013aa; Bussmann:2015aa)).

Moreover, since this lens modeling approach does not impose a restriction on the nature of the source plane emission, small but non-negligible offsets might be expected between the source-plane positions of reconstructions from different lensed images (§[3.2](#sec:optimization)). We measure the effective radius from the reconstruction of all lensed images together, so these offsets can artificially change the apparent size[^8].

To capture some of this uncertainty from lens modeling, we randomly select 10 of the MCMC lens modeling iterations to create different source-plane reconstructions, measure effective radii independently, and take the mean and standard deviation of this distribution.

Lastly, we convert these angular measurements to physical sizes in kpc given the redshift of the source plane.

Our observing setup with ALMA is not markedly different from that of (cite: Spilker:2016aa) and (cite: Bussmann:2015aa), for example, and the relative uncertainty in effective radius for this work is likewise similar. For this reason, we consider a direct comparison to be feasible.

However, as an added complication in comparing to the broader literature, there are different approaches to quantifying source size.

At optical wavelengths, it is standard to use the effective radius or half-light radius within which half the object’s light is contained (under an assumption of circular symmetry). This in turn is determined through fitting a Sérsic model to the radial profile ((cite: Sersic:1963aa); e.g., with GALFIT, (cite: Peng:2002aa)), for which the degree of central concentration is parameterized by a Sérsic index $n$. For radio imaging, it’s more common to assume a two-dimensional Gaussian functional form (equivalent to a Sérsic model with $n=0.5$). The full-width at half-maximum of the Gaussian is related to the effective radius as ${\rm FWHM} = 2 \times R_{\rm e}$.

In our method, we therefore use the geometric mean of the semi-major and semi-minor axes as the effective radius

[^9]. While the lensing-reconstructed PSF will vary in dimensions for the source plane, we do not account for this here for these global size measurements, as we expect this effect to be smaller than the uncertainties introduced from modeling.

![](figs/L_IR_vs_mag_w_VLA.png)

# Discussion

## PASSAGES sources have modest magnifications

Eleven out of the 15 objects in this work for which we present new lensing models were previously undiscovered[^10] before PASSAGES (cite: Harrington:2016aa; Berman:2022aa).

These new lens models therefore provide many of the first measurements of

magnification at any wavelength for PASSAGES.

In our analysis, we utilized *HST* (1.6$\mu$m  $0.15^{\prime\prime}$ resolution) and JVLA (6 GHz, $0.3-0.7^{\prime\prime}$ resolution) observations for all members. For 11 out of 15, we also used ALMA imaging (1 mm, $0.4-0.8^{\prime\prime}$ resolution), and for 8 out of 15, we used Gemini $r'$ and $z'$ observations.

In future work, we intend to refine and apply these lens models towards multi-J CO and \[CI\] high angular resolution datasets from ongoing campaigns with ALMA, the Submillimeter Array (SMA), and the Northern Extended Millimeter Array (NOEMA).

These will be used to interpret the kinematic structure of different gas components and build a systematic set of differential magnification corrections.

After accounting for this work, only 4 high-$z$ members of the PASSAGES sample lack published lens models: PJ074851.7 (Garcia Diaz et al., in prep.), PJ084650.1 (Foo et al., in prep.), and PJ132217.5 (clusters with background DSFGs at $z=2.76$, $z=2.66$, and $z=2.07$), and the presumed galaxy-galaxy lens PJ141230.5 ($z=3.31$), which currently lacks high-resolution mm/radio follow-up and does not have discernible lensing features in the near-IR.

The PASSAGES objects are detected in near-IR imaging with *Hubble* (Lowenthal et al. in prep.), in contrast to the often optical faintness of DSFGs, especially at $z>3$ (cite: Franco:2018aa; Wang:2019ab; Barrufet:2022aa; Nelson:2022aa; Zavala:2022ab).

This latter point is due in part to the fraction of obscured star formation increasing with SFR (cite: Whitaker:2017aa) and to the more dust-attenuated shorter wavelengths probed at higher-$z$.

Given the availability of lensing evidence in the rest-frame optical, in complement to the rest-frame far-IR, our approach in using LENSTOOL is less vulnerable to the pitfalls of modeling using solely interferometric imaging, which would typically necessitate direct modeling of $uv$-plane visibilities.

![](figs/mu_hist_Pl_Her_SPT_seaborn_Nov2022.png)

The distribution of magnifications for (sub-)mm continuum in this work is largely consistent with those from similar lensed surveys defined from *Herschel* and SPT, as shown in Figure [4](#fig:magnifications).

This may be surprising given the larger apparent luminosities of PASSAGES.

However, we caution that there are still several objects in the PASSAGES sample that lack detailed lens modeling, so this comparison is not robust at this point.

In addition, there are external factors at play in this distribution: in this work, we have largely reserved the time-intensive modeling of cluster lenses for subsequent analyses.

Likewise, the lenses identified with *Herschel* preferentially exclude cluster-scale deflectors, as noted by (cite: Bussmann:2015aa), due to their deconvolution of the *Herschel* Spectral and Photometric Imaging REceiver (SPIRE; (cite: Griffin:2010aa)) PSF (beam FWHM $18 - 36^{\prime\prime}$), which removes extended objects close to the size of the beam.

The SPT sample, however, contained four cluster-lensed objects, but these were not analyzed by (cite: Spilker:2016aa) as not all images were captured within the ALMA field-of-view.

Both this work and others are limited to objects with sufficient high-resolution, high-sensitivity data that are suitable for modeling.

The resolution of data can have some effect on the derived magnifications (e.g., (cite: Hezaveh:2012aa)). For example, the current $\sim 0.4^{\prime\prime}$ resolution comfortably resolves the lensed images in most cases, but does not offer much detail of substructure inside each of the images. Higher resolution ($\sim 0.1^{\prime\prime}$) might reveal chance alignments of compact, bright star-forming clumps with high-magnification areas near the caustic curve. Lower resolutions that are blind to these details could bias the magnification factors. As an added example, two well-separated clumps lying on opposite sides of the critical curve might result in an over-estimated magnification factor if they are blended in lower-resolution imaging, thus appearing to cross the critical curve contiguously. Such effects can not be mitigated completely, but future higher-resolution observations will be key to ruling out these biases.

(cite: Bussmann:2013aa) remarked on lower-than-expected magnifications for *Herschel*-identified lenses, given the objects’ apparent luminosities. Theoretical predictions from (cite: Wardlow:2013aa) based on submillimeter galaxy number counts to estimate the average magnification factor as a function of 500$\ensuremath{\mu}m$ flux density were consistently higher than model-derived magnifications in all but three cases.

In their case, an assumption of a single Sérsic profile to represent the source plane might systematically underestimate magnifications.

(cite: Bussmann:2015aa) offered an explanation that the resolution of their SMA and ALMA observations ($\theta \approx 0.5^{\prime\prime}$) was insufficient to spatially resolve emission within individual lensed images, leading to half-light radius estimates skewed to larger values, in turn giving smaller magnification factors. Indeed, later works showed that higher-resolution imaging ($\approx 100$ milliarcsecond) of the same objects (cite: Dye:2015aa; Rybak:2015aa; Tamura:2015aa) could lead to a factor of $1.5-2$ increase in magnification (cite: Bussmann:2015aa).

## Intrinsic IR luminosities of highly-magnified DSFGs and their relation to the main sequence

Apart from a different modeling approach, it is also possible that the

all-sky *Planck* selection used in PASSAGES (contrasted with the survey area-limited *Herschel* and SPT counterparts) is simply more advantageous for selecting

the rarest objects: intrinsically extreme starbursts that are also serendipitously subject to strong lensing.

While it is clear that identifying lensing candidates by setting simple submillimeter flux thresholds is very efficient, there is not an obvious relation between flux and magnification for the resultant sample.

With a larger ensemble, it will be logical to compare both the distribution functions of magnifications and the luminosity functions of the de-lensed objects with unlensed populations, but that is beyond the scope of this current work.

In the next section, we discuss the apparent balance for a source size that is large enough to sustain intense star formation but small enough to avoid the dilution of magnification due to size bias.

Using the lens model-derived magnifications at 1.1 mm, we can derive intrinsic, de-lensed IR luminosities (given in Table [3](#tab:effective_radii) and shown in Figure [3](#fig:corrected_luminosities)), which range from $L_{\rm IR} = 0.2 - 5.9 \times 10^{13}~L_{\odot}$ (median $1.4 \times 10^{13}~L_{\odot}$).

Since we expect the ALMA 1.1 mm dust continuum to capture the structure of the IR-emitting regions of the source plane, we use this magnification factor as a proxy in place of $\mu_{\rm IR}$. Deriving the intrinsic IR SED would ideally involve de-lensing each of the IR photometric measurements, but the resolution of *Planck*, *WISE*, *Herschel*, and AzTEC in the mid-IR and far-IR is dramatically coarser than the high-resolution ALMA 1.1 mm imaging. Using the magnification from a representative high-resolution rest-frame far-IR image remains the best approach.

However, for the objects modeled in this work and in others summarized in Table [2](#tab:lensproperties), four are lacking comparable ALMA imaging (due primarily to being inaccessible northern sources). In Figure [3](#fig:corrected_luminosities), we include the magnifications measured from 6 GHz radio continuum imaging at similar angular resolution, which are consistent within 40% relative difference for the majority of cases. These $\mu_{\rm 6 GHz}$ factors can thus be used to roughly estimate intrinsic $L_{\rm IR}$, as indicated in Table [3](#tab:effective_radii).

However, because of these possible differences in magnification, we do not include the objects lacking far-IR magnifications in the subsequent discussion on source sizes and star formation rate surface densities.

Despite their high inferred SFRs of $170 - 6300~M_{\odot}~{\rm yr}^{-1}$ (median $1500~M_{\odot}~{\rm yr}^{-1}$; Table [3](#tab:effective_radii)), it is not clear where exactly the PASSAGES members fall in relation to the star-formation main sequence,

a tight correlation between SFR and $M_\star$, the normalization of which evolves with redshift (e.g. (cite: Brinchmann:2004aa; Noeske:2007aa; Elbaz:2007aa; Daddi:2007aa; Whitaker:2012aa; Speagle:2014aa)).

The peak and Rayleigh-Jeans tail of their dust SEDs are well sampled by *Planck*, *Herschel*, AzTEC, and ALMA photometry, leading to secure SFR estimates; extensive multi-line/continuum modeling by (cite: Harrington:2021aa) results in robust molecular gas estimates. Yet, the dearth of stellar mass estimates makes it impossible to reliably place these other properties in context.

This is not a novel problem for DSFGs:

it has not been settled whether they largely represent abnormal outliers forming stars at elevated rates compared to other objects of similar mass, or if their stellar masses are proportionally higher to match their extreme SFRs (cite: Casey:2014aa). Typically poor constraints on rest-frame optical luminosities due to heavy dust attenuation make the assessment of $M_\star$ difficult for this population. This is additionally complicated by both the higher sensitivity to the initial mass function (IMF), as shorter-wavelength optical and UV fluxes predominantly trace the contribution of the most massive stars, and the less-constrained contribution of AGN to the near-IR continuum (cite: Hainline:2011aa). Recent work with other submillimeter-selected samplesprimarily with $\log_{10}[{\rm SFR} / M_{\odot}~{\rm yr}^{-1}] \sim 2.5 - 3.5$,

in line with PASSAGESby (cite: Miettinen:2017aa) (for $z \sim 1 - 7$ DSFGs in the COSMOS field; (cite: Scoville:2007aa)) and (cite: Barrufet:2020aa) (for $z \sim 1 - 5$ DSFGs in the North Ecliptic Pole field) suggested that around 60% of DSFGs might be consistent with the main sequence at their respective redshifts,

whereas (cite: Ikarashi:2017aa)

suggested 72% were safely above the main sequence ($z \approx 1.4 - 2.5$).

(cite: Harrington:2021aa) and (cite: Berman:2022aa) highlighted the PASSAGES sample’s short gas depletion times ($\tau_{\rm dep}=100-400$ Myr), but these values are not particularly meaningful without an estimate of the average depletion time of a main sequence galaxy at the same redshift and of similar stellar mass (e.g. (cite: Scoville:2017aa; Tacconi:2018aa)).

Following (cite: Liu:2019ad), (cite: Wang:2022ac) recently derived a best-fit relationship for molecular gas depletion time $\tau_{\rm mol} \equiv M_{\rm mol} / {\rm SFR}$ as a function of stellar mass, redshift/cosmic age, and distance to the main sequence, $\Delta {\rm MS} \equiv {\rm log}_{10} ({\rm SFR}/{\rm SFR}_{\rm MS})$ (see their equation 9).

For fiducial stellar masses[^11] of $10^{10.5} M_\odot$, $10^{10.75} M_\odot$, and $10^{11} M_\odot$ at a representative redshift of $z=2.5$, this yields main-sequence depletion times of 340, 360, and 380 Myr, respectively.

Conversely, for our observed range of depletion timeswith an inner 68% confidence interval of $\tau \sim 150 - 350$ Myrwe obtain $\Delta {\rm MS} = -0.02 - 0.69$ for $M_\star = 10^{10.5}~M_\odot$, $\Delta {\rm MS} = 0.02 - 0.78$ for $M_\star = 10^{10.75}~M_\odot$, and $\Delta {\rm MS} = 0.08 - 0.88$ for $M_\star = 10^{11}~M_\odot$.

This suggests that a clear majority of the PASSAGES objects should have specific star formation rates (sSFR $\equiv {\rm SFR}/M_\star$) that lie at least above the center of the main sequence, but raises doubts that they could all be classified uniformly as traditional starbursts. Specifically, a median depletion time and stellar mass (250 Myr and $M_\star = 10^{10.75}~M_\odot$) yields $\Delta {\rm MS} = 0.32$, which falls below the $\Delta {\rm MS} > 0.6$ dex threshold for starbursts proposed by (cite: Rodighiero:2011aa).

Another independent approach is to use a relation between star-formation rate surface density $\Sigma_{\rm SFR}$ and $\Delta {\rm log}_{10}({\rm sSFR})_{\rm MS} \equiv {\rm log}[{\rm sSFR}/{\rm sSFR}_{\rm MS}(M_\star, z)] (= \Delta {\rm MS})$, as proposed by (cite: Jimenez-Andrade:2019aa). For the highest-redshift bin[^12], $1.75 < z \le 2.25$, (cite: Jimenez-Andrade:2019aa) find a best-fit power-law relation of ${\rm log}(\Sigma_{\rm SFR}) = [1.5 \pm 0.2] \times \Delta {\rm log}({\rm sSFR})_{\rm MS}+ [1.2 \pm 0.1]$ for galaxies with ${\rm log}_{10} (M_\star / M_\odot) \gtrsim 10.5$.

For this work, the inner 68% confidence interval in star-formation surface density is $\Sigma_{\rm SFR} \approx 20 - 160$ (see §[4.4](#sec:Eddington_SFR)), suggesting distances to the main sequence of $\Delta {\rm log}_{10}({\rm sSFR})_{\rm MS} = 0.07 - 0.67$, in rather close agreement with the values estimated from depletion times. However, this relation seems to evolve somewhat from $z=0.5 - 2$, where the slope of the relation becomes shallower and the offset increases with redshift, meaning that surface densities are higher in the Universe, with smaller discrepancies in $\Sigma_{\rm SFR}$ between starbursts and main sequence galaxies, so its predictive power may be weakened for higher-$z$ PASSAGES members.

Forthcoming dynamical measurements of the gravitational potentials for PASSAGES will offer helpful context to this discussion, but

at present, their actual specific star formation rates

remain an open question.

Sensitive

telescopes like *JWST* will also offer the opportunity to better constrain the rest-frame UV and optical SED of such DSFGs, rendering stellar mass measurements slightly less uncertain.

To reiterate, based on the gravitational lens modeling in this work, we have found that the PASSAGES sample overwhelmingly consists of objects that are intrinsically luminous and not extraordinarily amplified by lensing.

This discovery prompts a more thorough exploration of their intrinsic properties, which we discuss in the next section.

## Source-plane reconstructed galaxy sizes

In §[3.6](#sec:effective_radius), we discuss our computation of galaxy size or effective radius as the geometric mean of the semi-major and semi-minor axes of a best-fit Gaussian.

At 1 mm, this results in dust continuum sizes of $R_{\rm e} = 1.7 - 4.3$ kpc (median 3.0 kpc; Table [3](#tab:effective_radii)). As we discuss in this section, the PASSAGES galaxies are larger at this wavelength than most DSFGs studied thus far, but to a degree that is consistent with their larger luminosities.

However, as these are lensed objects selected by their image-plane fluxes, selection effects may bias the intrinsic sizes to which we are sensitive.

### Possible source size bias?

![](figs/mag_vs_Reff_arcsec.png)

The intrinsic sizes of the DSFGs that make up the PASSAGES sample have implications for both the maximum lensing magnifications and the maximum star formation surface densities that can be observed.

For the former, there is a small region of the source plane capable of producing high magnifications (e.g. $\mu > 10$), especially in the case of galaxy-scale lenses where the caustic network is comparable in size to that of typical background objects.

For EAGLE-simulated lenses at $z_{\rm lens} \approx 0.37$, (cite: Robertson:2020aa) found source-plane cross-section solid areas at $z_s = 2$ satisfying $|\mu| > 10$ to be $\sigma^{\rm S}_{\rm lens} \approx 0.008$ and 0.08 arcsec$^2$ for halo masses of $10^{12}$ and $10^{13}~M_\odot$, respectively. For large magnification thresholds ($\mu_0 \gg 1$), this cross-section drops off as $\sigma^{\rm S}_{\rm lens} \propto \mu_0^{-2}$ (see also (cite: de-Freitas:2018aa)).

In the vicinity of a caustic curve (where magnification diverges), increasing source size has the effect of diluting the overall magnification, as the outer extent of the source reaches into lower magnification regions (such as the local minimum inside the caustic curves, or the asymptotically-decreasing magnifications exterior to the caustics).

However, in simulations to study the predicted size bias of flux-selected lens samples, (cite: Hezaveh:2012aa) found the intriguing result that intermediate total magnifications ($\mu\sim10$) could preferentially magnify *diffuse* (or extended) components in the source plane, contrary to the common intuition (e.g. (cite: Serjeant:2012aa)) that more compact components are amplified more strongly (which (cite: Hezaveh:2012aa) did indeed find to be the case for smaller and larger magnifications).

This latter effect may be due to the nuanced consideration that a larger source still has a greater chance of being modestly magnified ($\mu < 10$). In other words, as described by (cite: Robertson:2020aa), the maximum possible magnification (optimized as a function of source position) decreases for larger source sizes (as a decreasing fraction of the source will be some arbitrary distance from the caustic), but the probability of some part of the source being near to the caustic network increases for larger sources.

In the case of a singular isothermal sphere acting as a lens, (cite: de-Freitas:2018aa) determined that the cross section for $\mu > 10$ was optimally maximized when the source-plane object had an angular size of $\approx 30\%$ the Einstein radius (in contrast to $\approx 15\%$ for the threshold $\mu > 20$).

We make further comparisons to these predictions in §[4.5](#sec:lens_mass).

![](figs/Reff_vs_L_IR_w_lensed_DSFGs.png)

![](figs/Reff_vs_L_FIR.png)

This lensing size bias effect has been tested empirically by many works, including (cite: Serjeant:2012aa),

and (cite: Spilker:2016aa).

In the case of the latter, (cite: Spilker:2016aa) showed that 870$\ensuremath{\mu}m$ magnifications for SPT lenses, along with *Herschel* lenses from (cite: Bussmann:2013aa) and (cite: Bussmann:2015aa), did not appear to correlate strongly with source size across the entire range of observed sizes or magnifications. In fact, the largest sources covered a wide range of magnifications consistent with the remaining objects. However, the authors did note that the highest-magnification objects ($\mu_{870\mu m} > 10$) were preferentially more compact.

Notwithstanding this, (cite: Spilker:2016aa) found that the distribution of source sizes in the SPT and *Herschel* lens samples was statistically consistent with that of unlensed DSFGs,

such as the 850 $\ensuremath{\mu}m$ SCUBA-2 Cosmology Legacy Survey ((cite: Simpson:2015ab; Simpson:2015aa); median FWHM $0.30 \pm 0.04^{\prime\prime}$) and 1.1-mm AzTEC sources ((cite: Ikarashi:2015aa; Ikarashi:2017aa); median FWHM $0.20 \pm 0.04^{\prime\prime}$ and $0.31 \pm 0.03$).

Together, these tests suggested that the hypothesized size bias was not observable with the then-available sample size.

In Fig. [5](#fig:size_bias), we similarly test for the presence of any size bias for the PASSAGES sample (extending Fig. 5 of (cite: Spilker:2016aa)).

In our case, there is some evidence of anti-correlation between magnification and effective radius,

especially for $R_e \gtrsim 0.2^{\prime\prime}$,

a region of the parameter space for which our sample contributes significantly.

Objects with sizes larger than $0.3^{\prime\prime}$ all have lower magnifications, $\mu \leq 10$, whereas smaller objects exhibit a large range of magnifications.

These findings raise the question of the nature of selection biases in the definition of PASSAGES (cite: Harrington:2016aa; Berman:2022aa), as objects capable of producing observed luminosities $\mu L_{\rm IR} \sim 10^{14} L_\odot$ must have some combination of high total lensing magnification and high intrinsic luminosity.

If galaxy-scale lenses were to preferentially magnify more compact objects, then there would be a negative power-law slope between $\mu$ and $R_e$. In tandem with the positive slope of $L_{\rm IR}$ vs. $R_e$, it might be the case that the selection function of this sample identifies objects of an optimal size that maximizes the product of $\mu$ and $L_{\rm IR}$ (e.g. (cite: Lutz:2014aa)).

Of course, the distribution of intrinsic luminosities is also subject to the luminosity function at high-redshift, as there is an effective cutoff on the high-luminosity end.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Field | $R_{{\rm e},{1100\mu{\rm m}}}$ | $R_{{\rm e},{1100\mu{\rm m}}}$ | $\theta_{\rm maj}$ | $\theta_{\rm min}$ | PA | ${L_{\rm IR}}^a$ | ${{\rm SFR}_{\rm IR}}^b$ | $\Sigma_{\rm SFR}$ \[$\Sigma_{\rm SFR, peak}$\] |
|  | \[$^{\prime\prime}$\] | \[kpc\] | \[$^{\prime\prime}$\] | \[$^{\prime\prime}$\] | \[$^{\circ}$\] | \[$10^{13} L_{\odot}$\] | \[$M_{\odot}~{\rm yr}^{-1}$\] | \[$M_{\odot}~{\rm yr}^{-1}~ {\rm kpc}^{-2}$\] |
|  |  |  |  |  |  |  |  |  |
| PJ011646 | $0.45\pm0.02$ | $3.7 \pm 0.2$ | 0.43 | 0.38 | -83.2 | $1.7 \pm 0.4$ | $1820 \pm 460$ | $42 \pm 11$ \[41\] |
| PJ014341 | $0.31\pm0.02$ | $2.5 \pm 0.2$ | 0.49 | 0.40 | 67.7 | $0.16 \pm 0.05$ | $170 \pm 50$ | $9  \pm 3$ \[16\] |
| PJ020941 | $0.29\pm0.07$ | $2.3 \pm 0.6$ | 0.54 | 0.40 | 63.8 | $1.9 \pm 0.8$ | $2030 \pm 820$ | $119 \pm 56$ \[136\] |
| PJ022633 |  |  |  |  |  | $1.0 \pm 0.4^\dagger$ | $1020 \pm 470^\dagger$ |  |
| PJ030510 | $0.44\pm0.05$ | $3.6 \pm 0.4$ | 0.85 | 0.59 | 80.9 | $5.9 \pm 1.7$ | $6290 \pm 1850$ | $153 \pm 48$ \[187\] |
| PJ105353 | $0.22\pm0.01^{\dagger \dagger}$ | $1.7 \pm 0.0$ | 0.45 | 0.27 | 63.1 | $2.5 \pm 0.6$ | $2610 \pm 590$ | $290 \pm 66$ \[264\] |
| PJ112713 |  |  |  |  |  | $0.6 \pm 0.1^\dagger$ | $590 \pm 120^\dagger$ |  |
| PJ113805 | $0.36\pm0.02$ | $3.0 \pm 0.2$ | 1.03 | 0.66 | 3.5 | $0.9 \pm 0.2$ | $910 \pm 190$ | $32 \pm 7$ \[37\] |
| PJ113921 | $0.40\pm0.07$ | $3.1 \pm 0.5$ | 0.82 | 0.69 | -14.0 | $2.5 \pm 0.7$ | $2660 \pm 750$ | $87 \pm 29$ \[79\] |
| PJ132630 | $0.38\pm0.03$ | $2.9 \pm 0.2$ | 0.99 | 0.64 | -2.2 | $1.7 \pm 0.4$ | $1860 \pm 470$ | $68 \pm 18$ \[61\] |
| PJ133634 |  |  |  |  |  | $2.2 \pm 0.9^\dagger$ | $2310 \pm 990^\dagger$ |  |
| PJ144653 | $0.38\pm0.01$ | $3.1 \pm 0.1$ | 0.76 | 0.68 | 11.7 | $0.7 \pm 0.2$ | $710 \pm 180$ | $24 \pm 6$ \[24\] |
| PJ144958 | $0.33\pm0.10$ | $2.7 \pm 0.8$ | 0.81 | 0.67 | 6.3 | $1.0 \pm 0.6$ | $1050 \pm 580$ | $45 \pm 28$ \[78\] |
| PJ160722 |  |  |  |  |  | $0.2 \pm 0.1^\dagger$ | $220 \pm 110$ |  |
| PJ231356 | $0.52\pm0.05$ | $4.3 \pm 0.4$ | 0.78 | 0.61 | 68.0 | $1.0 \pm 0.3$ | $1060 \pm 310$ | $18 \pm 6$ \[29\] |
|  |  |  |  |  |  |  |  |  |
| *Literature* | $R_{{\rm e},{870\mu{\rm m}}}$ | $R_{{\rm e},{870\mu{\rm m}}}$ | $\theta_{\rm maj}$ | $\theta_{\rm min}$ | PA | ${L_{\rm IR}}$ | ${{\rm SFR}_{\rm IR}}^c$ | $\Sigma_{\rm SFR}$ |
|  | \[$^{\prime\prime}$\] | \[kpc\] | \[$^{\prime\prime}$\] | \[$^{\prime\prime}$\] | \[$^{\circ}$\] | \[$10^{13} L_{\odot}$\] | \[$M_{\odot}~{\rm yr}^{-1}$\] | \[$M_{\odot}~{\rm yr}^{-1}~ {\rm kpc}^{-2}$\] |
|  |  |  |  |  |  |  |  |  |
| PJ105322$^d$ |  |  |  |  |  | $2.9 \pm 0.2$ | $3090 \pm 210$ |  |
| PJ112714$^e$ | $0.17 \pm 0.04$ | $1.4\pm0.3$ | 0.90 | 0.75 | 39 | $0.4 \pm 0.1$ | $430   \pm 110$ | $70\pm20$ |
| PJ132302$^d$ |  |  |  |  |  | $0.9 \pm 0.1$ | $960   \pm 110$ |  |
| PJ132934$^f$ |  |  |  |  |  | $1.3 \pm 0.1$ | $1380 \pm 110$ |  |
| PJ142823$^g$ | $0.08\pm0.05$ | $0.71\pm0.43$ | $\approx 0.7$ | $\approx 0.7$ |  | $0.6 \pm 0.3$ | $640 \pm 320$ | $400\pm320$ |
| PJ154432$^d$ |  |  |  |  |  | $0.31 \pm 0.02$ | $330 \pm 20$ |  |
| PJ160918$^d$ |  |  |  |  |  | $1.6 \pm 0.1$ | $1710 \pm 130$ |  |

:  Lensing-corrected source-plane effective radii at 1.1 mm and intrinsic total IR luminosities $L_{\rm IR}$, using $\mu_{\rm 1.1mm}$ magnification factors as representative of dust emission magnification. The continuum synthesized beam parameters for each field are shown for context. The star formation rate surface density, $\Sigma_{\rm SFR}$ is given as both a global average value (total SFR divided by the area of the disk with given effective radius), and as a peak value given in brackets (see §[4.4](#sec:Eddington_SFR)).

Table notes:

$^a$ Lensing-corrected intrinsic luminosities derived by dividing apparent far-infrared luminosities ($8 - 1000\ensuremath{\mu}m$) from Table 6 of (cite: Berman:2022aa) (or Table 4 of (cite: Harrington:2016aa)) by magnification factors in Table [2](#tab:lensproperties). $^b$ Lensing-corrected IR-inferred star formation rates derived by dividing Starburst SED star formation rates from Table 6 of (cite: Berman:2022aa) (or Table 4 of (cite: Harrington:2016aa)) by magnification factors in Table [2](#tab:lensproperties). $^c$ Star formation rates derived from (cite: Kennicutt:1998aa) calibration, ${\rm SFR} = L_{\rm IR} / (9.4 \times 10^9) M_{\odot}{\rm yr}^{-1}$. $^d$ De-lensed $L_{\rm IR}$ from (cite: Canameras:2015aa; Canameras:2018ab). $^e$ De-lensed $L_{\rm IR}$ from (cite: Canameras:2015aa; Canameras:2018ab; Canameras:2018aa), using latest magnification factor from (cite: Pascale:2022aa). $^f$ De-lensed $L_{\rm IR}$ from (cite: Diaz-Sanchez:2017aa). $^g$ De-lensed $L_{\rm IR}$ from (cite: Bussmann:2013aa). $^\dagger$ Approximate intrinsic IR luminosity estimated using 6 GHz magnification factor (as high-resolution 1 mm/870 $\mu$m image is not available, see discussion in §[4.2](#sec:HyLIRGs)). $^{\dagger \dagger}$ Low-resolution ALMA Band 7 ($870\mu$m) measurement from program 2019.1.01636.S (PI: M. Yun).

### Intrinsic far-IR source size

With this work, we seek to place the

PASSAGES objects modeled in this work

in the context of other submm-selected lensed systems, as seen in Figures [5](#fig:size_bias) and [6](#fig:LIR_Reff_lensed).

In comparison to the *Herschel* and SPT lensed DSFGs, the PASSAGES DSFGs encompass larger intrinsic source sizes in physical units.

However, the largest PASSAGES object is comparable in size to the largest member of the (cite: Bussmann:2013aa) sample (J091305.0-005343 or SDP.130, $R_e = 4.14 \pm 0.72$).

Yet, despite occupying the upper end of luminosities covered by the other samples, PASSAGES objects show notable evidence for lower star-formation rate surface densities, which are primarily between $10 - 100~M_{\odot}$ yr$^{-1}$ kpc$^{-2}$, consistent with the vast majority of over 1000 dusty starbursts studied by (cite: Fujimoto:2017aa).

To further elucidate this discrepancy, we extrapolate our analysis to include unlensed DSFGs. Figure [7](#fig:LIR_Reff) reveals that PASSAGES is in accordance with a scaling relation of $L_{\rm IR}-R_e$ found by (cite: Fujimoto:2017aa), but both larger and more luminous than the physical quantities derived by (cite: Bussmann:2013aa) and (cite: Spilker:2016aa) (in members for which redshifts are measured).

(cite: Berman:2022aa) found that the PASSAGES DSFGs account for an average number density of about $10^{-2}~{\rm deg}^{-2}$, in comparison with the *Herschel* samples’ density of $0.02-0.1~{\rm deg}^{-2}$ (cite: Vieira:2013aa; Wardlow:2013aa; Weiss:2013aa), suggesting that PASSAGES includes some of the very rarest all-sky objects. It is thus not entirely surprising that they would have higher intrinsic luminosities (when considering comparable lensing magnifications) and larger source sizes than other DSFG samples, which probe deeper into the regime of less extreme DSFGs but are restricted to a smaller survey area.

It might also be the case that other factors are at play.

In the case of (cite: Spilker:2016aa) in particular, the more compact sizes might be due to their higher redshift ($z\sim 3.5-5$ primarily). While the angular size does not evolve significantly for a given physical size between $z\sim4$ and $z\sim2$, (cite: Fujimoto:2017aa) find a

detectable

evolution in physical size for a given $L_{\rm IR}$ ($L_{\rm IR} \sim 10^{12} - 10^{13}~L_{\odot}$), albeit with a small sample size ($<10$ galaxies at $z>4$). On the other hand, (cite: Enia:2018aa) do not observe a clear redshift evolution, and note that some apparent evolution could be due to selection effects biased against the decrease in surface brightness (for fixed luminosity and size) at higher redshifts.

Additionally, the lens modeling approach for PASSAGES in this work is fundamentally different from (cite: Bussmann:2013aa; Bussmann:2015aa), and (cite: Spilker:2016aa), which all optimize model parameters directly over interferometric visibilities. This requires an adoption of a parametric form of the source-plane distribution (in contrast to our method, described in Section [3.6](#sec:effective_radius)).

(cite: Enia:2018aa) note that estimating source size from parametric modeling consistently resulted in systematically lower values, in comparison with an approach of measuring the area of the source above a certain signal-to-noise threshold. This is especially true for clumpy morphologies, where a Gaussian or Sérsic profile might underestimate the true spatial extent.

An ample number of recent studies have revealed the presence of significant sub-kpc inhomogeneous, clumpy substructure that can dominate the sub-mm flux of DSFGs (cite: Swinbank:2010aa; Swinbank:2011aa; Danielson:2011aa; Hodge:2012aa; Hodge:2019aa; Alaghband-Zadeh:2012aa; Menendez-Delmestre:2013aa; Hatsukade:2015aa; Iono:2016aa; Canameras:2018aa; Tadaki:2018aa; Dessauges-Zavadsky:2019aa; Ramasawmy:2021aa; Spilker:2022aa), although some counter-evidence to the ubiquity of clumps in DSFGs does exist (e.g. (cite: Hodge:2016aa; Ivison:2020aa)).

These clumpy sites of star formation appear to be somewhat akin to larger ($\sim$100pc), more luminous analogs to giant molecular clouds (cite: Swinbank:2010aa; Dessauges-Zavadsky:2019aa).

Similar substructure is also apparent in rest-frame UV/optical imaging of star-forming galaxies (e.g. (cite: Forster-Schreiber:2011aa; Iani:2021aa), and references therein).

While the angular resolution of this current ALMA imaging ($\sim 0.5 ^{\prime\prime}$)

is consistent with that of the *Herschel* and SPT lenses,

it is challenging at present to assess the degree of clumpiness at sub-kpc scales (Fig. [2](#fig:model_SP)). In the future, we intend to compare these results with higher-resolution ALMA observations, which enables physical resolutions closer to 100 pc with lensing, at which point we can adequately map the spatial variation of $\Sigma_{\rm SFR}$ (e.g. (cite: Hodge:2019aa)).

The intrinsic far-IR continuum sizes in this study span a range of $1.7 - 4.3$ kpc, consistent with the typical predicted size of $\sim3$ kpc from radiative transfer modeling by (cite: Harrington:2021aa), especially when adopting a revised fiducial magnification of $\mu\sim10-20$.

For optically-thick regions, the Stefan-Boltzmann Law applied to typical ULIRG luminosities and temperatures gives

$R_e = 1.09 \cdot [L_{\rm IR} / 10^{12}~L_{\odot}]^{1/2} \cdot [T_{\rm dust} / 35~{\rm K}]^{-2}$ kpc (cite: Scoville:2013aa), so the luminosities for this sample ($L_{\rm IR} \approx (2 - 60) \times 10^{12} L_{\odot}$)

translate to expected sizes of $R_e \approx 1.5 - 8.5$ kpc.

The far-IR physical sizes we find are comparatively a bit larger than those found by recent studies of submillimeter-bright galaxies, including (cite: Simpson:2015ab) (median $R_e = 1.2\pm0.1$ kpc, interquartile range $1.8-3.2$ kpc), (cite: Tadaki:2015aa) ($R_e = 0.7\pm0.1$ kpc), (cite: Barro:2016aa) and (cite: Oteo:2016aa) ($R_e \sim 1$ kpc), (cite: Hodge:2016aa) (median $R_e = 1.8\pm0.2$ kpc), (cite: Rujopakarn:2016aa) (median $R_e = 2.1\pm0.9$ kpc),

(cite: Ikarashi:2017aa) ($R_e = 1.6\pm0.3$ kpc), (cite: Tadaki:2017ab) ($R_e \sim 1.5$ kpc),

and (cite: Gomez-Guijarro:2022ab)

(median $R_e = 0.73\pm0.29$ kpc).

As emphasized by radiative transfer modeling of FIRE-2 (cite: Hopkins:2014aa; Hopkins:2018aa) zoom-in cosmological simulations by (cite: Cochrane:2019aa), the spatial extent of single-band dust continuum emission is determined by a combination of the spatial extent of dust mass and of recent star formation, given the mechanism of dust heating. (cite: Cochrane:2019aa) confirmed that spatially-resolved dust temperature gradients (measured via spectral indices of multiple sub-mm bands) is an effective method to disentangle these combined effects (e.g. as done with local galaxies by (cite: Galametz:2012aa)).

A consistent picture has arisen that the far-IR emission of high-$z$ star-forming galaxies originates from a substantially more compact spatial region (by a typical factor of $2-4$) than that traced by rest-frame UV and optical imaging (e.g. (cite: Calanog:2014aa; Simpson:2015ab; Chen:2015aa; Ikarashi:2015aa; Barro:2016ab; Talia:2018aa; Tadaki:2020aa; Pantoni:2021ab)).

This is likewise generally the case for radio sizes as well, which are comparable to far-IR sizes (e.g. (cite: Bondi:2018aa; Jimenez-Andrade:2019aa)).

This compact phase of star formation is consistent with the evolutionary schemes for progenitors of massive elliptical/quiescent galaxies (e.g. (cite: Barro:2013aa; Toft:2014aa; Lapi:2018aa)).

Intriguingly, (cite: Ikarashi:2017aa) found that DSFGs with evidence for composite star-forming/AGN growth were more compact than star formation-dominated or AGN-dominated objects ($R_e=1.0\pm 0.2$ kpc vs. $R_e=1.6\pm 0.3$ for star-formation dominated or $R_e=1.5\pm 0.6$ for AGN-dominated), which the authors suggest might be due to supermassive black hole growth during a compact star-forming phase of merger coalescence (cite: Springel:2005aa). In contrast, extended FIR sizes of star-formation-dominated DSFGs may arise from an intermediary merger stage, while extended morphology of AGN-dominated DSFGs may be the result of positive feedback inducing star formation at larger radii (cite: Ishibashi:2012aa).

At present, though, there is not overwhelming evidence to support or rule out this theory.

As an added caveat, the extended rest-frame UV/optical sizes could be the result of a radial dependence of dust attenuation (e.g. (cite: Nelson:2016aa)), where a strongly centrally-concentrated distribution could result in artificially-extended half-light radii larger than half-mass radii (e.g., (cite: Tacchella:2018aa; Bondi:2018aa; Suess:2019aa)). Early studies with *JWST* have begun to test this hypothesis, and initial results (e.g. (cite: Suess:2022aa)) indicate the important role that spatial variations in dust attenuation and stellar population ages can play.

The elevated dust-emitting sizes of PASSAGES starbursts may be explained primarily by the larger intrinsic IR luminosities.

(cite: Fujimoto:2017aa) uncovered a power-law scaling relation between FIR effective radius and luminosity, $R_e \propto L_{\rm FIR}^{0.28 \pm 0.07}$ for $L_{\rm FIR} \gtrsim 10^{12} L_\odot$, in studying a large sample of several hundred 1 mm ALMA detections, with effective radii spanning physical scales of

$0.2 - 5.0$ kpc. (cite: Burnham:2021aa) offered some confirmation with a comparable power-law slope of $R_e \propto L_{\rm FIR}^{0.37 \pm 0.03}$ (in a much smaller sample of 18 DSFGs, median $R_e = 0.32\pm0.09$ kpc).

However, these trends have yet to be tested for a large ensemble of objects at $L_{\rm IR} \sim 10^{13} L_\odot$, i.e. HyLIRGs.

As we demonstrate in Fig. [7](#fig:LIR_Reff), the PASSAGES objects in this work are consistent with the previously-discovered trends.

Intriguingly, in comparison with the *Herschel* and SPT lensed DSFGs of (cite: Bussmann:2013aa) and (cite: Spilker:2016aa), as shown in Fig. [6](#fig:LIR_Reff_lensed), the PASSAGES objects appear to be larger on average for a given IR luminosity. This may be a result of the lower median redshift of PASSAGES, as discussed in the next section.

Some works have applied the Stefan-Boltzmann law at galaxy scales, where the IR luminosity can be related to effective galaxy size and dust temperature:

$L_{\rm IR} \approx 4\pi R_e^2 \sigma T_d^4$, for constant $\sigma = 5.670 \times 10^{-5}$ erg s$^{-1}$ cm$^{-2}$ K$^{-4}$.

(cite: Yan:2016aa) suggested the use of a generalized, temperature-dependent $\tilde{\sigma}(T) = \sigma \times 10^{-3} (-3.03T^{1.5} + 45.55 T -127.53)$

in the case of a modified blackbody spectrum,

whereas (cite: Ma:2015ab) used a simpler power-law relation to arrive at $L_{\rm IR} = 4\pi R_e^2 \sigma T_d^{4.32}$.

Here we adopt $\tilde{\sigma}(T) \propto T^{0.8}$, which closely approximates the (cite: Yan:2016aa) relation as a single power-law for the primary range of interest, $T_d = 20 - 50$ K, such that $L_{\rm IR} \propto R_e^2 T_d^{4.8}$.

Empirically, (cite: Fujimoto:2017aa) and (cite: Burnham:2021aa) found a relation of $L_{\rm IR} \propto R_e^{2.7 - 3.6}$, with which the PASSAGES objects concur (Fig. [7](#fig:LIR_Reff)).

In keeping with the Stefan-Boltzmann relation, this would necessitate

that $T_d \sim R_e^{0.2 - 0.3}$,

indicating a weak dependence, but this is contrary to some expectations that dust temperature decreases with size. For example, for 16 objects studied by (cite: Hodge:2016aa), there is an approximate correlation of $\log[T_d] / \log[R_e] \approx -2$ to $-1$ (although there is also an anti-correlation of temperature with redshift, which may play a larger role).

Regardless, it may be the case that this simple framework does not adequately describe the infrared emission of dusty star-forming objects, as it assumes that they radiate as optically-thick, spherical blackbodies. For this work in particular, sizes are measured at observed-frame 1 mm, in the Rayleigh-Jeans regime often assumed to be optically thin[^13] (which fortuitously allows for the direct estimation of ISM mass from flux; (cite: Scoville:2016aa; Scoville:2017aa)).

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Field | $S_{6{\rm GHz}}$ | $\log[L_{\rm 1.4 GHz}]$ | $q_{\rm FIR}$ | $R_{{\rm e},{6 GHz}}$ | $R_{{\rm e},{6 GHz}}$ | $\theta_{\rm maj}$ | $\theta_{\rm min}$ | PA |
|  | \[$\mu$Jy\] | $[{\rm W~Hz}^{-1}]$ |  | \[$^{\prime\prime}$\] | \[kpc\] | \[$^{\prime\prime}$\] | \[$^{\prime\prime}$\] | \[$^{\circ}$\] |
|  |  |  |  |  |  |  |  |  |
| PJ011646 | $664   \pm 37$ | 24.9 $\pm$ 0.1 | 2.3 $\pm$ 0.2 | $0.67\pm0.01$ | $5.5 \pm 0.1$ | 0.73 | 0.36 | 15.9 |
| PJ014341 | $76    \pm 7$ | 23.4 $\pm$ 0.3 | 2.8 $\pm$ 0.4 | $0.32\pm0.05$ | $2.6 \pm 0.4$ | 0.38 | 0.29 | 29.9 |
| PJ020941 | $909   \pm 37$ | 25.0 $\pm$ 0.3 | 2.3 $\pm$ 0.5 | $0.23\pm0.05$ | $1.9 \pm 0.4$ | 0.51 | 0.40 | 25.0 |
| PJ022633 | $1295  \pm 59$ | 25.0 $\pm$ 0.4 | 2.0 $\pm$ 0.6 | $0.57\pm0.39$ | $4.3 \pm 3.0$ | 0.48 | 0.37 | 64.3 |
| PJ030510 | $221   \pm 22$ | 24.9 $\pm$ 0.4 | 2.9 $\pm$ 0.5 | $0.79\pm0.03$ | $6.5 \pm 0.2$ | 1.21 | 0.43 | 27.2 |
| PJ105353 | $874   \pm 46$ | 25.3 $\pm$ 0.1 | 2.1 $\pm$ 0.3 | $0.25\pm0.01$ | $1.9 \pm 0.1$ | 0.42 | 0.36 | 24.6 |
| PJ112713 | $678   \pm 35$ | 24.6 $\pm$ 0.1 | 2.2 $\pm$ 0.2 | $0.27\pm0.01$ | $2.3 \pm 0.1$ | 0.61 | 0.37 | 74.6 |
| PJ113805 | $525   \pm 27$ | 25.0 $\pm$ 0.3 | 2.0 $\pm$ 0.3 | $0.21\pm0.03$ | $1.7 \pm 0.2$ | 0.33 | 0.30 | -67.7 |
| PJ113921 | $249   \pm 14$ | 24.7 $\pm$ 0.3 | 2.7 $\pm$ 0.4 | $0.53\pm0.05$ | $4.1 \pm 0.4$ | 0.44 | 0.39 | 47.2 |
| PJ132630 | $92    \pm 6$ | 24.2 $\pm$ 0.3 | 3.1 $\pm$ 0.4 | $0.34\pm0.11$ | $2.7 \pm 0.9$ | 0.43 | 0.38 | 80.9 |
| PJ133634 | $403   \pm 24$ | 25.0 $\pm$ 0.4 | 2.3 $\pm$ 0.6 | $0.44\pm0.21$ | $3.3 \pm 1.5$ | 0.33 | 0.28 | -69.2 |
| PJ144653 | $901   \pm 49$ | 24.3 $\pm$ 0.2 | 2.5 $\pm$ 0.4 | $0.27\pm0.03$ | $2.2 \pm 0.2$ | 0.41 | 0.37 | 49.4 |
| PJ144958 | $400   \pm 16$ | 24.4 $\pm$ 0.8 | 2.6 $\pm$ 1.0 | $0.30\pm0.18$ | $2.5 \pm 1.5$ | 0.41 | 0.38 | 61.7 |
| PJ160722 | $162   \pm 9$ | 23.9 $\pm$ 0.3 | 2.4 $\pm$ 0.6 | $0.34\pm0.05$ | $2.9 \pm 0.4$ | 0.47 | 0.37 | -1.1 |
| PJ231356 | $3244  \pm 163^\dagger$ | $^\dagger$ | $^\dagger$ | $^\dagger$ | $^\dagger$ | 0.43 | 0.29 | 44.2 |
|  |  |  |  |  |  |  |  |  |

![](figs/q_FIR_vs_z.png)

### Radio-FIR correlation and intrinsic radio source size

The well-studied correlation between radio and FIR flux (e.g., (cite: Helou:1985aa; Condon:1992aa; Yun:2001aa; Bell:2003aa; Murphy:2006aa; Murphy:2006ab)) is interpreted to be the result of the far-IR probing heated dust surrounding star-forming regions and the radio capturing

synchrotron emission from relativistic electrons originating from supernova remnants. As the latter are the end-product of massive star formation, these two proxies are tightly correlated when averaged over galactic scales.

The correlation even holds seemingly at sub-galactic scales (e.g. (cite: Tabatabaei:2007aa; Dumas:2011aa)),

which may be explained by the more efficient propagation of relativistic cosmic rays in the dense ISM, with its higher magnetic field density.

The correlation parameter $q_{\rm FIR}$ is computed as $$\begin{align}
q_{\rm FIR} = & \log[L_{\rm FIR} / (3.75 \times 10^{12}~ {\rm W})] \nonumber \\ 
& - \log[L_{\rm 1.4~GHz} / (1~{\rm W~Hz}^{-1})] 
\end{align}$$

where we determine $L_{\rm 1.4~GHz}$ from 6 GHz flux as $$\begin{align}
\frac{L_{\rm 1.4~GHz}}{{\rm W~Hz}^{-1}} = & \frac{1}{\mu_{\rm radio}} \frac{4\pi}{(1+z)^{1-\alpha}} \bigg( \frac{D_L(z)}{1~ {\rm m}}\bigg)^2 \\
& \times 
\bigg(\frac{S_{\rm 6 GHz}}{10^{32}~\mu{\rm Jy}} \bigg) \bigg(\frac{\rm 1.4~GHz}{\rm 6~GHz}\bigg)^{-\alpha} 
\end{align}$$ for luminosity distance $D_L$ in meters and spectral index $\alpha$ (assumed here to be 0.8; (cite: Condon:1992aa)) such that $S_\nu \propto \nu^{-\alpha}$.

These luminosities (corrected for lensing magnification $\mu_{\rm radio}$) are included in Table [\[tab:effective_radii_VLA\]](#tab:effective_radii_VLA), along with the corresponding values of $q_{\rm FIR}$.

We find values ranging from $q_{\rm FIR} = 2.0 - 3.1$, with a median of 2.3 and $1\sigma$ dispersion of 0.3, in agreement with the mean found by (cite: Yun:2001aa) for local IR-selected galaxies, $q_{\rm FIR} = 2.34$. This is also in good agreement with more recent results for *Herschel*-selected lenses from (cite: Giulietti:2022aa), who found a $2\sigma$ dispersion of $q_{\rm FIR} \approx 1.9 - 2.9$.

Unsurprisingly, none of the star-formation-dominated PASSAGES galaxies fall below the $q_{\rm FIR} < 1.8$ threshold for AGN-powered radio sources proposed by (cite: Condon:2002aa).

As shown in Fig. [8](#fig:radioFIRcorr_z), there is not an evident decline in the $q_{\rm FIR}$ parameter with redshift for PASSAGES galaxies.

As discussed extensively by (cite: Sargent:2010aa), any observed trend with redshift is heavily dependent on selection biases from objects selected only in the IR or radio. Accounting for this affect, (cite: Sargent:2010aa) found no evolution in the correlation out to at least $z\sim1.4$ (see also (cite: Sargent:2010ab)).

However, (cite: Magnelli:2015aa) and (cite: Delhaize:2017aa), both using a joint radio/FIR selection, observed similar redshift evolution in $q_{\rm FIR}$ to smaller values.

Moreover, for *Herschel*-selected lensed DSFGs, (cite: Giulietti:2022aa) remarked upon a weak but detectable trend in line with previous results.

(cite: Delhaize:2017aa) consider the possibility that contributions of AGN in the radio regime alone for star-forming galaxies could result in a steepening of the evolution with redshift.

Alternatively, it is possible the calculation of $q_{\rm FIR}$ for PASSAGES galaxies is weakened by the assumption of a single radio spectral index $\alpha$, rather than direct measurement for each galaxy.

As also noted by (cite: Delhaize:2017aa), for these higher-frequency measurements at 6 GHz, free-free emission (following instead $S_\nu \propto \nu^{-0.1}$) may contribute non-trivially at rest-frame $\nu \gtrsim 20$ GHz (cite: Condon:1992aa).

Under a different assumption of a flatter spectral index $\alpha = 0.5$ (similar to that of extreme local starbursts, e.g., (cite: Condon:1991aa; Clemens:2008aa)), we would find values of $q_{\rm FIR}$ greater than those reported in Table [\[tab:effective_radii_VLA\]](#tab:effective_radii_VLA) by a small amount, $q_{{\rm FIR}, \alpha=0.5} -  q_{{\rm FIR}, \alpha=0.8} = 0.3 - 0.4$.

This change in $q_{\rm FIR}$ is not insignificant, but it is smaller than the dispersion we find in $q_{\rm FIR}$ for our sample, and not much larger than the uncertainty on $q_{\rm FIR}$ for any individual object, so we conclude that the possible effect on our interpretation is minimal.

![image](figs/Reff_ratio_log_vs_Sigma_SFR_and_LIR.png) ![image](figs/Reff_ratio_log_vs_qFIR.png)

In Figs. [9](#fig:Reff_comparison) and [10](#fig:z_Reff), we examine the distribution of effective radii for our sample in both the rest-frame far-IR and radio, in comparison with far-IR sizes from (cite: Bussmann:2013aa) and (cite: Spilker:2016aa).

As both are expected to delineate the extent of ongoing massive star formation, the radio and far-IR sizes are reasonably consistent (where both are measurable), with discrepancies possibly explained partly by different observing resolutions.

While not for the same set of galaxies, (cite: Murphy:2017aa) found 10 GHz radio sizes comparable to the median dust-emission sizes of DSFGs from (cite: Ikarashi:2015aa) and (cite: Simpson:2015ab); see also (cite: Jimenez-Andrade:2019aa) at 3 GHz.

As a caution, however, the 1.4 GHz radio sizes for the same DSFGs from (cite: Simpson:2015ab) (presented in (cite: Biggs:2008aa)) are typically twice as large as the 870 $\mu$m sizes.

This comparison of continuum size at different wavelengths could instead be the result of different optical depths, or even different surface brightness sensitivities between the two sets of observations.

(cite: Simpson:2015ab) suggested that the larger diffusion scale for cosmic rays (of order $\sim1-2$ kpc; (cite: Bicay:1990aa; Marsh:1998aa; Murphy:2006ab)) might be responsible, relative to the smaller $\sim100$ pc diffusion length for the far-IR photons (which also explains why the radio-FIR correlation begins to decouple at resolved sub-kpc scales).

Fig. [9](#fig:Reff_comparison) shows the ratio of 1 mm to 6 GHz effective radii vs. $L_{\rm IR}$ and $\Sigma_{\rm SFR}$ for the 10 objects with both radii measured, and there is a discernible trend where the more luminous, more densely star-forming galaxies have preferentially more compact dust emission regions (or conversely, perhaps more extended radio emission). When excluding the lower-luminosity object PJ014341, this negative correlation with luminosity is significant at $p\lesssim0.01$.

(cite: Murphy:2006ab) suggested that galaxies with larger IR surface densities had undergone a more recent episode of star formation, such that young cosmic rays would only have had time to travel $\sim 100$ pc, leading to smaller radio scale lengths.

Curiously, this appears not to be the case for our sample,

which instead shows larger radio scales with larger $\Sigma_{\rm SFR}$, but it’s not currently practical to draw conclusions based on this sample.

However, in local edge-on galaxies, (cite: Wiegert:2015aa) also found preliminary evidence for a correlation of radio halo size with $\Sigma_{\rm SFR}$, such that a compact star formation distribution was advantageous to creating radio halos (also (cite: Dahlem:2006aa)).

Yet, (cite: Heesen:2018aa) did not find a strong correlation between radio scale height and SFR, $\Sigma_{\rm SFR}$, or galaxy rotation speed, for both diffusion- vs. advection-dominated (or wind-driven) modes of cosmic ray transport.

Lastly, in Fig. [9](#fig:Reff_comparison), we examine the same size ratio as a function of the radio-FIR correlation parameter, $q_{\rm FIR}$. There is again some weak indication of a negative correlation, but not with sufficient statistical significance given uncertainties.

Such a correlation might reveal the influence of an AGN in driving towards more compact radio half-light sizes.

![](figs/Reff_vs_z.png)

### Redshift evolution of galaxy size

(cite: Fujimoto:2017aa) found modest evolution in the $R_e-L_{\rm FIR}$ relationship between $z=1-2$ and $z=2-4$, and a more significant evolution (by a factor of $\sim 2$) to $z=4-6$. This decrease in effective radius with redshift for a given luminosity is consistent with rest-frame UV/optical samples.

For example, (cite: Shibuya:2015aa) found that the UV/optical effective radius of UV-luminous star-forming galaxies evolves with redshift as $R_{e, {\rm UV}}/{\rm kpc} \propto (1+z)^{-0.84 \pm 0.11}$. While the slope between $R_e$ and UV luminosity is consistent with redshift, the normalization decreases for the range $z=0-8$.

At longer wavelengths, (cite: Jimenez-Andrade:2021aa) found at 3 GHz that $R_{e, {\rm radio}}/{\rm kpc} \propto (1+z)^{-0.3 \pm 0.3}$ from $z\approx 0.3-3$, while (cite: Lindroos:2018aa) found steeper evolution at 1.4 GHz of $R_{e, {\rm radio}}/{\rm kpc} \propto (1+z)^{-1.7}$ out to $z\approx3$.

These results suggest that the correlation between luminosity and effective radius holds across cosmic time, but the size of an object with fixed luminosity decreases with lookback time. In turn, the surface density of star formation appears to increase with lookback time.

In Fig. [10](#fig:z_Reff), we

do not observe a clear indication of redshift evolution for the PASSAGES sample alone, covering only $z=1-3.5$, as is also the case for the *Herschel*-selected objects at a similar redshift range (cite: Bussmann:2013aa).

While the average far-IR size is elevated for PASSAGES relative to the (cite: Bussmann:2013aa) sample, there is significant overlap in the observed size range.

This minimal evolution in far-IR size matches the results found by (cite: Wang:2022ac) for stacked main-sequence galaxies from $z = 0.4 - 3.6$, in three stellar mass bins: high ($11.0 \le {\rm log}_{10} M_\star < 12.0$), mid ($10.5 \le {\rm log}_{10} M_\star < 11.0$), and low ($10.0 \le {\rm log}_{10} M_\star < 10.5$).

We find also that these main-sequence sizes are typically smaller than those found for the DSFGs in this work, but not much further than the level of $1\sigma$ uncertainties of each bin.

On the other hand, for the higher-redshift SPT sample ($z=3-6$), there is hardly any overlap in effective radius with PASSAGES galaxies, the latter of which are systematically larger in size.

This systematic discrepancy in sizes above vs. below $z\sim 3$

be a signpost of redshift evolution in DSFGs, but

this direct comparison is

complicated slightly by

the different selection effects at play for each sample.

## Eddington-limited star-formation surface densities?

As the DSFGs in this sample are among the most strongly star-forming systems presently known (cite: Berman:2022aa), they offer key insight into effective maximum thresholds of star formation (e.g. (cite: Elmegreen:1999aa; Tacconi:2006aa)).

In particular, stellar mass growth is understood to be a self-regulating process: as gas collapses under self-gravity to form stars, the short-lived, massive stars inject a sizable radiation pressure in opposition to dust grains, which are coupled to the remaining gas (cite: Thompson:2005aa).

The concept that radiation pressure can have significant influence on star formation is not novel (e.g. (cite: Elmegreen:1983aa; Scoville:2001aa; Scoville:2003aa)); it can even induce star formation in other regions of a cloud (e.g. (cite: Elmegreen:1977aa)).

(cite: Scoville:2001aa)

derived that a luminosity-to-mass ratio of a star cluster of $\sim 500 ~ L_\odot / M_\odot$ would provide a radiation pressure in excess of its self-gravity and halt accretion to the cloud coreanalogous to the so-called Eddington limitand by extension, on galaxy-wide scales as well. This is a conservative theoretical limit, assuming only free-fall collapse and no other turbulence- or magnetic-driven obstacles to molecular core accretion. It also does not consider the likely possibility of asymmetric cloud geometries reducing the importance of radiation pressure.

Additionally, this limit does not account for mechanical feedback contributed by stellar winds, which may well be an important factor (e.g. (cite: Tan:2001aa; Harper-Clark:2009aa; Rogers:2013aa)).

The vast majority of DSFGs and luminous IR galaxies appear to form stars at sub-Eddington rates (cite: Tacconi:2006aa; Hodge:2015aa; Hodge:2019aa) with the exception of some local LIRGs and ULIRGs (e.g. (cite: Barcos-Munoz:2017aa)). One example is the prototypical Arp 220 (cite: Scoville:1997aa; Downes:1998aa), which has star formation surface densitiesdefined as $\Sigma_{\rm SFR} = {\rm SFR}/(2\pi {R_{\rm eff, dust}}^2)$on the order of $10^4~{M}_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2}$, likely the highest-known value (cite: Barcos-Munoz:2015aa).

Here, $\Sigma_{\rm SFR} \approx 1000~{M}_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2}$, or $\Sigma_{\rm IR} \approx 10^{13}~L_\odot~{\rm kpc}^{-2}$ (cite: Thompson:2005aa; Andrews:2011ab), is the typical Eddington limit

for a star-forming system in equilibrium.

There is some evidence for near-Eddington star formation for a small number of high-$z$ objects, including the submillimeter-bright galaxies GN20 and AzTEC-1 (cite: Younger:2008aa; Daddi:2009aa);

AzTEC2-A (cite: Jimenez-Andrade:2020aa);

AzTEC-3 (cite: Riechers:2014aa);

HFLS3 (cite: Riechers:2013aa);

the Cosmic Eyelash (cite: Thomson:2015aa);

SGP38326 (cite: Oteo:2016aa);

SPT0346-52 (cite: Ma:2016aa);

ALMACAL-1 and ALMACAL-2 (cite: Oteo:2017ac);

ADFS-27 (cite: Riechers:2017aa);

and, more recently, the Sunrise Arc (cite: Vanzella:2019aa; Welch:2022ab).

Some quasar hosts have also shown evidence for such compact, maximal starbursts,

at $z\sim2$ (cite: Stacey:2021ab)

and $z>6$ (cite: Walter:2009aa).

However, angular resolution plays a critical role in this measurement, as it may be possible for objects to be sub-Eddington on global, galaxy-integrated scales but super-Eddington in local regions of dense star formation, as suggested by (cite: Simpson:2015ab) and (cite: Barcos-Munoz:2017aa).

For example, for local ULIRGs, (cite: Song:2022aa) found radio continuum clumps smaller than 100 pc with large surface densities up to $\Sigma_{\rm SFR} \approx 1600 ~{M}_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2}$.

Yet, a vexing result has been the discovery that high-redshift DSFGs almost universally do not exceed the Eddington limit even at $\sim$500pc scales, as accessed by very high-resolution ALMA imaging and/or strong lensing (e.g. (cite: Bussmann:2012aa; Bussmann:2013aa; Rybak:2015aa; Enia:2018aa; Hodge:2019aa; Dudzeviciute:2020aa)).

In particular, in the case of (cite: Rybak:2015aa), the star formation surface density of SDP.81 is mapped at sub-50pc scales (unprecedented at high-$z$), giving a maximum of $190\pm20~{M}_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2}$, significantly under the theoretical limit.

This also appears to be the case for the PASSAGES sample studied so far, as shown in Fig. [6](#fig:LIR_Reff_lensed) and [7](#fig:LIR_Reff) and Table [3](#tab:effective_radii).

In contrast, turbulence-based ISM modeling of the full sample by (cite: Harrington:2021aa) revealed several objects approaching $L_{\rm IR} / M_{\rm ISM} = 500 L_{\odot}/M_{\odot}$, but most of these are coincidentally excluded from our measurement, owing to their lack of either ALMA observations or fully-developed lens models.

In line with (cite: Hodge:2015aa; Hodge:2019aa), we also estimate the peak values of $\Sigma_{\rm SFR}$ in Table [3](#tab:effective_radii) by normalizing the 1 mm flux density to equal the SFR, effectively assuming that the spatial distribution at sub-mm wavelengths directly traces the distribution of star formation (also (cite: Hatsukade:2015aa; Tadaki:2018aa; Sharon:2019ab)).

Unlike (cite: Hodge:2019aa), however, this calculation applied towards lensed galaxies is complicated by the varying source-plane PSF. To mitigate this, we compute the 99.7th percentile (i.e. the 3$\sigma$ confidence interval of pixel values) as a lower bounds on $\Sigma_{\rm SFR, peak}$.

This helps to mitigate any spurious non-physical artifacts introduced by the lensing reconstruction, and also accounts partially for the correlation of adjacent pixels within a beam size.

In future work, with higher angular resolution observations, it will be worthwhile to construct smoothed (i.e. uniform PSF) maps of $\Sigma_{\rm SFR}$, but the current ALMA data are only marginally able to resolve this distribution. For this reason, the peak values given in Table [3](#tab:effective_radii) are usually consistent with globally-averaged values, which is what one would expect for source sizes comparable in extent to the resolving beam.

While it is clear that 100pc-scale imaging is essential to properly assess these maximum surface densities,

there may be other factors responsible.

One such factor, as pointed out by (cite: Hodge:2019aa), might be the assumption of a single dust temperature, leading to a possible underestimation of the overall SFR (cite: Berman:2022aa). For example, (cite: Calistro-Rivera:2018aa) find evidence for linear temperature gradients in four DSFGs, decreasing from the center to outer parts of the disk, which would directly affect the peak values of $\Sigma_{\rm SFR}$.

Still, it is not likely that this effect can fully account for the order-of-magnitude discrepancy in $\Sigma_{\rm SFR}$ below the Eddington limit. $\Sigma_{\rm SFR}$ scales linearly with star-formation rate, but scales with inverse-square dependence on galaxy size, so the latter is a more facile explanation.

Additionally, (cite: Andrews:2011ab) and (cite: Murray:2010aa) point out that intermittency and non-uniformity of star formation over the extent of a galaxy can lead to a global star-formation surface density that appears significantly more sub-Eddington than if higher spatial and temporal resolution were achieved.

Ultimately, a larger sample of sub-100pc dust continuum observations of DSFGs is required to make more substantive claims,

and we intend to pursue this in the future with a more thorough, higher-resolution analysis of the PASSAGES sample.

![](figs/M_enc_vs_mag_w_VLA.png)

## Connection of lensing halo mass to magnification

The distribution of Einstein radii (and masses enclosed within these radii) is summarized in Table [2](#tab:lensproperties) (also Lowenthal et al.,

in prep.).

As remarked by (cite: Frye:2019aa) (see their Figure 1), the objects selected via *Planck*-*Herschel* or *Planck*-WISE have a tendency for larger far-IR flux and Einstein radii,

perhaps resulting from the larger-area footprint of *Planck*.

The median Einstein radius is found to be $\sim 1.5^{\prime\prime}$, in contrast with the smaller median of $\sim 0.8^{\prime\prime}$ for the *Herschel* lenses of (cite: Eales:2015ab) and (cite: Amvrosiadis:2018aa).

While the clear majority are galaxy-scale lenses, the total halo masses enclosed within the Einstein radius for PASSAGES ranges from $1\times10^{10}$ to $\sim 3 \times 10^{13}~M_\odot$, covering galaxy, group, and low-mass cluster scales.

There is not a systematic effect where the most luminous objects in the sky are all high-magnification cluster-lensed DSFGs; galaxy-scale lenses are just as capable of producing lensed DSFGs with large fluxes.

The source-plane area inside the caustic curves that is capable of producing high magnifications (or lensing cross-section; (cite: Turner:1984aa; Meneghetti:2003ab)) has been found to correlate tightly with

the Einstein radius (regardless of definition; (cite: Meneghetti:2011aa)).

By extension, as $\theta_{\rm Ein} \propto \sqrt{M}$, this cross-section also should correlate with lensing mass.

This effect might be at play in Fig. [11](#fig:M_enc), which shows a positive correlation between magnification and the mass enclosed within the Einstein radius.

As a general rule-of-thumb, magnification scales approximately as $\mu \propto \sqrt{M_{\rm lens}}$ for a circularly symmetric lens (assuming fixed source position; see e.g. (cite: Narayan:1996aa; Frye:2019aa)).

Additional factors play a large role in determining magnificationincluding perhaps most notably the alignment of background relative to the foreground mass profileso there should be large scatter in this relation. We thus do not consider it instructive to parameterize it, but we remark that the distribution of PASSAGES objects in this work is broadly consistent with this trend (shown in Fig. [11](#fig:M_enc)).

Building on this,

since

we recall that more extended source-plane objects may also be subject to lower overall magnification factors than compact ones (e.g. (cite: Hezaveh:2012aa)), then a useful parameter might be the ratio of galaxy angular size (effective radius) to the angular Einstein radius of the lens, $R_0 \equiv R_{\rm e} / \theta_{\rm Ein}$.

If this ratio is close to unity, the size of the background object would be comparable to the areal extent of the caustic network.

Larger values would necessitate (in general) that the source extends further into lower-magnification regions, resulting in lower, more diluted magnifications. Smaller values, on the other hand, would suggest that the background object can carefully align inside the caustics.

As remarked in §[4.3.1](#sec:size_bias), however, smaller source-plane objects have a lower probability of being near to the high-magnification region of the source-plane when positioned at random.

Ideally, one can describe a balance between these two competing effects.

For a general SIS lens, (cite: de-Freitas:2018aa) derived analytic, perturbative solutions for the source-plane cross-sections $\sigma_\mu$or the solid angle of the region with magnifications exceeding some threshold $\mu_{\rm thr}$as a piecewise function of $R_0$:

$$\begin{align}
\label{eqn:deF}
\sigma_\mu &= 
    \begin{cases}
    \frac{4\pi}{\mu_{\rm thr}^2} + \frac{\pi}{4}R_0^2, & R_0 <  R_J \\
    \pi (4 R_0^2 - \mu_{\rm thr} R_0^3) \\
    \hspace{1cm}
    - \frac{1}{R_0^2} 
    \big( 
    \frac{3\pi - 8}{(4 - 8/\pi)^2} 
    \big) \\
    \hspace{1cm}
    \times
    (4 R_0^2 - \mu_{\rm thr} R_0^3)^2, & R_0 \ge R_J
    \end{cases}
\end{align}$$ where the joining point $R_J = 2.15 / \mu_{\rm thr}$ marks a transitional point to the Einstein ring regime. As $\sigma_\mu$ is relative to the Einstein radius, it can be multiplied by $R_0^2$ to obtain an absolute solid angle (e.g. in arcsec$^2$).

This treatment implies that the peak area for $\mu_{\rm thr} = 5$ is approximately $R_0 = 0.6$ (i.e., source size 60% of the Einstein radius).

![](figs/R_ratio_vs_mag_deFreitas18_2dpcolormesh_w_curves.png)

These analytic curves are shown in the bottom panel of Fig. [12](#fig:size_ratio_mag).

For given magnification $\mu$, the cross-sectional area $\sigma_\mu$ essentially describes the probability of a given $R_0$ ratio.

We find that the peaks for the selected magnification thresholds ($\mu_{\rm thr} = 5, 10,$ and 20) are approximately concordant with the negative correlation seen in the upper panel of Fig. [12](#fig:size_ratio_mag) for the PASSAGES sample, as indicated by the conjoined vertical/horizontal dotted lines.

Specifically, the local maxima of $\sigma_\mu$ in Equation [\[eqn:deF\]](#eqn:deF) are found to occur at $\mu(R_0) \approx 2.9522 / R_0$, shown as a solid black line in Fig. [12](#fig:size_ratio_mag).

There is perhaps greater deviation from this relation for smaller values of $R_0$, but there are also fewer objects occupying this regime, so the deviation is not a robust conclusion.

The relative probability of lower-magnification lenses is higher, as $\sigma_\mu \sim \mu_{\rm thr}^{-2}$, which would suggest that they would be more numerous. However, this will not be fully reflected for the PASSAGES sample, as the selection

is not uniformly sensitive to all magnifications.

This is because selection by apparent flux serves to maximize the multiplicative product of magnification and intrinsic luminosity (the latter of which is itself correlated with source-plane size, as discussed in §[4.3.2](#sec:FIR_size)).

For this reason, the recovered distributions of intrinsic luminosities, magnifications, Einstein radii, and source-plane sizes are all interconnected for PASSAGES and other lensing samples defined by flux.

In future work (Englert at al., in prep.),

we intend to place the PASSAGES sample in context with other studies that have used magnification and Einstein radius distributions as constraints on the halo mass function and other cosmological parameters (e.g., (cite: Eales:2015ab; Amvrosiadis:2018aa)). This is an analysis which benefits immensely from a large sample with consistent selection effects.

# Conclusions

We have presented detailed lens modeling for 15 members of the PASSAGES (*Planck* All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts) sample of dusty star-forming galaxies ($z=1.1 - 3.3$) that were introduced in (cite: Harrington:2016aa) and (cite: Berman:2022aa). To do this, we gather complementary information from an extensive set of recent multi-wavelength sub-arcsecond continuum imaging with ALMA, JVLA, *HST*, and Gemini-S. We implement parametric lens modeling with LENSTOOL, where priors on the nature of the foreground mass distribution are established by optical/near-IR imaging, and multiple image positions of background objects (from imaging at all wavelengths) provide modeling constraints.

In analyzing the results of this modeling and the resultant source-plane reconstructions, we find:

- The 1 mm and 6 GHz magnification factors of the DSFGs modeled in this sample range from $\mu=2-28$, with more than half at lower magnification, $\mu < 10$.

  Correcting the apparent infrared luminosities from (cite: Harrington:2016aa) and (cite: Berman:2022aa) with these magnification factors, we find intrinsic values of $L_{\rm IR} = 0.2-5.9\times 10^{13}~L_{\odot}$ (median $1.4\times 10^{13}~L_{\odot}$), placing them solidly within the regime of hyperluminous infrared galaxies, or HyLIRGs (Fig. [3](#fig:corrected_luminosities)).

  The corresponding inferred star formation rates (also corrected for lensing) span $200-6300~M_\odot~{\rm yr}^{-1}$ (median $1500~M_\odot~{\rm yr}^{-1}$).

  Their extreme, rare properties are

  likely to be a direct result of the all-sky selection method for PASSAGES.

  While initially assumed to be starbursts based on their large star formation rates, evidence from their molecular gas depletion times and star formation rate surface densities indicates thatwhile nearly all above the center of the star-forming main sequencethey largely are not predicted to surpass a $\Delta {\rm MS} > 0.6$ dex threshold typically imposed to define starbursts.

  Future work to attempt to constrain stellar masses is thereby warranted in order to directly establish their relation to the main sequence.

- Despite being among the most IR-luminous galaxies ever discovered in the Universe, owing to their advantageous large-area selection, their submillimeter magnification factors are largely consistent with those of lensed DSFGs identified by the likes of *Herschel*, SPT, and ACT (cite: Bussmann:2012aa; Bussmann:2013aa; Bussmann:2015aa; Hezaveh:2013aa; Dye:2014aa; Dye:2018aa; Spilker:2016aa; Enia:2018aa; Rivera:2019aa; Liu:2022ad) and other *Planck*-selected lenses not in PASSAGES (cite: Canameras:2015aa; Canameras:2018ab); see Fig. [4](#fig:magnifications).

- In characterizing their de-lensed, spatial extents in the source plane at rest-frame far-IR and radio,

  we find that the PASSAGES DSFGs are generally more extended than typical DSFGs (both lensed and unlensed). Since they appear to be consistent with size-luminosity scaling relations for unlensed submm-bright objects (cite: Fujimoto:2017aa), we interpret their larger sizes to be a consequence of their higher star formation rates (or vice versa); see Figs. [6](#fig:LIR_Reff_lensed) and [7](#fig:LIR_Reff).

  They are consistent with a framework of some DSFGs being the result of active growing of and accretion of gas onto a star-forming disk,

  with a wider distribution of star formation than low-$z$ ULIRGs, which form stars in compact nuclear regions.

- We compute the radio-FIR correlation parameter $q_{\rm FIR}$ by assuming a single radio spectral index; the range of values for $q_{\rm FIR}$ is in line with those from (cite: Giulietti:2022aa) for *Herschel*-selected lenses, but we find no clear evolution with redshift, as predicted by some recent works. We also find that PASSAGES objects do not show signs of significant contributions from AGN, which might be indicated by a radio excess, $q_{\rm FIR} < 1.8$.

- In comparing their radio vs. sub-mm sizes, we find some weak dependence on $L_{\rm IR}$, $\Sigma_{\rm SFR}$, and the radio-FIR correlation parameter $q_{\rm FIR}$, with the more luminous and more densely star-forming galaxies having preferentially more compact 1 mm sizes (or more extended 6 GHz halos). Relative to $q_{\rm FIR}$, we find that galaxies closer to being AGN-powered (i.e. showing a radio excess) had generally smaller radio sizes, which might be indicating that deeply-buried AGN are leading to more compact half-light radii. At present, our conclusions are limited by the small number of 10 objects with both radio and FIR sizes measured.

- The larger sizes of PASSAGES galaxies (relative to the broader population of DSFGs) may also owe to their concentration around Cosmic Noon, $z<3.5$, in contrast to higher-$z$ DSFGs like (cite: Spilker:2016aa). Nonetheless, we observe no clear trend in size as a function of redshift for the narrow range covered by these PASSAGES objects (Fig. [10](#fig:z_Reff)).

  This agrees with recent results by (cite: Wang:2022ac) for the FIR size of stacked main-sequence galaxies and (cite: Jimenez-Andrade:2019aa) for the radio size of star-forming galaxies, which evolves only shallowly with redshift.

- There may be some size bias present in the sample (Fig. [5](#fig:size_bias)), by which more compact objects are capable of producing higher lensing magnifications (cite: Hezaveh:2012aa; Spilker:2016aa).

  We parameterize this effect by comparing magnifications with the ratio of the angular size of background objects to the Einstein radius of the foreground, and find a modest downward trend as expected (Fig. [12](#fig:size_ratio_mag)), which is in line with predictions for isothermal lenses (e.g. (cite: de-Freitas:2018aa)).

  That the PASSAGES sample is not fully coincident with the distribution of lensing cross-sections $\sigma_\mu$ as a function of the size ratio and magnification is an indication of the selection function at play, as we are not uniformly sensitive to all magnifications.

  Given the selection of these objects by flux, they are likely of an optimal size that is simultaneously sufficiently large to host high intrinsic luminosities and sufficiently small to align with higher-magnification regions of the source plane.

- Since the spatial extents of their star-forming regions are proportionally larger to match their extreme luminosities, the star-formation surface densities for PASSAGES are significantly sub-Eddington on global scales (in agreement with most DSFGs for which this measurement has been made).

  There is still certainly a possibility that their rapid stellar mass assembly is substantially regulated by radiation pressure, but this effect must be on sub-kpc scales not captured by these current $0.4^{\prime\prime}$ (image-plane) resolution ALMA images, perhaps over short timescales that are not contemporaneous between sites of star formation.

  For these observations, ALMA does not significantly resolve the far-IR continuum, and so the peak values of $\Sigma_{\rm SFR}$ in each object are not much larger than the respective globally-averaged values.

  In the future, we hope to repeat this analysis with higher angular resolution from ALMA to properly assess the densities of star formation, which we expect may be clumpy and extended beyond just nuclear regions.

# Acknowledgments

.

PSK would like to thank Belén Alcalde Pampliega and Lilah Mercadante for helpful discussions related to this work, and the scientific staff at the NRAO Array Operations Center for assistance with data reduction.

PSK gratefully acknowledges support from the NRAO Student Observing Support (SOS) award SOSPA7-019 and the Massachusetts Space Grant Consortium.

This research is based on observations made with the NASA/ESA *Hubble Space Telescope* obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5. These observations are associated with programs GO-14653 and GO-14223. Support for program GO-14653 was provided by NASA through a grant from the Space Telescope Science Institute.

Some of the data presented in this paper were obtained from the Multimission Archive at the Space Telescope Science Institute (MAST).

This paper makes use of the following ALMA data: ADS/JAO.ALMA #2017.1.01214.S, #2015.1.01518.S, #2019.1.01636.S.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This work is based in part on observations obtained at the international Gemini Observatory, a program of NSF’s NOIRLab (acquired through the Gemini Observatory Archive and processed using the Gemini IRAF package), which is managed by the Association of Universities for Research in Astronomy (AURA) under a cooperative agreement with the National Science Foundation on behalf of the Gemini Observatory partnership: the National Science Foundation (United States), National Research Council (Canada), Agencia Nacional de Investigación y Desarrollo (Chile), Ministerio de Ciencia, Tecnología e Innovación (Argentina), Ministério da Ciência, Tecnologia, Inovações e Comunicações (Brazil), and Korea Astronomy and Space Science Institute (Republic of Korea).

This research has made use of NASA’s Astrophysics Data System,

of APLpy, an open-source plotting package for Python (cite: Robitaille:2012aa),

and of Astropy, a community-developed core Python package for Astronomy (cite: Astropy-Collaboration:2013aa).

# Facilities

HST(WFC3), LMT, ALMA, JVLA, Gemini

# Software

astropy (cite: Astropy-Collaboration:2013aa; Astropy-Collaboration:2018aa), LENSTOOL(cite: Kneib:1993aa; Kneib:1996aa; Jullo:2007aa; Jullo:2009aa), APLpy (cite: Robitaille:2012aa), IRAF (cite: Tody:1986aa; Tody:1993aa; Science-Software-Branch-at-STScI:2012aa), CASA (cite: McMullin:2007aa), Ned Wright’s Cosmology Calculator (cite: Wright:2006aa)

# Notes on individual objects

Section 5 of (cite: Harrington:2016aa) and Appendix B of (cite: Berman:2022aa) provide notes on each member of the larger PASSAGES sample (in addition to

Table 1 of (cite: Harrington:2021aa)).

In this section, we review the information necessary for our lens models, including spectroscopic redshifts of the background DSFGs, photometric/spectroscopic redshifts of foreground objects, and multiple image morphologies, summarized in Table [1](#tab:sample).

**PJ011646.** This galaxy-scale lens system appears to consist of multiple background components lensed by an elliptical galaxy with a

spectroscopic redshift of $z_{\rm spec} = 0.555$ determined with VLT MUSE observations (Kamieneski et al., in prep.).

There is a smaller, secondary foreground galaxy of unknown redshift to the northeast, but it has minimal impact on the lensing morphology and so we exclude it from our model. The foreground elliptical is modeled with our standard approach: an SIE profile with centroid, ellipticity, orientation, and velocity dispersion all kept as free parameters. The DSFG, with a CO(3-2) detection at $z = 2.125$ by LMT/RSR (cite: Berman:2022aa), is detected as two primary arcs in ALMA and JVLA imaging and appears to spatially coincide with a bright double image detected by *HST* (labeled $2ab$ in Figure [1](#fig:postage_stamps)). Another image family (labeled $1abcd$) is a clear quad image, nearly spatially coincident with family $2ab$ but noticeably bluer in the RGB image with Gemini $r'$ and $z'$ (Fig. [1](#fig:postage_stamps)). It is not entirely clear if this image family is located at the same redshift as $2ab$, but since the two families have very similar Einstein radii

and appear to be lensed by virtually the same foreground mass profile, then this should dictate that the background objects lie at similar redshifts. Within the Einstein radius uncertainty for this object (see discussion in Section [3.5](#sec:Einstein_radius)), $\theta_{\rm Ein,eq} = 2.34 - 2.41^{\prime\prime}$, and holding other quantities fixed, this corresponds to a redshift uncertainty of $z\approx 2.0 - 2.4$ (assuming $z_{\rm lens} = 0.555$).

For the purposes of deriving our lens models, it is sufficient to assume that they lie at the same redshift. Given the proximity of this quad component and the doubly-imaged DSFG component in the source plane ($\lesssim 1^{\prime\prime}$, 8.5 kpc at the CO-derived redshift), it seems most likely that these two components may be interacting (or else a very serendipitous alignment of two objects around $z\sim2$).

We also note that these multiple components are aligned with the foreground in such a way as to cover most of the caustic curve region so that there is a very complex set of concentric, partial Einstein ring structures in the image plane, offering excellent constraints on the mass of the foreground elliptical, $(1.54 \pm 0.03) \times 10^{12} M_\odot$ within the Einstein radius at $z_{\rm lens}=0.555$ (see Table [2](#tab:lensproperties)).

**PJ014341.**

This compact galaxy-scale lens is one of the lowest-redshift members of our sample, with a CO(2-1) detection from the background DSFG at $z=1.096$. The lensing foreground galaxy is detected spectroscopically at $z_{\rm spec}=0.594$ from SDSS (cite: Berman:2022aa). Its small Einstein radius of $\approx 0.5^{\prime\prime}$ (on the lower end of our sample, see Table [2](#tab:lensproperties)) is due primarily to the small separation in redshift space between the lens and source planes. The enclosed foreground mass is $(1.3 \pm 0.3) \times 10^{11} M_\odot$. The redshift geometry also has the consequence of making lensed image identification difficult, as they are likely heavily blended with foreground light in the optical (Fig. [1](#fig:postage_stamps)), and only marginally resolved beyond the beam size in the interferometric ALMA/JVLA images.

Nonetheless, the image morphology is consistent with a classic 4-image fold-caustic geometry, with two isolated images and an additional merging pair (Fig. [2](#fig:model_SP)).

The radio morphology is similar (Fig. [2](#fig:model_SP))

but more difficult to interpret due to its lower signal-to-noise, so it is not included as a constraint in this iteration of the model.

Given the compactness of the lensing configuration, the source-plane area subtended by the caustic curve is likely smaller than or similar in size to the DSFG, so slight offsets between radio and far-IR emitting regions can result in very different image morphologies.

There appear to be other foreground objects nearby, but given the compactness of the lensing configuration, we only parameterize the primary deflector with our standard SIE model.

The best-fit model finds a high ellipticity, $e=0.77^{+0.15}_{-0.21}$, which suggests these other foreground deflectors may contribute non-trivially. A refined model with more available constraints in the future might allow for a more complex mass distribution.

**PJ020941.**

Also known as *9io9* or the “Red Radio Ring", PJ020941 has been studied at length by (cite: Geach:2015aa; Geach:2018aa), (cite: Harrington:2016aa; Harrington:2019ab), (cite: Rivera:2019aa), (cite: Doherty:2020aa), and (cite: Liu:2022ad).

A comparison of our lens model with existing models is provided in Appendix [10](#sec:lens_model_comparison).

The target was first revealed by the gravitational lens citizen science project Space Warps (cite: Geach:2015aa; Marshall:2016aa; More:2016ab) before it was identified independently as a strong sub-millimeter source in surveys by *Planck* (cite: Harrington:2016aa), the Atacama Cosmology Telescope (cite: Su:2017aa; Gralla:2020aa), and *Herschel* (cite: Viero:2014aa). Near-infrared $i$-band and $J/K_s$-band imaging from the VISTA-CFHT Stripe 82 survey (cite: Geach:2017ab) and CFHT-MegaCam Stripe 82 survey (cite: Moraes:2014aa) revealed a nearly complete, red Einstein ring (cite: Geach:2015aa), confirmed with high-resolution $H$-band *HST* imaging ((cite: Geach:2018aa), Lowenthal et al. in prep.).

The 1.4 GHz eMERLIN and 5 GHz JVLA radio images (cite: Geach:2015aa) show a partial Einstein ring that largely coincides spatially with the near-IR emission, which is also borne out by ALMA continuum and spectral line images ((cite: Geach:2018aa; Doherty:2020aa; Berman:2022aa); and this work).

PJ020941 has a CO(3-2) detection by LMT/RSR at $z=2.553$ (cite: Harrington:2016aa; Harrington:2021aa). It is strongly lensed by an elliptical galaxy (SDSS J020941.27+001558.5) at $z_{\rm fg} = 0.202$, and by a secondary galaxy assumed to lie at a similar redshift (which is expected to have a non-negligible influence on the lens, (cite: Rivera:2019aa)).

Both are included in our model, with a standard SIE approach for the primary elliptical, and an SIS model (with position held fixed to the centroid of the luminous component) for the secondary object.

The overall lens morphology consists of a double image, with an extended arc to the west and a less-magnified counter-image to the northeast. Recent Cycle 7 ALMA $\theta \sim 0.15^{\prime\prime}$ Band 6 (1.1 mm) continuum imaging (2019.1.01197.S, PI: P. Kamieneski; to be presented in forthcoming work by Kamieneski et al. in prep.) provides further information.

Embedded inside the extended arc are 3 distinct quad-imaged regions, suggestive of a cusp-caustic configuration, which can be identified by matching clumps and using parity information.

This is a commonly-observed lensing configuration where some portion of a galaxy crosses into the inner region of the caustic, which is readily apparent from the morphology in Fig. [2](#fig:model_SP).

This quadruply-imaged portion is also evident from subtle surface brightness peaks in the *HST* image (Fig. [1](#fig:postage_stamps)) that coincide with the 1 mm peaks.

**PJ022633.** This partial Einstein ring consists of a background object lensed primarily by a group of three foreground objects, assumed to lie at the same redshift.

The DSFG CO(3-2) detection is at $z=3.120$ (cite: Berman:2022aa), with the brightest lensing galaxy at $z=0.41$ (cite: Wen:2015aa).

Obvious lensing features include a bright, extended partial Einstein ring to the southeast (images $1bc$) and a counter-image to the northeast (image $1a$), with faint emission connecting the two (more apparent in the optical image).

There is some evidence that the lensed image expected to be located on the western side of the primary deflector (opposite the semi-ring) is split into two images by the secondary foreground galaxy to the northwest, visible faintly in $H$-band and at 6 GHz (images $1de$, Figs. [1](#fig:postage_stamps) and [2](#fig:model_SP)). The radio images are nearly spatially coincident with an extended double-lobed radio jet emanating from the primary foreground elliptical, and the *HST* image is affected by a bright star nearby, so confirmation of this proposed morphology is still pending.

However, this interpretation is motivated by the image predictions of a simple zeroth-order lens model including only the mass of the primary and secondary ellipticals.

The primary is modeled as an SIE profile, with the secondary as an SIS model, with its position allowed to vary to a small amount.

**PJ030510.** This object is a galaxy-scale (or small group-scale) lens, with a CO(3-2) detection of the DSFG at $z=2.263$ (cite: Harrington:2021aa; Berman:2022aa).

A preliminary red cluster sequence analysis (cite: Gladders:2000aa) yields a foreground redshift of $z_{\rm phot} = 0.4 - 0.5$.

Near-IR imaging by *HST* and Gemini reveal ring-like features surrounding two foreground galaxies in a dense environment. Our model parameterizes the combined mass contribution from both as an SIE model. ALMA 1 mm continuum imaging has a slightly larger beam size of $0.85\times0.59^{\prime\prime}$, which leaves the DSFG only marginally resolved. It appears to consist of two lensed images, one of which is notably fainter, on opposite sides of the foreground pair.

It is possible that higher-resolution imaging might reveal more of a cusp-like quadruple-image morphology, but at present, a double-image configuration is the best explanation.

**PJ105353.** This object was discovered independently by (cite: Harrington:2016aa) and (cite: Canameras:2015aa) (also referred to as “the Ruby" or PLCK_G244.8+54.9),

and has also been studied by (cite: Canameras:2017aa; Canameras:2017ab; Canameras:2021aa).

We compare our modeling results with theirs in Appendix [10](#sec:lens_model_comparison).

The lensing galaxy is at a higher redshift than most other PASSAGES objects, $z=1.525$, with a source redshift of $z=3.005$.

It is modeled as an SIE profile, with position, ellipticity, orientation, and velocity dispersion as free parameters.

As we discuss in Appendix [10](#sec:lens_model_comparison), CO(4-3) imaging presented in (cite: Canameras:2017aa) reveals a complicated image-plane structure, dominated by an apparent quadruply-imaged component

with no clear counterpart in rest-frame optical (see also (cite: Canameras:2017aa; Canameras:2017ab)), likely due to blending with the foreground as suggested by (cite: Frye:2019aa).

High-resolution ($0.07^{\prime\prime}$) 1 mm imaging with ALMA (PID 2015.1.01518.S, PI: N. Nesvadba), which was not directly included in the model by (cite: Canameras:2017aa), leads us to a slightly different conclusion on the quad-image configuration.

For this work, we utilize the Band 7 ($870\mu$m) continuum image to derive the dust magnification, as the observing setup (resolution $\gtrsim 0.15^{\prime\prime}$) is closer to that of the other objects.

**PJ112713.** This object has not been imaged by AzTEC or ALMA, but a CO(2-1) line was detected by RSR at $z=1.303$ (cite: Harrington:2021aa; Berman:2022aa). A photometric redshift for the lens was derived to be $z_{\rm phot} = 0.42$ (Lowenthal et al., in prep.) using SDSS. JVLA imaging indicates two arcs ($1ab$) separated by $\sim1^{\prime\prime}$, assumed to be the lensed DSFG, as there are no other bright radio sources within 1$^\prime$. There is also indication of an incomplete Einstein ring in HST imaging, surrounding a single foreground object, with an Einstein radius that approximately matches the 6 GHz arcs, $\theta_{\rm Ein} = 0.6^{\prime\prime}$.

The foreground galaxy is modeled with the standard SIE approach of this work.

Intriguingly, there are two bright peaks in the optical Einstein ring (denoted $2ab$) that roughly correspond to minima in the partial radio ring. We interpret this as possibly the result of radio continuum tracing sites of heavily dust-obscured active star formation, whereas the optical peaks arise from less-extincted sightlines. Both $1ab$ and $2ab$ are utilized as constraints for our lens model.

**PJ113805.** A single CO(2-1) line was detected by RSR and interpreted to lie at $z=2.019$ (cite: Harrington:2021aa; Berman:2022aa). ALMA imaging reveals a compact galaxy-scale lens that is not resolved into multiple components (due in part to a lower-resolution synthesized beam, $1.03 \times 0.66 ^{\prime\prime}$). The system is however resolved into two primary components by JVLA 6 GHz imaging (Fig. [2](#fig:model_SP)). These double images appear to nearly coincide with faint arcs detected by *HST* ($1ab$), although the latter are heavily contaminated by light from the foreground lensing elliptical, which has a photometric redshift from SDSS of $z_{\rm phot} = 0.52$. Since the radio peaks are slightly offset from the optical images, we add them as independent constraints ($2ab$), although they are likely to provide only minimal new information on the foreground mass.

Given the sparse number of model constraints, this object is modeled only as an SIS profile, with position and velocity dispersion as free parameters.

**PJ113921.** This object was discovered independently by (cite: Canameras:2015aa), identified as PLCK_G231.3+72.2, and later reported in (cite: Berman:2022aa).

Our model-derived magnification is compared with that of (cite: Canameras:2018ab) in Appendix [10](#sec:lens_model_comparison).

The RSR CO(3-2) line is interpreted from photometric support to be at $z=2.858$, in agreement with additional spectroscopic coverage (cite: Canameras:2018ab; Nesvadba:2019aa; Harrington:2021aa). ALMA partially resolves what appears to be a quad-image in 260 GHz continuum ($1abcd$), centered around a foreground elliptical with a photometric redshift of $z=0.57$ (cite: Berman:2022aa),

but likely perturbed by at least one other nearby galaxy. Our model here includes the primary lens as an SIE, and the deflecting galaxy to the west as a simple SIS profile. A faint red feature in *HST* is possibly affiliated with the background DSFG, as it is close to the ALMA continuum emission, or it may be associated with an apparent foreground spiral galaxy to the southeast. In this iteration of the model, we do not include this feature in constraining our lens model.

**PJ132630.** This object was discovered independently through our sample (cite: Berman:2022aa) and in the H-ATLAS survey (cite: Bussmann:2013aa; Yang:2017aa), known also as NAv1.195. A single CO(3–2) line was detected with RSR at $z=2.951$ (confirmed with spectroscopic follow-up by (cite: Yang:2017aa) and (cite: Harrington:2021aa)).

(cite: Bussmann:2013aa) published a lens model for 340 GHz imaging by the SMA ($\mu_{\rm 340 GHz} = 4.1\pm0.3$), with a lens redshift of $z_{\rm fg} = 0.786$.

We compare their results with our model in Appendix [10](#sec:lens_model_comparison).

ALMA and JVLA imaging reveals that the DSFG is doubly-imaged, with images separated by 3.7$^{\prime\prime}$ in the image plane ($3ab$). An optical counterpart appears to separate into two components that surround the long-wavelength emission; we label these image families $1ab$ and $2ab$ and include them separately in the model. There is evidence for additional background sources lensed by the foreground elliptical, which we model using a standard SIE, but they are at an unknown redshift and are thus not considered as constraints.

**PJ133634.** Two CO lines ($J=3-2$ and $J=4-3$) were detected by RSR at $z=3.254$ (cite: Harrington:2021aa; Berman:2022aa). A pair of primary lensing galaxies separated by 0.9$^{\prime\prime}$ have an SDSS photometric redshift of $z=0.26$. The 6 GHz continuum reveals a clumpy, partial Einstein ring, centered $\approx 0.2^{\prime\prime}$ east of the center of the foreground elliptical (likely due to a small perturbation by the secondary). This object is too northern to be visible to ALMA, but the 1.1 mm continuum from AzTEC (8.5$^{\prime\prime}$ beam) coincides with the radio continuum, which we thus interpret to originate from the *Planck* DSFG.

The radio ring consists of multiple clumps larger than the synthesized beam, and we identify 3 doubly-imaged families in the eastern counter-image and western semi-ring to be used in the model ($1ab$, $2ab$, and $3ab$), making use of the expected parity flip between the counter-image and more extended arc.

The foreground mass is modeled as a single SIE profile, as the effect of the secondary perturber is not large enough to break the degeneracy with the primary lens.

**PJ144653.** This lower-redshift member of our sample has a CO(2-1) line detected by RSR at $z=1.084$ (cite: Harrington:2021aa; Berman:2022aa). The lensing galaxy has an SDSS spectroscopic redshift of $z=0.493$, and has the appearance of a face-on spiral galaxy. However, some of the spiral-like structure may actually be the result of the multiply-imaged background DSFG. At present, it is not feasible to make this distinction without imaging in an additional filter with comparable quality to the *HST* image. ALMA and JVLA images are consistent with each other and reveal the DSFG to follow a fold-caustic lensing configuration, with two isolated images and an additional merging image pair towards the southeast (labeled $1abc$). The images form a partial Einstein ring with a radius of $\approx 0.9^{\prime\prime}$.

The foreground is modeled with a single SIE profile.

The optimized model has a high ellipticity, $e = 0.65^{+0.18}_{-0.25}$, possibly because of the small number of available constraints currently available, which necessitates a perhaps too-simplistic model.

**PJ144958.** This cluster lens has a CO(3-2) line detection at $z=2.153$ (cite: Harrington:2021aa; Berman:2022aa) with a preliminary foreground cluster redshift measured at $z_{\rm phot} =0.4$. Optical emission probed by *HST* and Gemini appears to be more extended than at 1 mm and 6 GHz, which reveal a set of more point-source-like images. However, there appears at first to be four distinct images all on one side of a foreground galaxy group, with no obvious counter-image.

We consider it likely that the middle pair of images ($1bc$) is in fact a merging pair on either side of the critical curve (see Fig. [2](#fig:model_SP)). The northernmost image $1d$ also appears to be split into four images by another intervening cluster member ($4abc$), visible only with *HST*’s higher resolution and unresolved by ALMA and JVLA.

As constraints on our model, we include images $1abcd$ (JVLA/ALMA locations), $2abc$ for the peaks of the HST images, and $3abc$ as the fainter tail visible only in optical (adjacent to $2abc$).

Lastly, we include images $4abc$ for the point-like sources surrounding the perturbing foreground.

The lensing distribution is parameterized by a cluster-scale NFW

profile, 3 smaller SIS profiles describing the group of elliptical galaxies interior to the arc, and a fourth SIS profile for the perturbing galaxy at the northern end of the arc.

**PJ160722.** This member of our sample has a CO(2-1) line observed by RSR at $z=1.482$, confirmed with photometric information and subsequent spectroscopic follow-up (cite: Harrington:2016aa; Harrington:2021aa). *HST* imaging reveals two apparent foreground lensing objects with a photometric redshift of $z=0.65$, determined from the optical to mid-IR SED in (cite: Harrington:2016aa). A bright radio AGN is detected in the northern foreground (Fig. [2](#fig:model_SP)). Both near-IR and radio reveal extended ring-like arcs tightly surrounding the foreground.

Four peaks embedded with the surrounding ring are apparent in the radio and, to a lesser extent, in the optical image, which we interpret as a quadruply-imaged region of the source plane.

The lensing mass distribution is represented by a single SIE model, given the proximity of the two foregrounds (and therefore strong degeneracies in optimal parameters between the two).

**PJ231356.** This object has a CO(3-2) line observed by RSR at $z=2.215$, confirmed by spectroscopic follow-up (cite: Harrington:2021aa; Berman:2022aa). *HST*/WFC3 1.6$\mu$m imaging appears to show a primary lensing galaxy, with a secondary galaxy to the north that appears to have a substantial impact on the lensing morphology, leading to a surprisingly straight arc towards the north.

Numerous background arcs are visible in *HST*, some of which coincide with the arcs in ALMA 260 GHz continuum.

Most of these multiple images have not been identified definitively, but the quadruple-image family $1abcd$ is a sufficient constraint for the model at present.

The lensing mass distribution is parameterized by the primary elliptical (SIE) and the secondary perturber to the north (SIS).

While the $x$-position of the primary galaxy is left as a free parameter, we hold fixed its $y$-position to avoid degeneracy with the secondary lens.

# Lensed multiple image systems used as constraints

In §[3.1](#sec:family_id), we discuss our approach to identifying multiply-imaged features of the background DSFGs using *HST*, Gemini, JVLA, and ALMA observations. In Table [13](#tab:lensconstraints), we summarize these features that were used as constraints for our models, which are also marked on Fig. [1](#fig:postage_stamps).

|                        |          |           |            |           |
|:----------------------:|:--------:|:---------:|:----------:|:---------:|
|       **Field**        | Image \# |    RA     |    Dec.    |    $z$    |
|                        |          | \[deg.\]  |  \[deg.\]  |           |
|                        |          |           |            |           |
|      **PJ011646**      |    1a    | 19.195512 | -24.617222 |  $2.125$  |
|                        |    1b    | 19.194428 | -24.617920 |           |
|                        |    2a    | 19.195611 | -24.617580 | $2.125^a$ |
|                        |    2b    | 19.195158 | -24.616568 |           |
|                        |    2c    | 19.194320 | -24.617293 |           |
|                        |    2d    | 19.194704 | -24.617876 |           |
|                        |          |           |            |           |
|      **PJ014341**      |    1a    | 25.921762 | -1.790685  |  $1.096$  |
|                        |    1b    | 25.921923 | -1.7905189 |           |
|                        |    1c    | 25.921752 | -1.7904362 |           |
|                        |    1d    | 25.921651 | -1.7905364 |           |
|                        |          |           |            |           |
|      **PJ020941**      |    1a    | 32.422486 | 0.26643019 |   2.554   |
|                        |    1b    | 32.421489 | 0.26561695 |           |
|                        |    2a    | 32.422507 | 0.26633282 |           |
|                        |    2b    | 32.421262 | 0.26661786 |           |
|                        |    3a    | 32.422500 | 0.26639240 |           |
|                        |    3b    | 32.421370 | 0.26574041 |           |
|                        |    3c    | 32.421216 | 0.26607387 |           |
|                        |    3d    | 32.421181 | 0.26628788 |           |
|                        |    4a    | 32.422470 | 0.26642723 |           |
|                        |    4b    | 32.421480 | 0.26561101 |           |
|                        |          |           |            |           |
|      **PJ022633**      |    1a    | 36.642144 | 23.758811  |  $3.120$  |
|                        |    1b    | 36.642601 | 23.757341  |           |
|                        |    1c    | 36.642373 | 23.757083  |           |
|                        |    1d    | 36.640842 |  23.75822  |           |
|                        |    1e    | 36.640552 | 23.758414  |           |
|                        |          |           |            |           |
|      **PJ030510**      |    1a    | 46.294327 | -30.608571 |  $2.263$  |
|                        |    1b    | 46.294248 | -30.608259 |           |
| (PA $=$ 114$^{\circ}$) | critic1  | 46.294451 | -30.608419 |           |
| (PA $=$ 49$^{\circ}$)  | critic2  | 46.294136 | -30.608439 |           |
|                        |          |           |            |           |
|      **PJ105353**      |    1a    | 163.47142 | 5.9387914  |   3.005   |
|                        |    1b    | 163.47121 | 5.9385352  |           |
|                        |    1c    | 163.47158 | 5.9386185  |           |
|                        |    1d    | 163.47144 | 5.9383833  |           |
|                        |    2a    | 163.47152 | 5.9386507  |           |
|                        |    2b    | 163.47128 | 5.9383962  |           |
|                        |          |           |            |           |
|      **PJ112713**      |    1a    | 171.80585 | 46.156730  |   1.303   |
|                        |    1b    | 171.80619 | 46.156579  |           |
|                        |    2a    | 171.80595 | 46.156529  |           |
|                        |    2b    | 171.80630 | 46.156730  |           |
|                        |    3a    | 171.80619 | 46.156825  |           |
|                        |    3b    | 171.80596 | 46.156528  |           |

:  Multiple image positions used as constraints in the lensing models (presented in Table [6](#tab:lensmodels)), as per §[3.1](#sec:family_id). In some rare cases, the location and orientation of caustic curves as inferred by lensing morphologies are used as constraints.

|                       |          |           |           |         |
|:---------------------:|:--------:|:---------:|:---------:|:-------:|
|       **Field**       | Image \# |    RA     |   Dec.    |   $z$   |
|                       |          | \[deg.\]  | \[deg.\]  |         |
|                       |          |           |           |         |
|     **PJ113805**      |    1a    | 174.52314 | 32.965895 |  2.019  |
|                       |    1b    |  174.523  | 32.965711 |         |
|                       |    2a    | 174.52318 | 32.965891 |         |
|                       |    2b    | 174.52302 | 32.96573  |         |
|                       |          |           |           |         |
|     **PJ113921**      |    1a    | 174.84046 | 20.414097 |  2.858  |
|                       |    1b    | 174.84068 | 20.414272 |         |
|                       |    1c    | 174.84023 | 20.414594 |         |
|                       |    1d    | 174.84063 | 20.414802 |         |
|                       |          |           |           |         |
|     **PJ132630**      |    1a    | 201.62551 | 33.735859 |  2.951  |
|                       |    1b    | 201.62637 | 33.735124 |         |
|                       |    2a    | 201.62552 | 33.735968 |         |
|                       |    2b    | 201.62625 | 33.735165 |         |
|                       |    3a    | 201.62549 | 33.735844 |         |
|                       |    3b    | 201.62636 | 33.735133 |         |
|                       |          |           |           |         |
|     **PJ133634**      |    1a    | 204.14616 | 49.220425 |  3.254  |
|                       |    1b    | 204.14534 | 49.220706 |         |
|                       |    2a    | 204.14607 | 49.220635 |         |
|                       |    2b    | 204.14515 | 49.220373 |         |
|                       |    3a    | 204.14586 | 49.220788 |         |
|                       |    3b    | 204.14545 | 49.220180 |         |
|                       |          |           |           |         |
|     **PJ144653**      |    1a    | 221.72176 | 17.876174 | $1.084$ |
|                       |    1b    | 221.72135 | 17.875992 |         |
| (PA $=$ 35$^{\circ}$) | critic1  | 221.72186 | 17.875843 |         |
|                       |          |           |           |         |
|     **PJ144958**      |    1a    | 222.49332 | 22.642215 | $2.153$ |
|                       |    1b    | 222.49347 | 22.643774 |         |
|                       |    1c    | 222.49374 | 22.644154 |         |
|                       |    1d    | 222.49416 | 22.644439 |         |
|                       |    2a    | 222.49329 | 22.642269 | $2.153$ |
|                       |    2b    | 222.49346 | 22.643802 |         |
|                       |    2c    | 222.49371 | 22.644152 |         |
|                       |    3a    | 222.49331 | 22.642477 | $2.153$ |
|                       |    3b    | 222.49333 | 22.643417 |         |
|                       |    3c    | 222.4939  | 22.644268 |         |
|                       |    4a    | 222.49389 | 22.644384 | $2.153$ |
|                       |    4b    | 222.49402 | 22.644521 |         |
|                       |    4c    | 222.49415 | 22.644548 |         |
|                       |          |           |           |         |
|     **PJ160722**      |    1a    | 241.84517 | 73.783702 |  1.484  |
|                       |    1b    | 241.84558 | 73.784165 |         |
|                       |    1c    | 241.84418 | 73.784227 |         |
|                       |    1d    | 241.84422 | 73.783829 |         |
|                       |          |           |           |         |
|     **PJ231356**      |    1a    | 348.48594 | 1.1542249 |  2.217  |
|                       |    1b    | 348.48654 | 1.1545733 |         |
|                       |    1c    | 348.48615 | 1.1550713 |         |
|                       |    1d    | 348.48519 | 1.1548946 |         |

:  (continued)

Table notes: $^a$ Assumed to be located at the same redshift as the DSFG.

# Best-fit lens model parameters

In Table [6](#tab:lensmodels), we summarize the best-fit lens models for each object. In most cases, we list “median," “best," and “mode" solutions, which represent the set of parameters consisting (respectively) of the median of the posterior distribution, the highest-likelihood solution recovered from the MCMC iterations, and the mode of the posterior distribution. The latter solution is usually employed when the posterior distribution is bimodal, especially in terms of position angle where there may be solutions offset by $90^\circ$.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Field** |  |  |  |  |  |  |
| *Model description* | RA (deg.) | Dec. (deg.) | RMS$_{\rm im} (^{\prime\prime})$ | $\sigma_{\rm position} (^{\prime\prime})$ | $\nu$ | $\chi_\nu^2$ |
| potential $1, 2,...,n$ | $\Delta \alpha$ ($^{\prime\prime}$) | $\Delta \delta$ ($^{\prime\prime}$) | $e$ | $\theta$ ($^{\circ}$) | $\sigma$ (km s$^{-1}$) | $z$ |
|  |  |  |  |  |  |  |
| **PJ011646** |  |  |  |  |  |  |
| *Median* | 19.194989 | -24.617376 |  | 0.10 | 3 | 2.0 |
| potential 1 | $-0.12^{+0.03}_{-0.04}$ | $0.29^{+0.03}_{-0.03}$ | $0.37^{+0.04}_{-0.04}$ | $15.8^{+1.2}_{-1.2}$ | $364.0^{+3.0}_{-3.0}$ | $0.555^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.05 |  | 3 | 0.5 |
| potential 1 | $-0.12$ | $0.30$ | $0.36$ | $15.7$ | $363.8$ | $0.555^*$ |
|  |  |  |  |  |  |  |
| **PJ014341** |  |  |  |  |  |  |
| *Median* | 25.921794 | -1.7905377 |  | 0.17 | 3 | 1.7 |
| potential 1 | $-0.06^{+0.08}_{-0.07}$ | $-0.03^{+0.06}_{-0.06}$ | $0.77^{+0.15}_{-0.21}$ | $3.6^{+16.1}_{-11.2}$ | $209.7^{+11.4}_{-10.8}$ | $0.594^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.04 |  | 3 | 0.6 |
| potential 1 | $-0.06$ | $-0.02$ | $0.55$ | $-1.7$ | $202.1$ | $0.594^*$ |
|  |  |  |  |  |  |  |
| **PJ020941** |  |  |  |  |  |  |
| *Median* | 32.42192 | 0.26621843 |  | 0.15 | 6 | 0.8 |
| potential 1 | $-0.28^{+0.13}_{-0.12}$ | $0.12^{+0.04}_{-0.05}$ | $0.36^{+0.08}_{-0.08}$ | $-14.3^{+1.0}_{-0.9}$ | $312.0^{+5.9}_{-8.5}$ | $0.202^*$ |
| potential 2 (SIS) | $0.22^*$ | $2.59^*$ |  |  | $82.6^{+42.2}_{-48.4}$ | $0.202^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.04 |  | 6 | 0.1 |
| potential 1 | $-0.26$ | $0.12$ | $0.33$ | $-14.6$ | $314.7$ | $0.202^*$ |
| potential 2 (SIS) | $0.22^*$ | $2.59^*$ |  |  | $67.6$ | $0.202^*$ |
|  |  |  |  |  |  |  |
| **PJ022633** |  |  |  |  |  |  |
| *Median* | 36.641654 | 23.757872 |  | 0.40 | 1 | 5.9 |
| potential 1 | $-0.08^{+0.23}_{-0.26}$ | $-0.12^*$ | $0.25^{+0.11}_{-0.09}$ | $-9.0^{+6.8}_{-63.9}$ | $376.3^{+10.9}_{-11.5}$ | $0.41^*$ |
| potential 2 (SIS) | $2.94^{+0.43}_{-0.33}$ | $2.08^{+0.32}_{-0.55}$ |  |  | $208.3^{+25.6}_{-26.3}$ | $0.41^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.10 |  | 1 | 0.3 |
| potential 1 | $-0.08$ | $-0.12^*$ | $0.10$ | $-13.6$ | $383.0$ | $0.41^*$ |
| potential 2 (SIS) | $3.17$ | $1.88$ |  |  | $170.7$ | $0.41^*$ |
|  |  |  |  |  |  |  |
| **PJ030510** |  |  |  |  |  |  |
| *Median* | 46.294291 | -30.608356 |  | 0.14 | 1 | 2.0 |
| potential 1 | $-0.04^{+0.13}_{-0.09}$ | $-0.48^{+0.19}_{-0.14}$ | $0.39^{+0.32}_{-0.28}$ | $3.5^{+56.9}_{45.1}$ | $169.6^{+13.6}_{-11.8}$ | $0.4^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | $<0.01$ |  | 3 | 0.002 |
| potential 1 | $-0.01$ | $-0.39$ | $0.07$ | $-2.1$ | $165.0$ | $0.4^*$ |
|  |  |  |  |  |  |  |
| **PJ105353** |  |  |  |  |  |  |
| *Median* | 163.4714 | 5.9385728 |  | 0.10 | 3 | 2.4 |
| potential 1 | $0.05^{+0.05}_{-0.04}$ | $0.06^{+0.03}_{-0.02}$ | $0.35^{+0.15}_{-0.11}$ | $-6.8^{+3.9}_{-3.9}$ | $283.0^{+7.2}_{-7.6}$ | $1.525^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.05 |  | 3 | 0.5 |
| potential 1 | $0.03$ | $0.03$ | $0.20$ | $-5.9$ | $281.7$ | $1.525^*$ |
|  |  |  |  |  |  |  |
| **PJ112713** |  |  |  |  |  |  |
| *Median* | 171.80606 | 46.15670 |  | 0.20 | 3 | 0.8 |
| potential 1 (SIS) | $0.00^{+0.08}_{-0.09}$ | $-0.32^{+0.08}_{-0.08}$ |  |  | $182.7^{+7.4}_{-6.8}$ | $0.415^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.08 |  | 3 | 0.3 |
| potential 1 (SIS) | $-0.03$ | $-0.28$ |  |  | $179.2$ | $0.415^*$ |
|  |  |  |  |  |  |  |
| **PJ113805** |  |  |  |  |  |  |
| *Mode* | 174.52305 | 32.965806 |  | 0.20 | 1 | 0.3 |
| potential 1 (SIS) | $0.04^{+0.14}_{-0.14}$ | $-0.15^{+0.20}_{-0.17}$ |  |  | $145.5^{+11.2}_{-9.6}$ | $0.52^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.03 |  | 2 | 0.6 |
| potential 1 (SIS) | $-0.01$ | $-0.14$ |  |  | $146.1$ | $0.52^*$ |
|  |  |  |  |  |  |  |
| **PJ113921** |  |  |  |  |  |  |
| *Mode$^a$* | 174.84041 | 20.414479 |  | 0.39 | 2 | 1.3 |
| potential 1 | $0.00^*$ | $0.01^*$ | $0.65$ | $28.6$ | $230.5$ | $0.57^*$ |
| potential 2 (SIS) | $2.56^*$ | $0.58^*$ |  |  | $179.0$ | $0.57^*$ |
|  |  |  |  |  |  |  |
| *Median* |  |  |  |  | 2 | 1.7 |
| potential 1 | $0.00^*$ | $0.01^*$ | $0.49^{+0.15}_{-0.19}$ | $31.6^{+14.0}_{-12.4}$ | $232.7^{+17.3}_{-18.8}$ | $0.57^*$ |
| potential 2 (SIS) | $2.56^*$ | $0.58^*$ |  |  | $191.5^{+58.9}_{-57.3}$ | $0.57^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.23 |  | 2 | 0.7 |
| potential 1 | $0.00^*$ | $0.01^*$ | $0.69$ | $-74.8$ | $225.5$ | $0.57^*$ |
| potential 2 (SIS) | $2.56^*$ | $0.58^*$ |  |  | $274.9$ | $0.57^*$ |
|  |  |  |  |  |  |  |
| **PJ132630** |  |  |  |  |  |  |
| *Mode$^a$* | 201.62613 | 33.735272 |  | 0.38 | 1 | 0.4 |
| potential 1 | $-0.03$ | $0.14$ | $0.02$ | $-42.6$ | $331.0$ | $0.786^*$ |
|  |  |  |  |  |  |  |
| *Median* |  |  |  |  | 1 | 1.3 |
| potential 1 | $0.01^{+0.14}_{-0.12}$ | $0.15^{+0.13}_{-0.13}$ | $0.19^{+0.18}_{-0.13}$ | $-42.5^{+25.0}_{-29.8}$ | $330.5^{+13.7}_{-12.8}$ | $0.786^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.02 |  | 1 | 0.02 |
| potential 1 | $0.21$ | $0.31$ | $0.04$ | $-1.8$ | $334.5$ | $0.786^*$ |
|  |  |  |  |  |  |  |
| **PJ133634** |  |  |  |  |  |  |
| *Mode* | 204.14596 | 49.220455 |  | 0.30 | 5 | 0.7 |
| potential 1 | $0.37$ | $0.43$ | $0.01$ | $29.1$ | $218.7$ | $0.26^*$ |
|  |  |  |  |  |  |  |
| *Median* |  |  |  |  | 5 | 0.8 |
| potential 1 | $0.37^{+0.26}_{-0.24}$ | $0.40^{+0.14}_{-0.24}$ | $0.20^{+0.28}_{-0.16}$ | $70.3^{+59.5}_{-41.5}$ | $220.2^{+10.7}_{-8.0}$ | $0.26^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.08 |  | 5 | 0.1 |
| potential 1 | $0.71$ | $-0.17$ | $0.12$ | $160.6$ | $227.3$ | $0.26^*$ |
|  |  |  |  |  |  |  |
| **PJ144653** |  |  |  |  |  |  |
| *Median* | 221.72172 | 17.875883 |  | 0.37 | 1 | 3.2 |
| potential 1 | $0.10^*$ | $0.47^*$ | $0.65^{+0.18}_{-0.25}$ | $95.0^{+14.1}_{-14.0}$ | $262.8^{+18.0}_{-14.7}$ | $0.493^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.03 |  | 1 | 0.5 |
| potential 1 | $0.10^*$ | $0.47^*$ | $0.66$ | $96.4$ | $257.8$ | $0.493^*$ |
|  |  |  |  |  |  |  |
| **PJ144958** |  |  |  |  |  |  |
| *Median* | 222.49514 | 22.642985 |  | 0.50 | 13 | 0.4 |
| potential 1 (NFW) | $-1.11^{+2.56}_{-2.87}$ | $-1.55^{+1.40}_{-1.32}$ | $0.64^{+0.12}_{-0.20}$ | $12.2^{+4.2}_{-5.1}$ | $r_s (^{\prime\prime}) = 26.1^{+4.0}_{-3.5}$ | $0.4^*$ |
| potential 2 (SIS) | $3.52^*$ | $5.13^*$ |  |  | $114.0^{+10.0}_{-11.3}$ | $0.4^*$ |
| potential 3 (SIS) | $3.22^*$ | $1.73^*$ |  |  | $224.5^{+38.9}_{-35.9}$ | $0.4^*$ |
| potential 4 (SIS) | $8.44^*$ | $7.02^*$ |  |  | $89.6^{+76.4}_{-60.2}$ | $0.4^*$ |
| potential 5 (SIS) | $-1.63^*$ | $-3.80^*$ |  |  | $157.8^{+128.8}_{-111.4}$ | $0.4^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.12 |  | 13 | 0.1 |
| potential 1 (NFW) | $-1.27$ | $-1.96$ | $0.70$ | $10.7$ | $r_s (^{\prime\prime}) = 25.2$ | $0.4^*$ |
| potential 2 (SIS) | $3.52^*$ | $5.13^*$ |  |  | $107.2$ | $0.4^*$ |
| potential 3 (SIS) | $3.22^*$ | $1.73^*$ |  |  | $242.9$ | $0.4^*$ |
| potential 4 (SIS) | $8.44^*$ | $7.02^*$ |  |  | $193.4$ | $0.4^*$ |
| potential 5 (SIS) | $-1.63^*$ | $-3.80^*$ |  |  | $76.4$ | $0.4^*$ |
|  |  |  |  |  |  |  |
| **PJ160722** |  |  |  |  |  |  |
| *Best* | 241.84491 | 73.784031 | 0.13 | 0.20 | 1 | 1.6 |
| potential 1 | $-0.04$ | $-0.10$ | $0.36$ | $-34.0$ | $273.6$ | $0.65^*$ |
|  |  |  |  |  |  |  |
| *Median* |  |  |  |  | 1 | 5.2 |
| potential 1 | $-0.03^{+0.15}_{-0.14}$ | $-0.09^{+0.09}_{-0.07}$ | $0.61^{+0.13}_{-0.20}$ | $-32.1^{+82.6}_{-6.6}$ | $278.1^{+12.0}_{-11.6}$ | $0.65^*$ |
|  |  |  |  |  |  |  |
| **PJ231356** |  |  |  |  |  |  |
| *Median* | 348.485940 | 1.154663 |  | 0.10 | 1 | 4.0 |
| potential 1 | $-0.10^{+0.07}_{-0.07}$ | $0.04^*$ | $0.57^{+0.15}_{-0.09}$ | $117.8^{+12.0}_{-4.0}$ | $306.7^{+10.4}_{-12.9}$ | $0.56^*$ |
| potential 2 (SIS) | $0.25^*$ | $5.26^*$ |  |  | $297.8^{+38.5}_{-43.5}$ | $0.56^*$ |
|  |  |  |  |  |  |  |
| *Best* |  |  | 0.03 |  | 1 | 0.4 |
| potential 1 | $-0.11$ | $0.04^*$ | $0.62$ | $115.6$ | $308.7$ | $0.56^*$ |
| potential 2 (SIS) | $0.25^*$ | $5.26^*$ |  |  | $290.4$ | $0.56^*$ |

:  Optimized gravitational lens model parameters. Unless otherwise noted, all potentials are parameterized with singular isothermal ellipsoid (or spheroid) models. For NFW potentials, scale radius in arcsec ($r_s$) replaces velocity dispersion as a parameter. While the median of the posterior distribution for each parameter is typically the preferable statistical estimator, multi-modal distributions and highly non-Gaussian distributions may be better summarized by the mode of the posterior or the highest-likelihood (“best") sample. The first solution set listed (median, best, or mode) is taken to be the preferred model, but others are listed for completeness.

Table notes:

Fixed parameters are denoted with an asterisk. Asymmetric error bars indicate $1\sigma$ confidence levels and are determined from the resulting MCMC posterior distribution. Ellipticity is defined as $e= (a^2 - b^2) / (a^2 + b^2)$, for semi-major and semi-minor axes $a$ and $b$. The position angle $\theta$ is measured counterclockwise from east. Velocity dispersion $\sigma$ for singular isothermal ellipsoids are functionally equivalent to physical velocity dispersions. The Right ascension (RA) and Declination (Dec.) given are reference positions (to which $\Delta\alpha$ and $\Delta\delta$ are relative), and are typically chosen as the centroid of the brightest foreground. The positional uncertainty $\sigma_{\rm position}$ is supplied for each object, and is equal to the size of the synthesized beam for ALMA or JVLA (whichever is lowest resolution). RMS$_{\rm im}$ is the RMS deviation between observed and modeled multiple image positions for each field, calculated in the image plane for the lowest-$\chi^2$ solution.

The reduced $\chi_\nu^2$ is reported for the given number of degrees of freedom $\nu$.

$^a$ In some cases, the mode solution of the optimization is used instead of the median, which is less useful when the posterior distribution is bimodal or if one parameter’s optimization is sensitive to the choice of parameter bounds (e.g., when ellipticity is poorly constrained by the multiple images, the posterior tends to follow more of a uniform distribution, so the median tends towards the midpoint of the parameter bounds). For these solutions, the uncertainty in the median is taken to be representative of the uncertainty in the mode.

# Comparison with existing lens models

Several of the objects included in this work have already been the subject of gravitational lens modeling, but we independently derive models here to both incorporate information from new observations and to ensure consistency between models for this subsample.

In particular, we examine discrepancies in derived magnifications as a benchmark.

First, PJ020941 (or *9io9*) is perhaps the most well-studied DSFG included, with independent modeling efforts by (cite: Geach:2015aa; Geach:2018aa; Rivera:2019aa), and (cite: Liu:2022ad).

The initial model by (cite: Geach:2015aa) was based on 4 different radio observations and near-IR ground-based imaging (seeing $\approx 0.8^{\prime\prime}$), and was parameterized by an isothermal ellipsoid and a satellite isothermal spheroid for the secondary foreground, with added external shear. With the *gravlens* software (cite: Keeton:2011aa), they modeled the near-IR as a single Sérsic profile and the radio as two Gaussian components, finding a magnification of $\mu \approx 10$, in agreement with what we find, $\mu_{\rm 1mm} =10.5 \pm 3.7$ and $\mu_{\rm 6 GHz} = 12.0 \pm 3.5$ (Table [2](#tab:lensproperties)).

Revising this model using CO(4-3) ALMA spectro-imaging and a semi-linear inversion approach (cite: Warren:2003aa; Dye:2018aa), (cite: Geach:2018aa) found a slightly higher magnification of $\mu_{\rm CO4-3} = 14.7 \pm 0.3$.

(cite: Rivera:2019aa) incorporated CO(3-2) imaging with NOEMA, with 32 independent velocity channels as constraints, finding a smooth velocity gradient consistent with the structure found by (cite: Geach:2018aa). Also using a 2-component lens model with external shear, they found that the magnification varied strongly with velocity, ranging from $\mu \approx 7 - 22$, but with a luminosity-weighted mean of $\langle \mu \rangle \approx 13$.

Most recently, (cite: Liu:2022ad) used newly-collected adaptive optics $H$ and $K_s$-band imaging, alongside *HST*/WFC3 F125W, SMA 870 $\mu$m, and multi-J CO observations with ALMA in order to build their own lens model.

As with our work, (cite: Liu:2022ad) used LENSTOOL to fit the primary and secondary foreground with an SIE and SIS profile, constrained by the F125W image.

This approach is the one most similar to our own, so an equivalent comparison is possible. The authors found optimized parameters that agreed with all in our model (Table [6](#tab:lensmodels)) within uncertainties, except for only a small disagreement for position angle (PA $= -8 \pm 2$$^{\circ}$ vs. our $-14 \pm 1$$^{\circ}$), and their source-plane reconstruction is visually very similar to ours (Fig. [2](#fig:model_SP)).

As a result, (cite: Liu:2022ad) found a dust continuum magnification of $\mu_{\rm dust} = 12.8 \pm 0.3$ and a stellar component magnification of $\mu_{\rm star} = 13.6 \pm 0.4$, consistent with our value of $\mu_{\rm dust} \approx 10.5$, especially given the different interferometric configurations of ALMA vs. SMA.

PJ105353 (or G244.8+54.9, the “Ruby") was previously discussed and modeled by (cite: Canameras:2017aa; Canameras:2017ab; Frye:2019aa).

(cite: Canameras:2017aa) used LENSTOOL to model the $z=1.525$ foreground with a pseudo-isothermal elliptical mass density (PIEMD) profile (with the poorly-constrained core and cut radii held fixed at 0.15 kpc and 100 kpc), based on image locations and parities from CO(4-3) observations (angular resolution 0.1$^{\prime\prime}$).

However, the authors acknowledged that these image identifications were not completely unambiguous, but settled ultimately on a pair of source-plane objects imaged 2 and 4 times, respectively.

An additional 0.07$^{\prime\prime}$-resolution Band 6 (1 mm) observation with ALMA (Program 2015.1.01518.S, PI: N. Nesvadba) was not included as a constraint, but our interpretation of the image configuration differs slightly. Whereas (cite: Canameras:2017aa) identify a cusp-like configuration, the 1 mm image appears to instead show more of an Einstein cross, with 4 well-separated images (nearly aligned north, south, east, and west). However, the second, doubly-imaged system is in accord with (cite: Canameras:2017aa).

Unfortunately, the non-detection of the background object with *HST* (as it is blended with the foreground; (cite: Frye:2019aa)) makes confirmation of this morphology difficult.

(cite: Canameras:2017aa) find a dust magnification of $\mu_{\rm 3mm} = 21.8 \pm 0.6$ (reported in (cite: Canameras:2018ab)), with magnifications for individual clumps ranging from $\mu \approx 7 - 38$.

In our case, we find a significantly different total value of $\mu_{870 \mu {\rm m}} = 7.6 \pm 0.7$ (or $\mu_{\rm 1 mm} \approx 12$).

Given the difficulty in deriving robust constraints on the model, a discrepancy is not particularly unexpected, especially as both interpretations agree that the source-plane galaxy lies near to a caustic, where the magnification gradient is steep and highly sensitive to the model. On the other hand, values like the Einstein radius are not as sensitive, and our value is in close agreement with that of (cite: Canameras:2017aa).

While a lens model for PJ113921 (G231.3+72.2) has not yet been published, (cite: Canameras:2018ab) provide magnifications of $\mu_{\rm dust} = 7.9 \pm 0.3$ and $\mu_{\rm gas} = 6.0 \pm 0.5$, based on SMA 880 $\mu$m continuum and multi-J CO imaging with the IRAM Plateau de Bure Interferometer (PdBI), which are broadly consistent with our measurements of $\mu \approx 5 - 9$ from ALMA and JVLA.

Lastly, PJ132630 was modeled by (cite: Bussmann:2013aa) based on HST F110W near-IR and SMA 880 $\mu$m imaging observations, using an interferometric visibility-based approach. They found an Einstein radius of $\theta_E = 1.80 \pm 0.02$ (consistent with our $\theta_{\rm Ein} = 1.78 \pm 0.18$; Table [2](#tab:lensproperties)), a lens ellipticity of $\epsilon = 0.26 \pm 0.04$ (similar to our median solution, $e = 0.19 \pm 0.16$; Table [6](#tab:lensmodels)), and a dust continuum magnification of $\mu_{880\mu{\rm m}} = 4.1 \pm 0.3$ (in close agreement with our $\mu_{\rm 1mm} = 4.3 \pm 0.6$).

While magnifications are generally robust between various lens modeling approaches, the non-trivial differences between this work and others should not be discounted.

(cite: Spilker:2016aa) computes magnification as flux-weighted average over the elliptical model components describing the source plane, whereas (cite: Bussmann:2013aa; Bussmann:2015aa) use the ratio of image-plane to reconstructed source-plane flux.

On the other hand, (cite: Dye:2018aa) explore the sensitivity of magnification to imaging resolution and depth by calculating magnification as a function of fraction of source-plane flux (i.e. surface brightness threshold).

The authors found that, while variation can be small, in the vicinity of a caustic in particular, magnification can vary by up to 25% as a function of interferometric configuration.

Our work does not make explicit assumptions of source-plane structure, but also does not take advantage of the entirety of information present in the interferometric images like the visibility-modeling approach of these other works.

Future work to apply a visibility-based modeling approach to these objects will allow for a more direct comparison.

An additional promising method that we hope to explore in the future involves Regularized Semi-linear Inversion (cite: Warren:2003aa; Nightingale:2015aa; Enia:2018aa), by which the source plane is tessellated but not assumed to follow a specific parametric form.

In summary, the general agreement for most objects with prior models (derived from independent constraints) helps to lend credence to their robustness. We interpret any tensions in resultsin particular, for PJ105353to be more influenced by different observing setups than by different lens modeling approaches.

natexlab

(ref: Acebron:2017aa) Acebron, A., Jullo, E., Limousin, M., et al. 2017, MNRAS, 470, 1809, doi: [`10.1093/mnras/stx1330`](http://doi.org/10.1093/mnras/stx1330)

(ref: Acebron:2018aa) Acebron, A., Cibirka, N., Zitrin, A., et al. 2018, ApJ, 858, 42, doi: [`10.3847/1538-4357/aabe29`](http://doi.org/10.3847/1538-4357/aabe29)

(ref: Alaghband-Zadeh:2012aa) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2012, MNRAS, 424, 2232, doi: [`10.1111/j.1365-2966.2012.21386.x`](http://doi.org/10.1111/j.1365-2966.2012.21386.x)

(ref: Amvrosiadis:2018aa) Amvrosiadis, A., Eales, S. A., Negrello, M., et al. 2018, MNRAS, doi: [`10.1093/mnras/sty138`](http://doi.org/10.1093/mnras/sty138)

(ref: Andrews:2011ab) Andrews, B. H., & Thompson, T. A. 2011, ApJ, 727, 97, doi: [`10.1088/0004-637X/727/2/97`](http://doi.org/10.1088/0004-637X/727/2/97)

(ref: Astropy-Collaboration:2013aa) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy-Collaboration:2018aa) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Barcos-Munoz:2015aa) Barcos-Muñoz, L., Leroy, A. K., Evans, A. S., et al. 2015, ApJ, 799, 10, doi: [`10.1088/0004-637X/799/1/10`](http://doi.org/10.1088/0004-637X/799/1/10)

(ref: Barcos-Munoz:2017aa) —. 2017, ApJ, 843, 117, doi: [`10.3847/1538-4357/aa789a`](http://doi.org/10.3847/1538-4357/aa789a)

(ref: Barger:1998aa) Barger, A. J., Cowie, L. L., Sanders, D. B., et al. 1998, Nature, 394, 248, doi: [`10.1038/28338`](http://doi.org/10.1038/28338)

(ref: Barnabe:2009aa) Barnabè, M., Czoske, O., Koopmans, L. V. E., et al. 2009, MNRAS, 399, 21, doi: [`10.1111/j.1365-2966.2009.14941.x`](http://doi.org/10.1111/j.1365-2966.2009.14941.x)

(ref: Barro:2013aa) Barro, G., Faber, S. M., Pérez-González, P. G., et al. 2013, ApJ, 765, 104, doi: [`10.1088/0004-637X/765/2/104`](http://doi.org/10.1088/0004-637X/765/2/104)

(ref: Barro:2016aa) Barro, G., Kriek, M., Pérez-González, P. G., et al. 2016a, ApJL, 827, L32, doi: [`10.3847/2041-8205/827/2/L32`](http://doi.org/10.3847/2041-8205/827/2/L32)

(ref: Barro:2016ab) Barro, G., Faber, S. M., Dekel, A., et al. 2016b, ApJ, 820, 120, doi: [`10.3847/0004-637X/820/2/120`](http://doi.org/10.3847/0004-637X/820/2/120)

(ref: Barrufet:2020aa) Barrufet, L., Pearson, C., Serjeant, S., et al. 2020, A&A, 641, A129, doi: [`10.1051/0004-6361/202037838`](http://doi.org/10.1051/0004-6361/202037838)

(ref: Barrufet:2022aa) Barrufet, L., Oesch, P. A., Weibel, A., et al. 2022, arXiv e-prints, arXiv:2207.14733. [`https://arxiv.org/abs/2207.14733`](https://arxiv.org/abs/2207.14733)

(ref: Bartelmann:2001aa) Bartelmann, M., & Schneider, P. 2001, Phys. Rep., 340, 291, doi: [`10.1016/S0370-1573(00)00082-X`](http://doi.org/10.1016/S0370-1573(00)00082-X)

(ref: Becker:1995aa) Becker, R. H., White, R. L., & Helfand, D. J. 1995, ApJ, 450, 559, doi: [`10.1086/176166`](http://doi.org/10.1086/176166)

(ref: Behroozi:2013aa) Behroozi, P. S., Wechsler, R. H., & Conroy, C. 2013, ApJ, 770, 57, doi: [`10.1088/0004-637X/770/1/57`](http://doi.org/10.1088/0004-637X/770/1/57)

(ref: Bell:2003aa) Bell, E. F. 2003, ApJ, 586, 794, doi: [`10.1086/367829`](http://doi.org/10.1086/367829)

(ref: Berman:2022aa) Berman, D. A., Yun, M. S., Harrington, K. C., et al. 2022, MNRAS, 515, 3911, doi: [`10.1093/mnras/stac1494`](http://doi.org/10.1093/mnras/stac1494)

(ref: Bicay:1990aa) Bicay, M. D., & Helou, G. 1990, ApJ, 362, 59, doi: [`10.1086/169243`](http://doi.org/10.1086/169243)

(ref: Biggs:2008aa) Biggs, A. D., & Ivison, R. J. 2008, MNRAS, 385, 893, doi: [`10.1111/j.1365-2966.2008.12869.x`](http://doi.org/10.1111/j.1365-2966.2008.12869.x)

(ref: Blain:1996aa) Blain, A. W. 1996, MNRAS, 283, 1340, doi: [`10.1093/mnras/283.4.1340`](http://doi.org/10.1093/mnras/283.4.1340)

(ref: Blain:1993aa) Blain, A. W., & Longair, M. S. 1993, MNRAS, 264, 509, doi: [`10.1093/mnras/264.2.509`](http://doi.org/10.1093/mnras/264.2.509)

(ref: Blain:2002aa) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J.-P., & Frayer, D. T. 2002, Phys. Rep., 369, 111, doi: [`10.1016/S0370-1573(02)00134-5`](http://doi.org/10.1016/S0370-1573(02)00134-5)

(ref: Blandford:1992aa) Blandford, R. D., & Narayan, R. 1992, ARA&A, 30, 311, doi: [`10.1146/annurev.aa.30.090192.001523`](http://doi.org/10.1146/annurev.aa.30.090192.001523)

(ref: Bolton:2008ab) Bolton, A. S., Treu, T., Koopmans, L. V. E., et al. 2008, ApJ, 684, 248, doi: [`10.1086/589989`](http://doi.org/10.1086/589989)

(ref: Bondi:2018aa) Bondi, M., Zamorani, G., Ciliegi, P., et al. 2018, A&A, 618, L8, doi: [`10.1051/0004-6361/201834243`](http://doi.org/10.1051/0004-6361/201834243)

(ref: Borys:2006aa) Borys, C., Blain, A. W., Dey, A., et al. 2006, ApJ, 636, 134, doi: [`10.1086/497983`](http://doi.org/10.1086/497983)

(ref: Brinchmann:2004aa) Brinchmann, J., Charlot, S., White, S. D. M., et al. 2004, MNRAS, 351, 1151, doi: [`10.1111/j.1365-2966.2004.07881.x`](http://doi.org/10.1111/j.1365-2966.2004.07881.x)

(ref: Broadhurst:2005aa) Broadhurst, T., Takada, M., Umetsu, K., et al. 2005, ApJL, 619, L143, doi: [`10.1086/428122`](http://doi.org/10.1086/428122)

(ref: Brodwin:2008aa) Brodwin, M., Dey, A., Brown, M. J. I., et al. 2008, ApJL, 687, L65, doi: [`10.1086/593327`](http://doi.org/10.1086/593327)

(ref: Burnham:2021aa) Burnham, A. D., Casey, C. M., Zavala, J. A., et al. 2021, ApJ, 910, 89, doi: [`10.3847/1538-4357/abe401`](http://doi.org/10.3847/1538-4357/abe401)

(ref: Bussmann:2012aa) Bussmann, R. S., Gurwell, M. A., Fu, H., et al. 2012, ApJ, 756, 134, doi: [`10.1088/0004-637X/756/2/134`](http://doi.org/10.1088/0004-637X/756/2/134)

(ref: Bussmann:2013aa) Bussmann, R. S., Pérez-Fournon, I., Amber, S., et al. 2013, ApJ, 779, 25, doi: [`10.1088/0004-637X/779/1/25`](http://doi.org/10.1088/0004-637X/779/1/25)

(ref: Bussmann:2015aa) Bussmann, R. S., Riechers, D., Fialkov, A., et al. 2015, ApJ, 812, 43, doi: [`10.1088/0004-637X/812/1/43`](http://doi.org/10.1088/0004-637X/812/1/43)

(ref: Canameras:2015aa) Cañameras, R., Nesvadba, N. P. H., Guery, D., et al. 2015, A&A, 581, A105, doi: [`10.1051/0004-6361/201425128`](http://doi.org/10.1051/0004-6361/201425128)

(ref: Canameras:2017aa) Cañameras, R., Nesvadba, N. P. H., Kneissl, R., et al. 2017a, A&A, 600, L3, doi: [`10.1051/0004-6361/201630359`](http://doi.org/10.1051/0004-6361/201630359)

(ref: Canameras:2017ab) Cañameras, R., Nesvadba, N., Kneissl, R., et al. 2017b, A&A, 604, A117, doi: [`10.1051/0004-6361/201630186`](http://doi.org/10.1051/0004-6361/201630186)

(ref: Canameras:2018ab) Cañameras, R., Yang, C., Nesvadba, N. P. H., et al. 2018a, A&A, 620, A61, doi: [`10.1051/0004-6361/201833625`](http://doi.org/10.1051/0004-6361/201833625)

(ref: Canameras:2018aa) Cañameras, R., Nesvadba, N. P. H., Limousin, M., et al. 2018b, A&A, 620, A60, doi: [`10.1051/0004-6361/201833679`](http://doi.org/10.1051/0004-6361/201833679)

(ref: Canameras:2021aa) Cañameras, R., Nesvadba, N. P. H., Kneissl, R., et al. 2021, A&A, 645, A45, doi: [`10.1051/0004-6361/202038979`](http://doi.org/10.1051/0004-6361/202038979)

(ref: Calanog:2014aa) Calanog, J. A., Fu, H., Cooray, A., et al. 2014, ApJ, 797, 138, doi: [`10.1088/0004-637X/797/2/138`](http://doi.org/10.1088/0004-637X/797/2/138)

(ref: Calistro-Rivera:2018aa) Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56, doi: [`10.3847/1538-4357/aacffa`](http://doi.org/10.3847/1538-4357/aacffa)

(ref: Caminha:2016aa) Caminha, G. B., Grillo, C., Rosati, P., et al. 2016, A&A, 587, A80, doi: [`10.1051/0004-6361/201527670`](http://doi.org/10.1051/0004-6361/201527670)

(ref: Casey:2018ab) Casey, C. M., Hodge, J., Zavala, J. A., et al. 2018, ApJ, 862, 78, doi: [`10.3847/1538-4357/aacd11`](http://doi.org/10.3847/1538-4357/aacd11)

(ref: Casey:2014aa) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: Chen:2015aa) Chen, C.-C., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 194, doi: [`10.1088/0004-637X/799/2/194`](http://doi.org/10.1088/0004-637X/799/2/194)

(ref: Cibirka:2018aa) Cibirka, N., Acebron, A., Zitrin, A., et al. 2018, ApJ, 863, 145, doi: [`10.3847/1538-4357/aad2d3`](http://doi.org/10.3847/1538-4357/aad2d3)

(ref: Clemens:2008aa) Clemens, M. S., Vega, O., Bressan, A., et al. 2008, A&A, 477, 95, doi: [`10.1051/0004-6361:20077224`](http://doi.org/10.1051/0004-6361:20077224)

(ref: Cochrane:2019aa) Cochrane, R. K., Hayward, C. C., Anglés-Alcázar, D., et al. 2019, MNRAS, 488, 1779, doi: [`10.1093/mnras/stz1736`](http://doi.org/10.1093/mnras/stz1736)

(ref: Condon:1992aa) Condon, J. J. 1992, ARA&A, 30, 575, doi: [`10.1146/annurev.aa.30.090192.003043`](http://doi.org/10.1146/annurev.aa.30.090192.003043)

(ref: Condon:2002aa) Condon, J. J., Cotton, W. D., & Broderick, J. J. 2002, AJ, 124, 675, doi: [`10.1086/341650`](http://doi.org/10.1086/341650)

(ref: Condon:1991aa) Condon, J. J., Huang, Z. P., Yin, Q. F., & Thuan, T. X. 1991, ApJ, 378, 65, doi: [`10.1086/170407`](http://doi.org/10.1086/170407)

(ref: Conley:2011aa) Conley, A., Cooray, A., Vieira, J. D., et al. 2011, ApJL, 732, L35, doi: [`10.1088/2041-8205/732/2/L35`](http://doi.org/10.1088/2041-8205/732/2/L35)

(ref: Cutri:1994aa) Cutri, R. M., Huchra, J. P., Low, F. J., Brown, R. L., & Vanden Bout, P. A. 1994, ApJL, 424, L65, doi: [`10.1086/187276`](http://doi.org/10.1086/187276)

(ref: Daddi:2007aa) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156, doi: [`10.1086/521818`](http://doi.org/10.1086/521818)

(ref: Daddi:2009aa) Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, ApJ, 694, 1517, doi: [`10.1088/0004-637X/694/2/1517`](http://doi.org/10.1088/0004-637X/694/2/1517)

(ref: Dahlem:2006aa) Dahlem, M., Lisenfeld, U., & Rossa, J. 2006, A&A, 457, 121, doi: [`10.1051/0004-6361:20054787`](http://doi.org/10.1051/0004-6361:20054787)

(ref: Danielson:2011aa) Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2011, MNRAS, 410, 1687, doi: [`10.1111/j.1365-2966.2010.17549.x`](http://doi.org/10.1111/j.1365-2966.2010.17549.x)

(ref: Dannerbauer:2019aa) Dannerbauer, H., Harrington, K., Dı́az-Sánchez, A., et al. 2019, AJ, 158, 34, doi: [`10.3847/1538-3881/aaf50b`](http://doi.org/10.3847/1538-3881/aaf50b)

(ref: de-Freitas:2018aa) de Freitas, V. P., Makler, M., & Dúmet-Montoya, H. S. 2018, MNRAS, 481, 2189, doi: [`10.1093/mnras/sty2412`](http://doi.org/10.1093/mnras/sty2412)

(ref: Dekel:2009aa) Dekel, A., Sari, R., & Ceverino, D. 2009a, ApJ, 703, 785, doi: [`10.1088/0004-637X/703/1/785`](http://doi.org/10.1088/0004-637X/703/1/785)

(ref: Dekel:2009ab) Dekel, A., Birnboim, Y., Engel, G., et al. 2009b, Nature, 457, 451, doi: [`10.1038/nature07648`](http://doi.org/10.1038/nature07648)

(ref: Delhaize:2017aa) Delhaize, J., Smolčić, V., Delvecchio, I., et al. 2017, A&A, 602, A4, doi: [`10.1051/0004-6361/201629430`](http://doi.org/10.1051/0004-6361/201629430)

(ref: Despali:2017ac) Despali, G., Giocoli, C., Bonamigo, M., Limousin, M., & Tormen, G. 2017, MNRAS, 466, 181, doi: [`10.1093/mnras/stw3129`](http://doi.org/10.1093/mnras/stw3129)

(ref: Dessauges-Zavadsky:2019aa) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2019, Nature Astronomy, 3, 1115, doi: [`10.1038/s41550-019-0874-0`](http://doi.org/10.1038/s41550-019-0874-0)

(ref: Deustua:2016aa) Deustua, S. 2016, “WFC3 Data Handbook”, version 3.0, (Baltimore: STScI)

(ref: Diaz-Sanchez:2017aa) Dı́az-Sánchez, A., Iglesias-Groth, S., Rebolo, R., & Dannerbauer, H. 2017, ApJL, 843, L22, doi: [`10.3847/2041-8213/aa79ef`](http://doi.org/10.3847/2041-8213/aa79ef)

(ref: Doherty:2020aa) Doherty, M. J., Geach, J. E., Ivison, R. J., & Dye, S. 2020, ApJ, 905, 152, doi: [`10.3847/1538-4357/abc5b9`](http://doi.org/10.3847/1538-4357/abc5b9)

(ref: Downes:1998aa) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615, doi: [`10.1086/306339`](http://doi.org/10.1086/306339)

(ref: Dudzeviciute:2020aa) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: Dumas:2011aa) Dumas, G., Schinnerer, E., Tabatabaei, F. S., et al. 2011, AJ, 141, 41, doi: [`10.1088/0004-6256/141/2/41`](http://doi.org/10.1088/0004-6256/141/2/41)

(ref: Dye:2014aa) Dye, S., Negrello, M., Hopwood, R., et al. 2014, MNRAS, 440, 2013, doi: [`10.1093/mnras/stu305`](http://doi.org/10.1093/mnras/stu305)

(ref: Dye:2015aa) Dye, S., Furlanetto, C., Swinbank, A. M., et al. 2015, MNRAS, 452, 2258, doi: [`10.1093/mnras/stv1442`](http://doi.org/10.1093/mnras/stv1442)

(ref: Dye:2018aa) Dye, S., Furlanetto, C., Dunne, L., et al. 2018, MNRAS, 476, 4383, doi: [`10.1093/mnras/sty513`](http://doi.org/10.1093/mnras/sty513)

(ref: Eales:2015ab) Eales, S. A. 2015, MNRAS, 446, 3224, doi: [`10.1093/mnras/stu2214`](http://doi.org/10.1093/mnras/stu2214)

(ref: Elbaz:2007aa) Elbaz, D., Daddi, E., Le Borgne, D., et al. 2007, A&A, 468, 33, doi: [`10.1051/0004-6361:20077525`](http://doi.org/10.1051/0004-6361:20077525)

(ref: Eliasdottir:2007aa) Elı́asdóttir, Á., Limousin, M., Richard, J., et al. 2007, arXiv e-prints, arXiv:0710.5636. [`https://arxiv.org/abs/0710.5636`](https://arxiv.org/abs/0710.5636)

(ref: Elmegreen:1983aa) Elmegreen, B. G. 1983, MNRAS, 203, 1011, doi: [`10.1093/mnras/203.4.1011`](http://doi.org/10.1093/mnras/203.4.1011)

(ref: Elmegreen:1999aa) —. 1999, ApJ, 517, 103, doi: [`10.1086/307200`](http://doi.org/10.1086/307200)

(ref: Elmegreen:1977aa) Elmegreen, B. G., & Lada, C. J. 1977, ApJ, 214, 725, doi: [`10.1086/155302`](http://doi.org/10.1086/155302)

(ref: Enia:2018aa) Enia, A., Negrello, M., Gurwell, M., et al. 2018, MNRAS, doi: [`10.1093/mnras/sty021`](http://doi.org/10.1093/mnras/sty021)

(ref: Fanaroff:1974aa) Fanaroff, B. L., & Riley, J. M. 1974, MNRAS, 167, 31P, doi: [`10.1093/mnras/167.1.31P`](http://doi.org/10.1093/mnras/167.1.31P)

(ref: Forster-Schreiber:2011aa) Förster Schreiber, N. M., Shapley, A. E., Genzel, R., et al. 2011, ApJ, 739, 45, doi: [`10.1088/0004-637X/739/1/45`](http://doi.org/10.1088/0004-637X/739/1/45)

(ref: Forster-Schreiber:2018aa) Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, ApJS, 238, 21, doi: [`10.3847/1538-4365/aadd49`](http://doi.org/10.3847/1538-4365/aadd49)

(ref: Franco:2018aa) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152, doi: [`10.1051/0004-6361/201832928`](http://doi.org/10.1051/0004-6361/201832928)

(ref: Frye:2019aa) Frye, B. L., Pascale, M., Qin, Y., et al. 2019, ApJ, 871, 51, doi: [`10.3847/1538-4357/aaeff7`](http://doi.org/10.3847/1538-4357/aaeff7)

(ref: Fu:2012aa) Fu, H., Jullo, E., Cooray, A., et al. 2012, ApJ, 753, 134, doi: [`10.1088/0004-637X/753/2/134`](http://doi.org/10.1088/0004-637X/753/2/134)

(ref: Fujimoto:2017aa) Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83, doi: [`10.3847/1538-4357/aa93e6`](http://doi.org/10.3847/1538-4357/aa93e6)

(ref: Fujimoto:2018aa) Fujimoto, S., Ouchi, M., Kohno, K., et al. 2018, ApJ, 861, 7, doi: [`10.3847/1538-4357/aac6c4`](http://doi.org/10.3847/1538-4357/aac6c4)

(ref: Gaia-Collaboration:2016aa) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2016, A&A, 595, A2, doi: [`10.1051/0004-6361/201629512`](http://doi.org/10.1051/0004-6361/201629512)

(ref: Galametz:2012aa) Galametz, M., Kennicutt, R. C., Albrecht, M., et al. 2012, MNRAS, 425, 763, doi: [`10.1111/j.1365-2966.2012.21667.x`](http://doi.org/10.1111/j.1365-2966.2012.21667.x)

(ref: Geach:2018aa) Geach, J. E., Ivison, R. J., Dye, S., & Oteo, I. 2018, ApJL, 866, L12, doi: [`10.3847/2041-8213/aae375`](http://doi.org/10.3847/2041-8213/aae375)

(ref: Geach:2015aa) Geach, J. E., More, A., Verma, A., et al. 2015, MNRAS, 452, 502, doi: [`10.1093/mnras/stv1243`](http://doi.org/10.1093/mnras/stv1243)

(ref: Geach:2017ab) Geach, J. E., Lin, Y. T., Makler, M., et al. 2017, ApJS, 231, 7, doi: [`10.3847/1538-4365/aa74b6`](http://doi.org/10.3847/1538-4365/aa74b6)

(ref: Giulietti:2022aa) Giulietti, M., Massardi, M., Lapi, A., et al. 2022, MNRAS, 511, 1408, doi: [`10.1093/mnras/stac145`](http://doi.org/10.1093/mnras/stac145)

(ref: Gladders:2000aa) Gladders, M. D., & Yee, H. K. C. 2000, AJ, 120, 2148, doi: [`10.1086/301557`](http://doi.org/10.1086/301557)

(ref: Gladders:2005aa) —. 2005, ApJS, 157, 1, doi: [`10.1086/427327`](http://doi.org/10.1086/427327)

(ref: Goldreich:1974aa) Goldreich, P., & Kwan, J. 1974, ApJ, 189, 441, doi: [`10.1086/152821`](http://doi.org/10.1086/152821)

(ref: Gomez-Guijarro:2022ab) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 658, A43, doi: [`10.1051/0004-6361/202141615`](http://doi.org/10.1051/0004-6361/202141615)

(ref: Gralla:2020aa) Gralla, M. B., Marriage, T. A., Addison, G., et al. 2020, ApJ, 893, 104, doi: [`10.3847/1538-4357/ab7915`](http://doi.org/10.3847/1538-4357/ab7915)

(ref: Griffin:2010aa) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3, doi: [`10.1051/0004-6361/201014519`](http://doi.org/10.1051/0004-6361/201014519)

(ref: Hainline:2011aa) Hainline, L. J., Blain, A. W., Smail, I., et al. 2011, ApJ, 740, 96, doi: [`10.1088/0004-637X/740/2/96`](http://doi.org/10.1088/0004-637X/740/2/96)

(ref: Hales:2012aa) Hales, C. A., Murphy, T., Curran, J. R., et al. 2012, MNRAS, 425, 979, doi: [`10.1111/j.1365-2966.2012.21373.x`](http://doi.org/10.1111/j.1365-2966.2012.21373.x)

(ref: Harper-Clark:2009aa) Harper-Clark, E., & Murray, N. 2009, ApJ, 693, 1696, doi: [`10.1088/0004-637X/693/2/1696`](http://doi.org/10.1088/0004-637X/693/2/1696)

(ref: Harrington:2016aa) Harrington, K. C., Yun, M. S., Cybulski, R., et al. 2016, MNRAS, 458, 4383, doi: [`10.1093/mnras/stw614`](http://doi.org/10.1093/mnras/stw614)

(ref: Harrington:2019ab) Harrington, K. C., Vishwas, A., Wei$^\text{s}$, A., et al. 2019, MNRAS, 488, 1489, doi: [`10.1093/mnras/stz1740`](http://doi.org/10.1093/mnras/stz1740)

(ref: Harrington:2021aa) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95, doi: [`10.3847/1538-4357/abcc01`](http://doi.org/10.3847/1538-4357/abcc01)

(ref: Hatsukade:2015aa) Hatsukade, B., Tamura, Y., Iono, D., et al. 2015, PASJ, 67, 93, doi: [`10.1093/pasj/psv061`](http://doi.org/10.1093/pasj/psv061)

(ref: Heesen:2018aa) Heesen, V., Krause, M., Beck, R., et al. 2018, MNRAS, 476, 158, doi: [`10.1093/mnras/sty105`](http://doi.org/10.1093/mnras/sty105)

(ref: Helou:1985aa) Helou, G., Soifer, B. T., & Rowan-Robinson, M. 1985, ApJL, 298, L7, doi: [`10.1086/184556`](http://doi.org/10.1086/184556)

(ref: Hezaveh:2012aa) Hezaveh, Y. D., Marrone, D. P., & Holder, G. P. 2012, ApJ, 761, 20, doi: [`10.1088/0004-637X/761/1/20`](http://doi.org/10.1088/0004-637X/761/1/20)

(ref: Hezaveh:2013aa) Hezaveh, Y. D., Marrone, D. P., Fassnacht, C. D., et al. 2013, ApJ, 767, 132, doi: [`10.1088/0004-637X/767/2/132`](http://doi.org/10.1088/0004-637X/767/2/132)

(ref: Hildebrandt:2009aa) Hildebrandt, H., van Waerbeke, L., & Erben, T. 2009, A&A, 507, 683, doi: [`10.1051/0004-6361/200912655`](http://doi.org/10.1051/0004-6361/200912655)

(ref: Hodge:2012aa) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11, doi: [`10.1088/0004-637X/760/1/11`](http://doi.org/10.1088/0004-637X/760/1/11)

(ref: Hodge:2015aa) Hodge, J. A., Riechers, D., Decarli, R., et al. 2015, ApJL, 798, L18, doi: [`10.1088/2041-8205/798/1/L18`](http://doi.org/10.1088/2041-8205/798/1/L18)

(ref: Hodge:2016aa) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: Hodge:2019aa) Hodge, J. A., Smail, I., Walter, F., et al. 2019, ApJ, 876, 130, doi: [`10.3847/1538-4357/ab1846`](http://doi.org/10.3847/1538-4357/ab1846)

(ref: Hogbom:1974aa) Högbom, J. A. 1974, A&AS, 15, 417

(ref: Hopkins:2014aa) Hopkins, P. F., Kereš, D., Oñorbe, J., et al. 2014, MNRAS, 445, 581, doi: [`10.1093/mnras/stu1738`](http://doi.org/10.1093/mnras/stu1738)

(ref: Hopkins:2018aa) Hopkins, P. F., Wetzel, A., Kereš, D., et al. 2018, MNRAS, 480, 800, doi: [`10.1093/mnras/sty1690`](http://doi.org/10.1093/mnras/sty1690)

(ref: Hughes:1998aa) Hughes, D. H., Serjeant, S., Dunlop, J., et al. 1998, Nature, 394, 241, doi: [`10.1038/28328`](http://doi.org/10.1038/28328)

(ref: Iani:2021aa) Iani, E., Zanella, A., Vernet, J., et al. 2021, MNRAS, 507, 3830, doi: [`10.1093/mnras/stab2376`](http://doi.org/10.1093/mnras/stab2376)

(ref: Ikarashi:2015aa) Ikarashi, S., Ivison, R. J., Caputi, K. I., et al. 2015, ApJ, 810, 133, doi: [`10.1088/0004-637X/810/2/133`](http://doi.org/10.1088/0004-637X/810/2/133)

(ref: Ikarashi:2017aa) Ikarashi, S., Caputi, K. I., Ohta, K., et al. 2017, ApJL, 849, L36, doi: [`10.3847/2041-8213/aa9572`](http://doi.org/10.3847/2041-8213/aa9572)

(ref: Iono:2016aa) Iono, D., Yun, M. S., Aretxaga, I., et al. 2016, ApJL, 829, L10, doi: [`10.3847/2041-8205/829/1/L10`](http://doi.org/10.3847/2041-8205/829/1/L10)

(ref: Ishibashi:2012aa) Ishibashi, W., & Fabian, A. C. 2012, MNRAS, 427, 2998, doi: [`10.1111/j.1365-2966.2012.22074.x`](http://doi.org/10.1111/j.1365-2966.2012.22074.x)

(ref: Ivison:2020aa) Ivison, R. J., Richard, J., Biggs, A. D., et al. 2020, MNRAS, doi: [`10.1093/mnrasl/slaa046`](http://doi.org/10.1093/mnrasl/slaa046)

(ref: Ivison:2002aa) Ivison, R. J., Greve, T. R., Smail, I., et al. 2002, MNRAS, 337, 1, doi: [`10.1046/j.1365-8711.2002.05900.x`](http://doi.org/10.1046/j.1365-8711.2002.05900.x)

(ref: Ivison:2010ac) Ivison, R. J., Magnelli, B., Ibar, E., et al. 2010, A&A, 518, L31, doi: [`10.1051/0004-6361/201014552`](http://doi.org/10.1051/0004-6361/201014552)

(ref: Jimenez-Andrade:2019aa) Jiménez-Andrade, E. F., Magnelli, B., Karim, A., et al. 2019, A&A, 625, A114, doi: [`10.1051/0004-6361/201935178`](http://doi.org/10.1051/0004-6361/201935178)

(ref: Jimenez-Andrade:2020aa) Jiménez-Andrade, E. F., Zavala, J. A., Magnelli, B., et al. 2020, ApJ, 890, 171, doi: [`10.3847/1538-4357/ab6dec`](http://doi.org/10.3847/1538-4357/ab6dec)

(ref: Jimenez-Andrade:2021aa) Jiménez-Andrade, E. F., Murphy, E. J., Heywood, I., et al. 2021, ApJ, 910, 106, doi: [`10.3847/1538-4357/abe876`](http://doi.org/10.3847/1538-4357/abe876)

(ref: Johnson:2014aa) Johnson, T. L., Sharon, K., Bayliss, M. B., et al. 2014, ApJ, 797, 48, doi: [`10.1088/0004-637X/797/1/48`](http://doi.org/10.1088/0004-637X/797/1/48)

(ref: Jullo:2009aa) Jullo, E., & Kneib, J.-P. 2009, MNRAS, 395, 1319, doi: [`10.1111/j.1365-2966.2009.14654.x`](http://doi.org/10.1111/j.1365-2966.2009.14654.x)

(ref: Jullo:2007aa) Jullo, E., Kneib, J.-P., Limousin, M., et al. 2007, New Journal of Physics, 9, 447, doi: [`10.1088/1367-2630/9/12/447`](http://doi.org/10.1088/1367-2630/9/12/447)

(ref: Kassiola:1993aa) Kassiola, A., & Kovner, I. 1993, ApJ, 417, 450, doi: [`10.1086/173325`](http://doi.org/10.1086/173325)

(ref: Keeton:2011aa) Keeton, C. R. 2011, GRAVLENS: Computational Methods for Gravitational Lensing, Astrophysics Source Code Library. [`http://ascl.net/1102.003`](http://ascl.net/1102.003)

(ref: Kennicutt:1998aa) Kennicutt, Jr., R. C. 1998, ARA&A, 36, 189, doi: [`10.1146/annurev.astro.36.1.189`](http://doi.org/10.1146/annurev.astro.36.1.189)

(ref: Keres:2005aa) Kereš, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2, doi: [`10.1111/j.1365-2966.2005.09451.x`](http://doi.org/10.1111/j.1365-2966.2005.09451.x)

(ref: Kneib:1996aa) Kneib, J.-P., Ellis, R. S., Smail, I., Couch, W. J., & Sharples, R. M. 1996, ApJ, 471, 643, doi: [`10.1086/177995`](http://doi.org/10.1086/177995)

(ref: Kneib:1993aa) Kneib, J. P., Mellier, Y., Fort, B., & Mathez, G. 1993, A&A, 273, 367

(ref: Kochanek:1991aa) Kochanek, C. S. 1991, ApJ, 373, 354, doi: [`10.1086/170057`](http://doi.org/10.1086/170057)

(ref: Koopmans:2006aa) Koopmans, L. V. E., Treu, T., Bolton, A. S., Burles, S., & Moustakas, L. A. 2006, ApJ, 649, 599, doi: [`10.1086/505696`](http://doi.org/10.1086/505696)

(ref: Koopmans:2009aa) Koopmans, L. V. E., Bolton, A., Treu, T., et al. 2009, ApJL, 703, L51, doi: [`10.1088/0004-637X/703/1/L51`](http://doi.org/10.1088/0004-637X/703/1/L51)

(ref: Kormann:1994aa) Kormann, R., Schneider, P., & Bartelmann, M. 1994, A&A, 284, 285

(ref: Lapi:2018aa) Lapi, A., Pantoni, L., Zanisi, L., et al. 2018, ApJ, 857, 22, doi: [`10.3847/1538-4357/aab6af`](http://doi.org/10.3847/1538-4357/aab6af)

(ref: Leslie:2020aa) Leslie, S. K., Schinnerer, E., Liu, D., et al. 2020, ApJ, 899, 58, doi: [`10.3847/1538-4357/aba044`](http://doi.org/10.3847/1538-4357/aba044)

(ref: Lilly:1999aa) Lilly, S. J., Eales, S. A., Gear, W. K. P., et al. 1999, ApJ, 518, 641, doi: [`10.1086/307310`](http://doi.org/10.1086/307310)

(ref: Limousin:2009aa) Limousin, M., Cabanac, R., Gavazzi, R., et al. 2009, A&A, 502, 445, doi: [`10.1051/0004-6361/200811473`](http://doi.org/10.1051/0004-6361/200811473)

(ref: Limousin:2016aa) Limousin, M., Richard, J., Jullo, E., et al. 2016, A&A, 588, A99, doi: [`10.1051/0004-6361/201527638`](http://doi.org/10.1051/0004-6361/201527638)

(ref: Lindroos:2018aa) Lindroos, L., Knudsen, K. K., Stanley, F., et al. 2018, MNRAS, 476, 3544, doi: [`10.1093/mnras/sty426`](http://doi.org/10.1093/mnras/sty426)

(ref: Liu:2022ad) Liu, B., Chartab, N., Nayyeri, H., et al. 2022, ApJ, 929, 41, doi: [`10.3847/1538-4357/ac5745`](http://doi.org/10.3847/1538-4357/ac5745)

(ref: Liu:2019ad) Liu, D., Lang, P., Magnelli, B., et al. 2019a, ApJS, 244, 40, doi: [`10.3847/1538-4365/ab42da`](http://doi.org/10.3847/1538-4365/ab42da)

(ref: Liu:2019ae) Liu, D., Schinnerer, E., Groves, B., et al. 2019b, ApJ, 887, 235, doi: [`10.3847/1538-4357/ab578d`](http://doi.org/10.3847/1538-4357/ab578d)

(ref: Lonsdale:2006aa) Lonsdale, C. J., Farrah, D., & Smith, H. E. 2006, Ultraluminous Infrared Galaxies (Springer-Verlag), 285, doi: [`10.1007/3-540-30313-8_9`](http://doi.org/10.1007/3-540-30313-8_9)

(ref: Lutz:2014aa) Lutz, D. 2014, ARA&A, 52, 373, doi: [`10.1146/annurev-astro-081913-035953`](http://doi.org/10.1146/annurev-astro-081913-035953)

(ref: Ma:2016aa) Ma, J., Gonzalez, A. H., Vieira, J. D., et al. 2016, ApJ, 832, 114, doi: [`10.3847/0004-637X/832/2/114`](http://doi.org/10.3847/0004-637X/832/2/114)

(ref: Ma:2015ab) Ma, Z., & Yan, H. 2015, ApJ, 811, 58, doi: [`10.1088/0004-637X/811/1/58`](http://doi.org/10.1088/0004-637X/811/1/58)

(ref: Magnelli:2015aa) Magnelli, B., Ivison, R. J., Lutz, D., et al. 2015, A&A, 573, A45, doi: [`10.1051/0004-6361/201424937`](http://doi.org/10.1051/0004-6361/201424937)

(ref: Marsden:2014aa) Marsden, D., Gralla, M., Marriage, T. A., et al. 2014, MNRAS, 439, 1556, doi: [`10.1093/mnras/stu001`](http://doi.org/10.1093/mnras/stu001)

(ref: Marsh:1998aa) Marsh, K. A., & Helou, G. 1998, ApJ, 493, 121, doi: [`10.1086/305088`](http://doi.org/10.1086/305088)

(ref: Marshall:2016aa) Marshall, P. J., Verma, A., More, A., et al. 2016, MNRAS, 455, 1171, doi: [`10.1093/mnras/stv2009`](http://doi.org/10.1093/mnras/stv2009)

(ref: Massardi:2018aa) Massardi, M., Enia, A. F. M., Negrello, M., et al. 2018, A&A, 610, A53, doi: [`10.1051/0004-6361/201731751`](http://doi.org/10.1051/0004-6361/201731751)

(ref: McMullin:2007aa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meneghetti:2013aa) Meneghetti, M., Bartelmann, M., Dahle, H., & Limousin, M. 2013, Space Sci. Rev., 177, 31, doi: [`10.1007/s11214-013-9981-x`](http://doi.org/10.1007/s11214-013-9981-x)

(ref: Meneghetti:2003ab) Meneghetti, M., Bartelmann, M., & Moscardini, L. 2003, MNRAS, 340, 105, doi: [`10.1046/j.1365-8711.2003.06276.x`](http://doi.org/10.1046/j.1365-8711.2003.06276.x)

(ref: Meneghetti:2011aa) Meneghetti, M., Fedeli, C., Zitrin, A., et al. 2011, A&A, 530, A17, doi: [`10.1051/0004-6361/201016040`](http://doi.org/10.1051/0004-6361/201016040)

(ref: Menendez-Delmestre:2013aa) Menéndez-Delmestre, K., Blain, A. W., Swinbank, M., et al. 2013, ApJ, 767, 151, doi: [`10.1088/0004-637X/767/2/151`](http://doi.org/10.1088/0004-637X/767/2/151)

(ref: Miettinen:2017aa) Miettinen, O., Delvecchio, I., Smolčić, V., et al. 2017, A&A, 606, A17, doi: [`10.1051/0004-6361/201730762`](http://doi.org/10.1051/0004-6361/201730762)

(ref: Mocanu:2013aa) Mocanu, L. M., Crawford, T. M., Vieira, J. D., et al. 2013, ApJ, 779, 61, doi: [`10.1088/0004-637X/779/1/61`](http://doi.org/10.1088/0004-637X/779/1/61)

(ref: Moraes:2014aa) Moraes, B., Kneib, J. P., Leauthaud, A., et al. 2014, in Revista Mexicana de Astronomia y Astrofisica Conference Series, Vol. 44, Revista Mexicana de Astronomia y Astrofisica Conference Series, 202–203

(ref: More:2016ab) More, A., Verma, A., Marshall, P. J., et al. 2016, MNRAS, 455, 1191, doi: [`10.1093/mnras/stv1965`](http://doi.org/10.1093/mnras/stv1965)

(ref: Murphy:2017aa) Murphy, E. J., Momjian, E., Condon, J. J., et al. 2017, ApJ, 839, 35, doi: [`10.3847/1538-4357/aa62fd`](http://doi.org/10.3847/1538-4357/aa62fd)

(ref: Murphy:2006aa) Murphy, E. J., Braun, R., Helou, G., et al. 2006a, ApJ, 638, 157, doi: [`10.1086/498636`](http://doi.org/10.1086/498636)

(ref: Murphy:2006ab) Murphy, E. J., Helou, G., Braun, R., et al. 2006b, ApJL, 651, L111, doi: [`10.1086/509722`](http://doi.org/10.1086/509722)

(ref: Murray:2005aa) Murray, N., Quataert, E., & Thompson, T. A. 2005, ApJ, 618, 569, doi: [`10.1086/426067`](http://doi.org/10.1086/426067)

(ref: Murray:2010aa) —. 2010, ApJ, 709, 191, doi: [`10.1088/0004-637X/709/1/191`](http://doi.org/10.1088/0004-637X/709/1/191)

(ref: Narayan:1996aa) Narayan, R., & Bartelmann, M. 1996, ArXiv Astrophysics e-prints

(ref: Narayanan:2010ab) Narayanan, D., Hayward, C. C., Cox, T. J., et al. 2010, MNRAS, 401, 1613, doi: [`10.1111/j.1365-2966.2009.15790.x`](http://doi.org/10.1111/j.1365-2966.2009.15790.x)

(ref: Narayanan:2006aa) Narayanan, D., Cox, T. J., Robertson, B., et al. 2006, ApJL, 642, L107, doi: [`10.1086/504846`](http://doi.org/10.1086/504846)

(ref: Nayyeri:2016aa) Nayyeri, H., Keele, M., Cooray, A., et al. 2016, ApJ, 823, 17, doi: [`10.3847/0004-637X/823/1/17`](http://doi.org/10.3847/0004-637X/823/1/17)

(ref: Negrello:2007aa) Negrello, M., Perrotta, F., González-Nuevo, J., et al. 2007, MNRAS, 377, 1557, doi: [`10.1111/j.1365-2966.2007.11708.x`](http://doi.org/10.1111/j.1365-2966.2007.11708.x)

(ref: Negrello:2010aa) Negrello, M., Hopwood, R., De Zotti, G., et al. 2010, Science, 330, 800, doi: [`10.1126/science.1193420`](http://doi.org/10.1126/science.1193420)

(ref: Negrello:2017aa) Negrello, M., Amber, S., Amvrosiadis, A., et al. 2017, MNRAS, 465, 3558, doi: [`10.1093/mnras/stw2911`](http://doi.org/10.1093/mnras/stw2911)

(ref: Nelson:2016aa) Nelson, E. J., van Dokkum, P. G., Momcheva, I. G., et al. 2016, ApJL, 817, L9, doi: [`10.3847/2041-8205/817/1/L9`](http://doi.org/10.3847/2041-8205/817/1/L9)

(ref: Nelson:2022aa) Nelson, E. J., Suess, K. A., Bezanson, R., et al. 2022, arXiv e-prints, arXiv:2208.01630. [`https://arxiv.org/abs/2208.01630`](https://arxiv.org/abs/2208.01630)

(ref: Nesvadba:2019aa) Nesvadba, N. P. H., Cañameras, R., Kneissl, R., et al. 2019, A&A, 624, A23, doi: [`10.1051/0004-6361/201833777`](http://doi.org/10.1051/0004-6361/201833777)

(ref: Nightingale:2015aa) Nightingale, J. W., & Dye, S. 2015, MNRAS, 452, 2940, doi: [`10.1093/mnras/stv1455`](http://doi.org/10.1093/mnras/stv1455)

(ref: Noeske:2007aa) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43, doi: [`10.1086/517926`](http://doi.org/10.1086/517926)

(ref: Oteo:2017ac) Oteo, I., Zwaan, M. A., Ivison, R. J., Smail, I., & Biggs, A. D. 2017, ApJ, 837, 182, doi: [`10.3847/1538-4357/aa5da4`](http://doi.org/10.3847/1538-4357/aa5da4)

(ref: Oteo:2016aa) Oteo, I., Ivison, R. J., Dunne, L., et al. 2016, ApJ, 827, 34, doi: [`10.3847/0004-637X/827/1/34`](http://doi.org/10.3847/0004-637X/827/1/34)

(ref: Pantoni:2021ab) Pantoni, L., Massardi, M., Lapi, A., et al. 2021, MNRAS, 507, 3998, doi: [`10.1093/mnras/stab2346`](http://doi.org/10.1093/mnras/stab2346)

(ref: Pascale:2022aa) Pascale, M., Frye, B. L., Dai, L., et al. 2022, ApJ, 932, 85, doi: [`10.3847/1538-4357/ac6ce9`](http://doi.org/10.3847/1538-4357/ac6ce9)

(ref: Peng:2002aa) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266, doi: [`10.1086/340952`](http://doi.org/10.1086/340952)

(ref: Planck-Collaboration:2014ab) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2014, A&A, 571, A28, doi: [`10.1051/0004-6361/201321524`](http://doi.org/10.1051/0004-6361/201321524)

(ref: Planck-Collaboration:2015aa) Planck Collaboration, Aghanim, N., Altieri, B., et al. 2015, A&A, 582, A30, doi: [`10.1051/0004-6361/201424790`](http://doi.org/10.1051/0004-6361/201424790)

(ref: Ramasawmy:2021aa) Ramasawmy, J., Geach, J. E., Hardcastle, M. J., et al. 2021, A&A, 648, A14, doi: [`10.1051/0004-6361/202039858`](http://doi.org/10.1051/0004-6361/202039858)

(ref: Redlich:2012aa) Redlich, M., Bartelmann, M., Waizmann, J. C., & Fedeli, C. 2012, A&A, 547, A66, doi: [`10.1051/0004-6361/201219722`](http://doi.org/10.1051/0004-6361/201219722)

(ref: Refsdal:1994aa) Refsdal, S., & Surdej, J. 1994, Reports on Progress in Physics, 57, 117, doi: [`10.1088/0034-4885/57/2/001`](http://doi.org/10.1088/0034-4885/57/2/001)

(ref: Reuter:2020aa) Reuter, C., Vieira, J. D., Spilker, J. S., et al. 2020, ApJ, 902, 78, doi: [`10.3847/1538-4357/abb599`](http://doi.org/10.3847/1538-4357/abb599)

(ref: Richard:2010aa) Richard, J., Smith, G. P., Kneib, J.-P., et al. 2010, MNRAS, 404, 325, doi: [`10.1111/j.1365-2966.2009.16274.x`](http://doi.org/10.1111/j.1365-2966.2009.16274.x)

(ref: Riechers:2013aa) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329, doi: [`10.1038/nature12050`](http://doi.org/10.1038/nature12050)

(ref: Riechers:2014aa) Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014, ApJ, 796, 84, doi: [`10.1088/0004-637X/796/2/84`](http://doi.org/10.1088/0004-637X/796/2/84)

(ref: Riechers:2017aa) Riechers, D. A., Leung, T. K. D., Ivison, R. J., et al. 2017, ApJ, 850, 1, doi: [`10.3847/1538-4357/aa8ccf`](http://doi.org/10.3847/1538-4357/aa8ccf)

(ref: Rivera:2019aa) Rivera, J., Baker, A. J., Gallardo, P. A., et al. 2019, ApJ, 879, 95, doi: [`10.3847/1538-4357/ab264b`](http://doi.org/10.3847/1538-4357/ab264b)

(ref: Robertson:2020aa) Robertson, A., Smith, G. P., Massey, R., et al. 2020, MNRAS, doi: [`10.1093/mnras/staa1429`](http://doi.org/10.1093/mnras/staa1429)

(ref: Robitaille:2012aa) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library, record ascl:1208.017. [`http://ascl.net/1208.017`](http://ascl.net/1208.017)

(ref: Rodighiero:2011aa) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40, doi: [`10.1088/2041-8205/739/2/L40`](http://doi.org/10.1088/2041-8205/739/2/L40)

(ref: Rogers:2013aa) Rogers, H., & Pittard, J. M. 2013, MNRAS, 431, 1337, doi: [`10.1093/mnras/stt255`](http://doi.org/10.1093/mnras/stt255)

(ref: Rujopakarn:2016aa) Rujopakarn, W., Dunlop, J. S., Rieke, G. H., et al. 2016, ApJ, 833, 12, doi: [`10.3847/0004-637X/833/1/12`](http://doi.org/10.3847/0004-637X/833/1/12)

(ref: Rybak:2015aa) Rybak, M., McKean, J. P., Vegetti, S., Andreani, P., & White, S. D. M. 2015, MNRAS, 451, L40, doi: [`10.1093/mnrasl/slv058`](http://doi.org/10.1093/mnrasl/slv058)

(ref: Sanders:1996aa) Sanders, D. B., & Mirabel, I. F. 1996, ARA&A, 34, 749, doi: [`10.1146/annurev.astro.34.1.749`](http://doi.org/10.1146/annurev.astro.34.1.749)

(ref: Sargent:2010aa) Sargent, M. T., Schinnerer, E., Murphy, E., et al. 2010a, ApJS, 186, 341, doi: [`10.1088/0067-0049/186/2/341`](http://doi.org/10.1088/0067-0049/186/2/341)

(ref: Sargent:2010ab) —. 2010b, ApJL, 714, L190, doi: [`10.1088/2041-8205/714/2/L190`](http://doi.org/10.1088/2041-8205/714/2/L190)

(ref: Schneider:1992aa) Schneider, P., Ehlers, J., & Falco, E. E. 1992, Gravitational Lenses (Springer-Verlag), 112, doi: [`10.1007/978-3-662-03758-4`](http://doi.org/10.1007/978-3-662-03758-4)

(ref: Science-Software-Branch-at-STScI:2012aa) Science Software Branch at STScI. 2012, PyRAF: Python alternative for IRAF, Astrophysics Source Code Library, record ascl:1207.011. [`http://ascl.net/1207.011`](http://ascl.net/1207.011)

(ref: Scott:1992aa) Scott, D. W. 1992, Multivariate Density Estimation (John Wiley & Sons, Inc.)

(ref: Scoville:2003aa) Scoville, N. 2003, Journal of Korean Astronomical Society, 36, 167, doi: [`10.5303/JKAS.2003.36.3.167`](http://doi.org/10.5303/JKAS.2003.36.3.167)

(ref: Scoville:2007aa) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1, doi: [`10.1086/516585`](http://doi.org/10.1086/516585)

(ref: Scoville:2016aa) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: Scoville:2017aa) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150, doi: [`10.3847/1538-4357/aa61a0`](http://doi.org/10.3847/1538-4357/aa61a0)

(ref: Scoville:2013aa) Scoville, N. Z. 2013, in Secular Evolution of Galaxies, ed. J. Falcón-Barroso & J. H. Knapen (Cambridge University Press), 491

(ref: Scoville:2001aa) Scoville, N. Z., Polletta, M., Ewald, S., et al. 2001, AJ, 122, 3017, doi: [`10.1086/323445`](http://doi.org/10.1086/323445)

(ref: Scoville:1974aa) Scoville, N. Z., & Solomon, P. M. 1974, ApJL, 187, L67, doi: [`10.1086/181398`](http://doi.org/10.1086/181398)

(ref: Scoville:1997aa) Scoville, N. Z., Yun, M. S., & Bryant, P. M. 1997, ApJ, 484, 702, doi: [`10.1086/304368`](http://doi.org/10.1086/304368)

(ref: Scranton:2005aa) Scranton, R., Ménard, B., Richards, G. T., et al. 2005, ApJ, 633, 589, doi: [`10.1086/431358`](http://doi.org/10.1086/431358)

(ref: Serjeant:2012aa) Serjeant, S. 2012, MNRAS, 424, 2429, doi: [`10.1111/j.1365-2966.2012.20761.x`](http://doi.org/10.1111/j.1365-2966.2012.20761.x)

(ref: Sersic:1963aa) Sérsic, J. L. 1963, Boletin de la Asociacion Argentina de Astronomia La Plata Argentina, 6, 41

(ref: Sharma:2018aa) Sharma, S., Richard, J., Yuan, T., et al. 2018, MNRAS, 481, 1427, doi: [`10.1093/mnras/sty2352`](http://doi.org/10.1093/mnras/sty2352)

(ref: Sharma:2021aa) —. 2021, MNRAS, doi: [`10.1093/mnrasl/slab040`](http://doi.org/10.1093/mnrasl/slab040)

(ref: Sharon:2019ab) Sharon, C. E., Tagore, A. S., Baker, A. J., et al. 2019, ApJ, 879, 52, doi: [`10.3847/1538-4357/ab22b9`](http://doi.org/10.3847/1538-4357/ab22b9)

(ref: Sharon:2012aa) Sharon, K., Gladders, M. D., Rigby, J. R., et al. 2012, ApJ, 746, 161, doi: [`10.1088/0004-637X/746/2/161`](http://doi.org/10.1088/0004-637X/746/2/161)

(ref: Shibuya:2015aa) Shibuya, T., Ouchi, M., & Harikane, Y. 2015, ApJS, 219, 15, doi: [`10.1088/0067-0049/219/2/15`](http://doi.org/10.1088/0067-0049/219/2/15)

(ref: Simpson:2015ab) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015a, ApJ, 799, 81, doi: [`10.1088/0004-637X/799/1/81`](http://doi.org/10.1088/0004-637X/799/1/81)

(ref: Simpson:2015aa) —. 2015b, ApJ, 807, 128, doi: [`10.1088/0004-637X/807/2/128`](http://doi.org/10.1088/0004-637X/807/2/128)

(ref: Smail:1997aa) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5, doi: [`10.1086/311017`](http://doi.org/10.1086/311017)

(ref: Smith:1986aa) Smith, E. P., Heckman, T. M., Bothun, G. D., Romanishin, W., & Balick, B. 1986, ApJ, 306, 64, doi: [`10.1086/164321`](http://doi.org/10.1086/164321)

(ref: Song:2022aa) Song, Y., Linden, S. T., Evans, A. S., et al. 2022, ApJ, 940, 52, doi: [`10.3847/1538-4357/ac923b`](http://doi.org/10.3847/1538-4357/ac923b)

(ref: Speagle:2014aa) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: Spilker:2016aa) Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112, doi: [`10.3847/0004-637X/826/2/112`](http://doi.org/10.3847/0004-637X/826/2/112)

(ref: Spilker:2022aa) Spilker, J. S., Hayward, C. C., Marrone, D. P., et al. 2022, ApJL, 929, L3, doi: [`10.3847/2041-8213/ac61e6`](http://doi.org/10.3847/2041-8213/ac61e6)

(ref: Springel:2005aa) Springel, V., Di Matteo, T., & Hernquist, L. 2005, MNRAS, 361, 776, doi: [`10.1111/j.1365-2966.2005.09238.x`](http://doi.org/10.1111/j.1365-2966.2005.09238.x)

(ref: Stacey:2021ab) Stacey, H. R., McKean, J. P., Powell, D. M., et al. 2021, MNRAS, 500, 3667, doi: [`10.1093/mnras/staa3433`](http://doi.org/10.1093/mnras/staa3433)

(ref: Su:2017aa) Su, T., Marriage, T. A., Asboth, V., et al. 2017, MNRAS, 464, 968, doi: [`10.1093/mnras/stw2334`](http://doi.org/10.1093/mnras/stw2334)

(ref: Suess:2019aa) Suess, K. A., Kriek, M., Price, S. H., & Barro, G. 2019, ApJ, 877, 103, doi: [`10.3847/1538-4357/ab1bda`](http://doi.org/10.3847/1538-4357/ab1bda)

(ref: Suess:2022aa) Suess, K. A., Bezanson, R., Nelson, E. J., et al. 2022, ApJL, 937, L33, doi: [`10.3847/2041-8213/ac8e06`](http://doi.org/10.3847/2041-8213/ac8e06)

(ref: Swinbank:2010aa) Swinbank, A. M., Smail, I., Longmore, S., et al. 2010, Nature, 464, 733, doi: [`10.1038/nature08880`](http://doi.org/10.1038/nature08880)

(ref: Swinbank:2011aa) Swinbank, A. M., Papadopoulos, P. P., Cox, P., et al. 2011, ApJ, 742, 11, doi: [`10.1088/0004-637X/742/1/11`](http://doi.org/10.1088/0004-637X/742/1/11)

(ref: Swinbank:2014aa) Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267, doi: [`10.1093/mnras/stt2273`](http://doi.org/10.1093/mnras/stt2273)

(ref: Tabatabaei:2007aa) Tabatabaei, F. S., Beck, R., Krause, M., et al. 2007, A&A, 466, 509, doi: [`10.1051/0004-6361:20066731`](http://doi.org/10.1051/0004-6361:20066731)

(ref: Tacchella:2018aa) Tacchella, S., Carollo, C. M., Förster Schreiber, N. M., et al. 2018, ApJ, 859, 56, doi: [`10.3847/1538-4357/aabf8b`](http://doi.org/10.3847/1538-4357/aabf8b)

(ref: Tacconi:2006aa) Tacconi, L. J., Neri, R., Chapman, S. C., et al. 2006, ApJ, 640, 228, doi: [`10.1086/499933`](http://doi.org/10.1086/499933)

(ref: Tacconi:2008aa) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680, 246, doi: [`10.1086/587168`](http://doi.org/10.1086/587168)

(ref: Tacconi:2018aa) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: Tadaki:2018aa) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613, doi: [`10.1038/s41586-018-0443-1`](http://doi.org/10.1038/s41586-018-0443-1)

(ref: Tadaki:2015aa) Tadaki, K.-i., Kohno, K., Kodama, T., et al. 2015, ApJL, 811, L3, doi: [`10.1088/2041-8205/811/1/L3`](http://doi.org/10.1088/2041-8205/811/1/L3)

(ref: Tadaki:2017ab) Tadaki, K.-i., Genzel, R., Kodama, T., et al. 2017, ApJ, 834, 135, doi: [`10.3847/1538-4357/834/2/135`](http://doi.org/10.3847/1538-4357/834/2/135)

(ref: Tadaki:2020aa) Tadaki, K.-i., Iono, D., Yun, M. S., et al. 2020, ApJ, 889, 141, doi: [`10.3847/1538-4357/ab64f4`](http://doi.org/10.3847/1538-4357/ab64f4)

(ref: Talia:2018aa) Talia, M., Pozzi, F., Vallini, L., et al. 2018, MNRAS, 476, 3956, doi: [`10.1093/mnras/sty481`](http://doi.org/10.1093/mnras/sty481)

(ref: Tamura:2015aa) Tamura, Y., Oguri, M., Iono, D., et al. 2015, PASJ, 67, 72, doi: [`10.1093/pasj/psv040`](http://doi.org/10.1093/pasj/psv040)

(ref: Tan:2001aa) Tan, J. C., & McKee, C. F. 2001, in Starburst Galaxies: Near and Far, ed. L. Tacconi & D. Lutz, 188. [`https://arxiv.org/abs/astro-ph/0012005`](https://arxiv.org/abs/astro-ph/0012005)

(ref: Thompson:2005aa) Thompson, T. A., Quataert, E., & Murray, N. 2005, ApJ, 630, 167, doi: [`10.1086/431923`](http://doi.org/10.1086/431923)

(ref: Thomson:2015aa) Thomson, A. P., Ivison, R. J., Owen, F. N., et al. 2015, MNRAS, 448, 1874, doi: [`10.1093/mnras/stv118`](http://doi.org/10.1093/mnras/stv118)

(ref: Tody:1986aa) Tody, D. 1986, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 627, Instrumentation in astronomy VI, ed. D. L. Crawford, 733, doi: [`10.1117/12.968154`](http://doi.org/10.1117/12.968154)

(ref: Tody:1993aa) Tody, D. 1993, in Astronomical Society of the Pacific Conference Series, Vol. 52, Astronomical Data Analysis Software and Systems II, ed. R. J. Hanisch, R. J. V. Brissenden, & J. Barnes, 173

(ref: Toft:2014aa) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68, doi: [`10.1088/0004-637X/782/2/68`](http://doi.org/10.1088/0004-637X/782/2/68)

(ref: Treu:2010aa) Treu, T. 2010, ARA&A, 48, 87, doi: [`10.1146/annurev-astro-081309-130924`](http://doi.org/10.1146/annurev-astro-081309-130924)

(ref: Treu:2004aa) Treu, T., & Koopmans, L. V. E. 2004, ApJ, 611, 739, doi: [`10.1086/422245`](http://doi.org/10.1086/422245)

(ref: Trombetti:2021ab) Trombetti, T., Burigana, C., Bonato, M., et al. 2021, A&A, 653, A151, doi: [`10.1051/0004-6361/202140830`](http://doi.org/10.1051/0004-6361/202140830)

(ref: Turner:1980aa) Turner, E. L. 1980, ApJL, 242, L135, doi: [`10.1086/183418`](http://doi.org/10.1086/183418)

(ref: Turner:1984aa) Turner, E. L., Ostriker, J. P., & Gott, III, J. R. 1984, ApJ, 284, 1, doi: [`10.1086/162379`](http://doi.org/10.1086/162379)

(ref: Vanzella:2019aa) Vanzella, E., Calura, F., Meneghetti, M., et al. 2019, MNRAS, 483, 3618, doi: [`10.1093/mnras/sty3311`](http://doi.org/10.1093/mnras/sty3311)

(ref: Verdugo:2014aa) Verdugo, T., Motta, V., Foëx, G., et al. 2014, A&A, 571, A65, doi: [`10.1051/0004-6361/201423696`](http://doi.org/10.1051/0004-6361/201423696)

(ref: Vieira:2010aa) Vieira, J. D., Crawford, T. M., Switzer, E. R., et al. 2010, ApJ, 719, 763, doi: [`10.1088/0004-637X/719/1/763`](http://doi.org/10.1088/0004-637X/719/1/763)

(ref: Vieira:2013aa) Vieira, J. D., Marrone, D. P., Chapman, S. C., et al. 2013, Nature, 495, 344, doi: [`10.1038/nature12001`](http://doi.org/10.1038/nature12001)

(ref: Viero:2014aa) Viero, M. P., Asboth, V., Roseboom, I. G., et al. 2014, ApJS, 210, 22, doi: [`10.1088/0067-0049/210/2/22`](http://doi.org/10.1088/0067-0049/210/2/22)

(ref: Wagner:2016aa) Wagner, J., & Bartelmann, M. 2016, A&A, 590, A34, doi: [`10.1051/0004-6361/201527540`](http://doi.org/10.1051/0004-6361/201527540)

(ref: Wagner:2018aa) Wagner, J., & Tessore, N. 2018, A&A, 613, A6, doi: [`10.1051/0004-6361/201730947`](http://doi.org/10.1051/0004-6361/201730947)

(ref: Walter:2009aa) Walter, F., Riechers, D., Cox, P., et al. 2009, Nature, 457, 699, doi: [`10.1038/nature07681`](http://doi.org/10.1038/nature07681)

(ref: Wambsganss:1994aa) Wambsganss, J., & Paczynski, B. 1994, AJ, 108, 1156, doi: [`10.1086/117144`](http://doi.org/10.1086/117144)

(ref: Wang:2019ab) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211, doi: [`10.1038/s41586-019-1452-4`](http://doi.org/10.1038/s41586-019-1452-4)

(ref: Wang:2022ac) Wang, T.-M., Magnelli, B., Schinnerer, E., et al. 2022, A&A, 660, A142, doi: [`10.1051/0004-6361/202142299`](http://doi.org/10.1051/0004-6361/202142299)

(ref: Wardlow:2013aa) Wardlow, J. L., Cooray, A., De Bernardis, F., et al. 2013, ApJ, 762, 59, doi: [`10.1088/0004-637X/762/1/59`](http://doi.org/10.1088/0004-637X/762/1/59)

(ref: Warren:2003aa) Warren, S. J., & Dye, S. 2003, ApJ, 590, 673, doi: [`10.1086/375132`](http://doi.org/10.1086/375132)

(ref: Weiss:2013aa) Weiss, A., De Breuck, C., Marrone, D. P., et al. 2013, ApJ, 767, 88, doi: [`10.1088/0004-637X/767/1/88`](http://doi.org/10.1088/0004-637X/767/1/88)

(ref: Welch:2022ab) Welch, B., Coe, D., Zitrin, A., et al. 2022, arXiv e-prints, arXiv:2207.03532. [`https://arxiv.org/abs/2207.03532`](https://arxiv.org/abs/2207.03532)

(ref: Wen:2015aa) Wen, Z. L., & Han, J. L. 2015, ApJ, 807, 178, doi: [`10.1088/0004-637X/807/2/178`](http://doi.org/10.1088/0004-637X/807/2/178)

(ref: Whitaker:2017aa) Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ, 850, 208, doi: [`10.3847/1538-4357/aa94ce`](http://doi.org/10.3847/1538-4357/aa94ce)

(ref: Whitaker:2012aa) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: Wiegert:2015aa) Wiegert, T., Irwin, J., Miskolczi, A., et al. 2015, AJ, 150, 81, doi: [`10.1088/0004-6256/150/3/81`](http://doi.org/10.1088/0004-6256/150/3/81)

(ref: Wright:2006aa) Wright, E. L. 2006, PASP, 118, 1711, doi: [`10.1086/510102`](http://doi.org/10.1086/510102)

(ref: Yan:2016aa) Yan, H., & Ma, Z. 2016, ApJL, 820, L16, doi: [`10.3847/2041-8205/820/1/L16`](http://doi.org/10.3847/2041-8205/820/1/L16)

(ref: Yang:2017aa) Yang, C., Omont, A., Beelen, A., et al. 2017, A&A, 608, A144, doi: [`10.1051/0004-6361/201731391`](http://doi.org/10.1051/0004-6361/201731391)

(ref: Younger:2008aa) Younger, J. D., Fazio, G. G., Wilner, D. J., et al. 2008, ApJ, 688, 59, doi: [`10.1086/591931`](http://doi.org/10.1086/591931)

(ref: Yun:2001aa) Yun, M. S., Reddy, N. A., & Condon, J. J. 2001, ApJ, 554, 803, doi: [`10.1086/323145`](http://doi.org/10.1086/323145)

(ref: Yun:2015aa) Yun, M. S., Aretxaga, I., Gurwell, M. A., et al. 2015, MNRAS, 454, 3485, doi: [`10.1093/mnras/stv1963`](http://doi.org/10.1093/mnras/stv1963)

(ref: Zavala:2022ab) Zavala, J. A., Buat, V., Casey, C. M., et al. 2022, arXiv e-prints, arXiv:2208.01816. [`https://arxiv.org/abs/2208.01816`](https://arxiv.org/abs/2208.01816)

(ref: Zitrin:2011aa) Zitrin, A., Broadhurst, T., Barkana, R., Rephaeli, Y., & Benı́tez, N. 2011, MNRAS, 410, 1939, doi: [`10.1111/j.1365-2966.2010.17574.x`](http://doi.org/10.1111/j.1365-2966.2010.17574.x)

(ref: Zitrin:2009aa) Zitrin, A., Broadhurst, T., Umetsu, K., et al. 2009, MNRAS, 396, 1985, doi: [`10.1111/j.1365-2966.2009.14899.x`](http://doi.org/10.1111/j.1365-2966.2009.14899.x)

(ref: Zitrin:2015aa) Zitrin, A., Labbé, I., Belli, S., et al. 2015, ApJL, 810, L12, doi: [`10.1088/2041-8205/810/1/L12`](http://doi.org/10.1088/2041-8205/810/1/L12)

[^1]: Cluster-scale lenses, most of which are not included in this analysis, are more likely to be affected by this.

[^2]: <https://github.com/GeminiDRSoftware/DRAGONS>

[^3]: <https://projets.lam.fr/projects/lenstool/wiki>

[^4]: See also (cite: Broadhurst:2005aa), (cite: Acebron:2018aa), and (cite: Cibirka:2018aa).

[^5]: The right ascension and declination of each image provide 2 constraints for each image, but one member does not add constraints because the actual source position of all images is unknown.

[^6]: For cluster-scale lenses, the lens position is kept as a free parameter, although often the coordinates of the BCG may be assumed to represent the cluster center.

[^7]: For fields where the mode solution is also provide, we use the higher $\chi^2$ value of the two.

[^8]: It is not advisable here to measure sizes based on the reconstruction of individual lensed images, as some images may not include the full source-plane structure. As an example, for galaxies where only a small region crosses into a quadruply-imaged region, two of the four images will contain only this region alone (while the remaining two images will show the full galaxy).

[^9]: (cite: Murphy:2017aa) additionally demonstrate that the effective radius of marginally resolved sources can be connected to the deconvolved major axis of an inclined disk as $\theta_{\rm maj} \approx 2.430 \times R_{\rm e}$.

[^10]: We note that some were since identified independently by (cite: Trombetti:2021ab).

[^11]: These values are chosen in line with the characteristic mass (and $1\sigma$ confidence interval) of (cite: Leslie:2020aa) that contributes most to the cosmic SFR density at $z=2.5$. Moreover, abundance matching by (cite: Behroozi:2013aa) suggests an average upper stellar mass limit of $5\times10^{11}~M_\odot$ within halos of mass $10^{12}-10^{13}~M_\odot$.

[^12]: We note that the next highest redshift bin, $1.3 < z \le 1.75$, follows effectively the same relation, but where the vertical offset is 1.1 instead of 1.2.

[^13]: (cite: Harrington:2021aa) tested this assumption with masses derived from large velocity gradient (LVG; (cite: Goldreich:1974aa; Scoville:1974aa)) radiative transfer models, finding that the single-band estimation can systematically over-predict mass (see also (cite: Forster-Schreiber:2018aa; Liu:2019ae)).

</paper>

Write the methods card for this paper.