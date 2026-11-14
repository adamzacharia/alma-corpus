# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.498.3624L\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.498.3624L",
 "title": "Constraints on the electron-to-proton mass ratio variation at the epoch of reionization",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Levshakov, S. A.",
 "n_authors": 3,
 "arxiv_id": "2008.11143",
 "doi": "10.1093/mnras/staa2635",
 "alma_projects_linked_by_archive": [
  "2015.1.01265.S"
 ]
}
```

Paper text:
<paper>
# *Constraints on the electron-to-proton mass ratio variation at the epoch of reionization*

## Abstract

Far infrared fine-structure transitions of \[C i\] and \[C ii\] and rotational transitions of CO are used to probe hypothetical variations of the electron-to-proton mass ratio $\mu = m_{\rm e}/m_{\rm p}$ at the epoch of reionization ($z > 6$). A constraint on $\Delta\mu/\mu$ = $(\mu_{\rm obs} - \mu_{\rm lab})/\mu_{\rm lab} = (0.7 \pm 1.2)\times10^{-5}$ ($1\sigma$) obtained at $\bar{z} = 6.31$ is the most stringent up-to-date limit on the variation of $\mu$ at such high redshift. For all available estimates of $\Delta\mu/\mu$ ranging between $z = 0$ and $z \sim 1100$, – the epoch of recombination, – a regression curve $\Delta\mu/\mu$ = $k_\mu (1+z)^p$, with $k_\mu = (1.6 \pm 0.3)\times10^{-8}$ and $p = 2.00 \pm 0.03$, is deduced. If confirmed, this would imply a dynamical nature of dark matter/dark energy.

cosmology: observations – cosmological parameters – techniques: spectroscopic – quasars: individual: J0439+1634, J2310+1855 – elementary particles

# Introduction

A plethora of models for the dark sector (dark matter and dark energy) suppose the existence of Higgs-like scalar field(s) which couple non-universally to the matter content of the Standard Model (SM) of particle physics (for reviews see, e.g., Battaglieri et al. 2017; Irastorza & Redondo 2018; Beacham et al. 2019). Such coupling could change the masses of particles, thus leading to violation of the weak equivalence principle, and giving rise to the so-called 5$th$ force. However, all attempts to discover traces of any interaction beyond the SM in experiments on Earth and even in satellite missions have led to a null result (Thompson 2019a,b, 2018, 2017; Banerjee et al. 2018; Bergé et al. 2018; Antoniou & Perivolaropoulos 2017; Rider et al. 2016; Brax & Davis 2016; Li et al. 2016; Hamilton et al. 2015; Wagner et al. 2012). This means that the 5$th$ force – if exists – should be extremely long-ranged (with characteristic scales of order of galactic to intergalactic distances) and/or some screening mechanisms should be present which suppress the coupling strength in the environments where the experiments were performed (Brax 2018). In this respect the objects where the non-standard interactions could be expected from either the phenomenology or from theoretical considerations are more amenable to search for hidden fields.

The rotational curve of the Milky Way (MW) shows that the total matter (and the gravitational potential) within the solar circle is dominated by baryons with $\rho_{\rm b}/\rho_{\scriptscriptstyle{\rm DM}} \sim 10$, where $\rho_{\rm b}$ is the baryon density and $\rho_{\scriptscriptstyle{\rm DM}}$ is the density of dark matter (DM) (McGaugh 2018; McMillan 2017; Iocco et al. 2015; Sofue et al. 2009). Thus, the non-detection of a signal from the dark sector in objects located in the vicinity of the galactic position of the Sun is at least conceivable. On the other hand, studies of stellar dynamics revealed the regions where the gravitational potential indeed becomes DM-dominated – these are the low surface brightness dwarf galaxies or the outskirts of ’normal’ galaxies. In the quest for the ’dark’ signal, targets in such regions seem to be more favorable.

Extremely high-redshift objects also represent a perspective group. For instance, investigations of the ionization processes at redshift $z \sim 1100$ which are responsible for the temperature and polarization anisotropies of the cosmic microwave background (CMB) radiation (Hannestad 1999; Kaplinghat et al. 1999; Kujat & Scherrer 2000; Yoo & Scherrer 2003; Ichikawa et al. 2006; Planck Collaboration et al. 2015; Hart & Chluba 2020) show that the value of the Hubble constant $H_0$ correlates with the electron mass. As a consequence, an increased effective electron mass at the epoch of recombination, $m_{{\rm e},z} = (1.0190\pm0.0055)m_{\rm e,0}$, leads to a shifted value of the Hubble constant $H_0 \simeq 71$ km s$^{-1}$ Mpc$^{-1}$ as compared with that inferred from the $\Lambda$ cold dark matter model ($\Lambda$CDM) calibrated by Planck CMB data $H_0 = 67.4\pm0.5$ km s$^{-1}$ Mpc$^{-1}$ (Planck Collaboration et al. 2018). This interplay between $m_{{\rm e},z}$ and $H_0$ may alleviate the so-called Hubble tension – the difference between the Hubble constant measured in the late Universe ($z \;
\raise 0.3ex\hbox{$<$\kern-0.75em\raise-1.1ex\hbox{$\sim$}}\; 1$), $H_0 = 74.03\pm1.42$ km s$^{-1}$ Mpc$^{-1}$ (Riess et al. 2019) and $H_0 = 73.3\pm1.8$ km s$^{-1}$ Mpc$^{-1}$ (Wong et al. 2019), and the CMB value.

Another high-redshift control point is the cosmic dawn ($z \;
\raise 0.3ex\hbox{$<$\kern-0.75em\raise-1.1ex\hbox{$\sim$}}\; 20$). The depth of the H i 21-cm absorption trough at $z = 14-21$ detected in EDGES by Bowman et al. (2018) turned out to be twice as large as predicted what required additional mechanisms to explain it. Many models consider now different types of non-gravitational interaction between dark and baryonic matter as factors which could cool the neutral gas (Barkana et al. 2018; Houston et al. 2018; Fraser et al. 2018; Safarzadeh et al. 2018; Yang W. et al. 2019; Famaey et al. 2020).

The subsequent epoch of reionization ($6 < z < 10$) is characterized by the progressive ionization of the previously neutral intergalactic medium that makes possible observations across much of the electromagnetic spectrum. This results in a variety of methods which can be devised to test theoretical models beyond the SM. In particular, in the present paper we probe the non-standard coupling in two objects at $z > 6$ by means of radio spectroscopy of atomic and molecular transitions. Note that the cosmic time interval between $z=6$ and $z=1100$ is about 900 Myr, i.e., less than 1/10$th$ of the Hubble time, and between $z=6$ and $z=17$ is only 640 Myr[^2].

The theoretically predicted coupling affects preferentially the electron mass, whereas the mass of the proton is determined by the strength of the strong interaction of quarks and remains less affected. Therefore, the electron-to-proton mass ratio $\mu = m_{\rm e}/m_{\rm p}$ can be used as a probe to search for the hidden scalar fields.

Measurements of this ratio employ a variety of atomic and molecular transitions which have a different sensitivity to small changes in $\mu$, or in the fine structure constant $\alpha = e^2/\hbar c$, or in a combination of $\mu$ and $\alpha$, $F = \alpha^2/\mu$. However, Higgs-like couplings assume that the variations of $\alpha$ – if any – are typically much smaller than those of $\mu$ (e.g., Yoo & Scherrer 2003), so that in the first approximation $\alpha$ can be considered as a constant. If relative offsets between different molecular frequencies induced by the alleged changes in $\mu$ are large enough, they can be measured by direct spectroscopic methods in optical and radio bands (Kozlov & Levshakov 2013; Ubachs 2018).

Up to now, the most accurate probes of $\mu$ were obtained in Galactic molecular clouds distributed in the MW disk where the Galactic gravitational potential is the same as in the Solar system and $\rho_{\rm b}/\rho_{\scriptscriptstyle{\rm DM}} \sim 10$. The upper limit ($1\sigma$) on the fractional change in $\mu$, $\Delta\mu/\mu = (\mu_{\rm obs} - \mu_{\rm lab})/\mu_{\rm lab}$, for the MW disk clouds was found to be $|\Delta \mu/\mu| < 0.9\times10^{-8}$ (Levshakov et al. 2013). Employing methanol (CH$_3$OH) absorption-line transitions, Kanekar et al. (2015) obtained $|\Delta \mu/\mu| < 0.6\times10^{-7}$ for a molecular cloud in a distant galaxy at $z = 0.89$ which is a high-redshift analogue to the MW, i.e., the total mass balance in this galaxy is probably dominated by baryonic matter. On the other hand, for an object in the Large Magellanic Cloud located at the galactocentric distance where $\rho_{\rm b}/\rho_{\scriptscriptstyle{\rm DM}} < 1$ we deduced $\Delta \mu/\mu = (1.7 \pm 0.7)\times10^{-7}$ (Levshakov et al. 2019). Similarly, a value of $\Delta \mu/\mu = (3.5 \pm 1.2)\times10^{-7}$ was reported by Kanekar (2011) for a faint dwarf galaxy at $z = 0.69$ where the dark matter may prevail. However, the last two values may be affected by non evaluated systematics and require further investigations.

As for the measurements at high-redshifts, previously we estimated the value of $\Delta F/F = (F_{\rm obs}-F_{\rm lab})/F_{\rm lab}$ for two distant quasars BR 1202–0725 ($z = 4.69$) and J1148+5251 ($z = 6.42$) where $|\Delta F/F| < 1.5\times10^{-4}$ (Levshakov et al. 2008), and for a lensed galaxy HLSJ091828.6+514223 at $z = 5.24$ where $|\Delta F/F| < 1.5\times10^{-5}$ (Levshakov et al. 2012). Later on, the result towards J1148+5251 was slightly improved to $|\Delta F/F| < 4\times10^{-5}$ (Levshakov et al. 2017).

Here we evaluate two additional limits on $\mu$-variation using published IRAM/NOEMA spectra of the most distant gravitationally lensed quasar J0439+1634 at $z=6.519$ (Yang J. et al. 2019; herein referred to as Y19) and new ALMA observations of the quasar J2310+1855 at $z=6.003$ (Li et al. 2020; herein referred to as L20). Combining all points ranging between $z = 6.0$ and $z = 6.5$, we obtain the most stringent limit on $\mu$ variations at the end of the epoch of reionization.

# Data and method

The radial velocity offset, $\Delta V = V_{\rm rot} - V_{\rm fs}$, between low-lying rotational lines of carbon monoxide and atomic far infrared (FIR) fine-structure lines, being interpreted in terms of the fractional change in the quotient $F = \alpha^2/\mu$, or in the product $F = \tilde{\mu}\alpha^2$ gives (Levshakov et al. 2008): $$\begin{equation}
{\Delta V}/{c} = \Delta F/F  = 2\Delta\alpha/\alpha - \Delta\mu/\mu = \Delta z/(1 + \bar{z}),
\label{Equ1}
\end{equation}$$ or $$\begin{equation}
{\Delta V}/{c} = 2\Delta\alpha/\alpha + \Delta\tilde{\mu}/\tilde{\mu} = \Delta z/(1 + \bar{z}).
\label{Equ1a}
\end{equation}$$ Here $\tilde{\mu} = \mu^{-1}$, $c$ is the speed of light, $\Delta z = z_{\rm rot} - z_{\rm fs}$ is the redshift difference between the rotational and fine-structure lines, $\bar{z}$ is their mean redshift, and $z_{\rm rot}$, $z_{\rm fs}$ are related to the observed and laboratory frequencies, $\nu_{\rm obs}$ and $\nu_{\rm lab}$, via $$\begin{equation}
z = \nu_{\rm lab}/\nu_{\rm obs} - 1.
\label{Equ2}
\end{equation}$$ As already mentioned above, Higgs-like couplings do not change $\alpha$. Therefore, in this paper we will assume that $\alpha$ is kept fixed. In this approximation, we have $$\begin{equation}
\Delta F/F \approx -\Delta\mu/\mu .
\label{Equ2a}
\end{equation}$$

Velocity offsets $\Delta V$ measured in astrophysical objects usually include also random shifts caused by the heterogeneous spatial distribution of different species which may not trace each other exactly. On the other hand, in the present case we analyze integrated emission over the whole surface of a distant galaxy which means that such random shifts are already to a great extent averaged. Nevertheless, we define $\Delta V$ as a sum of two components — $\Delta V_F$ due to $F$-variations, and $\Delta V_D$ due to random kinematic effects (the so-called Doppler noise): $$\begin{equation}
\Delta V = \Delta V_F + \Delta V_D.
\label{Equ3}
\end{equation}$$ The Doppler noise is supposed to be normally distributed with a zero mean and a finite variance, and the signal $\Delta V_F$ can be estimated statistically by averaging over a data sample: $$\begin{equation}
\langle \Delta V \rangle = \langle \Delta V_F \rangle , \;\;\;
{\rm Var}(\Delta V) = {\rm Var}(\Delta V_F) + {\rm Var}(\Delta V_D).
\label{Equ4}
\end{equation}$$

For a single system, the dispersion of the Doppler noise can be estimated from the comparison of the velocity offsets between spectral lines of similar species which are linked to each other by a certain physical conditions. In our case these are \[C i\], \[C ii\], and CO lines. Low-lying rotational lines of carbon monoxide and FIR fine-structure lines of atomic carbon trace neutral gas which is well shielded from the ionizing radiation (Hollenbach & Tielens 1999) and, as a result, in molecular clouds their profiles are similar (Okada et al. 2019). As for \[C ii\], its FIR fine-structure emission is usually enhanced at the edges of molecular clouds in the photodissociation regions (PDRs). However, diffuse gas from the H ii regions can also contribute to some extent ($\;
\raise 0.3ex\hbox{$<$\kern-0.75em\raise-1.1ex\hbox{$\sim$}}\; 30$%, e.g., Kaufman et al. 1999) to the intensity of the ‘PDR’ lines, being integrated over the surface distribution of the \[C i\]/\[C ii\]/CO emitting gas of a galaxy. As a result, \[C ii\] lines may have a slightly wider profiles than \[C i\] and CO lines if H ii regions occupy considerable volume of the observed galaxy.

In the present paper, we analyze radial velocity offsets between the rotational lines of CO(5-4) 576.26793050(5) GHz, CO(6-5) 691.4730763(5) GHz, CO(7-6) 806.65180600(50) GHz, CO(8-7) 921.79970000(50) GHz, CO(9-8) 1036.91239300(50) GHz (Endres et al. 2016), and the FIR fine-structure lines of \[C i\] ${}^3{\rm P}_2 \rightarrow {}^3{\rm P}_1$ 809.341970(17) GHz (Haris & Kramida 2017), and \[C ii\]  $^2{\rm P}_{3/2} \rightarrow {}^2{\rm P}_{1/2}$ 1900.5369(13) GHz (Cooksy et al. 1986). These lines were observed in emission towards two distant quasars: J0439+1634 at $z = 6.519$ (Y19), and J2310+1855 at $z = 6.003$ (L20). Among them, only \[C i\], \[C ii\], CO(6-5), CO(7-6) and CO(9-8) demonstrate simple symmetric profiles and were taken with the same spectral resolution, $\Delta_{\rm ch} \simeq 50$ km s$^{-1}$ per channel.

The emission lines of CO(6-5), CO(7-6) and \[C i\] were detected in a single setting with receiver 1 (3 mm) and the angular resolution of $\theta = 6.\!''2 \times 3.\!''2$. The CO(9-8) line was observed with receiver 2 (2 mm) and $\theta = 3.\!''1 \times 2.\!''4$, whereas observations of \[C ii\] were performed with receiver 3 (1 mm) in two settings $\theta_1 = 4.\!''9 \times 1.\!''9$, and $\theta_2 = 1.\!''2 \times 0.\!''7$. In spite of different angular resolutions, all the IRAM/NOEMA detections are spatially unresolved.

However, J0439+1634 is a compact lensed quasar with a maximum image separation $\theta \sim 0.\!''2$ (Fan et al. 2019), and this fact may affect line profiles due to differential lensing, i.e., the lensing pattern of distant objects may cause complex velocity profiles of emission lines in the spatially unresolved images in case of different lensing magnifications of emitting regions (e.g., Rivera et al. 2019; Yang C. et al. 2019). This may modify the offset between the relative positions of spectral lines.

A combination of \[C i\]/\[C ii\]/CO lines, — the so-called Fine Structure Method (FSM), — has already been used in differential measurements of the fundamental physical constants in a wide redshift range — from $z \simeq 0$ up to $z \simeq 7$ (Levshakov et al. 2008, 2010, 2012, 2017, 2019; Curran et al. 2011; Weiß et al. 2012). To note is also that the FSM provides, at least, a factor of 30 more sensitive probe of the variability of physical constants than traditionally used UV and optical resonance lines of atoms and ions (Levshakov et al. 2008; Kozlov et al. 2008).

The accurate determination of the centroid $(V_0)$ and the full width at half maximum (FWHM) of a spectral line is crucial for high-precision measurements. If the line profile is a Gaussian then the statistical uncertainty of centroid is given by (e.g., Landman et al. 1982): $$\begin{equation}
\sigma_0 \simeq \frac{0.7 \Delta_{\rm ch}}{\rm SN} \sqrt{n},
\label{Equ5}
\end{equation}$$ where $\Delta_{\rm ch}$ is the channel width, SN — the signal-to-noise ratio, and $n = {\rm FWHM}/\Delta_{\rm ch}$ — the line width in units of channels.

Apart from the statistical uncertainty $\sigma_0$, there are systematic errors related to instrumental effects such as LSR corrections, $\sigma_{\scriptscriptstyle {\rm LSR}}$, and uncertainties in the rest frame frequencies, $\sigma_{\rm rest}$. For instance, a long periodic trend in the LSR corrections due to the effect of Jupiter is $\sigma_{\scriptscriptstyle \rm LSR} \simeq 12$ m s$^{-1}$, and the largest uncertainty of the rest frame frequency of $\sigma_{\rm rest} = 200$ m s$^{-1}$ belongs to \[C ii\] (Cooksy et al. 1986). Both of them is, however, much smaller than the channel width $\Delta_{\rm ch} \simeq 50$ km s$^{-1}$ of the spectral data in question. If, for a moment, we ignore these systematic errors, $\sigma_{\scriptscriptstyle \rm LSR}$ and $\sigma_{\rm rest}$, then for a moderate quality data with SN $\sim 10-20$ and $n \sim 5-6$ the relative statistical error, $\delta_0 = \sigma_0/\Delta_{\rm ch}$, is about $1/10th$ of the channel width. On the other hand, for a high quality data with SN $> 100$ the centroid limiting accuracy will be restricted by the systematic errors which for the case of the \[C ii\]/CO pairs provides a limiting accuracy of $\sigma(\Delta F/F)_{\rm lim} \simeq 7\times10^{-7}$, whereas for the \[C i\]/CO pairs it is $\simeq 2\times10^{-8}$.

Before processing, we subtracted baselines from each spectrum. The baseline was defined from the regression analysis of the mean signals from spectral intervals without emission lines and/or noise spikes. In each such interval the *rms* noise level was determined as well. Since individual *rms* uncertainties were of the same order of magnitude, their mean value was assigned to the whole spectrum.

# Results

## Constraints on $\mu$-variation at $z=6.519$

IRAM/NOEMA spectra of J0439+1634 exhibit four rotational transitions of CO: $J = 6\rightarrow5, 7\rightarrow6, 9\rightarrow8$, and $10\rightarrow9$. We do not use the last one since it is blended with the H$_2$O 3$_{1,2}$–2$_{2,1}$ emission line. The selected CO lines together with \[C ii\] and \[C i\] are shown by black histograms in Fig. [1](#Fg1). Each individual line was fitted by a single-component Gaussian model (shown by red). The residual uncertainties are plotted by the lower black histograms. All emission line profiles are well described by the Gaussian model with the minimum values of $\chi^2$ per degrees of freedom of about 1.

The derived model parameters are listed in Table [\[T1\]](#T1). The strongest line is \[C ii\] with a line flux ${\cal F}_{\scriptscriptstyle \rm [CII]}$ more than 5 times exceeding the other line fluxes. It was also observed with a high signal-to-noise ratio. Since the measured redshift of $z_{\scriptscriptstyle \rm [CII]} = 6.51877(11)$ is in good agreement with the previous result $z_{\scriptscriptstyle \rm [CII]} = 6.5188(1)$ of Y19, we used \[C ii\] as a reference line for the velocity scale shown in Fig. [1](#Fg1).

l r@.l r@.l c r@.l r@.l & & & FWHM & &\
& & & (km s$^{-1}$) &\
& 252&7725(38) & 0&249(12) & 295(14) & 10&96(5) & 6&51877(11)\
& 107&6406(49) & 0&090(12) & 251(33) & 0&54(15) & 6&51893(34)\
CO(6-5) & 91&9682(13) & 0&082(4) & 267(13) & 1&61(8) & 6&51861(11)\
CO(7-6) & 107&2778(18) & 0&101(5) & 282(14) & 1&60(8) & 6&51928(13)\
CO(9-8) & 137&9120(34) & 0&141(11) & 315(24) & 2&28(15) & 6&51865(19)\

In spite of a larger line width of \[C ii\] than that of \[C i\] (FWHN = 294 km s$^{-1}$ vs. 251 km s$^{-1}$), both values match each other within the measured $1\sigma$ uncertainty intervals. As for the widths of the CO lines, they show a tendency of increasing FWHM with increasing $J$: the cold gas ($T_{\rm kin} \;
\raise 0.3ex\hbox{$<$\kern-0.75em\raise-1.1ex\hbox{$\sim$}}\; 100$ K) tracers CO(6-5) and CO(7-6) have a compatible line width with that of \[C i\], whereas CO(9-8) is broader — the value of FWHM$_{\scriptscriptstyle \rm CO(9-8)}$ is shifted towards the width of FWHM$_{\scriptscriptstyle \rm [CII]}$. Since at the galactic scales the observed line profiles are formed by the global velocity field, it indicates that the contribution of warm gas ($T_{\rm kin} \sim 200$ K) to emissivity of \[C ii\] and CO(9-8) may be essential for the quasar host galaxy J0439+1634. The observed similarity of line profiles implies that the warm and cold gas are well mixed throughout the galactic disk.

As mentioned above, the observed profile of \[C ii\] is well fitted by a single-component Gaussian model. However, at $V \simeq -350$ km s$^{-1}$ in the residual uncertainties (Fig. [1](#Fg1)) there is an excess of four channel widths which may indicate the presence of a weak blueshifted subcomponent. We note that a blueshift of $310\pm120$ km s$^{-1}$ between the main component of \[C ii\] and the optical Mg ii ($\lambda_0 = 2798$ Å) emission line from the near-infrared spectrum of J0439+1634 (Fan et al. 2019) was previously revealed in Y19.

The dispersion of the measured redshifts is illustrated in Fig. [2](#Fg2), left panel. The largest deviation from the reference point $z_{\scriptscriptstyle \rm [CII]}$ is observed for CO(7-6) with the velocity offset $\Delta V = 20.3$ km s$^{-1}$, which is about one half of the channel size against an expected $\simeq 0.1\Delta_{\rm ch}$, as in the case of \[C i\], CO(6-5), and CO(9-8). The reason for such a large velocity offset is unclear and probably due to some systematic effects because CO $J = 7 \rightarrow 6$ is an intermediate transition between $J = 6 \rightarrow 5$ and $J = 9 \rightarrow 8$, and, hence, its apparent shift cannot be explained as a result of varying physical conditions in emitting regions traced by different CO lines.

To estimate an upper limit on $\Delta\mu/\mu$, at first we average separately the redshifts of the fine structure lines \[C i\] and \[C ii\], and the CO rotational transitions listed in Table [\[T1\]](#T1). It gives $\langle z \rangle_{\rm fs} = 6.51885(18)$ and $\langle z \rangle_{\rm rot} = 6.51885(9)$. Then we calculated $\Delta\mu/\mu$ = $(\langle z \rangle_{\rm rot} -
\langle z \rangle_{\rm fs})/(1 + \bar{z}) = (0.0 \pm 2.7)\times10^{-5}$ ($1\sigma$).

## Constraints on $\mu$-variation at $z=6.003$

Here we tighten our constraint on $\Delta\mu/\mu$ at $z = 6.519$ towards the quasar J2310+1855 at $z=6.003$ using the updated values of velocity offsets between four high-$J$ rotational transitions of CO ($J = 5 \rightarrow 4$, $J = 6 \rightarrow 5$, $J = 8 \rightarrow 7$, and $J = 9 \rightarrow 8$) and the fine-structure line of \[C ii\] $^2$P$_{3/2} \rightarrow ^2$P$_{1/2}$.

In our previous analysis of this quasar (Levshakov et al. 2017), we used the CO(6-5) line from PdBI observations with angular resolution $\theta = 5.\!''4 \times 3.\!''9$, and the \[C ii\] line from ALMA observations with $\theta = 0.\!''72 \times 0.\!''51$ (Wang et al. 2013). The redshift of $z_{\scriptscriptstyle \rm CO(6-5)} = 6.0025(7)$ and $z_{\scriptscriptstyle \rm [CII]} = 6.0031(2)$ gave an upper limit on \|$\Delta\mu/\mu$\| $< 10^{-4}$. Additional observations of J2310+1855 in CO lines with ALMA (L20; Feruglio et al. 2018) and IRAM/NOEMA (L20) allow us to set a more stringent limit on $\Delta\mu/\mu$.

The detected molecular lines are listed in Table 2 of L20. Carbon monoxide emission was observed in rotational transitions from $J = 2 \rightarrow 1$ up to $J = 13 \rightarrow 12$. From this dataset we selected CO lines obtained with the highest angular resolution and with redshifts measured with errors $\sigma_z \leq 0.0004$ (Table [\[T2\]](#T2)). The reported line widths are distributed around the mean $\langle {\rm FWHM} \rangle_{\rm CO} = 392$ km s$^{-1}$ with standard deviation $\sigma_{\rm FWHM} = 25$ km s$^{-1}$. The width of \[C ii\] is in good agreement with CO lines, i.e., they all are, most probably, co-spatially distributed.

The measured redshifts with their $1\sigma$ error bars are shown in Fig. [2](#Fg2), right panel. Averaging five CO redshifts from Table [\[T2\]](#T2) gives $\langle z \rangle_{\rm rot} = 6.00294(13)$. With $z_{\rm fs} = z_{\scriptscriptstyle \rm [CII]} = 6.0031(2)$ the updated result at $z = 6.003$ yields $\Delta\mu/\mu$ = $(2.3\pm3.4)\times10^{-5}$ ($1\sigma$).

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Transition | $z$ | FWHM | $\Delta_{\rm ch}$ | $\theta$ | Facilities |
|  |  | (km s$^{-1}$) | (km s$^{-1}$) | (arcsec) |  |
|  | 6.0031(2) | 393(21) | 18 | 0.72$\times$0.51 | ALMA$^1$ |
| CO(5-4) | 6.0030(4) | 409(44) | 60 | 1.67$\times$1.37 | NOEMA$^2$ |
| CO(6-5) | 6.0028(3) | 361(9) | 23.7 | 0.6$\times$0.4 | ALMA$^3$ |
| CO(6-5) | 6.0030(3) | 422(20) | 60 | 1.42$\times$1.19 | NOEMA$^2$ |
| CO(8-7) | 6.0028(1) | 390(15) | 36 | 0.79$\times$0.75 | ALMA$^2$ |
| CO(9-8) | 6.0031(2) | 376(18) | 32 | 0.77$\times$0.63 | ALMA$^2$ |

# Possible $z$-dependence of $\mu$ 

If we assume that the result of Hart & Chluba (2020), $m_{{\rm e},z} = (1.0190\pm0.0055)m_{\rm e,0}$, is real at the recombination epoch, then in combination with constraints on $\Delta\mu/\mu$ at lower redshifts, $z < 7$, this implies that there should be a redshift dependence of non-standard scalar field(s) coupled to ordinary matter. All available measurements of $\Delta\mu/\mu$ from the range $z \in [0,1100]$ are plotted by dots with error bars in Fig. [3](#Fg3), while the detailed information on individual data points is given in Appendix. Two inserts with expanded $Y$-scales are used to make the error bars visible in the indicated redshift intervals.

To approximate the $z$-dependence of $\mu$ we employ a simple power law $$\begin{equation}
\frac{\Delta\mu}{\mu} = k_\mu (1+z)^p\; ,
\label{Equ6}
\end{equation}$$ with $k_\mu$ and $p$ being the model parameters. A similar form was used in Hart & Chluba (2018, 2020).

The regression analysis yields $k_\mu = (1.6 \pm 0.3)\times10^{-8}$ and $p = 2.00 \pm 0.03$ ($1\sigma$) with the corresponding regression curve shown by red in Fig. [3](#Fg3). We note that the null result for the power index $p$ reported by Hart & Chluba (2020), $p = (0.7 \pm 3.1)\times 10^{-3}$, is due to the fact that their calculations were restricted by the epoch of recombination only, $\Delta z \simeq 200$ at $z = 1100$.

We also tried an exponential function depending on two parameters $k'_\mu$ and $p'$: $$\begin{equation}
\frac{\Delta\mu}{\mu} = k'_\mu \exp( p' z)\; .
\label{Equ6a}
\end{equation}$$ The corresponding curve for $k'_\mu = 1.7\times10^{-8}$ and $p' = 0.013$ is shown by the dashed grey curve in Fig. [3](#Fg3). It is clearly seen that the points available do not allow to decide between the power law and exponential functions. However, both of them lead to a positive coefficient $k_\mu$ ($k'_\mu$) at $z \rightarrow 0$ if the effective electron rest mass at the epoch of recombination differs from its terrestrial value.

The question arises how the obtained redshift dependence of $\Delta\mu/\mu$ with $k_\mu > 0$ can be verified?

It is obvious that the recombination point, which is crucial for the present analysis, should be confirmed in further studies of the cosmic microwave background anisotropies. We note that the fractional changes in $m_{\rm e}$ of $\sim$ 1-2% do not contradict the results of primordial nucleosynthesis ($z \sim 10^8$) which show that abundances of the light nuclei are not sensitive to the changes in $m_{\rm e}$ within $\pm10$% (e.g., Coc et al. 2007; Uzan 2011).

At $z \sim 17$, the central redshift of the observed H i 21-cm absorption, the expected value of $\Delta\mu/\mu$ is $5\times10^{-6}$ \[Eq.([\[Equ6\]](#Equ6))\] or $2\times10^{-8}$ \[Eq.([\[Equ6a\]](#Equ6a))\]. Measurements at such level of sensitivity can be provided solely by radio spectroscopy of molecular and atomic transitions. However, presently neither molecular nor atomic transitions have been detected above $z \sim 10$ albeit galaxies with redshifts $z > 10$ are expected to be observed with the Atacama Large Millimeter/submillimeter Array (de Blok et al. 2016) and the James Webb Space Telescope (Behroozi et al. 2020).

For the epoch of reionization ($6 < z < 10$) the expected value of $\Delta\mu/\mu$ is less than $10^{-6}$. To date, the best estimate of the fractional changes in $\mu$ at $z > 6$ is $|\Delta \mu/\mu| < 10^{-5}$, i.e., the measurement accuracy should be improved by an order of magnitude. According to Eq. ([\[Equ5\]](#Equ5)), this level can be achieved if the exposure time will be increased by $\sim 100$ times at the fixed values of the channel width $\Delta_{\rm ch} \simeq 50$ km s$^{-1}$ and the line width FWHM $\simeq 200$ km s$^{-1}$. With the existing observing facilities this seems to be problematic if one deals with \[C i\]/\[C ii\]/CO transitions.

Another way to reach an accuracy $\sim 10^{-6}$ is to use spectral lines with higher sensitivity coefficients, $Q_\mu$, to changes in $\mu$ \[see Eq.([\[Equ1A\]](#Equ1A)) in Appendix\]. For instance, the $1_1 - 2_2 E$ transition of the methanol isotopologue ${}^{12}$CD$_3{}^{16}$OH at a rest frequency of $\nu \approx 1.2$ GHz has $Q_\mu = -330$ (Jansen et al. 2011), the sensitivity coefficients of the $\Lambda$-doublet hyperfine components of the ${}^2\Pi_{1/2} J=9/2$ state of OH from the interval $\Delta\nu = 89-193$ MHz are ranging between $Q_\mu = 212$ and 460 (Kozlov 2009). The sensitivities of these transitions to variations in $\mu$ are more than two orders of magnitude larger than $Q_\mu = 1$ used in the current studies with \[C i\]/CO and \[C ii\]/CO pairs. These and other high sensitivity molecular transitions are planned to be observed with the Five-hundred-meter Aperture Spherical radio Telescope (Chen et al. 2019).

Observations of local objects ($z \sim 0$) have an important specificity that their angular sizes are larger than the aperture of a telescope. This makes possible the scanning of the local objects across their surfaces. Then spatial fluctuations of $\mu$ can be expected if some screening mechanism predicted in a number of theories is indeed at play. The currently available data show that the upper limit on the amplitude of such fluctuations is $k_\mu \;
\raise 0.3ex\hbox{$<$\kern-0.75em\raise-1.1ex\hbox{$\sim$}}\; 10^{-8}$. Thus, to detect the signal the spectral line positions should be measured with uncertainties of less or about 0.01 km s$^{-1}$. Such an accuracy can already be achieved at the existing observing facilities.

# Summary

Our main results are as follows:

- Using a combination of the \[C i\] and \[C ii\] fine structure lines together with CO(6-5), (7-6), and (9-8) rotational transitions observed towards the quasar J0439+1634 by Yang J. et al. (2019), we set a limit on $\Delta\mu/\mu$ $= (0.0 \pm 2.7)\times10^{-5}$ at $z = 6.519$.

- A combination of the \[C ii\] fine structure line with CO(5-4), (6-5), (8-7), and (9-8) rotational transitions from the spectrum of J2310+1855 (Li et al. 2020) yields $\Delta\mu/\mu$ $= (2.3 \pm 3.4)\times10^{-5}$ at $z = 6.003$.

- Two values of $\Delta\mu/\mu$ at $z = 6.519$ and $z = 6.003$, being combined with $\Delta\mu/\mu$ $= (-1.3 \pm 7.9)\times 10^{-5}$ at $z = 6.419$ towards the quasar J1148+5251 (Levshakov et al. 2017), give a mean value of $\langle \Delta\mu/\mu \rangle = (0.7 \pm 1.2)\times 10^{-5}$ at $\bar{z} = 6.3$ which is the most stringent up-to-date limit on the fractional changes in $\mu$ at the epoch of reionization.

- Exploiting the value of $m_{{\rm e},z} = (1.0190\pm0.0055)m_{\rm e,0}$ at $z = 1100$ from Hart & Chluba (2020) and all available data on $\Delta\mu/\mu$, we obtain a functional $z$-dependence of $\mu$ in the form $\Delta\mu/\mu$ $= k_\mu (1+z)^p$ with $k_\mu = (1.6 \pm 0.3)\times 10^{-8}$ and $p = 2.00 \pm 0.03$. Possible ways to verify this dependence by further observations are discussed.

# Acknowledgments

We would like to thank our referee Wim Ubachs for useful comments and suggestions. This work was supported by the Russian Science Foundation under grant No. 19-12-00157.

# Data Availability

Based on the published spectra obtained at the IRAM NOEMA Interferometer (project S18DO and W18EI) and at the ALMA Interferometer (project ADS/JAO.ALMA 2015.1.01265.S).

IRAM is supported by INSU/CNRS (France), MPG (Germany), and IGN (Spain). The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

ALMA is a partnership of ESO, NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile.

Spectral data used in this study are publicly available from the corresponding papers cited herein.

![](mn_20_3089_fig1)

![](mn_20_3089_fig2)

![](mn_20_3089_fig3)

(ref: ) Antoniou I., Perivolaropoulos L., 2017, PhRvD, 96, 1040002

(ref: ) Banerjee D., Burtsev V. E., Chumakov A. G., Cooke D., Crivelli P., Depero E., Dermenev A. V., et al., 2018, PhRvL, 120, 231802

(ref: ) Barkana R., Outmezguine N. J., Redigol D., Volansky T., 2018, Phs. Rev. D, 98, 103005

(ref: ) Battaglieri M., Belloni A., Chou A., Cushman P., Echenard B., Essig R., Estrada J. et al., 2017, arXiv:1707.04591 \[hep-ph\]

(ref: ) Beacham J., Burrage C., Curtin D., De Roeck A., Evans J., Feng J.L., Gatto C., et al., 2019, arXiv:1901.09966 \[hep-ex\]

(ref: ) Behroozi P., Conroy C., Wechsler R. H., Hearin A., Williams C. C., Moster B.P., Yung L. Y. A., et al., 2020, arXiv:2007.04988 \[astro-ph.CO\]

(ref: ) Bergé J., Brax P., Métris G., Pernot-Borràs M., Touboul P., Uzan J.-P., 2018, PhRvL, 120, 141101

(ref: ) Brax P., 2018, RPPh, 81, 016902

(ref: ) Brax P., Davis A.-C., 2016, PhRvD, 94, 104069

(ref: ) Bowman J. D., Rogers A. E. E., Monsalve R. A., Mozdzen T. J., Mahesh N., 2018, Nature, 555, 67

(ref: ) Chen X., Ellingsen S. P., Mei Y., 2019, RAA, 19, 018

(ref: ) Coc A., Nunes N. J., Olive K. A., Uzan J.-P., Vangioni E., 2007, PhRvD, 76, 023511

(ref: ) Cooksy A. L., Blake G. A., Saykally R. J., 1986, ApJL, 305, L89

(ref: ) Curran S. J., Tanna A., Koch F. E., Berengut J. C., Webb J. K., Stark A. A., Flambaum V. V., 2011, A&A, 533, A55

(ref: ) Daprá M., Henkel C., Levshakov S. A., Menten K. M., Muller S., Bethlem H. L., Ubachs W., 2017, MNRAS, 472, 4434

(ref: ) de Blok W. J. G., Walter F., Smith J.-D. T., Herrera-Camus R., Bolatto A. D., Requena-Torres M. A., Crocker A. F., et al., 2016, AJ, 152, 51

(ref: ) Endres C. P., Schlemmer S., Schilke P., Stutzki J., Müller H. S. P., 2016, J. Mol. Spectrosc., 327, 95

(ref: ) Famaey B., Khoury J., Penco R., Sharma A., 2020, JCAP, 06, 025

(ref: ) Fan X., Wang F., Yang J., Keeton C. R., Yue M., Zabludoff A., Bian F., et al., 2019, ApJ, 870, L11

(ref: ) Flambaum V. V., Kozlov M. G., 2007, PhRvL, 98, 240801

(ref: ) Fraser S., Hektor A., Hütsi G., Kannike K., Marzo C., Marzola L., Racioppi A., et al., 2018, Phys. Lett. B, 785, 159

(ref: ) Hamilton P., Jaffe M., Haslinger P., Simmons Q., Müller H., Khoury J., 2015, Science, 349, 849

(ref: ) Hannestad S., 1999, PhRvD, 60, 023515

(ref: ) Haris K., Kramida A., 2017, ApJS, 233, 16

(ref: ) Hart L., Chluba J., 2020, MNRAS, 493, 3255

(ref: ) Hart L., Chluba J., 2018, MNRAS, 474, 1850

(ref: ) Hollenbach D. J., Tielens A. G. G., 1999, Rev. Mod. Phys., 71, 173

(ref: ) Houston N., Li C., Li T., Yang Q., Zhang X., 2018, PhRvL, 121, 111301

(ref: ) Ichikawa K., Kanzaki T., Kawasaki M., 2006, PhRvD, 74, 023515

(ref: ) Iocco, F., Pato M., Bertone G., 2015, NPhys., 11, 245-248

(ref: ) Irastorza I.G., Redondo J., 2018, PrPNP, 102, 89

(ref: ) Jansen P., Xu L. H., Kleiner I., Ubachs W., Bethlem H. L., 2011, PhRvL, 106, 100801

(ref: ) Kanekar N., 2011, ApJ, 728, L12

(ref: ) Kanekar N., Ghosh T., Chengalur J. N., 2018, PhRvL, 120, 061302

(ref: ) Kanekar N., Ubachs W., Menten K. M., Bagdonaite J., Brunthaler A., Henkel C., Muller S., et al., 2015, MNRAS, 448, L104

(ref: ) Kanekar N., Langstone G. I., Stocke J. T., Carilli L. C., Menten K. L., 2012, ApJ, 746, L16

(ref: ) Kanekar N., Prochaska J. X., Ellison S. L., Chengalur J. N., 2010, ApJ, 712, L148

(ref: ) Kaplinghat M., Scherrer R. J., Turner M. S., 1999, PhRvD, 60, 023516

(ref: ) Kaufman M. J., Wolfire M. G., Hollenbach D. J., Luhman M. C., 1999, ApJ, 527, 795

(ref: ) Kozlov M. G., 2009, PhRvA, 80, 022118

(ref: ) Kozlov M. G., Levshakov S. A., 2013, Ann. Phys. 525, 452

(ref: ) Kozlov M. G., Porsev S. G., Levshakov S. A., Reimers D., Molaro P., 2008, PhRvA, 77, 032119

(ref: ) Kujat J., Scherrer R. J., 2000, PhRvD, 62, 023510

(ref: ) Landman D. A., Roussel-Dupré R., Tanigawa G., 1982, ApJ, 261, 732

(ref: ) Levshakov S. A., Ng K.-W., Henkel C., Mookerjea B., Agafonova I. I., Liu S.-Y., Wang W.-H., 2019, MNRAS, 487, 5175

(ref: ) Levshakov S. A., Ng K.-W., Henkel C., Mookerjea B., 2017, MNRAS, 471, 2143

(ref: ) Levshakov S. A., Reimers D., Henkel C., Winkel B., Mignano A., Centurión M., Molaro P., 2013, A&A, 559, A91

(ref: ) Levshakov S. A., Combes F., Boone F., Agafonova I. I., Reimers D., Kozlov M. G., 2012, A&A, 540, L9

(ref: ) Levshakov S. A., Molaro P., Reimers D., 2010, A&A, 516, A113

(ref: ) Levshakov S. A., Reimers D., Kozlov M. G., Porsev S. G., Molaro P., 2008, A&A, 479, 719

(ref: ) Li J., Wang R., Riechers D., Walter F., Decarli R., Venamans B. P., Neri R., et al., 2020, ApJ, 2020, 889, 162 \[L20\]

(ref: ) Li K., Arif M., Cory D. G., Haun R., Heacock B., Huber M. G., Nsofini J., et al., 2016, PhRvD, 93, 062001

(ref: ) McGaugh S. S., 2018, RNAAS, 2, 37

(ref: ) McMillan P. J., 2017, MNRAS, 465, 76

(ref: ) Okada Y., Güsten R., Requena-Torres M. A., Röllig M., Stutzki J., Graf U. U., Hughes A., 2019, A&A, 621, A62

(ref: ) Planck Collaboration et al., 2018, arXiv:1807.06209 \[astro-ph.CO\]

(ref: ) Planck Collaboration et al., 2015, A&A, 580, A22

(ref: ) Rider A. D., Moore D. C., Blakemore C. P., Louis M., Lu M., Gratta G., 2016, PhRvL, 117, 101101

(ref: ) Riess A. G., Casertano S., Yuan W., Macri L. M., Scolnic D., 2019, ApJ, 876, 85

(ref: ) Rivera J., Baker A. J., Gallardo P. A., Megan B., Harris A. I., Huffenberger K. M., Hughes J. P., et al., 2019, ApJ, 879, 95

(ref: ) Safarzadeh M., Scannapieco E., Babul A., 2018, ApJ, 859, L18

(ref: ) Sofue Y., Honma M., Omodaka T., 2009, PASJ, 61, 227

(ref: ) Thompson R., 2019a, MNRAS, 490, 2019

(ref: ) Thompson R., 2019b, MNRAS, 482, 5448

(ref: ) Thompson R., 2018, MNRAS, 477, 4104

(ref: ) Thompson R., 2017, MNRAS, 467, 4558

(ref: ) Ubachs W., 2018, Space Sci. Rev., 214, 3

(ref: ) Ubachs W., Salumbides E. J., Murphy M. T., Abgrall H., Roueff E., 2019, A&A, 622, A127

(ref: ) Ubachs W., Bagdonaite J., Salumbides E. J., Murphy M. T., Kaper L., 2016, Rev. Mod. Phys., 88, 021003

(ref: ) Wagner T. A., Schlamminger S., Gundlach J. H., Adelberger E. G., 2012, Class. Quantum Grav., 29, 184002

(ref: ) Wang R., Wagg J., Carilli C. L., Walter F., Lentati L., Fan X., Riechers D. A., Bertoldi F., et al., 2013, ApJ, 773, 44

(ref: ) Weiß A., Walter F., Downes D., Carrili C. L., Henkel C., Menten K. M., Cox P., 2012, ApJ, 753, 102

(ref: ) Wong K., Suyu S. H., Chen G. C.-F., Rusu C. E., Millon M., Sluse D., Bonvin V., et al., 2019, arXiv:1907:04869 \[astro-ph.CO\]

(ref: ) Yang C., Gavazzi R., Beelen A., Cox P., Omont A., Lehnert M. D., Gao Y., et al., 2019, A&A, 624, A138

(ref: ) Yang J., Venemans B., Wang F., Fan X., Novak M., Decarli R., Walter F., et al., 2019, ApJ, 880, 153 \[Y19\]

(ref: ) Yang W., Pan S., Vagnozzi S., Di Valentino E., Mota D. F., Capozziello S., 2019, JCAP, 11, 044

(ref: ) Yoo K. J., Scherrer R. J., 2003, PhRvD, 67, 043517

# Description of the data points

The data points shown in Fig. [3](#Fg3) were compiled from the following sources.

**Milky Way disk $(z=0)$**. In the Milky Way, high-resolution spectral observations of dark clouds were performed in the inversion line of NH$_3$(1,1) and pure rotational lines of other molecules (the so-called ammonia method) at the Medicina 32-m and the Effelsberg 100-m radio telescopes to measure the radial velocity offset, $\Delta V = V_{\rm rot} - V_{\rm inv}$, between the rotational and inversion transitions to calculate $$\begin{equation}
\frac{\Delta\mu}{\mu} = \frac{V_{\rm rot} - V_{\rm inv}}{c(Q_{\rm inv} - Q_{\rm rot})} 
\approx 0.3\frac{\Delta V}{c},
\label{Equ1A}
\end{equation}$$ where $c$ is the speed of light, and $Q_{\rm inv}, Q_{\rm rot}$ are the corresponding sensitivity coefficients to changes in $\mu$ (Flambaum & Kozlov 2007).

In Effelsberg observations, 19 independent offsets of $\Delta V$ gave a weighted mean $\langle \Delta V \rangle = 0.003 \pm 0.006$ km s$^{-1}$ ($1\sigma$) which constrained the $\mu$-variation at the level of $\Delta\mu/\mu$ = $(0.3 \pm 0.6)\times10^{-8}$. The Medicina observations of two dark clouds L1521 and L1498 provided respectively $\Delta\mu/\mu$ = $(0.1 \pm 2.2)\times10^{-8}$ and $\Delta\mu/\mu$ = $(-0.1 \pm 2.3)\times10^{-8}$ (Levshakov et al. 2013).

Later on, the dark cloud core L1498 was observed with the IRAM 30-m telescope in methanol CH$_3$OH lines (Daprà et al. 2017), which resulted in $\Delta \tilde{\mu}/\tilde{\mu} = (-3.3 \pm 1.9)\times10^{-8}$ or $\Delta\mu/\mu$ = $(3.3 \pm 1.9)\times10^{-8}$. Thus, a combined Medicina and IRAM limit on $\Delta\mu/\mu$ towards L1498 is $\Delta\mu/\mu$ = $(3.2 \pm 1.5)\times10^{-8}$. Now, if we add this value to both the Medicina L1521 and Effelsberg 19 clouds measurements, then the mean constraint on $\Delta\mu/\mu$ in the MW disk reads $\langle \Delta\mu/\mu \rangle = (1.2 \pm 0.9)\times10^{-8}$ ($1\sigma$).

**Magellanic Clouds $(z=0)$**. Analyzing data of 9 molecular clouds in the Large and Small Magellanic Clouds, we obtained for a highest resolution spectrum of a target PDR3-NE (LMC) an offset $\Delta V  = -0.05 \pm 0.02$ km s$^{-1}$ between the CO(7-6) and \[C i\] lines (Levshakov et al., 2019). Being interpreted in terms of $\alpha^2/\mu$ variations, this gives $\Delta F/F  = (-1.7 \pm 0.7)\times10^{-7}$, or $\Delta \mu/\mu = (1.7 \pm 0.7)\times10^{-7}$ ($1\sigma$) if we assume that $|\Delta \alpha/\alpha | \ll |\Delta \mu/\mu|$.

**Triangulum galaxy M33 $(z \approx 0)$**. 46 emitters in the CO(2-1) and \[C ii\] lines towards M33 show an offset $\langle \Delta V \rangle = -0.01 \pm 0.14$ km s$^{-1}$ (Levshakov et al. 2017), which corresponds to $\langle \Delta F/F \rangle = (-0.3 \pm 4.7)\times10^{-7}$, or $\langle \Delta\mu/\mu \rangle = (0.3 \pm 4.7)\times10^{-7}$ ($1\sigma$).

**Quasar PKS 1413+135 $(z=0.25)$**. The conjugate satellite OH 18 cm lines at redshift $z=0.247$ observed in emission (1720 MHz line) and absorption (1612 MHz) towards the BL Lacertae-type quasar PKS 1413+135 yield $\Delta\tilde{\mu}/\tilde{\mu}$ = $(-1.0 \pm 1.3)\times10^{-6}$ (Kanekar et al. 2018), or $\Delta\mu/\mu$ = $(1.0 \pm 1.3)\times10^{-6}$ ($1\sigma$).

**Gravitational lens system B0218+357 $(z=0.69)$**. The ammonia method was applied to the inversion (NH$_3$) and rotational (CS, H$_2$CO) absorption lines detected in a lensed galaxy at $z = 0.69$ towards B0218+357 (Kanekar 2011). The measured fractional changes in $\mu$ are limited at the level of $\Delta\mu/\mu$ = $(3.5 \pm 1.2)\times10^{-7}$ ($1\sigma$).

**Quasar J0134–0931 $(z=0.765)$**. A comparison between H i 21-cm and OH 18-cm absorption lines sets a limit on $\Delta X/X = (-5.2 \pm 4.3)\times10^{-6}$, where $X = g_{\rm p}(\tilde{\mu}\alpha^2)^{1.57}$ and $g_{\rm p}$ is the proton g-factor (Kanekar et al. 2012). Assuming that fractional changes in $g_{\rm p}$ and $\alpha$ are smaller than those in $\mu$, we obtain $\Delta\mu/\mu$ = $(3.3 \pm 2.7)\times10^{-6}$ where error includes both the statistical and systematic uncertainties.

**Gravitational lens system PKS1830–211 $(z=0.89)$**. In Kanekar et al. (2015), the $z = 0.89$ gravitational lens towards PKS1830–211 was observed in methanol CH$_3$OH absorption lines yielding $\Delta\mu/\mu$ = $(0.29 \pm 0.57)\times10^{-7}$ ($1\sigma$).

**Quasars Q 2337–011 $(z=1.36)$ and Q 0458–020 $(z=1.56)$**. Two absorbers at $z=1.36$ and $z=1.56$ towards respectively Q 2337–011 and Q 0458–020 were studied in the H i 21-cm and C i $\lambda\lambda$1560, 1657 Å lines to set constraints on the product $X = g_{\rm p}\tilde{\mu}\alpha^2$, where $g_{\rm p}$ is the proton g-factor (Kanekar et al. 2010). The mean value of $\Delta X/X = (6.8 \pm 1.0_{\rm stat} \pm 6.7_{\rm sys})\times10^{-6}$ transforms to $\Delta\mu/\mu$ = $(-6.8 \pm 6.8)\times 10^{-6}$ at $\bar{z} = 1.46$ if we assume that fractional changes in $g_{\rm p}$ and $\alpha$ are smaller than those in $\mu$.

**H$_2$ absorption-line systems $(\bar{z} = 2.76)$**. In the interval from $z = 2.05$ to $z = 4.22$, the $\mu$-variation can be constrained from a sample of nine H$_2$ systems selected from Ubachs et al. (2016, 2019). We list these measurements of $\Delta\mu/\mu$ along with their weighted mean value in Table [\[Ta1\]](#Ta1). At the mean redshift $\bar{z} = 2.763$, one finds $\langle \Delta\mu/\mu \rangle = (-2.5 \pm 5.3)\times10^{-6}$.

l c r@.l r@.l c & & & & Refs.\
& & &\
J2123–0050 & 2.05 & $-7$&6 & 3&5 & 1\
HE0027–1836 & 2.40 & 7&6 & 10&2 & 1\
Q2348–011 & 2.43 & 6&8 & 27&8 & 1\
Q0405–443 & 2.59 & $-7$&5 & 5&3 & 1\
B0642–5038 & 2.66 & $-9$&44 & 6&09 & 2\
J1237+064 & 2.69 & 4&37 & 6&30 & 2\
Q0528–250 & 2.81 & 0&5 & 2&7 & 1\
Q0347–383 & 3.02 & $-5$&1 & 4&5 & 1\
J1443+2724 & 4.22 & 9&5 & 7&5 & 1\
& $-2$&5 & 5&3\

**QSO host galaxy RXJ0911.4+0551 $(z=2.79)$**. One of the most attractive target for high-precision $\Delta F/F$ measurements is the quasar host galaxy RXJ0911.4+0551 at $z = 2.79$ which emits very strong and narrow CO(7-6) and \[C i\] lines (Weiß et al. 2012). The FSM applied to this system yields $\Delta F/F$ = $(6.9 \pm 3.7)\times10^{-6}$, or neglecting contribution from $\Delta\alpha/\alpha$, we have $\Delta\mu/\mu$ = $-(6.9 \pm 3.7)\times10^{-6}$ ($1\sigma$).

**Lensed galaxy HLSJ091828.6+514223 $(z=5.24)$**. An upper limit on $\Delta F/F$ was deduced from observation of CO(7-6) and \[C i\] lines towards the lensed galaxy HLSJ091828.6+514223 at $z = 5.243$ (Levshakov et al. 2012), which corresponds to $\Delta\mu/\mu$ = $(-0.27 \pm 1.53)\times10^{-5}$ ($1\sigma$).

**High-redshift \[C i\]/\[C ii\]/CO systems $(\bar{z} = 6.3)$**. Two estimates of $\Delta\mu/\mu$ = $(0.0\pm2.7)\times10^{-5}$ at $z = 6.519$ and $\Delta\mu/\mu$ = $(2.3\pm3.4)\times10^{-5}$ at $z = 6.003$ from the previous section can be combined with another high redshift value of $\Delta\mu/\mu$ = $(-1.3\pm7.9)\times10^{-5}$ at $z = 6.419$ towards the quasar J1148+5251 (Levshakov et al. 2017). Being averaged, these three estimates provide a weighted mean value of $\langle \Delta\mu/\mu \rangle = (0.7\pm1.2)\times10^{-5}$ at $\bar{z} = 6.3$ in the epoch of reionization.

**The CMB limit on electron mass changes $(z \simeq 1100)$**. In recent analysis of the cosmic microwave background radiation by Hart & Chluba (2020), it was shown that the electron rest mass, $m_{\rm e,0}$, might be slightly increased during the cosmological recombination era at $z \simeq 1100$: $\Delta m_{\rm e}/m_{\rm e,0} = (m_{{\rm e},z} - m_{\rm e,0})/m_{\rm e,0} =
0.0190 \pm 0.0055$ ($1\sigma$).

An important point to note for the CMB analysis is that while only dimensionless numbers are invariant to the adopted system of units, variation of the dimensional parameter $m_{\rm e}$ for the physics of recombination is equivalent after rescaling to a variation in the dimensionless parameter $\mu$, and “*the effect of a variation in $m_{\rm p}$ on recombination is subdominant compared to a variation in $m_{\rm e}$*” (Planck Collaboration et al. 2015). The binding energy of quarks can be also altered but its impact on the atomic and molecular frequencies and on the CMB spectrum is much weaker than the varying electron mass (Kujat & Scherrer 2000; Yoo & Scherrer 2003; Ichikawa et al. 2006).

[^1]: E-mail: lev@astro.ioffe.ru

[^2]: Here we adopt a flat $\Lambda$CDM cosmology with $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_\Lambda = 0.7$, $\Omega_{\rm m} = 0.3$.

</paper>

Write the methods card for this paper.