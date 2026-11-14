# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...688A.110S\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...688A.110S",
 "title": "Complex angular structure of three elliptical galaxies from high-resolution ALMA observations of strong gravitational lenses",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Stacey, H. R.",
 "n_authors": 7,
 "arxiv_id": "2403.04850",
 "doi": "10.1051/0004-6361/202449710",
 "alma_projects_linked_by_archive": [
  "2016.1.01374.S",
  "2011.0.00016.SV"
 ]
}
```

Paper text:
<paper>
# Complex angular structure of three elliptical galaxies from high-resolution ALMA observations of strong gravitational lenses

# Introduction

Strong gravitational lensing occurs when the light from a distant background galaxy is distorted and magnified into several distinct images by a massive foreground galaxy. This phenomenon has become a well-established tool with which to probe the mass structure and dark matter distribution within the lens galaxies. For example, the observed surface brightness distribution of the lensed images has been used to constrain the evolutionary pathways of elliptical galaxies (cite: Sonnenfeld:2012), cosmological parameters (e.g. (cite: Wong:2020; Collett:2018)) and the nature of dark matter via the gravitational effect of low-mass dark matter halos (cite: Vegetti:2014; Vegetti:2023; Ritondale:2019a; Hsueh:2020; Gilman:2020a; Enzi:2021; Powell:2023). Moreover, the magnification provided by the lens increases the effective angular resolution of the data, allowing the detailed astrophysical processes within extremely distant objects at important cosmological epochs to be studied (e.g. (cite: Yang:2019; Rizzo:2021; Stacey:2022; Geach:2023)). Fundamental to all these important lines of research with strong gravitational lensing is the parameterisation of the large-scale mass distribution of the lensing galaxy (the so-called ‘macro model’). For galaxy-scale strong lensing events, this is commonly assumed to be described by an ellipsoidal power-law mass-density profile with some external shear component to account for the sometimes complex environment of the lens. This simple parameterisation can lead to valid questions regarding the accuracy of the lens model or the robustness of the reconstructed source, given the uncertainties in the lens modelling.

Indeed, several recent works have highlighted the limitations of the power-law model assumption for the mass distribution of the lens and the impact this can have on the astrophysical applications of galaxy-scale gravitational lensing (cite: Powell:2021; Cao:2022; VandeVyvere:2022; Nightingale:2022; He:2023; O’Riordan:2023). The majority of elliptical galaxies have boxy or discy isophote shapes in their stellar distribution (cite: Bender:1988; Bender:1989; Cappellari:2016) and can exhibit twists and shape variations with radius (cite: Liller:1960; Liller:1966; King:1978). These features should manifest an anisotropic density structure that may result in systematic errors in the recovered Hubble constant from lensing (cite: Cao:2022; VandeVyvere:2022), change the relative predicted image magnifications by $10\--40$ percent (cite: Evans:2003; Congdon:2005; Powell:2022; Cohen:2024), and induce false detections of low-mass dark matter haloes (cite: Nightingale:2022; He:2023; O’Riordan:2023; Cohen:2024), leading to biased constraints on dark matter models.

Recently, (cite: Powell:2022) showed that complex angular structure in the lens and an external shear gradient were required to focus the source with observations at milli-arcsecond (mas) resolution (see also (cite: Spingola:2018)), suggesting that the sensitivity to angular structure increases with angular resolution. In this regard, observations of bright and highly magnified starburst galaxies at high redshift with the Atacama Large Millimetre/sub-millimetre Array (ALMA) can provide a detailed test of angular structure, given the higher angular resolution when compared to current optical or infrared telescopes. Here, we have analysed publicly available data from the ALMA archive for three gravitational lenses observed at an angular resolution of $\approx30$ mas. By using a pixellated lens modelling methodology adapted for interferometric data (cite: Vegetti:2009; Rybak:2015a; Rybak:2015b; Rizzo:2018; Ritondale:2019a; Powell:2021; Powell:2022), we investigated the angular structure in these lens galaxies with multipole expansions of the power-law density profile.

The paper is structured as follows. In Section [2](#section:data) we give an overview of the ALMA observations and data reduction. This section also includes a review of available *Hubble* Space Telescope (HST) infrared imaging, which we use to compare the mass and light distributions of the three lens galaxies. In Section [3](#section:modelling), we describe the lens model parameterisations and methodology. In Section [4](#section:results), we report our results and in Section [5](#section:discussion), we discuss the possible origins of the angular structure, before summarising and considering the direction of future work in Section [6](#section:conclusions).

![image](SDP81_Ls_deconvolved_plot_small.pdf) ![image](SPT0532_Ls_deconvolved_plot_small.pdf) ![image](SPT0538_Ls_deconvolved_plot_small.pdf)

# Data reduction

## ALMA observations

We obtained data from the ALMA archive for three gravitationally lensed dusty star-forming galaxies: SPT 0532$-$50 (SPT S J053250$-$5047.1), SPT 0538$-$50 (SPT S J053816$-$5030.8), and SDP 81 (H-ATLAS J090311.6$+$003906). These are galaxy-scale lenses with known source and lens redshifts ((cite: Negrello:2010; Spilker:2016); Table [\[table:obs\]](#table:obs)). Details of the lens systems and ALMA observations are given in Table [\[table:obs\]](#table:obs). The observations of SPT 0532$-$50 and SPT 0538$-$50 consisted of multiple epochs in compact and extended antenna configurations: we considered only the long-baseline configurations for this experiment to maintain the higher angular resolution. The data for SDP 81 were taken during the 2014 ALMA long baseline science verification campaign, using an atypical array configuration (cite: Vlahakis2015).

For the two SPT lenses, we used the ALMA pipeline in Common Astronomy Software Applications (CASA; (cite: casa2022)) for the initial calibration of the data. There is an apparent spectral line emission in two spectral windows for SPT 0532$-$50; therefore, these spectral windows are not considered further in our analysis. No line emission was detected for SPT 0548$-$50; therefore, we use all of the spectral windows. For SDP 81, the calibrated continuum-only dataset was obtained from ALMA via the science verification project.[^2] The atypical antenna configuration includes more short baselines, which results in diffuse, extended low-surface brightness emission in the image that is not useful for our analysis. Therefore, we only use baselines with lengths greater than 100 m ($\approx10^5$ k$\uplambda$) to remove sensitivity to this extended emission. For all of the datasets, the calibrated visibilities were inspected to confirm the quality of the pipeline calibration and any outlying data were flagged. No additional time or frequency averaging was done.

We performed several rounds of self-calibration to correct gain offsets between observational epochs and improve the dynamic range of the data for each target. We chose a minimum solution interval required to achieve a signal-to-noise ratio of greater than 3 for $>90$ percent of antennas, and only accepted calibrations that increase the dynamic range of the data and do not change the synthesised beam size by more than 10 percent. We iterated the procedure for as long as the dynamic range of the data improved. For SPT 0532$-$50 and SPT 0538$-$50, we derived gain corrections in phase and amplitude with a solution interval of each observational epoch. For SDP 81, we derived phase-only corrections of each observational epoch (spanning approximately 50 mins each).

Deconvolved images of three lens systems are shown in Fig. [1](#fig:clean_images).

## Hubble Space Telescope observations

The three lens systems were observed with the HST using the Wide-Field Camera 3 (WFC3) at 1.1 and 1.6 $\mu$m (F110W and F160W filters, respectively) as part of programmes GO-12194 (PI: Negrello) and GO-12659 (PI: Vieira). These data were obtained from the HST archive and processed using standard procedures within the astrodrizzle package. During this process, the images were drizzled to 60 mas pixel$^{-1}$.

# Lens modelling

## Mass distribution

We parameterised the underlying global mass distribution of the lens as a singular power-law ellipsoidal density profile. Following (cite: Tessore:2015) and (cite: ORiordan:2020), the 2D dimensionless surface mass density profile (convergence) is described by $$\begin{equation}
    \kappa(R) = \frac{3-\gamma}{2} \left ( \frac{b}{R} \right )^{\gamma -1}\, ,
\label{eq:PL}
\end{equation}$$ where $R$ is the elliptical radius ($R^{2}=q^{2}x^{2} + y^{2}$), $\gamma$ is the 3D density slope ($\gamma=2$ is isothermal), $q$ is the axis ratio, and $b=\sqrt{q}\ R_{E}$, where $R_E$ is the Einstein radius. $\theta_q$ describes the position angle of the ellipticity, defined in degrees east of north. We also allowed for an external shear described by a strength, $\Gamma$, and angle, $\theta_\Gamma$. We labeled this model ‘PL’.

We then allowed flexibility in the form of multipole perturbations that add angular variations to the PL density profile to account for deviations from perfect ellipticity. These are described by the following Fourier expansion: $$\begin{equation}
    \kappa_m(R,\theta) = R^{-(\gamma-1)}\left[A_m \sin(m\theta)+B_m\cos(m\theta)\right]\, ,
\label{eq:multipoles}
\end{equation}$$ in polar co-ordinates for multipole order $m$, where $A_m$ and $B_m$ are unitless sine and cosine multipole coefficients that give the strength of the density perturbations normalised to the critical density at 1 arcsec radius from the lens centre. $\gamma$ is the slope of the density profile from Eq ([\[eq:PL\]](#eq:PL)). We adopted multipoles of order $m=3$, which allows for asymmetrical density structure with respect to the lens centre, and order $m=4$, which can create boxy or discy shapes that are often observed in the isophotes of elliptical galaxies (cite: Bender:1988; Pasquali:2006; Hao:2006; Chaware:2014)[^3] if aligned with the ellipticity. We consider only up to order 4 here, as these have been predicted to be sources of systematic errors in the constraints derived from lensing (e.g. (cite: Nightingale:2022; VandeVyvere:2022; O’Riordan:2023)). We label this model component as ‘MP’.

## Bayesian inference

We employed the Bayesian pixellated lens modelling technique appropriate for interferometric data introduced by (cite: Powell:2021). This method reconstructs the source emission on vertices of Delaunay triangles adapted to the lensing magnification. The source (s) and lens parameters ($\boldsymbol{\eta}$) were inferred by maximising the following posterior:

$$\begin{equation}
    P(\mathbf{s}, \boldsymbol{\eta} | \mathbf{d}) \propto P(\mathbf{d} | \mathbf{s}, \boldsymbol{\eta}) P(\mathbf{s} | {\mathbf{H}}, \lambda_{\rm s}) P(\boldsymbol{\eta})\, ,
\label{equation:posterior}
\end{equation}$$

where **d** is the data. $P(\mathbf{s} | {\mathbf{H}}, \lambda_{\rm s})$ is a quadratic regularising prior on the source light distribution, $\mathbf{s}$, expressed in terms of a regularisation form, ${\mathbf H}$, and strength, $\lambda_{\rm s}$. The regularisation strength is a free hyper-parameter of the model. We refer to (cite: Vegetti:2009) and (cite: Powell:2022) for more details.

We considered three forms of regularisation: gradient, curvature, and area-weighted gradient. Gradient and curvature impose smoothness in the source surface brightness distribution by minimising the gradient or curvature between adjacent points on the Delaunay grid. The area-weighted gradient is a modification to the gradient regularisation that is weighted according to the triangle area, thereby allowing more freedom in high-magnification areas and less in regions of lower magnification. As was demonstrated by (cite: Suyu:2006), different source surface brightness distributions may require different forms of regularisation. We adopted the form and strength of regularisation that maximises the posterior (Eq. [\[equation:posterior\]](#equation:posterior)).

$P(\mathbf{d} | \mathbf{s}, \boldsymbol{\eta})$ is the likelihood, which we assumed to be Gaussian. As is described by (cite: Powell:2022), it encodes all the linear operators that describe the signal propagation processes from the source to the lensed image plane and the instrumental response; that is, $$\begin{equation}
\log{P(\mathbf{d} | \mathbf{s}, \boldsymbol{\eta})} = \frac{1}{Z} e^{ -\frac{1}{2}\chi^{2} }\, ,
\end{equation}$$ where $$\begin{equation}

    \chi^2 = \mathbf{s}_{\rm MAP}^{\rm T}\mathbf{L}^{\rm T}\mathbf{\tilde{C}}_{x}^{-1}\mathbf{L}\mathbf{s}_{\rm MAP} - 2 \mathbf{s}_{\rm MAP}^{\rm T}\mathbf{L}^{\rm T}\mathbf{d}_x + \mathbf{d}^{\rm T}\mathbf{C}^{-1}\mathbf{d}
\end{equation}$$ and $Z = \sqrt{\rm det(2\pi\mathbf{C})}$. $\mathbf{s}_{\rm MAP}$ is the maximum a posteriori source for the lensing operator, $\mathbf{L}(\boldsymbol{\eta})$. $\mathbf{d}$ is the data, $\mathbf{d}_x$ is the naturally weighted dirty image, and $\mathbf{C}$ is the noise covariance assuming uncorrelated, Gaussian noise. Due to the observing frequencies of these data and the antenna size of ALMA, the antenna response becomes significant just a few arcseconds from the pointing centre (which in our case is also the phase centre). We accounted for the loss of sensitivity using a Gaussian function with a half-power width of $1.13\times\lambda/D$, where $\lambda$ is the central frequency and $D$ is the antenna diameter (12 m).[^4] We implemented this as a diagonal operator, $\mathbf{P}$, such that the image-plane noise covariance takes the form $\mathbf{\tilde{C}}_{x}^{-1} = \mathbf{P}^{\rm T}\mathbf{D}^{\rm T}\mathbf{C}^{-1}\mathbf{D}\mathbf{P}$, where $\mathbf{D}$ is a discrete Fourier transform (the instrumental response). The terms $\mathbf{D}^{\rm T}\mathbf{C}^{-1}\mathbf{D}$ together are equivalent to a convolution with the dirty beam, which was performed using a fast Fourier transform.

The posterior probability distributions of the lens parameters, $\boldsymbol{\eta}$, source surface brightness, and source regularisation were inferred using MultiNest (cite: Feroz:2009; Feroz:2019). The Bayesian evidence was computed from the integral

$$\begin{equation}
    \mathcal{E} = \int {P(\mathbf{d} | \mathbf{s}, \boldsymbol{\eta})}\, {P(\mathbf{s}, \lambda_s)}\, {P(\boldsymbol{\eta})}\, \delta\lambda_s\, \delta\mathbf{s}\, \delta\boldsymbol{\eta}\, ,
\end{equation}$$

using 240 live points and importance sampling with a constant efficiency of 0.05 to improve the accuracy of the evidence calculation (cite: Feroz:2019). From tests on mock data, we have found that a minimum of 200 live points are required to recover the correct posterior for these data and the number of model parameters explored here (we note that this may be data-dependent).

Following an initial optimisation (see (cite: Vegetti:2009) for details), we set uniform priors for the lens model parameters at $\pm10$ to 20 percent of the optimised values, except the external shear, which was uniform in log space ($\log\Gamma\in[-3,-1]$) with a free position angle ($\theta_\Gamma\in[-90,90]$ deg). We marginalised over the source surface brightness and left the regularisation strength as a free parameter, which was uniform in log space.

For the multipole coefficients, we set uniform priors of $\pm0.01$. These priors are motivated by observations of isophotes of elliptical galaxies by (cite: Hao:2006) and the analysis of simulations by (cite: Kochanek:2004). Additionally, larger $m=4$ amplitudes paired with low ellipticity could produce exotic lensing configurations with six or more images (cite: Evans:2001; Hao:2006) and we are not aware of any such configurations reported for galaxy-scale lenses. We compared the Bayesian evidence from MultiNest for the different regularisation types to determine the appropriate type for the remainder of the analysis. We find that gradient regularisation gives the strongest evidence for SDP 81 and SPT 0538$-$50, while the area-weighted gradient gives stronger evidence for SPT 0532$-$50.

![](model_residuals_horiz.pdf)

![](kappa_diff.pdf)

# Results

## Evidence for complex angular structure

Table [\[table:nested\]](#table:nested) shows the marginalised posterior of the lens parameters and the relative evidence for the three datasets and the two different lens models tested here. The maximum a posteriori PL+MP lens model is shown in Fig. [2](#fig:lens_models) for each system. The differences in the convergence between the lens models are shown in Fig. [3](#fig:kappa_diff) and have convergence differences up to $\approx5$ to 10 percent at the Einstein radius.

The sources are not visually different between the PL and PL+MP models, as can be seen in Fig.[4](#fig:sources). Nevertheless, the PL+MP is preferred over a PL for all three lenses, with a relative Bayes factor (difference in $\ln{\mathcal{E}}$) of 28, 75, and 120 for SDP 81, SPT 0532$-$50 and SPT 0538$-$50, respectively (i.e. strong to decisive evidence in favour of more complex angular structure; (cite: Kass:1995)). In all cases, the improvement in model evidence is dominated by the increase in source regularisation rather than a change in the residuals (i.e. $\chi^{2}$). This indicates that the models can fit the data equally well, but the source can be smoother in the PL+MP case. This is consistent with the findings of (cite: Powell:2022), who compared various mass models for a system with a lensed radio jet. We interpret this as the regularisation trying to enforce the lens equation (i.e. better focus the source), as is discussed in Section 6.3 of (cite: Powell:2022).

![](source_plots_contour.pdf)

We find non-zero $m=3$ and $m=4$ amplitudes of $\approx0.01$ for all three lenses, suggesting a non-negligible departure from the PL model. The model parameters of the PL fitted with and without multipoles are generally in agreement for each of the three lens systems, although some parameters deviate by several sigma. Some notable differences are the positions of the mass centres for each system, the axis ratios, and position angles. Interestingly, the shear strength is largely consistent between the PL and PL+MP models, although the shear position angle does differ by several sigma for SDP 81 and SPT 0532. Altogether, we do not see clear evidence that the PL model is not compensating for some unmodelled angular structure when multipoles are not included, in contrast with the findings of (cite: Etherington:2023).

We find that the PL+MP model posterior for SDP 81 differs significantly in ellipticity, external shear, and multipole amplitudes from that of (cite: Hezaveh:2016) using the same set of observations. The underlying PL model is similar to those of previous studies using these visibility data from baselines $<2$ km (cite: Rybak:2015a) and deconvolved images (cite: Dye:2015; Inoue:2016; Tamura:2015; Wong:2015). We were not able to find a good model for the data using the PL+MP parameters reported by (cite: Hezaveh:2016).

## Isophote and isodensity shapes

Anisotropic shapes are a known feature of the stellar distribution of elliptical galaxies. Since stars compose the vast majority of the baryonic matter of elliptical galaxies, by measuring stellar isophotes for these lens galaxies we can test to what extent the mass-density distribution from lensing may be shaped by baryons.

For SDP 81, there is lensed emission detected in the F160W HST/WFC3 imaging that is blended with the lens light (cite: Rybak:2015b). We modelled this lensed emission with the PL lens model (Table [\[table:nested\]](#table:nested)) while simultaneously fitting the lens galaxy light (see (cite: Ritondale:2019a) for details of this methodology). We then subtracted model lensed emission from the data so as not to include it in our subsequent isophote fitting. After masking the light from any interposing objects, we used the isophote tool in the Python package photutils (cite: Bradley:2023) that uses an iterative method described by (cite: Jedrzejewski:1987) to fit elliptical isophotes to the lens galaxy light. These Fourier modes have the function

$$\begin{equation}
    R_m(\theta) = R_0 + a_m \sin(m\theta)+ b_m\cos(m\theta) 
\end{equation}$$

in polar coordinates, where $m$ is the harmonic mode ($m=3,4$) and $R_0$ is the elliptical path for that isophote at the angles defined by $\theta$. It should be noted that the isodensity multipole parameters are not the same as those of the lens model parameters because the multipoles in the lens model are spherical and the elliptical power-law model induces a radial dependence. We converted the multipole shape parameters to an amplitude and position angle for ease of interpretation; the amplitude of a Fourier mode is described by

$$\begin{equation}
    \eta_m = \sqrt{a_m^2 + b_m^2}\, ,
\end{equation}$$ and the position angle is described by $$\begin{equation}
    \phi_m = \frac{1}{m} \arctan{\frac{b_m}{a_m}}\, .
\end{equation}$$

Boxy or discy shapes can be discerned from the difference between $\eta_4$ and the ellipticity position angle ($\theta_q$), where 45, 135 deg is a truly boxy shape and 0, 90 deg is a truly discy shape.

Fig. [5](#fig:isophotes) shows the isophote fits to the F110W and F160W HST/WFC3 imaging of the three lens galaxies. F110W and F160W have similar isophote fits. However, SPT 0532$-$50 has the most scatter and the least well-constrained isophotes because the lens is significantly fainter than those of the other two lens systems.

A comparison of the total lens model convergence (PL+MP; isodensity) and the F160W isophotes is shown in Fig. [6](#fig:converence_isophotes). In addition, we show comparisons of the isophote shape parameters and isodensity parameters from lensing as a function of galaxy radius for the three lens systems in Fig. [7](#fig:isophote_params).

None of the lensing galaxies are truly boxy or discy in their isodensity shapes, but rather somewhere in between. However, those of SPT 0532$-$50 appear quite boxy (Fig. [6](#fig:converence_isophotes)). SDP 81 is largely consistent in terms of its isophote and isodensity shapes, while SPT 0532$-$50 and SPT 0548$-$50 show disagreement. For SPT 0532$-$50, the isophote ellipticity position angle is offset by about 40 deg relative to the isodensity profile at the Einstein radius, and for SPT 0538$-$50 this offset is around 25 deg.

In all cases, the ellipticities ($1-q$) are in good agreement at the Einstein radius. We also see that the isophotes for all three lens galaxies have some change in ellipticity and ellipticity position angle with radius, which is not accounted for in the lens model. We tested whether the position angles of the isophotes could be used to describe the mass distribution for SPT 0532$-$50 and SPT 0538$-$50, given the multipole flexibility. This was done by fixing the ellipticity position angle to that of the isophotes and leaving all other parameters free to optimise. The best fits result in significant residual emission and a more disrupted source, confirming that the isophote ellipticity position angles are indeed inconsistent with those of the total mass distribution.

![](isophote_residuals_together.pdf)

![](convergence_isophotes_together.pdf)

![](isophote_plots_together.pdf)

# Discussion

## Origin of the angular structure

The three lenses in our sample are massive elliptical galaxies, based on their optical colours and morphologies. Massive elliptical galaxies are generally slow, anisotropic rotators characterised by triaxial shapes, and are frequently found to have boxy or discy isophote morphologies to their rest-frame optical stellar emission (cite: Bender:1988; Cappellari:2016). These features are likely reflected to some extent in their isodensity structure. Therefore, one might assume that this could explain the low-amplitude multipole components that we detect in our lensing analysis if the total mass follows that of the stellar morphology.

We find isodensity multipole amplitudes in the range of 0.1 to 1 percent, which is comparable to what is typically seen in isophotes of elliptical galaxies (cite: Kormendy:1989; Kormendy:2009), and similar to what has been explored in recent theoretical work (cite: O’Riordan:2023; VandeVyvere:2022; Cohen:2024). However, when compared directly with these galaxies, there are minor differences in isodensity and isophote shapes, suggesting that their stellar distributions are not completely consistent with those of the total projected mass distributions. As the infrared stellar emission likely traces the vast majority of the baryonic mass in the inner halo, any differences could be caused by a different shape to the galaxy’s dark matter halo that can contribute significantly to the density at the Einstein radius (cite: Auger:2010; Sonnenfeld:2012; Oldham:2018).

Numerical simulations predict that the shape of a dark matter halo is influenced by baryonic structures and its merger history (cite: Prada:2019; Chua:2019). As a result, dark matter haloes can exhibit ellipticity, twists, and misalignment with baryons that increase with radius (cite: Liao:2017; Emami:2021; Han:2023). However, these simulations do not resolve the inner radii probed by galaxy-scale lensing, nor do they resolve them well, so they do not make clear predictions for our data.

The lens galaxies in this work may be part of groups in which the halo is disturbed by ongoing mergers and interactions: SPT 0538$-$50 and SDP 81 have several close galaxies in projection in the HST imaging (these have been masked in Fig. [5](#fig:isophotes)) that suggest the lens is the central galaxy of a group (we note that the redshifts of any neighbours are not reported in catalogues, so it is not necessarily clear what they are or whether they are associated). On the other hand, this does not appear to be the case for SPT 0532$-$50, which exhibits the strongest misalignment between its stellar and total mass distribution while being seemingly isolated. The lens of SPT 0532$-$50 is significantly less massive than the others and has a higher redshift, so it may be in a different stage of its evolution (cite: Despali:2014; Cataldi:2023) or follow a different formation pathway (cite: Penoyre:2017; Lagos:2018).

Alternatively, rather than the halo of the lens itself, the multipoles could be caused by density perturbations extrinsic to the lens galaxy. Galaxies at a different redshift close in projection could also be perturbing the lensed images. Here, the distributions of these nearby galaxies do not appear to correlate with the ellipticity position angle from lensing: for example, SPT 0532$-$50 demonstrates the largest offset, but no nearby galaxies are apparent in the infrared imaging. However, these perturbers need not be directly observable; (cite: O’Riordan:2023) find that the anisotropic distribution of dark sub-haloes may be interpreted as third and fourth-order multipoles in the lensing convergence. Line-of-sight interloper haloes may also induce multipole structure, as they produce a similar lensing effect and are expected to contribute significantly to the lensing perturbations (cite: Despali:2018; Amorisco:2022). Such a scenario could be occurring for SDP 81 and SPT 0538$-$50, where the $m=4$ amplitudes are inconsistent with those of the light. Additionally, SPT 0532$-$50, where the total mass shows the largest offset from the light, is also at the highest lens redshift, where there will be more lensing signal from low-mass haloes along the line of sight (cite: Despali:2018).

While there are several possible contributions to the inconsistency between the isodensity and isophotal shapes for these lens galaxies, it may be possible to discern these contributions with non-analytical lens modelling methods (e.g. (cite: Vegetti:2009; Vernardos:2022; Galan:2022)) if different mass components produce different lensing signatures. For example, (cite: Galan:2022) used a technique involving wavelets to demonstrate that it may be possible to differentiate the lensing signal induced by a population of low-mass haloes from an intrinsic multipole structure in the lensing galaxy, which could constrain dark matter models. Additionally, intrinsic multipole shapes or the lack thereof in the lens galaxies themselves may provide a test of self-interacting dark matter (cite: Brinckmann:2018), provided that the baryons do not significantly affect the shape of haloes in the regions of interest (cite: Despali:2022b).

## Consequences for lensing studies

Complex angular structure could have significant effects on lensing observables that are relevant for all lines of research in gravitational lensing, particularly measuring the Hubble constant from time delays (e.g. (cite: Wong:2020)) and constraints on dark matter models via the detection of low-mass dark matter haloes (e.g. (cite: Ritondale:2019b; Gilman:2020a)). Recent works have attempted to address this by considering composite models consisting of the observed stellar component (with a constant mass-to-light ratio) and an elliptical dark matter profile (e.g. (cite: Rusu:2020; Nightingale:2022; Chen:2022)), or explored the consequences of boxy and discy shapes (cite: VandeVyvere:2022). However, composite lens models, even when the two components are allowed to be misaligned, only allow for additional angular complexity of order $m=2$. Studies that consider the consequences of higher-order angular structure on lensing observables typically consider $m=4$ and not $m=3$ (cite: VandeVyvere:2022; Nightingale:2022; Gilman:2023), and often limit $m=4$ structure to true boxy or discy shapes (i.e. $\theta_q - \phi_4 = 0$). We have shown here that these models do not encompass the true angular complexity of lensing galaxies. Future work involving a larger sample of lenses is needed to provide statistics on the level of complex angular structure in lensing galaxies. Such data will provide an essential test of systematic errors on cosmological constraints derived from strong gravitational lensing.

# Conclusions

The singular ellipsoidal power-law model has been the predominant model in galaxy-scale strong lensing studies for decades. However, as observatories reach higher angular resolutions, the data becomes sensitive to deviations from this simple assumption. We have shown that significant multipole expansions of the power-law model up to the fourth order with Bayes factors between 28 and 120 can be measured with ALMA observations at an angular resolution of $\approx$ 30 mas. While this is significantly lower evidence than for very-long-baseline interferometry (VLBI) data at an angular resolution of $\sim$mas (cite: Powell:2022), the current relative abundance of lensed dusty star-forming galaxies compared to extended arcs in VLBI observations means that future observations with ALMA could provide a statistically meaningful sample of lensing angular structure. Additionally, future surveys, such as with *Euclid* and the Square Kilometre Array, will allow for the selection of a large sample of useful targets for high-resolution interferometry (cite: Serjeant:2014; McKean:2015).

Previous constraints on dark matter models via gravitationally lensed arcs have relied on rare individual detections of low-mass perturbers to constrain the shape of the dark matter halo mass function (cite: Vegetti:2014; Vegetti:2018; Ritondale:2019a; Enzi:2021). Searches for such perturbers could be susceptible to systematic biases if the angular structure in the lens is not accounted for (cite: Nightingale:2022). Indeed, (cite: O’Riordan:2023) used mock observations to show that angular structure in the lens could create false detections in HST-like data. Here we find, using data of a higher quality than those provided by the HST, that angular structure with comparable amplitudes does exist in such systems, and can be accounted for using multipoles. The differences we find between the lensing angular structure and stellar isophotes suggest a contribution from non-baryonic mass structure, which could be caused by a misalignment of the galaxy’s dark matter halo (cite: Liao:2017) and/or the influence of a population of low-mass perturbers (cite: O’Riordan:2023). Our future work will use pixellated potential corrections to shed further light on the nature of the complex angular structure identified for the sample of lenses presented in this paper.

# Acknowledgements

HRS, DMP and SV acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (LEDA: grant agreement No. 758853). JPM and DW acknowledge support from the Netherlands Organization for Scientific Research (NWO) (Project No. 629.001.023) and the Chinese Academy of Sciences (CAS) (Project No. 114A11KYSB20170054). This work is based on the research supported in part by the National Research Foundation of South Africa (Grant Number: 128943). Our analysis made use of SciPy, NumPy, Matplotlib, Astropy and Photutils packages for Python (cite: Virtanen:2020; Harris:2020; Hunter:2007; Astropy:2013; Astropy:2018; Bradley:2023). Figs. [1](#fig:clean_images), [2](#fig:lens_models), [5](#fig:isophotes) colour scheme courtesy of Rebecca Levy following (cite: Levy:2021). We used ALMA data with project codes 2011.0.00016.SV and 2016.1.01374.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We used observations made with the NASA/ESA *Hubble* Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with proposal IDs 12194 and 12659.

90 natexlab

(ref: Vlahakis2015) ALMA Partnership, Vlahakis, C., Hunter, T. R., et al. 2015, ApJL, 808, L4

(ref: Amorisco:2022) Amorisco, N. C., Nightingale, J., He, Q., et al. 2022, MNRAS, 510, 2464

(ref: Astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Auger:2010) Auger, M. W., Treu, T., Gavazzi, R., et al. 2010, ApJL, 721, L163

(ref: Bender:1988) Bender, R., Doebereiner, S., & Moellenhoff, C. 1988, A&AS, 74, 385

(ref: Bender:1989) Bender, R., Surma, P., Doebereiner, S., Moellenhoff, C., & Madejsky, R. 1989, A&A, 217, 35

(ref: Bradley:2023) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2023, astropy/photutils: 1.8.0

(ref: Brinckmann:2018) Brinckmann, T., Zavala, J., Rapetti, D., Hansen, S. H., & Vogelsberger, M. 2018, MNRAS, 474, 746

(ref: Cao:2022) Cao, X., Li, R., Nightingale, J. W., et al. 2022, , 22, 025014

(ref: Cappellari:2016) Cappellari, M. 2016, ARA&A, 54, 597

(ref: casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Cataldi:2023) Cataldi, P., Pedrosa, S. E., Tissera, P. B., et al. 2023, MNRAS, 523, 1919

(ref: Chaware:2014) Chaware, L., Cannon, R., Kembhavi, A. K., Mahabal, A., & Pandey, S. K. 2014, ApJ, 787, 102

(ref: Chen:2022) Chen, G. C. F., Fassnacht, C. D., Suyu, S. H., et al. 2022, MNRAS, 513, 2349

(ref: Chua:2019) Chua, K. T. E., Pillepich, A., Vogelsberger, M., & Hernquist, L. 2019, MNRAS, 484, 476

(ref: Cohen:2024) Cohen, J. S., Fassnacht, C. D., O’Riordan, C. M., & Vegetti, S. 2024, arXiv e-prints, arXiv:2403.08895

(ref: Collett:2018) Collett, T. E., Oldham, L. J., Smith, R. J., et al. 2018, Science, 360, 1342

(ref: Congdon:2005) Congdon, A. B. & Keeton, C. R. 2005, MNRAS, 364, 1459

(ref: Despali:2014) Despali, G., Giocoli, C., & Tormen, G. 2014, MNRAS, 443, 3208

(ref: Despali:2018) Despali, G., Vegetti, S., White, S. D. M., Giocoli, C., & van den Bosch, F. C. 2018, MNRAS, 475, 5424

(ref: Despali:2022b) Despali, G., Walls, L. G., Vegetti, S., et al. 2022, MNRAS, 516, 4543

(ref: Dye:2015) Dye, S., Furlanetto, C., Swinbank, A. M., et al. 2015, MNRAS, 452, 2258

(ref: Emami:2021) Emami, R., Hernquist, L., Alcock, C., et al. 2021, ApJ, 918, 7

(ref: Enzi:2021) Enzi, W., Murgia, R., Newton, O., et al. 2021, MNRAS, 506, 5848

(ref: Etherington:2023) Etherington, A., Nightingale, J. W., Massey, R., et al. 2023, arXiv e-prints, arXiv:2301.05244

(ref: Evans:2001) Evans, N. W. & Witt, H. J. 2001, MNRAS, 327, 1260

(ref: Evans:2003) Evans, N. W. & Witt, H. J. 2003, MNRAS, 345, 1351

(ref: Feroz:2009) Feroz, F., Hobson, M. P., & Bridges, M. 2009, MNRAS, 398, 1601

(ref: Feroz:2019) Feroz, F., Hobson, M. P., Cameron, E., & Pettitt, A. N. 2019, The Open Journal of Astrophysics, 2, 10

(ref: Galan:2022) Galan, A., Vernardos, G., Peel, A., Courbin, F., & Starck, J. L. 2022, A&A, 668, A155

(ref: Geach:2023) Geach, J. E., Lopez-Rodriguez, E., Doherty, M. J., et al. 2023, Nature, 621, 483

(ref: Gilman:2020a) Gilman, D., Birrer, S., Nierenberg, A., et al. 2020, MNRAS, 491, 6077

(ref: Gilman:2023) Gilman, D., Zhong, Y.-M., & Bovy, J. 2023, Phys. Rev. D, 107, 103008

(ref: Han:2023) Han, J. J., Semenov, V., Conroy, C., & Hernquist, L. 2023, ApJL, 957, L24

(ref: Hao:2006) Hao, C. N., Mao, S., Deng, Z. G., Xia, X. Y., & Wu, H. 2006, MNRAS, 370, 1339

(ref: Harris:2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: He:2023) He, Q., Nightingale, J., Robertson, A., et al. 2023, MNRAS, 518, 220

(ref: Hezaveh:2016) Hezaveh, Y. D., Dalal, N., Marrone, D. P., et al. 2016, ApJ, 823, 37

(ref: Hsueh:2020) Hsueh, J. W., Enzi, W., Vegetti, S., et al. 2020, MNRAS, 492, 3047

(ref: Hunter:2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: Inoue:2016) Inoue, K. T., Minezaki, T., Matsushita, S., & Chiba, M. 2016, MNRAS, 457, 2936

(ref: Jedrzejewski:1987) Jedrzejewski, R. I. 1987, MNRAS, 226, 747

(ref: Kass:1995) Kass, R. E. & Raftery, A. E. 1995, Journal of the American Statistical Association, 90, 773

(ref: King:1978) King, I. R. 1978, ApJ, 222, 1

(ref: Kochanek:2004) Kochanek, C. S. & Dalal, N. 2004, ApJ, 610, 69

(ref: Kormendy:1989) Kormendy, J. & Djorgovski, S. 1989, ARA&A, 27, 235

(ref: Kormendy:2009) Kormendy, J., Fisher, D. B., Cornell, M. E., & Bender, R. 2009, ApJS, 182, 216

(ref: Lagos:2018) Lagos, C. d. P., Schaye, J., Bahé, Y., et al. 2018, MNRAS, 476, 4327

(ref: Levy:2021) Levy, R. C., Bolatto, A. D., Leroy, A. K., et al. 2021, ApJ, 912, 4

(ref: Liao:2017) Liao, S., Gao, L., Frenk, C. S., Guo, Q., & Wang, J. 2017, MNRAS, 470, 2262

(ref: Liller:1960) Liller, M. H. 1960, ApJ, 132, 306

(ref: Liller:1966) Liller, M. H. 1966, ApJ, 146, 28

(ref: McKean:2015) McKean, J., Jackson, N., Vegetti, S., et al. 2015, in Advancing Astrophysics with the Square Kilometre Array (AASKA14), 84

(ref: Negrello:2010) Negrello, M., Hopwood, R., De Zotti, G., et al. 2010, Science, 330, 800

(ref: Nightingale:2022) Nightingale, J. W., He, Q., Cao, X., et al. 2023, MNRAS, 527, 10480

(ref: Oldham:2018) Oldham, L. J. & Auger, M. W. 2018, MNRAS, 476, 133

(ref: O’Riordan:2023) O’Riordan, C. M. & Vegetti, S. 2024, MNRAS, 528, 1757

(ref: ORiordan:2020) O’Riordan, C. M., Warren, S. J., & Mortlock, D. J. 2020, MNRAS, 496, 3424

(ref: Pasquali:2006) Pasquali, A., Ferreras, I., Panagia, N., et al. 2006, ApJ, 636, 115

(ref: Penoyre:2017) Penoyre, Z., Moster, B. P., Sijacki, D., & Genel, S. 2017, MNRAS, 468, 3883

(ref: Powell:2021) Powell, D., Vegetti, S., McKean, J. P., et al. 2021, MNRAS, 501, 515

(ref: Powell:2022) Powell, D. M., Vegetti, S., McKean, J. P., et al. 2022, MNRAS, 516, 1808

(ref: Powell:2023) Powell, D. M., Vegetti, S., McKean, J. P., et al. 2023, MNRAS, 524, L84

(ref: Prada:2019) Prada, J., Forero-Romero, J. E., Grand, R. J. J., Pakmor, R., & Springel, V. 2019, MNRAS, 490, 4877

(ref: Ritondale:2019b) Ritondale, E., Auger, M. W., Vegetti, S., & McKean, J. P. 2019a, MNRAS, 482, 4744

(ref: Ritondale:2019a) Ritondale, E., Vegetti, S., Despali, G., et al. 2019b, MNRAS, 485, 2179

(ref: Rizzo:2018) Rizzo, F., Vegetti, S., Fraternali, F., & Di Teodoro, E. 2018, MNRAS, 481, 5606

(ref: Rizzo:2021) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952

(ref: Rusu:2020) Rusu, C. E., Wong, K. C., Bonvin, V., et al. 2020, MNRAS, 498, 1440

(ref: Rybak:2015a) Rybak, M., McKean, J. P., Vegetti, S., Andreani, P., & White, S. D. M. 2015a, MNRAS, 451, L40

(ref: Rybak:2015b) Rybak, M., Vegetti, S., McKean, J. P., Andreani, P., & White, S. D. M. 2015b, MNRAS, 453, L26

(ref: Serjeant:2014) Serjeant, S. 2014, ApJL, 793, L10

(ref: Sonnenfeld:2012) Sonnenfeld, A., Treu, T., Gavazzi, R., et al. 2012, ApJ, 752, 163

(ref: Spilker:2016) Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112

(ref: Spingola:2018) Spingola, C., McKean, J. P., Auger, M. W., et al. 2018, MNRAS, 478, 4816

(ref: Stacey:2022) Stacey, H. R., Costa, T., McKean, J. P., et al. 2022, MNRAS, 517, 3377

(ref: Suyu:2006) Suyu, S. H., Marshall, P. J., Hobson, M. P., & Blandford, R. D. 2006, MNRAS, 371, 983

(ref: Tamura:2015) Tamura, Y., Oguri, M., Iono, D., et al. 2015, PASJ, 67, 72

(ref: Tessore:2015) Tessore, N. & Metcalf, R. B. 2015, A&A, 580, A79

(ref: VandeVyvere:2022) Van de Vyvere, L., Gomer, M. R., Sluse, D., et al. 2022, A&A, 659, A127

(ref: Vegetti:2023) Vegetti, S., Birrer, S., Despali, G., et al. 2023, arXiv e-prints, arXiv:2306.11781

(ref: Vegetti:2018) Vegetti, S., Despali, G., Lovell, M. R., & Enzi, W. 2018, MNRAS, 481, 3661

(ref: Vegetti:2009) Vegetti, S. & Koopmans, L. V. E. 2009, MNRAS, 392, 945

(ref: Vegetti:2014) Vegetti, S., Koopmans, L. V. E., Auger, M. W., Treu, T., & Bolton, A. S. 2014, MNRAS, 442, 2017

(ref: Vernardos:2022) Vernardos, G. & Koopmans, L. V. E. 2022, MNRAS, 516, 1347

(ref: Virtanen:2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Wong:2020) Wong, K. C., Suyu, S. H., Chen, G. C. F., et al. 2020, MNRAS, 498, 1420

(ref: Wong:2015) Wong, K. C., Suyu, S. H., & Matsushita, S. 2015, ApJ, 811, 115

(ref: Yang:2019) Yang, C., Gavazzi, R., Beelen, A., et al. 2019, A&A, 624, A138

[^1]: E-mail: hannah.stacey@eso.org

[^2]: <https://almascience.eso.org/alma-data/science-verification>

[^3]: Multipoles of order 0 and 2 are implicit in Eq. [\[eq:PL\]](#eq:PL).

[^4]: ALMA Cycle 7 Technical Handbook <https://arc.iram.fr/documents/cycle7/ALMA_Cycle7_Technical_Handbook.pdf>

</paper>

Write the methods card for this paper.