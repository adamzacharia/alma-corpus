# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...990...36T\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025ApJ...990...36T",
 "title": "Constraining Star Formation in M87 Using Deep Hubble Space Telescope UV Data",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Tamhane, Prathamesh",
 "n_authors": 14,
 "arxiv_id": "2507.13431",
 "doi": "10.3847/1538-4357/adf20d",
 "alma_projects_linked_by_archive": [
  "2013.1.00862.S"
 ]
}
```

Paper text:
<paper>
# Constraining star formation in M87 using deep HST UV data

## Abstract

We analyzed the deepest Hubble Space Telescope (HST) F275W ultraviolet (UV) imaging of M87 to obtain the most robust constraints on its star formation rate (SFR) and star formation history (SFH). After removing the galaxy continuum and globular clusters, we detected an excess of UV point sources near the center. By comparing their colors to young stellar source (YSS) colors generated by stochastically simulated star formation (SF) for various SFRs and SFHs, we ruled out their origin as a UV-upturn population and identified them as YSS. We found an extremely low SFR of $\sim 2\times10^{-5}$ M$_\odot$ yr$^{-1}$ in M87, with evidence of a weak starburst $\sim$125 Myr ago that formed $\sim 1000$ M$_\odot$ of stars. Unlike other cool-core clusters where SF is stronger and directly linked to cooling gas, we found no spatial correlation between YSS and H$\alpha$ filaments. Comparing SF activity with M87’s AGN outburst history suggests that recent AGN feedback events ($\lesssim$12 Myr ago) neither triggered nor were associated with any detectable SF, however, earlier outbursts may have triggered weak starbursts. We detected UV filaments co-spatial with H$\alpha$ filaments with similar lengths and widths, though they are obscured by dust near the center. These filaments are likely powered by metal-line emission from collisional ionization, suggesting ongoing low-level precipitation of the intracluster medium. Our results indicate that AGN feedback has quenched SF significantly in M87 for at least 200 Myr, even though some precipitation persists. Additionally, we identified a hotspot created by the counterjet, with the spectral index also constrained.

# Introduction

Multiphase filaments of cold and warm gas are prevalent in the central galaxies of cool core clusters, appearing in over one-third of all galaxy clusters and groups (cite: mcnamara12; gaspari20; dv22). These filaments—traced by CO (cite: salome03; russell19; olivares19; tamhane22), atomic gas (cite: edge10a), dust (cite: rawle12), warm H$_2$ (cite: donahue11), and H$\alpha$ emission (cite: crawford99; hamer16)—are clear evidence of ongoing cooling from the intracluster medium (ICM), despite the presence of radio-mode AGN feedback. Yet, even in systems with abundant cold gas, star formation is surprisingly weak, typically only $\sim 1$–2% of the classical X-ray cooling rate (cite: mcdonald18). This low star formation efficiency challenges our understanding of the cooling-feedback cycle and BCG growth.

Star formation is the final sink in the cooling process and depends on the balance of gravity, cooling, magnetic fields, turbulence, and bulk flows in the cool core. While strong radio AGN are known to regulate cooling and quench star formation, they may also briefly trigger it (cite: silk13; salome15; tamhane23). Intriguingly, nearly all systems with high SFRs ($>10$ M$_\odot$ yr$^{-1}$) are radio-loud, but many radio-loud cool cores exhibit only weak star formation. Given short AGN duty cycles ($\sim$10–-100 Myr; (cite: shulevski15)), it remains unclear whether strong AGN quickly quench starbursts or whether all such systems experience brief episodes of enhanced star formation.

To investigate this, a detailed study on nearby X-ray cool cores with strong radio AGN but weak SFR is required. We build a complete sample of nearby, strong X-ray cool cores from (cite: Sun09a) and (cite: cavagnolo09), with these criteria: a) $z < 0.02$; b) ($L_X > 10^{42} \, \text{erg s}^{-1}$) for the cool core; c) system $kT >$ 2 keV to only study clusters. There are only four such clusters, Virgo (M87), Centaurus, AWM7, and Perseus (NGC 1275). Among them, only NGC 1275 shows a high SFR ($\sim 20$ M$_\odot$ yr$^{-1}$; (cite: canning10)), consistent with the $\sim 1/3$ fraction of cluster BCGs with SFRs above 5 M$_\odot$ yr$^{-1}$ (cite: mcdonald18). M87, in contrast, hosts a strong radio AGN and a bright filamentary nebula but has an SFR of just $\sim 0.2$–0.3 M$_\odot$ yr$^{-1}$ (cite: hoffer12). It is also closest to us making it an ideal target for studying suppressed star formation in the presence of multiphase gas.

M87 is the BCG of the nearby Virgo cluster (16.5 Mpc; (cite: mei07)) and one of the best-studied radio galaxies. Its cool core, with a central cooling time $<$1 Gyr within 10 kpc (cite: cavagnolo09), shows X-ray cavities, shocks, and cold fronts from recurrent AGN outbursts (cite: forman05; werner10; forman17). Optical and UV observations reveal a network of emission-line filaments and $10^5$ K gas (cite: sparks12; boselli19; anderson18), likely formed through uplift of low-entropy gas and thermal instabilities in the ICM (cite: werner13). While ALMA detects no central CO (cite: boizelle25), molecular gas and dust are present in outer filaments (cite: alighieri13; werner13; simionescu18), confirming the multiphase nature of the system.

Though star formation in M87 is weak, existing very deep HST UV imaging of M87 combined with its proximity allow an unprecedented detailed study of its star formation activity and history. Section [2](#sec:data) describes the HST data and analysis; Section [3](#sec:pt_src_removal) covers point source detection; Section [4](#sec:sfr) presents star formation modeling; Section [5](#filaments) discusses UV-bright filaments; Section [6](#discussion) provides interpretation, and Section [7](#sec:conclusion) concludes the paper. At M87’s distance (16.5 Mpc), 1$^{\prime\prime}$= 80 pc.

| Filter | Instrument | Proposal ID | Obs Year | N$^{\rm a}$ | Tot Exp (ksec) | Mean $\lambda$ (Å) | Area (arcmin$^2$) |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| F275W | WFC3/UVIS | 12989, 14618, 16894 | 2013, 2017–2018, 2022 | 185 | 110.11 | 2719 | 11.98 |
| F606W | WFC3/UVIS | 14618, 16894 | 2017–2018, 2022 | 112 | 40.04 | 5999 | 11.98 |
| F660N | ACS/WFC | 12271 | 2011 | 18 | 13.88 | 6599 | 2.12 |
| F814W | ACS/WFC | 10543, 13731 | 2005–2006 | 268 | 87.21 | 8129 | 12.37 |

Note: $^{\rm a}$: the number of exposures.

# HST observations and Data Analysis

The HST data used in this work were collected with Advanced Camera for Surveys (ACS) and Wide Field Camera 3 (WFC3) instruments focusing on the inner 10 kpc of the galaxy. Observations from multiple filters (F275W, F606W, F660N-Pol, and F814W) provide complementary insights, with the F275W filter highlighting recent star formation, the F660N-Pol filter revealing the optical emission-line nebula, and the F606W and F814W filters showing the evolved stellar population. Together, these filters enable the estimation of stellar ages within the target galaxy and its surroundings. The data used in this paper came from the following proposals — 10543 (PI: Baltz), 12271 (PI: Sparks), 12989 (PI: Renzini), 13731 (PI: Meyer), 14618 (PI: Shara), and 16894 (PI: Neilsen), as summarized in Table [\[tab:obs\]](#tab:obs). Combined, this field is one of the deepest F275W fields with HST.

![](M87_rgb1.png)

To prepare the data for photometric analysis, the images were aligned to the GAIA Data Release 3 catalog (cite: gaia2016; gaia2023) to within 0$''$01 using the TWEAKREG tool from the DRIZZLEPAC package. For data with a small field of view, the HST pipeline drizzled images from each dither position were used in alignment, and the final alignment was back-propagated to the input images using TWEAKBACK within the DRIZZLEPAC. Images in the same band taken on different dates were photometrically normalized using PHOTEQ in the DRIZZLEPAC. Subsequently, the images in each band were drizzled together using ASTRODRIZZLE, which reduced noise, removed cosmic rays in overlapping regions, and produced a consistent pixel scale of 0$''$03 for all bands. The output weight images were set to inverse variance maps to provide accurate noise estimates for photometry using Source Extractor (SExtractor). Additionally, root mean square (RMS) images were generated by taking the inverse square root of the inverse variance maps, allowing for proper uncertainty estimates in the photometric analysis. This pipeline ensured that the data were processed uniformly and optimized for robust photometric measurements in the current study. The final images have a 5$\sigma$ limiting magnitudes of 28.21 mag, 28.01 mag, and 28.78 mag in F275W, F606W and F814W bands, respectively, in 0$''$.5 diameter circular aperture. Figure [1](#fig:rgb) shows the RGB image made by combining F275W (Blue), F606W (Green) and F814W (Red) images after subtracting the diffuse galactic emission modeled using PHOTUTILS[^1] isophote subtraction (see Sec. [3](#sec:pt_src_removal)) and smoothed with a gaussian kernel of 4 pix. All our data products are available at MAST as a High Level Science Product via .

# Point source detection

We performed point source identification on the F275W image using SExtractor, following the subtraction of diffuse galaxy emission. The diffuse emission was removed by iterative isophotal fitting implemented with PHOTUTILS following the example notebooks[^2]. For regions not covered by the elliptical fits, we applied 2D background subtraction using photutils with a 50$\times$50 pixel box size to remove large-scale residuals.

|             |             |                  |                  |                  |
|:-----------:|:-----------:|:----------------:|:----------------:|:----------------:|
|     RA      |     DEC     |       F275       |       F606       |       F814       |
|   (h:m:s)   |   (d:m:s)   |     (ABmag)      |     (ABmag)      |     (ABmag)      |
| 12:30:49.46 | 12:21:44.88 | 24.551$\pm$0.075 | 20.877$\pm$0.002 | 20.437$\pm$0.001 |
| 12:30:51.29 | 12:21:45.98 | 23.649$\pm$0.039 | 20.776$\pm$0.002 | 20.452$\pm$0.001 |
| 12:30:51.88 | 12:21:47.12 | 24.944$\pm$0.157 | 24.219$\pm$0.058 | 24.716$\pm$0.011 |
| 12:30:47.64 | 12:21:47.24 | 25.807$\pm$0.111 | 23.009$\pm$0.007 | 22.596$\pm$0.005 |
| 12:30:47.38 | 12:21:47.85 | 24.731$\pm$0.039 | 17.316$\pm$0.000 | 16.647$\pm$0.005 |

SExtractor operates by first estimating the background across the image, typically using a mesh grid and median filtering to account for large-scale background variations. It then detects sources by identifying contiguous groups of pixels above a specified threshold relative to the background. We adopted a detection threshold of 3$\sigma$. Additionally, the image was smoothed using a 5$\times$5 pixel Gaussian kernel with a standard deviation of 2.5 pixels to enhance the detectability of faint sources. Photometric fluxes were measured in a 0$''$.5 diameter circular aperture centered on each detected source. The aperture size is sufficiently large to detect individual stars and young star clusters, which typically range in size from a few to 20 pc. We performed multi-band photometry using SExtractor’s dual-image mode. Source detection was performed on the F275W image, while photometry was measured on the F606W and F814W images. All images were aligned to ensure consistent astrometry, with errors less than 0$''$.1.

We masked the central AGN and its jet to avoid contamination from bright structures. After source detection, we identified 1384 sources. Table [\[tab:src_summary\]](#tab:src_summary) summarizes source properties. We also compared our sources to the classical novae detected in M87 by (cite: shara23) and (cite: lessing24). We cross-matched our source catalog with their nova catalog using a matching radius of 0$''$.07, identifying 28 common sources across the entire image, which were subsequently removed from our UV source catalog. This radius was chosen to account for astrometric uncertainties while minimizing false matches. Finally, we selected 1219 sources with a signal-to-noise ratio greater than 5 for further analysis. The measured source fluxes were corrected for Galactic extinction using $A_V = 0.0612$ taken from (cite: schlafly11) dust maps and (cite: fitzpatrick99) extinction curve with $R_V = 3.1$ and converted to AB magnitudes.

Figure [2](#fig:cm) shows the color-magnitude diagram (CMD) for all point sources detected in M87 in F275W image. In the left panel, sources are distinctly grouped based on F275W$–$F606W color and F606W magnitude, forming two main populations. We categorize sources with F275W$–$F606W $>$ 2.6 mag and F606W $<$ 25 mag as Group 1 and the remaining sources as Group 2. There are 803 sources in Group 1 and 416 sources in Group 2. Sources in Group 1 with redder colors, likely correspond to globular clusters (GCs) in M87, as previously characterized by (cite: bellini15). However, (cite: bellini15) focused specifically on GCs and used only 26% of the F275W data analyzed here. Our deeper UV data enabled the detection of a bluer population in Group 2, consistent with young stellar sources. Many sources in this group have F606W magnitudes in the range of 24–28. The right panel shows the F275W$-$F814W color and F814W magnitude. The two populations of sources are visible in this CMD as well; however, they appear closer together. The bottom panel of Figure [2](#fig:cm) shows the spatial distribution of sources in M87. The magnitudes of our Group 1 sources are consistent with those of the globular clusters in (cite: bellini15) to within 0.006 mag in all bands.

![](fig2.pdf)

Since distinguishing galaxy-associated and background sources is challenging, we used the Hubble Deep UV (HDUV) Legacy Survey[^3] to estimate background source density. The HDUV (GOODS-N/S) fields offer comparable background conditions due to their depth, high Galactic latitude, and use of the same HST filter. We applied the same source detection and photometry method as for the M87 field for consistency, which is SExtractor with a 3$\sigma$ detection threshold, 50$\times$50 pixel background box, and a 5$\times$5 pixel Gaussian filter.

To evaluate source detection reliability, we conducted completeness tests on both M87 and HDUV images by injecting artificial point sources (FWHM 4–5 px, F275W mag 20–31.5) at random positions and re-running SExtractor. The completeness level was quantified as the ratio of the number of detected artificial sources to the total number of injected sources. M87 image completeness is 94% for sources with mag $<$26.5, 91% at 27.5, and 80% at 28.5. In the HDUV images, completeness is 100% to mag 23.5, 90% at 27, and 35% at 28.5.

In the left panel of Figure [3](#fig:src_num_den), we present the source surface density for both the M87 image and the HDUV fields. The source number densities in the figure are adjusted to account for completeness. The total source number density in M87 is 10 or more times higher than in the HDUV field in every magnitude bin where both data are present. In the HDUV fields, the average total source surface number density is $\sim$ 31 sources per arcmin$^2$. Thus the expected number of background sources in the M87 image is $\sim$ 276 which is $\sim$ 22% of the total detected point sources in the F275W image in M87. The right panel of Figure [3](#fig:src_num_den) shows the radial distribution of source surface number density in logarithmic units as a function of distance from the galaxy’s center without completeness correction. It increases towards the galaxy’s center by approximately $\sim$1 dex for all sources and for sources in Group 1. The Group 2 source number density increases from $\sim$50 arcmin$^{-2}$ at $\sim40''$ to $\sim$320 arcmin$^{-2}$ in the innermost region. This trend indicates an excess of blue sources in the inner region of M87, where most of the increase is in the inner 30$''$ region. There are $\sim$192 sources in this region of which only $\sim$24 sources are expected to be background sources, which is only $\sim$12.5% of the sources. This trend clearly indicates that there is an excess of UV-bright sources in the inner region of the galaxy. There are 67 sources in Group 2 in the inner 30$''$ region with approximately $\sim 12$% expected to be background sources. This still leaves approximately 58 Group 2 sources that we identify as young stellar sources.

We also estimated the contribution of older stars to the diffuse galactic UV light, known as the UV-upturn (cite: Martocchia25). The expected F275W$-$F606W color of UV-upturn sources in M87, from the (cite: Martocchia25) model, is significantly redder ($\sim$ 5.15) compared to the much bluer Group 2 sources ($-1$ to 2.6), confirming that UV-upturn stars do not contribute to the Group 2 population. In Appendix [8](#sec:rad_prof), we discuss the galaxy’s light and color profiles in detail and compare them with the expected UV emission from older stars. Additionally, we compared the colors of blue horizontal branch stars at high metallicity with ages of 10 and 15 Gyr from the (cite: maraston05) model and found that they have F275W$-$F606W colors of 4.17 and 4.30, respectively. Thus, these stars are bluer than UV-upturn-emitting stars but redder than the YSCs detected in M87.

![image](bkg_src_numDens.pdf) ![image](src_radial_distr.pdf)

![](slug_results.pdf)

# Star formation Rate in M87

One of the ways to measure the star formation rate and history is to compare observations to simulations of simple stellar populations in a galaxy with known SFR and SFH. Since star formation in M87 is expected to be very low, we use the code Stochastically Lighting Up Galaxies (SLUG)[^4] (cite: dasilva12; krumholz15). The SLUG code is a stellar population synthesis tool that models star clusters and galaxies by stochastically sampling individual stars and clusters, rather than assuming a continuous initial mass function (IMF). This approach allows the code to capture the effects of stochasticity in young, low-mass star clusters, providing more accurate predictions in the low star formation regime, which traditional synthesis codes based on averaged populations often miss.

For an initial analysis, we ran SLUG simulations in galaxy mode, modeling both continuous and single-burst SFHs with Chabrier IMF (cite: chabrier03), Padova isochrones including pulsating AGB stars, and metallicities of 0.05 and 0.02. For each SFH, we simulated 100 trials using a range of parameters to estimate the expected distribution of star cluster properties under different star formation scenarios. For continuous star formation, we applied a timescale of 200 Myr and SFRs between $10^{-4}$ and $10^{-6}$ M$_\odot$ yr$^{-1}$. For single-burst SFH, we assumed an exponential decay over 10 Myr, with burst peaks ranging from 6 Myr to 200 Myr and total stellar masses from 10$^2$ to $10^4$ M$_\odot$. The simulation generated 35–50 star clusters per trial, consistent with the expected number of Group 2 sources in the inner 30$''$ region, with mean cluster masses between 30–40 M$_\odot$, and HST band magnitudes within the observed range. To determine the best model producing simulated star cluster distribution closely resembling the observed distribution of ‘Group 2’ points, we computed the Bhattacharyya distance between simulated clusters of each parameter set and the observed sources. A Bhattacharyya distance of 0 represents identical source distributions with perfect overlap and larger values indicate diverging distributions with increasingly smaller overlap (cite: bhattacharyya46). We found that a single burst SFH model, a burst 125 Myr ago with 10$^3$ M$_\odot$ stars formed for solar ($Z=0.02$) metallicity tracks gave the best match between observed and simulated sources with a Bhattacharyya distance of 0.17. It implies a time-averaged SFR rate of $\sim 10^{-5}$ M$_\odot$ yr$^{-1}$.

For a more detailed analysis, we used the forward modeling approach presented in (cite: krumholz19) to infer the underlying mass and age distribution of the observed star cluster population. We used their extensive library of simulated star clusters with a Chabrier IMF and solar metallicity, spanning a wide range of cluster ages and masses. Rather than simulating new cluster populations for each assumed SFH, we reweighted each cluster by adjusting its relative probability based on its age to reflect the assumed SFH. We assumed a uniform prior on cluster age, allowing the data to constrain the SFH shape without bias. We then compared the reweighted simulated cluster sample to the observed HST magnitudes using a likelihood function, following the method described in (cite: krumholz19). The resulting posterior probability density distribution is shown in Figure [4](#fig:slug_result). We sampled the posterior probability distribution functions (PDFs) of stellar mass and age 10$^5$ times to infer the median mass, age, and SFR with 1$\sigma$ credible intervals. The total stellar mass formed is $995^{+3446}_{-573}$ M$_\odot$, with a cluster age of $7.1^{+10.0}_{-4.8} \times 10^7$ yr, corresponding to a time-averaged SFR of $1.8^{+1.7}_{-0.4} \times 10^{-5}$ M$_\odot$ yr$^{-1}$. The PDF of cluster age shows a clear peak at $\sim 125$ Myr and drops steeply at younger ages, approaching zero at $\sim 8$ Myr, indicating little to no ongoing star formation. The distribution also shows minor secondary peaks, including one around $\sim 28$ Myr, which coincides with the estimated age of M87’s outer radio lobe (cite: gasperin12; wu25), suggesting a possible link between AGN activity and star formation. The overall shape of the PDF supports a scenario of burst-like or episodic star formation rather than continuous activity.

# UV bright filaments

M87 hosts a complex network of filaments extending several kiloparsecs from the center, observed across X-ray, UV, optical and IR wavelengths (cite: sparks93; sparks09; werner10; werner13; forman17; boselli19). These filaments are also detected in the HST WFC3 F275W and F606W images and are co-spatial with the H$\alpha$ filaments. The left panel of Figure [5](#fig:filaments) shows the filaments detected in the F275W image after subtracting a smooth galaxy model. The right panel shows the similarly processed HST ACS F660N image containing the H$\alpha$ emission, where a 2D galaxy model has been subtracted (as described in Section [3](#sec:pt_src_removal)). In both images, arrows highlight the outer filaments, visible in F275W and H$\alpha$. We also detected a bright feature in the F275W image, located $\sim 2$ kpc south-east of the nucleus, indicated by cyan arrow in Fig. [5](#fig:filaments). This feature is not detected in the F665N image and coincides with the bright radio emission associated with M87’s counterjet. We interpret this as a hotspot created by the interaction of the radio jet with the surrounding medium.

All filaments detected in F275W are close but appear disconnected from each other. The filaments have lengths between 0.7 to 1.2 kpc and FWHM widths $\sim 22$ pc to 50 pc. The N filament appears thicker with a $\sim$ 70 pc width. However, it may be composed of several narrow thread-like filaments as seen in the F665N image in the right panel, where nebular filaments appear twisted. The eastern and southeastern filaments are more thread-like. The two sub-filaments in the E filament are $\sim$ 236 pc (2.9$''$) apart, whereas the narrow subfilaments in the SE filament are $\sim$ 400 pc apart. All of these filaments are co-spatial with the H$\alpha$+\[N II\] filaments shown in the right panel of Fig [5](#fig:filaments). The lengths and widths of UV filaments are consistent with H$\alpha$+\[N II\] filaments. The actual lengths can be longer depending on the relative orientation of the filaments to the line of sight.

The visibility of the outer H$\alpha$ filaments in the HST F275W images, in contrast to the non-detection of the inner H$\alpha$ filaments, is explained by differences in dust extinction. Multiple H$\alpha$ filaments stretch from the nucleus to the north and south, but the inner filaments are not detected in the F275W image. These inner filaments overlap with regions of significant dust absorption, as revealed by the dust absorption contours in the figure obtained from the unsharp-masked F606W image.

We estimated the extinction in these regions in the regions covered by the absorption contours as $A_{606} = -2.5 \, {\rm Log((F606_{mod}-abs(F606_{res}))/F606_{mod})}$, where $\rm F606_{mod}$ and $\rm F606_{res}$ are fluxes extracted from the model image of the galaxy’s continuum and residual image, respectively, within dust absorption regions. $A_V$ and expected $A_{275}$ were calculated using the (cite: cardelli89) extinction law and $R_V = 3.1$. We found an average visual extinction $A_V = 0.015 \pm 0.008$, consistent with previous studies. The expected extinction in the F275W band is $\sim 0.034$, while the observed extinction in F275W, estimated in those same regions following a similar approach as that for F606W image, is $A_{275} = 0.031 \pm 0.028$, which is close to the expected value. This level of extinction is sufficient to obscure the inner H$\alpha$+\[N II\] filaments in the F275W image. The flux ratio between the F275W regions that are cospatial with the bright inner H$\alpha$+\[N II\] filaments (in the original data, before subtracting the galaxy continuum) and the regions at the same radial distance that are not cospatial with the filaments is $\sim 2.9 \pm 0.6$ %. The outer filaments, however, show little to no extinction along the line of sight, which explains their visibility.

# Discussion

## Star formation history and AGN feedback

![](filaments_zoomin.pdf)

Early studies predicted a continuous SFR of up to 1 M$_\odot$ yr$^{-1}$ throughout the lifetime of 1 Gyr of the inner cooling flow in M87 (cite: fabian84). (cite: hoffer12) reported M87’s SFR between 0.2–0.3 M$_\odot$ yr$^{-1}$ based on integrated IR luminosity of the galaxy and an upper limit of 0.1 M$_\odot$ yr$^{-1}$ from GALEX UV flux upper limit. They used SFR-IR scaling relations from (cite: calzetti10) to convert IR fluxes to SFR, which have a scatter of 0.2 dex and are less reliable in the low SFR regime. This estimate is also likely an overestimate because the integrated IR flux is dominated by synchrotron emission from the AGN (cite: boselli10; baes10) which was not taken into account and subtracted from the total flux. In this work, we measured the most robust estimate of the current SFR and SFH in the last 200 Myr in M87 using the deepest HST UV data available. The star formation rate in M87 in the last $\sim 200$ Myr is very low at $\sim10^{-5}$ M$_\odot$ yr$^{-1}$ with a very weak starburst around 125 Myr ago leading to the formation of stars with a total stellar mass of $\sim 1000$ M$_\odot$. No supernovae have been reported in M87 over the last $\sim$ 100 years, which also supports the conclusion that its current star formation rate is low.

M87 has experienced at least three AGN outbursts in the past 200 Myr. The jet corresponds to the current outburst, estimated to be less than 1 Myr old. (cite: forman17) identified a previous outburst 11–12 Myr ago based on X-ray shocks. The absence of stars with comparable ages suggests that these recent outbursts did not trigger new star formation, consistent with the general picture of AGN feedback in massive early type galaxies, where mechanical energy from jets and shocks suppresses cooling and prevents cold gas accumulation (cite: mcnamara07; fabian12). However, the youngest stars observed in M87’s inner regions have ages comparable to the AGN outburst that occurred approximately 100–150 Myr ago, inferred from the extended radio halo (cite: owen00), as shown in Fig. [4](#fig:slug_result). This suggests that this earlier outburst may have triggered a mild starburst. However, updated age estimates of the outer halo place its age between 30–50 Myr (cite: gasperin12; wu25). The small bump in the stellar age PDF at $\sim$30 Myr may correspond to this event. If so, the main peak may correspond to an even earlier AGN outburst, the signatures of which have since faded or are undetectable, or to another mechanism entirely.

The presence of H$\alpha$ filaments and a small amount of molecular gas ($\sim 10^5$ M$_\odot$, (cite: simionescu18)) suggests that localized cooling persists, but not at levels sufficient to sustain substantial star formation. Despite M87’s short central ICM cooling time ($10^7$–$10^8$ yrs; (cite: russell15)) and a classical cooling rate of $\sim$20 M$_\odot$ yr$^{-1}$ (cite: russell13), XMM RGS measurements show much lower cooling rates, $<0.06$ M$_\odot$ yr$^{-1}$ below 0.5 keV (cite: werner10) and 0.8 M$_\odot$ yr$^{-1}$ for an absorbed cooling flow (cite: fabian23), although the RGS coverage does not fully include the cool core.

Star formation in M87 remains highly inefficient, likely due to a combination of mechanical heating, weak residual cooling, and uplift of low-entropy gas. Past AGN outbursts may have uplifted a significant amount of low-entropy gas to larger radii, reducing the supply of cool gas in the central regions (cite: werner10; mcnamara16). Since cold gas is the primary fuel for star formation, its depletion may have led to suppression of star formation in M87. AGN-driven turbulence can also disrupt cooling, preventing the gas from settling into a star forming phase. Sometimes it can lead to sporadic outbursts of low-level star formation and temporally correlated AGN outbursts (cite: voit18; gaspari17). Nonetheless, some level of residual cooling likely persists and may intermittently fuel the central SMBH.

While AGN feedback has largely suppressed star formation in M87, the presence of H$\alpha$ and UV filaments, despite the disruptive effects of the AGN, raises the question of what mechanisms are responsible for their excitation. Understanding how these filaments remain ionized, particularly in the absence of significant star formation, provides crucial insights into the interplay between cooling, feedback, and the surrounding ICM.

## Excitation mechanisms of the filaments in the F275W Band

Although we lack spectroscopic data in the F275W band to directly determine the mechanism powering the filaments at these wavelengths, insights can be drawn from previous studies in the FUV. The Mg II $\lambda2797$, $\lambda2803$ Å doublet would be covered by the F275W filter. The doublet traces neutral gas and can be strong in star forming regions and AGN (cite: guseva13; popovic19). To assess whether ionizing radiation from young stars could explain the observed F275W flux, we modeled a starburst spectrum for a 1000 M$_\odot$ stellar population. Our calculations show that reproducing the UV filament flux would require stars younger than 20 Myr with a total mass of approximately 500–1000 M$_\odot$. However, the lack of young UV sources in the galaxy strongly suggests that the filaments are not photoionized by stars. The observed star formation around the filaments is approximately 100 times lower than what is required to power them. Spectroscopic observations with HST COS of the E filament revealed that it is powered by line emission from collisional excitation, including lines such as C IV, He II, C II, Ly$\alpha$, and N V (cite: sparks12; anderson18). Such emission lines, some of which correspond to $10^5$ – $10^6$ K gas, are expected if the ICM gas is cooling from $\sim10^7$ K to $10^4$ K or even lower temperatures (cite: fabian22). Similar processes likely contribute to the observed brightness of the outer filaments in this band. Simulation of a hidden cooling flow (cite: fabian22) with CLOUDY suggests that the filament may be dominated by Fe and Mg emission lines around 2550–2800 Å (private communication).

We also estimated the contribution of shock ionization by two-photon emission, a process often observed in supernova shocks that can produce near- and far-UV continuum emission. Using the framework and parameters outlined in Appendix B of (cite: bracco20), we estimate the two-photon emission flux in the F275W band to be $\sim$ 3–6 $\times10^{-20}$ erg s$^{-1}$ cm$^{-2}$ Å$^{-1}$ - three orders of magnitude lower than the observed filament flux ($\sim$ 0.8–2 $\times10^{-17}$ erg s$^{-1}$ cm$^{-2}$ Å$^{-1}$). This suggests that two-photon emission is negligible in the filaments and that the observed flux is instead dominated by metal-line cooling from collisionally excited gas. Collisional excitation by the surrounding ICM, as well as mixing processes, may also contribute (cite: canning16).

## Connection between UV sources and optical/UV filaments

Figure [2](#fig:cm) shows the spatial distribution of all detected sources in the galaxy. Visual inspection reveals no apparent correlation between the sources and the optical H$\alpha$ filaments. This contrasts with NGC 1275, where young star clusters are closely associated with optical filaments, strongly suggesting that star formation in NGC 1275 is recent and fueled by cooling gas in cold filaments (cite: canning14). While the filaments in M87 may have formed through the thermally unstable cooling of hot X-ray gas in the ICM, some studies suggest that they could also be remnants of a merger or interaction with a star-forming galaxy (cite: boselli19). Nevertheless, if stars in M87 formed from gas in the filaments, a spatial correlation between the filaments and young stars would be expected. The absence of such a correlation suggests that the young stars in M87 are not associated with the optical filaments. On the other hand, stars decouple from the gas as soon as they form and move ballistically. Therefore, even a velocity difference as small as 10 km s$^{-1}$ between the gas and stars could result in a separation of 1.5 kpc (18$''$) or more over the lifetime of stars making such spatial correlation difficult to observe if present.

The reason for the absence of star formation in these filaments is not well understood. (cite: anderson18) propose that the low atomic gas mass in M87’s filaments, compared to those in NGC 1275 and similar systems, may be a contributing factor. If the filaments form through cooling of the ICM, their increasing density may enhance the magnetic field strength (cite: fabian16). The narrow width of the filaments suggests strong magnetic fields. (cite: werner13) estimated magnetic field strengths of 30–70 $\mu$G in these filaments, whereas equipartition arguments suggest higher values of $\gtrsim$100 $\mu$G (Tamhane et al., in prep). AGN jets may also induce turbulence in the surrounding medium (cite: wittor20), and combined magnetic and turbulent pressure could suppress gravitational collapse, suppressing star formation (cite: federrath12). Additionally, if the filaments are young and still accumulating mass, they may not yet have reached the threshold for star formation. Based on radial velocities from Far-UV lines and their distance from the nucleus, these filaments may be just a few 10$^7$ years old and are likely dynamic systems evolving in mass and temperature (cite: anderson18). Thus, their young age, low gas mass, and strong magnetic and turbulent support may all contribute to the suppression of star formation.

## Counterjet hotspot

We detected a hotspot produced by the counterjet in the F275W image, as shown in the left panel of Fig. [5](#fig:filaments). It is 3–4 times brighter than the filaments and is also visible in the F606W and F814W images. Additionally, we inspected the HST F150LP image from the HST Legacy Archive and found that the hotspot is detected in the far-UV (FUV) as well. We present its spectral energy distribution (SED) using available data.

We measured the hotspot flux within an elliptical aperture with semi-major and semi-minor axes of 2$''$.32 and 0$''$.81, respectively, and a position angle of 12 degrees, ensuring consistent coverage across all HST. We used the galaxy continuum subtracted HST images in the F275W, F606W and F814W bands. For F150LP, we subtracted the local background from an annular region around the hotpot excluding bright sources. The extracted HST fluxes were corrected for Galactic extinction in a similar way as for UV sources. We used the same region to extract flux from the VLA and ALMA images of the hotspot. VLA images were obtained from the NRAO VLA Archive Survey Images page[^5] and ALMA image was obtained from the pipeline processed product from the ALMA data archive with project ID 2013.1.00862.S (PI: Simionescu). No background subtraction was performed for VLA and ALMA data; therefore, the hotspot flux density may include some contribution from the radio lobe. We also used $\sim$ 1 Ms of Chandra data from 46 ACIS observations to constrain the X-ray emission for the hotspot, following standard Chandra ACIS data processing steps and measuring fluxes in the 0.5–1.5 keV and 5–9 keV bands assuming an absorbed powerlaw model with a photon index of 1.7. The hotspot is not detected. All extracted flux densities or limits are listed in Table [1](#tab:hotspot).

Since the hotspot emission is powered by synchrotron radiation (cite: sparks92), we calculated its spectral index $\alpha$ assuming a power-law spectrum $S \propto \nu^{-\alpha}$, where $S$ is the flux density and $\nu$ is the frequency. The optical-to-UV spectral index derived from only HST data is $1.81 \pm 0.04$, which is lower than the previously reported value of $2.23 \pm 0.5$ from S92 using ground-based optical data for the average hotspot emission, as shown by the red line in Fig. [6](#fig:hotspot). The radio spectral index from 1.4 to 214 GHz is $0.96 \pm 0.05$, much shallower than the optical spectral index, indicating a break in the synchrotron spectrum at frequencies between 214 GHz and 372 THz. We did not perform the detailed modeling of the hotspot SED as it is beyond the scope of this paper. As discussed by S92, the light travel time from the nucleus to the hotspot ($\sim 10^4$ years) exceeds the synchrotron lifetime of electrons in the hotspot (a few hundred years), implying that continuous energy injection is required to sustain the emission.

|     Band      |      Freq (Hz)       |        Flux density (Jy)         |
|:-------------:|:--------------------:|:--------------------------------:|
|     VLA L     |  1.42$\times 10^9$   |          0.92$\pm$0.03           |
|     VLA C     |  4.86$\times 10^9$   | (3.58$\pm$0.004)$\times 10^{-1}$ |
|     VLA X     |  8.21$\times 10^9$   | (2.54$\pm$0.01)$\times 10^{-1}$  |
|     VLA U     |  14.96$\times 10^9$  | (1.38$\pm$0.02)$\times 10^{-1}$  |
|     ALMA      |  214.1$\times 10^9$  | (7.90$\pm$0.61)$\times 10^{-3}$  |
|   HST F814W   | 3.73$\times 10^{14}$ | (24.94$\pm$0.01)$\times 10^{-6}$ |
|   HST F606W   | 5.09$\times 10^{14}$ | (15.46$\pm$0.02)$\times 10^{-6}$ |
|   HST F275W   | 1.11$\times 10^{15}$ | (3.50$\pm$0.02)$\times 10^{-6}$  |
|  HST F150LP   | 1.86$\times 10^{15}$ | (1.42$\pm$0.03)$\times 10^{-6}$  |
| Chandra 1 keV | 2.42$\times 10^{17}$ |      $<7.52 \times 10^{-9}$      |
| Chandra 7 keV | 1.69$\times 10^{18}$ |     $<5.64 \times 10^{-10}$      |

: Summary of flux measurement of the hotspot region from HST, ALMA, VLA and Chandra data. The errors are statistical only.

![](hotspot_sed.pdf)

# Conclusion

We analyzed the deepest HST F275W UV imaging of M87 to constrain its star formation rate and history. The unprecedented sensitivity ($>$28 mag) and spatial resolution ($\sim$ 2.5 pc) enabled the detection of individual star clusters. After subtracting the galaxy continuum and removing contributions from globular clusters, novae, and background sources, we identified an excess of UV sources within the central $\sim$30$''$. Using SLUG models, we constrained their ages and masses. We also detected bright, narrow UV filaments co-spatial with H$\alpha$ and multiwavelength filaments.

Our main findings are summarized as follows:

- The time-averaged SFR in M87 is extremely low, $1.8^{+1.7}_{-0.4} \times 10^{-5}$ M$_\odot$ yr$^{-1}$, over four orders of magnitude below the X-ray cooling rate. The age probability distribution peaks around $\sim$125 Myr, consistent with a mild starburst that formed $995^{+3446}_{-573}$ M$_\odot$ of stars.

- Comparison of AGN feedback activity with the star formation history suggests that the most recent AGN outbursts in M87 have not led to significant star formation. However, a small bump in the stellar age distribution around $\sim$30 Myr may indicate a minor episode of star formation potentially triggered by a previous AGN outburst, while the main burst at $\sim$125 Myr may have been triggered by an even earlier AGN outburst.

- UV filaments are dust-obscured near the center ($A_V \sim 0.015$) and not powered by young stars or two-photon emission. Instead, they likely trace cooling ICM gas, emitting via metal-line cooling from collisional ionization or mixing.

- We presented an SED of the hotspot created by the counterjet of M87. Its optical-UV spectral index $1.81 \pm 0.04$, whereas the radio spectral index is $0.96 \pm 0.05$, indicating a break in the synchrotron spectrum.

The extremely low star formation rate in M87 suggests that the radio AGN is efficient in quenching star formation in M87. The temporal overlap between the starburst and an AGN outburst suggests that it can occasionally trigger brief episodes of star formation. However, the modest amount of stars formed suggests that these starbursts are transient and do not lead to sustained star formation. Therefore, such brief starburst phases might be a common feature of the feedback cycle in radio-loud X-ray cool cores. Repeated occurrences of such bursts over cosmic time may contribute to the buildup of low-mass stars in the galaxy’s core. Our results therefore raise the possibility that this mode of star formation favors low-mass star formation (cite: jura77; fabian24), potentially contributing to the bottom-heavy IMFs observed in massive ellipticals, including M87 (cite: vandokkum10; oldham18).

Future deep multiwavelength observations will deepen our understanding of the AGN feedback in M87. Deep James Webb Space Telescope observations in the near-to-far infrared may reveal dust obscured star formation in the center if present and help characterize properties of stellar populations better, while high-resolution UV spectroscopy will help characterize the ionization state of the gas in the filaments. Moreover, X-ray Imaging and Spectroscopy Mission (XRISM) observations of M87 will constrain the ICM turbulence, providing insights on its role in AGN feedback cycle and star formation in cool-core clusters. Additionally, it will help linking the dynamics of the hot ICM to the cold filaments if they are indeed cooling from the hot ICM.

We thank Mark Krumholz for the help on the SLUG code. We thank Andy Fabian and Norbet Werner for comments. Based on observations with the NASA/ESA Hubble Space Telescope obtained from the Data Archive at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. Support for Program number (17037) was provided through a grant from the STScI under NASA contract NAS5-26555. W.F. acknowledges support from the Smithsonian Institution, the Chandra High Resolution Camera Project through NASA contract NAS8-0306, NASA Grant 80NSSC19K0116 and Chandra Grant GO1-22132X. M.G. acknowledges support from the ERC Consolidator Grant *BlackHoleWeather* (101086804). Some/all of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via . This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

# Facilities

HST(WFC3), HST(ACS)

# Software

astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A; astropy22),

Source Extractor (cite: 1996A&AS..117..393B), SLUG (cite: krumholz15), photutils (cite: photutils)

# Radial galaxy light and color profiles

We estimated radial F275W and F606W light profiles for M87 in the inner $\sim$7 kpc region. To do this, we used both a galaxy model generated with PHOTUTILS isophotes and direct measurements from the original image, after masking detected sources, the AGN, and the jet. The resulting profiles are shown in the left panel of Fig. [7](#fig:rad_prof). We found negligible differences between the profiles generated from the model image and those derived directly from the original image; therefore, we present the profiles from the original image. For reference, we also scaled the flux from all detected sources in both bands and overlaid them on the galaxy light profiles. Additionally, we derived the F275W$-$F606W color profile of the galaxy and compared it with UV-upturn models. The black dashed line in the right panel of Fig. [7](#fig:rad_prof) represents the expected color profile of old stars emitting in the UV convolved with M87’s SFH from (cite: Martocchia25).

Our analysis shows that M87 has a mild radial UV flux gradient, similar to its optical flux gradient. The observed F275W$-$F606W color profile gradually reddens from 4.75 at the center to 5.03 at $\sim$5.6 kpc (70$''$). This trend is slightly bluer than predictions from the UV upturn model. The UV upturn model of (cite: Martocchia25) predicts a shallower F275W$-$F606W gradient, with colors changing from 5.43 at the center to 5.15 at 2.4 kpc (30$''$), remaining relatively flat out to 8 kpc (100$''$). These models can produce bluer colors, such as 4.75 for a 12 Gyr old single stellar population with half solar metallicity. However, the central regions of M87 have super solar metallicity (cite: Martocchia25), which leads to a redder UV upturn color in the core, consistent with the expected metallicity dependence of the UV upturn phenomenon.

![image](radial_light_profiles_fromdata.pdf) ![image](radial_color_profile_fromdata.pdf)

natexlab

(ref: anderson18) Anderson, M. E., & Sunyaev, R. 2018, A&A, 617, A123, doi: [`10.1051/0004-6361/201732510`](http://doi.org/10.1051/0004-6361/201732510)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy22) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: baes10) Baes, M., Clemens, M., Xilouris, E. M., et al. 2010, A&A, 518, L53, doi: [`10.1051/0004-6361/201014555`](http://doi.org/10.1051/0004-6361/201014555)

(ref: bellini15) Bellini, A., Renzini, A., Anderson, J., et al. 2015, ApJ, 805, 178, doi: [`10.1088/0004-637X/805/2/178`](http://doi.org/10.1088/0004-637X/805/2/178)

(ref: 1996A&AS..117..393B) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: bhattacharyya46) Bhattacharyya, A. 1946, Sankhyā: The Indian Journal of Statistics (1933-1960), 7, 401. <http://www.jstor.org/stable/25047882>

(ref: boizelle25) Boizelle, B. D., Li, X., LeVar, N., et al. 2025, arXiv e-prints, arXiv:2503.03249. [`https://arxiv.org/abs/2503.03249`](https://arxiv.org/abs/2503.03249)

