# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...648A..38G\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...648A..38G",
 "title": "CO<SUP>+</SUP> as a probe of the origin of CO in diffuse interstellar clouds",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Gerin, M.",
 "n_authors": 2,
 "arxiv_id": "2102.09861",
 "doi": "10.1051/0004-6361/202039915",
 "alma_projects_linked_by_archive": [
  "2019.1.00120.S"
 ]
}
```

Paper text:
<paper>
# CO$^+$ as a probe of the origin of CO in diffuse interstellar clouds

The chemistry of the diffuse interstellar medium is driven by the combined influences of cosmic rays, ultraviolet (UV) radiation and turbulence. Previously detected at the outer edges of photo-dissociation regions (PDRs) and formed from the reaction of C$^+$ and OH, CO$^+$ is the main chemical precursor of HCO$^+$ and CO in a thermal, cosmic-ray and UV-driven chemistry.

To test whether the thermal cosmic-ray and UV-driven chemistry is producing CO in diffuse interstellar molecular gas through the intermediate formation of CO$^+$.

We searched for CO$^+$ absorption with the Atacama Large Millimeter Array (ALMA) towards two quasars with known Galactic foreground absorption from diffuse interstellar gas, J1717-3342 and J1744-3116, targeting the two strongest hyperfine components of the J=2-1 transition near 236 GHz.

We could not detect CO$^+$ but obtained sensitive upper limits toward both targets. The derived upper limits on the CO$^+$ column densities represent about 4 % of the HCO$^+$ column densities. The corresponding upper limit on the CO$^+$ abundance relative to H$_2$ is $<1.2 \times 10^{-10}$ .

The non-detection of CO$^+$ confirms that HCO$^+$ is mainly produced in the reaction between oxygen and carbon hydrides CH$_2^+$ or CH$_3^+$ induced by supra-thermal processes while CO$^+$ and HOC$^+$ result from reactions of C$^+$ with OH and H$_2$O. The densities required to form CO molecules at low extinction are consistent with this scheme.

# Introduction

The diffuse interstellar medium (ISM) hosts a rich chemistry where many species reach molecular abundances similar to those in denser and darker regions despite the lower densities (a few tens to a few hundred particules per $~{\rm cm}^{-3}$) and the relatively unattenuated far ultraviolet (FUV) illumination by the interstellar radiation field (cite: SnoMcC06; GerNeu+16; LLPG14; LisPet+14; LisGerBea+18; gerin:19). Diffuse and translucent interstellar clouds

(cite: SnoMcC06) have long been used as testbeds of interstellar chemistry (cite: GlaLan75; GlaLan76; BlaDal77; VanBla86; VanBla88). These efforts were successful in explaining the measured column densities for $\mathrm{{\rm H}_2}$ and small trace molecules such as CH, OH and CN using chemical reactions at temperatures 30 - 80K corresponding to kinetic temperatures measured in $\mathrm{{\rm H}_2}$ (cite: SavDra+77) although in some cases assuming regions of density $\ensuremath{\gtrsim} 1000 ~{\rm cm}^{-3}$ along the line of sight. However the observed column densities of CO and the common presence of high column densities of CH$^+$ presented challenges to such models of thermal, cosmic-ray and UV-driven ion-chemistry in diffuse molecular gas.

The observed CO column densities are empirically explained by the serendipitous detection of unexpectedly high column densities of HCO$^+$ seen in absorption at 89.2 GHz (cite: lucas:96). A nearly constant abundance of HCO$^+$ relative to $\mathrm{{\rm H}_2}$, X(HCO$^+$) = N(HCO$^+$)/N($\mathrm{{\rm H}_2}$) = $3\times10^{-9}\pm0.2$dex, is found in comparison with OH and CH (cite: gerin:19) whose own fixed abundances relative to $\mathrm{{\rm H}_2}$ are observed directly in optical/UV absorption (cite: SheRog+08; WesGal+09; WesGal+10). With such significant column densities, the observed HCO$^+$ ions will recombine with ambient thermal electrons at densities n(H) $\ensuremath{\gtrsim} 100 ~{\rm cm}^{-3}$ to produce the observed CO column densities (cite: LisLuc00; VisVan+09).

The 1970’s-1980’s era chemistry is qualitatively correct in predicting a fixed abundance ratio N(HCO$^+$)/N(OH) via a dominant chemical chain that proceeds from C$^+$ + OH $\rightarrow$ CO$^+$ + H (cite: GlaLan75; GlaLan76; dagdigian:19) to CO$^+$ + $\mathrm{{\rm H}_2}$ $\rightarrow$ HCO$^+$ + H and HCO$^+$ + e$^-$ $\rightarrow$ CO + H. However, the observed N(HCO$^+$)/N(OH) $\approx$ 1/30 is roughly thirty times higher than the predicted value through this simple chemical scheme. Some HCO$^+$ can also be produced in this chemistry by the reaction of C$^+$ and $\mathrm{{\rm H}_2}$O whose abundance is 28% that of OH (cite: GerNeu+16; wiesemeyer:16). Both reactions**,** CO$^+$ + $\mathrm{{\rm H}_2}$ and C$^+$ + $\mathrm{{\rm H}_2}$O produce equal amounts of HCO$^+$ and the slightly less tightly-bonded isomer HOC$^+$ that is observed with N(HOC$^+$)/N(HCO$^+$) $= 0.015\pm0.003$ (cite: gerin:19). This disparity in the abundances of HCO$^+$ and **HOC$^+$ ** is much too large to be explained by the isomerization reaction $\mathrm{{\rm H}_2}$ + HOC$^+$ $\rightarrow$ $\mathrm{{\rm H}_2}$ + HCO$^+$ as discussed below.

To reproduce the observed HCO$^+$ abundance at the low mean densities of diffuse clouds, the most successful models include transient production mechanisms that involve dynamical processes in magnetized gas such as low-velocity shocks or turbulent vortices, in which ions and neutral species are partially decoupled (cite: godard:14; lesaffre:20). The resulting slow velocity drift can therefore be used as an additional energy source to drive endothermic chemical reactions that could not operate otherwise (cite: SheRog+08; VisVan+09), especially the reaction C$^+$ + $\mathrm{{\rm H}_2}$ $\rightarrow$ CH$^+$ + H that is endothermic by 0.36 eV or about 4300 K. These models therefore include a specific chemical pathway to CO, which starts from CH$^+$, and is followed by a series of rapid hydrogen abstraction reactions producing CH$_2^+$ and CH$_3^+$. These two ions react with atomic oxygen to produce the required HCO$^+$, and not HOC$^+$. In this scheme, HCO$^+$ is once again the precursor of CO but the predicted CO and HCO$^+$ abundances fit the observations well and the relative rarity of HOC$^+$ arises very naturally.

Therefore the relative abundances of the three molecular ions CO$^+$, HCO$^+$ and HOC$^+$ provide key information on the mechanisms at the origin of CO in diffuse gas. Despite the pivotal role played by CO$^+$ in some versions of the chemistry, its abundance relative to $\mathrm{{\rm H}_2}$ is much less well constrained than those of HCO$^+$ and HOC$^+$. CO$^+$ was first identified in the interstellar medium towards the bright photo dissociation region (PDR) M17SW and the young, high-excitation planetary nebula NGC 7027 (cite: latter:93). CO$^+$ is now routinely observed in dense PDRs such as the Orion Bar (cite: Goicoechea:17) or MonR2 (cite: trevino:16). In such regions CO$^+$ is located at the very edge close to the HI/H$_2$ transition, and its abundance relative to HCO$^+$ ranges from one to several tens of percent (cite: fuente:03). In dense PDRs the intense FUV radiation can pump H$_2$ into vibrationally excited levels that can reach a significant population (cite: agundez:10) The internal energy of this vibrationally excited H$_2$ can trigger the endothermic reaction of C$^+$ + $\mathrm{{\rm H}_2}$ forming CH$^+$ as shown by the widespread distribution of CH$^+$ emission in such regions (cite: goicoechea:19). Paradoxically, the presence of CO$^+$ in dense PDRs is a sign that non-thermal chemical processes are working, while non-thermal processes are invoked in models of diffuse molecular gas to remove the need to produce CO$^+$ on the path to CO.

There are no reported detections of CO$^+$ in the diffuse and translucent interstellar medium: in this paper we present observations with the Atacama Large Millimeter Array (ALMA) that constrain the abundance of CO$^+$ there for the first time. The observation strategy is presented in section [2](#sec:obs) and the results are discussed in section [3](#sec:res) together with the implications for the CO chemistry that are emphasized in sections [4](#sec:chem) and [5](#sec:co). The conclusions are summarized in section [6](#sec:conclusion).

# Spectroscopy and observations

## Spectroscopy

Absorption spectroscopy represents the best method to probe the molecular content of diffuse clouds because the molecular excitation is weak at the low densities (few tens to few hundred cm$^{-3}$) and pressure (p/k $\approx 3\times 10^3 - 10^4$ K-cm$^{-3}$) of these regions (cite: jenkins:11; gerin:15; goldsmith:18) and the level populations are concentrated in the lowest rotational levels. As a $^2\Sigma$ molecular ion, the energy levels of CO$^+$ are described by three quantum numbers; $N$ the rigid body angular momentum quantum number, $S=1/2$ the electron spin angular momentum quantum number and $J = N+S = N \pm 1/2$, the total angular momentum quantum number (cite: sastry:81).

The CO$^+$ ground state rotational transitions at 117.7 GHz and 118.1 GHz are close to a strong atmospheric line from molecular oxygen at 118.75 GHz, rendering their observation from the ground very difficult. Hence observations of CO$^+$ have generally targeted excited transitions where the sky transmission is much better. We chose to search for the $N=2\rightarrow1$ transitions because the frequencies of this first excited transition near 236 GHz are easily accessible from ground-based radio observatories and the level population remains significant even in diffuse interstellar gas. This $N=2\rightarrow 1$ transition is split into three hyperfine components, with the strongest component at 236.06 GHz. Table [1](#table:coplus) lists the three targeted transitions, their frequencies, Einstein A-coefficient and the conversion factor between the integrated line opacity and the molecule column density $N(\rm{CO}^+)/\int \tau ~{\rm dv}$ assuming that the energy level population is determined by the cosmic microwave background at 2.73 K.

Apart from CO$^+$, the setting of the ALMA correlator included spectral windows targeting the $^{13}$CO($2-1$), C$^{18}$O($2-1$) and H$_2$CO($3_{0,3}-2_{0,2}$) transitions that were accessible with the same receiver tuning while including a dedicated spectral window for continuum phase calibration. Properties of the CO lines are given in Table [1](#table:coplus) where the column density/optical depth conversion is calculated for an excitation temperature of 5 K that is typical for this more easily-excited species in diffuse molecular gas (cite: goldsmith:18).

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Transition $^{a}$ | Frequency | A | $N(\rm{CO}^+)$/$\int \tau ~{\rm dv}$$^{b}$ |
| $N,J$ | MHz | s$^{-1}$ | cm$^{-2}$ km$^{-1}$s |
| 2,3/2 - 1 3/2 | 235380.046 | $0.689 \times 10^{-4}$ | $1.01 \times 10^{14}$ |
| 2,3/2 - 1 1/2 | 235789.641 | $3.465 \times 10^{-4}$ | $2.00 \times 10^{13}$ |
| 2,5/2 - 1 3/2 | 236062.553 | $4.172 \times 10^{-4}$ | $1.12 \times 10^{13}$ |
| Transition $^{a}$ | Frequency | A | $N(\rm{^{13}CO})$/$\int \tau ~{\rm dv}$$^{c}$ |
| $J$ | MHz | s$^{-1}$ | cm$^{-2}$ km$^{-1}$s |
| 2 - 1 | 220398.684 | $6.076 \times 10^{-7}$ | $2.42 \times 10^{15}$ |
| Transition $^{a}$ | Frequency | A | $N(\rm{C^{18}O})$/$\int \tau ~{\rm dv}$$^{c}$ |
| $J$ | MHz | s$^{-1}$ | cm$^{-2}$ km$^{-1}$s |
| 2 - 1 | 219560.354 | $6.012 \times 10^{-7}$ | $2.42 \times 10^{15}$ |

: Spectroscopic parameters of observed lines

Table notes:

## Target directions

The targeted sources are J1717-3342 and J1744-3116, two bright quasars situated at small galactic latitude behind the Galactic bulge that were known to have high intervening column densities of Galactic neutral gas detected in molecular absorption (cite: gerin:17; liszt:18; RiqBro+18). Their positions, continuum flux densities S$_\nu$, channel-channel baseline rms line/continuum noise and line profile integrals and velocity intervals used here as integration intervals for the targeted CO$^+$ transitions are given in Table [\[table:sources\]](#table:sources). Comparable quantities for the $\mathrm{^{13}CO}$(2-1) and $\mathrm{C^{18}O}$(2-1) lines are given in Table [\[table:co\]](#table:co).

![image](fig1a.eps) ![image](fig1b.eps)

![](fig2.eps)

## ALMA observations

The observations were performed with ALMA band 6 receivers tuned near 236 GHz during ALMA Cycle 7 under the project code 2019.1.00120.S. The CO$^+$ lines were observed with a channel spacing of 244 kHz, corresponding to a velocity resolution of 0.31 kms$^{-1}$. The channel spectral resolution is twice the channel spacing. As in our earlier observations toward these sources, the bandpass calibrator was fixed to J1924-2914. Absorption spectra were extracted from the standard pipeline-processed data products at the peak of the continuum map in each spectral window. The ALMA spectra of $^{13}$CO, CO$^+$ and HCO$^+$ are displayed in Fig. [1](#fig:coplus). The H$_2$CO ($3_{0,3}-2_{0,2}$) line was detected in both directions and will be discussed elsewhere.

## Other data discussed here

Also shown in Figures [1](#fig:coplus) and [2](#fig:specemi) are 89.2 GHz ALMA HCO$^+$ J=1-0 absorption line profiles with 0.205 $\mathrm{\,km~s^{-1}}$ channel spacing and 0.41 $\mathrm{\,km~s^{-1}}$ spectral resolution from our earlier work (cite: gerin:17; liszt:18). Profile integrals are quoted in Table 3, assuming excitation in equilibrium with the CMB and using N(HCO$^+$) = $1.12\times 10^{12}~{\rm cm}^{-2}\int \tau ~{\rm dv}$ as before. Also shown in Fig. 2 are the nearest $\lambda$2.6mm CO J=1-0 emission profiles with an $8.8\ensuremath{'}$ beamsize from the work of (cite: BitAlv+97) and a $\lambda$21cm H I emission profile from (cite: KalBur+05) (FWHM beam of 0.6$^\circ$). The CO emission profile for J1744-3116 at l,b = 357.875$^\circ$,-1$^\circ$ is very nearly along the same sightline; for J1717-3342, the CO profile at 352.75$^\circ$,2.5$^\circ$ is centered $6.6\ensuremath{'}$ away.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | $l$ | $b$ | LSR Velocity$^a$ | Line | Flux density S$_\nu$ | $\sigma_{l/c}$ | $\int \tau ~{\rm dv}^b$ |
|  | $^o$ | $^o$ | km s$^{-1}$ |  | Jy |  | km s$^{-1}$ |
| J1717-3342 | 352.7333 | 2.3911 | -14..10 | CO$^+$ J=5/2-3/2 | 0.780 | 0.0027 | $<$0.027 |
|  |  |  |  | CO$^+$ J=3/2-1/2 | 0.780 | 0.0034 | $<$0.033 |
| J1744-3116 | 357.8635 | -0.9968 | -20..20 | CO$^+$ J=5/2-3/2 | 0.234 | 0.0084 | $<$0.087 |
|  |  |  |  | CO$^+$ J=3/2-1/2 | 0.251 | 0.0107 | $<$0.111 |

\
$^a$Velocity interval used to integrate the line profile.\
$^b$Upper limits are 3$\sigma$.\

# Results and discussion

## The sight-lines toward J1717-3342 and J1744-3116

Absorption spectra of HCO$^+$, $\mathrm{^{13}CO}$ and CO$^+$ toward both sources are shown in Fig. 1, and Fig. 2 presents a comparison of the absorption spectra of CO and HCO$^+$ with emission spectra of HI and $\mathrm{^{12}CO}$(1-0) described in section [2.4](#subsec:otherdata). Column densities of HCO$^+$, $\mathrm{^{13}CO}$, $\mathrm{C^{18}O}$ and $\mathrm{{\rm H}_2}$ (N($\mathrm{{\rm H}_2}$) = N(HCO$^+$)/$3\times10^{-9}$) are given in Tables 3 and 4. To compute N($\mathrm{^{13}CO}$) and N($\mathrm{C^{18}O}$) we assume an excitation temperature of 5 K (Table 1) that is consistent with the observed brightness of the $\mathrm{^{12}CO}$ emission that is seen toward or near these sources, $1-2.5$ K.

The diffuse nature of the gas along these lines of sight has previously been discussed by (cite: gerin:17), (cite: liszt:18) and (cite: RiqBro+18). High gas column densities accumulate over long paths through the Galactic disk at low galactic latitude even without encountering dense clouds. This is indicated in our new data by the large ratio of $\mathrm{^{13}CO}$ and $\mathrm{C^{18}O}$ integrated optical depths or column densities, N($\mathrm{^{13}CO}$)/N($\mathrm{C^{18}O}$) = 29$\pm5$ toward J1744-3116 (Table 4). If the oxygen and carbon ratios have the usual interstellar values $^{16}$O/$^{18}$O $\sim 520$ and $^{12}$C/$^{13}$C $\sim 65$ (cite: wilson:94; milam:05; keene:98; giannetti:14), a fully molecular gas would have N($\mathrm{^{13}CO}$)/N($\mathrm{C^{18}O}$) = 8 toward J1744-3116. The much larger value we observe arises through some combination of selective photodissociation of $\mathrm{C^{18}O}$ and, more likely, fractionation of $\mathrm{^{13}CO}$ through endothermic carbon isotope exchange when the majority of the free gas phase carbon is in C$^+$ (cite: Lis17CO). Our value for N($\mathrm{^{13}CO}$) toward J1744-3116 in Table 4 agrees with that given by (cite: RiqBro+18) based on J=1-0 absorption, N($\mathrm{^{13}CO}$) $= 6.3 \times 10^{15}~{\rm cm}^{-2}$.

In our earlier work we also derived carbon isotope ratios H$^{12}$CO$^+$/H$^{13}$CO$^+$ = $58\pm9$ and $64\pm4$ in the low-velocity gas toward J1717-3342 and J1744-3116, respectively. These values are typical for Galactic disk gas near the Sun and quite different from what is observed inside the Galactic bulge. Thus although the sight-lines employed here cross the Galactic bulge, the low velocity gas that is analyzed in CO and CO$^+$ resides relative nearby in the disk and will be discussed under the assumption that local conditions are applicable.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Source | N(HCO$^+$) | N(CO$^+$) | N(CO$^+$)/N(HCO$^+$) | N(CO$^+$)/N($\mathrm{{\rm H}_2}$)$^a$ |
|  | $10^{12}$ cm$^{-2}$ | $10^{12}$ cm$^{-2}$ |  |  |
| J1717-3342 | $7.49\pm 0.03$ | $< 0.30$ | $<$ 0.040 | $< 1.2 \times 10^{-10}$ |
| J1744-3416 | $23.35 \pm0.06$ | $< 0.98$ | $<$0.042 | $<1.3 \times 10^{-10}$ |

\
$^a$N($\mathrm{{\rm H}_2}$) = N(HCO$^+$)/$3\times 10^{-9}$.

Overall the CO(1-0) emission is spread over the same velocity range as the HCO$^+$ absorption. Towards J1744-3116, there is a fair correspondence of the main CO emission peaks with the HCO$^+$ absorption features but the HCO$^+$ absorption profiles are more complex. The positive velocity component towards J1744-3116 is detected in $^{13}$CO(2-1) and C$^{18}$O(2-1) absorption and is associated with a self-absorption feature in the H I spectrum that was discussed in (cite: liszt:18). The presence of the three CO isotopologues indicates that this velocity component has probably the largest extinction and mean density and could be associated with translucent rather than diffuse gas. There is no self-absorption in the HI profile coincident with the negative velocity component, but the main $^{13}$CO(2-1) absorption is associated with a faint C$^{18}$O(2-1) feature.

The CO(1-0) emission differs more from the HCO$^+$ absorption towards J1717-3342 where the direction of the emission spectrum is 6.6$'$ away. Of the 8 main HCO$^+$ absorption features, only one is detected in $^{13}$CO(2-1) and none in C$^{18}$O(2-1) showing that the gas is more diffuse along this line of sight. The CO emission is weaker than towards J1744-3116, barely reaching 1 K. As discussed by (cite: liszt:10), in diffuse gas the CO(1-0) emission is highly variable as it traces the regions where CO reaches column densities above N(CO) $=10^{15}~{\rm cm}^{-2}$ that are high enough to produce detectable emission. This transition occurs over a small range of H$_2$ column densities and depends on the local physical conditions but CO emission at the level of 1 K-$\mathrm{\,km~s^{-1}}$ integrated intensity is not observed in regions where the molecular fraction of H-nuclei in $\mathrm{{\rm H}_2}$ is much below 0.6.

The comparison of the emission and absorption profiles therefore demonstrates that the two observed lines of sight encounter matter with variable physical conditions, ranging from diffuse to translucent gas. The upper limits for the CO$^+$ integrated opacities shown in Table [\[table:sources\]](#table:sources) provide constraints on the CO$^+$ column densities and abundances for the whole range of physical conditions. For the diffuse molecular gas sampled in absorption the molecule excitation is dominated by the cosmic microwave background because of the low gas densities. Therefore, the CO$^+$ column densities have been derived assuming an excitation temperature of 2.73 K. They are reported in Table 3 together with the HCO$^+$ column densities in the same velocity intervals. The achieved upper limit on CO$^+$ column densities leads to a very low value for the N(CO$^+$)/N(HCO$^+$) ratio, of about 0.04. The corresponding upper limit on the CO$^+$ abundance relative to H$_2$ is X(CO$^+$) $< 1.2 \times10^{-10}$, using the standard value for the HCO$^+$ abundance relative to H$_2$ in the diffuse molecular gas, $3\times 10^{-9}$ (cite: lucas:96; gerin:19). These values are a factor a few times higher than those established for HOC$^+$, N(HOC$^+$)/N(HCO$^+$) $= 0.015$ and X(HOC$^+$) $= 0.45 \times10^{-11}$ (cite: gerin:19).

## CO$^+$ as a source of HCO$^+$

Despite the excellent sensitivity with achieved fractional rms flux density levels $\Delta{\rm S}_\nu/{\rm S}_\nu$ of 0.22% and 0.83% for J1717-3342 and J1744-3116 respectively, CO$^+$ was not detected towards these sources. The derived $3\sigma$ upper limits N(CO$^+$)/N(HCO$^+$) $\ensuremath{\lesssim} 0.04$ and N(CO$^+$)/N($\mathrm{{\rm H}_2}$) $< 1.2-1.3\times10^{-10}$ are similar for both sources in Table [\[table:sources\]](#table:sources) because J1717-3342 with smaller intervening column density is much brighter in the continuum. The achieved upper limit on the relative abundance is somewhat above the values seen in dense PDRs where emission lines from CO$^+$ are detected and X(CO$^+$) reaches a few times 10$^{-11}$. They are below the relative abundances seen in the exceptional case of the young planetary nebula NGC 7027 where N(CO$^+$)/N($\mathrm{{\rm H}_2}$) $= 5\times 10^{-9}$ (cite: fuente:03).

It is straightforward to show that the relative abundance of CO$^+$ is too small to provide a major source of the observed HCO$^+$ in diffuse molecular gas, even independent of the HCO$^+$abundance. In chemical terms, the reaction CO$^+$ + $\mathrm{{\rm H}_2}$ $\rightarrow$ HCO$^+$ + H forming HCO$^+$ can be compared with the rate at which HCO$^+$ recombines with electrons with rates as given in Table [\[table:chem\]](#table:chem).

Equating formation and recombination of HCO$^+$ , neglecting photodissociation that is four orders of magnitude slower according to the Kinetic Database for Astrochemistry (KIDA) (cite: Kida2014)

$$k_2~n(\mbox{{CO$^+$}})n(\ensuremath{\mathrm{{\rm H}_2}}) = \alpha(T)~n(\mbox{HCO$^+$})n(e)$$

and rearranging, we have

$$n(\mbox{{CO$^+$}})/n(\mbox{HCO$^+$}) = (\alpha(T)/k_2) n(e)/n(\ensuremath{\mathrm{{\rm H}_2}})$$

or equivalently

$$n(\mbox{{CO$^+$}})/n(\mbox{HCO$^+$}) = (2/\mbox{f$_\ensuremath{\mathrm{{\rm H}_2}}$})~(\alpha(T)/k_2)~x(e)$$

where f$_\ensuremath{\mathrm{{\rm H}_2}}$ is the fraction of H-nuclei in $\mathrm{{\rm H}_2}$, $x(e)$ is the electron fraction, $n(\ensuremath{\mathrm{{\rm H}_2}})$ is the density of $\mathrm{{\rm H}_2}$ molecules, and $n({\rm H})$ is the total density of H-nuclei. Taking $x(e)= 2\times10^{-4}$ corresponding to the observed free gas-phase carbon abundance $n({\rm C}^+)/n({\rm H}) = 1.6\times10^{-4}$ (cite: SofLau+04) with a small added contribution from cosmic ray ionization of atomic hydrogen in largely molecular gas, the required amount of CO$^+$ needed to restore the HCO$^+$ lost to recombination is

$$n(\mbox{{CO$^+$}})/n(\mbox{HCO$^+$}) = (0.6/\mbox{f$_\ensuremath{\mathrm{{\rm H}_2}}$}) \times (40/T)^{0.69}$$

This is some 25 times higher than our upper limit if f$_\ensuremath{\mathrm{{\rm H}_2}}$ = 0.6 and T = 40 K. We noted above that CO emission even at the low levels shown in Fig. 2 does not arise in regions of very small molecular fraction and temperatures high enough to trigger the formation of CH$^+$, such regions are only characteristic of regions of strong turbulent energy dissipation.

Alternatively, equating the HCO$^+$ formation and recombination rates once again but setting $n(\mbox{HCO$^+$})/n(\ensuremath{\mathrm{{\rm H}_2}}) = 3\times 10^{-9}$ and $x(e) = 2\times10^{-4}$ = $2\times10^{-4}(2n(\ensuremath{\mathrm{{\rm H}_2}})/\mbox{f$_\ensuremath{\mathrm{{\rm H}_2}}$})$, one derives for the required relative abundance of CO$^+$ 

$$X(\mbox{{CO$^+$}}) = (1.8\times10^{-9}/\mbox{f$_\ensuremath{\mathrm{{\rm H}_2}}$}) \times (40/T)^{0.69}.$$

This is comparable to the CO$^+$ relative abundance seen in NGC 7027 ($\sim 5\times 10^{-9}$, (cite: fuente:03)) and is at least 15 times above the upper limit achieved here, $1.2 \times 10^{-10}$, if T = 40 K (Table 2). In this simplified analysis, reducing X(CO$^+$) below our upper limit would require temperatures of about 2000 K that are more nearly characteristic of the turbulence-driven chemistry, which can only be present in small and intermittent regions of space and time, where other thermal and non-chemical processes are operating. CO$^+$ is responsible for producing at most a few percent of the HCO$^+$ that recombines with ambient thermal electrons to form CO in diffuse molecular gas.

# The thermal chemistry of CO$^+$, HOC$^+$ and HCO$^+$

![](fig3.eps)

Our upper limits show that CO$^+$ cannot be responsible for forming the observed CO in diffuse molecular gas because CO$^+$ does not exist in sufficient quantity to replenish HCO$^+$ as it recombines with ambient electrons. However, beyond that, our limits combined with the observed relative abundance N(HOC$^+$)/N(HCO$^+$) $= 1.4\pm0.2 \times 10^{-4}$ (cite: gerin:19) can be used to gain further insights into the thermal chemistry that is working in diffuse molecular gas. Most of the reactions that form HCO$^+$ also form HOC$^+$, yet their observed abundances differ by a factor 70. To explore this, we extended the thermal CO$^+$ and HOC$^+$ chemistry discussed by (cite: gerin:19) to include some hypotheticals corresponding to uncertainties in reaction rates in the KIDA reaction rate database (cite: Kida2014) and molecular abundances (cite: GerNeu+16). As discussed in (cite: gerin:19), some of the rates of the reactions controlling the formation of CO$^+$ and HCO$^+$ were not well known, especially the reaction $\rm{C^+ + OH \rightarrow CO^+ + H / CO + H^+}$ and the isomerization reaction destroying HOC$^+$ and forming HCO$^+$, $\rm{HOC^+ + H_2 \rightarrow HCO^+ + H_2}$, whose rate is reported as $4 \times 10^{-10}$${\rm cm}^3~{\rm s}^{-1}$ at 25  K and 300  K (cite: smith:02), about 1/5 the Langevin capture value and, in this temperature range, probably independent of the temperature.

As originally suggested by (cite: GlaLan75; GlaLan76), CO$^+$ can be formed by the reaction of C$^+$ with OH, and also by the reaction of O with CH$^+$. CO$^+$ is destroyed by recombination with electrons and in chemical reactions with atomic and molecular hydrogen, and photo-dissociated with a free space rate $1\times10^{-10}$s$^{-1}$ that is always at least 300 times slower than the other destruction rates in the calculations discussed here. The OH relative abundance to $\mathrm{{\rm H}_2}$, X(OH) $= 1.0 \pm 0.14 \times10^{-7}$ varies only narrowly and is well-determined in local diffuse clouds (cite: WesGal+09; WesGal+10) such as those probed in this work. The excellent correspondence of the OH and $\mathrm{{\rm H}_2}$O absorption line profiles and of the $\mathrm{{\rm H}_2}$O and HCO$^+$ profiles along long sight-lines across the Galactic plane (cite: wiesemeyer:16; gerin:19) further indicates that this value of the OH abundance holds for the Galactic disk as well. The rate of the reaction of OH and C$^+$ was recently calculated by (cite: dagdigian:19), providing accurate information on the rate coefficient and branching ratio over a temperature range 10 – 1000   K. We approximate the rate constant for C$^+$ + OH forming CO$^+$ as $k =  2.2\times10^{-9}$(300/T)$^{0.107}$${\rm cm}^3~{\rm s}^{-1}$(see Table [\[table:chem\]](#table:chem) ). By contrast the abundance of CH$^+$ is locally variable and CH$^+$ may not co-exist with the other species if it is predominantly formed in the non-thermal chemistry (cite: godard:14; valdivia:17). We take X(CH$^+$) as a free parameter with X(CH$^+$) $= 10^{-9}$ by default in the following discussion.

HOC$^+$ can be formed in the reaction of $\mathrm{{\rm H}_2}$ with CO$^+$ and in the reaction of C$^+$ with $\mathrm{{\rm H}_2}$O whose fixed relative abundance X($\mathrm{{\rm H}_2}$O) $=2.4\times10^{-8}$ we take from (cite: GerNeu+16). We ignore HOC$^+$ formation by the reaction of O with CH$_3$$^+$ because the formation of CH$_3$$^+$ is an aspect of the non-thermal chemistry. HOC$^+$ recombines with electrons and is susceptible to photodissociation, but most importantly is isomerized to HCO$^+$ in reaction with $\mathrm{{\rm H}_2}$. The rate constant for the isomerization reaction of $\mathrm{{\rm H}_2}$ and HOC$^+$ has alternatives in the KIDA database as discussed previously. Here we consider the two extreme values for the rate constant, $10^{-1  1}$${\rm cm}^3~{\rm s}^{-1}$ given for 10-280 K and $4.7\times10^{-10}$${\rm cm}^3~{\rm s}^{-1}$ given at 305 K.

The CO$^+$ and HOC$^+$ chemistry is simple when other molecular abundances are held fixed but it involves the thermal and ionization balance for the temperature-sensitive recombination rates and the atomic/molecular hydrogen balance for various reactions with CO$^+$ and HOC$^+$. To treat this we performed calculations like those done earlier to account for the observations of HF and CF$^+$ (cite: LisGuz+15). In brief we calculated the self-consistent global atomic/molecular, ionization and thermal equilibrium in gas spheres of constant total hydrogen number and column density, subject to the usual interstellar radiation fields. The hydrogen column density was varied and molecular abundances were integrated along the central line of sight to form the results that are displayed here. Plotting the results against N($\mathrm{{\rm H}_2}$) removes some model sensitivities, for instance to the impact parameter about the cloud center used for the line of sight integration.

The results are shown in Fig. [3](#fig:chem). At left is a baseline model using default values (Table [\[table:chem\]](#table:chem)). The model produces CO$^+$ relative abundances about 2.5 times smaller than our observed upper limits, and about twice as much HOC$^+$ as observed. Declines in the abundances of CO$^+$ and HOC$^+$ for very high N($\mathrm{{\rm H}_2}$) arise from the recombination of the free gas-phase carbon from C$^+$ to neutral carbon and CO.

In the middle panel the solid lines show results when $\mathrm{{\rm H}_2}$-catalyzed HOC$^+$ $\rightarrow$ HCO$^+$ isomerization has the rate constant $10^{-11}$${\rm cm}^3~{\rm s}^{-1}$, a factor 2.5 above the default value. The green curve for HOC$^+$ shows that the predicted abundance of HOC$^+$ grows even further above what is observed when the HOC$^+$ $\rightarrow$ HCO$^+$ interconversion is slow. The orange curves show what happens when the rate constant for HOC$^+$ formation via $\mathrm{{\rm H}_2}$ + CO$^+$ $\rightarrow$ HOC$^+$ + H is set to 0. The predicted amount of CO$^+$ grows well above our upper limits and the abundance of HOC$^+$ falls far below the observed mean. We conclude that HOC$^+$ is forming mostly via C$^+$ + OH followed by CO$^+$ + $\mathrm{{\rm H}_2}$  but much or most of the HOC$^+$ so produced is lost to isomerization into HCO$^+$.

In the right side panel of Fig. [3](#fig:chem) the solid curves show model results when the reaction of C$^+$ and $\mathrm{{\rm H}_2}$O does not form HOC$^+$: all of the observed HOC$^+$ can indeed be made by the reaction of C$^+$ and OH, and agreement with the observed HOC$^+$/HCO$^+$ ratio is somewhat better when the contribution from $\mathrm{{\rm H}_2}$O is neglected. However, $\mathrm{{\rm H}_2}$O is observed to be present with X($\mathrm{{\rm H}_2}$O) $=2.4\times10^{-8}$ (cite: GerNeu+16) and would be expected to form some amount of HOC$^+$. The default model may be predicting an overabundance of CO$^+$ or perhaps some aspect of the reaction of C$^+$ and $\mathrm{{\rm H}_2}$O is not fully understood: a slower rate or a branching ratio that favors HCO$^+$would lead to a lower contribution of this reaction to the HOC$^+$ formation.

CH$^+$ may not co-exist with the other species if it is predominantly formed in the non-thermal chemistry (cite: godard:14; valdivia:17) and X(CH$^+$) is negligible ($10^{-9}$) in the default model. The final deviation from the default model is represented by the dash-dot lines in the righthand panel showing results when X(CH$^+$) = X(OH) = $10^{-7}$ is large. The reaction of O + CH$^+$ becomes an important source of CO$^+$ in the thermal chemistry when X(CH$^+$) $\ensuremath{\gtrsim} 5\times10^{-8}$ and our upper limits on CO$^+$ by themselves imply X(CH$^+$)/X(OH) $\ensuremath{\lesssim} 3$. At such high CH$^+$ abundances the discrepancy in HOC$^+$ grows even larger.

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Source | line | Flux | $\sigma_{l/c}$ | $\int \tau ~{\rm dv}$ | N$^a$ |
|  |  | Jy |  | km s$^{-1}$ | $10^{14}~{\rm cm}^{-2}$ |
| J1717-3342 | $\mathrm{^{13}CO}$ | 0.818 | 0.0024 | 0.260(0.004) | 6.3(0.4) |
|  | $\mathrm{C^{18}O}$ | 0.822 | 0.0123 | $<$ 0.055 | $<1.3$ |
| J1744-3116 | $\mathrm{^{13}CO}$ | 0.244 | 0.0073 | 2.975(0.023) | 72.0(0.6) |
|  | $\mathrm{C^{18}O}$ | 0.244 | 0.0084 | 0.102(0.018) | 2.5(0.4) |

\
$^a$Upper limit is 3$\sigma$.

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Reaction | Symbol | Rate Coefficient | Reference |
|  |  | $~{\rm cm}^{-3}$s$^{-1}$ |  |
| C$^+$ + OH $\rightarrow$ CO$^+$ + H | k$_1$ | $2.2\times10^{-9}$(300/T)$^{0.107}$ | (cite: dagdigian:19) |
| CO$^+$ + $\mathrm{{\rm H}_2}$ $\rightarrow$ HCO$^+$ + H | k$_2$ | $7.5\times10^{-10}$ | KIDA |
| C$^+$ + H$_2$O $\rightarrow$ HCO$^+$ + H | k$_3$ | $2.1\times10^{-9}$ | KIDA |
| C$^+$ + H$_2$O $\rightarrow$ HOC$^+$ + H | k$_4$ | $2.1\times10^{-9}$ | KIDA, (cite: martinez:08) |
| HOC$^+$ + H$_2$ $\rightarrow$ HCO$^+$ + H$_2$ | k$_5$ | $4 \times 10^{-10}$ | (cite: smith:02) |
| HOC$^+$ + H$_2$ $\rightarrow$ HCO$^+$ + H$_2$ | k$_6$ | $1 \times 10^{-11}$ | KIDA |
| HCO$^+$ + e$^-$ $\rightarrow$ CO + H | $\alpha(T)$ | $1.43\times10^{-5}/{\rm T}^{0.69}$ | (cite: hamberg:14) |
| Reaction | Symbol | Rate | Reference |
|  |  | s$^{-1}$ |  |
| CO + $h\nu$ $\rightarrow$ C + O | k$_d$ | $2.43 \times 10^{-10} {\rm exp}(-3.88 \ensuremath{A_\ensuremath{\mathrm{V}}})$ | KIDA, (cite: HeaBos+17) |
| CO$^+$ + $h\nu$ $\rightarrow$ C$^+$ + O |  | $1.04 \times 10^{-10}$ | KIDA |

![](fig4.eps)

# Conditions for the growth of CO

Balancing the formation of CO through dissociative recombination of HCO$^+$ and destruction of CO by photodissociation can constrain the physical conditions where CO might form in diffuse molecular gas. With a free-space photodissociation rate $k_d = 2.43 \times 10^{-10}$ s$^{-1}$ for the Draine radiation field (defined as $G_0=1$) and an attenuation scaling as $e^{-\gamma \ensuremath{A_\ensuremath{\mathrm{V}}}}$ this balance locally implies

$$\frac{n({\rm CO})}{n(\mbox{HCO$^+$})} = \frac{\alpha(T)x(e)n({\rm H})}{G_0k_d e^{-\gamma \ensuremath{A_\ensuremath{\mathrm{V}}}}}$$

For a uniform slab, integrating the attenuation term from 0 up to half the slab extinction,

$$\frac{N({\rm CO})}{N(\mbox{HCO$^+$})} = \frac{\alpha(T)x(e)n({\rm H})} {G_0k_d } \frac{0.5 \gamma  \ensuremath{A_\ensuremath{\mathrm{V}}}}{ 1-e^{-0.5\gamma  \ensuremath{A_\ensuremath{\mathrm{V}}}}}$$

$n({\rm H})/G_0$ can therefore be expressed as

$$n({\rm H})/G_0 = \frac{N({\rm CO})}{N(\mbox{HCO$^+$})}  \frac{k_d (1-e^{-0.5\gamma  \ensuremath{A_\ensuremath{\mathrm{V}}}})}{\alpha(T)x(e)0.5 \gamma  \ensuremath{A_\ensuremath{\mathrm{V}}}}$$

where we approximate $A_\ensuremath{\mathrm{V}}$$= 3.1$E(B-V) and take E(B-V) from (cite: GreGre+19), replacing local quantities with line of sight averages. The error bar in E(B-V) is a nominal value 0.02 mag. We take $\gamma = 3.88$ and use the reaction rates and rate coefficients given in Table [\[table:chem\]](#table:chem). Fig. [4](#fig:co) presents the variation of $n({\rm H})/G_0$ as a function of the reddening E(B-V) for the existing sample of QSO sight lines with HCO$^+$ and CO column densities determined in absorption (cite: LisLuc98; LisGer+19). We use conditions as described in Section 2, a uniform temperature of 40K and a uniform electron fraction $x(e) = 2 \times 10^{-4}$.

The mean value for the sample is $<n({\rm H})/G_0 > \sim 300~{\rm cm}^{-3}$. For a standard interstellar radiation field of $G_0 = 1$, the calculated densities n(H) $\sim 100-300 ~{\rm cm}^{-3}$ are modest for E(B-V) $\ensuremath{\gtrsim} 0.5$ mag, even in the absence of any consideration of CO shielding by itself or by $\mathrm{{\rm H}_2}$. The higher densities $n({\rm H}) \sim 1000-2000~{\rm cm}^{-3}$ calculated at E(B-V) $\ensuremath{\lesssim}$ 0.2 mag are higher by a factor $\sim$ 5 than are inferred from the brightness of HCO$^+$ emission in these directions (cite: Lis20Hotspots). Thermal pressures $p/k \sim$ 40 K $\times$ 1000$~{\rm cm}^{-3}$ are an order of magnitude higher than typical values in the diffuse molecular gas (cite: JenTri11) and would more likely represent the conditions under which a turbulence-driven chemistry forms HCO$^+$. A lower value of the radiation field toward these sight-lines would bring the derived densities closer to the mean values. The data shown in this plot include the sight lines with CO and HCO$^+$ detections, which may bias the derived $n({\rm H}/G_0$ to somewhat high values as a higher density implies a faster CO production rate.

The inverse variation of $n({\rm H})/G_0$ with E(B-V) in Fig. [4](#fig:co), mirroring the functional dependence on Av, reflects the fact that the observed values of N(CO)/N(HCO$^+$) are not correlated with E(B-V) and show a moderate scatter of at most a factor of 1. A majority of the selected sight-lines have N(CO)/N(HCO$^+$) between 1000 and 2000. We also plotted $n({\rm H})/G_0$ against the molecular fraction f$_\ensuremath{\mathrm{{\rm H}_2}}$ = 2N($\mathrm{{\rm H}_2}$)/N(H) taking N($\mathrm{{\rm H}_2}$) = N(HCO$^+$)/$3\times10^{-9}$ and N(H) = $a \times$ E(B-V). Requiring f$_\ensuremath{\mathrm{{\rm H}_2}}$ $\leq 1$ in all cases implies $a \ensuremath{\gtrsim} 8\times 10^{21}~{\rm H-nuclei}~{\rm cm}^{-2}$ mag$^{-1}$ but there is no trend for $n({\rm H})/G0$ to vary with f$_\ensuremath{\mathrm{{\rm H}_2}}$ calculated in this way.

# Summary and conclusions

We sought to test the origin of CO in diffuse molecular gas within the generally accepted framework that CO is predominantly formed through the dissociative electron recombination of HCO$^+$. HCO$^+$ is widely observed in diffuse molecular gas, with a relative abundance N(HCO$^+$)/N($\mathrm{{\rm H}_2}$) $= 3\times 10^{-9}$.

In a quiescent, thermal, cosmic-ray and UV-driven chemistry, HCO$^+$ is predominantly formed in the reactions C$^+$ + OH $\rightarrow$ CO$^+$ + H and CO$^+$ + $\mathrm{{\rm H}_2}$$\rightarrow$ HCO$^+$ + H. Using Cycle 7 ALMA Band 6 observations at 236 GHz (Table 1) we searched for CO$^+$ absorption toward two bright compact extragalactic mm-wave continuum sources seen at low latitude in the inner Galaxy and known to be occulted by high column densities of HCO$^+$-bearing diffuse molecular gas (see Section 2 and Table 2). We failed to detect CO$^+$ at levels sufficient to demonstrate in Section 3 that the reaction CO$^+$ + $\mathrm{{\rm H}_2}$ $\rightarrow$ HCO$^+$ + H cannot replenish more than a few percent of the observed HCO$^+$ that recombines. The non-detection of CO$^+$ confirms that HCO$^+$ is mainly produced in the reaction between oxygen and carbon hydrides CH$_2^+$ or CH$_3^+$ induced by supra-thermal processes while CO$^+$ and HOC$^+$ result from reactions between C$^+$ and OH and $\mathrm{{\rm H}_2}$O in the thermal chemistry that occurs in quiescent diffuse molecular gas. The observed CO$^+$ and HOC$^+$ abundances relative to $\mathrm{{\rm H}_2}$ set an upper limit on the rate coefficient of these reactions.

In Section 4 we explored the coupled thermal chemistries of CO$^+$ and HOC$^+$ given our observational upper limits on CO$^+$ and existing observations of HOC$^+$ showing N(HOC$^+$)/N(HCO$^+$) $= 0.015\pm0.003$. A baseline cosmic-ray and UV-driven thermal chemical model overproduced HOC$^+$ by a factor two, but by as much as a factor six if the isomerization reaction HOC$^+$ + $\mathrm{{\rm H}_2}$ $\rightarrow$ HCO$^+$ + $\mathrm{{\rm H}_2}$ does proceed rapidly. The option of a low rate for this reaction in the KIDA database should probably be ignored. The predicted HOC$^+$ abundance is in better agreement with observation if the reaction of C$^+$ and $\mathrm{{\rm H}_2}$O preferentially forms HCO$^+$, rather than HOC$^+$. We placed a weak limit on the relative abundance of CH$^+$ in quiescent gas, N(CH$^+$)/N(OH) $\ensuremath{\lesssim}$ 3 or X(CH$^+$)/X($\mathrm{{\rm H}_2}$) $\ensuremath{\lesssim} 3\times10^{-7}$ such that the reaction O + CH$^+$ does not become an important source of CO$^+$, substantially over-producing it.

In Section 5 we derived characteristic number densities $n({\rm H})$ at which CO would form in diffuse molecular gas with observed abundances. For E(B-V) $\ensuremath{\gtrsim}$ 0.5 mag the densities are modest, $n({\rm H}) \sim 100-300~{\rm cm}^{-3}$ but for CO-bright regions of low extinction E(B-V) $\sim 0.1-0.2$ mag they are an order of magnitude higher $n({\rm H}) \sim 1-2\times10^3 ~{\rm cm}^{-3}$ and such heavily over-pressured gas is more properly considered in the context of a turbulent dissipation chemistry. The presence of CO in sight-lines of low reddening could also indicate a lower radiation field intensity.

# Acknowledgements

The authors thanks the referee Helmut Wiesemeyer for his thoughtful comments and suggestions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00120.S.. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work was supported by the Programme National ”Physique et Chimie du Milieu Interstellaire” (PCMI) of CNRS/INSU with INC/INP co-funded by CEA and CNES.

59 natexlab

(ref: agundez:10) Agúndez, M., Goicoechea, J. R., Cernicharo, J., Faure, A., & Roueff, E. 2010, ApJ, 713, 662

(ref: BitAlv+97) Bitran, M., Alvarez, H., Bronfman, L., May, J., & Thaddeus, P. 1997, ApJS, 125, 99

(ref: BlaDal77) Black, J. H. & Dalgarno, A. 1977, ApJS, 34, 405

(ref: dagdigian:19) Dagdigian, P. J. 2019, , 151, 054306

(ref: endres:16) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: fuente:03) Fuente, A., Rodrıguez-Franco, A., Garcıa-Burillo, S., Martın-Pintado, J., & Black, J. H. 2003, A&A, 406, 899

(ref: gerin:17) Gerin, M. & Liszt, H. 2017, A&A, 600, A48

(ref: gerin:19) Gerin, M., Liszt, H., Neufeld, D., et al. 2019, A&A, 622, A26

(ref: GerNeu+16) Gerin, M., Neufeld, D. A., & Goicoechea, J. R. 2016, ARA&A, 54, 181

(ref: gerin:15) Gerin, M., Ruaud, M., Goicoechea, J. R., et al. 2015, A&A, 573, A30

(ref: giannetti:14) Giannetti, A., Wyrowski, F., Brand, J., et al. 2014, A&A, 570, A65

(ref: GlaLan75) Glassgold, A. E. & Langer, W. D. 1975, ApJ, 197, 347

(ref: GlaLan76) Glassgold, A. E. & Langer, W. D. 1976, ApJ, 206, 85

(ref: godard:14) Godard, B., Falgarone, E., & Pineau des Forêts, G. 2014, A&A, 570, A27

(ref: Goicoechea:17) Goicoechea, J. R., Cuadrado, S., Pety, J., et al. 2017, A&A, 601, L9

(ref: goicoechea:19) Goicoechea, J. R., Santa-Maria, M. G., Bron, E., et al. 2019, A&A, 622, A91

(ref: goldsmith:18) Goldsmith, P. F., Pineda, J. L., Neufeld, D. A., et al. 2018, ApJ, 856, 96

(ref: GreGre+19) Green, G. M., Schlafly, E., Zucker, C., Speagle, J. S., & Finkbeiner, D. 2019, ApJ, 887, 93

(ref: hamberg:14) Hamberg, M., Kashperkat, I., Thomas, R. D., et al. 2014, J. Phys. Chem. A., 118, 6034

(ref: HeaBos+17) Heays, A. N., Bosman, A. D., & van Dishoeck, E. F. 2017, A&A, 602, A105

(ref: jenkins:11) Jenkins, E. B. & Tripp, T. M. 2011a, ApJ, 734, 65

(ref: JenTri11) Jenkins, E. B. & Tripp, T. M. 2011b, ApJ, 734, 65

(ref: KalBur+05) Kalberla, P. M. W., Burton, W. B., Hartmann, D., et al. 2005, A&A, 440, 775

(ref: keene:98) Keene, J., Schilke, P., Kooi, J., et al. 1998, ApJL, 494, L107

(ref: latter:93) Latter, W. B., Walker, C. K., & Maloney, P. R. 1993, ApJL, 419, L97

(ref: lesaffre:20) Lesaffre, P., Todorov, P., Levrier, F., et al. 2020, MNRAS, 495, 816

(ref: liszt:18) Liszt, H. & Gerin, M. 2018, A&A, 610, A49

(ref: LisGerBea+18) Liszt, H., Gerin, M., Beasley, A., & Pety, J. 2018, ApJ, 856, 151

(ref: LisGer+19) Liszt, H., Gerin, M., & Grenier, I. 2019, A&A, 627, A95

(ref: LLPG14) Liszt, H., Lucas, R., Pety, J., & Gerin, M. 2014a, in IAU Symposium, Vol. 297, The Diffuse Interstellar Bands, ed. J. Cami & N. L. J. Cox, 163–172

(ref: Lis17CO) Liszt, H. S. 2017, ApJ, 835, 138

(ref: Lis20Hotspots) Liszt, H. S. 2020, ApJ, 897, 104

(ref: LisGuz+15) Liszt, H. S., Guzmán, V. V., Pety, J., et al. 2015, A&A, 579, A12

(ref: LisLuc98) Liszt, H. S. & Lucas, R. 1998, A&A, 339, 561

(ref: LisLuc00) Liszt, H. S. & Lucas, R. 2000, A&A, 355, 333

(ref: LisPet+14) Liszt, H. S., Pety, J., Gerin, M., & Lucas, R. 2014b, A&A, 564, A64

(ref: liszt:10) Liszt, H. S., Pety, J., & Lucas, R. 2010, A&A, 518, A45

(ref: lucas:96) Lucas, R. & Liszt, H. 1996, A&A, 307, 237

(ref: martinez:08) Martinez, Jr., O., Betts, N. B., Villano, S. M., et al. 2008, ApJ, 686, 1486

(ref: milam:05) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126

(ref: muller:05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: muller:01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: RiqBro+18) Riquelme, D., Bronfman, L., Mauersberger, R., et al. 2018, A&A, 610, A43

(ref: sastry:81) Sastry, K. V. L. N., Helminger, P., Herbst, E., & De Lucia, F. C. 1981, ApJL, 250, L91

(ref: SavDra+77) Savage, B. D., Drake, J. F., Budich, W., & Bohlin, R. C. 1977, ApJ, 216, 291

(ref: SheRog+08) Sheffer, Y., Rogers, M., Federman, S. R., et al. 2008, ApJ, 687, 1075

(ref: smith:02) Smith, M. A., Schlemmer, S., von Richthofen, J., & Gerlich, D. 2002, ApJL, 578, L87

(ref: SnoMcC06) Snow, T. P. & McCall, B. J. 2006, ARA&A, 44, 367

(ref: SofLau+04) Sofia, U. J., Lauroesch, J. T., Meyer, D. M., & Cartledge, S. I. B. 2004, ApJ, 605, 272

(ref: trevino:16) Treviño-Morales, S. P., Fuente, A., Sánchez-Monge, Á., et al. 2016, A&A, 593, L12

(ref: valdivia:17) Valdivia, V., Godard, B., Hennebelle, P., et al. 2017, A&A, 600, A114

(ref: VanBla86) Van Dishoeck, E. F. & Black, J. H. 1986, ApJ Supp. Ser., 62, 109

(ref: VanBla88) van Dishoeck, E. F. & Black, J. H. 1988, ApJ, 334, 771

(ref: VisVan+09) Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323

(ref: Kida2014) Wakelam, V., Loison, J. C., Herbst, E., et al. 2015, ApJS, 217, 20

(ref: WesGal+09) Weselak, T., Galazutdinov, G., Beletsky, Y., & Krełowski, J. 2009, A&A, 499, 783

(ref: WesGal+10) Weselak, T., Galazutdinov, G. A., Beletsky, Y., & Krełowski, J. 2010, MNRAS, 402, 1991

(ref: wiesemeyer:16) Wiesemeyer, H., Güsten, R., Heyminck, S., et al. 2016, A&A, 585, A76

(ref: wilson:94) Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191

</paper>

Write the methods card for this paper.