# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985..166K\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...985..166K",
 "title": "Early Planet Formation in Embedded Disks (eDisk). XXI. Limited Role of Streamers in Mass Supply to the Disk in the Class 0 Protostar IRAS 16544-1604",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Kido, Miyu",
 "n_authors": 20,
 "arxiv_id": "2504.00495",
 "doi": "10.3847/1538-4357/adc72a",
 "alma_projects_linked_by_archive": [
  "2018.1.01205.L",
  "2019.1.00261.L",
  "2019.A.00034.S"
 ]
}
```

Paper text:
<paper>
# Early Planet Formation in Embedded Disks (eDisk) XXI: Limited role of streamers in mass supply to the disk in the Class 0 protostar IRAS 16544-1604

## Abstract

Asymmetric and narrow infalling structures, often called streamers, have been observed in several Class 0/I protostars, which is not expected in the classical star formation picture. Their origin and impact on the disk formation remain observationally unclear. By combining data from the James Cleark Maxwell Telescope (JCMT) and Atacama Large Millimeter/submillimeter Array (ALMA), we investigate the physical properties of the streamers and parental dense core in the Class 0 protostar, IRAS 16544$-$1604. Three prominent streamers associated to the disk with lengths between 2800 to 5800 au, are identified on the northern side of the protostar in the C$^{18}$O emission. Their mass and mass infalling rates are estimated to be in the range of (1–4)$\times$10$^{-3}$ $M_\odot$ and (1–5)$\times$10$^{-8}$ $M_\odot$ yr$^{-1}$, respectively. Infall signatures are also observed in the more diffuse extended protostellar envelope observed with the ALMA from the comparison to the infalling and rotating envelope model. The parental dense core detected by the JCMT observation has a mass of $\sim$0.5 $M_\odot$, sub to transonic turbulence of $\mathcal{M}$ $=$ 0.8–1.1, and a mass-to-flux ratio of 2–6. Our results show that the streamers in IRAS 16544-1604 only possess 2% of the entire dense core mass and contribute less than 10% of the mass infalling rate

of the protostellar envelope. Therefore, the streamers in IRAS 16544-1604 play a minor role in the mass accretion process onto the disk, in contrast to those streamers observed in other sources and those formed in numerical simulations of collapsing dense cores with similar turbulence and magnetic field strengths.

,

# Introduction

Protostars are formed when dense cores collapse under their self-gravity (cite: 1969Larson). Simultaneously, protostellar disks composed of gas and dust are formed around these forming protostars (cite: 1977Shu; 1984Terebey). In this early stage of star formation (Class 0 and I), the remaining gas in the dense core exists as an envelope, which actively accretes onto the disks.

As the protostellar system evolves from the Class I to Class II stages, protoplanets may form rapidly within the disks, as suggested by the limited substructures in young protostellar disks (cite: 2023Ohashi; 2023Han) compared to ubiquitous ring-gap structures observed in Class II disks (cite: 2018Andrews).

The kinematics and chemical properties of Class 0/I embedded disks are strongly influenced by mass accretion from the envelope (cite: 2024Tobin). Thus, investigating the accretion process onto the disks in the young protostellar stage is essential to understand the planet formation process in the disks.

Recent high-resolution (sub-)millimeter radio observations detected asymmetric, filament-like structures connected to protostellar disks around several protostars at various evolutionary stages from Class 0 to II, even though the conventional pictures of star formation assume spherically symmetric collapsing gas around a protostellar system (cite: 2012Tobin; 2014Tokuda; 2020Pineda; 2020Sai; 2021Huang; 2023Flores; 2023Aso; 2023Gupta; 2024Lee).

These structures are often called “streamers”, characterized by narrow gas flows with velocity structures suggestive of infalling motions, and they are presumed to supply both mass and angular momentum to the disks.

It has been suggested that streamers can play an important role in providing mass to the disk (cite: 2022Valdivia; 2022Thieme).

Similar streamers are often seen in numerical simulations of the gravitational collapse of magnetized and turbulent dense cores under various physical conditions.

These simulations highlight the critical role of streamers in delivering mass to the disk and their significance to the disk formation process (cite: 2015Seifried; 2017Kuffmeier; 2019Lam; 2023Tu; 2024Lebreuilly), where the mass delivered by streamers can reach 0.5 $M_\odot$ in some cases (cite: 2023Kuffmeier). However, observationally, the formation mechanism of streamers and their impact on the disk formation remain unclear.

IRAS 16544$-$1604 (hereafter IRAS 16544) is a Class 0 protostar located in the Ophiuchus North region (cite: 2020Zucker). The bolometric temperature is estimated to be 50 K (cite: 2023Ohashi). It is deeply embedded in a dense core elongated along the north-south direction with a size of 20,000 au (cite: 2000Vallee; 2014Bertrang; 2024Yen), and is associated with a bipolar outflow along the northwest-southeast direction (cite: 1996Wu; 2003Vallee; 2007Vallee; 2014Dunham). IRAS 16544 is one of the targets of the Atacama Large Millimeter/submillimeter Array (ALMA) large programs “Fifty AU Study of the chemistry in the disk/envelope system of Solar-like protostars (FAUST; (cite: 2022Imai))”. They revealed that IRAS 16544 harbors a hybrid chemistry with complex organic molecules detected around the protostar and warm carbon-chain chemistry molecules distributed on the envelope scale of 1000 au.

The ALMA large programs “Early Planet Formation in Embedded Disks (eDisk)” also targeted IRAS 16544 (cite: 2023Ohashi; 2023Kido), and their observations showed a $\sim$30 au dusty disk oriented in the northeast-southwest direction and inclined by $\lesssim$73$\ensuremath{^\circ}$ from the plane-of-sky.

The Keplerian disk has a radius of $\sim$55 au, and the protostellar mass is estimated to be 0.14 $M_\odot$ from the Keplerian rotation of the gas disk (cite: 2023Kido). Outside the Keplerian disk, several asymmetric, elongated components have been observed in C$^{18}$O ($J$ $=$ 2–1) emission in IRAS 16544. The spatial and velocity structures of one of them (northeastern component) has been analyzed, and is consistent with being a streamer (cite: 2023Kido). This previous analyses did not, however, perform complete census of all the streamer candidates nor estimate their mass and mass infalling rates including the proper estimate of the missing fluxes. Thus, quantitative estimate of the importance of those streamers on the mass accretion to the star plus disk system has not yet been conducted.

To investigate the role of streamers in the star and disk formation process, we conducted follow-up observations using the James Clerk Maxwell Telescope (JCMT) toward IRAS 16544. In this paper, we utilize the unique combination of the JCMT, FAUST, and eDisk data that have overlapping *uv* coverages and result in a large spatial dynamical range, and we study the physical properties of the parental dense core and streamers in IRAS 16544 in detail.

In Section [2](#sec:obs), we describe details of the JCMT and ALMA observations and data reduction. Our analysis to estimate physical parameters of the dense core and streamers is described in Section [3](#sec:results). Through these results, we discuss the origin of the streamers and their impact on the protostellar disk in Section [4](#sec:discussion). Finally, we summarize our findings in Section [5](#sec:summary). Comparison of the properties of the streamers probed with ALMA among all eDisk targets will be introduced in the forthcoming paper.

# Observations and data reduction

## JCMT

We observed IRAS 16544 in C$^{18}$O $J$ $=$ 2–1 (219.5603541 GHz) with the heterodyne receiver ‘Ū‘ū on JCMT in five nights between 2023 March and September as part of the eDisk follow-up project (Project codes: M23AP020, M23BP016; PI: J. Sai).

The sky opacity at 225 GHz ranged from 0.13 to 0.29. We mapped a square region of 120$\ensuremath{''}$$\times$120$\ensuremath{''}$ around the protostar with the raster scan mode. The bandwidth and spectral resolution were set to 250 MHz and 30.5 kHz (corresponding to 0.042 km s$^{-1}$), respectively.

The full width half maximum (FWHM) beam size was 21$\ensuremath{''}$.

The obtained data were reduced with `Starlink` version 2023A. The antenna temperature was converted to the main beam temperature ($T_\mathrm{mb}$) with the main beam efficiency of 0.66. The image cubes were binned to a channel width of 91.6 kHz, corresponding to 0.125 km s$^{-1}$. The rms noise level of 0.31 K per channel in $T_\mathrm{mb}$ was achieved.

## ALMA

We utilize the ALMA 12-m and 7-m array Band 6 data obtained with the large program eDisk (project code: 2019.1.00261.L, PI: N. Ohashi), the Director’s Discretionary Time program (project code: 2019.A.00034.S, PI: J. J. Tobin), and the large program FAUST (project code: 2018.1.01205.L, PI: S. Yamamoto). The details of the eDisk observations have been described in (cite: 2023Ohashi) and (cite: 2023Kido) while those of FAUST have been reported in (cite: 2022Imai).

The combination of these data sets has the baseline lengths from 9 m to 12595 m and the maximum recoverable scale (MRS) of 6.2$''$.

All the data were calibrated with the pipeline of the Common Astronomy Software Applications (CASA) package (cite: 2022CASATeam). We extracted the C$^{18}$O visibility data using the CASA task `mstransform` and subtracted the continuum using `uvcontsub`.

All the C$^{18}$O data were imaged together using the task `tclean` of CASA version 6.6 with the Briggs robust parameter of 2.0 and the mosaic gridder, resulting in a beam size of 0.30$''$$\times$0.22$''$ (P.A. $=$ 77$\ensuremath{^\circ}$). The velocity resolution was set to 0.167 km s$^{-1}$. The auto-masking function of clean was adopted with the sidelobe threshold of 1.5, noise threshold of 4.25, low noise threshold of 1.0, minimum beam fraction of 0.3, and negative threshold of 0.0. A primary beam correction was applied. The rms noise level of the final image cube was measured to be 1.35 mJy beam$^{-1}$ ($=$ 0.52 K) within the radius of 10$\ensuremath{''}$ from the protostar in the line-free channels before the primary beam correction.

## JCMT and ALMA combined map

We generated combined JCMT$+$ALMA 12-m and 7-m array maps of the C$^{18}$O emission. The JCMT cube was first regridded with `imregrid` to have the same spatial and velocity axes as the ALMA cube and multiplied by the primary beam pattern of the ALMA map created in Section [2.2](#datareduction:ALMA) with `immath`.

Then the ALMA and JCMT maps were combined using the `feather` task in CASA (cite: 2017Cotton; 2023Plunkett).

Finally, the combined map was divided by the ALMA primary beam pattern. The resulting beam size is 0.30$''$$\times$0.22$''$ (P.A. $=$ 77$\ensuremath{^\circ}$). The rms noise level in the combined map was measured to be 1.46 mJy beam$^{-1}$ ($=$ 0.56 K) within the radius of 10$\ensuremath{''}$ in the line-free channels before the primary beam correction.

# Analysis and Results

We adopt three different maps for our analysis, i.e., the JCMT only, ALMA 12-m and 7-m combined (ALMA-only), and JCMT$+$ALMA 12-m and 7-m combined (feathered) maps (see Section [2](#sec:obs)).

The JCMT-only map is used to study the mass and velocity field of the parental dense core (Section [3.1](#subsec:dense core by JCMT)). The ALMA-only map resolves structures on scales of several hundred au and is used to investigate the spatial and velocity structure of the streamers (Sections [3.2.1](#subsubsec:identified_streamers) and [3.2.2](#subsubsec:streamer properties)).

The feathered map can recover the extended emission at high resolution. It is used to study the more diffuse extended protostellar envelope and assess the effect of missing flux in the ALMA-only map (Sections [3.4](#subsubsec:missing flux) and [3.3](#subsec:model)).

## Dense core observed with JCMT

### Morphology and Mass

![image](./figures/line_profiles_with_mom0_ver2.pdf)\

Figure [1](#fig_JCMTline) displays the grid map of the C$^{18}$O (2–1) spectra taken by JCMT. All the spectra show a single velocity component, with the emission mainly detected within 1 km s$^{-1}$ with respect to the systemic velocity ($V_\mathrm{sys}$) of 5.0 km s$^{-1}$. Since the peak brightness temperature of 4.8 K is much lower than the average dust temperature of 15 K of the dense core (cite: 2013Launhardt), the C$^{18}$O emission is most likely optically thin.

The background image of Figure [1](#fig_JCMTline) and Figure [2](#fig_JCMT_nt)(a) show the integrated intensity (moment 0) map of the C$^{18}$O emission over the velocity range of $V_\mathrm{LSR}$ $=$ 4.0–6.0 km s$^{-1}$ for IRAS 16544, obtained using JCMT. The C$^{18}$O emission is elongated along the northwest-southeast direction. This direction is slightly shifted from that of the 850 $\mu$m dust continuum emission, which is elongated in the north-south direction (cite: 2024Yen), whereas the peak positions of the C$^{18}$O and dust continuum emission are coincident.

We estimate the C$^{18}$O column density under the assumption of the local thermodynamic equilibrium (LTE) condition.

The excitation temperature is assumed to be 15 K, which is the average dust temperature in the envelope on a 60$\ensuremath{''}$ scale, as derived from Herschel observations by (cite: 2013Launhardt). The mean molecular weight of 2.8 (cite: 2008Kauffmann) and the C$^{18}$O abundance relative to H$_2$ of 1.7$\times$10$^{-7}$ (cite: 1982Frerking) are adopted.

The mass within a box in the map of Figure [2](#fig_JCMT_nt)(a) ($\sim$ 9000$\times$9000 au$^2$) is estimated to be $\sim$0.52 $M_{\odot}$. If the excitation temperature is assumed to be 10 or 30 K, the estimated core mass becomes 15% higher. Our estimate is comparable to the previous estimates of 0.6–1.9 $M_{\odot}$ with radii of 1000-5000 au by (cite: 2010Launhardt) and (cite: 2014Bertrang) from the dust continuum emission.

### Velocity Structures

![image](./figures/JCMT_mom1_nonthermal_fwhmmap2.pdf)\

The Figure [2](#fig_JCMT_nt)(b) shows the mean velocity (moment 1) map of the C$^{18}$O emission, integrating the emission above 3$\sigma$. A weak velocity gradient on a 120$\ensuremath{''}$ scale can be seen from the northwest to southeast direction. In the central 60$\ensuremath{''}$ region, the velocity gradient is along the northeast-southwest direction. We measured the velocity gradient following the method in (cite: 1993Goodman) and found that the resulting magnitude is $\sim$1.68$\pm$0.34 km s$^{-1}$ pc$^{-1}$ with a position angle of 210$\pm$12$\ensuremath{^\circ}$ within a radius of 60$\ensuremath{''}$. The direction of the core-scale velocity gradient is similar to that of the disk rotation with a position angle of 225$\ensuremath{^\circ}$.

The C$^{18}$O line profiles in IRAS 16544 observed with JCMT are mostly symmetric with respect to the systemic velocity. Here, we divide the cloud into two regions, north and south, based on the declination offset of 0$''$. The broader line profiles are observed in the central and northern regions, while narrower profiles are seen in the southern region (Figure [1](#fig_JCMTline)).

We fit these spectra with a single Gaussian function. The fitting is performed for those spectra with a peak signal-to-noise ratio greater than 3.

The centroid velocity and full width at half-maximum (FWHM) line width of the spectrum at the protostellar position are measured to be $V_\mathrm{LSR}$ $=$ 5.07$\pm$0.01 km s$^{-1}$ and $\Delta V_\mathrm{total}$ $=$ 0.53$\pm$0.03 km s$^{-1}$, respectively.

We estimate the non-thermal gas motion by subtracting the thermal components from the measured C$^{18}$O linewidth as follows: $$\begin{equation}
\Delta V_\mathrm{NT} = \sqrt[]{\Delta V_{\rm total}^2 - \frac{kT}{m_\mathrm{C^{18}O}}8\ln2},
\end{equation}$$ where $\Delta$$V_\mathrm{NT}$ is the FWHM of the non-thermal component, $\Delta$$V_\mathrm{total}$ is the measured C$^{18}$O FWHM, $k$ is the Boltzmann constant, $T$ is the kinetic temperature, and $m_\mathrm{C^{18}O}$ is the C$^{18}$O molecular mass (cite: 2008Kauffmann). $\Delta$$V_\mathrm{total}$ is from our Gaussian fitting to the spectra. We assume a uniform gas kinetic temperature of 15 K to derive the non-thermal gas motion, and a possible range of the kinetic temperature of 10–30 K to estimate the uncertainty.

Figure [2](#fig_JCMT_nt)(c) shows the resultant FWHM map of the non-thermal motion in the dense core. It is larger in the northern region with an average $\Delta$$V_\mathrm{NT}$ of 0.61$^{+0.01}_{-0.02}$ km s$^{-1}$, while it is lower in the southern region with an average $\Delta$$V_\mathrm{NT}$ of 0.41$^{+0.01}_{-0.03}$ km s$^{-1}$. The Mach number, $\mathcal{M}$ $=$ $\sigma_\mathrm{NT}$/c$_s$ ($\Delta V_\mathrm{NT}$ $=$ $\sqrt[]{8\mathrm{log}2}\sigma_\mathrm{NT}$), is derived to be 1.1$^{+0.3}_{-0.2}$ in the northern region and 0.8$^{+0.2}_{-0.3}$ in the southern region.

Thus, the dense core has subsonic to transonic non-thermal gas motions within a radius of 60$\ensuremath{''}$.

### B-field strength

The magnetic field structures in this dense core have been revealed with JCMT SCUBA-2/POL-2 observations (cite: 2024Yen). We adopt the Davis-Chandrasekhar-Fermi (DCF) method (cite: 1951Davis; 1953Chandrasekhar) to estimate the magnetic field strength in the dense core as follows: $$\begin{equation}
|\boldsymbol{B}_\mathrm{pos}| = \xi\ \sqrt[]{4\pi\rho_\mathrm{gas}}\frac{\sigma_{\mathrm{NT}}}{\sigma_\theta},
\end{equation}$$ where $\xi$ is the correction factor to take account for variations of magnetic field and density structures along the line of sight, $\rho_\mathrm{gas}$ is the mean volume mass density,

$\sigma_{\mathrm{NT}}$ is the mean 1$\sigma$ line width of non-thermal gas motion, and $\sigma_\theta$ is the angular dispersion of the magnetic fields. $\sigma_{\mathrm{NT}}$ is calculated with the overlapping region of the 850 $\mu$m dust continuum emission and moment 0 map in Figure [2](#fig_JCMT_nt)(a), and it is 0.18–0.20 km s$^{-1}$. $\sigma_\theta$ was estimated to be 7$\ensuremath{^\circ}$–13$\ensuremath{^\circ}$ within a radius of 60$\ensuremath{''}$ from the protostar with the JCMT POL-2 data in (cite: 2024Yen).

$\xi$ of 0.5 is adopted since the angular dispersion is smaller than 25$\ensuremath{^\circ}$ (cite: 2001Ostriker; 2001Heitsch). In the 850 $\mu$m dust continuum emission, the dense core is roundish with a diameter of 140$\ensuremath{''}$ (black contours in Figure [2](#fig_JCMT_nt)(a)). Thus, we assume the depth of the dense core to also be 140$\ensuremath{''}$ and estimated the mean volume density to be

(6.1–7.1)$\times$10$^{-20}$ g cm$^{-3}$. Then, with the DCF method, the magnetic field strength is estimated to be 34–76 $\mu$G. If we adopt the formulation in (cite: 2021Skalidis), which considers

compressible and magnetized turbulence: $$\begin{equation}
|\boldsymbol{B}_\mathrm{pos}| = \sqrt[]{2\pi\rho_\mathrm{gas}}\frac{\sigma_{\mathrm{NT}}}{\sqrt[]{\sigma_\theta}},
\end{equation}$$ the magnetic field strength in the dense core is estimated to be 23–37 $\mu$G.

The dimensionless mass-to-flux ratio ($\mu_\mathrm{pos}$) of the dense core on the plane of sky is derived as: $$\begin{equation}
\mu_\mathrm{pos} = 2\pi\ \sqrt[]{G}\frac{\Sigma}{B_\mathrm{pos}},
\end{equation}$$ where $G$ is the gravitational constant and $\Sigma$ is the mean surface density (cite: 1978Nakano). $\Sigma$ is calculated from the total enclosed mass, e.g., the core and central protostellar masses, divided by the core area within a box of 60$\ensuremath{''}$ from the protostar. The mass-to-flux ratio in the dense core is estimated to be 1.5–3.8 with the DCF method and 3.1-5.7 with the method in (cite: 2021Skalidis), suggesting that the dense core of IRAS 16544 is supercritical.

## Infalling streamers observed with ALMA

### Spatial and velocity structures of streamers

![image](./figures/ALMA_channelmap_12+7m_robust2.0.png)\

Figure [3](#fig_channelmap) shows the C$^{18}$O velocity channel maps generated from the combined ALMA-only data. The peak brightness temperature within the radius of 15$\ensuremath{''}$ is 12 K. Thus, the C$^{18}$O emission is most likely optically thin. The C$^{18}$O emission associated with the disk is detected at $V_\mathrm{LSR}$ $<$ 4.02 km s$^{-1}$ and $V_\mathrm{LSR}$ $>$ 6.36 km s$^{-1}$, as described in detail in (cite: 2023Kido). Here, we focus on the extended structures at the lower velocities.

Several elongated structures with lengths of 2$\ensuremath{''}$ to 20$\ensuremath{''}$ are detected around the protostar in the velocity channel maps. The three most prominent ones with peak intensities of 11–12 K are observed in the northeast at $V_\mathrm{LSR}$ $=$ 4.19–5.02 km s$^{-1}$, in the northwest at $V_\mathrm{LSR}$ $=$ 4.36–5.02 km s$^{-1}$, and in the north-northwest at $V_\mathrm{LSR}$ $=$ 5.19–6.03 km s$^{-1}$, (see Figure [3](#fig_channelmap)).

These elongated structures are unlikely to be associated with outflows because their velocity structures are different from those of typical outflows (cite: 2007Arce; 2024Lopez-Vazquez). The emission at the higher velocities is detected in the vicinity of the protostar, while that at the lower velocities is farther away from the protostar. Furthermore, the blueshifted outflow is observed on the southeastern side (P.A. $\sim$ 135$\ensuremath{^\circ}$), while the redshifted outflow is on the northwestern side (P.A. $\sim$ $-$17$\ensuremath{^\circ}$). The two blueshifted elongated structures are in the north, opposite to the direction of the velocity gradient of the blueshifted outflow (cite: 2023Kido).

On the other hand, both the redshifted elongated structure and the redshifted outflow are located to the northwest, and there is a slight overlap of the velocities between the redshifted outflow ($V_\mathrm{LSR}$ $=$ 5–20 km s$^{-1}$) and the redshifted elongated structure. Thus, in contrast to the two blueshifted elongated structures, it is possible that the redshifted elongated structure traces parts of the molecular outflow, however, this does not affect our conclusion in the present paper, as discussed below. On the contrary, as we show below, the detailed spatial and velocity structures suggest that the nature of the redshifted elongated structure is the same as those of the two blueshifted elongated structures.

Figure [4](#fig_almamom0)(a) and (b) show the moment 0 maps of the C$^{18}$O emission at the blue- and redshifted velocities, respectively. In the moment 0 maps, the three most prominent elongated structures are clearly seen in the northeast (NE), northwest (NW), and north-northwest (NNW) regions. The blueshifted NE elongated structure has been suggested to be an infalling streamer by (cite: 2023Kido) (hereafter NE streamer). Below we examine the spatial and velocity structures of the other two elongated structures in comparison with those of the NE streamer.

Blue and red lines in Figure [4](#fig_almamom0) represent the free-fall trajectories coincident with the elongated structures. These trajectories are derived with the infall-rotating envelope model in (cite: 1976Ulrich) and (cite: 1981Cassen), which is often called the UCM model and adopted to describe the kinematics of infalling material (cite: 2014Yen; 2020Pineda; 2023Flores; 2023Aso; 2024Lin; 2022Thieme). This model assumes that a particle falls toward a point mass with a conserved angular momentum and zero initial energy.

The model has 6 free parameters: stellar mass $M_*$, centrifugal radius $r_\mathrm{d}$, the initial polar angle $\theta_0$ and azimuthal angle $\phi_0$ of the particle, and two parameters $i_\mathrm{s}$ and $\theta_\mathrm{s}$ for the direction of the rotational axis. The spatial and velocity structures of the NE streamer have been successfully reproduced with this model in (cite: 2023Kido) obtaining the values of $M_*$ $=$ 0.14 $M_\odot$, $r_\mathrm{d}$ $=$ 100 au, $\theta_0$ $=$ 90$\ensuremath{^\circ}$, $\phi_0$ $=$ 64$\ensuremath{^\circ}$, *i*$_\mathrm{s}$ $=$ 73$\ensuremath{^\circ}$, and $\theta_\mathrm{s}$ $=$ 60$\ensuremath{^\circ}$.

To compare the morphologies of the NW and NNW elongated structures with the model infalling trajectories, we assume that their rotational axes are aligned with the disk and that their centrifugal radii are the same as the gas disk radius. Thus, we fix *i*$_\mathrm{s}$ $=$ 107$\ensuremath{^\circ}$, $\theta_\mathrm{s}$ $=$ $-$45$\ensuremath{^\circ}$, $r_\mathrm{d}$ $=$ 55 au, and $M_*$ $=$ 0.14 $M_\odot$, as measured by (cite: 2023Kido).

There remains only two free parameters: $\theta_0$ and $\phi_0$. We visually inspect and compare the observed structures with the model trajectories of all combinations of the parameters, and find that the model trajectory with $\theta_0$ of 20$\ensuremath{^\circ}$ and $\phi_0$ of $-$10$\ensuremath{^\circ}$ can match the NW elongated structure and that with $\theta_0$ of 70$\ensuremath{^\circ}$ and $\phi_0$ of $-$120$\ensuremath{^\circ}$ can match the NNW elongated structure, as shown in Figure [4](#fig_almamom0)(a) and (b). We note that there are other parameter combination that can also explain the observed emissions and we discuss the degeneracy of the parameters in Section [4.1](#subsubsec:dis_Degeneracy).

Figure [5](#fig_streamerpv) presents the Position–Velocity (PV) diagrams of the elongated structures cut along the model infalling trajectories. The model velocity structures (white lines) follow the observed emission (color scale), with the emission at higher velocities becoming more dominant closer to the protostar. These velocity structures are consistent with the UCM model. Note that the bright components seen at the highest redshifted velocity in the PV diagrams for the NE and NW structures and at the highest blueshifted velocity in that for the NNW structure are smoothly connected to the Keplerian components associated with the disk.

### Mass infalling rates of streamers

![](./figures/mom0maps_12+7m_robust2.0_lines2.png)

![](./figures/12+7m_streamer_PVdiagrams_ver2.png)

The comparison with the UCM model suggests that the three elongated structures (NE, NW, and NNW) likely trace infalling streamers. We set the 3$\sigma$ emissions in the moment 0 maps (Figure [4](#fig_almamom0)) as the edge of the streamers.

The NE, NW, and NNW streamers are detected at velocities of $V_\mathrm{LSR}$ $=$ 3.6–4.7 km s$^{-1}$, $-$0.1–4.9 km s$^{-1}$, and 5.2–6.8 km s$^{-1}$, respectively, as shown in their PV diagrams. For each streamer, we generate a moment 0 map integrating over its velocity range (see first column of Figure [10](#fig_different_model)). We estimate its width covering the emission above the 3$\sigma$ level in its moment 0 map. The widths of the three streamers are estimated to be 450 to 900 au,

and the lengths are estimate to be $\sim$1300 au on the plane of the sky.

Then we calculate the integrated C$^{18}$O flux of the streamer in its moment 0 map and estimated its mass with the same method described in Section [3.1.1](#subsubsec:dense core mass).

The masses of the NE, NW, and NNW streamers are estimated to be 1.3$^{+1.4}_{-0.2}$$\times$10$^{-3}$, 2.2$^{+2.1}_{-0.4}$$\times$10$^{-3}$, and 4.0$^{+4.0}_{-0.6}$$\times$10$^{-3}$ $M_{\odot}$, respectively. The uncertainties originate from the possible ranges of the C$^{18}$O abundance of (1–2)$\times$10$^{-7}$ (cite: 2022GOng) and the excitation temperature of 10–30 K.

The lengths of the NE, NW, and NNW streamers in three-dimensional space are estimated to be $\sim$4790 au, $\sim$2830 au, and $\sim$6130 au, respectively, based on the infalling trajectories from the UCM model.

Their free-fall timescales are calculated to be 1.0$\times$10$^5$, 4.5$\times$10$^4$, and 1.4$\times$10$^5$ yr from their lengths divided by their free-fall speeds at their lengths ($t_\mathrm{ff}$ $=$ $\sqrt{{R^3} / {2GM_*}}$), and the mass infalling rates are estimated to be 1.3$^{+1.4}_{-0.2}$$\times$10$^{-8}$, 4.8$^{+4.7}_{-0.7}$$\times$10$^{-8}$, and 2.8$^{+2.7}_{-0.4}$$\times$10$^{-8}$ $M_{\odot}$ yr$^{-1}$ using their estimated masses and infalling timescales for the NE, NW, and NNW streamers, respectively.

## Infalling protostellar envelope observed with ALMA and JCMT

![image](./figures/mom0maps_12+7m_feathering.png)\

![image](./figures/ALMA_channelmap_feathering.png)\

![image](./figures/major_minor_pv.pdf)\

Figure [6](#fig_feather_mom0) compares the C$^{18}$O moment 0 maps generated with the ALMA-only (a) and feathered data (b). In addition to the emission extended to the northern side seen in the ALMA-only map, additional extended emission with a roundish distribution around the protostar is enhanced in the feathered map. In the velocity channel maps of the feathered data (Figure [7](#fig_channelmap_feather)), the emission near the systemic velocity is recovered, and prominent extended emission is more visible on the western and southern sides at velocities from 4.86 to 5.36 km s$^{-1}$, distinct from the narrow elongated structures of the streamers. While these extended components tend to have lower brightness temperature ($<$ 10 K) than that of the streamers (11–12 K), their area is significantly larger than that of of the streamers. As seen in the velocity channels at 5.02 and 5.19 km s$^{-1}$, the extended emission is distributed approximately across the entire field of view.

This suggests that the streamers comprise only a portion of the entire protostellar envelope.

The PV diagrams cut along the disk major and minor axes of the C$^{18}$O emission from the feathered image cube are presented in Figure [8](#fig_majorpv). The PV diagrams show a diamond-shaped feature suggestive of a rotating and infalling envelope (cite: 1997Ohashi; 2014Ohashi; 2014Sakaib; 2016Oya; 2018Takakuwa; 2022Okoda).

We construct kinematical models of an infalling and rotating protostellar envelope with an embedded Keplarian disk to compare with the observed PV diagrams. Following (cite: 2024Takakuwa), we adopt the description of an infalling and rotating envelope from the UCM model and included an axisymmetric flared disk at the center in our kinematical model. The density profile of the model envelope is scaled to match the core mass and size of IRAS 16544 observed with JCMT. The mass, radius, and orientation of the model disk are adopted to be the same as those in IRAS 16544 observed with ALMA (cite: 2023Kido). For simplicity, the model assumes an isothermal temperature of 15 K as the C$^{18}$O emission in IRAS 16544 is likely optically thin.

All the model parameters are listed in Table[1](#table:model parameters).

|                     |                                |
|:--------------------|:------------------------------:|
| radial range        |           1-9000 au            |
| distance            |             151 pc             |
| stellar mass        |         0.14 $M_\odot$         |
| disk radius         |             55 au              |
| disk mass           | 1.0$\times$10$^{-2}$ $M_\odot$ |
| disk P.A.           |    45$\ensuremath{^\circ}$     |
| disk inclination    |    73$\ensuremath{^\circ}$     |
| envelope mass       |         0.52 $M_\odot$         |
| C$^{18}$O abundance |      1.7$\times$10$^{-7}$      |

: Parameters adopted in the protostellar disk+envelope model.

We then perform radiative transfer calculations using RADMC-3D (cite: 2012Dullemond) and generate a model C$^{18}$O image cube of our kinematical model. Our model adopts the dust opacity table in (cite: 2003Semenov) and the C$^{18}$O abundance of 1.7$\times$10$^{-7}$, assuming LTE condition.

The model images are convolved with a Gaussian beam of the same size as that of our feathered map of the C$^{18}$O emission. The PV diagrams cut along the disk major and minor axes extracted from the model image cube are overlaid on the observed ones in Figure [8](#fig_majorpv). The observed PV diagrams indeed show similar velocity structures to those of the isotropic infalling and rotating envelope model. Along the major axis, both diagrams show tilted, diamond-shaped features.

Along the minor axis, infalling motion is expected to induce a clear velocity gradient, where the northern part is more redshifted with fainter blueshifted emission and the southern part is more blueshifted with fainter redshifted emission, as seen in the model PV diagram. This feature is also seen in the observed PV diagram.

We note that the PV cuts and the trajectories of the streamers intersect. The positions and velocities of these intersections are labeled with the colored dots in the PV diagrams. There is only a minor contribution from the streamers in the PV diagrams.

The majority of the emission in the PV diagrams is from the extended envelope and shows the feature of infalling motion.

The good agreement between the observed and the model velocity structures in the PV diagrams suggests that the extended envelope observed in the feathered map is also infalling. Meanwhile, in addition to the detection of streamers, the observed intensity distribution cannot be fully explained by our axisymmetric envelope model, so that the density distribution of the protostellar envelope around IRAS 16544 is probably not axisymmetric.

## Influence of the Missing Flux

![](./figures/JCMT_ALMA_feather_flux_with_inset.pdf)

Although all three streamers have widths smaller than the MRS of 6.2$''$ as shown in the first column of Figure [10](#fig_different_model), we assess the possible bias due to the missing flux in the ALMA-only data by comparing the fluxes measured in the JCMT, ALMA-only, and feathered maps.

For this purpose, we regridded the velocity axis of the JCMT data to match that of the ALMA data using `imregrid` and then measured the flux within the ALMA field of view (FOV). Figure [9](#fig_missingflux) shows the comparison of the C$^{18}$O spectra integrated over the ALMA FOV from the JCMT, ALMA-only, and feathered images.

The spectrum of the feathered image coincides with that of the JCMT-only image, showing that the flux is properly recovered with the feathered procedure. Significant missing flux of more than 90% is seen within 0.2 km s$^{-1}$ from $V_\mathrm{sys}$ in the ALMA-only data, and the missing flux reduces to 65% at the velocities within 1.0 km s$^{-1}$ from $V_\mathrm{sys}$.

To assess the influence of this missing flux on our estimate of the streamer mass using the ALMA-only data, we also calculated the mass from the C$^{18}$O flux in the same area and velocity ranges using the feathered data, and the estimated mass becomes 20% to 50% higher than the ALMA-only data.

Thus, the influence of the missing flux on the streamers is limited.

Furthermore, the masses estimated using the ALMA data with and without the 7-m array data are almost identical (see Appendix [\[appndix:channelmap\]](#appndix:channelmap)), which suggests that the missing flux in the ALMA-only data can be primarily attributed to filtering out the extended diffuse envelope component.

Therefore, in the subsequent discussion, we adopt the streamer mass estimated with the ALMA-only data to avoid the contamination from the extended diffuse envelope component.

# Discussion

## Degeneracy of the UCM model

In our analysis of the infalling trajectories of the NW and NNW streamers in Section [3.2.1](#subsubsec:identified_streamers), their centrifugal radii and rotational axes are assumed to be the same as the radius and the rotational axis of the gas disk, and the initial position of the infalling material is estimated to be ($\theta_0$, $\phi_0$) $=$ (20$\ensuremath{^\circ}$, $-$10$\ensuremath{^\circ}$) and (70$\ensuremath{^\circ}$, $-$120$\ensuremath{^\circ}$), respectively.

We note that these solutions are not unique because of the projection effect.

Changing $\theta_0$ and $\phi_0$ by 10$\ensuremath{^\circ}$ to 40$\ensuremath{^\circ}$ can still result in other possible solutions that have spatial and velocity structures similar to the observations.

For example, the models with $\theta_0$ $=$ 30$\ensuremath{^\circ}$ and $\phi_0$ $=$ 30$\ensuremath{^\circ}$, and $\theta_0$ $=$ 40$\ensuremath{^\circ}$ and $\phi_0$ $=$ $-$140$\ensuremath{^\circ}$ can also reproduce the NW and NNW streamers, respectively.

If we allow the rotational axes and centrifugal radii of model streamers to differ from those of the gas disk of IRAS 16544, there are more possible infalling models that can match the observed spatial and velocity structures.

For example, with the parameters of $i_s$ $=$ 30$\ensuremath{^\circ}$, $\theta_s$ $=$ $-$30$\ensuremath{^\circ}$, $r_d$ $=$ 100 au, $\theta_0$ $=$ 20$\ensuremath{^\circ}$, and $\phi_0$ $=$ 75$\ensuremath{^\circ}$, the model infalling trajectory projected on the plane of sky and its corresponding line-of-sight velocity can explain the observation of the NNW streamer (Figure [10](#fig_different_model)(l) and (k)). Figure [10](#fig_different_model) demonstrates such a degeneracy of the models for each of the three streamers and these model parameters are listed as different model parameters in Table [2](#table:different model) (Appendix [6](#appndix:Alternative model)).

Although there is degeneracy in the derived infalling trajectories, the mass infalling rates estimated with these different trajectories only vary within a factor of four (Table [2](#table:different model)). This is because the mass infalling rate primarily depends on the length of a streamer. The conservative upper limit of the mass infalling rate can be given by the shortest length, which is the length projected on the plane of the sky, $\sim$1300 au. This approach yields mass infalling rates of 1 to 2$\times$10$^{-7}$ $M_\odot$ yr$^{-1}$, which remains an order of magnitude lower than that of the extended diffuse envelope.

Therefore, these uncertainties in the infalling trajectories do not affect our discussion on the contribution to mass accretion by the streamers in IRAS 16544.

In the case of the NE streamer, Figure [10](#fig_different_model)(c) and (d) show that with a rotational axis and a centrifugal radius aligned with the gas disk and the parameters of $\theta_0$ $=$ 70$\ensuremath{^\circ}$ and $\phi_0$ $=$ 73$\ensuremath{^\circ}$,

the model trajectory can reasonably explain the observed spatial and velocity structures at outer radii larger than 400 au.

However, this model trajectory is different from that adopted in (cite: 2023Kido) and does not pass through the curling SO and SiO emissions observed around the gas disk, which possibly traces the accretion shocks due to the collision between the streamer and disk (cite: 2023Kido).

Thus, observing the distributions of different molecules, such as shock tracers (cite: 2023Lee), may help to disentangle different model trajectories.

## Mass accretion via streamers

Three prominent elongated structures are observed in our ALMA data. Their morphologies and velocity structures are consistent with the trajectories and velocities of infalling material toward IRAS 16544. Therefore, these elongated structures most likely trace infalling streamers toward the protostar. The total mass of the three streamers is estimated to be $\sim$7.5$\times$10$^{-3}$ $M_\odot$ and is only $\sim$2$\%$ of the total mass of the dense core with a box of 9000 au even after considering the possible effect of missing fluxes.

Even if we compare this value to the dense core mass within a radius of 4000 au, which corresponds to the estimated length of the streamers in the 3D space, the mass of the streamers is still only $\sim$6$\%$ of the total core mass.

Therefore, these streamers only possess a small fraction of the mass reservoir of IRAS 16544. We note that there could be more, unidentified streamers existing in the dense core of IRAS 16544. For example, an elongated structure toward the east is also observed at the velocities of $V_\mathrm{LSR}$ $=$ 5.02–5.36 km s$^{-1}$ in the velocity channel maps (Figure [3](#fig_channelmap)). However, this emission is much fainter than the three most prominent streamers, so that its mass contribution is likely even smaller.

The mass infalling rates of these streamers are estimated to be 1 to 5$\times$10$^{-8}$ $M_\odot$ yr$^{-1}$ (Section [3.2.2](#subsubsec:streamer properties)). These estimates depend on the estimated length of the streamers in the 3D space. Although there could be degeneracy in the inferred infalling trajectories (see Section [4.1](#subsubsec:dis_Degeneracy)), we found that the estimated streamer lengths in all cases are comparable, and thus the derived infalling time and mass infalling rate are similar, within a factor of four. As discussed in Section [4.1](#subsubsec:dis_Degeneracy), a conservative estimate of mass infalling rates of streamers is calculated to be 1 to 2$\times$10$^{-7}$ $M_\odot$ yr$^{-1}$, and these values can be considered as the upper limits.

These estimated mass infalling rates of the streamers are more than an order of magnitude lower than the theoretically expected mass infalling rate of $\sim$2$\times$10$^{-6}$ $M_\odot$ yr$^{-1}$ in a collapsing isothermal and spherical dense core in the conventional model (cite: 1977Shu).

In IRAS 16544, in addition to the streamers, the extended gas around the protostar observed with ALMA is also infalling (see Section [3.3](#subsec:model)). With the dense core mass within a radius of 4000 au measured with JCMT and the free-fall velocity at this radius calculated from the central protostellar mass, the mass infalling rate in the protostellar envelope is estimated to be 1 to 5$\times$10$^{-6}$ $M_\odot$ yr$^{-1}$ in IRAS 16544, which is similar to the conventional picture and those observed in other Class 0 protostars (cite: 1997Ohashi; 1998Momose; 2013Takakuwa; 2015Aso; 2019Yen). This is one or two orders of magnitude higher than the estimated mass infalling rate of the streamers.

Therefore, the streamers in IRAS 16544 most likely have limited contribution to the mass infall onto the central protostar+disk system.

The mass accretion rate ($\dot{M}_\mathrm{acc}$) onto the protostar in IRAS 16544 is estimated to be 3.0$\times$10$^{-7}$ $M_\odot$ yr$^{-1}$ from the luminosity of the protostar as:

$$\begin{equation}
    \dot{M}_{acc} = \frac{L_{acc}R_*}{GM_*}, 
\end{equation}$$ where ${L}_\mathrm{acc}$ is the accretion luminosity, $R_*$ is the stellar radius, $M_*$ is the stellar mass, and $G$ is the gravitational constant. The bolometric luminosity ($L_\mathrm{bol}$) of IRAS 16544 is 0.89 $L_\odot$ (cite: 2023Ohashi), which is the sum of the stellar luminosity ($L_{*}$) and the accretion luminosity ($L_\mathrm{acc}$). Assuming that the accretion luminosity is 50$\%$ of the bolometric luminosity (cite: 2008Dunham; 2008Antoniucci) and the stellar radius is 3 $R_\odot$ (cite: 1988Stahler).

This estimation tells us that the mass infalling rate of the streamers is a factor of several lower than the mass accretion rate onto the protostar or is comparable to it if we consider the conservative upper limit of the mass infalling rate of the streamers (Section [4.1](#subsubsec:dis_Degeneracy)).

If the streamers are the main mass supply to the disk and fully accreted onto the disk, the total disk$+$streamer mass would be consumed in $\sim$3$\times$10$^4$ yr by the mass accretion from the disk onto the protostar, assuming that the mass accretion onto the protostar is constant.

Then the disk lifetime would be shorter than the typical time scale of the Class 0 and I stages (cite: 2022Mercimek).

Hence, the mass infall from the extended protostellar envelope onto the disk, in addition to the streamers, likely plays a more important role in the star formation process in IRAS 16544, unless the streamers are connected to a larger mass reservoir beyond the field of the view of our ALMA observations.

In other protostars exhibiting streamers, the mass infalling rates of the streamers are mostly on the order of 10$^{-6}$ $M_\odot$ yr$^{-1}$ (cite: 2017Yen; 2021Pineda; 2022Thieme; 2022Valdivia; 2023Flores; 2023Hsieh; 2024Cacciapuoti; 2024Taniguchi; 2024Lin).

This is comparable to the mass infalling rate in the classical model of collapsing dense cores. In these protostars, their streamers may play a more significant role in the star formation process, unlike the case of IRAS 16544. On the other hand, some other protostars have streamers with mass infalling rates on the order of 10$^{-7}$ $M_\odot$ yr$^{-1}$ (cite: 2014Yen; 2022Thieme; 2022Murillo; 2024Codella).

More statistical studies on streamers compared to global infall in protostellar envelopes are needed to understand their importance in star formation.

Even though in IRAS 16544 the mass infalling rate of the streamers is low, on the order of 10$^{-8}$ $M_\odot$ yr$^{-1}$, the streamers may still be able to cause accretion shocks on the disk, as demonstrated in numerical simulations (cite: 2015Lesur). Indeed, typical shock tracers, such as SO and SiO (cite: 2015Aota; 2017Miura; 2021vanGelder; 2023Yamato; 2023Flores; 2023van’tHoff), have been detected in the NE streamer (cite: 2023Kido), which could be due to sublimation/sputtering of dust grains caused by the mutual interactions between the NE streamer and protostellar disk. Observations resolving the shock regions in molecular lines are essential to reveal the physical and chemical impact of these streamers on the disk.

## Formation mechanisms of streamers

Theoretically, streamer-like structures can form via several mechanisms: (1) collapse of turbulent and magnetized dense cores (cite: 2023Tu; 2015Seifried), (2) interactions with stellar flyby (cite: 2023Cuello; 2023Smallwood), (3) encounter with cloudlet components (cite: 2019Dullemond; 2024Hanawa), and (4) collision between dense cores or between dense cores and filaments (cite: 2024Yano; 2024Nakamura).

A flyby is a perturber encountering a central star in a parabolic or hyperbolic orbit. If the central star is harboring a disk,

their mutual interaction can lead to the formation of spirals and a bridge connecting the two stars, and such structures may appear like streamers (cite: 2023Cuello; 2024Smallwood).

IRAS 16544 is embedded in the globule CB 68 located at the edge of the filament in the Ophiuchus North region. It is the only compact source detected within a radius of 100$\ensuremath{''}$ ($\sim$ 15,000 au) from the globule (cite: 1995Wang; 1999Huard).

The closest objects to IRAS 16544 on the plane-of-sky are located 15$\ensuremath{'}$ ($\sim$1.3$\times$10$^5$ au) away, which are young stellar objects (cite: 2000Tachihara; 2012Hatchell).

Therefore, it is unlikely that a flyby encounter has occurred in IRAS 16544.

Toward IRAS 03292$+$3039, a streamer component seen in molecular tracers of chemically-fresh material is connected with a cloudlet $\sim$8000 au in size, which is $\sim$0.1 pc away from the protostar (cite: 2024Taniguchi). This is an example of streamers produced by the cloudlet component. While the streamers in IRAS 16544 are also traced by the CCH emission, a prototypical tracer of chemically-young molecular gas (cite: 2022Imai), the JCMT C$^{18}$O moment 0 map shows only a single peak in the dense core without any cloudlet component.

Therefore, the streamers in IRAS 16544 are unlikely to be caused by the accretion from passing cloudlets.

However, it is important to note that the resolution of our JCMT observations, 21$\ensuremath{''}$ (or $\sim$3200 au), could smooth out 1000 au sized cloudlets, if any. Future mosaic observations at high resolution over the wider area will help us to reveal the density distribution in the globule CB 68 in more detail.

When a protostellar dense core collides with another dense core or a filament, a shocked-compressed layer can form. This layer may gradually transform into a spiral structure connecting to the disk by the stellar gravity, and eventually appear as a streamer (cite: 2024Yano; 2024Nakamura).

In the JCMT C$^{18}$O data, only a single velocity component is observed (Figure [1](#fig_JCMTline)), and the non-thermal linewidth is small ($\Delta$$V_\mathrm{NT}$ $\leq$ 1.0 km s$^{-1}$). Although the shocked gas tracers have been detected in IRAS 16544 (cite: 2023Kido), they are in the vicinity of the central disk. Hence, there is no sign of collision between the dense core of IRAS 16544 and another component.

Simulations of the collapse of magnetized dense cores, both with and without initial turbulence, often show several accretion flows connecting to the disk, which are similar to streamers in observations (cite: 2017Kuffmeier; 2019Lam; 2023Tu; 2024Lebreuilly).

Without turbulence, the high magnetic pressure pushes ambient gas away and forms low-density cavities when the magnetic flux is released from the material accreted onto the protostar. Streamer-like accretion flows then appear along these cavities. These accretion flows are most concentrated in the equatorial plane of the disk around the central star. With turbulence, the pseudo disk can be warped or fragmented and appears as accretion flows. These flows often extend vertically away from the equatorial plane of the disk.

Our analysis shows that IRAS 16544 has subsonic to transonic turbulence and a mass-to-flux ratio of 2–6 in the dense core. These levels of turbulence and magnetic field strength are comparable to those in the simulations of (cite: 2023Tu). In addition, the streamers in IRAS 16544 likely extend away from the midplane. Thus, the streamers in IRAS 16544 could be similar to those formed in the simulations of magnetized and turbulent dense cores.

However, these simulations show that the streamers are the main channels of mass accretion, and the density is enhanced by a factor of $\sim$30 in the streamers compared to the initial mean density of the dense core (cite: 2023Tu). In contrast, the streamers in IRAS 16544 have limited contribution to mass accretion toward the central protostar$+$disk system, and their density is only a factor of a few higher than the mean density of the dense core observed with JCMT. Thus, the streamers observed in IRAS 16544 are not as prominent as those seen in the simulations. While we observe streamers in IRAS 16544, their underlying formation mechanisms remains unclear. Further comparison of the density and velocity structures of the streamers in the theoretical simulations and observations is required to clarify the difference.

Thus, the origin of the streamers in IRAS 16544 is not adequately explained with the formation mechanisms mentioned above. We note that on an even larger scale, there is a bridge component connecting the dense core of IRAS 16544 and the C$^{18}$O core q2 which has the characteristic of a YSO, located 15$\ensuremath{'}$ ($\sim$1.3$\times$10$^5$ au) to the northwest (cite: 2000Tachihara; 2012Hatchell). This is detected by the Herschel continuum maps at 100, 160, 250, 350, and 500 $\mu$m and Digitized Sky Survey (DSS2) optical red image (cite: 2013Launhardt).

Streamers connecting to central protostellar systems and extending beyond associated dense cores have been observed in other protostars (cite: 2020Pineda), suggesting that the material may be funneled from outside the dense core. In IRAS 16544, all the prominent streamers are observed on the northern side in the dense core, where there is a large-scale bridge component. However, the relation between the streamers and the large scale bridge is not clear. To explore the potential connection between the streamers in IRAS 16544 and this bridge, high resolution observations covering a broader area are essential. These observations can clarify if the streamers in IRAS 16544 are part of a larger structure funneling mass transfer from the bridge to the protostar.

# Summary

We have analyzed the C$^{18}$O emission observed with JCMT and ALMA to investigate the kinematics and physical properties of the dense core, protostellar envelope, and streamers in IRAS 16544. The main results of our analysis are summarized as follows:

- The mass of the dense core derived from the JCMT observation is estimated to be $\sim$0.52-0.60 $M_\odot$. The Mach number ranges from 0.8 to 1.1, suggesting that the dense core has a subsonic to transonic level of turbulence. With the magnetic angular dispersion reported in (cite: 2024Yen), the magnetic field strength is estimated to be 23–76 $\mu$G, corresponding to a dimensionless mass-to-flux ratio of 2–6, making the core supercritical.

- Elongated structures with projected lengths of $\sim$1300 au are detected on the northern side of the disk by the ALMA observations. Their spatial and velocity structures can be explained with the kinematical model of free-falling streamers with a conserved angular momentum and zero total energy. Their lengths in 3D space are estimated to be 2800–6100 au based on the infall model. The mass and mass infalling rate of these streamers are estimated to be (1–4)$\times$10$^{-3}$ $M_\odot$ and (1–5)$\times$10$^{-8}$ $M_\odot$ yr$^{-1}$, respectively. The impact of missing flux is limited, based on a comparison with the JCMT$+$ALMA combined map. In addition to the streamers, there is a more extended protostellar envelope observed in the JCMT$+$ALMA combined map, and its mass infalling rate is estimated to be (1–5)$\times$10$^{-6}$ $M_\odot$ yr$^{-1}$ calculated from the JCMT observation. Compared to the protostellar envelope, the contribution of mass supply to the disk via the streamers is relatively small.

- The streamers in IRAS 16544 are unlikely formed due to a flyby, accretion of a cloudlet, or core-core/filament collision. The dense core of IRAS 16544 is turbulent and magnetized. Numerical simulations of collapsing dense cores with similar conditions often form streamers (cite: 2023Tu; 2015Seifried). In these simulations, the mass contribution from the streamers is dominant compared to the envelope, and they are the main channels of mass accretion. In contrast, the streamers in IRAS 16544 have a total mass of 7.5$\times$10$^{-3}$ $M_\odot$, only accounting for $2\%$ of the dense core mass. This is different from those numerical simulations. The origin of the streamers in IRAS 16544 is yet to be elucidated by future observational and theoritical studies.

# Acknowledgments

We are grateful to the anonymous referee for the helpful and constructive comments. We would like to thank all the ALMA staff supporting this work. This paper makes use of the following ALMA data: ADS/JAO.ALMA #2018.1.01205.L, 2019.1.00261.L, and 2019.A.00034.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

M.K. is supported by the TIGP-X Pilot Program, Academia Sinica, Taipei, Taiwan and by JSPS KAKENHI grant Number 24KJ1834. H.-W.Y. acknowledges support from the National Science and Technology Council (NSTC) in Taiwan through the grant NSTC 113-2112-M-001-035- and from the Academia Sinica Career Development Award (AS-CDA-111-M03). S.T. is supported by JSPS KAKENHI grant Nos. 21H00048 and 21H04495, and by NAOJ ALMA Scientific Research grant No. 2022-20A. N.O., C. F., and M.N. acknowledge support from National Science and Technology Council (NSTC 113-2112-M-001-037) and the Academia Sinica Investigator Project Grant (AS-IV-114-M02). Y.A. acknowledges support by NAOJ ALMA Scientific Research Grant code 2019-13B, Grant-in-Aid for Scientific Research (S) 18H05222, and Grant-in-Aid for Transformative Research Areas (A) 20H05844 and 20H05847. I. H. acknowledges support the funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (Grant agreement No. 101098309 - PEBBLES) P.M.K. acknowledges support from NSTC 108-2112- M-001-012, NSTC 109-2112-M-001-022 and NSTC 110-2112-M-001-057. W.K. was supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (RS-2024-00342488). J.-E.L. was supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (grant numbers 2021R1A2C1011718 and RS-2024-00416859). Z.-Y.L. is supported in part by NASA NSSC20K0533, NSF AST-1910106 and Virginia Institute for Theoretical Astronomy. L.W.L. acknowledges support from NSF AST-2108794. R.S acknowledge support from the Independent Research Fund Denmark (grant No. 0135-00123B). K. T. is supported by JSPS KAKENHI grant Nos. 21H04495, 21H04487, and 22KK0043. J.P.W. acknowledges support from NSF AST-2107841.

# Software

CASA (cite: Mcmullin2007), matplotlib (cite: Hunter2007), PVextractor (cite: 2016Ginsburg), astropy (cite: 2022Astropy)

JCMT, ALMA

# Alternative models of infalling trajectories

![image](./figures/streamers_SLAM.png)\

Figure [10](#fig_different_model) compares the spatial and velocity structures of the adopted and different model parameters that can explain the observed moment 0 maps and PV diagrams.

The parameters of each streamer are listed in Table [2](#table:different model). The C$^{18}$O moment 0 maps are generated by integrating the emission over the velocity ranges of each streamer. With the parameters different from those adopted in Section [3.2](#subsec:streamers by ALMA), the model trajectories can also explain the observations.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
| NE | fiducial model | 73 | 60 | 100 | 90 | 64 | 4790 | 3.6–4.7 | 1.3$^{+1.4}_{-0.2}$$\times$10$^{-3}$ | 1.0$\times$10$^5$ | 1.3$^{+1.4}_{-0.2}$$\times$10$^{-8}$ |
|  | different model parameter | 107 | $-$45 | 55 | 70 | 73 | 16830 | 3.5–4.8 | 1.9$^{+1.8}_{-0.3}$$\times$10$^{-3}$ | 6.6$\times$10$^5$ | 2.8$^{+2.8}_{-0.4}$$\times$10$^{-9}$ |
| NW | fiducial model | 107 | $-$45 | 55 | 20 | $-$10 | 2830 | $-$0.1–4.9 | 2.2$^{+2.1}_{-0.4}$$\times$10$^{-3}$ | 4.5$\times$10$^4$ | 4.8$^{+4.7}_{-0.7}$$\times$10$^{-8}$ |
|  | different model parameter | 150 | 120 | 100 | 40 | 68 | 7520 | 3.1–4.8 | 2.0$^{+1.9}_{-0.3}$$\times$10$^{-3}$ | 2.0$\times$10$^5$ | 10$^{+10}_{-1.4}$$\times$10$^{-9}$ |
| NNW | fiducial model | 107 | $-$45 | 55 | 70 | $-$120 | 6130 | 5.2–6.8 | 4.0$^{+4.0}_{-0.6}$$\times$10$^{-3}$ | 1.4$\times$10$^5$ | 2.8$^{+2.7}_{-0.4}$$\times$10$^{-8}$ |
|  | different model parameter | 30 | $-$30 | 100 | 20 | 75 | 2590 | 5.2–6.7 | 4.6$^{+4.4}_{-0.7}$$\times$10$^{-3}$ | 4.0$\times$10$^4$ | 11$^{+12}_{-1.2}$$\times$10$^{-8}$ |

: Adopted parameters in the UCM model

# Channel maps of the 12-m array data

![image](./figures/ALMA_channelmap_robust2.0.png)\

Figure [11](#fig_channelmap_12only) shows the channel maps of the C$^{18}$O emission generated from the ALMA 12-m array data without the 7-m array data. The images are generated with the same procedure in Section [2.2](#datareduction:ALMA) but with the auto-masking parameters of the sidelobe threshold of 1.0, noise threshold of 3.5, low noise threshold of 0.5, minimum beam fraction of 0.3, and negative threshold of 7.0. Strong emission appears at the edge of the field-of-view after primary beam correction. This is particularly prominent in the low-velocity range of 4.69–5.52 km s$^{-1}$, and it is more significant than that in the 12-m and 7-m array combined maps (Figure [3](#fig_channelmap)). Thus, there is a caution of potential artifacts, when discussing streamer-like structures using the 12-m array only data.

Without the 7-m array data, the mean missing flux at the velocities of $V_\mathrm{LSR}$ $=$ 4.0–4.9 km s$^{-1}$, $V_\mathrm{sys}$, and $V_\mathrm{LSR}$ $=$ 5.2–6.0 km s$^{-1}$ are estimated to be 74$\%$, 97$\%$, and 87$\%$, respectively. Including the 7-m array data, the recoverable flux is only slightly improved compared to the 12-m array only data.

natexlab

(ref: 2018Andrews) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: 2008Antoniucci) Antoniucci, S., Nisini, B., Giannini, T., & Lorenzetti, D. 2008, A&A, 479, 503, doi: [`10.1051/0004-6361:20077468`](http://doi.org/10.1051/0004-6361:20077468)

(ref: 2015Aota) Aota, T., Inoue, T., & Aikawa, Y. 2015, ApJ, 799, 141, doi: [`10.1088/0004-637X/799/2/141`](http://doi.org/10.1088/0004-637X/799/2/141)

(ref: 2007Arce) Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 245, doi: [`10.48550/arXiv.astro-ph/0603071`](http://doi.org/10.48550/arXiv.astro-ph/0603071)

(ref: 2015Aso) Aso, Y., Ohashi, N., Saigo, K., et al. 2015, ApJ, 812, 27, doi: [`10.1088/0004-637X/812/1/27`](http://doi.org/10.1088/0004-637X/812/1/27)

(ref: 2023Aso) Aso, Y., Kwon, W., Ohashi, N., et al. 2023, ApJ, 954, 101, doi: [`10.3847/1538-4357/ace624`](http://doi.org/10.3847/1538-4357/ace624)

(ref: 2022Astropy) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 2014Bertrang) Bertrang, G., Wolf, S., & Das, H. S. 2014, A&A, 565, A94, doi: [`10.1051/0004-6361/201323091`](http://doi.org/10.1051/0004-6361/201323091)

(ref: 2024Cacciapuoti) Cacciapuoti, L., Macias, E., Gupta, A., et al. 2024, A&A, 682, A61, doi: [`10.1051/0004-6361/202347486`](http://doi.org/10.1051/0004-6361/202347486)

(ref: 2022CASATeam) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 1981Cassen) Cassen, P., & Moosman, A. 1981, Icarus, 48, 353, doi: [`10.1016/0019-1035(81)90051-8`](http://doi.org/10.1016/0019-1035(81)90051-8)

(ref: 1953Chandrasekhar) Chandrasekhar, S., & Fermi, E. 1953, ApJ, 118, 113, doi: [`10.1086/145731`](http://doi.org/10.1086/145731)

(ref: 2024Codella) Codella, C., Podio, L., De Simone, M., et al. 2024, MNRAS, 528, 7383, doi: [`10.1093/mnras/stae472`](http://doi.org/10.1093/mnras/stae472)

(ref: 2017Cotton) Cotton, W. D. 2017, PASP, 129, 094501, doi: [`10.1088/1538-3873/aa793f`](http://doi.org/10.1088/1538-3873/aa793f)

(ref: 2023Cuello) Cuello, N., Ménard, F., & Price, D. J. 2023, European Physical Journal Plus, 138, 11, doi: [`10.1140/epjp/s13360-022-03602-w`](http://doi.org/10.1140/epjp/s13360-022-03602-w)

(ref: 1951Davis) Davis, L. 1951, Physical Review, 81, 890, doi: [`10.1103/PhysRev.81.890.2`](http://doi.org/10.1103/PhysRev.81.890.2)

(ref: 2012Dullemond) Dullemond, C. P. 2012, Astrophysics Source Code Library, 1202.015. <http://adsabs.harvard.edu/abs/2012ascl.soft02015D>

(ref: 2019Dullemond) Dullemond, C. P., Küffmeier, M., Goicovic, F., et al. 2019, A&A, 628, A20, doi: [`10.1051/0004-6361/201832632`](http://doi.org/10.1051/0004-6361/201832632)

(ref: 2014Dunham) Dunham, M. M., Arce, H. G., Mardones, D., et al. 2014, ApJ, 783, 29, doi: [`10.1088/0004-637X/783/1/29`](http://doi.org/10.1088/0004-637X/783/1/29)

(ref: 2008Dunham) Dunham, M. M., Crapsi, A., Evans, Neal J., I., et al. 2008, ApJS, 179, 249, doi: [`10.1086/591085`](http://doi.org/10.1086/591085)

(ref: 2023Flores) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, ApJ, 958, 98, doi: [`10.3847/1538-4357/acf7c1`](http://doi.org/10.3847/1538-4357/acf7c1)

(ref: 1982Frerking) Frerking, M. A., Langer, W. D., & Wilson, R. W. 1982, ApJ, 262, 590, doi: [`10.1086/160451`](http://doi.org/10.1086/160451)

(ref: 2016Ginsburg) Ginsburg, A., Robitaille, T., & Beaumont, C. 2016, pvextractor: Position-Velocity Diagram Extractor, Astrophysics Source Code Library, record ascl:1608.010. [`http://ascl.net/1608.010`](http://ascl.net/1608.010)