(ref: boselli10) Boselli, A., Ciesla, L., Buat, V., et al. 2010, A&A, 518, L61, doi: [`10.1051/0004-6361/201014534`](http://doi.org/10.1051/0004-6361/201014534)

(ref: boselli19) Boselli, A., Fossati, M., Longobardi, A., et al. 2019, A&A, 623, A52, doi: [`10.1051/0004-6361/201834492`](http://doi.org/10.1051/0004-6361/201834492)

(ref: bracco20) Bracco, A., Benjamin, R. A., Alves, M. I. R., et al. 2020, A&A, 636, L8, doi: [`10.1051/0004-6361/202037975`](http://doi.org/10.1051/0004-6361/202037975)

(ref: photutils) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2024, , 2.0.2 Zenodo, doi: [`10.5281/zenodo.13989456`](http://doi.org/10.5281/zenodo.13989456)

(ref: calzetti10) Calzetti, D., Wu, S. Y., Hong, S., et al. 2010, ApJ, 714, 1256, doi: [`10.1088/0004-637X/714/2/1256`](http://doi.org/10.1088/0004-637X/714/2/1256)

(ref: canning10) Canning, R. E. A., Fabian, A. C., Johnstone, R. M., et al. 2010, MNRAS, 405, 115, doi: [`10.1111/j.1365-2966.2010.16474.x`](http://doi.org/10.1111/j.1365-2966.2010.16474.x)

(ref: canning16) Canning, R. E. A., Ferland, G. J., Fabian, A. C., et al. 2016, MNRAS, 455, 3042, doi: [`10.1093/mnras/stv2390`](http://doi.org/10.1093/mnras/stv2390)

(ref: canning14) Canning, R. E. A., Ryon, J. E., Gallagher, J. S., et al. 2014, MNRAS, 444, 336, doi: [`10.1093/mnras/stu1191`](http://doi.org/10.1093/mnras/stu1191)

(ref: cardelli89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245, doi: [`10.1086/167900`](http://doi.org/10.1086/167900)

(ref: cavagnolo09) Cavagnolo, K. W., Donahue, M., Voit, G. M., & Sun, M. 2009, ApJS, 182, 12, doi: [`10.1088/0067-0049/182/1/12`](http://doi.org/10.1088/0067-0049/182/1/12)

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: crawford99) Crawford, C. S., Allen, S. W., Ebeling, H., Edge, A. C., & Fabian, A. C. 1999, MNRAS, 306, 857, doi: [`10.1046/j.1365-8711.1999.02583.x`](http://doi.org/10.1046/j.1365-8711.1999.02583.x)

(ref: dasilva12) da Silva, R. L., Fumagalli, M., & Krumholz, M. 2012, ApJ, 745, 145, doi: [`10.1088/0004-637X/745/2/145`](http://doi.org/10.1088/0004-637X/745/2/145)

(ref: gasperin12) de Gasperin, F., Orrú, E., Murgia, M., et al. 2012, A&A, 547, A56, doi: [`10.1051/0004-6361/201220209`](http://doi.org/10.1051/0004-6361/201220209)

(ref: alighieri13) di Serego Alighieri, S., Bianchi, S., Pappalardo, C., et al. 2013, A&A, 552, A8, doi: [`10.1051/0004-6361/201220551`](http://doi.org/10.1051/0004-6361/201220551)

(ref: donahue11) Donahue, M., de Messières, G. E., O’Connell, R. W., et al. 2011, ApJ, 732, 40, doi: [`10.1088/0004-637X/732/1/40`](http://doi.org/10.1088/0004-637X/732/1/40)

(ref: dv22) Donahue, M., & Voit, G. M. 2022, Phys. Rep., 973, 1, doi: [`10.1016/j.physrep.2022.04.005`](http://doi.org/10.1016/j.physrep.2022.04.005)

(ref: edge10a) Edge, A. C., Oonk, J. B. R., Mittal, R., et al. 2010, A&A, 518, L46, doi: [`10.1051/0004-6361/201014569`](http://doi.org/10.1051/0004-6361/201014569)

(ref: fabian12) Fabian, A. C. 2012, ARA&A, 50, 455, doi: [`10.1146/annurev-astro-081811-125521`](http://doi.org/10.1146/annurev-astro-081811-125521)

(ref: fabian22) Fabian, A. C., Ferland, G. J., Sanders, J. S., et al. 2022, MNRAS, 515, 3336, doi: [`10.1093/mnras/stac2003`](http://doi.org/10.1093/mnras/stac2003)

(ref: fabian84) Fabian, A. C., Itoh, H., Stewart, G. C., Canizares, C. R., & Nulsen, P. E. J. 1984, Nature, 307, 343, doi: [`10.1038/307343a0`](http://doi.org/10.1038/307343a0)

(ref: fabian23) Fabian, A. C., Sanders, J. S., Ferland, G. J., et al. 2023, MNRAS, 524, 716, doi: [`10.1093/mnras/stad1870`](http://doi.org/10.1093/mnras/stad1870)

(ref: fabian24) Fabian, A. C., Sanders, J. S., Ferland, G. J., et al. 2024, MNRAS, 531, 267, doi: [`10.1093/mnras/stae1206`](http://doi.org/10.1093/mnras/stae1206)

(ref: fabian16) Fabian, A. C., Walker, S. A., Russell, H. R., et al. 2016, MNRAS, 461, 922, doi: [`10.1093/mnras/stw1350`](http://doi.org/10.1093/mnras/stw1350)

(ref: federrath12) Federrath, C., & Klessen, R. S. 2012, ApJ, 761, 156, doi: [`10.1088/0004-637X/761/2/156`](http://doi.org/10.1088/0004-637X/761/2/156)

(ref: fitzpatrick99) Fitzpatrick, E. L. 1999, PASP, 111, 63, doi: [`10.1086/316293`](http://doi.org/10.1086/316293)

(ref: forman17) Forman, W., Churazov, E., Jones, C., et al. 2017, ApJ, 844, 122, doi: [`10.3847/1538-4357/aa70e4`](http://doi.org/10.3847/1538-4357/aa70e4)

(ref: forman05) Forman, W., Nulsen, P., Heinz, S., et al. 2005, ApJ, 635, 894, doi: [`10.1086/429746`](http://doi.org/10.1086/429746)

(ref: gaia2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1, doi: [`10.1051/0004-6361/201629272`](http://doi.org/10.1051/0004-6361/201629272)

(ref: gaia2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: gaspari17) Gaspari, M., Temi, P., & Brighenti, F. 2017, MNRAS, 466, 677, doi: [`10.1093/mnras/stw3108`](http://doi.org/10.1093/mnras/stw3108)

(ref: gaspari20) Gaspari, M., Tombesi, F., & Cappi, M. 2020, Nature Astronomy, 4, 10, doi: [`10.1038/s41550-019-0970-1`](http://doi.org/10.1038/s41550-019-0970-1)

(ref: guseva13) Guseva, N. G., Izotov, Y. I., Fricke, K. J., & Henkel, C. 2013, A&A, 555, A90, doi: [`10.1051/0004-6361/201221010`](http://doi.org/10.1051/0004-6361/201221010)

(ref: hamer16) Hamer, S. L., Edge, A. C., Swinbank, A. M., et al. 2016, MNRAS, 460, 1758, doi: [`10.1093/mnras/stw1054`](http://doi.org/10.1093/mnras/stw1054)

(ref: hoffer12) Hoffer, A. S., Donahue, M., Hicks, A., & Barthelemy, R. S. 2012, ApJS, 199, 23, doi: [`10.1088/0067-0049/199/1/23`](http://doi.org/10.1088/0067-0049/199/1/23)

(ref: jura77) Jura, M. 1977, ApJ, 212, 634, doi: [`10.1086/155085`](http://doi.org/10.1086/155085)

(ref: krumholz19) Krumholz, M. R., Adamo, A., Fumagalli, M., & Calzetti, D. 2019, MNRAS, 482, 3550, doi: [`10.1093/mnras/sty2896`](http://doi.org/10.1093/mnras/sty2896)

(ref: krumholz15) Krumholz, M. R., Fumagalli, M., da Silva, R. L., Rendahl, T., & Parra, J. 2015, MNRAS, 452, 1447, doi: [`10.1093/mnras/stv1374`](http://doi.org/10.1093/mnras/stv1374)

(ref: lessing24) Lessing, A. M., Shara, M. M., Hounsell, R., et al. 2024, ApJ, 973, 144, doi: [`10.3847/1538-4357/ad70b7`](http://doi.org/10.3847/1538-4357/ad70b7)

(ref: maraston05) Maraston, C. 2005, MNRAS, 362, 799, doi: [`10.1111/j.1365-2966.2005.09270.x`](http://doi.org/10.1111/j.1365-2966.2005.09270.x)

(ref: Martocchia25) Martocchia, S., Boselli, A., Maraston, C., et al. 2025, A&A, 696, A79, doi: [`10.1051/0004-6361/202453001`](http://doi.org/10.1051/0004-6361/202453001)

(ref: mcdonald18) McDonald, M., Gaspari, M., McNamara, B. R., & Tremblay, G. R. 2018, ApJ, 858, 45, doi: [`10.3847/1538-4357/aabace`](http://doi.org/10.3847/1538-4357/aabace)

(ref: mcnamara07) McNamara, B. R., & Nulsen, P. E. J. 2007, ARA&A, 45, 117, doi: [`10.1146/annurev.astro.45.051806.110625`](http://doi.org/10.1146/annurev.astro.45.051806.110625)

(ref: mcnamara12) McNamara, B. R., & Nulsen, P. E. J. 2012, New Journal of Physics, 14, 055023, doi: [`10.1088/1367-2630/14/5/055023`](http://doi.org/10.1088/1367-2630/14/5/055023)

(ref: mcnamara16) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2016, ApJ, 830, 79, doi: [`10.3847/0004-637X/830/2/79`](http://doi.org/10.3847/0004-637X/830/2/79)

(ref: mei07) Mei, S., Blakeslee, J. P., Côté, P., et al. 2007, ApJ, 655, 144, doi: [`10.1086/509598`](http://doi.org/10.1086/509598)

(ref: oldham18) Oldham, L., & Auger, M. 2018, MNRAS, 474, 4169, doi: [`10.1093/mnras/stx2969`](http://doi.org/10.1093/mnras/stx2969)

(ref: olivares19) Olivares, V., Salome, P., Combes, F., et al. 2019, A&A, 631, A22, doi: [`10.1051/0004-6361/201935350`](http://doi.org/10.1051/0004-6361/201935350)

(ref: owen00) Owen, F. N., Eilek, J. A., & Kassim, N. E. 2000, ApJ, 543, 611, doi: [`10.1086/317151`](http://doi.org/10.1086/317151)

(ref: popovic19) Popović, L. Č., Kovačević-Dojčinović, J., & Marčeta-Mandić, S. 2019, MNRAS, 484, 3180, doi: [`10.1093/mnras/stz157`](http://doi.org/10.1093/mnras/stz157)

(ref: rawle12) Rawle, T. D., Edge, A. C., Egami, E., et al. 2012, ApJ, 747, 29, doi: [`10.1088/0004-637X/747/1/29`](http://doi.org/10.1088/0004-637X/747/1/29)

(ref: russell15) Russell, H. R., Fabian, A. C., McNamara, B. R., & Broderick, A. E. 2015, MNRAS, 451, 588, doi: [`10.1093/mnras/stv954`](http://doi.org/10.1093/mnras/stv954)

(ref: russell13) Russell, H. R., McNamara, B. R., Edge, A. C., et al. 2013, MNRAS, 432, 530, doi: [`10.1093/mnras/stt490`](http://doi.org/10.1093/mnras/stt490)

(ref: russell19) Russell, H. R., McNamara, B. R., Fabian, A. C., et al. 2019, MNRAS, 490, 3025, doi: [`10.1093/mnras/stz2719`](http://doi.org/10.1093/mnras/stz2719)

(ref: salome03) Salomé, P., & Combes, F. 2003, A&A, 412, 657, doi: [`10.1051/0004-6361:20031438`](http://doi.org/10.1051/0004-6361:20031438)

(ref: salome15) Salomé, Q., Salomé, P., & Combes, F. 2015, A&A, 574, A34, doi: [`10.1051/0004-6361/201424932`](http://doi.org/10.1051/0004-6361/201424932)

(ref: schlafly11) Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103, doi: [`10.1088/0004-637X/737/2/103`](http://doi.org/10.1088/0004-637X/737/2/103)

(ref: shara23) Shara, M. M., Lessing, A. M., Hounsell, R., et al. 2023, ApJS, 269, 42, doi: [`10.3847/1538-4365/ad02fd`](http://doi.org/10.3847/1538-4365/ad02fd)

(ref: shulevski15) Shulevski, A., Morganti, R., Barthel, P. D., et al. 2015, A&A, 583, A89, doi: [`10.1051/0004-6361/201525632`](http://doi.org/10.1051/0004-6361/201525632)

(ref: silk13) Silk, J. 2013, ApJ, 772, 112, doi: [`10.1088/0004-637X/772/2/112`](http://doi.org/10.1088/0004-637X/772/2/112)

(ref: simionescu18) Simionescu, A., Tremblay, G., Werner, N., et al. 2018, MNRAS, 475, 3004, doi: [`10.1093/mnras/sty047`](http://doi.org/10.1093/mnras/sty047)

(ref: sparks93) Sparks, W. B., Ford, H. C., & Kinney, A. L. 1993, ApJ, 413, 531, doi: [`10.1086/173022`](http://doi.org/10.1086/173022)

(ref: sparks92) Sparks, W. B., Fraix-Burnet, D., Macchetto, F., & Owen, F. N. 1992, Nature, 355, 804, doi: [`10.1038/355804a0`](http://doi.org/10.1038/355804a0)

(ref: sparks09) Sparks, W. B., Pringle, J. E., Donahue, M., et al. 2009, ApJL, 704, L20, doi: [`10.1088/0004-637X/704/1/L20`](http://doi.org/10.1088/0004-637X/704/1/L20)

(ref: sparks12) Sparks, W. B., Pringle, J. E., Carswell, R. F., et al. 2012, ApJL, 750, L5, doi: [`10.1088/2041-8205/750/1/L5`](http://doi.org/10.1088/2041-8205/750/1/L5)

(ref: Sun09a) Sun, M. 2009, ApJ, 704, 1586, doi: [`10.1088/0004-637X/704/2/1586`](http://doi.org/10.1088/0004-637X/704/2/1586)

(ref: tamhane22) Tamhane, P. D., McNamara, B. R., Russell, H. R., et al. 2022, MNRAS, 516, 861, doi: [`10.1093/mnras/stac2168`](http://doi.org/10.1093/mnras/stac2168)

(ref: tamhane23) Tamhane, P. D., McNamara, B. R., Russell, H. R., et al. 2023, MNRAS, 519, 3338, doi: [`10.1093/mnras/stac3803`](http://doi.org/10.1093/mnras/stac3803)

(ref: vandokkum10) van Dokkum, P. G., & Conroy, C. 2010, Nature, 468, 940, doi: [`10.1038/nature09578`](http://doi.org/10.1038/nature09578)

(ref: voit18) Voit, G. M. 2018, ApJ, 868, 102, doi: [`10.3847/1538-4357/aae8e2`](http://doi.org/10.3847/1538-4357/aae8e2)

(ref: werner10) Werner, N., Simionescu, A., Million, E. T., et al. 2010, MNRAS, 407, 2063, doi: [`10.1111/j.1365-2966.2010.16755.x`](http://doi.org/10.1111/j.1365-2966.2010.16755.x)

(ref: werner13) Werner, N., Oonk, J. B. R., Canning, R. E. A., et al. 2013, ApJ, 767, 153, doi: [`10.1088/0004-637X/767/2/153`](http://doi.org/10.1088/0004-637X/767/2/153)

(ref: wittor20) Wittor, D., & Gaspari, M. 2020, MNRAS, 498, 4983, doi: [`10.1093/mnras/staa2747`](http://doi.org/10.1093/mnras/staa2747)

(ref: wu25) Wu, L., Xie, F.-G., Zheng, Q., et al. 2025, arXiv e-prints, arXiv:2505.21929, doi: [`10.48550/arXiv.2505.21929`](http://doi.org/10.48550/arXiv.2505.21929)

[^1]: <https://photutils.readthedocs.io/en/stable/>

[^2]: <https://github.com/astropy/photutils-datasets/tree/main/notebooks/isophote>

[^3]: <https://archive.stsci.edu/prepds/hduv/>

[^4]: <https://bitbucket.org/krumholz/slug2>

[^5]: <http://www.vla.nrao.edu/astro/nvas/>

</paper>

Write the methods card for this paper.