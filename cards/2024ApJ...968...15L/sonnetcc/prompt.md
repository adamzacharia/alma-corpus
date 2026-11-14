# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...968...15L\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...968...15L",
 "title": "JWST and ALMA Discern the Assembly of Structural and Obscured Components in a High-redshift Starburst Galaxy",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Liu, Zhaoxuan",
 "n_authors": 30,
 "arxiv_id": "2311.14809",
 "doi": "10.3847/1538-4357/ad4096",
 "alma_projects_linked_by_archive": [
  "2016.1.01426.S"
 ]
}
```

Paper text:
<paper>
# JWST and ALMA discern the assembly of structural and obscured components in a high-redshift starburst galaxy

## Abstract

We present observations and analysis of the starburst, PACS-819, at $z=1.45$ ($M_*=10^{10.7}$ M$_{
\odot}$), using high-resolution ($0^{\prime \prime}.1$; 0.8 kpc) ALMA and multi-wavelength JWST images from the COSMOS-Web program. Dissimilar to HST/ACS images in the rest-frame UV, the redder NIRCam and MIRI images reveal a smooth central mass concentration and spiral-like features, atypical for such an intense starburst. Through dynamical modeling of the CO (J=5–4) emission with ALMA, PACS-819 is rotation-dominated thus consistent with a disk-like nature. However, kinematic anomalies in CO and asymmetric features in the bluer JWST bands (e.g., F150W) support a more disturbed nature likely due to interactions. The JWST imaging further enables us to map the distribution of stellar mass and dust attenuation, thus clarifying the relationships between different structural components, not discernable in the previous HST images. The CO (J=5–4) and FIR dust continuum emission are co-spatial with a heavily-obscured starbursting core ($<1$ kpc) which is partially surrounded by much less obscured star-forming structures including a prominent arc, possibly a tidally-distorted dwarf galaxy, and a massive clump (detected in CO), likely a recently accreted low-mass satellite. With spatially-resolved maps, we find a high molecular gas fraction in the central area reaching $\sim3$ ($M_{\text{gas}}$/$M_*$) and short depletion times ($M_{\text{gas}}/SFR\sim$ 120 Myrs) across the entire system. These observations provide insights into the complex nature of starbursts in the distant Universe and underscore the wealth of complementary information from high-resolution observations with both ALMA and JWST.

# Introduction

What triggers a starburst galaxy? Outliers (i.e., starburst galaxies) are known to exist that are highly elevated above the typical star-forming population. The correlation between stellar mass ($M_{*}$) and star formation rate (SFR) defines the main sequence (MS) of star-forming galaxies which is our reference for identifying these outliers. Even though their contribution to the global SFR density is believed to be subdominant, even in the distant Universe ($\sim$10%; (cite: rodighiero_lesser_2011)), starbursts still deserve investigation of their physical properties and triggering mechanisms since they represent a crucial phase in the evolution of massive galaxies (cite: Lotz2008; lackner_late-stage_2014).

In the local Universe, these starbursts are the ultra-luminous infrared galaxies (ULIRGs) triggered by major-mergers (cite: solomon_molecular_1997; sanders_ultraluminous_1988). They typical exhibit high specific star formation rates (sSFR = SFR/$M_{*}$), compact molecular gas reservoirs and short gas depletion times ($\tau_{\mathrm{depl}}$ = $M_{\mathrm{gas}}/{\mathrm{SFR}}$).

However, in the distant Universe, whether the physical condition of a starburst is consistent with $z\sim0$ is still being investigated. According to simulations and related theoretical analysis (cite: hernquist_tidal_1989; mihos_ultraluminous_1994; barnes_transformations_1996; dekel_cold_2009; moreno_spatially_2021), the distant starbursts could be triggered by mergers and also by (violent) disk instabilities ultimately due to the high gas fraction in galaxies in the early Universe (cite: tacconi_evolution_2020). In a focused investigation of high-redshift starbursts with ALMA (cite: silverman_higher_2015; silverman_molecular_2018; silverman_concurrent_2018), a higher efficiency of converting gas to stars is found at $z\sim$1.6 (cite: tacconi_phibss_2018; tacconi_evolution_2020). On the other hand, the elevated SFRs of distant starbursts may be due to their enhanced gas fractions, not solely driven by a higher efficiency (cite: scoville_ism_2016; scoville_cosmic_2023).

In addition, some starbursts remain hidden within the Main Sequence (MS), displaying short depletion times (cite: magdis_evolving_2012; elbaz_starbursts_2018; gomez-guijarro_goods-alma_2022) and compact cores in the submillimeter (cite: puglisi_main_2019; puglisi_sub-millimetre_2021). These studies hint that a resolved study associating the stellar and gas is needed. However, a challenge in earlier studies was combining the properties of the ISM with those of stars at spatially resolved scales. This was largely due to the significant obscuration caused by dust, making it difficult to derive spatially resolved attributes from instruments like HST and ground-based telescopes.

With the advent of JWST, it is possible to shed light on the stellar populations hidden behind the dust veil in the distant Universe. Recent JWST research (cite: 2023arXiv230707599L) indicates that starbursts within the MS feature a compact starburst core and a surrounding massive disk with a reduced sSFR. Given these advancements, it’s imperative to reexamine off-MS starbursts using more in-depth, high-resolution multi-wavelength observations to understand better the mechanisms driving their starburst activity and departure from the MS.

In this study, we present an extreme starburst event (11$\times$ above the MS), PACS-819, utilizing high-resolution observations with JWST/NIRCam+MIRI images from COSMOS-Web (cite: casey_cosmos-web_2023) and ALMA Band 6. With a spatial resolution of approximately $0.1^{\prime\prime}$ and high signal-to-noise emission with ALMA, we successfully resolve the carbon monoxide $^{12}$CO transition $5\rightarrow4$ and dust continuum emission, enabling us to delve into the intricate morphology and kinematics of its compact center. Additionally, we identify a clump through its presence in CO emission and its impact on disk kinematics. The JWST observations enable us to produce stellar mass and extinction maps which are important in unveiling the nature of PACS-819, particularly the heavily obscured central region. By investigating this galaxy in such detail, we aim to advance our understanding of the trigger of the distant starbursts. Throughout this work, we follow the standard $\Lambda\mathrm{CDM}$ model by assuming $H_{0}=70 \mathrm{~km} \mathrm{~s}^{-1} \mathrm{Mpc}^{-1}, \Omega_{\Lambda}=0.7, \Omega_{\mathrm{M}}=0.3$. We use a (cite: chabrier_galactic_2003) IMF for estimating the stellar masses and SFRs.

# Target, data and analysis

## PACS-819: a starburst galaxy at $z=1.45$

PACS-819 is a distant starburst galaxy at $z$ = 1.445, detected by *Herschel*/PACS (cite: rodighiero_lesser_2011) and included in our FMOS-COSMOS near-infrared spectroscopic survey of star-forming galaxies with the Subaru Telescope (cite: Kashino2019). Its stellar mass $M_*$ is estimated to be $10^{10.7 \pm 0.1}~M_{\odot}$ from a comprehensive SED fitting conducted by (cite: liu_co_2021). The SFR is estimated to be 533$^{+68}_{-60}$ M$_{\odot}$ yr$^{-1}$, derived from $L_{\text{TIR}}$ (cite: silverman_molecular_2018). These measurements place PACS-819 just over 10 times above the MS (cite: speagle_highly_2014), given t = 4.32 Gyr (z = 1.45). Its starburst-like qualities (i.e., high gas fraction and star-forming efficiency) are based on CO (J=2–1) detections with S/N $>$ 5 using ALMA (cite: silverman_fmos-cosmos_2015). Notably, PACS-819 exhibits signs of a merger in HST F814W, with multiple UV/optical emission regions as depicted in Figure [1](#fig:obs819)a. Along with these properties, the high S/N CO (J=2–1) detection prompted our request for a higher-resolution observation with ALMA.

![](f1.pdf)

## JWST (+HST) imaging from COSMOS-Web

PACS-819 was observed with JWST/NIRCam on April 9th, 2023 as part of the large COSMOS-Web program (PIs: Casey & Kartaltepe; (cite: casey_cosmos-web_2023); GO #1727) of JWST Cycle 1. Images with four NIRCam filters (F115W, F150W, F277W, and F444W) are available. Additionally, on April 10th, PACS-819 was observed with MIRI/F770W. The 5$\sigma$ depths of these observations are 27.13, 27.35, 27.99, 27.83, and 25.70 magnitudes, respectively. The data used in this study is recalibrated by the COSMOS-Web team and reduced to a spatial scale of 30 mas/pixel (Franco in prep.).

To supplement the rest-frame optical filters, we also include previous observations conducted with HST/ACS. PACS-819 was observed in F606W and F814W as a part of the HST Cycle 19 (PI: A. Riess; Program #12461). It was also covered by the COSMOS project (cite: scoville_cosmos_2007) in F814W (cite: koekemoer_cosmos_2007). We utilized the F606W image at 40 mas/pixel, as reduced using the GRIZLI software (cite: 2023zndo...7712834B), and the F814W image at 30 mas/pixel by the COSMOS-Web team following the approaches first described in (cite: koekemoer_candels_2011). Together, this multi-wavelength data set from HST and JWST provides a comprehensive view, crucial for dissecting the complex morphology of this dusty starburst galaxy, particularly in the rest-frame UV and optical.

### SED fitting

To address the source complexity and make full use of the high-resolution images, we employ spatially resolved spectral energy distribution (SED) fitting on a pixel-by-pixel basis using two different software packages: `pixedfit` (cite: abdurrouf_introducing_2021) and `bagpipes` (cite: carnall_inferring_2018). The tool `pixedfit` provides us with a workflow for pixel-to-pixel SED fitting which consists of several individual modules. We utilize `piXedfit_images` to handle the image processing, downgrading all images to match the PSF (point spread function) of F444W and the pixel scale of F606W at 40 mas/pixel. For convolving the images, HST PSFs were generated by averaging the profiles of field stars. The JWST PSFs were generated using PSFEx (cite: 2011ASPC..442..435B). The re-sampled images physically probe the scale of a single resolved component with 4 pixels at 40 mas/pixel resolution. After correcting for galactic extinction, the photometric data cube, including the use of a segmentation map generated by the image module, was passed to the binning module to increase the signal-to-noise of some spatial elements. `piXedfit_bin` (cite: abdurrouf_introducing_2021) bins pixels with similar SED shapes to meet the S/N requirements and can smooth the data. When binning, we requested all bins to have an S/N $\ge$ 10 in F150W, F277W and F444W while the smallest bin size $D_{min,bin}$ is 1 pixel, i.e., no binning, to not sacrifice the number of pixels in the central bright regions for comparison with the ALMA images having a similar resolution. We did not include the dust continuum because it is hard to derive an accurate FIR model with only one band.

We then passed the rebinned photometric cubes to `bagpipes` for SED fitting, implementing a simple model due to the limited number of bands. We introduced 10% systematic uncertainty, as suggested by (cite: abdurrouf_understanding_2017). Since the metallicity has limited impact on our primary objective to assess the stellar mass (cite: osborne_strategies_2024), we fix the metallicity to solar (Z=0.02) to simplify our model when only six bands are available. We first applied a delayed-exponential star-formation history while allowing $\tau$ to vary. Dust modeling follows the method of (cite: calzetti_dust_2000) with $A_V$ varying between 0 and 4 magnitudes since the range in attenuation is likely large as suggested by the color map of PACS-819 (Figure [3](#fig:rgb)). Additionally, we fixed the ionization parameter U for the nebular emission to be $10^{-3}$ as the default. We constructed the UVJ color map with the best-fit SEDs of each bin to confirm that the entire galaxy is star-forming with the classification scheme of (cite: whitaker_star_2012). Then, we further simplified the model to a constant SFH, with a variable turning-on time from 100 Myr to the age of the Universe and a turning-off time at 1 Myr, keeping other priors the same.

## ALMA observations

With our ALMA Cycle 4 program (Proposal #2016.1.01426.S; PI J. Silverman), we acquired high- and low-resolution ALMA observations of three starbursts well above the MS: PACS-819, PACS-830, and PACS-787 (cite: silverman_concurrent_2018). Here, we focus on PACS-819 which was observed with 1.46 hrs of total on-source integration time with 45/40 12 m antennas thus resulting in high-resolution observations having a beam size of $0^{\prime \prime}.12 \times 0^{\prime \prime}.09$ in Band 6 to resolve the CO (J=5–4) emission line ($\nu_{\mathrm{rest}}$ = 576.27 GHz) and the underlying continuum ($\lambda_{\rm obs}$ = 1.3 mm). In the low-resolution configuration, PACS-819 was observed with 22.2 minutes with 42/43 12 m antennas to capture the total flux of the CO (J=5–4) and underlying continuum. The resulting beam size is $0^{\prime \prime}.83 \times 0^{\prime \prime}.68$. The summary of the ALMA observations is provided in Table [1](#tab:observations).

We use the Common Astronomy Software Applications (CASA 4.7.2) to carry out the reduction and recalibration of the raw data. Our measurements and analysis are processed by CASA 6.2.1 and python package `spectral_cube` as described in the following subsections.

### CO (J=5–4)

When constructing the high-resolution image cube, we applied a Briggs (cite: 1995AAS...18711202B) weighting factor of 0.5 to achieve a higher resolution and optimize the sensitivity for substructures in the gas distribution. The cube was subsequently rebinned to 20 $\text{km}\,\text{s}^{-1}$ (4 times the native resolution) to enhance the signal-to-noise ratio. We then collapse our high-resolution CO (J=5–4) detection over its full spectral range by manually setting $\Delta v$ in velocity, as listed in Table [2](#tab:properties2). For the low-resolution cube, we rebinned it to 35 $\text{km}\,\text{s}^{-1}$ (7 times the native resolution) to detect internal structures.

To perform flux measurements, we used the `imfit` task to generate a model based on an elliptical Gaussian function. A point-source component is added to model a potential unresolved central component; however, only 5% of the emission is associated with this component at the 3$\sigma$ significance level. The fit results, excluding the point source component, are listed in Table [2](#tab:properties2).

### Continuum

To identify and exclude emission lines in the continuum analysis, we initially flagged the frequency range of 4$\times$FWHM (Full Width at Half Maximum) centered at the line centroid in the dirty cubes, based on the ALMA data release products. Subsequently, we employed the `tclean` algorithm in multifrequency synthesis (`mfs`, (cite: 1990MNRAS.246..490C)) mode, covering all channels without emission lines. We also used `multiscale` deconvolver to detect the extended emission. For high-resolution images, we utilized the `auto-multithresh` (cite: cornwell_multiscale_2008) mask and opted for natural weighting to maximize the signal-to-noise ratio and a 0.5 Briggs weighting for a higher resolution. The resulting restored beams are 0$^{\prime \prime}$.16 $\times$ 0$^{\prime \prime}$.11 and 0$^{\prime \prime}$.13 $\times$ 0$^{\prime \prime}$.09 respectively. For the low-resolution observation, we only applied the 0.5 Briggs weighting for its high signal-to-noise ratio. The restored beam size is 0$^{\prime \prime}$.83 $\times$ 0$^{\prime \prime}$.69.

To derive morphological information and far-infrared flux, we utilized the `imfit` task in CASA, employing multiple 2D Gaussian models with the natural weighted image. A Gaussian model combined with a point source yielded a satisfactory result to describe its compact core.

## AGN

(cite: huang_diverse_2023) demonstrate that some distant ULIRGs at $z\sim2$ have an AGN contribution. Therefore, we searched for evidence supporting an association of the central starburst with AGN activity in PACS-819. There is no detection in the previous X-ray survey with $Chandra$ and XMM-$Newton$ in the COSMOS field (cite: cappelluti_xmm-newton_2009; civano_chandra_2016; marchesi_chandra_2016). In addition, the SED fitting using mid-infrared AGN SEDs from (cite: mullaney_defining_2011) with global multi-wavelength photometry by (cite: liu_automated_2019) shows no significant AGN contribution. Even though this starburst lies on the star-forming side near the boundary between SFGs and AGNs in the BPT diagram, analyzed in (cite: silverman_higher_2015) with FMOS spectra, we conclude that the AGN activity is not likely to be present.

![image](f3a.pdf) ![image](f3b.pdf)

# Results: I. The structural nature of PACS-819

The mode (i.e., major merger or secular process) through which starburst activity at high redshift ($z\gtrsim1$) occurs has been previously hampered by the lack of rest-frame optical and near-infrared imaging at sufficient spatial resolution. The smooth nature of the gas and dust in high-redshift galaxies (cite: Tadaki2020) imaged by ALMA, has been at odds with rest-frame UV imaging from HST as is the case for PACS-819 (Figure [1](#fig:obs819)). Here, we present results combining the capabilities of both JWST and ALMA on spatially-resolved scales, required to discern its intrinsic nature.

## Unveiling the stellar components with JWST

In Figure [1](#fig:obs819), we present the JWST NIRCam and MIRI images of PACS-819 as provided by the COSMOS-Web survey (cite: casey_cosmos-web_2023). PACS-819 was first described in (cite: silverman_higher_2015) as a galaxy merger based on multiple rest-frame UV components seen in the HST/ACS F814W image, shown in Figure [1](#fig:obs819)a. With JWST, the images clearly show the morphology changing significantly with wavelengths from appearing to be a merger at bluer wavelengths (panels b–c, rest-frame optical), to displaying normal galaxy features at redder wavelengths (rest-frame near-IR), particularly the F277W (panel d) and F444W (panel e) filters. The longer wavelength images include a central mass concentration and symmetric spiral-like features. Such features are similar to local Sa galaxies as opposed to disturbed tidal tails as expected in a major merger, especially for a starburst at $11\times$ above the MS as determined from broad-band photometry in COSMOS including $Herschel$.

To further discern the structures seen in the F444W image, we fit the galaxy with a single Sérsic profile using Galight (cite: 2020ApJ...888...37D) to remove the smooth, symmetric, and dominant component to the emission. In Figure [2](#fig:img_model_fit), we show the results from this exercise. The main galaxy has a Sérsic index of 1.5 and a half-light radius of 1.52 kpc. The residual map demonstrates that the remaining structure is dominated by spiral-like features. Therefore, we conclude that the structures seen in the redder JWST images are indicative of a typical star-forming galaxy with no strong signatures of being in an ongoing major merger. We note that the wider field-of-view, compared to Figure [1](#fig:obs819), shows nearby neighbors which may have had some interaction with PACS-819 (see Discussion and Appendix).

As expected for star-forming galaxies at $z>1$, the galaxy morphology is wavelength-dependent and highly affected by dust obscuration. To illustrate the obscured nature of PACS-819, we combine the F814W, F150W, and F277W filters into an RGB image to represent the blue (rest-frame UV, 3300Å, tracing the unobscured stars), green (rest-frame optical, 6100Å), and red (rest-frame near-infrared, 11000Å, tracing the obscured stellar population) components. As shown in Figure [3](#fig:rgb), we identify three primary components: a central highly obscured galaxy/nucleus in red, a bright blue arc (i.e., a disrupted galaxy or, less likely, a spiral arm or tidal tail based on its stellar mass - see below) to the southwest, and a faint secondary feature to the southeast displayed in green. This structure may be an accreted satellite galaxy or a clump which is present as a consequence of a violent disk instability.

### Spatially-resolved SED fitting and stellar masses of each structure

The nature of the three distinct components, seen in Figure [3](#fig:rgb) is revealed through spatially-resolved SED fitting as described in Sec. [2.2.1](#sec:sed). In Figure [4](#fig:p2p), we present the spatially-resolved maps of (a) stellar mass ($M_*$), (b) $A_V$, (c) and SFR. The spatial resolution ($\sim$0.16 arcsec) is comparable to the ALMA data. In contrast to the images at shorter wavelengths (e.g., HST-ACS/F814W, JWST-NIRCam/F115W; rest-frame $\sim$3300–4500Å) that are clumpy and peak at the southwest arc, the stellar mass distribution is fairly smooth, uniform, and peaks ($\sim 10^{9.5}$ M$_{\odot}$ kpc$^{-2}$) in the central region which is devoid of emission in the HST images. The sum of the stellar mass map is in agreement with that reported previously ($10^{10.7 \pm 0.1}~M_{\odot}$; (cite: liu_co_2021)). The SFR and extinction ($A_V\sim3$) are both highest at the center of the mass map. As a result, the primary galaxy is a central starburst enshrouded in dust (and gas; see Sec. [4](#subsec:sr)) which encompasses the majority of the stellar mass.

We gauge the importance of the ’blue’ and ’green’ features by assessing their stellar mass separately. We adopt the method described in (cite: kalita_rest-frame_2023) to determine the mass of the substructures with aperture SED fitting. Segmentation maps are constructed from the F115W image. We first convolve the image with a 2D Gaussian kernel using an FWHM of 3 pixels and subtract it from the raw image to highlight the clump features. We then set a 3$\sigma$ detection threshold and perform source deblending with the minimum number of connected pixels set to 5. Using `Photutils` (cite: bradley_astropyphotutils_2022), we subtract the ‘background’ contribution from the ’blue’ and ’green’ components with consideration of the contribution from the main and central massive galaxy. Our background estimate is based on annular regions with the two clumps being masked. Since the ’green’ component is rather small ($\sim$1kpc) and close to the central main galaxy, we set a 1-pixel wide annulus located on the edge of the clump to estimate a lower-limit to the background contribution thus estimating an upper-limit for the flux of the ’green’ component. The error on the flux could be large due to the difficulty in accurately assessing the background. Therefore, we set the error to be 10$\%$ of the flux before background subtraction. For the ’blue’ arc, we perform a similar removal of the background and set the flux error to be 10% of the measured value.

We repeat the SED fitting (Sec. [2.2.1](#sec:sed)), using the photometry within the segmentation map of each structure and employ a constant SFH model. In Figure [5](#fig:sed_examples), we show the SEDs for the ’blue’ and ’green’ features with best-fit stellar population models. First, the blue arc (to the southwest) is less massive ($log~M_*=8.81_{-0.13}^{+0.12}$, $\sim$1% of the total mass), hardly noticeable in the mass map (Figure [4](#fig:p2p)), and has relatively lower obscuration ($A_V\sim 0.2$). Given its mass, this structure may be a tidally-distorted dwarf galaxy, which does not significantly alter the morphology of the central massive galaxy. The stellar mass of this ’green’ feature is estimated to be $10^{9.18_{-0.24}^{+0.23}}~M_{\odot}$. However, we conservatively subtracted the background of the ’green’ component that may lead to an overestimate of the mass. Therefore, we claim that the ’green’ feature constitutes at most $\sim$5% of the total mass. Each of these three components, spatially offset and differing in color, is fully explored below in the context of the co-spatial gas and dust emission from ALMA.

![image](f5a.pdf) ![image](f5b.pdf)

![](f6.pdf)

For each panel, the north is up and the east is to the left.

## Galaxy kinematics with ALMA using CO J=5–4

In the distant Universe, typical star-forming galaxies exhibit disk rotation (cite: forster_schreiber_star-forming_2020). However, in the case of extreme starbursts, the kinematic features may differ due to factors such as strong turbulence or merging events that can disrupt ordered disk rotation. To investigate the existence of potential disk features and identify any subcomponents contributing to the enhanced star formation, we began with an analysis of the kinematics by examining the CO (J=5–4) spectrum and producing maps of the emission, both blue- and red-shifted from the line centroid. Following this, we use the 3D-Based Analysis of Rotating Objects via Line Observations ($^{3\mathrm{D}}$BAROLO, (cite: teodoro_3dbarolo_2015)) package to exploit the high spectral resolution (20 $\text{km}\,\text{s}^{-1}$) ALMA CO (J=5–4) observations at high signal-to-noise.

First, we display in Figure [6](#fig:obsalma) the ALMA image (panel a) of the full CO (J=5–4) spatial profile, along with the continuum (panel b). The CO emission is detected at high significance and evidently spatially-extended. The peak of the CO emission is centered on the heavily obscured nucleus as shown in the top panel of Figure [3](#fig:rgb) while a weaker secondary peak is co-spatial with the fainter ’green’ component in the RGB image.

We then employ a non-parametric approach to study the kinematics. For spectral analysis, we utilized the `specflux` task in CASA to extract spectra centered on the CO (J=5–4) emission line, as depicted in Figure [7](#fig:spec). The spectrum exhibits a double-peak profile, characteristic of a rotating disk, which is well-fit with a Gaussian model. The FWHMs of the double-peak profiles for PACS-819 are 190.0 $\text{km}\,\text{s}^{-1}$ and 189.2 $\text{km}\,\text{s}^{-1}$ for the low- and high-frequency wings, respectively. The empirical FWHM of the entire line region was found to be 417.7 $\text{km}\,\text{s}^{-1}$. When fitting the profile, we used the mean, amplitude, and standard deviation as initial estimates from CASA viewer, and employed the `models` function in the `astropy` package to fit the Gaussian models, allowing all parameters to vary.

We use the `spectral-cube` python package to produce two moment 0 maps by collapsing data over both redward and blueward narrow intervals, as depicted as the shaded area in Figure [7](#fig:spec)(a). These intervals were set to be 1.6 $\times$ the standard deviation (80.3 and 80.6 $\text{km}\,\text{s}^{-1}$, respectively) to minimize manual errors. The contours of these collapsed maps, plotted at several $\sigma_{\mathrm{rms}}$ levels, are shown in Figure [7](#fig:spec)(b) on the F277W image, allowing for a side-by-side comparison of different component profiles.

The CO kinematics may be indicative of a rotating disk (Figure [7](#fig:spec)b) as shown by the spatially offset red and blue velocity components. These components are symmetric around the central stellar mass concentration as indicated by the JWST F277W image. There appears to be faint extensions to the CO emission associated with the spiral features; these are seen in the lowest levels of the red contours to the southwest and in the blue contours to the north. Both blue and red contours have considerable extent along the minor axis (northeast to southwest direction), pointing to the possibility of disturbances within the disk.

![](f8.pdf)

![](f9.jpg)

### Model kinematic fitting

To determine whether the observed gas kinematics is truly characteristic of a typical rotating disk, we conduct a parametric kinematic analysis of the data cube with the software, $^{3\mathrm{D}}$BAROLO. This software fits the gas with a tilted ring model in 3D, allowing for a better interpretation of the kinematics of the gas, even with just a few resolved components. We successfully build a 3D disk model, as shown in Figure [8](#fig:barolo_a) with the CO intensity, velocity dispersion given in each column. The rows provide the science data, best-fit model and residual image.

Specifically, we used the SEARCH method to mask the data cube and set the normalization as LOCAL to generate an asymmetry model for our clumpy case. We fixed the system velocity to 0 and input the redshift and rest-frame frequency of our emission line. Due to our S/N limitations, we fixed the RA and Dec of the model and set the initial guess of inclination (INC) and position angle (PA). Then, we employed grid searching in the parameter spaces of INC and PA, with each INC varying by 5 degrees and each PA varying by 15 degrees. We fixed PA as 128 degrees, as it was easier to judge from the velocity field, and searched for the best INC, ultimately fixing it as 45 degrees. We set the rotation velocity $V_{rot}$ as completely free and constrained the dispersion $\sigma_{gas}$ to be higher than 20 $\text{km}\,\text{s}^{-1}$, which is our frequency channel width. $^{3\mathrm{D}}$BAROLO successfully modeled the intensity and velocity field, while dispersion was modeled with less precision due to the challenging nature of modeling it accurately.

Through our analysis, we find clear evidence for bulk rotation resembling a massive disk as shown in the middle panels of Figure [8](#fig:barolo_a). The position-velocity maps (Figure [9](#fig:barolo_b)) show an ’S’-shape curve characteristic of rotation along the major axis. However, there are kinematic anomalies, particularly on the edge of the residual velocity map at lower S/N (Figure [8](#fig:barolo_a)), which may be due to the lopsidedness of the disk or the low S/N and fewer velocity channels in these regions. Also, there is a distinct anomaly seen in the velocity and dispersion maps at the position of the blueshifted component (Figure [7](#fig:spec)b) that is cospatial with the ’green’ JWST component in the RGB image (Figure [3](#fig:rgb)) and likely indicating the existence of a distinct ’clump’. (cite: rizzo_alma-alpaka_2023) analyze the velocity anomalies of PACS-819 in detail and conclude that these anomalies are non-circular features rotating faster or slower than the disk. These features can also be spotted on the maps constructed by our independent study, as shown by the arrow (Figure [9](#fig:barolo_b)).

We report the measurements of the disk parameters for PACS-819 in Figure [10](#fig:parameters). The rotation velocity $V_{rot}$ is about 200 $\text{km}\,\text{s}^{-1}$ and the velocity dispersion $\sigma_{gas}$ is around 40 $\text{km}\,\text{s}^{-1}$, giving a $V_{rot}/\sigma_{gas}$ of around 5, which is rotation-dominated. In agreement with our assessment given above, PACS-819 has kinematic properties broadly consistent with a rotating disk which is typical for high-z star-forming galaxies (cite: schreiber_sinszc-sinf_2018; johnson_kmos_2018; ubler_ionized_2018; wisnioski_kmos3d_2019). Our conclusions align with the results presented by (cite: rizzo_alma-alpaka_2023), which characterize this galaxy as rotation-dominated ($V_{rot}/\sigma_{gas}>6-7$) and with notable non-circular features. Such a feature can be spotted in the region pointed out by the brown arrow in Figure [9](#fig:barolo_b). The gas there is moving slower than the disk rotation predicted by the model, which is interpreted as inflowing or outflowing extra-planar gas in (cite: rizzo_alma-alpaka_2023).

![](f10.pdf)

# Results: II. spatially-resolved properties of the ISM and obscured stellar populations

Here, we integrate the JWST and ALMA images to generate maps of physical properties as follows: (1) sSFR ($SFR/M_*$) using the CO (J=5–4) emission as a tracer for star formation, (2) gas fraction ($M_{gas}/M_*$) with the dust continuum as a proxy for the gas mass, and (3) the gas depletion time ($t_{depl}=M_{gas}/SFR$). The stellar mass map produced by the JWST and HST images is used for the first two of these. In Figure [11](#fig:combined_maps), the maps of these physical properties are shown along with the RGB image and overlaid contours of stellar mass to aid in the visualization. In addition, we examine the location of spatial regions of PACS-819 on the resolved Schmidt-Kennicutt relation (Figure [12](#fig:ks)).

## sSFR

The CO J=5–4 map is used to infer the two-dimensional distribution of SFR based on the relation between CO (J=5–4) luminosity $L'_{CO5-4}$ and the total infrared luminosity $L_{\mathrm{TIR}}$. This is an empirical linear relation that has been well demonstrated (cite: greve_star_2014; daddi_co_2015; liu_high-j_2015; valentino_co_2020). The CO (J=5–4) luminosity is calculated for each pixel as follows:

$$\begin{equation}
L_{\mathrm{CO}}^{\prime}=3.25 \times 10^{7} S_{\mathrm{CO}}~\Delta v~\nu_{\mathrm{obs}}^{-2} ~D_{\mathrm{L}}^{2}~(1+z)^{-3} 
\end{equation}$$

$S_{\mathrm{CO}}$ and $\Delta v$ are the flux and velocity range of the CO (J=5–4) line, with $I_{\mathrm{CO}5-4}$ based on the collapsed map across the full CO (J=5–4) line. $\nu_{\mathrm{obs}}$ is the redshifted frequency of CO (J=5–4) line. $D_{\mathrm{L}}$ is the luminosity distance. We then convert the CO luminosity to TIR luminosity by the linear relation in (cite: daddi_co_2015): $$\begin{equation}
\log L_{\mathrm{TIR}} / L_{\odot}=\log L_{\mathrm{CO}[5-4]}^{\prime}/(\text{K}~\text{km/s}~\text{pc}^2)+2.52.
\end{equation}$$

We note that there is a scatter of 0.2 dex in this relation that we need to take into account here. Using the relation in (cite: kennicutt_star_1998), we derive a total SFR of 626 $\pm$ 142 $M_{\odot}\text { yr }^{-1}$ with the TIR luminosity as the tracer based on the following calibration by (cite: hao_dust-corrected_2011) and (cite: murphy_calibrating_2011): $$\begin{equation}
\log \mathrm{SFR}\left(M_{\odot} \text { year }^{-1}\right)=\log L_{\mathrm{TIR}}\left(\text{erg/s}\right)-43.41 .
\end{equation}$$

Our derived SFR confirms that PACS-819 is a starburst with an SFR elevated by a factor of 11 above the MS (cite: speagle_highly_2014), given t = 4.32 Gyr (z = 1.45), which agrees with the previous $Herschel$ result as 533$^{+68}_{-60}$ $M_{\odot}\text { yr }^{-1}$. By comparing the total flux with the that ($I_{\mathrm{CO}5-4}$=3.22 $\pm$ 0.18) measured from the low-resolution observation ($\sim0.^{\prime \prime}8$), we confirm there is no significant missing flux (within $1\times\sigma_{rms}$) with a more extended configuration. In subsequent analyses, we mask regions with emission at low S/N ($<3\times \sigma_{rms}$).

Prior to merging the SFR and stellar mass maps, the SFR image is convolved by a Gaussian kernel to match the FWHM based on an empirical PSF model for the JWST/F444W filter using stars within the JWST image. The SFR map is then reprojected to the grid of the stellar mass map. Finally, the resolved sSFR map is simply derived from the division of the SFR map by the stellar mass map. As evident in Figure [11](#fig:combined_maps)a, the sSFR map has values around 2–6$\times10^{-8} \,\mathrm{yr}^{-1}$, a timescale typical for starbursts and shorter than MS galaxies ($\sim$Gyr$^{-1}$). These values are a few times higher than the global sSFR ($0.8\times10^{-8} \,\mathrm{yr}^{-1}$). This demonstrates that star formation has a more compact distribution than the stellar mass, indicating that the starburst is happening in the nucleus thus likely growing the bulge. There are variations across the CO-emitting region such as the emission to the southwest which exhibits an enhancement primarily due to the lower stellar mass in that region.

## Gas fraction

To deduce the dust and gas attributes of the starburst, we apply a straightforward blackbody model complemented by conversion factors from existing research. We adopt the black body emission model to infer the dust mass $\mathrm{M_{dust}}$. Utilizing the mass-weighted, average mass-to-light ratio and $\langle U \rangle$=30 estimated by the SED fitting from (cite: liu_co_2021), we subsequently translate this to a dust temperature $\mathrm{T_{dust}}$ of 33 K, assuming $\langle U \rangle = (\text{T/K} /18.9)^{6.04}$as in (cite: magdis_evolving_2012). The dust mass is then estimated using the following:

$$\begin{align}
\label{equation:gas}
M_{\text{dust}} = \frac{S_{\text{obs}} \times D_L^2}{(1 + z) \times B_{\nu_{\text{rest}}}(T) \times k_{\nu_{500\mu \text{m}}}},
\end{align}$$ where ${S_{\text{obs}}}$ represents the continuum flux, $B_{\nu_{\text{rest}}}(T)$ is the blackbody function at rest-frame frequency and temperature T, and the empirical dust mass absorption coefficient $k_{\nu_{\text{rest}}}$ at 500 $\mu m$ is 0.051 $\, \text{m}^2/\text{kg}$, as estimated by the Herschel Reference Survey (cite: clark_empirical_2016).

Given the gas-to-dust ratio of 35 estimated from the study of another starburst of similar redshift (z=1.5) in our survey (cite: silverman_concurrent_2018), the integrated gas mass is approximated at 4.6 $\pm$ 0.3 $\times 10^{10}M_{\odot}$. This is comparable to the gas mass of $4.6 \times 10^{10}M_{\odot}$ assessed using CO (J=2–1) in (cite: silverman_molecular_2018), based on a conversion factor $\alpha_{\mathrm{CO}}=1.3 M_{\odot}/ (\mathrm{K}~\mathrm{km}~\mathrm{s}^{-1}~\mathrm{pc}^2)$.

As with the SFR map, we regrid and smooth the gas map to match the F444W image and then simply divide the gas and stellar maps to produce an image of the gas fraction ($\mu=M_{gas}/M_{*}$). As depicted in Figure [11](#fig:combined_maps)b, the core region exhibits a high gas fraction peaking at $\sim$3, supportive of a large reservoir of gas supplying the central starburst. The pronounced sSFR, in tandem with the elevated gas fraction, hints at an accelerated stellar mass accumulation in the center. In addition, the peak to the southwest is likely due to the lower stellar mass in that region as also seen in the sSFR map.

## Resolved KS relation

With our resolved CO (J=5–4) map serving as the SFR map and the continuum map as a gas mass tracer, we investigate the Schmidt-Kennicutt (KS) law from the inner dense region to the outer regions, generating a resolved KS relation map. The KS law, first introduced by (cite: schmidt_rate_1959) and later refined by (cite: robert_c_kennicutt_global_1998), describes a power-law relation between the surface densities of SFR and gas mass, providing insights into the efficiency of star formation from gas. In order to reduce the influence of beam size, we use the same weighting factor (0.5) when generating the continuum and CO (J=5–4) maps. Thus, after masking the emission under 2$\times \sigma_{rms}$ and converting the CO (J=5–4) and continuum map into the SFR and gas mass map using the method introduced in Section [4](#subsec:sr), we derive the resolved map of the gas depletion time (M$_{gas}$/SFR; Figure [11](#fig:combined_maps)c). We can see various features with slightly differing depletion times. A central elongated region, running almost East to West, of the disk looks uniform at about 120 Myr with two clumps having longer depletion times over 150 Myr. However, we caution that these variations in depletion time are likely to be within the uncertainties and affected by a spatially varying gas-to-dust conversion factor which is beyond the scope of this work.

To display these results on the KS relation (Figure [12](#fig:ks)), we employ circular annuli with radii initially set to 1-4 times half of the major axis of the synthesized beam’s FWHM. In agreement with the above-mentioned depletion times, all our aperture measurements indicate a depletion time around 120 Myr. Therefore, PACS-819 has spatially-resolved depletion times similar to local starbursts and some high-z star-forming galaxies. We observe no significant variation within each annulus, indicating that the disk is forming stars with similar efficiency from the inner to the outer region on average.

# Discussion

We address the different scenarios and processes that can trigger such an extreme starburst event (11$\times$ above the MS) in PACS-819, based on our detailed spatially resolved analysis on the stellar mass, molecular gas and star-forming activity from the multi-wavelength observations with HST, JWST and ALMA.

First, we review the structural nature of PACS-819. The system has three primary components based on their rest-frame colors. A central red component is strongly obscured (i.e., HST-dark) and exhibits intense star-forming activity. This is supported by the $A_V$ map based on spatially-resolved SED fitting (Figure [4](#fig:p2p)b) and the dust continuum emission seen by ALMA (Figure [6](#fig:obsalma)b). As demonstrated by the stellar mass distribution (Figure [4](#fig:p2p)a), this component accounts for majority of the mass and has a rather smooth distribution. The red component exhibits disk-like kinematics, i.e., rotational support with $V_{rot}/\sigma_{gas}\sim4$ based on an analysis using 3D Barolo (Figure [9](#fig:barolo_b)) with clear kinematic anomalies.

The physical properties of the associated structures are important to discern the nature of the full system. The ’green’ component is a less dust-obscured clump evident in both the rest-frame UV/optical and CO (J=5–4) emission with a mass contains up to 5 percent of the entire system. It is kinematically distinct in velocity space and has considerable excess in the dispersion map (Figure [8](#fig:barolo_a)). The blue component is a prominent extended arc peaking in the rest-frame UV and observed in all HST and JWST NIRCam bands but having no counterpart in the CO (5–4) and dust continuum. This component is almost free of dust and has rather low mass with up to 5 percent of the whole system. Given the masses of these structures, we estimate that the main obscured ’red’ component comprises at least 90% of the total stellar mass thus ruling out the possibility that these three components are in an ongoing major merger.

## Minor merger scenario

By disfavouring a direct major merger event, the next likely process is ongoing minor merging. In support, the rest-frame optical and near-infrared emission is highly asymmetric with multiple peaks even in JWST/F150W (rest-frame $\sim6100$ Å). The blue arc-like component seems to be a dwarf galaxy tidally-distorted by the massive red component. The kinematic anomalies seen in the residual velocity maps may be an indication of torques on the gas due to interactions or past impacts of lower mass galaxies. For example, the ’green’ clump may be a recently accreted satellite galaxy which could have contributed to the boost in star formation.

In addition, there is a possibility for the starburst in PACS-819 to be partially induced or assisted by interactions with nearby galaxies. There is spectroscopic evidence for one of the two galaxies to the north to be at a similar redshift to PACS-819 (see the Appendix) thus in close proximity ($\sim$10 kpc away in projection).

## Secular process

Alternatively, a more secular process, such as a violent disk instability (VDI; (cite: dekel_wet_2014; dekel_conditions_2023)) is worth considering given the galaxy morphology, disk rotation, and low mass of the clumps. An in-falling gas stream could introduce a gravitational instability within the disk that can drive gas efficiently to the nuclear region and sustain nuclear starburst activity while keeping the rotating disk configuration intact (cite: dekel_formation_2009; dekel_cold_2009). Such a scenario may explain the significant increase in the velocity dispersion at the location of the ’green’ feature suggestive of turbulence possibly related to gravitational instabilities. The mass of the ’green’ clump is similar to those seen in a recent study with JWST (cite: kalita_near-ir_2024). However, a VDI is not expected to have a velocity offset from the disk itself but rather just show broadening in the dispersion. This lends weight to the likelihood of a past accretion event rather than a VDI.

# Conclusions

In this study, we present JWST and ALMA observations of the distant starburst system PACS-819 (z=1.445), located 11$\times$ above the star-forming MS from $Herschel$ photometry. A unique aspect of our study is the joint use of high-resolution JWST and ALMA observations (approximately 0$^{\prime\prime}$.1 or 0.8 kpc), allowing us to delve into the intricacies of relations between stellar mass, morphology, star formation, dust content, gas properties, and kinematics to address the mechanisms responsible for starburst activity in the gas-rich high-z Universe.

Unexpectedly, we find that PACS-819 has characteristics resembling a more typical star-forming galaxy which is not undergoing a major merger. This is based on the following three observations.

- **Morphology:** JWST NIRCam and MIRI images reveal PACS-819 as having a smooth central mass concentration and spiral-like morphology in the redder bands (e.g., F277W), inconsistent with the emission seen in the bluer bands with JWST and HST.

- **Kinematics:** Based on analysis with 3DBarolo, the 3D distribution of the CO J = 5 – 4 emission exhibits large disk-like rotation with $V_{rot}/\sigma_{gas}\sim5$.

- **Disk substructure:** A distinct feature (i.e., clump), associated the disk, is detected by HST, JWST and ALMA. It’s moderately-obscured and has a stellar mass of $\lesssim10^{9.2\pm0.2}~M_{\odot}$ (at most $5\%$ of the total; see Sec. [3.1.1](#text:mass_struct)). While there are kinematic anomalies within the disk possibly due to past accretion events or ongoing interactions, this structure does not appear to significantly affect the global kinematics of the rotating disk (see further below).

However, there are spatial and kinematic features that lend favor to the influence of a minor merger event and interactions as listed here.

- The emission seen in the bluer JWST bands (e.g., F150W; rest-frame $\sim6100$ Å) is highly asymmetric, has multiple peaks, and includes a prominant blue arc-like feature, as mentioned above, possibly a tidally-distorted dwarf galaxy also undergoing a starburst.

- There are kinematic residuals in the CO J=5–4 velocity and dispersion maps which indicate a disturbed disk, possibly induced by neighboring galaxies. The increase in the dispersion near the location of the ’green’ structure (i.e., a low-mass satellite galaxy) may be evidence of an impact, particularly given the velocity offset which would not be present if the feature was a VDI.

Taken together, the total system is dominated by a nuclear starburst which is building its central bulge through primarily secular processes with assistance from the accretion of a less massive satellite galaxy and interactions with nearby neighbors. This amalgamation of physical effects may illustrate the processes involved in triggering starbursts in the distant gas-rich Universe that lead to further galaxy compaction (cite: tacchella_confinement_2016; kalita_rest-frame_2023). After the starburst core gradually quenches in an inside-out manner (cite: tacchella_evolution_2016), PACS-819 may evolve into a clumpy galaxy with a stable disk and substructures, as in UDF2 (cite: rujopakarn_jwst_2023), and eventually into a massive quiescent galaxy in the nearby Universe.

In addition, we have constructed maps of physical properties (specific star formation rate, gas fraction, depletion time) which further elucidate the nature of the distinct structures present in PACS-819 and show that starburst characteristics (i.e, high gas fraction, short depletion times) persist on smaller physical scales.

- **Three major components within the starburst system:** A composite color (RGB) image - encompassing UV, optical, and near-infrared filters, coupled with CO J = 5 – 4 and FIR observations - uncovers three components: (1) the primary galaxy: massive, dusty, invisible to HST, yet exhibiting strong CO and continuum emission, (2) a secondary clump (as mentioned above): less dusty, of lower mass, aligning with the secondary peak in CO J = 5 – 4, and dominant in the blue JWST bands, and (3) a UV-bright arc likely representing a tidally-disturbed galaxy.

- **Spatial distribution of the obscured gas, dust and star formation:** The gas and dust distribution are centrally-concentrated mainly within the central kpc ($r_{eff}=1.1\pm0.1$ kpc) based on the FIR continuum image. This is supported by the CO J=5—4 emissions ($r_{eff}=1.2\pm0.1$ kpc), which is known to correlate well with total infrared luminosity and thus ongoing star formation.

- **Differential distribution in resolved sSFR and gas fraction maps:** With pixel-to-pixel SED fitting tools and JWST imaging, we construct a resolved stellar mass map to produce that of gas fraction and sSFR. The gas fraction is also centrally concentrated, with a significantly high value $\mu_{\mathrm{gas}}$ (over 3), thus indicating the stellar buildup of the core on rapid timescales (high sSFR), while the integrated gas fraction is $\sim1$, compatible to normal star-forming galaxies at similar redshifts. There is a further enhancement in the gas fraction and sSFR associated with the blue arc (i.e., a tidally-disturbed dwarf galaxy).

- **High and uneven distributed SFE:** Based on our resolved analysis, the whole system has a short depletion time of $\sim120$ Myr, aligning with local starbursts and high-z star-forming galaxies. Within the resolved SFE map, there are variations to be further explored.

To conclude, PACS-819 is clearly undergoing a nuclear starburst that is likely to be rapidly growing its bulge. Whether such a compact and highly starforming nucleus can occur without a major merger is still an open question. If realized, secular processes would alter our view of the physical drivers of starburst phenomenon in the gas-rich Universe at $z>1$. Most likely, the recent accretion of a low-mass satellite and interactions with neighboring galaxies may be responsible for destabilizing a disk and driving gas to the center thus powering a starburst. In any case, our study underscores the importance of high-resolution multi-wavelength data to further understand the nature and evolution of distant star-forming galaxies.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Configuration | Obs. Date | Band | Central Frequency | Band Width | On-source Time | Beam Size$^{b}$ | $\sigma_{\mathrm{rms}}$$^{b,c}$ |
|  | (UT) |  | (GHz) | (GHz) | (minutes) | ($^{\prime \prime}$) | (mJy beam$^{-1}$) |
| Compact | 2016 Dec 16 & | 6 | 217.99, 220.99 | 2.000, 2.000 | 11.1 + 11.1 | 0.83 $\times$ 0.69 | 0.02 |
|  | Apr 13 | 6 | 233.60, **235.60**$^{a}$ | 2.000, 1.875 |  | 0.84 $\times$ 0.70 | 0.54 |
| Extended | 2017 Aug 24 & | 6 | 217.99, 220.99 | 2.000, 2.000 | 35.4 + 16.9 + 35.4 | 0.13 $\times$ 0.09 | 0.01 |
|  | Sep 02 | 6 | 233.60, **235.60**$^{a}$ | 2.000, 1.875 |  | 0.12 $\times$ 0.09 | 0.41 |

: Summary of ALMA observations

Table notes: $^{a}$ The central frequency in bold indicates the spectral window where the CO line falls. $^{b}$ The first and second rows are read from the reconstructed continuum and cube with Briggs 0.5 weighting, respectively. $^{c}$ The rms noise of the cube is calculated from the channel where the line is strongest and the widths of the channel are 35 and 20 $\text{km}\,\text{s}^{-1}$.

| Quantity | PACS-819 | Units | Notes |
|:--:|:--:|:--:|:--:|
| $S_{1.3\text{mm}}$ | 0.639 $\pm$ 0.048 | $\mathrm{mJy}$ | total flux of the underlying continuum |
| $r_{\text{cir,CO}}$ | 1.21 $\pm$ 0.11 | kpc | Effective radius of CO (5-4); circularized |
| $r_{\text{cir,con}}$ | 1.08 $\pm$ 0.11 | kpc | Effective radius of continuum; circularized |
| $i_{\text{CO}}$ | $45 \pm 10$ | degrees | Disk inclination (CO) |
| $i_{\text{con}}$ | $30 \pm 20$ | degrees | Disk inclination (Continuum) |
| $I_{\mathrm{CO}5-4}$ | 2.92 $\pm$ 0.31 | $\mathrm{Jy}\,\mathrm{km}\,\mathrm{s}^{-1}$ | CO (5-4) intensity |
| $\Delta v$ | 920.0 | $\mathrm{km}\,\mathrm{s}^{-1}$ | Velocity range over which $I_{\mathrm{CO}5-4}$ is measured |
| $v_{\mathrm{FWHM}}$ | 417.7 | $\mathrm{km}\,\mathrm{s}^{-1}$ | CO velocity FWHM |
| $M_{\text{ISM}}$ | $4.6\pm0.3\times10^{10}$ | $M_{\odot}$ | From 1.3mm continuum |
| $\mu_{\text{gas}}$ | 1.0 $\pm$ 0.1 |  |  |
| $L'_{\mathrm{CO}(5-4)}$ | $1.3\pm0.1\times10^{10}$ | $\mathrm{K}\, \mathrm{km}\, \mathrm{s}{ }^{-1} \,\mathrm{pc}^{2}$ | CO (5-4) luminosity |
| SFR | 626 $\pm$ 142 | $M_{\odot}\, \mathrm{yr}^{-1}$ | From CO (5-4) |
| $\tau_{\mathrm{depl}}$ | 73 $\pm$ 10 | Myr |  |

: Measurements and derived properties

# Local environment of PACS-819

In the proximity of PACS-819, there are two galaxies within a 2$^{\prime\prime}$ radius. According to the COSMOS2020 catalog (cite: weaver_cosmos2020_2022), they are likely foreground galaxies with photometric redshifts as $0.396^{+0.008}_{-0.005}$ and $1.292^{+0.017}_{-0.016}$ estimated with `EAZY` (cite: brammer_eazy_2008) and $0.405^{+0.010}_{-0.010}$ and $1.222^{+0.051}_{-0.073}$ with `LePhare` (cite: arnouts_measuring_2002; ilbert_accurate_2006), based on the comprehensive photometric data set available in COSMOS. In fact, the former galaxy is reported to have a spectroscopic redshift of 1.445 based on a slit spectrum acquired with Keck/DEIMOS (cite: masters_complete_2019) and labeled as a serendipitous detection. After visual inspection, there is no other galaxy detected in CO or the continuum in the ALMA field of view within the observing channels. The non-detection agrees with the properties given in the COSMOS2020 catalog which shows these galaxies might be quiescent ($M_*\sim10^{10}~M_{\odot}$, SFR $<10 M_{\odot}\, \mathrm{yr}^{-1}$).

Fortunately, the area around PACS-819 has been observed with HST G141 GRISM (PI: Lemaux; #16684). We follow the `Grizli` pipeline (cite: 2023zndo...7712834B) to acquire and process the data. The reduced 2D spectra and best-fit models are presented in Figure [13](#fig:grism). Unfortunately, we encountered some issues in determining their spectroscopic redshifts when fitting the extracted spectra with `EAZY`. First, the galaxies are very close (within two arcsecs), so the nearby galaxies are strongly contaminated by the bright H$\alpha$ line emitted by the extreme starburst PACS-819. Second, the H$\alpha$ feature is at the edge of the field of view thus reducing the data quality and making it hard to discriminate any intrinsic spectral features and contamination. For PACS-819-L with a serendipitous detection, the derived spectroscopic redshift ($z=1.568$) is different from PACS-819 ($z=1.445$) even though there may be strong contamination. This disagrees with the spec-z reported for the serendipitous Keck/DEIMOS catalog. In any case, there is no evidence that this galaxy is at an equivalent redshift to PACS-819 to claim that there is an ongoing interation. The fitting result for the other galaxy (PACS-819-R) shows that it has the same spec-z ($z_{spec}=1.4478$) as PACS-819. The $L_{H_{\alpha}}$ from the fit is $9.8\pm1.8\times10^{41}~\mathrm{erg/s/cm^2}$, about two magnitudes lower than PACS-819, indicating this pair might be a dry merger. However, the lineup direction across it and PACS-819 is accidentally perpendicular to the direction of dispersion. Therefore, we can only state that the brighter nearby neighbor is likely to be at the same redshift as PACS-819 thus potentially undergoing an interaction with all members of a galaxy group.

We thank the anonymous referee for their constructive comments. Z.L. sincerely thanks J.S., E.D., and A.R. for their guidance and assistance. Z.L. would extend his sincere gratitude to Frederic Bournaud, Connor Bottrell, Andy Bunker, Y. Sophia Dai, Jing Wang, and Mingyang Zhuang for the scientific discussions and Shenli Tang, Qinyue Fei, Yi Xu, and Fengwu Sun for technical discussions. Z.L. is grateful to Yali Shao and Lihwai Lin for sharing the data points used in Figure [12](#fig:ks).

Kavli IPMU was established by World Premier International Research Center Initiative (WPI), MEXT, Japan. Z.L. is supported by the Global Science Graduate Course (GSGC) program of the University of Tokyo. J.S. is supported by JSPS KAKENHI (JP22H01262) and the World Premier International Research Center Initiative (WPI), MEXT, Japan. This work was supported by JSPS Core-to-Core Program (grant number: JPJSCCA20210003). G.E.M acknowledges the Villum Fonden research grant 13160 “Gas to stars, stars to dust: tracing star formation across cosmic time,” grant 37440, “The Hidden Cosmos,” and the Cosmic Dawn Center of Excellence funded by the Danish National Research Foundation under the grant No. 140. AP is supported by an Anniversary Fellowship at University of Southampton. SG acknowledges financial support from the Villum Young Investigator grant 37440 and 13160 and the Cosmic Dawn Center (DAWN), funded by the Danish National Research Foundation (DNRF) under grant No. 140.

Some of the data products presented herein were retrieved from the Dawn JWST Archive (DJA). DJA is an initiative of the Cosmic Dawn Center, which is funded by the Danish National Research Foundation under grant No. 140. Some of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via . This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01426.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

HST(STIS), JWST(STIS), ALMA(NRAO, ESO, NAOJ, ASIAA and Chile)

# Software

$^{3\mathrm{D}}$BAROLO, astropy, bagpipes, CASA, EAZY, Grizli, photutils, pixedfit, spectral-cube, uncertainties.

natexlab

(ref: abdurrouf_understanding_2017) Abdurro’uf, & Akiyama, M. 2017, Monthly Notices of the Royal Astronomical Society, 469, 2806, doi: [`10.1093/mnras/stx936`](http://doi.org/10.1093/mnras/stx936)

(ref: abdurrouf_introducing_2021) Abdurro’uf, Lin, Y.-T., Wu, P.-F., & Akiyama, M. 2021, ApJS, 254, 15, doi: [`10.3847/1538-4365/abebe2`](http://doi.org/10.3847/1538-4365/abebe2)

(ref: arnouts_measuring_2002) Arnouts, S., Moscardini, L., Vanzella, E., et al. 2002, Monthly Notices of the Royal Astronomical Society, 329, 355, doi: [`10.1046/j.1365-8711.2002.04988.x`](http://doi.org/10.1046/j.1365-8711.2002.04988.x)

(ref: barnes_transformations_1996) Barnes, J. E., & Hernquist, L. 1996, ApJ, 471, 115, doi: [`10.1086/177957`](http://doi.org/10.1086/177957)

(ref: 2011ASPC..442..435B) Bertin, E. 2011, in Astronomical Society of the Pacific Conference Series, Vol. 442, Astronomical Data Analysis Software and Systems XX, ed. I. N. Evans, A. Accomazzi, D. J. Mink, & A. H. Rots, 435

(ref: bothwell_high-resolution_2010) Bothwell, M. S., Chapman, S. C., Tacconi, L., et al. 2010, Monthly Notices of the Royal Astronomical Society, 405, 219, doi: [`10.1111/j.1365-2966.2010.16480.x`](http://doi.org/10.1111/j.1365-2966.2010.16480.x)

(ref: bradley_astropyphotutils_2022) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2022, Zenodo, doi: [`10.5281/zenodo.6825092`](http://doi.org/10.5281/zenodo.6825092)

(ref: 2023zndo...7712834B) Brammer, G. 2023, grizli, 1.8.2, Zenodo, Zenodo, doi: [`10.5281/zenodo.7712834`](http://doi.org/10.5281/zenodo.7712834)

(ref: brammer_eazy_2008) Brammer, G. B., Dokkum, P. G. v., & Coppi, P. 2008, ApJ, 686, 1503, doi: [`10.1086/591786`](http://doi.org/10.1086/591786)

(ref: 1995AAS...18711202B) Briggs, D. S. 1995, in American Astronomical Society Meeting Abstracts, Vol. 187, 112.02

(ref: calzetti_dust_2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: cappelluti_xmm-newton_2009) Cappelluti, N., Brusa, M., Hasinger, G., et al. 2009, A&A, 497, 635, doi: [`10.1051/0004-6361/200810794`](http://doi.org/10.1051/0004-6361/200810794)

(ref: carilli_imaging_2010) Carilli, C. L., Daddi, E., Riechers, D., et al. 2010, ApJ, 714, 1407, doi: [`10.1088/0004-637X/714/2/1407`](http://doi.org/10.1088/0004-637X/714/2/1407)

(ref: carnall_inferring_2018) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, Monthly Notices of the Royal Astronomical Society, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: casey_cosmos-web_2023) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31, doi: [`10.3847/1538-4357/acc2bc`](http://doi.org/10.3847/1538-4357/acc2bc)

(ref: chabrier_galactic_2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: civano_chandra_2016) Civano, F., Marchesi, S., Comastri, A., et al. 2016, ApJ, 819, 62, doi: [`10.3847/0004-637X/819/1/62`](http://doi.org/10.3847/0004-637X/819/1/62)

(ref: clark_empirical_2016) Clark, C. J. R., Schofield, S. P., Gomez, H. L., & Davies, J. I. 2016, Monthly Notices of the Royal Astronomical Society, 459, 1646, doi: [`10.1093/mnras/stw647`](http://doi.org/10.1093/mnras/stw647)

(ref: 1990MNRAS.246..490C) Conway, J. E., Cornwell, T. J., & Wilkinson, P. N. 1990, MNRAS, 246, 490

(ref: cornwell_multiscale_2008) Cornwell, T. J. 2008, IEEE J. Sel. Top. Signal Process., 2, 793, doi: [`10.1109/JSTSP.2008.2006388`](http://doi.org/10.1109/JSTSP.2008.2006388)

(ref: daddi_co_2015) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46, doi: [`10.1051/0004-6361/201425043`](http://doi.org/10.1051/0004-6361/201425043)

(ref: dekel_wet_2014) Dekel, A., & Burkert, A. 2014, Monthly Notices of the Royal Astronomical Society, 438, 1870, doi: [`10.1093/mnras/stt2331`](http://doi.org/10.1093/mnras/stt2331)

(ref: dekel_formation_2009) Dekel, A., Sari, R., & Ceverino, D. 2009a, ApJ, 703, 785, doi: [`10.1088/0004-637X/703/1/785`](http://doi.org/10.1088/0004-637X/703/1/785)

(ref: dekel_conditions_2023) Dekel, A., Tziperman, O., Sarkar, K. C., et al. 2023, Monthly Notices of the Royal Astronomical Society, 521, 4299, doi: [`10.1093/mnras/stad855`](http://doi.org/10.1093/mnras/stad855)

(ref: dekel_cold_2009) Dekel, A., Birnboim, Y., Engel, G., et al. 2009b, Nature, 457, 451, doi: [`10.1038/nature07648`](http://doi.org/10.1038/nature07648)

(ref: 2020ApJ...888...37D) Ding, X., Silverman, J., Treu, T., et al. 2020, ApJ, 888, 37, doi: [`10.3847/1538-4357/ab5b90`](http://doi.org/10.3847/1538-4357/ab5b90)

(ref: elbaz_starbursts_2018) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110, doi: [`10.1051/0004-6361/201732370`](http://doi.org/10.1051/0004-6361/201732370)

(ref: forster_schreiber_star-forming_2020) Förster Schreiber, N. M., & Wuyts, S. 2020, ARA&A, 58, 661, doi: [`10.1146/annurev-astro-032620-021910`](http://doi.org/10.1146/annurev-astro-032620-021910)

(ref: schreiber_sinszc-sinf_2018) Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, ApJS, 238, 21, doi: [`10.3847/1538-4365/aadd49`](http://doi.org/10.3847/1538-4365/aadd49)

(ref: freundlich_towards_2013) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2013, A&A, 553, A130, doi: [`10.1051/0004-6361/201220981`](http://doi.org/10.1051/0004-6361/201220981)

(ref: genzel_study_2010) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, Monthly Notices of the Royal Astronomical Society, 407, 2091, doi: [`10.1111/j.1365-2966.2010.16969.x`](http://doi.org/10.1111/j.1365-2966.2010.16969.x)

(ref: gomez-guijarro_goods-alma_2022) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 659, A196, doi: [`10.1051/0004-6361/202142352`](http://doi.org/10.1051/0004-6361/202142352)

(ref: gonzalez-lopez_alma_2017) González-López, J., Bauer, F. E., Aravena, M., et al. 2017, A&A, 608, A138, doi: [`10.1051/0004-6361/201730961`](http://doi.org/10.1051/0004-6361/201730961)

(ref: greve_star_2014) Greve, T. R., Leonidaki, I., Xilouris, E. M., et al. 2014, The Astrophysical Journal, 794, 142, doi: [`10.1088/0004-637X/794/2/142`](http://doi.org/10.1088/0004-637X/794/2/142)

(ref: hao_dust-corrected_2011) Hao, C.-N., Kennicutt, R. C., Johnson, B. D., et al. 2011, ApJ, 741, 124, doi: [`10.1088/0004-637X/741/2/124`](http://doi.org/10.1088/0004-637X/741/2/124)

(ref: hernquist_tidal_1989) Hernquist, L. 1989, Nature, 340, 687, doi: [`10.1038/340687a0`](http://doi.org/10.1038/340687a0)

(ref: huang_diverse_2023) Huang, J.-S., Li, Z.-J., Cheng, C., et al. 2023, ApJ, 949, 83, doi: [`10.3847/1538-4357/acc9c3`](http://doi.org/10.3847/1538-4357/acc9c3)

(ref: ilbert_accurate_2006) Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A, 457, 841, doi: [`10.1051/0004-6361:20065138`](http://doi.org/10.1051/0004-6361:20065138)

(ref: johnson_kmos_2018) Johnson, H. L., Harrison, C. M., Swinbank, A. M., et al. 2018, Monthly Notices of the Royal Astronomical Society, 474, 5076, doi: [`10.1093/mnras/stx3016`](http://doi.org/10.1093/mnras/stx3016)

(ref: kalita_rest-frame_2023) Kalita, B. S., Silverman, J. D., Daddi, E., et al. 2023, ApJ, 960, 25, doi: [`10.3847/1538-4357/acfee4`](http://doi.org/10.3847/1538-4357/acfee4)

(ref: kalita_near-ir_2024) —. 2024, Near-IR clumps and their properties in high-z galaxies with JWST/NIRCam, arXiv, doi: [`10.48550/arXiv.2402.02679`](http://doi.org/10.48550/arXiv.2402.02679)

(ref: Kashino2019) Kashino, D., Silverman, J. D., Sanders, D., et al. 2019, ApJS, 241, 10, doi: [`10.3847/1538-4365/ab06c4`](http://doi.org/10.3847/1538-4365/ab06c4)

(ref: robert_c_kennicutt_global_1998) Kennicutt. 1998a, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: kennicutt_star_1998) Kennicutt, R. C. 1998b, ARA&A, 36, 189, doi: [`10.1146/annurev.astro.36.1.189`](http://doi.org/10.1146/annurev.astro.36.1.189)

(ref: koekemoer_cosmos_2007) Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172, 196, doi: [`10.1086/520086`](http://doi.org/10.1086/520086)

(ref: koekemoer_candels_2011) Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS, 197, 36, doi: [`10.1088/0067-0049/197/2/36`](http://doi.org/10.1088/0067-0049/197/2/36)

(ref: lackner_late-stage_2014) Lackner, C. N., Silverman, J. D., Salvato, M., et al. 2014, ApJ, 148, 137, doi: [`10.1088/0004-6256/148/6/137`](http://doi.org/10.1088/0004-6256/148/6/137)

(ref: 2023arXiv230707599L) Le Bail, A., Daddi, E., Elbaz, D., et al. 2023, arXiv e-prints, arXiv:2307.07599, doi: [`10.48550/arXiv.2307.07599`](http://doi.org/10.48550/arXiv.2307.07599)

(ref: lin_almaquest_2022) Lin, L., Ellison, S. L., Pan, H.-A., et al. 2022, ApJ, 926, 175, doi: [`10.3847/1538-4357/ac4ccc`](http://doi.org/10.3847/1538-4357/ac4ccc)

(ref: liu_high-j_2015) Liu, D., Gao, Y., Isaak, K., et al. 2015, ApJL, 810, L14, doi: [`10.1088/2041-8205/810/2/L14`](http://doi.org/10.1088/2041-8205/810/2/L14)

(ref: liu_automated_2019) Liu, D., Lang, P., Magnelli, B., et al. 2019, ApJS, 244, 40, doi: [`10.3847/1538-4365/ab42da`](http://doi.org/10.3847/1538-4365/ab42da)

(ref: liu_co_2021) Liu, D., Daddi, E., Schinnerer, E., et al. 2021, ApJ, 909, 56, doi: [`10.3847/1538-4357/abd801`](http://doi.org/10.3847/1538-4357/abd801)

(ref: Lotz2008) Lotz, J. M., Davis, M., Faber, S. M., et al. 2008, ApJ, 672, 177, doi: [`10.1086/523659`](http://doi.org/10.1086/523659)

(ref: magdis_evolving_2012) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6, doi: [`10.1088/0004-637X/760/1/6`](http://doi.org/10.1088/0004-637X/760/1/6)

(ref: marchesi_chandra_2016) Marchesi, S., Civano, F., Elvis, M., et al. 2016, ApJ, 817, 34, doi: [`10.3847/0004-637X/817/1/34`](http://doi.org/10.3847/0004-637X/817/1/34)

(ref: masters_complete_2019) Masters, D. C., Stern, D. K., Cohen, J. G., et al. 2019, ApJ, 877, 81, doi: [`10.3847/1538-4357/ab184d`](http://doi.org/10.3847/1538-4357/ab184d)

(ref: mihos_ultraluminous_1994) Mihos, J. C., & Hernquist, L. 1994, ApJL, 431, L9, doi: [`10.1086/187460`](http://doi.org/10.1086/187460)

(ref: moreno_spatially_2021) Moreno, J., Torrey, P., Ellison, S. L., et al. 2021, MNRAS, 503, 3113, doi: [`10.1093/mnras/staa2952`](http://doi.org/10.1093/mnras/staa2952)

(ref: mullaney_defining_2011) Mullaney, J. R., Alexander, D. M., Goulding, A. D., & Hickox, R. C. 2011, Monthly Notices of the Royal Astronomical Society, 414, 1082, doi: [`10.1111/j.1365-2966.2011.18448.x`](http://doi.org/10.1111/j.1365-2966.2011.18448.x)

(ref: murphy_calibrating_2011) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67, doi: [`10.1088/0004-637X/737/2/67`](http://doi.org/10.1088/0004-637X/737/2/67)

(ref: osborne_strategies_2024) Osborne, C., & Salim, S. 2024, Strategies for obtaining robust SED fitting parameters for galaxies at z\~1 and z\~2 in the absence of IR data, arXiv, doi: [`10.48550/arXiv.2401.06865`](http://doi.org/10.48550/arXiv.2401.06865)

(ref: puglisi_main_2019) Puglisi, A., Daddi, E., Liu, D., et al. 2019, ApJL, 877, L23, doi: [`10.3847/2041-8213/ab1f92`](http://doi.org/10.3847/2041-8213/ab1f92)

(ref: puglisi_sub-millimetre_2021) Puglisi, A., Daddi, E., Valentino, F., et al. 2021, MNRAS, 508, 5217, doi: [`10.1093/mnras/stab2914`](http://doi.org/10.1093/mnras/stab2914)

(ref: rizzo_alma-alpaka_2023) Rizzo, F., Roman-Oliveira, F., Fraternali, F., et al. 2023, The ALMA-ALPAKA survey I: high-resolution CO and \[CI\] kinematics of star-forming galaxies at z = 0.5-3.5, arXiv. <http://arxiv.org/abs/2303.16227>

(ref: rodighiero_lesser_2011) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40, doi: [`10.1088/2041-8205/739/2/L40`](http://doi.org/10.1088/2041-8205/739/2/L40)

(ref: rujopakarn_jwst_2023) Rujopakarn, W., Williams, C. C., Daddi, E., et al. 2023, ApJL, 948, L8, doi: [`10.3847/2041-8213/accc82`](http://doi.org/10.3847/2041-8213/accc82)

(ref: sanders_ultraluminous_1988) Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325, 74, doi: [`10.1086/165983`](http://doi.org/10.1086/165983)

(ref: schmidt_rate_1959) Schmidt, M. 1959, ApJ, 129, 243, doi: [`10.1086/146614`](http://doi.org/10.1086/146614)

(ref: scoville_cosmos_2007) Scoville, N., Abraham, R. G., Aussel, H., et al. 2007, ApJS, 172, 38, doi: [`10.1086/516580`](http://doi.org/10.1086/516580)

(ref: scoville_ism_2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: scoville_cosmic_2023) Scoville, N., Faisst, A., Weaver, J., et al. 2023, ApJ, 943, 82, doi: [`10.3847/1538-4357/aca1bc`](http://doi.org/10.3847/1538-4357/aca1bc)

(ref: silverman_higher_2015) Silverman, J. D., Daddi, E., Rodighiero, G., et al. 2015a, ApJL, 812, L23, doi: [`10.1088/2041-8205/812/2/L23`](http://doi.org/10.1088/2041-8205/812/2/L23)

(ref: silverman_fmos-cosmos_2015) Silverman, J. D., Kashino, D., Sanders, D., et al. 2015b, ApJS, 220, 12, doi: [`10.1088/0067-0049/220/1/12`](http://doi.org/10.1088/0067-0049/220/1/12)

(ref: silverman_molecular_2018) Silverman, J. D., Rujopakarn, W., Daddi, E., et al. 2018a, ApJ, 867, 92, doi: [`10.3847/1538-4357/aae25e`](http://doi.org/10.3847/1538-4357/aae25e)

(ref: silverman_concurrent_2018) Silverman, J. D., Daddi, E., Rujopakarn, W., et al. 2018b, ApJ, 868, 75, doi: [`10.3847/1538-4357/aae64b`](http://doi.org/10.3847/1538-4357/aae64b)

(ref: solomon_molecular_1997) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, ApJ, 478, 144, doi: [`10.1086/303765`](http://doi.org/10.1086/303765)

(ref: speagle_highly_2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: tacchella_evolution_2016) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016a, Monthly Notices of the Royal Astronomical Society, 458, 242, doi: [`10.1093/mnras/stw303`](http://doi.org/10.1093/mnras/stw303)

(ref: tacchella_confinement_2016) —. 2016b, MNRAS, 457, 2790, doi: [`10.1093/mnras/stw131`](http://doi.org/10.1093/mnras/stw131)

(ref: tacconi_evolution_2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, Annual Review of Astronomy and Astrophysics, 58, 157, doi: [`10.1146/annurev-astro-082812-141034`](http://doi.org/10.1146/annurev-astro-082812-141034)

(ref: tacconi_phibss_2013) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: tacconi_phibss_2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: Tadaki2020) Tadaki, K.-i., Belli, S., Burkert, A., et al. 2020, ApJ, 901, 74, doi: [`10.3847/1538-4357/abaf4a`](http://doi.org/10.3847/1538-4357/abaf4a)

(ref: teodoro_3dbarolo_2015) Teodoro, E. M. D., & Fraternali, F. 2015, MNRAS, 451, 3021, doi: [`10.1093/mnras/stv1213`](http://doi.org/10.1093/mnras/stv1213)

(ref: ubler_ionized_2018) Übler, H., Genzel, R., Tacconi, L. J., et al. 2018, ApJL, 854, L24, doi: [`10.3847/2041-8213/aaacfa`](http://doi.org/10.3847/2041-8213/aaacfa)

(ref: valentino_co_2020) Valentino, F., Daddi, E., Puglisi, A., et al. 2020, A&A, 641, A155, doi: [`10.1051/0004-6361/202038322`](http://doi.org/10.1051/0004-6361/202038322)

(ref: weaver_cosmos2020_2022) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11, doi: [`10.3847/1538-4365/ac3078`](http://doi.org/10.3847/1538-4365/ac3078)

(ref: whitaker_star_2012) Whitaker, K. E., Dokkum, P. G. v., Brammer, G., & Franx, M. 2012, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: wisnioski_kmos3d_2019) Wisnioski, E., Schreiber, N. M. F., Fossati, M., et al. 2019, ApJ, 886, 124, doi: [`10.3847/1538-4357/ab4db8`](http://doi.org/10.3847/1538-4357/ab4db8)

</paper>

Write the methods card for this paper.