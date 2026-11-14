# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...692A.151S\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...692A.151S",
 "title": "Uncovering the structure and kinematics of the ionized core of M 2-9 with ALMA",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Sánchez Contreras, C.",
 "n_authors": 6,
 "arxiv_id": "2411.03825",
 "doi": "10.1051/0004-6361/202451669",
 "alma_projects_linked_by_archive": [
  "2016.1.00161.S",
  "2017.1.00376.S"
 ]
}
```

Paper text:
<paper>
# Uncovering the structure and kinematics of the ionized core of M 2-9 with ALMA

# Introduction

The onset of asphericity and polar acceleration in Planetary Nebulae (PNe) is still not fully understood, but these phenomena are already active in the early stages of evolution beyond the Asymptotic Giant Branch (AGB). To comprehend the complex and rapid ($\approx$1000 yr) evolution of nebulae from the AGB to the PN phase, it is then crucial to study pre-PNe (pPNe) and young PNe (yPNe). Previous studies of pPNe suggest that the presence of multiple lobes and high velocities may be attributed to the impact of collimated fast winds (CFWs or jets) on the slowly expanding circumstellar envelopes formed during the AGB phase (cite: bal02). However, direct characterization of the post-AGB jets and their launch regions, within a few hundred astronomical units, is challenging due to their small angular sizes and significant obscuration caused by optically thick circumstellar dust shells or disks.

During the mid-stages of their post-AGB evolution towards the PN phase, the central stars of pPNe begin to ionize their surroundings, typically reaching a B-type spectral classification. The just emerging (nascent) central ionized cores of pPNe/yPNe can be traced using radio continuum and recombination line emissions, offering the advantage of minimal dust extinction effects. A recent pilot study of millimeter radio recombination lines (mRRLs) in a sample of pPNe/yPNe with the IRAM-30 m radiotelescope (cite: san17) shows that mRRLs are optimal tracers to probe the deepest regions at the heart ($\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$150 au) of these objects, from where CFWs

are launched. One key finding from the study by CSC17 is the determination of mass-loss rates for young ($\sim$15–30 yr old) post-AGB ejections ($\dot{M}_{\rm pAGB}$$\sim$10$^{-6}$–$10^{-7}$ $M_{\odot}$ yr$^{-1}$) much higher than those currently used in stellar evolution models (cite: sch83; blo95; vas93; mil16).

These large rates imply a much faster transition from the AGB phase to the PN phase, particularly for low-mass ($\sim$1 $M_{\odot}$) progenitors. Subsequent mRRL studies conducted with the Atacama Large Millimeter Array (ALMA), achieving a remarkable angular resolution down to $\sim$0$.\!\!^{\prime\prime}$02, have also led to the first discovery of a rotating fast ($\sim$100 km s$^{-1}$) bipolar wind and disk system at the core of MWC 922, a B\[e\]-type post main-sequence star with a distinctive X-shaped nebula (cite: san19). This finding highlights the significance of mRRL observations in uncovering such intriguing systems.

In this work, we present an ALMA-based study of the nascent compact ionized region at the center of the pPN/yPN candidate M 2-9. We studied its inner regions down to 0$.\!\!^{\prime\prime}$03 ($\sim$20 au) scales using 1 and 3 mm observations of the continuum and the H30$\alpha$ and H39$\alpha$ mRRLs using the ALMA interferometer. This paper is organized as follows. In Sect. [2](#m29), we provide an introductory overview of M 2-9, and in Sect. [3](#obs) we describe the observations. In Sect. [4](#res_cont) and Sect. [5](#res-lines), the observational results from the continuum and from the lines, respectively, are reported. The analysis of the data, which includes line and continuum non-LTE radiative transfer modeling, is presented in Sect. [6](#analysis). The results are further examined and discussed in Section [7](#discussion), and a summary of our main findings and conclusions is provided in Section [8](#summary).

# M 2-9

M2-9, also known as “The Butterfly” or the “Twin Jet” Nebula, is one of the most iconic and well-studied pPN/yPNe candidates. At optical wavelengths (Fig. [10](#f-hstcont)), it displays a distinctive morphology with a bright compact core and nested bilobed structures that extend over large ($\sim$1$'$) angular scales in a north-south orientation (cite: sch97; cly15).

The nebula’s brightness and morphology have been dynamically changing on timescales of a few years (cite: all72; vdB74; koh80; doy00). The progressive east-to-west displacement of the primary emission features ($knots$) within the inner lobes represents an intriguing feature not observed in other pPNe/yPNe. This phenomenon lacks a comprehensive explanation but has been linked with potential causes such as a rapidly rotating (radiation and/or particle) beam exciting the inner cavity walls of M 2-9’s lobes (cite: doy00; cor11). The rotating pattern of the knots is considered indirect evidence for the presence of a central binary system with an orbital period of $\sim$90 yr.

The lobes of M 2-9, like many other pPNe/yPNe, display expansive kinematics, with velocities ranging from $\approx$20 km s$^{-1}$ in the inner regions of the lobes to $\approx$160 km s$^{-1}$ at their tips (cite: sch97; sol00; tor10; cly15). In the central core, broad H$\alpha$ emission with wings spanning $\sim$1600 km s$^{-1}$ is observed. However, the exact nature of these broad wings and, thus the gas kinematics at the nucleus, remain uncertain, as the H$\alpha$ wings are significantly broadened by Raman scattering (cite: tor10; arr03; lee01).

Recent hydrodynamic modeling by (cite: bal18) indicates that a low-density and mildly collimated jet with gas travelling at $\sim$200 km s$^{-1}$ from the core and impacting on a pre-existing envelope/wind can account for certain complex characteristics and kinematics within M2–9’s lobes, with higher jet velocities being unlikely.

The central star of

M 2-9 is estimated to be a B1 or late O-type with a temperature of $\sim$25-35 kK (cite: cal78; swi79). The presence of significant extinction and high-infrared excess in the direction of the nucleus of M 2-9 indicates the presence of a dusty torus that obstructs direct visibility of the central star and its putative companion.

However, this torus allows the central source’s radiation to illuminate the lobes of the nebula. The binarity of the nucleus has been indirectly confirmed through interferometric CO mm-wavelength emission maps, revealing two off-centered rings aligned with the equatorial plane of the nebula (cite: cc12; cc17). The rings are interpreted as the result of two short mass ejections occurring at different positions in the binary orbit, inclined by $i$$\sim$17$^\circ$ with respect to the line of sight. These mass ejections, which happened about $\sim$1400 yr and $\sim$900 yr ago, also resulted in the formation of two symmetric hourglass-shaped expanding structures that are observed to emerge from the CO rings and overlap with the base of the large-scale optical lobes (cite: cc17).

M 2-9 exhibits thermal radio-continuum emission, and previous studies have identified two components required to adequately fit the mm- and cm-wavelength data (cite: kwo85; lim00; lim03; dlF22). The first component is a compact ionized wind at the center, generating free-free emission following a power-law relationship with frequency S$_{\nu}$ $\propto$ $\nu$ $^{\sim [0.6-0.85]}$. The second component consists of high-density ionized condensations located in the extended lobes, contributing to a nearly flat continuum emission distribution. At mm-wavelengths, the contribution of the extended lobes to the observed continuum is minimal, and the dominant sources are the free-free emission from the compact ionized core and thermal emission from dust (cite: san98). In their study, CSC17 reported the detection of mm-wavelength emission from the H30$\alpha$ and H39$\alpha$ lines,

consistent with an ionized core-wind that has been ejected over the past $<$15 yr at an average rate of $\sim$3.5$\times 10^{\rm -7}$ $M_{\odot}$ yr$^{-1}$ and with a mean expansion velocity of $V_{\rm exp}$$\sim$22 km s$^{-1}$.

In a recent study by (cite: dlF22) using multi-epoch $\sim$23-43 GHz continuum maps, it was observed that the elongated ionized core-wind of M 2-9 exhibits a subtle C-shaped curvature, whose orientation is found to vary over time.

The distance to M 2-9 is highly uncertain, with values ranging from 50 pc to 3 kpc in the literature (cite: san17). In this study, we adopt a distance of 650 pc for M 2-9, which is based on the analysis of the proper motions of the optical knots by (cite: sch97) and of the spatio-kinematics, including also tentative proper motions, of the molecular rings (cite: cc12). This distance choice allows for a direct comparison with the study conducted by CSC17 on the nascent ionized core of M 2-9.

# Observations and data reduction

+--------:+:---------:+:---------:+:--------------------------+:----------:+
| Center  | Bandwidth | $\Delta$v | Line                      | Continuum  |
+---------+-----------+-----------+---------------------------+------------+
| (GHz)   | (MHz)     | (km/s)    |                           | Flux (mJy) |
+---------+-----------+-----------+---------------------------+------------+
| *Band 3. DATE: 2017-10-15*                                               |
+---------+-----------+-----------+---------------------------+------------+
| 95.350  | 5900      | 3         |                           | 105        |
+---------+-----------+-----------+---------------------------+------------+
| 97.000  | 5801      | 3         |                           | 106        |
+---------+-----------+-----------+---------------------------+------------+
| 106.737 | 659       | 0.3       | H39$\alpha$               | 124        |
+---------+-----------+-----------+---------------------------+------------+
| 107.100 | 657       | 2.7       |                           | 120        |
+---------+-----------+-----------+---------------------------+------------+
| 109.000 | 1290      | 2.7       |                           | 120        |
+---------+-----------+-----------+---------------------------+------------+
| 109.536 | 642       | 0.7       | H55$\gamma$               | 123        |
+---------+-----------+-----------+---------------------------+------------+
| 110.201 | 638       | 0.7       | $^{13}$CO 1-0)            | 122        |
+---------+-----------+-----------+---------------------------+------------+
| *Band 6. DATE: 2017-11-12*                                               |
+---------+-----------+-----------+---------------------------+------------+
| 215.400 | 2612      | 1.5       |                           | 227        |
+---------+-----------+-----------+---------------------------+------------+
| 217.500 | 2587      | 1.4       |                           | 232        |
+---------+-----------+-----------+---------------------------+------------+
| 230.538 | 610       | 0.6       | $^{12}$CO 2-1             | 242        |
+---------+-----------+-----------+---------------------------+------------+
| 231.901 | 607       | 0.6       | H30$\alpha$ +He30$\alpha$ | 245        |
+---------+-----------+-----------+---------------------------+------------+
| 232.900 | 2416      | 1.3       | He30$\alpha$              | 243        |
+---------+-----------+-----------+---------------------------+------------+

: Central frequency, bandwidth, velocity resolution, detected spectral lines and continuum fluxes in the different spectral windows (SPWs).

Table notes: Flux calibration uncertainties are $\sim$10%.

The observations of M 2-9 were conducted using the ALMA 12-m array as part of projects 2016.1.00161.S and 2017.1.00376.S. The observations were carried out in Band 3 (3 mm) and Band 6 (1 mm), with a total of twelve different spectral windows (SPWs) dedicated to mapping the emission of various mRRLs (and CO lines) as well as the continuum (Table [1](#tab:spws)). The Band 3 and Band 6 observations were conducted separately in two different execution blocks, with a duration of approximately 1.5 and 1.1 hr, in October and November 2017, respectively.

The observations utilized 45-50 antennas, with baselines ranging from 41.4 m to 16.2 km for Band 3, and from 113.0 m to 13.9 km for Band 6. The maximum recoverable scale (MRS) of the observations is $\sim$0$.\!\!^{\prime\prime}$8 and $\sim$0$.\!\!^{\prime\prime}$7 at 3 and 1 mm, respectively.

The total time spent on the science target, M 2-9, was about 49 min in Band 3 and 33 min in Band 6. A number of sources (J 1751+0939, J 1658$-$0739, J 1718-1120, and J 1733$-$1304) were also observed as bandpass, complex gain, pointing, and flux calibrators. The flux density adopted for J 1751+0939 is 1.95 Jy at 108.970 GHz with a spectral index $-$0.294, and and 1.38 Jy at 231.845 GHz with the same spectral index.

An initial calibration of the data was performed using the automated ALMA pipeline of the Common Astronomy Software Applications (CASA[^1], versions 4.7.2 and 5.1.1). Calibrated data were used to identify the line-free channels, allowing for the creation of initial images of both the lines and continuum in the various SPWs. Strong continuum emission was detected in all SPWs, with the noise being dominated by secondary lobes triggered by residual calibration errors.

Given the high signal-to-noise ratio (S/N$\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$200) achieved in the continuum images and the absence of significant/complex large-scale structure in M 2-9 in our observations (see Sect. [4](#res_cont)), we self-calibrated our data using the initial model of the source derived from the standard calibration to improve the sensitivity and fidelity of the images.

Self-calibration as well as image restoration and deconvolution was done using the GILDAS[^2] software MAPPING.

Continuum images were generated for each of the 12 SPWs by utilizing line-free channels. Flux measurements of the continuum emission for each SPW were obtained integrating the surface brightness within a circular aperture with a radius of 0$.\!\!^{\prime\prime}$25 fully enclosing the continuum source (Table [1](#tab:spws)). The absolute calibration uncertainties, estimated at around 10%, were determined by comparing the measured continuum flux at different frequencies for the phase, check, and flux calibrators (before and after self-calibration) with the values adopted by the ALMA calibration pipeline.

Line emission cubes were constructed by subtracting the corresponding continuum data from each SPW, specifically subtracting the continuum of the SPW containing the specific line of interest. The final self-calibrated line cubes and continuum images presented here were created using the Hogbom deconvolution method with a robust weighting scheme[^3] resulting in angular resolutions of $\sim$40$\times$30 mas at 1 mm and $\sim$90$\times$60 mas at 3 mm. Continuum maps with a circular restoring beam of half power beam width (HPBW) of 40 mas at 1 mm and 3 mm were also created to facilitate a better comparison between the two images. The typical rms noise level per channel of our spectral cubes is $\sigma$$\sim$1 mJy beam$^{-1}$ (1 mm) and 0.80 mJy beam$^{-1}$ (3 mm) at 3 km s$^{-1}$ resolution. The rms noise level range in the continuum maps is $\sim$25-85 $\mu$Jy beam$^{-1}$ and $\sim$60-100 $\mu$Jy beam$^{-1}$ for the individual SPWs within Band 3 and Band 6, respectively.

# Continuum emission

## Surface brightness distribution

![image](M2-9_spw2_contNav475-selfcal-NICE.pdf) ![image](M2-9_spw37_cont_sc_rob0p5-NICE.pdf) ![image](M2-9_spw2_cont_sc_beam0p04-NICE.pdf) ![image](M2-9_spw37_cont_sc_beam0p04-NICE.pdf)

ALMA continuum emission maps of M 2-9 at two representative frequencies at 1  and 3 mm are shown in Figs. [1](#f-cont) and [10](#f-hstcont). There are no appreciable differences between the continuum maps for the different SPWs within the same band (band 3 or 6), therefore as representative we have chosen those SPWs with larger bandwidth (BW=1.875GHz) at the higher and lower ends of the observed frequency range.

The peak surface brightness of the 3 mm continuum is located at coordinates R.A.=17$^{\rm h}$05$^{\rm m}$37.9668s and Dec.=$-$10$^\circ$08$'$32$.\!\!^{\prime\prime}$65 (J2000)[^4]. These coordinates serve as the reference point ($\delta$x=0$''$, $\delta$y=0$''$) for positional offsets in all figures representing image data throughout the paper.

The mm-continuum emission, which is spatially resolved, appears elongated along the north-south direction, i.e.  along the symmetry axis of the nebula, with full ($\sim$3$\sigma$ level) dimensions of $\sim$0$.\!\!^{\prime\prime}$22$\times$0$.\!\!^{\prime\prime}$13 and $\sim$0$.\!\!^{\prime\prime}$4$\times$0$.\!\!^{\prime\prime}$13 at 1 and 3 mm, respectively. The elongated shape of the mm-continuum surface brightness is similar to what is observed at cm wavelengths, although the mm-continuum emission is more compact (cite: kwo85; lim03). This compactness is expected based on the inverse relationship between the angular size of the continuum emission along the nebula axis and the observing frequency observed before in M 2-9 at cm wavelengths (cite: dlF22), which reflects the inverse proportionality between the free-free continuum opacity and the frequency (cite: pana75).

The elongated morphology of the mm-continuum emission in M 2-9 exhibits a slight bending towards the northwest (NW) and southwest (SW) directions, revealing a subtle C-shaped (mirror symmetric) curvature. This curvature is most clearly appreciated at 3 mm. The orientation of the C-shaped curvature in our maps is the same as in the JVLA maps of the 7 mm-continuum emission last observed in 2006 (cite: dlF22).

We observed some differences in the brightness surface of the continuum emission at 1 mm and 3 mm, which are worth highlighting. For example, the major-to-minor axis ratio is larger at 3 mm. While the length of the emission along the nebula’s axis is nearly twice as long at 3 mm compared to 1 mm, the average size of the emission in the equatorial direction (perpendicular to the nebula’s axis) is larger in the 1 mm continuum maps, which shows a slight widening in the central equatorial region compared to higher latitudes, i.e. a broad-waisted morphology (indicated by the incomplete yellow ellipse in Fig. [1](#f-cont)). The broad-waist is centered around the 1 mm-continuum emission peak (at offset $\sim$0$.\!\!^{\prime\prime}$007) and is not perfectly aligned with the equatorial plane of the large-scale nebula. The central and brightest regions of the 1 mm continuum map exhibit a higher degree of asymmetry with respect to the equator compared to the 3 mm map. At 1 mm, these regions appear to have an egg-shaped morphology, with the emission from the northern part being weaker than that from the southern part. Furthermore, the emission peak at 1 mm is slightly shifted to the south-east compared to the 3 mm peak.

These small but noticeable differences between the 1 and 3 mm continuum maps (including those restored with the same beam) are likely due, in part, to the presence of dust in these central regions, with a larger contribution to the mm-continuum emission at shorter wavelengths. The presence of a broad-waisted morphology in the 1 mm continuum emission suggests the possibility of a dust distribution in the form of an equatorial disk or belt surrounding the central ionized region. This interpretation is supported by independent indications in the CO emission maps that point towards the existence of such an equatorial structure (Sect. [5.2](#res-co) and Sect. [6.2](#disk_co)). Given the system’s inclination (with the northern lobe moving away from us), this dust structure likely obscures part of the northern ionized region, explaining its weaker 1 mm emission. Furthermore, the broad-waist feature observed in the 1 mm-continuum maps does not appear in the integrated intensity maps of the H30$\alpha$ and H39$\alpha$ lines (see Sect. [5.1](#res-mrrls)), which exclusively trace the free-free (not the dust) emission.

As further discussed in the next subsection, the broad-waist could represent the outer, cooler regions of the compact warm disk observed in the middy at the core of M 2-9 (cite: smg05; lyk11).

## Spectral energy distribution: free-free and dust continuum emission

![image](sed_alma_ff_SELFCAL_FREQ.pdf) ![image](sedm2_9_WARM600K_alpha0p30.pdf)

The overall fit to the continuum fluxes (Table [1](#tab:spws)) derived from 1 mm to 3 mm as a function of frequency yields $S_\nu$ $\propto$ $\nu^{0.92\pm 0.1}$ (Fig. [2](#sed-alma)-left), consistent with predominantly free-free emission from the compact ionized wind/core of M 2-9 with a secondary contribution from dust thermal emission, as discussed in Sect. [2](#m29).

The spectral energy distribution (SED) of M 2-9 from the near infrared (NIR) to the radio domain, including our ALMA continuum flux measurements, is shown in Fig. [2](#sed-alma) (right). Comparing the ALMA fluxes with the majority of the mm-continuum fluxes obtained with single-dish telescopes reveals flux losses of approximately 20% in our high-resolution interferometric measurements. This finding indicates that ALMA, in the extended configuration used in this work (with MRS$\sim$0$.\!\!^{\prime\prime}$7-0$.\!\!^{\prime\prime}$8, Sect. [3](#obs)), is filtering and losing the contributions from both the free-free emission originating from the extended ionized lobes, which results in a nearly flat continuum flux of $\sim$30 mJy (cite: kwo85), and the dust emission from extended structures.

These extended structures include the relatively cool dust present in the large-scale bipolar lobes (cite: san98; smg05) as well as the dust in the inner $\sim$1-2$''$-sized (in radius) equatorial disk (cite: cc17) and whose temperature remains unconstrained.

Besides the extended dust structures, the mid-IR images of M 2-9 reported by (cite: smg05) revealed the presence of an unresolved central core, suggesting the existence of a compact dust component at the center. A fitting of the mid-IR photometry of this unresolved central core (red solid line in Fig. [2](#sed-alma)-right) indicates an approximate temperature of $\sim$260 K. This finding was further supported by (cite: lyk11), who used mid-IR interferometry to confirm the presence of a compact disk with approximate dimensions of 37$\times$46 mas at 13$\mu$m. Unlike the emission from the extended dust structures mentioned in the previous paragraph, the emission from this compact disk is not expected to be affected by interferometric flux losses in our ALMA maps. Therefore, it is likely that the compact warm disk, which exhibits its peak emission in the mid-IR, is contributing to the total observed mm-continuum flux. Moreover, it is plausible that this compact disk corresponds to the inner, warmer regions of the broad-waisted structure detected in our 1 mm-continuum maps, as supported by the fact that the dimensions of the broad-waist are comparable to (although slightly larger than) the size of the disk observed in the mid-IR (Fig. [1](#f-cont)).

Under the assumption that a fraction of the mm-continuum flux observed with ALMA originates from the warm ($\sim$260 K) compact disk we can achieve a good fit of the mm-continuum with a combination of a $\sim$200-300 K dust contribution (with emissivity ranging from $\sim$0.2-0.5) and a free-free component that varies as $S_\nu$ $\propto$ $\nu^{0.89}$ (Fig. [2](#sed-alma)). The latter component accurately reproduces both the cm-wavelength continuum (exclusively from the ionized wind/core as reported by (cite: dlF22)[^5]) and the residual mm-wavelength continuum obtained by subtracting the $\sim$260 K dust emission from the total mm-continuum flux observed with ALMA.

It is important to emphasise that the decomposition/fit described above is subject to uncertainties and should be considered as a rough estimate, its main purpose being to provide an approximate value for the purely free-free continuum flux at mm-wavelength to be compared with the predictions from the model of the central ionized region presented in Section [6.1](#model).

# Line emission

We observed several mRRLs (including, H30$\alpha$, He30$\alpha$, H39$\alpha$, and H55$\gamma$) in M 2-9 using ALMA. The He30$\alpha$ and H55$\gamma$ lines are first detections, while H30$\alpha$ and H39$\alpha$ single-dish spectra were previously reported by (cite: san17). Despite the high sensitivity of our ALMA data, the weak H51$\epsilon$ and H63$\delta$ lines were undetected. We have also mapped two rotational transitions of carbon monoxide ($^{12}$CO 2–1 and $^{13}$CO 1–0). While the $^{12}$CO 2–1 emission has previously been mapped with NOEMA at a resolution of 0$.\!\!^{\prime\prime}$8$\times$0$.\!\!^{\prime\prime}$4 (cite: cc12), there are no known reports of $^{13}$CO 1–0 line maps.

## Millimeter recombination lines

![image](H30a_nchan55_dv3kms-selfcal-spectre.pdf) ![image](H30a_nchan55_dv3kms-selfcal-area-8-52-NICE.pdf) ![image](H30a_nchan55_dv3kms-selfcal-mask-VELO.pdf)\
![image](H39a_nchan55_dv3kms-selfcal-spectre.pdf) ![image](H39a_nchan55_dv3kms-selfcal-area-8-52-NICE.pdf) ![image](H39a_nchan55_dv3kms-selfcal-mask-VELO.pdf)

![image](H30a_nchan55_dv3kms-selfcal-vyx.pdf) ![image](H39a_nchan55_dv3kms-selfcal-vyx.pdf)\
![image](H30a_nchan55_dv3kms-selfcal-vxy.pdf) ![image](H39a_nchan55_dv3kms-selfcal-vxy.pdf)

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Line | Freq. | $\int{I_{\rm L}d\upsilonup}$ | $V_{\rm LSR}$ | FWHM | $I_{\rm L}$  |
|  | (GHz) | (Jy km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (mJy) |
| H30$\alpha$ | 231.900 | 13.3$\pm$0.3 | 73.0$\pm$0.4 | 44.9$\pm$0.9 | 280$\pm$5 |
| H39$\alpha$ | 106.737 | 2.07$\pm$0.08 | 75.1$\pm$0.7 | 54.0$\pm$1.7 | 36$\pm$1 |
| H55$\gamma$ | 109.536 | 0.17$\pm$0.05 | 78$\pm$4 | 50$\pm$10 | 3.3$\pm$0.6 |
| He30$\alpha$ | 231.995 | 0.96$\pm$0.07 | 71.5$\pm$1.0 | 44$\pm$3 | 20$\pm$1 |
| H51$\epsilon$  | 215.663 |  |  |  | $<$12$^{a}$ |
| H63$\delta$  | 95.964 |  |  |  | $<$1.2$^{a}$ |

: Line parameters from Gaussian fitting to the source-integrated profiles of the mRRLs in this study.

Table notes:\

The observational results from our ALMA data of the H30$\alpha$ and H39$\alpha$ transitions, which are main targets of this study, are summarized in Figs. [3](#f-h30yh39) and [4](#f-pv). The complete velocity-channel maps of these transitions are reported in Figs. [11](#f-cubeH30a) and [12](#f-cubeH39a).

Additionally, we summarize our results for the He30$\alpha$ and H55$\gamma$ transitions in Figures [13](#f-he30a) and [14](#f-h55g). The line parameters derived from the source-integrated line profiles of the mRRLs detected are reported in Table [2](#t-parms).

*Morphology and dimensions of the mRRL-emitting region.* Consistent with expectations, the H30$\alpha$ and H39$\alpha$ emission originate from a compact region that shares similar shape and dimensions with the continuum emitting area at 1 and 3 mm, respectively. The integrated intensity maps of the H30$\alpha$ line do not exhibit any emission corresponding to the broad-waist component that is observed in the 1 mm-continuum maps at a similar frequency and angular resolution (Fig. [1](#f-cont)). Since H30$\alpha$ exclusively traces free-free emission, the lack of detection of the broad-waist component in the H30$\alpha$ line supports our earlier conclusion that this component is primarily associated with dust emission in the equatorial region.

After deconvolution with the beam, the H30$\alpha$ line emission in our ALMA maps (at a 3$\sigma$ level) extends along the axis to a radial distance of $\sim$0$.\!\!^{\prime\prime}$07 ($\sim$45au at $d$=650pc) from the center. In the perpendicular direction, it extends to $\sim$0$.\!\!^{\prime\prime}$045 ($\sim$30 au). As expected, the optically thicker H39$\alpha$ line, extends up to slightly larger radial distances of $\sim$0$.\!\!^{\prime\prime}$11 ($\sim$70 au) and $\sim$0$.\!\!^{\prime\prime}$063 ($\sim$40 au) along the axis and equator, respectively (after beam deconvolution and at a 3$\sigma$ level). The major-to-minor axis ratio is larger for the H39$\alpha$ line ($\sim$1.75) compared to H30$\alpha$ ($\sim$1.5). This is well aligned with a previously reported size-to-frequency dependency that differs along the axis and along the equator (cite: lim03).

*Kinematics.* For both the H30$\alpha$ and H39$\alpha$ transitions, we observe a clear velocity gradient along the axis of the nebula. The emission shows a redshift in the North (receding) lobe and a blueshift in the South (approaching) lobe indicating a global expansion along the axis.

The position-velocity (PV) diagrams shown in Fig. [4](#f-pv) offer additional insights into the velocity structure of the ionized bipolar wind in M 2-9. The H30$\alpha$ emission exhibits a distinct S-shape pattern in the axial PV diagram, indicating an abrupt increase of the range of the line-of-sight velocities

in two diametrically opposed, compact regions located at offsets $\delta$y$\sim$$\pm$0$.\!\!^{\prime\prime}$02 along the axis. While the S-shape is less pronounced in the H39$\alpha$ transition, a similar behaviour is observed.

As shown in Sect. [6.1](#model), our model-based analysis of the mRRL emission maps suggests velocities of $\sim$70-90 km s$^{-1}$ in these regions, which are well described by high-density, high-velocity shell-like structures. We refer to these compact regions as the high-velocity spots/shells (HVSs).

The average velocity gradient observed in the inner regions of the ionized wind is $\nabla \upsilon$$\sim$1150km s$^{-1}$ arcsec$^{-1}$$\sim$1.8 km s$^{-1}$ au$^{-1}$, which results in extremely short kinematical ages of less than one year (after deprojection considering $i$$\sim$17$^\circ$, Sect. [2](#m29)).

This implies that observable changes in the profile of the mRRLs can occur in less than a year if there are variations on a similar timescale in the mass-loss rate, structure, or kinematics of the ionized wind.

The PV diagrams along the equator of both H30$\alpha$ and H39$\alpha$ reveal the presence of a subtle velocity gradient perpendicular to the lobes. Specifically, the east side of the equator ($\delta$x$>$0$''$) exhibits blue-shifted velocities, while the west side ($\delta$x$<$0$''$) shows red-shifted velocities. This is most evident in the velocity (first moment) maps of the lines, where the isovelocity contours are inclined rather than running parallel to the equatorial direction (Fig. [3](#f-h30yh39)). This behaviour suggests rotation (counterclockwise) of the ionized bipolar wind.

*Line profiles.* Both the H30$\alpha$ and H39$\alpha$ transitions show a nearly Gaussian source-integrated profile. The H30$\alpha$ line has a peak of emission at $V_{\rm LSR}$=73$\pm$0.4 km s$^{-1}$ and full width at half maximum of FWHM$\sim$44.8$\pm$0.9 km s$^{-1}$. The weaker H39$\alpha$ transition is centered at a slightly larger velocity $V_{\rm LSR}$=75.1$\pm$0.7 km s$^{-1}$ and is somewhat broader, with a FWHM$\sim$54.0$\pm$1.7 km s$^{-1}$. For both transitions, weak emission wings are observed with FWZI$\sim$130 km s$^{-1}$.

The comparison of the source-integrated line profiles as observed with ALMA and with the IRAM-30 m single-dish reveals apparent differences (Figs. [3](#f-h30yh39)). The most significant changes are observed in the H30$\alpha$ line, which exhibits a notable increase in brightness (by a factor of $\sim$2.2 in line flux and $\sim$1.6 in line peak intensity) and broadening of the profile, with the FWHM increasing by $\sim$11 km s$^{-1}$. For H39$\alpha$, we do not confirm an increase in brightness, but the line profile is broader by $\sim$14 km s$^{-1}$ in FWHM. In both transitions, the presence of broad wings in the ALMA observations that were not detected in the previous IRAM-30 m data suggests that these extended features have recently emerged or become more prominent. These differences are unlikely due to mispointing or flux calibration uncertainties (cite: san17), as these factors do not account for the observed variation in profile width.

The observed temporal variations of the mRRL profiles indicate changes in the gas dynamics or physical conditions of the central ionized wind of M 2-9 occurring over short timescales of $\sim$2 yr or less. This is not surprising given the short kinematic age estimated for the inner regions of the mRRL-emitting regions. Changes in the profiles of mRRLs on short ($\sim$2-25 year-long) timescales have been reported in the pPNe CRL 618 (cite: san17) and the post-supergiant candidate MWC 922 (cite: san19).

## CO lines

![image](CO_uvextract-selfcal-area-12-22-nice.pdf) ![image](CO_uvextract-selfcal-COabs-spectre.pdf)

While our study primarily focuses on mRRLs, we simultaneously mapped with ALMA the $^{12}$CO 2–1 and $^{13}$CO 1–0 lines (Table [1](#tab:spws)). As discussed in Sect. [1](#intro), CO (sub)mm-wavelength emission traces two off-centered, expanding equatorial rings (with radii of $\sim$1$.\!\!^{\prime\prime}$1 and $\sim$3-4$''$) that have been previously mapped with the NOEMA and ALMA interferometers and extensively studied by (cite: cc12) and (cite: cc17), respectively. As a result, we will not study the CO emission from the rings in this work.

Our only focus will be on a newly discovered absorption component detected towards the continuum source both in the $^{12}$CO and $^{13}$CO observed transitions (Fig. [5](#f-co) and Fig. [15](#f-13co)). We observe a narrow (FWHM$\sim$3 km s$^{-1}$) CO absorption feature below the continuum level near the center of the nebula at velocity $V_{\rm LSR}$$\sim$80–81 km s$^{-1}$, i.e., redshifted relative to the centroid of the mRRLs. The absorption indicates that the excitation temperature in the CO absorbing layers is lower than that of the continuum background source, which corresponds to the compact collimated ionized wind.

Interestingly, the CO absorption feature is not centered at the nebula’s center but is slightly offset by $\delta$y$\sim$0$.\!\!^{\prime\prime}$012 towards the north. Given that the north lobe is moving away from the observer (with an inclination $i$$\sim$17$^\circ$), this offset suggests that the structure responsible for the absorption is likely an equatorial torus or disk surrounding the collimated ionized wind and positioned perpendicular to the lobes. In this configuration, the front side of the disk partially blocks the emission from the base of the receding north lobe, resulting in the observed CO absorption.

The observed redshift rules out that the absorption is produced neither in the arcsecond-scale central rings nor in the hourglass-shaped structure emerging from them reported by (cite: cc17), since all these structures are in expansion and would necessarily produce a blue absorption given their spatio-kinematic structure, which is very well characterized in the mentioned previous works. The redshift of the CO absorption feature by $\sim$6.2 km s$^{-1}$ (deprojected velocity adopting $i$=17$^\circ$) with respect to the velocity centroid of the mRRLs (Table [2](#t-parms)) ,

likely signifies gas infall movements from the disk toward the central source. This is further discussed in Sect. [6.2](#disk_co).

# Analysis

## Non-LTE radiative transfer modeling of mRRL and free-free continuum emission

We have modelled the free-free continuum and mRRL emission in M 2-9 using the non-LTE three-dimensional radiative transfer code Co$^{3}$RaL (Code for 3D Computing Continuum and Recombination Lines). The code and our modeling approach are described in detail in Appendix [10](#ap-co3ral) and [10.3](#ap:approach), respectively.

Our modeling of the compact ionized wind in M 2-9 with Co$^{3}$RaL began by employing the identical physical model utilized by CSC17 (see their Table 4). This model has been previously shown to accurately replicate the single-dish free-free continuum flux measurements and mRRL profiles observed in 2015 by these authors. As expected, this original model (which generates synthetic single-dish data closely resembling those from MORELI[^6]) fails to capture some of the characteristics of the ionized wind now revealed by our ALMA $\sim$0$.\!\!^{\prime\prime}$03-0$.\!\!^{\prime\prime}$06-resolution maps (Appendix  [12](#ap:csc17), Fig. [21](#f:csc17)).

![image](Co3RaL_M2-9_cubic_grid_299_hires.pdf) ![image](M2-9_RRLs_grey_scale_HVspots_hole_299.pdf) ![image](M2-9_RRLs_density_HVspots_hole_298.pdf) ![image](M2-9_RRLs_velocity_HVspots_hole_298.pdf)

+:-------------------------------------------------------+:--------------------------------------------------------------------------:+
| *Input parameters*                                                                                                                  |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Distance ($d$)                                         | 650 pc$^{*}$                                                               |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| LSR Systemic velocity ($V_{\rm sys}$)                  | $+$78 km s$^{-1}$                                                          |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Geometry                                               | *C-shaped horn*$^{\dag}$                                                   |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Inclination ($i$)                                      | 12$^\circ$                                                                 |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Equatorial radius ($R_{\rm eq}$)                       | 8 au                                                                       |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Outer radius ($R_{\rm out}$)                           | 40 au                                                                      |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Nucleus outer radius ($R_0$)                           | 4 au                                                                       |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| HVSs inner boundary ($y_1$)                            | 15 au                                                                      |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| HVSs outer boundary ($y_2$)                            | 28 au                                                                      |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Electron temperature ($T_{\rm e}$)                     | 15000 K                                                                    |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Electron density ($n_{\rm e}$):                        |                                                                            |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| nucleus (I)                                            | 2.5$\times 10^{\rm 8}$ cm3                                                 |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| inner wind (II)                                        | 1.7$\times 10^{\rm 8}$($\frac{r}{4{\rm au}}$)$^{-3.0}$ $\,$cm$^{\rm -3}$   |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| HVSs (III)                                             | 1.0$\times 10^{\rm 8}$($\frac{r}{15{\rm au}}$)$^{-4.7}$ $\,$cm$^{\rm -3}$  |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| outer wind (IV)                                        | 2.5$\times 10^{\rm 6}$($\frac{r}{28{\rm au}}$)$^{-1.4}$ $\,$cm$^{\rm -3}$  |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Kinematics                                             | *radial expansion + rotation*                                              |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Expansion velocity ($V_{\rm exp}$):                    |                                                                            |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| nucleus (I)                                            | 10 km s$^{-1}$                                                             |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| inner wind (II)                                        | 10 km s$^{-1}$                                                             |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| HVSs (III)                                             | 70+1.5$\times$($r$-15 au) km s$^{-1}$                                      |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| outer wind (IV)                                        | 90 km s$^{-1}$                                                             |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Rotation velocity ($V_{\rm rot}$)                      | 7-10 km s$^{-1}$                                                           |
+--------------------------------------------------------+----------------------------------------------------------------------------+
|                                                        |                                                                            |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| *Implied physical properties of the jet*                                                                                            |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Ionized mass ($M_{\rm ion}$)                           | 4.3$\times 10^{\rm -6}$$M_{\odot}$                                         |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Mass-loss rate ($\dot{M}$)                             | 7.2$\times 10^{\rm -7}$ $M_{\odot}$ yr$^{-1}$                              |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Kinematic age ($T_{\rm kin}$)                          | 1.0-10.3 yr ($\sim$6 yr)                                                   |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Scalar momentum ($P$)$^{\ddag}$                        | 6.4$\times 10^{\rm 34}$ g cm/s                                             |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Total kinetic energy ($E_{\rm k}$)                     | 2.8$\times 10^{\rm 41}$ erg                                                |
+--------------------------------------------------------+----------------------------------------------------------------------------+
| Mechanical luminosity ($\dot{M}$$\times$$V_{\rm exp}$) | 1.5$\times 10^{\rm 33}$ erg/s                                              |
+--------------------------------------------------------+----------------------------------------------------------------------------+

: Properties of the central ionized core of M 2-9 derived from our radiative transfer modeling (Sect. [6.1](#model) and Fig. [6](#f-model)).

\
Table notes: In all cases, $r$ is the radial distance to the center. Departure coefficients $b_n$ are from (cite: sto95). Regions I-IV within the wind are shown in Fig. [6](#f-model). The model presented has 333$^3$ cubic cells of 0$.\!\!^{\prime\prime}$0015$\times$0$.\!\!^{\prime\prime}$0015$\times$0$.\!\!^{\prime\prime}$0015 ($\sim$1 au$\times$1 au$\times$1 au).

To obtain an improved model that fits these new details, we progressively adjusted the parameters of the input model (exploring a wide range of physical conditions and over $\sim$300 models) until a reasonable match was achieved between the model predictions and the data. The ALMA-based improved M 2-9 model presented here, contrary to the one in (cite: san17), has not been run under the LTE approximation but in non-LTE. This is because the new ALMA data show a frequency dependence of the integrated flux of the Hn$\alpha$ lines steeper than observed in 2015 with the IRAM-30 m radiotelescope and deviating from the expectations in LTE.

The best-fit model parameters are summarized in Table [3](#t-model) and Fig. [6](#f-model), and the predicted free-free continuum and mRRL emission maps are shown in Figs. [7](#f-contmod)-[9](#f-modfig4). Throughout the modeling process, we kept the number of model parameters as low as possible, aiming at simplicity.

![image](M2-9_RRLs_SED_HVspots_hole_282.pdf) ![image](M2-9_continuum_imaging_95_35GHz_HVspots_hole_299-NICE.pdf)

With regard to the wind’s structure, although the cylindrical geometry remains a reasonable approximation, the new observations necessitate two significant changes: $i$) a much narrower bipolar structure (particularly an outer radius value of $R_{\rm out}$$\sim$40 au), to reproduce the elongation of the maps and avoid generating excessively extended emission in the transverse direction compared to the data, and $ii$) a narrow waist at the base of the wind ($R_{\rm eq}$$\sim$8 au) to prevent excessive emission from the central regions. Additionally, we introduced a C-shaped curvature to the bipolar outflow to closely match the analogous shape observed in the 3mm-continuum maps. While this paper does not address centimeter-wavelength properties of the free-free continuum, which originates well beyond the mm-wavelength emission’s spatial range, we observed that gradually widening the wind beyond axial distances of 15-20 au (i.e. emulating a trumpet-like or hyperbolic horn shape) yields also a better match of the cm-continuum fluxes and best reproduces the faint, extended emission observed in the 3mm-continuum maps beyond $\delta$y$\sim$0$.\!\!^{\prime\prime}$12.

Various inclinations for the line-of-sight axis of the wind around $i$=17$^\circ$ were examined, with the most successful models having an inclination of $i$=12$^\circ$.

Regarding the wind’s density structure, a notable difference compared to the previous model is the necessity to include well-defined regions with different density profiles. These regions are defined as the nucleus (I), the inner wind (II), the HVSs (III), and the outer wind (IV) – see Fig. [6](#f-model). Specifically, to reproduce the relatively bright emission from the HVSs it becomes necessary to introduce a relatively dense, shell-like structure at axial distances of $\sim$15–30 au from the center within the wind.

Without these dense shells (i.e. with a unique, smooth density power-law) is not possible to reproduce the S-shape of the axial position-velocity diagrams observed for H30$\alpha$ and H39$\alpha$. Immediately below and above the HVSs are the inner and outer winds, respectively. The density in the outer wind primarily determines the cm-continuum flux and the surface brightness of the 3mm-continuum immediately beyond the HVSs. Meanwhile, the density of the inner wind is constrained by the 1mm-continuum maps and the line-to-wings intensity ratio of the mRRLs. The maximum electron density in the central regions interior to the HVSs is constrained to $n_{\rm e}$$<$3$\times 10^{\rm 8}$ $\,$cm$^{\rm -3}$ by the full width of the H30$\alpha$ line: higher electron densities would produce excessively broad emission wings from the core (offset $\delta$y=0$''$) due to electron pressure broadening (see also model caveats in Appendix [13](#ap:caveats)). Since the density of the inner wind cannot be larger than this maximum $n_{\rm e}$ value, a nuclear compact region (assumed spherical and with constant $n_{\rm e}$=2.5$\times 10^{\rm 8}$ $\,$cm$^{\rm -3}$, for simplicity) is then necessary to reproduce the mm-continuum flux level, which otherwise would fall below the observed values.

![image](M2-9_spectral_line_imaging_H30ALPHA_HVspots_hole_297-MODEL-spectre.pdf) ![image](M2-9_spectral_line_imaging_H30ALPHA_HVspots_hole_297-area-8-52-MODEL-NICE.pdf) ![image](M2-9_spectral_line_imaging_H30ALPHA_HVspots_hole_297-mask-MODEL-VELO.pdf)\
![image](M2-9_spectral_line_imaging_H39ALPHA_HVspots_hole_297-MODEL-spectre.pdf) ![image](M2-9_spectral_line_imaging_H39ALPHA_HVspots_hole_297-area-8-52-MODEL-NICE.pdf) ![image](M2-9_spectral_line_imaging_H39ALPHA_HVspots_hole_297-mask-MODEL-VELO.pdf)

![image](M2-9_spectral_line_imaging_H30ALPHA_HVspots_hole_297-vyx-MODEL.pdf) ![image](M2-9_spectral_line_imaging_H39ALPHA_HVspots_hole_297-vyx-MODEL.pdf)\
![image](M2-9_spectral_line_imaging_H30ALPHA_HVspots_hole_297-vxy-MODEL.pdf) ![image](M2-9_spectral_line_imaging_H39ALPHA_HVspots_hole_297-vxy-MODEL.pdf)

To simplify, we maintain a constant value for the electron temperature throughout the various regions of the wind. It is worth noting that while we cannot entirely rule out the possibility of temperature fluctuations within the wind, this factor alone cannot provide a satisfactory fit of the observed brightness distribution in the mRRL emission maps[^7].

The value deduced $T_{\rm e}$$\sim$15000 K, which should be taken as a representative average value within the ionized wind regions under study, is higher than than derived by CSC17 based on observations obtained 2 years earlier ($T_{\rm e}$$\sim$7500 K).

While there are uncertainties of up to $\Delta$$T_{\rm e}$$\sim$15–20%, the observed increase in the average electron temperature in the ionized wind might indeed reflect real variations in the wind’s properties over time, for example, an increase of the electron temperature may reflect an increase of collisional ionization as a result of recent propagation/development of shocks.

In terms of wind kinematics, the distinctive S-shape observed in the position-velocity diagrams along the axis of the mRRLs can only be explained by incorporating a steep velocity rise at the HVSs, which has been approximated by a step function. This step function represents a low velocity of $\sim$10 km s$^{-1}$ within distances less than $\sim$15 au; beyond this point, i.e. within the HVSs, the velocity rises from $\sim$70 to $\sim$90 km s$^{-1}$. Beyond the HVSs, in the outer wind, the velocity remains unconstrained as the line emission from these tenuous regions is below our detection limit.

Within the HVSs, we explored alternative velocity functions that varied in steepness (including constant velocity), but these produced a poorer match to the data.

Our best-fit model also includes rotation, which is needed to reproduce the observed velocity gradient perpendicular to the lobes (Sect. [5.1](#res-mrrls)). In the Appendix [9](#ap-figures) we show a model with no rotation for comparison. Since the angular resolution of the data does not allow us to distinguish between Keplerian or momentum conservation velocity profiles, we have used a constant rotation velocity of 7 km s$^{-1}$for simplicity. This value (at a representative radius of $R_{\rm eq}$=8 au) implies a lower limit to the central mass of $\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$0.4 $M_{\odot}$.

The total ionized mass within the model region that produces the observed (sub)mm-to-cm free-free continuum and mRRL emission is $M_{\rm ion}$$\sim$4$\times 10^{\rm -6}$ $M_{\odot}$, similar to that obtained by CSC17. Considering the mean kinematical age of the wind, \<$t_{\rm kin}$\>$\sim$6 yr, the average mass-loss rate implied from the model is $\dot{M}$$\sim$7$\times 10^{\rm -7}$ $M_{\odot}$ yr$^{-1}$, which is also in good agreement with the value obtained by CSC17. This agreement is expected because, as discussed in CSC17, the mass/mass-loss rate is almost exclusively constrained by the flux of the free-free continuum, which has not shown discernible variations considering flux uncertainties ($\sim$5–10% in our ALMA data and $\sim$20–30% in the IRAM-30 m data analyzed by CSC17). The determination of the mass/mass-loss rate is subject to some uncertainty due to factors such as the uncertain distance to the source, the simplified model used for the structure and kinematics of the ionized wind, and the moderate range of acceptable values for different model parameters. This likely results in a mass/mass-loss rate uncertainty of a factor $\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$2–3. We caution that given the relatively complex structure and density stratification in the ionized central regions of M 2-9, interpreting the meaning of the mass-loss rate is not straightforward (see Sect. [7.2](#dis-mloss)). The total scalar momentum, kinetic energy, and the average mechanical luminosity of the ionized wind have been computed and are given in Table [3](#t-model). Model caveats and other final modeling remarks are discussed in appendix  [13](#ap:caveats).

## CO absorption and 1 mm continuum: Evidence of a Compact Equatorial Disk

In this section, we provide compelling evidence from our ALMA data supporting the existence of an equatorial disk composed of gas and dust surrounding the collimated ionized wind emerging from M 2-9 and oriented perpendicular to the lobes. This equatorial disk is probably the counterpart of the compact ($\sim$37$\times$46 mas) flattened dust structure observed along the equatorial plane of the nebula using VLTI/MIDI at 8-13$\mu$m (cite: lyk11).

First, as shown in Fig. [5](#f-co) and briefly discussed in Sect. [5.2](#res-co), the structure responsible for the CO absorption observed against the compact continuum source at the center of M 2-9 is likely an equatorial torus or disk surrounding the collimated ionized wind and positioned perpendicular to the lobes. In this configuration, the front side of the disk partially blocks the emission from the base of the receding north lobe, resulting in the observed CO absorption. Furthermore, differences in the brightness distribution of the continuum at 1 and 3 mm can also be attributed to the presence of an equatorial dust disk, which is expected to be the counterpart of the gas disk inferred from the CO absorption. In particular, at 1 mm, where dust-related effects are more prominent due to higher dust opacity and a larger contribution of dust thermal emission to the total emission (Fig. [2](#sed-alma)), the lower brightness of the northern lobe compared to the southern lobe can be partially explained by absorption of the free-free continuum from the collimated ionized wind that is behind the front side of the disk.

Additionally, the broad-waisted structure observed in the 1 mm continuum map (but absent at 3 mm and in the H30$\alpha$ maps) can be attributed to dust thermal emission from regions outside the narrower background continuum source, indicative of the presence of a dusty disk surrounding the ionized wind. Indeed, in contrast to the expected behaviour for free-free continuum emission, we observe that the size of the waist is larger at 1 mm (reaching a maximum radius, at 3$\sigma$ level, of $\sim$0$.\!\!^{\prime\prime}$09 at 232.9 GHz – Fig. [1](#f-cont)).

However, in ionization-bounded or density-bounded H ii regions, the free-free continuum emission decreases with increasing frequency or remains constant, as it is indeed observed in the mm-to-cm continuum maps of M 2-9 in the axial direction and at lower frequencies in both the equatorial and axial directions (cite: lim03; dlF22). Therefore, the larger waist observed at higher frequencies is consistent with the contribution of dust thermal emission from the disk.

In the following, we attempt to establish some constraints on the physical conditions, including temperature and CO line opacity, as well as the dimensions (radius and vertical thickness) of the disk and its kinematics using the information contained in the CO absorption profile.

### Disk’s physical conditions

As shown in detail, for example, by (cite: san22) in their analysis of the compact NaCl absorption feature observed at the central rotating disk of the post-AGB nebula OH 231.8$+$4.2, the presence of absorption enables constraining the excitation temperature and opacity of the absorption line observed. This is done by comparing the brightness temperature of the absorption line (after continuum subtraction), $T_{l}^{\rm on}$, the brightness temperature outside the continuum source,

$T_{l}^{\rm off}$, and the continuum brightness peak in the same spectral window as the line is observed, $T_{\rm c}$. Taking into account the values of the absorption and the upper limit to the emission measured in the CO maps of M 2-9 along with the continuum peak in the same spectral window[^8] ($T_{l}^{\rm on}$$\sim$$-$308 K, $T_{l}^{\rm off}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$50 K, and $T_{\rm c}$$\sim$2350 K), we deduce $T_{\rm ex}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$330 K and $\tau$$\sim$0.16.

This value of the CO line opacity and $T_{\rm ex}$ imply a CO column density of $N_{\rm CO}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$6$\times 10^{\rm 17}$ $\,$cm$^{\rm -2}$, for a line width of $\sim$3 km s$^{-1}$ (in this calculation we used the on-line version of the non-LTE line radiative transfer code RADEX[^9] by (cite: radex)). Adopting a CO-to-H$_2$ relative abundance of $X_{\rm CO}$=2$\times 10^{\rm -4}$, which is typical of O-rich sources (cite: ram18), we derive a total column density of $N_{\rm H_2}$$\sim$3$\times 10^{\rm 21}$$\,$cm$^{\rm -2}$ across the absorbing layers (along the line of sight) of the disk.

However, this value represents a lower limit for the column density because the CO abundance used in the calculation is probably significantly overestimated due to strong photodissociation caused by intense ionizing radiation or shocks.

The outer radius of the disk can be estimated by considering the angular size of the broad-waist observed in the 232.9 GHz continuum map. From this analysis, an approximate value of $R_{\rm out}$$\sim$0$.\!\!^{\prime\prime}$075 (beam-deconvolved; equivalent to $\sim$50 au at a distance of 650 pc) is obtained, as discussed earlier in this section. This relatively large radius, along with the likely binary orbital separation of $\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$15 au (cite: lyk11; cc12; san17), suggests the disk is most likely circumbinary rather than an accretion disk, which typically has a size comparable to or slightly larger than the radius of the accreting compact object. A lower limit to the disk radius can also be obtained from the offset to the north where the CO absorption is observed ($r_{\rm
  abs}$$\sim$0$.\!\!^{\prime\prime}$012$\sim$8 au). This lower limit arises from geometric considerations, as the CO absorption corresponds to the radius within the disk where the column density reaches its maximum, which is not expected to occur at the very edge of the disk.

Assuming a line-of-sight inclination of $i$=12-17$^\circ$ for the disk equator, we can estimate a lower limit of $R_{\rm out}$$\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$27-38 au.

Based on the disk’s dimensions and the lower limit to the derived column density, we estimate the total mass to be $M_{\rm
  disk}$$>$2$\times 10^{\rm -6}$ $M_{\odot}$. Additionally, the disk could be larger than what is seen in our ALMA maps, as the emission is probably limited by sensitivity, which would result in an even larger value for the disk gas mass.

The radius and the temperature of the equatorial disk in M 2-9 are similar to those of the circumbinary disk recently discovered at the center of OH 231.8$+$4.2, a well-known massive bipolar outflow associated with an AGB+main-sequence binary system (cite: san22). Assuming the average density of both disks is similar, $n_{\rm H_2}$$\approx$10$^8$ $\,$cm$^{\rm -3}$, we estimate the line-of-sight path length for CO absorption to be $r_{\rm
  t}$$>$$N_{\rm H_2}$/$n_{\rm H_2}$$\sim$2 au. The lower limit arises from the upper limit to the CO/H$_2$ fractional abundance linked to a possibly enhanced CO photodissociation. This implies a vertical thickness of the M 2-9 disk, after deprojection, of $h$$>$0.6 au, resulting in an aspect ratio $h/r$ larger (or much larger if strong CO photodissociation) than 0.01.

### Disk’s kinematics

The (deprojected) redshift of the CO absorption feature by $\sim$6.2 km s$^{-1}$ with respect to the systemic velocity of the background collimated ionized wind can be plausibly explained by gas infall from the disk toward the central region. Gas infall motions from the inner regions of circumbinary disks, formed e.g. in Wind Roche Lobe OverFlow (WRLOF) binary systems, is theoretically expected (cite: mm99; moh07; chen17) and has indeed been observed in a number of post-AGB objects with interacting binaries (cite: buj21). An infall velocity of $\sim$6.2 km s$^{-1}$ observed at an average radial distance of $r_{\rm
  abs}$$\sim$27–38 au from the center (Sect. [6.2.1](#disk_phys)) would imply a central mass of $\sim$0.7 $M_{\odot}$, assuming that the gas started falling with (near) zero velocity from a point much far beyond the observed infall radius. This represents a lower limit for the central system’s mass since the closer we assume the fall started, the larger the estimated mass of the central system becomes. If we consider that the gas began falling in from the radius of the broad-waisted structure observed in the 1 mm continuum maps ($\sim$50 au) then the central mass would be $\sim$2.0 $M_{\odot}$. This should be regarded as an upper limit for two reasons. First, the radius of the disk in our maps might only represent a lower limit to the actual disk outer radius, which could extend beyond our sensitivity limit. Second, the infall velocity may be smaller than $\sim$6.2 km s$^{-1}$ if the centroid of the mRRLs is slightly blue-shifted relative to the systemic velocity of the source (as suggested by our model, Sect. [6.1](#model) and Table [3](#t-model)).

The mass range derived from these crude estimates is consistent with the previous assessments of the central binary’s mass by (cite: cc12), who proposed a low-mass companion of $m_2$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$0.1–0.2 $M_{\odot}$ orbiting around a $m_1$$\sim$0.5-1 $M_{\odot}$ mass-losing star.

In principle, rotation of the disk could also produce a redshifted CO absorption feature if (and only if) the center of rotation and the center of the ionized region do not coincide, i.e., if both are off-centered. Only then will the rotational velocity have a non-zero component in the line of sight direction. In the context of a circumbinary disk, where the disk rotates around the center of mass of the system rather than around one of the binary components, the offset of the disk relative to the centroid of the ionized wind is expected. However, to observe a significant line-of-sight rotational velocity it is essential that the separation between the disk’s centroid and the ionized wind (denoted as $r_{\rm dw}$) and the radial distance where most of the absorption occurs (denoted as $r_{\rm abs}$) are comparable. Our data allows us to estimate $r_{\rm dw}$ to be around $\sim$0$.\!\!^{\prime\prime}$007$\sim$5 au (Sect. [4.1](#cont_maps)) and $r_{\rm abs}$ to be $\sim$38–27 au (Sect. [6.2.1](#disk_phys)). Therefore, to achieve a line-of-sight rotational velocity of $\sim$6.2 km s$^{-1}$, the actual rotational velocity at $\sim$27–38 au should be $\sim$6.2$\times$$\frac{(27-38)}{5}$$\sim$33–47 km s$^{-1}$ (from basic geometric calculations). Such a high velocity would imply an unreasonably massive central object, exceeding 30 $M_{\odot}$.

# Discussion

Both the nature of the central binary system residing in the core of M 2-9 and which of the stars is launching and ionizing the bipolar wind observed in our mm-continuum and mRRL emission maps are two fundamental unknowns. In this section, we will analyze/discuss some of the results of our work with the aim of making progress in this regard.

## Ionizing central source

As is well known (cite: con16), the number of Lyman continuum photons emitted per second ($N_{\rm LyC}$) needed to reproduce the

emission from the ionized wind at the core of M 2-9 can be computed using the measured value of the free-free continuum flux (S$_\nu$) at a given frequency ($\nu$) as:

$$\begin{equation*}
\mbox{$N_{\rm LyC}$}= 7 \times 10^{46} \left( \frac{\mbox{$T_{\rm e}$}}{10^4\text{K}} \right)^{-0.45} \left( \frac{S_\nu}{\text{mJy}} \right) \left( \frac{d}{\text{kpc}} \right)^2 \left( \frac{\nu}{\text{GHz}} \right)^{0.1}
  
\end{equation*}$$

For an electron temperature of $T_{\rm e}$$\sim$15,000 K (Sect. [6.1](#model)) and a free-free continuum of 102.80 mJy at 95.3 GHz (after subtracting the 260 K dust emission component from the total continuum fluxes in Table [1](#tab:spws) — see also Fig. [2](#sed-alma)), we calculate a Lyman continuum photon rate of log$N_{\rm LyC}$$\sim$43.8 s$^{-1}$. This value has been compared with the Lyman continuum output rate from the grid of model atmospheres of early B-type stars by (cite: lan07) to investigate the central ionizing source. We find that a star with an effective temperature of around $T_{\rm eff}$$\sim$25 kK (with $R_{\star}$$\sim$1.3$R_{\odot}$, adopting $L_{\star}$$\sim$600 $L_{\odot}$ at 650 pc, and with a surface gravity log $g$\[cgs\]$\sim$4, adopting a stellar mass of $\sim$0.5 $M_{\odot}$ (cite: san17)) can account for the observed ionization. A similar effective temperature for the central ionizing source (early B-type or late O-type) was obtained by (cite: cal78) from analogous considerations (and using continuum flux measurements at cm-wavelengths) but also independently by (cite: all72) and (cite: swi79) from the analysis of the optical line emission spectra. This result implies that there is not need to invoke the presence of a hotter companion star to explain the observed nebular ionization in M 2-9.

If, as previously speculated, a white dwarf (WD) companion exists at the core of M 2-9 and is responsible for the observed nebular ionization, we can establish a lower limit to its effective temperature. By comparing the value of $N_{\rm LyC}$ calculated from the mm-continuum flux with the Lyman continuum output rate for WD stars expected from model atmosphere models by, e.g., (cite: wel13), we find that the effective temperature of the WD must be larger than 50,000 K, implying a spectral type O 5 or earlier.

The luminosity and mass of the progenitor star of M 2-9 remain uncertain due to the lack of precise distance measurements (Sect. [1](#intro)).

At a distance of $d$=650 pc, adopted in this study, the luminosity of M 2-9 is below the expected value of $\sim$2500 $L_{\odot}$ for the least massive stars (around 0.8 $M_{\odot}$) that are expected to evolve off the main sequence within a *Hubble* time (cite: mil16).

A possible explanation for the low luminosity of the central star of M 2-9 is that it could be a post Red Giant Branch (post-RGB) object, meaning that it has prematurely left the RGB phase of stellar evolution. Recent studies have highlighted the existence of post-RGB stars with many characteristics similar to post-AGB objects, and it has been speculated that their peculiar evolution, deviating from standard models, may be influenced by strong interactions with close binary companions (cite: oud22; kam16; hri20; olo19).

## Implications from the mass-loss rate

The average mass-loss rate of the ionized bipolar wind at the core of M 2-9 is deduced to be of $\dot{M}$$_{\rm  w}$$\approx$10$^{-7}$ $M_{\odot}$ yr$^{-1}$ (Sect. [6.1](#model)).

Interpreting the meaning of the mass-loss rate is not straightforward when we are uncertain about which of the stars is responsible for launching the wind.

If the ionized wind emerges from the mass-losing star, then, the measured mass-loss rate of the present-day wind is significantly lower than the rates observed $\sim$1300 and $\sim$900 years ago, $\approx$10$^{\rm -5}$ $M_{\odot}$ yr$^{-1}$, which were responsible for forming the large-scale nebula, including the massive CO equatorial rings (Sect. [1](#intro)). In this scenario, the substantial reduction in the mass-loss rate with respect to previous epochs can be interpreted as evidence that the primary star has transitioned to a post-AGB or post-RGB phase.

Alternatively, the star could currently be in the AGB phase with a mass-loss rate of $\dot{M}$$_{\rm AGB}$$\approx$10$^{\rm -7}$ $M_{\odot}$ yr$^{-1}$, which is more in line with what is expected for a low-mass progenitor star, but the ejection of the large-scale nebula, including the CO rings, could have occurred at two specific moments with "abnormally" high rates.

If the ionized wind does not directly originate from the mass-losing primary star but, instead, from its companion after mass transfer through disc-mediated accretion, it is expected that this wind would interact with the slow wind of the donor star. Such an interaction would give rise to a complex bipolar structure characterized by intricate density and velocity patterns, featuring multiple shock formations and a dense equatorial region as shown by analytical studies (cite: sok00; liv01) and numerical simulations (cite: gar04). According to these investigations, if this scenario applies to M 2-9, the region responsible for emitting mRRLs would encompass the ionized portion of this complex structure[^10], including both the primary’s slow wind and the companion’s fast wind, both of which would exhibit significant structural and velocity alterations due to their interaction. In this context, the mass-loss rate estimated in our study is likely to fall between the mass-loss rates of the mass-losing star and that of the companion.

## Wind structure and kinematics

Our ALMA observations show the presence of a collimated, ionized wind emanating from the center of M 2-9. As observed at mm-wavelengths, this narrow-waisted wind extends along the nebular axis direction up to radial distances of $\sim$75 au and $\sim$40 au in the perpendicular direction.

Based on radio-continuum emission maps, the ionized wind extends up to least 230 au along the axis (cite: lim03; dlF22), resulting in an aspect ratio of $>$4.5.

This wind displays high-velocity motions, reaching speeds of $\sim$80 km s$^{-1}$, thereby categorizing it as a jet. One of the significant findings from our data and modeling is the presence of a non-uniform density structure within the jet: we find alternating regions with noticeable density variations, characterized by regions of high density and areas of low density.

This density pattern may reflect the presence of shock-compressed regions and/or fluctuations in the mass-loss rate on short timescales.

The jet, as seen in the 3 mm-continuum emission maps (Fig. [1](#f-cont)), displays a distinctive C-shaped curvature, consistent with that observed in the JVLA 7 mm-continuum emission maps $\sim$11 years earlier (cite: dlF22). As suggested by (cite: dlF22), evoking the old model by (cite: liv01), the mirror curvature of the jet could be caused by the influence of the dense primary star’s wind on a jet hypothetically launched by the companion.

We believe that the presence of poloidal magnetic fields could also be considered as an alternative explanation, potentially exerting a bending effect on the ionized wind along the field lines. By equating the magnetic and mechanical energy densities, we estimate that a magnetic field strength of $\sim$50 mG could induce the observed curvature in the ionized jet, based on typical densities ($\sim$2$\times 10^{\rm 6}$ $\,$cm$^{\rm -3}$) and expansion velocities ($\sim$80 km s$^{-1}$) in the outer regions of the jet ($\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$30 au), where the curvature is observed. This estimate is in good agreement with existing, albeit limited, observations of magnetic fields in (post-)AGB envelopes at similar or even larger radial distances from the center (cite: bla09; vlem18).

In both cases, the orientation of the curvature depends on the relative position of the stars, which changes over time as the stars move in their orbit. Since the orientation of the curvature has remained unchanged since 2006, the star producing the bending effect is still situated on the same side

relative to the star launching the jet. This observation is consistent with the small time lapse between the ALMA and JVLA observations, approximately one ninth of the orbital period ($P_{\rm orb}$$\sim$90 yr).

Our ALMA data have revealed the kinematics of the jet, showing a non-uniform velocity field with low-expansion velocities ($\sim$10 km s$^{-1}$) at the center and maximum line-of-sight projected velocity widths of $\sim$80 km s$^{-1}$ at around $\sim$15–30 au along the axis (HVSs).

The abrupt change in velocity observed at/within the compact HVSs, relative to the center, can be interpreted in at least two ways. One possibility is that the wind acceleration occurs at these 15–30 au scales through some unknown mechanism, possibly a combination of line-radiation pressure and the magneto-centrifugal mechanism.

Alternatively, HVSs may indicate a wider range of line-of-sight velocities arising from shocks within the ionized wind. Analytical bow-shock models (cite: har87) and numerical simulations (cite: den08) predict substantial velocity spreads in compact, shocked regions, which are indeed observed in various pPNe (cite: den08; rie06; sah06). Internal shocks can arise due to variations in the wind expansion velocity, which aligns with the time-varying mRRL profiles of M 2-9 (Sect. [5.1](#res-mrrls)). Shocks could also result from the interaction of the winds of the two central stars, assuming that both stars possess winds (cite: sok00; liv01; gar04).

# Summary and conclusions

Using ALMA, we conducted detailed mapping in bands 6 and 3 of the inner layers (within $r$$\sim$0$.\!\!^{\prime\prime}$2$\sim$130 au at $d$=650 pc) of the ionized core of M 2-9. The mm-continuum and the H30$\alpha$ and H39$\alpha$ line emission were imaged with spatial resolutions reaching down to $\sim$0$.\!\!^{\prime\prime}$03 and $\sim$0$.\!\!^{\prime\prime}$06, respectively. Our data provides detailed evidence for the presence of a compact, bent jet expanding with velocities of up to $\sim$80 km s$^{-1}$ at the core of this remarkable object. Using the non-LTE radiative transfer code Co$^{3}$RaL (Sect. [6.1](#model) and Appendix [10](#ap-co3ral)-[13](#ap:caveats)), we performed data modeling to derive valuable insights into the morphology, kinematics, and physical conditions of the jet. Our findings suggest a potential interaction between a tenuous companion-launched jet and the dense primary star’s wind. Here is a summary of our key findings:

- The mm-continuum emitting region is elongated along the main symmetry axis of the nebula, with dimensions of 0$.\!\!^{\prime\prime}$4$\times$0$.\!\!^{\prime\prime}$13 (260$\times$85 au at $d$=650 pc) at 3 mm and slightly smaller at 1 mm due to the lower opacity of the free-free continuum at shorter wavelengths.

- The spectral index of the continuum ($\sim$0.9) suggests predominantly free-free emission from an ionized wind, with a minor contribution from dust possibly originating from a warm compact disk.

- The ionized wind is collimated and displays a C-shaped curvature at 3 mm consistent with previous observations taken 11 yr earlier at 7 mm.

- The 1 mm-continuum map reveals a broad-waisted morphology oriented perpendicularly to the wind lobes, which is plausibly the counterpart of the compact $\sim$260 K dust disk observed in the mid-IR.

- CO and $^{13}$CO absorption features further support the presence of an equatorial disk with a radius of $\sim$50 au (likely circumbinary), with gas infall towards the central source. The analysis of the CO absorption feature suggests an excitation temperature of $T_{\rm ex}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$330 K and a CO column density of $N_{\rm CO}$$\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$6$\times 10^{\rm 17}$ $\,$cm$^{\rm -2}$. A lower limit to the mass of the disk of $>$2$\times 10^{\rm -6}$ $M_{\odot}$ is deduced.

- Emission from H30$\alpha$, H39$\alpha$, He30$\alpha$, and H55$\gamma$ is detected, with line emission extending to radial distances of up to $\sim$75 au along the direction of the nebular axis and $\sim$40 au in the perpendicular direction.

- Changes in the H30$\alpha$ and H39$\alpha$ line profiles over two years indicate variations in the wind’s kinematics and physical conditions. The wind has become faster during this time period.

- Both the H30$\alpha$ and H39$\alpha$ transitions exhibit a distinct velocity gradient along the axis of the nebula, implying an overall expansion along the axis of the bipolar outflow.

- Low expansion velocities, of $\sim$10 km s$^{-1}$, are observed at the center. Rapid wind acceleration or shocks are suggested by peak velocities of $\sim$70–90 km s$^{-1}$ in two compact regions, situated at a radial distance of $\sim$$\pm$15–30 au along the axis (HVSs).

- The ionized wind has a short kinematical age, including regions of less than a year old, explaining changes in the mRRL profiles on similar year-long timescales.

- The emission maps of H30$\alpha$, H39$\alpha$, and He30$\alpha$ lines reveal a subtle velocity gradient perpendicular to the lobes suggestive of rotation ($V_{\rm rot}$$\sim$7-10 km s$^{-1}$).

- Radiative transfer modeling indicates an average electron temperature of $\sim$15000 K and reveals a non-uniform density structure within the ionized jet, with electron densities ranging from $n_{\rm e}$$\approx$10$^6$ to $\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$10$^8$ $\,$cm$^{\rm -3}$. The mass and average mass-loss rate of the ionized wind is deduced to be of $M_{\rm ion}$$\sim$4$\times 10^{\rm -6}$ $M_{\odot}$ and $\dot{M}$$\approx$10$^{-7}$ $M_{\odot}$ yr$^{-1}$, respectively. These results potentially reflect a complex bipolar flow pattern resulting from the interaction of a tenuous companion-launched jet and the dense primary star’s wind.

- The mass of the central system is uncertain, but it is likely in the range of 0.4 to 2 $M_{\odot}$, based on the rotational and infall motions observed in the jet and the circumbinary disks, respectively, described in this study.

- The required number of Lyman continuum photons per second is consistent with a central star with an effective temperature of $\sim$25 kK and a luminosity of $\sim$600 $L_{\odot}$, perhaps a post-RGB star. We do not observe empirical evidence of fast ($\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$1000 km s$^{-1}$) ejections indicative of a compact companion. While a WD companion is not ruled out, our findings do not provide empirical evidence for it.

- The nature of the companion remains highly uncertain. Unravelling the nature of M 2-9’s central binary system and the intricate interplay between the primary star and its companion are essential for comprehending the mechanisms governing the observed mass loss and wind dynamics in this system.

# Acknowledgements

We would like to thank the referee, Joel Kastner, for his insightful comments and suggestions, which helped improve the clarity of this work. This paper makes use of the following ALMA data: ADS/JAO­.ALMA#2016.1.00161.S and ADS/JAO.ALMA#2017.1.00376.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The data here presented have been reduced and analyzed using CASA (ALMA default calibration software; `https://casa.nrao.edu`) and the GILDAS software (`http://www.iram.fr/IRAMFR/GILDAS)`. This work is part of the I+D+i projects PID2019-105203GB-C22 and PID2019-105203GB-C21 funded by Spanish MCIN/AEI/10.13039/501100011033. This research has made use of the SIMBAD database operated at CDS (Strasbourg, France) and the NASA’s Astrophysics Data System.

