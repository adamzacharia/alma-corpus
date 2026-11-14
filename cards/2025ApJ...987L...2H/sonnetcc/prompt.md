# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...987L...2H\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...987L...2H",
 "title": "Dissecting the Massive Pristine, Neutral Gas Reservoir of a Remarkably Bright Galaxy at z = 14.179",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Heintz, Kasper E.",
 "n_authors": 9,
 "arxiv_id": "2502.06016",
 "doi": "10.3847/2041-8213/ade393",
 "alma_projects_linked_by_archive": [
  "2023.A.00037.S",
  "2024.A.00007.S"
 ]
}
```

Paper text:
<paper>
# Dissecting the massive pristine, neutral gas reservoir of a remarkably bright galaxy at $z=14.179$

## Abstract

At cosmic dawn, the first stars and galaxies are believed to form from and be deeply embedded in clouds of dense, pristine gas. Here we present a study of the JWST/NIRSpec data of the most distant, spectroscopically confirmed galaxy observed to date, JADES-GS-z14-0 (GS-z14 for short), at $z=14.179$, combined with recently reported far-infrared measurements of the \[O iii\]-$88\mu$m and \[C ii\]-$158\mu$m line transitions and underlying dust-continuum emission. Based on the observed prominent damped Lyman-$\alpha$ (DLA) absorption profile, we determine a substantial neutral atomic hydrogen (H i) column density, $\log (N_{\rm HI} / {\rm cm^{-2}}) = 22.27^{+0.08}_{-0.09}$, consistent with previous estimates though seemingly at odds with the dynamical and gas mass of the galaxy. Using various independent but complementary approaches, considering the implied neutral gas mass from the DLA measurement, the star-formation rate surface density, and the metal abundance, we demonstrate that the total gas mass of GS-z14 is of the order $\log (M_{\rm gas} / M_\odot) = 9.8\pm 0.3$. This implies a substantial gas mass fraction, $f_{\rm gas} \gtrsim 0.9$ and that the bulk of the interstellar medium (ISM) is in the form of H i.

We show that the derived gas mass is fully consistent with the non-detection of \[C ii\]-$158\mu$m, assuming an appropriate scaling to the neutral gas. The low dust-to-gas ratio, $A_V/N_{\rm HI} = (1.3\pm 0.6)\times 10^{-23}$ mag cm$^2$, derived in the line-of-sight through the DLA further indicates that the absorbing gas is more pristine than the central, star-forming regions probed by the \[O iii\]-$88\mu$m emission. These results highlight the implications for far-infrared line-detection searchers attainable with ALMA and demonstrate that the bright, relatively massive galaxy GS-z14 at $z=14.179$ is deeply embedded in a substantial, pristine H i gas reservoir dominating its baryonic matter content.

# Introduction

The first stars and galaxies are believed to have formed within the first 150-250 Myr after the Big Bang, at redshifts around $z=15-20$ (cite: Robertson22). This process is mainly driven by the inflow of pristine gas, mostly in the form of neutral atomic hydrogen (H i), onto dark matter halos. With the advent of the *James Webb Space Telescope* (JWST), we are now starting to uncover and spectroscopically characterize a substantial population of galaxies close to this first assembly stage at $z=10-14$ (cite: CurtisLake23; Bunker23_gnz11; ArrabalHaro23; Castellano24; Hsiao24a; Hsiao24b; Witstok24; Carniani24a; Carniani24b; Zavala25), and potentially even more distant sources at $z>15$ as indicated by their photometry (cite: Naidu22; Donnan23; Castellano22; Castellano23; Bouwens23; Atek23b; Harikane23; Austin24; Kokorev24; Whitler25).

The redshifts for these distant sources can be difficult to accurately pin-point with JWST near-infrared spectroscopy alone, as the Lyman-$\alpha$ break redshifts were found already in early JWST data to systematically overestimate the emission-line redshifts (cite: CurtisLake23; ArrabalHaro23; Fujimoto23_ceers; Finkelstein24). This effect was later shown to originate from dense, neutral gas reservoirs in and around these galaxies, some with substantial H i column densities, $N_{\rm HI} \gtrsim 10^{22}$ cm$^{-2}$, in the form of extremely damped Ly$\alpha$ (DLA) absorption line profiles (cite: Heintz24_DLA; Umeda23; DEugenio24; Hainline24b; Witstok24). These deep DLA absorption profiles even systematically bias the photometrically-derived redshifts due to their high incidence rate in the overall $z \gtrsim 9$ galaxy population (cite: Heintz25; Asada24). These measurements indicate that we are starting to probe the primordial matter that drives the formation of these galaxies and fuels their intense, early star-formation activity.

Due to the intrinsic faintness of rest-frame UV emission lines covered by JWST/NIRSpec for galaxies at $z>10$, and with the added complication of potential strong DLA absorption, a promising alternative avenue of accurately determining the redshift of these sources is via bright far-infrared emission lines. While the first efforts with the Atacama Large Millimetre/sub-millimetre Array (ALMA) mostly returned non-detections (cite: Fujimoto23_alma), the \[O iii\]-$88\mu$m emission of the galaxy GHZ2 were detected at $z=12.33$ (cite: Zavala24). Further, ALMA observations of JADES-GS-z14-0 (GS-z14 for short), revealed a significant detection of the \[O iii\]-$88\mu$m line (cite: Schouws24; Carniani24b) lining up precisely with a marginal ($3.6\sigma$) NIRSpec detection of the C iii\]$\lambda 1907, 1909 \, \text{\AA}$ doublet (cite: Carniani24a). The line-redshift was thus confirmed to be at $z=14.1796\pm 0.0006$, substantially lower ($\Delta z = 0.14$) than the photometric and Ly$\alpha$ break redshifts due to the strong DLA recovered in the JWST spectrum (cite: Carniani24b). Deep ALMA follow-up observations targeting the far-infrared \[C ii\]-$158\mu$m line revealed a non-detection, however, which potentially indicate a surprisingly low gas fraction in GS-z14 (cite: Schouws25) compared to other high-redshift sources (cite: Heintz23_JWSTALMA; Aravena24; Algera25).

In this Letter, we reanalyze the JWST/NIRSpec Prism spectrum of GS-z14 in the context of its H i gas content, corroborated by recent far-infrared line emission and continuum measurements. In Sect. [2](#sec:obs) we detail the observational data and in Sect. [3](#sec:res) we present the main analysis and results. In Sect. [4](#sec:disc), we will discuss and conclude on our work. Throughout the paper, we assume the concordance $\Lambda$CDM cosmological model with $H_0 = 67.4$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m} = 0.315$, and $\Omega_{\Lambda} = 0.685$ (cite: Planck18). This is also used to infer cosmological parameters such as the luminosity distance to GS-z14 and age of the Universe with the `Astropy` software package (cite: Astropy).

# Observations

GS-z14 was first identified by (cite: Hainline24a) with a photometric redshift $z_{\rm phot} = 14.51$, refined to $z_{\rm phot} = 14.39$ in the high-redshift galaxy population study by (cite: Robertson24). Multi-band JWST/NIRCam imaging was obtained as part of the JWST Advanced Deep Extragalactic Survey (cite: Eisenstein23a), the First Reionization Epoch Spectroscopically Complete Observations (cite: Oesch23), and of the JADES Origins Field (cite: Eisenstein23b). The data reduction is outlined in (cite: Rieke23; Eisenstein23a; Eisenstein23b). The photometry implicitly used in this article (to scale the spectrum) was obtained by modeling the galaxy with a Sérsic profile, using the `forcepho` tool (Johnson B., in prep.), as described in (cite: Carniani24a). The distinctive advantage of `forcepho` is the ability to model the galaxy surface brightness before combining individual frames into a mosaic (cite: Baker25). The fiducial `forcepho` model yields a half-light semi-major axis of $R_{\rm UV} = 0.26$ kpc and a Sérsic index of 1. The gravitational lensing magnification from a foreground nearby galaxy at $z=3.47$ is estimated to be only $\mu=1.17$ (cite: Carniani24a), so the lensing correction of 8 per cent is smaller than the 10 per cent systematic uncertainties of typical size measurements. GS-z14 has further been detected in $7.7\mu$m imaging with JWST/MIRI (cite: Helton24), implying the presence of strong nebular emission lines.

The JWST spectrum was first presented in (cite: Carniani24a). The data were obtained using the NIRSpec (cite: Jakobsen22) Micro-Shutter Assembly (cite: Ferruit22), with three-shutter slitlets (Prog. ID 1287, PI: Luetzgendorf). Here we focus on the prism spectrum[^1], which covers wavelengths $\lambda = 0.6-5.3\mu$m with a spectral resolving power $\mathcal{R}=30\text{--}300$, although the most important spectral region in this article, the Ly$\alpha$ break at $\lambda \approx 2~\mu$m, has $\mathcal{R}\sim 60$. The prism observations used the NRSIRS2 readout mode to mitigate pink noise (cite: Moseley10; Rauscher17), with 19 groups per integration and 2 integrations per exposure, with three nodded exposures for accurate background subtraction. This sequence (about 2.33 h total integration) was repeated four times, for a final on-source time of 9.3 h. Following (cite: Carniani24a), we apply a flux correction factor to the reduced spectrum to match the normalization of the `forcepho` photometry data using a simple polynomial $F_{\rm corr} = F_{\rm red} \times (0.18\times \lambda(\mu{\rm m}) + 1)$. This effectively takes into account and corrects for potential slit losses and/or uncertainties in the overall flux calibration.

Throughout this work, we adopt the spectral and physical galaxy measurements reported in (cite: Carniani24b). These were obtained using the `prospector` spectral-energy distribution (SED) modeling tool (cite: Johnson21), taking into account the full multi-wavelength spectroscopic and imaging data obtained for GS-z14. This yields a star-formation rate $SFR=14.5\pm 3~\mathrm{M_\odot \, yr^{-1}}$ and a stellar mass of $\log (M_\star/\mathrm{M_\odot}) = 8.29^{+0.09}_{-0.10}$, assuming a (cite: Chabrier03) initial mass function (IMF).

Dedicated far-infrared follow-up observations with ALMA were carried out to search for the \[O iii\]-$88\mu$m (Prog. ID: 2023.A.00037.S, PI: Schouws) and the \[C ii\]-$158\mu$m (Prog. ID: 2024.A.00007.S, PI: Schouws) line transitions. \[O iii\]-$88\mu$m is detected at $>6\sigma$ with a line luminosity $L_{\rm [OIII]} = (2.0\pm 0.5)\times 10^{8}\,L_\odot$ (cite: Schouws24; Carniani24b). Deep ALMA observations targeting the \[C ii\]-$158\mu$m line, however, resulted in a non-detection at a limit $<6\times 10^{7}\,L_\odot$ (cite: Schouws25), though still consistent with the typical high-redshift galaxy population (cite: Harikane20; Carniani20). Here we examine the constraints delivered from the far-infrared line transitions in context of the H i column density and physical properties to probe the full baryonic matter budget of GS-z14.

![](Figs/AltFig1.pdf)

# Analysis and results

Based on the observed Ly$\alpha$ break, and given the lack of strong rest-frame UV/optical nebular emission lines, (cite: Carniani24a) inferred a redshift of $z_{\rm Ly\alpha,break} = 14.32^{+0.08}_{-0.20}$, with the large uncertainties due to the covariance between redshift and H i column density. The significant detection of the far-infrared \[O iii\]-$88\mu$m emission line reveals the systemic redshift to be $z=14.1796\pm 0.0006$ (cite: Carniani24b; Schouws24). This measurement can break the degeneracy between redshift and H i column density, and constrains that a substantial H i column density arising in proximate neutral gas has imprinted a pronounced Ly$\alpha$ damping-wing absorption profile on the rest-frame UV continuum (cite: Carniani24b). We model the DLA absorption with a Voigt profile following (cite: Heintz24_z54), using the approximation from (cite: TepperGarcia06), and convolve the best-fit model with the spectral resolution at each step during the optimization. The high H i column densities of the absorbing gas effectively make this modeling only sensitive to the H i column density, $N_{\rm HI}$, reflected in the broad, prominent Ly$\alpha$ damping wing. Still, we include the unconstrained $x_{\rm HI}$ to fully capture the covariance between this and the other two parameters in the model. We assume that the rest-frame UV continuum can be approximated by a smooth power-law function, $F_\lambda \propto \lambda^{-\beta_{\rm UV}}$. Introducing more complex spectral shapes or prominent Ly$\alpha$ emission does not significantly affect the derived $N_{\rm HI}$ (cite: Heintz24_DLA), at least at high H i column densities (cite: Huberty25). We also include a prescription of the neutral hydrogen fraction $x_{\rm HI}= n_{\rm HI}/n_{\rm H,tot}$ of the IGM on our modeling, which we expect to be fully neutral at $z\approx 14$ (cite: MiraldaEscude98; Inoue14). We use `dynesty` nested sampling (cite: Speagle20) to sample the posteriors of the parameters $\log (N_{\rm HI})$, $x_{\rm HI}$, and $\beta_{UV}$, assuming a fixed DLA redshift of $z=14.1796$.

The best-fit DLA model is shown in Fig. [1](#fig:spec), together with the posterior distributions on the derived quantities; $\log (N_{\rm HI} / {\rm cm^{-2}}) = 22.27^{+0.08}_{-0.09}$, $x_{\rm HI} > 0.41$ ($1\sigma$ from the $68\%$ highest density interval), and $\beta_{\rm UV} = -1.93\pm 0.08$. The derived $N_{\rm HI}$ is 0.3 dex higher than the column density inferred from the full spectro-photometric fitting by (cite: Carniani24a), though still consistent within $3\sigma$. Setting the neutral hydrogen fraction to $x_{\rm HI} = 1$ as expected at $z=14$ does not significantly change the result since the DLA from the local H i gas dominates the optical depth of the Ly$\alpha$ absorption profile. Considering a model with only an IGM contribution ($x_{\rm HI}=1$) provides a statistically worse fit to the data with $\chi_\nu^2 = 1.69$, compared to $\chi_\nu^2 = 1.23$ for the fit with a DLA component. Additionally, the difference in Bayesian Information Criteria between the models $\Delta \rm BIC = 82$ indicates a strong statistical preference for the IGM+DLA model (see Fig. [1](#fig:spec)). We also compare the DLA model to a purely nebular continuum model, dominated by the two-photon ($2\gamma$) emission at rest-frame UV wavelengths, assuming $T = 20,000$ K and $n_e = 10^2$ cm$^{-3}$ from (cite: Schirmer16). This matches well the slope of the spectrum, but the strong UV turnover is inconsistent with the data ($\chi_\nu^2 = 1.53$).

With an absolute UV magnitude, $M_{\rm UV} = -20.81\pm 0.16$ mag (cite: Carniani24a), GS-z14 is thus an exemplary case of a bright, star-forming galaxy embedded in a substantial neutral gas reservoir.

To gauge the total H i gas mass of the galaxy, we use the measured H i column density in the line of sight and assume that the half-mass radius of the neutral gas is $\sim 3\times$ the rest-frame UV size (cite: Fujimoto20; Fudamoto22). For a spherically distributed gas, this yields an H i gas mass of $M_{\rm HI} = 5\times 10^{9}\,M_\odot$, substantially higher than the previously reported upper bound inferred on the (molecular) gas mass, $M_{\rm mol} < 10^{9.2}\,M_\odot$ (cite: Schouws25). If we consider the metallicity-dependent relation converting the \[C ii\]-$158\mu$m line luminosity into a H i gas mass (cite: Heintz21), based on $\gamma$-ray burst sightlines through high-redshift star-forming galaxies, we derive an upper bound of $M_{\rm HI} < 10^{9.9}\,M_\odot$ ($3\sigma$). This suggests that the derived H i gas masses are still consistent within the upper bound allowed by the non-detection of the \[C ii\]-$158\mu$m emission, taking into account the relatively low metallicity of the galaxy. However, this estimate of $M_{\rm HI}$ from the DLA $N_{\rm HI}$ is heavily dependent on the assumed geometry of the system. To corroborate the evidence for a substantial gas fraction in the system, we consider the Kennicutt-Schmidt relation (cite: Kennicutt12), universally connecting the SFR and gas surface density. We determine the star-formation rate surface density as $\Sigma_{\rm SFR} = {\rm SFR}_{\rm UV} / 2\pi R^2_{\rm UV}$, which given the half-light radius $R_{\rm UV} = 0.26$ kpc reported by (cite: Carniani24a) yields $\log (\Sigma_{\rm SFR} / M_{\odot}\,{\rm yr}^{-1}\,{\rm kpc}^{-2}) = 1.5\pm 0.30$ (assuming an inflated $30\%$ error on the SFR). This implies a molecular gas surface density of $\log (\Sigma_{\rm H_2} / M_{\odot}\,{\rm pc}^{-2}) = 3.6\pm 0.3$ following the global-galaxy Kennicutt-Schmidt relation, which we convert to a molecular gas mass of $\log (M_{\rm H_2}/M_\odot) = 9.2\pm 0.3$ within the star-forming region, at the limit for the upper bound derived from the \[C ii\]-to-H$_2$ conversion (cite: Schouws25). The global Kennicutt-Schmidt relation for the *total* (H i + H$_2$) gas mass predicts a higher total gas surface density $\log (\Sigma_{\rm gas} / M_{\odot}\,{\rm pc}^{-2}) = 4.2\pm 0.3$ and total gas mass $\log (M_{\rm gas}/M_\odot) = 9.8\pm 0.3$ within the star-forming region. Taken at face value, this implies a large gas fraction $f_{\rm gas} = M_{\rm gas} / (M_\star + M_{\rm gas}) \gtrsim 0.9$. Further, this estimate is consistent with the bulk of the interstellar medium (ISM) in GS-z14 being in the form of H i ($M_{\rm HI} = M_{\rm gas}-M_{\rm H_2} = 5\times 10^{9}\,M_\odot$, $M_{\rm HI} \approx 3\times M_{\rm H_2}$) exactly as predicted from the DLA H i column density.

Alternatively, we can determine the metal mass of GS-z14 from the measured line detection of \[O iii\]-$88\mu$m, and convert into a gas mass based on the metallicity quantified as an oxygen abundance, $\log ({\rm O/H}) = 7.92$ (for $Z/Z_\odot = 0.17$, and a solar oxygen abundance of $12+\log ({\rm O/H})_\odot = 8.69$; (cite: Asplund09)). The metal mass in the ISM is defined as $M_Z = M_{\rm gas}\times Z/Z_\odot \times Z_{\rm \odot,ref}$ with $Z_{\rm \odot,ref} = 0.018$. Using the set of observations from the local *Herschel* dwarf galaxy survey (cite: Cormier15) and smoothed particle hydrodynamics simulations applied to cosmological zoom-in simulations (cite: Olsen17), we find that the \[O iii\]-to-$M_Z$ calibration is anti-correlated with the $L_{\rm [OIII]} / L_{\rm [CII]}$ line luminosity ratio (cite: Heintz23_mz), such that $\log (M_Z / L_{\rm [OIII]}) = -1.0\pm 0.2$ for $L_{\rm [OIII]} / L_{\rm [CII]}>3$. This yields a total metal mass in the ISM of $M_Z = (2.0\pm 0.6)\times 10^{7}\,M_\odot$, which implies a total gas mass of $\sim 10^{9.8}\,M_\odot$ when taking the metallicity of GS-z14 into account, consistent with the above estimates.

To investigate in more detail the composition of the absorbing gas, we determine the dust-to-gas ratio, $A_V/N_{\rm HI}$. Here, $N_{\rm HI}$ is derived from the DLA model, and the visual extinction $A_V$ is determined from the spectral slope. Assuming a steep, intrinsic power-law with $\beta_{\rm UV} = -3$ requires $A_V = 0.3$ mag for a SMC-like reddening curve (cite: Gordon03) to match the observed rest-frame UV spectral slope. This quantity is effectively the maximum allowed amount of dust in the line-of-sight that will extinguish the light, since the intrinsic spectral slope will be redder for an slightly older stellar population on average. This upper bound is also consistent with the visual attenuation $A_V = 0.25\pm 0.10$ inferred from the full spectro-photometric modeling of the SED and line emission for GS-z14 (cite: Carniani24b). This yields a dust-to-gas ratio of $A_V/N_{\rm HI} = (1.3\pm 0.6)\times 10^{-23}$ mag cm$^{2}$. We compare this to equivalent measures from the compilation of $\gamma$-ray burst sightlines through high-redshift ($z=1.7-6.3$) star-forming galaxies presented in (cite: Heintz23_GRB) and to average value observed in the Milky Way and the Small and Large Magellanic Clouds (cite: Konstantopoulou24) in Fig. [2](#fig:dtg). It is evident that GS-z14 has a relatively low dust-to-gas ratio, consistent with the most metal-poor (\[M/H\]$<-1.0$) $\gamma$-ray burst sightlines. This suggest that this particular sightline either has a low dust-to-gas ratio due to inefficient dust production (or more violent dust destruction mechanisms) or that the DLA mainly trace more pristine gas than the galaxy itself. The empirical, best-fit relation indicate a gas-phase metallicity of $-1.95 < {\rm [M/H]} < -1.15$ (or $12+\log({\rm O/H}) = 6.75-7.55$). The inferred lower gas-phase metallicity from this approach compared to the emission-line metallicity is similar in methodology and consistent with the results from (cite: DEugenio24) for GS-z12 at $z=12.5$. We will discuss the observed dust deficit further in Sect. [4](#sec:disc) below.

![](Figs/DTGmet.pdf)

![](Figs/GalaxyDLA.pdf)

# Discussion and conclusions

We have examined in detail the gas content of the most distant, spectroscopically confirmed galaxy observed to date, GS-z14 at $z=14.179$ (cite: Carniani24a; Carniani24b; Schouws24). This galaxy is relatively bright, with an absolute UV magnitude $M_{\rm UV} = -20.8$ mag, a stellar mass $M_\star \sim 10^{8.3}\,M_\odot$, and shows evidence for chemically enriched gas ($Z/Z_\odot \sim 0.17$). We determined the total H i column density for GS-z14 to be $\log (N_{\rm HI}/{\rm cm^{2}})=22.27^{+0.08}_{-0.09}$, integrated over the line-of-sight. Assuming a simple spherical geometry, this implies a substantial H i gas mass of $M_{\rm HI} = 5\times 10^{9}\,M_\odot$. While a spherical geometry is an over-simplification, the high detection rate of DLA around galaxies at $z>10$ (cite: Heintz25) almost certainly implies a high covering factor, closer to a spherical distribution than to a thin disc. Importantly, we found this large H i gas mass estimate to be consistent with the expected total gas mass from the star-formation rate surface density and the universal Kennicutt-Schmidt relation and within the limits allowed by the non-detection of the \[C ii\]-$158\mu$m line emission (cite: Schouws25). These independent but complementary measurements all pointed to a total gas mass of the order $\log (M_{\rm gas}/M_\odot) = 9.5\pm 0.3$, implying a substantial gas mass fraction, $f_{\rm gas}\sim 0.7-0.9$. Assuming a bottom-light or top-heavy IMF (cite: Bate23; Bate25; Katz25) would increase the fraction even further. This implies that the bulk ISM, and the baryonic matter content of GS-z14 overall, is largely dominated by H i. Based on the low visual attenuation, $A_V = 0.25\pm 0.10$, we determined that the metallicity of the DLA is lower than that of the central star-forming region. This suggested that GS-z14 is embedded in a substantial, pristine neutral gas reservoir.

Previous estimates reporting a low gas fraction, $f_{\rm gas} \lesssim 0.7$, for GS-z14 are based on the dynamical mass estimated within the \[O iii\]-$88\mu$m emitting region ($\log (M_{\rm dyn}/M_\odot) = 9.0\pm 0.2$) and the non-detection of the \[C ii\]-$158\mu$m emission line (cite: Carniani24b; Schouws25). We argue that since \[O iii\]-$88\mu$m solely originates from the central, most intense star-forming regions (as is also the case for C iii\] $\lambda 1909$), this line transition is arguably not a reliable tracer of the total baryonic matter in the galaxy. Indeed, the rest-frame UV and the \[O iii\]-$88\mu$m emission has been observed to be much more spatially compact than the \[C ii\]-$158\mu$m emitting region (cite: Harikane20; Fujimoto20; HerreraCamus21; Fudamoto22). The fact that it is consistent with the inferred stellar mass from the SED modeling (cite: Carniani24b) instead supports this line mostly tracing the central star-forming component. The upper bound on the molecular gas mass inferred from the non-detection of \[C ii\]-$158\mu$m (cite: Schouws25) will also likely underestimate the total gas mass of the galaxy, given that \[C ii\] predominantly traces the neutral atomic gas, in particular in low-metallicity regions (cite: Madden93; Heintz22). This is because the ionization potential of neutral carbon (11.26 eV) is below that of neutral hydrogen (13.6 eV), such that any inherent ISM radiation field will ionize carbon to C$^+$ in the neutral ISM. Indeed, the substantial H i column density suggest that there is a large abundance of neutral H outside the central H ii region. We show a schematic of this proposed interpretation in Fig. [3](#fig:gal).

We note that the H$_2$ fraction may be suppressed in these galaxies by the lack of dust compared to lower-redshift galaxies, and that the lack of \[C ii\] could also be explained by a low C/O abundance ratio (cite: Carniani24b), which is expected for low-metallicity galaxies (cite: Nicholls17; TJones23; ArellanoCordova22; Curti24z94), or the high ionization parameter $\log U = -2.4$ which suppresses \[C ii\] in favor of C iii\].

The analytical model developed for GS-z14 by (cite: Ferrara24) of its star formation history and general physical properties is generally consistent with the observed quantities (cite: Carniani24b), and particularly predicts a low dust-to-gas mass ratio of $10^{-3.5}$. This is exactly at the limit we predict from the total gas mass and the upper bound on the dust mass $<10^{6}\,M_\odot$ from the far-infrared continuum (cite: Schouws24). We note that the observed dust-to-gas mass ratio ($<10^{-3.5}$) is $\sim 10\times$ lower than the Galactic average (cite: Konstantopoulou24), but consistent with the general trend seen at the local to high-redshift universe considering its low metallicity (cite: Heintz23_GRB). Further, the line-of-sight dust-to-gas ratio, $A_V/N_{\rm HI}$, is equally lower than the Galactic average at $4.5\times 10^{-22}$ mag cm$^2$ (cite: Watson11). These independent measures thus validate the low dust content of GS-z14, but suggest that it is primarily driven by the metallicity of the galaxy.

Our results have important implications for the follow-up strategies with both JWST and ALMA for characterizing in depth the gas and metal abundances of very high-redshift ($z>10$) galaxies. First, the typical lower metallicities of the galaxies affect the C/O abundance ratio and how in particular the far-infrared \[C ii\]-$158\mu$m emission scales with the neutral gas mass (cite: Katz22), while the \[O iii\]-$88\mu$m transition remains a valid tracer of the star-formation activity of even the most distant galaxies. This greatly motivates targeting the \[O iii\]-$88\mu$m line transition (cite: Bouwens22) to accurately pin-point the redshift of very high-redshift galaxies. We caution, however, that the gas mass inferred from the dynamics of \[O iii\] will likely underestimate the true total baryonic matter content of the sources. Second, the typical strong DLAs detected in the spectra of galaxies at $z>10$ (cite: Heintz24_DLA; Heintz25; Umeda23; DEugenio24; Hainline24b; Witstok24; Asada24) need to be taken into account when designing the far-infrared line scan configuration, which will be at a lower redshift than implied from the Ly$\alpha$ break alone. Finally, quantifying the metal abundance in the absorbing gas traced by the DLA will help disentangle whether this is mainly pristine, intergalactic gas or consistent with the chemically enriched interstellar inferred from the SED and nebular emission line ratios. For the substantial H i column densities $N_{\rm HI}\gtrsim 10^{22}$ cm$^{-2}$ and metallicities $Z/Z_\odot \sim 10\%$ seen in GS-z14 and other spectroscopically confirmed galaxies at $z>10$, we would expect to be able to detect the low-ion metal absorption lines from O i $\lambda 1302$ or C ii $\lambda 1334$, tracing the metal abundance of the neutral gas, in the higher resolution JWST/NIRSpec grating spectra. The main challenge will be to achieve high enough signal-to-noise in the rest-frame UV continuum to robustly measure the optical depth and thereby the column densities of the metal absorption lines, which requires substantial exposure times even for the intrinsically bright GS-z14 due to the large cosmological distances. This measure will, however, definitely establish whether the massive DLAs seen in most high-redshift spectra are predominantly tracing primordial or chemically enriched neutral atomic gas at cosmic dawn.

We would like to thank Johan Fynbo and Peter Laursen for insightful discussions about the interpretation of the results presented in this work. We also acknowledge and appreciate the substantial amount of work from the JADES collaboration in defining and carrying out the JWST/NIRSpec spectroscopic follow-up of the most distant galaxies uncovered to date. This work has received funding from the Swiss State Secretariat for Education, Research and Innovation (SERI) under contract number MB22.00072. The Cosmic Dawn Center (DAWN) is funded by the Danish National Research Foundation under grant DNRF140. FDE acknowledges the ERC Advanced Grant 695671 “QUENCH” and support by the Science and Technology Facilities Council (STFC) and by the UKRI Frontier Research grant RISEandFALL.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with programs #1210, #1287, and #3215. This work was furthermore based on observations taken by the Atacama Large Millimeter/submillimeter Array (ALMA). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

JWST(NIRSpec), ALMA

# Software

Astropy (cite: Astropy), Matplotlib (cite: Matplotlib), Numpy (cite: Numpy)

natexlab

(ref: Algera25) Algera, H., Rowland, L., Stefanon, M., et al. 2025, arXiv e-prints, arXiv:2501.10508, doi: [`10.48550/arXiv.2501.10508`](http://doi.org/10.48550/arXiv.2501.10508)

(ref: Aravena24) Aravena, M., Heintz, K., Dessauges-Zavadsky, M., et al. 2024, A&A, 682, A24, doi: [`10.1051/0004-6361/202347281`](http://doi.org/10.1051/0004-6361/202347281)

(ref: ArellanoCordova22) Arellano-Córdova, K. Z., Berg, D. A., Chisholm, J., et al. 2022, ApJL, 940, L23, doi: [`10.3847/2041-8213/ac9ab2`](http://doi.org/10.3847/2041-8213/ac9ab2)

(ref: ArrabalHaro23) Arrabal Haro, P., Dickinson, M., Finkelstein, S. L., et al. 2023, Nature, 622, 707, doi: [`10.1038/s41586-023-06521-7`](http://doi.org/10.1038/s41586-023-06521-7)

(ref: Asada24) Asada, Y., Desprez, G., Willott, C. J., et al. 2024, arXiv e-prints, arXiv:2410.21543, doi: [`10.48550/arXiv.2410.21543`](http://doi.org/10.48550/arXiv.2410.21543)

(ref: Asplund09) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481, doi: [`10.1146/annurev.astro.46.060407.145222`](http://doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: Astropy) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Atek23b) Atek, H., Shuntov, M., Furtak, L. J., et al. 2023, MNRAS, 519, 1201, doi: [`10.1093/mnras/stac3144`](http://doi.org/10.1093/mnras/stac3144)

(ref: Austin24) Austin, D., Conselice, C. J., Adams, N. J., et al. 2024, arXiv e-prints, arXiv:2404.10751, doi: [`10.48550/arXiv.2404.10751`](http://doi.org/10.48550/arXiv.2404.10751)

(ref: Baker25) Baker, W. M., Tacchella, S., Johnson, B. D., et al. 2025, Nature Astronomy, 9, 141, doi: [`10.1038/s41550-024-02384-8`](http://doi.org/10.1038/s41550-024-02384-8)

(ref: Bate23) Bate, M. R. 2023, MNRAS, 519, 688, doi: [`10.1093/mnras/stac3481`](http://doi.org/10.1093/mnras/stac3481)

(ref: Bate25) —. 2025, MNRAS, 537, 752, doi: [`10.1093/mnras/staf059`](http://doi.org/10.1093/mnras/staf059)

(ref: Bouwens22) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160, doi: [`10.3847/1538-4357/ac5a4a`](http://doi.org/10.3847/1538-4357/ac5a4a)

(ref: Bouwens23) Bouwens, R. J., Stefanon, M., Brammer, G., et al. 2023, MNRAS, 523, 1036, doi: [`10.1093/mnras/stad1145`](http://doi.org/10.1093/mnras/stad1145)

(ref: Bunker23_gnz11) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, A&A, 677, A88, doi: [`10.1051/0004-6361/202346159`](http://doi.org/10.1051/0004-6361/202346159)

(ref: Carniani20) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136, doi: [`10.1093/mnras/staa3178`](http://doi.org/10.1093/mnras/staa3178)

(ref: Carniani24a) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024a, Nature, 633, 318, doi: [`10.1038/s41586-024-07860-9`](http://doi.org/10.1038/s41586-024-07860-9)

(ref: Carniani24b) Carniani, S., D’Eugenio, F., Ji, X., et al. 2024b, arXiv e-prints, arXiv:2409.20533, doi: [`10.48550/arXiv.2409.20533`](http://doi.org/10.48550/arXiv.2409.20533)

(ref: Castellano22) Castellano, M., Fontana, A., Treu, T., et al. 2022, ApJL, 938, L15, doi: [`10.3847/2041-8213/ac94d0`](http://doi.org/10.3847/2041-8213/ac94d0)

(ref: Castellano23) —. 2023, ApJL, 948, L14, doi: [`10.3847/2041-8213/accea5`](http://doi.org/10.3847/2041-8213/accea5)

(ref: Castellano24) Castellano, M., Napolitano, L., Fontana, A., et al. 2024, ApJ, 972, 143, doi: [`10.3847/1538-4357/ad5f88`](http://doi.org/10.3847/1538-4357/ad5f88)

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Cormier15) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, A&A, 578, A53, doi: [`10.1051/0004-6361/201425207`](http://doi.org/10.1051/0004-6361/201425207)

(ref: Curti24z94) Curti, M., Witstok, J., Jakobsen, P., et al. 2024, arXiv e-prints, arXiv:2407.02575, doi: [`10.48550/arXiv.2407.02575`](http://doi.org/10.48550/arXiv.2407.02575)

(ref: CurtisLake23) Curtis-Lake, E., Carniani, S., Cameron, A., et al. 2023, Nature Astronomy, 7, 622, doi: [`10.1038/s41550-023-01918-w`](http://doi.org/10.1038/s41550-023-01918-w)

(ref: DEugenio24) D’Eugenio, F., Maiolino, R., Carniani, S., et al. 2024, A&A, 689, A152, doi: [`10.1051/0004-6361/202348636`](http://doi.org/10.1051/0004-6361/202348636)

(ref: Donnan23) Donnan, C. T., McLeod, D. J., Dunlop, J. S., et al. 2023, MNRAS, 518, 6011, doi: [`10.1093/mnras/stac3472`](http://doi.org/10.1093/mnras/stac3472)

(ref: Eisenstein23a) Eisenstein, D. J., Willott, C., Alberts, S., et al. 2023a, arXiv e-prints, arXiv:2306.02465, doi: [`10.48550/arXiv.2306.02465`](http://doi.org/10.48550/arXiv.2306.02465)

(ref: Eisenstein23b) Eisenstein, D. J., Johnson, B. D., Robertson, B., et al. 2023b, arXiv e-prints, arXiv:2310.12340, doi: [`10.48550/arXiv.2310.12340`](http://doi.org/10.48550/arXiv.2310.12340)

(ref: Ferrara24) Ferrara, A. 2024, A&A, 689, A310, doi: [`10.1051/0004-6361/202450944`](http://doi.org/10.1051/0004-6361/202450944)

(ref: Ferruit22) Ferruit, P., Jakobsen, P., Giardino, G., et al. 2022, A&A, 661, A81, doi: [`10.1051/0004-6361/202142673`](http://doi.org/10.1051/0004-6361/202142673)

(ref: Finkelstein24) Finkelstein, S. L., Leung, G. C. K., Bagley, M. B., et al. 2024, ApJL, 969, L2, doi: [`10.3847/2041-8213/ad4495`](http://doi.org/10.3847/2041-8213/ad4495)

(ref: Fudamoto22) Fudamoto, Y., Smit, R., Bowler, R. A. A., et al. 2022, ApJ, 934, 144, doi: [`10.3847/1538-4357/ac7a47`](http://doi.org/10.3847/1538-4357/ac7a47)

(ref: Fujimoto20) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1, doi: [`10.3847/1538-4357/ab94b3`](http://doi.org/10.3847/1538-4357/ab94b3)

(ref: Fujimoto23_ceers) Fujimoto, S., Arrabal Haro, P., Dickinson, M., et al. 2023a, ApJL, 949, L25, doi: [`10.3847/2041-8213/acd2d9`](http://doi.org/10.3847/2041-8213/acd2d9)

(ref: Fujimoto23_alma) Fujimoto, S., Finkelstein, S. L., Burgarella, D., et al. 2023b, ApJ, 955, 130, doi: [`10.3847/1538-4357/aceb67`](http://doi.org/10.3847/1538-4357/aceb67)

(ref: Gordon03) Gordon, K. D., Clayton, G. C., Misselt, K. A., Landolt, A. U., & Wolff, M. J. 2003, ApJ, 594, 279, doi: [`10.1086/376774`](http://doi.org/10.1086/376774)

(ref: Hainline24b) Hainline, K. N., D’Eugenio, F., Jakobsen, P., et al. 2024a, arXiv e-prints, arXiv:2404.04325, doi: [`10.48550/arXiv.2404.04325`](http://doi.org/10.48550/arXiv.2404.04325)

(ref: Hainline24a) Hainline, K. N., Johnson, B. D., Robertson, B., et al. 2024b, ApJ, 964, 71, doi: [`10.3847/1538-4357/ad1ee4`](http://doi.org/10.3847/1538-4357/ad1ee4)

(ref: Harikane20) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93, doi: [`10.3847/1538-4357/ab94bd`](http://doi.org/10.3847/1538-4357/ab94bd)

(ref: Harikane23) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, ApJS, 265, 5, doi: [`10.3847/1538-4365/acaaa9`](http://doi.org/10.3847/1538-4365/acaaa9)

(ref: Numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Heintz21) Heintz, K. E., Watson, D., Oesch, P. A., Narayanan, D., & Madden, S. C. 2021, ApJ, 922, 147, doi: [`10.3847/1538-4357/ac2231`](http://doi.org/10.3847/1538-4357/ac2231)

(ref: Heintz22) Heintz, K. E., Oesch, P. A., Aravena, M., et al. 2022, ApJL, 934, L27, doi: [`10.3847/2041-8213/ac8057`](http://doi.org/10.3847/2041-8213/ac8057)

(ref: Heintz23_JWSTALMA) Heintz, K. E., Giménez-Arteaga, C., Fujimoto, S., et al. 2023a, ApJL, 944, L30, doi: [`10.3847/2041-8213/acb2cf`](http://doi.org/10.3847/2041-8213/acb2cf)

(ref: Heintz23_mz) Heintz, K. E., Shapley, A. E., Sanders, R. L., et al. 2023b, A&A, 678, A30, doi: [`10.1051/0004-6361/202346573`](http://doi.org/10.1051/0004-6361/202346573)

(ref: Heintz23_GRB) Heintz, K. E., De Cia, A., Thöne, C. C., et al. 2023c, A&A, 679, A91, doi: [`10.1051/0004-6361/202347418`](http://doi.org/10.1051/0004-6361/202347418)

(ref: Heintz24_DLA) Heintz, K. E., Watson, D., Brammer, G., et al. 2024a, Science, 384, 890, doi: [`10.1126/science.adj0343`](http://doi.org/10.1126/science.adj0343)

(ref: Heintz24_z54) Heintz, K. E., Bennett, J. S., Oesch, P. A., et al. 2024b, arXiv e-prints, arXiv:2407.06287, doi: [`10.48550/arXiv.2407.06287`](http://doi.org/10.48550/arXiv.2407.06287)

(ref: Heintz25) Heintz, K. E., Brammer, G. B., Watson, D., et al. 2025, A&A, 693, A60, doi: [`10.1051/0004-6361/202450243`](http://doi.org/10.1051/0004-6361/202450243)

(ref: Helton24) Helton, J. M., Rieke, G. H., Alberts, S., et al. 2024, arXiv e-prints, arXiv:2405.18462, doi: [`10.48550/arXiv.2405.18462`](http://doi.org/10.48550/arXiv.2405.18462)

(ref: HerreraCamus21) Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649, A31, doi: [`10.1051/0004-6361/202039704`](http://doi.org/10.1051/0004-6361/202039704)

(ref: Hsiao24a) Hsiao, T. Y.-Y., Abdurro’uf, Coe, D., et al. 2024a, ApJ, 973, 8, doi: [`10.3847/1538-4357/ad5da8`](http://doi.org/10.3847/1538-4357/ad5da8)

(ref: Hsiao24b) Hsiao, T. Y.-Y., Álvarez-Márquez, J., Coe, D., et al. 2024b, ApJ, 973, 81, doi: [`10.3847/1538-4357/ad6562`](http://doi.org/10.3847/1538-4357/ad6562)

(ref: Huberty25) Huberty, M., Scarlata, C., Hayes, M. J., & Gazagnes, S. 2025, arXiv e-prints, arXiv:2501.13899, doi: [`10.48550/arXiv.2501.13899`](http://doi.org/10.48550/arXiv.2501.13899)

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Inoue14) Inoue, A. K., Shimizu, I., Iwata, I., & Tanaka, M. 2014, MNRAS, 442, 1805, doi: [`10.1093/mnras/stu936`](http://doi.org/10.1093/mnras/stu936)

(ref: Jakobsen22) Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80, doi: [`10.1051/0004-6361/202142663`](http://doi.org/10.1051/0004-6361/202142663)

(ref: Johnson21) Johnson, B. D., Leja, J., Conroy, C., & Speagle, J. S. 2021, ApJS, 254, 22, doi: [`10.3847/1538-4365/abef67`](http://doi.org/10.3847/1538-4365/abef67)

(ref: TJones23) Jones, T., Sanders, R., Chen, Y., et al. 2023, ApJL, 951, L17, doi: [`10.3847/2041-8213/acd938`](http://doi.org/10.3847/2041-8213/acd938)

(ref: Katz22) Katz, H., Rosdahl, J., Kimm, T., et al. 2022, MNRAS, 510, 5603, doi: [`10.1093/mnras/stac028`](http://doi.org/10.1093/mnras/stac028)

(ref: Katz25) Katz, H., Cameron, A. J., Saxena, A., et al. 2024, arXiv e-prints, arXiv:2408.03189, doi: [`10.48550/arXiv.2408.03189`](http://doi.org/10.48550/arXiv.2408.03189)

(ref: Kennicutt12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Kokorev24) Kokorev, V., Atek, H., Chisholm, J., et al. 2024, arXiv e-prints, arXiv:2411.13640, doi: [`10.48550/arXiv.2411.13640`](http://doi.org/10.48550/arXiv.2411.13640)

(ref: Konstantopoulou24) Konstantopoulou, C., De Cia, A., Ledoux, C., et al. 2024, A&A, 681, A64, doi: [`10.1051/0004-6361/202347171`](http://doi.org/10.1051/0004-6361/202347171)

(ref: Madden93) Madden, S. C., Geis, N., Genzel, R., et al. 1993, ApJ, 407, 579, doi: [`10.1086/172539`](http://doi.org/10.1086/172539)

(ref: MiraldaEscude98) Miralda-Escudé, J. 1998, ApJ, 501, 15, doi: [`10.1086/305799`](http://doi.org/10.1086/305799)

(ref: Moseley10) Moseley, S. H., Arendt, R. G., Fixsen, D. J., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7742, High Energy, Optical, and Infrared Detectors for Astronomy IV, ed. A. D. Holland & D. A. Dorn, 77421B, doi: [`10.1117/12.866773`](http://doi.org/10.1117/12.866773)

(ref: Naidu22) Naidu, R. P., Oesch, P. A., Setton, D. J., et al. 2022, arXiv e-prints, arXiv:2208.02794, doi: [`10.48550/arXiv.2208.02794`](http://doi.org/10.48550/arXiv.2208.02794)

(ref: Nicholls17) Nicholls, D. C., Sutherland, R. S., Dopita, M. A., Kewley, L. J., & Groves, B. A. 2017, MNRAS, 466, 4403, doi: [`10.1093/mnras/stw3235`](http://doi.org/10.1093/mnras/stw3235)

(ref: Oesch23) Oesch, P. A., Brammer, G., Naidu, R. P., et al. 2023, MNRAS, 525, 2864, doi: [`10.1093/mnras/stad2411`](http://doi.org/10.1093/mnras/stad2411)

(ref: Olsen17) Olsen, K., Greve, T. R., Narayanan, D., et al. 2017, ApJ, 846, 105, doi: [`10.3847/1538-4357/aa86b4`](http://doi.org/10.3847/1538-4357/aa86b4)

(ref: Planck18) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6, doi: [`10.1051/0004-6361/201833910`](http://doi.org/10.1051/0004-6361/201833910)

(ref: Rauscher17) Rauscher, B. J., Arendt, R. G., Fixsen, D. J., et al. 2017, PASP, 129, 105003, doi: [`10.1088/1538-3873/aa83fd`](http://doi.org/10.1088/1538-3873/aa83fd)

(ref: Rieke23) Rieke, M. J., Robertson, B., Tacchella, S., et al. 2023, ApJS, 269, 16, doi: [`10.3847/1538-4365/acf44d`](http://doi.org/10.3847/1538-4365/acf44d)

(ref: Robertson24) Robertson, B., Johnson, B. D., Tacchella, S., et al. 2024, ApJ, 970, 31, doi: [`10.3847/1538-4357/ad463d`](http://doi.org/10.3847/1538-4357/ad463d)

(ref: Robertson22) Robertson, B. E. 2022, ARA&A, 60, 121, doi: [`10.1146/annurev-astro-120221-044656`](http://doi.org/10.1146/annurev-astro-120221-044656)

(ref: Schirmer16) Schirmer, M. 2016, PASP, 128, 114001, doi: [`10.1088/1538-3873/128/969/114001`](http://doi.org/10.1088/1538-3873/128/969/114001)

(ref: Schouws24) Schouws, S., Bouwens, R. J., Ormerod, K., et al. 2024, arXiv e-prints, arXiv:2409.20549, doi: [`10.48550/arXiv.2409.20549`](http://doi.org/10.48550/arXiv.2409.20549)

(ref: Schouws25) Schouws, S., Bouwens, R. J., Algera, H., et al. 2025, arXiv e-prints, arXiv:2502.01610. [`https://arxiv.org/abs/2502.01610`](https://arxiv.org/abs/2502.01610)

