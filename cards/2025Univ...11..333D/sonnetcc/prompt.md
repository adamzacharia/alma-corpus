# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025Univ...11..333D\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025Univ...11..333D",
 "title": "Jets in Low-Mass Protostars",
 "year": 2025,
 "journal": "Universe",
 "first_author": "Dutta, Somnath",
 "n_authors": 1,
 "arxiv_id": "2510.12475",
 "doi": "10.3390/universe11100333",
 "alma_projects_linked_by_archive": [
  "2018.1.00302.S"
 ]
}
```

Paper text:
<paper>
# Jets in Low-Mass Protostars

# Introduction

Protostellar jets and outflows are ubiquitous phenomena observed during the early stages of star formation. Jets are highly collimated, fast-moving streams of gas ejected from the inner disk regions of young stellar objects (YSOs), often reaching velocities of several hundred kilometers per second. In contrast, winds or outflows generally refer to broader, less collimated flows of gas, typically moving at a few kilometers per second to a few tens of kilometers per second, launched from wider regions of the disk and often entrained by the jets (cite: 2001ARA&A..39..403R; 2007prpl.conf..245A; 2014prpl.conf..451F; 2014prpl.conf..387A; 2016ARA&A..54..491B; 2020A&ARv..28....1L; 2021NewAR..9301615R). Together, jets and outflows play a crucial role in removing excess angular momentum from the protostellar disk, thereby enabling mass accretion onto the central star (cite: 2016ARA&A..54..491B; 2017NatAs...1E.152L). An example of a protostellar system, G203.21-11.20W2, is shown in Figure [1](#fig:ALMA_jet_out_cont). A narrow, collimated jet, traced by SiO emission, is observed along the flow axis, within a wide-angle bipolar outflow cavity delineated by CO emission. The protostar, embedded within a dense envelope traced by 1.3 mm continuum emission, is located at the origin point where the two outflow lobes diverge.

Two primary theoretical frameworks have been proposed for the launching of jets: the X-wind model, where jets originate from a narrow region near the inner edge of the accretion disk at the magnetospheric truncation radius (cite: 1994ApJ...429..781S; 2000prpl.conf..789S), and the disk wind model, where winds are launched from a wider range of disk radii via magneto-centrifugal forces (cite: 2007prpl.conf..277P). Both models have been successful in explaining certain observational features, yet debates persist over their relative contributions in different sources. Recent models of both X-winds and magneto-hydrodynamic disk winds indicate that these mechanisms can generate not only highly collimated jets but also wider-angle winds, suggesting that the dichotomy between jets and winds is not always clear-cut (cite: 2020ApJ...905..116S).

![](G203W2_rgb_wcs.pdf)

Protostellar jets can be observed in molecular, atomic, and ionized forms. Jets are traced across multiwavelengths—from radio, (sub)millimeter, and infrared to optical—revealing their structure and dynamics (cite: 2016ARA&A..54..491B; 2020A&ARv..28....1L; 2021NewAR..9301615R).

The combination of molecular, atomic, and ionized jet studies provides a comprehensive view of jet evolution and propagation. Observations of these multiwavelength species enable the estimation of crucial physical parameters. For instance, the jet mass-loss rate provides a measure of how efficiently the protostar expels material, while the jet and outflow momentum flux or force offers insights into the feedback exerted on the surrounding environment. The dynamical time inferred from jet length and velocity gives an estimate of the jet’s age and episodic behavior. Additionally, by comparing jet and outflow mass-loss rates to the estimated accretion rates, often inferred from bolometric luminosity or infall tracers, one can evaluate the efficiency of jet launching mechanisms and the coupling between mass ejection and accretion. Together, these parameters help to constrain the physical processes that govern jet launching, collimation, propagation, and their impact on star and disk evolution.

Recent high-angular resolution observations with instruments such as the Atacama Large Millimeter/submillimeter Array (ALMA) and the James Webb Space Telescope (JWST) have revolutionized our understanding of protostellar jets and outflows. ALMA’s ability to resolve molecular emission at sub-arcsecond scales has revealed detailed structures of jet launching regions and outflow cavity walls (e.g., Figure [1](#fig:ALMA_jet_out_cont)), while JWST’s infrared sensitivity enables unprecedented views of shock-excited gas and embedded jet components (e.g., Figure [2](#fig:jwst_miri_hops315)). These advances provide new constraints on the jet launching mechanisms, evolutionary status of a protostar, accretion phase, and their impact on star and planet formation. In this review, we describe recent advances in the study of protostellar jets using observations from the ALMA and JWST telescopes.

# Discovery and Theoretical Foundations

The discovery of protostellar jets began with the identification of compact emission-line nebulae near young stars, now known as Herbig–Haro (HH) objects. These were independently reported by Herbig (1951) and Haro (1952), who interpreted them as signatures of high-velocity outflows from protostars interacting with the surrounding interstellar medium (cite: 1951ApJ...113..697H; 1952ApJ...115..572H). Their work laid the foundation for the modern study of stellar jets and outflows. Subsequently, (cite: 1980ApJ...239L..17S) detected large-scale bipolar molecular outflows traced by CO emission. It is now well established that molecular outflows and jets are a ubiquitous feature of accreting, rotating, and magnetized protostellar systems (cite: 1980ApJ...239L..17S; 1992A&A...261..274C; 1996A&A...311..858B; 2014ApJ...783...29D; 2015A&A...576A.109Y; 2021A&A...648A..45P; 2024AJ....167...72D). These observations also revealed a strong link between outflow activity, accretion processes, and protostellar evolution. Together, these discoveries established that mass loss is a fundamental aspect of early stellar evolution.

![](HOPS315_MIRI_H2.pdf)

Protostellar jets and outflows emerge naturally during the gravitational collapse of dense molecular cloud cores. In the initial isothermal collapse phase, efficient cooling allows the core to contract while maintaining a temperature of typically $\sim$10 K. As central densities increase, the collapse becomes adiabatic, leading to the formation of the first hydrostatic core (cite: 1969MNRAS.145..271L). During this stage, magneto-centrifugal forces and magnetic pressure gradients launch low-velocity, wide-angle outflows (cite: 1998ApJ...502L.163T; 2008ApJ...676.1088M). When temperatures reach $\sim$2000 K, molecular hydrogen dissociates, triggering a second collapse that forms the protostar. This leads to the emergence of fast, highly collimated jets driven by strong magnetic forces from the inner regions of the disk or the protostar itself (cite: 2008ApJ...676.1088M; 2013ApJ...763....6T).

# Physical Properties and Observational Characteristics of Jets and Outflows

## Molecular vs Neutral and Ionized Components

Jets from YSOs consist of molecular, neutral atomic, and ionized components, each traced by distinct sets of emission lines that probe different physical conditions and spatial regions within the jet–outflow system, as demonstrated in Figure [3](#fig:schematic_molecular_atomic). In the case of (sub)millimeter observations, molecular tracers such as CO, SiO, SO, and H$_2$CO are effective in probing the cooler components of the flow, typically at temperatures ranging from a few tens to a few hundreds of Kelvin. The lower-$J$ transitions, such as CO(1–0), CO(2–1), SiO(2–1), SiO(3–2), and H$_2$CO lines, are sensitive to lower-density, low-velocity, wide-angle outflows, or wind components, and are often associated with entrained ambient gas (e.g., (cite: 1996A&A...311..858B; 2014ApJ...783...29D)). However, some of these transitions can also be excited in high-velocity, high-density jets, particularly in shock-excited regions. In contrast, the higher-excitation transitions, including CO(3–2), SiO(5–4), SiO(8–7), and high-$J$ H$_2$CO lines, trace denser, warmer gas in the collimated jet cores, where shocks and magnetic launching mechanisms dominate the dynamics (e.g., (cite: 2014ApJ...783...29D; 2015A&A...576A.109Y; 2017NatAs...1E.152L; 2021A&A...648A..45P; 2024AJ....167...72D)). In infrared observations, the H$_2$ pure rotational (e.g., H$_2$ 0-0 S(1)) and ro-vibrational (H$_2$ 1-0 S(1), S(2), S(3), S(4), S(5), S(7, S(7)) are frequently observed in jets and outflows (e.g., Figure [2](#fig:jwst_miri_hops315)). The shorter wavelengths (e.g., H$_2$: 0-0 S(1); 1-0 S(7), S(6), S(5), S(4)) are often concentrated in the jets, while the longer wavelengths are also trace the wide angle outflow components (e.g., 1-0 S(1), S(2), S(3)) (cite: 2023ApJ...951L..32H; 2023Natur.622...48R; 2024ApJ...962L..16N; 2024A&A...687A..36T; 2024A&A...688A..26A; 2024A&A...691A.134C; 2025A&A...695A.145V; 2025ApJ...982..149O; 2025ApJ...985..225L). We note that, in some cases, the shorter-wavelength, lower-excitation rotational lines of H$_2$ also trace the wider-angle outflow rather than the collimated jet, as demonstrated by the JOYS program (cite: 2025A&A...699A.361V); however, this behavior is not universal.

In contrast, neutral atomic (e.g., \[O I\], \[C I\], \[S I\]) and ionized atomic tracers (e.g., \[S II\], \[N II\], \[O III\], \[Fe II\], H$\alpha$) reveal hotter ($T \sim 10^4$ K), lower-density regions, often linked to fast-moving, collimated jets and internal shocks (cite: 1995ApJ...452..736H; 2016ARA&A..54..491B). Forbidden lines such as \[S II\] $\lambda$6716, 6731 Å, \[N II\] $\lambda$6583 Å, and \[Fe II\] 1.644 μm commonly serve as effective tracers of physical conditions such as electron density, ionization fraction, and excitation temperature (cite: 2001ARA&A..39..403R; 2006A&A...459..821G). Hydrogen recombination lines like H$\alpha$ are also detected in ionized jets and accretion regions, indicating regions of high temperature and density (cite: 1998ApJ...492..743M). Moreover, mid-infrared ionized lines such as \[Ne II\] 12.8 μm and \[Fe II\] 25.99 μm, observed with instruments like *Spitzer* and *JWST*, provide access to deeply embedded or heavily extincted jet regions (cite: 2007ApJ...665..492L; 2012A&A...545A..44P).

Spatially, molecular emission tends to dominate on larger scales where shocks dissipate, while ionized emission is prominent near jet-driving sources or in high-velocity knots along the jet axis. Together, these components offer complementary insights: molecular lines trace momentum transfer and jet-envelope interactions, while ionized lines reveal shock heating, excitation mechanisms, and jet launching dynamics. A combined analysis is essential for a complete understanding of jet physics across evolutionary stages.

![](outflowJetSchematic_review.pdf)

## Morphology and Structure

Jets and outflows from protostars exhibit distinct morphological and structural characteristics, reflecting their different physical origins at the disk, their interaction with the envelope, and the evolutionary stages of the driving protostars. Collimated jets are typically narrow with high velocities, $v_j \sim 40$ km s$^{-1}$ to a few 100 s of km s$^{-1}$ with a mean of $\sim$110 km s$^{-1}$ (cite: 2024AJ....167...72D). As shown in the example in Figure [4](#fig:monopolarity_episodicJet), the jets often appear as chains of bright knots or bow shocks along their axes (e.g., (cite: 2001ARA&A..39..403R; 2015Natur.527...70P; 2016ARA&A..54..491B; 2024AJ....167...72D)). These knots result from episodic ejection events and internal shocks, while bow shocks mark the interaction between the jet and the surrounding medium. Jets are usually well-collimated with opening angles of only a few degrees, particularly near the launching region. In contrast, molecular outflows are broader, wide-angle structures with lower characteristic velocities ($v \lesssim$ 10–30 km s$^{-1}$) and exhibit a more conical or lobe-like appearance (cite: 2007prpl.conf..245A; 2014prpl.conf..451F; 2024AJ....167...72D).

The intrinsic opening angle ($\theta_{\text{int}}$) of the wide-angle outflow can be obtained from the observed opening angle, $\theta_{\text{obs}}$, and the inclination angle, $i$ (with $i = 0^\circ$ representing an edge-on disk and $i = 90^\circ$ a pole-on system), through the geometric relation: $$\begin{equation}
\theta_{\text{int}} = 2 \cdot \tan^{-1} \left( \frac{\tan\left( \tfrac{\theta_{\text{obs}}}{2} \right)}{\cos(i)} \right).
\end{equation}$$ Protostellar outflows trace ambient material that has been entrained and accelerated by underlying jets or wide-angle winds, often producing cavities shaped by shocks.

The cavity opening angle serves as a useful indicator of protostellar evolution: in the Class 0 phase, cavities are narrow and poorly defined due to dense envelopes and high accretion rates (cite: 1996A&A...311..858B; 2014ApJ...783....6V; 2017AJ....153..173H); during the Class I stage, successive ejection events progressively widen the cavities as the envelope mass declines; by Class II, cavities often appear broad and conical, with some systems revealing the underlying disk–jet structure (cite: 2008ApJ...675..427S; 2011ApJ...743...91O).

![](G209_55-19_68S2SiO_intgrated_pv.pdf)

## Shock Processing

Shocks in protostellar jets are commonly classified as either J-type (jump) or C-type (continuous), which differ in their internal structure and in how they affect molecules and chemistry (e.g., (cite: 1997IAUS..182..181H)). In a J-type shock, the gas undergoes an abrupt discontinuity in physical conditions (density, temperature) at the shock front; molecules may be dissociated or ionized in the shock, and they must re-form in the post-shock region. In contrast, a C-type shock develops in a weakly ionized medium with a significant magnetic field: ions (and charged particles) are tied to magnetic field lines and drag neutrals via ion–neutral collisions, resulting in a smoother, continuous transition in physical conditions (rather than a sharp “jump”) over a finite shock thickness. Because of this, molecules may survive passage through a C-type shock, and heating is more gradual; these differences strongly influence emission signatures, chemical abundances, and cooling behavior (e.g., (cite: 1997IAUS..182..181H)). In many jet/outflow systems, a mixture of J-type and C-type shock zones may coexist (e.g., at bow shock apices versus wings) depending on local physical conditions.

Protostellar jets are inherently variable, and fluctuations in their ejection velocity naturally generate internal shock structures where faster parcels of gas collide with slower ones. As demonstrated in Figure [3](#fig:schematic_molecular_atomic), these interactions form compact internal working surfaces characterized by a reverse shock that decelerates the jet gas and a forward shock that accelerates the ambient medium (cite: 1990ApJ...364..601R). Numerical simulations and observations (e.g., (cite: 2017A&A...597A.119T)) demonstrate that such internal shocks not only act along the jet axis but also drive sideways ejections, pushing shocked gas laterally into the surrounding envelope and producing expanding bow-shock structures within the jet. On larger scales, the overall bow-shaped interaction between the jet and its environment is described by a system of forward and reverse shocks (cite: 2001ApJ...557..429L; 2021ApJ...909...11J): the forward shock propagates into the ambient cloud, sweeping up molecular gas into wide cavities, while the reverse shock propagates back into the jet beam, compressing and energizing the jet material. This combination of internal shocks with lateral expansion and terminal forward–reverse shock pairs provides a unifying framework for the stratified kinematic and chemical structures observed in protostellar outflows, including compact knots and bullets along the jet channel together with broader, slower outflow lobes and shells.

## Chemical Composition in Shock Signatures

Jets and outflows profoundly alter the chemistry of their surroundings through shock-driven processes. As high-velocity material impacts the ambient medium, shocks trigger heating, sputtering of dust grains, and gas-phase reactions that release molecules from grain mantles, thereby enhancing the abundances of key species (cite: 1983ApJ...264..485D; 1997ApJ...487L..93B). Prominent tracers of such activity include submillimeter molecular species such as SiO, SO, CO, and CH$_3$OH whose abundances can increase by several orders of magnitude compared to quiescent gas (cite: 2008A&A...490..695G; 2010A&A...522A..91T), as well as infrared atomic and ionic lines (e.g., \[Fe II\], \[S I\]) and molecular transitions at various vibrational or rovibrational levels.

SiO is widely regarded as a hallmark of strong shocks (shock velocity, $v_s \gtrsim 20$ km s$^{-1}$), originating from the sputtering of silicate grains followed by gas-phase reactions. In contrast, molecules such as CH$_3$OH and H$_2$CO are typically associated with lower-velocity shocks or thermal desorption of grain mantles (cite: 1997A&A...321..293S; 1991ApJ...373..254G). As illustrated in Figure [3](#fig:schematic_molecular_atomic), different tracers highlight distinct layers of the shock structure: CO transitions trace the extended shock region, higher-$J$ SiO transitions are strongest at the forward shock and its immediate post-shock layers, while near-infrared H$_2$ emission marks the shock front.

These chemical signatures also act as chemical clocks, constraining shock timescales and outflow evolution. For example, models predict that elevated H$_2$O abundances induced by C‐type shocks persist for $4\text{–}7\times10^5\,$yr before declining again (cite: 1998ApJ...499..777B). MHD shock models and gas–grain chemistry suggest that molecules sputtered from grain mantles may survive for only tens of years post‐shock, showing rapid decline in abundance (cite: 2018Ap&SS.363..151N). Observations of complex species in the L1157-B1 outflow, whose age is $<2000\,$yr, indicate that those molecules are shock-released mantle products whose presence traces recent shock activity (cite: 2008ApJ...681L..21A). Models of episodic protostellar accretion likewise show that molecular tracers such as HCO$^+$ and N$_2$H$^+$ return to quiescent levels only after $10^3\text{–}10^5\,$yr, making them effective clocks for past heating or shock events (cite: 2015A&A...577A.102V).

On larger scales, repeated shocks inject turbulence, shape photodissociation regions (PDRs), and modify the ionization structure of the surrounding cloud (cite: 2007prpl.conf..245A; 2021A&A...648A..24V). Over time, such chemical feedback enriches outflow cavities and influences the conditions for subsequent star formation. Studying the chemical composition and shock tracers in protostellar jets therefore provides critical insights into the coupling between stellar feedback, gas dynamics, and astrochemistry in star-forming environments.

## Velocity Gradients and Rotation Signatures in Protostellar Jets and Outflows

Velocity gradients perpendicular to the jet axis are commonly observed in high spectral and spatial resolution studies of protostellar systems. These gradients have been interpreted as potential signatures of jet rotation (cite: 2002ApJ...576..222B; 2004ApJ...604..758C; 2007ApJ...670.1188L; 2017NatAs...1E.152L), providing insights into angular momentum transport during the earliest stages of star formation. If interpreted as rotation, these gradients allow estimates of the jet launching radius under the magneto-centrifugal wind framework (e.g., (cite: 2003ApJ...590L.107A; 2006A&A...453..785F; 2017NatAs...1E.152L)).

However, confirmation of rotation requires careful consideration of projection effects, beam smearing, and asymmetric shock structures, as emphasized by (cite: 2005A&A...435..125S).

In several Class 0/I protostellar jets, transverse velocity shifts of a few km s$^{-1}$ across the jet width have been reported, suggesting rotation in the launching region. For instance, (cite: 2002ApJ...576..222B) observed systematic velocity gradients across the DG Tau jet using HST/STIS, interpreting them as rotational motion. ALMA observations have extended such detections to molecular jets, including SiO and CO, in deeply embedded protostars (cite: 2007ApJ...665..492L; 2017NatAs...1E.146H). In the HH 212 system, (cite: 2017NatAs...1E.152L) estimated the jet launching radius to be $\sim 0.05^{+0.05}_{-0.02}$ AU using very high angular resolution ($\sim$16 AU) observations, providing the most precise measurement to date.

In wide-angle molecular outflows, transverse velocity gradients have also been identified, although distinguishing rotation from other asymmetries (e.g., jet precession, sideways ejection) remains challenging (cite: 2007prpl.conf..245A; 2009A&A...494..147L). Detailed modeling is often required to rule out alternative explanations. Rotating protostellar outflows trace angular momentum removal from disks, often via magnetohydrodynamic (MHD) disk winds. For example, in HH 212, SO emission reveals a rotating wide-angle disk wind around an episodic SiO jet. Resolving this outflow shows a collimated jet, a wide-angle disk wind, and a jet-driven cavity, confirming that disk winds efficiently extract angular momentum and providing a probe of large-scale magnetic fields in disks (cite: 2021ApJ...907L..41L). Recent ALMA observations of HH 212 at $\sim$24 au resolution (cite: 2024ApJ...977..126L) reveal a rotating wind launched from 9–15 au, situated between the SiO and CO shells. This shocked rotating wind interacts with the inner X-wind and mixes with SO emission, efficiently removing angular momentum and shaping the outflow structure.

## Physical Parameters

Jets and outflows from protostars exhibit a wide range of physical parameters that are crucial for understanding their roles in star formation. Typical mass-loss rates range from $\sim$$10^{-9}$ to $10^{-5}$ M$_\odot$ yr$^{-1}$, and generally vary with protostellar mass and evolutionary stage (cite: 2007A&A...468L..29C; 2014prpl.conf..451F). Although there is a connection between mass-loss rates and protostellar mass and evolution, this relationship is not monotonic; for instance, individual systems can vary significantly and do not always follow a trend of higher mass-loss rates with increasing protostellar mass. Molecular outflows usually dominate in terms of mass, while atomic jets carry significant kinetic energy and momentum flux. The momentum flux (or force) of outflows can reach values of $10^{-6}$ to $10^{-2}$ M$_\odot$ km s$^{-1}$ yr$^{-1}$, often correlating with the luminosity and accretion rate of the driving source (cite: 2002ApJ...576..222B; 2007prpl.conf..245A). Energetics analyses reveal that outflows can inject enough energy and momentum to significantly affect their surroundings, regulating star formation efficiency and driving turbulence in molecular clouds.

Typical particle densities vary from $10^3$ to $10^6$ cm$^{-3}$ in molecular outflows to $10^2$ to $10^4$ cm$^{-3}$ in atomic jets, with local enhancements in shock regions (cite: 1996A&A...311..858B; 1995ApJ...452..736H). Corresponding temperatures range from $\sim$10 to 100 K in cold molecular gas up to several thousand Kelvin in ionized or shocked atomic components (cite: 2005A&A...441..159N; 2013ApJ...778...71G). Together, these physical parameters provide a comprehensive framework for evaluating jet energetics, mass and momentum budgets, and their feedback on star-forming environments.

Figure [5](#fig:jet_accretion) shows the jet mass-loss rates as a function of accretion rates for protostars. Sources with molecular jets, which are typically younger, exhibit systematically higher accretion and ejection activity than T Tauri stars, which are generally more evolved and show lower rates. The two groups have been fitted separately with a logarithmic relation:

$$\begin{equation}
\log_{10}(\dot{M}_j) = \alpha \cdot \log_{10}(\dot{M}_{\text{acc}}) + \beta ,
\end{equation}$$ $$\begin{equation}
\dot{M}_j \propto \dot{M}_{\text{acc}}^{\alpha}
\end{equation}$$

The molecular jets show relatively shallow slopes ($\alpha$$\sim$0.40) compared to T Tauri stars ($\alpha$$\sim$0.57). This implies that younger objects tend to accrete at higher rates but eject smaller fraction of that mass. This Figure  [5](#fig:jet_accretion) illustrates that jets and outflows play a significant role in regulating protostellar growth and evolution. In particular, as the system evolves toward the T Tauri stage, the relative mass-loss efficiency increases, indicating that outflow activity becomes more effective at removing material rather than settling the mass onto the star.

![](jet_vs_accretion_mcmc_fit.pdf)

## Monopolarity Nature

While many protostellar jets and outflows exhibit bipolar symmetry, an increasing number of systems show monopolar or highly asymmetric morphologies. In such cases, emission is detected from only one lobe—in molecular lines, atomic tracers, or continuum maps. For example, the G209.55$-$19.68S2 source (HOPS 10) in Figure [4](#fig:monopolarity_episodicJet) shows one-sided SiO jet emission, with the opposite lobe absent in both SiO and CO.

The observed jet asymmetry likely arises from multiple factors, with geometry being key. In protostars, JWST-detected infrared emission is strongly affected by extinction from the envelope (e.g., Figure [2](#fig:jwst_miri_hops315)), particularly along the redshifted side (e.g., (cite: 2023ApJ...951L..32H; 2024A&A...692A.143B; 2024ApJ...966...41F; 2025A&A...699A.361V)). The orientation relative to the line of sight also introduces projection effects, while deeply embedded regions may remain invisible due to high optical depth.

Doppler boosting, important in relativistic AGN jets (e.g., M87; (cite: 2007ApJ...668L..27K; 2007ApJ...658..232C)), is negligible in protostellar jets since their velocities (a few hundred km s$^{-1}$) are too low. Yet nearly half of protostars with SiO jets appear monopolar at millimeter wavelengths (cite: 2024AJ....167...72D). Because dust extinction is minimal at submillimeter wavelengths, this high incidence cannot be explained by extinction alone, suggesting intrinsic launching asymmetries, possibly linked to magnetic field geometry or star–disk interactions.

Jet-launching models that include a stellar magnetosphere generate oppositely directed poloidal fields and a quadrupolar toroidal structure, enabling reconnection and driving jets in both hemispheres—consistent with bipolar outflows (e.g., (cite: 1994ApJ...429..781S; 2000prpl.conf..789S; 2003ApJ...599..363A; 2007prpl.conf..277P)). In contrast, disk-only magnetic fields are inherently asymmetric: the toroidal field remains unipolar within each hemisphere, lacking reversals across latitudes. Reconnection and amplification processes, such as avalanche accretion streams, then operate effectively only in one hemisphere (cite: 2025ApJ...988..107T; 2025arXiv250611333T). This asymmetry favors jet launching on a single side, producing unipolar rather than bipolar outflows.

## Episodic Nature and Their Origin

Jets and outflows from protostars often display a distinctly episodic character, with chains of knots, bow shocks, and discrete ejections tracing their axes (cite: 2001ARA&A..39..403R; 2016ARA&A..54..491B; 2015Natur.527...70P). An example of such episodic knots is shown in Figure [4](#fig:monopolarity_episodicJet). These structures arise when variable ejection speeds cause faster material to overtake earlier, slower ejecta, generating internal shocks (cite: 1990ApJ...364..601R; 1995ApJ...452..736H). Observations of proper motions and radial velocities suggest recurrence timescales ranging from a few years to several hundred years, depending on the system (cite: 2014A&A...563A..87E; 2015ApJ...805..186L; 2024AJ....167...72D).

This episodicity is widely attributed to unsteady accretion, with mass inflow onto the protostar closely linked to jet launching (e.g., (cite: 2014prpl.conf..387A)). Proposed drivers include disk instabilities—gravitational or magneto-rotational—magnetospheric reconnection, and dynamical perturbations from companions (cite: 2015ApJ...805..115V). Disk or jet precession may further modulate the ejection geometry, producing complex morphologies (cite: 2002ApJ...580..950M; 2010ApJ...713..731L). Such discontinuities likely reflect temporal variations in jet velocity or density, tied to quasi-periodic perturbations of the accretion flow. Candidate mechanisms include binary-induced variability, gravitational instabilities in the envelope or disk, episodic planetesimal accretion, and instabilities near dust sublimation fronts (cite: 2014prpl.conf..387A; 2020A&ARv..28....1L; 2023ASPC..534..355F).

Observationally, SiO jets often exhibit clumpy, knotty structures that may reflect quasi-periodic ejections, with inferred recurrence times of $\sim$20–175 years (cite: 2024AJ....167...72D). As shown in Figure [6](#fig:episodicity_luminosity_envelopeMass), the episodicities do not show any clear dependence on luminosity, most likely because luminosity alone does not reliably trace evolutionary status. Protostellar luminosity is the sum of internal luminosity and variable accretion-driven contributions, the latter decreasing with time after an outburst. In contrast, envelope mass more directly reflects the evolutionary state of the core hosting the protostar (e.g., (cite: 2023ApJ...944...49F)).

Systems with smaller envelope masses tend to exhibit reduced accretion and ejection activity. However, the relationship between ejection variability and envelope mass is not straightforward: the timescales traced by shocked knots indicate that accretion is highly system-dependent, influenced by factors such as the disk and stellar magnetic fields, as well as the infall properties of each individual system. Cores with inherently low-mass envelopes could not be distinguished or fully accounted for in this scenario.

![](Period_Lbol_Menv.pdf)

Multiple periodicities have been reported in individual systems, such as HH 34, HH 111, and HH 212, spanning years to decades (cite: 1998Natur.394..862Z; 2002A&A...395..647R), suggesting the coexistence of different accretion perturbation modes. Complementary evidence comes from long-term monitoring: the JCMT Transient Survey revealed submillimeter variability on decadal scales (cite: 2017ApJ...849...43H; 2021ApJ...920..119L), while NEOWISE mid-infrared data uncovered secular variability among embedded YSOs (cite: 2021ApJ...920..132P).

Estimating orbital radii from observed knot periods yields characteristic perturbation zones at $\sim$2–25 au for typical protostellar masses (cite: 2024AJ....167...72D), consistent with instabilities in small to intermediate disks rather than binary orbital forcing. Although correlations with luminosity and envelope mass remain weak or statistically inconclusive, these episodic jets provide crucial probes of time-dependent accretion and the dynamical evolution of protostellar disks. Continued monitoring and modeling will be essential to clarify the link between accretion variability and jet launching.

## Disk Winds Around the Jets?

Protostellar outflows generally consist of two main components: disk winds and jet winds (or simply jets), both of which play crucial roles in the star formation process. Disk winds are launched from a relatively extended region of the protostellar disk, typically ranging from $\sim$0.1 to a few astronomical units (au), where large-scale magnetic fields enable the ejection of material via magneto-centrifugal processes (cite: 1982MNRAS.199..883B; 2007prpl.conf..277P). These winds tend to have broad opening angles and moderate velocities, often around 1 to a few 10 s km s$^{-1}$, and are thought to efficiently carry away angular momentum from the disk, allowing sustained accretion. In contrast, jet winds originate from the innermost regions near the star–disk interface, typically within a fraction of an au. These jets are highly collimated along the flow-axis, with velocities that can exceed 40–300 km s$^{-1}$, and are commonly modeled as magnetically driven X-winds or magnetospheric ejections (cite: 1994ApJ...429..781S; 2006A&A...453..785F). Observationally, disk winds are often traced by molecular emission lines such as CO and SO at (sub)millimeter wavelengths, and by infrared lines of H$_2$ or atomic species in warmer regions (e.g., (cite: 2016Natur.540..406B; 2025dutta)). Jets, on the other hand, are traced by high-velocity atomic and ionized lines such as \[S II\], \[Fe II\], and H$\alpha$ in optical and infrared observations, and by shock-excited molecules such as SiO and CO in deeply embedded sources (cite: 2014prpl.conf..451F; 2016ARA&A..54..491B). While both components are magnetically driven, they differ in terms of launching regions, kinematics, collimation, and chemical tracers. Together, they reveal a complex, multi-component ejection process, with jets often showing episodic variability and bow shocks, while disk winds drive more continuous, wide-angle flows. Recent high-resolution observations with ALMA and JWST are beginning to resolve these components simultaneously, offering new insights into their interplay and their roles in disk evolution and star formation feedback (cite: 2017NatAs...1E.152L; 2020A&A...640A..82T).

# Launching Models

Several theoretical models have been proposed to explain the launching of jets and winds from protostellar systems, broadly classified into three main categories: X-winds, disk winds, and stellar winds. The *X-wind* model posits that jets are launched from a narrow region near the disk truncation radius, close to the corotation point with the star (typically fraction of one AU), where magnetic fields efficiently extract angular momentum and drive collimated outflows (cite: 1994ApJ...429..781S; 2007prpl.conf..261S), as illustrated in the schematic diagram shown in Figure [7](#fig:schematic_x-wind_disk-wind). In contrast, disk wind models propose that winds originate from a broader range of disk radii (typically 0.1 to a few 10 s of AU), with magnetic field lines anchored over an extended region of the disk surface launching material along open field lines via magneto-centrifugal acceleration (cite: 1982MNRAS.199..883B; 2006A&A...453..785F; 2007prpl.conf..277P), as demonstrated in Figure [7](#fig:schematic_x-wind_disk-wind). Disk winds generally produce wide-angle outflows and can efficiently remove angular momentum from the disk, supporting sustained accretion. In addition, thermally driven photoevaporative winds, launched from the disk surface by stellar UV and X-ray irradiation, provide another pathway for disk mass loss and can complement MHD-driven winds (e.g., (cite: 2021ApJ...913..122R; 2025ApJ...986..161H)). It is important to note that recent studies suggest that both X-winds and MHD disk winds can drive highly collimated jets as well as broader, less-collimated outflows, implying that the traditional separation between jets and winds may be overly simplistic (e.g., (cite: 2020ApJ...905..116S)). A third scenario involves stellar winds, driven by magnetic pressure or thermal gradients directly from the protostar itself (cite: 2005ApJ...632L.135M).

![](schematic_x-wind_disk-wind.pdf)

While stellar winds alone are unlikely to explain the highly collimated jets observed in young protostars, they may contribute to inner outflow regions. Recent high-resolution observations suggest that both X-winds and disk winds may operate simultaneously or sequentially in some systems, with disk winds responsible for wide-angle molecular outflows and X-winds accounting for high-velocity, collimated jets (cite: 2014prpl.conf..451F; 2020A&A...640A..82T). However, distinguishing between these models observationally remains challenging, as signatures often overlap.

# Future Works

Future research on protostellar jets and outflows will greatly benefit from the synergy between infrared and (sub)millimeter observations, particularly combining the capabilities of the James Webb Space Telescope (JWST) and the Atacama Large Millimeter/submillimeter Array (ALMA). JWST provides unprecedented sensitivity and spatial resolution in the infrared, ideal for probing warm molecular and atomic gas, as well as shock-excited regions along jets and outflow cavities (cite: 2022ApJ...936L..14P). ALMA, in turn, offers high-resolution imaging of cold molecular gas, shocked gas and dust structures at (sub)millimeter wavelengths, allowing detailed studies of jet launching regions, disk kinematics, and entrained outflows (cite: 2016Natur.540..406B; 2020A&A...640A..82T). Together, these facilities enable multi-wavelength studies that can trace jets across a wide range of temperatures and physical conditions, offering new insights into the interplay between accretion, ejection, and envelope clearing. Another promising avenue involves exploring the impact of jet feedback on planet formation. Jets and outflows can regulate disk mass and angular momentum, potentially influencing the formation and migration of planetary cores within the disk (cite: 2016ApJ...821...80B; 2021ApJ...915...90N). Incorporating jet-driven disk evolution into planet formation models is an emerging field, with future observational and theoretical efforts likely to clarify how early protostellar feedback shapes the initial conditions for planet formation.

# Summary and Conclusions

Jets and outflows play a central role in the evolution of protostars, acting as key agents in low-mass star formation by regulating the transport of mass, momentum, and angular momentum, and by influencing the surrounding environment. Traced by molecular, ionized, and atomic species at (sub)millimeter and infrared wavelengths, these flows provide crucial insights into the accretion–ejection connection and the early stages of protostellar evolution.

Jets are typically highly collimated, high-velocity components launched from the innermost disk regions, while broader, slower disk winds emerge from larger disk radii. Both components play complementary roles in regulating disk evolution and accretion.

Recent advances from high-resolution facilities such as the Atacama Large Millimeter/submillimeter Array (ALMA) and the James Webb Space Telescope (JWST) have dramatically enhanced our ability to resolve the physical and chemical structures of jets and outflows across multiple scales and wavelengths. ALMA has provided unprecedented details on molecular gas kinematics, jet launching regions, and disk winds, while JWST has unveiled deeply embedded infrared counterparts and shock-excited features in outflow cavities and jets.

Despite significant progress, challenges remain in fully disentangling different launching mechanisms, including X-winds, disk winds, and stellar winds. No single model can yet explain the diversity of observed morphologies, kinematics, and chemical properties. Future coordinated, multi-wavelength studies with ALMA, JWST, and upcoming facilities promise to further constrain jet launching physics and their role in disk evolution and planet formation. Although this review is observationally oriented, it might be worth mentioning that models must also incorporate more realistic physics and chemistry and reach finer spatial and temporal resolutions, in concert with modern observations with state-of-the-art facilities.

Finally, jet-driven feedback is emerging as a critical factor in shaping planet-forming environments. Incorporating jet and outflow physics into planet formation models will be essential for developing a comprehensive picture of how planetary systems originate within evolving protostellar disks.

**Funding:** This research is independent and has no funding.

**Data Availability:** This review article has utilized the data from the lead authors cited in each Figure. The raw ALMA data is available on the ALMA archive as: ADS/JAO.ALMA#2018.1.00302.S. The data from the NASA/ESA/CSA James Webb Space Telescope presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. All the *JWST* data used in this paper can be found in MAST: <https://doi.org/10.17909/52vn-6191>.

**Acknowledgments:** We are thankful to the anonymous reviewers for their valuable suggestions, which helped to improve the overall quality of this review. S.D. thanks Chin-Fei Lee for discussion at various stages of my research since last few years and provide the facilitties for my jet/outflow research. I would like to thank “ALMASOP project" team for accessing ALMA data and discussion on various stages. S.D. acknowledges the facilities from the Academia Sinica Institute of Astronomy and Astrophysics, Taiwan.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00302.S (PI: Tie Liu). ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC, and ASIAA (Taiwan), as well as KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

This work utilizes observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with JWST GO Cycle 1 (Proposal ID: 1854; PI: Melissa McClure). All the *JWST* data used in this paper can be found in MAST: <https://doi.org/10.17909/52vn-6191>. During the preparation of this manuscript/study, the author(s) used CASA 5.4 (cite: 2007ASPC..376..127M), Astropy (cite: 2013A&A...558A..33A), matplotlib (cite: 2007CSE.....9...90H) for the purposes of plotting and analyses. The authors have reviewed and edited the output and take full responsibility for the content of this publication.

**Conflicts of Interest** The authors declare no conflicts of interest. This research has no funding. The funders had no role in the design of the study; in the collection, analyses, or interpretation of data; in the writing of the manuscript; or in the decision to publish the results.

999

(ref: 2001ARA&A..39..403R) Reipurth, B.; Bally, J. . **2001**, *39*, 403–455. .

(ref: 2007prpl.conf..245A) Arce, H.G.; Shepherd, D.; Gueth, F.; Lee, C.F.; Bachiller, R.; Rosen, A.; Beuther, H. . *arXiv* **2007**, arXiv:astro-ph/0603071. .

(ref: 2014prpl.conf..451F) Frank, A.; Ray, T.P.; Cabrit, S.; Hartigan, P.; Arce, H.G.; Bacciotti, F.; Bally, J.; Benisty, M.; Eislöffel, J.; Güdel, M.; et al. . In *Protostars and Planets VI*; 2014; pp. 451–474. .

(ref: 2014prpl.conf..387A) Audard, M.; Ábrahám, P.; Dunham, M.M.; Green, J.D.; Grosso, N.; Hamaguchi, K.; Kastner, J.H.; Kóspál, Á.; Lodato, G.; Romanova, M.M.; et al. . In *Protostars and Planets VI*; 2014; pp. 387–410. .

(ref: 2016ARA&A..54..491B) Bally, J. . **2016**, *54*, 491–528. .

(ref: 2020A&ARv..28....1L) Lee, C.F. . **2020**, *28*, 1. .

(ref: 2021NewAR..9301615R) Ray, T.P.; Ferreira, J. . **2021**, *93*, 101615. .

(ref: 2017NatAs...1E.152L) Lee, C.F.; Ho, P.T.P.; Li, Z.Y.; Hirano, N.; Zhang, Q.; Shang, H. . **2017**, *1*, 0152. .

(ref: 1994ApJ...429..781S) Shu, F.; Najita, J.; Ostriker, E.; Wilkin, F.; Ruden, S.; Lizano, S. . **1994**, *429*, 781. .

(ref: 2000prpl.conf..789S) Shu, F.H.; Najita, J.R.; Shang, H.; Li, Z.Y. ; ; pp. 789–814.

(ref: 2007prpl.conf..277P) Pudritz, R.E.; Ouyed, R.; Fendt, C.; Brandenburg, A. . In *Protostars and Planets V*; 2007; p. 277. .

(ref: 2020ApJ...905..116S) Shang, H.; Krasnopolsky, R.; Liu, C.F.; Wang, L.Y. . **2020**, *905*, 116. .

(ref: 2024AJ....167...72D) Dutta, S.; Lee, C.F.; Johnstone, D.; Lee, J.E.; Hirano, N.; Di Francesco, J.; Moraghan, A.; Liu, T.; Sahu, D.; Liu, S.Y.; et al. . **2024**, *167*, 72. .

(ref: 1951ApJ...113..697H) Herbig, G.H. **1951**, *113*, 697–699. .

(ref: 1952ApJ...115..572H) Haro, G. **1952**, *115*, 572. .

(ref: 1980ApJ...239L..17S) Snell, R.L.; Loren, R.B.; Plambeck, R.L. **1980**, *239*, L17–L22. .

(ref: 1992A&A...261..274C) Cabrit, S.; Bertout, C. **1992**, *261*, 274–284.

(ref: 1996A&A...311..858B) Bontemps, S.; Andre, P.; Terebey, S.; Cabrit, S. . **1996**, *311*, 858–872.

(ref: 2014ApJ...783...29D) Dunham, M.M.; Arce, H.G.; Mardones, D.; Lee, J.E.; Matthews, B.C.; Stutz, A.M.; Williams, J.P. . **2014**, *783*, 29. .

(ref: 2015A&A...576A.109Y) Yıldız, U.A.; Kristensen, L.E.; van Dishoeck, E.F.; Hogerheijde, M.R.; Karska, A.; Belloche, A.; Endo, A.; Frieswijk, W.; Güsten, R.; van Kempen, T.A.; et al. . **2015**, *576*, A109. .

(ref: 2021A&A...648A..45P) Podio, L.; Tabone, B.; Codella, C.; Gueth, F.; Maury, A.; Cabrit, S.; Lefloch, B.; Maret, S.; Belloche, A.; André, P.; et al. . **2021**, *648*, A45. .

(ref: 2025dutta) Dutta, S. . **2025**, *991*, 45. .

(ref: 1969MNRAS.145..271L) Larson, R.B. . **1969**, *145*, 271. .

(ref: 1998ApJ...502L.163T) Tomisaka, K. . **1998**, *502*, L163–L167. .

(ref: 2008ApJ...676.1088M) Machida, M.N.; Inutsuka, S.i.; Matsumoto, T. . **2008**, *676*, 1088–1108. .

(ref: 2013ApJ...763....6T) Tomida, K.; Tomisaka, K.; Matsumoto, T.; Hori, Y.; Okuzumi, S.; Machida, M.N.; Saigo, K. . **2013**, *763*, 6. .

(ref: 2023ApJ...951L..32H) Harsono, D.; Bjerkeli, P.; Ramsey, J.P.; Pontoppidan, K.M.; Kristensen, L.E.; Jørgensen, J.K.; Calcutt, H.; Li, Z.Y.; Plunkett, A. . **2023**, *951*, L32. .

(ref: 2023Natur.622...48R) Ray, T.P.; McCaughrean, M.J.; Caratti o Garatti, A.; Kavanagh, P.J.; Justtanont, K.; van Dishoeck, E.F.; Reitsma, M.; Beuther, H.; Francis, L.; Gieser, C.; et al. . **2023**, *622*, 48–52. .

(ref: 2024ApJ...962L..16N) Narang, M.; Manoj, P.; Tyagi, H.; Watson, D.M.; Megeath, S.T.; Federman, S.; Rubinstein, A.E.; Gutermuth, R.; Caratti o Garatti, A.; Beuther, H.; et al. . **2024**, *962*, L16. .

(ref: 2024A&A...687A..36T) Tychoniec, Ł.; van Gelder, M.L.; van Dishoeck, E.F.; Francis, L.; Rocha, W.R.M.; Caratti o Garatti, A.; Beuther, H.; Gieser, C.; Justtanont, K.; Linnartz, H.; et al. . **2024**, *687*, A36. .

(ref: 2024A&A...688A..26A) Assani, K.D.; Harsono, D.; Ramsey, J.P.; Li, Z.Y.; Bjerkeli, P.; Pontoppidan, K.M.; Tychoniec, Ł.; Calcutt, H.; Kristensen, L.E.; Jørgensen, J.K.; et al. . **2024**, *688*, A26. .

(ref: 2024A&A...691A.134C) Caratti o Garatti, A.; Ray, T.P.; Kavanagh, P.J.; McCaughrean, M.J.; Gieser, C.; Giannini, T.; van Dishoeck, E.F.; Justtanont, K.; van Gelder, M.L.; Francis, L.; et al. . **2024**, *691*, A134. .

(ref: 2025A&A...695A.145V) Vleugels, C.; McClure, M.; Sturm, A.; Vlasblom, M. . **2025**, *695*, A145. .

(ref: 2025ApJ...982..149O) Okoda, Y.; Yang, Y.L.; Evans, II, N.J.; Kim, J.; Jin, M.; Garrod, R.T.; Francis, L.; Johnstone, D.; Ceccarelli, C.; Codella, C.; et al. . **2025**, *982*, 149. .

(ref: 2025ApJ...985..225L) Le Gouellec, V.J.M.; Lew, B.W.P.; Greene, T.P.; Johnstone, D.; Gusdorf, A.; Francis, L.; DeWitt, C.; Meyer, M.; Tychoniec, Ł.; van Dishoeck, E.F.; et al. . **2025**, *985*, 225. .

(ref: 2025A&A...699A.361V) van Dishoeck, E.F.; Tychoniec, Ł.; Rocha, W.R.M.; Slavicinska, K.; Francis, L.; van Gelder, M.L.; Ray, T.P.; Beuther, H.; Caratti o Garatti, A.; Brunken, N.G.C.; et al. . **2025**, *699*, A361. .

(ref: 1995ApJ...452..736H) Hartigan, P.; Edwards, S.; Ghandour, L. . **1995**, *452*, 736. .

(ref: 2006A&A...459..821G) Giannini, T.; McCoey, C.; Nisini, B.; Cabrit, S.; Caratti o Garatti, A.; Calzoletti, L.; Flower, D.R. . **2006**, *459*, 821–835. .

(ref: 1998ApJ...492..743M) Muzerolle, J.; Calvet, N.; Hartmann, L. . **1998**, *492*, 743–753. .

(ref: 2007ApJ...665..492L) Lahuis, F.; van Dishoeck, E.F.; Blake, G.A.; Evans, II, N.J.; Kessler-Silacci, J.E.; Pontoppidan, K.M. . **2007**, *665*, 492–511. .

(ref: 2012A&A...545A..44P) Podio, L.; Kamp, I.; Flower, D.; Howard, C.; Sandell, G.; Mora, A.; Aresu, G.; Brittain, S.; Dent, W.R.F.; Pinte, C.; et al. . **2012**, *545*, A44. .

(ref: 2015Natur.527...70P) Plunkett, A.L.; Arce, H.G.; Mardones, D.; van Dokkum, P.; Dunham, M.M.; Fernández-López, M.; Gallardo, J.; Corder, S.A. . **2015**, *527*, 70–73. .

(ref: 2014ApJ...783....6V) Velusamy, T.; Langer, W.D.; Thompson, T. . **2014**, *783*, 6. .

(ref: 2017AJ....153..173H) Hsieh, T.H.; Lai, S.P.; Belloche, A. . **2017**, *153*, 173. .

(ref: 2008ApJ...675..427S) Seale, J.P.; Looney, L.W. . **2008**, *675*, 427–442. .

(ref: 2011ApJ...743...91O) Offner, S.S.R.; Lee, E.J.; Goodman, A.A.; Arce, H. . **2011**, *743*, 91. .

(ref: 1997IAUS..182..181H) Hollenbach, D. . *Symp. Int. Astron. Union.* **1997**, *182*, 181–198.

(ref: 1990ApJ...364..601R) Raga, A.C.; Canto, J.; Binette, L.; Calvet, N. . **1990**, *364*, 601. .

(ref: 2017A&A...597A.119T) Tafalla, M.; Su, Y.N.; Shang, H.; Johnstone, D.; Zhang, Q.; Santiago-Garcı́a, J.; Lee, C.F.; Hirano, N.; Wang, L.Y. . **2017**, *597*, A119. .

(ref: 2001ApJ...557..429L) Lee, C.F.; Stone, J.M.; Ostriker, E.C.; Mundy, L.G. . **2001**, *557*, 429–442. .

(ref: 2021ApJ...909...11J) Jhan, K.S.; Lee, C.F. . **2021**, *909*, 11. .

(ref: 1983ApJ...264..485D) Draine, B.T.; Roberge, W.G.; Dalgarno, A. **1983**, *264*, 485–507. .

(ref: 1997ApJ...487L..93B) Bachiller, R.; Pérez Gutiérrez, M. . **1997**, *487*, L93–L96. .

(ref: 2008A&A...490..695G) Gusdorf, A.; Pineau Des Forêts, G.; Cabrit, S.; Flower, D.R. . **2008**, *490*, 695–706. .

(ref: 2010A&A...522A..91T) Tafalla, M.; Santiago-Garcı́a, J.; Hacar, A.; Bachiller, R. . **2010**, *522*, A91. .

(ref: 1997A&A...321..293S) Schilke, P.; Walmsley, C.M.; Pineau des Forets, G.; Flower, D.R. **1997**, *321*, 293–304.

(ref: 1991ApJ...373..254G) Glassgold, A.E.; Mamon, G.A.; Huggins, P.J. . **1991**, *373*, 254. .

(ref: 1998ApJ...499..777B) Bergin, E.A.; Melnick, G.J.; Neufeld, D.A. . **1998**, *499*, 777–792. .

(ref: 2018Ap&SS.363..151N) Nesterenok, A.V. . **2018**, *363*, 151. .

(ref: 2008ApJ...681L..21A) Arce, H.G.; Santiago-Garcı́a, J.; Jørgensen, J.K.; Tafalla, M.; Bachiller, R. . **2008**, *681*, L21. .

(ref: 2015A&A...577A.102V) Visser, R.; Bergin, E.A.; Jørgensen, J.K. . **2015**, *577*, A102. .

(ref: 2021A&A...648A..24V) van Dishoeck, E.F.; Kristensen, L.E.; Mottram, J.C.; Benz, A.O.; Bergin, E.A.; Caselli, P.; Herpin, F.; Hogerheijde, M.R.; Johnstone, D.; Liseau, R.; et al. . **2021**, *648*, A24. .

(ref: 2002ApJ...576..222B) Bacciotti, F.; Ray, T.P.; Mundt, R.; Eislöffel, J.; Solf, J. . **2002**, *576*, 222–231. .

(ref: 2004ApJ...604..758C) Coffey, D.; Bacciotti, F.; Woitas, J.; Ray, T.P.; Eislöffel, J. . **2004**, *604*, 758–765. .

(ref: 2007ApJ...670.1188L) Lee, C.F.; Ho, P.T.P.; Palau, A.; Hirano, N.; Bourke, T.L.; Shang, H.; Zhang, Q. . **2007**, *670*, 1188–1197. .

(ref: 2003ApJ...590L.107A) Anderson, J.M.; Li, Z.Y.; Krasnopolsky, R.; Blandford, R.D. . **2003**, *590*, L107–L110. .

(ref: 2006A&A...453..785F) Ferreira, J.; Dougados, C.; Cabrit, S. **2006**, *453*, 785–796. .

(ref: 2005A&A...435..125S) Soker, N. . **2005**, *435*, 125–129. .

(ref: 2017NatAs...1E.146H) Hirota, T.; Machida, M.N.; Matsushita, Y.; Motogi, K.; Matsumoto, N.; Kim, M.K.; Burns, R.A.; Honma, M. . **2017**, *1*, 0146. .

(ref: 2009A&A...494..147L) Launhardt, R.; Pavlyuchenkov, Y.; Gueth, F.; Chen, X.; Dutrey, A.; Guilloteau, S.; Henning, T.; Piétu, V.; Schreyer, K.; Semenov, D. . **2009**, *494*, 147–156. .

(ref: 2021ApJ...907L..41L) Lee, C.F.; Tabone, B.; Cabrit, S.; Codella, C.; Podio, L.; Ferreira, J.; Jacquemin-Ide, J. . **2021**, *907*, L41. .

(ref: 2024ApJ...977..126L) López-Vázquez, J.A.; Lee, C.F.; Shang, H.; Cabrit, S.; Krasnopolsky, R.; Codella, C.; Liu, C.F.; Podio, L.; Dutta, S.; Murphy, A.; et al. . **2024**, *977*, 126. .

(ref: 2007A&A...468L..29C) Cabrit, S.; Codella, C.; Gueth, F.; Nisini, B.; Gusdorf, A.; Dougados, C.; Bacciotti, F. . **2007**, *468*, L29–L32. .

(ref: 2005A&A...441..159N) Nisini, B.; Bacciotti, F.; Giannini, T.; Massi, F.; Eislöffel, J.; Podio, L.; Ray, T.P. . **2005**, *441*, 159–170. .

(ref: 2013ApJ...778...71G) Giannini, T.; Nisini, B.; Antoniucci, S.; Alcalá, J.M.; Bacciotti, F.; Bonito, R.; Podio, L.; Stelzer, B.; Whelan, E.T. . **2013**, *778*, 71. .

(ref: 2013A&A...551A...5E) Ellerbroek, L.E.; Podio, L.; Kaper, L.; Sana, H.; Huppenkothen, D.; de Koter, A.; Monaco, L. . **2013**, *551*, A5. .

(ref: 2024A&A...692A.143B) Birney, M.; Dougados, C.; Whelan, E.T.; Nisini, B.; Cabrit, S.; Zhang, Y. . **2024**, *692*, A143. .

(ref: 2024ApJ...966...41F) Federman, S.A.; Megeath, S.T.; Rubinstein, A.E.; Gutermuth, R.; Narang, M.; Tyagi, H.; Manoj, P.; Anglada, G.; Atnagulov, P.; Beuther, H.; et al. . **2024**, *966*, 41. .

(ref: 2007ApJ...668L..27K) Kovalev, Y.Y.; Lister, M.L.; Homan, D.C.; Kellermann, K.I. . **2007**, *668*, L27–L30. .

(ref: 2007ApJ...658..232C) Cohen, M.H.; Lister, M.L.; Homan, D.C.; Kadler, M.; Kellermann, K.I.; Kovalev, Y.Y.; Vermeulen, R.C. . **2007**, *658*, 232–244. .

(ref: 2003ApJ...599..363A) Allen, A.; Li, Z.Y.; Shu, F.H. . **2003**, *599*, 363–379. .

(ref: 2025ApJ...988..107T) Tu, Y.; Li, Z.Y.; Zhu, Z.; Hsu, C.Y.; Hu, X. . **2025**, *988*, 107. .

(ref: 2025arXiv250611333T) Tu, Y.; Li, Z.Y.; Zhu, Z.; Hu, X.; Hsu, C.Y. . **2025**, arXiv:2506.11333. .

(ref: 2014A&A...563A..87E) Ellerbroek, L.E.; Podio, L.; Dougados, C.; Cabrit, S.; Sitko, M.L.; Sana, H.; Kaper, L.; de Koter, A.; Klaassen, P.D.; Mulders, G.D.; et al. . **2014**, *563*, A87. .

(ref: 2015ApJ...805..186L) Lee, C.F.; Hirano, N.; Zhang, Q.; Shang, H.; Ho, P.T.P.; Mizuno, Y. . **2015**, *805*, 186. .

(ref: 2015ApJ...805..115V) Vorobyov, E.I.; Basu, S. . **2015**, *805*, 115. .

(ref: 2002ApJ...580..950M) Masciadri, E.; de Gouveia Dal Pino, E.M.; Raga, A.C.; Noriega-Crespo, A. . **2002**, *580*, 950–958. .

(ref: 2010ApJ...713..731L) Lee, C.F.; Hasegawa, T.I.; Hirano, N.; Palau, A.; Shang, H.; Ho, P.T.P.; Zhang, Q. . **2010**, *713*, 731–737. .

(ref: 2023ASPC..534..355F) Fischer, W.J.; Hillenbrand, L.A.; Herczeg, G.J.; Johnstone, D.; Kospal, A.; Dunham, M.M. . *arXiv* **2023**, arXiv:2203.11257. .

(ref: 2023ApJ...944...49F) Federman, S.; Megeath, S.T.; Tobin, J.J.; Sheehan, P.D.; Pokhrel, R.; Habel, N.; Stutz, A.M.; Fischer, W.J.; Hartmann, L.; Stanke, T.; et al. . **2023**, *944*, 49. .

(ref: 1998Natur.394..862Z) Zinnecker, H.; McCaughrean, M.J.; Rayner, J.T. . **1998**, *394*, 862–865. .

(ref: 2002A&A...395..647R) Raga, A.C.; Velázquez, P.F.; Cantó, J.; Masciadri, E. . **2002**, *395*, 647–656. .

(ref: 2017ApJ...849...43H) Herczeg, G.J.; Johnstone, D.; Mairs, S.; Hatchell, J.; Lee, J.E.; Bower, G.C.; Chen, H.R.V.; Aikawa, Y.; Yoo, H.; Kang, S.J.; et al. . **2017**, *849*, 43. .

(ref: 2021ApJ...920..119L) Lee, Y.H.; Johnstone, D.; Lee, J.E.; Herczeg, G.; Mairs, S.; Contreras-Peña, C.; Hatchell, J.; Naylor, T.; Bell, G.S.; Bourke, T.L.; et al. . **2021**, *920*, 119. .

(ref: 2021ApJ...920..132P) Park, W.; Lee, J.E.; Contreras Peña, C.; Johnstone, D.; Herczeg, G.; Lee, S.; Lee, S.; Bhardwaj, A.; Moriarty-Schieven, G.H. . **2021**, *920*, 132. .

(ref: 1982MNRAS.199..883B) Blandford, R.D.; Payne, D.G. **1982**, *199*, 883–903. .

(ref: 2016Natur.540..406B) Bjerkeli, P.; van der Wiel, M.H.D.; Harsono, D.; Ramsey, J.P.; Jørgensen, J.K. . **2016**, *540*, 406–409. .

(ref: 2020A&A...640A..82T) Tabone, B.; Cabrit, S.; Pineau des Forêts, G.; Ferreira, J.; Gusdorf, A.; Podio, L.; Bianchi, E.; Chapillon, E.; Codella, C.; Gueth, F. . **2020**, *640*, A82. .

(ref: 2007prpl.conf..261S) Shang, H.; Li, Z.Y.; Hirano, N. . *Protostars Planets V* **2007**, 261.

(ref: 2021ApJ...913..122R) Ricci, L.; Harter, S.K.; Ercolano, B.; Weber, M. . **2021**, *913*, 122. .

(ref: 2025ApJ...986..161H) Hu, X.; Bae, J.; Zhu, Z.; Wang, L. . **2025**, *986*, 161. .

(ref: 2005ApJ...632L.135M) Matt, S.; Pudritz, R.E. . **2005**, *632*, L135–L138. .

(ref: 2022ApJ...936L..14P) Pontoppidan, K.M.; Barrientes, J.; Blome, C.; Braun, H.; Brown, M.; Carruthers, M.; Coe, D.; DePasquale, J.; Espinoza, N.; Marin, M.G.; et al. . **2022**, *936*, L14. .

(ref: 2016ApJ...821...80B) Bai, X.N. . **2016**, *821*, 80. .

(ref: 2021ApJ...915...90N) Nakatani, R.; Kobayashi, H.; Kuiper, R.; Nomura, H.; Aikawa, Y. . **2021**, *915*, 90. .

(ref: 2007ASPC..376..127M) McMullin, J.P.; Waters, B.; Schiebel, D.; Young, W.; Golap, K. . In *Proceedings of the Astronomical Data Analysis Software and Systems XVI*; ASP Conference Series; Shaw, R.A., Hill, F., Bell, D.J., Eds.; 2007; Volume 376, p. 127.

(ref: 2013A&A...558A..33A) Astropy Collaboration.; Robitaille, T.P.; Tollerud, E.J.; Greenfield, P.; Droettboom, M.; Bray, E.; Aldcroft, T.; Davis, M.; Ginsburg, A.; Price-Whelan, A.M.; et al. . **2013**, *558*, A33. .

(ref: 2007CSE.....9...90H) Hunter, J.D. . **2007**, *9*, 90–95. .

[^1]: Corresponding author: sdutta@asiaa.sinica.edu.tw

</paper>

Write the methods card for this paper.