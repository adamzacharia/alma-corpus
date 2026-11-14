# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...682A..24A\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...682A..24A",
 "title": "The ALMA Reionization Era Bright Emission Line Survey: The molecular gas content of galaxies at z 7",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Aravena, M.",
 "n_authors": 22,
 "arxiv_id": "2309.15948",
 "doi": "10.1051/0004-6361/202347281",
 "alma_projects_linked_by_archive": [
  "2019.1.01634.L"
 ]
}
```

Paper text:
<paper>
# The ALMA Reionization Era Bright Emission Line Survey

# Introduction

One of the most important advances in astrophysics in the past two decades has been the determination of the evolution of the cosmic star formation rate (SFR) density from cosmic dawn to the present time. This quantity was found to rapidly rise from $z=10$ to $z=3$ (a span of 3 Gyrs of cosmic time), reaching a plateau at $z=1-3$, and then steadily declining at $z<1$ (cite: madau14; peroux20). The cosmic SFR activity appears dominated by star-forming galaxies that grow secularly, forming a tight correlation in the SFR versus stellar mass plane, usually termed as the star-forming “main-sequence” (cite: brinchmann08; daddi07; elbaz07; elbaz11; noeske07; peng10; rodighiero10; whitaker10; whitaker14; speagle14; schreiber15; iyer18; dicesare23). These galaxies sporadically will be involved in major galaxy interactions or mergers, leading to increased SFRs (cite: kartaltepe12), and eventually will halt star formation, possibly through exhaustion of their cold gas reservoirs that sustain star formation (cite: peng10; sargent14; spilker18; belli21; williams21; bezanson19; bezanson22).

This framework for galaxy growth has been built through intensive multiwavelength observational campaigns and simulations. Determination of the molecular gas content has been paramount, as the cold gas represents the fuel for star-forming activity. Since directly observing $H_2$ molecular gas is difficult, measurements of the molecular gas mass in distant galaxies have focused on the dust continuum and the CO and \[C i\] line emission (cite: heintz20). Dedicated targeted surveys and archival searches for such dust and CO/\[C i\] line observations have led to thousands of galaxies with measured molecular gas masses (cite: daddi08; daddi10; tacconi13; tacconi18; dessauges15; dessauges17; freundlich19; scoville14; scoville17; fudamoto17; liu19; valentino18; valentino20). A complementary approach has been performing deep systematic observations of dust continuum and CO line emission in contiguous patches of the sky centered on cosmological deep fields (cite: carilli02; decarli14; walter14; walter16; aravena16b; dunlop17; pavesi18; riechers19; franco20; hatsukade18; gonzalezlopez19; gonzalezlopez20; decarli20). Such deep field surveys have the advantage of avoiding pre-selection biases compared to targeted surveys, although by design they are restricted to fainter objects. Overall, these programs have enabled establishing a set of scaling relations that allow us to describe the galaxy growth in terms of the galaxies’ stellar mass, specific SFRs, and redshift, out to $z\sim4$. In particular, current studies indicate that from $z=3$ to 1, there is an increase in the molecular gas depletion timescales, a decrease in the molecular gas fractions, and a decrease of the specific SFR. Also, the molecular gas depletion timescales decrease with increasing specific SFR (cite: tacconi20). Of particular interest has been the determination of the cosmic density of molecular gas ($\rho_{\rm H2}$) as a function of redshift from various dust continuum and CO line surveys out to $z\sim5$ (cite: walter14; decarli16a; decarli19; decarli20; riechers19; magnelli20). This quantity has been measured to closely follow the evolution of the cosmic density of SFR, supporting a relatively unchanged star formation efficiency on cosmic scales. Based on these results, it has also become evident that gas accretion from the intergalactic medium (IGM) is necessary to sustain the build-up of stellar mass in galaxies, at least since $z=1.5$ (cite: walter20).

Due to cosmic dimming, the decreasing metallicities at higher redshifts, which make the dust continuum and CO/\[C i\]line emission fainter, and the increase of the cosmic microwave background with redshift, it becomes increasingly difficult to measure the molecular gas reservoirs of galaxies at $z>4$ (cite: carilli13). Since the \[C ii\] line is among the brightest coolant lines in galaxies, and because it is redshifted into the millimeter atmospheric windows observable from the ground at $z>4$, it has thus become a powerful tool to measure the interstellar medium (ISM) properties of galaxies. Even though its emission arises from various environments, including the neutral, ionized, and molecular gas phases (cite: vallini15; pallotini17; lagache18; olsen17), it has been reliably calibrated and used as a molecular gas tracer for massive galaxies at $z<0.2$ (cite: hughes17; madden20) and at $z>2$ (cite: zanella18; vizgan22). While \[C ii\] has been traditionally used as a tracer of star formation in galaxies, the close link between star formation and molecular gas content (i.e. the Schmidt-Kennicutt relation) yields naturally a relation between \[C ii\] and molecular gas. Current studies show that \[C ii\] would even trace the molecular gas better than CO for low-metallicity environments where the gas is CO-dark, which is the case for high-redshift galaxies (cite: madden20; vizgan22).

The brightness of the \[C ii\] line has allowed for the molecular gas measurements of galaxies at z$\sim4-6$ from the Atacama Large Millimeter/submillimeter Array (ALMA) Large Program to INvestigate C$+$ at Early Times (ALPINE) survey (cite: dessauges20).

Here, we aim to extend such exploration to even higher redshifts, by using data from the Reionization Era Bright Emission Line Survey (cite: bouwens22). REBELS is an ALMA large program aimed at confirming the redshifts of a sample of 40 UV-bright star-forming galaxy candidates at $z\sim6-9$ using \[C ii\] 158 $\mu$m and \[O iii\] 88$\mu$m emission line scans of the high-probability redshift range obtained from photometric redshift measurements. REBELS has enabled studies of the properties of these early galaxies through simultaneous studies of the dust continuum and \[C ii\] emission line, including: determination of the dust properties (cite: inami22; sommovigo22; ferrara22; dayal22), the IR luminosity function (cite: barrufet23) and obscured SFR density and fractions at $z\sim7$ (cite: algera23a), measurements of the dust temperature and \[OIII\]\]/\[CII\] line ratios in a few systems (cite: algera23b), specific SFRs (cite: topping22), the discovery of inconspicuous overdensities of dusty star-forming galaxies (cite: fudamoto21), measurements of cosmic HI gas mass densities (cite: heintz22), \[CII\] sizes (cite: fudamoto22) identification of Lyman-$\alpha$ emission and velocity offsets (cite: endsley22), and a resolved study of a massive star-forming system at $z=7.3$ (cite: hygate23).

In this paper, we present molecular gas mass estimates for a sample of 28 \[C ii\]-detected star-forming galaxies at $z\sim6-8$ drawn from REBELS (cite: bouwens22) and its pilot surveys (cite: smit18; schouws22a; schouws22b). These measurements are thereby used to provide estimates of the evolution of the molecular gas depletion timescales, molecular gas ratios, and cosmic molecular gas density at $z\sim7$. In Section [2](#sec:data), we present details about the REBELS survey, the available multi-wavelength data, and comparison samples used throughout this work. In Section [3](#sec:gasestimates), we discuss the use of the \[C ii\]-based molecular gas calibration in the REBELS sample, comparing it to alternative estimates of the molecular gas content available. In Section [4](#sec:analysis), we present measurements of the molecular gas depletion timescales, gas fraction, and cosmic molecular gas density, and discuss them in the context of the established scaling relations and predicted evolution of these quantities out to $z\sim7$. In Section [5](#sec:conclusions) we provide a summary of the main results of this work. Throughout the paper, we adopt a standard $\Lambda$CDM cosmology[^1], and a (cite: chabrier03) initial mass function (IMF), with stellar masses ranging from $0.1-300\ M_\ensuremath{\odot}$.

# Data

## Observations and sample

Our study takes advantage of the \[C ii\] line emission observations in a sample of $z\sim6-8$ galaxies obtained by the ALMA REBELS large program (PID: 2019.1.01634.L). The REBELS survey details are provided in (cite: bouwens22) and Schouws et al. (in preparation). Here, we provide a brief description of the observations.

The REBELS program used line scans to search for redshifted \[C ii\] 158$\mu$m and \[O iii\]88$\mu$m lines from sources that had previously been selected as candidate $z>6$ galaxies based on their UV luminosity ($M_{\rm UV}<-21.5$ mag) and photometric redshift probability distributions ($6.5<z<9.5$), following an approach similar to the pilot programs (cite: smit18; schouws22a).

The REBELS survey targeted 40 galaxies selected from a total area of 7 deg$^2$ encompassing various deep fields (Sec. [2.2](#sec:ancillary)). Line scans searching for the \[C ii\] and \[O iii\] lines were conducted for 36 galaxies at $z\sim6.5-7.5$ and four galaxies at $z\sim8.0-9.5$ using ALMA bands 6 and 8, respectively. For each target, the scanning range was chosen to cover 90% of the relevant frequency range following the photometric redshift probability distribution.

The ALMA observations used in this study were performed in the most compact configurations, C43-1 and C43-2, yielding synthesized beam sizes of $1.2-1.6''$ in band 6. The \[CII\] line scans were performed to a sensitivity of $2\times10^8 L_\ensuremath{\odot}$ at $z=7$ (cite: bouwens22).

![](figs/REBELS_histo_new_prospector_new_normalized.png)

Data calibration was done using the Common Astronomy Software Application (CASA) software following the observatory-provided pipeline. Datacubes were thus created, inverting the calibrated visibilities with the `tclean` task and using a natural weighting scheme to maximize the sensitivity. Continuum images were obtained by collapsing the datacubes and excluding the frequency ranges that contained the \[C ii\] lines (when detected) within $2\times$FWHM$_{\rm [CII]}$. The \[C ii\] line datacube and the continuum image were searched for emission at the location of the rest-frame UV source, following the procedures detailed in Schouws et al. (in preparation) and (cite: inami22).

We obtained 23 \[C ii\] line and 16 dust continuum detections, respectively, from the first year data. In this study, we thus focus on 23 galaxies with observations of \[C ii\] line and dust continuum emission at $z\sim7$, plus additional five galaxies with \[C ii\] detections (two of them with dust detections) from the pilot studies (cite: smit18; schouws22b). We deliberately exclude \[CII\] non-detections from the analysis, as it is unclear whether they are \[CII\] faint galaxies or they are sources with redshifts falling outside the line scan covered ranges. The redshift distribution of the 28 confirmed \[C ii\] line emitters considered in this work is shown in Figure [1](#fig:distr) (left). The mean redshift of these sources is $z=6.95$, spanning a range of $z=6.50-7.68$.

## Ancillary data

The REBELS sample was drawn from various cosmological survey fields, including the COSMOS/UltraVISTA (cite: scoville07; mccracken12), UKIDSS/UDS and VIDEO/XMM-LSS (cite: jarvis13; lawrence07), CANDELS (cite: grogin11), CLASH (cite: postman12), and BoRG/HIPPIES pure-parallel (cite: trenti11; yan11). The multi-wavelength imaging of these surveys provided full optical to near-IR photometric coverage.

The available photometry and the \[C ii\]-derived spectroscopic redshifts were thus used to infer the galaxies’ physical properties, including stellar masses as described by (cite: topping22). Estimates of total SFRs was done through rest-frame UV observations from HST (cite: bouwens22) and estimates of the IR luminosities from the ALMA rest-frame $158\mu$m continuum measurements (cite: inami22).

Spectral Energy Distribution (SED) fitting for the REBELS sample was conducted using the PROSPECTOR code (cite: leja19). Two different approaches were employed: a non-parametric prescription for the galaxies’ star formation histories (SFHs) (cite: johnson21) and a constant SFH. In both methods, consistent physical assumptions were made, including sub-solar metallicities ($0.2\ Z_\odot$), a (cite: chabrier03) initial mass function (IMF) for stellar masses below $300\ M_\odot$, and a Small Magellanic Cloud (SMC) dust extinction curve (cite: topping22).

Additionally, SED fitting for the REBELS sample was performed using the BEAGLE code (cite: chevallard16) with a constant SFH (Stefanon et al., in preparation) and identical physical assumptions, except for the fitting code and stellar population templates. Some of the derived properties obtained through this procedure have been reported in (cite: bouwens22).

As elaborated in detail by (cite: topping22), the use of PROSPECTOR with a constant SFH yields results similar to those obtained by BEAGLE. However, it is known that adopting constant SFHs can result in younger age estimates for starbursting galaxies, as the starburst can dominate the signal over older stellar populations (i.e. the ‘outshining’ problem: young stellar populations outshine the old ones). In such cases, non-parametric SFHs provide greater flexibility and can help mitigate this issue (cite: algera23a). Nevertheless, these models tend to yield larger estimates of stellar masses, with an average increase of 0.43 dex compared to constant SFH models (cite: topping22). For consistency with a related parallel study of the HI mass content of REBELS galaxies (cite: heintz22), we adopt the results from PROSPECTOR with non-parametric SFHs for this work. Using this approach, the majority of the REBELS galaxies are consistent within the uncertainties with the standard star formation main-sequence extrapolated to $z=7$ (cite: algera23a). In Section [4.2.1](#sec:biases), we discuss potential biases and the effect on our results introduced by the use of these non-parametric models.

## Comparison samples

Our prime comparison sample is based on the ALPINE survey (cite: lefevre20). This survey obtained \[C ii\] emission line and dust continuum observations for a sample of 118 star-forming galaxies in the redshift range $z=4-6$ (cite: bethermin20). These galaxies were selected based on their rest-frame UV properties and the availability of rest-UV spectroscopic redshift measurements. The derived stellar masses, in the range $10^{8.4}-10^{11}\ M_\odot$, and SFRs, in the range $3-630$ $M_\odot$ yr$^{-1}$, follow the expected trend of the star-forming main sequence at $z=4-6$. The ALPINE observations yielded \[CII\] line and dust continuum detections for 75 and 23 sources, respectively, at a signal-to-noise level of 3.5. While the range of stellar masses and SFRs covered by ALPINE is similar to that of REBELS (see Fig. [1](#fig:distr)), by design, the latter did not require the existence of previous rest-UV (e.g., Ly-$\alpha$) redshift determinations.

Figure [1](#fig:distr) (middle panels) shows the distribution in stellar mass and SFR for the REBELS galaxies, compared with that of the ALPINE sample. Our current REBELS sample covers wide ranges in both parameters, with $M_{\rm stars}\sim10^{8.5}-10^{10.5}$ $M_\ensuremath{\odot}$ and SFR$\sim30-300$ $M_\ensuremath{\odot}$ yr$^{-1}$, matching the range covered by ALPINE. Figure [2](#fig:ms) shows the location of the REBELS sources in the SFR(UV+IR)–stellar mass plane, compared to the expected location of the star-forming main sequence (MS) at $z\sim5-7$, based on various prescriptions (cite: schreiber15; iyer18; khusanova21). For clarity, we split our sample into sources detected and not in 158$\mu$m dust continuum emission. Most galaxies in our sample of \[CII\] detected sources fall within the boundaries of the MS at these redshifts ($\pm0.3$ dex) compared to the widely used (cite: schreiber15) prescription for galaxies at $z=7$. However, they appear to be above the MS compared with the (cite: iyer18) prescription at $z=7$, although still within $\pm0.5$ dex.

Based on this comparison, we find that REBELS galaxies have parameter distributions similar to the ones from the ALPINE sample. We note that the REBELS galaxies were not confirmed spectroscopically through rest-UV lines (Lyman-$\alpha)$ as was the ALPINE sample, although both samples were selected based on their rest-UV brightness. Furthermore, we find that most REBELS galaxies are consistent with being in the MS and thus represent examples of massive yet “typical” star-forming galaxies at high redshift. A similar conclusion is found by a recent study by (cite: dicesare23).

At lower redshifts ($z<4$), we adopt the compilation of CO line and dust continuum measurements obtained by the IRAM Plateau de Bureau HIgh-z Blue Sequence Survey (cite: tacconi13; tacconi18; freundlich19).

The PHIBSS is a targeted survey that provides stellar masses, SFRs, and molecular gas masses (from dust and CO observations) for large samples of 1444 massive star-forming galaxies at $z=0-4$.

We complement this with similar data from the ALMA Spectroscopic Survey in the Hubble UDF (cite: walter16; aravena19; aravena20; boogaard20) and other surveys (cite: papovich16; magdis17; gowardhan19; kaasinen19; molina19; bourne19; pavesi18; cassata20). We remark that since the \[CII\] emission line is difficult to access at these lower redshifts, the molecular gas mass estimates in the comparison samples are based on observations of CO and dust continuum emission.

![](figs/REBELS_Mstar_SFR_nolog_prospector_new.png)

# Measurements of molecular gas

Several far-infrared to radio emission line and dust continuum measurements have been used as standard tracers of the molecular gas content in galaxies (cite: carilli13; hodge20). These include the CO line, particularly in the lowest energy transitions, the \[C i\] line, and dust continuum emission in the Rayleigh-Jeans regime. These tracers have provided molecular gas mass measurements in galaxies out to $z\sim3-4$. However, due to their faintness, these tracers become harder to detect at high redshifts with current facilities. Furthermore, at $z>6$, the Cosmic Microwave Background (CMB) temperature becomes comparable to the excitation temperature of the most standard tracers like CO $J<3$ and dust emission in the Rayleigh-Jeans tail (cite: dacunha13). The radiation from these tracers thus becomes almost impossible to detect against the CMB at these redshifts.

The \[C ii\] 158$\mu$m line, due to its brightness, high excitation temperature, and accessibility from the ground at the observed redshifted frequencies (due to the atmosphere transparency), has appeared as a top ISM tracer in galaxies at $z>4$. (cite: zanella18) found a correlation between the \[C ii\] luminosity and the molecular gas mass with a mean absolute deviation of 0.3 dex, and without evident systematic variations. They find a \[CII\] luminosity to molecular gas mass conversion factor $\alpha_{\rm [CII]}\simeq 30 \ (M_\ensuremath{\odot}/L_\ensuremath{\odot})$. As indicated by (cite: zanella18), the \[C ii\]-to-H2 conversion factor, $\alpha_{\rm [CII]}$, appears to be largely independent of the molecular gas depletion time, metallicity, and redshift for galaxies in the star-formation main sequence. Such correlation appears to hold for galaxies on and above the MS, in the redshift range $0<z<6$, and with metallicities 12+log(O/H)=7.9 to 8.8. A larger scatter is observed for galaxies above the MS at lower metallicities.

Similar alternative correlations have been proposed most recently, although with varied values for the \[C ii\]-to-H2 conversion factor. (cite: madden20) find $\alpha_{\rm [CII]}\simeq 130 \ (M_\ensuremath{\odot}/L_\ensuremath{\odot})$ based on local galaxy observations with mostly low metallicites, while lower values are obtained based on simulations for high redshift galaxies ($z\sim6$), $\alpha_{\rm [CII]}\simeq 10-18 \ (M_\ensuremath{\odot}/L_\ensuremath{\odot})$ (cite: pallotini17; vizgan22). The discrepant $\alpha_{\rm [CII]}$ values in these studies seem to arise from competing unaccounted CO-dark gas and low metallicity effects, respectively.

There is vast literature indicating that the \[C ii\] emission in galaxies arises from various ISM phases, including ionized, neutral, and molecular gas (cite: lagache18; ferrara19; pallotini19; dessauges20). Numerical simulations and observations have shown evidence that $>60\%$ of the \[C ii\] emission is dominated by molecular clouds and photon-dominated regions (PDRs), with a minor contribution of $20-25\%$ each from diffuse ionized and neutral gas (cite: vallini15; olsen17; katz17; katz19; pallotini17; pallotini22; vizgan22). As such, \[C ii\] can be readily calibrated as a tracer of these various phases, including star formation (cite: delooze14), neutral gas (cite: heintz21) and molecular gas (cite: zanella18; madden20). These calibrations are a likely function of stellar mass (and/or metallicities), evolutionary stage, and cosmic time. The main caveat to using \[C ii\] as a molecular gas tracer is the unknown fraction of \[C ii\] emission that arise from PDRs. However, the current results indicate that \[C ii\] is a tracer as good as others, such as CO and dust for galaxies with stellar masses $\sim10^{10}\ M_\ensuremath{\odot}$, particularly considering the need to assume an excitation ladder and a metallicity-dependent $\alpha_{\rm CO}$ conversion factor for CO measurements, and given the necessary assumption of a gas-to-dust conversion (or similar calibrations) for dust continuum based measurements.

Based on this, we measured molecular gas masses for the REBELS galaxies in our sample using Equation (2) from (cite: zanella18), and following the approach adopted for the ALPINE survey by (cite: dessauges20), $$\begin{equation}
{\rm log} (L_{\rm [CII]}) = (-1.28\pm0.21) + (0.98\pm0.02)  {\rm log}(M_{\rm{mol}})
\end{equation}$$

We thus adopt $\alpha_{\rm [CII]}\simeq30 (M_\ensuremath{\odot}/L_\ensuremath{\odot})$, with $M_{\rm{mol}}=\alpha_{\rm [CII]} L_{\rm [CII]}$. Figure [1](#fig:distr) (right) shows the distribution of molecular gas masses obtained in this way. The masses range between $10^{9}-10^{11}\ M_\ensuremath{\odot}$, comparable to the range obtained for the ALPINE sample. Evidently, this is a consequence of the constant conversion factor and the same stellar mass and SFR ranges.

Before analyzing further the implications of these molecular gas measurements, in the rest of this section, we focus on checking the \[C ii\]-based molecular gas mass estimates against other derivations provided by the available data.

![image](figs/REBELS_Lir_Mgas_CII_nolog_new.png) ![image](figs/REBELS_mdust_new.png) ![image](figs/REBELS_Mdyn_Mmol_Mstars_CII_nolog_new4_prospector_new.png)

## IR luminosity as a proxy of molecular gas mass

One of the best-established relations in extragalactic astronomy is that between the IR luminosity ($L_{\rm IR}$) and the CO(1-0) luminosity ($L'_{\rm CO}$). This has long been known to hold for a variety of galaxies and environments, from local spirals (cite: leroy08) to the most extreme starburst galaxies known through a wide range of redshifts, out to $z\sim6$ (cite: aravena16a). Following (cite: dessauges20), we convert the \[C ii\]-derived molecular gas masses ($M_{\rm mol, [CII]}$) into the expected CO(1-0) luminosities under the assumption of typical $\alpha_{\rm CO}$ values, with $L'_{\rm CO}=M_{\rm mol, [CII]}/\alpha_{\rm CO}$. The $\alpha_{\rm CO}$ is known to depend on the metallicity, although with significant scatter (cite: bolatto13), and thus a range of typical values is considered between 1.0 to 4.36 $M_\ensuremath{\odot}$ (K km s$^{-1}$)$^{-1}$.

Figure [3](#fig:checks) (left) shows the $L_{\rm IR}$ vs. $L'_{\rm CO}$ diagram for the REBELS targets compared to standard curves representing the ranges occupied by star-forming galaxies, for reference. This includes the universal fit to the compilation of CO observations for star-forming galaxies by (cite: dessauges15), along with the same line with a factor $\pm0.3$ dex added, representing the typical scatter around the fit.

We find that assuming a standard value of $\alpha_{\rm CO}=4.36$ $M_\ensuremath{\odot}$ (K km s$^{-1}$)$^{-1}$, similar to what is found in the Milky Way and main-sequence galaxies at $z\sim2$, the REBELS galaxies fall right on top of the (cite: dessauges15) curve. Variations of $\alpha_{\rm CO}$ between $2.4-6.4$ $M_\ensuremath{\odot}$ (K km s$^{-1}$)$^{-1}$ would still yield a correlation within the 0.3 dex of the $L_{\rm IR}$ vs. $L'_{\rm CO}$ relation. Conversely, using a lower $\alpha_{\rm CO}$ of 1.0 (same units), comparable to what is found in local starbursts (cite: downes98), would lead to significantly larger CO luminosities being inconsistent with the $L_{\rm IR}$ vs. $L'_{\rm CO}$ relations. Using values of $\alpha_{\rm CO}>6.4$ $M_\ensuremath{\odot}$ (K km s$^{-1}$)$^{-1}$, as expected for sub-solar metallicities for high redshift galaxies, would also lead to $L'_{\rm CO}$ values incompatible with the $L_{\rm IR}$ vs. $L'_{\rm CO}$ relation.

We note that the values of $L_{\rm IR}$ appear to have a threshold at $\sim10^{11.5} L_\ensuremath{\odot}$, which is due in part to the depth of the REBELS program. However, we caution that the REBELS $L_{\rm IR}$ values were computed using a single dust continuum measurements and realistic assumptions of the dust temperature (46 K). Warmer (or colder) dust temperatures will yield larger or lower $L_{\rm IR}$ values.

While it is not surprising to find a linear scaling between both quantities, as the \[C ii\] luminosities are known to scale with SFR, the fact that the \[C ii\]-based CO values are consistent with the known $L_{\rm IR}$-$L'_{\rm CO}$ relation supports the idea of using \[C ii\] as a molecular gas tracer in the REBELS sample.

## Dust masses

The dust content in galaxies is related to the molecular gas mass through the gas-to-dust ratio ($\delta_{\rm GDR}$). This parameter depends strongly on the galaxies’ metallicities and thus on the stellar mass through the mass-to-metallicity (MZ) relation.

Dust mass ($M_{\rm d}$) estimates for the REBELS galaxies have recently been obtained by two independent studies by (cite: ferrara22) and (cite: sommovigo22). It is thus interesting to check how well the dust masses derived by these studies relate to the \[C ii\]-based molecular gas measurements in the REBELS sample. The former constructed a semi-empirical model for dust reprocessing that uses the UV spectral slope, the observed UV continuum flux at 1500Å and the observed FIR continuum at 158$\mu$m as input parameters, and considers various extinction curves and dust geometries. The latter adopted the (cite: sommovigo21) method to derive the dust properties of galaxies based on a combination of the \[C ii\] line emission and the underlying 158$\mu$m continuum, using standard functional forms with varying normalization for the star formation law (cite: ferrara19; pallotini19) and standard assumptions for the dust properties (cite: sommovigo21; sommovigo22).

Adopting a prescription of the MZ relation (cite: genzel15)[^2] and the broken power-law form of the $\delta_{\rm GDR}$-Z relation prescribed by (cite: remy14), we find typical values of $\delta_{\rm GDR}=1000-3000$ for the stellar masses and redshifts obtained for the REBELS galaxies (median $\sim10^{9.7}\ M_\ensuremath{\odot}$, $z\sim7$). These $\delta_{\rm GDR}$ values are consistent with recent predictions for these stellar masses and redshifts, based on hydrodynamical simulations (cite: graziani20).

Figure [3](#fig:checks) (middle) shows the comparison of both $M_{\rm d}$ estimates and $M_{\rm mol, [CII]}$, in the available galaxies. We find that both dust mass estimates are consistent and linearly related to the \[C ii\]-based molecular gas mass estimates within the scatter ($\sim30\%$), suggesting $\delta_{\rm GDR}\sim1500$. While it is not surprise that our molecular gas estimates correlate well with the dust mass estimates from (cite: sommovigo22), as both use \[CII\] line information, the comparison suggest an overall consistency among the different methods and measurements, including the independent method used by (cite: ferrara22).

## Estimates from dynamical mass

An alternative way to compute the molecular gas mass is provided by considering the mass budget in each galaxy. The dynamical mass within half-light radius will be given by $M_{\rm dyn}(<r_{\rm e})=0.5(M_{\rm stars}+M_{\rm gas})+M_{\rm DM}(<r_{\rm e})$ (cite: daddi10). Assuming that the mass budget within $r_{\rm e}$ will be dominated by baryons, thus the dark matter fraction is negligible and that the ISM is dominated by the molecular gas ($M_{\rm gas}\simeq M_{\rm mol}$), we can use the dynamical and stellar masses to obtain $M_{\rm mol, dyn}$.

Unfortunately, our \[C ii\] observations can spatially resolve only mildly some of the sources, and therefore we do not have information about their resolved \[C ii\] kinematics.

For simplicity, we estimate the dynamical masses of the REBELS sources using equations 10 and 11 in (cite: bothwell13). In the first case, the gas is distributed in a virialized spherical system, e.g. a compact starburst, with $M_{\rm dyn}=1.56\times10^6 \sigma^2 R$, where $\sigma$ is the velocity dispersion ($\sigma=\Delta v_{\rm FWHM}/2.35$) and $R$ is the source radius. In the second case, the gas is distributed in a disk with $M_{\rm dyn}=4\times10^4 \Delta_{\rm FWHM}^2 R/sin(i)^2$, where $i$ is the inclination angle of the disk. In both cases, we estimate the source radius from the circularized estimate $R=\sqrt{a_{\rm maj}\times a_{\rm min}}$, where $a_{\rm maj}$ and $a_{\rm min}$ are the semi-major and semi-minor axes, respectively. We restrict the estimates on $R$ by considering only sources that have been resolved at least marginally in a given axis with a significance of 2, or $a/\delta a>2$. In unresolved cases, we consider the source to be small and simply fix their radius to 2 kpc, based on previous size measurements in galaxies at similar redshifts (cite: fujimoto20; herreracamus21) and for the REBELS sample (cite: fudamoto22). This translates into $0.36''$ at $z=7$ (or a source diameter of $\sim0.7''$), corresponding to $\sim25\%$ of the observed beam size ($1.6''$). In the disk case, we adopt a mean inclination angle sin$(i)=\pi/4\approx0.79$. The virialized spherical geometry dynamical mass estimator will yield a mass 4.4 larger than the one obtained by assuming a disk-like gas distribution for the same source size, linewidth, and an average inclination parameter.

Figure [3](#fig:checks) (right) shows the comparison between the \[C ii\]-based molecular gas mass ($M_{\rm mol, [CII]}$) and the one estimated from the dynamical and stellar masses ($M_{\rm mol, dyn-stars}$). From Fig. [1](#fig:distr) we note that the stellar masses are systematically smaller than the derived molecular gas masses and thus have little effect in this comparison. Despite the number of assumptions and uncertainties in the parameters, we find overall agreement between both molecular gas estimates in the case of the disk geometry, with most of the galaxies falling within $\pm0.3$ dex from a linear relation. In the case of virialized geometry, we find a systematic offset between the \[C ii\]  and dynamical estimates and large scatter. The reason for such large scatter is likely due to the simple geometry assumption for very complex star-forming systems at these redshifts, where most of them are not expected necessarily to be either rotating disks or fully spherical systems.

In summary, we find that all the independent checks obtained by comparing the \[C ii\]-based molecular gas mass estimates with the IR luminosity, the dust masses, and the dynamical masses are consistent and support the application of the (cite: zanella18) calibration to estimate the molecular gas mass, assuming that the molecular gas-phase dominates the baryon budget at $z>6$ (cite: heintz22; vizgan22).

# Analysis and discussion

![image](figs/REBELS_tdep_deltaMS_CII_nolog_masslim_new_prospector_new.png) ![image](figs/REBELS_fgas_deltaMS_CII_nolog_masslim_new_prospector_new.png)

The relationship between the SFR and $M_{\rm mol}$ in galaxies is usually termed the global “Schmidt-Kennicutt” (SK) relation or “star formation” law. This relationship probes how star formation activity is linked to the molecular gas supply. The ratio between the two quantities is usually called the molecular gas depletion timescale, $t_{\rm dep}=M_{\rm mol}/$SFR, which is seen as the amount of time left before the galaxy runs out of molecular gas at the current rate of star formation. Per definition, this quantity does not account for possible feedback processes in the galaxy (outflows) and interaction with the IGM (inflows). The fraction of baryonic mass in the galaxy that is in the form of molecular gas is usually described by the molecular gas fraction, $f_{\rm mol}=M_{\rm mol}/(M_{\rm mol}+M_{\rm stars})$ or as the molecular gas to stellar mass ratio, $\mu_{\rm mol}=M_{\rm mol}/M_{\rm stars}$.

Several studies in the last decade have found that these quantities are intrinsically linked to other galaxy properties such as their stellar mass, specific SFR (sSFR), and/or their distance to the star-forming main sequence at a given redshift, $\Delta_\mathrm{MS} = \mathrm{sSFR}/\mathrm{sSFR}_\mathrm{MS}(z)$, yielding the differentiation of different modes of star-formation as a function of $\Delta_{\rm MS}$ (cite: sargent14). Furthermore, $t_{\rm dep}$ and $\mu_{\rm mol}$ were found to evolve with redshift (and stellar mass). While mild evolution is observed for the average $t_{\rm dep}$ for galaxies at $z<3$, strong evolution is seen for the average $\mu_{\rm mol}$ (cite: tacconi18; liu19). Recent determinations of the molecular gas mass in galaxies from the ALPINE survey permitted extending these results to the redshift range $4-6$, indicating little evolution on the average values of both $t_{\rm dep}$ and $\mu_{\rm mol}$ from $z\sim4-6$ to $z\sim3$ (cite: dessauges20), being therefore interesting to check if similar results are found in an independent sample, and at higher redshift.

In the following, we analyze and put in context the ISM properties of the REBELS galaxies compared to previous observations of distant galaxies. The comparison samples used are briefly described in Section [2.3](#sec:samples) and in the following analysis were restricted to the stellar mass range of the REBELS sample. This filter is important for the lower redshift samples which contain a significant number of more massive galaxies.

## Scaling relations

![image](figs/REBELS_tdep_z_CII_nolog_masslim_new_prospector.png) ![image](figs/REBELS_mugas_z_CII_nolog_masslim_new_prospector.png)

Figure [4](#fig:scaling) shows the relationships formed by $t_{\rm dep}$ and $\mu_{mol}$ with $\Delta_{\rm MS}$ for the REBELS sources, compared to the samples and prescriptions in the literature for the expected scaling relations at $z=7$ (cite: tacconi18; liu19; scoville17), computed at the median stellar mass of the REBELS sample, $10^{9.5} M_\ensuremath{\odot}$ at $z=7$. We note that the (cite: scoville17) measurements provide the total ISM masses (HI and H$_2$), and thus, by construction, yield larger masses compared to molecular gas fractions only. For the MS, we use the prescription from (cite: schreiber15). We note that these prescriptions for $\mu_{mol}$, $\Delta_{\rm MS}$ and the MS correspond to extrapolations based largely on CO and dust observations of galaxy samples $z<4$, as no similar observations are available for galaxies at $z>6$.

The REBELS sample does not show a strong dependency of $t_{\rm dep}$ on $\Delta_{\rm MS}$ as opposed to lower redshift samples and expectations from scaling relations. This could be partly due to IR luminosity limits (see Fig. [3](#fig:checks)).

We find that all galaxies are consistent within the scatter with the expected low values for $t_{\rm dep}$ at these redshifts. A similar trend is followed by the ALPINE sample, indicating that this trend is not associated with sample selection. Thus, the lack of dependency on $\Delta_{\rm MS}$ is likely related to the fact that most sources fall in the MS ($\Delta_{\rm MS}\sim0$) and to the scatter in this relationship expected at high-redshift. Moreover, the location of both REBELS and ALPINE samples in the $t_{\rm dep}$ vs. $\Delta_{\rm MS}$ plane agrees well with the expectation from the (cite: tacconi18) and (cite: scoville17) relations at these redshifts.

A significant difference in the dependency of $\mu_{mol}$ with $\Delta_{\rm MS}$ is seen between the high and low redshift samples and among the various prescriptions for the scaling relations. We find that for the REBELS and ALPINE samples, $\mu_{mol}$ consistently increases with distance from the MS, as expected (i.e. galaxies that have greater SFR per unit stellar mass have larger $M_{\rm mol}$ per unit stellar mass). Furthermore, $\mu_{mol}$ values are systematically larger for the REBELS and ALPINE samples compared to galaxies at $z\sim1-3$ (i.e. galaxies at higher redshifts are richer in molecular gas) for a given stellar mass. However, a significant difference is observed when comparing the various extrapolations for scaling relations at these redshifts, being the (cite: tacconi18) prescription the one that predicts values closer to our measurements. This is similar to previous findings from (cite: dessauges20).

Overall, the REBELS (and ALPINE) galaxies mimic the scaling relation trends expected based on lower redshift samples. However, we find large discrepancies among the various models at these redshifts. This is particularly evident for the dependence of $\mu_{mol}$ on $\Delta_{\rm MS}$, where model predictions differ by nearly two orders of magnitude for MS galaxies. As mentioned earlier, an important source of uncertainty, which affects the values of $\Delta_{\rm MS}$ and $\mu_{mol}$, is the lack of sensitive constraints on the rest-frame optical SED. This will affect the stellar mass estimates and their derived uncertainties.

## Evolution of $t_{\rm dep}$ and $\mu_{\rm mol}$

Figure [5](#fig:zevol) shows the measured dependency of $t_{\rm dep}$ and $\mu_{\rm mol}$ with redshift for the REBELS sources, compared with the literature samples and prescriptions for the expected scaling relations (cite: tacconi18; liu19; scoville17) for MS galaxies with a stellar mass of $10^{9.75} M_\ensuremath{\odot}$. To check for evolutionary trends, we divided the sample into ranges of redshift, grouping the ALPINE and REBELS samples into two bins each ($4.3<z<4.7$ and $5.0<z<6.0$ for ALPINE; $6.4<z<7.0$ and $7.0<z<7.8$ for REBELS) and dividing the literature galaxy samples at lower redshifts into six bins. With this, we computed the median among all galaxies in each bin. Uncertainties in each median point taken are obtained by computing the quartile values for the subsamples in each bin. These values are found to be in excellent agreement with weighted average values for the subsamples in each bin, and with previously reported values for these mass ranges (cite: tacconi18; dessauges20).

We find that the REBELS galaxies exhibit a mild (or no) evolution of $t_{\rm dep}$ from $z=7$ to $z\sim4-6$ (and at most redshifts), as expected from previous observations and models, yielding a median $t_{\rm dep}=0.5_{-0.14}^{+0.26}$ Gyr at $z=7$, where the uncertainty corresponds to the interquartile range. Little scatter is seen among the REBELS sample, and there is an overall consistency with the (cite: tacconi18) and (cite: scoville17) prescriptions. The short $t_{\rm dep}$ values found here require that there is additional gas accretion for the next 3 Gyr to sustain the high star formation activity until $z\sim2$.

Similarly, we find a median $\mu_{\rm mol}=2.6_{-1.4}^{+4.1}$ at $z=7$, equivalent to a molecular gas fraction $f_{\rm mol}=0.73_{-0.11}^{+0.17}$. The scatter seen here is mostly due to the wide range of stellar masses of galaxies per redshift bin, since there is a strong dependence of $\mu_{\rm mol}$ on $M_{\rm stars}$ (cite: dessauges20). This scatter could also be caused by the fact that the REBELS galaxies are likely younger than lower redshift objects at matched stellar mass and thus caught at earlier stages in their assembly process, or simply because of the uncertainties in stellar mass measurements, given the lack of rest-frame optical photometry.

In this case, the scaling relation model prescriptions diverge by one order of magnitude, with the (cite: tacconi18) model being the one that agrees best with the data. Since the (cite: scoville17) measurements yield the total ISM masses (HI and H2), they yield larger gas fractions when compared to molecular gas fractions only.

### Potential effects of our adoption of stellar masses

As discussed in Section [2.2](#sec:ancillary), we have adopted stellar masses obtained through SED fitting using non-parametric SFHs as this approach helps overcome the outshining problem and for consistency with a parallel study (cite: heintz22). For the sample considered in this study, these non-parametric stellar mass estimates are on average $\sim$0.35 dex higher than those computed using parametric constant SFHs.

This selection has only a minor effect on the main conclusions drawn in this and in the previous section. The choice of non-parametric stellar masses make the REBELS galaxies mostly consistent with the star-forming main-sequence, whereas using constant SFHs yields a slightly higher fraction of starburst galaxies, or above 0.5 dex from the expected star-forming main sequence at $z\sim7$. We find that only two sources are above this threshold for non-parametric stellar masses versus 9 sources for parametric ones.

The choice of non-parametric stellar masses has little effect on the computed $\Delta_{\rm MS}$. The median $\Delta_{\rm MS}$ for non-parametric SFHs is only 0.1 dex lower than that computed with parametric constant SFHs. Similarly, our choice of stellar mass measurements does not affect the $t_{\rm dep}$ estimates; however, it has a more important effect on $\mu_{\rm mol}$. The median $\mu_{\rm mol}$ obtained for non-parametric stellar masses is a factor 2.4 lower than that obtained with parametric ones. Choosing the parametric stellar masses would still put the REBELS galaxies within the expected scaling relations in the log($\mu_{\rm mol}$) vs. $\Delta_{\rm MS}$ plot (Fig. [4](#fig:scaling)). However, they would now be more consistent with the (cite: liu19) prescription for $\mu_{\rm mol}$ at $z=7$. This would be in contradiction to the consistently low value of $t_{\rm dep}$ at $z\sim7$, which is consistent with the prescription of (cite: tacconi20).

## Cosmic density of molecular gas

Great observational efforts have been made in recent years to measure the CO luminosity function (LF) at different redshifts and, thereby, the cosmic density of molecular gas $\rho_{\rm mol}$. Initial attempts to measure the CO LF at high redshift were done with the Very Large Array (VLA) in an overdense field at $z\sim1.5$ (cite: aravena12). However, the first dedicated survey for this purpose used the IRAM Plateau de Bureau Interferometer (PdBI) to perform a spectral scan over frequency and thus conduct a blind search for CO line emission in the *Hubble* Deep Field North (cite: walter14; decarli14). Later on, CO line and dust continuum surveys with ALMA were performed to this end in the *Hubble* UDF, including the ASPECS pilot (cite: walter16; aravena16b; aravena16c; decarli16a) and large programs (cite: decarli19; gonzalezlopez20; aravena19; aravena20; decarli20; boogaard20). Similar efforts were done with the VLA through the CO Luminosity Density at High-Redshift (COLDz) survey (cite: riechers19) covering larger areas at shallower depths for lower-J CO transitions. A parallel approach has taken advantage of targeted CO and dust continuum surveys, as each independently observed pointing would essentially yield a portion of a cosmological deep field, and combining it with statistical methods to assess the completeness and compute the cosmological volumes covered. This yielded estimates for the CO LF from the PHIBSS (cite: lenkic20), A3COSMOS (cite: liu19), and the ALMACAL surveys (cite: klitsch19). Similar estimates have been obtained from dust continuum observations (cite: scoville17; magnelli20), and most recently using the ALPINE \[C ii\] survey (cite: yan20).

![](figs/REBELS_rhoH2_new.png)

It is interesting to compare these measurements with the value of $\rho_{\rm mol}$ at $z=6.5-7.5$ from the REBELS survey. Following previous studies (cite: yan20; heintz21; heintz22), we compute $\rho_{\rm mol}$ from the \[C ii\] luminosity density, $\mathcal{L}$, obtained for galaxies at $z\approx7$ from the REBELS survey by Oesch et al. (in preparation). In this study, the \[C ii\] luminosity density is found by integrating the \[C ii\] luminosity function down to a limit of log($L_{\rm [CII], lim})=7.5$, as $\mathcal{L}={\int_{\rm [CII], lim}^{\infty} L_{\rm [CII]} \phi(L_{\rm [CII]}) \,dL}$, where $\phi(L_{\rm [CII]})$ is the \[C ii\] LF . The latter is obtained from the UV LF (cite: bouwens21), using an empirical $L_{\rm [CII]}-L_{\rm UV}$ relation, derived for galaxies at the same redshift (cite: barrufet23). With this, we obtain a \[C ii\] luminosity density log($\mathcal{L}/[L_\ensuremath{\odot} {\rm Mpc}^{-3}])=4.85^{+0.25}_{-0.20}$ for the REBELS sample. Now, this can be converted to a molecular gas mass density using the calibration described above, $\alpha_{\rm [CII]}\approx30 \, M_\ensuremath{\odot} \, L_\ensuremath{\odot}^{-1}$ (cite: zanella18), yielding log($\rho_{\rm mol}/({\rm M}_\ensuremath{\odot} \, {\rm Mpc}^{-3}))=6.34_{-0.31}^{+0.34}$ at $z=6.5-7.5$. This result includes the uncertainties associated with the $\alpha_{\rm [CII]}$ calibration (cite: zanella18). For the ALPINE data, we use the updated calculations of the \[C ii\] luminosity density from (cite: heintz22).

Figure [6](#fig:rhoh2) shows the result of this comparison. The measurements obtained from the different methods and tracers agree that $\rho_{\rm mol}$ resembles the evolution of the cosmic SFR density (cite: decarli20), although the studies by A3COSMOS (cite: liu19) and (cite: scoville17) find different normalizations.

However, the few measurements obtained at $z\sim4-6$, including the PHIBSS (cite: lenkic20) and COLDz (cite: riechers19) CO-based and the ALPINE \[C ii\] based estimates (cite: yan20; heintz22), appear to agree, indicating a continuous decline of $\rho_{\rm mol}$ at increasing redshifts. The REBELS measurements agree with the trend of $\rho_{\rm mol}$ declining at higher redshifts. These results indicate that $\rho_{\rm mol}$ increases by an order of magnitude from $z\sim7$ to $z\sim4$, and that beyond $z=6$, the values of $\rho_{\rm mol}$ reach levels similar and below the current $\rho_{\rm mol}$ (at $z=0$) of log($\rho_{\rm mol}/({\rm M}_\ensuremath{\odot} \, {\rm Mpc}^{-3}))\sim 7$.

# Conclusions

We present molecular gas mass estimates and properties for the sample of galaxies at $z\sim7$ unveiled by the REBELS large program survey, using the \[C ii\] line emission as a proxy for the molecular ISM. The main conclusions of this study are as follows.

1.  Comparison of the \[C ii\]-based molecular gas mass estimates with independent estimates and proxies, including the IR luminosity (as a proxy for the molecular gas mass through the $L_{\rm IR}-L'_{\rm CO}$ relation), dust masses, and dynamical mass estimates yield reasonable agreement when applied to the REBELS sample at $z\sim7$. Furthermore, the matched stellar mass and SFR distributions of REBELS and ALPINE surveys suggest that the calibrations to obtain $M_{\rm mol}$ from $L_{\rm [CII]}$ apply for massive main-sequence galaxies at $z\sim7$ and $z\sim4-6$.

2.  The molecular to stellar mass ratios ($\mu_{\rm mol}$) and molecular gas depletion timescales ($t_{\rm dep}$) appear to follow the standard scaling relations with distance to the main sequence $\Delta_{\rm MS}$ for REBELS galaxies at $z\sim7$. While $\mu_{\rm mol}$ increases toward larger $\Delta_{\rm MS}$, $t_{\rm dep}$ is observed to stay relatively constant. The location of the REBELS galaxies at $z\sim7$ in these plots agrees with the regions occupied by ALPINE galaxies and the distant end of lower redshift samples at matched stellar masses.

3.  The median $t_{\rm dep}$ and $\mu_{\rm mol}$ stay almost constant in the range $z\sim2-7$ for galaxies with stellar masses $10^{8.5-10.5}\ M_\ensuremath{\odot}$.

4.  We measure a value of the cosmic density of molecular gas at $z=6.5-7.5$ of log($\rho_{\rm mol}/({\rm M}_\ensuremath{\odot} \, {\rm Mpc}^{-3}))=6.34_{-0.31}^{+0.34}$, indicating an increase of an order of magnitude from $z\sim7$ to $z\sim4$.

The advent of infrared facilities such as the JWST and Roman will allow us to explore samples of hundreds to thousands of galaxies at $z>6$, opening the study of the formation processes of galaxies through the end of the epoch of reionization. Investigating the cold ISM of such early galaxies will require observations with submillimeter facilities as ALMA. However, due to the dimming of traditional ISM tracers such as CO line and dust continuum emission due to cosmological distances, lower metallicities, and increasingly low-contrast to the cosmic microwave background at higher redshift (cite: dacunha13), measurements of the ISM gas content (a key ingredient to study the galaxy assembly) will be increasingly difficult. The \[C ii\] line emission has therefore come to save the day, enabling relatively accurate measurements of $M_{\rm mol}$ for massive systems in the early universe. Calibration of the \[C ii\] line for larger samples of galaxies, as well as other fine-structure lines, will be essential for future galaxy formation studies.

# Acknowledgements

We thank the anonymous referee for their constructive feedback that helped improve this paper. We thank Roberto Decarli for the useful discussions and for providing the cosmic density literature measurements. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01634.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. M.A. acknowledges support from FONDECYT grant 1211951, ANID+PCI+INSTITUTO MAX PLANCK DE ASTRONOMIA MPG 190030, ANID+PCI+REDES 190194 and ANID BASAL project FB210003. HI and HSBA acknowledge support from the NAOJ ALMA Scientific Research Grant Code 2021-19A.PD acknowledges support from the NWO grant 016.VIDI.189.162 (“ODIN") and from the European Commission’s and University of Groningen’s CO-FUND Rosalind Franklin program. PD also warmly thanks the Institute for Advanced Study (IAS) Princeton, where a part of this work was carried out, for their generous hospitality and support through the Bershadsky Fund.

132 natexlab

(ref: algera23b) Algera, H., Inami, H., Sommovigo, L., et al. 2023a, arXiv e-prints, arXiv:2301.09659

(ref: algera23a) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023b, MNRAS, 518, 6142

(ref: aravena20) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, ApJ, 901, 79

(ref: aravena12) Aravena, M., Carilli, C. L., Salvato, M., et al. 2012, MNRAS, 426, 258

(ref: aravena19) Aravena, M., Decarli, R., Gónzalez-López, J., et al. 2019, ApJ, 882, 136

(ref: aravena16c) Aravena, M., Decarli, R., Walter, F., et al. 2016a, ApJ, 833, 71

(ref: aravena16b) Aravena, M., Decarli, R., Walter, F., et al. 2016b, ApJ, 833, 68

(ref: aravena16a) Aravena, M., Spilker, J. S., Bethermin, M., et al. 2016c, MNRAS, 457, 4406

(ref: barrufet23) Barrufet, L., Oesch, P. A., Bouwens, R., et al. 2023, MNRAS, 522, 3926

(ref: belli21) Belli, S., Contursi, A., Genzel, R., et al. 2021, ApJL, 909, L11

(ref: bethermin20) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: bezanson19) Bezanson, R., Spilker, J., Williams, C. C., et al. 2019, ApJL, 873, L19

(ref: bezanson22) Bezanson, R., Spilker, J. S., Suess, K. A., et al. 2022, ApJ, 925, 153

(ref: bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: boogaard20) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109

(ref: bothwell13) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047

(ref: bourne19) Bourne, N., Dunlop, J. S., Simpson, J. M., et al. 2019, MNRAS, 482, 3135

(ref: bouwens21) Bouwens, R. J., Oesch, P. A., Stefanon, M., et al. 2021, AJ, 162, 47

(ref: bouwens22) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160

(ref: brinchmann08) Brinchmann, J., Pettini, M., & Charlot, S. 2008, MNRAS, 385, 769

(ref: carilli02) Carilli, C. L. & Blain, A. W. 2002, ApJ, 569, 605

(ref: carilli13) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: cassata20) Cassata, P., Liu, D., Groves, B., et al. 2020, ApJ, 891, 83

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: chevallard16) Chevallard, J. & Charlot, S. 2016, MNRAS, 462, 1415

(ref: dacunha13) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: daddi10) Daddi, E., Bournaud, F., Walter, F., et al. 2010, ApJ, 713, 686

(ref: daddi08) Daddi, E., Dannerbauer, H., Elbaz, D., et al. 2008, ApJL, 673, L21

(ref: daddi07) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156

(ref: dayal22) Dayal, P., Ferrara, A., Sommovigo, L., et al. 2022, MNRAS, 512, 989

(ref: delooze14) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: decarli20) Decarli, R., Aravena, M., Boogaard, L., et al. 2020, ApJ, 902, 110

(ref: decarli16a) Decarli, R., Walter, F., Aravena, M., et al. 2016, ApJ, 833, 69

(ref: decarli14) Decarli, R., Walter, F., Carilli, C., et al. 2014, ApJ, 782, 78

(ref: decarli19) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138

(ref: dessauges20) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5

(ref: dessauges17) Dessauges-Zavadsky, M., Zamojski, M., Rujopakarn, W., et al. 2017, A&A, 605, A81

(ref: dessauges15) Dessauges-Zavadsky, M., Zamojski, M., Schaerer, D., et al. 2015, A&A, 577, A50

(ref: dicesare23) Di Cesare, C., Graziani, L., Schneider, R., et al. 2023, MNRAS, 519, 4632

(ref: downes98) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615

(ref: dunlop17) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861

(ref: elbaz07) Elbaz, D., Daddi, E., Le Borgne, D., et al. 2007, A&A, 468, 33

(ref: elbaz11) Elbaz, D., Dickinson, M., Hwang, H. S., et al. 2011, A&A, 533, A119

(ref: endsley22) Endsley, R., Stark, D. P., Bouwens, R. J., et al. 2022, MNRAS, 517, 5642

(ref: ferrara22) Ferrara, A., Sommovigo, L., Dayal, P., et al. 2022, MNRAS, 512, 58

(ref: ferrara19) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1

(ref: franco20) Franco, M., Elbaz, D., Zhou, L., et al. 2020, A&A, 643, A30

(ref: freundlich19) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2019, A&A, 622, A105

(ref: fudamoto17) Fudamoto, Y., Ivison, R. J., Oteo, I., et al. 2017, MNRAS, 472, 2028

(ref: fudamoto21) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489

(ref: fudamoto22) Fudamoto, Y., Smit, R., Bowler, R. A. A., et al. 2022, ApJ, 934, 144

(ref: fujimoto20) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1

(ref: genzel15) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: gonzalezlopez19) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139

(ref: gonzalezlopez20) González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91

(ref: gowardhan19) Gowardhan, A., Riechers, D., Pavesi, R., et al. 2019, ApJ, 875, 6

(ref: graziani20) Graziani, L., Schneider, R., Ginolfi, M., et al. 2020, MNRAS, 494, 1071

(ref: grogin11) Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, ApJS, 197, 35

(ref: hatsukade18) Hatsukade, B., Kohno, K., Yamaguchi, Y., et al. 2018, PASJ, 70, 105

(ref: heintz22) Heintz, K. E., Oesch, P. A., Aravena, M., et al. 2022, ApJL, 934, L27

(ref: heintz20) Heintz, K. E. & Watson, D. 2020, ApJL, 889, L7

(ref: heintz21) Heintz, K. E., Watson, D., Oesch, P. A., Narayanan, D., & Madden, S. C. 2021, ApJ, 922, 147

(ref: herreracamus21) Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649, A31

(ref: hodge20) Hodge, J. A. & da Cunha, E. 2020, Royal Society Open Science, 7, 200556

(ref: hughes17) Hughes, T. M., Ibar, E., Villanueva, V., et al. 2017, A&A, 602, A49

(ref: hygate23) Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS \[\]

(ref: inami22) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126

(ref: iyer18) Iyer, K., Gawiser, E., Davé, R., et al. 2018, ApJ, 866, 120

(ref: jarvis13) Jarvis, M. J., Bonfield, D. G., Bruce, V. A., et al. 2013, MNRAS, 428, 1281

(ref: johnson21) Johnson, B. D., Leja, J., Conroy, C., & Speagle, J. S. 2021, ApJS, 254, 22

(ref: kaasinen19) Kaasinen, M., Scoville, N., Walter, F., et al. 2019, ApJ, 880, 15

(ref: kartaltepe12) Kartaltepe, J. S., Dickinson, M., Alexander, D. M., et al. 2012, ApJ, 757, 23

(ref: katz19) Katz, H., Galligan, T. P., Kimm, T., et al. 2019, MNRAS, 487, 5902

(ref: katz17) Katz, H., Kimm, T., Sijacki, D., & Haehnelt, M. G. 2017, MNRAS, 468, 4831

(ref: khusanova21) Khusanova, Y., Bethermin, M., Le Fèvre, O., et al. 2021, A&A, 649, A152

(ref: klitsch19) Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2019, MNRAS, 490, 1220

(ref: lagache18) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: lawrence07) Lawrence, A., Warren, S. J., Almaini, O., et al. 2007, MNRAS, 379, 1599

(ref: lefevre20) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: leja19) Leja, J., Carnall, A. C., Johnson, B. D., Conroy, C., & Speagle, J. S. 2019, ApJ, 876, 3

(ref: lenkic20) Lenkić, L., Bolatto, A. D., Förster Schreiber, N. M., et al. 2020, AJ, 159, 190

(ref: leroy08) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: liu19) Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235

(ref: madau14) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: madden20) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141

(ref: magdis17) Magdis, G. E., Rigopoulou, D., Daddi, E., et al. 2017, A&A, 603, A93

(ref: magnelli20) Magnelli, B., Boogaard, L., Decarli, R., et al. 2020, ApJ, 892, 66

(ref: mccracken12) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156

(ref: molina19) Molina, J., Ibar, E., Smail, I., et al. 2019, MNRAS, 487, 4856

(ref: noeske07) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43

(ref: olsen17) Olsen, K., Greve, T. R., Narayanan, D., et al. 2017, ApJ, 846, 105

(ref: pallotini17) Pallottini, A., Ferrara, A., Bovino, S., et al. 2017, MNRAS, 471, 4128

(ref: pallotini19) Pallottini, A., Ferrara, A., Decataldo, D., et al. 2019, MNRAS, 487, 1689

(ref: pallotini22) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621

(ref: papovich16) Papovich, C., Labbé, I., Glazebrook, K., et al. 2016, Nature Astronomy, 1, 0003

(ref: pavesi18) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49

(ref: peng10) Peng, Y.-j., Lilly, S. J., Kovač, K., et al. 2010, ApJ, 721, 193

(ref: peroux20) Péroux, C. & Howk, J. C. 2020, ARA&A, 58, 363

(ref: postman12) Postman, M., Coe, D., Benı́tez, N., et al. 2012, ApJS, 199, 25

(ref: remy14) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31

(ref: riechers19) Riechers, D. A., Pavesi, R., Sharon, C. E., et al. 2019, ApJ, 872, 7

(ref: rodighiero10) Rodighiero, G., Cimatti, A., Gruppioni, C., et al. 2010, A&A, 518, L25

(ref: sargent14) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19

(ref: schouws22b) Schouws, S., Stefanon, M., Bouwens, R., & al, e. 2022a, ApJ, 999, 9

(ref: schouws22a) Schouws, S., Stefanon, M., Bouwens, R., et al. 2022b, ApJ, 928, 31

(ref: schreiber15) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74

(ref: scoville07) Scoville, N., Abraham, R. G., Aussel, H., et al. 2007, ApJS, 172, 38

(ref: scoville14) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84

(ref: scoville17) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150

(ref: smit18) Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178

(ref: sommovigo21) Sommovigo, L., Ferrara, A., Carniani, S., et al. 2021, MNRAS, 503, 4878

(ref: sommovigo22) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122

(ref: speagle14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: spilker18) Spilker, J., Bezanson, R., Barišić, I., et al. 2018, ApJ, 860, 103

(ref: tacconi18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: tacconi20) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: topping22) Topping, M. W., Stark, D. P., Endsley, R., et al. 2022, MNRAS, 516, 975

(ref: trenti11) Trenti, M., Bradley, L. D., Stiavelli, M., et al. 2011, ApJL, 727, L39

(ref: valentino18) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: valentino20) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24

(ref: vallini15) Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36

(ref: vizgan22) Vizgan, D., Greve, T. R., Olsen, K. P., et al. 2022, ApJ, 929, 92

(ref: walter20) Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111

(ref: walter16) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67

(ref: walter14) Walter, F., Decarli, R., Sargent, M., et al. 2014, ApJ, 782, 79

(ref: whitaker14) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104

(ref: whitaker10) Whitaker, K. E., van Dokkum, P. G., Brammer, G., et al. 2010, ApJ, 719, 1715

(ref: williams21) Williams, C. C., Spilker, J. S., Whitaker, K. E., et al. 2021, ApJ, 908, 54

(ref: yan11) Yan, H., Yan, L., Zamojski, M. A., et al. 2011, ApJL, 728, L22

(ref: yan20) Yan, L., Sajina, A., Loiacono, F., et al. 2020, ApJ, 905, 147

(ref: zanella18) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

[^1]: $H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}= 0.3$ and $\Omega_\Lambda=0.7$

[^2]: We adopt this prescription as it is widely used in similar studies at high redshift, as in (cite: tacconi18).

</paper>

Write the methods card for this paper.