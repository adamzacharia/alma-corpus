# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...684L..12S\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...684L..12S",
 "title": "FAUST. XIII. Dusty cavity and molecular shock driven by IRS7B in the Corona Australis cluster",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Sabatini, G.",
 "n_authors": 57,
 "arxiv_id": "2403.18108",
 "doi": "10.1051/0004-6361/202449616",
 "alma_projects_linked_by_archive": [
  "2018.1.01205.L"
 ]
}
```

Paper text:
<paper>
# FAUST\
XIII. Dusty cavity and molecular shock driven by IRS7B in the Corona Australis cluster

The origin of the chemical diversity observed around low-mass protostars probably resides in the earliest history of these systems. We aim to investigate the impact of protostellar feedback on the chemistry and grain growth in the circumstellar medium of multiple stellar systems.

In the context of the ALMA Large Program FAUST, we present high-resolution (50 au) observations of CH$_3$OH, H$_2$CO, and SiO and continuum emission at 1.3 mm and 3 mm towards the Corona Australis star cluster.

Methanol emission reveals an arc-like structure at $\sim$1800 au from the protostellar system IRS7B along the direction perpendicular to the major axis of the disc. The arc is located at the edge of two elongated continuum structures that define a cone emerging from IRS7B. The region inside the cone is probed by H$_2$CO, while the eastern wall of the arc shows bright emission in SiO, a typical shock tracer. Taking into account the association with a previously detected radio jet imaged with JVLA at 6 cm, the molecular arc reveals for the first time a bow shock driven by IRS7B and a two-sided dust cavity opened by the mass-loss process. For each cavity wall, we derive an average H$_2$ column density of $\sim$7$\times$10$^{21}$ cm$^{-2}$, a mass of $\sim$9$\times$10$^{-3}$ M$_\odot$, and a lower limit on the dust spectral index of $1.4$.

These observations provide the first evidence of a shock and a conical dust cavity opened by the jet driven by IRS7B, with important implications for the chemical enrichment and grain growth in the envelope of Solar System analogues.

# Introduction

![](Figure1_cont_Band6s1_panels3.pdf)

Protostellar feedback, resulting from the complex interplay between newly forming Sun-like stars and their environment, plays a crucial role in shaping the chemical composition of the interstellar medium (ISM). The injection of energy and momentum leads to a cascade of physical and chemical processes that influence the molecular composition of the ISM (cite: Herbst-vanDishoeck09; Frank14; Ceccarelli23). Feedback mechanisms, including stellar winds, jets, cavities, and outflows, create a dynamic environment (e.g. shocks) that favours the enrichment of chemical species (cite: Bachiller2001) and pave the way for the formation of interstellar complex organic molecules (iCOMs[^1]; i.e. organic molecules with at least six atoms; (cite: Ceccarelli17)). Modern interferometers, such as the Atacama Large Millimeter/submillimeter Array (ALMA), enable astronomers to investigate these processes more thoroughly. However, so far, no clear symmetric dusty cavities opened by protostellar jets have been imaged.\
In this context, the ALMA Large Program (LP) Fifty AU STudy of the chemistry in the disk/envelope system of Solar-like protostars (FAUST)[^2] is designed to characterise the chemical diversity of young solar-like protostars down to a spatial resolution of $\sim$50 au. FAUST has shown that the chemical structure of molecular envelopes on scales of $>$1000 au is influenced by protostellar outflow activity (cite: Okoda21). New case studies are needed to further investigate the role of protostellar feedback on the different scales of envelope–disc systems.\
One of the FAUST targets is the nearby Corona Australis (CrA) complex. This region has been the subject of numerous observational campaigns (e.g. (cite: Knacke73), (cite: Harju93) and (cite: Neuhauser08)). Several Class 0/I protostars have been identified and characterised in terms of both their chemical (e.g. (cite: Groppi07; Watanabe12) and (cite: Lindberg14)) and physical properties (e.g. (cite: Nutter05; Cazzoletti19) and (cite: Sandell21)). IRS7B is the protostar at the centre of the CrA cluster, and is classified as a transitional Class 0/Class I object (cite: Groppi07; Watanabe12). Recently, IRS7B was resolved into a binary system formed by IRS7B-a and IRS7B-b ((cite: Ohashi23)), both associated with discs aligned with a position angle (PA) of 115$^\circ$ and an inclination of $\sim$ 65$^\circ$ (cite: Takakuwa24). The cluster also contains CXO 34 and IRS7A, two embedded Class I protostars, and SMM 1C (cite: Peterson11; Lindberg15). These studies also revealed prominent continuum emission from SMM 1A, observed with SCUBA-2 at 450 $\mu$m (Fig. [1](#fig:cont_RCrA); left) and located $\sim$2000 au southwest of IRS7B; its nature is still unclear. SMM 1A has been interpreted as either a quiescent prestellar object (cite: Nutter05) or a filamentary structure affected by external irradiation by the Herbig Ae/Be star R-CrA (cite: LindbergJorgensen12; Perotti23). The present Letter casts a new light on SMM 1A; we present an investigation of the protostellar feedback of IRS7B on the chemical properties of the ISM in the formation of multiple star–disc systems in CrA.

# Observations and data reduction

The CrA complex was observed as part of the FAUST ALMA LP between October 2018 and September 2019 (2018.1.01205.L; PI: S. Yamamoto; (cite: Codella21)) at a resolution of $\sim$0.4$''$ ($\sim$52 au at the CrA distance of 130 pc; (cite: Lindberg14)). We observed three spectral setups, one in Band 3 (85-101 GHz) and two in Band 6 (214-234 GHz and 242-262 GHz). Appendix [6](#App:data) summarises the telescope setups for both the 12m array and the Atacama Compact Array (ACA; Band 6 only). The average maximum recoverable scale is $\sim$21$\ensuremath{''}$ ($\sim$2700 au). All observations were made with a precipitable water vapour of $<$ 2.0 mm.\
The observations were centred on ($\alpha_{\rm ICRS}, \delta_{\rm ICRS}) = ({\rm 19h01m56s.42}, {\rm -36^\circ57\ensuremath{'}28\ensuremath{''}.40}$). The absolute flux calibration uncertainty is 10%. Data were calibrated employing the CASA pipeline 6.2.1-7 ((cite: CASA_Team_22)), including additional routines to correct for system temperature and spectral normalisation issues[^3], and self-calibrated using line-free channels. The final continuum-subtracted line-cubes were cleaned (Hogbom deconvolver) with BRIGGS weighting scheme with ROBUST $=0.5$ (App. [6](#App:data)). The typical rms noise is $\sim$0.08 mJy beam$^{-1}$ for continuum and 0.8–3 mJy beam$^{-1}$ per channel for lines. Self-calibration improved the dynamic range of the continuum maps by factors of between 3 and 10 depending on the data set. The primary beam correction was applied to all the images.

+:---------------------------------+:-----------:+:--------------------:+:----------------------------:+:-----------------:+:---------------------------:+:------------------:+:------------:+:------------:+:------------:+
| Transitions                      | $\nu^{(a)}$ | $E_{\rm up}$$^{(a)}$ | log$_{10}(A_{\rm ul})^{(a)}$ | $g_{\rm u}^{(a)}$ | $\delta V_{\rm chan}^{(a)}$ | $n_{\rm cr}^{(c)}$ | $\int I$ \[K km s$^{-1}$\]$^{(a)}$         |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
|                                  | (MHz)       | \(K\)                | (s$^{-1}$)                   |                   | (km s$^{-1}$)               | (10$^4$ cm$^{-3}$) |     “A”      |     “B”      |     “C”      |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
| CH$_3$OH-A (8$_{0,8}$-7$_{1,7}$) | 95169.391   | 84                   | $-5.37$                      | 68                | 1.54                        | 1.3 – 1.4          | 8.6          | 4.1          | 6.1          |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
| CH$_3$OH-A (2$_{1,2}$-1$_{1,1}$) | 95914.310   | 22                   | $-5.60$                      | 20                | 1.54                        | 2.0 – 2.1          | 4.1          | 1.8          | 3.9          |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
| CH$_3$OH-A (3$_{1,3}$-4$_{0,4}$) | 107013.831  | 28                   | $-5.51$                      | 28                | 0.17                        | 3.2 – 3.5          | 4.5          | $<2.6$       | 2.8          |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
| SiO (5-4)                        | 217104.980  | 31                   | $-3.28$                      | 11                | 0.51                        | 153.1 – 156.1      | 1.2          | 3.7          | $<0.6$       |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
| CH$_3$OH-E (4$_{2,3}$-3$_{1,2}$) | 218440.063  | 46                   | $-4.33$                      | 36                | 0.17                        | 24.3 – 23.4        | 19.2         | 8.6          | 9.2          |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
| p-H$_2$CO (3$_{0,3}$-2$_{0,2}$)  | 218222.192  | 21                   | $-3.55$                      | 7                 | 0.17                        | 160.1 – 183.0      | 14.3         | 8.9          | 17.9         |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+
| CH$_3$OH-A (5$_{1,4}$-4$_{1,3}$) | 243915.788  | 50                   | $-4.22$                      | 44                | 0.15                        | 19.9 – 21.1        | –            | 6.9          | 3.9          |
+----------------------------------+-------------+----------------------+------------------------------+-------------------+-----------------------------+--------------------+--------------+--------------+--------------+

Table notes: $^{(a)}$ Spectroscopic data from The Cologne Database for Molecular Spectroscopy ((cite: Muller05)); $^{(b)}$ The SiO (5-4) spectrum is smoothed in velocity by a factor of three to increase sensitivity. $^{(c)}$ Critical densities obtained considering downward collision rates in a multilevel system and a temperature range of 50-100 K (Sect. [3.3](#sec3.3:RDiagram)). Collisional rates taken from the LAMDA database ((cite: Schoier05)), based on (cite: Balanca18) for SiO, (cite: Wiesenfeld13) for p-H$_2$CO and (cite: RabliFlower10) for the A- and E-type CH$_3$OH. $^{(d)}$ We assume an uncertainty of 20%. Regions ‘A’, ‘B’, and ‘C’ are centred at the peak positions of CH$_3$OH (4$_{2,3}$-3$_{1,2}$), SiO (5-4), and p-H$_2$CO (3$_{0,3}$-2$_{0,2}$), respectively (see Fig. [2](#fig:moments_zero)).

# Results

## Continuum emission

Figure [1](#fig:cont_RCrA) (central) shows the spatial distribution of dust continuum emission at 1.3 mm in the CrA field, where four compact sources are detected: IRS7B, CXO 34, IRS7A, and SMM1-C. For these sources, the position of the 1.3 mm continuum peaks derived with a 2D Gaussian fit (Appendix [7](#app:channels)) matches the coordinates reported by (cite: Lindberg14). In addition, a fifth source (labelled FAUST-5) is detected for the first time SE of IRS7B. No compact counterpart has been identified in the molecular lines in FAUST, suggesting a potential extragalactic origin.\
More intriguingly, the continuum emission reveals the existence of two elongated structures SW of the field. These structures are detected ($>$3$\sigma$) up to $\sim$1000 au (SW) and $\sim$1700 au (S), respectively, from IRS7B. A zoom onto the central region (Fig. [1](#fig:cont_RCrA); right) shows that the two structures are symmetric with respect to the normal direction of the disc and extend along the expected direction of the outflow driven by IRS7B, with an opening angle of $\sim$50$^\circ$ (dashed lines). Following (cite: Sabatini23), we estimate the H$_2$ column density and mass of the cavity walls, assuming optically thin dust emission, a dust temperature of 30 K (cite: Perotti23), a standard gas-to-dust ratio of 100, and a dust opacity of $\kappa_{\rm 1.3mm}$= 0.9 cm$^2$ g$^{-1}$ (cite: Ossenkopf94), which are typical values for icy mantle dust grains and well reproduce multi-wavelength observations of low-mass star-forming regions (cite: Evans01; Shirley05). The average $N$(H$_2$) and mass of each cavity wall are $\sim$7$\times$10$^{21}$ cm$^{-2}$ and $\sim$9$\times$10$^{-3}$ M$_\odot$, respectively. This mass corresponds to $\sim$0.1$\%$ of the IRS7B envelope mass estimated by (cite: vanKempen09). Taking into account an uncertainty of 10% in the absolute flux calibration of the ALMA data, $<$15% in the assumed dust temperature (cite: Sabatini22) and $\sim$30% for the dust opacity (cite: Sanhueza19), the overall uncertainty for $N$(H$_2$) and the mass of each cavity wall is $\lesssim$35%.

## Line emission

We mapped the molecular emission of five CH$_3$OH lines, associated with a range of upper level energy, $E_{\rm up}$, from 21 K to 84 K, para-H$_2$CO (3$_{0,3}$-2$_{0,2}$), and SiO (5-4) (see Table [\[tab:line_properties\]](#tab:line_properties)). Figure [2](#fig:moments_zero) shows the integrated intensity maps (moment 0 maps) of the brightest lines over the velocity range \[0, $+12$\] km s$^{-1}$.\

![](Figure2_multipanel_arc_RCrA_circle_v4.pdf)

Figure [2](#fig:moments_zero)a shows the spatial distribution of the CH$_3$OH-E (4$_{2,3}$-3$_{1,2}$), and reveals a molecular-arc structure that is confined within the two elongated structures detected in continuum. The arc has a length of $\sim$3000 au and is located at a projected distance from IRS7B of $\sim$1800 au, close to the coordinates of SMM 1A (cite: Nutter05; ChenArce10). Additional information is provided by the channel maps (Fig. [6](#fig:channelmaps)a). The methanol emission extends from +3.5 to +8.0 km s$^{-1}$ around the systemic velocity of IRS7B ($V^{\rm IRS7B}_{\rm sys}$ $\sim$ +6 km s$^{-1}$; (cite: Ohashi23)), with most of the emission at blueshifted velocities. Similar structures are traced by the other methanol lines in Fig. [2](#fig:moments_zero)(b, c). The CH$_3$OH-A (8$_{0,8}$-7$_{1,7}$), detected in Band 3, shows several bright spots consistent with the CH$_3$OH 4$_{2,3}$-3$_{1,2}$ transition, plus fainter spots outside the Band 6 ALMA field of view (FoV; green circle in Fig. [2](#fig:moments_zero)). This is consistent with the distribution of CH$_3$OH in Band 6 in the ACA-only maps, where the emission is recovered on a larger FoV at the expense of angular resolution (see Appendix [6](#App:data)). In the CH$_3$OH-A (5$_{1,4}$-4$_{1,3}$) line, part of the arc structure falls outside the FoV, which is smaller at $\sim$244 GHz compared to that at $\sim$218 GHz. The other methanol lines with low $E_{\rm up}$ (i.e. 22 K and 28 K; Table [\[tab:line_properties\]](#tab:line_properties)) do not allow a clear identification of the arc-like structure. However, these lines are also detected at $>$3$\sigma$ in the spectra integrated on the brightest emission peaks of the arc structure (Appendix [7](#app:channels)).\
The emission from para-H$_2$CO (3$_{0,3}$-2$_{0,2}$), hereafter referred to as p-H$_2$CO, is more extended than that from methanol; it probes both the arc structure, similarly to CH$_3$OH, and an extended component confined mostly within the boundaries of the cone probed by the dust at 1.3 mm (Fig. [2](#fig:moments_zero)d). The channel maps show that, at redshifted velocities and close to $V^{\rm IRS7B}_{\rm sys}$, the p-H$_2$CO emission is extended over a large portion of the FoV, and therefore it is likely contaminated by envelope emission, while it follows the methanol distribution at blueshifted velocities (Fig. [6](#fig:channelmaps)b), revealing arc structures.\
The SiO (5-4) moment 0 map reveals two emitting regions (Fig. [2](#fig:moments_zero)e): the first overlaps on the SW side of the molecular arc traced by CH$_3$OH and H$_2$CO; the second is located at the edge of the FoV, beyond the CH$_3$OH molecular arc, at a distance of $>$2100 au from IRS7B. The channel maps show that SiO has the predominant emission component in the blueshifted regime similarly to CH$_3$OH and H$_2$CO (Fig. [7](#fig:channel_SOSiO)). This suggests that the blueshifted emission of SiO is also associated with the arc-structure revealed by CH$_3$OH and H$_2$CO (see Sect. [5](#sec5:conclusions)).\

## Physical properties of the molecular arc

To determine the physical conditions of the emitting gas in the molecular arc, we extracted the spectra of all the observed lines at three positions along the arc structure, labelled ‘A’, ‘B’, and ‘C’, and centred at the peak positions of CH$_3$OH (4$_{2,3}$-3$_{1,2}$), SiO (5-4), and p-H$_2$CO (3$_{0,3}$-2$_{0,2}$), respectively (Fig. [2](#fig:moments_zero)). Each region has an equivalent area of nine ALMA beams. The spectra and the line fitting are discussed in Appendix [7](#app:channels).\
Assuming local thermodynamic equilibrium (LTE) and optically thin emission, we constructed rotational diagrams (RDs) to quantify the column density, $N_{\rm tot}$, and the rotational temperature, $T_{\rm rot}$, of CH$_3$OH (Fig. [3](#fig:RDiagram)) observed in the ‘A’, ‘B’, and ‘C’ positions. It is assumed that the methanol A/E ratio is equal to unity, which is a good approximation for temperatures of $> 20$ K (cite: Wirstrom11; Carney19). We derived the critical densities of the observed lines (Table [\[tab:line_properties\]](#tab:line_properties)) assuming a temperature range of 50-100 K and taking into account downward collision rates in a multi-level system (cite: Draine11). The critical densities range from 10$^4$ cm$^{-3}$ to $\sim$2$\times$10$^6$ cm$^{-3}$ —below the average H$_2$ number densities determined for SMM 1A (i.e. 10$^6$ cm$^{-3}$; (cite: LindbergJorgensen12))—, which supports the assumption of LTE conditions. The RD analysis is obtained using the line intensity integrated on the blueshifted arc component. Taking into account the calibration uncertainty and the rms of the lines spectra, the errors on the integrated intensities is $\sim$20%. The methanol $N^{\rm CH_3OH}_{\rm tot}$ are between 6$\pm$2$\times$10$^{15}$ cm$^{-2}$ and 16$\pm$3$\times$10$^{15}$ cm$^{-2}$, with $T_{\rm rot}$ of $\sim$50-60 K. In region ‘A’, where methanol peaks, we performed a non-LTE large velocity gradient (LVG) analysis using the `grelvg` code (cite: Ceccarelli03). The resulting $T_{\rm rot, LVG}\sim$70-90 K and $N^{\rm CH_3OH}_{\rm tot, LVG}$$\sim$2-6$\times$10$^{15}$ cm$^{-2}$ are in agreement with those derived from the RDs. Indeed the derived line opacities ($\tau<0.5$) and gas densities ($\sim$2$\times$10$^7$ cm$^{-3}$) support the LTE and optically thin RD assumptions. Our results are consistent with the previous estimate by (cite: Perotti23), who observed SMM 1A, combining Submillimeter Array (SMA) and Atacama Pathfinder Experiment (APEX) observations, and assuming a $T_{\rm rot}\sim$30 K.\

![image](Figure4_RD-RCrA-CH3OH_tot.pdf) 7

Assuming the same range of $T_{\rm rot}$ as that obtained for CH$_3$OH, we derive $N_{\rm tot}^{\rm H_2CO}$ $\simeq$ 0.8–2$\times$10$^{14}$ cm$^{-2}$. Our $N_{\rm tot}^{\rm H_2CO}$ values are approximately consistent with the values reported for SMM 1A by (cite: LindbergJorgensen12), 10$^{13}$–10$^{14}$ cm$^{-2}$, which are based on SMA/APEX observations with a resolution of $\sim$6$''$$\times$3$''$, and a $T_{\rm rot}$ $\sim$ 48 K. Finally, we derived the total column density of SiO, a typical shock-induced sputtering tracer (see Section [4](#sec4:discussion_conclusions)), assuming a temperature range of 50-150 K (cite: Podio21), obtaining $N_{\rm tot}^{\rm SiO}$ = 1-3 $\times$ 10$^{13}$ cm$^{-2}$ towards the SiO emitting peak (B). The estimated $N_{\rm tot}$, as well as the \[CH$_3$OH\]/\[SiO\] and \[CH$_3$OH\]/\[H$_2$CO\] abundance ratios ($\sim$250-600, and $\sim$40-130, respectively), are in agreement with the values derived in shocked regions around low-mass protostars (e.g. (cite: Bachiller1997; Cuadrado17; Podio21; deSimone22)).

# Discussion

![](Figure5_JVLA_zoom_cont.pdf)

The ALMA-FAUST data reveal an extended molecular arc-structure traced by CH$_3$OH, where emission due to H$_2$CO and SiO has also been detected. The arc is located in the SW region of the CrA cluster and matches the coordinates of SMM 1A. The RD analysis of the CH$_3$OH lines supports that the arc is a coherent structure with relatively constant $N_{\rm tot}^{\rm CH_3OH}$ and $T_{\rm rot}^{\rm CH_3OH}$ . The H$_2$CO distribution shows that the arc is connected to the IRS7B system at the CrA cluster centre.

## Physical origin of the molecular arc in CrA

Methanol is one of the most abundant iCOMs detected in star-forming regions and is considered a key precursor of many prebiotic compounds in space (cite: Herbst-vanDishoeck09; Ceccarelli23). The main chemical process for synthesising CH$_3$OH is CO hydrogenation on grains, in which CO is converted to H$_2$CO and then to methanol. This process is extremely efficient in solid phase during the early stages of star formation (cite: WatanabeKouchi02; Fuchs09; Santos22) when the gas temperatures are $<$20 K, $n(\rm H_2)> 10^{4}$ cm$^{-3}$, and CO is strongly depleted at the surface of dust grains (e.g. (cite: Caselli99; Bergin02; Sabatini19; Sabatini21; Sabatini22)). The detection of methanol in the arc-structure in CrA can be associated with either ($i$) external irradiation (cite: Cuadrado17) or ($ii$) shocked regions (cite: Ceccarelli23).\
The first interpretation was proposed by (cite: LindbergJorgensen12), who derived a map of H$_2$CO rotational temperature based on SMA/APEX observations with a resolution of 6$''$$\times$3$\ensuremath{''}$. The authors found $T_{\rm rot}^{\rm H_2CO}$ in the 60-100 K range, and interpreted this high value as a consequence of external illumination by the Herbig Ae/Be star R CrA located at $\sim$50$''$ in the NW direction (i.e. $\sim$6500 au at the cluster distance). The interstellar radiation field in SMM 1A would increase by a factor of 750 to 3000 when assuming a luminosity of 100-200 L$_\odot$ for R CrA, respectively. This picture is in agreement with the recent estimates of (cite: Sissa19), who report an R CrA luminosity of $\sim$130 L$_\odot$, and with the relatively small full width at half maximums (FWHMs) of the CH$_3$OH and H$_2$CO lines ($<$1.2 km s$^{-1}$) fitted in Fig. [8](#fig:spectra). Nevertheless, the 50 au angular resolution of the FAUST data enabled us to resolve the arc structure with unprecedented accuracy, that is, a factor of $\sim$10 greater accuracy than in (cite: LindbergJorgensen12). The newly discovered arc morphology found in SMM 1A would suggest a source of illumination in the southwest (outside the ALMA FoV) or in the cluster centre. Remarkably, no major illumination source is found in either direction, as only the IRS7B system ($L_{\rm bol}\sim 4.6$ L$_\odot$; (cite: Lindberg14)) and the prestellar source SMM 1As ($L_{\rm bol}\sim 0.04$ L$_\odot$; (cite: Sicilia-Aguilar13)) have been reported in the literature within 50$''$ of SMM 1A.\
On the other hand, the SiO detection at the edge of the CH$_3$OH arc supports the second scenario, in which the arc is the fingerprint of a shocked region. Indeed, SiO is mainly formed by the shock-induced sputtering and/or shattering of the grain mantles and refractory cores (cite: Caselli97; Gusdorf08a; Gusdorf08b; Jimenez-Serra08; Guillet11). In this case, the arc-shape suggests the occurrence of a jet driven by IRS7B towards the SW. Moreover, the molecular arc revealed by FAUST is blueshifted, in agreement with the disc flaring reported by (cite: Takakuwa24), indicating that the near disc-side is to the NE, and therefore the blueshifted jet is towards the SW.\
Evidence of outflowing material in CrA was first suggested by (cite: Levreault88) based on $^{12}$CO (2-1) data collected with the Millimeter Wave Observatory (MWO). Although the coarse resolution of the MWO (1.3$''$) prevented the identification of the driving source(s), the blueshifted wing of the outflow is aligned along the direction connecting IRS7B with SMM 1A. Radio continuum observations with ATCA[^4] at 3, 6, and 20 cm revealed a bipolar structure in the NE-SW direction centred on IRS7B (cite: Harju01; Choi08; Miettinen08). More recently, (cite: Liu14) also reported an extended ($\sim$70$''$ in the SMM 1A direction) bipolar radio jet detected at 3.5 cm with the Karl G. Jansky Very Large Array (JVLA; beam $\sim$4$''$$\times$2$\ensuremath{''}$). In Fig. [4](#fig:JVLA) (left panel), we show the JVLA map (green contrours; (cite: Liu14)) superimposed on the SCUBA-2 map at 450 $\mu$m (grey scale[^5]). What originally appeared in the SCUBA-2 data as an overdensity of cold gas (cite: Nutter05; Chen10) overlaps with both ($a$) the direction of propagation of the radio-jet discovered by (cite: Liu14) and ($b$) the molecular arc traced by methanol (see Fig. [4](#fig:JVLA), right). Moreover, the region in which the radio-jet would collide with the arc also corresponds to the zone in which the $T_{\rm rot}^{\rm H_2CO}$ derived in (cite: LindbergJorgensen12) reaches its maximum values. In conclusion, based on the arc-shape, the association with the radio jet detected at centimetre wavelengths, and the detection of a typical shock tracer, namely SiO, we conclude that the observed molecular arc is most likely the signature of a bow-shock driven by IRS7B.

## First imaging of symmetric dusty cavity walls

In light of these findings, the ‘V’-shaped structure detected in continuum (Fig. [4](#fig:JVLA), right) traces the dust emission from the cavity walls opened by the IRS7B outflow. This is in agreement with the direction of the JVLA radio jet with the orientation of the cavity observed by ALMA (Fig. [4](#fig:JVLA)). To our knowledge, this is the first imaging of symmetric cavity walls of dust opened by a jet (on scales of 50 au) in a low-mass star-forming system.\
\
The spectral index for typical ISM grains is $\alpha_{\rm ISM}$$\sim$3.7 (cite: Testi14), while low values (down to $\alpha$$\sim$1.5) have been observed in the inner few hundred astronomical units (au) around Class 0/I sources. Low $\alpha$ values can be due to dust growth (cite: Chiang12; Miotello14; Galametz19), while recent theoretical calculations and observations show that large grains in the envelope may be the result of transport from the site of growth, the inner dense disc, to the envelope via magnetohydrodynamical (MHD) winds (cite: Wong16; Giacalone19; Tsukamoto21; Cacciapuoti23). In this context, the estimated $\alpha>1.4$ allows the possibility that high-density cavity walls, like those in CrA, are the sites for in situ dust growth in protostellar envelopes.

# Conclusions

In this Letter, we present high-resolution (50 au) observations of continuum (1.3 and 3 mm) and molecular (CH$_3$OH, H$_2$CO and SiO) emission towards the CrA cluster in the context of the ALMA FAUST LP. Our analysis indicates that SMM 1A, previously identified as an extended continuum structure, is associated with a shock driven by IRS7B, and mapped in CH$_3$OH, H$_2$CO, and SiO, and with a conical dusty cavity opened by the mass-loss process. We estimated the H$_2$ column density ($\sim$7$\times$10$^{21}$ cm$^{-2}$) and mass ($\sim$9$\times$10$^{-3}$ M$_\odot$) in the cavity walls, and a lower limit for the dust spectral index ($\alpha > 1.4$), which could imply the presence of millimetre-sized grains. Based on these results, we conclude that the CrA cluster may be a unique laboratory with which to investigate and test models of dust grain growth in the envelope.\
Additional higher-sensitivity and higher-resolution observations of shock tracers, such as SiO and CO, are needed to reveal the IRS7B jet. The discovery of a twin system in IRS7B (cite: Ohashi23) opens the possibility that there are two jets. Therefore, the SiO knot could be due to precession. Further mapping of CH$_3$OH emission in the SW region around SMM 1A and beyond the FAUST FoV is also needed to reveal additional interactions between the jet and the CrA envelope on a larger scale; our Band-3 maps already suggest their existence. This would allow us to determine the extent to which the jet influences the chemical composition of the CrA cluster. Ultimately, a more accurate estimate of $\alpha$ will be made possible with more sensitive observations at longer wavelengths, allowing us to constrain the properties and size distribution of the dust grains in the cavity walls and to probe for the formation and/or entrainment of large grains in the envelope.\

# Acknowledgements

The authors thank the anonymous Referee for suggestions that improved the manuscript, and A. Garufi for the fruitful discussion and feedback on the properties of interstellar dust. GS, LP and CC acknowledge the project PRIN-MUR 2020 MUR BEYOND-2p (“Astrochemistry beyond the second period elements”, Prot. 2020AFB3FX), the PRIN MUR 2022 FOSSILS (Chemical origins: linking the fossil composition of the Solar System with the chemistry of protoplanetary discs, Prot. 2022JC2Y93), the project ASI-Astrobiologia 2023 MIGLIORA (Modeling Chemical Complexity, F83C23000800005), and the INAF-GO 2023 fundings PROTO-SKA (Exploiting ALMA data to study planet forming disks: preparing the advent of SKA, C13C23000770005). GS acknowledges the INAF-Minigrant 2023 TRIESTE (“TRacing the chemIcal hEritage of our originS: from proTostars to planEts”; PI: G. Sabatini). LP acknowledges the INAF Mini-Grant 2022 “Chemical Origins” (PI: L. Podio). EB acknowledges support from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) under German´s Excellence Strategy – EXC 2094 – 390783311. MB and SV acknowledge support from the European Research Council (ERC) Advanced Grant MOPPEX 833460. SBC was supported by the NASA Planetary Science Division Internal Scientist Funding Program through the Fundamental Laboratory Research work package (FLaRe). LL acknowledges the support of DGAPA PAPIIT grants IN108324 and IN112820 and CONACyT-CF grant 263356. IJ-S acknowledges funding from grants No. PID2019-105552RB-C41 and PID2022-136814NB-I00 from the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by “ERDF A way of making Europe”. This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01205.L (PI: S. Yamamoto). ALMA is a partnership of the ESO (representing its member states), the NSF (USA) and NINS (Japan), together with the NRC (Canada) and the NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the ESO, the AUI/NRAO, and the NAOJ.

73 natexlab

(ref: Bachiller1997) Bachiller, R. & Pérez Gutiérrez, M. 1997, ApJL, 487, L93

(ref: Bachiller2001) Bachiller, R., Pérez Gutiérrez, M., Kumar, M. S. N., & Tafalla, M. 2001, A&A, 372, 899

(ref: Balanca18) Balança, C., Dayou, F., Faure, A., Wiesenfeld, L., & Feautrier, N. 2018, MNRAS, 479, 2692

(ref: Bergin02) Bergin, E. A., Alves, J., Huard, T., & Lada, C. J. 2002, ApJL, 570, L101

(ref: Cacciapuoti23) Cacciapuoti, L., Testi, L., Podio, L., et al. 2024, ApJ, 961, 90

(ref: Carney19) Carney, M. T., Hogerheijde, M. R., Guzmán, V. V., et al. 2019, A&A, 623, A124

(ref: Caselli97) Caselli, P., Hartquist, T. W., & Havnes, O. 1997, A&A, 322, 296

(ref: Caselli99) Caselli, P., Walmsley, C. M., Tafalla, M., Dore, L., & Myers, P. C. 1999, ApJL, 523, L165

(ref: Cazzoletti19) Cazzoletti, P., Manara, C. F., Baobab Liu, H., et al. 2019, A&A, 626, A11

(ref: Ceccarelli17) Ceccarelli, C., Caselli, P., Fontani, F., et al. 2017, ApJ, 850, 176

(ref: Ceccarelli23) Ceccarelli, C., Codella, C., Balucani, N., et al. 2023, in ASP Conference Series, Vol. 534, ASP Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 379

(ref: Ceccarelli03) Ceccarelli, C., Maret, S., Tielens, A. G. G. M., Castets, A., & Caux, E. 2003, A&A, 410, 587

(ref: Chen10) Chen, H.-R., Liu, S.-Y., Su, Y.-N., & Zhang, Q. 2010, ApJ, 713, L50

(ref: ChenArce10) Chen, X. & Arce, H. G. 2010, ApJL, 720, L169

(ref: Chiang12) Chiang, H.-F., Looney, L. W., & Tobin, J. J. 2012, ApJ, 756, 168

(ref: Choi08) Choi, M., Hamaguchi, K., Lee, J.-E., & Tatematsu, K. 2008, ApJ, 687, 406

(ref: Codella21) Codella, C., Ceccarelli, C., Chandler, C., et al. 2021, FSPAS, 8, 227

(ref: Cuadrado17) Cuadrado, S., Goicoechea, J. R., Cernicharo, J., et al. 2017, A&A, 603, A124

(ref: deSimone22) De Simone, M., Codella, C., Ceccarelli, C., et al. 2022, MNRAS, 512, 5214

(ref: Draine11) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium by Bruce T. Draine. Princeton University Press

(ref: Evans01) Evans, Neal J., I., Rawlings, J. M. C., Shirley, Y. L., & Mundy, L. G. 2001, ApJ, 557, 193

(ref: Frank14) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 451–474

(ref: Fuchs09) Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629

(ref: Galametz19) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5

(ref: Giacalone19) Giacalone, S., Teitler, S., Königl, A., Krijt, S., & Ciesla, F. J. 2019, ApJ, 882, 33

(ref: Ginsburg22) Ginsburg, A., Sokolov, V., de Val-Borro, M., et al. 2022, AJ, 163, 291

(ref: Groppi07) Groppi, C. E., Hunter, T. R., Blundell, R., & Sandell, G. 2007, ApJ, 670, 489

(ref: Guillet11) Guillet, V., Pineau Des Forêts, G., & Jones, A. P. 2011, A&A, 527, A123

(ref: Gusdorf08a) Gusdorf, A., Cabrit, S., Flower, D. R., & Pineau Des Forêts, G. 2008a, A&A, 482, 809

(ref: Gusdorf08b) Gusdorf, A., Pineau Des Forêts, G., Cabrit, S., & Flower, D. R. 2008b, A&A, 490, 695

(ref: Harju93) Harju, J., Haikala, L. K., Mattila, K., et al. 1993, A&A, 278, 569

(ref: Harju01) Harju, J., Higdon, J. L., Lehtinen, K., & Juvela, M. 2001, in ASP Conference Series, Vol. 235, Science with the Atacama Large Millimeter Array, ed. A. Wootten, 125

(ref: Herbst-vanDishoeck09) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: Jimenez-Serra08) Jiménez-Serra, I., Caselli, P., Martı́n-Pintado, J., & Hartquist, T. W. 2008, A&A, 482, 549

(ref: Knacke73) Knacke, R. F., Strom, K. M., Strom, S. E., Young, E., & Kunkel, W. 1973, ApJ, 179, 847

(ref: Levreault88) Levreault, R. M. 1988, ApJS, 67, 283

(ref: LindbergJorgensen12) Lindberg, J. E. & Jørgensen, J. K. 2012, A&A, 548, A24

(ref: Lindberg14) Lindberg, J. E., Jørgensen, J. K., Brinch, C., et al. 2014, A&A, 566, A74

(ref: Lindberg15) Lindberg, J. E., Jørgensen, J. K., Watanabe, Y., et al. 2015, A&A, 584, A28

(ref: Liu14) Liu, H. B., Galván-Madrid, R., Forbrich, J., et al. 2014, ApJ, 780, 155

(ref: Miettinen08) Miettinen, O., Kontinen, S., Harju, J., & Higdon, J. L. 2008, A&A, 486, 799

(ref: Miotello14) Miotello, A., Testi, L., Lodato, G., et al. 2014, A&A, 567, A32

(ref: Muller05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: Neuhauser08) Neuhäuser, R. & Forbrich, J. 2008, in Handbook of Star Forming Regions, Volume II, ed. B. Reipurth, Vol. 5, 735

(ref: Nutter05) Nutter, D. J., Ward-Thompson, D., & André, P. 2005, MNRAS, 357, 975

(ref: Ohashi23) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8

(ref: Okoda21) Okoda, Y., Oya, Y., Francis, L., et al. 2021, ApJ, 910, 11

(ref: Ossenkopf94) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: Perotti23) Perotti, G., Jørgensen, J. K., Rocha, W. R. M., et al. 2023, A&A, 678, A78

(ref: Peterson11) Peterson, D. E., o Garatti, A. C., Bourke, T. L., et al. 2011, ApJS, 194, 43

(ref: Podio21) Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45

(ref: RabliFlower10) Rabli, D. & Flower, D. R. 2010, MNRAS, 406, 95

(ref: Sabatini21) Sabatini, G., Bovino, S., Giannetti, A., et al. 2021, A&A, 652, A71

(ref: Sabatini23) Sabatini, G., Bovino, S., & Redaelli, E. 2023, ApJL, 947, L18

(ref: Sabatini22) Sabatini, G., Bovino, S., Sanhueza, P., et al. 2022, ApJ, 936, 80

(ref: Sabatini19) Sabatini, G., Giannetti, A., Bovino, S., et al. 2019, MNRAS, 490, 4489

(ref: Sandell21) Sandell, G., Reipurth, B., Vacca, W. D., & Bajaj, N. S. 2021, ApJ, 920, 7

(ref: Sanhueza19) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102

(ref: Santos22) Santos, J. C., Chuang, K.-J., Lamberts, T., et al. 2022, ApJL, 931, L33

(ref: Schoier05) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: Shirley05) Shirley, Y. L., Nordhaus, M. K., Grcevich, J. M., et al. 2005, ApJ, 632, 982

(ref: Sicilia-Aguilar13) Sicilia-Aguilar, A., Henning, T., Linz, H., et al. 2013, A&A, 551, A34

(ref: Sissa19) Sissa, E., Gratton, R., Alcalà, J. M., et al. 2019, A&A, 630, A132

(ref: Takakuwa24) Takakuwa, S., Saigo, K., Kido, M., et al. 2024, arXiv e-prints, arXiv:2401.08722

(ref: Testi14) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339–361

(ref: CASA_Team_22) The CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Tsukamoto21) Tsukamoto, Y., Machida, M. N., & Inutsuka, S. 2021, ApJ, 913, 148

(ref: vanKempen09) van Kempen, T. A., van Dishoeck, E. F., Hogerheijde, M. R., & Güsten, R. 2009, A&A, 508, 259

(ref: WatanabeKouchi02) Watanabe, N. & Kouchi, A. 2002, ApJL, 571, L173

(ref: Watanabe12) Watanabe, Y., Sakai, N., Lindberg, J. E., et al. 2012, ApJ, 745, 126

(ref: Wiesenfeld13) Wiesenfeld, L. & Faure, A. 2013, MNRAS, 432, 2573

(ref: Wirstrom11) Wirström, E. S., Geppert, W. D., Hjalmarson, Å., et al. 2011, A&A, 533, A24

(ref: Wong16) Wong, Y. H. V., Hirashita, H., & Li, Z.-Y. 2016, PASJ, 68, 67

# Details on data reduction

Table [1](#tab:obs_ALMA) summarises the details of the dataset acquired with ALMA for the CrA stellar cluster in the context of the FAUST Large Program (cite: Codella21). The B6 data were acquired over 12 spectral windows (SPWs) with a bandwidth ($\Delta\nu$)/frequency resolution ($\delta\nu$) of 59 MHz/122 kHz ($\sim$67-82 km s$^{-1}$/0.17-0.20 km s$^{-1}$), whilst 6 SPWs of 59 MHz/61 kHz ($\sim$160-190 km s$^{-1}$/0.20 km s$^{-1}$) were observed in B3. In all spectral settings, one additional SPW of 1.9 GHz was dedicated to the thermal dust continuum emission, i.e. 2294 (B6s1), 2404 (B6s2), and 5917 km s$^{-1}$ (B3). For the latter, $\delta\nu$ was 0.5 MHz for B6s1 (0.72 km s$^{-1}$) and B3 (1.54 km s$^{-1}$), and 1.1 MHz (1.39 km s$^{-1}$) for B6s2. Details of the observations and of the calibrators are summarised in Table [1](#tab:obs_ALMA). The average angular scales covered at these frequencies range from a synthesised beam, $\theta_{\rm res}$, of $\sim$0.4$''$$\times$0.3$''$ to a maximum recoverable scale, $\theta_{\rm MRS}$, of $\sim$21$''$ ; that is, $\sim$52-2700 au at the source distance of 130 pc ((cite: Lindberg14)). The final datacubes were obtained combining different ALMA configurations, including the 12m array and the ACA. Figure [5](#fig:12m7m) shows an example of how the distribution of CH$_3$OH (4$_{2,3}$-3$_{1,2}$) E, observed in B6-s1, varies with the array used.\
After the data were calibrated (Sect. [2](#sec2:sample)), we followed a two-step deconvolution procedure for imaging: ($i$) An initial deconvolution was performed with a relatively low threshold ($\sim$4.5 times the dirty noise) and without masking the emission. A reference mask was generated applying the same threshold to the image obtained in this way. ($ii$) Then, a second deconvolution cycle was performed using the mask generated in step-$i$ as starting point for the AUTO-MULTITHRESH option in TCLEAN. This two-step procedure ensures that all channels, including those with strong spatial filtering, have been properly masked.

+:-----------------------------------------+:----------------------------------------------:+:----------------------------------------------:+:----------------------------------------------:+
| Fields                                   | Band 3                                         | Band 6                                         | Band 6                                         |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
|                                          | (B3)                                           | (B6s1)                                         | (B6s2)                                         |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| $\nu$ range (GHz)                        | 85.0–89.0,                                     | 214.0–219.0,                                   | 242.5–247.5,                                   |
|                                          +------------------------------------------------+------------------------------------------------+------------------------------------------------+
|                                          | 97.0–101.0                                     | 229.0–234.0                                    | 257.2–262.5                                    |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| Configurations                           | C3-C6                                          | C1-C4                                          | C1-C4                                          |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| B$_{\rm min}$-B$_{\rm max}$              | 9–1400 m                                       | 9–1400 m                                       | 15–3600 m                                      |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| ACA                                      | No                                             | Yes                                            | Yes                                            |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| Antennas$^{(a)}$                         | 47                                             | 45–48(12)                                      | 45–48(12)                                      |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| $\Delta\nu$ (SPW-lines)                  | 59 MHz                                         | 59 MHz                                         | 59 MHz                                         |
|                                          +------------------------------------------------+------------------------------------------------+------------------------------------------------+
|                                          | $\sim$175 km s$^{-1}$                          | $\sim$75 km s$^{-1}$                           | $\sim$75 km s$^{-1}$                           |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| $\delta\nu$ (SPW-lines)                  | 61 kHz                                         | 122 kHz                                        | 122 kHz                                        |
|                                          +------------------------------------------------+------------------------------------------------+------------------------------------------------+
|                                          | $\sim$0.2 km s$^{-1}$                          | $\sim$0.17 km s$^{-1}$                         | $\sim$0.17 km s$^{-1}$                         |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| $\langle\theta_{\rm res}\rangle$$^{(c)}$ | $0.40\ensuremath{''}\times0.27\ensuremath{''}$ | $0.42\ensuremath{''}\times0.34\ensuremath{''}$ | $0.41\ensuremath{''}\times0.30\ensuremath{''}$ |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| $\langle\theta_{\rm MRS}\rangle$$^{(c)}$ | 27$\ensuremath{''}$                            | 19$\ensuremath{''}$                            | 17$\ensuremath{''}$                            |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+
| Calibrators                              | J1924-2914,                                    | J1924-2914,                                    | J1802-3940,                                    |
|                                          +------------------------------------------------+------------------------------------------------+------------------------------------------------+
|                                          | J1925-3401,                                    | J2056-4714,                                    | J1924-2914,                                    |
|                                          +------------------------------------------------+------------------------------------------------+------------------------------------------------+
|                                          | J1937-3958                                     | J1957-3845                                     | J2056-4714                                     |
+------------------------------------------+------------------------------------------------+------------------------------------------------+------------------------------------------------+

: Technical details of the FAUST observations.

Table notes: $^{(a)}$ Parenthesis refer to the number of antennas for ACA. Ranges are given when multiple execution blocks are employed; $^{(b)}$ $\Delta\nu$ and $\delta\nu$ are the typical bandwidth and spectral resolution of SPWs dedicated to line observations; $^{(c)}$ Synthesised beam ($\theta_{\rm res} = \lambda/{\rm B_{max}}$) and maximum recoverable scale ($\theta_{\rm MRS}= 0.6\:\lambda/{\rm B_{min}}$) in the combined 12 m and ACA data sets;

![](FigureA1_mom0_12m_7m_vertical.pdf)

# Additional notes and results

![](FigureB1a_channel_CH3OHs1_extcut.pdf)

![](FigureB1b_channel_H2COs1_extcut.pdf)

## Source properties at 1.3 mm

We used the 2D Gaussian fit algorithm provided by CASA ((cite: CASA_Team_22)) to analyse the 1.3 mm continuum maps (see Section [3.1](#sec3.1:cont)) and extract the properties of each source identified in the CrA cluster.\
The fitting algorithm provided the positions of the continuum peaks of each source, the intensity of the continuum peaks, $\mathcal{F}_{\rm 1.3mm}^{\rm max}$, and the integrated flux density, $\int \mathcal{F}_{\rm 1.3mm}$ d$\Omega$, over a circular region encompassing the entire 3$\sigma$ continuum emission. A summary of these parameters is presented in Table [2](#tab:continuum).

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Source-ID | $\alpha_{\rm ICRS}$ | $\delta_{\rm ICRS}$ | $\mathcal{F}_{\rm 1.3mm}^{\rm max}$ | $\int \mathcal{F}_{\rm 1.3mm}$ d$\Omega$ |
|  | hh:mm:ss.ss | dd:mm:ss.ss | mJy/beam | mJy |
| IRS7B | 19:01:56.42 | -36:57:28.58 | 190 | 304 |
| SMM 1C | 19:01:55.30 | -36:57:17.23 | 97 | 269 |
| IRS7A | 19:01:55.33 | -36:57:22.60 | 17 | 20 |
| CXO 34 | 19:01:55.79 | -36:57:28.23 | 16 | 16 |
| FAUST-5 | 19:01:56.63 | -36:57:40.49 | 4 | 4 |

: Source properties derived at 1.3 mm.

![](FigureB2_channel_SiO_cut.pdf)

![](Figure3_multipanel_spectrarc_line_2.pdf)

## Channel maps, velocity structures, and spectra

In this subsection we report the channel maps of CH$_3$OH (4$_{2,3}$-3$_{1,2}$) and p-H$_2$CO (3$_{0,3}$-2$_{0,2}$) and the integrated intensity maps of the blueshifted and redshifted components of SiO (5-4) emission, respectively, in Figures [6](#fig:channelmaps)(a,b), and [7](#fig:channel_SOSiO). The velocity structures defined by the three molecular tracers are masked at the 3$\sigma$ level. The green framed panels in Figure [6](#fig:channelmaps) indicate the systemic velocity of IRS7B, while the blue- and red-framed panels represent the blueshifted and redshifted components of the emission, respectively. The same colour code was used in Figure [7](#fig:channel_SOSiO).\
Figures [6](#fig:channelmaps)(a,b) show one velocity channel in steps of three original spectral resolution elements, while in Figure [7](#fig:channel_SOSiO) we show the integrated blueshifted and redshifted components of SiO (5-4) in the velocity ranges of $\sim$\[+6.7, +12\] km s$^{-1}$ and $\sim$\[0, +6.2\] km s$^{-1}$, respectively. Cyan lines and arrows follow Figure [1](#fig:cont_RCrA), and trace the supposed outflow cavity walls detected at 1.3 mm with ALMA (Section [4](#sec4:discussion_conclusions)). Notably, the region shown in Figure [7](#fig:channel_SOSiO) is the only part of the ALMA FoV where extended integrated SiO emission is observed.\
Figure [8](#fig:spectra) shows the spectra of all the observed lines extracted at three positions along the arc structure, centred at the peak positions of CH$_3$OH (4$_{2,3}$-3$_{1,2}$), SiO (5-4) and p-H$_2$CO (3$_{0,3}$-2$_{0,2}$), labelled A, B and C, respectively. The targeted lines are detected with a signal-to-noise ratio of $>$3$\sigma$. The exceptions are the CH$_3$OH-A (3$_{1,3}$-4$_{0,4}$) at position B and the SiO (5-4) at position C, where we derived 3$\sigma$ upper limits (Table [\[tab:line_properties\]](#tab:line_properties)). All the CH$_3$OH and H$_2$CO lines observed with a spectral resolution of $\leq$ 0.5 km s$^{-1}$ show double-peaked profiles, with the redshifted component associated with extended envelope emission, and the blueshifted one due to the arc (see Appendix [7](#app:channels)). We used the Python Spectroscopic Toolkit (PySpecKit; (cite: Ginsburg22)) to fit the spectra assuming two Gaussian components. In regions B and C, the blueshifted lines have peak velocities of $\sim$+5 km s$^{-1}$ and a narrow FWHM of $\sim$1 km s$^{-1}$. The red components are centred at +6.6 km s$^{-1}$, and have FWHMs of between 1 and 1.2 km s$^{-1}$. The low-frequency methanol lines ($E_{\rm up}$ = 22 K, and 84 K) observed with a spectral resolution of 1.54 km s$^{-1}$ show single Gaussian-like profiles. The lines peak between +5.7 and +6.3 km s$^{-1}$, close to $V^{\rm IRS7B}_{\rm sys}$. The detection of a single Gaussian line in the low-resolution data is due to the coarse spectral resolution. On the other hand, the line width of SiO at position B is $\sim 3.5$ km s$^{-1}$.\

[^1]: The lower case ‘i’ emphasises that the term ‘complex’ only applies in the context of the ISM.

[^2]: <http://faust-alma.riken.jp>; see (cite: Codella21).

[^3]: <https://help.almascience.org/index.php?/Knowledgebase/Article/View/419>

[^4]: Australia Telescope Compact Array (ATCA)

[^5]: Reduced data can be found at the Canadian Astronomy Data Centre (Project-ID: MJLSG35; <https://www.cadc-ccda.hia-iha.nrc-cnrc.gc.ca/en/search/>).

</paper>

Write the methods card for this paper.