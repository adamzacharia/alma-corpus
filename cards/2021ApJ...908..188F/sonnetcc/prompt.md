# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...908..188F\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...908..188F",
 "title": "A Long Stream of Metal-poor Cool Gas around a Massive Starburst Galaxy at z = 2.67",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Fu, Hai",
 "n_authors": 8,
 "arxiv_id": "2101.06273",
 "doi": "10.3847/1538-4357/abdb32",
 "alma_projects_linked_by_archive": [
  "2015.1.00131.S",
  "2018.1.00548.S"
 ]
}
```

Paper text:
<paper>
# A Long Stream of Metal-Poor Cool Gas around a Massive Starburst Galaxy at z = 2.67

## Abstract

We present the first detailed dissection of the circumgalactic medium (CGM) of massive starburst galaxies at $z > 2$. Our target is a submillimeter galaxy (SMG) at $z=2.674$ that has a star formation rate of 1200 $M_\odot\,{\rm yr}^{-1}$ and a molecular gas reservoir of $1.3\times10^{11}$ $M_\odot$. We characterize its CGM with two background QSOs at impact parameters of 93 kpc and 176 kpc. We detect strong H i and metal-line absorption near the redshift of the SMG toward both QSOs, each consisting of three main subsystems spanning over 1500 km s$^{-1}$. The absorbers show remarkable kinematic and metallicity coherence across a separation of $\sim$86 kpc. In particular, the cool gas in the CGM of the SMG exhibits high H i column densities ($\log N_{\rm HI}/{\rm cm}^{-2} = 20.2, 18.6$), low metallicities (${\rm [M/H]} \approx -2.0$), and similar radial velocities ($\delta v \sim -300$ km s$^{-1}$). While the H i column densities match previous results on the CGM around QSOs at $z > 2$, the metallicities are lower by more than an order of magnitude, making it an outlier in the line width$-$metallicity relation of damped Ly$\alpha$ absorbers. The large physical extent, the velocity coherence, the high surface density, and the low metallicity are all consistent with the cool, inflowing, and near-pristine gas streams predicted to penetrate hot massive halos at $z > 1.5$. We estimate a total gas accretion rate of $\sim$100 $M_\odot\,{\rm yr}^{-1}$ from three such streams, which falls short of the star formation rate but is consistent with simulations. At this rate, it takes about a gigayear to acquire the molecular gas reservoir of the central starburst.

Department of Physics & Astronomy, University of Iowa, Iowa City, IA 52242 Institute for Astronomy, University of Hawaii, Honolulu, HI 96822 National Radio Astronomy Observatory, Charlottesville, VA, 22903 Department of Astronomy and Astrophysics, UCO/Lick Observatory, University of California, Santa Cruz, CA 95064 Astronomy Department, California Institute of Technology, Pasadena, CA 51125 Department of Physics and Astronomy, University of California, Riverside, CA 92521 Department of Physics and Astronomy, University of California, Irvine, CA 92697 Department of Astronomy, University of Florida, Gainesville, FL, 32611

# Introduction

The global gas supply for in situ star formation is a central question in galaxy formation and evolution, because star formation and merging are the two primary channels through which galaxies grow (cite: Oser10). According to spherical hydrodynamical models (cite: Birnboim03) and cosmological simulations (cite: Keres05), stable accretion shocks are established near the virial radius when a dark matter (DM) halo grows to a mass threshold of $M_{\rm shock} = 2-3\times10^{11}$ $M_\odot$. So in massive halos, a significant fraction of the accreted gas is expected to be shock-heated to the virial temperature ($T_{\rm vir} = 8\times10^6~(M_{\rm halo}/10^{13}~M_\odot)^{2/3}$ K) and develops an atmosphere of hot diffuse gas. The virial shock effectively cuts off the fuel supply for star formation, because of the inefficient radiative cooling of the hot gas even in the denser inner regions (cite: Keres09). But at high redshift, narrow filaments of cool gas ($T \lesssim 10^5$ K) from the cosmic web may penetrate the hot atmospheres of rare, massive halos without ever being shock-heated to the virial temperature, thanks to the lower masses of typical halos at higher redshifts that define the width of the filaments (cite: Dekel06; Dekel09). In fact, this *cold mode* accretion may dominate over the *hot mode* accretion (radiative cooling of shock-heated virialized gas) at all halo masses at $z > 2$ (cite: Keres09).

In emission, the predicted cold-mode accretion streams (or “cold streams” in short) feeding high-redshift massive galaxies may appear as giant filamentary Ly$\alpha$ nebulae around QSOs (cite: Weidinger04; Cantalupo14; Martin15; Martin19a) and in dense protocluster environments (cite: Moller01; Hennawi15; Umehata19; Li19a; Daddi20). However, it has been difficult to rule out outflows as the alternative interpretation, especially when QSO photoionization contributes to the Ly$\alpha$ emission and the chemical abundance of the nebulae cannot be easily measured.

In absorption, cold streams can be detected and distinguished from other gaseous components based on neutral hydrogen (H i) column density, kinematics, and particularly chemical abundance (cite: Fumagalli11a; Theuns21).

In this project, we have selected a sample of massive starbursts at high redshifts in the vicinity of background QSOs to trace the cool gas supply in these early massive halos. There, the problem of gas supply is the most acute because of the extremely short gas exhaustion timescale. We then utilize the absorption-line spectra of background QSOs to characterize the physical state of their circumgalactic medium (CGM) – the gas between the inner regions of galaxies and the diffuse intergalactic medium (IGM) – and to search for large-scale cool gas reservoirs. In this section, we review our knowledge of the target galaxy sample and QSO absorption-line systems in the literature. These earlier studies have motivated this project and will provide valuable reference samples that can be compared with the system dissected in this work.

## Submillimeter Galaxies

Heated dust in the interstellar medium cools by emitting a modified blackbody spectrum (MBB; $S_\nu \propto (1-e^{-\tau_\nu})B_\nu(T)$) with temperatures in the range $10~{\rm K} \lesssim T \lesssim 100~{\rm K}$, forming the far-infrared (IR) hump in the spectral energy distribution (SED) of a galaxy. At any given frequency along the Rayleigh-Jeans tail where the dust should be optically thin, the observed flux density ($S_{\nu,\rm obs}$) of the MBB is proportional to the dust mass ($M_{\rm dust}$), the dust temperature ($T$), and the redshift ($z$) — $$\begin{align}
S_{\nu,{\rm obs}} &\propto M_{\rm dust}~T~(1+z)^{\beta-1}~\nu_{\rm obs}^{2+\beta}/d_A(z)^2 \nonumber \\ \
&\propto M_{\rm dust}~T~(1+z)^{\beta-1},
\end{align}$$ where $d_A(z)$ is the angular diameter distance at redshift $z$ (which varies by only 22% between $z = 1$ and $z = 4$) and $\beta \approx 2$ is the dust emissivity parameter ($\kappa_\nu \propto \nu^\beta$). Therefore, galaxies selected at long wavelengths, such as the (sub)millimeter regime, preferentially have higher dust mass, higher dust temperature, and are at higher redshift than galaxies selected at shorter wavelengths. Furthermore, holding the metallicity ($Z_{\rm gas}$) constant, high dust mass together with high temperature implies that the galaxies are gas-rich ($M_{\rm gas} = M_{\rm dust}/Z_{\rm gas}$) and have high star-formation efficiency (${\rm SFE} = {\rm SFR}/M_{\rm gas}$, where SFR is the star formation rate), because $$\begin{equation}
T^4 \propto L_{\rm bol}/M_{\rm dust} \propto {\rm SFR}/(Z_{\rm gas} M_{\rm gas}),
\end{equation}$$ a result from the Stefan-Boltzmann law.

Indeed, follow-up observations of the brightest galaxies selected at 850 $\mu$m ($S_{850} \gtrsim 3$ mJy), the submillimeter galaxies (SMGs; (cite: Smail97; Barger98; Blain02)), have revealed a significant population of gas-rich starburst galaxies that contribute almost as much to the cosmic SFR density as UV-selected Lyman break galaxies at $z = 2-3$ (cite: Chapman05; Casey14). The SMGs are mature (cite: Hainline11; Michalowski12; Targett13), metal-rich (cite: Swinbank04), gas-rich (cite: Greve05; Tacconi08; Ivison11; Bothwell13), extreme star-forming systems ($\overline{\rm SFR} \sim 500$ $M_\odot\,{\rm yr}^{-1}$) with a broad redshift distribution that peaks at $\langle z \rangle \sim 2.5$ (cite: Chapman05; Wardlow11). The molecular gas reservoirs are turbulent, likely due to starburst-driven galactic outflows (cite: Falgarone17). Notably, the nearly linear relation between CO and IR luminosities implies an almost constant gas depletion timescale of $\tau_{\rm dep} \equiv M_{\rm mol}/{\rm SFR} \sim 0.1~{\rm Gyr}$ (cite: Bothwell13), which is far shorter than that of normal star-forming galaxies on the main sequence (cite: Tacconi18), justifying the usage of “starburst” in describing SMGs[^1].

On the other hand, the autocorrelation length for SMGs of $\sim$11 Mpc at $z = 1-3$ implies a characteristic dark matter halo mass of $M_{\rm halo}\sim 9\times10^{12}$ $M_\odot$ for $h=0.7$ (cite: Hickox12). The high halo mass is consistent with the high maximum rotation velocities ($V_{\rm circ} \gtrsim 500$ km s$^{-1}$) observed in several bright SMGs with spatially resolved kinematics (cite: Hodge12; Xue18). For Navarro–Frenk–White (NFW) halos (cite: Navarro96) at $z = 2.5$, the halo mass is directly related to the maximum circular velocity by a power law: $M_{\rm halo}= 10^{13}~M_\odot~(V_{\rm circ}/500~{\rm km~s}^{-1})^3$ (cite: Bullock01; Klypin11). Such a mass is well above the threshold mass for stable virial shocks ($M_{\rm shock}$), and atmospheres of hot gas at the virial temperature ($\sim8\times10^6$ K) are expected to fill the halo. But as previously discussed, at the early epoch of the SMGs, cool gas filaments can penetrate their halos, which could potentially deliver enough gas to build the molecular gas reservoir that supports the ongoing intense star formation.

## QSO Absorption-line Systems

Ever since the discovery of multiple absorption redshifts in QSO spectra (cite: Burbidge68), quasar absorption-line spectroscopy has become a powerful tool to study diffuse gas at various phases in the IGM and the CGM, which account for the majority of the baryonic mass in the universe (see (cite: Peroux20) for a recent review). The optical depth at the Lyman limit ($\lambda_{\rm rest} = 912$ Å) reaches unity when the H i column density reaches $\log N_{\rm HI}= 17.2$[^2] Accumulating evidence suggests that these optically thick absorbers trace material in virialized structures (cite: Fumagalli16; Lehner16), while the optically thin absorbers in the Ly$\alpha$ forest (LYAF) likely trace the IGM (cite: Rauch98). Due to their distinct physical properties, the optically thick absorbers are empirically subdivided into three categories based on their H i column densities: the Lyman limit systems (LLSs, $17.2 \leq \log N_{\rm HI}< 19$) that are mostly ionized, the damped Ly$\alpha$ absorbers (DLAs; $\log N_{\rm HI}\geq 20.3$) that are mostly neutral, and lastly the super-LLSs or sub-DLAs[^3] for the intermediate category of absorbers with $19 \leq \log N_{\rm HI}< 20.3$. Unlike absorbers at lower column densities, gas in the DLAs is mostly neutral. In fact, at all epochs since $z \sim 5$, the DLAs have contained most of the neutral gas that is poised to fuel star formation in galaxies (cite: Wolfe05).

## Emission$-$Absorption Connection

Because the H i column density threshold of DLAs was set by the observed limit of 21 cm emission at the cutoff boundaries of nearby spiral disks (cite: Wolfe86), the DLAs were expected to arise from gas-rich galactic disks even at high redshifts. However, the emission counterparts (i.e., the DLA galaxies) of most DLAs have eluded detection. Among the limited detections in optical searches, it is found that the DLA galaxies are very faint ($r \gtrsim 24$) and close ($\sim$2$''$) to the QSOs (cite: Steidel92; Fynbo08), making it difficult to measure their redshifts. To improve efficiency, searches of the emission counterparts of DLAs have focused on DLAs that are clearly chemically enriched (\[M/H\] $> -0.7$) (cite: Fynbo13; Jorgenson14) or sightlines that pass through multiple DLAs (cite: Srianand16). But still, only 16 $z > 1.9$ DLA host galaxies have been identified via emission lines in the optical (cite: Krogager17; Moller20) over an extensive search period of nearly three decades. The advent of (sub)millimeter interferometers such as the Atacama Large Millimeter/submillimeter Array (ALMA) and the Very Large Array (VLA) have significantly improved the success rate of identifying absorption-selected galaxies, because (1) the contrast between DLA host galaxies and the QSO is more favorable at longer wavelengths, and (2) the interferometers have an unattenuated view over a wide FoV (thus does not require lucky slit placements). In only a few years, there have been four $z \sim 4$ DLA galaxies identified in \[C ii\] 158 $\mu$m (cite: Neeleman17; Neeleman19) and five $z \sim 2$ DLA in CO(4-3) and CO(3-2) (cite: Kanekar20). Interestingly, the DLA galaxies previously identified in the optical/near-IR are not detected in CO and *vice versa* (cite: Kanekar20), indicating that observations at different wavelength are complementary to one another and that H i-absorption-selection tags gas-rich galaxies of all types. Some DLAs also have multiple emission counterparts that are consistent with the absorption redshifts, suggesting a group/cluster environment (cite: Fynbo18).

The opposite approach from the searches of DLA galaxies is to start from an emission-selected galaxy sample and look for corresponding absorption lines in the spectra of nearby background QSOs. This approach requires chance alignments of foreground galaxies and background QSOs, thus requires large samples of both populations. The implicit assumption is that the emission-selected galaxies have similar CGM properties, and therefore, the absorption signals obtained from different galaxy-QSO pairs can be combined to provide meaningful average properties of a typical halo in the studied galaxy population. The searches for absorbers are no longer limited to DLAs, but to all optically thick absorbers (i.e., LLSs and sub-DLAs). At $z \gtrsim 2$, the targeted galaxy populations have included Lyman Break Galaxies (LBGs) (cite: Simcoe06; Rudie12; Rudie13; Crighton13; Crighton15) and QSOs (cite: Hennawi06a; Prochaska13; Lau16). In addition, using a sample of projected QSO pairs where one of the QSOs intercepts a DLA, (cite: Rubin15) have probed the CGM of the DLA galaxy without identifying the DLA galaxy in emission. These studies have mapped out the H i column density, the ion ratios, and the metallicity as a function of impact parameters ($R_\bot$). The covering fraction of optically thick H i absorbers increases from $\sim$30% around LBGs (cite: Rudie12) and DLAs (cite: Rubin15) to $\gtrsim$60% around QSOs (cite: Prochaska13) for sightlines out to $R_\bot = 100-200$ kpc (comparable to the virial radius of DM halos with $M_{\rm halo}= 10^{12.5}$ $M_\odot$ at $z = 2$: $R_{\rm vir} = 154$ kpc). The abundance of neutral gas in the halos of QSOs is particularly puzzling. Simulations predict that such massive halos are dominated by a hot $T\sim 10^7\,{\rm K}$ virialized plasma and a significantly lower covering factor of optically thick H i absorbers (cite: Faucher-Giguere15).

The unexpectedly large covering factor of LLSs around $z \sim 2$ QSOs and the difficulty of reproducing the SMG population in galaxy formation models, could both be symptoms of the same problem. Attempting to reduce this tension between observations and theory, more recent cosmological zoom-in simulations have implemented recipes of stronger and presumably more realistic stellar feedback, which manages to preserve cool gas reservoirs in the accreted sub-halos during earlier phases of star formation before their infall into the massive halo. The presence of these gas-rich sub-halos increases the cool gas covering factor around QSOs (cite: Faucher-Giguere16) and their prolonged bombardment to the central galaxy leads to a rising star formation history that eventually produces SMGs between $2 < z < 3$ (cite: Narayanan15; Lovell21).

## Organization

QSO absorption-line spectroscopy combined with efficient emission-line mapping provides a powerful method to link star-forming galaxies with the neutral gas reservoir that may fuel future star formation. Our understanding of the formation and evolution of massive galaxies is severely limited by the lack of observational constraints of the CGM of SMGs. The advent of *Herschel* large-scale far-infrared surveys have provided an opportunity to use projected SMG$-$QSO pairs to probe the CGM of SMGs. In this paper, we focus on one particularly interesting system – GAMA J0913$-$0107 – where two background QSOs have revealed an unusually H i-rich CGM around a luminous SMG.

The main text of the paper is organized as follows. We first provide an orientation of the system in § [2](#sec:system), then proceed with a detailed study of the emission sources (§ [3](#sec:smg)) and the absorption-line systems (§ [4](#sec:qsos)), before finally drawing connections between the absorbers and their emission counterparts in § [5](#sec:connection). We conclude the paper with a summary of the main results and a discussion of the implications in § [6](#sec:summary). To keep the main text focused on the SMG$-$DLA system at $z \approx 2.67$, we move additional material to the *Appendices*. We analyze the nearby optical source to the SMG and its potential lensing effect in Appendix [7](#sec:fakecp), present the methodology and result of our blind search of line emitters in the ALMA band-3 data in Appendix [8](#sec:blindCO), give an inventory of the line-of-sight contaminating absorbers at other redshifts in Appendix [9](#sec:otherabs), provide tables of detailed ionic column density and metallicity measurements in Appendix [10](#sec:aodmtables), and describe our attempt to detect CO emission from faint optical sources near QSO1 and the identification of Comp b in Appendix [11](#sec:optCO).

Throughout this paper, we adopt a model optimization method that combines a heuristic $\chi^2$ minimization algorithm with a Markov Chain Monte Carlo (MCMC) algorithm (hereafter, the “amoeba + mcmc” method). It begins with using the downhill simplex method amoeba (cite: Press92) with simulated annealing amoeba_sa to find the solution that minimizes the residual. Although computationally more expensive than other least-$\chi^2$ solvers (e.g., the Levenberg-Marquardt technique), amoeba_sa has the advantage of avoiding being trapped in local minima in a multidimensional parameter space. This advantage is particularly important in more complex problems such as fitting the H i absorption profiles with many Voigt profiles (§ [4.2](#sec:voigt)). Next, starting from the minimum-$\chi^2$ solution of amoeba_sa, we use the Differential Evolution MCMC algorithm (cite: Ter-Braak06) implemented in exofast_demc (cite: Eastman13; Eastman19) to obtain the final solution and the statistical uncertainties of the parameters. The exofast_demc routine first determines the stepping scale of each parameter by varying it from the minimum $\chi^2$ solution until the $\chi^2$ increases by one. It then starts the chains from positions that are randomly offset from the minimum $\chi^2$ solution. The routine stops when the chains are considered well-mixed and the steps in the initial “burn-in” phase are removed. The marginalized 1$\sigma$ confidence interval of each parameter is determined from the values at 15.8 and 84.1 percentiles of the concatenated chains, and the *median* values are adopted as the *formal* solution. Parameters derived from the model parameters are treated likewise: their formal values and uncertainties are calculated from the 50, 15.8, and 84.1 percentiles of the array directly calculated from the chains of model parameters.

We assume the $\Lambda$CDM cosmology with $\Omega_{\rm m}=0.3$, $\Omega_\Lambda=0.7$, and $h \equiv H_0/(100~{\rm km~s}^{-1}~{\rm Mpc}^{-1}) = 0.7$ and quote proper/physical distances.

# System Overview

|  |  |  |  |  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Designation | Short Name | R.A. (J2000) | Decl. (J2000) | $z$ | $L^\prime_{\rm CO3-2}$ | $\theta_1$ | $\theta_2$ | $R_{\bot,1}$ | $R_{\bot,2}$ |
|  |  | (deg) | (deg) |  | (K km s$^{-1}$ pc$^2$) | (arcsec) | (arcsec) | (kpc) | (kpc) |
| ALMA J091339.55$-$010656.4 | SMM J0913 | 138.4147767 | $-$1.1156772 | 2.674 | $6.5\times10^{10}$ | 11.7 | 22.1 | 93.1 | 175.5 |
| ALMA J091338.28$-$010643.8 | Comp a | 138.4094849 | $-$1.1121639 | 2.6747 | $6.3\times10^9$ | 23.3 | 24.8 | 185.1 | 197.1 |
| ALMA J091338.49$-$010705.5 | Comp b | 138.4103803 | $-$1.1181869 | 2.6884 | $6.8\times10^8$ | 7.4 | 4.1 | 58.9 | 32.2 |
| — | — | — | — | 2.6917 | $5.3\times10^8$ | — | — | — | — |
| SDSS J091338.97$-$010704.6 | QSO1 | 138.4124260 | $-$1.1179280 | 2.9161 | ... | ... | ... | ... | ... |
| SDSS J091338.30$-$010708.6 | QSO2 | 138.4096520 | $-$1.1190520 | 2.7488 | $5.6\times10^9$ | 10.8 | ... | 85.0 | ... |

Fig. [1](#fig:fchart) illustrates the GAMA J0913$-$0107 system, where we label its major components: the SMG, its CO companions, and the two background QSOs. Table [\[tab:coords\]](#tab:coords) lists their coordinates, redshifts, CO (3$-$2) luminosities, along with the impact parameters of the QSO sightlines.

The GAMA J0913$-$0107 system is one of the 163 SMG$-$QSO pairs with *apparent* separations between 5$''$ and 30$''$, which were selected by cross-matching *Herschel*-selected SMGs with optically-selected QSOs from a compilation of spectroscopic surveys (cite: Fu16; Fu17). Located in the R.A. = 9 hr equatorial field of the *Herschel* Astrophysical Terahertz Large Area Survey (H-ATLAS) survey (cite: Eales10), the *Herschel* source at R.A. = $09^{\rm h}13^{\rm m}39^{\rm s}$, Decl. = $-01^\circ06\ensuremath{'}59\ensuremath{''}$ is detected at high S/N by SPIRE (cite: Griffin10) at 250, 350, and 500 $\mu$m, with de-boosted flux densities of $S_{250} = 52.5\pm7.4$ mJy, $S_{350} = 69.4\pm8.8$ mJy, and $S_{500} = 48.4\pm9.2$ mJy (cite: Valiante16; Fu17). The far-IR SED clearly peaks around 350 $\mu$m (i.e., “350 $\mu$m peakers”), giving a rough photometric redshift of $\sim$2.5 assuming a dust temperature of $\sim$50 K, following Wien’s displacement law for $S_\nu$ over $\lambda$: $\lambda_{\rm peak} = 102~\mu{\rm m}~(50~{\rm K}/T)~(1+z)$.

Our ALMA 345 GHz imaging pinpointed the position of the *Herschel* source (cite: Fu17), and Gemini near-IR and ALMA 94 GHz spectroscopy jointly determined a spectroscopic redshift of 2.674 (§ [3.1](#sec:specID) & [3.2](#sec:almaB3)). We designate the SMG as ALMA J091339.55$-$010656.4 or SMM J0913 in short. In addition, our ALMA 94 GHz observations detected companion galaxies in CO (3$-$2) near the redshift of the SMG: Comp a at $z = 2.6747$, and Comp b at $z = 2.6884, 2.6917$. Both are within 23$''$ of the SMG position. Comp b has two redshifts because it is a superposition of two galaxies (see § [3.5](#sec:comps)). Because *Herschel* has FWHM resolutions of 18$''$, 25$''$, and 35$''$ at 250, 350, and 500 $\mu$m, respectively, the SMG and its companions are blended in the *Herschel* images. But the contribution of the companions to the *Herschel* fluxes should be negligible given their orders-of-magnitude lower CO line luminosities.

There are *two* bright QSOs within 22$''$ of the SMG, QSO1 (SDSS J091338.97$-$010704.6, $g = 20.78$, $r = 20.38$) at $z = 2.9161$ and QSO2 (SDSS J091338.30$-$010708.6, $g = 20.71$, $r = 20.44$) at $z = 2.7488$. Both QSOs are in the background of the SMG, allowing us to probe its CGM at impact parameters of $R_\bot = 93.1$ kpc and $R_\bot = 175.5$ kpc, or approximately 0.5$\times$ and 0.9$\times$ the virial radius of a $10^{13}$ $M_\odot$ halo at $z = 2.674$ ($R_{\rm vir} = 186$ kpc). Coincidentally, strong H i and metal absorption lines near the SMG redshift have been previously detected in the QSO spectra (cite: Finley14).

When comparing the CO map with the KiDS $r$-band image in Fig. [1](#fig:fchart), we notice an $r = 21.6$ optical source just 0.8$''$ from the SMG. As we will show in Appendix [7](#sec:fakecp), it is a foreground galaxy with a spec-$z$ of $z = 0.055$ and its gravitational lensing effect on the SMG is negligible.

We also find that Comp b is just $\sim$3$''$ from an elongated optical source to the NNE. In the KiDS DR4 catalog, the optical source has a designation of J091338.527$-$010703.60 and magnitudes of $r = 23.8\pm0.1$ and $H = 22.0\pm0.3$. It has a photo-$z$ of $z_{\rm p} = 0.79^{+0.45}_{-0.06}$. Its SED shows a clear 1-magnitude drop-off between $Y$-band and $Z$-band, corresponding to a 4000 Å-break at $z \sim 1.2-1.5$, which is consistent with the maximum-likelihood photo-$z$ of $z_{\rm p} = 1.37$ in the catalog. We thus conclude that the optical source is most likely a foreground galaxy, although the extraction of an ALMA spectrum near the position of the optical source led to the identification of Comp b (Appendix [11](#sec:optCO)).

# The Submillimeter Galaxy and Its Companions

## ALMA Position and Near-IR Spectroscopy

*Herschel*/SPIRE positions have large uncertainties. A comparison between ALMA and *Herschel* positions showed a 1$\sigma$ positional offset of $\sim$4.2$''$ for sources with S/N $\sim$ 6 at 250 $\mu$m (cite: Fu17). Near-IR slit spectroscopy requires sub-arcsec positions, so we carried out 0.5$''$-resolution ALMA band-7 (345 GHz/870 $\mu$m) observations of GAMA J0913$-$0107 as part of our Cycle-3 project 2015.1.00131.S (cite: Fu17). GAMA J0913$-$0107 shared an hour-long observing session with nine other *Herschel* SMGs in the same H-ATLAS field. With four scans and 44 antennas, we accumulated a total on-source integration time of 189.5 s. A single high S/N source is detected in the $\sim$17$''$ Full Width at Half Power (FWHP) of the primary beam. It has a 870 $\mu$m flux density of $S_{870} = 7.4\pm0.5$ mJy, an offset from the *Herschel* position by 4.1$''$, and a beam-deconvolved FWHM of $0.46\ensuremath{''}\pm0.04\ensuremath{''}$ along the major axis (which corresponds to $\sim$4 kpc at $z = 2.5$).

The accurate ALMA position enabled our follow-up near-IR slit spectroscopy. Observations of SMM J0913 were carried out with Gemini near-infrared spectrograph (cite: Elias06) on 2017 Feb 19 as part of our queue program GN-2017A-Q-31. The A0-type star HIP49125 ($V$ = 7.19, $K$ = 6.553 Vega mag) was observed right after the science target to provide telluric correction and flux calibration. Because our goal was to measure the redshift, we used the cross-dispersed mode with the 32 l/mm grating to achieve a continuous wavelength coverage between 0.85 and 2.5 $\mu$m (orders 3 to 8). After applying a 30$''$ offset from an offset star to the NE, we placed the 1$''$-wide 7$''$-long slit on the ALMA 870 $\mu$m position at a position angle (PA) of 73 deg (E of N; the PA was chosen to reach a guide star). The expected spectral resolution of this configuration is $R = 510$ (FWHM = 590 km s$^{-1}$), but the actual spectral resolution may be higher depending on the source size and the seeing. We took 24 exposures of 136 s with a 3$''$-step ABBA dithering pattern. Data reduction was performed with a modified version of Spextool (cite: Cushing04) for GNIRS by K. Allers. The final coadded spectrum in Fig. [2](#fig:gnirs) includes all 24 frames and has a total on-source time of 54.4 min. We detected an emission line at $\sim$4$\sigma$-level at 2.4121 $\mu$m (heliocentric corrected, vacuum wavelength), which we identified as H$\alpha$ ($\lambda_{\rm rest} = 6564.63\,\AA$) at $z_{\rm H\alpha} = 2.6743\pm0.0003$. The \[N ii\] $\lambda$6585.28 line is undetected, likely due to the elevated background noise at its wavelength and its lower flux. Our best-fit Gaussian model yields a line ${\rm FWHM} = 230\pm60$ km s$^{-1}$ (i.e., the line is unresolved) and a line flux of $F_{\rm H\alpha} = (6.1\pm1.0)\times10^{-17}$ erg s$^{-1}$ cm$^{-2}$, which are comparable to those of the SMGs identified by the VLA (cite: Alaghband-Zadeh12; Fu16).

## ALMA CO (3$-$2) Spectral Line Imaging

To detect the molecular gas reservoir that fuels the intense star formation in the SMG, we carried out deep ALMA band-3 (100 GHz/3 mm) spectral line observations of SMM J0913 on 2018 December 10 and 15 with our Cycle 6 project 2018.1.00548.S. We tuned the four 1.875 GHz-bandwidth spectral windows to center on 92.2 (BB3), 94.0 (BB4), 104.2 (BB1), and 106.0 GHz (BB2) in dual linear polarization mode (*XX* and *YY*). We chose a spectral averaging factor of 16 to bin the Frequency Division Mode (FDM)’s input channel spacing of 0.488 MHz to an output channel spacing of 7.8125 MHz. The spectral averaging significantly reduces the output data rate and essentially eliminates the correlation between adjacent channels introduced by the Hanning window function applied to the correlation functions (see § 5.5 in the *ALMA Technical Handbook*). The resulting spectral response function is basically a top-hat function with a width of 7.8125 MHz (i.e., the output channel spacing), which corresponds to a spectral resolution of 22$-$25 km s$^{-1}$. The two lower frequency spectral windows provide a continuous frequency range between 91.27 and 94.94 GHz, which covers the CO (3$-$2) line ($\nu_{\rm rest} = 345.79599$ GHz and $\lambda_{\rm rest} = 866.96337$ $\mu$m) between $2.642 \leq z \leq 2.789$, encompassing the SMG at $z = 2.674$ and QSO2 at $z = 2.7498$. The frequency range covers a velocity window between $-2620$ and $+9240$ km s$^{-1}$ relative to the SMG redshift. The two higher frequency spectral windows provide a continuous frequency coverage between 103.27 and 106.94 GHz, which covers the CO (3$-$2) line between $2.234 \leq z \leq 2.348$ and traces the continuum emission at rest-frame frequencies around $\nu_{\rm rest} = 386$ GHz ($\lambda_{\rm rest} = 776$ $\mu$m) at $z = 2.674$.

The primary beam of the ALMA 12-m antennas has an FWHP of 62$''$ at 94 GHz. We set the field center at R.A. = $09^{\rm h}13^{\rm m}38.89^{\rm s}$, Decl. = $-01^\circ07\ensuremath{'}03.6\ensuremath{''}$, which is near the position of QSO1 but $\sim$12$''$ offset from the SMG. Three of the four planned observing sessions were executed, accumulating a total on-source time of 143.8 min with 6.05 s integrations. Either 43 or 46 12-m antennas were operational, with baselines ranging between 15.1 m and 740.5 m. The BL Lac object J0854$+$2006 served as the amplitude, bandpass, and pointing calibrator, and the flat-spectrum radio quasar J0909$+$0121 as the phase calibrator (cite: Bonato19).

## ALMA Data Processing

The raw visibility data were flagged and calibrated by the ALMA pipeline (Pipeline ver. 42030M, CASA ver. 5.4.0-68). The calibrated visibilities of the three observing sessions were then combined to form the final calibrated measurement set (MS). The pipeline worked very well. After inspecting the amplitudes of the calibrated visibilities, we found that additional flagging was only necessary for a tiny fraction of data. We used the CASA task `flagcmd` to flag the cross-correlation data of the antenna pair DA62 and DA65 in the 94.0 GHz spectral window between channels 188 and 191.

We use the CASA task `tclean` to image the calibrated visibilities of each spectral window into spectral data cubes. When visibilities are gridded into regularized $uv$-cells, we adopt natural weighting to maximize the sensitivity. The synthesized beams are on average 1.7$''$$\times$1.3$''$ in FWHM, so we set the imaging pixel size to 0.2$''$. In the spectral dimension, we retain the original channel spacing of 7.8125 MHz. The data were recorded in the Topocentric (TOPO) reference frame. Due to the motion of the Earth, every observing scan has a slightly different sampling in sky frequency. We image the data to the solar System Barycenter (BARY) reference frame to be consistent with the velocities measured in the heliocentric-corrected optical and near-IR spectra.

Significant continuum emission and a strong emission line at $\sim$94.1 GHz (in BB4) is detected at the ALMA 870 $\mu$m position of SMM J0913. To minimize the sidelobes from this bright source, we used Clark clean deconvolution algorithm with a mask consisting of a single 2$''$-radius circle centered on the SMG. The clean depth is set to be 2$\times$ the rms listed below.

For each spectral window, we generate two datacubes: one avoids interpolation in the spectral dimension by setting `interpolation = nearest` and is uncorrected for the primary beam, and the other uses linear interpolation and is corrected for the primary beam. The former is better suited for blind line searches because maps in adjacent channels remain uncorrelated, while the latter is better suited for measuring line parameters such as central frequency, width, and integrated flux. The resulting spectral cubes have a dimension of 540 pixels by 540 pixels by 240 channels. At the phase center, the sensitivities of the datacubes reach ${\rm rms} = 0.165, 0.171, 0.158, 0.155$ mJy beam$^{-1}$ channel$^{-1}$ for BB1, BB2, BB3, and BB4, respectively. The rms values are consistent with the visibility noise that we measured with `visstat` ($\sigma \sim 250$ mJy visibility$^{-1}$ channel$^{-1}$), because ${\rm rms} \sim \sigma/\sqrt{n_{\rm ch} n_{\rm pol} n_{\rm baseline} n_{\rm int}}$, where $n_{\rm ch} = 1$ (1 channel binning), $n_{\rm pol} = 2$ (2 polarizations), $n_{\rm baseline} = n_{\rm ant} (n_{\rm ant}-1)/2 = 903$ for $n_{\rm ant} = 43$ (903 baselines for 43 antennae), and $n_{\rm int} = t_{\rm on\_source}/t_{\rm int} \sim 1426$ (total number of integrations).

In addition, we generate one continuum image from the two higher frequency spectral windows (BB1 and BB2). We used the Multi-term Multi-Frequency Synthesis (`mtmfs`) clean algorithm with a linear spectral model (i.e., `nterms` = 2). Again, we used natural weighting, 0.2$''$ pixel size, and the same clean mask centered on the SMG. The sensitivity of the continuum image reaches ${\rm rms} = 7.4$ $\mu$Jy beam$^{-1}$, consistent with the rms of the spectral cubes divided by $\sqrt{n_{\rm ch}} \simeq 22$.

## SMG Properties

+-----------------------+------------------------------+--------------------------+
| Quantity              | Measurement                  | Unit                     |
+:======================+:============================:+:========================:+
| H$\alpha$ from Gemini/GNIRS                                                     |
+-----------------------+------------------------------+--------------------------+
| $z_{\rm H\alpha}$     | $2.6743(3)$                  | ...                      |
+-----------------------+------------------------------+--------------------------+
| $\Delta V_{\rm FWHM}$ | $<300$                       | km s$^{-1}$              |
+-----------------------+------------------------------+--------------------------+
| $F_{\rm H\alpha}$     | $(6.1\pm1.0)\times10^{-17}$  | erg s$^{-1}$ cm$^{-2}$   |
+-----------------------+------------------------------+--------------------------+
| $L_{\rm H\alpha}$     | $(2.9\pm0.5)\times10^{41}$   | erg s$^{-1}$             |
+-----------------------+------------------------------+--------------------------+
| SFR$_{\rm H\alpha}$   | $1.6\pm0.3$                  | $M_\odot\,{\rm yr}^{-1}$ |
+-----------------------+------------------------------+--------------------------+
| CO (3$-$2) from ALMA Band-3                                                     |
+---------------------------------------------------------------------------------+
| *Narrow Component*                                                              |
+-----------------------+------------------------------+--------------------------+
| $z_{\rm CO3-2}$       | 2.67399(3)                   | ...                      |
+-----------------------+------------------------------+--------------------------+
| $\Delta V_{\rm FWHM}$ | $249\pm8$                    | km s$^{-1}$              |
+-----------------------+------------------------------+--------------------------+
| $S_{\rm CO} \Delta V$ | $1.38\pm0.06$                | Jy km s$^{-1}$           |
+-----------------------+------------------------------+--------------------------+
| $L'_{\rm CO3-2}$      | $(5.0\pm0.2)\times10^{10}$   | K km s$^{-1}$ pc$^2$     |
+-----------------------+------------------------------+--------------------------+
| *Broad Component*                                                               |
+-----------------------+------------------------------+--------------------------+
| $z_{\rm CO3-2}$       | 2.6741(7)                    | ...                      |
+-----------------------+------------------------------+--------------------------+
| $\Delta V_{\rm FWHM}$ | $906\pm206$                  | km s$^{-1}$              |
+-----------------------+------------------------------+--------------------------+
| $S_{\rm CO} \Delta V$ | $0.41\pm0.07$                | Jy km s$^{-1}$           |
+-----------------------+------------------------------+--------------------------+
| $L'_{\rm CO3-2}$      | $(1.5\pm0.3)\times10^{10}$   | K km s$^{-1}$ pc$^2$     |
+-----------------------+------------------------------+--------------------------+
| *Total Emission*                                                                |
+-----------------------+------------------------------+--------------------------+
| $L'_{\rm CO1-0}$      | $(1.25\pm0.07)\times10^{11}$ | K km s$^{-1}$ pc$^2$     |
+-----------------------+------------------------------+--------------------------+
| $M_{\rm mol}$         | $(1.25\pm0.07)\times10^{11}$ | $M_\odot$                |
+-----------------------+------------------------------+--------------------------+
| *Intrinsic Source Size*                                                         |
+-----------------------+------------------------------+--------------------------+
| Deconv. Maj.          | $0.76\pm0.09$                | arcsec                   |
+-----------------------+------------------------------+--------------------------+
| Deconv. Min.          | $0.54\pm0.17$                | arcsec                   |
+-----------------------+------------------------------+--------------------------+

: Spectroscopy of the SMG

+--------------------+-------------------------------------+--------------------------+
| Quantity           | Measurement                         | Unit                     |
+:===================+:===================================:+:========================:+
| Herschel/SPIRE                                                                      |
+--------------------+-------------------------------------+--------------------------+
| R.A.               | 09:13:39.32                         | hms                      |
+--------------------+-------------------------------------+--------------------------+
| Decl.              | $-$01:06:58.6                       | dms                      |
+--------------------+-------------------------------------+--------------------------+
| $S_{250}$          | $52.5\pm7.4$                        | mJy                      |
+--------------------+-------------------------------------+--------------------------+
| $S_{350}$          | $69.4\pm8.8$                        | mJy                      |
+--------------------+-------------------------------------+--------------------------+
| $S_{500}$          | $48.4\pm9.2$                        | mJy                      |
+--------------------+-------------------------------------+--------------------------+
| ALMA Band-6 Continuum                                                               |
+--------------------+-------------------------------------+--------------------------+
| R.A.               | 09:13:39.55                         | hms                      |
+--------------------+-------------------------------------+--------------------------+
| Decl.              | $-$01:06:56.4                       | dms                      |
+--------------------+-------------------------------------+--------------------------+
| $S_{\rm 343.5GHz}$ | $7.4\pm0.5$                         | mJy                      |
+--------------------+-------------------------------------+--------------------------+
| Deconv. Maj.       | $0.46\pm0.04$                       | arcsec                   |
+--------------------+-------------------------------------+--------------------------+
|                    | $3.7\pm0.3$                         | kpc                      |
+--------------------+-------------------------------------+--------------------------+
| Deconv. Min.       | $0.28\pm0.06$                       | arcsec                   |
+--------------------+-------------------------------------+--------------------------+
|                    | $2.2\pm0.5$                         | kpc                      |
+--------------------+-------------------------------------+--------------------------+
| ALMA Band-3 Continuum                                                               |
+--------------------+-------------------------------------+--------------------------+
| $S_{\rm 93.1GHz}$  | $106\pm22$                          | $\mu$Jy                  |
+--------------------+-------------------------------------+--------------------------+
| $S_{\rm 105.1GHz}$ | $111\pm20$                          | $\mu$Jy                  |
+--------------------+-------------------------------------+--------------------------+
| Deconv. Maj.       | $0.68\pm0.47$                       | arcsec                   |
+--------------------+-------------------------------------+--------------------------+
| Deconv. Min.       | $0.47\pm0.23$                       | arcsec                   |
+--------------------+-------------------------------------+--------------------------+
| Modified Blackbody Fit                                                              |
+--------------------+-------------------------------------+--------------------------+
| $T$                | $44\pm7$                            | K                        |
+--------------------+-------------------------------------+--------------------------+
| $\beta$            | $2.3\pm0.2$                         | ...                      |
+--------------------+-------------------------------------+--------------------------+
| $\lambda_0$        | $98\pm24$                           | $\mu$m                   |
+--------------------+-------------------------------------+--------------------------+
| $\pi r_s^2$        | $9^{+10}_{-5}$                      | kpc$^2$                  |
+--------------------+-------------------------------------+--------------------------+
| $M_{\rm dust}$     | $(5.4\pm1.2)\times10^8$             | $M_\odot$                |
+--------------------+-------------------------------------+--------------------------+
| $L_{\rm IR}$       | $1.17^{+0.17}_{-0.11}\times10^{13}$ | $L_\odot$                |
+--------------------+-------------------------------------+--------------------------+
| SFR$_{\rm IR}$     | $1170^{+170}_{-110}$                | $M_\odot\,{\rm yr}^{-1}$ |
+--------------------+-------------------------------------+--------------------------+

: Photometry of the SMG

Fig. [3](#fig:cospec) shows the ALMA band-3 spectrum of the SMG. The spectrum is extracted with an elliptical aperture matching the beam-convolved source size. A prominent emission line peaks at $\nu_{\rm obs} = 94.12$ GHz, which we identify as the CO (3$-$2) line at $z_{\rm CO} = 2.67399\pm0.00003$. The CO detection thus confirms the H$\alpha$ redshift from the GNIRS spectrum ($z_{\rm H\alpha} = 2.6743\pm0.0003$, see § [3.1](#sec:specID)). Because the CO line is detected at a higher S/N and is less affected by dust extinction, we adopt the CO redshift for the SMG throughout the paper, i.e., $z_{\rm SMG} = z_{\rm CO} = 2.674$ (a slightly rounded-up value for simplicity).

A closer inspection of the CO (3$-$2) spectrum reveals a broad (FWHM $\sim$ 1000 km s$^{-1}$) emission-line component with a peak flux of $\sim$0.4 mJy underneath the prominent narrow component (FWHM $\sim$ 250 km s$^{-1}$). We thus model the CO spectrum with two Gaussians and compare its result with a single-Gaussian model.

We find that the improvement of the double-Gaussian model over the single-Gaussian model is highly significant. The formal double-Gaussian solution achieves a $\chi^2 = 220.2$ for a degree-of-freedom (DOF) of 209. For comparison, the formal single-Gaussian solution achieves a $\chi^2 = 251.8$ for DOF = 212. According to the $F$-test, such a difference rejects the null hypothesis, that the double-Gaussian model does not provide a significantly better fit, at a confidence level of 99.99964% or 4.6$\sigma$.

The result of the double-Gaussian fit from the “amoeba + mcmc” method is listed in Table  [1](#tab:smg_spec). The broad component has an FWHM of $\sim$900 km s$^{-1}$ and accounts for almost a quarter of the total emission-line flux. The existence of a narrow CO line on top of a broad CO line with essentially no velocity offset indicates that the SMG’s intense star-forming nucleus (the narrow component) is either embedded in a fast-rotating disk or driving a bipolar outflow (the broad component). Unfortunately, the spatial resolution of the ALMA data is inadequate to distinguish between the two scenarios. We note that such a broad CO component would not have been detected in shallower spectroscopic data that are more generally available to SMGs, so this feature may not be unique to SMM J0913.

With the redshift determined, we fit the SED between 250 $\mu$m and 3 mm from *Herschel*/SPIRE and ALMA with a modified blackbody curve. We adopt the general solution of the radiative transfer equation assuming local thermal equilibrium at a constant temperature $T$: $$\begin{equation}
S_\nu = (1-e^{-\tau_\nu})~B_\nu(T)~\pi r_s^2/d_L^2,
\label{eq:mbb}
\end{equation}$$ where $B_\nu(T)$ is the Planck function at a temperature of $T$ and a rest-frame frequency $\nu$, $\pi r_s^2$ the effective size of the dust emitting region, and $d_L$ the luminosity distance. Assuming that the dust opacity follows a power-law with a negative slope of $-\beta$ at wavelengths greater than the dust size ($\sim$10 $\mu$m), the optical depth should follow the same power-law: $$\begin{equation}
\tau_\nu = (\nu/\nu_0)^\beta = (\lambda/\lambda_0)^{-\beta},
\label{eq:tau}
\end{equation}$$ where $\nu_0$ ($\lambda_0$) is the rest-frame frequency (wavelength) at which the dust becomes optically thick. Given the dust mass-absorption coefficient of $\kappa = 0.07$ m$^2$ kg$^{-1}$ at 850 $\mu$m for Galactic dust (cite: Dunne00; James02), it can be shown that the dust mass is: $$\begin{equation}
M_{\rm dust} = 9.0\times10^9~M_\odot~(\pi r_s^2/{\rm kpc}^2)~(\lambda_0/850\,\mu {\rm m})^\beta.
\label{eq:mdust}
\end{equation}$$ The result of the SED fit gives us a measure of the dust temperature, the dust-obscured SFR, the dust mass, and the effective size of the dust photosphere. Fig. [4](#fig:smg) *left* shows the multi-band photometry, the median MCMC model, and the 1$\sigma$ spread of the models. Table [2](#tab:smg_phot) lists the formal parameters and their uncertainties. The dust is relatively warm ($T = 44\pm7$ K) and the dust photosphere has an effective size of $9_{-5}^{+10}$ kpc$^2$, comparable to the intrinsic source size measured at 343.5 GHz – $\pi a b/4 = 6.4\pm1.5$ kpc$^2$.

The ALMA CO (3$-$2) line luminosity offers an estimate of the mass of the molecular gas reservoir. Because CO (3$-$2) traces the warm and moderately dense ($n_{\rm eff} \sim 10^4$ cm$^{-3}$) component (cite: Juneau09), we first convert the CO (3$-$2) to CO (1$-$0) luminosity using the average brightness temperature ratio of $r_{31} \equiv L'_{\rm CO3-2}/L'_{\rm CO1-0} = 0.52$ observed in SMGs (cite: Bothwell13). We then convert the CO (1$-$0) luminosity to the total molecular gas mass with a CO-to-Molecular-Gas conversion factor of $\alpha_{\rm CO} = 1.0$, a value found appropriate for high-redshift dusty starbursts (cite: Hodge12; Magnelli12; Xue18). The result is a total molecular gas mass of $M_{\rm mol} = (1.25\pm0.07)\times10^{11}~(r_{31}/0.52)^{-1}~(\alpha_{\rm CO}/1.0)$ $M_\odot$, near the high end of the molecular gas masses measured in SMGs (see Fig. [4](#fig:smg) *middle*).

Combining the results from the SED fit and the CO (3$-$2) spectroscopy, we found a gas depletion timescale of $\sim$0.1 Gyr, which is similar to other SMGs but 6$\times$ shorter than co-eval main-sequence galaxies (Fig. [4](#fig:smg) *middle*). The SMG’s dust emission is resolved by the ALMA band-6 data with a beam-deconvolved size of 0.46$''$$\times$0.28$''$. Its CO (3$-$2) emission is resolved by the ALMA band-3 data with a beam-deconvolved size of 0.76$''$$\times$0.54$''$. In both cases, we have measured the intrinsic source sizes from clean’ed images using the CASA task `imfit`. These size measurements allow us to place the SMG on the Kennicutt-Schmit relation (Fig. [4](#fig:smg) *right*). It is characterized by high surface densities of SFR and molecular gas even compared to the SMG population. But like other SMGs, it features a high star-formation efficiency that is distinct from normal star-forming galaxies at $z \sim 2$ (cite: Daddi10b; Genzel10).

## Companion Galaxies

We carried out a blind search of line emitters in the ALMA datacubes with a matched-filter algorithm and tested the fidelity of the detections with simulated noise-only interferometer data (see Appendix § [8](#sec:blindCO)). In the spectral window centered at 94 GHz (i.e., BB4), we found two robust line emitters: the SMG at $z = 2.674$ (S/N = 67) and Comp a at $z = 2.6747$ (S/N = 6.4). The other companion, Comp b, was detected at high significance when we combine the two ALMA channels closest in velocity to the metal-line-detected absorbing clouds C1 and C2 toward QSO1 (see § [4.3](#sec:aodm)). The source has a peak S/N of 4.5 when combining the two channels, while its peak S/N is only 3.6 in the two individual channels, making it confused with noise spikes. The matched-filter algorithm fails to identify Comp b because it assumes that only adjacent channels can boost the S/N above the detection limit. In other words, the detection of Comp b is possible only because (1) we have utilized the prior knowledge of the redshifts of the absorption lines (with the implicit assumption that the emission counterparts have similar redshifts), and (2) the emission counterparts of the two clouds are superimposed on the sky (increasing the S/N when they are combined).

Our blind search detected four additional high-fidelity line emitters: QSO2 at $z = 2.7488$ (S/N = 7.0), its companion at $z = 2.7392$ ($\delta v = -770$ km s$^{-1}$; S/N = 6.1) located $\sim$30$''$ to the NE of QSO2, and two additional sources at $z = 2.3452$ (S/N = 5.5) and $z = 2.3324$ (S/N = 5.2) that may correspond to the $z_{\rm abs}= 2.345$ H i and C iv absorbers that appear toward both QSOs (see Fig. [12](#fig:absorbers) in Appendix [9](#sec:otherabs)). But on the other hand, only the SMG is detected in the continuum image of the two higher-frequency spectral windows (i.e., BB1 and BB2).

While the detection of CO in the SMG and QSO2 is expected, the detection of their companion CO emitters is not. We can use the ALMA Spectroscopic Survey in the Hubble Ultra Deep Field (cite: Decarli19) to estimate a baseline level of source-detection probability in normal field environments. The ASPECS covers an area of 4.6 arcmin$^2$ (${\rm PB} \geq 0.5$, where PB is a correction factor for the primary beam pattern) with 17 pointings in band 3 and a spectral range of 21 GHz (84$-$105 GHz) with five tunings. The rms sensitivity varies with frequency with a range between 0.12 and 0.4 mJy beam$^{-1}$ channel$^{-1}$ for a channel spacing of 7.8 MHz (the same as ours). To provide a conservative estimate, we only count the 7 sources detected at ${\rm S/N} > 6$ between 96 and 103 GHz (cite: Gonzalez-Lopez19), where ${\rm rms} \simeq 0.135$ mJy beam$^{-1}$ channel$^{-1}$. Only within this spectral range is ASPECS more sensitive than our data (${\rm rms} \simeq 0.16$ mJy beam$^{-1}$ channel$^{-1}$). This gives a source density of $0.22\pm0.08$ arcmin$^{-2}$ GHz$^{-1}$ in the field. Given that our ALMA observations cover an area of 0.88 arcmin$^2$ where ${\rm PB} \geq 0.5$ and are $\sim$20% shallower, one would expect to identify less than $0.36\pm0.14$ sources at ${\rm S/N} > 6$ over the 1.875 GHz bandwidth of a baseband, and only a third of these (i.e., $<0.12\pm0.05$ sources) are expected to fall within $\pm$0.3 GHz (1000 km s$^{-1}$) of the main galaxies to be considered as companions. In other words, one would need to increase our survey area by $>$8$\times$ to detect a chance “companion” galaxy of the SMG or QSO2 in the field. Yet we have detected one ${\rm S/N} > 6$ companion within 30$''$ of each main galaxy. Our result thus indicates that both the SMG and QSO2 inhabit overdense environments, which is consistent with their purported large halo masses (cite: Hickox12).

In addition to the companion galaxies detected in CO emission, both the SMG and QSO2 are also associated with absorbers of high H i column density in the spectrum of a common background QSO (QSO1), as we will show in the next section.

# Absorption-line Systems

The two QSOs in the GAMA J0913$-$0107 system were first identified in the Sloan Digital Sky Survey (SDSS) DR9 quasar catalog (cite: Paris12). The pair has a separation of only 10.8$''$, and more importantly, two closely separated DLAs were immediately identified in the low-resolution SDSS spectrum of QSO1 (cite: Noterdaeme12). The stronger DLA ($\log N_{\rm HI}\simeq 21.3$) at $z_{\rm abs}\approx 2.75$ is associated with QSO2 at $z = 2.7488$, providing an important probe of the CGM around QSOs at an impact parameter of $R_\bot = 85$ kpc (see Appendix [9](#sec:otherabs)). The other DLA ($\log N_{\rm HI}\simeq 20.5$) at $z_{\rm abs}\approx 2.68$ provides a window to probe the CGM of the SMG at $z = 2.674$, which is just 11.7$''$ from the QSO.

We searched the spectral databases with `specdb`[^4] and found that the QSO pair had accumulated an excellent set of spectroscopic data from Gemini Multiobject Spectrograph (cite: Prochaska13a), VLT/X-shooter (cite: Finley14), and Magellan Echellette Spectrograph (cite: Rubin15). (cite: Finley14) noticed the strong coincident absorption at $z_{\rm abs}\approx 2.68$ in the SDSS spectra of both QSOs, which motivated them to obtain the higher resolution X-shooter spectra for a detailed analysis. The absorption structure toward both QSOs is resolved into three major subsystems of variable metallicities and with a total velocity span of $>$1700 km s$^{-1}$. The observed kinematic and metallicity coherence across sightlines is remarkable, given the 86 kpc separation between the QSOs. The authors interpreted the system as a gaseous overdensity extended by six Mpc along the line-of-sight, which is suggestive of a clumpy filamentary structure that may eventually collapse and form a proto-cluster. They attributed the two main subsystems at lower velocities (A and B) as part of the IGM because of their low metallicity (${\rm [Fe/H]} < -1.9$) and suspected that the third main subsystem (C) with ${\rm [Fe/H]} = -1.1$ is likely associated with a galaxy. Now with the detection of the SMG and its companion galaxies, we will use the coincident absorption-line system to characterize the CGM of these galaxies in § [5](#sec:connection). We will show that subsystems A and B are cool gas streams in the CGM of the SMG, and subsystem C is indeed associated with a galaxy (Comp b).

In this section, we present a re-analysis of the $z_{\rm abs}\approx 2.68$ absorption system using a new reduction of the X-shooter spectra (§ [4.1](#sec:xshooter)). (cite: Finley14) used `vpfit`[^5] to fit Voigt profiles to the entire spectrum. Our approach is complementary to the `vpfit` analysis and our results show a good agreement with those presented in (cite: Finley14). The main differences between the two analyses are:

1.  We fit Voigt profiles to the H i Lyman series after masking out contaminating LYAF lines and quantify the statistical and systematic uncertainties of the model parameters using an MCMC algorithm (§ [4.2](#sec:voigt)).

2.  We measure the ionic column densities of metals with the apparent optical depth method (AODM; § [4.3](#sec:aodm)). This is a more direct and conservative technique compared with Voigt profile fitting using `vpfit`, because it relies only on equivalent width measurements and uses a straightforward method to detect line saturation.

3.  We use ionic column density ratios to constrain the photoionization model for each cloud, which in turn provides the ionization correction factors necessary for metallicity estimates (§ [4.4](#sec:MH)).

4.  We use the SMG to define the systemic redshift and adopt the solar abundance scale of (cite: Asplund09).

## VLT X-shooter Spectroscopy

The X-shooter observations of the QSOs took place between 2013 March 31 and 2013 May 1 on the 8.2 m VLT/UT2 telescope (program ESO 089.A-0855; (cite: Finley14)). X-shooter uses three individual echelle spectrographs to cover a wide wavelength range between 0.3 and 2.5 $\mu$m simultaneously (cite: Vernet11). (cite: Finley14) estimated spectral resolutions of $R \sim 6400$ (FWHM = 47 km s$^{-1}$) in the UVB arm (3000$-$5600Å), $R \sim 11000$ (27 km s$^{-1}$) in the VIS arm (5500Å$-$1$\mu$m), and $R \sim 6600$ (45 km s$^{-1}$) in the NIR arm (1$-$2.5 $\mu$m). The total exposure times are 100 min for QSO2 and 310 min for QSO1. We downloaded the raw data from the ESO archive and reduced the data with the spectroscopy data reduction pipeline developed by George Becker[^6]. The final 1D spectra were corrected for the 0.2Å (0.5 pixel) wavelength redshift of the spectra in the VIS arm noticed by (cite: Noterdaeme12a), which is likely produced by uncompensated instrumental flexure.

We fit the QSO continuum using the Python software package `linetools`[^7]. First, the spectrum is divided into a number of wavelength intervals, which are $\sim$50 Å wide shortward of the Ly$\alpha$ emission, narrower across strong emission lines, and wider in regions free of emission lines and longward of Ly$\alpha$. Next, a spline is fit through the central wavelength and median flux of each interval (i.e., the spline “knots”). Finally, these “knots” are iteratively added, deleted, or moved until a satisfactory continuum fit is obtained.

## Voigt Profile Fitting of Neutral Hydrogen

Fig. [5](#fig:voigt) shows the H i absorption profiles (Ly$\alpha$ through Ly$\delta$) of the absorbers at $z_{\rm abs}\approx 2.68$ toward the two QSOs. Although the two QSOs are separated by 10.8$''$ (86 kpc at $z = 2.674$), their H i absorption profiles show strikingly similar velocity structures spanning over 1800 km s$^{-1}$, as first noted by (cite: Finley14). The kinematic coherence indicates that the medium responsible for the absorption is extended at least 86 kpc across the sky plane.

Line blending from other absorbers is evident, as indicated by the disagreement in velocity profile among the Lyman series. To measure H i column densities in such a complex situation, it is beneficial to first identify a guessed solution by iteratively varying the Voigt profiles (convolved to $R = 6400$) until an acceptable fit to the data is obtained. The guessed solution not only provides a good starting point for the formal minimum $\chi^2$ approach below, but also helps to identify regions contaminated by line blending (which thus should be flagged out). During this procedure, we find that a minimum of 10 clouds are needed to adequately fit the Lyman series in each sightline. Because each cloud is described by three parameters ($v, b, \log N_{\rm HI}$), our model for each QSO spectrum has a total of 30 free parameters.

To model the absorption toward QSO1, the H i Lyman lines of the DLA at $z_{\rm abs}\approx 2.751$ (see Fig. [12](#fig:absorbers)$a$) must be included in the model because its Ly$\alpha$ and Ly$\delta$ blend with the Ly$\alpha$ and Ly$\gamma$ profiles of the absorber at $z_{\rm abs}\approx 2.68$. We find that the DLA’s H i absorption is adequately modeled as two clouds separated by 290 km s$^{-1}$ ($z_{\rm abs}= 2.7502,2.7538$), each with $\log N_{\rm HI}= 21.0$ and $b = 40$ km s$^{-1}$ (see Fig. [13](#fig:cgm_qso2)). These parameters for the DLA at $z_{\rm abs}= 2.751$ are fixed in the fitting process.

The $\chi^2$ minimization is focused on the velocity range between $-1500$ and 2100 km s$^{-1}$ for QSO1 and between $-600$ and 1350 km s$^{-1}$ for QSO2. With the guessed solution, we also mask out the pixels that are clearly contaminated by line blending within the fitting ranges. The surviving “good” pixels are indicated by diamond symbols with error bars in Fig. [5](#fig:voigt) and the Voigt models are optimized using the amoeba + mcmc method described in § [1.4](#sec:org). The priors of central velocities and column densities are centered around the guessed solution, with bounds of $\pm$100 km s$^{-1}$ for $v_{\rm HI}$ and $\pm$0.8 dex for $\log N_{\rm HI}$. On the other hand, the Doppler parameter, $b_{\rm HI}$, is allowed to vary between 5 and 70 km s$^{-1}$.

For three H i components, we found it necessary to fix their velocities to those measured from low-ion metal lines, because the H i series alone do not constrain their velocities well. Specifically, these components are at $-470$ and $-225$ km s$^{-1}$ toward QSO1 and at $-209$ km s$^{-1}$ toward QSO2.

The optimized models are plotted against the data as blue curves in Fig. [5](#fig:voigt) and the formal parameters and their statistical uncertainties are tabulated in Table [3](#tab:voigt).

Because of the empirical nature of our placement of the unabsorbed QSO continuum, the Voigt parameters suffer from significant systematic uncertainties. In particular, we are interested in the systematic uncertainties of $\log N_{\rm HI}$, which depends on (1) the column density due to the varying gradient of the curve of growth, (2) the quality of the spectrum, and (3) the significance of line blending. To quantify this, we run the same modeling procedure as above but vary the QSO continuum model by $\pm$10% and use the resulting offsets between the three formal solutions to estimate systematic uncertainties. All subsequent errors in $\log N_{\rm HI}$ and metallicities (\[X/H\]) include both statistical and systematic uncertainties.

Fig. [5](#fig:voigt) reveals that there are three separate kinematic clumps centered around $\delta v \approx -300, +400, +1200$ km s$^{-1}$ relative to $z_{\rm SMG}= 2.674$ (i.e., $z_{\rm abs}\approx 2.6703, 2.6789, 2.6887$), which we designate as subsystems A, B, and C, respectively, following the nomenclature of (cite: Finley14). The same clumps appear toward both QSOs, although their column densities vary between sightlines. Half of the six subsystems are optically thick (i.e., $\log N_{\rm HI}> 17.2$), including two sub-DLAs (QSO1-A and QSO1-C) and one LLS (QSO2-A). Metal absorption lines from these subsystems are thus expected, as we will show in the next subsection.

+:----------------------:+:----------------------:+:-----------------------:+:----------------------:+:---------------------:+:-----------------------:+
| toward QSO1                                                               | toward QSO2                                                              |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $v_{\rm HI}$           | $b_{\rm HI}$           | $\log N_{\rm HI}$       | $v_{\rm HI}$           | $b_{\rm HI}$          | $\log N_{\rm HI}$       |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| (km s$^{-1}$)          | (km s$^{-1}$)          | ($\log {\rm cm}^{-2}$)  | (km s$^{-1}$)          | (km s$^{-1}$)         | ($\log {\rm cm}^{-2}$)  |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $-470.1_{-0.0}^{+0.0}$ | $32.2_{-1.2}^{+1.0}$   | $19.64_{-0.05}^{+0.04}$ | $-276.3_{-1.3}^{+1.2}$ | $47.2_{-0.7}^{+0.8}$  | $18.56_{-0.09}^{+0.06}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $-224.7_{-0.0}^{+0.0}$ | $42.2_{-0.5}^{+0.6}$   | $20.06_{-0.04}^{+0.04}$ | $-208.5_{-0.0}^{+0.0}$ | $14.2_{-6.3}^{+6.6}$  | $17.48_{-0.47}^{+0.41}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $52.5_{-2.4}^{+2.3}$   | $45.8_{-3.6}^{+3.7}$   | $14.66_{-0.03}^{+0.03}$ | $31.6_{-1.3}^{+1.3}$   | $38.2_{-1.4}^{+1.4}$  | $14.79_{-0.04}^{+0.04}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $210.1_{-8.2}^{+7.8}$  | $43.3_{-12.0}^{+13.6}$ | $13.75_{-0.11}^{+0.10}$ | $205.1_{-5.9}^{+5.9}$  | $67.0_{-4.2}^{+2.2}$  | $13.75_{-0.03}^{+0.03}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $360.1_{-3.4}^{+4.3}$  | $22.2_{-3.5}^{+3.6}$   | $15.90_{-0.25}^{+0.41}$ | $384.7_{-4.2}^{+4.0}$  | $46.2_{-3.6}^{+3.4}$  | $16.03_{-0.13}^{+0.18}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $454.5_{-8.1}^{+9.0}$  | $58.3_{-8.3}^{+7.0}$   | $15.22_{-0.07}^{+0.06}$ | $509.1_{-8.4}^{+7.0}$  | $37.9_{-4.6}^{+5.3}$  | $14.85_{-0.08}^{+0.08}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $612.6_{-9.4}^{+8.9}$  | $51.9_{-11.4}^{+11.5}$ | $14.08_{-0.08}^{+0.08}$ | $632.9_{-4.8}^{+4.6}$  | $18.4_{-7.9}^{+10.0}$ | $13.24_{-0.07}^{+0.08}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $775.4_{-2.7}^{+2.7}$  | $62.1_{-3.9}^{+3.9}$   | $14.83_{-0.02}^{+0.02}$ | $798.1_{-1.5}^{+1.5}$  | $67.4_{-2.1}^{+1.7}$  | $14.41_{-0.02}^{+0.02}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $1159.5_{-2.0}^{+2.0}$ | $59.0_{-0.7}^{+0.7}$   | $20.23_{-0.02}^{+0.02}$ | $1014.4_{-2.3}^{+2.4}$ | $29.4_{-2.6}^{+2.8}$  | $14.30_{-0.05}^{+0.06}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+
| $1474.8_{-2.2}^{+1.6}$ | $30.2_{-0.8}^{+1.0}$   | $18.79_{-0.19}^{+0.14}$ | $1181.8_{-1.9}^{+1.9}$ | $54.1_{-2.0}^{+2.0}$  | $16.00_{-0.09}^{+0.10}$ |
+------------------------+------------------------+-------------------------+------------------------+-----------------------+-------------------------+

: Voigt Solution for H i Lyman Lines

## Ionic Column Densities from the AODM Method

|     |                      |           |        |        |
|:----|:--------------------:|----------:|-------:|-------:|
| Ion | $\lambda_{\rm rest}$ |  $\log f$ | IP$_0$ | IP$_1$ |
|     |         (Å)          |           |   (eV) |   (eV) |
| C   |      1334.5323       | $-0.8935$ |  11.26 |  24.38 |
| C   |      1548.2040       | $-0.7215$ |  47.89 |  64.49 |
| ... |      1550.7776       | $-1.0234$ |    ... |    ... |
| O   |      1302.1685       | $-1.3188$ |   0.00 |  13.62 |
| Mg  |      2796.3543       | $-0.2108$ |   7.65 |  15.04 |
| ... |      2803.5315       | $-0.5146$ |    ... |    ... |
| Al  |      1670.7886       |  $0.2405$ |   5.99 |  18.83 |
| Al  |      1854.7183       | $-0.2526$ |  18.83 |  28.45 |
| Si  |      1304.3702       | $-1.0640$ |   8.15 |  16.35 |
| ... |      1526.7070       | $-0.8761$ |    ... |    ... |
| Si  |      1393.7602       | $-0.2899$ |  33.49 |  45.14 |
| ... |      1402.7729       | $-0.5952$ |    ... |    ... |
| Fe  |      1608.4508       | $-1.2388$ |   7.90 |  16.20 |
| ... |      2382.7642       | $-0.4949$ |    ... |    ... |
| ... |      2600.1725       | $-0.6209$ |    ... |    ... |

: Selected Metal Transitions

Fig. [6](#fig:aodm) compares the velocity profiles of H i Ly$\beta$ and a selection of metal line transitions commonly observed in LLSs and DLAs (see Table [4](#tab:metallines) for transition data). We find that five of the six H i subsystems are detected in at least one metal transition; the only exception is QSO1-B. Similar to their H i absorption, the metal-line absorptions of subsystems QSO1-A and C, the two sub-DLAs, are resolved into multiple components. Note that the X-shooter spectrum has higher resolution for metal lines in the range $1500 < \lambda_{\rm rest} < 2700$ Å ($R = 11000$ or FWHM = 27 km s$^{-1}$) than for the H i Lyman lines at $\lambda_{\rm rest} < 1217$ Å ($R = 6400$ or FWHM = 47 km s$^{-1}$).

For each distinct metal-line cloud, we define a velocity integration window (highlighted in Fig. [6](#fig:aodm)) and name it by adding a number suffix to designate its associated subsystem.

The cloud QSO1-C1 shows the strongest metal absorption with at least four blended components within $\sim$200 km s$^{-1}$. We treat it as a single entity here, because for the purpose of measuring the gas metallicity it is unnecessary to deblend these components with Voigt profile fitting.

Because the absorption toward QSO2 spans a narrower velocity range than that toward QSO1, the former is missing the most blueshifted cloud “A1” and the most redshifted cloud “C2”. For completeness, we defined QSO1-B1 based on its H i absorption because no metal lines are detected there. As a result, there are a total of eight metal-line clouds.

The top section of Table [\[tab:aodm\]](#tab:aodm) lists the velocity integration windows of the clouds and their H i column densities by summing $\log N_{\rm HI}$ of the Voigt components within the velocity windows. Each cloud contains only one H i Voigt component except QSO1-B1 and QSO2-A2, both of which contain two closely separated components.

| Quantity | QSO1-A1 | QSO1-A2 | QSO1-B1 | QSO1-C1 | QSO1-C2 | QSO2-A2 | QSO2-B1 | QSO2-C1 |
|:---|---:|---:|---:|---:|---:|---:|---:|---:|
| $\delta v/{\rm km\,s}^{-1}$ | \[$-545, -405$\] | \[$-295, -155$\] | \[$325,  475$\] | \[$975, 1375$\] | \[$1425, 1575$\] | \[$-300, -110$\] | \[$300,  500$\] | \[$1100, 1250$\] |
| $\log N_{\rm HI}$ | $19.64_{-0.06}^{+0.04}$ | $20.06_{-0.05}^{+0.08}$ | $15.98_{-0.23}^{+0.39}$ | $20.23_{-0.08}^{+0.07}$ | $18.79_{-0.25}^{+0.33}$ | $18.59_{-0.43}^{+0.23}$ | $16.03_{-0.16}^{+0.21}$ | $16.00_{-0.09}^{+0.10}$ |
| log C iv/C ii | ... | $<-1.06$ | ... | $<-1.10$ | $<-1.23$ | $<-0.80$ | $>0.93$ | $>0.36$ |
| log Al iii/Al ii | $<-0.20$ | $<0.17$ | ... | $-0.58$ | $<0.00$ | $<0.22$ | ... | ... |
| log Si iv/Si ii | $<-1.47$ | $<-0.92$ | ... | $-1.22$ | $<-0.86$ | $>-0.37$ | ... | ... |
| $\log U$ | $<-3.4$ | $<-2.9$ | ... | $-3.0$ | $<-3.2$ | $-2.9$ | $> -2.1$ | $> -2.5$ |
| $\log U$, adopted | $-3.5$ | $-3.0$ | $-2.0$ | $-3.0$ | $-3.5$ | $-3.0$ | $-2.0$ | $-2.0$ |
| $\log n_{\rm H}/{\rm cm}^3$ | $-1.4$ | $-1.9$ | $-2.9$ | $-1.9$ | $-1.4$ | $-1.9$ | $-2.9$ | $-2.9$ |
| $\log N_{\rm H}/{\rm cm}^2$ | $19.9$ | $20.4$ | $19.5$ | $20.5$ | $19.7$ | $20.1$ | $19.5$ | $19.5$ |
| $\log f_{\rm HI}$ | $-0.3$ | $-0.3$ | $-3.5$ | $-0.3$ | $-0.9$ | $-1.5$ | $-3.5$ | $-3.5$ |
| $\log l/{\rm pc}$ | $2.8$ | $3.9$ | $3.9$ | $3.9$ | $2.6$ | $3.5$ | $3.9$ | $3.9$ |
| $[\alpha/{\rm H}]$ | $-1.77\pm0.06$ | $-2.28\pm0.08$ | ... | $-1.08\pm0.08$ | $-1.15\pm0.30$ | $-1.91\pm0.34$ | $-1.02\pm0.19$ | $-1.58\pm0.15$ |
| ion | O i | O i | ... | Si ii | O i | C ii | C iv | C iv |
| IC | $-0.01$ | $-0.01$ | ... | $-0.12$ | $-0.04$ | $-0.90$ | $-2.82$ | $-2.82$ |
| $[{\rm Fe/H}]$ | $-1.92\pm0.07$ | $-2.62\pm0.14$ | ... | $-1.27\pm0.09$ | $-1.76\pm0.34$ | ... | ... | ... |
| $[\alpha/{\rm Fe}]$ | $+0.15\pm0.09$ | $+0.34\pm0.16$ | ... | $+0.19\pm0.12$ | $+0.61\pm0.45$ | ... | ... | ... |

In Appendix [10](#sec:aodmtables), we provide an overview of the AODM method and our measurements of ionic column densities from all of the selected transitions (Table [\[tab:logN\]](#tab:logN)). The listed uncertainties of the unsaturated and unblended detections in the Table include both statistical and systematic errors. Column densities from the AODM method are taken as lower limits for lines with more than one saturated pixels (which we define as $I_{\rm obs}/I_0 \leq 0.05$ or $\tau \geq 3$) and are taken as upper limits for lines that are blended with transitions from absorbers at other redshifts. Lastly, for undetected transitions, we quote 3$\sigma_{\rm sta}$ upper limits on the column densities. Systematic errors are not used here because it’s not meaningful to adjust the QSO continuum around an undetected transition.

## Ionization Correction and Metallicities

A relative metallicity measurement of the intervening gas requires (1) H i column density, (2) ionic column density of a metal element, (3) the reference solar abundances, and (4) the ionization correction. The definition of the relative metallicity makes this explicit: $$\begin{align}
{\rm [X/H]} &\equiv \log (N_{\rm X}/N_{\rm H}) - \log (N_{\rm X}/N_{\rm H})_\odot \nonumber \\
            &= [\log (N_{\rm X_i}/N_{\rm HI}) - \log (N_{\rm X}/N_{\rm H})_\odot] + (\log f_{\rm HI} - \log f_{\rm X_i}) \nonumber \\
            &\equiv {\rm [X/H]}^\prime + {\rm IC} \label{eq:XH}
\end{align}$$ where X$_i$ denotes the ionic state $i$ of element X, $f_{\rm X_i} \equiv N_{\rm X_i}/N_{\rm X}$ is the fraction of the element in the ionic state $i$, $f_{\rm HI} \equiv N_{\rm HI}/N_{\rm H}$ is the neutral fraction of Hydrogen, ${\rm [X/H]}^\prime \equiv \log (N_{\rm X_i}/N_{\rm HI}) - \log (N_{\rm X}/N_{\rm H})_\odot$ is the *raw* metallicity, and ${\rm IC} \equiv \log f_{\rm HI} - \log f_{\rm X_i}$ is the ionization correction.

We have obtained the first two items ($\log N_{\rm HI}$ and $\log N_{\rm X_i}$) in § [4.2](#sec:voigt) and § [4.3](#sec:aodm) and the results are listed in Tables [3](#tab:voigt) and [\[tab:logN\]](#tab:logN). Combined with the elemental abundances of the present-day solar photosphere from (cite: Asplund09), we are ready to calculate the *raw* metallicity ${\rm [X/H]}^\prime$. Next, we calculate the ionization correction (IC) using cloudy photoionization models (cite: Ferland17).

The IC factors are sensitive to both the H i column density ($\log N_{\rm HI}$) and the ionization parameter $\log U = \log \Phi_{\rm H}/(n_{\rm H} c)$, where $\Phi_{\rm H}$ is the surface flux of ionizing photons with $h\nu > 1$ Ryd at the illuminated face. The former has been measured, but the latter needs to be constrained by comparing the column density ratios of different ionic states of the same elements and predictions from photoionization models. Therefore, for each cloud listed in Table [\[tab:aodm\]](#tab:aodm), we calculate a set of photoionization models, with a termination condition set to meet the observed H i column density. For the ionizing source, we use the (cite: Haardt12) radiation background interpolated to $z = 2.67$ with contributions from both galaxies and quasars. For the cloud, we assume plane-parallel geometry, the solar relative abundance pattern, a metallicity of ${\rm [M/H]} = -1.5$[^8], and a range of hydrogen volume densities ($1.09 \geq \log n_{\rm H}/{\rm cm}^{-3} \geq -4.91$) to cover ionization parameters between $-6 \leq \log U \leq 0$. For each cloud, we compare the observed ionic column ratios (C iv/C ii and Si iv/Si ii) and the model-predicted ratios to constrain the ionization parameter. We list the constraints on $\log U$ in Table [\[tab:aodm\]](#tab:aodm). It is rare to have detections of both high ions and low ions in the same cloud, leading to many upper or lower limits of $\log U$. But we found that the most plausible ionization parameters lie between $-4 \lesssim \log U \lesssim -2$, comparable to other published LLSs (cite: Prochaska99; Lehner16). Depending on the data constraint, we adopt $\log U$ values of $-3.5, -3.0,$ or $-2.0$ for each cloud. Finally, once both $\log N_{\rm HI}$ and $\log U$ are fixed, we use the cloudy model of the same parameters to calculate the ICs for all of the ions (Table [\[tab:IC\]](#tab:IC)), which are then used to obtain the ionization-corrected metallicity measurements for all of the transitions (Table [\[tab:XH\]](#tab:XH)).

Notice that the ionization correction only becomes important for (1) low ions in clouds with $\log N_{\rm HI}\lesssim 19$ and (2) intermediate or high ions (e.g., C iv and Si iv) at all column densities. For low ions in sub-DLAs, the ICs are fairly small ($\pm$0.15 dex).

We also use the model to infer the total H column density ($\log N_{\rm H}$), the H neutral fraction ($\log f_{\rm HI}$), the H volume density ($\log n_{\rm H}$), and the characteristic line-of-sight depth of the cloud ($\log l = \log N_{\rm H} - \log n_{\rm H}$). The results are listed in Table [\[tab:aodm\]](#tab:aodm).

The best metallicity measurement is provided by O i, because O i has the smallest ionization correction factors due to its charge-exchange reactions with hydrogen (cite: Field71) and its hydrogen-like ionization potential. Unfortunately, O i $\lambda1302$ is saturated in C1 toward QSO1 (a common issue of the transition for DLAs) and is undetected in cloud B toward QSO1 and the clouds toward QSO2. As a result, transitions from other ions need to be used. The bottom section of Table [\[tab:aodm\]](#tab:aodm) lists the final adopted metallicities from our preferred $\alpha$-element transitions and Fe ii. Note that the ICs for QSO2-B1 and QSO2-C1 are large because only the C iv lines are detected in these clouds. We fail to obtain a reliable metallicity measurement for QSO1-B1 because of the absence of metal absorption. For the four clouds where we have both \[$\alpha$/H\] and \[Fe/H\], we found a moderate level of $\alpha$-enhancement (\[$\alpha$/Fe\]) between 0.15 and 0.61 (with an inverse-variance-weighted mean of 0.2), comparable to those previously measured in $z > 2$ DLAs (\[$\alpha$/Fe\] = $0.30\pm0.16$; (cite: Rafelski12)).

We opt not to correct the gas-phase metallicity for dust depletion, because (1) little depletion is expected from volatile elements such as O and C, (2) the SDSS spectra and photometry of the QSOs show no evidence of significant dust reddening, and (3) the depletion factors are largely uncertain in external galaxies. As a reference, in the Milky Way’s ISM, volatile elements (e.g., C, N, O, S, Zn) show depletions of ${\rm {\rm (X/H)}_{\rm ISM} - (X/H)}_{\rm gas} \lesssim 0.3$, while refractory elements (e.g., Mg, Al, Si, Fe, Ni) show $0.7 \lesssim {\rm (X/H)}_{\rm ISM} - {\rm (X/H)}_{\rm gas} \lesssim 2.0$ (cite: Savage96; Groves04a). These local measurements from a metal-rich ISM provide strict upper limits on the level of depletion expected in the CGM of the SMG.

# Emission-Absorption Connection

Identifying the emission counterparts of the intervening gas helps us compare the properties of the galaxies to those of their CGM. Having analyzed the ALMA CO emitters in § [3](#sec:smg) and the QSO absorption spectra in § [4](#sec:qsos), we are now ready to draw connections between the emission and the absorption based on proximity in both spatial and redshift dimensions.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $\delta v$ | Galaxy | $R_\bot$ | $\log N_{\rm HI}$ | \[M/H\] |  |
|  | (km s$^{-1}$) |  | (kpc) | ($\log {\rm cm}^{-2}$) |  |  |
| QSO1-A | $[-545,-110]$ | SMG | 93.1 | $20.20_{-0.05}^{+0.07}$ | $-2.09\pm0.07$ |  |
| QSO2-A | — | — | 175.5 | $18.59_{-0.43}^{+0.23}$ | $-1.91\pm0.34$ |  |
| QSO1-B | \[300,550\] | SMG | 93.1 | $15.98_{-0.23}^{+0.39}$ | ... |  |
| QSO2-B | — | — | 175.5 | $16.06_{-0.15}^{+0.20}$ | $-1.02\pm0.19$ |  |
| QSO1-C | \[975,1575\] | Comp b | 58.9 | $20.25_{-0.07}^{+0.06}$ | $-1.09\pm0.11$ |  |
| QSO2-C | — | — | 32.2 | $16.01_{-0.09}^{+0.10}$ | $-1.58\pm0.15$ |  |

: Properties of the CGM around the SMG and Comp b

Fig. [7](#fig:emabs) directly compares the absorption profiles from the QSOs to the CO emission profiles from the SMG and its companions. The H i Ly$\beta$ and Al ii$\lambda$1670.8 profiles from the two QSOs are plotted together to illustrate the striking kinematic coherence. In addition, the figure illustrates $\log N_{\rm HI}$ from the Voigt profile solution in Table [3](#tab:voigt) and the ionization-corrected metallicities of the metal-line-defined clouds in Table [\[tab:aodm\]](#tab:aodm).

In § [4](#sec:qsos), we have found that the $z_{\rm abs}\approx 2.68$ H i absorbers have total H i column densities of $\log N_{\rm HI}= 20.53_{-0.06}^{+0.06}$ and $18.60_{-0.43}^{+0.23}$ toward QSO1 and QSO2, respectively. Each absorber is resolved into three main subsystems (A, B, and C) with velocity spans of $\sim$1500-2000 km s$^{-1}$. Although their H i column densities vary significantly between the two QSO sightlines, their radial velocities show remarkable consistency, indicating that the QSOs are intercepting three expansive sheets/filaments of gas. At the same time, the extreme velocity widths of the absorption-line systems suggest that they probe merging systems (cite: Prochaska19).

Results in Fig. [7](#fig:emabs) show that subsystem C is unlikely to be in the same halo as subsystems A, for several reasons. First, subsystem C is 10$\times$ more metal-enriched than subsystem A (${\rm [M/H]} \simeq -1.1$ vs. $-2.1$). Secondly, the velocity spans of $\sim$1950 km s$^{-1}$ (QSO1) and $\sim$1460 km s$^{-1}$ (QSO2; Table [3](#tab:voigt)) and their asymmetric distributions around $z_{\rm SMG}$ (absorption is centered at $z_{\rm abs}= 2.68$) are inconsistent with gravitational motions inside even a $10^{13}$ $M_\odot$ halo centered on the SMG, because the escape velocity of such a halo following the NFW profile is flat at $\sim$700 km s$^{-1}$ between 60 kpc and the virial radius of 186 kpc. Lastly, we have detected CO emission at almost exactly the redshifts of the absorbing clouds in subsystem C in Comp b, which lies much closer to the QSOs than the SMG. Therefore, we consider subsystem A part of the CGM of the SMG at $z = 2.674$, and subsystem C part of the CGM of Comp b at $z = 2.6884$ and 2.6917.

As for subsystem B ($\log N_{\rm HI}\simeq 16$), although its velocity allows an association with the SMG, it is unimportant because its contribution to the CGM is negligible compared to subsystem A.

Once the emission counterparts are determined, the absorption-line measurements from the two QSO sightlines can be plotted against the impact parameter to show crude radial profiles of the CGM around the SMG and Comp b. We consolidate the results in Table [5](#tab:subsys), where we have assigned a velocity window for each subsystem that captures its major clouds. We calculate the total H i column densities from the H i Voigt components within these velocity windows. When there are multiple metal-line clouds in a subsystem, the metallicity is calculated as the $N_{\rm H}$-weighted mean \[$\alpha$/H\], where $N_{\rm H}$ is the H i + H ii column density based on the adopted cloudy model.

The GAMA J0913$-$0107 system gives us the first glimpse into the CGM around an SMG. With high H i column density and low metallicity at large impact parameters, the CGM of the SMG is distinct from the CGM of QSOs and normal star-forming galaxies at $z \sim 2-3$.

The profile of H i column density is shown in Fig. [8](#fig:CGMprof)$a$. We compare our measurements with literature QSO absorption-line measurements in the surroundings of $z \sim 2-3$ QSOs (cite: Lau16) and Lyman Break Galaxies (cite: Simcoe06; Rudie12; Crighton13; Crighton15). The H i column densities of the SMG’s CGM, similar to coeval QSOs, are significantly greater than those of star-forming galaxies at $R_\bot \gtrsim 70$ kpc. The H i column density declines as we move away from the SMG, with a gradient of $-2.0\pm0.4$ dex per 100 kpc.

How do the observed column densities compare with the projected surface mass density $\Sigma_M(R)$ of NFW halos? To make this comparison, we first calculate $\Sigma_M(R)$ by integrating the NFW density profile $\rho(r)$ up to the virial radius: $$\begin{equation}
\Sigma_M(R) = 2 \int_{R}^{R_{\rm vir}} \frac{r \rho(r)}{\sqrt{r^2-R^2}} dr
\end{equation}$$ We then convert it to H i column densities by assuming a baryon$-$dark-matter density ratio of $f_b \equiv \Omega_b/\Omega_c = 0.187$ (cite: Planck-Collaboration20), a Helium correction of $f_{\rm He} = M_{\rm H+He}/M_{\rm H} = 1.36$, and an arbitrary neutral fraction of 10%[^9].

Fig. [8](#fig:CGMprof)$a$ shows that the H i column density profiles of the SMG and the QSOs are consistent with the expectation from a $\sim$$10^{13}$ $M_\odot$ halo. This is in agreement with the detection of a high column of H i ($\log N_{\rm HI}= 18.6$) at an impact parameter as far as 176 kpc. The agreement also shows that the neutral gas in the absorption-line systems can account for $\sim$10% of the total baryonic mass in the halo if they have a filling factor close to unity. On the other hand, the $\log N_{\rm HI}$ profile of LBGs is more consistent with a $\sim$$10^{12}$ $M_\odot$ halo.

The metallicity profile is shown in Fig. [8](#fig:CGMprof)$b$. The literature data points show that, metal-enriched gas with $-1 \lesssim {\rm [M/H]} \lesssim 0$ dominates the inner part ($R_\bot \lesssim 150$ kpc) of the CGM around both QSOs and LBGs. By contrast, the CGM of the SMG is poor in metal, with almost a constant metallicity of \[M/H\]$\approx -2$ across two sightlines separated by 86 kpc (10.8$''$). Its metallicity is near the 1$\sigma$ upper bound of the metallicities measured in the LYAF (cite: Simcoe04), and it is lower by $\sim$1.5 dex at $R_\bot = 93.1$ and by $\sim$0.5 dex at $R_\bot = 175.5$ kpc than that of the CGM of QSOs.

On the other hand, the CGM of Comp b show properties similar to that of normal star-forming galaxies at $z \sim 2-3$. Both line emitters in Comp b have orders of magnitude lower molecular gas mass than the SMG (see Table [\[tab:coords\]](#tab:coords)). Assuming a CO-to-molecular-mass correction factor of $\alpha_{\rm CO} = 4.3$ and a CO excitation correction of $r_{31} = 0.52$, the emitters at $z = 2.6884$ and 2.6917 have molecular gas masses of $M_{\rm mol} = 5.6\times10^9$ and $4.4\times10^9$ $M_\odot$, respectively. The gas masses are comparable to those measured in the lensed normal star-forming galaxies that have stellar masses of $\sim10^{10}$ $M_\odot$ (cite: Saintonge13). One would thus expect a CGM similar to that of LBGs. The corresponding subsystem C provides absorption-line measurements at $R_\bot = 32.3$ and 58.9 kpc. It shows significantly metal-enriched gas (compared to the IGM level) with a large variation in H i column density over just a difference of 27 kpc in impact parameter. Comp b thus is surrounded by a metal-enriched clumpy medium extended to at least $\sim$60 kpc.

In the above, we have shown that the CGM of SMM J0913 is distinctly different from the CGM of QSOs and normal star-forming galaxies. But how do our absorbers compare with other DLAs in terms of absorption-line properties only? The H i column densities of subsystems A and C toward QSO1 miss the DLA threshold of $\log N_{\rm HI}=  20.3$ by merely $\sim$0.1 dex. Because such small differences are comparable to the measurement uncertainty, more liberal thresholds have been used to select DLAs (cite: Rubin15). Combined with the result that the two sub-DLAs have neutral fraction of $\sim$50% from cloudy models, we believe that it is appropriate to compare their properties with those of the general DLA population.

With high-resolution spectra of 100 DLAs at $z_{\rm abs}\sim 2-4$, (cite: Rafelski12) found that their metallicity distribution is well fit by a Gaussian with a mean at ${\rm [M/H]} = -1.57$ and a dispersion of 0.57 dex. The DLA metallicity only mildly decreases with redshift, but shows a strong correlation with the width of low-ion metal lines (e.g., $\Delta V_{90}$ or $W_{1526}$) (cite: Neeleman13). This correlation between kinematics and metallicity is generally interpreted as a manifestation of the mass-metallicity relation (cite: Tremonti04; Erb06), because the line width may reflect the halo mass (like in the Tully-Fisher relation), which in turn is proportional to the stellar mass (cite: Moller13).

Previous works have used higher-resolution spectra ($R \gtrsim 40000$) to measure $\Delta V_{90}$, the velocity interval including 90% of the optical depth of an *unsaturated* line. And the alternative kinematic parameter $W_{1526}$, the rest-frame equivalent width of Si ii$\lambda$1526.7, is unsuitable for our sub-DLAs because the line is *unsaturated* (see Fig. [6](#fig:aodm)). The equivalent width only becomes a good kinematics indicator when the line is *saturated*, weakening its dependency on the Si$^+$ column density (and consequently, on metallicity).

So to place our sub-DLAs on the relation, we adopt the velocity separation between kinematically resolved substructures as a surrogate of $\Delta V_{90}$. QSO1-A shows two velocity components of similar strength separated by $\sim$250 km s$^{-1}$, and QSO1-C is dominated by the stronger C1 cloud, which appears to be a blend of four components with a velocity span of $\sim$200 km s$^{-1}$. These estimates of the velocity width should be considered as lower limits on $\Delta V_{90}$, because they are the separations between peak optical depths.

Fig. [9](#fig:mh_v90) compares the two sub-DLAs against literature DLAs. To control the redshift evolution of the mass-metallicity relation, only the DLAs between $2 < z_{\rm abs}< 3$ are plotted. While QSO1-C blends in the general trend established by DLAs, QSO1-A is a clear outlier. Firstly, very few DLAs have metallicities as low as QSO1-A: only 2 out of the 44 DLAs ($4.5_{-1.5}^{+5.5}$%) have ${\rm [M/H]} \leq -2.1$. Secondly, its high velocity width places it significantly below the metallicity-line-width relation of DLAs, which would have predicted a velocity width of only $\sim$20 km s$^{-1}$ based on its metallicity at ${\rm [M/H]} = -2.1$.

This finding suggests that most of the DLAs are likely closer to their hosts than our sub-DLA QSO1-A ($R_\bot = 93$ kpc), consistent with previous observations of DLA host galaxies (see § [1.3](#sec:intro-connection)).

More importantly, the unusual combination of high velocity-width and low metallicity provides a method – based on absorption-line properties alone – to potentially separate (sub-)DLAs associated with normal star-forming galaxies at low impact parameters with those associated with more massive galaxies like SMGs at large impact parameters.

# Summary & Discussion

We have carried out a comprehensive study of the emission-absorption system GAMA J0913$-$0107 at $z \sim 2.67$ with a multi-wavelength data set obtained primarily from *Herschel*, ALMA, and VLT/X-shooter. The system consists of a bright SMG, its CO companion galaxies, and a number of optically thick H i absorbers toward two background QSOs within 22$''$ of the SMG. Our main results are:

1.  The *Herschel*-selected SMG at $z = 2.674$, with an 870 $\mu$m flux of 7.4 mJy and an IR luminosity of $\sim10^{13}$ $L_\odot$, is one of the most luminous dusty star-forming galaxies. Its properties are similar to the general SMG population at $z \sim 2$, featuring a short gas depletion timescale of $\sim$0.1 Gyr and compact (sub-arcsec) sizes in both dust emission and CO (3$-$2) emission. The high S/N spectrum reveals two CO (3$-$2) components at almost the same redshift: $\sim$1/4 of the line flux is in a broad component with a ${\rm FWHM} \simeq 900$ km s$^{-1}$, while $\sim$3/4 of the flux in a narrow component with ${\rm FWHM} \simeq 250$ km s$^{-1}$.

2.  Three companion CO emitters are identified within 30$''$ and 1500 km s$^{-1}$ of the SMG. A comparison with the source counts from the ASPECS field survey indicates that the SMG lives in an over-dense environment.

3.  Two nearby QSOs provide background beacons to probe the CGM of the SMG. A DLA with a total H i column density of $\log N_{\rm HI}= 20.5$ is identified at $z_{\rm abs}\sim 2.68$ in the closer QSO sightline at $\theta = 11.7\ensuremath{''}$. The DLA is quite unusual, in terms of both the large impact parameter ($R_\bot = 93.1$ kpc to the SMG) and the enormous velocity span ($\sim$2000 km s$^{-1}$). X-shooter resolved the DLA into three major subsystems, including two sub-DLAs with distinctly different metallicities separated by $\sim$1600km s$^{-1}$. Remarkably, the same subsystems are also found in the farther QSO sightline at $\theta = 22.1\ensuremath{''}$: they have nearly the same velocities and metallicities as their counterparts at $\theta = 11.7\ensuremath{''}$, despite lower H i column densities (total $\log N_{\rm HI}= 18.6$).

4.  We use the absorption-line systems to characterize the CGM of the SMG and its companion Comp b, and we compare their properties with the CGM of QSOs and normal star-forming galaxies. The CGM of the SMG forms its own category: while its high column densities at large impact parameters are similar to the massive halos inhabited by $z = 2-3$ QSOs, its metal content ($\sim$1% solar) is an order of magnitude lower than the circum-QSO medium. On the other hand, the CGM of the much less luminous Comp b is more consistent with that of normal star-forming galaxies at $z = 2-3$: showing significant metal enrichment ($\sim$10% solar) within $R_\bot \lesssim 60$ kpc.

The detection of high-column density, mostly neutral, metal-poor gas in the CGM of a massive dusty starburst galaxy at $z = 2.674$ has powerful implications to theories of galaxy formation and evolution. The remarkable consistency of the H i absorbers in both kinematics and metallicity across two sightlines separated by 86 kpc is at odds with CGM models that assume randomly floating H i clouds in pressure equilibrium with hot X-ray gas. Instead, it is logical to assume that the background QSOs have intercepted a single filament of cool gas permeating in the halo.

Narrow filaments of cool gas and satellite galaxies can penetrate the hot CGM of massive halos without ever being shock-heated to the virial temperature, because (1) massive halos are rare and tend to form at the intersections of the cosmic web and (2) the cooling time is shorter in the filaments than in the halo (cite: Dekel06; Dekel09; Keres09). At $z \gtrsim 2.5$, such cold streams can survive even in halos more massive than $\sim$$10^{13}$ $M_\odot$ (although note that this mass limit is highly uncertain). In particular, stream-feeding is likely important in the bright SMGs with $S_{850} > 5$ mJy because their comoving space density exceeds the expectation from minor and major mergers (cite: Dekel09).

The observed properties of the absorption-line systems match the simulation-predicted properties of cold streams. First, the simulations of (cite: Dekel09) show that the inflow velocity is comparable to the virial velocity and is roughly constant along the filament. This is consistent with the velocity shift ($\delta v = -300$ km s$^{-1}$) and the kinematic coherence we saw between the clouds in both QSO sightlines. Secondly, by post-processing gas in seven simulated halos with $M_{\rm halo}= 10^{10}-10^{12}$ $M_\odot$ between $1.5 < z < 4.0$, (cite: Fumagalli11a) found that the absorption-line systems associated with the smooth stream component have systematically lower metallicity ($\sim$1% solar). This is exactly the level of the gas metallicity we measured in the absorbers associated with the SMG.

Radially inflowing on nearly a free-fall timescale, the cold streams may account for the bulk of the baryonic accretion rate and become the dominant mechanism to feed the growth of galaxies (cite: Keres09). We can crudely estimate the gas accretion rate from the filament that the QSOs intercepted. The filament has a length $>$176 kpc and a depth on the order of 10 kpc at $R_\bot = 93$ kpc. The former is estimated from the impact parameter of QSO2, and the latter is estimated from the ratio between the column density and the volume density of Hydrogen, $l = N_{\rm H}/n_{\rm H}$, inferred from the photoionization model of the sub-DLA QSO1-A2. The depth-to-distance ratio is 0.11 radian or $6^\circ$, comparable to the opening angles of $20-30^\circ$ seen in simulations (cite: Dekel09). Our photoionization models also indicate similar H i+H ii column densities for QSO1-A2 ($\log N_{\rm H} = 20.4$) and QSO2-A2 ($\log N_{\rm H} = 20.1$), the two main clouds associated with the SMG at $R_\bot = 93, 176$ kpc. By assuming an opening angle of $\beta = 25^\circ$, an average hydrogen column density of $\log N_{\rm H} = 20.2$, and a $10^{13}$ $M_\odot$ NFW halo at $z = 2.674$, we estimate that the mass of the filament is $M_{\rm fil} = f_{\rm He} m_p N_{\rm H} (\beta~R_{\rm vir}^2/2) \sim 1.3\times10^{10}$ $M_\odot$. Given an accretion timescale of $\tau_{\rm acc} = R_{\rm vir}/V_{\rm vir} = 4\times10^8$ yr, the gas accretion rate from this single filament is $\sim$33 $M_\odot\,{\rm yr}^{-1}$. Typically three main filaments are seen in the simulations, so our estimate shows that cold-mode accretion can supply gas at a rate of $\sim$100 $M_\odot\,{\rm yr}^{-1}$. Although accounting for only $\sim$10% of the current SFR, our estimated cool gas accretion rate is in fact comparable to the rate of total gas supply to the central galaxies in $10^{13}$ $M_\odot$ halos at $z = 2$ from cosmological simulations (cite: Keres09), and at this rate the molecular gas reservoir of $10^{11}$ $M_\odot$ can be acquired in just $\sim$1 Gyr. On the other hand, star formation at the current intensity seems unsustainable despite the efficient gas supply from cold streams.

In this work, we have presented the first observational evidence that supports the existence of cold streams in the CGM of a massive starburst galaxy. The GAMA J0913$-$0107 system has an excellent data set and the results are highly informative, but larger samples are clearly desired to draw conclusions on the general properties of the CGM. We hope that this will serve as a springboard for upcoming statistical studies of the CGM in similar galaxies. As an attempt to inform these future studies, it is worth discussing the major technical challenges we had faced in this program:

1.  The large beam of *Herschel* (17.8$''$ at 250 $\mu$m) makes it inefficient to identify SMG-QSO pairs with small angular separations ($\theta \lesssim 10\ensuremath{''}$). As a result, QSO1 in GAMA J0913$-$0107 is the only one that probes below 100 kpc; and despite intercepting a sub-DLA it has yet to expose the chemically enriched area of the CGM of the SMG.

2.  High S/N spectra with moderately high spectral resolution are needed to unambiguously detect optically thick absorbers with $17.2 < \log N_{\rm HI}\lesssim 19$. For example, with the $R \sim 2000$ SDSS spectrum of QSO2, we couldn’t have identified the LLS associated with the SMG (i.e., QSO2-A2 with $\log N_{\rm HI}= 18.6$). But the LLS is unambiguously detected in the X-shooter spectrum because of its resolved H i Lyman profiles and the clear detection of low-ion metal lines. Similarly low column densities are expected in most of our sample, because all of the other spectroscopically confirmed SMG-QSO pairs we have so far have impact parameters between $100 < R_\bot < 300$ kpc (cite: Fu16) and none of them show obvious (sub-)DLA features (which may be expected given the large impact parameters).

3.  It has been difficult to obtain spectroscopic redshifts of the *Herschel* sources because (1) they require sub-arcsec positions from interferometers to place spectroscopic slits, (2) the near-IR spectral range suffers from heavy telluric absorption and OH emission, and (3) SMGs tend to be weak in rest-frame optical lines. The latter two points are the main reasons why our redshift success rate is only $\sim$60%.

Possible solutions to these issues may be already on the horizon.

To address the first challenge, we need to design an efficient interferometer imaging survey, because a sample of *Herschel* sources with less than 10$''$ apparent offsets from optical QSOs is likely overwhelmed by contaminating sources. Two third of the *Herschel*-SDSS-selected pairs with apparent separations between 5$''$ and 10$''$ turned out to be IR-luminous QSOs instead of projected SMG-QSO pairs. A good strategy is to observe multiple sources located within a $\sim$10$^\circ$ diameter circle in a single ALMA scheduling block (SB). In (cite: Fu17), we managed to observe $\sim$10 targets in a single $\sim$50 min SB, achieving an on-source integration time of 200 s per source and an rms of 0.12 mJy beam$^{-1}$. Do we have enough such pairs to populate a 50-min SB? The surface density of *Herschel*-QSO pairs with offsets less than 10$''$ is 0.16 deg$^2$ (26 pairs in the 161.6 deg$^2$ H-ATLAS GAMA fields), which gives $\sim$13 targets for a $\sim$10$^\circ$ diameter circle.

To address the second challenge, we need QSO spectra with quality similar to the X-shooter spectra presented here to better sample the spatial profile of the CGM. The QSOs in our sample are selected to have $g < 22$, the majority of which requires $\sim$1.5 hours’ exposure time with an Echellette spectrograph on a 10-m-class telescope to reach a sufficient S/N at $R \sim 8000$ (cite: Rafelski12).

To address the last challenge, we need a more efficient method to obtain SMG redshifts. One potential approach is to exploit the frequency scan mode offered by modern millimeter interferometers. This method has the additional advantage of bypassing the interferometer imaging step because the primary beam is usually larger than the *Herschel* positional uncertainty and the line detection also provides positional information. For instance, with NOEMA scans of the 2 mm and 3 mm bands (only two spectral configurations per band), (cite: Neri20) obtained 12 secure redshifts for 13 sources. The average telescope time spent is $\sim$105 min per source, including $\sim$40 min overhead. Although the targets in this Pilot study have 500 $\mu$m flux densities greater than 80 mJy (many are strongly lensed), this technique could be applied to fainter sources (like ours with $S_{500} > 20$ mJy) as the instrument sensitivity and overheads continue to improve.

# Acknowledgments

We thank D. Kereš and J. Hennawi for discussions.

This work is partially supported by the National Science Foundation (NSF) grant AST-1614326. D. N. acknowledges support from NSF AST-1909153.

The National Radio Astronomy Observatory is a facility of the NSF operated under cooperative agreement by Associated Universities, Inc.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00131.S, ADS/JAO. ALMA#2018.1.00548.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

*Facilities*: Herschel, ALMA, Gemini/GNIRS, VLT/X-shooter, Keck/LRIS, Sloan, KiDS, VISTA

148 natexlab

(ref: Alaghband-Zadeh12) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2012, MNRAS, 424, 2232

(ref: Asplund09) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481

(ref: Barger98) Barger, A. J., Cowie, L. L., Sanders, D. B., et al. 1998, Nature, 394, 248

(ref: Benitez00) Benı́tez, N. 2000, ApJ, 536, 571

(ref: Birnboim03) Birnboim, Y., & Dekel, A. 2003, MNRAS, 345, 349

(ref: Blain02) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J.-P., & Frayer, D. T. 2002, Phys. Rep., 369, 111

(ref: Bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Bonato19) Bonato, M., Liuzzo, E., Herranz, D., et al. 2019, MNRAS, 485, 1188

(ref: Bothwell13) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047

(ref: Bruzual03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Bryan98) Bryan, G. L., & Norman, M. L. 1998, ApJ, 495, 80

(ref: Bullock17) Bullock, J. S., & Boylan-Kolchin, M. 2017, ARA&A, 55, 343

(ref: Bullock01) Bullock, J. S., Kolatt, T. S., Sigad, Y., et al. 2001, MNRAS, 321, 559

(ref: Burbidge68) Burbidge, E. M., Lynds, C. R., & Stockton, A. N. 1968, ApJ, 152, 1077

(ref: Cantalupo14) Cantalupo, S., Arrigoni-Battaia, F., Prochaska, J. X., Hennawi, J. F., & Madau, P. 2014, Nature, 506, 63

(ref: Casey14) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: Chapman05) Chapman, S. C., Blain, A. W., Smail, I., & Ivison, R. J. 2005, ApJ, 622, 772

(ref: Chen15) Chen, C.-C., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 194

(ref: Chen16) Chen, Y.-M., Shi, Y., Tremonti, C. A., et al. 2016, Nature Communications, 7, 13269 EP

(ref: Condon97) Condon, J. J. 1997, PASP, 109, 166

(ref: Crighton13) Crighton, N. H. M., Hennawi, J. F., & Prochaska, J. X. 2013, ApJL, 776, L18

(ref: Crighton15) Crighton, N. H. M., Hennawi, J. F., Simcoe, R. A., et al. 2015, MNRAS, 446, 18

(ref: Cushing04) Cushing, M. C., Vacca, W. D., & Rayner, J. T. 2004, PASP, 116, 362

(ref: Daddi09) Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, ApJ, 694, 1517

(ref: Daddi10b) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJ, 714, L118

(ref: Daddi20) Daddi, E., Valentino, F., Rich, R. M., et al. 2020, arXiv e-prints, arXiv:2006.11089

(ref: Decarli19) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138

(ref: Dekel06) Dekel, A., & Birnboim, Y. 2006, MNRAS, 368, 2

(ref: Dekel09) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: Downes98) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615

(ref: Dunne00) Dunne, L., Eales, S., Edmunds, M., et al. 2000, MNRAS, 315, 115

(ref: Eales10) Eales, S. A., Raymond, G., Roseboom, I. G., et al. 2010, A&A, 518, L23

(ref: Eastman13) Eastman, J., Gaudi, B. S., & Agol, E. 2013, PASP, 125, 83

(ref: Eastman19) Eastman, J. D., Rodriguez, J. E., Agol, E., et al. 2019, arXiv e-prints, arXiv:1907.09480

(ref: Elias06) Elias, J. H., Joyce, R. R., Liang, M., et al. 2006, in Proc. SPIE, Vol. 6269, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, 62694C

(ref: Erb06) Erb, D. K., Shapley, A. E., Pettini, M., et al. 2006, ApJ, 644, 813

(ref: Falgarone17) Falgarone, E., Zwaan, M. A., Godard, B., et al. 2017, Nature, 548, 430

(ref: Faucher-Giguere16) Faucher-Giguère, C.-A., Feldmann, R., Quataert, E., et al. 2016, MNRAS, 461, L32

(ref: Faucher-Giguere15) Faucher-Giguère, C.-A., Hopkins, P. F., Kereš, D., et al. 2015, MNRAS, 449, 987

(ref: Ferland17) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, RMxAA, 53, 385

(ref: Field71) Field, G. B., & Steigman, G. 1971, ApJ, 166, 59

(ref: Finley14) Finley, H., Petitjean, P., Noterdaeme, P., & Pâris, I. 2014, A&A, 572, A31

(ref: Fu17) Fu, H., Isbell, J., Casey, C. M., et al. 2017, ApJ, 844, 123

(ref: Fu13) Fu, H., Cooray, A., Feruglio, C., et al. 2013, Nature, 498, 338

(ref: Fu16) Fu, H., Hennawi, J. F., Prochaska, J. X., et al. 2016, ApJ, 832, 52

(ref: Fumagalli16) Fumagalli, M., O’Meara, J. M., & Prochaska, J. X. 2016, MNRAS, 455, 4100

(ref: Fumagalli11a) Fumagalli, M., Prochaska, J. X., Kasen, D., et al. 2011, MNRAS, 418, 1796

(ref: Fynbo08) Fynbo, J. P. U., Prochaska, J. X., Sommer-Larsen, J., Dessauges-Zavadsky, M., & Møller, P. 2008, ApJ, 683, 321

(ref: Fynbo13) Fynbo, J. P. U., Geier, S. J., Christensen, L., et al. 2013, MNRAS, 436, 361

(ref: Fynbo18) Fynbo, J. P. U., Heintz, K. E., Neeleman, M., et al. 2018, MNRAS, 479, 2126

(ref: Genzel10) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091

(ref: Gonzalez-Lopez19) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139

(ref: Greve05) Greve, T. R., Bertoldi, F., Smail, I., et al. 2005, MNRAS, 359, 1165

(ref: Griffin10) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3

(ref: Groves04a) Groves, B. A., Dopita, M. A., & Sutherland, R. S. 2004, ApJS, 153, 9

(ref: Haardt12) Haardt, F., & Madau, P. 2012, ApJ, 746, 125

(ref: Hainline11) Hainline, L. J., Blain, A. W., Smail, I., et al. 2011, ApJ, 740, 96

(ref: Harris10) Harris, A. I., Baker, A. J., Zonak, S. G., et al. 2010, ApJ, 723, 1139

(ref: Hennawi15) Hennawi, J. F., Prochaska, J. X., Cantalupo, S., & Arrigoni-Battaia, F. 2015, Science, 348, 779

(ref: Hennawi06a) Hennawi, J. F., Prochaska, J. X., Burles, S., et al. 2006, ApJ, 651, 61

(ref: Hickox12) Hickox, R. C., Wardlow, J. L., Smail, I., et al. 2012, MNRAS, 421, 284

(ref: Hodge12) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11

(ref: Ivison11) Ivison, R. J., Papadopoulos, P. P., Smail, I., et al. 2011, MNRAS, 412, 1913

(ref: James02) James, A., Dunne, L., Eales, S., & Edmunds, M. G. 2002, MNRAS, 335, 753

(ref: Jorgenson14) Jorgenson, R. A., & Wolfe, A. M. 2014, ApJ, 785, 16

(ref: Juneau09) Juneau, S., Narayanan, D. T., Moustakas, J., et al. 2009, ApJ, 707, 1217

(ref: Kanekar20) Kanekar, N., Prochaska, J. X., Neeleman, M., et al. 2020, ApJL, 901, L5

(ref: Kennicutt98b) Kennicutt, Robert C., J. 1998, ApJ, 498, 541

(ref: Kennicutt03) Kennicutt, Robert C., J., Bresolin, F., & Garnett, D. R. 2003, ApJ, 591, 801

(ref: Keres05) Keres, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2

(ref: Keres09) Kereš, D., Katz, N., Fardal, M., Davé, R., & Weinberg, D. H. 2009, MNRAS, 395, 160

(ref: Klypin11) Klypin, A. A., Trujillo-Gomez, S., & Primack, J. 2011, ApJ, 740, 102

(ref: Kneib11) Kneib, J.-P., & Natarajan, P. 2011, A&ARv, 19, 47

(ref: Krogager17) Krogager, J.-K., Møller, P., Fynbo, J. P. U., & Noterdaeme, P. 2017, MNRAS, 469, 2959

(ref: Kuijken19) Kuijken, K., Heymans, C., Dvornik, A., et al. 2019, A&A, 625, A2

(ref: Lau16) Lau, M. W., Prochaska, J. X., & Hennawi, J. F. 2016, ApJS, 226, 25

(ref: Lehner16) Lehner, N., O’Meara, J. M., Howk, J. C., Prochaska, J. X., & Fumagalli, M. 2016, ApJ, 833, 283

(ref: Li19a) Li, Q., Cai, Z., Prochaska, J. X., et al. 2019, ApJ, 875, 130

(ref: Lovell21) Lovell, C. C., Geach, J. E., Davé, R., Narayanan, D., & Li, Q. 2021, MNRAS

(ref: Magnelli12b) Magnelli, B., Saintonge, A., Lutz, D., et al. 2012a, A&A, 548, 22

(ref: Magnelli12) Magnelli, B., Lutz, D., Santini, P., et al. 2012b, A&A, 539, 155

(ref: Martin15) Martin, D. C., Matuszewski, M., Morrissey, P., et al. 2015, Nature, 524, 192

(ref: Martin19a) Martin, D. C., O’Sullivan, D., Matuszewski, M., et al. 2019, Nature Astronomy, 3, 822

(ref: Meiksin09) Meiksin, A. A. 2009, Reviews of Modern Physics, 81, 1405

(ref: Michalowski12) Michałowski, M. J., Dunlop, J. S., Cirasuolo, M., et al. 2012, A&A, 541, 85

(ref: Moller20) Møller, P., & Christensen, L. 2020, MNRAS, 492, 4805

(ref: Moller13) Møller, P., Fynbo, J. P. U., Ledoux, C., & Nilsson, K. K. 2013, MNRAS, 430, 2680

(ref: Moller01) Møller, P., & Fynbo, J. U. 2001, A&A, 372, L57

(ref: Morton03) Morton, D. C. 2003, ApJS, 149, 205

(ref: Narayanan15) Narayanan, D., Turk, M., Feldmann, R., et al. 2015, Nature, 525, 496

(ref: Navarro96) Navarro, J. F., Frenk, C. S., & White, S. D. M. 1996, ApJ, 462, 563

(ref: Neeleman17) Neeleman, M., Kanekar, N., Prochaska, J. X., et al. 2017, Science, 355, 1285

(ref: Neeleman19) Neeleman, M., Kanekar, N., Prochaska, J. X., Rafelski, M. A., & Carilli, C. L. 2019, ApJL, 870, L19

(ref: Neeleman13) Neeleman, M., Wolfe, A. M., Prochaska, J. X., & Rafelski, M. 2013, ApJ, 769, 54

(ref: Neri20) Neri, R., Cox, P., Omont, A., et al. 2020, A&A, 635, A7

(ref: Noterdaeme12) Noterdaeme, P., Petitjean, P., Carithers, W. C., et al. 2012a, A&A, 547, L1

(ref: Noterdaeme12a) Noterdaeme, P., Laursen, P., Petitjean, P., et al. 2012b, A&A, 540, A63

(ref: Oke95) Oke, J. B., Cohen, J. G., Carr, M., et al. 1995, PASP, 107, 375

(ref: Oser10) Oser, L., Ostriker, J. P., Naab, T., Johansson, P. H., & Burkert, A. 2010, ApJ, 725, 2312

(ref: Papadopoulos12b) Papadopoulos, P. P., van der Werf, P., Xilouris, E., Isaak, K. G., & Gao, Y. 2012, ApJ, 751, 10

(ref: Paris12) Pâris, I., Petitjean, P., Aubourg, É., et al. 2012, A&A, 548, A66

(ref: Pascale11) Pascale, E., Auld, R., Dariush, A., et al. 2011, MNRAS, 415, 911

(ref: Pavesi18) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49

(ref: Peroux20) Péroux, C., & Howk, J. C. 2020, ARA&A, 58, 363

(ref: Planck-Collaboration20) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: Press92) Press, W. H., Teukolsky, S. A., Vetterling, W. T., & Flannery, B. P. 1992, Numerical recipes in C. The art of scientific computing (Cambridge: University Press, $|$c1992, 2nd ed.)

(ref: Prochaska99) Prochaska, J. X. 1999, ApJL, 511, L71

(ref: Prochaska13) Prochaska, J. X., Hennawi, J. F., & Simcoe, R. A. 2013a, ApJL, 762, L19

(ref: Prochaska14) Prochaska, J. X., Lau, M. W., & Hennawi, J. F. 2014, ApJ, 796, 140

(ref: Prochaska19) Prochaska, J. X., Neeleman, M., Kanekar, N., & Rafelski, M. 2019, ApJL, 886, L35

(ref: Prochaska01) Prochaska, J. X., Wolfe, A. M., Tytler, D., et al. 2001, ApJS, 137, 21

(ref: Prochaska13a) Prochaska, J. X., Hennawi, J. F., Lee, K.-G., et al. 2013b, ApJ, 776, 136

(ref: Rafelski12) Rafelski, M., Wolfe, A. M., Prochaska, J. X., Neeleman, M., & Mendez, A. J. 2012, ApJ, 755, 89

(ref: Rauch98) Rauch, M. 1998, ARA&A, 36, 267

(ref: Rengelink97) Rengelink, R. B., Tang, Y., de Bruyn, A. G., et al. 1997, A&AS, 124, 259

(ref: Riechers11b) Riechers, D. A., Hodge, J., Walter, F., Carilli, C. L., & Bertoldi, F. 2011, ApJ, 739, L31

(ref: Rigby11) Rigby, E. E., Maddox, S. J., Dunne, L., et al. 2011, MNRAS, 415, 2336

(ref: Rubin15) Rubin, K. H. R., Hennawi, J. F., Prochaska, J. X., et al. 2015, ApJ, 808, 38

(ref: Rudie13) Rudie, G. C., Steidel, C. C., Shapley, A. E., & Pettini, M. 2013, ApJ, 769, 146

(ref: Rudie12) Rudie, G. C., Steidel, C. C., Trainor, R. F., et al. 2012, ApJ, 750, 67

(ref: Saintonge13) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2

(ref: Savage91) Savage, B. D., & Sembach, K. R. 1991, ApJ, 379, 245

(ref: Savage96) —. 1996, ApJ, 470, 893

(ref: Serra15) Serra, P., Westmeier, T., Giese, N., et al. 2015, MNRAS, 448, 1922

(ref: Sharon13) Sharon, C. E., Baker, A. J., Harris, A. I., & Thomson, A. P. 2013, ApJ, 765, 6

(ref: Simcoe04) Simcoe, R. A., Sargent, W. L. W., & Rauch, M. 2004, ApJ, 606, 92

(ref: Simcoe06) Simcoe, R. A., Sargent, W. L. W., Rauch, M., & Becker, G. 2006, ApJ, 637, 648

(ref: Smail97) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJ, 490, L5

(ref: Srianand16) Srianand, R., Hussain, T., Noterdaeme, P., et al. 2016, MNRAS, 460, 634

(ref: Steidel92) Steidel, C. C., & Hamilton, D. 1992, AJ, 104, 941

(ref: Swinbank04) Swinbank, A. M., Smail, I., Chapman, S. C., et al. 2004, ApJ, 617, 64

(ref: Tacconi08) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680, 246

(ref: Tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: Tacconi18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Targett13) Targett, T. A., Dunlop, J. S., Cirasuolo, M., et al. 2013, MNRAS, 432, 2012

(ref: Ter-Braak06) Ter Braak, C. J. F. 2006, Statistics and Computing, 16, 239

(ref: Theuns21) Theuns, T. 2021, MNRAS, 500, 2741

(ref: Tremonti04) Tremonti, C. A., Heckman, T. M., Kauffmann, G., et al. 2004, ApJ, 613, 898

(ref: Umehata19) Umehata, H., Fumagalli, M., Smail, I., et al. 2019, Science, 366, 97

(ref: Valiante16) Valiante, E., Smith, M. W. L., Eales, S., et al. 2016, MNRAS, 462, 3146

(ref: Vernet11) Vernet, J., Dekker, H., D’Odorico, S., et al. 2011, A&A, 536, A105

(ref: Walter16) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67

(ref: Wardlow11) Wardlow, J. L., Smail, I., Coppin, K. E. K., et al. 2011, MNRAS, 415, 1479

(ref: Weidinger04) Weidinger, M., Møller, P., & Fynbo, J. P. U. 2004, Nature, 430, 999

(ref: Wolfe05) Wolfe, A. M., Gawiser, E., & Prochaska, J. X. 2005, ARA&A, 43, 861

(ref: Wolfe86) Wolfe, A. M., Turnshek, D. A., Smith, H. E., & Cohen, R. D. 1986, ApJS, 61, 249

(ref: Xue18) Xue, R., Fu, H., Isbell, J., et al. 2018, ApJL, 864, L11

# Lensing of the SMG

In the KiDS $gri$ pseudo-color image in Fig. [1](#fig:fchart), there is an extended optical source just 0.8$''$ to the NW of the ALMA source. This offset cannot be an astrometry error, because the ALMA CO (3$-$2) emission of QSO2 agrees with its KiDS optical position within 0.1$''$. The optical source is in the KiDS-VISTA 9-band photometric catalog (cite: Kuijken19) with a designation of KiDSDR4 J091339.496$-$010656.17 and a photometric redshift of $z_p = 0.07_{-0.04}^{+0.05}$. We obtained an optical spectrum with the Low Resolution Imaging Spectrometer (cite: Oke95) on the Keck I telescope on 2017 Mar 23. Strong emission lines, such as \[O ii\]$\lambda$3728, \[O iii\]$\lambda\lambda$4960,5008, were detected at high significance in the 20 min exposure, placing its redshift at 0.055.

The source is detected in all of the nine photometric bands included in the KiDS$+$VISTA photometry catalog, with $r = 21.58\pm0.02$ and $K_s = 20.84\pm0.18$. Our best-fit stellar population synthesis model of the photometry reveals a stellar mass of $\sim3\times10^7$ $M_\odot$ and an SFR of $\sim0.006$ $M_\odot\,{\rm yr}^{-1}$. We have used the (cite: Bruzual03) models assuming exponentially declining star-forming histories and the (cite: Chabrier03) initial mass function.

Could the SMG be gravitationally magnified by this foreground dwarf galaxy? Using the halo-mass$-$stellar-mass relation from abundance matching (cite: Bullock17), we estimate a halo mass of $\sim3\times10^{10}$ $M_\odot$. The halo mass corresponds to a line-of-sight velocity dispersion ($\sigma$) of just $\sim$29 km s$^{-1}$, assuming a singular isothermal sphere (SIS; $\rho(r) = \sigma^2/2\pi G r^2$) and the fitting function of the halo overdensity $\Delta_c(z)$ from (cite: Bryan98). The Einstein radius of the SIS can be calculated as (cite: Kneib11): $$\begin{equation}
r_E = 4\pi \frac{\sigma^2}{c^2} \frac{D_{ds}}{D_s}
\end{equation}$$ where $c$ is the speed of light, $D_{ds}$ is the angular diameter distance between the deflector and the background source, and $D_s$ is the angular diameter distance between the observer and the background source. For our system consisting of a foreground lens at $z_d = 0.055$ with $\sigma = 29$ km s$^{-1}$ and a background source at $z_s = 2.674$, the Einstein radius is $r_E \sim 0.024\ensuremath{''}$. Because $r_E$ is 33$\times$ smaller than the 0.8$''$ offset between the SMG and the foreground galaxy, we conclude that the foreground galaxy is unlikely to have any measurable lensing effect on the SMG.

# Blind Line Detection in the ALMA Band-3 Data

To search for faint emission-line sources with unknown line widths in 3D data cubes, a matched-filtering algorithm is commonly used: e.g., in SoFiA (cite: Serra15), FindClump (cite: Walter16), LineSeeker (cite: Gonzalez-Lopez19), and MF3D (cite: Pavesi18). We wrote an IDL program to implement this simple algorithm. The convolution kernel we chose to filter the data in the spectral dimension is a top-hat function with a variable half-width between $n = 1$ and $n = 9$. For each channel, the data in the neighboring $\pm n$ channels are stacked with equal weighting. Given the average channel spacing of $\sim$25 km s$^{-1}$, the convolved channel widths range between $\sim$75 km s$^{-1}$ and $\sim$475 km s$^{-1}$. As shown in (cite: Gonzalez-Lopez19), the simple top-hat function is as effective as the more sophisticated Gaussian kernels in detecting low S/N line emission.

In each convoluted channel map, we measure the rms noise level with a robust sigma routine and detect unresolved sources near the highest S/N pixel. An elliptical Gaussian fixed to the shape of the core of the dirty beam is fit to the 8$''$$\times$8$''$ subregion centered on the pixel and subtracted from the image. The parameters of the best-fit Gaussians are saved at each iteration to form the raw source catalog. The iterative process continues until the image contains no pixels above the S/N threshold of ${\rm S/N}_{\rm pix,th} = 4.5$. It is worth noting that this source-detection algorithm is similar to the minor cycles of the clean deconvolution algorithm, but here we subtract only the core of the dirty beam to save computing time. This simplified approach is justified by the low S/N of the sources other than the SMG.

Given that a single source can be detected in multiple channels and with multiple convolution kernels, we remove duplicated detections by iteratively looping through the raw source list from the highest to the lowest S/N and discard all detections within 2$''$ and 0.2 GHz from the highest S/N source remaining in the list.

Because our search is restricted to point sources, the source S/N simply scales with the ratio between the peak of the best-fit Gaussian ($S_{\rm peak}$) and the rms noise of the convolved channel map: $$\begin{equation}
{\rm S/N} = 0.77 \frac{S_{\rm peak}}{{\rm rms}},
\end{equation}$$ where a scaling factor is used to account for fitting errors (Eq. 9 of (cite: Rengelink97), see also (cite: Condon97)).

To estimate the fidelity of the detected sources, we search for sources in simulated noise-only interferometer data instead of using negative “sources” in the actual data (cite: Gonzalez-Lopez19). First, we introduce random thermal noise by replacing the calibrated MS’s visibilities with a normally distributed random array of complex numbers generated with *numpy.random*. This is equivalent to the CASA `simulator` function `setnoise` in the “simplenoise” mode, but our approach is faster because it only writes the DATA column once and does not add MODEL_DATA and CORRECTED_DATA columns to the MS. Unlike the fixed random number seed (11111) adopted in the CASA `simulator`, each noise realization uses a different seed in our code. We set the widths of the normal distributions for the real and imaginary parts to the standard deviations of the original visibilities measured with `visstat` ($\sigma \sim 250$ mJy visibility$^{-1}$ with a slight dependence on the spectral window). Then, we use `tclean` to image the noise-only visibilities into spectral data cubes with natural weighting. The same `tclean` parameters are adopted except that we turn off de-convolution by setting `niter` = 0, because the simulated data contain no sources. For each spectral window, we generate a set of 10 simulated data cubes to provide enough source counts for the source fidelity calculation.

We run the same line search code on the simulated data with the same detection parameters. We compare the normalized cumulative distribution functions (CDF) of the detected sources in the actual data and in the simulated data to estimate the source fidelity. We use the following equation, similar to LineSeeker used in the ASPECS-LP survey (cite: Gonzalez-Lopez19): $$\begin{equation}
 \label{eq:fidelity}
{\rm Fidelity} = 1-\frac{F_{\rm sim}(\ge {\rm S/N}~|~n)}{F_{\rm data}(\ge {\rm S/N}~|~n)},
\end{equation}$$ where $F(\ge {\rm S/N}~|~n)$ is the fraction of sources detected at or above the source S/N, with its detection kernel width $n$, and at any frequency channel in the spectral window. The subscript indicates whether it is from the actual data or the simulated noise-only data. $F_{\rm data}$ is measured directly from the CDF, while $F_{\rm sim}$ is obtained from the best-fit error function of the CDF to mitigate noise at high S/N due to low source counts. The fidelity is thus the probability that the detected source is not due to random noise. A source has a high fidelity near unity when $F_{\rm sim} \ll F_{\rm data}$, and a low fidelity near zero when $F_{\rm sim} \approx F_{\rm data}$.

We identified a total of six emission-line sources with ${\rm fidelity} > 0.9$ within the primary beam from the non-interpolated datacubes of all four spectral windows. We extracted the spectrum for each detection from the linear-interpolated and primary-beam-corrected data cubes with an elliptical aperture matched to the sizes of the restoring beams; i.e., we had assumed that the sources are unresolved. We measured the central frequency ($\nu_0$), FWHM, and line flux with a single-Gaussian model and list the results in Table [\[tab:codetect\]](#tab:codetect). Fig. [10](#fig:codist) illustrates the distribution of the detected sources in the field, and Fig. [11](#fig:coemitters) shows the zoomed-in version of the integrated intensity maps and their ALMA spectra.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|---:|---:|:--:|:--:|:--:|:--:|:--:|
| ID | R.A. (J2000) | Decl. (J2000) | $n$ | S/N | Fidelity | $\nu_{\rm obs}$ | FWHM | Line Flux | $z_{\rm CO32}$ | $L'_{\rm CO32}$ | PB |
|  | (hms) | (dms) |  |  |  | (GHz) | (km s$^{-1}$) | (Jy km s$^{-1}$) |  | (K km s$^{-1}$ pc$^2$) |  |
| 1 | 09:13:39.55 | $-$01:06:56.5 | 5 | 66.6 | 1.00 | 94.120 | $271\pm  5$ | $1.3435\pm0.0264$ | $2.6740\pm0.0001$ | $10.69\pm0.01$ | 0.92 |
| 2 | 09:13:38.33 | $-$01:07:08.4 | 8 | 7.0 | 1.00 | 92.241 | $388\pm 69$ | $0.1482\pm0.0282$ | $2.7488\pm0.0004$ | $9.75\pm0.08$ | 0.95 |
| 3 | 09:13:38.28 | $-$01:06:43.8 | 9 | 6.4 | 1.00 | 94.102 | $358\pm 67$ | $0.1724\pm0.0318$ | $2.6747\pm0.0003$ | $9.80\pm0.08$ | 0.73 |
| 4 | 09:13:39.42 | $-$01:06:43.0 | 1 | 6.1 | 1.00 | 92.479 | $51\pm 10$ | $0.0590\pm0.0134$ | $2.7392\pm0.0001$ | $9.35\pm0.10$ | 0.74 |
| 5 | 09:13:40.47 | $-$01:07:13.8 | 3 | 5.5 | 1.00 | 103.371 | $166\pm 32$ | $0.1509\pm0.0293$ | $2.3452\pm0.0002$ | $9.64\pm0.08$ | 0.58 |
| 6 | 09:13:40.22 | $-$01:06:59.1 | 5 | 5.2 | 0.97 | 103.767 | $184\pm 53$ | $0.0488\pm0.0260$ | $2.3324\pm0.0002$ | $9.15\pm0.23$ | 0.72 |

# Other Absorbers in the QSO Spectra

Using the low-resolution ($R \sim 2000$) BOSS spectrum of QSO1, (cite: Noterdaeme12) identified two DLA candidates at $z_{\rm abs}= 2.680$ and 2.751. Subsequently, a number of Mg ii and C iv absorbers were identified toward both QSOs using the BOSS spectra: $z_{\rm abs}= 0.9388, 2.2530, 2.7512$ toward QSO1 and $z_{\rm abs}= 0.7876, 1.0126, 1.5010, 2.7248, 2.7418$ toward QSO2 (cite: Chen15; Chen16).

The X-shooter spectra confirm all of the previously known absorbers and reveal several additional absorbers toward both QSOs: $z_{\rm abs}= 1.0855, 2.283, 2.9147$ toward QSO1 and $z_{\rm abs}= 0.886, 1.0865, 2.2525,2.2845,2.3065,2.3445,2.3595$ toward QSO2. Fig. [12](#fig:absorbers) shows portions of the X-shooter spectra to illustrate all of the major absorbers we have identified (8 toward QSO1 and 12 toward QSO2), omitting only the Mg ii absorber at $z = 1.501$ toward QSO2.

The $z_{\rm abs}\approx 2.75$ DLA toward QSO1 is apparently associated to QSO2 at $z = 2.7488$. The DLA has been previously analyzed as part of the Quasar Probing Quasar (QPQ) project using a lower-resolution GMOS spectrum, from which they measured $\log N_{\rm HI}= 21.3\pm0.15$ (cite: Prochaska13a) and rest-frame equivalent widths of $2.60\pm0.05$ Å for C ii$\lambda$1334.5 and $0.51\pm0.05$Å for C iv$\lambda$1548.2 (cite: Prochaska14). We obtained similar results using the X-shooter spectrum (Fig. [13](#fig:cgm_qso2)). With Voigt profile fitting, we find that the H i Lyman series is adequately fit with two components separated by 290 km s$^{-1}$ ($z_{\rm abs}= 2.7502, 2.7538$), each with $\log N_{\rm HI}= 21.0$ and $b = 40$ km s$^{-1}$. We thus obtain a total column density of $\log N_{\rm HI}= 21.3$ with an estimated systematic uncertainty of $\sim$0.1 dex. With the AODM method and ICs from a cloudy model with $\log N_{\rm HI}= 21.3$, $\log U = -2.5$, and the HM12 radiation background, we measure an ionization-corrected $\alpha$ metallicity of \[C/H\] = $-1.2\pm0.1$ from C iv$\lambda$1550.8 and an iron metallicity of \[Fe/H\] = $-1.6\pm0.2$ from Fe ii$\lambda$1608.5 (see Table [\[tab:qso1dla\]](#tab:qso1dla)). Given the impact parameter of $R_\bot = 85$ kpc, this DLA fits nicely with the CGM profiles of $z = 2-3$ QSOs in Fig. [8](#fig:CGMprof) (cite: Lau16).

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|---:|---:|---:|---:|---:|---:|---:|---:|
| Ion | $\lambda_{\rm rest}$ | EW | $\log N$ | \[X/H\]$^\prime$ | \[X/H\] |  |  |  |  |
|  | (Å) | (Å) | (cm$^{-2}$) |  |  |  |  |  |  |
| C  | 1334.5323 | $2.13\pm0.01$ | $>15.48$ | $>-2.25$ | $>-2.26$ |  |  |  |  |
| C  | 1548.2040 | $0.63\pm0.02$ | $14.40\pm0.03$ | $-3.33\pm0.10$ | $-1.31\pm0.10$ |  |  |  |  |
| ... | 1550.7776 | $0.45\pm0.02$ | $14.50\pm0.04$ | $-3.23\pm0.11$ | $-1.21\pm0.11$ |  |  |  |  |
| O  | 1302.1685 | $1.94\pm0.01$ | $>15.86$ | $>-2.13$ | $>-2.14$ |  |  |  |  |
| Mg  | 2796.3543 | $4.37\pm0.04$ | $>14.44$ | $>-2.46$ | $>-2.26$ |  |  |  |  |
| ... | 2803.5315 | $3.40\pm0.08$ | $>14.59$ | $>-2.31$ | $>-2.11$ |  |  |  |  |
| Al  | 1670.7886 | $1.88\pm0.01$ | $>13.99$ | $>-1.76$ | $>-1.52$ |  |  |  |  |
| Al  | 1854.7183 | $0.43\pm0.01$ | $13.45\pm0.05$ | $-2.30\pm0.11$ | $-1.59\pm0.11$ |  |  |  |  |
| Si  | 1260.4221 | $2.07\pm0.00$ | $>14.54$ | $>-2.27$ | $>-2.31$ |  |  |  |  |
| ... | 1304.3702 | $1.69\pm0.01$ | $>15.46$ | $>-1.35$ | $>-1.40$ |  |  |  |  |
| ... | 1526.7070 | $1.89\pm0.02$ | $>15.23$ | $>-1.58$ | $>-1.63$ |  |  |  |  |
| Si  | 1393.7602 | $0.67\pm0.01$ | $13.98\pm0.02$ | $-2.83\pm0.10$ | $-1.48\pm0.10$ |  |  |  |  |
| ... | 1402.7729 | $0.24\pm0.01$ | $13.79\pm0.07$ | $-3.02\pm0.12$ | $-1.68\pm0.12$ |  |  |  |  |
| Fe  | 1608.4508 | $1.33\pm0.01$ | $15.22\pm0.01$ | $-1.58\pm0.10$ | $-1.62\pm0.10$ |  |  |  |  |
| ... | 2382.7642 | $3.01\pm0.03$ | $>14.67$ | $>-2.13$ | $>-2.16$ |  |  |  |  |
| ... | 2600.1725 | $3.16\pm0.03$ | $>14.73$ | $>-2.07$ | $>-2.10$ |  |  |  |  |

# The AODM Method and Results

This Appendix gives a brief overview of the AODM method (cite: Savage91; Prochaska01) and provides tables of ionic column densities, ionization corrections, and ionization-corrected metallicities for all of the selected metal transitions (Tables [\[tab:logN\]](#tab:logN), [\[tab:IC\]](#tab:IC), and [\[tab:XH\]](#tab:XH)). Equations are all in SI units. The corresponding expressions in cgs units can be obtained by setting $\epsilon_0 = 1/4\pi$.

The velocity-dependent scattering cross section of resonance line photons is (cite: Meiksin09): $$\begin{equation}
\sigma(u) = \left( \frac{\pi e^2}{m_e c} \right) \left[ \frac{1}{4\pi \epsilon_0} \right] f \lambda_0 \phi_u, \label{eq:sigma}
\end{equation}$$ where the constants $e$, $m_e$, $\epsilon_0$, $c$, $f$, and $\lambda_0$ are respectively the electron charge, electron mass, the permeability of vacuum, the speed of light, the oscillator strength, and the rest-frame wavelength of the transition, and the function $\phi_u$ is the probability density function per unit velocity due to line broadening (i.e., a Voigt profile).

For QSO absorption lines, the optical depth \[$\tau(u)$\] at velocity $u$ is the product of this velocity-dependent cross section and the column density ($N_a$): $$\begin{equation}
\tau(u) = \frac{e^2}{4 \epsilon_0 m_e c} f \lambda_0 N_a \phi_u \equiv \frac{e^2}{4 \epsilon_0 m_e c} f \lambda_0 N_{a,u} \label{eq:Nau}
\end{equation}$$ where we have defined the column density per unit velocity, $N_{a,u} \equiv N_a \phi_u$, by shifting the velocity dependency from the cross section to the column density.

The above relation provides a method to measure column densities from observed line profiles, because the optical depth is the natural logarithmic of the ratio between the incident continuum intensity ($I_0$) and the observed attenuated intensity ($I_{\rm obs}$): $$\begin{equation}
\tau(u) = \ln \frac{I_0(u)}{I_{\rm obs}(u)}.
\end{equation}$$

The total column density can then be calculated by integrating the apparent optical depth over the velocity integration window: $$\begin{equation}
N_a = \sum N_{a,u} \Delta u = \sum \frac{4 \epsilon_0 m_e c}{e^2 f \lambda_0} \tau(u) \Delta u
\end{equation}$$ and the 1$\sigma$ *statistical* variance on the column density through standard error propagation is: $$\begin{equation}
\sigma^2_{\rm sta}(N_a) = \sum \left( \frac{4 \epsilon_0 m_e c}{e^2 f \lambda_0} \right)^2 \sigma^2[\tau(u)] \Delta u^2
\end{equation}$$ where the statistical uncertainty of optical depth is estimated from the noise spectrum: $$\begin{equation}
\sigma_{\rm sta}[\tau(u)] = \sigma[I_{\rm obs}(u)]/I_{\rm obs}(u)
\end{equation}$$

Similar to the H i Voigt profile fitting (but to a less extent because of the narrower velocity range), the ionic column density is also affected by the systematic uncertainty in our empirical model of the QSO continuum. We again adopt a $\pm$10% error in the QSO continuum ($I_0$), which directly leads to $\sigma_{\rm sys}[\tau(u)] = 0.1$ and the equation for the systematic error of the ionic column density: $$\begin{equation}
\sigma^2_{\rm sys}(N_a) = \sum \left( \frac{4 \epsilon_0 m_e c}{e^2 f \lambda_0} \right)^2 0.1^2 \Delta u^2.
\end{equation}$$

+:----+:--------------------:+----------------:+---------------:+----------------:+----------------:+----------------:+----------------:+---------------:+---------------:+
| Ion | $\lambda_{\rm rest}$ | $\log N$                                                                                                                                   |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
|     | (Å)                  | QSO1-A1         | QSO1-A2        | QSO1-B1         | QSO1-C1         | QSO1-C2         | QSO2-A2         | QSO2-B1        | QSO2-C1        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| C   | 1334.5323            | $\lesssim14.74$ | $13.94\pm0.05$ | $<12.90$        | $>15.21$        | $14.18\pm0.03$  | $14.01\pm0.06$  | $<13.33$       | $<13.25$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| C   | 1548.2040            | $<12.88$        | $<12.88$       | $<12.91$        | $14.08\pm0.04$  | $<12.91$        | $<13.20$        | $14.23\pm0.03$ | $13.61\pm0.08$ |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 1550.7776            | $<13.21$        | $<13.19$       | $<13.19$        | $14.15\pm0.07$  | $\lesssim14.83$ | $\lesssim14.30$ | $14.30\pm0.04$ | $13.72\pm0.13$ |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| O   | 1302.1685            | $14.57\pm0.03$  | $14.48\pm0.04$ | $<13.16$        | $>15.55$        | $14.36\pm0.06$  | $<13.78$        | $<13.79$       | $<13.75$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Mg  | 2796.3543            | $13.24\pm0.07$  | $12.99\pm0.08$ | ...             | $>14.09$        | $13.21\pm0.05$  | ...             | ...            | $<12.60$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 2803.5315            | $13.49\pm0.06$  | $13.15\pm0.09$ | $\lesssim14.11$ | $>14.32$        | $13.08\pm0.09$  | ...             | $<12.93$       | $<12.76$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Al  | 1670.7886            | $12.37\pm0.11$  | $11.97\pm0.28$ | $<11.70$        | $13.49\pm0.02$  | $12.15\pm0.20$  | $12.28\pm0.19$  | $<12.12$       | $<12.06$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Al  | 1854.7183            | $<12.17$        | $<12.14$       | $<12.15$        | $12.91\pm0.16$  | $<12.12$        | $<12.50$        | $<12.53$       | $<12.49$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Si  | 1304.3702            | $13.76\pm0.12$  | $13.22\pm0.40$ | $<12.93$        | $14.81\pm0.02$  | $13.32\pm0.34$  | $<13.52$        | $<13.55$       | $<13.48$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 1526.7070            | $13.78\pm0.08$  | $<13.23$       | $<13.15$        | $14.76\pm0.02$  | $13.55\pm0.12$  | $<13.58$        | $<13.50$       | $<13.38$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Si  | 1393.7602            | $<12.30$        | $<12.30$       | $<12.36$        | $\lesssim13.70$ | $<12.56$        | $13.15\pm0.11$  | $<12.76$       | $<12.77$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 1402.7729            | $<12.82$        | $<12.84$       | $<12.79$        | $13.54\pm0.11$  | $<12.80$        | $<13.22$        | $<13.42$       | $<13.12$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Fe  | 1608.4508            | $13.55\pm0.26$  | $<13.39$       | $<13.44$        | $14.52\pm0.05$  | $<13.36$        | $<13.64$        | $<13.74$       | $<13.71$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 2382.7642            | $13.34\pm0.05$  | $12.90\pm0.13$ | $<12.58$        | $\lesssim14.47$ | $\lesssim13.90$ | $<12.79$        | $<12.66$       | $<12.71$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 2600.1725            | $\lesssim13.64$ | $13.13\pm0.10$ | $<12.58$        | $>14.25$        | $12.91\pm0.17$  | $<13.18$        | $<12.92$       | $<12.94$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+

+:----+---------:+---------:+---------:+---------:+---------:+---------:+---------:+--------:+
| Ion | ${\rm IC} \equiv \log f_{\rm HI} - \log f_{\rm X}$                         |         |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
|     | QSO1-A1  | QSO1-A2  | QSO1-B1  | QSO1-C1  | QSO1-C2  | QSO2-A2  | QSO2-B1  | QSO2-C1 |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| C   | $-0.18$  | $-0.10$  | $-1.74$  | $-0.08$  | $-0.58$  | $-0.90$  | $-1.74$  | $-1.74$ |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| C   | $2.78$   | $1.90$   | $-2.82$  | $2.00$   | $1.98$   | $0.40$   | $-2.82$  | $-2.82$ |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| O   | $-0.01$  | $-0.01$  | $2.56$   | $-0.01$  | $-0.04$  | $0.02$   | $2.56$   | $2.56$  |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| Mg  | $0.14$   | $0.25$   | $0.04$   | $0.27$   | $-0.36$  | $-0.71$  | $0.04$   | $0.04$  |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| Al  | $-0.05$  | $0.06$   | $-1.08$  | $0.12$   | $-0.68$  | $-1.20$  | $-1.08$  | $-1.08$ |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| Al  | $0.61$   | $0.55$   | $-1.18$  | $0.59$   | $0.21$   | $-0.51$  | $-1.18$  | $-1.18$ |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| Si  | $-0.21$  | $-0.14$  | $-1.17$  | $-0.12$  | $-0.62$  | $-0.95$  | $-1.17$  | $-1.17$ |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| Si  | $1.61$   | $1.03$   | $-2.37$  | $1.13$   | $0.83$   | $-0.46$  | $-2.37$  | $-2.37$ |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+
| Fe  | $-0.12$  | $-0.08$  | $1.58$   | $-0.07$  | $-0.37$  | $-0.49$  | $1.58$   | $1.58$  |
+-----+----------+----------+----------+----------+----------+----------+----------+---------+

+:----+:--------------------:+----------------:+---------------:+----------------:+----------------:+----------------:+----------------:+---------------:+---------------:+
| Ion | $\lambda_{\rm rest}$ | ${\rm [X/H]} \equiv {\rm [X/H]}^\prime + {\rm IC}$                                                                                         |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
|     | (Å)                  | QSO1-A1         | QSO1-A2        | QSO1-B1         | QSO1-C1         | QSO1-C2         | QSO2-A2         | QSO2-B1        | QSO2-C1        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| C   | 1334.5323            | $\lesssim-1.51$ | $-2.66\pm0.08$ | $<-1.25$        | $>-1.53$        | $-1.62\pm0.29$  | $-1.91\pm0.34$  | $<-0.87$       | $<-0.92$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| C   | 1548.2040            | $<-0.41$        | $<-1.72$       | $<-2.32$        | $-0.59\pm0.09$  | $<-0.33$        | $<-1.42$        | $-1.05\pm0.19$ | $-1.63\pm0.13$ |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 1550.7776            | $<-0.08$        | $<-1.41$       | $<-2.04$        | $-0.52\pm0.10$  | $\lesssim 1.59$ | $\lesssim-0.32$ | $-0.98\pm0.19$ | $-1.53\pm0.16$ |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| O   | 1302.1685            | $-1.77\pm0.06$  | $-2.28\pm0.08$ | $<3.05$         | $>-1.38$        | $-1.15\pm0.30$  | $<-1.48$        | $<3.63$        | $<3.62$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Mg  | 2796.3543            | $-1.87\pm0.09$  | $-2.42\pm0.10$ | ...             | $>-1.47$        | $-1.53\pm0.29$  | ...             | ...            | $<1.04$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 2803.5315            | $-1.61\pm0.08$  | $-2.26\pm0.11$ | $\lesssim 2.57$ | $>-1.24$        | $-1.66\pm0.30$  | ...             | $<1.34$        | $<1.20$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Al  | 1670.7886            | $-1.77\pm0.12$  | $-2.47\pm0.29$ | $<0.19$         | $-1.08\pm0.08$  | $-1.77\pm0.35$  | $-1.96\pm0.38$  | $<0.56$        | $<0.52$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Al  | 1854.7183            | $<-1.31$        | $<-1.82$       | $<0.54$         | $-1.18\pm0.17$  | $<-0.91$        | $<-1.05$        | $<0.87$        | $<0.87$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Si  | 1304.3702            | $-1.60\pm0.13$  | $-2.49\pm0.40$ | $<0.27$         | $-1.05\pm0.08$  | $-1.60\pm0.45$  | $<-1.53$        | $<0.84$        | $<0.80$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 1526.7070            | $-1.57\pm0.09$  | $<-2.48$       | $<0.48$         | $-1.10\pm0.08$  | $-1.37\pm0.31$  | $<-1.48$        | $<0.79$        | $<0.70$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Si  | 1393.7602            | $<-1.23$        | $<-2.24$       | $<-1.50$        | $\lesssim-0.91$ | $<-0.91$        | $-1.41\pm0.35$  | $<-1.14$       | $<-1.11$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 1402.7729            | $<-0.72$        | $<-1.70$       | $<-1.07$        | $-1.07\pm0.13$  | $<-0.68$        | $<-1.34$        | $<-0.49$       | $<-0.76$       |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| Fe  | 1608.4508            | $-1.71\pm0.27$  | $<-2.24$       | $<3.54$         | $-1.27\pm0.09$  | $<-1.30$        | $<-0.94$        | $<3.79$        | $<3.79$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 2382.7642            | $-1.92\pm0.07$  | $-2.73\pm0.15$ | $<2.68$         | $\lesssim-1.33$ | $\lesssim-0.76$ | $<-1.79$        | $<2.71$        | $<2.80$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+
| ... | 2600.1725            | $\lesssim-1.62$ | $-2.51\pm0.12$ | $<2.69$         | $>-1.55$        | $-1.76\pm0.34$  | $<-1.39$        | $<2.98$        | $<3.02$        |
+-----+----------------------+-----------------+----------------+-----------------+-----------------+-----------------+-----------------+----------------+----------------+

# The Identification of The Emission Counterpart of Subsystem C

In the deep $r$-band image from KiDS (5$\sigma$ limit at $\sim$25 mag) shown in Fig. [14](#fig:fchartC)$a$, we labeled four faint optical sources within 7$''$ of QSO1. Here we explore whether any of these sources is connected to the DLA at $z_{\rm abs}\approx 2.68$ by examining their photometric redshifts and their ALMA spectra.

Three of the sources (A, B, C) are listed in the joint KiDS-VISTA 9-band photometric catalog (cite: Kuijken19):

- KiDSDR4 J091338.791$-$010700.71 (A): $r = 23.6\pm0.1$, $H = 22.3\pm0.4$, $z_{\rm p} = 1.09^{+0.09}_{-0.15}$;

- KiDSDR4 J091338.711$-$010705.48 (B): $r = 24.5\pm0.2$, $H = 22.9\pm0.7$, $z_{\rm p} = 0.45^{+0.78}_{-0.12}$.

- KiDSDR4 J091338.527$-$010703.60 (C): $r = 23.8\pm0.1$, $H = 22.0\pm0.3$, $z_{\rm p} = 0.79^{+0.45}_{-0.06}$.

where the $r-$ and $H$-band magnitudes are from the homogenized “Gaussian Aperture and PSF (GAaP)” photometry and $z_{\rm p}$ are the 9-band photometric redshift estimates from the Bayesian photometric redshift code `BPZ` (cite: Benitez00). The 68% confidence intervals of the photometric redshifts suggest that both sources are in the far foreground of the SMG SMM J0913 ($z_{\rm SMG}= 2.674$).

The fourth object (D) is not in the catalog likely because its proximity to the bright QSO1. We measured its position directly from the image: R.A. = $09^{\rm h}13^{\rm m}39.05^{\rm s}$, Decl. = $-01^\circ07\ensuremath{'}06.5\ensuremath{''}$.

We then extracted spectra at their optical positions from the ALMA band-3 datacube. For objects A, B, and D, we adopted elliptical apertures matching the synthesized beam size (1.7$''$$\times$1.3$''$ at PA = 49$^\circ$). We show these spectra in Fig. [14](#fig:fchartC)$c$. Even at the depth of our ALMA data (rms$= 0.155$ mJy beam$^{-1}$ channel$^{-1}$ in BB4), none of the sources show emission lines at a detectable level.

For Object C, we initially used an aperture centered on the optical position and detected hints of emission lines at the expected frequencies of absorption-line clouds C1 and C2. We then made a CO map by combining the two channels that show the most significant emission. The CO image in Fig. [14](#fig:fchartC)$b$ led to the discovery of Comp b as it reveals a highly significant source $\sim$3$''$ to the SSW of the optical position, which we have designated as Comp b. Guided by the CO image, we re-extracted a spectrum from a 3.4$''$$\times$1.8$''$ elliptical aperture that matches the geometry of Comp b to optimize the line detection. This spectrum is shown in the Object C panel of Fig. [14](#fig:fchartC)$c$. Line emission is clearly detected at the expected frequencies of absorption-line clouds C1 and C2 toward QSO1. Through this exercise, we have identified Comp b as the most likely emission counterpart of absorption subsystem C toward both QSOs.

[^1]: Although most of the difference in $\tau_{\rm dep}$ is driven by the conversion factor from CO to molecular gas ($\alpha_{\rm CO} \equiv M_{\rm mol}/L_{\rm CO}^\prime$ in units of $M_\odot/({\rm K~km~s^{-1}~pc^2})$), constraints from dynamical masses and dust masses have shown that SMGs indeed have lower $\alpha_{\rm CO}$ than that of normal star-forming galaxies (cite: Hodge12; Magnelli12b; Xue18) and that the value adopted from local ultraluminous IR galaxies (cite: Downes98; Papadopoulos12b) is more appropriate for SMGs than the Galactic value (cite: Bolatto13).

[^2]: Column densities are given in units of cm$^{-2}$ throughout the paper.

[^3]: The two terms have been used interchangeably.

[^4]: <https://github.com/specdb/specdb>

[^5]: <https://people.ast.cam.ac.uk/~rfc/vpfit.html>

[^6]: <ftp://ftp.ast.cam.ac.uk/pub/gdb/>

[^7]: <https://github.com/linetools/linetools>

[^8]: The derived ICs are insensitive to the assumed metallicity.

[^9]: Comparable to the neutral fractions estimated by our photoionization models in Table [\[tab:aodm\]](#tab:aodm).

</paper>

Write the methods card for this paper.