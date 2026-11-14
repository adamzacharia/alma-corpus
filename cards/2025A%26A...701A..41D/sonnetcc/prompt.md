# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A..41D\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...701A..41D",
 "title": "Millimeter emission from supermassive black hole coronae",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "del Palacio, S.",
 "n_authors": 31,
 "arxiv_id": "2504.07762",
 "doi": "10.1051/0004-6361/202554936",
 "alma_projects_linked_by_archive": [
  "2015.1.01047.S",
  "2017.1.00236.S",
  "2019.1.00618.S",
  "2019.1.01230.S",
  "2021.1.00812.S",
  "2023.1.00121.S"
 ]
}
```

Paper text:
<paper>
# Millimeter emission from supermassive black hole coronae

Active Galactic Nuclei (AGN) host accreting supermassive black holes (SMBHs). The accretion process can lead to the formation of a hot, X-ray emitting corona close to the SMBH capable of accelerating relativistic electrons. Observations in the millimetre band can probe its synchrotron emission.

We intend to provide a framework to derive physical information of SMBH coronae by modelling their spectral energy distribution (SED) from radio to far infrared frequencies. We also explore the possibilities of deriving additional information from millimetre observations, such as the SMBH mass, and studying high-redshift lensed sources.

We introduce a corona emission model based on a one-zone spherical region with a hybrid thermal and non-thermal plasma. We investigate in detail how the corona SED depends on different parameters such as size, opacity, and magnetic field strength. Other galactic emission components from dust, ionised gas and diffuse relativistic electrons are also included in the SED fitting scheme. We apply our code consistently to a sample of radio-quiet AGN with strong indications of a coronal component in the millimetre.

The detected millimetre emission from SMBH coronae is consistent with having a non-thermal relativistic particle population with an energy density that is $\approx$0.5–10% of that in the thermal plasma. This requires magnetic energy densities close to equipartition with the thermal gas, and corona sizes of 60–250 gravitational radii. The model can also reproduce the observed correlation between millimetre emission and SMBH mass when accounting for uncertainties in the corona size.

The millimetre band offers a unique window into the physics of SMBH coronae, enabling the study of highly dust-obscured sources and high-redshift lensed quasars. Gaining a deeper understanding of the relativistic particle population in SMBH coronae can provide key insights into their potential multiwavelength and neutrino emission.

# Introduction

An Active Galactic Nucleus (AGN) is produced when a supermassive black hole (SMBH) accretes matter from its surrounding medium. The material around an SMBH is pulled by the strong gravitational field and spirals inward, forming an accretion disc. Processes related to turbulent magnetic viscosity in the accretion disc cause the material to lose angular momentum and fall towards the SMBH, releasing huge amounts of gravitational energy. The material then heats up, and radiates across a broad range of wavelengths (cite: Balbus1998). The accretion process is very efficient in converting gravitational potential energy into other forms, such as radiation, magnetic fields, and particle acceleration. Moreover, close to the innermost regions of the accretion disc, magnetic reconnection events can heat the gas to extremely high temperatures ($\sim$10$^9$ K), giving rise to a compact, hot region known as the corona (cite: Haardt1991; Kamraj2022).

Most ($\sim$90%) AGN emit only weakly at radio wavelengths and are therefore classified as radio-quiet (RQ). Although these AGNs lack a powerful radio jet (cite: Urry1995), radio emission at 22 GHz is commonly detected (cite: Smith2020; Magno2025). Interestingly, millimetre (mm) emission is also frequently observed in nearby RQ AGN, with most of the mm continuum flux originating from an unresolved core. Several studies have argued that this radiation is synchrotron emission produced in the corona, which also produces the hard X-ray emission above 2 keV through inverse Compton scattering of thermal disc photons, ubiquitously observed in AGN (cite: Laor2008; Inoue2014; Behar2018; Panessa2019). Recent studies strongly support this interpretation: high-resolution ($\sim$0.1–1") ALMA observations of nearby AGN revealed a tight correlation between X-ray emission and mm continuum at $\sim$200 GHz (cite: Kawamuro2022) and at $\sim$100 GHz (cite: Ricci2023), as well as a correlation between the SMBH mass and the mm flux density at $\sim$230 GHz (cite: Ruffa2024). In addition, correlated variability of X-ray and mm emission on year-timescales was found in NGC 1566 (cite: Jana2025). Together, these results support the idea that the corona plays a key role in the mm emission from RQ AGN.

The X-ray corona is expected to be very compact, $r_\mathrm{c} = R_\mathrm{c}/R_\mathrm{g} \sim 10$–50, where $R_\mathrm{g} = G M_\mathrm{BH} /c^2$ is the gravitational radius and $M_\mathrm{BH}$ the mass of the SMBH (cite: Fabian2015; Inoue2018). Nonetheless, the size of the corona is a topic of debate, with spectrotiming analysis of X-ray emission in Galactic X-ray binaries (XRBs) favouring dynamical coronae that vary in size from tens to hundreds of $R_\mathrm{g}$ (cite: Karpouzas2021). Even the geometry of the corona (lamp post, toroidal, spherical, sandwich-like) is unknown (cite: Bambi2021). Models for dynamical, outflowing coronae with sizes $r_c \sim 10$–$1000$ have also been suggested in the context of XRBs (cite: Kylafis2023); this is remarkably consistent with the results of mm variability in the RQ AGN IC 4329A(cite: Shablovinskaya2024). On the topic of variability, we also highlight the results by (cite: Petrucci2023) showing rapid variability in mm and X-ray emission from MCG+08$-$11$-$11 within a day, and by (cite: Michiyama2024) revealing mm variability in a few days in GRS 1734$-$292. The fast variability strongly supports that the mm emission comes from a compact region of $r_\mathrm{c} \sim 20$–$400$. Altogether, this shows that the size of the corona remains a topic of debate.

In addition, the presence of ultra-relativistic particles in coronae is supported by both theoretical and observational evidence. Magnetic reconnection events, as well as other processes related to internal shocks and/or turbulence, can be responsible for accelerating relativistic particles out of thermal equilibrium (cite: Inoue2008; Beloborodov2017; Sironi2020; Groselj2024; Nattila2024). In the case of a corona, the presence of extremely hot gas ($kT > 100$ keV) leads to the co-existence of both thermal and non-thermal relativistic particles (cite: Ozel2000), which we refer to as a ‘hybrid’ plasma. Another independent proof of a non-thermal electron population in the corona is the hard X-ray/soft gamma-ray tail detected in the XRBs Cyg X-1 (cite: Zdziarski2021) and MAXI J1820+070 (cite: Cangemi2021). A scenario involving (hadronic) cosmic rays in the corona is also compatible with the MeV polarised emission detected in Cyg X-1 (cite: Romero2014), and possibly with its sub-GeV and TeV emission (cite: Fang2024). In addition, $\gamma$-ray emission in the 1–300 GeV energy range was detected in the stacked signal of 37 RQ AGN, which was interpreted to be produced in extended coronae (cite: Fermi2025). Furthermore, several studies have suggested that significant neutrino emission can be produced by cosmic rays in SMBH coronae (cite: Inoue2019; Murase2020; Kun2024; Fang2024), consistent with the neutrino emission from NGC 1068 (cite: Inoue2020; Eichmann2022). This scenario is particularly attractive because it can account for gamma-ray luminosity orders of magnitude lower than the neutrino luminosity, as the corona environment produces strong gamma-gamma absorption.

A relatively new window to study SMBH corona is in the mm atmospheric bands. The relativistic electrons in the corona interact with the local magnetic fields and emit synchrotron radiation with a spectral energy distribution (SED) that peaks at around 100–300 GHz, depending on the plasma conditions in the corona and its non-thermal particle content (cite: Inoue2014; Inoue2019). Although corona properties such as temperature and optical depth can be derived from X-ray observations (cite: Fabian2015; Ricci2018), the magnetic field strength and non-thermal particle population content can only be inferred by modelling the mm emission (cite: Inoue2018).

Here, we present a framework for modelling the SEDs of RQ AGN. We pay special attention to the synchrotron emission from AGN coronae and its dependence on different physical parameters. We then apply this model consistently to a sample of objects for which good spectral coverage is available in order to derive the most relevant parameters of the coronae.

# Emission model

The nuclear region of an RQ galaxy (inner $\sim$100 pc) can contain large reservoirs of ionised gas, dust, cosmic rays, and an AGN. Thus, the observed continuum radio-to-submm SED of an RQ galaxy is the combination of several contributions, each with a distinct shape. We assume that these components are independent of each other and that the total emission is simply the sum of all components. The most relevant SED components that we consider are[^1]:

1.  **Ionised gas:** The warm, ionised gas in the galaxy emits free–free (f–f) radiation that can be relevant at frequencies between $\sim 10$–100 GHz, where it presents a spectral index $\alpha=-0.1$ (cite: Murphy2018). The intensity of this emission is expected to scale with the amount of ionised gas and thus the star formation rate (cite: Murphy2011). In the simplest case, this emission can be parameterised as: $$\begin{equation}
        \centering
            S_\mathrm{ff}(\nu) = A_\mathrm{ff} \, \left( \dfrac{\nu}{\nu_0} \right)^{-0.1} \,, 
            \label{eq:ff}
        
    \end{equation}$$ where $A_\mathrm{ff}$ is a normalisation constant and $\nu_0$ is a reference frequency (fixed at 100 GHz). We note that, at low frequencies, this emission can actually drop as the medium becomes optically thick ($\alpha=2$ instead of $-$0.1). The turnover frequency depends most strongly on the density of the medium but also on its structure (cite: Ramirez-Olivencia2022)

2.  **A diffuse cosmic-ray electron population:** Its origin is likely related to the SFR, where supernova remnants and winds from massive stars accelerate cosmic rays that diffuse in the galaxy (cite: Lacki2010; Kornecki2022), or to extended jets (cite: Urry1995). This component produces optically-thin synchrotron emission with a steep spectral index between $-0.5$ and $-1$ (cite: Heesen2022; An2024), dominating at low frequencies in the radio-cm range ($\lesssim 10$ GHz). In the simplest case, this emission can be parameterised as: $$\begin{equation}
        \centering
            S_\mathrm{sy}(\nu) = A_\mathrm{sy} \, \left( \dfrac{\nu}{\nu_0} \right)^{\alpha_\mathrm{sy}} \,, 
            \label{eq:sy}
        
    \end{equation}$$ where $A_\mathrm{sy}$ is a normalisation constant, $\nu_0$ is a reference frequency (fixed at 100 GHz), and $\alpha_\mathrm{sy}$ is the intrinsic spectral index of the synchrotron emission. At low frequencies, the behaviour of this component can deviate from a simple power-law, most likely due to f–f absorption in the ionised gas that flattens the spectrum at lower frequencies (cite: Kornecki2022; Dey2024), consistent with what is observed in studies at $\nu < 1$ GHz of a large sample of galaxies (cite: Heesen2022; An2024). If the ionised medium is inhomogeneous and clumpy, the absorption depends on the opacity and distribution of the clumps. This can result in significant absorption of the synchrotron emission, but also part of it can propagate between the clumps unaffected (cite: Lacki2013; Ramirez-Olivencia2022). We refrain from including such effects in our model as it would introduce additional free parameters that do not assist us in our main goal, which is to isolate and study the corona component that peaks at much higher frequencies.

3.  **Corona:** The intrinsic synchrotron SED is a power-law with a negative spectral index ($\alpha \sim -0.5$ to $-1$), but lower frequency radiation is absorbed by the relativistic electrons via synchrotron-self absorption (SSA), producing a turnover in the SED that shifts to a positive spectral index $\alpha = 5/2$ (cite: Margalit2021). The position of the turnover frequency, $\nu_\mathrm{SSA} \approx 100$–300 GHz, depends on the plasma conditions in the corona, such as its density, size, and magnetic field strength (see forthcoming Sect. [3.1](#sec:parameter_exploration)). This results in an SED with a rather pronounced peak at $\nu \sim \nu_\mathrm{SSA}$. As the main goal of this work is to derive the physical properties of the corona, in this case, we do not adopt a simple phenomenological model but rather compute the SED in a physically motivated way, detailed in Sect. [2.1](#sec:corona_model). We highlight that this region is extremely compact and can exhibit very high brightness temperatures (potentially up to $\sim10^9$ K if observed with a 10 $\mu$as resolution at 100 GHz, adopting as reference a flux density of $\sim$1 mJy).

4.  **Dust:** Its continuum emission dominates the SED at high frequencies ($\gtrsim 300$ GHz, depending on the source and the angular resolution of the observations). Within the Rayleigh-Jeans regime, this can be modelled as a modified-black body spectrum characterised by the frequency $\nu_{\tau_{1}}$ at which the dust opacity becomes equal to unity, and the index $\beta$ of the opacity coefficient $\kappa_\nu \propto \nu^\beta$ (with $\beta \approx 1$–2). At $\nu < \nu_{\tau_{1}}$ the SED is optically thin and has a spectral index $\alpha = 2+\beta$, while at $\nu > \nu_{\tau_{1}}$ it is optically thick and $\alpha = 2$. This is parameterised as: $$\begin{equation}
            S_\mathrm{d} = A_\mathrm{d} \, \left( \dfrac{\nu}{\nu_0} \right)^2 \, \left( 1 - e^{-\tau_\mathrm{d}} \right) \,, 
            \label{eq:dust}
        
    \end{equation}$$ where $A_\mathrm{d}$ is a normalisation constant, $\nu_0$ is a reference frequency (fixed at 100 GHz), and $\tau_\mathrm{d} = (\nu/\nu_{\tau_{1}})^\beta$. We note that the dust mass is $M_\mathrm{d} \propto \nu_{\tau_{1}}$ (cite: Draine2011), so that an accurate determination of $\nu_{\tau_{1}}$ can help to estimate dust masses, although this would typically require a good spectral coverage between 400–1 000 GHz that is challenging to obtain. We also note that, at the frequencies at which the dust becomes optically thick, it could also absorb the emission from the corona. However, this would depend on geometrical assumptions regarding the dust distribution along the line of sight, and it would only affect the optically thin part of the corona SED, which is difficult to observe as it is expected to be faint and typically below the dust continuum emission. We thus neglect this effect in our model fitting. In addition, rapidly spinning dust grains can produce Anomalous Microwave Emission (AME) that peaks around $\nu \sim 30$ GHz, although in certain conditions, it can reach $\sim$100 GHz (cite: Dickinson2018; Murphy2020). However, this component is faint and, in extragalactic contexts, it has only been detected in off-nuclear star-forming regions in a handful of nearby galaxies (cite: Poojon2024; Fernandez-Torreiro2024). It is thus unlikely that this component is bright in the sources of our sample, which in fact do not present a bump in their SED at (rest-frame) frequencies of $\sim$30 GHz (Sect. [3](#sec:results)). For this reason, we do not include an AME emission component in our model.

## Corona emission

We developed a corona emission model based on the one-zone model presented by (cite: Inoue2019), in which the corona is a hybrid plasma with a thermal and a non-thermal particle population. We therefore use the numerical code from (cite: Margalit2021)[^2] that computes the synchrotron SED of a hybrid plasma. We model the corona as a spherical region of size $R_\mathrm{c} = r_\mathrm{c} R_\mathrm{g}$, with $R_\mathrm{g}$ the gravitational radius and $r_\mathrm{c}$ an adimensional radius. The thermal plasma is characterised by its temperature $T_\mathrm{c}$ and number density $n_\mathrm{th,0}$. The latter is parameterised through the Thomson opacity $\tau_\mathrm{T}$ as $n_\mathrm{th,0} = \tau_\mathrm{T}/(\sigma_\mathrm{T}  R_\mathrm{c})$. The energy density in thermal electrons is $U_\mathrm{th,e} = a(\Theta) \, \Theta \, n_\mathrm{th,0} \, m_\mathrm{e} c^2$, where is $\Theta = k T_\mathrm{c} / (m_\mathrm{e} c^2)$ is an adimensional temperature and $a(\Theta) = (6 + 15\Theta)/(4 + 5\Theta)$ (cite: Margalit2021).

Following (cite: Margalit2021), for the non-thermal population we define a minimum Lorentz factor $\gamma_\mathrm{min}(\Theta) = 1+a(\Theta)\,\Theta$, such that at energies above $E_\mathrm{min} = \gamma_\mathrm{min} m_\mathrm{e} c^2$ the particle energy distribution is:

$$\begin{equation}
N(E) \propto \begin{cases}
    E^{-p+1}, \quad t_\mathrm{sy} \leq t_\mathrm{dyn} \\
    E^{-p}, \quad t_\mathrm{sy} > t_\mathrm{dyn} \end{cases} .   
\end{equation}$$

Here, $p$ is the spectral index of the electron distribution without cooling, $t_\mathrm{dyn}$ is the characteristic dynamical timescale for which we adopt the free-fall time $t_\mathrm{dyn}=R_\mathrm{c}/v_\mathrm{ff}$ (cite: Inoue2019), and $t_\mathrm{sy}$ is the synchrotron cooling timescale. We highlight that the values of $t_\mathrm{sy}$ and $t_\mathrm{dyn}$ are calculated self-consistently in the model for any given set of parameters ($M_\mathrm{BH}$, $r_\mathrm{c}$, etc.).

The next step is to define the non-thermal electron population in the corona and the magnetic field. For this, additional free parameters have to be introduced. One sensible way to do this is to use the energy density in thermal electrons as a reference. We define the ratio between the energy densities in the magnetic field and thermal electrons $\epsilon_B = U_B/U_\mathrm{th,e}$, and the ratio between the energy density in non-thermal electrons and thermal electrons $\delta = U_\mathrm{nt,e}/U_\mathrm{th,e}$. To constrain the model further, we assume $\delta < 1$, as otherwise the non-thermal electrons would dominate in the corona, which does not seem to be the case (cite: Zdziarski2021); we further note that (cite: Inoue2018) fixed this parameter to 0.04. Another consideration is that magnetic fields are believed to play a major role in heating the corona and accelerating relativistic particles (cite: Beloborodov2017; Sironi2020), and therefore it should be the case that $\epsilon_B$ is of order unity and $\epsilon_B > \delta$. We can thus impose an energy condition $U_B = \eta U_\mathrm{nt}$, where $U_\mathrm{nt}$ is the total energy in non-thermal particles. It is usual to write this as $U_\mathrm{nt} = U_\mathrm{nt,e} + U_\mathrm{nt,p} = (1 + \xi_\mathrm{e,p}) \, U_\mathrm{nt,e}$, where $\xi_\mathrm{e,p}$ is the ratio between the energy density in relativistic protons and electrons. With these definitions, we can rewrite $\epsilon_B = \eta \, \delta \, ( 1+\xi_\mathrm{e,p})$. Either because relativistic protons are easier to accelerate or because relativistic electrons cool faster than protons, the energy density in non-thermal protons is larger than that of electrons (cite: Eichmann2022), and therefore we fix $\xi_\mathrm{e,p}=40$ (cite: Merten2017). We additionally fix $\eta=1$, corresponding to an energy equipartition condition between non-thermal particles and magnetic fields. In this way, we remove a free parameter by the condition $\epsilon_B = 41 \, \delta$.

A related parameter commonly used to characterise the plasma conditions is the $\sigma$ parameter defined as $\sigma = B^2 / (4\pi n_\mathrm{th,e} m_\mathrm{e} c^2)$. Neglecting some factors of order unity, one can approximate $\sigma \approx \epsilon_B \, \Theta$, which helps to understand the dependence of $\sigma$ on the model parameters. In particular, for a highly magnetised plasma, one expects $\sigma$ to be of the order of unity. Similarly, this can be compared with the plasma $\beta_B$ parameter defined as the ratio of thermal and magnetic pressures, $\beta_B = P_\mathrm{th}/P_B$, which can be rewritten as[^3] $\beta_B \sim 5/\epsilon_B$.

Once the thermal and non-thermal particle populations have been defined, together with the physical properties of the corona, the code calculates the synchrotron SED, taking into account the emissivity and opacity (SSA) from both populations. In this way, the synchrotron SED (including $\nu_\mathrm{SSA}$) is self-consistently calculated for any set of parameters.

We finally convert the specific luminosities to flux densities in order to compare them with observed SEDs. For this, we use the `Planck18` library available in `astropy` to convert $z$ to a luminosity distance, and the rest-frame frequencies to the observed frame as $\nu_\mathrm{obs}=\nu/(1+z)$. Finally, for studying lensed sources (as explored in Sect. [3.2](#sec:high_z)), we introduce a multiplicative amplification factor $\mu$ to the intrinsic luminosity.

| Parameter (units) | Symbol | Values | Comments |
|:---|:--:|:--:|:--:|
| Redshift of the source | $z$ | $>0$ | Fixed to the literature value |
| Normalisation of the f–f component | $A_\mathrm{ff}$ | \[$10^{-3}$, $10^{1}$\] | Defined in Eq. [\[eq:ff\]](#eq:ff) |
| Normalisation of the diffuse synchrotron component | $A_\mathrm{sy}$ | \[$10^{-3}$, $10^{1}$\] | Defined in Eq. [\[eq:sy\]](#eq:sy) |
| Spectral index of the diffuse synchrotron component | $\alpha_\mathrm{sy}$ | \[$-2$, $-0.45$\] | Defined in Eq. [\[eq:sy\]](#eq:sy) |
| Normalisation of the dust component | $A_\mathrm{d}$ | \[$10^{-3}$, $10^{1}$\] | Defined in Eq. [\[eq:dust\]](#eq:dust) |
| Dust opacity index | $\beta$ | \[1, 2\] | Defined in Eq. [\[eq:dust\]](#eq:dust). Default value: 1.78 |
| Frequency at which $\tau_\mathrm{d} = 1$ (GHz) | $\nu_{\tau_1}$ | \[300, 1300\] | Defined in Eq. [\[eq:dust\]](#eq:dust). Default value: 700 |
| Mass of the supermassive black hole | $M_\mathrm{BH}$ | \[$10^{6}$, $10^{9}$\] | $\dagger$ |
| Corona radius ($r_g$) | $r_\mathrm{c}$ | \[10, 500\] |  |
| Corona temperature (keV) | $k\,T_\mathrm{c}$ | \[10, 200\] | Default value: 166$^\dagger$ |
| Corona Thomson opacity | $\tau_\mathrm{T}$ | \[0.01, 10.0\] | Default value: 0.25$^\dagger$ |
| Ratio of non-thermal particle energy density in the corona | $\delta$ | \[$10^{-4}$, $10^{0}$\] |  |
| Spectral index of the injected non-thermal particles | $p$ | (2, 4\] | Default value: 2.7 |
| Magnetic field energy density in the corona | $\epsilon_B$ | \[$10^{-3}$, $10^{1}$\] | Default value: $41\,\delta$ |

## Parameter fitting

![](Figures/corona_seds_many-parameters.pdf)

We developed a code[^4] that calculates the total SED from the physical coronal model, together with the phenomenological components described in Sect. [2](#sec:model). We use the Python package `Bilby` (cite: bilby) for fitting the SED using the standard sampler for Markov Chain Monte Carlo `emcee` (cite: emcee). One key issue is dealing with observations with different angular resolutions. The corona is extremely compact, so its emission should be point-like in all observations. The other galactic components are most likely extended and inhomogeneous, so it is not possible to scale the observed flux density with the beam size in a reliable way. For this reason, we use beam-matched data whenever possible, even if that requires compromising angular resolution. The main drawback is that the corona emission is not very bright, and so it can be well below the continuum of other galactic components in observations with poor angular resolution that collect too much diffuse emission, making it undetectable. For this reason, we filter out observations with coarse angular resolution (typically $> 1"$, corresponding to linear scales $>$100 pc for galaxies at distances beyond 20 Mpc) and consider them only as strict upper limits (ULs) for the total flux density. Similarly, when it comes to observations with significantly higher angular resolution than the rest of the dataset (e.g., from very large baseline interferometry—VLBI), we consider them only as strict lower limits (LLs) of the total flux density. In both cases, we leave a 1-$\sigma$ margin to be more conservative about using points as strict ULs or LLs, that is, for a measured flux of $S_\nu \pm \Delta S_\nu$, we choose $S_\mathrm{UL} = S_\nu + \Delta S_\nu$ and $S_\mathrm{LL} = S_\nu - \Delta S_\nu$.

To reduce the number of free parameters in the model, we can use the parameterisation for $\epsilon_B(\delta)$ described in Sect. [2.1](#sec:corona_model). In addition, in cases where there is no direct determination of $\tau_\mathrm{T}$ and $T_\mathrm{c}$ from X-ray data, we adopt the parameterisation for $T_\mathrm{c}(\tau_\mathrm{T})$ from (cite: Tortosa2018). As a reference, this corresponds to $kT_\mathrm{c}\simeq 166$ keV for the most typical case of $\tau_\mathrm{T} \simeq 0.25$ (cite: Ricci2018), while for $\tau_\mathrm{T} \simeq 1$ we get $kT_\mathrm{c}\simeq 63$ keV. We summarise all the model parameters and the range of values that they can take in Table [\[table:parameters\]](#table:parameters). We note that for quantities that can span several orders of magnitude, we fit the logarithm of the quantity.

This code has already been used to model the SEDs of IC 4329A(cite: Shablovinskaya2024) and NGC 1068 (cite: Mutie2025). As a sanity check, we verified that the sizes derived with this approach agree well with the simple analytical estimate from Eq. 4 in (cite: Shablovinskaya2024). Additionally, we confirmed that our results are consistent with those reported by (cite: Inoue2018) when fixing the same parameters as in their work.

Throughout this work, the quoted errorbars correspond to the 16th–84th percentile range (the $1\sigma$ confidence intervals for Gaussian distributions) and are derived from the posterior distribution. We also assume a conservative flux uncertainty to account for systematic errors in absolute flux calibrations, such that the total errorbar is $\Delta S_\nu = \sqrt{\Delta S_\mathrm{sta}^2 + \Delta S_\mathrm{sys}^2}$, with $\Delta S_\mathrm{sta}$ the statistical uncertainty and $\Delta S_\mathrm{sys} = f_\mathrm{sys}\,S_\nu$ the assumed systematic error. The factor $f_\mathrm{sys}$ is fixed to 5% for all observations, except for ALMA observations at B6–8 (212–500 GHz) and B9–10 (600–900 GHz), for which it is 10% and 20%, respectively[^5].

# Results

## Parameter exploration

We explore the corona SED response to the different model parameters in order to gain some intuition of the interpretation of the observed SEDs. For this we consider a reference case with the following parameters: $D = 100$ Mpc, $M_\mathrm{BH} = 10^8$ M$_\odot$, $\tau_\mathrm{T}=0.25$, $kT_\mathrm{c}=166$ keV, $r_\mathrm{c}=140$, $\epsilon_B=1.0$, $\delta=0.01$, and $p=2.7$. First, we vary one parameter at a time. The results are shown in Fig. [1](#fig:corona_seds). Some highlights are:

- Higher $\delta$ values mean more relativistic electrons and, therefore, lead to a higher emission and a higher opacity. Below $\nu_\mathrm{SSA}$ the emission is optically thick, so that a larger number of non-thermal electrons does not increase the flux, which remains constant for all $\delta$ values. The value of $\nu_\mathrm{SSA}$ does however increase with increasing $\delta$.

- The value of $\epsilon_B$ sets the magnetic field strength. Higher magnetic fields lead to more SSA, and therefore $\nu_\mathrm{SSA}$ depends strongly on this parameter. Moreover, for very small magnetic fields ($\epsilon_B < 0.01$), the electrons do not cool efficiently ($t_\mathrm{sy} > t_\mathrm{dyn}$), and the flux in the optically thin part of the SED varies significantly with $\epsilon_B$. For values of $\epsilon_B > 0.01$ the dependence of the SED with this parameter is, however, rather weak.

- The value of $p$ affects mostly the slope in the optically thin part of the spectrum. Thus, observational restrictions on this parameter can only be obtained with observations at frequencies significantly higher than $\nu_\mathrm{SSA}$. The frequency $\nu_\mathrm{SSA}$ itself does not vary significantly with $p$.

- Increasing the corona temperature increases $U_\mathrm{th,e}$, and therefore also $U_\mathrm{nt,e}$ and $U_B$ for fixed values of $\delta$ and $\epsilon_B$. Thus, increasing $T_\mathrm{c}$ has a similar impact as increasing $\delta$ and $\epsilon_B$. The main difference occurs for $k T_\mathrm{c} \sim 300$ keV, at which point the thermal electrons play a significant role in further absorbing the emission below $\nu_\mathrm{SSA}$, although their emission is negligible (cite: Margalit2021). For completeness, we explore in more detail the emission from thermal electrons in Appendix [6](#app:thermal_synchrotron).

- The Thomson opacity defines the density of thermal particles and, therefore, impacts $U_\mathrm{th,e}$. The increase in $\tau_\mathrm{T}$ therefore has a similar impact as the increase in $k T_\mathrm{c}$.

- For a fixed $M_\mathrm{BH}$, the value of $r_\mathrm{c}$ determines the size of the corona. A bigger corona produces more emission, and it is also more transparent as it is more diluted (as $n_\mathrm{th,0} \propto \tau_\mathrm{T} \, r_\mathrm{c}^{-1}$). Thus, $\nu_\mathrm{SSA}$ decreases with an increasing $r_\mathrm{c}$. This is the only parameter for which an increase in the total peak flux is accompanied by a decrease in $\nu_\mathrm{SSA}$, and it is, therefore, a key parameter in the SED fitting to get the correct peak position and flux.

As discussed in Sect. [2.1](#sec:corona_model), we can reduce the number of free parameters by assuming an energy condition of the form $\epsilon_B = \eta \, \delta \, ( 1+\xi_\mathrm{e,p}) = 41 \, \delta$ and the observational relation for $T_\mathrm{c}(\tau_\mathrm{T})$ from (cite: Tortosa2018). The results are shown in Fig. [2](#fig:corona_seds_tied_parameters). We can summarise them as:

- Increasing $\delta$ (with $\epsilon_B(\delta)$) leads to a significant increase in both $\nu_\mathrm{SSA}$ and the peak flux.

- Changes in $\tau_\mathrm{T}$ (with $T_\mathrm{c}(\tau_\mathrm{T})$) have negligible effects in the SED. This is because the SED depends in similar ways on $\tau_\mathrm{T}$ and $T_\mathrm{c}$, and $\tau_\mathrm{T}$ and $T_\mathrm{c}$ are anti-correlated, thus compensating the changes in the SED. This means that, in general, we do not expect the pairs of values of $\tau_\mathrm{T}$ and $T_\mathrm{c}$ to have a significant impact on the SED.

![image](Figures/corona_seds_fixed-conditions.pdf)\

On a final note, the SMBH mass, $M_\mathrm{BH}$, has a very strong impact on the SED as it affects the size of the corona (for a fixed $r_\mathrm{c}$) and, to a lesser extent, the non-thermal electron distribution (via $v_\mathrm{ff}$). In Fig. [3](#fig:corona_sed_M), we show corona SEDs for a broad range of SMBH masses. The behaviour is similar to that seen for variations in $r_\mathrm{c}$, i.e., a decreasing $\nu_\mathrm{SSA}$ and an increasing flux with an increasing $M_\mathrm{BH}$. We show that for the most massive SMBHs, we expect the corona emission to peak at a frequency $\nu_\mathrm{p} < 100$ GHz, whereas for low-mass SMBHs, the peak should fall at significantly higher frequencies ($\nu_\mathrm{p} > 400$ GHz). More specifically, the dependence of the peak frequency with the black hole mass in Fig. [3](#fig:corona_sed_M) is $\nu_\mathrm{p} \propto M_\mathrm{BH}^{-0.37}$.

![](Figures/corona_seds_M.pdf)

## Studying sources at high redshift

The detection of mm coronal emission has so far been almost exclusively limited to local AGN due to sensitivity limitations. This can potentially be overcome in the case of high-$z$ lensed quasars with high amplification factors $\mu$ and large $M_\mathrm{BH}$. Remarkably, a hint of such coronal emission was found in APM 08279+5255, an AGN at $z\simeq3.9$ hosting an SMBH with $M_\mathrm{BH} \approx 10^{9.8}$ M$_\odot$(cite: Yang2023b), and a clear detection was recently reporeted in the lensed quasar RXJ1131$-$1231, located at $z = 0.658$ (cite: Rybak2025).

In Fig. [4](#fig:corona_sed_z), we show the corona SEDs for a source with $M_\mathrm{BH}= 10^9$ M$_\odot$ and $\mu=10$ located at different $z$ values. The remaining parameters are the same as those used in Fig. [3](#fig:corona_sed_M). For sources at $z>1$, the peak of the SED falls below 40 GHz, and their maximum flux density falls below 0.1 mJy, thus making their observation unfeasible for ALMA. Instead, these are good candidates for the upcoming Square Kilometer Array (SKA[^6]). For conditions similar to those assumed here, we predict that the SKA-Mid could detect such sources up to $z \sim 4$ with a $\sim$1 h integration (reaching sensitivities of $\sim$1 $\mu$Jy).

![](Figures/corona_seds_z_M1e9_SKA.pdf)

## Analysis of the sample sources

We apply our model and fitting scheme to a sample of seven RQ AGNs that includes all sources for which strong indications of coronal activity have been reported in the literature (GRS 1734$-$292, IC 4329A, MCG+08$-$11$-$11, NGC 985 and NGC 1068), together with two sources for which high-resolution data from radio-cm to (sub)mm is available (MCG$-$06$-$30$-$15 and NGC 3227). For all sources, we do a detailed bibliographic search for published flux densities and then include additional data from unpublished archival observations from various surveys. Namely, we search for archival data with the Karl G. Jansky Very Large Array (VLA)[^7], and surveys accessed via the CIRADA image web cutout service[^8], in particular the VLASS (cite: Lacy2020), NVSS (cite: NVSS), and RACS (cite: Hale2021). In Appendix [7](#app:sample), we provide a short description of each source, and in Tables [1](#table:grs_fluxes)-[7](#table:ngc3227_fluxes) we detail the data used, including the flux densities and relevant angular sizes.

The SEDs of six sources and their fit are shown in Fig. [5](#fig:sources_seds_non-cons). We leave MCG+08$-$11$-$11 out of this part of the analysis, since its corona component is not constrained by the currently available data (Fig. [10](#fig:SED_mgce)). More details about the SED fitting procedure in each source are discussed in Appendix [7](#app:sample), and the corresponding fit posteriors are provided in Figs. [11](#fig:grs_cornerplot)– [17](#fig:ngc3227_cornerplot).

![image](Figures/SED_GRS1734.pdf) ![image](Figures/SED_IC4329A.pdf)\
![image](Figures/SED_MCG-6-30-15.pdf) ![image](Figures/SED_NGC985.pdf)\
![image](Figures/SED_NGC1068.pdf) ![image](Figures/SED_NGC3227.pdf)

We summarize the results of the SED fitting of the two relevant corona parameters, $r_\mathrm{c}$ and $\delta$, in Fig. [6](#fig:r_vs_delta). The parameters range in the values $r_\mathrm{c} = 60$–250 and $\delta=10^{-3}$–10$^{-1}$, with median values of $r_\mathrm{c} \approx 133$ and $\log{\delta} \approx -1.86$ ($\delta \approx 1.4$%). The derived values of $B$ range between 10–150 G, with a median of $\approx$20 G. We also find values of $\sigma$ ranging between 0.01–1, with a mean value of $\lesssim$0.1, roughly consistent with the assumption of a significantly magnetised medium ($\sigma \sim 1$).

![](Figures/plot_r_vs_delta_non-CONs.pdf)

The last thing we study here is whether the peak of the corona SED is anticorrelated with the SMBH mass as predicted in Sect. [3.1](#sec:parameter_exploration). We show a plot of these two quantities in Fig. [7](#fig:nup_vs_MBH). Although the sample is still very small, a hint of this anticorrelation can be seen.

![](Figures/plot_nup_vs_MBH_non-CONs.pdf)

## $M_\mathrm{BH}$–$L_\mathrm{220\,GHz}$ correlation modelling

For a fixed value of $M_\mathrm{BH}$, we can use our corona emission model to calculate the corona emission at a rest-frame frequency of 220 GHz. We can repeat this calculation for a broad range of $M_\mathrm{BH}$ and plot this relation as in Fig. [8](#fig:correlation). One key prediction of our model is a slope change in the correlation at $\nu L_\nu \sim 10^{39}$ erg s$^{-1}$, related to the corona emission becoming optically thin at 220 GHz for SMBHs more massive than $\sim$10$^8$ M$_\odot$(Fig. [3](#fig:corona_sed_M)).

We compare our correlation with the empirical one reported by (cite: Ruffa2024). The result is shown in Fig. [8](#fig:correlation). In general, we can broadly explain the spread on the observed correlation when taking into account the parameter space available in $\delta$ and $r_\mathrm{c}$, which are the most relevant parameters for the corona emission. This supports a physical connection underlying this correlation, although this still needs to be tested in more detail and with an increased sample size, in particular at $\nu L_\nu \lesssim 10^{37}$ erg s$^{-1}$ and $\nu L_\nu \gtrsim 10^{40}$ erg s$^{-1}$. In addition, when using a single frequency band, very-high-angular-resolution observations are needed to isolate the (compact) coronal component from other galactic contributions, which can otherwise contaminate significantly the flux densities at mm frequencies. This additional non-coronal emission shifts the observed sources farther to the right in Fig. [8](#fig:correlation). We also note that some points lie significantly to the left of the correlation (in particular around $\nu L_\nu \sim 10^{38}$ erg s$^{-1}$), suggesting that they are underluminous in mm wavelengths.

![image](Figures/correlation_L-vs-rc_range.pdf) ![image](Figures/correlation_L-vs-delta_range.pdf)

# Discussion

The corona properties we derived in Sect. [3.3](#sec:results_sources) are roughly in agreement with what has been reported by other authors in the literature (cite: Behar2015; Inoue2018), which raises two points. First, we note that the sizes inferred from the mm observations are consistently larger than the ones inferred from X-ray observations (cite: Fabian2015) or microlensing (cite: Rybak2025). Second, we note that the value we obtain of $\delta \approx 1.4$% is in agreement with the value required to explain the MeV background (cite: Inoue2008; Inoue2019). In addition, this value of $\delta$ corresponds to $\epsilon_B \sim 0.5$, leading to $\beta_B \sim 10$ (Sect. [2.1](#sec:corona_model)). We note that values of $\beta_B > 1$ may challenge the ability of magnetic fields to sustain particle acceleration and heating in the corona (cite: Inoue2024).

Below, we provide an overview of the main limitations of our multi-component SED fitting, both from the modelling perspective and the observational aspects, in order to suggest possible ways to move forward.

First, we highlight that we are using a one-zone coronal emission model. Even though the assumption of a homogeneous emitter is most likely an oversimplification, it still yields results that are currently consistent with the observations. It remains extremely difficult to constrain more complex models (cite: Raginski2016) unless the optically thick part of the radio-mm SED is clearly detected. In most sources, this will require very deep and high-angular-resolution observations at frequencies below 100 GHz. Notably, the correlation between radio and X-ray luminosity is weaker at 22 GHz (cite: Magno2025) than at 100 GHz (cite: Ricci2023), consistent with the weaker coronal emission at 22 GHz predicted by our one-zone model. Another limitation of assuming a homogeneous spherical corona is that we cannot predict realistic images of it, although their characteristic sizes of below a few $\mu$as make them unresolvable with current facilities. As a final note on the coronae, we note that when observing very dust-obscured sources, we could expect absorption of its emission by dust at frequencies above $\nu_{\tau_1}$, although this depends on the dust being along our line of sight to the corona.

Further limitations of the methodology used here include not accounting for an AME component from spinning dust grains, which could be relevant in sources that present a bump in the SED at $\sim$30 GHz (which is not the case for the sources in our sample). This component could be added at the expense of additional free parameters. Regarding the synchrotron component, we preferred to ignore the effects of f–f absorption (FFA) in this component due to the limited data at high angular resolution at low frequencies, although this possibility is available in our code (cite: Mutie2025). In this regard, it could be possible to adopt a more model-dependent approach in which, under certain assumptions about the diffuse gas distribution, the FFA is linked to the f–f emission, but this should be properly tested on a large sample of galaxies not necessarily limited to RQ AGN with corona emission. For this reason, we currently favour a more phenomenological approach in which the parameters that describe the FFA and f–f emission are not tied to further assumptions.

Finally, we highlight the observational challenges involved in studying the corona emission of RQ AGN. From a fitting perspective, it is crucial to have a well-sampled SED from radio to FIR with consistent angular resolutions and $uv$-coverage. This ensures that the same scales are probed, although it is very challenging to obtain such a consistent dataset (cite: Mutie2025). High-resolution IR imaging is currently unavailable, which hinders our chances of constraining the dust component. The next generation VLA (ngVLA[^9]) is very promising due to the extremely good angular resolution and sensitivity to frequencies up to $\sim$100 GHz that it will provide. In the mm to sub-mm domain, ALMA will remain the most suitable observatory.

One of the most difficult issues to address in the SED fitting is the corona variability on timescales of days. So far, the most extreme case of variability was found in IC 4329A, in which the mm flux density varied by a factor $\sim$3 and the inferred corona size by a factor of $\sim$2, while $\delta$ remained about constant (cite: Shablovinskaya2024). Other sources have shown even less variability, and thus the corresponding change in the coronal parameters should be even smaller. However, this is difficult to assess due to the very limited studies of this phenomenon to date, and the lack of broad frequency coverage needed to get a good SED fit. In this regard, the prospects for the ALMA Wide Sensitivity Upgrade are particularly promising, as it will allow us to obtain a broad bandwidth in a single epoch, something particularly useful around $\sim$100 GHz (cite: Shablovinskaya2024). Complementing this with simultaneous hard X-ray observations is ideal, as it can further reduce the uncertainty in the corona parameters $\tau_\mathrm{T}$ and $k\,T_\mathrm{c}$, although this should not be a deciding factor in most cases (Fig. [2](#fig:corona_seds_tied_parameters)).

# Conclusions

We presented a comprehensive study of mm-wave coronal emission in SMBH coronae. We first introduced a model for calculating the synchrotron emission from an SMBH corona based on (cite: Inoue2018), coupled with an SED fitting scheme optimised for realistic datasets. That is, we minimised the number of free parameters in the model by introducing a physically motivated parameterization of the magnetic field intensity and an empirical parameterization for the opacity and temperature of the corona. We applied our model systematically to the five RQ AGNs for which coronal mm emission had been reported, together with two additional RQ AGNs with excellent multi-wavelength data from radio-cm to sub-mm frequencies. Our SED fitting results suggest that the coronae have non-thermal particle energy density fractions of 0.5–10% and radii of 60–250 $R_\mathrm{g}$, from which we infer typical magnetic fields of 10–60 G. These sets of parameters can also explain the putative correlation between $M_\mathrm{BH}$ and mm-wave luminosity presented in (cite: Ruffa2024). This opens the possibility of estimating $M_\mathrm{BH}$ via mm-wave observations in systems difficult to observe at other wavelengths, such as extremely obscured sources. Another suggested application of this approach is to measure faint coronal emission in high-$z$ lensed quasars using next-generation radio observatories. We conclude that multifrequency continuum observations spanning from radio to far-IR frequencies—with particular emphasis on the mm band—can be used as direct probes of the physical properties of SMBH coronae. The knowledge gained from these observations can have direct applications to other studies related to accretion disc coronae, such as in XRBs and tidal disruption events. Moreover, the detailed information on electron acceleration in the corona can help multi-messenger emission modelling, allowing to derive more robust predictions of neutrino sources, or verify neutrino detections.

# Acknowledgements

SdP, CY, SA and SK gratefully acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No 789410, PI: S. Aalto). SGB acknowledges support from the Spanish grant PID2022-138560NB-I00, funded by MCIN AEI/10.13039/501100011033/FEDER, EU. MPS acknowledges support under grants RYC2021-033094-I, CNS2023-145506 and PID2023-146667NB-I00 funded by MCIN/AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR. JBT acknowledges support from the DFG, via the Collaborative Research Center SFB1491 "Cosmic Interacting Matters - from Source to Signal" (project no. 445052434). IGB is supported by the Programa Atracción de Talento Investigador “César Nombela” via grant 2023-T1/TEC-29030 funded by the Community of Madrid.

This paper makes use of the following ALMA data:

ADS/JAO.ALMA#2017.1.00236.S, ADS/JAO.ALMA#2019.1.00618.S, ADS/JAO.ALMA#2019.1.01230.S,

ADS/JAO.ALMA#2015.1.01047.S, ADS/JAO.ALMA#2023.1.00121.S, ADS/JAO.ALMA#2021.1.00812.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This research has made use of the CIRADA cutout service at [cutouts.cirada.ca](cutouts.cirada.ca), operated by the Canadian Initiative for Radio Astronomy Data Analysis (CIRADA). CIRADA is funded by a grant from the Canada Foundation for Innovation 2017 Innovation Fund (Project 35999), as well as by the Provinces of Ontario, British Columbia, Alberta, Manitoba and Quebec, in collaboration with the National Research Council of Canada, the US National Radio Astronomy Observatory and Australia’s Commonwealth Scientific and Industrial Research Organisation.

90 natexlab

(ref: Alonso-Herrero2019) Alonso-Herrero, A., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2019, A&A, 628, A65

(ref: An2024) An, F., Vaccari, M., Best, P. N., et al. 2024, MNRAS, 528, 5346

(ref: bilby) Ashton, G., Hübner, M., Lasky, P. D., et al. 2019, ApJS, 241, 27

(ref: Balbus1998) Balbus, S. A. & Hawley, J. F. 1998, Reviews of Modern Physics, 70, 1

(ref: Bambi2021) Bambi, C., Brenneman, L. W., Dauser, T., et al. 2021, Space Sci. Rev., 217, 65

(ref: Bauer2015) Bauer, F. E., Arévalo, P., Walton, D. J., et al. 2015, ApJ, 812, 116

(ref: Behar2015) Behar, E., Baldi, R. D., Laor, A., et al. 2015, MNRAS, 451, 517

(ref: Behar2018) Behar, E., Vogel, S., Baldi, R. D., Smith, K. L., & Mushotzky, R. F. 2018, MNRAS, 478, 399

(ref: Beloborodov2017) Beloborodov, A. M. 2017, ApJ, 850, 141

(ref: Bontempi2012) Bontempi, P., Giroletti, M., Panessa, F., Orienti, M., & Doi, A. 2012, MNRAS, 426, 588

(ref: Cangemi2021) Cangemi, F., Beuchert, T., Siegert, T., et al. 2021, A&A, 650, A93

(ref: Ciesla2012) Ciesla, L., Boselli, A., Smith, M. W. L., et al. 2012, A&A, 543, A161

(ref: NVSS) Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693

(ref: Dey2024) Dey, S., Goyal, A., Małek, K., & Dı́az-Santos, T. 2024, ApJ, 966, 61

(ref: Dickinson2018) Dickinson, C., Ali-Haı̈moud, Y., Barr, A., et al. 2018, New A Rev., 80, 1

(ref: Draine2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: Eichmann2022) Eichmann, B., Oikonomou, F., Salvatore, S., Dettmar, R.-J., & Tjus, J. B. 2022, ApJ, 939, 43

(ref: Fabian2015) Fabian, A. C., Lohfink, A., Kara, E., et al. 2015, MNRAS, 451, 4375

(ref: Fang2024) Fang, K., Halzen, F., Heinz, S., & Gallagher, J. S. 2024, arXiv e-prints, arXiv:2410.02119

(ref: Fernandez-Torreiro2024) Fernández-Torreiro, M., Génova-Santos, R. T., Rubiño-Martı́n, J. A., et al. 2024, MNRAS, 527, 11945

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: Gallagher2024) Gallagher, J. S., Kotulla, R., Laufman, L., et al. 2024, arXiv e-prints, arXiv:2406.12126

(ref: Gallimore2024) Gallimore, J. F., Impellizzeri, C. M. V., Aghelpasand, S., et al. 2024, ApJL, 975, L9

(ref: Garcia-Burillo2016) Garcı́a-Burillo, S., Combes, F., Ramos Almeida, C., et al. 2016, ApJL, 823, L12

(ref: Groselj2024) Grošelj, D., Hakobyan, H., Beloborodov, A. M., Sironi, L., & Philippov, A. 2024, , 132, 085202

(ref: Haardt1991) Haardt, F. & Maraschi, L. 1991, ApJL, 380, L51

(ref: Hale2021) Hale, C. L., McConnell, D., Thomson, A. J. M., et al. 2021, PASA, 38, e058

(ref: Heesen2022) Heesen, V., Staffehl, M., Basu, A., et al. 2022, A&A, 664, A83

(ref: IceCube2022) IceCube Collaboration, Abbasi, R., Ackermann, M., et al. 2022, Science, 378, 538

(ref: Ichikawa2019) Ichikawa, K., Ricci, C., Ueda, Y., et al. 2019, ApJ, 870, 31

(ref: Imanishi2016) Imanishi, M., Nakanishi, K., & Izumi, T. 2016, AJ, 152, 218

(ref: Ingram2023) Ingram, A., Ewing, M., Marinucci, A., et al. 2023, MNRAS, 525, 5437

(ref: Inoue2014) Inoue, Y. & Doi, A. 2014, PASJ, 66, L8

(ref: Inoue2018) Inoue, Y. & Doi, A. 2018, ApJ, 869, 114

(ref: Inoue2020) Inoue, Y., Khangulyan, D., & Doi, A. 2020, ApJL, 891, L33

(ref: Inoue2019) Inoue, Y., Khangulyan, D., Inoue, S., & Doi, A. 2019, ApJ, 880, 40

(ref: Inoue2024) Inoue, Y., Takasao, S., & Khangulyan, D. 2024, PASJ, 76, 996

(ref: Inoue2008) Inoue, Y., Totani, T., & Ueda, Y. 2008, ApJL, 672, L5

(ref: Jana2025) Jana, A., Ricci, C., Venselaar, S. M., et al. 2025, arXiv e-prints, arXiv:2505.13242

(ref: Kamraj2022) Kamraj, N., Brightman, M., Harrison, F. A., et al. 2022, ApJ, 927, 42

(ref: Karpouzas2021) Karpouzas, K., Méndez, M., Garcı́a, F., et al. 2021, MNRAS, 503, 5522

(ref: Kawamuro2022) Kawamuro, T., Ricci, C., Imanishi, M., et al. 2022, ApJ, 938, 87

(ref: Kornecki2022) Kornecki, P., Peretti, E., del Palacio, S., Benaglia, P., & Pellizza, L. J. 2022, A&A, 657, A49

(ref: Koss2017) Koss, M., Trakhtenbrot, B., Ricci, C., et al. 2017, ApJ, 850, 74

(ref: Kun2024) Kun, E., Bartos, I., Becker Tjus, J., et al. 2024, arXiv e-prints, arXiv:2404.06867

(ref: Kylafis2023) Kylafis, N. D., Reig, P., & Tsouros, A. 2023, A&A, 679, A81

(ref: Lacki2013) Lacki, B. C. 2013, MNRAS, 431, 3003

(ref: Lacki2010) Lacki, B. C. & Thompson, T. A. 2010, ApJ, 717, 196

(ref: Lacy2020) Lacy, M., Baum, S. A., Chandler, C. J., et al. 2020, PASP, 132, 035001

(ref: Laor2008) Laor, A. & Behar, E. 2008, MNRAS, 390, 847

(ref: Magno2025) Magno, M., Smith, K. L., Wong, O. I., et al. 2025, arXiv e-prints, arXiv:2501.17224

(ref: Margalit2021) Margalit, B. & Quataert, E. 2021, ApJL, 923, L14

(ref: Margalit2024) Margalit, B. & Quataert, E. 2024, arXiv e-prints, arXiv:2403.07048

(ref: Marti1998) Marti, J., Mirabel, I. F., Chaty, S., & Rodriguez, L. F. 1998, A&A, 330, 72

(ref: Mejia-Restrepo2022) Mejı́a-Restrepo, J. E., Trakhtenbrot, B., Koss, M. J., et al. 2022, ApJS, 261, 5

(ref: Merten2017) Merten, L., Becker Tjus, J., Eichmann, B., & Dettmar, R.-J. 2017, Astroparticle Physics, 90, 75

(ref: Michiyama2024) Michiyama, T., Inoue, Y., Doi, A., et al. 2024, ApJ, 965, 68

(ref: Murase2020) Murase, K., Kimura, S. S., & Mészáros, P. 2020, , 125, 011101

(ref: Murphy2011) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: Murphy2018) Murphy, E. J., Dong, D., Momjian, E., et al. 2018, ApJS, 234, 24

(ref: Murphy2020) Murphy, E. J., Hensley, B. S., Linden, S. T., et al. 2020, ApJL, 905, L23

(ref: Mutie2025) Mutie, I. M., del Palacio, S., Beswick, R. J., et al. 2025, MNRAS, 539, 808

(ref: Nattila2024) Nättilä, J. 2024, arXiv e-prints, arXiv:2408.08161

(ref: Ozel2000) Özel, F., Psaltis, D., & Narayan, R. 2000, ApJ, 541, 234

(ref: Pal2023c) Pal, I. & Stalin, C. S. 2023, MNRAS, 518, 2529

(ref: Panessa2019) Panessa, F., Baldi, R. D., Laor, A., et al. 2019, Nature Astronomy, 3, 387

(ref: Panessa2022) Panessa, F., Chiaraluce, E., Bruni, G., et al. 2022, MNRAS, 515, 473

(ref: Petrucci2023) Petrucci, P. O., Piétu, V., Behar, E., et al. 2023, A&A, 678, L4

(ref: Poojon2024) Poojon, P., Chung, A., Hoang, T., et al. 2024, ApJ, 963, 88

(ref: Raginski2016) Raginski, I. & Laor, A. 2016, MNRAS, 459, 2082

(ref: Raimundo2013) Raimundo, S. I., Davies, R. I., Gandhi, P., et al. 2013, MNRAS, 431, 2294

(ref: Ramirez-Olivencia2022) Ramı́rez-Olivencia, N., Varenius, E., Pérez-Torres, M., et al. 2022, A&A, 658, A4

(ref: Ricci2023) Ricci, C., Chang, C.-S., Kawamuro, T., et al. 2023, ApJL, 952, L28

(ref: Ricci2018) Ricci, C., Ho, L. C., Fabian, A. C., et al. 2018, MNRAS, 480, 1819

(ref: Romero2014) Romero, G. E., Vieyro, F. L., & Chaty, S. 2014, A&A, 562, L7

(ref: Ruffa2024) Ruffa, I., Davis, T. A., Elford, J. S., et al. 2024, MNRAS, 528, L76

(ref: Rybak2025) Rybak, M., Sluse, D., Gupta, K., et al. 2025, arXiv e-prints, arXiv:2503.13313

(ref: Sani2012) Sani, E., Davies, R. I., Sternberg, A., et al. 2012, MNRAS, 424, 1963

(ref: Sargent2025) Sargent, A. J., van der Horst, A. J., Johnson, M. C., et al. 2025, arXiv e-prints, arXiv:2503.20026

(ref: Shablovinskaya2024) Shablovinskaya, E., Ricci, C., Chang, C. S., et al. 2024, A&A, 690, A232

(ref: Shimwell2017) Shimwell, T. W., Röttgering, H. J. A., Best, P. N., et al. 2017, A&A, 598, A104

(ref: Sironi2020) Sironi, L. & Beloborodov, A. M. 2020, ApJ, 899, 52

(ref: Smith2020) Smith, K. L., Mushotzky, R. F., Koss, M., et al. 2020, MNRAS, 492, 4216

(ref: Fermi2025) The Fermi-LAT Collaboration, Wang, J.-M., Li, J., & Liu, J.-R. 2025, arXiv e-prints, arXiv:2502.19189

(ref: Tortosa2018) Tortosa, A., Bianchi, S., Marinucci, A., Matt, G., & Petrucci, P. O. 2018, A&A, 614, A37

(ref: Tortosa2017) Tortosa, A., Marinucci, A., Matt, G., et al. 2017, MNRAS, 466, 4193

(ref: Tortosa2024) Tortosa, A., Ricci, C., Shablovinskaia, E., et al. 2024, A&A, 687, A51

(ref: Urry1995) Urry, C. M. & Padovani, P. 1995, PASP, 107, 803

(ref: Yang2023b) Yang, C., Omont, A., Martı́n, S., et al. 2023, A&A, 680, A95

(ref: Zdziarski2021) Zdziarski, A. A., Jourdain, E., Lubiński, P., et al. 2021, ApJL, 914, L5

# Synchrotron emission from a thermal population of electrons

We explore in more detail whether it is feasible for thermal electrons alone to produce appreciable synchrotron emission, compatible with the mm emission detected in several sources. The number of relativistic electrons in a thermal distribution strongly depends on the temperature of the plasma. We, therefore, calculated SEDs for corona temperatures ranging from 200 to 400 keV, shown in Fig. [9](#fig:corona_seds_thermal). We note that values of $k T_\mathrm{c} \sim 500$ keV could be unsustainable due to runaway pair production. For $k T_\mathrm{c} < 200$ keV, there are simply not enough relativistic electrons to emit detectable synchrotron, and even for $k T_\mathrm{c} \gtrsim 300$ keV this emission is quite faint. For reference, we also show the total emission, including a very small fraction of non-thermal electrons, $\delta = 10^{-3}$. The non-thermal electrons completely dominate the emission for $k T_\mathrm{c} < 300$ keV. The only case in which the emission from thermal electrons could be dominant is for extremely high corona temperatures $k T_\mathrm{c} \sim 400$ keV and low values of $\delta \lesssim 10^{-3}$. However, such a scenario ($k T_\mathrm{c} \sim 400$ keV, $\tau_\mathrm{T}\sim1$, $r_\mathrm{c} \sim 120$, $B \sim 100$ G) is energetically very demanding, still produces faint mm emission, and would most likely overpredict the X-ray luminosity. We thus conclude that scenarios with $k T_\mathrm{c} < 200$ keV and $\delta > 10^{-3}$ are far more promising for explaining the mm emission in RQ AGNs.

![](Figures/corona_seds_T_thermal.pdf)

# Source sample

In the following, we provide a short description of the sources analysed in this work and their SED fitting. The fluxes reported in this work are a combination of archival and proprietary observations. As such, the datasets are non-simultaneous, with typical timespans of several years. Among the archives used, we highlight the LoTSS survey with LOFAR (cite: Shimwell2017), the RACS survey with ASKAP (cite: Hale2021), and the VLASS survey with the VLA (cite: Lacy2020). We note that all flux density errors presented in the tables include only the statistical errors; for the inclusion of systematic errors, we refer to Sect. [2.2](#sec:parameter_fitting). For flux densities that are not taken from the literature, we also specify the observatory that took the data we used. We used CARTA[^10] to obtain the flux density fitting a Gaussian profile.

For all sources, we also calculate the predicted X-ray luminosities by plugging the luminosity at 100 GHz from our model fitting into the correlation from (cite: Ricci2023) between the 100-GHz luminosity and the 14–150 keV luminosity. We note that, in principle, we could use the mm luminosity coming only from the corona (which should be the one scaling with the X-ray luminosity), but we prefer to keep consistency with how the correlations in (cite: Ricci2023) were derived, in which the total emission at 100 GHz was used, even though this can have a significant contribution from non-coronal components depending on the source. In addition, in some cases, the corona component peaks at frequencies significantly above 100 GHz, and we speculate that in those cases the correlation of (cite: Kawamuro2022) (K22) between the 230-GHz luminosity and the 14–150 keV luminosity can be more accurate.

## GRS 1734$-$292

This galaxy is located at a distance of 84 Mpc ($z=0.021$) and is a known hard X-ray source (cite: Tortosa2017). Moreover, (cite: Michiyama2024) found a $\gtrsim$50% increase in the source 100-GHz flux in timescales of days; this mm flux variability is a strong indication of the origin of the mm flux in the corona (cite: Shablovinskaya2024). Unfortunately, the source also presents a weak radio jet on angular scales of a few arcseconds, making it difficult to build a consistent SED, as the presence of diffuse emission leads to an artificially steep spectrum if the lower resolution data at lower frequencies are included. Due to these limitations on the dataset, and the fact that f–f emission cannot dominate at $\sim$100 GHz, we simply opt to remove the f–f component and to fix $\alpha_\mathrm{sy}=0.75$ as in (cite: Michiyama2024). In addition, the lack of data above 230 GHz prevents us from constraining the dust component, so we fix $\beta=1.78$ and $\nu_{\tau_1}=800$ GHz. We adopt a value of $M_\mathrm{BH}=10^{7.84}$ M$_\odot$(cite: Mejia-Restrepo2022). Furthermore, we fix $\tau_\mathrm{T}=2.98$ and $k T_\mathrm{c} = 12$ keV, as derived by (cite: Tortosa2017). We fit the flux densities listed in Table [1](#table:grs_fluxes). We obtain $r_\mathrm{c}=112 \pm 14$ ($R_\mathrm{c}\approx0.5$ ld) and $\log{\delta}=-1.74 \pm 0.13$, leading to $B \sim 20$ G and $\sigma \sim 0.011$; the corona peaks at $\nu_\mathrm{p} = 130 \pm 14$ GHz with a peak flux density of $S_\mathrm{p} = 0.91 \pm 0.11$ mJy and has a luminosity of $L_\mathrm{c} \approx 4\times 10^{39}$ erg s$^{-1}$. The predicted X-ray luminosity is $L_\mathrm{14-150\,keV} \approx 8\times 10^{43}$ erg s$^{-1}$, corresponding to $\lambda_\mathrm{Edd} \sim 0.004$. The cornerplot of the fit is shown in Fig. [11](#fig:grs_cornerplot).

In addition, we explore the change in the corona parameters during the epoch of higher flux, when there are only observations at ALMA B3. Thus, we choose to fix $\log{\delta}=-1.74$ as in the previous epoch, and the fit yields $r_\mathrm{c}=178 \pm 9$. This suggests that the size of the corona can be much larger than the one derived for the better-sampled epoch, although it is not possible at this stage to define which value is more representative of the average size of the mm-emitting corona.

|       |                 |                            |      |             |
|:-----:|:---------------:|:--------------------------:|:----:|:-----------:|
| $\nu$ |     $S_\nu$     | $\theta_1 \times \theta_2$ | Type |     Ref     |
| (GHz) |      (mJy)      |        (arcsec$^2$)        |      |             |
| 1.45  | $51.0 \pm 6.0$  |      $7.2 \times 7.2$      |  UL  |  $^{(c)}$   |
| 4.89  | $13.0 \pm 1.3$  |      $1.9 \times 1.9$      |  UL  |  $^{(c)}$   |
| 8.49  |  $5.6 \pm 0.6$  |      $1.2 \times 1.2$      |  UL  |  $^{(c)}$   |
| 14.9  |  $2.6 \pm 0.3$  |      $0.7 \times 0.7$      | yes  |  $^{(a)}$   |
| 22.0  |  $3.8 \pm 0.1$  |     $0.55 \times 0.55$     |  UL  | VLA$^{(b)}$ |
| 22.0  |  $1.4 \pm 0.1$  |      $0.3 \times 0.3$      |  LL  | VLA$^{(b)}$ |
| 97.5  | $1.45 \pm 0.07$ |      $0.3 \times 0.3$      | yes  |  $^{(a)}$   |
| 145.0 | $1.44 \pm 0.05$ |      $0.3 \times 0.3$      | yes  |  $^{(a)}$   |
| 225.0 | $1.20 \pm 0.07$ |      $0.3 \times 0.3$      | yes  |  $^{(a)}$   |

: Flux densities and sizes of the flux extraction regions for GRS 1734$-$292. The Type column indicates if the values were used for the fit as observed (yes), considered as upper limits (UL) or lower limits (LL). References: $^{(a)}$(cite: Michiyama2024) and references therein; $^{(b)}$this work; $^{(c)}$(cite: Marti1998).

## IC 4329A

This is a very well-studied source both in radio and X-rays (cite: Inoue2018; Ingram2023; Tortosa2024; Shablovinskaya2024), showing convincing evidence of a hybrid corona. In fact, this source is one of the first two sources for which a bump in the SED around $\sim$100 GHz was detected (cite: Inoue2018). Moreover, (cite: Shablovinskaya2024) proved that the emission at 100 GHz is significantly variable on daily timescales. We adopt $M_\mathrm{BH} = 6.8\times 10^7$  M$_\odot$ as in (cite: Shablovinskaya2024), and fit our model to the same dataset presented in Table 1 of (cite: Inoue2018). To present a consistent approach as with the other sources, we fix $p=2.7$ and $\tau_\mathrm{T}=0.25$ and $kT_\mathrm{c} \approx 166$ K. We note that, observationally, the values of $\tau_\mathrm{T}$ and $kT_\mathrm{c}$ are not well constrained and are also variable (cite: Tortosa2024), but the specific values adopted should not play a significant role in the fitting (as shown in Sect. [3.1](#sec:parameter_exploration)). The SED is poorly constrained between 10 and 100 GHz; we therefore fix $\alpha_\mathrm{sy}=-0.59$ as in (cite: Inoue2018). We obtain $r_\mathrm{c}=261^{+141}_{-45}$ and $\log{\delta}=-2.25^{+0.24}_{-0.48}$ ($R_\mathrm{c}\approx 1$ ld), leading to $B \sim 9.3$ G and $\sigma \sim 0.06$. The corona component peaks at $\nu_\mathrm{p} = 90\pm20$ GHz, with a peak flux density of $S_\mathrm{p} = 4.2\pm1.1$ mJy, and has a luminosity of $L_\mathrm{c} \approx 7\times 10^{39}$ erg s$^{-1}$. The cornerplot of the fit is shown in Fig. [12](#fig:icf_cornerplot). The predicted X-ray luminosity is $L_\mathrm{14-150\,keV} \approx 2\times 10^{44}$ erg s$^{-1}$, corresponding to $\lambda_\mathrm{Edd} \sim 0.02$. Alternatively, the SED fit to the multiple epochs of 100-GHz observations presented in (cite: Shablovinskaya2024) yielded a broader range of sizes of the corona of $\sim$170–300 $R_\mathrm{g}$.

|       |                 |                            |      |             |
|:-----:|:---------------:|:--------------------------:|:----:|:-----------:|
| $\nu$ |     $S_\nu$     | $\theta_1 \times \theta_2$ | Type |     Ref     |
| (GHz) |      (mJy)      |        (arcsec$^2$)        |      |             |
|  1.4  | $60.5 \pm 2.4$  |      $8.1 \times 3.6$      |  UL  |  $^{(a)}$   |
|  1.5  | $63.5 \pm 4.8$  |     $45.0 \times 45.0$     |  UL  |  $^{(a)}$   |
|  4.9  | $19.5 \pm 0.8$  |      $1.3 \times 0.5$      |  UL  |  $^{(a)}$   |
|  8.4  | $13.9 \pm 1.2$  |      $0.8 \times 0.4$      | yes  |  $^{(a)}$   |
| 22.0  | $10.1 \pm 0.1$  |     $2.65 \times 0.83$     |  UL  | VLA$^{(c)}$ |
| 33.0  | $14.3 \pm 1.6$  |      $8.5 \times 5.0$      |  UL  |  $^{(a)}$   |
| 35.0  | $14.7 \pm 1.7$  |      $8.0 \times 4.7$      |  UL  |  $^{(a)}$   |
| 90.5  | $8.00 \pm 0.49$ |     $0.45 \times 0.44$     | yes  |  $^{(a)}$   |
| 92.4  | $7.92 \pm 0.49$ |     $0.44 \times 0.43$     | yes  |  $^{(a)}$   |
| 102.5 | $8.07 \pm 0.50$ |     $0.43 \times 0.40$     | yes  |  $^{(a)}$   |
| 104.5 | $7.81 \pm 0.47$ |     $0.42 \times 0.39$     | yes  |  $^{(a)}$   |
| 138.0 | $6.69 \pm 0.38$ |     $0.28 \times 0.25$     | yes  |  $^{(a)}$   |
| 139.9 | $6.79 \pm 0.39$ |     $0.27 \times 0.25$     | yes  |  $^{(a)}$   |
| 150.0 | $6.45 \pm 0.39$ |     $0.29 \times 0.24$     | yes  |  $^{(a)}$   |
| 152.0 | $6.27 \pm 0.38$ |     $0.25 \times 0.23$     | yes  |  $^{(a)}$   |
| 213.0 | $4.39 \pm 1.21$ |     $0.17 \times 0.15$     | yes  |  $^{(a)}$   |
| 215.0 | $4.85 \pm 0.84$ |     $0.18 \times 0.16$     | yes  |  $^{(a)}$   |
| 229.0 | $5.17 \pm 0.92$ |     $0.18 \times 0.14$     | yes  |  $^{(a)}$   |
| 231.0 | $4.98 \pm 0.94$ |     $0.16 \times 0.14$     | yes  |  $^{(a)}$   |
| 263.0 | $13.0 \pm 0.2$  |     $0.95 \times 0.53$     |  UL  |  $^{(d)}$   |
| 1199  |  $488 \pm 73$   |     $>5.0 \times 5.0$      |  UL  |  $^{(b)}$   |

: Flux densities and sizes of the flux extraction regions for IC 4329A. The Type column indicates if the values were used for the fit as observed (yes), which are considered upper limits (UL) or lower limits (LL). References: $^{(a)}$(cite: Inoue2018); $^{(b)}$(cite: Ichikawa2019); $^{(c)}$this work; $^{(d)}$(cite: Imanishi2016).

## MCG$-$06$-$30$-$15

This RQ-AGN is located at a distance of $D=34$ Mpc and hosts an SMBH with $\log{M_\mathrm{BH}} \approx 7.3$ (cite: Raimundo2013). From hard X-ray observations it is inferred $kT_\mathrm{c} \approx 63$ keV and $\tau_\mathrm{T}=0.27$. An analysis of the VLA fluxes from images at different resolutions indicates that there is significant diffuse emission on scales $>0.3"$ (Table [3](#table:mcg6_fluxes)).

We cannot constrain the dust component properly due to the lack of data at $\nu > 300$ GHz with comparable resolution. Following (cite: Kawamuro2022), we assume that the dust contribution is not significant at mm wavelengths given the very high angular resolution of the observations. We thus fix the dust component normalization to an arbitrary low value. In addition, trying to fit the spectral index $p$ leads to a solution that hits the hard limit on the priors, and we thus fix $p=2.1$. We obtain $r_\mathrm{c}=115\pm6$ ($R_\mathrm{c}\approx 0.13$ ld) and $\log{\delta}=-1.98 \pm 0.06$, leading to $B \sim 20.9$ G and $\sigma \sim 0.036$. The corona component peaks at $\nu_\mathrm{p} = 133\pm6$ GHz, with a peak flux density of $S_\mathrm{p} = 0.64\pm0.06$ mJy, and has a bolometric synchrotron luminosity of $L_\mathrm{c}\approx 3\times10^{38}$ erg s$^{-1}$. The predicted X-ray luminosity is $L_\mathrm{14-150\,keV} \sim 8\times10^{43}$ erg s$^{-1}$, corresponding to an Eddington ratio of $\lambda_\mathrm{Edd} \sim 0.003$. The cornerplot of the fit is shown in Fig. [13](#fig:mcgs_cornerplot).

|        |                   |                            |      |              |
|:------:|:-----------------:|:--------------------------:|:----:|:------------:|
| $\nu$  |      $S_\nu$      | $\theta_1 \times \theta_2$ | Type |     Ref      |
| (GHz)  |       (mJy)       |        (arcsec$^2$)        |      |              |
|  1.4   |  $1.55 \pm 0.3$   |     $10.0 \times 10.0$     |  UL  | VLA$^{(a)}$  |
|  3.0   |  $0.94 \pm 0.2$   |      $3.6 \times 2.0$      |  UL  | VLA$^{(a)}$  |
|  4.9   |   $0.9 \pm 0.2$   |      $1.4 \times 1.4$      |  UL  | VLA$^{(a)}$  |
|  5.5   |  $0.28 \pm 0.06$  |      $1.5 \times 0.7$      |  UL  | VLA$^{(a)}$  |
|  8.46  |  $0.65 \pm 0.06$  |      $1.3 \times 0.5$      |  UL  | VLA$^{(a)}$  |
|  8.49  |  $0.12 \pm 0.04$  |     $0.52 \times 0.22$     |  UL  | VLA$^{(a)}$  |
|  9.0   | $0.408 \pm 0.035$ |      $0.8 \times 0.3$      |  UL  | VLA$^{(a)}$  |
| 90.52  |  $0.59 \pm 0.03$  |    $0.090 \times 0.090$    | yes  | ALMA$^{(a)}$ |
| 92.42  |  $0.59 \pm 0.03$  |    $0.090 \times 0.090$    | yes  | ALMA$^{(a)}$ |
| 102.52 |  $0.57 \pm 0.03$  |    $0.090 \times 0.090$    | yes  | ALMA$^{(a)}$ |
| 104.48 |  $0.60 \pm 0.03$  |    $0.090 \times 0.090$    | yes  | ALMA$^{(a)}$ |
| 226.31 |  $0.56 \pm 0.03$  |    $0.123 \times 0.123$    | yes  | ALMA$^{(a)}$ |
| 240.83 |  $0.53 \pm 0.03$  |    $0.123 \times 0.123$    | yes  | ALMA$^{(a)}$ |
| 228.81 |  $0.59 \pm 0.03$  |    $0.123 \times 0.123$    | yes  | ALMA$^{(a)}$ |
| 243.08 |  $0.54 \pm 0.03$  |    $0.123 \times 0.123$    | yes  | ALMA$^{(a)}$ |
| 348.4  |   $1.0 \pm 0.2$   |     $0.27 \times 0.24$     |  UL  | ALMA$^{(a)}$ |
| 856.6  |    $86 \pm 8$     |     $>5.0 \times 5.0$      |  UL  |   $^{(b)}$   |
|  1199  |   $233 \pm 14$    |     $>5.0 \times 5.0$      |  UL  |   $^{(b)}$   |

: Flux densities and sizes of the flux extraction regions for MCG$-$06$-$30$-$15. The Type column indicates if the values were used for the fit as observed (yes), considered as upper limits (UL) or lower limits (LL). References: $^{(a)}$this work; $^{(b)}$(cite: Ichikawa2019).

## MCG+08$-$11$-$11

This LIRG source is located at $z=0.02$ and hosts an SMBH with a mass of $\log{M_\mathrm{BH}} = 7.81$ (cite: Koss2017). This is a well-known hard X-ray source, and (cite: Petrucci2023) showed evidence of a correlated variability in the hard X-ray and mm emission at 100 GHz (using NOEMA observations). In (cite: Smith2020), it is listed as a jetted source at 22 GHz. VLA images at 8.5 and 14.9 GHz show that the inner structure has three point-like sources within 0.5", plus diffuse emission on larger scales. For this reason, we integrate the flux within a $\approx$1" region at all frequencies. Morevoer, (cite: Pal2023c) measured $kT_\mathrm{c} \sim$30–60 keV, suggesting that the source has $\tau_\mathrm{T} \gtrsim 1$; we fix $\tau_\mathrm{T} = 1.5$. The fact that the $\sim$100-GHz emission reported by (cite: Petrucci2023) is variable on hour-timescales indicates that the corona contribution is non-negligible at this frequency. CARMA observations at 100 GHz with a 1"-resolution indicate a flux density of 7.5 mJy (cite: Behar2018), which is significantly lower than the flux density of 18 mJy reported by (cite: Petrucci2023). We fixed the dust component parameters $\beta=1.78$ and $\nu_{\tau_1}=800$ GHz. The corona SED is, unfortunately, very poorly constrained, and a robust fit cannot be addressed at this stage without high-resolution observations at frequencies $>$100 GHz. Nonetheless, we can at least confirm that the observations are consistent with a corona of $r_\mathrm{c}\sim260$ ($R_\mathrm{c}\sim1$ ld) and $\log{\delta} \sim-1.4$ (yielding $B\sim30$ G). The predicted X-ray luminosity is $L_\mathrm{14-150\,keV} \sim 3\times10^{44}$ erg s$^{-1}$, corresponding to an Eddington ratio of $\lambda_\mathrm{Edd} \sim 0.035$. The SED is shown in Fig. [10](#fig:SED_mgce) and the cornerplot of the fit is shown in Fig. [14](#fig:mcge_cornerplot).

|       |                 |                            |      |                    |
|:-----:|:---------------:|:--------------------------:|:----:|:------------------:|
| $\nu$ |     $S_\nu$     | $\theta_1 \times \theta_2$ | Type |        Ref         |
| (GHz) |      (mJy)      |        (arcsec$^2$)        |      |                    |
| 1.51  |   $197 \pm 1$   |     $28.4 \times 28.4$     |  UL  |    VLA$^{(a)}$     |
|  3.0  |   $74 \pm 10$   |      $2.6 \times 3.0$      |  UL  |    VLA$^{(a)}$     |
| 4.91  | $17.0 \pm 0.2$  |     $0.84 \times 0.84$     |  LL  |    VLA$^{(a)}$     |
| 4.91  | $43.1 \pm 2.0$  |      $1.1 \times 1.3$      | yes  |    VLA$^{(a)}$     |
| 8.49  |  $7.5 \pm 0.1$  |     $0.38 \times 0.38$     |  LL  |    VLA$^{(a)}$     |
| 8.49  |  $27 \pm 2.0$   |      $1.1 \times 1.1$      | yes  |    VLA$^{(a)}$     |
| 14.9  |  $4.5 \pm 0.1$  |     $0.22 \times 0.22$     |  LL  |    VLA$^{(a)}$     |
| 14.9  | $15.2 \pm 1.3$  |      $1.1 \times 1.1$      | yes  |    VLA$^{(a)}$     |
| 22.0  | $5.95 \pm 0.4$  |     $0.14 \times 0.14$     |  LL  |    VLA$^{(a)}$     |
| 22.0  | $13.84 \pm 2.6$ |      $1.0 \times 1.0$      | yes  |      $^{(b)}$      |
| 22.0  | $15.85 \pm 3.1$ |      $6.0 \times 6.0$      |  UL  |      $^{(b)}$      |
| 45.0  |  $8.4 \pm 1.7$  |      $1.0 \times 1.0$      | yes  | $^{(b)}$, $^{(c)}$ |
| 100.0 |  $7.5 \pm 0.2$  |      $1.0 \times 1.0$      | yes  |      $^{(d)}$      |
| 100.0 | $18.33 \pm 2.0$ |     $>1.0 \times 1.0$      |  UL  |      $^{(e)}$      |
| 1199  | $2531 \pm 270$  |     $>5.0 \times 5.0$      |  UL  |      $^{(f)}$      |

: Flux densities and sizes of the flux extraction regions for MCG+08$-$11$-$11. The Type column indicates if the values were used for the fit as observed (yes), considered as upper limits (UL) or lower limits (LL). References: $^{(a)}$this work; $^{(b)}$(cite: Smith2020); $^{(c)}$(cite: Panessa2022); $^{(d)}$(cite: Behar2018); $^{(e)}$(cite: Petrucci2023); $^{(f)}$(cite: Ichikawa2019).

![](Figures/SED_MCG+08-11-11.pdf)

## NGC 985

This galaxy located at $D\approx 190$ Mpc hosts an SMBH with $M_\mathrm{BH} = 2.2\times 10^8$ M$_\odot$(cite: Inoue2018). (cite: Inoue2018) reported an excess in the SED of this source at $\sim$100 GHz from which they inferred the presence of a corona. The dust component is essentially unconstrained due to a very bright FIR flux from the whole galaxy (cite: Ichikawa2019). The high-resolution ALMA data favours a corona with a harder electron population, consistent with $p\approx2.1$ (cite: Inoue2018). Trying to fit this parameter hits the lower limit in the priors, and thus we fix it to $p=2.1$. Following (cite: Inoue2018), we also fix $kT_\mathrm{c}=29$ keV and $\tau_\mathrm{T}=3.5$. The inferred properties of the corona are: $r_\mathrm{c}=111^{+33}_{-14}$ ($R_\mathrm{c}\approx 1.4$ ld) and $\log{\delta}=-2.03^{+0.13}_{-0.22}$, leading to $B \sim 14.4$ G and $\sigma \sim 0.014$. The corona SED component peaks at $\nu_\mathrm{p} = 100\pm15$ GHz, with a peak flux density of $S_\mathrm{p} = 1.4\pm0.2$ mJy, and has a bolometric synchrotron luminosity of $L_\mathrm{c} \approx 4\times10^{40}$ erg s$^{-1}$. We estimate a hard X-ray luminosity $L_\mathrm{14-150\,keV}\approx 4\times 10^{45}$ erg s$^{-1}$, corresponding to an Eddington ratio of $\lambda_\mathrm{Edd} \sim 0.011$. The cornerplot of the fit is shown in Fig. [15](#fig:ngc985_cornerplot) and the data used is listed in Table [5](#table:ngcn_fluxes).

|       |                 |                            |      |             |
|:-----:|:---------------:|:--------------------------:|:----:|:-----------:|
| $\nu$ |     $S_\nu$     | $\theta_1 \times \theta_2$ | Type |     Ref     |
| (GHz) |      (mJy)      |        (arcsec$^2$)        |      |             |
|  1.4  |  $5.4 \pm 0.5$  |     $6.25 \times 6.25$     |  UL  | VLA$^{(a)}$ |
|  1.5  |  $4.7 \pm 1.4$  |     $28.4 \times 28.4$     |  UL  | VLA$^{(a)}$ |
|  4.9  |  $1.2 \pm 0.3$  |      $0.5 \times 0.4$      |  UL  |  $^{(b)}$   |
|  8.4  |  $1.1 \pm 0.2$  |      $0.9 \times 0.7$      |  UL  |  $^{(b)}$   |
| 8.49  | $0.89 \pm 0.08$ |     $0.26 \times 0.21$     | yes  | VLA$^{(a)}$ |
| 14.9  |     $<0.75$     |     $0.40 \times 0.17$     |  UL  | VLA$^{(a)}$ |
| 19.0  |  $1.7 \pm 0.7$  |     $16.1 \times 8.6$      |  UL  |  $^{(b)}$   |
| 21.0  |  $1.5 \pm 0.7$  |     $14.3 \times 7.8$      |  UL  |  $^{(b)}$   |
| 22.5  |  $1.2 \pm 0.4$  |     $0.39 \times 0.23$     |  UL  | VLA$^{(a)}$ |
| 22.5  |  $1.9 \pm 0.3$  |      $3.8 \times 1.7$      |  UL  |  $^{(b)}$   |
| 43.3  |  $3.1 \pm 1.2$  |      $0.3 \times 0.1$      | yes  |  $^{(b)}$   |
| 90.5  | $1.72 \pm 0.12$ |     $0.25 \times 0.22$     | yes  |  $^{(b)}$   |
| 92.4  | $1.92 \pm 0.13$ |     $0.25 \times 0.21$     | yes  |  $^{(b)}$   |
| 102.5 | $1.64 \pm 0.13$ |     $0.23 \times 0.19$     | yes  |  $^{(b)}$   |
| 104.5 | $1.59 \pm 0.13$ |     $0.22 \times 0.19$     | yes  |  $^{(b)}$   |
| 138.0 | $1.71 \pm 0.14$ |     $0.17 \times 0.14$     | yes  |  $^{(b)}$   |
| 139.9 | $1.54 \pm 0.12$ |     $0.18 \times 0.15$     | yes  |  $^{(b)}$   |
| 150.0 | $1.44 \pm 0.12$ |     $0.16 \times 0.13$     | yes  |  $^{(b)}$   |
| 151.8 | $1.57 \pm 0.12$ |     $0.16 \times 0.13$     | yes  |  $^{(b)}$   |
| 213.0 | $1.35 \pm 0.10$ |     $0.12 \times 0.10$     | yes  |  $^{(b)}$   |
| 215.0 | $1.27 \pm 0.10$ |     $0.12 \times 0.09$     | yes  |  $^{(b)}$   |
| 229.0 | $1.26 \pm 0.10$ |     $0.11 \times 0.09$     | yes  |  $^{(b)}$   |
| 231.0 | $1.22 \pm 0.09$ |     $0.11 \times 0.09$     | yes  |  $^{(b)}$   |
| 599.6 |  $184 \pm 25$   |        $7 \times 7$        |  UL  |  $^{(c)}$   |
| 856.6 |  $486 \pm 51$   |        $7 \times 7$        |  UL  |  $^{(c)}$   |
| 1199  |  $951 \pm 67$   |        $7 \times 7$        |  UL  |  $^{(c)}$   |

: Flux densities and sizes of the flux extraction regions for NGC 985. The Type column indicates if the values were used for the fit as observed (yes), considered as upper limits (UL) or lower limits (LL). References: $^{(a)}$this work; $^{(b)}$(cite: Inoue2018); $^{(c)}$(cite: Ichikawa2019).

## NGC 1068

This galaxy is located at $D \approx 14.6$ Mpc ($z=0.0033$) and hosts an SMBH with $M_\mathrm{BH} = (1.66\pm0.01)\times10^7$ M$_\odot$(cite: Gallimore2024). This source has been the subject of very extensive research, given that it was the first RQ galaxy to be identified as a neutrino source (cite: IceCube2022). It has also been extensively studied in X-rays, revealing the presence of a corona (cite: Bauer2015). Furthermore, (cite: Inoue2020) modelled the radio continuum data and concluded that the synchrotron emission from the corona was responsible for the sub-mm emission detected by ALMA, which means that the corona peaks at a rather high frequency in this source compared to others. In a more recent work, (cite: Mutie2025) presented a consistent SED of the source matched in resolution and *uv*-coverage, confirming the presence of corona emission. For completeness, we reproduce the fluxes from their work in Table [6](#table:ngc1068_fluxes).

The nuclear region of this source is particularly complex, and so is its SED at low frequencies (cite: Mutie2025). For this reason, here we consider only high-resolution observations at $\nu \geq 15$ GHz. Due to the lack of FIR data to constrain the dust component, we fix $\beta=1.78$ and $\nu_{\tau_1}=800$ GHz as with the other sources. We refer to (cite: Garcia-Burillo2016) for a discussion of the dust emission, although we caution that these authors did not take into account the coronal emission in their analysis. In addition, we fix $\alpha_\mathrm{sy}=-0.5$ as otherwise the spectral index hits the hard limit set on $-0.5$. We obtain $r_\mathrm{c}=67.5 \pm 5.5$ ($R_\mathrm{c}\approx 0.065$ ld) and $\log{\delta}=-0.98 \pm 0.13$, leading to $B \sim 158$ G and $\sigma \sim 1.1$. The corona SED peaks at $\nu_\mathrm{p} \simeq 568 \pm 55$ GHz, with a peak flux density of $S_\mathrm{p} = 10.1\pm1.9$ mJy, and has a bolometric synchrotron luminosity of $L_\mathrm{c} \approx 4.4\times10^{39}$ erg s$^{-1}$. Given that the peak frequency is much greater than 100 GHz, we estimate the hard X-ray luminosity using the relation from (cite: Kawamuro2022); we obtain a luminosity $L_\mathrm{14-150\,keV}\approx 2.3\times 10^{43}$ erg s$^{-1}$, corresponding to an Eddington ratio of $\lambda_\mathrm{Edd} \sim 0.011$. The cornerplot of the fit is shown in Fig. [16](#fig:ngc1068_cornerplot). We note that this fit is quite similar to the one obtained by (cite: Inoue2020) and (cite: Mutie2025).

|       |                |                            |      |          |
|:-----:|:--------------:|:--------------------------:|:----:|:--------:|
| $\nu$ |    $S_\nu$     | $\theta_1 \times \theta_2$ | Type |   Ref    |
| (GHz) |     (mJy)      |        (arcsec$^2$)        |      |          |
|  15   |   $17 \pm 1$   |      $0.1 \times 0.1$      |  UL  | $^{(a)}$ |
| 18.9  |  $13 \pm 0.1$  |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
| 19.4  | $12.6 \pm 0.1$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
| 19.9  | $12.5 \pm 0.1$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
| 21.9  | $12.1 \pm 0.1$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
| 22.3  | $12.5 \pm 0.1$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
| 22.9  | $12.0 \pm 0.1$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  94   | $11.0 \pm 0.6$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  100  | $10.2 \pm 0.5$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  241  | $10.6 \pm 0.6$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  256  | $9.9 \pm 0.1$  |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  345  | $16.1 \pm 0.3$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  357  | $13.9 \pm 0.1$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  477  | $18.7 \pm 0.5$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  483  | $19.6 \pm 0.4$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  688  | $20.0 \pm 2.5$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  697  | $17.0 \pm 1.7$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |
|  706  | $16.5 \pm 1.9$ |     $0.06 \times 0.06$     | yes  | $^{(a)}$ |

: Flux densities and sizes of the flux extraction regions for NGC 1068. The Type column indicates if the values were used for the fit as observed (yes), considered as upper limits (UL) or lower limits (LL). References: $^{(a)}$(cite: Mutie2025).

## NGC 3227

This galaxy located at $D\approx 23$ Mpc (cite: Ricci2023) hosts a $M_\mathrm{BH} = 4.2\times 10^7$ M$_\odot$ SMBH (cite: Behar2015). (cite: Behar2015) showed that this source has a significant excess at $\sim$100 GHz. (cite: Sani2012) reported its flux density at 3 mm as observed by the Plateau de Bure with a $\sim$1" resolution. In addition, flux densities from ALMA observations at B6 and B7 were reported in (cite: Alonso-Herrero2019). According to the very high angular resolution observations at B3 in (cite: Ricci2023), the flux from the core region is $\sim$0.85 mJy. The dust component is poorly constrained due to a very bright FIR flux from the whole galaxy (cite: Ciesla2012). However, (cite: Alonso-Herrero2019) fitted the IR SED with a dust model that has a flux of $\sim$10 mJy at $10^3$ GHz (their Fig. 4), so that we can at least check that our model fitting is consistent with that derived independently using dust modelling of mid-IR low-resolution observations. Unfortunately, it is not possible to fit a dataset with very high angular resolution ($<0.1"$) due to the limited number of data points. We thus use as reference points with resolutions $\sim$0.4"–1", which is not optimal for detecting the relatively faint corona emission. Thus, the properties of the corona are only loosely constrained as $r_\mathrm{c}=67^{+48}_{-26}$ ($R_\mathrm{c}\approx 0.06$ ld) and $\log{\delta}=-2.07^{+0.56}_{-0.48}$, leading to $B \sim 46$ G and $\sigma \sim 0.09$. The corona SED component peak is very poorly constrained at $\nu_\mathrm{p} = 233 \pm 91$ GHz, with a peak flux density of $S_\mathrm{p} = 0.94\pm0.48$ mJy, and has a bolometric synchrotron luminosity of $L_\mathrm{c} \approx 3\times10^{38}$ erg s$^{-1}$. Interestingly, the source is undetected in Q band with the VLA in A array configuration (project code AG568), giving an UL to the compact emission produced at 43.3 GHz, which is consistent with the SED fit of the corona component. We estimate a hard X-ray luminosity $L_\mathrm{14-150\,keV}\approx 8\times 10^{42}$ erg s$^{-1}$, corresponding to an Eddington ratio of $\lambda_\mathrm{Edd} \sim 0.004$. The cornerplot of the fit is shown in Fig. [17](#fig:ngc3227_cornerplot).

|       |                  |                            |      |              |
|:-----:|:----------------:|:--------------------------:|:----:|:------------:|
| $\nu$ |     $S_\nu$      | $\theta_1 \times \theta_2$ | Type |     Ref      |
| (GHz) |      (mJy)       |        (arcsec$^2$)        |      |              |
| 0.887 | $117.0 \pm 15.0$ |       $25 \times 25$       |  UL  | RACS$^{(c)}$ |
|  1.4  |  $82.7 \pm 0.2$  |      $5.7 \times 5.7$      |  UL  |   $^{(a)}$   |
|  1.4  |  $78.2 \pm 5.0$  |      $0.3 \times 0.3$      | yes  |   $^{(a)}$   |
|  1.7  | $1.22 \pm 0.12$  |   $0.0059 \times 0.0059$   |  LL  |   $^{(e)}$   |
|  3.0  |  $41.4 \pm 0.5$  |     $2.71 \times 2.67$     |  UL  | VLA$^{(c)}$  |
|  5.0  |  $0.6 \pm 0.07$  |   $0.0012 \times 0.0012$   |  LL  |   $^{(e)}$   |
|  5.0  |  $15.0 \pm 2.0$  |     $0.33 \times 0.33$     | yes  |   $^{(a)}$   |
|  5.0  |  $35.0 \pm 0.7$  |       $15 \times 15$       |  UL  |   $^{(a)}$   |
|  6.0  | $7.89 \pm 0.44$  |     $0.30 \times 0.23$     |  LL  |   $^{(g)}$   |
| 8.46  |  $15.4 \pm 0.5$  |      $2.6 \times 2.6$      |  UL  | VLA$^{(c)}$  |
|  8.5  |  $12.2 \pm 1.3$  |      $0.2 \times 0.2$      |  LL  |   $^{(a)}$   |
| 10.0  | $3.75 \pm 0.20$  |     $0.18 \times 0.16$     |  LL  |   $^{(g)}$   |
| 14.9  |  $6.5 \pm 1.1$   |     $0.89 \times 0.56$     | yes  | VLA$^{(c)}$  |
|  15   |  $4.7 \pm 0.3$   |     $0.13 \times 0.13$     |  LL  |   $^{(a)}$   |
|  22   |  $6.95 \pm 1.4$  |      $6.0 \times 6.0$      |  UL  |   $^{(f)}$   |
|  22   |  $4.13 \pm 0.8$  |      $1.0 \times 1.0$      |  UL  |   $^{(f)}$   |
| 43.34 |     $<0.121$     |    $0.043 \times 0.028$    |  no  | VLA$^{(c)}$  |
|  89   | $1.79 \pm 0.12$  |     $1.15 \times 1.05$     | yes  |   $^{(d)}$   |
|  95   |  $4.1 \pm 0.2$   |      $2.2 \times 2.2$      |  UL  |   $^{(b)}$   |
| 95.2  |  $2.1 \pm 0.7$   |     $0.66 \times 0.45$     |  UL  | ALMA$^{(c)}$ |
| 97.5  | $1.28 \pm 0.35$  |     $0.13 \times 0.09$     |  LL  | ALMA$^{(c)}$ |
| 107.9 | $1.27 \pm 0.25$  |     $0.16 \times 0.11$     |  LL  | ALMA$^{(c)}$ |
|  230  |  $0.7 \pm 0.1$   |      $0.2 \times 0.2$      |  LL  |   $^{(b)}$   |
|  230  |  $1.7 \pm 0.2$   |      $0.5 \times 0.5$      | yes  |   $^{(b)}$   |
|  350  |  $0.9 \pm 0.1$   |      $0.2 \times 0.2$      |  LL  |   $^{(b)}$   |
|  350  |  $2.0 \pm 0.2$   |      $0.5 \times 0.5$      | yes  |   $^{(b)}$   |
|  485  | $1.49 \pm 0.64$  |     $0.16 \times 0.12$     |  LL  | ALMA$^{(c)}$ |
|  600  |  $1815 \pm 68$   |      $>10 \times 10$       |  UL  |   $^{(h)}$   |

: Flux densities and sizes of the flux extraction regions for NGC 3227. The Type column indicates if the values were used for the fit as observed (yes), considered as upper limits (UL) or lower limits (LL). References: $^{(a)}$(cite: Behar2015); $^{(b)}$(cite: Alonso-Herrero2019); $^{(c)}$this work; $^{(d)}$(cite: Sani2012); $^{(e)}$(cite: Bontempi2012); $^{(f)}$(cite: Smith2020); $^{(g)}$(cite: Sargent2025); $^{(h)}$(cite: Ciesla2012).

# Parameter space and cornerplots

We sample a broad range in the parameter space to ensure that all possible solutions are explored. A list of parameters and their allowed ranges is presented in Table [\[table:parameters\]](#table:parameters). We highlight that we fit the logarithm of those parameter that can spread over several orders of magnitude (namely the normalisations and $\delta$).

We show the cornerplots for all the SED fits in Figs. [11](#fig:grs_cornerplot)–[17](#fig:ngc3227_cornerplot). The top panels of each plot show the 1-D distributions of the individual parameters, with the orange line marking the position of the median, and the dashed lines the 1-$\sigma$ confidence interval.

![](Figures/posterior_GRS1734.pdf)

![](Figures/posterior_IC4329A.pdf)

![](Figures/posterior_MCG-6-30-15.pdf)

![](Figures/posterior_MCG+08-11-11.pdf)

![](Figures/posterior_NGC985.pdf)

![](Figures/posterior_NGC1068.pdf)

![](Figures/posterior_NGC3227.pdf)

[^1]: All frequencies are given in the rest frame. For spectral indices we adopt the convention $S_\nu \propto \nu^{\alpha}$.

[^2]: <https://github.com/bmargalit/thermal-synchrotron>, with the correction later introduced in (cite: Margalit2024).

[^3]: If a two-temperature plasma is assumed for the corona, for $r_\mathrm{c} \sim 140$ we expect an ion temperature of $T_\mathrm{i} \sim 1.1$ MeV (cite: Inoue2024), and thus a total thermal pressure of $P_\mathrm{th} \sim (1 + T_\mathrm{i}/T_\mathrm{c}) \, U_\mathrm{th,e} / a(\Theta) \sim 5 U_\mathrm{th,e}$.

[^4]: <https://github.com/santimda/sed_fitter_BHcorona>

[^5]: <https://almascience.nrao.edu/proposing/proposers-guide#autotoc-item-autotoc-82>

[^6]: <https://www.skao.int/en>

[^7]: <https://www.vla.nrao.edu/cgi-bin/nvas-pos.pl>

[^8]: <http://cutouts.cirada.ca/>

[^9]: <https://ngvla.nrao.edu>

[^10]: <https://cartavis.org/>

</paper>

Write the methods card for this paper.