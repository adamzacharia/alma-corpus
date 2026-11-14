# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9..458M\sonnetcc\reply.txt

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
 "bibcode": "2025NatAs...9..458M",
 "title": "The evolution of dust attenuation in z ≈ 2-12 galaxies observed by JWST",
 "year": 2025,
 "journal": "Nature Astronomy",
 "first_author": "Markov, Vladan",
 "n_authors": 8,
 "arxiv_id": "2402.05996",
 "doi": "10.1038/s41550-024-02426-1",
 "alma_projects_linked_by_archive": [
  "2012.1.00173.S",
  "2015.1.00098.S",
  "2015.1.00543.S",
  "2017.1.00755.S",
  "2018.1.00035.L",
  "2022.1.00073.S"
 ]
}
```

Paper text:
<paper>
# Dust attenuation evolution in $z \sim 2-12$ galaxies observed by JWST [^1]

# Introduction

Dust attenuation refers to the absorption and scattering of photons along the line of sight (LOS), due to the intervening interstellar medium (ISM) dust. The shape of the dust attenuation curve, $A_\lambda$, in galaxies (i.e. the slope of the curve and the strength of the characteristic UV bump at $\sim 2175$ Å) is determined by both the intrinsic dust properties (mass, grain size distribution, chemical composition), and the spatial distribution of dust with respect to stars. In the case of simple dust-to-star geometry, e.g., a point-like background source with a uniform dust screen, the loss of light along the LOS is instead referred to as "dust extinction", which is governed solely by the intrinsic dust properties(cite: 2013seg..book..419C; 2020ARA&A..58..529S).

The slope of the attenuation curve is determined by the grain size distribution and chemical composition(cite: 1977ApJ...217..425M; 1984ApJ...285...89D; 2001ApJ...548..296W). In particular, a shift towards smaller (larger) grains results in steeper (shallower) shapes(cite: 2001ApJ...548..296W). Likewise, the rise of the characteristic UV bump feature at $2175$ Å is typically associated with the existence of small carbonaceous dust grains(cite: 1965ApJ...142.1683S; 1984ApJ...285...89D), including polycyclic aromatic hydrocarbons (PAHs)(cite: 1990A&A...237..215D; 1992A&A...259..614S). The V-band attenuation, $A_V$, which serves as a proxy of the galaxy dust content along the LOS, has been identified as one of the primary drivers of the shape of the dust attenuation law(cite: 2013MNRAS.432.2061C; 2020ApJ...888..108B). Theoretical studies suggest that this correlation may arise from radiative transfer effects dependent on the amount and spatial distribution of dust relative to different stellar populations (cite: 2018ApJ...869...70N; 2020MNRAS.491.3937T). For instance, the increasing complexity of the dust-to-star geometry flattens the slope of the dust attenuation curve and reduces the prominence of the UV bump, regardless of the initial dust extinction curve(cite: 1999ApJS..123..437F; 2018ApJ...869...70N).

The dust attenuation/extinction laws of high-$z$ sources remain largely unknown. Only a handful of early star-forming galaxies(cite: 2022A&A...663A..50B; 2023A&A...679A..12M; 2023Natur.621..267W), quasars(cite: 2010A&A...523A..85G; 2021MNRAS.506.3946D), and gamma-ray burst (GRB) afterglows(cite: 2011A&A...532A..45S; 2018A&A...609A..62B) have constrained dust curves. Dust laws at high-$z$ are expected to deviate from the well-established empirical dust curves of the local galaxies, such as the "Calzetti"(cite: 2000ApJ...533..682C) attenuation curve for local starbursts, and the Small Magellanic Cloud (SMC)(cite: 2003ApJ...594..279G) and the Milky Way (MW) extinction curves(cite: 1989ApJ...345..245C). This redshift ($z$) evolution may arise from several factors such as distinct dust formation processes(cite: 2017ApJ...851..152B; 2020A&A...637A..32B), and dust reprocessing mechanisms(cite: 1978ppim.book.....S; 1980ApJ...239..193D) occurring in the more extreme ISM conditions(cite: 2019MNRAS.489....1F; 2019MNRAS.487.1689P; 2022MNRAS.513.5621P; 2020MNRAS.495L..22V; 2022A&A...663A.172M) of early galaxies. Additionally, galaxies at intermediate(cite: 2009ApJ...706.1364F; 2022MNRAS.516.3532M) and high-$z$(cite: 2023MNRAS.522.3986F; 2023A&A...677L...4P) tend to be less dusty and show a clumpier structure and irregular distribution of dust and gas with respect to stars, compared to nearby sources(cite: 2018MNRAS.477..552B; 2018MNRAS.478.1170C; 2020A&A...641A..22M; 2022MNRAS.517.5930S).

In this Letter, we apply our customized version of the `BAGPIPES` code(cite: 2018MNRAS.480.4379C; 2023A&A...679A..12M) to a large sample of star-forming galaxies at $z \sim 2-12$, from the publicly available *James Webb* Space Telescope (JWST) spectroscopic observations, to investigate evolutionary trends of dust attenuation laws and their implications on the intrinsic dust properties and dust-to-star geometry.

# Redshift evolution of dust attenuation law

We employ our customized version of `BAGPIPES` code(cite: 2018MNRAS.480.4379C; 2023A&A...679A..12M) to fit the individual spectra of a sample of 173 galaxies at $z \sim 2-12$ observed by JWST. The code generates the best-fit model to the NIRSpec spectra and provides the best-fit parameters of the SED model from the medians of the posterior distribution. Outputs of the SED fitting process include fundamental physical characteristics of galaxies (stellar mass ($M*$), star formation rate (SFR), metallicity ($Z$), mass-weighted stellar age ( ${\langle a \rangle}_*^{\rm{m}}$), ionization parameter $U$, and $V$-band dust attenuation ($A_V$)) along with the properties of the dust attenuation model ($c_1 - c_4$; see the SED fitting section for details). We utilize the $c_1 - c_4$ parameters to construct the dust attenuation curve for each galaxy. The inferred attenuation curves of our sample exhibit a wide diversity of slopes and UV bump strengths (see Fig. [1](#all_curves) and the Galaxy Sample section).

To explore potential trends in dust attenuation evolution, we split our sample in redshift bins by adopting equidistant cosmic time in each bin ($\Delta t \sim 0.5 \ \rm{Gyr}$). The number of sources per bin varies in the 13-66 range.

Fig. [2](#all_curves_bin) depicts the median dust curves with the corresponding 1$\sigma$ dispersion for each subsample. Although the associated uncertainties are relatively large, a noticeable trend emerges in the evolution of the dust attenuation curves with redshift. Specifically, with increasing redshift, the median slope flattens and the strength of the UV bump decreases.

To provide a more quantitative analysis of these results, we characterize the shape of the dust attenuation curve with the $S$ and $B$ parameters, which represent proxies for the UV-optical slope and the 2175 Å bump strength, respectively(cite: 2020ARA&A..58..529S). The slope is defined by the ratio of attenuation at $1500$ Å and the one in the $V$-band, $S  = A_{1500}/A_V$. The UV bump strength is defined as $B = A_{\rm{bump}}/A_{2175}$, where $A_{\rm{bump}}$ is the additional attenuation above the baseline at 2175 Å, and $A_{2175}$ is the total attenuation at 2175 Å (see the Attenuation curve parametrization section). The trends that we see in Fig. [2](#all_curves_bin) remain apparent when we plot the UV-optical dust curve slope ($S$) and UV bump strength ($B$) separately, as functions of redshift (Figs. [3](#z_S)a and [3](#z_S)b, respectively).

## Redshift evolution of the slope

Fig. [3](#z_S)a illustrates the redshift evolution of the UV-optical slope ($S$), for each source of our full JWST sample, and median values for subsamples grouped by redshift (as in Fig. [2](#all_curves_bin)). The median slope of $z \sim 2-3.5$ galaxies approaches the SMC slope(cite: 2003ApJ...594..279G). However, it gradually flattens with increasing redshift ($z \sim 3.5-5.5$) and at $z > 5.5$ for galaxies is flatter than the MW slope(cite: 1989ApJ...345..245C).

The median slopes of galaxies at intermediate-$z$ are slightly steeper (although they are consistent within the 1$\sigma$ uncertainties) with respect to most of the inferred slopes of various samples of intermediate-$z$ galaxies from the literature. The discrepancy can be attributed to the fact that our overall JWST sample has a median $A_V$ of $\sim 0.38$. Conversely, the values of $A_V$ for most galaxy samples in the literature are somewhat higher, $A_V \sim  0.9$(cite: 2011A&A...533A..93B), ${A_V} \gtrsim  0.5$ (cite: 2012A&A...545A.141B; 2013ApJ...775L..16K; 2015ApJ...800..108S; 2015ApJ...806..259R), $A_V \sim  0.2-1.1$(cite: 2018MNRAS.475.2363T), and $A_V \sim  0.3-0.9$(cite: 2020ApJ...899..117S). Therefore, this difference in slopes is a consequence of a well-known trend wherein galaxies with low $A_V$ tend to have steeper UV-optical slopes(cite: 2013MNRAS.432.2061C; 2018ApJ...869...70N; 2022A&A...663A..50B). If we instead restrict our JWST sample to more attenuated galaxies (with $A_V > 0.38$), our results are more aligned with the slopes inferred for known samples of $z \sim 1-3$ galaxies. Additional potential origin of this discrepancy is discussed in the Observational and model uncertainties section.

Fig. [3](#z_S)a also depicts the best fit on the entire sample whereas Fig. [4](#z_S_Av) shows the best fit on subsets of sources with $A_V \sim 0.1-0.38$ and $A_V \geq 0.38$. We see that the slope of the attenuation curve (at fixed redshift) flattens with increasing $A_V$ (despite significant uncertainties), as expected. This effect is more evident at lower redshifts ($z \lesssim 4$), whereas at $z \gtrsim 6$ the dust attenuation curves remain shallow, and are largely unaffected by variations in $A_V$. Furthermore, the analysis of $A_{\lambda}(z)$ in different $A_V$ ranges shows that the flattening trend towards high-$z$ persists irrespective of the $A_V$ values considered. This implies that $A_V$ is not the driver of the redshift evolution of the slope. Additionally, we examine if the flattening trend stems from an underlying dependence on other galaxy properties (e.g., $M*$, SFR, $Z$, ${\langle a \rangle}_*^{\rm{m}}$, and $U$), but the overall trends remain regardless of the considered parameters (Extended Data Figs. [5](#z_S_logM), [6](#z_S_age), [7](#z_S_SFR), [8](#z_S_Z), and [9](#z_S_logU)).

## Redshift evolution of the UV bump strength

Fig. [3](#z_S)b depicts the redshift evolution of the UV bump strength ($B$). Similarly to the observed trends with the slope $S$, $B$ also exhibits a general decrease as redshift increases. The median $B$ value reaches levels comparable to $\sim 20-25\%$ of the MW bump strength in the $z \sim 2-4$ range. This is comparable with the inferred $B$ values of the intermediate-$z$ galaxies found in the literature(cite: 2011A&A...533A..93B; 2013ApJ...775L..16K), although the uncertainties remain relatively high. To further support this result, we emphasize that if we characterize the UV bump strength using the $c_4$ parameter (Eq. [\[dust_law\]](#dust_law)(cite: 2008ApJ...685.1046L)), we observe comparable trends in the redshift evolution of the UV bump strength (Extended Data Fig. [10](#z_c4)).

The presence of the UV bump has been confirmed with a significance level of $>3\sigma$ ($B/B^{\rm{err}} > 3$), for 28 sources, within the $z \sim 2-8$ range (marked by red open circles in Fig. [3](#z_S)b). This accounts for $\sim 16\%$ of the full JWST sample. However, $B$ is not well constrained and exhibits high uncertainties due to error propagation. If instead we use the $c_4$ parameter, which is better constrained as an output of the SED fitting procedure, we obtain a securely detected UV bump in $\sim 21\%$ of the sources (red open circles in Extended Data Fig. [10](#z_c4)). This percentage ($\sim 21\%$) is consistent with previous results (cite: 2009A&A...499...69N; 2012A&A...545A.141B) found in samples of $z \sim 1.0-2.5$ galaxies. The median bump strength of sources with UV bump detection is ${B} \approx 0.7 \times B^{\rm{MW}}$, i.e., ${c_4} \approx 0.75 \times \ {c_4}^{\rm{MW}}$.

Applying both $B$ and $c_4$ parameterizations, we confirm that the highest redshift galaxy of our JWST sample with a reliable UV bump detection is the 1433_3989 source at $z \sim 6.14$ (Fig. [11](#spec)a-c). The UV bump strength for 1433_3989 is measured as $B = 0.43 \pm 0.05$ ($>9\sigma$) or $c_4 = 0.083 \pm 0.014$ ($>6\sigma$), which corresponds to a factor of $\sim 1.2$ or $\sim 1.6$ higher than the MW bump, depending on the considered parametrization. Moreover, the highest redshift source with a confirmed UV bump detection using only the $B$ parameter is the 2750_449 source at $z \sim 7.55$ (Fig. [11](#spec)d-f). The UV bump strength for 2750_449 is quantified as $B = 0.34 \pm 0.10$ ($> 3\sigma$) or $c_4 = 0.054 \pm 0.025$ ($> 2\sigma$) (i.e., $\sim 0.95$ or $\sim 1.05$ of the MW bump).

# Discussion

Our results show that the attenuation law evolves with redshift. Specifically, the attenuation slope flattens (from $S>4$ at $z\sim 2$ to $S \sim 2$) at $z> 8$. This trend is found independently of the value of $A_V$. Furthermore, the strength of the UV bump decreases and eventually disappears (from $B\sim 0.1$ at $z\sim 2-4$ to $B\sim 0$ at $z> 5.5$) at early epochs.

We now turn to the interpretation of these findings. In principle, the observed evolutionary trends can be explained by three scenarios: radiative transfer (RT) effects dependent on (1) the amount of attenuation, i.e. $A_V$, or (2) dust distribution relative to stars of various ages, or (3) changes in the intrinsic dust properties (primarily grain size distribution and chemical composition). Although in general identifying the dominant factor is challenging(cite: 2013ARA&A..51..393C), the quality of the present data allows us to draw solid conclusions.

It is well established that smaller (larger) $A_V$ values produce steeper (flatter) attenuation curves. Such correlation has been both predicted(cite: 2013MNRAS.432.2061C; 2018ApJ...869...70N; 2020MNRAS.491.3937T) and observed(cite: 2016ApJ...827...20S; 2020ARA&A..58..529S). The physical interpretation is that, in the low-$A_V$ (optically thin) limit, UV photons have a higher probability of being scattered and eventually absorbed, leading to the steepening of the slope(cite: 2013MNRAS.432.2061C; 2023MNRAS.519.2475H). In the high-$A_V$ (optically thick) limit, the shape of the curve is flattened by both scattering into the LOS and radiation from unobscured OB stars (cite: 2018ApJ...869...70N). Indeed, we also find (Fig. [4](#z_S_Av)) that *at fixed redshift* S increases with decreasing $A_V$. However, we do see that the flattening trend towards high-$z$ persists irrespective of $A_V$. We can then rule out the first scenario.

Scenario (2) is based on the evidence that complex dust-to-star geometries flatten the slopes and reduce the UV bump strengths of dust attenuation curves(cite: 1999ApJS..123..437F; 2000ApJ...539..718C; 2018ApJ...869...70N; 2020MNRAS.491.3937T) as in those conditions UV photons from young stars escape more easily. Although the detailed distribution of dust and gas in galaxies is often not easy to measure, a clumpy ISM structure is commonly reported for galaxies across the entire redshift range $z \sim 2-11.5$ considered here (cite: 2018MNRAS.477..552B; 2018MNRAS.478.1170C; 2019MNRAS.489.2792Z; Fujimoto24; Adamo24). This suggests that the overall complex dust-to-star geometry at $z \sim 2-11.5$ alone may not be sufficient to explain the observed trends in attenuation curves across the considered redshift range. Thus, scenario (2) seems unlikely.

Scenario (3) invokes changes in the grain properties. First, we note that our results are consistent with predictions from theoretical studies(cite: 2018MNRAS.478.2851M; 2020MNRAS.492.3779H; 2022MNRAS.517.2076M) that have investigated the cosmological evolution of interstellar dust. A recent study(cite: 2022MNRAS.517.2076M) finds that, at a fixed metallicity, extinction curves flatten and the UV bump becomes less prominent with redshift. The study concluded that such trends are driven by a shift in the grain size distribution, favouring larger grains at early epochs. What causes such a shift?

The early prevalence of large grains could be attributed to dust production mechanisms in the ejecta of core-collapse Type II supernovae (SNII(cite: 2001MNRAS.325..726T; 2007ApJ...666..955N; 2014Natur.511..326G)). These dust sources are predicted to predominantly form large ($\approx 0.1 \mu$m) grains(cite: 2007ApJ...666..955N; 2013EP&S...65..213A; 2014Natur.511..326G; 2018MNRAS.478.2851M). Grains are then released into the ISM where they undergo shattering processes(cite: 2013MNRAS.432..637A; 2018MNRAS.478.2851M; 2020MNRAS.492.3779H; 2022MNRAS.517.2076M) breaking them into smaller units. However, shattering is a rather slow process, with typical timescales of $\gtrsim 0.5-1 \ \rm{Gyr}$(cite: 2013EP&S...65..213A; 2018MNRAS.478.2851M). Consequently, the transition from large to smaller grains is quite gradual and is completed only by $z\approx 6$. Alternatively, small grains might be preferentially destroyed by Coulomb explosions in the presence of strong radiation fields (cite: 2020ApJ...892..149T; 2020ApJ...892...84T) as the ones present in early, compact galaxies.

The redshift evolution of $S$ and $B$ (or $c_4$) we find supports the third scenario. Importantly, the slope remains consistently shallow with a small dispersion at $z \gtrsim 5.5$. This might be interpreted with the existence of a single, dominant dust formation channel (i.e. SNII), in which large grains are formed and only minimally reprocessed in the ISM in the limited cosmic time available(cite: 2014Natur.511..326G; 2018ApJ...868...62G). The decrease of the bump strength towards high-$z$ also supports this interpretation, as SNII yields ($\sim$90% of silicate and $\sim$10% of carbon dust) are scarce of carbonaceous grains(cite: 2020MNRAS.492.3779H).

At $z \lesssim 5-5.5$, a larger variety of attenuation curves is observed. This is likely due to a combination of several effects, including the transition from SNII to asymptotic giant branch (AGB) stars(cite: 1997A&A...326..305W; 2006A&A...447..553F) as the dominant dust sources, dust growth in the ISM(cite: 2013EP&S...65..213A; 2019A&A...624L..13L), more efficient shattering and sputtering(cite: 2013MNRAS.432..637A; 2018MNRAS.478.2851M; 2020MNRAS.492.3779H; 2022MNRAS.517.2076M). Concurrently, the UV bump emerges at $z \lesssim 5$ (around $\sim 1.2 \ \rm{Gyr}$), marking the epoch when dust formation in AGB stars becomes dominant, leading to enhanced production of carbonaceous grains. Finally, a marginal decrease in both $S$ and $B$ at $z \lesssim 3.4$ may be attributed to processes such as coagulation and accretion becoming more prominent at later epochs(cite: 2013MNRAS.432..637A; 2020MNRAS.492.3779H).

In summary, the flattening of dust attenuation curves at high-$z$ suggests that we might be observing galaxies through a curtain of dust newly formed in SNII ejecta, although other less likely explanations cannot be completely excluded. Progress might come from cosmological hydrodynamic simulations including dust and related RT effects(cite: 2018MNRAS.477..552B; 2021MNRAS.506.3946D; 2024arXiv240218515D). These will make it possible to accurately determine the dust-to-star geometry, incorporate and explore different intrinsic dust properties (grain size distribution and chemical composition), and take into account RT effects. In parallel, insights into the intrinsic dust properties of high-$z$ sources can be gained via observations of point-like sources, such as quasars(cite: 2004Natur.431..533M; 2010A&A...523A..85G), and gamma-ray burst afterglows(cite: 2011A&A...532A..45S; 2018A&A...609A..62B).

# Methods

## Spectroscopic data

We use publicly available Near Infrared Spectrograph (NIRSpec) data retrieved from the DAWN JWST Archive (DJA)(cite: DAWN), an initiative of the Cosmic Dawn Center. DJA includes all publicly available Cycle 1 and 2 spectroscopic and photometric observations from various JWST surveys. The data reduction was performed entirely and uniformly with `GRIZLI` (Grism redshift and line analysis software for space-based slitless spectroscopy(cite: brammer_2023_8370018)) and `MSAEXP` (Tool for extracting JWST NIRSpec Micro-Shutter Assembly (MSA) spectra(cite: Brammer_msaexp_NIRSpec_analyis_2022)) Python scripts, by the Cosmic Dawn Center.

Here, we focus on the analysis of NIRSpec prism spectra. The output 1D spectra achieve wavelength-dependent resolution of $R \sim 30-300$, ranging from $\lambda \sim 0.6-5.3 \ \mu m$. This allows us to probe the nebular lines and continuum emission from rest-frame UV to IR. However, due to the limited velocity resolution of $\gtrsim 1000\ \mathrm{km \ s^{-1}}$, we are unable to resolve nebular emission lines. A fraction of the spectral region below the wavelength of the Ly$\alpha$ line is selectively masked due to the potential contamination by the intervening neutral intergalactic medium (IGM).

## Sample selection

Our target selection process closely follows the one outlined in our recent work(cite: 2023A&A...679A..12M). We conduct a visual inspection of all grade 3 NIRSpec prism spectra, opting for galaxies exhibiting a prominent continuum and nebular line emission while excluding sources with strong negative features.

We select sources at $z>2$ to ensure that we can effectively probe the rest-frame UV-optical wavelength range, allowing us to accurately constrain the shape of the dust attenuation curve and the potential presence of the UV bump. We further clean our sample by selecting spectra with an average channel Signal-to-Noise (S/N) ratio of $\mathrm{S/N} > 3$, in the rest-frame wavelength range of $1925-2425$ Å, corresponding to the peak position of the UV bump ($2175$ Å). Additionally, we conduct a visual examination of the spectral energy distribution (SED) fits for all sources observed with NIRSpec. Any objects for which the SED models cannot yield a reasonable fit within the associated uncertainties are excluded from further consideration.

Finally, we exclude galaxies that exhibit negligible dust attenuation (i.e., with $A_V \sim 0$) from our initial sample. For a galaxy to be considered "dusty", it must meet two criteria: (1) $V-$band dust attenuation of $A_V > 0.1$; (2) $A_V > 0$ with a significance of $> 3\mathrm{\sigma}$ ($A_V/A_V^{\rm{err}} > 3$).

## Galaxy sample

We ended up with a final sample of 173 "dusty" galaxies. These galaxies fall within a spectroscopic redshift range of $2.0 \lesssim z \lesssim 11.4$, with a median redshift of ${z} \approx 4.5$), with stellar masses of $6.9 \lesssim \log{M_*/M_{\odot}} \lesssim 10.9$, star formation rates $0.1 \lesssim \rm{SFR}/M_{\odot} \ \rm{yr^{-1}} \lesssim 240$ and $V$-band dust attenuation $0.1 \lesssim A_V \lesssim 2.3$ (Supplementary Fig. 1).

Fig. [1](#all_curves) depicts a large diversity of attenuation curves of our full JWST sample. For instance, the slopes range from those shallower than the Calzetti curve to the ones considerably steeper than the SMC curve. The strength of the UV bump varies considerably from curves in which it is completely absent (as in the SMC case) to those surpassing the bump strength observed in the MW. In Fig. [1](#all_curves) we also plot the median attenuation curve along with its 1$\sigma$ uncertainties, computed from the full JWST sample. The median curve and its dispersion are derived using a bootstrapping approach.

## Slit-loss correction

The flux values at a given wavelength reported in JWST NIRSpec micro-shutter assembly (MSA)-based data may not always coincide with the ones reported in photometric data. The discrepancy between the NIRSpec MSA spectra and the photometric data can arise from several factors such as slit-losses, flux calibration of both spectra and photometry, and spectroscopic and photometric aperture. Slit-loss refers to the reduction in the observed flux in spectroscopic data due to extension and off-centred location of the science target in the NIRSpec spectrograph shutters of finite dimensions ($0.20" \times 0.46"$)(cite: JWST-docs; 2016SPIE.9910E..1OB). The impact of slit-loss is wavelength-dependent since the full width at half maximum (FWHM) of the point spread function (PSF) widens with increasing wavelength.

To address the impact of slit-loss and correct for the discrepancy between the NIRSpec spectra and the photometric data, we employ the following approach. First, we utilise the Python tool by DJA(cite: DAWN) to extract photometry from *Hubble* Space Telescope (HST), JWST Near-Infrared Camera (NIRCAM), and JWST Near-Infrared Imager and Slitless Spectrograph (NIRISS), using the right ascension, declination and redshift for each target. Next, we overlay the photometric points onto the spectrum for comparison. The discrepancy between the spectroscopic and photometric data is observed in $94\%$ of the sources from our sample. It can reach up to a factor of $6-9$ in the most extreme cases of very extended and/or off-centred sources. In case of a discrepancy, we correct the spectrum by dividing it with one of the throughputs provided by the JWST user documentation(cite: JWST-docs), until achieving a satisfactory alignment between the spectra and photometry.

To assess potential systematic uncertainties arising from the above-mentioned slit-loss correction method reliant on visual inspection, we adopt an alternative approach to take into account slit losses. This method involves quantifying the discrepancy between photometric and spectroscopic flux density measurements for each source ($\rm{f_{\lambda}^{phot}/f_{\lambda}^{spec}}$) and performing an uncertainty-weighted linear fit on these quantities. Subsequently, we utilize this linear regression function to correct the spectra affected by slit losses. By applying this reproducible and consistent methodology across our entire galaxy sample, we minimize potential inconsistencies and systematic errors. We find that our results closely mirror the initially reported redshift trends of dust attenuation curves (Figs. [2](#all_curves_bin) and [3](#z_S)), as demonstrated in supplementary Fig. 2.

Moreover, in Supplementary Fig. 3, we present the redshift trends of the attenuation curve, as well as the $S$ and $B$ parameters derived from SED fitting on spectra without correction for slit losses. In summary, our primary findings regarding the overall redshift trends of the slope ($S$) and the bump ($B$) remain consistent regardless of the application of slit-loss correction or the method employed for it.

## FIR observations

Although a significant portion of our sample sources is expected to exhibit sufficient brightness in the continuum emission within the FIR spectrum to be detectable with submillimeter facilities, given their typical SFR around $\rm{SFR \sim 4 M_{\odot}}$, we delved into the available ALMA data. A considerable fraction of our sources ($>60\%$), remained beyond the observational reach of ALMA due to their positioning in the northern sky, with $\delta > 20^\circ$. The remaining 69 sources of our JWST sample are distributed across the GOODS-South (50), Abell 2744 (17), and RXJ 2129 (2) fields. These sources include 13 (17) sources exhibiting UV bump detections, based on the $B$ ($c_4$) parameter.

Out of these 69 galaxies, ALMA data is available for 62 of them. Specifically, 49 out of 50 sources from GOODS-S were part of the GOODS-ALMA (2015.1.00543.S; PI: D. Elbaz)(cite: 2018A&A...620A.152F), ALMA Hubble Ultra Deep Field (2012.1.00173.S; PI: J. Dunlop)(cite: 2017MNRAS.466..861D), HUDF-JVLA-ALMA (2015.1.00098.S, PI: K. Kohno)(cite: 2018PASJ...70..105H), and GOODS-S (2017.1.00755.S; PI: D. Elbaz)(cite: 2022A&A...658A..43G) 1.1-1.3 mm surveys. Additionally, 13 out of 17 Abell 2744 sources were surveyed in MOSAIC-D (2022.1.00073.S; PI: S. Fujimoto)(cite: 2023arXiv230907834F) and Abell_2744 (2018.1.00035.L; PI: K. Kohno)(cite: 2022ApJ...932...77S) studies. Finally, ALMA did not observe the two sources within the RXJ 2129 field. Despite the accessibility of ALMA data for these 62 sources, none of them have produced statistically significant detections across the various surveyed datasets.

## SED fitting

In our recent study(cite: 2023A&A...679A..12M), we presented a customized version of the `BAGPIPES` SED fitting code(cite: 2018MNRAS.480.4379C) that enables us to simultaneously constrain the fundamental physical properties of galaxies (e.g. SFR, $M_*$, $Z$) and the shape of their dust attenuation law. Our tool has been thoroughly tested on synthetic spectra attenuated by empirical dust curves(cite: 2023A&A...679A..12M). In this section, we give a summary of our method.

`BAGPIPES` is a Bayesian SED fitting code that generates realistic galaxy spectra using the Stellar Population Synthesis (SPS) models(cite: 10.1093/mnras/stw1756), nebular emission models pre-computed with `CLOUDY` photoionization code(cite: 2017RMxAA..53..385F), and InterGalactic Medium (IGM) models(cite: 2014MNRAS.442.1805I). The Star Formation History (SFH) can be parameterized with various parametric and flexible SFH models. We employ the non-parametric SFH model with a "continuity" prior as our fiducial SFH model, since it allows greater flexibility in fitting the "true" SFHs and constraining less biased physical properties of galaxies, compared to parametric models(cite: 2019ApJ...876....3L; 2022MNRAS.516..975T; 2023A&A...679A..12M).

The warm dust emission component within HII regions is included in `CLOUDY`, whereas the cold dust emission component within the neutral ISM is modelled with the grey body emission. The dust attenuation recipe includes a two-component dust screen model(cite: 2000ApJ...539..718C) to account for extra attenuation toward the stellar birth clouds. Dust attenuation can be modelled using standard empirical templates: "Calzetti"(cite: 2000ApJ...533..682C) attenuation curve, SMC(cite: 2003ApJ...594..279G) and MW extinction curves(cite: 1989ApJ...345..245C) and flexible dust models(cite: 2000ApJ...539..718C; 2018ApJ...859...11S). We implement the analytical dust attenuation law(cite: 2008ApJ...685.1046L) into `BAGPIPES` and we use it as our fiducial dust attenuation model. The analytical form of the dust attenuation law, normalised by $A_V$ is:

$$\begin{equation}
 \label{dust_law}
\begin{split}   
A_{\lambda}/A_V &= \frac{c_1}{(\lambda/0.08)^{c_2}+(0.08/\lambda)^{c_2} +c_3} \\ 
& +  \frac{233[1-c1/(6.88^{c_2}+0.145^{c_2}+c_3)-c_4/4.60]}{(\lambda/0.046)^2+(0.046/\lambda)^2+90} \\ 
& + \frac{c_4}{(\lambda/0.2175)^2+(0.2175/\lambda)^2-1.95},
\end{split}
\end{equation}$$ where $c_1, ...,c_4$ are dimensionless parameters and $\lambda$ is the wavelength in $\mu$m. The three components of the Drude model describe the rise in far ultraviolet (FUV) attenuation, attenuation within the optical and near-infrared (NIR) spectrum, and the $2175$ Å bump, respectively. The main advantage of this flexible dust model is its capability to replicate local empirical dust curves (Calzetti, MW, SMC), along with all the fundamental properties of (synthetic) galaxies(cite: 2023A&A...679A..12M). Additionally, we note that the dust attenuation model flexibility enables the recovery of any potential variations in the dust attenuation laws of early galaxies(cite: 2023A&A...679A..12M). This aspect is significant in the case of high-redshift galaxies since there are no physical reasons to support the notion that dust attenuation curves in early epochs resemble any of the dust laws observed in the local Universe. In this work, we apply our tool to a large sample of high-redshift galaxies, and we showcase the flexibility of the dust model to capture large variations in both the slope of the attenuation curve and the UV bump strength. Nevertheless, it is important to note that the dust attenuation model sets the central wavelength and FWHM of the UV bump at fixed values of $\lambda_0 = 2175$ Å and $\rm{FWHM} \sim 475$ Å, respectively. The central wavelength of the UV bump feature exhibits minimal variation, at least locally(cite: 1989IAUS..135..313D). Hence, fixing the central wavelength at $2175$ Å is a reasonable assumption to make. Nonetheless, several studies of the FWHM of the UV bump at intermediate redshifts ($z \sim 2$) have reported smaller FWHM values, of a factor of $> 2$. This restriction might limit the model’s ability to capture variations of these UV bump parameters, which may be observed at higher redshift(cite: 2022MNRAS.514.1886S; 2023Natur.621..267W).

`BAGPIPES` is based on a Bayesian approach and the MultiNest nested sampling algorithm(cite: 2019OJAp....2E..10F). `BAGPIPES` requires to provide the instructions on the SED model, that is, the parameters of the model components (e.g., SFH, nebular emission, and dust attenuation) and their priors. The prior probability distributions for each of the parameters of the model are given in Supplementary Table 1.

In this work, the selected prior probability densities for model parameters are nearly identical to those of our initial work(cite: 2023A&A...679A..12M). The priors on the the dust attenuation parameters are carefully selected to encompass the parameter range of the dust model fit to Calzetti, SMC, LMC, and MW templates, as well as any potential unconventional attenuation curve variations. However, the allowed prior limits on all parameters have been expanded to encompass a potentially wider parameter space that could be relevant for a larger galaxy sample spanning a significantly broader redshift range of $z\sim 2-12$. For instance, prior limits are set to allow super-solar metallicities (up to $Z \sim 2.5 \ Z_\odot$), high dust content ($A_V \sim 8$, and prominent UV bump ($c_4 \sim 0.1$).

The prior limits of the UV bump parameter $c4$ (related to $B$) are set as $-0.005 < c_4 < 0.01$. These limits are designed to accommodate the potential convergence of $c4$ towards zero, a trait observed in certain well-known attenuation/extinction curves lacking a distinct UV bump, such as the SMC and Calzetti curves. As a result, there is a possibility for $c_4$ to occasionally yield slightly negative values during SED fitting (as seen in Extended Data Fig. [10](#z_c4)). However, it is important to note that such negative values are most probably not indicative of any physical phenomenon but rather a consequence of the constraints imposed by our prior limits.

## Statistical tests

To evaluate the quality of the fit, we initially rely on visual inspection to assess how accurately the SED model captures the features and trends present in the observed spectra.

Additionally, we compute the residuals between the observed and modelled spectra, as illustrated in Figs. [11](#spec)b and [11](#spec)e.

Next, we adopt a frequentist $\rm{\chi^2}$ test approach for assessing the goodness-of-fit and consistency for Bayesian models from the SED fitting procedure(cite: 2016A&A...588A..19L). Specifically, we utilize the chi-square statistics. Here, $\chi^2$ is defined as the difference between the observed and the modelled flux densities normalized by the observed errors:

$$\begin{equation}
\rm{\chi^2 = \sum_{i=1}^{n} \frac{(f_{\lambda}^{obs} - f_{\lambda}^{model})^2}{\sigma_{obs}^2}}.
\end{equation}$$

The reduced chi-square statistic $\chi_\nu^2 = \chi^2/\nu$, represents the total chi-square of each source $\chi^2$, normalised by the degrees of freedom, $\nu$. The degrees of freedom are calculated as $\nu = n - k$, where $n$ denotes the number of data points, while $k$ signifies the number of model parameters(cite: 2023A&A...679A..12M) ($k = 16$ for our fiducial model; Supplementary Table 1).

Our analysis reveals that the distribution of $\chi_\nu^2$ is in the range of $\chi_\nu^2 = 4.1_{1.5}^{6.3}$. Notably, three sources exhibit $\chi_\nu^2 >100$, primarily due to particularly noisy spectra at shorter wavelengths ($\rm{\lambda_{rf} < 2000}$ Å). However, removing the high-$\chi_\nu^2$ sources does not affect the identified trends.

Additionally, we present the $\chi_\nu^2$ measurements for two high-$z$ sources showing UV bump detections at the highest redshifts (Figs. [11](#spec)a and [11](#spec)d).

We compared the quality of fits between our fiducial model, featuring a flexible analytical dust attenuation model, and a SED fitting model using a Calzetti-like dust attenuation template for our galaxy sample(cite: 2023A&A...679A..12M). Our analysis shows that the fiducial model performs significantly better for 148 out of 173 sources ($\sim86\%$), with a $\rm{p-value} < 0.05$. The p-value distribution is heavily skewed towards lower values, emphasizing the fiducial model’s superior performance. 22 sources ($\sim 13\%$) have a p-value of $0.05 - 1$ indicating that the fiducial model provides a better fit, but the improvement is not statistically significant. The fiducial model does not significantly enhance the fit for the remaining 3 sources ($\sim 2\%$), with a $\rm{p-value} = 1$. However, many sources with high p-values exhibit a flat Calzetti-like curve (constrained by the analytical attenuation model). Additionally, a few sources show poorer SED fits due to noisy spectra in the rest-frame UV. Excluding sources with high p-values from our analysis does not alter the inferred redshift trends.

Furthermore, we compared the fit to the spectra using the fiducial dust attenuation model and a bump-free model (with $c_4 = 0$)(cite: 2023A&A...679A..12M), for a subsample of 28 galaxies with a UV bump detection (right panel of Fig. [3](#z_S)). Our analysis shows that our fiducial model provides a significantly better fit for 24 out of 28 sources ($\sim 86\%$), with a $\rm{p-value} < 0.05$. This includes both high-redshift sources with UV bump detection (Fig. [11](#spec)). The p-value distribution is significantly skewed towards 0, once again emphasizing the enhanced performance of our fiducial model. For one source, a p-value $\sim 0.2$ indicates a somewhat better fit with the fiducial model. In the remaining three sources, the UV bump does not enhance the fit significantly (p-value $\sim 1$), but both models show poorer SED fits due to noisy spectra in the rest-frame UV.

## Attenuation curve parametrization

To compare our constrained dust attenuation curves with those documented in the literature, we employ the parameterization introduced by Salim & Narayanan (2020)(cite: 2020ARA&A..58..529S). The primary parameters of their work that provide information about the wavelength-dependent attenuation characteristics are the UV-optical slope ($S$) and UV bump strength ($B$)(cite: 2020ARA&A..58..529S). The slope, $S$ is defined as $S  = A_{1500}/A_V$, where $A_{1500}$ is attenuation at $\lambda = 1500$ Å and $A_V$ is the attenuation in the $V$-band (i.e., at $\lambda = 5500$ Å).

The UV bump strength, $B$ is defined as $B = A_{\rm{bump}}/A_{2175}$, where $A_{\rm{bump}}$ refers to the extra attenuation attributed to the bump above the baseline at $\lambda = 2175$ Å, and $A_{2175}$ is the total attenuation at $\lambda = 2175$ Å. We note that in the original parametrization of the UV bump with the B parameter(cite: 2020ARA&A..58..529S), the baseline at 2175 Å is calculated using a relation derived from simulated attenuation curves(cite: 2018ApJ...869...70N) $A_{2175, 0} = 0.33A_{1500} + 0.67A_{A3000}$. In this work, we derive the 2175 Å baseline by fitting the dust curve with an analytical dust model(cite: 2008ApJ...685.1046L) and setting the $c_4$ parameter (which serves as a proxy for the UV bump strength) as $c_4 = 0$. This approach allows us to constrain the UV bump parameter $B$ more precisely, with slightly reduced uncertainties.

In Figs. [1](#all_curves) and [2](#all_curves_bin) the median attenuation curves and their dispersion are derived from the $16^{th}$, $50^{th}$, and $84^{th}$ percentiles of a set of 5000 attenuation curves that are generated using a bootstrapping approach, which involves 5000 random sampling of the $c_1-c_4$ parameters constrained for the given galaxy (sub)sample.

In Figs. [3](#z_S) $-$ [4](#z_S_Av) and Extended Data Figs. [5](#z_S_logM) $-$ [9](#z_S_logU) the values of $S$ and $B$ for each galaxy (grey stars) are determined through the application of the dust attenuation model, $A_{\lambda}/A_V = f(\lambda, c_1, c_2, c_3, c_4)$ (Eq. [\[dust_law\]](#dust_law)), where the $c_1-c_4$ parameters are the outputs of the SED fitting procedure for each source. Next, the uncertainty on $S$ and $B$ represents $1\sigma$ dispersion from the median, estimated by employing a boot-strapping approach, which involves generating 100 attenuation curves $A_{\lambda}/A_V$ from a random sampling of the $c_1-c_4$ parameters from the posterior. In Fig. [3](#z_S), the median values and 1$\sigma$ dispersion of $S$ and $B$ parameters of subsets of galaxies grouped by redshift (black stars) are estimated directly from the distribution of these parameters within each subset.

In Figs. [3](#z_S) $-$ [4](#z_S_Av) and Extended Data Figs. [5](#z_S_logM)$-$[9](#z_S_logU), the slope-redshift and UV bump-redshift relations have the form $\log{S} = k_1 \log{z} + n_1$ and and $B = k_2 z + n_2$. The best-fit values for the model parameters $k_i$ and $n_i$, along with their $1\sigma$ uncertainties are obtained using a `numpy polyfit` function, as

$$\begin{equation}
    \log{S} = (-0.580 \pm 0.064) \log{z} + (0.882 \pm 0.042),
\end{equation}$$

$$\begin{equation}
    B = (-0.020 \pm 0.05) z + (0.167 \pm 0.025).
\end{equation}$$

The uncertainties on the best-fit values of $S$ and $B$, are calculated by propagating the errors in the fitted parameters $k_i$ and $n_i$, and represents the $1\sigma$ standard error of the predicted values of $S$ and $B$.

In Extended Data Fig. [10](#z_c4), the $c_4$ parameter along with its associated uncertainty for each source represents the median and 1$\sigma$ dispersion of the posterior distribution. The values and uncertainties of the $c_4$ parameter for a subset of galaxies grouped by redshift, as well as the $c_4$-redshift relation are determined analogously as the $B$ parameter in Fig. [3](#z_S)b.

We have compared the V-band attenuation, $A_V$, derived from SED fitting to values from the Balmer decrement, $A_V^{\rm{BD}}$. We find that over $25\%$ of the galaxies in the sample are characterised by negative $A_V^{\rm{BD}}$(cite: 2015ApJ...806..259R; 2023ApJ...949L..11M; 2023arXiv230603931S) values. This non-physical result arises from observed line ratios that are lower or comparable to the intrinsic value of $2.86-2.87$(cite: 2006agna.book.....O).

The Balmer line ratio can be affected by various issues, including low spectral resolution, poor line fits, assumptions on empirical relations (e.g., H$\alpha$/NII line ratio), and physical conditions (e.g., temperature and gas density)(cite: 2023MNRAS.518..425C; 2023ApJ...952..167R) at high-$z$ that differ from the standard ones(cite: 2006agna.book.....O). Therefore, for consistency and reliability, we have used $A_V$ estimates obtained from SED fitting.

## Comparison with the literature

In Fig. [3](#z_S) we report the literature findings for the slope $S$ and the bump $B$. The MW(cite: 1989ApJ...345..245C) and the SMC(cite: 2003ApJ...594..279G) are indicated by blue dotted lines. Other local individual sources: M31(cite: 2017A&A...599A..64V), M33(cite: 2019MNRAS.487.2753W), M51(cite: 2014A&A...571A..69D), and M74(cite: 2019MNRAS.486..743D) are depicted as blue $\times$ symbols. The median/mean values of samples of nearby ($z \sim 0$) and intermediate-$z$ ($z \sim 1-4$) galaxies from various studies(cite: 2000ApJ...533..682C; 2005MNRAS.360.1413B; 2010ApJ...718..184C; 2011MNRAS.417.1760W; 2011A&A...533A..93B; 2012A&A...545A.141B; 2013ApJ...775L..16K; 2015ApJ...806..259R; 2015ApJ...800..108S; 2016ApJ...818...13B; 2019PhDT.......129D; 2020ApJ...899..117S) are represented by green $\times$ symbols. Slopes for subsamples of low and intermediate-$z$ galaxies are shown as magenta(cite: 2018ApJ...859...11S) and cyan(cite: 2018MNRAS.475.2363T) $\times$ symbols, respectively. Finally, individual high-$z$ ($z \sim 4-8$) sources are indicated by violet(cite: 2022A&A...663A..50B), olive(cite: 2023Natur.621..267W) and orange $\times$ symbols(cite: 2023A&A...679A..12M).

Literature results for all the local sources and most nearby(cite: 2000ApJ...533..682C; 2005MNRAS.360.1413B; 2010ApJ...718..184C; 2011MNRAS.417.1760W; 2016ApJ...818...13B) and intermediate-$z$(cite: 2009A&A...499...69N; 2011A&A...533A..93B; 2012A&A...545A.141B; 2013ApJ...775L..16K; 2015ApJ...806..259R; 2015ApJ...800..108S) galaxy samples are directly adopted from the work of Salim & Narayanan (2020)(cite: 2020ARA&A..58..529S). Specific literature values of $S$ and $B$ are recalculated from their original parametrizations using the relations provided by Salim & Narayanan (2020)(cite: 2020ARA&A..58..529S). For instance, certain studies(cite: 2018ApJ...859...11S) utilize the Charot & Fall (2000) parametrization(cite: 2000ApJ...539..718C), $A_{\lambda}/A_V  = (\lambda/0.55 \mu m)^{-n}$, where the power law exponent $n$ characterizes the UV-optical slope. In such cases, we make use of the relation $\log{S} = n/1.772$ to convert to the $S$ parameter. In works that use the Noll et al. (2009) parametrization(cite: 2009A&A...499...69N; 2019PhDT.......129D), and the $\delta$ parameter to parametrize the slope, we use the relation $\log{S} = 0.4 - 0.55\delta$. Tress et al. (2018)(cite: 2018MNRAS.475.2363T) use the Conroy et al. (2010) parametrization(cite: 2010ApJ...718..184C) and they provide a relation to convert to the Noll et al. (2009) parametrization(cite: 2009A&A...507.1793N). Finally, the remaining literature results(cite: 2019PhDT.......129D; 2020ApJ...899..117S; 2023Natur.621..267W; 2023A&A...679A..12M) are directly provided by the authors.

To date, the detection of the characteristic 2175 Å feature has been reported in two galaxies at $z\sim 7$(cite: 2023Natur.621..267W; 2023A&A...679A..12M), both of which are also a part of the DAWN sample.

Witstok et al. (2023)(cite: 2023Natur.621..267W) reported a UV bump detection (with a $6.4\sigma$) in the JADES-GS-z6-0 galaxy, achieved by fitting an excess attenuation centred at 2236 Å with a Drude profile. However, applying our method (but setting the central wavelength of the bump to 2236 Å, in order to match the peak wavelength of the UV bump reported in their study) to the full spectrum of JADES-GS-z6-0 from JADES resulted in a marginal detection, with a UV bump strength of $B = 0.134 \pm 0.067$ or $c_4 = 0.020_{-0.011}^{+0.012}$ ($\sim 2\sigma$). However, our model assumes a UV bump width that is $\sim$ twice as large as the value used in Witstok et al. (2023). Differences in the assumed bump width between the two studies could explain the variation in results.

Next, in our recent study(cite: 2023A&A...679A..12M), we reported a hint of a UV bump detection in one out of three high-$z$ sources, s00717 at $z \sim 6.9$, with a UV bump strength of $c_4 = 0.033_{-0.012}^{+0.013}$ ($\sim 2.7\sigma$). Employing the identical SED fitting method with the same set of priors(cite: 2023A&A...679A..12M) on the DAWN observations of the s00717 source yields $c_4 = 0.019_{-0.017}^{+0.031}$.

Inconsistencies in these results may arise from the use of various fitting procedures involving different models (for JADES-GS-z6-0) as well as different data reduction pipelines generating slightly different final 1D spectra (for s00717). For s00717, the data reduction in our previous work was performed with the standard pipeline(cite: 2022A&A...661A..80J), whereas the data in this work are reduced with the `MSAEXP` custom code(cite: Brammer_msaexp_NIRSpec_analyis_2022). The different pipeline versions have different sampling, resulting in slightly different flux densities, uncertainties, and channel widths, which can create inconsistencies. When investigating the redshift evolution of galaxy properties, it is thus recommended to adopt samples of galaxies for which the data reduction analysis is performed with the same pipeline, as in the case of our study.

## Observational and model uncertainties

Factors that could contribute to the discrepancy in slopes between our study and the ones from the literature at $z \sim 2$ can arise both from observational uncertainties and model dependencies. Regarding the observational uncertainties, at the low redshift limit of our sample ($z \sim 2-2.8$), NIRSpec prism observations ($\lambda \sim 0.6-5.3 \ \mu m$) are restricted to the rest-frame $\lambda  \gtrsim 1600-2000$ Å, which probe the UV bump peak and marginally extend into the far-UV rise of the attenuation curve. This constraint in wavelength coverage may contribute to larger uncertainties in inferred slopes (Fig. [2](#all_curves_bin)). Moreover, for $z \sim 2-2.8$ sources, NIRSpec data are probing the attenuation curve with a fraction of the spectra at shorter wavelengths, which suffer from larger uncertainties, due to the lower resolution ($R \sim \lambda/\Delta \lambda \sim 50$) of the NIRSpec prism disperser in the wavelength range of $\lambda_{\rm{obs}} \sim 0.5-2 \ \mu m$. Finally, the observed discrepancy may be attributed to the lower number of sources per bin at intermediate redshifts (13-21 sources) compared to the higher redshift bins (20-66 objects).

Regarding the model dependencies, different SED fitting codes with different sets of model prescriptions (SFHs(cite: 2023A&A...679A..12M; 2023MNRAS.519.5859W; 2023MNRAS.522.6236T), dust attenuation, SPS and initial mass function (IMF)(cite: 2022MNRAS.510.5603K; 2024ApJ...963...74W)) and imposed priors on parameters(cite: 2012A&A...545A.141B; 2018MNRAS.475.2363T) can have a significant impact on the output parameters, including the recovered attenuation curve. We conducted extensive testing of our customized SED fitting tool with seven different SFH models(cite: 2023A&A...679A..12M). Our analysis revealed that while the choice of SFH model can influence properties closely linked to the SFH itself (e.g., $M*$, SFR, and ${\langle a \rangle}_*^{\rm{m}}$), the constrained dust attenuation properties remain largely unaffected by the assumed SFH. This finding underscores the robustness of our results concerning dust attenuation, irrespective of the specific SFH model employed.

# Data availability

The data that support the findings of this study are available at <https://dawn-cph.github.io/dja/index.html>.

# Code availability

`GRIZLI` (Grism redshift and line analysis software for space-based slitless spectroscopy(cite: brammer_2023_8370018)) and `MSAEXP` (Tool for extracting JWST NIRSpec) Micro-Shutter Assembly (MSA) spectra(cite: Brammer_msaexp_NIRSpec_analyis_2022), and `BAGPIPES` (Bayesian Analysis of Galaxies for Physical Inference and Parameter EStimation)(cite: 2018MNRAS.480.4379C) Python scripts are publicly available at <https://github.com/gbrammer/grizli>, <https://github.com/gbrammer/msaexp>, and <https://github.com/ACCarnall/bagpipes>, respectively.

# Acknowledgements

We would like to express our gratitude to H. Hirashita and I. Shivaei for engaging in productive discussions with us and providing valuable insights and comments. Additionally, we thank M. Decleir, I. Shivaei, and J. Witstok for sharing their findings on the properties of the attenuation curve.

VM, AF, AP, and MK acknowledge support from the ERC Advanced Grant INTERSTELLAR H2020/740120. VM acknowledges support from the ERC Grant FIRSTLIGHT and from the Slovenian National Research agency ARRS through grants N1-0238, P1-0188. Partial support (AF) from the Carl Friedrich von Siemens-Forschungspreis der Alexander von Humboldt-Stiftung Research Award is kindly acknowledged. Any dissemination of results must indicate that it reflects only the author’s view and that the Commission is not responsible for any use that may be made of the information it contains.

The data products presented herein were retrieved from the Dawn JWST Archive (DJA). DJA is an initiative of the Cosmic Dawn Center, which is funded by the Danish National Research Foundation under grant No. 140.

We gratefully acknowledge the computational resources of the Center for High Performance Computing (CHPC) at SNS.

# Author contributions

VM, SG, and AF led the writing of this paper. EP, VM, MK, and SG contributed to the target selection. VM, EP, and SG contributed to the visual inspection and additional data reduction. SG, VM, and AP contributed to the sample cleaning. VM led the SED fitting of the selected targets. SG, VM, AF, AP, LS, and FDM contributed to the development of the customized SED fitting tool. VM, SG, LS, AP, AF, and MK contributed to the visualisation of the results. VM, SG, AP, MK, AF, EP, and FDM contributed to the analysis of the results. VM, AF, SG, and AP contributed to the discussion on the physical interpretation of the results. All authors reviewed the manuscript.

# Competing interests

The authors declare no competing interests.

![](z2_curves_continuity_SFR.pdf)

![](z2_curves_continuity_SFR_bins.pdf)

![image](z_S.pdf) ![image](z_B.pdf)

100 url urlprefix doiprefix

(ref: 2013seg..book..419C) Calzetti, D. . In Falcón-Barroso, J. & Knapen, J. H. (eds.) *Secular Evolution of Galaxies*, 419, DOI: `10.48550/arXiv.1208.2997` (ArXiv, 2013).

(ref: 2020ARA&A..58..529S) Salim, S. & Narayanan, D. . **58**, 529–575 (2020).

(ref: 1977ApJ...217..425M) Mathis, J. S., Rumpl, W. & Nordsieck, K. H. **217**, 425–433 (1977).

(ref: 1984ApJ...285...89D) Draine, B. T. & Lee, H. M. . **285**, 89 (1984).

(ref: 2001ApJ...548..296W) Weingartner, J. C. & Draine, B. T. . **548**, 296–309 (2001).

(ref: 1965ApJ...142.1683S) Stecher, T. P. **142**, 1683 (1965).

(ref: 1990A&A...237..215D) Desert, F. X., Boulanger, F. & Puget, J. L. . **237**, 215 (1990).

(ref: 1992A&A...259..614S) Siebenmorgen, R. & Kruegel, E. **259**, 614–626 (1992).

(ref: 2013MNRAS.432.2061C) Chevallard, J., Charlot, S., Wandelt, B. & Wild, V. . **432**, 2061–2091 (2013).

(ref: 2020ApJ...888..108B) Battisti, A. J., Cunha, E. d., Shivaei, I. & Calzetti, D. . **888**, 108 (2020).

(ref: 2018ApJ...869...70N) Narayanan, D., Conroy, C., Davé, R., Johnson, B. D. & Popping, G. . **869**, 70 (2018).

(ref: 2020MNRAS.491.3937T) Trayford, J. W., Lagos, C. d. P., Robotham, A. S. G. & Obreschkow, D. . **491**, 3937–3951 (2020).

(ref: 1999ApJS..123..437F) Ferrara, A., Bianchi, S., Cimatti, A. & Giovanardi, C. . **123**, 437–445 (1999).

(ref: 2022A&A...663A..50B) Boquien, M. *et al.* . **663**, A50 (2022).

(ref: 2023A&A...679A..12M) Markov, V. *et al.* . **679**, A12 (2023).

(ref: 2023Natur.621..267W) Witstok, J. *et al.* . **621**, 267–270 (2023).

(ref: 2010A&A...523A..85G) Gallerani, S. *et al.* . **523**, A85 (2010).

(ref: 2021MNRAS.506.3946D) Di Mascia, F. *et al.* . **506**, 3946–3961 (2021).

(ref: 2011A&A...532A..45S) Stratta, G., Gallerani, S. & Maiolino, R. **532**, A45 (2011).

(ref: 2018A&A...609A..62B) Bolmer, J. *et al.* . **609**, A62 (2018).

(ref: 2000ApJ...533..682C) Calzetti, D. *et al.* . **533**, 682–695 (2000).

(ref: 2003ApJ...594..279G) Gordon, K. D., Clayton, G. C., Misselt, K. A., Landolt, A. U. & Wolff, M. J. . **594**, 279–293 (2003).

(ref: 1989ApJ...345..245C) Cardelli, J. A., Clayton, G. C. & Mathis, J. S. . **345**, 245 (1989).

(ref: 2017ApJ...851..152B) Boyer, M. L. *et al.* . **851**, 152 (2017).

(ref: 2020A&A...637A..32B) Burgarella, D. *et al.* . **637**, A32 (2020).

(ref: 1978ppim.book.....S) Spitzer, L. *Physical processes in the interstellar medium* (John Wiley & Sons, Ltd, 1978).

(ref: 1980ApJ...239..193D) Dwek, E. & Scalo, J. M. . **239**, 193–211 (1980).

(ref: 2019MNRAS.489....1F) Ferrara, A. *et al.* . **489**, 1–12 (2019).

(ref: 2019MNRAS.487.1689P) Pallottini, A. *et al.* . **487**, 1689–1708 (2019).

(ref: 2022MNRAS.513.5621P) Pallottini, A. *et al.* . **513**, 5621–5641 (2022).

(ref: 2020MNRAS.495L..22V) Vallini, L., Ferrara, A., Pallottini, A., Carniani, S. & Gallerani, S. . **495**, L22–L26 (2020).

(ref: 2022A&A...663A.172M) Markov, V. *et al.* . **663**, A172 (2022).

(ref: 2009ApJ...706.1364F) Förster Schreiber, N. M. *et al.* . **706**, 1364–1428 (2009).

(ref: 2022MNRAS.516.3532M) Meštrić, U. *et al.* . **516**, 3532–3555 (2022).

(ref: 2023MNRAS.522.3986F) Ferrara, A., Pallottini, A. & Dayal, P. . **522**, 3986–3991 (2023).

(ref: 2023A&A...677L...4P) Pallottini, A. & Ferrara, A. . **677**, L4 (2023).

(ref: 2018MNRAS.477..552B) Behrens, C., Pallottini, A., Ferrara, A., Gallerani, S. & Vallini, L. . **477**, 552–565 (2018).

(ref: 2018MNRAS.478.1170C) Carniani, S. *et al.* . **478**, 1170–1184 (2018).

(ref: 2020A&A...641A..22M) Markov, V. *et al.* . **641**, A22 (2020).

(ref: 2022MNRAS.517.5930S) Sommovigo, L. *et al.* . **517**, 5930–5941 (2022).

(ref: 2018MNRAS.480.4379C) Carnall, A. C., McLure, R. J., Dunlop, J. S. & Davé, R. . **480**, 4379–4401 (2018).

(ref: 2011A&A...533A..93B) Buat, V. *et al.* . **533**, A93 (2011).

(ref: 2012A&A...545A.141B) Buat, V. *et al.* . **545**, A141 (2012).

(ref: 2013ApJ...775L..16K) Kriek, M. & Conroy, C. . **775**, L16 (2013).

(ref: 2015ApJ...800..108S) Scoville, N. *et al.* . **800**, 108 (2015).

(ref: 2015ApJ...806..259R) Reddy, N. A. *et al.* . **806**, 259 (2015).

(ref: 2018MNRAS.475.2363T) Tress, M. *et al.* . **475**, 2363–2374 (2018).

(ref: 2020ApJ...899..117S) Shivaei, I. *et al.* . **899**, 117 (2020).

(ref: 2008ApJ...685.1046L) Li, A. *et al.* . **685**, 1046–1051 (2008).

(ref: 2009A&A...499...69N) Noll, S. *et al.* . **499**, 69–85 (2009).

(ref: 2013ARA&A..51..393C) Conroy, C. . **51**, 393–455 (2013).

(ref: 2016ApJ...827...20S) Salmon, B. *et al.* . **827**, 20 (2016).

(ref: 2023MNRAS.519.2475H) Hsu, Y.-M., Hirashita, H., Lin, Y.-H., Camps, P. & Baes, M. . **519**, 2475–2485 (2023).

(ref: 2000ApJ...539..718C) Charlot, S. & Fall, S. M. . **539**, 718–731 (2000).

(ref: 2019MNRAS.489.2792Z) Zanella, A. *et al.* . **489**, 2792–2818 (2019).

(ref: Fujimoto24) Fujimoto, S. *et al.* . arXiv:2402.18543 (2024).

(ref: Adamo24) Adamo, A. *et al.* . arXiv:2401.03224 (2024).

(ref: 2018MNRAS.478.2851M) McKinnon, R., Vogelsberger, M., Torrey, P., Marinacci, F. & Kannan, R. . **478**, 2851–2886 (2018).

(ref: 2020MNRAS.492.3779H) Hirashita, H. & Murga, M. S. . **492**, 3779–3793 (2020).

(ref: 2022MNRAS.517.2076M) Makiya, R. & Hirashita, H. . **517**, 2076–2087 (2022).

(ref: 2001MNRAS.325..726T) Todini, P. & Ferrara, A. . **325**, 726–736 (2001).

(ref: 2007ApJ...666..955N) Nozawa, T. *et al.* **666**, 955–966 (2007).

(ref: 2014Natur.511..326G) Gall, C. *et al.* . **511**, 326–329 (2014).

(ref: 2013EP&S...65..213A) Asano, R. S., Takeuchi, T. T., Hirashita, H. & Inoue, A. K. . **65**, 213–222 (2013).

(ref: 2013MNRAS.432..637A) Asano, R. S., Takeuchi, T. T., Hirashita, H. & Nozawa, T. **432**, 637–652 (2013).

(ref: 2020ApJ...892..149T) Tazaki, R. & Ichikawa, K. . **892**, 149 (2020).

(ref: 2020ApJ...892...84T) Tazaki, R., Ichikawa, K. & Kokubo, M. . **892**, 84 (2020).

(ref: 2018ApJ...868...62G) Gall, C. & Hjorth, J. . **868**, 62 (2018).

(ref: 1997A&A...326..305W) Winters, J. M., Fleischer, A. J., Le Bertre, T. & Sedlmayr, E. **326**, 305–317 (1997).

(ref: 2006A&A...447..553F) Ferrarotti, A. S. & Gail, H. P. . **447**, 553–576 (2006).

(ref: 2019A&A...624L..13L) Leśniewska, A. & Michałowski, M. J. . **624**, L13 (2019).

(ref: 2024arXiv240218515D) Dubois, Y. *et al.* . arXiv:2402.18515 (2024).

(ref: 2004Natur.431..533M) Maiolino, R. *et al.* . **431**, 533–535 (2004).

(ref: DAWN) Brammer, G. Dawn jwst archive. `https://dawn-cph.github.io/dja/index.html` (2023).

