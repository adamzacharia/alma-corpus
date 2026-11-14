# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1000..235K\sonnetcc\reply.txt

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
 "bibcode": "2026ApJ..1000..235K",
 "title": "Forecasting the Observable Rates of Gravitationally Lensed Supernovae for the PASSAGES Dusty Starbursts",
 "year": 2026,
 "journal": "The Astrophysical Journal",
 "first_author": "Kamieneski, Patrick S.",
 "n_authors": 22,
 "arxiv_id": "2510.00923",
 "doi": "10.3847/1538-4357/ae459e",
 "alma_projects_linked_by_archive": [
  "2015.1.01518.S",
  "2016.1.00048.S",
  "2017.1.01214.S",
  "2019.1.01636.S"
 ]
}
```

Paper text:
<paper>
# Forecasting the Observable Rates of Gravitationally Lensed Supernovae for the PASSAGES Dusty Starbursts

## Abstract

More than 60 years have passed since the first formal suggestion to use strongly-lensed supernovae to measure the expansion rate of the Universe through time-delay cosmography.

Yet, fewer than 10 such objects have ever been discovered.

We consider

the merits of a targeted strategy focused on lensed hyperluminous infrared galaxies among the most rapidly star-forming galaxies known in the Universe.

With star formation rates (SFRs) $\sim {200 - 6000}~{\rm M}_\odot~{\rm yr}^{-1}$, the $\sim 30$ objects in the Planck All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts (PASSAGES) are excellent candidates for a case study, in particular, and have already led to the discovery of the multiply-imaged SN H0pe.

Considering their lens model-corrected SFRs,

we estimate their intrinsic supernova rates to be an extraordinary ${1.8 - 65}~{\rm yr}^{-1}$ (core-collapse) and ${0.2 - 6.4}~{\rm yr}^{-1}$ (Type Ia).

Moreover, these massive starbursts typically have star-forming companions which are unaccounted for in this tally. We demonstrate a strong correlation between Einstein radius and typical time delays, with cluster lenses often exceeding several months (and therefore most favorable for high-precision $H_0$ inferences).

A multi-visit monitoring campaign with a sensitive infrared telescope (namely, JWST) is necessary to mitigate dust attenuation.

Still, a porous interstellar medium and clumpy star formation in these extreme galaxies might produce favorable conditions for detecting supernovae as transient point sources.

Targeted campaigns of known lensed galaxies to discover new lensed supernovae can greatly complement wide-area cadenced surveys.

Increasing the sample size helps to realize the potential of supernova time-delay cosmography to elucidate the Hubble tension

through a single-step measurement,

independent of other $H_0$ techniques.

show\]pkamiene@asu.edu

# Introduction

Gravitationally lensed supernovae (glSNe) are invaluable cosmological tools that are finally now being discovered and leveraged

to make unique, one-step measurements of the Hubble constant, $H_0$, describing the expansion rate of the Universe (cite: Suyu:2024aa).

For multiply-imaged lensed objects, the arrival of the different images is staggered in time due to $i)$ the difference in path lengths along the different null geodesics; and $ii)$ the Shapiro effect (cite: Shapiro:1964aa), by which the light rays experience disparate amounts of time dilation from the differing gravitational potential along their paths.

The magnitude of this effect for galaxies at cosmological distancestypically of order hours to decadesis usually far too small to be detectable, given the timescales of Myr for galaxy-scale variations.

However, with rapidly varying or transient signals, like from quasars or supernovae, it is possible to capture and measure these lensing-induced time delays through light curve monitoring.

Through a technique now known as time-delay (TD) cosmography first introduced by (cite: Refsdal:1964aa) (see also reviews by (cite: Blandford:1992aa; Treu:2016aa; Treu:2022ac; Birrer:2024aa)),

these delays may be inverted to infer

distances within the Hubble flow, and therefore $H_0$.

This owes to the dependence of the time delays on a ratio of 3 angular-diameter distances (from the observer to the lens, from the observer to the source, and from the lens to the source; (cite: Schneider:1985aa)), which in turn is proportional to $H_0^{-1}$ (with minimal dependence on other cosmological parameters).

The “Hubble tension" between calculations of the Hubble constant $H_0$ still endures, despite an extraordinary number of measurements that have been put forth in the last two decades (see recent review by (cite: Verde:2024aa)).

The primary conflict arises from the smaller value of $H_0 =  67.4 \pm 0.5~{\rm km~ s}^{-1} ~{\rm Mpc}^{-1}$ (cite: Planck-Collaboration:2020aa) inferred from the cosmic microwave background (CMB) within the standard $\Lambda$CDM model (also (cite: Aiola:2020aa; Louis:2025aa)), relative to the larger values found from the local Universe (e.g., $H_0 = 73.0 \pm 1.0~{\rm km~ s}^{-1} ~{\rm Mpc}^{-1}$ from SH0ES; (cite: Riess:2022aa)).

The latter measurements are predominantly determined through calibration of a distance ladder on cosmological scales, making use of indicators such as Type Ia supernovae in combination with, e.g., $i)$ Cepheid variable stars (e.g., (cite: Riess:2022aa)), $ii)$ the tip of the red giant branch (TRGB; e.g., (cite: Freedman:2019aa; Anand:2024aa)), or $iii)$ the J-Region Asymptotic Giant Branch (JAGB; e.g., (cite: Lee:2021aa; Freedman:2025aa)).

Given the manifold challenges in this calibration ((cite: Mortsell:2022aa; Mortsell:2022ab)),

there is a drastic need for independent and orthogonal measurements of $H_0$ that do not suffer from the same systematics.

One such example is the Megamaser Cosmology Project ((cite: Reid:2009aa; Reid:2013aa; Pesce:2020aa)), which enables a “single-rung" geometric distance inference through high-precision mapping of circumnuclear H$_2$O masers originating from accretion disks around active galactic nuclei (AGN) in low-$z$ galaxies.

Another, of course, is TD cosmography, which is capable of yielding a single-rung measurement well into the Hubble flow

without hinging on the possible pitfalls from the usual distance ladder methods[^1].

TD cosmography has perhaps matured more quickly for lensed quasars, which are variable but offer the benefit of persistence that supernovae lack (cite: Wong:2020aa; Birrer:2020ab; Birrer:2024aa).

Over 300 lensed quasars have been identified, most with image separations of only a few arcseconds and with time delays typically less than one year, although some (e.g., (cite: Fohlmeister:2007aa; Fohlmeister:2008aa; Dahle:2015aa; Munoz:2022aa; Napier:2023aa)) have measured time delays using wide-separation cluster-lensed quasars (which have some advantages over galaxy-scale lenses and their systematic uncertainties; (cite: Kochanek:2020ab)).

However, inferring time delays from quasars requires long-term monitoring (of order 10 years) for accurate measurements (cite: Courbin:2005aa; Bonvin:2017aa), and can be plagued by microlensing (cite: Irwin:1989aa; Witt:1995ab; Schechter:2003aa; Vernardos:2024aa),

degeneracies and systematics in lens models ((cite: Keeton:2000aa; Koopmans:2003aa)),

and the well-known mass-sheet and mass-slope degeneracies ((cite: Falco:1985aa; Gorenstein:1988aa; Wambsganss:1994aa; Kochanek:2002aa; Schneider:2013aa)).

While some of these challenges also affect TD cosmography with supernovae, this approach has some distinct advantages. Their rapid and more predictable variation in brightness means that time delays can be measured with much shorter monitoring campaignseven as little as a few hours of spectroscopy (cite: Chen:2024ab)and with a level of precision and accuracy that is actually more affected by photometric uncertainties than by microlensing (e.g. (cite: Pierel:2019aa; Huber:2022aa; Pierel:2024aa)).

Perhaps the most important systematic plaguing the time-delay cosmography approach for supernovae at present is scarcity.

Supernovae are inherently rare events$\lesssim 1\%$ of all stars will end their lifetimes in core-collapse supernovas (CCSNe).

As their duration above a survey’s sensitivity limits is short-lived, especially at $z > 1$, their discovery essentially requires

a not insignificant amount of luck.

Strong gravitational lensing in the regime of producing multiple images is similarly quite rare (cite: Treu:2010aa).

While the lensing optical depth (probability of being lensed above a certain magnification threshold or lensed into more than one image) increases monotonically with source-plane redshift, this largely asymptotes above $z\gtrsim 2$ (e.g., (cite: Hilbert:2007aa; Hilbert:2008aa; Robertson:2020ac)).

As a result, barely more than a handful of other multiply-imaged lensed SNe have been discovered in the last decade since SN Refsdal was first identified behind the MACS J1149.6+2223 galaxy cluster ((cite: Kelly:2015aa; Kelly:2016aa; Grillo:2018aa); $H_0$ measurements in (cite: Kelly:2023ab; Grillo:2024aa)).

Since then, three other glSNe suitable for TD cosmography have been discovered: SN H0pe behind the PLCK G165.7+67.0 cluster (cite: Frye:2023ab; Frye:2024aa), and the pair of SN Requiem (cite: Rodney:2021ab) and SN Encore (cite: Pierel:2024ab), both within the same massive host galaxy lensed by MACS J0138.0-2155 and separated by 2.5 years in the galaxy’s rest frame.

The analysis of SN H0pe, the first confirmed glSN Ia used for TD cosmography, recently produced a new $H_0$ measurement at $\sim 10\%$ precision (cite: Pascale:2025aa).

This work also introduced a new weighting scheme for the seven independently-constructed lens models according to their ability to accurately predict observables like magnifications, made possible by H0pe’s nature as a standardizable candle.

The first $H_0$ result from SN Encore is imminent ((cite: Ertl:2025aa); S. Suyu et al., in prep.; J. D. R. Pierel et al., in prep.), and now there is also hope for a precise measurement from SN Requiem’s return a decade later in 2026-2027 (HST program GO-18069).

Upcoming wide-area surveys like the Vera C. Rubin Observatory’s Legacy Survey of Space and Time (LSST; (cite: LSST-Science-Collaboration:2009aa)) promise to reveal $\sim 50 - 100$ glSNe yr$^{-1}$ (cite: Arendse:2024ab; Bag:2024aa; Melo:2025aa; Sainz-de-Murieta:2024aa),

but not all of these will be discovered sufficiently early to follow up with light curve monitoring for the purposes of TD cosmography.

Also, many of the glSNe behind galaxy-scale deflectors will have time delays too short to yield meaningful precision on $H_0$, as in the case of iPTF16geu ($z=0.409$; (cite: Goobar:2017aa)).

Moreover, in the pessimistic scenario, currently active facilities like the Zwicky Transient Facility (ZTF; (cite: Bellm:2014aa)) were expected to yield at least one glSN per year,

but only one was identified in four years (SN Zwicky at $z=0.354$; (cite: Goobar:2023aa; Pierel:2023aa)), with few other compelling candidates ((cite: Magee:2023aa; Sagues-Carracedo:2024aa); see also (cite: Craig:2024aa)).

Still, the next decade is likely to see TD cosmography with glSNe mature more fully and reach a competitive precision on $H_0$, closer to 1% than 10% (cite: Treu:2022ac).

What, then, is the best strategy at present for discovering “live" glSNe[^2]?

One answer might come from remarking that some of the recent discoveries have been identified behind well-studied lensing clusters. These include two of the famous Hubble Frontier Fields: SN Refsdal behind MACS J1149.6+2223 (cite: Kelly:2015aa) and a $z\approx 3$ CCSN behind Abell 370 (cite: Chen:2022ag).

There is undoubtedly an observational bias here, given the attention these fields receive, resulting in a more well-sampled cadence, and the presence of numerous lens models to identify multiple imaging (cite: Bronikowski:2025aa).

Yet, these massive lensing clusters also provide sizable magnification for a large number of background sources (e.g., (cite: Gal-Yam:2002aa; Stanishev:2009aa; Petrushevska:2016aa; Petrushevska:2018ab; Petrushevska:2018aa; Petrushevska:2020aa)).

However, SN H0pe, SN Requiem, and SN Encore were all identified

within high-mass host galaxies lensed by less massive,

previously lesser-known clusters.

These discoveries were facilitated not necessarily by the extraordinary nature of the foreground, but more so of the background lensed host galaxies.

A targeted search for glSNe in known lensed galaxies that are very massive or have a high SFR (or both) is not an entirely novel idea.

(cite: Shu:2018ab) estimated that monitoring a sample of $>100$ galaxy-scale lensed star-forming galaxies would yield rates of $\sim 3$ combined CCSN and SN Ia events per year (cite: Shu:2021ab),

reaching a greater efficiency than a blind search.

A targeted strategy also provides greater confidence that any discovered SNe are in fact lensed (see also (cite: Holwerda:2021aa)).

Here, we modify the approach to encompass a much smaller sample, but with commensurately larger rates of star formation.

There is some difficulty in identifying sufficient numbers of starburst galaxies (with high intrinsic rates of supernovae) that are lensed into multiple images.

One possible approach is to monitor samples of known lensed dusty star-forming galaxies (DSFGs),

also referred to as submillimeter galaxies (SMGs)

which now number in the hundreds (cite: Giulietti:2024ab),

as these objects are inferred to form stars at prodigious rates of $300 - 1000 ~ M_\odot ~{\rm yr}^{-1}$ (or even greater).

The prevailing selection method for this population is unique, relying essentially on submillimeter flux alone (cite: Blain:1996aa; Perrotta:2002aa; Negrello:2010aa; Negrello:2017aa), as opposed to methods that identify distorted lensing morphologies or peaks in foreground mass density or Sunyaev-Zel’dovich effect signal.

As an application of this tactic,

we examine in particular

the set of lensed DSFGs identified from *Planck*, which is perhaps most well suited for this experiment due to its all-sky coverage.

For now, we consider the $\sim 30$ members of the *Planck* All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts (PASSAGES; (cite: Harrington:2016aa; Berman:2022aa; Kamieneski:2024aa)), some of which were also identified independently through *Herschel* follow-up (cite: Canameras:2015aa; Planck-Collaboration:2015aa).

Of these, 21 objects (summarized in Table [1](#tab:computations)) have the information necessary to compute expected glSN rates (§[2.4](#sec:f_unobs) and [3.1](#sec:RCC)).

(cite: Kamieneski:2024aa) determined that the median de-lensed (i.e. intrinsic) infrared luminosity for PASSAGES exceeded $10^{13}~L_\odot$, qualifying them as hyper-luminous infrared galaxies (HyLIRGs).

Nonetheless, the dust geometry of such extreme HyLIRGs remains quite uncertain at high-$z$. Any supernovae are likely to be attenuated by dust in even the best-case scenario,

so near-IR sensitivity is paramount.

HyLIRGs such as these are often signposts of significant over-dense regions (e.g., (cite: Foo:2025aa)).

While we consider

primarily the contribution to the supernova rate from the primary starburst galaxies, there is a high likelihood of other star-forming objects at the same redshift that might also fall into the strongly lensed portion of the source plane, further boosting the chances of identifying lensed transients in these fields.

This is also borne out in part with the discovery of SN H0pe behind the lensing cluster G165.7+67.0, which was itself identified through its amplification of one of the PASSAGES DSFGs.

Initial JWST/NIRCam imaging of the field through the Prime Extragalactic Areas for Reionization and Lensing Science program (cite: Windhorst:2023aa) revealed the Type Ia supernova not within the giant arc of lensed DSFGs, but in a highly-magnified arc nearby in projection. Both this host galaxy and the DSFGs were found to be members of respective photometric-redshift overdensities at $z=1.78$ and $z=2.24$ (cite: Frye:2024aa).

This work is organized as follows: in Section [2](#sec:methods), we detail our novel approach to deriving forecasts for the intrinsic and observer-frame rates of supernovae in HyLIRGs, using the PASSAGES fields as an example.

In Section [3](#sec:results), we discuss our inference of star formation rates (both obscured and unobscured modes), lensing multiplicities, and the core-collapse and degenerate white dwarf supernova rates that result from these inferences.

We also examine the expected typical time delays and draw a connection to the angular separation between images.

In Section [4](#sec:summary), we summarize our findings and reflect on the feasibility of our proposed approach in making a meaningful contribution to the rather saturated industry of deriving $H_0$ constraints.

Throughout, we adopt a fiducial $\Lambda$CDM concordance cosmology of $\Omega_m = 0.3$, $\Omega_\Lambda = 0.7$, and $H_0 = 70~{\rm km~s}^{-1}~{\rm Mpc}^{-1}$.

# Observations & Methods

## Case study sample selection: PASSAGES

In this work, we aim to forecast the expected rates of supernovae from strongly-lensed DSFGs at $z>1$.

Lensed DSFGs are efficiently selected through their submillimeter flux owing to a steep drop-off in number counts (cite: Blain:1996aa), such that an extragalactic source brighter than 100 mJy at 500 $\mu$m is $\gtrsim 30$ times more likely to be lensed than unlensed (cite: Negrello:2017aa).

However, they are still rare objects, with a modeled all-sky number density of $0.09 \pm 0.05~{\rm deg}^{-2}$ for $S_{500\mu{\rm m}} > 80$ mJy, while observations suggest up to $\sim 0.3~{\rm deg}^{-2}$ ((cite: Sedgwick:2025aa), and references therein including (cite: Negrello:2010aa; Bussmann:2013aa; Wardlow:2013aa; Negrello:2014aa; Negrello:2017aa; Bakx:2018aa; Urquhart:2022ab; Borsato:2024aa)).

This model predicts $3600 \pm 1800$ such sources to exist in the entire sky (increasing by a factor of $\sim 40$ if the threshold is lowered by a factor of 10; (cite: Bakx:2024aa; Sedgwick:2025aa)), but so far only a few hundred such objects have been uncovered (e.g. (cite: Giulietti:2024ab)).

*Euclid*’s Wide Survey (cite: Euclid-Collaboration:2022ab) is expected to be sensitive to several thousand.

For now, while *Planck*’s surveys reach shallower depths than *Herschel*, its wide-area coverage has been an asset for identifying the very brightest lensed DSFGs in the sky (cite: Trombetti:2021ab).

As discussed by (cite: Kamieneski:2024aa), there is a complex balance between their intrinsic luminosities and their magnifications: HyLIRGs tend to have larger sizes to match their higher luminosities (in line with the Eddington limit; (cite: Kamieneski:2024ab)), while size bias leads to more strongly-magnified objects correlating with more compact sizes (cite: Hezaveh:2012aa). Together, this means that candidates with apparent luminosities $\mu_{\rm IR}{\rm L}_{\rm IR} \gtrsim 10^{14}~ L_\odot$ tend to still have intrinsic ${\rm L}_{\rm IR} \gtrsim 10^{12.5}~ L_\odot$.

For this reason, the greater submillimeter fluxes of *Planck*-identified lensed DSFGs are not simply the result of higher magnifications alone. They are thus among the best candidates for high rates of glSNe given their high SFRs.

Moreover, their lower median redshift than lensed DSFGs identified in the millimeter regime (e.g., with the South Pole Telescope; (cite: Weiss:2013aa)) lends well to greater ease in detecting glSNe in the observed-frame near-IR.

## Determining the expected value of image multiplicity

A galaxy that crosses the caustic network will have different parts of the source plane lensed into varying numbers of multiple images.

In the canonical lensing example of a singular isothermal ellipsoid, an astroid tangential caustic encloses a region with an image multiplicity of 4 (excluding demagnified images), whereas the region between the tangential caustic and the elliptical radial caustic is lensed into 2 images, and structures exterior to the radial caustic are weakly lensed into only a single image.

For cluster-scale lenses, which have larger source-plane areas inside the caustics, it is more likely for most of a galaxy’s light to be contained within a region with constant image multiplicity.

On the other hand, galaxy-scale lenses have much tighter caustic loci, so galaxies can easily cross caustics and have two (or even more) different image multiplicities of the source.

The lensing multiplicity of a galaxy has a direct bearing on the average rate of SNe that can be observed on Earth.

To account for this, we introduce the concept of *effective multiplicity*, $\mathcal{N}_{\rm eff}$, which is the average multiplicity weighted by the distribution of star formation. We define it as $$\begin{equation}
\mathcal{N}_{\rm eff} \equiv \sum_n \bigg[ n \cdot \frac{{\rm SFR}_{n}}{{\rm SFR}} \bigg]
\label{eqn:Neff}
\end{equation}$$ for the different multiplicities $n$, where SFR$_n$ is the total star formation rate within the region of multiplicity $n$.

This calculation is illustrated for a singular isothermal ellipsoid lens (with a large axis ratio) in a cartoon in Fig. [1](#fig:Neff).

$\mathcal{N}_{\rm eff}$ can also be functionally expressed as a pixel-based summation: $$\begin{equation}
\mathcal{N}_{\rm eff} \equiv \frac{\sum_{i,j} N_{i,j} {\rm SFR}_{i,j}}{\sum_{i,j} {\rm SFR}_{i,j}}
\label{eqn:Neff2}
\end{equation}$$ where SFR$_{i,j}$ and $N_{i,j}$ are the star formation rate and multiplicity, respectively, at pixel $(i,j)$.

![](effective_multiplicity_sketch.png)

## ALMA 1mm continuum and VLA 6 GHz

To infer a map of SFR to compute $\mathcal{N}_{\rm eff}$ with the information available for the majority of PASSAGES, we rely on the 1mm dust continuum observed with the Atacama Large Millimeter/submillimeter Array (ALMA), by which we apportion the total IR SED-derived SFR (primarily from (cite: Harrington:2016aa; Berman:2022aa)).

For northern-declination sources not covered in these observations, we instead use 6 GHz (5 cm) continuum imaging from the *Karl G. Jansky* Very Large Array in A-configuration, with angular resolutions relatively close to the ALMA images. The 6 GHz images are largely correlated with the dust continuum through the radio-FIR correlation (e.g., (cite: Condon:1992aa)).

These observations are described in detail in Sections 2.4 and 2.5 of (cite: Kamieneski:2024aa), with images shown in their Figure 2.

We use these observations to map the source-plane spatial distribution of ${\rm SFR}_{\rm IR}$ (as inferred from unresolved far-IR photometry, the source of which is specified for each target in Table [1](#tab:computations)).

Since the star formation is likely dominated by the obscured mode probed by SFR$_{\rm IR}$, the distribution $\Sigma_{\rm SFR_{\rm IR}}$ is our best estimate of the 2d probability density function of core-collapse supernovae (e.g., (cite: Miluzio:2013aa)). While slightly less direct, this is also likely to closely match the spatial distribution of Type Ia supernovae, as well (especially if one assumes that $\Sigma_{\rm SFR}$ correlates with the distribution of stellar mass, $\Sigma_\star$; e.g., (cite: Baker:2022aa)).

Of course, the *observed* distribution of supernovae is more complex, and depends on dust geometry, but for the purpose of computing $\mathcal{N}_{\rm eff}$, $\Sigma_{\rm SFR_{\rm IR}}$ should suffice.

Nonetheless, given the highly stochastic nature of supernovae, even for galaxies with very high SFRs, and imperfections in the lens models, we adopt a conservative fractional uncertainty[^3] of 20% on $\mathcal{N}_{\rm eff}$.

The achieved resolutions for the ALMA and VLA observations ranged from $\theta \approx 0.4 - 0.8\ensuremath{''}$ and $\theta \approx 0.3 - 0.7\ensuremath{''}$, respectively.

While higher-resolution observations (e.g., spatially-resolved SED fitting with JWST) would improve the fidelity of $\mathcal{N}_{\rm eff}$, the location of the caustic network from lens models and systematics of SED-fitting dominate the uncertainty at present.

There is some concern that heavily dust-obscured active galactic nuclei (AGN) might contribute in the radio (cite: Donley:2005aa; Del-Moro:2013aa; Delvecchio:2017aa), thus biasing the calculation of $\mathcal{N}_{\rm eff}$.

However, (cite: Kamieneski:2024aa) found that the PASSAGES DSFGs did not have obvious evidence of radio-loud AGN manifesting as an excess in spatially-integrated radio continuum relative to FIR, suggesting that this bias is not likely to have a sizable effect.

## Estimating the obscured & unobscured SFR

### The situation at low-$z$ vs. $z>2$

CCSNe have been discovered successfully in low-$z$ luminous infrared galaxies (LIRGs) in the near-IR within projected radii $< 1$ kpc ((cite: Mannucci:2003aa; Mattila:2007aa; Kankare:2008aa; Kankare:2012aa; Miluzio:2013aa; Kool:2018aa; Jencson:2019aa; Fox:2021ab; Kankare:2021aa; Perez-Torres:2021aa)). These include some radio supernovae and supernova remnants found through very long baseline interferometry (e.g., (cite: Marti-Vidal:2007aa; Perez-Torres:2009aa; Bondi:2012aa; Varenius:2019aa)).

On the other hand, some campaigns have yielded zero, or at least

drastically fewer than expected, detected events for starbursts and ultra-luminous infrared galaxies (ULIRGs), including (cite: Cresci:2007aa) with *HST*/NICMOS, or (cite: Vaisanen:2008aa) with adaptive optics-assisted VLT imaging.

(cite: Mantynen:2025aa) recently found that $\approx$90% of CCSNe in local LIRGs might be missed if attenuations only up to $A_V < 3$ mag are detectable.

Even if hypothetically sensitive to extremely high values of $A_V \gtrsim 40$, the authors obtain an undetectable fraction $\gtrsim$50% owing to the concentrated distribution of dust and star formation in local LIRGs.

(cite: Fox:2021ab) emphasized the importance of a stable, symmetric, high-resolution PSF in the near-IR (as achieved with space-based facilities) in order to combat this high concentration.

This might paint a dire picture for executing successful campaigns at high-$z$, although clever workarounds are possible. For example, (cite: Yan:2018aa) demonstrated that the presence of SNe may be revealed through variability in the integrated near-IR light of a galaxy (at the time with *Spitzer*).

However, there also appear to be key distinctions between the typical structures of high-$z$ HyLIRGs and the LIRGs/ULIRGs in the low-$z$ Universe.

The typical star-dust geometry of DSFGs and starburst galaxies remains a matter of ongoing research, which of course has implications for the detectability of supernovae.

In particular, the presence of unobscured UV-bright sightlines in DSFGs may be responsible for bluer UV slopes $\beta_{\rm UV}$, resulting in the observed deviation from the IRX-$\beta$ relation (cite: Meurer:1999aa) where IRX$\equiv L_{\rm IR} / L_{\rm UV}$ is the IR excess (e.g., (cite: Cortese:2006ab; Boquien:2009aa; Casey:2014ab; Faisst:2017aa; Safarzadeh:2017ab; Narayanan:2018ab; Liang:2021aa)).

In essence, the exceptional rate of supernovae occurring per year in each of the PASSAGES galaxies (Table [1](#tab:computations)) is likely to result in a very porous ISM,

especially considering the groundwork laid by pre-supernova feedback (cite: Lucas:2020aa; Chevance:2022ab; Watkins:2023aa).

Supernovae are likely to occur within an inhomogeneous medium, and further contribute to this through compression of swept-up shells and rarefied bubbles (e.g., (cite: Clarke:2002aa; Kim:2015aa).

This ISM structure, in turn, favors the ability to observe supernovae, even in dusty environments.

Local ULIRGs often host extremely concentrated starburst regions (although as (cite: McQuinn:2012aa) point out, this may be partially a selection bias).

This high concentration reaches an extreme with compact obscured nuclei, or CONs (which have sizes of $10-100$ pc and very high attenuations of $A_V \gtrsim 10$; (cite: Sakamoto:2013aa; Aalto:2015aa; Falstad:2021aa)).

At Cosmic Noon ($z\sim 1 - 3$), their more luminous counterparts sustain high rates of star formation over the scale of several kpc (cite: Rujopakarn:2011aa; Hodge:2016aa; Hodge:2019aa; Harrington:2021aa; Kamieneski:2024aa; Kamieneski:2024ac; Mitsuhashi:2024aa; Polletta:2024ab), often in clumps resulting from gravitational instabilities in gas-rich disks (cite: Immeli:2004aa; Tadaki:2018aa; Faisst:2025aa; Fujimoto:2024aa; Liu:2024ae; Kalita:2025ac) that are continually replenished through accretion (cite: Bournaud:2007aa; Dekel:2009aa).

Also, the high rates of star formation likely lend well to an increased rate of star cluster formation, and thus a better sampling of the high-mass end of the cluster mass function.

For example, super star clusters (SSCs) are preferentially found in intense starburst regions, as exemplified by M82 and the Antennae Galaxies (e.g., (cite: Smith:2001aa; Mengel:2002aa; de-Grijs:2003aa; Whitmore:2010aa; Linden:2017aa; Emig:2020aa; Levy:2024aa)).

If much of the star formation of DSFGs is concentrated in SSCs, which are progenitors of massive globular clusters, then their strong stellar feedback may contribute to clearing sightlines that both allows for Lyman continuum (LyC) leakage (e.g., (cite: Bik:2018aa; Pascale:2023ab; Ji:2025aa)) and the escape of less-attenuated optical light from SNe (e.g., (cite: Leitet:2013aa; Roy:2024ae)).

### Adopting a fraction of unobscured SFR

H$\alpha$ SFRs are typically significantly less than those derived from the infrared.

This discrepancy is primarily resolved after applying a Balmer decrement extinction correction to the H$\alpha$-derived value (cite: Kewley:2002ab; Takata:2006aa; Dominguez-Sanchez:2012aa; Timmons:2015aa; Puglisi:2016aa; Liu:2024ae), although not in all cases ((cite: Chen:2020aa)).

For the (cite: Calzetti:2000aa) attenuation law, SFR$_{\rm H\alpha}$ is corrected as

$$\begin{equation}
{\rm SFR}_{\rm H\alpha, corr} = {\rm SFR}_{\rm H\alpha} \cdot 10^{0.4 \cdot E(B-V)_{\rm neb} \cdot k'({\rm H}\alpha)}
\end{equation}$$ where $k'(0.656 \mu {\rm m}) \approx 3.325$

and $E(B-V)_{\rm neb}$ is the color excess inferred from emission lines,

$$\begin{equation}
    E(B-V)_{\rm neb} 
    \approx 1.97 \cdot {\rm log}_{10}\bigg[\frac{L_{\rm H\alpha} / L_{\rm H\beta}}{2.86}\bigg]
\end{equation}$$ for case B recombination (cite: Osterbrock:2006aa).

Inherently, the strong attenuation of DSFGs has made it difficult to recover multiple Balmer lines.

In a composite spectrum of 31 DSFGs in the COSMOS field, (cite: Casey:2017aa) found a median Balmer decrement of $21.0 \pm 2.4$, yielding $E(B-V)= 1.7 \pm 0.1$ or $A_V = 6.9 \pm 1.4$ (using $R_V = 4.05 \pm 0.80$). This is higher than observed even for local ULIRGs on global scales (e.g., (cite: Wild:2011aa)).

More recently, in a sample of typical DSFGs at $z\sim 2-3$, (cite: Cooper:2025aa) found consistency with the shape of the (cite: Calzetti:2000aa) attenuation curve, and $A_V \sim 3 - 4$, through combination of Balmer and Paschen lines obtained with JWST/NIRSpec.

As some star formation is likely to be hosted in regions with dust obscuration strong enough such that no H$\alpha$ emission would be detectable, these Balmer decrements are biased low (cite: Puglisi:2017aa).

The extinction-corrected ${\rm SFR}_{\rm H \alpha}$ estimates are likely to give a more realistic assessment of the observable rates of supernovae, however. Therefore, in our analysis, we introduce an unobscured fraction $f_{\rm unobsc} \equiv {\rm SFR}_{\rm unobsc} / {\rm SFR}_{\rm IR} (\sim {\rm SFR}_{\rm H\alpha,corr} / {\rm SFR}_{\rm IR})$.

For example, (cite: Olivares:2016aa) found this fraction to be $<30\%$ in $z\sim 2$ SMGs (an upper limit since their H$\alpha$ SFRs are not corrected for extinction).

In other words, the discrepancy between the extinction-corrected SFR$_{\rm H\alpha, corr}$ and SFR$_{\rm IR}$ is a quantification of how much star formation is hosted in regions of extreme attenuation (from which neither H$\beta$ nor H$\alpha$ may be detected).

For the PASSAGES sample itself, two members already have measurements of the Balmer decrement.

For the pair of DSFGs PJ1127+42 at $z=2.24$ (comprising Arcs 1abc, 3abc, 4abc, and 6abc lensed by the G165.7+67.0 cluster), (cite: Frye:2024aa) found a value of $E(B-V) = 0.85 \pm 0.25$ through NIRSpec observations (corresponding to a Balmer decrement of $7.7 \pm 2.3$ and $A_V = 3.4 \pm 1.2$).

This yields a correction of log$_{10}$(SFR$_{\rm H\alpha} / {\rm SFR}_{\rm H\alpha,corr}) = -1.1 \pm 0.3$, such that the demagnified ${\rm SFR}_{\rm H\alpha,corr} \approx 100^{+200}_{-70} ~ M_\odot ~{\rm yr}^{-1}$ for Arc 1 only.

Given that ${\rm SFR}_{\rm IR} = 320 \pm 70 ~ M_\odot ~{\rm yr}^{-1}$ for the same object (cite: Kamieneski:2024ac), this gives $f_{\rm unobsc} \approx 31\%$.

We adopt this fraction for the entire arc complex (Arcs 1, 3, 4, and 6, per notation from (cite: Frye:2019aa)), which all lies at $z\approx 2.24$ (cite: Canameras:2018aa; Kamieneski:2024ac).

Similarly, for PJ0116-24 ($z=2.13$), (cite: Liu:2024ae) derived a color excess through Balmer decrement of $E(B-V) = 0.95 \pm 0.13$ with VLT/ERIS observations (Balmer decrement $8.7 \pm  1.3$; $A_V = 3.9 \pm 0.9$),

suggesting log$_{10}$(SFR$_{\rm H\alpha} / {\rm SFR}_{\rm H\alpha,corr}) = -1.3 \pm 0.2$ and ${\rm SFR}_{\rm H\alpha,corr} = 470 \pm 60~M_\odot ~{\rm yr}^{-1}$ and $f_{\rm unobsc} \approx 32\%$.

In this work, for objects without these Balmer decrement measurements at present, we adopt a range of $f_{\rm unobsc} = 20\pm 10\%$ in Table [1](#tab:computations) (see also, e.g., (cite: Swinbank:2004aa; Chen:2020aa; Cheng:2020ac)).

This might at first seem to run counter to the results of (cite: Whitaker:2017aa) that $f_{\rm obsc} \equiv {\rm SFR}_{\rm IR} / {\rm SFR}_{\rm UV+IR}$ increases continually for higher SFRs and stellar masses (exceeding 90% for massive galaxies ${\rm log}(M/M_\odot)>10.5$)[^4].

Higher dust obscuration may be due to elevated surface densities of both star formation and gas (which are themselves correlated; (cite: Schmidt:1959aa; Kennicutt:1998ac)).

However, $\Sigma_{\rm SFR}$ does not seem to increase strongly with $L_{\rm FIR}$. The size-luminosity relation found by (cite: Fujimoto:2017aa) for $11 \lesssim {\rm log}(L_{\rm FIR} / L_\odot) \lesssim 13$, $R_e \propto L_{\rm FIR}^{0.28}$, implies a weak dependence of $\Sigma_{\rm SFR} \propto \Sigma_{\rm FIR} \propto L_{\rm FIR}^{0.44}$.

Empirically, HyLIRGs appear to remain at or below $\Sigma_{\rm SFR} \approx 100~M_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2}$, with a similar distribution as ULIRGs with luminosities a decade lower (e.g., (cite: Hodge:2019aa; Bakx:2024ad; Kamieneski:2024aa)), suggesting that $\Sigma_{\rm SFR}$ may even saturate.

If this property plays an important role in the (cite: Whitaker:2017aa) relation, then the obscured fraction may saturate, as well.

Drawing again a parallel to the escape of Lyman continuum, this fraction of 20% has some precedent. For star-forming galaxies (SFGs) in UVCANDELS ($2.5 < z < 3.0$), (cite: Wang:2025an) reported an upper limit in the absolute Lyman continuum escape fraction of $f_{\rm esc} \lesssim 26\%$.

(cite: Smith:2018ac) found that the average absolute $f_{\rm esc}$ for massive SFGs and weak AGN at $z\sim 2.4$ was $\sim 22^{+44}_{-22}\%$ (see also (cite: Smith:2020ab) and (cite: Smith:2024aa), which found $f_{\rm esc} \sim 18\%$ for weak AGN in UVCANDELS).

If stellar and AGN feedback in galaxies at similar redshifts with comparable (or even much lower) SFRs can clear the way for this level of escape of Lyman continuumwhich is much more affected by dust than the light from SNethen it is likely not unreasonable to expect an unobscured fraction of $\sim 20\%$.

While clearly only a fraction of the star formation is visible in the unobscured mode for these objects, we emphasize that their total SFRs are large enough that the absolute unobscured star formation can still be quite substantial.

Moreover, these large color excesses $E(B-V)$ primarily quantify the dust attenuation within the more obscured star-forming regions (e.g., (cite: Wild:2011aa; Price:2014aa; Chen:2020aa)), which (cite: Calzetti:1997ab) found differed as $E(B-V)_{\rm stellar} = 0.44~E(B-V)_{\rm nebular}$.

Deviation from this towards greater color excess for the nebular component appears to correlate with specific SFR (sSFR $\equiv {\rm SFR}/M_\star$), as a greater share of star formation occurs in the obscured mode (cite: Reddy:2015aa), but it also is likely to vary spatially within individual galaxies (e.g., (cite: Robertson:2024aa)).

It is probably not reasonable to expect that DSFGs will have uniformly large dust attenuation of $A_V \sim 4 - 7$, but this remains to be tested more rigorously in larger samples.

It is also worth noting that multi-band JWST (or even HST) imaging enables robust spatially-resolved SED fitting for a wide range of redshifts (e.g., (cite: Abdurrouf:2023aa; Gimenez-Arteaga:2023aa; Kamieneski:2024ac; Liu:2024af; Polletta:2024ab; Akins:2025ab; Harvey:2025ac)), such that the distribution of star formation and dust attenuation can be characterized at sub-kpc scales.

This exercise is crucial to gain an understanding of where supernovae might be attenuated beyond detection limits, and even to better model the light curve of any SNe that are detected.

This can also help account for any contribution to $L_{\rm IR}$ from dust-obscured AGN in PASSAGES galaxies;

(cite: Harrington:2016aa) and (cite: Berman:2022aa) use mid- and far-IR photometry to show that they are star-formation-dominated, but not incontrovertibly.

# Results

## Computing expected intrinsic and observer-frame rates of CCSNe

As the progenitors of core-collapse supernovae are massive stars, the core-collapse rate is linearly related to the rate of star formation,

$$\begin{equation}
\label{eqn:RCC}
R_{\rm CC} = k_{\rm CC} \cdot {\rm SFR}
\end{equation}$$ (e.g., (cite: Madau:1998aa)).

The factor $k_{\rm CC}$ is determined from the initial mass function (IMF), $\phi(M)$, integrated over the mass range of progenitors, typically 8 $M_\odot$ (cite: Smartt:2009aa) to 50 $M_\odot$ (cite: Tsujimoto:1997aa): $$\begin{equation}
k_{\rm CC} = \frac{\int_{8~M_\odot}^{50~M_\odot} \phi(M) {\rm d}M}
{\int_{0.1~M_\odot}^{125~M_\odot} M \cdot \phi(M) {\rm d}M},
\end{equation}$$ where the denominator is limited to the total mass range of 0.1 to 125 $M_\odot$.

As the SFR estimates used in this work are based on a (cite: Kroupa:2001aa) IMF, we adopt a value of $k_{\rm CC}=0.0104~M_\odot^{-1}$.

This is consistent with the optically-thick regime ($\epsilon \approx 1$) of equation 5 of (cite: Mattila:2001aa), $R_{\rm CC}/{\rm yr}^{-1} = 1.1\times 10^{-12} \cdot \epsilon^{-1} \cdot L_{\rm FIR} / L_\odot$,

where $\epsilon$ is the fraction of optical/UV energy absorbed and re-radiated in the FIR.

In comparison, for a (cite: Salpeter:1955aa) IMF[^5], this yields $k_{\rm CC} = 0.0070~M_\odot^{-1}$

(e.g., (cite: Young:2008aa; Melinder:2012aa)).

![](R_CC_vs_z.png)

In Fig. [2](#fig:Rcc), we show the observable rate of CCSN images[^6] $$\begin{equation}
\label{eqn:RCC_obs}
\mathcal{R}_{\rm CC,obs} \equiv f_{\rm unobsc} \cdot R_{\rm CC} \cdot \mathcal{N}_{\rm eff} \cdot (1+z)^{-1}
\end{equation}$$ against redshift, with intrinsic rate $R_{\rm CC}$ determined from the intrinsic (i.e., magnification-corrected) SFR$_{\rm IR}$.

The apparent rates, $\mu$SFR, and magnifications $\mu$ are retrieved from the references given in Table [1](#tab:computations).

Given the dusty nature of these sources, we include $f_{\rm unobsc}$ in the equation *ab initio*, for a more realistic quantification of expected rates.

This does not quantify the fraction of supernovae that could be detectable in any observational campaign, but is more akin to a *maximum* recoverable fraction for what is reasonable with current telescope facilities.

For comparison, (cite: Mantynen:2025aa) recently found that the undetectable fraction of CCSNe in low-$z$ LIRGs for a survey sensitive to $A_V < 16$ mag is $66^{+8.6}_{-14.6}\%$.

Using our formulation, this would suggest $f_{\rm unobsc} = 34^{+14.6}_{-8.6}\%$.

For a much shallower survey down to $A_V < 3$ mag, they found instead an undetectable fraction of $89.7^{+2.6}_{-4.4}\%$.

The large uncertainties in $\mathcal{R}_{\rm CC,obs}$ are the direct result of a combination of $i)$ the broad range chosen for $f_{\rm unobsc}$; $ii)$ inherently large uncertainty in ${\rm SFR}_{\rm IR}$; $iii)$ large uncertainty in magnification $\mu$ for the current lens models; and $iv)$ the conservative fractional uncertainties used for the effective multiplicity $\mathcal{N}_{\rm eff}$.

However, despite this uncertainty, the median $\mathcal{R}_{\rm CC,obs}$ is very high at $\sim 2~{\rm yr}^{-1}$, especially considering the average volumetric rates of $\sim 10^{-4}-10^{-3} ~ {\rm yr}^{-1}~{\rm Mpc}^{-3}$ at Cosmic Noon (cite: Dahlen:2012aa; Strolger:2015aa).

As discussed in §[2.4](#sec:f_unobs), the IR-inferred SFRs are likely the closest to the true SFRs for these dust-obscured galaxies, but they are not necessarily representative of the rates of SNe that one could expect to observe.

We adopt a typical value of $f_{\rm unobsc} = 0.2 \pm 0.1$, following the findings of Balmer decrements for two members of the sample and for other DSFGs in the literature (§[2.4](#sec:f_unobs))[^7].

In §[3.3](#sec:independent), we compare the predicted rates $R_{\rm CC}$ (and the rate of SNe Ia) for PASSAGES with those from other works that also examine candidate samples for SN monitoring, alongside the expected rates for host galaxies of some of the already-discovered glSNe.

In Fig. [2](#fig:Rcc), we observe an increase in $\mathcal{R}_{\rm CC,obs}$ with redshift, which is likely to be driven primarily by the generally higher SFRs in the sample above $z\gtrsim 2$

(whereas $\mathcal{N}_{\rm eff}$ is essentially constant with redshift).

In §[3.3](#sec:independent), we discuss how this compares with the redshift evolution of the cosmic star formation rate density.

## Estimating the rate of Type Ia SNe

As the progenitors of Type Ia supernovae are best understood to be binary systems that include a white dwarf star, the rate of SNe Ia inherently depends in part on the number of evolved lower-mass stars (cite: Ruiter:2025aa).

In turn, since these make up the bulk of the stellar mass of a typical galaxy, it is reasonable to expect that the rate of Type Ia supernovae $R_{\rm Ia}$ would increase with $M_\star$ (either linearly or with some positive power law).

The donor star from which the progenitor white dwarf accretes may itself be another white dwarf

or a main sequence or giant star,

which implies that $R_{\rm Ia}$ should also have some dependence on the SFR, as with $R_{\rm CC}$.

(cite: Mannucci:2005aa) and (cite: Scannapieco:2005aa) found that the observed rate of SNe Ia could be described as a two-component linear combination of SFR and $M_\star$ (see also (cite: Sullivan:2006aa)).

(cite: Smith:2012aa) included a power law for both terms in their bivariate parameterization, favoring $$\begin{eqnarray}
    \label{eqn:RIa}
    R_{\rm Ia} = & &(1.05 \pm 0.16) \times 10^{-10} ~ M_\star^{\ 0.68 \pm 0.01} \nonumber \\
    &+&
    (1.01 \pm 0.09) \times 10^{-3} ~ {\rm SFR}^{1.00 \pm 0.05} \nonumber \\
    
    \approx & &(6.6 \pm 1.0) \times 10^{-4} ~ \bigg(\frac{M_\star}{10^{10}~M_\odot} \bigg)^{0.68 \pm 0.01}\nonumber \\
    &+&
    (1.0 \pm 0.1) \times 10^{-1} ~ \bigg(\frac{\rm SFR}{100~M_\odot~{\rm yr}^{-1}} \bigg)^{1.00 \pm 0.05}
\end{eqnarray}$$

with a “prompt" term and a “delayed" term (although this is for a sample at $z<0.25$).

(cite: Sullivan:2006aa) found that the rate of SNe Ia per unit mass increases with increasing sSFR, which may partly explain the sub-linear dependence on $M_\star$.

A more rigorous treatment would use the star formation history (SFH) convolved with the delay time distribution (DTD; (cite: Madau:1998aa; Mannucci:2006aa)). Instead, the “A+B" parameterization with $M_\star$ and SFR essentially samples the continuous SFH and DTD at two times (cite: Maoz:2014aa).

However, as cautioned by (cite: Andersen:2018aa), this calibration is unconstrained for starburst galaxies with log(sSFR) $> -9$.

While this dependency may in principle also evolve with redshift, several combinations of cosmic star formation histories and delay time distributions tested by (cite: Palicio:2024aa) were able to adequately fit the observed rates of Type Ia supernovae (which are themselves still quite uncertain above $z > 2$).

For our purposes, we consider it justifiable to use the (cite: Smith:2012aa) resultsderived from a wide range of $8 < {\rm log}(M_\star / M_\odot) < 11$to make predictions for our sample.

![](R_Ia_vs_SFR.png)

Unfortunately, the stellar masses for the majority of the PASSAGES DSFGs remain unconstrained, but they are at least very likely to be on the massive end of the stellar mass function (log($M_\star/M_\odot) > 10.5$) given their extreme luminosities and molecular gas masses (cite: Harrington:2021aa).

While most are actually detected in $H$-band imaging with HST (cite: Kamieneski:2024aa),

insufficient observed-frame near-IR data have been collected so far to enable robust SED fitting for most of the background lensed sources[^8], apart from two exceptions.

For the pair of interacting DSFGs behind the G165 cluster, JWST NIRCam and NIRSpec observations yield stellar masses of ${\rm log}_{10} M_\star \approx 10.2$ and 10.3 (cite: Frye:2024aa; Kamieneski:2024ac).

With their IR-inferred SFRs, their sSFRs are both 0.9 dex above the MS, but the likely tidal interaction between the two galaxies might be driving an elevated starburst phase above the rest of the sample.

Also, (cite: Liu:2024ae) found

a large stellar mass of ${\rm log}(M_\star/M_\odot) \approx 11.2 \pm 0.4$ for PJ0116-24

with SFR$_{\rm IR} \approx 1480 ~ M_\odot {\rm yr}^{-1}$, which is 0.8 dex above the star-forming main sequence (SFMS).

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | $z_s$ | $\mu$ | SFR$_{\rm IR, intr.}$ | $f_{\rm unobsc}^\dagger$ | $R_{\rm CC}({\rm SFR}_{\rm IR})$ | $R_{\rm Ia}$ | $\mathcal{N}_{\rm eff}$ | $\mathcal{R}_{\rm CC,obs}$ | $\mathcal{R}_{\rm Ia,obs}$ | Refs. |  |
|  |  |  | ($M_\odot~{\rm yr}^{-1}$) | (%) | (${\rm yr}^{-1}$) | (${\rm yr}^{-1}$) |  | (${\rm yr}^{-1}$) | (${\rm yr}^{-1}$) |  |  |
| PJ0116$-$24 | $2.125$ | $\approx 17$ | $1490 \pm 400$ | $\approx 32\%^\ddagger$ | $15.5 \pm 4.2$ | $1.5 \pm 0.4$ | $2.3 \pm 0.5$ | $3.6 \pm 0.9$ | $1.1 \pm 0.4$ | \(1\) |  |
| PJ0143$-$01 | $1.096$ | $7.1 \pm 2.2$ | $170 \pm 50$ | $20 \pm 10\%$ | $1.8 \pm 0.5$ | $0.2 \pm 0.1$ | $2.3 \pm 0.5$ | $0.4 \pm 0.2$ | $0.2 \pm 0.1$ | \(2\) $\mu$ (3) SFR |  |
| PJ0209+00 | $2.554$ | $10.5 \pm 3.7$ | $2030 \pm 820$ | $20 \pm 10\%$ | $21.1 \pm 8.5$ | $2.1 \pm 0.8$ | $2.2 \pm 0.4$ | $2.6 \pm 1.8$ | $1.3 \pm 0.6$ | \(2\) $\mu$ (4) SFR |  |
| PJ0226+23 | $3.120$ | $28.2 \pm 11.3$ | $1020 \pm 470$ | $20 \pm 10\%$ | $10.6 \pm 4.9$ | $1.0 \pm 0.5$ | $4.0 \pm 0.8$ | $2.1 \pm 1.5$ | $1.0 \pm 0.5$ | \(2\) $\mu$ (3) SFR |  |
| PJ0305$-$30 | $2.263$ | $2.2  \pm 0.6$ | $6290 \pm 1850$ | $20 \pm 10\%$ | $65 \pm 19$ | $6.4 \pm 1.9$ | $2.0 \pm 0.4$ | $8.0 \pm 4.9$ | $3.9 \pm 1.4$ | \(2\) $\mu$ (3) SFR |  |
| PJ0748+59 | $2.755$ | $\approx 15$ | $920 \pm 250$ | $20 \pm 10\%$ | $9.6 \pm 2.6$ | $0.9 \pm 0.3$ | $3.0 \pm 0.6$ | $1.5 \pm 0.9$ | $0.8 \pm 0.3$ | \(5\) $\mu$ (3) SFR |  |
| PJ0846+15 | $2.664$ | $7.7 \pm 1.5$ | ${5200 \pm 2600}$ | $20 \pm 10\%$ | $54 \pm 27$ | $5.3 \pm 2.6$ | $1.5 \pm 0.3$ | $4.4 \pm 3.3$ | $2.2 \pm 1.2$ | \(6\) $\mu$ (3) SFR |  |
| PJ1053+60 | $3.549$ | $\approx 24$ | $710 \pm 200$ | $20 \pm 10\%$ | $7.4 \pm 2.1$ | $0.7 \pm 0.2$ | $3.0 \pm 0.6$ | $1.0 \pm 0.6$ | $0.5 \pm 0.2$ | \(7\) $\mu$ (3) SFR |  |
| PJ1053+05 | $3.005$ | $7.6 \pm 0.7$ | $2610 \pm 590$ | $20 \pm 10\%$ | $27.1 \pm 6.1$ | $2.7 \pm 0.6$ | $3.0 \pm 0.6$ | $4.1 \pm 2.4$ | $2.0 \pm 0.6$ | \(2\) $\mu$ (4) SFR |  |
| PJ1127+46 | $1.303$ | $4.5 \pm 0.6$ | $590 \pm 120$ | $20 \pm 10\%$ | $6.1 \pm 1.2$ | $0.6 \pm 0.1$ | $2.0 \pm 0.4$ | $1.1 \pm 0.6$ | $0.5 \pm 0.2$ | \(2\) $\mu$ (3) SFR |  |
| PJ1127+42 | $2.236$ | $16.4 \pm 3.0$ | $720 \pm 110$ | $\approx$ 31% | $7.5 \pm 1.1$ | $0.7 \pm 0.1$ | $1.3 \pm 0.3$ | $0.9 \pm 0.2$ | $0.3 \pm 0.1$ | \(8\) $\mu$ (4) SFR |  |
| PJ1138+32 | $2.019$ | $2.8  \pm 0.4$ | $910 \pm 190$ | $20 \pm 10\%$ | $9.5 \pm 2.0$ | $0.9 \pm 0.2$ | $2.0 \pm 0.4$ | $1.3 \pm 0.7$ | $0.6 \pm 0.2$ | \(2\) $\mu$ (3) SFR |  |
| PJ1139+20 | $2.858$ | $4.8 \pm 1.1$ | $2660 \pm 750$ | $20 \pm 10\%$ | $27.7 \pm 7.8$ | $2.7 \pm 0.8$ | $3.0 \pm 0.6$ | $4.3 \pm 2.6$ | $2.1 \pm 0.7$ | \(2\) $\mu$ (3) SFR |  |
| PJ1322+09 | $2.068$ | $\approx 20$ | $460 \pm 120$ | $20 \pm 10\%$ | $4.8 \pm 1.2$ | $0.5 \pm 0.1$ | $6.0 \pm 1.2$ | $1.9 \pm 1.1$ | $0.9 \pm 0.3$ | \(5\) $\mu$ (3) SFR |  |
| PJ1326+33 | $2.951$ | $4.3 \pm 0.6$ | $1860 \pm 470$ | $20 \pm 10\%$ | $19.3 \pm 4.9$ | $1.9 \pm 0.5$ | $2.0 \pm 0.4$ | $2.0 \pm 1.2$ | $1.0 \pm 0.3$ | \(2\) $\mu$ (3) SFR |  |
| PJ1329+22 | $2.040$ | $11 \pm 2$ | $1380 \pm 110$ | $20 \pm 10\%$ | $14.4 \pm 1.1$ | $1.4 \pm 0.1$ | $2.5 \pm 0.5$ | $2.4 \pm 1.3$ | $1.2 \pm 0.3$ | \(6\) $\mu$ (3) SFR |  |
| PJ1336+49 | $3.254$ | $8.3 \pm 3.1$ | $2310 \pm 990$ | $20 \pm 10\%$ | $24 \pm 10$ | $2.4 \pm 1.0$ | $2.0 \pm 0.4$ | $2.3 \pm 1.6$ | $1.1 \pm 0.5$ | \(2\) $\mu$ (3) SFR |  |
| PJ1446+17 | $1.084$ | $3.9 \pm 0.7$ | $710 \pm 180$ | $20 \pm 10\%$ | $7.4 \pm 1.9$ | $0.7 \pm 0.2$ | $3.3 \pm 0.7$ | $2.4 \pm 1.4$ | $1.2 \pm 0.4$ | \(2\) $\mu$ (3) SFR |  |
| PJ1449+22 | $2.153$ | $10.1 \pm 5.2$ | $1050 \pm 580$ | $20 \pm 10\%$ | $10.9 \pm 6.0$ | $1.1 \pm 0.6$ | $4.0 \pm 0.8$ | $2.8 \pm 2.1$ | $1.4 \pm 0.8$ | \(2\) $\mu$ (3) SFR |  |
| PJ1607+73 | $1.482$ | $6.8 \pm 1.7$ | $220 \pm 110$ | $20 \pm 10\%$ | $2.3 \pm 1.1$ | $0.2 \pm 0.1$ | $2.7 \pm 0.5$ | $0.5 \pm 0.4$ | $0.2 \pm 0.1$ | \(2\) $\mu$ (4) SFR |  |
| PJ2313+01 | $2.217$ | $6.1 \pm 1.2$ | $1060 \pm 310$ | $20 \pm 10\%$ | $11.0 \pm 3.2$ | $1.1 \pm 0.3$ | $3.7 \pm 0.7$ | $2.5 \pm 1.5$ | $1.2 \pm 0.4$ | \(2\) $\mu$ (3) SFR |  |

: Estimated intrinsic and observable rates of SNe in a subset of PASSAGES

Table notes: **References** for SFR and $\mu$ estimates: (1) (cite: Liu:2024ae); (2) (cite: Kamieneski:2024aa) (3) (cite: Berman:2022aa); (4) (cite: Harrington:2016aa); (5) P. Kamieneski et al., in prep.; (6) (cite: Foo:2025aa); (7) (cite: Wang:2024ab); (8) (cite: Kamieneski:2024ac); (9) (cite: Diaz-Sanchez:2017aa).

$^{^\dagger}$ Unobscured SFR estimated using the adopted $f_{\rm unobsc}$, except for PJ0116-24 (cite: Liu:2024ae) and G165, which are estimated directly from H$\alpha$ (cite: Frye:2024aa) following correction from the measured Balmer decrement. For G165, we assume that the $f_{\rm unobsc}$ for Arc 1 ($\approx 31\%$) applies also for its counterpart, Arc 3. $^{^\ddagger}$ Derived using ${\rm SFR}_{\rm H\alpha,corr} = 470 \pm 60~M_\odot~{\rm yr}^{-1}$ (cite: Liu:2024ae).

In Appendix [5](#sec:appendix_RIa), we use the expected offset of DSFGs from the SFMS to gain an imprecise estimate of reasonable stellar masses. However, ultimately the dependence of Equation [\[eqn:RIa\]](#eqn:RIa) on $M_\star$ is highly subdominant to the contribution from SFR in the star-forming regime (${\rm SFR}\gtrsim 10~M_\odot~{\rm yr}^{-1}$).

Fortunately, this allows us to still predict $R_{\rm Ia}$ for the sample within reason, which we include in Table [1](#tab:computations).

In Fig. [3](#fig:RIa), we show the predicted observable rates of Type Ia supernovae for PASSAGES, $\mathcal{R}_{\rm Ia,obs} \equiv f_{\rm unobsc} \cdot R_{\rm Ia} \cdot \mathcal{N}_{\rm eff} \cdot (1+z)^{-1}$, as a function of their SFR$_{\rm IR}$.

In this regime of star formation, the SN Ia rates are dominated by the contribution from SFR, but the data points’ colors correspond to the lower limits in stellar masses that we adopt, at 0.9 dex above the star-forming main sequence.

In Fig. [4](#fig:RIa_z), we show the observable rates $\mathcal{R}_{\rm Ia,obs} \cdot (f_{\rm unobsc})^{-1}$ vs. redshift[^9], with transparent points indicating the intrinsic rates $R_{\rm Ia}$.

This particularly emphasizes our finding that the decrement in observable rate due to redshift time dilation is approximately counteracted by the boost provided by multiple imaging.

![](R_Ia_vs_z.png)

![image](R_CC_IR_intr_vs_z.png) ![image](R_Ia_IR_intr_vs_z.png)

## Predicting the rate of independent supernova events

Up to this point, we have considered the rate of observable supernovae from Earth’s perspective, taking into account both cosmological time dilation by $(1+z)^{-1}$ and amplification by multiple imaging $\mathcal{N}_{\rm eff}$.

This rate is useful if one’s goal is to catch any image of a glSN, but if the goal is to perform TD cosmography, then the rate of *independent* supernovae events is of greater interest[^10].

We show these rates for PASSAGES in Fig. [5](#fig:comparison), along with the predicted rates from similar works forecasting glSN rates in targeted monitoring searches, including the Frontier Fields (cite: Petrushevska:2018aa; Petrushevska:2018ab) and $128$ galaxy-scale lenses from (cite: Shu:2018ab; Shu:2021ab).

We also indicate rates from the host galaxies of a number of the already-discovered glSNee.g., the core-collapse SN Refsdal (cite: Kelly:2015aa) in a galaxy lensed by MACS J1149, and the set of Type Ia supernovae that includes SN Requiem/SN Encore (cite: Rodney:2021ab; Pierel:2024ab) in MRG-M0138 (cite: Newman:2018aa) and SN H0pe in G165 Arc 2abc (cite: Frye:2024aa).

While $R_{\rm CC}$ and $R_{\rm Ia}$ might appear at first to be equivalent to within a constant factor, this is not quite the case.

By equations [\[eqn:RCC\]](#eqn:RCC) and [\[eqn:RIa\]](#eqn:RIa), the ratio $R_{\rm Ia} / R_{\rm CC} \sim {\rm sSFR}^{-1} \cdot M_\star^{-0.32}$ (plus a constant term).

By the star-forming main sequence, many of the star-forming galaxies included in Fig. [5](#fig:comparison) will have comparable values of sSFR, while the ratio is more weakly dependent on $M_\star$.

For a $10^{10}~M_\odot$ galaxy on the main sequence at $z\sim 2$, for example, $R_{\rm Ia} / R_{\rm CC} \approx 0.1$ (adopting a Kroupa IMF).

Every PASSAGES object included in this work exceeds the rate of all other targets considered in Fig. [5](#fig:comparison), demonstrating the dramatic potential of this sample.

Most are even $>2$ dex above typical arcs in the Frontier Fields; while these clusters are remarkable for their lensing power, the background objects are largely unremarkable in terms of their SFR.

Perhaps more surprising is the observation that our predictions for $R_{\rm CC}$ are all $\gtrsim 1.5$ dex above the host galaxy of SN Refsdal, and even our predicted $R_{\rm Ia}$ are $\gtrsim 1$ dex above MRG-M0138, the host of two recent SNe Ia, Requiem and Encore.

We also observe that the redshift-dilated $R_{\rm CC}$ and $R_{\rm Ia}$ rates for PASSAGES roughly increase with redshift (likely owing to their identification by flux; see Fig. 2 of (cite: Wang:2024ab)). This trend is contrary to the slow decline of the (dilated) cosmic star formation rate density, $\psi(z) \cdot (1+z)^{-1}$ (cite: Madau:2014aa), shown as a gray curve in Fig. [5](#fig:comparison).

In absolute terms, the median (Earth-frame) occurrence rate of individual CCSNe is $3.5~{\rm yr}^{-1}$ and $\sim 0.3~{\rm yr}^{-1}$ for SNe Ia.

This does not imply, we caution, that any 1-year monitoring program would yield multiple glSNe per field, as the actual yield is the occurrence rate multiplied by the *control time* (cite: Zwicky:1938aa).

This is effectively the cumulative duration for which a given supernovae would fall above the detection threshold, which itself depends on a combination of observing sensitivity, dust attenuation, lensing magnification, and the precise supernova type.

We do not simulate a mock observing campaign in this work, but simply remark that this sample has $\gtrsim 18$ members with core-collapse occurrence rates $R_{\rm CC}\cdot (1+z)^{-1}$ in excess of 1 yr$^{-1}$ (with a median closer to 4 per year).

As a conservative example, an observer-frame control time of 1 month per epoch, with 3 epochs over the course of a year, would result in a yield of $N_{\rm CC} \sim 0.5$ detections for each field.

If these 18 fields were all monitored at this rate, one could expect to detect $\sim 9$ CCSNe with this campaign alone (not to mention any SNe Ia that are uncovered).

With the depths of $28 - 29$ mag routinely reachable by JWST at $\sim 1.5~\mu$m in $\sim 1$ hr, it is highly feasible to extend the per-epoch control time well beyond 1 month (e.g., Fig. 12 of (cite: Petrushevska:2016aa)), even for only modestly magnified arcs, such that even a subsample would be expected to result in at least one detection.

As another example, we consider SNe Ia, which of course are more uniform in their light curve behavior, and which are themselves predicted to be quite frequent in HyLIRGs. With SN H0pe as a recent example of a $z\sim 2$ glSN Ia in a relatively dusty environment, we note that its de-magnified peak was observed at $\sim 24$ mag in F150W (rest-frame $V$-band), but it also remained above 25 mag for a duration of $\approx 90$ days in the observed frame (cite: Pierel:2024aa).

The light curve model suggested $A_V = 1.21 \pm 0.11$ (also (cite: Chen:2024ab)); if the supernova were subjected to substantially higher attenuation as might be expected for HyLIRGs, such as $A_V = 5$, then the peak would be $\sim 4$ mag fainter (i.e. $\sim 28$ mag) and the SN would remain above 29 mag for an observer for $\sim 3$ months. With only modest magnification $\mu = 5$ (or 1.7 mag), a 5$\sigma$ point-source limiting depth of 27.3 mag would be required for a detection, achieved in less than 10 minutes of integration with JWST/NIRCam[^11] or $<2$ orbits with HST WFC3/IR in F160W.

As a caveat, however, the occurrence rates we estimate do not account for the possibility that some detected SN events might be caught only when the last image is still visible.

In this hypothetical scenario, there is not likely to be any hope for performing TD cosmography, since no delays can actually be measured through light curves.

It is rather non-trivial to quantify the likelihood of this actually occurring, as it depends on both the time delays between images and the control time (such that the penultimate image to arrive has faded below the detection limit, but not the final image).

To place these forecasts in context, we compare with the yields that are currently expected from other search strategies.

(cite: Sainz-de-Murieta:2024aa) predicted that LSST will uncover $\sim$7 Type Ia glSNe per year within known galaxy-lensed objects that are suitable for TD cosmography.

In this case, the authors note that an $H_0$ measurement is not feasible if the host galaxy is not itself lensed as well (thereby enabling precise lens modeling).

Similarly, (cite: Arendse:2024ab) predict a “gold sample" of $\sim 10$ glSNe Ia yr$^{-1}$ uncovered with LSST that are sufficiently bright and with time delays that are long enough to enable follow-up observations (which are likely essential; (cite: Huber:2019aa)).

Complementary to this will be an approach of monitoring a “watchlist" of lensing galaxy clusters (cite: Ryczanowski:2023aa), which are beneficial for reasons discussed in §[3.4](#sec:REin).

(cite: Bronikowski:2025aa) predict $1-2$ such SNe will be discovered by LSST per year from a sample of 46 well-studied lensing clusters.

The SNe Ia cosmology program of the upcoming *Nancy Grace Roman Space Telescope* (cite: Hounsell:2018aa) will also reveal some fraction that are gravitationally lensed (cite: Oguri:2010ac), which may number as high as $\sim 11$ glSNe Ia and $\sim 20$ cumulative lensed CCSNe (cite: Pierel:2021ab).

## Identifying candidates with the longest median time delay

Cluster-scale lenses are typically the best candidates for high rates of lensed SNe in the observed frame due to their large lensing cross sections $\sigma(z_s)$ in the source-plane at $z_s$ (cite: Turner:1984aa).

This cross-section is closely linked to the Einstein radius $$\begin{equation}
\theta_E = \bigg[\frac{4GM(<\theta_E)}{c^2} \cdot \frac{D_{LS}}{D_L D_S}\bigg]^{1/2}
\end{equation}$$ (e.g., (cite: Narayan:1996aa)) for enclosed mass $M(<\theta_E)$ and angular-diameter distances to the lens ($D_L$), to the source plane ($D_S$), and between these two ($D_{LS}$).

To first order, the area that produces 4 lensed images from a singular isothermal ellipsoid (again excluding demagnified images) is

$\sigma_4 = \pi \epsilon^2 \theta_E^2 / 6$ (cite: Kochanek:2006aa),

where $\epsilon \equiv 1- b/a$ is the ellipticity (from major and minor axes, $a$ and $b$).

The cross section then scales linearly with mass, $\sigma_4 \propto M(<\theta_E)$,

such that a cluster can have orders of magnitude larger areas.

As discussed in §[2.2](#sec:multiplicity), this larger area of magnification means that a galaxy is more likely to be lensed uniformly into a constant multiplicity of images,

but it also means that objects nearby in projected distance will also be multiply-imaged (§[3.6](#sec:environments)). This further amplifies the expected rate of observable SNe.

Cluster lenses with large Einstein radii are also beneficial for following up lensed SNe for the purpose of TD cosmography (e.g., (cite: Bronikowski:2025aa)).

It is true that time delays between any pair of cluster-lensed images can still be very short (e.g. a few days)especially in the case where the deflection is dominated by a galaxy- or group-scale halo embedded within the cluster. For example, this was the case with the first four images of SN Refsdal, which formed an Einstein cross configuration ($\theta_{\rm Ein} \approx 1.3$; delays $\approx 10-20$ days; (cite: Kelly:2023ab)) around an elliptical galaxy in the cluster at $z=0.54$ (cite: Kelly:2015aa).

However,

one should expect that

a larger Einstein radius (or angular separation between images) would correlate with a larger median delay, by virtue of the longer path lengths followed by the highly-deflected light rays.

In practice, varying approaches are used to quantify the Einstein radius of a system (see for example §3.5 of (cite: Kamieneski:2024aa)).

For the PASSAGES objects in this work, the values of $\theta_{\rm Ein}$ shown in Table [2](#tab:td_Ein) are derived according to the *equivalent* Einstein radius definition, which is the radius of the smallest circle centered on the peak of lensing convergence $\kappa$ that contains an average $\langle \kappa \rangle < 1$ (cite: Schneider:1992aa).

For lensed systems with multi-modal mass distributions, different Einstein radii may be measured for the different mass components.

This notably includes G165, the field containing both SN H0pe and the PJ1127+42 DSFG.

With the model from (cite: Kamieneski:2024ac), we measure $\theta_{\rm Ein} = 10.7\ensuremath{''} \pm 1.1\ensuremath{''}$ for the $z=2.24$ DSFG arc on the southwest side of the cluster, and $21.1\ensuremath{''} \pm 0.5\ensuremath{''}$ for the $z=1.78$ arc hosting SN H0pe on the northeast side.

(cite: Frye:2019aa) measured a lens size of $13\ensuremath{''}$, but with a different definition (based on the total area inside the critical curve for the full cluster).

(cite: Pascale:2022aa) measured $15.3\ensuremath{''}$ for $z=9$ using the same approach, or $\approx 14.4\ensuremath{''}$ rescaled to $z_s = 2.24$, although this and the (cite: Frye:2019aa) measurement were made before new constraints from NIRCam were available (cite: Frye:2024aa).

For other previously discovered glSNe summarized at the bottom of Table [2](#tab:td_Ein), the Einstein radii are estimated

using the publicly-available Frontier Fields lens models (cite: Lotz:2017aa). For these, we also employ a model-independent approach to determine the radius of a circle that best captures the distribution of features/clumps within the lensed arcs (e.g., (cite: Remolina-Gonzalez:2020aa; Mork:2025aa)).

Fig. [6](#fig:R_E) shows the median lens model-predicted time delay ($\widetilde{t_d}$) vs. Einstein radius for the PASSAGES sample, along with the observed/predicted values for the set of known glSNe.

While there is a decent amount of scatterespecially at the high-$\theta_E$, high-$t_d$ endthere is a clear strong correlation between $t_d$ and $\theta_E$ (Spearman’s rank correlation coefficient $\rho = 0.89$, with high significance $p\ll 0.01$), such that $\theta_E$ may be used to select likely long-delay lenses as a rule-of-thumb.

As we discuss in Appendix [6](#sec:appendix_td_Re_corr), this correlation has some theoretical underpinning, since time delays can be related to the image separations of arcs relative to the lens centroid.

## Optimizing the success of a random monitoring program

Ideally, for a monitoring program to be successful, time delays between images should be relatively comparable to the average duration between supernovae in the observer-framei.e., $\tau_{\rm SN} \equiv (R_{\rm CC} + R_{\rm Ia})^{-1} \cdot (1+z)$.

If the median time delay is much less than this characteristic time between SNe, $\widetilde{t_d} \ll \tau_{\rm SN}$, then multiple imaging does not contribute very favorably to boosting the rate of observable SNe.

In this scenario, there would still be long durations where no SN images would be visible, presenting challenges for monitoring campaigns.

The PASSAGES targets and the hosts of some of the confirmed glSNe in the literature are shown in Fig. [7](#fig:tau_SN).

There are also unique challenges for fields with very short $\tau_{\rm SN}$ timescales (e.g. less than 1 month observed-frame), as it can then become difficult to confirm that transient events seen in multiple images of a galaxy are in fact images of the same supernova.

This risk of confusion can certainly be mitigated: information on parity and relative location of the transient within the arc can be helpful in ruling out unrelated events.

Very few targets are likely to lie in this regime, and a well-refined lens model can assist in assessing the reliability of glSN candidates. For PASSAGES, for example, PJ0846+15 nominally has a very short $\tau_{\rm SN}$, but in reality, the very high SN rates arise from a very high SFR from multiple galaxies in a candidate protocluster core (cite: Foo:2025aa), in which case it is much easier to rule out unrelated transient events.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | $z_l$ | $z_s$ | $\theta_{\rm Ein}$ | $\widetilde{t_d}^{\ \dagger}$ | max $t_d^{\ \dagger}$ | Refs.$^\ddagger$ |
|  |  |  | ($\ensuremath{''}$) | (days) | (days) |  |
| PJ0116$-$24 | $0.555$ | $2.125$ | $2.37 \pm 0.04$ | $72$ | 201 | \(1\) |
| PJ0143$-$01 | $0.594$ | $1.096$ | $0.53 \pm 0.08$ | $3.4$ | 10 | \(1\) |
| PJ0209+00 | $0.202$ | $2.554$ | $2.6 \pm 0.2$ | $56$ | 60 | \(1\) |
| PJ0226+23 | $0.41$ | $3.120$ | $3.6 \pm 0.3$ | $110$ | 190 | \(1\) |
| PJ0305$-$30 | $0.5$ | $2.263$ | $0.6 \pm 0.1$ | $11$ | 11 | \(1\) |
| PJ0748+59 | $0.402$ | $2.755$ | $16.2 \pm 1.3$ | $3600$ | 5400 | (2,3) |
| PJ0846+15 | $0.766$ | $2.664$ | $5.5 \pm 1.6^{\dagger\dagger}$ | 560$^{\dagger\dagger}$ | 780$^{\dagger\dagger}$ | \(4\) |
| PJ1053+60 | $0.837$ | $3.549$ | 5.9 |  |  | \(5\) |
| PJ1053+05 | $1.525$ | $3.005$ | $0.71 \pm 0.04$ | $23$ | 62 | \(1\) |
| PJ1127+46 | $0.42$ | $1.303$ | $0.58 \pm 0.06$ | $14$ | 14 | \(1\) |
| PJ1127+42 | $0.348$ | $2.236$ | $10.7 \pm 1.1$ | $470$ | 580 | (6,7) |
| PJ1138+32 | $0.52$ | $2.019$ | $0.40 \pm 0.05$ | $14$ | 16 | \(1\) |
| PJ1139+20 | $0.57$ | $2.858$ | $0.7 \pm 0.4$ | $46$ | 59 | \(1\) |
| PJ1322+09 | 0.6 | $2.068$ | $6.1\pm 1.0$ | $420$ | 560 | \(3\) |
| PJ1326+33 | $0.786$ | $2.951$ | $1.8 \pm 0.2$ | $510$ | 580 | \(1\) |
| PJ1329+22 | $0.44$ | $2.040$ | $11.0 \pm 0.4$ |  |  | \(8\) |
| PJ1336+49 | $0.26$ | $3.254$ | $1.2 \pm 0.1$ | $36$ | 39 | \(1\) |
| PJ1446+17 | $0.493$ | $1.084$ | $0.82 \pm 0.05$ | $12$ | 14 | \(1\) |
| PJ1449+22 | $0.4$ | $2.153$ | $6.5 \pm 1.2$ | $300$ | 460 | \(1\) |
| PJ1607+73 | $0.65$ | $1.482$ | $1.0 \pm 0.1$ | $35$ | 36 | \(1\) |
| PJ2313+01 | $0.560$ | $2.217$ | $2.1 \pm 0.2$ | $58$ | 94 | \(1\) |
| **Literature** |  |  |  |  |  |  |
| PS1-10afx | $1.117$ | $1.388$ | $0.12$ | $1.3$ |  | (9,10) |
| SN Refsdal(S1-S4) | $0.54$ | $1.49$ | $1.37 \pm 0.08^{\dagger\dagger}$ | $4$ |  | (11,12) |
| SN Refsdal(SX) |  |  | $4.5^{\dagger\dagger}$ | $380$ |  | (11,13) |
| iPTF16geu | $0.216$ | $0.409$ | $0.3$ | $1.4$ |  | (14,15,16) |
| SN Requiem/Encore | $0.338$ | $1.95$ | $18.8 \pm 1.1$ | $7800$ |  | (17,18,19) |
| SN Zwicky | $0.226$ | $0.354$ | $0.168$ | $0.42$ |  | (20,21) |
| SN A370-C22 | $0.375$ | $2.93$ | $1.0 \pm 0.5^{\dagger\dagger}$ | $31$ |  | \(22\) |
| SN H0pe | $0.348$ | $1.78$ | ${21.1 \pm 0.5}^{\dagger\dagger}$ | $83$ |  | (6,23) |

: Einstein radii and lens model-estimated median time delays for PASSAGES targets and for glSNe drawn from the literature.

Table notes: **References**: (1) (cite: Kamieneski:2024aa); (2) (cite: Amodeo:2018aa); (3) P. Kamieneski et al., in prep.; (4) (cite: Foo:2025aa); (5) (cite: Wang:2024ab); (6) (cite: Frye:2024aa); (7) (cite: Kamieneski:2024ac); (8) (cite: Diaz-Sanchez:2017aa); (9) (cite: Chornock:2013aa); (10) (cite: Quimby:2014aa); (11) (cite: Kelly:2015aa); (12) (cite: Rodney:2016aa); (13) (cite: Kelly:2023aa); (14) (cite: Goobar:2017aa); (15) (cite: Diego:2022ad); (16) (cite: Dhawan:2020aa); (17) (cite: Rodney:2021ab); (18) (cite: Pierel:2024ab); (19) (cite: Ertl:2025aa); (20) (cite: Goobar:2022aa); (21) (cite: Pierel:2023aa); (22) (cite: Chen:2022ag); (23) (cite: Pierel:2024aa).

$^{^\dagger}$ Median (and maximum) time delays for PASSAGES objects derived in this work (unless otherwise noted), using lens models from the supplied references. The representative values are simply determined by taking the median/maximum of the delays from the first image in each lensed system to arrive. Estimates are not currently available for PJ1053+60 and PJ1329+22. $^{^\ddagger}$ References for table values, roughly in order of columns (e.g., SN discovery if applicable, followed by redshifts, then $\theta_{\rm Ein}$, and finally time delays). For SN Requiem/Encore, $\theta_{\rm Ein}$ is determined by rescaling $\theta_{\rm Ein}(z\to\infty)$ from (cite: Ertl:2025aa) to $z_s=1.95$. $^{^{\dagger\dagger}}$ Estimated in this work. The Einstein radii for the SNe in Abell 370 and MACS J1149 (Refsdal) are taken as the median $\theta_{\rm Ein}$ derived from the publicly available convergence maps from the Frontier Fields (cite: Lotz:2017aa) lens models at <https://archive.stsci.edu/prepds/frontier/lensmodels>in particular, the CATS, GLAFIC, and Sharon models (given their similarity to the LENSTOOL models used for the PASSAGES objects).

The range of values are combined with our own empirical measurements according to the method from (cite: Mork:2025aa).

For PJ0846+15, $\theta_{\rm Ein}$ and $\widetilde{t_d}$ are estimated for the Einstein cross system, 12abcd (cite: Foo:2025aa).

The sample members with the longest predicted median time delays $>100$ days include (in descending order) PJ0748+59,

PJ0846+15 , PJ1326+33, PJ1127+42, PJ1322+09, PJ1449+22, and PJ0226+23.

These are also among the widest-separation targets, as expected.

Except for PJ0226+23, these all also have $\widetilde{t_d} > \tau_{\rm SN}$ and $\mathcal{R}_{\rm CC,obs} + \mathcal{R}_{\rm Ia,obs} > {1}$.

This upper echelon only considers the $\mathcal{R}$ rates and expected time delaysi.e., not magnification, dust attenuation, or other factors that influence the control time.

![](td_med_vs_r_Ein.png)

Lastly, we note that the vast majority ($90\%$) of objects in the full sample have an expected value of multiplicity, $\mathcal{N}_{\rm eff} > 2$.

This suggests that supernovae hosted by the primary DSFGs in these fields are likely to be multiply-imaged (and not just weakly lensed into a single image), and therefore hypothetically suitable for time-delay analysesalthough $\mathcal{N}_{\rm eff} < 2$ certainly does not mean glSNe are not possible.

In the next section, we discuss contribution from other galaxies in the fields nearby to the DSFGs that might also be lensed into multiple images, but this generally requires a large lensing cross section that can only be attributed to galaxy cluster lenses.

![](tau_SN_vs_td.png)

## Contribution from galaxy-overdense regions

Thus far, our estimated SN rates have been limited to the lensed dusty star-forming galaxies that were responsible for the submillimeter flux by which the PASSAGES sample was selected.

However, this does not account for the contributions from other galaxies that might also be gravitationally lensed, especially in the case of cluster-scale lenses with wide caustic networks.

Numerous recent works have revealed that DSFGs, like other very massive galaxies ((cite: Greve:2005aa)), might be effective signposts of proto-clusters (or at least overdense regions; (cite: Kauffmann:1999ab; Chiang:2013aa); reviews by (cite: Overzier:2016aa; Alberts:2022ab)).

This complements the established association of proto-clusters with over-densities of H$\alpha$ and Lyman-$\alpha$ emitters, High-$z$ Radio Galaxies, and Lyman Break Galaxies (e.g., (cite: De-Breuck:2004aa; Venemans:2007aa; Miley:2008aa; Daddi:2009aa; Capak:2011ab; Drake:2020aa)).

The rich set of literature with evidence for DSFGs (or over-densities of DSFGs) as proto-cluster signposts includes (cite: Riechers:2010aa; Dannerbauer:2014aa; Casey:2015aa; Umehata:2015aa; Casey:2016aa; Clements:2016aa; Hung:2016aa; Smolcic:2017ab; Lewis:2018aa; Miller:2018ab; Pavesi:2018aa; Calvi:2023ab).

Two members of the PASSAGES sample have themselves been highlighted as protocluster candidates ((cite: Frye:2024aa; Foo:2025aa)).

On the other hand, DSFGs may not be efficient tracers of over-densities at all redshifts. (cite: Miller:2015aa) suggest that since $z\lesssim 2.5$, the high-mass end of galaxies within the most massive dark matter halos have already quenched their star formation and ceased to be submillimeter-bright.

Semi-analytic modeling by (cite: Araya-Araya:2024aa) revealed an excess of SMGs in $z \gtrsim 2$ protocluster cores (relative to protocluster outskirts or field environments).

The authors concluded that this was driven primarily by oversampling the high-mass end of the halo mass function.

Fortunately, overdensities of starbursts in protocluster cores

((cite: Oteo:2018aa; Long:2020aa; Champagne:2021aa; Arribas:2024aa))

suggest that they may be confined within regions of $\sim 100 - 500$ kpc in diameter ($\sim 0.2 - 1.0\ensuremath{'}$ at $z=3$). They thus can overlap more substantially with the multiply-imaged source-plane regions behind lensing clusters.

For example, (cite: Frye:2024aa) estimated an integrated SFR of $100-500~{\rm M}_\odot~{\rm yr}^{-1}$ in two overdensities ($z\approx 1.8$ and $z\approx 2.2$) behind the G165 cluster, accounting for $\sim 1 - 3$ CCSNe yr$^{-1}$.

Perhaps as a proof of concept, the triply-imaged SN H0pe was discovered in a massive host galaxy within the $z\sim 1.8$ overdensity behind G165 (cite: Frye:2023ab; Polletta:2023aa; Frye:2024aa),

through JWST/NIRCam imaging that was primarily targeting the PASSAGES DSFG that is nearby in projection.

# Summary

So far, discoveries of gravitationally lensed supernovae that can be observed in multiple images have been very limitedunsurprisingly, as both lensing and supernovae are rare phenomena.

They are, however, exceptionally useful for the purpose of time-delay cosmography, which depends upon the delays in arrival time between pairs of multiple images (induced by the difference both in path lengths of their respective geodesics and in the gravitational potential that they experience).

Considering the yet-unresolved Hubble tension in different measurements of the Universe’s expansion rate, novel and independent methods to constrain $H_0$ are likely to be highly informative.

Yet, fewer than 10 multiply-imaged supernovae have ever been discovered, and only 2 of which have so far been employed successfully for TD cosmography (SN Refsdal and SN H0pe; (cite: Kelly:2023ab; Pascale:2025aa)).

There are several advantages to using supernovae for this measurement over, for example, lensed quasars

(e.g., reviews by (cite: Treu:2022ac; Birrer:2024aa));

chief among them is that the light curve of a supernova is transient, not just variable like quasars, and is capable of being modeled.

For now, though, lensed quasars have a key advantage through being simply more numerous.

A joint inference of $H_0$, combining information from several lensed supernovae, can be quite competitive with the level of precision achieved for other methods that have so far received much more attention.

To get to this point in the next decade, however, requires many more discoveries, and it will likely not be sufficient to rely on luck alone.

To this end, we consider the feasibility of a targeted approach focused on galaxies that are expected to be uniquely fruitful for gravitationally lensed supernovae.

In this work, we have attempted to forecast the rates of glSNe that might be reasonably observed for a set of 21 dusty star-forming galaxies from the PASSAGES sample, spanning $z\approx 1.1 - 3.5$.

Using their magnification-corrected intrinsic star formation rates, derived in previous works, we tabulate their rates of core-collapse and Type Ia supernovae, $R_{\rm CC}$ and $R_{\rm Ia}$.

Given the expectation that only a fraction of this star formation is occurring in regions with low enough dust obscuration to ever be detectable, even with the likes of JWST, we apply an assumed unobscured fraction ($\sim 20\%$) to our supernova rates.

The exact sensitivity and control time will depend on observing setup, but (cite: Mantynen:2025aa) found a detectable fraction of $\approx 34\%$ for local LIRGs in an experiment sensitive to $A_V < 16$.

We also include the reduction in observable rates due to the fact that time in these galaxies is slowed by a factor of $1+z$ from the perspective of Earth.

On the other hand, the observable rates are boosted by some factor $\mathcal{N}_{\rm eff}$ (capturing the expected value of multiple images that a SN will appear in), based on existing gravitational lens models and the probabilistic distribution of star formation captured by dust and/or radio continuum.

As a result, we estimate a range of intrinsic rates $R_{\rm CC} \approx {1.8 - 65}~{\rm yr}^{-1}$ (core-collapse; median $11~{\rm yr}^{-1}$) and $R_{\rm Ia} \approx {0.2 - 6.4}~{\rm yr}^{-1}$ (Type Ia; median $1.1~{\rm yr}^{-1}$),

with observable rates $\mathcal{R}_{\rm CC} \approx {0.4 - 8.0}~{\rm yr}^{-1}$ (median $2.3~{\rm yr}^{-1}$) and $\mathcal{R}_{\rm Ia} \approx {0.2 - 3.9}~{\rm yr}^{-1}$ (median $1.1~{\rm yr}^{-1}$).

As for the time-delayed rates of individual SNe, $R\cdot (1+z)^{-1}$, we find ranges of $0.8 - 20~{\rm yr}^{-1}$ (median $3.5~{\rm yr}^{-1}$)

and $0.1 - 2.0~{\rm yr}^{-1}$ (median $0.3~{\rm yr}^{-1}$)

for CCSNe and SNe Ia, respectively.

The number of supernovae that a monitoring campaign would yield is dependent on the control time of the observations, or the duration for which a given supernova would be above survey limits.

In this regard, the biggest challenge for this particular sample would be ensuring adequate near-IR sensitivity to withstand dust attenuation, effectively necessitating JWST/NIRCam. While we have discussed some evidence that the attenuation might be inhomogeneous enough to allow some relatively unobscured sightlines, this is a source of large uncertainty at the moment.

Despite this challenge, the population of lensed starbursts is a veritable wealth of supernovae, in the extremely rarefied stratum of galaxies with more than one supernova occurring per (rest-frame) year.

Notwithstanding sheer luck, for almost any other targeted strategy to discover glSNe, it would be necessary to monitor either a small sample for several years, or else a very large sample over a shorter timespan.

Whereas only 2 glSNe have yet delivered time-delay cosmographical measurements (SN Refsdal and SN H0pe, at time of writing), every new discovery has enormous potential to significantly improve the level of uncertainty on $H_0$ inferences and other cosmological parameters (e.g., (cite: Grillo:2024aa)).

The ultimate goal of the next decade is to reach $\sim 1\%$ precision through joint inference (cite: Coe:2009aa; Treu:2016aa; Treu:2022ac).

Fortunately, the PASSAGES objects typically have wider separations between lensed images; their Einstein radii satisfy $\theta_{\rm Ein} \gtrsim 0.5\ensuremath{''}$ in the vast majority of cases, with some even exceeding 10$\ensuremath{''}$.

We find that a strong correlation between $\theta_{\rm Ein}$ and their median lens model-predicted time delays, which may even have some analytical basis connecting the maximum time delay that can be expected for an axisymmetric isothermal lens and its Einstein radius (Appendix [6](#sec:appendix_td_Re_corr)).

Finally, we compare the expected median time delays to the characteristic observed-frame timescale between supernova events (including both core-collapse and Type Ia).

We find that PASSAGES occupies an ideal regime where the lensing time delays are not significantly shorter than the time between individual supernovae, such that multiple imaging from lensing helps improve the odds of catching one in a random monitoring program.

While this work forecasts the potential of the $\sim 30$ PASSAGES lensed DSFGs, in part because they account for a non-negligible fraction of the known HyLIRGs,

there are several hundred other candidate lensed DSFGs known currently, and perhaps many thousand more yet to be discovered at slightly lower intrinsic luminosities (cite: Sedgwick:2025aa).

We contend that an optimal approach would involve targeted searches in tandem with (ongoing and planned) wide-area and blind surveys with *Euclid*, Rubin LSST, the *China Space Station Telescope*, and the *Roman Space Telescope* (e.g., (cite: Goldstein:2017aa; Goldstein:2019aa; Wojtak:2019aa; Pierel:2021ab; Ryczanowski:2023aa; Sainz-de-Murieta:2023aa; Arendse:2024ab; Dong:2024ab; Sainz-de-Murieta:2024aa; Bronikowski:2025aa)).

The level of precision in $H_0$ measurements from cluster-lensed supernovae has been of order $6-7\%$ for SN Refsdal (cite: Grillo:2018aa; Kelly:2023ab) and $7-13\%$ for SN H0pe (cite: Pascale:2025aa).

While it will not be possible to replicate the fully-blinded process used in obtaining these results, there is a distinct possibility in refining these uncertainties.

For example, the lens models for SN H0pe were constructed with only 5 spectroscopically-confirmed image system redshifts (out of 21), which can have a sizeable influence on model accuracy (e.g., (cite: Johnson:2016aa)).

Similarly, the SN H0pe inference was subject to unique photometric uncertainties at the time of publication due to the lack of a “template" image (where the supernova was not visible) of the host galaxy in most filters (cite: Pierel:2024aa).

The images of SN Encore with the shortest time delays are similarly expected to yield a measurement of order $\approx 10\%$ precision, whereas the longest delays ($>3000$ days) could reduce this to $2-3\%$ ((cite: Pierel:2024ab); S. Suyu et al., in prep.; J. D. R. Pierel et al., in prep.).

Within PASSAGES, 5 cluster fields have estimated median time delays exceeding 100 days

and $\theta_{\rm Ein} > 5\ensuremath{''}$ (PJ0748+59,

PJ0846+15 ,

PJ1127+42, PJ1322+09, and PJ1449+22)

and should in principle offer the greatest likelihood of a similar level of precision if glSNe were discovered in each.

A joint population inference for $\sim 20$ lensed supernovae has the potential to reach $\sim 1\%$ level precision on $H_0$ (cite: Suyu:2020aa), but even a sample of only 6 lensed quasars has been able to reach $\sim 2\%$ relative uncertainty (cite: Wong:2020aa).

The discovery of 5 lensed supernovae suitable for cosmography from a sample like PASSAGES would result in a competitive $H_0$ measurement, shedding much-needed light on the Hubble tension.

P.S.K. would like to thank Haojing Yan, Kate Whitaker, and Kevin Croker for helpful discussions related to this work.

R.A.W., S.H.C., and R.A.J. acknowledge support from NASA JWST Interdisciplinary Scientist grants NAG5-12460, NNX14AN10G and 80NSSC18K0200 from GSFC.

T.C. acknowledges support from the Beus Center for Cosmic Foundations.

E.F.-J.A. acknowledges support from UNAM-PAPIIT project IA102023, and from CONAHCyT Ciencia de Frontera project ID: CF-2023-I-506.

This paper makes use of the following ALMA data:

ADS/JAO.ALMA #2015.1.01518.S, #2017.1.01214.S, #2016.1.00048.S, and #2019.1.01636.S.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This research has made extensive use of NASA’s Astrophysics Data System.

This work utilizes gravitational lensing models produced by PIs Bradač, Natarajan & Kneib (CATS), Merten & Zitrin, Sharon, Williams, Keeton, Bernstein and Diego, and the GLAFIC group. This lens modeling was partially funded by the HST Frontier Fields program conducted by STScI. STScI is operated by the Association of Universities for Research in Astronomy, Inc. under NASA contract NAS 5-26555. The lens models were obtained from the Mikulski Archive for Space Telescopes (MAST).

We also acknowledge the indigenous peoples of Arizona, including the Akimel O’odham (Pima) and Pee Posh (Maricopa) Indian Communities, whose care and keeping of the land has enabled us to be at ASU’s Tempe campus in the Salt River Valley, where much of our work was conducted.

# Facilities

ALMA, VLA

# Software

APLpy (cite: Robitaille:2012aa; Robitaille:2019aa), astropy (cite: Astropy-Collaboration:2013aa; Astropy-Collaboration:2018aa; Astropy-Collaboration:2022aa), blobcat (cite: Hales:2012aa), casa (cite: McMullin:2007aa), LENSTOOL (cite: Kneib:1993aa; Kneib:1996aa; Jullo:2007aa; Jullo:2009aa), matplotlib (cite: Hunter:2007aa), pandas (cite: McKinney:2010aa; The-pandas-development-Team:2024aa), Ned Wright’s Cosmology Calculator (cite: Wright:2006aa)

# Estimating Type Ia supernova rates robustly without stellar mass measurements

For a subset of the PASSAGES sample, (cite: Kamieneski:2024aa) made predictions for the sSFRs relative to the star-forming main sequence of galaxies between SFR and $M_\star$ (e.g., (cite: Brinchmann:2004aa; Daddi:2007aa; Whitaker:2012aa; Speagle:2014aa)).

(cite: Kamieneski:2024aa) used the objects’ gas depletion times ($\sim 150 - 350$ Myr; (cite: Harrington:2016aa; Harrington:2021aa; Berman:2022aa)) to estimate that they occupied the regime of $\Delta{\rm MS} \equiv {\rm log}_{10}({\rm SFR}/ {\rm SFR}_{\rm MS}) \approx 0.0 - 0.9$, following the prescription of (cite: Wang:2022ac) (see also (cite: Genzel:2015aa; Tacconi:2018aa; Liu:2019ae)).

In an independent approach, (cite: Kamieneski:2024aa) used star formation rate surface densities $\Sigma_{\rm SFR}$ to estimate $\Delta{\rm MS}$, as per (cite: Jimenez-Andrade:2019aa), resulting in a range of $\Delta{\rm MS} \approx -0.1 - 0.5$.

With this information in mind, a sensible upper limit for their sSFRs would be $\Delta{\rm MS} < 0.9$ dex, which happens to be $\approx 3$ times the $1\sigma$ scatter of the main sequence, and also 0.3 dex above the typical threshold for starburst galaxies (cite: Rodighiero:2011aa).

To further motivate this, we consider some recent measurements of stellar masses in large samples of DSFGs.

(cite: Miettinen:2017aa) found that $57\%$ of a sample of 124 mm-selected DSFGs in COSMOS were within a factor of 3 ($\approx 0.5$ dex) of the main sequence, and $89\%$ were below $\Delta{\rm MS} < 0.9$ dex.

Similarly, for 185 submm-selected DSFGs in the North Ecliptic Pole (NEP) field, (cite: Barrufet:2020aa) found 57% within 0.5 dex of the main sequence.

More recently, in a large sample of $\approx$ 450 $z>1$ sources in the NEP selected at 850 $\mu$m, (cite: Shim:2022aa)

found 67% with $\Delta{\rm MS} < 0.5$ dex and 90% with $\Delta{\rm MS} < 0.9$ dex.

This finding that DSFGs are largely not dramatically above the main sequencewith apparently the majority even consistent with the SFMSis not particularly surprising.

As discussed by (cite: Casey:2014aa),

the duty cycle of DSFGs in the starburst regime ($\Delta_{\rm MS}>0.6$ dex) might be quite short, so that they spend most of their time on the main sequence.

We can use this upper limit in sSFR of 0.9 dex above the main sequence (computed according to (cite: Speagle:2014aa)),

along with the total SFRs inferred from the IR, in order to derive lower limits in $M_\star$.

We also use a lower limit of sSFR 0.3 dex below the SFMS, giving the upper limits in $M_\star$.

By extension, these provides lower and upper limits, respectively, in the Ia supernova rate, $R_{\rm Ia}$.

Fortunately, as illustrated in Equation [\[eqn:RIa\]](#eqn:RIa), the dependence on $M_\star$ is quite weak relative to SFR for galaxies on or above the main sequence, so these approximate limits contribute extremely minimally to the error budget in comparison with the uncertainties on SFR.

# The connection between typical time delays and image separations

As noted by (cite: Witt:2000ab) and (cite: Oguri:2007aa), a lens with an isothermal potential $\phi(r,\theta) = r \cdot F(\theta)$ for generalized angular structure $F(\theta)$

will result in time delays between arcs $i$ and $j$ $$\begin{equation}
\Delta t_{ij} = \frac{1+z_l}{2c} \frac{D_L D_S}{D_{LS}} (r_j^2 - r_i^2)
\end{equation}$$ where $r_i$ is the angular distance from arc $i$ to the center of the lens.

This produces the result that $r_j$ and $r_i$ can be arbitrarily largeand therefore $\theta_{\rm Ein}$ as welland still produce a small time delay, as long as $r_j \approx r_i$.

Also, at the redshift of the lens, the physical separation between deflected light rays is $R_{\rm Ein} = D_L \cdot \theta_{\rm Ein}$.

Considering the maximum possible time delays in this formulation (holding fixed the lens and source redshift), $$\begin{equation}
{\rm max}(\Delta t_{ij}) \propto {\rm max}(r_j^2 - r_i^2) \propto (R_{\rm Ein})^2.
\end{equation}$$

In the left panel of Fig. [8](#fig:R_E_kpc), we modify Fig. [6](#fig:R_E) to show $R_{\rm Ein}$ (in kpc) on the horizontal axis and the median time delay, dilated to the redshift of the lens with a $(1+z_l)^{-1}$ factor.

The best-fit power-law slope for the *median* time delays is $\widetilde{t_d} \propto (R_{\rm Ein})^{1.53 \pm 0.16}$, slightly shallower than the prediction for the *maximum* time delays.

In at least the specific case of a singular isothermal spheroid (SIS) lens, the two images satisfy $$\begin{equation}
r_j^2 - r_i^2 = (\theta_{\rm Ein} + \beta)^2 - (\theta_{\rm Ein} - \beta)^2 = 4 \theta_{\rm Ein} \beta
\end{equation}$$ for source-plane offset $\beta$ relative to the lens centroid (cite: Narayan:1996aa). By necessity, $\beta < \theta_{\rm Ein}$, or else only a single image appears.

Therefore, $$\begin{equation}
{\rm max}(r_j^2 - r_i^2) = 4\theta_{\rm Ein}^2
\end{equation}$$ and $$\begin{equation}
\label{eqn:tij}
{\rm max}(\Delta t_{ij}) = \frac{1+z_l}{2c} \frac{D_L D_S}{D_{LS}} \cdot 4\theta_{\rm Ein}^2
\end{equation}$$ for an SIS lens, with $\theta_{\rm Ein}$ in radians.

The right panel of Fig. [8](#fig:R_E_kpc) plots this term on the horizontal axis, with the lens model-predicted maximum time delays (Table [2](#tab:td_Ein)) on the vertical axis. A quasi-forbidden region is shaded in gray, representing model-predicted time delays that exceed the maximum from the (cite: Witt:2000ab) and (cite: Oguri:2007aa) equation in the case of an SIS.

We observe that the maximum model-predicted time delays $t_d$ remain below ${\rm max}(\Delta t_{ij})$.

![image](td_med_vs_r_Ein_kpc.png) ![image](td_med_vs_r_Ein_Oguri07.png)

Given the limiting assumptions implicit to this formulation (mainly that the lensing mass is consistent with a single SIS lens), this connection between time delays and Einstein radii will not hold in all cases.

Still, it is reasonably useful for our purposes in identifying lenses that are more likely to have time delays of order months to years.

By equation [\[eqn:tij\]](#eqn:tij), for a fiducial SIS lens at $z_l=0.5$ and source at $z_s=2$, ${\rm max}(\Delta t_{ij}) < 30$ days for $\theta_{\rm Ein} \lesssim 0.4\ensuremath{''}$, while ${\rm max}(\Delta t_{ij}) < 100$ days for $\theta_{\rm Ein} \lesssim 0.8\ensuremath{''}$.

Only $\sim 29\%$ of the PASSAGES subsample have $\theta_{\rm Ein} < 0.8\ensuremath{''}$ (Table [2](#tab:td_Ein)), while none considered have $\theta_{\rm Ein} < 0.4\ensuremath{''}$, so their time delays are more likely to be longer, which generally yields improved $H_0$ precision.

natexlab

(ref: Aalto:2015aa) Aalto, S., Martı́n, S., Costagliola, F., et al. 2015, A&A, 584, A42, doi: [`10.1051/0004-6361/201526410`](http://doi.org/10.1051/0004-6361/201526410)

(ref: Abdurrouf:2023aa) Abdurro’uf, Coe, D., Jung, I., et al. 2023, ApJ, 945, 117, doi: [`10.3847/1538-4357/acba06`](http://doi.org/10.3847/1538-4357/acba06)

(ref: Aiola:2020aa) Aiola, S., Calabrese, E., Maurin, L., et al. 2020, JCAP, 2020, 047, doi: [`10.1088/1475-7516/2020/12/047`](http://doi.org/10.1088/1475-7516/2020/12/047)

(ref: Akins:2025ab) Akins, H. B., Casey, C. M., Champagne, J. B., et al. 2025, arXiv e-prints, arXiv:2508.06607. [`https://arxiv.org/abs/2508.06607`](https://arxiv.org/abs/2508.06607)

