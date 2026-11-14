# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...991L...6T\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...991L...6T",
 "title": "A Radially Resolved Magnetic Field Threading the Disk of TW Hya",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Teague, Richard",
 "n_authors": 8,
 "arxiv_id": "2509.09450",
 "doi": "10.3847/2041-8213/adff4d",
 "alma_projects_linked_by_archive": [
  "2022.1.00840.S"
 ]
}
```

Paper text:
<paper>
# A Radially Resolved Magnetic Field Threading the Disk of TW Hya

## Abstract

We present a new approach to detecting and characterizing a magnetic field in protoplanetary disks through the differential broadening of unpolarized molecular emission from CN. To demonstrate this technique, we apply it to new ALMA observations of the full complement of hyperfine components from the $N=1-0$ transition, achieving a spatial and spectral resolution of ${\approx}0.5\ensuremath{''}$ and $80~{\rm m\,s^{-1}}$, respectively. By fitting a model that incorporates the velocity structure of the disk, the potential non-LTE excitation of the molecule, and the Zeeman effect, we recover a radially resolved magnetic field with a strength of ${\sim}10~{\rm mG}$ between 60 and 120 au. The morphology of the field is also inferred through azimuthal variations in the line broadening, revealing a predominantly poloidal field at 60 au, sharply transitioning to one within the disk plane outside of the gap at 82 au. The signal-to-noise ratio of the data meant that the planar component was unable to be decomposed into toroidal and radial components. Lower limits on the local gas density ($n({\rm H_2}) \gtrsim 10^8~{\rm cm^{-3}}$) from the excitation analysis of the CN emission correspond to a lower limit between 0.1 and 0.01 for the plasma $\beta$.

show\]rteague@mit.edu

# Introduction

Planets form in protoplanetary disks, the remnant gas and dust from the star formation process that settles around the newly formed star. A variety of mechanisms have been proposed to account for the evolution of these systems, facilitating the redistribution of angular momentum, the concentration of gas and dust into regions favorable for planet formation, and the eventual dissipation of the disk (cite: Morbidelli_ea_2024). High angular resolution observations have revealed large-scale perturbations in both the gas and dust of these sources demonstrating their highly active nature (cite: Andrews_2020; Bae_ea_2023).

While purely hydrodynamical (HD) instabilities have shown promise in accounting for this evolution, the highly specific conditions required for such instabilities to grow and sustain themselves argue against these being the dominant mechanisms moderating the evolutionary processes (cite: Lesur_ea_2023). Instead, magneto-hydrodynamical (MHD) instabilities appear to be less sensitive to the range of disk properties if the disk is threaded by a magnetic field making them a more attractive mechanism to explain disk evolution. However, while magnetic fields are commonplace on larger scales earlier in the star formation process (cite: Pattle_ea_2023) and have been indirectly inferred to be present during the formation of our solar system (cite: Weiss_ea_2021), the detection and characterization of magnetic fields threading protoplanetary disks remains a significant observational challenge. Without robust evidence of the presence of magnetic fields threading a protoplanetary disk and a constraint on their morphology, the importance of MHD processes for the evolution of protoplanetary disks remains unconstrained.

Routinely used to trace magnetic fields in star forming regions, continuum polarization detected observed in multiple sources is mostly due to grain alignment mechanisms unrelated to magnetic fields (cite: Tazaki_ea_2017) or the self-scattered of emission (cite: Kataoka_ea_2015). However, there is one recent report of magnetically aligned grains in HD 142527 (cite: Ohashi_ea_2025), where the relative wavelength-independence of the polarization pattern suggested magnetic alignment by a field of ${\sim}~0.3$ mG over a select range of azimuths in the disk.

![](flux_density.pdf)

Searches for polarized molecular line emission have also been conducted. Both (cite: Stephens_ea_2020) and (cite: Teague_ea_2021) report the detection of linearly polarized CO emission in HD 142527 and IM Lup, and TW Hya, respectively, suggesting that the emission is due to the Goldreich-Kylafis effect (cite: Goldreich_Kylafis_1982). While the detection itself signifies the presence of a magnetic field, the GK effect is insensitive to the magnetic field strength (above some negligible lower limit) and the averaging and stacking of the data required to pull out the detections removes any sensitivity to the field morphology.

Attempts to detect the circular polarization of molecular emission due to the Zeeman effect were also carried out, however they yielded only upper limits in both TW Hya and AS 209 (cite: Vlemmings_ea_2019; Harrison_ea_2021). Similar to the linearly polarized emission, the unresolved highly structured emission morphology (cite: Mazzei_ea_2020) and cancellation of the polarization signal from the back side of the disk (cite: Lankhaar_Teague_2023) likely contributed to the non-detections. The high angular resolution and deep observations that these works suggest are necessary to detect circular polarization results in prohibitively long programs which would be exceedingly challenging to schedule. Alternative, less costly methodologies are needed.

In this paper, we present and apply such a technique to CN emission from the disk around TW Hya. The detection of magnetic fields solely through the broadening of unpolarized molecular emission due to Zeeman splitting bypasses the need for polarized emission and benefits from the improved schedulability of low frequency programs. We describe the observations and data reduction in Section [2](#sec:observations), the modeling methodology in Section [3](#sec:methodology) and results in Section [4](#sec:results). A discussion of these results and their implications are provided in Section [5](#sec:discussion), with Section [6](#sec:conclusions) providing a summary of the findings.

# Observations

The data from project 2022.1.00840.S (P.I. Teague) comprise ten execution blocks (EBs) observed between 7 January 2023 and 12 May 2023, using between 41 and 44 antennas, for a total on-source integration time of 670 minutes. Projected baselines ranged from 15.3 to 2516.8 m, and the maximum recoverable scale (MRS) was 12.2$''$, with a typical precipitable water vapor (PWV) range of 1.4-5.5 mm. Three spectral windows covered multiple CN $N=1-0$ transitions from 113.123 to 113.520 GHz, with a spectral resolution of 80 m s$^{-1}$.

All individual EBs were first re-aligned to a common disk center, determined based on a Gaussian fit to the continuum emission, using the `phaseshift` and `fixplanets` tasks. We then performed three rounds of phase-only self-calibration on the short-baseline (SB) data with solution intervals (`solint`) of `inf`, 360 s, and 90 s), followed by one round of amplitude self-calibration with `solint` = `inf`. These calibrated SB data were concatenated with the long-baseline (LB) observations, after which two rounds of phase-only self-calibration (`solint` = `inf`, 360 s) and one round of ampltitude self-calibration (`solint` = `inf`) were applied.

This calibration yielded an improvement of approximately 4$\times$ in the peak continuum SNR. The final calibration tables were then applied to the aligned line visibilities.

We adopt a $80~{\rm m\,s^{-1}}$ channel spacing, the FWHM spectral resolution of the data, and a `robust` value of 1 for the final imaging run, CLEANing down to a threshold of $3\sigma$. These parameters result in a median beam size of $0.53\ensuremath{''} \times 0.42\ensuremath{''}$ with a position angle of $105\ensuremath{^\circ}$, and a per channel sensitivity of $1.8~{\rm mJy~beam^{-1}}$ (0.76 K).

Flux densities for all nine hyperfine components are shown in Figure [1](#fig:flux_density) which were calculated by spatially integrating a circulate aperture with a radius of 4$''$ (240 au) in each channel using `GoFish` (cite: GoFish). Below each line the $w$ value represents the relative sensitivity to Zeeman splitting, measured as the product of $Z$ and $\bar{Q}$, where $Z$ is the line-specific Zeeman coefficient and $\bar{Q}$ quantifies the contribution of the intra-group broadening to the total Zeeman broadening, as defined in (cite: Lankhaar_Teague_2023). Note that the brightest components do not necessarily correspond to the components most sensitive to the Zeeman splitting. The total integrated flux for the $N=1-0$ transition is $4.38 \pm 0.04~{\rm Jy~km\,s^{-1}}$ with integrated fluxes for individual hyperfine components given in Table [1](#tab:observations).

# Methodology

In this section we describe the modeling methodology employed to infer the magnetic field strength and morphology. This builds on excitation analyses described in many previous works, such as (cite: Teague_ea_2016) and (cite: Teague_ea_2018c), but with the addition of the Zeeman splitting of the lines.

## Excitation Analysis

At its core, this approach models the observed spectrum using the `SpectralRadex` (cite: SpectralRadex) implementation of `RADEX` (cite: vanderTak_ea_2007) with the collision rates from (cite: Kaligina_Lique_2015) to calculate the optical depth of each hyperfine component given a kinetic temperature, $T_{\rm kin}$, a column density of CN, $N({\rm CN})$, a local collider density, dominated by H$_2$ molecules, $n({\rm H_2})$, and non-thermal contribution to the line width, $\Delta V_{\rm nt}$. This model makes the implicit assumption that the emitting region can be well represented by a geometrically thin, isothermal slab. For the face-on case of TW Hya, where no vertical extent can be observed, this has been shown to be an appropriate assumption and has been successfully used to reproduce a range of spectral observations (cite: Teague_ea_2018c; Romero-Mirza_ea_2023).

Importantly, this approach accounts for both LTE and non-LTE solutions (cite: Teague_Loomis_2020). Following (cite: Cataldi_ea_2021), we account for any systematic broadening, such as instrumental broadening or due to unresolved Keplerian shear, by convolving the resulting spectrum with a Gaussian kernel with a FWHM that was allowed to vary, ${\rm FWHM_{conv}}$. To differentiate between non-thermal broadening (which would affect the optical depth profile) and instrumental broadening (which acts on the intensity profile) we include a Gaussian prior on $\Delta V_{\rm nt}$ centered on zero with a standard deviation of $0.08~c_s$ following the upper limits reported in (cite: Flaherty_ea_2018).

A single pixel does not contain sufficient signal to robustly identify the influence of a magnetic fields on the line profile. So instead, we simultaneously fit annuli of spatially independent pixels (i.e., pixels that are separated by at least a beam FWHM). The assumption here is that the disk is azimuthally symmetric such that the line profiles vary only in their centers due to the projection of the disk velocity structure. Previous works, such as (cite: Teague_ea_2016), aligned and stacked these spectra prior to the fitting, following the now standard ‘shift-and-stack’ approach described in (cite: Yen_ea_2016). In order to incorporate the uncertainties associated with this process, we opt to instead shift our model spectra to the appropriate reference frame through

$$\begin{equation}
    v_0(r,\,\phi) = v_{\phi,\,\rm proj}(r,\,\phi) + v_{r,\,\rm proj}(r,\,\phi) + v_{z,\,\rm proj}(r,\,\phi) + v_{\rm LSR}
\end{equation}$$

where $v_{\phi,\,\rm proj}$, $v_{r,\,\rm proj}$ and $v_{z,\,\rm proj}$ are the azimuthally symmetric rotational, radial, and vertical velocity fields projected along the line of sight. These can be decomposed into their disk-frame components as

$$\begin{align}
    v_{\phi,\,\rm proj}(r,\,\phi) &= +v_{\phi}(r) \cos(\phi)\sin(|i|),\\
    v_{r,\,\rm proj}(r,\,\phi) &= -v_{r}(r) \sin(\phi)\sin(i)\\
    v_{z,\,\rm proj}(r,\,\phi) &= -v_{z}(r) \cos(i)
\end{align}$$

where $\phi$ is the polar angle in the disk frame and $i$ is the disk inclination. Note that the sign of $i$ is chosen here to encode the rotation direction of the disk, with positive values indicating clockwise rotation on the sky and negative values indicating counter-clockwise rotation. Assuming that the large spiral arm found in TW Hya is trailing (cite: Teague_ea_2022) would imply that the disk is rotating in a clockwise direction and thus the $i$ in this parameterization is positive. Following (cite: Teague_ea_2022), a source inclination and position angle of $+5.8\ensuremath{^\circ}$ and $151.6\ensuremath{^\circ}$ were adopted and used to calculate each annulus.

## Zeeman Splitting

![](zeeman_splitting_demonstration.pdf)

Rather than adopt a Gaussian optical depth profile for each hyperfine component, we implement the Zeeman splitting model presented in (cite: Lankhaar_Teague_2023). We represent the line profile of the CN transitions as a sum, weighted by the relative line strength, over all allowed transitions between the magnetic substates of the hyperfine levels. The energies associated with the magnetic substates are shifted with respect to the zero-field energy in proportion to the magnetic field strength, $|\mathbf{B}|$, the level-specific $g$-factor, the statistical weight of the level, and the associated magnetic quantum number $m$. The adopted molecular parameters are described in Table [1](#tab:observations). Figure [2](#fig:zeeman_splitting_demonstration) demonstrates how the magnetic subtransition groups are influenced by a magnetic field, resulting in a broadened line profile. Note that at field strengths larger than the 15 mG used for Figure [2](#fig:zeeman_splitting_demonstration), the splitting is significant enough that the resulting line profile is poorly reproduced with a single Gaussian profile. At the typical magnetic field strengths expected in the outer regions of protoplanetary disks, on the order of 1 – 10 mG, the Zeeman split lines still maintain a close-to-Gaussian morphology, as discussed more in Appendix [9.2](#sec:app:model:zeeman).

Figure [2](#fig:zeeman_splitting_demonstration) also highlights how the projection of the magnetic field along the line of sight changes the resulting profile. When aligned with the line of sight, $\theta = 0\ensuremath{^\circ}$, only the $\sigma^{\pm}$ transitions populate. With a progressively more perpendicular field, $\theta$ approaches $90\ensuremath{^\circ}$, the $\pi^0$ transitions starts to dominate. As only the $\sigma^{\pm}$ transition groups are shifted relative to the true line center, broadening is more significant when the magnetic field is preferentially aligned with the line of sight.

The final component of the model was a magnetic field prescription. As the magnitude of the Zeeman splitting is sensitive to $1 + \cos^2(\theta)$, where $\theta$ is the angle between the magnetic field vector and the line of sight (cite: Lankhaar_Teague_2023), we explore two scenarios: one where $\theta$ is constant around the annulus, as would be the case for some large-scale, external field, and one where $\theta$ is able to vary as a function of $\phi$ in a manner which can be recast as an azimuthally symmetric disk-centric field described by $(B_{\phi},\, B_r,\, B_z)$.

These two scenarios are described by $|\mathbf{B}|$, the magnetic field strength, $\theta_B$, the azimuthally averaged $\theta$ value, and, for the disk-centric case, $\phi_B$, the mixing angle between toroidal and radial magnetic fields. For the latter case, these can be recast to describe the disk-centric components,

$$\begin{align}
    B_{\phi} &= |\mathbf{B}| \sin(\theta_B) \cos (\phi_B),\\
    B_r      &= |\mathbf{B}| \sin(\theta_B) \sin (\phi_B),\\
    B_z      &= |\mathbf{B}| \cos(\theta_B),
\end{align}$$

where all values are implicitly dependent on radius and from which $\theta$ can be calculated for any position around the annulus:

$$\begin{equation}
    |\mathbf{B}|\cos\big(\theta(\phi)\big) = B_{\phi} \cos(\phi) \sin(|i|) - B_{r} \sin(\phi) \sin(i) - B_z \cos(i) .
\end{equation}$$

This seemingly more complex parameterization was chosen over modeling $(B_{\phi},\, B_r,\, B_z)$ directly, as uniform priors in these parameters results in non-uniform priors for $|\mathbf{B}|$ and $\theta_B$, that, most importantly, favor non-zero magnetic field strengths. The additional benefit is that the inferred posteriors for $|\mathbf{B}|$ and $\theta_B$ can be directly compared between the two field morphologies.

In total, the model contains either nine or ten free parameters: three describing the azimuthally symmetric velocity structure of the disk, $v_{\phi}$, $v_r$, and $v_z$; four describing the excitation conditions of the line, $T_{\rm kin}$, $N({\rm CN})$, $n({\rm H_2})$, and $\Delta V_{\rm nt}$; either two or three describing the magnetic field, $(|\mathbf{B}|,\, \theta_B,\, \phi_B)$, and one describing the width of the convolution kernel, ${\rm FWHM_{conv}}$.

With this model, we implicitly ignore the impact of continuum opacity, motivated by two reasons. Firstly, with an angular resolution of ${\approx}~0.45\ensuremath{''}$, the observations used here are minimally affected by convolution effects beyond ${\approx}~0.9\ensuremath{''}$ and so the analysis will necessarily focus on those regions of the disk. At these radii, (cite: Macias_ea_2021) estimates the 3.1 mm continuum optical depth to be $\lesssim 0.1$, suggesting that effects from the continuum will be negligible. Secondly, (cite: Lankhaar_Teague_2023) argued that while continuum opacity would suppress polarized emission, it would only marginally impact the broadening of unpolarized emission. This is because the continuum subtraction effect is wavelength independent, at least across the bandwidths needed for excitation analyses, and so would not result in a changing of the line width ratios.

## MCMC Sampling

An exploration of the parameter posterior distributions was performed with the MCMC package `emcee` (cite: emcee) utilizing 128 walkers which took 20,000 steps using the default `StretchMove` move. The median autocorrelation time of all parameters, $\langle \tau \rangle$, was estimated to be ${\sim}200$. As such, $20\langle \tau \rangle$ samples were removed as burn-in steps with the remaining samples representing the posterior distributions. To create the radial profiles, annuli were extracted every $0.1\ensuremath{''}$, roughly a fifth of the beam major axis, with a width of one pixel, $0.05\ensuremath{''}$, between $0.4\ensuremath{''}$ and $4\ensuremath{''}$ from the star. The narrow annuli are necessary to reduce the impact of Keplerian shear across the annulus width that would introduce significant non-thermal broadening at a level that ranges between ${\sim}~100~{\rm m\,s^{-1}}$ at $1\ensuremath{''}$ down to ${\sim}~10~{\rm m\,s^{-1}}$ at 3$''$ (cite: Teague_Loomis_2020). All parameters assumed uniform priors over some broad range of possible values, except the non-thermal broadening contribution which was chosen to have a Gaussian prior centered on zero with a width of $0.08~c_s$ based on the upper limits reported in (cite: Flaherty_ea_2018).

## Randomized Zeeman Sensitivities

![](model_spectrum.pdf)

Zeeman splitting offers a powerful way to differentiate the broadening due to magnetic fields from other broadening processes, as only certain lines are sensitive to the Zeeman effect. In the model described above, the thermal and non-thermal broadening, as well as the smoothing convolution, will uniformly broaden all hyperfine components. In contrast, increasing the magnetic field strength will broaden certain transitions more than others. To verify that the broadening we detect can be uniquely associated with magnetic-field induced Zeeman splitting, we run two additional ‘randomized’ models for both field morphology scenarios where the Zeeman-specific properties of the most sensitive transitions, $J=3/2 - 1/2$ $F = 3/2 - 1/2$ and $J = 1/2 - 1/2$ $F = 3/2 - 3/2$, are swapped with those of the least sensitive transitions $J=3/2 - 1/2$ $F = 1/2 - 1/2$ and $J=3/2 - 1/2$ $F = 3/2 - 3/2$. The two models represent the two possible pairs of swapping. In this case, the inferred magnetic field should prefer lower values as to not over-broaden the less sensitive, and thus narrower, transitions.

As this approach does not completely remove all sensitivity to magnetic fields, it is not expected that a field strength consistent with zero is recovered. Instead, we should infer a strength that is significantly lower than with the correct molecular properties. To classify the posterior distributions as statistically different, we require that their medians are separated by more than the quadrature sum of their standard deviations. Appendix [9](#sec:app:model) shows the posterior distributions for each radius in each case.

# Results

In this section, we discuss the inferred magnetic field strength, morphology, and limits on the plasma beta. A more comprehensive discussion of the derived velocity profiles and excitations conditions can be found in Appendix [9](#sec:app:model). Figure [3](#fig:model_spectrum) demonstrates the typical quality of fit we are able to achieve with the model. In general, beam smearing will impact the shape of the spectrum in regions inwards of approximately twice the beam FWHM. This effect heavily biases the results interior to ${\approx}~1\ensuremath{''}$ (60 au), so we are cautious over interpretation of the posteriors in this region.

## Field Strength

![](B_theta_radial_profiles.pdf)

The inferred magnetic field strengths and (azimuthally averaged) field orientations are shown in Figure [4](#fig:B_theta_radial_profiles) for the two magnetic field parameterizations. The colored points show radii where the magnetic field strength posteriors of the ‘correct’ Zeeman sensitivities are significantly higher than for the ‘mixed’ Zeeman sensitives. For completeness, we plot posterior distributions for all radii where we were able to obtain a constraint on the gas temperature and CN column density.

Both field morphologies yield a similar radially averaged magnetic field strength of $9 \pm 2$ mG and $8 \pm 2$ mG for the disk-centric model and for the environmental field, respectively. Both models also recover a comparable radial profile for the magnetic field strength: a negligible field within the inner $1\ensuremath{''}$ (60 au) and beyond ${\sim}~2.5\ensuremath{''}$ (150 au), and a highly significant, $|\mathbf{B}| \, / \,\delta|\mathbf{B}| \gtrsim 5$, where $\delta|\mathbf{B}|$ is the uncertainty on $|\mathbf{B}|$, detection of a ${\sim}~10~{\rm mG}$ ($1~\mu{\rm T}$) field between $1$ and $2.5\ensuremath{''}$. For the disk-centric case, a magnetic field is also detected at $3.2\ensuremath{''}$ (190 au) with a ${\sim}~12$ mG field strength, however such a field is not found for the environmental scenario. Interestingly, the magnetic field strength appears to peak at the location of a gap observed in scattered light, thermal continuum, and molecular line emission at $1.37\ensuremath{''}$ (cite: vanBoekel_ea_2017; Ilee_ea_2022; Teague_ea_2017), which will be discussed further in Section [5.1](#sec:discussion:field_morphology).

## Field Orientation

![](B_covariances.pdf)

The inferred field morphologies are also consistent between the two assumed morphologies, in so far as the data has little constraining power for this parameter. The bottom row of Fig. [4](#fig:B_theta_radial_profiles) shows the posterior distributions for $\theta_B$, the azimuthally averaged value of $\theta$. Note that for the disk-centric model, $\theta$ varies as a function of annulus, while for the environmental model, $\theta$ is constant as a function of azimuth. In both cases, a predominantly poloidal field is inferred interior to the gap center at $1.37\ensuremath{''}$, which rapidly transitions to one within the plane of the disk at larger radii. Beyond $1.8\ensuremath{''}$ (110 au), the data is insufficient to constrain $\theta_B$ (with the posterior distributions matching the uniform priors), except at $3.2\ensuremath{''}$, where the disk-centric model recovers a magnetic field and an in-plane field is inferred.

In the disk-centric model, $\phi_B$, the mixing angle between the $B_{\phi}$ and $B_r$ components, was an additional free parameter. At no radius in the disk was a constraint on this parameter inferred. The modeled posterior distributions are entirely consistent the uniform prior distribution which spanned $0\ensuremath{^\circ}$ to $360\ensuremath{^\circ}$. Figure [5](#fig:B_covariances) demonstrates this by plotting the covariances between $\theta_B$ and $\phi_B$ for five radial bins where the magnetic field was robustly detected. It is clear that there is a steady transition from $\theta_B \lesssim 30\ensuremath{^\circ}$ at $1.2\ensuremath{''}$ to $\theta_B \gtrsim 60\ensuremath{^\circ}$ at $1.6\ensuremath{''}$, while at each radius $\phi_B$ is completely unconstrained. This suggests that either the data sensitivity and/or spectral resolution is insufficient to tease out this subtle variation in broadening or that there is no variation in $\theta$ as a function of $\phi$. The interpretation of this in terms of a global field morphology is discussed in Section [5.1](#sec:discussion:field_morphology).

## Plasma $\beta$

The excitation analysis also provides an opportunity to derive a radially resolved plasma $\beta$ value, the ratio of the thermal to magnetic pressure, from where the CN emission arises. The thermal pressure was calculated assuming an ideal gas with a temperature set to the inferred $T_{\rm kin}$ and a gas density given by the $n({\rm H_2})$ collider density. As discussed in Appendix [9](#sec:app:model), the data favored an LTE solution at all radii, which results only in lower limits of the gas density and, in turn, the derived plasma $\beta$. The magnetic pressure is given by $|\mathbf{B}|^2 \, / \, 8\pi$ (cite: Lesur_ea_2023).

The resulting $\beta(r)$ radial profiles are shown in Fig. [6](#fig:plasma_beta) where, the median of the parameter distribution was chosen as the plotted lower limit, and semi-transparent points mark where the inferred broadening cannot be robustly attributed to Zeeman splitting. Both field morphologies yield similar limits, with $\beta$ ranging between ${\gtrsim}0.1$ in the inner disk and values as low as ${\sim}0.01$ at the disk edge, albeit with increased scatter. It is important to note that these values are *not* for the midplane, but rather from the CN emission layer. Based on the gas kinetic temperature, discussed in Appendix [9](#sec:app:model), emission interior to $2.5\ensuremath{''}$ (150 au) traces regions that are warmer than 10 K (up to 30 K in the inner disk regions), so likely substantially above the midplane. Indeed, for the case of IM Lup, (cite: Paneque-Carreno_ea_2024) report CN $N=3-2$ emission arising from a region that is ${\sim}~0.2r$ above the midplane. Beyond this region, the recovered kinetic temperature plateaus at 10 K, potentially signaling a region closer to the disk midplane; however, given the quality of the signal at these extended radii, this should be taken with caution.

![](plasma_beta.pdf)

# Discussion

## Global Magnetic Field Morphology

Two different field morphologies were invoked to explain the observations: a disk-centric field which could be decomposed into azimuthally symmetric components $(B_{\phi},\, B_r,\, B_z)$, such that $\theta$ varied across the surface of the disk; and a large-scale environmental field, where $\theta$ was assumed to be constant as a function of azimuth. As both morphologies were able to equally well explain the data, and recovered similar field strengths and (azimuthally averaged) angles between the line of sight and the magnetic field vector, neither is clearly favored.

For the disk-centric morphology, the model was flexible enough to allow toroidal and radial magnetic field components (with most models predicting strong toroidal components close to the disk midplane; (cite: Flock_ea_2015)). However, as demonstrated in Figure [5](#fig:B_covariances), no distinction was possible. This could be due to two different issues. Firstly, the data could be too noisy to identify the subtle azimuthal variations in broadening that would allow the distinction between $B_{\phi}$ and $B_r$ components. The azimuthal variations in $\theta$ that arise due to the changing projection of $B_{\phi}$ and $B_r$ components are only ${\sim}10\ensuremath{^\circ}$, much lower than the typical width of the posterior on $\theta_B$, around ${\sim}30\ensuremath{^\circ}$, suggesting that this is likely. Note that in more moderately inclined sources, this variation will be larger, in principle making the distinction easier, however in practice the added complications of contamination from the bottom surfaces will be the limiting factor (cite: Izquierdo_ea_2025).

A second possibility is that we are instead tracing a large-scale environmental field, which should have an azimuthally constant $\theta$ that results in a azimuthally varying $\phi_B$. In this scenario, it would be expected that, as the annuli are symmetric about the star, both the field strength and $\theta$ are constant as a function of radius (the magnetic field should not know about the orientation and position of the disk). While the magnetic field strength could plausibly be argued to be constant as a function of radius given the large error bars, there is a clear variation in the morphology of the field. A scenario in which the gapped disk structure perturbs the environmental field and alters its morphology (cite: Riols_Lesur_2019) could account for this, however deeper observations that are able to constrain the magnetic field strength and orientation across a larger radial range would be necessary to truly determine the global field morphology.

## Comparisons with Previous Studies

There have been many attempts to detect magnetic fields in protoplanetary disks. These can broadly be split between those searching for polarized continuum emission arising due to magnetic grain alignment, and those attempting to detect linear polarized molecular emission from with the Goldreich Kylafis effect (cite: Goldreich_Kylafis_1982) or the circular polarized emission from Zeeman splitting.

Thus far, there has only been one claimed detection of a magnetic field in a protoplanetary disk. (cite: Ohashi_ea_2025) report the presence of a primarily toroidal magnetic field threading the disk around HD 142527. Based on the coherence of the morphology of the polarization, the authors argued that magnetic grain alignment was the dominant polarization mechanism and recovered a field strength of ${\sim}0.3$ mG at a distance of ${\sim}200$ au when comparing the inferred magnetic field morphology to specific MHD predictions. This field is considerably weaker than the field reported here, by almost two orders-of-magnitude. When assuming a local gas density of $6.6 \times 10^{-16}~{\rm g\,cm^{-3}}$, around the same value as the lower limit we recover for TW Hya, the authors find a plasma $\beta$ of ${\sim}200$ resulting in $\alpha$ values of ${\sim}10^{-3}$, broadly consistent with typical levels of turbulence found via non-thermal broadening (cite: Flaherty_ea_2020) or the vertical extent of dust rings (cite: Doi_ea_2023). It should be noted, however, that the $\beta$ derived here would be representative of the vertical region from which CN emanates, while that reported in (cite: Ohashi_ea_2025) will be describing the midplane. As described in Appendix [9.1](#sec:app:model:excitation), the excitation conditions are suggestive of a vertical region between $z \, / \, r \sim 0.2$ – 0.3, consistent with the findings of (cite: Teague_Loomis_2020) and (cite: Yoshida_ea_2024).

HD 142527 also exhibited some level of polarized CO emission after (cite: Stephens_ea_2020) followed a ‘shift-and-stack’ process to uncover a marginal detection. Intriguingly, their Figure A5 shows that $^{13}$CO shows a strong polarized signal peaking at the location where (cite: Ohashi_ea_2025) found evidence of magnetic grain alignment. Unfortunately the GK effect is not sensitive to the magnetic field strength, and any sensitivity to the field morphology, which would need extensive numerical modeling to interpret, was removed due to the shift-and-stack analysis. Nonetheless, the presence of linearly polarized molecular emission coincident with regions where magnetic grain alignment is found to be the dominant polarization mechanism strongly suggest that even marginal detections of polarized molecular emission can signal a magnetic field.

For the case of TW Hya, (cite: Vlemmings_ea_2019) placed tight upper limits on the level of circularly polarized emission from CN. Despite a robust detection of the unpolarized emission, no polarized emission was found: the authors converted those results to a $1\sigma$ upper limit on the magnetic field strength in the disk of $|B_z| \leq 0.8~{\rm mG}$ or $B_{\phi} \leq 30~{\rm mG}$. While the toroidal limits are consistent with the results presented here, the poloidal field limits are over an order-of-magnitude weaker than what is inferred around $1.2\ensuremath{''}$ based on the Zeeman broadening (where $|B_z| \sim 11~{\rm mG}$). It is impossible to definitively determine why circular polarization was not detected, however it is likely that cancellation of the polarized signal, and not the broadening signal, is the most likely culprit. Cancellation can be intrinsic to the source or due to the chosen observational setup. If there is a change in the magnetic field morphology along the path traced by the emission, then alternating field orientations can result in cancellation. This can happen at the very local level, with a highly tangled or turbulent magnetic field (cite: Hughes_ea_2009), or due to large, disk-wide variations, such as the flip in direction either side of the disk midplane if a toroidal field dominates (cite: Lankhaar_Teague_2023). If polarized emission does escape from the disk, then it will exhibit a highly structured morphology (cite: Mazzei_ea_2020). Without sufficient angular resolution to spatially resolve these substructures, the signal will be averaged over and lie undetected. If a circular polarization is able to be detected, potentially with low frequency, high angular resolution observations to remove the continuum absorption and spatial cancellation, then the relative importance of these effects can be constrained.

However, linearly polarized molecular emission has been reported for TW Hya: (cite: Teague_ea_2021) found low-level linearly polarized emission from $^{12}$CO and $^{13}$CO between $0.5\ensuremath{''}$ and $1\ensuremath{''}$ which would require the presence of a (very weak) magnetic field in order for the GK effect to work. As for the case of HD 142527, the shift-and-stack methodology removes any information about the magnetic field structure. As these works have shown, prior assumptions about the field morphology are needed in order to tease out the weak polarized signals. A re-analysis of these datasets with a prior model of the underlying magnetic field based on the results presented here would offer an opportunity to test our understanding of polarized radiative transfer and whether the limits based on the lack of circular emission should be reevaluated.

## Comparison with the Young Solar System

The inferred magnetic field strengths presented here can be compared to those from paleomagnetic measurements of meteorites from the early solar system and to expectations from MHD simulations of protoplanetary disks. Most paleomagnetically studied meteorites likely originate from the innermost ${\sim}10$ au of the solar system (cite: Sutton_ea_2017) and none are thought to sample distances ${\gtrsim}50$ au, precluding direct comparison with the results here. However, meteorite-inferred magnetic fields are relevant in three ways. First, magnetic field strengths between 10 and 1000 mG recorded by meteorites likely sampling the 2–7 au region broadly support the importance of magnetic field-driven radial transport, which predicts magnetic field of order 10–100 mG in this region (cite: Wardle_2007; Bai_2015). Second, these models, which are derived by relating the magnetic torque to the observed inward disk accretion rate, would predict magnetic fields of order 1 mG at 60 au, assuming a $2.5 \times 10 ^{-9}$ $M_\odot \, {\rm yr}^{-1}$ accretion rate (cite: Herczeg_ea_2023). These predictions are supported by inferences of weak fields, typically upper limits of ${\lesssim}0.1~\mathrm{G}$, from paleomagnetic studies of the most distantly sourced (${\gtrsim}7~\mathrm{au}$) material (cite: Mansbach_ea_2025). The ${\sim}10$ mG field inferred here is ${\sim}10\,{\times}$ stronger than those predicted by these models, which may indicate local magnetic field amplification processes, such as spontaneous zonal field concentration (cite: Suriano_ea_2018), unrelated to large-scale radial transport.

This leads to the third inference from solar system meteorites, which have provided evidence for the persistence of strong magnetic field ($\geq 1000$ mG) zones in the otherwise weakly magnetized carbonaceous chondrite-formation regions (cite: Fu_ea_2021; Borlina_ea_2021). If hypothesized magnetic field enhancement mechanisms (cite: Suriano_ea_2018; Riols_Lesur_2019) can result in the ${\sim}100{\times}$ increase in local magnetic fields in the solar system, they would be sufficient for producing 10 mG fields observed in TW Hya, assuming they can operate at such large radii and low density, high-ionization conditions.

## Future Outlook

The implementation of the Wideband Sensitivity Upgrade (cite: Carpenter_ea_2023) for ALMA will facilitate extremely high spectral resolution observations with the default spectral resolution dropping to 13.5 kHz ($36~{\rm m\,s^{-1}}$ at the 113 GHz of the ground-state CN transition), and ‘zoom’ modes offering even finer resolutions. This improvement will bring huge power through the enhanced sampling of the narrow CN emission and enable even more subtle variations in line width to be discerned. Furthermore, the 2 GHz bandwidth available at this high spectral resolution will provide an opportunity to target multiple Zeeman-sensitive species simultaneously, vastly improving the information content of these data.

While new instrumentation will increase our sensitivity to weaker magnetic fields, a more widespread issue is the contamination of the spectra from emission from the back side of the protoplanetary disk for all sources that are not viewed face on. This has already been acknowledged as an issue when looking at the kinematics of moderately inclined sources (cite: Izquierdo_ea_2025). While not insurmountable, accounting for the 3D nature of the emitting source will require the use of extensive radiative transfer models and the development of techniques able to segment the data into contributions from the top and bottom surfaces.

# Conclusions

We have presented a novel approach to detecting and characterizing magnetic fields through the subtle broadening of molecular emission lines due to Zeeman splitting. Application to observations of CN $N=1-0$ emission from the disk of TW Hya reveal the presence of a ${\sim}10$ mG field between $1\ensuremath{''}$ (60 au) and $2\ensuremath{''}$ (120 au), apparently peaking in strength at the radial location of a well-characterized gap in the disk at ${\sim}80$ au. The data were insufficient to provide tight constraints on the morphology of the field, however the modeling favors a predominantly poloidal field interior to the gap and one that is within the plane of the disk exterior to it. The data were unable to support a decomposition of the in-plane contribution into toroidal and radial components. However, the data were equally well fit with a model that imposed an azimuthally constant $\theta$ highly suggestive of the magnetic environment at these radii being dominated by a large-scale environmental field rather than one generated by dynamos within the star and/or disk. An excitation analysis, yielding lower limits to the gas pressure, and the derived magnetic field strength constraints allowed for strict lower limits on a radially resolved plasma $\beta$ value ranging between $10^{-1}$ and $10^{-2}$. This approach to detecting magnetic fields without the need for polarized emission offers a powerful angle with which to attack the question of the importance of magnetic fields for the formation of planetary systems.

We thank the referee for helpful comments which significantly improved the clarity of the manuscript. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.00840.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory and Green Bank Observatory are facilities of the U.S. National Science Foundation operated under cooperative agreement by Associated Universities, Inc. BL acknowledges support from the Swedish Research Council (VR) under grant number 2021-00339

# Facilities

ALMA

# Software

`CASA` (cite: CASA), `RADEX` (cite: vanderTak_ea_2007), `SpectralRadex` (cite: SpectralRadex), `GoFish` (cite: GoFish)

# Molecular Properties

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $J^{\prime} - J^{\prime\prime}$ | $F^{\prime} - F^{\prime\prime}$ | $\nu_0$ | $A_{\rm ul}$ | $g_{\rm u}$ | $z$ | $\Delta Q$ | $\bar{Q}$ | $w$ | Integrated Intensity |
|  |  | $({\rm GHz})$ | $({\rm s^{-1}})$ |  | $({\rm kHz \, mG^{-1}})$ |  |  |  | $({\rm Jy\,km\,s^{-1}})$ |
| 1/2 - 1/2 | 1/2 - 1/2 | 113.123369 | $1.29 \times 10^{-6}$ | 2 | -0.62 | 3.01 | 5.01 | 0.038 | $0.101 \pm 0.009$ |
| 1/2 - 1/2 | 1/2 - 3/2 | 113.144147 | $1.05 \times 10^{-5}$ | 2 | 2.18 | -0.98 | 1.14 | 0.030 | $0.476 \pm 0.009$ |
| 1/2 - 1/2 | 3/2 - 3/2 | 113.191289 | $6.68 \times 10^{-6}$ | 4 | 0.63 | 21.89 | 42.84 | 0.326 | $0.565 \pm 0.009$ |
| 1/2 - 1/2 | 3/2 - 1/2 | 113.170511 | $5.14 \times 10^{-6}$ | 4 | -0.30 | 0.06 | 8.42 | 0.031 | $0.462 \pm 0.009$ |
| 3/2 - 1/2 | 3/2 - 1/2 | 113.488126 | $6.74 \times 10^{-6}$ | 4 | 2.17 | 15.07 | 17.07 | 0.447 | $0.569 \pm 0.009$ |
| 3/2 - 1/2 | 5/2 - 3/2 | 113.490964 | $1.19 \times 10^{-5}$ | 6 | 0.56 | -0.96 | 1.28 | 0.009 | $1.148 \pm 0.009$ |
| 3/2 - 1/2 | 1/2 - 1/2 | 113.499634 | $1.06 \times 10^{-5}$ | 2 | 0.62 | -0.86 | 1.97 | 0.015 | $0.486 \pm 0.009$ |
| 3/2 - 1/2 | 3/2 - 3/2 | 113.508902 | $5.19 \times 10^{-6}$ | 4 | 1.62 | -0.86 | 1.26 | 0.025 | $0.455 \pm 0.009$ |
| 3/2 - 1/2 | 1/2 - 3/2 | 113.520420 | $1.30 \times 10^{-6}$ | 2 | 1.56 | -0.53 | 4.27 | 0.080 | $0.102 \pm 0.009$ |

: CN $N=1-0$ Hyperfine Components

Table [1](#tab:observations) details the observed molecular transitions, pertinent Zeeman-related properties and their observed integrated intensities. Einstein A coefficients, $A_{\rm ul}$, and upper-state level weights, $g_{\rm u}$, were taken from CDMS (cite: Endres_ea_2016) which collates data from (cite: Dixon_Woods_1977) and (cite: Skatrud_ea_1983). Properties relating to Zeeman splitting, $z$, $\Delta Q$ and $\bar{Q}$, were taken from (cite: Lankhaar_Teague_2023).

![](figures/broadening_nongaussianity.pdf)

The line centers were measured from the data. Firstly, spectra from each annulus was aligned and averaged using the velocity profiles described in Appendix [9](#sec:app:model) before having a Gaussian line profile fit to it to derive a line center. The mean line center between $0.5\ensuremath{''}$ and $3\ensuremath{''}$ was taken as the true line center after subtracting a systemic velocity of $2.84~{\rm km\,s^{-1}}$. The typical uncertainty on each of these is less than 10 kHz and is dominated by the systematic uncertainty related to the determination of the systemtic velocity.

The integrated intensities were calculated using standard ‘shift-and-stack’ techniques (cite: Yen_ea_2016) where a dynamical stellar mass of $0.84~M_{\odot}$ and a disk inclination of $5.8\ensuremath{^\circ}$ were adopted. The data were spatially integrated out to $4\ensuremath{''}$ (240 au) and spectrally over $\pm 300~{\rm kHz}$, or equivalently $\pm \, {\sim}800~{\rm m\,s^{-1}}$ at this frequency.

# Observational Signatures of Zeeman Broadening

To robustly identify the presence of a magnetic field through a change in the line profile caused by Zeeman splitting without a companion polarization measurement, we must be confident that the broadening we see can be uniquely attributed to Zeeman splitting. In this Appendix, we discuss how this broadening manifests for the low to moderate fields expected in protoplanetary disks, and how we can be confident that we are correctly identifying a magnetic field.

As described in Section [3.2](#sec:methodology:zeeman) and shown in Figure [2](#fig:zeeman_splitting_demonstration), the broadening experienced by each line results from the separation of the three magnetic subtransition groups, $\pi^0$, $\sigma^+$ and $\sigma^-$, dependent on the magnetic field strength, $|\mathbf{B}|$, and the relative propagation propensity of these transition groups, influenced by the magnetic field orientation, $\theta$. The sensitivity of each line to these perturbations, initially derived in (cite: Crutcher_ea_1996), is codified in the line-specific parameters $z$, $\Delta Q$, and $\bar{Q}$, listed in Table [1](#tab:observations) and described in (cite: Lankhaar_Teague_2023). At the moderately low field strengths expected to be threading protoplanetary disks, the dominant signal will therefore be a specific ratio of line widths; more sensitive lines should experience more broadening than less sensitive lines.

This is demonstrated in the top row of Figure [7](#fig:app:broadening_nongaussianity) which shows the change in line width (derived by the fit of a Gaussian profile) when the magnetic field is increased for the most sensitive hyperfine component to Zeeman splitting, $N=1-0$ $J=3/1-1/2$ $F=3/2-1/2$, in red, and the least sensitive hyperfine component, $N=1-0$ $J=3/1-1/2$ $F=5/2-3/2$, in blue. The left hand panel assumes a purely poloidal field $\theta = 0\ensuremath{^\circ}$ and varies $|\mathbf{B}|$, while the right panel fixed $|\mathbf{B}| = 20~{\rm mG}$ and varies $\theta$. Note that the remaining 7 hyperfine components will fall between these two limiting cases. This demonstrates that each magnetic field configuration, $(|\mathbf{B}|,\, \theta)$, should relate to a very specific ratio of the line widths.

With stronger fields, the Zeeman splitting can become sufficiently strong that the lines deviate from a purely Gaussian profile. This impact of this is shown in the bottom row of Figure [7](#fig:app:broadening_nongaussianity) which plots $f_G$, a parameter which describes the non-Gaussianity of the line. This parameter is defined as $f_G = 1 - (\sum | {\rm I_{\rm instrinic}} - I_{\rm gaussian}| \, / \sum I_{\rm intrinsic})$, where $I_{\rm intrinsic}$ is the intrinsic line profile and $I_{\rm gaussian}$ is the best-fit Gaussian profile. When a Gaussian profile perfectly reproduces the intrinsic line profile, $f_G = 1$, and drops as the line becomes progressively less Gaussian. As can be seen, it is only at magnetic field strengths around 15 mG that a noticeable deviation from Gaussianity is observed (although the specific field strength this occurs at will depend on the optical depth of the line as the saturate core will also lead to non-Gaussianity). Importantly, the methodology described in Section [3](#sec:methodology) models the full Zeeman splitting and so implicitly accounts for any non-Gaussianity in the line, either through the Zeeman splitting or from optical depth effects.

Another fortuitous aspect is that the sensitivity of the line to Zeeman splitting, summarized by $w$ in Table [1](#tab:observations), does not correlate with the relative intensity of the line. This is of primary importance as many broadening effects correlate with the peak intensity of the line, such as the asymmetric perturbations associated with unresolved spatial intensity gradients (cite: Keppler_ea_2019; Boehler_ea_2021) or contamination from ‘back-side’ emission (cite: Izquierdo_ea_2025), so a clear correlation between line width and peak intensity would signify broadening mechanisms unrelated to Zeeman splitting. To demonstrate this, Figure [8](#fig:app:broadening_sensitivity) plots the line width ratio (again, derived by the fit of a Gaussian line profile to the resulting spectrum) of the most sensitive hyperfine component to the least hyperfine component as we increase different model parameters which impact the line width. As can be seen, it is only the magnetic field strength, $|\mathbf{B}|$, which results in an increasing ratio, while all the others show minimal change in the ratio, despite all lines getting broader. The slight decrease observed here is due to the less sensitive line, $N=1-0$ $J=3/1-1/2$ $F=3/2-1/2$, having a substantially larger optical depth and so the impacts of non-Gaussianity due to optically thick cores reduces the ratio.

![](figures/broadening_sensitivity.pdf)

One final consideration is the impact of the disk vertical structure which is not considered in the excitation analysis that assumes the emission arises from a homogeneous slab. As each of the hyperfine components has a different optical depth, it is possible that their emission arises from substantially different conditions which may lead to varying line profiles for each hyperfine component. As previously mentioned, the fact that the sensitivity to Zeeman splitting for each of the lines does not correlate with the relative intensity of the line suggests that this should not result in changes that could be misinterpreted as Zeeman splitting. To demonstrate that this is the case, Figure [9](#fig:app:temperature_tau_correlation) plots the effective kinetic temperature for each line (the kinetic temperature one would infer based on the line width assuming that thermal broadening was the sole broadening mechanism) as a function of their optical depth for different magnetic field strengths (different colors) and CN column densities (different line styles). As can be seen, the increased Zeeman sensitivity of the lines with average optical depths lead to broader lines which would be interpreted as arising from warmer regions. Thus, assuming that $\tau$ is a proxy of the height above the midplane that the emission arises, one would need to invoke an unrealistic vertical temperature structure to explain the observed line broadening ratios, demonstrating that such an effect could not masquerade as Zeeman broadening.

![](figures/temperature_tau_correlation.pdf)

# Model Fits

In this section we discuss the other parameters derived as part of the spectral analysis shown in Figure [10](#fig:app:excitation_conditions). As with Fig. [4](#fig:B_theta_radial_profiles), blue points denote the model with a disk-centric magnetic field morphology while the red points show the environmental field morphology. All error bars represent the 16th to 84th percentile range of the posterior distribution. It is clear (and expected) that the assumed field morphology should have no influence on any of these parameters.

## Excitation Analysis

Panels (a), (b) and (c) show the recovered azimuthally-averaged velocity profiles. To bring out the structure in the velocity profile, panel (a) shows the rotation velocity after subtracting a Keplerian velocity profile for a stellar mass of $0.82~M_{\odot}$ and source inclination of $5.8\ensuremath{^\circ}$. There is negligible deviation from this Keplerian profile out to $2.5\ensuremath{''}$ (150 au) where a slowing of the rotation is observed, likely due to the onset of the pressure support from the exponential taper of the gas surface density (cite: Teague_ea_2022). Interior to $1\ensuremath{''}$ there is a considerable deviation, however this is dominated by beam smearing effects (cite: Teague_ea_2018a). There is no discernible radial velocity component inwards of $2.5\ensuremath{''}$, however around a deviation is inferred with a maximum velocity of $|v_r| \approx 100~{\rm m\,s^{-1}}$, as shown in panel (b). Unfortunately, given the close to face-on nature of the disk around TW Hya, we are unable to robustly differentiate inwards and outwards motions, although the clockwise motion suggested by the spiral arm would suggest an *inwards* motion (cite: Teague_ea_2022). As such, it is unclear whether this is a signature of a disk wind or another phenomena. No significant vertical motions are detected outwards of $1\ensuremath{''}$, although there is a large scatter. Interior to this a vertical component is required to reproduce the data, however this is likely due to beam smearing effects, as with $v_{\phi}$.

As shown in panel (d), the kinetic temperature is found to decrease radially, starting from above 30 K in the inner disk and dropping to around 10 K outside $2.5\ensuremath{''}$ where it plateaus. This appears to be close to the expected midplane temperature (cite: Macias_ea_2021). The column density of CN also drops radially, shown in panel (e), ranging from just under $10^{15}~{\rm cm^{-2}}$ at $0.5\ensuremath{''}$, down to less than $10^{13}~{\rm cm^{-2}}$ beyond $3.5\ensuremath{''}$. Two subtle dips are perceptible in both the kinetic temperature and column density radial profiles at ${\sim}~1.3\ensuremath{''}$ (78 au) and ${\sim}~2.7\ensuremath{''}$ (162 au). Depressions at these radial locations was also reported in the CS (5-4) integrated flux profile in (cite: Teague_ea_2022) suggesting that these regions may be gaps in the gas surface density.

The collider density, assumed to be solely H$_2$, is show in panel (f) as lower limits. These are the critical densities for the (1-0) transition for the given temperature and column density of CN. To derive this lower limit from the posterior distributions of $n({\rm H_2})$, shown in Fig. [12](#fig:app:nh2_posteriors) for both field morphologies, we fit a scaled cumulative Gaussian distribution function and use the median of the Gaussian distribution as the lower limit to the density. These are shown as the dashed vertical lines in Fig. [12](#fig:app:nh2_posteriors). Interior to $1\ensuremath{''}$, the posteriors appear to be peaked around the critical density, however this is likely due to beam smearing effects perturbing the line profiles and thus we suggest that these are not robust density estimates.

Panels (g) and (h) show the systematic broadening mechanisms: non-thermal broadening and a Gaussian convolution of the final spectrum, respectively. The $1\sigma$ width of the prior on the non-thermal broadening based on the upper limts from (cite: Flaherty_ea_2018) are shown in (g). Across the bulk of the disk, the non-thermal broadening is consistent with zero, in agreement with previous searches for non-thermal broadening in this source (cite: Hughes_ea_2011; Teague_ea_2016; Flaherty_ea_2018). Beyond ${\sim}~2.5\ensuremath{''}$, non-zero values are found needed to account for the extremely narrow thermal widths in these regions (a kinetic temperature of 10 K produces a thermal Doppler width of $80~{\rm m\,s^{-1}}$. With such narrow lines, the limited spectral resolution of the data will prohibit robust inferences about the line width, as evidenced by the magnetic field inferences shown in Fig. [13](#fig:B_posteriors_disk) and [14](#fig:B_posteriors_env).

Figure [11](#fig:cornerplot_disk) shows the marginalized posterior distributions and covariances for all the parameters of the model for a disk-centric magnetic field optimized for $1.4\ensuremath{''}$ annulus in the disk. No significant correlations are found, however a slight covariance is observed between ${\rm FWHM_{conv}}$ and $|\mathbf{B}|$ which is unsurprising given that both influence the width of the resulting line.

(cite: Yoshida_ea_2024) performed a similar non-LTE analysis as described here and found consistent excitation conditions across the radial region where these two analyses overlapped: $0.6\ensuremath{''}$ and $2\ensuremath{''}$. (cite: Yoshida_ea_2024) used these conditions to suggest an emission height for CN to arise from $z \, / \, r 
\sim 0.2 - 0.3$, consistent with the previous estimate from (cite: Teague_Loomis_2020).

![](excitation_conditions.pdf)

![](cornerplot_disk_1.4arcsec.pdf)

![](nh2_posteriors.pdf)

## Zeeman Sensitivities

Figures [13](#fig:B_posteriors_disk) and [14](#fig:B_posteriors_env) compare the posterior distributions for the magnetic field strength when the line-specific sensitives to the Zeeman effect are correct, in color, and mixed up in gray. The two gray models are when the most sensitive transitions, $J=3/2 - 1/2$ $F = 3/2 - 1/2$ and $J = 1/2 - 1/2$ $F = 3/2 - 3/2$, are swapped with the least sensitive transitions, $J=3/2 - 1/2$ $F = 1/2 - 1/2$ and $J=3/2 - 1/2$ $F = 3/2 - 3/2$, and overlap for most radii. Each panel shows a different radial bin and those with a gray background are where the two distributions are not statistically distinct. For this measure we calculate the posterior distance as the difference between the two posterior medians and require this to be larger than the quadrature sum of the two posterior widths, taken as the 16th to 84th percentile range. As the posteriors for the two ‘random’ models are extremely similar for most radii, we combine them and treat them as a single posterior distribution for this calculation.

Over most of the disk the ‘correct’ energy level structure posteriors appear to peak at larger magnetic field strengths than for the ‘mixed’ structures, as would be expected for Zeeman splitting, however the large widths of the posteriors in the outer disk, $\gtrsim 2.5\ensuremath{''}$, preclude a robust differentiation between the posteriors.

![](B_posteriors_disk.pdf)

![](B_posteriors_env.pdf)

natexlab

(ref: Andrews_2020) Andrews, S. M. 2020, ARA&A, 58, 483, doi: [`10.1146/annurev-astro-031220-010302`](http://doi.org/10.1146/annurev-astro-031220-010302)

(ref: Bae_ea_2023) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423, doi: [`10.48550/arXiv.2210.13314`](http://doi.org/10.48550/arXiv.2210.13314)

(ref: Bai_2015) Bai, X.-N. 2015, ApJ, 798, 84, doi: [`10.1088/0004-637X/798/2/84`](http://doi.org/10.1088/0004-637X/798/2/84)

(ref: Boehler_ea_2021) Boehler, Y., Ménard, F., Robert, C. M. T., et al. 2021, A&A, 650, A59, doi: [`10.1051/0004-6361/202040089`](http://doi.org/10.1051/0004-6361/202040089)

(ref: Borlina_ea_2021) Borlina, C. S., Weiss, B. P., Bryson, J. F. J., et al. 2021, Science Advances, 7, eabj6928, doi: [`10.1126/sciadv.abj6928`](http://doi.org/10.1126/sciadv.abj6928)

(ref: Carpenter_ea_2023) Carpenter, J., Brogan, C., Iono, D., & Mroczkowski, T. 2023, in Physics and Chemistry of Star Formation: The Dynamical ISM Across Time and Spatial Scales, ed. V. Ossenkopf-Okada, R. Schaaf, I. Breloy, & J. Stutzki, 304, doi: [`10.48550/arXiv.2211.00195`](http://doi.org/10.48550/arXiv.2211.00195)

(ref: Cataldi_ea_2021) Cataldi, G., Yamato, Y., Aikawa, Y., et al. 2021, ApJS, 257, 10, doi: [`10.3847/1538-4365/ac143d`](http://doi.org/10.3847/1538-4365/ac143d)

(ref: Crutcher_ea_1996) Crutcher, R. M., Troland, T. H., Lazareff, B., & Kazes, I. 1996, ApJ, 456, 217, doi: [`10.1086/176642`](http://doi.org/10.1086/176642)

(ref: Das_ea_2024) Das, S., Kurtovic, N. T., & Flock, M. 2024, A&A, 689, A104, doi: [`10.1051/0004-6361/202450278`](http://doi.org/10.1051/0004-6361/202450278)

(ref: Dixon_Woods_1977) Dixon, T. A., & Woods, R. C. 1977, , 67, 3956, doi: [`10.1063/1.435412`](http://doi.org/10.1063/1.435412)

(ref: Doi_ea_2023) Doi, K., & Kataoka, A. 2023, ApJ, 957, 11, doi: [`10.3847/1538-4357/acf5df`](http://doi.org/10.3847/1538-4357/acf5df)

(ref: Endres_ea_2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: Flaherty_ea_2020) Flaherty, K., Hughes, A. M., Simon, J. B., et al. 2020, ApJ, 895, 109, doi: [`10.3847/1538-4357/ab8cc5`](http://doi.org/10.3847/1538-4357/ab8cc5)

(ref: Flaherty_ea_2018) Flaherty, K. M., Hughes, A. M., Teague, R., et al. 2018, ApJ, 856, 117, doi: [`10.3847/1538-4357/aab615`](http://doi.org/10.3847/1538-4357/aab615)

(ref: Flock_ea_2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68, doi: [`10.1051/0004-6361/201424693`](http://doi.org/10.1051/0004-6361/201424693)

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Fu_ea_2021) Fu, R. R., Volk, M. W. R., Bilardello, D., et al. 2021, AGU Advances, 2, e00486, doi: [`10.1029/2021AV000486`](http://doi.org/10.1029/2021AV000486)

(ref: Goldreich_Kylafis_1982) Goldreich, P., & Kylafis, N. D. 1982, ApJ, 253, 606, doi: [`10.1086/159663`](http://doi.org/10.1086/159663)

(ref: Harrison_ea_2021) Harrison, R. E., Looney, L. W., Stephens, I. W., et al. 2021, ApJ, 908, 141, doi: [`10.3847/1538-4357/abd94e`](http://doi.org/10.3847/1538-4357/abd94e)

(ref: Herczeg_ea_2023) Herczeg, G. J., Chen, Y., Donati, J.-F., et al. 2023, ApJ, 956, 102, doi: [`10.3847/1538-4357/acf468`](http://doi.org/10.3847/1538-4357/acf468)

(ref: SpectralRadex) Holdship, J., Vermariën, G., van der Tak, F., & Black, J. H. 2025, , Astrophysics Source Code Library, record ascl:2501.010

(ref: Hughes_ea_2011) Hughes, A. M., Wilner, D. J., Andrews, S. M., Qi, C., & Hogerheijde, M. R. 2011, ApJ, 727, 85, doi: [`10.1088/0004-637X/727/2/85`](http://doi.org/10.1088/0004-637X/727/2/85)

(ref: Hughes_ea_2009) Hughes, A. M., Wilner, D. J., Cho, J., et al. 2009, ApJ, 704, 1204, doi: [`10.1088/0004-637X/704/2/1204`](http://doi.org/10.1088/0004-637X/704/2/1204)

(ref: Ilee_ea_2022) Ilee, J. D., Walsh, C., Jennings, J., et al. 2022, MNRAS, 515, L23, doi: [`10.1093/mnrasl/slac048`](http://doi.org/10.1093/mnrasl/slac048)

(ref: Izquierdo_ea_2025) Izquierdo, A. F., Stadler, J., Galloway-Sprietsma, M., et al. 2025, ApJL, 984, L8, doi: [`10.3847/2041-8213/adc439`](http://doi.org/10.3847/2041-8213/adc439)

(ref: Kaligina_Lique_2015) Kalugina, Y., & Lique, F. 2015, MNRAS, 446, L21, doi: [`10.1093/mnrasl/slu159`](http://doi.org/10.1093/mnrasl/slu159)

(ref: Kataoka_ea_2015) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78, doi: [`10.1088/0004-637X/809/1/78`](http://doi.org/10.1088/0004-637X/809/1/78)

(ref: Keppler_ea_2019) Keppler, M., Teague, R., Bae, J., et al. 2019, A&A, 625, A118, doi: [`10.1051/0004-6361/201935034`](http://doi.org/10.1051/0004-6361/201935034)

(ref: Lankhaar_Teague_2023) Lankhaar, B., & Teague, R. 2023, A&A, 678, A17, doi: [`10.1051/0004-6361/202345840`](http://doi.org/10.1051/0004-6361/202345840)

(ref: Lesur_ea_2023) Lesur, G., Flock, M., Ercolano, B., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 465, doi: [`10.48550/arXiv.2203.09821`](http://doi.org/10.48550/arXiv.2203.09821)

(ref: Macias_ea_2021) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33, doi: [`10.1051/0004-6361/202039812`](http://doi.org/10.1051/0004-6361/202039812)

(ref: Mansbach_ea_2025) Mansbach, E. N., Weiss, B. P., Lima, E. A., et al. 2024, AGU Advances, 5, 2024AV001396, doi: [`10.1029/2024AV001396`](http://doi.org/10.1029/2024AV001396)

(ref: Mazzei_ea_2020) Mazzei, R., Cleeves, L. I., & Li, Z.-Y. 2020, ApJ, 903, 20, doi: [`10.3847/1538-4357/abb67a`](http://doi.org/10.3847/1538-4357/abb67a)

(ref: Morbidelli_ea_2024) Morbidelli, A., Marrocchi, Y., Ahmad, A. A., et al. 2024, A&A, 691, A147, doi: [`10.1051/0004-6361/202451388`](http://doi.org/10.1051/0004-6361/202451388)

(ref: Ohashi_ea_2025) Ohashi, S., Muto, T., Tsukamoto, Y., et al. 2025, Nature Astronomy, 9, 526, doi: [`10.1038/s41550-024-02454-x`](http://doi.org/10.1038/s41550-024-02454-x)

(ref: Paneque-Carreno_ea_2024) Paneque-Carreño, T., Izquierdo, A. F., Teague, R., et al. 2024, A&A, 684, A174, doi: [`10.1051/0004-6361/202347757`](http://doi.org/10.1051/0004-6361/202347757)

(ref: Pattle_ea_2023) Pattle, K., Fissel, L., Tahani, M., Liu, T., & Ntormousi, E. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 193, doi: [`10.48550/arXiv.2203.11179`](http://doi.org/10.48550/arXiv.2203.11179)

(ref: Riols_Lesur_2019) Riols, A., & Lesur, G. 2019, A&A, 625, A108, doi: [`10.1051/0004-6361/201834813`](http://doi.org/10.1051/0004-6361/201834813)

(ref: Romero-Mirza_ea_2023) Romero-Mirza, C. E., Öberg, K. I., Law, C. J., et al. 2023, ApJ, 943, 35, doi: [`10.3847/1538-4357/aca765`](http://doi.org/10.3847/1538-4357/aca765)

(ref: Skatrud_ea_1983) Skatrud, D. D., De Lucia, F. C., Blake, G. A., & Sastry, K. V. L. N. 1983, Journal of Molecular Spectroscopy, 99, 35, doi: [`10.1016/0022-2852(83)90290-4`](http://doi.org/10.1016/0022-2852(83)90290-4)

(ref: Stephens_ea_2020) Stephens, I. W., Fernández-López, M., Li, Z.-Y., Looney, L. W., & Teague, R. 2020, ApJ, 901, 71, doi: [`10.3847/1538-4357/abaef7`](http://doi.org/10.3847/1538-4357/abaef7)

(ref: Suriano_ea_2018) Suriano, S. S., Li, Z.-Y., Krasnopolsky, R., & Shang, H. 2018, MNRAS, 477, 1239, doi: [`10.1093/mnras/sty717`](http://doi.org/10.1093/mnras/sty717)

(ref: Sutton_ea_2017) Sutton, S., Alexander, C. M. O., Bryant, A., et al. 2017, , 211, 115, doi: [`10.1016/j.gca.2017.05.021`](http://doi.org/10.1016/j.gca.2017.05.021)

(ref: Tazaki_ea_2017) Tazaki, R., Lazarian, A., & Nomura, H. 2017, ApJ, 839, 56, doi: [`10.3847/1538-4357/839/1/56`](http://doi.org/10.3847/1538-4357/839/1/56)

(ref: GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: Teague_ea_2018a) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018a, ApJL, 860, L12, doi: [`10.3847/2041-8213/aac6d7`](http://doi.org/10.3847/2041-8213/aac6d7)

(ref: Teague_Loomis_2020) Teague, R., & Loomis, R. 2020, ApJ, 899, 157, doi: [`10.3847/1538-4357/aba956`](http://doi.org/10.3847/1538-4357/aba956)

(ref: Teague_ea_2016) Teague, R., Guilloteau, S., Semenov, D., et al. 2016, A&A, 592, A49, doi: [`10.1051/0004-6361/201628550`](http://doi.org/10.1051/0004-6361/201628550)

(ref: Teague_ea_2017) Teague, R., Semenov, D., Gorti, U., et al. 2017, ApJ, 835, 228, doi: [`10.3847/1538-4357/835/2/228`](http://doi.org/10.3847/1538-4357/835/2/228)

(ref: Teague_ea_2018c) Teague, R., Henning, T., Guilloteau, S., et al. 2018b, ApJ, 864, 133, doi: [`10.3847/1538-4357/aad80e`](http://doi.org/10.3847/1538-4357/aad80e)

(ref: Teague_ea_2021) Teague, R., Hull, C. L. H., Guilloteau, S., et al. 2021, ApJ, 922, 139, doi: [`10.3847/1538-4357/ac2503`](http://doi.org/10.3847/1538-4357/ac2503)

(ref: Teague_ea_2022) Teague, R., Bae, J., Andrews, S. M., et al. 2022, ApJ, 936, 163, doi: [`10.3847/1538-4357/ac88ca`](http://doi.org/10.3847/1538-4357/ac88ca)

(ref: CASA) Team, T. C., Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: vanBoekel_ea_2017) van Boekel, R., Henning, T., Menu, J., et al. 2017, ApJ, 837, 132, doi: [`10.3847/1538-4357/aa5d68`](http://doi.org/10.3847/1538-4357/aa5d68)

(ref: vanderTak_ea_2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: Vlemmings_ea_2019) Vlemmings, W. H. T., Lankhaar, B., Cazzoletti, P., et al. 2019, A&A, 624, L7, doi: [`10.1051/0004-6361/201935459`](http://doi.org/10.1051/0004-6361/201935459)

(ref: Wardle_2007) Wardle, M. 2007, Ap&SS, 311, 35, doi: [`10.1007/s10509-007-9575-8`](http://doi.org/10.1007/s10509-007-9575-8)

(ref: Weiss_ea_2021) Weiss, B. P., Bai, X.-N., & Fu, R. R. 2021, Science Advances, 7, eaba5967, doi: [`10.1126/sciadv.aba5967`](http://doi.org/10.1126/sciadv.aba5967)

(ref: Yen_ea_2016) Yen, H.-W., Koch, P. M., Liu, H. B., et al. 2016, ApJ, 832, 204, doi: [`10.3847/0004-637X/832/2/204`](http://doi.org/10.3847/0004-637X/832/2/204)

(ref: Yoshida_ea_2024) Yoshida, T. C., Nomura, H., Furuya, K., et al. 2024, ApJ, 966, 63, doi: [`10.3847/1538-4357/ad2fb4`](http://doi.org/10.3847/1538-4357/ad2fb4)

</paper>

Write the methods card for this paper.