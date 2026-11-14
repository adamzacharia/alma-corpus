# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A.275B\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...686A.275B",
 "title": "Proper motion study of the 6.7 GHz methanol maser rings. I. A sample of sources with little variation",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Bartkiewicz, A.",
 "n_authors": 8,
 "arxiv_id": "2404.07333",
 "doi": "10.1051/0004-6361/202449491",
 "alma_projects_linked_by_archive": [
  "2019.1.00195.L"
 ]
}
```

Paper text:
<paper>
# Proper motion study of the 6.7 GHz methanol maser rings.

Methanol masers at 6.7 GHz are well-known signposts of high-mass star-forming regions. Due to their high brightness, they enable us to derive the three-dimensional gas kinematics near protostars and young stars.

We aim to understand the origin of the ring-like structures outlined by methanol maser emission in a number of sources. This emission could be, a priori, spatially associated with an outflow and/or disc around a high-mass protostar. In cases of expansion or rotation, maser proper motions should be, for instance, diverging from the ring centre or perpendicular to the ring radius.

Using sensitive, three-epoch observations spanning over eight years with the European VLBI Network, we have started the most direct investigations of maser rings using very accurate proper motion measurements with uncertainties below $\sim$1 km s$^{-1}$.

We present full results for the five targets of our sample, G23.207$-$00.377, G23.389$+$00.185, G28.817$+$00.365, G31.047$+$00.356, and G31.581$+$00.077, where proper motions show similar characteristics; maser cloudlets do not move inwards towards the centre of the rings but rather outwards. We also include the most circular source, G23.657$-$00.127, in the discussion as a reference.

The magnitude of maser proper motions ranges from a maximum of about 13 km s$^{-1}$ to 0.5 km s$^{-1}$. In two of the five sources with a high number of maser spots ($>$ 100), namely G23.207$-$00.377 and G23.389$+$00.185, we show that the size of the best elliptical model, fitted to the distribution of persistent masers, increases in time in a manner similar to the case of G23.657$-$00.127. Moreover, we checked the separations between the pairs of spots from distinct regions, and we were able to assess that G28.817$+$00.365 and G31.047$+$00.356 can be interpreted as showing expanding motions. We analysed the profiles of single maser cloudlets and studied their variability. Contrary to single-dish studies, the interferometric data indicate variability of the emission of single-masing cloudlets.

In five of the six targets, namely, G23.207$-$00.377, G23.389$+$00.185, G23.657$-$00.127, G28.817$+$00.365, and G31.047$+$00.356, expansion motions prevail. Only in the case of G31.581$+$00.077 can a scenario of disc-like rotation not be excluded. Complementary observations of thermal tracers as well as searching for ultra-compact H II regions in the same sources are needed. Although the overall morphology of the maser emission has remained stable, the intensities of individual maser cloudlets varied from epoch to epoch, suggesting internal instabilities.

# Introduction

Young high-mass stars with masses larger than 8 M$_{\odot}$ form inside star-forming regions, and they are still challenging targets in modern astrophysics, as they are distant (distances of a few kiloparsecs), obscured at optical and near-infrared wavelengths, and evolve on short timescales. These massive young stellar objects (MYSOs) can be studied by means of 6.7 GHz methanol maser observations (cite: m91) because this line has been found to uniquely trace their environment (e.g. (cite: br13) and references therein). Very long baseline interferometry (VLBI) allows us to derive the detailed spatial structure of methanol maser emission at milliarcsecond resolution (e.g. (cite: mos11), (cite: mosmas11), (cite: n2023)) and investigate the small (a few astronomical units) regions of neutral gas in the vicinity of MYSOs (at radii of 1000s AU). Since the first VLBI observations of the 6.7 GHz methanol maser emission almost three decades ago, maser spots have been shown to be found in diverse structures. These structures can consist of a few or many maser spots, having either linear or arched spatial distributions, which often show regular velocity gradients as well (e.g. (cite: n93), (cite: p98), (cite: w98), (cite: m00)). With the increase of the VLBI sensitivity, ring-like structures were also discovered ((cite: b09), (cite: t11), (cite: f14)). However, the general question about where the methanol maser emission arises has not yet been answered. Recently, proper motion studies using VLBI data have added further information to address this question. Such observations provide the most direct measurements of the gas kinematics near MYSOs, although long time baselines are required – typically of a few years – to trace shifts on the order of a few milliarcseconds for a single maser spot.

A series of works by (cite: mos00; mos05; mos07; mos11) demonstrated the ability of water masers to trace 3D velocities of gas, which usually expands from MYSOs at several 10 km s$^{-1}$. Towards two MYSOs, G16.59$-$0.05 and G23.01$-$0.41, (cite: s10a; s10b) also reported accurate multi-epoch proper motion measurements of the 6.7 GHz masers for the first time, using a time baseline of two years. This maser emission arises close to the central protostar (within 1000 AU) and traces gas either rotating and/or expanding with mean (transverse) velocities of 6–7 km s$^{-1}$. Similarly, (cite: mosmas11) showed that the methanol masers in IRAS 20126$+$4104 are associated with a rotating disc while also moving in the direction of the jet axis. A special case was further discovered in AFGL 5142, where the methanol masers provided a direct measurement of gas infall within a radius of 300 AU from an intermediate-mass protostar ((cite: g11)). In Cepheus A HW2, the velocity field is dominated by an infall component of about 2 km s$^{-1}$ down to a radius of 300 AU, where a rotational component of 4 km s$^{-1}$ becomes dominant, as revealed by the 6.7 GHz methanol maser studies ((cite: t11), (cite: s14), (cite: s17)).

The following project aims to measure the proper motions of those 6.7 GHz methanol masers distributed along ring-like structures. We selected twelve objects from our sample of 31 sources that were observed from 2004 to 2007 by (cite: b09) using the European VLBI Network[^1] (EVN) and repeated the observations with a similar setup in 2013 and 2015. Since 6.7 GHz methanol masers typically trace gas velocities of less than 10 km s$^{-1}$ and the targets in our sample have distances within about 4 kpc from the Sun, one would expect to detect position shifts of  3 mas after six years. These angular shifts are about half the EVN beam size and are easily detectable when there is a sufficient signal-to-noise ratio (S/N).

In this paper, we present proper motion results for five of the 12 sources in our sample. The first sub-sample concerns targets whose ring-like morphology was stable and where we identified persistent spots distributed along the whole structure over about eight years. Single-dish monitoring showed little or no variation of the 6.7 GHz line emission towards the same targets (cite: sz18). Another source, G23.657-00.127, showing a nearly circular morphology, also belongs to this sub-sample but was analysed and described in detail in (cite: b20). Here, we also include some results of G23.657$-$00.127 for completeness.

# Observations and data reduction

The observations of the 6668.519 MHz methanol maser line taken from 2004 to 2007 are described in (cite: b09) and are referred to here as epoch 1 (hereafter E1). The observations for epoch 2 and epoch 3 (hereafter E2 and E3, respectively) were carried out using the EVN on March 2013 and 2015 (Table [\[table1\]](#table1)). Data were obtained from the following antennas: Jodrell Bank, Effelsberg, Medicina, Onsala, Noto, Torun, Westerbork, and Yebes. Details of the observations, such as pointing positions of the targets, phase calibrators, and exact dates of observations for the five masers, are given in Table [\[table1\]](#table1). Each observing run lasted for 9 hours. The phase-referencing mode was used, repeating a loop of 5 min between the maser target (3.25 min) and a phase calibrator from the VLBA Calibrator List (1.75 min). The calibrator 3C345 was observed during a few 15-min scans at each run; these scans were used to calibrate the bandpass and instrumental phases. Three maser sources were observed in each 9-hr run; these targets were selected to be within a few degrees of each other, in projection on the sky, and of similar maser emission velocities (Table [\[table1\]](#table1)). This process yielded the on-source time for each maser of ca. 1.5 hr. The SFXC software correlator in JIVE was used with a 2-second integration time (cite: k15). Selection of 1024 channels in the 2 MHz bandwidth resulted in a 0.1 km s$^{-1}$ resolution. To increase S/N on the phase-reference source, eight 2-MHz BBCs per polarisation were used for a second correlator pass with 128 channels per BBC.

The data reduction was carried out with the Astronomical Image Processing System (AIPS) developed by the National Radio Astronomy Observatory (NRAO) with standard procedures for spectral line observations. The Effelsberg antenna was set as the reference. As we aimed for detailed internal motion studies of masers and relied on the relative motions, fringe fitting (task FRING) was performed on the strongest maser channel from the first-epoch observations (cite: b09). This allowed us to exclude motions due to annual parallax and Galactic rotation and also provided the highest possible S/N to get the most accurate measurements of the relative positions. To obtain the positions of the methanol maser spots in all channel maps, we used the AIPS tasks JMFIT or SAD (depending on the number of spots per source) fitting two-dimensional Gaussian models to the compact maser emission. The formal fitting errors were typically less than 0.1 mas per spot.

The rms noise level (1$\sigma_{\rm rms}$) in line-free channels was typically 4 or 6 mJy for each source, and we searched for maser emission above a threshold of 7$\sigma_{\rm rms}$ in each channel map. The synthesised beams, obtained with natural weightings in E2, are also listed in Table [\[table1\]](#table1).

+:-------------------+:---------------+:---------------------+:-------------------:+:----------------:+:-------------------------------------------:+:------------------------------:+
| Source$^{a}$       | Pointing positions (J2000)            | Velocity            | Phase-calibrator | Observing                                   | Synthesised beam$^{c}$         |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
|                    |                |                      | peak                |                  | runs$^{b}$ (and 1$\sigma_{\rm rms}$ levels) |                                |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
| Gll.lll$\pm$bb.bbb | RA (h:m:s)     | Dec ($^{\rm o}$:’:”) | $({\rm km~s}^{-1})$ |                  | (mJy)                                       | (mas$\times$mas; PA($^\circ$)) |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
| G23.207$-$00.377   | 18:34:55.21212 | $-$08:49:11.8926     | 77.1                | J1825$-$0737     | A(4), E(4)                                  | 8.3$\times$4.1; $-$27          |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
| G23.389$+$00.185   | 18:33:14.32477 | $-$08:23:57.4723     | 75.4                | J1825$-$0737     | A(4), E(4)                                  | 8.3$\times$4.1; $-$27          |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
| G23.657$-$00.127   | 18:34:51.56482 | $-$08:18:21.3045     | 82.6                | J1825$-$0737     | A(4), E(4)                                  | 9.0$\times$4.0; $-$28          |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
| G28.817$+$00.365   | 18:42:37.34797 | $-$03:29:40.9216     | 90.7                | J1834$-$0301     | C(4), G(4)                                  | 7.9$\times$4.1; $-$30          |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
| G31.047$+$00.356   | 18:46:43.85506 | $-$01:30:54.1551     | 80.7                | J1834$-$0301     | C(4), G(4)                                  | 7.5$\times$4.1; $-$32          |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+
| G31.581$+$00.077   | 18:48:41.94108 | $-$01:10:02.5281     | 95.6                | J1834$-$0301     | D(6), H(6)                                  | 9.3$\times$5.5; $+$4.7         |
+--------------------+----------------+----------------------+---------------------+------------------+---------------------------------------------+--------------------------------+

Table notes: $^a$ The names are the Galactic coordinates of the brightest maser spots as in (cite: b09). $^b$ The project EB052 was observed in the following runs: A (2/03/2013),

C (4/03/2013), D (5/03/2013), E (15/03/2015),

G (18/03/2015) and H (19/03/2015). $^{c}$ The sizes as in the runs A, C, D carried out in 2013.

## Proper motions measurements

In order to study the proper motion of the masers, we followed the general procedure (method 1): i) First we determined the maser ‘cloudlets’ at each epoch, where a maser cloudlet is defined as a combination of at least three (in rare cases two) maser spots appearing at consecutive spectral channels and coinciding in position within half the synthesised beam (e.g. (cite: s17)). ii) Next, we identified the persistent maser cloudlets over the epochs on the basis of their linear motion with respect to a bright, compact, and spectrally stable feature. Relative proper motions were derived via linear fits of cloudlet displacements over the three epochs. iii) Last, we subtracted the average proper motion of persistent cloudlets from the proper motion of each cloudlet. As a result of this, we defined a centre of motion approximating the MYSO’s rest frame, with respect to which we calculated the proper motions. This is equivalent to calculating the geometric mean of the positions of all persistent maser cloudlets at each epoch and then referring the proper motions to this point. We have already discussed this approach in (cite: b20) for G23.657$-$00.127.

For two targets with a significant number of spots ($>$100), namely G23.207$-$00.377 and G23.389$+$00.185 (as well as in G23.657$-$00.127 as presented in (cite: b20)), we also followed a second approach for the proper motion analysis, taking advantage of the best-fitted ellipses to the maser distribution. This second approach (method 2) involved four steps: i) selection of maser spots that were visible at all three epochs; ii) fitting the flux-weighted ellipses to the selected maser spots at each epoch using the code by (cite: f99); iii) aligning of the centres of best-fitted ellipses with respect to the first epoch; iv) constructing the averaged proper motion vector (i.e. the displacements between pairs of spots within a group were summed and divided by the number of pairs for each group of maser spots that were clearly separated from each other). Assuming that the methanol emission traces an ellipse and that the centre of the ellipse coincides with the MYSO position enabled us to remove any bulk motion of the ring in the plane of the sky and obtain the proper motions of masers relative to MYSO.

As mentioned earlier, the formal fitting errors of maser spot positions were typically negligible, less than 0.1 mas. This evidence strengthens the accuracy of the proper motion measurements. Also, the long time baseline (8-11 yr) of the observations is an advantage of the present study, considering that the targets are at distances of a few kiloparsecs. We assumed in our studies that co-spatial maser spots at the same LSR velocity identified at different epochs trace the same volume of gas. In method 1, we derived the proper motions via linear fits of cloudlet displacements over three epochs. We drew ‘error cones’ for each proper motion vector, as derived from the uncertainty of the linear fits in each direction (RA and Dec). In method 2, we derived the averaged proper motion vectors between E1-E2 and E1-E3 data and drew error cones as a range of these two directions.

## Single-dish monitoring

The whole sample has been monitored with the 32-m Torun radio telescope under the project described in (cite: sz18) in the period 2009-2013. In addition, follow-up observations have been ongoing since early 2018. The spectral resolution was 0.09 km s$^{-1}$ after Hanning smoothing, a typical sensitivity (3$\sigma$) was 0.8 Jy, and the flux density calibration accuracy was about 10%.

# Results

In this section, we present the results for five sources that show similar characteristics in their proper motions and for which the single-dish monitoring showed little or no variation of the 6.7 GHz line (cite: sz18). The archetype ring-like source G23.657$-$00.127 is presented in detail in (cite: b20), and here we only report some characteristics for comparison.

In Fig. [7](#threeepochs) we present the distribution of the 6.7 GHz methanol maser emission (all visible spots at single maser channel maps) at all three epochs of observations. Also, we present the spectra of the cloudlets and analyse their Gaussian profiles. The dynamic spectra of the 6.7 GHz methanol maser variability, obtained using the Torun dish, are presented in Fig. [8](#spectravar). Distances to the targets, derived either from trigonometric parallax measurements or kinematic distances, have been added to Table [1](#ellipses), where the flux-weighted ellipse fits to the distribution of the persisting cloudlets are summarised. The maser cloudlets with derived proper motions are listed in Table [3](#clouds) and presented in Figs [1](#g23207cm)-[5](#g31581cm). One can note that the overall structures in all cases persisted over almost eight years (G28.817$+$00.365, G31.047$+$00.356) or even 10.5 years (G23.207$-$00.377, G23.389$+$00.185, G23.657$-$00.127). In general, displacements of the cloudlets suggest outward motions from the centres of the rings (i.e. fitted ellipses).

![image](bartkiewicz_g23p207_pm_meanvectors.pdf) ![image](bartkiewicz_g23p207_pm_mean.pdf)

For G23.207$-$00.377, the following number of spots were registered during observations in 2004, 2013, and 2015: 218, 219, and 250, respectively (Fig. [7](#threeepochs)). We identified 140 spots that appeared in all three epochs and that can be grouped into 23 cloudlets. These cloudlets show Gaussian profiles (Fig. [7](#threeepochs)) with varying flux densities for most of them between 2004 and 2013 (Table [3](#clouds)). The brightest cloudlet in 2004, at the LSR velocity of 77.1 km s$^{-1}$, decreased by a factor of more than four after 8.5 yr. This is contrary to the results of single-dish monitoring, where the overall emission from this target in recent years (since 2009) shows little spectral variation (Fig. [8](#spectravar); see also (cite: sz18)). In the poor signal-to-noise ratio observations and without any possibility to spatially resolve spectrally blended features, it is impossible to detect single-cloudlet variability. As we stated in (cite: b20), the internal instabilities of the masing regions may reduce the velocity coherence along the path of maser rays and induce flux variations. However, we also note that the difference in the variability patterns from VLBI and the 32-m single-dish monitoring possibly results from the blending effect, as VLBI probes the most compact cloud or the core of the cloudlet.

We selected 20 cloudlets with approximately linear motions over three epochs (with respect to the brightest one) and used them for calculating the average proper motion. The remaining three cloudlets are marked in Table [3](#clouds). Figure [1](#g23207cm) presents the derived proper motions for G23.207$-$00.377. This plot highlights the fact that the majority of cloudlets move outwards from the centroid of their distribution. Their motions range from 0.06 to 0.58 mas yr$^{-1}$, which at a distance of 4.18 kpc (cite: r19) correspond to linear velocities from 1.2 to 11.6 km s$^{-1}$. We calculated the radial and tangential components of the proper motions (Fig. [9](#fig_rot_exp)), and there is a clear outward radial motion in the sky with a mean value of 2.61$\pm$0.09 km s$^{-1}$. The tangential components do not show any consistent rotation pattern. Following method 2 to measure maser proper motions, by aligning the centre of the ellipses at different epochs, we obtained results consistent with method 1 after excluding the blueshifted spots to the SW of the ellipse fit. The major axis of the best-fitted ellipses increased in time, with a linear size of 1072, 1082, and 1084 AU in 2004, 2013, and 2015, respectively (Table [1](#ellipses)), indicating the same outward motion of the masing cloudlets.

![image](bartkiewicz_g23p389_pm_meanvectors.pdf) ![image](bartkiewicz_g23p389_pm_mean.pdf)

For G23.389$+$00.185, 128, 118, and 129 maser spots were found in 2004, 2013, and 2015, respectively. Their elliptical fit shows an elongation towards the NE-SW direction (Fig. [7](#threeepochs)). Seventy-nine spots appeared at all three epochs and are grouped in ten cloudlets. They all showed linear motions and were used to derive the average proper motion relative to the brightest cloudlet at the LSR velocity of 75.338 km s$^{-1}$. The result is presented in Fig. [2](#g23389cm). Proper motions range from 0.02 to 0.7 mas yr$^{-1}$, corresponding to 0.5 to 16.1 km s$^{-1}$ at a distance of 4.8 kpc (cite: r19). Between method 1 and method 2, the results are consistent. The major axis of the best-fitted ellipses increased in time by ca. 30 mas over 10.5 yrs. The radial and tangential components of proper motions calculated in method 1 are presented in Fig. [9](#fig_rot_exp). Again, the outward radial motion dominates, and its mean is 3.4$\pm$0.4 km s$^{-1}$. This source shows little variation in the 6.7 GHz methanol maser emission in recent years (Fig. [8](#spectravar)), as reported by (cite: sz18). However, we detected an overall decrease in the flux density of the brightest spectral features, particularly between 2004 and 2013, and also of the redshifted spectral features (Fig. [7](#threeepochs)). Moreover, the source has recently undergone an outburst, reported by (cite: t23). The spectral features at the LSR velocities of 74.7 and 75.3 km s$^{-1}$ have increased their flux densities to 100 and 120 Jy, respectively. Interferometric observations are needed to properly identify the outbursting region.

In our sample, G23.657$-$00.127 is the target with the most circular and widespread distribution of methanol maser spots. Details were described in (cite: b20), and we summarise them here for completeness of the sub-sample. Radially outward motions were clear, with values from 0.5 to 5.4 km s$^{-1}$ in the sky. Consistent results of radially outward motions were obtained by applying either method 1 or method 2 when we excluded the blueshifted cloudlet to the SW for the ellipse fit. The major axis of the best-fitted ellipses increased about 7 mas over 10.5 yr (Table [1](#ellipses)). Again, the single-dish monitoring of the 6.7 GHz methanol maser spectrum showed non-variable emission over nearly 20 yr within an accuracy of 10%. (cite: sz18). However, our EVN observations revealed significant changes in the intensity of the individual cloudlets over the whole range of velocity.

![](bartkiewicz_g28p817_pm_meanvectors.pdf)

For G28.817$+$00.365, 36, 67, and 80 maser spots were detected in 2007, 2013, and 2015, respectively (Fig. [7](#threeepochs)). Twenty-one of them appeared at all three epochs and are grouped in seven cloudlets. We used five of them that show approximately linear motions to derive the average proper motion (the excluded cloudlets are marked in Table [3](#clouds)). The proper motions are presented in Fig. [3](#g28817cm). They range from 0.07 to 0.6 mas yr $^{-1}$, corresponding to a range from 1.6 to 13.0 km s$^{-1}$ for a kinematic distance of 4.6 kpc (cite: r19). The decomposition of the proper motion velocity vectors into radial and tangential components is presented in Fig. [9](#fig_rot_exp). Due to the small number of cloudlets, the domination of any of these cannot be estimated. The mean radial motion is 3.5$\pm$0.4 km s$^{-1}$. Gaussian profiles of maser cloudlets show that the peak of the brightest one (at the LSR velocity of 90.6 km s$^{-1}$) decreased in time by a factor of three between 2007 and 2013. More complex spectral profiles also appeared in the LSR velocity range 91–92 km s$^{-1}$ between 2007 and 2013. Again, this is opposite to the single-dish monitoring results (Fig. [8](#spectravar); (cite: sz18)).

![](bartkiewicz_g31p047_pm_meanvectors.pdf)

Towards G31.047$+$00.356, 31, 77, and 83 single maser spots were detected in 2007, 2013, and 2015, respectively (Fig. [7](#threeepochs)). Twenty-three spots appeared at all three epochs and are grouped in four cloudlets. Uniquely for this target, we analysed the motions of all single spots because of the significant extension of the western maser emission that would be missed when grouping spots into cloudlets. The brightest spot was spectrally stable (at the LSR velocity of 80.709 km s$^{-1}$) and was selected as a reference. Twenty-one spots showed linear motions and were used for calculating the average proper motion (the two excluded spots are marked in Table [3](#clouds)). Proper motions are presented in Fig. [4](#g31047cm). They range from 0.03 to 0.31 mas yr$^{-1}$, corresponding to a range from 0.7 to 7.1 km s$^{-1}$ for a kinematic distance of 4.9 kpc (cite: r19). Similarly, as in G28.817$+$00.365, the decomposition of proper motion velocity vectors into radial and tangential components does not indicate a dominant expansion or rotation motions (Fig. [9](#fig_rot_exp)). Gaussian profiles of cloudlets between 2007 and 2013 exhibit significant changes (Fig. [7](#threeepochs)), and we did not find any non-variable feature. Also, we noticed that the cloudlet at the LSR velocity of 82.99 km s$^{-1}$ shows the radial motion component of $-$0.10 m s$^{-1}$ yr$^{-1}$. The single-dish monitoring from 2009 did not reveal strong variability, although there is a systematic spectral drift of the redshifted components (Fig. [8](#spectravar)).

![](bartkiewicz_g31p581_pm_meanvectors.pdf)

Towards the source G31.581$+$00.077, 35, 43, and 49 single maser spots were detected in 2007, 2013, and 2015, respectively (Fig. [7](#threeepochs)). Nineteen of them were identified as appearing at all three epochs. They were grouped in eight cloudlets. Six of them showed linear motions and were used to derivate average motions. Proper motions are presented in Fig. [5](#g31581cm), and the decomposition of them into radial and tangential components is presented in Fig. [9](#fig_rot_exp). We did not notice any sign of regularities in them. This source lies at 5.5 kpc, as its trigonometric parallax was measured by (cite: r19). Again, interferometric data show amplitude variability of the spectral features, contrary to the single-dish data (Fig. [7](#threeepochs)).

At this point we can state that the differences in variability patterns based on VLBI and single-dish observations likely result from significant differences in angular resolution (arcmin vs. mas). Detailed studies of radial velocity drifts of single cloudlets combined with the proper motions may uniquely allow the 3D velocities to be estimated.

+:-------------------------+:-----------+:------------+:--------------------------------+
| Source$^{a}$             | Centre$^a$               | Semi-axes; PA$_{\rm major}$$^b$ |
+--------------------------+------------+-------------+---------------------------------+
| Distance                 | $\Delta$RA | $\Delta$Dec |                                 |
+--------------------------+------------+-------------+---------------------------------+
| (kpc)                    | (mas)      | (mas)       | (mas$\times$mas; $^\circ$)      |
+--------------------------+------------+-------------+---------------------------------+
| G23.207$-$00.377         | $-$55.817  | $+$81.207   | 128.33$\times$40.07; $-$48      |
+--------------------------+------------+-------------+---------------------------------+
| 4.18$^c$                 | $-$56.378  | $+$82.097   | 129.48$\times$40.80; $-$48      |
+--------------------------+------------+-------------+---------------------------------+
|                          | $-$56.573  | $+$82.302   | 129.74$\times$40.90; $-$48      |
+--------------------------+------------+-------------+---------------------------------+
|                          |            |             |                                 |
+--------------------------+------------+-------------+---------------------------------+
| G23.389$+$00.185         | $-$39.045  | $-$74.610   | 101.84$\times$51.41, $+$52      |
+--------------------------+------------+-------------+---------------------------------+
| 4.8$^c$                  | $-$40.010  | $-$75.244   | 105.16$\times$51.06; $+$52      |
+--------------------------+------------+-------------+---------------------------------+
|                          | $-$40.023  | $-$75.514   | 105.10$\times$51.18; $+$52      |
+--------------------------+------------+-------------+---------------------------------+
|                          |            |             |                                 |
+--------------------------+------------+-------------+---------------------------------+
| G23.657$-$00.127         | $-$66.058  | $-$96.411   | 134.89$\times$123.94; $-$20     |
+--------------------------+------------+-------------+---------------------------------+
| 3.19$^d$                 | $-$66.379  | $-$96.246   | 136.01$\times$124.49; $-$19     |
+--------------------------+------------+-------------+---------------------------------+
|                          | $-$66.824  | $-$97.350   | 136.06$\times$125.27; $-$19     |
+--------------------------+------------+-------------+---------------------------------+
|                          |            |             |                                 |
+--------------------------+------------+-------------+---------------------------------+
| G28.817$+$00.365         | $-$47.443  | $-$14.272   | 61.53$\times$26.47; $+$53       |
+--------------------------+------------+-------------+---------------------------------+
| 4.6$^e$                  | $-$46.509  | $-$13.680   | 59.77$\times$27.41; $+$53       |
+--------------------------+------------+-------------+---------------------------------+
|                          | $-$46.429  | $-$13.658   | 59.65$\times$27.61; $+$52       |
+--------------------------+------------+-------------+---------------------------------+
|                          |            |             |                                 |
+--------------------------+------------+-------------+---------------------------------+
| G31.047$+$00.356$^\star$ | $-$31.068  | $-$11.355   | 34.28$\times$12.57; $+$63       |
+--------------------------+------------+-------------+---------------------------------+
| 4.9$^e$                  | $-$30.665  | $-$10.780   | 33.54$\times$14.04; $+$63       |
+--------------------------+------------+-------------+---------------------------------+
|                          | $-$30.855  | $-$10.639   | 33.76$\times$14.07; $+$64       |
+--------------------------+------------+-------------+---------------------------------+
|                          |            |             |                                 |
+--------------------------+------------+-------------+---------------------------------+
| G31.581$+$00.077         | $+$46.437  | $+$69.870   | 108.22$\times$76.09; $+$87      |
+--------------------------+------------+-------------+---------------------------------+
| 5.5$^c$                  | $+$46.626  | $+$69.040   | 108.18$\times$74.62; $+$86      |
+--------------------------+------------+-------------+---------------------------------+
|                          | $+$46.756  | $+$68.912   | 108.18$\times$74.55; $+$86      |
+--------------------------+------------+-------------+---------------------------------+

: Parameters of flux-weighted ellipses fitted to the maser cloudlets that appeared in all three epochs. First-epoch fits are presented in Figs [1](#g23207cm)-[5](#g31581cm).

Table notes: $^a$ The relative coordinates to the brightest spot position in each target in the first epoch as given in Table [\[table1\]](#table1). $^b$ The position angle of the major axis (north to east).

Distances were derived either through the trigonometric parallaxes, $^c$ (cite: r19) and $^d$ (cite: b08), or the calculated near kinematic distances, $^e$ (cite: r19); the online calculator is available at http://bessel.vlbi-astrometry.org/node/378. $^\star$ The fitting was done to all maser spots visible at each epoch separately (Fig. [7](#threeepochs)).

# Discussion

## Proper motions: Expansion

In the six targets presented here, the overall distributions of methanol maser emission along ring-like structures have generally been stable for up to eight to ten years. We detected the variability of individual maser cloudlets, although the single-dish monitoring suggested non-variable emission overall. The proper motions of single maser cloudlets have been estimated to range from a maximum of 13.5 km s$^{-1}$ to 0.5 km s$^{-1}$. These values are in agreement with other studies of proper motions of the 6.7 GHz methanol masers (e.g. (cite: s10a)). It can be clearly seen, especially in the case of the targets with a significant number of spots (Figs [1](#g23207cm)-[5](#g31581cm)), that the proper motions are consistent with expansion rather than infall, as was claimed for two well-known MYSOs: Cep A ((cite: t11); (cite: s14), (cite: s17)) and AFLG 5142 (cite: g11).

The best elliptical fits to the maser distribution in G23.207$-$00.377, G23.389$+$00.185, and G23.657$-$00.127 indicate that the sizes of their major axes have increased in time (Table [1](#ellipses)). This result is consistent with our independent measurement of the maser proper motions (method 1 in Sect. 2.1), providing support to the idea that the maser distribution expands from a common centre and is part of a coherent kinematic structure.

We also note that the displacements of single maser spots lying outside the best-fitted ellipses are consistent with expansion as well. In the case of the remaining three targets, where a smaller number of maser spots (and cloudlets) were detected, the increase of ellipse axes is not obvious. Also, the proper motion studies using the method 1 (Sect. 2.1) do not imply clear expansions in these cases.

![](bartkiewicz_g23p207_expansion_full.pdf)

In order to quantify the internal motion of maser spots in each source in a manner independent from the methods described above, we calculated the separations between pairs of spots from distinct regions at each epoch. In Figs [6](#histograms) and [13](#histogramsapp), we present histograms of separations between given groups (the separated ones) of cloudlets in each epoch. For clarity, we also present the changes in these separations, that is, the differences between epochs: i) 2004 (or 2007) and 2013, and ii) 2004 (or 2007) and 2015. The mean and median values are also marked with dashed and dotted lines, respectively.

In the case of G23.207$-$00.377, we used 72 blueshifted maser spots from the SE part and 40 spots from the NW (selected at the intermediate LSR velocities). The mean and median values of the spots’ separations increased by 2.31 and 2.95 mas, respectively, between 2004 and 2013, and by 2.95 and 3.09 mas between 2004 and 2015. An increase in the spots’ separation of 3 mas corresponds to velocities of 7.18 km s$^{-1}$ (for the time baseline 2004-2013) and 5.77 km s$^{-1}$ (for 2004-2015) at the distance of the source (Table [1](#ellipses)).

In G23.389$+$00.185, we calculated the separation between pairs of spots from the NE (32 spots) and the SW parts (27 spots). The mean and median values also increased (2.5 and 1.6 mas for separations between 2004 and 2013, and 2.9 and 2.0 mas between 2004 and 2015, respectively). For this source, an increase in the spots’ separation of 2 mas corresponds to 5.5 km s$^{-1}$ (2004-2013) and 4.4 km s$^{-1}$ (2004-2015).

In G23.657$-$00.127, we considered pairs of spots lying to the north and south of the EW line at $\Delta$Dec$= 20$ mas (see Fig. 1 in (cite: b20)). The northern group contained 88 spots, and the southern one had 120 spots. The mean and median values of their relative separation increased by 1.66 and 1.70 mas for the time baseline 2004-2013 and by 2.13 and 2.15 mas between 2004 and 2015. At the distance of the source, an increase of 2 mas corresponds to velocities of 3.7 km s$^{-1}$ (2004-2013) and 2.9 km s$^{-1}$ (2004-2015).

In G28.817$+$00.365, we considered 19 spots located in the eastern part and two spots from the western part. The mean (median) values of changes in separations are 0.82 and 0.72 mas (0.86 and 0.63 mas) for a time baseline of six and eight years, respectively. An increase in the spots’ separation of 1 mas from 2007 to 2013 or from 2007 to 2015 corresponds to velocities of 4.0 km s$^{-1}$ and 2.9 km s$^{-1}$, respectively.

Similarly, in 31.047$+$00.356 we calculated the separations between pairs of spots at east and west, and their mean and median values of changes in separations are as follows: 0.64 and 1.44 mas (2007-2013) and 1.08 and 2.08 mas (2007-2015), respectively. Here, a displacement of 1 mas from 2007 to 2013 or from 2007 to 2015, corresponds to velocities of 3.8 km s$^{-1}$ and 2.8 km s$^{-1}$, respectively.

Finally, in G31.581$+$00.077, we calculated the separations between spots from the east (seven) and west (nine spots) regions. The means of their changes are $-$0.11 and $-$0.03 mas, and the median values are 0.02 and $-$0.01 mas for 2007-2013 and 2007-2015, respectively.

The separation analysis confirmed that for sources G23.207$-$00.377, G23.389$+$00.185, and G23.657$-$00.127, a clear overall expansion is detected. In addition, a tentative expansion is seen in G28.817$+$00.365 and G31.047$+$00.356. For these two latter sources, only a small number of spots was available, and the time baseline of the observations was shorter, so the results are less robust and need to be confirmed with future observations. In the case of G31.581$+$00.077, which is the most distant target from our sample, we cannot exclude a sign of rotation considering the separation analysis and the proper motion studies. The fitted ellipses have similar axes in three epochs of observations as well. Therefore, this scenario has to be confirmed by future observations and repeated proper motion studies with a longer time baseline.

## Infrared and radio counterparts

In general, it is difficult to relate the 6.7 GHz maser spatial morphology, which we measured at the mas scale, to the position of the young star, which can be inferred, for instance, from infrared and radio continuum observations at scales more than an order of magnitude larger so far. In the following, we collect the information available in the literature for the five sources.

Inspection of mid-infrared data from the *Spitzer* IRAC maps, GLIMPSE, and MIPSGAL[^2] revealed that three out of the six targets (i.e. G23.207$-$00.377, G23.389$+$00.185, and G23.657$-$00.127) coincide with unresolved sources. They are also so bright that they saturate the detectors; the coincidence is within a pixel (i.e. 1.2$''$) in a GLIMPSE map. (cite: deb12) presented high-resolution near- and mid-infrared images of G23.389$+$00.185 and G23.657$-$00.127. The emission peaks are located northward (ca. 0.25$''$) from the methanol maser ring G23.389$+$00.185. Similarly, the near- and mid-infrared peaks are slightly shifted southward from the ring G23.657$-$00.127. In both cases, there was no compelling evidence in support of the hypothesis that methanol masers resided in circumstellar discs. (cite: h2016) also reported weak (0.38 mJy) continuum emission at 6 GHz towards G23.389$+$00.185, where the emission shows an elongated morphology that could be interpreted as a jet associated with the methanol masers. However, the poor astrometry and sensitivity of the radio continuum observations did not allow for a detailed comparison of position and morphology with the masers. Furthermore, (cite: b09) reported a non-detection of 8.4 GHz continuum emission towards these three sources, with an upper limit of 150 $\mu$Jy beam$^{-1}$.

In contrast, the 6.7 GHz methanol masers in G28.817$+$00.365 were found within 0.1$''$ of the position of the 8.4 GHz continuum peak (cite: b09). This emission, likely an ultra-compact HII region, was also imaged at 6 GHz by (cite: h2016). A search for mid-infrared data from the catalogues mentioned above did not show any clear counterpart. Similarly, the G31.047$+$00.356 masers are offset from the mid-infrared sources. (cite: h2016) reported weak continuum emission at 6 GHz that likely coincides with the methanol emission; this emission was previously undetected at 8.4 GHz by (cite: b09) with an upper limit of 150 $\mu$Jy beam$^{-1}$. In the case of G31.581$+$00.077, a continuum source was detected by (cite: h2016) but with no evidence supporting the physical relationship between the maser and continuum source since the maser is offset eastward by 0.19 pc.

We searched the Atacama Large Millimeter/Submillimeter Array (ALMA) Archive and found three sources with available data: G23.389$+$00.185, G23.657$-$00.127, and G31.581$+$00.077. They were part of the large programme ALMAGal (ALMA Evolutionary study of High Mass Protocluster Formation in the Galaxy; ID: 2019.1.00195.L). The observations covered the frequency range from 216.8 GHz to 244.14 GHz (band 6), with the best spatial resolution being 0.27" for G23.389$+$00.185 and G23.657$-$00.127 and 5.57" for G31.581$+$00.077. Methanol masers in G23.389$+$00.185 overlap with the centres of continuum emission of C$^{18}$O and CH${_3}$CN emission, proving that the local gas is warm and that the methanol masers arise from a hot molecular core (due to the nearby presence of CH${_3}$CN emission) and a larger gas condensation (traced by C$^{18}$O). In G23.657$-$00.127, however, we observed a westward offset by 0.006 pc, and in G31.581$+$00.077, we observed a south-west offset by ca. 0.21 pc (Fig. [14](#almacounter)). A detailed analysis of the association between thermal and maser lines at high angular resolution goes beyond the scope of this study, and it is postponed to a subsequent dedicated paper. Moreover, the angular resolution of the data is diverse. It is especially poor for G31.581$+$00.077, and the offset might be marginal.

## Origin of the methanol rings

(cite: s19) targeted the high-mass star-forming G23.01$-$0.41 with the ALMA at a resolution of 0.2$''$ and directly imaged a molecular disc around a MYSO in thermal methanol (and methyl cyanide). The disc rotates and undergoes infall around the central star and drives a molecular jet arising from the inner disc regions ($<$ 800 AU). The environment surrounding the young star is also one of the richest (Galactic) sites of methanol maser emission, where the maser cloudlets are distributed within a radius of 1500 AU from the central star and, on average, show expanding motions on the order of 7 km s$^{-1}$ ((cite: s15), their Fig. 4). In five out of the six sources presented in this paper (i.e. all but G31.581$+$00.077), the methanol maser kinematics show similar properties, with the maser emission distributed over large areas (300-800 AU) and the proper motions tracing expansion at velocities of several kilometers per second. These findings might be consistent with a scenario where the methanol masers are excited in the inner outflow cavity at the interface with a flare disc. A similar scenario explains the proper motions of SiO masers in Orion Source I, the closest MYSO, where the masers arise from a wide-angle bipolar wind emanating from a rotating edge-on disc (cite: m10).

In order to test whether this scenario also applies to the methanol maser rings, complementary observations of thermal tracers at high angular resolution ($\sim$0.1$''$) are needed, which can be used to interpret the environment of methanol masers. In this respect, we have started a sensitive ($\sim\mu$Jy) search of radio continuum emission towards the methanol maser rings with The Karl G. Jansky Very Large Array. These observations will be able to detect the ionised gas emission, including from radio thermal jets or hyper-compact H II regions, excited by any B-type young star associated with the masers and will allow us to pinpoint the driving source of the masers at a resolution comparable with the extent of the maser rings. Moreover, we also expect to explore the origin of maser rings in combination with the accretion disc or outflow tracers based on locations of the emission peak of dust and thermal lines, such as CH$_3$CN, SiO, and C$^{18}$O, relative to the location of the maser.

For comparison, in G23.657$-$00.127 we proposed two scenarios: a maser ring related to an outflow or a wide-angle wind at the base of a protostellar jet tracing a combination of rotation around and expansion along the jet (cite: b20). Similar decomposition of proper motion vectors for the remaining targets does not show a clearer scenario. In G23.207$-$00.377 and G23.389$+$00.185, the proper motion characteristics are similar to the ring, and one may assume the same physically connected structure. However, the rotational components are not convincing in that sense.

## Modelling a plane of gas motion

(cite: s17) showed that the 3D proper motion vectors of the methanol maser cloudlets in the HMSFR Cepheus A HW2 move along a plane. The 3D velocity field of methanol maser cloudlets was known from the proper motions and LSR velocities with subtraction of the region’s systematic velocity. They showed that the masers were detected within a radius ranging from 300 to 900 AU from HW2 tracing infall and rotational components. Due to the lack of complementary data for our sample of methanol maser rings, we were not able to infer the YSO position and the associated disc nor the jet orientation in order to give a more robust interpretation similar to what was presented in Cerpheus A HW2. However, we used the same planar hypothesis to search for a similar behaviour in our sample. Using the results from method 1 (Sect. 2.1), we searched for the best plane containing the 3D velocity vectors by minimising the average ratio V$_z$/V$_t$, that is, the perpendicular (V$_z$) to the tangential components (V$_t$) of the vectors to a given plane in the space (for details, see Sect. 4.1 and Fig. 3 in (cite: s17)). The plane is identified with two angles: i$_{\rm model}$, the angle between the perpendicular to the plane and the line of sight, and PA$_{\rm model}$, the position angle (north to east) of the sky-projection of the perpendicular to the plane. In Table [2](#table_model), we list the best fits for our targets.

We also calculated the inclination angles derived from the best ellipse fits (assuming the inclined disc-like structure). The inclination, i, is based on the ratio of minor to major axes in the same convention as i$_{\rm model}$, that is, the angle between the perpendicular to the plane of the best ellipse fit and the line of sight, and position angle of the minor axis, PA$_{\rm minor}$, is based on the ellipses’s fits as given in Table [1](#ellipses) (PA$_{\rm minor}$$\perp$PA$_{\rm major}$.) We note the agreement (within 20-40$^\circ$) between the inclinations of the best plane from the above model and the plane of the ellipse for G23.207$-$00.377, G28.817$+$00.365, G31.047$+$00.356, and G31.581$+$00.077. However, in general, as a result of this comparison, that is, the model of the 3D proper motion vectors moving along a plane and the maser cloudlets tracing an inclined ring, we did not find an agreement. This may indicate that the masers are located in a ring and their motion is substantially out of the plane of the ring. For G23.389$+$00.185 and G23.657$-$00.127, the fits are mutually exclusive. In the case of the most circular configuration observed in G23.657$-$00.127, the plane shows an almost edge-on inclination, while the distribution of maser spots suggest the existence of a ring-like morphology seen close to face-on. That may indicate the weakness of a model that does not fit the positions but only the 3D velocities. However, extensive searches for G23.657$-$00.127 where several parameters of the model were changed suggest that there is a significant (dominant) contribution of the line of sight velocities to the 3D velocities or that the masers move at a large angle with the plane of the sky. That is generally consistent with a disc-wind scenario (cite: b20), where although the flow starts from the disc, the velocities have a significant component along the disc (jet) axis.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | i$_{\rm model}$ | PA$_{\rm model}$ | V$_{\rm sys}$ | i | PA$_{\rm minor}$ |
|  | ($^\circ$) | ($^\circ$) | (km s$^{-1}$) | ($^\circ$) | ($^\circ$) |
| G23.207$-$00.377 | 51 | 165 | 77.5$^a$ | 72 | $+$42 |
| G23.389$+$00.185 | 6 | 15 | 75.5$^b$ | 60 | $-$38 |
| G23.657$-$00.127 | 81 | 285 | 80.5$^b$ | 23 | $+$70 |
| G28.817$+$00.365 | 76 | 285 | 86.9$^a$ | 64 | $-$37 |
| G31.047$+$00.356 | 101 | 200 | 77.6$^a$ | 76 | $-$27 |
| G31.581$+$00.077 | 81 | 245 | 96.0$^a$ | 45 | $-$3 |

: Parameters of best fits of the preferential planes of gas motion.

Table notes: Systemic velocities are estimated using NH$_3$ emission from $^a$ (cite: w12), $^b$ (cite: u11).

# Conclusions

We report the proper motions of 6.7 GHz methanol maser sources that were earlier classified as having a ring-like morphology (cite: b09). Three-epoch observations using the EVN and spanning over eight to ten years enabled us to detect velocities on the order of a few kilometers per second at distances from 3.19 to 5.5 kpc. We find that in G23.207$-$00.377, G23.389$+$00.185, G23.657$-$00.127, G28.817$+$00.365, and G31.047$+$00.356, the internal motions of maser cloudlets clearly suggest expansion from a common centre. In G31.581$+$00.077, the results are still marginal, and possible rotation cannot be excluded. The overall morphology of the maser emission has remained stable, although the intensities of individual maser cloudlets varied from epoch to epoch, suggesting internal instabilities. Our studies also show that the maser spot distribution alone does not allow for a direct interpretation of the ongoing scenario (e.g. if the rings trace the discs) and that multi-frequency studies at a complementary angular resolution are needed.

# Acknowledgements

AB, MS, PW, AK, MD acknowledge support from the National Science Centre, Poland through grant 2021/43/B/ST9/02008. The research leading to these results has received funding from the European Commission Seventh Framework Programme (FP/2007-2013) under grant agreement No. 283393 (RadioNet3).

34 natexlab

(ref: b08) Bartkiewicz, A., Brunthaler, A., Szymczak, M., van Langevelde, H. J., & Reid, M. J. 2008, A&A, 490, 787

(ref: b20) Bartkiewicz, A., Sanna, A., Szymczak, M., et al. 2020, A&A, 637, A15

(ref: b09) Bartkiewicz, A., Szymczak, M., van Langevelde, H. J., Richards, A. M. S., & Pihlström, Y. M. 2009, A&A, 502, 155

(ref: br13) Breen, S. L., Ellingsen, S. P., Contreras, Y., et al. 2013, MNRAS, 435, 524

(ref: deb12) De Buizer, J. M., Bartkiewicz, A., & Szymczak, M. 2012, ApJ, 754, 149

(ref: f99) Fitzgibbon, A., Pilu, M., & Fisher, R. B. 1999, IEEE Trans. Pattern Anal. Mach. Intell., 21, 476

(ref: f14) Fujisawa, K., Sugiyama, K., Motogi, K., et al. 2014, PASJ, 66, 31

(ref: g11) Goddi, C., Moscadelli, L., & Sanna, A. 2011, A&A, 535, L8

(ref: h2016) Hu, B., Menten, K. M., Wu, Y., et al. 2016, ApJ, 833, 18

(ref: k15) Keimpema, A., Kettenis, M. M., Pogrebenko, S. V., et al. 2015, Experimental Astronomy, 39, 259

(ref: m10) Matthews, L. D., Greenhill, L. J., Goddi, C., et al. 2010, ApJ, 708, 80

(ref: m91) Menten, K. M. 1991, ApJL, 380, L75

(ref: m00) Minier, V., Booth, R. S., & Conway, J. E. 2000, A&A, 362, 1093

(ref: mos00) Moscadelli, L., Cesaroni, R., & Rioja, M. J. 2000, A&A, 360, 663

(ref: mos05) Moscadelli, L., Cesaroni, R., & Rioja, M. J. 2005, A&A, 438, 889

(ref: mos11) Moscadelli, L., Cesaroni, R., Rioja, M. J., Dodson, R., & Reid, M. J. 2011a, A&A, 526, A66

(ref: mos07) Moscadelli, L., Goddi, C., Cesaroni, R., Beltrán, M. T., & Furuya, R. S. 2007, A&A, 472, 867

(ref: mosmas11) Moscadelli, L., Sanna, A., & Goddi, C. 2011b, A&A, 536, A38

(ref: n2023) Nakamura, M., Motogi, K., Nakamura, H., Yonekura, Y., & Fujisawa, K. 2023, MNRAS, 526, 1000

(ref: n93) Norris, R. P., Whiteoak, J. B., Caswell, J. L., Wieringa, M. H., & Gough, R. G. 1993, ApJ, 412, 222

(ref: p98) Phillips, C. J., Norris, R. P., Ellingsen, S. P., & McCulloch, P. M. 1998, MNRAS, 300, 1131

(ref: r19) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2019, ApJ, 885, 131

(ref: s19) Sanna, A., Kölligan, A., Moscadelli, L., et al. 2019, A&A, 623, A77

(ref: s10a) Sanna, A., Moscadelli, L., Cesaroni, R., et al. 2010a, A&A, 517, A71

(ref: s10b) Sanna, A., Moscadelli, L., Cesaroni, R., et al. 2010b, A&A, 517, A78

(ref: s17) Sanna, A., Moscadelli, L., Surcis, G., et al. 2017, A&A, 603, A94

(ref: s15) Sanna, A., Surcis, G., Moscadelli, L., et al. 2015, A&A, 583, L3

(ref: s14) Sugiyama, K., Fujisawa, K., Doi, A., et al. 2014, A&A, 562, A82

(ref: sz18) Szymczak, M., Olech, M., Sarniak, R., Wolak, P., & Bartkiewicz, A. 2018, MNRAS, 474, 219

(ref: t23) Tanabe, Y. & Yonekura, Y. 2023, The Astronomer’s Telegram, 16303, 1

(ref: t11) Torstensson, K. J. E., van Langevelde, H. J., Vlemmings, W. H. T., & Bourke, S. 2011, A&A, 526, A38

(ref: u11) Urquhart, J. S., Morgan, L. K., Figura, C. C., et al. 2011, MNRAS, 418, 1689

(ref: w98) Walsh, A. J., Burton, M. G., Hyland, A. R., & Robinson, G. 1998, MNRAS, 301, 640

(ref: w12) Wienen, M., Wyrowski, F., Schuller, F., et al. 2012, A&A, 544, A146

# Additional tables and figures

![image](bartkiewicz_G23p207_three_epochs.pdf) ![image](bartkiewicz_G23p207gauss_stable.pdf)

![image](bartkiewicz_G23p389_three_epochs.pdf) ![image](bartkiewicz_G23p389gauss_stable.pdf)

![image](bartkiewicz_G28p817_three_epochs.pdf) ![image](bartkiewicz_G28p817gauss_stable.pdf)

![image](bartkiewicz_G31p047_three_epochs.pdf) ![image](bartkiewicz_G31p047gauss_stable.pdf)

![image](bartkiewicz_G31p581_three_epochs.pdf) ![image](bartkiewicz_G31p581gauss_stable.pdf)

![image]({bartkiewicz_G23.207-0.377dynamic_spectrum}.png) ![image]({bartkiewicz_G23.389+0.185dynamic_spectrum}.png) ![image]({bartkiewicz_G23.657-0.127dynamic_spectrum}.png) ![image]({bartkiewicz_G28.817+0.365dynamic_spectrum}.png) ![image]({bartkiewicz_G31.047+0.356dynamic_spectrum}.png) ![image]({bartkiewicz_G31.581+0.077dynamic_spectrum}.png)

![image](bartkiewicz_g23p207_pm_rot_exp.pdf) ![image](bartkiewicz_g23p389_pm_rot_exp.pdf) ![image](bartkiewicz_g28p817_pm_rot_exp.pdf)

![image](bartkiewicz_g31p047_pm_rot_exp.pdf) ![image](bartkiewicz_g31p581_pm_rot_exp.pdf)

![Histograms of separations between NE and SW maser spot pairs in each epoch and the separation increase between epochs E2 and E3 relative to E1 in G23.389$+$00.185. The dashed lines mark the mean histogram values, while the dotted lines mark the median values.](bartkiewicz_g23p389_expansion_full.pdf)

![](bartkiewicz_g23p657_expansion_full.pdf)

![](bartkiewicz_g28p817_expansion_full.pdf)

![](bartkiewicz_g31p047_expansion_full.pdf)

![](bartkiewicz_g31p581_expansion_full.pdf)

![image]({bartkiewicz_g23_c18o_title}.png) ![image]({bartkiewicz_g23_ch3cn_title}.png) ![image]({bartkiewicz_g23p657_C18o_title}.png) ![image]({bartkiewicz_g23p657_ch3cn_title}.png) ![image]({bartkiewicz_g31_c18o_title}.png) ![image]({bartkiewicz_g31_ch3cn_title}.png)

+:-------------:+------------------:+------------------:+:-----------------:+:-----------------:+:-----------------:+:-----------------:+:-----------------:+:-----------------:+:-----------------:+:-----------------:+
| V$_{\rm p}$   | $\Delta$RA        | $\Delta$Dec       | $\mu_{\rm RA}$    | $\mu_{\rm Dec}$   | Flux density                                              | FWHM                                                      |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| (km s$^{-1}$) | (mas)             | (mas)             | (mas yr$^{-1}$)   | (mas yr$^{-1}$)   | E1                | E2                | E3                | E1                | E2                | E3                |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   | (Jy beam$^{-1}$)                                          | (km s$^{-1}$)                                             |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| V$_{\rm p}$   | $\Delta$RA        | $\Delta$Dec       | $\mu_{\rm RA}$    | $\mu_{\rm Dec}$   | Flux density                                              | FWHM                                                      |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| (km s$^{-1}$) | (mas)             | (mas)             | (mas yr$^{-1}$)   | (mas yr$^{-1}$)   | E1                | E2                | E3                | E1                | E2                | E3                |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   | (Jy beam$^{-1}$)                                          | (km s$^{-1}$)                                             |
+---------------+-------------------+-------------------+-------------------+-------------------+-----------------------------------------------------------+-------------------+-------------------+-------------------+
|               | **RA=18$^{\rm h}$34$^{\rm m}$55.20790s, Dec=$-$08$^{\rm o}$49’11.8421$''$ (J2000)**                                                       |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 72.53         | -38.824           | +14.095           | -0.04 $\pm$ 0.01  | +0.19 $\pm$ 0.01  | 0.319             | 0.204             | 0.365             | 0.35              | 0.39              | 0.30              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 73.84         | +30.114           | -32.762           | +0.17 $\pm$ 0.01  | +0.09 $\pm$ 0.02  | 0.446             | 1.195             | 0.319             | 0.28              | 0.29              | 0.32              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 74.85         | +37.313           | -48.534           | +0.16 $\pm$ 0.01  | +0.04 $\pm$ 0.04  | 0.787             | 0.444             | 0.457             | 0.33              | 0.51              | 0.61              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.56              | 0.53              |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 75.07         | +62.927           | -60.272           | +0.05 $\pm$ 0.03  | -0.10 $\pm$ 0.01  | 0.462             | 0.384             | 0.421             | 0.29              | 0.32              | 0.33              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 75.42         | -206.951          | -75.988           | -0.17 $\pm$ 0.01  | -0.00 $\pm$ 0.01  | 2.040             | 1.343             | 1.183             | 0.36              | 0.39              | 0.39              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 75.51         | +119.937          | -91.755           | +0.19 $\pm$ 0.01  | -0.15 $\pm$ 0.01  | 1.356             | 1.049             | 0.807             | 0.35              | 0.54              | 0.42              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 75.69         | -158.935          | -191.421          | -0.21 $\pm$ 0.04  | -0.27 $\pm$ 0.05  | 0.130             | 0.307             | 0.371             | 0.32              | 0.29              | 0.29              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 76.30$^n$     | +50.295           | -54.298           | -0.13 $\pm$ 0.04  | -0.08 $\pm$ 0.01  | 10.212            | 2.264             | 1.914             | 0.40$^d$          | 0.36              | 0.35              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 76.66$^n$     | +52.242           | -43.572           | +0.54 $\pm$ 0.11  | +0.22 $\pm$ 0.03  |                   | 3.528             | 3.978             | 0.40$^d$          | 0.47              | 0.44              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 77.14         | +62.746           | -49.179           | +0.06 $\pm$ 0.01  | -0.02 $\pm$ 0.01  | 18.302            | 5.211             | 4.615             | 0.36              | 0.50              | 0.65              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 77.49         | +92.042           | -46.048           | +0.05 $\pm$ 0.01  | -0.11 $\pm$ 0.01  | 7.326             | 3.939             | 4.621             | 0.45              | 0.55              | 0.37              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   | 0.36              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 77.93         | +74.636           | -52.639           | -0.03 $\pm$ 0.03  | -0.07 $\pm$ 0.02  | 6.301             | 2.607             | 3.052             | 0.45              | 0.39              | 0.37              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   | 0.69              | 0.80              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.59         | +106.129          | -21.073           | -0.05 $\pm$ 0.01  | -0.15 $\pm$ 0.03  | 0.607             | 0.604             | 0.609             | $-$               | 0.41              | 0.42              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.59         | +116.001          | -17.315           | +0.09 $\pm$ 0.01  | -0.08 $\pm$ 0.03  | 0.949             | 0.370             | 0.317             | 0.54              | 0.40              | 0.49              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.20         | +113.382          | -18.202           | +0.05 $\pm$ 0.01  | -0.06 $\pm$ 0.01  | 2.835             | 1.765             | 1.608             | 0.31              | 0.19              | 0.30              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.38         | -73.128           | +141.111          | -0.06 $\pm$ 0.01  | +0.05 $\pm$ 0.01  | 0.709             | 0.268             | 0.340             | 0.23              | 0.32              | $>$1              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   | 0.21              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.86         | -94.615           | +184.008          | -0.08 $\pm$ 0.01  | +0.06 $\pm$ 0.04  | 0.260             | 0.298             | 0.329             | 0.22              | 0.33              | 0.31              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.91         | +4.970            | +20.324           | +0.03 $\pm$ 0.01  | +0.11 $\pm$ 0.03  | 0.546             | 2.282             | 1.963             | 0.31              | 0.31              | 0.33              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 80.78$^n$     | -100.734          | +97.145           | -0.20 $\pm$ 0.05  | +0.18 $\pm$ 0.03  | 12.578            | 4.050             | 2.918             | 0.32              | 0.35              | 0.53              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.72              | 0.33              |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 81.84         | -77.854           | +90.433           | -0.15 $\pm$ 0.04  | +0.20 $\pm$ 0.02  | 13.482            | 4.664             | 5.733             | 0.52              | 0.63              | 0.48              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 81.83         | -94.597           | +95.504           | +0.23 $\pm$ 0.01  | +0.17 $\pm$ 0.01  | 4.189             | 4.162             | 4.647             | 0.35              | $-$               | 0.24              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 82.76         | -89.469           | +96.954           | -0.47 $\pm$ 0.04  | +0.10 $\pm$ 0.01  | 2.309             | 9.441             | 14.526            | 0.41              | 0.37              | 0.38              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   | 0.57              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 84.87         | +14.185           | +62.763           | +0.17 $\pm$ 0.01  | -0.01 $\pm$ 0.01  | 1.584             | 1.920             | 2.485             | 0.34              | 0.40              | 0.40              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.42              |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| **G23.389$+$00.185**                                                      | **RA=18$^{\rm h}$33$^{\rm m}$14.32364s, Dec=$-$08$^{\rm o}$23’57.5461$''$ (J2000)**                                                       |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 72.39         | -62.001           | +40.339           | -0.01 $\pm$ 0.01  | -0.03 $\pm$ 0.01  | 7.076             | 4.943             | 6.594             | 0.46              | 0.32              | 0.30              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 73.62         | +69.944           | +43.180           | +0.26 $\pm$ 0.06  | +0.65 $\pm$ 0.10  | 9.712             | 1.128             | 2.481             | 0.16              | 0.37              | 0.40              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.51              |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 74.00         | +65.994           | +36.741           | +0.02 $\pm$ 0.02  | -0.16 $\pm$ 0.06  | 3.215             | 3.944             | 5.206             | 0.40              | 0.25              | 0.27              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   | 0.31              |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 74.50         | -26.090           | +42.224           | +0.10 $\pm$ 0.01  | -0.08 $\pm$ 0.03  | 5.628             | 2.979             | 3.739             | 0.30              | 0.40              | 0.39              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 74.81         | +48.317           | +3.084            | -0.02 $\pm$ 0.01  | +0.00 $\pm$ 0.01  | 20.440            | 12.713            | 14.389            | 0.35              | 0.37              | 0.35              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.42              | 0.33              | 0.40              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 75.34         | +16.794           | +73.460           | +0.00 $\pm$ 0.01  | +0.08 $\pm$ 0.01  | 23.521            | 14.063            | 16.308            | 0.24              | 0.28              | 0.28              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   | 0.37              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 76.04         | -75.817           | -81.790           | -0.12 $\pm$ 0.04  | -0.05 $\pm$ 0.03  | 4.859             | 5.303             | 7.542             | 0.16              |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.42              | 0.42              | 0.33              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.29              | 0.33              | 0.36              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 76.13         | -59.326           | -71.429           | -0.26 $\pm$ 0.08  | -0.26 $\pm$ 0.01  | 6.771             | 4.557             | 5.545             | 0.36              | 0.51              | 0.45              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   | 0.14              |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 77.01         | +37.558           | -1.593            | +0.04 $\pm$ 0.01  | -0.03 $\pm$ 0.02  | 0.693             | 0.338             | 0.396             | 0.30              | 0.31              | 0.30              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 77.45         | -15.369           | -84.216           | -0.01 $\pm$ 0.01  | -0.13 $\pm$ 0.01  | 0.533             | 0.216             | 0.306             | 0.23              | 0.27              | 0.26              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| **G28.817$+$00.365**                                                      | **RA=18$^{\rm h}$42$^{\rm m}$37.34596s, Dec=$-$03$^{\rm o}$29’40.9556$''$ (J2000)**                                                       |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 87.73         | -42.815           | -22.111           | -0.04 $\pm$ 0.04  | +0.07 $\pm$ 0.05  | 0.306             | 0.178             | 0.211             | $-$               | 0.23              | 0.23              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 89.75         | +28.677           | +27.623           | -0.06 $\pm$ 0.00  | -0.33 $\pm$ 0.07  | 0.660             | 0.264             | 0.278             | 0.68              | 0.37              | 0.64              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   | 0.25              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 90.01         | -60.296           | +14.278           | -0.01 $\pm$ 0.05  | -0.07 $\pm$ 0.02  | 0.124             | 0.085             | 0.089             | $-$               | $-$               | 0.21              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 90.45$^n$     | +29.833           | +33.252           | +0.07 $\pm$ 0.01  | +0.10 $\pm$ 0.01  | 2.774             | 1.245             | 1.479             | 0.56              | 0.54              | 0.31              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 91.33         | +33.482           | +52.819           | +0.03 $\pm$ 0.01  | +0.31 $\pm$ 0.08  | 2.309             | 1.360             | 1.365             | 0.32              | 0.22              | 0.26              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   | 0.31              | 0.26              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   | 0.32              | 0.32              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 92.39$^n$     | +24.487           | +43.176           | -0.17 $\pm$ 0.14  | +0.57 $\pm$ 0.18  | 0.371             | 0.209             | 0.194             | 0.43              | 0.88              | 0.27              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   | 0.44              |                   | 0.40              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 92.65         | +27.411           | +60.646           | +0.09 $\pm$ 0.01  | +0.03 $\pm$ 0.03  | 1.924             | 1.129             | 1.292             | 0.38              | 0.40              | 0.42              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| **G31.047$+$00.356** (spots)                                              | **RA=18$^{\rm h}$46$^{\rm m}$43.85452s, Dec=$-$01$^{\rm o}$30’54.1557$''$ (J2000)**                                                       |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.07         | +7.095            | +8.027            | -0.02 $\pm$ 0.01  | +0.02 $\pm$ 0.05  | 0.255             | 0.108             | 0.068             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.25         | +6.715            | +6.818            | -0.03 $\pm$ 0.01  | -0.01 $\pm$ 0.01  | 0.045             | 0.122             | 0.111             | $-$               | 0.46              | 0.38              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.42$^n$     | +7.633            | +5.233            | -0.20 $\pm$ 0.11  | +0.14 $\pm$ 0.07  | 0.122             | 0.067             | 0.114             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.60$^n$     | +6.881            | +4.722            | -0.11 $\pm$ 0.06  | +0.10 $\pm$ 0.05  | 0.076             | 0.082             | 0.073             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.78         | +6.638            | +4.113            | -0.01 $\pm$ 0.03  | +0.09 $\pm$ 0.01  | 0.300             | 0.228             | 0.174             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 78.95         | +6.758            | +3.839            | -0.00 $\pm$ 0.01  | +0.08 $\pm$ 0.01  | 0.610             | 0.540             | 0.492             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.13         | +6.625            | +3.621            | +0.06 $\pm$ 0.02  | +0.06 $\pm$ 0.01  | 0.981             | 0.826             | 0.996             | 0.71              | 0.69              | 0.71              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.30         | +6.593            | +3.584            | +0.07 $\pm$ 0.02  | +0.02 $\pm$ 0.01  | 0.943             | 0.756             | 0.930             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.48         | +6.807            | +3.180            | +0.03 $\pm$ 0.00  | +0.01 $\pm$ 0.02  | 0.641             | 0.562             | 0.689             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.65         | +7.274            | +3.109            | -0.01 $\pm$ 0.01  | -0.08 $\pm$ 0.05  | 0.433             | 0.463             | 0.597             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 79.83         | +7.893            | +2.172            | +0.00 $\pm$ 0.00  | -0.03 $\pm$ 0.03  | 0.278             | 0.604             | 0.641             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 80.00         | +8.222            | +2.092            | +0.02 $\pm$ 0.01  | -0.04 $\pm$ 0.02  | 0.382             | 1.090             | 1.040             | 0.34              | 0.60              | 0.54              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 80.18         | +8.406            | +2.072            | +0.03 $\pm$ 0.01  | -0.03 $\pm$ 0.03  | 0.471             | 1.657             | 1.880             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 80.36         | +8.650            | +2.197            | -0.00 $\pm$ 0.02  | -0.08 $\pm$ 0.06  | 0.467             | 1.487             | 1.763             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 80.53         | +8.212            | +1.292            | +0.02 $\pm$ 0.00  | -0.03 $\pm$ 0.02  | 0.943             | 1.453             | 1.464             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 80.71         | +7.973            | +0.656            | +0.01 $\pm$ 0.01  | -0.04 $\pm$ 0.01  | 1.580             | 1.664             | 1.867             | 0.81              | 0.21              | 0.18              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 80.88         | +7.830            | -0.395            | +0.02 $\pm$ 0.01  | -0.03 $\pm$ 0.01  | 1.351             | 1.416             | 1.584             |                   | 0.65              | 0.61              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 81.06         | +7.427            | -0.946            | +0.04 $\pm$ 0.01  | -0.05 $\pm$ 0.01  | 1.142             | 1.274             | 1.484             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 81.06         | -51.775           | -28.434           | +0.17 $\pm$ 0.02  | +0.07 $\pm$ 0.05  | 0.198             | 0.232             | 0.357             | $-$               | 0.29              | 0.29              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 81.23         | +6.718            | -1.695            | +0.06 $\pm$ 0.01  | -0.05 $\pm$ 0.01  | 0.920             | 0.903             | 0.965             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 81.41         | +5.790            | -2.762            | +0.12 $\pm$ 0.01  | +0.02 $\pm$ 0.01  | 0.357             | 0.393             | 0.393             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 82.82         | -39.990           | -6.322            | -0.28 $\pm$ 0.01  | +0.07 $\pm$ 0.01  | 0.115             | 2.263             | 3.496             |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 82.99         | -39.859           | -6.220            | -0.30 $\pm$ 0.01  | +0.04 $\pm$ 0.01  | 0.528             | 1.019             | 0.560             | 0.28              | 0.29              | 0.31              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| **G31.581$+$00.077**                                                      | **RA=18$^{\rm h}$48$^{\rm m}$41.94582, Dec=$-$01$^{\rm o}$10’2.4794$''$ (J2000)**                                                         |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 91.60$^n$     | +34.405           | -128.074          | -0.00 $\pm$ 0.11  | +0.21 $\pm$ 0.06  | 0.299             | 0.102             | 0.110             | 0.31              | 0.34              | 0.37              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 95.64         | -71.099           | -48.651           | -0.01 $\pm$ 0.00  | -0.04 $\pm$ 0.00  | 2.630             | 1.083             | 1.822             | 0.33              | 0.34              | 0.33              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 97.75         | -132.089          | +8.874            | -0.01 $\pm$ 0.00  | +0.06 $\pm$ 0.00  | 0.266             | 0.132             | 0.211             | $-$               | 0.24              | 0.22              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 98.01$^n$     | -33.952           | -55.679           | -0.01 $\pm$ 0.06  | +0.04 $\pm$ 0.02  | 0.741             | 0.202             | 0.237             | 0.29              | 0.93$^{*}$        | 0.30              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 98.45         | -38.817           | -52.326           | +0.07 $\pm$ 0.04  | -0.10 $\pm$ 0.05  | 0.319             | 0.141             | 0.247             | 0.36              | 0.93$^{*}$        | 0.31              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 98.80         | +78.855           | +45.003           | -0.04 $\pm$ 0.01  | +0.02 $\pm$ 0.03  | 1.628             | 1.078             | 2.020             | 0.30              | 0.39              | 0.33              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 99.24         | +82.712           | +39.239           | -0.04 $\pm$ 0.03  | +0.07 $\pm$ 0.06  | 0.847             | 0.367             | 0.737             | 0.30              | 0.32              | 0.31              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
| 99.68         | +80.440           | +7.862            | +0.03 $\pm$ 0.03  | -0.01 $\pm$ 0.02  | 0.749             | 0.517             | 1.081             | 0.37              | 0.45              | 0.40              |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+
|               |                   |                   |                   |                   |                   |                   |                   |                   |                   |                   |
+---------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+-------------------+

: Continued.

Table notes: $^d$ in G23.207$-$00.377 denotes a case when a single Gaussian profile in the first epoch (E1) becomes a double in E2 and E3.

[^1]: The European VLBI Network is a joint facility of independent European, African, Asian, and North American radio astronomy institutes. Scientific results from data presented in this publication are derived from the following EVN project codes: EN003, EB031, EB034, EB052.

[^2]: https://irsa.ipac.caltech.edu/

</paper>

Write the methods card for this paper.