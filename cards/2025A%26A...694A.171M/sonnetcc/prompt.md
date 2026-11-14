# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694A.171M\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...694A.171M",
 "title": "The host galaxies of radio-loud quasars at z &gt; 5 with ALMA",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Mazzucchelli, C.",
 "n_authors": 16,
 "arxiv_id": "2411.11952",
 "doi": "10.1051/0004-6361/202451290",
 "alma_projects_linked_by_archive": [
  "2019.1.00840.S"
 ]
}
```

Paper text:
<paper>
# The host galaxies of radio–loud quasars at $z>$5 with ALMA

The interaction between radio-jets and quasar host galaxies plays a paramount role in quasar/galaxy co-evolution. However, very little has been known so far about this interaction at very high$-z$. Here, we present new Atacama Large Millimeter/submillimeter Array (ALMA) observations in Band 7 and Band 3 of six radio-loud quasars’ host galaxies at $z > 5$. We recover \[C II\] 158 $\mu$m line and underlying dust continuum emission at $>2\sigma$ for five sources, while we obtain upper limits for the CO(6-5)  emission line and continuum for the remaining source. At the spatial resolution of our observations ($\sim$1.0$''$-1.4$''$), we do not recover perturbed/extended morphologies or kinematics, signatures of potential mergers. These galaxies already host large quantities of gas ($\sim10^{10}$ M$_{\odot}$), with \[C II\]  luminosities of $L_{\rm [C\,II]}\sim10^{8-9} L_{\odot}$ and \[C II\]-based star formation rates of $30-400 M_{\odot}$yr$^{-1}$. Building their radio/sub-mm spectral energy distributions (SEDs), we find that in at least four cases the 1mm continuum intensity arises from a combination of synchrotron and dust emission, with an initial estimation of synchrotron contribution at 300 GHz of $\gtrsim$10%.

Assuming the case in which the continuum emission is due to only cold dust as upper limit, we obtain infrared (IR) luminosities of $L_{\rm IR}\sim10^{11-12} L_{\odot}$. We compare the properties of the sources inspected here with a large collection of radio-quiet sources from the literature, as well as a sample of radio-loud quasars from previous studies, at comparable redshift.

We recover a potential mild decrease in $L_{\rm [C\,II]}$ for the radio-loud sources, which might be due to a suppression of the cool gas emission due to the radio-jets. We do not find any \[C II\] emitting companion galaxy candidate around the five radio-loud quasars observed in Band 7: given the depth of our dataset, this result is still consistent with that observed around radio-quiet quasars.

Further higher-spatial resolution observations, over a larger frequency range, of high$-z$ radio-loud quasars hosts will allow for a better understanding of the physics of such sources.

# Introduction

Quasars are among the most luminous, non-transient sources in the universe, and they can be observed at very large distances, hence at large look-back time. In the last two decades, the number of quasars known at high redshift ($z\gtrsim 5$, i.e. within one Gyr from the Big Bang) increased dramatically, with more than 400 sources discovered so far (e.g. (cite: fan2001),(cite: fan2006), (cite: banados2016), (cite: mazzucchelli2017b), (cite: matsuoka2018), (cite: reed2019), (cite: yang2019), (cite: yang2023), (cite: wenzl2021)) up to $z\sim7.5$ ((cite: banados2018a), (cite: yang2020), (cite: wangf2021); see (cite: fan2023) for a recent review). Very large supermassive black holes (SMBH) have been observed in their centers ($>10^{8} M_{\odot}$; e.g. (cite: willott2015), (cite: yang2021), (cite: farina2022), (cite: mazzucchelli2023)), surrounded by gas already enriched at (super-)solar metallicities (e.g. (cite: xu2018), (cite: onoue2020), (cite: lai2022)).

Observations of the stellar radiation from the host galaxies of high-redshift quasars have been challenging (e.g. (cite: decarli2012), (cite: mechtley2012), (cite: marshall2020)), due to the overwhelming radiation from the nuclear engine. Only very recently, observations with the *James Webb Space Telescope* (JWST) have uncovered such stellar emission in a few sources (e.g. (cite: ding2023), (cite: marshall2023), (cite: stone2023a), (cite: stone2024), (cite: yue2024), (cite: onoue2024)). Conversely, the properties of the host galaxies can be more easily explored with observations of the cool gas and dust emission from the interstellar medium (ISM), recovered in the (sub-)mm regime at high$-z$. In particular, the \[C II\] 158 $\mu$m emission line is the main coolant of the ISM, and can emit up to $3\%$ of the total galactic output (e.g. (cite: carilli2013)). Initial studies of a few, massive sources known at that time were pursed with the IRAM Plateau de Bure interferometer in the 2010s (e.g. (cite: maiolino2005), (cite: walter2009), (cite: wang2010)). Afterwards, the advent of the Atacama Large Millimeter/submillimeter Array (ALMA) paved the way for the exploration of large, statistically significant samples of quasars (e.g. (cite: wang2013), (cite: willott2015),(cite: willott2017), (cite: trakhtenbrot2017), (cite: decarli2018), (cite: venemans2018),(cite: venemans2020), (cite: izumi2018),(cite: izumi2019),(cite: izumi2021), (cite: nguyen2020), (cite: wangf2024)). So far, almost 80 quasars’ host galaxies have been observed in the (sub-)mm at $z>5$. The main results of these observations are: $a)$ quasars’ hosts already contain large reservoirs of gas and dust ($M_{\rm dust} > 10^{8} M_{\odot}$), and are very rapidly forming stars, with star formation rates (SFR) up to $>100-1000 M_{\odot}$ yr$^{-1}$. $b)$ the central SMBHs seem to be overmassive with respect to predictions from the SMBH-host galaxy mass relation observed in the local universe (e.g. (cite: venemans2016), (cite: pensabene2020), (cite: neeleman2021)), although this discrepancy seems less marked at lower luminosities/black hole masses (e.g. (cite: izumi2021)). $c)$ quasars’ hosts presents a variety of kinematics–e.g. rotation supported, dispersion dominated, or disturbed by close companions and/or mergers events (e.g. (cite: neeleman2021))–while observational studies provide mixed results for the presence of major molecular/cool gas outflows (e.g. (cite: decarli2018), (cite: bischetti2019), (cite: novak2020), (cite: meyer2022a)). $d)$ $\gtrsim 20 - 40 \%$ of these sources are surrounded by overdensities of galaxies on tens of kpcs scales (e.g.(cite: decarli2017),(cite: trakhtenbrot2017),(cite: nguyen2020), (cite: venemans2020)), which are extremely dust/gas-rich and severely obscured (e.g. (cite: mazzucchelli2019)). Despite the large sample of high-redshift quasars now observed in the sub-mm, almost all have been radio-quiet (RQ), due to the absence of dedicated ALMA follow-up of radio-loud quasars.

Indeed, a fraction of quasars ($\sim 10\%-20\%$, irrespective of redshift up to $z\gtrsim6$, i.e. within the Epoch of Reionization, EOR; e.g. (cite: banados2015b), (cite: liu2021); but see also (cite: sbarrato2022)) show strong radio emission, associated with powerful jets. These sources are defined as radio-loud (RL) quasars, i.e. with a radio-loudness parameter $R_{4400} = f_{\nu,{\rm 5GHz}} / f_{\rm 4400 \AA} > 10$ (cite: kellerman1989) or $R_{2500} = f_{\nu,{\rm 5GHz}} / f_{\rm 2500 \AA} > 10$ (cite: jiang2007), where $f_{\nu,{\rm 5GHz}}$, $f_{\rm 4400 \AA}$ and $f_{\rm 2500 \AA}$ are the flux densities at 5GHz, 4400 $\AA$ and 2500 $\AA$, respectively. These two quantities provide similar results for an un-obscured type-1 quasar; in this paper we will consider $R_{2500}$ as our radio-loudness parameter. Radio-jets are thought to be key elements in the host galaxy-SMBH (co-)evolution, via the so-called ‘radio-mode feedback’. Indeed, on one hand, jets can reduce star formation by sweeping away the gas reservoir (e.g. (cite: villarmartin2014)), while on the other hand they might enhance the formation of new stars, especially at high$-z$, via shock-induced gravitational collapse of gas clouds in an in-homogeneous and dense medium (e.g. (cite: silk2013), (cite: salome2015), (cite: fragile2017)). Moreover, RL quasars are routinely observed in rich galactic environments (e.g. (cite: wylezalek2013), (cite: venemans2007)), and are considered the best targets to discover overdensities of galaxies in the EOR (e.g. (cite: zheng2006), (cite: ajiki2006), (cite: bosman2020)). Currently, there are 50 RL quasars known at $z \gtrsim 5$ (see (cite: banados2021) and references there-in), out of which 5 are classified as blazars (i.e. with the relativistic jets aligned with our line of sight; e.g. (cite: belladitta2019), (cite: belladitta2020), (cite: banados2024a)); more than half of these sources were identified in the last two years (e.g.  (cite: gloudemans2022), (cite: banados2023), (cite: belladitta2023)). Very few of their host galaxies have been studied so far. (cite: rojas2021) observed the $z\sim5.8$ RL quasar PSO352-15 with a collection of (sub-)mm and radio data, obtained with ALMA, the NOrthern Extended Millimeter Array (NOEMA) and the upgraded Giant Metrewave Radio Telescope (uGMRT). They found that the total sub-mm emission can not be uniquely explained by dust emission, and that synchrotron radiation contributes down to these frequencies. (cite: khusanova2022) observed four other $z>6$ RL quasars in the Northern Hemisphere with NOEMA, targeting their dust and \[C II\] emission lines. While the host of the highest reshift ($z\sim6.8$) RL quasar known so far is not detected, some of the remaining hosts show asymmetric line profiles–indicative of a potential merger or strong outflow–and SFRs comparable to RQ quasars hosts. Very recently, (cite: banados2024a) discovered a blazar at $z\sim7$, and (cite: banados2024b) reported NOEMA (2021) and ALMA (2022) observations of this source. They recovered a large ($>30$%) flux variation within only 10 months, and they estimated a synchrotron contribution to the observed $\sim$230 GHz flux as high as $\sim$80%.

Here, we present new ALMA observations of the dust continuum and \[C II\] or CO(6-5) emission lines of the host galaxies of six $5<z<6$ RL quasars, and one RQ source[^2]. This paper is organized as follows: in Section [2](#sec:sampobs) we report our sample and observations; in Section [3](#sec:results) we describe our methods to derive continuum and emission lines measurements; in Section [4](#sec:analysis) we report our redshift estimates, present radio-mm Spectral Energy Distribution (SEDs) of our RL quasars, calculate gas and \[C II\] luminosities, SFRs, dust, dynamical and molecular gas masses, and place them in the context of RQ quasars host galaxies’ observations recovered from the literature. We also compare the infrared (host galaxies) and UV (nuclear emission) properties, and search for the presence of further line emitting galaxies in their fields. Finally, we discuss our results in Section [5](#sec:disc) and present our conclusions in Section [6](#sec:conc).

Throughout this work, we use a cosmology, with $H_{0} = 67.8$ km s${-1}$ Mpc$^{-1}$, $\Omega_{M} = 0.3$ and $\Omega_{\Lambda} = 0.7$. The age of the universe at $z=5.5$ is 1.04 Gyr, and the transverse physical scale is 6.1 kpc per arcsec. All magnitudes are reported in the AB system.

# Sample and Observations

For this study, we focused on high-redshift ($z>5$) RL quasars, observable from ALMA (Declination $<20$ deg). At the time of the submission of the proposal (April 2018), the source J2053+0047 was tentatively classified as RL by (cite: banados2015a), based on data from the Faint Images of the Radio Sky at Twenty cm survey (FIRST, (cite: becker1995)), with a radio-loudness parameter of $R_{4400}= 44.1 \pm 18.7$. However, (cite: liu2021) showed it to be RQ, based on deeper follow-up data with the Karl G. Janski Very Large Array (VLA), with $R_{4400} < 9.7$. We still provide our measurements and results for this quasar in the paper, but label it as RQ. We list in Table [\[tab:sample1\]](#tab:sample1) the general properties of our sample, i.e. coordinates, literature redshifts, magnitude at rest-frame 1450 Å, and radio-loudness parameter.

ALMA Cycle 7 observations (program ID: 2019.1.00840.S, PI: Mazzucchelli) were obtained between October and December 2019. For 5 sources, we targeted the \[C II\] emission line, falling in Band 7 at 5$<\,z\,<$5.8. The redshift of two sources ($z\sim5.9$; J2228+0110 and J2053+0047) places their \[C II\] line close to the gap between Band 6 and 7, hence, in these cases, we targeted the CO(6-5) emission line, recovered in Band 3. We chose a compact configuration C(43-2) to avoid flux losses, with 44 antennas used. We centered two spectral windows, slightly overlapping, on the expected observed frequency of the \[C II\] or CO(6-5) emission line. The remaining two spectral windows were placed to recover the continuum emission at slightly different frequencies. A bandwidth of 1.875 GHz was covered per spectral window. The data were reduced with CASA (McMullin et al. 2007) pipeline for ALMA (version 6.2.1-7), with standard configuration. The cubes were imaged using the CASA task `tclean` with weighting and robust parameters set to ’briggs’ and ’2’, respectively, to maximize the signal-to-noise ratio (SNR), following similar works from the literature (cite: decarli2018). We produce cubes with a spectral resolution width of 30 km s$^{-1}.$ The typical rms noise per 30 km s$^{-1}$ channel is $\sim$0.50 mJy beam$^{-1}$, with a typical synthesized beam size of 1.35$''$$\times$1.10$''$.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | R.A. | Decl. | $z$ | $z$ method | $M_{1450}$ | R$_{2500}$ | Reference |
|  | (J2000) | (J2000) |  |  |  |  | Disc / $z$ / $M_{1450}$ |
| J0131-0321$^{\dagger}$ | 01:31:27.3400 | –03:21:00.180 | 5.1904 $\pm$ 0.0003 | Mg II | $-$29.11 | 116 $\pm$ 9 | 1 / 2 / 1 |
| PSO055-00 | 03:41:41.8580 | –00:48:12.740 | 5.68 $\pm$ 0.05 | template | $-$26.37 | 83 $\pm$ 9 | 3 / 3 / 4 |
| PSO135+16 | 09:01:32.6530 | 16:15:06.830 | 5.63 $\pm$ 0.05 | template | $-$25.91 | 177 $\pm$ 18 | 3 / 3 / 4 |
| J1034+2033 | 10:34:18.6500 | 20:33:00.220 | 5.01 $\pm$ 0.02 | z_VI$^{\ddagger}$ | $-$27.76 | 47 $\pm$ 4 | 5 / 6 / 7 |
| J2228+0110 | 22:28:43.5350 | 01:10:32.200 | 5.903 $\pm$ 0.0002 | $\mathrm{Ly}\ensuremath{\alpha}$ | $-$24.50 | 71 $\pm$ 15 | 8 / 9 / 8 |
| PSO352–15 | 23:29:36.8362 | –15:20:14.460 | 5.84 $\pm$ 0.02 | template | $-$25.60 | 1470 $\pm$ 110 | 10 / 10 / 10 |
| J2053+0047$^{\star}$ | 20:53:21.766 | +00:47:06.80 | 5.92 $\pm$ 0.03 | $\mathrm{Ly}\ensuremath{\alpha}$ | $-$25.30 | $<$9.7$^{\mp}$ | 11 / 11 / 11 |

Table notes: The radio-loudness parameter is from (cite: banados2021) ((cite: banados2021); and references therein), with the exception of POS352-15, where $R_{2500}$ is from (cite: rojas2021). Further references are: 1) (cite: yi2014); 2) this work; 3) (cite: banados2015a); 4) (cite: banados2016); 5) (cite: schneider2010) ; 6) (cite: paris2018) ; 7) (cite: banados2021); 8) (cite: zeimann2011); 9) (cite: roche2014); 10) (cite: banados2018c); 11) (cite: jiang2009). $^{\dagger}$Classified as blazar (see Section [2](#sec:sampobs) for details). $^{\ddagger}$ See (cite: paris2018) for a discussion on different redshift estimates. $^{\star}$ We note J2053+0047 was reclassified as a RQ quasar with deeper radio VLA observations (see Section [2](#sec:sampobs) for details). $^{\mp}$ Limit on radio-loudness parameter is obtained from (cite: liu2021)

Below we report notes on individual objects in the sample and further details on their observations.

## J0131–0321

(cite: yi2014) discovered this very luminous source ($i$ = 18.47) by cross-matching the Sloan Digital Sky Survey (SDSS) Data Release 7 (cite: schneider2010) and the Wide-Field Infrared Survey Explorer (WISE; (cite: wright2010)) catalogs, with further confirmation via spectroscopic observations at the Lijiang 2.4m telescope, and with MaGE and FIRE at the Magellan telescope. By fitting the Mg II  emission line and underlying continuum emission, the authors estimated a redshift of $z=5.18 \pm 0.02$, a large black hole mass of 2.7$\times$10$^{9} M_{\odot}$ and a bolometric luminosity of $L_{\rm bol} \sim 10^{48}$ erg s$^{-1}$, with a resulting super-Eddington rate of $\sim$3.14. Given a radio flux density of 33 mJy at 1.4 GHz, this source presented a large radio-loudness parameter of $\sim$100. (cite: ghisellini2015) highlighted the potential blazar nature of J0131–0321 with $Swift$-XRT X-ray observations. Fitting its SED with an accretion disk+torus+jet model, they estimated a viewing angle of 3-5 deg, and a black hole mass of $\sim 10^{10} M_{\odot}$ (with a factor of $\gtrsim$2 of systematic uncertainty), allowing for a sub-Eddington accretion rate of $\sim$0.8. High-resolution Very Large Baseline Interferometer (VLBI) observations with the European VLBI Network (EVN) at 1.7 GHz, obtained by (cite: gabanyi2015), showed a compact source with high brightness temperature ($T_{\rm B} < 10^{11}$ K) and moderate Doppler boosting factor ($\gtrsim$6). Moreover, they noted a strong radio flux variability with respect to the FIRST survey, supporting the blazar hypothesis. Finally, this source was observed with the uGMRT at 323 MHz, but radio frequency interference contaminated the data, preventing any measurement (cite: shao2020). Nevertheless, using observations at 150 MHz from the TIFR GMRT Sky Survey (TGSS; (cite: itema2017)), the authors could estimate a radio power law slope of $\alpha_{\nu} \sim 0.3$ (with $S_{\nu} \propto \nu^{\alpha}$).

J0131–0321 was observed with ALMA on 2019 Nov 28, with a total on-source exposure time of 726 s. The synthesized beam size is 1.06$''$$\times$ 0.94$''$, with a position angle (PA) of 82 deg. The rms noise on 30 km s$^{-1}$ channels is 0.49 mJy beam$^{-1}$.

## PSO055–00

This quasar was selected by mining the Pan-STARRS and FIRST surveys, and confirmed by spectroscopic follow-up with Palomar/DBSP and VLT/FORS2 (cite: banados2015a). A reduced $\chi^{2}$ fit of the observed spectrum to a composite high$-z$ quasar template yielded a redshift of $z=5.68 \pm 0.05$. PSO055–00 presents a radio flux density at 1.4GHz of $2.14 \pm 0.14$ mJy, as obtained from the FIRST Survey, and a radio-loudness parameter $R_{2500} = 83 \pm 9$ (cite: banados2021).

Our ALMA observations of this quasar were obtained on 2019 Dec 17 with a total on-source exposure time of 816 s. The measured rms noise is 0.54 mJy beam$^{-1}$ on 30 km s$^{-1}$ channels, while the beam size is 1.39$''$ $\times$ 1.05$''$, with PA=81 deg.

## PSO135+16

PSO135+16 was selected as a high$-z$ quasar candidate in a similar fashion as PSO055–00. It was then confirmed spectroscopically with LBT/MODS and VLT/FORS2 (cite: banados2015a). It is located at $z = 5.68 \pm 0.05$, as measured by fitting its spectrum to a reference template. Its radio-loudness parameter is $R_{2500} = 177 \pm 18$, with a radio flux density of $f_{\rm 1.4GHz} = 3.04\pm0.15$ mJy, as obtained from the FIRST survey.

ALMA observed PSO135+16 on 2019 Dec 02 with exposure time of 1058 s. The beam size is of 1.39$''$ $\times$ 1.21$''$, PA=$-$30 deg, and the rms noise is of 0.50 mJy beam$^{-1}$ on 30 km s$^{-1}$ channels.

## J1034+2033

This bright ($z=19.79$) source was firstly presented as part of the SDSS-DR7 quasar catalog (cite: schneider2010). It is located at redshift $z=5.01$[^3] (cite: paris2018). J1034+2033 has a radio flux density $f_{\rm 1.4GHz} = 3.96 \pm 0.15$ mJy, from the FIRST survey, and a radio-loudness parameter $R_{2500} = 47 \pm 4$. (cite: shao2020) observed J1034+2033 with the uGMRT, measuring a flux density of 2.97$\pm$0.19 mJy at 323 MHz, and fitting a radio spectral slope of $\alpha_{\nu} \sim 0.18$.

Our ALMA data for this quasar were obtained on 2019 Dec 04, with a rms noise of 0.78 mJy beam$^{-1}$ on 30 km s$^{-1}$ channels, and a beam size of 1.36$''$ $\times$ 1.04$''$, PA=$-$33 deg. The total exposure time was 1058s.

## J2228+0110

(cite: zeimann2011) selected J2228+0110 as a quasar candidate by cross-matching the Stripe82 SDSS and Stripe 82 VLA surveys. Its high$-z$ quasar nature was confirmed by observations with the Keck/LRIS spectrograph. J2228+0110 is optically faint (with an observed magnitude $z=22.3$), with a radio flux density of $f_{\rm 1.4GHz} = 0.31 \pm 0.06$ mJy and a radio-loudness parameter of $R_{2500} \sim 70$. A tentative detection of a Lyman Alpha Halo (LAH) around this quasar was firstly presented by (cite: roche2014), using GTC-OSIRIS long-slit spectroscopy. Deep (11h) MUSE observations confirmed the presence of an extended ($\sim$6.0$''$, i.e. $\sim$ 30 pkpc at $z\sim6$) and bright ($\sim 2 \times 10^{-16}$ erg s$^{-1}$ cm$^{-2}$) LAH towards the south-east direction ((cite: drake2019), (cite: farina2019)).

ALMA targeted J2228+0110 on 2019 Oct 12, with an exposure time of 3810 s. The measured rms noise is 0.32 mJy beam$^{-1}$ on 30 km s$^{-1}$ channels, and the beam size is 1.44$''$ $\times$ 1.28$''$, PA=$-$78 deg.

## PSO352–15

(cite: banados2018c) selected PSO352–15 as a quasar candidate from the Pan-STARRS survey, and confirmed it with spectroscopic observations with Magellan/LDSS3. This quasar was initially located at $z = 5.84$, via template fit, and is optically faint ($z=21.22$). With very bright radio flux density measurements from available radio surveys and dedicated VLA follow-up, it is one of the radio loudest sources at $z>5$. Further high-resolution radio observations with the Very Long Baseline Array (VLBA) resolved the source into different components with a spatial extension of $\sim$1.3 kpc, and a morphology consistent with a one-sided jet or a compact symmetric object (cite: momjian2018). (cite: rojas2021) presented a collection of multi-wavelength observations for this source, included ALMA data collected as part of this program. They re-calculated the radio-loudness parameter as $R_{2500} \sim 1350$, and showed evidence for a break in the radio spectral distribution. Intriguingly, they found signs for synchrotron emission contribution down to the rest-frame infrared regime (see also Section [4.3](#sec:sed) below). We still report PSO352-15 here as part of the RL sample and we re-calculate its properties for consistency (see Section [3](#sec:results)).

This object was observed on 2019 Nov 28, with an exposure time of 756 s. We measured a rms noise of 0.58 mJy beam$^{-1}$, and a beam size of 1.27$''$ $\times$ 1.00$''$, PA=86 deg.

## J2053+0047

This faint ($z = 21.41$) quasar at redshift $z = 5.92$ was selected by (cite: jiang2009) using SDSS survey data. (cite: banados2015a) identified a 3$\sigma$ detection in the FIRST survey data, with a radio flux density of $f_{\rm 1.4GHz} = 434 \pm 143 \mu$Jy, obtaining a radio-loudness parameter of $\sim$44, signaling this as a RL quasar. Deeper observations with the VLA provided new flux density limits of $f_{\rm 1.4GHz} \sim 13 \mu$Jy, yielding an upper limit on the radio-loudness parameter as low as $<$9.7 (cite: liu2021). Hence, J2053+0047 has been currently reclassified as a RQ source. We still report the data collected for this source here for completeness.

Our ALMA observations of this source was obtained on 2019 Oct 13. The total exposure time was 2570 s, and we measure a beam size of 1.56$''$ $\times$ 1.20$''$, PA=65 deg, and a rms noise of 0.23 mJy beam$^{-1}$.

# Results

We describe here our steps to recover the properties of the \[C II\], CO(6-5)  emission lines, and the underlying dust continuum.

## \[CII\] line measurements

We target the \[C II\] emission line in five quasars: J0131-0321, PSO055-00, PSO135+16, J1034+2033 and PSO352-15. In order to properly account for potentially extended sources, we extract our one dimensional spectrum for each source in an aperture centered on the quasar position (e.g. (cite: novak2019), (cite: rojas2021)). We determine the best aperture by extracting the flux of the quasars in concentric apertures from 0.1$''$ up to 3.0$''$, and choosing the radius at which the flux encounters a plateau. Once the best aperture is found, we extract the one dimensional spectra, and fit them with a flat continuum and a Gaussian line. We detect the \[C II\] emission line in all sources. The emission line for the quasar PSO055-00 is found at the edge of the bandwidth: this is due to the large uncertainty of the literature redshift derived from template fit of the rest-frame UV spectrum. Therefore, caution should be taken when considering its \[C II\] emission line value, and the derived quantities. We report the 1D spectra in Figure [1](#fig:1dciiline), and the values of the fit and apertures radii in Table [\[tab:1dcii\]](#tab:1dcii).

We create continuum-subtracted \[C II\] emission line cubes in the following way. We choose the line spectral windows centered on the frequency peak of the Gaussian fit and width corresponding to $\pm$1.4$\sigma$; this recovers $\sim 83\%$ of the total line flux and maximizes the SNR, in case of a perfectly Gaussian line profile (e.g. (cite: decarli2018), (cite: novak2020), appendix A). The continuum subtraction is done in the *uv* space using the CASA task *uvcontsub*. We then re-image the continuum subtracted cubes with `tclean`, with robust=2. We report the \[C II\] continuum-subtracted moment-0 maps in Figure [2](#fig:1dciimap). We fit the continuum-subtracted \[C II\] map with a 2D Gaussian function within CASA, selecting a small rectangular region around the source. We report the flux values and sizes of the sources in our sample in Table [\[tab:2dfit\]](#tab:2dfit). We note that the maps are built considering only $83\%$ of the total line flux, therefore the 2D flux need to be corrected by a factor of $\sim$1.20 (e.g. (cite: decarli2018)).

We make a first order assessment of the kinematics of these sources (see Appendix A). However, due to the low SNR and the limited spatial resolution of the maps, we are not able to draw stronger conclusions on their kinematics, for which additional deeper, and higher resolution observations are needed. It is worth noting that our results for the quasar PSO352-15 are consistent with those presented in (cite: rojas2021), and we direct the reader to this work for further insights in the morphological study of this source.

In the remainder of the paper, we use the \[C II\] emission line flux obtained by the 2D Gaussian fit, corrected by a factor of 1.20.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $\nu_{\rm obs}$ (\[C II\]) | $z$ (\[C II\]) | FWHM (\[C II\]) | $F_{\rm line}$ (\[C II\]) | $F_{\rm cont}$ | $r_{\rm aper}$ |
|  | \[GHz\] |  | \[km s$^{-1}$\] | \[Jy km s$^{-1}$\] | \[mJy\] | \[$''$\] |
| J0131-0321 | 306.895$\pm$0.03 | 5.1928$\pm$0.0006 | 170$\pm$70 | 0.35$\pm$0.20 | 2.10$\pm$0.10 | 1.4 |
| PSO055-00$^{\star}$ | 283.889$\pm$0.02 | 5.7183$\pm$0.0005 | 150$\pm$60 | 0.55$\pm$0.30 | 0.46$\pm$0.20 | 2.3 |
| PSO135+16 | 282.889$\pm$0.008 | 5.7183$\pm$0.002 | 340$\pm$29 | 3.30$\pm$0.30 | 4.00$\pm$0.10 | 1.6 |
| J1034+2033 | 317.172$\pm$0.03 | 4.9921$\pm$0.0005 | 190$\pm$80 | 0.47$\pm$0.30 | 0.064$\pm$0.10 | 1.3 |
| PSO352–15 | 278.202$\pm$0.03 | 5.8315$\pm$0.0007 | 390$\pm$90 | 1.20$\pm$0.040 | 0.18$\pm$0.20 | 1.7 |

Table notes: The spectra were extracted from different apertures ($r_{\rm aper}$, see Section [3.1](#sec:ciimeasure)). $^{\star}$ We note that PSO055-00’s line emission is recovered at the edge of the bandwith. Therefore, caution should be taken when considering its \[C II\] emission line value and all derived quantities.

![](fig_1dspectrum_aper_202406.pdf)

![](fig_ciimap_aper_202408.pdf)

## CO(6-5) line measurements

Observations in Band 3, targeting the CO(6-5) emission lines, were obtained for two quasars: J2228+0110 and J2053+0047. No clear emission is seen in the reduced cubes. We extract the one dimensional spectrum from the central pixel, i.e. at the nominal position of the quasar. No line nor continuum emission were detected.

We can place upper limits to the continuum emission at 2$\sigma$ by considering the mean rms noise on the extracted 1D spectrum. We also estimate upper limits on the emission line flux at 3$\sigma$, and considering a typical line width of 300 km s$^{-1}$ (e.g. (cite: decarli2022)). We show in Figure [3](#fig:1dco65line) the extracted one dimensional spectra, and in Table [1](#tab:co65) the continuum and CO(6-5)  emission line flux limits.

![](fig_1dspectrum_co65_202406.pdf)

| Name                                            | J2228+0110 | J2053+0047 |
|:------------------------------------------------|:----------:|:----------:|
| $F_{\rm CO(6-5)}$ \[Jy km s$^{-1}$\]            |  $<$0.68   |  $<$0.53   |
| $F_{\rm cont,690  GHz}$ \[mJy\]                 |  $<$0.64   |  $<$0.47   |
| $L_{\rm CO(6-5)}$ \[$10^{8}\, L_{\odot}$\]      |   $<$2.4   |   $<$1.9   |
| $L^{'}_{\rm CO(6-5)}$ \[$10^{10}\, L_{\odot}$\] |   $<$2.2   |   $<$1.8   |
| $L_{\rm FIR}$ \[$10^{12}\, L_{\odot}$\]         |   $<$46    |   $<$34    |
| $L_{\rm TIR}$ \[$10^{12}\, L_{\odot}$\]         |   $<$67    |   $<$50    |

: Limits on the continuum and CO(6-5)  emission line fluxes (see Section [3.2](#sec:co65measure)), and derived limits on the line and infrared luminosities (see Section [4.5](#sec:co65analysis)).

## Continuum measurements

We recover the continuum emission at $\nu_{\rm rf} \sim 1900$ GHz and $\nu_{\rm rf} \sim 1970$ GHz in Band 7 in the lower and upper side bands, respectively. In the case of Band 3, we target the continuum at $\nu_{\rm rf} \sim 690$ GHz (lower) and $\nu_{\rm rf} \sim 620$ GHz (upper side band).

We estimate the continuum properties for the sources observed in Band 7 as follows. We create pure continuum maps for the lower and upper side bands by collapsing the frequency channels not incorporating the \[C II\] emission line (see Section [3.1](#sec:ciimeasure)). In both cases the continuum emission is recovered in all the sources. We model each continuum emission from the maps with a 2D Gaussian function, using CASA. The measured sizes are consistent with the beam size. We produce similar continuum maps for the two sources observed in Band 3, but no emission is recovered in either case.

We report the continuum flux density and size values for observed Band 7 emission in Table [\[tab:2dfit\]](#tab:2dfit), and limits on non detections in Band 3 in Table [1](#tab:co65). The continuum maps are shown in Figures [4](#fig:contmap) and [5](#fig:cont23map). For the remainder of the paper, to calculate the corresponding IR quantities (see Section [4](#sec:analysis)), we use the continuum emission flux obtained at 1900 GHz from the 2D Gaussian fit ($F_{\rm cont, 1900GHz}$), and reported in Table [\[tab:2dfit\]](#tab:2dfit).

![](fig_contmap_aper_202408.pdf)

![](fig_contmap23_202408.pdf)

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | Size$\rm _{[C\,II]}$ | Size$_{\rm 1900 GHz}$ | Size$_{\rm 1970 GHz}$ | $F_{\rm [C\,II]}$ | $F_{\rm [C\,II],corr}$ | $F_{\rm cont, 1900 GHz}$ | $F_{\rm cont, 1970 GHz}$ |
|  | \[$^{\prime \prime}$\] | \[$^{\prime \prime}$\] | \[$^{\prime \prime}$\] | \[Jy km s$^{-1}$\] | \[Jy km s$^{-1}$\] | \[mJy\] | \[mJy\] |
| J0131$-$0321 | 1.660 $\times$ 1.140 | 1.120 $\times$ 0.982 | 1.205 $\times$ 1.035 | 0.398$\pm$0.079 | 0.480$\pm$0.095 | 2.130$\pm$0.056 | 2.176$\pm$0.090 |
| PSO055$-$00$^{\star}$ | 1.314 $\times$ 1.148 | 1.713 $\times$ 1.300 | 1.566 $\times$ 0.908 | 0.281$\pm$0.023 | 0.339$\pm$0.028 | 0.586$\pm$0.027 | 0.386$\pm$0.043 |
| PSO135+16 | 1.352 $\times$ 1.261 | 1.352 $\times$ 1.245 | 1.295 $\times$ 1.179 | 2.504$\pm$0.092 | 3.017$\pm$0.111 | 4.42$\pm$0.16 | 4.510$\pm$0.15 |
| J1034+2033 | 1.560 $\times$ 1.120 | 1.044 $\times$ 0.867 | 1.52 $\times$ 1.12 | 0.345$\pm$0.034 | 0.416$\pm$0.041 | 0.168$\pm$0.030 | 0.231$\pm$0.045 |
| PSO352–15 | 1.614 $\times$ 1.184 | 1.280 $\times$ 0.897 | 1.91 $\times$ 1.30 | 0.695$\pm$0.093 | 0.837$\pm$0.112 | 0.300$\pm$0.031 | 0.581$\pm$0.098 |

Table notes: The corrected flux is obtained by considering a 1.20 factor (see Section [3.1](#sec:ciimeasure)). The (not deconvolved) size measurements provided here are consistent with the beam sizes. $^{\star}$ We note that PSO055-00’s line emission is recovered at the edge of the bandwith. Therefore, caution should be taken when considering its \[C II\] emission line value and all derived quantities.

# Analysis

We report here gas and dust properties derived from the measurements of our RL quasars sample. We also compare them with those of RQ quasars’ hosts at similar redshift taken from the literature.

## Literature Sample

In this work we compare the properties of RL quasars host galaxies with those derived from the literature.

For the RQ sample, we consider sources from the following studies, which targeted their dust continuum and \[C II\] emission line: (cite: walter2009), (cite: wang2013) (cite: wang2016), (cite: willott2013b), (cite: willott2015), (cite: willott2017), (cite: mazzucchelli2017b), (cite: trakhtenbrot2017), (cite: decarli2018), (cite: izumi2018), (cite: izumi2019), (cite: izumi2021), (cite: venemans2020), (cite: nguyen2020), (cite: yang2020), (cite: eilers2020a), (cite: eilers2021). The total number of RQ sources is 76.

We also consider six additional RL quasars’ hosts galaxies properties from the literature. Four of these come from (cite: khusanova2022): J0309+2717 ($z=6.115$), J1427+3312 ($z=6.115$), J1429+5447 ($z=6.1845$) and PSO172+18 (a potentially very young radio source at $z=6.823$, (cite: momjian2021), for which only upper limits in both continuum and \[C II\] emission lines have been obtained).

The fifth source is J2318-3113 ($z=6.44$), which was re-classified as a RL quasar by (cite: ighina2021). Using new 888 MHz radio observations acquired with the Rapid ASKAP Continuum Survey (RACS; (cite: mcconnell2020), (cite: hale2021)) they obtained a new radio loudness parameter of R$_{4400} \sim 70$ and observed a potential flux density variability of a factor of $\sim$2 in one year. In a recent study, (cite: ighina2024) presented new, multi-wavelength (radio, optical/NIR, X-ray) data, which reinforced the scenario of a young radio source with a black hole mass of $\sim8 \times 10^{8}$ M$_{\odot}$. Here, we adopt $R_{2500} = 152$ and a spectral index of $\alpha=0.54$ reported by (cite: ighina2021). J2318-3113 has been previously observed with ALMA by (cite: decarli2018) and (cite: venemans2020). We here include J2318-3113 in our RL quasar sample, utilizing the measurements provided by (cite: venemans2020). We finally include a very recently discovered blazar at $z=6.9964$, J0410-0139 (cite: banados2024a). We consider here the continuum and \[C II\] emission line fluxes from ALMA Band 6 observations obtained in August 2022 (cite: banados2024b). For all the sources from the literature, we re-derive IR and \[C II\] luminosities, SFRs, and dust masses consistently with the objects presented in this work, and as outlined below in Section [4.4](#sec:analysis_lum).

## Redshift estimations

We estimate the redshifts of the quasars in our sample from the peak of the \[C II\]  emission line, and we report these values in Table [\[tab:1dcii\]](#tab:1dcii).

Several studies (e.g. (cite: venemans2017c), (cite: decarli2018), (cite: meyer2019), (cite: schindler2020)) highlight a systematic, large blueshift of the rest-frame UV emission lines (e.g.  C IV, Mg II) with respect to lines arising from the ISM in the host galaxy, considered the rest-frame of the system. Moreover the $\mathrm{Ly}\ensuremath{\alpha}$ emission line at high-redshift is known to provide a poor estimation of the quasars’ redshift, due to effects introduced by the absorption of the intergalactic medium (IGM; e.g.  (cite: banados2016)). Here, we find that the blueshift for J0131-0321, the only quasar whose redshift was known from the Mg II emission line, is very small, i.e. $\Delta v_{\rm Mg\,II- [C\,II]} = -127$ km s$^{-1}$. This is consistent with the median difference of  $\Delta v_{\rm Mg\,II- [C\,II]}$ observed in the literature for RQ quasars ($\sim -367/ -390$ km s$^{-1}$ at $z\sim5/6$, (cite: nguyen2020) and (cite: schindler2020)). However, the blueshift relative to our \[C II\]  redshifts for the cases of literature redshifts based on observations of the $\mathrm{Ly}\ensuremath{\alpha}$ emission line or from template fitting are much larger, with a maximum value of $-$2060 km s$^{-1}$ (for PSO055-00, which is indeed recovered at the edge of the bandwidth). We measure a mean, median and standard deviation for  $\Delta v_{\rm \mathrm{Ly}\ensuremath{\alpha}/ temp - [C\,II]}$ of $-1269$, $-770$, and $2271$ km s$^{-1}$, respectively.

## Radio and (sub-)mm Spectral Energy Distribution

We place our ALMA measurements of the continuum emission in the context of the spectral energy distribution (SED) of the RL quasars studied here. We utilize radio measurements from the literature ((cite: zeimann2011), (cite: banados2018c), (cite: shao2020), (cite: shao2022), (cite: rojas2021), (cite: krezinger2024)) obtained either via dedicated follow-up with VLA, VLBI, uGMRT and/or NOEMA, or from the FIRST and TGSS surveys. In addition, we obtained new measurements from RACS and the ASKAP First Large Absorption Survey in HI (ASKAP-FLASH; (cite: allison2022)). In practice, we downloaded from CASDA[^4] the available images of the quasars PSO055-00, PSO135+16 and J1034+2033, and we fitted a Gaussian profile within CASA to obtain the integrated fluxes at observed frequencies 0.89 GHz and 1.37 GHz (RACS) and at 0.86 GHz (FLASH). We note that the various reported observations were obtained in different times, within days to several years from each other, hence the radio intrinsic SED shape might be altered by variability effects. The resulting SEDs are shown in Figure [6](#fig:sed).

In general, quasars’ SEDs at radio frequencies are dominated by synchrotron emission, which can be modelled with a power law ($S_{\nu} \propto \nu^{\alpha}$). In the case of PSO352-15, a broken power-law with $\alpha^{0.215}_{3} = -0.88 \pm 0.08$ (measured between observed frequencies 0.215 and 3 GHz) and $\alpha^{3}_{100} = -1.26 \pm 0.03$ (measured between observed frequencies 3 and 100 GHz) better reproduces the data; for a detailed discussion on this source, we direct the reader to (cite: rojas2021). We highlight that extrapolating the sole synchrotron emission, one would obtain at the observed ALMA frequency a flux of $\sim$0.027 mJy (see Figure [6](#fig:sed)). Consequently, the estimated synchrotron contribution for this source is of $\sim$9%, as discussed in (cite: rojas2021).

J0131-0321 and J1034+2033 were extensively observed with the VLA and uGMRT by (cite: shao2020) and ((cite: shao2022)). A turn-over of the radio spectra was recovered, around an observed (rest-frame) frequency of $\sim$2 ($\sim$10) GHz in J0131-0321, and of $\sim$4 ($\sim$20) GHz in J1034+2033. Such radio spectral shapes are typically observed in GHz-peaked sources (GPS), or high-frequencies peakers (HFP). (cite: shao2022) shows that a model of free-free absorption by an external, in-homogeneous medium can best reproduce both cases. We report in Figure [6](#fig:sed) the corresponding, approximate power-law emission at frequencies higher than the turn-over, with the slopes indicated by (cite: shao2022), which we can extrapolate to the frequencies of our dust emission model. We note that, in the case of J0131-0321, virtually most of the emission we recover from our ALMA continuum observations at observed 300 GHz could be due to synchrotron emission. For J1034+2033, the recovered intensity measured with ALMA (0.168 mJy; see Table [\[tab:2dfit\]](#tab:2dfit)) is higher than what is expected by the sole synchrotron emission extrapolation ($\sim$0.065 mJy; see Figure [6](#fig:sed)). In both cases, a mix of dust+synchrotron radiation could be responsible for the continuum emission observed with ALMA. In particular, extrapolating the radio power-law, we can obtain a first order estimate of synchrotron contribution at $\sim$300 GHz of $\sim$40% and $\sim$100% for J1034+2033 and J0131-0321, respectively.

J2228+0110 is the weakest radio emitter in this sample. It was observed with VLA and uGMRT by (cite: shao2020), and ((cite: shao2022)): in contrast to J0131-0321 and J1034+2033, no clear radio turn-over was observed, although the upper limits recovered with the uGMRT could provide a hint of a change in the spectrum. Not considering this upper limit, the radio emission could be modelled, between observed frequencies 323 MHz and 1 GHz, with a relatively flat power law, with $\alpha=-0.39 \pm 0.17$. This object was also not detected in our ALMA Band 3 observations, hence we only have upper limits for its continuum emission, which we show with gray shades in Figure [6](#fig:sed).

PSO055-00 and PSO135+16 were observed only within 0.8-1.7 GHz, hence a model of their radio emission can not be meaningfully fitted; we show in Figure [6](#fig:sed) an indicative power law emission with slope $\alpha=-0.67$, used in (cite: banados2021) to derive their radio-loudnesss parameters, and calculated as the median slope of the radio emission in $z>5$ quasars. In both cases, this slope is broadly consistent with the radio measurements, and we do not observe strong variability. Our ALMA measurements (0.586 mJy and 4.42 mJy for PSO055-00 and PSO135+16, respectively; see Table [\[tab:2dfit\]](#tab:2dfit)) are approximately one order of magnitude higher than the flux density obtained when extrapolating the synchrotron emission ($\sim$0.057 mJy and $\sim$0.102 mJy for PSO055-00 and PSO135+16, respectively; see Figure [6](#fig:sed)). In this case, the estimated synchrotron contribution at $\sim$300 GHz are $\sim$9% and $\sim$2% for PSO055-00 and PSO135+16, respectively.

All these lines of evidence show the variety of the SEDs of high$-z$ RL quasars, and highlights how observations at rest frame $\sim$1mm, in case of RL quasars, could be the result of thermal and non-thermal emission. Therefore, extreme caution should be used when deriving SFR, dust/gas masses etc.  from continuum measurements at these wavelengths. In order to still provide valuable estimates, discussions and comparisons with the literature, while considering the above described limitations with the currently available datasets, we derive such quantities in two ways. We firstly consider the total ALMA recovered continuum data as purely produced by dust, which will provide upper limits to IR luminosities, SFR and dust/gas masses. Secondly, we derive these measurements subtracting the synchrotron values as extrapolated at $\sim$1mm from the radio power-law functions (as described above) to the total observed ALMA continuum flux. Considering that the radio power-law functions are expected to bend downward towards higher frequencies, due to the interaction between high-energy particles in the jets and the surrounding medium (e.g. (cite: jaffe1973)), decreasing the synchrotron contribution, the IR-related quantities derived in this way can be considered as lower limits. The intrinsic SFR, IR luminosities and gas/dust masses should then be found within the two reported values. Given that virtually $\sim$100% of the $\sim$300 GHz flux density of J0131-0321 could be due to synchrotron, we do not derive a second measure for this source, but consider the firstly derived IR values as pure upper limits. Also, we do not derive a second set of values for J2228+110, as only upper limits are recovered from our ALMA data.

Further observations at intermediate frequencies are needed to properly model these RL quasars SED, and to more accurately and quantitatively retrieve all their components.

![](fig_all_qsos_sed_202408.pdf)

## IR and \[C II\]  luminosities, Star Formation Rates and Dust Masses

We can estimate the \[C II\]  line luminosity from the measured velocity-integrated line flux, following (cite: carilli2013) : $$\begin{equation}
 \label{eq:lcii}
    \dfrac{L_{\rm [CII]}}{L_{\odot}} = 1.04 \times 10^{-3} \dfrac{F_{\rm [CII]}}{\rm Jy\, km\, s^{-1}} \dfrac{\nu_{\rm obs}}{\rm GHz} \left(\dfrac{D_{\rm L}}{\rm Mpc}\right)^{2}
\end{equation}$$ with $F_{\rm [CII]}$ flux of the \[C II\]  emission line, $\nu_{\rm obs}$ the observed frequency of the line, and $D_{\rm L}$ the luminosity distance.

Meanwhile, the infrared emission of high$-z$ quasars can be modelled with a modified black body (e.g., (cite: decarli2018), (cite: venemans2018)). Hence, in the optically thin scenario, the observed continuum flux density can be derived as follows (e.g. (cite: novak2019)): $$\begin{equation}
    F_{\rm obs} = \dfrac{f_{\rm CMB} [1+z]}{D_{\rm L}^{2}} \kappa_{\nu,{\rm rest}}(\beta) M_{\rm dust} B_{\nu,{\rm rest}}(T_{\rm dust}, z)
\end{equation}$$ where $M_{\rm dust}$ is the dust mass, $T_{\rm dust}$ is the dust temperature and $B_{\nu,{\rm rest}}(T_{\rm dust}, z)$ is the Planck function: $$\begin{equation}
    B_{\nu,{\rm rest}}(T_{\rm dust},z) = \dfrac{2h}{c^{2}} \nu_{\rm rest} \left[ \exp \left( {\dfrac{h_{\rm \nu}}{k T_{\rm dust}}}\right) -1 \right]
\end{equation}$$ The factor $\kappa_{\nu,{\rm rest}}(\beta)$ is the dust mass opacity coefficient, which can be written as (e.g. (cite: dunne2000)): $$\begin{equation}
    \kappa_{\nu,{\rm rest}}(\beta) = 0.077 \left( \dfrac{\nu_{\rm rest}}{\rm 352 GHz} \right)^{\beta} {\rm m^{2} kg^{-1}}
\end{equation}$$ with $\beta$ the dust emissivity power law spectral index. At high redshift ($z\gtrsim5$) the Cosmic Microwave Background (CMB) contrast starts to become significant. We can take into account this correction via the factor $f_{\rm CMB}$ (e.g. (cite: dacunha2013)): $$\begin{equation}
    f_{\rm CMB} = 1 - \dfrac{B_{\nu, {\rm rest}} (T_{{\rm CMB},z})}{B_{\nu, {\rm rest}} (T_{{\rm dust},z})}
\end{equation}$$

Here, we consider values for dust temperature and $\beta$ typically used in the literature, i.e.  $T_{\rm dust} = 47 K$ and $\beta = 1.6$ (e.g. (cite: beelen2006), (cite: decarli2018), (cite: rojas2021)). We scale the above function to the observed continuum flux densities at $\nu_{\rm rest}=1900$ GHz of our sources (as derived from the 2D Gaussian fit), as well as considering the synchrotron corrected ones (see Section [4.3](#sec:sed)). Hence, we derive dust masses for our quasars’ hosts of $<$3$\times$ 10$^{8} M_{\odot}$.

We calculate the far-infrared luminosity ($L_{\rm FIR}$) by integrating the modified black body between rest-frame wavelength 42.5 and 122.5 $\mu$m (e.g.  (cite: helou1988)). We also estimate the total infrared luminosity ($L_{\rm TIR}$) by integrating the SED between 8 and 1000 $\mu$m (e.g.  (cite: kennicutt2012)), which is equivalent to $L_{\rm FIR} = 0.75 L_{\rm TIR}$ for the model considered here.

We also estimate the equivalent width of the \[C II\]  emission line ($\rm EW_{[CII]}$): $$\begin{equation}
    \dfrac{\rm EW_{[CII]}}{\rm km\, s^{-1}} = 1000 \times \dfrac{F_{\rm [CII]}\, [{\rm Jy\, km\, s^{-1}}]}{F_{\rm cont}\, {\rm [mJy]}} 
\end{equation}$$

We can compute the star formation rates in the quasars’ host galaxies by relying both on the \[C II\]  emission line ($\rm SFR_{[CII]}$) and the infrared luminosities ($\rm SFR_{IR}$). Several studies establish a relation between $L_{\rm [C\,II]}$ and star formation rates, e.g. (cite: delooze2011), (cite: sargsyan2012), (cite: herreracamus2015). Here, we obtain \[C II\]-derived SFR using: $$\begin{equation}
    {\rm SFR_{[CII]}} = 3 \times 10^{-9} \left( \dfrac{L_{\rm [CII]}}{L_{\odot}} \right)^{1.18}
\end{equation}$$ from (cite: delooze2014), whose relation was calibrated on $z>0.5$ galaxies with a scatter of $\sim$0.4dex. For the dust-based star formation rates we use the equation from (cite: kennicutt2012): $$\begin{equation}
    \dfrac{\rm SFR_{IR}}{M_{\odot}\, {\rm yr^{-1}}} = 1.49 \times 10^{-10} \dfrac{L_{\rm TIR}}{L_{\odot}}
\end{equation}$$

We report the $L_{\rm [CII]}$, $\rm EW_{[CII]}$ and $\rm SFR_{[C\,II]}$ values obtained for the RL quasars in this work in Table [\[table:analysis_cii\]](#table:analysis_cii). The $L_{\rm FIR}$, $M_{\rm dust}$ and $\rm SFR_{IR}$ for the RL quasars newly reported here, and calculated considering the two flux density sets as described in Section [4.3](#sec:sed), are listed in Table [\[table:analysis_cont\]](#table:analysis_cont).

In Figure [7](#fig:distrprop), we show the distribution of $L_{\rm [CII]}$, $\rm EW_{[CII]}$, $\rm FWHM_{[CII]}$ and $\rm SFR_{[C\,II]}$, and their comparison with the literature sample of RQ and RL quasars. We also report the mean, median and standard deviation of the two samples in Table [\[table:mean\]](#table:mean).

Despite the limited data for RL quasars with respect to the RQ ones, we can already note that the distribution of \[C II\] emission line EW and FWHM are similar between the two samples. We performed a Kolmogorov-Smirnov (KS) test in order to assess if these properties are taken from the same underlying distribution, and report the corresponding p-values in Table [\[table:mean\]](#table:mean). For p-values $<0.05$, we can reject the null hypothesis (i.e. reject that the underlying distribution is the same). In our case, we calculate a p-value of 0.24 and 0.14 for EW and FWHM distributions, respectively, indicating that there are no systematic differences between RL and RQ quasars. Finally, we can observe potential differences in the distribution of \[C II\] emission line luminosities, where RL quasars seem to be systematically fainter than the RQ ones. We obtain a p-value of 0.04, moderately suggesting that there are differences in the two samples. More observations of \[C II\] emission in a larger sample of RL quasars at high-redshift will allow us to explore this hypothesis further.

An important effect observed in a variety of galaxies and AGN at high and low redshift is the so-called “\[C II\] deficit”, i.e. a decrease of the $L_{\rm [C\,II]}/L_{\rm FIR}$ ratio as a function of infrared luminosity. A unique understanding of the origin of this effect is still lacking, as there are several factors that could contribute to the suppression of \[C II\] luminosity. Some scenarios considered in the literature are: the ionization of C$^{+}$due to X-ray radiation from an AGN, that also boost FIR luminosities (e.g. (cite: langer2015)); self-absorption of \[C II\] in high density environments, which becomes higher than the critical density for collisional interaction (e.g.(cite: diazsantos2017), (cite: sutter2021)); or thermal saturation of C$^{+}$due to strong far-UV radiation (e.g. (cite: rybak2019)). In Figure [8](#fig:lfir_lciifir) we show $L_{\rm [C\,II]}/L_{\rm FIR}$ vs $L_{\rm FIR}$ for different samples: star-forming galaxies and Luminous Infrared Galaxies (LIRGs) at $z<1$ ((cite: farrah2013), (cite: sargsyan2014), (cite: malhotra2001) and (cite: diazsantos2013)), star forming galaxies at $1<z<5$ ((cite: stacey2010), (cite: brisbin2015), (cite: gullberg2015)), and RQ and RL quasars at $z>5$. In the low-redshift universe, there is a clear decrement of \[C II\] luminosity with increasing FIR luminosity, while for high$-z$ star forming galaxies the scatter is larger. RQ quasars hosts at $z>5$ follow a trend similar to low$-z$ ULIRGs/star forming galaxies, with $L_{\rm [C\,II]}/L_{\rm FIR}$ between $\sim 10^{-2} - 10^{-3}$. The RL quasars’ hosts mainly follow the distribution of RQ ones, with no strong dependency on the radio loudness parameter. We note that, if we consider the entire $\sim$1mm flux density as due to dust, the quasars J0131-0321 and J0410-139 show the largest difference to the parameter space occupied by high$-z$ quasars, with a $L_{\rm [C\,II]}/L_{\rm FIR}$ ratios as low as 2.5-1.2$\times$10$^{-4}$. However, once considering the synchrotron contribution, these sources move closer to the locus of RQ quasars’ hosts.

![](fig_quant_distr_202408_cii-1.pdf)

![](fig_lfir_lciifir_20240826_v4.pdf)

## IR and CO(6-5) luminosities limits

We estimate limits on the CO(6-5)  emission line luminosities ($L_{\rm CO(6-5)}$) using Equation [\[eq:lcii\]](#eq:lcii). One can also express the line luminosity via the quantity $L'$ in units of \[K km s$^{-1}$ pc$^{2}$\] following (cite: carilli2013): $$\begin{equation}
    L'_{\rm CO(6-5)} = 3.25 \times 10^{7} \times  \dfrac{F_{\rm CO(6-5)}}{\rm Jy\, km\, s^{-1}} \dfrac{1}{(1+z)^{3}} \left(\dfrac{\nu_{\rm obs}}{\rm GHz}\right)^{-2} \left(\dfrac{D_{\rm L}}{\rm Mpc}\right)^{2}
\end{equation}$$ Additionally, we can estimate the limits on the far and total-infrared luminosities as done for the objects observed in Band 7 (see Section [3.1](#sec:ciimeasure)). All the limits on CO(6-5)  and infrared luminosities from Band 3 observations are reported in Table [1](#tab:co65).

We compare the upper limits found here with CO(6-5) emission line observations in a sample of RQ quasars at $z>5$ from the literature ((cite: wang2010), (cite: wang2013), (cite: feruglio2018), (cite: feruglio2023), (cite: wangf2019), (cite: yangj2019), (cite: decarli2022), (cite: kaasinen2024)). We also consider the source PSO352-15, part of the sample here. This source was observed with NOEMA at 101 GHz by (cite: rojas2021). They estimated a 3$\sigma$ limit on the CO(6-5) emission line of $L'_{\rm CO(6-5)} < 5 \times 10^{10}$ K km s$^{-1}$ pc$^{2}$ (see their Section 3.2 for further details). Conversely, we consider the corresponding FIR luminosity derived in this work (see Table [\[table:analysis_cont\]](#table:analysis_cont)), which is consistent with the value reported by (cite: rojas2021). We report $L_{\rm FIR}$, re-calculated for the RQ sources in the literature with the method reported in Section [4.4](#sec:analysis_lum) for consistency, as a function of CO(6-5) emission line luminosities in Figure [9](#fig:lco65_lfir). We also report the expected relation between these two quantities calculated in (cite: kamenetzky2016). The limits on these quantities for the two objects newly presented here do not show a critical difference between them and the RQ quasars sample. Given the somewhat loose constraints on the CO(6-5)  luminosity of PSO352-15, this source is also consistent with the RQ quasars measurements. Deeper observations on a larger sample of RL quasars are needed to place more meaningful constraints.

![](fig_lco65_lfirlco65.pdf)

## Mass Budget

A key physical parameter that one can derive from sub-mm observations of high$-z$ quasars’ hosts is the dynamical mass of the system. This, in combination with measurements of the central SMBH mass, allows for studies of the SMBH/galaxy co-evolution at very high redshifts. Based on such comparisons, several works have shown that SMBHs in the EOR seem to be overmassive with respect to systems in the local universe (e.g.  (cite: farina2022); see (cite: pacucci2024) for a recent compilation, but also (cite: izumi2021)).

In this work, the FIR continuum and \[C II\] emission of the radio-loud quasars’ host galaxies are unresolved (see Figure [2](#fig:1dciimap), [11](#fig:ciimapmom0) and Table [\[tab:2dfit\]](#tab:2dfit)). Hence, the quality of our data prevents us from performing a full modeling of the kinematics of our sources, as done in studies of $z>5$ quasars’ hosts with higher spatial resolution and SNR observations (e.g.  (cite: pensabene2020), (cite: neeleman2021)). Therefore, we estimate the dynamical masses of the host galaxies presented here in a simplified way, following (cite: decarli2018). Briefly, under the assumption that the system is dominated by dispersion, one can express $M_{\rm dyn}$ with the following:

$$\begin{equation}
    M_{\rm dyn} = \frac{3}{2} \dfrac{ {\rm R_{[C\,II]}} \sigma_{\rm [C\,II]}^{2} }{\rm G} = \frac{\rm R_{[C\,II]}}{G} \left( \dfrac{\rm 0.75 FWHM_{[C\,II]}}{sin(i)} \right)^{2}
\end{equation}$$

where $\rm R_{[C\,II]}$ is the size of the \[C II\] emission line, considered as the major axis of the 2D Gaussian fit of the \[C II\] map, $G$ is the gravitational constant and $\sigma_{\rm [C\,II]}$ is derived from the Gaussian fit of the line, which is equivalent to 0.75$\times$FWHM$_{\rm [C\,II]}$. The second equation stands valid assuming that the width of the line is rotation-dominated, considering a flat disk structure with an inclination angle $i$. We utilize an angle $i=46^{\circ}$, i.e.  the median inclination of a $z>6$ quasar hosts’ sample derived by (cite: wangf2024). We obtain dynamical masses between $2-20 \times 10^{10} M_{\odot}$ (see Table [\[table:analysis_cii\]](#table:analysis_cii)). This is broadly consistent with values similarly obtained for RQ quasars in the literature (e.g.  (cite: decarli2018), (cite: wangf2024)).

We can also infer molecular masses ($M_{\rm H2}$) relying on the \[C II\] luminosity, as calibrated from a sample of $z\sim2$ main sequence and starburst galaxies by (cite: zanella2018):

$$\begin{equation}
    \dfrac{M_{\rm H2, [C\,II]}}{M_{\odot}} = \dfrac{\alpha_{\rm [C\,II]}}{M_{\odot}\, L_{\odot}^{-1}} \dfrac{L_{\rm [C\,II]}}{L_{\odot}}
\end{equation}$$

with $\alpha_{\rm [C\,II]} = 30 M_{\odot} L_{\odot}^{-1}$. We report the values of $M_{\rm H2,[C\,II]}$ for the sources presented here in Table [\[table:analysis_cii\]](#table:analysis_cii). RL sources do not show significant differences with respect to RQ ones (e.g. (cite: decarli2022)).

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Name | $L_{\rm [CII]}$ | EW$\rm _{[CII]}$ | $\rm SFR_{[CII]}$ | $M_{\rm dyn}$ | $M_{\rm H2,[C\,II]}$ |
|  | \[$10^{8}\, L_{\odot}$\] | \[km  s$^{-1}$\] | \[$M_{\odot}\, {\rm yr}^{-1}$\] | \[$10^{10}\, M_{\odot}$\] | \[$10^{9}\, M_{\odot}$\] |
| J0131-0321 | 3.8$\pm$0.8 | 225$\pm$45 | 40$\pm$9 | 4.8$\pm$4.0 | 11$\pm$2.0 |
| PSO055-00$^{\star}$ | 3.1$\pm$0.3 | 578$\pm$78 | 32$\pm$3 | 2.8$\pm$2.2 | 9.3$\pm$0.8 |
| PSO135+16 | 27.7$\pm$1.0 | 683$\pm$35 | 416$\pm$18 | 15.0$\pm$1.8 | 83$\pm$3.0 |
| J1034+2033 | 3.1$\pm$0.3 | 2476$\pm$505 | 32$\pm$4 | 5.8$\pm$4.9 | 9.3$\pm$0.9 |
| PSO352–15 | 7.9$\pm$1.1 | 2790$\pm$472 | 95$\pm$15 | 23.3$\pm$10.7 | 24$\pm$3.0 |

Table notes: **$^{\star}$** We note that PSO055-00’s line emission is recovered at the edge of the bandwith. Therefore, caution should be taken when considering its \[C II\] emission line value and all derived quantities.

+:-------------------------------------------------+:----:+:------:+:------:+:--------:+:--------:+:--------:+:-------:+
|                                                  | RQ quasars             | RL quasars$^{\star}$           | KS-test |
+--------------------------------------------------+------+--------+--------+----------+----------+----------+---------+
|                                                  | mean | median | st.dev | mean     | median   | st.dev   | p-value |
+--------------------------------------------------+------+--------+--------+----------+----------+----------+---------+
| FWHM$_{\rm [CII]}$ \[km s$^{-1}$\]               | 387  | 379    | 133    | 272      | 290      | 110      | 0.14    |
+--------------------------------------------------+------+--------+--------+----------+----------+----------+---------+
| EW$_{\rm [CII]}$ \[km s$^{-1}$\]                 | 2362 | 1691   | 2013   | 1848     | 1180     | 1441     | 0.24    |
+--------------------------------------------------+------+--------+--------+----------+----------+----------+---------+
| $L_{\rm [CII]}$ \[$10^{9}\, L_{\odot}$\]         | 2.9  | 1.8    | 2.6    | 1.5      | 0.8      | 1.2      | 0.04    |
+--------------------------------------------------+------+--------+--------+----------+----------+----------+---------+
| $\rm SFR_{[CII]}$ \[M$_{\odot}\,{\rm yr}^{-1}$\] | 466  | 258    | 498    | 211      | 95       | 194      | 0.04    |
+--------------------------------------------------+------+--------+--------+----------+----------+----------+---------+

Table notes: We also report the p-values obtained with a Kolmogorov-Smirnov test, to assess if the observed quantities for RQ and RL quasars were obtained from the same underlying distribution. **$^{\star}$** We only consider sources with \[C II\] emission lines detection, i.e. we exclude PSO172+18 from this comparison.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $L_{\rm FIR,tot}$ | $L_{\rm FIR,syn}$ | $\rm SFR_{IR,tot}$ | $\rm SFR_{IR,syn}$ | $M_{\rm dust,tot}$ | $M_{\rm dust,syn}$ |
|  | \[$10^{11}\, L_{\odot}$\] | \[$10^{11}\, L_{\odot}$\] | \[$M_{\odot}\, {\rm yr}^{-1}$\] | \[$M_{\odot}\, {\rm yr}^{-1}$\] | \[$10^{7}\, M_{\odot}$\] | \[$10^{7}\, M_{\odot}$\] |
| J0131-0321**$^{\dagger}$** | 32.4$\pm$0.85 | \- | 400$\pm$10 | \- | 19.9$\pm$0.3 | \- |
| PSO055-00 | 10.5$\pm$1.1 | 9.4$\pm$1.1 | 129$\pm$14 | 116$\pm$14 | 2.8$\pm$2.2 | 3.8$\pm$0.4 |
| PSO135+16 | 78.8$\pm$2.9 | 77$\pm$2.8 | 973$\pm$35 | 951$\pm$35 | 31.5$\pm$1.1 | 30.7$\pm$1.1 |
| J1034+2033 | 2.4$\pm$0.4 | 1.47$\pm$0.4 | 30$\pm$5 | 18$\pm$5 | 0.9$\pm$0.2 | 0.6$\pm$0.2 |
| PSO352–15 | 5.5$\pm$0.6 | 5.5$\pm$0.8 | 68$\pm$7 | 68$\pm$7 | 2.2$\pm$0.2 | 2.2$\pm$0.2 |

Table notes: **$^{\dagger}$** The synchrotron contribution could amount to almost all the flux density at $\sim$300 GHz for this source. Hence, we report in this case only the IR values obtained from considering the total measured ALMA flux density as due to the dust, and use them as upper limits.

## Impact of AGN Luminosity on \[C II\] and FIR Emission

Unveiling the relative role of AGN vs star formation in heating gas and dust in the ISM is crucial to understand quasar/galaxy (co)evolution, especially at high redshift.

This can be done by comparing observations of different far-infrared emission lines (e.g. \[N II\] 205$\mu$m, \[O I\] 146$\mu$m, \[O III\] 88$\mu$m, \[C I\] 369$\mu$m) with output of photoionization codes (e.g. CLOUDY; (cite: ferland2017)).

Some works in the literature provide these studies for few $z\gtrsim6$ quasars, showing that their host galaxies are mainly heated by star formation, with apparently no evident contribution from the AGN (e.g. (cite: venemans2017b), (cite: novak2019), (cite: pensabene2021), (cite: meyer2022a)).

However, such investigations are currently limited to few objects, due to the time consuming nature of the observations of different, faint lines in the (sub-)mm. Hence, to gauge the AGN contribution to the host galaxy in a larger sample of quasars, one can resort to more straightforward methods, e.g. comparing the absolute UV magnitude at rest frame wavelength 1450 $\AA$, linked with the AGN activity, to the FIR and \[C II\] luminosities, arising instead from the host galaxy. (cite: decarli2018) and (cite: venemans2018) provided this comparison for $\sim30$ UV-bright quasars observed with ALMA, remarking that no strong correlation between UV and FIR was recovered, especially when focusing on the more complete sample at high UV luminosities. (cite: venemans2020) confirmed this lack of correlation with ALMA observations at higher ($\sim$kpc) spatial resolution, concluding that not even the most central FIR emission seemed to be affected by the presence of an AGN.

Here, we show $L_{\rm [C\,II]}$ and $L_{\rm FIR}$ as a function of $M_{1450}$ for the RQ quasars sample from the literature and for the RL quasars (Figure [10](#fig:M1450IR)). We note that the majority of the RL quasars fall in the same parameter space as the RQ ones, i.e.  in both samples, considering a given UV luminosity, we observe a large range of $L_{\rm [C\,II]}$ and $L_{\rm FIR}$ values, with a scatter larger than an order of magnitude. No strong correlation with radio-loudness can be recovered. However, we note that few objects (J0131-0321, J1034+2033, PSO055-00 and PSO172+18) are outliers in the $L_{\rm [C\,II]}$ vs $M_{1450}$ plane, i.e. they show a much lower \[C II\] luminosity than that observed in RQ quasars with a comparable UV luminosity.

![](fig_m1450_lciifir_202405_v2-1.pdf)

## Companions

RL quasars and radio galaxies are found to be surrounded by overdensities of galaxies (e.g. (cite: wylezalek2013), (cite: gilli2019)). Different studies using rest-frame UV observations recovered a rich environment around the $z\sim5.8$ RL quasar J0836+0054 (e.g. (cite: zheng2006), (cite: ajiki2006), (cite: bosman2020), (cite: overzier2022)). At the same time, ALMA observations of RQ quasars found several, line-emitters in their surroundings, from systems in advanced mergers to galaxies at tens of kpc distances (e.g. (cite: decarli2017), (cite: trakhtenbrot2017), (cite: nguyen2020), (cite: neeleman2021)). Nevertheless, we note that studies looking for continuum dust emitters around quasars were not successful in discovering clear overdensities (e.g. (cite: champagne2018), (cite: meyer2022b)).

In this work, we search for line emitters in the fields of the RL quasars observed in Band 7, using the continuum emission subtracted cubes obtained as reported in Section [3.1](#sec:ciimeasure). We utilize the code *findclumps*[^5] (cite: walter2016). In brief, $\textit{findclumps}$ performs a floating average of channels over different spectral windows. For each window, it searches for positive and negative emission peaks at different SNR, where the noise is calculated as the rms of the collapsed map. In this work, we use spectral windows of width between 3 and 19 channels. We crop multiple entries by discarding sources which are closer than 2$''$  Finally, we perform a fidelity check to test the reliability of our candidates. Under the assumption that the positive emission comprehends real astrophysical sources and noise, while the negative emission are due only to noise, we use the following equation (cite: walter2016): $$\begin{equation}
    {\rm fidelity (SNR)} = 1 - \dfrac{N_{\rm neg} ({\rm SNR})}{N_{\rm pos} ({\rm SNR})} 
\end{equation}$$ with $N_{\rm neg} ({\rm SNR})$ and $N_{\rm pos} ({\rm SNR})$ are the number of negative and positive detections at a certain SNR, respectively. In order to not be limited by the low number counts of positive and negative detections around each quasar, we compute the fidelity considering the catalogs obtained from of all the quasars fields at once. Following (cite: venemans2020) and (cite: meyer2022b), we assume a fidelity threshold as calculated in each channel of 90% (Fidelity$>$0.9). We select sources with SNR$>$4, although it is worthwhile to notice that the cut on fidelity already selects sources with SNR$\gtrsim$4-5. We crop sources close to the edge of the field of view and those at a distance of $\Delta v > \pm 1000$ km s$^{-1}$[^6] (e.g.  (cite: venemans2020)).

Considering all the above conditions, we do not recover any companion candidate in our RL quasars fields. We can still compare this result with what observed around RQ quasars fields and with expectations from blank fields.

In particular, (cite: venemans2020) found 27 line emitters in the fields of 14 RQ quasars at $z\sim6$, out of 26 fields inspected. In particular, 19 (17) of these sources were identified as \[C II\]  emitters companion candidates to the quasars, with $\Delta v < 2000$ km s$^{-1}$ ($\Delta v < 1000$ km s$^{-1}$). They also discovered 3 companion candidates in the field of the RL quasar J2318-3113. However, our work and (cite: venemans2020) are characterized by different depths. If we consider solely the companion candidates around RQ quasars that would satisfy our SNR$>$4 criterion, for a \[C II\]  emission line with typical FWHM$\sim$300 km s$^{-1}$ ($F_{\rm [C\,II]} \sim$1.77 Jy km s$^{-1}$), we are left with only 3 sources. These sources (in the fields of J0842+1218, PSO231-20, J2100-1715) were also recovered by (cite: decarli2017), whose observations sensitivity is similar to that of our work. We also note that the companion candidates found by (cite: venemans2020) around J2338-3113 are fainter than the detection limits of our observations. Hence, at the depth of our work, one would expect to recover 3 \[C II\]  emitting companion candidates in 26 RQ quasars fields, i.e.  in only $\sim$10% of the fields. This is still consistent with finding zero companion candidates in 5 fields. We can also compare our results with the expected number of sources in a blank field, i.e.  with no quasar. We consider the number density of \[C II\]  emitting sources provided in (cite: uzgil2021) and (cite: decarli2020), in the redshift range $z=6-8$, with $L_{\rm [C\,II]} > 2.8 \times 10^{8} L_{\odot}$[^7] ($<$1.94$\times$10$^{-4}$ Mpc$^{-3}$; see Table 3 in (cite: uzgil2021)). Considering the total volume covered in the 5 RL quasars fields observed here, within $\Delta v<1000$ km s$^{-1}$, we would expect to observe $<$0.02 sources.

In conclusion, given the depth of our current observations and the number of fields explored, we are not able to place strong constraints on the properties of the fields of RL quasars, i.e.  they are still consistent with both the expectations of blank fields and RQ quasars fields. Larger samples of RL quasars targeted in the sub-mm, and/or with deeper observations, will allow for further comparisons between the two samples.

# Discussion

The interaction between radio jets and the ISM of galaxies is expected to produce different outcomes, depending on various circumstances local to each galaxy and their proximate environment. As seen in both observations and simulations, a radio jet can drive massive, multi-phase (ionized, warm and molecular gas) outflows, whose geometry (following the jet direction, or perpendicular to it) depends on the jet inclination and jet-ISM coupling (e.g. (cite: morganti2015), (cite: Meenakshi2022), (cite: Zhong2024)). This mechanism will also boost the gas turbulence, and hence increase the observed gas velocity and dispersion (e.g. (cite: venturi2023)). In addition, the passage of the jet can form density fluctuations in the ISM, forming hot ($>150$ K) and dense ($>10^{5}$ cm$^{-3}$) gas, that can be observed via several CO emission lines, with an increase in the flux of higher J level transitions (e.g. (cite: audibert2023)). At the same time, observations of spectacular cases of RL AGN at low$-z$ (e.g. (cite: guillard2015), (cite: appleton2018)) showed how the \[C II\] emission line can be originated from shocks and/or outflows, and trace the radio jet-ISM interaction. (cite: pinchukova2019) reported a significant boost of \[C II\]  emission in a nearby AGN with radio jets, with a $L_{\rm [C\,II]}/L_{\rm IR}$ ratio ten times higher than other AGN at comparable redshifts. Considering all these, we might expect in RL quasars to observe \[C II\] emission lines with larger FWHM, and/or asymmetric line profiles, or peculiar morphologies and with higher luminosities with respect to what recovered in RQ ones. On the contrary, the \[C II\] luminosities of the sources in our sample are comparable or slightly lower than those observed in $z\sim6$ RQ quasars, and we do not recover any strong differences in FWHM values, spectral profiles or morphologies. This can be due to the fact that the aforementioned mechanisms might not be instantaneous, or could only be important on local scales, and hence difficult to highlight with our integrated, spatially unresolved, and low SNR observations (see also (cite: molyneux2024), for comparable conclusions in a study of a sample of $z<0.2$ radio AGN). Moreover, high spatial resolution observations highlight that several high$-z$ RQ quasars’ hosts are found in mergers, which can broaden the apparent FWHM values (cite: neeleman2021), complicating the comparison. Another important aspect to consider is the possibility that extreme feedback from radio-jets can displace the gas and remove it altogether from the gravitational influence of the galaxy (e.g. (cite: murthy2022)). The marginally lower \[C II\] luminosities observed in our high$-z$ RL quasars sample may than be the result of such process. Finally, however, it is important to notice that the complex physical mechanisms responsible for \[C II\] emission complicate the interpretation of our results. Higher SNR and angular resolution \[C II\] observations are necessary to disentangle these different interpretations.

Conversely, it is believed that radio-loud AGN are preferentially found in major mergers, which could trigger the nuclear accretion and the formation of the jets by funnelling a large amount of gas towards the center (e.g. (cite: chiaberge2015), (cite: breiding2024)). At the same time, as discussed above, RL sources are expected to be found in overdensities of galaxies (e.g. (cite: wylezalek2013), (cite: hatch2014)). (cite: khusanova2022) showed potential evidence for a larger merger fraction amongst $z>6$ RL quasars ($>40$%) with respect to RQ ones ($\sim30$%; (cite: neeleman2021)). We do not recover merger signs in the RL quasars newly studied in this work. If we consider the entire sample of RL quasars (this work+literature), we recover only 2 sources which are potentially hosted in a major merger, allowing for a merger fraction of $\sim20$%, even lower than that observed in RQ quasars. At the same time, none of the RL quasars inspected is surrounded by strong overdensities of bright \[C II\] emitters. Given the course angular resolution and low SNR of our observations, and the limited sample reported, we refrain from drawing further conclusions.

# Conclusions and Outlooks

In this work, we present new ALMA observations of six RL and one RQ quasars at $z>5$. We acquire data in Band 7 (5 RL sources), targeting the \[C II\]  emission line and underlying dust continuum, and in Band 3 (2 sources, 1 RL and 1 RQ), focusing on the CO(6-5)  line. We detect (at $\sigma>$2) the \[C II\]  emission line and continuum for the quasars targeted in Band 7 (Tables [\[tab:1dcii\]](#tab:1dcii), [\[tab:2dfit\]](#tab:2dfit)), while no emission is recovered in Band 3, hence we can only place upper limits on the relative CO(6-5)  emission line flux/luminosity and underlying dust continuum/IR luminosity (Table [1](#tab:co65)).

At current spatial resolution ($\sim$1.0$''$$-$1.4$''$), no extended or disturbed morphologies are clearly detected in the Band 7 continuum maps (Figures [4](#fig:contmap), [5](#fig:cont23map)), nor in the continuum-subtracted \[C II\]  emission line maps (Figure [2](#fig:1dciimap)): i.e.  the source sizes are broadly consistent with the beam sizes. All the extracted \[C II\]  1D spectra are well fitted with a single Gaussian function (Figure [1](#fig:1dciiline)). Hence, there is no strong evidence for mergers in the RL quasars hosts newly analyzed here.

Considering our new ALMA data and radio/sub-mm observations from the literature, we build the SED of the six RL quasars studied here (Figure [6](#fig:sed)). Although the observations forming the SEDs are obtained at different epochs and are not corrected for any potential variability, we observe that the ALMA 1mm measurements are consistent with being a combination of the high-frequency tail of radio synchrotron emission and dust continuum emission. At least in four sources this contribution is estimated to be $>9$%, and in two cases, J1034+2033 and J0131-0321, it can be as high as $\sim$40% and $\sim$100%, respectively. Hence, extreme caution should be taken when deriving dust properties (luminosities, masses, SFR) for these objects.

Given the limited data at hands, a full spectral fit of the different components is currently out of the scope of this work.

We derive estimates on the \[C II\]  and infrared luminosities, as well as on the dust, dynamical and molecular gas masses, and \[C II\]-  and IR-based SFRs considering two scenarios: first, under the assumption that all the continuum emission arises from the galaxies’ ISM, and secondly by accounting for our initial estimate of the synchrotron contribution (see Section [4.4](#sec:analysis_lum) and [4.6](#sec:analysis_massdyn)). The hosts of the RL quasars observed in this work present relatively large cool gas reservoirs, with $L_{\rm [C\,II]} \sim 3-30 \times 10^{8}$, $M_{\rm dyn}\sim1-10 \times 10^{10} M_{\odot}$, and $M_{\rm H2, [C\,II]}\sim9-80 \times 10^{9} M_{\odot}$. Moreover, they are also actively forming stars, with SFR$_{\rm [C\,II]}\sim30-400$ $M_{\odot}$ yr$^{-1}$.

We place these new measurements in the context of observations of RQ and RL quasars’ hosts from the literature. The \[C II\]  EW and FWHM in RL quasars are broadly consistent with those of RQ ones, but we observe slightly lower \[C II\]  luminosities and SFR for RL sources (with a p-value of $\sim$0.04; Figure [7](#fig:distrprop) and Table [\[table:mean\]](#table:mean)).

Furthermore, the \[C II\]  decrement in RL quasars’ hosts is in the same parameter space as those of RQ ones, with no dependency on radio loudness parameter. When considering the synchrotron contribution at $\sim$1mm, even outlier cases (e.g.  J0131-0321 and J0410-0139) are consistent with RQ quasars (Figure [8](#fig:lfir_lciifir)).

Additionally, we search for line emitting candidates in the fields of the five RL quasars observed in Band 7 in this work, using the *findclumps* code, and selecting sources with a fidelity value higher than 0.9, a SNR$>4$, excluding the edges of the images, and within $\Delta v < 1000$ km s$^{-1}$ (see Section [4.8](#sec:analysis_comp)). We do not recover any \[C II\] emitting companion candidate. Comparing this result with the number of sources expected in a blank field, and observed around a sample of RQ quasars at $z\sim$6, we see that the fields of RL quasars are still comparable with RQ ones or the blank field, given the depth of our data.

Several approaches will be important for further investigations of high$-$z RL quasars hosts properties. In the latest few years, the number of RL quasars at high$-z$ strongly increased (e.g. (cite: gloudemans2022), (cite: belladitta2023)), allowing, in the future, to cover a larger sample of such sources and to undertake a more meaningful comparison with RQ quasars’ hosts. In addition, radio/sub-mm observations of RL quasars over a large frequency range, covering the spectral region dominated by the jet and down to the peak of the modified black body dust emission, with several facilities (i.e., ALMA, VLA, NOEMA, uGMRT), will allow for a full fit of the spectral energy distributions. Hence, it will be possible to properly disentangle the non-thermal synchrotron and dust contributions, and to place strong constraints on the ISM properties of the host galaxies. Moreover, follow-up observations of different sub-mm emission lines (e.g. \[N II\] 205$\mu$m, \[O I\] 146$\mu$m, \[O III\] 88$\mu$m, \[C I\] 369$\mu$m, high-J CO transitions) would enable constraints on the role of the central AGN and/or of the radio-jets in the arising of the \[C II\]  and continuum emission (e.g. (cite: pensabene2021), (cite: li2024)). Additional higher spatial-resolution and SNR data targeted at the \[C II\]  emission line could allow to constrain more complex morphology/kinematic signatures, which might be due to merger events or the passage of a radio-jet (e.g. (cite: neeleman2021), (cite: khusanova2022)). The recently launched JWST already showed its key role in unveiling the properties of the hot ionized gas in both high-redshift quasars’ hosts/galaxies (e.g.  (cite: ding2023), (cite: marshall2023)) and in powerful jetted/non-jetted AGN at Cosmic Noon (e.g.  (cite: wylezalek2022), (cite: cresci2023),(cite: vayner2023), (cite: wangw2024)). Thus, deep NIRSpec IFU/NIRCAM observations of $z>5$ RL quasars’ hosts would shed a fundamental light on the rest-frame optical properties of such galaxies, e.g. the underlying stellar continuum emission, the black hole mass and accretion rate from the H$\alpha$ or H$\beta$ emission line modelling, any central or extended outflow via observations of the \[OIII\] emission lines, and the characterization of the warm ionized ISM, and uncover any interplay with the radio-jets and their role in launching complex, multi-phase outflows.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00840.S. ALMA is a partnership of ESO (representing its member states), NFS (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This scientific work uses data obtained from Inyarrimanha Ilgari Bundara / the Murchison Radio-astronomy Observatory. We acknowledge the Wajarri Yamaji People as the Traditional Owners and native title holders of the Observatory site. CSIRO’s ASKAP radio telescope is part of the Australia Telescope National Facility (https://ror.org/05qajvd42). Operation of ASKAP is funded by the Australian Government with support from the National Collaborative Research Infrastructure Strategy. ASKAP uses the resources of the Pawsey Supercomputing Research Centre. Establishment of ASKAP, Inyarrimanha Ilgari Bundara, the CSIRO Murchison Radio-astronomy Observatory and the Pawsey Supercomputing Research Centre are initiatives of the Australian Government, with support from the Government of Western Australia and the Science and Industry Endowment Fund. This paper includes archived data obtained through the CSIRO ASKAP Science Data Archive, CASDA (https://data.csiro.au).

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

C.M. acknowledges support from Fondecyt Iniciacion grant 11240336 and the ANID BASAL project FB210003.

F.W. acknowledges support from the US NSF Grant AST-2308258.

R.A.M acknowledges support from the Swiss National Science Foundation (SNSF) through project grant 200020_207349.

natexlab

(ref: ajiki2006) Ajiki, M., Taniguchi, Y., Murayama, T., et al. 2006, PASJ, 58, 499, doi: [`10.1093/pasj/58.3.499`](http://doi.org/10.1093/pasj/58.3.499)

(ref: allison2022) Allison, J. R., Sadler, E. M., Amaral, A. D., et al. 2022, PASA, 39, e010, doi: [`10.1017/pasa.2022.3`](http://doi.org/10.1017/pasa.2022.3)

(ref: appleton2018) Appleton, P. N., Diaz-Santos, T., Fadda, D., et al. 2018, ApJ, 869, 61, doi: [`10.3847/1538-4357/aaed2a`](http://doi.org/10.3847/1538-4357/aaed2a)

(ref: audibert2023) Audibert, A., Ramos Almeida, C., Garcı́a-Burillo, S., et al. 2023, A&A, 671, L12, doi: [`10.1051/0004-6361/202345964`](http://doi.org/10.1051/0004-6361/202345964)

(ref: banados2018c) Bañados, E., Carilli, C., Walter, F., et al. 2018a, ApJL, 861, L14, doi: [`10.3847/2041-8213/aac511`](http://doi.org/10.3847/2041-8213/aac511)

(ref: banados2015b) Bañados, E., Decarli, R., Walter, F., et al. 2015a, ApJL, 805, L8, doi: [`10.1088/2041-8205/805/1/L8`](http://doi.org/10.1088/2041-8205/805/1/L8)

(ref: banados2015a) Bañados, E., Venemans, B. P., Morganson, E., et al. 2015b, ApJ, 804, 118, doi: [`10.1088/0004-637X/804/2/118`](http://doi.org/10.1088/0004-637X/804/2/118)

(ref: banados2016) Bañados, E., Venemans, B. P., Decarli, R., et al. 2016, ApJS, 227, 11, doi: [`10.3847/0067-0049/227/1/11`](http://doi.org/10.3847/0067-0049/227/1/11)

(ref: banados2018a) Bañados, E., Venemans, B. P., Mazzucchelli, C., et al. 2018b, Nature, 553, 473, doi: [`10.1038/nature25180`](http://doi.org/10.1038/nature25180)

(ref: banados2021) Bañados, E., Mazzucchelli, C., Momjian, E., et al. 2021, ApJ, 909, 80, doi: [`10.3847/1538-4357/abe239`](http://doi.org/10.3847/1538-4357/abe239)

(ref: banados2023) Bañados, E., Schindler, J.-T., Venemans, B. P., et al. 2023, ApJS, 265, 29, doi: [`10.3847/1538-4365/acb3c7`](http://doi.org/10.3847/1538-4365/acb3c7)

(ref: banados2024a) Banados, E., Momjian, E., Connor, T., et al. 2024a, arXiv e-prints, arXiv:2407.07236, doi: [`10.48550/arXiv.2407.07236`](http://doi.org/10.48550/arXiv.2407.07236)

(ref: banados2024b) Banados, E., Khusanova, Y., Decarli, R., et al. 2024b, arXiv e-prints, arXiv:2408.12299, doi: [`10.48550/arXiv.2408.12299`](http://doi.org/10.48550/arXiv.2408.12299)

(ref: becker1995) Becker, R. H., White, R. L., & Helfand, D. J. 1995, ApJ, 450, 559, doi: [`10.1086/176166`](http://doi.org/10.1086/176166)

(ref: beelen2006) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694, doi: [`10.1086/500636`](http://doi.org/10.1086/500636)

(ref: belladitta2023) Belladitta, S., Moretti, A., Caccianiga, A., et al. 2023, A&A, 669, A134, doi: [`10.1051/0004-6361/202243855`](http://doi.org/10.1051/0004-6361/202243855)

(ref: belladitta2019) —. 2019, A&A, 629, A68, doi: [`10.1051/0004-6361/201935965`](http://doi.org/10.1051/0004-6361/201935965)

(ref: belladitta2020) —. 2020, A&A, 635, L7, doi: [`10.1051/0004-6361/201937395`](http://doi.org/10.1051/0004-6361/201937395)

(ref: bischetti2019) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, A&A, 630, A59, doi: [`10.1051/0004-6361/201833557`](http://doi.org/10.1051/0004-6361/201833557)

(ref: boogaard2021) Boogaard, L., Meyer, R. A., & Novak, M. 2021, Interferopy: analysing datacubes from radio-to-submm observations, v1.0.0-beta, Zenodo, doi: [`10.5281/zenodo.5775603`](http://doi.org/10.5281/zenodo.5775603)

(ref: bosman2020) Bosman, S. E. I., Kakiichi, K., Meyer, R. A., et al. 2020, ApJ, 896, 49, doi: [`10.3847/1538-4357/ab85cd`](http://doi.org/10.3847/1538-4357/ab85cd)

(ref: breiding2024) Breiding, P., Chiaberge, M., Lambrides, E., et al. 2024, ApJ, 963, 91, doi: [`10.3847/1538-4357/ad19db`](http://doi.org/10.3847/1538-4357/ad19db)

(ref: brisbin2015) Brisbin, D., Ferkinhoff, C., Nikola, T., et al. 2015, ApJ, 799, 13, doi: [`10.1088/0004-637X/799/1/13`](http://doi.org/10.1088/0004-637X/799/1/13)

(ref: carilli2013) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: champagne2018) Champagne, J. B., Decarli, R., Casey, C. M., et al. 2018, ApJ, 867, 153, doi: [`10.3847/1538-4357/aae396`](http://doi.org/10.3847/1538-4357/aae396)

(ref: chiaberge2015) Chiaberge, M., Gilli, R., Lotz, J. M., & Norman, C. 2015, ApJ, 806, 147, doi: [`10.1088/0004-637X/806/2/147`](http://doi.org/10.1088/0004-637X/806/2/147)

(ref: cresci2023) Cresci, G., Tozzi, G., Perna, M., et al. 2023, A&A, 672, A128, doi: [`10.1051/0004-6361/202346001`](http://doi.org/10.1051/0004-6361/202346001)

(ref: dacunha2013) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13, doi: [`10.1088/0004-637X/766/1/13`](http://doi.org/10.1088/0004-637X/766/1/13)

(ref: delooze2011) De Looze, I., Baes, M., Bendo, G. J., Cortese, L., & Fritz, J. 2011, MNRAS, 416, 2712, doi: [`10.1111/j.1365-2966.2011.19223.x`](http://doi.org/10.1111/j.1365-2966.2011.19223.x)

(ref: delooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62, doi: [`10.1051/0004-6361/201322489`](http://doi.org/10.1051/0004-6361/201322489)

(ref: decarli2012) Decarli, R., Walter, F., Yang, Y., et al. 2012, ApJ, 756, 150, doi: [`10.1088/0004-637X/756/2/150`](http://doi.org/10.1088/0004-637X/756/2/150)

(ref: decarli2017) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: decarli2018) —. 2018, ApJ, 854, 97, doi: [`10.3847/1538-4357/aaa5aa`](http://doi.org/10.3847/1538-4357/aaa5aa)

(ref: decarli2020) Decarli, R., Aravena, M., Boogaard, L., et al. 2020, ApJ, 902, 110, doi: [`10.3847/1538-4357/abaa3b`](http://doi.org/10.3847/1538-4357/abaa3b)

(ref: decarli2022) Decarli, R., Pensabene, A., Venemans, B., et al. 2022, A&A, 662, A60, doi: [`10.1051/0004-6361/202142871`](http://doi.org/10.1051/0004-6361/202142871)

(ref: diazsantos2013) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68, doi: [`10.1088/0004-637X/774/1/68`](http://doi.org/10.1088/0004-637X/774/1/68)

(ref: diazsantos2017) —. 2017, ApJ, 846, 32, doi: [`10.3847/1538-4357/aa81d7`](http://doi.org/10.3847/1538-4357/aa81d7)

(ref: ding2023) Ding, X., Onoue, M., Silverman, J. D., et al. 2023, Nature, 621, 51, doi: [`10.1038/s41586-023-06345-5`](http://doi.org/10.1038/s41586-023-06345-5)

(ref: drake2019) Drake, A. B., Farina, E. P., Neeleman, M., et al. 2019, ApJ, 881, 131, doi: [`10.3847/1538-4357/ab2984`](http://doi.org/10.3847/1538-4357/ab2984)

(ref: dunne2000) Dunne, L., Eales, S., Edmunds, M., et al. 2000, MNRAS, 315, 115, doi: [`10.1046/j.1365-8711.2000.03386.x`](http://doi.org/10.1046/j.1365-8711.2000.03386.x)

(ref: eilers2020a) Eilers, A.-C., Hennawi, J. F., Decarli, R., et al. 2020, ApJ, 900, 37, doi: [`10.3847/1538-4357/aba52e`](http://doi.org/10.3847/1538-4357/aba52e)

(ref: eilers2021) —. 2021, ApJ, 914, 74, doi: [`10.3847/1538-4357/ac05c3`](http://doi.org/10.3847/1538-4357/ac05c3)

(ref: fan2023) Fan, X., Bañados, E., & Simcoe, R. A. 2023, ARA&A, 61, 373, doi: [`10.1146/annurev-astro-052920-102455`](http://doi.org/10.1146/annurev-astro-052920-102455)

(ref: fan2001) Fan, X., Narayanan, V. K., Lupton, R. H., et al. 2001, AJ, 122, 2833, doi: [`10.1086/324111`](http://doi.org/10.1086/324111)

(ref: fan2006) Fan, X., Strauss, M. A., Becker, R. H., et al. 2006, AJ, 132, 117, doi: [`10.1086/504836`](http://doi.org/10.1086/504836)

(ref: farina2019) Farina, E. P., Arrigoni-Battaia, F., Costa, T., et al. 2019, ApJ, 887, 196, doi: [`10.3847/1538-4357/ab5847`](http://doi.org/10.3847/1538-4357/ab5847)

(ref: farina2022) Farina, E. P., Schindler, J.-T., Walter, F., et al. 2022, ApJ, 941, 106, doi: [`10.3847/1538-4357/ac9626`](http://doi.org/10.3847/1538-4357/ac9626)

(ref: farrah2013) Farrah, D., Lebouteiller, V., Spoon, H. W. W., et al. 2013, ApJ, 776, 38, doi: [`10.1088/0004-637X/776/1/38`](http://doi.org/10.1088/0004-637X/776/1/38)

(ref: ferland2017) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385, doi: [`10.48550/arXiv.1705.10877`](http://doi.org/10.48550/arXiv.1705.10877)

(ref: feruglio2018) Feruglio, C., Fiore, F., Carniani, S., et al. 2018, A&A, 619, A39, doi: [`10.1051/0004-6361/201833174`](http://doi.org/10.1051/0004-6361/201833174)

(ref: feruglio2023) Feruglio, C., Maio, U., Tripodi, R., et al. 2023, ApJL, 954, L10, doi: [`10.3847/2041-8213/ace0c8`](http://doi.org/10.3847/2041-8213/ace0c8)

(ref: fragile2017) Fragile, P. C., Anninos, P., Croft, S., Lacy, M., & Witry, J. W. L. 2017, ApJ, 850, 171, doi: [`10.3847/1538-4357/aa95c6`](http://doi.org/10.3847/1538-4357/aa95c6)

(ref: gabanyi2015) Gabanyi, K. E., Cseh, D., Frey, S., et al. 2015, MNRAS, 450, L57, doi: [`10.1093/mnrasl/slv046`](http://doi.org/10.1093/mnrasl/slv046)

(ref: ghisellini2015) Ghisellini, G., Tagliaferri, G., Sbarrato, T., & Gehrels, N. 2015, MNRAS, 450, L34, doi: [`10.1093/mnrasl/slv042`](http://doi.org/10.1093/mnrasl/slv042)

(ref: gilli2019) Gilli, R., Mignoli, M., Peca, A., et al. 2019, A&A, 632, A26, doi: [`10.1051/0004-6361/201936121`](http://doi.org/10.1051/0004-6361/201936121)

(ref: gloudemans2022) Gloudemans, A. J., Duncan, K. J., Saxena, A., et al. 2022, A&A, 668, A27, doi: [`10.1051/0004-6361/202244763`](http://doi.org/10.1051/0004-6361/202244763)

(ref: guillard2015) Guillard, P., Boulanger, F., Lehnert, M. D., et al. 2015, A&A, 574, A32, doi: [`10.1051/0004-6361/201423612`](http://doi.org/10.1051/0004-6361/201423612)

(ref: gullberg2015) Gullberg, B., De Breuck, C., Vieira, J. D., et al. 2015, MNRAS, 449, 2883, doi: [`10.1093/mnras/stv372`](http://doi.org/10.1093/mnras/stv372)

(ref: hale2021) Hale, C. L., McConnell, D., Thomson, A. J. M., et al. 2021, PASA, 38, e058, doi: [`10.1017/pasa.2021.47`](http://doi.org/10.1017/pasa.2021.47)

(ref: hatch2014) Hatch, N. A., Wylezalek, D., Kurk, J. D., et al. 2014, MNRAS, 445, 280, doi: [`10.1093/mnras/stu1725`](http://doi.org/10.1093/mnras/stu1725)

(ref: helou1988) Helou, G., Khan, I. R., Malek, L., & Boehmer, L. 1988, ApJS, 68, 151, doi: [`10.1086/191285`](http://doi.org/10.1086/191285)

(ref: herreracamus2015) Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1, doi: [`10.1088/0004-637X/800/1/1`](http://doi.org/10.1088/0004-637X/800/1/1)

(ref: ighina2021) Ighina, L., Belladitta, S., Caccianiga, A., et al. 2021, A&A, 647, L11, doi: [`10.1051/0004-6361/202140362`](http://doi.org/10.1051/0004-6361/202140362)

(ref: ighina2024) Ighina, L., Caccianiga, A., Moretti, A., et al. 2024, A&A, 687, A242, doi: [`10.1051/0004-6361/202449369`](http://doi.org/10.1051/0004-6361/202449369)

(ref: itema2017) Intema, H. T., Jagannathan, P., Mooley, K. P., & Frail, D. A. 2017, A&A, 598, A78, doi: [`10.1051/0004-6361/201628536`](http://doi.org/10.1051/0004-6361/201628536)

(ref: izumi2018) Izumi, T., Onoue, M., Shirakata, H., et al. 2018, Publications of the Astronomical Society of Japan, 70, 36, doi: [`10.1093/pasj/psy026`](http://doi.org/10.1093/pasj/psy026)

(ref: izumi2019) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2019, PASJ, 71, 111, doi: [`10.1093/pasj/psz096`](http://doi.org/10.1093/pasj/psz096)

(ref: izumi2021) —. 2021, ApJ, 908, 235, doi: [`10.3847/1538-4357/abd7ef`](http://doi.org/10.3847/1538-4357/abd7ef)

(ref: jaffe1973) Jaffe, W. J., & Perola, G. C. 1973, A&A, 26, 423

(ref: jiang2007) Jiang, L., Fan, X., Ivezić, Ž., et al. 2007, ApJ, 656, 680, doi: [`10.1086/510831`](http://doi.org/10.1086/510831)

(ref: jiang2009) Jiang, L., Fan, X., Bian, F., et al. 2009, AJ, 138, 305, doi: [`10.1088/0004-6256/138/1/305`](http://doi.org/10.1088/0004-6256/138/1/305)

(ref: kaasinen2024) Kaasinen, M., Venemans, B., Harrington, K. C., et al. 2024, A&A, 684, A33, doi: [`10.1051/0004-6361/202348463`](http://doi.org/10.1051/0004-6361/202348463)

(ref: kamenetzky2016) Kamenetzky, J., Rangwala, N., Glenn, J., Maloney, P. R., & Conley, A. 2016, ApJ, 829, 93, doi: [`10.3847/0004-637X/829/2/93`](http://doi.org/10.3847/0004-637X/829/2/93)

(ref: kellerman1989) Kellermann, K. I., Sramek, R., Schmidt, M., Shaffer, D. B., & Green, R. 1989, AJ, 98, 1195, doi: [`10.1086/115207`](http://doi.org/10.1086/115207)

(ref: kennicutt2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: khusanova2022) Khusanova, Y., Bañados, E., Mazzucchelli, C., et al. 2022, A&A, 664, A39, doi: [`10.1051/0004-6361/202243660`](http://doi.org/10.1051/0004-6361/202243660)

(ref: krezinger2024) Krezinger, M., Baldini, G., Giroletti, M., et al. 2024, A&A, 690, A321, doi: [`10.1051/0004-6361/202451025`](http://doi.org/10.1051/0004-6361/202451025)

(ref: lai2022) Lai, S., Bian, F., Onken, C. A., et al. 2022, MNRAS, 513, 1801, doi: [`10.1093/mnras/stac1001`](http://doi.org/10.1093/mnras/stac1001)

(ref: langer2015) Langer, W. D., & Pineda, J. L. 2015, A&A, 580, A5, doi: [`10.1051/0004-6361/201525950`](http://doi.org/10.1051/0004-6361/201525950)

(ref: li2024) Li, J., Wang, R., Pensabene, A., et al. 2024, ApJ, 962, 119, doi: [`10.3847/1538-4357/ad1754`](http://doi.org/10.3847/1538-4357/ad1754)

(ref: liu2021) Liu, Y., Wang, R., Momjian, E., et al. 2021, ApJ, 908, 124, doi: [`10.3847/1538-4357/abd3a8`](http://doi.org/10.3847/1538-4357/abd3a8)

(ref: maiolino2005) Maiolino, R., Cox, P., Caselli, P., et al. 2005, A&A, 440, L51, doi: [`10.1051/0004-6361:200500165`](http://doi.org/10.1051/0004-6361:200500165)

(ref: malhotra2001) Malhotra, S., Kaufman, M. J., Hollenbach, D., et al. 2001, ApJ, 561, 766, doi: [`10.1086/323046`](http://doi.org/10.1086/323046)

(ref: marshall2020) Marshall, M. A., Mechtley, M., Windhorst, R. A., et al. 2020, ApJ, 900, 21, doi: [`10.3847/1538-4357/abaa4c`](http://doi.org/10.3847/1538-4357/abaa4c)

(ref: marshall2023) Marshall, M. A., Perna, M., Willott, C. J., et al. 2023, A&A, 678, A191, doi: [`10.1051/0004-6361/202346113`](http://doi.org/10.1051/0004-6361/202346113)

(ref: matsuoka2018) Matsuoka, Y., Iwasawa, K., Onoue, M., et al. 2018, ApJS, 237, 5, doi: [`10.3847/1538-4365/aac724`](http://doi.org/10.3847/1538-4365/aac724)

(ref: mazzucchelli2017b) Mazzucchelli, C., Bañados, E., Venemans, B. P., et al. 2017, ApJ, 849, 91, doi: [`10.3847/1538-4357/aa9185`](http://doi.org/10.3847/1538-4357/aa9185)

(ref: mazzucchelli2019) Mazzucchelli, C., Decarli, R., Farina, E. P., et al. 2019, ApJ, 881, 163, doi: [`10.3847/1538-4357/ab2f75`](http://doi.org/10.3847/1538-4357/ab2f75)

(ref: mazzucchelli2023) Mazzucchelli, C., Bischetti, M., D’Odorico, V., et al. 2023, A&A, 676, A71, doi: [`10.1051/0004-6361/202346317`](http://doi.org/10.1051/0004-6361/202346317)

(ref: mcconnell2020) McConnell, D., Hale, C. L., Lenc, E., et al. 2020, PASA, 37, e048, doi: [`10.1017/pasa.2020.41`](http://doi.org/10.1017/pasa.2020.41)

(ref: mechtley2012) Mechtley, M., Windhorst, R. A., Ryan, R. E., et al. 2012, ApJL, 756, L38, doi: [`10.1088/2041-8205/756/2/L38`](http://doi.org/10.1088/2041-8205/756/2/L38)

(ref: Meenakshi2022) Meenakshi, M., Mukherjee, D., Wagner, A. Y., et al. 2022, MNRAS, 516, 766, doi: [`10.1093/mnras/stac2251`](http://doi.org/10.1093/mnras/stac2251)

(ref: meyer2019) Meyer, R. A., Bosman, S. E. I., & Ellis, R. S. 2019, MNRAS, 487, 3305, doi: [`10.1093/mnras/stz1504`](http://doi.org/10.1093/mnras/stz1504)

(ref: meyer2022a) Meyer, R. A., Walter, F., Cicone, C., et al. 2022a, ApJ, 927, 152, doi: [`10.3847/1538-4357/ac4e94`](http://doi.org/10.3847/1538-4357/ac4e94)

(ref: meyer2022b) Meyer, R. A., Decarli, R., Walter, F., et al. 2022b, ApJ, 927, 141, doi: [`10.3847/1538-4357/ac4f67`](http://doi.org/10.3847/1538-4357/ac4f67)

(ref: molyneux2024) Molyneux, S. J., Calistro Rivera, G., De Breuck, C., et al. 2024, MNRAS, 527, 4420, doi: [`10.1093/mnras/stad3133`](http://doi.org/10.1093/mnras/stad3133)

(ref: momjian2021) Momjian, E., Bañados, E., Carilli, C. L., Walter, F., & Mazzucchelli, C. 2021, AJ, 161, 207, doi: [`10.3847/1538-3881/abe6ae`](http://doi.org/10.3847/1538-3881/abe6ae)

(ref: momjian2018) Momjian, E., Carilli, C. L., Bañados, E., Walter, F., & Venemans, B. P. 2018, ApJ, 861, 86, doi: [`10.3847/1538-4357/aac76f`](http://doi.org/10.3847/1538-4357/aac76f)

(ref: morganti2015) Morganti, R., Oosterloo, T., Oonk, J. B. R., Frieswijk, W., & Tadhunter, C. 2015, A&A, 580, A1, doi: [`10.1051/0004-6361/201525860`](http://doi.org/10.1051/0004-6361/201525860)

(ref: murthy2022) Murthy, S., Morganti, R., Wagner, A. Y., et al. 2022, Nature Astronomy, 6, 488, doi: [`10.1038/s41550-021-01596-6`](http://doi.org/10.1038/s41550-021-01596-6)

(ref: neeleman2021) Neeleman, M., Novak, M., Venemans, B. P., et al. 2021, ApJ, 911, 141, doi: [`10.3847/1538-4357/abe70f`](http://doi.org/10.3847/1538-4357/abe70f)

(ref: nguyen2020) Nguyen, N. H., Lira, P., Trakhtenbrot, B., et al. 2020, ApJ, 895, 74, doi: [`10.3847/1538-4357/ab8bd3`](http://doi.org/10.3847/1538-4357/ab8bd3)

(ref: novak2019) Novak, M., Bañados, E., Decarli, R., et al. 2019, ApJ, 881, 63, doi: [`10.3847/1538-4357/ab2beb`](http://doi.org/10.3847/1538-4357/ab2beb)

(ref: novak2020) Novak, M., Venemans, B. P., Walter, F., et al. 2020, ApJ, 904, 131, doi: [`10.3847/1538-4357/abc33f`](http://doi.org/10.3847/1538-4357/abc33f)

(ref: onoue2020) Onoue, M., Bañados, E., Mazzucchelli, C., et al. 2020, ApJ, 898, 105, doi: [`10.3847/1538-4357/aba193`](http://doi.org/10.3847/1538-4357/aba193)

(ref: onoue2024) Onoue, M., Ding, X., Silverman, J. D., et al. 2024, arXiv e-prints, arXiv:2409.07113, doi: [`10.48550/arXiv.2409.07113`](http://doi.org/10.48550/arXiv.2409.07113)

(ref: overzier2022) Overzier, R. A. 2022, ApJ, 926, 114, doi: [`10.3847/1538-4357/ac448c`](http://doi.org/10.3847/1538-4357/ac448c)

(ref: pacucci2024) Pacucci, F., & Loeb, A. 2024, ApJ, 964, 154, doi: [`10.3847/1538-4357/ad3044`](http://doi.org/10.3847/1538-4357/ad3044)

(ref: paris2018) Pâris, I., Petitjean, P., Aubourg, É., et al. 2018, A&A, 613, A51, doi: [`10.1051/0004-6361/201732445`](http://doi.org/10.1051/0004-6361/201732445)

(ref: pensabene2020) Pensabene, A., Carniani, S., Perna, M., et al. 2020, A&A, 637, A84, doi: [`10.1051/0004-6361/201936634`](http://doi.org/10.1051/0004-6361/201936634)

(ref: pensabene2021) Pensabene, A., Decarli, R., Bañados, E., et al. 2021, A&A, 652, A66, doi: [`10.1051/0004-6361/202039696`](http://doi.org/10.1051/0004-6361/202039696)

(ref: reed2019) Reed, S. L., Banerji, M., Becker, G. D., et al. 2019, MNRAS, 487, 1874, doi: [`10.1093/mnras/stz1341`](http://doi.org/10.1093/mnras/stz1341)

(ref: roche2014) Roche, N., Humphrey, A., & Binette, L. 2014, MNRAS, 443, 3795, doi: [`10.1093/mnras/stu1430`](http://doi.org/10.1093/mnras/stu1430)

(ref: rojas2021) Rojas-Ruiz, S., Bañados, E., Neeleman, M., et al. 2021, ApJ, 920, 150, doi: [`10.3847/1538-4357/ac1a13`](http://doi.org/10.3847/1538-4357/ac1a13)

(ref: rybak2019) Rybak, M., Calistro Rivera, G., Hodge, J. A., et al. 2019, ApJ, 876, 112, doi: [`10.3847/1538-4357/ab0e0f`](http://doi.org/10.3847/1538-4357/ab0e0f)

(ref: salome2015) Salomé, Q., Salomé, P., & Combes, F. 2015, A&A, 574, A34, doi: [`10.1051/0004-6361/201424932`](http://doi.org/10.1051/0004-6361/201424932)

(ref: sargsyan2014) Sargsyan, L., Samsonyan, A., Lebouteiller, V., et al. 2014, ApJ, 790, 15, doi: [`10.1088/0004-637X/790/1/15`](http://doi.org/10.1088/0004-637X/790/1/15)

(ref: sargsyan2012) Sargsyan, L., Lebouteiller, V., Weedman, D., et al. 2012, ApJ, 755, 171, doi: [`10.1088/0004-637X/755/2/171`](http://doi.org/10.1088/0004-637X/755/2/171)

(ref: sbarrato2022) Sbarrato, T., Ghisellini, G., Tagliaferri, G., et al. 2022, A&A, 663, A147, doi: [`10.1051/0004-6361/202243569`](http://doi.org/10.1051/0004-6361/202243569)

(ref: schindler2020) Schindler, J.-T., Farina, E. P., Bañados, E., et al. 2020, ApJ, 905, 51, doi: [`10.3847/1538-4357/abc2d7`](http://doi.org/10.3847/1538-4357/abc2d7)

(ref: schneider2010) Schneider, D. P., Richards, G. T., Hall, P. B., et al. 2010, AJ, 139, 2360, doi: [`10.1088/0004-6256/139/6/2360`](http://doi.org/10.1088/0004-6256/139/6/2360)

(ref: shao2020) Shao, Y., Wagg, J., Wang, R., et al. 2020, A&A, 641, A85, doi: [`10.1051/0004-6361/202038469`](http://doi.org/10.1051/0004-6361/202038469)

(ref: shao2022) —. 2022, A&A, 659, A159, doi: [`10.1051/0004-6361/202142489`](http://doi.org/10.1051/0004-6361/202142489)

(ref: silk2013) Silk, J. 2013, ApJ, 772, 112, doi: [`10.1088/0004-637X/772/2/112`](http://doi.org/10.1088/0004-637X/772/2/112)

(ref: pinchukova2019) Smirnova-Pinchukova, I., Husemann, B., Busch, G., et al. 2019, A&A, 626, L3, doi: [`10.1051/0004-6361/201935577`](http://doi.org/10.1051/0004-6361/201935577)

(ref: stacey2010) Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010, ApJ, 724, 957, doi: [`10.1088/0004-637X/724/2/957`](http://doi.org/10.1088/0004-637X/724/2/957)

(ref: stone2023a) Stone, M. A., Lyu, J., Rieke, G. H., & Alberts, S. 2023, ApJ, 953, 180, doi: [`10.3847/1538-4357/acebe0`](http://doi.org/10.3847/1538-4357/acebe0)

(ref: stone2024) Stone, M. A., Lyu, J., Rieke, G. H., Alberts, S., & Hainline, K. N. 2024, ApJ, 964, 90, doi: [`10.3847/1538-4357/ad2a57`](http://doi.org/10.3847/1538-4357/ad2a57)

(ref: sutter2021) Sutter, J., Dale, D. A., Sandstrom, K., et al. 2021, MNRAS, 503, 911, doi: [`10.1093/mnras/stab490`](http://doi.org/10.1093/mnras/stab490)

(ref: trakhtenbrot2017) Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 8, doi: [`10.3847/1538-4357/836/1/8`](http://doi.org/10.3847/1538-4357/836/1/8)

(ref: uzgil2021) Uzgil, B. D., Oesch, P. A., Walter, F., et al. 2021, ApJ, 912, 67, doi: [`10.3847/1538-4357/abe86b`](http://doi.org/10.3847/1538-4357/abe86b)

(ref: vayner2023) Vayner, A., Zakamska, N. L., Ishikawa, Y., et al. 2023, ApJ, 955, 92, doi: [`10.3847/1538-4357/ace784`](http://doi.org/10.3847/1538-4357/ace784)

(ref: venemans2016) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, ApJ, 816, 37, doi: [`10.3847/0004-637X/816/1/37`](http://doi.org/10.3847/0004-637X/816/1/37)

(ref: venemans2007) Venemans, B. P., Röttgering, H. J. A., Miley, G. K., et al. 2007, A&A, 461, 823, doi: [`10.1051/0004-6361:20053941`](http://doi.org/10.1051/0004-6361:20053941)

(ref: venemans2017c) Venemans, B. P., Walter, F., Decarli, R., et al. 2017a, ApJL, 851, L8, doi: [`10.3847/2041-8213/aa943a`](http://doi.org/10.3847/2041-8213/aa943a)

(ref: venemans2017b) —. 2017b, ApJ, 845, 154, doi: [`10.3847/1538-4357/aa81cb`](http://doi.org/10.3847/1538-4357/aa81cb)

(ref: venemans2018) Venemans, B. P., Decarli, R., Walter, F., et al. 2018, ApJ, 866, 159, doi: [`10.3847/1538-4357/aadf35`](http://doi.org/10.3847/1538-4357/aadf35)

(ref: venemans2020) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130, doi: [`10.3847/1538-4357/abc563`](http://doi.org/10.3847/1538-4357/abc563)

(ref: venturi2023) Venturi, G., Treister, E., Finlez, C., et al. 2023, A&A, 678, A127, doi: [`10.1051/0004-6361/202347375`](http://doi.org/10.1051/0004-6361/202347375)

(ref: villarmartin2014) Villar Martı́n, M., Emonts, B., Humphrey, A., Cabrera Lavers, A., & Binette, L. 2014, MNRAS, 440, 3202, doi: [`10.1093/mnras/stu448`](http://doi.org/10.1093/mnras/stu448)

(ref: walter2009) Walter, F., Riechers, D., Cox, P., et al. 2009, Nature, 457, 699, doi: [`10.1038/nature07681`](http://doi.org/10.1038/nature07681)

(ref: walter2016) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67, doi: [`10.3847/1538-4357/833/1/67`](http://doi.org/10.3847/1538-4357/833/1/67)

(ref: wangf2019) Wang, F., Wang, R., Fan, X., et al. 2019, ApJ, 880, 2, doi: [`10.3847/1538-4357/ab2717`](http://doi.org/10.3847/1538-4357/ab2717)

(ref: wangf2021) Wang, F., Yang, J., Fan, X., et al. 2021, ApJL, 907, L1, doi: [`10.3847/2041-8213/abd8c6`](http://doi.org/10.3847/2041-8213/abd8c6)

(ref: wangf2024) —. 2024a, ApJ, 968, 9, doi: [`10.3847/1538-4357/ad3fb4`](http://doi.org/10.3847/1538-4357/ad3fb4)

(ref: wang2010) Wang, R., Carilli, C. L., Neri, R., et al. 2010, ApJ, 714, 699, doi: [`10.1088/0004-637X/714/1/699`](http://doi.org/10.1088/0004-637X/714/1/699)

(ref: wang2013) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44, doi: [`10.1088/0004-637X/773/1/44`](http://doi.org/10.1088/0004-637X/773/1/44)

(ref: wang2016) Wang, R., Wu, X.-B., Neri, R., et al. 2016, ApJ, 830, 53, doi: [`10.3847/0004-637X/830/1/53`](http://doi.org/10.3847/0004-637X/830/1/53)

(ref: wangw2024) Wang, W., Wylezalek, D., De Breuck, C., et al. 2024b, A&A, 683, A169, doi: [`10.1051/0004-6361/202348531`](http://doi.org/10.1051/0004-6361/202348531)

(ref: wenzl2021) Wenzl, L., Schindler, J.-T., Fan, X., et al. 2021, AJ, 162, 72, doi: [`10.3847/1538-3881/ac0254`](http://doi.org/10.3847/1538-3881/ac0254)

(ref: willott2015) Willott, C. J., Bergeron, J., & Omont, A. 2015, ApJ, 801, 123, doi: [`10.1088/0004-637X/801/2/123`](http://doi.org/10.1088/0004-637X/801/2/123)

(ref: willott2017) —. 2017, ApJ, 850, 108, doi: [`10.3847/1538-4357/aa921b`](http://doi.org/10.3847/1538-4357/aa921b)

(ref: willott2013b) Willott, C. J., Omont, A., & Bergeron, J. 2013, ApJ, 770, 13, doi: [`10.1088/0004-637X/770/1/13`](http://doi.org/10.1088/0004-637X/770/1/13)

(ref: wright2010) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: wylezalek2013) Wylezalek, D., Galametz, A., Stern, D., et al. 2013, ApJ, 769, 79, doi: [`10.1088/0004-637X/769/1/79`](http://doi.org/10.1088/0004-637X/769/1/79)

(ref: wylezalek2022) Wylezalek, D., Vayner, A., Rupke, D. S. N., et al. 2022, ApJL, 940, L7, doi: [`10.3847/2041-8213/ac98c3`](http://doi.org/10.3847/2041-8213/ac98c3)

(ref: xu2018) Xu, F., Bian, F., Shen, Y., et al. 2018, MNRAS, 480, 345, doi: [`10.1093/mnras/sty1763`](http://doi.org/10.1093/mnras/sty1763)

(ref: yang2019) Yang, J., Wang, F., Fan, X., et al. 2019a, AJ, 157, 236, doi: [`10.3847/1538-3881/ab1be1`](http://doi.org/10.3847/1538-3881/ab1be1)

(ref: yangj2019) Yang, J., Venemans, B., Wang, F., et al. 2019b, ApJ, 880, 153, doi: [`10.3847/1538-4357/ab2a02`](http://doi.org/10.3847/1538-4357/ab2a02)

(ref: yang2020) Yang, J., Wang, F., Fan, X., et al. 2020, ApJL, 897, L14, doi: [`10.3847/2041-8213/ab9c26`](http://doi.org/10.3847/2041-8213/ab9c26)

(ref: yang2021) —. 2021, ApJ, 923, 262, doi: [`10.3847/1538-4357/ac2b32`](http://doi.org/10.3847/1538-4357/ac2b32)

(ref: yang2023) Yang, J., Fan, X., Gupta, A., et al. 2023, ApJS, 269, 27, doi: [`10.3847/1538-4365/acf99b`](http://doi.org/10.3847/1538-4365/acf99b)

(ref: yi2014) Yi, W.-M., Wang, F., Wu, X.-B., et al. 2014, ApJL, 795, L29, doi: [`10.1088/2041-8205/795/2/L29`](http://doi.org/10.1088/2041-8205/795/2/L29)

(ref: yue2024) Yue, M., Eilers, A.-C., Simcoe, R. A., et al. 2024, ApJ, 966, 176, doi: [`10.3847/1538-4357/ad3914`](http://doi.org/10.3847/1538-4357/ad3914)

(ref: zanella2018) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976, doi: [`10.1093/mnras/sty2394`](http://doi.org/10.1093/mnras/sty2394)

(ref: zeimann2011) Zeimann, G. R., White, R. L., Becker, R. H., et al. 2011, ApJ, 736, 57, doi: [`10.1088/0004-637X/736/1/57`](http://doi.org/10.1088/0004-637X/736/1/57)

(ref: zheng2006) Zheng, W., Overzier, R. A., Bouwens, R. J., et al. 2006, ApJ, 640, 574, doi: [`10.1086/500167`](http://doi.org/10.1086/500167)

(ref: Zhong2024) Zhong, Y., Inoue, A. K., Sugahara, Y., et al. 2024, MNRAS, 529, 4531, doi: [`10.1093/mnras/stae798`](http://doi.org/10.1093/mnras/stae798)

# Velocity maps

We report here the continuum-subtracted \[C II\]  velocity maps of the RL quasars (see Figure [11](#fig:ciimapmom0)). We obtained these maps using the CASA task *immoments* with moments=1. We observe different kinematics: the majority of the quasars seem to be characterized by a uniform velocity fields, some with low velocities (e.g. PSO135+16, PSO352-15), another with velocities around $\sim -$200 km s$^{-1}$ (J1034+2033) and finally PSO055-00 characterized by very high velocities, up to $\sim$800 km s$^{-1}$. On the other hand, J0131-0321 seem to present more complex features, with a potential disk-like structure, with velocities between +400/$-$250 km $^{-1}$, and an elongated morphology. However, due to the low spatial resolution and limited SNR, more robust conclusions on the kinematical structure of our sources cannot be drawn. Further, higher resolution and SNR observations are necessary to firmly pin-point the velocity structures of high$-z$ RL quasars.

![](fig_mom1map_062022.pdf)

[^1]: email: chiara.mazzucchelli@mail.udp.cl

[^2]: At the time of observations, J2053+0047 was miss-classified as RL, see Section [2](#sec:sampobs) for more details.

[^3]: We considered here the redshift from visual inspection and as uncertainty the corresponding dispersion of Z_VI - Z_MGII. All the other redshift measurements in this case are consistent with the reported value within the uncertainty.

[^4]: [https://data.csiro.au/domain/casda ](https://data.csiro.au/domain/casda )

[^5]: With the python implementation provided in the interferopy package: <https://interferopy.readthedocs.io/en/latest/index.html>, (cite: boogaard2021).

[^6]: We note that changing this limit to $\Delta v > \pm 2000$ km s$^{-1}$ does not change our final resuls.

[^7]: We note that our data is shallower, by a factor of $\sim$3, than those used to determine the blank field number density.

</paper>

Write the methods card for this paper.