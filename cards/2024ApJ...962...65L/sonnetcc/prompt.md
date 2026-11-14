# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...962...65L\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...962...65L",
 "title": "Unveiling a Hidden Bar-like Structure in NGC 1087: Kinematic and Photometric Evidence Using MUSE/VLT, ALMA, and JWST",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "López-Cobá, Carlos",
 "n_authors": 3,
 "arxiv_id": "2312.04098",
 "doi": "10.3847/1538-4357/ad152a",
 "alma_projects_linked_by_archive": [
  "2018.1.01651.S"
 ]
}
```

Paper text:
<paper>
# Unveiling a hidden bar-like structure in NGC 1087: kinematic and photometric evidence using MUSE/VLT, ALMA and JWST

## Abstract

We report a faint non-axisymmetric structure in NGC 1087 through the use of JWST Near Infrared Camera (NIRCam), with an associated kinematic counterpart observed as an oval distortion in the stellar velocity map, H$\alpha$ and CO $J=2\rightarrow1$ velocity fields. This structure is not evident in the MUSE optical continuum images but only revealed in the near-IR with the F200W and F300M band filters at $2\mu$m and $3\mu$m respectively. Due to its elongation, this structure resembles a stellar bar although with remarkable differences with respect to conventional stellar bars. Most of the near-IR emission is concentrated within $6\ensuremath{''}~\sim500$ pc with a maximum extension up to 1.2 kpc. The spatial extension of the large-scale non-circular motions is coincident with the bar, which undoubtedly confirms the presence of a non-axisymmetric perturbation in the potential of NGC 1087. The oval distortion is enhanced in CO due to its dynamically cold nature rather than in H$\alpha$. We found that the kinematics in all phases including stellar, ionized and molecular, can be described simultaneously by a model containing a bisymmetric perturbation; however, we find that an inflow model of gas along the bar major axis is also likely. Furthermore the molecular mass inflow rate associated can explain the observed star formation rate in the bar. This reinforces the idea that bars are mechanisms for transporting gas and triggering star formation. This work contributes to our understanding of non-axisymmetry in galaxies using the most sophisticated data so far.

# Introduction

Stellar bars or “bars” are one of the most visual signs of non-axisymmetry in galaxies (cite: 3RC). Like other morphological structures in galaxies, bars are not well defined, although they are relatively easy to identity in composite images because of their bar-shape structure (cite: Masters2011; Cheung2013), and their prominent bar dust lanes (cite: Athanassoula1992).

NGC 1087 is a clear example where the combination of high spatial resolution data allowed us to reveal a hidden bar that is only observed in the near-infrared (NIR).

The James Webb Space Telescope (JWST) is allowing us to reveal structures not seen before due to the lack of resolution and sensitivity. Their infrared bands are prone to detect the emission from old-stellar structures like bars $\sim10$ Gyr (cite: sanchez-blazquez11).

In the optical, dust obscuration can prevent their detection, affecting the global statistics of galaxies hosting bars in the nearby Universe (cite: sell93). Apart from their optical and NIR characteristics, bars leave imprints of non-axisymmetry in the kinematics of gas and stars (cite: Wong2004; fathi05; LopezCoba2022); thus studying the dynamical effects of bars at local scales is crucial for understanding the role they play in galaxy evolution.

A comprehensive study of bars could be addressed if kinematics and wide-range photometric observations were accessible for a considerably large sample of galaxies. Yet, spatial resolution plays an important role in separating the different structural components of galaxies.

For example, the large integral field spectroscopic surveys like CALIFA (cite: sanchez12a) or MaNGA (cite: ManGA), although providing a large statistical sample of galaxies, their nominal resolution of $2.5\ensuremath{''}\sim1$ kpc inhibits a detailed study of individual galaxies, while biasing the sample towards bar-lengths larger than the FWHM resolution.

In a similar manner NIR photometric and optical catalogs provide resolution of few arcseconds which again limits the detection of small bars (cite: S4G).

In this work, we make use of the most sophisticated data to unravel the detection of a bar in NGC 1087. This paper is structured as follows: in Section 2 we describe the data and data analysis; in Section 3 we address the detection of a faint stellar bar in the infrared while their ionized and molecular counterpart are addressed in Section 4; Section 5 describes the oval distortion and in Section 6 we present the discussion and conclusions.

# Data and Data analysis

NGC 1087 is an intermediate Sc galaxy located at 14 Mpc (cite: Kourkchi2017); at this distance the physical spatial resolution is 68 pc$\mathrm{~arcsec^{-1}}$.

This work is based on public data from the Multi-Unit Spectroscopic Explorer (cite: Bacon2010); data from the JWST Near Infrared Camera (NIRCam); and ALMA CO $J=2\rightarrow$1 observations, in particular we used the data products from the PHANGS–ALMA survey (cite: Leroy2021a; Leroy2021b), namely moments 0 and 1.

The MUSE-VLT data was obtained as part of the recent release of the MUSE-PHANGS datacubes (cite: PHANGS_doi; Emsellem2022). MUSE is an integral field spectrograph which provides spatially resolved spectra over a $1\ensuremath{'}\times1\ensuremath{'}$ field of view (FoV), covering the optical spectrum, with a spectral resolution at full width at half maximum (FWHM) of $\sim2.6$Å. The estimated spatial resolution of the $2\ensuremath{'}\times3\ensuremath{'}$ MUSE mosaic covering NGC 1087 is not worse than $0.9\ensuremath{''}$/FWHM (cite: Emsellem2022).

We used fully calibrated data products from JWST from the JWST Science Calibration Pipeline version 1.10.1 (cite: bushouse). Specifically, we made use of the PHANGS-JWST first result products (cite: PHANGS-JWST_doi), namely, the NIRCam F200W filter (FWHM $\sim0.05\ensuremath{''}$ and $0.031\ensuremath{''}/\mathrm{pixel}$ sampling), which has its nominal wavelength at $1.99\mu$m, in addition to the F360M and F335M band filters to trace the stellar continuum. Finally the spatial resolution of the ALMA data is $1.60\ensuremath{''}$/FWHM following (cite: Leroy2021a).

The CO moment 0 map was transformed to surface density ($\mathrm{ \Sigma_{mol} }$), assuming a standard Milky Way $\mathrm{ \alpha_\mathrm{CO}^{1-0}=4.35\,M_{\odot} /pc^2 }$ conversion factor and $\mathrm{ \Sigma_{mol}[M_\odot pc^2] = 6.7\, I_{CO(2-1)}[K\,km/s]} \cos i$ (cite: Leroy2021a), with $i$ being the disk inclination angle estimated in $44.5^{\circ}$.

The MUSE data analysis was made with the pypipe3d tool (cite: Lacerda2022). In short, pypipe3d performs a decomposition of the observed stellar spectra into multiple simple stellar populations (SSPs) each with different age and metalicities. For concordance with (cite: Emsellem2022), we use the same stellar libraries based on the extended MILES (cite: EMILES), FWHM $=2.5$Å;

We convolved the spectral resolution of the SSPs to that of the MUSE line-spread function (cite: Bacon2017). To increase the signal-to-noise (SN) of the stellar continuum, we performed a Voronoi binning-segmentation on a 2D-slice centered around the V-band, ensuring bin-sizes of the order of the MUSE-FWHM resolution and SN $\sim50$. This binned map will serve to compute different properties of the underlying stellar continuum, while the ionized gas properties are analyzed in a spaxel-wise sense.

The result of pypipe3d is a set of maps comprising information about the stellar populations (stellar velocity, stellar mass, among others products), and the ionized gas (emission-line fluxes including: H$\alpha$, H$\beta$, \[ S II \]$\lambda6717,6731$, \[ N II \]$\lambda6584$, \[ O III \]$\lambda5007$, \[ O I \]$\lambda6300$, emission-line velocities, equivalent widths etc); see (cite: Lacerda2022) for a thorough description of the analysis and dataproducts. From this analysis we estimate the stellar mass of this object in $\mathrm{ \log M_{\star}/M_{\odot} = 9.9}$.

![](main_fig.png)

# FAINT stellar bar

The optical continuum image of NGC 1087 exhibits a bright, fuzzy and featureless nucleus with several dust lanes as revealed by the $gri$ MUSE image in Figure [1](#fig:main), because of that it is unclear whether this object shows a stellar bar in the optical. Two bright spots are observed in the central region where the near-IR (NIR) nucleus is found.

Unlike the majority of galaxies hosting stellar bars, NGC 1087 does not show a well defined bar, nucleus neither a star forming ring (cite: 3RC).

Conversely, the high spatial resolution from the F200W imaging filter allows to resolve a clear elongated and clumpy structure of presumably stellar clusters aligned along a preferential position angle (P.A.), which differs from the disk orientation[^1] $\phi_{disk}^{\prime} = 359^{\circ}$, as observed in Figure [1](#fig:main). At $2\mu$m this structure resembles a faint stellar bar and it is obscured in the optical due to dust absorption.

F200W traces mostly stellar continuum, hence, it is expected that most of the continuum emission along this structure comes from old stars (cite: Starburst99).

Elliptical isophotes with variable position angle and ellipticity ($\varepsilon^{\prime}$) show a preferential alignment of the $2\mu$m emission as observed in the top-right panel from Figure [1](#fig:main).

![image](xs_phot.png)\
![image](xs_phot2.png)

![](bpt.png)

![](metallicity.png)

![](ssfr.png)

![](fig2)

## Bar light modeling

The method adopted here is similar to the non-parametric method from (cite: Reese2007), which is the same algorithm used by $\mathtt{XS}$ (cite: XookSuut) for extracting the different velocities in the kinematic models, as we explain in the following sections. Our non-parametric model minimizes the function $\chi^2 = (I_{obs}-I_k(r) w_k(r))^2$, where $I_{obs}$ is the observed intensity map, $I_k$ represents a set of intensities that will be estimated at different annuli, and $w_k$ is a set of weighting factors that will serve for performing a linear interpolation between the estimated $I_k$ intensities. The implementation on the F200W and F300M band filters is shown in Figure [2](#fig:xs_phot).

The NIR light from the bar-structure can be successfully modeled by an elliptical light distribution with with a constant orientation in the sky. The P.A. of such ellipse is $\phi_{bar}^{\prime}=305^{\circ}$[^2] and $\varepsilon^{\prime}_{bar} = 0.5$, as shown in Figure [2](#fig:xs_phot). From this analysis the estimated semi-major axis length of the NIR bar is $a_{bar}^{\prime} = 14\ensuremath{''}$ or $18\ensuremath{''} \sim 1.2$ kpc[^3] on the disk at the considered distance. However, this structure is very diffuse, with most of the 2$\mu$m emission $\sim70\%$, concentrated within the inner $6\ensuremath{''}\sim500$ pc. The latter region encloses the two bright spots observed in the MUSE optical continuum images.

# Ionized and molecular gas

The central panel of Figure [1](#fig:main) shows the ionized gas distribution traced by the H$\alpha$, \[ S II \] and \[ O III \] emission-line fluxes.

In general, galaxies hosting stellar bars do not frequently present cold or warm gas along the bar. This is often explained as a lost of angular momentum after the gas encounters the offset ridges, resulting in an infall of gas towards a central ring (cite: Athanassoula1992).

NGC 1087 shows plenty of ionized gas throughout the disk and within the bar region. Furthermore, as we will see later, multiple enhanced CO bloops are spatially coincident with the F200W emission.

To investigate the dominant ionizing source along the bar-like structure we made use of line-ratios sensitive to the ionization, in particular the \[ O I \]6300/H$\alpha$ and \[ O III \]/H$\beta$. The \[ O I \]6300/H$\alpha$ ratio has the advantage of being a good indicator of the presence of shocks.

The top panel from Figure [3](#fig:bpt) shows these line-ratios color-coded with the $2\mu$m emission. The observed ionized gas is compatible with being produced by star-formation (SF) according to the (cite: Kewley2006) demarcation line.

However, dust lanes in bars are often associated with shocks as a result of the complex gas dynamics (cite: Athanassoula1992). The bar-region in NGC 1087 shows several dust lanes, thus we adopt shock models to investigate whether shock ionization can reproduce the observed line ratios. For this purpose we used the photoionization grids from MAPPINGS V (cite: mappingsv) computed by (cite: Alarie2019); we adopt the (cite: Gutkin2016) metallicities. The latter parameter was set from the oxygen gas-phase abundance, adopting the (cite: Pilyugin2016) calibrator based on strong emission-lines (see Figure [4](#fig:metal)). For the bar-region we find $\mathrm{ 12+\log O/H \sim 8.5}$ corresponding to $\mathrm{ Z_{ISM} = 0.008 }$ in the (cite: Gutkin2016) models. For this metallicity, the predicted emission-line intensities from shock models can not explain the observed \[ O I \]/H$\alpha$ line ratios as observed in the top panel of Figure [3](#fig:bpt).

Thus, if shocks are happening in the bar-region, then their optical emission is not expected to be the dominant ionizing source. Although there is still a possibility that a combination of SF plus shocks could contribute to the observed line-ratios (cite: Davies2016).

Additionally, Figure [3](#fig:bpt) shows the equivalent width of H$\alpha$ (EW($\rm{H}\alpha$)) for the ionized gas in the bar-region. Hot, old, and low-mass evolved stars are characterized for producing EW($\rm{H}\alpha$)$~\lesssim 3$Å  (cite: Stasinska2008; Cid2010; Lacerda2018).

The large values of EW($\rm{H}\alpha$) $\gtrsim 100$ Å found in the bar, can not be explained by the ionizing continuum emitted by this population of stars.

Therefore, if most of the $2\mu$m emission observed along the bar is due to old stars, then their ionizing continuum is not sufficient to explain the observed line-ratios.

The star formation rate (SFR) was estimated from the H$\alpha$ luminosity (cite: Kennicutt1998), after correcting the H$\alpha$ flux from dust extinction adopting the (cite: Cardelli1989) extinction law with $\mathrm{R_V = 3.1}$, and assuming an intrinsic flux ratio of H$\alpha$/H$\beta$= 2.86 and ionized gas temperature of T $\sim10^4$ K corresponding to case B recombination (cite: Osterbrock). The integrated SFR within the NIR bar (i.e., Figure [2](#fig:xs_phot)) is $\mathrm{SFR(H\alpha)_{bar}} = 0.08~\mathrm{M_{\odot}/yr}$, while the total $\mathrm{SFR(H\alpha)_{total}} = 0.4~\mathrm{M_{\odot}/yr}$.

The specific star formation rate (sSFR) was obtained from dividing the SFR surface density (=SFR/pixel area) by the stellar mass surface density as shown in Figure [5](#fig:ssfr). We note a clear enhancement in SF along the bar main axis; furthermore, the molecular surface density shows an enhancement in the same region.

Overall, our analysis suggests that the ionized gas in the bar structure is mostly associated to SF processes. Following we investigate whether the CO and SF concentration is induced by the bar potential.

# Inner Oval distortion

If a perturbation in the gravitational potential, such as that induced by a bar potential, is causing the $2\mu$m light distribution to elongate along a preferred direction; then the particles in such structure are expected to follow quasi-elliptical orbits (cite: Athanassoula1992). Hence kinematics of gas and stars should reflect this perturbation (cite: Pence1984b).

Figure [6](#fig:vel_maps) shows the CO, ionized and stellar kinematics around the bar region. The gas, being collisional, is more sensitive to non-axisymmetric perturbations. This is clearly reflected in the CO moment 1 map where a strong distortion of the semi-minor axis is observed. The former misalignment is a signature of an oval distortion produced by a bar (cite: Pence1988; LopezCoba2022), here observed at high spatial resolution.

The distortion is also observed in the H$\alpha$ velocity map, however, since the ionized gas traced by H$\alpha$ is hotter ($\mathrm{T\sim10^4}$ K), and therefore it presents a larger intrinsic velocity dispersion than the one of the molecular gas traced with CO ($\mathrm{T\sim10}$ K), it is less pronounced in the ionized gas and is probably affected by local SF.

The stellar kinematics although affected by the pixel-coadding during the SSP analysis, it still reveal a clear distortion in the iso-velocities near the bar as noted in Figure [6](#fig:vel_maps).

So far, it is clear that the stars, the molecular gas traced with CO and the ionized gas traced with H$\alpha$ respond in a similar way to the presence of this bar-like structure detected in NGC 1087.

## Kinematic interpretation of the oval distortion

The distortion in the velocity field such as the ones observed before could be caused by an elongated potential.

However, only a few kinematic models in the literature attempt to describe the flow caused by an oval distortion (cite: velfit; Maciejewski2012).

A bisymmetric distortion induced by a second order perturbation to the potential, such as that induced by an elongated potential, has been shown to successfully reproduce the velocity field in bars (cite: velfit).

Since the F200W image evidences the presence of a faint bar-like structure oriented at $305^{\circ}$ in the sky, we performed bisymmetric models over the stellar, H$\alpha$ and CO velocity maps, with a fixed orientation of the oval distortion.

The bisymmetric model from (cite: velfit) is described by the following expression:

$$\begin{multline}
 \label{Eq:bisymmetric}
 V_\mathrm{LoS}  =  \sin i \Big( V_t(r)\cos \theta - V_{2,t}(r)\cos 2\theta_\mathrm{bar} \cos \theta \\ - V_{2,r}(r) \sin 2\theta_\mathrm{bar} \sin \theta \Big) + V_\mathrm{sys} 
\end{multline}$$

where $\theta_{bar} = \theta - \phi_{bar}$; with $\theta$ being the azimuthal angle measured on the disk plane from the line of nodes and $\phi_{bar}$ the position angle of the bar-like structure on the disk plane. $V_{t}$ is the tangential or circular rotation and $V_{2r}$ and $V_{2t}$ represent the radial and tangential velocities that result from a bisymmetric distortion to the gravitational potential.

Before this analysis we performed a circular rotation model to obtain the disk projection angles and the rotational curves.

In this case and in the subsequent, we used the $\mathtt{XS}$ code for generating the kinematic models (cite: XookSuut).

This code derives an interpolated model over a set of concentric rings evenly spaced $r_k$, minimizing the function $\chi^2 = (V_{obs}-V_k(r) w_k(r))^2/\sigma^2$, where $V_{obs}$ is the observed velocity map; $V_{k}$ are the set of velocities inferred at $r_k$; $w_k$ is a set of weights that depend on the specific kinematic model adopted and will serve to create a 2D model; $\sigma$ is the error velocity map. We refer to (cite: XookSuut) for a thorough description of this analysis. It is important to mention that the modeling does not assume any parametric function on the velocity profiles.

A pure circular rotation, without non-circular motions, is described by the first term on the right from Equation [\[Eq:bisymmetric\]](#Eq:bisymmetric).

The disk orientation of NGC 1087 was estimated from modeling the H$\alpha$ and stellar velocity maps with circular rotation only, obtaining $\phi_{disk}^{\prime} = 358.9^{\circ}$, $i=44.5^{\circ}$ and $V_{sys}=1526$ km s$^{-1}$.

The residual velocity maps from this model i.e., $V_{obs}-V_{circular}$, are shown in the third column from Figure [6](#fig:vel_maps).

The circular rotation models leave large-scale residual velocities of the order of $30$ km s$^{-1}$ with a mirror symmetry about the nucleus; this corresponds to de-projected amplitudes of $\sim 50$ km s$^{-1}$ for the non-circular velocities on the disk plane. These residual patterns have been observed in larger scales in galaxies with long bars in H$\alpha$ (cite: Lang2020; LopezCoba2022) and molecular gas (cite: Pence1988; Mazzalay2014).

The bisymmetric model with a fixed oval orientation at $\phi_{bar}^{\prime}$ is shown in the fourth column in Figure [6](#fig:vel_maps). This model reproduces simultaneously the twisted iso-velocities in the three velocity maps. The root mean square (rms) of the models decrease compared with the circular rotation one, therefore, in terms of the residuals, the LoS-velocities observed around the bar region can be reproduced by a kinematic model that considers a bar-like perturbation as the main source of non-circular motions. However, at such high spatial resolution $\sim 70$ pc, there are still residual velocities that the bisymmetric model can not account for, this is reflected in the 15 km s$^{-1}$ rms in the models, which is similar or larger than the level of turbulence of the ISM (cite: Moiseev2015).

An alternative interpretation to the observed non-circular motions in the H$\alpha$ and CO velocity maps is the presence of gas inflow induced by the NIR-bar (cite: Mundell1999); in fact, hydro-dynamical models simulating bars predict inflow of gas along the offset ridges, or bar dust lanes, (cite: Athanassoula1992). As observed in Figure [1](#fig:main), the MUSE image of NGC 1087 shows several dust lanes in the central region making difficult the identification of those associated with the bar.

Assuming the spiral arms are trailing (see bottom-right panel from Figure [1](#fig:main)), NGC 1087 rotates counterclockwise in the sky. Thus, positive (negative) residuals in the near (far) side represent inflow; hence, a radial flow ($V_{rad}$) along the bar major axis is inflowing if $V_{rad}<0$.

We implemented a non-axisymmetric model, with a flow streaming along $\phi_{bar}^{\prime}$.

The non-axisymmetric inflow model is described by the following expression:

$$\begin{multline}
 \label{Eq:inflow}
 V_{LoS} = (V_{t}(r)\cos\theta + V_{rad}(r)\cos \theta_{bar} \sin \phi_{bar}) \sin i \\ + V_{sys} 
\end{multline}$$

where $V_{rad}$ is the radial velocity of the flow, and $\phi_{bar}$ is the misalignment between the disk and the bar position angles on the disk plane. This model assumes the gas is flowing along $\phi_{bar}$. This expression is similar to (cite: Hirota2009) and (cite: Wu2021) assuming that the gas flows parallel to the bar major axis.

In order to consider pixels likely affected by this motion, we consider the elliptical region that better describes the bar-like light distribution and defined in Figure [2](#fig:xs_phot).

The 2D representation of this model is shown in Figure [6](#fig:vel_maps), while the kinematic radial profiles of all models are shown in Figure [7](#fig:all_vels). As observed, the radial velocity $V_{rad}$ results negative in the model, with maximum inflow velocities of the order of 50 km s$^{-1}$.

![](all_vels)

The molecular mass flow rate ($\dot{M}_{mol}$) associated can be computed following the expression (cite: DiTeodoro2021): $$\begin{equation}
 \dot{M}_{mol}(r) = 2\pi r \Sigma_{mol}(r) V_{inflow}(r)
\end{equation}$$

with $\mathrm{ \Sigma_{mol} }$ being the de-projected molecular mass surface density, $V_{inflow}$ the CO inflow velocity and $r$ the galactocentric distance. Figure [8](#fig:inflow) shows the spatially resolved $\dot{M}_{mol}$ and its average radial profile. We find an average $\dot{M}_{mol}\sim -20 \mathrm{M_{\odot}/yr}$. For comparison, spiral arms induce radial flows and radial velocities of the order of $1\mathrm{M_{\odot}/yr}$ and $10$ km s$^{-1}$ respectively, (cite: DiTeodoro2021).

![](inflow.png)

# Discussion and Conclusions

The combination of spatially resolved spectra provided by MUSE-VLT, with the high spatial resolution from JWST and the ALMA CO $J=2\rightarrow 1$ data allowed us to reveal a central kinematic oval distortion, as well as a small scale elongated structure in the NIR continuum in NGC 1087.

This elongated structure is not evident in optical images, but only revealed with the NIRCam F200W and F360M filters at $2\mu$m and $3\mu$m respectively, thanks to its exquisite resolution. The optical counterpart of this bar is likely to be affected by dust absorption and by the intense radiation from young stars.

Its preferential elongation suggests the presence of a non-axisymmetric perturbation in the gravitational potential, in particular a bar-like type. At first order, the 2$\mu$m light distribution of this structure can be described with an exponential disk profile oriented at $\phi_{bar}^{\prime} = 305^{\circ}$, and the ellipticity of the elongated structure is $\varepsilon^{\prime} = 0.5$, (see Figure [2](#fig:xs_phot)), with a half-major axis length of $a_{bar}^{\prime}\sim 14\ensuremath{''}$ or $\sim$ 1.2 kpc in the galaxy plane.

Overall the shape of this structure resembles to a faint stellar bar, although with remarkable differences with respect to conventional stellar bars, in terms of bar-length, the lack of a SF nuclear ring and not clear associated dust lanes along the bar axis. The same argument however applies for an elongated bulge. The main reason this is not considered is due to the large reservoirs of molecular gas observed, since bulges tend to be quiescent structures with null or low SFRs (cite: Shapiro2010).

Furthermore, the \[ O I \]$/$H$\alpha$ and \[ O III \]$/$H$\beta$ line-ratios and large EWH$\alpha$ from the bar (see Figure [1](#fig:main)) indicate that the ionized gas is product from a recent or ongoing SF event given its spatial coincidence with the CO emission.

The ionized and molecular gas kinematics and the stellar velocity, reveal simultaneously the presence of an oval distortion in the velocity maps in concordance with the extension of the faint bar.

This evidences undoubtedly the imprints of a non-axisymmetric perturbation in the potential, here captured in different phases and enhanced in dynamically cold gas.

Kinematic models for a second order potential perturbation successfully described the LoS velocities in the three velocity maps. We showed that this is achieved just by fixing the orientation of the stream flow to the bar major axis in the models, and the radial profiles of the noncircular velocities are consistent with the residuals from circular rotation, with possible differences in amplitudes due to assymmetric drift and other random motions not considered in the model as we showed in Figure [7](#fig:all_vels).

Apart from the elliptical motions considered in the bisymmetric models, radial inflows are expected in bars, and these are observed to occur along the bar-dust lanes (cite: Wu2021; Sormani2023).

Our implementation of an inflow model is therefore physically motivated.

An inflow of cold gas caused by a lose of angular momentum could trigger the SF observed along the bar. Although a fraction of ionized gas could arise by the shock with the dust lanes, the contribution of shocks is expected to be minor.

Moreover, the sign of the radial flow suggests the gas is inflowing to the center at a maximum speed of $50$ km s$^{-1}$. This kinematic model yields the lowest rms despite being the model with the lowest number of free variables. Statistically speaking, the inflow scenario is favored over the bisymmetric model, although given the complex behavior of gas in bars, the contribution of gas oval orbits can not be ruled out. In fact both type of motions are expected to happen simultaneously in bars (cite: Athanassoula1992; Regan1999). To date, there is no a 2D-kinematic model that includes such dynamics of bars.

The gas inflow model is in concordance with the observed enhancement in H$\alpha$ flux along the bar. The inferred inflow velocities translate in molecular mass inflow rates of $\dot{M}_{mol} = 20~ \mathrm{M_{\odot}/yr}$. This is larger than the measured SFR(H$\alpha$) along the bar, thus we argue that a major inflow of gas might be feeding the SF in the bar. In fact SF prevents the so-called continuity problem (cite: Simon2003; Maciejewski2012) when often considering radial flow models. This large inflow rate is partially due to the large inflow velocities; although this amplitude of non-circular motions is observed in bars, the global inflow rate expected by hydrodynamical models is lower (cite: Athanassoula1992; Mundell1999).

To summarize, in this work we have taken the advantage of multiple archival data to reveal a hidden non-axisymmetric structure in the optical, thanks to the high angular resolution of the data. We were able to confirm the presence of an oval distortion and successfully model it with a bar-like flow model. We also show that the SFR in the bar could be explained by an inflow of gas along the bar major-axis. Our results contribute to understand the overall picture of non-axisymmetry in galaxies with the most sophisticated data so far. Additionally, it highlights the importance of using the IR instead of optical bands to detect stellar bars, which could increase the fraction of barred galaxies detected in the local Universe.

# Acknowledgment

We thank the anonymous referee for their comments and suggestions which help to improve the quality of this manuscript. CLC acknowledges support from Academia Sinica Institute of Astronomy and Astrophysics. LL acknowledges the Ministry of Science & Technology of Taiwan under the grant NSTC 112-2112-M-001-062 -.

Based on data obtained from the ESO Science Archive Facility with DOI(s): .

The specific PHANGS–JWST observations analyzed can be can be found in MAST: . This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01651.S.

natexlab

(ref: Alarie2019) Alarie, A., & Morisset, C. 2019, , 55, 377, doi: [`10.22201/ia.01851101p.2019.55.02.21`](http://doi.org/10.22201/ia.01851101p.2019.55.02.21)

(ref: Athanassoula1992) Athanassoula, E. 1992, MNRAS, 259, 345, doi: [`10.1093/mnras/259.2.345`](http://doi.org/10.1093/mnras/259.2.345)

(ref: Bacon2010) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Proc. SPIE, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, 773508, doi: [`10.1117/12.856027`](http://doi.org/10.1117/12.856027)

(ref: Bacon2017) Bacon, R., Conseil, S., Mary, D., et al. 2017, A&A, 608, A1, doi: [`10.1051/0004-6361/201730833`](http://doi.org/10.1051/0004-6361/201730833)

(ref: ManGA) Bundy, K., Bershady, M. A., Law, D. R., et al. 2015, ApJ, 798, 7, doi: [`10.1088/0004-637X/798/1/7`](http://doi.org/10.1088/0004-637X/798/1/7)

(ref: bushouse) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2022, JWST Calibration Pipeline, 1.8.2, Zenodo, doi: [`10.5281/zenodo.7229890`](http://doi.org/10.5281/zenodo.7229890)

(ref: Cardelli1989) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245, doi: [`10.1086/167900`](http://doi.org/10.1086/167900)

(ref: Cheung2013) Cheung, E., Athanassoula, E., Masters, K. L., et al. 2013, ApJ, 779, 162, doi: [`10.1088/0004-637X/779/2/162`](http://doi.org/10.1088/0004-637X/779/2/162)

(ref: Cid2010) Cid Fernandes, R., Stasińska, G., Schlickmann, M. S., et al. 2010, MNRAS, 403, 1036, doi: [`10.1111/j.1365-2966.2009.16185.x`](http://doi.org/10.1111/j.1365-2966.2009.16185.x)

(ref: Davies2016) Davies, R. L., Groves, B., Kewley, L. J., et al. 2016, MNRAS, 462, 1616, doi: [`10.1093/mnras/stw1754`](http://doi.org/10.1093/mnras/stw1754)

(ref: 3RC) de Vaucouleurs, G., de Vaucouleurs, A., Corwin, Herold G., J., et al. 1991, Third Reference Catalogue of Bright Galaxies

(ref: DiTeodoro2021) Di Teodoro, E. M., & Peek, J. E. G. 2021, ApJ, 923, 220, doi: [`10.3847/1538-4357/ac2cbd`](http://doi.org/10.3847/1538-4357/ac2cbd)

(ref: Emsellem2022) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: fathi05) Fathi, K., van de Ven, G., Peletier, R. F., et al. 2005, MNRAS, 364, 773, doi: [`10.1111/j.1365-2966.2005.09648.x`](http://doi.org/10.1111/j.1365-2966.2005.09648.x)

(ref: Gutkin2016) Gutkin, J., Charlot, S., & Bruzual, G. 2016, MNRAS, 462, 1757, doi: [`10.1093/mnras/stw1716`](http://doi.org/10.1093/mnras/stw1716)

(ref: Hirota2009) Hirota, A., Kuno, N., Sato, N., et al. 2009, PASJ, 61, 441, doi: [`10.1093/pasj/61.3.441`](http://doi.org/10.1093/pasj/61.3.441)

(ref: Kennicutt1998) Kennicutt, Jr., R. C. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: Kewley2006) Kewley, L. J., Groves, B., Kauffmann, G., & Heckman, T. 2006, MNRAS, 372, 961, doi: [`10.1111/j.1365-2966.2006.10859.x`](http://doi.org/10.1111/j.1365-2966.2006.10859.x)

(ref: Kourkchi2017) Kourkchi, E., & Tully, R. B. 2017, ApJ, 843, 16, doi: [`10.3847/1538-4357/aa76db`](http://doi.org/10.3847/1538-4357/aa76db)

(ref: Lacerda2022) Lacerda, E. A. D., Sánchez, S. F., Mejı́a-Narváez, A., et al. 2022, New A, 97, 101895, doi: [`10.1016/j.newast.2022.101895`](http://doi.org/10.1016/j.newast.2022.101895)

(ref: Lacerda2018) Lacerda, E. A. D., Cid Fernandes, R., Couto, G. S., et al. 2018, MNRAS, 474, 3727, doi: [`10.1093/mnras/stx3022`](http://doi.org/10.1093/mnras/stx3022)

(ref: Lang2020) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122, doi: [`10.3847/1538-4357/ab9953`](http://doi.org/10.3847/1538-4357/ab9953)

(ref: Starburst99) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3, doi: [`10.1086/313233`](http://doi.org/10.1086/313233)

(ref: Leroy2021a) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021a, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: Leroy2021b) Leroy, A. K., Hughes, A., Liu, D., et al. 2021b, ApJS, 255, 19, doi: [`10.3847/1538-4365/abec80`](http://doi.org/10.3847/1538-4365/abec80)

(ref: XookSuut) Lopez-Coba, C., Lin, L.-H., & Sanchez Sanchez, S. F. 2021, arXiv e-prints, arXiv:2110.05095. [`https://arxiv.org/abs/2110.05095`](https://arxiv.org/abs/2110.05095)

