# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...968...87K\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...968...87K",
 "title": "Impacts of Bar-driven Shear and Shocks on Star Formation",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Kim, Taehyun",
 "n_authors": 15,
 "arxiv_id": "2405.00107",
 "doi": "10.3847/1538-4357/ad410e",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00484.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00129.S"
 ]
}
```

Paper text:
<paper>
# Impacts of bar-driven shear and shocks on star formation

## Abstract

Bars drive gas inflow. As the gas flows inwards, shocks and shear occur along the bar dust lanes. Such shocks and shear can affect the star formation and change the gas properties. For four barred galaxies, we present H$\alpha$ velocity gradient maps that highlight bar-driven shocks and shear using data from the PHANGS-MUSE and PHANGS-ALMA surveys which allow us to study bar kinematics in unprecedented detail. Velocity gradients are enhanced along the bar dust lanes, where shocks and shear are shown to occur in numerical simulations. Velocity gradient maps also efficiently pick up expanding shells around HII regions. We put pseudo slits on the regions where velocity gradients are enhanced and find that H$\alpha$ and CO velocities jump up to $\sim$ 170 km$\,\rm s^{-1}$, even after removing the effects of circular motions due to the galaxy rotation. Enhanced velocity gradients either coincide with the peak of CO intensity along the bar dust lanes or are slightly offset from CO intensity peaks, depending on the objects. Using the BPT diagnostic, we identify the source of ionization on each spaxel and find that star formation is inhibited in the high velocity gradient regions of the bar, and the majority of those regions are classified as LINER or composite. This implies that star formation is inhibited where bar-driven shear and shocks are strong. Our results are consistent with the results from the numerical simulations that show star formation is inhibited in the bar where shear force is strong.

# Introduction

Numerical simulations and observations find that once a galactic disk is massive enough and dynamically cold, it is often easy to form bars (e.g., (cite: hohl_71; ostriker_73; combes_81; athanassoula_02a; kraljic_12; sheth_12; seo_19; fragkoudi_20)). Bars are frequently found in nearby galaxies, and the fraction of barred galaxies exceeds 65% including weak bars (e.g., (cite: devaucouleurs_63; eskridge_00; menendez_delmestre_07; barazza_08; aguerri_09; masters_11; buta_15; diaz-garcia_16; lee_19)). Bars are non-axisymmetric structures inducing tangential forces and gravitational torques on the gas. As the gas around the bar within the corotation radius loses angular momentum, it flows inward. Piled-up gas in the central region ignites active star formation (SF, (cite: hawarden_86; knapen_95; sheth_05)) to form nuclear disks which lead to the formation of inner bars in the nuclear disks and nuclear rings in some galaxies (e.g., (cite: sormani_18b; seo_19; delorenzo_caceres_19b; gadotti_20; bittner_21; desafreitas_23a; desafreitas_23b)). The gas transported to the central 100 pc may feed active galactic nuclei (e.g., (cite: storchi-bergmann_19; silva_lima_22; garland_23; kolcu_23)), although the connection between bars and AGN is still controversial (e.g., (cite: ho_97; knapen_00; laine_02; cisternas_13; cheung_15; neumann_19; zee_23)). Moreover, bars also enrich the diversity of the outer part of galaxies. Bars are frequently accompanied by an inner and outer ring and also induce spiral arms (e.g., (cite: salo_10; comeron_14; buta_15)).

In addition to structure and morphology, there are significant differences in the observed kinematics between barred and unbarred disk galaxies. Unbarred disk galaxies show iso-velocity maps that can be well explained by circular motions (e.g., (cite: bosma_81)), while barred galaxies exhibit characteristic “S-shaped” bends along the bar in iso-velocity diagrams (e.g., (cite: peterson_80; fathi_05; lopez_coba_22)). Due to the non-axisymmetric structure, both gas and stellar kinematics are affected. Gas in the bar region experiences non-circular, streaming motions which is estimated to be $\sim$ 40$-$100 km$\,\rm s^{-1}$((cite: rozas_00; zurita_04)). Stars in the bar region are thought to follow x1 orbits which are elongated along the major axis of the bar, and also x2 orbits that are rounder, and elongated perpendicular to the bar (e.g., (cite: contopoulos_80b)).

![](tk23_new_fig1.pdf)

In Figure [1](#fig:schematic), we present a schematic diagram that describes the direction and magnitude of gas velocities within the bar region. Gas flows inward along the bar dust lanes which are found at locations of hydrodynamic shocks based in simulations (e.g., (cite: roberts_79; athanassoula_92b; sormani_15b; fragkoudi_17a)). If there is a nuclear ring, a part of the gas ($\sim$ 20 – 30%, (cite: regan_97a; hatchfield_21)) enters the nuclear ring while the remaining gas overshoots and sprays toward the other bar dust lane (e.g., (cite: sormani_19)). On the right panel of Figure [1](#fig:schematic), shocks and shear are described in the blue and orange boxes, respectively. When the gas particles are sprayed and encounter the other bar dust lane, the gas particles are suddenly decelerated, and both the direction and the magnitude of the gas velocities are abruptly changed (see e.g., figure 7 and 8 of (cite: kim_w_12aa)). This mechanism makes dissipative gas particles experience shocks. As gas particles flow into the dust lane, they also experience large velocity shear. The shear occurs when there are velocity gradients across the flow, here perpendicular to the dust lane. To highlight shear motions, only the gas velocity vectors that are parallel to the dust lane are drawn on the right bottom panel of Figure [1](#fig:schematic). There are velocity gradients along the orange dotted arrow, which lead to velocity shear. More details from simulated barred galaxies can be found in figure 2 of (cite: athanassoula_92b), figure 10 of (cite: downes_96), figure 9 of (cite: regan_99), figure 7(a) of (cite: kim_w_12aa), and figure 8 and 9 of (cite: sormani_18a).

Using hydrodynamic simulations, (cite: kim_w_12aa) investigate the formation and properties of various substructures of barred galaxies. They find strong velocity shear across the bar dust lane amounting to $\sim$1–3 km$\,\rm s^{-1}$pc$^{-1}$, which is $\sim$10 times larger than the shear from the Galactic rotation in the solar neighborhood.

Gas flows into the central regions of the galaxy along the bar dust lanes (e.g., (cite: athanassoula_92b; englmaier_97; kim_w_12aa; fragkoudi_16; sormani_23)), and as the bar-driven shocks and shear occur right at the dust lane, it is one of the most interesting sites to test the influence of shocks and shear on SF. In this study, we aim to examine whether SF is promoted or suppressed along the bar where strong shear and shocks are expected.

The loci of SF and star formation rate (SFR) vary among barred galaxies (e.g., (cite: verley_07; neumann_19; diaz-garcia_20; fraser-mckelvie_20a)). Detailed studies on individual galaxies found that SF in the bar region is low (e.g., (cite: tubbs_82)), although the gas column densities in the bar dust lanes are high ((cite: sheth_00)). Star formation efficiency (SFE) is found to be low in the bar region compared to other regions in the disk ((cite: Momose_10; hirota_14; muraoka_16; yajima_19; maeda_20b; pessa_22; maeda_23)).

However, studies on larger samples give different results and find that SFE in the bar region is not systematically lower compared to that in the other regions (e.g., (cite: Muraoka_19; diaz-garcia_21; querejeta_21)). (cite: diaz-garcia_21) report that SFE in strong bars is not systematically inhibited, and the SFEs are roughly constant along bars. Using PHANGS-ALMA, (cite: querejeta_21) define five environments within galaxies (center, bar, spiral arm, interarm region, and disk without strong spirals) and find that the SFR surface density in bars is comparable to that in spiral arms and higher than those in disks and interarm regions.

Spatial resolution may play a role in resolving the detailed structures in the bar region (e.g., nuclear rings). Large IFS surveys (e.g., CALIFA, (cite: sanchez_12), MaNGA, (cite: bundy_15)) typically have an average spatial resolution of $\sim$ 1–2 kpc, and therefore often cannot resolve nuclear rings, nuclear discs or other smaller structures or star-forming sites. On the other hand, recent surveys such as TIMER ((cite: gadotti_19)), PHANGS-ALMA ((cite: leroy_21a; leroy_21b)) and PHANGS-MUSE ((cite: emsellem_22)) provide more resolved datasets (with spatial resolution $\lesssim$ 100 pc). However, different results on SFR and SFE do not seem to be particularly affected by different resolutions. The main difference may arise from the definition of the bar ends. Because the SF in bar ends is often high and efficient for some galaxies (e.g., (cite: martin_97; hirota_14; renaud_15; beuther_17; yajima_19)), including the bar ends (e.g., (cite: querejeta_21)) or excluding the bar ends (e.g., (cite: maeda_23)) in analyzing SFE in bar regions would yield different results. The differences may also stem from various samples of different bar evolutionary phases (e.g., (cite: verley_07; fraser-mckelvie_20a)).

Several mechanisms have been introduced to explain the suppression of SF in the bar region. First, bar-driven high shear prevents SF (e.g., (cite: tubbs_82; athanassoula_92b; zurita_04; kim_w_12aa; emsellem_15; renaud_15)). Studies using simulations find that shear may suppress the growth of gravitational instability to form stars. Second, cloud-cloud collisions have been found to affect SF (e.g., (cite: stone_70a; scoville_86)). If the relative velocity of two colliding gas clouds is high, i.e., if the gas clouds enter into the dust lane with high velocity, then the SF can be suppressed (e.g., (cite: tubbs_82; reynaud_98; fujimoto_14a; maeda_21)). Third, gas within the bar extent may already have been all consumed into stars, and thus gas is depleted and the current SF is low ((cite: spinoso_17; james_18)). Fourth, the fraction of dense gas is related to SF and SFE ((cite: Solomon_92; Gao_04; Muraoka_09a; Usero_15; bigiel_16)), and vigorous motions near the dust lane make it difficult for dense gas to survive and may only exist as diffuse gas in the bar region between the center and bar ends (e.g., (cite: sorai_12; muraoka_16; yajima_19)). Lastly, turbulence ((cite: elmegreen_04_araa; mckee_07; haywood_16; khoperskov_18; sun_20)) and magnetic fields found in the dust lanes of the bar ((cite: beck_99; kim_w_12bb)) may prevent molecular clouds from collapsing to form stars ((cite: krumholz_19)).

Extensive studies on NGC 1530, an archetypal barred galaxy, have been performed on kinematics. (cite: reynaud_98) argue that the SF in NGC 1530 is inhibited in dust lanes where shocks and shear are expected to be strong. Using Fabry-Pérot interferometry in H$\alpha$ on NGC 1530, (cite: zurita_04) presents clear observational evidence that shear inhibits massive SF, whereas shocks act to enhance it.

Another aim of this paper is to examine whether the emission-line ratios are modified due to the bar-driven shocks and shear. Several studies show that shocks from stellar winds, stellar feedback, supernova explosions, and galactic outflows can change the optical emission-line ratios (e.g., \[OIII\]/H$\beta$, \[NII\]/H$\alpha$, \[SII\]/H$\alpha$ and \[OI\]/H$\alpha$, (cite: shull_79; calzetti_04; hong_13; ho_14)). Shocks with velocities greater than 110 km$\,\rm s^{-1}$ can generate sufficient UV radiation for complete ionization of H and He ((cite: shull_79)). Depending on the shock velocity and contribution of shock, emission-line ratios can change from the star-forming to the low-ionization nuclear emission-line region (LINER) in the BPT diagram (figure 13 of (cite: ho_14)). Therefore, we examine the emission-line ratio of the bar-driven shocks and shear region in the BPT diagram in order to see whether bar-driven shocks and shear can change the gas properties.

![](fig2_set8_b.pdf)

The paper is organized as follows. We describe the data and the analysis in Section 2. We explain the methods to estimate the H$\alpha$ velocity gradients to identify bar-driven shock and shear in Section 3. We quantify velocity jumps across the high velocity gradients in Section 4. We investigate whether the bar-induced shocks and shear promote or prevent SF in Section 5. By examining the BPT map, we classify the ionizing source on each spaxel, and assess the impact of bar-driven shocks and shear on SF in Section 6. We conclude and summarize our results in Section 7.

# Data

We make use of data products from the PHANGS-MUSE survey ((cite: emsellem_22)). We use the mosaicked datacubes and emission-line fluxes, gas and stellar kinematics, which were convolved and optimized in terms of resolution (“copt”). The PSF of these data have been homogenized spatially across the galaxy, and the seeing of the “copt” data of our sample spans from 0.96” to 1.25”. H$\alpha$ flux and kinematics of the PHANGS-MUSE are obtained using pPXF ((cite: Cappellari_04)).

The H$\alpha$ emission-line is fitted treating as an additional Gaussian function, while the stellar continuum is fitted simultaneously. The velocity and velocity dispersion for H$\alpha$ and H$\beta$ are tied together. Detailed descriptions can be found in (cite: emsellem_22). The spectral resolution is $\sim$50 km$\,\rm s^{-1}$ at H$\alpha$. CO (2$-$1) emission-line flux and velocity maps are drawn from the PHANGS-ALMA survey ((cite: leroy_21b)).

Basic properties of our 4 sample galaxies are presented in Table 1. We present an optical image, maps of H$\alpha$ velocity, galaxy rotation model from H$\alpha$ velocity, difference between H$\alpha$ velocity and galaxy rotation model, H$\alpha$ intensity, stellar velocity, and difference between H$\alpha$ velocity and stellar velocity for NGC 1365 in Figure [2](#fig:NGC1365_basic) as an example. In order to model the galaxy rotation, we utilize ((cite: diteodoro_15)) which is a tool for fitting 3D tilted-ring models to emission-line datacubes. The position angle, inclination of the galaxies, and center are fixed to the values from Table 2 of (cite: lang_20) in running 3D–BAROLO. Velocity dispersion and scale height of the disk are fixed to 8 km$\,\rm s^{-1}$ and 0 arcsec, respectively, which are initial values implemented in . An example of rotation model is presented in Figure [2](#fig:NGC1365_basic)(c). We present velocity differences between the H$\alpha$ velocity and the H$\alpha$ rotation model in Figure [2](#fig:NGC1365_basic)(d), and the velocity differences between H$\alpha$ velocity and stellar velocity maps in Figure [2](#fig:NGC1365_basic)(h).

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Type | Log $M_{\rm star}$ | Distance | Log(SFR) | V$_{\rm sys}$ | PA$_{\rm disk}$ | PA$_{\rm bar}$ | Inc | Scale | Copt PSF |
|  |  | \[M$_{\odot}$\] | \[Mpc\] | \[M$_{\odot}$/yr\] | \[km$/$s\] | \[deg\] | \[deg\] | \[deg\] | \[pc/arcsec\] | \[arcsec\] |
| NGC 1365 | $(R')SB(r\underline{s},nr)bc$ | 10.99 | 19.57 | 1.23 | 1613.3 | 201.1 | 88.5 (65$^{\dag}$) | 55.4 | 94.9 | 1.15 |
| NGC 1512 | $(R\underline{L})SB(r,bl,nr)a$ | 10.71 | 18.83 | 0.11 | 871.4 | 261.9 | 43.07 | 42.5 | 91.3 | 1.25 |
| NGC 1672 | $(R')SA\underline{B}(rs,nr)b$ | 10.73 | 19.40 | 0.88 | 1319.2 | 134.3 | -84.0 | 42.6 | 94.1 | 0.96 |
| NGC 3627 | $SB_{\rm{x}} \rm{(s)b~pec}$ | 10.83 | 11.32 | 0.58 | 717.9 | 173.1 | -22.81 | 57.3 | 54.9 | 1.05 |

: Basic properties of sample galaxies.

Table notes: (1): Galaxy name. (2): Mid-Infrared galaxy morphology ((cite: buta_15)). (3): Stellar mass ((cite: leroy_21b)). (4): Distance ((cite: anand_21)). (5): Star formation rate ((cite: leroy_21b)). (6): Systemic velocity ((cite: lang_20)). (7): Position angle of galaxy from CO kinematics, CCW from the North ((cite: lang_20)). (8): Position angle of bar measured using 3.6 $\mu$m images ((cite: salo_15)). (9): Inclination ((cite: lang_20)). (10): Scale of the PHANGS-MUSE ((cite: emsellem_22)). (11): FWHM of the Gaussian PSF of the homogenized, convolved and optimized (copt) PHANG-MUSE mosaic ((cite: emsellem_22)). ${\dag}$: the PA of the bar dust lane of NGC 1365. As it is different from the PA of the stellar bar for NGC 1365, we rotate NGC 1365 with the PA of the bar dust lane when we obtain the velocity gradient map.

# Velocity gradient

## Deriving gas velocity gradient maps

To explore bar-driven non-circular motions, it is necessary to remove the effect of circular motions. Non-circular motions can be measured in two ways. The first one is to obtain a galaxy rotation model, and subtract it from the observed velocity field (i.e., the H$\alpha$ velocity field in this study, (cite: zurita_04)). The second one is to utilize the differences between the gas and stellar velocity field as gas and stars respond to the bar-driven gravitational forces differently. We use both methods to produce velocity gradient maps for NGC 1365 to explain the methodologies and compare them and present results for other galaxies later in this section. We obtain the velocity gradient map first using the galaxy rotation model with the following steps.

![image](fig3_vg3.pdf) ![image](fig3_shell2.pdf)

1.  From the H$\alpha$ velocity map (Figure [2](#fig:NGC1365_basic)b), we subtract the H$\alpha$ galaxy rotation model (Figure [2](#fig:NGC1365_basic)c) to obtain the H$\alpha$ velocity residual map (Figure [2](#fig:NGC1365_basic)d).

2.  We rotate the velocity residual map to align the bar horizontally using the position angle of the bar presented in Table 1, and denote this map as $V_{\rm res}$.

3.  We move along the velocity residual map by 1 pixel (0.2”, 11 $\sim$ 19 pc depending on object) to the left ($V_{\rm res,-1pix}$) and to the right ($V_{\rm res,+1pix}$), and estimate the horizontal velocity gradient as: $$\begin{equation}
    \nabla V_{x} = \frac{1}{2} \left(| V_{\rm res} - V_{\rm res,-1pix}| + | V_{\rm res} - V_{\rm res,+1pix}| \right)
    \label{eq:vx}
    \end{equation}$$

4.  We estimate the vertical velocity gradient ($\nabla V_{y}$) similarly by moving 1 pixel up and down, perpendicular to the bar.

5.  We add in quadrature both the horizontal ($\nabla V_{x}$) and vertical ($\nabla V_{y}$) velocity gradients to obtain the full velocity gradient. $$\begin{equation}
    \nabla V = \sqrt{{\nabla V_{x}}^2 + {\nabla V_{y}}^2}
    \label{eq:v}
    \end{equation}$$

We plot the velocity gradient map for NGC 1365 in Figure [3](#fig:NGC1365_vg_comparison)(a). The unit of the velocity gradient is km$\,\rm s^{-1}$pc$^{-1}$, and it is not corrected for galaxy inclination[^1]. (cite: zurita_04) show that velocity gradients perpendicular to the bar trace shear along the bar, while velocity gradients parallel to the bar trace shock along the bar. However, our sample galaxies show rather curved dust lanes. Thus, even velocity gradients perpendicular (parallel) to the bar may not perfectly represent shear (shock). Therefore, we use $\nabla V$ for further analysis. We present $\nabla V_{x}$ and $\nabla V_{y}$ in Appendix [8](#sec:app_vg).

Velocity gradients can also be estimated using the differences between the H$\rm \alpha$ and observed stellar velocities (Figure [2](#fig:NGC1365_basic)(h)). We calculate the $V_{\rm H\alpha} - V_{\rm star}$ map and follow the same procedure from step 2 to 5 to obtain the velocity gradient map of NGC 1365 (Figure [3](#fig:NGC1365_vg_comparison)(b)).

Comparing Figure [3](#fig:NGC1365_vg_comparison)(a) and (b), we find that the patterns are almost the same while the one from subtracting the galaxy rotation model is more patchy due to low signal-to-noise regions in estimating the galaxy rotation model. We found similar results for the other sample galaxies where galaxy rotation models are radially smooth. However, when galaxy rotation models are not smooth, the resulting velocity gradient maps becomes bumpy and thus unsuitable for investigating the velocity gradients. Therefore, we opt to use the velocity gradient maps from $V_{\rm H\alpha}-V_{\rm star}$ for further analysis which is unaffected by the galaxy rotation model. In general, if a galaxy is dynamically hot (e.g., bulge-dominated galaxies), we cannot use stellar velocity fields to trace the galaxy rotation because stars also reside outside the disk plane and are dynamically hotter than gas. However, as our sample of barred galaxies are relatively dynamically cold, Figure [3](#fig:NGC1365_vg_comparison) shows that we can use stellar velocity field to trace the galaxy rotation in order to obtain non-circular motions.

We also have tried to obtain the velocity gradient using CO from the PHANGS-ALMA data set. However, bar regions are not sufficiently detected or are patchy along and adjacent to the bar. Thus it is not suitable to obtain the velocity gradient map over the full bar regions for our sample galaxies, although the spectral resolution is superb. We compare the velocity gradients of H$\alpha$ and CO in Appendix [9](#sec:vg_co_ha), and conclude that we can use H$\alpha$ velocity gradients to trace molecular gas velocity gradients for our sample galaxies.

## Two different types of velocity gradients

The velocity gradient map tells us where the velocity changes abruptly. As we add vertical and horizontal components in quadrature, it shows velocity change in both directions. Figure [3](#fig:NGC1365_vg_comparison) shows that there are various shapes of enhanced velocity gradient regions which can be categorized into two groups. First, along the bar dust lanes, there are enhanced velocity gradients that are extended more than 1 kpc, as indicated with white arrows in Figure [3](#fig:NGC1365_vg_comparison)a and b. These are directly connected to the gas inflow along the bar. Therefore, we claim that these velocity gradients are produced by bar-driven shocks and shear.

Second, there are circular or arc-shaped enhanced velocity gradients that are few hundred parsecs in radius which are not related to the bar but spread throughout the galaxy (see white dashed ellipses in Figure [3](#fig:NGC1365_vg_comparison)). The shape of the regions with enhanced velocity gradients suggests they are expanding. Such shapes of high velocity gradients are especially numerous in NGC 1365. We find that H$\alpha$ sources and PAH emissions at 7.7 $\mu {\rm m}$ are located at the center of these circles and arcs (see Figure [3](#fig:NGC1365_vg_comparison)). Thus, we infer that these are due to the expanding shells from HII regions ionized by young stars or stellar associations ((cite: relano_05; bresolin_20)). Also supernova remnants, superbubbles ((cite: watkins_23)) or pre-stellar compression shocks may well produce such high velocity gradients. These velocity gradients are not artificially created by procedures we followed. The velocity difference in these regions can be even seen directly in the H$\alpha$ velocity map and $V_{\rm H\alpha} - V_{\rm star}$ in Figure [2](#fig:NGC1365_basic)(b) and (h). We will study these velocity gradients of expanding regions in more detail in a future paper, while in this work we focus on the first type of high velocity gradients and examine whether the bar-driven shocks and shear inhibit or promote the SF.

![image](fig4_set4_del1_1_ref.pdf) ![image](fig4_set4_del1_2_ref.pdf)

## Velocity gradients due to bar-driven gas inflow

Velocity gradient maps for our sample galaxies are presented in Figure [4](#fig:vg_set4) along with optical, H$\alpha$, and CO images. In deriving velocity gradient maps, we applied amplitude-over-noise ratio of H$\alpha$ greater than 3. We exclude regions where the H$\alpha$ velocity errors ($\delta \rm V_{\rm H\rm \alpha} (x,y)$) are high in the velocity gradient map as follows. We mask out pixels where $\delta \rm V_{\rm H\rm \alpha} (x,y) > \langle \rm \delta \rm V_{H\alpha} \rangle + C \times\sigma(\delta V_{\rm H\alpha})$, where $\langle \delta V_{\rm H\alpha} \rangle$ is the average of H$\alpha$ velocity errors and $\sigma(\delta \rm V_{\rm H\alpha})$ is standard deviation of $\delta V_{\rm H\alpha}$ for each galaxy. Constant C is set to 0.2 for NGC 1365 and NGC 3627, while C is empirically set to $-0.05$ for NGC 1512 and NGC 1672 to avoid spurious signals around the bar to produce a reliable velocity gradient map. The PHANGS-MUSE datasets are Voronoi binned to a target signal-to-noise ratio S/N$=$35 in the continuum range 5300 – 5500 $\rm\AA$), thus regions with low signals have a large bin size. We found that for some of those bins, the differences between H${\rm \alpha}$ and stellar velocity ($V_{\rm H\alpha} - V_{\rm star}$) are artificially large especially at the edge of those bins due to binning. We empirically find that those pixels can be removed if we remove pixels that have the stellar velocity errors greater than the median of stellar velocity errors of each galaxy.

Enhanced velocity gradients clearly show up along the bar dust lanes and they extend out for a considerable length, almost covering the whole bar except for NGC 1365. The velocity gradients of bar region in NGC 1365 range between 0.1 – 1.0 km$\,\rm s^{-1}$pc$^{-1}$. This is consistent with the study of (cite: zurita_04), who find velocity gradients up to 0.35 km$\,\rm s^{-1}$pc$^{-1}$for NGC 1530 and also consistent with the study of (cite: kim_w_12aa), who find 1 – 3 km$\,\rm s^{-1}$pc$^{-1}$of shear across the bar dust lane from numerical simulations. Our results should be considered as a lower limit of the velocity gradient because of the smoothing effect due to the spatial resolution (0.2$"/$pixel) and spectral resolution (2.6 Å, corresponds to 50 km$\,\rm s^{-1}$at H$\alpha$). Detailed notes on each object are available in the Appendix [11](#sec:append_individuals).

## Comparison to the CO Map

Figure 4 shows that the velocity gradients are pronounced along the bars in all samples of galaxies. But exactly where are the velocity gradients enhanced?

Previous studies have found that the velocity gradients coincide with the dust lane, i.e., on the leading side of the bar (see, e.g., (cite: zurita_04) and (cite: feng_22) for studies on NGC 1530 and M31, respectively).

![](VG_CO_contour_label3.pdf)

We plot CO emission-line contours on top of velocity gradient map in Figure [5](#fig:VG_CO_contour_set4) for comparison. We find that velocity gradients are enhanced either along the bar dust lane inferred from the CO distribution or slightly offset to the edge of the bar dust lane.

In NGC 1365, the southern part of the enhanced velocity gradients are located right next to the brightest contour of the CO emission along the bar dust lane. We find that in NGC 1512, enhanced velocity gradients coincide with the CO emission detected along the bar dust lane which can be seen in the optical image. However, in NGC 1672 and NGC 3627, velocity gradients are slightly offset towards to the peak of the CO emission. Velocity gradients are enhanced on the leading side of the bar in NGC 1672 and in the southern part of the NGC 3627. Interestingly, in the northern part of the bar in NGC 3627, it is the opposite. Details on NGC 3627 are in the Appendix [11](#sec:append_individuals). In summary, the locations of enhanced velocity gradient regions either coincide with the peak of the CO emissions or are slightly offset to them, depending on the objects.

![](fig6_a_del1.pdf)

![](NGC1365_slit_vel_rad.pdf)

# Velocity Jumps

We quantify how much velocity jump occurs in the regions where strong bar-driven shocks and shear are expected for our sample galaxies. In order to estimate velocity jumps, we place pseudo slits perpendicular to the regions of high velocity gradient in the bar region. Figure [6](#fig:vel_jump) shows the velocity changes along the slits in selected regions for NGC 1365.

We find that the velocity jump exceeds 100 km$\,\rm s^{-1}$ within 2”(190 pc) in both H$\alpha$ and CO in the slit 1 and 3. Within 5”(475 pc), the velocity of CO changes up to 200 km$\,\rm s^{-1}$, and that of H$\alpha$ changes up to 150 km$\,\rm s^{-1}$ in slit 1. The inclination of NGC 1365 is estimated to be 55.4$^{\circ}$ ((cite: lang_20)). Thus, the velocity jump would become even higher (${\times}$1.2 for NGC 1365) if we correct for inclination. We note that these velocity jumps are measured directly from the velocity map, and therefore are not model-dependent.

While the gaseous velocity jumps are prominent, the stellar velocity jumps are not as pronounced in these regions. The degree of velocity jumps may be different between gas and stars because they respond differently to the gravitational forces of the bar. Gas is dynamically cold and thus highly responsive to the changes in the gravitational potentials it feels as it orbits in the disk.

In addition, gas is collisional and thus easily influenced by shear and shocks, and therefore loses angular momentum more easily, which leads to stronger non-circular motions. However, stars are generally not affected by shocks and stars making up bars are in more stable orbits which lead to milder velocity jumps.

Components of galactic rotation are included in the velocity map and thus in these velocity jumps. Therefore, to exclude the effects of circular motions from galaxy rotation, we subtract the galaxy rotation model from H$\alpha$ velocity map. Then we assess the velocity jump in the bottom right panel of Figure [6](#fig:vel_jump). In fitting galaxy kinematics using 3D–BAROLO, position angles and inclinations can be fixed or freely modeled ring by ring. We present both results. Even after the circular motions are removed, we still find the velocity changes reaching 140 km$\,\rm s^{-1}$ (170 km$\,\rm s^{-1}$ after deprojecion) within 2”(190 pc) in slit 3 and 90 km$\,\rm s^{-1}$ (110 km$\,\rm s^{-1}$ after deprojection) within 4”(380 pc) in slit 1 for NGC 1365. Velocity jumps and the position of pseudo slits of other sample galaxies are present in Appendix [10](#sec:app_veljump). Velocity jumps of other sample galaxies after removal of the galaxy rotation span from 50 to 80 km$\,\rm s^{-1}$ (75 to 95 km$\,\rm s^{-1}$ after deprojection) within 2” and H$\alpha$ velocity jumps are more pronounced compared to stellar velocity jumps as in NGC 1365.

Velocity jumps reaching $\sim$100$-$150 km$\,\rm s^{-1}$ have been found using H$\alpha$, \[NII\], \[SII\], HI and CO ((cite: pence_84; reynaud_98; laine_99; mundell_99; weiner_01a; zurita_04)), and even up to 200 km$\,\rm s^{-1}$ ((cite: zanmar_sanchez_08; feng_22)). Thus, our results are comparable to previous observational studies on the other objects. With idealized hydrodynamic simulations, (cite: kim_w_12aa) show that the velocity along the slit direction changes abruptly by up to 100 km$\,\rm s^{-1}$ within 100 pc while the velocity perpendicular to the slit direction jumps up to 200 km$\,\rm s^{-1}$ within 100 pc in their Figure 8. It is not straightforward to directly compare the values of velocity jump from simulations with our observational data analysis, because we only measure the line of sight velocity. Nevertheless, overall results are still comparable. If we know the pattern speed of the bar and the inclination of the galaxy, we can derive gas velocity vector (e.g., (cite: sormani_23)) by assuming that the gas velocity vector in the bar lanes is parallel to the lane, but this is beyond the scope of this paper.

# Impact of shear and shock on star formation

![](Ha_VG_contour3.pdf)

![](fig_comp_sfr_sd_vg_all_bar_sf_all3.pdf)

In this section, we examine the impact of bar-driven shear and shock on star formation which can be traced approximately by velocity gradients and H$\alpha$ emission, respectively. With this aim, we compare the velocity gradients with H$\alpha$ emission-line maps spatially.

Figure [7](#fig:VG_Ha_contour_set4) shows an extinction-corrected H$\alpha$ emission-line map superimposed with the velocity gradient contours. To correct for extinction, we use the flux ratio of two emission-lines, H$\alpha$/H$\beta$ (Balmer decrement) (e.g., (cite: berman_36; groves_12)). We assume the value of the intrinsic H$\alpha$/H$\beta$ to be 2.86, corresponding to a temperature $T =10^4$ K and an electron density $n_{e} = 10^2 \rm cm^{-3}$ for Case B recombination ((cite: baker_38)). Overall, bright H$\alpha$ sources are rarely found in high velocity gradient regions along the bar. In particular, SF in NGC 1512 is concentrated in the nuclear ring and the inner ring that encircles the bar, and bright H$\alpha$ sources are rare inside of the ring that encompasses the bar. In NGC 3627, there are many star forming regions along the spiral and inter-arm regions. Interestingly, high velocity gradients are avoiding bright star forming regions. Overall, bright SF knots are not found on the enhanced velocity gradient regions.

Then, we examine whether there is an anti-correlation between star forming sites and regions of strong shear and shock in a quantitative approach.

We plot the SFR surface density and velocity gradients in Figure [8](#fig:sfrsd_vg). Each point corresponds to a spaxel. To focus on the shear and shock regions that are directly connected to the gas inflow along the bar, we select the bar regions outside the nuclear region and inside the bar ends, and plot the selected regions in color according to each spaxel’s molecular gas surface density in Figure [8](#fig:sfrsd_vg). Nuclear regions, bar ends, outside the bar regions, and regions with no PHANGS-ALMA CO (2$-$1) detection are plotted in grey. We use the environmental masks from (cite: querejeta_21) to define the bar, bar ends, and nuclear regions.

The SFR is calculated based on H$\alpha$ luminosity. H$\alpha$ traces recent SF as 90% of the H$\alpha$ emission comes from stellar populations younger than 10 Myr ((cite: kennicutt_12)). Although the SFR can be better estimated with hybrid estimators in combination with H$\alpha$, MIR and/or FUV data, it has been shown that once stellar continuum absorption and dust attenuation are properly corrected, there is a good correlation between the SFR derived from H$\alpha$ and the SFR derived from H$\alpha$, UV and MIR data ((cite: catalan_torrecilla_15), see also (cite: belfiore_23)). Furthermore, to conserve the resolution of the H$\alpha$ velocity gradients, we use the SFR derived from H$\alpha$ luminosity in this study.

We estimate the SFR using the following relation ((cite: calzetti_07; kennicutt_12)) $$\begin{equation}
\rm{SFR [M_{\odot} yr^{-1}] = 5.3 \times 10^{42} L(\rm H\alpha)_{corr} [erg\,s^{-1}]},
\end{equation}$$ where $\rm L(\rm H\alpha)_{corr}$ is the extinction-corrected $\rm H\alpha$ luminosity. The molecular mass surface density can be estimated using CO(2$-$1) as $$\begin{equation}
\rm{\Sigma_{mol} = \alpha^{1-0}_{CO} \: R^{-1}_{21} \: I_{CO (2-1)} cos \, \it{i} },
\end{equation}$$ where $\alpha^{1-0}_{\rm CO}$ is the CO(1$-$0) conversion factor, $R^{-1}_{21}$ the CO(2$-$1)$-$to$-$CO(1$-$0) line ratio, and *i* the inclination of a galaxy. We use $\alpha^{1-0}_{\rm CO}$ of the standard Milky Way (4.35 \[$\rm M_{\odot} \rm pc^{-2} ($K km$\,\rm s^{-1}$ $)^{-1}]$, (cite: bolatto_13a)), and we use $R^{-1}_{21}=0.65$ ((cite: leroy_13b; denbrok_21)).

If shear and shocks prevent SF, there should be an anti-correlation between the SFR surface density and the velocity gradients, i.e., the SFR surface density should decrease with the velocity gradients. However, Figure [8](#fig:sfrsd_vg) shows that while the upper envelope of SFR surface density - velocity gradient decreases, data points fill the area below the upper envelope. In low velocity gradient regions, there are regions of diverse values of SFR surface density. But as the velocity gradient increases, the upper envelope of SFR surface density decreases. If we combine it with molecular gas density, this distribution becomes clear to understand. In low velocity gradients, i.e., low shear and shock, regions with high molecular gas density regions show active SF. In the high shear/shock region, active SF is rare. Exceptions are the nuclear regions of NGC 1365 and NGC 1672 where they protrude horizontally in the SFR surface density $-$ velocity gradients diagram.

Our results imply that SF is hindered in bar-driven shear and shocks. This is consistent with previous studies ((cite: reynaud_98; zurita_04)), who conclude that steep velocity gradients prevent molecular gas clouds from condensing to form stars.

Our results are in line with the study of (cite: emsellem_15), who find a notable correlation between the regions of newly formed stars and the location of high density gas clumps with low shear, but not with high shear using hydrodynamical simulations of a Milky Way-like galaxy. In the next section, we re-visit the impact of bar-driven shear and shock on SF using the BPT classification.

# Changes to emission-line ratios due to bar-driven shear and shocks: BPT diagrams

## BPT map

We examine whether shear and shocks driven by bars lead to any change in the ionized gas properties by inspecting emission-line ratio diagnostic diagrams.

Dominant ionizing sources of gas can be separated using the BPT diagram ((cite: baldwin_81; veilleux_87; kewley_01; kauffmann_03c)). A theoretical maximum starburst line ((cite: kewley_01), solid line in Figure [9](#fig:bpt_diagram_1365)) is defined by the upper limit of the theoretical pure stellar photo-ionization model. Points above this line are likely to be dominated by gas ionized by an AGN or shock. Points below the dotted line in Figure [9](#fig:bpt_diagram_1365) ((cite: kauffmann_03c)) represent regions where the emissions come from pure SF. The regions between the dotted line and solid line indicate that gas is ionized by both SF and AGN, thus is named “composite". The dashed line ((cite: cidfernandes_11)) divides Seyfert and low-ionization narrow emission-line regions (LINER).

We plot the BPT diagram for NGC 1365 in Figure [9](#fig:bpt_diagram_1365). Each point denotes a spaxel of the galaxy. All the spaxels which satisfy the amplitude-over-noise ratio of emission-lines greater than 5 are plotted. Blue points represent emissions from star forming regions and green ones denote composite spectra. Orange to red points correspond to Seyfert and magenta points represent LINER. Points that are in close proximity to the maximum starburst line are plotted in lighter shades, whereas points distant from the maximum starburst line are denoted with darker shades. The corresponding maps for all galaxies in the sample are presented in Figure [10](#fig:vg_contour_on_bpt) with the same color coding as in Figure [9](#fig:bpt_diagram_1365).

![](NGC1365_map3.png)

![image](bpt_map1b3.pdf) ![image](bpt_map2b3.pdf)

NGC 1365 displays a biconical outflow (e.g., (cite: phillips_83; jorsater_84; venturi_18; gao_21)). Within that outflow regions, emission-line ratios are located in either Seyfert or LINER area in the BPT diagram. Bar-driven high velocity gradient regions are mostly composite, LINER, or Seyfert. The region marked by the yellow arrow in Figure [10](#fig:vg_contour_on_bpt) shows a remarkably sharp change compared to adjacent regions, from star-forming to composite and Seyfert type. However, in the other bar-driven high velocity gradient regions, the ionizing sources seem to be contaminated by the outflow. Inside the bar radius of NGC 1512, the sources of ionization in most regions are LINER, and it also applies to strong shear regions driven by the bar.

For NGC 1672, high shocks and shear regions are not preferentially occupied by any types of ionizing sources. In NGC 3627, the northern part of the high shear regions is mostly of composite or Seyfert type. However, the southern part of the high shear regions show either star forming or composite.

In the previous Section, we plot velocity gradients and SFR surface density in Figure 8. It contains all the spaxels of SF, LINER, composite, and AGN. If we only consider SF spaxels (black contours in Figure 8), the mean SFR surface density is $\sim$5 times higher on average compared to the spaxels of composite, LINER, and Seyfert (purple contours in Figure 8). SF spaxels span slightly narrow range of velocity gradients with lower ($\sim$20$\%$ on average) mean value.

## SF classified with the BPT

![](bpt_ratio2.pdf)

In order to re-examine whether the SF is inhibited in high shear/shock regions, we classify the ionizing sources using the BPT diagnostics and compare with those of low shear/shock regions in the bar, and all the other regions of galaxy in Figure [11](#fig:ratio_bpt). Nuclear regions and bar ends are excluded in this “bar” region, as they exhibit active SF and shear and shocks due to bar-driven gas inflow are not strong there. We define the high velocity gradient regions in the bar (H) as those with their velocity gradients greater than the upper 5th percentile in the bar for each galaxy, and define the low velocity gradient regions in the bar (L) to have their velocity gradients less than the upper 5th percentile. We also define the interbar region (IB), outside the bar but still within the bar radius. We find that the fraction of the SF group in high velocity gradient regions in the bar (H in Figure [11](#fig:ratio_bpt)) is lower than that of low velocity gradient regions in the bar (L) and all the other regions of the galaxy (A). The majority of high velocity gradient regions exhibit composite or LINER. The fraction of SF group in high velocity gradient regions of the bar spans $\sim$ 2 – 40$\%$. This implies that SF is inhibited in high velocity gradient regions in the bar, which is in line with our results from the previous section that bar-driven shear/shock hinders SF.

By analyzing 240 barred galaxies with MaNGA, (cite: Krishnarao_20b) find that ionized gas is generally classified as LINER-like within the bars, composite in the interbar regions, while ionized gas from SF is located either at the center and/or outside the bar radius. Figure [11](#fig:ratio_bpt) also shows that in the interbar region (IB), the majority of spaxels are either composite or LINER which is consistent with the results of (cite: Krishnarao_20b). Except for NGC 1672, our sample galaxies fit well into their picture in general. However, some galaxies still show SF regions in the bar region (NGC 1365 and NGC 1672). We also found that there are Seyfert spaxels which are not just confined to the center, but related to the biconic outflow from the AGN (NGC 1365) or spread inside the bar radius (NGC 1512, NGC 1672) even without the AGN.

## Enhanced emission-line ratios in the high velocity gradient regions

Our results imply that the emission-line ratios (e.g., \[NII\]/H$\alpha$ and \[OIII\]/H$\beta$) are elevated due to bar-driven shear/shock towards either composite or LINER in the BPT diagram. However, for NGC 1512, the difference between high and low velocity gradient regions of the bar is negligible. There can be two reasons for this.

First, the shock velocity and the fraction of shock converted to excite the gas play roles in enhancing the line ratio. (cite: ho_14) show that in their Figure 13, the line ratios of \[NII\]/H$\alpha$, \[SII\]/H$\alpha$ and \[OI\]/H$\alpha$ increase as the shock velocity increases. Also, within the same shock velocity, the line ratio of \[OIII\]/H$\beta$ increases as the shock fraction increases, where the shock fraction is the contribution of shock excitation relative to HII regions. In Section [4](#sec:velocityjump), we show that the velocity jump in the high velocity gradient regions ranges from 75 km$\,\rm s^{-1}$ to 170 km$\,\rm s^{-1}$, depending on the objects. Therefore, we would expect high shear regions to show enhanced \[NII\]/H$\alpha$ to some degree toward the LINER regime in the BPT diagram. But the shift of \[NII\]/H$\alpha$ also depend on the fraction of shock that is converted to change the emission-line ratio, which can not be readily estimated. Therefore, we infer that the shock fraction might not have been large enough to show a prominent change in the emission-line ratio for NGC 1512.

Second, even though the shear and shock may enhance the line ratio by shock-excitation, if the regions already have increased emission-line ratio and located in LINER or Seyfert domain, then it would be difficult to uplift the line ratios. The whole bar of NGC 1512 is dominated by the LINER or Seyfert type emissions judging by the BPT diagnostics.

It should be also noted that enhanced emission-line ratios do not necessarily guarantee that the ionizing source of the regions are shock originated. The leaking of ionizing photons from HII regions are suggested to be able to explain the diffuse ionized gas with LINER-like emissions ((cite: belfiore_22)). Also, ionization by hot evolved stars (e.g., post AGB) are found to present LINER-like emission ((cite: singh_13)). As post AGB stars are common in galaxies, their ionizing effect can be observed unless a strong radiation from SF or AGN outshines them. As we observe superimposed different ionizing sources along the line of sight, not just on the disk plane but also in the galactic halo, if there is lack of SF in the disk, we may well be left with the LINER-like emission from the post AGBs located along the line of sight. The whole bar regions of NGC 1512 may consist of old stars. Indeed, (cite: pessa_23) find that the mean mass weighted age of the stellar populations in the bar region of NGC 1512 is $\sim$ 10 Gyr.

Recently, (cite: johnston_23) proposed a novel method to distinguish ionizing sources by using the multi-dimensional diagnostic diagram which exploit the classical BPT, velocity dispersion, and equivalent width of H$\alpha$ (see also (cite: cidfernandes_11; dagostino_19)). With the multidimensional diagnostics, they categorize more diverse range of ionization sources, such as the ionization from hot low-mass evolved stars, shocks, elevated kinematics with low emission-line ratio, diffuse ionized gas, in addition to the classical divisions of AGN, LINER, Seyfert, and SF. Applying this multidimensional diagnostics to divide into more detailed classification is beyond the scope of the current paper as we focus on the impact of bar-driven shear and shock on star formation, and we will apply this in the upcoming future paper to explore further the impact of bar dynamics on gas ionization, gas properties such as virial parameter and turbulent pressure.

# Summary and Conclusion

We investigate the impact of bar-driven shocks and shear along the bar dust lane on SF and emission-line ratios by utilizing data from the PHANGS-MUSE and PHANGS-ALMA survey. Our results can be summarized as follows.

1.  We derive velocity gradients using H$\alpha$ and stellar velocity maps, and find that velocity gradients are enhanced along the bar dust lane where shear and shock are expected to occur. CO intensity peaks coincide with the enhanced velocity gradient regions or slightly offset to the edge of the bar dust lane. Enhanced velocity gradient regions show velocity jumps from 50 to 150 km$\,\rm s^{-1}$.

2.  We examine the velocity gradient versus SFR surface density and find that spaxels with high (low) molecular surface density show high (low) SFR surface density in general. In low velocity gradient regions, there are various SFR surface density values from low to high. However, as the velocity gradient increases, the range of SFR surface density narrows down such that the maximum SFR surface density decreases with velocity gradient. Exceptions are nuclear regions and star forming knots in the inner rings, which protrude out in the trend with enhanced velocity gradients.

3.  By comparing the H$\alpha$ emission-line maps and velocity gradient maps (Figure [7](#fig:VG_Ha_contour_set4)), we find that strong SF does not occur in the high velocity gradient regions. We apply the BPT diagnostics on a spaxel by spaxel basis, and find that the fraction of SF spaxels is lower in high velocity gradient regions in the bar compared to low velocity gradient regions in the bar and to all the other regions of the galaxy (Figure [11](#fig:ratio_bpt)). This implies that SF is inhibited in the high velocity gradient regions in the bar where shocks and shear are strong.

4.  The majority of high velocity gradient regions are classified into either LINER or composite categories. This may imply that emission-line ratios are elevated due to bar-driven shock or shear. But we cannot rule out that the absence of recent SF results in revealing LINER-like emission-line.

5.  Our results are consistent with numerical simulations in which bars drive strong shear, and thus, inhibit SF (e.g., (cite: emsellem_15)). Currently, it is not yet clearly known what properties of a barred galaxy control the strength of bar-driven shear and at what shear strength the SF is inhibited. These questions might be answered through further numerical simulations which will lead us to understand the diverse impact of bars on the SF and galaxy evolution.

This research was supported by the Basic Science Research Program through the National Research Foundation of Korea (NRF) funded by the Ministry of Education (RS-2023-00240212 and No. 2019R1I1A3A02062242) and NRF grant funded by the Korean government Ministry of Science and ICT (MSIT) (No. 2022R1A4A3031306). This work was supported by STFC grants ST/T000244/1 and ST/X001075/1. TK acknowledges the support from the Korea Foundation for Women In Science, Engineering and Technology (WISET) Grant (2022-804) funded by MSIT under the Support for Parental Leave Replacement Jobs.

MQ and PSB acknowledge support from the Spanish grants PID2019-106027GA-C44 and PID2019-107427GB-C31 respectively, funded by MCIN/AEI/10.13039/501100011033. A.Z. acknowledges financial support by the research projects PID2020-113689GB-I00, and PID2020-114414GB-I00, financed by MCIN/AEI/10.13039/501100011033, the project A-FQM-510-UGR20 financed from FEDER/Junta de Andalucía-Consejería de Transforam- ción Económica, Industria, Conocimiento y Universidades/Proyecto and by the grants P20\_00334 and FQM108, financed by the Junta de Andalucía (Spain). JN acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). JMA acknowledges the support of the Viera y Clavijo Senior program funded by ACIISI and ULL and the support of the Agencia Estatal de Investigación del Ministerio de Ciencia e Innovación (MCIN/AEI/10.13039/501100011033) under grant nos. PID2021-128131NB-I00 and CNS2022-135482 and the European Regional Development Fund (ERDF) ‘A way of making Europe’ and the ‘NextGenerationEU/PRTR’. AdLC acknowledges financial support from the Spanish Ministry of Science and Innovation (MICINN) to the coBEARD project (PID2021-128131NB-I00). AdLC also acknowledges financial support from MICINN through the Spanish State Research Agency, under the Severo Ochoa Centres of Excellence Programme 2020-2023 (CEX2019-000920-S). LPM thanks FAPESP through grant 2022/03703-1 and CNPQ through grant 307115/2021-6 for financial support. LASL acknowledges CAPES for the support through grant 88887.637633/2021-00 and CNPQ through grant 200469/2022-3. WTK was supported by the grant of the National Research Foundation of Korea (2022R1A2C1004810). MGP acknowledges the support from the Basic Science Research Program through the National Research Foundation of Korea (NRF No- 2019R1I1A3A02062242 and NRF No-2018R1A6A1A06024970) funded by the Ministry of Education, Korea. Based on observations collected at the European Southern Observatory under ESO programmes 1100.B-0651, 095.C-0473, and 094.C- 0623 (PHANGS-MUSE; PI: Schinnerer), as well as 094.B-0321 (MAGNUM; PI: Marconi), and 097.B-0640 (TIMER; PI: Gadotti). Raw and reduced data are available at the ESO Science Archive Facility.

# Facilities

VLT, ALMA, JWST

# Velocity gradient perpendicular to the bar and parallel to the bar

Velocity gradients can be divided in two different components, perpendicular and parallel to the bar. We estimate parallel velocity gradient ($\nabla V_x$) and perpendicular velocity gradient ($\nabla V_y$) separately, and compare them in Figure [12](#fig:VG_per_par). We re-estimate the ratio of the SF group classified by the BPT diagnostics in high and low velocity gradient regions and all the other regions of each galaxy with $\nabla V_x$ and $\nabla V_y$ as in Figure [11](#fig:ratio_bpt). We obtain the same results that the ratio of SF group is lower in high velocity gradient regions compared to the others.

![image](fig_app_vgs_1_log.pdf) ![image](fig_app_vgs_2_log.pdf) ![image](fig_app_vgs_3_log.pdf)

# Comparing velocity gradients from H$\alpha$ and CO

Velocity gradients can also be obtained using the CO velocity field. However, compared to H$\rm \alpha$, CO is patchy and only detected marginally along the bar for some galaxies. In order to examine how well do H$\rm \alpha$ velocity gradients trace velocity gradients of molecular clouds, we compare velocity gradients from H$\rm \alpha$ ($\nabla V_{\rm H \rm \alpha}$) and CO ($\nabla V_{\rm CO}$) in Figure [13](#fig:VG_CO_Ha). $\nabla V_{\rm H\alpha}$ is estimated from the map of ($V_{\rm H \alpha} - V_{\rm star}$) and $\nabla V_{\rm CO}$ is estimated with ($V_{\rm CO} - V_{\rm star}$) map following the same steps presented in Section [3.1](#sec:deriving_vg). CO in the bar of NGC 1512 is marginally detected along the bar, therefore we could not obtain CO velocity gradients for this object. We find that while there is a spread (specially for low gradients), CO velocity gradients are correlated with H$\alpha$ velocity gradients. This suggests that we can use H$\rm \alpha$ velocity gradients to trace molecular gas velocity gradients for these galaxies.

![](comp_ha_co_vgmag_set3.png)

# Velocity jumps for sample galaxies

We present velocity jumps on high velocity gradient regions for the rest of the sample galaxies in Figure [14](#fig:vel_jump_appendix).

![image](fig_app_slits3_ngc1512.pdf) ![image](NGC1512_slit_vel_rad.pdf)

![image](fig_app_slits3_ngc1672.pdf) ![image](NGC1672_slit_vel_rad.pdf)

![image](fig_app_slits3_ngc3627.pdf) ![image](NGC3627_slit_vel_rad.pdf)

# Notes on individual galaxies

## NGC 1365

Although there are numerous enhanced velocity gradients which are thought to be originated by the expanding HII regions, velocity gradients along the bar dust lanes are not prominent in the outer part (R$>$15”) of the galaxy, and are not symmetric. (cite: schinnerer_23) combined JWST/MIRI, ALMA and MUSE data and found that the gas inflow onto the central ring is asymmetric and different between the two dust lanes. In addition, they found that in the southern dust lane, young star clusters are rarely found even with abundant molecular gas with properties similar to the other dust lane are present. Exactly in this region (marked with yellow arrow in Figure [10](#fig:vg_contour_on_bpt)), we found that the velocity gradient is enhanced.

## NGC 1672

In Figure [8](#fig:sfrsd_vg), there are two branches that stick out prominently, one with high $\Sigma_{mol}$, and one with lower $\Sigma_{mol}$. The branch with high $\Sigma_{mol}$, where the $\Sigma_{mol}$ ranges between $10^{-1}$ and $10^0$ and the velocity gradients between 0.2 and 0.7 km$\,\rm s^{-1}$ , belong to the nuclear region (R$<$2.5”) inside the nuclear ring. In this region, CO (2$-$1) and H$\alpha$ intensity is high, and also the velocity gradient is extraordinarily high. The elevated velocity gradients may be caused by intense winds from young stars, as it appears to be the case in other galaxies with star-bursting nuclear rings, such as NGC 3351 (see (cite: leaman_19)). The other branch with low $\Sigma_{\rm mol}$ ($10^{-3}\sim10^{-2}$) consist of regions around faint H$\alpha$ sources with distinctive velocities.

## NGC 3627

Enhanced velocity gradients along the dust lane are disconnected at R$\sim$19" ($\sim$1 kpc) in both sides from the center (Figure [4](#fig:vg_set4)). The elevated velocity gradients in the southern outer part (R$>$19") are located at the leading side compared to the CO peaks (Figure [5](#fig:VG_CO_contour_set4)), but in the inner part (R$<$19”), they are located at the trailing side compared to the CO intensity. Along the northern part of the bar, enhanced velocity gradients are located along the trailing side. It is not clear why enhanced velocity gradient regions are located in the trailing side in some parts especially in this galaxy, as they are located along or at the leading side of the dust lane in other sample galaxies. Gas inflow is found to be reduced when there is a boxy/peanut-shaped bulge ((cite: fragkoudi_16)), and interestingly the boxy/peanut-shaped bulge of the galaxy spans 18" ((cite: erwin_16)). We suggest that the orbital structures due to the boxy/peanut-shaped bulge and spurs ((cite: erwin_13; erwin_16)) may have an effect on the gas inflow, and may be related to the origin of this offset.

natexlab

(ref: aguerri_09) Aguerri, J. A. L., Méndez-Abreu, J., & Corsini, E. M. 2009, A&A, 495, 491, doi: [`10.1051/0004-6361:200810931`](http://doi.org/10.1051/0004-6361:200810931)

(ref: anand_21) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: athanassoula_92b) Athanassoula, E. 1992, MNRAS, 259, 345

(ref: athanassoula_02a) Athanassoula, E., & Misiriotis, A. 2002, MNRAS, 330, 35, doi: [`10.1046/j.1365-8711.2002.05028.x`](http://doi.org/10.1046/j.1365-8711.2002.05028.x)

(ref: baker_38) Baker, J. G., & Menzel, D. H. 1938, ApJ, 88, 52, doi: [`10.1086/143959`](http://doi.org/10.1086/143959)

(ref: baldwin_81) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5, doi: [`10.1086/130766`](http://doi.org/10.1086/130766)

(ref: barazza_08) Barazza, F. D., Jogee, S., & Marinova, I. 2008, ApJ, 675, 1194, doi: [`10.1086/526510`](http://doi.org/10.1086/526510)

(ref: beck_99) Beck, R., Ehle, M., Shoutenkov, V., Shukurov, A., & Sokoloff, D. 1999, Nature, 397, 324, doi: [`10.1038/16861`](http://doi.org/10.1038/16861)

(ref: belfiore_22) Belfiore, F., Santoro, F., Groves, B., et al. 2022, A&A, 659, A26, doi: [`10.1051/0004-6361/202141859`](http://doi.org/10.1051/0004-6361/202141859)

(ref: belfiore_23) Belfiore, F., Leroy, A. K., Sun, J., et al. 2023, A&A, 670, A67, doi: [`10.1051/0004-6361/202244863`](http://doi.org/10.1051/0004-6361/202244863)

(ref: berman_36) Berman, L. 1936, MNRAS, 96, 890, doi: [`10.1093/mnras/96.9.890`](http://doi.org/10.1093/mnras/96.9.890)

(ref: beuther_17) Beuther, H., Meidt, S., Schinnerer, E., Paladino, R., & Leroy, A. 2017, A&A, 597, A85, doi: [`10.1051/0004-6361/201526749`](http://doi.org/10.1051/0004-6361/201526749)

(ref: bigiel_16) Bigiel, F., Leroy, A. K., Jiménez-Donaire, M. J., et al. 2016, ApJL, 822, L26, doi: [`10.3847/2041-8205/822/2/L26`](http://doi.org/10.3847/2041-8205/822/2/L26)

(ref: bittner_21) Bittner, A., de Lorenzo-Cáceres, A., Gadotti, D. A., et al. 2020, arXiv e-prints, arXiv:2012.04661. [`https://arxiv.org/abs/2012.04661`](https://arxiv.org/abs/2012.04661)