(ref: Brammer_msaexp_NIRSpec_analyis_2022) Brammer, G. , DOI: `10.5281/zenodo.7299500` (2022).

(ref: JWST-docs) Jwst user documentation. `https://jwst-docs.stsci.edu/jwst-near-infrared-spectrograph/nirspec-operations/nirspec-mos-operations/nirspec-mos-operations-slit-losses` (2017).

(ref: 2016SPIE.9910E..1OB) Beck, T. L. *et al.* . In Peck, A. B., Seaman, R. L. & Benn, C. R. (eds.) *Observatory Operations: Strategies, Processes, and Systems VI*, vol. 9910 of *Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series*, 99101O, DOI: `10.1117/12.2232804` (2016).

(ref: 2018A&A...620A.152F) Franco, M. *et al.* . **620**, A152 (2018).

(ref: 2017MNRAS.466..861D) Dunlop, J. S. *et al.* . **466**, 861–883 (2017).

(ref: 2018PASJ...70..105H) Hatsukade, B. *et al.* . **70**, 105 (2018).

(ref: 2022A&A...658A..43G) Gómez-Guijarro, C. *et al.* . **658**, A43 (2022).

(ref: 2023arXiv230907834F) Fujimoto, S. *et al.* . arXiv:2309.07834 (2023).