(ref: Speagle20) Speagle, J. S. 2020, MNRAS, 493, 3132, doi: [`10.1093/mnras/staa278`](http://doi.org/10.1093/mnras/staa278)

(ref: TepperGarcia06) Tepper-Garcı́a, T. 2006, MNRAS, 369, 2025, doi: [`10.1111/j.1365-2966.2006.10450.x`](http://doi.org/10.1111/j.1365-2966.2006.10450.x)

(ref: Umeda23) Umeda, H., Ouchi, M., Nakajima, K., et al. 2023, arXiv e-prints, arXiv:2306.00487, doi: [`10.48550/arXiv.2306.00487`](http://doi.org/10.48550/arXiv.2306.00487)

(ref: Watson11) Watson, D. 2011, A&A, 533, A16, doi: [`10.1051/0004-6361/201117120`](http://doi.org/10.1051/0004-6361/201117120)

(ref: Whitler25) Whitler, L., Stark, D. P., Topping, M. W., et al. 2025, arXiv e-prints, arXiv:2501.00984, doi: [`10.48550/arXiv.2501.00984`](http://doi.org/10.48550/arXiv.2501.00984)

(ref: Witstok24) Witstok, J., Jakobsen, P., Maiolino, R., et al. 2024, arXiv e-prints, arXiv:2408.16608, doi: [`10.48550/arXiv.2408.16608`](http://doi.org/10.48550/arXiv.2408.16608)

(ref: Zavala24) Zavala, J. A., Bakx, T., Mitsuhashi, I., et al. 2024, ApJL, 977, L9, doi: [`10.3847/2041-8213/ad8f38`](http://doi.org/10.3847/2041-8213/ad8f38)

(ref: Zavala25) Zavala, J. A., Castellano, M., Akins, H. B., et al. 2025, Nature Astronomy, 9, 155, doi: [`10.1038/s41550-024-02397-3`](http://doi.org/10.1038/s41550-024-02397-3)

[^1]: Available at <https://doi.org/10.5281/zenodo.12578542>

</paper>

Write the methods card for this paper.