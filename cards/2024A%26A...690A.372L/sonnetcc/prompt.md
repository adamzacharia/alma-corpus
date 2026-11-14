# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...690A.372L\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...690A.372L",
 "title": "A new measurement of the Galactic <SUP>12</SUP>C/<SUP>13</SUP>C gradient from sensitive HCO<SUP>+</SUP> absorption observations",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Luo, Gan",
 "n_authors": 7,
 "arxiv_id": "2409.11821",
 "doi": "10.1051/0004-6361/202451412",
 "alma_projects_linked_by_archive": [
  "2019.1.00685.S",
  "2022.1.01438.S"
 ]
}
```

Paper text:
<paper>
# A new measurement of the Galactic $^{12}$C/$^{13}$C gradient from sensitive HCO$^+$ absorption observations

# Introduction

The measurements of isotopic ratios in the interstellar medium (ISM) are important for understanding Galactic chemical evolution (GCE) due to different stellar yields with different masses (cite: Guesten1982; Maeder1983; Iben1983; Clayton2003; Kobayashi2011; Romano2017; Kobayashi2020). One of the few isotopic ratios that can be easily measured is $^{12}$C/$^{13}$C . Notably, $^{12}$C is mainly produced through He-burning as the primary element (e.g., core-collapse supernovae and He-burning shells in low-mass stars), while $^{13}$C is an intermediate product of CNO cycling in intermediate-mass asymptotic giant branch (AGB) stars (cite: Kobayashi2011; Romano2017). Since the timescale in which massive stars release the elements into the ISM is much shorter than for low-to-intermediate mass stars, the $^{12}$C/$^{13}$C ratios predicted from GCE models would decrease as a function of time with a given initial mass function (IMF). In the Milky Way, a radial gradient in the $^{12}$C/$^{13}$C ratio inferred from $^{12}$C$^{18}$O and $^{13}$C$^{18}$O rises from approximately 24 at a galactocentric distance ($R_{\rm GC}$) of $\sim$ 0.5 kiloparsec (kpc) to roughly 70 at $R_{\rm GC}$ $\sim$ 12 kpc (cite: Langer1990; Langer1993).

While various methodologies and tracers have been employed in recent years to constrain the Galactic $^{12}$C/$^{13}$C gradient (cite: Halfen2017; Yan2019; Jacob2020; Sun2024), the different methods have yielded inconsistent results, especially for the Galactic center (GC) regions. Measuring the $^{12}$C/$^{13}$C isotopic ratio with molecular lines faces challenges from both observational factors (e.g., opacity, beam dilution) and chemical effects (e.g., selective photodissociation and fractionation). The most abundant carbon-bearing isotopologs (e.g., $^{12}$CO, H$^{12}$CO$^+$, H$^{12}$CN) can easily become optically thick in dense clouds, making precise estimation of column densities difficult. In diffuse and translucent clouds, the main isotopologs may not pose challenges for optical depths, but the rare isotopologs are often difficult to detect due to their low abundance and sub-thermally excitation of even the ground state transition (cite: Godard2010; Luo2020). Additionally, distant clouds have smaller beam-filling factors, which reduces the reliability of the measurements observed with a single dish.

Isotope-selective photodissociation and isotopic exchange reactions can strongly alter the $^{12}$C/$^{13}$C isotopic ratios in molecules from the original element ratios. For abundant species such as CO, the self-shielding of $^{12}$CO is significantly stronger than less abundant isotopologs (e.g., $^{13}$CO and C$^{18}$O). Thus, the $^{12}$C/$^{13}$C ratio in CO would be higher under the existence of external UV radiation (cite: Bally1982; Chu1983; Liszt2007). Additionally, due to the differences in zero-point energy between different isotopologs, isotopic exchange reactions can further alter $^{12}$C/$^{13}$C ratios in various molecules. For instance, the isotopic exchange reaction between $^{13}$C$^+$ and CO is exothermic, leading to an enrichment of $^{13}$C in CO and other molecules primarily formed through CO in cold environments (cite: Watson1976; Langer1984; Roueff2015; Colzi2020; Sipila2023).

Absorption lines against strong continuum sources can overcome such difficulties. The advantage of using absorption lines is to measure the optical depth as well as the column density precisely even if the transition is sub-thermally excited. Such a methodology has been widely used to quantify the physical properties of low-density gas (cite: Lucas1996; Lucas1998; Luo2020; Luo2023b; Rybarczyk2022a; Liszt2023; Gerin2024). (cite: Lucas1998) is one of the first works that measured the isotopic ratios in the solar neighborhood through millimeter molecular absorption lines. (cite: Liszt2018) measured the H$^{12}$CO$^+$/H$^{13}$CO$^+$ ratios in four directions toward the Galactic bulge, and they inferred a much higher value ($\sim$60) than the other tracers ($\sim$20). Inspired by these pioneering works, systematic measurements at different $R_{\rm GC}$ with such a methodology could be useful to constrain the $^{12}$C/$^{13}$C gradient.

In this work, we present a new measurement of the Galactic $^{12}$C/$^{13}$C gradient by using absorption lines of H$^{12}$CO$^+$ and H$^{13}$CO$^+$ with high-angular observations of the Atacama Large Millimeter/submillimeter Array (ALMA) and the Northern Extended Millimeter Array (NOEMA). We emphasize that such a methodology to constrain the isotopic gradient of the Milky Way with a large sample, especially for future searches in the anti-center direction (though rare and challenging), could provide valuable constraints for GCE models.

# Observations

## Quasar sight lines

We carried out H$^{12}$CO$^+$ and H$^{13}$CO$^+$ *J*=1-0 observations toward six quasars (Fig. [1](#fig:srn)). Five were observed with ALMA (2022.1.01438.S, PI: Thomas G. Bisbas) during March 20–30, 2023, and one source (3C 111) was observed with NOEMA (W20BB, PI: Gan Luo) in December 2020 and January 2021. The angular resolution of ALMA is $\sim$0.6$''$ at 89 GHz. The spectral resolution of ALMA is 122 kHz, corresponding to a velocity resolution of $\sim$0.4 km s$^{-1}$ at 89 GHz. The raw data was calibrated using the standard pipeline with the Common Astronomy Software Applications (cite: CASA2022). The imaging of the calibrated visibilities was performed using the *tclean* algorithm with Briggs weighting (robust = 0.5). The NOEMA observations have an angular resolution of $\sim$2.1$''$ at 89 GHz and a velocity resolution of $\sim$0.21 km s$^{-1}$. The PolyFiX backend of NOEMA covers H$^{12}$CN, H$^{13}$CN, HN$^{12}$C, and HN$^{13}$C *J*=1-0 transitions simultaneously. The calibration of the raw data was performed using clic software in the gildas.[^1] The typical optical depth noise levels are 3$\sim$7$\times$10$^{-3}$ per 0.4 km s$^{-1}$ velocity channel for ALMA observations and 2$\times$10$^{-3}$ per 0.21 km s$^{-1}$ velocity channel for NOEMA observations.

![](Figures/srn_MW.pdf)

## UCH ii sight lines

The ALMA observations toward ten UCH ii regions (red crosses in Fig. [1](#fig:srn)), which were selected from the ALMA Three-millimeter Observations of Massive Star-forming regions (ATOMS) survey (2019.1.00685.S, PI: Tie Liu), were observed from September to November 2019 with both 12-m and 7-m arrays at band 3. The baselines of ATOMS range from 15 to 783.5 m, corresponding to an angular resolution of $\sim$1.2$''$ at 89 GHz. The spectral resolution of H$^{12}$CO$^+$ and H$^{13}$CO$^+$ *J*=1-0 transitions are 0.2 km s$^{-1}$ and 0.422 km s$^{-1}$, respectively. The raw data were calibrated using CASA version 5.6, and the combination and imaging of 12-m and 7-m data were performed with CASA version 6.4.1. The sensitivity of the resultant spectra depends on the properties of each source, a detailed description of observations can be found in (cite: Liu2020).

# Results

## Absorption spectra and integrated optical depth

The absorption spectra of HCO$^+$ (hereafter, HCO$^+$ refers to H$^{12}$CO$^+$) and H$^{13}$CO$^+$[^2] were extracted from the continuum peak of each source. Figure [2](#fig:fig1) shows an example of normalized spectra of HCO$^+$ and H$^{13}$CO$^+$ toward J1851+0035. Spectra toward all other sources can be found in Appendix [6](#sec:a).

Since most of the sources are located in the Galactic plane ($|b| < 2^{\circ}$), the foreground absorption components are mixed, and it is difficult to decompose individual Gaussian components (except for the high-latitude source 3C111; see Appendix [7](#sec:b)). To obtain the column density ratios, we integrated the optical depths ($\int \tau_\nu d\upsilon$) of HCO$^+$ and H$^{13}$CO$^+$ in the same velocity range (shadowed region in Fig. [2](#fig:fig1) and [5](#fig:allspec)). We set four criteria when identifying the integrated range: 1) H$^{13}$CO$^+$ absorption should not be contaminated with absorption features of other molecules (e.g., $-25$ km s$^{-1}$ component of H$^{13}$CO$^+$ in Fig. [2](#fig:fig1)); 2) each of the integrated ranges of H$^{13}$CO$^+$ should be distinguished from the others (no overlap); 3) the absorption profile of HCO$^+$ should not be saturated ($e^{-\tau}$ \> rms); and 4) absorption spectra toward UCH ii regions should not be contaminated with emission features from the compact foreground envelopes. The uncertainty of $\int \tau_\nu d\upsilon$ ($\sigma_{\rm I}$) through an error propagation formula is thus defined by $$\begin{equation}
    \rm \sigma_I = \frac{d\upsilon}{2} \sqrt{\sum_{i=1}^{N-1} (\sigma_{\tau_i}^2+\sigma_{\tau_{i+1}}^2)},
\end{equation}$$ where ${\rm d\upsilon}$ is the channel width, N is the length of the data array in the velocity range over which the opacity profile is integrated, and ${\rm \sigma_{\tau_i} = RMS/e^{-\tau_i}}$ is the uncertainty of $\tau$ at the $i$th channel. The integrated optical depths of HCO$^+$ and H$^{13}$CO$^+$ toward all sources are listed in Table [\[table:tab2\]](#table:tab2).

The molecular column density can be written as a function of $\int \tau_\nu d\upsilon$ (cite: Mangum2015): $$\begin{equation}
N_{\rm tot} = \frac{3h}{8{\pi}^3\left | \mu_{\rm lu} \right |^2} \frac{Q_{\rm rot}}{g_{\rm u}} \frac{e^{\frac{E_{\rm u}}{kT_{\rm ex}}}} {e^{\frac{h\nu}{kT_{\rm ex}}}-1}  \int \tau_\nu d\upsilon,
\label{eq:n_tot}
\end{equation}$$ where $h$ is the Planck constant, $k$ is the Boltzman constant, $\left | \mu_{\rm lu} \right |^2$ is the dipole matrix element, $Q_{\rm rot}$ is the rotational partition function, $g_{\rm u}$ is the degeneracy of the upper energy level, $E_{\rm u}$ is the upper energy level, and $T_{\rm ex}$ is the excitation temperature. For each transition, $\left | \mu_{\rm lu} \right |^2$, $E_{\rm u}$, and the rest frequency $\nu$ were taken from the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005), and they are listed in Table [1](#tab:transitions). For linear molecules, the simplified partition function is given by (cite: McDowell1987) $$\begin{equation}
Q_{\rm tot} = \frac{kT}{hB_0} e^{\frac{hB_0}{3kT}} ,
\label{eq:q_tot}
\end{equation}$$ where $B_0$ is the rigid rotor rotation constant.

The excitation temperature of HCO$^+$ in diffuse molecular clouds is usually close to the cosmic microwave background temperature ($T_{\rm CMB}$ = 2.73 K) (cite: Godard2010; Luo2020). If we fill in all the constants in Eq. [\[eq:n_tot\]](#eq:n_tot) and take $T_{\rm ex} = 2.73$ K for both HCO$^+$ and H$^{13}$CO$^+$, the column density ratios can be simplified as $$\begin{equation}
    \frac{N_{\rm HCO^+}}{N_{\rm H^{13}CO^+}} = 0.974 \frac{\int \tau_{\rm HCO^+} d\upsilon}{\int \tau_{\rm H^{13}CO^+} d\upsilon}.
\end{equation}$$ Though $T_{\rm ex}$ of HCO$^+$ can rise above 2.73 K when the gas density is higher than 300 cm$^{-3}$ (cite: Rybarczyk2022b), a variance of $T_{\rm ex}$ from 2.73 to 5 K only results in a variance of the column density ratio of less than 1%. The calculated ratios in our samples range from 12.7$\pm$0.2[^3] to 139.4$\pm$38.0 (Table [\[table:tab1\]](#table:tab1)).

![](Figures/J1851+0035__spec.pdf)

## The $^{12}$C/$^{13}$C gradient

Obtaining an accurate distance of a distant molecular cloud is difficult, especially without parallax measurements from maser emissions. The most common estimation of such a distance is based on kinematic distance. We calculated the $R_{\rm GC}$ for each velocity component with the Monte Carlo kinematic distance method, using the latest rotational curve and updated solar motion parameters (cite: Wenger2018). This model is obtained through the trigonometric parallax results from the high-mass star-forming regions (HMSFRs) in the BeSSeL Survey (cite: Reid2014; Reid2019). This method samples the local standard of rest velocity ($V_{\rm lsr}$) and Galactic rotational curve parameters for HMSFRs and derives the probability density distribution (PDF) of kinematic distance, resulting in a median uncertainty of 13% to the parallax distances. A detailed description of this method can be found in (cite: Wenger2018).

The optical depth-weighted $V_{\rm lsr}$ in our samples is calculated by $$\begin{equation}
    V_{\rm lsr} = \frac{\int \upsilon \tau_{\rm HCO^+} d\upsilon}{\int \tau_{\rm HCO^+} d\upsilon}.
\end{equation}$$ The calculated $V_{\rm lsr}$ and $R_{\rm GC}$ as well as the uncertainties are listed in Table [\[table:tab1\]](#table:tab1). We note that such an estimation with pure circular motions may fail to predict the $R_{\rm GC}$ near the GC (e.g., the highly negative $V_{\rm lsr}$ toward J1720-3552), in which non-circular motions should be taken into account (cite: Liszt2018). Therefore, we used the tilted-disk model presented by (cite: Burton1978) to estimate the velocity components of $V_{\rm lsr} < -140$ km s$^{-1}$ toward J1720-3552, resulting in an $R_{\rm GC}$ between 1.24 to 1.5 kpc. Thus, we adopted a value of 1.37$\pm$0.04 kpc for this component.

Figure [3](#fig:fig2) shows the measured HCO$^+$/H$^{13}$CO$^+$ ratios as a function of $R_{\rm GC}$. The weighted-mean $^{12}$C/$^{13}$C ratios increase from 42$\pm$1 toward the GC to 66$\pm$5 in the solar neighborhood. To avoid an underestimation of the HCO$^+$ optical depth when $\tau$ is large, we set stricter constraints ($\tau < 3$) when fitting a gradient. We used the Markov chain Monte Carlo (MCMC) method within the $emcee$ code (cite: Foreman-Mackey2013) to sample the free parameters and the posterior probability distribution. The maximum likelihood fit of the data is shown with a red solid curve in Fig. [3](#fig:fig2), which gives a H$^{12}$CO$^+$/H$^{13}$CO$^+$ gradient as a function of $R_{\rm GC}$: $$\begin{equation}
    \rm \frac{H^{12}CO^+}{H^{13}CO^+} = (6.4\pm1.9) \frac{{\it R}_{GC}}{kpc} + (25.9\pm10.5).
\end{equation}$$

![](Figures/Rgc_r.pdf)

# Analysis and discussion

## The $^{12}$C/$^{13}$C ratios in the solar neighborhood

While the $^{12}$C/$^{13}$C ratios in the nearby molecular clouds have been derived extensively with various molecules, the most reliable tracer thought to represent the true element $^{12}$C/$^{13}$C ratios is CH$^+$ (cite: Ritchey2011). The measured $^{12}$C/$^{13}$ ratios from our HCO$^+$ samples range from 62.0$\pm$4.4 to 139.4$\pm$38.0 within 500 pc of the solar circle ($7.6 \leq R_{\rm GC} \leq 8.6$ kpc), with a weighted mean value of 66$\pm$5. This value is in good agreement with the mean value obtained through optical $^{12}$CH$^+$/$^{13}$CH$^+$ measurements toward diffuse sight lines (cite: Ritchey2011) and the $-0.9$ km s$^{-1}$ component of 3C 111 (Appendix [7](#sec:b)).

## The $^{12}$C/$^{13}$C ratios in the Galactic center

The measurements of the $^{12}$C/$^{13}$C ratio within $\sim$2 kpc of the GC are rare. This is mainly due to the high gas column density (e.g., $N_{\rm H_2} \gtrsim 10^{24}$ cm$^{-2}$), which makes the molecular transitions optically thick, even for the rare isotopologs (e.g., C$^{18}$O). (cite: Halfen2017) measured the isotopic ratios using complex organic molecules (COMs) toward Sgr B2(N) and found an average value of 24$\pm$7, which is similar to the value obtained from dense gas tracers (cite: Humire2020). The measurements from absorption lines of CH toward Sgr B2(M) and H$_2$CO toward Sgr B2 result in $^{12}$C/$^{13}$C ratios of 15.8$\pm$2.4 (cite: Jacob2020) and 11.48$\pm$0.03 (cite: Yan2019), respectively.

Previous absorption observations toward the Galactic bulge have revealed a significantly high $^{12}$C/$^{13}$C ratio (cite: Liszt2018). However, since these observations integrated the full velocity range, which has HCO$^+$ absorptions (the H$^{13}$CO$^+$ absorptions are much narrower), the absorption of HCO$^+$ could be contaminated with foreground diffuse gas, leading to a high value. Since the HCO$^+$ absorptions toward the dense regions (e.g., Sgr B2(N)) are completely saturated, the measured values at $R_{\rm GC} < 2$ kpc in our work are in fact the diffuse molecular components (cite: Gerin2017; Liszt2018).

The two measurements at $R_{\rm GC} < 2$ kpc from our observations have $^{12}$C/$^{13}$C ratios of 42.2$\pm$1.7 and 37.5$\pm$6.5, values which are consistent with absorption measurements of c-C$_3$H$_2$ (cite: Corby2018) but still larger than the other tracers in high-density ($n_{\rm H_2} > 10^5$ cm$^{-3}$) regions. Furthermore, the two lower limits of $^{12}$C/$^{13}$C at $-$181 and $-$162 km s$^{-1}$ of J1720-3552 are $>19$ and $>31$. These results are consistent with previous observations of CH$^+$ toward Sgr A$^*$ and Sgr B2(N) (cite: Godard2012), which is again distinct from the previously reported low values toward Sgr B2 but supports our results. Thus, either opacity effects or fractionation may have an impact on the measured isotopic ratios in the high-density tracers (e.g., CN, and COMs), while our measurements at low density are less influenced.

## The $^{12}$C/$^{13}$C gradient and comparison with GCE models

Different tracers have been used to calculate the Galactic $^{12}$C/$^{13}$C gradient. This gradient is mostly constrained by results from $\rm ^{12}C^{18}O/^{13}C^{18}O$ (cite: Langer1990; Langer1993; Wouterloot1996; Giannetti2014); $\rm ^{12}CN/^{13}CN$ (cite: Savage2002; Milam2005; Sun2024); H$_2^{12}$CO/H$_2^{13}$CO (cite: Henkel1982; Yan2019); C$^{34}$S (cite: Yan2023); and a combined analysis from various tracers (cite: Halfen2017; Jacob2020). The gradients from different methodologies are shown with different curves in Fig. [3](#fig:fig2).[^4]

By comparing the gradients using different tracers, we found that the measurements in the low-density molecular clouds (HCO$^+$, $n_{\rm H_2} \sim$ a few 10$^2$ cm$^{-3}$) are higher than those from higher density environments ($n_{\rm H_2}$ $\geq$ a few 10$^4$ cm$^{-3}$), such as C$^{18}$O, H$_2$CO, CS, and CN (cite: Giannetti2014; Yan2019; Yan2023; Sun2024). The systematically increasing trend of the $^{12}$C/$^{13}$C gradient from high-density to low-density gas may again suggest that fractionation plays a crucial role in the measured $^{12}$C/$^{13}$C ratios in molecules. Predictions from the chemical models by (cite: Colzi2020) are in agreement with this observational trend, finding that $^{12}$C/$^{13}$C ratios of HCN, HNC, and HCO$^+$ tend to increase from the higher (10$^6$ cm$^{-3}$) to the lower (10$^3$ cm$^{-3}$) densities.

The comparison between the derived $^{12}$C/$^{13}$C gradient and the GCE models presented in (cite: Colzi2022) is shown in Fig. [4](#fig:fig3), in which the models consider different mass ranges for white dwarf progenitors and average ejected masses of $^{13}$C and $^{15}$N per nova outburst (cite: Romano2019; Romano2021). Our result is reasonably consistent with the GCE models with a mass range of white dwarf progenitors 1–8 M$_\odot$ and higher average ejected masses of $^{13}$C (models 3 and 4). Given the limited range of $R_{\rm GC}$ in the current samples, future observations at $R_{\rm GC} > 10$ kpc would be exceptionally useful to constrain GCE models.

However, one should always keep in mind that the formula of the isotopic gradient strongly depends on the accuracy of the $R_{\rm GC}$, which is mostly based on the kinematic distance estimation. For instance, the estimated $R_{\rm GC}$ before and after the model by (cite: Reid2019) could differ by several kpc (cite: Sun2024). The large scatter of $^{12}$C/$^{13}$C at $R_{\rm GC}$ between 4 kpc to 8 kpc in both our work and the literature may suggest that our understanding of the Milky Way rotational model or inhomogeneous mixing of the elements may also contribute to the scatter.

![](Figures/Rgc_GCE.pdf)

## Chemical effects on the measured $^{12}$C/$^{13}$C ratios

The isotopic exchange reactions could be one of the main processes that lead to different isotopic ratios in HCO$^+$. In this section, we consider the isotopic exchange reaction that produces H$^{13}$CO$^+$ (cite: Langer1978; Roueff2015; Colzi2020)[^5]: $$\begin{align}
\rm ^{13}C^+ + CO \rightleftharpoons &\ \rm ^{13}CO + C \tag{R1},\label{r:R1}\\
\rm ^{13}CO + HCO^+ \rightleftharpoons &\ \rm H^{13}CO^+ + CO \tag{R2}.
\label{r:R2}
\end{align}$$

We considered the main formation pathways of H$^{13}$CO$^+$ in low-to-intermediate density gas (cite: vanDishoeck1988; Luo2023b): $$\begin{align}
\rm ^{13}CO^+ + H_2 \rightarrow &\ \rm H^{13}CO^+ + H \tag{R3},\label{r:R3}\\
\rm ^{13}C^+ + H_2O \rightarrow &\ \rm H^{13}CO^+ + H \tag{R4},\label{r:R4}\\
\rm ^{13}CH + O \rightarrow &\ \rm H^{13}CO^+ + e \tag{R5}.
\label{r:R5}
\end{align}$$ The destruction of HCO$^+$ (and H$^{13}$CO$^+$) is dominated by electrons: $$\begin{equation}
    \rm HCO^+ + e^- \rightarrow CO + H \tag{R6}.
    \label{r:R6}
\end{equation}$$ Thus, the isotopic exchange reaction would influence the HCO$^+$/H$^{13}$CO$^+$ ratio only if the right side reaction [\[r:R2\]](#r:R2) is comparable to reactions [\[r:R3\]](#r:R3) $\sim$ [\[r:R5\]](#r:R5). The reaction rate of the above reaction is $2.6\times10^{-10}\times(T/300)^{-0.4}$ cm$^{3}$ s$^{-1}$ (cite: Roueff2015). The typical abundance of CO$^+$ is $10^{-10} \sim 10^{-9}$(cite: Stauber2009; Trevino-Morales2016), the abundance of HCO$^+$ is a few $10^{-9}$(cite: Lucas1996; Gerin2019; Luo2020), and the abundance of CH is $3\times10^{-8}$ (cite: Liszt2002; Sheffer2008; Tang2021; Luo2023a). Even if we only consider reaction [\[r:R3\]](#r:R3) (the reaction rate k = $7.5\times10^{-10}$ cm$^{3}$ s$^{-1}$; (cite: McElroy2013)) and scale the above abundance with $^{12}$C/$^{13}$C = 70, the formation of H$^{13}$CO$^+$ through reaction [\[r:R3\]](#r:R3) would overwhelm reaction [\[r:R2\]](#r:R2) by over four orders of magnitude at the typical gas temperature of $\sim$50 K (cite: Snow2006). Therefore, fractionation would have little impact on the measured HCO$^+$/H$^{13}$CO$^+$ ratios in low-density gas. This is also consistent with various chemical modelings of carbon fractionation, in which HCO$^+$/H$^{13}$CO$^+$ can overall best represent the original $^{12}$C/$^{13}$C element ratio in low-to-intermediate density gas (cite: Szucs2014; Roueff2015; Colzi2020; Sipila2023).

In dense regions, CO becomes the precursor of HCO$^+$ (cite: Dalgarno2006; Indriolo2012; Bisbas2015): $$\begin{equation}
    \rm CO + H_3^+ \rightarrow HCO^+ + H_2 \tag{R7}.
    \label{r:R7}
\end{equation}$$ Since reaction [\[r:R6\]](#r:R6) is still the dominant formation channel of CO even in high-density clouds (cite: Luo2023a), the fractionation of CO in the dense cloud could greatly impact the isotopic ratio in HCO$^+$ only if reaction [\[r:R7\]](#r:R7) is comparable to reaction [\[r:R6\]](#r:R6). However, the gas density that will significantly alter the $^{12}$C/$^{13}$C ratio measured in HCO$^+$ would be above 10$^4$ cm$^{-3}$ (cite: Sipila2023).

The highest column density of HCO$^+$ in Table [\[table:tab1\]](#table:tab1) is $\sim 3.4\times10^{13}$ cm$^{-2}$, corresponding to an H$_2$ column density of $10^{22}$ cm$^{-2}$, assuming a constant HCO$^+$ abundance (cite: Lucas1996; Liszt2016)[^6] Therefore, most components are not expected to trace such a high-density regime and will be less influenced by the fractionation effect. Nevertheless, both detailed chemical modeling (Colzi et al. in prep) and the constraints of gas volume density and temperature through multiple lines in the future are necessary to determine where and how fractionation impacts the isotopic ratios.

# Conclusion

In this work, we have performed high sensitivity absorption line observations toward strong continuum sources (including quasars and UCH ii regions). We derived $^{12}$C/$^{13}$C ratios from HCO$^+$ absorption and $R_{\rm GC}$ according to the latest parallax-based distance calculation. Our main conclusions are as follows:

1.  The derived $^{12}$C/$^{13}$C gradient from HCO$^+$ absorption measurements is (6.4$\pm$1.9)$R_{\rm GC}$/kpc+(25.9$\pm$10.5), which is reasonably consistent with current GCE models.

2.  The derived weighted mean $^{12}$C/$^{13}$C ratio in the solar neighborhood is 66$\pm$5, which is consistent with those measured from CH$^+$ (74.4$\pm$7.6).

3.  Our measurements toward the GC are two to three times higher than those measured with dense gas tracers toward Sgr B2 (11$\sim$24). Nevertheless, our results are supported by the CH$^+$ observations toward Sgr A$^*$ and Sgr B2(N) ($>$30) as well as absorption measurements of c-C$_3$H$_2$ ($\sim$40).

4.  The discrepancy between our method and those from dense gas tracers suggests that opacity effects and fractionation may have a larger impact on the dense gas tracers in high-density regions.

We highlight the use of absorption lines to measure the isotopic ratios with interferometry observations, which are less affected by optical depth, beam dilution, and chemical fractionation. Future large samples toward the GC and the anti-center directions may provide more constraints on the Galactic $^{12}$C/$^{13}$C gradient as well as the GCE models.

# Acknowledgements

We are grateful to the anonymous referee for the thoughtful comments and suggestions that greatly improved the clarity of our work, especially the suggestion of including the non-circular motion to estimate the distance near the GC. We thank Zhiyu Zhang, J$\rm {\acute{e}}$r$\rm {\hat{o}}$me Pety, and Michel Gu$\rm {\acute{e}}$lin for their useful comments, Donatella Romano for providing the GCE models, and the staffs at IRAM for carrying out the NOEMA observations and reducing the data. L. C acknowledges support from the grant No. PID2022-136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. Tie Liu acknowledges the supports by the National Key R&D Program of China (No. 2022YFA1603100), National Natural Science Foundation of China (NSFC) through grants No.12073061 and No.12122307, and the Tianchi Talent Program of Xinjiang Uygur Autonomous Region. D. L. is a New Cornerstone investigator. N.-Y. Tang is sponsored by the University Annual Scientific Research Plan of Anhui Province (No. 2023AH030052, No. 2022AH010013), the China Manned Space Program through its Space Application System, Zhejiang Lab Open Research Project (No. K2022PE0AB01). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01438.S and ADS/JAO.ALMA#2019.1.00685.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work is based on observations carried out under project number W20BB with the IRAM NOEMA Interferometer. IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain).

72 natexlab

(ref: Bally1982) Bally, J. & Langer, W. D. 1982, ApJ, 255, 143

(ref: Bisbas2015) Bisbas, T. G., Papadopoulos, P. P., & Viti, S. 2015, ApJ, 803, 37

(ref: Burton1978) Burton, W. B. & Liszt, H. S. 1978, ApJ, 225, 815

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chu1983) Chu, Y. H. & Watson, W. D. 1983, ApJ, 267, 151

(ref: Clayton2003) Clayton, D. 2003, Handbook of Isotopes in the Cosmos

(ref: Colzi2022) Colzi, L., Romano, D., Fontani, F., et al. 2022, A&A, 667, A151

(ref: Colzi2020) Colzi, L., Sipilä, O., Roueff, E., Caselli, P., & Fontani, F. 2020, A&A, 640, A51

(ref: Corby2018) Corby, J. F., McGuire, B. A., Herbst, E., & Remijan, A. J. 2018, A&A, 610, A10

(ref: Dalgarno2006) Dalgarno, A. 2006, Proceedings of the National Academy of Science, 103, 12269

(ref: Foreman-Mackey2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: Gerin2017) Gerin, M. & Liszt, H. 2017, A&A, 600, A48

(ref: Gerin2019) Gerin, M., Liszt, H., Neufeld, D., et al. 2019, A&A, 622, A26

(ref: Gerin2024) Gerin, M., Liszt, H., Pety, J., & Faure, A. 2024, A&A, 686, A49

(ref: Giannetti2014) Giannetti, A., Wyrowski, F., Brand, J., et al. 2014, A&A, 570, A65

(ref: Godard2010) Godard, B., Falgarone, E., Gerin, M., Hily-Blant, P., & de Luca, M. 2010, A&A, 520, A20

(ref: Godard2012) Godard, B., Falgarone, E., Gerin, M., et al. 2012, A&A, 540, A87

(ref: Guesten1982) Guesten, R. & Mezger, P. G. 1982, Vistas in Astronomy, 26, 159

(ref: Halfen2017) Halfen, D. T., Woolf, N. J., & Ziurys, L. M. 2017, ApJ, 845, 158

(ref: Henkel1982) Henkel, C., Wilson, T. L., & Bieging, J. 1982, A&A, 109, 344

(ref: Humire2020) Humire, P. K., Thiel, V., Henkel, C., et al. 2020, A&A, 642, A222

(ref: Iben1983) Iben, I., J. & Renzini, A. 1983, ARA&A, 21, 271

(ref: Indriolo2012) Indriolo, N. & McCall, B. J. 2012, ApJ, 745, 91

(ref: Jacob2020) Jacob, A. M., Menten, K. M., Wiesemeyer, H., et al. 2020, A&A, 640, A125

(ref: Kobayashi2020) Kobayashi, C., Karakas, A. I., & Lugaro, M. 2020, ApJ, 900, 179

(ref: Kobayashi2011) Kobayashi, C., Karakas, A. I., & Umeda, H. 2011, MNRAS, 414, 3231

(ref: Langer1984) Langer, W. D., Graedel, T. E., Frerking, M. A., & Armentrout, P. B. 1984, ApJ, 277, 581

(ref: Langer1990) Langer, W. D. & Penzias, A. A. 1990, ApJ, 357, 477

(ref: Langer1993) Langer, W. D. & Penzias, A. A. 1993, ApJ, 408, 539

(ref: Langer1978) Langer, W. D., Wilson, R. W., Henry, P. S., & Guelin, M. 1978, ApJL, 225, L139

(ref: Liszt2018) Liszt, H. & Gerin, M. 2018, A&A, 610, A49

(ref: Liszt2023) Liszt, H. & Gerin, M. 2023, ApJ, 943, 172

(ref: Liszt2002) Liszt, H. & Lucas, R. 2002, A&A, 391, 693

(ref: Liszt2007) Liszt, H. S. 2007, A&A, 476, 291

(ref: Liszt2016) Liszt, H. S. & Gerin, M. 2016, A&A, 585, A80

(ref: Liu2020) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020, MNRAS, 496, 2790

(ref: Lucas1996) Lucas, R. & Liszt, H. 1996, A&A, 307, 237

(ref: Lucas1998) Lucas, R. & Liszt, H. 1998, A&A, 337, 246

(ref: Luo2020) Luo, G., Li, D., Tang, N., et al. 2020, ApJL, 889, L4

(ref: Luo2023a) Luo, G., Zhang, Z.-Y., Bisbas, T. G., et al. 2023a, ApJ, 942, 101

(ref: Luo2023b) Luo, G., Zhang, Z.-Y., Bisbas, T. G., et al. 2023b, ApJ, 946, 91

(ref: Maeder1983) Maeder, A. 1983, A&A, 120, 113

(ref: Mangum2015) Mangum, J. G. & Shirley, Y. L. 2015, PASP, 127, 266

(ref: McDowell1987) McDowell, R. S. 1987, JQSRT, 38, 337

(ref: McElroy2013) McElroy, D., Walsh, C., Markwick, A. J., et al. 2013, A&A, 550, A36

(ref: Milam2005) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126

(ref: Muller2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: Muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: Reid2019) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2019, ApJ, 885, 131

(ref: Reid2014) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, ApJ, 783, 130

(ref: Ritchey2011) Ritchey, A. M., Federman, S. R., & Lambert, D. L. 2011, ApJ, 728, 36

(ref: Romano2021) Romano, D., Magrini, L., Randich, S., et al. 2021, A&A, 653, A72

(ref: Romano2019) Romano, D., Matteucci, F., Zhang, Z.-Y., Ivison, R. J., & Ventura, P. 2019, MNRAS, 490, 2838

(ref: Romano2017) Romano, D., Matteucci, F., Zhang, Z. Y., Papadopoulos, P. P., & Ivison, R. J. 2017, MNRAS, 470, 401

(ref: Roueff2015) Roueff, E., Loison, J. C., & Hickson, K. M. 2015, A&A, 576, A99

(ref: Rybarczyk2022b) Rybarczyk, D. R., Gong, M., Stanimirović, S., et al. 2022a, ApJ, 926, 190

(ref: Rybarczyk2022a) Rybarczyk, D. R., Stanimirović, S., Gong, M., et al. 2022b, ApJ, 928, 79

(ref: Savage2002) Savage, C., Apponi, A. J., Ziurys, L. M., & Wyckoff, S. 2002, ApJ, 578, 211

(ref: Sheffer2008) Sheffer, Y., Rogers, M., Federman, S. R., et al. 2008, ApJ, 687, 1075

(ref: Sipila2023) Sipilä, O., Colzi, L., Roueff, E., et al. 2023, A&A, 678, A120

(ref: Snow2006) Snow, T. P. & McCall, B. J. 2006, ARA&A, 44, 367

(ref: Stauber2009) Stäuber, P. & Bruderer, S. 2009, A&A, 505, 195

(ref: Sun2024) Sun, Y., Zhang, Z.-Y., Wang, J., et al. 2024, MNRAS, 527, 8151

(ref: Szucs2014) Szűcs, L., Glover, S. C. O., & Klessen, R. S. 2014, MNRAS, 445, 4055

(ref: Tang2021) Tang, N., Li, D., Luo, G., et al. 2021, ApJS, 257, 47

(ref: Trevino-Morales2016) Treviño-Morales, S. P., Fuente, A., Sánchez-Monge, Á., et al. 2016, A&A, 593, L12

(ref: vanDishoeck1988) van Dishoeck, E. F. & Black, J. H. 1988, ApJ, 334, 771

(ref: Watson1976) Watson, W. D., Anicich, V. G., & Huntress, W. T., J. 1976, ApJL, 205, L165

(ref: Wenger2018) Wenger, T. V., Balser, D. S., Anderson, L. D., & Bania, T. M. 2018, ApJ, 856, 52

(ref: Wouterloot1996) Wouterloot, J. G. A. & Brand, J. 1996, A&AS, 119, 439

(ref: Yan2023) Yan, Y. T., Henkel, C., Kobayashi, C., et al. 2023, A&A, 670, A98

(ref: Yan2019) Yan, Y. T., Zhang, J. S., Henkel, C., et al. 2019, ApJ, 877, 154

# Absorption spectra toward all sources

The normalized absorption profiles of 14 sources are shown in Fig. [5](#fig:allspec). Note that for the UCH ii sight lines, the H40$\alpha$ emissions are usually associated with UCH ii regions (cite: Liu2020) (e.g., $-150 \sim -80$ km s$^{-1}$ toward I15254+5621), this is not the bad baseline. Furthermore, since the emission from the compact structures around UCH ii regions could have a high excitation temperature, the spectra may still show emission in conjunction with absorption. We avoid these velocity ranges in our calculation. Future high angular resolution and high sensitivity observations may help reconstruct both the emission and absorption profiles around UCH ii regions.

![](Figures/Spec1.pdf)

# Gaussian decomposition of absorption profiles toward 3C 111

Absorption profiles and Gaussian decomposition of H$^{12}$CN, H$^{13}$CN, HN$^{12}$C, and HN$^{13}$C *J*=1-0 transitions toward 3C 111 are shown in Fig. [6](#fig:3c111), in which the spectra of H$^{12}$CN and H$^{13}$CN are hyperfine transitions. The Gaussian decomposition is performed with $curve\_fit$ package in $scipy$ using the Levenberg-Marquardt algorithm, and the resultant optical depths and linewidth ($\Delta V$) are shown in Table [\[table:tab1\]](#table:tab1). We set constraints when fitting hyperfine transitions that all hyperfine lines have 1) the same linewidth ($\Delta V$) and 2) the same velocity offset with respect to $V_{\rm lsr}$.

There are two velocity components ($-0.9$ km s$^{-1}$ and $-2.5$ km s$^{-1}$) in front of 3C 111, the 3D extinction indicates that the cloud is within 300 pc from the Sun (cite: Lucas1998). The gas volume density at $-0.9$ km s$^{-1}$ is $n_{\rm H_2} = 398\pm22$ cm$^{-3}$ (Luo et al. in prep), and $n_{\rm H_2}$ is supposed to be much lower at $-2.5$ km s$^{-1}$ than at $-0.9$ km s$^{-1}$ (cite: Lucas1998). However, the HCO$^+$ absorption profile is almost saturated toward 3C 111 and we cannot get a good Gaussian decomposition. Thus, we use HCN and HNC to derive the $^{12}$C/$^{13}$C ratio. The optical depth ratios of the H$^{12}$CN hyperfine transitions are 1:2.3:3.5 and 1:2.9:4.6 at $-$0.9 km s$^{-1}$ and $-$2.5 km s$^{-1}$, respectively. While the latter represents the intrinsic line ratio (1:3:5), the former deviates from it by 30%, indicating that the optical depths of the H$^{12}$CN (F=1–1 and 2–1) at $-$0.9 km s$^{-1}$ are underestimated. As an alternative, we can fix the optical depth ratios at 1:3:5 instead of treating them as free parameters to obtain a more accurate value of the column density.

The $^{12}$C/$^{13}$C ratio at $-0.9$ km s$^{-1}$ derived from H$^{12}$CN/H$^{13}$CN is 74$\pm$3, which is 30% higher than that previously obtained by (cite: Lucas1998). Measurement from HN$^{12}$C/HN$^{13}$C (62$\pm$6) also show similar result. The $^{12}$C/$^{13}$C ratio at $-2.5$ km s$^{-1}$ component derived from H$^{12}$CN/H$^{13}$CN is 138$\pm$28, which is $\sim$2 times higher than that at $-0.9$ km s$^{-1}$. As suggested by (cite: Lucas1998), this could be a particular case, where the $^{13}$CO has been enriched and fractionation leads to a deficit of $^{13}$C in less abundant carbon carriers. Chemical models that consider the isotopic fractionation also predict a higher isotopic ratio of H$^{12}$CN/H$^{13}$CN than that from CO or HCO$^+$ (cite: Roueff2015; Colzi2020). Our detection of HN$^{13}$C at $-2.5$ kms s$^{-1}$ (S/N of $\int \tau dv$ $\sim$ 4) is consistent with the hypothesis (HN$^{12}$C/HN$^{13}$C = $95\pm39$).

![](Figures/Spec2.pdf)

+------------+------------------------------------------------+------------------------------------------------+---+
| Molecules  | $-0.9$ km s$^{-1}$                             | $-2.5$ km s$^{-1}$                             |   |
+:==========:+:===================:+:========================:+:===================:+:========================:+:=:+
| 2-3        | $\tau$              | $\Delta V$ (km s$^{-1}$) | $\tau$              | $\Delta V$ (km s$^{-1}$) |   |
+------------+---------------------+--------------------------+---------------------+--------------------------+---+
| H$^{12}$CN | 1.21$\pm$0.02$^{a}$ | 0.94$\pm$0.01            | 0.42$\pm$0.02$^{a}$ | 0.93$\pm$0.01            |   |
+------------+---------------------+--------------------------+---------------------+--------------------------+---+
| H$^{13}$CN | 0.082$\pm$0.002     | 0.90$\pm$0.03            | 0.013$\pm$0.002     | 1.1$\pm$0.2              |   |
+------------+---------------------+--------------------------+---------------------+--------------------------+---+
| HN$^{12}$C | 2.14$\pm$0.03       | 1.03$\pm$0.01            | 0.595$\pm$0.008     | 1.0$\pm$0.2              |   |
+------------+---------------------+--------------------------+---------------------+--------------------------+---+
| HN$^{13}$C | 0.028$\pm$0.002     | 0.94$\pm$0.07            | 0.005$\pm$0.002     | 0.95$\pm$0.4             |   |
+------------+---------------------+--------------------------+---------------------+--------------------------+---+

Table notes:

# The source properties

The derived source properties from Sect. [3](#sec:results) are shown in Table [\[table:tab2\]](#table:tab2).

| Source | $V_{\rm lsr}$ | $R_{\rm GC}$ | $\int \tau_{\rm H^{12}CO^+} d\upsilon$ | $\int \tau_{\rm H^{13}CO^+} d\upsilon$ | $N_{\rm H^{12}CO^+}$/$N_{\rm H^{13}CO^+}$ | RMS |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 2-7 | km s$^{-1}$ | kpc | km s$^{-1}$ | km s$^{-1}$ |  | $10^{-3}$ |
| I15254-5621 | -54.0$\pm$0.7 | 6.0$^{+0.2}_{-0.2}$ | 1.944$\pm$0.017 | 0.019$\pm$0.007 | 101.8$\pm$37.4 | 11.7 |
| I15254-5621 | -30.4$\pm$0.3 | 6.8$^{+0.2}_{-0.2}$ | 3.166$\pm$0.023 | 0.038$\pm$0.010 | 82.1$\pm$21.5 | 11.7 |
| I15502-5302 | -75.3$\pm$0.8 | 5.1$^{+0.1}_{-0.2}$ | 1.787$\pm$0.013 | 0.038$\pm$0.003 | 46.0$\pm$4.0 | 9.0 |
| I15502-5302 | -40.0$\pm$0.3 | 6.3$^{+0.2}_{-0.2}$ | 8.526$\pm$0.048 | 0.127$\pm$0.006 | 65.1$\pm$3.0 | 9.0 |
| I15567-5236 | -86.6$\pm$2.3 | 4.7$^{+0.1}_{-0.2}$ | 7.101$\pm$0.130 | 0.072$\pm$0.026 | 96.6$\pm$35.0 | 30.9 |
| I15567-5236 | -65.9$\pm$1.4 | 5.3$^{+0.2}_{-0.1}$ | 3.254$\pm$0.047 | 0.060$\pm$0.021 | 52.9$\pm$18.2 | 30.9 |
| I15567-5236 | -46.0$\pm$1.6 | 6.0$^{+0.2}_{-0.2}$ | 12.476$\pm$0.307 | 0.197$\pm$0.024 | 61.6$\pm$7.7 | 30.9 |
| I15567-5236 | -16.4$\pm$1.0 | 7.3$^{+0.2}_{-0.2}$ | 11.112$\pm$0.489 | 0.091$\pm$0.026 | 118.4$\pm$34.0 | 30.9 |
| I16060-5146 | -80.0$\pm$0.5 | 4.7$^{+0.2}_{-0.2}$ | 2.381$\pm$0.011 | 0.037$\pm$0.003 | 62.6$\pm$4.7 | 4.5 |
| I16060-5146 | -56.7$\pm$0.2 | 5.5$^{+0.2}_{-0.2}$ | 10.094$\pm$0.022 | 0.159$\pm$0.005 | 62.0$\pm$2.0 | 4.5 |
| I16164-5046 | -48.0$\pm$1.5 | 5.7$^{+0.2}_{-0.2}$ | 5.727$\pm$0.126 | 0.106$\pm$0.005 | 52.5$\pm$2.7 | 8.9 |
| I16164-5046 | -38.7$\pm$0.3 | 6.1$^{+0.2}_{-0.2}$ | 2.976$\pm$0.016 | 0.043$\pm$0.005 | 67.5$\pm$8.3 | 8.9 |
| I16164-5046 | -22.5$\pm$0.2 | 6.8$^{+0.2}_{-0.2}$ | 1.676$\pm$0.009 | 0.032$\pm$0.004 | 50.9$\pm$7.1 | 8.9 |
| I16172-5028 | -41.3$\pm$0.4 | 5.9$^{+0.2}_{-0.2}$ | 6.853$\pm$0.043 | 0.096$\pm$0.006 | 69.5$\pm$4.4 | 8.0 |
| I18479-0005 | 70.8$\pm$0.6 | 5.2$^{+0.2}_{-0.1}$ | 6.478$\pm$0.036 | 0.113$\pm$0.012 | 55.7$\pm$6.1 | 11.7 |
| I18507+0110 | 11.6$\pm$0.2 | 7.6$^{+0.2}_{-0.2}$ | 4.714$\pm$0.056 | 0.074$\pm$0.006 | 62.0$\pm$4.8 | 11.4 |
| I18507+0110 | 27.3$\pm$0.4 | 6.9$^{+0.2}_{-0.2}$ | 2.579$\pm$0.027 | 0.029$\pm$0.005 | 87.7$\pm$14.2 | 11.4 |
| I18507+0110 | 48.3$\pm$0.4 | 6.0$^{+0.2}_{-0.2}$ | 3.619$\pm$0.021 | 0.043$\pm$0.006 | 82.5$\pm$12.1 | 11.4 |
| I18507+0110 | 52.2$\pm$0.9 | 5.9$^{+0.1}_{-0.2}$ | 8.472$\pm$0.109 | 0.123$\pm$0.006 | 67.3$\pm$3.5 | 11.4 |
| I19078+0901 | 39.4$\pm$2.8 | 6.7$^{+0.2}_{-0.2}$ | 8.199$\pm$0.404 | 0.154$\pm$0.008 | 52.0$\pm$3.8 | 11.4 |
| I19078+0901 | 59.6$\pm$0.6 | 6.0$^{+0.2}_{-0.1}$ | 15.748$\pm$0.106 | 0.188$\pm$0.012 | 81.6$\pm$5.3 | 11.4 |
| J1603-4904 | -27.0$\pm$0.2 | 6.7$^{+0.2}_{-0.2}$ | 5.195$\pm$0.026 | 0.072$\pm$0.010 | 70.4$\pm$9.6 | 6.0 |
| J1603-4904 | 2.8$\pm$0.1 | 8.5$^{+0.2}_{-0.2}$ | 3.352$\pm$0.043 | 0.036$\pm$0.007 | 91.6$\pm$16.9 | 6.0 |
| J1720-3552 | -181.4$\pm$1.6 | 1.37$^{+0.04}_{-0.04}$$^{a}$ | 0.927$\pm$0.005 | $<$0.047$^{b}$ | $>19$ | 3.4 |
| J1720-3552 | -161.9$\pm$2.4 | 1.37$^{+0.04}_{-0.04}$$^{a}$ | 0.679$\pm$0.007 | $<$0.021 | $>31$ | 3.4 |
| J1720-3552 | -140.9$\pm$1.0 | 1.37$^{+0.04}_{-0.04}$$^{a}$ | 1.426$\pm$0.007 | 0.037$\pm$0.006 | 37.5$\pm$6.5.5 | 3.4 |
| J1720-3552 | -104.6$\pm$1.3 | 1.3$^{+0.0}_{-0.0}$ | 6.219$\pm$0.056 | 0.144$\pm$0.005 | 42.2$\pm$1.7 | 3.4 |
| J1720-3552 | -31.7$\pm$0.1 | 4.2$^{+0.2}_{-0.2}$ | 10.925$\pm$0.019 | 0.227$\pm$0.011 | 46.8$\pm$2.3 | 3.4 |
| J1720-3552 | -22.0$\pm$0.2 | 5.0$^{+0.2}_{-0.2}$ | 2.321$\pm$0.018 | 0.178$\pm$0.004 | 12.7$\pm$0.3 | 3.4 |
| J1720-3552 | -7.9$\pm$0.0 | 6.8$^{+0.3}_{-0.3}$ | 34.042$\pm$0.124 | 0.784$\pm$0.012 | 42.3$\pm$0.7 | 3.4 |
| J1720-3552 | 6.3$\pm$0.1 | 6.9$^{+0.1}_{-0.1}$ | 3.447$\pm$0.021 | 0.043$\pm$0.005 | 78.6$\pm$9.5 | 3.4 |
| J1832-1035 | 7.1$\pm$0.2 | 7.6$^{+0.2}_{-0.2}$ | 6.393$\pm$0.136 | 0.045$\pm$0.013 | 139.4$\pm$41.9 | 3.7 |
| J1832-1035 | 70.9$\pm$0.3 | 4.3$^{+0.1}_{-0.1}$ | 10.348$\pm$0.032 | 0.140$\pm$0.018 | 72.1$\pm$9.2 | 3.7 |
| J1851+0035 | 14.5$\pm$0.2 | 7.5$^{+0.2}_{-0.2}$ | 9.555$\pm$0.077 | 0.093$\pm$0.021 | 99.6$\pm$22.7 | 5.5 |
| J1851+0035 | 32.5$\pm$0.4 | 6.6$^{+0.2}_{-0.2}$ | 1.971$\pm$0.017 | 0.023$\pm$0.011 | 82.6$\pm$40.8 | 5.5 |
| J1851+0035 | 55.6$\pm$1.1 | 5.8$^{+0.2}_{-0.2}$ | 11.614$\pm$0.162 | 0.136$\pm$0.019 | 83.4$\pm$11.8 | 5.5 |
| J1922+1530 | 5.8$\pm$0.1 | 8.0$^{+0.2}_{-0.2}$ | 3.135$\pm$0.024 | 0.025$\pm$0.010 | 123.7$\pm$47.7 | 6.9 |
| J1922+1530 | 40.9$\pm$1.1 | 6.8$^{+0.2}_{-0.2}$ | 8.187$\pm$0.156 | 0.116$\pm$0.009 | 68.8$\pm$5.3 | 6.9 |
| J1922+1530 | 55.9$\pm$1.1 | 6.3$^{+0.2}_{-0.1}$ | 3.238$\pm$0.044 | 0.042$\pm$0.007 | 75.2$\pm$13.4 | 6.9 |

Table notes:

# The Molecular transitions

The molecular transitions mentioned in this work are taken from the CDMS database (cite: Muller2001; Muller2005), which are listed in Table [1](#tab:transitions).

| Transition | $\nu$ | $\left | \mu_{\rm lu} \right |^2$ | $E_{\rm u}$ |
|:--:|:--:|:--:|:--:|
| 2-4 | MHz | Debye$^2$ | K |
| H$^{12}$CO$^+$ (1-0) | 89188.5247 | 15.21 | 4.28 |
| H$^{13}$CO$^+$ (1-0) | 86754.2884 | 15.21 | 4.16 |
| H$^{12}$CO (1/2-1/2, F=1-1) | 86777.46 | 1.86 | 4.18 |
| H$^{12}$CN (1-0, F=1-1) | 88630.4156 | 8.9 | 4.25 |
| H$^{12}$CN (1-0, F=2-1) | 88631.8475 | 8.9 | 4.25 |
| H$^{12}$CN (1-0, F=0-1) | 88633.9357 | 8.9 | 4.25 |
| H$^{13}$CN (1-0, F=1-1) | 86338.7352 | 8.9 | 4.14 |
| H$^{13}$CN (1-0, F=2-1) | 86340.1666 | 8.9 | 4.14 |
| H$^{13}$CN (1-0, F=0-1) | 86342.2543 | 8.9 | 4.14 |
| HN$^{12}$C (1-0) | 90663.568 | 9.3 | 4.35 |
| HN$^{13}$C (1-0) | 87090.85 | 7.28 | 4.18 |

: Molecular transitions mentioned in this work.

# The unusual low H$^{12}$CO$^+$/H$^{13}$CO$^+$ toward J1720-3552

The $-22$ km s$^{-1}$ velocity component was recognized as an independent component in the H$^{13}$CO$^+$ line profiles when we calculated the H$^{12}$CO$^+$/H$^{13}$CO$^+$ ratios. The derived isotopic ratio is more than three times lower than the components toward the GC; however, the reason is still unclear. If this low value is caused by chemical fractionation, the gas component at $-22$ km s$^{-1}$ must have a high density and compact size ($\leq$0.01 pc at a distance of $\sim$ 3 kpc; otherwise, we would see emission lines around the continuum source). It should be surrounded by low-density envelopes since the H$^{12}$CO$^+$/H$^{13}$CO$^+$ ratios toward the neighboring velocity components are much higher. Future high-$J$ molecular line observations may help reveal the nature of this low value.

[^1]: https://www.iram.fr/IRAMFR/GILDAS

[^2]: All transitions refers to *J*=1-0 rotational transition unless otherwise noted.

[^3]: However, this low value ($< 30$) is only derived at $V_{\rm lsr} = -22$ km s$^{-1}$ toward J1720-3552; see Appendix [10](#sec:e) for more detail.

[^4]: For different works using the same tracer, we adopted the latest gradient.

[^5]: The forward reaction only has high efficiency ($\geq$ 50%) in cold environments (e.g., $T_{\rm k} < 30$ K).

[^6]: However, since the integrated velocity range is over 20 km/,s$^{-1}$ and contains a few velocity components, the actual column density of each component should be a few fractions of the total.

</paper>

Write the methods card for this paper.