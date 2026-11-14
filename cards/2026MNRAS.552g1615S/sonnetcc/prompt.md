# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026MNRAS.552g1615S\sonnetcc\reply.txt

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
 "bibcode": "2026MNRAS.552g1615S",
 "title": "The efficient star-forming regions of stripped-envelope supernovae",
 "year": 2026,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Solar, Martín",
 "n_authors": 16,
 "arxiv_id": "2608.18897",
 "doi": "10.1093/mnras/stag1615",
 "alma_projects_linked_by_archive": [
  "2013.1.00243.S",
  "2013.1.01161.S",
  "2015.1.00902.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00392.S",
  "2017.1.00886.L",
  "2018.1.00272.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.1.01305.S",
  "2021.1.00099.S"
 ]
}
```

Paper text:
<paper>
# The efficient star-forming regions of stripped-envelope supernovae

## Abstract

Massive stars ($\geq8\,\rm{M}_{\odot}$) play a key role in shaping the interstellar medium of galaxies through stellar feedback. However, how these stars form and evolve before exploding as core-collapse supernovae (SNe) remains elusive. We compute for the first time the star-formation efficiencies (SFEs) at the locations of hydrogen-rich (H-rich) SNe and stripped-envelope SNe (SESNe) to constrain their progenitor properties. We used VLT/MUSE and ALMA observations of $\mathrm{H}~\alpha/\mathrm{H}~\beta$ and CO(2–1) emission lines to trace the components of the warm ionised gas and cold molecular gas, respectively.

Both observations resolve individual H ii regions and giant molecular clouds at spatial resolutions on cloud-scales ($\sim 100$ pc). This combined data allows us to compute the SFE from the star formation rate (SFR) and the molecular gas mass ($M_{\rm mol}$) as $\mathrm{SFE}=\mathrm{SFR}/M_{\rm mol}$. We find that SESNe explode in environments that are currently forming stars eight times more efficiently than those of H-rich SNe (higher SFR for SESNe with similar $M_{\rm mol}$).

On one hand, this is consistent with the scenario in which the majority of SESNe are produced from very massive stars ($\geq20~\rm{M}_{\odot}$) if the initial mass function is top-heavy. On the other hand, most of SESN progenitor channels are formed from interacting binaries ($\leq20~\rm{M}_{\odot}$) if an increased binary system formation rate is connected with turbulences and, in turn, with the boost to SFE. Then, an increased binary fraction could explain the enhanced H $\alpha$ luminosities.

In summary, SESNe preferentially occur in regions of intense, efficient star formation rather than simply higher gas content.

galaxies: ISM – ISM: HII regions – ISM: molecules – methods: observational – stars: massive – supernovae: general

# Introduction

Core-collapse supernovae (CCSNe) are explosions of stars within initial masses higher than $8~\rm{M}_{\odot}$ (hereafter massive stars). Understanding these explosions is important because they shape the interstellar medium (ISM) through different mechanisms. For instance, CCSNe synthesise metals and dust, inject momentum causing both positive and negative feedback on star formation, generate cosmic rays at evolved stages, and produce neutrinos (cite: 2017Branch). As massive stars are not static objects, they have a complex formation and evolutionary phase, leading to different types of CCSNe (cite: 2019Modjaz; 2025Gilkis; 2026Souropanis). Therefore, it is necessary to constrain the properties of CCSN progenitors to predict how they explode.

Historically, supernovae (SNe) were classified as Type I and Type II based on their spectral features at the time of maximum optical light (cite: 1941Minkowski). In particular, CCSNe are classified as follows: Type II SNe are hydrogen-rich (H-rich), whereas stripped-envelope SNe (SESNe) lack hydrogen and silicon features. SESNe are further subdivided into several subclasses: Type Ib SNe show no hydrogen lines; Type IIb SNe initially resemble Type II SNe shortly after explosion, but after several weeks their spectra evolve to resemble those of Type Ib; and Type Ic SNe exhibit neither hydrogen nor helium lines (cite: 1997Filippenko; 2017GalYam). Ideally, the classification of CCSNe should be linked to the nature of their progenitor stars, however, the observational classification alone does not provide a complete physical interpretation of their origin.

One powerful technique that enables one to constrain SN progenitors is the statistical study of their environments (cite: 2015Anderson). This approach has been used across ultraviolet (cite: 2006Fruchter; 2013Kangas; 2023bSun), optical (cite: 2011Leloudas; 2013Kuncarayakti; 2013Lyman; 2017Kangas; 2018Kuncarayakti; 2014Hakobyan; 2016Galbany; 2023Pessi; 2024Thone; 2025Ganss), submillimetre (cite: 2017Galbany), and radio (cite: 2015Michalowski; 2018bMichalowski; 2020Michalowski; 2020bMichalowski; 2015Arabsalmani; 2022Arabsalmani; 2024deUgartePostigo; 2026Slaus) observations. However, these previous studies were limited to small samples, observations at galactic-scale spatial resolutions ($> 1~\mathrm{kpc}$) or integrated observations of entire galaxies. To constrain the SN progenitor channels, it is essential to resolve the stellar populations or gas properties at the explosion sites. Although SNe themselves and galaxy-averaged host properties have been studied extensively (cite: 2008Hakobyan; 2009Boissier; 2010Arcavi; 2012Kelly; 2024Jones; 2024Qin; 2024Pritchet; 2026Nugent), higher-resolution observations are necessary to understand the nature of SNe. Cloud-scale observations (cite: 2016Leroy) do not resolve individually star-forming regions (cite: 2003Oey) or giant molecular clouds (cite: 2017MivilleDeschenes), but these spatial scales recover their general trends (cite: 2024Schinnerer). The resolution comparable to typical sizes of H ii regions and GMCs is beneficial as CCSN progenitors should be associated with the ionised gas and their parent molecular clouds at the moment of the explosions.

The advent of integral field unit (cite: 2012Sanchez; 2015Bundy) spectrographs revolutionised studies of SN environments. Specifically, the Multi Unit Spectroscopic Explorer (MUSE) at the Very Large Telescope (cite: 2010Bacon) is able to physically resolve the warm ionised gas (typically $10^4$ K) conditions (e.g., star formation rate, metallicity, dust extinction, etc.) at explosion sites and infer the ISM properties in which progenitor stars were born. For example, the optical range includes Balmer series emission lines, making it possible to trace the warm ionised gas. Since the most massive stars are responsible for ionising the surrounding gas, the typical lifetimes of H ii regions are comparable to the explosion delay time of these massive stars (cite: 2010Goddard; 2021Torniamenti; 2022Chevance; 2026Wainer). From optical environmental studies using VLT/MUSE, SESN locations have been associated with regions of higher star formation rates (SFRs) than those of H-rich SNe (cite: 2018Kuncarayakti; 2023Pessi; 2024MaykerChen). Thus, SESNe may be associated with younger and more massive star-forming regions, implying progenitors more massive than those of H-rich SNe. However, all these studies solely used Balmer lines as a proxy to derive the properties of SN progenitors. Balmer lines only trace recent star formation, and a more promising approach is to include multiwavelength observations of the ISM.

(cite: 2017Galbany) served as a benchmark study of cold molecular hydrogen gas ($\sim$10–30 K; hereafter molecular gas) mass ($M_{\mathrm{mol}}$) reservoirs (at $\sim$ $1.5$ kpc spatial scales) at the SN explosion sites. Later, using Atacama Large Millimeter/submillimeter Array (ALMA) data at cloud-scale spatial resolutions, (cite: 2023MaykerChen) explored molecular gas at SN locations and found modest differences between H-rich SNe and SESNe. Following a similar approach, (cite: 2024Solar) used a larger CCSN sample and found that H-rich SNe and SESNe share similar molecular-gas environmental properties. Combining both approaches (VLT/MUSE + ALMA) makes it possible to compute the star formation efficiency (SFE) from the ratio of the star formation rate to the amount of molecular gas ($\mathrm{SFE} \equiv \mathrm{SFR}/M_{\rm mol}$, or the molecular gas depletion time $\tau_{\rm{dep}}\equiv\mathrm{SFE}^{-1}$). This estimator indicates how effectively a GMC converts its molecular gas into stars.

Previous works have already analysed star formation rate and molecular gas properties of host galaxies of various transients. Examples of such transients include long-duration ($>2$ s) Gamma-Ray Bursts (GRBs; (cite: 2014Hatsukade; 2020aHatsukade; 2015aStanway; 2015bStanway; 2016Michalowski; 2018aMichalowski; 2019Hashimoto; 2020Arabsalmani; 2020deUgartePostigo; 2024deUgartePostigo; 2021Chen); (cite: 2023Nadolny; 2024Thone)), short-duration ($<2$ s) GRBs (cite: 2021NicuesaGuelbenzu), and super-luminous SNe (cite: 2019Arabsalmani; 2020bHatsukade). For CCSNe, detailed host-galaxy features have been studied in small samples (cite: 2018bMichalowski; 2020Michalowski). However, there has been a lack of statistical studies on SFE measurements. In this Paper, we measure for the first time the SFE at the locations of recent CCSN explosions ($< 100$ yr) using a statistical sample, resolved at cloud scales. For this purpose, we combine VLT/MUSE and ALMA data to measure warm ionised gas and molecular gas, respectively. We use a flat $\Lambda$-CDM cosmological model with $H_{0} = 69$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\Lambda} = 0.71$, and $\Omega_{m} = 0.29$ (cite: 2015Schneider).

# Method

## Sample Selection

Only CCSNe are included in the sample; thermonuclear SNe (or Type Ia SNe) were removed. This is because thermonuclear SNe have different explosion mechanisms and progenitor systems, with longer delay times ($> 100$ Myr), which prevents direct comparison with CCSN progenitor channels at the explosion sites (cite: 2015bAnderson). The CCSN sample was collected from different databases (cite: 1989Barbon; 1993Tsvetkov; 1998Rutledge; 1999Barbon; 2004Tsetkov; 2012Lennarz; 2017Guillochon). The CCSNe were divided into the following classification groups: Type II, IIP, and IIn as H-rich SNe and Type Ib, IIb, Ib/c, Ic, Ic-pec, and Ic-BL as SESNe.

To constrain CCSN progenitors through the SFE of their environments, both measurements of star formation and molecular gas are required. The spectral lines of the Balmer series for hydrogen-alpha ($\mathrm{H}~\alpha$; at $6562.79~\mathrm{\mathring{A}}$) and hydrogen-beta ($\mathrm{H}~\beta$; at $4861.35~\mathrm{\mathring{A}}$), and carbon monoxide (CO) using the $J = 2\rightarrow1$ rotational transition (hereafter CO\[2–1\], at $230.54~\mathrm{GHz}$) trace the properties of the star-forming regions and molecular gas, respectively. We selected available observations from both VLT/MUSE and ALMA at spatial resolutions of $\sim$ $100$ pc for host galaxies of known CCSNe in the southern hemisphere. The instrumental limitations constrained the distances of the sources at $<80$ Mpc (redshift $z<0.018$). Also, to avoid strong projection effects, we used face-on galaxies with low inclination angles (cite: 2014Makarov; 2020Lang).

In this Paper, we made use of the following dataset (see Section [2.2](#sec:subsec2) for data description): the Physics at High Angular resolution in Nearby GalaxieS[^3] (PHANGS) survey (cite: 2021Leroy_a; 2021Leroy_b; 2022Emsellem), the All-weather MUse Supernova Integral-field Nearby Galaxies (AMUSING) survey (cite: 2016Galbany; 2020LopezCoba), the ALMA CO SN (ACOS) survey (cite: 2024Solar), our own VLT/MUSE observations (114.27G5.001: PI M. Solar), and ALMA archival data[^4].

The PHANGS sample comprises 90 nearby galaxies ($<20$ Mpc), of which all were observed by ALMA and 19 by both ALMA and VLT/MUSE. In these 19 PHANGS-ALMA-VLT/MUSE galaxies, 25 CCSN explosions[^5] have been discovered in 10 host galaxies[^6]. In addition, the AMUSING survey collects VLT/MUSE host galaxy observations at the location of around 1000 SNe. Data from AMUSING and ALMA archive result in eight CCSNe[^7] exploding in seven host galaxies[^8].

Finally, we used supernovae from the ACOS survey and followed up with our own VLT/MUSE observations. We selected follow-up observations based on the data quality of the ACOS survey (i.e., it is possible to distinguish background noise from the physical signal). This resulted in eight CCSNe[^9] from eight host galaxies[^10]. One ACOS source had previous AMUSING data (SN 2009bb in NGC 3278; (cite: 2018bMichalowski)). The sample consists of 42 SNe in 26 host galaxies. The number of H-rich SNe and SESNe resulted in 22 and 20, respectively.

## Data Description

The PHANGS is a survey aimed at studying the cloud-scale structure of spiral, star-forming, main-sequence galaxies using multiwavelength observations. PHANGS observations covers full galaxy extension in H $\alpha$, H $\beta$, and CO(2–1).

We refer to (cite: 2021Pessa) for a description of how the maps were computed. For observations not covered by PHANGS, we followed a similar approach for archival data in order to use as homogenous datasets as possible. This subsection describes the archival data, first for VLT/MUSE and later for ALMA.

MUSE (cite: 2010Bacon) is a second generation instrument located at the Nasmyth focus of UT4 at the VLT at the Paranal Observatory of the European Southern Observatory (ESO). The VLT/MUSE field of view comprises 24 IFU modules. Each of these IFU channels contains 48 slices that disperse the light to create a 3D data cube. Specifically, we used the Wide Field Mode with natural seeing, which covers a field of view of $1.0\ensuremath{'} \times 1.0\ensuremath{'}$, a spatial sampling of $0.2\ensuremath{''} \times 0.2\ensuremath{''}$, a spatial resolution of $0.4\ensuremath{''}$ at 700 nm, a wavelength range 465–930 nm, a mean resolution of 3000, and a resolving power of 2000 at 460 nm and 4000 at 930 nm. VLT/MUSE spectral data was collected from the AMUSING survey (from the specific program 095.D-0172: PI H. Kuncarayakti) and our own observations, and the execution time per target ranged from 1 to 2 h. Observations from 095.D-0172 were performed during 2015 May. Observations from 114.27G5.001 were performed from 2024 November to 2025 March (aimed to follow up the ACOS observations, described in the following paragraph). The VLT/MUSE data was reduced using the ESO Reflex MUSE pipeline (cite: 2020Weilbacher). All data are publicly available.

ALMA observes at the submillimetre and millimetre wavelengths. It is composed of 66 antennas (54 of 12-meter diameter and 12 of 7-meter diameter). For ALMA, we made use of data that covered the CO(2–1) line at resolutions of $100$ pc, observable at its Band 6 (cite: 2004Ediss; 2009Wootten). For the case of ACOS, the sensitivity was set to a root mean square of 100 mK and a bandwidth of 2.049 km s$^{-1}$ (1.6 MHz) per 50 pc beam. The observations are centred at the SESN position to gain the best signal-to-noise ratio. The observed integration time ranged from 0.3 to 3.6 h, and requested angular resolutions of $0.5\ensuremath{''}$ to $1.1\ensuremath{''}$. The sensitivity to the large-scale structures (on kiloparsec scales) is not required for the detection of marginally-resolved sources. The dual polarisation mode was used to obtain the best possible sensitivity. Observations from 2021.1.00099.S were made from 2022 January to 2022 May.

For ALMA archival data[^11], angular resolutions ranged from $0.22\ensuremath{''}$ to $5.77\ensuremath{''}$, able to spatially resolve cloud-scale observations. The ALMA data was reduced and analysed using the Common Astronomy Software Applications (cite: 2022CASATeam). All data are publicly available.

## Star Formation Efficiency at Core-collapse Supernova Explosion Sites

The main goal of this Paper is to analyse the local ISM conditions through the SFE for CCSNe. This parameter is calculated from the ratio of the surface densities of SFR ($\Sigma_{\rm{SFR}}$) and M$_{\mathrm{mol}}$ ($\Sigma_{\rm{mol}}$). VLT/MUSE data was corrected for foreground Galactic extinction using the NASA/IPAC Infrared Science Archive[^12] (cite: 2011Schlafly). To calculate the SFR from H $\alpha$ and H $\beta$, we first subtracted the optical continuum. For each spectrum, we fitted the best stellar continuum with `STARLIGHT` (cite: 2005CidFernandes) and subtracted it from the observed spectrum to obtain a pure gas-phase emission spectrum. The integrated area under the Gaussian profile fitted to the respective emission lines gave us an estimate of the flux.

The SFR measured from hydrogen recombination cascades is sensitive to the effects of dust (cite: 1998Kennicutt). To correct for dust, a nebula is assumed to be optically thick to ionising photons, using the known line-intensity ratio of H $\alpha$ and H $\beta$ of 2.86, as dictated by quantum mechanics (cite: 2006Osterbrock). For this a Case B recombination is assumed, in which the electron temperature ($T_{e}$) is $T_{e}=10\,000~\rm{K}$ and the electron density ($n_{e}$) is $n_{e}=100~\rm{cm}^{-3}$ (standard for star-forming galaxies). Applying the (cite: 1994ODonnell) extinction law (with the extinction coefficients $\rm{k}_{\alpha}=2.52$ and $\rm{k}_{\beta}=3.66$), it is possible to derive the total visual extinction ($A_{V}$). This approach works reasonably well for local star-forming galaxies, resulting in a range of $A_{V}=$1–2$~\rm{mag}$ (cite: 1983Kennicutt; 1998Kennicutt; 2009Kennicutt).

To compute $\Sigma_{\mathrm{SFR}}$ from the luminosity of H $\alpha$ corrected for internal extinction ($L_{\mathrm{H~\alpha,cor}}$), we follow the (cite: 2013Calzetti) prescription as

$$\begin{equation}
\label{eq:eq1}
    \Sigma_{\mathrm{SFR}} = 5.5 \times 10^{-42}\,L_{\mathrm{H~\alpha,cor}}\,\cos i,
\end{equation}$$

where the factor $5.5 \times 10^{-42}$ is in units of $\frac{\mathrm{M}_{\odot}\,\mathrm{yr}^{-1}}{\mathrm{erg}\,\mathrm{s}^{-1}}$ and the H $\alpha$-SFR conversion uses a (cite: 2001Kroupa) initial mass function (IMF).

ALMA observations of CO(2–1) are used to trace the molecular gas, at millimetre wavelengths unaffected by dust extinction. To calculate $\Sigma_{\rm{mol}}$, we follow the (cite: 2024Schinnerer) prescription, which accounts for the fraction of the CO-dark molecular gas, the emissivity, and the opacity of CO-emitting regions as

$$\begin{equation}
\label{eq:eq2}
    \Sigma_{\mathrm{mol}} = \alpha_{\mathrm{CO,MW}}^{1-0}\,\left( Z / Z_{\odot}\right)^{-1.5}\,R_{21}^{-1}\,I_{\mathrm{CO(2-1)}} \cos i,
\end{equation}$$

where $\alpha_{\mathrm{CO,MW}}^{1-0}=4.35~\mathrm{M}_{\odot}~\left( \mathrm{K}\,\mathrm{km}\,\mathrm{s}^{-1}\,\mathrm{pc}^{2} \right) ^{-1}$ is the CO-to-H$_{2}$ conversion factor assuming a Milky Way calibration (cite: 2013Bolatto), $Z$ is the metallicity, $R_{21}=0.65\times\frac{\Sigma_{\mathrm{SFR}}}{1.8\times10^{-2}}~\left( \mathrm{M_{\odot}}\,\mathrm{yr}^{-1}\,\mathrm{kpc}^{-2} \right)^{-1}$ is the CO(2–1)-to-CO(1–0) line ratio as a function of $\Sigma_{\rm SFR}$ from local ISM conditions (cite: 2025denBrok), and $I_{\mathrm{CO(2-1)}}$ is the line-integrated CO(2–1) intensity in units of K km s$^{-1}$. The metallicity $Z$ is converted from the oxygen-abundances in the nebular regions (Appendix [6](#app:app1)). In cases of non-detections of molecular gas surface density (for $\Sigma_{\rm{mol}}<2\sigma$), $2\sigma$ upper limits were used.

For CCSNe, we extracted the environmental parameters using the coarsest resolution available from VLT/MUSE and ALMA. If VLT/MUSE had the coarsest resolution, ALMA data were convolved with a Gaussian with the VLT/MUSE full width at half maximum. Otherwise, VLT/MUSE observations were smoothed to the ALMA beam shape (with the respective major and minor axes). SFE (or $\tau_{\mathrm{dep}}$) is computed as the ratio of $\Sigma_{\rm{SFR}}$ and $\Sigma_{\rm{mol}}$ as

$$\begin{equation}
\label{eq:eq3}
    \mathrm{SFE}= \tau_{\mathrm{dep}}^{-1}=\Sigma_{\rm{SFR}}/\Sigma_{\rm{mol}}.
\end{equation}$$

The SFE is defined as the rate at which available molecular gas mass is converted into stars. However, gas in these regions can be ionised due to various sources. Examples of these sources are active galactic nucleus (AGNs) and massive stars. Therefore, to select regions of star formation where the gas is primarily excited by massive stars, we performed an emission-line diagnostic. These regions are identified using the so-called Baldwin, Phillips & Terlevich (BPT) diagram (cite: 1981Baldwin), as detailed in Fig. [3](#fig:figA1) (Appendix [7](#app:app2)). Since regions within galaxies can be ionised due to AGNs, increasing the observed value of H $\alpha$, we removed 20 per cent of AGN-dominated galaxy pixels to obtain a clean sample. Similarly, we removed two CCSNe (SN 2019ehk in NGC 4321 and SN 2023dpj in NGC 5135). Their host galaxies contain AGNs (cite: 2005GarciaBurillo; 2018Sabatini), and their galactocentric distances are 1.8 and 1.1 kpc, respectively. After this correction, the final sample is 21 H-rich SNe and 19 SESNe, exploding in 25 host galaxies.

To compare these measurements with the properties of the host galaxies, we also repeated the procedure for random PHANGS pixels. To give each galaxy a similar statistical weight, we randomly selected 10 000 pixels per galaxy. This gives us a reference estimate of the PHANGS’s average properties of H ii regions within galaxies (hereafter referred to as host galaxies).

# Results

The star-formation law (cite: 1959Schmidt; 1998Kennicutt) is an empirical relation of SFR and gas density within galaxies. Figure [1](#fig:fig1) presents the star-formation law (only for molecular gas content) for the locations of our CCSNe. At the explosion sites of all CCSNe, H $\alpha$ emission was detected in the VLT/MUSE observations. CO(2–1) was detected at the positions of 23 CCSNe (12 H-rich SNe and 11 SESNe), and 17 were not detected (9 H-rich SNe and 8 SESNe). We also include the pixel distributions of host galaxies as a comparison sample ($\sim$ 20 per cent of CO host pixels are non-detections). The constant SFE relations ($\tau_{\mathrm{dep}}$) are shown for $10~\mathrm{Gyr}^{-1}$ ($0.1~\mathrm{Gyr}$), $1~\mathrm{Gyr}^{-1}$ ($1~\mathrm{Gyr}$), and $0.1~\mathrm{Gyr}^{-1}$ ($10~\mathrm{Gyr}$). This figure shows that H-rich SNe lie closer to the lower-SFE (longer depletion times) values, while SESNe lie closer to the higher-SFE (shorter depletion times) values.

![](Fig1.pdf)

Figure [2](#fig:fig2) shows empirical cumulative distribution functions (eCDFs) for CCSNe and host galaxies in star formation rate, molecular gas mass, and star formation efficiency. Their 1$\sigma$ confidence intervals (computed using 1000 Monte Carlo simulations) are shown in Table [\[tab:tab1\]](#tab:tab1). To test whether distributions differ significantly (p-value $< 0.05$), Table [\[tab:tab2\]](#tab:tab2) reports two-sample Kolmogorov–Smirnov (KS) and Anderson–Darling (AD) tests. A summary of the properties of the host-galaxy and the results derived is provided in Table [\[tab:tabC1\]](#tab:tabC1) and Table [\[tab:tabC2\]](#tab:tabC2) (Appendix [8](#app:app3)), respectively. Our results are also available in the online Supplementary Material.

![](Fig2.pdf)

| Parameter | $\log \left( \Sigma_{\rm{SFR}} \, / \,  \mathrm{M}_{\odot}\,\mathrm{yr}^{-1}\,\mathrm{kpc}^{-2}  \right)$ | $\log  \left( \Sigma_{\rm{mol}} \, / \,   \mathrm{M}_{\odot}\,\mathrm{kpc}^{-2}  \right)$ | $\log \left( \rm{SFE} \, / \, \mathrm{Gyr}^{-1}  \right)$ |
|:---|:--:|:--:|:--:|
| Host galaxies | $-2.8227^{+0.0002}_{-0.0002}$ | $6.86150^{+0.00003}_{-0.00001}$ | $-1.0954^{+0.0003}_{-0.0003}$ |
| H-rich SNe | $-2.09^{+0.01}_{-0.01}$ | $7.7^{+0.1}_{-0.1}$ | $-0.74^{+0.09}_{-0.08}$ |
| SESNe | $-1.26^{+0.01}_{-0.01}$ | $7.6^{+0.1}_{-0.1}$ | $0.18^{+0.06}_{-0.10}$ |

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Two-sample test | KS statistic | KS p-value | AD statistic | AD p-value | Null hypothesis rejected? |
|  |  |  |  |  | (p-value $<0.05$) |
| $\Sigma_{\rm{SFR}}  \rightarrow$ Host galaxies    vs. H-rich SNe | 0.4 | $6 \times 10^{-4}$ | 10 | $8 \times 10^{-6}$ | **Yes** |
| $\Sigma_{\rm{SFR}}  \rightarrow$ Host galaxies    vs. SESNe | 0.8 | $1 \times 10^{-10}$ | 40 | $9 \times 10^{-20}$ | **Yes** |
| $\Sigma_{\rm{SFR}}  \rightarrow$ H-rich SNe vs. SESNe | 0.5 | $1 \times 10^{-2}$ | 6 | $1 \times 10^{-3}$ | **Yes** |
| $\Sigma_{\rm{mol}}\,\rightarrow$ Host galaxies    vs. H-rich SNe | 0.5 | $5 \times 10^{-4}$ | 10 | $2 \times 10^{-5}$ | **Yes** |
| $\Sigma_{\rm{mol}}\,\rightarrow$ Host galaxies    vs. SESNe | 0.4 | $7 \times 10^{-3}$ | 4 | $8 \times 10^{-3}$ | **Yes** |
| $\Sigma_{\rm{mol}}\,\rightarrow$ H-rich SNe vs. SESNe | 0.3 | $5 \times 10^{-1}$ | 1 | $3 \times 10^{-1}$ | No |
| $\mathrm{SFE}\,\,   \rightarrow$ Host galaxies    vs. H-rich SNe | 0.3 | $4 \times 10^{-2}$ | 3 | $2 \times 10^{-2}$ | **Yes** |
| $\mathrm{SFE}\,\,   \rightarrow$ Host galaxies    vs. SESNe | 0.7 | $6 \times 10^{-8}$ | 40 | $8 \times 10^{-20}$ | **Yes** |
| $\mathrm{SFE}\,\,   \rightarrow$ H-rich SNe vs. SESNe | 0.7 | $1 \times 10^{-4}$ | 7 | $2 \times 10^{-4}$ | **Yes** |

For the measured star formation rate density (in units of $\mathrm{M}_{\odot}\,\mathrm{yr}^{-1}\,\mathrm{kpc}^{-2}$), we find a clear increasing trend from: host galaxy pixels ($\log \Sigma_{\mathrm{SFR}} = -2.8227^{+0.0002}_{-0.0002}$), to H-rich SNe ($\log \Sigma_{\mathrm{SFR}} = -2.09^{+0.01}_{-0.01}$), and SESNe ($\log \Sigma_{\mathrm{SFR}} = -1.26^{+0.01}_{-0.01}$). This is also supported by the two-sample tests of KS and AD as the p-values are significantly lower than 0.05, so the null hypothesis is rejected and the distributions are drawn from different parent populations. In summary, SESNe preferentially explode in regions of higher SFR than H-rich SNe, and both CCSN types lie above the host-galaxy baseline.

For the computed molecular gas surface density (in units of $\mathrm{M}_{\odot}\,\mathrm{kpc}^{-2}$), a similar analysis yields different results. Both CCSN classes occur in regions with higher molecular-gas surface density ($\log \Sigma_{\mathrm{mol}}= 7.7^{+0.1}_{-0.1}$ for H-rich SNe and $\log \Sigma_{\mathrm{mol}} = 7.6^{+0.1}_{-0.1}$ for SESNe) than the sample of host galaxy pixels ($\log \Sigma_{\mathrm{mol}} = 6.86150^{+0.00003}_{-0.00001}$. The $\Sigma_{\mathrm{mol}}$ in the environments of H-rich SNe and SESNe are consistent within uncertainties. This is also supported by the high KS and AD p-values (0.5 and 0.3, respectively). This indicates that the observed difference between H-rich SNe and SESNe is not statistically significant, so the null hypothesis cannot be rejected. On the other hand, a significant difference is found when $\Sigma_{\mathrm{mol}}$ in the environments of both CCSNe are compared with the host galaxy pixels. This is also confirmed by low p-values for the two-sample tests of KS and AD, comparing the host galaxies with H-rich SNe (KS $\mathrm{p}$-$\mathrm{value}$$\,\sim$ $5\times10^{-4}$ and AD $\mathrm{p}$-$\mathrm{value}$$\,\sim$ $2\times10^{-5}$) and SESNe ($\sim$ $7\times10^{-3}$ and $\sim$ $8\times10^{-3}$). Altogether, both CCSNe explode in regions with similar molecular gas surface densities, but at densities higher than the host galaxy average.

When the SFE is analysed, a similar trend is found compared to the results of SFR. The SFE values (in units of Gyr$^{-1}$) are as follows: host galaxy pixels ($\log \rm{SFE}=-1.0954^{+0.0003}_{-0.0003}$) $<$ H-rich SNe ($\log \rm{SFE}=-0.74^{+0.09}_{-0.08}$) $<$ SESNe ($\log \rm{SFE}=0.18^{+0.06}_{-0.10}$). The distributions of host galaxies with H-rich SNe give p-values of $0.04$ for KS and $0.02$ for AD, respectively. Also, for SFE of host galaxies and SESNe, the p-values are $6\times10^{-8}$ for KS and $8\times10^{-20}$ for AD, respectively. A clear difference in star formation efficiency values is also found when comparing H-rich SNe and SESNe. This is supported by the low p-values of $1\times10^{-4}$ and $2\times10^{-4}$ for KS and AD, respectively. Although we work with values of $\Sigma_{\mathrm{mol}}$ corrected by $12\,+\, \left( \mathrm{O}/\mathrm{H} \right)$, our trends do not change whether this metallicity is taken into account or not.

# Discussion

First, the main outcome of this work is that SFE values increase in the following order: host galaxies $\rightarrow$ H-rich SNe $\rightarrow$ SESNe. Second, the SFR trends are consistent with previous studies, with higher values for SESNe than for H-rich SNe (cite: 2008Anderson; 2012Anderson; 2013Crowther; 2014Galbany; 2018Galbany; 2018Kuncarayakti; 2023Pessi), and both CCSN types being above the host-galaxy average (cite: 2024MaykerChen). Third, our molecular gas values show trends similar to (cite: 2024Solar) –

$\mathrm{host}$ $\mathrm{galaxies} < \mathrm{H}$-$\mathrm{rich}$ $\mathrm{SNe}$ $\sim$ $\mathrm{SESNe}$ – but different from (cite: 2017Galbany) and (cite: 2023MaykerChen) – $\mathrm{H}$-$\mathrm{rich}$ $\mathrm{SNe} < \mathrm{SESNe}$.

In summary, we find similar $\Sigma_{\mathrm{mol}}$ environments for SESNe and H-rich SNe, but higher $\Sigma_{\mathrm{SFR}}$ for the former. There is roughly an order-of-magnitude ($\times 8$) difference in SFE values between SESNe and H-rich SNe. This can be explained by two progenitor scenarios of high-mass stars ($\geq 8~\mathrm{M}_{\odot}$) for SESNe, both differing from the H-rich SNe: very massive stars (cite: 1993Woosley) or binary systems (cite: 1992Podsiadlowski). For the very-massive-star case, the outer layers are removed due to strong mass-loss (given the high initial stellar mass).

We show below that this could be consistent with the data if the IMF in these regions is top-heavy. For the latter case, a companion is responsible for stripping away the envelope, and this mechanism is more effective at lower initial masses than for very massive stars. This can explain our data because, as we discuss below, higher binarity fraction (possibly boosted by increased turbulence) implies higher H $\alpha$ luminosity.

## Very Massive Stars

The H $\alpha$ emission is expected to be linked to massive stars (cite: 2012Kennicutt). This is because the most massive stars are responsible for ionising the surrounding gas medium through intense UV radiation. We find that the SFR at the explosion sites of both CCSN populations are higher compared to the sample of all host-galaxy pixels. Many of the galaxy pixels are not related to young and intense star-forming regions, therefore the host galaxy distribution will be shifted towards a lower SFR.

Here we shed light on the outcome that SESNe explode in regions of higher SFR than those of H-rich SNe, implying a possible difference in their progenitor properties. For instance, SESN progenitors could be more massive than H-rich SNe, and therefore their lifetimes are shorter, which explains higher SFRs (cite: 2026Xi). In other words, the explosion delay time after the formations of progenitors of more massive stars is shorter, so their parents clouds should have a high SFR, whereas for lower-mass stars at the time of the explosion the SFR has already decreased.

In the very-massive-star scenario, SESNe are associated with higher-SFR regions because they host higher numbers of such stars.

For a fixed amount of molecular gas, this could produce a higher flux of H $\alpha$ per unit of gas.

Because higher star formation rates correspond to younger, short-lived stellar populations, they can also increase the number of single-star SN progenitors.

However, once molecular-gas densities at their positions are included through this multiwavelength approach, a different interpretation of CCSN progenitors emerges, as we present in what follows. The amount of gas present at the time of the explosion dissipate over time due to feedback from young stars (cite: 1978Spitzer). In other words, the molecular gas mass at the CCSN positions can be used as an indicator of their progenitor lifetimes (cite: 2024Solar). More massive stars (associated with higher H $\alpha$ emission) would be expected to explode in the densest regions of the molecular gas. However, this is inconsistent with the fact that we observe similar values of molecular gas surface density at the locations of SESNe and H-rich SNe which implies that their progenitor lifetimes and therefore initial masses are similar (cite: 1992Schaller).

The higher SFE at the locations of SESNe than for H-rich SNe but similar molecular gas densities could alternatively be explained by variations in the IMF. SESN progenitors could be preferentially formed in top-heavy IMF regions (cite: 2018Schneider). This means that the regions hosting SESNe can be similar to those hosting H-rich SNe with regards to all properties, but the number of very massive stars for the former. This would leave the molecular gas distribution similar for both types of CCSNe, but those hosting SESNe would have higher H $\alpha$ luminosities due to higher number of very massive stars. This is consistent with our measurements.

## Binary Systems

We also suggest another scenario for the progenitor channels of SESNe in which they arise from binary systems.

This is then consistent with similar molecular gas masses at their positions and at those of H-rich SNe, because the binary systems are expected to have lifetimes similar to those of H-rich SN progenitors.

Growing evidence supports the binary model for SESNe, such as simulations of helium stars (cite: 2020Dessart), emission-line diagnostics of stellar populations (cite: 2019Xiao), periodic undulations evidenced from a bound compact remnant (cite: 2023Moore; 2024Chen; 2026Cartier), high relative rate of SESNe and H-rich SNe (cite: 2011Smith; 2017Shivvers), direct detections of binary companions at the SN site (cite: 2004Maund; 2015Maund; 2022Fox; 2026Zapartas), using molecular gas as tracer of progenitor lifetimes (cite: 2024Solar), and low ejecta masses (cite: 2011Drout; 2016Modjaz). Lightcurve studies also suggest this with modelling (cite: 2016Lyman; 2021Barbarino) and early-excess lightcurve characteristics (cite: 2024Das; 2025Ayala; 2025Chiba). Moreover, there is a lack of evidence for Wolf-Rayet stars (or luminous progenitors) for most of SESNe (cite: 2013Eldridge; 2015Smartt): difficulty to detect massive stars as progenitors (cite: 2012Yoon; 2013Cao; 2018Kilpatrick; 2018VanDyk) and failed explosions (cite: 2011OConnor; 2016Ertl; 2020Patton; 2021bZapartas).

It is essential to include binary evolution when modelling synthetic stellar spectra in galaxies. Specifically, when binary star models are included, they boost the ionisation of He II (at $1640~\mathrm{\mathring{A}}$) emission lines (cite: 2012Eldridge; 2017Eldridge), cosmic reionisation of hydrogen (cite: 2020Gotber), H ii regions (cite: 2025CournoyerCloutier), and a number of young, metal-poor, actively star-forming galaxies (cite: 2024Lecroq). Similarly, younger open clusters tend to exhibit a higher binary fraction than older counterparts (cite: 2025Alexander), consistent with more recent star formation and higher H $\alpha$ emission. In summary, pre-SN feedback from binary stars (mechanical or radiative) enhances the overall ionising radiation from young stellar populations. These effects may explain why SESNe are located in regions with higher H $\alpha$ luminosities that those for H-rich SNe, despite having similar molecular gas properties.

Concentrating now on the H-rich SNe, their progenitors arise from high-mass stars, and our results for $\Sigma_{\mathrm{SFR}}$ and $\Sigma_{\mathrm{mol}}$ are consistent with this interpretation when compared to random pixels from the host galaxies (both with six times higher values than typical pixels). This is also consistent with the SFE being around two times greater for H-rich SNe than for host galaxies. Given this difference in SFE, there is a clear trend for progenitor channels of H-rich SNe to be associated with high-mass stars. H-rich SNe are also expected to be produced by a significant fraction of binary systems ($\sim$ $30$–$50$ per cent), mostly from mass accretion or merging processes (cite: 2019Zapartas). The binary progenitors of H-rich SNe explode later than the red supergiants from single stars of the same final luminosity (cite: 2021aZapartas).

Theoretically, this prolonged delay-time can even exceed the lifetime of all single star CCSN progenitors, going into the regime of 50–200 Myr, when all single stars have already exploded (cite: 2017Zapartas). However, the more pronounced difference in SFE values for SESNe and host galaxies (around 20 times greater) could reflect more extreme conditions of their progenitors. This may imply that more efficient star-forming regions enhance the production of interacting binaries and the multiplicity fraction.

The related interpretation is that regions hosting SESNe are preferentially those above the Kennicutt–Schmidt scaling relation with higher $\Sigma_{\mathrm{SFR}}$ for their $\Sigma_{\mathrm{mol}}$ have increased binary fraction, possibly due to turbulences. GMCs are short-lived structures ($\sim$10–30 Myr) where star formation proceeds fast and inefficiently since only a small fraction of the molecular gas is converted into stars (cite: 2017Semenov; 2019Kruijssen; 2020Chevance; 2022Kim). The GMCs that lie above the scatter of the star-forming scaling relation represent regions with an unusually high SFR for their given $M_{\rm mol}$ (boosted SFE and shortened $\tau_{\rm dep}$). One physical reason for the scatter comes from the supersonic, kinetic (non-thermal) molecular gas turbulence. Turbulence plays a dual role in star formation: supports molecular clouds against global gravitational collapse (low SFE) and creates shock waves that compress gas locally, forming dense filaments and clumps, which are the seeds for new stars (high SFE). CCSNe (H-rich SNe and SESNe) are found in turbulent GMCs (cite: 2026Solar), suggesting that their progenitors have increased formation in high densities and/or are associated with a binary nature. Similarly, the binarity fraction increases with the initial stellar mass (cite: 2017Moe; 2023Offner), which is also directly related to the SFR.

We do not rule out bimodal distribution of the mechanisms responsible for removing the outer layers of SESNe. Moreover, SESN progenitors could arise from a population with slightly higher initial masses than H-rich SN progenitors and also a higher binarity fraction (with a higher incidence of interacting systems).

## Caveats

Using a median redshift of $z=0.0149$ (distance $\sim$ $60$ Mpc), (cite: 2025Pessi) find volumetric fractions of all CCSNe of $\sim$ $60$ and $\sim$ $30$ per cent for H-rich SNe and SESNe (cite: 2026Ercolino), respectively. Also, from this work, the specific (per unit stellar mass) CCSN rate increases for galaxies with lower stellar mass. In our case, the ratio is different, as we have 21 H-rich SNe and 19 SESNe, and the sample is composed only of massive host galaxies ($\sim$ $\log \left[ 10.5 / \mathrm{M}_{\odot}\right]$). Our host galaxies are not a homogeneous sample and are biased toward large and massive galaxies, which makes it systematically inclined to metal-rich galaxies (cite: 2004ATremonti). A similar study done for an unbiased sample would resolve this tension, but would require significant investment of the ALMA observing time.

Furthermore, our host galaxies are nearby targets ($<80$ Mpc), hence, the physics is constrained to conditions of the Local Universe. Metallicities in the earlier Universe are lower in comparison with low-$z$ galaxies. In our case, the metallicity correction $(Z/Z_{\odot})^{-1.5}$ from eq. [\[eq:eq1\]](#eq:eq1) resulted in a similar increase of 50 per cent for both CCSN locations and host galaxy pixels (for 0.75 $Z_{\odot}$; see Appendix [7](#app:app2)). Conversely, for a metallicity of 0.25 $Z_{\odot}$, the correction is almost an order of magnitude and this could affect the interpretation of results significantly (e.g., for high-$z$ galaxies). That is why several proxies of the molecular gas should be used in addition (such as \[C I\] at both 370 and 609 $\mu$m and/or \[C II\] at 156 $\mu$m). Further studies including other physical conditions (e.g., metal content, binarity fraction, turbulence, stellar populations, etc.) would be required to consider whether SFE alone is producing the observed outcomes.

SFR calibrators using H $\alpha$ and H $\beta$ breaks down for $A_{V} >2.5~\rm{mag}$ (cite: 2009Kennicutt). In our case, typical galaxy pixels have $A_{V}=1$–$2$ mag values; 90 per cent of CCSN environments have $A_{V}<2.5~\rm{mag}$. Only three CCSNe show high dust extinction values: 4.3, 2.9, and 4.6 mag for SN 1985P, SN 2011hp, and SN 2004ip, respectively. However, when these highly extincted CCSNe are removed from the original sample, the trends stay similar. $A_{V}$ is expected to increase in central regions of galaxies, so the observed H $\alpha$ flux will be biased toward lower values. This means that inner galactic regions could exhibit higher values of SFR and SFE than the those reported here. In our data, since we compare CCSNe and host galaxy locations at similar galactocentric distances, this effect would not alter the results.

Although we refer to cloud-scale observations at $\sim$100 pc spatial scales, the actual H ii region and GMC sizes span the range from a few tens of parsecs up to approximately 100 pc (cite: 2010Fukui; 2011Lopez). Due to instrumental limitations, increasing the spatial resolution would reduce the sample size. For this reason, to achieve the goals of mapping individual structures in the ISM, we used a homogenised sample from VLT/MUSE and ALMA observations, leveraging the capabilities of these telescopes as the best in the world in their respective wavelength regimes.

# Conclusions

We collected the surface densities of star formation rate and molecular gas for all available CCSNe to compute star formation efficiencies in their environments. To do so, we used telescopes capable of resolving individual H ii regions and GMCs ($\sim$ 100 pc): VLT/MUSE and ALMA, respectively. A total of 21 H-rich SNe and 19 SESNe were collected (in 25 host galaxies). Both populations of CCSNe explode in regions of higher SFE than the average of their host (PHANGS) galaxies, suggesting that progenitors are associated with massive stars. We find that SESNe are preferentially located in regions with significantly higher star formation rate surface densities, but comparable molecular gas surface densities relative to H-rich SNe. This results in star formation efficiencies (molecular gas depletion times) that are higher (shorter) by an order of magnitude at SESN locations than at H-rich SN. In summary, SESNe preferentially explode in environments characterised by highly efficient, intense star formation. We conclude that the observed properties are best explained by the following scenarios (not mutually exclusive):

1.  Top-heavy IMF: regions hosting SESN explosions may be biased toward a top-heavy IMF. In this case, an excess of very massive stars boosts the observed H $\alpha$ luminosity (and thus the measured SFR) without a corresponding increase in the total molecular gas reservoir.

2.  Binaries dominate the overall ionising radiation: if SESN progenitors predominantly arise from binary systems, then their increased production of ionising photons could enhance the measured star formation rate at these locations. This allows for a high H $\alpha$ flux for a given molecular gas density.

3.  Environmentally driven binarity: specific physical conditions (such as increased turbulence) favour a higher binary fraction. In this model, SESNe are tracers of efficient star-forming environments where binary interaction is the dominant evolutionary path.

It is unlikely the scenario where SESN progenitors originate only from very massive stars in star-forming regions with normal IMFs. Such a model would imply that SESNe should be found in regions with higher $M_{\text{mol}}$ due to the shorter timescales involved, a prediction that is inconsistent with our data and previous works. Ultimately, our results suggest that the ‘SFR–$M_{\text{mol}}$’ relation for CCSN environments is a powerful probe of progenitor physics, pointing towards either IMF variations and/or a high binary fraction as the primary driver for increased SESN rate.

This is the first time that the environments of SFE is computed for a significant sample of CCSNe. Furthermore, these observations resolved cloud-scales for H ii regions and GMCs. Future telescopes such as ELT/HARMONI will have a strong impact in IFU studies at locations of SNe, as better resolutions (possible to match with ALMA), extended wavelengths coverage, and larger samples will be achieved. In addition, to improve galaxy evolution models in numerical cosmological simulations, SESN populations should be implemented in the prescriptions, as they differ in the feedback injected into the ISM and chemical mixing from H-rich SNe.

# Acknowledgements

This research was funded in whole or in part by the National Science Centre (NCN), Poland (grant numbers 2024/53/N/ST9/00350 and 2023/49/B/ST9/00066). For the purpose of Open Access, the author has applied a CC-BY public copyright licence to any Author Accepted Manuscript (AAM) version arising from this submission. Supported by the Foundation for Polish Science (FNP). J.N. acknowledges the support of the Polish National Agency for Academic Exchange (NAWA) Bekker grant BPN/BEK/2023/1/00271, and the kind hospitality of the IAC. L.G. acknowledges financial support from CSIC, MCIN and AEI 10.13039/501100011033 under projects PID2023-151307NB-I00, PIE 20215AT016, CEX2020-001058-M, and by the MaX-CSIC Excellence Award MaX4-SOMMA-ICE. This work was supported by a research grant (VIL54489) from VILLUM FONDEN. This research has made use of the services of the ESO Science Archive Facility. Based on data products created from observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programme(s) 1100.B-0651 (PHANGS-MUSE; PI Schinnerer), 094.B-0321 (MAGNUM; PI Marconi), 0100.B-0116 (MAD; PI Carollo), 097.B-0640 (TIMER; PI Gadotti), 60.A-9194 (PI Kool), 095.D-0172 (AMUSING, PI Kuncarayakti), and 114.27G5.001 (PI Solar). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00243.S: PI Colina (archival), NGC 5135; ADS/JAO.ALMA#2013.1.01161.S: PI Sakamoto (PHANGS), NGC 1365; ADS/JAO.ALMA#2015.1.00902.S: PI Ao (archival), PGC 084885; ADS/JAO.ALMA#2015.1.00925.S: PI Blanc (PHANGS), NGC 1087, NGC 1566; ADS/JAO.ALMA#2015.1.00956.S: PI Leroy (PHANGS), NGC 1672, NGC 3627, NGC 4254, NGC 4303, NGC 4321, NGC 6744; ADS/JAO.ALMA#2017.1.00392.S: PI Blanc (PHANGS), NGC 1087, NGC 1433, NGC 1566; ADS/JAO.ALMA#2017.1.00886.L: PI Schinnerer (PHANGS), NGC 2997; ADS/JAO.ALMA#2018.A.00062.S: PI Faesi (PHANGS), NGC 5128; ADS/JAO.ALMA#2018.1.00272.S: PI Sliwa (archival), NGC 4038; ADS/JAO.ALMA#2018.1.01651.S: PI Leroy (PHANGS), NGC 1300, NGC 1087, NGC 1433, NGC 1566; ADS/JAO.ALMA#2019.1.01305.S: PI Tanaka (archival), NGC 4981; ADS/JAO.ALMA#2021.1.00099.S: PI Michałowski (ACOS survey), ESO 440-011, ESO 492-002, NGC 0908, NGC 1729, NGC 3278, NGC 3354, NGC 3810, NGC 4219, PGC 037625. This research has made use of the Transient Name Server (TNS), operated by the IAU Supernova Working Group and hosted by the Weizmann Institute of Science. We used IAU Circulars and CBETs presented by the Central Bureau for Astronomical Telegrams. We acknowledge the use of the Supernova Catalog maintained by the Institute of Astronomy, Moscow State University (SAI MSU). The catalog can be accessed at: http://stella.sai.msu.ru/sncat/. We acknowledge the work of astronomers supporting the LEDA database (http://leda.univ-lyon1.fr/), the Asiago Supernova Catalogue (http://graspa.oapd.inaf.it/asnc.html), The STScI Digitized Sky Survey (http://archive.stsci.edu/cgi-bin/dss_form), and CfA List of Supernovae (http://www.cbat.eps.harvard.edu/lists/RecentSupernovae.html). This research has made use of the NASA/IPAC Extragalactic Database (NED), which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration (http://ned.ipac.caltech.edu/). Facilities: ALMA; VLT: Yepun. Software: `JULIA` (cite: 2017Bezanson), `STARLIGHT` (cite: 2005CidFernandes), `CARTA` (cite: 2021Comrie), `ASTROPY` (cite: 2013Astropy; 2022Astropy), `NUMPY` (cite: 2020Harris), and `SCIPY` (cite: 2020Virtanen). M.S. led the project, performed all the data analysis, and wrote the paper. M.J.M. supervised the whole project and provided the ACOS data. J.N. co-supervised the whole project. L.G. provided the AMUSING data. L.G., J.P.A., J.S., T.P., and E.Z. presented significant contributions to the interpretation of the data. B.Š., J.A., O.R., J.H., C.J., P.N., D.S., and A.L. contributed to the discussion of results and improve the text in the manuscript. All co-authors provided input to the paper.

# Data Availability

The data underlying this article are available in the article and in its online supplementary material.

# Metallicity corrections

We correct the $\Sigma_{\rm{mol}}$ values from the metallicity. To do so, we computed the gas-phase metallicity indicator described by (cite: 2013Marino) as

$$\begin{equation}
    12 + \log \left( \mathrm{O}/\mathrm{H} \right) = 8.535 - 0.214 \times \mathrm{O3N2},
\end{equation}$$

where $\mathrm{O3N2} = \log \frac{[O III] / \mathrm{H}~\beta}{\mathrm{[N II}] / \mathrm{H}~\alpha}$, and N II (at $6583.45~\mathrm{\mathring{A}}$) and O III (at $5006.843~\mathrm{\mathring{A}}$) are the singly ionised nitrogen and doubly ionised oxygen, respectively. Metallicity $Z$, which is the abundance of elements heavier than helium, was calculated in the following way:

$$\begin{equation}
   \left( Z/Z_{\odot} \right) = 
   10^{\left[12 + \left( \mathrm{O}/\mathrm{H} \right) \right]
   -
   \left[12 + \left( \mathrm{O}/\mathrm{H} \right) \right]_{\odot}},
\end{equation}$$

where according to (cite: 2009Asplund), $Z_{\odot} = 0.0142$ and $12 + \log \left( \mathrm{O}/\mathrm{H} \right)_{\odot} = 8.69$. The factor $(Z/Z_{\odot})^{-1.5}$ used in the correction of $\Sigma_{\rm{mol}}$ is equal to $1.7451^{+0.0003}_{-0.0003}$, $1.62^{+0.04}_{-0.03}$, and $1.66^{+0.12}_{-0.04}$ for host galaxies, H-rich SNe, SESNe, respectively.

# Dominant ionisation source

Gas can be photoionised by star-forming regions or collisionally excited by AGNs (cite: 2023Groves). The BPT diagnostic uses the ratios \[O III\]/H $\beta$ and \[N II\]/H $\alpha$ to pinpoint which is the dominant ionisation source (see Fig. [3](#fig:figA1)). We retained CCSNe located in star-forming and composite regions (a total of 40). We excluded two CCSNe located in AGN regions because their environments are not primarily ionised by massive stars, which is required for calculating the star formation efficiency. A total of 20 per cent of the pixels were removed from the BPT diagram for host galaxies.

![](FigA1.pdf)

# Host galaxies and supernova environments

Detailed information on our host-galaxy sample and properties of the SNe is given in Table [\[tab:tabC1\]](#tab:tabC1). This table lists the host-galaxy name, whether the observation was made by PHANGS, SN name, right ascension (R.A.), declination (Dec.), SN type, SN group, and redshift.

|  |  |  |  |  |  |  |  |  |  |
|---:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | Host galaxy | PHANGS- | PHANGS- | SN name | SN R.A. | SN Dec. | SN type | SN group | $z$ |
|  | name | ALMA | VLT/MUSE |  |  |  |  |  |  |
|  |  |  |  |  | ($\rm{h}\,\rm{min}\,\rm{s}$) | ($\ensuremath{^\circ}\,\ensuremath{'}\,\ensuremath{''}$) |  |  |  |
| 1 | ESO 440-011 | No | No | LSQ13doo | 11$^{\rm{h}}$48$^{\rm{m}}$45.780s | -28$^\circ$17$'$31.20$''$ | Ic | SESNe | 0.006468 |
| 2 | ESO 492-002 | No | No | SN 2005lr | 07$^{\rm{h}}$11$^{\rm{m}}$39.030s | -26$^\circ$42$'$20.20$''$ | Ic | SESNe | 0.008647 |
| 3 | NGC 0908 | No | No | SN 1994ai | 02$^{\rm{h}}$23$^{\rm{m}}$06.170s | -21$^\circ$13$'$58.30$''$ | Ic | SESNe | 0.005026 |
| 4 | NGC 1087 | Yes | Yes | SN 1995V | 02$^{\rm{h}}$46$^{\rm{m}}$26.770s | -00$^\circ$29$'$55.60$''$ | II | H-rich SNe | 0.00507 |
| 5 | NGC 1300 | Yes | Yes | SN 2022acko | 03$^{\rm{h}}$19$^{\rm{m}}$38.990s | -19$^\circ$23$'$42.68$''$ | II | H-rich SNe | 0.005264 |
| 6 | NGC 1365 | Yes | Yes | SN 1983V | 03$^{\rm{h}}$33$^{\rm{m}}$31.630s | -36$^\circ$08$'$55.00$''$ | Ic | SESNe | 0.0055 |
| 7 | NGC 1365 | Yes | Yes | SN 2001du | 03$^{\rm{h}}$33$^{\rm{m}}$29.110s | -36$^\circ$08$'$32.50$''$ | II | H-rich SNe | 0.00371 |
| 8 | NGC 1433 | Yes | Yes | SN 1985P | 03$^{\rm{h}}$42$^{\rm{m}}$06.300s | -47$^\circ$12$'$35.60$''$ | II | H-rich SNe | 0.0036 |
| 9 | NGC 1566 | Yes | Yes | ASASSN-14ha | 04$^{\rm{h}}$20$^{\rm{m}}$01.410s | -54$^\circ$56$'$17.00$''$ | II | H-rich SNe | 0.005017 |
| 10 | NGC 1672 | Yes | Yes | SN 2017gax | 04$^{\rm{h}}$45$^{\rm{m}}$49.430s | -59$^\circ$14$'$42.56$''$ | Ib/c | SESNe | 0.00444 |
| 11 | NGC 1672 | Yes | Yes | SN 2022aau | 04$^{\rm{h}}$45$^{\rm{m}}$41.830s | -59$^\circ$14$'$43.87$''$ | II | H-rich SNe | 0.00444 |
| 12 | NGC 1729 | No | No | SN 2012ap | 05$^{\rm{h}}$00$^{\rm{m}}$13.720s | -03$^\circ$20$'$51.20$''$ | Ic | SESNe | 0.012155 |
| 13 | NGC 2997 | Yes | No | SN 2003jg | 09$^{\rm{h}}$45$^{\rm{m}}$37.910s | -31$^\circ$11$'$21.00$''$ | Ib/c | SESNe | 0.003626 |
| 14 | NGC 3278 | No | No | SN 2009bb | 10$^{\rm{h}}$31$^{\rm{m}}$33.870s | -39$^\circ$57$'$30.00$''$ | Ic-BL | SESNe | 0.009995 |
| 15 | NGC 3354 | No | No | SN 2011jl | 10$^{\rm{h}}$43$^{\rm{m}}$02.950s | -36$^\circ$21$'$52.40$''$ | Ic | SESNe | 0.010001 |
| 16 | NGC 3627 | Yes | Yes | SN 1973R | 11$^{\rm{h}}$20$^{\rm{m}}$11.500s | +12$^\circ$59$'$55.00$''$ | II | H-rich SNe | 0.00193 |
| 17 | NGC 3627 | Yes | Yes | SN 1997bs | 11$^{\rm{h}}$20$^{\rm{m}}$14.160s | +12$^\circ$58$'$19.56$''$ | IIn | H-rich SNe | 0.00193 |
| 18 | NGC 3627 | Yes | Yes | SN 2009hd | 11$^{\rm{h}}$20$^{\rm{m}}$16.990s | +12$^\circ$58$'$46.30$''$ | II | H-rich SNe | 0.0024 |
| 19 | NGC 3627 | Yes | Yes | SN 2016cok | 11$^{\rm{h}}$20$^{\rm{m}}$19.090s | +12$^\circ$58$'$57.20$''$ | IIP | H-rich SNe | 0.00243 |
| 20 | NGC 3810 | No | No | SN 1997dq | 11$^{\rm{h}}$40$^{\rm{m}}$55.900s | +11$^\circ$28$'$45.70$''$ | Ib/c | SESNe | 0.003315 |
| 21 | NGC 4038 | No | No | SN 2004gt | 12$^{\rm{h}}$01$^{\rm{m}}$50.370s | -18$^\circ$52$'$12.70$''$ | Ib/c | SESNe | 0.00548 |
| 22 | NGC 4038 | No | No | SN 2013dk | 12$^{\rm{h}}$01$^{\rm{m}}$52.720s | -18$^\circ$52$'$18.30$''$ | Ic | SESNe | 0.00548 |
| 23 | NGC 4219 | No | No | SN 2011hp | 12$^{\rm{h}}$16$^{\rm{m}}$25.470s | -43$^\circ$19$'$46.90$''$ | Ic | SESNe | 0.00662 |
| 24 | NGC 4254 | Yes | Yes | SN 1967H | 12$^{\rm{h}}$18$^{\rm{m}}$55.000s | +14$^\circ$24$'$00.70$''$ | II | H-rich SNe | 0.008 |
| 25 | NGC 4254 | Yes | Yes | SN 1972Q | 12$^{\rm{h}}$18$^{\rm{m}}$50.000s | +14$^\circ$26$'$00.70$''$ | II | H-rich SNe | 0.008 |
| 26 | NGC 4254 | Yes | Yes | SN 1986I | 12$^{\rm{h}}$18$^{\rm{m}}$52.030s | +14$^\circ$24$'$43.80$''$ | II | H-rich SNe | 0.008029 |
| 27 | NGC 4254 | Yes | Yes | SN 2014L | 12$^{\rm{h}}$18$^{\rm{m}}$48.680s | +14$^\circ$24$'$43.50$''$ | Ic | SESNe | 0.008029 |
| 28 | NGC 4303 | Yes | Yes | SN 1926A | 12$^{\rm{h}}$21$^{\rm{m}}$54.000s | +04$^\circ$29$'$00.60$''$ | II | H-rich SNe | 0.00804 |
| 29 | NGC 4303 | Yes | Yes | SN 1961I | 12$^{\rm{h}}$22$^{\rm{m}}$00.440s | +04$^\circ$28$'$13.30$''$ | II | H-rich SNe | 0.0052 |
| 30 | NGC 4303 | Yes | Yes | SN 1964F | 12$^{\rm{h}}$21$^{\rm{m}}$52.000s | +04$^\circ$28$'$00.40$''$ | II | H-rich SNe | 0.0052 |
| 31 | NGC 4303 | Yes | Yes | SN 1999gn | 12$^{\rm{h}}$21$^{\rm{m}}$57.040s | +04$^\circ$27$'$45.70$''$ | IIP | H-rich SNe | 0.0052 |
| 32 | NGC 4303 | Yes | Yes | SN 2006ov | 12$^{\rm{h}}$21$^{\rm{m}}$55.300s | +04$^\circ$29$'$16.70$''$ | II | H-rich SNe | 0.0052 |
| 33 | NGC 4303 | Yes | Yes | SN 2020jfo | 12$^{\rm{h}}$21$^{\rm{m}}$50.480s | +04$^\circ$28$'$54.05$''$ | IIP | H-rich SNe | 0.00522 |
| 34 | NGC 4321 | Yes | Yes | SN 1979C | 12$^{\rm{h}}$22$^{\rm{m}}$58.580s | +15$^\circ$47$'$52.70$''$ | II | H-rich SNe | 0.00455 |
| 35 | NGC 4321 | Yes | Yes | SN 2020oi | 12$^{\rm{h}}$22$^{\rm{m}}$54.925s | +15$^\circ$49$'$25.05$''$ | Ic | SESNe | 0.00524 |
| 36 | NGC 4981 | No | No | SN 2007C | 13$^{\rm{h}}$08$^{\rm{m}}$49.300s | -06$^\circ$47$'$01.00$''$ | Ib | SESNe | 0.005595 |
| 37 | NGC 5128 | No | No | SN 2016adj | 13$^{\rm{h}}$25$^{\rm{m}}$24.110s | -43$^\circ$00$'$57.90$''$ | IIb | SESNe | 0.001889 |
| 38 | NGC 6744 | Yes | No | SN 2005at | 19$^{\rm{h}}$09$^{\rm{m}}$53.570s | -63$^\circ$49$'$22.80$''$ | Ic | SESNe | 0.002803 |
| 39 | PGC 037625 | No | No | SN 2014ad | 11$^{\rm{h}}$57$^{\rm{m}}$44.440s | -10$^\circ$10$'$15.70$''$ | Ic-pec | SESNe | 0.0053 |
| 40 | PGC 084885 | No | No | SN 2004ip | 18$^{\rm{h}}$32$^{\rm{m}}$41.260s | -34$^\circ$11$'$26.70$''$ | II | H-rich SNe | 0.018276 |

The results obtained in our work are given in Table [\[tab:tabC2\]](#tab:tabC2). Specifically, at the positions of CCSNe we measured the star formation rate surface density, the molecular gas surface density, and the star formation efficiency.

|  |  |  |  |  |  |  |
|---:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | SN name | SN group | $\Sigma_{\mathrm{SFR}}$ | $\Sigma_{\mathrm{mol}}$ | SFE | ALMA detection |
|  |  |  | $\left[ \rm{M}_{\odot}\,yr^{-1}\,kpc^{-2}\right]$ | $\left[ \rm{M}_{\odot}\,kpc^{-2} \right]$ | $\left[\rm{Gyr}^{-1}\right]$ |  |
|  |  |  | $\times 10^{-5}$ | $\times 10^{6}$ | $\times 10^{-2}$ |  |
| 1 | ASASSN-14ha | H-rich SNe | $1698 \pm 17$ | $871 \pm 28$ | $2 \pm 0.1$ | Detection |
| 2 | LSQ13doo | SESNe | $1431 \pm 35$ | $10 \pm 6$ | $142 \pm 8$ | Non-detection |
| 3 | SN 1926A | H-rich SNe | $467 \pm 44$ | $27 \pm 14$ | $18 \pm 9$ | Non-detection |
| 4 | SN 1961I | H-rich SNe | $1102 \pm 32$ | $55 \pm 28$ | $20 \pm 10$ | Non-detection |
| 5 | SN 1964F | H-rich SNe | $171 \pm 11$ | $39 \pm 21$ | $4 \pm 2$ | Non-detection |
| 6 | SN 1967H | H-rich SNe | $5531 \pm 42$ | $215 \pm 8$ | $26 \pm 1$ | Detection |
| 7 | SN 1972Q | H-rich SNe | $498 \pm 11$ | $54 \pm 9$ | $9 \pm 2$ | Detection |
| 8 | SN 1973R | H-rich SNe | $126 \pm 5$ | $155 \pm 16$ | $1 \pm 0.1$ | Detection |
| 9 | SN 1979C | H-rich SNe | $222 \pm 59$ | $23 \pm 12$ | $10 \pm 6$ | Non-detection |
| 10 | SN 1983V | SESNe | $1885 \pm 12$ | $56 \pm 7$ | $34 \pm 4$ | Detection |
| 11 | SN 1985P | H-rich SNe | $56 \pm 9$ | $28 \pm 18$ | $2 \pm 1$ | Non-detection |
| 12 | SN 1986I | H-rich SNe | $2295 \pm 32$ | $98 \pm 12$ | $23 \pm 3$ | Detection |
| 13 | SN 1994ai | SESNe | $4860 \pm 110$ | $2 \pm 1$ | $2400 \pm 1200$ | Non-detection |
| 14 | SN 1995V | H-rich SNe | $1023 \pm 10$ | $179 \pm 13$ | $6 \pm 0.4$ | Detection |
| 15 | SN 1997bs | H-rich SNe | $50 \pm 6$ | $24 \pm 16$ | $2 \pm 2$ | Non-detection |
| 16 | SN 1997dq | SESNe | $806 \pm 16$ | $56 \pm 32$ | $14 \pm 8$ | Non-detection |
| 17 | SN 1999gn | H-rich SNe | $5817 \pm 33$ | $132 \pm 11$ | $44 \pm 4$ | Detection |
| 18 | SN 2001du | H-rich SNe | $730 \pm 9$ | $35 \pm 8$ | $21 \pm 5$ | Detection |
| 19 | SN 2003jg | SESNe | $6290 \pm 130$ | $49 \pm 14$ | $128 \pm 37$ | Detection |
| 20 | SN 2004gt | SESNe | $12410 \pm 220$ | $76 \pm 38$ | $163 \pm 82$ | Non-detection |
| 21 | SN 2004ip | H-rich SNe | $508600 \pm 7500$ | $127 \pm 35$ | $4000 \pm 1100$ | Detection |
| 22 | SN 2005at | SESNe | $1901 \pm 38$ | $675 \pm 15$ | $3 \pm 0.1$ | Detection |
| 23 | SN 2005lr | SESNe | $19910 \pm 280$ | $53 \pm 5$ | $375 \pm 36$ | Detection |
| 24 | SN 2006ov | H-rich SNe | $1348 \pm 86$ | $33 \pm 17$ | $41 \pm 21$ | Non-detection |
| 25 | SN 2007C | SESNe | $5480 \pm 160$ | $47 \pm 3$ | $117 \pm 8$ | Detection |
| 26 | SN 2009bb | SESNe | $77200 \pm 1100$ | $110 \pm 30$ | $700 \pm 190$ | Detection |
| 27 | SN 2009hd | H-rich SNe | $2143 \pm 12$ | $479 \pm 15$ | $4 \pm 0.2$ | Detection |
| 28 | SN 2011hp | SESNe | $11780 \pm 250$ | $21 \pm 6$ | $550 \pm 160$ | Detection |
| 29 | SN 2011jl | SESNe | $1134 \pm 30$ | $6 \pm 3$ | $186 \pm 93$ | Non-detection |
| 30 | SN 2012ap | SESNe | $1201 \pm 72$ | $15 \pm 9$ | $80 \pm 46$ | Non-detection |
| 31 | SN 2013dk | SESNe | $13010 \pm 240$ | $32 \pm 16$ | $410 \pm 210$ | Non-detection |
| 32 | SN 2014L | SESNe | $7547 \pm 49$ | $393 \pm 15$ | $19 \pm 1$ | Detection |
| 33 | SN 2014ad | SESNe | $4673 \pm 66$ | $4 \pm 2$ | $1090 \pm 540$ | Non-detection |
| 34 | SN 2016adj | SESNe | $20970 \pm 530$ | $69 \pm 4$ | $305 \pm 21$ | Detection |
| 35 | SN 2016cok | H-rich SNe | $400 \pm 5$ | $81 \pm 10$ | $5 \pm 1$ | Detection |
| 36 | SN 2017gax | SESNe | $513 \pm 26$ | $114 \pm 15$ | $5 \pm 1$ | Detection |
| 37 | SN 2020jfo | H-rich SNe | $816 \pm 12$ | $29 \pm 15$ | $28 \pm 14$ | Non-detection |
| 38 | SN 2020oi | SESNe | $10308 \pm 57$ | $216 \pm 18$ | $48 \pm 4$ | Detection |
| 39 | SN 2022aau | H-rich SNe | $10243 \pm 31$ | $497 \pm 20$ | $21 \pm 1$ | Detection |
| 40 | SN 2022acko | H-rich SNe | $204 \pm 36$ | $11 \pm 6$ | $19 \pm 11$ | Non-detection |

[^1]: E-mail: martin.solar@amu.edu.pl

[^2]: E-mail: michal.michalowski@amu.edu.pl

[^3]: https://sites.google.com/view/phangs/home

[^4]: https://almascience.eso.org/aq/

[^5]: SN 1926A, SN 1961I, SN 1964F, SN 1967H, SN 1972Q, SN 1973R, SN 1979C, SN 1983V, SN 1985P, SN 1986I, SN 1995V, SN 1997bs, SN 1999gn, SN 2001du, SN 2006ov, SN 2009hd, ASASSN-14ha, SN 2014L, SN 2016cok, SN 2017gax, SN 2019ehk, SN 2020jfo, SN 2020oi, SN 2022aau, and SN 2022acko

[^6]: NGC 1087, NGC 1300, NGC 1365, NGC 1433, NGC 1566, NGC 1672, NGC 3627, NGC 4254, NGC 4303, and NGC 4321

[^7]: SN 2003jg, SN 2004gt, SN 2004ip, SN 2005at, SN 2007C, SN 2013dk, SN 2016adj, SN 2023dpj

[^8]: NGC 2997, NGC 4038, NGC 4981, NGC 5128, NGC 5135, NGC 6744, and PGC 084885

[^9]: SN 1994ai, SN 1997dq, SN 2005lr, SN 2011hp, SN 2011jl, SN 2012ap, LSQ13doo, and SN 2014ad

[^10]: ESO 440-011, ESO 492-002, NGC 0908, NGC 1729, NGC 3354, NGC 3810, NGC 4219, and PGC 037625

[^11]: 2013.1.00243.S, 2015.1.00902.S, 2015.1.00956.S, 2017.1.00886.L, 2018.A.00062.S, 2018.1.00272.S, and 2019.1.01305.S

[^12]: https://irsa.ipac.caltech.edu/applications/DUST/

</paper>

Write the methods card for this paper.