(ref: all72) Allen, D. A. & Swings, J. P. 1972, ApJ, 174, 583.

(ref: arr03) Arrieta, A. & Torres-Peimbert, S. 2003, ApJS, 147, 97.

(ref: bae13) Báez-Rubio, A., Martı́n-Pintado, J., Thum, C., & Planesas, P. 2013, A&A, 553, A45

(ref: bae14) Báez-Rubio, A., Martı́n-Pintado, J., Thum, C., et al. 2014, A&A, 571, L4.

(ref: buj01) Bujarrabal, V., Castro-Carrizo, A., Alcolea, J., et al. 2001, A&A, 377, 868.

(ref: buj05) Bujarrabal, V., Castro-Carrizo, A., Alcolea, J., & Ner i, R. 2005, A&A, 441, 1031

(ref: bal02) Balick, B., & Frank, A. 2002, ARA&A, 40, 439

(ref: bal18) Balick, B., Frank, A., Liu, B., et al. 2018, ApJ, 853, 168.

(ref: bla09) Blackman, E. G. 2009, Cosmic Magnetic Fields: From Planets, to Stars and Galaxies, 259, 35.

(ref: blo95) Bloecker, T. 1995, A&A, 299, 755 evolutionary tracks

(ref: Brussaard1962) Brussaard, P. J. & van de Hulst, H. C. 1962, Reviews of Modern Physics, 34, 507.

