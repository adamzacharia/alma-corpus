# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...990L..70L\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...990L..70L",
 "title": "Discovery of Hα Emission from a Protoplanet Candidate around the Young Star 2MASS J16120668─3010270 with MagAO-X",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Li, Jialin",
 "n_authors": 35,
 "arxiv_id": "2508.11155",
 "doi": "10.3847/2041-8213/adfcbd",
 "alma_projects_linked_by_archive": [
  "2022.1.00646.S"
 ]
}
```

Paper text:
<paper>
# Discovery of H$\alpha$ Emission from a Protoplanet Candidate Around the Young Star 2MASS J16120668-3010270 with MagAO-X

## Abstract

2MASS J16120668-3010270 (hereafter 2MJ1612) is a young M0 star that hosts a protoplanetary disk in the Upper Scorpious star-forming region. Recent ALMA observations of 2MJ1612 show a mildly inclined disk ($i$=37$^\circ$) with a large dust-depleted gap (R$_\text{cav}\approx$0.4" or 53 au). We present high-contrast H$\alpha$ observations from MagAO-X on the 6.5m Magellan Telescope and new high resolution sub-mm dust continuum observations with ALMA of 2MJ1612. On both 2025 April 13 and 16, we recovered a point source with H$\alpha$ excess with SNR $\gtrsim$5 within the disk gap in our MagAO-X Angular and Spectral Differential (ASDI) images at a separation of 141.96$\pm$2.10 mas (23.45$\pm$0.29 au deprojected) from the star and position angle (PA)= 159.00$\pm$0.55$^\circ$. Furthermore, this H$\alpha$ source is within close proximity to a K band point source in SPHERE/IRDIS observation taken in 2023 July 21 (cite: sphere2025sub). The astrometric offset between the K band and H$\alpha$ source can be explained by orbital motion of a bound companion. Thus our observations can be best explained by the discovery of an accreting protoplanet, 2MJ1612 b, with an estimated mass of 4$M_\text{Jup}$ and H$\alpha$ line flux ranging from (29.7 $\pm$7.5)$\times$10$^{-16}$ ergs/s/cm$^2$ to (8.2$\pm$3.4)$\times$10$^{-16}$ ergs/s/cm$^2$. 2MJ1612 b is likely the third example of an accreting H$\alpha$ protoplanet responsible for carving the gap in its host disk, joining PDS 70b and c. Further study is necessary to confirm and characterize this protoplanet candidate and to identify any additional protoplanets that may also play a role in shaping the gap.

show\]jialinli@arizona.edu

\]jrmales@arizona.edu

\]haffert@strw.leidenuniv.nl

\]kfollette@amherst.edu

\]sandrews@cfa.harvard.edu

\]John.Carpenter@alma.cl

\]warrenbfoster@gmail.com

\]kvangorkom@email.arizona.edu

\]Alexander.Hedglen@ngc.com

\]gherczeg1@gmail.com

\]jkueny@arizona.edu

# Introduction

Protoplanetary disks have shown a variety of substructures in high-resolution observations at sub-mm and infrared/optical wavelengths (see review by (cite: 2020ARA&A..58..483A) (cite: 2020ARA&A..58..483A) and conference proceeding series by (cite: 2023ASPC..534.....I) (cite: 2023ASPC..534.....I)). Interactions between protoplanets and their host disks can alter the environment, and the presence of these substructures is often interpreted as signs of ongoing planet formation (cite: 2024A&A...685A..52G; 2018ApJ...869...17L; 2018ApJ...869L..41A). The origins of these substructures, whether attributed solely or partially to planet formation or other processes within disks, remain unclear as they are inferred from the substructures themselves rather than their direct causes (cite: 2023ASPC..534..423B; 2018ApJ...869L..47Z; 2016ApJ...826...75D).

Imaging protoplanets inside these circumstellar disks is difficult because there are multiple noise sources that mimic point source signals; residual wavefront errors create stellar speckles and High Contrast Imaging (HCI) post-processing algorithms can spatially filter and turn scattered light off dust into point sources. Therefore, many detected candidates embedded in dust are highly controversial (cite: 2017AJ....153..264F; 2017AJ....153..244R). Thus, observations have targeted systems with large gaps in attempts to recover protoplanets (e.g., HD 169142 b, (cite: 2023MNRAS.522L..51H); GAPlanetS Survey, (cite: 2023AJ....165..225F)). Tracing giant planets through their accretion signatures (i.e. hydrogen recombination lines) may result in a clearer identification of protoplanet candidates. The only bona fide accreting protoplanets, PDS 70b and c, serve as an example where the detection of H$\alpha$ (656.3 nm) protoplanet accretion flux enables clear identification of the companions from disk structures (cite: 2018ApJ...863L...8W; 2019NatAs...3..749H). Furthermore, lower mass giant planets ($\lesssim$5M$_{Jup}$) can have higher planet/star contrast at H$\alpha$ than in the near infrared, which decreases the threshold of detection (cite: 2014ApJ...781L..30C). The high angular resolution ($\sim$ 25 mas at D= 6.5m) at H$\alpha$ or nearby continuum (668 nm) may also enable circumplanetary disk (CPD) material to be resolved (cite: 2025AJ....169...35C). Unfortunately, detection of hydrogen recombination lines can also result from scattered stellar accretion signatures off dust structures (cite: 2023AJ....166..220Z). However, removal of the stellar accretion signature can be made possible through spectral differential imaging (cite: 2000PASP..112...91M), where the stellar contribution to the accretion line flux can be measured in respect to a neighboring continuum wavelength (see (cite: 2023AJ....165..225F) for more details). Consequently, the scattered stellar accretion flux can be subtracted from the H$\alpha$ image, revealing the protoplanets (cite: 2014ApJ...781L..30C).

Young systems ($\lesssim$ 10 Myr) like PDS 70 are optimal targets for the search of accreting protoplanets as their large dust-depleted cavities minimize extinction, while gas is still present and available for accretion. Large dust cavities have been hypothesized to result from planetary systems in mean motion resonance (MMR) with overlapping dust clearing regions of $\sim$4-10$\times$Hill Sphere (cite: 2020AJ....160..221C; 2020MNRAS.499.2015T; 2019ApJ...884L..41B; 2011ApJ...738..131D) or from more disruptive orbits of single companions (cite: 2022AJ....164...29B; 2018MNRAS.477.1270P). The former hypothesis has been supported by observations of PDS 70b and c, which are in near-circular orbits migrating into a 2:1 MMR (cite: 2019NatAs...3..749H; 2021AJ....161..148W).

As revealed by recent Atacama Large Millimeter/submillimeter Array (ALMA) observations with moderate resolution (0.2-0.3", (cite: 2024ApJ...974..102S; 2025ApJ...978..117C)), 2MASS J16120668-3010270 (a.k.a. UCAC4 300-090317, hereafter 2MJ1612) hosts a protoplanetary disk with a large dust and gas depleted gap very similar to that observed around PDS 70. This 5-10 Myr M0 (0.7M$_\odot$) star, located 131.9$\pm$0.3 pc away in the Upper Scorpius star-forming region (cite: 2021AJ....161..147B; 2023A&A...674A...1G), has a mildly inclined ($i$=37$\ensuremath{^\circ}$) disk that exhibits a bright dust ring peaking at 0.57" (75 au) as well as a faint inner disk in sub-mm (cite: 2024ApJ...974..102S). (cite: 2024ApJ...974..102S) reported a 3$\sigma$ compact sub-mm continuum source near the center of the gap at a projected radius of 0.2" (26.4 au) from the central star, which was proposed as a CPD candidate. They also identified a kinematic kink that may be a result of the dynamical interaction between the disk and an embedded planet (cite: 2018ApJ...860L..13P), located at 0.875" (115.6 au) in the $^{12}$CO channel maps. The disk of 2MJ1612 was resolved for the first time in scattered light using VLT/SPHERE in the work by (cite: sphere2025sub), revealing an inner disk with two spiral arms extending out to $\sim$40 au. Furthermore, they tentatively detected 2 unpolarized point sources in H and K bands, albeit at different positions. Their hydrodynamic modeling suggests the disk features are consistent with the presence of an unseen gas giant planet between 0.1 and 5 M$_\text{Jup}$ at an orbital distance greater than the detected point sources. All of these features observed in the sub-mm and NIR make 2MJ1612 a prime target to search for accreting planets that may carve the gap (R$_{cav}\sim$0.4" or 53 au).

In this letter, we present observations of 2MJ1612 using MagAO-X on the 6.5m Magellan Clay Telescope in Chile (cite: 2024SPIE13097E..09M; 2018SPIE10703E..09M). This target was observed as part of the MagAO-X H$\alpha$ Protoplanet Survey (cite: 2020AJ....160..221C). We also present a high-resolution ($\sim$0.08") millimeter continuum map of 2MJ1612, taken as part of a disk structure survey of bright Upper Sco disks with ALMA in Cycle 9. Observational setup, along with data selection and reduction, is detailed in Section [2](#sec:Observations). Results and discussion are detailed in Section [3](#sec:results+discussion). We summarize our findings in Section [4](#sec:conclusion).

![](Fig1-v2.png)

# Observations and Data Reduction

## H$\alpha$ SDI with MagAO-X

We observed 2MJ1612 on 2025 April 13 and 16 with the 6.5m Magellan Clay telescope as part of MaXProtoPlanetS Survey (cite: 2025AJ....169...35C). We used the Angular and Spectral Differential Imaging (ASDI) technique (cite: 1999PASP..111..587R; 2000PASP..112...91M; 2006ApJ...641..556M; 2006SPIE.6269E..3MM; 2025AJ....169...35C), and observed through narrow H$\alpha$ ($\lambda_o$=0.656 $\mu$m, $\Delta \lambda$~eff~=0.001 $\mu$m) and continuum ($\lambda_o$=0.668 $\mu$m, $\Delta \lambda$~eff~=0.008 $\mu$m) filters on two separate science cameras simultaneously. The observation conditions, AO setup and camera settings can be found in Table [\[tab:table\]](#tab:table). We did not use a coronagraph because the observation would not have strongly benefited due to the faintness (I$\sim$12 mag; V=13.3 mag) of the central star. The predicted Strehl ratio drops below 20$\%$ for a guide star fainter than I=12 mag at the H$\alpha$ (cite: 2018SPIE10703E..09M). We present the first on-sky, high-contrast H$\alpha$ images acquired using a guide star of this faint magnitude.

In addition to its faintness, the maximal elevation of 88.77$^{\circ}$ during transit made 2MJ1612 a very difficult target to observe at transit; the significant increase in azimuthal velocity of the Alt-Az telescope near zenith leads to rapid field rotation and off-loading challenges for the AO system. In attempts to keep applying AO corrections, the parameters of the AO system were adjusted during the observations, which also maintains the best performance of the system. Specifically for the 10-15 mins before and after transit, we follow the following prescription to keep the AO system locked on the star. The intervals of tip/tilt off-loading from Alpao DM-97 woofer to Clay telescope are shortened to 1s while the offload gain is slowly increased by 5 times to prevent saturation in DM stroke and maintain AO stability. The interval continues to shorten as time to transit gets closer, and the offloading interval and gain slowly revert to the original value after transit.

On 2025 Apr 13 and in seeing of 0.68-1.08", the AO was locked with 288 modes of correction applied on the star throughout transit in the first epoch observation, yielding $\sim$170$^\circ$ of total sky rotation. This dataset contains $\sim$1.5 hr of 3s exposure frames. The second epoch observation on 2025 Apr 16 was observed in better seeing conditions (0.34-0.52"), which enabled corrections of higher order modes up to 840 and shorter single frame exposure times. However, the AO loop was lost for about 6 mins shortly after transit, costing us about 40$^\circ$ of rotation. This latter dataset contained 1.25 hr of 1s exposure frames and $\sim$ 172$^\circ$ rotation, along with a higher Strehl PSF, but with larger systematic changes in eccentricity (0.22-0.58) than the previous night ($\sim$0.2). The Strehl ratio at H$\alpha$ for Apr 13 and 16 are respectively 2.83$\%$-5.17$\%$ and 9.55$\%$-18.95$\%$. [^1]

## MagAO-X Data Selection and Reduction

Data selection and reduction was conducted similarly to the successful approach used for PDS 70b and c in (cite: 2025AJ....169...35C), and are identical for the two science cameras. In short, the procedures are as follows: frame selection, alignment, combination, starlight subtraction with PyKLIP and SDI. Since high counts are a convenient indicator of high Strehl ratio, we performed thresholding on each of the 1024$\times$1024 pixel images to ensure image quality. We rejected data with lower Strehl, which are roughly 70$\%$ and 25$\%$ of the total data for the April 13 and 16 data. We first assign the pixel with the maximal count as the central star location and refine it during the subsequent reduction process. A box of size 256$\times$256 pixels centered on the rough position of the star is cropped out of each image to enable more efficient processing. This translates to a box of size 1.51"$\times$1.51" with the MagAO-X average pixel scale being 5.93$\pm$0.03 mas per pixel (cite: 2025AJ....169...36L). When searching for companions further out, the size of the box is adjusted to ensure the object of interest is in a region of the frame where edge effects are negligible. For 2MJ1612, a separate reduction of 512$\times$512 pixel images was made to search for the potential companion associated with the kinematic kink at $\sim$0.87".

All frames that meet the selection criteria described above are aligned via cross-correlation with bi-cubic interpolation using the OpenCV Python package to account for shifts up to the one-hundredth of a pixel (cite: opencv_library). The first 50 frames with the highest counts are aligned to each other, median-combined, and shifted such that the star is centered on the central pixel of the image; this serves as the reference for cross-correlating the rest of the dataset. To reduce runtime, only a 32$\times$32 pixel image stamp around the star position in the 256$\times$256 pixel image is used for alignment measurements. The final percentages of frames kept for both epochs of data can be found in Table [\[tab:table\]](#tab:table).

Because the expected H$\alpha$ flux from the protoplanets is low, we carefully combine the selected frames to preserve every detected photo-electron from the planet and ensure that the planet’s light survives PSF subtraction. This approach combines a number of frames via summation to create one “combined frame" with a longer exposure time and a larger number of H$\alpha$ counts. Rather than frame summing by time, a method shown to be effective in (cite: 2025AJ....169...35C), frame averaging by parallactic angle (PARANG) is an alternative co-adding method used for data that lack consistent and consecutive observations through transit or a lack of diversity in PARANG (cite: 2024SPIE13097E..14L). The PARANG value associated with each “combined frame" is the average of the individual PARANG values associated with the original frames and can be found in Table [\[tab:table\]](#tab:table). Averaging equal amounts of PARANG rotation is particularly good for observations with lower total sky rotation and observations with less evenly distributed frames across PARANG, as this approach creates a more evenly spaced data cube to enhance ADI performance. Thus, we applied this method to the Apr 13 observation. For the Apr 16 observation, which has a significant gap in the PARANG sequence after transit, we opted to use a hybrid method. This approach combines frames by time when the PARANG varies slowly with time, and combines frames by PARANG when the PARANG changes rapidly. Additional adjustments have been made to ensure the number of individual frames used for one combined frame is not too few or too many, stabilizing the quality of the combined frame PSF. Details of this reduction method are further discussed in Appendix [6](#sec:25a-reduction). We have found that having 50 to 200 average combined frames leads to higher efficiency and ensures the diversity in PARANG for increased angular differential imaging (ADI) performance (cite: 2006ApJ...641..556M). A Gaussian high-pass (HP) filter is applied to individual combined frames, serving as a substitute for dark subtraction and helps to remove the smooth stellar halo that dominates low spatial frequencies. The Gaussian HP filter applied has a standard deviation value of 5 pixels (FWHM$\approx$ 2.35$\times$5 = 11.75 pixels) for both epochs of observation. Hence, the planet light (FWHM$\leq$8 pixels) is mostly unaffected by the HP filter, but the stellar halo is removed.

We used the Python package PyKLIP (cite: 2015ascl.soft06001W) to perform KLIP-ADI for starlight subtraction. Karhunen-Loève Image Projection (cite: 2012ApJ...755L..28S) is a method to perform point-spread function (PSF) subtractions by decomposing a set of reference PSF images, which is the data set itself, into Karhunen-Loève (KL) modes and projecting the target image onto these modes to model and remove the stellar PSF, enhancing the detection of faint exoplanets and circumstellar disks (cite: 2012ApJ...755L..28S). Three key parameters in PyKLIP can affect the stellar PSF reconstruction and subtraction: ${\tt annuli}$, ${\tt subsections}$, and ${\tt numbasis}$ (cite: 2023AJ....165...57A). The PSF is modeled in annular segments (${\tt annuli}$), each subdivided into equal subsections (${\tt subsections}$) and with a number of KL modes or principal components (${\tt numbasis}$). PyKLIP produces a de-rotated data cube containing the images after the removal of inputted number of principal components. We reduced our data with 4 subsections, 10 annuli, and 1 to 50 KL modes subtracted. The ${\tt movement}$ parameter, an exclusion criterion for selecting reference PSFs, was set to values ranging from 0-5 pixels; Low values of ${\tt movement}$ minimize disk features which aids in the recovery of point sources, at the cost of increased self-subtraction. In other words, the reconstruction of the target PSF does not use images in its PSF mode library/co-varience matrix, where the rotation of the companion between the target and reference is less than the given ${\tt movement}$ value.

Residual starlight and scattered light from disk structures are eliminated by creating a final ASDI image, formed by subtracting the KLIP-ADI continuum image from the H$\alpha$ image, both reduced with the same KLIP parameters to minimize PSF differences from starlight subtraction. Before subtraction, the continuum image is scaled by the central star’s flux ratio between the two filters to account for its flux differences at the two wavelengths. Aperture photometry on the median image of the dataset measures the central star’s flux, with an uncertainty of $\sim$0.2$\%$, dominated by photon noise. This should eliminate both residual starlight and scattered light from disk structures. We also scaled the continuum image spatially by the ratio of the two wavelengths (656.3/668 = 0.98), to account for the slight change in the star’s diffraction pattern with wavelength before ASDI subtraction.

cc\|cc\|cc & &\
& Camera 1 (Cont) & Camera 2 (H$\alpha$) & Camera 1 (Cont) & Camera 2 (H$\alpha$)\

& Seeing ($^{\prime\prime}$) & &\
& Wind (mph) & &\
& Photometric Sky? & &\

& \# of AO modes corrected & &\
& AO Loop Speed (Hz) & &\

& Exposure Time (DIT) & &\
& Filter Central Wavelength (nm) & 668 & 656.3 & 668 & 656.3\
& Filter Width (nm) & 8 & 1.045 & 8 & 1.045\
& EM as set on camera & 900 & 900 & 900 & 900\
& $EM_{\mathrm{gain}}$ (ADU/e$^-$) & 197.18$\pm$2.85 & 292.91$\pm$0.25 & 197.18$\pm$2.85 & 292.91$\pm$0.25\

& Percentages of Frames Kept & 30.04% & 30.85% & 76.57% & 76.22%\
& Total Exposure Time (min) & 27.0 & 28.6 & 70.7 & 71.4\
& \# of Frames Kept & 548 & 571 & 4239 & 4286\
& Total ADI Rotation ($^\circ$) & 167 & 169 & 172 & 172\
& PARANG Bin Size ($^\circ$) & 1.7 & 1.7 & 3.01 & 3.01\
& FWHM of PSF (pixels) & 11.7 & 11.9 & 7.2 & 7.1\
& Strehl Ratio & &\
& PSF Eccentricity & &\

& Separation (mas) & &\
& PA ($^\circ$) & &\
& H$\alpha$ SNR & &\
& ASDI SNR & &\
& H$\alpha$ Contrast & &\
& ASDI Contrast & &\
& $\beta$ & &\
& H$\alpha$ Line Flux (erg s$^{-1}$ cm$^{-2}$) & &\
& $\dot M$ ($M_{\odot}$ yr$^{-1}$) & &\

## Astrometry and Photometry of Planet Candidate 2MJ1612 b

PSF subtraction algorithms can distort the companion PSF; ADI introduces self-subtraction artifacts in the azimuthal direction, while SDI causes self-subtraction along the radial direction from the wavelength-dependent scaling. As a result, we cannot rely solely on Gaussian fitting to retrieve the position and flux of the companion. Instead, we obtained companion astrometry and photometry with the forward modeling feature in PyKLIP (cite: 2015ascl.soft06001W; 2016AJ....152...97W; 2016ApJ...824..117P) for accurate measurements and uncertainties on the companion parameters. We determine the initial position of the companion by fitting a Gaussian to the ASDI images. A grid of negative planets is injected into the datacube of combined frames around the initial position with $\Delta$ Position Angle (PA)=$\pm$5$^{\circ}$ of 0.5$^{\circ}$ increments and $\Delta$separation=29.65 mas of 2.97 mas increments. The astrometric error is broadly consistent with the uncertainty estimated as the companion PSF’s post-KLIP FWHM divided by its SNR, which is $\sim$6 mas. Note that all planets are injected with the same flux for optimizing the location. Thus, the optimal candidate location is identified as the negative planet position that minimizes flux within a circular aperture, with a radius equivalent to the FWHM of the PSF, centered around the injected companion. To account for the uncertainty of the initial position, the optimal location is taken to be the median value of positions with minimized total flux with aperture radii ranging from 0.75 FWHM to 1.5 FWHM.

To calculate the final astrometric error, we must also consider the uncertainties of the MagAO-X true-north offset and pixel scale, which are both reported in detail by (cite: 2025AJ....169...36L). For the true-north rotation correction, we adopted the value of 2.0$\pm$0.6$^\circ$. The central offset value was calibrated using same-night observations of systems with known orientations, and the uncertainty is taken as the standard deviation of all past measurements to account for year-to-year variations (cite: 2025AJ....169...36L). We adopted the pixel scale of 5.93$\pm$0.03, the average and standard deviation of all measurements from Table 4 of (cite: 2025AJ....169...36L) since its variation by year is much less compared to that of the true-north rotation. Adding the uncertainty from retrieval, plate scale, and true-north offset in quadrature, the final uncertainty in separation and PA are respectively 2.97 mas and 0.78$^\circ$. We determined the contrast of the companion in a similar method by injecting negative fake planets of various flux at the optimized position, but we minimized the root-mean-square (RMS) of the individual pixel values in the aperture centered on the optimized position. The uncertainty in contrast is obtained through calculating the ratio between the standard deviation in a ring of fake injected planets with the optimal positive flux at the optimal separation, and the flux of the central star (see Appendix B from (cite: 2025AJ....169...35C) for more details).

## Signal to Noise Calculations

To estimate the significance of candidate detection in regions dominated by residual speckle noise, we calculate the signal-to-noise ratio (SNR) considering small sample statistics rather than the standard Gaussian approach (cite: 2014ApJ...792...97M). A ring of one FWHM-wide aperture is placed at the optimal separation as the planet candidate. We find that the FWHM of the source in the KLIP-ADI image can be slightly smaller (FWHM$_{\text{source}}$ $\lesssim$ FWHM$_{\text{PSF}}$ - 1 pixel) than the unprocessed median stellar PSF, likely a result of the high-pass filter and the azimuthal self-subtraction. Thus, the diameter of apertures ranged from 6-8 pixels. The total flux within the circular aperture centered on the source is treated as the signal, while the standard deviation of fluxes in the surrounding noise apertures defines the noise. Due to the small separation between the central star and the source, we followed the two-sample t-test defined in (cite: 2014ApJ...792...97M). See Table 1 and the next section for our SNR values.

# Results and Discussion

We identified a compact point source with H$\alpha$ excess in both epochs of MagAO-X observations within the gap of the dust disk of 2MJ1612 as shown in Figure [1](#fig:ALMA). The point source has an SNR= 5.3 and 3.7 in the Apr 13 and Apr 16 H$\alpha$ images. Bright residuals from the wind-driven halo (cite: 2020A&A...638A..98C) in the Apr 16 continuum and H$\alpha$ images likely reduce the H$\alpha$ SNR that night. The effects of the WDH remain the same between the cameras, thus with identical reduction procedures, the residual WDH blobs can be well removed in the ASDI image, increasing the SNR to 5.1 for the point source at 0.145"$\pm$0.003" and PA= 158.00$\pm$0.78$^\circ$ in the Apr 16 data. Despite the low Strehl of 3-5$\%$ in the Apr 13 data, we still recover a point source with SNR=5.5 in the ASDI image at sep 0.139"$\pm$0.003" and PA= 160.60$\pm$0.78$^\circ$. The contrast of the sources in the ASDI images are (4.0$\pm$0.9)$\times$10$^{-3}$ and (1.0$\pm$0.4)$\times$10$^{-3}$ respectively for Apr 13 and 16.

The small offset ($\approx$ 1 pix) between the position between the 2 observations can be well explained by the astrometric uncertainties and difference in SNR between the two epochs. Thus, we conclude that the H$\alpha$ excess detected in both epochs are certainly coming from the same source at an average separation = 141.96$\pm$2.10" and PA= 159.00$\pm$0.55$^\circ$. This translates to a de-projected separation of 23.8$\pm$1.7 au, assuming the companion is coplanar with the disk (i$\sim$37$^{\circ}$; disk PA=45$^{\circ}$). Although the mass of the source cannot be constrained with H$\alpha$ photometry, the non-detection at continuum wavelengths suggests the companion is a substellar object, possibly a protoplanet.

## Comparison to SPHERE/IRDIS Observations

2MJ1612 observation with SPHERE using the Infra-Red Dual Imaging and Spectrograph (cite: 2008SPIE.7014E..3LD) in 2023 revealed an H band (1.6 $\mu$m) unpolarized source at separation= 0.129"$\pm$0.011" and PA=151$\pm$3$^\circ$ and a K band point source at separation = 0.172"$\pm$0.017" and PA=195$\pm$4$^\circ$ (cite: sphere2025sub). Despite its closer proximity to the H$\alpha$ source and absence in the H-band polarized intensity, the low SNR and elongation in the radial direction of the H band unpolarized source indicate its likely an artifact created from the disk signal by self-subtraction introduced in the classical ADI reduction (cite: sphere2025sub). This is consistent with the non-detection of this H band source in the K band iterative reference differential imaging (iRDI) processed image of the second epoch of SPHERE observation.

Unlike the H band source, the K source is more likely to be thermal light emitted by a young planetary photosphere, as K observations are more sensitive to redder objects. It is also less likely to originate from residual disk light, as RDI minimizes self-subtraction of extended structures like disks. Furthermore, the mass derived ($\sim4M_\text{Jup}$) from K band photometry of $\sim\Delta$9.2 mag is consistent with the planet mass ($>5M_\text{Jup}$) estimated from the hydrodynamical simulations (cite: sphere2025sub) and masses of known accreting protoplanets (cite: 2021AJ....161..148W). Assuming the K-band source is of astrophysical origin, the close proximity of the K band point source to the MagAO-X H$\alpha$ source shown in Figure [2](#fig:orbit), may originate from the same object. The astrometric offset can be explained by the prograde orbital motion from the two-year interval between observations. We adopt a larger error bar of 1 FWHM for both the K (0.0675") and H$\alpha$ (0.03") astrometry to account for the uncertainty of an embedded, low SNR object and the potential additional systematic plate scale errors from different telescopes/instruments.

![](Fig2+3.png)

Rather than the Markov Chain Monte Carlo (MCMC) algorithm, we use the Orbits For The Impatient (OFTI) algorithm (cite: 2017AJ....153..229B) implemented in the `orbitize!` python package (cite: 2020AJ....159...89B), for a faster convergence in fitting an orbit with limited coverage of orbital fraction; OFTI is a rejection sampling algorithm that generates orbital parameters from prior distributions, rescales them to match the astrometric observations, and accepts or rejects them based on their likelihood to efficiently sample the posterior for sparsely observed orbits (cite: 2017AJ....153..229B).

The adopted priors used for the orbital fit are loosely constrained by observed disk properties. The system mass is set to be $M_\text{tot}$=0.70$\pm$0.05$M_\odot$, the derived dynamical mass from the $^{12}$CO velocity map fits by (cite: 2024ApJ...974..102S). The semi-major axis is assigned a uniform prior from 1 to 60 au, which encompasses the region within the outer disk. A Gaussian prior is placed on inclination centered at the disk inclination of 37$^\circ$ with a standard deviation of 5$^\circ$ (cite: sphere2025sub), as co-planar orbit is commonly expected for embedded or recently formed planets (cite: 2006A&A...447..369K; 2016ApJ...816L..12D). The eccentricity prior is chosen to be a Guassian centered at 0.1 with standard deviation of 0.1, allowing exploration of a broad range of orbital shapes while favoring circular orbits. This choice is motivated the lack of disk asymmetries in the sub-mm and NIR observations other than the inner disk with spiral arms, as features such as eccentric rings are known to be produced a companion on an eccentric orbit in simulations (cite: 2022ApJ...925...95T). The 50 highest-likelihood orbits out of the 10,000 accepted solutions have orbital periods of approximately 100 years and are shown in of Figure [2](#fig:orbit)b. The corner plot detailing semimajor axis, eccentricity, inclination, argument of periastron, longitude of ascending node, epoch of periastron ($\tau$), system mass, and system parallax can be found in Fig [4](#fig:corner) of Appendix [7](#sec:24a).

The orbital fit should be interpreted with caution due to a few underlying caveats. The current astrometric data lack sufficient orbital phase coverage, and additional epochs are required to constrain the orbit meaningfully (cite: 2021AJ....161..241F). Thus, we only used the observed separation for further analysis rather than the fitted separation in App [7](#sec:24a) Fig [4](#fig:corner). The H$\alpha$ source is located at the edge of the inner disk with non-negligible inner disk flux, while the K band source is not separated clearly from the inner disk (cite: sphere2025sub). Although there is increased background flux where H$\alpha$ source is located, it is unlikely the H$\alpha$ is a false positive from scattered light from the inner disk, as we were unable to recover the source at the same location in H$\alpha$ continuum, nor any scattered disk light at that location. We do acknowledge that a significant amount of the accepted orbital solutions are grazing the current inner disk, which would only be self‑consistent if the disk structures are co‑orbiting with the planet candidate. To assess whether the inner‑disk features co-orbit with the planet candidate, further observations are needed. Thus, we cannot dismiss the possibility that the H$\alpha$ source has a different origin than the K band source. However, Occam’s Razor suggests they are the same planet, since their positions are consistent with orbital motion to within $\pm$1 PSF FWHM.

## H$\alpha$ Variability and Line Flux

Following Section 6 from (cite: 2025AJ....169...35C), we estimated the H$\alpha$ line flux and mass accretion rate of the protoplanet candidate using the measured ASDI contrast. To enable easier comparison to other observed protoplanet line fluxes and accretion rates, which generally assumes no extinction (cite: 2025AJ....169...35C), we adopt values of 0 for both the common extinction to both the star and the planet (A$_{R}$) and the extra extinction toward the planet (A$_{p}$) in the line flux calculation. Using the stellar r$'$ magnitude of 12.64$\pm$0.01 (cite: 2012yCat.1322....0Z), the mean H$\alpha$ line flux on Apr 13 and Apr 16 are respectively (29.7 $\pm$7.5)$\times$10$^{-16}$ ergs/s/cm$^2$ and (8.2$\pm$3.4)$\times$10$^{-16}$ ergs/s/cm$^2$. As a point of reference, the line flux of PDS 70b measured by MagAO-X dropped from (10.4 $\pm$1.6)$\times$10$^{-16}$ ergs/s/cm$^2$ to (3.6$\pm$0.9)$\times$10$^{-16}$ ergs/s/cm$^2$ in a span of 2 years (cite: 2025AJ....169...35C). Although forward modeling accounts for throughput losses and self-subtraction introduced by ASDI, uncertainties can still be introduced as the injected PSFs are assumed to be Gaussian while the stellar PSFs observed are elliptical. Thus, the large decrease in H$\alpha$ line flux over three nights may stem from the added uncertainty in retrieving flux from PSFs with greater eccentricity variations—especially in our April 16 dataset. (see Table [\[tab:table\]](#tab:table) for the range of eccentricity values between the 2 nights and [1](#tab:bin) for detail breakdown for the Apr 16 dataset). However, accretion line (HI Paschen $\beta$) flux variability of $<$50$\%$ has been observed at timescales below their rotation period for wide orbit substellar companions in young associations (cite: 2023A&A...676A.123D). An alternative explanation to the decrease in H$\alpha$ line flux may be because we are observing a side of the companion emitting less in H$\alpha$ on the second epoch.

We considered the impact of increased H$\alpha$ line fluxes by adopting an extinction range of 0–3 magnitudes, which was used to define the upper and lower bounds of the inferred mass accretion rates ($\dot M$), following a similar approach to that used in (cite: 2021AJ....161..244Z). Using the same 5Myr DUSTY model as (cite: sphere2025sub), the 4$M_\text{Jup}$ planet would have radius = 1.5$R_\text{Jup}$(cite: 2000ApJ...542..464C). The $\dot M$ of this planet would be (3.4$^{+5.6}_{-0.3})\times10^{-12}$ $M_{\odot}$/yr and (2.2$^{+3.6}_{-0.4})\times10^{-12}$ $M_{\odot}$/yr for Apr 13 and 16 respectively. The H$\alpha$ line flux and $\dot M$ of 2MJ1612 b are similar to that of PDS 70 protoplanets (cite: 2025AJ....169...35C). Their low accretion rate ($\dot M$ $\sim$10$^{-2}$-10$^{-3}$ M$_{Jup}$/Myr) may be attributed to the system’s older age of 5-10 Myr, as they are all members of the Sco-Cen complex. At this accretion rate, these protoplanets can only gain a few percent more of their total mass before total gas dissipation.

## Can a Single Massive Jupiter Explain the Disk gap?

Our observations suggest the presence of a substellar companion with H$\alpha$ excess at deprojected separation of 23.45$\pm$0.29 au around 2MJ1612, assuming the it is co-planar with the disk. As discussed in section [3.1](#subsec:orbit), if both the K band and H$\alpha$ emission originates from the same source, the companion would be roughly 4$M_\text{Jup}$ and can potentially clear a gap of 4-10 times its Hill radius of 2.8$\pm$0.7 au around a 0.7M$_{\odot}$ star (cite: 2011ApJ...738..131D; 2012A&A...545A..81P). Although this is consistent with the mass range of 0.1-5$M_\text{Jup}$ estimated from matching radiative transfer models in hydrodynamic simulations to the observed NIR features (cite: sphere2025sub), we cannot directly comparable it to our observations, as the modeled planet was injected at a much wider separation, from which it later migrated inward. It is still unclear if just one planet can clear this large gap of $\sim$0.4" (53 au) and additional disk processes (cite: 2023ASPC..534..423B) can contribute to create the outer gap, which cannot be ruled out with our observations.

However, the presence of an additional, as yet unseen, outer companion within the gap, similar to that of the PDS 70 system, may aid the formation of the observed large gap. The massive accreting gap (MAG) planet model of (cite: 2020AJ....160..221C) predicts the semi-major axes of three co-planar quasi-circular planets in a 1:2:4 MMR (at a$_1$, a$_2$, and a$_3$) within transitional disks with dust-free cavities based on the observed ALMA gap radius, R$_{cav}$. The model assumes planet masses decrease with increasing orbital radius, implying that the outer planets at a$_2$ and a$_3$ are fainter. Although an inner disk excludes a planet at a$_1$, the model still predicts planets at a$_2$=0.475$\times$R$_\text{cav}$ and a$_3$=0.753$\times$R$_\text{cav}$. For the 2MJ1612 system, this corresponds to a 1.4M$_\text{jup}$ at a$_2$= 25 au and a 0.7M$_\text{jup}$ planet at a$_3$= 40 au. The estimated a$_2$ of 25 au is broadly consistent with derived observational values (23.45$\pm$0.29 au), suggesting a possible additional lower-mass companion at larger separation contributing to gap maintenance. Assuming a 2:1 MMR, the location of the hypothetical outer companion can be inferred from the measured separation of a$_2$ = 23.45$\pm$0.29 au, yielding a$_3$= 36.5 au ($\sim$0.28"). This inferred location of an outer planet is consistent with the separation of 0.2-0.5" constrained by (cite: sphere2025sub) using the ratio of gap size measured in ALMA and SPHERE observations, although their model only contains a single planet with constrained mass estimated to be of 1-2 M$_\text{Jup}$.

## Search for Outer Companions

The search for other external companions located near the ALMA 3$\sigma$ compact emission and kinematic kink in both epochs of our observations yielded null detections. The CPD candidate signal, seen in the dust gap by (cite: 2024ApJ...974..102S), could not be recovered in the H$\alpha$ continuum, H and K bands(cite: sphere2025sub), as well as sub-mm images with higher resolution (0.02-0.08" at 1.33mm; see Appendix [5](#sec:alma_frank)) and sensitivity. The non-detection in our ALMA maps may be due to the emission being resolved out with a smaller beam. Associated with the velocity kink, the planet candidate outside the disk has an estimated upper mass limit of 0.8 $M_{Jup}$ from circumplanetary disk Keplerian rotation (cite: 2024ApJ...974..102S). This is a very low mass planet to be directly detected. An accreting object with sub-Jupiter mass is unlikely to generate high enough hydrogen gas shock strength to be easily detectable. Assuming the best case scenario of dust free opacities, a $<$1M$_{Jup}$ would be challenging to detect (cite: 2020ApJ...902..126S), with H$\alpha$ contrast of $\sim$10$^{-4}$ (cite: 2025AJ....169...35C), thus a sub-Jupiter mass object would certainly below the detection limit of MagAO-X in this system where the guide star is so faint. For this reason, we cannot definitively say, one way or the other, if the velocity kink observed by (cite: 2024ApJ...974..102S) is due to a low mass ($<$1M$_{Jup}$) protoplanet. But the scenario of accreting protoplanets with masses above 2M$_{Jup}$ is unlikely as we should have detected them.

# Conclusions

On 2025 April 13 and 16, we observed 2MJ1612 with MagAO-X in the H$\alpha$ SDI mode on the 6.5 m Magellan Clay telescope at Las Campanas Observatory, Chile. With SNR $\gtrsim$5, we detected an H$\alpha$ excess source across 2 epochs of observations in the ASDI images, at an average sep = 141.96$\pm$2.10 mas and PA= 159.00$\pm$0.55$^\circ$.

SPHERE/IRDIS RDI observations in K band revealed a source that lies in close proximity to the H$\alpha$ excess. The observed positional offset is consistent with orbital motion over a two-year baseline, thus we interpreted the H$\alpha$ excess and K band light to be originating from an accreting companion, 2MJ1612 b (or MaxProtoPlanetS 1b), at $\sim$0.14" from the central star. The non-detection of H$\alpha$ continuum suggest 2MJ1612 b is likely substellar, and the K band photometry further constrains the companion mass to be $\sim$4$M_\text{Jup}$. Although it is unlikely this single companion is solely responsible for carving the gap in its protoplanetary disk, we were unable to recover signs of additional outer companions in our data. The $\lesssim$0.8M$_{Jup}$ planet candidate at 0.875" associated with a kinematic kink in the $^{12}$CO channel(cite: 2024ApJ...974..102S) is likely below the MagAO-X detection limit due to its low mass.

2M1612 b may become the third *bona fide* H$\alpha$ accreting protoplanet discovered to date. Further investigation is required to confirm the detection of our protoplanet candidate and search for additional companions that might also be contributing to carving out the gap. Follow-up observations using MagAO-X at H$\alpha$ and SPHERE/IRDIS in the JHK bands can help validate the detection and place tighter constraints on the mass of the candidate. Additionally, integral field spectroscopy with MUSE on the VLT and imaging with NIRCAM through the NIR wavelengths with JWST can serve as alternative or complementary approaches, offering both confirmation and further characterization of the system in visible/NIR wavelengths.

We are grateful for support from the NSF MRI award No. 1625441 for MagAO-X development and the Heising-Simons Foundation that made the MagAO-X Phase II upgrade program possible. J.L., J.K. , E.A.M., and M.Y.K. are supported by NSF Graduate Research Fellowship. L.M.C. and the MaxProtoPlanetS survey was partially supported by NASA eXoplanet Research Program (XRP) grant 80NSSC18K0441 and is now supported by 80NSSC21K0397 which currently funds the MaxProtoPlanetS survey. Support for F.L. was provided by NASA through the NASA Hubble Fellowship grant #HST-HF2-51512.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. L.M. acknowledges funding by the European Union through the E-BEANS ERC project (grant number 100117693). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them. S.M. was supported by a Royal Society University Research Fellowship (URF- R1-221669). L.M.P. acknowledges support from ANID BASAL project FB210003 and ANID FONDECYT Regular $\#$1221442.

# Facilities

Magellan:Clay (MagAO-X), ALMA

# Software

astropy (cite: 2018AJ....156..123A), scikit-image (cite: 2014PeerJ...2..453V), pyKLIP (cite: 2015ascl.soft06001W), OpenCV (cite: opencv_library), orbitize! (cite: 2020AJ....159...89B)

# ALMA Band 6 Continuum Observations

ALMA Band 6 data for 2MJ1612 were taken as part of program 2022.1.00646.S (PI: Feng Long), including two executions with short-baseline configurations on April 25 2023 and July 21 2024, and one long-baseline execution on July 06 2023. The two short-baseline executions made use of antenna baselines from 15 m to $\sim$2.5 km, each with $\sim$9 min on-source time, and the long-baseline data spanned baselines from 113 m to 9.7 km, with $\sim$40 min on-source integration. Spectral window setups were identical in each execution, including three continuum basebands centered at 219, 221, and 232 GHz, each with a bandwidth of 1.875 GHz, and a fourth baseband for $^{12}$CO emission. Continuum images were created using the line-free channels.

Data reduction started with the standard ALMA pipelines, and the subsequent self-calibration and imaging were performed with CASA 6.5 (cite: CASATeam2022PASP). Before combining data taken at different epochs, we first determined the disk emission center for large cavity disks following the approach described in (cite: Long2022) and shifted all datasets to a common phase center. Two rounds of phase-only self-calibration for the two short-baseline datasets led to a $\sim$10% improvement in the image peak signal-to-noise ratio, while the improvement was minimal when including the long-baseline dataset for self-calibration. To further improve the image quality, we downloaded and calibrated (including self-calibration) the seven executions at Band 6 used in (cite: 2024ApJ...974..102S), which were shifted to the common phase center and flux rescaled. The final continuum image at 1.3 mm was created by concatenating all these datasets using `robust=0.5` in the Briggs weighting scheme, which results in a beam of $85\times67$ mas (PA=$-71\ensuremath{^\circ}$) with 1$\sigma$ noise of 9.6 $\mu$Jy beam$^{-1}$. Compared to (cite: 2024ApJ...974..102S), our final image has a factor of 2 better angular resolution and sensitivity.

To better describe the dust emission morphology and identify any point-source residuals, we adopted the `frank` software (cite: Jennings2020) that assumes an azimuthally symmetric disk model and fits the real component of the ALMA visibilities. The `frank` parameters are set as $\alpha=1.4$ and $\omega_{smooth}=0.01$, which are conservative choices to capture the main emission features. We fixed the disk inclination of 37$\ensuremath{^\circ}$ and position angle of 45$\ensuremath{^\circ}$ (cite: 2024ApJ...974..102S), and adopted the outer ring center as the phase center offsets. Figure [3](#fig:frank) shows the `frank` model results, with model and residual images created with the same `tclean` parameters as the data image. Besides the primary ring at 0.57$''$, an additional faint ring also emerges at around 0.16$''$. The 3$\sigma$ compact source at $\sim$0.2$''$, reported by (cite: 2024ApJ...974..102S) is not recovered in our deeper data.

![](fig_J1612_frank_ringcenter_profile.pdf)

# MagAO-X 2025 Apr 16 Frame Combination

After initial selection and cross correlation, the individual raw frames of the 2025 Apr 16 data are combined through both time and PARANG. As each dataset is unique, the procedure outlined in the following paragraph has not been systematically optimized; instead, parameter choices were made through iterative refinement. We loosely adhered to three guiding principles: (1) Each pyKLIP reduction should use 50 to 100 combined frames, as this range has empirically provided a good compromise between PSF subtraction performance and processing time in previous reductions; (2) The PSF quality across combined frames should be comparable, which can be achieved by combining a similar number of individual frames, as this ensures each KLIP frame can reach threshold SNR; and (3) The combined frames should strike a balance between maximizing angular diversity and ensuring a sufficient number of reference frames for effective subtraction.

As previously discussed in Section [2.1](#subsec:magao-x), we have a total of 170$^\circ$ of rotation in this dataset and due to its declination, majority of data is collected around PARANG$\approx$ +75$^\circ$ or -75$^\circ$. We first divided the selected raw frames into 57 bins, each containing frames within $\Delta$PARANG$=$3.01$^\circ$, as a bin of this size ensures each bin around transit has about 10 frames. We adopted a threshold of 50 raw frames—roughly the mean bin size—to decide between our two binning strategies. Bins containing more than 50 frames are grouped by time; those with 50 frames or fewer are grouped by PARANG. Within those 57 bins, there are 5 bins that do not contain any frames as the AO loop was open.

To adhere to principle of (2) and (3), we further downsample large bins (contains $\geq$90 raw frames) by time to create more than one combined frame within that bin, as well as merge small bins (contains $<$10 raw frames) into one. All remaining bins are processed by combining their raw frames into a single combined frame. Table [1](#tab:bin) summarizes the end PARANG, the number of raw frames, the binning method applied, the number of frames used in each downsampled set, resulting number of combined frames per bin, and the median eccentricity of the PSF(s) in each PARANG bin. This procedure yielded a total of 81 combined frames for use in the subsequent steps of the data reduction process with pyKLIP.

| PARANG($^\circ$) | \# of individual frames | binning method | Downsample | \# of Combined Frames | Median PSF Eccentricities |
|:--:|:--:|:--:|:--:|:--:|:--:|
| -80.79 | 453 | time | 90 | 5 | 0.34 |
| -77.78 | 384 | time | 90 | 4 | 0.35 |
| -74.76 | 283 | time | 67 | 4 | 0.31 |
| -71.75 | 200 | time | 45 | 4 | 0.27 |
| -68.74 | 149 | time | 45 | 3 | 0.30 |
| -65.72 | 117 | time | 45 | 2 | 0.32 |
| -62.71 | 91 | time | 45 | 2 | 0.38 |
| -59.70 | 57 | time | 57 | 1 | 0.39 |
| -56.68 | 51 | time | 51 | 1 | 0.39 |
| -53.67 | 40 | PARANG | 40 | 1 | 0.47 |
| -50.66 | 43 | PARANG | 43 | 1 | 0.46 |
| -47.64 | 28 | PARANG | 28 | 1 | 0.47 |
| -44.63 | 37 | PARANG | 37 | 1 | 0.46 |
| -41.62 | 32 | PARANG | 32 | 1 | 0.51 |
| -38.60 | 31 | PARANG | 31 | 1 | 0.43 |
| -35.59 | 29 | PARANG | 29 | 1 | 0.46 |
| -32.58 | 27 | PARANG | 27 | 1 | 0.45 |
| -29.56 | 24 | PARANG | 24 | 1 | 0.45 |
| -26.55 | 23 | PARANG | 23 | 1 | 0.48 |
| -23.54 | 22 | PARANG | 22 | 1 | 0.48 |
| -20.52 | 20 | PARANG | 20 | 1 | 0.54 |
| -17.51 | 20 | PARANG | 20 | 1 | 0.49 |
| -14.50 | 14 | PARANG | 14 | 1 | 0.46 |
| -11.49 | 16 | PARANG | 16 | 1 | 0.50 |
| -8.47 | 18 | PARANG | 18 | 1 | 0.48 |
| -2.45 | 17 | PARANG | 17 | 1 | 0.44 |
| 0.57 | 18 | PARANG | 18 | 1 | 0.53 |
| 3.58 | 18 | PARANG | 18 | 1 | 0.56 |
| 6.59 | 18 | PARANG | 18 | 1 | 0.52 |
| 9.61 | 18 | PARANG | 18 | 1 | 0.49 |
| 12.62 | 15 | PARANG | 15 | 1 | 0.55 |
| 15.63 | 18 | PARANG | 18 | 1 | 0.55 |
| 18.65 | 18 | PARANG | 18 | 1 | 0.50 |
| 21.66 | 19 | PARANG | 19 | 1 | 0.58 |
| 24.67 | 19 | PARANG | 19 | 1 | 0.52 |
| 30.70 | 10 | PARANG | 10 | 1 | 0.38 |
| 33.71 | 16 | PARANG | 16 | 1 | 0.39 |
| 51.79 | 19 | PARANG | 19 | 1 | 0.47 |
| 54.81 | 21 | PARANG | 21 | 1 | 0.34 |
| 57.82 | 14 | PARANG | 14 | 1 | 0.33 |
| 60.83 | 30 | PARANG | 30 | 1 | 0.33 |
| 63.85 | 35 | PARANG | 35 | 1 | 0.30 |
| 66.86 | 35 | PARANG | 35 | 1 | 0.30 |
| 72.89 | 63 | PARANG | 63 | 1 | 0.29 |
| 75.90 | 159 | time | 45 | 3 | 0.28 |
| 78.91 | 159 | time | 45 | 3 | 0.31 |
| 81.93 | 271 | time | 67 | 4 | 0.28 |
| 84.94 | 444 | time | 90 | 4 | 0.26 |
| 87.95 | 623 | time | 90 | 6 | 0.22 |

: Details of frame combination using the hybrid binning method for the 2025 Apr 16 data: ending PARANG, the number of individual frames, binning method, the number of raw frames used for downsampling, the number of combined frames of each bin, and the median eccentricity of the combined frame PSF in PARANG bin. The downsample number is also the total integration time included in each combined frames in seconds.

# MagAO-X 2024 March 25 SDI Observations

We also observed 2MJ1612 on 2024 March 25 in the same H$\alpha$ SDI mode as the 25A observations with MagAO-X. This dataset was taken in 0.5"-0.8" seeing and contained 65 mins of 1s exposure frames taken well after transit, resulting in just $\sim$36$^\circ$ of PARANG rotation, compared to $\sim$170$^\circ$ in 2025 April 13 and 16. We recovered a positive H$\alpha$ source in this dataset that overlaps with the SPHERE/IRDIS H band data taken in Apr 2023. Interestingly, the fainter tail of this H$\alpha$ source also overlaps with the 2025 Apr 16 SDI source located separation = 141.96 mas and PA= 159.00$^{\circ}$. Therefore, the 2024 H$\alpha$ source can be interpreted as a combination of H$\alpha$ accretion from the protoplanet candidate, scattered stellar H$\alpha$ light by the inner disk, and residual stellar light.

Unfortunately, the H$\alpha$ point source detection on 2024 March 25 is co-located with the readout stripe, a stripe created by charge transfer from the bright central star to the readout region on our frame transfer EMCCD. The stripe remains in the same position on the EMCCD throughout the observations. If there is sufficient PARANG rotation in the dataset, via de-rotation in the normal ADI post-processing, its contribution will be rotationally smeared by $\Delta\text{PARANG}\sim$170 degrees and distributed evenly through the image, minimizing its effect. This is the case for the MagAO-X data taken in 2025. However, due to the lack of PARANG rotation $\Delta\text{PARANG}\sim$ 36$^{\circ}$ in the 2024 Mar 25 data, the stripe partially persists through post-processing, resulting in bright blobs in the vicinity of the position angle (PA) of the H$\alpha$ source. Although complete removal of the stripe cannot be performed, we did attempt to eliminate the stripe and its artifacts in the immediate region around the source. We observed a shift ($\sim$1-2 pixels) in the center of light and flux of the companion following readout stripe removal, indicating increased measurement uncertainties in this dataset and complicating the interpretation of the H$\alpha$ source, which motivated the need for additional observations. Therefore, we chose to include only the 25A measurements in our analysis.

![image](corner_plot.png)

natexlab

(ref: 2023AJ....165...57A) Adams Redai, J. I., Follette, K. B., Wang, J., et al. 2023, AJ, 165, 57, doi: [`10.3847/1538-3881/aca60d`](http://doi.org/10.3847/1538-3881/aca60d)

(ref: 2020ARA&A..58..483A) Andrews, S. M. 2020, ARA&A, 58, 483, doi: [`10.1146/annurev-astro-031220-010302`](http://doi.org/10.1146/annurev-astro-031220-010302)

(ref: 2018ApJ...869L..41A) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2023ASPC..534..423B) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423, doi: [`10.48550/arXiv.2210.13314`](http://doi.org/10.48550/arXiv.2210.13314)

(ref: 2019ApJ...884L..41B) Bae, J., Zhu, Z., Baruteau, C., et al. 2019, ApJL, 884, L41, doi: [`10.3847/2041-8213/ab46b0`](http://doi.org/10.3847/2041-8213/ab46b0)

(ref: 2021AJ....161..147B) Bailer-Jones, C. A. L., Rybizki, J., Fouesneau, M., Demleitner, M., & Andrae, R. 2021, AJ, 161, 147, doi: [`10.3847/1538-3881/abd806`](http://doi.org/10.3847/1538-3881/abd806)

(ref: 2022AJ....164...29B) Balmer, W. O., Follette, K. B., Close, L. M., et al. 2022, AJ, 164, 29, doi: [`10.3847/1538-3881/ac73f4`](http://doi.org/10.3847/1538-3881/ac73f4)

(ref: 2017AJ....153..229B) Blunt, S., Nielsen, E. L., De Rosa, R. J., et al. 2017, AJ, 153, 229, doi: [`10.3847/1538-3881/aa6930`](http://doi.org/10.3847/1538-3881/aa6930)

(ref: 2020AJ....159...89B) Blunt, S., Wang, J. J., Angelo, I., et al. 2020, AJ, 159, 89, doi: [`10.3847/1538-3881/ab6663`](http://doi.org/10.3847/1538-3881/ab6663)

(ref: opencv_library) Bradski, G. 2000, Dr. Dobb’s Journal of Software Tools

(ref: 2020A&A...638A..98C) Cantalloube, F., Farley, O. J. D., Milli, J., et al. 2020, A&A, 638, A98, doi: [`10.1051/0004-6361/201937397`](http://doi.org/10.1051/0004-6361/201937397)

(ref: 2025ApJ...978..117C) Carpenter, J. M., Esplin, T. L., Luhman, K. L., Mamajek, E. E., & Andrews, S. M. 2025, ApJ, 978, 117, doi: [`10.3847/1538-4357/ad8ebc`](http://doi.org/10.3847/1538-4357/ad8ebc)

(ref: CASATeam2022PASP) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2000ApJ...542..464C) Chabrier, G., Baraffe, I., Allard, F., & Hauschildt, P. 2000, ApJ, 542, 464, doi: [`10.1086/309513`](http://doi.org/10.1086/309513)

(ref: 2020AJ....160..221C) Close, L. M. 2020, AJ, 160, 221, doi: [`10.3847/1538-3881/abb375`](http://doi.org/10.3847/1538-3881/abb375)

(ref: 2014ApJ...781L..30C) Close, L. M., Follette, K. B., Males, J. R., et al. 2014, ApJL, 781, L30, doi: [`10.1088/2041-8205/781/2/L30`](http://doi.org/10.1088/2041-8205/781/2/L30)

(ref: 2025AJ....169...35C) Close, L. M., Males, J. R., Li, J., et al. 2025, AJ, 169, 35, doi: [`10.3847/1538-3881/ad8648`](http://doi.org/10.3847/1538-3881/ad8648)

(ref: 2023A&A...676A.123D) Demars, D., Bonnefoy, M., Dougados, C., et al. 2023, A&A, 676, A123, doi: [`10.1051/0004-6361/202346221`](http://doi.org/10.1051/0004-6361/202346221)

(ref: 2011ApJ...738..131D) Dodson-Robinson, S. E., & Salyk, C. 2011, ApJ, 738, 131, doi: [`10.1088/0004-637X/738/2/131`](http://doi.org/10.1088/0004-637X/738/2/131)

(ref: 2008SPIE.7014E..3LD) Dohlen, K., Langlois, M., Saisse, M., et al. 2008, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7014, Ground-based and Airborne Instrumentation for Astronomy II, ed. I. S. McLean & M. M. Casali, 70143L, doi: [`10.1117/12.789786`](http://doi.org/10.1117/12.789786)

(ref: 2016ApJ...826...75D) Dong, R., Fung, J., & Chiang, E. 2016a, ApJ, 826, 75, doi: [`10.3847/0004-637X/826/1/75`](http://doi.org/10.3847/0004-637X/826/1/75)

(ref: 2016ApJ...816L..12D) Dong, R., Zhu, Z., Fung, J., et al. 2016b, ApJL, 816, L12, doi: [`10.3847/2041-8205/816/1/L12`](http://doi.org/10.3847/2041-8205/816/1/L12)

(ref: 2021AJ....161..241F) Ferrer-Chávez, R., Wang, J. J., & Blunt, S. 2021, AJ, 161, 241, doi: [`10.3847/1538-3881/abf0a8`](http://doi.org/10.3847/1538-3881/abf0a8)

(ref: 2017AJ....153..264F) Follette, K. B., Rameau, J., Dong, R., et al. 2017, AJ, 153, 264, doi: [`10.3847/1538-3881/aa6d85`](http://doi.org/10.3847/1538-3881/aa6d85)

(ref: 2023AJ....165..225F) Follette, K. B., Close, L. M., Males, J. R., et al. 2023, AJ, 165, 225, doi: [`10.3847/1538-3881/acc183`](http://doi.org/10.3847/1538-3881/acc183)

(ref: 2023A&A...674A...1G) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: sphere2025sub) Ginski, C., Pinilla, P., Benisty, M., et al. 2025, Astronomy & Astrophysics

(ref: 2024A&A...685A..52G) Ginski, C., Garufi, A., Benisty, M., et al. 2024, A&A, 685, A52, doi: [`10.1051/0004-6361/202244005`](http://doi.org/10.1051/0004-6361/202244005)

(ref: 2019NatAs...3..749H) Haffert, S. Y., Bohn, A. J., de Boer, J., et al. 2019, Nature Astronomy, 3, 749, doi: [`10.1038/s41550-019-0780-5`](http://doi.org/10.1038/s41550-019-0780-5)

(ref: 2023MNRAS.522L..51H) Hammond, I., Christiaens, V., Price, D. J., et al. 2023, MNRAS, 522, L51, doi: [`10.1093/mnrasl/slad027`](http://doi.org/10.1093/mnrasl/slad027)

(ref: 2023ASPC..534.....I) Inutsuka, S., Aikawa, Y., Muto, T., Tomida, K., & Tamura, M., eds. 2023, Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII

(ref: Jennings2020) Jennings, J., Booth, R. A., Tazzari, M., Rosotti, G. P., & Clarke, C. J. 2020, MNRAS, 495, 3209, doi: [`10.1093/mnras/staa1365`](http://doi.org/10.1093/mnras/staa1365)

(ref: 2006A&A...447..369K) Kley, W., & Dirksen, G. 2006, A&A, 447, 369, doi: [`10.1051/0004-6361:20053914`](http://doi.org/10.1051/0004-6361:20053914)

(ref: 2024SPIE13097E..14L) Li, J., Close, L. M., Males, J. R., et al. 2024, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 13097, Adaptive Optics Systems IX, ed. K. J. Jackson, D. Schmidt, & E. Vernet, 1309714, doi: [`10.1117/12.3020333`](http://doi.org/10.1117/12.3020333)

(ref: 2018ApJ...869...17L) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17, doi: [`10.3847/1538-4357/aae8e1`](http://doi.org/10.3847/1538-4357/aae8e1)

(ref: Long2022) Long, F., Andrews, S. M., Zhang, S., et al. 2022, ApJL, 937, L1, doi: [`10.3847/2041-8213/ac8b10`](http://doi.org/10.3847/2041-8213/ac8b10)

(ref: 2025AJ....169...36L) Long, J. D., Pearce, L., Haffert, S. Y., et al. 2025, AJ, 169, 36, doi: [`10.3847/1538-3881/ad924f`](http://doi.org/10.3847/1538-3881/ad924f)

(ref: 2018SPIE10703E..09M) Males, J. R., Close, L. M., Miller, K., et al. 2018, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 10703, Adaptive Optics Systems VI, ed. L. M. Close, L. Schreiber, & D. Schmidt, 1070309, doi: [`10.1117/12.2312992`](http://doi.org/10.1117/12.2312992)

(ref: 2024SPIE13097E..09M) Males, J. R., Close, L. M., Haffert, S. Y., et al. 2024, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 13097, Adaptive Optics Systems IX, ed. K. J. Jackson, D. Schmidt, & E. Vernet, 1309709, doi: [`10.1117/12.3019464`](http://doi.org/10.1117/12.3019464)

(ref: 2000PASP..112...91M) Marois, C., Doyon, R., Racine, R., & Nadeau, D. 2000, PASP, 112, 91, doi: [`10.1086/316492`](http://doi.org/10.1086/316492)

(ref: 2006ApJ...641..556M) Marois, C., Lafrenière, D., Doyon, R., Macintosh, B., & Nadeau, D. 2006a, ApJ, 641, 556, doi: [`10.1086/500401`](http://doi.org/10.1086/500401)

(ref: 2006SPIE.6269E..3MM) Marois, C., Phillion, D. W., & Macintosh, B. 2006b, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 6269, Ground-based and Airborne Instrumentation for Astronomy, ed. I. S. McLean & M. Iye, 62693M, doi: [`10.1117/12.672263`](http://doi.org/10.1117/12.672263)

(ref: 2014ApJ...792...97M) Mawet, D., Milli, J., Wahhaj, Z., et al. 2014, ApJ, 792, 97, doi: [`10.1088/0004-637X/792/2/97`](http://doi.org/10.1088/0004-637X/792/2/97)

(ref: 2012A&A...545A..81P) Pinilla, P., Benisty, M., & Birnstiel, T. 2012, A&A, 545, A81, doi: [`10.1051/0004-6361/201219315`](http://doi.org/10.1051/0004-6361/201219315)

(ref: 2018ApJ...860L..13P) Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJL, 860, L13, doi: [`10.3847/2041-8213/aac6dc`](http://doi.org/10.3847/2041-8213/aac6dc)

(ref: 2018MNRAS.477.1270P) Price, D. J., Cuello, N., Pinte, C., et al. 2018, MNRAS, 477, 1270, doi: [`10.1093/mnras/sty647`](http://doi.org/10.1093/mnras/sty647)

(ref: 2016ApJ...824..117P) Pueyo, L. 2016, ApJ, 824, 117, doi: [`10.3847/0004-637X/824/2/117`](http://doi.org/10.3847/0004-637X/824/2/117)

(ref: 1999PASP..111..587R) Racine, R., Walker, G. A. H., Nadeau, D., Doyon, R., & Marois, C. 1999, PASP, 111, 587, doi: [`10.1086/316367`](http://doi.org/10.1086/316367)

(ref: 2017AJ....153..244R) Rameau, J., Follette, K. B., Pueyo, L., et al. 2017, AJ, 153, 244, doi: [`10.3847/1538-3881/aa6cae`](http://doi.org/10.3847/1538-3881/aa6cae)

(ref: 2024ApJ...974..102S) Sierra, A., Pérez, L. M., Agurto-Gangas, C., et al. 2024, ApJ, 974, 102, doi: [`10.3847/1538-4357/ad6e73`](http://doi.org/10.3847/1538-4357/ad6e73)

(ref: 2012ApJ...755L..28S) Soummer, R., Pueyo, L., & Larkin, J. 2012, ApJL, 755, L28, doi: [`10.1088/2041-8205/755/2/L28`](http://doi.org/10.1088/2041-8205/755/2/L28)

(ref: 2020ApJ...902..126S) Szulágyi, J., & Ercolano, B. 2020, ApJ, 902, 126, doi: [`10.3847/1538-4357/abb5a2`](http://doi.org/10.3847/1538-4357/abb5a2)

(ref: 2022ApJ...925...95T) Tanaka, Y. A., Kanagawa, K. D., Tanaka, H., & Tanigawa, T. 2022, ApJ, 925, 95, doi: [`10.3847/1538-4357/ac3af5`](http://doi.org/10.3847/1538-4357/ac3af5)

(ref: 2020MNRAS.499.2015T) Toci, C., Lodato, G., Christiaens, V., et al. 2020, MNRAS, 499, 2015, doi: [`10.1093/mnras/staa2933`](http://doi.org/10.1093/mnras/staa2933)

(ref: 2014PeerJ...2..453V) van der Walt, S., Schönberger, J. L., Nunez-Iglesias, J., et al. 2014, PeerJ, 2, e453, doi: [`10.7717/peerj.453`](http://doi.org/10.7717/peerj.453)

(ref: 2018ApJ...863L...8W) Wagner, K., Follete, K. B., Close, L. M., et al. 2018, ApJL, 863, L8, doi: [`10.3847/2041-8213/aad695`](http://doi.org/10.3847/2041-8213/aad695)

(ref: 2015ascl.soft06001W) Wang, J. J., Ruffio, J.-B., De Rosa, R. J., et al. 2015, , Astrophysics Source Code Library, record ascl:1506.001

(ref: 2016AJ....152...97W) Wang, J. J., Graham, J. R., Pueyo, L., et al. 2016, AJ, 152, 97, doi: [`10.3847/0004-6256/152/4/97`](http://doi.org/10.3847/0004-6256/152/4/97)

(ref: 2021AJ....161..148W) Wang, J. J., Vigan, A., Lacour, S., et al. 2021, AJ, 161, 148, doi: [`10.3847/1538-3881/abdb2d`](http://doi.org/10.3847/1538-3881/abdb2d)

(ref: 2012yCat.1322....0Z) Zacharias, N., Finch, C. T., Girard, T. M., et al. 2012, , VizieR On-line Data Catalog: I/322A. Originally published in: 2013AJ....145...44Z

(ref: 2018ApJ...869L..47Z) Zhang, S., Zhu, Z., Huang, J., et al. 2018, ApJL, 869, L47, doi: [`10.3847/2041-8213/aaf744`](http://doi.org/10.3847/2041-8213/aaf744)

(ref: 2021AJ....161..244Z) Zhou, Y., Bowler, B. P., Wagner, K. R., et al. 2021, AJ, 161, 244, doi: [`10.3847/1538-3881/abeb7a`](http://doi.org/10.3847/1538-3881/abeb7a)

(ref: 2023AJ....166..220Z) Zhou, Y., Bowler, B. P., Yang, H., et al. 2023, AJ, 166, 220, doi: [`10.3847/1538-3881/acf9ec`](http://doi.org/10.3847/1538-3881/acf9ec)

[^1]: The reduced MagAO-X data are available upon request. Please reach out to the corresponding author for access.

</paper>

Write the methods card for this paper.