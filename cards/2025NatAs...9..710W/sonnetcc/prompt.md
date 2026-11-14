# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9..710W\sonnetcc\reply.txt

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
 "bibcode": "2025NatAs...9..710W",
 "title": "A giant disk galaxy two billion years after the Big Bang",
 "year": 2025,
 "journal": "Nature Astronomy",
 "first_author": "Wang, Weichen",
 "n_authors": 17,
 "arxiv_id": "2409.17956",
 "doi": "10.1038/s41550-025-02500-2",
 "alma_projects_linked_by_archive": [
  "2021.1.00793.S"
 ]
}
```

Paper text:
<paper>
# A Giant Disk Galaxy Two Billion Years After The Big Bang

1\], ,

2\], ,

3\], ,

4\], ,

5\],

6\],

7\], ,

8\], ,

9\],

10\], ,

The galaxy, dubbed “Big Wheel", was discovered serendipitously in a bright-quasar field at redshift ($z$) of 3.25 (cite: Pensabene2024) through James Webb Space Telescope (JWST) imaging at wavelengths of 1.5$\,\mu$m and 3.2$\,\mu$m (rest-frame 0.4$\,\mu$m and 0.8$\,\mu$m). Hubble Space Telescope (HST) observations at 0.8$\,\mu$m (rest-frame 0.2$\,\mu$m) reveal only isolated clumps at the galaxy outskirts, possibly tracing young stars and/or low dust obscuration. A RGB-image combining the HST and JWST images is shown in Fig. [1](#fig:fig1)b, while Fig. [1](#fig:fig1)a shows a zoomed-in view of the Big Wheel. The Big Wheel features a red center, visible only in the JWST near-infrared filters (green and red channels), and a stellar disk extending to at least 30 kiloparsecs in diameter. Spiral-arm features are visible, appearing clumpy in rest-frame ultraviolet, reminiscent of some spiral galaxies at $z \sim 0$ (cite: GildePaz2007). Its stellar half-light radius is 9.6 kiloparsecs along the major axis in the rest-frame optical (0.5$\,\mu m$), as measured using statmorph (cite: Rodriguez-Gomez2019) (see *Methods*).

![](bigspiral_figure1_v3.png)

Hydrogen H$\alpha$ spectroscopy obtained with the Near Infrared Spectrograph (NIRSpec) confirms the rotating-disk nature of Big Wheel.

Three spectroscopic slits (see *Methods*) were placed onto the galaxy (Fig. [2](#fig:fig2)a-c), including one covering the galaxy center. H$\alpha$ two-dimensional spectra are presented in Fig. [2](#fig:fig2)d-f, whereas the corresponding slit positions are indicated in Fig. [2](#fig:fig2)a-c.

Initial evidence supporting disk rotation can be gleaned from the slit spectrum covering the galaxy center (Fig. [2](#fig:fig2)d). Moving towards to the external regions, the velocity increases first and then plateaus at around $\pm 200$ km/s (prior to inclination correction). Such pattern is typical of disk galaxies with flat rotation curves (cite: Lelli2016). Additional features are present in the spectra, such as a bright clump which appears kinematically distinct from the disk (green box) and could be associated with a companion galaxy seen in projection.

![](bigspiral_figure2_v3b.png)

The H$\alpha$ spectra of the remaining slits (Fig. [2](#fig:fig2)e-f) also have patterns consistent with disk-like rotation. To demonstrate this, we measure the rotation velocities from the H$\alpha$ profiles across the slits as shown in Fig. [2](#fig:fig2)d-f (see *Methods*) and present the result as a velocity map in Fig. [2](#fig:fig2)g. As shown in Fig. [2](#fig:fig2)d-f, these profiles agree remarkably well over the main stellar disk body with predictions from a simple disk kinematic model, in which a flat rotation curve is adopted (yellow curves in Fig. [2](#fig:fig2)d-f).

The disk model, described in detail in *Methods*, includes six free parameters which specify the disk center location, major axis orientation, inclination, and normalization of the rotation curve. The model was fit to the data using the Markov Chain Monte Carlo scheme (cite: Foreman-Mackey2013). The best fit model is presented in Fig. [2](#fig:fig2)h and the residuals in Fig. [2](#fig:fig2)i. The maximum rotation velocity (corrected for inclination) $v_\mathrm{rot}$ is $280^{+32}_{-31}$ km/s, i.e. $4.5^{+1.4}_{-1.1}$ times the velocity dispersion $\sigma_\mathrm{int}$ ($61^{+17}_{-13}$ km/s; see *Methods*). These values indicate that the Big Wheel is rotationally supported and has a dispersion value consistent with (smaller) turbulent disks at similar and lower redshifts (cite: Kassin2012; ForsterSchreiber2020). Combining $v_\mathrm{rot}$ and $\sigma_\mathrm{int}$ using the commonly adopted relation in the literature(cite: Ubler2017) (see *Methods*) we obtain a circular velocity $v_\mathrm{circ}=304^{+32}_{-31}\,$km/s. The velocity map of the molecular gas obtained through ALMA observations (cite: Pensabene2024) covering the full galaxy, albeit with lower spatial resolution, shows consistent results (see *Methods*).

| Property | Value | Unit |
|:---|:---|:---|
| Right ascension (J2000) | 00h41m35.113s | \- |
| Declination (J2000) | -49d37m12.42s | \- |
| Redshift | 3.2452 | \- |
| Stellar mass | $3.7^{+2.6}_{-2.2}\times 10^{11}$ | solar mass ($M_\odot$) |
| Stellar mass (assuming a parametric SFH) | $1.7^{+1.4}_{-0.7}\times 10^{11}$ | solar mass ($M_\odot$) |
| Star-formation rate | $2.5^{+7.5}_{-2.1}\times 10^{2}$ | $M_\odot/$yr |
| Half-light radius | $1.27^{+0.07}_{-0.16}$, $9.6^{+0.5}_{-1.2}$ | arcsec, kiloparsec |
| Minor-to-major axis ratio | $0.69^{+0.03}_{-0.01}$ | \- |
| Disk inclination angle | $48^{+1}_{-4}$  (morphology) | degree |
|  | 52$_{-5}^{+5}\,\,$ (kinematics) | degree |
| H$\alpha$ rotational velocity($v_\mathrm{rot}$) | $280^{+32}_{-31}$ | km/s |
| H$\alpha$ velocity dispersion ($\sigma_\mathrm{int}$) | 61$^{+17}_{-13}$ | km/s |
| $v_\mathrm{rot}/\sigma_\mathrm{int}$ | 4.5$^{+1.4}_{-1.1}$ | \- |
| Circular velocity($v_\mathrm{circ}$) | $304^{+32}_{-31}$ | km/s |
| CO(4-3) line luminosity | $1.3\times 10^8$ | solar luminosity ($L_\odot$) |
| H$_2$ mass estimated from CO | $1.8^{+1.0}_{-0.8}\times 10^{11}$ | $M_\odot$ |
| Environment overdensity | $\geq 10$ | \- |
|  |  |  |

: **Properties of the Big Wheel galaxy**

The stellar mass and star formation rate (SFR) were obtained by fitting the photometry in seven filters against spectral energy distribution (SED) models with the prospector tool (cite: Leja2017) (see *Methods*). Flexible star formation histories (SFHs) and dust attenuation laws were adopted, as well as the potential emission from an active galactic nucleus (AGN). The best-fit stellar mass and SFR values are $3.7^{+2.6}_{-2.2}\times10^{11}\,M_\odot$ and $2.5^{+7.5}_{-2.1} \times 10^2 \,M_\odot/$yr, respectively. These results indicate that the Big Wheel is one of the most massive systems detected so far at $z\gtrsim 3$, some of which discovered only recently with JWST (cite: Nanayakkara2024).

![](bigspiral_figure4_rev.png)

The physical properties of the Big Wheel are summarized in Tab. [1](#tab:table1) and are compared to the observed galaxy population at similar redshifts in Fig. [3](#fig:fig4). Most intriguingly, the Big Wheel has a larger radius (measured at rest-frame 0.5$\,\mu m$) and is more massive than any other kinematically-confirmed disk galaxy discovered so far at similar redshifts (see Fig. [3](#fig:fig4)a and *Methods*). Fig. [3](#fig:fig4)b shows the size versus stellar mass relations for $z \sim 3$ star-forming galaxies for both observations and simulations, as well as the observed relation at $z\sim 0$. The Big Wheel is clearly offset to high values, both in terms of stellar mass and sizes, with respect to both the observed and simulated relations at $z \sim 3$.

In addition, in terms of size, the Big Wheel galaxy is more similar to $z \sim 0$ disk galaxies than other currently known disk galaxies at $z \sim 3$. As shown in Fig. [3](#fig:fig4)d, it is located on top of the stellar mass Tully-Fisher relation of the $z\sim 0$ disks (cite: Lelli2016) with a stellar mass and circular velocity similar to local “super-spirals”(cite: DiTeodoro2021). Despite the similarities to the $z\sim 0$ objects, the Big Wheel galaxy is actively growing in mass like other galaxies at $z\sim3$, with an SFR consistent with the trend of typical $z \sim 3$ star-forming galaxies (Fig. [3](#fig:fig4)c).

Our observations reveal that the Big Wheel is a giant rotating disk with physical properties unique for $z\sim 3$, raising questions about its formation scenario. Within the classical theoretical framework (cite: MMW1998; Bullock2001), the disk size is expected to be simply proportional to the halo size times the dimensionless halo spin parameter ($\lambda$)(cite: MMW1998; Bullock2001), with small deviations with halo concentration and disk-to-halo mass ratio. The halo $\lambda$ follows a distribution well constrained from simulations and can be fit with a log-normal function with an average of $\simeq0.035$ and a log-normal standard deviation (in log base 10) of $\simeq0.25$(cite: Bullock2001; Bryan2013) without significant variations with halo mass and redshift.(cite: Bryan2013; Zjupa2017).

Despite the model simplicity, its predictions are consistent with the observed galaxy size distributions both in terms of shape and scatter. In particular, the most recent observations at $z\simeq3$, find a log-normal size distribution with an intrinsic scatter of $\simeq0.22-0.28$(cite: Ward2023; Varadaraj2024), which is strikingly similar to the simple expectations mentioned. As shown in Fig. [3](#fig:fig4)b, the Big Wheel is at least three times larger than the expected size of star-forming, disk galaxies at its mass and redshift given the observed size-mass relation in random fields(cite: Ward2023; Varadaraj2024). The probability of randomly finding such a galaxy, if environment does not play a role,

is less than 2% (see *Methods* for details). The Big Wheel is one of the few star forming galaxies with rest-frame optical size measurement and a mass above 10$^{11}$ $M_\odot$ found so far at $z>3$, and the only one with confirmed kinematical measurements demonstrating its rotating disk nature. As such, its serendipitous discovery in one of the largest overdensities of galaxies found so far at $z\gtrsim3$ (cite: Pensabene2024) suggests that additional physical mechanisms could be at play in determining the size of massive disk galaxies in such regions of the universe.

Major mergers are expected to be more frequent than the cosmic average in overdense regions(cite: Jian2012) and a few models suggest that they can, in exceptional conditions, facilitate disk growth by increasing the disk spin rather than destroying it.(cite: Governato2009; Hopkins2009) In particular, models suggest that disks can survive disruption or reform afterwards if mergers have favorable orbital parameters and the progenitor galaxies are gas-rich(cite: Governato2009; Hopkins2009). If these predictions are correct, the presence of such a giant disk in a large overdensity of galaxies could imply, e.g., a connection between the dense environment and an elevation of the gas fraction of galaxies. In turn, the high gas content of galaxies could be caused by more efficient accretion of the gas from the Cosmic Web in denser environments at early cosmic epochs.

Alternatively, large disks could also be the result of accretion of cosmic gas with coherent angular momentum, resulting in larger disk-to-halo angular momentum ratio with respect to expectations from previous analytical models (cite: Stewart2017).

The relevant galaxy formation and evolution mechanisms are still not well constrained to date. To the best of our knowledge, current cosmological simulations (cite: Costantin2023; LaChance2024), some of which are presented in Fig. [3](#fig:fig4), have not predicted disks as large as the Big Wheel galaxy at $z\gtrsim3$ at comparable masses.

In addition to its uncertain origin, the subsequent evolution of the Big Wheel also remains unknown. The fact that the galaxy is not growing in isolation and the presence of at least one companion galaxy as shown in Fig. [2](#fig:fig2) could suggest future mergers responsible for an evolution in the Big Wheel properties.

Moreover, its dense environment suggests the presence of a proto-cluster (cite: Pensabene2024), hinting that its descendant might be one of the most massive members of today’s galaxy clusters. Nevertheless, further studies are needed to understand how common giant disks like the Big Wheel are in dense environments at early cosmic epochs and whether their physical properties and number densities are consistent with the putative progenitors of today’s most massive cluster galaxies.

# Methods

Imaging data was obtained from HST Program GO 17065 (PI: Cantalupo) and JWST Program GO 1835 (PI: Cantalupo) using the NIRCam filters, F150W2 and F322W2, each for 1632s of exposure and HST filters ACS/WFC F625W and ACS/WFC F814W, for 10 and 12 orbits, respectively. The JWST data are reduced and combined using the official jwst pipeline (v1.9.3; \[\]) with calibration reference file version jwst_1039.pmap. We implemented customized steps in the reduction to remove the correlated readout noises and stray light, following the practices adopted among the literature (cite: Bagley2023). The image resolutions in terms of the full width of the half maximum (FWHM) are 0.12 arcsec, 0.12 arcsec, 0.05 arcsec, and 0.11 arcsec for F625W, F814W, F155W2, and F322W2, respectively.

We also obtained near-infrared data with the Very Large Telescope (VLT) in 2022 as part of a program in P110 (PI: Cantalupo). The High Acuity Wide field K-band Imager (HAWKI) was used in the Ground Layer Adaptive Optics mode, leading to spatial resolutions of 0.4 arcsec in FWHM, using the filters CH4, H, and Ks. On-source exposure times were 60 min, 100 min, and 100 min, respectively. The images of each filter were reduced and combined using the official pipeline esorex (cite: esorex2015).

Photometry was performed on the images described above using the Source Extractor tool (cite: Bertin1996). For the measurement, the image mosaics were resampled to a common grid of 0.06$\times$0.06 arcsec pixels using the drizzle package (cite: Fruchter2002). Source Extractor was run in dual mode for the space-based and ground-based data, using the F322W2 and H mosaics as detection images, respectively.

![](bigspiral_extfig1_rev1.png)

Follow-up spectroscopic observations using NIRSpec were obtained as a part of the same JWST program as above. The observations used the Micro-Shutter Assembly (MSA), with the F170LP/G235H filter and grating pair, leading to a resolving power $R \sim 3200$ or equivalently 95 km/s in FWHM at the observed wavelength of the H$\alpha$ line ($2.8\,\mu$m). The exposure time was $\sim 3$ hours for each of the three MSA slits. The data for each slit were reduced and combined using the official jwst pipeline (v1.11.3) with calibration reference file version jwst_1097.pmap. The spatial resolution of the data, which is inferred with the webbpsf tool (cite: Perrin2014), is 0.13 arcsec in FWHM at $2.8\,\mu$m and resampled to a pixel scale of 0.10 arcsec. The smooth background and galaxy continua have been removed by applying a median filter with a width of 3000 km/s to each pixel row of the 2D spectra and subtracting the filtered product from the original spectra. We also extracted an integrated 1D spectrum from the combined 2D spectra. The resulting 1D spectrum and identified emission lines are shown in Extended Data Fig. [4](#fig:efig1)a. The galaxy redshift is inferred from the observed wavelengths of the H$\alpha$, \[N II\], and H$\beta$ lines on the spectrum.

The Big Wheel was also observed with the Atacama Large (sub-)Millimeter Array (ALMA) in Cycle 8 (ID: 2021.1.00793.S; PI: Cantalupo), the details of which are provided in \[14\]. Data cleaning was performed down to $1.5\sigma$ with a circular mask of $2''$ in radius, which encloses emission of the galaxy in the cube. The synthesized beam size (FWHM) of the “cleaned" data cube is $1\rlap{.}''4\times1\rlap{.}''3$ at $109.00\,{\rm GHz}$. We fit the spectral continua with zeroth-order polynomials and subtracted them from the cube using the task `imcontsub` of Common Astronomy Software Application (cite: CASA2022).

The Big Wheel was also observed using the Advanced CCD Imaging Spectrometer onboard the Chandra X-ray Observatory during 2022-2023 (PI: Cantalupo), with a total of 634 ks of exposure. The galaxy is associated with a 3-$\sigma$ X-ray point source with a luminosity of $L_{2-10\, keV} = 9.8^{+1.8}_{-1.7} \times 10^{43}\,\mathrm{erg\cdot s}^{-1}$, which is measured assuming a photon index of 1.7-1.8 and corrected for absorption. Such a luminosity is consistent with the typical value of a moderate-luminosity Seyfert AGN (cite: Ueda2014). The existence of the AGN was also confirmed from the ratios of the nebular emission lines from the galaxy center ($r<1.5$ kpc) on the NIRSpec spectrum, according to the criteria by \[\], whereas the emission lines from all other parts of the galaxy are consistent with being driven by star formation (Extended Data Fig. [4](#fig:efig1)b).

![](bigspiral_extfig2.png)

The half-light radius in the rest-frame optical, is measured from the background-subtracted images in the NIRCam F150W2 and F322W2 filters. The galaxy images in these filters, as well as the F814W image, are shown in Extended Data Fig. [5](#fig:efig2). We measured the radius by running a non-parametric morphological analysis using $^{16}$. This method is free from any assumption regarding the functional form of the galaxy light profile. The radius measurements were made for both the F150W2 and F322W2 filters. For each filter, we measured the radius of an ellipse enclosing half of the total light of the galaxy. Throughout the measurement, the radius is measured along the major axis of the ellipse and the orientation and ellipticity of the ellipse are fixed to values calculated from the mathematical moments of the pixel flux density distribution, which in turn are physically determined by the global morphology of the galaxy (see \[16, \] for details). The half-light radii measured from the two filters are 1.34 arcsec and 1.12 arcsec, respectively. As a check for consistency, we also measured the radius by fitting the Sérsic(cite: Sersic1963) profiles with statmorph using the PSFs measured from stars in the field. The resulting half-light radii are all within 5% of the values reported above. Masking out clump A in Fig. 2a, which might be a companion galaxy, leads to only negligible ($<$2%) changes in measured sizes.

The radial light profiles, measured along the galaxy major axis, are shown in Extended Data Fig. [6](#fig:efig2b)a together with exponential disk profiles for comparison. Both the F150W2 and F322W2 profiles are consistent with exponential disks with deviations in the central regions, which are at least partially due to the diffuse dust attenuation (panel b, left) as corroborated by the smoother dust-corrected mass density profile shown in panel c. The H$\alpha$ attenuation inferred from the H$\alpha$-to-H$\beta$ ratios following \[\] is also shown for reference, but we caution that it may be subject to NIRSpec flux calibration errors(cite: DEugenio2024) and traces only sightlines toward the youngest stars which does not reflect attenuation to the full continuum light seen in the two broad filters.(cite: Calzetti2001; Nelson2019) We evaluated the uncertainties of the size measurements, which could be caused by beam-smearing effects due to the finite PSF of the imaging data and the imaging noise. To quantify the effects, we created a model exponential disk with an intrinsic half-light radius of 1 arcsec, convolved the model image with the NIRCam PSF, and added artificial noise to the image. Then, we measured the half-light radius from this synthetic image in the same way as was done with the real data. For each filter, such a series of steps was repeated 500 times, from which a distribution of the measured radii was obtained. We found from the distribution that the measured sizes deviate from the intrinsic value (1 arcsec) by only 2.8% and 3.4% for F150W2 and F322W2 at the 3-sigma confidence level, indicating that the uncertainties due to beam-smearing and noises are relatively small. These percentage values are adopted as the relative uncertainties of our size measurements.

In addition, we investigated whether the Big Wheel is subject to any gravitational lensing magnification caused by any foreground (i.e., low-redshift) galaxy nearby or galaxy cluster. This possibility is rejected based on the non-detection of any foreground cluster according to the X-ray and galaxy redshift measurements available to the field and the non-detection of any galaxy nearby with a mass large enough for lensing.

Finally, following the convention adopted in the literature,$^{5,8,}$(cite: Mowla2019) we inferred the half-light radius of the Big Wheel galaxy at rest-frame 0.5$\,\mu$m. It was calculated by interpolating between the radius values measured in the two NIRCam filters, under the assumption that the radius is a linear function of wavelength. To account for the systematic uncertainty due to the interpolation conservatively, we adopted the sizes measured in the two individual filters as the bounds of the uncertainty range, and then combined in quadrature this uncertainty with the propagated uncertainty due to the beam-smearing and noise. The final calculated half-light radius is $1.27^{+0.07}_{-0.16}$ arcsec, or equivalently $9.6^{+0.5}_{-1.2}$ kiloparsecs.

![](bigwheel_aperphot_lightmassprofile_rev2.png)

One-dimensional H$\alpha$ kinematical profiles have been obtained from the 2D spectra from each pixel row, which spans 0.1 arcsec along the slit, after convolving them with the instrument line spread function. The 1D spectra were then fit with a Gaussian using emcee.$^{18}$ Outputs of the fits include the rotation velocity (Gaussian centroid) and velocity dispersion (Gaussian width) as a function of the spatial location along the slit, which are shown in Extended Data Fig. [7](#fig:efig3). Using the rotation velocities measured from the three slits, we created a velocity map of the galaxy (Fig. 2g).

For the disk modeling, we adopted a flat rotation curve using the galpy python package (cite: Bovy2015). The rotation curve model has a form corresponding to the commonly-used pseudo-isothermal potential(cite: Burkert1995). It has two free parameters determining the location where the rotation curve turns flat and the plateau velocity, respectively. We created a model galaxy disk using this rotation curve, with an inclination angle and orientation angle of the disk major axis as two more free parameters. Two other free parameters are included which anchor the galaxy center (X, Y). Then, we created a velocity map from this six-parameter disk model by calculating the velocity along the line of sight for each part of the disk. The model map was fitted against the observed velocity map using emcee. After the fitting is done, we calculated the 50th-percentiles of the parameter posterior distributions and used these parameters to create the best-fit disk model.

Based on the measurements and modeling, we derived the following galaxy kinematic properties. First, we calculated the $v_\mathrm{rot}$, defined as the maximum rotation velocity after inclination correction at 1 half-light radius, where the rotation curve flattens. We calculated the 16-84th percentiles of the $v_\mathrm{rot}$ posterior as the 1-sigma uncertainty from fitting. In addition, wiggles and other small variations from perfect rotating-disk motion are seen in the velocity profiles in Extended Data Fig. [7](#fig:efig3). Such features are comparable to the ones commonly seen in other disk galaxies in the local universe, including apparently isolated sources (e.g., \[\]), and they might also contribute to the uncertainty as a systematic term. To quantify this, we calculated the mean absolute deviation of the observed rotation curve with respect to the model (de-projected for inclination) and use it as an upper limit for the systematic uncertainty, which was then combined with the fitting uncertainty as the full uncertainty of $v_\mathrm{rot}$. Second, we measured the averaged intrinsic velocity dispersion $\sigma_\mathrm{int}$ as the median of the dispersion values measured from the two off-center slits in Extended Data Fig. [7](#fig:efig3)b-c, where the beam-smearing effect is expected to be minimal (see below). The 16th and 84th percentiles of the dispersion values in Extended Data Fig. [7](#fig:efig3)b-c are quoted as the 1-sigma uncertainty range. The values of $v_\mathrm{rot}$ and $\sigma_\mathrm{int}$ are listed in Tab. 1. Finally, we calculated the circular velocity $v_\mathrm{circ}$, which is used in Fig. 3d, using the following relation adopted in \[7, \]: $v_\mathrm{circ}^2 = v_\mathrm{rot}^2 + 2 \times 1.68\ (R/R_\mathrm{eff})\ \sigma_\mathrm{int}^2$, in which $R$ is where $v_\mathrm{rot}$ was measured in terms of radial distance and equal to one effective radius ($R_\mathrm{eff}$) for the Big Wheel galaxy. The calculated value of $v_\mathrm{circ}$ is $304^{+32}_{-31}\,$km/s.

![](bigspiral_extfig3_v2.png)

We investigated the effect of the finite spatial resolution of the observations to the modeling described above, namely the beam-smearing effect (cite: Weiner2006). We found that it has no substantial impact on the kinematic measurements, since the NIRSpec spatial resolution element (0.13 arcsec) is substantially smaller than the galaxy size. To justify this, we created a model galaxy with an exponential 2D flux density profile and an intrinsic velocity map identical to what is shown in Fig. 2h. We created a 3D mock cube of the intrinsic H$\alpha$ line emission based on this setup. Next, we convolved each wavelength slice of this cube by the instrument PSF to get the synthetic cube “seen” at the JWST resolution and produce the corresponding velocity map. We found that this map deviates from the intrinsic velocity map by no more than 15 km/s, except for the region within 0.2 arcsec of the center, confirming that the beam-smearing effect has negligible impact for most parts of the galaxy.

The CO velocity map of the Big Wheel galaxy from the ALMA observations was obtained through the first-moments of the CO(4–3) profiles. The map is shown in Extended Data Fig. [8](#fig:fig3)a, whereas the H$\alpha$ velocity map is shown in Extended Data Fig. [8](#fig:fig3)b for comparison. The CO map has a substantially larger PSF than the H$\alpha$ map and, as a result, shows narrower spans of velocity due to the stronger beam-smearing effect (cite: Weiner2006). Nevertheless, the CO map shows smooth velocity gradients oriented along the galaxy major axis similarly to the H$\alpha$, providing evidence that both the cold molecular and warm ionized gas rotates in a similar fashion. The observed CO kinematics is quantitatively consistent with the H$\alpha$ kinematics once the ALMA PSF is taken into account, as shown in Extended Data Fig. [9](#fig:efig7). In addition, the gas mass was also measured from the ALMA data and listed in Tab. 1, obtained using the CO-to-H$_2$ conversion factors described in \[14\].

![](bigspiral_figure3.png)

![](biggal_diskrotcurve_beamsemaring_re1.12arcsec_sersicn1.00.png)

The stellar mass and star formation rate (SFR) were measured from SED fits with the tool.$^{17,}$(cite: Johnson2021) Photometric flux densities measured from seven filters are used in the fit: ACS F625W, ACS F814W, NIRCam F150W2, HAWKI CH4, HAWKI H, HAWKI Ks, and NIRCam F322W2. The measured flux densities and the corresponding best-fit SED model are presented in Extended Data Fig. [10](#fig:efig4). For the fitting, we fixed the redshift to the value measured from the NIRSpec spectrum. A non-parametric form of the star formation history with a prior favoring continuity(cite: Wang2024) was adopted, binned into seven consecutive ranges in look-back time: 0-50 Myr, 50-100 Myr, 100-150 Myr, 150-200 Myr, 200-400 Myr, 400-800 Myr, and 800-1900 Myr. A Chabrier(cite: Chabrier2003) initial mass function (IMF) and a flexible dust attenuation law as described in \[\] are adopted. Other assumptions of the fitting procedure, including the forms of the Bayesian priors, are the same as described in \[\]. Emission from the AGN was also modeled following the prescription described in \[\], although the relevant parameters were unconstrained by the fit. The total stellar mass and SFR (averaged over 100 Myr) of the galaxy were calculated as the 50th-percentiles of the Bayesian posteriors. The uncertainties were calculated from the 5-95th percentiles of the posteriors and added in quadrature with the systematic uncertainties due to the fitting assumptions as described in \[\]. The inferred stellar mass and SFR are $3.7^{+2.6}_{-2.2} \times 10^{11}\,M_\odot$ and $2.5^{+7.5}_{-2.1} \times 10^2 \,M_\odot/$yr, respectively. For comparison, from the H$\alpha$ fluxes contained with the three NIRSpec slits, an SFR of about $1.5\times 10^2 \,M_\odot/$yr (prior to dust correction) was estimated. We noticed though that the slits only cover about 20% of the galaxy.

We examined systematic uncertainties of the stellar mass due to the presence of the faint AGN in the center. First, we put an upper limit to its potential contribution to the integrated galaxy fluxes via aperture photometry. Specifically, we measured the fluxes in the HST and JWST filters from within 0.3 arcsec of the galaxy center, where most of the AGN emission is expected according to the PSFs. We found that this region contributes less than 1% and 15% of the total galaxy light in the HST and JWST filters, respectively, justifying that the AGN has only minor contributions in the rest-frame UV-to-optical. Second, we performed annulus-by-annulus spatially resolved SED fitting with prospector using the HST and JWST data. With identical fitting setups as described above and conservatively excluding the $r<0.3$ arcsec region, we found that the resulting mass decreases by only 0.08 dex with respect to the value from the integrated fitting above (Extended Data Fig. [6](#fig:efig2b)c,d). Such a decrease is negligible compared to the stellar mass uncertainty (0.3 dex) reported above, and thus we conclude that the AGN has no significant impact on mass measurements. The mass profile in Extended Data Fig. [6](#fig:efig2b)c appears to have small variations from a perfectly smooth disk profile (dashed line) by $\pm$0.2 dex, which are, however, within the errorbars. These features are also commonly found with comparable amplitudes in other disk galaxies at $z=0$, including apparently isolated sources(cite: deBlok2008).

We conducted two consistency checks for the SED fit described above. First, we repeated the fit with a parametric star formation history, which was adopted for stellar mass measurements by the majority of the observational studies included for comparison in Fig. 3. The adopted history in a delayed exponentially declining form. The stellar mass inferred is $1.7^{+1.4}_{-0.7}\times 10^{11}\,M_\odot$, moderately lower than that reported from the non-parametric fit but still consistent within uncertainties. Furthermore, we also performed SED fit using the code CIGALE (cite: Burgarella2005; Noll2009; Boquien2019). It models both optical/infrared and X-ray flux densities, the latter measured with Chandra, based on the prescriptions described by \[\]. The fitting assumptions are similar to those adopted for prospector, except that the SFH is assumed to have a delayed exponentially declining form. According to the fitting results in Extended Data Fig. [11](#fig:efig5), the AGN emission (orange curve) has only minimal contribution ($\lesssim10^{-3}$) to the observed fluxes (filled circles) in the optical and infrared filters. The best-fit stellar mass and SFR (averaged over 100 Myr) are $2.5 \times 10^{11}\,M_\odot$ and $1.5 \times 10^2 \,M_\odot/$yr, respectively, both within the uncertainty ranges inferred by prospector.

![](bigspiral_extfig4_v2.png)

![](cigale_bestfit_jun2024.png)

Disk galaxies at $z$=3-4 from the literature that were confirmed by kinematics and measured for size are included in Fig. 3a. They are from ground-based studies based on rest-frame optical emission lines (cite: Gnerucci2011; Livermore2015; Turner2017; Gillman2019), except for two objects which are based on the CO emission lines with ALMA (cite: Swinbank2015) and optical emission lines with JWST (cite: Wu2023). All the disk galaxies were selected to have rotational velocities greater than the velocity dispersions, i.e., $v_\mathrm{rot}>\sigma_\mathrm{int}$, a lenient disk criterion commonly adopted in the literature.$^{7,19,}$(cite: Simons2017; Wisnioski2015) The stellar masses of all the disk galaxies were inferred using a Chabrier(cite: Chabrier2003) or Kroupa IMF(cite: Kroupa2001), except for the AMAZE(cite: Maiolino2008) subsample in Gnerucci et al(cite: Gnerucci2011) which adopt a Salpeter IMF(cite: Salpeter1955). We adjust the latter to the Chabrier IMF by subtracting the reported mass values by 0.24 dex (cite: Courteau2014; Santini2015). We also note that disks have also been identified kinematically beyond z=4, which are not included in Fig. 3. These kinematically-confirmed disks were mostly discovered with ALMA, with one discovered with JWST.$^{4,}$(cite: Carniani2013; Jones2017; Tadaki2018; Neeleman2019; Rizzo2021; Rizzo2023; Fraternali2021; Fujimoto2021; Lelli2021; Tsukui2021; Herrera-Camus2022; Nelson2023; Parlanti2023; Roman-Oliveira2023) The largest galaxies reported by these studies are around 5 kiloparsecs in radius (cite: Neeleman2019; Parlanti2023), which are approximately two times smaller than the Big Wheel galaxy.

We note that kinematical measurements are essential for the confirmation of disks, because measurements using imaging data alone may be subject to ambiguity of interpretation due to clumps, mergers, dust, and peculiar galaxy geometry, all found common at $z\gtrsim 1$.$^{7,}$(cite: vanderwel2014; Guo2015; Vega-Ferrero2024) As an evidence supporting this argument, we examined the galaxies from \[5\] at $z=3-4$ with large radii ($>0.5\,$arcsec) measured from HST near-infrared images, and found that the majority of them, if not all, have irregular or major merger-like morphology rather than disk-like. For this reason, only galaxies with kinematic measurements were considered for comparison in Fig. 3a.

The size-mass scaling relations in Fig. 3b are measured at or around the rest-frame $0.5\,\mu$m, the same wavelength where the size of the Big Wheel galaxy is measured. We include only star-forming galaxies.$^{8,9,11,12,}$(cite: Mowla2019; Ormerod2024) The size-mass relation of Ward et al\[8\] are measured in two redshift bins, $z=2-3$ and $z=3-5.5$, and we adopted the average values to match the redshift of our galaxy ($z=3.245$). The size-mass relation of Costantin et al$^{11}$ is provided as an analytical function of redshift and we adopted the relation at $z=3.2$. The size-mass relation of Mowla et al(cite: Mowla2019) is determined in the work as the median trend of a statistical galaxy sample at $z=0.1-0.5$.

Based on the literature measurements, the probability of finding a star forming galaxy, independent of kinematical confirmation, with the size of the Big Wheel at its stellar mass and redshift in random fields was obtained as follows. First, we calculated the expected galaxy size at the mass and redshift of the Big Wheel, using the relations from two most recent and complete JWST studies as shown in Fig. 3b$^{8,9}$. We found it to be 0.41 dex and 0.70 dex smaller than the observed size of the Big Wheel in log using \[8\] and \[9\] relations, respectively. The distribution of sizes is well constrained as a log-normal in these studies with

an intrinsic log-normal scatter in exponential units ($\sigma_{\mathrm{log(R_e)}}$) of these size-mass relations of 0.22 dex and 0.28 dex, respectively. Therefore the corresponding probabilities of finding a galaxy equal to or larger than the Big Wheel in random fields are 2% and 0.6% according to the two studies, respectively.

In addition, star forming galaxies with masses larger than 10$^{11}\ M_\odot$, such as the Big Wheel (which has a mass of at least $10^{11}\ M_\odot$), are extremely rare, independent of their sizes. This can be quantified again by using the previously quoted JWST results$^{8,9}$. Only two star forming galaxies above a mass of $10^{11}\ M_\odot$ are detected in these surveys above redshift 3 over a combined area of 440 arcmin$^2$ and no galaxies have a mass above $10^{11}\ M_\odot$, the lower limit for the Big Wheel considering different methodologies.

Thus, in order to randomly discover a galaxy with a mass of at least $10^{11}\ M_\odot$ at redshift greater than 3 and sizes similar to the Big Wheel (using the conservative probability limit of 2%), if the environment does not play a role, we would have required a survey with a size of at least 11 thousand arcmin$^2$.

Regarding the general galaxy population shown in Fig. 3c, they are selected to be at $z=3.0-3.5$ from \[\]. In the same panel, scaling relations from two other literature studies are also shown (cite: Speagle2014; Popesso2023). The $z\sim 3.5$ galaxies in Fig. 3d were selected to have the rotational velocity ($v_\mathrm{rot}$) greater than the velocity dispersion ($\sigma_\mathrm{int}$). We inferred their circular velocities ($v_\mathrm{circ}$) by performing a correction for disordered motions to $v_\mathrm{rot}$, which was measured at 2 times the half-light radius (cite: Turner2017), following the same equation as used for the Big Wheel above. The $z\sim 0$ galaxies in the same panel are from \[22\] and \[\]. The stellar masses in these studies were all inferred assuming a Chabrier(cite: Chabrier2003) IMF.

Supplementary Information is available for this paper.

This project was supported by the European Research Council (ERC) Consolidator Grant 864361 (CosmicWeb). A.P. acknowledges the support from Fondazione Cariplo grant no. 2020-0902. M.M. acknowledges funding from NASA via HST-GO-17065. T.N. acknowledge support from Australian Research Council Laureate Fellowship FL180100060. This work is based in part on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program #1835. Support for program #1835 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127. This research is based on observations made with the NASA/ESA Hubble Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with program 17065. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The scientific results reported in this article are based in part on observations made by the Chandra X-ray Observatory. This work is also based on observations collected at the European Southern Observatory under ESO programme (110.23ZX).

W.W. was responsible for the JWST and HST observations, reduced the data from JWST, HST, VLT, conducted the imaging, spectroscopic, and modeling analyses of this work, produced the figures and worked in collaboration with S.C. to the text writing. S.C. led the proposal and planning for the JWST, HST, and VLT observations used in this work, contributed to the observational, theoretical analyses and interpretation of the data and results including text writing. A.P. was responsible for the ALMA observations, conducted the analysis and modeling of ALMA data, contributed to the interpretation and discussion. M.G. contributed to the observation planning, assisted in reducing the VLT data, performed the SED fitting, and contributed to the interpretation of the results. A.T. planned the Chandra observations, reduced the Chandra data, and contributed to analyses relevant to the AGN properties. C.S. assisted with the JWST target selection, observation planning, and data reduction, and contributed to the interpretation of science results. M.Fossati and M.Fumagalli assisted with the JWST proposal preparation, contributed to the interpretation and discussion of the observational results. T.L., S.dB., and G.Q. contributed to the comparison with simulations and relevant discussion. M.M. assisted with the JWST NIRSpec MSA mask design, preparation of the APT files, advised on observing and data reduction strategies, and contributed to the interpretation and discussion. S.G., J.M., R.M., T.N., and G.P. contributed to the proposal planning, data interpretation and discussion for the JWST and HST observations.

The JWST NIRCam data (Program ID: GO 1835) are publicly available at <https://mast.stsci.edu/search/ui/#/jwst>. The HST data (Program ID: 17065) are publicly available at <https://mast.stsci.edu/search/ui/#/hst>. This paper also makes use of the ALMA dataset ADS/JAO.ALMA#2021.1.00793.S. which can be obtained at <http://almascience.nao.ac.jp>. The Source Extractor code is available at <https://astromatic.github.io/sextractor/>. The statmorph package is available to download at <https://github.com/vrodgom/statmorph/>. The emcee package is available at <https://emcee.readthedocs.io/en/stable/>. The galpy package is available at <https://github.com/jobovy/galpy>. The prospector code is available to download at <https://github.com/bd-j/prospector>. The CIGALE code is available at <https://cigale.lam.fr/>. The drizzle code is available to download at <https://github.com/spacetelescope/drizzle>.

The authors declare no competing interests.

Correspondence and requests for materials should be addressed to Weichen Wang (weichen.wang@unimib.it).

10 url urlprefix

(ref: Genzel2006) Genzel, R. *et al.* . *Nature* **442**, 786–789 (2006).

(ref: Law2012) Law, D. R. *et al.* . *Nature* **487**, 338–340 (2012).

(ref: Genzel2017) Genzel, R. *et al.* . *Nature* **543**, 397–401 (2017).

(ref: Rizzo2020) Rizzo, F. *et al.* . *Nature* **584**, 201–204 (2020).

(ref: vanderwel2014b) van der Wel, A. *et al.* . *Astrophys. J.* **788**, 28 (2014).

(ref: Ogle2016) Ogle, P. M., Lanz, L., Nader, C. & Helou, G. . *Astrophys. J.* **817**, 109 (2016).

(ref: ForsterSchreiber2020) Förster Schreiber, N. M. & Wuyts, S. . *Annu. Rev. Astron. Astrophys.* **58**, 661–725 (2020).

(ref: Ward2023) Ward, E. *et al.* . *Astrophys. J.* **962**, 176 (2024).

(ref: Varadaraj2024) Varadaraj, R. G. *et al.* . *Mon. Not. R. Astron.* (2024).

(ref: MMW1998) Mo, H. J., Mao, S. & White, S. D. M. . *Mon. Not. R. Astron.* **295**, 319–336 (1998).

(ref: Costantin2023) Costantin, L. *et al.* . *Astrophys. J.* **946**, 71 (2023).

(ref: LaChance2024) LaChance, P. *et al.* . *Preprint at arxiv.org/abs/2401.16608* (2024).

(ref: Lelli2016) Lelli, F., McGaugh, S. S. & Schombert, J. M. . *Astron. J.* **152**, 157 (2016).

(ref: Pensabene2024) Pensabene, A. *et al.* . *Astron. Astrophys.* **684**, A119 (2024).

(ref: GildePaz2007) Gil de Paz, A. *et al.* . *Astrophys. J. Suppl. Ser.* **173**, 185–255 (2007).

(ref: Rodriguez-Gomez2019) Rodriguez-Gomez, V. *et al.* . *Mon. Not. R. Astron.* **483**, 4140–4159 (2019).

(ref: Foreman-Mackey2013) Foreman-Mackey, D., Hogg, D. W., Lang, D. & Goodman, J. . *Publ. Astron. Soc. Pac.* **125**, 306 (2013).

(ref: Kassin2012) Kassin, S. A. *et al.* . *Astrophys. J.* **758**, 106 (2012).

(ref: Ubler2017) Übler, H. *et al.* . *Astrophys. J.* **842**, 121 (2017).

(ref: Leja2017) Leja, J., Johnson, B. D., Conroy, C., van Dokkum, P. G. & Byler, N. . *Astrophys. J.* **837**, 170 (2017).

(ref: Nanayakkara2024) Nanayakkara, T. *et al.* . *Scientific Reports* **14**, 3724 (2024).

(ref: DiTeodoro2021) Di Teodoro, E. M., Posti, L., Ogle, P. M., Fall, S. M. & Jarrett, T. . *Mon. Not. R. Astron.* **507**, 5820–5831 (2021).

(ref: Bullock2001) Bullock, J. S. *et al.* . *Astrophys. J.* **555**, 240–257 (2001).

(ref: Bryan2013) Bryan, S. E. *et al.* . *Mon. Not. R. Astron.* **429**, 3316–3329 (2013).

(ref: Zjupa2017) Zjupa, J. & Springel, V. . *Mon. Not. R. Astron.* **466**, 1625–1647 (2017).

(ref: Jian2012) Jian, H.-Y., Lin, L. & Chiueh, T. . *Astrophys. J.* **754**, 26 (2012).

(ref: Governato2009) Governato, F. *et al.* . *Mon. Not. R. Astron.* **398**, 312–320 (2009).

(ref: Hopkins2009) Hopkins, P. F., Cox, T. J., Younger, J. D. & Hernquist, L. *Astrophys. J.* **691**, 1168–1201 (2009).

(ref: Stewart2017) Stewart, K. R. *et al.* . *Astrophys. J.* **843**, 47 (2017).

(ref: Bushouse2022) Bushouse, H. *et al.* , 1.8.0 (2022).

(ref: Bagley2023) Bagley, M. B. *et al.* . *Astrophys. J. Lett.* **946**, L12 (2023).

(ref: esorex2015) ESO CPL Development Team. . Astrophysics Source Code Library, record ascl:1504.003 (2015).

(ref: Bertin1996) Bertin, E. & Arnouts, S. *A&AS* **117**, 393–404 (1996).

(ref: Fruchter2002) Fruchter, A. S. & Hook, R. N. . *Publ. Astron. Soc. Pac.* **114**, 144–152 (2002).

(ref: Kewley2001) Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A. & Trevena, J. . *Astrophys. J.* **556**, 121–140 (2001).

(ref: Perrin2014) Perrin, M. D. *et al.* , J., Jacobus M., Clampin, M., Fazio, G. G. & MacEwen, H. A. (eds) *Updated point spread function simulations for JWST with WebbPSF*. (eds Oschmann, J., Jacobus M., Clampin, M., Fazio, G. G. & MacEwen, H. A.) *Space Telescopes and Instrumentation 2014: Optical, Infrared, and Millimeter Wave*, Vol. 9143 of *Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series*, 91433X (2014).

(ref: CASA2022) CASA Team *et al.* . *Publ. Astron. Soc. Pac.* **134**, 114501 (2022).

(ref: Ueda2014) Ueda, Y., Akiyama, M., Hasinger, G., Miyaji, T. & Watson, M. G. . *Astrophys. J.* **786**, 104 (2014).

(ref: Baldwin1981) Baldwin, J. A., Phillips, M. M. & Terlevich, R. *Publ. Astron. Soc. Pac.* **93**, 5–19 (1981).

(ref: Sersic1963) Sérsic, J. L. . *Bol. Asoc. Argent. Astron. Plata Argent.* **6**, 41–43 (1963).

(ref: Dominguez2013) Domı́nguez, A. *et al.* . *Astrophys. J.* **763**, 145 (2013).

(ref: DEugenio2024) D’Eugenio, F. *et al.* . *Preprint at arxiv.org/abs/2404.06531* (2024).

(ref: Calzetti2001) Calzetti, D. . *Publ. Astron. Soc. Pac.* **113**, 1449–1485 (2001).

(ref: Nelson2019) Nelson, E. J. *et al.* . *Astrophys. J.* **870**, 130 (2019).

(ref: Mowla2019) Mowla, L. A. *et al.* . *Astrophys. J.* **880**, 57 (2019).

(ref: Lange2015) Lange, R. *et al.* . *Mon. Not. R. Astron.* **447**, 2603–2630 (2015).

(ref: Bovy2015) Bovy, J. . *Astrophys. J. Suppl. Ser.* **216**, 29 (2015).

(ref: Burkert1995) Burkert, A. . *Astrophys. J. Lett.* **447**, L25–L28 (1995).

(ref: Rubin1978) Rubin, V. C., Ford, J., W. K. & Thonnard, N. *Astrophys. J. Lett.* **225**, L107–L111 (1978).

(ref: Noordermeer2007) Noordermeer, E., van der Hulst, J. M., Sancisi, R., Swaters, R. S. & van Albada, T. S. . *Mon. Not. R. Astron.* **376**, 1513–1546 (2007).

(ref: deBlok2008) de Blok, W. J. G. *et al.* . *Astron. J.* **136**, 2648–2719 (2008).

(ref: NestorShachar2023) Nestor Shachar, A. *et al.* . *Astrophys. J.* **944**, 78 (2023).

(ref: Weiner2006) Weiner, B. J. *et al.* . *Astrophys. J.* **653**, 1027–1048 (2006).

(ref: Johnson2021) Johnson, B. D., Leja, J., Conroy, C. & Speagle, J. S. . *Astrophys. J. Suppl. Ser.* **254**, 22 (2021).

(ref: Wang2024) Wang, B. *et al.* . *Astrophys. J. Suppl. Ser.* **270**, 12 (2024).

(ref: Chabrier2003) Chabrier, G. . *Publ. Astron. Soc. Pac.* **115**, 763–795 (2003).

(ref: Charlot2000) Charlot, S. & Fall, S. M. . *Astrophys. J.* **539**, 718–731 (2000).

(ref: Pacifici2023) Pacifici, C. *et al.* . *Astrophys. J.* **944**, 141 (2023).

(ref: Burgarella2005) Burgarella, D., Buat, V. & Iglesias-Páramo, J. . *Mon. Not. R. Astron.* **360**, 1413–1425 (2005).

(ref: Noll2009) Noll, S. *et al.* . *Astron. Astrophys.* **507**, 1793–1813 (2009).

(ref: Boquien2019) Boquien, M. *et al.* . *Astron. Astrophys.* **622**, A103 (2019).

(ref: Yang2022) Yang, G. *et al.* . *Astrophys. J.* **927**, 192 (2022).

(ref: Gnerucci2011) Gnerucci, A. *et al.* . *Astron. Astrophys.* **528**, A88 (2011).

(ref: Livermore2015) Livermore, R. C. *et al.* . *Mon. Not. R. Astron.* **450**, 1812–1835 (2015).

(ref: Turner2017) Turner, O. J. *et al.* . *Mon. Not. R. Astron.* **471**, 1280–1320 (2017).

(ref: Gillman2019) Gillman, S. *et al.* . *Mon. Not. R. Astron.* **486**, 175–194 (2019).

(ref: Swinbank2015) Swinbank, A. M. *et al.* . *Astrophys. J. Lett.* **806**, L17 (2015).

(ref: Wu2023) Wu, Y. *et al.* . *Astrophys. J. Lett.* **942**, L1 (2023).

(ref: Simons2017) Simons, R. C. *et al.* . *Astrophys. J.* **843**, 46 (2017).

(ref: Wisnioski2015) Wisnioski, E. *et al.* . *Astrophys. J.* **799**, 209 (2015).

(ref: Kroupa2001) Kroupa, P. . *Mon. Not. R. Astron.* **322**, 231–246 (2001).

(ref: Maiolino2008) Maiolino, R. *et al.* . *Astron. Astrophys.* **488**, 463–479 (2008).

(ref: Salpeter1955) Salpeter, E. E. *Astrophys. J.* **121**, 161 (1955).

(ref: Courteau2014) Courteau, S. *et al.* . *Reviews of Modern Physics* **86**, 47–119 (2014).

(ref: Santini2015) Santini, P. *et al.* . *Astrophys. J.* **801**, 97 (2015).

(ref: Carniani2013) Carniani, S. *et al.* . *Astron. Astrophys.* **559**, A29 (2013).

(ref: Jones2017) Jones, G. C. *et al.* . *Astrophys. J.* **850**, 180 (2017).

(ref: Tadaki2018) Tadaki, K. *et al.* . *Nature* **560**, 613–616 (2018).

(ref: Neeleman2019) Neeleman, M., Kanekar, N., Prochaska, J. X., Rafelski, M. A. & Carilli, C. L. . *Astrophys. J. Lett.* **870**, L19 (2019).

(ref: Rizzo2021) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R. & Powell, D. . *Mon. Not. R. Astron.* **507**, 3952–3984 (2021).

(ref: Rizzo2023) Rizzo, F. *et al.* . *Astron. Astrophys.* **679**, A129 (2023).

(ref: Fraternali2021) Fraternali, F. *et al.* . *Astron. Astrophys.* **647**, A194 (2021).

(ref: Fujimoto2021) Fujimoto, S. *et al.* . *Astrophys. J.* **911**, 99 (2021).

(ref: Lelli2021) Lelli, F. *et al.* . *Science* **371**, 713–716 (2021).

(ref: Tsukui2021) Tsukui, T. & Iguchi, S. . *Science* **372**, 1201–1205 (2021).

(ref: Herrera-Camus2022) Herrera-Camus, R. *et al.* . *Astron. Astrophys.* **665**, L8 (2022).

(ref: Nelson2023) Nelson, E. J. *et al.* . *Astrophys. J. Lett.* **948**, L18 (2023).

(ref: Parlanti2023) Parlanti, E. *et al.* . *Astron. Astrophys.* **673**, A153 (2023).

(ref: Roman-Oliveira2023) Roman-Oliveira, F., Fraternali, F. & Rizzo, F. . *Mon. Not. R. Astron.* **521**, 1045–1065 (2023).

(ref: vanderwel2014) van der Wel, A. *et al.* . *Astrophys. J. Lett.* **792**, L6 (2014).

(ref: Guo2015) Guo, Y. *et al.* . *Astrophys. J.* **800**, 39 (2015).

(ref: Vega-Ferrero2024) Vega-Ferrero, J. *et al.* . *Astrophys. J.* **961**, 51 (2024).

(ref: Ormerod2024) Ormerod, K. *et al.* . *Mon. Not. R. Astron.* **527**, 6110–6125 (2024).

(ref: Barro2019) Barro, G. *et al.* . *Astrophys. J. Suppl. Ser.* **243**, 22 (2019).

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L. & Silverman, J. D. . *Astrophys. J. Suppl. Ser.* **214**, 15 (2014).

(ref: Popesso2023) Popesso, P. *et al.* . *Mon. Not. R. Astron.* **519**, 1526–1544 (2023).

</paper>

Write the methods card for this paper.