(ref: buj21) Bujarrabal, V., Agúndez, M., Gómez-Garrido, M., et al. 2021, A&A, 651, A4.

(ref: cal78) Calvet, N., & Cohen, M. 1978, MNRAS, 182, 687

(ref: cc12) Castro-Carrizo, A., Neri, R., Bujarrabal, V., et al. 2012, A&A, 545, A1

(ref: cc17) Castro-Carrizo, A., Bujarrabal, V., Neri, R., et al. 2017, A&A, 600, A4. 004-6361/201630101

(ref: cly15) Clyne, N., Akras, S., Steffen, W., et al. 2015, A&A, 582, A60.

(ref: con16) Condon, J. J. & Ransom, S. M. 2016, Essential Radio Astronomy, by James J. Condon and Scott M. Ransom. ISBN: 978-0-691-13779-7. Princeton, NJ: Princeton University Press, 2016.

(ref: cor11) Corradi, R. L. M., Balick, B., & Santander-Garcı́a, M. 2011, A&A, 529, A43.

(ref: chen17) Chen, Z., Frank, A., Blackman, E. G., et al. 2017, MNRAS, 468, 4465.

(ref: dec10) Decin, L., De Beck, E., Brünken, S., et al. 2010, A&A, 516, A69

(ref: den08) Dennis, T. J., Cunningham, A. J., Frank, A., et al. 2008, ApJ, 679, 1327.

