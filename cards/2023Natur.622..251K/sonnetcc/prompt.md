# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023Natur.622..251K\sonnetcc\reply.txt

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
 "bibcode": "2023Natur.622..251K",
 "title": "A planetary collision afterglow and transit of the resultant debris cloud",
 "year": 2023,
 "journal": "Nature",
 "first_author": "Kenworthy, Matthew",
 "n_authors": 22,
 "arxiv_id": "2310.08360",
 "doi": "10.1038/s41586-023-06573-9",
 "alma_projects_linked_by_archive": [
  "2019.A.00040.S"
 ]
}
```

Paper text:
<paper>
# A planetary collision afterglow and transit of the resultant debris cloud

1\], ,

2\], ,

3\], ,

4\], ,

5\], ,

6\], ,

7\],

8\],

9\],

10\], ,

11\], ,

12\],

13\], ,

14\], ,

15\], ,

16\],

17\],

18\],

19\], ,

# Main Article

The otherwise unremarkable star 2MASS J08152329-3859234 underwent a sudden optical dimming event in December 2021 (cite: RizzoSmith21; RizzoSmith22) and was assigned the identifier ASASSN-21qj by the ASAS-SN survey (cite: shappee_man_2014; kochanek_all-sky_2017).

Here, we combine both optical (from the Las Cumbres Observatory Global Telescope, LCOGT) and infrared (from the WISE satellite) observations of ASASSN-21qj for the years before and after this dimming event (Figure [1](#fig:wisephot)).

Optical multiband photometry shows a wavelength dependent depth consistent with extinction by sub-micron particles.

About 900 days prior to the optical dimming event, the ASASSN-21qj system showed a significant brightening in the infrared, of 0.4 magnitudes at 3.8 microns ($W1$) and 0.8 magnitudes at 4.5 microns ($W2$).

Before this time the IR brightness was consistent with being purely stellar.

The increased IR fluxes indicate that in addition to the quiescent stellar flux, there was new emission at a temperature of approximately 1000 K.

Such a remarkable combination of observations, particularly the 2.5 year delay between the IR and optical variation, requires an explanation.

![](figures/all_phot_nature_delta_flux.pdf)

The optical and infrared light curves (Figure [1](#fig:wisephot)) provide key constraints on any proposed scenario.

The post-brightening IR fluxes in the $W1$ and $W2$ WISE passbands are consistent with emission at a blackbody temperature of $1000 \pm 100$ K and this temperature is sustained, within error, for the remainder of our observation window, despite a decline in the total flux.

For an emitter located at the distance of ASASSN-21qj from Earth, and the observed maximum luminosity of approximately 0.04 $L_\star$, this implies an emitting area of 0.01 au$^2$, equivalent to an object with a radius of 7 $R_\odot$, or $750$ $R_{\rm Earth}$.

If this emission was from material – e.g., dust – passively heated by proximity to the star, then that material must have been generated and remained within about 0.1 au to produce the observed temperature.

One possible explanation is that we are observing two unrelated but coincidental phenomena: a warm dust generating collision within 0.1 au of the star, with a separate object transiting the star 900 days later.

Two events that are themselves very rare occurring independently in one system is, however, highly improbable.

A second explanation is that warm dust is generated close to the star and causes the optical transit, but this requires a fine-tuned configuration where the star is optically blocked by scale height variations in the resulting disk.

Instead, we hypothesize that are we are observing the aftermath of a single collision between super-Earths or mini Neptunes – a so-called giant impact – between 2 and 16 au from the star.

These distances are determined, respectively, by the delay between the IR brightening and the optical eclipse (Fig. [1](#fig:wisephot)), and by gradients in the optical light curve (Fig. [2](#fig:eclipse_overview)).

In contrast to other extreme debris disk events where the star heats the dust, we propose that the infrared emission is directly from the post-impact body (cite: Lock2017; 2009ApJ...704..770M), and that impact debris produced the optical transit.

Giant impacts are a common occurrence in planet formation (cite: Schlichting2018a; DAngelo2018) and also occur during instabilities in older systems (cite: Kaib2016); this would explain the observations with a single event of a type that are expected for systems with ages like ASASSN-21qj.

Giant impacts are one of the most energetic events planets experience.

For example, the kinetic energy of impacts between two half-Neptune-mass bodies range from $10^{33}$ to $10^{34}$ J, enough to vaporize the colliding bodies several times over.

A large fraction of this energy is dissipated in the colliding bodies and post-impact bodies are substantially melted and vaporized (cite: Nakajima2015; Lock2017; Carter2020).

Furthermore, extreme torques exerted in impacts often produce rapidly rotating bodies (cite: Lock2017).

Such low density and rotationally-flattened bodies can be hundreds of times larger than the pre-impact planets (cite: Lock2017) with correspondingly large radiative surfaces.

Giant impacts produce significant amounts of debris, typically around 1% of the colliding mass, that is injected into orbit around the host star(cite: Canup2001; Lock18).

Impact ejecta have a wide range of sizes, from sub-micron dust to planetesimals of tens to hundreds of kilometers, and often contains the most highly heated material (cite: Benz2008_Mercury_book; Leinhardt2015; Carter2020a).

For sufficiently high impact velocities ($>1$ km s$^{-1}$ for water ice, and $>8$ km s$^{-1}$ for forsterite) a substantial fraction of this material is vaporised (cite: Stewart2008; Davies2020; Carter2020a).

Shearing of droplets and cooling and condensation of vapor produces a population of small dust grains and solid spherules.

The size distribution of this fraction of the debris is uncertain, due to difficulties in modelling condensate nucleation and breakup, but previous work suggests that debris could range in size from sub-micron to decimeters (cite: Benz2008_Mercury_book; Johnson2015).

The wavelength-dependent eclipse suggests that the optical depth of the transiting dust cloud is dominated by sub-micron grains, consistent with these previous estimates.

While the fading of the excess infrared flux occurs within 100 days of the start of the optical transit, we consider the timing to be coincidental because there is no clear correspondence between the light curves, for example no change in the (six month cadence) IR flux when the star dims in the optical wavelengths just before MJD 59500.

![](figures/master_lightcurve_nature_simple.pdf)

The radiative flux from post-impact bodies has not been explored in depth.

Computational resource limitations make resolving the low-density outer regions and photosphere of post-impact bodies extremely challenging.

However, preliminary simulations of impacts between super-Earth and mini-Neptunes place an approximate lower limit on the extent of post-impact bodies and show that post-impact bodies can extend to hundreds of Earth radii.

Such an object radiating at $\sim$1000 K would produce a flux comparable to the 0.04 $L_*$ inferred from our observations.

Independent of impact simulations, there are fundamental limits on the size of post-impact bodies from the Hill and Bondi radii.

Any post-impact structure must lie within the Hill sphere, the distance within which the gravity of an object dominates over that of the star.

Furthermore, only vapor within the Bondi radius would be bound to the post-impact body.

Figure [3](#fig:Hill_Bondi_R)A shows the Hill radii at different distances from ASASSN-21qj (solid lines) and the Bondi radii for example gas species (dotted lines).

Beyond 2.4 au, the Hill radii of greater than Earth-mass bodies are large enough to accommodate a post-impact body capable of producing the required IR flux ($\sim7R_*$, dotted line).

Heavier gases (H$_2$O, SiO, and SiO$_2$) are also bound to bodies of more than a few Earth masses.

A post-impact body of a few Earth masses can hence theoretically produce the observed IR emission, with a photosphere that is dust and/or vapor.

![](figures/Size_cooling_combined_figure.pdf)

A key line of evidence for direct detection of a post-impact body is the constant emission temperature.

It is argued (cite: Lock18) that rocky post-impact bodies become optically thin at low pressures where radiative loss drives rapid condensation of the rock vapor.

The emission temperature is then set by the liquid-vapor phase boundary and is constant until the post-impact body almost fully condenses (cite: Lock18; Caracas2023).

The dew point (onset of condensation) and bubble point (onset of substantial vaporization) of material with bulk silicate Earth composition are similar (cite: Lock18; Fegley2023_BSE_cond) at the low pressures of the photosphere of a post-impact body.

However, even small amounts of water (10$^{-3}$ mole fraction) may lower the bubble and dew points for silicates by $\sim$100 K (cite: Fegley2023_BSE_cond; Lock18).

The emission temperature of bodies produced by collisions of proto-planets composed of rock and ices/volatiles could be buffered at $\sim$1000 K during early evolution.

The temporal variation of flux from a post-impact body is controlled by evolution of the bodies’ size which is governed by a number of competing factors (cite: Lock18; Lock2020), including radiative energy loss, viscous spreading, and mass and angular momentum transfer by condensates.

For silicate-dominated post-impact bodies, the high emission temperature means that radiative cooling dominates, and the post-impact body contracts rapidly, fully condensing over years to thousands of years (cite: Lock18; Lock2020).

The body we observed has a much lower emission temperature, and contracted substantially more slowly.

Figure [3](#fig:Hill_Bondi_R) B and C show evolution of conceptual post-impact bodies in the limiting case that radiative cooling dominates.

If sufficient mass is injected into the outer regions (i.e., less negative power law exponents) the observed flux can remain constant for an initial period and then decays over the order of hundreds of days, in agreement with infrared observations.

Further work is required to understand the structure and evolution of bodies produced by impacts between super-Earths and mini-Neptunes of different compositions and identify temporal flux variations consistent with our observations.

# Methods

The stellar properties of ASASSN-21qj (Gaia DR3 5539970601632026752 = 2MASS J08152329-3859234) are listed in Extended Data Table [1](#tab:Stellarprop), showing that ASASSN-21qj is consistent with being a G2 type dwarf star.

Where necessary we assume a stellar mass equal to the Sun.

ASASSN-21qj has a neighbor (Gaia DR3 5539970597334497024 = 2MASS J08152298-3859244) which is a visual double.

Based on the Gaia DR3 mean ICRS position for epoch 2016.0, the visual companion lies at a separation $\rho$ = $3738.243\pm0.062$ mas and at position angle $\theta$ = $249^{\circ}.977$.

Their parallaxes ($\varpi$ = $1.7631\pm0.0112$ mas vs. $1.4711\pm0.0523$ mas) differ by 5.5$\sigma$ and proper motions ($\mu_{\alpha} = -9.692\pm0.012$, $\mu_{\delta} = 7.349\pm0.012$ mas yr$^{-1}$  vs. $\mu_{\alpha} = -0.114\pm0.055$, $\mu_{\delta} = 6.419\pm0.053$ mas yr$^{-1}$) differ by a factor of 2.

The large differences in distance and proper motions suggests that these stars are not associated.

The stellar photospheric flux was estimated by fitting stellar models to GAIA, APASS, and DENIS and WISE optical/near-IR photometry (the 2MASS $J$ photometry is an upper limit, and $H$ and $K_s$ are flagged as contaminated).

Extended Data Figure [4](#fig:sed) shows the resulting models (the dashed line is discussed below).

The ALLWISE photometry ($\sim$2010) is consistent with the NEOWISE photometry pre-brightening nearly ten years later.

A fit using the method of (cite: 2019MNRAS.488.3588Y) with GAIA and DENIS photometry finds that the WISE W1/2 fluxes are about 20% too high, but better agreement is found with APASS photometry.

The difference is explained by the fact that WISE and APASS have lower spatial resolution and include the flux of the $\sim$2 mag fainter visual double to the West of ASASSN-21qj (which is visible in 2MASS).

The best fit stellar effective temperature is $5560 \pm 100$ K.

We do not find that reddening is needed for these models; while there is relatively little photometry with which to strongly constrain both $T_{\rm eff}$ and $A_V$, the $T_{\rm eff}$ from GAIA DR3 is $5760 \pm 10$ K, which suggests that the conclusion of little reddening is valid.

Primarily, we conclude that there is no evidence that ASASSN-21qj showed evidence for an IR excess before the brightening seen by NEOWISE.

To estimate the IR excess properties we fit the same models, but now including the first five post-brightening NEOWISE data points.

We correct for the nearby source by using the GAIA photometry for the star, and the post/pre-brightening difference for the WISE excess flux.

This fit yields the fractional luminosity $L_{\rm dust}/L_\star = 0.04 \pm 0.005$ and a dust temperature $950 \pm 30$ K.

To estimate the dust temperature as a function of time we simply subtract the median pre-brightening W1/2 fluxes, with the RMS of these values as the uncertainty (see Figure [1](#fig:wisephot)).

The temperature uncertainty increases as the excess fades; the excess flux uncertainty depends on both the observed flux and the stellar flux, and as the excess decreases the stellar uncertainty (which is constant) becomes an increasingly large fraction of the excess.

These fluxes therefore exclude the contaminating flux from the nearby object, and are consistent with the SED-derived dust temperature.

Converting dust temperatures to stellocentric radii is uncertain because dust temperature depends on grain size.

Typically the radius derived under the assumption of blackbody emission is an underestimate by a factor of up to five (cite: 2013MNRAS.428.1263B; 2015MNRAS.454.3207P).

Thus, we conclude that the dust location might in the most extreme case be as far as 1 au, but not sufficiently far to explain the 900 day delay between the WISE and optical flux variations. which requires a distance of at least 2 au.

![](figures/sed.pdf)

| Property                           |         Value         |
|:-----------------------------------|:---------------------:|
| $\alpha_{ICRS}$, \[hh mm ss\]      |      08:15:23.30      |
| $\delta_{ICRS}$, \[dd mm ss\]      |      -38:59:23.3      |
| $\mu_{\alpha}$ \[mas yr$^{-1}$\]   |   $-9.692\pm0.012$    |
| $\mu_{\delta}$ \[mas yr$^{-1}$\]   |    $7.349\pm0.012$    |
| $\varpi$ \[mas\]                   |    $1.763\pm0.011$    |
| RV \[km s$^{-1}$\]                 |      $25.8\pm3$       |
| Distance \[pc\]                    | $567.2^{+6.7}_{-5.9}$ |
| $G$ \[mag\]                        |   $13.371\pm 0.003$   |
| $G_{BP}$ \[mag\]                   |   $13.697\pm 0.003$   |
| $G_{RP}$ \[mag\]                   |   $12.882\pm 0.004$   |
| $G_{BP}-G_{RP}$ \[mag\]            |   $0.815\pm 0.005$    |
| $J$ \[mag\]                        |       $>12.07$        |
| $H$ \[mag\]                        |    $12.03\pm0.04$     |
| $K_s$ \[mag\]                      |    $11.99\pm0.04$     |
| $B$ (AB) \[mag\]                   |    $14.16\pm0.06$     |
| $V$ (AB) \[mag\]                   |    $13.48\pm0.03$     |
| $g'$ (AB) \[mag\]                  |    $13.77\pm0.03$     |
| $r'$ (AB) \[mag\]                  |    $13.29\pm0.03$     |
| $i'$ (AB) \[mag\]                  |    $13.20\pm0.08$     |
| $T_\mathrm{eff}$ \[K\]             |      $5760\pm10$      |
| \[Fe/H\] \[dex\]                   |    $-0.23\pm0.01$     |
| log $g$ \[log$_{10}$ cm s$^{-2}$\] |    $4.339\pm0.005$    |
| $R_*$ \[$R_\odot$\]                |        $1.04$         |
| log($L_{bol}/L_{\odot}$) \[dex\]   |        $0.033$        |
| $m_{bol}$ \[mag\]                  |    $13.49\pm0.02$     |
| $E(G_{BP}-G_{RP})$ \[mag\]         |   $0.01 \pm 0.005$    |
| Age \[Myr\]                        |      $300\pm92$       |

: Properties of ASASSN-21qj

## Observations

The beginning of the eclipse was announced (cite: RizzoSmith21) by the ASAS-SN survey, which triggered several observing campaigns at optical wavelengths and an ALMA observation at Band 7 (program `2019.A.00040.S`).

| Survey name | Filter | Number of points |
|:------------|:------:|:----------------:|
| ASASSN      |  $V$   |       758        |
|             |  $g'$  |       3225       |
| ATLAS       |  $c$   |       161        |
|             |  $o$   |       677        |
| AAVSO       |  $B$   |       729        |
|             |  $I$   |       728        |
|             |  $V$   |       722        |
| LCOGT       |  $g$   |       275        |
|             |  $r$   |       224        |
|             |  $i$   |       168        |
| NEOWISE     |  $W1$  |        18        |
|             |  $W2$  |        18        |

: Photometric observations of ASASSN-21qj. The number of points are listed per survey and filter. This is the count after initial rejection of photometric points with significantly large error bars. Further photometric points may have been rejected in the different analysis steps. The ROAD observations constitute the majority of observations from the AAVSO data sets.

The All Sky Automated Survey (cite: pojmanski_all_1997; asas_2005; asas_2018) is a survey consisting of two observing stations - one in Las Campanas, Chile and the other on Maui, Hawaii.

Each observatory is equipped with two CCD cameras using V and I filters and commercial f $= 200$ mm, D $= 100$ mm lenses, although both larger (D $=250$ mm) and smaller (50-72 mm) lenses were used at earlier times.

The majority of the data are taken with a pixel scale of $\approx$ 15$^{\prime\prime}$.

ASAS splits the sky into 709 partially overlapping 9$^\circ$ $\times$ 9$^\circ$ fields, taking on average 150 3-minute exposures per night, leading to a variable cadence of 0-2 frames per night.

Depending on the equipment used and the mode of operation, the ASAS limiting magnitude varied between 13.5 and 15.5 mag in V, and the saturation limit was 5.5 to 7.5 mag.

Precision is around 0.01-0.02 mag for bright stars and below 0.3 mag for the fainter ones.

ASAS photometry is calibrated against the Tycho catalog, and its accuracy is limited to 0.05 mag for bright, non-blended stars.

The All Sky Automated Survey for Supernovae (cite: shappee_man_2014; kochanek_all-sky_2017) consists of five stations around the globe, with each station hosting four telescopes with a shared mount.

The telescopes consist of a 14-cm aperture telephoto lens with a field of view of approximately 4.5$^\circ$$\times$4.5$^\circ$ and an 8.0$^{\prime\prime}$ pixel scale.

Two of the original stations (one in Hawaii and one in Chile) were initially fitted with $V$ band filters, but now these and all the other stations (Texas, South Africa and a second in Chile) observe with $g'$ band filters down to 18 mag.

The Remote Observatory Atacama Desert (cite: Hambsch12) is a fully automated telescope located in Chile that obtains nightly photometry in Astrodon B, V and I bands for a wide range of astronomical projects.

It consists of a 40-cm $f/6.8$ Optimized Dall-Kirkham and uses a Finger Lakes Instruments camera with a 4k$\times$4k array with pixels of $9\mu m$ in size.

Data are reduced using a custom pipeline and then published on the AAVSO website.

Las Cumbres Observatory Global Telescope (LCOGT) is a network of 25 fully robotic operated telescopes distributed over 7 sites located all around the globe.

These telescopes are designed to observe transient astronomical events at optical and near-infrared wavelengths.

LCOGT provides a large variety of filter options, but the data we collected are in SDSS $g'$, $r'$ and $i'$ bands.

All data is automatically processed and calibrated by the BANZAI pipeline.

The visual companion caused complications in BANZAIs automatic aperture extraction routine; sometimes correct apertures were extracted for both ASASSN-21qj and the nearby star, and sometimes both sources were extracted in one large aperture, often with an offset from the true center of ASASSN-21qj.

To correct this, the last two stages of the BANZAI routine, aperture extraction and photometry calibration, were modified for this specific situation.

The calibrated magnitudes of all sources in the frames are computed using the default BANZAI photometry calibration routine.

ATLAS is a project that searches for near earth asteroids down to a magnitude of 19 (cite: Tonry18).

Two filters were obtained, the $o$ (orange) and $c$ (cyan) filters respectively.

The data consists of two to four photometric points observed each night when conditions permitted.

Photometry with large errors was rejected in a first pass, then the remaining observations during a night were averaged and an error based on the r.m.s. of these nightly points was calculated.

The photometry covers the time period where the collision event occurred.

The Transiting Exoplanet Survey Satellite (cite: 2015JATIS...1a4003R) is a satellite designed to survey for transiting exoplanets among the brightest and nearest stars over most of the sky.

The TESS satellite orbits the Earth every 13.7 days on a highly elliptical orbit, scanning a sector of the sky spanning 24$^\circ$$\times$ 96$^\circ$ for a total of two orbits, before moving on to the next sector.

It captures images at a 2 second (used for guiding), 20 seconds (for 1000 bright asteroseismology targets), 120 seconds (for 200 000 stars that are likely planet hosts) and 30 minute (full frame image) cadences.

The instrument consists of 4 CCDs each with a field of view of 24$^\circ$$\times$24$^\circ$, with a wide band-pass filter from 600-1000 nm (similar to the $I_C$ band) and provides high precision ($\approx$milli-mag) light curves for stars down to about 14 mag ($I_C$).

The Near-Earth Object Wide-field Infrared Survey Explorer (NEOWISE) is a space-based infrared telescope that has been surveying the sky since 2013 at $3.4$ and $4.6~\mu$m.

NEOWISE orbits near the Earth’s day-night terminator, scanning rings of the sky near $\sim90^\circ$ Solar elongation, and obtains a sequence of observations of a given region of sky every six months.

The two wavelength channels are obtained simultaneously through a beamsplitter, allowing for color information to be extracted for each source detected in both bands.

Detailed descriptions of NEOWISE operations and early results from the Reactivation mission (cite: mainzer14neowise) and the standard data processing and data characteristics (cite: cutri15) are available.

A single data point for each epoch and wavelength is calculated by taking the weighted average of the individual NEOWISE measurements.

The ALMA data from programme `2019.A.00040.S` were downloaded and processed through to a measurement set with CASA (cite: 2007ASPC..376..127M).

These observations were taken 2021 September 28 (MJD=59485) and used band 7, with a mean wavelength of 880 $\mu$m.

No source is visible in the default archive products, and we also detect no source at the expected location in CLEAN images.

The archive products report an RMS of 17 $\mu$Jy, and we measure an RMS of 20 $\mu$Jy in a naturally weighted image.

We therefore consider these results as an upper limit of 60 $\mu$Jy.

In terms of the infrared excess visible in the mid-IR with WISE this upper limit is not at all constraining, but does set limits on emission from cooler dust (Figure [4](#fig:sed)).

## Light curves

In this section we consider the light curves; first the implications of the TESS data for the stellar age, and then the implications of the ground-based optical light curves for transverse velocity of the occulting material and dust grain sizes.

## Stellar rotation and age

![](figures/tess_asas_ls_epochs.pdf)

TESS data from the Quick-Look Pipeline (cite: 2020RNAAS...4..204H; 2021RNAAS...5..234K) was retrieved from the MAST archive and is shown in Extended Data Fig. [5](#fig:TESS_lc).

The star was observed in sectors 8, 34 and 35.

The star was observed soon after the infrared brightening, and two sequential sectors some time later.

A periodic signal with a period of approximately 4.3 days is seen with a peak to peak amplitude of 2% of the mean flux, and the similar period can be seen in the two later sectors but they are overwhelmed with the first signs of debris from the transiting object.

We carry out a Lomb-Scargle periodogram on S08, and obtain a significant detection of $P=4.43\pm 0.33$ days.

A similar period is seen at lower significance in the later sectors.

Aside from a peak at 1 day, the strongest peak in the ASAS-SN data has a similar period, at 4.1 days.

We attribute this modulation due to star spots on the star rotating in and out of our view, and so we assert that is the rotational period of the star.

Using this rotational period the gyrochronological age (cite: Bouma23; Kounkel22) is calculated to be $300\pm92$ Myr.

### Duration of the eclipse and gradient analysis

![](figures/master_lightcurve_nature_with_zoom_3_panel.pdf)

Figure [2](#fig:eclipse_overview) shows the optical light curves.

The start of the optical eclipse is seen around MJD 59350 in the $g'$ band observations, and returns to pre-eclipse levels by MJD 59850, giving a total eclipse duration of approximately 500 days.

The eclipse depth varies as a function of wavelength, which is discussed below.

The normalisation of the light curves for the ASAS-SN, ATLAS and ALLWISE photometry was by calculating the out of transit flux before MJD 58700.

The LCOGT and AAVSO photometry was determined by aligning the photometry of the eclipse with the ASAS-SN and ATLAS photometry on a per band basis.

By treating the linear changes in flux as due to the edges of large dust clouds crossing the disk of the star, and the largest amount of absorption within any of these segments as an estimate for the absorption of the cloud (cite: Kennedy17), we can determine a robust lower limit to the transverse velocity of 7.5 km s$^{-1}$ for the material moving in front of the star.

The method is illustrated in Extended Data Figure [6](#fig:gradientconvert) and the results over the full optical transit are shown in the lower panel of Figure [2](#fig:eclipse_overview).

We convert the magnitude $M(t)$ at time $t$ to a normalised flux $f(t)=10^{\left(\left(M(t)-M_0\right)/-2.5\right)}$ where $M_0$ is the mean magnitude outside of the eclipse.

We visually determine turning points in the linearly increasing or decreasing photometric flux, fit straight lines to the selected points, and determine the flux gradient in units of day$^{-1}$.

A lower bound can be derived for the transverse velocity of the dust, $v$, by measuring the gradient of the light curve and determining what velocity a sharp edged and completely opaque occulter moving across the disk of the star would need to make the same gradient.

If the dust is on a circular orbit, it therefore has to be within 16 au (equivalent to an orbital period of 63 years) around the star. The temperature of sub-micron dust grains at this distance would be in the range 100-200 K.

### Dust properties from optical colors

![](figures/blueing.pdf)

As is clear from Figure [2](#fig:eclipse_overview) the photometry shows deeper absorption at bluer wavelengths compared to redder wavelengths.

This wavelength dependent absorption is typical of extinction due to particles with a characteristic size similar to or smaller than that of the observed wavelengths.

The differences are quantified in Extended Data Figure [7](#fig:blueing), which shows the AAVSO $BVI$ photometric colours as a function of $V$ magnitude.

For both $B-V$ and $V-I$ the colour becomes redder as the star dims, and the reddening is here quantified by the total to selective extinction ratio $A_\lambda/A_V$ (dashed lines).

The values are similar to those seen for interstellar extinction (cite: 1989ApJ...345..245C), indicating that the dimming is caused by sub-micron sized dust (cite: 1977ApJ...217..425M; 2001ApJ...548..296W).

A further constraint from the colours relates to scattering; in protoplanetary disk systems that undergo dimming (e.g. UX Ori types) the colour initially reddens with dimming, but moves back towards the stellar colour when the dimming is more than one or two magnitudes (cite: 1994AJ....108.1906H).

This “blueing” is typically interpreted as the relative increase in dust-scattered starlight from the disk or envelope as the star itself fades (cite: 1988SvAL...14...27G).

This behaviour is also seen in Extended Data Figure [7](#fig:blueing), where $B-V$ shows significant blueing, while $V-I$ does not.

The solid lines show an extinction model where an underlying scattered light component with the same colour as the star has been added; as the star dims it reddens, but will eventually return to the stellar colour.

This happens more quickly for $B-V$ because nearly all of the stellar flux in $B$ is blocked, and is less pronounced for $V-I$ because the star is significantly less dimmed in $I$.

The fraction of scattered light is relatively large at 7.5%, implying a significant complex of small dust around the star by the time the deepest parts of the optical transit occur.

This high fraction suggests that the impact occurred a significant fraction of an orbit before the optical transit, thus allowing the dust complex time to spread around the star.

## Dust mass estimates

The SED in Extended Data Figure [4](#fig:sed) gives an estimate of the infrared flux that would arise from dust thrown off in the putative collision.

We assume that the collision occurred at of order 10 au from the star, and hence that a dust temperature of 100 K is reasonable.

Here 1% of the mass of a  $\mathrm{M_{Earth}}$ planet is assumed to be converted entirely into 0.1 $\mu$m sized grains; this is an optimistic assumption given that the total mass thrown off in collisions is of order 1% or less (cite: 2012ApJ...745...79L), and that this ejected mass is constituted of bodies of a range of sizes and all the mass is not present as dust.

The dust spectrum in Extended Data Figure [4](#fig:sed) is approximated as a blackbody multiplied by $0.01 \times (10 / \lambda)^{1.5}$ (with $\lambda$ in $\mu$m), based on the absorption efficiency for silicates (cite: 1993ApJ...402..441L).

Changing the grain size to 1 $\mu$m yields a similar dust spectrum; while the dust emitting area is less, these grains emit more efficiently.

Thus, the mass in small grains detectable with ALMA is about 0.2 $M_{\rm Earth}$.

The dust spectrum lies well below the WISE measurements, and just below the ALMA measurement.

Even in this optimistic case, thermal emission from dust thrown off in the collision is therefore not necessarily easily detected.

This difference is one of surface area; at 600 pc thousands of square au of 100 K dust is needed for a thermal detection with ALMA, but only a small fraction of a square au is needed to significantly dim a star (which has radius $\sim$0.005 au).

## Alternative explanations for the observations

We consider three possible scenarios to explain the observations: 1) The initial brightening and later eclipse are two unrelated phenomena.

2\) The infrared emission and optical transit are both produced by a debris disk at $\sim0.1$ au.

3\) We are observing the aftermath of a collision between super-Earths or mini Neptunes at at a semi-major axis of several au (see Extended Data Figure [8](#fig:hypothesis)).

We provide here some more detail on the failures of the first two, and a preliminary simulation illustrating how an impact between two large bodies can produce a large object as hypothesised for our preferred scenario

![](figures/asassn-21qj-cartoon.pdf)

First, the IR flux increase and the optical dimming might be unrelated, coincidental phenomena.

For example, one debris disk at 0.1 au passively heated to 1000 K producing the IR emission and another disk further from the star that transited ASASSN-21qj.

This explanation is unsatisfactory because both IR flux increases and dimming events are rare.

Mid-IR excesses are exceptionally rare among main-sequence stars (cite: 2013MNRAS.433.2334K), and still uncommon for young stars (cite: 2013MNRAS.433.2334K), and no star has previously shown a sizeable increase starting from no excess.

A single case of a disappearing mid-IR excess has been seen, which remains largely unexplained (cite: 2012Natur.487...74M).

Similarly, optical dimming events are rare for main-sequence stars, for example only one was seen to undergo dust-related optical dimming with Kepler main mission, which observed 150,000 stars for four years (cite: 2016MNRAS.457.3988B).

Both optical and IR variability are independently less than 1% probabilities for a given star, so for ASASSN-21qj to show both by chance is at best a 0.01% probability, and probably much lower.

Another possibility is that both the IR and optical features are produced by a single debris disk at about 0.1 au from the star.

At such a close distance, any dust clumps would initially produce periodic eclipses on the timescale of days (cite: 2019MNRAS.488.4465G) before being sheared into an azimuthally symmetric structure in months, so the occultation of the star would need to be be related to changes in the vertical structure of a near edge-on post-collision disk, for example by dynamical “stirring” of debris by impact remnants (cite: 1992Icar...96..107I).

The optical depth of the disk must then decrease due to ongoing collisional depletion to explain the slow return to pre-transit levels of optical flux and gradual decrease in IR flux.

Three issues with this model are that 1) the disk must have precisely the right geometry to slowly occult the star as the scale height increased, and must coincidentally become optically thin, 2) there is no apparent change in dust temperature, which would be expected as the optical depth decreases and the warmer inner disk becomes visible, and 3) significant optical variation is seen three years after the putative collision, so any initially created clumps would already have sheared out.

Newer clumps must contribute of order 50% of the dust area to explain the large variations around 59500 MJD, but the IR flux shows a gradual decline rather than any strong variation that would be associated with clump creation.

A fourth, but less critical issue, is that the inferred clump velocities are not as high as they could be for transiting structures at 0.1 au, which should result in transverse velocities of up to 100 km s$^{-1}$.

## SPH collision simulations

To provide some more insight into the collision scenario, we performed impact simulations using the SWIFT smoothed particle hydrodynamics (SPH) code (cite: Schaller2016; Schaller2018; Kegerreis2019).

Extended Data Figure [9](#fig:SPH) shows a collision between two 25 $M_{\rm Earth}$ (Earth-mass) planets at 45.77 km s$^{-1}$ (1.4 $v_{\rm esc}$, escape velocity neglecting the atmosphere) at an impact parameter of 0.4 (an impact angle of 23.6$^\circ$).

The colliding bodies were 22.5% rock (cite: Stewart2019forsteriteEOS; Stewart2020_key_req_EOS), 67.5% water (cite: Senft2008), and 10% H/He (cite: Hubbard1980) by mass.

2.1$\times10^6$ particles were used in the simulation.

To make simulations with high resolution numerically tractable, SWIFT imposes a maximum smoothing length that, in effect, imposes a minimum density for particles in the simulation ($\sim30$ kg m$^{-3}$ for the simulation shown here).

The bound post-impact material is spread over hundreds of Earth radii following the collision, illustrating that giant impacts can produce very large post-impact objects.

However, for the massive and highly extended bodies produced by collisions between super-Earths and mini-Neptunes, a large fraction of the post-impact body is at the minimum density (green particles in lower right panel in Extended Data Figure [9](#fig:SPH)).

SPH simulations therefore likely underestimate the extent of such post-impact bodies, and further work is needed to fully quantify the size of post-impact bodies produced in different impacts.

![](figures/final_v2_less0d029.jpg)

## Post-impact body cooling calculations

How the emission from a post-impact body would evolve with time is highly dependent on the initial mass distribution and thermal state of the body, and the balance between radiative cooling, viscous spreading, and mass and angular momentum transport by condensates (cite: Lock2017; Lock18; Lock2020).

Given the limitations of SPH simulations (see above) it is not possible to accurately determine the initial structure of post-impact bodies in the relevant regime.

To explore a range of possible evolution pathways, we have calculated the evolution of post-impact bodies with different power-law surface density profiles, $\Sigma$, under the limiting case that radiative cooling and condensation of the vapor is the single driver for evolution of the structure.

We chose a power-law surface density profile as it can straightforwardly cover the wide range of surface density profiles expected after super-Earth/mini-Neptune collisions, based on that found in impact simulations between lower-mass, terrestrial bodies (cite: Lock2017; Canup2001; Canup2012; Cuk2012; Rufu2017; Reufer2012).

The surface density profile is given by:

$$\begin{equation}
\Sigma=\begin{cases}
\Sigma_0, & \text{if } r_{xy}\leq R_{\rm c}\\
\alpha r_{xy}^{\beta}, & \text{if } R_{\rm c} < r_{xy}\leq R_{\rm emit}\\
0, & \text{if } r_{xy}> R_{\rm emit}
\end{cases}   
\label{eqn:sigma}
\end{equation}$$

where: $r_{xy}$ is the distance from the rotation axis; $R_{\rm c}$ is the outer radius of a constant surface density central region, roughly analogous to the corotating regions seen in Earth-mass synestias (cite: Lock2017; Lock18); $\Sigma_0$ is the surface density of the central region; $\beta$ is the power law exponent; and $R_{\rm emit}$ is the initial emitting radius. Imposing surface density continuity gives

$$\begin{equation}
    \alpha=\Sigma_0 R_{\rm c}^{-\beta} \; .
\end{equation}$$

We can determine $\Sigma_0$ by fixing the mass of the body,

$$\begin{equation}
    M_{\rm p} = \int_0^{R_{\rm c}}{2 \pi r'_{xy} \Sigma_0 dr'_{xy}} + \int_{R_{\rm c}}^{R_{\rm emit}}{2 \pi r'_{xy} \Sigma(r'_{xy}) dr'_{xy}} \; ,
\end{equation}$$

which can be solved to give:

$$\begin{equation}
\Sigma_0=\begin{cases}
\frac{M_{\rm p}}{\pi \left [R_{\rm c}^2 + 2 R_{\rm c}^{-\beta} \left ( \ln{R_{\rm emit}}-\ln{R_{\rm c}}\right ) \right ]}, & \text{if } \beta=-2,\\
\frac{M_{\rm p}}{\pi \left [R_{\rm c}^2 + \frac{2 R_{\rm c}^{-\beta}}{\beta+2} \left ( R_{\rm emit}^{\beta+2}-R_{\rm c}^{\beta+2}\right ) \right ]}, & \text{otherwise.} 
\end{cases}
\end{equation}$$

The time taken for a given region of the structure to cool to the point that a sufficient fraction of material is condensed for the temperature to drop below the condensation-buffer (see above) and so the emitted flux to drop is given by

$$\begin{equation}
    t_{\rm cool} (r_{xy})=\frac{l f(r_{xy}) \Sigma(r_{xy})}{\sigma T^4_{\rm emit}}
\end{equation}$$

where $f$ is the initial vapor fraction at that radius, $l$ is the latent heat of vaporization of the material (here we have taken the limiting case of pure water $l=2.256\times 10^6$ (cite: Chase1998), but the addition of silicates could make the latent heat much larger), $\sigma$ is the Stefan–Boltzmann constant, and $T_{\rm emit}$ is the emission temperature.

Figure [3](#fig:Hill_Bondi_R) shows example evolutions of the emission from a post-impact body using this model for different parameters (solid lines).

Results of a modified model where the initial surface density (by the addition of a constant parameter to Equation [\[eqn:sigma\]](#eqn:sigma)) is forced to be zero at $R_{\rm emit}$ are shown as dashed lines.

G.M.K is supported by the Royal Society as a Royal Society University Research Fellow.

S. J. L. acknowledges funding from the UK Natural Environment Research Council (grant NE/V014129/1).

L.C. acknowledges funding from the European Union H2020-MSCA-ITN-2019 under Grant Agreement no. 860470 (CHAMELEON)

J. D. acknowledges funding support from the Chinese Scholarship Council (No. 202008610218).

Giant impact simulations were carried out using the Isambard 2 UK National Tier-2 HPC Service (http://gw4.ac.uk/isambard/) operated by GW4 and the UK Met Office, and funded by EPSRC (EP/T022078/1).

We thank Krzysztof Stanek and the work of the ASAS-SN team with their survey and for providing public access to the database.

Part of this research was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004).

MAK led the writing of the paper, management, obtaining the optical observations, and initial models.

SL led the afterglow modelling and theory.

GMK led the orbital analysis and dust analysis.

RvC did the optical light curve data reduction and reddening analysis and velocity constraint analysis.

EM performed the analysis of the properties of the star.

F.-J.H and EG carried out optical monitoring of the star.

JM, AM, JDK and AS were responsible for NEOWISE identification and data reduction.

SL, LC, JD, PT and ZL provided discussion on the ejected material and subsequent evolution.

JD performed the SPH impact simulations.

HB, SC, OG, PLD, LM and PT were responsible for the observation and reduction of observational data.

MRS led the discovery of the optical dimming of the star.

All co-authors assisted with manuscript writing and proofreading.

The authors declare no competing interests.

The data sets generated and analysed during the current study are available in the Zenodo repository <https://doi.org/10.5281/zenodo.8344755>.

All the code for the analysis and the generation of all the figures are available in a showyourwork (cite: Luger2021) reproducible framework available as a git repository on github: <https://github.com/mkenworthy/ASASSN-21qj-collision/>.

The source code and documentation for the SWIFT open-source simulation code is available from [www.swiftsim.com](www.swiftsim.com).

should be addressed to Matthew Kenworthy.

is available at http://www.nature.com/reprints.

</paper>

Write the methods card for this paper.