# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.494.5542R\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.494.5542R",
 "title": "Full of Orions: a 200-pc mapping of the interstellar medium in the redshift-3 lensed dusty star-forming galaxy SDP.81",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Rybak, Matus",
 "n_authors": 7,
 "arxiv_id": "1912.12538",
 "doi": "10.1093/mnras/staa879",
 "alma_projects_linked_by_archive": [
  "2016.1.00633.S",
  "2016.1.01093.S",
  "2011.0.00016.SV"
 ]
}
```

Paper text:
<paper>
# Full of Orions: a 200-pc mapping of the interstellar medium in the redshift-3 lensed dusty star-forming galaxy SDP.81

## Abstract

We present a sub-kpc resolved study of the interstellar medium properties in SDP.81, a $z=3.042$ strongly gravitationally lensed dusty star-forming galaxy, based on high-resolution, multi-band ALMA observations of the FIR continuum, CO ladder and the \[C ii\] line. Using a visibility-plane lens modelling code, we achieve a median source-plane resolution of $\sim$200 pc. We use photon-dominated region (PDR) models to infer the physical conditions – far-UV field strength, density, and PDR surface temperature – of the star-forming gas on 200-pc scales, finding a FUV field strength of $\sim10^{3}-10^{4} G_0$, gas density of $\sim10^5$ cm$^{-3}$ and cloud surface temperatures up to 1500 K, similar to those in the Orion Trapezium region. The \[C ii\] emission is significantly more extended than that FIR continuum: $\sim$50 per cent of \[C ii\] emission arises outside the FIR-bright region. The resolved \[C ii\]/FIR ratio varies by almost 2 dex across the source, down to $\sim2\times10^{-4}$ in the star-forming clumps. The observed \[C ii\]/FIR deficit trend is consistent with thermal saturation of the C$^+$ fine-structure level occupancy at high gas temperatures. We make the source-plane reconstructions of all emission lines and continuum data publicly available.

galaxies: high-redshift – galaxies: ISM – gravitational lensing: strong – submillimetre: galaxies

# Introduction

Dusty star-forming galaxies (DSFGs) with star-formation rates (SFR) of 100-1000 M$_\odot$ yr$^{-1}$ play a key role in the epoch of peak star-forming activity of the Universe, in the $z=2-4$ redshift range (e.g., (cite: Casey2014; Swinbank2014)). The rest-frame far-UV radiation from the young, massive stars is often completely obscured by their large dust reservoirs and re-radiated at rest-frame far-infrared (FIR) wavelengths.

The key to understanding the intense star-formation in DSFGs is their interstellar medium (ISM) - dense gas and dust in their (giant) molecular clouds (GMCs). In the canonical GMC picture (e.g., (cite: Tielens1985)), the surface of the clouds is exposed to the intense far-UV radiation from the new-born massive O/B-type stars. This results in a thermal and chemical stratification of the GMC: while deep in the cloud, the gas is in the molecular form (H$_2$, CO); the ionizing flux and gas temperature increase towards the surface, causing CO to dissociate into C and O, with C being ionized into C$^+$ in the photon-dominated region (PDRs) at the cloud surface. Crucially, as the depth of individual layers – and the strength of the emission lines associated with individual species – is largely determined by the surface the FUV field strength ($G$) and the cloud density ($n$(H)), observing emission from multiple chemical species (e.g., C$^+$, C and O fine-structure and CO rotational transitions, dust continuum) allows the PDR properties to be inferred, typically via forward modelling.

The PDR properties in present-day (U)LIRGS have been extensively studied using FIR and mm-wave spectroscopy. An early study by (cite: Stacey1991) – combining *Kuiper Airborne Observatory* \[C ii\] and FIR continuum observations with ground-based CO(1–0) observations – found a range of densities $n$(H)$=10^3-10^6$ cm$^{-3}$, with $G$ in excess of $10^3$ $G_0$[^2]. These studies were revolutionized by *Herschel* FIR spectroscopy, opening doors to large systematic surveys of FIR emission lines down to $\sim$500-pc scales in nearby star-forming galaxies and (ultra)luminous infrared galaxies ((U)LIRGS), e.g., (cite: GraciaCarpio2011; Diaz2013; Rosenberg2015; Smith2017; Diaz2017; Herrera2018a).

Previous studies of gas and dust properties in DSFGs have been limited to spatially-integrated quantities, due to their faintness ($S_\mathrm{850~\mu m}$ of few mJy) and compact sizes (few arcsec), compared to the resolution available at FIR/mm-wavelengths. (cite: Stacey2010) used unresolved \[C ii\], CO(2–1)/(1–0) and FIR continuum observations of a sample of twelve $z=1-2$ galaxies to infer typical $G=10^{2.5}-10^{4}~G_0$, $n$(H)$\simeq10^3-10^{4.5}$ cm$^{-3}$. More recently, the large samples of strongly-lensed DSFGs discovered in FIR/mm-wave surveys by *Herschel* - H-ATLAS (cite: Eales2010; Negrello2010; Negrello2017) and HerMES (cite: Oliver2012; Wardlow2012) - and the South Pole Telescope (cite: Vieira2013; spilker2016) have provided an opportunity to obtain robust continuum and line detections in a fraction of time compared to non-lensed sources. For example, (cite: Gullberg2015) used ground-based FIR, \[C ii\] and low-$J$ CO emission to infer the ISM properties in a sample of strongly lensed galaxies from the South Pole Telescope sample. (cite: Brisbin2015) used *Herschel* \[O i\] 63-$\mu$m and ground-based \[C ii\] and low-$J$ CO observations to infer $n$(H)$=10^3-10^2$ cm$^{-3}$, $G=10^1-10^3~G_0$ in a sample of eight $z$=1.5-2.0 DSFGs. (cite: Wardlow2017) used *Herschel* fine-structure line spectroscopy of strongly lensed DSFGs, obtaining $n$(H)$=10^1-10^3$ cm$^{-3}$, $G=10^{2.2}-10^{4.5}~G_0$. Similarly, (cite: Zhang2018b) used *Herschel* \[N ii\] and \[O i\] observations for the H-ATLAS DSFGs to infer typical densities of $n$(H)$=10^3-10^4$ cm$^{-3}$.

The main limitation of deriving PDR properties from spatially-integrated observations is the implicit assumption that the PDR conditions are uniform across the source, i.e., that the FIR continuum and different emission lines are co-spatial. However, resolved observations of DSFGs found that low-$J$ CO emission is significantly more extended than the FIR continuum (e.g., (cite: Ivison2011; Riechers2011; Spilker2015; CR18)), and that mid-/high-$J$ CO emission is more compact than low-$J$ CO emission (e.g., (cite: Ivison2011), R15b). Additionally, line ratios in strongly lensed sources can be affected by differential magnification, introducing a significant bias in the inferred source properties, particularly for highly-magnified galaxies (e.g., (cite: Serjeant2012)).

Consequently, resolved multi-tracer observations are necessary to robustly infer the PDR conditions in DSFGs. For example, (cite: Rybak2019) have used resolved \[C ii\], CO(3–2) and FIR continuum ALMA observations to study the properties of the star-forming ISM in the central regions ($R\leq2$ kpc) of two $z\sim3$ DSFGs from the ALESS sample (cite: Hodge2013; Karim2013), finding FUV fields in excess of $10^4$ G$_0$ and moderately high densities $n$(H)=$10^{3.5}-10^{4.5}$ cm$^{-3}$. In this regime, the surface temperature of the PDR regions is of the order of few hundred K and the \[C ii\] emission becomes thermally saturated, resulting in a pronounced \[C ii\]/FIR deficit (cite: MunozOh2016).

In this work, we use high-resolution, multi-Band ALMA observations to map the ISM properties in the strongly lensed $z=3.042$ DSFG SDP.81 at 200-pc resolution to address the following questions:

- How are different tracers of ISM - FIR continuum, CO and \[C ii\] emission spatially distributed?

- What is the cooling budget of the molecular gas, and does it vary across the source?

- What are the conditions of the star-forming gas in DSFGs at $z\sim3$ - in particular, FUV field strength, density and surface temperature of the PDR regions? Do they vary significantly across the source?

This paper is structured as follows: in Section [2](#sec:observations), we summarize the ALMA observations analyzed in this work; Section [3](#sec:imaging+modelling) describes the synthesis imaging and lens-modelling of this data. In Section [4](#sec:results+discussion), we use resolved FIR continuum, CO and \[C ii\] maps to investigate the dust properties of SDP.81 (Section [4.1](#subsec:dust_sed)), CO spectral energy distribution and the gas cooling budget (Section 4.2) and the \[C ii\]/FIR ratio and deficit (Section 4.3). Section 5 then describes the PDR modelling procedure and results, and discusses the resolved ISM conditions in SDP.81 and the physical mechanisms driving the \[C ii\]/FIR deficit. Finally, Section [6](#sec:conclusions) summarizes the results of this work.

Throughout this paper we use a flat $\Lambda$CDM cosmology from (cite: Planck2015). Adopting the spectroscopic redshift of $z=3.042$ (cite: alma2015), this translates to a luminosity distance of 26480 Mpc, and an angular scale of 1 arcsec = 7.857 kpc (cite: Wright2006).

# Observations

## Target description

SDP.81 (J2000 09:03:11.6 +00:39:06; (cite: Bussmann2013)), is a $z_S=3.042$ DSFG, strongly lensed by a foreground early-type galaxy with $z_L=0.299$. Identified in the H-ATLAS survey (cite: Eales2010; Negrello2010; Negrello2017), SDP.81 was targeted by the ALMA 2014 Long Baseline Campaign (cite: alma2015). Ancillary observations include HST near infra-red imaging (cite: Dye2014), *Herschel* FIR spectroscopy (cite: Valtchanov2011; Zhang2018b), and radio/mm-wave low-resolution spectroscopy and imaging (cite: Valtchanov2011; Lupu2012). This extensive high-resolution, high-S/N ancillary data make SDP.81 perhaps the best-studied DSFG.

(cite: Rybak2015a; Rybak2015b) (henceforth R15a, R15b) presented the reconstructed maps of Bands 6 and 7 dust continuum, and CO(5–4) and (8–7) emission with a typical resolution of 50-100 pc, alongside the reconstruction of *Hubble Space Telescope* near-IR imaging. These revealed a significantly disturbed morphology of stars, dust and gas in SDP.81, with an ordered rotation in a central dusty disk some 2–3 kpc; a similar conclusion has been reached by independent analysis both in the $uv$-plane (cite: Hezaveh2016) and Cleaned images (cite: Dye2015; Swinbank2015). Based on the kinematic analysis of the CO(5–4) and (8–7) maps, SDP.81 is classified as a post-coalescence merger ((cite: Dye2015), R15b, (cite: Swinbank2015)). In this paper, we adopt the CO(5–4) and CO(8–7) from R15b, and obtain matched-resolutions reconstructions of Band 6 and Band 7 continuum (Section 3.1.3).

## ALMA Band 3 observations

The CO(3–2) line was observed in ALMA Cycle 5, (Project #2016.1.00633). The observations were carried out on 2017 September 9 in ALMA Band 3. While the original project requested a total of 4 hours on-source with a resolution of 0.2 arcsec, the total observations amount to only $\sim$45 min. The array configuration consisted of 40 12-meter antennas, with baselines extending from 39 to 7550 m, covering angular scales between $\sim$0.10 and 19 arcsec. The measured precipitable water vapour was 1.5 mm. The frequency setup consisted of four spectral windows (SPWs), centered at 97.730, 99.626, 85.813 and 87.614 GHz, respectively. Two SPWs were configured in the line mode with 1920 channels of 976.6 kHz width per channels, for a total bandwidth of 1.875 GHz per SPW. The other two SPWs were configured in the continuum mode (channel width 15.625 MHz), with a bandwidth of 2.0 GHz per SPW.

## ALMA Band 8 observations

The \[C ii\] line was observed in ALMA Cycle 4 (Project #2016.1.01093.S). The observations were carried out on 2016 November 14 with 44 12-meter antennas with baselines extending from 13 to 850 m, corresponding to angular scales between $\sim$0.16 and 10.5 arcsec. The precipitable water vapour ranged between 0.52–0.64 mm. The frequency setup consisted of four SPWs, centered on 468.35, 458.24, 456.35 and 470.24 GHz, respectively. SPWs 0–2 were configured in a continuum mode with a bandwidth of 2.0 GHz per SPW, while SPW 3 was split into 240 7.812-kHz-wide channels, for a total bandwidth of 1.875 GHz.

## ALMA 2014 Long Baseline Campaign observations

As the ALMA Long Baseline Campaign (LBC) observations of SDP.81 were described in detail in (cite: alma2015), here we provide a only brief overview of the data The observations comprised of 5.9, 4.4 and 5.6 hours on-source in Bands 4, 6 and 7 respectively, taken in October 2014. The frequency setup covered the CO(5–4) line in Band 4, CO(8–7) and H$_2$O (2$_{02}-1_{11}$) lines in Band 6 and CO(10–9) line in Band 7. The frequency setup provided 7.5 GHz bandwidth per Band, with a channel width of 0.976 – 1.95 MHz for line-containing spectral windows (SPWs), and 15.6 MHz for the continuum SPWs. The antenna configuration consisted of 22-36 12-meter antennas, with baselines ranging from $\sim$15 m to $\sim$15 km, resulting in a synthesized beam size of $\sim30$ mas for Band 7 to $\sim$55 mas for Band 4 (Briggs weighing, robust = 1). For the CO lines, a strong drop in S/N was observed for baselines longer than 1 M$\lambda$ (cite: alma2015). This resulted in restricting the CO line analysis to baselines $\leq1$ M$\lambda$; here we adopt this $uv$-distance cut for all the ALMA datasets.

# Data processing and analysis

## Data preparation and imaging

All the data processing was done with Casa versions 4.7 and 5.0 (cite: McMullin2007). Figure [1](#fig:cleaned) shows the Cleaned frequency-integrated maps of the Band 8, \[C ii\], CO(3–2) and CO(10–9) emission, obtained using natural weighting and an outer Gaussian taper of 0.2 arcsec.

### ALMA Band 3

The data were calibrated and flagged using the standard ALMA Cycle 4 pipeline; in addition, antennas DA53 and DV22 were manually flagged due to a systematically high antenna temperature. The CO(3–2) line was detected between 85.509 and 85.571 GHz. Due to the low S/N, we frequency-averaged the line-containing channels into a single frequency bin. A time-averaging of 20 s was applied, as in R15a,b. This reduces the size of the problem by a factor of a few without compromising the surface-brightness sensitivity. The Cleaned images (Figure [1](#fig:cleaned)) show CO(3–2) emission along the main arc and in the counterimage, with a peak S/N of 5.6$\sigma$.

The Cleaned Band 3 continuum map has an rms noise of 10 $\mu$Jy beam$^{-1}$ (natural weighting). We do not detect any Band 3 continuum emission from the lensed source at 3$\sigma$ significance. We detect the active galactic nucleus (AGN) synchrotron emission in the lensing galaxy (rest-frame frequency 111 GHz) with a total flux of 52$\pm$10 $\mu$Jy. The observed flux is consistent with the (cite: Tamura2015) synchrotron spectrum for the foreground AGN within $2\sigma$.

### ALMA Band 8

After applying the standard ALMA Cycle 4 calibration, we performed manual flagging in the time-domain to remove several integrations which showed elevated noise levels; a total of 6 minutes of data was flagged. We also flagged channels affected by atmospheric lines at 468.0 and 457.3 GHz.

The \[C ii\] line is detected between 469.791 and 470.253 GHz. The observed image-plane \[C ii\] integrated line flux of 170$\pm$20 Jy km s$^{1}$ ($(2.7\pm0.3)\times10^{-18}$ W m$^{-2}$) is consistent with the *Herschel* Spire FTS measurement of $(2.9\pm0.6)\times10^{-18}$ W m$^{-2}$ (cite: Zhang2018b) within 1$\sigma$. This confirms that ALMA Band 8 observations are not resolving out extended \[C ii\] emission[^3].

The \[C ii\] absorption from diffuse ionized gas was detected towards some Galactic star-forming regions (e.g., (cite: Gerin2015)). At high redshift, (cite: Nesvadba2016) detected a \[C ii\] absorption towards to $z=3.4$ DSFG, which they interpreted as evidence for infalling gas. Looking for a potential \[C ii\] absorption in the Cleaned cube with a velocity resolution of 40 km s$^{-1}$, we do not find any evidence for \[C ii\] absorption against the 160-$\mu$m continuum.

### ALMA Long Baseline Campaign: Bands 6 and 7 continuum, CO(10–9) line

To ensure that all the tracers are compared on the same spatial scales, we revisit the (cite: alma2015) Bands 6 and 7 continuum, applying a $uv$-distance cut of $\leq$1 M$\lambda$ as opposed to the 2-M$\lambda$ cut in R15a. For details of the continuum data preparation, we refer the reader to R15a.

Finally, we include the CO(10–9) line, which was observed in ALMA Band 7 (see (cite: alma2015) for detailed description and imaging). The CO(10–9) line is detected between 284.733–285.52 GHz; due to the low S/N ratio (peak image-plane SN$\simeq5$, Fig. [1](#fig:cleaned)) we frequency-averaged the visibilities into a single channel. Although we obtain an integrated CO(10–9) line flux (measured from the Cleaned images) $\sim$50 per cent higher than reported by (cite: alma2015) (derived from spectral fitting), the two measurements are consistent within 2$\sigma$.

![](./figures/fig1.png)

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | $\nu_\mathrm{obs}$ | Beam FWHM | Beam PA | $\sigma_\mathrm{rms}$ | $S_\nu$ | $S_\mathrm{peak}$ | $\Delta v$ | $S_\nu \Delta v$ |
|  | \[GHz\] | \[arcsec\] | \[deg\] | \[mJy beam$^{-1}$\] | \[mJy\] | \[mJy beam$^{-1}$\] | \[km s$^{-1}$\] | \[Jy km s$^{-1}$\] |
| $[$C ii$]$ | 470.02 | 0.32$\times$0.26 | 138 | 0.5 | 180$\pm$7 | 5.5 | 700$\pm$100 | 170$\pm$20 |
| CO(3-2) | 85.55 | 0.36$\times$0.24 | 137 | 0.13 | 17.9$\pm$1.8 | 0.73 | 660$\pm$110 | 11.8$\pm$2.3 |
| CO(10–9) | 285.1 | 0.31$\times$0.19 | 24 | 0.07 | 6.7$\pm$0.9 | 0.33 | 780$\pm$100 | 4.5$\pm$0.6 |
| Band 8 cont. | 463.35 | 0.32$\times$0.26 | 138 | 0.14 | 112$\pm$2.0 | 6.8 | – | – |

## Lens modelling

We reconstruct the source-plane surface brightness distribution of individual tracers via lens-modelling, thereby minimizing the differential magnification bias. The additional complication in case of interferometric data arises from the fact that radio-interferometers do not measure directly the sky-plane surface brightness distributions, but the visibility function, which is essentially a sparsely-sampled Fourier transform of the sky. Furthermore, the high angular resolution provided by ALMA requires the source to be reconstructed on a pixellated grid, as simple analytic models for the source (e.g., Sérsic profiles) are no longer sufficient to fully capture the complex structure of the source. Consequently, several visibility-fitting lens-modelling codes aimed primarily at ALMA observations, have been developed (R15a, (cite: Hezaveh2016; Dye2018)).

We perform the lens-modelling using the method first presented in (cite: Rybak2015a), which is an extension of the Bayesian technique of (cite: Vegetti2009) to the radio-interferometric data. To summarize, this technique uses a parametric lens model, while the source is reconstructed on an adaptive triangular grid obtained via the Delaunay tessellation. This setup provides an increased source-plane resolution in the high-magnification regions. We minimize the following penalty function, which combines $\chi^2$ calculated in the visibility-space with a source-plane regularization to constrain the problem and prevent noise-fitting:

$$\begin{multline}
P(\boldsymbol{s}\,|\, \psi(\boldsymbol{\eta},\boldsymbol{x}), \lambda_s, \boldsymbol{d})=(\mathbf{FL} \boldsymbol{s} - \boldsymbol{d})^{\top} \mathbf{C}_d^{-1} (\mathbf{FL}\boldsymbol{s} - \boldsymbol{d})+\\
+\lambda_s (\mathbf{R}_s \boldsymbol{s})^{\top} \mathbf{R}_s \boldsymbol{s},
\label{equ:penalty_f}
 
\end{multline}$$

where $\mathbf{F}$ and $\mathbf{L}$ are Fourier-transform (including the primary beam response) and lensing operators, $\lambda_s$ and $\mathbf{R}_s$ are the regularisation constant and the regularisation matrix for the source surface brightness distribution and $\mathbf{C}_d^{-1}$ is the covariance matrix of the observed visibilities. For a detailed discussion of the lens-modelling technique, we refer the reader to (cite: Koopmans2005) and (cite: Vegetti2009).

We adopt the lens model of R15a derived from 0.1-arcsec resolution ALMA Band 6 and 7 continuum observations, which follows a singular isothermal ellipsoid profile with an external shear component. Keeping the lens mass model fixed, we re-optimize for the offset between the lens center and phase-tracking centre (which differ for different observations) and the source regularization parameter $\lambda_S$. The sky-plane pixel size is set to 25 mas; as the adaptive grid is obtained by casting back every second pixel, the synthesized beam is sub-sampled by a factor of $\sim4$. The primary beam response is approximated by an elliptical Gaussian. The rms noise for each visibility is estimated as the $1\sigma$ scatter of the real/imaginary visibilities for a given baseline over a 10-minute interval, rather than from the Sigma column of the ALMA Measurement Set files.

We estimate the uncertainty on the reconstructed source-plane surface brightness distribution by drawing 1000 random realizations of the noise map given the $\sigma_\mathrm{rms}$ for each baseline, solving for the source using the best-fitting lens model and $\lambda_S$, and calculating the scatter per grid element from the resulting source reconstructions.

As the source-plane surface brightness sensitivity depends on the spatial position, we estimate the spatially-integrated magnifications for each tracer as follows: we take all the source-plane pixels with S/N $\geq$1, 2 and 3, forward-lens them into the image-plane and calculate the corresponding magnification and uncertainty for each S/N threshold; and finally estimate the overall magnification as the mean of the magnification factors for different S/N thresholds.

## Source-plane reconstructions

We now discuss the source-plane reconstructions for the ALMA Band 8 continuum and the \[C ii\] and CO(3–2) emission. Given the varying S/N of individual line and continuum observations, we further assess the reliability of the source-plane reconstruction by performing our lens modelling analysis on mock datasets in Appendix [8](#sec:appendix_B); these confirm the robustness of our source-plane reconstruction, with the mean surface brightness recovered within 10–15 per cent for most datasets ($\sim$20 per cent for CO(3–2)), comparable to the ALMA flux calibration uncertainty. We therefore consider our reconstructions to be robust.

Fig. [2](#fig:reconstructions) presents the best-fitting models of the \[C ii\], 160-$\mu$m continuum and CO(3–2) emission; the full output of the lens modelling procedure are provided in Appendix [7](#sec:appendix_A). The source-plane models reproduce the full range of image-plane structures (given the S/N), as demonstrated by the lack of significant residuals in the dirty-image plane. The median source-plane resolution is $\sim$30 mas, which corresponds to $\sim$200 parsec; the resolution in the vicinity of the caustic is as high as $\sim$3 pc. To allow the comparison on a uniform spacial scale, for the analysis in Section [4](#sec:results+discussion) we re-sample the reconstructed source onto a Cartesian grid with 200$\times$200 pc pixels.

![](./figures/fig2.png)

![](./figures/fig3.png)

### ALMA Band 8 continuum

The Band 8 continuum emission is observed at the highest S/N; consequently, the small-scale structure can be robustly reconstructed. Similarly to the Bands 6 and 7 continuum, the Band 8 continuum surface-brightness distribution is concentrated into two prominent clumps, corresponding roughly to the northern and central parts of the source, surrounded by a fainter emission approximately $3\times2$ kpc in extent (R15a,(cite: Dye2015)). The northern clump is quadruply imaged, which results in a superb S/N and reconstruction fidelity, while the central clump is only doubly imaged. The relative brightness of the clumps is roughly constant across Bands 6, 7 and 8, indicating only a limited change in the dust spectral energy distribution (Section [4.1](#subsec:dust_sed)).

### \[CII\] emission

Thanks to the high S/N of the \[C ii\] observations, we are able to model the full velocity structure of the \[C ii\] emission, rather than just the frequency-averaged line. We frequency-averaged the line into channels 62.50 MHz ($\sim40$ km s$^{-1}$) wide, which provide a good trade-off between S/N per channel (necessary for a robust source reconstruction) and resolving the velocity structure; we then optimize for the source regularization parameter $\lambda_S$ for each channel separately. The velocity resolution matches that of the CO(5–4) and CO(8–7) reconstructions from R15b. We calculate the velocity moment-zero (surface brightness) and moment-one maps. For the moment-one map, we mask pixels with SNR$\leq$1 in each channel before calculating the velocity map.

The \[C ii\] emission is considerably more extended than both the FIR continuum and the CO(5–4) and CO(8–7) emission (Fig. [2](#fig:reconstructions)). Although the \[C ii\] luminosity increases in the FIR-bright region of the source, at the position of the peak FIR surface brightness, the \[C ii\] emission shows a significant drop, indicating an extremely low \[C ii\]/FIR ratio. A similar drop in \[C ii\]/FIR ratio at the continuum peak was recently found in a $z=1.7$ lensed DSFG SDP.11 (cite: Lamarche2018), in which the regions with the highest $\Sigma_\mathrm{SFR}$ are essentially undetected in the \[C ii\] line emission. We will address the \[C ii\]/FIR ratio in SDP.81 in more detail in Section [4.3](#subsec:CII_FIR).

The reconstructed \[C ii\] emission map reveals a low surface-brightness emission ($\Sigma_\mathrm{[CII]}\sim3\times10^7~L_\odot$ kpc$^{-2}$) between -20 and +170 km s$^{-1}$, stretching out to $\sim$10 kpc north of SDP.81 (Fig. [4](#fig:cii_mom1)). The velocity maps show that this excess emission is not co-rotating with the main \[C ii\]/CO(5–4)/CO(8–7) component. This double-imaged feature is present in the dirty images of the corresponding velocity channels (Fig. [17](#fig:reconstructions_appendix_cii)), clearly offset from the main Einstein arc. The total $L_\mathrm{[CII]}$ luminosity of this component is $\sim0.6\times10^9~L_\odot$, less than 10 per cent of the total source-plane \[C ii\] luminosity. We do not detect any FIR continuum or CO emission from the region outside the dashed box in Fig. [4](#fig:cii_mom1), despite the high S/N of the FIR and CO(5–4)/CO(8–7) data. This second \[C ii\] source is not co-spatial with the optically-bright substructure detected in the HST WFC3 160W imaging ((cite: Dye2014), R15b). Given the perturbed velocity/velocity-dispersion fields (R15b), we interpret this morphology as a potential low-mass companion; assuming the $M_\mathrm{gas}$ scales with $L_\mathrm{[CII]}$, the gas mass ratio of the two components is 10:1. Assuming this \[C ii\] emission is due to star-formation, we use the (cite: Herrera2015) SFR-\[C ii\] relation to derive a typical $\Sigma_\mathrm{SFR}=1$ M$_\odot$ yr$^{-1}$. It total, $\sim$50 per cent of the total \[C ii\] luminosity arises from regions with $\Sigma_\mathrm{SFR}\leq10~M_\odot$ yr$^{-1}$.

![image](./figures/fig4a.png) ![image](./figures/fig4b.png)

### CO(3–2) emission

The CO(3–2) emission is only detected in the northern part of the FIR-bright region in SDP.81, at $\sim5\sigma$ significance. As the CO(3–2) has much lower S/N ($\sim10$) than the remaining lines/continuum data, it must be interpreted carefully. A key check on the relative source-plane distribution of individual tracers is to compare their image-plane surface brightness distributions. As seen in Fig. [1](#fig:cleaned), in the image plane, the CO(3–2) emission peaks in a different region compared to the Band 8 continuum and \[C ii\]. We confirm that this is not an artifact of a sparse $uv$-plane coverage by reconstructing mock ALMA observations matching the S/N and $uv$-plane coverage of the CO(3–2) data (Appendix [8](#sec:appendix_B)): for a uniformly distributed CO(3–2) emission, emission from the southern part of the counterimage would be detected. This confirms that the CO(3–2) emission is concentrated to the north of the source. In the sky-plane, the CO(1–0) emission peaks to the south of the FIR source ((cite: Valtchanov2011), R15b); which implies a significant offset between the CO(3–2) and CO(1–0) surface brightness peaks.

### CO(10–9) emission

The CO(10–9) emission is concentrated between the diamond caustics, and to the north, continuing the trend seen in the CO(8–7) emission. The lower S/N makes the interpretation of the faint extended structure (surface brightness \<1.2 mJy km s$^{-1}$ kpc$^{-2}$) challenging: as we show in Appendix [9](#sec:appendix_C), this structure can be an artifact of the lensing reconstruction.

Finally, Fig. [3](#fig:composite) shows the relative distribution of the FIR continuum, \[C ii\] and CO emission. This highlights the compact nature of the FIR continuum with respect to the CO and \[C ii\] lines, and the extended, low-surface brightness \[C ii\] emission.

# Results and discussion

## Dust continuum

### Global dust SED

First, we consider the dust thermal spectral energy distribution (SED). Namely we use the ALMA Bands 4/6/7/8 and *Herschel* PACS/SPIRE observations listed in Table [1](#tab:sed) and an optically-thin modified black-body SED:

$$\begin{equation}
S_\nu \propto M_\mathrm{dust} \frac{\nu^{3+\beta}}{\exp(-h\nu/k T_\mathrm{dust})-1},
\label{eq:mbb}
\end{equation}$$

where $M_\mathrm{dust}$ is the dust mass, $h$ is the Planck constant, $k$ is the Boltzman constant, $T_\mathrm{dust}$ the dust temperature and $\beta$ the emissivity index. As the continuum magnification varies only marginally between ALMA Bands 6/7/8, we assume that the (unresolved) *Herschel* PACS/SPIRE continuum follows the same source-plane surface brightness distribution as ALMA Band 8 continuum, and hence has the same magnification factor. We assume a uniform $T_\mathrm{dust}$ and $\beta$, and adopt a uniform magnification for the 160-$\mu$m to 1.3-mm continuum. We obtain $T_\mathrm{dust}=35\pm4$ K and $\beta=1.8\pm0.3$ and a (magnification-corrected) FIR luminosity (8-1000 $\mu$m) $L_\mathrm{FIR}=(2.4\pm0.5)\times10^{12}$ L$_\odot$. These are in agreement with previous estimates ((cite: Bussmann2013; Swinbank2015; Sharda2018); note that (cite: Sharda2018), do not explicitly fit for $\beta$). The inferred $T_\mathrm{dust}$, $\beta$ are in line with those derived for the general high-redshift DSFG population. For example, for the 99 DSFGs from the ALESS sample (cite: Hodge2013) (cite: Swinbank2014) derived a median $T_\mathrm{dust}=35\pm1$ K using *Herschel* SPIRE and ALMA Band 7 photometry (approach directly comparable to ours); while (cite: daCunha2015) found a median $T_\mathrm{dust}=43\pm10$ K by including additional UV- to radio-wavelength photometry. The dust emissivity index $\beta$ is within the range of $\beta=1.5-2.0$ inferred for ALESS galaxies (cite: Swinbank2014).

Although the increasing CMB temperature at high redshifts can significantly bias the inferred $T_\mathrm{dust}$ and $L_\mathrm{FIR}$ (cite: daCunha2013; Zhang2016), we consider the CMB effects to be negligible for SDP.81, Namely, adopting the (cite: daCunha2013) corrections, the CMB effect on $T_\mathrm{dust}$ is $\leq0.1$ K, while the inferred $L_\mathrm{FIR}$ is biased by $\leq$0.1 dex.

We derive the global star-formation rate and the resolved star-formation rate surface density $\Sigma_\mathrm{SFR}$ (Fig. [5](#fig:sigma_SFR)) using the (cite: Kennicutt1998) SFR-$L_\mathrm{FIR}$ relation for the Salpeter initial mass function (see also (cite: Casey2014)): $$\begin{equation}
\mathrm{SFR} [M_\odot~\mathrm{yr}^{-1}] = 1.71\times10^{-10} L_\mathrm{FIR} [L_\odot],
\end{equation}$$ which yields SFR = 410$\pm$90 M$_\odot$ yr$^{-1}$. Note that a part of the FIR luminosity in intensely star-forming systems might be due to FUV heating contribution from older stellar populations (cite: Narayanan2015); however, this effect only becomes important at SFRs much higher than that of SDP.81. Given the compact size of the FIR emission in SDP.81 compared to the CO and \[C ii\] emission, we will refer to the region with $\Sigma_\mathrm{SFR}\geq 50$ M$_\odot$ yr$^{-1}$ kpc$^{-2}$ as the *FIR-bright region*.

![](./figures/fig5.png)

| Band                     |      \[mJy\]       |
|:-------------------------|:------------------:|
| PACS 160 $\mu$m          | (58$\pm$10)/$\mu$  |
| SPIRE 250 $\mu$m         | (133$\pm$11)/$\mu$ |
| SPIRE 350 $\mu$m         | (186$\pm$14)/$\mu$ |
| SPIRE 500 $\mu$m         | (165$\pm$14)/$\mu$ |
| ALMA Band 8 (640 $\mu$m) |    5.0$\pm$0.5     |
| ALMA Band 7 (1.0 m)      |    1.9$\pm$0.2     |
| ALMA Band 6 (1.3 mm)     |   1.14$\pm$0.11    |

: FIR and mm-wave photometry of SDP.81 used for the dust SED modelling, with *Herschel* PACS and SPIRE flux-densities adopted from (cite: Zhang2018b) and ALMA Bands 6 and 7 flux-densities adopted from R15a. The *Herschel* flux measurements are given in the image-plane; for our analysis, we assume all the 160 to 500-$\mu$m emission to follow the Band 8 surface brightness distribution.

### Resolved dust SED

Having derived the spatially-integrated $T_\mathrm{dust}$ and $\beta$, we now consider the spatial variation in the dust continuum SED using the source-plane reconstructions of the ALMA Bands 6, 7 and 8 continuum (rest-frame wavelength 160–350 $\mu$m). These are well within the Rayleigh-Jeans tail of the modified black-body profile, and hence can not robustly constrain both $T_\mathrm{dust}$ and $\beta$ at the same time. We therefore adopt $\beta=1.8$ derived from the spatially-integrated SED fit, and fit for $T_\mathrm{dust}$ only.

However, fitting the modified black-body SED to the resolved Bands 6, 7 and 8 data, we do not find any significant spatial variation in $T_\mathrm{dust}$; the variation in $\Sigma_\mathrm{FIR}$ is fully accounted by a varying $M_\mathrm{dust}$. Repeating the SED-fitting on the Cleaned Bands 6, 7 and 8 images (thus eliminating any lens-modelling systematics) yields results consistent with the source-plane analysis. Therefore, for the rest of this paper, we adopt a uniform $T_\mathrm{dust}$ approximation for the FIR luminosity calculation.

The uniform dust temperature in SDP.81 contrasts with the expectation of $T_\mathrm{dust}$ increasing towards the centre of DSFGs; for example, (cite: CR18) invoked a radial decrease in $T_\mathrm{dust}$ and dust optical depth to explain the different FIR and CO(3–2) sizes in the stacked observations of the ALESS sample, with $T_\mathrm{dust} \geq 80$ K in the central $R \leq 1$ kpc region (A. Weiß, private communication).

We therefore consider whether our data might support high $T_\mathrm{dust}$ ($\geq$60 K) in the central FIR-bright clumps. We do this by fixing $T_\mathrm{dust}$ to 60 and 80 K, respectively, and optimizing for the normalization ($\propto M_\mathrm{dust}$) only. We find $T_\mathrm{dust}$=60 K to be inconsistent with the data at $\geq3\sigma$ significance anywhere except in the vicinity of the FIR brightness maximum (Fig. [6](#fig:t_dust)); $T_\mathrm{dust}$=80 K is excluded at $\geq3\sigma$ confidence level for the entire source. These results are therefore in tension with the high central $T_\mathrm{dust}$ invoked by (cite: CR18).

Finally, we note three fundamental limitations of inferring $T_\mathrm{dust}$ from the rest-frame 160–350 $\mu$m continuum. First, at 200-pc scales probed here, the high-$T_\mathrm{dust}$ regions might not dominate the continuum SED, resulted in a bias towards low $T_\mathrm{dust}$ temperature estimates due to the mass-weighting in Equation ([\[eq:mbb\]](#eq:mbb)). Second, our resolved ALMA imaging is still on the Rayleigh-Jeans tail of the dust continuum SED; higher-frequency, resolved observations (e.g., with ALMA Bands 9 or 10) will be necessary to properly constrain $T_\mathrm{dust}$ and $\beta$ on sub-kpc scales. Finally, the optically thin approximation make break down in the central regions, biasing the inferred $T_\mathrm{dust}$.

![image](./figures/fig6a.png) ![image](./figures/fig6b.png)

## Emission lines

With the resolved maps of the \[C ii\] line and the almost complete CO SLED in hand, we can compare the total gas cooling via the \[C ii\], \[O i\] and all the CO lines combined. In particular, for the strong FUV fields and high gas (surface) densities expected in DSFGs, as the outer C$^+$ layer becomes progressively thinner, the main cooling channel of the neutral gas can switch from the \[C ii\] line to the \[O i\] 63 $\mu$m/145$\mu$m fine-structure lines, or even CO rotational lines (cite: Kaufman1999; Kaufman2006; Narayanan2017).

Table [\[tab:co_cii_balance\]](#tab:co_cii_balance) lists the inferred source-plane CO and \[C ii\] line luminosities, integrated over the entire source. We complemented the resolved ALMA observations by archival observations of the CO(1–0) (VLA; (cite: Valtchanov2011)) and CO(7–6) (CARMA, (cite: Valtchanov2011)) lines, as well as an upper limit[^4] on the CO(9–8) lines (Z-Spec on the Caltech Submillimeter Observatory, (cite: Lupu2012)). The unresolved/low-resolution nature of the archival data prevents a source-plane reconstruction. Therefore, we assume that the CO(1–0), (7–6) and (9–8) lines follow the same spatial distribution as the CO(3–2), (8–7) and (10–9) lines, respectively.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Line | $\mu$ | $L_\mathrm{line}$ | $L'_\mathrm{line}$ | Ref. |
|  |  | \[$10^{9}$ L$_\odot$\] | \[$10^{10}$ K km s$^{-1}$ pc$^{-2}$\] |  |
| FIR | 18.2$\pm$1.2 | 2400$\pm$500 | – | R15a (Bands 6 & 7) |
|  |  |  |  | This work (Band 8) |
| C ii | 15.3$\pm$0.5 | 4.36$\pm$0.44 | 1.99$\pm$0.20 | This work |
| O i 63 $\mu$m | – | 2.5$\pm$0.7 | 1.4$\pm$0.4 | (cite: Zhang2018b) |
| CO(1–0)$^a$ | — | 0.005$\pm$0.001 | 11$\pm$2 | Valtchanov et al., (2011) |
| CO(3–2) | 17.0$\pm$0.4 | 0.018$\pm$0.010 | 1.33$\pm$0.13 | This work |
| CO(5–4) | 17.9$\pm$0.7 | 0.075$\pm$0.024 | 1.23$\pm$0.12 | R15b |
| CO(7–6)$^a$ | – | 0.06$\pm$0.02 | 0.6$\pm$0.2 | Valtchanov et al., (2011) |
| CO(8–7) | 16.9$\pm$1.1 | 0.098$\pm$0.020 | 0.39$\pm$0.04 | R15b |
| CO(9–8)$^a$ | – | $<$0.49 | $<$0.21 | Lupu et al. (2012) |
| CO(10–9) | 20.6$\pm$2.6 | 0.0060$\pm$0.0010 | 0.0124$\pm$0.0012 | This work |

$^a$ inferred from unresolved observations.

### \[CII\] dominates the gas cooling budget

We first compare the source-averaged \[C ii\], \[O i\] and CO SLED cooling rates. The \[O i\] 63-$\mu$m line is detected in *Herschel* SPIRE FTS spectra (cite: Valtchanov2011; Zhang2018b) with a line flux of $(2.1\pm0.7)\times10^{-18}$ W m$^{-2}$, while the 3$\sigma$ upper limit on the \[O i\] 145-$\mu$m line flux is $2.3\times10^{-18}$ W m$^{-2}$ (cite: Zhang2018b). This translates to image-plane line luminosities of $\mu L_\mathrm{[OI]63}=(45\pm12)\times10^{9}$ L$_\odot$, $\mu L_\mathrm{[OI]145}<5\times10^{10}$ L$_\odot$. Assuming both lines follow the FIR continuum surface brightness distribution, we obtain the de-lensed source-plane luminosities of $L_\mathrm{[OI]63}=(2.5\pm0.7)\times10^9$ L$_\odot$ and $L_\mathrm{[OI]145}<3\times10^9$ L$_\odot$, respectively. The inferred \[O i\]/\[C ii\] luminosity ratio is 0.6$\pm$0.2 for the \[O i\] 63-$\mu$m and $\leq$0.7 (but likely much lower) for the \[O i\] 145-$\mu$m line.

To compare the total gas cooling via the CO ladder and the \[C ii\], we first obtain a first-order estimate of the total cooling via the CO $J_\mathrm{upp}=1-10$ lines (in the absence of CO(2–1), CO(4–3), CO(6–5) and CO(7–6) observations) assuming that the CO line ratios in SDP.81 match CO ratios of the Class I ULIRGs from (cite: Rosenberg2015). Given the low CO(10–9) luminosity, the $J_\mathrm{upp}>10$ CO rotational lines are expected to contribute only marginally to the gas cooling. The total CO luminosity is $L_\mathrm{CO}=\Sigma_{J=1}^{10} L_\mathrm{CO(J_\mathrm{upp})}\simeq0.8\times10^9~L_\odot$, $\sim$20 per cent of the total $L_\mathrm{[CII]}$ and $\sim$10 per cent of the total gas cooling ($L_\mathrm{[CII]}+L_\mathrm{CO}+L_\mathrm{[OI]}$). Therefore, the global gas cooling in SDP.81 is dominated by the \[C ii\] line.

Fig. [7](#fig:gas_cooling) shows the resolved CO/\[C ii\] gas cooling ratio. The \[C ii\] line dominates over the CO cooling across the entire source, with the highest CO/\[C ii\] cooling ratio ($\sim20$ per cent) found at the position of the northern star-forming clump. The low CO/\[C ii\] cooling ratios indicate molecular cloud surface density $\leq10^3$ M$_\odot$ pc$^{-2}$ (c.f., (cite: Narayanan2017)).

![image](./figures/fig7.png)\

### CO spectral energy distribution

The global source-plane CO SLED in SDP.81 peaks between $J_\mathrm{upp}=5$ and 9 (in units of $L_\odot$), with a sharp drop at $J_\mathrm{upp}=10$ (Fig. [8](#fig:co_sled), see also (cite: Yang2017), for a recent sky-plane analysis). Compared to the (cite: Rosenberg2015) study of CO excitation in present-day ULIRGS, the sharp drop in $L_\mathrm{CO}$ for $J_\mathrm{upp}\geq9$ and minor CO contribution to the global neutral gas cooling makes SDP.81 akin to (cite: Rosenberg2015) Class I sources, which have similarly low CO cooling contributions ($\leq10$ per cent). In addition to the heating by FUV radiation, mechanical heating by dissipating supernovae shocks can contribute significantly to the gas energy budget in starburst regions (e.g., (cite: Meijerink2011; Kazandjian2012; Kazandjian2015)), pumping the $J_\mathrm{upp}\geq10$ CO transitions, as well as high-$J$ HCN, HNC and $^{13}$CO lines. Significant mechanical heating is required to explain the high-$J$ CO excitation in some of the archetypal present-day ULIRGs, such as e.g., Arp 220 (cite: Rangwala2011), NGC 253 (cite: Rosenberg2014) and NGC 6420 (cite: Meijerink2013). Given the absence of CO $J_\mathrm{upp}>10$, HCN or $^{13}$CO observations in SDP.81, we do not attempt to directly constrain the mechanical heating contribution. As the SDP.81 CO ladder is well-reproduced ($\chi^2\leq1$) by the PDRToolbox models which do not include mechanical heating and as the SDP.81-like (cite: Rosenberg2015) Class I ULIRGs are fully compatible with UV heating, the observed line ratios in SDP.81 are consistent with negligible mechanical heating.

Finally, we consider how closely individual CO lines trace the FIR emission. We calculate the Pearson’s correlation coefficient $R$ for each line and estimate the corresponding uncertainty by drawing 1000 random realizations of CO/\[C ii\] and FIR surface brightness (with the mean and standard deviation from Fig. [2](#fig:reconstructions)) for each pixel with SNR$\geq$3 in both tracers. We find $R_\mathrm{CO(3-2)/FIR}=0.401\pm0.010$, $R_\mathrm{CO(5-4)/FIR}=0.847\pm0.006$, $R_\mathrm{CO(8-7)/FIR}=0.821\pm0.006$ and $R_\mathrm{CO(10-9)/FIR}=0.664\pm0.09$. However, the stronger regularization of CO reconstructions compared to the FIR continuum might artificially decrease the CO–FIR correlation by smoothing the small-scale CO features, especially at high $\Sigma_\mathrm{FIR}$. For comparison, the correlation coefficient for \[C ii\] $R_\mathrm{[CII]/FIR}=0.712\pm0.006$

![image](./figures/fig8a.png)\
![image](./figures/fig8b.png)\

### Gas depletion time across the source

Finally, we combine the resolved $\Sigma_\mathrm{SFR}$ maps and CO emission line maps to estimate the molecular gas depletion time, $t_\mathrm{dep}\sim\Sigma_\mathrm{H_2}/\Sigma_\mathrm{SFR}$. We estimate the molecular gas surface density $\Sigma_\mathrm{H_2}$ using the CO(3–2) line map. For $J_\mathrm{upp}>1$ CO transitions, the $L'_\mathrm{CO}$ is first down-converted to $L'_\mathrm{CO(1-0)}$ via the $R_{J1} = L'_\mathrm{CO(J-J-1)}/L'_\mathrm{CO(1-0)}$ factor, which is then converted to $M_\mathrm{gas}$ via $M_\mathrm{gas}=\alpha_\mathrm{CO} L'_\mathrm{CO(1-0)}$. We adopt $R_{31}$ from (cite: Sharon2016) who found a mean $R_{31}=0.78\pm0.27$ for a sample of $z\sim2$ sub-millimeter galaxies; and $\alpha_\mathrm{CO}=1.0$ inferred by (cite: CR18) from CO kinematic studies of $z=2-3$ DSFGs (a similar value has been derived by (cite: Bothwell2013)). These are consistent with the dynamical mass constraints from the CO(5–4) and (8–7) velocity maps (R15b, (cite: Swinbank2015)).

Fig. [9](#fig:t_depletion) shows the resolved $t_\mathrm{dep}$ map in SDP.81. With the CO(3–2) emission concentrated to the north, we find a strong variation of $t_\mathrm{dep}$ across the FIR bright source, from $\sim1$ Myr in the south to $\sim20$ Myr in the north. By adopting the (cite: Sharon2016) $r_{3/1}$ value, the relative uncertainty is $\sim$33 per cent; the flux calibration uncertainty on the CO(3–2)/FIR ratio is $\sim15$ per cent.

Due to the low S/N and structure in the reconstructed CO(3–2) emission, we refrain from investigating the Kennicutt-Schmidt relation, particularly the slope of $\Sigma_\mathrm{H_2}-\Sigma_\mathrm{SFR}$ relation. However, as the concentration of the CO(3–2) emission to the north (and the low CO(3–2) surface brightness to the south) is robustly recovered by the lens modelling (Appendix [8](#sec:appendix_B)), the general $t_\mathrm{dep}$ trend is robust. As a further check, using the CO(5–4) line as a molecular gas tracer[^5] and adopting $R_{51}=0.32\pm0.05$ from the (cite: Bothwell2013) CO SLED survey of a sample of 40 DSFGs at $z=1.2-4.1$, we find a $t_\mathrm{dep}=1-30$ Myr, confirming the extremely short gas depletion time.

Resolved $t_\mathrm{dep}$ measurements have been carried out for only a handful of DSFGs (see (cite: Sharon2019) for a recent compilation), which generally show similarly strong ($\sim1$ dex) variation in $t_\mathrm{dep}$. The depletion times in SDP.81 are in the extreme starburst regime, an order of magnitude lower than seen in some other high-redshift DSFGs – e.g., GN20 ($t_\mathrm{dep}=50-200$ Myr, (cite: Hodge2015)), J14011 (50-100 Myr, (cite: Sharon2013)) and J0911 (200-1000 Myr, (cite: Sharon2019)). (cite: Canameras2017) found a comparably low $t_\mathrm{dep}$ (10-100 Myr) in an extreme strongly lensed $z\sim3$ starburst PLCK G244.8+54.9, albeit at much higher star-formation surface densities ($\Sigma_\mathrm{SFR}\sim2\times10^3$ M$_\odot$ yr$^{-1}$ kpc$^{-2}$). Given the extremely short depletion time in the centre of SDP.81, sustaining the high $\Sigma_\mathrm{SFR}$ requires an efficient loss of gas angular momentum to feed the star formation.

![image](./figures/fig9.png)\

## \[CII\]/FIR ratio and deficit

Studies of nearby star-forming galaxies (e.g., (cite: Malhotra2001; Luhman2003)) have revealed that the \[C ii\]/FIR ratio decreases with increasing FIR luminosity (i.e., SFR) – the so-called \[C ii\]/FIR deficit. This trend was confirmed by *Herschel* FIR surveys of local main-sequence galaxies (e.g., (cite: Smith2017)) and ULIRGs (e.g., (cite: Diaz2013; Diaz2017)), as well as by unresolved observations of high-redshift DSFGs (e.g., (cite: Stacey2010; Gullberg2015; spilker2016)). In particular, resolved observations at $z\sim0$ have found a tight correlation with the FIR (SFR) surface density (cite: Herrera2015). Recently, resolved \[C ii\] studies in $z>1$ DSFGs have been presented by (cite: Gullberg2018; Lamarche2018; Litke2019) and (cite: Rybak2019), revealing a pronounced \[C ii\]/FIR deficit down to $L_\mathrm{[CII]}/L_\mathrm{FIR}\simeq10^{-4}$. Similarly pronounced \[C ii\]/FIR deficits have been found in resolved ALMA observations of $z\geq5$ quasar hosts (e.g., (cite: Wang2019; Neeleman2019; Venemans2019)). Here, we consider both the source-averaged and resolved \[C ii\]/FIR ratio in SDP.81, and compare it to local and high-redshift studies.

Based on the source-plane FIR and \[C ii\] luminosities (Table [\[tab:co_cii_balance\]](#tab:co_cii_balance)), we infer a spatially integrated \[C ii\]/FIR luminosity ratio of $(1.5 \pm 0.3)\times 10^{-3}$. This is consistent with low \[C ii\]/FIR ratios seen in other high-redshift sources (Fig. [11](#fig:cii_fir_comparison)), as well as the *Herschel* observations of ULIRGs from the GOALS sample (cite: Diaz2017). However, as the \[C ii\] emission is significantly more extended than the FIR continuum (in line with (cite: Gullberg2018; Rybak2019)), the source-averaged \[C ii/FIR measurement provides only an upper limit on the \[C ii\]/FIR ratio in the central, FIR-bright region. The large extent of the \[C ii\] emission compared to the FIR continuum implies that the spatially-averaged \[C ii\]/FIR measurements in high-redshift sources – as inferred from unresolved observations – mask the potentially very strong \[C ii\]/FIR deficit in the actual star-forming regions.

Considering the resolved \[C ii\]/FIR maps in Fig. [10](#fig:cii_fir_map), the \[C ii\]/FIR ratio varies by more than 1 dex across the source, down to $\sim(2-3)\times10^{-4}$ in the two FIR-bright clumps – almost an order of magnitude lower than the spatially-integrated \[C ii\]/FIR ratio. We find significant ($\geq3\sigma$) gradients in the \[C ii\]/FIR ratio on sub-kpc scales. Namely, on the outskirts, the \[C ii\]/FIR ratio is consistent with expected gas heating efficiency via the photoelectric effect (0.1–1.0 per cent, e.g., (cite: BakesTielens1994)). However, the \[C ii\]/FIR ratio decreases steeply towards the FIR-bright clumps, down to $\sim3\times10^{-4}$, indicating a strong \[C ii\]/FIR deficit. Similar radial trends have been observed in other resolved \[C ii\]/FIR observations at high redshift (cite: Gullberg2015; Lamarche2018; Litke2019; Rybak2019; Wang2019). As shown in Fig. [7](#fig:gas_cooling), the reduced efficiency of \[C ii\] cooling is partially compensated by the increase in CO/\[C ii\] luminosity ratio, as expected from radiative transfer arguments (e.g., (cite: Narayanan2017)). We note that several isolated pixels at the very outskirts show very loiw \[C ii/FIR ratios - these are likely lens-modelling artifacts.

Fig. [11](#fig:cii_fir_comparison) compares the \[C ii\]/FIR ratio in SDP.81 as a function of the star-formation rate surface density $\Sigma_\mathrm{SFR}$ to other local and high-redshift sources, and the empirical relation of (cite: Smith2017). Resolved \[C ii\]/FIR deficit measurements in high-redshift DSFGs (cite: Gullberg2018; Lagache2018; Litke2019; Rybak2019) show a $\geq1$ dex scatter in \[C ii\]/FIR for a given $\Sigma_\mathrm{SFR}$. While this might partially stem from systematic uncertainties in $\Sigma_\mathrm{SFR}$ estimates and the varying fraction of the \[C ii\] emission from ionized gas (c.f., (cite: Diaz2017)), the observed \[C ii\]/FIR dispersion is likely due to the intrinsic scatter in galactic properties, such as gas and dust conditions. From the SDP.81 data, we estimate the best-fitting $\log \Sigma_\mathrm{SFR}$-$\log$(\[C ii\]/FIR) slope of $-0.75\pm0.01$, using orthogonal distance regression, similar to the slope of $-0.7$ derived by (cite: Lamarche2018) for SDP.11. This is much steeper than the (cite: Smith2017) trend ($-0.21\pm0.03$). We address the \[C ii\]/FIR slope when correcting for the fraction of gas in \[C ii\] and the physical origin of the \[C ii\]/FIR deficit in more detail in Section [5.4](#subsec:cii_fir_origin).

![image](./figures/fig10a.png)\
![image](./figures/fig10b.png)

![](./figures/fig11_large.png)

# PDR modelling

## Modelling setup

We adopt the line and FIR continuum predictions from the PDRToolbox models (cite: Kaufman1999; Kaufman2006; Pound2008). The PDRToolbox models are calculated for a semi-infinite slab geometry, assuming a solar metallicity and stopping the calculation at the depth corresponding to a visual extinction $A_V=10$. The PDRToolbox models have been widely used in interpreting atomic and molecular line observations from both $z\sim0$ ULIRGs (e.g., (cite: Diaz2017)) and high-redshift DSFGs (e.g., (cite: Valtchanov2011; Gullberg2015; Wardlow2017; Rybak2019)); we now apply the same approach to SDP.81. As the FIR studies of metallicity tracers in $z\geq1$ DSFGs indicate metallicities $\geq1~Z_\odot$ (cite: Wardlow2017), we consider the $Z=1~Z_\odot$ default PDRToolbox model as appropriate for dust-rich ISM of SDP.81.

The default PDRToolbox models are sampled onto a 0.25 dex grid which is too coarse to estimate the uncertainties on the inferred properties. We re-sample them onto a finer grid (steps of 0.05 dex), using a degree 2 spline for interpolation.

For the comparison with observations, we consider the following independent line ratios: \[C ii\]/FIR, \[C ii\]/CO(5–4), \[C ii\]/CO(3–2), CO(8–7)/CO(5–4) and CO(10–9)/CO(5–4). The unresolved lines - \[O ii\] and CO(7–6) are excluded from this comparison, as their magnification factors are unknown. Finally it should be noted that the \[O i\] 63-$\mu$m line can undergo significant self-absorption (e.g., (cite: Rosenberg2015)). The line ratios are calculated using line luminosities in units of $L_\odot$. In addition to the surface-brightness uncertainty due to lens modelling, we include an additional 10 per cent flux calibration error for each tracer, as appropriate for high-S/N ALMA observations. In the line-ratio maps, we consider pixels with SNR$\geq$3 as robust detections; for pixels with SNR$<3$, we adopt $3\sigma$ upper limits. We then calculate the $\chi^2$ for each $G$, $n$ model. Following (cite: Sawicki2012), we include the $3\sigma$ upper limits as

$$\begin{multline}
\chi^2(G_i, n_i) = \sum_j \left( \frac{R^\mathrm{data}_j-R^\mathrm{model}_j(G_i, n_i) }{\sigma^\mathrm{data}_j} \right)^2 - \\
 - 2 \sum_{j'} \ln \left[ \sqrt{\frac{\pi}{2}} \sigma_{j'} \left( 1+\mathrm{erf}\left(\frac{R^\mathrm{model}_{j'}(G_i, n_i)-3\sigma_{j'} }{\sqrt{2} \sigma_{j'}} \right) \right) \right],
\label{eq:pdr_pf}
\end{multline}$$

where $R^\mathrm{data}_i$, $R^\mathrm{model}_i$ are the measured and predicted values of the $i$-th line ratio, the indices $j$, $j'$ run over the line ratios with SNR$\geq3$ (detections) and $<$3 (upper limits), respectively, and $\sigma_{j}$, $\sigma_{j'}$ denote corresponding uncertainties. Considering only the SNR$\geq$3 detections (i.e. dropping the second term in Equation [\[eq:pdr_pf\]](#eq:pdr_pf)) changes the best-fitting $G$, $n$ only marginally ($\leq$0.1 dex).

Several corrections need to be applied to the data before a direct comparison with the PDR models. First, the observed \[C ii\] luminosity has to be corrected for the contribution from non-PDR sources (i.e. ionized gas). The contribution of ionized gas to \[C ii\] emission can be estimated using \[N ii\] 122/205-$\mu$m lines (cite: Croxall2017; Herrera2018a); however, \[N ii\] 122-$\mu$m emission is undetected in the *Herschel* spectra with only weak upper limits ($\leq2.6\times10^{-18}$ W m$^{-2}$ (cite: Zhang2018b), giving a PDR fraction of $\geq$0.6), while \[N ii\] 205-$\mu$m line falls outside the *Herschel* spectral coverage. Alternatively, using the empirical relation for the GOALS sample, the PDR contribution to the \[C ii\] can be estimated using the rest-frame 63-$\mu$m and 158-$\mu$m continuum (Equation 4 of (cite: Diaz2017)): for SDP.81, these correspond to the SPIRE 250-$\mu$m and ALMA Band 8 continuum (Table [1](#tab:sed)), yielding $f_\mathrm{[CII]}^\mathrm{PDR}=0.90\pm0.10$. Given the available constraints, we adopt a conservative estimate of the $f_\mathrm{[CII]}^\mathrm{PDR}=0.8$. We discuss the sensitivity of the inferred PDR properties to this choice below.

Second, the PDRToolbox predictions need to be adjusted in case a ratio of an optically thin and an optically thick tracer is considered. Namely, the emergent line intensities are predicted for a semi-infinite slab of gas illuminated only from the face side; for the extended starburst environment in SDP.81, the clouds are likely exposed to FUV radiation from multiple sides. While for the optically-thick tracers, only the emission from the face side of the cloud is observed, for the optically-thin tracers, both the sides facing to and away from the observer will contribute to the observed flux, and the predicted fluxes need to be doubled. The FIR continuum is typically optically thin down to rest-frame 70-100$\mu$m (e.g., (cite: Casey2014)). We assume that the \[C ii\] emission is optically thin, although moderate optical depths ($\tau\sim1$) have been proposed for some Galactic PDRs (e.g., (cite: Graf2012; Sandell2015)) and high-redshift sources (cite: Gullberg2015). The CO rotational lines are all optically thick, with $\tau\geq10$ at $\Sigma_\mathrm{SFR}>1$ M$_\odot$ yr$^{-1}$ kpc$^{-2}$ (cite: Narayanan2014).

As the results of PDR modelling depend directly on the reconstructed source-plane surface brightness distribution for each tracer, the robustness of the inferred PDR properties against potential bias in line ratios needs to be assessed. In Appendix [9](#sec:appendix_C), we investigate the effect of an extreme (order unity) bias in the measured surface brightness ratios for all the tracers considered; note that this is much larger than the surface brightness bias due to lens modelling for even the lowest-S/N tracer considered. We find that the inferred $G$, $n$(H) values shift by $\leq0.5$ dex even in such an extreme scenario, confirming that the PDR results are robust to (reasonable) bias in measured surface brightness ratios.

Finally, we consider the CMB temperature effects at $z=3$ on the observed line luminosities. Adopting the (cite: daCunha2013) models (for n(H)$\sim10^4$ cm$^{-3}$, see results below), the CO line luminosity is biased by $\leq$10 per cent even for the most affected line (CO(3–2)), below the flux calibration uncertainty. We therefore consider the CMB effect on the inferred PDR models to be negligible.

## Global PDR model

We first apply the PDR modelling to the spatially-integrated source-plane line and continuum luminosities. Fig. [12](#fig:pdr_models_global) shows the $G$ and $n$ values traces by individual line ratios[^6]. The maximum a posteriori model gives $G = 10^{3.1\pm0.1}~G_0$, $n = 10^{4.9\pm0.1}$ cm$^{-3}$, with a reduced $\chi^2=0.96$. The derived values are largely insensitive to \[C ii\] optical depth: for an optically thick \[C ii\] emission, the inferred $G$, $n$ values change by +0.5 dex and -0.1 dex, respectively. Increasing the fraction of \[C ii\] emission originating in PDR regions from 80 to 100 per cent results in $G$, $n$ changing by $\leq$0.1 dex.

Compared to the (cite: Valtchanov2011) global PDR model for SDP.81 (inferred using the same PDRToolbox models based on \[O i\], \[C ii\] and CO(1–0) lines and FIR continuum), our $G$, $n$ estimates are $\sim$1 dex higher. This is mainly due to two factors; (1) the lower \[C ii\] line luminosity measured by ALMA and the re-reduced *Herschel* spectroscopy (Section [3](#sec:imaging+modelling)); (2) we are considering CO $J_\mathrm{upp}\geq3$lines, which trace denser molecular gas that CO(1–0) in (cite: Valtchanov2011) (see Section 5.3 for a detailed discussion of systematics).

To assess the impact of differential magnification on the global PDR model, we apply the same analysis to the sky-plane (i.e., not de-lensed) line and FIR luminosities (Fig. [12](#fig:pdr_models_global)). The best fitting $G$, $n$ sky-plane model is only marginally ($\sim0.1$ dex) offset from the source-plane one. This is due to the large spatial extent (compared to the beam size) of all tracers considered; this significantly reduces the differential magnification bias.

![](./figures/fig12.png)

## Resolved PDR model

We now perform the resolved PDR modelling, using the line ratios and upper limits for each 200-pc pixel. For this part of the analysis, we adopt conservative uncertainties estimates. The total error budget consists of:

- Flux calibration uncertainty, assumed to be 10 per cent in each Band.

- Pixel-by-pixel surface brightness uncertainty from the lens modelling for a fixed source regularization parameter $\lambda_S$, estimated using the scatter in source realizations in Section [3](#sec:imaging+modelling).

- Source-averaged surface-brightness uncertainty estimated from reconstructions of *mock* sources (Appendix [8](#sec:appendix_B)), which account for potential bias in the maximum a posteriori $\lambda_S$. These vary between 6 per cent (FIR continuum) to 30 per cent for CO(10–9) and 65 per cent for CO(3–2) (Table [2](#tab:app_b)). For CO(3–2) and CO(10–9), this error dominates the error budget.

During the fitting procedure, we discard the solutions with $G_0/n$(H)$\leq10^{-3}$, which would imply an unphysically large source (c.f. (cite: Diaz2017; Wardlow2017)). Fig. [13](#fig:G0_nH) shows the $G_0$ and $n$(H) values inferred for individual 200-pc regions in SDP.81, given the surface brightness distributions from Fig. [2](#fig:reconstructions). In the central, FIR-bright region, we find strong FUV fields with $G=10^{3.5} - 10^{4.0}~G_0$, and high density $n$(H)=$10^{5.0}-10^{5.5}$ cm$^{-3}$, with a typical uncertainty of $\sim0.2$ dex. These agree well with the global PDR model. We find a significant ($>3\sigma$) gradient in $G$ in the East-West direction: $G$ increases from $10^{3.0\pm0.2}$ to $10^{4.0\pm0.1}~G_0$. While the star-burst region might exhibit increased gas density, we do not find a significant spatial variation in $n$(H). The most direct interpretation is that the star-formation is constrained to the central, disc-like part of the gas reservoir.

The PDR surface temperature $T_\mathrm{PDR}$ varies from about 150 K in the outskirts to 1500 K in the FIR-bright clumps. However, with $T_\mathrm{PDR}$ S/N $\leq$5 across the source, we can not robustly measure the spatial variation of $T_\mathrm{PDR}$. The full implications of the high $T_\mathrm{PDR}$ and its local variations for the \[C ii\]/FIR deficit are discussed in Section [4.3](#subsec:CII_FIR).

![image](./figures/fig13.png)\

How do these values compare to measurements for other star-forming systems? Fig. [14](#fig:G0_nH_comparison) compares the resolved $G$, $n$ value in SDP.81 to unresolved PDR models of $z=2-5$ DSFGs from (cite: Gullberg2015) and stacked DSFGs from (cite: Wardlow2017). Compared to both samples, SDP.81 shows a similar FUV field strength, with density $\geq1$ dex above the (cite: Wardlow2017) range, and comparable to the densest (cite: Gullberg2015) sources. Using resolved \[C ii\] and CO(3–2) and FIR ALMA imaging, (cite: Rybak2019) inferred $G\sim10^4~G_0$, $n\sim10^4-10^5$ cm$^{-3}$ in the central regions of two $z=2.94$ DSFGs from the ALESS sample; SDP.81 shows slightly higher $G$ and lower $n$(H).

Compared to the PDR properties of the present-day ULIRGs (GOALS sample, (cite: Diaz2017)) – inferred from the \[O i\] 63-$\mu$m and \[C ii\] lines and FIR continuum – both the global and resolved PDR properties of SDP.81 show density almost $\sim$2 dex higher, with somewhat ($\sim0.5$ dex) stronger FUV fields.

Finally, we consider star-forming regions in the Milky Way and the Large Magellanic Cloud[^7] from the (cite: Oberst2011) compilation. The resolved PDR properties of SDP.81 show densities comparable to large molecular clouds such as Sgr B2 and 30 Dor, albeit with FUV fields $\sim1$ dex stronger; these might indicate a closer distance between the stars providing FUV radiation and the PDR surfaces, compared to 11–80 pc in 30 Dor ((cite: Chevance2016)). Indeed, close associations of the O/B stars and gas clouds have been invoked by (cite: Herrera2018b) to explain the \[C ii\]/FIR deficit in $z\sim0$ star-forming galaxies and ULIRGs.

On sub-pc scales, we compare the inferred PDR properties with the resolved ($\sim0.05$ pc) study of Orion by (cite: Goicoechea2015), who used \[C ii\], FIR continuum and CO(2–1) observations to infer the PDR conditions in the OMC 1. Using the (cite: Stacey2010) diagnostic diagram (based on (cite: Kaufman1999; Kaufman2006) PDR models used in our analysis), (cite: Goicoechea2015) obtain $G\simeq3\times10^4~G_0$, $n\geq10^5$ cm$^{-3}$ for the region closest ($R\leq$0.1 kpc) to the Trapezium cluster, decreasing down to $G\simeq10^3~G_0$, $n\simeq10^4$ cm$^{-3}$. These are, respectively, on the upper and lower end of the conditions seen in the FIR-bright region of SDP.81; however, in SDP.81, these describe physical conditions averaged over 200-pc scales (which likely include a number of star-forming regions and the voids between them), underlining the extreme nature of the star-forming regions in DSFGs.

![image](./figures/fig14.png)\

### Caveats and limitations

Our PDR analysis - both resolved and unresolved - is based on semi-infinite slab, uniform-density PDR models, which are compared with the FIR continuum (160-330 $\mu$m rest-frame), \[C ii\] and CO ($J_\mathrm{upp}\geq3$) observations. Our choice of the modelling suite - the PDRToolbox models - was motivated by the satisfactory performance of the models given the lines studied here and corresponding the uncertainties, and for consistency with earlier, source-averaged studies of ISM properties in DSFGs. The PDRToolbox models reproduce the observed line ratios well (reduced $\chi^2\leq5$), at least given the spatial resolution, diagnostics considered and S/N of the data at hand. Here, we summarize the limitations of this approach:

- Large surface-brightness uncertainties for CO(3–2) and CO(10–9). As outlined at the beginning of this Section, we adopt conservative surface-brightness uncertainty estimates to avoid over-interpreting the data. For the CO(3–2) and CO(10–9) lines, these are dominated by the error on source reconstruction due to their low S/N. Namely, excluding the uncertainties from Appendix [8](#sec:appendix_B) from the error budget decreases the quality of the best-fitting models in the FIR-bright clumps(reduced $\chi^2=10-25$). This suggests that an additional heating mechanism or a multi-phase ISM model would be more appropriate in high-$\Sigma_\mathrm{SFR}$ clumps. However, as shown in Appendix [8](#sec:appendix_B), the S/N of the CO(3–2) and (10–9) data at hand is currently insufficient to fully constrain the relative importance of different heating mechanisms.

- Geometry effects. Our semi-infinite, uniform-density slab models (even after adjusting for multi-side illumination) are likely too simplistic given the complex, clumpy star-forming environment expected in SDP.81, where strong gradients in ISM density and composition along the line-of-sight might be expected. These can be properly accounted for by 3D radiative transfer codes that account for the full spatial stratification of the (multi-phase) ISM, and a realistic distribution of radiation sources.

- Isochoric models. The self-gravity and external pressure on the molecular clouds will result in a density stratification, which is not included in our models. The effects of assumed cloud density profiles were recently studied by (cite: Popping2019), who found that different assumed density profiles result in \[C ii\] and CO ($J_\mathrm{upp}\leq5$) luminosities changing by up to $\sim$0.5 dex. This effect might be even more dramatic for the CO(8–7) and CO(10–9) lines. Alternatively, isobaric models - e.g., as in a recent application of the (cite: LePetit2006) code to the resolved observations of 30 Doradus by (cite: Chevance2016) - might provide a better description of molecular clouds in intensely star-forming environment. However, (cite: Chevance2016) do not find significant differences between gas properies inferred using the isochoric and isobaric assumptions.

- Reliance on mid- to high-$J$ CO lines. Our PDR modelling is largely driven by the CO(5–4) and CO(8–7) lines, however, the predictions for the emergent line intensities can vary significantly between different PDR codes. This is because the high-$J$ CO emission is confined to the outer cloud layer; therefore, differences in CO abundance will result in a different predictions (e.g., (cite: Rollig2007)). Therefore, the inferred gas properties might depend strongly on the underlying PDR model.

- Limited sensitivity to cold, low-density gas. By including only $J_\mathrm{upp}\geq3$ CO lines (critical density $n_\mathrm{crit}\geq8\times10^3$ cm$^{-3}$, we effectively discount the extended cold, low-density ($n\leq10^3$ cm$^{-3}$) gas phase traced by CO(1–0) and CO(2–1) lines. Indeed, studies of the CO ladders including the $J_\mathrm{upp}=1-2$ lines have found significant cold gas components both in $z\sim0$ ULIRGs (e.g., (cite: Kamenetzky2014; Greve2014)) and high-redshift DSFGs (e.g., (cite: Bothwell2013; Yang2017)). While the cold gas component can contribute to the CO(3–2) and CO(5–4) luminosity, the (cite: Yang2017) source-averaged CO SLED model for SDP.81 - which includes both a cold and a warm component - shows the cold-gas contribution to the CO(3–2) and CO(5–4) luminosities to be $\leq$30 and $<$10 per cent, respectively. Therefore, our results should not be significantly affected by the cold gas component (Appendix [9](#sec:appendix_C)).

- Mechanical and cosmic/X-ray heating. In the high-$\Sigma_\mathrm{SFR}$ regime, additional mechanism not included in the PDRToolbox models - e.g., mechanical heating by shocks, X-ray radiation and cosmic rays - can contribute significantly to the total gas heating. Although the line ratios in SDP.81 are well-reproduce by models that include only far-UV heating by stars; some of the key diagnostics of e.g., mechanical heating, are not available for SDP.81 (Section 4.2.1). Future observations of additional tracers (e.g., high-$J$ CO lines, mid-$J$ HCN/HCO$^+$ lines, CO isotopologues) will be necessary to properly assess the relative importance of different heating mechanisms.

## What drives the \[CII\]/FIR deficit in SDP.81?

With the inferred $G$, $n$ and $T_\mathrm{PDR}$ maps in hand, we now address the origin of the \[C ii\]/FIR deficit in SDP.81.

Recently, (cite: Rybak2019) used resolved (0.15–0.5 arcsec) observations of \[C ii\], CO(3–2) and FIR continuum emission in two unlensed $z\sim3$ DSFGs to show that the \[C ii\]/FIR deficit in their central regions is due to thermal saturation. We apply the analysis of (cite: Rybak2019) to the 200-pc resolution maps of SDP.81. Namely, we consider the following mechanisms: (1) thermal saturation of the \[C ii\] fine-structure levels; (2) reduced gas heating due to positive grain charging; (3) AGN contribution.

### Reduced photoelectric heating

We calculate the photoelectric heating rate per hydrogen atom following (cite: Wolfire2003):

$$\begin{multline}
\Gamma_\mathrm{PE} = \frac{1.1\times10^{-25}G'Z_d}{1+3.2\times10^{-2}\Big[G'\big(T_\mathrm{gas}/100~K\big)^{1/2} n_e^{-1}\phi_\mathrm{PAH}\Big]^{0.73}} \\ \mathrm{erg \, s^{-1}},
\label{eq:photoel}
\end{multline}$$

where $G'=1.7 \times G_0$, $Z_d$ is the dust-to-gas ratio (normalized to the Galactic value), $n_e$ the electron density and $\phi_\mathrm{PAH}$ a factor associated with the PAH molecules. Assuming $n_e=1.1\times10^{-4}\,n$ and $\phi_\mathrm{PAH}=0.5$, we calculate $\Gamma_\mathrm{PE}$ for each resolution 200$\times$200 pc resolution element. The $\Gamma_\mathrm{PE}$ varies by only $\sim$50 per cent across the source; this variation is insufficient to explain the $\sim$1.5 dex variation in the observed \[C ii\]/FIR ratio.

### AGN effects

At sub-kpc scales, a strong \[C ii\]/FIR deficit can be driven by AGNs, by simultaneously suppressing the \[C ii\] emission by X-ray-driven ionization of C$^+$ to C$^{2+}$ etc., and increasing the FIR luminosity due to extra FUV flux from the accretion disk. Resolved \[C ii\]/FIR studies of local active galaxies (cite: Smith2017; Herrera2018b) have revealed a strong \[C ii\]/FIR drop within $\sim500$-pc radius of the AGN in some galaxies. While the AGN influence will be largely negligible for kpc-scale deficits (c.f., (cite: Rybak2019)), the AGN sphere of influence is comparable to the 200-pc resolution of our data. XMM observations of the SDP.81 field detect 0.5–8 keV flux of $(49\pm7)\times10^{-15}$ erg s$^{-1}$ cm$^{-2}$, with a hardness ratio of -0.4 at the position of SDP.81 (cite: Ranalli2015). However, it is unclear whether this flux is associated with the lensed DSFG, or the AGN in the $z=0.299$ lens, which is detected in radio and mm-wave imaging. Assuming the X-ray flux is all due to a hypothetical AGN at the position of the northern FIR-bright clump (lensing magnification $\mu\simeq20$), we find a source-plane X-ray luminosity $L_\mathrm{0.5-8.0~keV}\simeq2\times10^{44}$ erg s$^{-1}$ (uncorrected for obscuration). This is similar to X-ray luminosities observed in DSFGs from the ALESS sample ($L_\mathrm{0.5-8.0~keV}=23\times10^{42}-3\times10^{44}$ erg s$^{-1}$, (cite: Wang2013))[^8]. Even assuming the highest column density for the ALESS sources from (cite: Wang2013), ($N_\mathrm{H}\simeq5\times10^{24}$ cm$^{-3}$), a comparison with carbon ionization model in the vicinity of X-ray bright AGNs of (cite: Langer2015) shows that the X-ray flux in SDP.81 is insufficient to drive the \[C ii\]/FIR deficit on scales beyond few hundred pc (c.f., (cite: Rybak2019)). Finally, circumstantial evidence also disfavours the AGN-driven \[C ii\]/FIR deficit: (1) a single AGN is hard to reconcile with the two similarly deep \[C ii\]/FIR minima separated by $\sim$1 kpc (Fig. [11](#fig:cii_fir_comparison); although an ”Arp 220“-like merging configuration would account for this) and (2) although the CO SLED is more excited in the northern part of the FIR-bright region (as evidenced by the higher CO(10–9) surface brightness, Fig. [2](#fig:reconstructions)), the CO excitation is fully consistent with star-formation, without a need for additional AGN-associated X-ray/cosmic-ray heating.

### C$^+$ thermal saturation

At high gas temperature $T_\mathrm{gas}$, the relative occupancy of the upper/lower C$^+$ fine-structure levels becomes thermally saturated (cite: MunozOh2016) at temperatures higher than the \[C ii\] transition temperature $T_\mathrm{[CII]}=92$ K. As the C$^+$ requires high UV flux to remain ionized, the C$^+$ (and \[C ii\] emission) is constrained to the surface layer ($A_V\leq2$) of the molecular clouds. This allows us to take the PDR surface temperature $T_\mathrm{PDR}$ as indicative of the gas temperature in the \[C ii\]-emitting regions. For a dense gas ($n$ larger than \[C ii\] critical density) and assuming the \[C ii\] line is optically thin, the gas cooling via the \[C ii\] line per hydrogen atom scales as:

$$\begin{equation}
\Lambda_\mathrm{[CII]} = 2.3\times10^{-6} \, k_\mathrm{B} \, T_\mathrm{[CII]} \frac{2}{2+\exp(T_\mathrm{CII}/T_\mathrm{gas})} \frac{\mathrm{C}}{\mathrm{H}},
\label{eq:cii_cooling}
\end{equation}$$

where $k_\mathrm{B}$ is the Boltzmann constant, and C/H the carbon-to-hydrogen number ratio (see (cite: MunozOh2016)).

In the thermally saturated regime (cite: MunozOh2016), the \[C ii\]/FIR ratio is $$\begin{equation}
\frac{L_\mathrm{[CII]}}{L_\mathrm{FIR}} = 2.2\times10^{-3} f_\mathrm{[CII]} \left[\frac{\Sigma_\mathrm{FIR}}{10^{11}~L_\odot~\mathrm{kpc}^{-2}}\right]^{-1/2},
\label{eq:cii_munozoh2016}
\end{equation}$$

where $f_\mathrm{[CII]}$ is the mass of gas traced by the \[C ii\] emission ((cite: MunozOh2016)):

$$\begin{equation}
f_\mathrm{[CII]} = \frac{1}{1+3\times10^4 \alpha_\mathrm{CO} L_\mathrm{CO(1-0)}/L_\mathrm{CII}},
\label{eq:f_cii}
\end{equation}$$

assuming the fraction of gas traced by \[C ii\] or doubly-ionized carbon is negligible. As noted already in Section [4.3](#subsec:CII_FIR), the $L_\mathrm{[CII]}/L_\mathrm{FIR}$ slopes in SDP.81 (this work) and SDP.11 (cite: Lamarche2018) are considerably steeper (approximately -0.7), compared to the -0.5 slope in Equation ([\[eq:cii_munozoh2016\]](#eq:cii_munozoh2016). However, $f_\mathrm{[CII]}$ is likely varying across the source. We quantify this directly via Equation ([\[eq:f_cii\]](#eq:f_cii)), estimating $L_\mathrm{CO(1-0)}$ from the resolved $L_\mathrm{CO(5-4)}$ maps[^9] by using the (cite: Bothwell2013) conversion factor and $\alpha_\mathrm{CO}$ from (cite: CR18) (see Section [4.2.3](#subsec:t_dep)). To ensure a robust $f_\mathrm{[CII}$ estimates and to eliminate the effect of potentially spurious artifacts, we consider the pixels with CO(5–4) S/N$\geq3$, and within the region denoted in Figure [13](#fig:G0_nH). Calculating the $f_\mathrm{[CII]}$ correction for each 200$\times$200 pc pixel, we obtain a mean $f_\mathrm{[CII]}=0.32\pm16$. After correcting the resolved \[C ii\]/FIR deficit for $f_\mathrm{[CII]}$ (Fig. [15](#fig:cii_fir_slopefit), upper panel), we obtain a best-fitting power-law slope of $=-0.55\pm0.02$, in line with the (cite: MunozOh2016) prediction. For comparison, fitting the uncorrected \[C ii\]/FIR data over the same region yields $\alpha=0.65\pm0.01$, in a significant tension with the (cite: MunozOh2016) model.

Given the high PDR surface temperature inferred from PDR modelling (Section [5](#sec:pdr_models)), the good match between the \[C ii\] abundance-corrected \[C ii\]/FIR slope with the (cite: MunozOh2016) predictions, and the limited effects of the positive grain charging and AGN heating, we consider the thermal saturation of the C$^+$ fine-structure levels to be the most likely cause of the strong \[C ii\]/FIR deficit in SDP.81.

![image](./figures/fig15a.png)\
![image](./figures/fig15b.png)\

# Conclusions

We have presented matched-resolution source-plane reconstructions of the \[C ii\], CO (3–2), CO(10–9) and the ALMA Bands 6, 7 and 8 (rest-frame 160-320 $\mu$m) continuum emission in a $z=3.042$ gravitationally lensed, dusty star-forming galaxy SDP.81. Using a visibility-fitting lens modelling code with an adaptive source-plane grid (cite: Rybak2015a), we achieve a median source-plane resolution of $\sim$200 pc. Combining these with the CO(5–4) and CO(8–7) data from (cite: Rybak2015b), we use PDR models of (cite: Kaufman1999; Kaufman2006; Pound2008), to map the physical conditions of the star-forming ISM – in particular, the FUV field strength, gas density and PDR surface temperature – on sub-kpc scales. Compared to other studies of the \[C ii\]/FIR deficit at high redshift, we are able to leverage the resolved CO and FIR continuum observations to characterize the ISM properties in SDP.81 on sub-kpc scales. Our main results are:

- The ALMA Band 8 continuum source-plane surface brightness distribution is consistent with the previously-published Band 6 and Band 7 continuum reconstructions (R15a, (cite: Dye2015; Hezaveh2016)). Fitting for the dust temperature on 200-pc scales, we do not find evidence for a strong dust temperature gradient, and $T_\mathrm{dust}\geq80$ K, in tension with models proposed by (cite: CR18).

- The \[C ii\] emission is significantly more extended than the FIR continuum and CO($J_\mathrm{upp}\geq5$) emission: $\sim$50 per cent of \[C ii\] emission originates outside the FIR-bright region. The \[C ii\] maps reveal an extended, low surface-brightness emission extending to $\sim$4 kpc from SDP.81, providing further evidence to SDP.81 being a merger-induced starburst.

- The CO(3–2) emission is concentrated to the north of the source, with the CO(3–2)/FIR ratio varying rapidly across the source (by $\geq1$ dex). Using the CO(3–2) as a molecular gas tracer, we find an extremely short gas depletion timescale of $t_\mathrm{dep}=10^6-2\times10^7$ Myr, significantly shorter than in most other resolved $t_\mathrm{dep}$ studies in high-redshift DSFGs.

- The CO SLED in SDP.81 is comparable to that of Class I ULIRGs from (cite: Rosenberg2015). Given the data at hand, the CO SLED is consistent with PDR models, without a need for additional energy source (e.g., mechanical heating). Although globally, the CO lines contribute only marginally (few per cent) to the total gas cooling, the CO/\[C ii\] ratio can be as high as 25 per cent for the FIR-bright clumps.

- Comparing the source-integrated (unresolved) de-lensed \[C ii\], CO and FIR emission with PDR models of (cite: Kaufman1999; Kaufman2006; Pound2008), we find FUV field strength $G=10^3~G_0$ and gas density $n$(H)=$10^5$ cm$^{-3}$, significantly higher than the earlier model by (cite: Valtchanov2011). The source-averaged PDR properties inferred from the de-lensed (source-plane) and observed (sky-plane) luminosities are consistent with each other; the differential lensing does not bias the global PDR model significantly.

- Modelling the PDR conditions on 200-pc scales, we find the FUV field strength to vary considerably across the source ($G=10^{2.5}-10^{4.0}~G_0$). In contrast, $n$(H) varies only marginally ($10^{5.0}-10^{5.5}$ cm$^{-3}$). Compared to the unresolved models, the resolved PDR model shows $G$ up to 1 dex higher; this is due to the strong variation of \[C ii\]/FIR ratio (which determines $G$) on sub-kpc scales, the FIR continuum being much more compact than \[C ii\]. The physical conditions averaged over 200-pc scales are comparable to the vicinity of the Trapezium cluster in Orion (cite: Goicoechea2015), underlying the extreme nature of DSFGs, and highlighting a need for more sophisticated radiative transfer models for interpreting the observed line ratios.

- The \[C ii\]/FIR ratio in SDP.81 varies by $\sim$1.5 dex across the source, with a strong \[C ii\]/FIR deficit in the central FIR-bright clumps ($L_\mathrm{[CII]}/L_\mathrm{FIR}=3\times10^{-4}$). Although the \[C ii\] surface brightness generally increases towards the FIR-bright part of the source, it drops at the position of the FIR-bright clumps.

- Given the resolved PDR properties, the most likely cause of the \[C ii\]/FIR deficit in SDP.81 is thermal saturation of the C$^+$ fine-level structure due to strong FUV fields and high PDR surface temperature. After correcting the resolved \[C ii\]/FIR for the fraction of gas traced by the \[C ii\] emission, we find the \[C ii\]/FIR trend to be consistent with the thermal saturation model of (cite: MunozOh2016).

We emphasise that the agreement between the observed line ratios and the simplistic PDR models is largely due to significant systematic uncertainties on the CO(3–2) and CO(10–9) source reconstructions. High-sensitivity observations of these two lines, and additional fainter diagnostics (e.g., HCN and HCO$^+$ lines, CO isotopologues) are necessary to discriminate between e.g., different heating mechanism on sub-kpc scales.

This paper presents a first look into the PDR properties of high-redshift, dusty star-forming galaxies on scales of few hundred pc, and a major improvement on the unresolved studies of DSFGs. Our results reveal the complex nature of DSFGs, with strong spatial variations in \[C ii\]/FIR ratio, the FUV field strength and the PDR surface temperature. By studying the properties of the photon-dominated regions on 200 pc scales, this work bridges the high-redshift starbursts and local studies of large star-forming regions. We make the reconstructed source-plane maps of the CO ladder and \[C ii\] line and the ALMA Bands 6, 7 and 8 continuum (Figures [2](#fig:reconstructions), [17](#fig:reconstructions_appendix_cii)) publicly available at `sdp81.strw.leidenuniv.nl`. We hope this legacy dataset will facilitate independent analysis of the conditions in high-redshift DSFGs on sub-kpc scales.

# Acknowledgements

The authors thank the anonymous referee for their thorough comments and M. Kazadjian and F. Israel for helpful discussions on the radiative transfer modelling, Ana Lopez-Sepulcre for help with ALMA observing setup, and C. Lamarche and K. Litke for sharing their \[C ii\]/FIR data. MR thanks MPA Garching, and S. D. M. White in particular, for the access to computational facilities.

MR and JH acknowledge support of the VIDI research programme with project number 639.042.611, which is (partly) financed by the Netherlands Organisation for Scientific Research (NWO). LG acknowledges support from the Amaldi Research Center funded by the MIUR program "Dipartimento di Eccellenza" (CUP:B81I18001170001). This paper makes use of the following ALMA data: ADS/JAO.ALMA #2011.0.00016.SV, #2016.1.00633.S and #2016.1.01093.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Fig. [14](#fig:G0_nH_comparison) utilizes the corner package by (cite: Corner).

# Lensing reconstructions

Figures [16](#fig:reconstructions_appendix) and [17](#fig:reconstructions_appendix_cii) show the lens modelling results for the Band 8 continuum, velocity-integrated CO(3–2) and CO(10–9) lines, and the reconstructions for individual 40 km s$^{-1}$ \[C ii\] velocity channels. The dirty images are calculated using natural weighting (i.e., each visibility is weighted by $1/\sigma^2$).

![](./figures/fig_A1.png)

![](./figures/fig_A2_1)

![](./figures/fig_A2_2.png)

![](./figures/fig_A2_3.png)

# Estimating the systematic error on the source reconstructions

We reconstructed the lensed source using source-plane regularization to impose a spatial correlation in the source-plane and prevent noise-fitting. However, for low-S/N data, the optimization process might yield high levels of regularization, overly smoothing the source. Here, we assess the systematic uncertainty on the reconstructed source by creating mock ALMA observations for each tracer.

We consider two different source-plane surface brightness distributions: (1) a uniform surface-brightness elliptical source with major/minor axis of 3.4$\times$2.4 kpc (corresponding to the FIR-bright source size at 45 deg inclination) and (2) a surface-brightness distribution matching the FIR luminosity map. These sources are then forward-lensed using the lens model for SDP.81. We then create mock ALMA observations for each tracer by setting the sky-plane flux density to the observed value (see Table [\[tab:image-plane\]](#tab:image-plane)), using the same $uv$-plane coverage and adding the observed noise-per-baseline. Finally, we perform the full lens-modelling procedure for the each dataset. The reconstructed sources are shown in Figures [18](#fig:app_B1) (uniform) and [19](#fig:app_B2) (FIR-like).

First, we estimate the systematic error on the reconstructed source-plane surface brightness distribution, which we use in Section [5.3](#sec:pdr_resolved). Namely, we compare the input surface brightness for the uniform-brightness model (Fig. [18](#fig:app_B1)) to the mean inferred surface brightness, integrated over the extent of the input source. The input and inferred surface brightness values, and the corresponding uncertainites are listed in Table [2](#tab:app_b).

For the continuum data, \[C ii\] and CO(5–4) and (8–7) line, the resulting uncertainty is $\sim$10 per cent, i.e. comparable to the flux calibration uncertainty. However, for the CO(3–2) and (10–9) lines, which are observed at lower S/N, the fractional uncertainty is 65 and 30 per cent, respectively.

Second, we consider the reliability of the inferred source morphology:

- FIR continuum: the reconstructed Bands 6, 7 and 8 data recover the input source structure reliably, including the positions and separation of FIR-bright clumps in Fig. [19](#fig:app_B2).

- CO(3–2): the low S/N and curvature regularization cause the source to be overly extended in the east-west (i.e., radial) direction; the magnification in this direction is $\sim1$. The mean surface brightness is recovered within 20 per cent. However, neither of our mock reconstructions shows the increase in the CO(3–2) luminosity towards the north of the source, seen in the real data (Fig. [2](#fig:reconstructions)). We therefore conclude that the observed variations in the CO(3–2) luminosity (and $\Sigma_\mathrm{H_2}$ in the depletion time analysis) is physical.

- CO(5–4) and (8–7): both the uniform and FIR-like source morphologies are reliably recovered. The surface brightness bias is somewhat larger for the CO(8–7) line due to its lower S/N (15 per cent, compared to 10 per cent for CO(5–4). This confirms the robustness of the source-plane structures from (cite: Rybak2015b), namely the extent of the CO(5–4)/(8–7) emission, and their offsets with respect to each other, and the FIR continuum (Fig. [2](#fig:reconstructions)).

- CO(10–9): the reconstructed source shows spurious structure for both mock source realizations. However, the observed concentration of the CO(10–9) emission to the north of the source is not (spuriously) reproduced in either of the mock source reconstructions; we thus consider it to be a physical. On the other hand, the low-surface brightness CO(10–9) to the south-west in Fig. [2](#fig:reconstructions) is reminiscent of the spurious structures seen in the mock reconstructions. As this faint component contributes negligibly to the CO SLED and PDR modelling results in this paper, we do not exclude it from our analysis. However, we note that given the S/N of the data at hand, this could be a modelling artifact.

- : both the uniform and FIR-like source are reliably recovered. In particular, for the FIR-based source, the positions of the FIR surface brightness maxima are recovered in the reconstructed maps. This confirms that the decline in \[C ii\] surface brightness in these regions seen in the real data is physical, rather than a modelling artifact.

![](./figures/fig_B1.png)

![](./figures/fig_B2.png)

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Tracer | $S_\mathrm{in}$ | $\langle S_\mathrm{out} \rangle$ | $\delta$ |
|  | \[mJy arcsec$^{-2}$\] | \[mJy arcsec$^{-2}$\] | \[per cent\] |
| CO(3-2) | 9.0 | 14.8$\pm$2.8 | 65 |
| CO(5-4) | 24 | 22$\pm$7 | 10 |
| CO(8-7) | 24 | 20$\pm$4 | 20 |
| CO(10-9) | 2.5 | 1.9$\pm$0.5 | 30 |
| \[C ii\] | 91 | 97$\pm$20 | 7 |
| Band 6 cont. | 13.1 | 12.9$\pm$3.8 | 2 |
| Band 7 cont. | 19 | 20$\pm$6 | 5 |
| Band 8 cont. | 55 | 61$\pm$14 | 11 |
| FIR | – | – | 7 |

: Systematic error on the mean source surface brightness $\delta$ estimated from the mock source reconstructions in Fig. [18](#fig:app_B1). The columns list the input (uniform) surface brightness ($S_\mathrm{in}$), the measured mean surface brightness with 1$\sigma$ uncertainties ($\langle S_\mathrm{out} \rangle$), and the fractional systematic error $\delta$.

# Sensitivity of G, n to inferred line ratios

We now assess the robustness of $G$ and $n$ inferred from the PDR modelling to the bias in the reconstructed source-plane brightness distribution. In other words, if the lens modelling introduces a bias in the reconstructed source, how much will this affect the inferred $G$ and $n$? Fig. [20](#fig:pdr_models_sensitivity) shows the $G$-$n$ space isocontours corresponding to 1$\times$ and 2$\times$ of the mean line ratios in SDP.81, using the PDRToolbox models (cite: Kaufman1999). As the systematic error the inferred line ratios is less than unity (Appendix [8](#sec:appendix_B)), a change by a factor of two thus overestimates the actual uncertainty. As the line ratios considered are either between different species or non-neighbouring CO rotational transitions, a change by a factor of two results in relatively minor ($\leq$0.5 dex) shifts in the $G$/$n$(H) space. The only exception is the CO(5–4)/(3–2) ratio; however, given the relatively large associated uncertainty (Fig. [12](#fig:pdr_models_global)), we do not expect the inferred PDR properties to be significantly biased.

![](./figures/fig_C1.png)

[^1]: E-mail: mrybak@strw.leidenuniv.nl

[^2]: $G_0$ denotes the Habing field, $1\,G_0 = 1.6\times10^{-3}$ erg s$^{-1}$ cm$^{-2}$.

[^3]: Note that an older reduction of the *Herschel* \[C ii\] spectra by (cite: Valtchanov2011) yielded a 5$\times$ higher an integrated \[C ii\] line flux.

[^4]: Unlike (cite: Lupu2012) who report a marginal (2$\sigma$) detection of the CO(9–8) line, we consider the CO(9–8) line to be undetected. We adopt a $3\sigma$ upper limit of $0.49\times10^9$ L$_\odot$ for the CO(9-8) line luminosity.

[^5]: although CO(5–4) generally correlates closely with FIR continuum (cite: Daddi2015), and hence does not directly trace $t_\mathrm{dep}$.

[^6]: Due to the shape of the \[C ii\]/FIR isocontours in the $G_0$/$n$(H) plane, a pure $\chi^2$ optimization might yield very low $G_0$ values for the pixels in the densest regions. This would imply extremely dense regions without any star-formation; we discount these solutions as unphysical. The same issue has been encountered by (cite: Diaz2017) in the analysis of nearby ULIRGs; they likewise discard the low $G_0$/$n$ solutions.

[^7]: Note that the $G$, $n$(H) estimates for local star-forming regions are predominantly inferred from the FIR continuum and the \[C ii\], \[O i\] 63/145-$\mu$m lines, rather than the CO lines used in this work, and using a variety of modelling approaches. The sizes of local star-forming regions shown here range between $\sim$0.1 pc to $\sim$100 pc.

[^8]: Based on the (cite: Wang2004) models, the observed hardness ratio in SDP.81 is compatible with both a low-obscuration ($N_\mathrm{H}\simeq10^{21.5}$ cm$^{-3}$, $A_\mathrm{V}\simeq3$) $z=0.299$ solution, and a highly obscured ($N_\mathrm{H}=10^{23}$ cm$^{-3}$, $A_\mathrm{V}\simeq5$) $z=3.04$ solution. We derive the corresponding $A_\mathrm{V}$ factors using the (cite: Guver2009) $N_\mathrm{H}-A_\mathrm{V}$ relation

[^9]: Although using the CO(3–2) emission would give us a more direct probe of CO(1–0), its S/N is insufficient to trace the small-scale structure seen in the \[C ii\]/FIR maps.

</paper>

Write the methods card for this paper.