(ref: 2022ApJ...932...77S) Sun, F. *et al.* . **932**, 77 (2022).

(ref: 10.1093/mnras/stw1756) Chevallard, J. & Charlot, S. . **462**, 1415–1443 (2016).

(ref: 2017RMxAA..53..385F) Ferland, G. J. *et al.* . **53**, 385–438 (2017).

(ref: 2014MNRAS.442.1805I) Inoue, A. K., Shimizu, I., Iwata, I. & Tanaka, M. . **442**, 1805–1820 (2014).

(ref: 2019ApJ...876....3L) Leja, J., Carnall, A. C., Johnson, B. D., Conroy, C. & Speagle, J. S. . **876**, 3 (2019).

(ref: 2022MNRAS.516..975T) Topping, M. W. *et al.* . **516**, 975–991 (2022).

(ref: 2018ApJ...859...11S) Salim, S., Boquien, M. & Lee, J. C. . **859**, 11 (2018).

(ref: 1989IAUS..135..313D) Draine, B. . In Allamandola, L. J. & Tielens, A. G. G. M. (eds.) *Interstellar Dust*, vol. 135, 313 (1989).

(ref: 2022MNRAS.514.1886S) Shivaei, I. *et al.* . **514**, 1886–1894 (2022).

(ref: 2019OJAp....2E..10F) Feroz, F., Hobson, M. P., Cameron, E. & Pettitt, A. N. . **2**, 10 (2019).

