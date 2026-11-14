# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025PASJ...77..432U\sonnetcc\reply.txt

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
 "bibcode": "2025PASJ...77..432U",
 "title": "ADF22-WEB: A giant barred spiral starburst galaxy in the z = 3.1 SSA22 protocluster core",
 "year": 2025,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Umehata, Hideki",
 "n_authors": 18,
 "arxiv_id": "2410.22155",
 "doi": "10.1093/pasj/psaf010",
 "alma_projects_linked_by_archive": [
  "2019.1.00008.S",
  "2021.1.00041.S",
  "2021.1.00071.S",
  "2021.1.01406.S",
  "2022.1.00223.S"
 ]
}
```

Paper text:
<paper>
# ADF22-WEB: A giant barred spiral starburst galaxy in the $z=3.1$ SSA22 protocluster core

## Abstract

In the present-day universe, the most massive galaxies are ellipticals located in the cores of galaxy clusters, harboring the heaviest super-massive black holes (SMBHs). However the mechanisms that drive the early growth phase and subsequent transformation of these morphology and kinematics of galaxies remain elusive. Here we report (sub)kiloparsec scale observations of stars, gas, and dust in ADF22.A1, a bright dusty starburst galaxy at $z=3.1$, hosting a heavily obscured active galactic nucleus and residing in a proto-cluster core. ADF22.A1 is a giant spiral galaxy with the kinematics of a rotating disk with rotation velocity $V_{\rm rot}=530\pm10$ km s$^{-1}$ and diameter $>30$ kpc. The high specific stellar angular momentum of this system, $j_*=3400\pm600$ kpc km s$^{-1}$, requires a mechanism to effectively spin-up ADF22.A1, indicating the importance of accretion from the cosmic web to supply both gas and angular momentum to galaxies in their early gas-rich starburst phase. In its inner region, gas flows along dust lanes in a bar connected with the bright dusty core and the estimated mass ratio of a bulge to SMBH matches the local relation, suggesting that bars are a key mechanism to shape the early co-evolution of these components. Comparison with cosmological simulations shows that ADF22.A1 will likely evolve into a massive elliptical at the present day, experiencing a significant reduction in angular momentum associated with subsequent galaxy mergers.

Institute for Advanced Research, Nagoya University, Furocho, Chikusa, Nagoya 464-8602, Japan Department of Physics, Graduate School of Science, Nagoya University, Furocho, Chikusa, Nagoya 464-8602, Japan

Cahill Center for Astronomy and Astrophysics, California Institute of Technology, MS249-17, Pasadena, CA91125, USA

Centre for Extragalactic Astronomy, Department of Physics, Durham University, South Road, Durham DH1 3LE, UK

Department of Astronomy and Astrophysics, The Pennsylvania State University, 525 Davey Lab, University Park, PA 16802, USA

School of Mathematics, Statistics and Physics, Newcastle University, Newcastle upon Tyne, NE1 7RU, UK

Department of Physics, University of Arkansas, 226 Physics Building, 825 West Dickson Street, Fayetteville, AR 72701, USA

National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan

Department of Astronomical Science, The Graduate University for Advanced Studies, SOKENDAI, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan

Astronomical Institute, Tohoku University, 6-3, Aramaki, Aoba, Sendai, Miyagi, 980-8578, Japan

Institute of Astronomy, Graduate School of Science, The University of Tokyo, 2-21-1 Osawa, Mitaka, Tokyo 181-0015, Japan

Research Center for the Early Universe, Graduate School of Science, The University of Tokyo, 7-3-1 Hongo, Bunkyo-ku, Tokyo 113-0033, Japan

European Southern Observatory (ESO), Karl-Schwarzschild-Strasse 2, D-85748 Garching, Germany School of Cosmic Physics, Dublin Institute for Advanced Studies, 31 Fitzwilliam Place, Dublin D02 XF86, Ireland Institute for Astronomy, University of Edinburgh, Royal Observatory, Blackford Hill, Edinburgh EH9 3HJ, UK ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D)

Faculty of Global Interdisciplinary Science and Innovation, Shizuoka University, 836 Ohya, Suruga-ku, Shizuoka 422-8529, Japan

Waseda Research Institute for Science and Engineering, Faculty of Science and Engineering, Waseda University, 3-4-1 Okubo, Shinjuku, Tokyo 169-8555, Japan

# Introduction

One of the fundamental correlations observed in galaxy evolution is the morphology-density relation. It is known that the cores of clusters in the local universe are populated by the oldest and most massive elliptical galaxies, while spiral galaxies are more common in the surrounding low-density environments ((cite: 1980ApJ...236..351D)).

In addition to their stellar populations, supermassive black holes (SMBHs) are known to be hosted by these galaxies, provides an important clue.

An important observational result that links the central SMBH with the host galaxy is a tight correlation between the mass of the central black hole, $M_\mathrm{BH}$, and the mass of the host galaxy’s bulge (e.g., (cite: 1998AJ....115.2285M); (cite: 2013ARA&A..51..511K)). This relation suggests a co-evolutionary pathway, where the growth of the SMBH and the host galaxy are regulated by common processes.

The connection between the environment and these galaxy populations showcases that environment play a key role in the formation and evolution of galaxies.

Recent observations and theoretical models suggest that the progenitors of massive ellipticals observed in the local Universe have formed most of their stars at high redshift ($z \gtrsim 2$) ((cite: 2005ApJ...621..673T); (cite: 2006MNRAS.366..499D)). Dusty star-forming galaxies (DSFGs), characterized by intense star formation and significant dust obscuration (for a review, (cite: 2014PhR...541...45C)), are plausible progenitors ((cite: 2014ApJ...782...68T); (cite: 2016ApJ...824...36C)).

DSFGs often harbor active galactic nuclei (AGNs), which suggests that DSFGs also exhibit the growth phase of SMBHs (e.g., (cite: 2005ApJ...632..736A)).

In the last decades, several works reported the co-existence of DSFGs and proto-clusters at $z\sim3-4$ based on interferometric observations (e.g., (cite: 2009ApJ...694.1517D); (cite: 2015ApJ...815L...8U); (cite: 2016ApJ...828...56W); (cite: 2018ApJ...856...72O); (cite: 2018Natur.556..469M)).

The SSA22 proto-cluster at $z=3.09$ is one of the most remarkable overdensity at $z>2$ ((cite: 1998ApJ...492..428S); (cite: 2004AJ....128.2073H); (cite: 2012AJ....143...79Y)) and offers one of the best targets to investigate the early formation of massive galaxies and the environmental dependence.

On top of single-dish surveys prior to the launch of the Atacama Large Millimeter/submillimeter Array (ALMA) ((cite: 2004ApJ...611..725B); (cite: 2005MNRAS.363.1398G); (cite: 2005ApJ...622..772C); (cite: 2009Natur.459...61T); (cite: 2014MNRAS.440.3462U)), (cite: 2015ApJ...815L...8U) (see also (cite: 2019Sci...366...97U)) discovered that 16 DSFGs and 6 X-ray selected AGNs with $z_{\rm spec}\approx3.09$ are concentrated into the proto-cluster core, utilizing the contiguous 1mm mapping of the $2^{\prime\prime}\times3^{\prime\prime}$ core region. This was the first discovery of the tight connection between such a large number of DSFGs/AGNs and proto-clusters in the early universe free from source confusion. The ALMA mosaic field is called as the ALMA Deep Field in SSA22 (ADF22) ((cite: 2015ApJ...815L...8U); (cite: 2017ApJ...835...98U)).

ADF22.A1 at $z_{\rm spec}=3.09$ is the brightest DSFG in ADF22 situated within a large-scale Ly $\alpha$ filament extending over several Mpc ((cite: 2019Sci...366...97U)). It is also the most luminous X-ray source in the field, hosting an intrinsically bright yet heavily obscured AGN ((cite: 2010ApJ...724.1270T); (cite: 2023ApJ...951...15M)). As such, ADF22.A1 offers a unique laboratory for exploring how the most massive galaxies and supermassive black holes (SMBHs) accumulate their mass, acquire their morphology, and undergo the transformations that ultimately evolve them into the most massive elliptical galaxies observed at $z=0$.

For years our understanding of the structure of the galaxy has been hampered in the past because of heavy dust extinction affecting its rest-frame UV appearance ((cite: 2010ApJ...724.1270T); (cite: 2014MNRAS.440.3462U)). However, with the advent of the James Webb Space Telescope (JWST) and ALMA, we can now resolve its structure and kinematics, providing unprecedented insights into the physical processes shaping the evolution of massive galaxies.

We adopt a standard concordance cosmology with $H_0=70$ km s$^{-1}$,Mpc$^{-1}$, $\Omega_{\rm m}=0.30$, and $\Omega_\lambda=0.70$. Here $H_0$ is the Hubble constant. $\Omega_{\rm m}$ and $\Omega_\lambda$ are the matter density and dark energy density at the present time, respectively.

This gives a scale of 7.63 kpc per arcsec at $z=3.09$.

# Observation and data reduction

![](figures/Fig1.pdf)

## JWST NIRCam imaging

The NIRCam imaging observation was performed on October 15 in 2023 as part of a JWST Cycle-2 program (PI Umehata, GO 3547) designed to cover ADF22, including ADF22.A1, with four filters (F115W, F200W, F356W, and F444W). The exposure time for each filter was 1869 sec. We used the STANDARD subpixel dither pattern, while no primary dither was applied. We used the MEDIUM8 readout mode.

Data reduction was performed using the JWST calibration pipeline (v.1.8.4), following the recipe provided by the CEERS team (cite: 2023ApJ...946L..12B). We applied “snowball” removal, wisp subtraction and “1/f” noise subtraction in addition to the standard reduction.

The 5$\sigma$ limiting magnitudes for a 0.1$^{\prime\prime}$ radius aperture are 29.01, 29.15, 29.49, and 29.00 AB mag for F115W, F200W, F356W, and F444W, respectively. The point spread function (PSF) of each image was matched to that of the F444W image.

We refer to the joint ALMA-JWST effort within the proto-cluster core as “ADF22-WEB”.

## ALMA observations

The \[C ii\] emission was observed using ALMA Band-8 as part of two ALMA observing programs. The main program, to obtain a high angular resolution map of ADF22.A1, was carried out in April to June 2022 during the Cycle-8 project (PI Umehata, 2021.1.01406.S). The array configurations of C43-2 and C43-5 were utilized to achieve both high angular resolution as well as sensitivity to spatially extended emission. The on-source times were 11 min and 39 min, respectively. The precipitable water vapour (PWV) was typically 0.4 mm. Two spectral windows of 1.875 GHz bandwidth (with dual polarization) centered at 463.822 and 465.663 GHz were employed.

Data reduction was performed using version 6.5.0. of the Common Astronomy Software Applications (CASA) package. After continuum subtraction the data were mapped with the tclean task, adopting Briggs weighting (robust = 0.5). This yielded a synthesized beam $0.23^{\prime\prime}\times0.17^{\prime\prime}$ at a position angle of 78 deg. The typical noise level is $1\sigma=0.47$ mJy beam$^{-1}$ per 80 km s$^{-1}$ channel.

The parameters of the observations are summarized in Table [\[table:observation_summary\]](#table:observation_summary), which also includes details of other observations described below.

As a part of the ALMA Cycle-8 project (PI, Umehata, 2021.1.00041.S), \[C ii\] emission in ADF22.A1 was also observed in ALMA Band-8 in the C43-2 configuration in April 2022. The total on-source time was 18 min, adopting the same correlator set-ups as the project above. Imaging used the the tclean task adopting natural weighting and uvtaper=0.75$^{\prime\prime}$, to trace extended emission, was performed, combining all 29-minutes data taken with the C43-2 configuration in this project and the one above. The cube has a synthesized beam size of $0.92^{\prime\prime}\times0.84^{\prime\prime}$ with position angle 74 deg. The typical noise level is $1\sigma=0.8$ mJy beam$^{-1}$ per 80 km s$^{-1}$ channel.

As a part of the ALMA Cycle-9 project (PI Umehata, 2022.1.00223.S), dust continuum emission in ADF22.A1 was observed in ALMA Band 8. The C43-7 configuration was used in June 2023. The total on-source time was 64 min. The image has representative frequency of 476.667 GHz (630 $\mu$m).

The cube has a synthesized beam size of $0.078^{\prime\prime}\times0.062^{\prime\prime}$ with position angle -67 deg. The typical noise level is $1\sigma=0.23$ mJy beam$^{-1}$. This image was used to obtain a high-resolution dust continuum map.

ALMA Band-7 observations to map the 870 $\mu$m continuum were performed as a part of the Cycle-8 project (PI.Umehata, 2021.1.00071.S). The C43-3 and C43-6 array configurations were utilized in May and July in 2022, achieving on-source time of 8 min and 21 min, respectively. The correlator was set up with two spectral windows of 1.875 GHz bandwidth (dual polarization) each per sideband. The spectral windows had central frequencies of 336.5, 338.4, 348.5, and 350.5 GHz, respectively.

Data reduction was performed using version casa 6.5.0, mapped with the tclean task, adopting natural weighting to yield a synthesized beam $0.21^{\prime\prime}\times0.20^{\prime\prime}$ with position angle 78 deg. Typical noise level is $1\sigma=21$ $\mu$Jy beam$^{-1}$.

Finally, ALMA Band-6 observations to map the 1.1 mm dust continuum were carried out in August 2021 as a part of the Cycle-7 project (PI Umehata, 2019.1.00008.S). The array configuration was C43-8 and the total integration time was 31 min. The four spectral windows had central frequencies of 253.0, 254.8, 267.0, 269.0 GHz.

Data reduction was performed using version 6.1.0. of the casa package. The continuum image was created using the line-free channels with the the tclean task. In the case of natural weighting, the resulting synthesized beam size is $0.042^{\prime\prime}\times0.042^{\prime\prime}$ with position angle $-4$ deg. The r.m.s. noise level is $1\sigma=12$ $\mu$Jy beam$^{-1}$. In the case of adopting natural weighting with uvtaper=0.038$^{\prime\prime}$, the resulting synthesized beam size is $0.079^{\prime\prime}\times0.072^{\prime\prime}$ with position angle $-81$ deg. The r.m.s. noise level is $1\sigma=18$ $\mu$Jy beam$^{-1}$. The tapered image is used in figures throughout the paper, while the original natural weighting image is utilized to measure the size of the dusty core.

## JVLA observation

The CO(1–0) line at $z=3.09$ falls in the Ka-band of the Karl G. Jansky Very Large Array (JVLA). Observations were carried out over winter 2016 to summer 2021 in two programs (PI, Umehata, 16A-357, 21A-346).

We utilized the Wideband Interferometric Digital Architecture (WIDAR) correlator with 8-bit samplers. A continuous frequency range of $32.67-33.70$ GHz and $27.67-28.70$ GHz, which allowed us to observe the CO(1–0) line at the redshift range of $z=2.42-2.53$ and $z=3.02-3.17$ covering the $z=3.1$ proto-cluster.

The array configurations of C, CnB, and D were utilized to accumulate the total on-source time was 24 hours.

The calibration was accomplished using the standard casa pipeline for VLA (version 6.1.2.7). All the $uv$-data were combined into a single data set. The data were mapped using tclean in casa with robust 2.0 weighting. The resulting synthesized beam size is $3.23^{\prime\prime}\times2.55^{\prime\prime}$ with position angle $-9$ deg. The achieved r.m.s. level per 100 km s$^{-1}$ velocity channel is $30-40$ $\mu$Jy beam$^{-1}$ at $28.0-28.4$ GHz.

## Astrometry

The astrometric accuracy of the ALMA images and cubes depends on (i) the S/N of the source and (ii) the quality of phase referencing and the positional uncertainty of the phase calibrator. First we measure the centroid of the phase calibrator J2226–0052 using the observed 870 $\mu$m image, and confirm that the source position is matched within 1 mas in the International Celestial Reference System (ICRS). Then we adopt the nominal positional accuracy for a compact source of 11 mas, for the Band-7 data, which is derived by ${\rm pos}_{\rm acc}\approx {\rm beam}_{\rm FWHM}/{\rm SNR}/0.9$, where ${\rm beam}_{\rm FWHM}$ is the FWHM of the synthesized beam, SNR is the signal-to-noise ratio (up to 20), and 0.9 is a factor to account for a nominal 10% signal decorrelation (ALMA technical Handbook and references therein).

The JWST/NIRCam observation is not a mosaic but a single field observation. The limited spatial coverage of the NIRCam image means only a small number of Gaia stars are available. This makes it challenging to derive accurate absolute coordinates. Here our purpose is matching the JWST coordinate system with that of ALMA. We first align the four-band NIRCam images to each other, matching with Gaia stars. Then we perform the emission profile fit for ALMA 870 $\mu$m and NIRCam F444W images in a manner described in $\S 7$ also for other DSFGs in the field (H. Umehata et al. in preparation, for more details). We matched the ALMA and JWST images minimizing the systematic offsets between the peaks measured with the both images. Consequently both images match within a pixel scale of the JWST F444W image (0.063$^{\prime\prime}$ pix$^{-1}$).

# Analysis and Results

## Resolved views in stellar, gas, and dust components

The JWST/NIRCam images trace the rest-frame optical-to-near-infrared wavelengths, have resolved the main stellar components at 0.2$^{\prime\prime}$ resolution (1.5 kpc at $z=3.1$). Our images uncover spiral structure in the galaxy (Fig. [1](#fig:almamap)a).

The 870 $\mu$m dust continuum and emission in the fine-structure line of singly ionized carbon (\[C ii\] 158 $\mu$m) at kiloparsec resolution. These observations resolve the distribution and kinematics of the cold interstellar medium (ISM) in the young spiral galaxy.

As shown in Fig. [1](#fig:almamap)b, the resolved dust continuum image uncovered that active star-formation activity, accompanied with significant dust production, occurs not only at the galactic center but across the whole disk.

The \[C ii\] intensity distribution broadly traces the stellar light, suggesting spiral arms (Fig. [1](#fig:almamap)c, see also Fig. [11](#fig:bar_summary)). The velocity field is characteristic of a regularly rotating disk in ADF22.A1, while non-circular motions cause a twisted pattern at the center (Fig. [1](#fig:almamap)d).

## Panchromatic SED Fit

![](figures/Fig2.pdf)

Total flux densities of ADF22.A1 in the NIRCam images were measured with an elliptical aperture, which yields $<0.24$, $1.89\pm0.15$, $7.34\pm0.04$, $13.5\pm0.24$ $\mu$Jy for F115W, F200W, F356W, and F444W, respectively. We measure 870 $\mu$m flux density $S_{\rm 870}=15.5\pm0.6$ mJy based on a curve growth method.

The X-ray-to-IR spectral energy distributions (SEDs) of ADF22.A1, except for these new measurements, were previously fit with the SED-fitting code lightning ((cite: 2023ApJ...951...15M)). This code allows us to simultaneously constrain emission from star-formation heated dust and AGN dust emission. We improve the fit by including the NIRCam and ALMA measurements.

The new best-fit SED model and the probability distribution function for key parameters are shown in Fig. [2](#fig:lightning). The fit yields SFR=$610_{-270}^{+340}$ M$_\odot$ yr$^{-1}$, log($M_*$/M$_\odot$)=11.4$^{+0.1}_{-0.2}$, log($M_{\rm BH}$/M$_\odot$)=8.5$^{+0.2}_{-0.3}$, and log $\lambda_{\rm Edd}$=$-0.9^{-0.4}_{-0.3}$, where $\lambda_{\rm Edd}$ is the Eddington ratio. The estimates are generally consistent with the previous ones.

## Profile Fit

![](figures/Fig3.pdf)

![](figures/Fig4.pdf)

We performed Sérsic profile fitting using the F444W image using galfit ((cite: 2002AJ....124..266P); ). The image traces the rest-frame near-infrared emission around 1 $\mu$m, which is expected to be sensitive to stellar mass distribution.

The best-fit model and residula images are shown in Fig. [3](#fig:galfit).

This best-fit model has an effective radius $r_{\rm e, F444w}=7.0\pm0.1$ kpc and Sérsic index $n=1.7\pm0.1$.

We compare the measured size of the stellar emission with other works based on JWST NIRcam observation and simulations in Fig. [4](#fig:z_size). It has been known that there is a trend between the galaxy size and stellar mass ((cite: 2014ApJ...788...28V)). For a fair comparison, we here focus on works which uses the rest-frame optical-to-near infrared wavelengths proved with JWST images (or simulations for JWST). The size-mass relation derived based on the NIRCam images taken with the CEERS survey was measured ((cite: 2024ApJ...962..176W)), which provides a suitable comparison sample (note that most of their samples are based on photometric redshifts). We plot the derived effective radius for each redshift bin, adopting $M_*=2\times10^{11}$ M$_\odot$, which is equivalent to the stellar mass of ADF22.A1. We note that we use the relation for star-forming galaxies in this work, while they discuss both star-forming galaxies and passive galaxies separately.

The result of mock observations of TNG50 simulations are also shown, adopting the same stellar mass ((cite: 2023ApJ...946...71C)). The best-fit functions for the observation and simulation are $r_{\rm eff}/{\rm kpc}=11.2\times(1+z)^{-0.74}$ and $r_{\rm eff}/{\rm kpc}=165.4\times(1+z)^{-2.9}$, respectively. Note that there are several caveats. The sampling of the CEERS survey data is sparse at $z>3$, resulting in a single redshift bin to cover $z=3-5.5$. Meanwhile, the simulation models galaxies at $z=3-6$ only. Galaxies with $M_*\gtrsim2\times10^{11}$ M$_\odot$ are quite rare at $z\gtrsim3$ in both observations and simulations, and the size-mass relation in the mass range largely relies on extrapolation of the lower-mass range. Nevertheless, they provide useful comparison at $z\simeq3$.

As shown, the effective radius of ADF22.A1 at $z=3.09$ is about $(1.8-2.5)\times$ larger than the representative values expected at the redshift from observations or simulations. The effective radius is larger than any galaxies in the CEERS survey at $z>3$ ((cite: 2024ApJ...962..176W)), which demonstrate that ADF22.A1 is one of the largest galaxies at such an early epoch. The effective radius is equivalent to that of typical star-forming galaxies at $z=0.5-1.0$, suggesting accelerated size growth of a stellar disk in the violently growth phase in a rare $z=3.1$ proto-cluster core with a space density below those sampled by recent simulations. The Sérsic index is significantly larger than unity, giving further evidence for the existence of a growing bulge.

In Fig. [4](#fig:z_size), we also compared the result with other measurements on stellar sizes of DSFGs based on JWST/NIRCam. Eighty DSFGs observed by the PRIMER project at $z=2.7_{-0.7}^{+1.2}$ have effective radius $r_{\rm e, F444W}=2.7\pm0.2$ kpc ((cite: 2024arXiv240603544G)) with two relatively large examples with $r_{\rm e, F444W}\sim7$ kpc. GN20 at $z=4.05$, which is a member of the proto-cluster at the field, have an effective radius $r_{\rm e, F560W}=3.6\pm0.03$ kpc ((cite: 2023A&A...673L...6C)).

It is also reported that A1489-850.1 at $z=4.26$ has $r_{\rm e, F444W}=3.8\pm0.4$ kpc ((cite: 2023ApJ...958...36S)).

While these are relatively larger than other DSFGs at a lower redshift, their sizes are still only about a half of ADF22.A1. Thus the large size of ADF22.A1 is unusual among the DSFG population.

We also model the 0.2$^{\prime\prime}$ 870 $\mu$m dust continuum emission and \[C ii\] total flux with a Sérsic profile (Fig. [3](#fig:galfit)). ADF22.A1 has the peak flux density $S_{\rm 870}=2.61 \pm0.02$ mJy beam$^{-1}$, which corresponds to the signal-to-noise ratio (SNR) $\approx124$. We masked $5\sigma$ peaks as presented in (cite: 2019ApJ...876..130H) in the case of 870 $\mu$m dust continuum, which yielded the best-fit model with an effective radius $r_{\rm e, 870}=4.7\pm0.1$ kpc and Sérsic index $n=0.9\pm0.1$.

For \[C ii\], the $^{\rm 3D}$barolo package ((cite: 2015MNRAS.451.3021D)) was used to extract the \[C ii\] emission from the cube with 40 km s$^{-1}$ bins to make the moment-0 map. The genuine emission was identified with the search task with SNRCUT=4.5, GROWTHCUT=4.5, and MINCHANNELS=3. The \[C ii\] peak flux is $1.95\pm0.07$ Jy beam$^{-1}$ km s$^{-1}$ (SNR$\approx28$, by assuming that three channels as the typical channel width to combine).

We fit a Sérsic profile without a bright emission mask and obtained $r_{\rm e, [CII]}=7.6\pm0.2$ kpc and Sérsic index $n=0.4\pm0.1$.

We note that the models still leave residuals, which demonstrate the power of high-resolution images at the 0.2$^{\prime\prime}$ resolution. These substructures include a core, clumps, and spiral arms. The spiral arms are indicated by all three components (stars, dust, and gas) while the relative strength among the three tracers show significant variation.

## Kinematic modeling

![](figures/Fig5.pdf)

We made \[C ii\] data cubes and fitted them with a rotating disk model to derive the kinematic properties.

As presented in Fig. [1](#fig:almamap), the observed \[C ii\] velocity field shows a generally monotonic velocity gradient, indicating a rotating gas disk in the spiral galaxy. A twisted pattern at the center also suggests the presence of non-circular motion (see also Fig. [11](#fig:bar_summary)b for the detailed view). The $^{\rm 3D}$barolo package was utilized to model the \[C ii\] kinematics as a rotating disk, which also allows a chance to isolate the non-circular components. In addition to the original 0.2$^{\prime\prime}$ resolution cube, we used a smoothed cube with a 0.9$^{\prime\prime}$ resolution, which improves the detectability of emission in the outskirts and suppresses the deviations produced by the non-circular motions at the center.

First we made use of the high-resolution cube (0.2$^{\prime\prime}$). The cube was created with a 40 km s$^{-1}$ bin, which was then Hanning-smoothed with the smoothspec function. We adopted a disk model where the kinematic center ($x_0$, $y_0$), position angle (PA), inclination ($i$), systemic velocity ($V_{\rm sys}$), rotation velocity ($V_{\rm rot}$), and velocity dispersion ($\sigma$) were free-parameters. The scale-height of the disc was fixed to be 300 pc ((cite: 2021Sci...371..713L)). We adopted a ring width of $0.097^{\prime\prime}$, which is half of the resolution element $\sqrt{\theta_x + \theta_y}$, where $\theta_{\rm x}$ and $\theta_{\rm y}$ are the major and minor axes of the synthesized beam. Considering the complex gas morphology (Fig. [1](#fig:almamap)), a disk model with non-axisymmetric gas distributions was studied by renormalizing the flux density of each spatial pixel to the observed intensity map.

The evaluated inclination generally ranges from $i=70$ deg to $i=75$ deg with a typical errors of 4 deg. The median value is $i=73$ deg. For position angle, PA=$87-96$ deg (a median value PA=92 deg with errors of 5 deg) are estimated. The kinematic center position matches with peaks of F444W and 870 $\mu$m dust continuum emissions within the F444W pixel sampling. Fig. [5](#fig:barolo)a shows the position-velocity (PV) diagram of the best-fit model, compared to the observed emission. While the model successfully reproduces the observed emission as a whole, there are some discrepancy in the inner most region comprising the twisted pattern. Errors on the derived parameters become large, reflecting the influence of the non-circular motion at the center.

An elliptical region, which is centered at the kinematic center and aligned along the kinematic major axis, is defined to isolate the innermost region. This region is denoted as the “bar region” since the region corresponds to the area of the dusty core and offset ridges (Fig. [11](#fig:bar_summary)). We will discuss this aspect more in §[4.2](#dis:bar) later, together with possible influence of AGN.

The 0.9$^{\prime\prime}$ resolution cube is used to obtain the overall trend of the velocity structure, which is insensitive to the innermost non-circular motion and sensitive to the extended emission in the outer region. We adopt and fix the obtained median values of the parameters during the run for the 0.2$^{\prime\prime}$ cube except for rotation velocity and velocity dispersion. We adopt a ring width of 0.$^{\prime\prime}$35, which is 40% of the resolution element, considering the consistency with spatial resolution and the accuracy of velocity field estimation. In the fit, rotation velocity and velocity dispersion are estimated. The PV diagram of the modeled and observed emissions are shown in Fig. [5](#fig:barolo). In this case, the model generally reproduces the observed emission.

It is suggested that the velocity dispersion derived by $^{\rm 3D}$barolo in the standard way can be significantly underestimated when the velocity resolution is not sufficient, which may be a typical situation in observations of galaxies at high redshift ((cite: 2023A&A...672A.106L)). We use the task spacepar in $^{\rm 3D}$barolo to investigate a global minimum in the $V_{\rm rot}$-$\sigma$ space and obtain a better constraint on velocity dispersion, fixing other parameters. The explored parameter space is a range of $V_{\rm rot}$ from 1 to 700 km s$^{-1}$ and $\sigma$ from 1 to 100 km s$^{-1}$, respectively. Steps are 2 km s$^{-1}$ for each. The minimum $\sigma$ is in a range from 44 to 60 km s$^{-1}$ at $r=0.63^{\prime\prime}$ to 1.02$^{\prime\prime}$ (4.8 to 7.8 kpc). The area corresponds to bright spiral arms and disks away from the central bulge and bar regions. This is close to the velocity resolution (80 km s$^{-1}$) and hence we perform the similar test for a cube with 20 km s$^{-1}$ bins (the velocity resolution after Hanning smoothing is 40 km s$^{-1}$). This test resulted in a similar $\sigma$ range, which support the validity of the measurement with the original cube. We conservatively adopt a representative $\sigma=60$ km s$^{-1}$.

![](figures/Fig6.pdf)

The evaluated rotation velocity is plotted as a function of radius in Fig. [6](#fig:rotationcurve) for both cases. We fit the rotation curve based on the 0.9$^{\prime\prime}$ cube with an arctangent model:

$$\begin{equation}
v(r) = \frac{2}{\pi} v_{\infty} \arctan\left(\frac{r}{r_t}\right)
\end{equation}$$

where $v_{\infty}$ is the asymptotic velocity at sufficiently large radii and ${r_t}$ is the scale radius at which the rotation curve transitions from rising to flat.

The best fit model is also shown in Fig. [6](#fig:rotationcurve) with $v_{\infty}=540$ km s$^{-1}$ and ${r_t}=0.52$ kpc. The rotation curve from the 0.2$^{\prime\prime}$ cube is generally consistent with that of the 0.9$^{\prime\prime}$ cube. Potential deviations are seen in the inner region ($r\lesssim4$ kpc). The steep rise in the innermost bin can be caused by the compact gravitational potential associated with the stellar bulge, as other works report in some DSFGs ((cite: 2021Sci...371..713L)).

The derived rotation velocity $V_{\rm rot}$ remains flat with $V_{\rm rot}=530\approx$ km s$^{-1}$ in the outer disk, extending to $r\approx15$ kpc.

We measure a rotation velocity $V_{\rm rot}$ using the arctangent model. At a radius of $r=2{\rm r}_{\rm e}$, $V_{\rm rot}=530\pm10$ km s$^{-1}$. Adopting this value as a representative $V_{\rm rot}$, the ratio between the rotation velocity and velocity dispersion is $V_{\rm rot}/\sigma=8.8\pm1.5$. Hence rotation support dominates pressure support in ADF22.A1. Based on this result, we assume that the rotation velocity is approximated equal to the circular velocity.

The nature of ADF22.A1, a huge and rapidly-rotating disk, is distinguished among any known galaxies in the early universe. The rotation velocity and extent of the gas disk are several times larger than those reported for DSFGs at $z\sim4-5$ ((cite: 2020Natur.584..201R); ; (cite: 2021Sci...371..713L)) (Fig. [6](#fig:rotationcurve)), and also uniquely large among DSFGs at $z\sim2$(cite: 2023arXiv231208959A). One possibly resemble case is GN20 at $z=4.05$ ((cite: 2012ApJ...760...11H)). While the CO(2–1) data obtained with the VLA does not have sufficient quality for fair comparison with ADF22.A1, the reported maximum rotational velocity of $v_{\rm max} = 575 \pm 100$ km s$^{-1}$ is comparable. They reported the emission extends to $r=7$ kpc, which is about a half of that of ADF22.A1. Interestingly GN20 also resides in a proto-cluster at $z=4$ similar to ADF22.A1.

There are also intriguing discovery about normal star-forming galaxies (not DSFGs). Large disk galaxies at $z\sim3$ in an overdensity are recently reported ((cite: 2023ApJ...942L...1W); (cite: 2024arXiv240917956W)). While the rotation velocity is not so large ($v_{\rm rot} \sim 200-300$ km s$^{-1}$), the disk size is similar to ADF22.A1.

There may be a common driver to form rapidly rotating disks and/or giant disks in a proto-cluster environment. As we discussed in the paper, both cold gas accretion and gas-rich major-mergers are expected to work efficiently in such an environment.

A difference between rotation velocities based on the two resolution cubes is identified in the inner region ($r\lesssim4$ kpc), while both measurements are consistent in the outer part. A steep rise in $V_{\rm rot}$ in the innermost region may be caused by a bulge potential ((cite: 2021Sci...371..713L)), while the adjacent decline indicates the effect of a bar flow ((cite: 2009PASJ...61..441H)).

## Resolved stellar profile and specific stellar angular momentum

![](figures/Fig7.pdf)

The stellar specific angular momentum ($j_*=J_*/M_*$, where $J_*$ is total stellar angular momentum) involves three uncorrelated variables; a length scale, and a rotation-velocity, is one of the most fundamental quantities to describe kinematics and structures of galaxies (e.g., (cite: 1980MNRAS.193..189F); (cite: 2012ApJS..203...17R)). The specific stellar angular momentum is given by

$$\begin{equation}
j_* = \frac{J_*}{M_*} = \frac{\int_{r_*} (\mbox{\boldmath $r$} \times \bar{\mbox{\boldmath $v$}}) \rho_* d^3 \mbox{\boldmath $r$}}{\int_{r} \rho_* d^3 \mbox{\boldmath $r$}}
\end{equation}$$

where $\vb*{r}$, $\bar{\vb*{v}}(\vb*{r})$, and $\rho(\vb*{r})$ are the position, mean-velocity vectors, and the three-dimensional density of the stars.

This equation (2) can be reduced to a one-dimensional integral and given by: $$\begin{equation}
\label{eq:j*}
j_* = \frac{\int_0^\infty \Sigma(r) \, v(r) \, r^2 \, dr}{\int_0^\infty \Sigma(r) \, r \, dr}
\end{equation}$$

where $r$ is the radius, $\Sigma(r)$ is the surface mass density at radius $r$, and $v(r)$ is the rotational velocity at radius $r$. Thus one need to derive surface stellar mass density profile and rotation velocity as a function of radius, in a spatially resolved way for both, to calculate the stellar specific angular momentum.

First we evaluate the surface stellar mass density profile through multi-wavelength SED fit in a pixel-by-pixel way. Here we briefly describe the method, while details will be reported in another paper (H. Umehata et al, in preparation, see also a previous work ((cite: 2023ApJ...958...36S))). We use the F115W, F200W, F356W, and F444W images, matching the PSF to that of F444W. To account for the dust-obscured star-formation activity, we also include a spatially resolved 870 $\mu$m dust continuum map at $0.2^{\prime\prime}$ sampling.

Utilizing the F444W image as a detection mask, we use the magphys code ((cite: 2012IAUS..284..292D)) to fit the SED of each pixel. We adopt the median of the stellar mass distribution as a representative value for a pixel, while lower and upper values are determined as 16th and 84th percentiles.

We use the stellar mass map to derive stellar mass density profile through elliptical aperture photometry. The profile obtained is shown in Fig. [7](#fig:sAM)a. There is a significant excess of stellar mass surface density at the innermost region ($R\lesssim2$ kpc) above a simple exponential disk, which reflects the stellar bulge in ADF22.A1. Note that the panchromatic SED fit for the whole galaxy including X-ray suggests that the contribution from the AGN in the F444W photometry is limited ($\lesssim5$%) and does not have significant impact on the derived stellar mass profile (Fig. [2](#fig:lightning)). As some previous works (e.g., (cite: 2023A&A...672A.106L)), we fit the observed profile with the combination of the bulge and disk components. For the bulge, we adopt the Sérsic profile with $n=3$, while we assume an exponential profile for the disk. The best-fit model is shown in Fig. [7](#fig:sAM)a. The best-fit model is not significantly effected by Sérsic index for a range of $n=2-4$. There are potential excess at $z\sim2-3$ kpc between the observed and modeled profile, which may be due to a stellar bar, but the limited sampling of the profile prevent us from adding the third component. We evaluate the bulge to total stellar mass ratio $B/T\approx0.2$ from the excess over the disk exponential profile in the inner part. Since the currently available photometry taken with JWST and ALMA is not sufficient to uncover the stellar mass surface distribution in outer parts due to the lack of sensitivity, we extrapolate the profile at $R\gtrsim8$ kpc.

Until recently, stellar specific angular momentum was approximated with simplified profiles of stellar mass distribution and velocity at high redshift ((cite: 2012ApJS..203...17R)). Now, we can derive the parameter with the measured stellar mass distribution, obtained from the pixel-by-pixel SED fit including submm photometry, and a rotation curve, assuming that gas kinematics trace that of the stellar component ((cite: 2014ApJ...784...26O)).

To suppress the influence of non-circular motion in the bar region, we adopt the arctangent model as the rotation velocity profile. Then the stellar specific angular momentum ($j_*$) is calculated following equation ([\[eq:j\*\]](#eq:j*)). The cumulative profile of stellar specific angular momentum is plotted in Fig. [7](#fig:sAM)b, together with profiles of stellar mass distribution and rotation velocity. The total stellar specific angular momentum is calculated as a converged value, $j_*=3400\pm600$ km s$^{-1}$ kpc.

While the above method is the most direct way to derive $j_*$, it is usually quite challenging to obtain both resolved rotation curve and stellar mass surface density profile for galaxies at high redshift due to the limited sensitivity, spatial resolution, and available range of photometries. As an approximation, the scaling relation among specific angular momentum, rotation velocity and disc size and morphology has been suggested ((cite: 2012ApJS..203...17R)): $$\begin{equation}
    \tilde{j_*}=k_n v_s r_{\rm e}
\end{equation}$$ where $v_s$ is the rotation velocity at $2\times r_{\rm e}$. The remaining parameter $k_n$ is a numerical coefficient that depends on the Sérsic index ($n$) of the galaxy: $$\begin{equation}
    k_n = 1.15+0.029n+0.062n^2
\end{equation}$$

Assuming that we only have effective radius in an image (here F444W is adopted), this approximation gives $\tilde{j_*}\simeq5100$ kpc km s$^{-1}$ which is $\sim50$ % larger than the estimate based on the resolved profile and rotation curve. There are several plausible factors to make the estimate of the stellar angular momentum uncertain in the approximation. First the F444W emission profile of ADF22.A1 is not perfectly modeled with a single Sérsic profile as there is residual emissions (Fig. [3](#fig:galfit)). ADF22.A1 has a bulge and spiral arms, and there is a limitation to fitting with a single component. Second, the stellar emission in the F444W image would not be necessarily a good tracer of stellar mass distribution. The rest-frame wavelength 11000 Å, which can be still affected by significant dust attenuation in massive star-forming galaxies including DSFGs. It is reported that dust attenuation can result in flatter light profiles that yield larger effective radii ((cite: 2023ApJ...946...71C); (cite: 2024arXiv240116608L)). This can also lead an overestimate of specific stellar angular momentum.

The result demonstrates that calculation of specific stellar angular momentum based on resolved profiles of stellar mass surface density and rotation velocity for galaxies at high-redshift is critically important.

## Molecular gas mass and Toomre-Q paramter

![](figures/Fig8.pdf)

To investigate the cause of the starburst activity seen in ADF22.A1, the Toomre-$Q$ parameter was computed for ADF22.A1, utilizing the resolved gas kinematics traced by \[C ii\] and total molecular gas mass measured with CO(1–0) emission.

The total molecular gas mass of ADF22.A1 was estimated utilizing the line luminosity of the CO(1–0) emission. The ground $J = 1-0$ transition offers a well-established tracer of the cold molecular gas reservoirs of galaxies. The JVLA observations have successfully detected the emission in ADF22.A1, as the velcoity-integrated flux image is shown in Fig. [8](#fig:co10). The total line flux measured using the casa/imfit task was ($0.20\pm0.03$) Jy km s$^{-1}$, which corresponds to a line luminosity $L^{\prime}_{\rm CO(1-0)}=(8.1\pm1.4)\times10^{10}$ K km s$^{-1}$ pc$^2$.

This gives the molecular gas mass $M_{\rm gas}=(\alpha_{\rm CO}/2.5)\times(2.0\pm0.4)\times10^{11}$ M$_\odot$. It is known that $\alpha_{\rm CO}$ vary among galaxies (for example, $\alpha_{\rm CO}\simeq0.8$ for local ULIRGs and $\alpha_{\rm CO}\simeq4.6$ for the Milky-Way like galaxies ((cite: 2005ARA&A..43..677S) and references therein). We adopt $\alpha_{\rm CO}\simeq2.5$ as a representative value, which has been derived through comparison between CO and \[C i\] line luminosities for a set of DSFGs ((cite: 2017MNRAS.466.2825B)). The molecular gas mass measurement provides an estimate of gas mass fraction $f_{\rm gas}=M_{\rm gas}/(M_{*}+M_{\rm gas})=0.45\pm0.10$.

The Toomre-Q parameter ((cite: 1964ApJ...139.1217T)) was calculated to examine the average stability of the galactic disc against local gravitational collapse. The parameter is defined as $Q=\sigma \kappa / (\pi G \Sigma_{\rm gas})$, where $G$ is the gravitational constant, and $\Sigma_{\rm gas}$ is the gas mass surface density. Here $\sigma$ is the velocity dispersion and $\kappa$ is the epicyclic frequency. Since A1 shows a flat rotation curve, we approximate it as $\kappa=\sqrt{2}V_{\rm rot}/r$ where $V_{\rm rot}$ is the rotation velocity of the disc at radius $r$.

The CO(1–0) emission is not well resolved with JVLA (Fig.  [8](#fig:co10)). Here we assumed that the CO(1–0) profile is the same as that of \[C ii\]. We calculate the Toomre-Q parameter, calculating $\kappa$ at $r_{\rm e, [CII]}$ and averaged molecular gas mass surface density within the radius. We adopt the velocity profile and velocity dispersion measured with the \[C ii\] modeling. The calculated $Q=0.7\pm0.2$ supports a scenario that the gas disk is gravitationally unstable and the instabilities can develop on scales larger than the Jeans length and drive active star formation observed across the disk (Fig. [1](#fig:almamap)).

# Discussion

## Origin of the rapidly rotating, giant disk

![](figures/Fig9.pdf)

The derived relation between stellar mass and specific stellar angular momentum is plotted in Fig. [9](#fig:j_ms). For comparison, we also show the relation measured for local spiral galaxies ((cite: 2014ApJ...784...26O); (cite: 2023MNRAS.518.6340D)) and ellipticals ((cite: 2018ApJ...868..133F)), together with the best-fit functions ((cite: 2018ApJ...868..133F)). For ADF22.A1 and local spiral galaxies, markers are color-coded with molecular gas mass fraction $f_{\rm gas} = M_{\rm mol}/(M_*+M_{\rm mol})$.

The specific stellar angular momentum of ADF22.A1 is as high as seen in the most massive and largest local spiral galaxies ((cite: 2014ApJ...784...26O)), following the local $M_*-j_*$ relation for spiral galaxies ((cite: 2012ApJS..203...17R)). Therefore, the nature of ADF22.A1 is likely reflects a high stellar mass and a rapidly-rotating disk. This also suggests that the association with the Hubble sequence (“the mass-spin-morphology relation”)((cite: 2013ApJ...769L..26F)), has already emerged at $z\sim3$.

However, a distinct characteristic between ADF22.A1 at $z=3.09$ and local spirals is the molecular gas mass fraction. ADF22.A1 is a starburst and has an implied gas mass fraction of $\sim$45%, which is around two orders of magnitude higher than local spirals (Fig. [9](#fig:j_ms)).

There must be a source which supplies angular momentum and gas fuel to form such a system - rapidly rotating gas disk - only $\sim2$ billion years after the Big Bang.

![](figures/Fig10.pdf)

A plausible mechanism for forming a large, rapidly rotating disk is cold stream accretion from the cosmic web ((cite: 2006MNRAS.368....2D); (cite: 2009Natur.457..451D)). The redshift-$M_{\rm h}$ diagram is proposed by (cite: 2006MNRAS.368....2D) as a diagnostic of whether cold mode accretion is allowed or prohibited (Fig. [10](#fig:zhalo)).

Cosmological simulations show that these cold gas flows have a specific angular momentum much higher than that of the host halo and are able to quickly form into an extended disk of cold gas in $t\lesssim1$ Gyr ((cite: 2013ApJ...769...74S); (cite: 2022MNRAS.510.3266K)).

We estimate dark matter halo mass ($M_{\rm h}$) hosting ADF22.A1 utilizing the empirical relation between the halo mass and flat rotation velocity for late-type galaxies ((cite: 2019MNRAS.483L..98K)):

$$\begin{equation}
M_{\rm h}= A {\rm log}_{10}(V_{\rm flat}/{\rm km} {\rm s}^{-1})+B 
\end{equation}$$

where $A=2.216\pm0.208$ and $B= 6.907\pm0.471$ for the NFW halo profile ((cite: 1996ApJ...462..563N)). Using the flat rotation velocity derived above, the relation gives log($M_{\rm h}$/M$_\odot$)$=12.9\pm0.7$. In Fig. [10](#fig:zhalo), we plot the relation between redshift and dark matter halo mass, comparing with model tracks of the mass growth of dark matter halos and derived values in previous works for host halos of DSFGs (with clustering analysis ((cite: 2021MNRAS.504..172S)) or decomposition of rotation curves ((cite: 2020Natur.584..201R); ; (cite: 2021Sci...371..713L)). The host halo of ADF22.A1 is one of the most massive halos known at $z\simeq3$ and also the most massive among host halos of DSFGs in the early universe.

ADF22.A1 corresponds to the “cold in hot” regime as marked Fig. [10](#fig:zhalo). This suggests that while ADF22.A1 resides in a very massive halo, cold mode accretion can still survive to provide fuel and angular momentum for the galaxy.

Intriguingly ADF22.A1 resides in the massive halo, which is associated with plentiful cool gas visible as a Mpc-scale network of Ly $\alpha$ filaments ((cite: 2019Sci...366...97U)). Such an environment is predicted to sustain efficient cold gas accretion.

In addition to cold accretion, there is another possible contributor. Mergers of gas-rich spiral galaxies are considered to converge to a larger, massive spiral disk satisfying the $M_*-j_*$ relation ((cite: 2009ApJ...691.1168H)). Mergers may hence account for the nature of ADF22.A1, coupled to the formation of gas-rich, rapidly-rotating pre-merger galaxies from cold accretion.

The resultant giant gas disc has significant amount of molecular gas mass while rotation velocity is large. As a consequence the Toomre-Q parameter below unity as estimated in §[3.6](#analysis:toomreq) and can show starburst nature due to disk instability.

## Bar-driven bulge formation

![](figures/Fig11.pdf)

### a bar traced in dust continuum

We further explored the inner regions of the galaxy where dust emission is concentrated.

The 0.08$^{\prime\prime}$ resolution 1.1 mm dust continuum map shows that ADF22.A1 has a bright dusty core (with the effective radius, accompanied with a pair of curved dust lanes at a $r\approx3.3$ kpc scale.

The spatial relation between the spiral arms and the dusty core and dust lanes in ADF22.A1 is illustrated in Fig. [11](#fig:bar_summary)a, while the structure of the dust emission is shown in Fig. [11](#fig:bar_summary)b.

As illustrated, the high-fidelity 1.1 mm dust continuum image of the inner region uncovers a pair of curved dust lanes located in the leading side, associated with the central, dusty core. The same structure is present in the 630 $\mu$m map, demonstrating that these structures are securely detected.

The dust lanes are called the “offset ridges”, which form in the leading side ((cite: 1992MNRAS.259..345A)). Such structures of the ISMs is a common feature seen in local barred spiral galaxies and have been reproduced by numerical and analytical calculations, including the cloud-orbit and hydrodynamical shock wave models ((cite: 1980A&A....92...33C), (cite: 1991MNRAS.252..210B), (cite: 1992MNRAS.259..345A), (cite: 2023ApJ...944L..15S)). Thus the resolved structure traced by dust continuum shows that ADF22.A1 has a bar.

The existence of bars in star-forming galaxies at high redshift have been discussed in previous works (e.g., (cite: 2023Natur.623..499C); (cite: 2024MNRAS.527.8941T)). Bars are suggested based on elongated morphology in dust emission ((cite: 2019ApJ...876..130H); (cite: 2019MNRAS.490.4956G)),though signatures are not seen in stellar emission ((cite: 2024arXiv240715846H)), while morphology of stellar emission show hints of a bar in some DSFGs ((cite: 2023ApJ...958...36S); (cite: 2023ApJ...958L..26H)).

ADF22.A1 shows the most detailed map of dust emission in DSFGs, which allows us to delineate the offset ridges in the bar.

Profile fit for the dusty core in the high angular resolution image (0.04$^{\prime\prime}$) shows $r_{\rm e}=670\pm30$ pc and $n=0.6\pm0.1$.

The bar length is roughly estimated as the major axis of elliptical apertures which encompass the offset ridges delineated with 1.1 mm dust continuum (Fig. [11](#fig:bar_summary)a). The estimated bar size is $r\approx3.3$ kpc.

The bar structure is not clearly visible in other tracers, including stellar light or \[C ii\] intensity, as has also been reported for some DSFGs ((cite: 2024arXiv240715846H)). This is most likely due to severe dust attenuation. The fact that the region is bright in dust continuum indicates that dust obscuration is significant. A similar situation, a visible dust bar which is not seen in stellar light due to high extinction is reported for the local barred spiral NGC 253 ((cite: 2003AJ....125..525J)). While the F444W image allows us to observe $\sim11000$ Å at rest frame, this is insufficient to overcome the high dust extinction. Second angular resolution of the two tracers, $0.2^{\prime\prime}$ (1.5 kpc), may not be sufficiently fine to resolve the inner structure which is visible with the $0.07^{\prime\prime}$ (500 pc) resolution.

### a bar traced in gas kinematics

The offset ridges in the bar spatially coincide with the twisted pattern of the non-circular motion in the \[C ii\] velocity field (Fig. [1](#fig:almamap)d). The right panel of Fig. [11](#fig:bar_summary)b shows the residual velocity map at 0.2$^{\prime\prime}$ after subtracting a model derived with the 3d barolo, together with the 1.1 mm dust continuum contours. As shown, both the approaching and receding gas motion is detected, bracketing the central dusty core.

To further diagnose the origin of the non-circular motion, we derive two PV-diagrams along the offset-ridges (A is for the side associated with receding gas flow, while B is for the other side connected with the approaching gas flow, Fig. [11](#fig:bar_summary)c). As shown, it is found that there are multiple velocity components in the inner region ($r\lesssim0.4^{\prime\prime}$). In addition to a high velocity component whose velocity is equivalent to that of outer regions, a low velocity component is found in both sides.

This is what is expected in the gas flow in the $x-1$ orbit along the bar potential toward a core (e.g., (cite: 2023ApJ...944L..15S)). Gas clouds flow toward the core along the offset ridge in the rotating frame with a bar pattern speed. The line-of-sight velocity of the gas flow is governed with the bar pattern speed in the innermost region, which appears as a low velocity components in the bar region ((cite: 2009PASJ...61..441H)).

Hence as summarized in Fig. [11](#fig:bar_summary), there is gas inflow along the offset ridges toward the dusty core, in addition to the disk rotation.

While the moderate spatial resolution of the \[C ii\] data allows significant blending from both components in the region, the disk rotation and bar flow has different velocities as described above, which are identified as multiple velocity components and the non-circular motion with the twisted pattern.

This finding strongly supports the theoretical expectation that bars drive gas inward from the disk, triggering central star formation and contributing to the growth of pseudobulges in disk galaxies ((cite: 2004ARA&A..42..603K)).

Cosmological simulations predict that a gas-rich, short-lived ($t\lesssim1$ Gyr) bar forms in response to various perturbations including cold accretion from the filaments and mergers ((cite: 2024MNRAS.52711095B)), which can account for the case of ADF22.A1.

### Contribution from AGNs

ADF22.A1 harbors an obscured AGN at the center ((cite: 2010ApJ...724.1270T); (cite: 2023ApJ...951...15M)), and AGN outflow may offer another mechanism to cause a non-circular motion. While it is challenging to determine such a contribution from AGN outflow to \[C ii\] velocity field in ADF22.A1, we note that a typical biconical outflow which is perpendicular to the disk plane is unlikely to produce the non-circular motion. Considering the configuration that the southern side is the near side and the north side is the far side from us, which is determined by the combination of the velocity field and a pattern of spiral arms ((cite: 2023ApJ...957...48G)), such an outflow would show a blue-shifted component in the north and a red-shifted component in the south. This is opposite of what is observed.

Furthermore, the observed non-circular motion is caused by low-velocity components, which is different from fast AGN outflows often observed in AGN-host galaxies ((cite: 2024MNRAS.533.4287U)).

Thus observational evidences obtained so far suggest that any outflow from the AGN is not dominating the \[C ii\] kinematics.

## Co-evolution in the hidden early phase

![](figures/Fig12.pdf)

ADF22.A1 is known to harbor a heavily obscured, but intrinsically X-ray bright (log$L_X=44.3$ erg s$^{-1}$) ((cite: 2010ApJ...724.1270T); (cite: 2023ApJ...951...15M)) active galactic nucleus and hence active accretion onto its central supermassive black hole is expected in the bright dusty core.

We investigated the relation between the SMBH mass and total stellar mass/bulge mass of ADF22.A1. These masses are derived based on the SED fit as described above. We plot the two ratios in Fig. [12](#fig:smbh). For comparison, we also show the relation for the total galaxy mass for both spiral galaxies and ellipticals in the local universe. Data for individual galaxies and best-fit functions are adopted from a recent review ((cite: 2020ARA&A..58..257G) and references there in).

As shown, the total galaxy mass-SMBH mass relation is consistent with that measured for local spirals, suggesting relatively overmassive stellar mass compared with the relation for local ellipticals.

This trend is consistent with literature which report the similar trend for DSFGs at $z\sim2$ ((cite: 2008AJ....135.1968A)).

If we only focus on the bulge components, on the other hand, the mass ratio between SMBH and bulge masses $M_{\rm BH}$/$M_{\rm bulge}$ matches that of local ellipticals ((cite: 2013ARA&A..51..511K); (cite: 2020ARA&A..58..257G)) (Fig. [12](#fig:smbh)).

This suggests that the co-growth of bulges and SMBHs can occur during the early forming phase at $z\approx3$, driven by bar structures. This furthermore indicates that subsequent reconfiguration of the stellar mass in the current disk component of ADF22.A1 into a pressure-supported spheroid must also be associated with further growth of the SMBH.

## Evolution into local massive ellipticals

ADF22.A1 is the most massive and active galaxy in the SSA22 proto-cluster core ((cite: 2015ApJ...815L...8U); (cite: 2023ApJ...951...15M)) and a plausible analog for the progenitors of the most massive elliptical galaxies in today’s dense clusters, such as Brightest Cluster Galaxies (BCGs), including cD galaxies. The results presented here give unique insights into the evolution of the most massive galaxies and SMBHs.

ADF22.A1 is a spiral galaxy although it is located in a proto-cluster core. This exhibits an inverse relation between galaxy morphology and environment compared with the local clusters ((cite: 1980ApJ...236..351D)), indicating that the most massive galaxies in overdense environments must evolve from late-type rotationally dominated disks to early-type dispersion-dominated ellipticals.

To achieve this, ADF22.A1 will have to experience a significant loss of angular momentum.

The EAGLE simulation suggests that bulge-dominated galaxies (with the bulge-to-total stellar mass ratio $B/T>0.5$) lose the majority of their specific stellar angular momentum ($80\%$ is the median value) from “turnaround” (at $z\sim3$) to $z\sim0$ ((cite: 2016MNRAS.460.4466Z)), associated with mergers of galaxies and dynamical friction during the inner dark matter halo’s assembly ((cite: 2017MNRAS.464.3850L); (cite: 2018MNRAS.473.4956L)). In Fig. [9](#fig:j_ms)b, we plot a predicted descendant at $z=0$ of ADF22.A1, assuming that (i) the molecular gas mass is all converted into stars (ii) other process (additional inflow, mergers, outflows) does not affect the stellar mass of the descendant, and (iii) 80% of the specific stellar angular momentum is lost. As shown, the net loss predicted by the simulation sufficiently reduce the angular momentum to the levels seen in elliptical galaxies.

# Conclusion

We present JWST NIRCam imaging and ALMA imaging spectroscopy to resolve the inner structures and kinematics on (sub-)kpc scales in a bright DSFG located at the core of a $z=3.09$ proto-cluster. Our main findings include:

- NIRCam images reveal a spiral-like stellar structure tracing rest-frame optical-to-near-infrared emissions. The measured effective radius, $r_{\rm e} = 7.0 \pm 0.1,\mathrm{kpc}$, is more than twice the typical size of coeval, equally massive galaxies and is comparable to that of local galaxies at $z = 0$–1, suggesting accelerated size growth in the proto-cluster core.

- The ALMA 870 $\mu$m image reveals that the dust continuum is not just concentrated in a core, as seen in some DSFGs, but is distributed across the disk. This indicates that active star formation is also occurring in the disk, accompanied by significant dust production. Statistical samples with resolved studies will reveal if this is general.

- The \[C ii\] velocity field is primarily dominated by rotation, with non-circular motions also detected in the center. Kinematic modeling of the \[C ii\] emission reveals a flat rotation curve with $V_{\rm rot} = 530 \pm 10$ km s$^{-1}$ out to $r\sim15$ kpc, indicating that ADF22.A1 is an unusually fast-rotating, giant spiral galaxy.

- The derived $M_*$-$j_*$ relation tells us that ADF22.A1 at $z=3.09$ follows the mass-spin-morphology relation seen in the local universe. This requires a mechanism to highly spin up the disk of ADF22.A1 only $\sim$2 billion years after the Big Bang. Cold accretion is the most plausible case, coupled with mergers.

- The derived $M_*$-$j_*$ relation indicates that ADF22.A1 at $z=3.09$ follows the mass-spin-morphology relation observed in the local universe. This suggests that a mechanism must have rapidly spun up the disk of ADF22.A1 within only $\sim$2 billion years after the Big Bang. Cold accretion, combined with mergers, is the most plausible explanation.

- A bright, compact dusty core is found at the galaxy’s center, indicating the active growth phase of a proto-bulge. The estimated mass ratio of the bulge to the SMBH aligns with the local relation, while the mass ratio of the entire galaxy to the SMBH matches that of local spirals. These results suggest the emergence of bulge-SMBH co-evolution at $z \sim 3$, driven by bars.

- Comparison with the EAGLE simulation suggests that ADF22.A1 likely underwent significant angular momentum loss during halo assembly and associated mergers. Massive, giant spirals may represent an important early phase in the formation of BCGs and cD galaxies found in present-day cluster cores.

The data presented in this paper demonstrate the power of combining JWST and ALMA for well-resolved studies. Expanding the sample and obtaining higher-resolution observations will be crucial for deepening our understanding of the early formation phases of the most massive galaxies.

We thank the anonymous referee for constructive suggestions and comments.

We thank Hidenobu Yajima for discussions on perspectives of simulations; Takuma Izumi for discussions on the co-evolution; Fumi Egusa and Fumiya Maeda for discussions on local analogs of barred galaxies; Tom Bakx for discussions on ALMA data reduction.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program #3547.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00008.S, 2021.1.00041.S, 2021.1.00071.S, 2019.1.00008.S, 2021.1.01406.S, 2022.1.00223.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work is based on the observations of Karl G. Jansky Very Large Array (VLA) (program ID: 16A-357; 21A-346).

HU acknowledges support from JSPS KAKENHI Grant Numbers 20H01953, 22KK0231, 23K20240.

KK acknowledges support from JSPS KAKENHI Grant Numbers 22H0493, 23K20035, 24H00004.

DI acknowledges support from JSPS KAKENHI Grant Number 23K20870.

This work was supported by NAOJ ALMA Scientific Research Grant Numbers 2024-26A.

IS, AMS, DMA acknowledge STFC support (ST/X001075/1).

natexlab

(ref: 2005ApJ...632..736A) Alexander, D. M., Bauer, F. E., Chapman, S. C., et al. 2005, ApJ, 632, 736

(ref: 2008AJ....135.1968A) Alexander, D. M., Brandt, W. N., Smail, I., et al. 2008, AJ, 135, 1968

(ref: 2023arXiv231208959A) Amvrosiadis, A., Wardlow, J. L., Birkin, J. E., et al. 2023, arXiv e-prints, arXiv:2312.08959

(ref: 1992MNRAS.259..345A) Athanassoula, E. 1992, MNRAS, 259, 345

(ref: 2023ApJ...946L..12B) Bagley, M. B., Finkelstein, S. L., Koekemoer, A. M., et al. 2023, ApJL, 946, L12

(ref: 2024MNRAS.52711095B) Bi, D., Shlosman, I., & Romano-Dı́az, E. 2024, MNRAS, 527, 11095

(ref: 1991MNRAS.252..210B) Binney, J., Gerhard, O. E., Stark, A. A., Bally, J., & Uchida, K. I. 1991, MNRAS, 252, 210

(ref: 2004ApJ...611..725B) Blain, A. W., Chapman, S. C., Smail, I., & Ivison, R. 2004, ApJ, 611, 725

(ref: 2017MNRAS.466.2825B) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825

(ref: 2016ApJ...824...36C) Casey, C. M. 2016, ApJ, 824, 36

(ref: 2014PhR...541...45C) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: 2005ApJ...622..772C) Chapman, S. C., Blain, A. W., Smail, I., & Ivison, R. J. 2005, ApJ, 622, 772

(ref: 2023A&A...673L...6C) Colina, L., Crespo Gómez, A., Álvarez-Márquez, J., et al. 2023, A&A, 673, L6

(ref: 1980A&A....92...33C) Contopoulos, G., & Papayannopoulos, T. 1980, A&A, 92, 33

(ref: 2023Natur.623..499C) Costantin, L., Pérez-González, P. G., Guo, Y., et al. 2023a, Nature, 623, 499

(ref: 2023ApJ...946...71C) Costantin, L., Pérez-González, P. G., Vega-Ferrero, J., et al. 2023b, ApJ, 946, 71

(ref: 2012IAUS..284..292D) da Cunha, E., Charlot, S., Dunne, L., Smith, D., & Rowlands, K. 2012, in IAU Symposium, Vol. 284, The Spectral Energy Distribution of Galaxies - SED 2011, ed. R. J. Tuffs & C. C. Popescu, 292–296

(ref: 2009ApJ...694.1517D) Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, ApJ, 694, 1517

(ref: 2006MNRAS.366..499D) De Lucia, G., Springel, V., White, S. D. M., Croton, D., & Kauffmann, G. 2006, MNRAS, 366, 499

(ref: 2006MNRAS.368....2D) Dekel, A., & Birnboim, Y. 2006, MNRAS, 368, 2

(ref: 2009Natur.457..451D) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: 2015MNRAS.451.3021D) Di Teodoro, E. M., & Fraternali, F. 2015, MNRAS, 451, 3021

(ref: 2023MNRAS.518.6340D) Di Teodoro, E. M., Posti, L., Fall, S. M., et al. 2023, MNRAS, 518, 6340

(ref: 1980ApJ...236..351D) Dressler, A. 1980, ApJ, 236, 351

(ref: 1980MNRAS.193..189F) Fall, S. M., & Efstathiou, G. 1980, MNRAS, 193, 189

(ref: 2013ApJ...769L..26F) Fall, S. M., & Romanowsky, A. J. 2013, ApJL, 769, L26

(ref: 2018ApJ...868..133F) —. 2018, ApJ, 868, 133

(ref: 2005MNRAS.363.1398G) Geach, J. E., Matsuda, Y., Smail, I., et al. 2005, MNRAS, 363, 1398

(ref: 2023ApJ...957...48G) Genzel, R., Jolly, J. B., Liu, D., et al. 2023, ApJ, 957, 48

(ref: 2024arXiv240603544G) Gillman, S., Smail, I., Gullberg, B., et al. 2024, arXiv e-prints, arXiv:2406.03544

(ref: 2020ARA&A..58..257G) Greene, J. E., Strader, J., & Ho, L. C. 2020, ARA&A, 58, 257

(ref: 2019MNRAS.490.4956G) Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, MNRAS, 490, 4956

(ref: 2004AJ....128.2073H) Hayashino, T., Matsuda, Y., Tamura, H., et al. 2004, AJ, 128, 2073

(ref: 2009PASJ...61..441H) Hirota, A., Kuno, N., Sato, N., et al. 2009, PASJ, 61, 441

(ref: 2012ApJ...760...11H) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11

(ref: 2019ApJ...876..130H) Hodge, J. A., Smail, I., Walter, F., et al. 2019, ApJ, 876, 130

(ref: 2024arXiv240715846H) Hodge, J. A., da Cunha, E., Kendrew, S., et al. 2024, arXiv e-prints, arXiv:2407.15846

(ref: 2009ApJ...691.1168H) Hopkins, P. F., Cox, T. J., Younger, J. D., & Hernquist, L. 2009, ApJ, 691, 1168

(ref: 2023ApJ...958L..26H) Huang, S., Kawabe, R., Kohno, K., et al. 2023, ApJL, 958, L26

(ref: 2003AJ....125..525J) Jarrett, T. H., Chester, T., Cutri, R., Schneider, S. E., & Huchra, J. P. 2003, AJ, 125, 525

(ref: 2019MNRAS.483L..98K) Katz, H., Desmond, H., McGaugh, S., & Lelli, F. 2019, MNRAS, 483, L98

(ref: 2013ARA&A..51..511K) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511

(ref: 2004ARA&A..42..603K) Kormendy, J., & Kennicutt, Robert C., J. 2004, ARA&A, 42, 603

(ref: 2022MNRAS.510.3266K) Kretschmer, M., Dekel, A., & Teyssier, R. 2022, MNRAS, 510, 3266

(ref: 2024arXiv240116608L) LaChance, P., Croft, R., Ni, Y., et al. 2024, arXiv e-prints, arXiv:2401.16608

(ref: 2017MNRAS.464.3850L) Lagos, C. d. P., Theuns, T., Stevens, A. R. H., et al. 2017, MNRAS, 464, 3850

(ref: 2018MNRAS.473.4956L) Lagos, C. d. P., Stevens, A. R. H., Bower, R. G., et al. 2018, MNRAS, 473, 4956

(ref: 2021Sci...371..713L) Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713

(ref: 2023A&A...672A.106L) Lelli, F., Zhang, Z.-Y., Bisbas, T. G., et al. 2023, A&A, 672, A106

(ref: 1998AJ....115.2285M) Magorrian, J., Tremaine, S., Richstone, D., et al. 1998, AJ, 115, 2285

(ref: 2018Natur.556..469M) Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, Nature, 556, 469

(ref: 2023ApJ...951...15M) Monson, E. B., Doore, K., Eufrasio, R. T., et al. 2023, ApJ, 951, 15

(ref: 1996ApJ...462..563N) Navarro, J. F., Frenk, C. S., & White, S. D. M. 1996, ApJ, 462, 563

(ref: 2014ApJ...784...26O) Obreschkow, D., & Glazebrook, K. 2014, ApJ, 784, 26

(ref: 2018ApJ...856...72O) Oteo, I., Ivison, R. J., Dunne, L., et al. 2018, ApJ, 856, 72

(ref: 2016A&ARv..24...14O) Overzier, R. A. 2016, A&ARv, 24, 14

(ref: 2002AJ....124..266P) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266

(ref: 2010AJ....139.2097P) —. 2010, AJ, 139, 2097

(ref: 2021MNRAS.507.3952R) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952

(ref: 2020Natur.584..201R) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201

(ref: 2012ApJS..203...17R) Romanowsky, A. J., & Fall, S. M. 2012, ApJS, 203, 17

(ref: 2023ApJ...944L..15S) Schinnerer, E., Emsellem, E., Henshaw, J. D., et al. 2023, ApJL, 944, L15

(ref: 2023ApJ...958...36S) Smail, I., Dudzevičiūtė, U., Gurwell, M., et al. 2023, ApJ, 958, 36

(ref: 2005ARA&A..43..677S) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: 2021MNRAS.504..172S) Stach, S. M., Smail, I., Amvrosiadis, A., et al. 2021, MNRAS, 504, 172

(ref: 1998ApJ...492..428S) Steidel, C. C., Adelberger, K. L., Dickinson, M., et al. 1998, ApJ, 492, 428

(ref: 2013ApJ...769...74S) Stewart, K. R., Brooks, A. M., Bullock, J. S., et al. 2013, ApJ, 769, 74

(ref: 2009Natur.459...61T) Tamura, Y., Kohno, K., Nakanishi, K., et al. 2009, Nature, 459, 61

(ref: 2010ApJ...724.1270T) Tamura, Y., Iono, D., Wilner, D. J., et al. 2010, ApJ, 724, 1270

(ref: 2005ApJ...621..673T) Thomas, D., Maraston, C., Bender, R., & Mendes de Oliveira, C. 2005, ApJ, 621, 673

(ref: 2014ApJ...782...68T) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68

(ref: 1964ApJ...139.1217T) Toomre, A. 1964, ApJ, 139, 1217

(ref: 2024MNRAS.527.8941T) Tsukui, T., Wisnioski, E., Bland-Hawthorn, J., et al. 2024, MNRAS, 527, 8941

(ref: 2024MNRAS.533.4287U) Übler, H., D’Eugenio, F., Perna, M., et al. 2024, MNRAS, 533, 4287

(ref: 2014MNRAS.440.3462U) Umehata, H., Tamura, Y., Kohno, K., et al. 2014, MNRAS, 440, 3462

(ref: 2015ApJ...815L...8U) —. 2015, ApJL, 815, L8

(ref: 2017ApJ...835...98U) —. 2017, ApJ, 835, 98

(ref: 2019Sci...366...97U) Umehata, H., Fumagalli, M., Smail, I., et al. 2019, Science, 366, 97

(ref: 2014ApJ...788...28V) van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28

(ref: 2016ApJ...828...56W) Wang, T., Elbaz, D., Daddi, E., et al. 2016, ApJ, 828, 56

(ref: 2024arXiv240917956W) Wang, W., Cantalupo, S., Pensabene, A., et al. 2024, arXiv e-prints, arXiv:2409.17956

(ref: 2024ApJ...962..176W) Ward, E., de la Vega, A., Mobasher, B., et al. 2024, ApJ, 962, 176

(ref: 2023ApJ...942L...1W) Wu, Y., Cai, Z., Sun, F., et al. 2023, ApJL, 942, L1

(ref: 2012AJ....143...79Y) Yamada, T., Nakamura, Y., Matsuda, Y., et al. 2012, AJ, 143, 79

(ref: 2016MNRAS.460.4466Z) Zavala, J., Frenk, C. S., Bower, R., et al. 2016, MNRAS, 460, 4466

</paper>

Write the methods card for this paper.