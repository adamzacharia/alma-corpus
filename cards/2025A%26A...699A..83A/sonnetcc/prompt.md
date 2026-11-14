# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...699A..83A\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...699A..83A",
 "title": "Molecular gas excitation and outflow properties of obscured quasars at z ∼ 0.1",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Audibert, A.",
 "n_authors": 7,
 "arxiv_id": "2505.02759",
 "doi": "10.1051/0004-6361/202453291",
 "alma_projects_linked_by_archive": [
  "2011.0.00652.S",
  "2012.1.00797.S",
  "2013.1.00180.S",
  "2016.1.01535.S",
  "2018.1.00699.S",
  "2018.1.00870.S",
  "2018.1.01767.S"
 ]
}
```

Paper text:
<paper>
# Molecular gas excitation and outflow properties of obscured quasars at $z\sim$0.1

# Introduction

Active Galactic Nuclei (AGN) are nowadays understood as events in the life-cycle of a galaxy (cite: harrison24) due to their short and episodic nature (cite: martini04; hickox14; king15; schawinski15). The accretion of matter onto the supermassive black holes (SMBHs) in the center of galaxies and subsequent release of radiation and kinetic energy in form of outflows, profoundly influence the surrounding interstellar medium (ISM) and galactic-scale gas reservoirs (cite: veilleux20; valentini20; santi21; santi24; mandal21; Ward24; cra22). AGN feedback plays a pivotal role in shaping the evolution of massive galaxies by regulating the growth of their SMBHs and regulating star formation within their host galaxies (cite: croton06; dimatteo08; harrison17; nelson19; harrison24).

It is widely recognized that AGN feedback operates through two primary channels: the "quasar/radiative" mode and the "radio/kinetic" mode (cite: fabian12; dubois16). The quasar mode predominates in luminous AGN with high accretion rates, where radiatively-driven wide-angle winds are launched and commonly manifests in high-redshift, young quasars (cite: king03; zubovas12; bieri17). The radio mode is often associated with collimated relativistic jets, primarily observed in low-luminosity AGN with low accretion rates. The kinetic energy deposit by the jets into the the galaxies delays cooling flows from the intracluster/intragroup medium and prevents the formation of extremely massive galaxies (cite: fabian12; mcnamara12; bourne17; bourne23).

Despite this dichotomy between feedback modes, low-to-moderate luminosity ($\log P_{\rm1.4GHz}<10^{24}$ W Hz$^{-1}$) kiloparsec scale radio jets are starting to be recognised as a potential driver of multi-phase outflows in radiatively efficient “radio-quiet” quasars. For example, in the case of optically selected type 2 quasars (QSO2s; e.g. (cite: reyes08)), compact radio jets are associated with morphologically and kinematically distinct features in the ionized and molecular gas, such as outflowing bubbles and increased turbulence, revealing jet-gas interactions on galactic scales (cite: mullaney13; vm17; cra22; girdhar22; ane23; venturi23; speranza24; ulivi24). Simulations show that indeed, confined low-power jets ($P_{\rm jet}\sim10^{43-44}$ erg s$^{-1}$) are able to induce feedback into the ISM in the form of local turbulence and shocks that alter the physical conditions of the surrounding gas (cite: mukherjee18sim; meenakshi22; talbot22).

Hosting ubiquitous galactic scale multi-phase outflows, QSO2s offer an excellent opportunity to study both quasar and radio mode AGN feedback impact on the host galaxies properties. In particular, the impact of AGN on the molecular gas content of the ISM plays a critical role for galaxy evolution, since in the nearby Universe, the cold molecular gas phase appears to carry the bulk of the outflow mass budget, while the ionized gas phase only carries a small fraction of the total outflowing mass, at least for low-to-intermediate AGN luminosities (cite: fiore17; fluetsch19). However, most of the molecular outflows traced using CO were detected in low-luminosity AGN (cite: combes13; ane19; ane21; santi19; santi21; feruglio20; mavi21) and in ultra-luminous infrared galaxies (cite: feruglio10; cicone14; santi15; pereira18; fluetsch19; lamperti22; luke24) and until recently, the high-luminosity regime was scarcely observed in the molecular gas phase.

In the quasar regime of AGN luminosities ($L_{\rm AGN}\gtrsim10^{45-46}$ erg s$^{-1}$), where most massive outflows are expected in the molecular phase, recent observational results revealed a different scenario. In a sample of seven QSO2s at redshifts $z\sim$0.1 observed with the Atacama Large Millimeter/submillimeter Array (ALMA) in CO(2-1) at 0.2$''$ (400 pc), RA22 reported

cold molecular outflows in the five QSO2s with CO(2-1) detections. The molecular mass outflow rates ($\dot{M}_{\rm out}$) are lower than those expected from their AGN luminosities according to empirical scaling relations (cite: cicone14; fiore17; fluetsch19). The measured outflow mass rates and velocities, of Ṁ$_{\rm out}\sim$8-16  M$\rm _{\odot}\, yr^{-1}$ and $v_{\rm out}\sim$200-350 km s$^{-1}$ ( RA22), are intermediate between those of the molecular outflows detected in Seyfert galaxies ($\dot{M}_{\rm out}$$\sim$0.3-5  M$\rm _{\odot}\, yr^{-1}$, $v_{\rm out}\sim$90-200 km s$^{-1}$) and ULIRGs hosting AGN ($\dot{M}_{\rm out}$$\sim$60-400  M$\rm _{\odot}\, yr^{-1}$, $v_{\rm out}\sim$600-1200 km s$^{-1}$). See RA22  for a discussion on the different outflows properties in these systems.

Additionally, molecular outflows with sizes of a few kiloparsecs were detected in four QSO2s with redshifts z\<0.2 using CO(3-2) observations at 0.3$''$-0.6$''$ spatial resolution, and in the case of two of the targets molecular gas was detected extending along 5-13 kpc scale radio lobes of these “radio-quiet” sources (cite: girdhar24). In the case of the the ‘Teacup’, a radio-quiet quasar hosting a compact jet almost coplanar with the cold molecular disk, the bulk of the molecular outflow is mostly detected along the direction perpendicular to the compact radio jet (cite: ane23). This is traced by the large CO velocity dispersion and also by a high L$^\prime_{\rm CO(3-2)}/L^\prime_{\rm CO(2-1)}$ line ratio (R$_{\rm 32}$) perpendicular to the radio jet. A comparison with the tailored simulations of jet-ISM interaction first presented in (cite: mukherjee18sim) and (cite: meenakshi22) supports an scenario where the radio jet compresses and accelerates the molecular gas, driving a lateral outflow that shows enhanced turbulence and gas excitation perpendicular to the radio jet in the Teacup ( AA23). Similar enhanced velocity dispersion perpendicular to jets has been observed in CO(3-2) for another QSO2 by (cite: girdhar22) and in a few QSO2s in the ionized gas traced by \[OIII\] (cite: venturi23; speranza24; ulivi24).

Altogether, these results suggest that other factors aside from AGN luminosity, such as the jet power, the spatial distribution of the dense gas in the ISM, and the coupling between jets and the dense gas, might also be relevant for driving more or less massive molecular outflows ( RA22, AA23).

An alternative approach for discerning the imprints of AGN feedback on molecular gas involves examining various CO transitions, or CO spectral line energy distributions (SLEDs), which provide insights into the mechanisms driving molecular gas excitation. The CO excitation is suggested to be driven by photodissociation regions (PDRs) and X-ray-dominated regions (XDRs), displaying a wide range of temperature and gas densities (cite: hollenbach99; meijerink07; esposito22; esposito24). Processes related to AGN activity, such as shocks induced by jets/outflows and by X-ray emission can enhance the gas emission, specially at high J transitions (cite: vanderwerf10; mingozi18; vallini19). Recently, (cite: moly24) analyzed multiple integrated CO transitions in a sample of 17 QSO2s at z\<0.2 observed with the Atacama Compact Array (ACA) or the Atacama Pathfinder EXperiment telescope (APEX). Their CO SLEDs indicate that AGN feedback does not seem to exert a substantial influence on the molecular gas content and excitation on global galaxy scales. Instead, they propose that its effects might be observed on localized and more nuclear scales that cannot be resolved with the ACA and APEX observations. Indeed, spatially resolved line ratios offer a means to explore these scales and unveil localized alterations in gas excitation attributable to jets and/or outflows, as evidenced by elevated values of low-J CO line ratios observed in certain jetted Seyfert/radio galaxies (cite: santi14; dasyra16; oosterloo17; oosterloo19; fotopoulou19; ruffa22). However, investigations into local variations in gas conditions due to compact jets or AGN-driven outflows in“radio-quiet” quasars utilizing spatially resolved molecular line ratios have thus far been limited to the study of the Teacup galaxy ( AA23).

In this work we present an analysis of the molecular gas kinematics and excitation of six QSO2s which are part of the Quasar Feedback ([QSOFEED](http://research.iac.es/galeria/cra/qsofeed/)) sample, using ALMA CO(3-2) observations at 0.25$''$$-$0.6$''$ (450$-$1300 pc) resolution, in addition to the CO(2-1) data at 0.2$''$ resolution first presented in RA22. The observations used in this work and the data reduction are described in Section [2](#sec:data), and the morphology, kinematics, and CO line ratios are presented in Section [3](#sec:results). We discuss the dependency of the molecular outflow energetics on the AGN, radio-jet, and host galaxy properties in Section [4](#sec:discussion), and the main conclusions are drawn in Section [5](#sec:sum). We adopt a flat $\Lambda$CDM cosmology with H$_{\rm 0}$=70 km s$^{-1}$Mpc$^{-1}$, $\Omega_{\rm M}$=0.3, and $\Omega_{\rm \Lambda}$=0.7.

# Sample and observations

This work is part of the QSOFEED project (cite: cra22; cra25; pierce23; bessiere24; speranza24), whose aim is to

characterise and understand the direct impact of AGN feedback on the central region of nearby quasar host galaxies. The QSOFEED sample was drawn from the compilation of narrow-line AGN by (cite: reyes08) and were selected based on their \[OIII\] luminosites ($L_{\rm [OIII]}>10^{8.5}L_\odot$) and redshits ($z<$0.14), resulting in a sample of 48 QSO2s with stellar masses ranging from 10$^{10.7}$ to 10$^{11.6}$M$_\odot$. The redshift cut was set to detect 2.12 $\mu$m H$_2$ emission line in the near-infrared (NIR; see for instance (cite: cra17; cra19; speranza22; mavi25)) from the ground. The ionized outflow properties and stellar populations of the full sample are reported in (cite: bessiere24) and the optical morphologies, which are dominated by galaxy interactions, in (cite: pierce23).

The subset of six quasars presented here consist of the five QSO2s with CO(2-1) ALMA observations at 0.2$''$ spatial resolution analysed in RA22 plus J1347+1217 (also known as 4C12.50 and F13451+1232), a ULIRG with the largest radio luminosity in the QSOFEED sample. The main properties of the selected six QSO2s are listed in Table [\[tab:main\]](#tab:main). In this work, we re-analysed the CO(2-1) data of the five QSO2s presented in RA22 together with archival ALMA CO(3-2) observations at 0.25$''$$-$0.6$''$ resolutions (corresponding to physical scales of 450 pc to 1.1 kpc at the redshifts of our targets), and in the case of J1347+1217, we use publicly available CO(2-1) and CO(3-2) ALMA observations at similar angular resolution, first presented in (cite: fotopoulou19) and (cite: lamperti22).

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| SDSS ID | z | D$_{\rm L}$ | Scale | log L$_{\rm [OIII]}^{\rm corr}$ | log L$_{\rm bol}$ | log L$_{\rm 1.4GHz}$ | log M$_{\rm*}$ | SFR | Galaxy |  |  |
|  | SDSS | (Mpc) | (kpc/$''$) | (L$_{\rm \ensuremath{\odot}}$) | (erg/s) | (W/Hz) | (M$_{\rm \ensuremath{\odot}}$) |  M$\rm _{\odot}\, yr^{-1}$ | Morphology |  |  |
| J101043.36+061201.4 | 0.0977 | 449 | 1.807 | 9.30 | 45.54 | 24.37 | 10.99 | 30 | Interacting ETG |  |  |
| J110012.39+084616.3 | 0.1004 | 462 | 1.851 | 9.60 | 45.84 | 24.18 | 11.02 | 34 | Barred spiral |  |  |
| J134733.36+121724.3 | 0.1217$^*$ | 568 | 2.189 | 9.28 | 45.52 | 26.30 | 11.70 | 59$^\dag$ | Merging ETG |  |  |
| J135646.10+102609.0 | 0.1232 | 576 | 2.213 | 9.29 | 45.53 | 24.36 | 11.27 | 69 | Merging ETG |  |  |
| J143029.88+133912.0 | 0.0851 | 388 | 1.597 | 9.58 | 45.82 | 23.67 | 11.15 | 12 | Post-merger ETG |  |  |
| J150904.22+043441.8 | 0.1115 | 517 | 2.028 | 9.79 | 46.03 | 23.81 | 10.94 | 34 | Barred spiral |  |  |

Table notes: The values of L$_{\rm bol}$ were derived from the extinction-corrected \[OIII\] luminosities from (cite: kong18), listed in column 5, multiplied by the factor of 474 from (cite: lamastra09).

Rest-frame radio luminosities are calculated from integrated FIRST fluxes (cite: becker95), assuming a spectral index $\alpha$=-0.7, and the stellar masses and SFRs are from RA22.

$^*$ The redshift measured from the CO(2-1) is computed by (cite: lamperti22). $^\dag$ SFR from (cite: bessiere24).

The ALMA observations of the CO(2-1) and CO(3-2) emission lines were observed in bands 5, 6, and 7. The CO(2-1) observations and data reduction are described in detail in RA22, and those of J1347+1217 in (cite: lamperti22). We retrieve the CO(3-2) observations from the ALMA archive for five of the targets, as no CO(3-2) observations are available for J1509+0434. These observations are part of different projects, whose details, including principal investigator (PI) name, project ID, synthesised beam, and root mean square (rms) noise are listed in Table [\[tab:obs\]](#tab:obs).

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Short | CO | ALMA | $t_{\rm int}$ | beam | beam | MRS | rms | $v_{\rm res}$ | PI | project |  |  |
| name | transition | band | \(h\) | ($''$ $\times$ $''$) | (pc $\times$ pc) | ($''$) | (mJy) | ( km s$^{-1}$) | name | ID |  |  |
| J1010 | (2-1) | 5 | 0.17 | 0.76$\times$0.67 | 1373 $\times$ 1211 | 7.3 | 0.82 | 11.2 | C. Ramos Almeida | \(1\) |  |  |
|  | (3-2) | 7 | 1.58 | 0.25$\times$0.24 | 452 $\times$ 434 | 8.3 | 0.31 | 15.0 | A. Thomson | \(2\) |  |  |
| J1100 | (2-1) | 5 | 0.87 | 0.23$\times$0.20 | 426 $\times$ 370 | 7.4 | 0.42 | 11.2 | C. Ramos Almeida | \(1\) |  |  |
|  | (3-2) | 7 | 1.35 | 0.31$\times$0.24 | 574 $\times$ 444 | 8.1 | 0.34 | 15.0 | A. Thomson | \(2\) |  |  |
| J1347 | (2-1) | 5 | 1.34 | 0.22$\times$0.17 | 482 $\times$ 372 | 4.2 | 0.74 | 11.4 | M. Pereira Santaella | \(3\) |  |  |
|  | (3-2) | 7 | 0.08 | 0.61$\times$0.47 | 1335 $\times$ 1029 | 4.3 | 1.39 | 10.0 | K. Dasyra | \(4\) |  |  |
| J1356 | (2-1) | 5 | 0.99 | 0.24$\times$0.23 | 531 $\times$ 509 | 8.7 | 0.39 | 11.4 | C. Ramos Almeida | \(1\) |  |  |
|  | (3-2) | 7 | 1.08 | 0.53$\times$0.35 | 1125 $\times$ 743 | 9.4 | 1.30 | 16.0 | J. Greene | (5,6) |  |  |
| J1430 | (2-1) | 6 | 0.56 | 0.24$\times$0.19 | 383 $\times$ 303 | 7.5 | 0.39 | 11.0 | C. Ramos Almeida | \(1\) |  |  |
|  | (3-2) | 7 | 0.51 | 0.60$\times$0.54 | 958 $\times$ 862 | 5.3 | 1.93 | 10.0 | G. Lansbury | \(7\) |  |  |
| J1509 | (2-1) | 5 | 0.91 | 0.26$\times$0.23 | 527 $\times$ 466 | 9.0 | 0.42 | 11.3 | C. Ramos Almeida | \(1\) |  |  |

Table notes: Columns indicate the main observational properties of the sample: name, CO transition, integration time, beam size, maximum recoverable scale (MRS), root mean square (rms), velocity resolution, Principal Investigator (PI) and ALMA Project ID. Project IDs: (1) 2018.1.00870.S, (2): 2018.1.01767.S, (3) 2018.1.00699.S, (4) 2013.1.00180.S, (5) 2011.0.00652.S, (6) 2012.1.00797.S, (7) 2016.1.01535.S

The CO(3-2) data were calibrated using the appropriate CASA  software version (cite: casa) in the pipeline mode and using the standard flux, bandpass, and phase calibrators. Once calibrated, the imaging and cleaning were performed with the task TCLEAN. The spectral line map was obtained after subtracting the continuum in the $uv$-plane using the tasks UVCONTSUB and a 0th order polynomial in the channels free from emission lines. The CO(3-2) data cubes were produced with spectral resolutions listed in Table [\[tab:obs\]](#tab:obs) and using Briggs weighting mode and a robust parameter set to 0.5 in order to achieve the best compromise between resolution and sensitivity. In the case of J1347, the CO(3-2) data reduction was performed by (cite: fotopoulou19) using similar CASA  routines. Finally, the datacubes were corrected for primary beam attenuation. In order to study the line ratios and compare the CO(2-1) to the new CO(3-2) datacube, we regridded the CO(2-1) data to the same pixel scale of the CO(3-2) and then convolved it to the same common beam sizes.

The auxiliary radio data used here are the 6 GHz Very Large Array (VLA) C-band observations of J1010, J1100, J1356, and J1430 first presented in (cite: jarvis19; jarvis21). These data were obtained in two different configurations: the high-resolution (0.25$''$, HR) A-array and the low-resolution (1.0$''$, LR) B-array maps. In the case of J1100, we also consider the e-MERLIN observations at 1.5 GHz obtained at a 0.3$''$ resolution from (cite: jarvis19). In the case of J1347 (4C12.50), we used the 15 GHz observations from the Very Long Baseline Array (VLBA), retrieved from the NASA/IPAC Extragalactic Database (NED) and presented in (cite: kellermann04). Finally, no VLA observations are yet available for J1509. The main properties of the radio observations used in this work are listed in Table [\[tab:radio\]](#tab:radio) of Appendix [6](#sec:radio).

# Results and analysis

## Moment maps of the CO(3-2) emission

The properties of the molecular gas traced by the CO(2-1) emission are presented in RA22 for five of the QSO2s and in (cite: lamperti22) for J1347. In order to show the distribution of the CO(2-1) gas from a slightly different perspective and to allow a comparison with the CO(3-2) emission, we computed the peak intensity maps of CO(2-1), which are shown in Figure [1](#fig:tpeaks). As discussed in RA22, the CO(2-1) emission of the QSO2s reveals a variety of morphologies: from spiral arms in the case of the J1100 and J1509 to double-peaked structures in J1010, J1347, and J1430, and a central concentration in J1356 together with a west arc that is part of an on-going merger. One of the advantages of the peak maps is that clumpy and narrow structures can be better seen, since they are smoothed in the integrated intensity (moment 0) maps. The CO(2-1) peak maps clearly exhibit the double-peaked features in J1010, J1347, and J1430 (the merging/interacting systems) but also enhance conspicuous regions in the spiral systems, that appear diluted in the integrated intensity maps. The CO(2-1) moment 0 map of J1100, shown in RA22, revealed only some of the clumps mainly along the bar, while the peak map shows clumps spread along the two spiral arms. In the case of J1509, the CO(2-1) moment 0 map shows centrally concentrated gas, and the CO(2-1) peak map reveals several clumpy structures within the central region.

![](tpeaks.png)

Using the CO(3-2) data cubes, we computed the peak intensity, integrated intensity (moment 0), intensity-weighted velocity field (moment 1), and velocity dispersion (moment 2) maps, which are shown in Figure [2](#fig:co32moms). The moment maps were created using the CASA task `immoments` and a 3$\sigma_{\rm rms}$ clipping. The CO(3-2) maps of J1430 (Teacup) were presented in Appendix A of AA23, but they are included here for comparison with those of the other QSO2s. Double-peaked morphologies[^1] are also seen in the CO(3-2) peak intensity maps (left panels of Figure [2](#fig:co32moms)) for the interacting quasars J1010, J1347, and J1430. The CO(3-2) distribution shown in the moment 0 maps (central-left panels) is more compact than the CO(2-1) in the cases of J1010 and J1356, although the western arc part of the merger in the latter is less noticeable in CO(3-2) than in CO(2-1). For J1347, the coarser resolution of the CO(3-2) data makes the southern part of the merger clearly detected. In the case of J1100, the bar and spiral arms are prominent in CO(3-2), similar to the morphology seen in CO(2-1).

![](CO32_new.png)

The integrated velocity field maps (moment 1) in the middle-right panels of Figure [2](#fig:co32moms) show a rotation pattern for the main disk of the five quasars displayed, with projected velocities of $v\approx \pm$220 km s$^{-1}$, except for J1010 that shows a higher amplitude up to $v\approx \pm$300 km s$^{-1}$. We note that the interacting western arc in J1356 has blueshifted velocity components, while the southern region part the merging system in J1347 shows redshifted velocities. The fact that the velocity pattern of the merging regions coincides with the blue(red)shifted sides of the main disk indicates that the gas there is starting to settle into them.

In the right panels of Figure [2](#fig:co32moms) we present the CO(3-2) velocity dispersion (moment 2) maps. The central velocity dispersions are typically $v_{\rm disp}\gtrsim$100  km s$^{-1}$ in the nucleus of the galaxies, with decreasing values outwards. J1356 shows high values of $v_{\rm disp}$, of $\sim$200  km s$^{-1}$, which are larger than the maximum value of $\sim$160 km s$^{-1}$ measured from CO(2-1) by RA22. The same is observed for the barred spiral J1100, where the CO(3-2) and CO(2-1) maximum dispersion values are $\sim$160  km s$^{-1}$ and $\sim$120  km s$^{-1}$, respectively. The opposite is found for J1010, since the CO(3-2) $v_{\rm disp}$ in the nucleus peaks at 100  km s$^{-1}$, smaller then the 120  km s$^{-1}$ measured for the CO(2-1). The velocity dispersion values of CO(3-2) for J1347 are centrally peaked at $\sim$140 km s$^{-1}$, same as those reported in CO(2-1) by (cite: lamperti22). There is a difference in the southern merging region, where CO(2-1) exhibits low values ($<$40 km s$^{-1}$), indicative of gas settling in the merger (see the CO(2-1) velocity dispersion map in Figure [3](#fig:ratiosdisp)), while in CO(3-2) the same region shows values of up to 160 km s$^{-1}$. We note that higher velocity dispersions measured in CO(3-2) can be due to beam smearing, as these observations have coarser resolution then the CO(2-1) data. Indeed, when convolving to a common resolution the values measured for CO(3-2) and CO(2-1) are more similar.

## Integrated fluxes and line ratios

+:-----+:--------------------+:----------------:+:---------------------------------------:+:------------------------:+:------:+:-----:+:------------:+
| Name | CO                  | S$_{\rm CO}$     | $L^\prime_{\rm CO(J\rightarrow {J-1})}$ | M$_{\rm H_2}$            | Radius         | R$_{\rm 32}$ |
|      +---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+              |
|      | (J$\rightarrow$J-1) | (Jy km s$^{-1}$) | 10$^9$($\rm K~km~s^{-1}~pc^{2}$)        | 10$^9$( M$_{\rm \odot}$) | ($''$) | (kpc) |              |
+------+---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+--------------+
|      | (2-1)               | 7.92 $\pm$ 0.96  | 0.89 $\pm$ 0.11                         | 3.87 $\pm$ 1.59          | 1.33   | 2.4   | 0.75         |
+------+---------------------+------------------+-----------------------------------------+--------------------------+        |       |              |
|      | (3-2)               | 13.35 $\pm$ 1.36 | 0.66 $\pm$ 0.07                         | 2.89 $\pm$ 1.16          |        |       |              |
+------+---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+--------------+
|      | (2-1)               | 30.6 $\pm$ 3.4   | 3.63 $\pm$ 0.40                         | 15.8 $\pm$ 6.3           | 2.70   | 5.0   | 0.22         |
+------+---------------------+------------------+-----------------------------------------+--------------------------+        |       |              |
|      | (3-2)               | 15.34 $\pm$ 1.54 | 0.81 $\pm$ 0.08                         | 3.53 $\pm$ 1.41          |        |       |              |
+------+---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+--------------+
|      | (2-1)               | 41.5 $\pm$ 0.6   | 7.30 $\pm$ 0.11                         | 5.8 $\pm$ 3.7            | 1.92   | 4.2   | 0.69         |
+------+---------------------+------------------+-----------------------------------------+--------------------------+        |       |              |
|      | (3-2)               | 64.1 $\pm$ 8.1   | 5.01 $\pm$ 0.63                         | 3.0 $\pm$ 1.3            |        |       |              |
+------+---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+--------------+
|      | (2-1)               | 14.7 $\pm$ 2.3   | 2.65 $\pm$ 0.42                         | 11.5 $\pm$ 5.2           | 2.28   | 5.0   | 0.30         |
+------+---------------------+------------------+-----------------------------------------+--------------------------+        |       |              |
|      | (3-2)               | 9.9 $\pm$ 1.1    | 0.79 $\pm$ 0.09                         | 3.46 $\pm$ 1.42          |        |       |              |
+------+---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+--------------+
|      | (2-1)               | 16.9 $\pm$ 1.8   | 1.43 $\pm$ 0.15                         | 6.24 $\pm$ 2.48          | 0.81   | 1.3   | 0.54         |
+------+---------------------+------------------+-----------------------------------------+--------------------------+        |       |              |
|      | (3-2)               | 20.6 $\pm$ 3.6   | 0.78 $\pm$ 0.14                         | 3.38 $\pm$ 1.60          |        |       |              |
+------+---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+--------------+
|      |                     |                  |                                         |                          |        |       |              |
+------+---------------------+------------------+-----------------------------------------+--------------------------+--------+-------+--------------+

Table notes: The CO(2-1) measurements of J1347 are from (cite: lamperti22), and since this QSO2 is a ULIRG, the mass was calculated using an $\alpha_{\rm CO}$=0.8  M$_{\rm \odot}$(K  km s$^{-1}$ pc$^2$)$^{-1}$. For the other five QSO2s the values are from RA22 and the masses were computed using an $\alpha_{\rm CO}$=4.35  M$_{\rm \odot}$(K  km s$^{-1}$ pc$^2$)$^{-1}$.

We report the integrated fluxes, $\rm S_{CO}\Delta V$, detected in CO(2-1) and CO(3-2) in Table [\[tab:co\]](#tab:co). To compute the total CO masses, we first convert the integrated flux measurements to CO luminosities $L^\prime_{\rm CO}$ , in units of $\rm K~km~s^{-1}~pc^{2}$, using the following equation of (cite: solomon05): $$\begin{equation}
{L^\prime_{\rm CO}}(K km s^{-1} pc^2) = 3.25\times10^7 \frac{S_{\rm CO}\Delta V}{(1+z)^3}  \left( \frac{D_{\rm L}}{\nu_{\rm obs}} \right)^2, 
\end{equation}$$ where $\nu_{\rm obs}$ is the observed frequency of the CO line, in GHz, $D_{\rm L}$ is the luminosity distance of the galaxy, in Mpc, $z$ is the redshift and $\rm S_{\rm CO}\Delta V$ is the integrated flux in Jy km s$^{-1}$. The CO transitions can be converted to $L^\prime_{\rm CO(1-0)}$ adopting a line ratio, called R$_{\rm J-1}=\frac{L^\prime_{\rm CO(J\rightarrow {J-1} )}}{L^\prime_{\rm CO(1\rightarrow0)}}$. Under the assumption that the gas is thermalised and optically thick, $L^\prime_{\rm CO(3-2)} = L^\prime_{\rm CO(2-1)} = L^\prime_{\rm CO(1-0)}$, and therefore the brightness temperature ratio R$_{\rm J-1}$=1.

The molecular masses can be calculated from ${L^\prime_{\rm CO(1-0)}}$ using the CO-to-H$_2$ conversion factor $M_{H_2}=\alpha_{\rm CO} {L^\prime_{\rm CO(1-0)}}$. We adopted the standard Galactic CO-to-H$_2$, conversion factor of $\alpha_{\rm CO}=4.36M_\odot (K kms^{-1}pc^{2})^{-1}$ (cite: tacconi13; bolatto13).

The molecular masses inferred from the CO(3-2) emission are of the order of (3-4)$\times 10^9$ M$_{\rm \odot}$ (see Table [\[tab:co\]](#tab:co)), which are systematically lower than the ones derived using the CO(2-1) observations in RA22 and (cite: lamperti22). Both mass estimates were computed under the same assumptions of $\alpha_{\rm CO}$ and thermalised gas $R_{\rm 31}$=$R_{\rm 21}$=1, therefore indicating that the molecular gas in the QSO2s is less excited and has temperature and density conditions below the thermalised limit. Indeed, we derived the integrated $R_{\rm 32}$ line rations, also listed in Table [\[tab:co\]](#tab:co), and we find values of $R_{\rm 32}<$1. The values derived for the integrated line ratios range 0.22$<$R$_{\rm 32}$$<$0.75, with an average value of $<$R$_{\rm 32}$$>$=0.5$\pm$0.2, similar to the line ratios typically measured in spiral and disk galaxies (cite: leroy22). However, in the next section we will present spatially resolved line ratios to examine possible localised changes in the gas conditions of the QSO2s. A discussion of the physical condition of the gas is addressed in Section [4.3](#sec:gasphysics).

![](ratios-disp-new.png)

## Spatially resolved line ratios

The spatial resolution of our ALMA CO(2-1) and CO(3-2) observations allows us to produce spatially resolved line ratio maps, which can provide insights into the changes in gas excitation due to the AGN ionization, jets, and star formation. Line ratio maps allow us to unveil signatures that differentiate outflows from ambient ISM. In Figure [3](#fig:ratiosdisp) we present the R$_{\rm 32}$ maps (top panels) together with the velocity dispersion (bottom panels) of the five quasars, similar to the analysis reported for the Teacup in AA23. The radio continuum emission from the VLA HR data at 6 GHz is indicated as black contours (except for J1100 and J1347, for which we report e-MERLIN data at 1.5 GHz and VLBA data at 15 GHz, respectively). The PA orientation of the radio emission is indicated with black solid lines. The ALMA continuum at either 200 or 300 GHz is shown in blue contours overlaid on the velocity dispersion maps.

The R$_{\rm 32}$ maps shown in the top panels of Figure [3](#fig:ratiosdisp) show higher values in the nuclear region, of R$_{\rm 32}$$\sim$0.7-0.9, compared to the smaller values found across the CO disks, of R$_{\rm 32}$$\sim$0.2-0.5. The regions of enhanced R$_{\rm 32}$ are usually co-spatial with those showing high central velocity dispersion in the bottom panels.

No clear trend regarding the orientation of high R$_{\rm 32}$ and velocity dispersion with the PA of the radio jets is found for the QSO2s. Apparent enhanced turbulence and gas excitation perpendicular to the radio jet is only found for the Teacup, as reported in AA23. Tentative perpendicular orientation of the R$_{\rm 32}$ and velocity dispersion is found for J1100, where the PA$\rm_{jet}$=175$^\circ$ derived from the e-MERLIN contours is misaligned by $\sim$135$^\circ$ with the axis of high R$_{\rm 32}$ and dispersion (PA$\sim$40$^\circ$).

The region showing high values of R$_{\rm 32}$ in J1347 appears perpendicular to the orientation of the 100 pc jet, whilst the region of high velocity dispersion is aligned with the jet.

For J1010 and J1356, the VLA HR data is unresolved, and therefore the orientation of possible jets (as suggested by the spectral index analysis in (cite: jarvis19)) is merely indicative and derived from the larger scale radio structures seen in the low-resolution radio images.

Therefore, although some targets exhibit a degree of (anti-)alignment between R$_{\rm 32}$, velocity dispersion, and radio emission, the results are not consistent across the sample. One of the goals of the QSOFEED project is to understand how different outflow, jet, and ISM properties — and their interactions, including orientation and energy exchange among others — shape the observed gas kinematics and excitation. Given the diverse and complex nature of the individual targets, a larger sample is required to explore the broad parameter space and derive more general conclusions.

## Modelling the kinematics of the molecular gas

We analysed the CO(2-1) and CO(3-2) kinematics using the “3D-Based Analysis of Rotating Objects from Line Observations” (^3D^BAROLO) software by (cite: barolo15). ^3D^BAROLO  performs a 3D tilted-ring modelling of the emission line datacubes to derive the parameters that better describe the kinematics of the data. We ran ^3D^BAROLO  on both CO(3-2) and CO(2-1) datacube in order to investigate non circular motions, since the code allows us to infer radial velocities in the fit of the rotation curves.

The center was fixed to the position of the continuum peak at 200 GHz and we allowed ^3D^BAROLO to fit the inclination, PA, systemic velocity, rotation velocity, and dispersion as free parameters. For the initial guess on the inclination and PA, we used the parameters derived in RA22 and for the case of J1347 in (cite: luke24). We then fixed the inclination, PA, and systemic velocity to the average values derived from the first run[^2] and allow the code to fit only rotation and dispersion. We present the results of the analysis with ^3D^BAROLO in form of position-velocity diagrams (PVDs) along the major and minor axis of the CO(3-2) disk in Figures [4](#fig:pv1010)-[7](#fig:pv1356). Since the CO(2-1) ^3D^BAROLO fits are already shown in detail in RA22, here we just show the results for CO(3-2), although in the right panels of Figures [4](#fig:pv1010)-[7](#fig:pv1356) we also present the PVDs of the R$_{\rm 32}$ to identify regions having different gas excitation conditions. The R$_{\rm 32}$ PVDs were smoothed using a Gaussian kernel with a $\sigma$=1.5 to reveal intrinsic variations and reduce the noise due to a pixel-by-pixel ratio.

![](j1010pv.png)

In Figure [4](#fig:pv1010) the CO(3-2) PVDs for the quasar J1010 show a clear rotation pattern along the major axis (PA=288$^\circ$, or PA=-72$^\circ$). The ^3D^BAROLO  model is displayed as red contours and it reproduces well rotation up to velocities of $\sim$300 km s$^{-1}$, although it cannot fit the high-velocity gas within 0 and 1.5$''$ to the east, which shows velocities of up to -400 km s$^{-1}$ (see top left panel in Figure [4](#fig:pv1010)). This non-circular velocity feature is more clearly visualised in the high velocity map shown in Figure [8](#fig:highvel) and discussed in Section [4.1](#energetics). The line ratio PVDs shown on the right panels of Figure [4](#fig:pv1010) have typical values of R$_{\rm 32}$$\sim$0.8, in agreement with the global ratio derived from the integrated fluxes listed in Table [\[tab:co\]](#tab:co). However, there are several regions that show values R$_{\rm 32}$$>1$, indicating the presence of optically thin gas and/or gas with higher excitation temperatures. However, these regions with R$_{\rm 32}$$>1$ are distributed all over the minor and major axis slits, for both low and high velocity components.

![](j1100pv.png)

The CO(3-2) PVDs for the spiral J1100 are presented in the left panels of Figure [5](#fig:pv1100) and show clear rotation along the major axis (PA=69$^\circ$, same as the PA derived for the CO(2-1) line) that is well reproduced by the ^3D^BAROLO fit shown as red contours, and the typical 0th velocities along the minor axis. In the central region, concentrated in a radius of less than 0.4$''$ (740 pc), the PVDs along the major and minor axes show a large velocity gradient with velocities reaching $\pm$300 km s$^{-1}$. The ^3D^BAROLO  model reproduces well rotation up to velocities of $\sim$180 km s$^{-1}$, but it cannot fit the high velocities in the nuclear region. These high velocity regions coincide with the highest line ratios seen in the R$_{\rm 32}$ PVDs on the right panels of Figure [5](#fig:pv1100), with R$_{\rm 32}$ values between 0.6-1.2, higher than the typical values of R$_{\rm 32}$$<$0.5 found along the spiral arms at larger radii. Compared to the integrated value of $<$R$_{\rm 32}$$>$=0.22 in Table [\[tab:co\]](#tab:co), this indicates that the global ratio traces mostly the contribution from the galaxy disk.

![](j1347pv.png)

For the merging galaxy J1347, we show the PVDs in Figure [6](#fig:pv1347). The CO(3-2) along the major axis (top left panel) shows a rotation pattern oriented along the west-east direction (PA=248$^\circ$) that can be fit with the ^3D^BAROLO model up to velocities of $\sim$300 km s$^{-1}$. There is a clear excess of blueshifted velocities up to 420 km s$^{-1}$ in the central to east direction that cannot be fit by rotation. Along the minor axis (PA=-22$^\circ$, bottom left panel), the high blueshifted velocities are also present, and we can see the contribution from the southern part of the merger mostly in redshifted velocities. The line ratio PVDs (right panels of Figure [6](#fig:pv1347)) of the main disk (r$<$1$''$) have values of R$_{\rm 32}$$\sim$0.8, slightly larger than the global ratio derived from the integrated fluxes of $<$R$_{\rm 32}$$>$=0.69, as listed in Table [\[tab:co\]](#tab:co), and values R$_{\rm 32}$$<$0.5 across the southern part of the merger. However, the regions having the high blueshifted velocities both along the major and minor axes show the highest line ratios, of R$_{\rm 32}$$\sim$1-2, indicating the presence of optically thin/warmer fast gas.

![](j1356pv.png)

In Figure [7](#fig:pv1356) the CO(3-2) PVDs of J1356 show a less prominent contribution from rotation along the major axis (PA=110$^\circ$) for the main galaxy disk (r$<$0.5$''$ $\simeq$1.1 kpc) and the system present an overall large velocity dispersion (see Figure [3](#fig:ratiosdisp)). The blueshifted velocities seen between 0 and 1$''$ to the west correspond to the western arc of the merging system. The ^3D^BAROLO model, displayed as red contours, can reproduce rotation up to velocities of $\sim$300 km s$^{-1}$, but it fails to reproduce the high velocity gas at velocities up to **$\pm$**400 km s$^{-1}$, mostly detected at redshifted velocities. The line ratio PVDs on the right panels of Figure [7](#fig:pv1356) have typical values of R$_{\rm 32}$$\sim$0.6 along the main disk (or north nucleus in RA22) and R$_{\rm 32}$$<$0.5 along the western arc, higher than the value derived from the integrated intensities of $<$R$_{\rm 32}$$>$0.3. One possible reason is that the sensitivity of the CO(2-1) is much better than the CO(3-2), allowing for a clearer detection of the western arm and the southern nucleus of the system (see Appendix D.1 in RA22), while in the shallower CO(3-2) observations only part of the western arm is detected and the southern nucleus is undetected, making the integrated R$_{\rm 32}$ lower. On the other hand, we find R$_{\rm 32}$ values of up to 1.2 in regions that are co-spatial with the redshifted high velocity gas, indicating different excitation conditions there.

The PVDs of CO(2-1), CO(3-2), and R$_{\rm 32}$ of the Teacup (J1430) can be seen in Figure 2 of AA23 and are described in full there. We find values of R$_{\rm 32}$$\sim$0.4-0.8 across the disc, and the highest values, of up to R$_{\rm 32}$$\sim$1, in the region occupied by high-velocity blueshifted gas ($\sim$200-350 km s$^{-1}$) within 0 and 1$''$ to the south.

The regions of the QSO2s where we detected high velocity gas components and gas excitation differing from ambient gas conditions in the main disks are interpreted as outflowing gas. This interpretation is based on the fact that their kinematics cannot be explained by regular rotation, based on our analysis using ^3D^BAROLO, and they show higher excitation temperatures than those typically found in the galaxy disks of non-active star-forming galaxies. We note that this is the same outflow definition employed in (cite: cra22), but adding gas excitation. We note that in the case of the merging galaxies, J1347 and J1356, the observed non-rotational motions could be attributable to merger-induced flows. However, numerical simulations suggest that molecular gas velocity dispersions in mergers typically reach only tens of  km s$^{-1}$ (cite: bournaud08; bournaud11), which is significantly lower than the values that we measure in the QSO2s. Observationally, ALMA CO(3-2) observations of the overlapping region between the merging Antennae galaxies (NGC 4038/39), a prototypical merger, revealed knots of low-velocity dispersion ($\sim$10 km s$^{-1}$) and maximum values of up to $\sim$80 km s$^{-1}$ in supergiant molecular clouds (cite: whitmore14). Considering this, we favor the outflow interpretation to explain the observed kinematics and gas excitation.

## Molecular outflow properties

![](high-vels.png)

The determination of the outflow mass rates in the literature is performed using heterogeneous methods. From the observational point of view, it is challenging to obtain a precise determination of the outflow mass, radius, and velocities, all affected by uncertainties. Different methodologies and assumptions can lead to estimates that diverge in more than an order of magnitude (cite: kiara23; harrison24). For these reasons, here we consider three scenarios for estimating the outflow masses and mass rates, from least to most conservative, following AA23. To measure the fluxes and corresponding masses, we used the CO(2-1) data at the original 0.2$''$ resolution to avoid artefacts or wrong interpretations of the results due to possible beam smearing effects because of the larger CO(3-2) beam size. The only exception is for J1010, in which CO(3-2) was used because it has better spatial resolution (0.25$''$) than the CO(2-1) data (0.75$''$).

I) In the first scenario, we assume that all the molecular gas that cannot be reproduced with our rotating disc model is outflowing. Thus, we just integrated the emission from the ^3D^BAROLO model and subtracted it from the CO(2-1) datacube. We find that for the spirals J1100 and J1509 and the interacting early-type galaxy J1010, most of the CO(2-1) emission can be reproduced with rotation ($\sim$75%), while the mergers J1347 and J1356, and the post-merger system J1430 present more complex kinematics, with J1356 being dispersion-dominated (see Figure [18](#fig:vsig) in Appendix [8](#sec:vsig)) and therefore rotation accounts for $\sim$50% of the total CO emission. In this scenario, we adopted an outflow velocity, $v_{\rm out}$, calculated as the average of the mean redshifted and the mean blueshifted velocity residuals

from the ^3D^BAROLO fit shown in RA22 and in Appendix [7](#sec:baloro), using absolute values. These velocities are in the range 50$<v_{\rm out}<$100 km s$^{-1}$ (see Table [\[tab:prop\]](#tab:prop)).

+:-----:+:--------:+:----------------:+:--------------:+:-------:+:-------:+:------------------:+:----------------------------:+:-------------------------:+:------:+:------------------------:+:-------------------------------:+
| Name  | Scenario | $S_{\rm CO}$     | $v_{\rm out}$  | $r_{\rm out}$     | $M_{\rm out}$      | $\dot{M}_{\rm out}$          | $M_{\rm out}/M_{\rm H_2}$ | $\eta$ | $P_{\rm jet}$            | $\dot{E}_{\rm out}/P_{\rm jet}$ |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       |          | (Jy km s$^{-1}$) | ( km s$^{-1}$) | ($''$)  | (kpc)   | (10$^7$ M$_\odot$) | ( M$\rm _{\odot}\, yr^{-1}$) | (%)                       |        | (10$^{43}$ erg s$^{-1}$) |                                 |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | I        | 3.10$\pm$0.3     | 50             |         |         | 27.9$\pm$20        | 7.9$\pm$5.7                  | 7.2                       |        |                          | 0.0001                          |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
| J1010 | II       | 0.34$\pm$0.03    | 300            | 1.0     | 1.8     | 3.1$\pm$2.1        | 5.2$\pm$3.6                  | 0.8                       | 0.2    | 8.9                      | 0.0017                          |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | III      | 0.30$\pm$0.05    | 300            |         |         | 2.7$\pm$2.1        | 4.6$\pm$3.6                  | 0.7                       |        |                          | 0.0015                          |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | I        | 13$\pm$0.9       | 70             |         |         | 123$\pm$85.7       | 36.7$\pm$25.5                | 7.8                       |        |                          | 0.001                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
| J1100 | II       | 2.7$\pm$0.1      | 180            | 1.3     | 2.4     | 26$\pm$17.5        | 14.4$\pm$9.7                 | 1.6                       | 0.4    | 7.2                      | 0.001                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | III      | 1.0$\pm$0.1      | 180            |         |         | 9.5$\pm$6.9        | 5.2$\pm$3.8                  | 0.6                       |        |                          | 0.0004                          |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | I$^a$    |                  | 514            | 0.05    | 0.12    | 3.4                | 148                          | 0.6                       |        |                          | 0.023                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
| J1347 | II       | 0.9$\pm$0.2      | 300            | 0.29    | 0.65    | 13.2$\pm$10.5      | 62.9$\pm$50                  | 2.3                       | 1.1    | 53                       | 0.003                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | III$^b$  |                  | 390            | 0.23    | 0.52    | 4.2                | 31.6                         | 0.72                      |        |                          | 0.003                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | I$^c$    | 0.99$\pm$0.1     | 400            | 0.14    | 0.3     | 7.0                | 92.8                         | 1.1                       |        |                          | 0.053                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
| J1356 | II       | 0.89$\pm$0.07    | 300            | 0.58    | 1.3     | 12.9$\pm$9         | 26.2$\pm$18                  | 2.0                       | 0.4    | 8.9                      | 0.008                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | III$^d$  | 0.1$\pm$0.02     | 310            | 0.2     | 0.4     | 1.4$\pm$1.2        | 10$\pm$8.8                   | 0.22                      |        |                          | 0.003                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | I        | 7.6$\pm$0.9      | 100            |         |         | 51.5$\pm$48.2      | 44.0 $\pm$ 32.7              | 8.3                       |        |                          | 0.004                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
| J1430 | II       | 2.4$\pm$0.1      | 300            | 0.75    | 1.2     | 16.0$\pm$10.9      | 41.0$\pm$27.9                | 2.6                       | 3.4    | 3.3                      | 0.035                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | III      | 0.9$\pm$0.1      | 300            |         |         | 5.6$\pm$4.3        | 15.1$\pm$11.0                | 0.9                       |        |                          | 0.013                           |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | I        | 10.1$\pm$1.1     | 50             |         |         | 119$\pm$87         | 26.6 $\pm$ 19.6              | 6.7                       |        |                          | 0.0003                          |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
| J1509 | II       | 1.52$\pm$0.15    | 240            | 1.1     | 2.1     | 17.9$\pm$12.9      | 19.2$\pm$13.9                | 1.0                       | 0.6    | 6.1                      | 0.0058                          |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+
|       | III      | 1.29$\pm$0.14    | 240            |         |         | 15.2$\pm$11.1      | 16.3$\pm$12.0                | 0.9                       |        |                          | 0.0049                          |
+-------+----------+------------------+----------------+---------+---------+--------------------+------------------------------+---------------------------+--------+--------------------------+---------------------------------+

\
Table notes: The reported outflow velocities, $v_{\rm out}$, correspond to the projected velocities. The uncertainty in $\alpha_{\rm CO}=$0.8$\pm$0.5  M$_{\rm \odot}$(K  km s$^{-1}$ pc$^2$)$^{-1}$ (cite: downes98) is included in the mass error estimates. For J1347, the values reported for scenario I$^a$ are the nuclear outflow properties derived from CO(1-0) data at 0.05$''$ resolution by (cite: luke24) and for scenario III$^b$, the upper limits reported by (cite: lamperti22) for the unresolved outflow detected in CO(2-1), using the average outflow velocity and radius of 390 km s$^{-1}$ and 0.52 kpc that they adopted for non-detections. For J1356, the values reported for scenario I$^c$ correspond to the CO(3-2) outflow measurements reported by (cite: sun14), but adopting an outflow velocity of 400 km s$^{-1}$ instead of the maximum outflow velocity used by these authors (500 km s$^{-1}$), and scenario III$^d$ to the measurements from RA22, which correspond to outflowing gas along the kinematic minor axis. The outflow mass fractions were computed using the total masses of $M_{\rm H_2}$ listed in Table [\[tab:co\]](#tab:co), except for J1356, for which we used the mass of J1356N reported by RA22, of $M_{\rm H_2}$=6.39$\times$10$^9$  M$_{\rm \odot}$. For J1509, $M_{\rm H_2}$=17.6$\pm$7.4  M$_{\rm \odot}$ ( RA22).

II) In the second scenario, we consider that only the gas with the highest velocities is outflowing. The determination of the velocity cut comes from the comparison between the PVDs shown in Figures [4](#fig:pv1010)-[7](#fig:pv1356) and the ^3D^BAROLO rotation model, shown in red contours in the same figures.

The outflow velocity, $v_{\rm out}$, is defined as the velocity cut above the maximum rotation velocity that is modeled with ^3D^BAROLO. To calculate the flux of the high velocity gas, we then created moment 0 maps by selecting only channels above the rotation velocities modelled with ^3D^BAROLO, shown in Figure [8](#fig:highvel). In the case of J1010 we only see the blueshifted side of the outflow, reaching velocities up to 300  km s$^{-1}$ in the corresponding PVD (see Figure [4](#fig:pv1010)). The same happens in the case of J1347, based on the detection of high-velocity gas and excitation seen in the PVDs in Figure [6](#fig:pv1347). As for J1356, we only considered the more prominent redshifted velocities seen in the PVDs in Figure [7](#fig:pv1356) that also correspond to the region with high values of R$_{\rm 32}$.

III) The third scenario is a mix of the first two. We assume that all the high-velocity gas is outflowing, but the contribution from rotation is subtracted following a similar approach as in (cite: santi19). We first subtracted the contribution of circular motions by de-projecting the one dimensional rotation curve derived with ^3D^BAROLO  to the corresponding velocity field on a pixel by pixel basis. We re-shuffled the channels in order to remove the rotation component from the velocity axis of the CO(2-1) datacube. Then, we created the residual integrated spectrum, resulting in a narrower residual CO profile (i.e., without the rotation component), as the one we presented for the Teacup in Appendix C of AA23. Since this method is suited to optimize the signal-to-noise of the emission associated with non-circular motions, it can reveal high-velocity wings that otherwise are too faint and/or immersed in the total CO profiles to be detected. Using the residual CO profiles, we estimate the flux contribution of the outflowing gas by integrating the flux of the high-velocity gas in the blue and red wings, using the same velocity cut as in Scenario II.

In Table [\[tab:prop\]](#tab:prop) we list the derived outflow integrated intensities ($S_{\rm CO}$), velocities ($v_{\rm out}$), and radii ($r_{\rm out}$) of the QSO2s in each of the three scenarios considered. We note that for J1347 and J1356 we did not measure the outflow fluxes as described in scenarios I and III because they are ongoing mergers with very complex kinematics showing a small contribution from rotation (as discussed in Section [3.4](#sec:model) and Appendix [8](#sec:vsig)), and since scenarios I and III depend on the subtraction of the rotation model, respectively, they cannot be performed accurately. Instead, in the case of J1347 we used as the least conservative scenario (Scenario I in Table [\[tab:prop\]](#tab:prop)) the recent molecular outflow properties reported by (cite: luke24) based on CO(1-0) observations at 0.05$''$ resolution. The CO(1-0) outflow is compact (120 pc) and likely driven by the small scale radio jet detected with VLBI and shown in Figure [3](#fig:ratiosdisp) (cite: morganti13; luke24). As for the most conservative scenario (Scenario III in Table [\[tab:prop\]](#tab:prop)), we adopted the upper limit derived by (cite: lamperti22) from the CO(2-1) observations at 0.22$''$ resolution. We note that the CO(3-2) data, first presented in (cite: fotopoulou19), show blueshifted velocities of up to $\sim$400 km s$^{-1}$ that are not seen in CO(2-1). However, for this QSO2 the high angular resolution CO(1-0) data reported by (cite: luke24) were crucial to detect the nuclear outflow of r$_{\rm out}\sim$120 pc, which shows velocities of up to $\sim$600 km s$^{-1}$. In the case of J1356, we adopt as the least conservative scenario (Scenario I in Table [\[tab:prop\]](#tab:prop)) the outflow properties reported by (cite: sun14), based on the CO(3-2) observations, but using an average outflow velocity of 400 km s$^{-1}$ instead of the maximum outflow velocity adopted by these authors, of $v_{\rm out}$=500 km s$^{-1}$. The most conservative scenario (Scenario III in Table [\[tab:prop\]](#tab:prop)) in the case of J1356 corresponds to the outflow properties reported by RA22, which were calculated considering just outflowing gas along the kinematic minor axis of the galaxy.

We computed the outflow masses from the integrated flux measurements of the outflows. First, the integrated fluxes were converted to CO luminosities, L$_{\rm CO(2-1)}^\prime$, in units of ${\rm K\,km\,s^{-1}\,pc^2}$ using Equation 3 of (cite: solomon05) and then translated into masses using the CO-to-H$_2$ ($\alpha_{\rm CO}$) conversion factor M$_{\rm H_2}$=$\alpha_{\rm CO}$R$_{\rm 12}$L$^\prime_{\rm CO(2-1)}$. Under the assumption that the gas is thermalised and optically thick, the brightness temperature ratio $R_{\rm 12}={L_{\rm CO(1-0)}^\prime}/{L_{\rm CO(2-1)}^\prime}$=1. We adopted the conservative value of $\alpha_{\rm CO}$ = 0.8, commonly used to derive outflow masses (see RA22 and references therein). The values of the outflow masses derived from each scenario are listed in Table [\[tab:prop\]](#tab:prop).

To compute outflow mass rates, we use the values for the outflow radii, $r_{\rm out}$, listed in Table [\[tab:prop\]](#tab:prop). These radii correspond to the maximum distances from the nucleus measured for the high-velocity gas shown with contours in Figure [8](#fig:highvel). The cold molecular outflow radii range between 0.65$<r_{\rm out}<$2.4 kpc. For J1347 and J1356 we also include the outflow radii reported by the corresponding authors in the case of scenarios I and III. Considering them, the range of outflow radii includes smaller values, of 0.12 and 0.52 kpc in the case of J1347, and 0.3 and 0.4 kpc in J1356. The outflow velocities that we measure range from 50 to 100 km s$^{-1}$ in the case of scenario I, while in scenarios II and III the high velocity maps were created considering emission above/below $v_{\rm out}$=180-300 km s$^{-1}$ and integrating the flux in the high-velocity residual wings, respectively (see Table [\[tab:prop\]](#tab:prop)). In the case of J1347 and J1356, faster outflow velocities were reported in the corresponding works that we used here as more and less conservative scenarios (see Table [\[tab:prop\]](#tab:prop)).

For a time-averaged thin expelled shell geometry (cite: rupke05), $\dot{M}_{\rm out}$=$M_{\rm out} \left(v_{\rm out}/r_{\rm out}\right)$, which corresponds to the outflow mass averaged over the flow timescale, $t_{\rm out}={r_{\rm out}}/{v_{\rm out}}$. This geometry has been previously adopted in other studies of molecular outflows in the local Universe (cite: fluetsch19; lutz20; cra22). The outflow velocities and radii we reported for the three scenarios correspond to the projected values, since the determination of the outflow angle is uncertain. For a given outflow angle, the mass outflow rates will be then corrected to $\dot{M}_{\rm out}$= $M_{\rm out} \times \frac{v_{\rm out}}{r_{\rm out}} \times tan(\alpha)$. For the case of outflows co-planar to the CO disks, then $tan(\alpha) = tan(90-i)=1/tan(i)$, where $i$ is the inclination angle of the CO disk ( RA22).

Considering scenario I, we measure outflow masses that correspond to $\sim$0.6-8% of the total molecular gas mass of the QSO2s, and outflow rates in the range 8$<$$\dot{M}_{\rm out}$$<$148 M$\rm _{\odot}\, yr^{-1}$. From scenario II we derive outflow mass fractions of $M_{\rm out}/M_{\rm H_2}$=0.8-2.6%, and 5$<$$\dot{M}_{\rm out}$$<$63 M$\rm _{\odot}\, yr^{-1}$. Finally, in the case of the most conservative scenario III, the outflowing mass fractions are $\lesssim$1% of the total molecular gas and 5$<$$\dot{M}_{\rm out}$$<$32 M$\rm _{\odot}\, yr^{-1}$, similar to the measurements reported by RA22 for the same QSO2s. The largest values of the outflow mass rate in the three scenarios considered here correspond to those of J1347, the only radio-loud QSO2 in our sample. It is noteworthy that this is not the case for the outflow masses, for which we measure the highest values in J1100 and J1509. We note that the outflow mass fractions depend on the choice of the $\alpha_{\rm CO}$ conversion factors used to compute the total and outflow masses. We adopted the standard Galactic value ($\alpha_{\rm CO}=4.36M_\odot (K kms^{-1}pc^{2})^{-1}$) for the total molecular mass and $\alpha_{\rm CO}=0.8 M_\odot (K kms^{-1}pc^{2})^{-1}$ for the outflow masses, resulting in a factor of $\sim$5 larger fractions if same $\alpha_{\rm CO}$ was adopted.

The mass loading factors, defined as $\eta = \dot{M}_{\rm out}$/SFR, for scenario II are listed in Table [\[tab:prop\]](#tab:prop), with measured values ranging from $\eta \sim$ 0.2 to 3.4. We find $\eta > 1$, which is indicative of outflows efficiently removing molecular gas, for the Teacup and J1347. For the remaining QSO2s, the relatively low values of $\eta$ (0.2-0.6) might be indicating that star formation is the primary mechanism consuming molecular gas (see RA22 and (cite: speranza24) for further discussion).

In Section [4.1](#energetics) we discuss the energetics of these outflows in the context of radio and quasar mode AGN feedback.

# Discussion

## Energetics of the molecular outflows

Empirical scaling relations using molecular gas observations of AGN and ULIRGs of different luminosities showed that the mass outflow rate increases with AGN luminosity (cite: cicone14; fiore17; fluetsch19), supporting the scenario of accretion disc winds pushing away the surrounding gas and launching galaxy-scale outflows (i.e., quasar feedback). However, it is noteworthy that these scaling relations were inferred using galaxies that were known to host powerful molecular outflows detected using CO and/or OH observations. Indeed, more recent studies of less biased AGN and ULIRG samples have revealed important deviations from the classical scaling relations, and many luminous AGN including the QSO2s studied here lie well below them (cite: cra22; lamperti22; speranza24). This indicates that AGN luminosity itself is not a sufficient condition for driving powerful outflows, and other factors might be relevant for an AGN to drive more or less massive molecular outflows.

![](MoutLAGN_alljet.png)

In this work we used three scenarios to compute the mass outflow rates, as described in Section [3.5](#sec:outprop), and found values of $\dot{M}_{\rm out}$=5-150 M$\rm _{\odot}\, yr^{-1}$. The mass outflow rates that we derive from the most conservative scenario III if we exclude the radio-loud QSO2 J1347, are $\dot{M}_{\rm out}$=5-16 M$\rm _{\odot}\, yr^{-1}$. These values are similar to those reported by RA22 using a different method, consisting of considering as outflowing gas that along the kinematic minor axis of the galaxies, and assuming that the outflows are coplanar with the CO disc. In Figure [9](#fig:moutrates) we show the $\dot{M}_{\rm out}$ versus L$_{\rm bol}$ plot including our QSO2s, with the intermediate values (big purple circles) representing scenario II and the black dashed lines connecting the least and most conservative values derived from scenarios I and III (small purple circles). In agreement with the results presented in RA22, our $\dot{M}_{\rm out}$ values lie below the (cite: fiore17) empirical relation, even when we consider the least conservative scenario I. This is also the case for the AGN-dominated ULIRGs presented in (cite: lamperti22), also shown in Figure [9](#fig:moutrates), whose outflow mass rates range from 3 to 145 M$\rm _{\odot}\, yr^{-1}$. Based on their bolometric luminosities (L$_{\rm bol}\sim$10$^{45-46}$ erg s$^{-1}$), both our QSO2s and the AGN-dominated ULIRGs were expected to have molecular outflow rates of $\gtrsim$100 M$\rm _{\odot}\, yr^{-1}$ based on the (cite: fiore17) scaling relation. The four $z<$0.2 QSO2s with nuclear molecular outflows reported in (cite: girdhar24) also occupy the same region in the $\dot{M}_{\rm out}$- L$_{\rm bol}$ plane as the QSOFEED QSO2s.

This and other recent works are starting to reveal a population of AGN with less massive molecular outflows that those expected from empirical scaling relations. This is likely due to the advent of sub-mm facilities with high sensitivity such as ALMA and NOEMA, which enable the observation of more diverse, and hence less biased, AGN samples. Based on all the outflow measurements included in Figure [9](#fig:moutrates), from this and other works, we claim that the scaling relations found by e.g. (cite: cicone14), (cite: fiore17), and (cite: fluetsch19)

most likely represent the upper boundary of the $\dot{M}_{\rm out}$- L$_{\rm AGN}$ relation, as first suggested by RA22.

We note that part of the discrepancy between the empirical $\dot{M}_{\rm out}$- L$_{\rm AGN}$ relation and the observations lying below it in Figure [9](#fig:moutrates) could be associated with the different outflow velocity definitions (e.g., $v_{\rm max}$ versus $v_{\rm out}$). For example, (cite: venturi23) reported that the use of $v_{\rm max}$, defined as $v_{\rm out}$+FWHM/2, instead of $v_{\rm out}$ results in an increase of the ionized mass outflow rates by a factor of 3-20.

In the case of molecular outflows, which have lower velocities than the ionized ones, $v_{\rm out}$ cannot be measured from the line wings in most cases, but rather from the residuals obtained after kinematical modeling, such as the analysis performed here. This is also the case of some of the molecular outflows used by (cite: fiore17) to derive the empirical relation shown in Figure [9](#fig:moutrates), such as NGC 1068 (cite: santi14) and NGC 1433 (cite: combes13). We refer the reader to (cite: kiara23) and (cite: speranza24) for further details on how the use of different methodologies and outflow parameter definitions affect the derived outflow energetics.

To explain these “mild” molecular outflows detected in luminous AGN, RA22 suggested that other factors including jet power, coupling between winds, jets, and/or ionized outflows and the CO disks, and the ISM distribution might also be relevant (see also (cite: harrison24) for a recent review). To investigate the possible role of compact jets as drivers of the molecular outflows, we computed the kinetic power of the outflows ($\dot{E}_{\rm out}$=0.5$\dot{M}_{\rm out}$$v_{\rm out}^2$) and compared them with the values of $L_{\rm bol}$ and the jet-power ($P_{\rm jet}$) of the QSO2s and other AGN in Figure [10](#fig:ekin). The values of $P_{\rm jet}$ were computed using the 1.4 GHz VLA fluxes and spectral indices corresponding to the HR data from (cite: jarvis19) and applying the $L_{\rm 1.4GHz}\times P_{\rm jet}$ relation of (cite: birzan08), as in AA23. They are listed in Table [\[tab:prop\]](#tab:prop).

The observed kinetic powers of the QSO2 outflows are in the range of 6.4$\times 10^{39}<\dot{E}_{\rm out}<1.2 \times 10^{43}$ erg s$^{-1}$, and in the left panel of Figure [10](#fig:ekin) we can see that the radiative coupling efficiencies, defined as $\epsilon_{\rm AGN}\equiv \dot{E}_{\rm out}/L_{\rm bol}$, lie below the 1:1000 relation, except for the least conservative value measured for J1347. This is showing that the kinetic power of the outflows correspond to $\ll$0.1% of the AGN bolometric luminosities shown in Table [\[tab:main\]](#tab:main). There is a large scatter, of more than three orders of magnitude, in the $\epsilon_{\rm AGN}$ derived when we considered the measurements from the three different scenarios ($10^{-6}<\epsilon_{\rm AGN}<10^{-4}$ if we only consider scenario II; 0.0001-0.01%). This scatter is similar to the one found for observationally-derived outflow kinetic powers compiled by (cite: harrison18). Although the majority of the cosmological simulations require $\epsilon_{\rm AGN}\gtrsim$1% for AGN feedback to efficiently suppress star formation (cite: dubois14; schaye15; costa18), these fiducial efficiencies adopted in the simulations should not be directly compared to the observed coupling efficiencies (cite: costa18; harrison18; harrison24). This is because theoretical efficiencies are calibrated quantities, and not a prediction from the simulations, and also because only a fraction of the injected energy is converted into outflow kinetic energy, depending on the properties of ISM, the gravitational potential, and other factors, so the observed coupling efficiencies are often small (cite: harrison24).

Low radiative coupling efficiencies can also be due to the fact that radiation pressure–driven outflows depend strongly on the distribution and geometry of gas and dust around the AGN (cite: bieri17; costa18). Radiative coupling efficiency depends on the degree to which radiation is trapped and reprocessed within an optically thick, dusty medium. In clumpy or porous environments, radiation can escape through low-density channels, significantly reducing the momentum imparted to the gas (cite: ishibashi15; costa18). This strong dependence on the small-scale structure of the ISM can naturally explain the lower radiative coupling efficiencies observed in the quasars in this work. The purpose of showing Figure [10](#fig:ekin) including the 1:100 relation is to highlight that for the six QSO2s and for the majority of the observational data shown in that Figure, $\epsilon_{\rm AGN}\ll$1%.

![](Eout.png)

For comparison, in the right panel of Figure [10](#fig:ekin) we present $\dot{E}_{\rm out}$ versus $P_{\rm jet}$. The jet coupling efficiencies considering scenario II, defined as $\epsilon_{\rm jet}\equiv \dot{E}_{\rm out}/P_{\rm jet}$, are in the range 0.001$<\epsilon_{\rm jet}<$0.035 (0.1-3.5%). These are similar to the jet coupling efficiencies of the four QSO2s at $z<$0.2 reported by (cite: girdhar24), of 0.05-4% (one of them is Teacup, so in the following we will refer to the other three), and are significantly higher than the corresponding radiative coupling efficiencies.

We investigated possible correlations exiting between the outflow kinetic power, $\dot{E}_{\rm out}$, and $L_{\rm bol}$ and $P_{\rm jet}$. The first test was to apply a logarithmic linear regression to the six QSOFEED sources studied in this work. The second test was to group the six QSOFEED QSO2s and other nearby quasars with molecular outflows reported in the literature: three QSO2s at $z\lesssim$0.2 reported in (cite: girdhar24) and the two type-1 PG quasars at $z\sim$0.06 recently reported by (cite: fei24). Finally, the third test includes all the quasars included in the second test and the low-power jet-driven outflow in a low-luminosity AGN from (cite: murthy22) and the compilation of possibly jet-driven outflows in AGN of different bolometric luminosities presented in (cite: michalis23).

In Table [1](#tab:correlations) we list the derived parameters for the logarithmic linear regression in the format $\log(Y)= a*\log(X)+ b$, with the corresponding Pearson correlation coefficients, with possible values in the range of -1$<r_{\rm Pearson}<$1 and the $p$-values. $r_{\rm Pearson}$ values close to zero indicate no correlation, close to 1 a strong correlation and close to -1 an anti-correlation.

| Log correlation | $a$ | $b$ | $r_{\rm Pearson}$ | $p$-value |
|:---|:--:|:--:|:--:|:--:|
|  |  |  |  |  |
| $\dot{E}_{\rm out} \times L_{\rm bol}$ | -0.19 | 54.0 | -0.44 | 0.38 |
| $\dot{E}_{\rm out} \times P_{\rm jet}$ | 0.98 | -2.3 | 0.48 | 0.33 |
|  |  |  |  |  |
| $\dot{E}_{\rm out} \times L_{\rm bol}$ | 0.12 | 40.6 | 0.17 | 0.62 |
| $\dot{E}_{\rm out} \times P_{\rm jet}$ | 0.54 | 17.6 | 0.25 | 0.45 |
|  |  |  |  |  |
| $\dot{E}_{\rm out} \times L_{\rm bol}$ | 1.43 | -18.0 | 0.61 | 0.0003 |
| $\dot{E}_{\rm out} \times P_{\rm jet}$ | 1.15 | -8.6 | 0.55 | 0.0017 |
|  |  |  |  |  |

: Correlation parameters of the outflow energetics

The $p$-values shown in Table [1](#tab:correlations) show that the only statistically significant correlations are found when considering all the measurements in the literature, i.e., the “All molecular” case, with $p$-value$<$ 0.2% and $r_{\rm Pearson}\sim$0.6, indicating a positive correlation with both $L_{\rm bol}$ and $P_{\rm jet}$. On the other hand, when using the “QSOFEED molecular” (6 galaxies) and “Quasars molecular” (11 galaxies) samples, the $p$-values are high and indicate no correlations, possibly due to the small sample sizes. However, we note that the linear regression using only the values of $\dot{E}_{\rm out}$ and and $P_{\rm jet}$ derived for “QSOFEED molecular” (indicated with a purple dashed line in the right panel of Figure [10](#fig:ekin)) follows the 1:1000 relation, indicating jet coupling efficiencies of $\epsilon_{\rm jet}\sim$0.1%. This might indicate that the compact, low-power jets often detected in radio-quiet AGN, are potentially capable of launching the molecular outflows that we observe. To confirm or discard any of these trends, more observations covering larger parameter space in $P_{\rm jet}$ and $L_{\rm bol}$ are required.

Therefore, despite the fact that our QSO2s have high AGN luminosities, low-power jets might be driving some of the molecular outflows that we see, based on the higher jet coupling efficiencies reported here. This result is

predicted by simulations of jet-ISM interactions (cite: mukherjee18sim; meenakshi22) and in agreement with previous studies using similar samples of obscured quasars (cite: mullaney13; zakamska14; jarvis19; moly19; girdhar22; girdhar24). In fact, low-to-moderate power kiloparsec scale jets are starting to be recognized as potential drivers of multi-phase outflows and as relevant mechanisms for AGN feedback (cite: morganti15; venturi21). In “radio-quiet” quasars, spatially resolved radio structures are often associated with morphological and kinematic distinct features in the ionized and molecular gas, such as increased turbulence and outflowing bubbles (cite: vm17; jarvis19; jarvis21; girdhar22; cra22; ane23; ulivi24). This suggest that jets can be an important feedback mechanism in highly accreting radio-quiet quasars, where radiative feedback would be expected to prevail. Alternatively, it has been proposed that the radio structures detected in e.g. VLA data of radio-quiet AGN could be produced by shocks induced by the outflows themselves as they made progress through the ambient ISM (cite: fischer19; fischer23).

We note that even if a jet-like morphology is resolved only for J1430 (Teacup) in the HR VLA radio images of our QSO2s, the unresolved radio emission of the others might still be attributed to small scale radio jets. (cite: jarvis19) analysed the VLA data of J1010, J1100, J1356[^3], and J1430. They all show a radio excess and lie above the FIR–radio correlation of star-forming galaxies (cite: bell03), indicating that only star formation processes are not enough to produce their radio emission. In addition, (cite: jarvis19) classified the unresolved nuclear radio emission of these QSO2s as “jet/lobe/wind”, based on their steep spectral indices (cite: jarvis19). This hypothesis is confirmed for the case of J1347, which shows diffuse emission on large scales (cite: stanghe05) and an unresolved core using low angular resolution radio observations, but high angular resolution VLBI data revealed a 100 pc scale jet (cite: kellermann04; morganti13), shown as black contours in the inset panel of J1347 in Figure [3](#fig:ratiosdisp).

The sensitivity and resolution of next generation radio facilities such as the LOw Frequency ARray (LOFAR), the Square Kilometre Array (SKA), and the new-generation Very Large Array (ngVLA) will help us to understand the origin of the radio emission in “radio-quiet” AGN (cite: panessa19) and they likely will reveal a wealth of galactic scale jets (cite: nyland18; morabito22; ye23). This will be particularly important to advance our understanding of the role of galactic scale low-power jets for AGN feedback, since “radio-quiet” sources dominate the AGN population (cite: padovani16).

## Relative orientation of the multi-phase outflows

In order to provide a more comprehensive view of the multi-phase outflows detected in the quasars studied here, we compare our findings for the cold molecular gas (T$\sim$10–100 K) with observations in the optical and NIR, allowing us to probe a broad range of gas temperatures and densities (cite: cicone18; harrison24). In the optical, the QSOFEED outflows have been studied in the warm ionized phase using the \[O III\]$\lambda$5007 $\AA$ emission line (T$\sim$10$^4$ K), and in the NIR using the ro-vibrational H$_2$ lines to trace the warm molecular gas (T$\gtrsim$10$^3$ K).

Using GTC/MEGARA

integral field spectroscopic observations of five QSO2s (same as RA22 and this work, except for J1347), (cite: speranza24) characterized the morphology and kinematics of the \[O III\] emitting gas. According to the outflow properties there reported, the ionized outflows in these five QSO2s carry less mass than their molecular counterparts and are more extended (3.2$<r_{\rm out}<$12.6 kpc) and faster (500$<|v_{\rm out}|<$1300 km s$^{-1}$) than the molecular outflows reported here (0.65$<r_{\rm out}<$2.4 kpc and 180$<|v_{\rm out}|<$300 km s$^{-1}$ from scenario II). The orientations (PAs) of the ionized outflows are indicated in Figure [8](#fig:highvel) and Table [2](#tab:pa) for comparison with the PAs measured here for the cold molecular outflows. The PA of J1010 could not be accurately measured from the GTC/MEGARA data, since this was the only QSO2 analyzed in (cite: speranza24) in which the \[O III\] outflow is not spatially resolved. However, from inspection of the kinematic maps shown in (cite: speranza24), the blueshifted side of the ionized outflow would have a PA of $\sim$-45$^\circ$, i.e. towards the north-west. (cite: ulivi24) analyzed a VLT/MUSE cube of this QSO2 and also detected broad, blueshifted \[OIII\] emission, but without a clear outflow PA.

We followed a similar procedure to that adopted in (cite: speranza24) to determine the PA of the blueshifted and/or redshifted sides of the molecular outflows. (cite: speranza24) fitted an ellipse to the 3$\sigma$ contour of the O\[III\] outflow flux maps using a Python script (cite: hill16). Here we used the same script to fit ellipses to the global shape of the high-velocity contours in Figure [8](#fig:highvel). We then determined the outflow PA using the line connecting the QSO2 nucleus, defined by the 200 GHz continuum peak, and the most distant point within the ellipse. The cold molecular outflow PAs are listed in Table [2](#tab:pa) and shown as dashed blue and red lines in Figure [8](#fig:highvel) for the blueshifted and redshifted sides of the outflows, respectively.

+:------+:------:+:------:+:-------:+:-------:+:--------:+:--------:+:-------------:+
| Name  | PA$\rm_{CO}$    | PA$\rm_{H_2}$     | PA$\rm_{[OIII]}$    | PA$\rm_{jet}$ |
+-------+--------+--------+---------+---------+----------+----------+---------------+
|       | blue   | red    | blue    | red     | blue     | red      |               |
+-------+--------+--------+---------+---------+----------+----------+---------------+
| J1010 | 116    | …      | …       | …       | …        | …        | 182           |
+-------+--------+--------+---------+---------+----------+----------+---------------+
| J1100 | 200    | 55     | …       | …       | 63       | …        | 175           |
+-------+--------+--------+---------+---------+----------+----------+---------------+
| J1347 | 56     | …      |         | …       | ……       | …        | 160           |
+-------+--------+--------+---------+---------+----------+----------+---------------+
| J1356 | …      | 129    | …       | 135     | 197      | 200      | 18            |
+-------+--------+--------+---------+---------+----------+----------+---------------+
| J1430 | 188    | -18    | 175     | -5      | 65       | 198      | 60            |
+-------+--------+--------+---------+---------+----------+----------+---------------+
| J1509 | 174    | -51    | …       | …       | -40      | …        | …             |
+-------+--------+--------+---------+---------+----------+----------+---------------+
|       |        |        |         |         |          |          |               |
+-------+--------+--------+---------+---------+----------+----------+---------------+

: PAs of the cold, warm molecular and ionized outflows and radio jets.

Table notes: The values of PA$\rm_{H_2}$ are from (cite: mavi25), PA$\rm_{[OIII]}$ from (cite: speranza24), shown in Figure [8](#fig:highvel) together with the the values of PA$_{\rm CO}$, and PA$\rm_{jet}$ from (cite: jarvis19), shown in Figure [3](#fig:ratiosdisp).

The projected PAs of the ionized and molecular outflows do not have similar orientations. In fact, in the cases of J1100, J1430, and J1509, their orientation appears to be inverted (see Figure [8](#fig:highvel)). For instance, in J1430, the redshifted \[O III\] outflow (PA$\rm_{[OIII],red}$=198$^\circ$) is almost aligned with the blueshifted CO outflow (PA$\rm_{CO,blue}$=188$^\circ$). The same is found for J1100 and J1509, where the redshifted sides of the CO outflows (PA$\rm_{CO,red}$ of 55$^\circ$and -51$^\circ$, respectively) are closely aligned with the blueshifted ionized outflow sides (PA$\rm_{[OIII],blue}$ of 63$^\circ$and -40$^\circ$). A caveat to consider is that the MEGARA observations are seeing-limited, with a resolution of approximately 1.1$''$, which is significantly coarser than the resolution of the ALMA data ($\sim$0.2$''$), although in the case of well-resolved ionized outflows as it is the case of J1100, J1356, J1430, and J1509 should not be an issue when it comes to determining the outflow orientation.

On the other hand, the warm molecular gas kinematics in J1356 and J1430, traced by the H$_2$1-0 S(1) and S(2) emission lines observed with VLT/SINFONI (seeing of $\sim$0.8$''$), are consistent with that of the cold molecular gas observed by ALMA (cite: mavi25). Both the blue- and redshifted sides of the warm molecular outflow are detected in J1430, while in J1356 only the redshifted outflow side is detected, having the same orientation observed for CO in this work (see Table [2](#tab:pa)), and similar radii and velocities (1.8$<r_{\rm out}<$1.9 kpc and 370\<\|v$_{\rm out}|<$470 km s$^{-1}$). The main difference is that the warm molecular outflows represent just a small fraction of the total molecular gas mass: (cite: mavi25) measured warm-to-cold gas ratios of $\sim$1$\times$10$^{-5}$ in the two QSO2s (cite: mavi25).

In general, the warm and cold molecular phases seem to be tracing the same outflow, with the main distinction being the mass fraction carried by them. On the contrary, the warm ionized outflows do not seem to be a different face of the same outflow, showing different orientation, velocity, and radius. This is likely related to the different temperatures and densities of the molecular and ionized gas, which respond differently to the action of AGN-driven winds and jets. This should be considered when comparing with simulations, which often consider “cold” gas that at temperatures of $\sim$10$^3$-10$^4$ K (e.g. (cite: mukherjee16; Ward24)).

## Global versus localised physical conditions of the molecular gas

In Sections [3.2](#sec:integrated) and [3.3](#sec:spaline) we presented the R$_{\rm 32}$ line ratios measured from the galaxy-integrated CO fluxes and the spatially resolved R$_{\rm 32}$ maps of the QSO2s. The global values derived from the integrated CO(3-2) and CO(2-1) intensities listed in Table [\[tab:co\]](#tab:co) are shown in the histogram of Figure [11](#fig:r32hist). We compare our global R$_{\rm 32}$ measurements with those derived for other samples of galaxies: a similar sample of 17 QSO2s at $z<$0.2 from (cite: moly24) using either ACA or APEX CO integrated fluxes from J $\rightarrow$ 1 up to 7 transitions; 36 hard X-ray-selected AGN host galaxies from the BAT AGN Spectroscopic Survey (BASS) analyzed in (cite: lamperti20), observed with the 15 m single-dish James Clerk Maxwell Telescope; a sample of 36 local ULIRGs observed with APEX by (cite: montoya23); and the low-J transitions study of a large sample of nearby star-forming disk galaxies using single-dish CO mapping surveys and PHANGS-ALMA by (cite: leroy22).

We derived integrated values of 0.22$<$R$_{\rm 32}$$<$0.75 and an average value of $<$R$_{\rm 32}$$>$0.5$\pm$0.2 for the QSO2s, which is similar to the average values derived for normal disk galaxies in (cite: leroy22), of 0.23$<$R$_{\rm 32}$$<$0.59.

(cite: moly24) reported a median value of \<R$_{\rm 32}$\>=0.6 for their sample of QSO2s, similar to ours, but their values range from 0.37-1.46, a broader range than the one we found for our smaller sample. A slightly higher average value of $<$R$_{\rm 32}$$>$0.74$\pm$0.3 was measured for the AGN BASS sample by (cite: lamperti20), with ratios ranging from 0.3-1.7. A similarly broad interval of R$_{\rm 32}$ was found by (cite: montoya23) for a sample of ULIRGs including active and non-active galaxies, with a median value of \<R$_{\rm 32}$\>=0.76 and a range of 0.4$<$R$_{\rm 32}$$<$1.7.

![](R32hist.png)

The CO SLEDs derived for QSO2s at $z<$0.2 in (cite: moly24) do not show evidence for high gas excitation for high J$\rightarrow$6,7 transitions, as it is observed for more luminous high-redshift quasars (cite: carilli13). We note however that only one of the four QSO2s observed in CO(6-5) by (cite: moly24) was detected and none of the three QSO2s observed in CO(7-6) were detected. These authors concluded that AGN feedback is not exerting any influence in the overall gas excitation on global scales, and instead, they proposed that feedback from winds/jets might by occurring on localized regions that they cannot resolve with the ACA/APEX observations. For lower J transitions, the CO SLEDs of a sample of 35 local AGN ($z\leq$0.15) reported by (cite: esposito22) indicate no evidence for AGN influence on the cold and low-density gas on more localised kiloparsec-scales.

The high angular resolution ALMA observations employed here allow us to probe physical scales of a few hundreds of parsecs of the QSO2s. The spatially resolved R$_{\rm 32}$ maps shown in Figure [3](#fig:ratiosdisp) reveal a gradient of excitation, with higher values of R$_{\rm 32}$$\sim$0.7-0.9 within the central kiloparsec of the galaxies and of $\sim$0.2-0.5 across the galaxy disks. Spatially resolved CO line ratio emission analyses have been reported for a few nearby Seyferts and radio galaxies (cite: viti14; morganti15; dasyra16; oosterloo17; oosterloo19; ruffa22), but not for quasars, with the exception of the Teacup ( AA23).

Using a plethora of molecular lines (i.e., CO, HCN, HCO$^+$, and CS lines) and the RADEX (cite: radex) radiative transfer code, (cite: viti14) modelled the excitation conditions of the molecular gas in the circumnuclear disc of NGC 1068. The authors claimed that elevated values of $R_{\rm 31} \equiv L^\prime_{\rm CO(3-2)}/L^\prime_{\rm CO(1-0)}\sim$5 and $R_{\rm 21} \equiv L^\prime_{\rm CO(2-1)}/L^\prime_{\rm CO(1-0)}\gtrsim$4 correspond to hot dense gas (kinetic temperatures $T>$150 K and gas density $n_{\rm H}>10^5$ cm$^{-3}$) excited by the AGN.

Higher values of different emission line ratios have been reported for the molecular gas interacting with jets in the radio galaxy PKS 1549-79 (cite: oosterloo19), and also in the Seyfert galaxy IC 5063 (cite: dasyra16; oosterloo17). IC 5063 is a clear-cut example of jet coplanar with the galaxy disc, which is driving a multi-phase outflow (cite: tadhunter14; morganti15). The jet power estimated for IC 5063 is $P_{\rm jet}\sim$10$^{\rm 44}$ erg s$^{-1}$ and the PVD along the jet axis revealed R$_{\rm 32}$ values ranging from 1.0$-$1.5 in the outflowing regions, clearly different from the gas following regular rotation ($R_{\rm 32}<0.7$). Under local thermodynamic equilibrium (LTE) conditions, $R_{\rm 32}>$1 corresponds to excitation temperatures ($T_{\rm ex}$) of $\sim$50 K (cite: oosterloo17). A similar temperature was found for the fast outflow gas component of IC 5063 using $R_{\rm 42}\equiv L^\prime_{\rm CO(4-3)}/L^\prime_{\rm CO(2-1)}>>$1, suggesting that the gas in the outflow is optically thin (cite: dasyra16).

![](pv-R32hist.png)

Another example of jet-induced molecular gas excitation is the radio galaxy NGC 3100. The cold molecular gas is distributed in a ring-like morphology, with the central region ($\sim$500 pc) depleted of CO. Most of the CO emission presents $R_{\rm 21}$ and $R_{\rm 31}$ ratios of $<$1, implying sub-thermal excitation conditions (cite: ruffa22), but ratios of $R_{\rm 21}\sim$4 and $R_{\rm 31}\sim$3 are observed at the inner part of the disc, where there is spatial correlation with the radio lobes. All these cases indicate that jet-impacted regions have different gas excitation conditions due to shocks and/or reduced optical thickness (cite: morganti21).

In an attempt to quantify the differences in R$_{\rm 32}$ found between the disk and outflow regions, Figure [12](#fig:pv-r32hist) shows the histograms of R$_{\rm 32}$ values included in the PVDs along the minor axis (see Figures [4](#fig:pv1010)-[7](#fig:pv1356)). The green histograms correspond to molecular gas with velocities v$<v_{\rm out}$ from scenario II, which we attributed to the disk, and the red histograms to gas with v$>v_{\rm out}$, which we associate with the outflow regions. We note that this method only includes gas along the minor axis, within a simulated slit of a given size, and therefore does not include all the gas in the disk or outflow. The outflow histograms show higher values of R$_{\rm 32}$ than the disk ones in J1100, J1347, and J1356. In the case of J1010, as we described in Section [3.4](#sec:model), the regions with R$_{\rm 32}$$>$1 are distributed all over the minor and major axis PVDs, for both low and high velocity gas. This is likely related to coarser resolution of the CO(2-1) data in the case of J1010, of $\sim$0.8$''$, which prevents us from accurately constraining the R$_{\rm 32}$ distribution in this QSO2. For J1430, studied in detail in AA23, the jet is almost coplanar with the CO disk, producing elevated R$_{\rm 32}$ values across the whole disk, and particularly along the direction perpendicular to the jet.

Therefore, based on the analysis presented in this work, for our QSO2s we find that the regions with high-velocity gas that cannot be attributed to rotation, as modelled with ^3D^BAROLO, have values of R$_{\rm 32}$ of up to $\approx$1-2, with J1347 showing the highest values.

These values are significantly higher than those measured in areas of the PVDs dominated by rotation (R$_{\rm 32}$$\approx$0.3-0.7) and than the values reported by (cite: leroy22) for normal disk galaxies (mean R$_{\rm 32}$ of 0.5),

indicating that the molecular gas participating in the outflows exhibits enhanced temperature and is optically thin. Shocks could potentially induce a different temperature profile and thus affect the observed line ratios in these outflows (cite: meijerink13). This could also be due to higher X-ray emission in the vicinity of the AGN, since R$_{\rm 32}$  tends to increase with the X-ray luminosity in high density gas ($n_{\rm H}>10^4$ cm$^{-3}$), as shown in (cite: lamperti20). However, we are unable to infer the physical conditions ($T_{\rm ex}$ and density) of the gas using only one molecular line ratio, since more transitions, specially from higher J, would be necessary for that.

# Conclusions

We presented the analysis of ALMA CO(2-1) and CO(3-2) observations at 0.2$''$-0.6$''$ resolution (370-960 pc) of a sample of six obscured quasars at $z\sim$0.1, which belong to the QSOFEED sample. Our goal was to investigate the relevance of quasar-driven winds and/or jets on their cold molecular ISM and kinematics. To do so, we performed kinematic modelling together with spatially resolved line ratios, R$_{\rm 32}$, that indicate changes in the gas excitation conditions. Our main findings can be summarized as follows.

-The CO(3-2) emission of the QSO2s, even if measured from slightly lower angular resolution data (0.6$''$), shows similar morphology and kinematics than those of the CO(2-1) emission first presented in RA22. The peak intensity maps better reveal clumpy structures and double-peaked morphologies than the corresponding moment 0 maps.

-The line ratios using the integrated CO(2-1) and CO(3-2) fluxes measured for our sample range from 0.22$<$R$_{\rm 32}$$<$0.75, with an average value of \<R$_{\rm 32}$\>=0.5$\pm$0.2, similar to the line ratios typically found in the galaxy disks of nearby star-forming galaxies. In principle, this implies no impact of the AGN on the global molecular gas excitation. However, our spatially resolved R$_{\rm 32}$ maps reveal a gradient of excitation, with higher values of R$_{\rm 32}$$\sim$0.7-0.9 within the central kiloparsec of the galaxies that decrease to values of $\sim$0.2-0.5 across the galaxy disks. The regions of higher excitation coincide with areas of high velocity dispersion, but we do not find a clear trend between the orientation of this enhancement of gas excitation and dispersion either along or perpendicular to the radio emission, with the exception of the Teacup (J1430), previously reported by AA23.

-The combination of kinematic modelling with ^3D^BAROLO and the R$_{\rm 32}$ PVDs reveals that the high velocity regions associated with outflows have the highest line ratios seen in the PVD, exceeding R$_{\rm 32}$$>$1. This indicates that either the high velocity gas presents higher gas excitation (higher temperatures) or it is optically thin.

-Using three scenarios to compute the mass outflow rates, we found values ranging from $\dot{M}_{\rm out}$=5-150 M$\rm _{\odot}\, yr^{-1}$. These values lie below the $\dot{M}_{\rm out}$-L$_{\rm bol}$ empirical relations reported in literature (e.g. (cite: fiore17)), even when we consider the least conservative scenario I.

-We measured outflow kinetic powers in the range of 6.4$\times 10^{39}<\dot{E}_{\rm out}<1.2 \times 10^{43}$ erg s$^{-1}$ for our QSO2s. The radiative coupling efficiencies ($\epsilon_{\rm AGN}\equiv \dot{E}_{\rm out}/L_{\rm bol}$) range from $10^{-6}<\epsilon_{\rm AGN}<10^{-4}$ when we use the kinetic powers derived from scenario II, corresponding to coupling efficiencies of $\ll$0.1%. On the other hand, the jet coupling efficiencies ($\epsilon_{\rm jet}\equiv \dot{E}_{\rm out}/P_{\rm jet}$) range from 0.001 \< $\epsilon_{\rm jet}$ \< 0.035 ($\epsilon_{\rm jet}\sim$0.1%).

These findings might indicate that, despite the high AGN luminosities of the QSO2s (L$_{\rm bol}\sim$10$^{45.5-46}$ erg s$^{-1}$), compact low-power jets might be playing a key role in driving the molecular outflows.

-By comparing the cold molecular outflow properties with those derived for some of the QSO2s in the ionized (cite: speranza24) and warm molecular gas phases (cite: mavi25), we find that the warm and cold molecular phases appear to be tracing the same outflow, while the warm ionized one does not, as it exhibits distinct orientation and kinematics.

To better understand the role of jets and winds on the distribution, kinematics, and gas excitation of molecular gas in “radio quiet” quasars, high-angular resolution CO and radio observations of larger samples are required. In particular, high angular resolution data of multiple CO transitions will be crucial to disentangle the outflow from regular kinematics, characterize the impact of winds and jets on gas with different molecular gas densities, and constrain the excitation mechanisms.

# Acknowledgements

The authors acknowledge the anonymous referee for their constructive report. AA and CRA acknowledge support from the Agencia Estatal de Investigación of the Ministerio de Ciencia, Innovación y Universidades (MCIU/AEI) under the grant “Tracking active galactic nuclei feedback from parsec to kiloparsec scales”, with reference PID2022$-$141105NB$-$I00 and the European Regional Development Fund (ERDF). They also acknowledge the projects “Quantifying the impact of quasar feedback on galaxy evolution”, with reference EUR2020-112266, funded by MICINN-AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR, and the Consejería de Economía, Conocimiento y Empleo del Gobierno de Canarias and the European Regional Development Fund (ERDF) under grant “Quasar feedback and molecular gas reservoirs”, with reference ProID2020010105, ACCISI/FEDER, UE. AA acknowledges funding from the MICINN (Spain) through the Juan de la Cierva-Formación program under contract FJC2020-046224-I and from the European Union grant WIDERA ExGal-Twin, GA 101158446. SGB acknowledges support from the Spanish grant PID2022-138560NB-I00, funded by MCIN/AEI/10.13039/501100011033/FEDER, EU. MPS acknowledges support under grants RYC2021-033094-I, CNS2023-145506, and PID2023-146667NB-I00 funded by MCIN/AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR. IL acknowledges support from PRIN-MUR project "PROMETEUS" (202223XPZM). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00870.S, and ADS/JAO.ALMA#2016.1.01535.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC(Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

125 natexlab

(ref: ane19) Audibert, A., Combes, F., Garcı́a-Burillo, S., et al. 2019, A&A, 632, A33

(ref: ane21) Audibert, A., Combes, F., Garcı́a-Burillo, S., et al. 2021, A&A, 656, A60

(ref: ane23) Audibert, A., Ramos Almeida, C., Garcı́a-Burillo, S., et al. 2023, A&A, 671, L12

(ref: becker95) Becker, R. H., White, R. L., & Helfand, D. J. 1995, ApJ, 450, 559

(ref: bell03) Bell, E. F. 2003, ApJ, 586, 794

(ref: bessiere24) Bessiere, P. S., Ramos Almeida, C., Holden, L. R., Tadhunter, C. N., & Canalizo, G. 2024, arXiv e-prints, arXiv:2405.06421

(ref: bieri17) Bieri, R., Dubois, Y., Rosdahl, J., et al. 2017, MNRAS, 464, 1854

(ref: birzan08) Bîrzan, L., McNamara, B. R., Nulsen, P. E. J., Carilli, C. L., & Wise, M. W. 2008, ApJ, 686, 859

(ref: bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: bournaud08) Bournaud, F., Duc, P. A., & Emsellem, E. 2008, MNRAS, 389, L8

(ref: bournaud11) Bournaud, F., Powell, L. C., Chapon, D., & Teyssier, R. 2011, in Astrophysical Dynamics: From Stars to Galaxies, ed. N. H. Brummell, A. S. Brun, M. S. Miesch, & Y. Ponty, Vol. 271, 160–169

(ref: bourne17) Bourne, M. A. & Sijacki, D. 2017, MNRAS, 472, 4707

(ref: bourne23) Bourne, M. A. & Yang, H.-Y. K. 2023, Galaxies, 11, 73

(ref: carilli13) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: cicone18) Cicone, C., Brusa, M., Ramos Almeida, C., et al. 2018, Nature Astronomy, 2, 176

(ref: cicone14) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: combes13) Combes, F., Garcı́a-Burillo, S., Casasola, V., et al. 2013, A&A, 558, A124

(ref: costa18) Costa, T., Rosdahl, J., Sijacki, D., & Haehnelt, M. G. 2018, MNRAS, 473, 4197

(ref: croton06) Croton, D. J., Springel, V., White, S. D. M., et al. 2006, MNRAS, 365, 11

(ref: dasyra16) Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016, A&A, 595, L7

(ref: dimatteo08) Di Matteo, T., Colberg, J., Springel, V., Hernquist, L., & Sijacki, D. 2008, ApJ, 676, 33

(ref: barolo15) Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021

(ref: downes98) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615

(ref: dubois16) Dubois, Y., Peirani, S., Pichon, C., et al. 2016, MNRAS, 463, 3948

(ref: dubois14) Dubois, Y., Pichon, C., Welker, C., et al. 2014, MNRAS, 444, 1453

(ref: esposito24) Esposito, F., Vallini, L., Pozzi, F., et al. 2024, MNRAS, 527, 8727

(ref: esposito22) Esposito, F., Vallini, L., Pozzi, F., et al. 2022, MNRAS, 512, 686

(ref: fabian12) Fabian, A. C. 2012, ARA&A, 50, 455

(ref: fei24) Fei, Q., Wang, R., Molina, J., et al. 2024, arXiv e-prints, arXiv:2409.15611

(ref: feruglio20) Feruglio, C., Fabbiano, G., Bischetti, M., et al. 2020, ApJ, 890, 29

(ref: feruglio10) Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155

(ref: fiore17) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: fischer19) Fischer, T., Smith, K. L., Kraemer, S., et al. 2019, ApJ, 887, 200

(ref: fischer23) Fischer, T. C., Johnson, M. C., Secrest, N. J., Crenshaw, D. M., & Kraemer, S. B. 2023, ApJ, 953, 87

(ref: fluetsch19) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: fotopoulou19) Fotopoulou, C. M., Dasyra, K. M., Combes, F., Salomé, P., & Papachristou, M. 2019, A&A, 629, A30

(ref: santi21) Garcı́a-Burillo, S., Alonso-Herrero, A., Ramos Almeida, C., et al. 2021, A&A, 652, A98

(ref: santi19) Garcı́a-Burillo, S., Combes, F., Ramos Almeida, C., et al. 2019, A&A, 632, A61

(ref: santi15) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2015, A&A, 580, A35

(ref: santi14) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: santi24) Garcı́a-Burillo, S., Hicks, E. K. S., Alonso-Herrero, A., et al. 2024, A&A, 689, A347

(ref: girdhar22) Girdhar, A., Harrison, C. M., Mainieri, V., et al. 2022, MNRAS, 512, 1608

(ref: girdhar24) Girdhar, A., Harrison, C. M., Mainieri, V., et al. 2024, MNRAS, 527, 9322

(ref: harrison17) Harrison, C. M. 2017, Nature Astronomy, 1, 0165

(ref: harrison18) Harrison, C. M., Costa, T., Tadhunter, C. N., et al. 2018, Nature Astronomy, 2, 198

(ref: harrison24) Harrison, C. M. & Ramos Almeida, C. 2024, Galaxies, 12, 17

(ref: kiara23) Hervella Seoane, K., Ramos Almeida, C., Acosta-Pulido, J. A., et al. 2023, A&A, 680, A71

(ref: hickox14) Hickox, R. C., Mullaney, J. R., Alexander, D. M., et al. 2014, ApJ, 782, 9

(ref: hill16) Hill, C. 2016, Learning Scientific Programming with Python (Cambridge University Press)

(ref: luke24) Holden, L. R., Tadhunter, C., Audibert, A., et al. 2024, MNRAS, 530, 446

(ref: hollenbach99) Hollenbach, D. J. & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71, 173

(ref: ishibashi15) Ishibashi, W. & Fabian, A. C. 2015, MNRAS, 451, 93

(ref: jarvis21) Jarvis, M. E., Harrison, C. M., Mainieri, V., et al. 2021, MNRAS, 503, 1780

(ref: jarvis19) Jarvis, M. E., Harrison, C. M., Thomson, A. P., et al. 2019, MNRAS, 485, 2710

(ref: kellermann04) Kellermann, K. I., Lister, M. L., Homan, D. C., et al. 2004, ApJ, 609, 539

(ref: king03) King, A. 2003, ApJL, 596, L27

(ref: king15) King, A. & Nixon, C. 2015, MNRAS, 453, L46

(ref: kong18) Kong, M. & Ho, L. C. 2018, ApJ, 859, 116

(ref: lamastra09) Lamastra, A., Bianchi, S., Matt, G., et al. 2009, A&A, 504, 73

(ref: lamperti22) Lamperti, I., Pereira-Santaella, M., Perna, M., et al. 2022, A&A, 668, A45

(ref: lamperti20) Lamperti, I., Saintonge, A., Koss, M., et al. 2020, ApJ, 889, 103

(ref: leroy22) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149

(ref: lutz20) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134

(ref: mandal21) Mandal, A., Mukherjee, D., Federrath, C., et al. 2021, MNRAS, 508, 4738

(ref: martini04) Martini, P. 2004, in Coevolution of Black Holes and Galaxies, ed. L. C. Ho, 169

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mcnamara12) McNamara, B. R. & Nulsen, P. E. J. 2012, New Journal of Physics, 14, 055023

(ref: meenakshi22) Meenakshi, M., Mukherjee, D., Wagner, A. Y., et al. 2022, MNRAS \[\]

(ref: meijerink13) Meijerink, R., Kristensen, L. E., Weiß, A., et al. 2013, ApJL, 762, L16

(ref: meijerink07) Meijerink, R., Spaans, M., & Israel, F. P. 2007, A&A, 461, 793

(ref: mingozi18) Mingozzi, M., Vallini, L., Pozzi, F., et al. 2018, MNRAS, 474, 3640

(ref: moly24) Molyneux, S. J., Calistro Rivera, G., De Breuck, C., et al. 2024, MNRAS, 527, 4420

(ref: moly19) Molyneux, S. J., Harrison, C. M., & Jarvis, M. E. 2019, A&A, 631, A132

(ref: montoya23) Montoya Arroyave, I., Cicone, C., Makroleivaditi, E., et al. 2023, A&A, 673, A13

(ref: morabito22) Morabito, L. K., Jackson, N. J., Mooney, S., et al. 2022, A&A, 658, A1

(ref: morganti13) Morganti, R., Fogasy, J., Paragi, Z., Oosterloo, T., & Orienti, M. 2013, Science, 341, 1082

(ref: morganti21) Morganti, R., Oosterloo, T., Murthy, S., & Tadhunter, C. 2021, Astronomische Nachrichten, 342, 1135

(ref: morganti15) Morganti, R., Oosterloo, T., Oonk, J. B. R., Frieswijk, W., & Tadhunter, C. 2015, A&A, 580, A1

(ref: mukherjee16) Mukherjee, D., Bicknell, G. V., Sutherland, R., & Wagner, A. 2016, MNRAS, 461, 967

(ref: mukherjee18sim) Mukherjee, D., Bicknell, G. V., Wagner, A. Y., Sutherland, R. S., & Silk, J. 2018, MNRAS, 479, 5544

(ref: mullaney13) Mullaney, J. R., Alexander, D. M., Fine, S., et al. 2013, MNRAS, 433, 622

(ref: murthy22) Murthy, S., Morganti, R., Wagner, A. Y., et al. 2022, Nature Astronomy, 6, 488

(ref: nelson19) Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS, 490, 3234

(ref: nyland18) Nyland, K., Harwood, J. J., Mukherjee, D., et al. 2018, ApJ, 859, 23

(ref: oosterloo19) Oosterloo, T., Morganti, R., Tadhunter, C., et al. 2019, A&A, 632, A66

(ref: oosterloo17) Oosterloo, T., Raymond Oonk, J. B., Morganti, R., et al. 2017, A&A, 608, A38

(ref: padovani16) Padovani, P. 2016, A&ARv, 24, 13

(ref: panessa19) Panessa, F., Baldi, R. D., Laor, A., et al. 2019, Nature Astronomy, 3, 387

(ref: michalis23) Papachristou, M., Dasyra, K. M., Fernández-Ontiveros, J. A., et al. 2023, A&A, 679, A115

(ref: pereira18) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2018, A&A, 616, A171

(ref: pierce23) Pierce, J. C. S., Tadhunter, C., Ramos Almeida, C., et al. 2023, MNRAS, 522, 1736

(ref: cra19) Ramos Almeida, C., Acosta-Pulido, J. A., Tadhunter, C. N., et al. 2019, MNRAS, 487, L18

(ref: cra22) Ramos Almeida, C., Bischetti, M., Garcı́a-Burillo, S., et al. 2022, A&A, 658, A155

(ref: cra25) Ramos Almeida, C., Garcia-Bernete, I., Pereira-Santaella, M., et al. 2025, arXiv e-prints, arXiv:2504.01595

(ref: cra17) Ramos Almeida, C., Piqueras López, J., Villar-Martı́n, M., & Bessiere, P. S. 2017, MNRAS, 470, 964

(ref: reyes08) Reyes, R., Zakamska, N. L., Strauss, M. A., et al. 2008, AJ, 136, 2373

(ref: ruffa22) Ruffa, I., Prandoni, I., Davis, T. A., et al. 2022, MNRAS, 510, 4485

(ref: rupke05) Rupke, D. S., Veilleux, S., & Sanders, D. B. 2005, ApJS, 160, 115

(ref: schawinski15) Schawinski, K., Koss, M., Berney, S., & Sartori, L. F. 2015, MNRAS, 451, 2517

(ref: schaye15) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521

(ref: solomon05) Solomon, P. M. & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: speranza24) Speranza, G., Ramos Almeida, C., Acosta-Pulido, J. A., et al. 2024, A&A, 681, A63

(ref: speranza22) Speranza, G., Ramos Almeida, C., Acosta-Pulido, J. A., et al. 2022, A&A, 665, A55

(ref: stanghe05) Stanghellini, C., O’Dea, C. P., Dallacasa, D., et al. 2005, A&A, 443, 891

(ref: sun14) Sun, A.-L., Greene, J. E., Zakamska, N. L., & Nesvadba, N. P. H. 2014, ApJ, 790, 160

(ref: tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: tadhunter14) Tadhunter, C., Morganti, R., Rose, M., Oonk, J. B. R., & Oosterloo, T. 2014, Nature, 511, 440

(ref: talbot22) Talbot, R. Y., Sijacki, D., & Bourne, M. A. 2022, MNRAS, 514, 4535

(ref: ulivi24) Ulivi, L., Venturi, G., Cresci, G., et al. 2024, A&A, 685, A122

(ref: valentini20) Valentini, M., Murante, G., Borgani, S., et al. 2020, MNRAS, 491, 2779

(ref: vallini19) Vallini, L., Tielens, A. G. G. M., Pallottini, A., et al. 2019, MNRAS, 490, 4502

(ref: radex) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: vanderwerf10) van der Werf, P. P., Isaak, K. G., Meijerink, R., et al. 2010, A&A, 518, L42

(ref: veilleux20) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2

(ref: venturi21) Venturi, G., Cresci, G., Marconi, A., et al. 2021, A&A, 648, A17

(ref: venturi23) Venturi, G., Treister, E., Finlez, C., et al. 2023, A&A, 678, A127

(ref: vm17) Villar-Martı́n, M., Emonts, B., Cabrera Lavers, A., et al. 2017, MNRAS, 472, 4659

(ref: viti14) Viti, S., Garcı́a-Burillo, S., Fuente, A., et al. 2014, A&A, 570, A28

(ref: Ward24) Ward, S. R., Costa, T., Harrison, C. M., & Mainieri, V. 2024, MNRAS, 533, 1733

(ref: whitmore14) Whitmore, B. C., Brogan, C., Chandar, R., et al. 2014, ApJ, 795, 156

(ref: ye23) Ye, H., Sweijen, F., van Weeren, R., et al. 2023, arXiv e-prints, arXiv:2309.16560

(ref: zakamska14) Zakamska, N. L. & Greene, J. E. 2014, MNRAS, 442, 784

(ref: mavi21) Zanchettin, M. V., Feruglio, C., Bischetti, M., et al. 2021, A&A, 655, A25

(ref: mavi25) Zanchettin, M. V., Ramos Almeida, C., Audibert, A., et al. 2025, A&A, 695, A185

(ref: zubovas12) Zubovas, K. & King, A. 2012, ApJL, 745, L34

# Radio observations

We describe the main properties of the radio continuum observations used in this work. In Table [\[tab:radio\]](#tab:radio) we list the telescope and observed frequency, the synthesized beam size, rms and project name. We note that in the case of VLA observations, we only report the values for the HR configuration from (cite: jarvis19), which were the mostly used in this work.

+:------+:---------:+:---------:+:---------------------:+:--------------:+:--------------------:+:---------:+
| Name  | telescope | frequency | beam                  | rms            | project              | Reference |
|       +-----------+-----------+-----------------------+----------------+----------------------+-----------+
|       |           | (GHz)     | ($''$ $\times$ $''$)  | ($\mu$Jy/beam) | ID                   |           |
+-------+-----------+-----------+-----------------------+----------------+----------------------+-----------+
| J1010 | VLA       | 6         | 0.25$\times$0.22      | 79             | 13B-127              | \(1\)     |
+-------+-----------+-----------+-----------------------+----------------+----------------------+-----------+
| J1100 | VLA       | 6         | 0.23$\times$0.22      | 48             | 13B-127              | \(1\)     |
+-------+-----------+-----------+-----------------------+----------------+----------------------+-----------+
| J1100 | e-MERLIN  | 1.5       | 0.30$\times$0.18      | 300            | CY2217               | \(1\)     |
+-------+-----------+-----------+-----------------------+----------------+----------------------+-----------+
| J1347 | VLBA      | 15        | 1.25mas$\times$0.6mas | 48             | 2cm survey$^\dagger$ | \(2\)     |
+-------+-----------+-----------+-----------------------+----------------+----------------------+-----------+
| J1356 | VLA       | 6         | 0.37$\times$0.29      | 100            | 13B-127              | \(1\)     |
+-------+-----------+-----------+-----------------------+----------------+----------------------+-----------+
| J1430 | VLA       | 6         | 0.23$\times$0.23      | 23             | 13B-127              | \(1\)     |
+-------+-----------+-----------+-----------------------+----------------+----------------------+-----------+

Table notes: Columns indicate the main observational properties of the sample: name, telescope, frequency, beam size, rms, project ID, and reference for the works that describe the data reduction in detail. References: (1) (cite: jarvis19) (2): (cite: kellermann04). $^\dagger$ <https://www.cv.nrao.edu/2cmsurvey/>. Projects ID 13B-127 and CY2217 PI: C. Harrison.

# ^3D^BAROLO modelling

The results of the kinematic modelling using ^3D^BAROLO are shown in Figures [13](#fig:bar1010)-[17](#fig:bar1430) for the CO(3-2) emission. The main parameters derived from the best fit of the CO(3-2) data and of the CO(2-1) datacubes degraded to the resolution of CO(3-2) are shown in Table [3](#tab:barolo). All parameters are in agreement with the values obtained from the kinematic modelling presented in RA22.

+:------+:--------------------+:----------:+:----------:+:---------------:+
| Name  | CO                  | $i$        | PA         | $v_{\rm sys}$   |
|       +---------------------+------------+------------+-----------------+
|       | (J$\rightarrow$J-1) | ($^\circ$) | ($^\circ$) | ( km s$^{-1}$)  |
+-------+---------------------+------------+------------+-----------------+
|       | (2-1)               | 37$\pm$1   | 287$\pm$8  | -35             |
+-------+---------------------+------------+------------+-----------------+
|       | (3-2)               | 36$\pm$1   | 288$\pm$4  | -35             |
+-------+---------------------+------------+------------+-----------------+
|       | (2-1)               | 38$\pm$1   | 68$\pm$3   | 36              |
+-------+---------------------+------------+------------+-----------------+
|       | (3-2)               | 38$\pm$2   | 67$\pm$5   | 36              |
+-------+---------------------+------------+------------+-----------------+
|       | (2-1)               | 60$\pm$1   | 252$\pm$4  | 17              |
+-------+---------------------+------------+------------+-----------------+
|       | (3-2)               | 61$\pm$2   | 262$\pm$7  | -50             |
+-------+---------------------+------------+------------+-----------------+
|       | (2-1)               | 54$\pm$1   | 107$\pm$11 | 5               |
+-------+---------------------+------------+------------+-----------------+
|       | (3-2)               | 62$\pm$0   | 110$\pm$10 | 5               |
+-------+---------------------+------------+------------+-----------------+
|       | (2-1)               | 38$\pm$2   | 3$\pm$1    | 0               |
+-------+---------------------+------------+------------+-----------------+
|       | (3-2)               | 41$\pm$2   | 4$\pm$3    | 0               |
+-------+---------------------+------------+------------+-----------------+
| J1509 | (2-1)               | 43$\pm$1   | 266$\pm$4  | 0               |
+-------+---------------------+------------+------------+-----------------+
|       |                     |            |            |                 |
+-------+---------------------+------------+------------+-----------------+

: ^3D^BAROLO  best fits for the CO(2-1) and CO(3-2) data.

![](SDSS_J101043_maps_local.pdf)

![](J1100+0846_maps_local.pdf)

![](J1347+1217_maps_local.pdf)

![](SDSSJ1356+10_maps_local.pdf)

![](Teacup_AGN_maps_local.pdf)

# Dispersion and rotation dominated systems

We present the velocity over the velocity dispersion maps, $v/\sigma$, for the six QSO2s studied in this work in Figure [18](#fig:vsig). To create the $v/\sigma$ maps we used the higher resolution CO(2-1) observations, except for J1010, for which we used the higher spatial resolution CO(3-2) data.

All but one systems appear to be rotation-dominated in most of the emitting regions according to the criterion $v/\sigma>$1, highlighted by the dotted blue lines showing the $v/\sigma$=1 contour. The regions showing $v/\sigma<$1 correspond to the line of zeros in the velocity field, as expected for rotation along the minor axis of the galaxies. The exception is J1356, where high velocity dispersion values ($v/\sigma<$1) dominate the main gas concentration (i.e. J1356N), while the western arc shows lower velocity dispersion, as shown by the moment maps in Figure [2](#fig:co32moms). Therefore, the determination of the rotation curve for this galaxy is not accurate and therefore we did not derive scenarios I and III for the outflows, which rely on a correct determination of gas rotation.

![](V_sig.png)

[^1]: We note that the double-peaked morphologies seen in CO do not mean the galaxy necessarily host two nuclei. For the cases in which there are two nuclei identified in the optical images and in ALMA continuum at 200 GHz, namely J1347 and J1356, we show the position of the second nucleus in Figure [2](#fig:co32moms) as blue stars.

[^2]: Overall the average values derived for the CO(3-2) inclination and PA are similar or the same as those derived using the CO(2-1) line, see Table [3](#tab:barolo) in Appendix [7](#sec:baloro).

[^3]: J1356 shows a jet-like morphology extending up to 2.6$''$ (5.7 kpc) in the LR data (1$''$ resolution), but not in the HR data (0.25$''$ resolution).

</paper>

Write the methods card for this paper.