(ref: Alberts:2022ab) Alberts, S., & Noble, A. 2022, Universe, 8, 554, doi: [`10.3390/universe8110554`](http://doi.org/10.3390/universe8110554)

(ref: Amodeo:2018aa) Amodeo, S., Mei, S., Stanford, S. A., et al. 2018, ApJ, 853, 36, doi: [`10.3847/1538-4357/aa98dd`](http://doi.org/10.3847/1538-4357/aa98dd)

(ref: Anand:2024aa) Anand, G. S., Riess, A. G., Yuan, W., et al. 2024, ApJ, 966, 89, doi: [`10.3847/1538-4357/ad2e0a`](http://doi.org/10.3847/1538-4357/ad2e0a)

(ref: Andersen:2018aa) Andersen, P., & Hjorth, J. 2018, MNRAS, 480, 68, doi: [`10.1093/mnras/sty1837`](http://doi.org/10.1093/mnras/sty1837)

(ref: Araya-Araya:2024aa) Araya-Araya, P., Cochrane, R. K., Hayward, C. C., et al. 2024, ApJ, 977, 204, doi: [`10.3847/1538-4357/ad90ae`](http://doi.org/10.3847/1538-4357/ad90ae)

(ref: Arendse:2024ab) Arendse, N., Dhawan, S., Sagués Carracedo, A., et al. 2024, MNRAS, 531, 3509, doi: [`10.1093/mnras/stae1356`](http://doi.org/10.1093/mnras/stae1356)

(ref: Arribas:2024aa) Arribas, S., Perna, M., Rodrı́guez Del Pino, B., et al. 2024, A&A, 688, A146, doi: [`10.1051/0004-6361/202348824`](http://doi.org/10.1051/0004-6361/202348824)

(ref: Astropy-Collaboration:2013aa) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy-Collaboration:2018aa) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy-Collaboration:2022aa) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bag:2024aa) Bag, S., Huber, S., Suyu, S. H., et al. 2024, A&A, 691, A100, doi: [`10.1051/0004-6361/202450485`](http://doi.org/10.1051/0004-6361/202450485)

(ref: Baker:2022aa) Baker, W. M., Maiolino, R., Bluck, A. F. L., et al. 2022, MNRAS, 510, 3622, doi: [`10.1093/mnras/stab3672`](http://doi.org/10.1093/mnras/stab3672)

(ref: Bakx:2024aa) Bakx, T. J. L. C., Gray, B. S., González-Nuevo, J., et al. 2024a, MNRAS, 527, 8865, doi: [`10.1093/mnras/stad3759`](http://doi.org/10.1093/mnras/stad3759)

(ref: Bakx:2018aa) Bakx, T. J. L. C., Eales, S. A., Negrello, M., et al. 2018, MNRAS, 473, 1751, doi: [`10.1093/mnras/stx2267`](http://doi.org/10.1093/mnras/stx2267)

(ref: Bakx:2024ad) Bakx, T. J. L. C., Amvrosiadis, A., Bendo, G. J., et al. 2024b, MNRAS, 535, 1533, doi: [`10.1093/mnras/stae2409`](http://doi.org/10.1093/mnras/stae2409)

(ref: Barrufet:2020aa) Barrufet, L., Pearson, C., Serjeant, S., et al. 2020, A&A, 641, A129, doi: [`10.1051/0004-6361/202037838`](http://doi.org/10.1051/0004-6361/202037838)

(ref: Bellm:2014aa) Bellm, E. 2014, in The Third Hot-wiring the Transient Universe Workshop, ed. P. R. Wozniak, M. J. Graham, A. A. Mahabal, & R. Seaman, 27–33, doi: [`10.48550/arXiv.1410.8185`](http://doi.org/10.48550/arXiv.1410.8185)

(ref: Berman:2022aa) Berman, D. A., Yun, M. S., Harrington, K. C., et al. 2022, MNRAS, 515, 3911, doi: [`10.1093/mnras/stac1494`](http://doi.org/10.1093/mnras/stac1494)

(ref: Bik:2018aa) Bik, A., Östlin, G., Menacho, V., et al. 2018, A&A, 619, A131, doi: [`10.1051/0004-6361/201833916`](http://doi.org/10.1051/0004-6361/201833916)

(ref: Birrer:2020ab) Birrer, S., Shajib, A. J., Galan, A., et al. 2020, A&A, 643, A165, doi: [`10.1051/0004-6361/202038861`](http://doi.org/10.1051/0004-6361/202038861)

(ref: Birrer:2024aa) Birrer, S., Millon, M., Sluse, D., et al. 2024, Space Sci. Rev., 220, 48, doi: [`10.1007/s11214-024-01079-w`](http://doi.org/10.1007/s11214-024-01079-w)

(ref: Blain:1996aa) Blain, A. W. 1996, MNRAS, 283, 1340, doi: [`10.1093/mnras/283.4.1340`](http://doi.org/10.1093/mnras/283.4.1340)

(ref: Blandford:1992aa) Blandford, R. D., & Narayan, R. 1992, ARA&A, 30, 311, doi: [`10.1146/annurev.aa.30.090192.001523`](http://doi.org/10.1146/annurev.aa.30.090192.001523)

(ref: Bondi:2012aa) Bondi, M., Pérez-Torres, M. A., Herrero-Illana, R., & Alberdi, A. 2012, A&A, 539, A134, doi: [`10.1051/0004-6361/201118446`](http://doi.org/10.1051/0004-6361/201118446)

(ref: Bonvin:2017aa) Bonvin, V., Courbin, F., Suyu, S. H., et al. 2017, MNRAS, 465, 4914, doi: [`10.1093/mnras/stw3006`](http://doi.org/10.1093/mnras/stw3006)

(ref: Boquien:2009aa) Boquien, M., Calzetti, D., Kennicutt, R., et al. 2009, ApJ, 706, 553, doi: [`10.1088/0004-637X/706/1/553`](http://doi.org/10.1088/0004-637X/706/1/553)

(ref: Borsato:2024aa) Borsato, E., Marchetti, L., Negrello, M., et al. 2024, MNRAS, 528, 6222, doi: [`10.1093/mnras/stad3381`](http://doi.org/10.1093/mnras/stad3381)

(ref: Bournaud:2007aa) Bournaud, F., Elmegreen, B. G., & Elmegreen, D. M. 2007, ApJ, 670, 237, doi: [`10.1086/522077`](http://doi.org/10.1086/522077)

(ref: Brinchmann:2004aa) Brinchmann, J., Charlot, S., White, S. D. M., et al. 2004, MNRAS, 351, 1151, doi: [`10.1111/j.1365-2966.2004.07881.x`](http://doi.org/10.1111/j.1365-2966.2004.07881.x)

(ref: Bronikowski:2025aa) Bronikowski, M., Petrushevska, T., Pierel, J. D. R., et al. 2025, arXiv e-prints, arXiv:2504.01068. [`https://arxiv.org/abs/2504.01068`](https://arxiv.org/abs/2504.01068)

(ref: Bussmann:2013aa) Bussmann, R. S., Pérez-Fournon, I., Amber, S., et al. 2013, ApJ, 779, 25, doi: [`10.1088/0004-637X/779/1/25`](http://doi.org/10.1088/0004-637X/779/1/25)

(ref: Canameras:2015aa) Cañameras, R., Nesvadba, N. P. H., Guery, D., et al. 2015, A&A, 581, A105, doi: [`10.1051/0004-6361/201425128`](http://doi.org/10.1051/0004-6361/201425128)

(ref: Canameras:2018aa) Cañameras, R., Nesvadba, N. P. H., Limousin, M., et al. 2018, A&A, 620, A60, doi: [`10.1051/0004-6361/201833679`](http://doi.org/10.1051/0004-6361/201833679)

(ref: Calvi:2023ab) Calvi, R., Castignani, G., & Dannerbauer, H. 2023, A&A, 678, A15, doi: [`10.1051/0004-6361/202346200`](http://doi.org/10.1051/0004-6361/202346200)

(ref: Calzetti:1997ab) Calzetti, D. 1997, in American Institute of Physics Conference Series, Vol. 408, The ultraviolet universe at low and High redshift, ed. W. H. Waller, 403–412, doi: [`10.1063/1.53764`](http://doi.org/10.1063/1.53764)

(ref: Calzetti:2000aa) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Capak:2011ab) Capak, P. L., Riechers, D., Scoville, N. Z., et al. 2011, Nature, 470, 233, doi: [`10.1038/nature09681`](http://doi.org/10.1038/nature09681)

(ref: Casey:2016aa) Casey, C. M. 2016, ApJ, 824, 36, doi: [`10.3847/0004-637X/824/1/36`](http://doi.org/10.3847/0004-637X/824/1/36)

(ref: Casey:2014aa) Casey, C. M., Narayanan, D., & Cooray, A. 2014a, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: Casey:2014ab) Casey, C. M., Scoville, N. Z., Sanders, D. B., et al. 2014b, ApJ, 796, 95, doi: [`10.1088/0004-637X/796/2/95`](http://doi.org/10.1088/0004-637X/796/2/95)

(ref: Casey:2015aa) Casey, C. M., Cooray, A., Capak, P., et al. 2015, ApJL, 808, L33, doi: [`10.1088/2041-8205/808/2/L33`](http://doi.org/10.1088/2041-8205/808/2/L33)

(ref: Casey:2017aa) Casey, C. M., Cooray, A., Killi, M., et al. 2017, ApJ, 840, 101, doi: [`10.3847/1538-4357/aa6cb1`](http://doi.org/10.3847/1538-4357/aa6cb1)

(ref: Chabrier:2003aa) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Champagne:2021aa) Champagne, J. B., Casey, C. M., Zavala, J. A., et al. 2021, ApJ, 913, 110, doi: [`10.3847/1538-4357/abf4e6`](http://doi.org/10.3847/1538-4357/abf4e6)

(ref: Chen:2020aa) Chen, C.-C., Harrison, C. M., Smail, I., et al. 2020, A&A, 635, A119, doi: [`10.1051/0004-6361/201936286`](http://doi.org/10.1051/0004-6361/201936286)

(ref: Chen:2022ag) Chen, W., Kelly, P. L., Oguri, M., et al. 2022, Nature, 611, 256, doi: [`10.1038/s41586-022-05252-5`](http://doi.org/10.1038/s41586-022-05252-5)

(ref: Chen:2024ab) Chen, W., Kelly, P. L., Frye, B. L., et al. 2024, ApJ, 970, 102, doi: [`10.3847/1538-4357/ad50a5`](http://doi.org/10.3847/1538-4357/ad50a5)

(ref: Cheng:2020ac) Cheng, C., Ibar, E., Smail, I., et al. 2020, MNRAS, 499, 5241, doi: [`10.1093/mnras/staa3036`](http://doi.org/10.1093/mnras/staa3036)

(ref: Chevance:2022ab) Chevance, M., Kruijssen, J. M. D., Krumholz, M. R., et al. 2022, MNRAS, 509, 272, doi: [`10.1093/mnras/stab2938`](http://doi.org/10.1093/mnras/stab2938)

(ref: Chiang:2013aa) Chiang, Y.-K., Overzier, R., & Gebhardt, K. 2013, ApJ, 779, 127, doi: [`10.1088/0004-637X/779/2/127`](http://doi.org/10.1088/0004-637X/779/2/127)

(ref: Chornock:2013aa) Chornock, R., Berger, E., Rest, A., et al. 2013, ApJ, 767, 162, doi: [`10.1088/0004-637X/767/2/162`](http://doi.org/10.1088/0004-637X/767/2/162)

(ref: Clarke:2002aa) Clarke, C., & Oey, M. S. 2002, MNRAS, 337, 1299, doi: [`10.1046/j.1365-8711.2002.05976.x`](http://doi.org/10.1046/j.1365-8711.2002.05976.x)

(ref: Clements:2016aa) Clements, D. L., Braglia, F., Petitpas, G., et al. 2016, MNRAS, 461, 1719, doi: [`10.1093/mnras/stw1224`](http://doi.org/10.1093/mnras/stw1224)

(ref: Coe:2009aa) Coe, D., & Moustakas, L. A. 2009, ApJ, 706, 45, doi: [`10.1088/0004-637X/706/1/45`](http://doi.org/10.1088/0004-637X/706/1/45)

(ref: Condon:1992aa) Condon, J. J. 1992, ARA&A, 30, 575, doi: [`10.1146/annurev.aa.30.090192.003043`](http://doi.org/10.1146/annurev.aa.30.090192.003043)

(ref: Cooper:2025aa) Cooper, O. R., Brammer, G., Heintz, K. E., et al. 2025, ApJ, 982, 125, doi: [`10.3847/1538-4357/adb8e1`](http://doi.org/10.3847/1538-4357/adb8e1)

(ref: Cortese:2006ab) Cortese, L., Boselli, A., Buat, V., et al. 2006, ApJ, 637, 242, doi: [`10.1086/498296`](http://doi.org/10.1086/498296)

(ref: Courbin:2005aa) Courbin, F., Eigenbrod, A., Vuissoz, C., Meylan, G., & Magain, P. 2005, in Gravitational Lensing Impact on Cosmology, ed. Y. Mellier & G. Meylan, Vol. 225, 297–303, doi: [`10.1017/S1743921305002097`](http://doi.org/10.1017/S1743921305002097)

(ref: Craig:2024aa) Craig, P., O’Connor, K., Chakrabarti, S., et al. 2024, MNRAS, 534, 1077, doi: [`10.1093/mnras/stae2103`](http://doi.org/10.1093/mnras/stae2103)

(ref: Cresci:2007aa) Cresci, G., Mannucci, F., Della Valle, M., & Maiolino, R. 2007, A&A, 462, 927, doi: [`10.1051/0004-6361:20065364`](http://doi.org/10.1051/0004-6361:20065364)

(ref: Daddi:2007aa) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156, doi: [`10.1086/521818`](http://doi.org/10.1086/521818)

(ref: Daddi:2009aa) Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, ApJ, 694, 1517, doi: [`10.1088/0004-637X/694/2/1517`](http://doi.org/10.1088/0004-637X/694/2/1517)

(ref: Dahle:2015aa) Dahle, H., Gladders, M. D., Sharon, K., Bayliss, M. B., & Rigby, J. R. 2015, ApJ, 813, 67, doi: [`10.1088/0004-637X/813/1/67`](http://doi.org/10.1088/0004-637X/813/1/67)

(ref: Dahlen:2012aa) Dahlen, T., Strolger, L.-G., Riess, A. G., et al. 2012, ApJ, 757, 70, doi: [`10.1088/0004-637X/757/1/70`](http://doi.org/10.1088/0004-637X/757/1/70)

(ref: Dannerbauer:2014aa) Dannerbauer, H., Kurk, J. D., De Breuck, C., et al. 2014, A&A, 570, A55, doi: [`10.1051/0004-6361/201423771`](http://doi.org/10.1051/0004-6361/201423771)

(ref: De-Breuck:2004aa) De Breuck, C., Bertoldi, F., Carilli, C., et al. 2004, A&A, 424, 1, doi: [`10.1051/0004-6361:20035885`](http://doi.org/10.1051/0004-6361:20035885)

(ref: de-Grijs:2003aa) de Grijs, R., Anders, P., Bastian, N., et al. 2003, MNRAS, 343, 1285, doi: [`10.1046/j.1365-8711.2003.06777.x`](http://doi.org/10.1046/j.1365-8711.2003.06777.x)

(ref: Dekel:2009aa) Dekel, A., Sari, R., & Ceverino, D. 2009, ApJ, 703, 785, doi: [`10.1088/0004-637X/703/1/785`](http://doi.org/10.1088/0004-637X/703/1/785)

(ref: Del-Moro:2013aa) Del Moro, A., Alexander, D. M., Mullaney, J. R., et al. 2013, A&A, 549, A59, doi: [`10.1051/0004-6361/201219880`](http://doi.org/10.1051/0004-6361/201219880)

(ref: Delvecchio:2017aa) Delvecchio, I., Smolčić, V., Zamorani, G., et al. 2017, A&A, 602, A3, doi: [`10.1051/0004-6361/201629367`](http://doi.org/10.1051/0004-6361/201629367)

(ref: Dhawan:2020aa) Dhawan, S., Johansson, J., Goobar, A., et al. 2020, MNRAS, 491, 2639, doi: [`10.1093/mnras/stz2965`](http://doi.org/10.1093/mnras/stz2965)

(ref: Diaz-Sanchez:2017aa) Dı́az-Sánchez, A., Iglesias-Groth, S., Rebolo, R., & Dannerbauer, H. 2017, ApJL, 843, L22, doi: [`10.3847/2041-8213/aa79ef`](http://doi.org/10.3847/2041-8213/aa79ef)

(ref: Diego:2022ad) Diego, J. M., Bernstein, G., Chen, W., et al. 2022, A&A, 662, A34, doi: [`10.1051/0004-6361/202143009`](http://doi.org/10.1051/0004-6361/202143009)

(ref: Dominguez-Sanchez:2012aa) Domı́nguez Sánchez, H., Mignoli, M., Pozzi, F., et al. 2012, MNRAS, 426, 330, doi: [`10.1111/j.1365-2966.2012.21710.x`](http://doi.org/10.1111/j.1365-2966.2012.21710.x)

(ref: Dong:2024ab) Dong, J., Shu, Y., Li, G., et al. 2024, A&A, 689, A192, doi: [`10.1051/0004-6361/202450838`](http://doi.org/10.1051/0004-6361/202450838)

(ref: Donley:2005aa) Donley, J. L., Rieke, G. H., Rigby, J. R., & Pérez-González, P. G. 2005, ApJ, 634, 169, doi: [`10.1086/491668`](http://doi.org/10.1086/491668)

(ref: Drake:2020aa) Drake, A. B., Walter, F., Novak, M., et al. 2020, ApJ, 902, 37, doi: [`10.3847/1538-4357/aba832`](http://doi.org/10.3847/1538-4357/aba832)

(ref: Emig:2020aa) Emig, K. L., Bolatto, A. D., Leroy, A. K., et al. 2020, ApJ, 903, 50, doi: [`10.3847/1538-4357/abb67d`](http://doi.org/10.3847/1538-4357/abb67d)

(ref: Ertl:2025aa) Ertl, S., Suyu, S. H., Schuldt, S., et al. 2025, arXiv e-prints, arXiv:2503.09718. [`https://arxiv.org/abs/2503.09718`](https://arxiv.org/abs/2503.09718)

(ref: Euclid-Collaboration:2022ab) Euclid Collaboration, Scaramella, R., Amiaux, J., et al. 2022, A&A, 662, A112, doi: [`10.1051/0004-6361/202141938`](http://doi.org/10.1051/0004-6361/202141938)

(ref: Faisst:2017aa) Faisst, A. L., Capak, P. L., Yan, L., et al. 2017, ApJ, 847, 21, doi: [`10.3847/1538-4357/aa886c`](http://doi.org/10.3847/1538-4357/aa886c)

(ref: Faisst:2025aa) Faisst, A. L., Yang, L., Brinch, M., et al. 2025, ApJ, 980, 204, doi: [`10.3847/1538-4357/ada566`](http://doi.org/10.3847/1538-4357/ada566)

(ref: Falco:1985aa) Falco, E. E., Gorenstein, M. V., & Shapiro, I. I. 1985, ApJL, 289, L1, doi: [`10.1086/184422`](http://doi.org/10.1086/184422)

(ref: Falstad:2021aa) Falstad, N., Aalto, S., König, S., et al. 2021, A&A, 649, A105, doi: [`10.1051/0004-6361/202039291`](http://doi.org/10.1051/0004-6361/202039291)

(ref: Fohlmeister:2008aa) Fohlmeister, J., Kochanek, C. S., Falco, E. E., Morgan, C. W., & Wambsganss, J. 2008, ApJ, 676, 761, doi: [`10.1086/528789`](http://doi.org/10.1086/528789)

(ref: Fohlmeister:2007aa) Fohlmeister, J., Kochanek, C. S., Falco, E. E., et al. 2007, ApJ, 662, 62, doi: [`10.1086/518018`](http://doi.org/10.1086/518018)

(ref: Foo:2025aa) Foo, N., Harrington, K. C., Frye, B., et al. 2025, arXiv e-prints, arXiv:2504.05617. [`https://arxiv.org/abs/2504.05617`](https://arxiv.org/abs/2504.05617)

(ref: Fox:2021ab) Fox, O. D., Khandrika, H., Rubin, D., et al. 2021, MNRAS, 506, 4199, doi: [`10.1093/mnras/stab1740`](http://doi.org/10.1093/mnras/stab1740)

(ref: Freedman:2025aa) Freedman, W. L., Madore, B. F., Hoyt, T. J., et al. 2025, ApJ, 985, 203, doi: [`10.3847/1538-4357/adce78`](http://doi.org/10.3847/1538-4357/adce78)

(ref: Freedman:2019aa) Freedman, W. L., Madore, B. F., Hatt, D., et al. 2019, ApJ, 882, 34, doi: [`10.3847/1538-4357/ab2f73`](http://doi.org/10.3847/1538-4357/ab2f73)

(ref: Frye:2019aa) Frye, B. L., Pascale, M., Qin, Y., et al. 2019, ApJ, 871, 51, doi: [`10.3847/1538-4357/aaeff7`](http://doi.org/10.3847/1538-4357/aaeff7)

(ref: Frye:2023ab) Frye, B. L., Pascale, M., Cohen, S., et al. 2023, Transient Name Server AstroNote, 96, 1

(ref: Frye:2024aa) Frye, B. L., Pascale, M., Pierel, J., et al. 2024, ApJ, 961, 171, doi: [`10.3847/1538-4357/ad1034`](http://doi.org/10.3847/1538-4357/ad1034)

(ref: Fujimoto:2017aa) Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83, doi: [`10.3847/1538-4357/aa93e6`](http://doi.org/10.3847/1538-4357/aa93e6)

(ref: Fujimoto:2024aa) Fujimoto, S., Ouchi, M., Kohno, K., et al. 2024, arXiv e-prints, arXiv:2402.18543, doi: [`10.48550/arXiv.2402.18543`](http://doi.org/10.48550/arXiv.2402.18543)

(ref: Gal-Yam:2002aa) Gal-Yam, A., Maoz, D., & Sharon, K. 2002, MNRAS, 332, 37, doi: [`10.1046/j.1365-8711.2002.05274.x`](http://doi.org/10.1046/j.1365-8711.2002.05274.x)

(ref: Genzel:2015aa) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20, doi: [`10.1088/0004-637X/800/1/20`](http://doi.org/10.1088/0004-637X/800/1/20)

(ref: Gimenez-Arteaga:2023aa) Giménez-Arteaga, C., Oesch, P. A., Brammer, G. B., et al. 2023, ApJ, 948, 126, doi: [`10.3847/1538-4357/acc5ea`](http://doi.org/10.3847/1538-4357/acc5ea)

(ref: Giulietti:2024ab) Giulietti, M., Gandolfi, G., Massardi, M., Behiri, M., & Lapi, A. 2024, Galaxies, 12, 9, doi: [`10.3390/galaxies12020009`](http://doi.org/10.3390/galaxies12020009)

(ref: Goldstein:2017aa) Goldstein, D. A., & Nugent, P. E. 2017, ApJL, 834, L5, doi: [`10.3847/2041-8213/834/1/L5`](http://doi.org/10.3847/2041-8213/834/1/L5)

(ref: Goldstein:2019aa) Goldstein, D. A., Nugent, P. E., & Goobar, A. 2019, ApJS, 243, 6, doi: [`10.3847/1538-4365/ab1fe0`](http://doi.org/10.3847/1538-4365/ab1fe0)

(ref: Goobar:2017aa) Goobar, A., Amanullah, R., Kulkarni, S. R., et al. 2017, Science, 356, 291, doi: [`10.1126/science.aal2729`](http://doi.org/10.1126/science.aal2729)

(ref: Goobar:2023aa) Goobar, A., Johansson, J., Schulze, S., et al. 2023, Nature Astronomy, 7, 1098, doi: [`10.1038/s41550-023-01981-3`](http://doi.org/10.1038/s41550-023-01981-3)

(ref: Goobar:2022aa) Goobar, A. A., Johansson, J., Dhawan, S., et al. 2022, Transient Name Server AstroNote, 180, 1

(ref: Gorenstein:1988aa) Gorenstein, M. V., Falco, E. E., & Shapiro, I. I. 1988, ApJ, 327, 693, doi: [`10.1086/166226`](http://doi.org/10.1086/166226)

(ref: Greve:2005aa) Greve, T. R., Bertoldi, F., Smail, I., et al. 2005, MNRAS, 359, 1165, doi: [`10.1111/j.1365-2966.2005.08979.x`](http://doi.org/10.1111/j.1365-2966.2005.08979.x)

(ref: Grillo:2024aa) Grillo, C., Pagano, L., Rosati, P., & Suyu, S. H. 2024, A&A, 684, L23, doi: [`10.1051/0004-6361/202449278`](http://doi.org/10.1051/0004-6361/202449278)

(ref: Grillo:2018aa) Grillo, C., Rosati, P., Suyu, S. H., et al. 2018, ApJ, 860, 94, doi: [`10.3847/1538-4357/aac2c9`](http://doi.org/10.3847/1538-4357/aac2c9)

(ref: Hales:2012aa) Hales, C. A., Murphy, T., Curran, J. R., et al. 2012, MNRAS, 425, 979, doi: [`10.1111/j.1365-2966.2012.21373.x`](http://doi.org/10.1111/j.1365-2966.2012.21373.x)

(ref: Harrington:2016aa) Harrington, K. C., Yun, M. S., Cybulski, R., et al. 2016, MNRAS, 458, 4383, doi: [`10.1093/mnras/stw614`](http://doi.org/10.1093/mnras/stw614)

(ref: Harrington:2021aa) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95, doi: [`10.3847/1538-4357/abcc01`](http://doi.org/10.3847/1538-4357/abcc01)

(ref: Harvey:2025ac) Harvey, T., Conselice, C. J., Adams, N. J., et al. 2025, arXiv e-prints, arXiv:2504.05244, doi: [`10.48550/arXiv.2504.05244`](http://doi.org/10.48550/arXiv.2504.05244)

(ref: Hezaveh:2012aa) Hezaveh, Y. D., Marrone, D. P., & Holder, G. P. 2012, ApJ, 761, 20, doi: [`10.1088/0004-637X/761/1/20`](http://doi.org/10.1088/0004-637X/761/1/20)

(ref: Hilbert:2007aa) Hilbert, S., White, S. D. M., Hartlap, J., & Schneider, P. 2007, MNRAS, 382, 121, doi: [`10.1111/j.1365-2966.2007.12391.x`](http://doi.org/10.1111/j.1365-2966.2007.12391.x)

(ref: Hilbert:2008aa) Hilbert, S., White, S. D. M., Hartlap, J., & Schneider, P. 2008, MNRAS, 386, 1845, doi: [`10.1111/j.1365-2966.2008.13190.x`](http://doi.org/10.1111/j.1365-2966.2008.13190.x)

(ref: Hodge:2016aa) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: Hodge:2019aa) Hodge, J. A., Smail, I., Walter, F., et al. 2019, ApJ, 876, 130, doi: [`10.3847/1538-4357/ab1846`](http://doi.org/10.3847/1538-4357/ab1846)

(ref: Holwerda:2021aa) Holwerda, B. W., Knabel, S., Steele, R. C., et al. 2021, MNRAS, 505, 1316, doi: [`10.1093/mnras/stab1370`](http://doi.org/10.1093/mnras/stab1370)

(ref: Hounsell:2018aa) Hounsell, R., Scolnic, D., Foley, R. J., et al. 2018, ApJ, 867, 23, doi: [`10.3847/1538-4357/aac08b`](http://doi.org/10.3847/1538-4357/aac08b)

(ref: Huber:2019aa) Huber, S., Suyu, S. H., Noebauer, U. M., et al. 2019, A&A, 631, A161, doi: [`10.1051/0004-6361/201935370`](http://doi.org/10.1051/0004-6361/201935370)

(ref: Huber:2022aa) Huber, S., Suyu, S. H., Ghoshdastidar, D., et al. 2022, A&A, 658, A157, doi: [`10.1051/0004-6361/202141956`](http://doi.org/10.1051/0004-6361/202141956)

(ref: Hung:2016aa) Hung, C.-L., Casey, C. M., Chiang, Y.-K., et al. 2016, ApJ, 826, 130, doi: [`10.3847/0004-637X/826/2/130`](http://doi.org/10.3847/0004-637X/826/2/130)

(ref: Hunter:2007aa) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Immeli:2004aa) Immeli, A., Samland, M., Gerhard, O., & Westera, P. 2004, A&A, 413, 547, doi: [`10.1051/0004-6361:20034282`](http://doi.org/10.1051/0004-6361:20034282)

(ref: Irwin:1989aa) Irwin, M. J., Webster, R. L., Hewett, P. C., Corrigan, R. T., & Jedrzejewski, R. I. 1989, AJ, 98, 1989, doi: [`10.1086/115272`](http://doi.org/10.1086/115272)

(ref: Jarrett:2013aa) Jarrett, T. H., Masci, F., Tsai, C. W., et al. 2013, AJ, 145, 6, doi: [`10.1088/0004-6256/145/1/6`](http://doi.org/10.1088/0004-6256/145/1/6)

(ref: Jencson:2019aa) Jencson, J. E., Kasliwal, M. M., Adams, S. M., et al. 2019, ApJ, 886, 40, doi: [`10.3847/1538-4357/ab4a01`](http://doi.org/10.3847/1538-4357/ab4a01)

(ref: Ji:2025aa) Ji, Z., Alberts, S., Zhu, Y., et al. 2025, arXiv e-prints, arXiv:2504.01067. [`https://arxiv.org/abs/2504.01067`](https://arxiv.org/abs/2504.01067)

(ref: Jimenez-Andrade:2019aa) Jiménez-Andrade, E. F., Magnelli, B., Karim, A., et al. 2019, A&A, 625, A114, doi: [`10.1051/0004-6361/201935178`](http://doi.org/10.1051/0004-6361/201935178)

(ref: Johnson:2016aa) Johnson, T. L., & Sharon, K. 2016, ApJ, 832, 82, doi: [`10.3847/0004-637X/832/1/82`](http://doi.org/10.3847/0004-637X/832/1/82)

(ref: Jullo:2009aa) Jullo, E., & Kneib, J.-P. 2009, MNRAS, 395, 1319, doi: [`10.1111/j.1365-2966.2009.14654.x`](http://doi.org/10.1111/j.1365-2966.2009.14654.x)

(ref: Jullo:2007aa) Jullo, E., Kneib, J.-P., Limousin, M., et al. 2007, New Journal of Physics, 9, 447, doi: [`10.1088/1367-2630/9/12/447`](http://doi.org/10.1088/1367-2630/9/12/447)

(ref: Kalita:2025ac) Kalita, B. S., Silverman, J. D., Daddi, E., et al. 2025, MNRAS, 537, 402, doi: [`10.1093/mnras/staf031`](http://doi.org/10.1093/mnras/staf031)

(ref: Kamieneski:2024ab) Kamieneski, P. S. 2024, IAU Symposium, 381, 147, doi: [`10.1017/S174392132300368X`](http://doi.org/10.1017/S174392132300368X)

(ref: Kamieneski:2024aa) Kamieneski, P. S., Yun, M. S., Harrington, K. C., et al. 2024a, ApJ, 961, 2, doi: [`10.3847/1538-4357/acf930`](http://doi.org/10.3847/1538-4357/acf930)

(ref: Kamieneski:2024ac) Kamieneski, P. S., Frye, B. L., Windhorst, R. A., et al. 2024b, ApJ, 973, 25, doi: [`10.3847/1538-4357/ad5d59`](http://doi.org/10.3847/1538-4357/ad5d59)

(ref: Kankare:2008aa) Kankare, E., Mattila, S., Ryder, S., et al. 2008, ApJL, 689, L97, doi: [`10.1086/595820`](http://doi.org/10.1086/595820)

(ref: Kankare:2012aa) Kankare, E., Mattila, S., Ryder, S., et al. 2012, ApJL, 744, L19, doi: [`10.1088/2041-8205/744/2/L19`](http://doi.org/10.1088/2041-8205/744/2/L19)

(ref: Kankare:2021aa) Kankare, E., Efstathiou, A., Kotak, R., et al. 2021, A&A, 649, A134, doi: [`10.1051/0004-6361/202039240`](http://doi.org/10.1051/0004-6361/202039240)

(ref: Kauffmann:1999ab) Kauffmann, G., Colberg, J. M., Diaferio, A., & White, S. D. M. 1999, MNRAS, 307, 529, doi: [`10.1046/j.1365-8711.1999.02711.x`](http://doi.org/10.1046/j.1365-8711.1999.02711.x)

(ref: Keeton:2000aa) Keeton, C. R., Falco, E. E., Impey, C. D., et al. 2000, ApJ, 542, 74, doi: [`10.1086/309517`](http://doi.org/10.1086/309517)

(ref: Kelly:2015aa) Kelly, P. L., Rodney, S. A., Treu, T., et al. 2015, Science, 347, 1123, doi: [`10.1126/science.aaa3350`](http://doi.org/10.1126/science.aaa3350)

(ref: Kelly:2016aa) Kelly, P. L., Rodney, S. A., Treu, T., et al. 2016, ApJL, 819, L8, doi: [`10.3847/2041-8205/819/1/L8`](http://doi.org/10.3847/2041-8205/819/1/L8)

(ref: Kelly:2023ab) Kelly, P. L., Rodney, S., Treu, T., et al. 2023a, Science, 380, abh1322, doi: [`10.1126/science.abh1322`](http://doi.org/10.1126/science.abh1322)

(ref: Kelly:2023aa) Kelly, P. L., Rodney, S., Treu, T., et al. 2023b, ApJ, 948, 93, doi: [`10.3847/1538-4357/ac4ccb`](http://doi.org/10.3847/1538-4357/ac4ccb)

(ref: Kennicutt:1998ac) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: Kewley:2002ab) Kewley, L. J., Geller, M. J., Jansen, R. A., & Dopita, M. A. 2002, AJ, 124, 3135, doi: [`10.1086/344487`](http://doi.org/10.1086/344487)

(ref: Kim:2015aa) Kim, C.-G., & Ostriker, E. C. 2015, ApJ, 802, 99, doi: [`10.1088/0004-637X/802/2/99`](http://doi.org/10.1088/0004-637X/802/2/99)

(ref: Kneib:1996aa) Kneib, J.-P., Ellis, R. S., Smail, I., Couch, W. J., & Sharples, R. M. 1996, ApJ, 471, 643, doi: [`10.1086/177995`](http://doi.org/10.1086/177995)

(ref: Kneib:1993aa) Kneib, J. P., Mellier, Y., Fort, B., & Mathez, G. 1993, A&A, 273, 367

(ref: Kochanek:2006aa) Kochanek, C., Schneider, P., , & Wambsganss, J. 2006, Gravitational Lensing: Strong, Weak and Micro, 1st edn., ed. G. Meylan, P. Jetzer, & e. a. North, P., Saas-Fee Advanced Courses (Springer). [`https://arxiv.org/abs/astro-ph/0407232`](https://arxiv.org/abs/astro-ph/0407232)

(ref: Kochanek:2002aa) Kochanek, C. S. 2002, ApJ, 578, 25, doi: [`10.1086/342476`](http://doi.org/10.1086/342476)

(ref: Kochanek:2020ab) Kochanek, C. S. 2020, MNRAS, 493, 1725, doi: [`10.1093/mnras/staa344`](http://doi.org/10.1093/mnras/staa344)

(ref: Kool:2018aa) Kool, E. C., Ryder, S., Kankare, E., et al. 2018, MNRAS, 473, 5641, doi: [`10.1093/mnras/stx2463`](http://doi.org/10.1093/mnras/stx2463)

(ref: Koopmans:2003aa) Koopmans, L. V. E., Treu, T., Fassnacht, C. D., Blandford, R. D., & Surpi, G. 2003, ApJ, 599, 70, doi: [`10.1086/379226`](http://doi.org/10.1086/379226)

(ref: Kroupa:2001aa) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Lee:2021aa) Lee, A. J., Freedman, W. L., Madore, B. F., et al. 2021, ApJ, 907, 112, doi: [`10.3847/1538-4357/abd253`](http://doi.org/10.3847/1538-4357/abd253)

(ref: Leitet:2013aa) Leitet, E., Bergvall, N., Hayes, M., Linné, S., & Zackrisson, E. 2013, A&A, 553, A106, doi: [`10.1051/0004-6361/201118370`](http://doi.org/10.1051/0004-6361/201118370)

(ref: Levy:2024aa) Levy, R. C., Bolatto, A. D., Mayya, D., et al. 2024, ApJL, 973, L55, doi: [`10.3847/2041-8213/ad7af3`](http://doi.org/10.3847/2041-8213/ad7af3)

(ref: Lewis:2018aa) Lewis, A. J. R., Ivison, R. J., Best, P. N., et al. 2018, ApJ, 862, 96, doi: [`10.3847/1538-4357/aacc25`](http://doi.org/10.3847/1538-4357/aacc25)

(ref: Liang:2021aa) Liang, L., Feldmann, R., Hayward, C. C., et al. 2021, MNRAS, 502, 3210, doi: [`10.1093/mnras/stab096`](http://doi.org/10.1093/mnras/stab096)

(ref: Linden:2017aa) Linden, S. T., Evans, A. S., Rich, J., et al. 2017, ApJ, 843, 91, doi: [`10.3847/1538-4357/aa7266`](http://doi.org/10.3847/1538-4357/aa7266)

(ref: Liu:2019ae) Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235, doi: [`10.3847/1538-4357/ab578d`](http://doi.org/10.3847/1538-4357/ab578d)

(ref: Liu:2024ae) Liu, D., Förster Schreiber, N. M., Harrington, K. C., et al. 2024, Nature Astronomy, 8, 1181, doi: [`10.1038/s41550-024-02296-7`](http://doi.org/10.1038/s41550-024-02296-7)

(ref: Liu:2024af) Liu, Z., Silverman, J. D., Daddi, E., et al. 2024, ApJ, 968, 15, doi: [`10.3847/1538-4357/ad4096`](http://doi.org/10.3847/1538-4357/ad4096)

(ref: Long:2020aa) Long, A. S., Cooray, A., Ma, J., et al. 2020, ApJ, 898, 133, doi: [`10.3847/1538-4357/ab9d1f`](http://doi.org/10.3847/1538-4357/ab9d1f)

(ref: Lotz:2017aa) Lotz, J. M., Koekemoer, A., Coe, D., et al. 2017, ApJ, 837, 97, doi: [`10.3847/1538-4357/837/1/97`](http://doi.org/10.3847/1538-4357/837/1/97)

(ref: Louis:2025aa) Louis, T., La Posta, A., Atkins, Z., et al. 2025, arXiv e-prints, arXiv:2503.14452, doi: [`10.48550/arXiv.2503.14452`](http://doi.org/10.48550/arXiv.2503.14452)

(ref: LSST-Science-Collaboration:2009aa) LSST Science Collaboration, Abell, P. A., Allison, J., et al. 2009, arXiv e-prints, arXiv:0912.0201, doi: [`10.48550/arXiv.0912.0201`](http://doi.org/10.48550/arXiv.0912.0201)

(ref: Lucas:2020aa) Lucas, W. E., Bonnell, I. A., & Dale, J. E. 2020, MNRAS, 493, 4700, doi: [`10.1093/mnras/staa451`](http://doi.org/10.1093/mnras/staa451)

(ref: Madau:1998aa) Madau, P., della Valle, M., & Panagia, N. 1998, MNRAS, 297, L17, doi: [`10.1046/j.1365-8711.1998.01697.x`](http://doi.org/10.1046/j.1365-8711.1998.01697.x)

(ref: Madau:2014aa) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Magee:2023aa) Magee, M. R., Sainz de Murieta, A., Collett, T. E., & Enzi, W. 2023, arXiv e-prints, arXiv:2303.15439, doi: [`10.48550/arXiv.2303.15439`](http://doi.org/10.48550/arXiv.2303.15439)

(ref: Mannucci:2006aa) Mannucci, F., Della Valle, M., & Panagia, N. 2006, MNRAS, 370, 773, doi: [`10.1111/j.1365-2966.2006.10501.x`](http://doi.org/10.1111/j.1365-2966.2006.10501.x)

(ref: Mannucci:2005aa) Mannucci, F., Della Valle, M., Panagia, N., et al. 2005, A&A, 433, 807, doi: [`10.1051/0004-6361:20041411`](http://doi.org/10.1051/0004-6361:20041411)

(ref: Mannucci:2003aa) Mannucci, F., Maiolino, R., Cresci, G., et al. 2003, A&A, 401, 519, doi: [`10.1051/0004-6361:20030198`](http://doi.org/10.1051/0004-6361:20030198)

(ref: Mantynen:2025aa) Mäntynen, I., Kankare, E., Mattila, S., et al. 2025, arXiv e-prints, arXiv:2506.18518, doi: [`10.48550/arXiv.2506.18518`](http://doi.org/10.48550/arXiv.2506.18518)

(ref: Maoz:2014aa) Maoz, D., Mannucci, F., & Nelemans, G. 2014, ARA&A, 52, 107, doi: [`10.1146/annurev-astro-082812-141031`](http://doi.org/10.1146/annurev-astro-082812-141031)

(ref: Marti-Vidal:2007aa) Martı́-Vidal, I., Marcaide, J. M., Alberdi, A., et al. 2007, A&A, 470, 1071, doi: [`10.1051/0004-6361:20077522`](http://doi.org/10.1051/0004-6361:20077522)

(ref: Mattila:2001aa) Mattila, S., & Meikle, W. P. S. 2001, MNRAS, 324, 325, doi: [`10.1046/j.1365-8711.2001.04255.x`](http://doi.org/10.1046/j.1365-8711.2001.04255.x)

(ref: Mattila:2007aa) Mattila, S., Väisänen, P., Farrah, D., et al. 2007, ApJL, 659, L9, doi: [`10.1086/516821`](http://doi.org/10.1086/516821)

(ref: McKinney:2010aa) McKinney, W. 2010, in Proceedings of the 9th Python in Science Conference, ed. Stéfan van der Walt & Jarrod Millman, 56 – 61, doi: [`10.25080/Majora-92bf1922-00a`](http://doi.org/10.25080/Majora-92bf1922-00a)

(ref: McMullin:2007aa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: McQuinn:2012aa) McQuinn, K. B. W., Skillman, E. D., Dalcanton, J. J., et al. 2012, ApJ, 759, 77, doi: [`10.1088/0004-637X/759/1/77`](http://doi.org/10.1088/0004-637X/759/1/77)

(ref: Melinder:2012aa) Melinder, J., Dahlen, T., Mencı́a Trinchant, L., et al. 2012, A&A, 545, A96, doi: [`10.1051/0004-6361/201219364`](http://doi.org/10.1051/0004-6361/201219364)

(ref: Melo:2025aa) Melo, A., Cañameras, R., Schuldt, S., et al. 2025, A&A, 698, A264, doi: [`10.1051/0004-6361/202453195`](http://doi.org/10.1051/0004-6361/202453195)

(ref: Mengel:2002aa) Mengel, S., Lehnert, M. D., Thatte, N., & Genzel, R. 2002, A&A, 383, 137, doi: [`10.1051/0004-6361:20011704`](http://doi.org/10.1051/0004-6361:20011704)

(ref: Meurer:1999aa) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64, doi: [`10.1086/307523`](http://doi.org/10.1086/307523)

(ref: Miettinen:2017aa) Miettinen, O., Delvecchio, I., Smolčić, V., et al. 2017, A&A, 606, A17, doi: [`10.1051/0004-6361/201730762`](http://doi.org/10.1051/0004-6361/201730762)

(ref: Miley:2008aa) Miley, G., & De Breuck, C. 2008, A&ARv, 15, 67, doi: [`10.1007/s00159-007-0008-z`](http://doi.org/10.1007/s00159-007-0008-z)

(ref: Miller:2015aa) Miller, T. B., Hayward, C. C., Chapman, S. C., & Behroozi, P. S. 2015, MNRAS, 452, 878, doi: [`10.1093/mnras/stv1267`](http://doi.org/10.1093/mnras/stv1267)

(ref: Miller:2018ab) Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, Nature, 556, 469, doi: [`10.1038/s41586-018-0025-2`](http://doi.org/10.1038/s41586-018-0025-2)

(ref: Miluzio:2013aa) Miluzio, M., Cappellaro, E., Botticella, M. T., et al. 2013, A&A, 554, A127, doi: [`10.1051/0004-6361/201321192`](http://doi.org/10.1051/0004-6361/201321192)

(ref: Mitsuhashi:2024aa) Mitsuhashi, I., Tadaki, K.-i., Ikeda, R., et al. 2024, A&A, 690, A197, doi: [`10.1051/0004-6361/202348782`](http://doi.org/10.1051/0004-6361/202348782)

(ref: Mork:2025aa) Mork, S. D., Gladders, M. D., Khullar, G., et al. 2025, ApJ, 979, 184, doi: [`10.3847/1538-4357/ada24c`](http://doi.org/10.3847/1538-4357/ada24c)

(ref: Mortsell:2022aa) Mörtsell, E., Goobar, A., Johansson, J., & Dhawan, S. 2022a, ApJ, 933, 212, doi: [`10.3847/1538-4357/ac756e`](http://doi.org/10.3847/1538-4357/ac756e)

(ref: Mortsell:2022ab) Mörtsell, E., Goobar, A., Johansson, J., & Dhawan, S. 2022b, ApJ, 935, 58, doi: [`10.3847/1538-4357/ac7c19`](http://doi.org/10.3847/1538-4357/ac7c19)

(ref: Munoz:2022aa) Muñoz, J. A., Kochanek, C. S., Fohlmeister, J., et al. 2022, ApJ, 937, 34, doi: [`10.3847/1538-4357/ac8877`](http://doi.org/10.3847/1538-4357/ac8877)

(ref: Napier:2023aa) Napier, K., Sharon, K., Dahle, H., et al. 2023, ApJ, 959, 134, doi: [`10.3847/1538-4357/ad045a`](http://doi.org/10.3847/1538-4357/ad045a)

(ref: Narayan:1996aa) Narayan, R., & Bartelmann, M. 1996, ArXiv Astrophysics e-prints

(ref: Narayanan:2018ab) Narayanan, D., Davé, R., Johnson, B. D., et al. 2018, MNRAS, 474, 1718, doi: [`10.1093/mnras/stx2860`](http://doi.org/10.1093/mnras/stx2860)

(ref: Negrello:2010aa) Negrello, M., Hopwood, R., De Zotti, G., et al. 2010, Science, 330, 800, doi: [`10.1126/science.1193420`](http://doi.org/10.1126/science.1193420)

(ref: Negrello:2014aa) Negrello, M., Hopwood, R., Dye, S., et al. 2014, MNRAS, 440, 1999, doi: [`10.1093/mnras/stu413`](http://doi.org/10.1093/mnras/stu413)

(ref: Negrello:2017aa) Negrello, M., Amber, S., Amvrosiadis, A., et al. 2017, MNRAS, 465, 3558, doi: [`10.1093/mnras/stw2911`](http://doi.org/10.1093/mnras/stw2911)

(ref: Newman:2018aa) Newman, A. B., Belli, S., Ellis, R. S., & Patel, S. G. 2018, ApJ, 862, 125, doi: [`10.3847/1538-4357/aacd4d`](http://doi.org/10.3847/1538-4357/aacd4d)

(ref: Oguri:2007aa) Oguri, M. 2007, ApJ, 660, 1, doi: [`10.1086/513093`](http://doi.org/10.1086/513093)

(ref: Oguri:2010ac) Oguri, M., & Marshall, P. J. 2010, MNRAS, 405, 2579, doi: [`10.1111/j.1365-2966.2010.16639.x`](http://doi.org/10.1111/j.1365-2966.2010.16639.x)

(ref: Olivares:2016aa) Olivares, V., Treister, E., Privon, G. C., et al. 2016, ApJ, 827, 57, doi: [`10.3847/0004-637X/827/1/57`](http://doi.org/10.3847/0004-637X/827/1/57)

(ref: Osterbrock:2006aa) Osterbrock, D. E., & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei (University Science Books)

(ref: Oteo:2018aa) Oteo, I., Ivison, R. J., Dunne, L., et al. 2018, ApJ, 856, 72, doi: [`10.3847/1538-4357/aaa1f1`](http://doi.org/10.3847/1538-4357/aaa1f1)

(ref: Overzier:2016aa) Overzier, R. A. 2016, A&ARv, 24, 14, doi: [`10.1007/s00159-016-0100-3`](http://doi.org/10.1007/s00159-016-0100-3)

(ref: Palicio:2024aa) Palicio, P. A., Matteucci, F., Della Valle, M., & Spitoni, E. 2024, A&A, 689, A203, doi: [`10.1051/0004-6361/202449740`](http://doi.org/10.1051/0004-6361/202449740)

(ref: Pascale:2023ab) Pascale, M., Dai, L., McKee, C. F., & Tsang, B. T. H. 2023, ApJ, 957, 77, doi: [`10.3847/1538-4357/acf75c`](http://doi.org/10.3847/1538-4357/acf75c)

(ref: Pascale:2022aa) Pascale, M., Frye, B. L., Dai, L., et al. 2022, ApJ, 932, 85, doi: [`10.3847/1538-4357/ac6ce9`](http://doi.org/10.3847/1538-4357/ac6ce9)

(ref: Pascale:2025aa) Pascale, M., Frye, B. L., Pierel, J. D. R., et al. 2025, ApJ, 979, 13, doi: [`10.3847/1538-4357/ad9928`](http://doi.org/10.3847/1538-4357/ad9928)

(ref: Pavesi:2018aa) Pavesi, R., Riechers, D. A., Sharon, C. E., et al. 2018, ApJ, 861, 43, doi: [`10.3847/1538-4357/aac6b6`](http://doi.org/10.3847/1538-4357/aac6b6)

(ref: Perez-Torres:2021aa) Pérez-Torres, M., Mattila, S., Alonso-Herrero, A., Aalto, S., & Efstathiou, A. 2021, A&ARv, 29, 2, doi: [`10.1007/s00159-020-00128-x`](http://doi.org/10.1007/s00159-020-00128-x)

(ref: Perez-Torres:2009aa) Pérez-Torres, M. A., Romero-Cañizales, C., Alberdi, A., & Polatidis, A. 2009, A&A, 507, L17, doi: [`10.1051/0004-6361/200912964`](http://doi.org/10.1051/0004-6361/200912964)

(ref: Perrotta:2002aa) Perrotta, F., Baccigalupi, C., Bartelmann, M., De Zotti, G., & Granato, G. L. 2002, MNRAS, 329, 445, doi: [`10.1046/j.1365-8711.2002.05009.x`](http://doi.org/10.1046/j.1365-8711.2002.05009.x)

(ref: Pesce:2020aa) Pesce, D. W., Braatz, J. A., Reid, M. J., et al. 2020, ApJL, 891, L1, doi: [`10.3847/2041-8213/ab75f0`](http://doi.org/10.3847/2041-8213/ab75f0)

(ref: Petrushevska:2020aa) Petrushevska, T. 2020, Symmetry, 12, 1966, doi: [`10.3390/sym12121966`](http://doi.org/10.3390/sym12121966)

(ref: Petrushevska:2018ab) Petrushevska, T., Okamura, T., Kawamata, R., et al. 2018a, Astronomy Reports, 62, 917, doi: [`10.1134/S1063772918120272`](http://doi.org/10.1134/S1063772918120272)

(ref: Petrushevska:2016aa) Petrushevska, T., Amanullah, R., Goobar, A., et al. 2016, A&A, 594, A54, doi: [`10.1051/0004-6361/201628925`](http://doi.org/10.1051/0004-6361/201628925)

(ref: Petrushevska:2018aa) Petrushevska, T., Goobar, A., Lagattuta, D. J., et al. 2018b, A&A, 614, A103, doi: [`10.1051/0004-6361/201731552`](http://doi.org/10.1051/0004-6361/201731552)

(ref: Pierel:2019aa) Pierel, J. D. R., & Rodney, S. 2019, ApJ, 876, 107, doi: [`10.3847/1538-4357/ab164a`](http://doi.org/10.3847/1538-4357/ab164a)

(ref: Pierel:2021ab) Pierel, J. D. R., Rodney, S., Vernardos, G., et al. 2021, ApJ, 908, 190, doi: [`10.3847/1538-4357/abd8d3`](http://doi.org/10.3847/1538-4357/abd8d3)

(ref: Pierel:2023aa) Pierel, J. D. R., Arendse, N., Ertl, S., et al. 2023, ApJ, 948, 115, doi: [`10.3847/1538-4357/acc7a6`](http://doi.org/10.3847/1538-4357/acc7a6)

(ref: Pierel:2024aa) Pierel, J. D. R., Frye, B. L., Pascale, M., et al. 2024a, ApJ, 967, 50, doi: [`10.3847/1538-4357/ad3c43`](http://doi.org/10.3847/1538-4357/ad3c43)

(ref: Pierel:2024ab) Pierel, J. D. R., Newman, A. B., Dhawan, S., et al. 2024b, ApJL, 967, L37, doi: [`10.3847/2041-8213/ad4648`](http://doi.org/10.3847/2041-8213/ad4648)

(ref: Planck-Collaboration:2015aa) Planck Collaboration, Aghanim, N., Altieri, B., et al. 2015, A&A, 582, A30, doi: [`10.1051/0004-6361/201424790`](http://doi.org/10.1051/0004-6361/201424790)

(ref: Planck-Collaboration:2020aa) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6, doi: [`10.1051/0004-6361/201833910`](http://doi.org/10.1051/0004-6361/201833910)

(ref: Polletta:2023aa) Polletta, M., Nonino, M., Frye, B., et al. 2023, A&A, 675, L4, doi: [`10.1051/0004-6361/202346964`](http://doi.org/10.1051/0004-6361/202346964)

(ref: Polletta:2024ab) Polletta, M., Frye, B. L., Garuda, N., et al. 2024, A&A, 690, A285, doi: [`10.1051/0004-6361/202450671`](http://doi.org/10.1051/0004-6361/202450671)

(ref: Pontoppidan:2016aa) Pontoppidan, K. M., Pickering, T. E., Laidler, V. G., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9910, Observatory Operations: Strategies, Processes, and Systems VI, ed. A. B. Peck, R. L. Seaman, & C. R. Benn, 991016, doi: [`10.1117/12.2231768`](http://doi.org/10.1117/12.2231768)

(ref: Price:2014aa) Price, S. H., Kriek, M., Brammer, G. B., et al. 2014, ApJ, 788, 86, doi: [`10.1088/0004-637X/788/1/86`](http://doi.org/10.1088/0004-637X/788/1/86)

(ref: Puglisi:2016aa) Puglisi, A., Rodighiero, G., Franceschini, A., et al. 2016, A&A, 586, A83, doi: [`10.1051/0004-6361/201526782`](http://doi.org/10.1051/0004-6361/201526782)

(ref: Puglisi:2017aa) Puglisi, A., Daddi, E., Renzini, A., et al. 2017, ApJL, 838, L18, doi: [`10.3847/2041-8213/aa66c9`](http://doi.org/10.3847/2041-8213/aa66c9)

(ref: Quimby:2013aa) Quimby, R. M., Werner, M. C., Oguri, M., et al. 2013, ApJL, 768, L20, doi: [`10.1088/2041-8205/768/1/L20`](http://doi.org/10.1088/2041-8205/768/1/L20)

(ref: Quimby:2014aa) Quimby, R. M., Oguri, M., More, A., et al. 2014, Science, 344, 396, doi: [`10.1126/science.1250903`](http://doi.org/10.1126/science.1250903)

(ref: Reddy:2015aa) Reddy, N. A., Kriek, M., Shapley, A. E., et al. 2015, ApJ, 806, 259, doi: [`10.1088/0004-637X/806/2/259`](http://doi.org/10.1088/0004-637X/806/2/259)

(ref: Refsdal:1964aa) Refsdal, S. 1964, MNRAS, 128, 307, doi: [`10.1093/mnras/128.4.307`](http://doi.org/10.1093/mnras/128.4.307)

(ref: Reid:2009aa) Reid, M. J., Braatz, J. A., Condon, J. J., et al. 2009, ApJ, 695, 287, doi: [`10.1088/0004-637X/695/1/287`](http://doi.org/10.1088/0004-637X/695/1/287)

(ref: Reid:2013aa) Reid, M. J., Braatz, J. A., Condon, J. J., et al. 2013, ApJ, 767, 154, doi: [`10.1088/0004-637X/767/2/154`](http://doi.org/10.1088/0004-637X/767/2/154)

(ref: Remolina-Gonzalez:2020aa) Remolina González, J. D., Sharon, K., Reed, B., et al. 2020, ApJ, 902, 44, doi: [`10.3847/1538-4357/abb2a1`](http://doi.org/10.3847/1538-4357/abb2a1)

(ref: Riechers:2010aa) Riechers, D. A., Capak, P. L., Carilli, C. L., et al. 2010, ApJL, 720, L131, doi: [`10.1088/2041-8205/720/2/L131`](http://doi.org/10.1088/2041-8205/720/2/L131)

(ref: Riess:2022aa) Riess, A. G., Yuan, W., Macri, L. M., et al. 2022, ApJL, 934, L7, doi: [`10.3847/2041-8213/ac5c5b`](http://doi.org/10.3847/2041-8213/ac5c5b)

(ref: Robertson:2020ac) Robertson, A., Smith, G. P., Massey, R., et al. 2020, MNRAS, 495, 3727, doi: [`10.1093/mnras/staa1429`](http://doi.org/10.1093/mnras/staa1429)

(ref: Robertson:2024aa) Robertson, C., Holwerda, B. W., Young, J., et al. 2024, AJ, 167, 263, doi: [`10.3847/1538-3881/ad39c4`](http://doi.org/10.3847/1538-3881/ad39c4)

(ref: Robitaille:2019aa) Robitaille, T. 2019, APLpy v2.0: The Astronomical Plotting Library in Python, 2.0, Zenodo Zenodo, doi: [`10.5281/zenodo.2567476`](http://doi.org/10.5281/zenodo.2567476)

(ref: Robitaille:2012aa) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python,, Astrophysics Source Code Library [`http://ascl.net/1208.017`](http://ascl.net/1208.017)

(ref: Rodighiero:2011aa) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40, doi: [`10.1088/2041-8205/739/2/L40`](http://doi.org/10.1088/2041-8205/739/2/L40)

(ref: Rodney:2021ab) Rodney, S. A., Brammer, G. B., Pierel, J. D. R., et al. 2021, Nature Astronomy, doi: [`10.1038/s41550-021-01450-9`](http://doi.org/10.1038/s41550-021-01450-9)

(ref: Rodney:2016aa) Rodney, S. A., Strolger, L. G., Kelly, P. L., et al. 2016, ApJ, 820, 50, doi: [`10.3847/0004-637X/820/1/50`](http://doi.org/10.3847/0004-637X/820/1/50)

(ref: Roy:2024ae) Roy, N., Heckman, T., Henry, A., et al. 2024, arXiv e-prints, arXiv:2410.13254, doi: [`10.48550/arXiv.2410.13254`](http://doi.org/10.48550/arXiv.2410.13254)

(ref: Ruiter:2025aa) Ruiter, A. J., & Seitenzahl, I. R. 2025, A&ARv, 33, 1, doi: [`10.1007/s00159-024-00158-9`](http://doi.org/10.1007/s00159-024-00158-9)

(ref: Rujopakarn:2011aa) Rujopakarn, W., Rieke, G. H., Eisenstein, D. J., & Juneau, S. 2011, ApJ, 726, 93, doi: [`10.1088/0004-637X/726/2/93`](http://doi.org/10.1088/0004-637X/726/2/93)

(ref: Ryczanowski:2023aa) Ryczanowski, D., Smith, G. P., Bianconi, M., et al. 2023, MNRAS, 520, 2547, doi: [`10.1093/mnras/stad231`](http://doi.org/10.1093/mnras/stad231)

(ref: Safarzadeh:2017ab) Safarzadeh, M., Hayward, C. C., & Ferguson, H. C. 2017, ApJ, 840, 15, doi: [`10.3847/1538-4357/aa6c5b`](http://doi.org/10.3847/1538-4357/aa6c5b)

(ref: Sagues-Carracedo:2024aa) Sagués Carracedo, A., Goobar, A., Mörtsell, E., et al. 2024, arXiv e-prints, arXiv:2406.00052, doi: [`10.48550/arXiv.2406.00052`](http://doi.org/10.48550/arXiv.2406.00052)

(ref: Sainz-de-Murieta:2024aa) Sainz de Murieta, A., Collett, T. E., Magee, M. R., et al. 2024, MNRAS, 535, 2523, doi: [`10.1093/mnras/stae2486`](http://doi.org/10.1093/mnras/stae2486)

(ref: Sainz-de-Murieta:2023aa) Sainz de Murieta, A., Collett, T. E., Magee, M. R., et al. 2023, MNRAS, 526, 4296, doi: [`10.1093/mnras/stad3031`](http://doi.org/10.1093/mnras/stad3031)

(ref: Sakamoto:2013aa) Sakamoto, K., Aalto, S., Costagliola, F., et al. 2013, ApJ, 764, 42, doi: [`10.1088/0004-637X/764/1/42`](http://doi.org/10.1088/0004-637X/764/1/42)

(ref: Salpeter:1955aa) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Scannapieco:2005aa) Scannapieco, E., & Bildsten, L. 2005, ApJL, 629, L85, doi: [`10.1086/452632`](http://doi.org/10.1086/452632)

(ref: Schechter:2003aa) Schechter, P. L., Udalski, A., Szymański, M., et al. 2003, ApJ, 584, 657, doi: [`10.1086/345716`](http://doi.org/10.1086/345716)

(ref: Schmidt:1959aa) Schmidt, M. 1959, ApJ, 129, 243, doi: [`10.1086/146614`](http://doi.org/10.1086/146614)

(ref: Schneider:1985aa) Schneider, P. 1985, A&A, 143, 413

(ref: Schneider:1992aa) Schneider, P., Ehlers, J., & Falco, E. E. 1992, Gravitational Lenses (Springer-Verlag), 112, doi: [`10.1007/978-3-662-03758-4`](http://doi.org/10.1007/978-3-662-03758-4)

(ref: Schneider:2013aa) Schneider, P., & Sluse, D. 2013, A&A, 559, A37, doi: [`10.1051/0004-6361/201321882`](http://doi.org/10.1051/0004-6361/201321882)

(ref: Sedgwick:2025aa) Sedgwick, C., Serjeant, S., & Weiner, C. 2025, MNRAS, 539, 1077, doi: [`10.1093/mnras/staf414`](http://doi.org/10.1093/mnras/staf414)

(ref: Shapiro:1964aa) Shapiro, I. I. 1964, , 13, 789, doi: [`10.1103/PhysRevLett.13.789`](http://doi.org/10.1103/PhysRevLett.13.789)

(ref: Shim:2022aa) Shim, H., Lee, D., Kim, Y., et al. 2022, MNRAS, 514, 2915, doi: [`10.1093/mnras/stac1105`](http://doi.org/10.1093/mnras/stac1105)

(ref: Shu:2018ab) Shu, Y., Bolton, A. S., Mao, S., et al. 2018, ApJ, 864, 91, doi: [`10.3847/1538-4357/aad5ea`](http://doi.org/10.3847/1538-4357/aad5ea)

(ref: Shu:2021ab) Shu, Y., Bolton, A. S., Mao, S., et al. 2021, ApJ, 919, 67, doi: [`10.3847/1538-4357/ac24a4`](http://doi.org/10.3847/1538-4357/ac24a4)

(ref: Smartt:2009aa) Smartt, S. J. 2009, ARA&A, 47, 63, doi: [`10.1146/annurev-astro-082708-101737`](http://doi.org/10.1146/annurev-astro-082708-101737)

(ref: Smith:2018ac) Smith, B. M., Windhorst, R. A., Jansen, R. A., et al. 2018, ApJ, 853, 191, doi: [`10.3847/1538-4357/aaa3dc`](http://doi.org/10.3847/1538-4357/aaa3dc)

(ref: Smith:2020ab) Smith, B. M., Windhorst, R. A., Cohen, S. H., et al. 2020, ApJ, 897, 41, doi: [`10.3847/1538-4357/ab8811`](http://doi.org/10.3847/1538-4357/ab8811)

(ref: Smith:2024aa) Smith, B. M., Windhorst, R. A., Teplitz, H., et al. 2024, ApJ, 964, 73, doi: [`10.3847/1538-4357/ad1ef0`](http://doi.org/10.3847/1538-4357/ad1ef0)

(ref: Smith:2001aa) Smith, L. J., & Gallagher, J. S. 2001, MNRAS, 326, 1027, doi: [`10.1046/j.1365-8711.2001.04627.x`](http://doi.org/10.1046/j.1365-8711.2001.04627.x)

(ref: Smith:2012aa) Smith, M., Nichol, R. C., Dilday, B., et al. 2012, ApJ, 755, 61, doi: [`10.1088/0004-637X/755/1/61`](http://doi.org/10.1088/0004-637X/755/1/61)

(ref: Smolcic:2017ab) Smolčić, V., Miettinen, O., Tomičić, N., et al. 2017, A&A, 597, A4, doi: [`10.1051/0004-6361/201526989`](http://doi.org/10.1051/0004-6361/201526989)

(ref: Speagle:2014aa) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: Stanishev:2009aa) Stanishev, V., Goobar, A., Paech, K., et al. 2009, A&A, 507, 61, doi: [`10.1051/0004-6361/200911982`](http://doi.org/10.1051/0004-6361/200911982)

(ref: Strolger:2015aa) Strolger, L.-G., Dahlen, T., Rodney, S. A., et al. 2015, ApJ, 813, 93, doi: [`10.1088/0004-637X/813/2/93`](http://doi.org/10.1088/0004-637X/813/2/93)

(ref: Sullivan:2006aa) Sullivan, M., Le Borgne, D., Pritchet, C. J., et al. 2006, ApJ, 648, 868, doi: [`10.1086/506137`](http://doi.org/10.1086/506137)

(ref: Suyu:2024aa) Suyu, S. H., Goobar, A., Collett, T., More, A., & Vernardos, G. 2024, Space Sci. Rev., 220, 13, doi: [`10.1007/s11214-024-01044-7`](http://doi.org/10.1007/s11214-024-01044-7)

(ref: Suyu:2020aa) Suyu, S. H., Huber, S., Cañameras, R., et al. 2020, A&A, 644, A162, doi: [`10.1051/0004-6361/202037757`](http://doi.org/10.1051/0004-6361/202037757)

(ref: Swinbank:2004aa) Swinbank, A. M., Smail, I., Chapman, S. C., et al. 2004, ApJ, 617, 64, doi: [`10.1086/425171`](http://doi.org/10.1086/425171)

(ref: Tacconi:2018aa) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: Tadaki:2018aa) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613, doi: [`10.1038/s41586-018-0443-1`](http://doi.org/10.1038/s41586-018-0443-1)

(ref: Takata:2006aa) Takata, T., Sekiguchi, K., Smail, I., et al. 2006, ApJ, 651, 713, doi: [`10.1086/507985`](http://doi.org/10.1086/507985)

(ref: The-pandas-development-Team:2024aa) The pandas Development Team. 2024, pandas-dev/pandas: Pandas, v2.2.3 Zenodo, doi: [`10.5281/zenodo.3509134`](http://doi.org/10.5281/zenodo.3509134)

(ref: Timmons:2015aa) Timmons, N., Cooray, A., Nayyeri, H., et al. 2015, ApJ, 805, 140, doi: [`10.1088/0004-637X/805/2/140`](http://doi.org/10.1088/0004-637X/805/2/140)

(ref: Treu:2010aa) Treu, T. 2010, ARA&A, 48, 87, doi: [`10.1146/annurev-astro-081309-130924`](http://doi.org/10.1146/annurev-astro-081309-130924)

(ref: Treu:2016aa) Treu, T., & Marshall, P. J. 2016, A&ARv, 24, 11, doi: [`10.1007/s00159-016-0096-8`](http://doi.org/10.1007/s00159-016-0096-8)

(ref: Treu:2022ac) Treu, T., Suyu, S. H., & Marshall, P. J. 2022, A&ARv, 30, 8, doi: [`10.1007/s00159-022-00145-y`](http://doi.org/10.1007/s00159-022-00145-y)

(ref: Trombetti:2021ab) Trombetti, T., Burigana, C., Bonato, M., et al. 2021, A&A, 653, A151, doi: [`10.1051/0004-6361/202140830`](http://doi.org/10.1051/0004-6361/202140830)

(ref: Tsujimoto:1997aa) Tsujimoto, T., Yoshii, Y., Nomoto, K., et al. 1997, ApJ, 483, 228, doi: [`10.1086/304215`](http://doi.org/10.1086/304215)

(ref: Turner:1984aa) Turner, E. L., Ostriker, J. P., & Gott, III, J. R. 1984, ApJ, 284, 1, doi: [`10.1086/162379`](http://doi.org/10.1086/162379)

(ref: Umehata:2015aa) Umehata, H., Tamura, Y., Kohno, K., et al. 2015, ApJL, 815, L8, doi: [`10.1088/2041-8205/815/1/L8`](http://doi.org/10.1088/2041-8205/815/1/L8)

(ref: Urquhart:2022ab) Urquhart, S. A., Bendo, G. J., Serjeant, S., et al. 2022, MNRAS, 511, 3017, doi: [`10.1093/mnras/stac150`](http://doi.org/10.1093/mnras/stac150)

(ref: Vaisanen:2008aa) Väisänen, P., Mattila, S., Kniazev, A., et al. 2008, MNRAS, 384, 886, doi: [`10.1111/j.1365-2966.2007.12703.x`](http://doi.org/10.1111/j.1365-2966.2007.12703.x)

(ref: Varenius:2019aa) Varenius, E., Conway, J. E., Batejat, F., et al. 2019, A&A, 623, A173, doi: [`10.1051/0004-6361/201730631`](http://doi.org/10.1051/0004-6361/201730631)

(ref: Venemans:2007aa) Venemans, B. P., Röttgering, H. J. A., Miley, G. K., et al. 2007, A&A, 461, 823, doi: [`10.1051/0004-6361:20053941`](http://doi.org/10.1051/0004-6361:20053941)

(ref: Verde:2024aa) Verde, L., Schöneberg, N., & Gil-Marı́n, H. 2024, ARA&A, 62, 287, doi: [`10.1146/annurev-astro-052622-033813`](http://doi.org/10.1146/annurev-astro-052622-033813)

(ref: Vernardos:2024aa) Vernardos, G., Sluse, D., Pooley, D., et al. 2024, Space Sci. Rev., 220, 14, doi: [`10.1007/s11214-024-01043-8`](http://doi.org/10.1007/s11214-024-01043-8)

(ref: Wambsganss:1994aa) Wambsganss, J., & Paczynski, B. 1994, AJ, 108, 1156, doi: [`10.1086/117144`](http://doi.org/10.1086/117144)

(ref: Wang:2024ab) Wang, Q. D., Diaz, C. G., Kamieneski, P. S., et al. 2024, MNRAS, 527, 10584, doi: [`10.1093/mnras/stad3827`](http://doi.org/10.1093/mnras/stad3827)

(ref: Wang:2022ac) Wang, T.-M., Magnelli, B., Schinnerer, E., et al. 2022, A&A, 660, A142, doi: [`10.1051/0004-6361/202142299`](http://doi.org/10.1051/0004-6361/202142299)

(ref: Wang:2025an) Wang, X., Teplitz, H. I., Smith, B. M., et al. 2025, ApJ, 980, 74, doi: [`10.3847/1538-4357/ada4ab`](http://doi.org/10.3847/1538-4357/ada4ab)

(ref: Wardlow:2013aa) Wardlow, J. L., Cooray, A., De Bernardis, F., et al. 2013, ApJ, 762, 59, doi: [`10.1088/0004-637X/762/1/59`](http://doi.org/10.1088/0004-637X/762/1/59)

(ref: Watkins:2023aa) Watkins, E. J., Barnes, A. T., Henny, K., et al. 2023, ApJL, 944, L24, doi: [`10.3847/2041-8213/aca6e4`](http://doi.org/10.3847/2041-8213/aca6e4)

(ref: Weiss:2013aa) Weiss, A., De Breuck, C., Marrone, D. P., et al. 2013, ApJ, 767, 88, doi: [`10.1088/0004-637X/767/1/88`](http://doi.org/10.1088/0004-637X/767/1/88)

(ref: Whitaker:2017aa) Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ, 850, 208, doi: [`10.3847/1538-4357/aa94ce`](http://doi.org/10.3847/1538-4357/aa94ce)

(ref: Whitaker:2012aa) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: Whitaker:2014ab) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104, doi: [`10.1088/0004-637X/795/2/104`](http://doi.org/10.1088/0004-637X/795/2/104)

(ref: Whitmore:2010aa) Whitmore, B. C., Chandar, R., Schweizer, F., et al. 2010, AJ, 140, 75, doi: [`10.1088/0004-6256/140/1/75`](http://doi.org/10.1088/0004-6256/140/1/75)

(ref: Wild:2011aa) Wild, V., Charlot, S., Brinchmann, J., et al. 2011, MNRAS, 417, 1760, doi: [`10.1111/j.1365-2966.2011.19367.x`](http://doi.org/10.1111/j.1365-2966.2011.19367.x)

(ref: Windhorst:2023aa) Windhorst, R. A., Cohen, S. H., Jansen, R. A., et al. 2023, AJ, 165, 13, doi: [`10.3847/1538-3881/aca163`](http://doi.org/10.3847/1538-3881/aca163)

(ref: Witt:2000ab) Witt, H. J., Mao, S., & Keeton, C. R. 2000, ApJ, 544, 98, doi: [`10.1086/317201`](http://doi.org/10.1086/317201)

(ref: Witt:1995ab) Witt, H. J., Mao, S., & Schechter, P. L. 1995, ApJ, 443, 18, doi: [`10.1086/175499`](http://doi.org/10.1086/175499)

(ref: Wojtak:2019aa) Wojtak, R., Hjorth, J., & Gall, C. 2019, MNRAS, 487, 3342, doi: [`10.1093/mnras/stz1516`](http://doi.org/10.1093/mnras/stz1516)

(ref: Wong:2020aa) Wong, K. C., Suyu, S. H., Chen, G. C. F., et al. 2020, MNRAS, 498, 1420, doi: [`10.1093/mnras/stz3094`](http://doi.org/10.1093/mnras/stz3094)

(ref: Wright:2006aa) Wright, E. L. 2006, PASP, 118, 1711, doi: [`10.1086/510102`](http://doi.org/10.1086/510102)

(ref: Yan:2018aa) Yan, H., Ma, Z., Beacom, J. F., & Runge, J. 2018, ApJ, 867, 21, doi: [`10.3847/1538-4357/aadf38`](http://doi.org/10.3847/1538-4357/aadf38)

(ref: Young:2008aa) Young, D. R., Smartt, S. J., Mattila, S., et al. 2008, A&A, 489, 359, doi: [`10.1051/0004-6361:20078662`](http://doi.org/10.1051/0004-6361:20078662)

(ref: Zwicky:1938aa) Zwicky, F. 1938, ApJ, 88, 529, doi: [`10.1086/144007`](http://doi.org/10.1086/144007)

[^1]: To be clear, this technique does not rely on the nature of SNe Ia as “standardizable candles" like other late-Universe efforts (although this property may assist in more objectively assessing the accuracy of various lens models; (cite: Pascale:2025aa)).

    Supernovae are simply a useful transient source by which time delays may be measured, revealing the underlying cosmology.

[^2]: Here, “live" glSNe draws a distinction from those discovered after the supernova has faded in all images, only apparent through its disappearance in a second epoch of observation, and therefore not suitable for monitoring to infer $H_0$.

[^3]: This uncertainty can be very roughly approximated as the fraction of a galaxy’s star-forming area that is within the 1$\sigma$ uncertainty on the caustic’s location, multiplied by the relative change in multiplicity on either side of the caustic.

    In a canonical case of a galaxy straddling a caustic curve separating regions of double- vs. quad-imaging, this would be $\Delta N = 2$ from the $N=2$ to $N=4$ region, with average $N\sim 3$.

    For a source-plane positional uncertainty of $\sim 0.1\ensuremath{''}$ and a typical source-plane size of $\sim 0.4\ensuremath{''}$ for PASSAGES (cite: Kamieneski:2024aa), the typical uncertainty thus becomes $\sigma_{\mathcal{N}_{\rm eff}} / \mathcal{N}_{\rm eff} \sim (0.1/0.4) \cdot (4-2) / 3 \sim 20\%$.

[^4]: Note the different definition from (cite: Whitaker:2017aa) for $f_{\rm obsc}$, which also differs in their computation of SFR$_{\rm IR}$ using a calibration from UV and 24$\mu$m photometry (cite: Whitaker:2014ab).

[^5]: For completeness, a (cite: Chabrier:2003aa) IMF integrated over the same progenitor mass ranges gives $k_{\rm CC} = 0.0110~M_\odot^{-1}$, closer to that for the Kroupa IMF. However, since converting from a Salpeter to Chabrier IMF also lowers the SFR by a factor of 0.63 (cite: Madau:2014aa), the resulting $R_{\rm CC} = 0.0069 \cdot {\rm SFR}_{\rm Salpeter}$, thus certainly consistent within uncertainties.

[^6]: To minimize confusion, we use $\mathcal{R}$ when referring to what we define as the observable rate, and simply $R$ when referring to an intrinsic, rest-frame rate.

[^7]: As noted in Table [1](#tab:computations), for two exceptions we use the direct measurements of $f_{\rm unobsc}$ that are available for PJ0116-24 (cite: Liu:2024ae) and PJ1127+42 (cite: Frye:2024aa).

[^8]: In principle, lensing-corrected rest-frame $K$-band luminosity may correlate with stellar mass (e.g., (cite: Jarrett:2013aa)) and could be determined for $z\sim 2$ with WISE at 4.6$\mu$m, for example. However, there is likely significant differential magnification between the stellar continuum and dust continuum, and measuring the magnification factors for the rest-frame near-IR is beyond the scope of this work.

[^9]: Dividing $\mathcal{R}_{\rm Ia,obs}$ by the obscured fraction in this version reduces the relative uncertainties and thus makes it easier to interpret. Given that $R_{\rm Ia}$ is dominated by the SFR, we expect the SNe Ia to be subject to roughly the same average attenuation as the CCSNe, but few works have yet examined this at these redshifts.

[^10]: Here, this rate still accounts for $R_{\rm CC}$ and $R_{\rm Ia}$ being modulated by $(1+z)^{-1}$ time dilation, but not by $f_{\rm unobsc}$, to allow for a more direct comparison with literature values.

[^11]: Sensitivity is estimated with the JWST Exposure Time Calculator (cite: Pontoppidan:2016aa).

</paper>

Write the methods card for this paper.