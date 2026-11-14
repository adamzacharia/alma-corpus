# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...700A.141H\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...700A.141H",
 "title": "Statistical nuclear spin ratios of deuterated ammonia in the pre-stellar core L1544",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Harju, J.",
 "n_authors": 9,
 "arxiv_id": "2507.04825",
 "doi": "10.1051/0004-6361/202555336",
 "alma_projects_linked_by_archive": [
  "2016.1.00240.S"
 ]
}
```

Paper text:
<paper>
# Statistical nuclear spin ratios of deuterated ammonia in the pre-stellar core L1544 [^1]

The relative abundances of the nuclear spin modifications of molecules contain information on their formation mechanism. We determined the ortho/para (o/p) ratios of $\rm NH_2D$ and $\rm NHD_2$ in the archetypical pre-stellar core L1544. L1544 was observed in the two lowest rotational lines of ortho- and para-$\rm NH_2D$ using the Atacama Pathfinder EXperiment (APEX) and the IRAM 30 m telescopes. The ground-state lines of ortho- and para-$\rm NHD_2$ were observed with APEX. The distributions of chemical abundances in the core were predicted using a gas-grain chemistry model with two different scenarios concerning proton transfer reactions in the gas. One of the scenarios, the so-called full scrambling (FS), allows protons and deuterons to be completely mixed in the intermediate reaction complex before dissociation, whereas the other describes these reactions as proton or deuteron hops (PH). We also tested assumed abundance profiles independent of the chemistry models. Radiative transfer calculations were used to simulate the observed $\rm NH_2D$ and $\rm NHD_2$ lines from the predicted and assumed abundance profiles. Our modelling efforts suggest that the ground-state lines of $\rm NH_2D$ and $\rm NHD_2$ at the wavelength $\lambda=0.9$ mm that are observable with the same beam and in the same spectrometer band are the most reliable probes of the o/p ratios. Simulations using the PH reaction scheme show systematically better agreement with the observations than simulations with the FS model. Simulations using a broken power law abundance profile as a function of the gas density, which seems to agree with previous observations and models, give spin ratios that are close to the predictions of the PH scenario: o/p-$\rm NH_2D=2.85\pm0.05$, o/p-$\rm NHD_2=2.10\pm0.06$ ($1\,\sigma$). The o/p ratios predicted by the PH scenario in the gas phase correspond to the nuclear spin statistical weights, that is, o/p-$\rm NH_2D=3$, o/p-$\rm NHD_2=2$. In view of the fact that H and D atom addition reactions on grain surfaces also result in these ratios, it is reasonable to assume that the spin ratios of interstellar ammonia and its deuterated forms are in general equal to their statistical values.

# Introduction

Ammonia and its deuterated isotopologues are frequently used as probes of physical and chemical conditions in dense interstellar clouds through their rotation-inversion spectra at centimetre and millimetre wavelengths. These molecules contain two or three identical protons (fermions) or deuterons (bosons), and the symmetrisation postulate of quantum mechanics imposes certain restrictions on their complete internal wave functions, which describe the quantum state of an isolated molecule, including the electronic and rotational-vibrational states as well as the electronic and nuclear spins. For example, the complete internal wave function of $\rm NH_2D$ must change sign under the permutation of the two protons, while that of $\rm NHD_2$ must remain unchanged by the interchange of the two deuterons. $\rm NH_2D$ and $\rm NHD_2$ have both symmetric and anti-symmetric nuclear spin wave functions, and to comply with the symmetrisation postulate, these can only be associated with certain rotation-inversion states. The restrictions described above give rise to different nuclear spin modifications of $\rm NH_3$, $\rm NH_2D$, $\rm NHD_2$, and $\rm ND_3$, which can be treated as different chemical species. It is customary to use the Greek appellation ‘ortho’ for the modification with the highest nuclear spin statistical weight (number of symmetrised nuclear spin functions that have appropriate symmetry) and ‘para’ for the modification with the lowest weight. $\rm ND_3$ has a third symmetry species called ‘meta’ (e.g. (cite: bunker&jensen2005); (cite: 2009JChPh.130p4302H); (cite: 2016MNRAS.457.1535D)).

Chemical models that distinguish between different spin species indicate that their relative abundances do not necessarily correspond to the nuclear spin statistical weights. Deviations from the statistical weights originate in chemical reactions that form ammonia if they proceed through an intermediate reaction complex where protons and deuterons can be completely mixed. The possible spin states of the reaction complex and the dissociation products are determined by selection rules that derive from the conservation of spin angular momentum and permutation symmetry ((cite: 2009JChPh.130p4302H); (cite: 2015A&A...581A.122S); (cite: 2016JChPh.145g4301S); (cite: 2018MNRAS.477.4454H)). A practical reason to have a priori knowledge of the spin ratios is that it is not always easy to determine the abundances of all the spin modifications of a molecule and thus its total abundance directly from observations. For example, the fundamental transitions of ortho-$\rm NH_3$ and ortho-$\rm ND_3$ are at unfavourable frequencies (572 and 615 GHz, respectively) for ground-based observations. The former line has been observed in the pre-stellar core L1544 with *Herschel* but is difficult to interpret due to self-absorption (cite: 2017A&A...603L...1C). Deviations from the statistical ortho/para (o/p) ratios of water and ammonia (the latter derived from NH$_2$) have been reported in comets ((cite: 2011ARA&A..49..471M); (cite: 2016MNRAS.462S.124S)). These were previously thought to reflect the temperatures at which the ices in the comet nucleus were formed or condensed. Currently, the idea that possible deviations from statistical ratios are caused by gas-phase reactions in comae is perhaps more favoured ((cite: 2013ApJ...770L...2F); (cite: 2018ApJ...857L..13H); (cite: 2019MNRAS.487.3392F)). Experimental and theoretical studies suggest that water desorbing from cometary nuclei should have a statistical o/p ratio of 3 ((cite: 2018ApJ...857L..13H); (cite: 2022A&A...663A..43C) and references therein). A couple of recent observational estimates for cometary comae find no significant deviation from this value when optical thickness effects are carefully taken into account ((cite: 2022A&A...663A..43C); (cite: 2025PSJ.....6..139W)).

We have previously determined the o/p ratios of $\rm NH_2D$ and $\rm NHD_2$ in two pre-stellar cores in Ophiuchus, H-MM1 and Oph D, using the Large APEX sub-Millimeter Array (LAsMA) multi-beam receiver of the Atacama Pathfinder EXperiment (APEX) telescope (cite: 2024A&A...682A...8H). These observations show, with a higher accuracy than previously achieved, that the mentioned spin ratios are within $20\%$ (taking $3\,\sigma$ limits into account) of their high-temperature statistical values, 3 and 2, respectively. The results were explained by a chemistry model that assumes the proton hop (PH) mechanism (see e.g. (cite: 2004JMoSp.228..635O)) in proton transfer and hydrogen abstraction reactions that contribute to the formation of ammonia (cite: 2019A&A...631A..63S). The alternative to PH is the so-called full scrambling (FS) mechanism, in which chemical reactions proceed via the formation of a relatively long-lived intermediate complex, where the light H and D nuclei can be mixed. According to our tests with both the PH and FS scenarios, the efficiency of ammonia desorption from grains does not affect its spin ratios in the gas. The insensitivity to the desorption rate was explained by a rapid reprocessing of released material in ion-molecule reactions, and this was considered to rule out the possibility that statistical spin ratios are caused by formation on grains. In contrast to PH, the FS model predicts clear deviations from the statistical spin ratios. In FS simulations, the o/p-$\rm NH_2D$ ratio generally decreases well below 3 or even below 2 in the gas, and o/p-$\rm NHD_2$ always stays clearly above 2 ((cite: 2015A&A...581A.122S); (cite: 2018MNRAS.477.4454H)).

The Ophiuchus molecular cloud complex, where H-MM1 and Oph D are located, is exposed to strong radiation from the Sco OB2 association and local B stars (e.g. (cite: 2020A&A...638A..74L); (cite: 2022A&A...667A.163M)), and it is possible that the formation history and external conditions of the two cores have affected their composition in a way that current chemistry models cannot account for. Therefore, it seems helpful to repeat the measurement of the spin ratios in a quiescent environment. To this end, we present observations of the ortho and para modifications of $\rm NH_2D$ and $\rm NHD_2$ towards the pre-stellar core L1544, which lies on the outskirts of the Taurus molecular cloud complex, far from strong sources of radiation and stellar winds. The core is characterised by a high central density ($n(\rm H_2)>10^6\,\rm cm^{-3}$) and a low central temperature ($\sim7$ K; e.g., (cite: 2007A&A...470..221C); (cite: 2019ApJ...874...89C); (cite: 2022ApJ...929...13C)). An additional motivation for observing L1544 is that the column densities of ortho- and para-$\rm NH_2D$ ($\rm oNH_2D$ and $\rm pNH_2D$) derived in the spectroscopic survey of (cite: 2021JMoSp.37711431M) indicate an o/p-$\rm NH_2D$ ratio of $2.31\pm0.11$, which would agree with the predictions of FS models. This o/p ratio was derived from the ortho- and para-lines at 85.9 GHz and 110.2 GHz ($\lambda \sim 3.5$ and $2.7$ mm) and includes uncertainty caused by the different beam sizes and the different Einstein coefficients and critical densities of the two transitions. To confirm the low o/p-$\rm NH_2D$ ratio, and to also determine the o/p-$\rm NHD_2$ ratio in this object, we observed the ground-state lines of both species at $\lambda\sim0.9$ mm with APEX/LAsMA, and combined these with lines of the same molecules around $\lambda=3$ mm, obtained with the 30 m telescope of the Institut de radioastronomie millimétrique (IRAM).

# Observations

(80,80)(0,0) (-15,0)

(0,0) ![image](L1544_spitzer.ps)

## APEX

The ground-state rotational lines of $\rm oNH_2D$, $\rm pNH_2D$, ortho-$\rm NHD_2$ ($\rm oNHD_2$), and para-$\rm NHD_2$ ($\rm pNHD_2$) near 333 and 335 GHz were observed towards L1544 with the LAsMA array (cite: 2008SPIE.7020E..10G) on the APEX telescope (cite: 2006A&A...454L..13G). The observations were made in August 2023, under project number M-0112.F-9506A-2023. These were single-point position switching observations with the central pixel of LAsMA pointed at the column density peak of L1544 (RA $05^{\rm h}04^{\rm m}17.1s$, Dec. $+25\ensuremath{^\circ}10\ensuremath{'}43\ensuremath{''}$ (J2000.0)). The reference position (OFF) was selected $10\ensuremath{'}$ to the equatorial east of the ON position. The array has 7 pixels separated by approximately $40\ensuremath{''}$. Figure [1](#lasma_footprint) shows the footprint of the instrument superposed on the $8\,\mu$m map of the core measured by the InfraRed Array Camera (IRAC) of the Spitzer Space Telescope. The beam size of APEX is $18.7\ensuremath{''}$ (full width at half maximum) at 333 GHz. The 12 m APEX telescope is located at an altitude of 5100 m at Llano de Chajnantor in Chile.

The backend was composed of fast Fourier transform spectrometers (FFTSs; called the FFTS4G) that covered two 4 GHz intermediate frequency bands resolved into 65 536 spectral channels of width 61.03 kHz (corresponding to $\sim 55\,\rm m\,s^{-1}$). Lines of ortho- and para-$\rm NH_2D$ and $\rm NHD_2$ were observed in the lower sideband of the receiver, which was centred at 334.145 GHz. The frequencies of the observed transitions are listed in Table [1](#transitions). The energies of the upper transition level and the critical densities, $n_{\rm crit}$, of the transitions are also listed. Spectroscopic data were taken from (cite: 2021JMoSp.37711431M). The (de)excitation rate coefficients for $\rm NH_2D$ and $\rm NHD_2$ in collisions with $\rm H_2$ were adopted from (cite: 2014MNRAS.444.2544D) and (cite: 2016MNRAS.457.1535D).

The critical densities in Table [1](#transitions) were estimated at 10 K, using the optically thin formula presented by Shirley ((cite: 2015PASP..127..299S), Eq. (4)). This formula takes into account all collisionally induced transitions starting from the upper transition level of the emission line. In addition to the downward collisions to the lower transition level, it is primarily the collisions $1_{01}\rightarrow1_{11}$ and $1_{11}-0_{00}$ that affect the critical densities of the $1_{01}\rightarrow0_{00}$ and $1_{11}\rightarrow1_{01}$ emission lines of $\rm oNH_2D$ and $\rm pNH_2D$. For $\rm oNHD_2$ and $\rm pNHD_2$, the collisions $1_{11}\rightarrow1_{01}$ compete with collisions $1_{11}\rightarrow0_{00}$, which correspond to the observed ground-state lines.

+------------------------------------------------+-----------------+-----------------+------------------------------------+
| Transition                                     | Freq. (MHz)$^a$ | $E_{\rm u}$ (K) | $n_{\rm crit}$ ($\rm cm^{-3}$)$^b$ |
+:=============+:================================+================:+:================+:===================================+
|              |                                 |                 |                 |                                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
| $\rm oNH_2D$ | $1_{01}^{\rm a}-0_{00}^{\rm a}$ | 332781.803      | 16.6            | $7.1\times10^4$                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
| $\rm pNH_2D$ | $1_{01}^{\rm s}-0_{00}^{\rm s}$ | 332822.521      | 16.0            | $6.6\times10^4$                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
| $\rm oNHD_2$ | $1_{11}^{\rm s}-0_{00}^{\rm s}$ | 335513.715      | 16.1            | $7.4\times10^4$                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
| $\rm pNHD_2$ | $1_{11}^{\rm a}-0_{00}^{\rm a}$ | 335446.240      | 16.3            | $8.4\times10^4$                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
|              |                                 |                 |                 |                                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
| $\rm oNH_2D$ | $1_{11}^{\rm s}-1_{01}^{\rm a}$ | 85926.258       | 20.7            | $6.1\times10^4$                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
| $\rm pNH_2D$ | $1_{11}^{\rm a}-1_{01}^{\rm s}$ | 110153.550      | 21.3            | $1.3\times10^5$                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+
|              |                                 |                 |                 |                                    |
+--------------+---------------------------------+-----------------+-----------------+------------------------------------+

: Observed transitions.

$^a$ The frequencies are adopted from (cite: 2021JMoSp.37711431M).

$^b$ Computed at 10 K.

## IRAM 30 m

The L1544 core was mapped in the 85.9 GHz and 110.2 GHz ortho- and para-$\rm NH_2D$ lines with the IRAM 30 m telescope in the on-the-fly mode. The mapping was performed in 2015. The scan directions alternated between the east-west equatorial and the north-south direction. The separation between rows and columns of the 85.9 GHz map was in general $5\ensuremath{''}$; the half-power beam width (HPBW) is $28.6\ensuremath{''}$ at this frequency, so the separation is $\sim 0.17\times{\rm HPBW}$. The area covered was $120\ensuremath{''}\times120\ensuremath{''}$. In the 110.2 GHz map, the rows and columns were separated by $8\ensuremath{''}$ ($\sim0.36\times{\rm HPBW}$; the HPBW is $22.3\ensuremath{''}$), and the map covered an area of $\sim 160\ensuremath{''}\times160\ensuremath{''}$. Both maps were centred on the column density peak of the core, RA $05^{\rm h}04^{\rm m}17.2\ensuremath{''}$, Dec. $+25\ensuremath{^\circ}10\ensuremath{'}43\ensuremath{''}$ (J2000.0).

For imaging, the maps were interpolated and averaged to regular grids using the cell sizes $5\ensuremath{''}$ and $8\ensuremath{''}$ for the 85.9 GHz and 110.2 GHz maps, respectively. As gridding function, we used a Bessel function of the first kind, $J_1$, tapered with a Gaussian ((cite: 2007A&A...474..679M); (cite: 2008PASJ...60..445S)). In practice, the observation representing a certain grid position was obtained by accumulating all observations with a radius of one HPBW from this position, weighted by the function $J_1(\pi r/a)/(\pi r/a) \times \exp(-(r/b)^2)$, where $r$ is the distance from the grid position in units of 1/3 of the beam width, and the constants are $a=1.55$, $b=2.52$. This gridding function causes a small broadening of the effective beam. The effect is approximately 10% for the 110.2 GHz map, but negligible for the 85.9 GHz map, where the cell size is small compared to the beam (see (cite: 2008PASJ...60..445S), their Fig. 6). In addition to the gridding function, the accumulated spectra were weighted by the inverse square of the system noise temperature $T_{\rm SYS}$ (the integration time was the same for all samples).

The observations were performed with the IRAM Eight Mixer Receiver (EMIR) operating at millimetre wavelengths. The two $\rm NH_2D$ transitions required different spectral setups of the E90 channel of the receiver; the line at 85.9 GHz was observed in the lower-outer subband, whereas the 110.2 GHz line was placed in the upper-outer subband. The EMIR receiver was connected to FFTSs. The FFTS back-end was configured to give 7.28 GHz of instantaneous bandwidth and a channel width of 50 kHz. The FFTS broadband spectra also covered the $1_{10}-1_{01}$ lines of ortho- and para-$\rm NHD_2$ near 111 GHZ. These lines were only marginally detected and were not useful in determining the o/p ratio.

## ALMA

We included in the analysis the para-$\rm NH_2D(1_{11}-1_{01})$ map of L1544 that was observed in 2016 with the Atacama Large (Sub)millimeter Array (ALMA) and presented in (cite: 2022ApJ...929...13C). The observations consisted of a three-point mosaic using the 12 m array, which is the main array, and a single pointing with the 7 m array, the Atacama Compact Array (ACA). The project ID was 2016.1.00240.S (PI Caselli). Here, we used an image cube that was produced by using natural weighting of the combined (12  m array and ACA) visibilities, and the CLEAN algorithm in the deconvolution of the dirty image. The final image was obtained by convolving the CLEAN component image with a Gaussian beam of $2.3\ensuremath{''}\times1.6\ensuremath{''}$, which corresponds to the main lobe of the synthesised beam. The rms noise in the central parts of the image is 0.15 K per 42 $\rm m\,s^{-1}$ channel. The reduction procedure is described in Sect. 2.1 of (cite: 2022ApJ...929...13C). The extent of p$\rm NH_2D$ emission was found to be approximately $1\ensuremath{'}\times0.5\ensuremath{'}$ (see Fig. A.1 in (cite: 2022ApJ...929...13C), and Fig. [12](#pnh2d_alma) below).

## Observed spectra and maps

(160,65)(0,0) (-5,0)

(0,0) ![image](L1544_0_0_oNH2D_spectra.ps)

(85,0)

(0,0) ![image](L1544_0_0_pNH2D_spectra.ps)

(90,65)(0,0) (0,0)

(0,0) ![image](L1544_0_0_NHD2_spectra.ps)

(160,70)(0,0) (-5,70)

(0,0) ![image](l1544_onh2d_11_map.ps)

(85,70)

(0,0) ![image](l1544_pnh2d_11_map.ps)

The $\rm NH_2D$ and $\rm NHD_2$ spectra observed with APEX and IRAM towards the $\rm H_2$ column density maximum of L1544 are shown in Figs. [2](#peak_nh2d_spectra) and [3](#peak_nhd2_spectra). The APEX spectra correspond to pixel of the LAsMA array. The integrated intensity maps of the 85.9 GHz and 110.2 GHz lines of $\rm NH_2D$ observed with the 30 m telescope are shown in Fig. [4](#nh2d_maps). Spectra and maps are presented on the antenna temperature, $T_{\rm A}^*$, scale.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |
| transition | peak $T_{\rm MB}$ | $\upsilon_{\rm LSR}$ | $\Delta \upsilon$ | $T_{\rm ex}$ | $\tau$ | $N_{\rm tot}$ |
| $J_{K_a,K_c}$ | \(K\) | ($\rm km\,s^{-1}$) | ($\rm km\,s^{-1}$) | \(K\) |  | ($10^{14}\, \rm cm^{-2}$) |
| $1_{11} - 1_{01}$ | 2.291 (0.005) | 7.263 (0.001) | 0.359 (0.001) | 5.31 (0.01) | 9.05 (0.04) | 4.13 (0.04) |
| $1_{01} - 0_{00}$ | 0.965 (0.016) | 7.319 (0.001) | 0.282 (0.003) | 5.69 (0.02) | 5.71 (0.20) | 3.55 (0.16) |
|  |  |  |  |  |  |  |
| transition | $T_{\rm MB}$ | $\upsilon_{\rm LSR}$ | $\Delta \upsilon$ | $T_{\rm ex}$ | $\tau$ | $N_{\rm tot}$ |
| $J_{K_a,K_c}$ | \(K\) | ($\rm km\,s^{-1}$) | ($\rm km\,s^{-1}$) | \(K\) |  | ($10^{14}\,\rm cm^{-2}$) |
| $1_{11} - 1_{01}$ | 1.341 (0.007) | 7.254 (0.001) | 0.326 (0.002) | 4.86 (0.02) | 3.67 (0.06) | 1.52 (0.07) |
| $1_{01} - 0_{00}$ | 0.470 (0.017) | 7.362 (0.003) | 0.293 (0.007) | 4.98 (0.11) | 2.53 (0.34) | 1.54 (0.33) |
|  |  |  |  |  |  |  |
| transition | $T_{\rm MB}$ | $\upsilon_{\rm LSR}$ | $\Delta \upsilon$ | $T_{\rm ex}$ | $\tau$ | $N_{\rm tot}$ |
| $J_{K_a,K_c}$ | \(K\) | ($\rm km\,s^{-1}$) | ($\rm km\,s^{-1}$) | \(K\) |  | ($10^{13}\,\rm cm^{-2}$) |
| $1_{11} - 0_{00}$ | 0.367 (0.010) | 7.254 (0.002) | 0.323 (0.006) | 5.70 (0.37) | 0.89 (0.22) | 2.91 (1.17) |
|  |  |  |  |  |  |  |
| transition | $T_{\rm MB}$ | $\upsilon_{\rm LSR}$ | $\Delta \upsilon$ | $T_{\rm ex}$ | $\tau$ | $N_{\rm tot}^*$ |
| $J_{K_a,K_c}$ | \(K\) | ($\rm km\,s^{-1}$) | ($\rm km\,s^{-1}$) | \(K\) |  | ($10^{13}\,\rm cm^{-2}$) |
| $1_{11} - 0_{00}$ | 0.221 (0.009) | 7.466 (0.004) | 0.353 (0.010) | 7.46 (4.48) | \- | 1.24 (0.14)$^*$ |
|  |  |  |  |  |  |  |

$^*$ Column density using the optically thin approximation assuming $T_{\rm ex}(\rm para)=T_{\rm ex}(\rm ortho)$.

The line parameters and column densities derived from Gaussian fits to the hyperfine structure of the lines observed towards the column density peak of L1544 are presented in Table [\[line_parameters\]](#line_parameters). The observed spectra were converted to the main-beam brightness temperature scale, $T_{\rm MB}$, using the beam efficiencies provided by the telescope teams. In column density estimates, we assumed uniform beam filling, line-of-sight homogeneity, and that the excitation temperature, $T_{\rm ex}$, is constant for all rotational transitions of the molecule. Furthermore, the calculation involved the assumption that populations of hyperfine states at a certain rotational level are proportional to their statistical weights. The strong quadrupole interaction of the N nucleus with the electric field of the electrons gives rise to five distinct components of the $J_{K_a,K_c}=1_{11}-1_{01}$ lines of $\rm NH_2D$, and three components of the ground-state lines ($1_{01}-0_{00}$ and $1_{11}-0_{00}$) of $\rm NH_2D$ and $\rm NHD_2$. These are further split into several unresolved components owing to quadrupole interaction of the deuteron, and weaker spin-rotation and spin-spin couplings ((cite: 2006A&A...449..855C); (cite: 2021JMoSp.37711431M)). The line width listed in Table [\[line_parameters\]](#line_parameters) refers to the intrinsic width of an individual hyperfine component. The derived local standard of rest velocities of the $1_{11}-0_{00}$ lines of $\rm oNHD_2$ and $\rm pNHD_2$ differ by approximately $210\,\rm m\,s^{-1}$, whereas velocity difference of the $\rm oNH_2D$ and $\rm pNH_2D$ lines in the same band is only $43\,\rm m\,s^{-1}$. This suggests that the rest frequencies of the $\rm NHD_2$ lines are not as accurate as those of the $\rm NH_2D$ lines. The velocity difference $210\,\rm m\,s^{-1}$ corresponds to $\sim 240$ kHz.

The strong rotation-inversion lines of $\rm NH_2D$ at $\lambda=3$ mm with five hyperfine groups have very high signal-to-noise ratios, and the formal errors of the column densities of $\rm NH_2D$ derived from these lines are clearly smaller than the estimates from the $\lambda=0.9$ mm lines. Although the column densities of $\rm pNH_2D$ from the $1_{11}-1_{01}$ and $1_{01}-0_{00}$ lines agree, the total $\rm oNH_2D$ column densities derived from the two ortho-lines differ by approximately 15%. This is due in part to the different beam sizes for the two o$\rm NH_2D$ lines ($29\ensuremath{''}$ vs $19\ensuremath{''}$). For the two p$\rm NH_2D$ lines the difference is smaller ($22\ensuremath{''}$ vs $19\ensuremath{''}$). The o/p-$\rm NH_2D$ ratio from the IRAM observations is $2.7\pm0.2$, whereas from the APEX spectra we obtain o/p-$\rm NH_2D=2.3\pm 0.5$. The hyperfine structure fit to the p$\rm NHD_2(1_{11}-0_{00})$ line does not give reliable estimates for the $T_{\rm ex}$ and $\tau$, and we estimated the column density using the optically thin approximation, adopting the $T_{\rm ex}$ derived for the ortho-line. The resulting o/p-$\rm NHD_2$ ratio is $2.3\pm1.2$. Depending on the distribution of the gas density and molecular abundances, the effective source size can be different for each observed line. This causes an uncertainty in the beam-source coupling efficiency, which propagates to $T_{\rm ex}$. In addition to the uncertainties involved in the determination of $T_{\rm ex}$ and $\tau$, especially when the line only has three resolved components, the assumption of a constant $T_{\rm ex}$ along the line of sight in the presence of large density gradients is an additional source of uncertainty. In what follows, we estimate the column densities and the fractional abundances of the observed molecules applying radiative transfer calculations to a spheroidal model of the L1544 core.

# Core model

We adopted the density and gas and dust temperature distributions from the model used for L1544 by (cite: 2019MNRAS.487.1269S) and (cite: 2023A&A...680A..87R), which, in turn, was developed from a model derived by (cite: 2010MNRAS.402.1625K). However, because the core is clearly elongated, we deformed the originally spherical model to a prolate spheroid. A Gaussian fit to the Spitzer $8\,\mu$m image of the core gave an axis ratio of 2.0 and a long axis tilt angle of $-36.1\ensuremath{^\circ}$ from the declination axis. For the purpose of radiative transfer calculations, we constructed a cubical grid with an edge length of $\sim 180\ensuremath{''}$ or 30,600 au. The transformation to the spheroidal model was done so that the volume within an isosurface (a surface representing constant values of the density, temperature, etc.) is the same as that of the corresponding isosurface of the spherical model. Consequently, the gas properties at point $(x,y,z)$ in the grid, measured from the origin of the principal axis system, correspond to those of the spherical model at radius $r$, which is obtained from $r=2^{1/3}\{x^2 + y^2 + z^2/\gamma^2\}^{1/2}$, where $\gamma \equiv c/a$ is the axis ratio of the spheroid (here $\gamma=2$).

We first tested how well the observed spectra can be reproduced by assuming that the fractional abundances of $\rm NH_2D$ and $\rm NHD_2$ are constant along the line of sight. Line simulations were performed using the Line radiative transfer with the OpenCL (LOC) program (cite: 2020A&A...644A.151J). The hyperfine structure of the lines was modelled by assuming local thermodynamic equilibrium between the components, that is, the effects of line overlap were not taken into account. The fractional abundances were determined by comparing the simulated spectra with the observed ones; the method that applies minimum chi-square estimation is described in Sect. 3.2 of (cite: 2024A&A...682A...8H). Only the statistical uncertainties based on the noise of the observed spectra are taken into account in this method. The best-fit abundances and their $1\,\sigma$ uncertainties obtained in the centre of the map (0,0) and the second strongest position $(-23\ensuremath{''},35\ensuremath{''})$ are listed in Table [2](#chi2_fracs). In the latter position, the $\rm NHD_2$ lines are weak, and only the $\rm NH_2D$ abundances are given. The $\rm NH_2D$ and $\rm NHD_2$ spectra observed in the seven LAsMA positions, including (0,0) and $(-23\ensuremath{''},35\ensuremath{''})$, are shown in Figs. [10](#lasma_dammo) and [11](#lasma_ddammo). The derived fractional $\rm NH_2D$ abundance is clearly higher towards the offset position than towards the centre of the core. We note that the $N(\rm H_2)$ estimate used for the fractional abundance comes from the spheroidal core model, which may miss a local condensation near position $(-23\ensuremath{''},35\ensuremath{''})$. The other alternative is that the assumption of constant abundances throughout the core is not true, which would also render the assumption of line-of-sight constancy illogical. In what follows, we apply a chemistry model to predict the abundance distributions in the core and simulate spectra from the obtained models.

|  |  |  |
|:---|:--:|:--:|
|  | (0,0) | ($-23\ensuremath{''},35\ensuremath{''}$) |
|  | ($\times10^{-9}$)$^a$ | ($\times10^{-9}$)$^a$ |
| $X(\rm oNH_2D)$ | $5.07 (0.05)$ | $12.7 (0.2)$ |
| $X(\rm pNH_2D)$ | $1.62 (0.03)$ | $4.30 (0.27)$ |
| $X(\rm oNHD_2)$ | $1.04 (0.02)$ |  |
| $X(\rm pNHD_2$ | $0.481 (0.009)$ |  |
| $X(\rm NH_2D)$ | $6.69 (0.06)$ | $17.0 (0.3)$ |
| $X(\rm NHD_2)$ | $1.52 (0.03)$ |  |
| $\rm NH_2D/\rm NH_2D$ | $0.23 (0.01)$ |  |
| o/p$\rm NH_2D$ | $3.13 (0.07)$ | $2.95 (0.19)$ |
| o/p$\rm NHD_2$ | $2.15 (0.06)$ |  |

: Fractional abundances, $X$, and abundance ratios in L1544 derived from the LAsMA spectra in pixels (0,0) and ($-23\ensuremath{''},35\ensuremath{''}$) assuming that $X$ is constant throughout the core.

$^a$ Factor of the fractional abundances, $X.$

# Chemistry model

For chemical simulations, we used the gas-grain chemical model *pyRate* described in (cite: 2019A&A...631A..63S), (cite: 2023A&A...680A..87R), and (cite: 2024A&A...682A...8H), employing the PH and FS scenarios for proton donation and abstraction reactions. In the PH network, proton transfer reactions involving O, C, and N are assumed to proceed via the exchange of one proton (or deuteron) between the reactants, while in the FS network multiple atom exchanges are possible. However, the $\rm H_3^++ \rm H_2$ reaction system and its deuterated variants form an exception in the PH network. For the reactions that involve only the H or D nuclei, the rate coefficients and branching ratios adopted from (cite: 2009JChPh.130p4302H), follow the FS scenario in both networks. Some deuterated variants of the $\rm H_3^++ \rm H_2$ system were recently studied by (cite: 2024A&A...692A.121J) through experiments and simulations. The results indicate that the growth of the abundances of $\rm D_2H^+$, $\rm D_2H^+$, and $\rm D_3^+$ is suppressed more than previously thought in warm conditions by hydrogenation reactions. Since we are dealing with very cold gas in L1544, we did not make any changes to the original reaction set of (cite: 2009JChPh.130p4302H).

The efficiency of chemical desorption was assumed to be constant, with 1% exothermic surface reactions leading to desorption. The dust grains were assumed to have uniform size characterised by the grain radius $a$ and the density of the material $\rho$, assumed to be $2.5\,{\rm g}\,\rm cm^{-3}$. The simulations were performed using the grain radii $a=0.1$, 0.2, and $0.3\,\mu$m. The value $a=0.1\,\mu$m corresponds to a grain surface area of $5.0\times10^{-22}\,\rm cm^{-2}$ per H atom, with the adopted material density and the dust-to-gas mass ratio (0.01; (cite: 2020A&A...640A..94S)). The grain surface area is inversely proportional to the grain radius for particles of uniform size. We also varied the cosmic-ray ionisation rate, testing the values 0.5,1,2,4, and 8 times $1.3\times10^{-17}\,\rm s^{-1}$.

We assumed that the gas has been processed under low-density ‘dark cloud’ conditions ($n(\rm H_2)=10^4\,\rm cm^{-3}$, $T=10$ K, $A_{\rm V}=5^{\rm mag}$) for half a million years before the ‘dense core’ phase. The initial abundances used for the first simulation step are the same as those listed in Table 1 of (cite: 2023A&A...680A..87R). The chemical abundances attained at the end of the dark cloud phase were in turn used as initial values of the dense core phase. The abundances in the dense core were calculated for concentric spherical shells using the one-dimensional model described in (cite: 2023A&A...680A..87R). These were interpolated to the spheroidal model for spectral line simulations using the transformation described above.

The evolution of the average fractional abundances of $\rm NH_2D$ and $\rm NHD_2$ in the FS and PH models is shown in Fig. [5](#x_vs_time), with the ortho- and para-species separated. Here, the grain radius is $a=0.2\,\mu$m, and the cosmic-ray ionisation rate is $\zeta_{\rm H_2}=2.6\times10^{-17}\,\rm s^{-1}$. The curves represent the column density ratios $N({\rm mol})/N(\rm H_2)$ towards the centre of the core. These column densities are derived from the spheroidal models and convolved with the telescope beam. The ratios are in this sense comparable to the estimates presented in Table [2](#chi2_fracs) for the (0,0) position. In Fig. [6](#ops_dfracs) we show the o/p ratios of $\rm NH_3$, $\rm NH_2D$, and $\rm NHD_2$, and the fractionation ratios $\rm NH_2D/\rm NH_3$, $\rm NHD_2/\rm NH_2D$, and $\rm ND_3/\rm NHD_2$ as functions of time predicted by the same PH and FS models as shown in Fig. [5](#x_vs_time). The PH model predicts constant o/p ratios corresponding to their high-temperature statistical values, whereas in the FS model the ratios show some time variation. One can see that the predicted values of the o/p-$\rm NH_2D$ and o/p-$\rm NHD_2$ ratios are almost swapped between the PH and FS models. In agreement with the simulations of (cite: 2013ApJ...770L...2F) and (cite: 2014A&A...562A..83L), the o/p ratio of $\rm NH_3$ remains below 1 in the FS model. The deuterium fractionation ratios will be discussed briefly in Sect. [7.2](#op_ratios).

(160,65)(0,0) (-10,0)

(0,0) ![image](L1544_1D_PH_a2_z2.6e-17_time.ps)

(80,0)

(0,0) ![image](L1544_1D_FS_a2_z2.6e-17_time.ps)

(7,60)**(a)** (97,60)**(b)** (67,60) (158,60)

(160,65)(0,0) (-10,0)

(0,0) ![image](dfracs_op_ph.ps)

(80,0)

(0,0) ![image](dfracs_op_fs.ps)

(7,50)**(a)** (97,50)**(b)** (67,50) (158,50)

# Simulated spectra

We first attempted to reproduce the spectra observed with APEX and IRAM using the abundance distributions predicted by the chemistry models described above. Almost all models tested here can reasonably well reproduce the two p$\rm NH_2D$ lines and the o$\rm NH_2D(1_{01}-0_{00})$ line at 333 GHz at one simulation time. Examples of simulated $\rm NH_2D$ spectra towards the centre of the core are shown in Fig. [7](#sample_nh2d). These are the best-fit spectra from the FS and PH models with certain combinations of $a$ and $\zeta_{\rm H_2}$. For models assuming $a=0.2\,\mu$m and $\zeta_{\rm H_2}=2.6\times10^{-17}\,\rm s^{-1}$ (top panel), the best-fit simulation time is $3.2\times10^5$ yr. Like for most other models, the 86 GHz line of the o$\rm NH_2D$ line is clearly brighter than observed whenever the three other lines agree. The discrepancy depends mainly on the relatively large telescope beam ($29\ensuremath{''}$ vs $19\ensuremath{''}$-$22\ensuremath{''}$) in the 86 GHz observations. It suggests either that the predicted $\rm NH_2D$ distribution is overly extended or that the model underpredicts the abundances near the centre of the core. In both cases, the lines simulated with smaller beams would be excessively weak with respect to the simulated 86 GHz line. Taking a closer look at the spectra one notices that the PH model can better reproduce both 333 GHz lines simultaneously. In the FS model, one of these lines is either too weak or too strong when the other agrees. The same is true for ortho- and para-$\rm NHD_2$. This difference is also seen in Figs. [5](#x_vs_time) and [6](#ops_dfracs). For the PH model, the curves showing the fractional abundances of $\rm oNH_2D$ and $\rm pNH_2D$ cross the horizontal lines indicating the values derived from observations approximately at the same time, and the predicted o/p ratios (constantly 3 and 2) are close to the observationally derived values. For the FS model, the best-fit times are different, and the o/p-$\rm NH_2D$ and o/p-$\rm NHD_2$ ratios are almost reversed with respect to those in the PH model. The best-fit simulation times in Fig. [7](#sample_nh2d) do not correspond to the times when the curves shown in Fig. [5](#x_vs_time) cross the horizontal lines because the ‘observed levels’ shown in the latter figure were derived assuming constant abundances. Examples of simulated abundance distributions are shown below.

(160,120)(0,0) (-5,60)

(0,0) ![image](nh2d_ph_a2_z2.6e-17_t3.2e5.ps)

(85,60)

(0,0) ![image](nh2d_fs_a2_z2.6e-17_t3.2e5.ps)

(-5,0)

(0,0) ![image](nh2d_ph_a2_z1.04e-16_t3.2e4.ps)

(85,0)

(0,0) ![image](nh2d_fs_a2_z1.04e-16_t3.2e4.ps)

The agreement between the simulated and observed 86 GHz lines of o$\rm NH_2D$ improves with an increase in the cosmic-ray ionisation rate. In the bottom panel of Fig. [7](#sample_nh2d), we show the spectra obtained from the models with $\zeta_{\rm H_2}=1.04\times10^{-16}\,\rm s^{-1}$ for the grain radius $a=0.2\,\mu$m. The agreement is also good for the model with $a=0.3\,\mu$m. At high values of $\zeta_{\rm H_2}$ chemical reactions proceed rapidly and the 333 GHz lines reach the observed intensities already after $3-4\times10^4$ yr of simulation time. Also in this case, the relative intensities of the ortho- and para-lines of $\rm NH_2D$ at 333 GHz are better reproduced by the PH model. At the best-fit time, the o/p-$\rm NH_2D$ and o/p-$\rm NHD_2$ ratios predicted by the FS model are 2.3 and 2.9, respectively, while in the PH model they are always 3.0 and 2.0. Figure [8](#abundance_profiles) shows the abundance profiles of $\rm NH_2D$ and $\rm NHD_2$ in the core models used for the left-hand side of Fig. [7](#sample_nh2d). One can see that in the model with a high cosmic-ray ionisation rate, the abundances of $\rm NH_2D$ and $\rm NHD_2$ are higher near the centre of the core than in the model with a lower $\zeta_{\rm H_2}$. In fact, the abundances of ortho- and para-$\rm NH_2D$ are almost constant in a wide range of densities and radial distances greater than $\sim 10\ensuremath{''}$ from the centre.

(160,60)(0,0) (-5,0)

(0,0) ![image](x_vs_dens_PH_a2_z2.6e-17_3.2e5.ps)

(85,0)

(0,0) ![image](x_vs_dens_PH_a2_z1.04e-16_3.2e4.ps)

(10,50) (100,50)

The ortho- and para-$\rm NHD_2$ lines at 335 GHz can be fitted with models that also reproduce the 333 GHz lines of $\rm NH_2D$. However, as suggested in Fig. [5](#x_vs_time), $\rm NHD_2$ reaches the best-fit abundance earlier than $\rm NH_2D$. We think the difference is attributable to the static core model, which neglects the contraction of the core at the same time as the chemistry is evolving. This makes it difficult to reach agreement with observations simultaneously for two different species. The simulations of $\rm NHD_2$ spectra from the models that approximately reproduce all four $\rm NH_2D$ spectra ($a=0.2\,\mu$m, $\zeta_{\rm H_2}=1.04\times10^{-16}\,\rm s^{-1}$) are shown in Fig. [9](#sample_nhd2).

(80,105)(0,0) (0,55)

(0,0) ![image](nhd2_ph_a2_z1.04e-16_t2e4.ps)

(0,0)

(0,0) ![image](nhd2_fs_a2_z1.04e-16_t2e4.ps)

# Simulations with an ad hoc abundance profile

The agreement between the simulated and observed spectra reached by increasing the cosmic-ray ionisation rate to $\zeta_{\rm H_2} \sim 10^{-16}\,\rm s^{-1}$ is not satisfactory because a clearly lower average value of $\zeta_{\rm H_2}$ ($\sim 3\times10^{-17}\,\rm s^{-1}$) has been estimated in L1544 based on observations of molecular ions (cite: 2021A&A...656A.109R). On the other hand, the abundance profile of $\rm NH_2D$ predicted by the high-ionisation-rate model is likely to have an element of truth. In the inner part of the core, it agrees with the ALMA observations and the modelling results of (cite: 2022ApJ...929...13C), which show that p$\rm NH_2D$ becomes heavily depleted within $10\ensuremath{''}$ (1700 au) from the centre of L1544 (see their Fig. 5). We ran another series of simulations assuming that the fractional abundances of ortho- and para-$\rm NH_2D$ and $\rm NHD_2$ are constant in the density range $n_{\rm H_2}=5\times10^4-5\times10^5\,\rm cm^{-3}$ (corresponding to radial distances $10\ensuremath{''}-30\ensuremath{''}$), but decrease both towards the centre and the outer parts. Here, the simulations included both the single-dish observations with APEX and IRAM and the p$\rm NH_2D$ map observed with ALMA. We first assumed that fractional abundances are proportional to $n^{-1}$ and $n$ in these two regions. A similar distribution was used to model the observations of $\rm NH_2D$ and $\rm NHD_2$ in the pre-stellar cores H-MM1 and Oph D in Ophiuchus (cite: 2024A&A...682A...8H), except that it was assumed that the density threshold of the region dominated by accretion is lower. The high threshold used in L1544 is based on the observations of (cite: 2022ApJ...929...13C). Although the APEX and IRAM spectra were not very sensitive to the slope of the density dependence in the inner part of the core, to reproduce the ALMA observations it was necessary to assume that the decrease in the $\rm NH_2D$ abundance near the centre is steeper than $n^{-1}$. We obtained rather a good agreement with all the observed spectra by assuming that the fractional $\rm NH_2D$ and $\rm NHD_2$ abundances are proportional to $n^{-2}$ in the inner parts of the core. The steepness of the slope does not affect the o/p ratios obtained from the APEX data.

The fractional abundances of o$\rm NH_2D$, p$\rm NH_2D$, o$\rm NHD_2$, and p$\rm NHD_2$ (in the flat region) were independently varied and the simulated spectra of the spheroidal core model were compared with observations. The best-fit abundances and their uncertainties were estimated by evaluating the $\chi^2$ statistic as explained in (cite: 2024A&A...682A...8H). The results of these simulations are presented in Table [3](#X_updown). The simulated spectra from the best-fit model towards the seven positions observed with APEX/LAsMA are shown in Figs. [10](#lasma_dammo) and [11](#lasma_ddammo), together with the observed spectra at these positions. The observed and simulated ALMA spectra of p$\rm NH_2D$ along two orthogonal strips near the centre of the core are shown in Fig. [12](#pnh2d_alma).

+:----------------------+:----------------------:+:----------------------:+
|                       | Maximum                | Average                |
+-----------------------+------------------------+------------------------+
|                       | ($\times 10^{-9}$)$^a$ | ($\times 10^{-9}$)$^a$ |
+-----------------------+------------------------+------------------------+
| $X({\rm o}\rm NH_2D)$ | $9.26\pm0.06$          | $3.74\pm0.02$          |
+-----------------------+------------------------+------------------------+
| $X({\rm p}\rm NH_2D)$ | $3.25\pm0.04$          | $1.31\pm0.02$          |
+-----------------------+------------------------+------------------------+
| $X({\rm o}\rm NHD_2)$ | $2.23\pm0.03$          | $0.90\pm0.01$          |
+-----------------------+------------------------+------------------------+
| $X({\rm p}\rm NHD_2)$ | $1.06\pm0.02$          | $0.43\pm0.01$          |
+-----------------------+------------------------+------------------------+
| $X(\rm NH_2D)$        | $12.5\pm0.1$           | $5.05\pm0.03$          |
+-----------------------+------------------------+------------------------+
| $X(\rm NHD_2)$        | $3.30\pm0.03$          | $1.33\pm0.01$          |
+-----------------------+------------------------+------------------------+
| $\rm NH_2D/\rm NH_2D$ | $0.264\pm0.003$                                 |
+-----------------------+-------------------------------------------------+
| o/p$\rm NH_2D$        | $2.85\pm0.05$                                   |
+-----------------------+-------------------------------------------------+
| o/p$\rm NHD_2$        | $2.10\pm0.06$                                   |
+-----------------------+-------------------------------------------------+

: Fractional abundances, $X$, and abundance ratios in L1544 derived using a model where the abundances are constant in the density range $n_{\rm H_2}=5\times10^4-5\times10^5\,\rm cm^{-3}$ but decrease towards higher and lower densities.

$^a$ Factor of the fractional abundances, $X.$

# Discussion

## Distributions of $\rm NH_2D$ and $\rm NHD_2$ in L1544

The efforts to simulate the observed $\rm NH_2D$ and $\rm NHD_2$ lines towards L1544 have shown that it is fairly easy to construct a model that approximately reproduces the observed $\rm NH_2D$ lines at 333 GHz and the p$\rm NH_2D$ line at 110 GHz, and the lines of $\rm NHD_2$ at 335 GHz. Because the beam sizes used to observe the aforementioned lines are similar ($\sim20\ensuremath{''}$) their relative intensities do not strongly depend on the spatial extent of the molecular distribution as long as the ortho and para modifications of $\rm NH_2D$ and $\rm NHD_2$ follow the same pattern. However, we encounter severe problems when including the 86 GHz line of o$\rm NH_2D$, which was observed with a larger beam ($\sim29\ensuremath{''}$). For most models, the 86 GHz line is too strong whenever the intensities of the other lines agree with the observations, indicating that the abundance of $\rm NH_2D$ is excessively high in the outer parts of the core relative to that in the central parts. Because the chemistry model predicts heavy depletion of molecules in the inner parts of the core as a result of accretion onto the grains, it is natural to suspect that the depletion is too efficient in the model. One way to decrease accretion is to increase the effective grain radius, $a$, which reduces the total surface area of the grains. Simulations with constant grain radii of $a=0.2$ and $0.3\,\mu$m gave better results than our standard assumption $a=0.1\,\mu$m. We also performed simulations with a varying grain radius according to the coagulation model of (cite: 2009A&A...502..845O), but these did not result in significant changes relative to our standard model. This is probably because in the varying grain size model the effective radius exceeds $a=0.3\,\mu$m only in a few central shells of the core model, within an angular distance of $5\ensuremath{''}$ from the centre. The 86 GHz and 333 GHz lines of o$\rm NH_2D$ could not be fitted simultaneously with any of the grain size distributions tested if the other model parameters were left unchanged.

By increasing the cosmic-ray ionisation rate, from the standard value $\zeta_{\rm H_2}=1.3\times10^{-17}$ by a factor of 8, to $\zeta_{\rm H_2}=1.04\times10^{-16}\,\rm s^{-1}$, we achieved, at an early simulation time, spatial distributions of $\rm NH_2D$ and $\rm NHD_2$ that reproduce all of the observed lines more or less simultaneously. An increased cosmic-ray ionisation rate speeds up gas-phase chemical reactions leading to high abundances of $\rm NH_2D$ and $\rm NHD_2$ in the inner parts of the core before depletion takes effect. The resulting distribution of $\rm NH_2D$ is fairly flat at the beginning, except for a drop near the very centre (Fig. [8](#abundance_profiles) right). The shape of the distribution in the inner parts of the core agrees with the ALMA observations and modelling results of (cite: 2022ApJ...929...13C), which show that p$\rm NH_2D$ becomes heavily depleted within $10\ensuremath{''}$ (1700 au) from the centre of L1544 (see their Fig. 5). As discussed in this paper, the detection of such a small, almost complete freeze-out zone requires interferometric observations. That the present chemical model seems to overpredict molecular depletion and that single-dish observations can be modelled assuming constant fractional abundances have been previously noted by (cite: 2025A&A...694A..27S). In the present study, increasing the cosmic-ray ionisation rate is a way to achieve high abundances of $\rm NH_2D$ and $\rm NHD_2$ in the inner parts of the core, but we are not sure how seriously the value $\zeta_{\rm H_2}\sim 10^{-16}\,\rm s^{-1}$ should be taken. It would agree with the estimate of (cite: 2019ApJ...884..176I) based on the gas temperature measurements in L1544, and a model for the equilibrium gas temperature and size-dependent dust temperature. This model assumes the canonical grain size distribution of (cite: 1977ApJ...217..425M) with $dn(a)/da \propto a^{-3.5}$ in the range $a_{\rm min} \leq a \leq a_{\rm max}$, where $a_{\rm min}=5$ nm and $a_{\rm max}=250$ nm. As noted in (cite: 2021A&A...656A.109R), this size distribution is unlikely to be valid in dense molecular clouds where the smallest grains are eliminated by coagulation (cite: 2020A&A...641A..39S), and taking this into account, the estimate from the theory of (cite: 2019ApJ...884..176I) is lowered by a factor of 3. The revised value agrees with the results of (cite: 2021A&A...656A.109R) giving an average $\zeta_{\rm H_2}$ of $3\times10^{-17}\,\rm s^{-1}$ in L1544. The abundances of the molecular ions observed by (cite: 2021A&A...656A.109R) are highly dependent on the cosmic-ray ionisation rate, and the estimate of these authors is probably more trustworthy than the high value obtained here. The lower value would be in line with recent estimates of the cosmic-ray ionisation rate in nearby diffuse clouds ($<10^{-16}\,\rm s^{-1}$; (cite: 2024ApJ...973..142O); (cite: 2024ApJ...973..143N)). These are based on updated gas density estimates from three-dimensional extinction maps and the excitation of diatomic carbon. On the other hand, one could expect a local enhancement of the cosmic-ray ionisation rate in the Taurus molecular cloud complex, including L1544, because of their apparent location in the intersection of large-scale structures known as the Local Bubble and the Per-Tau Shell ((cite: 2022Natur.601..334Z); (cite: 2021ApJ...919L...5B)). As discussed in (cite: 2022Natur.601..334Z), these structures are likely to have been generated by multiple supernova events in the past. Shock acceleration in the blast waves of supernova remnants is a major source of cosmic rays (e.g., (cite: 2019PhRvL.123g1101D) and references therein).

In addition of the cosmic-ray ionisation rate, there are several other parameters in the chemistry model that influence the accretion and desorption of molecules and thereby their radial distribution in a dense core. However, the objective of the present study is to determine the o/p ratios of $\rm NH_2D$ and $\rm NHD_2$. In what follows, we leave the difficulties in modelling the spatial distribution of these molecules aside and concentrate on their spin ratios.

## Ortho/para ratios

Judging from the difficulty in fitting the o$\rm NH_2D$ line at 86 GHz together with the other lines of $\rm NH_2D$, we think that observations of the ground-state lines of $\rm NH_2D$ and $\rm NHD_2$ at 333 and 335 GHz provide the most reliable estimates for the o/p ratios of these molecules. In addition to the fact that the ground-state lines are observed with the same beam, their relative intensities are free from calibration issues, because they lie close in frequency and are observable in the same spectrometer band. As can be seen in the spectra shown in Figs. [7](#sample_nh2d) and [9](#sample_nhd2), simulations from the FS reaction scheme underpredict the intensity of the o$\rm NH_2D(1_{01}-0_{00})$ when the p$\rm NH_2D(1_{01}-0_{00})$ line agrees, and conversely overpredict the o$\rm NHD_2(1_{11}-0_{00})$ intensity when p$\rm NHD_2(1_{11}-0_{00})$ fits. Simulations from the PH reaction scheme give reasonably good agreement with both ortho- and para-lines at the same time. The differences between the simulated line intensities from the PH and FS reaction schemes are not large, but the FS model produces systematically discrepant line ratios of the ortho- and para-species. The line simulations described in Sect. [6](#updown), which used a fixed fractional abundance profile but let the absolute values float freely, support the PH scenario. The best-fit fractional abundances imply the spin ratios o/p-$\rm NH_2D=2.85\pm0.05$ and o/p-$\rm NHD_2=2.10\pm0.06$ (taking into account $1\sigma$ errors). This means that it is reasonable to assume that the o/p ratios of $\rm NH_2D$ and $\rm NHD_2$ in L1544 are simply determined by the nuclear spin statistical weights. We arrived previously at the same conclusion in the Ophiuchus cores H-MM1 and Oph D. This also agrees with the earlier results of (cite: 2016MNRAS.457.1535D) towards the dense cores B1b and I16293E.

Based on the arguments presented in (cite: 2024A&A...682A...8H), we assume that the o/p ratios of $\rm NH_2D$ and $\rm NHD_2$ observed in the gas are not inherited from molecules released from grains, but result from ion-molecule reactions in the gas, which thus must be regarded as PH reactions rather than reactions where the H and D nuclei are completely scrambled. The viability of mixing hydrogen or deuterium atoms in reactions leading to deuterated ammonia was briefly discussed in (cite: 2013JPCA..117.9800R) and (cite: 2017A&A...600A..61H), with reference to theoretical calculations of (cite: 1991JChPh..94.7842H) and (cite: 1992JChPh..97.1191I) of the potential energy surface of the system $[\rm NH_3..\rm H_2/{\rm HD/D_2}]^+$, which is the dominant pathway to the ammonium ion ${\rm NH_4^+}$. As discussed in (cite: 1992JChPh..97.1191I), interchange of H or D atoms is possible through certain transition structures of the reaction complex, some of which have relatively low energies while others constitute substantial barriers. However, in some cases, a barrier can be avoided due to the nearly free internal rotation of the ${\rm NH_4^+}$ moiety in the exit channel complex $[{\rm NH_4..H}]^+$. We are not aware of theoretical calculations that would address the reactions $\rm NH_3+\rm H_2D^+/\rm D_2H^+/\rm D_3^+$, which probably produce most of the deuterated ammonia in dense cores. We note that when only one hydrogen or deuterium atom is transferred from one molecule to another, the spin ratios maintain their statistical values even if nuclei are mixed within the two parts of the entrance and exit channel complexes.

As discussed in (cite: 2019A&A...631A..63S), the choice of the reaction scheme also affects the deuterium fractionation in addition to the spin ratios. Reactions where two deuterium atoms are transferred, such as $\rm NH_3+\rm D_2H^+\rightarrow \rm NHD_2+\rm H_2$, are possible in the FS scheme but not allowed in the PH scheme (see Fig. 1 in (cite: 2019A&A...631A..63S)). In the present simulations, the PH model predicts higher $\rm NH_2D/\rm NH_3$ ratios and lower $\rm NHD_2/\rm NH_2D$ and $\rm ND_3/\rm NHD_2$ ratios than the FS model, especially at late times ($t\goa10^6$ yr; see Fig. [6](#ops_dfracs)). Because the abundance of $\rm NHD_2$ peaks earlier than that of $\rm NH_2D$ (see Fig. [5](#x_vs_time)), the predicted $\rm NHD_2/\rm NH_2D$ ratio generally does not correspond to the observed value at the time when the $\rm NH_2D$ spectra agree with the observations. In contrast to previous simulations of (cite: 2019A&A...631A..63S), the ratio $\rm NH_2D/\rm NH_3$ remains low ($\sim 0.1$) also in the PH model. The present chemistry models include chemical desorption, which enhances the replenishment of the gas with molecules formed in the icy mantles of grains, where deuterium fractionation is weaker. These simulations also show that the molecules released from the grains are quickly reprocessed in the gas, and the spin ratios are determined by the ion-molecule reactions no matter how efficient the desorption is (cite: 2024A&A...682A...8H). As evident in Fig. [6](#ops_dfracs), the predicted deuterium fractionation ratios of ammonia vary significantly during the probable lifetime of a dense core ($\loa10^6$ yr). The figure suggests that fractionation ratios can be useful for chemical dating, while spin ratios do not serve this purpose.

# Conclusions

We have determined the o/p ratios of the $\rm NH_2D$ and $\rm NHD_2$ molecules in one of the most sheltered and coldest places in the local Universe, the inner parts of the pre-stellar core L1544 in the Taurus molecular cloud complex. In accordance with similar measurements towards two starless cores in Ophiuchus, the o/p ratios of both molecules are found to correspond to the nuclear spin statistical weights, o:p-$\rm NH_2D=3:1$ and o:p-$\rm NH_2D=2:1$. Because the ratios are likely to be determined by gas-phase ion-molecule reactions, these reactions are best described as single-proton or single-deuteron hops that maintain the statistical spin ratios. Ammonia formation on grain surfaces is predicted to proceed through H or D atom additions that also produce ortho- and para-species according to their statistical weights, so it seems reasonable to assume that the spin ratios of ammonia and its deuterated isotopologues are always statistical. Another consequence of adopting the PH reaction scheme is that singly deuterated ammonia is favoured at the cost of $\rm NHD_2$ and $\rm ND_3$. This scheme therefore leads to fractionation ratios $\rm NH_2D/\rm NH_3$, $\rm NHD_2/\rm NH_2D$, and $\rm ND_3/\rm NHD_2$ that are different from those predicted by the FS scheme.

# Acknowledgements

The authors thank APEX staff for performing the observations, the anonymous reviewer for helpful comments on the manuscript, and the Max Planck Society for financial support.

52 natexlab

(ref: 2021ApJ...919L...5B) Bialy, S., Zucker, C., Goodman, A., et al. 2021, ApJL, 919, L5

(ref: bunker&jensen2005) Bunker, P. R. & Jensen, P. 2005, Fundamentals of Molecular Symmetry (London: IOP Publishing Ltd)

(ref: 2017A&A...603L...1C) Caselli, P., Bizzocchi, L., Keto, E., et al. 2017, A&A, 603, L1

(ref: 2022ApJ...929...13C) Caselli, P., Pineda, J. E., Sipilä, O., et al. 2022, ApJ, 929, 13

(ref: 2019ApJ...874...89C) Caselli, P., Pineda, J. E., Zhao, B., et al. 2019, ApJ, 874, 89

(ref: 2022A&A...663A..43C) Cheng, Y. C., Bockelée-Morvan, D., Roos-Serote, M., et al. 2022, A&A, 663, A43

(ref: 2006A&A...449..855C) Coudert, L. H. & Roueff, E. 2006, A&A, 449, 855

(ref: 2007A&A...470..221C) Crapsi, A., Caselli, P., Walmsley, M. C., & Tafalla, M. 2007, A&A, 470, 221

(ref: 2014MNRAS.444.2544D) Daniel, F., Faure, A., Wiesenfeld, L., et al. 2014, MNRAS, 444, 2544

(ref: 2016MNRAS.457.1535D) Daniel, F., Rist, C., Faure, A., et al. 2016, MNRAS, 457, 1535

(ref: 2019PhRvL.123g1101D) Diesing, R. & Caprioli, D. 2019, , 123, 071101

(ref: 2013ApJ...770L...2F) Faure, A., Hily-Blant, P., Le Gal, R., Rist, C., & Pineau des Forêts, G. 2013, ApJL, 770, L2

(ref: 2019MNRAS.487.3392F) Faure, A., Hily-Blant, P., Rist, C., et al. 2019, MNRAS, 487, 3392

(ref: 2008SPIE.7020E..10G) Güsten, R., Baryshev, A., Bell, A., et al. 2008, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7020, Millimeter and Submillimeter Detectors and Instrumentation for Astronomy IV, ed. W. D. Duncan, W. S. Holland, S. Withington, & J. Zmuidzinas, 702010

(ref: 2006A&A...454L..13G) Güsten, R., Nyman, L. Å., Schilke, P., et al. 2006, A&A, 454, L13

(ref: 2018ApJ...857L..13H) Hama, T., Kouchi, A., & Watanabe, N. 2018, ApJL, 857, L13

(ref: 2017A&A...600A..61H) Harju, J., Daniel, F., Sipilä, O., et al. 2017, A&A, 600, A61

(ref: 2024A&A...682A...8H) Harju, J., Pineda, J. E., Sipilä, O., et al. 2024, A&A, 682, A8

(ref: 1991JChPh..94.7842H) Herbst, E., Defrees, D. J., Talbi, D., Pauzat, F., & Koch, W. 1991, , 94, 7842

(ref: 2018MNRAS.477.4454H) Hily-Blant, P., Faure, A., Rist, C., Pineau des Forêts, G., & Flower, D. R. 2018, MNRAS, 477, 4454

(ref: 2009JChPh.130p4302H) Hugo, E., Asvany, O., & Schlemmer, S. 2009, , 130, 164302

(ref: 1992JChPh..97.1191I) Ischtwan, J., Smith, B. J., Collins, M. A., & Radom, L. 1992, , 97, 1191

(ref: 2019ApJ...884..176I) Ivlev, A. V., Silsbee, K., Sipilä, O., & Caselli, P. 2019, ApJ, 884, 176

(ref: 2024A&A...692A.121J) Jiménez-Redondo, M., Sipilä, O., Jusko, P., & Caselli, P. 2024, A&A, 692, A121

(ref: 2020A&A...644A.151J) Juvela, M. 2020, A&A, 644, A151

(ref: 2010MNRAS.402.1625K) Keto, E. & Caselli, P. 2010, MNRAS, 402, 1625

(ref: 2020A&A...638A..74L) Ladjelate, B., André, P., Könyves, V., et al. 2020, A&A, 638, A74

(ref: 2014A&A...562A..83L) Le Gal, R., Hily-Blant, P., Faure, A., et al. 2014, A&A, 562, A83

(ref: 2007A&A...474..679M) Mangum, J. G., Emerson, D. T., & Greisen, E. W. 2007, A&A, 474, 679

(ref: 1977ApJ...217..425M) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: 2021JMoSp.37711431M) Melosso, M., Bizzocchi, L., Dore, L., et al. 2021, Journal of Molecular Spectroscopy, 377, 111431

(ref: 2022A&A...667A.163M) Miret-Roig, N., Galli, P. A. B., Olivares, J., et al. 2022, A&A, 667, A163

(ref: 2011ARA&A..49..471M) Mumma, M. J. & Charnley, S. B. 2011, ARA&A, 49, 471

(ref: 2024ApJ...973..143N) Neufeld, D. A., Welty, D. E., Ivlev, A. V., et al. 2024, ApJ, 973, 143

(ref: 2024ApJ...973..142O) Obolentseva, M., Ivlev, A. V., Silsbee, K., et al. 2024, ApJ, 973, 142

(ref: 2004JMoSp.228..635O) Oka, T. 2004, Journal of Molecular Spectroscopy, 228, 635

(ref: 2009A&A...502..845O) Ormel, C. W., Paszun, D., Dominik, C., & Tielens, A. G. G. M. 2009, A&A, 502, 845

(ref: 2021A&A...656A.109R) Redaelli, E., Sipilä, O., Padovani, M., et al. 2021, A&A, 656, A109

(ref: 2023A&A...680A..87R) Riedel, W., Sipilä, O., Redaelli, E., et al. 2023, A&A, 680, A87

(ref: 2013JPCA..117.9800R) Rist, C., Faure, A., Hily-Blant, P., & Le Gal, R. 2013, Journal of Physical Chemistry A, 117, 9800

(ref: 2008PASJ...60..445S) Sawada, T., Ikeda, N., Sunada, K., et al. 2008, PASJ, 60, 445

(ref: 2016JChPh.145g4301S) Schmiedt, H., Jensen, P., & Schlemmer, S. 2016, , 145, 074301

(ref: 2016MNRAS.462S.124S) Shinnaka, Y., Kawakita, H., Jehin, E., et al. 2016, MNRAS, 462, S124

(ref: 2015PASP..127..299S) Shirley, Y. L. 2015, PASP, 127, 299

(ref: 2020A&A...641A..39S) Silsbee, K., Ivlev, A. V., Sipilä, O., Caselli, P., & Zhao, B. 2020, A&A, 641, A39

(ref: 2019A&A...631A..63S) Sipilä, O., Caselli, P., & Harju, J. 2019a, A&A, 631, A63

(ref: 2019MNRAS.487.1269S) Sipilä, O., Caselli, P., Redaelli, E., Juvela, M., & Bizzocchi, L. 2019b, MNRAS, 487, 1269

(ref: 2015A&A...581A.122S) Sipilä, O., Harju, J., Caselli, P., & Schlemmer, S. 2015, A&A, 581, A122

(ref: 2020A&A...640A..94S) Sipilä, O., Zhao, B., & Caselli, P. 2020, A&A, 640, A94

(ref: 2025A&A...694A..27S) Spezzano, S., Redaelli, E., Caselli, P., et al. 2025, A&A, 694, A27

(ref: 2025PSJ.....6..139W) Woodward, C. E., Bockélee-Morvan, D., Harker, D. E., et al. 2025, , 6, 139

(ref: 2022Natur.601..334Z) Zucker, C., Goodman, A. A., Alves, J., et al. 2022, Nature, 601, 334

# Observed and simulated APEX and IRAM spectra

The $\rm NH_2D$ spectra observed towards positions corresponding to the seven pixels of the LAsMA array are shown in Fig. [10](#lasma_dammo). These positions were observed in the $1_{01}-0_{00}$ lines with APEX. The $1_{11}-1_{01}$ spectra are extracted from the maps observed with the IRAM 30 m telescope. The $1_{11}-0_{00}$ spectra of $\rm NHD_2$ observed with APEX are shown in Fig. [11](#lasma_ddammo). In both figures, the predictions using the abundance profile described in Sect. [6](#updown) are shown in red. In this profile, the maximum fractional abundance is assumed to be found at intermediate densities, with decreasing tendencies both towards the centre and towards the outer boundary of the core. The maximum values are given at the top of the panels. The offset from the core centre is indicated on the top right of each panel.

(160,110)(0,0) (40,40)

(0,0) ![image](onh2d_9.30e-09_pnh2d_3.20e-09_0_0.ps)

(19,4)

(0,0) ![image](onh2d_9.30e-09_pnh2d_3.20e-09_21_-36.ps)

(-1,41)

(0,0) ![image](onh2d_9.30e-09_pnh2d_3.20e-09_41_1.ps)

(20,75)

(0,0) ![image](onh2d_9.30e-09_pnh2d_3.20e-09_20_35.ps)

(63,74)

(0,0) ![image](onh2d_9.30e-09_pnh2d_3.20e-09_-23_35.ps)

(80,38)

(0,0) ![image](onh2d_9.30e-09_pnh2d_3.20e-09_-40_-2.ps)

(59,3)

(0,0) ![image](onh2d_9.30e-09_pnh2d_3.20e-09_-19_-37.ps)

(160,110)(0,0) (40,40)

(0,0) ![image](onhd2_2.20e-09_pnhd2_1.10e-09_0_0.ps)

(19,4)

(0,0) ![image](onhd2_2.20e-09_pnhd2_1.10e-09_21_-36.ps)

(-1,41)

(0,0) ![image](onhd2_2.20e-09_pnhd2_1.10e-09_41_1.ps)

(20,75)

(0,0) ![image](onhd2_2.20e-09_pnhd2_1.10e-09_20_35.ps)

(63,74)

(0,0) ![image](onhd2_2.20e-09_pnhd2_1.10e-09_-23_35.ps)

(80,38)

(0,0) ![image](onhd2_2.20e-09_pnhd2_1.10e-09_-40_-2.ps)

(59,3)

(0,0) ![image](onhd2_2.20e-09_pnhd2_1.10e-09_-19_-37.ps)

# Observed and simulated ALMA spectra

The integrated p$\rm NH_2D(1_{11}-1_{01})$ line intensity map of L1544 and a selection of spectra observed with ALMA by (cite: 2022ApJ...929...13C) are shown in Fig. [12](#pnh2d_alma). The two line segments where the spectra are extracted start from the column density peak (our (0,0)), and are aligned with the minor and major axis of the elliptical core as determined in Sect. [3](#core_model). The spectra calculated from the ad hoc model discussed in Sect. [6](#updown) are shown in red. The position angle of the core as delineated by $\rm NH_2D$ emission ($\sim -25\ensuremath{^\circ}$) differs from the angle determined by $8\,\mu$ absorption ($\sim -36\ensuremath{^\circ}$). Similar figures were shown in (cite: 2022ApJ...929...13C), except that the strip along the main axis was directed south-east. There, the observed line emission weakens more quickly towards the core edge than in the north-west, where the spheroidal model agrees well with the observations.

(160,50) (-17,2)

(0,0) ![image](l1544_alma_pnh2d.ps)

(42,0)

(0,0) ![image](l1544_pnh2d_minor.ps)

(106,0)

(0,0) ![image](l1544_pnh2d_major.ps)

(-2,46)**(a)** (48,46)**(b)** (113,46)**(c)**

[^1]: The data were collected with the Atacama Pathfinder EXperiment (APEX; programme ID M-0112.F-9506A-2023), and with the 30 metre telescope of the Institut de radioastronomie millimétrique (IRAM). The APEX Project is led by the Max Planck Institute for Radio Astronomy at the ESO La Silla Paranal Observatory.

</paper>

Write the methods card for this paper.