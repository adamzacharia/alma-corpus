# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...700A.277C\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...700A.277C",
 "title": "Dust emission from the bulk of galaxies in the Epoch of Reionisation",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Ciesla, L.",
 "n_authors": 9,
 "arxiv_id": "2412.02557",
 "doi": "10.1051/0004-6361/202453278",
 "alma_projects_linked_by_archive": [
  "2012.1.00173.S",
  "2012.1.00775.S",
  "2012.1.00869.S",
  "2012.1.00983.S",
  "2013.1.00718.S",
  "2013.1.00884.S",
  "2013.1.01271.S",
  "2013.1.01292.S",
  "2015.1.00039.S",
  "2015.1.00098.S",
  "2015.1.00543.S",
  "2015.1.00821.S",
  "2015.1.00870.S",
  "2015.1.01096.S",
  "2015.1.01379.S",
  "2015.1.01447.S",
  "2015.A.00009.S",
  "2016.1.00324.L",
  "2016.1.00721.S",
  "2016.1.01240.S",
  "2017.1.00190.S",
  "2017.1.00428.L",
  "2017.1.00755.S",
  "2017.1.01027.S",
  "2018.1.00164.S",
  "2018.1.00567.S",
  "2018.1.01044.S",
  "2019.1.01528.S"
 ]
}
```

Paper text:
<paper>
# Dust emission from the bulk of galaxies at the Epoch of Reionization

The excess of UV bright galaxies observed at $z>10$ has been one of the major surprises from the JWST early observations. Several explanations have been proposed to understand the mild change in space density of the UV bright galaxies at these high redshifts, among them an evolution of dust attenuation properties in galaxies. However, our view of dust in primordial galaxies is limited towards a few tens of $z\sim7$ galaxies, pre-selected from UV-optical observations, and are thus not necessarily representative of the bulk of the sources at these redshifts. In this work, we aim at constraining the dust properties of galaxies at $6<z<12$ by making the most of the A$^3$COSMOS database in the JADES/GOODS-South field. We stacked ALMA band 6 and 7 observations of 4464 JADES galaxies covered by the A$^3$COSMOS database and used the measurements as constraints to perform UV-to-FIR SED modelling. We obtain tentative signals for the brightest UV galaxies ($M_{\mathrm{UV}}<-19$ mag) as well as for the most massive ones ($\log M_\star/M_\odot>9$) at $6<z<7$, and upper limits for fainter ($M_{\mathrm{UV}}>-19$ mag), lower mass sources ($\log M_\star/M_\odot<9$), and at higher redshift ($z>7$). Fitting these $6<z<7$ galaxies with ALMA constraints results in lower star formation rates ($-0.4$ dex) and FUV attenuation ($-0.5$ mag) for galaxies with $\log M_\star/M_\odot>8$, compared to the fit without FIR. We extend the $L_{\mathrm{IR}}$ vs $M_{\mathrm{UV}}$ relation down to $M_{\mathrm{UV}}=-19$ mag and show a tentative breakdown of the relation at fainter UV magnitudes. The positions of the JADES $z\sim6.5$ sample on the infrared excess (IRX) versus $\beta$ and IRX versus $M_\star$ diagrams are consistent with those of the ALPINE ($z\sim5.5$) and REBELS ($z\sim6.5$) samples, suggesting that the dust composition and content of our mass-selected sample are similar to these UV-selected galaxies. Extending our analysis of the infrared properties to $z>7$ galaxies, we find a non-evolution of $\beta$ in the $M_{\mathrm{UV}}$ range probed by our sample (-17.24$^{+0.54}_{-0.62}$) and highlight the fact that samples from the literature are not representative of the bulk of galaxy populations at $z>6$. We confirm a linear relation between A$_{\rm V}$ and sSFR$^{-1}$ with a flatter slope than previously reported due to the use of ALMA constraints. Our results suggest that rapid and significant dust production has already happened by $z\sim7$.

# Introduction

In the interstellar medium (ISM) of galaxies, dust plays a crucial role, catalysing the transformation of atomic hydrogen into molecular hydrogen, the raw material for star formation (cite: Wolfire95). Dust also enables gas to cool and condense into new stars by absorbing ultraviolet (UV) radiation from nearby young stars (cite: Draine78; Dwek86; Hollenbach&Tielens97). This absorbed energy is then re-emitted in the infrared (IR) range, where dust grain thermal emission dominates the spectral energy distribution (SED) of galaxies, covering wavelengths from approximately 8 to 1000 $\mu$m. Because of its important role in the ISM and its tight link with the other components of galaxies, the study of dust emission is paramount for a better understanding of all of the processes at play, especially galaxies’ star formation activity.

At $z>4$, most of the constraints on star formation in galaxies are obtained via UV emission which is highly sensitive to dust attenuation and needs to be corrected to obtain a complete view (cite: Calzetti00; SalimNarayanan20). Understanding how dust attenuation varies with redshift and other galaxy properties is thus essential for accurately determining star formation rates (SFRs), and thereby constructing a precise account of galaxy evolution throughout cosmic history. At $z>4$, two programs targeted UV-selected galaxies to be observed with the Atacama Large Millimeter/Submillimeter Array (ALMA). ALPINE (cite: LeFevre20; Bethermin20; Faisst20) provided 23 far-infrared continuum-detected galaxies at $z\sim5$. At slightly higher redshift, the REBELS survey (cite: Bouwens22) provided dust continuum ALMA observations of 40 UV-selected bright galaxies at $6.5<z<7.7$. At $z>7$, a few galaxies have been detected in dust emission (cite: Watson15; Laporte17; Laporte19; Bowler18; Tamura19; Bakx20; Sugahara21; Endsley22; Witstok22; Schouws22; Algera23; Schouws24) providing hints that significant dust reservoirs are already in place at early times. Although they provide an indispensable and detailed view on dust emission at $z\gtrsim4$, these UV-selected samples are limited in terms of statistics and might only represent the tip of the infrared luminosity distribution at these redshifts. To overcome this, with a different approach, (cite: Magnelli24) used the A$^3$COSMOS ALMA database (cite: Liu19; Adscheid24) gathering the wealth of ALMA archival observations to statistically probe dust properties of a mass selected sample at $4<z<5$.

The infrared excess (IRX$\equiv L_{\mathrm{IR}}/L_{\mathrm{UV}}$) vs $\beta$ relation is widely used as a dust attenuation diagnostic (cite: Calzetti94; Meurer99; Calzetti00). While this relation provides accurate estimates of the attenuation for local starburst galaxies (cite: Meurer99), the position of normal star-forming galaxies relative to it is still debated (cite: Capak15; Barisic17; Hashimoto19; Bakx20; Bowler22; Schouws22; Boquien22; Magnelli24; Bowler24). The position of galaxies with respect to the IRX-$\beta$ relation depends on the geometry of dust and stars in the galaxy (cite: Popping17; Narayanan18; Ferrara22; Pallottini22; Vijayan22) and the effect of the star formation history (SFH) is also expected since the UV $\beta$ slope is a combination of dust attenuation and the intrinsic UV slope, $\beta_0$ (cite: Boquien12). (cite: Magnelli24) used averaged measurements of ALMA galaxies using A$^3$COSMOS to investigate the dust attenuation properties of star-forming galaxies at $4<z<5$. They find that the average properties of their sample are compatible with the relations of (cite: Meurer99) and (cite: Calzetti00) for local starbursts. Similar conclusions were reached by (cite: Bowler24) on stacked properties of the REBELS galaxies at z$\sim$7. Both results point towards non-evolving grain properties (e.g., size distribution, composition). However, using the ALPINE sample of galaxies at $4.4<z<5.5$, (cite: Boquien22) found a wider variety of attenuation curves among these sources from relations steeper than the Small Magellanic Cloud (SMC) extinction curve to relations shallower than for local starbursts. In their fitting process, the slope of the attenuation curve, $\delta$, was let free which could explain the larger variety of curves that they find.

The relation between IRX and the stellar mass is another diagnostic of the dust attenuation properties, with the IRX quantifying the dust obscured fraction while the stellar mass is a proxy of the past star formation activity, hence of dust production. Recently, there have been claims of a steepening of the relation between IRX and stellar mass with increasing redshifts (cite: Fudamoto20; Magnelli24), that is a decreasing obscured fraction with redshifts. This would imply an evolution of dust geometry relative to new-formed stars. Using the REBELS sample of galaxies at $z\sim 7$, (cite: Bowler24) also found a decrease in the obscured fraction with redshifts but associated with a IRX-stellar mass relation with a relatively flat slope, in contradiction with the results of (cite: Fudamoto20) and (cite: Magnelli24), thus adding to the debate.

The goal of this work is to extend these studies in terms of statistics but also redshift with a statistical analysis using the A$^3$COSMOS (A$^3$GOODSS) archival data, pushing it to its limits by stacking galaxies at $z=6$ and beyond, observed as part of the JADES survey (cite: Rieke23). Indeed, dust at higher redshift ($z\gtrsim9-10$) is also central in the discussion to understand the origin of the excess of UV bright galaxies observed at $z>10$ (cite: Castellano22; Naidu22; Donnan23; Harikane23; Arrabal23; CurtisLake23; Robertson23; Harikane23b; RobertsBorsani24). The evolution of attenuation properties is mentioned as a possible explanation to the abundance of such “blue monsters” (cite: Ferrara23). Constraints on the infrared emission of early galaxies could provide benchmark properties for these studies.

The paper is organised as follows: in Sect. [\[sample\]](#sample) we describe the JADES sample used as prior for the ALMA stacking and in Sect. [\[sec:sedfit\]](#sec:sedfit) the SED fitting procedure to obtain the UV magnitudes and stellar mass from which we bin them. The ALMA stacking of the sources using A$^3$COSMOS is detailed in Sect. [\[stack\]](#stack). We compare the properties of the galaxies with and without using the ALMA constraint in the SED modelling in Sect. [\[impact\]](#impact) and study the dust properties of the sample in Sect. [\[dust_results\]](#dust_results). Constraints on galaxies at $z>7$ are provided in Sect. [\[highz\]](#highz). Throughout the paper, we use a (cite: Salpeter55) initial mass function and WMAP7 cosmology (cite: Komatsu11).

# The sample

## Sample selection

We use the second release of the JWST Advanced Deep Extragalactic Survey (cite: Rieke23; Bunker23; Eisenstein23; Hainline23) of the Hubble Ultra Deep Field covering 68 sq.arcmin presented in (cite: Eisenstein23b). Although the main part of the study focuses on galaxies with $6<z<7$, we select galaxies with $6<z<12$ in the JADES catalogue. We refer to (cite: Rieke23), (cite: Eisenstein23b), and (cite: Robertson24) for more details on the data reduction process, photometry procedures, and redshift estimates. This catalogue combines nine broad and five medium JWST/NIRCam bands from the JADES and JEMS (cite: Williams23) surveys, respectively, and existing HST imaging, for a total of 23 photometric bands. The reddest NIRCam filter, where the galaxies were selected (F444W), allows us to probe the 0.63 $\mu$m and 0.34 $\mu$m rest frame at $z=6$ and $z=12$, respectively.

In this work we use the photometry catalogue made from KRON apertures. In the broad NIRCam bands, the 5$\sigma$ flux depths are between 1.9 and 3.0 nJy, while they range from 1.6 to 3.3 nJy in the medium bands. Photometric redshifts available in the JADES catalogue are computed with the code `EAZY` (cite: Brammer08). The average offset between photometric redshifts and a compilation of spectroscopic redshifts is 0.05 with a $\Delta z/(1+z)$ of 0.024. We use spectroscopic redshifts when available although it concerns only 0.6$\%$ of the sample at $6<z<7$, and 0% at $z>7$. We also checked for spectroscopic data through the Dawn JWST Archive[^2] and find 37 NIRSpec spectra. Out of these, 9 of them are galaxies with $z_{spec}<5.5$, we exclude them from our analysis.

As in (cite: Ciesla24), we impose each galaxy to be detected with a signal-to-noise (S/N) higher 3 in at least 3 JWST filters. This criterion results in a subsample of 8810 galaxies with redshifts between 6 and 12, 6000 of them between 6 and 7. Given the uncertainty on photometric redshift, several studies impose a criterion on the quality of the photometric redshift, based on its PDF (cite: Cole23; Finkelstein23). However, in the following, we consider the full galaxy sample. Indeed after redoing the analysis of this work imposing the same photo-$z$ quality criteria as (cite: Cole23), we find no strong impact on our results, a conclusion also reached by (cite: Cole23).

A particular focus on the $6<z<7$ bin is made in the paper, driven by the tentative signal obtained from stacking the ALMA observations that is more constraining at $6<z<7$ than at higher redshifts. We extend our analysis at higher redshifts in Sect. [\[highz\]](#highz).

## SED modelling with `CIGALE` and physical properties

We use the SED modelling code `CIGALE`[^3] (cite: Boquien19) on the HST+JWST set of data, probing the UV to NIR restframe wavelength range. The fitting set up of `CIGALE` is the same than the one tested and used in (cite: Ciesla24) which adopts a non-parametric star formation history (SFH) specifically tailored for early galaxies. The non-parametric approach usually assumes a prior to handle the relation between two consecutive SFR bins of the SFH (continuity, bursty continuity, etc.). In this work, we use the non-parametric SFH from (cite: Ciesla24) who used no prior and showed that it provides more flexibility to model the bursty SFH expected in early galaxies. We note that this SFH library results in a wide range of $\beta_0$, the intrinsic UV slope, ranging from -2.78 to 2.65 with a median value of -2.20. We use the stellar population models of (cite: BruzualCharlot03), and a (cite: Calzetti00) dust attenuation law which is found to be suitable for galaxies at $z>6$ (cite: Bowler22; Markov24).

`CIGALE` assumes energy balance: the energy absorbed in the UV-optical is re-emitted in the IR. Some studies have shown a spatial offset between the stellar (UV) and dust (IR) emission in some high redshift sub-millimetre galaxies (cite: Hodge16; Elbaz18) resulting in discussions on the validity of UV-to-IR SED modelling based on energy balance. Using the disturbed morphology of M 82 as a test-bed, (cite: Seille22) showed that the estimates of the star formation rate and stellar mass for the whole galaxy are found to be consistent with the sum of the same parameters obtained for individual regions. The same conclusion is reached by (cite: Li24) at $4<z<6$ from a resolved analysis of ALMA-CRISTAL galaxies therefore suggesting that there is no bias due to outshining by young stars on the derived global properties of these sources. Furthermore, using FIRE zoom-in simulations of dusty and high-redshift galaxies, (cite: Haskell23) demonstrated that when the quality of the fit is acceptable, the fidelity of SED modelling estimates using energy balance is independent from the degree of UV/FIR offset, with similar quality than previously reported for local galaxies. Therefore, we are confident in using the ALMA constraint and perform the SED modelling from UV to FIR using energy balance.

To model the IR emission, we use the dust library of (cite: Schreiber18) that has two free parameters. One the fraction of dust mass locked in the form of Polycyclic Aromatic Hydrocarbons (PAH), which can vary from 0 to 100%. The second is the dust temperature, varying from 15 to 60 K. The data used in this work does not allow to constrain the PAH fraction. Therefore we choose to fix this input parameter to 3% which corresponds to the estimate of (cite: Schreiber18) at $z\sim3$, the highest redshift constraint provided in their study. Regarding dust temperature, following the results of (cite: Sommovigo22) from REBELS galaxies, we set it to 47 K and test in Sect. [\[tdust\]](#tdust) the impact of this dust temperature assumption on our results.

+----------------+--------------------------+---------------------------------------------------+
| **Parameter**  | **Value**                | **Definition**                                    |
+:===============+:========================:+:==================================================+
| **Non-parametric SFH –**                                                                      |
+----------------+--------------------------+---------------------------------------------------+
| $age$ (Myr)    | 200, 300, 500, 750       | maximum possible age                              |
+----------------+--------------------------+---------------------------------------------------+
| sfr$\_$max     | 500 M$_{\odot}$yr$^{-1}$ | max. value of the SFR                             |
+----------------+--------------------------+---------------------------------------------------+
| $N_{\rm bins}$ | 10                       | \# of time bins of the SFH                        |
+----------------+--------------------------+---------------------------------------------------+
| $N_{\rm SFH}$  | 500                      | \# of SFH per $age$ value                         |
+----------------+--------------------------+---------------------------------------------------+
| Last bin size  | 10 Myr                   |                                                   |
+----------------+--------------------------+---------------------------------------------------+
| **Stellar population –**                                                                      |
+----------------+--------------------------+---------------------------------------------------+
| metallicity    | 0.004, 0.02              |                                                   |
+----------------+--------------------------+---------------------------------------------------+
| **Emission lines –**                                                                          |
+----------------+--------------------------+---------------------------------------------------+
| $\log$U        | -3, -2                   | ionisation parameter                              |
+----------------+--------------------------+---------------------------------------------------+
| $f_{\rm esc}$  | 0, 0.1                   | Lyman continuum photons escape fraction           |
+----------------+--------------------------+---------------------------------------------------+
| $f_{\rm dust}$ | 0, 0.1                   | Lyman continuum photons fraction absorbed by dust |
+----------------+--------------------------+---------------------------------------------------+
| **Dust attenuation –**                                                                        |
+----------------+--------------------------+---------------------------------------------------+
| E(B-V) lines   | $\big[$0; 0.5$\big]$     | 8 values linearly sampled                         |
+----------------+--------------------------+---------------------------------------------------+
| E(B-V)s factor | 0.5                      | colour excess ratio between continuum & nebular   |
+----------------+--------------------------+---------------------------------------------------+
| **Dust emission –**                                                                           |
+----------------+--------------------------+---------------------------------------------------+
| $f_{\rm PAH}$  | 3%                       | fraction of PAH                                   |
+----------------+--------------------------+---------------------------------------------------+
| $T_{\rm dust}$ | 47 K                     | dust temperature                                  |
+----------------+--------------------------+---------------------------------------------------+
|                |                          |                                                   |
+----------------+--------------------------+---------------------------------------------------+

To estimate the physical properties, the models are fitted to the observations and the likelihoods are computed from the $\chi^2$. The galaxy properties are taken as the likelihood-weighted means and the uncertainties are the likelihood-weighted standard deviations. One important aspect to note is that upper limits are taken into account in the fitting procedure (cite: Boquien19). In this work, we take 3$\sigma$ observational uncertainties as the upper limits.

The parameters used for the fit are provided in Table [\[inputparam\]](#inputparam). In their analysis, (cite: Ciesla24) showed that the physical properties, such as stellar mass and SFR, of galaxies with $6<z<12$ are well constrained with the HST+JWST set of filters of the JADES survey. As we are using the same combination of filters, we rely on their results. We first apply this `CIGALE` setup on the JADES sample using only HST and JWST observations. The resulting normalised distributions of UV magnitude, stellar mass, SFR, and UV slope ($\beta$) are shown in Fig. [1](#fig:stats_noir) for the $6<z<7$ galaxies. Our sample allows us to probe relatively faint UV magnitude (-17.11$^{0.55}_{0.63}$ mag), a median stellar mass of $\log M_\star/M_\odot=7.82^{0.27}_{0.22}$, median SFR of $\log SFR/M_\odot.yr^{-1}=-0.05^{0.30}_{0.21}$, and relatively blue UV $\beta$ slopes (-2.24$^{0.18}_{0.14}$). The sample that we use for the ALMA stacking is built from this HST+JWST `CIGALE` run. We select galaxies with a reduced $\chi^2$ no larger than 4, removing 26 galaxies among which many sources with SEDs that are similar to brown dwarves’ SEDs. The second run of CIGALE using the ALMA constraints is presented in Sect. [\[impact\]](#impact).

![](stats_noir.pdf)

# ALMA stacking of JADES galaxies

We used the A$^3$GOODSS ALMA archival database, part of the A$^3$COSMOS database (cite: Liu19; Adscheid24), to perform a stacking analysis on our galaxy sample, choosing ALMA images from bands 6 ($\sim$243 GHz) and 7 ($\sim$324 GHz). Out of the 5974 galaxies in our $6<z<7$ sample, 4464 are covered by one or multiple ALMA pointings (i.e., within an area of a primary beam attenuation $>0.5$). Regarding astrometry, the most critical optical versus ALMA astrometric errors are $<$0.2$''$ (cite: Franco18). JWST astrometry are tied to Gaia and should therefore be better. As the ALMA observations we are using have PSF FWHM greater than 0.2$''$, we do not consider astrometry as a possible issue. This reduces our sample to 4464 galaxies, with redshift, stellar mass, UV luminosity, and UV spectral slope distributions that are indistinguishable (Kolmogorov-Smirnov test) from those of their parent sample of 5974 galaxies.

Because of this large number of galaxies, it was impractical to stack them in the $uv$-domain in order to deal with the heterogeneity in angular resolution (ranging from $\sim$0.1$\ensuremath{''}$ to $\sim$2$\ensuremath{''}$) of these multiple ALMA pointings (cite: Wang22; Wang24; Magnelli24). To solve this problem, we instead used the fact that at $\sim$1 mm, galaxies are compact in size (cite: GomezGuijarro22a) and can therefore be considered spatially unresolved at resolutions $\geq$0.2$\ensuremath{''}$, so that $S_{\rm peak}=S_{total}$. Therefore, we excluded images with synthesised beam sizes $<0.2\ensuremath{''}$ from our analysis and ‘stacked’ only primary beam-corrected flux densities measured from the central pixel at each source position. The measured fluxes were renormalised from their observed wavelength (within the ALMA bands 6 or 7) to a common 1.1 mm observed wavelength using the star-forming galaxy SED template of (cite: Bethermin12). The final stacked flux density is the noise-weighted mean of all individual flux densities, $S_i$: $$\begin{equation*}
S_{1.1\,mm,\mathrm{stack}} = \frac{\sum S_{1.1,i} \cdot \sigma_i^{-2} }{\sum\sigma_i^{-2}},
\end{equation*}$$ with $\sigma_i$ the pixel RMS noise at the position of each galaxy.

We first binned galaxies by UV magnitude in four bins: $-22<M_{\mathrm{UV}}<-20$ mag, $-20<M_{\mathrm{UV}}<-19$ mag, $-19<M_{\mathrm{UV}}<-18$ mag, and $-18<M_{\mathrm{UV}}<-17$ mag. Selecting galaxies with $M_{\mathrm{UV}}<-17$ mag yields a total of 2455 galaxies. We provide in Table [\[tab:stack_fluxes\]](#tab:stack_fluxes) the resulting ALMA measurements for each bin as well as the corresponding number of galaxies and pointings.

|  |  |  |  |
|:--:|:--:|:--:|:--:|
|  | N$_{galaxies}$ | N$_{pointings}$ | $\left<S_{\nu}\right>$ |
|  |  |  | $\mu$Jy |
| $-22<M_{\mathrm{UV}}<-20$ | 45 | 198 | 5.4$\pm$3.7 |
| $-20<M_{\mathrm{UV}}<-19$ | 154 | 515 | 5.2$\pm$3.0 |
| $-19<M_{\mathrm{UV}}<-18$ | 629 | 2056 | $<$4.8 |
| $-18<M_{\mathrm{UV}}<-17$ | 1627 | 5943 | $<$2.5 |
| $8< \log$M$_\star<9$ | 1352 | 5341 | $<$2.5 |
| $9< \log$M$_\star<10$ | 59 | 226 | 8.7$\pm$3.8 |
| $10< \log$M$_\star<11$ | 4 | 14 | 38.5$\pm$29.0 |

We show these measurements in the left panel of Fig. [2](#fig:flux) along with the predicted ALMA fluxes obtained from UV-NIR only SED fitting.

![](ALMA_Mstar.pdf)

The ALMA flux of the brightest sources ($M_{\mathrm{UV}}<-20$ mag) is slightly overestimated in the absence of IR constraint although still compatible within the errors. At fainter magnitudes, the upper limit predictions are in agreement with the ALMA measurements. We note that if we assume the ALMA fluxes predicted from the UV-NIR SED modeling, a S/N=3 detection from the ALMA stacking would require approximately 10660 and 52000 sources, in the $-19<M_{\mathrm{UV}}<-18$ mag and $-18<M_{\mathrm{UV}}<-17$ mag bins, respectively, or a deeper ALMA observations of the 629 and 1627 sources observed in these bins, respectively.

We also stacked the ALMA observations of the JADES/A$^3$COSMOS galaxies by bins of stellar mass ($8<\log M_\star/M_\odot<9$, $9<\log M_\star/M_\odot<10$, and $10<\log M_\star/M_\odot<11$), and show the results on the right panel of Fig. [2](#fig:flux). Selecting galaxies with $\log M_\star/M_\odot>8$ yields a total number of 1415 galaxies. The predictions from UV-NIR SED fitting are consistent with the constraints obtained from the ALMA stacking. Despite being the most populated bin (1352 galaxies), the ALMA measurement of the lowest stellar mass bin ($8<\log M_\star/M_\odot<9$) results in a 3$\sigma$ upper limit of 2.5 $\mu$Jy. A factor 5 more sources would be needed according to SED modeling predictions to reach a S/N of 3 on this measurement. These galaxies being less massive, it is expected that they contain less dust than more massive galaxies. We cannot constrain the dust mass of the galaxies of our sample since we only have one ALMA data point probing the 137-157 $\mu$m rest-frame emission. To understand if this non-detection is compatible with the fact that lower-mass galaxies should have lower dust content, we take the stellar mass as a proxy for galaxy SED normalisation and scale down the ALMA flux density obtained from galaxies in the intermediate mass bin ($9<\log M_\star/M_\odot<10$). We obtain a predicted S$_{1.1\,mm}$ of 3.2 $\mu$Jy which is tension with our limit, suggesting that the dust content per unit stellar mass of these low mass systems is indeed lower than that observed in more massive objects.

# Impact of the ALMA constraint on physical properties of $6<z<7$ galaxies

In this section, we investigate the impact of the ALMA constraints on the inference of the physical properties of the JADES subsample. We thus run `CIGALE` a second time using the ALMA stacking measurements as constraints for the IR part of the SED. We attribute to each galaxy the ALMA flux density obtained from stacking according to the derived UV magnitude of the first `CIGALE` run. For example, each galaxy with a UV magnitude within $-22<M_{\mathrm{UV}}<-20$ is attributed a S$_{1.1\,mm}$ of 5.4$\pm$3.7 $\mu$Jy.

![](SED_example.pdf)

In Fig. [3](#fig:sed), we show an example of a $z=6.78$ galaxy with $M_{\mathrm{UV}}=-20.5$ mag and $\log M_\star^{\mathrm{no-IR}}=$9.3. We show on the figure the resulted best fits without and with the ALMA constraint in blue and red, respectively. Clearly, without the ALMA constraint, the IR luminosity is over-predicted by the UV-NIR SED modelling, resulting in a significant A$_{\rm V}$ of 1.1 mag. Using ALMA stacked measurement as a constraint, the A$_{\rm V}$ decreases to 0.3 mag. This difference in A$_{\rm V}$ results in a difference in age, with an older age obtained from the run using ALMA of 235 Myr compared to 105 Myr when ALMA is not used.

To understand the impact of the IR constraint on the derived physical properties of the galaxies of the whole sample, we compare in Fig. [4](#fig:comps) the stellar masses, SFRs, FUV attenuations, and UV continuum $\beta$ slopes obtained with and without the ALMA constraint.

![](comparisons.pdf)

The stellar mass is weakly affected by the addition of the ALMA constraints. However, for galaxies with $8<\log (M_\star^{\mathrm{no-IR}}/M_\odot)<10$ the use of ALMA leads to slightly higher stellar masses, although it is well within the typical error on $M_\star$ which is 0.24 dex. Regarding the SFR, the estimates with and without IR measurements are on average in agreement although there are sources, the most massive ones ($\log (M_\star^{\mathrm{no-IR}}/M_\odot)>8$ for which the SFR is clearly lower using IR measurements, with a median difference of -0.37 dex. For the FUV attenuation, the average trend shows a lower $A_{\rm FUV}$ when ALMA is used but only by 5% on the average value, which is negligible compared to the typical errors on this measurement. However, as for the SFR, we find that for the most massive sources, $A_{\rm FUV}$ is also lower when using IR constraints, with a median value of -0.49 mag. Finally, the UV slope $\beta$ tends to be bluer when using ALMA constraints. The sources that deviate the most from the one-to-one relationship for each parameter are galaxies with $\log (M_\star^{noIR}/M_\odot)>8$. For these sources, without IR constraint, the code is using stronger attenuation to fit the observations while the fit with IR tends toward lower attenuation but older ages instead. This comparison suggests the evidence of biases when estimating the physical properties of $z>6$ galaxies without FIR constraints.

# Dust attenuation properties

In this section, we study the dust attenuation properties of $6<z<7$ galaxies, taking into account the ALMA constraint obtained from stacking. The physical properties of this sample are derived from their distribution (median, 25$^{th}$, and 75$^{th}$ percentiles) using the same weights used to estimate the ALMA fluxes and are provided in Table [\[tab:stack_prop\]](#tab:stack_prop). For bins containing both galaxies with high S/N values and galaxies with upper limits on these physical properties, we derive upper limits of the median value using a parametric approach, that is by fitting a normal distribution to the data and determining the z-score at 84$\%$ confidence level. The upper limit of the bin is then derived by adding to the mean of the distribution the z-score times the standard deviation of the distribution.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | $\left<\textrm{redshift}\right>$ | $\log\left<M_\star\right>$ | $\left<\textrm{SFR}\right>$ | $\left<\beta\right>$ | $\left<M_{\mathrm{UV}}\right>$ | $\left<\textrm{IRX}\right>$ | log $\left<L_{\mathrm{IR}}\right>$ |
|  |  | M$_{\odot}$ | M$_{\odot}$yr$^{-1}$ |  | mag |  | L$_{\odot}$ |
| $-22<M_{\mathrm{UV}}<-20$ | $6.18^{+0.51}_{-0.06}$ | $9.43^{+0.0}_{-0.14}$ | $14.6^{+1.3}_{-6.7}$ | $-2.05^{+0.01}_{-0.03}$ | $-20.47^{+0.38}_{-0.07}$ | $0.05^{+0.12}_{-0.09}$ | $10.53^{+0.06}_{-0.06}$ |
| $-20<M_{\mathrm{UV}}<-19$ | $6.64^{+0.09}_{-0.42}$ | $8.85^{+0.12}_{-0.51}$ | $12.6^{+6.8}_{-4.6}$ | $-2.13^{+0.05}_{-0.18}$ | $-19.44^{+0.19}_{-0.25}$ | $0.30^{+0.16}_{-0.15}$ | $10.42^{+0.25}_{-0.18}$ |
| $-19<M_{\mathrm{UV}}<-18$ | $6.68^{+0.20}_{-0.38}$ | $8.23^{+0.31}_{-0.07}$ | $2.0^{+0.7}_{-1.1}$ | $-2.34^{+0.07}_{-0.07}$ | $-18.40^{+0.25}_{-0.25}$ | $<$-0.09 | $<$9.59 |
| $-18<M_{\mathrm{UV}}<-17$ | $6.62^{+0.12}_{-0.36}$ | $7.99^{+0.21}_{-0.22}$ | $0.7^{+0.3}_{-0.2}$ | $-2.28^{+0.10}_{-0.12}$ | $-17.38^{+0.19}_{-0.28}$ | $<$-0.10 | $<$9.17 |
| $8<\log M_\star<9$ | $6.65^{+0.14}_{-0.36}$ | $8.27^{+0.15}_{-0.12}$ | $0.4^{+0.4}_{-0.2}$ | $-2.16^{+0.22}_{-0.14}$ | $-17.47^{+0.59}_{-0.69}$ | $<$0.11 | $<$9.20 |
| $9<\log M_\star<10$ | $6.19^{+0.53}_{-0.07}$ | $9.27^{+0.14}_{-0.19}$ | $8.8^{+8.3}_{-7.2}$ | $-2.03^{+0.08}_{-0.13}$ | $-20.06^{+0.43}_{-0.48}$ | $0.13^{+0.05}_{-1.82}$ | $10.59^{+0.12}_{-2.30}$ |
| $10<\log M_\star<11$ | $6.31^{+0.00}_{-0.00}$ | $10.86^{+0.00}_{-0.44}$ | $9.2^{+0.0}_{-0.0}$ | $-0.42^{+0.00}_{-0.67}$ | $-18.37^{+0.00}_{-0.96}$ | $1.28^{+0.00}_{-0.24}$ | $10.96^{+0.15}_{-0.00}$ |

Several pre-JWST and JWST studies have reported a relation between the UV $\beta$ slope and UV magnitude such as UV slopes shift towards bluer $\beta$ at low UV luminosities (cite: Finkelstein12; Bouwens14; BhatawdekarConselice21; Topping24). Although still debated at $z>8$, this relation would indicate a trend between dust attenuation, which is the dominant component affecting the UV slope, and UV luminosity that may hint at a relationship between luminosity and metals in early galaxies (cite: Cullen23; Topping24). In Fig. [5](#fig:beta_muv), we compare the UV properties ($\beta$ and $M_{\mathrm{UV}}$) of our sample with sources from the literature at the same redshift.

![](beta_muv.pdf)

Combining our measurement to the stack estimates from REBELS (cite: Bowler24), (cite: Austin24), and (cite: RobertsBorsani24), we obtain the following relation from a linear regression fit: $$\begin{equation}
\beta = -0.08\pm0.03 \times M_{\mathrm{UV}} -3.70\pm0.11.
\end{equation}$$ The resulting slope is in agreement with the relations from (cite: Topping24) who found a $d\beta/dM_{\rm UV}$ slope of $-$0.11$\pm$0.02 and $-$0.12$\pm$0.02 at $z\sim5.9$ and $z\sim7.3$, respectively, as well as the slopes obtained at $z\sim5$ by (cite: Rogers14) and (cite: Bouwens14) within errors (-0.12$\pm$0.02 and -0.14$\pm$0.02, respectively).

![](lir_muv.pdf)

The ALMA stacking provides a constraint on the IR luminosity of the galaxies of our sample. In Fig. [6](#fig:lir_muv), we show the $L_{\mathrm{IR}}$ as a function of UV magnitude. The JADES sample combined with A$^3$COSMOS observations allows us to probe fainter magnitudes and extend the $L_{\mathrm{IR}}$ vs M$_{UV}$ relation down to M$_{UV}\sim-17$ mag. Our sample has $\log L_{\mathrm{IR}}/L_\odot$ spanning from 7.4 to 12.3 with a median value of 9.3. For comparison, we add the stacked measurements of the REBELS sample as well as those from the ALPINE sample at $z\sim5.5$ from (cite: Khusanova21). Both these samples probe higher UV magnitude ranges and higher IR luminosities. A fit to the REBELS+ALPINE stacked signals combined with our two highest UV magnitude bins yields the following relation:

$$\begin{equation}
\log \left(L_{\mathrm{IR}}/L_{\odot}\right) = -0.31\pm0.05 \times M_{\mathrm{UV}} + 4.31\pm0.42.
\end{equation}$$

Extended to fainter UV magnitude, this relation predicts higher $L_{\mathrm{IR}}$ at M$_{UV}>$-19 than our estimates using ALMA. At M$_{UV}=$-18.4 mag and -17.4 mag, the relation derived from higher UV magnitudes overestimates the $L_{\mathrm{IR}}$ by 0.45 dex and 0.56 dex, respectively. This is a possible hint at a breakdown in the $L_{\mathrm{IR}}$ vs M$_{UV}$ relation at low UV magnitudes that could be due to lower dust content. For the two UV faintest bin that have a median M$_{UV}$ of -18.4 and -17,4, the average stellar mass are $\log M_{\star}/M_\odot = 8.2$ and 8.0, respectively. These two UV bins have also low dust attenuation: 0.31 and 0.33, respectively. Therefore, at these low UV magnitude, we are dominated by low-mass, low-attenuation systems, leading to a turnover of L$_{IR}$, which has been already observed at lower redshift ($z\sim4$) by (cite: Bernhard14).

## IRX versus $\beta$

![](IRX_beta.pdf)

We place our measurements, obtained from ALMA stacking in UV magnitude bins, on the IRX-$\beta$ diagram in Fig. [7](#fig:irx_beta). Our averaged data points are close to the stacked measurements from REBELS, especially the brightest UV magnitude bin ($-22<M_{\mathrm{UV}}<-20$) which corresponds to the UV magnitude range probed by the REBELS galaxies. They disfavour the expected relation from a SMC extinction curve but are compatible with a (cite: Calzetti00) relations used in (cite: Bowler24) with $\beta_0=-2.3$. Although our SFH library has a wide range of $\beta_0$, galaxies of our sample favour blue $\beta_0$ with a median value of -2.5, which is consistent with the assumed $\beta_0$ of (cite: Reddy18). Therefore, including the effect of dust, our sample has relatively blue $\beta$ with a median value of -2.25.

Galaxies of our sample are also compatible with both the starburst and SMC relations of (cite: Reddy18) who used them with a different $\beta_0$ than (cite: Bowler24) ($\beta_0=-2.6$). These relations were found by (cite: Boquien22) to be suitable for the ALPINE sample. In our process, we tested letting the $\delta$ slope of the attenuation curve free, like in (cite: Boquien22). However, the improvement of the fit, using a $\Delta$BIC analysis (Bayesian Information Criterion), proved to be statistically significant for only 3.7$\%$ of the sample. Therefore, we kept $\delta$ fixed to 0 (no modification of the attenuation curve). Although they seem to favour the (cite: Reddy18) relations, most of estimates at low IRX are obtained from the ALMA upper limits on the IR and are thus upper limits on the IRX, as indicated by the two faintest UV magnitude bins. However, at higher IRX, our estimates are compatible with both a (cite: Calzetti00) with $\beta_0=-2.3$ and (cite: Reddy18) relations (starbursts and SMC, using $\beta_0=-2.6$). These findings are consistent with the results that grain size and dust composition at very high redshift are similar to local starbursts and SMC, indicating no fundamental evolution. Our results confirm that at $z>6$, there is no clear sign of a break-down of (cite: Calzetti00) relation.

## IRX versus stellar mass

![](IRX_Mstar.pdf)

We place our galaxies on the IRX-$M_\star$ plane in Fig. [8](#fig:irx_mstar). Specifically in this figure, we use the results of the SED fitting using the ALMA constraints obtained from stacking in bins of stellar mass ($8<\log M_\star/M_\odot<9$, $9<\log M_\star/M_\odot<10$, and $10<\log M_\star/M_\odot<11$). Along with our data points, we add the relations from (cite: Pannella15) at $z\sim 1-3$, (cite: Magnelli24) at $4<z<5$, (cite: Fudamoto20) at $z\sim 5.5$, and (cite: Bowler24) at $z\sim 7$.

Our low mass bin upper limit on IRX does not provide any useful constraint on the position of these galaxies on the IRX-$M_\star$ plane. The intermediate mass median value is compatible with the relations of (cite: Bowler24), (cite: Magnelli24), and marginally with the relation of (cite: Fudamoto20). There seems to be a better agreement with the relation of (cite: Bowler24) albeit the large scatter indicated by the errorbars (25$^{th}$ and 75$^{th}$ percentile). The high mass bin data point is in agreement with both (cite: Magnelli24) and (cite: Fudamoto20) relations, and marginally with the (cite: Bowler24) relation, but here again, the large scatter does not allow us to discriminate a relation. For comparison, we show the brightest UV magnitude bin, $-22<M_{UV}<-20$ (red star), for consistency with the REBELS sample and find that it falls on the relation from (cite: Bowler24), thus in agreement with their result. Finally, we show the relation obtained by (cite: Pannella15) at lower redshift ($z<4$), indicating that there is a clear decrease of IRX at fixed stellar mass with increasing redshift.

## Impact of dust temperature assumption

At $6<z<7$, ALMA 1.1 mm probes the 137-157 $\mu$m rest frame which provides a good constraint on the peak of the IR SED. However, with only one flux measurement in the IR, the $L_{\mathrm{IR}}$ strongly depends on the assumption taken on the IR SED shape. In the dust emission model of (cite: Schreiber18), this shape is handled through two free parameters: the PAH fraction and the dust temperature. The PAH fraction has little effect on the $L_{\mathrm{IR}}$, but the dust temperature, that we originally fixed at 47 K, is a key assumption that we can test in this section. We run `CIGALE` several times, each time fixing the dust temperature to a different value. Given their extreme $L_{\mathrm{IR}}$ (Fig. [6](#fig:lir_muv)), on average higher than the galaxies of our sample, we consider the dust temperature of REBELS galaxies determined by (cite: Sommovigo22) to be the maximum dust temperature for our galaxies. We thus only decrease T$_{\mathrm{dust}}$ from the original assumption (47 K) down to a minimum value of 30 K, which corresponds to the lowest temperature of REBELS galaxies found by (cite: Sommovigo22) (REBELS-32, 39 K minus the lower error of 9 K). We note that (cite: Mitsuhashi24) found temperatures as low as 26$^{+14.5}_{-6.5}$ K in the SERENADE sample, which is typical of dust temperature at $z<1$ (cite: Schreiber18), and, recently, (cite: Algera24) obtained a dust temperature of 32$^{+9}_{-6}$ K for REBELS-25, a galaxy at redshift 7.31. Our lowest assumed temperature of 30 K is thus also consistent with the temperatures derived from the SERENADE sample and REBELS-25.

![](LIR_lowT_MUV_full.pdf)

![](LIR_lowT_full.pdf)

We look at the distribution of $L_{\mathrm{IR}}$ using either the UV magnitude bins for the ALMA stacking (Fig. [9](#fig:lir_muv_lowT)) or stellar mass bins (Fig. [10](#fig:lir)). We show the results of the SED modelling run for each dust temperature assumption (30, 33, 36, 39, 42, 45, and 47 K). As expected, the effect of decreasing dust temperature assumption is to shift the $L_{\mathrm{IR}}$ distributions towards lower values. However, temperatures higher than $\sim$36 K result in similar $L_{\mathrm{IR}}$. This is due to the fact that the rest frame range probed by the ALMA constraint at these redshifts is close to the peak of the IR SED at high temperature. Therefore, if the dust temperature in these galaxies is higher than $\sim$36 K (value used in our test), then the $L_{\mathrm{IR}}$ estimate is quite reliable. Despite these uncertainties on the IR SED, the distributions shown in Fig. [9](#fig:lir_muv_lowT) and Fig. [10](#fig:lir) provide average constraints on the range of $L_{\mathrm{IR}}$ of the bulk of galaxies at $6<z<7$.

![](IRX_Mstar_beta_lowT.pdf)

The impact of T$_{\mathrm{dust}}$ on the different physical properties studied in Sect. [\[dust_results\]](#dust_results) is presented in Fig. [11](#fig:irx_mstar_beta_lowT). This figure shows on the left panel the IRX-M$_\star$ plane using ALMA observations stacked in stellar mass bins, assuming the same set of dust temperatures than in Fig. [9](#fig:lir_muv_lowT). As expected, the IRX parameter is affected. Very small variations are also found in M$_\star$ due to the fact that `CIGALE` performs SED modelling using energy balance over the whole wavelength range, another indication on the error on the measurement that we can have on this parameter. Despite the wide range of dust temperature, the intermediate mass bin galaxies are still compatible with the (cite: Bowler24) relation. A strong effect is however observed for the most massive bin, but this bin contains only 4 galaxies and is thus more subject to statistical variations.

On the right panel of Fig. [11](#fig:irx_mstar_beta_lowT), we show the impact of dust temperature assumption on the IRX-$\beta$ diagram. The conclusions of Sect. [\[dust_results\]](#dust_results) are still valid: Our data points are compatible with a (cite: Calzetti00) relation using $\beta_0=-2.3$ or the (cite: Reddy18) relation for starburst and SMC with $\beta_0=-2.6$. Even with a more accurate estimate on the dust temperature, it will be difficult to discriminate, within the errors, between these relations in this $\beta$ range.

# Infrared constraints at $z>7$

We apply the ALMA stacking analysis described in Sect. [\[stack\]](#stack) on JADES galaxies at $z>7$ . The measurements result only in upper limits, however they provide first constraints on the IR emission of the bulk of the population at these redshifts. We provide these upper limits in Table [1](#tab:stack_fluxes_z7) in UV magnitude and stellar mass bins. We then perform the same SED modelling procedure on the $z>7$ sources as for the $6<z<7$ redshift bin, assuming the same dust temperature of $T_{\rm dust}=$47 K.

+:-------------------------:+:--------------:+:---------------:+:----------------------:+
|                           | N$_{galaxies}$ | N$_{pointings}$ | $\left<S_{\nu}\right>$ |
+---------------------------+----------------+-----------------+------------------------+
|                           |                |                 | $\mu$Jy                |
+---------------------------+----------------+-----------------+------------------------+
| **7$<$z$<$9**                                                                         |
+---------------------------+----------------+-----------------+------------------------+
| $-22<M_{\mathrm{UV}}<-20$ | 17             | 55              | $<$26.4                |
+---------------------------+----------------+-----------------+------------------------+
| $-20<M_{\mathrm{UV}}<-19$ | 90             | 267             | $<$13.6                |
+---------------------------+----------------+-----------------+------------------------+
| $-19<M_{\mathrm{UV}}<-18$ | 302            | 1058            | $<$6.2                 |
+---------------------------+----------------+-----------------+------------------------+
| $-18<M_{\mathrm{UV}}<-17$ | 893            | 3337            | $<$3.2                 |
+---------------------------+----------------+-----------------+------------------------+
| $8<$ log M$_\star<9$      | 863            | 3527            | $<$2.9                 |
+---------------------------+----------------+-----------------+------------------------+
| $9<$ log M$_\star<10$     | 35             | 130             | $<$14.8                |
+---------------------------+----------------+-----------------+------------------------+
| $10<$ log M$_\star<11$    | 4              | 18              | $<$72.0                |
+---------------------------+----------------+-----------------+------------------------+
| **9$<$z$<$12**                                                                        |
+---------------------------+----------------+-----------------+------------------------+
| $-22<M_{\mathrm{UV}}<-20$ | 7              | 18              | $<$62.3                |
+---------------------------+----------------+-----------------+------------------------+
| $-20<M_{\mathrm{UV}}<-19$ | 40             | 170             | $<$11.0                |
+---------------------------+----------------+-----------------+------------------------+
| $-19<M_{\mathrm{UV}}<-18$ | 159            | 479             | $<$9.4                 |
+---------------------------+----------------+-----------------+------------------------+
| $-18<M_{\mathrm{UV}}<-17$ | 403            | 1447            | $<$4.5                 |
+---------------------------+----------------+-----------------+------------------------+
| $8<$ log M$_\star<9$      | 452            | 1734            | $<$3.8                 |
+---------------------------+----------------+-----------------+------------------------+
| $9<$ log M$_\star<10$     | 33             | 127             | $<$14.4                |
+---------------------------+----------------+-----------------+------------------------+
| $10<$ log M$_\star<11$    | 2              | 4               | $<$188.0               |
+---------------------------+----------------+-----------------+------------------------+

: Results of the ALMA stacking analysis at $7<z<9$ and $9<z<12$.

## Evolution of $\beta$

![](beta_redshift.pdf)

We examine $\beta$ as a function of redshift in Fig. [12](#fig:betaz). Although galaxies of our sample are slightly redder than the averaged measurements of (cite: RobertsBorsani24) at the same redshifts, they do not show extreme values and lie within the range spanned by individual galaxies in the literature. As discussed in (cite: Franco24) (cite: Topping24), there is a caveat in using SED modelling to measure $\beta$ as models are limited to a given $\beta$ value toward the blue side of the distribution, in our case this value is defined by the lowest intrinsic value allowed by our model: $\beta_0=-2.77$. On the other hand, despite being more flexible, a direct measurement of $\beta$ from the data can also introduce systematics due to the different rest-frame wavelength range used to measure $\beta$.

To understand to which extent our results could be affected by the lower limit on $\beta_0$ induced by SED modelling, we show in the inset panel of Fig. [12](#fig:betaz) the distributions of $\beta_0$ allowed by our models (dark blue), $\beta_0$ obtained from the SED fitting run (cyan), the $\beta$ for our galaxies (purple). For the total sample, that is the three redshift bins, only 15$\%$ of the galaxies select the lowest possible value of $\beta_0$. A Kolmogorov-Smirnov test indicate that these galaxies have similar redshift and $A_{\rm FUV}$ distributions to the total sample, but different $M_\star$ and ages distributions resulting in lower values for both properties. The fact that galaxies with the lowest $\beta_0$ are not at a particular redshift means that these galaxies would not necessarily drive a trend that we would be missing between $\beta$ and redshift. Furthermore, although we would expect to miss galaxies with the bluest $\beta$ in the highest redshift bin from the expected trend, only 5$\%$ of these $z=$9-12 galaxies have the lowest $\beta_0$ value compared to 18 and 13$\%$ at $z=$6-7 and $z=$7-9, respectively. Therefore, despite the fact that we may miss a fraction of galaxies with extreme blue colours, our results seem to favour a relatively flat relation between $\beta$ and redshift.

The $\beta$ distribution of our sample points toward an absence of trend between $\beta$ and redshift. A trend would be expected with galaxies having bluer colours with increasing redshift since they become progressively metal- and dust-poor (cite: Topping24; Cullen23). Recently, (cite: Cullen23) found extremely blue galaxies at $z\sim$12 with a median $\beta$ of -2.5 while (cite: Topping24) obtained a median $\beta$ of -2.48$^{+0.14}_{-0.12}$ on a sample drawn from JADES. At the same redshift, we find a median value of -2.14$\pm$0.21 which is slightly redder. Although both the studies from (cite: Cullen23) and (cite: Topping24) found a decrease of $\beta$ with increasing redshift, the latter mention that the rate of this evolution is slowest at low UV luminosities with minor differences between galaxies with $M_{UV}=-18$ at $z=$5-9 and $z>9$. The bulk of our sample are UV faint (see Fig. [6](#fig:lir_muv)) and the absence of strong evolution that we observe for the whole sample is thus consistent with the finding from (cite: Topping24). Interestingly, we note that $\beta$ is slightly redder in the highest redshift bin ($z>9.5$) possibly confirming the results of (cite: Saxena24) who found such a redder $\beta$ at the same redshift using a spectroscopic sample. They interpret this redder value from a rapid build-up of dust content in the very early Universe or a significant contribution from the nebular continuum emission to the observed UV spectra, depending on gas temperatures and densities.

We now try to put constraints on the evolution of $L_{\mathrm{IR}}$ with redshift. At these high redshifts, the temperature of the Cosmic Microwave Background (CMB) increases rapidly reaching 19 K, 22 K, 27 K, and 30 K at $z=$6, 7, 9, and 10, respectively (cite: DaCunha13). If not taken into account in the SED fitting procedure, the impact of the CMB results in an under-estimation of the $L_{\mathrm{IR}}$ that depends on the dust temperature and redshift. (cite: DaCunha13) demonstrated that for $T_{\rm dust}=40$ K, the $L_{\mathrm{IR}}$ is under-estimated by -0.018, -0.019, -0.045, and -0.070 dex at $z=$6, 7, 9, and 10, respectively. We thus correct our $L_{\mathrm{IR}}$ measurement accordingly in Fig. [13](#fig:lirz) where we show them as a function of redshift. We note that at $6<z<7$ the correction is negligible and was not taken into account in Fig. [6](#fig:lir_muv). For comparison, we add on Fig. [13](#fig:lirz) individual measurements from the literature: the REBELS sample (cite: Inami22), the SERENADE sample (cite: Mitsuhashi24), and the individual sources of (cite: Laporte17), (cite: Tamura19), (cite: Laporte19), and (cite: Schouws24). Fig. [13](#fig:lirz) highlights the fact that the bulk of the population is still out of reach and that the samples on which models are basing their assumptions have extreme IR properties.

![](lir_redshift.pdf)

## Dust formation in early galaxies

Combining V-band attenuation and sSFR measured from JWST/NIRSpec spectra of 631 galaxies at $3<z<14$, (cite: Langeroodi24) found that dust must have appeared rapidly and that attenuation follows star formation on timescales shorter than $\sim$30 Myr, favouring the scenario where dust is produced by supernovae (SN). They found a linear correlation between A$_{\rm V}$ and the inverse sSFR (sSFR$^{-1}$, a proxy for the age of the galaxies) for galaxies with redshift from 3 to 14, and $\beta$ from -3 to 0. Through a model, they show that the slope of this relation, $\gamma$, depends on several dust properties such as the efficiency of SN in producing dust, the fraction of dust destroyed by SN reverse and forward shocks, the fraction of dust removed from galaxy by feedback-driven outflows, dust geometry, and dust grain properties. They obtained $\gamma=0.67\pm0.2$ cm$^2$g$^{-1}$, 30 times lower than the value expected if the entire SN dust yield were preserved in the ISM, and had Milky-Way-like grain properties. Here, we use our photometry-based estimates of A$_{\rm V}$, M$_\star$, and SFR, to compare the results obtained with thus two different methods.

![image](av_invssfr.pdf) ![image](av_invssfr_noir.pdf)

In Fig. [14](#fig:avssfr), we show the V-band attenuation as a function of the inverse sSFR for the whole sample ($6<z<12$) binned by UV slope $\beta$, similarly to (cite: Langeroodi24). Consistently with the results of the previous sections, we confirm a rapid dust production in early galaxies with non-negligible dust attenuation at sSFR$^{-1}>30$ Myr. Despite using different methods (spectroscopy vs photometry-based SED modelling), our data points also confirm the linear relation between A$_{\rm V}$ and sSFR$^{-1}$ found by (cite: Langeroodi24), implying that dust production is driven by star formation activity and stellar mass build-up.

However, the intercept and slope of the relation obtained by our sample are lower and flatter, respectively: $$\begin{equation}
\log A_{\mathrm{V}} = (0.61\pm0.05) \times \log \mathrm{sSFR}^{-1} - (0.30\pm0.03).
\end{equation}$$

First we checked if the flatter slope that we observe is due to the SED modelling by performing a mock analysis (cite: Buat15; Ciesla17; Boquien19). Basically, we ran `CIGALE` once on the JADES galaxies. We took the best fit SED, convolved it in the JADES+ALMA set of filters, added noise to the photometry. We ran again `CIGALE` on the mock photometry. In this way we can compare estimated parameters to the true ones used to build the mock photometry. From this test, we find that sSFR$^{-1}$ is recovered within errorbars with a systematic overestimate (60%) and that A$_{\rm V}$ is systematically underestimated by -0.4 mag. However, applying corrections derived from this mock analysis does not yield a slope consistent with the observations from (cite: Langeroodi24) (0.58$\pm$0.12). Although we looked at the impact of dust temperature assumption in Sect. [\[tdust\]](#tdust) and concluded that it does not affect strongly our conclusions for the $6<z<7$ redshift bin, studies predict that dust temperature keep increasing with redshift (cite: Sommovigo22; Mitsuhashi24). The temperature of 47 K that we assumed in this work is consistent with the results and prediction of (cite: Sommovigo22) and (cite: Mitsuhashi24). However, it can reach up to 60-65 K at $z>7$. We thus test the impact of increasing the assumption on T$_{\rm dust}$ for galaxies in the $9<z<12$ to 60 K (maximum value available in (cite: Schreiber18) library) and look at the impact of it on the slope of the A$_{\rm V}$-sSFR$^{-1}$ relation. We obtain a slope of 0.63$\pm$0.05 and conclude that the assumption on T$_{\rm dust}$ is not causing the difference observed between our study and the results of (cite: Langeroodi24).

We then test if the use of ALMA constraints is causing the discrepancy. Indeed, left panel Fig. [4](#fig:comps) shows that A$_{\rm FUV}$ is lower when ALMA information is used in the SED modelling. However, using A$_{\rm V}$, M$_{\star}$, and SFR obtained from the UV-to-NIR SED modelling run (Fig. [4](#fig:comps), right panel), our binned points are in perfect agreement with (cite: Langeroodi24). We obtain a slope of 0.91$\pm$0.17 if we discard the reddest $\beta$ bin which seems to be discrepant and has a much lower statistics than the other bins. Therefore, we conclude that the addition of ALMA constraints is at the origin of the different slopes between the spectroscopic sample of (cite: Langeroodi24) and our photometric one. Our flatter slope increases even more the discrepancy with $\gamma$ obtained in Milky-Way conditions, but also points towards a relation between sSFR$^{-1}$ and the SFR surface density ($\Sigma_{\rm SFR}$ ) for which we do not have access for our sample.

# Conclusions

To place constraints on dust emission in galaxies at the epoch of reionization, we have used the A$^3$COSMOS (A$^3$GOODSS) database to stack all JADES galaxies at $6<z<12$ with available ALMA coverage in band 6 and 7. Focusing on the $6<z<7$ redshift bin, our results are summarized as follows:

- ALMA stacks result in upper limits for galaxies with $M_{\mathrm{UV}}>$-19 and $\log M_\star<9$, and tentative detections at brighter UV magnitudes and higher stellar masses at $6<z<7$.

- Upper limits for UV faint galaxies are in agreement with predicted ALMA fluxes from UV-to-NIR SED fitting while ALMA fluxes are lower than predicted for UV bright $M_{\mathrm{UV}}<$-20 galaxies. For galaxies binned with stellar mass, the predicted fluxes without ALMA constraint and the ALMA fluxes are in agreement. However, for galaxies with $\log M_\star<9$, there is a tension between the ALMA derived upper limit (3$\sigma$) and the flux expected from scaling down the ALMA flux of the upper stellar mass bin. This is a hint at a possible lower dust to stellar mass ratio at these low stellar masses.

- The addition of the ALMA constraints for the SED modelling results in lower SFR (0.4 dex), lower $A_{\rm FUV}$ (0.5 dex) for galaxies with $\log M_\star>8$, as well as slightly higher stellar masses and lower $\beta$ for the same sources, implying older stellar population (25% older on average).

- Using infrared constraints for the SED modelling, our $\beta$ vs $M_{\mathrm{UV}}$ is consistent with measurements from the literature, and in perfect agreement with the relation from (cite: Topping24).

- Our measurements extend the $L_{\mathrm{IR}} - M_{\mathrm{UV}}$ relation down to $M_{\mathrm{UV}}\sim -19$ and hint at a possible breakdown of the relation at fainter UV magnitudes.

- When the ALMA constraints are used in the fitting, galaxies are consistent with the literature (REBELS and ALPINE) when placed on the IRX vs $\beta$ indicating similar dust composition and content than in these UV-selected samples. Our stack measurements computed in bins of stellar masses do not provide strong constraints on the IRX-$M_\star$ relation. However, the position of our UV bright bin ($M_{\mathrm{UV}}<-20$) is in good agreement with the relation from (cite: Bowler24). Nevertheless, we find that a given stellar mass, the IRX decreases with increasing redshift.

We tested the impact of dust temperature assumption on our results and find that temperature assumptions between 36 K and 47 K yield similar $L_{\mathrm{IR}}$. The conclusions obtained with a dust temperature of 47 K are still valid when changing the assumed dust temperature: In the IRX-$\beta$ diagram, our points are compatible with a (cite: Calzetti00) relation using $\beta_0=-2.3$ or the (cite: Reddy18) relation for starburst and SMC ($\beta_0=-2.6$). Regarding IRX-$M_\star$, even with a more accurate estimate of the dust temperature, it will be difficult to discriminate, within the errors, between the different relations from the literature in this $\beta$ range.

Combining the whole sample ($6<z<12$), we obtain the following results:

- We did not find a clear evolution of $\beta$ with redshift for the galaxies of our sample and showed that this absence of variation is not due to the lower limit in $\beta_0$ imposed by our SED modelling procedure as only 5% of galaxies at $z>9$ have the lowest value, and 15% of the whole sample at $z>6$. Considering that the median $M_{\mathrm{UV}}$ of our sample is -17.24$_{-0.62}^{+0.54}$, this non evolution is consistent with the results of (cite: Topping24) at similar UV magnitude range.

- We provided upper limits on the IR luminosity of NIRCam-selected galaxies at $z>7$, and show that detected sample from the literature (REBELS, SERENADE, and individual detections) are not representative of the bulk of galaxies at these redshifts.

- We confirmed a linear relation between the V-band attenuation and the inverse sSFR showing a non-negligible attenuation at sSFR$^{-1}>30$ Myr and a flatter slope than obtained from (cite: Langeroodi24) from a spectroscopic sample, due to the use of ALMA constraints in our physical properties measurements.

Our results focused on $6<z<7$ galaxies indicate that the dust properties at the Epoch of Reionization are mostly similar to lower redshift galaxies, implying that a significant dust production must have already happened by $z\sim6.5$. However, the breakdown observed in the $L_{\rm IR}$ versus $M_{\rm UV}$ relation at $M_{\rm UV}\geq$-19 is possible hint at a different regime in the UV faint galaxies. These galaxies have on average low masses ($\log M_\star\sim8$) resulting in shallower gravitational potential that could allow metals to escape, thus resulting in less dust. Or it could be also be due to the lower SFR measured in these sources ($\sim$0.5-2 M$_{\odot}$yr$^{-1}$) resulting in a lower dust production. Nevertheless, the rapid build-up concluded from the $6<z<7$ galaxies is also confirmed by the non-negligible amount of attenuation observed at sSFR$^{-1}>30$ Myr for galaxies with $6<z<12$.

# Acknowledgements

LC warmly thanks A. Ferrara, J. Lewis, M. Trebitsch, and D. Elbaz for insightful discussions that improved greatly this work. The authors thank the JADES team for the huge work and effort put in the preparation, observation, and production of the data used in this work. This work received support from the French government under the France 2030 investment plan, as part of the Initiative d’Excellence d’Aix-Marseille Université – A\*MIDEX AMX-22-RE-AB-101. This project has received financial support from CNRS and CNES through the MITI interdisciplinary programs. SA gratefully acknowledges the Collaborative Research Center 1601 (SFB 1601 sub-project C2) funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) – 500700252. LC and MB acknowledges the funding of the French Agence Nationale de la Recherche for the project iMAGE (grant ANR-22-CE31-0007). NIRCam was built by a team at the University of Arizona (UofA) and Lockheed Martin’s Advanced Technology Center, led by Prof. Marcia Rieke at UoA. ES acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. MB gratefully acknowledges support from the ANID BASAL project FB210003 and from the FONDECYT regular grant 1211000. This work was supported by the French government through the France 2030 investment plan managed by the National Research Agency (ANR), as part of the Initiative of Excellence of Université Côte d’Azur under reference number ANR-15-IDEX-01.

99 natexlab

(ref: Adscheid24) Adscheid, S., Magnelli, B., Liu, D., et al. 2024, A&A, 685, A1

(ref: Algera24) Algera, H. S. B., Inami, H., De Looze, I., et al. 2024, MNRAS, 533, 3098

(ref: Algera23) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142

(ref: Arrabal23) Arrabal Haro, P., Dickinson, M., Finkelstein, S. L., et al. 2023, ApJL, 951, L22

(ref: Austin23) Austin, D., Adams, N., Conselice, C. J., et al. 2023, ApJL, 952, L7

(ref: Austin24) Austin, D., Conselice, C. J., Adams, N. J., et al. 2024, arXiv e-prints, arXiv:2404.10751

(ref: Bakx20) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294

(ref: Barisic17) Barisic, I., Faisst, A. L., Capak, P. L., et al. 2017, ApJ, 845, 41

(ref: Bernhard14) Bernhard, E., Béthermin, M., Sargent, M., et al. 2014, MNRAS, 442, 509

(ref: Bethermin12) Béthermin, M., Daddi, E., Magdis, G., et al. 2012, ApJL, 757, L23

(ref: Bethermin20) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: BhatawdekarConselice21) Bhatawdekar, R. & Conselice, C. J. 2021, ApJ, 909, 144

(ref: Boquien12) Boquien, M., Buat, V., Boselli, A., et al. 2012, A&A, 539, A145

(ref: Boquien22) Boquien, M., Buat, V., Burgarella, D., et al. 2022, A&A, 663, A50

(ref: Boquien19) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: Bouwens14) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2014, ApJ, 793, 115

(ref: Bouwens22) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160

(ref: Bowler18) Bowler, R. A. A., Bourne, N., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2018, MNRAS, 481, 1631

(ref: Bowler22) Bowler, R. A. A., Cullen, F., McLure, R. J., Dunlop, J. S., & Avison, A. 2022, MNRAS, 510, 5088

(ref: Bowler24) Bowler, R. A. A., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 5808

(ref: Brammer08) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503

(ref: BruzualCharlot03) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Buat15) Buat, V., Oi, N., Heinis, S., et al. 2015, A&A, 577, A141

(ref: Bunker23) Bunker, A. J., Cameron, A. J., Curtis-Lake, E., et al. 2023, arXiv e-prints, arXiv:2306.02467

(ref: Calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Calzetti94) Calzetti, D., Kinney, A. L., & Storchi-Bergmann, T. 1994, ApJ, 429, 582

(ref: Capak15) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455

(ref: Castellano22) Castellano, M., Fontana, A., Treu, T., et al. 2022, ApJL, 938, L15

(ref: Ciesla17) Ciesla, L., Elbaz, D., & Fensch, J. 2017, A&A, 608, A41

(ref: Ciesla24) Ciesla, L., Elbaz, D., Ilbert, O., et al. 2024, A&A, 686, A128

(ref: Cole23) Cole, J. W., Papovich, C., Finkelstein, S. L., et al. 2023, arXiv e-prints, arXiv:2312.10152

(ref: Cullen23) Cullen, F., McLure, R. J., McLeod, D. J., et al. 2023, MNRAS, 520, 14

(ref: CurtisLake23) Curtis-Lake, E., Carniani, S., Cameron, A., et al. 2023, Nature Astronomy, 7, 622

(ref: DaCunha13) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: Donnan23) Donnan, C. T., McLeod, D. J., Dunlop, J. S., et al. 2023, MNRAS, 518, 6011

(ref: Draine78) Draine, B. T. 1978, ApJS, 36, 595

(ref: Dwek86) Dwek, E. 1986, ApJ, 302, 363

(ref: Eisenstein23b) Eisenstein, D. J., Johnson, B. D., Robertson, B., et al. 2023a, arXiv e-prints, arXiv:2310.12340

(ref: Eisenstein23) Eisenstein, D. J., Willott, C., Alberts, S., et al. 2023b, arXiv e-prints, arXiv:2306.02465

(ref: Elbaz18) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110

(ref: Endsley22) Endsley, R., Stark, D. P., Fan, X., et al. 2022, MNRAS, 512, 4248

(ref: Faisst20) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: Ferrara23) Ferrara, A., Pallottini, A., & Dayal, P. 2023, MNRAS, 522, 3986

(ref: Ferrara22) Ferrara, A., Sommovigo, L., Dayal, P., et al. 2022, MNRAS, 512, 58

(ref: Finkelstein23) Finkelstein, S. L., Bagley, M. B., Ferguson, H. C., et al. 2023, ApJL, 946, L13

(ref: Finkelstein12) Finkelstein, S. L., Papovich, C., Salmon, B., et al. 2012, ApJ, 756, 164

(ref: Franco24) Franco, M., Akins, H. B., Casey, C. M., et al. 2024, ApJ, 973, 23

(ref: Franco18) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152

(ref: Fudamoto20) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, A&A, 643, A4

(ref: GomezGuijarro22a) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 658, A43

(ref: Hainline23) Hainline, K. N., Johnson, B. D., Robertson, B., et al. 2023, arXiv e-prints, arXiv:2306.02468

(ref: Harikane23b) Harikane, Y., Nakajima, K., Ouchi, M., et al. 2023a, arXiv e-prints, arXiv:2304.06658

(ref: Harikane23) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023b, ApJS, 265, 5

(ref: Hashimoto19) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71

(ref: Haskell23) Haskell, P., Smith, D. J. B., Cochrane, R. K., Hayward, C. C., & Anglés-Alcázar, D. 2023, MNRAS, 525, 1535

(ref: Hodge16) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103

(ref: Hollenbach&Tielens97) Hollenbach, D. J. & Tielens, A. G. G. M. 1997, ARA&A, 35, 179

(ref: Inami22) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126

(ref: Khusanova21) Khusanova, Y., Bethermin, M., Le Fèvre, O., et al. 2021, A&A, 649, A152

(ref: Komatsu11) Komatsu, E., Smith, K. M., Dunkley, J., et al. 2011, ApJS, 192, 18

(ref: Langeroodi24) Langeroodi, D., Hjorth, J., Ferrara, A., & Gall, C. 2024, arXiv e-prints, arXiv:2410.14671

(ref: Laporte17) Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJL, 837, L21

(ref: Laporte19) Laporte, N., Katz, H., Ellis, R. S., et al. 2019, MNRAS, 487, L81

(ref: LeFevre20) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: Li24) Li, J., Da Cunha, E., González-López, J., et al. 2024, arXiv e-prints, arXiv:2409.10961

(ref: Liu19) Liu, D., Lang, P., Magnelli, B., et al. 2019, ApJS, 244, 40

(ref: Magnelli24) Magnelli, B., Adscheid, S., Wang, T.-M., et al. 2024, arXiv e-prints, arXiv:2405.18086

(ref: Markov24) Markov, V., Gallerani, S., Ferrara, A., et al. 2024, arXiv e-prints, arXiv:2402.05996

(ref: Meurer99) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64

(ref: Mitsuhashi24) Mitsuhashi, I., Harikane, Y., Bauer, F. E., et al. 2024, ApJ, 971, 161

(ref: Naidu22) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJL, 940, L14

(ref: Narayanan18) Narayanan, D., Conroy, C., Davé, R., Johnson, B. D., & Popping, G. 2018, ApJ, 869, 70

(ref: Pallottini22) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621

(ref: Pannella15) Pannella, M., Elbaz, D., Daddi, E., et al. 2015, ApJ, 807, 141

(ref: Popping17) Popping, G., Somerville, R. S., & Galametz, M. 2017, MNRAS, 471, 3152

(ref: Reddy18) Reddy, N. A., Shapley, A. E., Sanders, R. L., et al. 2018, ApJ, 869, 92

(ref: Rieke23) Rieke, M. & the JADES Collaboration. 2023, arXiv e-prints, arXiv:2306.02466

(ref: RobertsBorsani24) Roberts-Borsani, G., Treu, T., Shapley, A., et al. 2024, arXiv e-prints, arXiv:2403.07103

(ref: Robertson24) Robertson, B., Johnson, B. D., Tacchella, S., et al. 2024, ApJ, 970, 31

(ref: Robertson23) Robertson, B. E., Tacchella, S., Johnson, B. D., et al. 2023, Nature Astronomy, 7, 611

(ref: Rogers14) Rogers, A. B., McLure, R. J., Dunlop, J. S., et al. 2014, MNRAS, 440, 3714

(ref: SalimNarayanan20) Salim, S. & Narayanan, D. 2020, ARA&A, 58, 529

(ref: Salpeter55) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: Saxena24) Saxena, A., Cameron, A. J., Katz, H., et al. 2024, arXiv e-prints, arXiv:2411.14532

(ref: Schouws24) Schouws, S., Bouwens, R. J., Ormerod, K., et al. 2024, arXiv e-prints, arXiv:2409.20549

(ref: Schouws22) Schouws, S., Stefanon, M., Bouwens, R., et al. 2022, ApJ, 928, 31

(ref: Schreiber18) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, A&A, 618, A85

(ref: Seille22) Seillé, L. M., Buat, V., Haddad, W., et al. 2022, A&A, 665, A137

(ref: Sommovigo22) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122

(ref: Sugahara21) Sugahara, Y., Inoue, A. K., Hashimoto, T., et al. 2021, ApJ, 923, 5

(ref: Tamura19) Tamura, Y., Mawatari, K., Hashimoto, T., et al. 2019, ApJ, 874, 27

(ref: Topping24) Topping, M. W., Stark, D. P., Endsley, R., et al. 2024, MNRAS, 529, 4087

(ref: Vijayan22) Vijayan, A. P., Wilkins, S. M., Lovell, C. C., et al. 2022, MNRAS, 511, 4999

(ref: Wang24) Wang, T.-M., Magnelli, B., Schinnerer, E., et al. 2024, A&A, 681, A110

(ref: Wang22) Wang, T.-M., Magnelli, B., Schinnerer, E., et al. 2022, A&A, 660, A142

(ref: Watson15) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327

(ref: Williams23) Williams, C. C., Tacchella, S., Maseda, M. V., et al. 2023, arXiv e-prints, arXiv:2301.09780

(ref: Witstok22) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751

(ref: Wolfire95) Wolfire, M. G., Hollenbach, D., McKee, C. F., Tielens, A. G. G. M., & Bakes, E. L. O. 1995, ApJ, 443, 152

[^1]:

[^2]: <https://dawn-cph.github.io/dja/>

[^3]: <http://cigale.lam.fr>

</paper>

Write the methods card for this paper.