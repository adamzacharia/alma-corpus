# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9.1486L\sonnetcc\reply.txt

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
 "bibcode": "2025NatAs...9.1486L",
 "title": "Pristine ices in a planet-forming disk revealed by heavy water",
 "year": 2025,
 "journal": "Nature Astronomy",
 "first_author": "Leemker, Margot",
 "n_authors": 7,
 "arxiv_id": "2510.19919",
 "doi": "10.1038/s41550-025-02663-y",
 "alma_projects_linked_by_archive": [
  "2021.1.00186.S",
  "2023.1.00588.S"
 ]
}
```

Paper text:
<paper>
# Pristine ices in a planet-forming disk revealed by heavy water

\[1\], , 2\], 3\], , 4\], ,

6\], , 7\], 8\], ,

Water may have been delivered to Earth via cometary and/ or asteroid impacts, tracing the pristine material left over from the protoplanetary disk where the Solar System originated . However, it is unclear whether the water ice on these bodies primarily formed in e.g., the protoplanetary disk phase or is much older and originated from the parent molecular cloud . This is because the bulk water reservoir is extremely difficult to detect and follow across the various phases of star and planet formation . If the water molecules that formed in the cloud survive the cloud collapse into a protostar with a surrounding envelope and subsequently the formation of a disk, then protoplanetary disks are injected with a rich chemical icy inventory as many complex organic molecules (COMs) have formation pathways in the ice . This potential ice inheritance would set the initial conditions for the chemical inventory of protoplanetary disks and is crucial to interpreting observations of COMs in disks. Intriguingly, if the water ice survives the journey from cloud to disk to comets and possibly (exo-)planets, then the water seen across all these phases and possibly on Earth predates the formation of the star and our Sun, respectively .

A sensitive tracer to distinguish the inheritance and (partial) reset of water ice from pre-stellar cores to protoplanetary disks is the deuteration level of water. In case of reset, at least one of the chemical bonds between the atoms of the water molecule is destroyed. The deuteration is only enhanced above the D/H ratio of $2\times 10^{-5}$ in the interstellar medium (ISM) under specific conditions: below 25 K and where the density is sufficiently high for the freeze-out of atoms and molecules (few times $10^4$ cm$^{-3}$) ; therefore, water ice formed at these low temperatures will be rich in deuterated water isotopologues. On the contrary, reprocessing of this pristine material at temperatures higher than 500 K can lower the abundance of deuterated water isotopologues by destroying the molecules themselves . The high level of singly deuterated water (HDO) seen in protostellar envelopes, disks, and comets has been presented as evidence of the inheritance of water . However, the abundance of HDO can be as high as $\sim10^{-3}$ with respect to even if the majority of the water reservoir is reprocessed . Instead, doubly deuterated water () is the most sensitive tool to distinguish inheritance from reset because it cannot reform efficiently after reprocessing. Yet, observations targeting this isotopologue are rare across all star- and planet formation phases because its abundance is expected to be low even if deuteration is enhanced because of the double deuteration and the low D/H of the ISM.

In particular, observations of doubly deuterated water are missing in the protoplanetary disk stage. The few existing observations probing water ice in disks cannot distinguish whether water is formed in the initial stages of star and planet formation or in situ due to a lack of detected isotopologues . In addition, most protoplanetary disks are too cold to host a large and observable reservoir of gas-phase water. Tracers other than water isotopologues provide evidence for both inheritance and reprocessing depending on the disk and tracers observed. Inheritance is suggested by the detection of gas-phase methanol in three disks that are too warm for significant CO freeze-out . As methanol can only form efficiently when CO is frozen-out, the methanol ice in those disks must have formed before the envelope collapsed to form a disk and survived this process . On the other hand, the deuteration seen in methanol and other complex organic molecules in the same disk as the one analyzed in this work, V883 Ori, is lower than expected based on a much younger protostellar envelope and a much older comet. This has been interpreted as an indication for some reprocessing of the ices in this disk , yet possibly is slightly more reprocessed than water due to its lower sublimation temperature . We present observations in the V883 Ori disk of doubly-deuterated water , the most sensitive tracer to distinguish inheritance from reprocessing to shed light on the origin of ices in disks, in particular the origin of water ice.

# Results

We detect the $1_{1,0}-1_{0,1}$ transition at 316.7998 GHz in the disk surrounding the young, outbursting V883 Ori star with the Atacama Large Millimeter/submillimeter Array (ALMA). This star is located at 400 pc (1300 ly) in the Orion molecular cloud and has a source velocity of 4.3 km s$^{-1}$ . Freshly sublimated ices are seen in this disk due to the heating from the outbursting star allowing for a unique look into the bulk water reservoir . We compare our detection with the previously observed HDO and H$_2^{18}$O emission in this disk .

The line observed in this program is blended with emission from neighboring transitions of deuterated methanol () at 316.7916 GHz ($3_{2, 1}-3_{-1, 3}$ A) and 316.7951 GHz ($7_{0, 7}- 6_{0, 6}$ A) and two dimethyl ether () transitions at 316.7915 GHz ($22_{6,16}-22_{5,17}$ EE) and 316.7925 GHz ($22_{6,16}-22_{5,17}$ AA), respectively, similar to observations of younger Class 0 objects . To separate the from these COMs, each pixel in the image cube is shifted by the projected Keplerian velocity associated to that pixel in order to remove the rotation component of the line velocity, before extracting the disk-integrated spectrum in an elliptical region with a $0\ensuremath{\overset{\prime\prime}{.}}4$ semi-major axis presented in Figure [1](#fig:spec). The non-shifted version is presented in Extended Data Figure 1. The line is detected at a peak signal-to-noise ratio of 11 in the shifted spectrum, where the noise is estimated using the rms of 520 independent shifted spectra extracted from a 19" square in the cube without primary beam correction, excluding the inner $2\ensuremath{\overset{\prime\prime}{.}}4$ square to avoid possible contamination with extended line emission. In addition, the channel maps show significant emission across multiple channels that can only be attributed to the molecule and not to any neighboring lines of complex organic molecules. . An overview of the , HDO, and H$_2^{18}$O line properties is presented in Table [1](#tab:CDMS_JPL). The line flux is measured both from the channel maps presented in Extended Data Figure 2, 3, and 4 and from the shifted spectra presented in Extended Data Figure 5, 6, 7, and 8. An overview of these line fluxes is presented in Table [2](#tab:fluxes), where the reimaged HDO and H$_2^{18}$O emission originally presented in are included for consistency. The flux measured using the Keplerian masks is considered to be the fiducial flux (see Sect. [3.4](#sec:flux) for details).

As the spatial distribution of all three water isotopologues (, HDO, and H$_2^{18}$O) is similar (see Figure [2](#fig:D2O_channel_maps_cf_HDO) for the channel maps of and HDO and (cite: Tobin2023) for a comparison of HDO and H$_2^{18}$O), we use the excitation temperature of $199\pm 42$ K of the HDO molecule , the only water isotopologue with two observed transitions, for all the water isotopologues. The effect of the uncertainty on this excitation temperature is discussed in Supplementary Sect. 3.1 as one of the HDO lines used for this measurement is heavily blended with an emission line of a COM, possibly affecting the derived excitation temperature. The line fluxes are measured using Keplerian masks that separate the water isotopologue emission from that of the neighbouring COMs in both Right Ascension, Declination, and velocity. These line fluxes of the , HDO, and H$_2^{18}$O transitions are then converted to column densities of $(4.2 \pm 1.2)\times 10^{13}$ cm$^{-2}$, $(49.5 \pm 6.9) \times 10^{14}$ cm$^{-2}$, and $(23.7 \pm 5.7) \times 10^{14}$ cm$^{-2}$ assuming an emitting area equal to the elliptical region used to extract the spectrum and the flux integrated over the velocity channels where all three water isotopologues can be separated from other emission lines (see also Sect. [3.4](#sec:flux), [3.5](#sec:rot_dia), Supplementary Sect. 3, and Table [3](#tab:N)). As no strong isotope selective effects are expected between and H$_2^{18}$O, the H$_2^{18}$O column density is scaled to a total column density of $(13.3\pm 3.2) \times 10^{17}$ cm$^{-2}$ using the typical ratio of $560 \pm 25$ in the ISM , consistent with the lower limit derived in the HL Tau disk of $N($H$_2^{16}$O$)/N($H$_2^{18}$O$) >40$ . These column densities translate to / = $(3.2 \pm 1.0) \times 10^{-5}$ and (/HDO) / (HDO/) = $2.3 \pm 1.0$.

# Discussion and conclusions

## Water isotopologue ratios along the water trail

Both the / and the (/HDO) / (HDO/) ratios in the V883 Ori disk are similar to the observed values of / = $(2-9)\times 10^{-5}$ and (/HDO) / (HDO/) = $2.2-7.1$ in younger Class 0 objects , which are expected to trace pristine ices. In addition, the / ratio in the V883 Ori disk is similar to that of $(1.9 \pm 1.0)\times 10^{-5}$ in the comet 67 P , see Figure [3](#fig:inheritance_vs_reset). This strongly indicates that the ice in the V883 Ori disk is inherited from the cold molecular cloud that collapsed to form a Class 0 protostar with protostellar envelope and subsequently an embedded disk, and potentially connects to the cometary phase.

The abundance in the V883 Ori disk is not expected to be greatly altered by the outburst as modelling of HDO and in a 1D evolving disk around an outbursting star has shown that the outburst only affects the water deuteration in the inner 1-3 au . The emission of the water isotopologues in the V883 Ori disk is only seen much further out at radii larger than 40 au, as optically thick dust hides the line emission inside that radius .

The colored background in Figure [3](#fig:inheritance_vs_reset) indicates the range of / ratios consistent with inheritance (blue) and reset (red) based on chemical modelling of gas and ice in a collapsing core by . These simulations follow gas parcels as the rotating core collapses from the inside out and forms a disk and envelope. These stream lines are post processed with a dedicated chemical network modelling the deuterium chemistry in the gas, a chemically active surface layer of ice interacting with the gas, and a chemically inert bulk ice phase. As these stream lines trace a range in physical conditions, also the water isotopologue ratios show a range of possible values for either inheritance (all stream lines where $\lesssim 10$% of the water ice is destroyed) or reset (all stream lines where $\gtrsim 70$% of the water ice is destroyed). The V883 Ori datapoint coincides with the peak of the model prediction histogram for inheritance well within $1\sigma$, further supporting that the material in this disk is inherited.

The observed (/HDO) / (HDO/) ratio is consistent between Class 0 objects and the V883 Ori disk and are all a factor of $\sim 40-140$ higher than the most likely value of $\sim 5\times 10^{-2}$ in the case the material is reset (see Extended Data Figure 9). The (/HDO) / (HDO/) ratio predicted in for inheritance is 10, which is a factor up to $\sim 5$ higher than that observed. Nonetheless, in contrast to the values for reset, the initial (/HDO) / (HDO/) can vary between $\sim 0.8$ and $\sim 19$ due to variations in the initial conditions of the models (see the Supplementary Information for details). The similarity in the observed ratio between the V883 Ori disk and the Class 0 objects strongly suggests that material is inherited.

As all three analyzed transitions lie at different frequencies of 316.7998 GHz (), 225.8967 GHz (HDO), and 203.4075 GHz (H$_2^{18}$O), frequency dependent radiative transfer effects could affect the observed / and the (/HDO) / (HDO/) ratios. In particular, the dust inside 40 au is optically thick absorbing the emission of COMs and other molecules whose emission partly originates at altitudes comparable to the optically thick layer of the continuum emission . As the continuum optical depth increases with frequency, more emission could be hidden than HDO and H$_2^{18}$O due to the higher frequency of the line. Therefore, if optically thick dust is affecting the lines differentially, the measured ratios will be driven further into the regime consistent with inheritance. Other systematics that could affect the measured / and (/HDO) / (HDO/) ratios such as a lower excitation temperature are discussed in Supplementary Sect. 3.

## Deuteration of complex organic molecules

The high abundance of with respect to in the V883 Ori disk demonstrates that water in this disk is likely inherited. This is further supported by the high gas-phase HDO/ ratio seen across protostellar envelopes, disks, and comets and the high HDO/ ratio seen in the ice in a single low mass protostar and two massive protostars . However, the abundance of , , , and compared to their main isotopologues is measured to be lower in the V883 Ori disk than in the younger hot corino IRAS 16296 B and the comet 67P. This lower level of deuteration in the V883 Ori disk has been interpreted as an indication for some reprocessing of COMs .

COMs are traditionally thought to form in CO rich ice but there are indications in the V883 Ori disk that COMs possibly partially formed in a water-rich ice matrix () . The contribution from COMs formed in the CO-rich ice matrix is expected to have a higher D/H ratio as deuteration is efficient at the temperature where CO freezes-out. The initial deuteration levels of these COMs likely follows the /HDO ratio as and HDO are formed at the same time. The levels of deuteration seen in a / ratio of $1.97 \times 10^{-2}$ and the low upper limits on the deuteration in , , , and of $\lesssim (5.7-20) \times 10^{-3}$ are consistent with the /HDO ratio of $(8.5 \pm 2.8) \times 10^{-3}$ in this disk. Yet, chemical reactions where H and D are exchanged or abstracted can alter the D/H ratio in COMs complicating the analysis . Even though COMs are likely to at least partially form in the CO-rich ice matrix, the contribution of COMs formed within the water ice matrix will have a low deuteration level due to the higher gas temperatures at the time of formation making deuteration inefficient.

## Summary

The inheritance of water from the ice on dust grains in the cloud before stars are born to the disk and subsequently to comets connects the major steps in the formation of planets as comets likely form from the same reservoir of material as the planets. Our result demonstrates that pristine water that formed at the earliest phases of star and planet formation is available in protoplanetary disks, a phase where potential hints of embedded planets are frequently seen in the form of e.g., dust substructures . Even though the journey of water from the disk to Earth is still debated and the deuteration in Earth’s oceans is lower than HDO/ ratio in the V883 Ori disk, , the deuteration of Earth’s oceans is enhanced compared to the ISM by an order of magnitude . In addition, the / ratio is similar across Class 0 objects, the V883 Ori disk, and a comet. Together with the enhanced deuteration seen in HDO across all these four phases, this suggests that the trail of inherited water does not stop at the cometary phase but potentially continues to the water present on exoplanets formed in water ice rich protoplanetary disks.

# Methods

## Self-calibration

We observed the V883 Ori disk in ALMA band 7 for 2.4 hours on source distributed over three execution blocks (EBs; Supplementary Data Table 1; 2023.1.00588.S; PI: M. Leemker). These data targeted the $1_{1,0} -1_{0,1}$ transition at 316.7998 GHz at a spectral resolution of 61 kHz (58 m s$^{-1}$) and a total bandwidth of 117.2 MHz. A continuum spectral window covering 1.875 GHz of bandwidth at a spectral resolution of 1.1 km s$^{-1}$ was centered at 315 GHz. In addition, 6 spectral windows centered at the $N=3-2$, $J=5/2-3/2$, $F_1=2-1$, $F=3-2$ (325.943 GHz), $13_{0,0}-12_{0,0}$ (326.556 GHz), $13_{-1,2}-12_{1,2}$ (326.685 GHz), $18_{1,18}-17_{0,17}$ EE (326.931 GHz), $22_{1,21}-22{0,22}, J=45/2-45/2, F=43/2-43/2$ (328.097 GHz), and $22_{1,21}-22_{0,22}, J=45/2-45/2, F=47/2-47/2$ (328.131 GHz) transitions were included with a spectral resolution of 122 kHz ($\sim 130$ m s$^{-1}$) and a bandwidth of 58.6 MHz. Finally, the $10_{3,8}-9_{2,7}$ EE transition at 328.857 GHz was targeted at the same spectral resolution but a bandwidth of 117.2 MHz.

The data were self-calibrated using CASA version 6.5.4 following the analysis used in the exoALMA large program outlined in , with several routines by . A pseudo-continuum Measurement Set was created for each EB after carefully flagging all spectral regions exhibiting line emission, and then averaging all the data in individual channels for each spectral window. Since this is a very line-rich disk, the total continuum bandwidth used for the self-calibration is reduced to 180 MHz. Before aligning and then combining the three EBs, one round of phase self-calibration over a solution interval equal to the length of a single EB (1 hour and 19 minutes) was performed combining all scans, and both polarizations. A `CLEAN` model was used for the self-calibration, as constructed over an elliptical mask of $0\ensuremath{\overset{\prime\prime}{.}}6$ in semi-major axis, and a Position Angle (PA) and semi-minor axis computed from the PA and inclination of the V883 disk of 32$\degree$ and 38.3$\degree$, respectively . We employed Briggs weighting with `robust`$=0.5$. The model was created by cleaning the emission in all line-free channels down to a conservative threshold of $6\sigma$. The peak signal-to-noise ratio in the images of the individual EBs improved between 76 and 160%. The continuum observed in the third EB had the highest signal to noise ratio of all EBs and therefore was used as a reference for the alignment where the phase angle and the amplitude differences are minimized between the first EBs and the third EB .

After combining all execution blocks, seven rounds of phase-only self-calibration were performed with solution intervals with the length of a single EB, 360, 120, 60, 20, 10, and 6 seconds. The imaging followed the same mask and weighting as for the individual EBs before concatenation. In the first round of phase self-calibration, separate solutions were found for both polarizations, whereas in all subsequent rounds a single solution was obtained for both polarizations. In addition, all scans were combined during the first three rounds as the solution interval exceeded the scan length.

Comparing the amplitude of the continuum visibilities between the three execution blocks showed that the data taken on December 24th 2023 had an 8.6% higher amplitude across all baselines up to 600 k$\lambda$ where the signal-to-noise ratio drops compared to the execution block with the highest signal-to-noise-ratio. Therefore, we rescaled the flux before self-calibration in this execution block and concatenated this to the data of the other two EBs before self-calibration. Subsequently, these concatenated data were self-calibrated with seven rounds of phase-only self-calibration and a single round of phase and amplitude self-calibration with separate solutions for both polarizations and a solution interval of the length of a single EB. The model for the amplitude self-calibration was created by cleaning the line-free channels down to a $1\sigma$ threshold to capture as much emission as possible in the model. Solutions deviating by more than $\sim$20% in amplitude were flagged. The phase self-calibration improved the peak signal-to-noise ratio of the data by a factor of 186%, from a peak signal-to-noise ratio of 495 to one of 1457. The amplitude and phase self-calibration improved the peak signal-to-noise ratio by 3% (see Supplementary Figure 1 for the final continuum image). The peak continuum intensity increases by 15% after phase-only self-calibration due to the improved phase coherence after phase-only self-calibration. The peak continuum intensity changes by less than 0.5% after phase and amplitude self-calibration. The solutions were then applied to the full dataset, following the same logical order as for the pseudo continuum Measurement Set.

## Continuum subtraction

As many lines of COMs are detected in this dataset, too few line-free channels were available to subtract the continuum emission in the $uv$-plane using the standard CASA task `uvcontsub`. Instead, the continuum in the spectral window was subtracted in each EB separately. First, a mtmfs image up to and including first order (`nterms` $=2$) was created using the line free channels in the spectral window. The resulting model for the continuum emission was added to the measurement set using `ft`. This model was then used to subtract the continuum using the CASA task `uvsub`. The resulting MS tables for all three EBs were then combined to make the final continuum subtracted dataset for .

## Imaging

The line itself was imaged using the CASA task `tclean` with Briggs weighting and a `robust` parameter of 0, which provides the best balance between spatial resolution and noise, resulting in a $0\ensuremath{\overset{\prime\prime}{.}}24 \times 0\ensuremath{\overset{\prime\prime}{.}}19\ (89\degree)$ beam. The spectrum around the emission is presented in Extended Data Figure 1 and the channel maps are presented in Figure [2](#fig:D2O_channel_maps_cf_HDO). The relatively small beam allows for better deblending of the lines while still detecting the line. The image is cleaned down to $1\sigma$ to capture all the flux in the model and make the final measurement independent of any non-Gaussian features in the beam at the cost of potential imaging artifacts . The channel spacing for the final image is 400 m s$^{-1}$ to match that of the HDO and H$_2^{18}$O data. The resulting cubes are used to produce channel maps and measure the flux using a Keplerian mask. Only when the data cubes are shifted with the projected Keplerian velocity associated to each pixel, the native spectral resolution of the data of 58, 162, and 180 m s$^{-1}$ for , HDO, and H$_2^{18}$O, respectively, is used to minimize artifacts due to the finite spectral resolution of the data.

To accurately measure the (/HDO) / (HDO/) and / ratio in this disk, we re-imaged the HDO and H$_2^{18}$O data presented in (2021.1.00186.S; PI: J. J. Tobin). In this work, these data are cleaned down to $1\sigma$, similar to the line, and allow for a uniform analysis of the line fluxes and migitate any effects of the non-Gaussian beam shape on the measured line flux . The resulting beam sizes are $0\ensuremath{\overset{\prime\prime}{.}}13\times  0\ensuremath{\overset{\prime\prime}{.}}11 (-72\degree)$ and $0\ensuremath{\overset{\prime\prime}{.}}10\times 0\ensuremath{\overset{\prime\prime}{.}}08 (-78\degree)$ for the H$_2^{18}$O and the HDO when cleaned with a `robust` parameter of 1.0 and 2.0, respectively, to provide the best balance between the signal-to-noise ratio and a small beam to separate the lines from neighbouring COMs. The resulting channel maps for HDO and H$_2^{18}$O are presented in Extended Data Figure 3 and Extended Data Figure 4, respectively.

## Flux measurements

The transitions of all three water isotopologues discussed in this paper are blended with lines from neighboring COMs. To separate these lines and accurately measure the line flux, two methods are employed: Keplerian masking in the channel maps and spectral shifting of the spectrum. In the former case, the lines are separated in the image plane by computing the region in Right Ascension and Declination where a molecule is expected to emit based on the Keplerian rotation of the disk and its orientation on the sky. As this region shifts for each velocity channel, lines of neighbouring COMs can be separated from the water isotopologue emission. The Keplerian masks are constructed using the package by following using a distance of 400 pc , a stellar mass of 1.3 M$_{\odot}$, a disk inclination of 38.3$\degree$, and a position angle of 32$\degree$ and an emitting region extending from 40 au to 120 au tracing $z/r=0.4$. The line width is assumed to follow 350 m s$^{-1} \times \sqrt{40~\mathrm{au}/r}$ and the mask is shifted by 4.3 km s$^{-1}$ to match the systemic velocity of V883 Ori . These parameters are identical between all three analyzed water isotopologues. Finally, the mask is convolved with a Gaussian 0.5 (), 1.25 (HDO), and 0.75 (H$_2^{18}$O) times larger than the beam of the respective observations. This parameter is chosen after visual inspection of the data. The factor varies slightly from line to line to match the spatial extent of the emission observed in the channel maps and to match the spatial resolution of the resulting masks to have a $\sim 0.1-0.12"$ major axis and a $0.08-0.1"$ minor axis across all lines. The effect of neighboring COMs is investigated using an identical mask but then shifted to the frequency of those lines.

In general the emission of the , HDO 225 GHz, and the H$_2^{18}$O transition can be well separated in most channels using this method. To measure the disk integrated flux, only the channels between 1.2 and 6.4 km s$^{-1}$ are used as only in these channels the water emission can be separated from the COMs for all three isotopologues. The uncertainties on the disk integrated line fluxes are estimated as the rms of the flux measured in masks shifted to eight different positions $1\ensuremath{\overset{\prime\prime}{.}}4$ from the original location and to five different velocities resulting in 40 unique, non-overlapping locations. The HDO 241 GHz line on the other hand is too severely blended and is therefore not considered in this analysis.

The second method to deblend the lines is through spectral shifting. Similar to the Keplerian masking, this method utilizes the Keplerian rotation of the disk. Each pixel is shifted to correct for the projected Keplerian velocity expected at this location in the disk. The lines in the spectrum extracted from such a shifted cube are much narrower and single peaked than the double peaked line profiles in the non-shifted cube. As the lines are only seen over a small radial range, the emission is assumed to be originating from the disk midplane.

The resulting line profiles are not necessarily Gaussian. Therefore, the line profile of each COM is reconstructed from the data directly, see Extended Data Figures 5, 6, and 7. The non-blended side of COM emission line is mirrored in the line center creating a symmetric line profile that is then subtracted from the shifted spectrum. This procedure is repeated for all bright lines of COMs around the water lines. The and H$_2^{18}$O line were still blended by some remaining COM emission. Therefore, a spectral template for the and H$_2^{18}$O themselves were created using the clean side of the line after the COM emission was subtracted (see the cyan line in the bottom panel of Extended Data Figures 5 and 7). For the H$_2^{18}$O, the contribution of the contaminating shoulder is negligible at $<1\sigma$, whereas for the the contributed 8 mJy km s$^{-1}$ to the total flux. The region used to create the line profile of the COMs is indicated with the blue shaded region and that used to measure the water isotopologue line flux is indicated in red.

Extended Data Figure 8 presents a spectrum of the H$_2^{18}$O line but then extracted from a somewhat smaller region of $0\ensuremath{\overset{\prime\prime}{.}}35 \times 0\ensuremath{\overset{\prime\prime}{.}}27$ (semi-axes). The noise is estimated from 720 independent spectra covering a 19" region in the image plane while excluding the central $2\ensuremath{\overset{\prime\prime}{.}}1$ square in the non-primary beam corrected cube. As less noise is added to this spectrum than in Extended Data Figure 7, it clearly shows an emission peak at the expected frequency for the H$_2^{18}$O line, showing that this line is detected in this dataset. This spectrum is not used for any of calculations to avoid a bias due to the smaller region used to extract this spectrum compared to that of the and HDO lines.

An overview of the measured fluxes is presented in Table [2](#tab:fluxes), where for the and H$_2^{18}$O emission, we report the flux measured by the spectral template centered on those lines to account for the remaining shoulder of COM emission in the spectrum. The reported uncertainties on the line fluxes do include the statistical uncertainty but not the 5% absolute flux calibration uncertainty for ALMA Band 5 and 6 (HDO and H$_2^{18}$O) and 10% for ALMA Band 7 (). The absolute flux calibration uncertainty is included for all line ratios together with the uncertainty on the / ratio of $560 \pm 25$ in the ISM . The uncertainty on the / ratio in the ISM is negligible for the resulting column density and water isotopologue ratios.

The two methods to measure the line fluxes are consistent within $\leq 3\sigma$ for all three water isotopologues. This difference stems from the limited velocity range used for the Keplerian masking method. In this case only the channels between 1.2 and 6.4 km s$^{-1}$ are used as all three water isotopologues can be separated from the neighbouring COMs in these channels, whereas emission in some isotopologues is seen up to 0.8 and 8.4 km s$^{-1}$. As some flux from the inner disk region may be lost due to the spectral shifting of the data as a result of beam smearing and the main goal of this work is to obtain ratios of water isotoplogues, the fluxes measured using the Keplerian masks are used for the final analysis presented in the main text.

## Column density estimates

In order to compute the ratios of water isotopologues, their line fluxes need to be converted to column densities using the properties of the emission lines listed in Table [1](#tab:CDMS_JPL). In this work, optically thin emission and local thermodynamical equilibrium (LTE) are assumed for this conversion. These assumptions are further discussed in Supplementary Sect. 3.2 and 3.4, respectively. The column density of the upper energy level can be determined without any knowledge on the rotational temperature : $$\begin{align}
    N_u = \frac{4\pi F_{\nu}\Delta V}{A_{ul}\Omega hc},
\end{align}$$ with $\int F_{\nu} dV \approx F_{\nu}\Delta V$ the integrated flux, $A_{ul}$ the Einstein-A coefficient of the transition, $\Omega$ the emitting region in steradian, $h$ the Planck constant, and $c$ the speed of light. The water snowline, the midplane region where water sublimates is possibly at 40 au but most likely around $75-120$ au based on gas-phase measurements , , , . In addition, gas-phase water traced by HDO and H$_2^{18}$O is seen out to 160 au ($0\ensuremath{\overset{\prime\prime}{.}}4$) and as the spatial distribution of the , HDO, and H$_2^{18}$O water isotopologues is similar (see Figure [2](#fig:D2O_channel_maps_cf_HDO), Extended Data Figures 2, 3, and 4) an elliptical emitting region with that radius is used. The minor axis of this elliptical region is set to $0\ensuremath{\overset{\prime\prime}{.}}4 \times \cos(i) = 0\ensuremath{\overset{\prime\prime}{.}}31$, with $i$ the disk inclination to trace a circular region with a radius of 160 au in the disk frame.

The column density of the upper energy level is then converted to the total column density using the partition function $Q$ at the rotational temperature $T_{\rm rot}$ and the degeneracy $g_u$ and the upper energy level $E_u$ of the line: $$\begin{align}
    N_{\rm tot} = \frac{N_u Q(T_{\rm rot})}{g_u}\exp{\left (\frac{E_u}{k_{\rm B}T_{\rm rot}} \right )},
\end{align}$$ with $k_{\rm B}$ the Boltzmann constant. If multiple lines of the same molecule are observed, this equation can be solved for each line to find the excitation temperature of the molecule. In this work, the excitation temperature derived by from two HDO transitions with different upper energy levels is used for all analyzed lines as these water isotopologues emit from the same disk region.

For the and H$_2^{18}$O molecules that contain two deuterium or two hydrogen atoms, the molecules can be either in an ortho or in a para-state. The transitions used in this work are both para-states. The column density of and p-H$_2^{18}$O are converted to the total column density using a thermalized ortho-to-para ratio of 2 and 3, respectively . A summary of the derived column densities are presented in Table [3](#tab:N).

# Declarations

## Data availability

The ALMA data from ALMA programs #2021.1.00186.S and #2023.1.00588.S are publicly available on the ALMA archive on the ALMA archive at <https://almascience.eso.org/aq/>.

## Code availability

The code used for this work is based on publicly available python packages. In addition, the code itself is available upon reasonable request to M.L..

## Acknowledgements

We would like to thank the referees for the constructive comments. M.L. would like to thank Ewine van Dishoeck, Milou Temmink, and Shota Notsu for the useful discussions and acknowledges assistance from Allegro, the European ALMA Regional Center node in the Netherlands. M.L. and S.F. are funded by the European Union (ERC, UNVEIL, 101076613). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them. S.F. acknowledges financial contribution from PRIN-MUR 2022YP5ACE. P.C. acknowledges support by the ANID BASAL project FB210003. A.S.B. is supported by a Clay Postdoctoral Fellowship from the Smithsonian Astrophysical Observatory. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00186.S and #2023.1.00588.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory and Green Bank Observatory are facilities of the U.S. National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

## Author contributions

M.L. wrote the majority of the text of the manuscript and analyzed the data. M.L., P.C., J.J.T., and S.F. self-calibrated and imaged the ALMA data that was obtained by proposals led by M.L. and J.J.T. All co-authors provided input on the manuscript.

## Competing interests

The authors declare no competing interests.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | frequency | $\log(A_{ul})$ | $E_u$ | $g_u$ | $Q$ | $Q$ | $Q$ |
|  |  | (GHz) | $(\mathrm{s^{-1}})$ | \(K\) |  | 300 K | 150 K | 75 K |
|  | $1_{1,0}-1_{0,1}$ | 316.79981 | -3.20 | 32.6 | 3 | 349.6 | 123.7 | 44.4 |
| HDO | $3_{1,2}-2_{2,1}$ | 225.89672 | -4.88 | 167.6 | 7 | 146.9 | 52.3 | 18.9 |
| H$_2^{18}$O | $3_{1,3}-2_{2,0}$ | 203.40752 | -5.31 | 203.7 | 7 | 179.6 | 64.2 | 23.4 |
|  |  |  |  |  |  |  |  |  |

: Properties of the transitions analyzed in this work.

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Molecule | Transition | Line flux (mJy km s$^{-1}$) | Line flux (mJy km s$^{-1}$) |
|  |  | Keplerian mask | Shifted spectrum |
|  | $1_{1,0}-1_{0,1}$ | $53 \pm 4$ | $61 \pm 4$ |
| HDO | $3_{1,2}-2_{2,1}$ | $358 \pm 14$ | $408 \pm 12$ |
| H$_2^{18}$O | $3_{1,3}-2_{2,0}$ | $43 \pm 9$ | $58 \pm 10$ |
|  |  |  |  |

: Disk integrated line fluxes excluding emission from neighboring complex organics.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Method | $N$() | $N$(HDO) | $N$(H$_2^{18}$O) | / | /HDO | $\frac{\mathrm{D_2O/HDO}}{\mathrm{HDO/H_2O}}$ |
|  | ($10^{13}$ cm$^{-2}$) | ($10^{14}$ cm$^{-2}$) | ($10^{14}$ cm$^{-2}$) | ($\times 10^{-5}$) | $(\times 10^{-3})$ |  |
| Keplerian mask | $4.2 \pm 1.2$ | $49.5 \pm 6.9$ | $23.7 \pm 5.7$ | $3.2 \pm 1.2$ | $8.5 \pm 2.8$ | $2.3 \pm 1.0$ |
| Shifted spectrum | $4.9 \pm 1.4$ | $56.4 \pm 7.7$ | $32.3 \pm 6.3$ | $2.7 \pm 1.0$ | $8.6 \pm 2.8$ | $2.8 \pm 1.1$ |
|  |  |  |  |  |  |  |

: Column densities and column density ratios of water isotopologues.

![](Leemker_fig1.pdf)

![](Leemker_Fig2.pdf)

![](Leemker_Fig3.pdf)

Correspondence and requests for materials should be addressed to Margot Leemker.

# Supplementary information

# Observational details

A full description of the self-calibration of the ALMA data can be found in the Methods section. The dates, number of antennas, configuration, and the bandpass, flux, and phase calibrators are summarized in Supplementary Table [4](#tab:EBs). In addition, the self-calibrated continuum emission of the V883 Ori disk is presented in Supplementary Figure [4](#fig:cont).

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Date | number of | min. baseline | max. baseline | bandpass & flux | phase |  |
|  | antennas | \(m\) | (km) | calibrator | calibrator |  |
| 24 Dec. 2023 | 43 | 15.1 | 1.2 | J0423-0120 | J0607-0834 |  |
| 28 Jul. 2024 | 45 | 15.1 | 1.4 | J0538-4405 | J0607-0834 |  |
| 30 Jul. 2024 | 47 | 15.1 | 1.4 | J0538-4405 | J0607-0834 |  |
|  |  |  |  |  |  |  |

: ALMA observations covering the line.

![](cont.pdf)

# Water isotopologue ratios

The (/HDO) / (HDO/) has been suggested as an indicator to distinguish inheritance from reset in addition to the / ratio . The HDO/ ratio is more accessible through observations than the (/HDO) / (HDO/) ratio as the former only requires observations of two water isotopologues. However, modeling of the ices in a two-dimensional collapsing core shows that the HDO/ ratio in the case of reset can be similar to or even higher than the inherited value due to reformation of HDO ice from deuterium rich fragments on the ice and non-equilibrium gas-phase chemistry whose deuterated products freeze-out .

To determine if water is inherited or reset, we follow a twofold argument. First of all, the water isotopologue ratios in the V883 Ori disk are compared to those in younger and older objects to look for similarity. Second, these ratios are compared to the model predictions by . Here, the most important uncertainties in the model predictions are discussed.

## Modelling uncertainties

The rotation of the envelope and number of chemically active monolayers in the chemical network typically only affect the water abundance by a factor of several . As the expected values for / and (/HDO) / (HDO/) between inheritance and reset generally differ by two orders of magnitude this is not expected to significantly affect the expected ratios.

The deuteration of water is only efficient at sufficiently low temperatures of $\lesssim 25$ K and densities above a few $10^4$ cm$^{-3}$ . Therefore, the deuteration will be more (less) extreme than modelled if the temperature in the V883 Ori system were lower (higher) and the density was higher than in the models by .

The abundance of HDO and in the case of inheritance can be further enhanced if the D/H in the gas increases at the time the water ice forms in the protostellar envelope or protoplanetary disk phase. This higher D/H in the gas only gets transferred to the water ice if the timescale for the gas-phase ion-neutral chemistry is faster than the timescale of the freeze-out of atomic oxygen. These timescales roughly match for a gas density of $10^4$ cm$^{-3}$ and a cosmic ray ionization rate of $10^{-17}$ s$^{-1}$ . Such low densities are unlikely at later evolutionary stages. For higher densities of $10^6$ cm$^{-3}$, the cosmic ray ionization rate needs to exceed $10^{-15}$ s$^{-1}$ to enhance the deuteration of water ice. As there are no indications for a cosmic ray ionization rate that is elevated by two orders of magnitude, an enhancement in the water deuteration in the protostellar envelope or protoplanetary disk phase of the V883 Ori system is not expected.

![](Water_iso_ratios_hist_HDOH2O.pdf)

## HDO/ ratio

Using the reimaged HDO and H$_2^{18}$O emission that was originally presented in , we derive the HDO/ ratio to be $(3.7 \pm 1.0)\times 10^{-3}$. This is consistent within 1.2$\sigma$ with that of $(2.3\pm 0.6) \times 10^{-3}$ derived in and their conclusions.

A summary of the observed HDO/ ratios across Class 0, the reanalyzed datapoint in the V883 Ori disk, and comets is presented in Supplementary Data Figure [5](#fig:inheritance_vs_reset_methods_HDOH2O) . Recently it was found that the D/H ratio in water in the comet 67 P is lower than originally thought at a value of $(2.59\pm 0.36) \times 10^{-4}$ (corresponding to HDO/ = $(5.18\pm 0.72) \times 10^{-4}$) due to the effect preferential adsorption of HDO on the dust grains . As the abundance has not been rederived taking the effect of the dust into account, we use previously derived HDO/ ratio of $(1.06 \pm 0.14) \times 10^{-3}$ for a consistent analysis across all water isotopologue ratios measured in this comet . Using the newly derived HDO/ ratio in the comet 67 P would increase the (/HDO)/(HDO/) ratio by a factor of 4 assuming that the does not preferentially adsorb on the dust grains like HDO. This does not change our conclusions. The color shading in the background of the left panel and the histogram on the right clearly demonstrate that the distributions of the expected HDO/ ratio overlap for inheritance and reset and thus that this ratio does not distinguish inheritance from reset despite the similarity in the HDO/ ratio across three evolutionary phases suggesting inheritance.

![](Water_iso_ratios_hist_D2OHDO.pdf)

## /HDO ratio

Another water isotopologue ratio is the /HDO ratio. This ratio in astronomical objects together with the model predictions by are presented in Supplementary Data Figure [6](#fig:inheritance_vs_reset_methods_D2OHDO). In case the material is inherited, the /HDO ratio is $\sim 2\times 10^{-2}$, whereas in case the material is reset, the /HDO ratio is $\sim 10^{-4}$, though high values up $\sim 1\times 10^{-2}$ are rare but still possible. The /HDO ratio in the V883 Ori disk is $(8.5 \pm 2.8) \times 10^{-3}$, much closer to the ratio expected for inheritance than for reset. In addition, this ratio is consistent within $1\sigma$ with that in the Class 0 sources L483 and NGC 1333 IRAS 2A, and with the comet 67 P and within $2\sigma$ of B335, the only other Class 0 source with an /HDO measurement. Therefore, the /HDO ratio in the V883 Ori disk is consistent with inheritance.

## (/HDO) / (HDO/) ratio

Similarly, the overlap between the (/HDO) / (HDO/) ratio for inheritance and reset is much less than that for the HDO/ ratio and therefore this is a better tracer than the HDO/ ratio . Model predictions show that the (/HDO) / (HDO/) ratio is $\sim 0.8-19$ if the material is inherited where the spread is due to e.g., variations in the initial ortho-to-para ratio of , the abundances at the time at the time the prestellar core forms, and lifetime of the prestellar core before collapse . In the collapsing core models by the initial (/HDO) / (HDO/) ratio is 10. If material is reset, the expected value is $\sim 5 \times 10^{-2}$ and only few of the modeled stream lines predict a (/HDO) / (HDO/) above 1 in case of reprocessing (see Extended Data Figure 9) .

The observations of the (/HDO) / (HDO/) ratio in the V883 Ori disk together with those in younger Class 0 objects and the 67 P comet are presented in Extended Data Figure 9. All values are consistent with those for inheritance when variations in the initial conditions are considered . Only NGC 1333 IRAS 2A and 67 P are consistent with the model prediction for inheritance by within $1\sigma$. The two remaining Class 0 sources and the V883 Ori disk have a somewhat lower value of $\sim2-3$, possibly due to e.g., a different ortho-to-para ratio of and thus a different reservoir of chemical energy in the initial phases or due a different evolution of the early phases such as the time before the onset of collapse of the prestellar core and the visual extinction of the cloud when the initial conditions of the chemical network are initialized . The similarity in the observed (/HDO) / (HDO/) ratio across Class 0 objects and the V883 Ori disk, together with the spread in possible values for inheritance strongly suggests that ice is preserved from the earliest phases of star and planet formation.

# Systematic uncertainties

In addition to the effect of the continuum optical depth potentially leading to an underestimation of the water isotopologue ratios discussed in the main text, other systematic effects could affect the derived ratios.

## Excitation temperature

As only a single line of each water isotopologue is analyzed in this work, their measured column densities are derived using an assumed excitation temperature of $199\pm 42$ K derived from a rotational diagram analysis of two HDO lines by . As one HDO line at 241 GHz used in that analysis is severely blended with two COMs, the derived excitation temperature is somewhat uncertain. The temperature derived from these two HDO lines is higher than the typically assumed 120 K temperature for COMs in this disk based on their desorption temperature of $\sim 100$ K and lower than the excitation temperature of $343 \pm 102$ K for , the warmest COM seen in this disk . Supplementary Data Table [5](#tab:Tex) summarizes the effect of the assumed excitation temperature on the derived / and the (/HDO) / (HDO/) ratios by varying the temperature by $\pm 100$ K, the approximate range of temperatures found for COMs in this disk. These ratios increase with temperature, driving the results further into inheritance if the gas is warmer than assumed. Even if the gas were only 99 K, the / ratio would be fully consistent with inheritance of material. In addition, the (/HDO) / (HDO/) ratio at this temperature is consistent within $1\sigma$ with those in Class 0 objects tracing pristine material.

| $T_{\rm rot}$ (K) |               /               | (/HDO) / (HDO/) |
|:-----------------:|:-----------------------------:|:---------------:|
|        99         | $(1.3 \pm 0.8)\times 10^{-5}$ |  $1.4 \pm 0.9$  |
|        199        | $(3.2\pm 1.2)\times 10^{-5}$  |  $2.3 \pm 1.0$  |
|        299        | $(4.3\pm  1.4)\times 10^{-5}$ |  $2.7 \pm 1.0$  |
|                   |                               |                 |

: Effect of the excitation temperature on the / and the (/HDO) / (HDO/) ratios.

## Optical depth

The column densities of the water isotopologues are derived in the assumption of optically thin emission. The optical depth at the line center $\tau$ can be approximated as : $$\begin{align}
    \tau = \frac{A_{ul} c^3}{8\pi \nu^3 \Delta V}N_u \left (e^{h\nu / kT_{\rm rot}} -1 \right ) 
\end{align}$$ with $\nu$ the frequency of the line and $\Delta V$ the thermal linewidth. This expression approximates the peak of the normalized line profile as $1/\Delta V$ which is very close to that for a Gaussian line profile $2\sqrt{\ln{2}}/(\sqrt{\pi} \Delta V)$. The thermal linewidth is defined as: $$\begin{equation}
    
    \Delta V = \sqrt{\frac{8kT_{\rm rot} \ln 2 }{m}}      
\end{equation}$$ with $m$ the mass of the molecule. For all three water isotopologues, this results in an FWHM linewidth of $\sim 0.7$ km s$^{-1}$ at a temperature of $199$ K. This is slightly narrower than the line width in the shifted spectra because the finite resolution of the data and possible differences in the true emitting geometry set by the stellar mass, inclination, position angle, and assumed emitting height. An overview of the optical depth estimates is presented in Supplementary Data Table [6](#tab:tau).

For the fiducial temperature of 199 K, the thermal linewidth and derived column densities of the upper energy levels, all lines analyzed in this work are optically thin. The HDO line has the highest optical depth at 0.14, which results in a 7% correction factor on the column density using the optical depth correction factor $\tau / (1-e^{-\tau})$ . At a lower temperature of 99 K, the HDO line has an optical depth of 0.54 which leads to a correction factor of 29% on the HDO column density. This lowers the (/HDO) / (HDO/) ratio to 1.5 which is at the boundary of 1 between inheritance and reset. At a higher temperature of 299 K, all lines are fully optically thin. The best tracer to distinguish inheritance from reset used in this work, the / ratio, is not affected by the optical depth of HDO. Therefore, the observed and H$_2^{18}$O emission remain consistent with the inheritance scenario even if the temperature is different from $199 \pm 42$ K.

Finally, the effect of the assumed emitting region for the emission is summarized in the final column of Supplementary Data Table [6](#tab:tau). The fiducial region of $0\ensuremath{\overset{\prime\prime}{.}}4$ radius in the frame of the disk is motivated by the HDO and H$_2^{18}$O emission that is seen out to that distance . As the midplane water snowline is located at $\sim$80 au ($0\ensuremath{\overset{\prime\prime}{.}}2$) indicated by the steep drop off in the HDO and H$_2^{18}$O column densities, the smallest physically motivated emitting region is an elliptical annulus between $0\ensuremath{\overset{\prime\prime}{.}}1$ and $0\ensuremath{\overset{\prime\prime}{.}}2$. The inner boundary is set by the optically thick dust that hides the line emission out to 40 au ($0\ensuremath{\overset{\prime\prime}{.}}1$).

The area of the annulus is a factor of 5.3 smaller than the fiducial region, increasing the derived column densities by that same factor. As all column densities change by that factor under the assumption of optically thin emission, the derived line ratios remain unaffected. The optical depths of the water isotopologue lines on the other hand increases by a factor of 5.3. For this small emitting region, the HDO emission becomes optically thick with an optical depth of $9.8\times 10^{-1}$, making the water isotopologue ratios involving HDO hard to interpret as they are very sensitive to the precise optical depth and because the HDO possibly emits from a higher layer in the disk than the and H$_2^{18}$O. The and H$_2^{18}$O on the other hand remain approximately optically thin with optical depths of $7.6\times 10^{-2}$ and $1.5\times 10^{-1}$, respectively. Therefore, even in this case the / ratio can be used to infer that water is inherited.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| molecule | $\tau$ | $\tau$ | $\tau$ | $\tau$ |
|  | $T_{\rm rot}= 199$ K (fid.) | $T_{\rm rot}= 99$ K | $T_{\rm rot}= 299$ K | $T_{\rm rot}= 199$ K & |
|  |  |  |  | small emitting region |
|  | $1.4\times 10^{-2}$ | $4.2\times 10^{-2}$ | $7.6\times 10^{-3}$ | $7.6\times 10^{-2}$ |
| HDO | $1.8\times 10^{-1}$ | $5.4\times 10^{-1}$ | $9.9\times 10^{-2}$ | $9.8\times 10^{-1}$ |
| H$_2^{18}$O | $2.8\times 10^{-2}$ | $8.0\times 10^{-2}$ | $1.5\times 10^{-2}$ | $1.5\times 10^{-1}$ |
|  |  |  |  |  |

: Optical depth of the lines analyzed in this work.

## Ortho-to-para ratios

The and H$_2^{18}$O molecules both have ortho and para states due to the presence of two deuterium and two hydrogen atoms, respectively. Observations of in the IRAS 16293-2422 cold protostellar envelope show that the observed value is consistent with the statistical value of 2 . In addition, observations of the main water isotopologue show a similar trend with most observations being consistent with the statistical value of 3 . If the true ortho-to-para ratio (OPR) is different than the assumed statistical then the column density derived is scaled by a factor of $\rm (1+OPR)/3$ and $\rm (1+OPR)/4$, respectively. If the OPR is at a low value of 1 for both molecules, then the derived / increases to $(4.2\pm 1.6)\times 10^{-5}$ and (/HDO) / (HDO/) ratio decreases to $0.8 \pm 0.3$. Even in this case, the / ratio remains consistent with inheritance.

## Masing

The column densities of the water isotopologues are derived under the assumption of LTE. However, a recent analysis by showed that the HDO 225 GHz and the H$_2^{18}$O lines are possibly weakly masing in a large region in the V883 Ori disk. At the moment, detailed calculations of the masing conditions of the line are not reported. Still, the critical density for transitions of a non-linear, polyatomic molecule like the $1_{1,0}-1_{0,1}$ transition at 200 K is $9.9 \times 10^{5}$ cm$^{-3}$ using the collisional rate coefficients by . This is much lower than the expected densities in the V883 Ori disk. Therefore, the $1_{1,0}-1_{0,1}$ line is expected to be in LTE.

If the HDO and H$_2^{18}$O lines are indeed weakly masing as suggested by , their column densities are overestimated due to the assumption of LTE for the rotational diagram analysis. In addition, the relation between column density and observed flux becomes highly sensitive to the local conditions. Therefore, the (/HDO) / (HDO/) is not a meaningful measure in this case. However, the / ratio can still be used as the potential masing of the H$_2^{18}$O line only drives this ratio further into the inheritance regime whereas the line is expected to be in LTE.

# Extended Data

![](Leemker_ED_Fig1.jpg)

![](Leemker_ED_Fig2.jpg)

![](Leemker_ED_Fig3.jpg)

![](Leemker_ED_Fig4.jpg)

![](Leemker_ED_Fig5.jpg)

![](Leemker_ED_Fig6.jpg)

![](Leemker_ED_Fig7.jpg)

![](Leemker_ED_Fig8.jpg)

![](Leemker_ED_Fig9.jpg)

10

(ref: OBrien2018) David P. O’Brien, Andre Izidoro, Seth A. Jacobson, Sean N. Raymond, and David C. Rubie. . , 214(1):47, February 2018.

(ref: Cleeves2014) L. Ilsedore Cleeves, Edwin A. Bergin, Conel M. O. ’D. Alexander, Fujun Du, Dawn Graninger, Karin I. Öberg, and Tim J. Harries. . , 345(6204):1590–1593, September 2014.

(ref: Hogerheijde2011) Michiel R. Hogerheijde, Edwin A. Bergin, Christian Brinch, L. Ilsedore Cleeves, Jeffrey K. J. Fogel, Geoffrey A. Blake, Carsten Dominik, Dariusz C. Lis, Gary Melnick, David Neufeld, Olja Panić, John C. Pearson, Lars Kristensen, Umut A. Yıldız, and Ewine F. van Dishoeck. . , 334(6054):338, October 2011.

(ref: Persson2016) M. V. Persson, D. Harsono, J. J. Tobin, E. F. van Dishoeck, J. K. Jørgensen, N. Murillo, and S. P. Lai. . , 590:A33, May 2016.

(ref: Du2017) Fujun Du, Edwin Anthony Bergin, Michiel Hogerheijde, Ewine F. van Dishoeck, Geoff Blake, Simon Bruderer, Ilse Cleeves, Carsten Dominik, Davide Fedele, Dariusz C. Lis, Gary Melnick, David Neufeld, John Pearson, and Umut Yıldız. . , 842(2):98, June 2017.

(ref: Notsu2019) Shota Notsu, Eiji Akiyama, Alice Booth, Hideko Nomura, Catherine Walsh, Tomoya Hirota, Mitsuhiko Honda, Takashi Tsukagoshi, and T. J. Millar. . , 875(2):96, April 2019.

(ref: Harsono2020) D. Harsono, M. V. Persson, A. Ramos, N. M. Murillo, L. T. Maud, M. R. Hogerheijde, A. D. Bosman, L. E. Kristensen, J. K. Jørgensen, E. A. Bergin, R. Visser, J. C. Mottram, and E. F. van Dishoeck. . , 636:A26, April 2020.

(ref: vanDishoeck2021) E. F. van Dishoeck, L. E. Kristensen, J. C. Mottram, A. O. Benz, E. A. Bergin, P. Caselli, F. Herpin, M. R. Hogerheijde, D. Johnstone, R. Liseau, B. Nisini, M. Tafalla, F. F. S. van der Tak, F. Wyrowski, A. Baudry, M. Benedettini, P. Bjerkeli, G. A. Blake, J. Braine, S. Bruderer, S. Cabrit, J. Cernicharo, Y. Choi, A. Coutens, Th. de Graauw, C. Dominik, D. Fedele, M. Fich, A. Fuente, K. Furuya, J. R. Goicoechea, D. Harsono, F. P. Helmich, G. J. Herczeg, T. Jacq, A. Karska, M. Kaufman, E. Keto, T. Lamberts, B. Larsson, S. Leurini, D. C. Lis, G. Melnick, D. Neufeld, L. Pagani, M. Persson, R. Shipman, V. Taquet, T. A. van Kempen, C. Walsh, S. F. Wampfler, U. Yıldız, and WISH Team. . , 648:A24, April 2021.

(ref: Watanabe2002) Naoki Watanabe and Akira Kouchi. . , 571(2):L173–L176, June 2002.

(ref: Garrod2006) Robin Garrod, In Hee Park, Paola Caselli, and Eric Herbst. . , 133:51, January 2006.

(ref: Potapov2021) Alexey Potapov, Serge A. Krasnokutski, Cornelia Jäger, and Thomas Henning. . , 920(2):111, October 2021.

(ref: Linsky2003) Jeffrey L. Linsky. . , 106(1):49–60, April 2003.

(ref: Watson1976) William D. Watson. . , 48(4):513–552, October 1976.

(ref: Ceccarelli2014) C. Ceccarelli, P. Caselli, D. Bockelée-Morvan, O. Mousis, S. Pizzarello, F. Robert, and D. Semenov. . In *Protostars and Planets VI*, page 859, January 2014.

(ref: Owen2015) James E. Owen and Emmanuel Jacquet. . , 446(4):3285–3296, February 2015.

(ref: Furuya2016) K. Furuya, E. F. van Dishoeck, and Y. Aikawa. . , 586:A127, February 2016.

(ref: Furuya2017) K. Furuya, M. N. Drozdovskaya, R. Visser, E. F. van Dishoeck, C. Walsh, D. Harsono, U. Hincelin, and V. Taquet. . , 599:A40, March 2017.

(ref: Tobin2023) John J. Tobin, Merel L. R. van’t Hoff, Margot Leemker, Ewine F. van Dishoeck, Teresa Paneque-Carreño, Kenji Furuya, Daniel Harsono, Magnus V. Persson, L. Ilsedore Cleeves, Patrick D. Sheehan, and Lucas Cieza. . , 615(7951):227–230, March 2023.

(ref: Slavicinska2024) Katerina Slavicinska, Ewine F. van Dishoeck, Łukasz Tychoniec, Pooneh Nazari, Adam E. Rubinstein, Robert Gutermuth, Himanshu Tyagi, Yuan Chen, Nashanty G. C. Brunken, Will R. M. Rocha, P. Manoj, Mayank Narang, S. Thomas Megeath, Yao-Lun Yang, Leslie W. Looney, John J. Tobin, Henrik Beuther, Tyler L. Bourke, Harold Linnartz, Samuel Federman, Dan M. Watson, and Hendrik Linz. . , 688:A29, August 2024.

(ref: Chiang2001) E. I. Chiang, M. K. Joung, M. J. Creech-Eakman, C. Qi, J. E. Kessler, G. A. Blake, and E. F. van Dishoeck. . , 547(2):1077–1089, February 2001.

(ref: Sturm2023) J. A. Sturm, M. K. McClure, T. L. Beck, D. Harsono, J. B. Bergner, E. Dartois, A. C. A. Boogert, J. E. Chiar, M. A. Cordiner, M. N. Drozdovskaya, S. Ioppolo, C. J. Law, H. Linnartz, D. C. Lis, G. J. Melnick, B. A. McGuire, J. A. Noble, K. I. Öberg, M. E. Palumbo, Y. J. Pendleton, G. Perotti, K. M. Pontoppidan, D. Qasim, W. R. M. Rocha, H. Terada, R. G. Urso, and E. F. van Dishoeck. . , 679:A138, November 2023.

(ref: Booth2021HD100) Alice S. Booth, Catherine Walsh, Jeroen Terwisscha van Scheltinga, Ewine F. van Dishoeck, John D. Ilee, Michiel R. Hogerheijde, Mihkel Kama, and Hideko Nomura. . , 5:684–690, January 2021.

(ref: vanderMarel2021_IRS48) Nienke van der Marel, Alice S. Booth, Margot Leemker, Ewine F. van Dishoeck, and Satoshi Ohashi. . , 651:L5, July 2021.

(ref: Booth2023) Alice S. Booth, Charles J. Law, Milou Temmink, Margot Leemker, and Enrique Macı́as. . , 678:A146, October 2023.

(ref: Leemker2023) M. Leemker, A. S. Booth, E. F. van Dishoeck, N. van der Marel, B. Tabone, N. F. W. Ligterink, N. G. C. Brunken, and M. R. Hogerheijde. . , 673:A7, May 2023.

(ref: Leemker2024) M. Leemker, A. S. Booth, E. F. van Dishoeck, L. Wölfer, and B. Dent. . , 687:A299, July 2024.

(ref: Geppert2006) W. D. Geppert, M. Hamberg, R. D. Thomas, F. Österdahl, F. Hellberg, V. Zhaunerchyk, A. Ehlerding, T. J. Millar, H. Roberts, J. Semaniak, M. Af Ugglas, A. Källberg, A. Simonsson, M. Kaminska, and M. Larsson. . , 133:177, January 2006.

(ref: Yamato2024) Yoshihide Yamato, Shota Notsu, Yuri Aikawa, Yuki Okoda, Hideko Nomura, and Nami Sakai. . , 167(2):66, February 2024.

(ref: Minissale2022) Marco Minissale, Yuri Aikawa, Edwin Bergin, Mathieu Bertin, Wendy A. Brown, Stephanie Cazaux, Steven B. Charnley, Audrey Coutens, Herma M. Cuppen, Victoria Guzman, Harold Linnartz, Martin R. S. McCoustra, Albert Rimola, Johanna G. M. Schrauwen, Celine Toubin, Piero Ugliengo, Naoki Watanabe, Valentine Wakelam, and Francois Dulieu. . , 6(3):597–630, March 2022.

(ref: Kounkel2017) Marina Kounkel, Lee Hartmann, Laurent Loinard, Gisela N. Ortiz-León, Amy J. Mioduszewski, Luis F. Rodrı́guez, Sergio A. Dzib, Rosa M. Torres, Gerardo Pech, Phillip A. B. Galli, Juana L. Rivera, Andrew F. Boden, II Evans, Neal J., Cesar Briceño, and John J. Tobin. . , 834(2):142, January 2017.

(ref: Cieza2016) Lucas A. Cieza, Simon Casassus, John Tobin, Steven P. Bos, Jonathan P. Williams, Sebastian Perez, Zhaohuan Zhu, Claudio Caceres, Hector Canovas, Michael M. Dunham, Antonio Hales, Jose L. Prieto, David A. Principe, Matthias R. Schreiber, Dary Ruiz-Rodriguez, and Alice Zurlo. . , 535(7611):258–261, July 2016.

(ref: vantHoff2018) Merel L. R. van ’t Hoff, John J. Tobin, Leon Trapman, Daniel Harsono, Patrick D. Sheehan, William J. Fischer, S. Thomas Megeath, and Ewine F. van Dishoeck. . , 864(1):L23, September 2018.

(ref: Lee2019) Jeong-Eun Lee, Seokho Lee, Giseon Baek, Yuri Aikawa, Lucas Cieza, Sung-Yong Yoon, Gregory Herczeg, Doug Johnstone, and Simon Casassus. . , 3:314–319, February 2019.

(ref: Jensen2021b) S. S. Jensen, J. K. Jørgensen, L. E. Kristensen, A. Coutens, E. F. van Dishoeck, K. Furuya, D. Harsono, and M. V. Persson. . , 650:A172, June 2021.

(ref: Wilson1994) T. L. Wilson and R. Rood. . , 32:191–226, January 1994.

(ref: Facchini2024) Stefano Facchini, Leonardo Testi, Elizabeth Humphreys, Mathieu Vander Donckt, Andrea Isella, Ramon Wrzosek, Alain Baudry, Malcom D. Gray, Anita M. S. Richards, and Wouter Vlemmings. . , 8:587–595, May 2024.

(ref: Coutens2014) A. Coutens, J. K. Jørgensen, M. V. Persson, E. F. van Dishoeck, C. Vastel, and V. Taquet. . , 792(1):L5, September 2014.

(ref: Jensen2019) S. S. Jensen, J. K. Jørgensen, L. E. Kristensen, K. Furuya, A. Coutens, E. F. van Dishoeck, D. Harsono, and M. V. Persson. . , 631:A25, November 2019.

(ref: Altwegg2015) K. Altwegg, H. Balsiger, A. Bar-Nun, J. J. Berthelier, A. Bieler, P. Bochsler, C. Briois, U. Calmonte, M. Combi, J. De Keyser, P. Eberhardt, B. Fiethe, S. Fuselier, S. Gasc, T. I. Gombosi, K. C. Hansen, M. Hässig, A. Jäckel, E. Kopp, A. Korth, L. LeRoy, U. Mall, B. Marty, O. Mousis, E. Neefs, T. Owen, H. Rème, M. Rubin, T. Sémon, C. Y. Tzou, H. Waite, and P. Wurz. . , 347(6220):1261952, January 2015.

(ref: Altwegg2017) K. Altwegg, H. Balsiger, J. J. Berthelier, A. Bieler, U. Calmonte, J. De Keyser, B. Fiethe, S. A. Fuselier, S. Gasc, T. I. Gombosi, T. Owen, L. Le Roy, M. Rubin, T. Sémon, and C. Y. Tzou. . , 375(2097):20160253, May 2017.

(ref: Houge2024) Adrien Houge, Enrique Macı́as, and Sebastiaan Krijt. . , 527(4):9668–9682, February 2024.

(ref: Isella2016) Andrea Isella, Greta Guidi, Leonardo Testi, Shangfei Liu, Hui Li, Shengtai Li, Erik Weaver, Yann Boehler, John M. Carperter, Itziar De Gregorio-Monsalvo, Carlo F. Manara, Antonella Natta, Laura M. Pérez, Luca Ricci, Anneila Sargent, Marco Tazzari, and Neal Turner. . , 117(25):251101, December 2016.

(ref: Weaver2018) Erik Weaver, Andrea Isella, and Yann Boehler. . , 853(2):113, February 2018.

(ref: Slavicinska2025) Katerina Slavicinska, Łukasz Tychoniec, Marı́a Gabriela Navarro, Ewine F. van Dishoeck, John J. Tobin, Martijn L. van Gelder, Yuan Chen, A. C. Adwin Boogert, W. Blake Drechsler, Henrik Beuther, Alessio Caratti o Garatti, S. Thomas Megeath, Pamela Klaassen, Leslie W. Looney, Patrick J. Kavanagh, Nashanty G. C. Brunken, Patrick Sheehan, and William J. Fischer. . , 986(2):L19, June 2025.

(ref: Jeong2024) Jae-Hong Jeong, Jeong-Eun Lee, Seonjae Lee, Giseon Baek, Ji-Hyun Kang, Seokho Lee, Chul-Hwan Kim, Hyeong-Sik Yun, Yuri Aikawa, Gregory J. Herczeg, Doug Johnstone, and Lucas Cieza. . , 276(2):49, February 2025.

(ref: Taquet2012) V. Taquet, C. Ceccarelli, and C. Kahane. . , 748(1):L3, March 2012.

(ref: Bae2023) J. Bae, A. Isella, Z. Zhu, R. Martin, S. Okuzumi, and S. Suriano. . In S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, and M. Tamura, editors, *Protostars and Planets VII*, volume 534 of *Astronomical Society of the Pacific Conference Series*, page 423, July 2023.

(ref: Hagemann1970) R. Hagemann, G. Nief, and E. Roth. . , 22(6):712–715, December 1970.

(ref: DeLaeter2003) John R. de Laeter, John Karl Böhlke, P. De Bièvre, H. Hidaka, H. S. Peiser, K. J. R. Rosman, and P. D. P. Taylor. Atomic weights of the elements. review 2000 (iupac technical report). , 75(6):683–800, 2003.

(ref: McMullin2007) J. P. McMullin, B. Waters, D. Schiebel, W. Young, and K. Golap. . In R. A. Shaw, F. Hill, and D. J. Bell, editors, *Astronomical Data Analysis Software and Systems XVI*, volume 376 of *Astronomical Society of the Pacific Conference Series*, page 127, October 2007.

(ref: LoomisexoALMA) Ryan A. Loomis, Stefano Facchini, Myriam Benisty, Pietro Curone, John D. Ilee, Gianni Cataldi, Hsi-Wei Yen, Richard Teague, Christophe Pinte, Jane Huang, Himanshi Garg, Ryuta Orihara, Ian Czekala, Brianna Zawadzki, Sean M. Andrews, David J. Wilner, Jaehan Bae, Marcelo Barraza-Alfaro, Daniele Fasano, Mario Flock, Misato Fukagawa, Maria Galloway-Sprietsma, Andrés F. Izquierdo, Kazuhiro Kanagawa, Geoffroy Lesur, Cristiano Longarini, Francois Menard, Daniel J. Price, Giovanni Rosotti, Jochen Stadler, Gaylor Wafflard-Fernandez, Lisa Wölfer, and Tomohiro C. Yoshida. . , 984(1):L7, May 2025.

(ref: Andrews2018) Sean M. Andrews, Jane Huang, Laura M. Pérez, Andrea Isella, Cornelis P. Dullemond, Nicolás T. Kurtovic, Viviana V. Guzmán, John M. Carpenter, David J. Wilner, Shangjia Zhang, Zhaohuan Zhu, Tilman Birnstiel, Xue-Ning Bai, Myriam Benisty, A. Meredith Hughes, Karin I. Öberg, and Luca Ricci. . , 869(2):L41, December 2018.

(ref: Czekala2021) Ian Czekala, Ryan A. Loomis, Richard Teague, Alice S. Booth, Jane Huang, Gianni Cataldi, John D. Ilee, Charles J. Law, Catherine Walsh, Arthur D. Bosman, Viviana V. Guzmán, Romane Le Gal, Karin I. Öberg, Yoshihide Yamato, Yuri Aikawa, Sean M. Andrews, Jaehan Bae, Edwin A. Bergin, Jennifer B. Bergner, L. Ilsedore Cleeves, Nicolas T. Kurtovic, François Ménard, Hideko Nomura, Laura M. Pérez, Chunhua Qi, Kamber R. Schwarz, Takashi Tsukagoshi, Abygail R. Waggoner, David J. Wilner, and Ke Zhang. . , 257(1):2, November 2021.

(ref: Jorsater1995) Steven Jorsater and Gustaaf A. van Moorsel. . , 110:2037, November 1995.

(ref: Teague2020) Richard Teague. , December 2020.

(ref: Goldsmith1999) Paul F. Goldsmith and William D. Langer. . , 517(1):209–225, May 1999.

(ref: Loomis2018) Ryan A. Loomis, L. Ilsedore Cleeves, Karin I. Öberg, Yuri Aikawa, Jennifer Bergner, Kenji Furuya, V. V. Guzman, and Catherine Walsh. . , 859(2):131, June 2018.

(ref: Leemker2021) M. Leemker, M. L. R. van’t Hoff, L. Trapman, M. L. van Gelder, M. R. Hogerheijde, D. Ruı́z-Rodrı́guez, and E. F. van Dishoeck. . , 646:A3, February 2021.

(ref: Wang2025) Yu Wang, Chris W. Ormel, Shoji Mori, and Xue-Ning Bai. . , 696:A38, April 2025.

(ref: Vastel2010) C. Vastel, C. Ceccarelli, E. Caux, A. Coutens, J. Cernicharo, S. Bottinelli, K. Demyk, A. Faure, L. Wiesenfeld, Y. Scribano, A. Bacmann, P. Hily-Blant, S. Maret, A. Walters, E. A. Bergin, G. A. Blake, A. Castets, N. Crimier, C. Dominik, P. Encrenaz, M. Gérin, P. Hennebelle, C. Kahane, A. Klotz, G. Melnick, L. Pagani, B. Parise, P. Schilke, V. Wakelam, A. Baudry, T. Bell, M. Benedettini, A. Boogert, S. Cabrit, P. Caselli, C. Codella, C. Comito, E. Falgarone, A. Fuente, P. F. Goldsmith, F. Helmich, T. Henning, E. Herbst, T. Jacq, M. Kama, W. Langer, B. Lefloch, D. Lis, S. Lord, A. Lorenzani, D. Neufeld, B. Nisini, S. Pacheco, J. Pearson, T. Phillips, M. Salez, P. Saraceno, K. Schuster, X. Tielens, F. van der Tak, M. H. D. van der Wiel, S. Viti, F. Wyrowski, H. Yorke, P. Cais, J. M. Krieg, M. Olberg, and L. Ravera. . , 521:L31, October 2010.

(ref: Hama2016) Tetsuya Hama, Akira Kouchi, and Naoki Watanabe. . , 351(6268):65–67, January 2016.

(ref: Messer1984) J. K. Messer, Frank C. De Lucia, and Paul Helminger. . , 105(1):139–155, May 1984.

(ref: Matsushima2001) Fusakazu Matsushima, Motomi Matsunaga, Guang-Yuan Qian, Yuichiro Ohtaki, Rong-Long Wang, and Kojiro Takagi. . , 206(1):41–46, March 2001.

(ref: Muller2001) H. S. P. Müller, S. Thorwirth, D. A. Roth, and G. Winnewisser. . , 370:L49–L52, April 2001.

(ref: Muller2005) Holger S. P. Müller, Frank Schlöder, Jürgen Stutzki, and Gisbert Winnewisser. . , 742(1-3):215–227, May 2005.

(ref: Bunken2007) Sandra Brünken, Holger S. P. Müller, Christian Endres, Frank Lewen, Thomas Giesen, Brian Drouin, John C. Pearson, and Heinrich Mäder. . , 9(17):2103, January 2007.

(ref: Endres2016) Christian P. Endres, Stephan Schlemmer, Peter Schilke, Jürgen Stutzki, and Holger S. P. Müller. . , 327:95–104, September 2016.

(ref: Pickett1998) H. M. Pickett, R. L. Poynter, E. A. Cohen, M. L. Delitsky, J. C. Pearson, and H. S. P. Müller. , 60(5):883–890, November 1998.

(ref: DeLucia1972) Frank C. de Lucia, Paul Helminger, Robert L. Cook, and Walter Gordy. . , 6(4):1324–1326, October 1972.

(ref: Bergin2007) Edwin A. Bergin and Mario Tafalla. . , 45(1):339–396, September 2007.

(ref: Persson2014) M. V. Persson, J. K. Jørgensen, E. F. van Dishoeck, and D. Harsono. . , 563:A74, March 2014.

(ref: Mandt2024) Kathleen E. Mandt, Jacob Lustig-Yaeger, Adrienn Luspay-Kuti, Peter Wurz, Dennis Bodewits, Stephen A. Fuselier, Olivier Mousis, Steven M. Petrinec, and Karlheinz J. Trattner. A nearly terrestrial d/h for comet 67p/churyumov-gerasimenko. , 10(46):eadp2191, 2024.

(ref: BockeleeMorvan1998) D. Bockelée-Morvan, D. Gautier, D. C. Lis, K. Young, J. Keene, T. Phillips, T. Owen, J. Crovisier, P. F. Goldsmith, E. A. Bergin, D. Despois, and A. Wootten. . , 133(1):147–162, May 1998.

(ref: Meier1998) Roland Meier, Tobias C. Owen, Henry E. Matthews, David C. Jewitt, Dominique Bockelee-Morvan, Nicolas Biver, Jacques Crovisier, and Daniel Gautier. . , 279:842, February 1998.

(ref: Gibb2012) Erika L. Gibb, Boncho P. Bonev, Geronimo Villanueva, Michael A. DiSanti, Michael J. Mumma, Emily Sudholt, and Yana Radeva. . , 750(2):102, May 2012.

(ref: Villanueva2009) G. L. Villanueva, M. J. Mumma, B. P. Bonev, M. A. Di Santi, E. L. Gibb, H. Böhnhardt, and M. Lippi. . , 690(1):L5–L9, January 2009.

(ref: BockeleeMorvan2012) D. Bockelée-Morvan, N. Biver, B. Swinyard, M. de Val-Borro, J. Crovisier, P. Hartogh, D. C. Lis, R. Moreno, S. Szutowicz, E. Lellouch, M. Emprechtinger, G. A. Blake, R. Courtin, C. Jarchow, M. Kidger, M. Küppers, M. Rengel, G. R. Davis, T. Fulton, D. Naylor, S. Sidher, and H. Walker. . , 544:L15, August 2012.

(ref: Biver2006) N. Biver, D. Bockelée-Morvan, J. Crovisier, D. C. Lis, R. Moreno, P. Colom, F. Henry, F. Herpin, G. Paubert, and M. Womack. . , 449(3):1255–1270, April 2006.

(ref: Biver2016) N. Biver, R. Moreno, D. Bockelée-Morvan, Aa. Sandqvist, P. Colom, J. Crovisier, D. C. Lis, J. Boissier, V. Debout, G. Paubert, S. Milam, A. Hjalmarson, S. Lundin, T. Karlsson, M. Battelino, U. Frisk, D. Murtagh, and Odin Team. . , 589:A78, May 2016.

(ref: Lis2013) D. C. Lis, N. Biver, D. Bockelée-Morvan, P. Hartogh, E. A. Bergin, G. A. Blake, J. Crovisier, M. de Val-Borro, E. Jehin, M. Küppers, J. Manfroid, R. Moreno, M. Rengel, and S. Szutowicz. . , 774(1):L3, September 2013.

(ref: Hartogh2011) Paul Hartogh, Dariusz C. Lis, Dominique Bockelée-Morvan, Miguel de Val-Borro, Nicolas Biver, Michael Küppers, Martin Emprechtinger, Edwin A. Bergin, Jacques Crovisier, Miriam Rengel, Raphael Moreno, Slawomira Szutowicz, and Geoffrey A. Blake. . , 478(7368):218–220, October 2011.

(ref: Lis2019) Dariusz C. Lis, Dominique Bockelée-Morvan, Rolf Güsten, Nicolas Biver, Jürgen Stutzki, Yan Delorme, Carlos Durán, Helmut Wiesemeyer, and Yoko Okada. . , 625:L5, May 2019.

(ref: Andreu2023) A. Andreu, A. Coutens, F. Cruz-Sáenz de Miera, N. Houry, J. K. Jørgensen, A. Kóspál, and D. Harsono. . , 677:L17, September 2023.

(ref: Faure2019) A. Faure, P. Hily-Blant, C. Rist, G. Pineau des Forêts, A. Matthews, and D. R. Flower. . , 487(3):3392–3403, August 2019.

(ref: Faure2024) A. Faure, M. Żółtowski, L. Wiesenfeld, F. Lique, and A. Bergeat. . , 527(2):3087–3093, January 2024.

</paper>

Write the methods card for this paper.