(ref: LopezCoba2022) López-Cobá, C., Sánchez, S. F., Lin, L., et al. 2022, ApJ, 939, 40, doi: [`10.3847/1538-4357/ac937b`](http://doi.org/10.3847/1538-4357/ac937b)

(ref: Maciejewski2012) Maciejewski, W., Emsellem, E., & Krajnović, D. 2012, MNRAS, 427, 3427, doi: [`10.1111/j.1365-2966.2012.22040.x`](http://doi.org/10.1111/j.1365-2966.2012.22040.x)

(ref: Masters2011) Masters, K. L., Nichol, R. C., Hoyle, B., et al. 2011, MNRAS, 411, 2026, doi: [`10.1111/j.1365-2966.2010.17834.x`](http://doi.org/10.1111/j.1365-2966.2010.17834.x)

(ref: Mazzalay2014) Mazzalay, X., Maciejewski, W., Erwin, P., et al. 2014, MNRAS, 438, 2036, doi: [`10.1093/mnras/stt2319`](http://doi.org/10.1093/mnras/stt2319)

(ref: Moiseev2015) Moiseev, A. V., Tikhonov, A. V., & Klypin, A. 2015, MNRAS, 449, 3568, doi: [`10.1093/mnras/stv489`](http://doi.org/10.1093/mnras/stv489)

(ref: Mundell1999) Mundell, C. G., & Shone, D. L. 1999, MNRAS, 304, 475, doi: [`10.1046/j.1365-8711.1999.02330.x`](http://doi.org/10.1046/j.1365-8711.1999.02330.x)

(ref: Osterbrock) Osterbrock, D. E. 1989, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Pence1984b) Pence, W. D., & Blackman, C. P. 1984, MNRAS, 210, 547, doi: [`10.1093/mnras/210.3.547`](http://doi.org/10.1093/mnras/210.3.547)

(ref: Pence1988) Pence, W. D., Taylor, K., Freeman, K. C., de Vaucouleurs, G., & Atherton, P. 1988, ApJ, 326, 564, doi: [`10.1086/166117`](http://doi.org/10.1086/166117)

(ref: Pilyugin2016) Pilyugin, L. S., & Grebel, E. K. 2016, MNRAS, 457, 3678, doi: [`10.1093/mnras/stw238`](http://doi.org/10.1093/mnras/stw238)

(ref: Reese2007) Reese, A. S., Williams, T. B., Sellwood, J. A., Barnes, E. I., & Powell, B. A. 2007, AJ, 133, 2846, doi: [`10.1086/516826`](http://doi.org/10.1086/516826)

(ref: Regan1999) Regan, M. W., Sheth, K., & Vogel, S. N. 1999, ApJ, 526, 97, doi: [`10.1086/307960`](http://doi.org/10.1086/307960)

(ref: PHANGS-JWST_doi) Rosolowsky, Erik. 2022, PHANGS-JWST First Results, STScI/MAST, doi: [`10.17909/9BDF-JN24`](http://doi.org/10.17909/9BDF-JN24)

(ref: sanchez12a) Sánchez, S. F., Kennicutt, R. C., Gil de Paz, A., et al. 2012, A&A, 538, A8, doi: [`10.1051/0004-6361/201117353`](http://doi.org/10.1051/0004-6361/201117353)

(ref: sanchez-blazquez11) Sánchez-Blázquez, P., Ocvirk, P., Gibson, B. K., Pérez, I., & Peletier, R. F. 2011, MNRAS, 415, 709, doi: [`10.1111/j.1365-2966.2011.18749.x`](http://doi.org/10.1111/j.1365-2966.2011.18749.x)

(ref: PHANGS_doi) Schinnerer, E. 2021, 3D Mapping of the Dynamic Feedback and Chemistry in the Star Formation Process across Galaxy Disks, European Southern Observatory (ESO), doi: [`10.18727/ARCHIVE/47`](http://doi.org/10.18727/ARCHIVE/47)

(ref: sell93) Sellwood, J. A., & Wilkinson, A. 1993, Reports on Progress in Physics, 56, 173, doi: [`10.1088/0034-4885/56/2/001`](http://doi.org/10.1088/0034-4885/56/2/001)

(ref: Shapiro2010) Shapiro, K. L., Falcón-Barroso, J., van de Ven, G., et al. 2010, MNRAS, 402, 2140, doi: [`10.1111/j.1365-2966.2009.16111.x`](http://doi.org/10.1111/j.1365-2966.2009.16111.x)

(ref: S4G) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397, doi: [`10.1086/657638`](http://doi.org/10.1086/657638)

(ref: Simon2003) Simon, J. D., Bolatto, A. D., Leroy, A., & Blitz, L. 2003, ApJ, 596, 957, doi: [`10.1086/378200`](http://doi.org/10.1086/378200)

(ref: Sormani2023) Sormani, M. C., Barnes, A. T., Sun, J., et al. 2023, MNRAS, 523, 2918, doi: [`10.1093/mnras/stad1554`](http://doi.org/10.1093/mnras/stad1554)

(ref: velfit) Spekkens, K., & Sellwood, J. A. 2007, ApJ, 664, 204, doi: [`10.1086/518471`](http://doi.org/10.1086/518471)

(ref: Stasinska2008) Stasińska, G., Vale Asari, N., Cid Fernandes, R., et al. 2008, MNRAS, 391, L29, doi: [`10.1111/j.1745-3933.2008.00550.x`](http://doi.org/10.1111/j.1745-3933.2008.00550.x)

(ref: mappingsv) Sutherland, R., Dopita, M., Binette, L., & Groves, B. 2018, MAPPINGS V: Astrophysical plasma modeling code, Astrophysics Source Code Library, record ascl:1807.005. [`http://ascl.net/1807.005`](http://ascl.net/1807.005)

(ref: EMILES) Vazdekis, A., Koleva, M., Ricciardelli, E., Röck, B., & Falcón-Barroso, J. 2016, MNRAS, 463, 3409, doi: [`10.1093/mnras/stw2231`](http://doi.org/10.1093/mnras/stw2231)

(ref: Wong2004) Wong, T., Blitz, L., & Bosma, A. 2004, ApJ, 605, 183, doi: [`10.1086/382215`](http://doi.org/10.1086/382215)

(ref: Wu2021) Wu, Y.-T., Trejo, A., Espada, D., & Miyamoto, Y. 2021, MNRAS, 504, 3111, doi: [`10.1093/mnras/stab1087`](http://doi.org/10.1093/mnras/stab1087)

[^1]: From now on primed variables make reference to values measured on the sky plane, otherwise in the disk plane.

[^2]: Sky angles relative the disk major axis can be translated to angles measured in the galaxy plane and vise versa through, $\tan \phi_{bar} = \tan \Delta \phi / \cos i$, with $\Delta \phi = \phi_{bar}^{\prime} - \phi_{disk}^{\prime}$.

[^3]: Distances measured at different P.A. in the sky plane can be translated to distances in the galaxy plane following: $r_{disk}^2 = r_{sky}^2 (\cos^2 \Delta \phi + \sin^2 \Delta \phi / \cos^2 i)$.

</paper>

Write the methods card for this paper.