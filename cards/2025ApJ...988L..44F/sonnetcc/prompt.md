# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...988L..44F\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...988L..44F",
 "title": "A Deep Search for Ethylene Glycol and Glycolonitrile in the V883 Ori Protoplanetary Disk",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Fadul, Abubakar M. A.",
 "n_authors": 6,
 "arxiv_id": "2507.14905",
 "doi": "10.3847/2041-8213/adec6e",
 "alma_projects_linked_by_archive": [
  "2021.1.00452.S"
 ]
}
```

Paper text:
<paper>
# A deep Search for Ethylene Glycol and Glycolonitrile in the V883 Ori Protoplanetary Disk

## Abstract

Ethylene glycol ($\mathrm{(CH_2OH)_2}$, hereafter EG) and Glycolonitrile ($\mathrm{HOCH_2CN}$, hereafter GN) are considered molecular precursors of nucleic acids. EG is a sugar alcohol and the reduced form of Glycolaldehyde ($\mathrm{CH_2(OH)CHO}$, hereafter GA). GN is considered a key precursor of adenine formation (nucleotide) and can be a precursor of glycine (amino acid). Detections of such prebiotic molecules in the interstellar medium are increasingly common. How much of this complexity endures to the planet formation stage, and thus is already present when planets form, remains largely unknown. Here we report Atacama Large Millimeter/sub-millimeter Array (ALMA) observations in which we tentatively detect EG and GN in the protoplanetary disk around the outbursting protostar V883 Ori. The observed EG emission is best reproduced by a column density of $\mathrm{3.63^{+0.11}_{-0.12} \times 10^{16} \; cm^{-2}}$ and a temperature of at least 300 K. The observed GN emission is best reproduced by a column density of $\mathrm{3.37^{+0.09}_{-0.09} \times 10^{16} \; cm^{-2}}$ and a temperature of $88^{+1.2}_{-1.2}$ K. Comparing the abundance of EG and GN relative to methanol in V883 Ori with other objects, V883 Ori falls between hot cores and comets in terms of increasing complexity. This suggests that the build up of prebiotic molecules continues past the hot core phase into the epoch of planet formation. Nascent planets in such environments may inherit essential building blocks for life, enhancing their potential habitability. Further observations of this protoplanetary disk at higher spectral resolution are required to resolve blended lines and to confirm these tentative detection.

# Introduction

The ingredients for life originated in space. A key element to assessing how common life is in the universe is understanding the extent to which the Earth inherited biotic molecules. Within our own solar system sugars, sugar acids, amino acids, and the nucleobases which make up DNA and RNA have been seen in asteroids and meteorites (cite: Cooper01; Glavin10; Callahan11; Parker23; Oba23; Koga24; Glavin25).

Comets, which are comprised of less processed material than meteors and asteroids, have not been observed to contain the most complex molecules listed above. However, sugar acids thought to be the precursors of amino acids and nucleic acids, such as GA and EG, have been observed in the comae of several comets (cite: Crovisier04; LeRoy15; Biver2015SciA; Biver24). Additionally, glycine, the simplest amino acid, which is thought to form from the reaction between GN and ammonia ((cite: Zeng19) and references therein), was detected in the coma of comet 67P/Churyumov-Gerasimenko (67P/C-G) by the Rosetta mission (cite: Altwegg16).

Observations of hot dense cores in the ISM have revealed a plethora of complex organic molecules (COMs), molecules six atoms or larger containing at least one Carbon atom (cite: McGuire22). This includes GA, EG, and the nitrogen-bearing GN (also called hydroxyacetonitile) among others (cite: Hollis00; Hollis02; Rivilla17; Rivilla22). This chemical complexity appears to persist in the envelopes of protostars (cite: Coutens2015A&A; Jorgensen2016A&A; Zeng19; Ligterink2021A&A).

How much this chemical complexity is preserved, enhanced, or destroyed in the protoplanetary disk remains uncertain. Shocks and heating during protostellar collapse, and as infalling gas transitions from the envelope to the protoplanetary disk, may destroy many COMs. In this ‘reset’ scenario the COMs seen in comets must form no earlier than the protoplanetary disk phase. Even if some chemical complexity is inherited, additional ice chemistry on dust grains within the disk can lead to increased COM abundances.

Relatively few COMs have been detected in protoplanetary disks compared to less evolved sources (cite: Walsh16; Yamato2024AJ). The difficulty of observing COMs in protoplanetary disks is two fold. First, the emission area is small. Second, disks are cold, such that many COMs are frozen out on dust grains as ices throughout much of the disk. There are two special cases which have proved conducive to detecting COMs in disks. The first is dust traps, where photodesorbed ices can be seen in the gas (cite: Marel2021A&A; Booth24b). The second is in FU Orionis objects during an outburst event, which heats the disk, liberating ices and increasing the area hot enough to emit (cite: Calahan24). This second approach has proved successful in detecting a plethora of molecules in the disk of V883 Ori, including COMs (cite: Merel2018ApJ; Lee_2019; Tobin23; Yamato2024AJ; Lee2025ApJ). However, the more complex pre-biotic species detected in the envelopes of less evolved protostars remain undetected in any protoplanetary disk.

Here we report tentative detection of EG and GN in the V883 Ori protoplanetary disk. Our observations cover a frequency range not yet explored for this object, but which has yielded tentative detections of pre-biotic molecules in less evolved sources. The resulting spectrum is rich in molecular lines, as recently reported by (cite: Fadul25). In this work we focus on the detection of the pre-biotic species. Section [2](#sec:reduction) describes the observations and data reduction. Section [3](#sec:analysis) describes the data analysis. Section [4](#sec:discussion) discusses our findings in the context of other sources. Finally, our conclusions are given in Section [5](#sec:conclusion).

# Observations and Data Reduction

V883 Ori was observed with the Atacama Large Millimeter/sub-milliter Array (ALMA) over six execution blocks between 30 December, 2021 and 19 September, 2022 as part of project 2021.1.00452.S. Observations were done in Band 7 in spectral scanning mode, covering the frequency range 348-366 GHz. The spectral resolution was set to 488.281 kHz, corresponding to approximately 0.42 km $\mathrm{s^{-1}}$ at these frequencies.

Data reduction was carried out using the standard ALMA calibration pipeline in the Common Astronomy Software Applications (CASA) package, version 6.4.1.12. Imaging was carried out using *tclean* with Briggs weighting and a robust factor of 0.5. The final continuum subtracted line cube has a $0.48\ensuremath{''} \times 0.29\ensuremath{''}$ beam with a position angle of $-68^{\circ}$. The RMS noise level is 5.97 mJy beam$^{-1}$. For additional details on the observations and calibration see (cite: Fadul25).

# Analysis

The identification and analysis of these lines was carried out with the spectral line fitting tool developed by (cite: Fadul25). The spectroscopic parameters of EG and GN, as well as GA and the species identified by (cite: Fadul25) were taken from the Cologne Database for Molecular Spectroscopy (CDMS; (cite: CDMS2001A&A; CDMSEndres_2016)) using “Splatalogue[^1]” online database. The model line emission is generated assuming local thermodynamic equilibrium (LTE) conditions using the formula $$\begin{equation}
    F_{mod}(\nu) = \Omega \, \Delta V \, B(\nu, T_{ex}) \, \frac{\nu \, \tau_0}{2 \, c \, \sqrt{\text{ln}(2)}},
\end{equation}$$ where $\Omega = \mathrm{\pi (\frac{R}{d})^2}$ is the emitting area, $R = 0.3\ensuremath{''}$ is the emission radius, $d=400$ pc is the distance to the star, and $\Delta V = 2 \mathrm{ km\; s^{-1}}$ is the full width at half maximum (FWHM) of the line. The emitting area and FWHM are both based on previous higher spatial resolution observations of COMs in V883 Ori (cite: Lee_2019). $B(\nu, T_{ex})$ is the Planck function for a blackbody, $\nu$ is the rest frequency of a given transition, and $\tau_0$ is optical depth at line center: $$\begin{equation}
    \tau_0 = \Biggl(\frac{\sqrt{\mathbf{ln(2)}}}{4\pi\, \sqrt{\pi}}\Biggl)\, \Biggl(\frac{A_{ul}\, N_{tot}}{\Delta V}\Biggl)\, \Biggl(\frac{c}{\nu}\Biggl)^3\, \Biggl(\frac{n_l\, g_u}{g_l} - n_u\Biggl).
\end{equation}$$ In Equation 2 $A_{ul}$ is the Einstein A coefficient, $N_{tot}$ is the total column density of the species, $n_u$ and $n_l$ are the number of molecules in the upper and lower energy levels assuming LTE, and $g_u$ and $g_l$ are the statistical weights for the respective levels.

The Markov Chain Monte Carlo (MCMC) package *emcee* (cite: emcee2013) is used to identify the best fit combination of $N_{tot}$ and $T_{ex}$ for each molecule. The goodness of fit is determined by calculating the $\chi^2$ at frequencies where emission is detected above $5\sigma$ corresponding to known transitions of the fitted molecule. Fitting is done one molecule at a time, with the best fit model subtracted from the spectra before fitting subsequent species. The fitting and identification processes, as well as the model has been used is described in detail by (cite: Fadul25). We subtracted all the molecules (shown in blue in Figure [1](#results)) identified by (cite: Fadul25) from the data before fitting EG and then GN.

We tentatively identify 15 transitions of EG and 6 transitions of GN (Figure [1](#results)). The cumulative model for all molecules detected by (cite: Fadul25), including EG and GN, is shown in Figure [6](#summed_spectra) in Appendix [8](#AppendixC). All the modeled transitions are reported in Appendix [6](#AppendixA). We also attempted to fit GA, based on its detection in protostars for which EG was also detected, but were unable to secure a robust detection, see Appendix D in (cite: Fadul25). The best fit values of $\mathrm{T_{ex}}$ and $\mathrm{N_{tot}}$ are reported in Table [\[resulttable\]](#resulttable). $\mathrm{T_{ex}}$ and $\mathrm{N_{tot}}$ are well constrain for GN by the model (see Appendix [7](#AppendixB)). For EG, $T_{ex}$ was not well constrained by the model, instead always approaching the highest allowed temperature. However, we find that using a two temperature model neither improves the fit nor provides a better constraint on the temperature(s). We fixed the temperature to 300 K where we have a best fit from the model. However, it is possible that the data would be better fit by a model with a more complex temperature structure.

To improve the fit we utilize a multiple Gaussian fitting approach in the region where transitions from EG or GN are present, fitting Gaussian profiles to all lines which overlap with target molecule. We then isolate the Gaussian profiles associated with EG and GN from nearby lines. Subsequently, we run our MCMC model on the isolated Gaussian fits to identify the best-fit parameters. Figure [2](#fittest) shows the isolated Gaussian profiles of the EG and GN transitions plotted on the observed data along with the best-fit model of these profiles. No significant improvement was observed in the fit compared to the best-fit model applied directly to the observed data.

Furthermore, to confirm whether these transitions originate from EG and GN or other molecules, we checked the Splatalogue database to search for molecules that emit at similar frequencies. We modeled the emission of molecules that are highly likely to blend with EG and GN, but none were found to overlap with these two species. The molecules tested include: Acetic acid, Glycine, Aminoacetonitrile, Ethanol, Propenal, Methoxymethanol, Vinyl alcohol, among others already examined by (cite: Fadul25).

Figure [3](#momentmaps) shows the integrated intensity (moment 0) and the intensity weighted velocity (moment 1) maps of the most isolated EG and GN transitions. The integrated intensity maps sum the emission from 4 transitions of EG and 2 transitions of GN respectively, while the intensity weighted velocity maps are averages. The moment 1 maps show a clear shift from red-shifted to blue-shifted across the disk semi-major axis, consistent with emission from a rotating disk. This pattern supports our assumption of emission from a Keplerian disk centered at these frequencies.

[1](#results) ![image](Figures/prebiotic_spectra.png)

| Molecule | Formula | N$_{\text{tot}}$ (cm$^{-2}$) | T$_{\text{ex}}$ (K) | No. lines |
|:---|:--:|:--:|:--:|:--:|
| Ethylene glycol | $\mathrm{g'Gg-(CH_2OH)_2}$ | $3.62^{+0.11}_{-0.12}\times 10^{16}$ | \[300\] | 18 |
| Glycolonitrle | $\mathrm{HOCH_2CN}$ | $3.37^{+0.09}_{-0.09}\times 10^{16}$ | $88^{+1.2}_{-1.2}$ | 9 |
|  |  |  |  |  |

![](Figures/prebiotic_spectra_GT.png)

The dotted and dashed gray line indicates the noise level in the data (corresponding to 1 and 3$\sigma$).

![](Figures/V883_momentmaps_HNC.png)

# Discussion

## Comparison to other sources

EG and GN have been detected in multiple environments, including in the central molecular zone of the Galaxy, nearby high mass star-forming regions, Class 0 protostars, and in solar system bodies. The results presented here are tentative detection of these prebiotic molecules in a protoplanetary disk. To compare the abundances across sources, we take the ratio of the derived EG and GN column density to that of methanol (Figure [4](#prebiotic_methanl)). Methanol is one of the simplest CHO-bearing molecules, and thus one of the first to form. Thus, it is often used as a reference species when comparing abundances between sources (cite: Drozdovskaya2018MNRAS).

The abundance of EG relative to methanol in V883 Ori is greater than that seen in Class 0 protostellar envelopes but less than that of comets. GN has yet to be detected in any solar system bodies, but has been detected in a number of protostellar envelopes and molecular clouds. The abundance ratio of GN relative to methanol in V883 Ori is several orders of magnitude higher than the ratio in less evolved environments. Taken together, these ratios point to substantial prebiotic chemistry during the evolution from protostellar envelope to protoplanetary disk.

The increased abundance of these COMs from the protostellar envelope to the protoplanetary disk stage offers insight into whether chemical complexity is lost between the two stages. Chemical models of protoplanetary disk environments require timescales of several million years to build up a large abundance of methanol from CO on the surface of dust grains (cite: Bosman18; Schwarz2019ApJ). The build up of more complex species such as EG and GN should take even longer. Thus, the increase in the abundance of both EG and GN relative to methanol between envelopes and the V883 Ori disk suggests that the envelope COMs are delivered to the disk largely intact, but COMs continue to be produced in the disk. Comparison of the abundance of simpler ices in envelopes, disks, and comets also supports the idea that chemical complexity is inherited from earlier evolutionary stages (cite: Lippi24).

## Upper limits of GA

Previous studies of protoplanetary disks have searched unsuccessfully for both GA and EG (cite: Brunken2022A&A; Lee2025ApJ). Our observations focus on a higher frequency range in part because this regime should provide the highest signal-to-noise ratio for GA emission assuming a gas temperature of 103, the temperature derived for CH$_\mathrm{3}$OCHO by (cite: Lee_2019). While we searched our observations for GA, we were unable to secure a robust detection. There are only two transitions that matched the data. However, these GA transitions overlap with formaldehyde ($\mathrm{H_2CO}$) transitions. For all other expected transitions there is no emission in the observed data. Therefore, we take column density from our best fit model as an upper limit. The expected GA transitions from our model are shown in Appendix D in (cite: Fadul25).

The non-detection of GA could be attributed to its destruction by OH, as suggested by (cite: Coutens2018MNRAS). Their models indicate that in low-mass sources, OH efficiently depletes GA, lowering its abundance to extremely low levels ($\sim 10^{-16}$) within a few hundred thousand years, making it undetectable. Another possible reason for its non-detection could be its conversion to EG by hydrogenation (cite: leroux2021). These two mechanisms could significantly lower the GA abundance. Consequently, it might be extremely hard to secure a robust detection of this molecule.

## Previous non-detections of EG in V883 Ori

Previous studies has already searched for both GA and EG (cite: Brunken2022A&A; Lee2025ApJ) in Oph IRS 48 and V883 Ori without success. For EG, we tentatively detect the g’Gg-conformer but not the a’Gg-conformer. To further test our model, we run a check using ALMA band 6 data, which published by (cite: Lee2025ApJ) as it covers many transitions of EG and GA. We plot the predicted EG in Band 6 using our best fit results from Band 7 in Appendix [9](#AppendixD). While the current study does not focus on the Band 6 data, our model appears consistent with the observations in this Band. We note that the predicted EG emission is relatively weak, which could explain the non-detection reported by (cite: Lee2025ApJ). Additionally, confusion with nearby lines could also contribute (cite: Jorgensen2020ARA&A). In summary, the Band 6 data appear to support the existence of EG in V883 Ori, though a more detailed analysis is needed.

![](Figures/prebiotic_methanol.png)

## Formation routes

GN can form on the icy grain surface through several reaction pathways. First is the reaction between $\mathrm{H_2CO}$ and isocyanide (HNC) (cite: Woon2001JPCA). The reaction is exothermic and has enough energy to desorb the formed GN into the gas phase. Second is the thermal reaction between $\mathrm{H_2CO}$, $\mathrm{NH_3}$ and HCN (cite: Danger2012ApJ). GN can also form through the hydrogenation of $\mathrm{OCH_2CN}$ and HOCHCN (cite: Danger2013A&A).

EG is likely formed on grain surfaces, either through the hydrogenation of GA (cite: leroux2021) or the recombination of $\mathrm{CH_2OH}$ radicals produced from methanol (cite: Butscher2015MNRAS). Both EG and GA may originate from radical-radical reactions involving methanol. Additionally, it is known that these two molecules can interconvert via hydrogenation or irradiation processes (cite: Fedoseev2015MNRAS; hudson2005). If EG forms from GA, the abundance ratio of the two species is expected to be near unity (cite: Rivilla17). However, since the GA was not detected in our observations and our reported ratio of EG/GA is a lower limit, it is possible that the actual ratio being near unity cannot be ruled out. This could bring the ratio in V883 Ori into agreement with that of the Class 0 protostar IRAS 16293 B ((cite: Nazari2024A&A; Jorgensen2016A&A)). Tighter constraints on the EG/GA ratio could clarify if EG was actually formed via hydrogenation of GA. The non-detection of GA in our observations is consistent with $\mathrm{(CH_2OH)_2} /\ \mathrm{CH_2(OH)CHO} \leq 1.6$ for a gas temperature of 300 K. Without tighter constraints on the GA abundance, we cannot determine the formation mechanism for EG in this source. For both EG and GN, it is likely these species formed via reactions between ices on the grain surface and are observable in V883 Ori because of the outburst induced temperature increase.

## Uncertainty in the measured abundances

The $\mathrm{CH_3OH}$ column density is taken from (cite: Fadul25). Since $\mathrm{CH_3OH}$ column density is not reliably measured, its difficult to constrain from the main isotopologue. Instead we use the $\mathrm{^{13}CH_3OH}$ column density multiplied by the canonical ISM $\mathrm{^{12}C/^{13}C}$ ratio of 60 (cite: Langer93ApJ). The ratio of $\mathrm{^{12}C/^{13}C}$ in star-forming regions has been found to be significantly lower than the canonical ISM value (see, e.g., (cite: Jorgensen2018A&A; Yamato2024AJ; 2025arXiv250202873H)). This variation could lead to significant uncertainty, especially when using the ISM $\mathrm{^{12}C/^{13}C}$ ratio to compare the abundances of molecules in star-forming regions, where the $\mathrm{^{12}C/^{13}C}$ ratio is lower than in the ISM. Additional sources of uncertainty include dust opacity and assuming a constant source size. All of these factors have been discussed in detail in (cite: Fadul25). Furthermore, since we tentatively detect these molecules, this also introduces uncertainty in the comparison with other sources that have confirmed detections. In particular, there is significant line blending at the current spectral resolution of 0.42 km $\mathrm{s^{-1}}$, making it difficult to disentangle contributions from other species. Additional observations of this disk are required to confirm the detection and to reliably compare it with other sources.

# Conclusions

We report tentative detection of 15 transitions of EG and 6 transitions of GN toward the outbursting source V883 Ori. This is the first time either species has been tentatively detected in a protoplanetary disk. We find the observations are best fit by a model of EG with a column density $3.63^{+0.11}_{-0.12}\times10^{16}$ cm$^\mathrm{-2}$, where the temperature has been fixed to 300 K. GN is best fit by a column density of $3.37^{+0.09}_{-0.09}\times10^{16}$ cm$^\mathrm{-2}$ and a temperature of $88^{+1.2}_{-1.2}$ K. Comparing these abundances to those in other sources places V883 Ori in a sequence of increasing complexity with evolutionary stage, with higher abundances than seen in protostellar cores but lower abundances than seen in comets. This further suggests that protoplantary disks inherit complex molecules from protostellar envelopes and that COM formation can continue during the protoplantary disk stage. Further observations are needed to confirm the detection of these species and further look for more complex species.

We thank the reviewer for their constructive and insightful comments, which have helped improve the quality of the paper. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00452.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

K.S. and T.S. would like to acknowledge European Research Council under the Horizon 2020 Framework Program via the ERC Advanced Grant Origins 83 24 28.

# Facilities

ALMA

# Software

Astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A; astropy:2022), Gofish (cite: GoFish), Emcee (cite: emcee2013), CASA (cite: The_CASA_Team_2022), Numpy (cite: numpyharris2020array), Matplotlib (cite: matplotlibHunter:2007), corner.py (cite: corner), Pandas (cite: pandasmckinney-proc-scipy-2010)

# ORCID iDs

Abubakar M. A. Fadul : <https://orcid.org/0009-0003-6626-8122>

Kamber R. Schwarz : <https://orcid.org/0000-0002-6429-9457>

Tushar Suhasaria : <https://orcid.org/0000-0002-4755-4719>

Jenny K. Calahan : <https://orcid.org/0000-0002-0150-0125>

Jane Huang : <https://orcid.org/0000-0001-6947-6072>

Merel L. R. van ’t Hoff : <https://orcid.org/0000-0002-2555-9869>

natexlab

(ref: Altwegg16) Altwegg, K., Balsiger, H., Bar-Nun, A., et al. 2016, Science Advances, 2, e1600285, doi: [`10.1126/sciadv.1600285`](http://doi.org/10.1126/sciadv.1600285)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Belloche2013A&A) Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013, A&A, 559, A47, doi: [`10.1051/0004-6361/201321096`](http://doi.org/10.1051/0004-6361/201321096)

(ref: Biver2014A&A) Biver, N., Bockelée-Morvan, D., Debout, V., et al. 2014, A&A, 566, L5, doi: [`10.1051/0004-6361/201423890`](http://doi.org/10.1051/0004-6361/201423890)

(ref: Biver2015SciA) Biver, N., Bockelée-Morvan, D., Moreno, R., et al. 2015, Science Advances, 1, 1500863, doi: [`10.1126/sciadv.1500863`](http://doi.org/10.1126/sciadv.1500863)

(ref: Biver24) Biver, N., Bockelée-Morvan, D., Handzlik, B., et al. 2024, A&A, 690, A271, doi: [`10.1051/0004-6361/202450921`](http://doi.org/10.1051/0004-6361/202450921)

(ref: Bockel2000A&A) Bockelée-Morvan, D., Lis, D. C., Wink, J. E., et al. 2000, A&A, 353, 1101

(ref: Booth24b) Booth, A. S., Temmink, M., van Dishoeck, E. F., et al. 2024, AJ, 167, 165, doi: [`10.3847/1538-3881/ad26ff`](http://doi.org/10.3847/1538-3881/ad26ff)

(ref: Bosman18) Bosman, A. D., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 618, A182, doi: [`10.1051/0004-6361/201833497`](http://doi.org/10.1051/0004-6361/201833497)

(ref: Brouillet2015A&A) Brouillet, N., Despois, D., Lu, X. H., et al. 2015, A&A, 576, A129, doi: [`10.1051/0004-6361/201424588`](http://doi.org/10.1051/0004-6361/201424588)

(ref: Brunken2022A&A) Brunken, N. G. C., Booth, A. S., Leemker, M., et al. 2022, A&A, 659, A29, doi: [`10.1051/0004-6361/202142981`](http://doi.org/10.1051/0004-6361/202142981)

(ref: Butscher2015MNRAS) Butscher, T., Duvernay, F., Theule, P., et al. 2015, MNRAS, 453, 1587, doi: [`10.1093/mnras/stv1706`](http://doi.org/10.1093/mnras/stv1706)

(ref: Calahan24) Calahan, J. K., Bergin, E. A., van’t Hoff, M., et al. 2024, ApJ, 975, 170, doi: [`10.3847/1538-4357/ad78d1`](http://doi.org/10.3847/1538-4357/ad78d1)

(ref: Callahan11) Callahan, M. P., Smith, K. E., Cleaves, H. J., et al. 2011, Proceedings of the National Academy of Science, 108, 13995, doi: [`10.1073/pnas.1106493108`](http://doi.org/10.1073/pnas.1106493108)

(ref: Cieza2016Natur) Cieza, L. A., Casassus, S., Tobin, J., et al. 2016, Nature, 535, 258, doi: [`10.1038/nature18612`](http://doi.org/10.1038/nature18612)

(ref: Cooper01) Cooper, G., Kimmich, N., Belisle, W., et al. 2001, Nature, 414, 879, doi: [`10.1038/414879A`](http://doi.org/10.1038/414879A)

(ref: Coutens2015A&A) Coutens, A., Persson, M. V., Jørgensen, J. K., Wampfler, S. F., & Lykke, J. M. 2015, A&A, 576, A5, doi: [`10.1051/0004-6361/201425484`](http://doi.org/10.1051/0004-6361/201425484)

(ref: Coutens2018MNRAS) Coutens, A., Viti, S., Rawlings, J. M. C., et al. 2018, MNRAS, 475, 2016, doi: [`10.1093/mnras/stx3335`](http://doi.org/10.1093/mnras/stx3335)

(ref: Crovisier04) Crovisier, J., Bockelée-Morvan, D., Biver, N., et al. 2004, A&A, 418, L35, doi: [`10.1051/0004-6361:20040116`](http://doi.org/10.1051/0004-6361:20040116)

(ref: Danger2012ApJ) Danger, G., Duvernay, F., Theulé, P., Borget, F., & Chiavassa, T. 2012, ApJ, 756, 11, doi: [`10.1088/0004-637X/756/1/11`](http://doi.org/10.1088/0004-637X/756/1/11)

(ref: Danger2013A&A) Danger, G., Duvernay, F., Theulé, P., et al. 2013, A&A, 549, A93, doi: [`10.1051/0004-6361/201219779`](http://doi.org/10.1051/0004-6361/201219779)

(ref: Drozdovskaya2018MNRAS) Drozdovskaya, M. N., van Dishoeck, E. F., Jørgensen, J. K., et al. 2018, MNRAS, 476, 4949, doi: [`10.1093/mnras/sty462`](http://doi.org/10.1093/mnras/sty462)

(ref: CDMSEndres_2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. 2016, Journal of Molecular Spectroscopy, 327, 95–104, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: Fadul25) Fadul, A. M. A., Schwarz, K. R., van ’T Hoff, M. L. R., et al. 2025, The Astronomical Journal, 169, 307, doi: [`10.3847/1538-3881/adc998`](http://doi.org/10.3847/1538-3881/adc998)

(ref: Fedoseev2015MNRAS) Fedoseev, G., Cuppen, H. M., Ioppolo, S., Lamberts, T., & Linnartz, H. 2015, MNRAS, 448, 1288, doi: [`10.1093/mnras/stu2603`](http://doi.org/10.1093/mnras/stu2603)

(ref: corner) Foreman-Mackey, D. 2016, The Journal of Open Source Software, 1, 24, doi: [`10.21105/joss.00024`](http://doi.org/10.21105/joss.00024)

(ref: emcee2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Glavin10) Glavin, D., Callahan, M., Dworkin, J., & ELSILA, J. 2010, Meteoritics & Planetary Science, 45, 1948 , doi: [`10.1111/j.1945-5100.2010.01132.x`](http://doi.org/10.1111/j.1945-5100.2010.01132.x)

(ref: Glavin25) Glavin, D. P., Dworkin, J. P., Alexander, C. M. O., et al. 2025, Nature Astronomy, 9, 199, doi: [`10.1038/s41550-024-02472-9`](http://doi.org/10.1038/s41550-024-02472-9)

(ref: numpyharris2020array) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hollis00) Hollis, J. M., Lovas, F. J., & Jewell, P. R. 2000, ApJL, 540, L107, doi: [`10.1086/312881`](http://doi.org/10.1086/312881)

(ref: Hollis02) Hollis, J. M., Lovas, F. J., Jewell, P. R., & Coudert, L. H. 2002, ApJL, 571, L59, doi: [`10.1086/341148`](http://doi.org/10.1086/341148)

(ref: 2025arXiv250202873H) Hsieh, T. H., Pineda, J. E., Segura-Cox, D. M., et al. 2025, arXiv e-prints, arXiv:2502.02873, doi: [`10.48550/arXiv.2502.02873`](http://doi.org/10.48550/arXiv.2502.02873)

(ref: hudson2005) Hudson, R. L., Moore, M. H., & Cook, A. M. 2005, Advances in Space Research, 36, 184

(ref: matplotlibHunter:2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Lee2025ApJ) Jeong, J.-H., Lee, J.-E., Lee, S., et al. 2025, ApJS, 276, 49, doi: [`10.3847/1538-4365/ad9450`](http://doi.org/10.3847/1538-4365/ad9450)

(ref: Jorgensen2020ARA&A) Jørgensen, J. K., Belloche, A., & Garrod, R. T. 2020, ARA&A, 58, 727, doi: [`10.1146/annurev-astro-032620-021927`](http://doi.org/10.1146/annurev-astro-032620-021927)

(ref: Jorgensen2016A&A) Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595, A117, doi: [`10.1051/0004-6361/201628648`](http://doi.org/10.1051/0004-6361/201628648)

(ref: Jorgensen2018A&A) Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, A&A, 620, A170, doi: [`10.1051/0004-6361/201731667`](http://doi.org/10.1051/0004-6361/201731667)

(ref: Koga24) Koga, T., Takano, Y., Oba, Y., Naraoka, H., & Ohkouchi, N. 2024, , 365, 253, doi: [`10.1016/j.gca.2023.10.024`](http://doi.org/10.1016/j.gca.2023.10.024)

(ref: Langer93ApJ) Langer, W. D., & Penzias, A. A. 1993, ApJ, 408, 539, doi: [`10.1086/172611`](http://doi.org/10.1086/172611)

(ref: LeRoy15) Le Roy, L., Altwegg, K., Balsiger, H., et al. 2015, A&A, 583, A1, doi: [`10.1051/0004-6361/201526450`](http://doi.org/10.1051/0004-6361/201526450)

(ref: Lee_2019) Lee, J.-E., Lee, S., Baek, G., et al. 2019, Nature Astronomy, 3, 314, doi: [`10.1038/s41550-018-0680-0`](http://doi.org/10.1038/s41550-018-0680-0)

(ref: leroux2021) Leroux, K., Guillemin, J.-C., & Krim, L. 2021, MNRAS, 507, 2632

(ref: Ligterink2021A&A) Ligterink, N. F. W., Ahmadi, A., Coutens, A., et al. 2021, A&A, 647, A87, doi: [`10.1051/0004-6361/202039619`](http://doi.org/10.1051/0004-6361/202039619)

(ref: Lippi24) Lippi, M., Podio, L., Codella, C., et al. 2024, ApJL, 970, L5, doi: [`10.3847/2041-8213/ad5a6d`](http://doi.org/10.3847/2041-8213/ad5a6d)

(ref: Manigand2020A&A) Manigand, S., Jørgensen, J. K., Calcutt, H., et al. 2020, A&A, 635, A48, doi: [`10.1051/0004-6361/201936299`](http://doi.org/10.1051/0004-6361/201936299)

(ref: McGuire22) McGuire, B. A. 2022, ApJS, 259, 30, doi: [`10.3847/1538-4365/ac2a48`](http://doi.org/10.3847/1538-4365/ac2a48)

(ref: pandasmckinney-proc-scipy-2010) McKinney, W. 2010, in Proceedings of the 9th Python in Science Conference, ed. S. van der Walt & J. Millman, 51 – 56

(ref: Mininni2023A&A) Mininni, C., Beltrán, M. T., Colzi, L., et al. 2023, A&A, 677, A15, doi: [`10.1051/0004-6361/202245277`](http://doi.org/10.1051/0004-6361/202245277)

(ref: CDMS2001A&A) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: Nazari2024A&A) Nazari, P., Cheung, J. S. Y., Asensio, J. F., et al. 2024, A&A, 686, A59, doi: [`10.1051/0004-6361/202347832`](http://doi.org/10.1051/0004-6361/202347832)

(ref: Oba23) Oba, Y., Koga, T., Takano, Y., et al. 2023, Nature Communications, 14, 1292, doi: [`10.1038/s41467-023-36904-3`](http://doi.org/10.1038/s41467-023-36904-3)

(ref: Parker23) Parker, E. T., McLain, H. L., Glavin, D. P., et al. 2023, , 347, 42, doi: [`10.1016/j.gca.2023.02.017`](http://doi.org/10.1016/j.gca.2023.02.017)

(ref: Rivilla17) Rivilla, V. M., Beltrán, M. T., Cesaroni, R., et al. 2017, A&A, 598, A59, doi: [`10.1051/0004-6361/201628373`](http://doi.org/10.1051/0004-6361/201628373)

(ref: Rivilla22) Rivilla, V. M., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2022, Frontiers in Astronomy and Space Sciences, 9, 876870, doi: [`10.3389/fspas.2022.876870`](http://doi.org/10.3389/fspas.2022.876870)

(ref: Schuhmann2019ESC) Schuhmann, M., Altwegg, K., Balsiger, H., et al. 2019, ACS Earth and Space Chemistry, 3, 1854, doi: [`10.1021/acsearthspacechem.9b00094`](http://doi.org/10.1021/acsearthspacechem.9b00094)

(ref: Schwarz2019ApJ) Schwarz, K. R., Bergin, E. A., Cleeves, L. I., et al. 2019, ApJ, 877, 131, doi: [`10.3847/1538-4357/ab1c5e`](http://doi.org/10.3847/1538-4357/ab1c5e)

(ref: GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: The_CASA_Team_2022) Team, T. C., Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Tobin23) Tobin, J. J., van’t Hoff, M. L. R., Leemker, M., et al. 2023, Nature, 615, 227, doi: [`10.1038/s41586-022-05676-z`](http://doi.org/10.1038/s41586-022-05676-z)

(ref: Marel2021A&A) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, A&A, 651, L5, doi: [`10.1051/0004-6361/202141051`](http://doi.org/10.1051/0004-6361/202141051)

(ref: Merel2018ApJ) van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018, ApJL, 864, L23, doi: [`10.3847/2041-8213/aadb8a`](http://doi.org/10.3847/2041-8213/aadb8a)

(ref: Walsh16) Walsh, C., Loomis, R. A., Öberg, K. I., et al. 2016, ApJL, 823, L10, doi: [`10.3847/2041-8205/823/1/L10`](http://doi.org/10.3847/2041-8205/823/1/L10)

(ref: Woon2001JPCA) Woon, D. E. 2001, Journal of Physical Chemistry A, 105, 9478, doi: [`10.1021/jp011830h`](http://doi.org/10.1021/jp011830h)

(ref: Yamato2024AJ) Yamato, Y., Notsu, S., Aikawa, Y., et al. 2024, AJ, 167, 66, doi: [`10.3847/1538-3881/ad11d9`](http://doi.org/10.3847/1538-3881/ad11d9)

(ref: Zeng19) Zeng, S., Quénard, D., Jiménez-Serra, I., et al. 2019, MNRAS, 484, L43, doi: [`10.1093/mnrasl/slz002`](http://doi.org/10.1093/mnrasl/slz002)

# Appendix A

Appendix [6](#AppendixA) presents a list of spectral transitions tentatively identified in our analysis.

+:-----------------------------------------:+:-------------:+:---------------------------:+:--------:+:------------:+:--------:+
| Transition                                | Frequency     | Einstein A                  | $g_u$    | Energy upper | Blended  |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
|                                           | $\nu_0$ (GHz) | log$_{10}A_{ul}$ (s$^{-1}$) |          | $E_u$ (K)    |          |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
|                                           |               |                             |          |              |          |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| Transition                                | Frequency     | Einstein A                  | $g_u$    | Energy upper | Blended  |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
|                                           | $\nu_0$ (GHz) | log$_{10}A_{ul}$ (s$^{-1}$) |          | $E_u$ (K)    |          |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
|                                           |               |                             |          |              |          |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $37_{1,36} - 36_{2,35} \; , v = 0$        | 348.802586    | \-$3.42435$                 | 675      | 326.06599    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $30_{6,25} - 29_{5,24} \,, \, v = 0$      | 349.3103568   | \-$3.86474$                 | 549      | 246.11554    | Yes      |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $35_{4,31} - 34_{5,30}  \, , \, v = 0$    | 349.69353     | \-$3.20425$                 | 639      | 319.51415    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $47_{18,29} - 47_{17,30} \, , \, v = 0$   | 350.703786    | \-$3.6413$                  | 855      | 707.73134    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $46_{18,28} - 46_{17,29} \, , \, v = 0$   | 351.0159031   | \-$3.64404$                 | 651      | 684.79508    | Yes      |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $45_{18,27} - 45_{17,28} \, , \, v = 0$   | 351.3039335   | \-$3.6469$                  | 819      | 662.34685    | Yes      |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $43_{18,25} - 43_{17,46} \, , \, v = 0$   | 351.8125551   | \-$3.65334$                 | 783      | 618.91426    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $42_{18,24} - 42_{17,25} \, , \, v = 0$   | 352.0354431   | \-$3.657$                   | 595      | 597.92987    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $41_{18,23} - 41_{17,24} \, , \, v = 0$   | 352.2388443   | \-$3.66099$                 | 581      | 577.43358    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $36_{3,3} - 35_{4,32} \, , \, v = 0$      | 352.381056    | \-$3.48615$                 | 511      | 328.35156    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $36_{4,33} - 35_{3,32} \, , \, v = 1$     | 352.4266183   | \-$3.48771$                 | 511      | 328.41202    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $36_{4,33} - 35_{3,32} \, , \, v = 0$     | 352.4310121   | \-$3.58553$                 | 657      | 328.35252    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $27_{18,9} - 27_{17,10} \, , \, v = 0$    | 353.5701978   | \-$3.79924$                 | 495      | 341.73379    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $33_{18,15} - 33_{17,17} \, , \, v = 1-0$ | 353.9290933   | \-$3.75616$                 | 469      | 431.06459    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $36_{5,31} - 35_{6,30} \, , \, v = 1$     | 358.3990899   | \-$3.56208$                 | 657      | 344.14887    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $23_{7,16} - 22_{6,17} \, , \, v = 0$     | 363.2782984   | \-$3.65169$                 | 423      | 158.99611    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $21_{8,14} - 20_{7,13} \, , \, v = 0$     | 364.1631555   | \-$3.67378$                 | 301      | 144.01107    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $13_{12,1} - 12_{11,2} \, , \, v = 0$     | 364.8996675   | \-$3.32904$                 | 189      | 114.36793    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| **Glycolonitrile $\mathrm{HOCH_2CN}$**                                                                                       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $38_{2,37} - 37_{1,36} \, , \, v = 0$     | 348.1984298   | \-$3.57192$                 | 77       | 329.59594    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $40_{0,40} - 39_{1,39} \, , \, v = 0$     | 353.2911373   | \-$3.4031$                  | 81       | 351.06461    | Yes      |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $29_{3,27} - 28_{2,26} \, , \, v = 0$     | 358.8614609   | \-$4.06515$                 | 59       | 205.25471    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $17_{4,13} - 16_{3,14} \, , \, v = 0$     | 359.3372576   | \-$3.81874$                 | 35       | 328.35252    | Yes      |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $39_{9,31} - 38_{9,30} \, , \, v = 0$     | 359.8689093   | \-$2.86629$                 | 79       | 457.84286    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $39_{12,27} - 38_{12,26} \, , \, v = 0$   | 359.8813728   | \-$2.88562$                 | 79       | 544.98815    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $39_{4,36} - 38_{4,35} \, , \, v = 0$     | 360.6069554   | \-$2.84584$                 | 79       | 368.30635    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $41_{0,41} - 40_{1,40} \, , \, v = 0$     | 362.0311982   | \-$3.36973$                 | 83       | 368.44463    | No       |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+
| $41_{1,41} - 40_{0,40} \, , \, v = 0$     | 362.2211371   | \-$3.3691$                  | 83       | 368.44871    | Yes      |
+-------------------------------------------+---------------+-----------------------------+----------+--------------+----------+

: Continuation of Table [1](#tab:transitions)

# Appendix B

Posterior distribution of glycolonitrile. We ran an MCMC with 100 walkers for 10,000 steps. We discarded the first 2,000 steps as burn-in, and the remaining 8,000 steps were used to demonstrate the posterior distribution of the parameter space of $\mathrm{T_{ex}}$ and $\mathrm{N_{tot}}$.

![](Figures/HOCH2CN.png)

# Appendix C

Figure [6](#summed_spectra) shows the cumulative model, which adds the best-fit spectra from each molecule reported by (cite: Fadul25) in blue. Additionally, the EG and GN best-fit spectra are included in the same cumulative model, shown in green.

![](Figures/summed_spectra.png)

# Appendix D

Here we show the predicted spectra from our model (see (cite: Fadul25) for more details) of ethylene glycol ($\mathrm{g'Gg-(CH_2OH)_2}$) at $\mathrm{T_{ex}}$ of 300 K and $\mathrm{N_{tot}}$ of $3.6\times10^{16}\; \mathrm{cm^{-2}}$ (best fit values of EG from Band 7 observations (this work)) plotted on top of ALMA Band 6 data published by (cite: Lee2025ApJ). The data have been downloaded from the ALMA archive, and the spectrum was extracted using the function *integrated_spectrum()* implemented in the Python package *Gofish* (cite: GoFish) (for more details see (cite: Fadul25) Section 3). The main parameters used to extract the spectrum are an inner radius of $0\ensuremath{''}$, an outer radius of $0.21\ensuremath{''}$, a position angle of $32^\circ$, an inclination angle of $38.3^\circ$, a distance of 388 pc, and a stellar mass of 1.29 $\mathrm{M\odot}$ ((cite: Cieza2016Natur; Lee_2019; Tobin23; Yamato2024AJ)).

![](Figures/leedata1.png)

![](Figures/leedata2.png)

[^1]: <https://splatalogue.online/#/home>

</paper>

Write the methods card for this paper.