(ref: doy00) Doyle, S., Balick, B., Corradi, R. L. M., et al. 2000, AJ, 119, 1339.

(ref: gar04) Garcı́a-Arredondo, F. & Frank, A. 2004, ApJ, 600, 992.

(ref: Goldwire1968) Goldwire, H. C. 1968, ApJS, 17, 445.

(ref: har87) Hartigan, P., Raymond, J., & Hartmann, L. 1987, ApJ, 316, 323.

(ref: her86) Herman, J., Burger, J. H., and Penninx, W. H. 1986, A&A, 167, 247

(ref: hof18) Höfner, S. & Olofsson, H. 2018, A&ARv, 26, 1.

(ref: hri20) Hrivnak, B. J., Henson, G., Hillwig, T. C., et al. 2020, ApJ, 901, 9.

(ref: dlF22) de la Fuente, E., Trinidad, M. A., Tafoya, D., et al. 2022, PASJ, 74, 594. pasj/psac020

(ref: kam16) Kamath, D., Wood, P. R., Van Winckel, H., et al. 2016, A&A, 586, L5.

(ref: Kardashev1959) Kardashev, N. S. 1959, Soviet Astronomy, 3, 813

(ref: Kielkopf1973) Kielkopf, J. F. 1973, Journal of the Optical Society of America (1917-1983), 63, 987

