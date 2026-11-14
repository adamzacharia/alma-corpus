# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...909...84U\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...909...84U",
 "title": "Internal Structure of Molecular Gas in a Main-sequence Galaxy With a UV Clump at z = 1.45",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Ushio, Kaito",
 "n_authors": 5,
 "arxiv_id": "2101.08396",
 "doi": "10.3847/1538-4357/abdd1f",
 "alma_projects_linked_by_archive": [
  "2011.0.00648.S",
  "2015.1.01129.S"
 ]
}
```

Paper text:
<paper>
# Internal structure of molecular gas in a main sequence galaxy with a UV clump at $z = 1.45$

## Abstract

We present results of sub-arcsec ALMA observations of CO(2-1) and CO(5-4) toward a massive main sequence galaxy at $z = 1.45$ in the SXDS/UDS field, aiming at examining the internal distribution and properties of molecular gas in the galaxy. Our target galaxy consists of the bulge and disk, and has a UV clump in the HST images. The CO emission lines are clearly detected and the CO(5-4)/CO(2-1) flux ratio ($R_{52}$) is $\sim 1$, similar to that of the Milky Way. Assuming a metallicity dependent CO-to-$\rm H_{2}$ conversion factor and a CO(2-1)/CO(1-0) flux ratio of 2 (the Milky Way value), the molecular gas mass and the gas mass fraction ($f_{\rm gas} = {\rm molecular \ gas \ mass} / ({\rm molecular \ gas \ mass} + {\rm stellar \ mass})$) are estimated to be $\sim 1.5 \times 10^{11} M_{\odot}$ and $\sim 0.55$, respectively. We find that $R_{52}$ peak coincides with the position of the UV clump and its value is approximately two times higher than the galactic average. This result implies high gas density and/or high temperature in the UV clump, which qualitatively agrees with a numerical simulation of a clumpy galaxy. The CO(2-1) distribution is well represented by a rotating disk model and its half-light radius is $\sim 2.3 \rm \ kpc$. Compared to the stellar distribution, the molecular gas is more concentrated in the central region of the galaxy. We also find that $f_{\rm gas}$ decreases from $\sim 0.6$ at the galactic center to $\sim 0.2$ at $3 \times$ half-light radius, indicating that the molecular gas is distributed in more central region of the galaxy than stars and seems to associate with the bulge rather than the stellar disk.

# Introduction

![](position_calibrated_HST_images_ratio=25.pdf)

Understanding when and how disk galaxies formed is one of the very important subjects in modern astrophysics. The cosmic star-formation rate (SFR) density increases from the early universe, peaks at $z \sim 1-3$, and decreases by one order of magnitude to the present day (cite: Madau14). Galaxies are thought to evolve drastically at $z \sim 1-3$, and thus observing galaxies at this redshift range is indispensable to understand galaxy formation and evolution.

Recent deep imagings with high angular resolutions by *Hubble Space Telescope* (HST) enable us to resolve the structure of galaxies at $z \sim 1 - 3$ on sub-kiloparsec scale in rest UV to optical bands. Galaxy population resembling the present-day disk galaxies emerges from $z \sim 2 - 3$ (cite: Cameron11; Mortlock13; Talia14) , and at $z \sim 0.8$ fundamental structure of disks seems to be already matured (cite: Lilly98; Takeuchi15). The bulge-like structures are also seen in disk-like galaxies at $z \sim 1 - 2$ in the rest-frame optical band (cite: Cameron11). These observational features suggest the disk galaxies acquire their nature seen in the local universe during the period around at $z \sim 1 - 3$.

About half of star-forming galaxies (SFGs) at this redshift range show clumpy structures in rest UV band (cite: Elmegreen07; Guo15; Shibuya16). These “clumpy" galaxies are thought to evolve into the present-day disk galaxies. Observational studies reveal that the clumps have stellar mass of $\sim 10^{8-10} \, M_{\ensuremath{\odot}}$, SFR of $\sim 1 - 100 \, M_{\ensuremath{\odot}}\,\rm yr^{-1}$, size of $1 - 2 \ \rm kpc$, and age of $\sim 10^{7-9} \, \rm yr$. The clumps close to the center of the host galaxy show larger stellar mass, redder color, and older age than the clumps reside in the outer part (cite: Forster11; Guo12; Guo18). This trend is explained by a theoretical scenario that a gas-rich disk forms through a cold gas accreting from a dark matter halo and/or streaming from the outside of the galaxy and clumps form through gravitational instability in the gas disk. Due to the dynamical friction and/or dynamical interaction, the clumps migrate toward the center of the disk and eventually coalesce into a young bulge (cite: Noguchi99; Bournaud14).

Meanwhile the inside-out growth of galaxies is also one aspect of observational results. For massive SFGs ($M_{\rm star} \gtrsim 10^{11} \, M_{\ensuremath{\odot}}$), no significant increase of stellar mass is seen in the central region of galaxies since $z \sim 2$, and most of new mass growth is seen in the outer region (cite: VanDokkum10; Patel13; Tacchella18). For less massive SFGs, the mass growth is seen at all galactic radii, suggesting a synchronous growth of the bulge and disk at $z \ensuremath{\gtrsim} 1$, while $z \ensuremath{\lesssim} 1$ in the central region the stellar mass growth gradually halts, despite the mass growth continues in the outer region (cite: VanDokkum13; Tacchella18). From analysis of main sequence galaxies with $M_{\rm star} > 10^{10} \, M_{\ensuremath{\odot}}$ at $z \sim 1 - 3$, (cite: Margalef18) show a bulge to disk SFR ratio decreases from $z \sim 3$ to $\sim 1$, which suggests inside-out quenching of star formation.

The properties of molecular gas in SFGs at $z \sim 1 - 3$ have recently been investigated. The cosmic molecular gas density evolves similarly to the cosmic SFR density: it peaks at $z \sim 1-3$ and is higher than local value by approximately one order of magnitude (cite: Maeda17; Decarli19; Riechers19). Observations of molecular gas in main sequence SFGs at this redshift range reveal that gas mass fractions ($f_{\rm gas} = M_{\rm gas}/(M_{\rm gas}+M_{\rm star})$, where $M_{\rm gas}$ refers to a molecular gas mass) are high (cite: Tacconi13; Seko16) as compared with those of local galaxies (typically, $f_{\rm gas} \ensuremath{\lesssim} 0.1$). The average CO excitation of SFGs (sBzK galaxies) at $z \sim 1.5$ is significantly higher than that of the Milky Way (cite: Carilli13; Daddi15), suggesting the physical conditions of the molecular gas are different. In order to understand galaxy evolution further, observations of the distribution of molecular gas in normal SFGs including clumpy galaxies on sub-kiloparsec scale are inevitable. However, resolving distribution of the molecular gas in high-redshift galaxies is still challenging and is limited to some particular cases such as submillimeter galaxies and gravitationally lensed systems (cite: Hodge20). Our knowledge on spatial distribution of molecular gas and its properties in SFGs at $z \sim 1-3$ is still poor.

In this paper, we present results of sub-arcsecond Atacama Large Millimeter/submillimeter Array (ALMA) observations of CO(2-1) and CO(5-4) emission lines toward a massive main sequence galaxy at $z = 1.45$ in the Subaru-XMM/Newton Deep Survey (cite: Furusawa08) field. The CO observations toward this galaxy enable us to study molecular gas properties in a normal star-forming galaxy with a UV clump around at the peak of cosmic SFR density. Combining multitransition CO data and high-resolution HST data of the galaxy, we also study CO(5-4)/CO(2-1) flux ratio in the UV clump. Through model fittings, we compare properties of molecular gas and stellar distributions, and also reveal the radial profile of gas mass fraction.

This paper is structured as follows: in Section [2](#sec:sample), we present the properties of our sample galaxy. The ALMA observations, the data reductions, and the archival HST data are described in Section [3](#sec:obs). The results and discussions are provided in Section [4](#sec:result_and_discussion). We report molecular gas properties and distributions in Section [4.1](#subsec:COresult), and stellar distributions in Section [4.2](#subsec:stellardist). In Section [4.3](#subsubsec:distributions), we compare the molecular gas and stellar distributions. Finally, we put the summary in Section [5](#sec:summary). Throughout this paper, we adopt a flat cosmology with $\Omega_{M} = 0.3, \ \Omega_{\Lambda} = 0.7$ and $H_0 = 70 \ \rm km \, s^{-1} \, Mpc^{-1}$. At the redshift of our sample galaxy ($z = 1.450$), the linear scale is $8.45 \ \rm kpc \, arcsec^{-1}$ The initial mass function (IMF) of (cite: Chabrier03) is adopted. Magnitudes are AB system unless otherwise noted.

![](result_mom0_profile_22.pdf)

# Sample Galaxy

The sample galaxy in this study, SXDS1_13015, is one of the most massive main sequence galaxies at $z \sim 1.4$ in the sample galaxies by (cite: Yabe12) and (cite: Seko16). Using the Fiber Multi-Object Spectrograph (FMOS) on the Subaru telescope, (cite: Yabe12) made near-infrared spectroscopic observations of *Ks*-band selected 317 SFGs at $z \sim 1.4$ in the SXDS/UDS (cite: Lawrence07) field. The stellar masses were derived by spectral energy distribution (SED) fittings with optical to mid-infrared data, adopting the stellar population synthesis model by (cite: Bruzual03) and the IMF by (cite: Salpeter55). The SFRs were derived from extinction-corrected rest UV luminosity densities by using a conversion factor by (cite: Kennicutt98annurev), where the extinction law of (cite: Calzetti00) was assumed and the color excesses were estimated from the rest-frame UV slopes. After correcting the difference of the adopted IMF with the factor of 0.58 (cite: Speagle14), the stellar mass and SFR of SXDS1_13015 are $\sim 1.2 \times 10^{11} \, M_{\ensuremath{\odot}}$ and $\sim 130 \, M_{\ensuremath{\odot}}\,\rm yr^{-1}$, respectively. $\rm H\alpha$ emission lines were detected from 71 galaxies including SXDS1_13015 and the gas metallicities were derived based on N2 method (cite: Pettini04).

Using ALMA, (cite: Seko16) made observations of ${\rm ^{12}CO(5-4)}$ and dust thermal emission toward 20 SFGs selected from the sample galaxies by (cite: Yabe12). 20 SFGs were selected to cover a wide range of stellar mass ($4 \times 10^9 - 4 \times 10^{11} \ M_{\ensuremath{\odot}}$) and metallicity ($12 + {\rm log(O/H)} = 8.2 - 8.9$) uniformly in the diagrams of stellar mass versus SFR and the stellar mass versus metallicity. CO(5-4) lines are detected toward 11 galaxies and dust emissions are clearly detected from 2 galaxies. Both the CO emission and dust thermal emission were detected for SXDS1_13015. Adopting metallicity-dependent CO-to-${\rm H_2}$ conversion factor (cite: Genzel12) and CO(5-4)/CO(1-0) luminosity ratio of 0.23 (cite: Daddi15), the molecular gas mass of SXDS1_13015 was estimated to be $\sim 1 \times 10^{11} \ M_{\ensuremath{\odot}}$. Using a modified blackbody model with dust temperature of $30 \rm \ K$ and dust emissivity index of 1.5, the dust mass of SXDS1_13015 was estimated to be $\sim 5 \times 10^{8} \ M_{\ensuremath{\odot}}$.

Properties of SXDS1_13015 are summarized in Table [1](#table:01). Figure [1](#fig:RGB) (left) shows the composite image of HST WFC3 F160W (hereafter, $H_{160}$), F125W ($J_{125}$) and ACS F606W ($V_{606}$). The galaxy seems to consist of the bulge and disk. In the disk, an arm-like feature is seen in particular northeastern side of the galaxy. Figure [1](#fig:RGB) (right) shows HST $V_{606}$ image corresponding to rest-frame UV ($\sim 2500$ Å). The image clearly shows the presence of a UV clump located at $\sim 0.\ensuremath{''}3$ north of the center, which is also a UV bright region.

|  |  |
|:---|:---|
| R.A. (J2000) | $\rm 02^{h}17^{m}13.62^{s}$ |
| decl. (J2000) | $^\circ$09$'$40.$''$0 |
| $z_{\rm CO}$ | $1.4500 \pm     0.0002$ |
| $M_{\rm star}\,(M_{\ensuremath{\odot}})$ | $1.2^{+0.3}_{-0.2} \times 10^{11}$ |
| SFR ($M_{\ensuremath{\odot}} \, \rm yr^{-1}$) | $128 \pm 32$ |
| $12 + \rm log(O/H)$ | $8.85   \pm     0.04$ |
| $E(B-V) \, (\rm mag)$ |  |

: *Properties of SXDS1_13015*

*Coordinate of the peak pixel of the CO(2-1) 0th moment map.*

*Redshift derived from the CO(2-1) line profile.*

*Derived from the SED fitting with optical to mid-infrared data.*

*Chabrier IMF is adopted. Difference of the adopted IMF is corrected with a factor of 0.58 (cite: Speagle14). The SFR is derived from the extinction-corrected UV luminosity density.*

*Derived with the N2 method. (cite: Pettini04) calibration is adopted.*

*Derived from the rest-frame UV slope.*

# Data Sources

## CO Data

Observations of ${\rm ^{12}CO(2-1)}$ toward SXDS1_13015 were made with ALMA on 2016 August 24 and September 3 during the ALMA Cycle3 (ID: 2015.1.01129.S, PI: K. Ohta). The number of 12 m antennas was 41. The length of the longest and shortest baseline was 1.8 km and 15.1 m, respectively, corresponding to an angular resolution of $\sim 0.\ensuremath{''}55$ and a maximum recoverable scale of $\sim 11\ensuremath{''}$. The observed frequency range was $93.598 - 94.535 \, \rm GHz$ (band 3) to detect ${\rm ^{12}CO(2-1)}$ emission line ($\nu_{\rm rest} = 230.538 \, \rm GHz$, $\nu_{\rm obs} = 94.097 \, \rm GHz$) with bandwidth of 937.5 MHz and spectral resolution of 564.453 kHz, corresponding to a velocity range and resolution of $2988 \ \rm km \, s^{-1}$ and $1.8 \ \rm km \, s^{-1}$, respectively. The total on-source time was 4.7 hours. J0006-0623 and J0238-1636 were used as the flux, bandpass, and amplitude calibrators. The phase calibrators were J0209-0438 and J0215-0222.

The details of CO(5-4) observations are described by (cite: Seko16). The observation was conducted during the ALMA Cycle 0 (ID: 2011.0.00648.S, PI: K. Ohta), and the angular resolution was $\sim$ 0.$''$7. The observed frequency range was $222.094 - 252.583 \, \rm GHz$ (band 6), the spectral resolution was 488.28 kHz ($\sim 0.6 \ \rm km \, s^{-1}$) and the on-source time was $\sim$ 10 minutes.

The raw visibility data of CO(2-1) was calibrated with the Common Astronomy Software Applications (cite: McMullin07) version 4.7.2 and the observatory-provided calibration script. The raw visibility data of CO(5-4) was calibrated with CASA version 4.2 by (cite: Seko16). The imagings of the ALMA data were carried out using CASA version 5.4.0. In order to make cleaned channel maps of CO(2-1) and CO(5-4), we used the CASA tasks `uvcontsub` and `tclean`. Firstly, continuum emission in CO(5-4) data was subtracted with the `uvcontsub`. After that, we made $3\sigma$-clean channel maps of CO(2-1) and CO(5-4) using the `tclean` with weighting of briggs (${\tt robust} = 0.5$) and channel width of $25 \ \rm km \, s^{-1}$. The synthesized beam sizes of CO(2-1) and CO(5-4) channel maps were $0.\ensuremath{''}61 \times 0.\ensuremath{''}52$ ($\sim 4.8 \ \rm kpc$) and $0.\ensuremath{''}84 \times 0.\ensuremath{''}60$ ($\sim 6.0 \ \rm kpc$), respectively. The noise levels of CO(2-1) and CO(5-4) at the velocity width of $25 \ \rm km \, s^{-1}$ were $0.18 \, \rm mJy \, beam^{-1}$ and $0.91 \, \rm mJy \, beam^{-1}$, respectively.

## HST Data

SXDS1_13015 is located in the UKIDSS UDS field, and imaged with HST ACS, WFC3/UVIS and WFC3/IR as a part of Cosmic Assembly Near-infrared Deep Extragalactic Legacy Survey (cite: Grogin11; Koekemoer11) observations. We used the archival ACS $V_{606}$, WFC3 $J_{125}$ and $H_{160}$ data on CANDELS website[^1]. The images are drizzled and the pixel scales are $0.\ensuremath{''}03$ for $V_{606}$, and $0.\ensuremath{''}06$ for $J_{125}$ and $H_{160}$.

# results and discussions

## Molecular Gas Properties

The integrated CO(2-1) and CO(5-4) intensity maps (0th moment maps) and the line profiles of SXDS1_13015 are shown in Figure [2](#fig:GalCO). The symmetric double-peak line profile of CO(2-1) implies the galaxy has a rotating gas disk. The peak position of the CO(5-4) image shows a slight ($\sim 0.\ensuremath{''}15$) offset from that of CO(2-1) image and asymmetry is seen in the CO(5-4) line profile. These features are originated from the presence of the UV clump as described later (Section [4.1.2](#subsubsec:excitationmap)). Thus we adopt the peak in the CO(2-1) map as the center of the galaxy and the central frequency of the observed CO(2-1) emission line ($94.097 \pm 0.008 \ \rm GHz$, corresponding to the redshift of $1.4500 \pm 0.0002$) is taken as the zero velocity.

### Total Flux and Molecular Gas Mass

|  |  |
|:---|:---|
| $S_{\rm CO(2-1)}\Delta v\,(\rm Jy\,km\,s^{-1})$ | $1.03 \pm 0.05$ |
| $S_{\rm CO(5-4)}\Delta v\,(\rm Jy\,km\,s^{-1})$ | $1.16 \pm 0.17$ |
| $R_{52}$ | $1.1  \pm 0.2$ |
| $L'_{\rm CO(1-0)}\,(\rm K\,km\,s^{-1}\,pc^2)$ | $(5.62 \pm 0.27) \times 10^{10}$ |
| $M_{\rm mol}\,(M_{\ensuremath{\odot}})$ | $(1.45 \pm 0.07) \times 10^{11}$ |
| $f_{\rm gas}$ | $0.55 \pm 0.08$ |
| $\tau_{\rm depl} \, (\rm Gyr)$ | $1.1 \pm 0.3$ |

: *Molecular gas properties of SXDS1_13015*

*CO(5-4)/CO(2-1) flux ratio.*

*We adopt CO(2-1)/CO(1-0) flux ratio of 2 (the Milky Way like value).*

*Including a 36% mass contribution of helium. The metallicity dependent CO-to-$H_2$ conversion factor (Equation (7) of (cite: Genzel15)) is adopted.*

*Gas mass fraction ($= M_{\rm mol} / (M_{\rm mol} + M_{\rm star})$).*

*Gas depletion time ($= M_{\rm mol} / SFR$)*

![](CO_excitation_map_2sigmamask.pdf)

The total CO(2-1) and CO(5-4) flux of SXDS1_13015 are derived by fitting an elliptical Gaussian model to the respective integrated intensity maps. We use the data in a 1.$''$5 diameter circle centered on the peak of the CO(2-1) integrated intensity map. The total CO(2-1) and CO(5-4) flux of SXDS1_13015 are estimated to be $(1.03 \pm 0.05) \ \rm Jy \, km \, s^{-1}$ and $(1.16 \pm 0.17) \ \rm Jy \, km \, s^{-1}$, respectively. The beam-deconvolved FWHM of the CO(2-1) source is $4.0 \pm 0.5 \ \rm kpc$.

The CO(5-4) flux value is different from that derived by (cite: Seko16) because of the differences of the adopted velocity width and the data reduction.

The CO(5-4)/CO(2-1) flux ratio ($R_{52} = \\ S_{\rm CO(5-4)}\Delta v / S_{\rm CO(2-1)}\Delta v$) is $1.1 \pm 0.2$, which suggests that the CO excitation ladder of SXDS1_13015 is similar to that of the Milky Way rather than color-selected SFGs at $z \sim 1 - 3$ (cite: Carilli13).[^2] Such low CO excitations are also reported in some SFGs at $z \sim 1-2.5$ (cite: Decarli16).

We calculate the total CO(1-0) luminosity ($L'_{\rm CO(1-0)}$) as $$\begin{equation}
\begin{split}
  L'_{\rm CO(1-0)} &= 3.25 \times 10^7\nu_{\rm rest:CO(1-0)}^{-2}D_L^2(1+z)^{-1} \\
  & \quad \times R_{21}^{-1}S_{\rm CO(2-1)}\Delta v ,
\label{eq:COluminosity}
\end{split}
\end{equation}$$ where $L'_{\rm CO(1-0)}$ is measured in ${\rm K\, km\,s^{-1} \, pc^2}$, $\nu_{\rm rest:CO(1-0)}$ is the rest frequency of the CO(1-0) emission line of 115.271 GHz, $D_L$ is the luminosity distance in Mpc, $R_{21}$ is the CO(2-1)/CO(1-0) flux ratio, and $S_{\rm CO(2-1)}\Delta v$ is the observed CO(2-1) flux in $\rm Jy\ km\,s^{-1}$. Because the CO excitation ladder of the galaxy is similar to that of the Milky Way, we assume $R_{21} = 2$. The calculated total CO(1-0) luminosity of SXDS1_13015 is $(5.62 \pm 0.27) \times 10^{10} \ {\rm K\, km\,s^{-1} \, pc^2}$.

The molecular gas mass is derived from $$\begin{equation}
M_{\rm mol} = \alpha_{\rm CO}L'_{\rm CO(1-0)} ,
\label{eq:gasmass}
\end{equation}$$ where $\alpha_{\rm CO}$ is the CO-to-$\rm H_{2}$ conversion factor in $M_{\ensuremath{\odot}} \rm (K\, km\,s^{-1}\, pc^2)^{-1}$. $\alpha_{\rm CO}$ in SFGs at $z \sim 1-2$ is expected to depend on gas metallicity; the value of $\alpha_{\rm CO}$ is larger in galaxies with lower metallicity (cite: Wolfire10; Bolatto13). As the dependence of $\alpha_{\rm CO}$ on metallicity,

we adopt the Equation (7) of (cite: Genzel15): $$\begin{equation}

\alpha_{\rm CO} = 4.36 \times 10^{-1.27 \times (12 + {\rm log(O/H)} - 8.67)}, 
\label{eq:conversionfactor}
\end{equation}$$ where $\alpha_{\rm CO}$ includes a 36% mass contribution of helium and $(12 + {\rm log(O/H)})$ is the metallicity based on (cite: Pettini04) calibration. The $\alpha_{\rm CO}$ of SXDS1_13015 is calculated to be $2.58\ M_{\ensuremath{\odot}} \rm (K\, km\,s^{-1}\, pc^2)^{-1}$. The resulting total molecular gas mass is $(1.45 \pm 0.07) \times 10^{11} \ M_{\ensuremath{\odot}}$ and the gas mass fraction is $f_{\rm gas} = 0.55 \pm 0.08$. The gas depletion time ($\tau_{\rm depl} = M_{\rm mol}/{\rm SFR}$) of the galaxy is estimated to be $= 1.1 \pm 0.3 \ \rm Gyr$. The derived molecular gas properties of SXDS1_13015 are listed in Table [2](#table:molecule).

### Spatial Distribution of $R_{52}$

![](result_velmap.pdf)

![](excitation_map_negvel.pdf)

![](result_galpak_mom0_line.pdf)

We made the $R_{52}$ map by dividing the CO(5-4) 0th moment map by the CO(2-1) map convolved to the same beam size as CO(5-4) data. The $R_{52}$ is calculated in pixels with ${\rm S/N} > 2.5$ in the CO(5-4) map. The resulting CO flux ratio map is shown in Figure [3](#fig:COexcitationMap). The peak of the CO(5-4)/CO(2-1) flux ratio ($R_{52} \sim 2.2$) is significantly larger than the $R_{52}$ averaged over SXDS1_13015 and that of the Milky Way. The ratio is comparable to the average $R_{52}$ for sBzK galaxies at $z \sim 1.5$ (cite: Daddi15). The peak of the flux ratio is located at $\sim 0.\ensuremath{''}3$ north of the peak of the CO(2-1) distribution (cross mark in Figure [3](#fig:COexcitationMap)).

Interestingly, the location coincides with the UV clump. The velocity at this position is $\sim -150 \ \rm km \, s^{-1}$ in the CO(2-1) velocity field (Figure [4](#fig:Galvel)), and this velocity corresponds to the peak velocity in the CO(5-4) profile (Figure [2](#fig:GalCO), bottom right); the asymmetric feature of the CO(5-4) profile is presumably due to this component. We show the 0th moment maps integrated over the velocity range of $-250 \ \rm km \, s^{-1}$ to $0 \ \rm km \, s^{-1}$ in Figure [5](#fig:negvel_mom0). The $R_{52}$ map in this velocity range also peaks at the position of the UV clump. In the UV clump, it is expected that the density and/or temperature of the molecular gas are higher than those in other regions. This result, the high $R_{52}$ in the UV clump, is qualitatively consistent with the CO excitation ladder modeled by a large velocity gradient analysis of the hydrodynamically simulated high-$z$ clumpy galaxy (cite: Bournaud15).

It is worth noting that the spatial offset and the asymmetric profile of CO(5-4) are not results of noise. We performed simulations of CO(5-4) observation with CASA task `simobserve` assuming a gaussian distribution mimicking the CO(5-4) distribution and line profile. Consequently, we found that the 1-$\sigma$ uncertainty of the peak position of CO(5-4) is $\sim 0.04 \ \rm arcsec$. he observed offset between the peak positions of CO(5-4) and CO(2-1) is $\sim 0.15 \ \rm arcsec$ which corresponds to $\sim 3.8 \sigma$. We also found that the 1-$\sigma$ uncertainty of the peak velocity is $\sim 30 \ \rm km \, s^{-1}$. The observed peak CO(5-4) velocity and the central CO(2-1) velocity is $\sim 150 \ \rm km \, s^{-1}$ which corresponds to $\sim 5 \sigma$. Thus the offset and the peak velocity difference are considered to be real. It should be also noted here, we made astrometric corrections to the HST images with the offset shown below. We assume the peak of $J_{125}$ image coincides with the peak of the CO(2-1) 0th moment map, because the CO(2-1) shows a good symmetry in the line profile and S/N of the image is high. The offset is $(\Delta{\rm R.A.}, \Delta{\rm Dec.}) = (+0.\ensuremath{''}058, -0.\ensuremath{''}198)$. Similar amounts of the offset between ALMA astrometry and HST astrometry are also reported in Hubble Ultra-Deep Field and CANDELS GOODS-S region (cite: Barro16; Rujopakarn16; Dunlop17).

(cite: Cibinel17) presented ALMA observations of CO(5-4) line towards a main sequence, clumpy galaxy at $z \sim 1.5$, but no CO(5-4) emission from the UV clumps was detected. This is presumably due to the low SFR of the UV clumps ($\sim 1 - 4 \ M_{\odot} \rm \, yr^{-1}$). The sensitivity of their observation was not deep enough to detect the CO(5-4) emissions from the UV clumps. The SFR of the UV clump in our sample galaxy is estimated to be $\sim 30 \  M_{\odot} \rm \, yr^{-1}$ from UV luminosity, and is larger than those of clumps in (cite: Cibinel17). By assuming a depletion time of $0.5 \ \rm Gyr$ and the sBzK-like CO $J$-ladder, the contribution of the UV clump to the total CO(5-4) flux is expected to be $\sim 20-25 \%$ in our case.

|                                 |                 |
|:--------------------------------|:----------------|
| flux $\rm (Jy \, km \, s^{-1})$ | $1.10 \pm 0.05$ |
| $r_{1/2}$ (kpc)                 | $2.30 \pm 0.12$ |
| inclination (deg)               | $47.6 \pm 6.5$  |
| PA (deg)                        | $42.8 \pm 2.0$  |
| $r_{t}$ (kpc)                   | $0.48 \pm 0.22$ |
| $V_{\rm max}\ \rm(km\,s^{-1})$  | $350  \pm 30$   |

: *Best-fit parameters derived by ${\rm GalPaK^{3D}}$*

*Uncertainties are estimated based on simulations (see text).*

*Half-light radius.*

*Turnover radius.*

*Inclination-corrected maximum rotational velocity.*

| filter                       | $J_{125}$              | $H_{160}$              |
|:-----------------------------|:-----------------------|:-----------------------|
| $n$                          | $2.04 \pm 0.19$        | $1.76 \pm 0.11$        |
| $R_{1/2}$ (kpc)              | $3.54 \pm 0.15$        | $3.22 \pm 0.07$        |
| $b/a$                        | $0.62 \pm 0.01$        | $0.60 \pm 0.01$        |
| PA (deg)                     | $32.0 \pm 0.9$         | $36.2 \pm 0.7$         |
| $R_{1/2; \rm bulge}$ (kpc)   | $0.45\pm0.23$          | $0.44\pm0.22$          |
| $R_{1/2; \rm disk}$ (kpc)    | $5.05\pm0.33$          | $4.49\pm0.21$          |
| $L_{\rm bulge}/L_{\rm disk}$ | $0.38^{+0.11}_{-0.08}$ | $0.36^{+0.11}_{-0.08}$ |

*Uncertainties are estimated by changing sky level within its error, stars to construct the PSFs and the size of the fitting region.*

*Results of single component fitting. Sérsic index, half-light radius, axis ratio, and position angle, respectively.*

*Results of two components (bulge ($n=4$) and disk ($n=1$)) fitting.*

![](radial_profiles_fit_subsky.pdf)

### Fitting a Rotating Disk Model

The velocity field of CO(2-1) (Figure [4](#fig:Galvel)) shows a clear velocity gradient along the major axis, indicating that the galaxy has a rotating gas disk, which is also implied by the double-peak CO(2-1) line profile. In order to eliminate the effect of beam smearing and derive the intrinsic molecular gas distribution and kinematic properties of the galaxy, we fit a rotating disk model by using ${\rm GalPaK^{3D}}$ (cite: Bouche15). ${\rm GalPaK^{3D}}$ is a program code that estimates morphological parameters (e.g., size and inclination) and kinematic parameters (e.g., maximum rotational velocity and velocity dispersion) of the galaxy by fitting a disk model convolved with two-dimensional PSF and one-dimensional line spread function (LSF) to a given data cube. We fit a disk model whose radial flux profile is exponential (Sérsic index $n=1$) and radial rotational velocity profile is hyperbolic tangent to the CO(2-1) channel map. PSF and LSF correspond to the synthesized beam ($0.\ensuremath{''}61 \times 0.\ensuremath{''}53$, ${\rm PA} = 79\ensuremath{^\circ}$) and the channel bin (velocity width is $25 \ \rm km \, s^{-1}$), respectively. The fitting parameters are central position, central frequency, total flux, half-light radius ($r_{1/2}$), inclination, position angle, turnover radius ($r_{t}$), maximum rotational velocity ($V_{\rm max}$), and velocity dispersion ($\sigma_0$) which is assumed to be constant over the disk. The best-fit models as well as input image are shown in Figure [6](#fig:Galpak) (upper panels). The residual ($\rm observed - model$) integrated intensity map and line profile are also shown in Figure [6](#fig:Galpak) (bottom panels). The residuals demonstrate that the CO(2-1) distribution of the galaxy is well represented by the rotating disk model. The best-fit parameters are listed in Table [3](#table:02). In order to estimate the uncertainties on the best-fit parameters, we created 100 cleaned cubes by simulating observations of the best-fit disk model with `simobserve` by changing the noise seeds randomly. Disk models are fitted to the simulated cubes by ${\rm GalPaK^{3D}}$, and the means and the standard deviations of the disk model parameters are derived. We adopt the square root of the sum of the square of systematic error and standard deviation as the uncertainty for each best-fit parameter derived by ${\rm GalPaK^{3D}}$. The best-fit flux ($1.10 \pm 0.05 \ \rm Jy \, km \, s^{-1}$) is consistent with that derived from the two-dimensional Gaussian fitting to the integrated intensity map. The best-fit $r_{1/2} = 2.30 \pm 0.12 \ \rm kpc$ is also consistent with the HWHM of the 2D Gaussian fitting ($\sim 2 \ \rm kpc$)[^3]. The best-fit $V_{\rm max}$ and $\sigma_0$ are $350 \pm 30 \ \rm km \, s^{-1}$ and $2.7 \pm 8.7 \ \rm km \, s^{-1}$, respectively. The best-fit value for $\sigma_0$ is very much small and has a very large uncertainty ($\sigma_0$ is derived to be $\sim 40 \ \rm km \, s^{-1}$ from some simulated cubes). The value is considered not to be reliable. In fact, the observed line profile is well reproduced without changing other output parameters such as $r_{1/2}$, even if we fit a disk model with a fixed $\sigma_{0} \sim 50 \ \rm km \, s^{-1}$ (cite: Wisnioski15; Forster18). Due to the large beam size, the observed line width seems to be largely affected by beam smearing effect, and it is hard to constrain the intrinsic velocity dispersion well.

## Stellar Distribution

In order to derive properties of the stellar distribution, we fit Sérsic profile models to HST WFC3/IR $J_{125}$ and $H_{160}$ band images using GALFIT (cite: Peng02). GALFIT is a program code that fits given surface brightness model convolved with PSF to an observed galaxy. Four(Six) bright but unsaturated stars in the $J_{125}$($H_{160}$) image of the CANDELS-UDS field are stacked to construct the PSFs for the fittings. The $\sim 2.\ensuremath{''}5 \times 2.\ensuremath{''}5$ boxy region centered at the image peak is used for the fitting. The pixels contaminated by neighboring objects are masked out. After sky subtractions, we firstly fit the surface brightness with single component Sérsic profile. The fitting parameters are central position, total magnitude, half-light radius ($R_{1/2}$), Sérsic index ($n$), axial ratio, and position angle. We also fit another surface brightness model with two-component Sérsic profiles. In this fitting, Sérsic indices are fixed to be $n=4$ for bulge and $1$ for disk, because the galaxy has a rotating gas disk and seems to consist of the bulge and disk in the HST composite image (see Figure [1](#fig:RGB)). The fitting parameters are total magnitude of each component, half-light radius of each component ($R_{1/2; \rm bulge}, R_{1/2; \rm disk}$) and axial ratio of the bulge. Central position of each component, position angle of each component, and axial ratio of the disk are fixed to the values derived from the single component fitting. The derived best-fit parameters are listed in Table [\[table:03\]](#table:03). The observed and fitted radial profiles are shown in Figure [7](#fig:radialprofile).

![](intrinsic_radial_profiles_me.pdf)

![](radial_profiles_fit_subsky_deconv_wfgas.pdf)

Assuming a constant mass-to-luminosity ratio, we derived the stellar mass surface density profile of SXDS1_13015 from $J_{125}$ distribution modeled with the single component model. In Figure [8](#fig:comparePatel), the derived profile of SXDS1_13015 is plotted with the median profiles of galaxies at different redshifts by (cite: Patel13). The sample galaxies of (cite: Patel13) are selected at a constant cumulative number density of $1.4 \times 10^{-4} \ \rm Mpc^{-3}$ for different redshifts (corresponding to the stellar mass of $\sim 1.1 \times 10^{11} \ M_{\ensuremath{\odot}}$ for $1.0 < z < 1.5$). The number of sample galaxies at $1.0 < z < 1.5$ is 20 including $\sim 65\%$ of quiescent galaxies. The surface density profiles are derived by assuming a constant mass-to-luminosity ratio, and are modeled by fitting single component Sérsic profile to the rest optical image for each redshift using GALFIT. The standard deviations for the median profiles at $z \sim 1.0-1.5$ and $z \sim 1.5-2.0$ are calculated by generating 1000 median profiles based on the uncertainties of the median half-light radius and Sérsic index at each redshift provided by (cite: Patel13). SXDS1_13015 shows slightly higher surface density than the median of the galaxies at similar redshift, and reaches to the surface density comparable to that of galaxies at $z \sim 0.06$. The surface density of SXDS1_13015 is also comparable to that of local galaxies with the stellar mass of the Milky Way (cite: VanDokkum13). At $r \ensuremath{\lesssim} 1 \ \rm kpc$, the surface density of SXDS1_13015 is lower than those of the median profiles. However, the scale of $1 \ \rm kpc$ is comparable to the HWHM of the PSF for our fitting ($\sim 0.8 \ \rm kpc \sim 1.5 \ \rm pixels$), and it is possible that the profile is not sufficiently recovered within this scale.

## Molecular Gas and Stellar Distribution in SXDS1_13015

### Modeled Gas and Stellar Distributions

By using the modeled molecular gas distribution derived by $\rm GalPaK^{3D}$ and the stellar distribution derived by GALFIT, we obtain intrinsic radial surface distributions of the molecular gas as well as the stellar component in SXDS1_13015 (Figure [9](#fig:intrinsicprofile)). The uncertainty on the molecular gas surface distribution is estimated with radial profiles derived from $\rm GalPaK^{3D}$ fitting to the 100 simulated cubes (see Section [4.1.3](#subsubsec:rotation)). The uncertainty on the stellar surface distribution is derived from uncertainties on the total stellar mass and galaxy parameters of GALFIT. We also derive gas mass fraction ($f_{\rm gas}$) at each radius. The uncertainty on $f_{\rm gas}$ is derived from the uncertainties on the molecular gas and stellar radial surface distributions. $f_{\rm gas}$ is higher than galactic total value ($\sim 0.55$) at $r \lesssim 3 \ \rm kpc$, and decreases with increasing galactocentric radius from $\sim 0.6$ at the central region to $\sim 0.2$ at $\sim 3 \times r_{1/2}$. The molecular gas is distributed in more inner region of the galaxy than stars and seems to associate with the bulge rather than the stellar disk, which is also indicated by the best-fit half-light radii.

By using the best-fit kinematic parameters of the molecular gas disk, dynamical masses ($M_{\rm dyn}(r) \sim rv_{\rm rot}^{2}/G$) at $r = r_{1/2}, \ 2r_{1/2}, \ 3r_{1/2}$ ($r_{1/2}$ is half-light radius of molecular gas disk) are estimated to be $\sim (0.7,\ 1.3,\ 2.0) \times 10^{11} \ M_{\ensuremath{\odot}}$. We also derive the molecular gas and stellar masses within these radii assuming the inner mass ($m(<r)$) is proportional to the luminosity within the radius ($L(<r)$) in $J_{125}$ image: $$\begin{equation}
m(<r) = \frac{L(<r)}{L_{\rm total}} M_{\rm total} \ .
\label{eq:innermass}
\end{equation}$$ The molecular gas and stellar masses within $r = r_{1/2}, \ 2r_{1/2}, \ 3r_{1/2}$ are $m_{\rm mol} \sim (0.7,\ 1.2,\ 1.4) \times 10^{11} \ M_{\ensuremath{\odot}}$ and $m_{\rm star} \sim (0.4,\ 0.7,\ 0.9) \times 10^{11} \ M_{\ensuremath{\odot}}$, respectively. Baryon fractions ($f_{\rm baryon} = (m_{\rm mol} + m_{\rm star})/(M_{\rm dyn} + m_{\rm mol} + m_{\rm star})$) within those radii are estimated to be $\sim 0.61,\ 0.59,\ 0.53$; within $r = 3r_{1/2} \sim 7 \ \rm kpc$.

### CO and Optical Half-light Radii

![](half_light_radius_comparizon.pdf)

Figure [10](#fig:radius_comparison) (left) shows the location of SXDS1_13015 in optical versus CO half-light radius plane compared to other field and cluster galaxies at $z \sim 1 - 1.6$. The field sample includes 12 main sequence galaxies at $z \sim 1 - 1.5$ by (cite: Tacconi13) and 3 sBzK galaxies by (cite: Daddi10). All galaxies of the field sample show both disk-like morphologies in HST images and clear CO velocity gradients (classified “Disk(A)" by (cite: Tacconi13)). The CO and optical half-light radii were estimated by fitting $n = 1$ Sérsic profile to image planes or circular Gaussians to *uv* planes, and by fitting single Sérsic profile to HST-WFC3 $I_{814}$ band data using GALFIT, respectively. The typical uncertainties of both CO and optical half-light radius is $\sim 25\%$. The cluster sample consists of 4 cluster galaxies at $z \sim 1.6$ by (cite: Noble19) (J0225-371, J0225-460, J0225-281 and J0225-541); they are detected with high S/Ns and show clear velocity gradients in CO(2-1). The CO and optical half-light radii were estimated by fitting elliptical Gaussians to the CO(2-1) images and single Sérsic profile to $H_{160}$ band data using GALFIT, respectively. The typical uncertainty of CO half-light radius is $\sim 10\%$. As shown in Figure [10](#fig:radius_comparison) (right), the field and cluster sample galaxies are mostly main sequence galaxies at similar redshift and with similar stellar mass to SXDS1_13015.

Studies in rest *V* band of galaxies at similar redshift to SXDS1_13015 show that SFGs with similar stellar mass show half-light radius of a few to a few tens kpc and Sérsic index of $n \sim 1.5 - 4$ (cite: Wuyts11; vanderWel14; Shibuya15; Mowla19). The $n$ and half-light radius of SXDS1_13015 derived from the single component fitting are within the range of those obtained in other main sequence galaxies. The CO and optical half-light radii of SXDS1_13015 are, however, relatively small as compared with other main sequence galaxies, but the CO-to-optical half-light radius ratio of SXDS1_13015 ($R_{1/2,\rm CO}/R_{1/2,\rm F125W} = 0.65 \pm 0.04$, $R_{1/2,\rm CO}/R_{1/2,\rm F160W} = 0.71 \pm 0.04$) is typical among these samples.

# Summary

We presented the results of sub-arcsecond ALMA ${\rm ^{12}}$CO(2-1) and ${\rm ^{12}}$CO(5-4) observations toward a massive main sequence galaxy at $z = 1.45$ (SXDS1_13015). These observations enabled us to study molecular gas properties, its distribution in the galaxy, and CO(5-4)/CO(2-1) flux ratio in a UV clump detected in the rest-frame UV HST image. By fitting a rotating gas disk model to the CO(2-1) data, we derived molecular gas distribution and kinematics. Combining with the HST images, we compared the properties of molecular gas and stellar distributions. The results are as follows:

i\) CO(2-1) and CO(5-4) emission lines are clearly detected from the galaxy (Figure [2](#fig:GalCO)) and the symmetric and double-peak line profile of CO(2-1) implies the presence of the molecular gas disk in the galaxy. $R_{52}$ of the galaxy is $1.1 \pm 0.2$, which suggests the CO excitation ladder of the galaxy is similar to that of the Milky Way rather than sBzK galaxies at $z \sim 1.5$. The molecular gas mass of the galaxy is $1.45 \times 10^{11} \ M_{\odot}$, adopting $R_{21} = 1$ (the Milky Way value) and metallicity dependent CO-to-$\rm H_2$ conversion factor. The gas mass fraction and depletion time are $0.55 \pm 0.08$ and $1.1 \pm 0.3 \ \rm Gyr$, respectively.

ii\) In the $R_{52}$ map (Figure [3](#fig:COexcitationMap)), the peak value of $R_{52}$ is $\sim 2.2$, comparable to that of the average of sBzK galaxies at $z \sim 1.5$. $R_{52}$ peaks at the position of the UV clump. These results are similar to a result of a hydrodynamic simulation of a clumpy galaxy (cite: Bournaud15). In the UV clump, the gas density and/or temperature are/is higher than those in the other galactic regions.

iii\) By using $\rm GalPaK^{3D}$, the molecular gas distribution of the galaxy traced by CO(2-1) is well represented by the rotating disk model (Figure [6](#fig:Galpak)). The half-light radius of the modeled gas disk is $2.3 \ \rm kpc$.

iv\) By comparing the molecular gas distribution and stellar distribution derived by fitting Sérsic models to the rest optical HST images, the molecular gas is more concentrated in the galactic center (Figure [9](#fig:intrinsicprofile)). The gas mass fraction decreases with increasing galactocentric radius from $\sim 0.6$ at the central region to $\sim 0.2$ at $\sim 3 \times r_{1/2}$, suggesting that the galaxy is forming its bulge.

# Acknowledgments

We thank the anonymous referee for useful comments and suggestions, which improve the paper. We are grateful to K. Nakanishi, F. Egusa, K. Saigo, and the staff at the ALMA Regional Center for their help in data reduction. We also thank K. Tadaki for his critical comment on our earlier study with this galaxy. F.M. is supported by Research Fellowship for Young Scientists from the Japan Society of the Promotion of Science (JSPS). K.O. is supported by JSPS KAKENHI Grant Number JP19K03928. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01129.S. and #2011.0.00648.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Software

GALFIT (cite: Peng02), GalPaK3D (cite: Bouche15), CASA (cite: McMullin07)

natexlab

(ref: Barro16) Barro, G., Kriek, M., Pérez-González, P. G., et al. 2016, ApJL, 827, L32, doi: [`10.3847/2041-8205/827/2/L32`](http://doi.org/10.3847/2041-8205/827/2/L32)

(ref: Bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Boogaard20) Boogaard, L. A., van der Werf, P., Weiß, A., et al. 2020, arXiv e-prints, arXiv:2009.04348. [`https://arxiv.org/abs/2009.04348`](https://arxiv.org/abs/2009.04348)

