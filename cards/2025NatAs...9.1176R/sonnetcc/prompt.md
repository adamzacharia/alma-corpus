# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9.1176R\sonnetcc\reply.txt

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
 "bibcode": "2025NatAs...9.1176R",
 "title": "A young gas giant and hidden substructures in a protoplanetary disk",
 "year": 2025,
 "journal": "Nature Astronomy",
 "first_author": "Ribas, Álvaro",
 "n_authors": 10,
 "arxiv_id": "2507.11612",
 "doi": "10.1038/s41550-025-02576-w",
 "alma_projects_linked_by_archive": [
  "2017.1.01167.S",
  "2017.1.01419.S",
  "2022.1.01758.S"
 ]
}
```

Paper text:
<paper>
# A young gas giant and hidden substructures in a protoplanetary disk

\[1\], ,

2\],

3\],

4\],

5\],

6\],

7\],

8\],

9\],

# Main

Despite extensive efforts to find protoplanets in protoplanetary disks, they have only been robustly detected in two systems so far (cite: Keppler_2018; Haffert_2019; Barber_2024). Accessing the population of young planets would be truly valuable for planet formation studies as this would provide direct benchmarks to our models, but common detection methods such as transits, radial velocity, or direct imaging are extremely challenging or simply unfeasible for embedded companions due to the high dust extinction in the disk and the increased stellar activity of young stars (cite: Testi_2015; Donati_2020). Instead, the presence of planets in disks is typically inferred by planet-disk interaction footprints such as disk substructures and velocity perturbations. In fact, arguably the most significant discovery of the last decade for the field of planet formation is the ubiquity of substructures in protoplanetary disks. Rings, gaps, spiral arms, or azimuthal asymmetries are found in virtually every large disk observed with sufficient angular resolution (cite: Andrews_2018; Long_2018; Bae_2023).

Disk substructures offer a natural solution to the problem of dust radial drift: the interaction of mm/cm-sized grains with the gas in the disk causes large grains to drift towards the central star. This process is much faster than typical timescales for planet formation and can quickly deplete the population of large grains in disks, presenting a theoretical barrier to build rocky planets and the cores of gas giants (cite: Weidenschilling_1977; Brauer_2007). Local gas pressure maxima (induced by planets or other processes) have been proposed as a mechanism to trap large grains and allow them to grow to larger sizes (cite: Paardekooper_2004; Lyra_2009; Pinilla_2012), but this solution remained hypothetical until the high resolution and sensitivity of observatories such as the Atacama Large Millimeter/Submillimeter Array (ALMA) and the Spectro-Polarimetric High-contrast Exoplanet REsearch instrument (SPHERE) uncovered the plethora of disk substructures (cite: Andrews_2018; Garufi_2024; Ginski_2024).

As of today, MP Mus is the only large Class II protoplanetary disk that appears structureless when observed at millimetre wavelengths with high spatial resolution (cite: Ribas_2023). This K1V star is located 97.9$\pm$0.1 pc away from Earth (cite: Gaia_2021b) and has an estimated age of 7-10 Myr (cite: Ribas_2023). Its dust disk extends up to $R_{\rm dust, 90\%}$=45 au at 1.3 mm (i.e., the radius encompassing 90% of the 1.3 mm continuum emission), while the gaseous disk traced by the $^{12}$CO(J=2-1) reaches $R_{\rm CO~90\%}$=110 au. This ratio of gas/dust radii is similar to that of structured disks, in which dust traps are likely acting (cite: Toci_2021). However, the disk appears structureless at 1.3 mm down to 4 au scales except for a tentative narrow dust ring in the outer regions (cite: Ribas_2023), recently confirmed by (cite: Aguayo_2025) in high-resolution ALMA 0.89 mm observations. In contrast, scattered light observations of this system show an apparent gap between 40 and 80 au (cite: Wolff_2016; Avenhaus_2018). Nevertheless, the fact that the millimetre disk extends up to $\sim$55 au, the clearly Keplerian rotation of the disk as traced by ALMA, and its flat appearance, strongly suggest that the drop in scattered light intensity between 40 and 80 au is due to a shadowing effect and not an actual gap in the disk (cite: Ribas_2023). The smooth 1.3 mm radial profile is yet more puzzling when we compare the characteristic lifetime of disks (cite: Haisch_2001; Fedele_2010; Ribas_2015) with the age of MP Mus. To explain the survival of large dust grains in such an old and seemingly structureless disk, (cite: Ribas_2023) proposed a number of possible solutions: 1) substructures may be present in the disk but the 1.3 mm continuum is optically thick, effectively hiding them, 2) substructures smaller than 4 au exist and remain unresolved with current observations, or 3) the disk is really featureless and a different (unknown) mechanism is retaining mm-emitting grains in it. None of these scenarios could be tested with the existing observations at the time, and MP Mus remained an outlier among disks.

## The *Gaia* proper motion anomaly of MP Mus

The 1.3 mm continuum emission of MP Mus shows no obvious signs of planets in the system but, in contrast, its astrometry deviates from a single star solution. By measuring the proper motion vector of the photocenter at different times, we can identify changes (proper motion anomalies, PMas) that signal the presence of companions (cite: Perryman_2014; Kervella_2019; Kervella_2022). PMas have already been used to identify exoplanets around main sequence stars (cite: deRosa2023; Mesa_2023; Currie_2023; Kiefer_2024), but this method has not been applied to sources with protoplanetary disks yet. Compared to main sequence stars, protostars exhibit additional phenomena (e.g., variability, strong disk asymmetries, differential extinction, stellar obscuration by accretion columns) that could potentially induce a PMa. However, the analysis of well-known protoplanetary disks shows that only edge-on, highly asymmetric, or massive disks can induce proper motion anomalies (Vioque et al. in prep), and MP Mus has a very low accretion rate (cite: Ingleby_2023). Therefore, none of these potential issues apply to the MP Mus system (cite: Ribas_2023).

We determined the PMa of MP Mus by comparing the proper motion vectors of *Gaia* DR2 and *Gaia* DR3 (cite: Penoyre_2022a; Penoyre_2022b). The resulting PMa has a significance of 4.5 $\sigma$ and implies a change in the proper motion of $|\Delta \mu|=0.21\pm0.05$ mas yr$~^{-1}$. We used the scanning law of *Gaia* DR2 \[(cite: Boubert_2021)\] and *Gaia* DR3 [^1] to retrieve the epochs and scan angles in which *Gaia* observed this source. We then used these epochs and angles, together with realistic *Gaia* uncertainties, to simulate the *Gaia* DR2 and DR3 observations of MP Mus assuming a two body system with different mass ratios and periods (cite: Penoyre_2022a). We assumed no eccentricity and a relation between the mass ($q=M_{\rm{comp}}/M_{\rm{primary}}$) and light ($l=L_{\rm{comp}}/L_{\rm{primary}}$) ratio of the components of $l = q^{3.5}$, a heuristic commonly used for main-sequence stars. We ran $500\,000$ simulations randomly sampling the log-uniform space of mass ratios (from 0.0001 to 1) and periods (from 0.016 to 1585 yr). The mass of the primary source, the viewing angles, and the orbital phase were sampled at random every time following the measured values and uncertainties of stellar mass ($1.30\pm0.08~M_\odot$), inclination ($32\pm1^{\circ}$), and position angle ($10\pm1^{\circ}$, disk geometries from (cite: Ribas_2023)). We then selected only those simulations which resulted in astrometric properties compatible with what is observed in MP Mus ($0.26>|\Delta \mu|>0.16$ mas yr$~^{-1}$, $|\Delta \mu|/\sigma_{|\Delta \mu|}>4$). In addition, MP Mus has a re-normalized unit weight error (RUWE) very close to 1 in both *Gaia* DR2 and DR3 (of 0.98 and 0.96, respectively). We hence imposed a conservative threshold to the simulations of $\rm{UWE_{DR3}}<1.1$ (cite: Penoyre_2022a).

![](figures/PMa_combined_fig1.pdf)

Figure [1](#fig:PMa) shows the orbital separations and masses for a companion to induce the observed PMa and RUWE. We note that we only model a two-body interaction, and the interpretation of the PMa becomes more complex for multi-body systems. In this work we assume that, although there may be other planets in MP Mus, its PMa is dominated by a single companion. From the *Gaia* data, we conclude that the PMa of MP Mus is most likely due to a companion at orbital separations $<$30 au, with the required mass increasing with orbital distance (Fig. [1](#fig:PMa)). The non-detection of astrometric noise (i.e., RUWE$\approx$1) also rules out massive bodies with short periods (i.e., $a<1$ au). The strong statistical significance of the *Gaia* PMa detection makes for a good companion candidate in MP Mus, but a second, independent signature is needed to further constrain its location and mass.

## Hidden substructures at 3 mm

To better understand MP Mus we obtained new ALMA observations at 3 mm and with a spatial resolution (4 au) similar to that of the 1.3 mm data presented by (cite: Ribas_2023) (see Methods for details about the observations and data processing). Longer wavelengths offer two main advantages to search for substructures in disks. First, the dust opacity (and therefore the optical depth) decreases with wavelength, and the observations probe emission closer to the disk midplane where planets are expected to form. This is most important in the disk inner regions where the emission is likely to be optically thick, as indicated by the low ($\alpha<2$) local millimetre spectral index of MP Mus between 1.3 and 2.2 mm (cite: Ribas_2023). A second benefit of observations at longer wavelengths is that they trace larger grains, which experience a stronger gas drag and are more strongly trapped in pressure maxima. Therefore, if present, substructures may show an enhanced contrast at longer wavelengths (cite: Pinilla_2015).

![](figures/B3_and_B6_fig2.pdf)

The ALMA 3 mm observations are shown in Fig. [2](#fig:ALMA) alongside with previous 1.3 mm data. The disk appears smooth at 1.3 mm (cite: Ribas_2023), but the new 3 mm data reveal a ring at 10.5 au and two gaps at 7.5 and 15 au that are undetected at shorter wavelengths. The 3 mm image also has flatter central emission, with hints of two peaks suggesting the presence of a barely resolved cavity (this is better seen in Supplementary Fig. 1). To better characterise the structure of the system, we calculated and compared the intensity radial profiles of the disk at both wavelengths. We do this in visibility space with the code FRANK (cite: frank), which achieves higher angular resolution and recovers smaller structures than working with synthesised images. The profiles are shown in Fig. [3](#fig:rad_profiles) and more clearly reveal the aforementioned structures in the 3 mm image: an inner cavity with a radius of $\sim$3 au, as well as a ring and two gaps. The FRANK residuals are provided in Supplementary Fig. 2. Although not as clear, radial profiles calculated directly from synthesised images also show these substructures (see Methods and Supplementary Fig. 3).

![](figures/rad_profiles_frank_fig3.pdf)

The 3 mm data prove that MP Mus is indeed structured, which could explain both the disk longevity and the similar ratio of gas/dust radii to other structured disks. A naive interpretation of the disk architecture, in which the inner cavity and two gaps are each being carved by a different planet, would imply that MP Mus hosts a multi-planetary system. Nevertheless, we caution that mechanisms other than planets can open cavities and gaps (cite: Zhang_2015; Flock_2015; Gonzalez_2017) and that such interpretation may be too simplistic. Moreover, simulations have shown that a single planet may carve multiple gaps in low viscosity discs (cite: Dong_2017; Bae_2017), although this is no longer the case for models including radiative effects (cite: Ziampras_2020).

We can, however, attempt to link the new-found structures to the *Gaia* PMa to search for possible explanations for both phenomena. First, previous observing campaigns to detect planets and substellar objects in MP Mus have ruled-out sources more massive than $2-3~M_{\rm Jup}$ at separations $>40-50$ au (cite: Wolff_2016; AsensioTorres_2021). If instead we assume that a putative companion in either of the gaps (i.e., at 7.5 au or at 15 au) is responsible for the PMa, it would require masses above $10~M_{\rm Jup}$ to account for the observed signal (Fig. [1](#fig:PMa)). Such a massive object would open much wider gaps and strongly alter the disk structure, in stark contrast with its narrow gaps and overall smooth appearance (cite: Bae_2023; Ruzza_2024). For these reasons, even if planets may be carving those gaps, they are unlikely to be the cause of the PMa. On the other hand, the inner $\sim$3 au cavity appears as an optimal location for possible companions. We can further restrict the location of the companion if we assume that it is responsible for carving the cavity: even in the most favourable scenario (i.e., an equal mass binary), a non-eccentric binary system can only open a cavity as large as 2-3 times the orbital separation (cite: Artymowicz_1994; Ragusa_2020). Put together, the *Gaia* and ALMA data strongly suggest that MP Mus harbours a giant protoplanet in the inner 1-3 au of the system.

## Confronting observations with simulations

To explore if a protoplanet within the mass range and orbital separations suggested by the *Gaia* PMa could explain the inner cavity seen at 3 mm, we ran hydrodynamical simulations of a star + planet system using the smoothed particle hydrodynamics (SPH) code PHANTOM (cite: Price_2018). We ran a grid of 25 models with different orbital radii and masses that would fit inside the 3 au cavity, namely at 0.5, 1, 1.5, 2, and 2.5 au (corresponding to orbital periods of 0.3, 0.9, 1.6, 2.5, and 3.5 years, respectively), and with companion masses of 3, 5, 7, 10, and 15 $M_{\rm Jup}$. Details on the modelling setup are provided in the Methods section. We then performed radiative transfer with the MCFOST code (cite: MCFOST; MCFOST2) to produce continuum images at 1.3 and 3 mm and convolved the results with the corresponding ALMA beams. Fig. [4](#fig:rad_profiles_sim) shows the radial profiles of the simulations at 1.3 and 3 mm for three representative cases as calculated directly from the images with the code GOFISH (cite: GoFish). The results for the full grid are provided in Section 2 of the Supplementary Material and in Supplementary Fig. 4.

![](figures/rad_profiles_phantom_examples_fig4.pdf)

The SPH simulations provide additional information about the properties of the companion. First, none of the models with an orbital separation of 0.5 au carve an inner cavity large enough to be discernible with the current spatial resolution, regardless of their mass. On the other extreme, planets at $\geq$2 au produce cavities that are too large to be compatible with the observations. The mass of the companion does not have a strong effect on the cavity size, but more massive objects result in deeper cavities. We also note that some simulations create a cavity of the right size at 3 mm while no cavity is visible at 1.3 mm, just as observed with ALMA (although this is more sensitive to the adopted disk and dust properties). Overall, the simulations show that the observed cavity can be successfully explained by a gas giant orbiting at 1-2 au, lending further indirect but independent support to the presence of such planet in MP Mus.

## Discussion

The combination of two independent but consistent pieces of evidence (the *Gaia* PMa and the finding of a small inner cavity) create a very compelling case for the existence of MP Mus b, a gas giant planet orbiting between $\sim$1-3 au. The case is strengthened even further when we consider the SPH simulations of the system, which show that planets between 1-2 au carve a cavity with the correct size, and in some cases even reproduce the peculiar feature of the inner cavity being visible at 3 mm but not at 1.3 mm. The presence of a companion in the inner regions of MP Mus would also account for its low accretion rate compared to other disks with similar masses (cite: Ingleby_2023). It is unlikely that such a planet would form at its current location: planet formation is thought to be more efficient at radii near and outside the snowline (the location at which water ice sublimates) due to the change in dust properties and enhanced dust-to-gas ratios (cite: Drkazkowska_2017), and the gas giants found with 1-2 au orbits are believed to have undergone planetary migration (cite: Alexander_2012). Interestingly, at 1-2 au, it is possible that MP Mus b resides in the habitable zone of its 1.3 $M_\odot$ star. Detecting such a planet with radial velocity would be a formidable challenge, as the expected signal of a $\sim$5 $M_{\rm Jup}$ between 1 and 3 au (i.e., a radial velocity semi-amplitude of 40-70 m s$^{-1}$) is below the typical level of stellar activity in young stars (cite: Zakhozhay_2022), and even detections of very massive protoplanets much closer to their host stars are very difficult to disentangle from other sources of radial velocity signal (cite: Johns-Krull_2016; Biddle_2018; Donati_2020; Donati_2024; Manick_2024). This highlights the unique potential of the PMa technique to uncover the population of young planets in close (a few au) orbits embedded in protoplanetary disks, a region of the parameter space that remains beyond the reach of other current detection methods. This becomes especially promising when combined with additional information about the possible presence of the protoplanet such as in the case of MP Mus, where the disk structure traced by ALMA allows to pinpoint the location of the companion; the narrow width of the two gaps rules them out as possible sites for the body inducing the PMa, leaving the inner cavity as the only suitable location.

In addition to the inner cavity revealed by the new 3 mm data, the different morphology of the disk at 1.3 and 3 mm can be solely attributed to the difference in wavelength (given that both observations have the same spatial resolution). As mentioned in Sec. [1.2](#sec:alma_3mm), this arises from a combination of the enhanced contrast of substructures (due to more efficient trapping of larger grains) and the lower optical depth with increasing wavelength. Previous studies have already shown that disk substructures often appear sharper and with a higher contrast at longer wavelengths (cite: CarrascoGonzalez_2019; Huang_2020; Doi_2023). MP Mus represents an extreme example of this as it is the first source in which new substructures are uncovered at longer wavelengths, but it is unlikely to be the only system in which this occurs. The new 3 mm observations also confirm that 1 mm emission from the inner regions of protoplanetary disk can remain optically thick and, more importantly, indicate that our current census of disk substructures (cite: Bae_2023) is potentially very incomplete. Protoplanetary disks may be more structured than currently believed, on the one hand providing even more dust trapping of large grains, and on the other hand clearly necessitating high-resolution, high-sensitivity surveys at longer wavelengths to understand the frequency and properties of a potential population of hidden substructures.

# Methods

## ALMA data processing and imaging

The MP Mus ALMA Band 3 (3 mm) data correspond to the ALMA project 2022.1.01758.S (P.I.: Á. Ribas) and were taken with two different configurations. The compact configuration was observed once on 21 May 2022 and contains baselines from 27 m to 3.6 km. The extended configuration was observed three times on 27-28 July 2022 with baselines ranging from 230 m to 16.2 km. The correlator was setup to maximise the continuum sensitivity, containing four spectral windows centred at 90.521, 92.416, 102.521, and 104.479 GHz, each with a bandwidth of 1.875 GHz and 128 channels. All the observations were first calibrated using the pipeline script and CASA V.6.4.1.12, and further processing was performed with CASA V.6.5.6.22. In particular, we first performed phase-only self-calibration on the extended and compact configurations separately. We then placed the phase centre on the disk for each observation, set the coordinates of each phase centre to a common value, and re-scaled the flux of the three extended executions to match the flux of the compact one. Finally, one additional round of phase-only self-calibration was applied after combining the four execution blocks.

The Band 6 data (1.3 mm) are part of ALMA project 2017.1.01167.S (P.I.: S. Pérez) and were already presented in (cite: Ribas_2023). In that work, (cite: Ribas_2023) combined these observations with those of ALMA project 2017.1.01419.S (P.I.: C. Cáceres), which had lower spatial resolution but were useful to study gas emission in the system. We chose not to include those data in this work since here we focus on the continuum only. The data consist of a compact configuration observed on 15 January 2018 with baselines between 15 m and 2.4 km, and an extended one taken on 16 November 2017 with baselines between 90 m and 8.2 km. The observations were calibrated with the pipeline and CASA V.5.1.1-5, and we then used CASA V.6.5.6.22 for the rest of the analysis. The correlator setup in this case contained four spectral windows, three for continuum centred at 232.483, 244.983, and 246.983 GHz (bandwidth of 1.875 GHz and 128 channels each), and the fourth one centred at 230.525 GHz targeting the $^{12}$CO (2-1) line (bandwidth of 1.875 GHz and 960 channels). We flagged channels containing CO emission and then performed self-calibration with a similar process as for the Band 3 data: we first self-calibrated the compact and extended configurations individually, placed the phase centre at the centre of the disk in each case and changed its coordinates to a common value, and then re-scaled the compact configuration to have the same flux as the extended one (in this case, the observatory calibrator appeared more stable around the time of the extended observations, although this has no impact on any of our results). We then ran one final round of phase-only self-calibration in which both the compact and extended configurations were combined.

We imaged the data using the `tclean` routine in CASA using different weighting to achieve the best compromise between spatial resolution and sensitivity. For the purpose of analysing the disk structures (Fig. [2](#fig:ALMA)) we used the `mtmfs` option with `nterms=1` and scales of 0, 1, 3, and 5 beams. We adopted a `robust` parameter of 0 for both wavelengths, resulting in a beam of 0.06"$\times$0.04" in both cases, and a position angle of $PA=-13^\circ$ at 1.3 mm and $-27^\circ$ at 3 mm. The corresponding image rms values are 37 $\mu$Jy beam$^{-1}$ and 7.7 $\mu$Jy beam$^{-1}$ at 1.3 and 3 mm, respectively. The peak S/N of these images is 105 at 1.3 mm and 90 at 3 mm. The disk flux, radius, and mass measured at 3 mm are provided in Section 1 of the Supplementary Material.

## Radial profiles and additional sanity checks

The radial profiles in Fig. [3](#fig:rad_profiles) were created using the FRANK code (cite: frank). Under the assumption that the the disk is axisymmetric, this software calculates the radial profile of the disk directly from the observed visibilities using a Hankel transform. For both the 1.3 and 3 mm data we first fit the geometry of the system with the non-parametric option and using the measured disk inclination and position angles as initial guesses (cite: Ribas_2023). The values of $i$ and $PA$ determined by FRANK are compatible with the 1$^\circ$ uncertainty of these quantities. We then explored the effect of changing the $\alpha$ and $w_{\rm smooth}$ hyper-parameters: the results were largely insensitive to the choice of these in the case of the 1.3 mm data, yielding a profile similar to the one presented in (cite: Ribas_2023) (unless extreme values of $\alpha$ and $w_{\rm smooth}$ were used, which induced artificial wiggles) and we adopted $\alpha$=1.2 and $w_{\rm smooth}=5\times10^{-3}$. In the case of 3  mm we found that going below $\alpha$=1.3 or $w_{\rm smooth}=10^{-2}$ produced clearly artificial ripples in the profile, and we thus used these values. We then imaged the residuals after subtracting the FRANK visibilities from the observed ones (Supplementary Fig. 2), which appear largely signal-free: the residuals are below three times the image noise (rms) in the case of the 3 mm observations, and the 1.3 mm show only two localised blobs around the 5 rms level.

We performed two sanity checks to ensure that the observed structures are not an artefact from FRANK. First, we also calculated the radial profiles directly from the synthesised images using the GOFISH code (cite: GoFish). These profiles have less spatial resolution (image synthesis incurs some information loss during the binning and weighting of visibilities), but serve to confirm that substructures are present in the 3 mm image and are not an artefact of FRANK. For this purpose, we produced images with `robust=-0.5` to improve the angular resolution. The ring and two gaps are also visible in the image profile. The cavity is only tentatively detected in the profile as a flattening of the intensity in the inner regions.

In addition, we also used the non-parametric GPUVMEM image reconstruction code (cite: Carcamo_2018) to create a maximum-entropy version of the image. The maximum-entropy method implemented in GPUVMEM belongs to the family of regularised maximum likelihood methods, which have gained significant traction in recent years (cite: EHT_2019; Zawadzki_2023; mpol). The self-calibrated continuum data were super-resolved using GPUVMEM with no entropy term in the objective function (cite: Carcamo_2018); image positivity alone provided sufficient regularisation (cite: Perez_2020). This approach yielded an image with slightly higher angular resolution and sensitivity compared to an equivalent `tclean` image. The GPUVMEM image reproduces the same substructures identified in the `tclean` image while also revealing a small central cavity.

These tests confirm that the inner cavity, ring, and gaps recovered by FRANK are real features. The 3 mm `robust=-0.5` and the GPUVMEM images, as well as the corresponding radial profiles, are provided in the Supplementary Figs. 2 and 3.

## PHANTOM simulations

### Hydrodynamical simulations

We ran 3D global hydrodynamical simulations using the SPH code PHANTOM (cite: Price_2018), widely used to study gas and dust dynamics in planet forming environments (cite: Dipierro_2015; Toci_2020; Veronesi_2020). To model the inner cavity of MP Mus, we ran a grid of 25 simulations varying the semi-major axis and the mass of the companion within ranges compatible with the *Gaia* PMa. In all the simulations, the mass of the star is $M_\star = 1.3~M_\odot$ and the disk mass is $M_{\rm disk} = 0.01~M_\odot$ (informed by the dust mass calculated from the 3 mm emission and adopting a standard gas-to-dust ratio of 100, see section 1 of the Supplementary Material). The disk is locally isothermal with a mid-plane temperature profile $T\propto R^{-0.5}$, and the initial surface density profile follows $\Sigma \propto R^{-1}$. We adopted a typical disk aspect ratio $H/R$ to 0.1 at a reference radius of 100 au (cite: Law_2021; Paneque_2023). The resolution is set by the number of particles ($N=10^6$). The outer radius is initialised to 50 au as traced by the 1.3 mm continuum observations, and the inner radius is chosen according to the semi-major axis of the inner companion $a_{\rm p}$, namely $R_\text{in} = 1.5~a_{\rm p}$. The central star and the companion were modelled as sink particles, with accretion radii $R_{\rm acc, \star}=0.75~a_{\rm p}$ for the central star and $R_{\rm acc, p}=0.25R_h$ for the secondary, where $R_{\rm h}$ is the companion Hill radius. The choice of the primary sink radius is safe since it is always smaller than the semi-major axis of the companion, and the radius of cavity we observe is always 3-4 times bigger, meaning that it is carved by the tidal interaction rather than being a numerical artefact. We used SPH shock capturing viscosity to model the mechanisms transporting the angular momentum through the disk, prescribing shock capturing viscosity coefficients $\alpha_\text{AV} = 0.2$ and $\beta_\text{AV} = 2$ which resulted in a viscosity parameter of $\alpha_\text{\rm ss}= 5\times10^{-3}$.

The dust component is set by adopting an initial gas-to-dust ratio of 100 uniformly across the entire disk. We simulated five dust grains sizes ranging from $1~\mu$m to 0.5 cm and with intrinsic density 3 g cm$^{-3}$. The dust is treated with the mixture algorithm, also known as one fluid algorithm (Laibe Price), suitable for coupled dust grains. The mass of the five different grain size populations is calculated according to $n(s) \propto s^{-3.5}$, where $s$ is the grain size.

The mass and semi-major axis of the companion are $M_p\in(3,5,7,10,15)~ M_{\rm Jup}$ and $a_p\in(0.5,1,1.5,2,2.5)$ au, as discussed in section [1.1](#sec:PMa). We let the simulations evolve for $1000$ planet orbits, enough time to ensure that the inner cavity reaches a steady state (cite: Ragusa_2020).

### Radiative transfer

The thermal structure and the 1.3 mm and 3 mm continuum emission images were computed using the Monte Carlo radiative transfer code MCFOST (cite: MCFOST; MCFOST2). The code takes as input the distribution of gas and dust grains from the hydrodynamical simulation to create a Voronoi mesh where each cell corresponds to an SPH particle. The disk receives passive heating from the central star, modelled as a black body with temperature of 5000 K, radius $R_\star$=1.25 $R_\odot$ and mass $M_\star$=1.3 $M_\odot$. We adopted a DIANA standard dust composition (cite: Woitke_2016; Min_2016) – i.e. 60% silicates, 15% amorphous carbon (cite: Dorschner_1995; Zubko_1996) and 25% porosity. The code assumes that sub-$\mu$m grains follow the gas, while the spatial distribution of dust grains between $\mu$m and cm is obtained by interpolation. We discretise the radiation field using $N_\gamma = 10^8$ photons in order to compute the temperature structure of the disk assuming local thermal equilibrium. Images are then computed via ray-tracing again with $N_\gamma = 10^8$ photons.

# Data availability

All the data used in this work are publicly available through the ALMA archive (programs 2022.1.01758.S and 2017.1.01167.S) and the *Gaia* archive.

# Code availability

The Python packages used in this study are publicly available:\
ASTROMET (<https://github.com/zpenoyre/astromet.py>),\
FRANK (<https://github.com/discsim/frank>),\
PHANTOM (<https://github.com/danieljprice/phantom>),\
MCFOST (<https://github.com/cpinte/mcfost>),\
and GPUVMEM (<https://github.com/miguelcarcamov/gpuvmem>).

# Acknowledgements

We thank the reviewers for their careful analysis of this work, which has significantly improved the manuscript. We also thank Marion Villenave and Stefano Facchini for insightful discussions and comments, and Miguel Cárcamo for his help with running `gpuvmem`. A.R., C.L, and C.J.C. have been supported by the UK Science and Technology Facilities Council (STFC) via the consolidated grant ST/W000997/1. This project has received funding by the European Union’s Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreements No. 823823 (RISE DUSTBUSTERS project). N.C. acknowledges funding from the European Research Council (ERC) under the European Union Horizon Europe programme (grant agreement No. 101042275, project Stellar-MADE). S.P. acknowledges support from FONDECYT grant 1231663 and funding from ANID – Millennium Science Initiative Program – Center Code NCN2024_001. I.dG. acknowledges support from grant PID2020-114461GB-I00, funded by MCIN/AEI/10.13039/501100011033. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01758.S and ADS/JAO.ALMA#2017.1.01167.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Author contributions

A.R. led the ALMA Band 3 proposal, processed and analysed the ALMA observations, led the project, and wrote the manuscript. M.V. performed the analysis of the *Gaia* proper motion anomaly of MP Mus. F.Z. and E.M. aided with the processing of the ALMA data. C.L. ran the PHANTOM simulations. S.P. produced the `gpuvmem` images of MP Mus. All authors contributed to the interpretation of the results and commented on the manuscript.

# Competing interests

The authors declare no competing interests.

# Supplementary material

## Properties and additional analysis of the ALMA data at 3 mm

We measured a 3 mm flux of 22$\pm$1 mJy from the image synthesised with `robust=0.5`. The uncertainty is largely dominated by the absolute calibration (5% in Band 3, see the ALMA Technical Handbook). We then calculated a dust disk mass of $0.12^{+0.03}_{-0.02}$ $M_{\rm Jup}$ using standard assumptions (cite: Andrews_2005): optically thin emission, an average dust temperature of 20 K, and a power-law dependence of the dust opacity with frequency following $\kappa_\nu = \kappa_\text{230 GHz} (\nu/\text{230 GHz})^\beta$, where $\kappa_\text{230 GHz}$=2.3 cm$^2$ g$^{-1}$ and $\beta$ values between 0 and 0.5, as typically inferred in protoplanetary disks (cite: Tazzari_2021). To determine the disk mass and its uncertainty we bootstrapped 1000 estimates by varying the 3 mm flux within its uncertainty, as well as the temperature value following a Normal distribution with a standard deviation of 2.5 K, and $\beta$ with a uniform distribution between 0 and 0.5. The reported dust mass and uncertainties correspond to the median and the 16% and 84% values. This mass is compatible with the dust mass derived from the 1.3 mm flux in (cite: Ribas_2023).

The radii encompassing 68%, 90%, and 95% of the 3 mm continuum flux are 22$\pm$5 au, 35$\pm$5 au, and 44$\pm$5 au respectively, based on the cumulative curve of the intensity profiles. We used the `robust=0` images for this purpose as they provide a good compromise between angular resolution and sensitivity, but the results with other weightings are compatible within beam size of the observations. The comparison with the $R_{68\,\%}$ and $R_{90\,\%}$ values at 1.3 mm reported in (cite: Ribas_2023) also shows that the disk appears $\sim$30% more compact at 3 mm.

The 3 mm `robust=-0.5` image using `tclean` in `CASA` and the one produced by GPUVMEM and convolved with a similar beam are presented in Fig. [5](#fig:B3_robust-0.5). Fig. [6](#fig:frank_residuals) shows the residuals of the FRANK fit for both wavelengths. These were obtained by first subtracting the FRANK visibilities from the observed ones, and then imaging the result with `robust=0.0`. Finally, the radial profiles calculated from the `robust=-0.5` and GPUVMEM images using GOFISH (cite: GoFish) are shown in Fig. [7](#fig:rad_profiles_image).

![image](figures/supplementary/B3_robust-0p5.pdf) ![image](figures/supplementary/B3_gpuvmem.pdf)

![image](figures/supplementary/frank_residuals_B3.pdf) ![image](figures/supplementary/frank_residuals_B6.pdf)

![](figures/supplementary/rad_profiles_image.pdf)

## Full set of PHANTOM simulations

Figure [8](#fig:PHANTOM_full) shows the corresponding radial profiles for the full grid of PHANTOM models. As mentioned in Section [2.3](#sec:PHANTOM), companions at separations $<$1 au do not open a large enough cavity, while separations $\geq$2 au carve cavities that are too wide. Increasing the mass of the planet results in deeper cavities. It is also worth noticing that a 3-7 $M_{\rm Jup}$ companion at $\sim$1 au creates a cavity at 3 mm that remains undetected at 1.3 mm, just as observed in the ALMA data. However, this is highly sensitive to the disk and dust properties which we have not explored in detail, and should therefore be considered as a strong indication that planets with such properties can explain the observations, rather than as precise measurements of the planet location and mass.

![](figures/supplementary/rad_profiles_phantom_full.pdf)

10 url urlprefix

(ref: Keppler_2018) Keppler, M. *et al.* . *Astron. Astrophys.* **617**, A44 (2018).

(ref: Haffert_2019) Haffert, S. Y. *et al.* . *Nat. Astron.* **3**, 749–754 (2019).

(ref: Barber_2024) Barber, M. G. *et al.* . *Nature* **635**, 574–577 (2024).

(ref: Testi_2015) Testi, L. *et al.* . *Astrophys. J. Lett.* **812**, L38 (2015).

(ref: Donati_2020) Donati, J. F. *et al.* . *Mon. Not. R. Astron. Soc.* **491**, 5660–5670 (2020).

(ref: Andrews_2018) Andrews, S. M. *et al.* . *Astrophys. J. Lett.* **869**, L41 (2018).

(ref: Long_2018) Long, F. *et al.* . *Astrophys. J.* **869**, 17 (2018).

(ref: Bae_2023) Bae, J. *et al.* , S., Aikawa, Y., Muto, T., Tomida, K. & Tamura, M. (eds) *Structured Distributions of Gas and Solids in Protoplanetary Disks*. (eds Inutsuka, S., Aikawa, Y., Muto, T., Tomida, K. & Tamura, M.) *Protostars and Planets VII*, Vol. 534 of *Astronomical Society of the Pacific Conference Series*, 423 (2023). .

(ref: Weidenschilling_1977) Weidenschilling, S. J. *Mon. Not. R. Astron. Soc.* **180**, 57–70 (1977).

(ref: Brauer_2007) Brauer, F. *et al.* . *Astron. Astrophys.* **469**, 1169–1182 (2007).

(ref: Paardekooper_2004) Paardekooper, S. J. & Mellema, G. . *Astron. Astrophys.* **425**, L9–L12 (2004).

(ref: Lyra_2009) Lyra, W., Johansen, A., Klahr, H. & Piskunov, N. . *Astron. Astrophys.* **493**, 1125–1139 (2009).

(ref: Pinilla_2012) Pinilla, P., Benisty, M. & Birnstiel, T. . *Astron. Astrophys.* **545**, A81 (2012).

(ref: Garufi_2024) Garufi, A. *et al.* . *Astron. Astrophys.* **685**, A53 (2024).

(ref: Ginski_2024) Ginski, C. *et al.* . *Astron. Astrophys.* **685**, A52 (2024).

(ref: Ribas_2023) Ribas, Á. *et al.* . *Astron. Astrophys.* **673**, A77 (2023).

(ref: Gaia_2021b) Gaia Collaboration *et al.* . *Astron. Astrophys.* **649**, A1 (2021).

(ref: Toci_2021) Toci, C., Rosotti, G., Lodato, G., Testi, L. & Trapman, L. . *Mon. Not. R. Astron. Soc.* **507**, 818–833 (2021).

(ref: Aguayo_2025) Aguayo, Aurora *et al.* . *Astron. Astrophys.* **698**, A165 (2025).

(ref: Wolff_2016) Wolff, S. G. *et al.* . *Astrophys. J. Lett.* **818**, L15 (2016).

(ref: Avenhaus_2018) Avenhaus, H. *et al.* . *Astrophys. J.* **863**, 44 (2018).

(ref: Haisch_2001) Haisch, K. E., Jr., Lada, E. A. & Lada, C. J. . *Astrophys. J. Lett.* **553**, L153–L156 (2001).

(ref: Fedele_2010) Fedele, D., van den Ancker, M. E., Henning, T., Jayawardhana, R. & Oliveira, J. M. . *Astron. Astrophys.* **510**, A72 (2010).

(ref: Ribas_2015) Ribas, Á., Bouy, H. & Merı́n, B. . *Astron. Astrophys.* **576**, A52 (2015).

(ref: Perryman_2014) Perryman, M., Hartman, J., Bakos, G. Á. & Lindegren, L. . *Astrophys. J.* **797**, 14 (2014).

(ref: Kervella_2019) Kervella, P., Arenou, F., Mignard, F. & Thévenin, F. . *Astron. Astrophys.* **623**, A72 (2019).

(ref: Kervella_2022) Kervella, P., Arenou, F. & Thévenin, F. . *Astron. Astrophys.* **657**, A7 (2022).

(ref: deRosa2023) De Rosa, R. J. *et al.* . *Astron. Astrophys.* **672**, A94 (2023).

(ref: Mesa_2023) Mesa, D. *et al.* . *Astron. Astrophys.* **672**, A93 (2023).

(ref: Currie_2023) Currie, T. *et al.* . *Science* **380**, 198–203 (2023).

(ref: Kiefer_2024) Kiefer, F., Lagrange, A.-M., Rubini, P. & Philipot, F. . *arXiv e-prints* arXiv:2409.16993 (2024).

(ref: Ingleby_2023) Ingleby, L. *et al.* . *Astrophys. J.* **767**, 112 (2013).

(ref: Penoyre_2022a) Penoyre, Z., Belokurov, V. & Evans, N. W. . *Mon. Not. R. Astron. Soc.* **513**, 2437–2456 (2022).

(ref: Penoyre_2022b) Penoyre, Z., Belokurov, V. & Evans, N. W. . *Mon. Not. R. Astron. Soc.* **513**, 5270–5289 (2022).

(ref: Boubert_2021) Boubert, D., Everall, A., Fraser, J., Gration, A. & Holl, B. . *Mon. Not. R. Astron. Soc.* **501**, 2954–2968 (2021).

(ref: Pinilla_2015) Pinilla, P. *et al.* . *Astron. Astrophys.* **584**, A16 (2015).

(ref: frank) Jennings, J., Booth, R. A., Tazzari, M., Rosotti, G. P. & Clarke, C. J. . *Mon. Not. R. Astron. Soc.* **495**, 3209–3232 (2020).

(ref: Zhang_2015) Zhang, K., Blake, G. A. & Bergin, E. A. . *Astrophys. J. Lett.* **806**, L7 (2015).

(ref: Flock_2015) Flock, M. *et al.* . *Astron. Astrophys.* **574**, A68 (2015).

(ref: Gonzalez_2017) Gonzalez, J. F., Laibe, G. & Maddison, S. T. . *Mon. Not. R. Astron. Soc.* **467**, 1984–1996 (2017).

(ref: Dong_2017) Dong, R., Li, S., Chiang, E. & Li, H. . *Astrophys. J.* **843**, 127 (2017).

(ref: Bae_2017) Bae, J., Zhu, Z. & Hartmann, L. . *Astrophys. J.* **850**, 201 (2017).

(ref: Ziampras_2020) Ziampras, A., Kley, W. & Dullemond, C. P. . *Astron. Astrophys.* **637**, A50 (2020).

(ref: AsensioTorres_2021) Asensio-Torres, R. *et al.* . *Astron. Astrophys.* **652**, A101 (2021).

(ref: Ruzza_2024) Ruzza, A., Lodato, G. & Rosotti, G. P. . *Astron. Astrophys.* **685**, A65 (2024).

(ref: Artymowicz_1994) Artymowicz, P. & Lubow, S. H. . *Astrophys. J.* **421**, 651 (1994).

(ref: Ragusa_2020) Ragusa, E., Alexander, R., Calcino, J., Hirsh, K. & Price, D. J. . *Mon. Not. R. Astron. Soc.* **499**, 3362–3380 (2020).

(ref: Price_2018) Price, D. J. *et al.* . *Publ. Astron. Soc. Aust.* **35**, e031 (2018).

(ref: MCFOST) Pinte, C., Ménard, F., Duchêne, G. & Bastien, P. . *Astron. Astrophys.* **459**, 797–804 (2006).

(ref: MCFOST2) Pinte, C. *et al.* . *Astron. Astrophys.* **498**, 967–980 (2009).

(ref: GoFish) Teague, R. Gofish: Fishing for line observations in protoplanetary disks. *The Journal of Open Source Software* **4**, 1632 (2019). URL .

(ref: Drkazkowska_2017) Drążkowska, J. & Alibert, Y. . *Astron. Astrophys.* **608**, A92 (2017).

(ref: Alexander_2012) Alexander, R. D. & Pascucci, I. . *Mon. Not. R. Astron. Soc.* **422**, L82–L86 (2012).

(ref: Zakhozhay_2022) Zakhozhay, O. V. *et al.* . *Astron. Astrophys.* **667**, A63 (2022).

(ref: Johns-Krull_2016) Johns-Krull, C. M. *et al.* . *Astrophys. J.* **826**, 206 (2016).

(ref: Biddle_2018) Biddle, L. I., Johns-Krull, C. M., Llama, J., Prato, L. & Skiff, B. A. . *Astrophys. J. Lett.* **853**, L34 (2018).

(ref: Donati_2024) Donati, J. F. *et al.* . *Mon. Not. R. Astron. Soc.* **530**, 264–286 (2024).

(ref: Manick_2024) Manick, R. *et al.* . *Astron. Astrophys.* **686**, A249 (2024).

(ref: CarrascoGonzalez_2019) Carrasco-González, C. *et al.* . *Astrophys. J.* **883**, 71 (2019).

(ref: Huang_2020) Huang, J. *et al.* . *Astrophys. J.* **891**, 48 (2020).

(ref: Doi_2023) Doi, K. & Kataoka, A. . *Astrophys. J.* **957**, 11 (2023).

(ref: Carcamo_2018) Cárcamo, M., Román, P. E., Casassus, S., Moral, V. & Rannou, F. R. . *Astron. Comput.* **22**, 16–27 (2018).

(ref: EHT_2019) Event Horizon Telescope Collaboration *et al.* . *Astrophys. J. Lett.* **875**, L1 (2019).

(ref: Zawadzki_2023) Zawadzki, B. *et al.* . *Publ. Astron. Soc. Pac.* **135**, 064503 (2023).

(ref: mpol) Czekala, I. *et al.* Mpol-dev/mpol: v0.2.0 release (2023). URL .

(ref: Perez_2020) Pérez, S. *et al.* . *Astrophys. J. Lett.* **889**, L24 (2020).

(ref: Dipierro_2015) Dipierro, G. *et al.* . *Mon. Not. R. Astron. Soc.* **453**, L73–L77 (2015).

(ref: Toci_2020) Toci, C., Lodato, G., Fedele, D., Testi, L. & Pinte, C. . *Astrophys. J. Lett.* **888**, L4 (2020).

(ref: Veronesi_2020) Veronesi, B. *et al.* *Mon. Not. R. Astron. Soc.* **495**, 1913–1926 (2020).

(ref: Law_2021) Law, C. J. *et al.* . *Astrophys. J. Suppl. Ser.* **257**, 4 (2021).

(ref: Paneque_2023) Paneque-Carreño, T. *et al.* . *Astron. Astrophys.* **669**, A126 (2023).

(ref: Woitke_2016) Woitke, P. *et al.* . *Astron. Astrophys.* **586**, A103 (2016).

(ref: Min_2016) Min, M., Rab, C., Woitke, P., Dominik, C. & Ménard, F. . *Astron. Astrophys.* **585**, A13 (2016).

(ref: Dorschner_1995) Dorschner, J., Begemann, B., Henning, T., Jaeger, C. & Mutschke, H. *Astron. Astrophys.* **300**, 503 (1995).

(ref: Zubko_1996) Zubko, V. G., Mennella, V., Colangeli, L. & Bussoletti, E. . *Mon. Not. R. Astron. Soc.* **282**, 1321–1329 (1996).

(ref: Andrews_2005) Andrews, S. M. & Williams, J. P. . *Astrophys. J.* **631**, 1134–1160 (2005).

(ref: Tazzari_2021) Tazzari, M. *et al.* . *Mon. Not. R. Astron. Soc.* **506**, 2804–2823 (2021).

[^1]: [Gaia documentation](https://gea.esac.esa.int/archive/documentation/GDR3/Gaia_archive/chap_datamodel/sec_dm_auxiliary_tables/ssec_dm_commanded_scan_law.html)

</paper>

Write the methods card for this paper.