(ref: koh80) Kohoutek, L. & Surdej, J. 1980, A&A, 85, 161

(ref: kwo85) Kwok, S., Purton, C. R., Matthews, H. E., & Spoelstra , T. A. T. 1985, A&A, 144, 321

(ref: lan07) Lanz, T., & Hubeny, I. 2007, ApJS, 169, 83.

(ref: lee01) Lee, H.-W., Kang, Y.-W., & Byun, Y.-I. 2001, ApJL, 551, L121.

(ref: lim00) Lim, J., & Kwok, S. 2000, Asymmetrical Planetary Nebulae II: From Origins to Microstructures, 1 99, 259

(ref: lim03) Lim, J., & Kwok, S. 2003, Symbiotic Stars Probing Stellar Evolution, 303, 437

(ref: liv01) Livio, M. & Soker, N. 2001, ApJ, 552, 685.

(ref: lyk11) Lykou, F., Chesneau, O., Zijlstra, A. A., et al. 2011, A&A, 527, A105.

(ref: Martin2022) Martin, P. & Maass, F. 2022, Results in Physics, 35, 105283.

(ref: mar23) Martı́nez-Henares, A., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2023, ApJ, 955, 119.

(ref: mm99) Mastrodemos, N. & Morris, M. 1999, ApJ, 523, 357.