(ref: Bouche15) Bouché, N., Carfantan, H., Schroetter, I., Michel-Dansac, L., & Contini, T. 2015, AJ, 150, 92, doi: [`10.1088/0004-6256/150/3/92`](http://doi.org/10.1088/0004-6256/150/3/92)

(ref: Bournaud15) Bournaud, F., Daddi, E., Weiß, A., et al. 2015, A&A, 575, A56, doi: [`10.1051/0004-6361/201425078`](http://doi.org/10.1051/0004-6361/201425078)

(ref: Bournaud14) Bournaud, F., Perret, V., Renaud, F., et al. 2014, ApJ, 780, 57, doi: [`10.1088/0004-637X/780/1/57`](http://doi.org/10.1088/0004-637X/780/1/57)

(ref: Bruzual03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: Calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Cameron11) Cameron, E., Carollo, C. M., Oesch, P. A., et al. 2011, ApJ, 743, 146, doi: [`10.1088/0004-637X/743/2/146`](http://doi.org/10.1088/0004-637X/743/2/146)

(ref: Carilli13) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Cibinel17) Cibinel, A., Daddi, E., Bournaud, F., et al. 2017, MNRAS, 469, 4683, doi: [`10.1093/mnras/stx1112`](http://doi.org/10.1093/mnras/stx1112)

(ref: Daddi10) Daddi, E., Bournaud, F., Walter, F., et al. 2010, ApJ, 713, 686, doi: [`10.1088/0004-637X/713/1/686`](http://doi.org/10.1088/0004-637X/713/1/686)

(ref: Daddi15) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46, doi: [`10.1051/0004-6361/201425043`](http://doi.org/10.1051/0004-6361/201425043)

(ref: Decarli16) Decarli, R., Walter, F., Aravena, M., et al. 2016, ApJ, 833, 70, doi: [`10.3847/1538-4357/833/1/70`](http://doi.org/10.3847/1538-4357/833/1/70)

(ref: Decarli19) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138, doi: [`10.3847/1538-4357/ab30fe`](http://doi.org/10.3847/1538-4357/ab30fe)

(ref: Dunlop17) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861, doi: [`10.1093/mnras/stw3088`](http://doi.org/10.1093/mnras/stw3088)

(ref: Elmegreen07) Elmegreen, D. M., Elmegreen, B. G., Ravindranath, S., & Coe, D. A. 2007, ApJ, 658, 763, doi: [`10.1086/511667`](http://doi.org/10.1086/511667)

(ref: Forster11) Förster Schreiber, N. M., Shapley, A. E., Genzel, R., et al. 2011, ApJ, 739, 45, doi: [`10.1088/0004-637X/739/1/45`](http://doi.org/10.1088/0004-637X/739/1/45)

(ref: Forster18) Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, ApJS, 238, 21, doi: [`10.3847/1538-4365/aadd49`](http://doi.org/10.3847/1538-4365/aadd49)

(ref: Furusawa08) Furusawa, H., Kosugi, G., Akiyama, M., et al. 2008, ApJS, 176, 1, doi: [`10.1086/527321`](http://doi.org/10.1086/527321)

(ref: Genzel12) Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69, doi: [`10.1088/0004-637X/746/1/69`](http://doi.org/10.1088/0004-637X/746/1/69)

(ref: Genzel15) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20, doi: [`10.1088/0004-637X/800/1/20`](http://doi.org/10.1088/0004-637X/800/1/20)

(ref: Grogin11) Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, ApJS, 197, 35, doi: [`10.1088/0067-0049/197/2/35`](http://doi.org/10.1088/0067-0049/197/2/35)

(ref: Guo12) Guo, Y., Giavalisco, M., Ferguson, H. C., Cassata, P., & Koekemoer, A. M. 2012, ApJ, 757, 120, doi: [`10.1088/0004-637X/757/2/120`](http://doi.org/10.1088/0004-637X/757/2/120)

(ref: Guo15) Guo, Y., Ferguson, H. C., Bell, E. F., et al. 2015, ApJ, 800, 39, doi: [`10.1088/0004-637X/800/1/39`](http://doi.org/10.1088/0004-637X/800/1/39)

(ref: Guo18) Guo, Y., Rafelski, M., Bell, E. F., et al. 2018, ApJ, 853, 108, doi: [`10.3847/1538-4357/aaa018`](http://doi.org/10.3847/1538-4357/aaa018)

(ref: Hodge20) Hodge, J. A., & da Cunha, E. 2020, arXiv e-prints, arXiv:2004.00934. [`https://arxiv.org/abs/2004.00934`](https://arxiv.org/abs/2004.00934)

(ref: Kennicutt98annurev) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189, doi: [`10.1146/annurev.astro.36.1.189`](http://doi.org/10.1146/annurev.astro.36.1.189)

(ref: Koekemoer11) Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS, 197, 36, doi: [`10.1088/0067-0049/197/2/36`](http://doi.org/10.1088/0067-0049/197/2/36)

(ref: Lawrence07) Lawrence, A., Warren, S. J., Almaini, O., et al. 2007, MNRAS, 379, 1599, doi: [`10.1111/j.1365-2966.2007.12040.x`](http://doi.org/10.1111/j.1365-2966.2007.12040.x)

(ref: Lilly98) Lilly, S., Schade, D., Ellis, R., et al. 1998, ApJ, 500, 75, doi: [`10.1086/305713`](http://doi.org/10.1086/305713)

(ref: Madau14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Maeda17) Maeda, F., Ohta, K., & Seko, A. 2017, ApJ, 835, 120, doi: [`10.3847/1538-4357/835/2/120`](http://doi.org/10.3847/1538-4357/835/2/120)

(ref: Margalef18) Margalef-Bentabol, B., Conselice, C. J., Mortlock, A., et al. 2018, MNRAS, 473, 5370, doi: [`10.1093/mnras/stx2633`](http://doi.org/10.1093/mnras/stx2633)

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mortlock13) Mortlock, A., Conselice, C. J., Hartley, W. G., et al. 2013, MNRAS, 433, 1185, doi: [`10.1093/mnras/stt793`](http://doi.org/10.1093/mnras/stt793)

(ref: Mowla19) Mowla, L. A., van Dokkum, P., Brammer, G. B., et al. 2019, ApJ, 880, 57, doi: [`10.3847/1538-4357/ab290a`](http://doi.org/10.3847/1538-4357/ab290a)

(ref: Noble19) Noble, A. G., Muzzin, A., McDonald, M., et al. 2019, ApJ, 870, 56, doi: [`10.3847/1538-4357/aaf1c6`](http://doi.org/10.3847/1538-4357/aaf1c6)

(ref: Noguchi99) Noguchi, M. 1999, ApJ, 514, 77, doi: [`10.1086/306932`](http://doi.org/10.1086/306932)

(ref: Patel13) Patel, S. G., van Dokkum, P. G., Franx, M., et al. 2013, ApJ, 766, 15, doi: [`10.1088/0004-637X/766/1/15`](http://doi.org/10.1088/0004-637X/766/1/15)

(ref: Peng02) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266, doi: [`10.1086/340952`](http://doi.org/10.1086/340952)

(ref: Pettini04) Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59, doi: [`10.1111/j.1365-2966.2004.07591.x`](http://doi.org/10.1111/j.1365-2966.2004.07591.x)

(ref: Riechers19) Riechers, D. A., Pavesi, R., Sharon, C. E., et al. 2019, ApJ, 872, 7, doi: [`10.3847/1538-4357/aafc27`](http://doi.org/10.3847/1538-4357/aafc27)

(ref: Rujopakarn16) Rujopakarn, W., Dunlop, J. S., Rieke, G. H., et al. 2016, ApJ, 833, 12, doi: [`10.3847/0004-637X/833/1/12`](http://doi.org/10.3847/0004-637X/833/1/12)

(ref: Salpeter55) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Seko16) Seko, A., Ohta, K., Yabe, K., et al. 2016, ApJ, 819, 82, doi: [`10.3847/0004-637X/819/1/82`](http://doi.org/10.3847/0004-637X/819/1/82)

(ref: Shibuya15) Shibuya, T., Ouchi, M., & Harikane, Y. 2015, ApJS, 219, 15, doi: [`10.1088/0067-0049/219/2/15`](http://doi.org/10.1088/0067-0049/219/2/15)

(ref: Shibuya16) Shibuya, T., Ouchi, M., Kubo, M., & Harikane, Y. 2016, ApJ, 821, 72, doi: [`10.3847/0004-637X/821/2/72`](http://doi.org/10.3847/0004-637X/821/2/72)

(ref: Speagle14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: Tacchella18) Tacchella, S., Carollo, C. M., Förster Schreiber, N. M., et al. 2018, ApJ, 859, 56, doi: [`10.3847/1538-4357/aabf8b`](http://doi.org/10.3847/1538-4357/aabf8b)

(ref: Tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: Takeuchi15) Takeuchi, T. M., Ohta, K., Yuma, S., & Yabe, K. 2015, ApJ, 801, 2, doi: [`10.1088/0004-637X/801/1/2`](http://doi.org/10.1088/0004-637X/801/1/2)

(ref: Talia14) Talia, M., Cimatti, A., Mignoli, M., et al. 2014, A&A, 562, A113, doi: [`10.1051/0004-6361/201322193`](http://doi.org/10.1051/0004-6361/201322193)

(ref: Valentino20) Valentino, F., Daddi, E., Puglisi, A., et al. 2020, A&A, 641, A155, doi: [`10.1051/0004-6361/202038322`](http://doi.org/10.1051/0004-6361/202038322)

(ref: vanderWel14) van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28, doi: [`10.1088/0004-637X/788/1/28`](http://doi.org/10.1088/0004-637X/788/1/28)

(ref: VanDokkum10) van Dokkum, P. G., Whitaker, K. E., Brammer, G., et al. 2010, ApJ, 709, 1018, doi: [`10.1088/0004-637X/709/2/1018`](http://doi.org/10.1088/0004-637X/709/2/1018)

(ref: VanDokkum13) van Dokkum, P. G., Leja, J., Nelson, E. J., et al. 2013, ApJL, 771, L35, doi: [`10.1088/2041-8205/771/2/L35`](http://doi.org/10.1088/2041-8205/771/2/L35)

(ref: Wisnioski15) Wisnioski, E., Förster Schreiber, N. M., Wuyts, S., et al. 2015, ApJ, 799, 209, doi: [`10.1088/0004-637X/799/2/209`](http://doi.org/10.1088/0004-637X/799/2/209)

(ref: Wolfire10) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191, doi: [`10.1088/0004-637X/716/2/1191`](http://doi.org/10.1088/0004-637X/716/2/1191)

(ref: Wuyts11) Wuyts, S., Förster Schreiber, N. M., van der Wel, A., et al. 2011, ApJ, 742, 96, doi: [`10.1088/0004-637X/742/2/96`](http://doi.org/10.1088/0004-637X/742/2/96)

(ref: Yabe12) Yabe, K., Ohta, K., Iwamuro, F., et al. 2012, PASJ, 64, 60, doi: [`10.1093/pasj/64.3.60`](http://doi.org/10.1093/pasj/64.3.60)

[^1]: <https://archive.stsci.edu/pub/hlsp/candels/uds/uds-tot/v1.0/>

[^2]: As compared with the $R_{52}$-SFR surface density relations recently obtained by (cite: Valentino20) and (cite: Boogaard20), SXDS1_13015 shows a lower $R_{52}$ at similar SFR surface density among SFGs at $z \sim 1 - 2$.

[^3]: Generally, the HWHM of a 2D Gaussian corresponds to half-light radius.

</paper>

Write the methods card for this paper.