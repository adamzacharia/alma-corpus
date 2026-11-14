# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023PASJ...75..925F\sonnetcc\reply.txt

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
 "bibcode": "2023PASJ...75..925F",
 "title": "The correlation between the 500 pc scale molecular gas masses and AGN powers for massive elliptical galaxies",
 "year": 2023,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Fujita, Yutaka",
 "n_authors": 6,
 "arxiv_id": "2303.16927",
 "doi": "10.1093/pasj/psad050",
 "alma_projects_linked_by_archive": [
  "2011.0.00735.S",
  "2012.1.00837.S",
  "2015.1.00598.S",
  "2015.1.00623.S",
  "2015.1.00627.S",
  "2015.1.00644.S",
  "2015.1.01198.S",
  "2016.1.01214.S"
 ]
}
```

Paper text:
<paper>
# The correlation between the 500 pc scale molecular gas masses and AGN powers for massive elliptical galaxies

## Abstract

Massive molecular clouds have been discovered in massive elliptical galaxies at the center of galaxy clusters. Some of this cold gas is expected to flow in the central supermassive black holes and activate galactic nucleus (AGN) feedback. In this study, we analyze archival ALMA data of 9 massive elliptical galaxies, focusing on CO line emissions, to explore the circumnuclear gas. We show that the mass of the molecular gas within a fixed radius (500 pc) from the AGNs ($M_{\rm mol}\sim
10^7$–$10^8\rm\: M_\odot$) is correlated with the jet power estimated from X-ray cavities ($P_{\rm cav}\sim 10^{42}$–$10^{45}\rm\: erg\:
s^{-1}$). The mass accretion rate of the circumnuclear gas $\dot{M}$ also has a correlation with $P_{\rm
cav}$. On the other hand, the continuum luminosities at $\sim 1.4$ GHz and $\sim 100$–300 GHz have no correlation with $M_{\rm mol}$. These results indicate that the circumnuclear gas is sustaining the long-term AGN activities ($\sim 10^7$ yr) rather than the current ones. The circumnuclear gas mass is a better indicator of the jet power than the continuum luminosity, which probably changes on a shorter time scale. We also study the origin of the continuum emission from the AGNs at $\sim
100$–300 GHz and find that it is mostly synchrotron radiation. For low-luminosity AGNs, however, dust emission appears to contaminate the continuum.

Department of Physics, Graduate School of Science Tokyo Metropolitan University 1-1 Minami-Osawa, Hachioji-shi, Tokyo 192-0397

National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588

National Institute of Technology, Kure College, 2-2-11, Agaminami, Kure, Hiroshima, 737-8506, Japan

The Graduate University for Advanced Studies, SOKENDAI, Osawa 2-21-1, Mitaka, Tokyo 181-8588

# Introduction

Massive elliptical galaxies are often located at the center of galaxy clusters. They host supermassive black holes, which are observed as active galactic nuclei (AGNs). While the cooling time of the hot gas in the galaxies is much smaller ($\lesssim 10^8$ yr) than the age of the Universe (cite: 1994ARA&A..32..277F), the AGNs are expected to serve as heating sources and prevent the development of massive cooling flows (AGN feedback; (cite: 2000A&A...356..788C; 2007ARA&A..45..117M; 2012ARA&A..50..455F)). Since the galaxies are immersed in the hot gas, it may be natural to assume that the hot gas feeds into the black holes in the form of the Bondi accretion (cite: 1952MNRAS.112..195B) and stimulates the AGNs. In fact, (cite: 2006MNRAS.372...21A) found a tight correlation between the Bondi accretion rates and the power emerging from the AGNs in relativistic jets. However, later studies have revealed that the correlation is weak (cite: 2013MNRAS.432..530R).

In addition to the hot gas, cold molecular gas has been discovered in the massive elliptical galaxies (e.g. (cite: 2001MNRAS.328..762E; 2003A&A...412..657S; 2014ApJ...792...94D; 2014ApJ...785...44M)). It has been indicated that nebular emission, enhanced star formation, and AGN activities are recognized when the entropy of the hot gas decreases to $\lesssim 30\:\rm keV\: cm^2$, or almost equivalently when the radiative cooling time is $\lesssim 1$ Gyr (e.g. (cite: 2008ApJ...683L.107C; 2008ApJ...687..899R; 2009MNRAS.398.1698S; 2017MNRAS.464.4360M)). This suggests that radiative cooling turns the hot gas into cold gas, and the cold gas drives star formation and AGN activity. Recently, (cite: 2022ApJ...924...24F) discussed gas circulation in the massive elliptical galaxies using a semi-analytical model. They indicated that while some of the cold gas is consumed in star formation, the rest flows into the galactic center. Moreover, if a circumnuclear disk is formed around the central black hole, disk instabilities regulate the gas accretion toward the black hole; the overall AGN activity depends on the mass of the disk. We note that the typical size of the circumnuclear disk is $\sim 100$–500 pc for the massive elliptical galaxies at the cluster centers (cite: 2019ApJ...883..193N; 2022ApJ...924...24F).

In this paper, we analyze Atacama Large Millimeter Array (ALMA) archival data of massive elliptical galaxies in galaxy clusters and seek correlations among the properties of circumnuclear molecular gas and the AGN activity, which may support the idea that the gas fuels the AGNs. We note that (cite: 2019MNRAS.490.3025R) have compared the mass of the circumnuclear molecular gas with the AGN jet power and found a correlation (their Figure 7). However, they measured the mass in a single ALMA synthesized beam centered on the AGNs. Since the physical size of a given beam is larger for more distant objects, the mass inside it tends to be larger, while distant AGNs are observationally biased toward brighter and powerful ones. This could create an artificial correlation. To lessen such biases, we focus on the mass within a fixed physical radius. We also study the mass accretion rates and the radio continuum luminosities of the AGNs to further investigate the fueling process. We assume $H_0=70\rm\: km\: s^{-1}\: Mpc^{-1}$, $\Omega_m=0.3$, and $\Omega_\Lambda=0.7$ in this study. All errors are $1\:\sigma$ unless otherwise noted.

# Data Reduction

We analyzed archival ALMA observations of CO line emissions from the cold gas in massive elliptical galaxies at the center of galaxy clusters, and we investigated relations between the cold gas and the AGN activity. Targets were selected from those studied in (cite: 2019A&A...631A..22O) and (cite: 2019MNRAS.490.3025R). From the sample, we chose the ones for which AGN jet powers ($P_{\rm cav}$) have been estimated through observations of X-ray cavities. Moreover, we chose those for which the inner 500 pc (1 kpc in diameter) is resolved with ALMA. The selected sample includes M87 and RXJ 0821$+$0752. However, the molecular gas detected in M87 is located in the outer region of the galaxy and has no connection to the AGN (cite: 2018MNRAS.475.3004S), and the data of RXJ 0821+0752 are poorly calibrated because of an issue of water vapor radiometer (cite: 2017ApJ...848..101V). Thus, we did not include them in our sample. The list of the 9 remaining galaxies are shown in table [\[tab:obs\]](#tab:obs). We call the central galaxies by the names of their host clusters. The galaxy redshifts $z$ are those determined by optical observations.

The galaxies were observed with ALMA at frequencies corresponding to the CO(J=1-0), CO(J=2-1), or CO(J=3-2) rotational transition lines as well as at additional spectral windows that were used to image the mm/submm ($\sim
100$–300 GHz) continuum emission. The observations were single pointing ones centered on the AGNs, and they were calibrated using the appropriate version of Common Astronomy Software Application (CASA) software (cite: 2007ASPC..376..127M) and ALMA Pipeline used for the quality assurance. Data sets taken in the early ALMA Cycles were calibrated by the EA ALMA Regional Center (EA-ARC) through the request via the ALMA Helpdesk because of unavailability of the recommended CASA version.

The line and underlying continuum emissions were reconstructed using the CASA `tclean` task down to $3\:\sigma$ level. To study the line emissions, we subtracted the continuum using line-free channels with the CASA task `uvcontsub` (fitorder=1). Following previous studies (cite: 2019A&A...631A..22O; 2019MNRAS.490.3025R), we adopted Briggs weighting with a robust parameter of 2 (natural weighting). Each receiver was tuned to cover one of the abovementioned lines. The targets were observed with four spectral windows except for 2A0335+096 and PKS 0745-191 (two windows). Each spectral window has a bandwidth of 1.875 or 2.0 GHz. The synthesized beam size, and rms in each final data-cube are shown in table [\[tab:obs\]](#tab:obs).

References of redshifts: ($a$) (cite: 2008AJ....135.2424O), ($b$) (cite: 1992CORV..C...0000F), ($c$) (cite: 2019A&A...631A..22O), ($d$) (cite: 2017ApJS..233...25A), ($e$) (cite: 2019ApJ...872..134Z), and ($f$) (cite: 2019MNRAS.485..229R).\
A noise level for a channel map with a velocity width of $v$ binning.

# Results

Using the CASA task `immoments`, images of the integrated intensity, intensity-weighted mean radial velocity (velocity center hereafter), and intensity-weighted mean velocity dispersion (full width at half-maximum or FWHM) were created for the vicinities of the AGNs in the 9 galaxies covering each CO line (figure [1](#fig:image)). We extracted spectra from the central 500 pc region centered on the AGNs. We confirmed that the maximum recoverable scales are much larger than 500 pc for all the targets and the missed flux from the 500 pc region should be ignorable. Each spectrum was fitted with a model consisting of one or two Gaussian components (figure [2](#fig:spec)). The significance levels of those line components are $>5\:\sigma$. The best-fitting line center velocity $v$ relative to the galaxy rest frame, FWHM, and integrated intensity for each gaussian component $S_{\rm CO}\Delta v$ are presented in table [\[tab:result\]](#tab:result). We ignored line-like features if the line center velocity is $|v|\gtrsim 500\rm\: km\: s^{-1}$ because the corresponding gases are unlikely to be bound to the nuclei although they may still reside in the disks of central galaxies. They may be gas blobs that are falling toward or being ejected from the galactic centers. Hydra A has a prominent cold molecular gas disk seen in CO and substantial absorption due to the disk is seen at the line frequency at the position of the AGN ((cite: 2019MNRAS.485..229R); see figure [1](#fig:image)). Thus, we excluded the innermost 160 pc, and we extracted and examined the spectra in the eastern and western regions of the AGN separately (figure [2](#fig:spec)). The parenthesized FWHM values shown in table [\[tab:result\]](#tab:result) are the flux averages of the two gaussian components except for Hydra A, for which it is the flux average of the east and west values.

![image](f1_N5044.png) ![image](f1_Cent.png) ![image](f1_A262.png) ![image](f1_A3581.png)

![image](f1_A2052.png) ![image](f1_2A0335.png) ![image](f1_HydraA.png) ![image](f1_A1795.png)

![](f1_PKS0745.png)

![](f2_N5044.pdf)

![](f2_Centaurus.pdf)

![](f2_A262.pdf)

\

![](f2_A3581.pdf)

![](f2_A2052.pdf)

![](f2_2A0335.pdf)

\

![](f2_HydraA.pdf)

![](f2_A1795.pdf)

![](f2_PKS0745.pdf)

The velocity of the line component relative to the systemic velocity of the galaxy.\
Flux-averaged ones are parenthesized.\
The spectral index of the continuum emission around $\nu_{\rm con}$, which cannot be constrained for 2A0335+096 and PKS 0745-191 (see text).

## Molecular gas mass

From the CO intensities $S_{\rm CO}\Delta v$ presented in table [\[tab:result\]](#tab:result), we derive the masses of molecular gas within $500$ pc from the AGNs using the following relation from (cite: 2013ARA&A..51..207B):

$$\begin{equation}
 M_{\rm mol} = \frac{1.05\times 10^4}{F_{\rm ul}}\left(\frac{X_{\rm CO}}{2\times 10^{20}
\frac{\rm cm^{-2}}{\rm K\: km\: s^{-1}}}\right)
\left(\frac{1}{1+z}\right)
\left(\frac{S_{\rm CO}\Delta v}{\rm Jy\: km\: s^{-1}}\right)
\left(\frac{D_{\rm L}}{\rm Mpc}\right)^2\: M_\odot\:,
\end{equation}$$

where $X_{\rm CO}$ is the CO-to-H$_2$ conversion factor, and $D_{\rm L}$ is the luminosity distance. The factor $F_{\rm ul}$ represents the assumption on the CO excitation, which is necessary to estimate CO(J=1-0) flux from higher-J measurements. Specifically, $F_{21}$ gives a CO(J=2-1)/CO(J=1-0) line ratio in flux density scale, 3.2, and $F_{32}$ is a CO(J=3-2)/CO(J=1-0) ratio of 7.2 (cite: 2019MNRAS.485..229R; 2019MNRAS.490.3025R). The dispersion of the values among the galaxies is about $\sim 40$ % (cite: 1992A&A...264..433B; 2003A&A...412..657S). The conversion factor $X_{\rm CO}$ is not well-understood for elliptical galaxies. Thus, we adopt a standard value of $X_{\rm CO}=2\times 10^{20}\rm\: cm^{-2}(K\:
km\: s^{-1})^{-1}$ measured in the Milky Way, following previous studies ((cite: 2019A&A...631A..22O; 2019MNRAS.490.3025R) and see their discussion). The results are shown in table [\[tab:Mmol\]](#tab:Mmol). When there are two gaussian components in the spectrum, the mass is their summation.

Calculated from $\nu_{\rm con}$ and $F_{\rm con}$ shown in table [\[tab:result\]](#tab:result) using equation ([4](#fig:dMdt-Pcav)).\

Jet power from (cite: 2006ApJ...652..216R) and (cite: 2018ApJ...853..177P).\
 GHz flux from (cite: 1998AJ....115.1693C) except for Centaurus (cite: 1981A&AS...45..367K)\
Black hole mass from (cite: 2006ApJ...652..216R) except for NGC 5044 (cite: 2009ApJ...705..624D).\

## Circumnuclear gas and jet power

Figure [3](#fig:M-Pcav) shows the relation between the molecular gas mass at $r<500$ pc ($M_{\rm mol}$) and the jet power required to inflate X-ray cavities ($P_{\rm cav}$). The data of $P_{\rm cav}$ have been taken from the literature (cite: 2006ApJ...652..216R; 2018ApJ...853..177P). A correlation can be seen between $M_{\rm mol}$ and $P_{\rm cav}$, and the Pearson correlation coefficient on the logarithmic scales is 0.754 with $p$-value 0.019. The correlation can be described by a power-law model of the form:

$$\begin{equation}
\label{eq:A1}
 \log\left(\frac{P_{\rm cav}}{10^{42}\rm erg\: s^{-1}}\right) = A_1\log\left(\frac{M_{\rm mol}}{M_\odot}\right) + B_1\:.
\end{equation}$$

Using the bivariate correlated errors and intrinsic scatter BCES $(Y|X)$ estimator (cite: 1996ApJ...470..706A), which accounts for errors in both axes and the presence of possible intrinsic scatter, we obtain $A_1 = 1.3\pm 0.4$ and $B_1 = -8.6\pm 3.0$. In other words, the correlation indicates that the jet power is proportional to the average density of the circumnuclear molecular gas because we considered the mass within the fixed radius and $A_1\sim 1$. Abell 262 appears to be an outlier of this correlation because it is outside the $3\:\sigma$ confidence range (figure [3](#fig:M-Pcav)). If we exclude Abell 262 from the sample, the correlation coefficient increases to 0.906 with $p$-value 0.0020. Abell 262 has a lower AGN activity despite retaining a large amount of gas. Possible reasons will be discussed in section [4.1](#sec:circ).

![](f3.pdf)

The gas accretion rate $\dot{M}$ may be more directly related to the AGN activity than $M_{\rm mol}$. The accretion is likely to be induced by the angular momentum transfer by turbulence (cite: 2010MNRAS.408..961P; 2017MNRAS.466..677G). In this case, the accretion process can be regarded as a diffusion process of gas clumps, and the diffusion coefficient is $\nu \sim \ell_{\rm t} v_{\rm t}$, where $\ell_{\rm t}$ and $v_{\rm t}$ is the eddy scale and the velocity of the turbulence, respectively (e.g. (cite: 1995ApJ...440..674X)) Thus, the diffusion or the accretion time scale of the gas on the scale of interest ($r_{\rm g}$) is $t_{\rm acc}\sim r_{\rm g}^2/\nu$, and the accretion rate is $\dot{M}\sim M_{\rm mol}/t_{\rm acc}$. We note that this estimation can even be applied to the standard disk (cite: 1973A&A....24..337S). Since the kinetic viscosity coefficient can be regarded as the diffusion coefficient, the accretion time of a disk on a scale of $r_{\rm g}$ is also $t_{\rm acc}\sim r_{\rm g}^2/\nu$ (section 6 of (cite: 1981ARA&A..19..137P)). Thus, we adopt the relation of $\dot{M}=
M_{\rm mol}/t_{\rm acc}$ regardless of whether molecular gas has a disk-like structure or not. We assume that $v_t={\rm FWHM}/(2\sqrt{2\ln
2})\approx {\rm FWHM}/2.35$ and $\ell_{\rm t}=\alpha r_{\rm g}$ (cite: 1983bhwd.book.....S), where $r_{\rm g}=500$ pc and $\alpha =
0.15$. For the FWHM, we use the flux averaged values when there are two gaussian components (parenthesized ones in table [\[tab:Mmol\]](#tab:Mmol)). We note that the derived $v_t$ may include a rotational component on a small scale that cannot be spatially resolved (see (cite: 2019ApJ...883..193N)) and it should be regarded as the upper limit. However, the effect of rotation velocity contamination may not be significant. We have investigated the effect within the observing beam, using a cube model code 3D-Barolo [^1] for Abell 262, a galaxy with a spatially resolved CO velocity field. The model fit shows that $v_t\sim 100\rm\: km\: s^{-1}$, which is close to FWHM/2.35$\sim 90\rm\:
km\: s^{-1}$ (table [\[tab:result\]](#tab:result)). We also indicate that not all the in-flowing gas ($\dot{M}$) is eventually swallowed by the black hole because some of it is consumed in star formation (cite: 2022ApJ...924...24F). The obtained $t_{\rm acc}$ and $\dot{M}$ are shown in table [\[tab:Mmol\]](#tab:Mmol).

Figure [4](#fig:dMdt-Pcav) shows the relation between $\dot{M}$ and $P_{\rm cav}$, which is similar to that between $M_{\rm mol}$ and $P_{\rm cav}$ (figure [3](#fig:M-Pcav)). The correlation coefficient is 0.733 with $p$-value 0.025, and it is 0.871 with $p$-value 0.0049 if we exclude Abell 262 because it is almost at the end of the $3\:\sigma$ confidence range. The correlation among the 9 objects can be represented by a power-law model of the form:

$$\begin{equation}
 \log\left(\frac{P_{\rm cav}}{10^{42}\rm erg\: s^{-1}}\right) = A_2\log\left(\frac{\dot{M}}{M_\odot\:\rm yr^{-1}}\right) + B_2\:.
\end{equation}$$

The BCES $(Y|X)$ estimator gives $A_2=1.5\pm 0.6$ and $B_2=1.0\pm 0.3$. The similarity between figures [3](#fig:M-Pcav) and [4](#fig:dMdt-Pcav) reflects the fact that while FWHM varies only a factor of few, $M_{\rm
mol}$ ranges nearly two orders of magnitude. This suggests that the mass of circumnuclear molecular gas is the main factor that determines the jet activity. Thus, the $\dot{M}$–$P_{\rm cav}$ relation seems to be robust even if we consider potential uncertainties such as the gas morphology (disk-like or not) and the contamination of a rotational velocity component.

![](f4.pdf)

## Circumnuclear gas and continuum emission

Since radio continuum emission is observed as a point source at the position of the AGNs, it should come from the vicinity of the AGNs ($\lesssim 500$ pc) and reflect their recent activity. We derive the continuum flux at line-free channels.

We convert fluxes at observed frequencies to those at the rest-frame CO(J=1-0) line frequency ($\nu_{10}=115.3$ GHz) assuming that the continuum emission is represented by a power-law $S_\nu \propto
(\nu/\nu_{10})^{\gamma}$, where $\nu$ is the frequency. We adopt a typical spectral index of $\gamma=-0.75$. For an object at the redshift $z$ and observed at the frequency $\nu_{\rm con}$, the radio continuum luminosity at the frequency $\nu_{10}$ is estimated to be

$$\begin{equation}
 L_{\rm con} = \frac{4\pi D_{\rm L}^2 \nu_{\rm con} F_{\rm con}}{[(1+z)\eta]^{1+\gamma}}\:,
\end{equation}$$

where $F_{\rm con}$ is the observed flux (mJy) and $\eta$ is the line frequency ratios ($\eta=1$ for CO(J=1-0), $\eta\approx 2$ for CO(J=2-1)[^2], and $\eta\approx 3$ for CO(J=3-2)), which is required for the flux conversion among different line frequencies. The derived luminosities $L_{\rm con}$ are presented in table [\[tab:Mmol\]](#tab:Mmol) and they are compared with $M_{\rm mol}$ in figure [5](#fig:M-Lcon). The correlation coefficient is 0.386 and the $p$-value is 0.30, which is much larger than the conventional threshold of 0.05. Thus, it is unlikely that that $L_{\rm con}$ is correlated with $M_{\rm mol}$. Again, Abell 262 appears to be an outlier because the radio luminosity is extremely small for its large $M_{\rm mol}$. If we exclude Abell 262 from the sample, the coefficient is 0.740 with $p$-value 0.036, which shows a sign of correlation.

![](f5.pdf)

Traditionally, radio emissions at lower frequencies have been used as an indicator of AGN activities (cite: 2004ApJ...607..800B; 2018ApJ...853..177P). Figure [6](#fig:M-L14) compares the radio luminosity estimated from 1.4 GHz observations (NRAO/VLA Sky Survey[^3]; (cite: 1998AJ....115.1693C)) with the mass of the circumnuclear molecular gas ($M_{\rm mol}$). The former is derived by

$$\begin{equation}
 L_{\rm 1.4} = \frac{4\pi D_{\rm L}^2 \nu_{\rm 1.4} F_{\rm 1.4}}
{(1+z)^{1+\gamma}}\:,
\end{equation}$$

where $\nu_{1.4}$ is $1.4$ GHz, $F_{\rm 1.4}$ is the observed flux at 1.4 GHz, and $\gamma=-0.75$. Since our targets are at lower redshifts ($z\lesssim 0.1$), the correction of $(1+z)^{1+\gamma}$ is insensitive to $\gamma$. The correlation coefficient is 0.556 with $p$-value 0.12. Thus, $L_{\rm 1.4}$ is unlikely to be correlated with $M_{\rm mol}$. However, if Abell 262 is ignored, the correlation coefficient is 0.778 with $p$-value 0.023, which may indicate the existence of correlation.

![](f6.pdf)

# Discussion

## Circumnuclear gas and AGN activity

We have shown that the mass of circumnuclear molecular gas ($M_{\rm
mol}$) within a fixed radius (500 pc) has a correlation with the jet power estimated from X-ray cavities ($P_{\rm cav}$; figure [3](#fig:M-Pcav)). This suggests that the circumnuclear molecular gas serves as the fuel for AGN feedback (cite: 2022ApJ...924...24F). Assuming that the gas accretion is caused by angular momentum transport by turbulence, the accretion rate ($\dot{M}$) is also correlated with $P_{\rm cav}$ (figure [4](#fig:dMdt-Pcav)), although the $\dot{M}$–$P_{\rm cav}$ relation is virtually the $M_{\rm mol}$–$P_{\rm cav}$ relation. We conclude that the jet power depends on the average density of the circumnuclear molecular gas because we considered the mass within the fixed radius. Since $A_1 = 1.3\pm 0.4$ in equation ([\[eq:A1\]](#eq:A1)), a simple relation of $P_{\rm cav}\propto M_{\rm mol}$ is acceptable. This fact would be useful when constructing sub-grid models of AGN feedback in numerical simulations, which have often adopted the classical Bondi accretion rate. The correlation between the mass of circumnuclear molecular gas and the AGN activity has been known for disk galaxies (e.g. (cite: 2016ApJ...827...81I), but there is a counter-example, see (cite: 2020ApJ...895...73K)). Thus, the AGN fueling mechanism for elliptical galaxies may be similar to that in the disk galaxies.

In contrast with $P_{\rm cav}$, the continuum luminosities both at $\sim
1.4$ GHz ($L_{1.4}$) and $\sim 100$–300 GHz ($L_{\rm col}$) seem to have no correlation with $M_{\rm mol}$ (figures [5](#fig:M-Lcon) and [6](#fig:M-L14)). The difference may be ascribed to the relevant time scales of AGN activities. The jet power $P_{\rm cav}$ is often described by the ratio of the energy required to inflate the cavity to its evolution time ($t_{\rm cav}$) such as the cavity’s buoyancy age ((cite: 2006MNRAS.372...21A; 2006ApJ...652..216R); see also (cite: 2016PASJ...68...26F)). Thus, $P_{\rm cav}$ reflects the AGN activity averaged over on a time scale of $t_{\rm cav}$, which is estimated to be $\sim 10^7$ yr (cite: 2006ApJ...652..216R). Interestingly, it is comparable to the gas accretion time $t_{\rm acc}$ (table [\[tab:Mmol\]](#tab:Mmol)). On the other hand, since the mm/submm ($\sim 100$–300 GHz) continuum is observed as nuclear point sources coincident with the AGNs, the size of the emitting regions should be $\lesssim 500$ pc. Since the light-travel time of the regions is only $\lesssim 1600$ yr, the emission virtually reflects the current activity of the AGN. The existence of the correlation between $P_{\rm
cav}$ and $M_{\rm mol}$ and the non-existence between the continuum luminosities and $M_{\rm mol}$ suggest that the circumnuclear gas is rather persistently fueling the AGN activity on a longer time scale ($t_{\rm cav}\sim 10^7$ yr), while the continuum luminosities vary on a short time scale. However, since $L_{\rm 1.4}$ is the total luminosity of the galaxy, it may include emissions from larger and older structures such as $\sim$ kpc radio jets and lobes[^4]. Thus, it could be proven that $L_{\rm 1.4}$ is more strongly correlated with $M_{\rm mol}$ than $L_{\rm con}$, once a larger sample becomes available.

In figures [3](#fig:M-Pcav)–[6](#fig:M-L14), Abell 262 appears to be an outlier. While it has a large amount of circumnuclear molecular gas ($M_{\rm mol}$), both the jet power ($P_{\rm cav}$) and the continuum luminosities ($L_{\rm con}$ and $L_{\rm 1.4}$) are small. This might be explained if the AGN activity has been gentle for a long time. Thus, there may be an additional factor that affects the activity other than the mass of circumnuclear molecular gas. For example, compared with other galaxies with similar amount of $M_{\rm mol}$ (Abell 1795, Hydra A, and PKS 0745–191), the mass of the black hole ($M_{\rm BH}$) at the center of Abell 262 is small (table [\[tab:pro\]](#tab:pro)). This may lead to a lower efficiency of power generation, which may explain its peculiarity. Alternatively, the AGN may have been at a “pre-feedback” phase (cite: 2023arXiv230304821U).

## The origin of the mm/submm continuum emission

So far, the origin of the continuum emission from the AGNs in massive elliptical galaxies has not been much studied in the mm/submm band. We study the spectral index of the continuum emission $\beta_{\rm con}$ by comparing the fluxes between the upper and lower sidebands of the CO lines (table [\[tab:result\]](#tab:result)). For most galaxies, the frequency difference between the sidebands is $\Delta\nu_{\rm ul}\sim 15$ GHz. However, it is only $\sim 2$ GHz for 2A0335$+$096 and PKS 0745$-$191, and their indices cannot be well constrained. Table [\[tab:result\]](#tab:result) shows that the indices are $\beta_{\rm con}< 0$ except for NGC 5044, which indicates that the emission is likely to be dominated by synchrotron radiation and the contribution of dust emission is minor. Thus, the assumption of $\gamma=-0.75$ in section [3.3](#sec:MLcon) seems to be reasonable.

Figure [7](#fig:L14-Lcon) compares the continuum luminosities at $\nu\sim \nu_{10}= 115.3$ GHz ($L_{\rm con}$) with those at $1.4$ GHz ($L_{1.4}$) estimated in section [3.3](#sec:MLcon). Those two luminosities are positively correlated and the correlation coefficient is 0.823 with $p$-value 0.0059. The correlation among the 9 objects can be represented by a power-law model of the form:

$$\begin{equation}
 \log\left(\frac{L_{\rm con}}{10^{42}\rm erg\: s^{-1}}\right) = A_3\log\left(\frac{L_{\rm 1.4}}{10^{42}\rm erg\: s^{-1}}\right) + B_3\:.
\end{equation}$$

The BCES $(Y|X)$ estimator gives $A_3=0.43\pm 0.10$ and $B_3=-0.51\pm
0.18$. We have confirmed that there is no correlation between fluxes $F_{\rm con}$ and $F_{\rm 1.4}$ (the correlation coefficient is -0.2567 and $p$-value is 0.48). Thus, it is unlikely that the $L_{\rm
1.4}$–$L_{\rm con}$ relation with $A_3\neq 1$ is due to redshift selection effects (cite: 1983ApJ...269..400F). The fact that $A_3$ is significantly smaller than one means that the ratio $L_{\rm con}/L_{\rm
1.4}\propto L_{1.4}^{A_3-1}$ increases as $L_{\rm 1.4}$ decreases. This suggests that the mm/submm continuum emission from the AGNs with large $L_{\rm 1.4}$ is pure synchrotron radiation, while that from the AGNs with smaller $L_{\rm 1.4}$ is contaminated by additional dust emission. Figure [8](#fig:SED) shows the ratios $F_{\rm con}/F_{\rm 1.4}$ and illustrates a possible continuum spectrum (solid line). We assume that the spectrum is simply represented by a combination of power-law (synchrotron) and modified blackbody (dust) components:

$$\begin{equation}
 S(\nu) = N_{\rm AGN}\nu^{\gamma} + N_{\rm BB}(1-e^{-(\nu/\nu_0)^b})B_\nu(\nu,T)\:,
\end{equation}$$

where $\gamma=-0.75$, $\nu_0=1.5$ THz, $b=1.5$, and $B_\nu(\nu,T)$ is a blackbody distribution (e.g. (cite: 2019A&A...621A..27F)). The dust temperature is assumed to be $T=10$ K, which is obtained for massive elliptical galaxies at cluster centers (e.g. (cite: 2019ApJ...879..103F)). The relatively low temperature may be because the surface area of the molecular gas is small for a given mass and it is well shielded (cite: 2019ApJ...879..103F). If $T>10$ K, the peak frequency of dust emission shifts to a higher frequency. The constants $N_{\rm AGN}$ and $N_{\rm BB}$ are adjusted to reproduce the observations of NGC 5044. Figure [8](#fig:SED) suggests that, except for NGC 5044, the contribution of the dust component at $\sim
100$–300GHz is small, which is consistent with observations of local AGNs (cite: 2022ApJ...938...87K).

![](f7.pdf)

![](f8.pdf)

# Conclusion

We have studied the relation between the circumnuclear molecular gas and the activities of the AGNs in the massive elliptical galaxies at the center of galaxy clusters. We analyzed ALMA archival data for 9 galaxies and obtained the circumnuclear molecular gas mass at $r<500$ pc from the AGNs. We found that the mass has a correlation with the jet power of the AGNs. Since the jet power is estimated from the size of X-ray cavities, it should be the average power over the cavity formation period. Thus, the correlation indicates that the circumnuclear gas is responsible for long-term AGN activities ($\sim 10^7$ yr). We also estimated the mass accretion rate of the cold gas assuming that the angular momentum transfer is caused by turbulence. We showed that the accretion rate is also correlated with the jet power. On the other hand, radio continuum emissions from the AGNs at 1.4 GHz and $\sim 100$–300 GHz are not correlated with the mass of circumnuclear molecular gas. This means that the gas is not directly associated with the current AGN activity. The spectra of the mm/submm ($\sim 100$–300 GHz) continuum emission indicate that they are mostly synchrotron radiation. However, comparison with 1.4 GHz luminosity suggests that dust emission is contaminated for lower luminosity AGNs.

We thank the reviewer for helpful comments that improved the paper. We also thank the EA ALMA Regional Center (EA-ARC) for their support. This work was supported by NAOJ ALMA Scientific Research Grant Code 2022-21A, and JSPS KAKENHI Grant Number JP20H00181, JP22H01268, JP22H00158 (Y.F.), JP20K14531, JP21H04496 (T.I.), JP19K03918 (N.K.), JP21H01137, JP18K03709 (H.N.). This paper makes use of the following ALMA data: ADS/JAO.2011.0.00735.S, ADS/JAO.2012.1.00837.S, ADS/JAO.2012.1.00837.S, ADS/JAO.2015.1.00598.S, ADS/JAO.2015.1.00623.S, ADS/JAO.2015.1.00627.S, ADS/JAO.2015.1.00644.S, ADS/JAO.2015.1.01198.S, ADS/JAO.2016.1.01214.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan.

(ref: 2017ApJS..233...25A) Albareti, F. D., Allende Prieto, C., Almeida, A., et al. 2017, ApJS, 233, 25. doi:10.3847/1538-4365/aa8992

(ref: 2006MNRAS.372...21A) Allen, S. W., Dunn, R. J. H., Fabian, A. C., et al. 2006, MNRAS, 372, 21. doi:10.1111/j.1365-2966.2006.10778.x

(ref: 1996ApJ...470..706A) Akritas, M. G. & Bershady, M. A. 1996, ApJ, 470, 706. doi:10.1086/177901

(ref: 2004ApJ...607..800B) Bı̂rzan, L., Rafferty, D. A., McNamara, B. R., et al. 2004, ApJ, 607, 800. doi:10.1086/383519

(ref: 2013ARA&A..51..207B) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207. doi:10.1146/annurev-astro-082812-140944

(ref: 1952MNRAS.112..195B) Bondi, H. 1952, MNRAS, 112, 195. doi:10.1093/mnras/112.2.195

(ref: 1992A&A...264..433B) Braine, J. & Combes, F. 1992, A&A, 264, 433

(ref: 2008ApJ...683L.107C) Cavagnolo, K. W., Donahue, M., Voit, G. M., et al. 2008, ApJL, 683, L107. doi:10.1086/591665

(ref: 2000A&A...356..788C) Churazov, E., Forman, W., Jones, C., et al. 2000, A&A, 356, 788. doi:10.48550/arXiv.astro-ph/0002375

(ref: 1998AJ....115.1693C) Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693. doi:10.1086/300337

(ref: 2009ApJ...705..624D) David, L. P., Jones, C., Forman, W., et al. 2009, ApJ, 705, 624. doi:10.1088/0004-637X/705/1/624

(ref: 2001MNRAS.328..762E) Edge, A. C. 2001, MNRAS, 328, 762. doi:10.1046/j.1365-8711.2001.04802.x

(ref: 2014ApJ...792...94D) David, L. P., Lim, J., Forman, W., et al. 2014, ApJ, 792, 94. doi:10.1088/0004-637X/792/2/94

(ref: 1994ARA&A..32..277F) Fabian, A. C. 1994, ARA&A, 32, 277. doi:10.1146/annurev.aa.32.090194.001425

(ref: 2012ARA&A..50..455F) Fabian, A. C. 2012, ARA&A, 50, 455. doi:10.1146/annurev-astro-081811-125521

(ref: 2019A&A...621A..27F) Falkendal, T., De Breuck, C., Lehnert, M. D., et al. 2019, A&A, 621, A27. doi:10.1051/0004-6361/201732485

(ref: 1983ApJ...269..400F) Feigelson, E. D. & Berg, C. J. 1983, ApJ, 269, 400. doi:10.1086/161051

(ref: 2019ApJ...879..103F) Fogarty, K., Postman, M., Li, Y., et al. 2019, ApJ, 879, 103. doi:10.3847/1538-4357/ab22a4

(ref: 1992CORV..C...0000F) Fouque, P., Durand, N., Bottinelli, L., Gouguenheim, L., & Paturel, G. 1992, Catalogue of Optical Radial Velocities (Meudon: Observatoire de Paris-Meudon), Vol. 1, 1

(ref: 2022ApJ...924...24F) Fujita, Y., Kawakatu, N., & Nagai, H. 2022, ApJ, 924, 24. doi:10.3847/1538-4357/ac31a6

(ref: 2016PASJ...68...26F) Fujita, Y., Kawakatu, N., & Shlosman, I. 2016, PASJ, 68, 26. doi:10.1093/pasj/psw012

(ref: 2017MNRAS.466..677G) Gaspari, M., Temi, P., & Brighenti, F. 2017, MNRAS, 466, 677. doi:10.1093/mnras/stw3108

(ref: 2016ApJ...827...81I) Izumi, T., Kawakatu, N., & Kohno, K. 2016, ApJ, 827, 81. doi:10.3847/0004-637X/827/1/81

(ref: 2020ApJ...895...73K) Kameno, S., Sawada-Satoh, S., Impellizzeri, C. M. V., et al. 2020, ApJ, 895, 73. doi:10.3847/1538-4357/ab8bd6

(ref: 2022ApJ...938...87K) Kawamuro, T., Ricci, C., Imanishi, M., et al. 2022, ApJ, 938, 87. doi:10.3847/1538-4357/ac8794

(ref: 1981A&AS...45..367K) Kuehr, H., Witzel, A., Pauliny-Toth, I. I. K., et al. 1981, A&AS, 45, 367

(ref: 2017MNRAS.464.4360M) Main, R. A., McNamara, B. R., Nulsen, P. E. J., et al. 2017, MNRAS, 464, 4360. doi:10.1093/mnras/stw2644

(ref: 2007ARA&A..45..117M) McNamara, B. R. & Nulsen, P. E. J. 2007, ARA&A, 45, 117. doi:10.1146/annurev.astro.45.051806.110625

(ref: 2014ApJ...785...44M) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2014, ApJ, 785, 44. doi:10.1088/0004-637X/785/1/44

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., et al. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: 2019ApJ...883..193N) Nagai, H., Onishi, K., Kawakatu, N., et al. 2019, ApJ, 883, 193. doi:10.3847/1538-4357/ab3e6e

(ref: 2008AJ....135.2424O) Ogando, R. L. C., Maia, M. A. G., Pellegrini, P. S., et al. 2008, AJ, 135, 2424. doi:10.1088/0004-6256/135/6/2424

(ref: 2019A&A...631A..22O) Olivares, V., Salome, P., Combes, F., et al. 2019, A&A, 631, A22. doi:10.1051/0004-6361/201935350

(ref: 2010MNRAS.408..961P) Pizzolato, F. & Soker, N. 2010, MNRAS, 408, 961. doi:10.1111/j.1365-2966.2010.17156.x

(ref: 1981ARA&A..19..137P) Pringle, J. E. 1981, ARA&A, 19, 137. doi:10.1146/annurev.aa.19.090181.001033

(ref: 2018ApJ...853..177P) Pulido, F. A., McNamara, B. R., Edge, A. C., et al. 2018, ApJ, 853, 177. doi:10.3847/1538-4357/aaa54b

(ref: 2008ApJ...687..899R) Rafferty, D. A., McNamara, B. R., & Nulsen, P. E. J. 2008, ApJ, 687, 899. doi:10.1086/591240

(ref: 2006ApJ...652..216R) Rafferty, D. A., McNamara, B. R., Nulsen, P. E. J., et al. 2006, ApJ, 652, 216. doi:10.1086/507672

(ref: 2019MNRAS.485..229R) Rose, T., Edge, A. C., Combes, F., et al. 2019, MNRAS, 485, 229. doi:10.1093/mnras/stz406

(ref: 2013MNRAS.432..530R) Russell, H. R., McNamara, B. R., Edge, A. C., et al. 2013, MNRAS, 432, 530. doi:10.1093/mnras/stt490

(ref: 2019MNRAS.490.3025R) Russell, H. R., McNamara, B. R., Fabian, A. C., et al. 2019, MNRAS, 490, 3025. doi:10.1093/mnras/stz2719

(ref: 2003A&A...412..657S) Salomé, P. & Combes, F. 2003, A&A, 412, 657. doi:10.1051/0004-6361:20031438

(ref: 2009MNRAS.398.1698S) Sanderson, A. J. R., Edge, A. C., & Smith, G. P. 2009, MNRAS, 398, 1698. doi:10.1111/j.1365-2966.2009.15214.x

(ref: 2003A&A...412..657S) Salomé, P. & Combes, F. 2003, A&A, 412, 657. doi:10.1051/0004-6361:20031438

(ref: 1973A&A....24..337S) Shakura, N. I. & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: 1983bhwd.book.....S) Shapiro, S. L. & Teukolsky, S. A. 1983, A Wiley-Interscience Publication, New York: Wiley, 1983

(ref: 2018MNRAS.475.3004S) Simionescu, A., Tremblay, G., Werner, N., et al. 2018, MNRAS, 475, 3004. doi:10.1093/mnras/sty047

(ref: 2023arXiv230304821U) Ubertosi, F., Gitti, M., Brighenti, F., et al. 2023, arXiv:2303.04821. doi:10.48550/arXiv.2303.04821

(ref: 2017ApJ...848..101V) Vantyghem, A. N., McNamara, B. R., Edge, A. C., et al. 2017, ApJ, 848, 101. doi:10.3847/1538-4357/aa8fd0

(ref: 1995ApJ...440..674X) Xie, T., Allen, M., & Langer, W. D. 1995, ApJ, 440, 674. doi:10.1086/175305

(ref: 2019ApJ...872..134Z) Zaw, I., Chen, Y.-P., & Farrar, G. R. 2019, ApJ, 872, 134. doi:10.3847/1538-4357/aaffaf

[^1]: https://editeodoro.github.io/Bbarolo/

[^2]: Exactly speaking, the continuum flux is not measured right at the frequency of the CO line. However, since the index is $1+\gamma=0.35$, the minor modification $\eta$ does not affect the results.

[^3]: https://www.cv.nrao.edu/nvss/NVSSlist.shtml

[^4]: The angular resolution of the observations is $45''$ (cite: 1998AJ....115.1693C), which corresponds to 18 kpc at $z=0.02$.

</paper>

Write the methods card for this paper.