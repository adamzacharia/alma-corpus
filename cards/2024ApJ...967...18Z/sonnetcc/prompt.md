# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...967...18Z\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...967...18Z",
 "title": "Magnetic Field of Molecular Gas Measured with the Velocity Gradient Technique. II. Curved Magnetic Field in kpc-scale Bubble of NGC 628",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Zhao, Mengke",
 "n_authors": 12,
 "arxiv_id": "2404.02651",
 "doi": "10.3847/1538-4357/ad3a62",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S"
 ]
}
```

Paper text:
<paper>
# **Magnetic Field of Molecular Gas Measured with the Velocity Gradient Technique II: Curved Magnetic Field in kpc-Scale Bubble of NGC 628**

## Abstract

We report the detection of the ordered alignment between the magnetic field and kpc-scale bubbles in the nearby spiral galaxy, NGC 628. Applying the Velocity Gradient Technique (VGT) on CO spectroscopic data from the ALMA-PHANGS, the magnetic field of NGC 628 is measured at the scale of 191 pc ($\sim$ 4 $''$). The large-scale magnetic field is oriented parallel to the spiral arms and curves around the galactic bubble structures in the mid-infrared emission observed by the James Webb Space Telescope (JWST). Twenty-one bubble structures have been identified at the edges of spiral arms with scales over 300 pc, which includes two kpc-scale structures. These bubbles are caused by supernova remnants and prolonged star formation and are similar to the outflow chimneys found in neutral hydrogen in galactic disks. At the edge of the bubbles, the shocks traced by the OIII emission present a curved magnetic field that parallels the bubble’s shell. The magnetic field follows the bubble expansion and binds the gas in the shell to trigger further star formation. By analyzing the larger sample of 1694 bubbles, we found a distinct radial-size distribution of bubbles in NGC 628 indicating the star formation history in the galaxy.

= 150pt

\]

# introduction

Magnetic fields are a primary component of the interstellar media (ISM) that play an important role in star formation, and the evolution of spiral galaxies (cite: 2007ARA&A..45..565M; 2013pss5.book..641B). Magnetic fields have been observed over the past decades at all spatial scales in the Galaxy and in extra-galactic sources using far-infrared and radio observations (cite: 1994RPPh...57..325K; 2004NewAR..48.1289B; 2015A&ARv..24....4B; 2020ApJ...888...66L; 2020AJ....160..167J). Shocks, supernovae, star formation activities, and other physical processes may affect and distort the local magnetic field structures in the ISM (eg: (cite: 2004MNRAS.353..550B; 2017NatAs...1E.158L; 2021A&A...647A..78A) and the structure of spiral arms and spurs (cite: 1980ApJ...242..528E; 1985ApJ...297...61B; 2012ApJ...756...45L; 2014ApJ...792..122L).

The recent introduction of the Velocity Gradient Technique (VGT; (cite: 2017ApJ...835...41G; 2018ApJ...853...96L; 2018MNRAS.480.1333H)) provides a new way to measure the magnetic field using Doppler-shifted emission lines in nearby galaxies (cite: 2023ApJ...946....8T; 2022ApJ...941...92H; 2023MNRAS.519.1068L). In a turbulent magnetized medium, the turbulent eddies will extend along the local B-field and have a velocity gradient perpendicular to their semi-major axis (cite: 1995ApJ...438..763G; 1999ApJ...517..700L).

These velocity gradients of elongated eddies are expected to be perpendicular to the local B-field orientation. The PHANGS-ALMA survey provides high-resolution CO isotopolog data where anisotropies of the turbulence can be extracted and used to trace the velocity gradients of eddies. The ability of the VGT technique to trace molecular-gas-associated magnetic fields has been tested in observations in nearby galaxies (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L).

Early Release Observations (ERO; (cite: 2022ApJ...936L..14P)) of the spiral galaxy NGC 628 with the James Webb Space Telescope (JWST) reveal new features compared with previous observations in the form of ’bubble structures’ along spiral arms that have no mid-infrared continuum emission. Such features resemble the chimney outflows found in neutral hydrogen related to star formation in edge-on spiral galaxies. Combined with the observation of the magnetic field, these bubbles provide new understanding of how the magnetic field may affect the structure of the spiral galaxy.

In this work, we aim to study the magnetic field in and around the bubbles structures of the spiral galaxy NGC 628 at the distance of 7.3 Mpc (cite: 2004AJ....127.2031K), which exhibits ongoing star formation but is not undergoing a central starburst (cite: 2018PASP..130h4101L). The details of the archival data are shown in Section [2](#sect2). In Section [3](#sect3), we introduce the details of the VGT and VDA (Velocity Decomposition Algorithm; (cite: 2021ApJ...910..161Y)) techniques. The magnetic field structure and galactic bubbles in NGC 628 are described and discussed in Sections [3](#sect3) and [4](#sect4). We discuss the nature of the bubbles and their magnetic field structure in Section [5](#sect5). A summary has been provided in Section [6](#sect6).

![](f1/NGC628-LIC-2.png)

# The NGC 628 Data

## The spectral line emission

In this work, we select $^{12}$CO (2-1) emission as the main tracer to measure the magnetic field of the spiral galaxy NGC628 with the VGT technique. The spectral cube data comes from the PHANGS-ALMA survey (cite: 2021ApJS..257...43L), which includes 90 nearby galaxies (d $\leq$ 20 Mpc).

high signal-to-noise ratio data with the RMS noise level of $\sim$ 0.30 $\pm$ 0.13 K km s$^{-1}$. The spatial resolution for NGC 628 is $\sim$ 1.12$''$ (FWHM $\sim$ 53.5 pc) and the velocity resolution is around 2.5 km s$^{-1}$ (cite: 2021ApJS..257...43L). The rms level of the PHANGS-ALMA Survey is around 0.3 $\pm$ 0.17 K km s$^{-1}$.

In addition, the OIII emission in NGC 628 has been selected to trace the shocks, which comes from the PHANGS-MUSE Survey (cite: 2022A&A...659A.191E) with a sub-arcsec beam scale size.

## The continuum emission

The continuum emissions of NGC 628 are observed by the James Webb Space Telescope (JWST) Early Release Observations (ERO; (cite: 2022ApJ...936L..14P)). The filters F770W (7.7 $\mu$m), F1000W (10 $\mu$m), F1130W (11.3 $\mu$m), and F2100W (21 $\mu$m) from the JWST Mid Infrared Instrument (MIRI) will be used in this work.

## The polarization data

The synchrotron polarization of NGC 628 has been observed with the $\it{Karl G. Jansky}$ Very Large Array (JVLA) at S -band (2.6–3.6 GHz effective bandwidth and spatial resolution $\sim$ 18$''$; (cite: 2017A&A...600A...6M)). The orientation of the magnetic field $\theta_B$ derived from the JVLA polarization data are estimated by: $$\begin{equation}
    \begin{aligned}
        \rm \theta_B = \frac{1}{2}\,arctan(U,Q) \, + \frac{1}{2}\pi,
    \end{aligned}
\end{equation}$$ where the Q and U are the Stokes parameters.

# Using the VGT Method

## The anisotropy of the MHD turbulence

The velocity gradient technique (VGT; (cite: 2017ApJ...835...41G; 2018ApJ...853...96L; 2018MNRAS.480.1333H)) is the main analysis tool used in this work. This has been developed based on the current theories of MHD turbulence (cite: 1995ApJ...438..763G) and fast turbulent re-connection (cite: 1999ApJ...517..700L). These studies revealed that turbulent eddies are anisotropic, which means that the eddies are elongated along the local magnetic field lines (cite: 1995ApJ...438..763G; 1999ApJ...517..700L). If the scale of the eddies is decomposed into parallel ($l_\parallel$) and perpendicular ($l_\bot$) components with respect to the magnetic field, the anisotropy suggests $l_\bot \ll l_\parallel$. This property has been confirmed with numerical simulations (cite: 2000ApJ...539..273C; 2001ApJ...554.1175M; HXL21) and with solar wind observations (cite: 2016ApJ...816...15W; 2020FrASS...7...83M; 2021ApJ...915L...8D). Another important property of MHD turbulence is that the velocity fluctuations are scale-dependent such that (cite: 1999ApJ...517..700L):

$$\begin{equation}
    \label{eq.v}
    v_l\simeq v_{\rm inj}(\frac{l_\bot}{L_{\rm inj}})^{\frac{1}{3}}M_{\rm A}^{1/3},
\end{equation}$$ where $v_l$ is the fluctuation at scale $l$, $v_{\rm inj}$ is the velocity at the injection scale $L_{\rm inj}$, and $M_A$ is Alfvén Mach number. Together with the anisotropic relation $l_\bot \ll l_\parallel$, the scaling of the velocity gradients can be easily obtained (cite: 2020ApJ...898...65Y): $$\begin{equation}
    \label{eq.grad}
    \begin{aligned}
        \nabla v_l&\propto\frac{v_{l}}{l_\bot}\simeq \frac{v_{\rm inj}}{L_{\rm inj}}(\frac{l_{\perp}}{L_{\rm inj}})^{-\frac{2}{3}} M_{\rm A}^{\frac{1}{3}}.
    \end{aligned}
\end{equation}$$ Eq. [\[eq.grad\]](#eq.grad) suggests that the gradient amplitude increases when the scale $l_\bot$ decreases, i.e., the small resolved eddies correspond to strong velocity gradients. Therefore, in extragalactic sources, where the shear velocity and the differential rotation might contribute to the total velocity gradient, the contribution from the MHD turbulence would dominate at small scales ($<100$ pc), as demonstrated in (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L).

## The Velocity Gradient Technique

The input of the VGT technique is the high-resolution position-position-velocity (PPV) data cube of the $^{12}$CO emission in this work. The extraction of the velocity channel Ch(x,y) information from the PPV cube of the spectral line data has been done via the velocity caustics effect. The concept of the velocity caustics effect has been defined as the effect of the density structure distorting the turbulence and shear velocities along the line of sight (cite: 2000ApJ...537..720L). The density structure changes significantly for the different velocity channel and the resulting velocity fluctuations are thought to be most prominent in thin channel maps (cite: 2000ApJ...537..720L; 2021ApJ...915...67H). The difference for thin and thick channels is as follows: $$\begin{equation}
\label{eq5}
    \begin{aligned}
        \Delta v \, > \, \sqrt{\delta (v^2)}, \rm thick\,channel,
    \end{aligned}
\end{equation}$$ $$\begin{equation}
    \begin{aligned}
        \Delta v \, < \, \sqrt{\delta (v^2)}, \rm thin\,channel,        
    \end{aligned}
\end{equation}$$ where $\Delta v$ is the velocity channel width and $\sqrt{\delta (v^2)}$ is the velocity dispersion.

The thin velocity channel map Ch$_i$(x,y) is applied on the VGT technique (cite: 2022MNRAS.511..829H) to extract the velocity information from the PPV cubes via the velocity caustics effect. Each thin velocity channel map Ch$_i$(x,y) is used to calculate the pixelised gradient map $\psi^i_g (x,y)$: $$\begin{equation}
\label{eq.a4}
    \begin{aligned}
        \rm\bigtriangledown_x Ch_i(x,y) = Ch_i(x,y) - Ch_i(x-1,y) \,,
    \end{aligned}
\end{equation}$$ $$\begin{equation}
\label{eq.a5}
    \begin{aligned}
        \rm\bigtriangledown_y Ch_i(x,y) = Ch_i(x,y) -Ch_i(x,y-1)\,, 
    \end{aligned}
\end{equation}$$ $$\begin{equation}
    \begin{aligned}
        \rm\psi^i_g (x,y) = tan^{-1} (\frac{\bigtriangledown_y Ch_i(x,y)}{\bigtriangledown_x Ch_i(x,y)} \,,
    \end{aligned}
\end{equation}$$ where $\bigtriangledown_x$Ch$_i$(x,y) and $\bigtriangledown_y$Ch$_i$(x,y) are the x and y components of the gradient, respectively. The (x,y) two-dimensional position will be displayed in the (RA,DEC) plane of the sky for pixels whose spectral line emission has a signal-to-noise ratio greater than 3, which is high enough for credibility.

The orientation of the magnetic field is perpendicular to the velocity gradient direction in each sub-region. A sub-block averaging (cite: 2017ApJ...837L..24Y) method has been used to export the velocity gradients from the raw gradients within a sub-block of interest and then plotted in a corresponding histogram of the raw velocity gradient orientations $\psi^i_g$. The size of the sub-block is set as 20 $\times$ 20 pixels, which determines the size of the final magnetic field resolution. Using sub-block averaging, the total n$_v$ processed gradient maps $\psi^i_{g_s}(x,y)$ with i = 1,2,...,n$_v$ are taken to calculate the pseudo-Stokes-parameters $Q_g$ and $U_g$. Then, these pseudo-Stokes-parameters $Q_g$ and $U_g$ of the gradient-inferred magnetic field would be constructed by: $$\begin{equation}
    \begin{aligned}
        \rm Q_g(x,y) = \sum\limits_{i=1}^{n_v} Ch_i(x,y)cos(2\psi^i_{g_s}(x,y)),
    \end{aligned}
\end{equation}$$ $$\begin{equation}
    \begin{aligned}
        \rm U_g(x,y) = \sum\limits_{i=1}^{n_v} Ch_i(x,y)sin(2\psi^i_{g_s}(x,y)),
    \end{aligned}
\end{equation}$$ $$\begin{equation}
\label{eq12}
    \begin{aligned}
        \rm\psi_g = \frac{1}{2}tan^{-1}\frac{U_g}{Q_g},
    \end{aligned}
\end{equation}$$ where I$_i$(x,y) is the two dimensions integrated intensity of spectra cubes and n$_v$ is the number of velocity channels. The $\psi_g$ pseudo polarization is derived from the pseudo-Stokes-parameters $Q_g$ and $U_g$, which projects the three-dimensional $\psi^i_{g_s}$ data into a two-dimensional pseudo polarization angle $\psi_g$. The pseudo magnetic field orientation $\psi_B$ is perpendicular to the pseudo polarization angle $\psi_g$ on POS: $$\begin{equation}
\label{eq13}
    \psi_B = \psi_g + \pi /2 ,
\end{equation}$$ This pseudo magnetic field orientation is the B-field orientation measured with the VGT method from the spectral line data. Applying the VGT technique on the $^{12}$CO emission from the PHANGS-ALMA survey (cite: 2021ApJS..257...43L), the magnetic field orientations can be measured and be presented as an LIC (cite: Cabral_lic) as shown in Figure [1](#fig1). The resolution of the B-field measured with VGT can be approaching 4$"$ ($\sim$ 190 pc).

## The Velocity Decomposition Algorithm

The VGT technique is based on the position-position-velocity statistics (cite: 2000ApJ...537..720L), where the PPV cube has two components: a velocity and a density contribution. While the VGT technique is more sensitive to the velocity contribution, the Velocity Decomposition Algorithm (VDA) is a new technique that separates the velocity and density contribution from the PPV cube (cite: 2021ApJ...910..161Y),. By this method, the accuracy of VGT tracing of the magnetic field will be improved (cite: 2022ApJ...934...45Z).

In this work, the gas traced by the CO emission may come from star formation regions tracing the spiral arms. These star formation regions may have supersonic motions and the properties of the velocity component $V(X, v, \Delta v)$ may be calculated as: $$\begin{equation}
    \begin{aligned}
        \rm V(X, v, \Delta v) = - c^2_s \frac{\partial Ch(X, v, \Delta v)}{\partial v} \,,
    \end{aligned}
\end{equation}$$ where Ch(X, v, $\Delta$v) is the channel of the PPV cube, X means the position, v is the local velocity, and $\Delta$v is the velocity channel width. The velocity of sound $c_s$ can be calculated by assuming a uniform temperature $\sim$ 10 K, which results in a value $c_s$ $\sim$ 186 m s$^{-1}$. Using these velocity properties $p_v$ to replace the values for Ch(x,y) in Eq. [\[eq.a4\]](#eq.a4) and [\[eq.a5\]](#eq.a5), this VGT-VDA method can trace the magnetic field better. The VDA algorithm exhibits a sensitivity to spectral lines characterized by a high signal-to-noise ratio, particularly those present in structures of high density and small scale.

|     |             |              |      |            |
|:---:|:-----------:|:------------:|:----:|:----------:|
| ID  |     RA      |     DEC      | size | Estimated  |
|     |             |              | (pc) | SNR number |
|  1  | 1h36m44.64s | 15d46m20.7 s | 1164 | $\sim$ 194 |
|  2  | 1h36m40.84s | 15d48m09.6s  | 808  | $\sim$ 135 |
|  3  | 1h36m35.95s | 15d48m06.1s  | 418  | $\sim$ 70  |
|  4  | 1h36m36.29s | 15d48m11.1s  | 408  | $\sim$ 68  |
|  5  | 1h36m37.39s | 15d48m01.4s  | 520  | $\sim$ 87  |
|  6  | 1h36m37.51s |  15d47m12s   | 460  | $\sim$ 77  |
|  7  | 1h36m38.47s | 15d46m07.9s  | 392  | $\sim$ 65  |
|  8  | 1h36m38.63s | 15d46m51.85s | 408  | $\sim$ 68  |
|  9  | 1h36m39.33s | 15d48m08.5s  | 762  | $\sim$ 127 |
| 10  | 1h36m39.43s | 15d46m07.8s  | 496  | $\sim$ 83  |
| 11  | 1h36m39.5s  | 15d45m53.2s  | 490  | $\sim$ 82  |
| 12  | 1h36m40.71s | 15d48m35.7s  | 394  | $\sim$ 66  |
| 13  | 1h36m40.98s | 15d46m27.8s  | 500  | $\sim$ 83  |
| 14  | 1h36m42.25s | 15d48m09.8s  | 484  | $\sim$ 81  |
| 15  | 1h36m42.41s | 15d45m52.7s  | 592  | $\sim$ 99  |
| 16  | 1h36m42.81s | 15d46m47.1s  | 588  | $\sim$ 98  |
| 17  | 1h36m43.25s | 15d48m08.1s  | 476  | $\sim$ 79  |
| 18  | 1h36m43.64s | 15d46m38.4s  | 512  | $\sim$ 85  |
| 19  | 1h36m44.39s | 15d45m32.7s  | 614  | $\sim$ 102 |
| 20  | 1h36m45.49s | 15d46m35.8s  | 510  | $\sim$ 85  |

: The position and the supernova remnant numbers of the bubbles in NGC 628

## VGT method in Shock Fronts

On smaller scales, the shocks induce velocity jumps that are perpendicular to shock fronts, which can interfere with the turbulence-induced gradients. While the effect of shocks would reduce with a decreasing velocity channel width, it should be noticeable for the CO data having a velocity channel width large enough at $\sim$ 2.5 km s$^{-1}$. At a shock front, the velocity perpendicular to the shock will be reduced while the velocity component parallel to the shock front will be unchanged. For oblique shocks, this changes the orientation of the velocity vector and the velocity gradient at the shock front (cite: 2019ApJ...886...17H). Since the anisotropy of the MHD turbulence does not affect the shock, a magnetic field component in the same direction as the propagation direction of the shock front will still suggest a velocity gradient perpendicular to the magnetic field, and a propagation direction of the shock perpendicular to the shock front. For a magnetic field that is perpendicular to the propagation direction of the shock front or has some angle, the relative orientation of the velocity gradient and magnetic field is not maintained at 90 degrees (cite: 2019ApJ...878..157X). For a shock front that is parallel to the magnetic field, the direction of the magnetic field and the velocity gradient tend to be parallel. In cases where the shock front is oriented perpendicularly to the local magnetic field, the magnetic field that is unaffected by the local shock front aligns perpendicularly to the orientation of the mean velocity gradient (see Eq. [\[eq13\]](#eq13)). This physical process mirrors that observed in the VGT pipeline, as detailed in Section [3.2](#A.VGT). Conversely, when the shock front aligns paralleling the local magnetic field, the magnetic field influenced by the shock aligns paralleling the mean velocity gradient orientation and perpendicularly to the pseudo-magnetic field orientation $$\begin{equation}
\label{eqfrontparal}
    \begin{aligned}
        & if \, B \, \mathop{//}\, {\rm shock front},\,\, \psi_{Bs} = \psi_B + 90^\circ, \\
    \end{aligned}
\end{equation}$$ $$\begin{equation}
    \begin{aligned}
        if \, B \, \bot \, {\rm shock front}, \,\, \psi_{Bs} = \psi_B,\\
    \end{aligned}
\end{equation}$$ where the $\psi_B$ is the VGT orientation and $\psi_{Bs}$ is the magnetic field orientation at the shock front. The shock fronts can thus be traced by the velocity field of the OIII emission. The local magnetic field orientation can be discerned from the polarization at lower resolution, which encompasses the shock front.

# Result

## The magnetic fields in NGC 628

The magnetic fields in the galaxy NGC 628 have been measured using the Velocity Gradient Technique using the high-resolution $^{12}$CO (2-1) spectral line emission. Using the VGT technique, the magnetic field is derived at a scale of 191 pc ($\sim$ 4$''$) with the sub-block size set at 20$\times$20 pixels and with a pixel size of the $^{12}$CO emission of 0.2$''$. The magnetic field structure of NGC 628 is shown in Figure [1](#fig1).

On larger scales, the magnetic field is distributed along the spiral arms and the B-field orientations are nearly parallel to the tangential direction of the spiral arms. On smaller scales, the magnetic field displays curved structures around the spiral arms (ring-like shapes).

![image](f1/NGC628-AM-t.png) ![image](f1/NGC628-AM-g.png) ![image](f1/NGC628-AM-VDA-g.png)

## Bubbles in extragalactic sources

The JWST Early Release Observations (cite: 2022ApJ...936L..14P) present details of the spiral galaxy NGC 628. The high-resolution mid-infrared emission from JWST, characterized by a Full Width at Half Maximum (FHWM) of approximately 10 pc, presents a unique opportunity for investigating bubbles within extragalactic environments. This advanced capability allows for the observation of distinctive bubble features such as shells, stellar sources, and the hot emissions encapsulated by these bubbles (cite: 2006ApJ...649..759C; 2014ApJS..212....1A; 2019MNRAS.488.1141J). In a recent study, (cite: 2023ApJ...944L..24W) identified numerous bubbles within the extragalactic system NGC 628, demonstrating a broad range of scales with diameters spanning from 12 to 1164 pc. From the bubble catalog of (cite: 2023ApJ...944L..24W),we have identified 21 sizable bubbles exceeding twice the beam width of the magnetic field measured with VGT (approximately 390 pc). Of these, one particular bubble situated at the galactic center does not align with the focus of our work; it may be influenced more by the galactic center’s black hole rather than stellar feedback and star formation activities. Our attention centers on the remaining 20 large-scale bubbles within our sample, which are potentially linked to local star formation activities, as detailed in Table [1](#tab1). These large-scale bubbles display the hole-like shape around the ring shape. The ring structure contains large amounts of gas and shocks traced by CO and O III emission (see Fig. [7](#fig6)). The scale of our structures is all larger than 390 pc, where 390 pc is twice the beam for measuring the magnetic field structure accurately. Details of the bubble structures are shown in Table [1](#tab1).

## Comparison of the B-fields from VGT and from Synchrotron Polarization

The magnetic field measured with VGT for CO emission has a higher resolution ($\sim$ 4$''$), compared with previously determined B-field structures derived from synchrotron polarization ($\sim$ 18$''$) with JVLA at 3.1 GHz (cite: 2017A&A...600A...6M). We smooth the magnetic field derived by VGT to the same scale as that from JVLA resolution ($\sim$ 18$''$) and compare the two versions of the magnetic field. The alignment between the B-field orientations measured with polarization $\theta_B$ and VGT $\Phi_B$ is quantified as the **Alignment Measure** (AM; (cite: 2017ApJ...835...41G)): $$\begin{equation}
\label{AMeq}
    \begin{aligned}
        \rm AM = 2(\left \langle cos^2(\theta_B - \Phi_B) \right \rangle - \frac{1}{2}) \,.
    \end{aligned}
\end{equation}$$ The range of AM values should be from -1 to 1, where AM values close to 1 mean that $\phi_B$ is parallel to $\psi_g$ and AM values close to -1 indicate that $\phi_B$ is perpendicular to $\psi_g$. The uncertainty in the AM value $\sigma_{AM}$ may be given by a standard deviation divided by the square root of the sample size.

### The B-field in the galactic disk

Figure [2](#fig2) shows the magnetic field structure measured with VGT for CO emissions and from synchrotron polarization with a beam size of 18 $''$. The synchrotron radiation could originate from the warm ISM in star formation regions (cite: 2017A&A...600A...6M), while the CO emission originates from the cold ISM in the disk (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L).

Star-forming regions may be actively generating cosmic rays (CRs) and the cooling times of these CRs emitting at 3.1 GHz could be estimated as $t_{synch}$ $\sim$ 1.5($B$/mG)$^{-1.5}$(h$v$/kev)$^{-0.5}$ $\sim$ 13 Myrs, where the total magnetic field strength is around 10$\mu$G (cite: 2017A&A...600A...6M). The average diffusion time of $\sim$ 1 GeV CR protons in the Milky Way is around 10 Myrs for an assumed diffusion coefficient of 10$^{28}$ cm$^{2}$ s$^{-1}$ and a halo size around 1 kpc (cite: 1976RvMP...48..161G; 1990acr..book.....B; 1998ApJ...509..212S; 2019PhRvD..99j3023E). However, in star-formation regions and molecular clouds the CR diffusion is suppressed as a result of the CR steaming along confusing turbulence magnetic fields (cite: 2022ApJ...927...94X) or mirror diffusion (cite: 2021ApJ...923...53L; 2021ApJ...922..264X), which is also observed in Milky Way . Assuming that the disk height is hundreds of pc, the diffusion time could thus be one or two orders of magnitude longer. Since the cooling time of CR electrons is less than the diffusion time, electrons at 3.1 GHz would not diffuse into the halo. Therefore, CR electrons are still actively generated but are confined in the vicinity of the galactic disc and the origin of the CO emission could be similar to that of synchrotron emission.

Figure [2](#fig2) shows that the mean AM value is approaching 0.53 and is $\geq$ 0.5, which suggests that the magnetic field orientations from VGT are nearly parallel to those inferred from synchrotron polarization. The magnetic field derived by VGT is basically consistent with the previous results obtained from synchrotron polarization. Because the magnetic field measured with VGT for CO emission has a higher resolution in the galactic disk, the results may reflect the magnetic field at the spiral arms but also the small-scale structures around it.

![](f1/bubbble_1.png)

![](f1/Bubbles.pdf)

### The B-field at the Bubbles

The two largest bubbles, Bubble 1 and Bubble 2 (elaborated in Table [1](#tab1)), exceed the spatial resolution of previous synchrotron polarization observations (FWHM $\sim$ 800 pc) (cite: 2017A&A...600A...6M). These two large-scale bubbles offer exemplary instances for assessing the congruence between magnetic field orientation and VGT within minute-scale structures. The OIII emission from PHANGS-MUSE Survey is the tracer of shocks and Figure [2](#fig2) shows that the shock in Bubble 1 is close but does not overlap the gas shell of the bubble. Because of the shock front and the gas not being in the same position, the shock could not change the velocity gradient of the cold neutral medium traced by the CO emission. By comparison between the magnetic field for VGT and that for polarization, the mean AM is 0.70 ($\pm$ 0.01). This means that the magnetic field measured with VGT could be similar to that from polarization. In the no-shock region, the velocity gradient remains perpendicular to the magnetic field.

Different from Bubble 1, a shock exists at the gas shell of Bubble 2. As Figure [2](#fig2) shows, part of the bubble shell in Bubble 2 coincides with a shock front and the region has massive OIII emission. The OIII emission may be smoothed to trace the shock front at a scale of 18$''$, where the intensity is over 3$\times$10$^{-16}$ cm$^{-2}$ erg s$^{-1}$. Here the shape of the shock front is parallel to the magnetic field derived by polarization. The VGT orientation in this region is re-rotated by 90 degrees to achieve the B-field orientation, as dictated by Eq. [\[eqfrontparal\]](#eqfrontparal). By re-rotating the VGT orientation at the shock front, the AM between two measures of magnetic fields is 0.54, and the two types of magnetic fields are parallel to one another. In the shock front, the accuracy of VGT tracing magnetic field has been tested and the velocity gradient is close to being parallel to the magnetic field. In the region of the shock front, the VGT orientation needs to be re-rotated 90$^\circ$.

For the two largest bubbles, we also use the VDA method to improve the accuracy of the VGT technique by removing the density contribution in the PPV data cube. As Fig. [3](#fig3) shows, we compare the magnetic field measured with VGT-VDA and 3.1 GHz polarization. The AM value of Bubble 1 and Bubble 2 is up to 0.74 and 0.64, which is larger than the AM of VGT (Bubble 1 = 0.7 and Bubble 2 = 0.54). This means that the VGT-VDA has higher accuracy in tracing magnetic fields than only the VGT method, but it also verifies that the magnetic fields measured with VGT for the CO emission. It also means that we can reliably use the VGT technique to study the small-scale structures in NGC 628.

# Discussion

## Large-scale Bubbles as Supernova Remnants

The bubble structures appear rather common around the inner spiral arms of NGC 628 as seen in Fig. [1](#fig1). To establish the nature of the structure of these large-scale bubbles and the role of the magnetic field, the VGT-VDA method has been used to study the effects of the high-resolution magnetic field on large-scale bubble structures. This method improves the accuracy of the VGT method as the application of VDA removes the effect of the density contribution to the velocity gradient, which is particularly important at the edges of the structures.

Supernova remnants (SNRs, (cite: 1988ARA&A..26..145T; 1988ARA&A..26..295W)) and prolonged star formation are the most likely cause for the creation of a cavity within the circular bubble structures. Supernova explosions could have enough energy to cause large-scale bubbles with scales up to hundreds of pc or even kpc. These bubbles are found to be surrounded by gas structures with much-triggered star formation activities as traced by 11.3 $\mu$m and 21 $\mu$m emissions. This makes the bubbles to be relics of past star formation that only now show up at mid-infrared frequencies (see Fig. [1](#fig1)).

The kpc-scale Bubble 1 in Figure [3](#fig3) may be used as a high-confidence example of a bubble, where the shape and magnetic field structure could be caused by SNRs. The OIII emission serves as a valuable indicator for tracing the impact of shocks, as shown in Fig. [2](#fig2).

At the edge of Bubble 1, the shock front traced by the OIII emission is close to the bubble’s shell but it does not overlap with the spiral arms traced by the CO emission. The magnetic field morphology in the curved structure of Bubble 1 is like a closed ring that is aligned around the shape of the bubble. Due to the shock front being close to the shell at the edge of the bubbles, the supernovae create the shock and compress the gas to cause the bubbles and the shell. As a result of the gas flow towards the shell, the magnetic field has been distorted and forced to be perpendicular to the direction of matter flow (see Fig. [5](#fig4)). The curved magnetic field structure therefore represents the shocked boundaries of the large-scale bubble and serves as indirect evidence that the bubble structure and its curved magnetic field would be caused by the SNRs.

Alternative star formation processes, such as stellar feedback and the expansion of HII regions, may exhibit a greater inclination toward instigating the smaller-scale structure of ISM. These formations might lack the requisite energy to give rise to structures on a scale of hundreds of pc. Similar phenomena may also manifest within sub-regions of the large-scale bubbles. As an illustration, the orientations of magnetic fields in the sub-region of Bubble 2 (see Fig. [4](#figsample)) are observed to be perpendicular to the gas structures in sub-regions with existing star formation as traced by 21$\mu$m emissions. It is noteworthy that local magnetic fields may undergo distortion due to the influence of star formation activities in this specific region, a phenomenon akin to those observed within the Milky Way (cite: 2017NatAs...1E.158L; 2024ApJ...961..124Z).

![](f/gap-size-Galrad.pdf)

## Bubble Size and Galactic Distribution

In this paper, only the large-scale bubbles have been considered and their magnetic field structures have been determined (see Fig. [5](#fig4)). A more complete sample of bubbles in NGC 628 includes 1694 bubbles with different sizes and is provided by (cite: 2023ApJ...944L..24W). A histogram of the size distribution and the galacto-centric distance of the bubbles in this extended sample is presented in Fig. [5](#fig4) and shows a peak in the extended distribution at a bubble size of 50 pc and at a galacto-centric distance of 3 kpc. In the galactic distribution of bubbles, the number of bubbles increases nearly linearly up to the galacto-centric distance as 3 kpc, and then they decrease sharply and non-linearly. The large-scale bubbles considered are thus mainly distributed in the inner part of the galaxy within 3 kpc.

The bubble number distribution along the galactocentric distance is similar to the star formation rate distribution in the Milky Way (cite: 2022ApJ...941..162E). The bubble scale of $\sim$ 50 pc could be typical for NGC 628 and is similar to the largest supernova remnants found in the Milky Way (cite: 1988RvMP...60....1O; 2021A&A...648A..30B). However, this typical bubble size in NGC 628 is much larger than the typical size of $\sim$ 6 pc for most SNRs in the Milky Way and it is unknown how many SNs actually contributed to this large size. The peak radial position of the bubble distribution exists at about 1/6 to 1/5 of the disk size and suggests a ring structure with an enhanced star formation history. The existence of this ring requires further investigation because of its implications for the radial density structure and the rotation curve in the disk, as well as for the location of the Inner Lindblad resonance in the galaxy.

![](f1/NGC628-I-R-1.png)

## The origin of large-scale bubbles

The large-scale bubbles could be caused by the superposition of multiple supernova explosions for three reasons:\
1. The shock front traced by the OIII emissions is distributed around the shell of the bubbles (see Fig. [2](#fig2)).\
2. There is triggered star formation at the edges of the bubbles, which is traced by the 11.3$\mu$m and 21$\mu$m emission (see Fig. [1](#fig1) and [3](#fig3)).\
3. The curved magnetic field structure is aligned with the structure of the bubbles.

The size of the large-scale bubbles ($>$ 300 pc) considered here clearly exceeds the size of even the largest SNR in the Milky Way ($\sim$ 50 pc). Such large-scale bubble structures may only result from massive star formation and the contribution of multiple supernova explosions. The shock wave from an SN could compress the surrounding gas and merge with shells from many others (cite: 2023ApJ...944L..24W) to form a large-scale bubble with a surface close to spherical. Depending on the thickness of the disk, the bubble cavity will become cylindrical and form a chimney outflow perpendicular to the disk as seen in neutral hydrogen surveys. The diffuse gas in the disk would be compressed in a circular shell that is also constrained by the embedded local magnetic field and this enriched shell may lead to triggered star formation. A situation similar to that of NGC 628 is found, for instance, in the galaxy NGC 6946 (cite: 2012ApJ...754L..35H).

The radio emission from SNRs results from high-energy electrons accelerated during a supernova explosion and end up spiraling along the magnetic field structure (cite: 2019JApA...40...36G; 2024ApJS..270...21C). (cite: 2017A&A...600A...6M) provides a high-resolution synchrotron radiation map of NGC 628 at 3.1 GHz with resolution up to 8$''$ (FWHM $\approx$ 390 pc; twice of B-field beam in this work). As Figure [6](#figIR) shows, the synchrotron emission is aligned with the spatial distribution of bubbles from (cite: 2017A&A...600A...6M),which includes both the large-scale bubbles (FWHM $\textgreater$ 390 pc, the resolution of synchrotron radiation) and the small-scale bubbles (FWHM $\textless$ 390 pc). These bubbles could be candidates of SuperNova Remnants. The regions with richer synchrotron emissions have massive small-scale bubbles compared with the large-scale bubbles. The small-scale bubbles are located at the spiral arms with rich gas. In the spiral arms, despite impactful physical phenomena like supernova explosions, it proves challenging to propel massive amounts of gas and facilitate the formation of large-scale structures. On the other hand, the diffuse gas surrounding the large-scale bubbles could be pushed by supernovae over greater lengths and form the large-scale structure of bubbles.

The diffuse gas and limited synchrotron emissions surrounding the expansive bubbles on a large scale imply that the number of supernovae contributing to the formation of such bubbles is comparatively modest when juxtaposed with equivalent areas in spiral arm regions. Assuming that the aggregate flux, $I$, of the large-scale bubbles and their scale size, $R$, follow a power-law relation: $$\begin{equation}
\label{eqIR}
    I \propto R^\alpha \propto (\frac{R}{R_0})^{\alpha},
\end{equation}$$ where $R_0$ is the characteristic scale of one SNR, and $\alpha$ signifies the slope between $R$ and $I$ in log-log space. When the flux within the bubble is uniform, the value of $\alpha$ becomes 2 (since the area is proportional to the square of the radius). By fitting the total flux and scale of each large-scale bubble, the derived alpha converges around 1 (less than 2). The growth rate of the flux in the bubbles is below that of the growth in scale. As the bubble’s scale expands, the synchrotron emissions from SNR may undergo dilution.

We adopt a maximum size of a single SNR in the Milky Way ($\sim$ 6 pc) as the characteristic scale populating the bubbles. The SNR number of large-scale bubbles can be estimated by the scale $R$ of the bubbles: $$\begin{equation}
    {\rm N (SNR)} = k(R / R_0) \propto (I/I_0)
\end{equation}$$ Because of the unknown characteristic flux $I_0$, we assume the factor k as 1.

Then the largest bubble, Bubble 1 (scale $\sim$ 1164 pc) contains an estimated 194 SNRs. Details regarding the number of SNRs in other large-scale bubbles can be found in Tab.  [1](#tab1). The observed large-scale bubbles in NGC 628 provide a good picture of the succession of star formation and its history.

# Summary

The magnetic fields of NGC 628 has been measured with the VGT technique using the $^{12}$CO (2-1) emission at the scale of 4$''$ (FWHM $\sim$ 191 pc). The magnetic field is in alignment with the structure of the bubbles in NGC 628 and forms a surrounding ring-like structure leaving a central cavity at the Mid-infrared wavelengths.

1\. The high-resolution magnetic field measured with VGT for the CO emission is ordered and distributed along the spiral arms at the large scale. The result is in agreement with the preview observations of the synchrotron polarization at the low resolution of 18$''$. For smaller-scale bubble sources, the VGT-VDA method has been used to trace the magnetic field and improve accuracy, and the magnetic fields display curved structures.

2\. 20 large-scale bubbles (390 pc -1164 pc) in NGC 628 display a hole-like shape surrounded by a ring structure, which includes rich gas reservoirs and shock wave trails. These large-scale bubbles are all distributed on the edge of spiral arms and are the result of multiple supernova activities.

3\. The distribution of bubble size versus galactocentric distance of a large sample of 1694 bubbles displays a peak for a size around 50 pc at a galactocentric distance of 3k̇pc. The number of bubbles in the galactic distribution increases linearly up to 3 kpc and rapidly decreases beyond this distance. The distribution of bubbles in NGC 628 forms a ring structure that is densely filled with bubbles and reveals the intense star formation history in the central region of NGC 628. The distribution of bubbles is similar to the star formation rate distribution in Milky Way. The bubbles observed in NGC 628 have been observed to be associated with outflow chimneys in neutral hydrogen in other galaxies.

4\. The apparent ring of 50 pc bubble structures at about 3 kpc that surrounds regions of intense star formation in the inner part of the disk in NGC 628 has implications for the radial density structure the rotation curve in the disk, and the location of the Inner Lindblad resonance in the galaxy.

5\. The bubble structure appears to be caused by repeated supernova explosions and prolonged star formation, which squeezes gas towards the edge of the bubbles and triggers new star formation in these compressed regions. The organization of the magnetic field in the shock boundary surrounding the bubble structures will be perpendicular to the propagation direction of the SNR shocks and parallel to the shell of OIII gas. While these bubbles are relics of past star formation, they continue to trigger new star formation.

6\. The large-scale bubbles could be caused by the contribution of massive/multiple supernova explosions.

The multiple supernovae drive the diffuse gas over a large length and cause the large-scale bubbles. Scaling of the power needed to form such large-scale bubbles suggests contributions from large numbers (up to hundreds) of single SNR as observed in the Milky Way. The number and size of the bubbles observed in NGC 628 reveal the long-term star formation history in the galaxy, which is a common evolutionary process in galaxies.

Further plan are to observe the magnetic field using dust polarization at sub-arcsec resolution in order to study the small-scale magnetic field structure of the large-scale bubbles. Analysis of a face-on galaxy will promote understanding of similar physical processes in the Milky Way.

# Acknowledgements

We thank the referee for the careful reading of the paper and the constructive comments. This work was mainly funded by the National Natural Science foundation of China (NSFC) under grant No. 11973076. Partial funding was obtained from the CAS "Light of West China" Program under grant No. 2020-XBQNXZ-017, the NSFC under grant Nos. 11903070, 12173075, 12103082, and 12303027, the Natural Science Foundation of Xinjiang Uygur Autonomous Region under grant No. 2022D01E06, the Heaven Lake Hundred Talent Program of Xinjiang Uygur Autonomous Region of China, the Tianshan Innovation Team Plan of Xinjiang Uygur Autonomous Region (2022D14020), Xinjiang Key Laboratory of Radio Astrophysics (No. 2022D04033), the Youth Innovation Promotion Association CAS, and the Project of Xinjiang Uygur Autonomous Region of China for Flexibly Fetching in Upscale Talents and the Hebei NSF No. A2022109001. A.L. and Y.H. acknowledge the support of the NASA ATP 80NSSC20K0542, AAH7546, and NASA TCAN 144AAG1967. W.A.B has been funded by the Chinese Academy of Sciences President’s International Fellowship Initiative grant No. 2021VMA0008 and 2022VMA0019.

natexlab

(ref: 2014ApJS..212....1A) Anderson, L. D., Bania, T. M., Balser, D. S., et al. 2014, ApJS, 212, 1, doi: [`10.1088/0067-0049/212/1/1`](http://doi.org/10.1088/0067-0049/212/1/1)

(ref: 2021A&A...647A..78A) Arzoumanian, D., Furuya, R. S., Hasegawa, T., et al. 2021, A&A, 647, A78, doi: [`10.1051/0004-6361/202038624`](http://doi.org/10.1051/0004-6361/202038624)

(ref: 1985ApJ...297...61B) Balbus, S. A., & Cowie, L. L. 1985, ApJ, 297, 61, doi: [`10.1086/163503`](http://doi.org/10.1086/163503)

(ref: 2015A&ARv..24....4B) Beck, R. 2015, A&ARv, 24, 4, doi: [`10.1007/s00159-015-0084-4`](http://doi.org/10.1007/s00159-015-0084-4)

(ref: 2004NewAR..48.1289B) Beck, R., & Gaensler, B. M. 2004, New A Rev., 48, 1289, doi: [`10.1016/j.newar.2004.09.013`](http://doi.org/10.1016/j.newar.2004.09.013)

(ref: 2013pss5.book..641B) Beck, R., & Wielebinski, R. 2013, in Planets, Stars and Stellar Systems. Volume 5: Galactic Structure and Stellar Populations, ed. T. D. Oswalt & G. Gilmore, Vol. 5, 641, doi: [`10.1007/978-94-007-5612-0_13`](http://doi.org/10.1007/978-94-007-5612-0_13)

(ref: 2021A&A...648A..30B) Becker, W., Hurley-Walker, N., Weinberger, C., et al. 2021, A&A, 648, A30, doi: [`10.1051/0004-6361/202040156`](http://doi.org/10.1051/0004-6361/202040156)

(ref: 2004MNRAS.353..550B) Bell, A. R. 2004, MNRAS, 353, 550, doi: [`10.1111/j.1365-2966.2004.08097.x`](http://doi.org/10.1111/j.1365-2966.2004.08097.x)

(ref: 1990acr..book.....B) Berezinskii, V. S., Bulanov, S. V., Dogiel, V. A., & Ptuskin, V. S. 1990, Astrophysics of cosmic rays

(ref: Cabral_lic) Cabral, B., & Leedom, L. C. 1993, in Proceedings of the 20th Annual Conference on Computer Graphics and Interactive Techniques, SIGGRAPH ’93 (New York, NY, USA: Association for Computing Machinery), 263–270, doi: [`10.1145/166117.166151`](http://doi.org/10.1145/166117.166151)

(ref: 2000ApJ...539..273C) Cho, J., & Vishniac, E. T. 2000, ApJ, 539, 273, doi: [`10.1086/309213`](http://doi.org/10.1086/309213)

(ref: 2006ApJ...649..759C) Churchwell, E., Povich, M. S., Allen, D., et al. 2006, ApJ, 649, 759, doi: [`10.1086/507015`](http://doi.org/10.1086/507015)

(ref: 2024ApJS..270...21C) Cotton, W. D., Kothes, R., Camilo, F., et al. 2024, ApJS, 270, 21, doi: [`10.3847/1538-4365/ad0ecb`](http://doi.org/10.3847/1538-4365/ad0ecb)

(ref: 2021ApJ...915L...8D) Duan, D., He, J., Bowen, T. A., et al. 2021, ApJL, 915, L8

(ref: 2022ApJ...941..162E) Elia, D., Molinari, S., Schisano, E., et al. 2022, ApJ, 941, 162, doi: [`10.3847/1538-4357/aca27d`](http://doi.org/10.3847/1538-4357/aca27d)

(ref: 1980ApJ...242..528E) Elmegreen, D. M. 1980, ApJ, 242, 528, doi: [`10.1086/158486`](http://doi.org/10.1086/158486)

(ref: 2022A&A...659A.191E) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: 2019PhRvD..99j3023E) Evoli, C., Aloisio, R., & Blasi, P. 2019, Phys. Rev. D, 99, 103023, doi: [`10.1103/PhysRevD.99.103023`](http://doi.org/10.1103/PhysRevD.99.103023)

(ref: 1976RvMP...48..161G) Ginzburg, V. L., & Ptuskin, V. S. 1976, Reviews of Modern Physics, 48, 161, doi: [`10.1103/RevModPhys.48.161`](http://doi.org/10.1103/RevModPhys.48.161)

(ref: 1995ApJ...438..763G) Goldreich, P., & Sridhar, S. 1995, ApJ, 438, 763, doi: [`10.1086/175121`](http://doi.org/10.1086/175121)

(ref: 2017ApJ...835...41G) González-Casanova, D. F., & Lazarian, A. 2017, ApJ, 835, 41, doi: [`10.3847/1538-4357/835/1/41`](http://doi.org/10.3847/1538-4357/835/1/41)

(ref: 2019JApA...40...36G) Green, D. A. 2019, Journal of Astrophysics and Astronomy, 40, 36, doi: [`10.1007/s12036-019-9601-6`](http://doi.org/10.1007/s12036-019-9601-6)

(ref: 2012ApJ...754L..35H) Heald, G. H. 2012, ApJL, 754, L35, doi: [`10.1088/2041-8205/754/2/L35`](http://doi.org/10.1088/2041-8205/754/2/L35)

(ref: 2022ApJ...941...92H) Hu, Y., Lazarian, A., Beck, R., & Xu, S. 2022a, ApJ, 941, 92, doi: [`10.3847/1538-4357/ac9df0`](http://doi.org/10.3847/1538-4357/ac9df0)

(ref: 2022MNRAS.511..829H) Hu, Y., Lazarian, A., & Wang, Q. D. 2022b, MNRAS, 511, 829, doi: [`10.1093/mnras/stac159`](http://doi.org/10.1093/mnras/stac159)

(ref: 2021ApJ...915...67H) Hu, Y., Lazarian, A., & Xu, S. 2021a, ApJ, 915, 67, doi: [`10.3847/1538-4357/ac00ab`](http://doi.org/10.3847/1538-4357/ac00ab)

(ref: HXL21) Hu, Y., Xu, S., & Lazarian, A. 2021b, ApJ, 911, 37

(ref: 2018MNRAS.480.1333H) Hu, Y., Yuen, K. H., & Lazarian, A. 2018, MNRAS, 480, 1333, doi: [`10.1093/mnras/sty1807`](http://doi.org/10.1093/mnras/sty1807)

(ref: 2019ApJ...886...17H) —. 2019, ApJ, 886, 17, doi: [`10.3847/1538-4357/ab4b5e`](http://doi.org/10.3847/1538-4357/ab4b5e)

(ref: 2019MNRAS.488.1141J) Jayasinghe, T., Dixon, D., Povich, M. S., et al. 2019, MNRAS, 488, 1141, doi: [`10.1093/mnras/stz1738`](http://doi.org/10.1093/mnras/stz1738)

(ref: 2020AJ....160..167J) Jones, T. J., Kim, J.-A., Dowell, C. D., et al. 2020, AJ, 160, 167, doi: [`10.3847/1538-3881/abada8`](http://doi.org/10.3847/1538-3881/abada8)

(ref: 2004AJ....127.2031K) Karachentsev, I. D., Karachentseva, V. E., Huchtmeier, W. K., & Makarov, D. I. 2004, AJ, 127, 2031, doi: [`10.1086/382905`](http://doi.org/10.1086/382905)

(ref: 1994RPPh...57..325K) Kronberg, P. P. 1994, Reports on Progress in Physics, 57, 325, doi: [`10.1088/0034-4885/57/4/001`](http://doi.org/10.1088/0034-4885/57/4/001)

(ref: 2000ApJ...537..720L) Lazarian, A., & Pogosyan, D. 2000, ApJ, 537, 720, doi: [`10.1086/309040`](http://doi.org/10.1086/309040)

(ref: 1999ApJ...517..700L) Lazarian, A., & Vishniac, E. T. 1999, ApJ, 517, 700, doi: [`10.1086/307233`](http://doi.org/10.1086/307233)

(ref: 2021ApJ...923...53L) Lazarian, A., & Xu, S. 2021, ApJ, 923, 53, doi: [`10.3847/1538-4357/ac2de9`](http://doi.org/10.3847/1538-4357/ac2de9)

(ref: 2018ApJ...853...96L) Lazarian, A., & Yuen, K. H. 2018, ApJ, 853, 96, doi: [`10.3847/1538-4357/aaa241`](http://doi.org/10.3847/1538-4357/aaa241)

(ref: 2014ApJ...792..122L) Lee, W.-K. 2014, ApJ, 792, 122, doi: [`10.1088/0004-637X/792/2/122`](http://doi.org/10.1088/0004-637X/792/2/122)

(ref: 2012ApJ...756...45L) Lee, W.-K., & Shu, F. H. 2012, ApJ, 756, 45, doi: [`10.1088/0004-637X/756/1/45`](http://doi.org/10.1088/0004-637X/756/1/45)

(ref: 2021ApJS..257...43L) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: 2017NatAs...1E.158L) Li, H.-B., Jiang, H., Fan, X., Gu, Q., & Zhang, Y. 2017, Nature Astronomy, 1, 0158, doi: [`10.1038/s41550-017-0158`](http://doi.org/10.1038/s41550-017-0158)

(ref: 2023MNRAS.519.1068L) Liu, M., Hu, Y., Lazarian, A., Xu, S., & Soida, M. 2023, MNRAS, 519, 1068, doi: [`10.1093/mnras/stac3518`](http://doi.org/10.1093/mnras/stac3518)

(ref: 2020ApJ...888...66L) Lopez-Rodriguez, E., Dowell, C. D., Jones, T. J., et al. 2020, ApJ, 888, 66, doi: [`10.3847/1538-4357/ab5849`](http://doi.org/10.3847/1538-4357/ab5849)

(ref: 2018PASP..130h4101L) Luisi, M., Anderson, L. D., Bania, T. M., et al. 2018, PASP, 130, 084101, doi: [`10.1088/1538-3873/aac8e9`](http://doi.org/10.1088/1538-3873/aac8e9)

(ref: 2001ApJ...554.1175M) Maron, J., & Goldreich, P. 2001, ApJ, 554, 1175, doi: [`10.1086/321413`](http://doi.org/10.1086/321413)

(ref: 2020FrASS...7...83M) Matteini, L., Franci, L., Alexandrova, O., et al. 2020, Frontiers in Astronomy and Space Sciences, 7, 83

(ref: 2007ARA&A..45..565M) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565, doi: [`10.1146/annurev.astro.45.051806.110602`](http://doi.org/10.1146/annurev.astro.45.051806.110602)

(ref: 2017A&A...600A...6M) Mulcahy, D. D., Beck, R., & Heald, G. H. 2017, A&A, 600, A6, doi: [`10.1051/0004-6361/201629907`](http://doi.org/10.1051/0004-6361/201629907)

(ref: 1988RvMP...60....1O) Ostriker, J. P., & McKee, C. F. 1988, Reviews of Modern Physics, 60, 1, doi: [`10.1103/RevModPhys.60.1`](http://doi.org/10.1103/RevModPhys.60.1)

(ref: 2022ApJ...936L..14P) Pontoppidan, K. M., Barrientes, J., Blome, C., et al. 2022, ApJL, 936, L14, doi: [`10.3847/2041-8213/ac8a4e`](http://doi.org/10.3847/2041-8213/ac8a4e)

(ref: 1998ApJ...509..212S) Strong, A. W., & Moskalenko, I. V. 1998, ApJ, 509, 212, doi: [`10.1086/306470`](http://doi.org/10.1086/306470)

(ref: 1988ARA&A..26..145T) Tenorio-Tagle, G., & Bodenheimer, P. 1988, ARA&A, 26, 145, doi: [`10.1146/annurev.aa.26.090188.001045`](http://doi.org/10.1146/annurev.aa.26.090188.001045)

(ref: 2023ApJ...946....8T) Tram, L. N., Bonne, L., Hu, Y., et al. 2023, ApJ, 946, 8, doi: [`10.3847/1538-4357/acaab0`](http://doi.org/10.3847/1538-4357/acaab0)

(ref: 2016ApJ...816...15W) Wang, X., Tu, C., Marsch, E., He, J., & Wang, L. 2016, ApJ, 816, 15

(ref: 2023ApJ...944L..24W) Watkins, E. J., Barnes, A. T., Henny, K., et al. 2023, ApJL, 944, L24, doi: [`10.3847/2041-8213/aca6e4`](http://doi.org/10.3847/2041-8213/aca6e4)

(ref: 1988ARA&A..26..295W) Weiler, K. W., & Sramek, R. A. 1988, ARA&A, 26, 295, doi: [`10.1146/annurev.aa.26.090188.001455`](http://doi.org/10.1146/annurev.aa.26.090188.001455)

(ref: 2021ApJ...922..264X) Xu, S. 2021, ApJ, 922, 264, doi: [`10.3847/1538-4357/ac2d8f`](http://doi.org/10.3847/1538-4357/ac2d8f)

(ref: 2019ApJ...878..157X) Xu, S., Ji, S., & Lazarian, A. 2019, ApJ, 878, 157, doi: [`10.3847/1538-4357/ab21be`](http://doi.org/10.3847/1538-4357/ab21be)

(ref: 2022ApJ...927...94X) Xu, S., & Lazarian, A. 2022, ApJ, 927, 94, doi: [`10.3847/1538-4357/ac4dfd`](http://doi.org/10.3847/1538-4357/ac4dfd)

(ref: 2021ApJ...910..161Y) Yuen, K. H., Ho, K. W., & Lazarian, A. 2021, ApJ, 910, 161, doi: [`10.3847/1538-4357/abe4d4`](http://doi.org/10.3847/1538-4357/abe4d4)

(ref: 2017ApJ...837L..24Y) Yuen, K. H., & Lazarian, A. 2017, ApJL, 837, L24, doi: [`10.3847/2041-8213/aa6255`](http://doi.org/10.3847/2041-8213/aa6255)

(ref: 2020ApJ...898...65Y) —. 2020, ApJ, 898, 65, doi: [`10.3847/1538-4357/ab9307`](http://doi.org/10.3847/1538-4357/ab9307)

(ref: 2022ApJ...934...45Z) Zhao, M., Zhou, J., Hu, Y., et al. 2022, ApJ, 934, 45, doi: [`10.3847/1538-4357/ac78e8`](http://doi.org/10.3847/1538-4357/ac78e8)

(ref: 2024ApJ...961..124Z) Zhao, M., Li, G.-X., Zhou, J., et al. 2024, ApJ, 961, 124, doi: [`10.3847/1538-4357/ad09df`](http://doi.org/10.3847/1538-4357/ad09df)

# A CO and OIII intensity map

Figure [7](#fig6) shows the intensity maps of the main tracers in this work $^{12}$CO (2-1) and OIII.

![](f1/NGC628-2mom0.png)

</paper>

Write the methods card for this paper.