(ref: bolatto_13a) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013, Nature, 499, 450, doi: [`10.1038/nature12351`](http://doi.org/10.1038/nature12351)

(ref: bosma_81) Bosma, A. 1981, AJ, 86, 1825, doi: [`10.1086/113063`](http://doi.org/10.1086/113063)

(ref: bresolin_20) Bresolin, F., Rizzi, L., Ho, I. T., et al. 2020, MNRAS, 495, 4347, doi: [`10.1093/mnras/staa1472`](http://doi.org/10.1093/mnras/staa1472)

(ref: bundy_15) Bundy, K., Bershady, M. A., Law, D. R., et al. 2015, ApJ, 798, 7, doi: [`10.1088/0004-637X/798/1/7`](http://doi.org/10.1088/0004-637X/798/1/7)

(ref: buta_15) Buta, R. J., Sheth, K., Athanassoula, E., et al. 2015, ApJS, 217, 32, doi: [`10.1088/0067-0049/217/2/32`](http://doi.org/10.1088/0067-0049/217/2/32)

(ref: calzetti_04) Calzetti, D., Harris, J., Gallagher, John S., I., et al. 2004, AJ, 127, 1405, doi: [`10.1086/382095`](http://doi.org/10.1086/382095)

(ref: calzetti_07) Calzetti, D., Kennicutt, R. C., Engelbracht, C. W., et al. 2007, ApJ, 666, 870, doi: [`10.1086/520082`](http://doi.org/10.1086/520082)

(ref: Cappellari_04) Cappellari, M., & Emsellem, E. 2004, PASP, 116, 138, doi: [`10.1086/381875`](http://doi.org/10.1086/381875)

(ref: catalan_torrecilla_15) Catalán-Torrecilla, C., Gil de Paz, A., Castillo-Morales, A., et al. 2015, A&A, 584, A87, doi: [`10.1051/0004-6361/201526023`](http://doi.org/10.1051/0004-6361/201526023)

(ref: cheung_15) Cheung, E., Trump, J. R., Athanassoula, E., et al. 2015, MNRAS, 447, 506, doi: [`10.1093/mnras/stu2462`](http://doi.org/10.1093/mnras/stu2462)

(ref: cidfernandes_11) Cid Fernandes, R., Stasińska, G., Mateus, A., & Vale Asari, N. 2011, MNRAS, 413, 1687, doi: [`10.1111/j.1365-2966.2011.18244.x`](http://doi.org/10.1111/j.1365-2966.2011.18244.x)

(ref: cisternas_13) Cisternas, M., Gadotti, D. A., Knapen, J. H., et al. 2013, ApJ, 776, 50, doi: [`10.1088/0004-637X/776/1/50`](http://doi.org/10.1088/0004-637X/776/1/50)

(ref: combes_81) Combes, F., & Sanders, R. H. 1981, A&A, 96, 164

(ref: comeron_14) Comerón, S., Salo, H., Laurikainen, E., et al. 2014, A&A, 562, A121, doi: [`10.1051/0004-6361/201321633`](http://doi.org/10.1051/0004-6361/201321633)

(ref: contopoulos_80b) Contopoulos, G., & Papayannopoulos, T. 1980, A&A, 92, 33

(ref: dagostino_19) D’Agostino, J. J., Kewley, L. J., Groves, B. A., et al. 2019, MNRAS, 487, 4153, doi: [`10.1093/mnras/stz1611`](http://doi.org/10.1093/mnras/stz1611)

(ref: delorenzo_caceres_19b) de Lorenzo-Cáceres, A., Sánchez-Blázquez, P., Méndez-Abreu, J., et al. 2019, MNRAS, 484, 5296, doi: [`10.1093/mnras/stz221`](http://doi.org/10.1093/mnras/stz221)

(ref: desafreitas_23a) de Sá-Freitas, C., Gadotti, D. A., Fragkoudi, F., et al. 2023a, arXiv e-prints, arXiv:2308.04482, doi: [`10.48550/arXiv.2308.04482`](http://doi.org/10.48550/arXiv.2308.04482)

(ref: desafreitas_23b) —. 2023b, A&A, 678, A202, doi: [`10.1051/0004-6361/202347028`](http://doi.org/10.1051/0004-6361/202347028)

(ref: devaucouleurs_63) de Vaucouleurs, G. 1963, ApJS, 8, 31, doi: [`10.1086/190084`](http://doi.org/10.1086/190084)

(ref: denbrok_21) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221, doi: [`10.1093/mnras/stab859`](http://doi.org/10.1093/mnras/stab859)

(ref: diteodoro_15) Di Teodoro, E. M., & Fraternali, F. 2015, MNRAS, 451, 3021, doi: [`10.1093/mnras/stv1213`](http://doi.org/10.1093/mnras/stv1213)

(ref: diaz-garcia_20) Dı́az-Garcı́a, S., Moyano, F. D., Comerón, S., et al. 2020, A&A, 644, A38, doi: [`10.1051/0004-6361/202039162`](http://doi.org/10.1051/0004-6361/202039162)

(ref: diaz-garcia_16) Dı́az-Garcı́a, S., Salo, H., Laurikainen, E., & Herrera-Endoqui, M. 2016, A&A, 587, A160, doi: [`10.1051/0004-6361/201526161`](http://doi.org/10.1051/0004-6361/201526161)

(ref: diaz-garcia_21) Dı́az-Garcı́a, S., Lisenfeld, U., Pérez, I., et al. 2021, A&A, 654, A135, doi: [`10.1051/0004-6361/202140674`](http://doi.org/10.1051/0004-6361/202140674)

(ref: downes_96) Downes, D., Reynaud, D., Solomon, P. M., & Radford, S. J. E. 1996, ApJ, 461, 186, doi: [`10.1086/177046`](http://doi.org/10.1086/177046)

(ref: elmegreen_04_araa) Elmegreen, B. G., & Scalo, J. 2004, ARA&A, 42, 211, doi: [`10.1146/annurev.astro.41.011802.094859`](http://doi.org/10.1146/annurev.astro.41.011802.094859)

(ref: emsellem_15) Emsellem, E., Renaud, F., Bournaud, F., et al. 2015, MNRAS, 446, 2468, doi: [`10.1093/mnras/stu2209`](http://doi.org/10.1093/mnras/stu2209)

(ref: emsellem_22) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: englmaier_97) Englmaier, P., & Gerhard, O. 1997, MNRAS, 287, 57, doi: [`10.1093/mnras/287.1.57`](http://doi.org/10.1093/mnras/287.1.57)

(ref: erwin_13) Erwin, P., & Debattista, V. P. 2013, MNRAS, 431, 3060, doi: [`10.1093/mnras/stt385`](http://doi.org/10.1093/mnras/stt385)

(ref: erwin_16) —. 2016, ApJL, 825, L30, doi: [`10.3847/2041-8205/825/2/L30`](http://doi.org/10.3847/2041-8205/825/2/L30)

(ref: eskridge_00) Eskridge, P. B., Frogel, J. A., Pogge, R. W., et al. 2000, AJ, 119, 536, doi: [`10.1086/301203`](http://doi.org/10.1086/301203)

(ref: fathi_05) Fathi, K., van de Ven, G., Peletier, R. F., et al. 2005, MNRAS, 364, 773, doi: [`10.1111/j.1365-2966.2005.09648.x`](http://doi.org/10.1111/j.1365-2966.2005.09648.x)

(ref: feng_22) Feng, Z.-X., Li, Z., Shen, J., et al. 2022, ApJ, 933, 233, doi: [`10.3847/1538-4357/ac7964`](http://doi.org/10.3847/1538-4357/ac7964)

(ref: fragkoudi_16) Fragkoudi, F., Athanassoula, E., & Bosma, A. 2016, MNRAS, 462, L41, doi: [`10.1093/mnrasl/slw120`](http://doi.org/10.1093/mnrasl/slw120)

(ref: fragkoudi_17a) —. 2017, MNRAS, 466, 474, doi: [`10.1093/mnras/stw3023`](http://doi.org/10.1093/mnras/stw3023)

(ref: fragkoudi_20) Fragkoudi, F., Grand, R. J. J., Pakmor, R., et al. 2020, MNRAS, 494, 5936, doi: [`10.1093/mnras/staa1104`](http://doi.org/10.1093/mnras/staa1104)

(ref: fraser-mckelvie_20a) Fraser-McKelvie, A., Aragón-Salamanca, A., Merrifield, M., et al. 2020, MNRAS, 495, 4158, doi: [`10.1093/mnras/staa1416`](http://doi.org/10.1093/mnras/staa1416)

(ref: fujimoto_14a) Fujimoto, Y., Tasker, E. J., & Habe, A. 2014, MNRAS, 445, L65, doi: [`10.1093/mnrasl/slu138`](http://doi.org/10.1093/mnrasl/slu138)

(ref: gadotti_19) Gadotti, D. A., Sánchez-Blázquez, P., Falcón-Barroso, J., et al. 2019, MNRAS, 482, 506, doi: [`10.1093/mnras/sty2666`](http://doi.org/10.1093/mnras/sty2666)

(ref: gadotti_20) Gadotti, D. A., Bittner, A., Falcón-Barroso, J., et al. 2020, A&A, 643, A14, doi: [`10.1051/0004-6361/202038448`](http://doi.org/10.1051/0004-6361/202038448)

(ref: gao_21) Gao, Y., Egusa, F., Liu, G., et al. 2021, ApJ, 913, 139, doi: [`10.3847/1538-4357/abf738`](http://doi.org/10.3847/1538-4357/abf738)

(ref: Gao_04) Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271, doi: [`10.1086/382999`](http://doi.org/10.1086/382999)

(ref: garland_23) Garland, I. L., Fahey, M. J., Simmons, B. D., et al. 2023, MNRAS, 522, 211, doi: [`10.1093/mnras/stad966`](http://doi.org/10.1093/mnras/stad966)

(ref: groves_12) Groves, B., Brinchmann, J., & Walcher, C. J. 2012, MNRAS, 419, 1402, doi: [`10.1111/j.1365-2966.2011.19796.x`](http://doi.org/10.1111/j.1365-2966.2011.19796.x)

(ref: hatchfield_21) Hatchfield, H. P., Sormani, M. C., Tress, R. G., et al. 2021, ApJ, 922, 79, doi: [`10.3847/1538-4357/ac1e89`](http://doi.org/10.3847/1538-4357/ac1e89)

(ref: hawarden_86) Hawarden, T. G., Mountain, C. M., Leggett, S. K., & Puxley, P. J. 1986, MNRAS, 221, 41P

(ref: haywood_16) Haywood, M., Lehnert, M. D., Di Matteo, P., et al. 2016, A&A, 589, A66, doi: [`10.1051/0004-6361/201527567`](http://doi.org/10.1051/0004-6361/201527567)

(ref: hirota_14) Hirota, A., Kuno, N., Baba, J., et al. 2014, PASJ, 66, 46, doi: [`10.1093/pasj/psu006`](http://doi.org/10.1093/pasj/psu006)

(ref: ho_14) Ho, I. T., Kewley, L. J., Dopita, M. A., et al. 2014, MNRAS, 444, 3894, doi: [`10.1093/mnras/stu1653`](http://doi.org/10.1093/mnras/stu1653)

(ref: ho_97) Ho, L. C., Filippenko, A. V., & Sargent, W. L. W. 1997, ApJ, 487, 591, doi: [`10.1086/304643`](http://doi.org/10.1086/304643)

(ref: hohl_71) Hohl, F. 1971, ApJ, 168, 343, doi: [`10.1086/151091`](http://doi.org/10.1086/151091)

(ref: hong_13) Hong, S., Calzetti, D., Gallagher, John S., I., et al. 2013, ApJ, 777, 63, doi: [`10.1088/0004-637X/777/1/63`](http://doi.org/10.1088/0004-637X/777/1/63)

(ref: james_18) James, P. A., & Percival, S. M. 2018, MNRAS, 474, 3101, doi: [`10.1093/mnras/stx2990`](http://doi.org/10.1093/mnras/stx2990)

(ref: johnston_23) Johnston, V. D., Medling, A. M., Groves, B., et al. 2023, ApJ, 954, 77, doi: [`10.3847/1538-4357/ace90e`](http://doi.org/10.3847/1538-4357/ace90e)

(ref: jorsater_84) Jorsater, S., Lindblad, P. O., & Boksenberg, A. 1984, A&A, 140, 288

(ref: kauffmann_03c) Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055, doi: [`10.1111/j.1365-2966.2003.07154.x`](http://doi.org/10.1111/j.1365-2966.2003.07154.x)

(ref: kennicutt_12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: kewley_01) Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J. 2001, ApJ, 556, 121, doi: [`10.1086/321545`](http://doi.org/10.1086/321545)

(ref: khoperskov_18) Khoperskov, S., Haywood, M., Di Matteo, P., Lehnert, M. D., & Combes, F. 2018, A&A, 609, A60, doi: [`10.1051/0004-6361/201731211`](http://doi.org/10.1051/0004-6361/201731211)

(ref: kim_w_12aa) Kim, W.-T., Seo, W.-Y., Stone, J. M., Yoon, D., & Teuben, P. J. 2012a, ApJ, 747, 60, doi: [`10.1088/0004-637X/747/1/60`](http://doi.org/10.1088/0004-637X/747/1/60)

(ref: kim_w_12bb) Kim, W.-T., & Stone, J. M. 2012b, ApJ, 751, 124, doi: [`10.1088/0004-637X/751/2/124`](http://doi.org/10.1088/0004-637X/751/2/124)

(ref: knapen_95) Knapen, J. H., Beckman, J. E., Heller, C. H., Shlosman, I., & de Jong, R. S. 1995, ApJ, 454, 623, doi: [`10.1086/176516`](http://doi.org/10.1086/176516)

(ref: knapen_00) Knapen, J. H., Shlosman, I., & Peletier, R. F. 2000, ApJ, 529, 93, doi: [`10.1086/308266`](http://doi.org/10.1086/308266)

(ref: kolcu_23) Kolcu, T., Maciejewski, W., Gadotti, D. A., et al. 2023, MNRAS, 524, 207, doi: [`10.1093/mnras/stad1896`](http://doi.org/10.1093/mnras/stad1896)

(ref: kraljic_12) Kraljic, K., Bournaud, F., & Martig, M. 2012, ApJ, 757, 60, doi: [`10.1088/0004-637X/757/1/60`](http://doi.org/10.1088/0004-637X/757/1/60)

(ref: Krishnarao_20b) Krishnarao, D., Tremonti, C., Fraser-McKelvie, A., et al. 2020, ApJ, 898, 116, doi: [`10.3847/1538-4357/ab9fa3`](http://doi.org/10.3847/1538-4357/ab9fa3)

(ref: krumholz_19) Krumholz, M. R., & Federrath, C. 2019, Frontiers in Astronomy and Space Sciences, 6, 7, doi: [`10.3389/fspas.2019.00007`](http://doi.org/10.3389/fspas.2019.00007)

(ref: laine_99) Laine, S., Kenney, J. D. P., Yun, M. S., & Gottesman, S. T. 1999, ApJ, 511, 709, doi: [`10.1086/306709`](http://doi.org/10.1086/306709)

(ref: laine_02) Laine, S., Shlosman, I., Knapen, J. H., & Peletier, R. F. 2002, ApJ, 567, 97, doi: [`10.1086/323964`](http://doi.org/10.1086/323964)

(ref: lang_20) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122, doi: [`10.3847/1538-4357/ab9953`](http://doi.org/10.3847/1538-4357/ab9953)

(ref: leaman_19) Leaman, R., Fragkoudi, F., Querejeta, M., et al. 2019, MNRAS, 488, 3904, doi: [`10.1093/mnras/stz1844`](http://doi.org/10.1093/mnras/stz1844)

(ref: lee_23) Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2023, ApJL, 944, L17, doi: [`10.3847/2041-8213/acaaae`](http://doi.org/10.3847/2041-8213/acaaae)

(ref: lee_19) Lee, Y. H., Ann, H. B., & Park, M.-G. 2019, ApJ, 872, 97, doi: [`10.3847/1538-4357/ab0024`](http://doi.org/10.3847/1538-4357/ab0024)

(ref: leroy_13b) Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ, 146, 19, doi: [`10.1088/0004-6256/146/2/19`](http://doi.org/10.1088/0004-6256/146/2/19)

(ref: leroy_21a) Leroy, A. K., Hughes, A., Liu, D., et al. 2021a, ApJS, 255, 19, doi: [`10.3847/1538-4365/abec80`](http://doi.org/10.3847/1538-4365/abec80)

(ref: leroy_21b) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: lopez_coba_22) López-Cobá, C., Sánchez, S. F., Lin, L., et al. 2022, ApJ, 939, 40, doi: [`10.3847/1538-4357/ac937b`](http://doi.org/10.3847/1538-4357/ac937b)

(ref: maeda_23) Maeda, F., Egusa, F., Ohta, K., Fujimoto, Y., & Habe, A. 2023, ApJ, 943, 7, doi: [`10.3847/1538-4357/aca664`](http://doi.org/10.3847/1538-4357/aca664)

(ref: maeda_21) Maeda, F., Ohta, K., Fujimoto, Y., & Habe, A. 2021, MNRAS, 502, 2238, doi: [`10.1093/mnras/stab130`](http://doi.org/10.1093/mnras/stab130)

(ref: maeda_20b) Maeda, F., Ohta, K., Fujimoto, Y., Habe, A., & Ushio, K. 2020, MNRAS, 495, 3840, doi: [`10.1093/mnras/staa1296`](http://doi.org/10.1093/mnras/staa1296)

(ref: martin_97) Martin, P., & Friedli, D. 1997, A&A, 326, 449

(ref: masters_11) Masters, K. L., Nichol, R. C., Hoyle, B., et al. 2011, MNRAS, 411, 2026, doi: [`10.1111/j.1365-2966.2010.17834.x`](http://doi.org/10.1111/j.1365-2966.2010.17834.x)

(ref: mckee_07) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565, doi: [`10.1146/annurev.astro.45.051806.110602`](http://doi.org/10.1146/annurev.astro.45.051806.110602)

(ref: menendez_delmestre_07) Menéndez-Delmestre, K., Sheth, K., Schinnerer, E., Jarrett, T. H., & Scoville, N. Z. 2007, ApJ, 657, 790, doi: [`10.1086/511025`](http://doi.org/10.1086/511025)

(ref: Momose_10) Momose, R., Okumura, S. K., Koda, J., & Sawada, T. 2010, ApJ, 721, 383, doi: [`10.1088/0004-637X/721/1/383`](http://doi.org/10.1088/0004-637X/721/1/383)

(ref: mundell_99) Mundell, C. G., & Shone, D. L. 1999, MNRAS, 304, 475, doi: [`10.1046/j.1365-8711.1999.02330.x`](http://doi.org/10.1046/j.1365-8711.1999.02330.x)

(ref: Muraoka_09a) Muraoka, K., Kohno, K., Tosaki, T., et al. 2009, PASJ, 61, 163, doi: [`10.1093/pasj/61.2.163`](http://doi.org/10.1093/pasj/61.2.163)

(ref: muraoka_16) Muraoka, K., Sorai, K., Kuno, N., et al. 2016, PASJ, 68, 89, doi: [`10.1093/pasj/psw080`](http://doi.org/10.1093/pasj/psw080)

(ref: Muraoka_19) Muraoka, K., Sorai, K., Miyamoto, Y., et al. 2019, PASJ, 71, S15, doi: [`10.1093/pasj/psz015`](http://doi.org/10.1093/pasj/psz015)

(ref: neumann_19) Neumann, J., Gadotti, D. A., Wisotzki, L., et al. 2019, A&A, 627, A26, doi: [`10.1051/0004-6361/201834441`](http://doi.org/10.1051/0004-6361/201834441)

(ref: ostriker_73) Ostriker, J. P., & Peebles, P. J. E. 1973, ApJ, 186, 467, doi: [`10.1086/152513`](http://doi.org/10.1086/152513)

(ref: pence_84) Pence, W. D., & Blackman, C. P. 1984, MNRAS, 207, 9, doi: [`10.1093/mnras/207.1.9`](http://doi.org/10.1093/mnras/207.1.9)

(ref: pessa_22) Pessa, I., Schinnerer, E., Leroy, A. K., et al. 2022, A&A, 663, A61, doi: [`10.1051/0004-6361/202142832`](http://doi.org/10.1051/0004-6361/202142832)

(ref: pessa_23) Pessa, I., Schinnerer, E., Sanchez-Blazquez, P., et al. 2023, A&A, 673, A147, doi: [`10.1051/0004-6361/202245673`](http://doi.org/10.1051/0004-6361/202245673)

(ref: peterson_80) Peterson, C. J., & Huntley, J. M. 1980, ApJ, 242, 913, doi: [`10.1086/158525`](http://doi.org/10.1086/158525)

(ref: phillips_83) Phillips, M. M., Turtle, A. J., Edmunds, M. G., & Pagel, B. E. J. 1983, MNRAS, 203, 759, doi: [`10.1093/mnras/203.3.759`](http://doi.org/10.1093/mnras/203.3.759)

(ref: querejeta_21) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: regan_99) Regan, M. W., Sheth, K., & Vogel, S. N. 1999, ApJ, 526, 97, doi: [`10.1086/307960`](http://doi.org/10.1086/307960)

(ref: regan_97a) Regan, M. W., Vogel, S. N., & Teuben, P. J. 1997, ApJL, 482, L143, doi: [`10.1086/310717`](http://doi.org/10.1086/310717)

(ref: relano_05) Relaño, M., & Beckman, J. E. 2005, A&A, 430, 911, doi: [`10.1051/0004-6361:20041708`](http://doi.org/10.1051/0004-6361:20041708)

(ref: renaud_15) Renaud, F., Bournaud, F., Emsellem, E., et al. 2015, MNRAS, 454, 3299, doi: [`10.1093/mnras/stv2223`](http://doi.org/10.1093/mnras/stv2223)

(ref: reynaud_98) Reynaud, D., & Downes, D. 1998, A&A, 337, 671

(ref: roberts_79) Roberts, W. W., J., Huntley, J. M., & van Albada, G. D. 1979, ApJ, 233, 67, doi: [`10.1086/157367`](http://doi.org/10.1086/157367)

(ref: rozas_00) Rozas, M., Zurita, A., Beckman, J. E., & Pérez, D. 2000, A&AS, 142, 259, doi: [`10.1051/aas:2000329`](http://doi.org/10.1051/aas:2000329)

(ref: salo_10) Salo, H., Laurikainen, E., Buta, R., & Knapen, J. H. 2010, ApJL, 715, L56, doi: [`10.1088/2041-8205/715/1/L56`](http://doi.org/10.1088/2041-8205/715/1/L56)

(ref: salo_15) Salo, H., Laurikainen, E., Laine, J., et al. 2015, ApJS, 219, 4, doi: [`10.1088/0067-0049/219/1/4`](http://doi.org/10.1088/0067-0049/219/1/4)

(ref: sanchez_12) Sánchez, S. F., Kennicutt, R. C., Gil de Paz, A., et al. 2012, A&A, 538, A8, doi: [`10.1051/0004-6361/201117353`](http://doi.org/10.1051/0004-6361/201117353)

(ref: schinnerer_23) Schinnerer, E., Emsellem, E., Henshaw, J. D., et al. 2023, ApJL, 944, L15, doi: [`10.3847/2041-8213/acac9e`](http://doi.org/10.3847/2041-8213/acac9e)

(ref: scoville_86) Scoville, N. Z., Sanders, D. B., & Clemens, D. P. 1986, ApJL, 310, L77, doi: [`10.1086/184785`](http://doi.org/10.1086/184785)

(ref: seo_19) Seo, W.-Y., Kim, W.-T., Kwak, S., et al. 2019, ApJ, 872, 5, doi: [`10.3847/1538-4357/aafc5f`](http://doi.org/10.3847/1538-4357/aafc5f)

(ref: sheth_12) Sheth, K., Melbourne, J., Elmegreen, D. M., et al. 2012, ApJ, 758, 136, doi: [`10.1088/0004-637X/758/2/136`](http://doi.org/10.1088/0004-637X/758/2/136)

(ref: sheth_00) Sheth, K., Regan, M. W., Vogel, S. N., & Teuben, P. J. 2000, ApJ, 532, 221, doi: [`10.1086/308530`](http://doi.org/10.1086/308530)

(ref: sheth_05) Sheth, K., Vogel, S. N., Regan, M. W., Thornley, M. D., & Teuben, P. J. 2005, ApJ, 632, 217, doi: [`10.1086/432409`](http://doi.org/10.1086/432409)

(ref: shull_79) Shull, J. M., & McKee, C. F. 1979, ApJ, 227, 131, doi: [`10.1086/156712`](http://doi.org/10.1086/156712)

(ref: silva_lima_22) Silva-Lima, L. A., Martins, L. P., Coelho, P. R. T., & Gadotti, D. A. 2022, A&A, 661, A105, doi: [`10.1051/0004-6361/202142432`](http://doi.org/10.1051/0004-6361/202142432)

(ref: singh_13) Singh, R., van de Ven, G., Jahnke, K., et al. 2013, A&A, 558, A43, doi: [`10.1051/0004-6361/201322062`](http://doi.org/10.1051/0004-6361/201322062)

(ref: Solomon_92) Solomon, P. M., Downes, D., & Radford, S. J. E. 1992, ApJL, 398, L29, doi: [`10.1086/186569`](http://doi.org/10.1086/186569)

(ref: sorai_12) Sorai, K., Kuno, N., Nishiyama, K., et al. 2012, PASJ, 64, 51, doi: [`10.1093/pasj/64.3.51`](http://doi.org/10.1093/pasj/64.3.51)

(ref: sormani_15b) Sormani, M. C., Binney, J., & Magorrian, J. 2015, MNRAS, 449, 2421, doi: [`10.1093/mnras/stv441`](http://doi.org/10.1093/mnras/stv441)

(ref: sormani_18b) Sormani, M. C., Sobacchi, E., Fragkoudi, F., et al. 2018a, MNRAS, 481, 2, doi: [`10.1093/mnras/sty2246`](http://doi.org/10.1093/mnras/sty2246)

(ref: sormani_18a) Sormani, M. C., Treß, R. G., Ridley, M., et al. 2018b, MNRAS, 475, 2383, doi: [`10.1093/mnras/stx3258`](http://doi.org/10.1093/mnras/stx3258)

(ref: sormani_19) Sormani, M. C., Treß, R. G., Glover, S. C. O., et al. 2019, MNRAS, 488, 4663, doi: [`10.1093/mnras/stz2054`](http://doi.org/10.1093/mnras/stz2054)

(ref: sormani_23) Sormani, M. C., Barnes, A. T., Sun, J., et al. 2023, MNRAS, 523, 2918, doi: [`10.1093/mnras/stad1554`](http://doi.org/10.1093/mnras/stad1554)

(ref: spinoso_17) Spinoso, D., Bonoli, S., Dotti, M., et al. 2017, MNRAS, 465, 3729, doi: [`10.1093/mnras/stw2934`](http://doi.org/10.1093/mnras/stw2934)

(ref: stone_70a) Stone, M. E. 1970, ApJ, 159, 277, doi: [`10.1086/150309`](http://doi.org/10.1086/150309)

(ref: storchi-bergmann_19) Storchi-Bergmann, T., & Schnorr-Müller, A. 2019, Nature Astronomy, 3, 48, doi: [`10.1038/s41550-018-0611-0`](http://doi.org/10.1038/s41550-018-0611-0)

(ref: sun_20) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8, doi: [`10.3847/2041-8213/abb3be`](http://doi.org/10.3847/2041-8213/abb3be)

(ref: tubbs_82) Tubbs, A. D. 1982, ApJ, 255, 458, doi: [`10.1086/159846`](http://doi.org/10.1086/159846)

(ref: Usero_15) Usero, A., Leroy, A. K., Walter, F., et al. 2015, AJ, 150, 115, doi: [`10.1088/0004-6256/150/4/115`](http://doi.org/10.1088/0004-6256/150/4/115)

(ref: veilleux_87) Veilleux, S., & Osterbrock, D. E. 1987, ApJS, 63, 295, doi: [`10.1086/191166`](http://doi.org/10.1086/191166)

(ref: venturi_18) Venturi, G., Nardini, E., Marconi, A., et al. 2018, A&A, 619, A74, doi: [`10.1051/0004-6361/201833668`](http://doi.org/10.1051/0004-6361/201833668)

(ref: verley_07) Verley, S., Combes, F., Verdes-Montenegro, L., Bergond, G., & Leon, S. 2007, A&A, 474, 43, doi: [`10.1051/0004-6361:20077650`](http://doi.org/10.1051/0004-6361:20077650)

(ref: watkins_23) Watkins, E. J., Barnes, A. T., Henny, K., et al. 2023, ApJL, 944, L24, doi: [`10.3847/2041-8213/aca6e4`](http://doi.org/10.3847/2041-8213/aca6e4)

(ref: weiner_01a) Weiner, B. J., Williams, T. B., van Gorkom, J. H., & Sellwood, J. A. 2001, ApJ, 546, 916, doi: [`10.1086/318288`](http://doi.org/10.1086/318288)

(ref: yajima_19) Yajima, Y., Sorai, K., Kuno, N., et al. 2019, PASJ, 71, S13, doi: [`10.1093/pasj/psz022`](http://doi.org/10.1093/pasj/psz022)

(ref: zanmar_sanchez_08) Zánmar Sánchez, R., Sellwood, J. A., Weiner, B. J., & Williams, T. B. 2008, ApJ, 674, 797, doi: [`10.1086/524940`](http://doi.org/10.1086/524940)

(ref: zee_23) Zee, W.-B. G., Paudel, S., Moon, J.-S., & Yoon, S.-J. 2023, ApJ, 949, 91, doi: [`10.3847/1538-4357/acc79a`](http://doi.org/10.3847/1538-4357/acc79a)

(ref: zurita_04) Zurita, A., Relaño, M., Beckman, J. E., & Knapen, J. H. 2004, A&A, 413, 73, doi: [`10.1051/0004-6361:20031049`](http://doi.org/10.1051/0004-6361:20031049)

[^1]: As we do not intend to compare velocity gradients among different galaxies, velocity gradients are not corrected for inclination. The main conclusion we draw from Section  [5](#sec:impact_on_SF) and [6](#sec:impact_on_SF_bpt) do not change when correcting for inclination.

</paper>

Write the methods card for this paper.