# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...976..241Y\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024ApJ...976..241Y",
 "title": "The ALMA-QUARKS Survey: Fibers' Role in Star Formation Unveiled in an Intermediate-mass Protocluster Region of the Vela D Cloud",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Yang, Dongting",
 "n_authors": 35,
 "arxiv_id": "2410.15333",
 "doi": "10.3847/1538-4357/ad8919",
 "alma_projects_linked_by_archive": [
  "2019.1.00685.S",
  "2021.1.00095.S"
 ]
}
```

Paper text:
<paper>
# **The ALMA-QUARKS Survey: Fibers’ role in star formation unveiled in an intermediate-mass protocluster region of the Vela D cloud**

## Abstract

In this paper, we present a detailed analysis of the IRS 17 filament within the intermediate-mass protocluster IRAS 08448-4343 (of $\sim\,10^3$ $L_{\odot}$), using ALMA data from the ATOMS 3-mm and QUARKS 1.3-mm surveys. The IRS 17 filament, which spans $\sim$54000 au ($0.26\,\rm pc$) in length and $\sim$4000 au ($0.02\,\rm pc$) in width, exhibits a complex, multi-component velocity field, and harbours hierarchical substructures. These substructures include three bundles of seven velocity-coherent fibers, and 29 dense ($n\sim 10^8\,\rm cm^{-3}$) condensations. The fibers have a median length of $\sim 4500\,\rm au$ and a median width of $\sim 1400\,\rm au$. Among these fibers, four are identified as “fertile", each hosting at least three dense condensations, which are regarded as the “seeds" of star formation. While the detected cores are randomly spaced within the IRS 17 filament based on the 3-mm dust continuum image, periodic spacing ($\sim1600\,\rm au$) of condensations is observed in the fertile fibers according to the 1.3-mm dust map, consistent with the predictions of linear isothermal cylinder fragmentation models. These findings underscore the crucial role of fibers in star formation and suggest a hierarchical fragmentation process that extends from the filament to the fibers, and ultimately, to the smallest-scale condensations.

# Introduction

Filamentary structuresare prevalent in the molecular clouds of the Milky Way, and recognized to play a vital role in both low-mass and high-mass star formation scenarios (cite: 2010A&A...518L.100M; 2010A&A...518L.102A; 2014prpl.conf...27A; 2020A&A...635A..34K; 2023MNRAS.522.3719L). *Herschel* dust continuum observations in far/submillimeter bands have demonstrated that prestellar cores and protostars predominantly form in the densest filaments within molecular clouds . Moreover, filaments resolved in nearby star-forming regions exhibit a power-law distribution for both the filament mass function (FMF), $\frac{\mathrm{d}N}{\mathrm{d}M} \propto M^{-2.6}$, and filament line mass function (FLMF), $\frac{\mathrm{d}N}{\mathrm{d}m} \propto m^{-2.4}$, respectively (cite: 2019A&A...629L...4A). This may naturally result in a power-law distribution of core masses (cite: 2019A&A...629L...4A; 2019A&A...621A..42A), i.e., the core mass function (CMF). Accordingly, the CMF has also been observed to agree well with the stellar initial mass function (IMF) in the range of low to intermediate stellar masses ($\sim 0.1-5$ $M_{\odot}$, (cite: 2010A&A...518L.106K)), as previously reported . Nonetheless, this agreement has been observed to be challenging in regions of massive star formation , with an evident deviation between the CMF and the IMF in terms of the slope at the high-mass end. In this context, filaments play a critical role in the star formation process, setting up its initial conditions. However, their formation, evolution into substructures, dense cores, and ultimately stars, is still not fully understood.

![](RGB.pdf)

Substantial progress has been made in deciphering the evolution of filaments. When scrutinized at a high enough resolution, an increasing number of studies reveal a new type of dense molecular filaments at small scales, which are called dense fibers. These fibers are detected across the mass spectrum of clouds, for example, in low-mass clouds (cite: 2013A&A...554A..55H; 2013A&A...553A.119A; 2016A&A...590A..75F), intermediate mass clusters (cite: 2014ApJ...790L..19F; 2017A&A...606A.123H), and high-mass star-forming regions (cite: 2018A&A...610A..77H; 2019A&A...629A..81T; 2019A&A...623A..16S; 2022ApJ...926..165L; 2022ApJ...927..106C). As summarized by (cite: 2023ASPC..534..153H), the fibers typically display sub-parsec lengths ($L\lesssim$ 1pc), and have line masses near the critical value (cite: 2018A&A...610A..77H) for hydrostatic equilibrium. Fibers also exhibit high central gas densities $n_0 > 10^4$ cm$^{-3}$, and small characteristic widths (full width half maximum (FWHM)$<0.1$ pc; see (cite: 2018A&A...610A..77H), measured in the dense gas tracer, $\rm N_2H^+$ (1-0). It is interesting to note that the width of filaments or fibers depends on the gas tracer investigated. The widths are observed to be narrower for dense gas tracers, such as H$^{13}$CO$^{+}$$(1-0)$ and $\rm N_2H^+$ (1-0) as compared to the low-density gas tracers like $\rm ^{13}CO\,(1-0)$ and $\rm C^{18}O\,(1-0)$ (cite: 2023A&A...672A.133S).

Fibers correspond to the hierarchical substructure within larger and more massive filaments (cite: 2014prpl.conf...27A). Whether fibers or larger filaments form first remains a subject of debate due to the existence of two possibilities. That is, hierarchical fiber structures could arise either from top-down fragmentation due to the self-gravity of their parent filament (cite: 2013A&A...554A..55H; 2015A&A...574A.104T), or from a bottom-up process whereby gravitational collapse assembles larger filaments from gas containing pre-existing fibers (cite: 2014MNRAS.445.2900S).

In addition to dense fibers, dense cores are viewed as crucial substructures of filaments where stars form. The spacing of prestellar cores in star-forming filaments is generally observed to be non-periodic (cite: 2014prpl.conf...27A; 2020A&A...635A..34K), though a few examples of quasi-periodic chains of dense cores have been reported (cite: 2015A&A...574A.104T; 2020A&A...642A..76Z; 2019MNRAS.487.1259L; 2023ApJ...951...68C; 2023ApJ...957...94Y). Theoretically, periodic core spacing is predicted by standard semi-analytic cylinder fragmentation models within the framework of gravitational instability of filaments (e.g., (cite: 1963AcA....13...30S; 2010ApJ...719L.185J; 2018MNRAS.478.2119L)). This discrepancy between observations and simple theoretical predictions may be attributed to the presence of hierarchical fibers within larger filaments (cite: 2020MNRAS.497.4390C). Therefore, examining the substructures (i.e., fibers, and cores) of parental filaments is beneficial in understanding the evolution of filaments into cores and ultimately stars.

The target of this work is the IRAS 08448-4343 protocluster (see Fig. [1](#fig:RGB)), which is part of the Vela Molecular Ridge-D (VMR-D) cloud (cite: 1991A&A...247..202M) located at $\sim 1.2\pm0.1$ kpc (cite: 2024RAA....24b5009L). This distance is consistent with the range of 0.7 to 1.2 kpc estimated by (cite: 1992A&A...265..577L) using photometric distance methods. The IRAS 08448-4343 protocluster clump has a molecular gas mass of $\sim 116$ $M_{\odot}$ within a size of 0.5 pc, which have been scaled to the distance adopted here (e.g., (cite: 2004A&A...426...97F; 2020MNRAS.496.2790L)). This protocluster corresponds to a bright infrared (IR) source, IRS 17, identified by (cite: 1992A&A...265..577L) as an intermediate-mass Class I YSO object according to its luminosity of $\sim 10^3$ $L_{\odot}$ (cite: 1992A&A...265..577L; 1999A&AS..136..471M). Near-IR observations reveal that more than 20 jet knots are associated with IRS 17 ($\#\,57$ in (cite: 2002ApJ...564..839L) and (cite: 2005A&A...433..941G)). The *Spitzer* three-color image in 3.6/4.5/8.0 $\mu$m  (see Fig. [1](#fig:RGB)) displays an IR-bright patch and point sources surrounding IRS 17. Furthermore, the IRS 17 region appears as a compact source in radio centimeter emission (e.g., at 6 cm, (cite: 2007A&A...476.1019M)), which is confirmed by 1.28 GHz radio emission (see red contours in Fig. [1](#fig:RGB)), retrieved from the MeerKAT Galactic Plane Survey (cite: 2023MNRAS.524.1291P; 2024MNRAS.531..649G). This suggests strong feedback from ionized gas excited by the IRS 17 protocluster. From *Herschel* 250 $\mu$m emission, the molecular cloud hosting the IRS 17 region appears as a clumpy structure elongated along the northeast-southwest direction. This elongation is manifested as a filamentary structure (hereafter the IRS 17 filament) when observed in

ALMA 3-mm continuum image at a resolution of $\sim$2 $''$ (cite: 2024RAA....24b5009L).

In this work, we investigate the role of small-scale fibers in the evolution of the IRS 17 filament into cores/condensations, leveraging on the combination of the ALMA 3-mm and our new 1.3-mm observations (see below). This paper is structured as follows: observations are described in Section [2](#sec:obse); the results and analysis are presented in Section [3](#sec:result); the discussion is followed in Section [4](#sec:dsicussion); and finally the summary and conclusion are given in Section [5](#sec:summary).

![](band3_continuum_all.pdf)

![](band6_continuum.pdf)

# ALMA observations

The IRS 17 region was observed as part of the ALMA Three-millimeter Observations of Massive Star-forming regions (ATOMS) survey, which targeted 146 active massive protoclusters regions with the ALMA 7-m Atacama Compact Array (ACA) and the 12-m array in the 3-mm band (cite: 2020MNRAS.496.2790L). The data were calibrated in CASA 5.6 (cite: 2007ASPC..376..127M). The ACA and 12-m array data were jointly imaged and cleaned using natural weighting for pblimit = 0.2, in the CASA tclean task, for both continuum images and line cubes. The combined data for the IRS 17 region have a field of view (FoV) and a maximum recoverable scale both of $\sim80\ensuremath{''}$ or 0.5 pc at the distance of IRS 17 (e.g.; $1.2\pm0.1\,\rm kpc$). The combined continuum data have a synthesized beam size of $1.6\ensuremath{''} \times 1.2\ensuremath{''}$, and a typical sensitivity of $rms\sim0.2$ mJy beam$^{-1}$. The H$^{13}$CO$^{+}$ (1–0) line cube, used here for kinematics analysis, has a synthesized beam size of $1.8\ensuremath{''} \times 1.4\ensuremath{''}$ and a sensitivity of $rms \sim8$ mJy beam$^{-1}$ at a velocity resolution of $\rm \sim 0.2\,km~s^{-1}$. Details on the observing setups of the survey and its data reduction can be found in (cite: 2020MNRAS.496.2790L; 2020MNRAS.496.2821L; 2021MNRAS.505.2801L; 2022MNRAS.510.5009L; 2022MNRAS.511.4480L).

IRS 17 was also observed as part of the Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures (QUARKS) survey, complementing the ATOMS survey with higher angular resolution ($\sim 0.3\ensuremath{''}$). The observations were carried out with both the ACA and 12-m arrays (cite: 2024RAA....24b5009L). In particular, the elongated spatial extent of the IRS 17 region was covered by two pointings, each of which has a field of view of 40$''$ or 0.2 pc (see the yellow curve in Fig. [2](#fig:band3:con)), and a maximum recoverable scale of $\sim20\,\ensuremath{''}$ or 0.1 pc. The ACA and 12-m data were independently calibrated in CASA 6.5, and then jointly imaged and cleaned using the CASA tclean task for both continuum images and line cubes. The combined ACA and 12-m continuum data for the IRS 17 region have a synthesized beam size of $0.34\ensuremath{''} \times 0.33\ensuremath{''}$, corresponding to $\sim$400 au at a distance of the source. The sensitivity of the continuum data is $\sim0.15\,\rm\,mJy\,beam^{-1}$, which translates to a mass sensitivity of $\sim 10^{-3}$ $M_{\odot}$  for a dust temperature of $\sim 25$ K (see Sect. [3.2.1](#subsub:sec:fibers and condensation) for the detailed mass calculation). Moreover, the QUARKS survey includes the data of major lines at 1.3 mm, such as $\rm N_2D^+$, DCN, $\rm H_2CO$, and $\rm ^{13}CS$ (see Table 1 of (cite: 2024RAA....24b5009L)). The native velocity resolution of these line data is 0.6–0.7 km s$^{-1}$. However, these line data have low detection rates in the IRS 17 region, and hence are considered only for ancillary analysis. Details on the observing setups of the survey and data reduction are described in (cite: 2024RAA....24b5009L) and (cite: 2024arXiv240402275X)

+:---------+:----------------------:+:----------------------:+:-----------------:+:-----------------------:+:-----------------:+:-----------------------:+:------------:+:-------------------:+:-----------:+
| Name     | *          $\rm Position^{\it a}$          *    | *          $L^{\it b}$          *           | *          $W^{\it b}$          *           | Aspect ratio | $S^{\rm int}_{\nu}$ | Data Source |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
|          | $\alpha$(J2000)        | $\delta$(J2000)        | ($''$)            | $(\rm \times 10^3\,au)$ | ($''$)            | $(\rm \times 10^3\,au)$ |              | (mJy)               |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| Filament | 08:46:33.84            | -43:54:32.53           | $43.5\pm4.4$      | $53.6\pm5.4$            | $3.2\pm1.5$       | $3.9\pm1.9$             | 13.6         | $43.8\pm4.4$        | 3 mm        |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| fiber    |                        |                        |                   |                         |                   |                         |              |                     | 1.3 mm      |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| 1        | 08:46:35.12            | -43:54:23.44           | $5.5\pm0.6$       | $6.7\pm0.7$             | $1.5\pm0.6$       | $1.9\pm0.8$             | 3.7          | $103.8\pm10.4$      |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| 2        | 08:46:34.92            | -43:54:32.46           | $3.8\pm0.4$       | $4.6\pm0.5$             | $1.2\pm0.3$       | $1.5\pm0.4$             | 3.1          | $34.8\pm3.5$        |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| 3        | 08:46:34.47            | -43:54:33.00           | $3.5\pm0.4$       | $4.3\pm0.4$             | $1.2\pm0.5$       | $1.5\pm0.6$             | 3.0          | $44.5\pm4.5$        |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| 4        | 08:46:34.05            | -43:54:34.54           | $3.5\pm0.4$       | $4.3\pm0.4$             | $1.1\pm0.3$       | $1.3\pm0.4$             | 3.5          | $27.2\pm2.7$        |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| 5        | 08:46:33.49            | -43:54:34.66           | $6.6\pm0.7$       | $8.0\pm0.8$             | $0.9\pm0.6$       | $1.1\pm0.8$             | 7.8          | $78.9\pm7.9$        |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| 6        | 08:46:33.40            | -43:54:38.20           | $2.6\pm4.4$       | $3.2\pm0.3$             | $0.8\pm0.2$       | $1.0\pm0.3$             | 3.2          | $50.5\pm5.1$        |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+
| 7        | 08:46:32.69            | -43:54:36.17           | $7.1\pm0.7$       | $8.7\pm0.9$             | $1.3\pm0.8$       | $1.5\pm0.9$             | 5.8          | $111.5\pm11.2$      |             |
+----------+------------------------+------------------------+-------------------+-------------------------+-------------------+-------------------------+--------------+---------------------+-------------+

: Parameters of filament and fibers obtained with the *getsf* algorithm

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $M$ | $m$ | $m^{\rm tur}_{\rm crit}$ | $\langle n \rangle$ | $v_{\rm lsr}^*$ | $\sigma _{\rm obs}^*$ |
|  | ($M_{\odot}$) | ($M_{\odot}$$\rm ~pc^{-1}$) | ($M_{\odot}$$\rm ~pc^{-1}$) | $\rm (\times 10^7\,cm^{-3})$ | $\rm (km\,s^{-1})$ | $\rm (km\,s^{-1})$ |
| Filament | $24.9\pm5.0$ | $95.8\pm19.2$ | $70.7\pm29.1$ | $0.49\pm0.15$ | $3.26\pm1.15$ | $0.39\pm0.25$ |
| fiber |  |  |  |  |  |  |
| 1 | $2.54\pm0.51$ | $77.0\pm15.4$ | $178.7\pm47.6$ | $1.70\pm0.34$ | $5.11\pm0.30$ | $0.62\pm0.32$ |
| 2 | $0.83\pm0.17$ | $37.7\pm7.5$ | $67.1\pm5.6$ | $1.29\pm0.10$ | $5.31\pm0.20$ | $0.38\pm0.11$ |
| 3 | $1.09\pm0.22$ | $51.9\pm10.4$ | $50.6\pm29.1$ | $1.82\pm0.36$ | $3.25\pm0.87$ | $0.33\pm0.25$ |
| 4 | $0.66\pm0.13$ | $31.4\pm6.3$ | $47.6\pm22.5$ | $1.47\pm0.15$ | $3.11\pm0.79$ | $0.32\pm0.22$ |
| 5 | $1.92\pm0.38$ | $49.2\pm9.8$ | $70.7\pm24.6$ | $3.20\pm1.60$ | $3.39\pm0.27$ | $0.39\pm0.23$ |
| 6 | $1.23\pm0.25$ | $82.0\pm16.4$ | $90.0\pm7.9$ | $6.21\pm0.62$ | $3.10\pm0.40$ | $0.44\pm0.13$ |
| 7 | $2.72\pm0.54$ | $61.8\pm12.4$ | $94.2\pm9.1$ | $2.24\pm0.89$ | $2.33\pm0.64$ | $0.45\pm0.14$ |

: Estimated properties and velocity information of filament and fibers

# Results and analysis

## IRS 17 filament seen in ATOMS 3-mm continuum

Figure [2](#fig:band3:con) shows the 3-mm continuum map of the IRS 17 protocluster region (also refer to Fig. [7](#fig:band3:band6)a). The IRS 17 filament extends from the northeast to the southwest. To identify this filament, the *getsf* extraction algorithm (cite: 2021A&A...649A..89M) was used. This algorithm has been widely employed in previous studies (cite: 2023MNRAS.520.3259X; 2024arXiv240402275X; 2024MNRAS.527.5895D; 2024arXiv240718719L) due to its effectiveness in handling uneven noise background, separating blended sources/filaments, and extracting extended emission features. After applying the *getsf* to the 3-mm continuum map, we obtained a single filament skeleton and its footprint, that are shown in Fig. [2](#fig:band3:con) as the black line and the dashed contour, respectively. The filament parameters measured by the *getsf* algorithm are listed in Table [1](#tab:filament). These include the center positions, length, width, and integrated flux. The IRS 17 filament has a length of $\sim 5\times10^4\,\rm au$ (0.26 pc) and a width of $\sim 4\times 10^3\,\rm au$ (0.02 pc). The tablulated widths

refer to the mean values of the median widths obtained from both side by the *getsf* algorithm. Note that the median width corresponds to half-power diameters estimated directly from the profiles using *getsf*, without any fitting, such as Gaussian or Plummer fitting (cite: 2021A&A...649A..89M).

Assuming that 3-mm continuum emission is optically thin and arises primarily from thermal dust radiation, we can compute the mass of the IRS 17 filament using the expression

$$\begin{equation}
\label{equ:mass:cal}
    M=\frac{S^{\rm int}_\nu D^2R_{\rm gd}}{\kappa_\nu B_\nu(T_{\rm dust})},
\end{equation}$$ where the integrated flux, $S^{\rm int}_\nu$, is derived from 3-mm continuum emission, *D* is the source distance, the ratio of gas-to-dust, $R_{\rm gd}$, is assumed to be 100, and the dust opacity, $\kappa_\nu$, is taken as $0.18 \rm\,cm^{2}~g^{-1}$ at 3 mm (cite: 1994A&A...291..943O; 2021MNRAS.505.2801L). $B_\nu(T_{\rm dust}$) is the Planck function for a given dust temperature. Here, $T_{\rm dust}= \rm 25\,K$ is adopted for the IRS 17 filament, the same as its natal clump’s average temperature derived from the spectral energy distribution (cite: 2004A&A...426...97F).

The calculated mass of the IRS 17 filament is $M_{\rm F}\sim 24.9$ $M_{\odot}$. The line mass ($m_{\rm F}$) was computed as $m_{\rm F} = M_{\rm F}/L_{\rm F}\sim95.8$ $M_{\odot}$ $\rm pc^{-1}$. This line mass is around 2–3 times higher than those inferred from *Herschel* observations toward low mass star forming filaments, such as Musca (see Fig. 4 of (cite: 2016A&A...590A.110C)), and Taurus B211/3 (see Fig. 2 of (cite: 2013A&A...550A..38P)) but lower than those toward high-mass counterparts such as Orion ISF (cite: 2016A&A...590A...2S). Assuming that the FMF could naturally produce the CMF, which in turn is proportional to the IMF (cite: 2019A&A...629L...4A), this result suggests that the IRS 17 filament is an intermediate-mass star forming region. Additionally, it is also consistent with the presence of the intermediate-mass IR bright YSO (i.e., the IRS 17 point source). Moreover, assuming a uniform density distribution for the filament, the average number density ($\langle n_{\rm F} \rangle$, see Col.4 in Table [2](#tab:filament:calculated)) relates to $M_{\rm F}/(\pi r_{\rm F}^2 L)$, where $r_{\rm F}$ represents the radius of the filament ($r_{\rm F} = \frac{1}{2} W_{\rm F}$).

Within the footprint of the IRS 17 filament, ten 3 mm dense cores are identified (see Fig. [2](#fig:band3:con)). These cores were identified by (cite: 2021MNRAS.505.2801L), who utilized both the *astrodendro* algorithm and the *CASA imfit* function together for the identification. These cores have a mass range of 0.3-2.5 $M_{\odot}$  (see Table 4 of (cite: 2021MNRAS.505.2801L)) with sizes of the order of 0.01 pc. However, one of the cores (i.e., #2, see Fig. [2](#fig:band3:con)), with a mass of 2.0 $M_{\odot}$, is associated with the ionized gas excited by the intermediate-mass IRS 17 protocluster. Therefore, its mass could be overestimated by assuming that 3-mm continuum emission arises primarily from dust thermal emission. As such, the mass of this core should be interpreted with caution. It is worth noting that the same issue could influence the mass calculation of the natal filament, but not significantly. This is because the absolute value of the mass of the related core, which encompasses most of the ionized gas, is much lower than the filament mass. Furthermore, these dense cores within the filament do not exhibit a periodic chain-like distribution as seen in Fig. [2](#fig:band3:con), which will be discussed in Sect. [4.1](#sub:fiber:star:formation).

## Fibers and condensations in QUARKS 1.3-mm dust continuum 

Figure [3](#fig:bad6) displays the QUARKS 1.3-mm dust continuum map of the IRS 17 protocluster region (also refer to Fig. [7](#fig:band3:band6)b). The IRS 17 filament can still be observed in 1.3-mm emission, confirming the filamentary nature seen in 3-mm emission. This filament presents several substructures in 1.3-mm observations, including small-scale fibers and dense condensations. To identify them, the *getsf* algorithm was applied to the 1.3-mm dust continuum map. The bona fide fibers were identified based on the following three criteria: i) the peak flux of a fiber is detected at least at 3 $rms$ significance level, ii) the length of a fiber is at least 3 times the synthesized beam size at 1.3-mm, and iii) the aspect ratio is at least 3.

As a result, a total of 7 fibers and 24 condensations were obtained (Fig. [3](#fig:bad6)). However, upon a careful visual inspection, several dense fibers and condensations appear not be recognized by the *getsf* algorithm. Specifically, a network of fibers between condensations 25, 28 and 29 is seen in the figure but not detected by *getsf* (see Fig. [8](#fig:band6:zoomin)). This is because they are disjoint due to low peak emission of $<3$ $rms$ along each individual fiber in the network. In addition, this network of fibers does not appear as velocity coherent structures, which can be found in the H$^{13}$CO$^{+}$ (1–0) velocity field map (see Fig. [4](#fig:h13co:moment)b). To recover the missing condensations, another source extraction method, SExtractor (cite: 1996A&AS..117..393B; 2016zndo....804967B) was utilized, as adopted in other studies (e.g.; (cite: 2013A&A...549A..45C; 2014A&A...568A..41U; 2024arXiv240402275X)). This approach identified 6 additional condensations (i.e., C 1, C 18, C 19, C 22, C 23, and C 24), leading to a total of 30 condensations (refer to Table [4](#tab:core)). Except for C 30, all condensations are located in the IRS 17 filament (see Fig. 3). The parameters measured by the *getsf* for fibers are listed in Table [1](#tab:filament), including the center positions, length, width, and integrated flux. The parameters by the *getsf* or the SExtractor for condensations are given in Table [4](#tab:core), including the center positions, size, integrated flux and peak flux.

The gas kinematics of the IRS 17 filament and the identified fibers was inferred using the H$^{13}$CO$^{+}$ (1–0) molecular line transition from the ATOMS survey. The velocity centroid and the velocity dispersion of both filament and the fibers are tabulated in Table [2](#tab:filament:calculated).

### Derived parameters of fibers and condensations

Following Eq. [\[equ:mass:cal\]](#equ:mass:cal), we quantified the mass of fibers ($M_{\rm f}$) and condensations ($M_{\rm c}$) from the integrated flux at 1.3-mm, given the corresponding dust opacity $\kappa_{\rm 1.3mm} = 0.899\,\mathrm{cm^2\,g^{-1}}$ (cite: 1994A&A...291..943O) and the temperature of 25 K. Using the same approach as for the IRS 17 filament, we can estimate for fibers the line mass ($m_{\rm f}$), and the average number density ($\langle n_{\rm f} \rangle$). For condensations, assuming a uniform spherical density distribution, their number density can be inferred as $n_{\rm c} = \frac{3M_{\rm c}}{4\pi R_{\rm c}^3 \mu m_H}$, the mean molecular weight $\mu=2.8$, and $m_H$ is the mass of the hydrogen atom. $R_{\rm c}$ is the radius of each condensation, given by $R_{\rm c} = \sqrt{R_{eff}^2-(1/4\,\ln{2}){\rm bmaj}\times\,{\rm bmin}}$ (cite: 2014ApJ...790...84L), where the effective radius, $R_{eff}= \sqrt{FWHM_{\rm maj} \times FWHM_{\rm min}}/2$).

Table [2](#tab:filament:calculated) and Table [4](#tab:core) outline the parameters derived above for the fibers and condensations, respectively. The fibers exhibit a length range of $\sim3000$ to $9000$ au, with a median value of $\sim4500$ au. Their width varies from about $\sim1000$ to $2000$ au, with a median of roughly 1400 au. The mass of these fibers spans from 0.66 to 2.72 $M_{\odot}$, with a median of $\sim1.2$ $M_{\odot}$. The line mass ($m_{\rm f}$) extends from 31.4 to 82.0 $M_{\odot}$ ${\rm pc^{-1}}$, with a median of 51.9 $M_{\odot}$ ${\rm pc^{-1}}$. The average number density of fibers varies within a range of $\rm 1.3\times10^7-6.2\times10^7\,cm^{-3}$ with a median of ${\rm 1.8\times10^7\,cm^{-3}}$. As for the condensations, their effective radius and number density have a range of \[180, 410\] au, and \[$7.3\times10^7$, $2.7\times10^9$\]  ${\rm cm^{-3}}$, respectively. The mass of these condensations spans from 0.02 to 1.31 $M_{\odot}$, with a median of 0.11 $M_{\odot}$. These results for condensations are comparable to values derived in other intermediate-mass star-forming regions, such as the condensation mass ranges from 0.1 to 0.4 $M_{\odot}$  in the TUKH122 prestellar core in the Orion A cloud (cite: 2018ApJ...856..147O), and the mass ranges from 0.01 to 0.2 $M_{\odot}$  in the NGC 2071 IR (cite: 2022ApJ...933..178C). It is worth noting here that the derived masses could be underestimated for two likely reasons (1) the assumed average clump temperature of 25 K could be on the higher side for some of the non-YSO bearing condensations and (2) the high-resolution interferometric observations could have filtered out diffuse, low-density emission. Additionally, we cannot rule out over estimation of mass for condensations harboring protostars where temperatures could be as high as 50 K.

### Classification of fertile fibers

As depicted in Fig. [3](#fig:bad6), some fibers accommodate dense condensations, which are likely precursors to star formation. Given their spatial association with condensations, fibers can be classified as “fertile" or “sterile" (cite: 2013A&A...554A..55H; 2015A&A...574A.104T). According to these authors,fertile fibers generally have a higher line mass and contain at least three dense condensations, unlike their sterile counterparts. In the IRS 17 filament, four fibers (namely, f 1 and f 5–7) are classified as fertile, while the rest are considered sterile.

We applied the minimum-spanning tree (MST) method (cite: 1985MNRAS.216...17B; 2016ApJS..226....9W; 2019ApJ...886..102S; 2022MNRAS.510.5009L; 2024ApJS..270....9X) to estimate the separation between condensations within the fertile fibers. The MST approach (e.g. (cite: 2019A&A...629A.135D)) determines the shortest distances that can possibly connect each of the objects in a given field. The estimated separations of condensations in the four fertile fibers range from approximately 850 to 3450 au, with a median of around ${\rm 1600\pm600\,au}$, where the error is the standard deviation of their separations.

## Filament and fibers seen in molecular gas emission

![](H13cop_moment_map.pdf)

Figure [4](#fig:h13co:moment) presents the moment maps of H$^{13}$CO$^{+}$ (1–0) toward the IRS 17 filament observed in 3-mm dust continuum. The H$^{13}$CO$^{+}$ (1–0) line, with a critical density of $\sim\rm 10^{5}\,cm^{-3}$ (cite: 2012ApJ...756...60S), allows us to trace relatively dense gas compared to CO and its isotopologue lines (cite: 2023A&A...672A.133S). The Moment 0 map of H$^{13}$CO$^{+}$ (1–0) reveals that relatively dense gas emission spans the entire filament, except for the region around the intermediate-mass protocluster (see the purple star symbol in Fig. [4](#fig:h13co:moment)) where protostellar feedback is supposed to be strong. In addition, near the protocluster, H$^{13}$CO$^{+}$ (1–0) emission does not cover the full filament footprint.

This could be attributed to the missing flux in the interferometric data or to the clean-up by the outflows with a wide opening angle from the IRS 17 protocluster (see the red-shifted high-velocity CO gas component related to the protocluster in Fig. [9](#fig:outflow)a). As a consequence, though the H$^{13}$CO$^{+}$ emission appears to be primarily distributed south of the crest of the IRS 17 filament, particularly in the southwest region, the morphology and the location of identified fibers indicate that it traces the 3-mm filament.

In the velocity field (Moment 1) map of H$^{13}$CO$^{+}$, the molecular gas shows a coherent velocity distribution along the dust emission filament. Similar to the velocity structure of the filamentary cloud in Taurus, presented in (cite: 2013A&A...554A..55H), multiple velocity components are seen in the IRS 17 filament, ranging from 1.5 to 5.5$\rm \,km\,s^{-1}$ (see H$^{13}$CO$^{+}$ velocity field in Fig [4](#fig:h13co:moment)b), suggesting complex gas structures. Here, these velocity components can also be observed in the velocity map of the DCN line (see Fig. [10](#fig:dcn:moment1)) from the QUARKS survey at higher angular resolution but lower detection rate than the same map of the H$^{13}$CO$^{+}$ line from the ATOMS survey. Additionally, a distinct velocity gradient is also observed along the filament, with increasing velocity centroid from west to east. Despite this complex gas kinematics observed in the filament, the individual identified fibers are seen to be velocity coherent sub-structures (the velocity centroid ranges from 2.3 to 5.3 $\rm\,km\,s^{-1}$, see Col. 5 in Table [2](#tab:filament:calculated)). Furthermore, the detected fibers are seen to be in three bundles with similar kinematics, (1) f 1–2 corresponding to a velocity of $\sim$5.0 $\rm km\,s^{-1}$, (2) f 3–6 with velocity $\sim$3.1 $\rm km\,s^{-1}$, and (3) f 7 with velocity $\sim$2.3 $\rm km\,s^{-1}$.

In Fig. [4](#fig:h13co:moment)c, we present the velocity dispersion (Moment 2) map of H$^{13}$CO$^{+}$ (1–0). Within the IRS 17 dust filament, molecular gas has a median velocity dispersion of $0.39\pm0.25\,\rm km\,s^{-1}$, indicating transonic gas motions compared to the typical thermal sound speed of 0.3 $\rm km\,s^{-1}$ at a temperature of 25 K. The locally enhanced gas motions likely result from local active star formation feedback, including strong ionized gas from the intermediate-mass IRS 17 protocluster (see the purple star symbol in Fig. [4](#fig:h13co:moment)c) and outflows (see the arrows in Fig. [4](#fig:h13co:moment)c) distributed along the filament. Specifically, the northeastern region near the protocluster bears more pronounced supersonic motions due to ionized gas feedback, while several outflows scattered along the filament make local gas motions enhanced. Additionally, several regions outside the filament appear even higher supersonic velocities (i.e., $\rm \sim 1\,km\,s^{-1}$), which deserves further investigation in the future. (cite: 2018A&A...610A..77H) investigated the massive Integral Shape Filament (ISF) in Orion, which experiences more intense star formation feedback. Their observations of the ISF fibers using the $\rm N_2H^+$ (1-0) transition revealed transonic non-thermal velocity dispersions (0.24 km s$^{-1}$ on average) relative to the local temperature. Given this, the velocity dispersion estimated from H$^{13}$CO$^{+}$ (1–0) appears reasonable for the IRS 17 region.

## Stability of the IRS 17 filament and fibers

The gravitational stability of filaments and fibers can be quantitatively evaluated under an ideal model of isothermal and infinite cylinders using the parameter of the critical line mass ($m_{\rm crit}$, (cite: 1963AcA....13...30S; 1964ApJ...140.1056O)). Filaments and fibers with an observed line mass greater than $m_{\rm crit}$ (supercritical) are expected to collapse under their own gravity, while those with an observed line mass less than $m_{\rm crit}$ (subcritical) can maintain a hydrostatic equilibrium or become dispersed.

The $m_{\rm crit}$ parameter can be expressed as follows (cite: 1963AcA....13...30S; 1964ApJ...140.1056O): $$\begin{equation}
\label{eq:cseff:cri}
    m_{\rm crit}=\frac{2\sigma^2_{\rm eff}}{G},
\end{equation}$$ where $G$ represents the gravitational constant and $\sigma_{\rm eff}$ is the effective speed of sound to be considered in varied situations. If we consider only the contribution from thermal motions, the term $\sigma_{\rm eff}$ can be replaced with the thermal sound speed of gas, $c_{\rm s}$, resulting in the thermal critical line mass: $$\begin{equation}
\label{eq:th:cri}
    m_{\rm crit}^{\rm th}=\frac{2c^2_{\rm s}}{G} \sim 16.6(\frac{T}{\rm 10\,K})M_{\odot}\,\rm pc^{-1}\,\rm ,
\end{equation}$$ where $T$ is the kinetic temperature of the gas. Here, we assume it to be the same as the average dust temperature of $T=$ 25 K. This yields $m_{\rm crit}\sim$ 41.5 $M_{\odot}$ $\rm pc^{-1}$. Compared with the observed line mass, the IRS 17 filament and all the fibers except f 2 and f 4 are thermally supercritical (see Table. [2](#tab:filament:calculated)). It is important to note that the assumed average dust temperature of 25 K is relatively high compared to the estimated temperatures of other intermediate-mass protoclusters, such as NGC 1333 ($\sim$10 K; see Table 2 of (cite: 2018A&A...610A..77H)). However, adopting a temperature of 10 K would render fibers f 2 and f 4 supercritical, which contradicts their observed nature since no associated condensations are present (see Fig. [2](#fig:band3:con)). Therefore, accurate temperature measurements will be essential in future studies to resolve this discrepancy.

If we account for the contribution from non-thermal motions to the stability of the IRS 17 fibers, the term $\sigma_{\rm eff}$ can be substituted with the total velocity dispersion, $\sigma_{\rm tot}$, and thus the turbulent critical line mass becomes $$\begin{equation}
\label{eq:tur:cri}
    m_{\rm crit}^{\rm tur}=\frac{2\sigma_{\rm tot}^2}{G} \sim 465(\frac{\sigma_{\rm tot}}{\rm 1\,km\,s^{-1}})^{2}M_{\odot}\,\rm pc^{-1}.
\end{equation}$$ From the H$^{13}$CO$^{+}$ (1–0) line data, we obtained an median velocity dispersion of $\sim 0.39\pm 0.25\,{\rm km\,s^{-1}}$ within the IRS 17 filament (see Table [2](#tab:filament:calculated)). Using this, we estimate a turbulent $m_{\rm crit}^{\rm tur}$ of $70.7\pm 29.1$ $M_{\odot}\,\rm pc^{-1}$. Given the complex velocity field and within the quoted uncertainties, the IRS 17 filament could be supercritical, consistent with the fragementation to fibers hypothesis discussed in Section [4.1](#sub:fiber:star:formation). However, the estimated turbulent $m_{\rm crit}^{\rm tur}$ is significantly greater than the observed line mass of fibers within IRS 17 region (except for f 3, see Col.3 in Table. [2](#tab:filament:calculated)), with a factor of 1.1 to 2.3. This contradicts the observed scenario of gravitational collapse of the fibers and the formation of the detected condensations within them. The discrepancy is likely produced by the ongoing active star formation within IRS 17 filament, where outflows and feedback from ionized gas results in large velocity dispersion. Such high turbulence may not be prevalent during the initial stages of collapse of the small-scale fibers, but is typically close to the sound speed (cite: 2013A&A...554A..55H; 2018A&A...610A..77H). The above discussion finds support in the observed cascade of turbulence with the decreasing scale of the density structures (cite: 1981MNRAS.194..809L; 2023ASPC..534..153H; 2024AJ....167..228L). The $\sigma_{\rm tot}$ follows $\sigma-L$ ($\sigma_{\rm tot}=c_{\rm s}(1+\frac{L}{\rm 0.5\,pc})^{0.5})$, an empirical relation observed by (cite: 2023ASPC..534..153H) for filaments and fibers, which is akin to the first of Larson’s relation for general clouds (cite: 1981MNRAS.194..809L). For the estimated length scale of the IRS 17 fibers, which are significantly less than 0.05 pc ($\sim$ 10000 au), $\sigma_{\rm tot} \sim c_{\rm s}$ making $m_{\rm crit}^{\rm tur} \sim m_{\rm crit}^{\rm th}$. Thus, for the length scale of the IRS 17 fibers, the role of turbulence would be negligible. Summarizing the stability analysis, except f 2 and f 4, the other IRS 17 fibers are observed to be supercritical consistent with the presence of dense condensations within them. However, we should note that the $\sigma-L$ has uncertainties of $\pm0.2\,\rm pc$ and $\pm0.2$ for the length ($L$) and exponent, respectively (cite: 2023ASPC..534..153H).

Note that magnetic fields could potentially have a considerable impact on the stability of the fibers. However, our analysis above ignores the magnetic fields, as such information is not available.

![](virial_parameters.pdf)

## Stability of condensations

The stability of condensations can be evaluated by the virial parameter ($\alpha_{\rm vir
}$) as below (cite: 1992ApJ...395..140B): $$\begin{equation}
    \alpha_{\rm vir}=\frac{5\sigma_{\rm eff}^2R_{c}}{\rm G{\it M_{\rm c}}}\,,
\end{equation}$$ where $R_{\rm c}$ is the condensation radius. The subvirial cores with $\alpha_{\rm vir}\leq2$ will collapse to form stars (cite: 2022MNRAS.510.5009L). For the stability analysis of the condensations, one needs to include the contribution from turbulence in the $\sigma_{\rm eff}$ term. However, we lack molecular line data (e.g., $\rm N_2H^+$ (1–0)) at matching angular resolution. Moreover, if IRS 17 fibers exhibit transonic turbulent motions similar to the OrionA ISF fibers as reported by (cite: 2018A&A...610A..77H) using $\rm N_2H^+$ observations, the impact of turbulence on the stability of smaller-scale condensations will become negligible. This is consistent with $\sigma - L$ scaling (see Section [3.4](#subsub:instability)), where the effect of turbulence would be negligible for the length scales of these sub-structures. Hence, we consider only the thermal motion and replace $\sigma_{\rm eff}$ by the sound speed of gas, $c_{\rm s}$. Assuming the same $c_{\rm s}$ value (i.e., $0.3\,\rm km\,s^{-1}$) for all condensations in the IRS 17 filament at a temperature of 25 K, we find most (25 of 30, $83\,\%$) of them with $\alpha_{\rm vir}\leq 2$, with a median value of 1.1 (see Fig. [5](#fig:vir)). This implies that most of identified condensations within the IRS 17 region are gravitationally bound and will undergo collapse unless supported by magnetic field. Moreover, two of the condensations (C5 and C21) are associated with the Class I/0 YSOs (see Fig. [3](#fig:bad6)), and additional seven (i.e., C2, C10, C13, C16, C17, C25 and C26) are associated with outflows identified from the SiO and CO line transitions (see Fig. [9](#fig:outflow)). The association of these YSOs and outflows lends strong support to our understanding that these condensations are potential seeds of star formation. It is worth noting that, as mentioned in Section [3.2.1](#subsub:sec:fibers and condensation), the condensations without YSO associated could have lower temperatures possibly down to 10K, while those with YSO associated could have higher temperature possible up to 50 K. The former case will make the virial parameters about 6 times lower than the current values, and thus does not change the subvirial state of those condensations without YSOs; the latter case will make the virial parameters about 4 times higher, and accordingly make the dynamical state of those condensations with YSOs change to be supervirial.

A point that solicits further discussion is the low masses of the identified condensations (see Table [4](#tab:core)). Notwithstanding the issue of assuming a higher dust temperature or factoring in the missing flux of the interferometric observations, for the non-YSO bearing and non-outflow hosting condensations, the estimated masses are similar to those derived for the protostars in NGC 2071 IR by (cite: 2022ApJ...933..178C) using 1.3 mm ALMA observations. As pointed out by these authors, these could be treated as lower limits, since the emission from the protostars could be partially optically thick at 1.3 mm. Furthermore, with the sensitivity and the resolution of the observed data, these detected supercritical ($\alpha_{\rm vir}\leq 2$) condensations could be just the central cores of Bonnor–Ebert spheres that have steep density profiles (cite: 2018ApJ...856..147O). However, one cannot rule out the formation of very low-mass objects from these condensations. The condensations associated with YSOs and outflows, on the other hand, might be undergoing a dynamical process of star formation, as described in various dynamical models of star formation (e.g., (cite: 2019MNRAS.490.3061V; 2020ApJ...900...82P)). For instance, the inertial inflow model proposed by (cite: 2020ApJ...900...82P) outlines star formation as a three-step dynamical process: (1) the formation of a gravitationally unstable core, (2) the collapse of this core into a low to intermediate-mass star, and (3) the subsequent accretion of the remaining mass from the natal core onto the star. An exception is the condensation C21, where the estimated mass is too low ($0.02\pm0.01$ $M_{\odot}$ ) to explain the signature of star formation therein. Given the weak 1.3 mm emission observed, it is highly likely that we are detecting only the peak emission from the central region.

+:------+:---------------:+:---------------:+:----------------------------:+:---------------------------:+:-----------------------:+:-----------------------:+
| Fiber | *          Position          *    | $\langle n_0\rangle^a$       | $\rm <\lambda_{\rm pro}>^b$ | H                       | $\lambda_{\rm max}$     |
+-------+-----------------+-----------------+------------------------------+-----------------------------+-------------------------+-------------------------+
|       | $\alpha$(J2000) | $\delta$(J2000) | $(\rm \times10^8\, cm^{-3})$ | $(\rm \times 10^3\,au)$     | $(\rm \times 10^2\,au)$ | $(\rm \times 10^3\,au)$ |
+-------+-----------------+-----------------+------------------------------+-----------------------------+-------------------------+-------------------------+
| f1    | 08:46:35.12     | -43:54:23.44    | $2.18\pm0.34$                | $2.3\pm0.4$                 | $0.7\pm0.1$             | $1.8\pm0.1$             |
+-------+-----------------+-----------------+------------------------------+-----------------------------+-------------------------+-------------------------+
| f5    | 08:46:33.49     | -43:54:34.66    | $3.18\pm0.63$                | $1.9\pm1.0$                 | $0.6\pm0.1$             | $1.2\pm0.2$             |
+-------+-----------------+-----------------+------------------------------+-----------------------------+-------------------------+-------------------------+
| f6    | 08:46:33.40     | -43:54:38.20    | $8.97\pm1.42$                | $0.9\pm0.2$                 | $0.3\pm0.1$             | $0.7\pm0.1$             |
+-------+-----------------+-----------------+------------------------------+-----------------------------+-------------------------+-------------------------+
| f7    | 08:46:32.69     | -43:54:36.17    | $2.21\pm0.34$                | $1.7\pm0.2$                 | $0.7\pm0.1$             | $1.5\pm0.3$             |
+-------+-----------------+-----------------+------------------------------+-----------------------------+-------------------------+-------------------------+

: Derived parameters of fibers

## Fragmentation of fibers

Theoretically, semi-analytic linear cylinder fragmentation models, such as the “sausage” instability model (cite: 1987PThPh..77..635N; 2010ApJ...719L.185J), are commonly used to investigate the fragmentation of filamentary structures. The premise of these theoretical models is that the fragmentation of a self-gravitating fluid cylinder can lead to chains of dense cores with nearly periodic separations . This separation corresponds to the characteristic wavelength ($\lambda_{\rm crit}$) where the instability grows most rapidly. For an incompressible fluid, perturbation analysis indicates that the critical wavelength emerges at $\lambda_{\rm crit} =  11 R_{\rm cyl}$, where $R_{\rm cyl}$ is the cylinder’s radius . In the context of an infinite isothermal gas cylinder, the characteristic wavelength becomes $\lambda_{\rm crit} = 22 H$, where $H = c_{\rm s} (4\pi G \rho_{\rm c})^{-1/2}$ represents the isothermal scale height and $\rho_{\rm c}$ is the central mass density along the cylinder’s axis . For a finite isothermal gas cylinder surrounded by a uniform medium, the value of $\lambda_{\rm crit}$ is influenced by the $R_{\rm cyl}/H$ ratio. If $R_{\rm cyl}/H \gg 1$, the characteristic separation approximates $\lambda_{\rm crit} = 22 H$, aligning with the infinite isothermal gas cylinder model. However, if $R_{\rm cyl}/H \ll 1$, it shifts to $\lambda_{\rm crit} = 11 R_{\rm cyl}$, which corresponds to the incompressible case .

For the IRS 17 filament, we observe no chain of dense cores with a characteristic periodic separation. This suggests that the IRS 17 filament fragmentation into dense cores does not conform to predictions of a simple linear cylinder model. In comparison, predictions of the model as patterns of periodically-spaced dense condensations are evident in the fertile fibers (i.e., f 1, and f 5–7) within the filament. Hence, assuming the fibers as isothermal and hydrostatic gas cylinders, we take the average volume density of condensations (refer to Col.4 in Table. [3](#tab:fibers)) within each fiber as its central density ($\rho_{\rm c}$). This allows us to estimate the isothermal scale height for the fibers, yielding $H\sim60\,\rm au$ at a temperature of 25 K. The median radius of the fertile fibers is $\sim$700 au ($1/2\,\times W_{\rm f}$), which corresponds to the case of $R\gg H$. Hence, the separation of dense condensations within fibers can be predicted from $\lambda_{\rm max}=22H$. Consequently, the predicted $\lambda_{\rm max}$ for the four fertile fibers ranges from $700-1800\,\rm au$ (see Col. 7 in table [3](#tab:fibers)). This agrees with the observed typical separation between dense condensations within fertile fibers of $\sim 900-2300\rm\,au$ (see Col.5  in table [3](#tab:fibers)).

# Discussion

## Role of fibers in star formation

![](cylinder_model.pdf)

Since their discovery (cite: 2013A&A...554A..55H), subparsec-scale fibers have been reported across varied star-forming regions, including low-mass clouds (cite: 2013A&A...553A.119A; 2016A&A...590A..75F), intermediate-mass clusters (cite: 2014ApJ...790L..19F; 2017A&A...606A.123H), and high-mass star-forming regions (cite: 2018A&A...610A..77H; 2019A&A...629A..81T; 2022ApJ...926..165L). In good agreement with observations, hydrodynamical simulations of turbulent clouds reveal the natural occurrence of network of fibers within filaments (cite: 2014MNRAS.445.2900S; 2016MNRAS.455.3640S). Furthermore, in most regions, the population of observed cores are seen to be predominantly harboured in these fibers, thus highlighting the key role played by these dominant sub-structures in star formation across the mass spectrum. Such a scenario is discerned in the IRS 17 filament, with the observed association between fibers and dense condensations (potential seeds of star formation). A systematic analysis of the internal fibers of the massive Orion-ISF filament and lower-mass objects (e.g., Musca, Taurus) led (cite: 2018A&A...610A..77H) to propose a unified star formation paradigm. In this framework, the observed differences between low- and high-mass clouds naturally emerge from the initial concentration of fibers.

Fibers are proposed to play a critical role in star formation. (cite: 2013A&A...554A..55H) and (cite: 2015A&A...574A.104T) based on their observations of L1495/B213 filamentary complex in Taurus, infer a hierarchical fragmentation process termed ‘fray and fragment’, where the filamentary clouds first fragment to fibers (sub-filaments) which further fragment to dense cores. The above scenario of the impact of fibers on the fragmentation of filaments finds strong support in the numerical study discussed in (cite: 2020MNRAS.497.4390C).

As shown by these authors, in contrast to the classical filament fragmentation models, the presence of fibers as the intermediate fragmentation stage results in the absence of a strong imprint of quasi-periodic cores in filaments.

The above picture is aptly captured in the cartoon presented in Fig. [6](#fig:sheet:cylinder:model), which explains the observed features in the IRS 17 filament. As discussed in Section [3.3](#sub:fil:fib:gas), the IRS 17 filament presents multiple velocity components, consistent with the three bundles of velocity-coherent fibers identified. The detected cores are randomly spaced in the large-scale filament. This is in good agreement with recent dynamic models using numerical simulations that consider accretion, turbulence, and magnetic fields to interpret the observed randomly-distributed core spacings (cite: 2015MNRAS.452.2410S; 2016MNRAS.458..319C; 2017MNRAS.468.2489C; 2020MNRAS.497.4390C; 2017ApJ...834..202G). However, the signature of periodic core-spacing is observed in a few of the detected velocity-coherent, fertile fibers in IRS 17 filament. Not consistent with the above picture of hierarchical fragmentation, are the hydrodynamical simulations by (cite: 2014MNRAS.445.2900S; 2016MNRAS.455.3640S). These authors propose a ‘bottom-up’ model, where fibers pre-exist in clouds, formed as a natural outcome of a turbulent cascade. Subsequently, these fibers are swept together to form the large-filaments as a consequence of the large-scale gravity-driven collapse of the cloud. The differing views advocate for further such studies of filamentary clouds at higher resolution and sensitivity for a better insight into the formation and role of fibers in star formation.

# Summary

We have investigated the internal structure of the IRS 17 filament in the intermediate mass protocluster, IRAS 08448-4343, using both 3 mm and 1.3 mm ALMA data from the ATOMS and QUARKS survey, respectively. Our study has illustrated the role of small-scale fibers in star formation. Our major results are as follows:

A sub-parsec filament ($\sim$0.26 pc), referred to as the IRS 17 filament, is seen in 3 mm continuum emission within the IRS 17 protocluster region. The gas kinematics of this filament presents a complex and multi-component field.

Within the apparent IRS 17 filament, three bundles of seven velocity-coherent fibers and twenty-nine dense condensations were revealed from the QUARKS 1.3 mm continuum map. The fibers have a median length of $\sim 4500\,\rm au$ and a median width of $\sim 1400\,\rm au$ with a line mass of 51.9 $M_{\odot}$$\rm ~pc^{-1}$. We identified four fertile fibers, each hosting three or more condensations, based on the association between condensations and fibers. Some condensations are linked to ongoing star formation signatures, such as YSOs and outflows, while most are subvirial. These findings suggest that the majority of condensations could potentially seed star formation.

Furthermore, periodic spacings of condensations are observed in the fertile fibers, which agrees with linear isothermal cylinder fragmentation models. However, this periodic pattern is not observed for the detected 3 mm cores in the larger-scale IRS 17 filament. This reflects the crucial role of fibers on the fragmentation of the filament into cores. In other words, there may be an intermediate fragmentation step, involving the formation of fibers, before core formation out of the IRS 17 filament. This step leaves no strong imprint of quasi-periodic fragmentation of filaments into cores.

# Acknowledgements

We thank the referee for the valuable comments and suggestions that greatly improved the quality of this paper. This work has been supported by the National Key R&D Program of China (No. 2022YFA1603101). H.-L. Liu is supported by National Natural Science Foundation of China (NSFC) through the grant No.12103045, and by Yunnan Fundamental Research Project (grant No. 202301AT070118, 202401AS070121). T. Liu acknowledges the supports by NSFC through grants No.12073061 and No.12122307; and X. Liu has also been supported by CPSF No. 2022M723278; S.-L. Qin is supported by NSFC under No.12033005. G.G. gratefully acknowledges support by the ANID BASAL project FB210003. PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP22H01271 and JP23H01221) of JSPS, and by Yoshinori Ohsumi Fund (Yoshinori Ohsumi Award for Fundamental Research). This work was performed in part at the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration (80NM0018D0004). SRD acknowledges support from the Fondecyt Postdoctoral fellowship (project code 3220162) and ANID BASAL project FB210003. This work was partly supported by Yunnan Xingdian Talent Support Plan–Youth Project. LB gratefully acknowledges support by the ANID BASAL project FB210003. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00685.S, 2021.1.00095.S and 2023.1.00425.

# Complementary figures and tables

![](band3_band6_continuum.pdf)

![](band6_continuum_zoomin.pdf)

![](outflow.pdf)

![](DCN_moment_1.pdf)

+:-------------+:---------------:+:---------------:+:-------------------:+:-------------------:+:-------------------:+:---------------------------:+:----------------------------:+:-----------:+:-------------:+:----------------------------:+
| Condensation | *          Position          *    | $FWHM_{\rm maj}$    | $FWHM_{\rm min}$    | PA                  | $S^{\rm int}_{\rm 1.3\,mm}$ | $F^{\rm peak}_{\rm 1.3\,mm}$ | $R_{\rm c}$ | $M_{\rm c}$   | $n_{\rm c}$                  |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
|              | $\alpha$(J2000) | $\delta$(J2000) | $(\ensuremath{''})$ | $(\ensuremath{''})$ | $(\hbox{$^\circ$})$ | $\rm (mJy)$                 | $\rm (mJy~beam^{-1})$        | $\rm (au)$  | ($M_{\odot}$) | $(\rm \times 10^8\,cm^{-3})$ |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| $\rm C1^*$   | 08:46:35.24     | -43:54:23.41    | 0.83                | 0.35                | 164.7               | $3.0\pm0.3$                 | $1.2\pm0.1$                  | 222.8       | $0.08\pm0.01$ | $2.19\pm0.35$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C2           | 08:46:35.13     | -43:54:24.32    | 0.77                | 0.64                | 42.4                | $6.2\pm0.3$                 | $1.3\pm0.2$                  | 353.4       | $0.16\pm0.02$ | $1.1\pm0.18$                 |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C3           | 08:46:34.94     | -43:54:23.68    | 0.36                | 0.33                | 36.0                | $4.0\pm0.2$                 | $2.9\pm0.2$                  | 210.3       | $0.10\pm0.01$ | $3.26\pm0.52$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C4           | 08:46:34.90     | -43:54:26.78    | 0.37                | 0.33                | 102.2               | $3.7\pm0.2$                 | $2.8\pm0.2$                  | 213.2       | $0.09\pm0.01$ | $2.81\pm0.44$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C5           | 08:46:34.85     | -43:54:30.15    | 0.33                | 0.33                | 69.8                | $11.4\pm0.1$                | $9.4\pm0.1$                  | 201.3       | $0.29\pm0.04$ | $10.76\pm1.71$               |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C6           | 08:46:34.79     | -43:54:30.52    | 0.33                | 0.29                | 175.5               | $0.6\pm0.1$                 | $0.6\pm0.1$                  | 188.7       | $0.02\pm0.01$ | $0.90\pm0.18$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C7           | 08:46:34.63     | -43:54:32.50    | 0.88                | 0.70                | 102.9               | $6.7\pm0.2$                 | $1.1\pm0.1$                  | 413.2       | $0.17\pm0.02$ | $0.73\pm0.08$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C8           | 08:46:34.32     | -43:54:39.61    | 0.44                | 0.34                | 98.9                | $6.1\pm0.1$                 | $3.2\pm0.1$                  | 235.9       | $0.15\pm0.02$ | $3.46\pm0.44$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C9           | 08:46:33.74     | -43:54:34.32    | 0.42                | 0.34                | 30.0                | $4.1\pm0.1$                 | $2.4\pm0.1$                  | 230.5       | $0.10\pm0.01$ | $2.47\pm0.39$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C10          | 08:46:33.65     | -43:54:34.71    | 0.37                | 0.33                | 56.7                | $4.5\pm0.1$                 | $3.1\pm0.1$                  | 213.2       | $0.11\pm0.02$ | $3.44\pm0.55$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C11          | 08:46:33.57     | -43:54:34.99    | 0.44                | 0.35                | 83.4                | $3.8\pm0.2$                 | $2.1\pm0.2$                  | 239.4       | $0.10\pm0.1$  | $2.21\pm0.35$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C12          | 08:46:33.45     | -43:54:37.11    | 0.51                | 0.38                | 62.0                | $7.0\pm0.2$                 | $3.5\pm0.2$                  | 268.5       | $0.18\pm0.2$  | $2.82\pm0.45$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C13          | 08:46:33.38     | -43:54:37.44    | 0.54                | 0.45                | 34.3                | $19.5\pm0.3$                | $7.7\pm0.3$                  | 178.8       | $0.49\pm0.07$ | $25.95\pm4.13$               |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C14          | 08:46:33.37     | -43:54:38.20    | 0.53                | 0.49                | 119.9               | $4.1\pm0.2$                 | $1.7\pm0.2$                  | 195.4       | $0.10\pm0.01$ | $4.06\pm0.59$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C15          | 08:46:33.32     | -43:54:38.63    | 0.43                | 0.38                | 68.0                | $6.0\pm0.2$                 | $3.4\pm0.2$                  | 246.6       | $0.15\pm0.2$  | $3.03\pm0.48$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C16          | 08:46:33.31     | -43:54:34.67    | 0.38                | 0.34                | 60.8                | $6.2\pm0.2$                 | $4.2\pm0.2$                  | 219.3       | $0.16\pm0.02$ | $4.59\pm0.73$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C17          | 08:46:32.97     | -43:54:34.83    | 0.39                | 0.37                | 106.7               | $4.6\pm0.2$                 | $2.9\pm0.2$                  | 231.7       | $0.12\pm0.02$ | $2.92\pm0.46$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| $\rm C18^*$  | 08:46:32.82     | -43:54:35.07    | 0.45                | 0.19                | 103.8               | $1.1\pm0.1$                 | $1.0\pm0.1$                  | 178.4       | $0.03\pm0.01$ | $1.60\pm0.25$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| $\rm C19^*$  | 08:46:32.77     | -43:54:36.09    | 0.61                | 0.31                | 29.6                | $2.8\pm0.3$                 | $1.0\pm0.1$                  | 265.3       | $0.07\pm0.01$ | $1.13\pm0.18$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C20          | 08:46:32.75     | -43:54:39.57    | 0.34                | 0.32                | 98.4                | $1.1\pm0.2$                 | $0.9\pm0.2$                  | 201.2       | $0.03\pm0.01$ | $1.12\pm0.22$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C21          | 08:46:32.72     | -43:54:40.88    | 0.34                | 0.27                | 76.2                | $0.8\pm0.1$                 | $0.7\pm0.1$                  | 184.8       | $0.02\pm0.01$ | $0.96\pm0.15$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| $\rm C22^*$  | 08:46:32.64     | -43:54:35.42    | 0.64                | 0.43                | 58.7                | $4.5\pm0.5$                 | $1.1\pm0.1$                  | 209.6       | $0.11\pm0.02$ | $3.62\pm0.57$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| $\rm C23^*$  | 08:46:32.62     | -43:54:36.75    | 1.15                | 0.31                | 32.8                | $6.4\pm0.6$                 | $1.7\pm0.2$                  | 272.4       | $0.16\pm0.03$ | $2.40\pm0.38$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| $\rm C24^*$  | 08:46:32.50     | -43:54:37.17    | 0.73                | 0.32                | 108.5               | $5.2\pm0.5$                 | $2.4\pm0.2$                  | 294.8       | $0.13\pm0.02$ | $1.54\pm0.24$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C25          | 08:46:32.32     | -43:54:36.90    | 0.41                | 0.39                | 179.0               | $51.7\pm0.4$                | $26.2\pm0.2$                 | 243.9       | $1.31\pm0.18$ | $27.34\pm4.33$               |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C26          | 08:46:32.22     | -43:54:41.06    | 0.5                 | 0.43                | 109.8               | $4.5\pm0.2$                 | $1.7\pm0.1$                  | 282.8       | $0.11\pm0.02$ | $1.47\pm0.23$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C27          | 08:46:32.13     | -43:54:41.72    | 0.34                | 0.33                | 121.0               | $3.2\pm0.1$                 | $2.6\pm0.1$                  | 204.3       | $0.08\pm0.01$ | $2.84\pm0.45$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C28          | 08:46:31.99     | -43:54:40.20    | 0.38                | 0.37                | 119.4               | $4.2\pm0.2$                 | $2.7\pm0.2$                  | 228.7       | $0.11\pm0.01$ | $2.78\pm0.44$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C29          | 08:46:31.80     | -43:54:36.07    | 0.43                | 0.37                | 77.5                | $6.6\pm0.1$                 | $3.4\pm0.1$                  | 243.3       | $0.17\pm0.02$ | $3.57\pm0.57$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+
| C30          | 08:46:31.17     | -43:54:36.57    | 0.37                | 0.34                | 124.1               | $8.8\pm0.2$                 | $6.2\pm0.1$                  | 216.4       | $0.22\pm0.03$ | $6.57\pm1.04$                |
+--------------+-----------------+-----------------+---------------------+---------------------+---------------------+-----------------------------+------------------------------+-------------+---------------+------------------------------+

: Physical parameters of 1.3 mm condensations

natexlab

(ref: 2007ASSP....3..417A) Alves, J., Lombardi, M., & Lada, C. 2007, in Astrophysics and Space Science Proceedings, Vol. 3, Island Universes, 417, doi: [`10.1007/978-1-4020-5573-7_72`](http://doi.org/10.1007/978-1-4020-5573-7_72)

(ref: 2019A&A...629L...4A) André, P., Arzoumanian, D., Könyves, V., Shimajiri, Y., & Palmeirim, P. 2019, A&A, 629, L4, doi: [`10.1051/0004-6361/201935915`](http://doi.org/10.1051/0004-6361/201935915)

(ref: 2007A&A...472..519A) André, P., Belloche, A., Motte, F., & Peretto, N. 2007, A&A, 472, 519, doi: [`10.1051/0004-6361:20077422`](http://doi.org/10.1051/0004-6361:20077422)

(ref: 2014prpl.conf...27A) André, P., Di Francesco, J., Ward-Thompson, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 27–51, doi: [`10.2458/azu_uapress_9780816531240-ch002`](http://doi.org/10.2458/azu_uapress_9780816531240-ch002)

(ref: 2010A&A...518L.102A) André, P., Men’shchikov, A., Bontemps, S., et al. 2010, A&A, 518, L102, doi: [`10.1051/0004-6361/201014666`](http://doi.org/10.1051/0004-6361/201014666)

(ref: 2013A&A...553A.119A) Arzoumanian, D., André, P., Peretto, N., & Könyves, V. 2013, A&A, 553, A119, doi: [`10.1051/0004-6361/201220822`](http://doi.org/10.1051/0004-6361/201220822)

(ref: 2019A&A...621A..42A) Arzoumanian, D., André, P., Könyves, V., et al. 2019, A&A, 621, A42, doi: [`10.1051/0004-6361/201832725`](http://doi.org/10.1051/0004-6361/201832725)

(ref: 2016zndo....804967B) Barbary, K. 2016, extinction v0.3.0, Zenodo, doi: [`10.5281/zenodo.804967`](http://doi.org/10.5281/zenodo.804967)

(ref: 1985MNRAS.216...17B) Barrow, J. D., Bhavsar, S. P., & Sonoda, D. H. 1985, MNRAS, 216, 17, doi: [`10.1093/mnras/216.1.17`](http://doi.org/10.1093/mnras/216.1.17)

(ref: 1996A&AS..117..393B) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: 1992ApJ...395..140B) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140, doi: [`10.1086/171638`](http://doi.org/10.1086/171638)

(ref: 2022ApJ...927..106C) Cao, Y., Qiu, K., Zhang, Q., & Li, G.-X. 2022, ApJ, 927, 106, doi: [`10.3847/1538-4357/ac4696`](http://doi.org/10.3847/1538-4357/ac4696)

(ref: 1953ApJ...118..116C) Chandrasekhar, S., & Fermi, E. 1953, ApJ, 118, 116, doi: [`10.1086/145732`](http://doi.org/10.1086/145732)

(ref: 2022ApJ...933..178C) Cheng, Y., Tobin, J. J., Yang, Y.-L., et al. 2022, ApJ, 933, 178, doi: [`10.3847/1538-4357/ac7464`](http://doi.org/10.3847/1538-4357/ac7464)

(ref: 2023ApJ...951...68C) Chung, E. J., Lee, C. W., Kwon, W., et al. 2023, ApJ, 951, 68, doi: [`10.3847/1538-4357/acd540`](http://doi.org/10.3847/1538-4357/acd540)

(ref: 2017MNRAS.468.2489C) Clarke, S. D., Whitworth, A. P., Duarte-Cabral, A., & Hubber, D. A. 2017, MNRAS, 468, 2489, doi: [`10.1093/mnras/stx637`](http://doi.org/10.1093/mnras/stx637)

(ref: 2016MNRAS.458..319C) Clarke, S. D., Whitworth, A. P., & Hubber, D. A. 2016, MNRAS, 458, 319, doi: [`10.1093/mnras/stw407`](http://doi.org/10.1093/mnras/stw407)

(ref: 2020MNRAS.497.4390C) Clarke, S. D., Williams, G. M., & Walch, S. 2020, MNRAS, 497, 4390, doi: [`10.1093/mnras/staa2298`](http://doi.org/10.1093/mnras/staa2298)

(ref: 2013A&A...549A..45C) Contreras, Y., Schuller, F., Urquhart, J. S., et al. 2013, A&A, 549, A45, doi: [`10.1051/0004-6361/201220155`](http://doi.org/10.1051/0004-6361/201220155)

(ref: 2016A&A...590A.110C) Cox, N. L. J., Arzoumanian, D., André, P., et al. 2016, A&A, 590, A110, doi: [`10.1051/0004-6361/201527068`](http://doi.org/10.1051/0004-6361/201527068)

(ref: 2024MNRAS.527.5895D) Dewangan, L. K., Bhadari, N. K., Maity, A. K., et al. 2024, MNRAS, 527, 5895, doi: [`10.1093/mnras/stad3384`](http://doi.org/10.1093/mnras/stad3384)

(ref: 2019A&A...629A.135D) Dib, S., & Henning, T. 2019, A&A, 629, A135, doi: [`10.1051/0004-6361/201834080`](http://doi.org/10.1051/0004-6361/201834080)

(ref: 2004A&A...426...97F) Faúndez, S., Bronfman, L., Garay, G., et al. 2004, A&A, 426, 97, doi: [`10.1051/0004-6361:20035755`](http://doi.org/10.1051/0004-6361:20035755)

(ref: 2016A&A...590A..75F) Fehér, O., Tóth, L. V., Ward-Thompson, D., et al. 2016, A&A, 590, A75, doi: [`10.1051/0004-6361/201424385`](http://doi.org/10.1051/0004-6361/201424385)

(ref: 2014ApJ...790L..19F) Fernández-López, M., Arce, H. G., Looney, L., et al. 2014, ApJL, 790, L19, doi: [`10.1088/2041-8205/790/2/L19`](http://doi.org/10.1088/2041-8205/790/2/L19)

(ref: 2005A&A...433..941G) Giannini, T., Massi, F., Podio, L., et al. 2005, A&A, 433, 941, doi: [`10.1051/0004-6361:20041959`](http://doi.org/10.1051/0004-6361:20041959)

(ref: 2024MNRAS.531..649G) Goedhart, S., Cotton, W. D., Camilo, F., et al. 2024, MNRAS, 531, 649, doi: [`10.1093/mnras/stae1166`](http://doi.org/10.1093/mnras/stae1166)

(ref: 2017ApJ...834..202G) Gritschneder, M., Heigl, S., & Burkert, A. 2017, ApJ, 834, 202, doi: [`10.3847/1538-4357/834/2/202`](http://doi.org/10.3847/1538-4357/834/2/202)

(ref: 2023ASPC..534..153H) Hacar, A., Clark, S. E., Heitsch, F., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 153, doi: [`10.48550/arXiv.2203.09562`](http://doi.org/10.48550/arXiv.2203.09562)

(ref: 2017A&A...606A.123H) Hacar, A., Tafalla, M., & Alves, J. 2017, A&A, 606, A123, doi: [`10.1051/0004-6361/201630348`](http://doi.org/10.1051/0004-6361/201630348)

(ref: 2018A&A...610A..77H) Hacar, A., Tafalla, M., Forbrich, J., et al. 2018, A&A, 610, A77, doi: [`10.1051/0004-6361/201731894`](http://doi.org/10.1051/0004-6361/201731894)

(ref: 2013A&A...554A..55H) Hacar, A., Tafalla, M., Kauffmann, J., & Kovács, A. 2013, A&A, 554, A55, doi: [`10.1051/0004-6361/201220090`](http://doi.org/10.1051/0004-6361/201220090)

(ref: 1992ApJ...388..392I) Inutsuka, S.-I., & Miyama, S. M. 1992, ApJ, 388, 392, doi: [`10.1086/171162`](http://doi.org/10.1086/171162)

(ref: 2010ApJ...719L.185J) Jackson, J. M., Finn, S. C., Chambers, E. T., Rathborne, J. M., & Simon, R. 2010, ApJL, 719, L185, doi: [`10.1088/2041-8205/719/2/L185`](http://doi.org/10.1088/2041-8205/719/2/L185)

(ref: 2017A&A...600A.141K) Kainulainen, J., Stutz, A. M., Stanke, T., et al. 2017, A&A, 600, A141, doi: [`10.1051/0004-6361/201628481`](http://doi.org/10.1051/0004-6361/201628481)

(ref: 2010A&A...518L.106K) Könyves, V., André, P., Men’shchikov, A., et al. 2010, A&A, 518, L106, doi: [`10.1051/0004-6361/201014689`](http://doi.org/10.1051/0004-6361/201014689)

(ref: 2020A&A...635A..34K) Könyves, V., André, P., Arzoumanian, D., et al. 2020, A&A, 635, A34, doi: [`10.1051/0004-6361/201834753`](http://doi.org/10.1051/0004-6361/201834753)

(ref: 1981MNRAS.194..809L) Larson, R. B. 1981, MNRAS, 194, 809, doi: [`10.1093/mnras/194.4.809`](http://doi.org/10.1093/mnras/194.4.809)

(ref: 2022ApJ...926..165L) Li, S., Sanhueza, P., Lee, C. W., et al. 2022, ApJ, 926, 165, doi: [`10.3847/1538-4357/ac3df8`](http://doi.org/10.3847/1538-4357/ac3df8)

(ref: 1992A&A...265..577L) Liseau, R., Lorenzetti, D., Nisini, B., Spinoglio, L., & Moneti, A. 1992, A&A, 265, 577

(ref: 2018MNRAS.478.2119L) Liu, H.-L., Stutz, A., & Yuan, J.-H. 2018, MNRAS, 478, 2119, doi: [`10.1093/mnras/sty1270`](http://doi.org/10.1093/mnras/sty1270)

(ref: 2019MNRAS.487.1259L) —. 2019, MNRAS, 487, 1259, doi: [`10.1093/mnras/stz1340`](http://doi.org/10.1093/mnras/stz1340)

(ref: 2021MNRAS.505.2801L) Liu, H.-L., Liu, T., Evans, Neal J., I., et al. 2021, MNRAS, 505, 2801, doi: [`10.1093/mnras/stab1352`](http://doi.org/10.1093/mnras/stab1352)

(ref: 2022MNRAS.510.5009L) Liu, H.-L., Tej, A., Liu, T., et al. 2022a, MNRAS, 510, 5009, doi: [`10.1093/mnras/stab2757`](http://doi.org/10.1093/mnras/stab2757)

(ref: 2022MNRAS.511.4480L) —. 2022b, MNRAS, 511, 4480, doi: [`10.1093/mnras/stac378`](http://doi.org/10.1093/mnras/stac378)

(ref: 2023MNRAS.522.3719L) —. 2023, MNRAS, 522, 3719, doi: [`10.1093/mnras/stad047`](http://doi.org/10.1093/mnras/stad047)

(ref: 2020MNRAS.496.2790L) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020a, MNRAS, 496, 2790, doi: [`10.1093/mnras/staa1577`](http://doi.org/10.1093/mnras/staa1577)

(ref: 2020MNRAS.496.2821L) —. 2020b, MNRAS, 496, 2821, doi: [`10.1093/mnras/staa1501`](http://doi.org/10.1093/mnras/staa1501)

(ref: 2024RAA....24b5009L) Liu, X., Liu, T., Zhu, L., et al. 2024, Research in Astronomy and Astrophysics, 24, 025009, doi: [`10.1088/1674-4527/ad0d5c`](http://doi.org/10.1088/1674-4527/ad0d5c)

(ref: 2002ApJ...564..839L) Lorenzetti, D., Giannini, T., Vitali, F., Massi, F., & Nisini, B. 2002, ApJ, 564, 839, doi: [`10.1086/324305`](http://doi.org/10.1086/324305)

(ref: 2024arXiv240718719L) Louvet, F., Sanhueza, P., Stutz, A., et al. 2024, arXiv e-prints, arXiv:2407.18719, doi: [`10.48550/arXiv.2407.18719`](http://doi.org/10.48550/arXiv.2407.18719)

(ref: 2014ApJ...790...84L) Lu, X., Zhang, Q., Liu, H. B., Wang, J., & Gu, Q. 2014, ApJ, 790, 84, doi: [`10.1088/0004-637X/790/2/84`](http://doi.org/10.1088/0004-637X/790/2/84)

(ref: 2024AJ....167..228L) Luo, A.-X., Liu, H.-L., Qin, S.-L., Yang, D.-t., & Pan, S. 2024, AJ, 167, 228, doi: [`10.3847/1538-3881/ad35ca`](http://doi.org/10.3847/1538-3881/ad35ca)

(ref: 2024ApJ...961L..35M) Mai, X., Liu, T., Liu, X., et al. 2024, ApJL, 961, L35, doi: [`10.3847/2041-8213/ad19c3`](http://doi.org/10.3847/2041-8213/ad19c3)

(ref: 1999A&AS..136..471M) Massi, F., Giannini, T., Lorenzetti, D., et al. 1999, A&AS, 136, 471, doi: [`10.1051/aas:1999471`](http://doi.org/10.1051/aas:1999471)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2021A&A...649A..89M) Men’shchikov, A. 2021, A&A, 649, A89, doi: [`10.1051/0004-6361/202039913`](http://doi.org/10.1051/0004-6361/202039913)

(ref: 2010A&A...518L.100M) Molinari, S., Swinyard, B., Bally, J., et al. 2010, A&A, 518, L100, doi: [`10.1051/0004-6361/201014659`](http://doi.org/10.1051/0004-6361/201014659)

(ref: 1998A&A...336..150M) Motte, F., Andre, P., & Neri, R. 1998, A&A, 336, 150

(ref: 2018ARA&A..56...41M) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41, doi: [`10.1146/annurev-astro-091916-055235`](http://doi.org/10.1146/annurev-astro-091916-055235)

(ref: 2007A&A...476.1019M) Mottram, J. C., Hoare, M. G., Lumsden, S. L., et al. 2007, A&A, 476, 1019, doi: [`10.1051/0004-6361:20077663`](http://doi.org/10.1051/0004-6361:20077663)

(ref: 1991A&A...247..202M) Murphy, D. C., & May, J. 1991, A&A, 247, 202

(ref: 1987PThPh..77..635N) Nagasawa, M. 1987, Progress of Theoretical Physics, 77, 635, doi: [`10.1143/PTP.77.635`](http://doi.org/10.1143/PTP.77.635)

(ref: 2018ApJ...856..147O) Ohashi, S., Sanhueza, P., Sakai, N., et al. 2018, ApJ, 856, 147, doi: [`10.3847/1538-4357/aab3d0`](http://doi.org/10.3847/1538-4357/aab3d0)

(ref: 1994A&A...291..943O) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: 1964ApJ...140.1056O) Ostriker, J. 1964, ApJ, 140, 1056, doi: [`10.1086/148005`](http://doi.org/10.1086/148005)

(ref: 2023MNRAS.524.1291P) Padmanabh, P. V., Barr, E. D., Sridhar, S. S., et al. 2023, MNRAS, 524, 1291, doi: [`10.1093/mnras/stad1900`](http://doi.org/10.1093/mnras/stad1900)

(ref: 2020ApJ...900...82P) Padoan, P., Pan, L., Juvela, M., Haugbølle, T., & Nordlund, Å. 2020, ApJ, 900, 82, doi: [`10.3847/1538-4357/abaa47`](http://doi.org/10.3847/1538-4357/abaa47)

(ref: 2013A&A...550A..38P) Palmeirim, P., André, P., Kirk, J., et al. 2013, A&A, 550, A38, doi: [`10.1051/0004-6361/201220500`](http://doi.org/10.1051/0004-6361/201220500)

(ref: 2022A&A...664A..26P) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26, doi: [`10.1051/0004-6361/202142951`](http://doi.org/10.1051/0004-6361/202142951)

(ref: 2023A&A...674A..76P) —. 2023, A&A, 674, A76, doi: [`10.1051/0004-6361/202244776`](http://doi.org/10.1051/0004-6361/202244776)

(ref: 2012ApJ...756...60S) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012, ApJ, 756, 60, doi: [`10.1088/0004-637X/756/1/60`](http://doi.org/10.1088/0004-637X/756/1/60)

(ref: 2019ApJ...886..102S) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102, doi: [`10.3847/1538-4357/ab45e9`](http://doi.org/10.3847/1538-4357/ab45e9)

(ref: 2015MNRAS.452.2410S) Seifried, D., & Walch, S. 2015, MNRAS, 452, 2410, doi: [`10.1093/mnras/stv1458`](http://doi.org/10.1093/mnras/stv1458)

(ref: 2019A&A...623A..16S) Shimajiri, Y., André, P., Palmeirim, P., et al. 2019, A&A, 623, A16, doi: [`10.1051/0004-6361/201834399`](http://doi.org/10.1051/0004-6361/201834399)

(ref: 2023A&A...672A.133S) Shimajiri, Y., André, P., Peretto, N., et al. 2023, A&A, 672, A133, doi: [`10.1051/0004-6361/202140857`](http://doi.org/10.1051/0004-6361/202140857)

(ref: 2014MNRAS.445.2900S) Smith, R. J., Glover, S. C. O., & Klessen, R. S. 2014, MNRAS, 445, 2900, doi: [`10.1093/mnras/stu1915`](http://doi.org/10.1093/mnras/stu1915)

(ref: 2016MNRAS.455.3640S) Smith, R. J., Glover, S. C. O., Klessen, R. S., & Fuller, G. A. 2016, MNRAS, 455, 3640, doi: [`10.1093/mnras/stv2559`](http://doi.org/10.1093/mnras/stv2559)

(ref: 1963AcA....13...30S) Stodólkiewicz, J. S. 1963, Acta Astronomica, 13, 30

(ref: 2010ApJ...719....9S) Strafella, F., Elia, D., Campeggio, L., et al. 2010, ApJ, 719, 9, doi: [`10.1088/0004-637X/719/1/9`](http://doi.org/10.1088/0004-637X/719/1/9)

(ref: 2015ApJ...798..104S) Strafella, F., Lorenzetti, D., Giannini, T., et al. 2015, ApJ, 798, 104, doi: [`10.1088/0004-637X/798/2/104`](http://doi.org/10.1088/0004-637X/798/2/104)

(ref: 2016A&A...590A...2S) Stutz, A. M., & Gould, A. 2016, A&A, 590, A2, doi: [`10.1051/0004-6361/201527979`](http://doi.org/10.1051/0004-6361/201527979)

(ref: 2015A&A...574A.104T) Tafalla, M., & Hacar, A. 2015, A&A, 574, A104, doi: [`10.1051/0004-6361/201424576`](http://doi.org/10.1051/0004-6361/201424576)

(ref: 2019A&A...629A..81T) Treviño-Morales, S. P., Fuente, A., Sánchez-Monge, Á., et al. 2019, A&A, 629, A81, doi: [`10.1051/0004-6361/201935260`](http://doi.org/10.1051/0004-6361/201935260)

(ref: 2014A&A...568A..41U) Urquhart, J. S., Csengeri, T., Wyrowski, F., et al. 2014, A&A, 568, A41, doi: [`10.1051/0004-6361/201424126`](http://doi.org/10.1051/0004-6361/201424126)

(ref: 2019MNRAS.490.3061V) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061, doi: [`10.1093/mnras/stz2736`](http://doi.org/10.1093/mnras/stz2736)

(ref: 2016ApJS..226....9W) Wang, K., Testi, L., Burkert, A., et al. 2016, ApJS, 226, 9, doi: [`10.3847/0067-0049/226/1/9`](http://doi.org/10.3847/0067-0049/226/1/9)

(ref: 2024arXiv240402275X) Xu, F., Wang, K., Liu, T., et al. 2024a, arXiv e-prints, arXiv:2404.02275, doi: [`10.48550/arXiv.2404.02275`](http://doi.org/10.48550/arXiv.2404.02275)

(ref: 2024ApJS..270....9X) —. 2024b, ApJS, 270, 9, doi: [`10.3847/1538-4365/acfee5`](http://doi.org/10.3847/1538-4365/acfee5)

(ref: 2023MNRAS.520.3259X) Xu, F.-W., Wang, K., Liu, T., et al. 2023, MNRAS, 520, 3259, doi: [`10.1093/mnras/stad012`](http://doi.org/10.1093/mnras/stad012)

(ref: 2023ApJ...957...94Y) Yoo, H., Lee, C. W., Chung, E. J., et al. 2023, ApJ, 957, 94, doi: [`10.3847/1538-4357/acf8c2`](http://doi.org/10.3847/1538-4357/acf8c2)

(ref: 2020A&A...642A..76Z) Zhang, G.-Y., André, P., Men’shchikov, A., & Wang, K. 2020, A&A, 642, A76, doi: [`10.1051/0004-6361/202037721`](http://doi.org/10.1051/0004-6361/202037721)

(ref: 2015ApJ...804..141Z) Zhang, Q., Wang, K., Lu, X., & Jiménez-Serra, I. 2015, ApJ, 804, 141, doi: [`10.1088/0004-637X/804/2/141`](http://doi.org/10.1088/0004-637X/804/2/141)

</paper>

Write the methods card for this paper.