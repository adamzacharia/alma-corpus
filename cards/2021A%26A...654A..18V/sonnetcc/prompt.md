# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...654A..18V\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...654A..18V",
 "title": "Maser emission from the CO envelope of the asymptotic giant branch star W Hydrae",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Vlemmings, W. H. T.",
 "n_authors": 3,
 "arxiv_id": "2109.05048",
 "doi": "10.1051/0004-6361/202141656",
 "alma_projects_linked_by_archive": [
  "2015.1.01446.S",
  "2016.A.00029.S",
  "2017.1.00824.S"
 ]
}
```

Paper text:
<paper>
# Maser emission from the CO envelope of the asymptotic giant branch star W Hydrae

Observation of CO emission around asymptotic giant branch (AGB) stars is the primary method to determine gas mass-loss rates. While radiative transfer models have shown that molecular levels of CO can become mildly inverted, causing maser emission, CO maser emission has yet to be confirmed observationally.

High-resolution observations of the CO emission around AGB stars now have the brightness temperature sensitivity to detect possible weak CO maser emission.

We used high angular resolution observations taken with the Atacama Large Millimeter/submillimeter Array (ALMA) to observe the small-scale structure of CO $J=3-2$ emission around the oxygen-rich AGB star W Hya.

We find CO maser emission amplifying the stellar continuum with an optical depth $\tau\approx-0.55$. The maser predominantly amplifies the limb of the star because CO $J=3-2$ absorption from the extended stellar atmosphere is strongest towards the centre of the star.

The CO maser velocity corresponds to a previously observed variable component of high-frequency H$_2$O masers and with the OH maser that was identified as the amplified stellar image. This implies that the maser originates beyond the acceleration region and constrains the velocity profile since we find the population inversion primarily in the inner circumstellar envelope. We find that inversion can be explained by the radiation field at 4.6 $\mu$m and that the existence of CO maser emission is consistent with the estimated mass-loss rates for W Hya. However, the pumping mechanism requires a complex interplay between absorption and emission lines in the extended atmosphere. Excess from dust in the circumstellar envelope of W Hya is not sufficient to contribute significantly to the required radiation field at 4.6 $\mu$m. The interplay between molecular lines that cause the pumping can be constrained by future multi-level CO observations.

# Introduction

The mass loss of asymptotic giant branch (AGB) stars, with main-sequence masses in the range $1-8$ M$_\odot$, is an important source of interstellar enrichment (cite: HO18). The primary method of determining the gas mass-loss rates of these stars is to use observations of CO lines in their circumstellar envelopes (CSEs). Radiative transfer calculations of rotational and vibrational CO transitions in the (sub)millimetre to far-infrared (far-IR) wavelength range are subsequently used to determine the total gas content in the CSE, and thus, indirectly, the AGB mass-loss rate.

It has long been known that, under specific conditions in CSEs, some of the lowest rotational energy levels of CO can become mildly inverted causing weak maser emission (cite: Goldsmith72; Morris80; Schoenberg88; Piehler91). Masing of CO emission could also occur in shocks in molecular clouds (cite: McKee82; Draine84). In these models the population inversion is primarily caused by absorption of $4.6~\mu$m photons that will excite CO to the first vibrational level. From this level it decays back to the ground vibrational state in higher rotational states. If the rate of absorption of the $4.6~\mu$m photons is sufficiently high, an inversion in the lowest rotational levels can occur. This requires the $4.6~\mu$m lines to have relatively low optical depth so that the IR emission can reach the region of the CSE where the population is not collisionally quenched. A detailed analysis thus restricts possible maser action to AGB stars that a have low mass-loss rate, a high CO abundance, and a strong IR radiation field (cite: Morris80; Schoenberg88). In particular, it was concluded that the most likely candidate AGB stars where CO maser action could be detected would be carbon stars with low mass-loss rates (cite: Morris80). Because the maser inversion is very sensitive to the IR radiation, CO abundance, and the density in the envelope, observations of CO masers could provide unique constraints on localised regions of the CO envelope and on the IR radiation field coming from the stellar atmosphere.

![](./Fig_WHyaCO.pdf)

There have been no confirmed detections of CO maser emission to date. Narrow $J=2-1$ CO emission around the carbon star V Hydrae was previously thought to be due to maser inversion (cite: Zuckerman86). However, later observations revealed that the narrow emission is identical in the $J=1-0$ line and is more likely a kinematic effect (cite: Zuckerman89). There are also no clear detections yet of CO maser emission from molecular clouds.

Here we present the first unambiguous detection of CO maser emission, in the $J=3-2$ transition, around the oxygen-rich AGB star W Hya. W Hya is a semi-regular variable star located at $\approx 100$ pc from the Sun (cite: Vlemmings03; vanLeeuwen2007) with a mass-loss rate of $\sim10^{-7}$ M$_\odot$ yr$^{-1}$ (cite: Maercker08; Khouri14) and a main-sequence mass, as constrained by oxygen isotopic ratios between 1.0 and 1.5 M$_\odot$ (cite: Khouri14; Danilovich2017). Continuum observations of the extended stellar atmosphere with ALMA show that, at $345$ GHz, the star has a brightness temperature of $\sim2700$ K and a size of $\sim5$ au (cite: Vlemmings19). These observations have also revealed strong variable surface hotspots with brightness temperatures sometimes in excess of $50000$ K (cite: Vlemmings17; Vlemmings19).

The maser is detected in high angular resolution observations taken at two epochs. We present the observations in §[2](#obs) and the results in §[3](#res). We compare in §[4](#disc) the results with simple radiative transfer models that investigate the dependence on the continuum radiation field (cite: Morris80) as well as a simplified implementation of the line overlap pumping described in (cite: Piehler91). Our conclusions are summarised in §[5](#conc).

# Observations and data reduction

The observations of W Hya presented in this paper were previously presented in (cite: Vlemmings17) and (cite: Vlemmings19). Here we summarise the observation set-up and calibration steps. The first epoch of observations of W Hya in ALMA band 7, which included the CO $J=3-2$ transition at $345.796$ GHz, were taken as part of ALMA project 2015.1.01446.S (PI: Takigawa) in three executions between 30 Nov and 5 Dec 2015 for a total on-source time of $\sim2.1$ hr. The second epoch was observed as part of project 2016.A.00029.S (PI: Vlemmings) on 25 Nov 2017 with an on-source observing time of $\sim35$ min. All observations were taken in spectral line mode, and the spectral window (spw) that contained the CO $J=3-2$ transition provided a native spectral resolution of 0.98 MHz ($\sim0.9$ km s$^{-1}$) for both epochs. The initial calibration (of the bandpass, amplitude, absolute flux-density scale, and phase) was done using the Common Astronomy Software Applications (CASA) package (cite: McMullin07), using the manual calibration scripts provided by the observatory. Further observation details, including the flux and gain calibrators used, are given in (cite: Vlemmings17) and (cite: Vlemmings19).

After the initial calibration we performed two rounds of phase self-calibration on the strong stellar continuum. The self-calibration improved the continuum signal-to-noise ratio (S/N) by a factor of three. Imaging of the CO lines was done using Briggs weighting with a robust parameter of $-1.0$ and $0.5,$ respectively for the two epochs, in order to achieve a similar angular resolution. The resulting beam sizes were $31\times21$ mas ($-63^\circ$ from north) and $29\times21$ mas ($-68^\circ$). The maximum recoverable scale is approximately $0.6\ensuremath{''}$. Despite the additional observing time for epoch 1, the rms noise near the CO line was $\sim3.5$ mJy beam$^{-1}$ for both epochs due to the different weighting adopted.

# Results

![](./obsspectra.pdf)

In both observational epochs, bright and relatively compact CO $J=3-2$ emission is detected. The emission maps of the brightest channels are shown in Fig. [1](#WHya_COmap). After subtracting the $\sim2700$ K stellar continuum, the peak of the emission has a brightness temperature of $T_b\approx1950$ K in the two epochs. The emission region is complex and, if it consists of multiple more compact components, the derived $T_b$ presents a lower limit. As the emission is amplifying the underlying stellar continuum, the brightness temperatures imply a maser optical depth of $\tau\approx-0.55$.

The morphology of the bright masing CO emission has markedly changed between the two observing sessions. During the first epoch the emission appears the be dominated by a relatively compact region towards the western hemisphere of the star, close to the bright hotspots observed on the stellar continuum surface (cite: Vlemmings17). In the second epoch the emission is more extended and follows along the eastern limb of the stellar continuum.

The CO spectra taken in a single beam towards the peak of the maser emission are shown in Fig. [2](#COspec)(left). In both epochs the maser emission is confined to a few velocity channels ($\sim1$ km s$^{-1}$ in width) between $33$ and $36.5$ km s$^{-1}$ with a peak at $\sim35$ km s$^{-1}$. The brightest spectral component has a full width at half maximum (FWHM) of $1.9$ and $2.2$ km s$^{-1}$ in the two epochs, respectively. The masers are superimposed on an absorption profile originating from CO in the extended stellar atmosphere. This absorption profile is of very different depth at the position of the CO maser at each epoch. To investigate if there is any short-term variability in the CO maser emission we also individually imaged the three days in epoch 1 (30 Nov, 3 Dec, and 5 Dec). Although the synthesised beams are different, the morphology of the maser emission does not change significantly. The spectra of the three days, taken towards the peak identified in the combined epoch 1 image and convolved to a common beam size, are shown in Fig. [2](#COspec)(right). The emission brightness temperature appears to change from $T_b\approx1330$ K on 30 Nov to $T_b\approx2000$ K on 3 Dec and to $T_b\approx1570$ K on 5 Dec 2015. If the maser emission is more compact than the common beam of $30\times21$ mas, these brightness temperature values would correspond to lower limits. This indicates that there could be variability of the order of $\pm20\%$ within only a five-day timescale. For comparison, the continuum flux varies by less than $2.5\%$ over the three days so the flux variation is not due to an uncertainty in the flux calibration.

# Discussion

## Morphology and variability

![](./Schematic.pdf)

As seen in Fig. [1](#WHya_COmap), a common feature at the two epochs is that the brightest CO maser emission is found projected towards the limb of the stellar continuum. Although CO emission also originates from the extended AGB atmosphere, maser inversion of the ground state CO lines cannot occur there because the density of the collision partners is too high (cite: Vlemmings17; Khouri18). Thus, the maser emission has to originate from CO gas beyond the dust formation region where the wind is accelerated. There the CO maser in front of the star will amplify the stellar continuum emission. However, as illustrated in Fig. [3](#schematic), at the expansion velocity of the large-scale outflow, the CO molecules in the extended atmosphere absorb more efficiently towards the stellar centre than the limbs. Hence, the CO molecules in the outflow see a limb-brightened star, and amplification is naturally strongest towards the limbs. This can also explain the morphological changes between the observing epochs as the maser emission will depend on a combination of stellar surface emission variations (such as the observed hotspots) and the depth of the molecular absorption at the maser velocity. Finally, the maser emission will also be affected by a possible density and velocity structure in the foreground material. However, because the maser inversion is small, this effect will be much less pronounced compared to SiO, H$_2$O, and OH masers. Furthermore, transverse motions of dense clumps across the full stellar disk within two years would, at the distance of W Hya, require a transverse velocity of $\sim10$ km s$^{-1}$, which is much higher than the turbulent velocities estimated in CSEs ($\sim0.7$ km s$^{-1}$ for W Hya, (cite: Khouri14)). Thus, we suggest that the changes in the maser emission primarily reflect changes in the underlying structure of the star and extended atmosphere.

The flux variation of $\pm20\%$ observed over five days during the first epoch is likely due to a combination of changes in the extended atmosphere coupled with small changes in foreground masing material. If the maser is amplifying the same background emission, a $\pm20\%$ variability reflects a similar change in the background emission or small variations in the maser optical depth between $\tau\sim-0.4$ and $-0.56$. The background continuum emission itself does not change by more than a few percent, which means that it is unlikely that the observed variability is the result of rapid changes in the stellar continuum. As seen in Fig. [2](#COspec)(right), the atmospheric CO absorption itself shows that variations up to $\sim10\%$ could be present. The maser optical depth is also very sensitive to the pumping emission at 4.6 $\mu$m and the effect of line overlap (see § [4.3.1](#models)). Thus, a small change in the background 4.6 $\mu$m emission and CO absorption of the stellar continuum in the extended atmosphere, together with small-scale turbulence in the masing gas that alters the coherent velocity path length, can cause the observed variation in maser flux.

![](./modelspecs.pdf)

## Velocity

The velocity of the CO maser remained stable at $\sim35$ km s$^{-1}$ over the two epochs with a FWHM velocity width of $\sim2$ km s$^{-1}$. This means that the maser coincides in velocity with the brightest 1665 and 1667 MHz OH maser at $35.6$ km s$^{-1}$, observed between 1999 and 2002, which was shown to be amplifying the background stellar radio continuum (cite: Vlemmings03). At 183 GHz, H$_2$O masers show a very distinct emission peak at $35.1$ km s$^{-1}$, with almost the same strength as the main peak (cite: Humphreys17). A similar feature, though slightly weaker compared to the peak emission, is seen in the 1.296 THz H$_2$O maser (cite: Neufeld17), while observations of the 658 GHz H$_2$O maser show a weak but distinct peak at the same velocity (cite: Baudry18). The 321 and 325 GHz H$_2$O maser spectra from (cite: Yates95) show multiple peaks, but they do not extend to the velocity where we find the CO maser. Similarly, the 22 GHz H$_2$O masers spectra show no emission at around $35$ km s$^{-1}$ (cite: Imai19) and imaging with the MERLIN interferometer seems to show that the 22 GHz masers are predominantly found in a tangentially amplified shell between $\sim5$ and $25$ au from the star (cite: Richards12).

Even if all features seen in the various masers around $35$ km s$^{-1}$ are related, it is unlikely that this is due to a physical association in a single maser cloud. The 658 GHz H$_2$O masers require a high temperature ($>1000$ K) and H$_2$O density ($>10^5$ cm$^{-3}$), while the 183 GHz H$_2$ masers are found over a larger range of temperatures (between $\sim400$ K and $2500$ K), but with an H$_2$O density $<10^5$ cm$^{-3}$. The conditions for the 1.296 THz masers fall roughly between the other two maser transitions (cite: Gray16). Considering an H$_2$O abundance of $1.5\times10^{-3}$ for W Hya (cite: Maercker08), this means that the H$_2$O masers are excited at molecular hydrogen densities of $n_{\rm
  H_2}\sim 10^{6}$ up to $10^9$ cm$^{-3}$. For the typically assumed mass-loss rate of W Hya this corresponds to a region within $\sim35$ au, and hence well within the region where we would expect the amplified stellar image in the OH masers. According to an OH maser shell model of (cite: Szymczak98), the OH masers occur in a shell with a radius of $\sim1000$ au and a thickness of $\sim300$ au, although the fit of the observations to a thin shell is poor. Furthermore, the time baseline of the various observations spans more than 20 years. It is thus more likely that the velocity of the CO maser and the other features corresponds to the largest coherent velocity path length towards the star, which results in an amplified stellar image in a large number of different maser species and transitions.

![](./ACAspecs.pdf)

![](./RDorCO.pdf)

![](./tauplot.pdf)

![](./MLspecs.pdf)

## Radiative transfer models

### Continuum pumping

+---------------------------------:+----------------------------------------:+
| Stellar parameters:                                                        |
+----------------------------------+-----------------------------------------+
| T$_*$                            | 2500 K                                  |
+----------------------------------+-----------------------------------------+
| L$_*$                            | 5400 L$_\odot$                          |
+----------------------------------+-----------------------------------------+
| D                                | 115 pc                                  |
+----------------------------------+-----------------------------------------+
| Envelope parameters:                                                       |
+----------------------------------+-----------------------------------------+
| $\dot{\rm M}$                    | $1.5\times 10^{-7}$ M$_\odot$ yr$^{-1}$ |
+----------------------------------+-----------------------------------------+
| $R_{\rm in}$                     | 3.68 au                                 |
+----------------------------------+-----------------------------------------+
| Abundance and e-folding radius:                                            |
+----------------------------------+-----------------------------------------+
| $X_{\rm CO}$                     | $4\times10^{-4}$                        |
+----------------------------------+-----------------------------------------+
| $R_{\rm 0.5}$                    | 630 au                                  |
+----------------------------------+-----------------------------------------+
| Gas velocity law:                                                          |
+----------------------------------------------------------------------------+
| $V(r)=V_{\rm 0}+(V_{\infty}-V_{\rm 0})(1-R_{\rm in}/r)^{\beta}$            |
+----------------------------------+-----------------------------------------+
| $\beta$                          | 5.0                                     |
+----------------------------------+-----------------------------------------+
| $V_{\rm 0}$                      | 3.0                                     |
+----------------------------------+-----------------------------------------+
| $V_{\infty}$                     | 7.5                                     |
+----------------------------------+-----------------------------------------+
| Turbulent velocity:                                                        |
+----------------------------------+-----------------------------------------+
| $V_t$                            | 0.8                                     |
+----------------------------------+-----------------------------------------+
| Dust:                                                                      |
+----------------------------------+-----------------------------------------+
| $\tau_{10 \mu{\rm m}}$           | 0.1                                     |
+----------------------------------+-----------------------------------------+
| Type                             | Silicate                                |
+----------------------------------+-----------------------------------------+

: Adopted parameters of the baseline CO model$^a$

Table notes:

In order to investigate the occurrence of the CO maser in the $J=3-2$ transition, we perform one-dimensional radiative transfer models using the Monte Carlo radiative transfer code *mcp* (cite: Schoeier01). We include the CO rotational levels $J=0$ to $J=81$ and the vibrational levels $v=0$ and $v=1$. The transition frequencies, energy levels, and Einstein coefficients were taken from the CDMS and JPL databases (cite: Muller01; Picket98) and the collisional rate coefficients come from (cite: Yang10).

It has long been recognised that mild population inversion of CO can occur for a narrow mass-loss range (cite: Morris80). The maser range is set by the mass-loss rate (or gas density) and CO abundance as well as the availability of 4.6 $\mu$m pump photons. At high gas density, the CO is mostly collisionally excited, quenching the maser. A high CO column density also produces a high opacity at the 4.6 $\mu$m CO $v=0-1$ transitions reducing the volume over which the maser can operate. Conversely, as the maser requires a sufficiently large negative optical depth, a CO column density that is too low also reduces the maser strength. To investigate the occurrence of the CO maser around W Hya, we model the observations of a single aperture (with a size of $2R_*$) towards the star using the parameters for the CO envelope given in Table [1](#Table:COmod) taken from (cite: Khouri14); we do not adjust the distance and adopt the value used in the model. Since the model is one-dimensional we only compare the emission along the line of sight to the star. In order to include the effect of the broad CO absorption that originates from the extended atmosphere, we include this absorption profile on top of the stellar black body when ray-tracing the solutions of the radiative transfer model. We include a comparison of the model with recent ACA observations (with a beam size of $4.5\times3.6\ensuremath{''}$). The results of this model are shown in Fig. [4](#figspecs)(left). The ACA spectrum and corresponding model are shown in Fig. [5](#ACAspecs)(left). No maser emission is generated with these model parameters. Additionally, at the terminal velocity, an absorption component is seen that is the result of observing towards the star through the cool blue-shifted CO envelope in the foreground. Such a narrow absorption component is absent in our observed spectrum, although we do see this effect in high angular resolution observations of the CO $J=2-1$ emission around the nearby AGB star R Dor (shown in Fig. [6](#RDor)).

Subsequently, we artificially adjust the strength of the 4.6 $\mu$m radiation field, following the same method as in (cite: Morris80), to investigate when maser emission is generated. Specifically, we multiply the radiation field for all wavelengths $<5~\mu$m by a factor $M$. The result of these models are shown in Figs. [4](#figspecs)(right) and [5](#ACAspecs)(right). Several things become apparent from these models. Firstly, a maser of sufficient strength can be generated if the radiation field at 4.6 $\mu$m is increased by a factor $M\sim3$. However, because the inversion mostly occurs in the inner envelope, the maser velocity is too close to the stellar velocity in the adopted model. Finally, the maser width is too narrow. In order to overcome these issues, we require a larger velocity at the inner envelope ($V_0\approx4.2$ km s$^{-1}$), a slightly steeper acceleration ($\beta\approx 2.5$), and larger turbulent velocity component ($V_t\approx 1.0$ km s$^{-1}$). Varying these three parameters, we can reproduce the maser as seen in the representative model in Fig. [4](#figspecs)(right). While making these changes, we did not consider further constraints from the lower angular resolution observations. In order to investigate where, in this model, most of the maser emission originates with respect to the star, the extended atmosphere, and the CSE, we present the radial CO optical depth $\tau$ as a function of radius in Fig. [7](#tau). Population inversion in the $J=3-2$ line persists throughout most of the CSE and peaks around $7$ au. This can be compared to the stellar radius (at 345 GHz) of $2.5$ au and the approximate size of the extended stellar atmosphere and start of the dust formation zone at $\sim 3.7$ au. In the extended atmosphere, no maser emission can occur because of the high densities. As discussed in § [4.1](#morph) and illustrated in Fig. [3](#schematic), the stellar continuum emission is absorbed by CO gas in the extended atmosphere before it is subsequently amplified by the foreground CO maser. The exact shape of the optical depth profile is strongly dependent on the velocity profile and enhanced IR radiation field adopted in the model.

In Fig. [8](#MLspecs) we investigate the effect of changing the mass-loss rate on our maser model. Under the assumed conditions we find that maser emission is generated, from different parts of the envelope, for mass-loss rates between $0.5-5\times10^{-7}$ M$_\odot$ yr$^{-1}$. Specifically for W Hya, most of this range can be ruled out by the lower angular resolution observations, limiting the rate to between $1.5-3.0\times10^{-7}$ M$_\odot$ yr$^{-1}$.

In our models we can reproduce the required continuum excess by including a dust shell with an optical depth at 4.6 $\mu$m of $\sim0.2$, which is located closer to the star than the maser-emission region. Such a dust shell would have optical depths greater by at least a factor of five at $\sim 10~\mu$m and $\sim 1~\mu$m, affecting the spectral energy distribution in a way that is not supported by the observed infrared spectrum (cite: Justtanont14). Although the model results show that the maser can be reproduced by a general increase in IR radiation field and fine-tuning the model parameters, we conclude that this is not a viable solution. We thus investigate pumping that can occur due to line overlap around 4.6 $\mu$m.

![](./IRdiff_spectra.pdf)

### Line overlap

Line overlap of spectral lines around the pump wavelength at 4.6 $\mu$m has also been suggested as the cause of CO maser emission (cite: Piehler91). Specifically, a combination of absorption and emission lines originating from the stellar atmosphere, can change the relative pumping of the $v=0-1$ IR lines. Here we focus on the effect on the IR lines of the $\Delta J\pm1$ transitions between the ground state and the first vibrationally excited state for $J=0$ up to $J=5$. By relative changes of the radiation field seen by these lines, maser inversion can readily be obtained. In Fig. [9](#IRdiffspecs) we show the results of changing the stellar radiation field experienced by these transitions. We adopted the CO envelope parameters from Table [1](#Table:COmod) with the adjustment to the velocity field as discussed previously. Based on observations around 4.6 $\mu$m (cite: Justtanont14) we include an overall decrease in the stellar radiation field around this wavelength, adopting a transmission of 85% of the stellar black body. As expected, the appearance of the CO $v=0, J=3-2$ maser is closely related to the relative pumping into and out of the $J=3$ level. The maser emission in this transition requires a slight overpopulation of the $v=0, J=3$ level. This means that an increase in the intensity of the radiation field affecting the transition between the $v=1, J=3$ level and the $v=0, J=2$ levels will decrease the $v=0, J=2$ population in favour of the $v=1, J=3$ level. As a consequence, the ratio of $v=0, J=3$ to $v=0, J=2$ inverts. Similarly, a decrease in the intensity of the radiation field affecting the transition between $v=1, J=3$ and $v=0, J=4$ will reduce the pumping from the $v=0, J=4$ to the $v=1, J=3$ level. The subsequent decay of the larger population in the $v=0, J=4$ level to the $v=0, J=3$ level will result in maser inversion in the CO $v=0, J=3-2$ transition. Our models and the more extensive study involving many spectral components in (cite: Piehler91) highlight that the maser emission is highly sensitive to the exact profile, including absorption and emission lines, of the stellar atmosphere. The current observations of a single transition can be reproduced by many different combinations of relative pumping in the IR. Still, considering the rich structure known to exist in the spectra originating from the stellar atmosphere, it is highly likely that the line overlap is the main reason for the observed CO maser. In particular, also because pumping due to continuum emission requires an increase in the IR radiation field that is not observed (see § [4.3.1](#models)). The range of mass-loss over which a maser can be reproduced using the pumping of a single IR line is similar to that shown in Fig. [8](#MLspecs) for the excess continuum IR emission. However, a detailed study of this would involve too many degenerate parameters to be constrained with a single observed maser transition.

A study involving multiple masing transitions can provide stronger constraints on the contribution of the different IR lines. In Appendix [6](#others) we investigate the effect of selective pumping of the different IR lines on the CO $J=2-1$ (Fig. [11](#IRdiffspecs21)) and $J=4-3$ (Fig. [13](#IRdiffspecs43)) transitions. We also include the CO $J=3-2$ results without the atmospheric absorption profile in Fig. [12](#IRdiffspecs32). These model results show that in particular the combination of these three lines can be used to investigate which $v=0-1$ IR transitions are responsible for the CO maser pumping since all three are affected differently by pumping the different IR lines. For example, the extra absorption between the $v=0, J=4$ and $v=1, J=3$ levels (which can explain the CO $J=3-2$ maser of W Hya) would not produce any maser in the $J=2-1$ transition. This could explain why no maser is observed in the CO $J=2-1$ transition of R Dor (Fig. [6](#RDor)) even though R Dor has a mass-loss rate similar to that of W Hya.

![](./IRdiff_ACAspectra.pdf)

Similar to the continuum pumping, a change in the relative emission incident on the individual 4.6 $\mu$m CO transitions also changes the CO emission profile on the larger scales shown in Fig. [10](#IRdiffspecsACA). Because of the large number of degeneracies including the individual line pumping, we did not attempt to adjust the standard CSE model to simultaneously reproduce the larger scale observations. However, it is clear that the models that can reproduce the maser emission also produce changes in the larger scale emission that do not match the observations. The selective pumping our model requires has a different relative effect on each of the low-excitation rotational CO lines. Hence, model parameters such as mass-loss rate, velocity structure, and turbulent velocity will be much better determined when considering constraints from CO maser emission, when present.

# Conclusions

Using ALMA long baseline observations, we have confirmed that mild maser inversion occurs in the CSE of the AGB star W Hya. The maser emission is shown to occur at a stable $V_{\rm LSR}$ velocity in two observational epochs separated by two years. While the flux density of the maser emission is also similar, the morphology has altered significantly in this time. Since the maser is seen to amplify the underlying stellar continuum, the changes in morphology are likely due to a combination of small-scale structure in the masing material and changes in the underlying stellar continuum. The maser emission is found at $V_{\rm LSR}\approx 35$ km s$^{-1}$, which corresponds, within the spectral resolution, to the velocity of the amplified stellar emission feature seen in the OH 1665 and 1667 MHz masers (cite: Vlemmings03). It also corresponds to the velocity of a bright emission peak in the 183 GHz H$_2$O masers (cite: Humphreys17) and a weaker feature in the 658 GHz and 1.296 THz H$_2$O masers (cite: Baudry18; Neufeld17). This implies a large column of material at coherent velocity in front of the star since the excitation conditions of the masers and the CO stretch over a wide range of densities and temperatures.

We can reproduce the CO maser emission assuming a mass-loss rate similar to that typically derived for W Hya ($\sim10^{-7}$ M$_\odot$ yr$^{-1}$, e.g. (cite: Khouri14)). We find the CO $J=3-2$ line can be inverted if the 4.6 $\mu$m continuum radiation field for the circumstellar dust is significantly enhanced. However, this requires a radiation field at 4.6 $\mu$m that is inconsistent with observations (cite: Justtanont14). Instead, the likely explanation for the maser emission involves a complex structure of atmospheric emission and absorption lines that produce differential pumping of the IR CO transitions around 4.6 $\mu$m, between the ground level and the first vibrational level. A more exact determination of the relative pumping of these lines is not possible with the current observations of only one CO maser transition and would require near-simultaneous observations at high angular resolution of multiple rotational transitions. Our models show that the relative IR pumping that gives rise to the maser also introduces an overall uncertainty in the molecular line radiative transfer modelling for stars such as W Hya. A proper inclusion of the IR lines in the AGB atmosphere is thus needed to further reduce uncertainties in mass-loss and radiative transfer modelling.

# Acknowledgements

WV and TK acknowledge support from the Swedish Research Council under grants No. 2014-05713 and 2019-03777. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01446.S, ADS/JAO.ALMA#2016.A.00029.S, ADS/JAO.ALMA#2016.2.00025.S, and ADS/JAO.ALMA#2017.1.00824.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We also acknowledge support from the Nordic ALMA Regional Centre (ARC) node based at Onsala Space Observatory. The Nordic ARC node is funded through Swedish Research Council grant No 2017-00648.

30 natexlab

(ref: Baudry18) Baudry, A., Humphreys, E. M. L., Herpin, F., et al. 2018, A&A, 609, A25

(ref: Danilovich2017) Danilovich, T., Lombaert, R., Decin, L., et al. 2017, A&A, 602, A14

(ref: DeBeck2018) De Beck, E. & Olofsson, H. 2018, A&A, 615, A8

(ref: Draine84) Draine, B. T. & Roberge, W. G. 1984, ApJ, 282, 491

(ref: Goldsmith72) Goldsmith, P. F. 1972, ApJ, 176, 597

(ref: Gray16) Gray, M. D., Baudry, A., Richards, A. M. S., et al. 2016, MNRAS, 456, 374

(ref: HO18) Höfner, S. & Olofsson, H. 2018, A&ARv, 26, 1

(ref: Humphreys17) Humphreys, E. M. L., Immer, K., Gray, M. D., et al. 2017, A&A, 603, A77

(ref: Imai19) Imai, H., Nakagawa, A., & Takaba, H. 2019, PASJ, 71, 120

(ref: Justtanont14) Justtanont, K., de Jong, T., Tielens, A. G. G. M., Feuchtgruber, H., & Waters, L. B. F. M. 2004, A&A, 417, 625

(ref: Khouri14) Khouri, T., de Koter, A., Decin, L., et al. 2014, A&A, 570, A67

(ref: Khouri18) Khouri, T., Vlemmings, W. H. T., Olofsson, H., et al. 2018, A&A, 620, A75

(ref: Maercker08) Maercker, M., Schöier, F. L., Olofsson, H., Bergman, P., & Ramstedt, S. 2008, A&A, 479, 779

(ref: McKee82) McKee, C. F., Storey, J. W. V., Watson, D. M., & Green, S. 1982, ApJ, 259, 647

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Morris80) Morris, M. 1980, ApJ, 236, 823

(ref: Muller01) Müller, H. S. P., Thorwirth, S., Roth, D. A., et al. 2001, A&A, 370, L49

(ref: Neufeld17) Neufeld, D. A., Melnick, G. J., Kaufman, M. J., et al. 2017, ApJ, 843, 94

(ref: Picket98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: Piehler91) Piehler, G., Kegel, W. H., & Tsuji, T. 1991, A&A, 245, 580

(ref: Ramstedt20) Ramstedt, S., Vlemmings, W. H. T., Doan, L., et al. 2020, A&A, 640, A133

(ref: Richards12) Richards, A. M. S., Etoka, S., Gray, M. D., et al. 2012, A&A, 546, A16

(ref: Schoenberg88) Schoenberg, K. 1988, A&A, 195, 198

(ref: Schoeier01) Schöier, F. L. & Olofsson, H. 2001, A&A, 368, 969

(ref: Szymczak98) Szymczak, M., Cohen, R. J., & Richards, A. M. S. 1998, MNRAS, 297, 1151

(ref: vanLeeuwen2007) van Leeuwen, F. 2007, A&A, 474, 653

(ref: Vlemmings17) Vlemmings, W., Khouri, T., O’Gorman, E., et al. 2017, Nature Astronomy, 1, 848

(ref: Vlemmings19) Vlemmings, W. H. T., Khouri, T., & Olofsson, H. 2019, A&A, 626, A81

(ref: Vlemmings03) Vlemmings, W. H. T., van Langevelde, H. J., Diamond, P. J., Habing, H. J., & Schilizzi, R. T. 2003, A&A, 407, 213

(ref: Yang10) Yang, B., Stancil, P. C., Balakrishnan, N., et al. 2010, ApJ, 718, 1062

(ref: Yates95) Yates, J. A., Cohen, R. J., & Hills, R. E. 1995, MNRAS, 273, 529

(ref: Zuckerman86) Zuckerman, B. & Dyck, H. M. 1986, ApJ, 311, 345

(ref: Zuckerman89) Zuckerman, B. & Dyck, H. M. 1989, A&A, 209, 119

# Other CO maser transitions

In Figs. [11](#IRdiffspecs21), [12](#IRdiffspecs32), and [13](#IRdiffspecs43) we present the same models from § [4.3.2](#overlap), including different relative radiation fields for the $v=0-1$ IR transitions, for the CO $J=2-1$, $3-2,$ and $4-3$ lines. In these models no atmospheric absorption profile was included.

![](./IRdiff_spectraCO21.pdf)

![](./IRdiff_spectraCO32.pdf)

![](./IRdiff_spectraCO43.pdf)

[^1]: wouter.vlemmings@chalmers.se

</paper>

Write the methods card for this paper.