(ref: 2022GOng) Gong, Y., Liu, S., Wang, J., et al. 2022, A&A, 663, A82, doi: [`10.1051/0004-6361/202142713`](http://doi.org/10.1051/0004-6361/202142713)

(ref: 1993Goodman) Goodman, A. A., Benson, P. J., Fuller, G. A., & Myers, P. C. 1993, ApJ, 406, 528, doi: [`10.1086/172465`](http://doi.org/10.1086/172465)

(ref: 2023Gupta) Gupta, A., Miotello, A., Manara, C. F., et al. 2023, A&A, 670, L8, doi: [`10.1051/0004-6361/202245254`](http://doi.org/10.1051/0004-6361/202245254)

(ref: 2023Han) Han, I., Kwon, W., Aso, Y., Bae, J., & Sheehan, P. 2023, ApJ, 956, 9, doi: [`10.3847/1538-4357/acf853`](http://doi.org/10.3847/1538-4357/acf853)

(ref: 2024Hanawa) Hanawa, T., Garufi, A., Podio, L., Codella, C., & Segura-Cox, D. 2024, MNRAS, 528, 6581, doi: [`10.1093/mnras/stae338`](http://doi.org/10.1093/mnras/stae338)

(ref: 2012Hatchell) Hatchell, J., Terebey, S., Huard, T., et al. 2012, ApJ, 754, 104, doi: [`10.1088/0004-637X/754/2/104`](http://doi.org/10.1088/0004-637X/754/2/104)

(ref: 2001Heitsch) Heitsch, F., Zweibel, E. G., Mac Low, M.-M., Li, P., & Norman, M. L. 2001, ApJ, 561, 800, doi: [`10.1086/323489`](http://doi.org/10.1086/323489)

(ref: 2023Hsieh) Hsieh, T. H., Segura-Cox, D. M., Pineda, J. E., et al. 2023, A&A, 669, A137, doi: [`10.1051/0004-6361/202244183`](http://doi.org/10.1051/0004-6361/202244183)

(ref: 2021Huang) Huang, J., Bergin, E. A., Öberg, K. I., et al. 2021, ApJS, 257, 19, doi: [`10.3847/1538-4365/ac143e`](http://doi.org/10.3847/1538-4365/ac143e)

(ref: 1999Huard) Huard, T. L., Sandell, G., & Weintraub, D. A. 1999, ApJ, 526, 833, doi: [`10.1086/308022`](http://doi.org/10.1086/308022)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 2022Imai) Imai, M., Oya, Y., Svoboda, B., et al. 2022, ApJ, 934, 70, doi: [`10.3847/1538-4357/ac77e7`](http://doi.org/10.3847/1538-4357/ac77e7)

(ref: 2008Kauffmann) Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., I., & Lee, C. W. 2008, A&A, 487, 993, doi: [`10.1051/0004-6361:200809481`](http://doi.org/10.1051/0004-6361:200809481)

(ref: 2023Kido) Kido, M., Takakuwa, S., Saigo, K., et al. 2023, ApJ, 953, 190, doi: [`10.3847/1538-4357/acdd7a`](http://doi.org/10.3847/1538-4357/acdd7a)

(ref: 2017Kuffmeier) Kuffmeier, M., Haugbølle, T., & Nordlund, Å. 2017, ApJ, 846, 7, doi: [`10.3847/1538-4357/aa7c64`](http://doi.org/10.3847/1538-4357/aa7c64)

(ref: 2023Kuffmeier) Kuffmeier, M., Jensen, S. S., & Haugbølle, T. 2023, European Physical Journal Plus, 138, 272, doi: [`10.1140/epjp/s13360-023-03880-y`](http://doi.org/10.1140/epjp/s13360-023-03880-y)

(ref: 2019Lam) Lam, K. H., Li, Z.-Y., Chen, C.-Y., Tomida, K., & Zhao, B. 2019, MNRAS, 489, 5326, doi: [`10.1093/mnras/stz2436`](http://doi.org/10.1093/mnras/stz2436)

(ref: 1969Larson) Larson, R. B. 1969, MNRAS, 145, 271, doi: [`10.1093/mnras/145.3.271`](http://doi.org/10.1093/mnras/145.3.271)

(ref: 2010Launhardt) Launhardt, R., Nutter, D., Ward-Thompson, D., et al. 2010, ApJS, 188, 139, doi: [`10.1088/0067-0049/188/1/139`](http://doi.org/10.1088/0067-0049/188/1/139)

(ref: 2013Launhardt) Launhardt, R., Stutz, A. M., Schmiedeke, A., et al. 2013, A&A, 551, A98, doi: [`10.1051/0004-6361/201220477`](http://doi.org/10.1051/0004-6361/201220477)

(ref: 2024Lebreuilly) Lebreuilly, U., Hennebelle, P., Colman, T., et al. 2024, A&A, 682, A30, doi: [`10.1051/0004-6361/202346558`](http://doi.org/10.1051/0004-6361/202346558)

(ref: 2023Lee) Lee, J.-E., Matsumoto, T., Kim, H.-J., et al. 2023, ApJ, 953, 82, doi: [`10.3847/1538-4357/acdd5b`](http://doi.org/10.3847/1538-4357/acdd5b)

(ref: 2024Lee) Lee, J.-E., Kim, C.-H., Lee, S., et al. 2024, ApJ, 966, 119, doi: [`10.3847/1538-4357/ad3106`](http://doi.org/10.3847/1538-4357/ad3106)

(ref: 2015Lesur) Lesur, G., Hennebelle, P., & Fromang, S. 2015, A&A, 582, L9, doi: [`10.1051/0004-6361/201526734`](http://doi.org/10.1051/0004-6361/201526734)

(ref: 2024Lin) Lin, S.-J., Yen, H.-W., & Lai, S.-P. 2024, AJ, 168, 107, doi: [`10.3847/1538-3881/ad5add`](http://doi.org/10.3847/1538-3881/ad5add)

(ref: 2024Lopez-Vazquez) López-Vázquez, J. A., Lee, C.-F., Shang, H., et al. 2024, arXiv e-prints, arXiv:2411.01728, doi: [`10.48550/arXiv.2411.01728`](http://doi.org/10.48550/arXiv.2411.01728)

(ref: Mcmullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: 2022Mercimek) Mercimek, S., Codella, C., Podio, L., et al. 2022, A&A, 659, A67, doi: [`10.1051/0004-6361/202141790`](http://doi.org/10.1051/0004-6361/202141790)

(ref: 2017Miura) Miura, H., Yamamoto, T., Nomura, H., et al. 2017, ApJ, 839, 47, doi: [`10.3847/1538-4357/aa67df`](http://doi.org/10.3847/1538-4357/aa67df)

(ref: 1998Momose) Momose, M., Ohashi, N., Kawabe, R., Nakano, T., & Hayashi, M. 1998, ApJ, 504, 314, doi: [`10.1086/306061`](http://doi.org/10.1086/306061)

(ref: 2022Murillo) Murillo, N. M., van Dishoeck, E. F., Hacar, A., Harsono, D., & Jørgensen, J. K. 2022, A&A, 658, A53, doi: [`10.1051/0004-6361/202141250`](http://doi.org/10.1051/0004-6361/202141250)

(ref: 2024Nakamura) Nakamura, F., Nguyen-Luong, Q., Ishihara, K., & Yoshino, A. 2024, arXiv e-prints, arXiv:2409.02661, doi: [`10.48550/arXiv.2409.02661`](http://doi.org/10.48550/arXiv.2409.02661)

(ref: 1978Nakano) Nakano, T., & Nakamura, T. 1978, PASJ, 30, 671

(ref: 1997Ohashi) Ohashi, N., Hayashi, M., Ho, P. T. P., et al. 1997, ApJ, 488, 317, doi: [`10.1086/304685`](http://doi.org/10.1086/304685)

(ref: 2023Ohashi) Ohashi, N., Tobin, J. J., J$\o$rgensen, J. J., & eDisk Team. 2023, ApJ, in press

(ref: 2014Ohashi) Ohashi, N., Saigo, K., Aso, Y., et al. 2014, ApJ, 796, 131, doi: [`10.1088/0004-637X/796/2/131`](http://doi.org/10.1088/0004-637X/796/2/131)

(ref: 2022Okoda) Okoda, Y., Oya, Y., Imai, M., et al. 2022, ApJ, 935, 136, doi: [`10.3847/1538-4357/ac7ff4`](http://doi.org/10.3847/1538-4357/ac7ff4)

(ref: 2001Ostriker) Ostriker, E. C., Stone, J. M., & Gammie, C. F. 2001, ApJ, 546, 980, doi: [`10.1086/318290`](http://doi.org/10.1086/318290)

(ref: 2016Oya) Oya, Y., Sakai, N., López-Sepulcre, A., et al. 2016, ApJ, 824, 88, doi: [`10.3847/0004-637X/824/2/88`](http://doi.org/10.3847/0004-637X/824/2/88)

(ref: 2021Pineda) Pineda, J. E., Schmiedeke, A., Caselli, P., et al. 2021, ApJ, 912, 7, doi: [`10.3847/1538-4357/abebdd`](http://doi.org/10.3847/1538-4357/abebdd)

(ref: 2020Pineda) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158, doi: [`10.1038/s41550-020-1150-z`](http://doi.org/10.1038/s41550-020-1150-z)

(ref: 2023Pineda) Pineda, J. E., Arzoumanian, D., Andre, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 233, doi: [`10.48550/arXiv.2205.03935`](http://doi.org/10.48550/arXiv.2205.03935)

(ref: 2023Plunkett) Plunkett, A., Hacar, A., Moser-Fischer, L., et al. 2023, PASP, 135, 034501, doi: [`10.1088/1538-3873/acb9bd`](http://doi.org/10.1088/1538-3873/acb9bd)

(ref: 2020Sai) Sai, J., Ohashi, N., Saigo, K., et al. 2020, ApJ, 893, 51, doi: [`10.3847/1538-4357/ab8065`](http://doi.org/10.3847/1538-4357/ab8065)

(ref: 2014Sakaib) Sakai, N., Oya, Y., Sakai, T., et al. 2014, ApJL, 791, L38, doi: [`10.1088/2041-8205/791/2/L38`](http://doi.org/10.1088/2041-8205/791/2/L38)

(ref: 2015Seifried) Seifried, D., Banerjee, R., Pudritz, R. E., & Klessen, R. S. 2015, MNRAS, 446, 2776, doi: [`10.1093/mnras/stu2282`](http://doi.org/10.1093/mnras/stu2282)

(ref: 2003Semenov) Semenov, D., Henning, T., Helling, C., Ilgner, M., & Sedlmayr, E. 2003, A&A, 410, 611, doi: [`10.1051/0004-6361:20031279`](http://doi.org/10.1051/0004-6361:20031279)

(ref: 1977Shu) Shu, F. H. 1977, ApJ, 214, 488, doi: [`10.1086/155274`](http://doi.org/10.1086/155274)

(ref: 2021Skalidis) Skalidis, R., Sternberg, J., Beattie, J. R., Pavlidou, V., & Tassis, K. 2021, A&A, 656, A118, doi: [`10.1051/0004-6361/202142045`](http://doi.org/10.1051/0004-6361/202142045)

(ref: 2024Smallwood) Smallwood, J. L., Nealon, R., Cuello, N., Dong, R., & Booth, R. A. 2024, MNRAS, 527, 2094, doi: [`10.1093/mnras/stad3057`](http://doi.org/10.1093/mnras/stad3057)

(ref: 2023Smallwood) Smallwood, J. L., Yang, C.-C., Zhu, Z., et al. 2023, MNRAS, 521, 3500, doi: [`10.1093/mnras/stad742`](http://doi.org/10.1093/mnras/stad742)

(ref: 1988Stahler) Stahler, S. W. 1988, ApJ, 332, 804, doi: [`10.1086/166694`](http://doi.org/10.1086/166694)

(ref: 2000Tachihara) Tachihara, K., Mizuno, A., & Fukui, Y. 2000, ApJ, 528, 817, doi: [`10.1086/308189`](http://doi.org/10.1086/308189)

(ref: 2013Takakuwa) Takakuwa, S., Saito, M., Lim, J., & Saigo, K. 2013, ApJ, 776, 51, doi: [`10.1088/0004-637X/776/1/51`](http://doi.org/10.1088/0004-637X/776/1/51)

(ref: 2018Takakuwa) Takakuwa, S., Tsukamoto, Y., Saigo, K., & Saito, M. 2018, ApJ, 865, 51, doi: [`10.3847/1538-4357/aadb93`](http://doi.org/10.3847/1538-4357/aadb93)

(ref: 2024Takakuwa) Takakuwa, S., Saigo, K., Kido, M., et al. 2024, ApJ, 964, 24, doi: [`10.3847/1538-4357/ad1f57`](http://doi.org/10.3847/1538-4357/ad1f57)

(ref: 2024Taniguchi) Taniguchi, K., Pineda, J. E., Caselli, P., et al. 2024, ApJ, 965, 162, doi: [`10.3847/1538-4357/ad2fa1`](http://doi.org/10.3847/1538-4357/ad2fa1)

(ref: 1984Terebey) Terebey, S., Shu, F. H., & Cassen, P. 1984, ApJ, 286, 529, doi: [`10.1086/162628`](http://doi.org/10.1086/162628)

(ref: 2022Thieme) Thieme, T. J., Lai, S.-P., Lin, S.-J., et al. 2022, ApJ, 925, 32, doi: [`10.3847/1538-4357/ac382b`](http://doi.org/10.3847/1538-4357/ac382b)

(ref: 2012Tobin) Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2012, Nature, 492, 83, doi: [`10.1038/nature11610`](http://doi.org/10.1038/nature11610)

(ref: 2024Tobin) Tobin, J. J., & Sheehan, P. D. 2024, arXiv e-prints, arXiv:2403.15550, doi: [`10.48550/arXiv.2403.15550`](http://doi.org/10.48550/arXiv.2403.15550)

(ref: 2014Tokuda) Tokuda, K., Onishi, T., Saigo, K., et al. 2014, ApJL, 789, L4, doi: [`10.1088/2041-8205/789/1/L4`](http://doi.org/10.1088/2041-8205/789/1/L4)

(ref: 2023Tu) Tu, Y., Li, Z.-Y., Lam, K. H., Tomida, K., & Hsu, C.-Y. 2023, arXiv e-prints, arXiv:2307.16774, doi: [`10.48550/arXiv.2307.16774`](http://doi.org/10.48550/arXiv.2307.16774)

(ref: 1976Ulrich) Ulrich, R. K. 1976, ApJ, 210, 377, doi: [`10.1086/154840`](http://doi.org/10.1086/154840)

(ref: 2022Valdivia) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2022, A&A, 667, A12, doi: [`10.1051/0004-6361/202243310`](http://doi.org/10.1051/0004-6361/202243310)

(ref: 2000Vallee) Vallée, J. P., Bastien, P., & Greaves, J. S. 2000, ApJ, 542, 352, doi: [`10.1086/309531`](http://doi.org/10.1086/309531)

(ref: 2007Vallee) Vallée, J. P., & Fiege, J. D. 2007, AJ, 134, 628, doi: [`10.1086/519163`](http://doi.org/10.1086/519163)

(ref: 2003Vallee) Vallée, J. P., Greaves, J. S., & Fiege, J. D. 2003, ApJ, 588, 910, doi: [`10.1086/374309`](http://doi.org/10.1086/374309)

(ref: 2021vanGelder) van Gelder, M. L., Tabone, B., van Dishoeck, E. F., & Godard, B. 2021, A&A, 653, A159, doi: [`10.1051/0004-6361/202141591`](http://doi.org/10.1051/0004-6361/202141591)

(ref: 2023van’tHoff) van’t Hoff, M. L. R., Tobin, J. J., Li, Z.-Y., et al. 2023, ApJ, 951, 10, doi: [`10.3847/1538-4357/accf87`](http://doi.org/10.3847/1538-4357/accf87)

(ref: 1995Wang) Wang, Y., Evans, Neal J., I., Zhou, S., & Clemens, D. P. 1995, ApJ, 454, 217, doi: [`10.1086/176478`](http://doi.org/10.1086/176478)

(ref: 1996Wu) Wu, Y., Huang, M., & He, J. 1996, A&AS, 115, 283

(ref: 2023Yamato) Yamato, Y., Aikawa, Y., Ohashi, N., et al. 2023, ApJ, 951, 11, doi: [`10.3847/1538-4357/accd71`](http://doi.org/10.3847/1538-4357/accd71)

(ref: 2024Yano) Yano, Y., Nakamura, F., & Kinoshita, S. W. 2024, ApJ, 964, 119, doi: [`10.3847/1538-4357/ad2a54`](http://doi.org/10.3847/1538-4357/ad2a54)

(ref: 2019Yen) Yen, H.-W., Gu, P.-G., Hirano, N., et al. 2019, ApJ, 880, 69, doi: [`10.3847/1538-4357/ab29f8`](http://doi.org/10.3847/1538-4357/ab29f8)

(ref: 2017Yen) Yen, H.-W., Koch, P. M., Takakuwa, S., et al. 2017, ApJ, 834, 178, doi: [`10.3847/1538-4357/834/2/178`](http://doi.org/10.3847/1538-4357/834/2/178)

(ref: 2014Yen) Yen, H.-W., Takakuwa, S., Ohashi, N., et al. 2014, ApJ, 793, 1, doi: [`10.1088/0004-637X/793/1/1`](http://doi.org/10.1088/0004-637X/793/1/1)

(ref: 2024Yen) Yen, H.-W., Williams, J. P., Sai, J., et al. 2024, ApJ, 969, 125, doi: [`10.3847/1538-4357/ad4c6b`](http://doi.org/10.3847/1538-4357/ad4c6b)

(ref: 2020Zucker) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2020, A&A, 633, A51, doi: [`10.1051/0004-6361/201936145`](http://doi.org/10.1051/0004-6361/201936145)

</paper>

Write the methods card for this paper.