(ref: Menzel1937) Menzel, D. H. 1937, ApJ, 85, 330.

(ref: Mezger1967) Mezger, P. G. & Hoglund, B. 1967, ApJ, 147, 490.

(ref: mil16) Miller Bertolami, M. M. 2016, A&A, 588, A25.

(ref: moh07) Mohamed, S. & Podsiadlowski, P. 2007, 15th European Workshop on White Dwarfs, 372, 397

(ref: olo19) Olofsson, H., Khouri, T., Maercker, M., et al. 2019, A&A, 623, A153.

(ref: oud22) Oudmaijer, R. D., Jones, E. R. M., & Vioque, M. 2022, MNRAS, 516, L61.

(ref: pana75) Panagia, N. & Felli, M. 1975, A&A, 39, 1

(ref: pur75) Purton, C. R., Feldman, P. A., & Marsh, K. A. 1975, ApJ, 195, 479

(ref: ram18) Ramos-Medina, J., Sánchez Contreras, C., Garcı́a-Lario, P., et al. 2018, A&A, 619, C2.

(ref: rie06) Riera, A., Binette, L., & Raga, A. C. 2006, A&A, 455, 203.

(ref: Rybicki1986) Rybicki, G. B. & Lightman, A. P. 1986, Radiative Processes in Astrophysics, by George B. Rybicki, Alan P. Lightman, pp. 400. ISBN 0-471-82759-2. Wiley-VCH , June 1986., 400

(ref: sah06) Sahai, R., Young, K., Patel, N. A., et al. 2006, ApJ, 653, 1241.

(ref: san98) Sánchez Contreras, C., Alcolea, J., Bujarrabal, V., et al. 1998, A&A, 337, 233

(ref: san17) Sánchez Contreras, C., Báez-Rubio, A., Alcolea, J., et al. 2017, A&A, 603, A67.

(ref: san19) Sánchez Contreras, C., Báez-Rubio, A., Alcolea, J., et al. 2019, A&A, 629, A136.

(ref: san22) Sánchez Contreras, C., Alcolea, J., Rodriguez Cardoso, R., et al. 2022, A&A, 665, A88.

(ref: smg05) Smith, N. & Gehrz, R. D. 2005, AJ, 129, 969.

(ref: sch04) Schöier, F. L., Olofsson, H., Wong, T., Lindqvist, M., & Kerschbaum, F. 2004, A&A, 422, 651

(ref: sch83) Schönberner, D. 1983, ApJ, 272, 708

(ref: sch97) Schwarz, H. E., Aspin, C., Corradi, R. L. M., et al. 1997, A&A, 319, 267

(ref: sok00) Soker, N. & Rappaport, S. 2000, ApJ, 538, 241.

(ref: sol00) Solf, J. 2000, A&A, 354, 674

(ref: sto95) Storey, P. J., & Hummer, D. G. 1995, MNRAS, 272, 41

(ref: swi79) Swings, J. P., & Andrillat, Y. 1979, A&A, 74, 85

(ref: tor10) Torres-Peimbert, S., Arrieta, A., & Bautista, M. 2010, , 46, 221

(ref: vdB74) van den Bergh, S. 1974, A&A, 32, 351

(ref: radex) van der Tak, F. F. S., Black, J. H., Schöier, F. L., et al. 2007, A&A, 468, 627.

(ref: vas93) Vassiliadis, E., & Wood, P. R. 1993, ApJ, 413, 641

(ref: wel13) Welsh, B. Y., Wheatley, J., Dickinson, N. J., et al. 2013, PASP, 125, 644.

(ref: Wilson2009) Wilson, T. L., Rohlfs, K., & Hüttemeister, S. 2009, Tools of Radio Astronomy, by Thomas L. Wilson; Kristen Rohlfs and Susanne Hüttemeister. ISBN 978-3-540-85121-9. Published by Springer-Verlag, Berlin, Germany, 2009..

(ref: vlem18) Vlemmings, W. H. T. 2018, Contributions of the Astronomical Observatory Skalnate Pleso, 48, 187

# Additional Figures

![image](hst_1mmcont.pdf) ![image](hst_3mmcont.pdf)

![](fig_cubeH30a.pdf)

![](fig_cubeH39a.pdf)

![](He30a_nchan36_dv3kms-selfcal-spectre.pdf)

![](He30a_nchan36_dv3kms-selfcal-area-1-36-NICE.pdf)

![](He30a_nchan36_dv3kms-selfcal-mask-VELO.pdf)

![](H55g_nchan44-selfcal-spectre.pdf)

![](H55g_nchan44-selfcal-area-21-28-NICE.pdf)

![image](13CO_nchan33_dv0p6kms-selfcal-r0p5-area-11-21-nice.pdf) ![image](13CO_nchan33_dv0p6kms-selfcal-r0p5-13COabs-spectre.pdf)

![image](M2-9_spectral_line_imaging_H30ALPHA_HVspots_hole_283-mask-MODEL-VELO.pdf) ![image](M2-9_spectral_line_imaging_H39ALPHA_HVspots_hole_283-mask-MODEL-VELO.pdf)

# The non-ETL free-free continuum and mRRL radiative transfer code

Here, we provide a detailed description of our code used to model the free-free continuum and radio recombination line ALMA data presented in this work.

## Numerical calculations of the solution of the radiative transfer equation

As is well known, the solution of the radiative transfer equation in a plane-parallel, homogeous, and isotropic medium can be expressed as:

$$\begin{equation}
\label{eq:4}
I_\nu(\tau_{\nu}) = I_\nu(0){\rm e}^{-\tau_{\nu}} +
\mathcal{S}_{\nu}(1-{\rm e}^{-\tau_{\nu}}), 
\end{equation}$$

involving the frequency ($\nu$), the optical depth ($\tau_{\nu}$), the initial specific radiation at that frequency at the back surface of the source ($I_\nu(0)$), the specific intensity outgoing from the front surface of the source ($I_\nu(\tau_{\nu})$), and the source function ($\mathcal{S}_{\nu}$).

