# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...698A.165A\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...698A.165A",
 "title": "Confirmation of a ring structure in the disk around MP Mus (PDS 66) with ALMA Band 7 observations",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Aguayo, Aurora",
 "n_authors": 13,
 "arxiv_id": "2504.17978",
 "doi": "10.1051/0004-6361/202554484",
 "alma_projects_linked_by_archive": [
  "2017.1.01167.S",
  "2017.1.01419.S",
  "2021.1.01205.S"
 ]
}
```

Paper text:
<paper>
# Confirmation of a ring structure in the disk around MP Mus (PDS 66) with ALMA Band 7 observations

Young stellar objects (YSOs) are surrounded by protoplanetary disks, which are the birthplace of young planets. Ring and gap structures are observed among evolved protoplanetary disks, often interpreted as a consequence of planet formation. The pre-Main Sequence (pre-MS) star MP Mus hosts one of the few known examples of protoplanetary disks within  100 pc. Previously, a disk ring structure, with a radius of 80-85 au, was detected in scattered light via near-infrared coronographic/polarimetric imaging. This ring structure may be indicative of the disk clearing process. Although such ring structures were not seen in the ALMA Band 6 images, some features were detected at $\sim$50 au. In this paper, we analyzed new ALMA Band 7 observations of MP Mus in order to investigate the details of its disk substructures. By subtracting the continuum profile generated from Band 7 data, we discovered a ring structure in the Band 7 dust continuum image at $\sim$50 au. We calculated the overall dust mass as $28.4\pm2.8 M_{\oplus}$ at 0.89 mm and $26.3\pm2.6 M_{\oplus}$ at 1.3 mm and the millimeter spectral index $\alpha_{0.89-1.3mm} \sim 2.2 \pm 0.3$ between 0.89 mm and 1.3 mm. Moreover, we display the spatial distribution of the spectral index ($\alpha_{mm}$), estimating values ranging from 1.3 at the inner disk to 4.0 at a large radius. Additionally, we observed an extended gas disk up to $\sim$120 au, in contrast with a compact continuum millimeter extent of $\sim$60 au. We conclude that there are strong indicators for an active radial drift process within the disk. However, we cannot discard the possibility of a dust evolution process and a grain growth process as responsible for the outer disk structures observed in the ALMA continuum imaging.

# Introduction

Stars are born from molecular clouds. Due to the conservation of angular momentum, newborn stars are surrounded by dust and gas-rich circumstellar disks, known as protoplanetary disks, which are the formation sites of young planets. In the protoplanetary disk phase (gas-rich), dust particles grow and may form objects large enough to accrete gas from the disk in a runaway process. Also, substructures such as gaps and rings are generated, potentially by planet formation and/or other processes. After roughly ten million years, photoevaporation dissipates the gas disk, leaving behind a debris disk (cite: Williams&Cieza2011) which may then evolve into a mature planetary system.

The structure and evolution of the protoplanetary disk provide crucial information on planet formation (cite: Williams&Cieza2011; Andrews2020; Pinte2023). High spatial resolution observations have discovered substructures inside the circumstellar disk, potentially indicating their ongoing planet formation process (cite: Andrews2018; Long2018), as early as during the protostellar stage (cite: SeguraCox2020). The bright and dark ring structures have been a topic of great debate as they are expected to be detected as a consequence of already formed (proto)planets on the disk (cite: Zhu2014; Perez2015). However, there are other mechanisms that can also form or show these structures, without requiring the presence of protoplanets, such as an effect of dust opacity due to grain growth (cite: Birnstiel2015), hydrodynamic instabilities (cite: Ward2000; TakahashiInutsuka2014), magnetohydrodynamic instabilities (cite: Gressel2015; Flock2015), fast pebble growth near condensation fronts (cite: Zhang2015), and dust rings induced by sintering (cite: Okuzumi2016; OkuzumiTazaki2019; Hu2019). Regardless of their origin, these ring structures are excellent places to accumulate and concentrate large dust grains (cite: Zhu2014; Flock2015; Ruge2016; Sierra2017; Sierra2019), and their presence among disks of all ages (cite: VanderMarel2016; Andrews2018; Shi2024) becomes a great indicator that the formation of rings is a necessary first step for the formation of terrestrial planets (cite: Carrasco-Gonzalez2016; Kuwahara2024).

The sizes of even the brightest and largest protoplanetary disks in any given molecular cloud are $\sim$100 au (cite: Williams&Cieza2011), whilst the median size of most disks is $\sim$14 au (cite: Dasgupta2025). For spatially resolving disks in nearby star formation regions ($\sim$140 pc), observations with subarcsecond resolutions are required. Thus, observations with the Atacama Large Millimeter/submillimeter Array (ALMA) became crucial to resolve structures in disks. In the past decade, ALMA has provided data that revolutionized our understanding of the spatial properties of protoplanetary disks. This includes constraints on the distribution of millimeter sized dust grains, the kinematic parameters of molecular gas, and the disk chemical structures (cite: Andrews2020; Huang2018; Oberg2021). High resolution ALMA data will also assist us in distinguishing different disk clearing mechanisms (e.g., photoevaporation and grain growth), providing constraints to the theoretical models, and finally placing an accurate diagnosis of the evolutionary stage of the planetary system.

Here, we focus on submillimeter observations obtained with ALMA of the disk around MP Mus, also known as PDS 66 or Hen 3-892: A star of 1.2 $\pm$ 0.2 $M_{\odot}$, K1 spectral type and an age of 3.1 $\pm$ 0.9 Myr (cite: Asensio-Torres2021). According to Gaia DR3, the distance of MP Mus is 97.8 pc (cite: Gaia2024), placing it among the three known, actively accreting, near solar mass stars within 100 pc. The other two nearby, roughly solar-mass pre-main sequence (pre-MS) stars that display evidence for ongoing accretion are TW Hya and V4046 Sgr (cite: KastnerPrincipe2022). The young nature of MP Mus was originally reported by (cite: Gregorio1992), based on the infrared excess and a strong H$\alpha$ emission feature in the spectrum. This star is located in the nearest OB association Scorpius-Centaurus and was originally considered a member of the Lower Centaurus Cruz (LCC) subgroup (cite: Mamajek2002), with an estimated age of 17 Myr. Later, MP Mus was classified as a member of the $\epsilon$ Chamaeleon Association (CA), which has a much younger age of 3-8 Myr (cite: Torres2008; Murphy2013; Dickson2021). A younger age of the system, 7 Myr, is also supported by the strength of the Li absorption line at 6708 Å$\,$ (cite: Weise2010) and the star’s position near the boundary of the $\epsilon$ CA and the youngest ($\sim$8 Myr) LCC subgroup (cite: Varga2024). Applying contemporaneous near-UV observation from the Hubble Space Telescope (HST) and ground-based optical spectrum, (cite: Ingleby2013) measured the mass accretion rate as 1.3$\times 10^{-10} M_\odot$ yr${^{-1}}$, placing it at the lower mass accretion range of pre-MS stars.

The measurement of the circumstellar disk properties of MP Mus started almost two decades ago. First, the total dust mass of the disk has been estimated to be 5$\times 10^{-5} M_\odot$ or 1.6 $M_\oplus$ (cite: Carpenter2005). Using the N-band (8 - 13 $\mu$m) spectra and infrared Spectral Energy Distribution (SED) up to 1 mm, (cite: Schutz2005a) discovered grain growth in the circumstellar disc. Later on, (cite: Bouwman2008) detected circumstellar silicate dust grains in the disk of MP Mus, applying mid-infrared spectra from the Spitzer satellite. The first scattered light image of MP Mus was taken by the NICMOS on HST (cite: Cortes2009), with an estimated disk radius of 170 au. (cite: Kastner2010) established the presence of a significant gaseous component within the MP Mus disk via detection of $^{12}$CO(3-2) emission and estimated the gas disk radius as $\sim$120 au. With the development of the laser guiding near-infrared observations, a disk ring was detected around 80 au by the Gemini Planet Imager (cite: Wolff2016). The dip of the surface brightness between the bright optically thick inner disk and the ring structure at 80 au indicates an ongoing clearing process inside the disk plane, consistent with the classification of a transitional disk. Similarly, (cite: Avenhaus2018) discovered a ring structure at 85 au and an inclination of 30 deg using the SPHERE instrument located in ESO/VLT. In addition, no accreting sub-stellar component was detected by the H$\alpha$ emission inside the disk cavity down to the 12 mag contrast of the central star (cite: Zurlo2020).

(cite: Ribas2023) presented ALMA observations of MP Mus down to 4 au resolution in the 1.3 mm bandpass (Band 6). They found an optically thick disk with a radius of 60$\pm$5 au, with the possible exception of a barely resolved outer ring at $\sim$50 au. The mismatch between the gap locations detected in scattered light and dust continuum indicates that the ring structure seen in the near-infrared might only be a shadow cast by a puffed inner disk. The molecular gas (e.g., $^{12}$CO) emission spreads widely to a radius of 130 au. They also measured the millimeter spectral index ($\alpha_{mm}$) and found an inhomogeneous distribution of the $\alpha_{mm}$ value. This result indicates that the optically thick emission arises from high albedo dust grains residing in the inner 30 au of the disk ($\alpha < 2$). Subsequently, (cite: Grimble2024) analyzed the structure and composition of MP Mus using the Spitzer IRS spectrum and ALMA Band 6 image, with radiative transfer models. In this work, the authors found that a density gap (i.e., a ring at 80 au) fits the observational SED better than disk shadowing, within the limitations of the modeling.

# Observations and data reduction

In this study, we present and analyze ALMA observations of MP Mus from two Cycle 5 programs at 1.3 mm (Band 6; 2017.1.01419.S P.I. Claudio Cáceres; 2017.1.01167.S P.I.: Sebastián Pérez) and one Cycle 8 program at 0.89 mm (Band 7; 2021.1.01205.S P.I.: Claudio Cáceres). For the continuum analysis, we focus on Band 7 observations, and for comparison, we used the extended configuration of 2017.1.01167.S in Band 6 since it has the best resolution between the two datasets. The rms of the compact configurations for both datasets are systematically higher than the one of the extended configurations. In addition, the compact configurations Band 7 dataset showed issues during the phase calibration. After combining the compact and extended configurations we did not see an improvement in the rms nor in the image quality, thus we decided to use only the extended configurations of Band 7 and Band 6 for the continuum analysis. However, for line analysis, we used the combined compact and extended configurations of each data set. The details of the different data sets are summarized in Tables [\[tab:observation log\]](#tab:observation log) and [\[tab:correlator config log\]](#tab:correlator config log), including the corresponding correlator configurations.

For data reduction, we used the standard pipeline calibration provided by the ALMA staff using the Common Astronomy Software Applications package, (cite: McMullin2007) version 5.6.1-8-10.14. We detected continuum emission from the disk with a high peak Signal to Noise ratio (S/N \>` 100`). After this, we performed selfcalibration to the extended configurations for each band; first excluding all channels with emission lines and then, using `mtmfs` deconvolver, `Briggs` weighting, a `robust` value of 0.5 and -0.5, and `nterms`=2. In addition, selfcalibration was performed on the combined compact and extended configurations for the line analysis. To properly combine these datasets, we found the peak of the disk continuum emission by fitting a 2D Gaussian shape to each dataset. Then, we applied CASA tasks `fixvis` and `fixplanets` to set the phase center to a common coordinate to finally use `concat` task to concatenate both data sets.

For Band 7, we performed a five-step phase only calibration. We sought solutions over 60 s intervals on the first four steps and solutions over 45 s on the fifth step. By doing so, we improved the root mean square (rms) noise by 60% and S/N of the emission peak by 215% (from 125 to 394) for a robust value of $r = 0.5$ and an improvement of 30% on S/N (from 107 to 141) for a robust value of $r = -0.5$. For Band 6 observations, we performed a similar four step phase only calibration and sought solutions over 35 s for the first and second steps, and solutions over 25 s for the third and fourth steps. In this case, the rms noise is reduced by 80% and S/N is improved by 800% (from $\sim$40 to $\sim$320) for both robust values: $r = 0.5$ and $r = -0.5$.

![](B7_ext_selfcal_log_linear_r-05.png)

# Results

The ALMA Band 7 observation provides a high spatial resolution of 0.07$\times$0.05" that complements the previous Band 6 observations that reach a resolution of 0.06$\times$0.04" (cite: Ribas2023), both with a robust value of -0.5. In this section, we will analyze the disk structures from these Band 6 and 7 observations, in terms of the continuum images and radial profiles, and their CO spectral line counterparts.

## Dust continuum

### Continuum images

We present synthesized continuum images at 0.89 mm (Band 7) and 1.3 mm (Band 6) from the selfcalibrated data described in Sect. [2](#sec:2). We applied the `tclean` algorithm with ` mtmfs` deconvolver and "nterms=2". We adopted a robust value of $r = 0.5$, which is an intermediate value between the angular resolution and S/N, and also consistent with the analysis made by (cite: Ribas2023). Additionally, we applied $r=-0.5$ to explore the disk with a better angular resolution ($\sim$5 au at 98 PC), thus observing small scale substructures. The resulting beam sizes are 0.09" $\times$ 0.07" at 0.89 mm and 0.12" $\times$ 0.10" at 1.3 mm for $r = 0.5$; and 0.07" $\times$ 0.05" at 0.89 mm and 0.11"$\times$ 0.09" at 1.3 mm for $r = -0.5$. The estimated rms for Band 7 are $4.8\times10^{-5}$ \[Jy/beam\] for $r=0.5$ and $5.8\times10^{-5}$ \[Jy/beam\] for $r=-0.5$ and for Band 6 are $4.1\times10^{-5}$ \[Jy/beam\] for $r=0.5$ and $3.9\times10^{-5}$ for $r=-0.5$ (see Table [\[tab:continuum parameters\]](#tab:continuum parameters)). We only used selfcalibrated extended configurations to produce the continuum images and deprojected brightness profiles. To estimate continuum fluxes, we applied aperture photometry on these images with a 5-$\sigma$ mask. The measured continuum fluxes are 388 $\pm$ 39 mJy at 0.89 mm and 168 $\pm$ 17 mJy at 1.3 mm. The maximum recoverable scales ($\theta_{\rm MRS}$), based on the most extended antenna configuration we used in this study (with a minimum baseline of 92 m in Band 6 and 41 m in Band 7, see Table [\[tab:observation log\]](#tab:observation log)), are 2.7" and 1.8" at 0.89 mm and 1.3 mm, respectively[^1]. Both values are larger than the observed angular size of the disk. In Fig. [1](#fig:Continuum B7 ext selfcal r-05), we present the Band 7 image with $r=-0.5$ on both linear and logarithmic scales. A ring structure at 0.45-0.50" or $\sim$45-50 au (assuming d = 98 pc) is detected.

|                |      |                  |             |                |          |
|:--------------:|:----:|:----------------:|:-----------:|:--------------:|:--------:|
|      ALMA      | ALMA | Robust value (r) |    Beam     |      RMS       | Peak S/N |
|  Project Code  | Band |                  |             | ($\mu$Jy/beam) |          |
| 2017.1.01167.S |  6   |       0.5        | 0.12"x0.10" |       41       |   320    |
|                |  6   |       -0.5       | 0.11"x0.09" |       39       |   320    |
| 2021.1.01205.S |  7   |       0.5        | 0.09"x0.07" |       48       |   394    |
|                |  7   |       -0.5       | 0.07"x0.05" |       58       |   141    |

### Continuum radial profiles

The radial profile of a circumstellar disk carries valuable information on the disk morphology, therefore revealing substructures such as rings and gaps. Additionally, it also provides the intensity distribution, which will further infer the spatial distribution of dust grains and gas molecules in the disk.

The disk inclination angle (i) and position angle (PA) of MP Mus were measured as $32^\circ$ and $10^\circ$ based on a 2D Gaussian fit to the 0.89 mm dust continuum in Band 7, which is in total agreement with estimations made from Band 6 at 1.3 mm dust continuum (cite: Ribas2023) and scattered light observations (cite: Avenhaus2018). To confirm the existence of the substructures in the disk, we deprojected the continuum image adopting the aforementioned disk inclination and PA. We then extracted the azimuthal average radial profile, as the average intensity within concentric rings centered at the peak intensity of the source. The central location is also estimated by the 2D Gaussian fit. These profiles are presented in Fig. [2](#fig:Radial profile (cont)).

![](B7B6_continuum_profiles_log_robust.png)

The continuum profiles are extended until $\sim$60 au in Band 7, a similar result to that in (cite: Ribas2023). While Band 6 profiles are apparently smooth, in Band 7, some structures are seen. With a robust value of $r=-0.5$ in the Band 7 profile, we discovered what seems to be a little bump at $\sim$50 au that could correspond to the ring structure observed in Fig. [1](#fig:Continuum B7 ext selfcal r-05) since they are at the same location at $\sim 45-50$ au. Moreover, this bump is in total agreement with the feature found by (cite: Ribas2023) in Band 6. In addition, from the Band 7 profiles, it seems that a second bump emerged at $\sim 60$ au, but this is a very low S/N feature.

### Frank radial profile

Here, we used the frankenstein software (cite: Jennings2020) to construct a 1D radial profile from the visibilities of the continuum in Band 7, to perform an in depth study of the MP Mus. Frank calculates super resolution radial profiles of protoplanetary disks assuming azimuthal symmetry, an assumption that is in agreement with previous observations of MP Mus (cite: Avenhaus2018). Using a fast ($<$1 min) Gaussian process, the Frank software fits the visibilities directly and reconstructs a 1D radial brightness profile nonparametrically. The inclination and position angle values derived from Frank are consistent with the previously adopted results. We then compare it with the one previously calculated in Band 6 by (cite: Ribas2023) and with the continuum radial profiles (see Fig. [3](#fig:Frank profiles)).

![](Frank_profiles.png)

From the reconstruction of Frank profiles, we noticed that the bump at $\sim$45-50 au is present, which is in total agreement with the continuum image and the continuum radial profile in Band 7.

### Dust continuum versus $^{12}$CO profiles

The micrometer sized dust grains that reflect starlight are distributed out to greater distances than the larger particles responsible for the millimeter continuum (cite: Garufi2018; Ansdell2018). Also, models of transitional disks show that small grains extend to larger radii than large grains (e.g., (cite: Villenave2019)). All of this is expected since small grains are predicted to be well coupled with the gas. On the other hand, large grains are much less decoupled from the gas and under the effects of radial drift, settle to the disk midplane (cite: Barriere-Fouchet2005).

![](12CO_profiles_FINAL.png)

Moreover, if we look at the $^{12}$CO line profiles in Fig. [4](#fig:12CO_continuo), where smaller dust grains sizes are coupled to the gas, the disk is much more extended than $\sim$60 au (the millimeter dust grains extension), reaching a disk extension of $\sim$110 au for $^{12}CO(2-1)$ and $\sim$120 au for $^{12}CO(3-2)$, which results in total agreement with the relation found by (cite: Andrews2020) of $R_{\rm CO} \geq 2R_{mm}$ based on 0.9 mm data from (cite: Oberg2011), (cite: Simon2017), (cite: Ansdell2018), and (cite: Facchini2019).

## Parameters calculation

### Disk masses

Submillimeter observations are ideal for estimating disk masses (cite: Andrews&Williams2005). At a scale much larger than 10 au, the continuum emission is assumed to be optically thin; therefore, the observed flux, $F_{\nu}$, is directly related to the disk mass. Here, we use the following relation to estimate the disk dust mass (cite: Hildebrand1983):

$$\begin{equation}
M_{\rm dust} \simeq  \frac{F_{\nu}d^{2}}{\kappa_{\nu}B_{\nu}(T)}
\end{equation}$$ where $d = 98 pc$ is the distance to MP Mus from Gaia DR3. We assume $B_\nu \approx 2\nu^{2}kT/c^{2}$ since the Planck function is close to the Rayleigh-Jeans regime, a temperature of $T = 20 K$ and $\kappa_{\nu} \sim 3cm^{2}g^{-1}$ as the dust opacity at 0.89 mm (cite: Ricci2012A) and 1.3 mm (cite: Andrews2011). This results in $(8.53\pm0.85)\times10^{-5} M_{\odot}$ or $28.4\pm2.8 M_{\oplus}$ at 0.89 mm and $(7.88\pm0.79)\times10^{-5} M_{\odot}$ or $26.3\pm2.6 M_{\oplus}$ at 1.3 mm as upper limits.

In addition, by assuming that MP Mus has properties similar to a median disk in Taurus, we use the linear relations derived by (cite: Cieza2008) to estimate the total disk mass from the observed flux:

$$\begin{equation}
M_{\rm disk} = 1.7 \times 10^{-1} \left [  \frac{F_{\nu}(1.3mm)}{mJy} \times \left (\frac{d}{140pc} \right )^{2} \right ] M_{J}
\end{equation}$$

$$\begin{equation}
M_{\rm disk} = 8.0 \times 10^{-2} \left [ \frac{F_{\nu}(0.85mm)}{mJy} \times \left (\frac{d}{140pc} \right )^{2}  \right ]M_{J}
\end{equation}$$

These relations come from modeling the IR and submillimeter SED of observations presented by (cite: Andrews&Williams2005; Andrews&Williams2007), with a disk temperature of $T = 20 K$, which is the median disk calculated by (cite: Andrews&Williams2005), and a dust opacity of $\kappa_{\nu} = 10[\nu/1200 GHz] \, cm^{2}g^{-1}$ that simply assumes a gas-to-dust mass ratio of 100 (cite: Williams&Cieza2011; Cieza2016). These results on total disk masses of 15.43 $\pm$ 1.55 $M_{Jup}$ at Band 7 and of 14.2 $\pm$ 1.44 $M_{Jup}$ at Band 6.

However, dust opacities at millimeter wavelengths have a great dependence on grain size distribution, structure, and composition of the disk, therefore, their values still remain highly uncertain (cite: Birnstiel2018; Birnstiel2024).

### Spectral index

In protoplanetary disks, the millimeter spectral index ($\alpha_{mm}$) has a strong dependence on the grain size distribution and, therefore, it is a widely used parameter to investigate grain growth in circumstellar disks among several star forming regions (cite: Ricci2012; Ribas2017; Ansdell2018; Tazzari2021).

At millimeter wavelengths, the thermal emission of a disk, integrated over its surface, is dominated by the emission of the outer, optically thin region. By assuming that the dust emission from the disk is optically thin and in the Rayleigh-Jeans limit regime (unless the disk would be abnormally cold), the wavelength dependence of the integrated flux is expressed as $F_{\nu} \propto \nu^{\beta_{mm}+2}$, where $\beta_{mm}$ is the dust opacity index. Thus, we can fit the observed submillimeter and millimeter SED between two frequencies with $F_{\nu 1}/F_{\nu 2} = (\nu_{1}/\nu_{2})^{\alpha_{mm}}$, where the sub-mm/mm spectral index is related to the dust opacity index by $\alpha_{mm} = \beta_{mm} + 2$.

We calculated a spectral index between Band 6 and Band 7 as $\alpha_{0.89-1.3 mm} = 2.2 \pm 0.3$ by using the integrated fluxes values calculated in Sect. [3.1](#sec:3.1). However, this value only represents an average spectral index in the disk, without the information of the spatial distribution. In addition, based on more recent millimeter observations at different wavelengths of several protoplanetary disks, the opacity index and, by extension, the spectral index, may change with the radius (cite: Guilloteau2011; Pinilla2014; Birnstiel2024). In order to study the spatial variation of $\alpha$, we combined 0.89 mm and 1.3 mm observations to produce a spectral index map. To join the data, we set a common phase center estimated by a 2D Gaussian fit, and then we used the `tclean` task with `mtmfs` deconvolver, `nterms`=2, which internally sets a common beam size between the two visibility data sets. We also probe with different `robust` values (0.5, 0.0, and -0.5). The resulting `alpha` images were used as the spectral index map, and it is shown in Fig. [5](#fig:spectral index) along with its deprojected radial profiles. As expected, the spectral index ($\alpha_{0.89-1.3 mm}$), is variable through the disk, increasing with radius, starting with a value of $\sim$1.2 at the inner radius and finishing with a value of $\sim$4 for r = 0.5. For a further discussion, see Sect. [4.2](#sec:4.2).

![](Spectral_index_deprojected_FINAL.png)

# Discussion

## Millimeter substructure in Band 7

With the new dataset with high angular resolution in Band 7 ($\sim$5 au), we are able to observe a small outer ring that has been revealed at $\sim$50 au from the continuum emission at 0.89 mm. However, there are still no signs of an inner cavity.

In previous works at millimeter wavelengths, MP Mus appeared to be a smooth disk, although it has a ring structure in scattered light (cite: Avenhaus2018). (cite: Ribas2023) reached a similar angular resolution at 1.3 mm ($\sim$4 au) as our Band 7 data, observing a smooth disk with the possibility of a barely resolved outer ring at $\sim$50 au. This is an interesting scenario, where the angular resolutions are similar in both bands and the structure is revealed at 0.89 mm observations, confirming the features found at 1.3 mm by (cite: Ribas2023), which may be more pronounced at Band 7 since it has a larger S/N emission than that at Band 6.

To emphasize the structure, we made a brightness profile multiplying the brightness intensity by $r^{2}$, shown in Fig. [6](#fig:Intensity_r2), where a peak is shown between 45-50 au, which matches the observed outer ring in the continuum image at 0.89 mm.

![](Intensity_r_square.png)

To understand the reasons why we are not able to observe the same structure in the 1.3 mm continuum, we convolved the 0.89 mm continuum image with the beam size of the 1.3 mm continuum image and then corrected the images to a common phase center, estimated by a 2D Gaussian fit. The resulting image, along with its residual image, are shown in Fig. [7](#fig:B7_convolved_B6). The ring structure seems to disappear with the convolution to the larger beam size, suggesting that there is not enough angular resolution to resolve the structure in our 1.3 mm image. However, the ring structure is clearly presented in the residual image (see the right panel of Fig. [7](#fig:B7_convolved_B6)).

![](residuos_B7-B6_scaled_centered.png)

In addition, (cite: Pinilla2014) compared data from (cite: Ricci2012A), who presented millimeter fluxes and integrated spectral indices of $\sim$50 classical disks in Taurus, Ophiuchus, and Orion star forming regions with data of transitional disks in Taurus, Perseus, Lupus, Ophiuchus, and, among others (references therein). They found that the mean value of the integrated spectral index for a typical protoplanetary disk corresponds to a value of $\overline{\alpha}^{PD}_{mm} = 2.20 \pm 0.07$ in comparison to a value of $\overline{\alpha}^{TD}_{mm} = 2.70 \pm 0.13$ for transitional disks. Also, the values estimated on previous works are consistent with both, classical and transitional disks: (cite: Cortes2009) found a value of ${\alpha}_{3mm-12cm} = 2.4 \pm 0.1$ and (cite: Ribas2023) found values of ${\alpha}_{0.89-1.3mm} = 2.4 \pm 0.3$, ${\alpha}_{1.3-2.2mm} = 2.12\pm 0.11$ and ${\alpha}_{0.89-2.2mm} = 2.25 \pm 0.13$. From the spectral index estimated for MP Mus (${\alpha}_{0.89-1.3mm} \sim 2.2$), its value is more concordant with classical protoplanetary disks, added to the fact that it does not present a large inner cavity, a necessary feature for MP Mus to be classified as a transitional disk.

## Indicators of grain growth and radial drift on the disk

As we mentioned before, the spectral index has been widely used to characterize the dust properties in protoplanetary disks, especially to constrain the maximum particle sizes in the submillimeter to centimeter range. The opacity spectral index, $\beta$, is sensitive to the maximum grain size of the disk, $a_{max}$ (cite: NattaTesti2004; Draine2006; Testi2014). When dust grains reach millimeter or larger sizes ($a_\text{max}$ $>> \lambda$), the absolute value of dust opacity, $\kappa_{\lambda}$, decreases, $\beta$ becomes smaller ($\beta \sim$ 0) and the emission follows the shape of a blackbody ($\alpha_{mm} \sim 2$). Alternatively, smaller dust grains ($a_\text{max}$ $<< \lambda$, e.g., ISM like grains) have $\beta \sim$ 2. Another possible explanation for low values of $\beta$ is regions of high optical depth, where (cite: Ricci2012) has shown that this scenario would only be possible for the brightest and most massive disk. Thus, low values of $\beta$, and therefore, $\alpha_{mm}$ are indicative of significant grain growth, high optical depth, or a combination of these two processes (cite: Birnstiel2024). From our derived spectral index $\alpha_{0.89-1.3mm}$, we found a range of $\beta$ between: 0.0-0.5.

On the other hand, compact disks at millimeter wavelengths are expected from radial drift models, where dust pebbles drift toward (local) pressure maxima present in the gas structure (cite: Weidenschilling1977), grain growth of the millimeter grains, and also due to line optical depth. These effects predict that millimeter continuum emission should be much more compact than the emission of gas tracers, particularly of the CO tracer (cite: Facchini2017; Trapman2019).

(cite: BirnstielAndrews2014) demonstrate that the combined effects of radial drift and (viscous) gas drag naturally produce a sharp outer edge in the dust distribution, where this edge feature forms before grain growth has made much progress in the outer disk, and remains over longer timescales. Also, the average dust-to-gas mass ratio of the disk should be lower than the canonical 1%, with the inner regions locally showing a higher value.

Furthermore, $\alpha_{mm}$ is variable and increases its value as a function of the radius. In Fig. [5](#fig:spectral index), we observed a value variation of $\alpha_{0.89-1.3mm}$ between 1.2 and 3.0-4.0 depending on the robust value we used, where the blackbody limit is reached at $\sim$30 au ($\alpha = 2$). Since the spectral index is lower ($\alpha_{mm}<$2) at the inner radius, it suggests that this part of the disk is optically thick, the information about dust sizes is lost and we are observing an elevated surface of the disk with the continuum emission at 1.3 mm and 0.89 mm, which could hide some structures in the midplane of the disk. For larger radii, where $\alpha_{mm}>$2 and $\beta$ remain in lower values (between 30-40 au), it could be possible that grain growth takes part as an effective process. In addition, in regions where dust growth is effective, assuming that dust opacity is dominated by absorption is far from reality; instead, for those large particles, the dust opacity should indeed be dominated by scattering (cite: Birnstiel2018; Sierra2019).

Since the inner part of the MP Mus disk is optically thick, we only have information on the surface, indicating a larger population of grains than the observation, which could be translated into a higher dust-to-gas ratio. Also, MP Mus shows a compact disk in millimeter continuum ($\sim$ 60 au) in contrast with gas tracers such as $^{12}$CO lines, reaching a radius of $\sim 110-120$ au (see appendix [8](#sec:C)). Moreover, we obtained an estimated ratio of $R_{gas}/R_{dust} \sim 2$, a value that is not large enough to demonstrate dust evolution, which requires an $R_{gas}/R_{dust} > 4$ (cite: Trapman2019). Thus, it is likely that the radial drift is the most dominant process. However, identifying the dust evolution process from $R_{gas}/R_{dust}$ requires modeling the disk structure, including the total CO content.

## Comparison with disk opacity theory

Substructures in the disk of MP Mus have been identified in the scattered light images from SPHERE (cite: Avenhaus2018), with a depression of its intensity between 25-75 au. However, on the ALMA Band 6 continuum image, there were no indications of substructures within the 80 au of the disk (cite: Ribas2023), except for a feature at $\sim$50 au. In Fig. [8](#fig:sphere-mm), we compare the radial profiles of the near-IR scattered light (1.65 $\mu$m) that shows a peak of intensity at  80 au with ALMA Band 6 continuum (1.3 mm), where the profile is extended until $\sim$60 au.

(cite: Birnstiel2015) proposed that the inconsistency between the near infrared and submillimeter observed disk profiles may be an effect of dust opacity due to dust evolution. Briefly, in the distribution of particle sizes as a function of radius, there is a disk region where the population of small grains is not replenished and fragmentation is inefficient. Hence, the turbulent diffusion cannot extend there, resulting in short dust growth and drift timescales, leading to the presence of smaller dust grains (cite: Birnstiel2015). Additionally, its predictions in the radial intensity profiles between scattered light and millimeter continuum could be in agreement with our observations at (25-50 au), where a dip in the scattered light is observed, whilst there is an absence in millimeter observations (cite: Birnstiel2015). However, the ring is detected at $\sim$(80 au), and at this radius, we have no signal from millimeter observations. Moreover, we detected a ring at $\sim 50$ au, whose results are incompatible with the predictions for this effect, that it is based on the fact that there is no structure at 1.3 mm.

![](Perfiles_B6_SPHERE.png)

# Conclusions

Protoplanetary disks are the birthplace of planetary systems, offering a unique view of the mechanisms of planet formation and disk evolution. Transitional disks, characterized by their gaps and rings, represent an intermediate stage between gas rich primordial disks and debris dominated systems. In this work, we studied the disk structure of MP Mus, as one of the closest disks to our solar system. At a distance of 97.8 pc, MP Mus is an excellent target for investigating detailed grain growth and disk evolution procedures. Previous studies of MP Mus revealed disk structures in the near-IR (due to scattering light) but a lack of resolved detections in the submillimeter data.

Here, we presented new observations of MP Mus obtained with ALMA Band 7 at 0.89 mm. These observations provide a higher spatial resolution of $\sim$5 au that complements previous Band 6 data at 1.3 mm which reaches a resolution of $\sim$4 au, allowing us to probe the disk morphology in greater detail. The spectral index ($\alpha_{mm}$) was mapped by combining multiband ALMA dust continuum data, enabling us to investigate the radial distribution of grain sizes and their implications for disk opacity and grain growth processes. Our key findings include:

- Detection of a ring structure: A ring was confirmed at $\sim 50$ au at 0.89 mm dust continuum from the ALMA Band 7 data, a feature that was not observed in our Band 6 data due to its low spatial resolution.

- Extended gas disk: A gas disk was observed to extend up to $\sim 120$ au in the $^{12}CO$ tracer, significantly beyond the dust disk ($\sim60$ au), consistent with theoretical predictions on the large gas disk radii due to radial drift. However, it can also be a contribution to dust evolution, but models for disk structure that include the total CO content are required.

- Spectral index variation: The radial variation of the spectral index in Band 6 and Band 7 showed a significant increase from $\sim 1.2$ in the inner disk to $\sim 3.0-4.0$ in the outer radius ($\sim$55 au), depending on the robust value we used. This gradient reflects the changing optical depth and grain size distribution, suggesting active processes such as radial drift and dust trapping.

- Implications for grain growth: The detection of substructures at shorter wavelengths and their absence in Band 6 implies that millimeter sized grains dominate the emission in the observed regions, providing evidence of ongoing grain growth and evolution.

- Disk classification: Putting together the relation between spectral index and type of disks, and that there is no evidence of a large inner cavity in the disk, we cannot classify MP Mus as a transitional disk. However, the ring structure detected and the indications for the radial drift process suggest an interesting stage of evolution in the disk.

In summary, our results underline the complex interplay of physical processes shaping disks such as MP Mus. The presence of a ring structure at 50 au and the radial variation of the spectral index provide critical information about disk clearing mechanisms and the initial stages of planet formation. Future theoretical modeling, coupled with more observational data (e.g., JWST and ALMA), will be the key to further understanding the dynamics and evolution of such systems.

The authors thank Professor Ruobing Dong for his kind referee report on this study. We have improved the manuscript under his suggestions. The authors thank Dr. James Miley for his guidance on the frankenstein software. A.A. acknowledges support through a Fellowship for National PhD students from ANID, grant number 21212094. A.A. acknowledges suppor from ANID, Millennium Science Initiative, via the Núcleo Milenio de Formación Planetaria (NPF). C.C. acknowledges support by ANID BASAL project FB210003. ZG is supported by the ANID FONDECYT Postdoctoral program No. 3220029. ZG is supported by the China-Chile Joint Research Fund (CCJRF No.2301) and the Chinese Academy of Sciences South America Center for Astronomy (CASSACA) Key Research Project E52H540301. CCJRF is provided by the CASSACA and established by the National Astronomical Observatories, Chinese Academy of Sciences (NAOC), and Chilean Astronomy Society (SOCHIAS) to support China-Chile collaborations in astronomy. A.R. has been supported by the UK Science and Technology Facilities Council (STFC) via the consolidated grant ST/W000997/1 and by the European Union’s Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement No. 823823 (RISE DUSTBUSTERS project). S.P. acknowledges support from FONDECYT grant 1231663 and funding from ANID – Millennium Science Initiative Program – Center Code NCN2024_001. L.A.C. acknowledges support from the Millennium Nucleus on Young Exoplanets and their Moons (YEMS), ANID - NCN2021 080 and NCN2024 001. L.A.C. acknowledges support from ANID, FONDECYT Regular grant number 1241056, Chile. W.G. acknowledges that partial support for this work was provided by Vanderbilt University’s First Center for Autism & Innovation. A.S.M. acknowledges support from ANID / Fondo 2022 ALMA / 31220025. This work was funded by ANID, Millennium Science Initiative, AIM23-0001. This paper makes use of the following ALMA data: ADS/JAO.ALMA 2017.1.01419.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, auI/NRAO and NAOJ.

78 natexlab

(ref: Andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, The Messenger, 174, 19

(ref: Andrews&Williams2005) Andrews, S. M. & Williams, J. P. 2005, ApJ, 631, 1134

(ref: Andrews&Williams2007) Andrews, S. M. & Williams, J. P. 2007, ApJ, 671, 1800

(ref: Andrews2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42

(ref: Ansdell2018) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21

(ref: Asensio-Torres2021) Asensio-Torres, R., Henning, T., Cantalloube, F., et al. 2021, A&A, 652, A101

(ref: Avenhaus2018) Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, ApJ, 863, 44

(ref: Barriere-Fouchet2005) Barrière-Fouchet, L., Gonzalez, J. F., Murray, J. R., Humble, R. J., & Maddison, S. T. 2005, A&A, 443, 185

(ref: Birnstiel2024) Birnstiel, T. 2024, ARA&A, 62, 157

(ref: BirnstielAndrews2014) Birnstiel, T. & Andrews, S. M. 2014, ApJ, 780, 153

(ref: Birnstiel2015) Birnstiel, T., Andrews, S. M., Pinilla, P., & Kama, M. 2015, ApJL, 813, L14

(ref: Birnstiel2018) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45

(ref: Bouwman2008) Bouwman, J., Henning, T., Hillenbrand, L. A., et al. 2008, ApJ, 683, 479

(ref: Carpenter2005) Carpenter, J. M., Wolf, S., Schreyer, K., Launhardt, R., & Henning, T. 2005, AJ, 129, 1049

(ref: Carrasco-Gonzalez2016) Carrasco-González, C., Henning, T., Chandler, C. J., et al. 2016, ApJL, 821, L16

(ref: Cieza2016) Cieza, L. A. 2016, in IAU Symposium, Vol. 314, Young Stars & Planets Near the Sun, ed. J. H. Kastner, B. Stelzer, & S. A. Metchev, 128–134

(ref: Cieza2008) Cieza, L. A., Swift, J. J., Mathews, G. S., & Williams, J. P. 2008, ApJL, 686, L115

(ref: Cortes2009) Cortes, S. R., Meyer, M. R., Carpenter, J. M., et al. 2009, ApJ, 697, 1305

(ref: Dasgupta2025) Dasgupta, A., Cieza, L. A., Gonzalez Ruilova, C. I., et al. 2025, arXiv e-prints, arXiv:2501.15789

(ref: Dickson2021) Dickson-Vandervelde, D. A., Wilson, E. C., & Kastner, J. H. 2021, AJ, 161, 87

(ref: Draine2006) Draine, B. T. 2006, ApJ, 636, 1114

(ref: Facchini2017) Facchini, S., Birnstiel, T., Bruderer, S., & van Dishoeck, E. F. 2017, A&A, 605, A16

(ref: Facchini2019) Facchini, S., van Dishoeck, E. F., Manara, C. F., et al. 2019, A&A, 626, L2

(ref: Flock2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68

(ref: Gaia2024) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Garufi2018) Garufi, A., Benisty, M., Pinilla, P., et al. 2018, A&A, 620, A94

(ref: Gregorio1992) Gregorio-Hetem, J., Lepine, J. R. D., Quast, G. R., Torres, C. A. O., & de La Reza, R. 1992, AJ, 103, 549

(ref: Gressel2015) Gressel, O., Turner, N. J., Nelson, R. P., & McNally, C. P. 2015, ApJ, 801, 84

(ref: Grimble2024) Grimble, W., Kastner, J., Pinte, C., et al. 2024, ApJ, 970, 137

(ref: Guilloteau2011) Guilloteau, S., Dutrey, A., Piétu, V., & Boehler, Y. 2011, A&A, 529, A105

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hu2019) Hu, X., Zhu, Z., Okuzumi, S., et al. 2019, ApJ, 885, 36

(ref: Huang2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42

(ref: Ingleby2013) Ingleby, L., Calvet, N., Herczeg, G., et al. 2013, ApJ, 767, 112

(ref: Jennings2020) Jennings, J., Booth, R. A., Tazzari, M., Rosotti, G. P., & Clarke, C. J. 2020, MNRAS, 495, 3209

(ref: Kastner2010) Kastner, J. H., Hily-Blant, P., Sacco, G. G., Forveille, T., & Zuckerman, B. 2010, ApJL, 723, L248

(ref: KastnerPrincipe2022) Kastner, J. H. & Principe, D. A. 2022, in Handbook of X-ray and Gamma-ray Astrophysics, ed. C. Bambi & A. Sangangelo, 49

(ref: Kuwahara2024) Kuwahara, A., Lambrechts, M., Kurokawa, H., Okuzumi, S., & Tanigawa, T. 2024, A&A, 692, A45

(ref: Long2018) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17

(ref: Mamajek2002) Mamajek, E. E., Meyer, M. R., & Liebert, J. 2002, AJ, 124, 1670

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Murphy2013) Murphy, S. J., Lawson, W. A., & Bessell, M. S. 2013, MNRAS, 435, 1325

(ref: NattaTesti2004) Natta, A. & Testi, L. 2004, in Astronomical Society of the Pacific Conference Series, Vol. 323, Star Formation in the Interstellar Medium: In Honor of David Hollenbach, ed. D. Johnstone, F. C. Adams, D. N. C. Lin, D. A. Neufeeld, & E. C. Ostriker, 279

(ref: Oberg2021) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1

(ref: Oberg2011) Öberg, K. I., Qi, C., Fogel, J. K. J., et al. 2011, ApJ, 734, 98

(ref: Okuzumi2016) Okuzumi, S., Momose, M., Sirono, S.-i., Kobayashi, H., & Tanaka, H. 2016, ApJ, 821, 82

(ref: OkuzumiTazaki2019) Okuzumi, S. & Tazaki, R. 2019, ApJ, 878, 132

(ref: Perez2015) Pérez, L. M., Chandler, C. J., Isella, A., et al. 2015, ApJ, 813, 41

(ref: Pinilla2014) Pinilla, P., Benisty, M., Birnstiel, T., et al. 2014, A&A, 564, A51

(ref: Pinte2023) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645

(ref: Ribas2017) Ribas, Á., Espaillat, C. C., Macı́as, E., et al. 2017, ApJ, 849, 63

(ref: Ribas2023) Ribas, Á., Macı́as, E., Weber, P., et al. 2023, A&A, 673, A77

(ref: Ricci2012) Ricci, L., Testi, L., Natta, A., Scholz, A., & de Gregorio-Monsalvo, I. 2012a, ApJL, 761, L20

(ref: Ricci2012A) Ricci, L., Trotta, F., Testi, L., et al. 2012b, A&A, 540, A6

(ref: Ruge2016) Ruge, J. P., Flock, M., Wolf, S., et al. 2016, A&A, 590, A17

(ref: Schutz2005a) Schütz, O., Meeus, G., & Sterzik, M. F. 2005, A&A, 431, 165

(ref: SeguraCox2020) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228

(ref: Shi2024) Shi, Y., Long, F., Herczeg, G. J., et al. 2024, ApJ, 966, 59

(ref: Sierra2017) Sierra, A., Lizano, S., & Barge, P. 2017, ApJ, 850, 115

(ref: Sierra2019) Sierra, A., Lizano, S., Macı́as, E., et al. 2019, ApJ, 876, 7

(ref: Simon2017) Simon, M., Guilloteau, S., Di Folco, E., et al. 2017, ApJ, 844, 158

(ref: TakahashiInutsuka2014) Takahashi, S. Z. & Inutsuka, S.-i. 2014, ApJ, 794, 55

(ref: Tazzari2021) Tazzari, M., Testi, L., Natta, A., et al. 2021, MNRAS, 506, 5117

(ref: Testi2014) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339–361

(ref: Torres2008) Torres, C. A. O., Quast, G. R., Melo, C. H. F., & Sterzik, M. F. 2008, in Handbook of Star Forming Regions, Volume II, ed. B. Reipurth, Vol. 5, 757

(ref: Trapman2019) Trapman, L., Facchini, S., Hogerheijde, M. R., van Dishoeck, E. F., & Bruderer, S. 2019, A&A, 629, A79

(ref: VanderMarel2016) van der Marel, N., Cazzoletti, P., Pinilla, P., & Garufi, A. 2016, ApJ, 832, 178

(ref: Varga2024) Varga, A., Kastner, J. H., Dickson-Vandervelde, D. A., & Binks, A. 2024, AJ, 168, 251

(ref: Villenave2019) Villenave, M., Benisty, M., Dent, W. R. F., et al. 2019, A&A, 624, A7

(ref: Ward2000) Ward, W. R. & Hahn, J. M. 2000, in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell, 1135

(ref: Weidenschilling1977) Weidenschilling, S. J. 1977, MNRAS, 180, 57

(ref: Weise2010) Weise, P., Launhardt, R., Setiawan, J., & Henning, T. 2010, A&A, 517, A88

(ref: Williams&Cieza2011) Williams, J. P. & Cieza, L. A. 2011, ARA&A, 49, 67

(ref: Wolff2016) Wolff, S. G., Perrin, M., Millar-Blanchaer, M. A., et al. 2016, ApJL, 818, L15

(ref: Zhang2015) Zhang, K., Blake, G., & Bergin, E. 2015, in IAU General Assembly, Vol. 29, 2256118

(ref: Zhu2014) Zhu, Z., Stone, J. M., Rafikov, R. R., & Bai, X.-n. 2014, ApJ, 785, 122

(ref: Zurlo2020) Zurlo, A., Cugno, G., Montesinos, M., et al. 2020, A&A, 633, A119

# Tables

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ALMA | ALMA | Date | Time on source | $N_{\rm ant}$ | Baselines | PWV | Flux Calibrator |
| Project Code | Band |  | (min) |  | \(m\) | \(mm\) |  |
| 2017.1.01167.S | 6 | 2017-11-16 | 11.4 | 44 | 92 - 8283 | 1.1 | J1427-4206 |
|  | 6 | 2018-01-15 | 5.6 | 46 | 15 - 2387 | 1.6 | J1427-4206 |
| 2017.1.01419.S | 6 | 2017-12-26 | 16.7 | 43 | 15 - 2516 | 0.34 | J1427-4206 |
|  | 6 | 2018-06-06 | 8.3 | 44 | 15 - 313 | 0.72 | J1427-4206 |
| 2021.1.01205.S | 7 | 2021-11-20 | 24.2 | 44 | 41 - 3638 | 0.36 | J1427-4207 |
|  | 7 | 2022-08-19 | 6.0 | 44 | 15 - 1301 | 0.32 | J1427-4206 |

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ALMA | ALMA | Central Freq. | Bandwidth | Channels | Spectral lines |  |
| Project Code | Band | (GHz) | (Mhz) |  |  |  |
| 2017.1.01167.S | 6 | 232.485 | 2000 | 128 | ... |  |
|  |  | 244.984 | 2000 | 128 | ... |  |
|  |  | 246.984 | 20000 | 128 | ... |  |
|  |  | 230.531 | 1875 | 960 | $^{12}CO(2-1)$ |  |
| 2017.1.01419.S | 6 | 217.550 | 2000 | 128 | ... |  |
|  |  | 232.800 | 2000 | 128 | ... |  |
|  |  | 219.494 | 1875 | 3840 | $^{13}CO(2-1), C^{18}O(2-1)$ |  |
|  |  | 230.620 | 234 | 1920 | $^{12}CO(2-1)$ |  |
|  |  | 231.205 | 234 | 1920 | ... |  |
| 2021.1.01205.S | 7 | 343.609 | 2000 | 128 | ... |  |
|  |  | 345.188 | 117 | 960 | ... |  |
|  |  | 345.788 | 117 | 960 | $^{12}CO(3-2)$ |  |
|  |  | 355.067 | 1875 | 3840 | $HCN(4-3)$ |  |
|  |  | 356.722 | 938 | 3840 | $HCO^{+}(4-3)$ |  |

# Line cube images

![](Imagenes_lineas_B6_B7_2.png)

# Line radial profiles

![](Line_profiles.png)

# Gas disk radii

We measured the gas size by using the lines we had available. For this, we deprojected moment 0 images using position angle and inclination previously estimated by a 2D Gaussian fit of the continuum and then, extracted deprojected azimuthally averaged radial profiles of the gas emission lines. We considered the following definition for integrated disk flux:

$$\begin{equation}
    F(r) = 2\pi \int_{0}^{r} I(s)sds
\end{equation}$$

where $s$ is the projected radial coordinate in the sky and $I(s)$ is the observed intensity. We estimated the gas disk radius, $R_{gas}$, as the radius that contains 95$\%$ of the total flux. We obtained an $R_{^{12}CO(2-1)}$ of 110.8 $\pm$ 8.9 au and an $R_{^{12}CO(3-2)}$ of 121.7 $\pm$ 9.7 au.

[^1]: See [ALMA Technical Handbook](https://almascience.nrao.edu/documents-and-tools/cycle12/alma-technical-handbook), Eq. 3.28 and Sect. 7.2

</paper>

Write the methods card for this paper.