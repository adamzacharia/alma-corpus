# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...974..150W\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...974..150W",
 "title": "Accretion and Outflow in Orion-KL Source I",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Wright, Melvyn",
 "n_authors": 9,
 "arxiv_id": "2408.05114",
 "doi": "10.3847/1538-4357/ad7026",
 "alma_projects_linked_by_archive": [
  "2016.1.00165.S",
  "2017.1.00497.S"
 ]
}
```

Paper text:
<paper>
# Accretion and Outflow in Orion-KL Source I

## Abstract

We present ALMA observations of SiO, SiS, $\rm H_2O$, NaCl, and SO line emission at $\sim$30 to 50 mas resolution. These images map the molecular outflow and disk of Orion Source I (SrcI) on $\sim$12 to 20 AU scales. Our observations show that the flow of material around SrcI creates a turbulent boundary layer in the outflow from SrcI which may dissipate angular momentum in the rotating molecular outflow into the surrounding medium. Additionally, the data suggests that the proper motion of SrcI may have a significant effect on the structure and evolution of SrcI and its molecular outflow. As the motion of SrcI funnels material between the disk and the outflow, some material may be entrained into the outflow and accrete onto the disk, creating shocks which excite the NaCl close to the disk surface.

# Introduction

Massive stars play an important role in numerous astrophysical processes, but their formation and evolution remains ambiguous. Current theory regarding high-mass ($>8 M_\odot$) protostellar evolution strongly suggests that accretion onto the central parts via disks, and the specific geometry and rate are key variables that dictate the characteristics of the resulting star (cite: Caretti_o_Garatti_2017; Hosokawa2010). Efforts to find a mechanism that reconciles the in-falling accreted material and outgoing outflows/radiation have resulted in numerous theories regarding the necessary rate and three-dimensional accretion flow geometry e.g., (cite: Hosokawa2010; Whitney_2013; Kuiper_2011). Other theories, such as stellar mergers (cite: Bonnell_1998) and competitive accretion (cite: Bonnell_2008) have also been considered. However, regardless of the specifics, the mechanism must be able to move material into the protostar for it to continue growing.

Study of the evolution of high-mass protostars is possible in the Kleinmann-Low Nebula in Orion (Orion-KL). At a distance of 415pc (cite: Menten2007; Kim2008; Kounkel2018), Orion-KL is the nearest interstellar cloud with observable massive star formation.

Observations of Orion-KL and simulations suggest that three stars were involved in a dynamical decay event approximately 550 years ago, which ejected them from a multi-star system (cite: Bally2017; Bally2020). One of these stars, the Becklin-Neugebauer (BN) object, has a proper motion of $\sim$26 $\rm km~s^{-1}$  northwestward. Radio Source I (SrcI) is another star involved, and moves at $\sim$10 $\rm km~s^{-1}$ southward. Finally, near-infrared source x (SrcX) moves at $\sim$55 $\rm km~s^{-1}$ southeastward (cite: Dzib_2017; Luhman_2017; Rodgriguez2017).

Direct observation of the central object in SrcI is not possible as the high opacity of the continuum emission from the SrcI disk conceals the central source. The specific nature and mass of this object has been the subject of extensive study and theorization. Estimation-through conservation of linear momentum and dynamical simulation best agreed with SrcI being a $\sim20 M_\odot$ binary (proto-)star system (cite: Rodriguez2017; Rodriguez2020; Bally2020; Goddi2011b). (cite: Ginsburg2018) found SrcI to have a mass of $15 \pm 2 M_\odot$ by fitting the rotation curve of the $5_{5,0}-6_{4,3}$ spectral line.

To build stronger constrains on its nature, we explore the outflow SrcI produces due to its close association with accretion. Outflows provide an avenue to carry excess angular momentum out of the system, enabling accreting matter to fall upon the star. This transfer of momentum and kinetic energy influences star formation in surrounding regions.

SrcI has been well-studied as it is the closest observable high-mass protostar with a circumstellar disk and molecular outflow (cite: Hirota2014; Plambeck2016; Ginsburg2018). The molecular outflow from SrcI is prominent in SiO, SO, and SiS (cite: Hirota2020; Wright2020; Lopez-Vazquez2020). The disk and outflow are associated with SiO and masers (cite: Reid2007; Goddi2009; Goddi2011; Plambeck2009; Matthews2010; Niederhofer2012; Greenhill2013). The mechanisms that drive outflows, such as the entrainment of molecular gas by a higher-velocity jet or an MHD-driven outflow by magneto-centrifugal disk winds, are still poorly understood (cite: Commercon2022).

In this paper, we re-examine our observational data from ALMA, using several molecular spectral lines that trace key structures in SrcI to look for signatures of accretion in SrcI.

# Observations

We used data at $223$ GHz (ALMA Band 6; B6) and $340$ GHz (ALMA Band 7; B7) as described in (cite: Ginsburg2018). This data was processed into images using both uniform and natural weighting of the uv-data. The Brigg’s visibility weighting was set to robust $=0$ to avoid the excessive weight being given to visibilities in relatively sparsely filled regions of the uv-plane by uniform weighting. For naturally-weighted images, we set robust $=2$ to map the low-brightness, more extended emission. The observational parameters are given in Table 1 for the uniformly-weighted uv-data.

Within these bands, several molecular species have been identified as present in SrcI: SiO, SiS, , NaCl, and SO. Based on the shape and location of the emission from these lines, SiO and SiS have been interpreted as tracers of a wide-angle outflow along the minor axis of a circumbinary disk, while and NaCl have a strong presence on the surface of/within the circumbinary disk. The structure of SO is more complex and will be further explored in later sections.

The high opacity at $220$ - $330$ GHz of the continuum emission from the SrcI disk conceals the internal structure of the disk. The less opaque $99$ GHz continuum observations from (cite: Wright2022) will also be analyzed as they reveal details of disk’s structure. Emission from molecules associated with the disk gives us information about the structure and kinematics of the SrcI disk and its interaction with the material in its immediate environment.

Hereafter, we discuss the specific molecular lines $^{28}$SiO,

$^{29}$SiO,

SiS,

, NaCl, and SO to analyze the structure and kinematics of molecular lines closely associated with SrcI for evidence of accretion. The spectral lines discussed in this paper are listed in Table 2.

# Results

In this section we present the spectral line data as the average intensity and average velocity of the emission across the spectral line. These were derived from the intensity and velocity of each spectral channel. The contours map the intensity of the emission. This may be expressed in units of Jy/beam or Kelvin. We give the equivalent Rayleigh-Jeans brightness in Kelvin for the peak value in the image. The average velocity is shown as a color scale in units of $\rm km~s^{-1}$ .

## The Molecular Outflow; SiO and SiS

[1](#fig:sio_mom0+1) shows the $217.105$ GHz $^{28}$SiO$\quad v=0\quad(J=5-4)$ emission with a peak brightness of $1078$ K at a velocity resolution of $2$ $\rm km~s^{-1}$ . This figure also shows $214.385$ GHz $^{29}$SiO$\quad v=0\quad(J=5-4)$ emission with a peak brightness of $18300$ K at a velocity resolution of $2$ $\rm km~s^{-1}$ . The high peak brightness temperature of the $^{29}$SiO emission indicates the presence of masers.

[2](#fig:sis_mom0+1) shows the $217.818$ GHz SiS$\quad v=0\quad(J=12-11)$ emission with a peak brightness of $409$ K with a velocity resolution of $2$ $\rm km~s^{-1}$ . The SiS emission traces a shell-like structure along the boundaries of the SiO outflow (cite: Wright2020). This higher-resolution SiS image reveals the complex structure it traces.

## SO

[3](#fig:son344GHz) shows the 344.31 GHz SO emission with natural weighting of the u-v data to emphasize the larger scale structure. The peak brightness with 1 $\rm km~s^{-1}$ velocity resolution is 375 K.

##  and NaCl Emission

[4](#fig:nacl_mom0+1) shows the and Emission. The 232.687 GHz line (5(5,0), v$_{2}$=1 - 6(4,3), v$_{2}$=1) is more closely associated with the SrcI disk than the SiO and SiS, which primarily trace the molecular outflow.

[4](#fig:nacl_mom0+1) also shows the 232.51 GHz NaCl$\quad v=1\quad(J=18-17)$ emission with a peak brightness of $197$ K with a velocity resolution of $2$ $\rm km~s^{-1}$ .

# Discussion

In this section we discuss each of the molecular lines observed, and the regions of the disk and outflow that each traces. The distribution of the molecular lines depends on the formation and destruction of the molecules, and we include a discussion of the chemical interactions between the outflow and ambient material. The structure and kinematics of the SiS suggest that ambient material may be entrained into the molecular outflow leading to the export of angular momentum from the outflow. We discuss the evidence for Bondi-Hoyle-Lyttleton accretion onto the disk around Source I, and the evolution of the disk and the protostar(s)

## The Bipolar Outflow

(cite: Hirota2017) fitted a hollow cone model to the 484.056 GHz Si$^{18}$O $J=12-11$ line and constrained the launching radius and outward velocity of the outflow to be $>$10 AU and $\sim$10 km s$^{-1}$, respectively. From these results, (cite: Hirota2017) concluded that the rotating outflow in SrcI is likely driven by a magneto-centrifugal disk wind. (cite: Hirota2017) note that the critical density required to excite the $J=12-11$ transition ($6\times10^7$ cm$^{-3}$) is higher than those of $J=2-1$ at 86 GHz ($3\times10^5$ cm$^{-3}$) and $J=5-4$ at 217 GHz ($4\times10^6$ cm$^{-3}$). Additionally, the $^{28}$SiO molecular line may be highly opaque, as discussed by (cite: Lopez-Vazquez2020). The Si$^{18}$O isotopologue is expected to be optically thin, as it traces regions of higher density than the optically thick Si$^{16}$O lines.

Both SiO isotopes shown here in [1](#fig:sio_mom0+1) clearly trace the wide-angle outflow in SrcI, with the velocity structure growing in complexity away from the disk. In [1](#fig:sio_mom0+1), a clear velocity gradient across the (projected) minor axis of the disk can be seen in regions close to the central source. The smooth blue-green-red transition from SE-NW indicates that the rotational velocity of these molecules dominates in these regions. Further away from the center, the smooth velocity gradient disappears and the velocities become "mixed." The $^{28}$SiO image shows little blue-shifted emission beyond the small amount present close the center, with the outer regions of the outflow dominated by an irregular patchwork of green and red-shifted emission. A similar pattern can be seen in the $^{29}$SiO. These features are roughly consistent with the rotating expanding model presented by (cite: Hirota2017). [5](#fig:sio+sis) shows the velocity channel maps of the outflow seen in SiO and SiS emission. At 54$\times$34 mas (22$\times$14 au) resolution, the SiS image shows a shell-like structure. The visible velocity structure suggests that there is a turbulent layer on the outside of the SiO emission.

[6](#fig:29sio.4cuts) shows the 214.39 GHz $v=0$ $J=5-4$, and 217.82 GHz SiS $v=0$ $J=12-11$ emission integrated over -10 to +20 km s$^{-1}$. Four cuts are drawn across the outflow: along the outflow edges (PA = 122$\ensuremath{^\circ}$ & 172$\ensuremath{^\circ}$), along the circumbinary disk major axis (PA = 142$^\circ$), and along the outflow axis (PA = 52$^\circ$).

[7](#fig:29sio.4pv) shows position-velocity profiles for emission along these 4 cuts. Two of these cuts (PA = 122$\ensuremath{^\circ}$ & 172$\ensuremath{^\circ}$) are along the edges of the outflow. The line-of-sight velocity widths decrease from the full width of the emission close the the disk (-20 to +30 km s$^{-1}$ at 0$''$) to $\sim$ –5 to +15 km s$^{-1}$ at $\sim$ 0.2 to 0.3$''$ (80 to 120 AU) from the disk.

The position-velocity profile along the disk’s major axis (PA $=142\ensuremath{^\circ}$) follows the rotation of the disk with strong absorption at red-shifted velocities. The position-velocity profile along the disk minor axis (PA $=52\ensuremath{^\circ}$) measures the radial expansion velocity, with small contributions, $v_{z}\times cos(i)$, from the outflow velocity along the minor axis, and from the rotation velocity. The line of sight velocity along the disk’s minor axis is $\sim$ –5, and $\sim$ +15 km s$^{-1}$ from the front and back side of the outflow.

## Entrainment of ambient material into the Molecular Outflow ?

[8](#fig:sis.4pv) shows position-velocity profiles for emission along these 4 cuts. The emission shows a more complex structure than . Along the edges of the outflow (PA = 122$\ensuremath{^\circ}$ & 172$\ensuremath{^\circ}$), the line-of-sight velocity range is consistently centered around the the systemic velocity of SrcI ($\sim$ +5 km s$^{-1}$). The velocity width decreases from its maximum ($\sim$ –14 to +24 km s$^{-1}$) close the the disk to $\sim$ –5, and +15 km s$^{-1}$ at $\sim$ 0.4$''$ (160 AU) from the disk. The line of sight velocity along the edges of the outflow measures the rotation velocity, $v_{\phi}\times sin(i)$, where $i$ is the inclination of the disk to the line of sight. Assuming a disk inclination 80 to 85$^\circ$, there are small contributions from the radial expansion velocity, $v_{r}\times cos(i)$, and the outflow velocity along the minor axis, $v_{z}\times cos(i)$. Both and SiS show that the rotational velocity decreases with distance from the disk, consistent with the results shown by (cite: Hirota2017) for the Si$^{18}$O $J=12-11$ line.

Multiple velocity components can be seen along the edges of the outflow in [7](#fig:29sio.4pv) and [8](#fig:sis.4pv).

The position-velocity profile along the disk major axis (PA = 142$^\circ$) follows the rotation of the disk. The is not seen in absorption along the major axis of the disk.

The position-velocity profile along the disk minor axis (PA = 52$^\circ$, lower-right sub-image of [8](#fig:sis.4pv)) measures the radial expansion velocity, with smaller contributions from the outflow velocity along the minor axis, and the rotation velocity. The line of sight velocity in along the disk minor axis increases in a parabolic fashion, i.e. more rapidly close the the disk. Gaussian fits to the spectra along the minor axis show that the line of sight velocity of the emission is initially centered at the system velocity at regions close to the disk ($\sim$ +5 km s$^{-1}$ at $<$ 0.1$''$ (40 AU) from the disk). This diverges into two distinct, much thinner velocity structures in either direction away from the disk. The NW outflow has velocity structures centered at $\sim$ –8 and $\sim$ +17 km s$^{-1}$ (at $\sim$ +0.3$''$). The SE outflow has structures centered at $\sim$ –4 and $\sim$ +17 km s$^{-1}$ (at $\sim$ -0.3$''$). As expected, this two-pronged velocity structure is due to the contributions of the far and close sides of the outflow.

The radial velocity is $\sim$ 4 km s$^{-1}$ more blue-shifted on the NW side of the disk. Assuming the same opening angle of the outflow on both sides of the disk, this difference in the line of sight velocity along the disk minor axis measures the outflow velocity, $v_z \times cos(i)$, where $i$ is the inclination of the disk to the line of sight. Assuming a disk inclination 80 to 85$^\circ$, the implied outflow velocity, $v_z\sim$23 to 45 km s$^{-1}$.

For comparison, (cite: Hirota2017) found, using the 484 GHz line, a radial velocity ($v_r$) between $\sim$ 8 to 12 km s$^{-1}$ and a rotation velocity ($v_{\phi}$) which decreases from $\sim$ 7 km s$^{-1}$ at 50 AU from the disk to $\sim$ 2 km s$^{-1}$ at 150 AU from the disk.

The relative velocity of the ambient material is roughly parallel to the plane of the disk and perpendicular to the direction of the outflow. In consequence, the wide-angled nature of the outflow poses a significant disruption to the flow of the ambient material around SrcI.

Additionally, the outflow appears to be co-moving with the disk. It is not swept back by ram pressure from its motion through the medium. Material ejected from the disk earlier in its trajectory seems to move in tandem with the disk. Naturally, this raises the question of how this ejected material is maintaining its momentum and connection to the central disk.

A possible explanation is that the outflow is being stiffened by magnetic fields (cite: Hirota2020). It is also possible that the outflow’s density, when compared to the external medium, is high enough to render the effect of motion negligible. The outflow from SrcI has a larger cross section than the edge-on disk, and intercepts the ambient medium which it is moving through. Assuming an ambient density, n\[\] $\sim$1.6 $\times$ 10$^5$ cm$^{-3}$ (cite: Snell1984), a velocity 10 $\rm km~s^{-1}$ ,  and cross sectional dimensions of 1000 $\times$ 200 AU for the SrcI outflow, the ambient mass flow is $\sim$ 10$^{-5}$ M$_{\odot}$$\mathrm{yr^{-1}}$, or $\sim$5 $\times$ 10$^{-3}$ M$_{\odot}$ over the $\sim$ 550 years since the BN/SrcI encounter. This is comparable to the estimated mass in the outflow, which ranges from $10^{-5}-10^{-3}$ M$_\odot$ $\mathrm{yr^{-1}}$. These estimates may be affected by the motion of SrcI through the BN/SrcI explosion debris (cite: Wright2022).

It is notable that (cite: Lopez-Vazquez2020) fitted position-velocity (PV) profiles to SiO and SiS lines and found that a model of a rotating molecular envelope accreting onto the outflow (cite: Ulrich1976) was not a good fit to the data. However, the dilution of the rotational velocity with distance from the disk (as noted above) suggests that some of the ambient material may be entrained by the rotating outflow. In laboratory experiments, (cite: Pilloch_2021) found that dry silicate dust becomes more sticky as the temperature increases, by a factor $\sim$10 up to 1000K, and then by another factor $\sim$100 for temperatures $\sim$1200K. Compression and shock heating of the envelope of the outflow may thus make adhesion and entrainment of some ambient material into the outflow more likely.

A final point of note is that the emission does not extend all the way to the disk surface, unlike the (refer to [2](#fig:sis_mom0+1)). The parabolic increase in the radial velocity ($v_r$) at $\sim$40 - 80AU from the disk where the brightest emission is located could result from ambient material being funnelled between the disk and the outflow (refer to [8](#fig:sis.4pv)). The velocity difference between the ambient material and the rotating outflow would result in shocks and heating of the outflow. Note that it is at this distance from the disk where the outflow expands and changes from co-rotation with the disk, and ground state masers appear in the J=1-0 and J=2-1 transitions ((cite: Greenhill2013); (cite: Hirota2020)).

(cite: Greenhill2013) suggested that shocks resulting from a decease in the Alfven velocity to a point below the outflow velocity may trigger the appearance of maser emission in the outflow at $\sim$100 AU. Shock heating from the flow of ambient material funnelled between the disk and the outflow provide an alternative explanation consistent with our observations. The maps the boundary of the outflow mapped in SiO, suggesting chemical interactions between the outflow and ambient material.

## Chemical Interactions Between the Outflow and Ambient Material

(cite: Li_2015) studied the sulfur chemistry in 36 sources in massive star-forming regions, observing OCS, , , , and SO transitions. Their results suggest that is likely the primary sulfur-carrying molecule in massive hot cores. The column density and abundance of OCS were generally higher than CS and SO as well. The hot core model of Orion KL could reproduce the general trend ( $>$ OCS $>$ CS $>$ SO) observed in this paper. is likely to be the most abundant gas-phase sulfur-containing molecule in hot massive cores. Since hydrogenation is expected to be the most efficient process on grains, could be formed on interstellar grains (cite: van_Dishoeck_1998). During the cold collapse phase of star formation, sulfur atoms freeze out onto grains and remain there in the form of until core heating begins. At this point, is evaporated from the grains and rapidly undergoes reactions which drive the production of SO and ((cite: Charnley_1997); (cite: Wakelam_2005); (cite: Wakelam_2011)). The initial destruction of by is more efficient in high-mass protostars compared to in lower-mass ones as water is more abundant (cite: van_der_Tak_2006).

The observed SiS shell around the outflow may be produced in shocks from S-bearing molecular species in the ambient medium and SiO (or other Si-bearing molecules) in the outflow. Models by (cite: Pineau1993) of C-type shocks with velocities between 5 and 40 $\rm km~s^{-1}$ and densities between $10^{4}$ and $10^{6}$ cm$^{-3}$ showed an enhancement of SO and abundances by 2 orders of magnitude. SO decreases quickly after the passage of a shock, whilst is enhanced during and for some time after the shock. The relative velocity of the ambient medium from the proper motion of SrcI and the rotation and expansion velocity of the disk and outflow provides a range of shock velocities between $\sim$ 0 and 30$\rm km~s^{-1}$ .

[6](#fig:29sio.4cuts) shows that the SiS has a complex structure, which may be evidence for this turbulent mixing. However, reactions with both atomic hydrogen and atomic oxygen will both destroy SiS rapidly. We can estimate a timescale from the SiS layer thickness and the diffusion/turbulent velocity. Estimating a thickness of 40 AU and velocity of $\sim$10 $\rm km~s^{-1}$ from the observed SiS images, we would expect the SiS to persist for $\sim$20 yr after formation.

Finally, we make note of a possible chemical interaction occurring between the SiO in the outflow and the SO in the ambient medium. (cite: Wright2020) found that SiS appears to map the boundary layer of the SiO outflow, and co-rotates with the SiO. This raises questions about the potential role of SO in the formation chemistry of SiS.

Several studies have examined potential formation pathways for SiS in recent years, motivated by its proposed key role in the formation of sulfide dust grains (cite: Doddipatla:2021:eabg7003). Three pathways to forming SiS are worth consideration:

$$\begin{align}
    \ce{Si + SH &-> SiS + H} \label{si_sh}\\
    \ce{Si + H2S &-> SiS + H2} \label{si_h2s} \\
    \ce{SiH + S &-> SiS + H}. \label{sih_s}
\end{align}$$

(cite: Paiva:2020:299) have shown that Reaction [\[si_sh\]](#si_sh) is exothermic and barrierless. Reaction [\[si_h2s\]](#si_h2s) is exothermic (cite: Paiva:2020:299), and computational work by (cite: Doddipatla:2021:eabg7003) suggests that substantial SiS can be formed by this pathway as is abundant in this region. Reaction [\[sih_s\]](#sih_s) is also exothermic and barrierless, but can produce Si + SH instead, and the branching ratios are not yet known (cite: Rosi:2018:87). The remaining question is then the source of the reactants.

In SrcI, with the SiS emission tracing the outer edges of the outflow, Si could be readily produced in shocks. Since the SiO outflow co-rotates with the disk close to the disk and then mushrooms out with blended rotation signature, shocks may occur as the outflow imparts angular momentum to ambient material, which creates and can be mapped in SiS. Both SH and are similarly known to be enhanced in shocked regions, being liberated from ice mantles (cite: Neufeld:2012:L6). abundances are enhanced by a factor of 1000 in the Orion hot core and the “plateau" $[H_2S/H_2]$$\sim10^{-6}$ relative to quiescent clouds. (cite: Minh_1990). The large abundance of in the hot core may result from grain mantle evaporation, while the large abundance in the plateau could result from high-temperature gas-phase chemistry and/or grain-surface chemistry (cite: Minh_1990).

The plateau emission comes from the outflow associated with SrcI where shock chemistry may also be responsible for the large abundances of SO, $SO_2$, , and SiO. and $H_2^{34}S$ with $E_u<$ 500 K are seen as blueshifted absorption features at 0.2$''$  resolution indicating that they originate in outflowing gas (cite: Plambeck2016). Detailed shock models (cite: vanGelder_2021) found that SO and $SO_2$ are good tracers of accretion shocks. Desorption of SO and $SO_2$ ices can occur in high-velocity ($>$5 $\rm km~s^{-1}$ ) shocks at high densities ($>10^7$ cm$^{-3}$). They found that the abundances of atomic S and O, and in ices such as $H_2S$, $CH_4$, SO, and $SO_2$ play a key role in the abundances of SO and $SO_2$ that are reached in the shock. Reaction [\[sih_s\]](#sih_s), on the other hand, is harder to justify as important in our case. While (cite: Rosi:2018:87) show that this reaction is exothermic and barrierless, the source of sufficient SiH to produce our observed quantities of SiS is unclear. To date, SiH has only been tentatively identified in space (albeit in Orion-KL) using Caltech Submillimeter Observations (cite: Schilke:2001:281).

Our observed coincidence of SiS with SO suggests another pathway might be viable, $$\begin{equation}
    \ce{SO + SiO -> SiS + O2}. \label{so_sio}
\end{equation}$$

(cite: Campanha:2022:369) studied the reverse reaction, $$\begin{equation}
    \ce{SiS + O2 -> SiO + SO}, \label{sis_o2}
\end{equation}$$ which they showed possesses a substantial activation barrier. While this might suggest the forward reaction is efficient, in fact their potential energy surface (their Fig. 3) indicates that both forward and reverse reactions possess entrance barriers, and that the forward reaction to form SiS is substantially endothermic, but could be driven by shock heating. These endothermic reactions may prove to be important in the brief, high-temperature regime of interstellar shocks (Burkhardt et al. 2019). Extensive modeling work would be needed to determine the extent of the effect on the overall chemistry. Further computational or experimental work exploring other potential pathways between these species is warranted.

One potential reaction that has not been, to our knowledge, well studied is that between SiH and SH: $$\begin{equation}
    \ce{SiH + SH -> SiS + H2}.
\end{equation}$$ There also remain some open questions about the relationship between SiS and , which may be especially relevant given the excited present at the base of the outflow in SrcI. Taken as a whole, and given the spatial overlap of many of these molecules in SrcI, further observations at high-resolution in SrcI particularly targeting SiS, SiO, SiH, SH, , SO, , and are warranted.

##  in the Outflow

The origin of this water line in the gas phase is not clear. The emission extends deeper and likely formed in the disk, but icy grain mantles are unlikely to have survived in the hot disk for $\sim$550 years since the BN/SrcI encounter. Hydrated minerals are another possible source of . The AlO line emission that was mapped in the outflow close to the disk suggests that refractory grain cores and grain mantles are destroyed (cite: Wright2020). Carbon grains are destroyed at $\sim$800 - 1150 K, silicate grains are evaporated at $\sim$1300 K, and AlO at $\sim$1700 K (cite: Lenzuni1995).

This vibrationally excited water line,

is also detected in the Keplerian disc around the O-type protostar G17.64+0.16 (cite: Maud_2019) and in the O-type protobinary system IRAS 16547–4247 (cite: Tanaka2020). The $v_{2}$ = 1 emission with E$_{u}$ = 3464 K is concentrated at the positions of protostars (cite: Tanaka2020) and in several other high mass protostellar objects (cite: Ginsburg2023ApJ).

Near IR observations of toward the massive protostar AFGL 2136 IRS 1 identified 47 ro-vibrational transitions in warm (500 K), dense (n(H${_2}$) $>$5 $\times 10^{9} cm^{-3}$) gas, suggesting an origin close to the central protostar (cite: Indriolo_2013).

On the other hand, [9](#fig:h2o+sis+sio) shows that emission peaks are associated with SiS close to the disk, suggesting that heating by shocks may play a role in the formation and dissociation of , $\sim$50 AU from the SrcI disk, where the rotating SiO column expands abruptly into a turbulent wide angle outflow. These distributions fit into a scenario where the SiO is formed from grain destruction following the dissociation of (cite: Schilke1997). In these models, grain mantles and grain cores are destroyed in shocks; Si is released into the gas phase, and then oxidized by dissociation products of .

(cite: Ginsburg2018) fitted a Keplerian rotation curve to the envelope of a position-velocity along the major axis of the SrcI disk. However, the butterfly-like shape seen in [4](#fig:nacl_mom0+1) suggests that the also has an outflow component.

[9](#fig:h2o+sis+sio) compares the emission with the SiS and SiO at $\sim50\times30$ mas resolution. At velocities -18 to -10 and 22 to 30 $\rm km~s^{-1}$ , the traces the SiO outflow along the minor axis of the disk, while at velocities -8 to 20 $\rm km~s^{-1}$ , the traces the bright emission in the inner part of the SiS outflow.

## Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I

As summarized by (cite: Edgar_2004), the Bondi-Hoyle-Lyttleton (BHL) accretion model describes a possible process of for accretion onto a moving point mass passing through a uniform gas cloud. In essence, the gravity of the mass lenses the medium into a trail in its wake. From this dense, aligned column, the mass can accrete. This model neglects pressure and thermal effects, such as the trapping of thermal energy in the trailing column. Accretion onto the disk from the ambient cloud would be limited to roughly the BHL rate, which for $n_{H_{2}} = 1.6 \times 10^5 \; \text{cm}^{-3}$, $\rho \sim 5 \times 10^{-19} \; \text{g} \; \text{cm}^{-3}$, $M = 15 \; M_\odot$, and $v= 10 \; \text{km} \; \text{s}^{-1}$. relative to the interstellar background is given by

$$\begin{equation}
    \dot{M} = \lambda_* 4 \pi \rho \frac{\left(GM\right)^2}{\left(v^2 + c_s^2\right)^{3/2}} \approx 5 \times 10^{-7} M_\odot \; \text{yr}^{-1}
\end{equation}$$

where $c_s = \sqrt{ k_B T / \mu m_p }$ is the ambient thermal (sound) speed $\sim$ $1\text{-}5 \; \text{km} \; \text{s}^{-1}$ for $T=10\text{-}1000 \; \text{K}$, and $\mu = 2.8$. $\lambda_*$ is a dimensionless constant of order unity (cite: shu1991physics).

The SO line is a possible tracer of this trailing shocked ambient medium around SrcI resulting from the BN/SrcI explosion. (cite: Bally2017) observed the 219.95 GHz SO line with ALMA at 1$''$  resolution. Figure 17 from (cite: Wright2020) shows a 30$''$  region image centered on SrcI. The SO is seen throughout this region with a similar filamentary structure in the SiO and CO emission.

[3](#fig:son344GHz) shows SO emission around SrcI, and the expected proper motion of SrcI in 100 years. Table 1 from (cite: Rodgriguez2017) gives the positions and proper motions of the runaway stars in OMC1. The proper motion vector of SrcI has a PA $=$152 $\pm$ 4$^\circ$. It appears to be misaligned by 9$\pm$4$^\circ$ with the SrcI disk major axis (PA$=-$37 $\pm$ 0.4$^\circ$, as observed at 220-340 GHz) (cite: Wright2020). The SrcI major axis aligns with the BN proper motion (323 $\pm$ 2**$^\circ$**) (cite: Rodgriguez2017), within 2**$^\circ$** . This is expected, as in the BN-SrcI interaction, material in orbit around the stars experienced a torque that align their disks with the stellar proper motion vectors (cite: Bally2020). The small misalignment of the SrcI disk is consistent with the hypothesis that the BN-I interaction shaped the disk rather than subsequent BHL accretion. Misalignment of the SrcI disk with its proper motion may produce the turbulent wake seen in SO emission. It is also possible that this misalignment is the product of source x and the current SrcI binary, or merger remnant, having separated after the initial SrcI disk formation and relaxation.

Since the outer radius of SrcI’s disk is smaller that the gravitational radius, $r_G$ $\sim GM/v_{rot}^2$ $\sim$ 130 AU, it is likely that most of the SrcI disk has had to re-form since the dynamic interaction $\sim$550 years ago from pre-existing circumstellar material. This formation process may be contributing to the current accretion (and outflow). The fall-back and resulting turbulence might contribute to shocks, and enhanced accretion from disk to star.

[10](#fig:so) shows the $215.221$ GHz SO emission with uniform weighting of the u-v data to emphasize the small scale structure with a velocity resolution of $1$ $\rm km~s^{-1}$ .

The SO line shows an envelope of emission around the disk, with a steep gradient at the SE end of the disk, and an extended tail to the NW of the disk. There are also significant emission features at 0.2 to 0.4$''$ to the NE and SW of the disk. The emission surrounding the disk is largely red-shifted, consistent with the 0.2$''$ resolution spectra of SrcI plotted by (cite: Plambeck2016), in which the sulfur-bearing species (CS, , SO, and ) exhibit prominent blue-shifted absorption profiles.

SO and are heavily absorbed across SrcI at velocities of -8 to +4 $\rm km~s^{-1}$ (cite: Wright2020). This blue-shifted absorption is the reason for the domination of red-shifted emission around the disk. Since the velocity width of the absorption is comparable with the halfwidth of the SiO emission lines, it is likely that the absorbing molecules are located in the (cooler) outer layers of the SrcI outflow, rather than in unrelated foreground gas (cite: Plambeck2016).

In [10](#fig:so), the $215.221$ GHz SO$\quad v=0\quad(J=5-4)$ line shows a steep gradient at the SE end of the disk, with an extended tail to the NW of the disk. The SO suggests a bow shock from the motion of SrcI through the medium, with a turbulent wake similar to the simulations in (cite: Moeckel_2009). is heavily present in the region around the disk, and very roughly follows a velocity pattern around the disk. The leading (SE) side of the disk has blue-shifted SO emission, while the leeward side has red-shifted SO emission. This would be expected if SO was wrapping around the disk between the outflow lobes; about half the incoming SO would have a velocity component towards us along our line of sight to the disk, and red-shifted towards the leeward side of SrcI.

Past this region, we see a significant body of SO extending away from the disk that has a small $v_{los}$ component (indicated in green, where 0 $<$ $v_{los}$ $<$ 10 $\rm km~s^{-1}$ ). [11](#fig:SiS+SO.cmn) shows the velocity structure of the trailing plume of 215.22 GHz SO emission to the NW of the disk, using natural weighting of the uv-data to enhance the brightness sensitivity in 1 $\rm km~s^{-1}$ intervals. The RMS noise level is 9 mJy/beam (35 K) in a synthesized beam FWHM 95$\times$76 mas at PA -83$^\circ$.

This region may correspond to the “quasi-static" body mentioned above. Material within a radius $R_A = 2GM/\sqrt(c_s^2+ v^2)$ $\sim$90 au for $M\sim$ 15 $M_{\odot}$, will be accreted on a time scale $R_A/c_s$ $\sim$ 300 yr (cite: Moeckel_2009), where $c_s = \sqrt{ k_B T / \mu m_p }$ is the ambient thermal (sound) speed $\sim$ 1.4 $\rm km~s^{-1}$ for T$\sim$500 K.

In addition, studies have shown using simulations that the radiation pressure exerted by massive protostars does not preclude accretion; mass can be delivered into the star through non-axisymmetric disks and filaments that self-shield against radiation, created by gravitational and Rayleigh-Taylor instabilities while radiation escapes through optically thin bubbles (cite: Krumholz2009). Gravitational instabilities can also lead to the formation of companion stellar objects (cite: Krumholz2009).

Another difficulty of getting material to infall upon massive stars is removing the angular momentum from the accreting material. The accretion disk is a mediating structure for this process, providing a buffer between the surrounding material and the protostar. For further discussion of this topic, see (cite: Pudritz_2019).

The material accretes onto the disk as it loses some angular momentum, and then more angular momentum is removed through processes such as D-winds and X-winds (cite: Shu2000), resulting in material falling onto the protostar from the disk. These steps are time-variable and may not always occur at the same rate relative to one another. X-winds are an alternative mechanism for generating outflows from disks. According to this model, high velocity outflows come from a narrow annulus where the star magnetosphere interacts directly with the inner edge of the disk, at the co-rotation radius (cite: Shu2000). The hot spot observed on the inner edge of the SrcI disk (cite: Ginsburg2018) may result from this mechanism, or alternatively from the proximity of a binary protostar. If SrcI is a binary protostar, it is not clear how the magnetospheres of the two stars interact with each other, and with the disk.

Observations of the scattered near-infrared emission suggest that the near-infrared reflection spectrum observed in the Orion-KL region is produced close to SrcI, and similar to stellar photospheres in the range Teff $\sim$ 3500 to 4500 K (cite: Testi2010). The spectrum excludes SrcI being a massive protostar rotating at breakup speed. (cite: Testi2010) suggest that the absorption spectrum comes a disk surrounding a $\sim$10 $M_{\odot}$ protostar, accreting from its disk at a high rate of a few $\times 10^{-3}$ $M_\odot$/yr.

(cite: Hosokawa2010) studied the evolution of massive protostars with disk accretion. They identified four evolutionary phases, including deuterium burning which may account for a significant fraction of the luminosity of SrcI at some point. However their models show that that a massive protostar bloats to a radius of several hundreds of $R_{\odot}$ with an accretion rate exceeding 10$^{-3}$ $M_\odot$/yr. The large radius leads to a low effective temperature consistent with that observed for SrcI. They also note that the low UV luminosity will inhibit the formation of an H II region until mass accretion onto the star deceases significantly. Assuming a stellar radius of 1 AU with color temperature 4000K, the theoretical luminosity would be,

$$L_{tot} = 4 \pi R^{2} \sigma T^{4} \simeq 1.01 \times 10^{4} L_\odot$$

Comparatively, if we assume an infall rate $5\times10^{-3}$ M$_\odot$ / year onto a central mass of 15 M$_\odot$, the luminosity to be

$$L_{tot} = \frac{G M \dot{M}}{R} \simeq 1.05 \times 10^{4}L_\odot$$

Currently, no direct observations of infall onto SrcI have been made. The expected infall rate ($\dot{M}$) is inferred from the observed outflow to range from 10$^{-5}$ to 10$^{-3}$ $M_\odot$/yr. The rotation-fitting done by (cite: Ginsburg2018) favor a $\sim$15 $M_{\odot}$ protostar with a high accretion rate. To maintain the observed luminosity of $\sim$10$^4$ $L_\odot$, if the accretion onto the circumbinary disk is akin to the Bondi-Hoyle rate ($\sim$10$^{-7}$ $M_\odot$/yr) and accretion from the disk onto the star is $\sim$10$^{-3}$ $M_\odot$/yr, then the disk will be depleted on a timescale of $M_{disk}$/$\dot{M}$. (cite: Plambeck2016) estimated M$_{disk}$ $\sim$ 0.02 to 0.2$M_\odot$, giving a disk depletion time of 200 to 2000 yr for $\dot{M}$$\sim$10$^{-3}$ $M_\odot/yr$.

If a higher rate of accretion onto the circum-binary disk is not occurring, then the protostar will likely deplete the disk and reach the final stage of its pre-main sequence evolution. This is a rather exciting possibility, as it would expect SrcI to become a directly visible stellar object within several centuries. However, the source would still be in the Orion A cloud for a while. To emerge into the Orion Nebula would take tens of thousands of years. If it is currently $\sim$ 0.1 pc behind the ionization front with a radial velocity (v$_r) \sim 4$ $\rm km~s^{-1}$ , this would take $\sim 2.5~10^{4}$ years. Also, if $\dot{M} \sim 10^{-3}$ $M_\odot/yr$, the photosphere will remain on the AU scale, and after the disk is gone, it will take a Kelvin-Helmholtz time-scale to heat up from 4,000 K to $\sim$ 40,000 K for the newborn star to begin ionizing the surroundings.

## Evidence of a Warped Disk in Salt Emission

Salt emission has been detected in nine high-mass YSO disks so far (cite: Ginsburg2019; Maud_2019; Tanaka2020; Ginsburg2023ApJ). In SrcI, salt emission is found close to the dust layer at the surface of SrcI and maps the rotation close to the disk surface (cite: Ginsburg2018; Ginsburg2019).

A comparison of the and NaCl at $\sim50\times30$ mas resolution is shown in [12](#fig:h2o+nacl). The NaCl emission is more closely associated with the continuum disk and extends to greater radii along the disk major axis than the emission. [4](#fig:nacl_mom0+1) shows the moment 1 image–the velocity weighted intensity–of the emission. This shows a simple, linear velocity gradient (implied by the linear color gradient across the disk), which is consistent with an almost edge on thick disk. (cite: Matthews2010) found that the SiO masers suggest an inclination of $\sim$85$\ensuremath{^\circ}$. Additionally, (cite: Ginsburg2018) fitted a Keplerian rotation curve to the envelope of a position-velocity along the major axis of the SrcI disk in good agreement.

Using a linear velocity gradient combined with the observed NaCl moment 0 image, we generated model images in 2 km/s channels for comparison with the data shown in [13](#fig:nacl.cm1-cont+velimage5.resid).

This simple model agrees with the observed NaCl emission in 2 km/s channels between -10 and +20 km/s. The maximum differences between the model and the data occur at the ends of the disk where the model and the data are asymmetrically offset. We used the MIRIAD tool **imdiff** to fit the offset as as a function of velocity. The offsets can be minimized by allowing the position angle of the disk to change with radius. A possible explanation for this disagreement at the velocity and radial extrema is that the NaCl emission resulted from (recently) accreted material having a different angular momentum compared to the original disk which resulted from the BN/SrcI encounter. Accreted material, or the localized outflow resulting from accreted material, could exert a torque. This may produce the warping observed in the 99 GHz continuum emission from the disk (cite: Wright2022) and the NaCl emission at the ends of the disk. Alternatively, misalignment between the rotation axis and the B-field direction could also create a warped disk structure (cite: Machida_2019).

Additionally, the salt lines could be excited by infall of material onto the disk. [14](#fig:naclv=1+v=2) shows a comparison of the 232.51 GHz NaCl $\quad v=1\quad(J=18-17)$ and the 217.98 GHz NaCl$\quad v=2\quad(J=17-16)$ in 2 $\rm km~s^{-1}$ channels. Note that the $v=1$ and $v=2$ emission come from the same regions, and have the same velocity distribution, suggesting a common origin for different transitions. This common origin may be excitation due to shocks created by accretion onto the disk.

[15](#fig:naclv=2+sio) shows a comparison of 217.98 GHz NaCl$\quad v=2\quad(J=17-16)$ and SiO in 2 $\rm km~s^{-1}$ channels. Note that the NaCl emission that comes from the ends of the disk may be a byproduct of an accretion shock of material falling into the disk, while the SiO emerges from a smaller radius in the disk, corresponding to the footprint of a magneto-centrifugal outflow from the disk. Some of the material falling towards the disk at radii within this footprint would be swept out by the outflow.

The symmetry of the NaCl bright spots about the rotation axis may be from the rotation of the disk. If this explanation is correct, then this implies that accretion is followed by orbital redistribution i.e. the salt must stay in the gas phase for the orbital timescale at $\sim$ 30 AU radius for a 15 $M_\odot$ star, $>$40 years.

The vibrationally excited NaCl must be populated on these time scales because of the high Einstein A-values (cite: Ginsburg2019). However, the density and temperature rise within 100 - 1000 yr as the shock goes through the surface layers of the disk (cite: Burkhardt_2019). The 1/e scale height of the disk surface estimated from the 340 GHz continuum is a only a few au (cite: Wright2020), and presents a wide range of temperatures and densities for accreting material. More detailed modeling is needed to see if accretion shocks could populate the observed NaCl levels.

Similar to the NaCl distribution, observations of the $5_0 - 4_0$ (A) methanol line at 241.79143 GHz, ($E_u$ 35K) in the surface layer at the ends of the disk in the Class 0 protostellar object L1157 has been previously reported as evidence for an accretion shock (cite: Velusamy_2002).

(cite: Ginsburg2023ApJ) took a sample of 23 candidate high-mass young stellar objects (HMYSO) in 17 high-mass star-forming regions found five new detections of , NaCl, KCl, PN, and SiS. While these detections had disk-like kinematic structures, SrcI is the only HMYSO that has been confirmed to have these molecules present in its disk. These results indicate that NaCl emission features are likely common in HMYSO disks.

# Summary

1\. We present ALMA observations of SiO, SiS, , NaCl, and SO at $\sim$30 to 50 mas resolution. These images map the molecular outflow and disk of Orion Source I (SrcI) on $\sim$12 to 20 AU scales.

2\. The SiO and emission map a rotating, expanding outflow. The emission is consistent with a magneto-centrifugal outflow from the SrcI disk. The rotational velocity decreases with distance from the disk.

3\. The SiS maps a turbulent boundary layer in the outflow. We argue that the SiS emission is created and destroyed in a shocked region between the outflow and the ambient medium as SrcI moves through it. This process would dissipate the angular momentum held by the rotating molecular outflow into the surrounding medium.

4\. The vibrationally excited water line (E$_{u}$ = 3461.9 K) traces the rotation of the SrcI disk and also traces the SiO outflow and SiS emission close to the disk, suggesting that shocks may play a role in the emission. The origin of the vibrationally excited water line in the gas phase is not clear. The emission extends deeper and likely formed in the disk, but icy grain mantles could not persist in the hot disk. Hydrated minerals are a possible source of in the hot disk.

5\. The NaCl emission closely traces the disk. The emission follows a linear velocity gradient along the disk major axis. At both ends of the disk, the position angle of the NaCl emission is consistent with a twist, or warp. Bright hot spots in NaCl emission may be excited by accretion shocks from material falling onto the disk. The motion of SrcI forces the external material to pass between the disk and the outflow, which may result in some material accreting onto the disk, creating shocks which excite the NaCl emission close to the disk surface.

6\. SO traces a bow-shock at the leading edge of the SrcI disk and a turbulent plume of material extending from the trailing edge of the disk. This trailing material may accrete onto the disk. These features are created by the movement of SrcI through the medium and Bondi-Hoyle-Lyttleton accretion.

7\. If the accretion onto the circum-binary disk is the Bondi-Hoyle-Lyttleton rate $\sim$10$^{-7}$ $M_\odot$/yr and accretion from the disk onto the star is $\sim$10$^{-3}$ $M_\odot$/yr to maintain the observed luminosity of $\sim$10$^4$ $L_\odot$, then the disk is being depleted on a timescale

time of 200 to 2000 yr.

8\. These data suggest that the BN - SrcI interaction, and the proper motion of SrcI may have a significant effect on the structure and evolution of SrcI and its molecular outflow.

# Facilities

ALMA, VLA

# Software

Miriad (cite: Sault1995)

# Acknowledgements

We thank the referee for a careful review and detailed suggestions to improve this paper.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: 2017.1.00497.S, 2016.1.00165.S, 2016.1.00165.S . ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. T.H. is financially supported by the MEXT/JSPS KAKENHI grant Nos. 17K05398, 18H05222, and 20H05845

|       |                |            |       |                       |            |
|:-----:|:--------------:|:----------:|:-----:|:---------------------:|:----------:|
| freq  |  project code  |    date    | time  |      synth beam       |  baseline  |
| (GHz) |                |            | (min) |     (milliarcsec)     |  (meters)  |
|  99   | 2017.1.00497.S | 2017-10-12 |  158  | 45$\times$36 at PA 47 | 40 - 16200 |
|  224  | 2016.1.00165.S | 2017-09-19 |  44   | 39$\times$19 at PA 66 | 40 - 10500 |
|  340  | 2016.1.00165.S | 2017-11-08 |  45   | 26$\times$11 at PA 58 | 90 - 12900 |

: Observations

 

CCCC Molecule & Transition & Frequency & Upper Energy\
& & (GHz) & (K)\
\^28SiO & v = 0, J = 5 - 4 & 217.105 & 14.5\
\^29SiO & v = 0, J = 5 - 4 & 214.385 & 30.9\
SiS & v = 0, J = 12 - 11 & 217.818 & 68.0\
H\_2O & 5( 5, 0), v\_2=1 - 6( 4, 3), v\_2=1 & 232.687 & 3461.9\
NaCl & v = 1, J = 18 - 17 & 232.510 & 625.7\
NaCl & v = 2, J = 17 - 16 & 217.980 & 1128.4\
SO & \^3v = 0, J = 5 - 4 & 215.221 & 44.1\
SO & \^3v = 0, J = 8 - 7 & 344.311 & 87.5

![image](figures/sio_mom0+1.pdf) ![image](29sio_mom0+1.pdf)

![](sis_mom0+1.pdf)

![](B7_memcm01+SO_344.31.cmn.mom0.pdf)

![image](h2o_mom0+1.pdf) ![image](figures/nacl_mom0+1.pdf)

![](sio+sis.pdf)

![image](29sio.pdf) ![image](sis.pdf)

![](29sio.4pv.pdf)

![](sis.4pv.pdf)

![](h2o+sis+sio.pdf)

![](B7_memcm01+SO_215.22.cm.mom0.pdf)

![](SiS_217.82+SO_215.22.cmn.pdf)

![](h2o+nacl.pdf)

![](nacl.cm1-cont+velimage5.resid.pdf)

![](naclv=1+v=2.pdf)

![](naclv=2+sio.pdf)

</paper>

Write the methods card for this paper.