(ref: 2016A&A...588A..19L) Lucy, L. B. . **588**, A19 (2016).

(ref: 2023ApJ...949L..11M) Matharu, J. *et al.* . **949**, L11 (2023).

(ref: 2023arXiv230603931S) Sandles, L. *et al.* . arXiv:2306.03931 (2023).

(ref: 2006agna.book.....O) Osterbrock, D. E. & Ferland, G. J. *Astrophysics of gaseous nebulae and active galactic nuclei* (University Science Books, 2006, 2006).

(ref: 2023MNRAS.518..425C) Curti, M. *et al.* . **518**, 425–438 (2023).

(ref: 2023ApJ...952..167R) Reddy, N. A., Topping, M. W., Sanders, R. L., Shapley, A. E. & Brammer, G. . **952**, 167 (2023).

(ref: 2017A&A...599A..64V) Viaene, S. *et al.* . **599**, A64 (2017).

(ref: 2019MNRAS.487.2753W) Williams, T. G. *et al.* . **487**, 2753–2770 (2019).

(ref: 2014A&A...571A..69D) De Looze, I. *et al.* . **571**, A69 (2014).

(ref: 2019MNRAS.486..743D) Decleir, M. *et al.* . **486**, 743–767 (2019).

(ref: 2005MNRAS.360.1413B) Burgarella, D., Buat, V. & Iglesias-Páramo, J. . **360**, 1413–1425 (2005).