Astronomical sources are not completely homogeneous and the physical conditions vary from place to place. To address this, a common approach for computing the outgoing intensity of a realistically heterogeneous source is to partition it into small cells, each characterised by approximately constant physical conditions (refer to Figure [16](#fig:2)).

![](RT_cubes.pdf)

Once the source is subdivided into small cells with uniform temperature and density, Equation ([\[eq:4\]](#eq:4)) can be used to compute the outgoing intensity of each cell. As depicted in Figure [16](#fig:2), the outgoing intensity $I_{\nu,i-1}$ of cell $i-1$ serves as the initial intensity $I_\nu(0)$ for cell $i$, and similarly, the outgoing intensity of cell $i$ is used as the initial intensity for cell $i+1$, and so forth. The intensity of the pixel with coordinates ($x, y$), denoted $I_\nu(x,y)$, is determined through successive computations of the radiative transfer equation solution (Equation ([\[eq:4\]](#eq:4))) for cells along a single line of sight (i.e. along the $z$-axis). As a result, $I_\nu(x,y)$ represents the resulting outgoing intensity of the cell positioned at the forefront of the source, closest to the observer.\

## Code for Computing Continuum and Radio-recombination Lines: Co$^{3}$RaL

The Code for Computing Continuum and Radio-recombination Lines (Co$^{3}$RaL) is a C-based code designed to calculate the intensity of the free-free continuum and recombination line emission originating from an ionised nebula. It operates on user-defined geometrical shapes that can be specified analytically and relies on provided density, temperature, and velocity fields given by analytical functions. The outputs are ASCII tables containing information needed to generate continuum images, spectral energy distribution (SED) plots, spectral cubes, and spectral line profiles.

### Definition of the geometry

The grid of cells considered by Co$^{3}$RaL, within which the geometry of the emitting region is defined, is created in a coordinate system $\mathcal{C}$. The coordinates of each cell are given within the intervals $[-x_{\rm max}, x_{\rm max}]$, $[-y_{\rm max}, y_{\rm
    max}]$, and $[-z_{\rm max}, z_{\rm max}]$ for the $x$, $y$, and $z$ axes, respectively. The $x$-$y$ plane corresponds to the plane-of-the-sky, while the $z$-axis corresponds to the line-of-sight. Each interval is evenly divided into n$_{x}$, n$_{y}$, and n$_{z}$ cells along the respective axis. Co$^{3}$RaL sweeps through the cells of the grid along the $z$-axis and calculates the outgoing intensity for each cell until it reaches the cell positioned at the forefront of the source.

![](coordinate_systems.pdf)

The boundaries of the emitting region (i.e., the cells where the density and temperature are non-zero) are defined by an analytical function in a coordinate system $\mathcal{C}^{\prime}$. In general, the coordinate system $\mathcal{C}^{\prime}$ is rotated with respect to the coordinate system $\mathcal{C}$ (see, for example, Figure [17](#fig:3)). Consequently, the emitting region typically appears rotated relative to the $\mathcal{C}^{\prime}$ system. Co$^{3}$RaL sweeps through the cells of the grid along the $z$-axis of the coordinate system $\mathcal{C}$. When it reaches a cell with coordinates ($x$, $y$, $z$), it transforms the coordinates from $\mathcal{C}$ to $\mathcal{C}^{\prime}$ using the following rotation matrix:

$$\begin{equation}
\label{eq:5-1}
\begin{bmatrix}
    x' \\ y' \\ z'
\end{bmatrix}
=
\begin{bmatrix}
    \cos(\phi) & \sin(\phi) & 0 \\ -\cos(\theta) \sin(\phi) &
    \cos(\theta) \cos(\phi) & -\sin(\theta) \\ -\sin(\theta)
    \sin(\phi) & \cos(\phi) \sin(\theta) & \cos(\theta)
\end{bmatrix}
\begin{bmatrix}
    x \\ y \\ z
\end{bmatrix},
\end{equation}$$

where $\theta$ and $\phi$ are the inclination angle with respect to the plane of the sky and the position angle of the source, respectively. Once the coordinates of the cell are transformed into the coordinate system $\mathcal{C}^{\prime}$, Co$^{3}$RaL checks whether the cell is within the emitting region. If the cell is within the emitting region, the radiative transfer is performed using Equation ([\[eq:4\]](#eq:4)). If the cell is outside the boundary of the emitting region, it is skipped, meaning it is assumed that the cell does not affect the intensity $I_{\nu}$, and the code moves to the next cell along the line-of-sight. The resulting intensity for each line-of-sight, $I_\nu(x,y)$, is output using the coordinates of the coordinate system $\mathcal{C}$. It is worth noting that, since the radiative transfer is performed along rays in the line-of-sight, the result of the calculations is sensitive to the inclination of the source but not to the position angle.\

### Definition of the physical parameters

The definition of the physical parameters is more straightforward in the rotated $\mathcal{C}^{\prime}$ system, where they are expressed as relatively simple analytical functions dependent on the primed coordinates: $T$($x^{\prime}, y^{\prime}, z^{\prime}$), $n$($x^{\prime}, y^{\prime}, z^{\prime}$), and $\vec{v}$($x^{\prime},
y^{\prime}, z^{\prime}$). However, as mentioned above, Co$^{3}$RaL sweeps through the cells of the grid along the $z$-axis of the coordinate system $\mathcal{C}$. Thus, for each cell within the emitting region, Co$^{3}$RaL transforms the coordinates ($x$, $y$, $z$) to ($x^{\prime}$, $y^{\prime}$, $z^{\prime}$) (using the rotation matrix in Equation ([\[eq:5-1\]](#eq:5-1))), and then calculates the corresponding values of the physical parameters using the analytical functions defined in the $\mathcal{C}^{\prime}$ system. Subsequently, the outgoing intensity of the cell is calculated iteratively using Equation ([\[eq:4\]](#eq:4)) and the physical parameter values specific to that cell.

### Computation of the radio continuum

To compute the radio continuum emission, Co$^{3}$RaL uses the following free-free emission coefficient (cite: Rybicki1986):

$$\begin{equation}
\label{eq:5}
j_{\nu}^{\rm cont} = 6.8 \times 10^{-38} \left( \frac{n_e n_i}{4 \pi}
\right) Z^{2} T_{e}^{1/2} {\rm e}^{( -h\nu/k T_{e})} {g}(\nu,T_{e}),
\end{equation}$$

where $n_e$ and $n_i$ are the electron and ion densities, respectively, $Z$ is the electric charge of the ions, $T_e$ is the electron temperature, $h$ and $k$ are the Planck and Boltzmann constants, $\nu$ is the frequency of the radiation, and ${g}(\nu,T_{e})$ is the Gaunt factor, which is the sum of the Gaunt factors for free-free and bound-free transitions, ${g}(\nu,T_{e})=g^{ff}+g^{bf}$.\
Following (cite: bae13), the Gaunt factor for free-free transitions is calculated in the following way:

$$\begin{equation}
{g}_{ff} = \sqrt{\left( \frac{\sqrt{3} {\rm e}^{x} K_{0}(x)}{\pi}
  \right)^{2} + \left( a - b \log_{10} \left( \frac{h \nu}{k T_{e}}
  \right) \right)^{2}},
\end{equation}$$

where $K_{0}(x)$ is the modified Bessel function of the second kind and

$$\begin{flalign*}
& \gamma^{2} = Z^{2}\frac{h \nu_0}{k T_e}, & \\ & x = \left( \frac{h
    \nu} {2 k T_{e}} \right) \left( 1 + \sqrt{10 \gamma^{2}} \right),
  & \\ & a = 1.2 \exp \left( -\left( \frac{\log_{10}(\gamma^{2}) -
    1}{3.7} \right)^{2} \right), & \\ & b = 0.37 \exp \left( -\left(
  \frac{\log_{10}(\gamma^{2}) + 1}{2} \right)^{2} \right), &
\end{flalign*}$$

where $\nu_0$ is the hydrogen ionisation frequency with a numerical value of $\nu_0$=3.291$\times$10$^{15}$ Hz.\
The modified Bessel function of the second kind, $K_{0}(x)$, is computed using the following approximation (cite: Martin2022):

$$\begin{multline*}
K_{0}(x) = \frac{1}{\left(1 + 1.9776 x^2\right) \left(1 + 0.2778
  x^2\right)^{5/4} \cosh(x)}\cdot \\ \left(0.1159 - 0.0119x^2 - 0.5
\cdot \ln\left(\frac{x^2}{1 + x^2}\right) \right. \cdot \\ \left(1 +
3.0749 x^2 + 2.6248 x^4 + 0.4999 x^6\right)\biggr).
\end{multline*}$$

The Gaunt factor for bound-free transitions is calculated in the following way (cite: Brussaard1962):

$$\begin{flalign*}
& {g}_{bf} =
  2\Theta\sum_{n=m}^{\infty}g_{n}(\nu)\frac{{\rm e}^{\Theta/n^{2}}}{n^{3}},
  & \\ & \Theta=\frac{h\nu_{0}}{kT_{e}}, & \\ & m={\rm
    int}\left(\sqrt{\frac{\nu_{0}}{\nu}}\right)+1, &
\end{flalign*}$$

where int($x$) is the nearest integer value (rounded off value) of $x$. As pointed out by (cite: bae13), the value of $g_{n}(\nu)$ is taken as unity for all the considered frequencies, which yields results with an accuracy of $\sim$10 – 20%. However, it is worth noting that the Gaunt factors for bound-free transitions become significant only for frequencies $\nu$$\gtrsim$10$^{4}$ GHz (see Fig.A.1 of (cite: bae13)). Thus, this factor is negligible for RRLs.\
Subsequently, the absorption coefficient, $\kappa_{\nu}$, is obtained using Kirchhoff’s law as

$$\begin{equation}
\label{eq:6}
\kappa_{\nu}^{\rm cont} = j_{\nu}^{\rm cont}/B_{\nu}(T),
\end{equation}$$

where $B_{\nu}(T)$ is the Planck function given by

$$\begin{equation}
\label{eq:7}
B_{\nu}(T)=\frac{2 h \nu^3}{c^2} \cdot \frac{1}{{\rm e}^{h \nu/k T} - 1}.
\end{equation}$$

The optical depth, $\tau_{\nu}^{\rm cont}$ that is used in Equation ([\[eq:4\]](#eq:4)) to compute the intensity of the continuum emission is thus computed as

$$\begin{equation}
\label{eq:7}
\tau_{\nu}^{\rm cont} = \kappa_{\nu}^{\rm cont} dl,
\end{equation}$$

where $dl$ is the physical size of the cell, given in CGS units.

### Computation of the radio recombination lines in LTE conditions

Co$^{3}$RaL computes the emission of RRLs in LTE and non-LTE conditions. The emission of the lines in LTE conditions is computed using the following absorption emission coefficient (cite: Wilson2009):

$$\begin{equation}
\label{eq:10}
\kappa_{\nu}^{\text{line,*}} = \frac{1}{8 \pi} \left(
\frac{c\,\mathsf{n_{u}}}{\nu_{ul}} \right)^{2} \left( \frac{h^2}{2 \pi
  m_e k T_e} \right)^{3/2} {\rm e}^{h \nu_0/n_l^2 k T_e} A_{ul} \left(1 -
{\rm e}^{-h \nu_{ul}/k T_e} \right) n_e n_i V_{\nu},
\end{equation}$$

where $\nu_{ul}$ is the central rest frequency of the line, $\mathsf{n_{u}}$ is the upper level electronic quantum number, and $V_{\nu}$ is the Voigt profile of the line, obtained as a convolution of Gaussian and Lorentzian profiles. Using the notation of (cite: Kielkopf1973), the expression of the convolution is given as follows:

$$\begin{equation}
V(\beta_{l},\beta_{g}|\nu)=\int_{-\infty}^{+\infty}
\frac{\beta_{l}/\pi}{\beta_{l}^{2}+(\nu-\nu^{\prime})}\frac{1}{\sqrt{\pi}\beta_{g}}{\rm e}^{-(\nu^{\prime}/\beta_{g})^{2}}d\nu^{\prime},
\end{equation}$$

where $\beta_{l}$ and $\beta_{g}$ are the Lorentzian and Gaussian widths, defined as the half width at half maximum. Given that the calculation of this convolution needs to be done for every cell, it turns out to be computationally expensive. Therefore, Co$^{3}$RaL uses the approximation to the convolution given by (cite: Kielkopf1973):

$$\begin{equation}
V(\beta_{l},\beta_{g}|\beta\,x)=I(\beta_{l},\beta_{g})\,U(x),
\end{equation}$$

where $I(\beta_{l},\beta_{g})$ is given as

$$\begin{equation}
\label{eq:13}
I(\beta_{l},\beta_{g})=\frac{a}{\sqrt{\pi}\beta_{l}}f(a),
\end{equation}$$

and the expression for $U(x)$ is the following:

$$\begin{equation}
\label{eq:14}
U(x)=(1-\eta)G(x)+\eta L(x)+\eta (1-\eta)E(x)[G(x)-L(x)].
\end{equation}$$

The factor $a$ in Equation ([\[eq:13\]](#eq:13)) is defined as the ratio of the Lorentzian and Gaussian widths, $a=\beta_{l}/\beta_{g}$, and the form of the function $f(a)$ depends on the value of $a$ as follows:

$$\begin{equation}
f(a) =
\begin{cases} 
\frac{1}{\sqrt{\pi}} \left(\frac{1}{a + \frac{1/2}{a + \frac{1}{a +
      \frac{3/2}{a + \frac{2}{a + \dots}}}}}\right) & \text{if } a >
1.5, \\ \frac{1}{\sqrt{\pi}}(b_{1}t+b_{2}t^{2}+b_{3}t^{3}) & \text{if
} a < 1.5,
\end{cases}
\end{equation}$$

where

$$\begin{equation}
t=\frac{1}{1+b_{0}a},
\end{equation}$$ and $b_{0}=0.47047$, $b_{1}=0.61686$, $b_{2}=-0.16994$, and $b_{3}=1.32554$.\
The functions $G(x)$, $L(x)$, and $E(x)$ in Equation ([\[eq:14\]](#eq:14)) are defined as follows:

$$\begin{align}
& G(x)={\rm e}^{-\text{ln}(2)x^{2}}, \\ & L(x)=\frac{1}{1+x^{2}}, \\ &
  E(x)=\frac{0.8029-0.4207x^{2}}{1+0.2030x^{2}+0.07335x^{4}}.
\end{align}$$

The factor $\eta$ in Equation ([\[eq:14\]](#eq:14)) is defined as follows:

$$\begin{equation}
\eta=\frac{l}{l+g^{2}},
\end{equation}$$

where

$$\begin{align}
& l=\frac{\beta_{l}}{\beta}, \\ & \beta=\frac{1}{2}\beta_{l} \left\{1
  + \epsilon\,\text{ln}(2) + \left[\left(1 - \epsilon
    \,\text{ln}(2)\right)^{2} +
    \left(4.0\,\text{ln}(2)/a^{2}\right)\right]^{1/2}\right\}, \\ &
  g=\left(\frac{1-l}{\text{ln}(2)}\right)^{1/2},
\end{align}$$

and $\epsilon$=0.0990.\
The Gaussian width of the line, $\beta_{g}$, is calculated using the following expression (cite: Mezger1967):

$$\begin{equation}
\beta_g = \sqrt{\frac{2 k T_e}{m_H} + \frac{2}{3} v_{\text{tur}}^2},
\end{equation}$$

where $m_H$ is the mass of the hydrogen atom and $v_{\text{tur}}$ is the turbulent velocity due to turbulent motions of the plasma. The expression of the Lorentzian width, $\beta_{l}$, is taken from Table B.1 of (cite: bae13).

Finally, the optical depth of the line, $\tau_{\nu}^{\rm line*}$, in LTE conditions is given as

$$\begin{equation}
\tau_{\nu}^{\rm line*} = \kappa_{\nu}^{\text{line,*}} dl, 
\end{equation}$$

and the total optical depth, $\tau_{\nu}^{*}$, that is used in Equation ([\[eq:4\]](#eq:4)) to compute the intensity of the line plus continuum is the sum of both optical depths:

$$\begin{equation}
\tau_{\nu}^{*} = \tau_{\nu}^{\rm line*} + \tau_{\nu}^{\rm cont}.
\end{equation}$$

After performing the radiative transfer for the line plus continuum, the emission from the continuum is subtracted to obtain the emission from the line only.

### Computation of the spontaneous emission Einstein coefficients

The relationship between the Einstein coefficient for spontaneous emission, $A_{ul}$, and the thermalised absorption oscillator strength $f(\mathsf{n_{l}},\mathsf{n_{u}})$, with $\mathsf{n_{u}}>\mathsf{n_{l}}$, is given by (cite: Goldwire1968):

$$\begin{equation}
\label{Eq:1.3}
A_{ul} = 2\pi\alpha^{3}Z^{4}\, c \, \text{R$_{M}$} \frac{{(\mathsf{n_{u}}+\mathsf{n_{l}})^2 \cdot (\mathsf{n_{u}}-\mathsf{n_{l}})^2}}{{\mathsf{n_{l}}^2 \mathsf{n_{u}}^6}} f(\mathsf{n_{l}},\mathsf{n_{u}}),
\end{equation}$$

where $\alpha$ is the fine structure constant, $Z$ is the atomic number, $c$ is the speed of light, and $\text{R$_{M}$}$ is the Rydberg constant defined as

$$\begin{equation}
\label{Eq:1.4}
\text{R${_M}$} = \frac{\text{R${_\infty}$}}{1 + (m_{e}/M)},
\end{equation}$$

with $m_{\rm e}$ being the mass of the electron and $M$ denoting the total mass of the nucleus. Furthermore, $\text{R$_{\infty}$}$ is given by

$$\begin{equation}
\label{Eq:1.5}
R_\infty = \frac{m_{\rm e} e^4}{8 \varepsilon_{0}^{2}} h^3 c,
\end{equation}$$

where $e$ represents the elementary charge, $\varepsilon_{0}$ is the permittivity of free space, and $h$ stands for the Planck constant. The numerical value of $\text{R$_{\infty}$}$ is 109737.315685 cm$^{-1}$.\
The most straightforward way to calculate the oscillator strengths is using the following expression given by (cite: Kardashev1959):

$$\begin{equation}
\label{Eq:1.1}
\begin{aligned}
    f(\mathsf{n_{l}},\mathsf{n_{u}})=&\frac{2}{3}\mathsf{n_{u}}^{2}\frac{(4\mathsf{n_{u}}\mathsf{n_{l}})^{2\mathsf{n_{l}}+2}(\mathsf{n_{u}}-\mathsf{n_{l}})^{2\mathsf{n_{u}}-2\mathsf{n_{l}}-4}}{(\mathsf{n_{u}}+\mathsf{n_{l}})^{2\mathsf{n_{u}}+2\mathsf{n_{l}}+3}}\\
    &\times\binom{\mathsf{n_{u}}-1}{\mathsf{n_{u}}-\mathsf{n_{l}}-1}^{2}F^{2}(-\mathsf{n_{l}},-\mathsf{n_{l}},\mathsf{n_{u}}-\mathsf{n_{l}};x^{-1})\\
    &-\binom{\mathsf{n_{u}}}{\mathsf{n_{u}}-\mathsf{n_{l}}+1}^{2}x^{-2}F^{2}(-\mathsf{n_{l}}+1,-\mathsf{n_{l}}+1,\mathsf{n_{u}}-\mathsf{n_{l}}+2;x^{-1}),
\end{aligned}
\end{equation}$$

where the parenthesis $\binom{a}{b}$ is the binomial coefficient, $F(a,b,c;z)$ is a hyper-geometric function and $x$ is defined as

$$\begin{equation}
\label{Eq:1.2}
    x = -\frac{4 \mathsf{n_{u}} \mathsf{n_{l}}}{(\mathsf{n_{u}} - \mathsf{n_{l}})^{2}}.\\
\end{equation}$$

Thus, by substituting Equation ([\[Eq:1.1\]](#Eq:1.1)) into Equation ([\[Eq:1.3\]](#Eq:1.3)), the Einstein coefficient for spontaneous emission can be calculated. This approach requires evaluating the hyper-geometric function in Equation ([\[Eq:1.1\]](#Eq:1.1)), which is not included in Co$^{3}$RaL. Therefore, the Einstein coefficients for spontaneous emission are calculated separately, and Co$^{3}$RaL reads the values from a table.

### Computation of the radio recombination lines in non-LTE conditions

Non-LTE conditions occur when the populations of the energy levels deviate from the Boltzmann distribution. The computation of RRL emission can be done by following the procedure introduced by (cite: Menzel1937), in which departure coefficients $b_n$ relate the true population of a level, $N_n$, to the population under LTE conditions, $N_n^{\text{*}}$, by the relationship $N_n = b_n
N_n^{\text{*}}$. Under this consideration, the Boltzmann equation becomes:

$$\begin{equation}
\label{eq:25}
\frac{N_{u}}{N_{l}}=\frac{b_{u}}{b_{l}}\frac{g_{u}}{g_{l}}{\rm e}^{-h\nu_{ul}/kT},
\end{equation}$$

where $g_{i}$ (with $i=u,l$) are the statistical weights of the electronic levels, calculated as $g_{i}=\mathsf{n_{i}}^{2}$, and $b_{i}$ (with $i=u,l$) are the non-LTE departure coefficients mentioned above. The value of the $b_{i}$ factors is always $<$1, since the $A_{ul}$ coefficient for the lower state is larger and the atom is smaller so collisions are less effective, $b_{i}$$\rightarrow$1 for LTE conditions (cite: Wilson2009). Using the expression of Equation ([\[eq:25\]](#eq:25)) in the expression for the absorption emission coefficient (Equation ([\[eq:10\]](#eq:10))), the absorption emission coefficient under non-LTE conditions can be written as

$$\begin{equation}
\kappa_{\nu}^{\text{line}} = \frac{1}{8 \pi} \left( \frac{c\,\mathsf{n_{u}}}{\nu_{ul}} \right)^{2} \left( \frac{h^2}{2 \pi m_e k T_e} \right)^{3/2} {\rm e}^{h \nu_0/n_l^2 k T_e} b_{l} A_{ul} \left(1 - \frac{b_{u}}{b_{l}}{\rm e}^{-h \nu_{ul}/k T_e} \right) n_e n_i  V_{\nu}.
\end{equation}$$

Thus, the relation between the absorption coefficients under LTE conditions and non-LTE conditions can be written in the following way:

$$\begin{equation}
\label{eq:28}
\kappa_{\nu}^{\text{line}} = b_{l} \beta_{ul} \kappa_{\nu}^{\text{line,*}} 
\end{equation}$$

where the coefficient $\beta_{ul}$ is defined as

$$\begin{equation}
\beta_{ul}=\frac{1 - (b_{u}/b_{l}){\rm e}^{-h \nu_{ul}/k T_e}}{1 - {\rm e}^{-h \nu_{ul}/k T_e}}.
\end{equation}$$

In general, the relationship between the emission and absorption coefficients for the line can be written as follows (cite: Wilson2009):

$$\begin{equation}
\frac{j_{\nu}^{\text{line}}}{\kappa_{\nu}^{\text{line}}}=\frac{2 h \nu^3}{c^2}\left(\frac{1}{\frac{g_{u}}{g_{l}}\frac{N_{l}}{N_{u}} - 1}\right),
\end{equation}$$

and using Equation ([\[eq:25\]](#eq:25)) we arrive to the following expression:

$$\begin{equation}
\frac{j_{\nu}^{\text{line}}}{\kappa_{\nu}^{\text{line}}}=\frac{2 h \nu^3}{c^2}\cdot\frac{1}{(b_{l}/b_{u}){\rm e}^{h \nu_{ul}/k T_e} - 1}.
\end{equation}$$

Substituting Equation ([\[eq:28\]](#eq:28)) into this expression and using Kirchhoff’s law, $j_{\nu}^{\text{line,*}}$ $/\kappa_{\nu}^{\text{line,*}} = B_{\nu}(T)$, it is possible to write the relation between the emission coefficients under LTE conditions and non-LTE conditions in the following way:

$$\begin{equation}
\label{eq:32}
j_{\nu}^{\text{line}} = b_{u} j_{\nu}^{\text{line,*}}.
\end{equation}$$

The expression for the source function under non-LTE conditions is given by the following expression:

$$\begin{equation}
\mathcal{S}_{\nu} = \frac{j_{\nu}}{\kappa_{\nu}} = \frac{j_{\nu}^{\text{line}}+j_{\nu}^{\rm cont}}{\kappa_{\nu}^{\text{line}}+\kappa_{\nu}^{\text{cont}}}= \frac{b_{u} j_{\nu}^{\text{line,*}}+j_{\nu}^{\rm cont}}{b_{l} \beta_{ul} \kappa_{\nu}^{\text{line,*}}+\kappa_{\nu}^{\text{cont}}}, 
\end{equation}$$

which can be written as

$$\begin{equation}
\mathcal{S}_{\nu} = \eta_{\nu} B_{\nu}(T), 
\end{equation}$$

with

$$\begin{equation}
\eta_{\nu} = \frac{b_{u} \kappa_{\nu}^{\text{line,*}}+\kappa_{\nu}^{\text{cont}}}{b_{l} \beta_{ul} \kappa_{\nu}^{\text{line,*}}+\kappa_{\nu}^{\text{cont}}}.
\end{equation}$$

Thus, the radiative transfer equation (Equation ([\[eq:4\]](#eq:4))) for non-LTE conditions becomes

$$\begin{equation}
\label{eq:36}
I_\nu(\tau_{\nu}) = I_\nu(0){\rm e}^{-\tau_{\nu}} + \eta_{\nu} B_{\nu}(T)(1-{\rm e}^{-\tau_{\nu}}).\\
\end{equation}$$

![](Coefficients_Storey_Hummer_case_b_n40.pdf)

The non-LTE departure coefficients, $b_{i}$, are obtained from the tables provided by (cite: sto95) for Case B. These tables include values of non-LTE departure coefficients for a range of temperatures from 500 to 30,000 K and densities from 10$^{2}$ to 10$^{14}$ cm$^{-3}$. Figure [18](#fig:4) shows the values for $\mathsf{n_{u}}=40$. As can be seen from Figure [18](#fig:4), the values are close to 1 for high electron densities and temperatures, and they have lower values for low densities and temperatures.\
To obtain the value of the non-LTE departure coefficients for any value of density and temperature, Co$^{3}$RaL performs a two-dimensional linear interpolation. First, it interpolates the values between densities at the same temperature, and then it interpolates the values between two temperatures corresponding to the electron density in question. Figure [19](#fig:5) shows a diagram of the procedure to find the value of the non-LTE departure coefficient for any arbitrary electron density and temperature.\
Various interpolation methods were tested to calculate the non-LTE departure coefficients for different values of density and temperature. However, these methods did not result in significant differences in the outcomes. Therefore, the previously described method was chosen for its simplicity and efficiency.\

![](b_coefficient_diagram.pdf)

## Co$^{3}$RaL general description and modeling approach

The Co$^{3}$RaL code can consider any given 3D geometry for the ionized region. The geometry can be analytically described in Cartesian, spherical or cylindrical coordinates or, alternatively, it can be read from an input file where the coordinates of the model cells are provided. In addition to the geometry, the other major inputs for the model are: the electron density ($n_{\rm e}$), the electron temperature ($T_{\rm e}$), and the velocity field ($\overrightarrow{v}$). For simplicity, $n_{\rm e}$ and $T_{\rm e}$ are assumed to follow a power law of the type $\propto$$r^{\beta}$, where $r$ is the radial distance to the central source and $\beta$ is a real number positive or negative. Non-uniform distributions are accommodated by employing different laws, as necessary, across distinct layers within the ionized wind.

The same approach can be applied to describe the velocity field, also allowing for various combinations of radial, axial, equatorial, and shear expansion, with equatorial rotation. The velocity modulus can be constant or increase/decrease as any given function of $r$. Latitude- and longitude-dependent variations can be incorporated for any of the input physical parameters.

In addition to the gas macroscopic motions, thermal broadening as well as electron impact (pressure) broadening are included in the line profile function. In the present model of M 2-9 (Sect. [6.1](#model)), turbulence velocity dispersion is not considered as an additional form of line broadening since it is expected to be very small ($\sigma_{\rm
  turb}$$<$2-3 km s$^{-1}$) in the envelopes of AGB and post-AGB objects (cite: sch04; buj05; dec10) and, thus, negligible compared to other broadening terms.

# Comparison of Co$^{3}$RaL with MORELI

In the pilot single-dish study of the emerging ionized regions of pPNe by CSC17, the free-free continuum and mRRLs emission was modelled using the radiative transfer code MORELI (cite: bae13). MORELI is a code previously employed in several studies of ionized regions, including works by (cite: bae14; san19; mar23). Here, we present a comparative analysis between the predictions generated by our code, Co$^{3}$RaL, and those produced by MORELI, utilizing identical input models. This comparison serves as a mutual benchmarking exercise of both codes. We separately run LTE and non-LTE models for M 2-9 and CRL 618, respectively, pPNe that are both modelled by CSC17 using MORELI.

The two input models employed correspond to the configurations described for M 2-9 and CRL 618 in Table 4 of CSC17, depicting in both cases a cylindrical outflow radially expanding, with the detailed geometry, physical structure, and kinematics of the cylindrical outflow being different for, and adapted to, each source. We refer to these preliminary models based on single-dish data as CSC17’s models. As in CSC17, Co$^{3}$RaL was run under the LTE approximation for M 2-9 and non-LTE for CRL 618.

As shown in Fig. [20](#f:coral_moreli), the predictions for the free-free continuum flux at (sub)mm-to-cm wavelengths, along with the mRRLs H30$\alpha$ and H39$\alpha$, for Co$^{3}$RaL and MORELI exhibit a high level of consistency. The continuum fluxes predicted by MORELI and Co$^{3}$RaL are indeed almost identical, with differences falling below 1%-2% precision for both objects.

Under LTE (M 2-9), the mRRLs line profiles are also identical. For non-LTE (CRL 618), Co$^{3}$RaL predicts slightly (10%–15%) higher peak intensities for both lines, resulting in a small difference in the best-fit electron temperature of $T_{\rm e}$$^{\rm CoRaL}$–$T_{\rm e}$$^{\rm MORELI}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$700 K ($<$4%) when derived using the two codes on the same data set, while keeping the rest of CSC17’s model parameters the same. Without access to the original MORELI source code, it is impossible to determine the exact reason for this small discrepancy. The discrepancy could be related to the various approximations and interpolations made when estimating the $b_n$ departure coefficients (available in the literature only for a discrete grid of electron density and temperature pairs), pressure broadening coefficients, integration of the Voigt profile, etc (see Appendix [10](#ap-co3ral) for details).

![image](sed_m29_co3ral_moreli.pdf) ![image](H30alpha_co3ral_moreli.pdf) ![image](H39alpha_co3ral_moreli.pdf)\
![image](sed_crl618_co3ral_moreli.pdf) ![image](H30alpha_co3ral_moreli_c618.pdf) ![image](H39alpha_co3ral_moreli_c618.pdf)

# Comparison of CSC17’s model for M 2-9 with new ALMA maps from this work

In Fig. [21](#f:csc17), we show synthetic ALMA-like cubes representing emission from 93 GHz free-free continuum and H30$\alpha$ and H39$\alpha$ lines, based on the model of M 2-9 derived from single-dish observations by CSC17. While this model accurately reproduces the free-free (mm-to-cm) continuum flux and the single-dish line profiles, the corresponding synthetic ALMA images reveal notable differences from the actual ALMA data (Figs. [1](#f-cont) and [4](#f-pv)). These differences suggest the presence of a collimated wind or jet that is narrower than initially assumed and that exhibits a certain C-shaped curvature as well as a significant velocity gradient along its axis. In Section [6.1](#model), we introduce an updated model that replicates these and other features observed in our ALMA datasets, which has a resolution of a few tens of milliarcsecond.

![image](M2-9_continuum_imaging_95_35GHz_M2-9_SC_17-NICE.pdf) ![image](M2-9_spectral_line_imaging_H30ALPHA_M2-9_SC_17-vyx-MODEL.pdf) ![image](M2-9_spectral_line_imaging_H39ALPHA_M2-9_SC_17-vyx-MODEL.pdf)

# Model caveats and final modeling remarks

It is important to emphasize that the relatively simple model presented in Sect. [6.1](#model) is probably not unique and that more intricate geometries, kinematics, and density and temperature profiles (e.g. latitude-dependent) cannot be dismissed as possibilities. Although a comprehensive parameter space study has not been performed and is beyond the scope of this paper, we are confident that the bulk features deduced from the model– such as the presence of dense, high-velocity shell-like regions within a narrow-waisted bipolar (horn-like) wind– are robust and necessary to reproduce the main features inferred directly from the data. The model’s primary role is to reinforce these features and provide a more precise characterization of the physical properties in the wind. Below, we describe the uncertainties associated with some parameters, but we stress that these do not affect our overall conclusions, as we have been careful not to overinterpret minor details. Instead, we focused on bulk parameters that control the main features, whose effects are clearly distinguishable in the synthetic maps. While some minor parameters may exhibit hidden interdependencies, their impact on the overall scientific conclusions derived in our study is very small.

Uncertainties in the absolute densities and temperatures deduced are also moderate, within a factor $\sim$2–3 and 15–20%, respectively. The position and width of the HVSs are accurate down to $\sim$2–3 au. The radius of the wind at its base (waist), $R_{\rm eq}$$\sim$7–8 au, is relatively well constrained by the extent of the continuum maps at the center. However, the size of the nucleus, its true geometry, and accurate density distribution remain unknown. For simplicity, we assume a spherical region with an intermediate value for the radius of 4 au and an average density of a few$\times 10^{\rm 8}$ $\,$cm$^{\rm -3}$. However, larger[^11] (or smaller) dimensions together with smaller (or larger) average density are also possible. The systemic velocity of the source is probably in the range 75–78 km s$^{-1}$.

One shortcoming of our model is its failure to predict the asymmetry in the H30$\alpha$ line profile, particularly noticeable in the axial position-velocity diagram, where the blue-shifted emission wing from the south lobe is moderately more intense than the red-shifted one from the north lobe. This asymmetry, also observed in the 1mm-continuum map, may be partially attributed to an intrinsic asymmetry in the ionized wind and/or to partial absorption of the free-free emission from the base of the northern lobe that is behind the front side of the circumbinary dust disk (see Sect. [6.2](#disk_co)). These effects are not considered in our model.

Furthermore, the model predicts an H39$\alpha$ line that is too wide and has a slightly blueshifted centroid compared to the observations. This issue results from a combination of pressure broadening, opacity, and non-LTE effects, which could only be alleviated by reducing the density below 1$\times 10^{\rm 7}$ $\,$cm$^{\rm -3}$ in all regions, including the central ones (nucleus and inner wind). However, we have not found any satisfactory models with such low densities, as these would require a much larger emitting volume, incompatible with the extent of the ionized wind observed in the maps.

It is also crucial to recognize that the accuracy of the ultimate (best-fit) model is influenced by the chosen values of critical parameters that remain challenging to precisely quantify, such as departure coefficients or approximated expressions for pressure broadening, Gaunt factors, etc.

For example, departure coefficients $b_n$ indeed vary depending on the radiation field for a specific assumed geometry and physical structure, which may differ from those presumed in the models of (cite: sto95) used in this work.

Furthermore, pressure broadening expressions used in this work, commonly employed in analytical approaches (cite: bae13), posed modeling challenges at high densities ($\raisebox{-.4ex}{$\stackrel{>}{\scriptstyle \sim}$}$10$^8$ cm$^{-3}$), where the line wings, notably those of H39$\alpha$[^12], significantly exceed observations in central regions (regions I and II) of M 2-9. Throughout the modeling process, efforts have been made to address this discrepancy by reducing electron density (to alleviate the effect) and enlarging the dimensions of the emitting region (to maintain a consistent free-free continuum flux). This was done to simultaneously reproduce narrower central wings in the H39$\alpha$ line and the observed dimensions of the emitting region. However, there is a possibility of inaccuracies in the pressure broadening expressions, which might have led to uncertainties in the density in these central regions.

[^1]: `https://casa.nrao.edu/`

[^2]: ` http://www.iram.fr/IRAMFR/GILDAS`.

[^3]: We used a value of 0.5 for the threshold of the robust weighting in MAPPING.

[^4]: Absolute astrometric uncertainties are of 0$.\!\!^{\prime\prime}$003.

[^5]: The spectral index derived by us, 0.89$\pm$0.06, and derived by (cite: dlF22), 0.85$\pm$0.05, are consistent with each other within the uncertainties and considering that these authors only use radio-continuum data.

[^6]: MORELI is the code used in the analysis by CSC17 (cite: bae13).

[^7]: As discussed by CSC17 a temperature stratification has a rather limited effect on the free-free continuum flux.

[^8]: For a proper line-to-continuum comparison, we use the continuum maps of the same spectral window where the line was observed cleaned and restored exactly in the same manner and, thus, imaged with the same beam.

[^9]: ` http://var.sron.nl/radex/radex.php`

[^10]: The specific part of this intricate structure that becomes ionized depends on its exposure to the central ionizing source, which may be selectively obstructed in specific directions.

[^11]: Up to a maximum value of $R_{\rm eq}$$\sim$7–8 au

[^12]: Pressure broadening, i.e. broadening of the energy levels due to collisions with electrons, increases as a power-law of the level principal quantum number $n$.

</paper>

Write the methods card for this paper.