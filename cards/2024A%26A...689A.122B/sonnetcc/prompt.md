# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.122B\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...689A.122B",
 "title": "The properties and kinematics of HCN emission across the closest starburst galaxy NGC 253 observed with ALMA",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Bešlić, I.",
 "n_authors": 24,
 "arxiv_id": "2403.13751",
 "doi": "10.1051/0004-6361/202347568",
 "alma_projects_linked_by_archive": [
  "2018.1.01321.S",
  "2019.2.00236.S"
 ]
}
```

Paper text:
<paper>
# The properties and kinematics of HCN emission across the closest starburst galaxy NGC 253 observed with ALMA

Investigating molecular gas tracers, such as hydrogen cyanide (HCN), to probe higher densities than CO emission across nearby galaxies remains a challenge. This is due to the large observing times required to detect HCN at high sensitivity and spatial resolution. Although $\sim$kpc scale of HCN maps are available for tens of galaxies, higher-resolution maps are still scarce. We aim to study the properties of molecular gas, the contrast in intensity between two tracers that probe different density regimes (the HCN(1–0)/CO(2–1)  ratio), and their kinematics across NGC 253, one of the closest starburst galaxies. With its advanced capabilities, the Atacama Large Millimeter/submillimeter Array (ALMA) can map these features at high resolution across large field of view and uncover the nature of such dense gas in extragalactic systems.

We present new ALMA Atacama Compact Array and Total Power (ACA+TP) observations of the HCN emission across NGC 253. The observations cover the inner 8.6$'$ of the galaxy disk at a spatial resolution of 300 pc. Our study examines the distribution and kinematics of the HCN-traced gas and its relationship with the bulk molecular gas traced by CO(2–1). We analyze the integrated intensity and mean velocity of HCN and CO along each line of sight. We also use the SCOUSE software to perform spectral decomposition, which considers each velocity component separately.

We find that the denser molecular gas traced by HCN piles up in a ring-like structure at a radius of 2 kpc. The HCN emission is enhanced by 2 orders of magnitude in the central 2 kpc regions, beyond which its intensity decreases with increasing galactocentric distance. The number of components in the HCN spectra shows a robust environmental dependence, with multiple velocity features across the center and bar. We have identified an increase in the HCN/CO ratio in these regions, which corresponds to a velocity component that is likely associated with a molecular outflow. We have also discovered that the ratio between the total infrared luminosity and dense gas mass, which is an indicator of the star formation efficiency of dense gas, is anticorrelated with the molecular gas surface density up to approximately 200 M$_{\odot}$ pc$^{-2}$. However, beyond this point, the ratio starts to increase.

We argue that using information about spectroscopic features of molecular emission is an important aspect of understanding molecular properties in galaxies.

# Introduction

The densest structures of molecular clouds are found to be sites of star formation across galaxies (cite: gao_2004a; lada_2012; longmore_2014). However, since the primary constituent of molecular gas, H$_2$ does not probe the coldest, densest parts of these clouds, other molecular lines are needed to observe star-forming gas and be used to constrain various properties. In the past, researchers have primarily used CO, the second most abundant molecule in the universe, to observe molecular clouds (cite: bolatto_2013b). CO emits relatively bright signals within the millimeter and (sub)millimeter regime, and its abundance scales with H$_2$. The assumption that the CO emission traces the overall molecular gas content of the interstellar medium (ISM) is commonly used within the literature (cite: bigiel_2008; leroy_2008; tacconi_2010; schruba_2011; cormier_2014; genzel_2015; saintonge_2017).

In most cases, the low-J CO lines can be used to estimate the total H$_2$ mass, although they might not be reliable bulk tracers in extreme environments with, e.g., high cosmic-ray ionization rates (cite: bisbas_2015) or with intense UV radiation and/or low-metallicity (cite: pak_1998).

CO is a good tracer of the cloud-scale surface density (cite: sun_2018), but it does not reveal information about the star-forming part of molecular clouds. Therefore, to probe such dense regions ($n>10^3\,\mathrm{cm^{-3}}$, $200\,$M$_{\odot}$pc$^{-2}$), astronomers observe molecular lines with high critical densities (cite: shirley_2015), such as those of HCN, HCO$^+$, N$_2$H$^+$, defined in this paper as "dense gas tracers". However, observing this gas at extragalactic distances is challenging; many preferred molecular lines commonly used in Galactic studies (cite: forbrich_2014; pety_2017; kauffmann_2017), such as N$_2$H$^+$, can only be easily detected towards the centers of bright, nearby galaxies NGC 253 (cite: martin_2021) and NGC 6946 (cite: eibensteiner_2022; jimenez-donaire_2023).

The $J=1\xrightarrow{}0$ transition of the hydrogen cyanide, HCN, is one of the brightest high-critical density molecular lines commonly studied within the extragalactic literature (cite: gao_2004a; usero_2015; gallagher_2018a; jimenez19; beslic_2021; sanchez-garcia_2022). The comparison between low and high-critical density lines, such as CO(1–0) and HCN(1–0), yields an approximate gauge of the intensity contrast between two tracers probing different density regimes, as the latter requires significantly higher densities for collisional excitation compared to the low-J CO lines (cite: shirley_2015). This contrast offers the best currently available observational constraint on changes in the underlying density distribution in other galaxies (cite: leroy_2017a).

From the observational point of view, HCN surveys in extragalactic systems found a tight and linear correlation between HCN luminosity and star formation rate (cite: gao_2004a; jimenez19). This correlation is approximately linear in logarithmic space, spanning more than ten orders of magnitude, and covers a wide range of physical scales: from dense clumps and cores (a few pc - e.g., (cite: wu_2010) within the Milky Way, to galaxy disks and galaxy centers (cite: gao_2004a; gracia_carpio_2008). Although it has been argued that the linear relation between HCN and SFR suggests that gas above a specific density threshold starts forming stars (cite: lada_2012), systemic variations in the IR/HCN ratio imply that not all dense gas is equally efficient. For example, the Central Molecular Zone (CMZ), known to be the inner 500 pc region of our Galaxy, shows an order of magnitude lower SFR than those predicted from measurements of dense molecular gas (cite: longmore_2013a; henshaw_2022), implying a possibility of the non-universality of the star formation efficiency (cite: maclow_2004; padoan_2011; federrath_2012; kruijssen_2014a; semenov_2015). This environmental impact on the dense gas ability for star formation has also been observed across other galaxies. While most dense gas mass is found in centers of galaxies, but this gas is less efficient at star formation than the gas in the rest of the disk (cite: gallagher_2018a; jimenez19). Observed variations in IR/HCN could be caused by non-steady effects dominant at small spatial scales such as stellar feedback and galactic shear, which become averaged out on larger scales.

In order to fully understand star formation process, it is important to connect what we learn from studying extragalactic sources with studies of individual star-forming regions within our own Milky Way. To do this, we need to observe molecular clouds in extragalactic samples at a high sensitivity and on small spatial scales, while also covering a broad range of different environments and physical conditions. This is a crucial step towards connecting studies of the Milky Way, where we can examine the substructure of individual molecular clouds (cite: pety_2017), with studies of more distant galaxies that contain vastly different environments, such as starburst galaxies (cite: garcia_burillo_2012). To achieve this, it is essential to observe nearby galaxies that span the range of scales needed to benchmark our understanding of local clouds and high-z galaxies. Due to their proximity, we can map dense molecular gas content across nearby galaxies at high spatial resolution and sensitivity. Moreover, the high molecular surface brightness of these sources, known as $\Sigma_\mathrm{mol}$, can provide a sensitive mapping of the HCN emission that we can now observe using advanced observing facilities such as ALMA. Recent studies of HCN at higher resolutions, approaching molecular cloud-scales of around 100 pc, have been focused mainly on the brightest regions of nearby galaxies, such as in M 51 (cite: querejeta_2019), a larger part of the disk of NGC 3627 (cite: beslic_2021), the center of NGC 6946 (cite: eibensteiner_2022), and the inner ring of NGC 1068 (cite: sanchez-garcia_2022).

In this paper, we answer some of the science questions related to high-critical density molecular emission, such as the following:

1.  How is dense molecular gas distributed across the disk of NGC 253 (Section [3](#sec:line_of_sight))?

2.  What is the kinematics of the HCN-tracing gas, and how does it compare with the CO emission (Section [4](#sec:scouse))?

3.  What is the role of dense gas in star formation across different environments found in NGC 253 (Section [5](#sec:star_formation))?

To address these questions, we use ALMA observations of the closest starburst galaxy outside the Local Group, the Sculptor galaxy, NGC 253. The main properties of this galaxy are listed in Table [1](#tab:NGC0253_prop). NGC 253 (see its composite image in Figure [1](#fig:ngc253)) is the highly inclined, starburst galaxy (cite: rieke_1980) located in the southern hemisphere. Due to its proximity (cite: anand_2020), NGC 253 represents an ideal target for high-resolution studies to understand the nature of its kpc nuclear region (cite: bolatto_2013; leroy_2015; walter_2017; holdship_2021) of which the center appears to be undergoing an intense phase of active star formation. The star formation rate within the center is SFR=2 M$_\mathrm{\odot}$yr$^{-1}$ (cite: leroy_2015), which is 50 $\%$ of the SFR found in the whole disk of this galaxy (cite: sanders_2003).

The central one kpc of NGC 253 shows rich molecular emission (see our detected molecular lines in the bottom panel of Figure [1](#fig:ngc253)), demonstrated in (cite: martin_2006), (cite: aladro_2011), and (cite: Meier_2015), who detected 50 molecular species at 3 mm wavelength (e.g. C$_2$H$_5$OH, HOCN, HC$_3$H). In addition, ALMA Comprehensive High-resolution Extragalactic Molecular Inventory (ALCHEMI) mapped a continuous frequency range from (sub)mm to mm wavelengths in the nuclear region of NGC 253 (cite: martin_2021). NGC 253 has a plethora of ancillary data covering a variety of gas phases, from hot (cite: lopez_2022), atomic (cite: heckman_2000), molecular (cite: houghton_1997; mauersberger_1996; paglione_2004), and the most recent ACA observations of CO(2–1) which we use in this work (cite: faesi_2023), to ionized gas (cite: arnaboldi_1995).

| Property | Value |
|:--:|:--:|
| Name | NGC 0253 (Sculptor galaxy) |
| Hubble type $^{(a)}$ | SABb |
| Center RA (J2000) | 00h47m33s |
| Center DEC (J2000) | -25d17m19s |
| Inclination, $i$ $\mathrm{[^{\circ}]}$ $^{(a)}$ | 76$\pm$6 |
| Position angle, $PA$ $\mathrm{[^{\circ}]}$ $^{(a)}$ | 52 |
| Distance, $D$ $\mathrm{[Mpc]}$ $^{(b)}$ | 3.7 |
| $r_{25}$ \[$'$\] $^{(b,c)}$ | 5.12 |
| $V_\mathrm{sys, hel}$ \[km s$^{-1}$\] $^{(d)}$ | 258 |
| SFR \[M$_{\odot}$ yr$^{-1}$\] $^{(e)}$ | 4.2 |
| log$_{10}(M_*$) \[$\mathrm{M}_\odot$\] $^{(f)}$ | 10.5 |

: Main properties of NGC 253.

\(a\) (cite: hlavacek-larrondo_2011).\
(b) Distance from (cite: anand_2020).\
(c) Radius of the $B$-band 25th magnitude isophote.\
(d) Systemic velocity from (cite: casasola_2011).\
(e) Star formation rate calculated from the IR luminosity (cite: sanders_2003).\
(f) Integrated stellar mass based on 3.6 μm emission, taken from the PHANGS-ALMA survey paper (cite: leroy_2021b).\

![image](Figures_v2/Ngc253_1.png) ![image](Figures_v2/Ngc253_2.png)

Although NGC 253 has been well-studied over the last few decades, most investigations have focused on its inner 1-2 kpc nuclear region. The molecular gas outside the galaxy center needs to be better understood, particularly the properties of its dense phase and its kinematics on larger scales in a wide range of disk environments.

In this paper, we present new ACA observations across the disk of the NGC 253. These data have a spatial resolution of 300 pc, covering a large part of the disk of this galaxy ($8\times3$$'$$^2$) and probe different dynamical features in this galaxy. The paper is structured as follows. Section [2](#sec:obs) describes observations, data reduction, additional data sets used throughout this work, and present moment maps of the HCN and CO(2–1). Next, we present our results: Section [3](#sec:line_of_sight) describes the distribution of the line of sight HCN emission and the measured HCN/CO(2–1) ratio. Section [4](#sec:scouse) presents the decomposed line of sight HCN emission and measured properties of such decomposed emission and describes results on measured velocity dispersion. Moreover, we answer Question 3 in Section [5](#sec:star_formation). Our findings are discussed in Section [6](#sec:discussion). Finally, we summarize and outline our most important results in Section [7](#sec:summary).

# Observations and data reduction

![](Figures_v2/Moment_maps.pdf)

## ALMA+ACA observations

The observations (project ID: 2019.2.00236.S) of NGC 253 presented in this paper are part of the ALMA Cycle 7 and were obtained in December 2019 and January 2020. We observe molecular line emission using the Atacama Compact Array (7m - ACA), which included the Total Power (TP) array in Band 3 (84 – 116 GHz), covering several ”typical” extragalactic tracers of high-density gas, shown on the bottom panel in Figure [1](#fig:ngc253). The total observing time is 22.9 and 44.1 hours for the 7 meter array and the TP antennas, respectively. The observed field of view contains 25 7m pointings with the primary beam full-width half maximum (FWHM) of 57.6 $^{\prime\prime}$, that covers a $114$$^{\prime\prime}$$\times516$$^{\prime\prime}$($\sim$2$\times$9 kpc$^2$) region of the inner disk of NGC 253 (see Figure [1](#fig:ngc253)). The beam size is $21.40$$^{\prime\prime}$$\times10.36\,$$^{\prime\prime}$, and the beam position angle is 83.5 degrees. From our ancillary CO(2–1)  observations (Section [2.3](#sec:smol)) and SFR images (Section [2.4](#sec:ssfr)), we find that the region mapped within the ACA comprises 90$\%$ of the total molecular mass of NGC 253 and 85$\%$ of its total SFR. Thus, our observations cover the brightest regions in molecular gas and the most star-forming parts in NGC 253.

Our interferometric observations are sensitive to the emission from angular scales of $\sim$14 $^{\prime\prime}$($\sim$240 pc) to the largest angular scale obtained by the TP of $\sim$100 $^{\prime\prime}$($\sim$1.7 kpc). The obtained sensitivity is $\sim$2.5 mK (7.6 mJy/beam) at the angular and spectral resolution of 22 $^{\prime\prime}$and 10 km s$^{-1}$. The spectral setup consisted of 4 spectral windows with $\sim1.8$ GHz width and 0.4 MHz resolution laid out as at the bottom of Figure [1](#fig:ngc253). We detected 13 molecular lines, but here, we focus on the HCN(1–0) line covered by spectral window 2, labeled as spw2 on Figure [1](#fig:ngc253).

The raw data calibration is done in Common Astronomy Software Applications (CASA - (cite: mcmullin_2007)), version 6.5, and the imaging and post-processing, including short-spacing correction using the PHANGS-ALMA processing pipeline (cite: leroy_2021a). Firstly, we flag all the emission lines within each band to calculate and subtract the continuum emission. The 7m data was imaged using CASA’s standard TCLEAN procedure. We use the CO(2–1)-based clean mask (cite: leroy_2021a; leroy_2021b) as the initial clean mask for our imaging, which is then combined with the single-scale clean during the imaging. The HCN 7m flux within the cleaning mask is 99$\%$ of the total flux within the full image.

The single-dish data are also processed using the PHANGS-ALMA total power processing pipeline (cite: herrera_2020), included in the PHANGS-ALMA pipeline (cite: leroy_2021a). In the final data reduction step, we combine 7m observations with TP for the missing short-scale emission using the standard CASA task *feather*. The total flux from the interferometric data is $70\%$ of the total flux measured from the single-dish data. The final data cube is additionally primary beam corrected and convolved to have a circular beam size of 22 $^{\prime\prime}$($\sim$370 pc) and channel width of 10 $\, \ensuremath{\mathrm{km\,s^{-1}}}$.

In addition, we compute the dense gas mass, $M_\mathrm{dense}$, assuming a constant $X_\mathrm{HCN} = 10\,[\mathrm{M_{\odot}\,(\mathrm{K\,km\,s^{-1}\,pc^2})^{-1}] }$ conversion factor (cite: gao_2004a):

$$\begin{equation}
    M_\mathrm{dense} [\mathrm{M_{\odot}}] = X_\mathrm{HCN}\cdot L_\mathrm{HCN} \cdot \cos{i},
\label{eq:mdense}
\end{equation}$$

where $i$ is the galaxy inclination reported in Table [1](#tab:NGC0253_prop).

## Environmental masks

To separate regions with different characteristics in NGC 253, we use environmental masks defined for this galaxy based on infrared data (cite: querejeta_2021). They have four regions: the disk, ring, bar, and center. Additionally, NGC 253 has two spiral arm features, visible in optical data (cite: pence_1980) and constrained from the 3.6 and 4.5 μm observations obtained by the Spitzer telescope, as part of the S$^4$G survey (cite: munoz-mateos_2015; herrera-endoqui_2015). Therefore, we also define a spiral arm mask in this work as follows. We use the unsharp-masked near-infrared Herschel PACS $70$μm data to locate spiral features, and then we fit those in polar ($\rho,\theta$) space as linear functions. The width of such constructed spiral arms is defined manually in the SAO-NASA ds9 software (cite: ds9). Finally, we add these spiral arm regions to the existing environmental mask, shown in Figure [1](#fig:ngc253). We distinguish five environments in NGC 253: the nuclear region lies within the inner $\sim$0.5 kpc region, and the bar feature is located in the inner two  kpc region. The ring is at radii between 2 and 5 kpc, and the dust lanes are at $r_\mathrm{gal}=5$ kpc. All remaining pixels not assigned to any of these environments belong to the disk.

## ALMA-CO(2–1) observations from PHANGS

In this work, we use ancillary ALMA ACA+TP CO(2–1) observations (PI: C. Faesi, 2018.1.01321.S), included in the PHANGS-ALMA survey (cite: leroy_2021b; faesi_2023). The angular resolution of these data is 8 $^{\prime\prime}$, and the channel width is 2.5 km s$^{-1}$. In the final step, we convolve the CO(2–1) data cube to match the working angular and spectral resolution of 22 $^{\prime\prime}$and 10 $\, \ensuremath{\mathrm{km\,s^{-1}}}$ and regrid to a common pixel scale. We compute the molecular surface density using the following equation:

$$\begin{equation}
  \Sigma_\mathrm{mol} [\mathrm{M_{\odot} pc^{-2} }] = \alpha_\mathrm{CO}\cdot \dfrac{I_\mathrm{CO(2-1)}}{R_\mathrm{21}} \cdot \cos{i} = \alpha_\mathrm{CO}\cdot \dfrac{I_\mathrm{CO(2-1)}}{\Sigma_{\mathrm{SFR}}^{0.15}} \cdot \cos{i} ,
\label{eq:sigma_mol}
\end{equation}$$

where $\alpha_\mathrm{CO}$ is the metallicity-dependent conversion factor taken from (cite: sun_2020b), $I_\mathrm{CO(2-1)}$ is the CO(2–1)  integrated intensity, $R_{21}$ is the CO(2–1)/CO(1–0)  line ratio (cite: sandstrom_2013; denbrok_2021; yajima_2021; leroy_2022), and $i$ is the same as in Equation [\[eq:mdense\]](#eq:mdense). In this work, we use the scaling relation: $R_{21}\propto \Sigma_\mathrm{SFR}^{0.15}$ (cite: sun_2023). The $\alpha_\mathrm{CO}$ has a range from 4.2 (at the centre) to 20 $[$M$_{\odot}/(\mathrm{K\,km\,s^{-1}\,pc^2})]$ (at the outskirts). The validity of the $\alpha_\mathrm{CO}$ factor, depends on the mass scales probed. For masses greater than $10^5$ M$_{\odot}$, the statistical assumptions underlying the $\alpha_\mathrm{CO}$ factor remain valid (cite: dickman_1986), which is achieved in our work. We present the $\Sigma_\mathrm{mol}$ map in Figure [15](#fig:smol_map) in Appendix [8](#sec:app-smol).

## Star formation rate

To estimate the star formation rate surface density ($\Sigma_\mathrm{SFR}$), we use a combination of IR Herschel data from the KINGFISH (Key Insights on Nearby Galaxies: a Far-Infrared Survey with Herschel) survey (cite: kennicutt_2011). To compare our results with recent similar studies (cite: jimenez19), we choose to calculate $\Sigma_\mathrm{SFR}$ using Herschel bands at $\lambda=$70, 160, and 250 microns. First, we convolve our Herschel maps to a final resolution of 22 $^{\prime\prime}$  using the kernels defined in (cite: aniano_2011) and match the coordinate grid with the final HCN data image. We calculate the total infrared surface density ($\Sigma_\mathrm{TIR}$) following the prescription from (cite: galametz_2013):

$$\begin{equation}
    \Sigma_\mathrm{TIR} [\mathrm{W\,kpc^{-2}}] = \sum_{j} c_{j}\cdot \Sigma_{j} [\mathrm{W\,kpc^{-2}}],
\label{eq:tir}
\end{equation}$$ where $c_{j}$ is the coefficient and $\Sigma_{j}$ is the surface density at a band j, listed in Table [2](#tab:coeff_tir) in Appendix [9](#sec:app-sfr). We then calculate $\Sigma_\mathrm{SFR}$ from $\Sigma_\mathrm{TIR}$ and correct for the galaxy inclination $i$ (cite: galametz_2013): $$\begin{equation}
    \Sigma_\mathrm{SFR} [\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}] = 1.48\cdot10^{-10}\, \Sigma_\mathrm{TIR} [\mathrm{L_{\odot}\,kpc^{-2}}] \cos{i}.
\end{equation}$$

We show the $\Sigma_\mathrm{SFR}$ map in Figure [16](#fig:sfr_map) in Appendix [9](#sec:app-sfr).

## Moment maps

We show moment maps, i.e., the line of sight integrated intensity (moment 0) map, centroid velocity map (moment 1), and velocity dispersion map (moment 2) in Figure [2](#fig:moment_maps), at 22 $^{\prime\prime}$resolution (370 pc) for HCN(1–0) (top row) and CO(2–1) data (bottom row).

The integrated intensity is computed as a sum of the emission along each line of sight (i.e., we integrate along the velocity axis). We first create a CO(2–1) based mask. This mask is produced by selecting all voxels with a signal-to-noise ratio higher than 4 and then expanding it to include all contiguous voxels with signal-to-noise $>2\sigma$ level. Next, we apply this mask to the HCN and CO(2–1) data cubes. The moment maps are derived from the masked data cubes using the `python` package SpectralCube (cite: spectral_cube).

The HCN emission shows a clumpy structure and compact emission, prominent in the center of the galaxy and also concentrated along the ring and the bar. There are spots of bright HCN emission located at the contact points of the bar, dust lanes, and ring, which we also see in the $\Sigma_\mathrm{SFR}$ (Figure [16](#fig:sfr_map) in Appendix [9](#sec:app-sfr)). These bright spots of HCN emission are expected to be found in the regions where the bar and ring intersect, as these are interfaces where gas orbits converge (cite: kenney_1994; beuther_2017). Moreover, we see CO(2–1) bright spots co-spatial with those seen in HCN.

The moment one map is the intensity-weighted mean velocity map. We show these in the middle column of Figure [2](#fig:moment_maps) for both HCN and CO(2–1). The velocity map is corrected for the systemic velocity (Table [1](#tab:NGC0253_prop)). The outskirts of the map (left and right side) show the highest velocity difference, i.e., along the major axis (around $-230$ and $+230$ $\, \ensuremath{\mathrm{km\,s^{-1}}}$ on the eastern and western parts, respectively). The northeastern side of the galaxy is blue-shifted. HCN and CO(2–1) velocities look mainly consistent across the disk of NGC 253 (we discuss this in detail in Section [4](#sec:scouse)). We expect their consistency from the assumption that HCN traces denser gas than the CO, thus probing denser molecular substructures traced by the CO emission. We note a few regions within which we observe discrepancy in centroid velocities of HCN and CO(2–1)  and further discuss when considering spectral complexity along the line of sight in Section [4](#sec:scouse).

The second moment map represents the velocity dispersion of the observed emission. The broadest line profiles are observed towards the center of this galaxy in both HCN and CO emission. Apart from the center, we also note other regions with relatively large velocity dispersion ($\sim50\,$km/s) in the HCN and CO(2–1) emission, such as the bar and partially the ring. CO(2–1) shows higher velocity dispersion than the HCN, and this difference becomes more notable at the outer parts of our map.

# Line of sight HCN emission

## Radial distribution of the line of sight HCN intensity

![](Figures_v2/hcn_radial_profile.png)

![](Figures_v2/hcn-co21.png)

To investigate the HCN emission across NGC 253, we resample the HCN map on a hexagonal grid where adjacent pixels are half-beam spaced. We show the radial distribution of the HCN integrated intensity in Figure [3](#fig:hcn_radial_profile). We detect significant HCN emission up to $\sim6.5$ kpc. The high inclination of this galaxy causes large deprojected distances from the center along the minor axis (i.e.,  the minor axis effect). After inspection of the deprojected distances along the major axis, where we do not expect to encounter such impact, we conclude that the farthest data point from the center of the map has a deprojected distance of 5.3 kpc, assuming an axisymmetric distribution. Consequently, data points at radii higher than the 5.3 kpc should be taken cautiously when interpreting such radial trends. In addition, this effect will blur the observing trends. The uncertainty of the inclination (Table [1](#tab:NGC0253_prop)) affects the calculated radial distances by a factor of 0.4.

Next, we extract sight lines from each environment by applying the environmental mask (cite: querejeta_2021) and color-code the points by the environment, following the color scheme used in Figure [1](#fig:ngc253). The HCN intensity distribution in NGC 253 follows the CO(1–0) distribution described in (cite: sorai_2000; paglione_2004), i.e. the "twin-peaks" morphology, typical for barred galaxies (cite: kenney_1992). The brightest HCN emission is located at the center of the galaxy, which is also seen in other galaxies: at kpc resolution in the EMPIRE (cite: jimenez19) and ALMOND (cite: neumann_2023), in M 51 (cite: bigiel_2016), in nearby galaxies at similar spatial scales (cite: gallagher_2018a), and at higher spatial resolution in NGC 3627 (cite: beslic_2021). There is a steep decrease in HCN intensity by two orders of magnitude along the bar. Moreover, the HCN intensity varies by order of magnitude at distances of $r_\mathrm{gal}>2$ kpc, coincident with the ring and spiral arms. With increasing distance from the center of NGC 253, we also note a decrease in the HCN emission, particularly in the inner 1-2 kpc region within the bar where HCN intensity decreases steadily by order of magnitude, similar to the barred galaxy NGC 3627 (cite: beslic_2021).

Ancillary observations of the CO(1–0) emission at similar spatial resolution (16$''$ $\sim$250 pc) across NGC 253 (cite: sorai_2000; paglione_2004) show similar radial trends. (cite: sorai_2000) observed a secondary peak in CO(1–0) surface density around $r_\mathrm{gal}$=2 kpc, located at the end of the bar. In our case, we observe a similar increase in the CO(2–1) emission at a distance between $3-4$ kpc from the center of NGC 253, right outside the bar. In addition, we observe local enhancements in HCN in regions where the bar and the ring overlap and a decrease in HCN emission in the outermost parts of our map. By comparison, (cite: sorai_2000) found a decrease in CO(2–1) surface brightness by two orders of magnitude in the inner 1-2 kpc region of NGC 253, and the intensity after the second peak observed at 2 kpc is steadily decreasing. Moreover, the rotation curve of NGC 253 derived from the CO(1–0) emission (cite: koribalski_1995; sorai_2000) flattens in the ring, which suggests that molecular gas at these positions starts losing its angular momentum and infalling towards the center (cite: sorai_2000).

## Line of sight HCN/CO(2–1) intensity ratio

![](Figures_v2/spectra_new.png)

The ratio of HCN to CO(1–0) is often used within the literature to constrain the dense gas fraction, $f_\mathrm{dense}$ (cite: leroy_2017a). Knowing the scaling between $J=\mbox{(1--0)}$ and $J=\mbox{(2--1)}$ intensity ratio (cite: sandstrom_2013; zschaechner_2018; denbrok_2021; leroy_2022), it is possible to use HCN/CO(2–1) for determining the $f_\mathrm{dense}$. In the case of NGC 253, we are particularly interested in seeing how this line ratio varies across the galaxy and search for any environmental dependence.

We calculate the HCN/CO(2–1) integrated intensity ratio from the hexagonally, half-beam-sized sampled grid data points at 22 $^{\prime\prime}$. The uncertainty of the HCN/CO(2–1) ratio is computed from the uncertainties of their integrated intensities, using the standard error propagation technique (cite: beslic_2021; eibensteiner_2022). Figure [4](#fig:hcn_co21) shows the HCN/CO(2–1) line intensity ratio as a function of a distance from the center of NGC 253. The radial distribution of HCN/CO(2–1) follows the trends seen in the HCN emission (Figure [3](#fig:hcn_radial_profile)). It decreases towards larger galactocentric distances. The highest values (from 0.1 to 0.13) of this line ratio are found within the center of NGC 253. The transition from the central region to the disk is sharp, especially in the inner 2 kpc region of NGC 253 along the bar, where the HCN/CO(2–1) decreases by an order of magnitude. This finding is similar to the results reported in previous studies (cite: bigiel_2016; jimenez19; gallagher_2018a; querejeta_2019), whereas the weak radial variation of HCN/CO(2–1) intensity ratio across NCG 3627 was found in (cite: beslic_2021). In the rest of the environments, particularly in the ring, spiral arms and the disk, the HCN/CO(2–1) intensity ratio does not vary significantly (values between 0.01 and 0.05). We note exceptionally high values of the HCN/CO(2–1) intensity ratio at distances larger than 6 kpc, which arises from the fact that at these distances CO(2–1) emission appears to decrease more rapidly than the HCN.

To quantify HCN/CO(2–1) in these environments, we show the distribution of this line ratio in each region in the form of a violin plot on the upper right corner of Figure [4](#fig:hcn_co21). In this panel, the length of each violin corresponds to the range of HCN/CO(2–1)  intensity ratios. In contrast, the horizontal line indicates the mean measured in each environment. Points located in the center of NGC 253 have the highest mean of HCN/CO(2–1) of 0.1197$\pm$0.0002, which is about 4 times higher than the median values found in the rest of the galaxy. The bar shows the widest distribution and possible bimodal behavior. The first group of sight lines has a high HCN/CO(2–1) ratio of 0.1 and above, close to those found in the center. The second group of points contains HCN/CO(2–1) values similar to those seen in the ring and the rest of the regions (from 0.01 to 0.08). Therefore, the bar represents an intermediate region that bridges the center and the rest of the environments found in NGC 253. The enhancement in the HCN/CO(2–1) ratio found has a few possible implications, which we discuss in more detail in Section [6.1](#sec:outflow).

The observed HCN/CO(2–1) line ratio shows agreement within the literature data for other galaxies. Similar to (cite: gallagher_2018a), (cite: jimenez19), and (cite: beslic_2021), this line ratio has the highest values in the inner $\sim$500 pc region of the galaxy, i.e. the vast majority of the dense molecular gas relative to bulk molecular content is found within the center of a galaxy. (cite: knudsen_2007) found HCN/CO(1–0) ratio in the inner 1 kpc region to be 0.08. By applying the $R_{21}$ line ratio of 0.8 (cite: zschaechner_2018), we obtain higher values of HCN/CO(1–0). As opposed to HCN/CO(2–1) in the barred galaxy NGC 3627 (cite: beslic_2021), we see a stronger environmental dependence of HCN/CO(2–1) and a significant decrease toward higher galactocentric radii.

# Decomposed HCN emission

![](Figures_v2/scouse_comparisons.png)

To characterize the gas structure along each line of sight and its variation with the galactic environment, we study the spectra of the HCN emission in 5 different dynamical zones. We use a Semi-automated multi-COmponent Universal Spectral-line fitting Engine (cite: henshaw_2016a; henshaw_2019) to decompose the observed emission into separate components along each line of sight. This program is developed to analyze spectral lines and extract information (e.g., centroid velocity, line width) from modeling the shape of a spectral line. Appendix [10](#sec:app-scouse) provides a detailed description of using SCOUSE. We show the number of HCN velocity components identified by SCOUSE on the left panel of Figure [5](#fig:scouse1). Figure [5](#fig:scouse1) shows examples of 4 spectra originating from different dynamical regions (center, bar, ring, and spiral arms - each marked with a black rectangle on the left panel of Figure [5](#fig:scouse1)). In particular, lines of sight from the central region and the bar have multiple line profiles, whereas spectra towards the ring structure, spiral arms, and the disk are mainly narrow and single-peaked (the right panel in Figure [5](#fig:scouse1)). Similarly, (cite: sorai_2000) found compound velocity structures in CO(1–0), particularly within the bar. However, this is not due to the line broadening caused by galactic rotation within the beam. Instead, (cite: sorai_2000) proposed that strong non-circular motions cause the existence of two velocity components along the line of sight.

In Figure [6](#fig:scouse2), we present our results from applying the SCOUSE analysis to HCN and CO(2–1) datasets. Each panel of the figure shows the distribution of fitting parameters describing a Gaussian line shape derived from SCOUSE, which include the number of components, peak temperature, centroid velocity, and velocity dispersion. Furthermore, these parameters are divided according to each environment.

As shown in Figure [5](#fig:scouse1), each environment contains different spectral features in HCN and CO(2–1). CO(2–1) profiles are generally brighter than HCN, and the spectra within the center, followed by those in the bar, have the highest temperature peaks. The distribution of $T_\mathrm{peak}$ within the center has the largest dynamical range compared to the $T_\mathrm{peak}$ determined in spectra from other environments.

The third row in Figure [6](#fig:scouse2) summarizes what has been demonstrated in Figure [5](#fig:scouse1). The highest number of velocity components is seen towards the bar and nuclear region. HCN spectra are predominantly double and triple-peaked in these regions, unlike HCN spectra in the ring, spiral arms, and disk. We find similar spectral complexity of the CO(2–1) emission. In addition, we identify several pixels whose CO(2–1) spectrum shows three velocity components in the bar and only a few pixels containing three HCN velocity components. Two scenarios could explain the lower frequency of multiple components observed in the HCN emission than in the CO(2–1) spectrum. The first explanation is that the HCN emission is generally fainter than CO(2–1). In this scenario, assuming that each CO(2–1) has its own HCN partner and the new CO(2–1)  component along the same line of sight has a considerably lower signal-to-noise ratio than the previous one, it would explain why more HCN components were not detected. In the other case, since CO(2–1) and HCN trace overall different gas densities, it may occur that certain CO(2–1) clouds do not contain denser subregions possibly traced by HCN. The number of CO(2–1) velocity components towards each sight line within the ring and spiral arms is mostly one, except for a few lines of sight where we identify two CO(2–1) velocity features within the same pixel, possibly due to higher CO(2–1) sensitivity.

![](Figures_v2/hcn-co21-scouse.png)

Next, we comment on the individual velocity dispersion of HCN and CO(2–1). Here, the environmental dependence becomes prominent as in $T_\mathrm{peak}$. Central sight lines show the broadest lines, followed by sight lines from the bar. The distribution of HCN and CO(2–1) velocity dispersion in the center has a bimodal behavior. The broadest is the $\sigma$ distribution within the bar in HCN and CO(2–1)Ṫhe distribution of $\sigma$ in HCN and CO(2–1)  is compact in the rest of the environments. The highest median in $\sigma$ is found within the center (55 km s$^{-1}$ and 65 km s$^{-1}$ for the HCN and CO(2–1)). Interestingly, within the bar, we find higher median values in HCN (40 km s$^{-1}$) than in CO(2–1)  emission (30 km s$^{-1}$). In the ring and spiral arms, the median $\sigma$ in CO(2–1)  is higher than in HCN. The lines of sight across the disk show broad HCN and CO(2–1) components. These lines of sight are close to the center of NGC 253 (see Figure [3](#fig:hcn_radial_profile)).

## Decomposed HCN/CO(2–1) line intensity ratio

This section investigates the HCN/CO(2–1) intensity ratio derived from SCOUSE and compares it with our previous findings described in Section [3](#sec:line_of_sight). To directly compare HCN and CO(2–1) intensities from each component derived from SCOUSE, it is necessary to match the detected velocity components in HCN with those found in the CO(2–1) emission. As seen on the top left panel of Figure [6](#fig:scouse2), the number of Gaussian components differs from region to region and between HCN and CO(2–1). This could result from the CO(2–1)  tracing more lower density gas at shifted velocity to which the HCN is not sensitive.

The first step in associating velocity components is to look at the centroid velocities determined for each component within each pixel in HCN and CO(2–1), particularly the difference in $\upsilon_\mathrm{centroid, HCN}$ and $\upsilon_\mathrm{centroid, CO\mbox{(2--1)}}$. When the HCN velocity component is associated with the CO(2–1), their centroid velocities should be similar. Therefore, we consider that the HCN line is associated with the CO(2–1) if: $$\begin{equation}
\label{eq:centr}
    |\upsilon_\mathrm{centroid, HCN}-\upsilon_\mathrm{centroid, CO\mbox{(2--1)}}|<\sigma_\mathrm{thresh}.
\end{equation}$$ We define the $\sigma_\mathrm{thresh}$ as following: $$\begin{equation}
\label{eq:sigma_thresh}
    \sigma_\mathrm{thresh} = \dfrac{\sigma_\mathrm{CO(2-1)} + \sigma_\mathrm{HCN}}{2},
\end{equation}$$ and calculate this value for each pixel where we decompose the emission. Equations [\[eq:centr\]](#eq:centr) and [\[eq:sigma_thresh\]](#eq:sigma_thresh) represent the overlap of the clouds. Such a criterion assures us that clouds with higher line widths have a less strict association criterion. After applying this threshold, we match 100 $\%$ of HCN emission lines to those in CO(2–1) in the center, ring, and spiral arms. We matched $78\%$ of HCN emission to the CO(2–1) components within the bar. Around 60 percent of the CO(2–1) flux entering this analysis (see Section [2.3](#sec:smol)) is associated with the HCN emission. In exceptional cases, when two components have similar centroid velocities, we take the one with higher amplitude, i.e., the $T_\mathrm{peak}$.

Similarly, as in Figure [4](#fig:hcn_co21), in Figure [7](#fig:scouse_hcn_co21_ratio) we show the component-by-component HCN/CO(2–1) intensity ratio as a function of distance from the center of NGC 253 (left panel) and the distribution of this line ratio within each environment (right panel). The radial distribution of the component-by-component HCN/CO(2–1) is similar to that of the line of sight HCN/CO(2–1) (Figure [4](#fig:hcn_co21)). We also observe here the center showing the highest HCN/CO(2–1) ratio, followed by the bar. Similarly, as in Figure [4](#fig:hcn_co21), we observe a steady decrease in HCN/CO(2–1) at distances of $1-2$ kpc. By comparing the distributions of HCN/CO(2–1) computed from SCOUSE with those presented in Section [3.2](#sec:los_hcn-co) (dashed violin shapes on the right panel in Figure [7](#fig:scouse_hcn_co21_ratio)), we see the biggest difference between these two approaches in the center. Although the means of these two distributions are similar, their shape is different, i.e., the decomposed HCN/CO(2–1) distribution is significantly elongated than the line of sight distribution. The distributions of data points using both approaches within the bar are similar; they both show signs of bimodal behavior, but their mean values differ. The mean of the HCN/CO(2–1) from SCOUSE is comparable to the mean values calculated from the line of sight line ratio. Moreover, distributions of HCN/CO(2–1) of spiral arms and disk derived from SCOUSE are different than the line of sight HCN/CO(2–1), mainly because of a generally lower signal-to-noise ratio of the HCN emission in these environments, which resulted in a lower number of successfully decomposed lines of sight.

## HCN velocity dispersion

Molecular gas flows impact the dynamical state of the gas (cite: meidt_2018) and lead to collisions and gas crowding (cite: beuther_2017), thus possibly suppressing or enhancing star formation. This directly impacts the star formation efficiency, which is in line with turbulent models of star formation (cite: federrath_2013). On the one hand, whether tied to galactic gas flows or star formation feedback, super-virial gas motions can reduce star formation efficiencies (cite: padoan_2011; meidt_2020a). On the other hand, large velocity dispersions may signify elevated Mach numbers and a preferential build-up of dense gas (cite: krumholz_2005a; federrath_2012; jindra_2020).

The environments studied here represent a diversity of gas flows and conditions: strong shear in the center, elliptical streaming motions and strong radial inflows in the bar, a pile-up of gas in the ring, and strong spiral streaming motions. Here, we investigate the sensitivity of the gas velocity dispersion to these environments. We also explore how the velocity dispersion of dense gas compares to that of molecular gas. Dense gas arising from the small scales might be expected to be less sensitive to the flows present at or just beyond the cloud envelope, while its presence may reveal signatures of the critical role that colliding flows and shear have on the gas structure.

![](Figures_v2/scouse_hcn_vs_co21.png)

We compare the observed velocity dispersion in NGC 253 for HCN and CO(2–1) emission in Figure [8](#fig:scouse3). The solid black line represents the one-to-one ratio in HCN and CO(2–1) velocity dispersion. The HCN emission lines are narrower than the CO lines, as the data points typically lie below the diagonal line. This trend is particularly pronounced in the center and the bar, whereas data points are scattered around the solid black line at velocity dispersions below 50 km s$^{-1}$. Central sight lines populate the higher-values region, whereas sight lines from the spiral arms (orange points) and the ring (pink points) have low values. Interestingly, bar sight lines are distributed over the full range of the observed values along both axes.

The general positive correlation in HCN and CO(2–1)  velocity dispersion in NGC 253 agrees with previous velocity dispersion measurements in M 51 (cite: querejeta_2019), and across NGC 3627 (cite: beslic_2021). Our result confirms expectations that higher-density gas (traced by the HCN in our case) has smaller turbulent velocity dispersion than lower-density gas (traced by the CO(2–1)). This finding also agrees with the models that observed the building up of higher-density gas in the stagnation regions of convergent flows from the larger-scale turbulence. Consequently, the average velocity dispersion of the gas at these stagnation points will be smaller.

![](Figures_v2/hcn_co21_sigmaco21.png)

![](Figures_v2/sfe_dense_sfe_mol_fdense.png)

In Figure [9](#fig:scouse4), we show decomposed HCN/CO(2–1) intensity ratio derived from SCOUSE as a function of the CO(2–1) velocity dispersion. Our data points populate two different parts of this figure. In particular, we note at $\sigma_\mathrm{CO\mbox{(2--1)}}$ of $>45$ km s$^{-1}$ higher HCN/CO(2–1) values, which is a consequence of the environment, as these data points are located in the bar and the center. In the case of lower velocity dispersions, the 16% and 84% of observed HCN/CO(2–1) lie in the range from $0.02$ to $0.04$.

# Dense molecular gas and star formation

## Environmental dependence of the star formation efficiency of the dense gas

Previous extragalactic studies have shown different behavior of SFE$_\mathrm{dense}$  across the disk of a galaxy. For example, regions with high stellar surface density and thus interstellar pressure, such as centers of galaxies, typically have relatively lower SFE$_\mathrm{dense}$, i.e., the ability of dense gas to form stars is significantly reduced (cite: longmore_2013; kruijssen_2014a; usero_2015; bigiel_2016; barnes_2017; jimenez19; beslic_2021; eibensteiner_2022). In the following, we investigate properties of star formation efficiency of dense gas SFE$_\mathrm{dense}$ (usually traced by the $L_\mathrm{IR}/M_\mathrm{dense}$) across NGC 253.

In Figure [10](#fig:sfe_fdense), we show the TIR/HCN luminosity (TIR/$M_\mathrm{dense}$ on the right y-axis) ratio as a function of the molecular gas surface density. Dashed vertical lines in both panels show the gas surface density thresholds presented in (cite: bigiel_2008). The left vertical line at $\sim10\,\mathrm{M_{\odot}\,pc^{-2}}$ indicates the surface density above which the molecular gas dominates over the atomic phase (cite: bigiel_2008), whereas the right vertical line shows the surface density threshold of $\sim200\,\mathrm{M_{\odot}\,pc^{-2}}$, after which we enter the regime where dense molecular gas emission linearly scales with the star formation (cite: gao_2004a; bigiel_2008). The blue-shaded region corresponds to binned trends and their respective range of 16th and 84th percentiles. The horizontal shaded region shows a range of $400-500\,\mathrm{L_{\odot}/M_{\odot}}$.

Our HCN measurements are located in moderate density regimes (part of the bar, ring, spiral arms, and disk) and at high surface densities (lines of sight from the center and bar). That said, we do not have information about the HCN emission for molecular gas surface densities lower than a few $\mathrm{M_{\odot}\,pc^{-2}}$, where the atomic gas dominates the total gas surface densities (cite: bigiel_2008). The lowest values of SFE$_\mathrm{dense}$ are measured in the disk of NGC 253. At the intermediate surface densities (9-200 M$_\mathrm{\odot}$ pc$^{-2}$), SFE$_\mathrm{dense}$ rises with the cloud-scale molecular surface density up to $\sim100$M$_\mathrm{\odot}$ pc$^{-2}$, after which it starts decreasing. The mean SFE$_\mathrm{dense}$  increases up to $\sim500\,\mathrm{L_{\odot}/M_{\odot}}$ in the intermediate density regime, while the high surface density part shows nearly constant SFE$_\mathrm{dense}$  of $\sim400\,\mathrm{L_{\odot}/M_{\odot}}$. The lowest SFE$_\mathrm{dense}$ in this regime have lines of sight at the bar.

The center of NGC 253 is characterized by strong tidal forces and generally high pressure, typical also for other galaxies (cite: gallagher_2018b). Therefore, tidal forces may impact the fraction of gas that is self-gravitating, which can lead to a reduction in the observed SFE$_\mathrm{dense}$  when, at the same time, some part of the HCN-emitting gas is prevented from being in a state to collapse and form stars. Therefore, we suggest that the elevated average cloud density characteristic of the high-pressure central environment (cite: gallagher_2018b) implies that a greater portion of the cloud emits HCN in the central regions of NGC 253.

The observed behaviour of SFE$_\mathrm{dense}$  presented on Figure [10](#fig:sfe_fdense) may result the non-constant conversion factor $X_\mathrm{HCN}$. When $X_\mathrm{HCN}$ varies, the relation between HCN luminosity and dense gas mass becomes non-linear, and consequently, the SFE$_\mathrm{dense}$ will have intrinsic scatter. At the spatial scales probed in this work (300 pc), the temporal and environmental effects impact observed SFE$_\mathrm{dense}$, which are averaged out at larger scales.

In addition, it is important to consider the caveats of using the HCN emission as a proxy of dense gas, which has become especially important in regions with high-mean gas density. As seen in Figure [10](#fig:sfe_fdense), SFE$_\mathrm{dense}$  reaches a regime of $400-500\,\mathrm{L_{\odot}/M_{\odot}}$ at which SFE$_\mathrm{dense}$  becomes constant, also found in previous studies (cite: shirley_2003; scoville_2004; thompson_2005; wu_2010). In these high-density regimes, the HCN(1–0)  emission does not necessarily probe pure star-forming gas, as, for example, in other regions, where mean gas densities are comparable or lower than the critical density of HCN(1–0)  (cite: leroy_2017; beslic_2021). Alternatively, higher $J$ transitions of HCN can better probe dense gas mass relative to the average gas density in these regions. Therefore, excited HCN emission could be used to derive the $X_\mathrm{HCN}$ factor at higher densities and constrain the dense gas mass, which is beyond the scope of this work.

## Star formation efficiency and velocity dispersion

In this section, we investigate how the IR/HCN luminosity (and $L_\mathrm{IR}/M_\mathrm{dense}$) ratio varies with velocity dispersion and environment in NGC 253. We show the SFE$_\mathrm{dense}$  as a function of the HCN velocity dispersion inferred from SCOUSE decomposition (Section [4](#sec:scouse)) in Figure [11](#fig:scouse_sigma_sfedense). Similarly, as in Figure [8](#fig:scouse3), data points populate two distinct parts of Figure [11](#fig:scouse_sigma_sfedense). The first group of data points is located in the upper left part of the figure, showing HCN velocity dispersions lower than 40 $\, \ensuremath{\mathrm{km\,s^{-1}}}$, whereas the second group shows $\sigma_\mathrm{HCN}>$40 $\, \ensuremath{\mathrm{km\,s^{-1}}}$  and lies at the bottom right part of the figure.

The first group of data points consists of lines of sight from the ring and spiral arms, whereas the central lines of sight are in the second group. Lines of sight from the bar and the disk are found in both groups. The IR/HCN luminosity ratio decreases with increasing HCN velocity dispersion. This decrease is significantly steeper for data points with higher velocity dispersions. It is worth pointing out that the systemic rotation velocity is not necessarily resolved at our scales, which causes line broadening at the center. In addition, the observed anticorrelation between IR/HCN and $\sigma_\mathrm{HCN}$ comes from the correlation between CO and HCN intensities and their respective line widths. We note that, at the scales of our observations, the systemic rotation velocity is not fully resolved, which also broadens observed lines.

Nevertheless, broader molecular lines imply lower efficiency of such gas at star formation, and our results indicate that gas turbulence could be suppressing star formation (cite: padoan_2011; meidt_2018; meidt_2020a). Similar results are found in M 51 and NGC 3627 (cite: querejeta_2019; beslic_2021): central sight lines show broader emission lines, but the ability of such gas for star formation is reduced. (cite: murphy_2015) compared SFR/HCO$^+$ with HCO$^+$ line widths in the nuclear region and bar ends in NGC 3627 and concludes that the velocity dispersion of molecular is an important factor in setting star formation.

![](Figures_v2/scouse_sfe_dense_sigma_hcn.png)

# Discussion

## Enhancement of the HCN/CO(2–1) ratio in the inner 2 kpc of NGC 253

In the following, we provide a brief discussion of our results presented in Sections [3.1](#sec:hcn_radial_profile) and [3.2](#sec:los_hcn-co). As seen in Figure [3](#fig:hcn_radial_profile), the HCN integrated intensity shows general decrease towards the higher galactocentric radii. The steepest change in the HCN intensity occurs in the inner 2 kpc region of NGC 253. Such behaviour has been observed in previous studies probing similar or even smaller spatial scales (cite: beslic_2021; neumann_2023). Similarly, by looking at the radial trend of HCN/CO(2–1)  intensity ratio (Figure [4](#fig:hcn_co21)), we observe change by a factor of $\sim7$ in the inner 2 kpc, at the location of a bar in NGC 253. The reason for such steep decrease of the HCN, but also the CO(2–1)  intensities could be due to the bar influence. However, we speculate that other mechanisms impact this enhanced HCN/CO(2–1)  intensity ratio in the case of NGC 253.

The starburst in this galaxy drives the outflow seen in various gas phases: in ionized gas (H$\alpha$ and X-ray (cite: strickland_2000; strickland_2002; westmoquette_2011; lopez_2022), neutral gas (cite: heckman_2000), warm H$_2$ (cite: veilleux_2009), OH both in emission and absorption (cite: turner_1985; sturm_2011). Moreover, this outflow contains a significant amount of dust (HST observations (cite: watson_1996)), molecular gas, based on ALMA CO(1–0) observations (cite: bolatto_2013; krieger_2020), and dense molecular gas traced by HCN emission (cite: walter_2017; krieger_2017).

The enhanced HCN/CO(2–1) in the bar towards the centre of NGC 253 and the bimodal distribution for the bar sight lines in HCN/CO(2–1) have a few possible interpretations. On the one hand, we might witness a molecular gas flow, and there is a chance that enhanced HCN/CO(2–1) points in the bar originate from the molecular wind, as shown in (cite: walter_2017). On the other hand, beam smearing effects caused by a high galaxy inclination are not negligible. Therefore, we may detect the emission originating from the centre within the bar. Moreover, (cite: paglione_2004) found high gas densities traced by CO(1–0) emission near the inner Lindblad radius (cite: iodice_2014) and along the bar’s minor axis. We investigate these sight lines to further explore and explain the enhancement in HCN/CO(2–1).

The bar’s data points that form the upper locus of HCN/CO(2–1) (right panel of Figure [4](#fig:hcn_co21)) have values above 0.1. After inspecting the data points that cause the upper locus in the HCN/CO(2–1), we find that these points lie along the minor axis in NGC 253, i.e., where we expect to see the outflow. It is worth noting that the spatial scales probed by our data are not sufficient to resolve the outflow. Nevertheless, it is still possible to see the signs of the outflow within the spectra. (cite: walter_2017) observed the wind in NGC 253 in CO(1–0) emission and found a separate velocity component at intermediate ($-4$" to $-10$") offsets from the major axis. Therefore we plot the HCN spectrum including the decomposed emission derived from SCOUSE (Section [4](#sec:scouse)) towards the sight lines with enhanced HCN/CO(2–1) found along the minor axis, towards the direction of the brightest, south-western (SW) streamer of the outflow (negative offsets from the minor axis). We show these in Figure [12](#fig:hcn_spectra). Each spectrum is coloured by the HCN/CO(2–1) line intensity ratio.

Across all these points, we observe that the HCN emission consists of two components, the dominant one (dashed line) centered at velocities higher than 243 km s$^{-1}$, and a second one (solid line) centered at velocities lower than $-43\,$km s$^{-1}$, consisted with the value for the outflow, $\upsilon=-43$ km s$^{-1}$ (cite: walter_2017). We show this velocity as a solid black line in Figure [12](#fig:hcn_spectra), and systemic NGC 253 velocity as a black dashed line.

(cite: walter_2017) calculated HCN/CO(1–0) line intensity ratio in the outflow and the disk of NGC 253. This study found that the HCN/CO(1–0) is $\sim$0.1 in the outflow, and three times lower value in the disk ($1/30$). We estimate the HCN/CO(1–0) ratio from our measurements. To do so, we use a mean $R_{21}$ ratio of 0.8 measured in NGC 253 (cite: zschaechner_2018). After applying the $R_{21}$ ratio, sight lines with enhanced HCN/CO(2–1) line intensity ratio (from 0.1 to 0.12) correspond to values within the 0.080 to 0.096 range in HCN/CO(1–0). Therefore, the molecular outflow could explain the enhanced HCN/CO(2–1) intensity ratio found along the minor axis.

![](Figures_v2/spectra_minor_axis_new.png)

## Molecular gas kinematics

The inner 500 pc region of NGC 253, also called the central molecular zone (CMZ) is characterized by a strong dust continuum emission (cite: leroy_2018). The giant molecular clouds found in the CMZ of NGC 253 (cite: leroy_2015) are more massive and have higher velocity dispersion than the GMCs in the Milky Way (cite: krieger_2020). These clouds contain young massive clusters, bright in continuum and line emission (cite: leroy_2015; leroy_2018), with detected large-scale outflow in dense molecular (cite: levy_2021) and ionized gas (cite: mills_2021).

(cite: Meier_2015) provided a schematic representation of the central region in NGC 253, demonstrating its interesting and complex structure. These authors found that the nuclear disk consists of an inner and outer region ($\sim170$ pc and $\sim400$ pc). The inner nuclear disk contains high-density molecular gas and intense star formation. In contrast, the outer nuclear disk is considered the region where gas flows inward along the large-scale bar (cite: sorai_2000; paglione_2004; Meier_2015).

We show the position-velocity diagram in Figure [13](#fig:scouse_pvd) of the centroid velocities of HCN emission from the SCOUSE as a function of the offset from the galaxy’s minor axis. Each point is colour-coded by the HCN/CO(2–1) integrated intensity and the environment. The HCN/CO(2–1) is derived from the integrated intensities calculated from SCOUSE (see Section [7](#fig:scouse_hcn_co21_ratio)). Bar sight lines tend to form a "parallelogram"-shaped feature in the pv plane, previously seen in CO(1–0) (cite: sorai_2000) and CS(2–1) emission (cite: peng_1996), consistent with gas flowing in a bar potential (cite: binney_1991; athanassoula_1992; peng_1996; sormani_2015a). We note that there are more data points on the leading side of the bar (bottom left part of Figure [13](#fig:scouse_pvd)), which is indicative of molecular gas concentrations caused by a non-axisymmetric bar potential (cite: kuno_2000). The velocity gradient is the steepest in the bar and centre and more shallow in the ring and spiral arms. As the molecular gas travels from the outer disc, it starts losing angular momentum at galactocentric radii lower than the co-rotation radius $\sim3{-}4$ kpc (cite: iodice_2014), and is accreted onto the ring. The rotation curve within the ring is almost flat, causing the crowding of molecular gas, which is possibly supported by the observed narrow single-peaked HCN spectral features.

![](Figures_v2/scouse_pv_gal.png)

## Star formation efficiency

In Figure [14](#fig:gs), we summarize previous HCN surveys and studies, including recent ones (cite: neumann_2023). We show the relation of HCN luminosity and dense gas mass relation to star formation on the top left panel of Figure [14](#fig:gs), and to the TIR/HCN luminosity ratio and $L_\mathrm{IR}/M_\mathrm{dense}$ (cite: jimenez19).

We observe an approximately linear correlation between IR and HCN luminosities. As seen from the top panels of Figure [14](#fig:gs), the literature overview shows this correlation spanning more than ten orders of magnitude, covering a wide range of physical scales, from dense clumps and cores (cite: wu_2010; stephens_2016) within the Milky Way, to GMCs in local and nearby galaxies (cite: chin_1997; chin_1998; braine_2017; brouillet_2005; buchbender_2013; chen_2017; querejeta_2019), measurements of resolved galaxy disks (a few kpcs (cite: kepley_2014; usero_2015; bigiel_2016; chen_2015; gallagher_2018a; tan_2018; jimenez19; jiang_2020)) to whole galaxies and their centers (cite: gao_2004a; gao_2007; krips_2008; gracia_carpio_2008; juneau_2009; garcia_burillo_2012; crocker_2012; privon_2015; puschnig_2020). By observing this trend, a direct conclusion is that more dense molecular gas implies a higher star formation rate.

Therefore, we investigate how our results fit the relationship between star formation and dense molecular gas within the literature. We also include measurements from this work on NGC 253, colored by different regions in this galaxy in Figure [14](#fig:gs).

Our measurements span $\sim$ 3 orders of magnitude in IR luminosity and dense gas mass. Lines of sight from NGC 253 fall into the same region of the SFR-HCN plane as measurements of whole galaxies and parts of galaxies. The center of NGC 253 contains the largest amount of dense gas and shows the highest star formation activity, unlike the rest of the NGC 253’s environments. By contrast, in the top right panel, we note that regions with the brightest HCN emission in NGC 253 have the lowest SFE$_\mathrm{dense}$. This is in agreement with previous studies. For instance, the CMZ, the densest and most active region in our Galaxy, shows an order of magnitude lower SFR than those predicted from measurements of dense molecular gas (cite: longmore_2013a; henshaw_2022). In extragalactic work, (cite: jimenez19; neumann_2023) observed reduced SFE$_\mathrm{dense}$  towards centers of nearby galaxies, despite containing most of $M_\mathrm{dense}$ and the highest $f_\mathrm{dense}$. (cite: querejeta_2019) have shown that gas in spiral arms has large SFE$_\mathrm{dense}$  in M 51. Similarly, bar ends in NGC 3627 show higher SFE$_\mathrm{dense}$  than the center of this galaxy (cite: beslic_2021).

To first order, this relation seen in top panels of Figure [14](#fig:gs) suggests a universal density threshold above which gas starts to form stars (cite: lada_2012). However, the systematic scatter in the right panel in Figure [14](#fig:gs) implies that not all dense gas is equally efficient at star formation, i.e., SFE$_\mathrm{dense}$  is environmentally dependent. On the one hand, this could imply a physical change in $L_\mathrm{IR}/M_\mathrm{dense}$, possibly driven by dynamical effects such as turbulence and stellar feedback (cite: padoan_2011; federrath_2012) that become important at GMC scales (cite: gallagher_2018a; querejeta_2019; sanchez-garcia_2022; neumann_2023). In addition, as previously discussed in Section [5.1](#sec:sfe_fdense), a systematic variation in $X_\mathrm{HCN}$ can cause the observed scatter.

On the other hand, even in the case of a constant conversion factor between HCN luminosity and dense gas mass, it is possible that HCN might not be a reliable linear tracer of $M_\mathrm{dense}$, resulting in not all HCN-tracing gas taking part in star formation.

![image](Figures_v2/gs_1.png) ![image](Figures_v2/gs_2.png)

In the bottom panels of Figure [14](#fig:gs), we compare our results with other HCN observations across other starburst systems. We show measurements from (cite: kepley_2014) across the nearby starburst galaxy M 82 at slightly smaller physical scales (200 pc) than our work the sample of ULIRGs from (cite: garcia_burillo_2012), and sight lines from the galaxy merger, Antennae at 700 pc (cite: bigiel_2015). LIRGs and ULIRGs show elevated IR and HCN luminosity, two orders of magnitude higher than starburst systems. M 82 sight lines appear to have higher IR luminosity than NGC 253. The Centre of M 82 exhibits the brightest HCN emission (cite: kepley_2014), although it is fainter than the HCN emission towards the center of NGC 253. M 82 and NGC 253 are both typical starburst galaxies. However, these galaxies go through a different evolutionary phase (cite: rieke_1988) and have different magnitudes of starburst. NGC 253 is in the earlier starburst stage than M 82 (cite: telesco_1991). In addition, M 82 is a gas-rich starburst triggered by a major interaction with M 81. Therefore, we expect a higher fraction of HCN-tracing gas across NGC 253.

Looking at the top right panel in Figure [14](#fig:gs), we note scatter in the IR/HCN ratio of $\sim$3 dex for all sources. Overall, among each source presented in this figure, we observe that lines of sight with the highest HCN luminosities have the lowest star formation efficiencies, except M 82, where this trend is unclear. LIRGS and ULIRGS (cite: garcia_burillo_2012), together with measurements of M 82 (cite: kepley_2014), have the highest star formation efficiencies.

The results discussed in this section are consistent with the known role of the HCN-tracing gas in star formation, i.e., that higher HCN luminosity implies higher star formation rate, but that the scatter in IR/HCN as a function of HCN luminosity is not negligible. We observe environmental dependence on the observed IR/HCN with dense gas mass, as confirmed in several previous studies (cite: jimenez19). However, The still observed scatter remains to be explained by future more sensitive, high-resolution observations across nearby galaxies that can probe the physical properties of individual molecular clouds.

# Summary

We present new ALMA ACA+TP observations of HCN emission at 300 pc scales across the closest southern starburst galaxy NGC 253. These observations cover a large portion of NGC 253 disk that contains 95$\%$ of detected CO(2–1) emission obtained by ALMA ACA, and 85$\%$ of the star formation activity measured from ancillary infrared data at 70, 160, and 250 $\mu$m obtained by Herschel Space Telescope (cite: pilbratt_2010). Our work investigates the HCN line intensity distribution, its relation to the CO(2–1) emission, gas kinematics traced by this molecular line, the ability of gas to form stars, and the environmental dependence of these properties. Here we summarize our results:

- We use two independent methods to derive the integrated intensity of HCN emission. The first approach is based on calculating the zeroth moment map and extracting the information of HCN emission from it. In contrast, the second one uses information derived from the spectral decomposition of the observed emission along each line of sight. By performing spectral decomposition, we gain insight into the velocity components that contribute to the observed line emission at each point.\

- Our results derived from both methods are in good agreement. We find environmental differences in the observed HCN emission across NGC 253, particularly in regions closer to the center and regions in the disc. The HCN emission is strongly enhanced towards the center of NGC 253, and its intensity decreases by two orders of magnitude along the bar. HCN intensity weakly varies along the ring, spiral arm, and disc.\

- In addition, the HCN spectrum shows complexity and environmental dependence. In the inner 2 kpc region, we observe multiple velocity structures in the HCN and CO(2–1)spectra. Using spectral decomposition, we find up to three separate velocity structures in the central and bar sight lines, indicating that our observations probe multiple gas flows. Moreover, HCN and CO(2–1) spectral lines within the ring structure and spiral arms are mainly single-peaked and significantly narrower than the spectra from the inner regions. Our results support the idea that the molecular gas sits in the ring, after which it is inflowing towards the nuclear region along the bar.

- We investigate HCN/CO(2–1) line intensity ratio and its environmental distribution in NGC 253. We found that the HCN/CO(2–1) distribution within the bar shows bimodal behavior, which is a consequence of beam-smearing effects and a possible indication of the molecular outflow found in (cite: walter_2017). A nearly constant HCN/CO(2–1) intensity ratio within the ring, in line with the flattened rotational curve of CO at this region, suggests that molecular gas traced by HCN emission gets piled up in that region.\

- The majority of the decomposed HCN emission has an associated CO(2–1) component. All lines of sight in the ring, spiral arms, and disc have HCN emission associated with the CO(2–1). In contrast, in inner regions, the percentage of associated components is somewhat lower, which could be due to opacity broadening, lower signal-to-noise ratio in HCN than CO(2–1) emission, but also that some of the CO(2–1) is diffuse and does not contain HCN. Together with spectral complexity, we find the environment to be the driver of the measured HCN velocity dispersion and broader HCN lines in regions with different dynamical characteristics.\

- Wider CO(2–1) profiles contain wider HCN emission lines, and CO(2–1) emission lines are broader than HCN lines, suggesting that HCN-tracing gas arises from smaller spatial structures. This result aligns with turbulence theory, which predicts that high-density gas is mostly seen at the stagnation regions of larger-scale convergent flows.\

- We investigate the ability of the gas to form stars as a function of the relative amount of HCN-traced molecular gas to bulk molecular gas. Lines of sight with the highest HCN/CO(2–1) ratio appear the least efficient at star formation (the lowest IR/HCN). This result suggests that the processes that regulate star formation vary with the environment.

Our work illustrates the importance of mapping the spatially resolved emission of the molecular gas tracing star-forming content on the example of NGC 253. In this work, we also analyze the spectrum of these lines along individual lines of sight. We highlight the necessity of extending our understanding of dense gas properties across starburst systems such as NGC 253 since they provide additional constraints on the dense gas properties in the vicinity of extreme physical conditions, particularly in its center.

# Acknowledgements

We thank the anonymous referee for their insightful comments that improved this manuscript. The author wants to thank Maryvonne Gerin and Jerome Pety for their insightful discussion that contributed to the quality of this work.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.2.00236.S and ADS/JAO.ALMA#2018.1.01321.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. In addition, publications from NA authors must include the standard NRAO acknowledgement: The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

IB, ATB, and FB would like to acknowledge the funding provided from the European Union’s Horizon 2020 research and innovation programme (grant agreement No 726384/Empire). HAP acknowledges support by the National Science and Technology Council of Taiwan under grant 110-2112-M-032-020-MY3. KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship DE220100766 funded by the Australian Government. KG is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. MC gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant number CH2137/1-1). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins. JMDK gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement number 714907). RSK acknowledges support from DFG via the collaborative research center “The Milky Way System” (SFB 881; project ID 138713538; sub-projects B1, B2 and B8), from the Heidelberg cluster of excellence EXC 2181“STRUCTURES” (project ID 390900948), funded by the German excellence strategy, from ERC via the synergy grant “ECOGAL” (grant 855130), and from the German Ministry for Economic Affairs and Climate Action for funding in project “MAINN” (funding ID 50OO2206).

140 natexlab

(ref: aladro_2011) Aladro, R., Martı́n-Pintado, J., Martı́n, S., Mauersberger, R., & Bayet, E. 2011, A&A, 525, A89

(ref: anand_2020) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2020, MNRAS

(ref: aniano_2011) Aniano, G., Draine, B. T., Gordon, K. D., & Sandstrom, K. 2011, PASP, 123, 1218

(ref: arnaboldi_1995) Arnaboldi, M., Capaccioli, M., Cappellaro, E., Held, E. V., & Koribalski, B. 1995, AJ, 110, 199

(ref: athanassoula_1992) Athanassoula, E. 1992, MNRAS, 259, 345

(ref: barnes_2017) Barnes, A. T., Longmore, S. N., Battersby, C., et al. 2017, MNRAS, 469, 2263

(ref: beuther_2017) Beuther, H., Meidt, S., Schinnerer, E., Paladino, R., & Leroy, A. 2017, A&A, 597, A85

(ref: beslic_2021) Bešlić, I., Barnes, A. T., Bigiel, F., et al. 2021, MNRAS, 506, 963

(ref: bigiel_2008) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846

(ref: bigiel_2015) Bigiel, F., Leroy, A. K., Blitz, L., et al. 2015, ApJ, 815, 103

(ref: bigiel_2016) Bigiel, F., Leroy, A. K., Jiménez-Donaire, M. J., et al. 2016, ApJL, 822, L26

(ref: binney_1991) Binney, J., Gerhard, O. E., Stark, A. A., Bally, J., & Uchida, K. I. 1991, MNRAS, 252, 210

(ref: bisbas_2015) Bisbas, T. G., Papadopoulos, P. P., & Viti, S. 2015, ApJ, 803, 37

(ref: bolatto_2013b) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013a, ARA&A, 51, 207

(ref: bolatto_2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013b, ARA&A, 51, 207

(ref: braine_2017) Braine, J., Shimajiri, Y., André, P., et al. 2017, A&A, 597, A44

(ref: brouillet_2005) Brouillet, N., Muller, S., Herpin, F., Braine, J., & Jacq, T. 2005, A&A, 429, 153

(ref: buchbender_2013) Buchbender, C., Kramer, C., Gonzalez-Garcia, M., et al. 2013, A&A, 549, A17

(ref: casasola_2011) Casasola, V., Hunt, L. K., Combes, F., Garcı́a-Burillo, S., & Neri, R. 2011, A&A, 527, A92

(ref: chen_2017) Chen, H., Braine, J., Gao, Y., Koda, J., & Gu, Q. 2017, ApJ, 836, 101

(ref: chen_2015) Chen, H., Gao, Y., Braine, J., & Gu, Q. 2015, ApJ, 810, 140

(ref: chin_1998) Chin, Y. N., Henkel, C., Millar, T. J., Whiteoak, J. B., & Marx-Zimmer, M. 1998, A&A, 330, 901

(ref: chin_1997) Chin, Y. N., Henkel, C., Whiteoak, J. B., et al. 1997, A&A, 317, 548

(ref: cormier_2014) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2014, A&A, 564, A121

(ref: crocker_2012) Crocker, A., Krips, M., Bureau, M., et al. 2012, MNRAS, 421, 1298

(ref: denbrok_2021) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221

(ref: dickman_1986) Dickman, R. L., Snell, R. L., & Schloerb, F. P. 1986, ApJ, 309, 326

(ref: eibensteiner_2022) Eibensteiner, C., Barnes, A. T., Bigiel, F., et al. 2022, A&A, 659, A173

(ref: faesi_2023) Faesi, C. in prep

(ref: federrath_2012) Federrath, C. & Klessen, R. S. 2012, ApJ, 761, 156

(ref: federrath_2013) Federrath, C. & Klessen, R. S. 2013, ApJ, 763, 51

(ref: forbrich_2014) Forbrich, J., Öberg, K., Lada, C. J., et al. 2014, A&A, 568, A27

(ref: galametz_2013) Galametz, M., Kennicutt, R. C., Calzetti, D., et al. 2013, MNRAS, 431, 1956

(ref: gallagher_2018b) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018a, ApJL, 868, L38

(ref: gallagher_2018a) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018b, ApJ, 858, 90

(ref: gao_2007) Gao, Y., Carilli, C. L., Solomon, P. M., & Vand en Bout, P. A. 2007, ApJL, 660, L93

(ref: gao_2004a) Gao, Y. & Solomon, P. M. 2004, ApJS, 152, 63

(ref: garcia_burillo_2012) Garcı́a-Burillo, S., Usero, A., Alonso-Herrero, A., et al. 2012, A&A, 539, A8

(ref: jindra_2020) Gensior, J., Kruijssen, J. M. D., & Keller, B. W. 2020, MNRAS, 495, 199

(ref: genzel_2015) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: spectral_cube) Ginsburg, A., Koch, E., Robitaille, T., et al. 2019, radio-astro-tools/spectral-cube: v0.4.4

(ref: gracia_carpio_2008) Graciá-Carpio, J., Garcı́a-Burillo, S., & Planesas, P. 2008, Ap&SS, 313, 331

(ref: heckman_2000) Heckman, T. M., Lehnert, M. D., Strickland, D. K., & Armus, L. 2000, ApJS, 129, 493

(ref: henshaw_2022) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2022, arXiv e-prints, arXiv:2203.11223

(ref: henshaw_2019) Henshaw, J. D., Ginsburg, A., Haworth, T. J., et al. 2019, MNRAS, 485, 2457

(ref: henshaw_2016a) Henshaw, J. D., Longmore, S. N., Kruijssen, J. M. D., et al. 2016, MNRAS, 457, 2675

(ref: herrera_2020) Herrera, C. N., Pety, J., Hughes, A., et al. 2020, A&A, 634, A121

(ref: herrera-endoqui_2015) Herrera-Endoqui, M., Dı́az-Garcı́a, S., Laurikainen, E., & Salo, H. 2015, A&A, 582, A86

(ref: hlavacek-larrondo_2011) Hlavacek-Larrondo, J., Carignan, C., Daigle, O., et al. 2011, MNRAS, 411, 71

(ref: holdship_2021) Holdship, J., Viti, S., Martı́n, S., et al. 2021, A&A, 654, A55

(ref: houghton_1997) Houghton, S., Whiteoak, J. B., Koribalski, B., et al. 1997, A&A, 325, 923

(ref: iodice_2014) Iodice, E., Arnaboldi, M., Rejkuba, M., et al. 2014, A&A, 567, A86

(ref: jiang_2020) Jiang, X.-J., Greve, T. R., Gao, Y., et al. 2020, MNRAS, 494, 1276

(ref: jimenez-donaire_2023) Jimenez-Donaire, M. J. 2023, MNRAS in prep

(ref: jimenez19) Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2019, ApJ, 880, 127

(ref: ds9) Joye, W. A. & Mandel, E. 2003, in Astronomical Society of the Pacific Conference Series, Vol. 295, Astronomical Data Analysis Software and Systems XII, ed. H. E. Payne, R. I. Jedrzejewski, & R. N. Hook, 489

(ref: juneau_2009) Juneau, S., Narayanan, D. T., Moustakas, J., et al. 2009, ApJ, 707, 1217

(ref: kauffmann_2017) Kauffmann, J., Goldsmith, P. F., Melnick, G., et al. 2017, A&A, 605, L5

(ref: kenney_1994) Kenney, J. D. P. 1994, in Astronomical Society of the Pacific Conference Series, Vol. 59, IAU Colloq. 140: Astronomy with Millimeter and Submillimeter Wave Interferometry, ed. M. Ishiguro & J. Welch, 282

(ref: kenney_1992) Kenney, J. D. P., Wilson, C. D., Scoville, N. Z., Devereux, N. A., & Young, J. S. 1992, ApJL, 395, L79

(ref: kennicutt_2011) Kennicutt, R. C., Calzetti, D., Aniano, G., et al. 2011, PASP, 123, 1347

(ref: kepley_2014) Kepley, A. A., Leroy, A. K., Frayer, D., et al. 2014, ApJL, 780, L13

(ref: knudsen_2007) Knudsen, K. K., Walter, F., Weiss, A., et al. 2007, The Astrophysical Journal, 666, 156

(ref: koribalski_1995) Koribalski, B., Whiteoak, J. B., & Houghton, S. 1995, PASA, 12, 20

(ref: krieger_2020) Krieger, N., Bolatto, A. D., Koch, E. W., et al. 2020, ApJ, 899, 158

(ref: krieger_2017) Krieger, N., Ott, J., Beuther, H., et al. 2017, ApJ, 850, 77

(ref: krips_2008) Krips, M., Neri, R., Garcı́a-Burillo, S., et al. 2008, ApJ, 677, 262

(ref: kruijssen_2014a) Kruijssen, J. M. D., Longmore, S. N., Elmegreen, B. G., et al. 2014, MNRAS, 440, 3370

(ref: krumholz_2005a) Krumholz, M. R. & McKee, C. F. 2005, ApJ, 630, 250

(ref: kuno_2000) Kuno, N., Nishiyama, K., Nakai, N., et al. 2000, PASJ, 52, 775

(ref: lada_2012) Lada, C. J., Forbrich, J., Lombardi, M., & Alves, J. F. 2012, ApJ, 745, 190

(ref: leroy_2015) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25

(ref: leroy_2018) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2018, ApJ, 869, 126

(ref: leroy_2021a) Leroy, A. K., Hughes, A., Liu, D., et al. 2021a, arXiv e-prints, arXiv:2104.07665

(ref: leroy_2022) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149

(ref: leroy_2017) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2017a, ApJ, 846, 71

(ref: leroy_2021b) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, arXiv e-prints, arXiv:2104.07739

(ref: leroy_2017a) Leroy, A. K., Usero, A., Schruba, A., et al. 2017b, ApJ, 835, 217

(ref: leroy_2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: levy_2021) Levy, R. C., Bolatto, A. D., Leroy, A. K., et al. 2021, ApJ, 912, 4

(ref: longmore_2013a) Longmore, S. N., Bally, J., Testi, L., et al. 2013a, MNRAS, 429, 987

(ref: longmore_2013) Longmore, S. N., Bally, J., Testi, L., et al. 2013b, MNRAS, 429, 987

(ref: longmore_2014) Longmore, S. N., Kruijssen, J. M. D., Bastian, N., et al. 2014, Protostars and Planets VI, 291

(ref: lopez_2022) Lopez, S., Lopez, L. A., Nguyen, D. D., et al. 2022, arXiv e-prints, arXiv:2209.09260

(ref: maclow_2004) Mac Low, M.-M. & Klessen, R. S. 2004, Reviews of Modern Physics, 76, 125

(ref: martin_2021) Martı́n, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46

(ref: martin_2006) Martı́n, S., Mauersberger, R., Martı́n-Pintado, J., Henkel, C., & Garcı́a-Burillo, S. 2006, ApJS, 164, 450

(ref: mauersberger_1996) Mauersberger, R., Henkel, C., Wielebinski, R., Wiklind, T., & Reuter, H. P. 1996, A&A, 305, 421

(ref: mcmullin_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: meidt_2018) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2018a, ApJ, 854, 100

(ref: meidt_2020a) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2018b, ApJ, 854, 100

(ref: Meier_2015) Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, The Astrophysical Journal, 801, 63

(ref: mills_2021) Mills, E. A. C., Gorski, M., Emig, K. L., et al. 2021, ApJ, 919, 105

(ref: munoz-mateos_2015) Muñoz-Mateos, J. C., Sheth, K., Regan, M., et al. 2015, ApJS, 219, 3

(ref: murphy_2015) Murphy, E. J., Dong, D., Leroy, A. K., et al. 2015, ApJ, 813, 118

(ref: neumann_2023) Neumann, L., Gallagher, M. J., Bigiel, F., et al. 2023, MNRAS, 521, 3348

(ref: padoan_2011) Padoan, P. & Nordlund, Å. 2011, ApJ, 730, 40

(ref: paglione_2004) Paglione, T. A. D., Yam, O., Tosaki, T., & Jackson, J. M. 2004, ApJ, 611, 835

(ref: pak_1998) Pak, S., Jaffe, D. T., van Dishoeck, E. F., Johansson, L. E. B., & Booth, R. S. 1998, ApJ, 498, 735

(ref: pence_1980) Pence, W. D. 1980, ApJ, 239, 54

(ref: peng_1996) Peng, R., Zhou, S., Whiteoak, J. B., Lo, K. Y., & Sutton, E. C. 1996, ApJ, 470, 821

(ref: pety_2017) Pety, J., Guzmán, V. V., Orkisz, J. H., et al. 2017, A&A, 599, A98

(ref: pilbratt_2010) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1+

(ref: privon_2015) Privon, G. C., Herrero-Illana, R., Evans, A. S., et al. 2015, ApJ, 814, 39

(ref: puschnig_2020) Puschnig, J., Hayes, M., Östlin, G., et al. 2020, A&A, 644, A10

(ref: querejeta_2021) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, arXiv e-prints, arXiv:2109.04491

(ref: querejeta_2019) Querejeta, M., Schinnerer, E., Schruba, A., et al. 2019, A&A, 625, A19

(ref: rieke_1980) Rieke, G. H., Lebofsky, M. J., Thompson, R. I., Low, F. J., & Tokunaga, A. T. 1980, ApJ, 238, 24

(ref: rieke_1988) Rieke, G. H., Lebofsky, M. J., & Walker, C. E. 1988, ApJ, 325, 679

(ref: saintonge_2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22

(ref: sanchez-garcia_2022) Sánchez-Garcı́a, M., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2022, A&A, 660, A83

(ref: sanders_2003) Sanders, D. B., Mazzarella, J. M., Kim, D. C., Surace, J. A., & Soifer, B. T. 2003, AJ, 126, 1607

(ref: sandstrom_2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: schruba_2011) Schruba, A., Leroy, A. K., Walter, F., et al. 2011, The Astronomical Journal, 142, 37

(ref: scoville_2004) Scoville, N. Z. & Wilson, C. D. 2004, in Astronomical Society of the Pacific Conference Series, Vol. 322, The Formation and Evolution of Massive Young Star Clusters, ed. H. J. G. L. M. Lamers, L. J. Smith, & A. Nota, 245

(ref: semenov_2015) Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2016, The Astrophysical Journal, 826, 200

(ref: shirley_2015) Shirley, Y. L. 2015, PASP, 127, 299

(ref: shirley_2003) Shirley, Y. L., Evans, Neal J., I., Young, K. E., Knez, C., & Jaffe, D. T. 2003, ApJS, 149, 375

(ref: sorai_2000) Sorai, K., Nakai, N., Kuno, N., Nishiyama, K., & Hasegawa, T. 2000, PASJ, 52, 785

(ref: sormani_2015a) Sormani, M. C., Binney, J., & Magorrian, J. 2015, MNRAS, 449, 2421

(ref: stephens_2016) Stephens, I. W., Jackson, J. M., Whitaker, J. S., et al. 2016, ApJ, 824, 29

(ref: strickland_2000) Strickland, D. K., Heckman, T. M., Weaver, K. A., & Dahlem, M. 2000, AJ, 120, 2965

(ref: strickland_2002) Strickland, D. K., Heckman, T. M., Weaver, K. A., Hoopes, C. G., & Dahlem, M. 2002, ApJ, 568, 689

(ref: sturm_2011) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: sun_2023) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, ApJL, 945, L19

(ref: sun_2020b) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8

(ref: sun_2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, The Astrophysical Journal, 860, 172

(ref: tacconi_2010) Tacconi, L. 2010, in From Stars to Galaxies: Connecting our Understanding of Star and Galaxy Formation, 130

(ref: tan_2018) Tan, Q.-H., Gao, Y., Zhang, Z.-Y., et al. 2018, ApJ, 860, 165

(ref: telesco_1991) Telesco, C. M., Campins, H., Joy, M., Dietz, K., & Decher, R. 1991, in Dynamics of Galaxies and Their Molecular Cloud Distributions, ed. F. Combes & F. Casoli, Vol. 146, 284

(ref: thompson_2005) Thompson, T. A., Quataert, E., & Murray, N. 2005, ApJ, 630, 167

(ref: turner_1985) Turner, J. L. & Ho, P. T. P. 1985, ApJL, 299, L77

(ref: usero_2015) Usero, A., Leroy, A. K., Walter, F., et al. 2015, AJ, 150, 115

(ref: veilleux_2009) Veilleux, S., Rupke, D. S. N., & Swaters, R. 2009, ApJL, 700, L149

(ref: walter_2017) Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, ApJ, 835, 265

(ref: watson_1996) Watson, A. M., Gallagher, J. S., I., Holtzman, J. A., et al. 1996, AJ, 112, 534

(ref: westmoquette_2011) Westmoquette, M. S., Smith, L. J., & Gallagher, J. S., I. 2011, MNRAS, 414, 3719

(ref: wu_2010) Wu, J., Evans, Neal J., I., Shirley, Y. L., & Knez, C. 2010, ApJS, 188, 313

(ref: yajima_2021) Yajima, Y., Sorai, K., Miyamoto, Y., et al. 2021, PASJ, 73, 257

(ref: zschaechner_2018) Zschaechner, L. K., Bolatto, A. D., Walter, F., et al. 2018, ApJ, 867, 111

# Molecular surface density

We show $\Sigma_\mathrm{mol}$  in Figure [15](#fig:smol_map). The production of this map is described in Section [2.3](#sec:smol). In this work, we used a specific region of CO(2–1) emission, highlighted by the dashed white rectangle in Figure [1](#fig:ngc253).

![](Figures_v2/smol_map.png)

# Star formation surface density

In Table [2](#tab:coeff_tir) we show coefficients used to compute the star formation surface density, which map we show in Figure [16](#fig:sfr_map).

![](Figures_v2/sfr_maps.png)

| $j=\lambda$ \[nm\] |       $c_j$       |
|:------------------:|:-----------------:|
|         70         | 1.018 $\pm$ 0.021 |
|        160         | 1.068 $\pm$ 0.035 |
|        250         | 0.402 $\pm$ 0.097 |

: Coefficient for calculation total infrared surface density (Equation [\[eq:tir\]](#eq:tir), Section [2.4](#sec:ssfr)) taken from (cite: galametz_2013).

# Spectral decomposition using SCOUSE

In our work, we use the Semi-automated multi-COmponent Universal Spectral-line fitting Engine (SCOUSE) (cite: henshaw_2016a; henshaw_2019), which is the spectral decomposition algorithm that defines where the line is located within the spectrum and describes such lines using Gaussian fitting. SCOUSE consists of four steps. In the first step, we define a spatial area over which we want to fit the spectra by creating a grid of macro pixels called Spectral Averaging Areas (SAAs). The size of a SAA is a free parameter. In our case, each SAA contains 4 pixels. The spectrum of each SAA represents the averaged spectrum of all the spectra within pixels contained in the SAA. In the second phase, SCOUSE fits each SAA’s spectrum and suggests a model solution assuming the Gaussian line profile. The model solution within each SAA consists of the detected number of Gaussian components and the fitting parameters: the amplitude, the centroid velocity, and the line width. In case when SCOUSE cannot find a proper solution for a fit, the user can manually change the requested signal-to-noise ratio in order for fitting parameters to converge or fit the respective spectrum manually by selecting the location of the spectral line within the spectrum, its peak, and the brightness temperature at which the spectrum reaches the 50 $\%$ of its peak. After completing the second phase, SCOUSE has a model solution of each SAA’s spectrum and uses these to fit pixels within each SAA. In the third phase, the user checks the SCOUSE’s model solutions for each pixel. Like the second phase, the user can change the number of Gaussian components and their fitting parameters. The location of each pixel in the map and SCOUSE solutions for their spectrum are saved in the textual file in the final, fourth phase.

</paper>

Write the methods card for this paper.