(ref: 2010ApJ...718..184C) Conroy, C., Schiminovich, D. & Blanton, M. R. . **718**, 184–198 (2010).

(ref: 2011MNRAS.417.1760W) Wild, V. *et al.* . **417**, 1760–1786 (2011).

(ref: 2016ApJ...818...13B) Battisti, A. J., Calzetti, D. & Chary, R. R. . **818**, 13 (2016).

(ref: 2019PhDT.......129D) Decleir, M. *DustKING - Revealing the dust attenuation in nearby galaxies*. Ph.D. thesis, Ghent University, Belgium (2019).

(ref: 2009A&A...507.1793N) Noll, S. *et al.* . **507**, 1793–1813 (2009).

(ref: 2022A&A...661A..80J) Jakobsen, P. *et al.* . **661**, A80 (2022).

(ref: 2023MNRAS.519.5859W) Whitler, L. *et al.* . **519**, 5859–5881 (2023).

(ref: 2023MNRAS.522.6236T) Tacchella, S. *et al.* . **522**, 6236–6249 (2023).

(ref: 2022MNRAS.510.5603K) Katz, H. *et al.* **510**, 5603–5622 (2022).

(ref: 2024ApJ...963...74W) Wang, B. *et al.* . **963**, 74 (2024).

# Extended data

![image](z_S_Av.pdf) ![image](z_B_Av.pdf)

![image](z_S_logM.pdf) ![image](z_B_logM.pdf)

![image](z_S_age.pdf) ![image](z_B_age.pdf)

![image](z_S_SFR.pdf) ![image](z_B_SFR.pdf)

![image](z_S_Z.pdf) ![image](z_B_Z.pdf)

![image](z_S_logU.pdf) ![image](z_B_logU.pdf)

![](z_c4.pdf)

![image](1433_3989_spectrum_full.pdf) ![image](1433_3989_curves_continuity_SFR.pdf) ![image](2750_449_spectrum_full.pdf) ![image](2750_449_curves_continuity_SFR.pdf)

[^1]: This is the accepted manuscript version of the article published in *Nature Astronomy*: Markov, V. et al. (2024), Nat. Astron. <https://doi.org/10.1038/s41550-024-02426-1>. The final version is available at: [nature.com/articles/s41550-024-02426-1](https://www.nature.com/articles/s41550-024-02426-1)

</paper>

Write the methods card for this paper.