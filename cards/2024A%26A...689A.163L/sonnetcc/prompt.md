# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.163L\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...689A.163L",
 "title": "The fountain of the luminous infrared galaxy Zw049.057 as traced by its OH megamaser",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Lankhaar, Boy",
 "n_authors": 18,
 "arxiv_id": "2406.07620",
 "doi": "10.1051/0004-6361/202450065",
 "alma_projects_linked_by_archive": [
  "2019.1.01612.S"
 ]
}
```

Paper text:
<paper>
# The fountain of the luminous infrared galaxy Zw049.057 as traced by its OH megamaser

High resolution ($0.037\ensuremath{''}-0.13\ensuremath{''}$ \[$10-35$ pc\]) e-MERLIN ($\lambda6-18$ cm) and ($0.024\ensuremath{''}$ \[$6.5$ pc\]) ALMA ($\lambda 1.1$ mm) observations have been used to image OH (hydroxyl) and H$_2$CO (formaldehyde) megamaser emission, and HCN $3 \to 2$ emission towards the nuclear ($<100$ pc) region of the luminous infrared galaxy Zw049.057. Zw049.057 hosts a compact obscured nucleus (CON), thus representing a class of galaxies that are often associated with inflow and outflow motions. Formaldehyde megamaser emission is detected towards the nuclear region, $\lesssim 30$ pc ($0.1\ensuremath{''}$), and traces a structure along the disk major axis. OH megamaser (OHM) emission is detected along the minor axis of the disk, $\sim 30$ pc ($0.1\ensuremath{''}$) from the nucleus, where it exhibits a velocity gradient with extrema of $-20$ km s$^{-1}$ south-east (SE) of the disk and $-110$ km s$^{-1}$ north-west (NW) of the disk. HCN $3 \to 2$ emission reveals extended emission, along the disk minor axis out to $\sim 60$ pc ($0.2\ensuremath{''}$). Analysis of the minor axis HCN emission reveals high-velocity features, extending out to $600$ km s$^{-1}$, redshifted on the SE side and blueshifted on the NW side. We propose that the high-velocity HCN emission traces a fast ($>250$ km s$^{-1}$) and collimated outflow, that is enveloped by a wide-angle and slow ($\sim 50$ km s$^{-1}$) outflow that is traced by the OHM emission. Analysis of the outflow kinematics suggests that the slow wide-angle outflow will not reach escape velocity and instead will fall back to the galaxy disk, evolving as a so-called fountain flow, while the fast collimated outflow traced by HCN emission will likely escape the nuclear region. We suggest that the absence of OHM emission in the nuclear region is due to high densities there. Even though OHMs associated with outflows are an exception to conventional OHM emission, we expect them to be common in CON sources that host both OHM and H$_2$CO megamasers.

# Introduction

The majority of the most luminous galaxies radiate the bulk of their energy in the far-infrared (cite: sanders:96). According to their luminosity, these are either classified as luminous ($L_{\mathrm{IR}}>10^{11}$ $\mathrm{L}_{\odot}$) infrared galaxies (LIRGs), or ultra luminous ($L_{\mathrm{IR}}>10^{12}$ $\mathrm{L}_{\odot}$) infrared galaxies (ULIRGs). The extreme luminosities of (U)LIRGs are powered by an active galactic nucleus (AGN), an intense starburst (SB) phase, or both. (U)LIRGs emit the bulk of their energy in the FIR as their luminosity sources are embedded in a dusty phase that reprocesses radiation to longer wavelengths. While (U)LIRGs represent an evolutionary phase that many galaxies go through (cite: smail:97; hughes:98), they themselves are rapidly evolving objects.

A significant fraction of (U)LIRGs host compact ($r<100$ pc), highly obscured ($N_{\mathrm{H}_2} \gtrsim 10^{25}$ cm$^{-2}$) and warm ($T \gtrsim 100$ K) nuclei (cite: aalto:15; falstad:19; falstad:21; garcia:22; donnan:23). These compact obscured nuclei (CONs) are responsible for a large fraction of the total infrared luminosity of their host galaxies, despite their small sizes (cite: gonzalez:12; falstad:15; falstad:21). Due to their opaque nature, it is difficult to discern the ultimate source of their luminosity. It has become increasingly clear that the CONs represent an evolutionary phase that is associated with both inflowing (cite: gonzalez:17; aalto:19; falstad:19) and outflowing (cite: barcos:18; falstad:18; gorski:23; wethers:24) gas motions. Yet, due to their opaqueness, signatures of radial gas motions are often only discernible at wavelengths $\gtrsim 1\ \mathrm{mm}$ (cite: falstad:19).

Radial gas motions towards galaxy nuclei are decidedly important to understand galaxy evolution. Inflowing gas motions drive nuclear activity and feed the nuclear star-forming gas. In turn, outflows transport the chemically enriched nuclear gas and dust away from the nuclear region, towards galaxy halos and the intergalactic medium (cite: veilleux:20; martin:05), but also may contribute to nuclear growth by efficiently transporting angular momentum (cite: wada:12; konigl:94). Galactic outflows may be driven by nuclear activity, stellar winds and supernovae from the SB phase, radiation pressure or cosmic-ray pressure (cite: veilleux:20). Indeed, the association of CONs with radial gas motions indicates that these sources are rapidly evolving (cite: sakamoto:13). Understanding these gas motions, and constraining their driving mechanism(s) is of pivotal importance to understand CONs, both as a subclass of (U)LIRGs, as well as their individual relations with their host galaxies.

In this work, we study gas kinematics towards the galaxy Zw049.057 (IRAS 15107+0724). Zw049.057 is a LIRG, with luminosity $L_{\mathrm{IR}} = 1.8 \times 10^{11}$ L$_{\odot}$, located (\[RA, DEC\] (J2000) = \[15:13:13.10 +07:13:32.0\]) at an estimated distance of $56$ Mpc (cite: sanders:03) that hosts a CON (cite: aalto:15; falstad:21). We adopt a redshift of $z=0.01299$, which corresponds to a systemic velocity of $3897$ km s$^{-1}$ (cite: katgert:98). Throughout this paper the optical velocity convention is used with respect to the barycentric reference frame. It is an OHM galaxy (cite: baan:87; mcbride:13), with evidence of inflows (cite: falstad:15) and outflow structures (cite: baan:87; falstad:18), that are heavily obscured in the nuclear region (cite: falstad:19). The major axis of the nuclear disk has a position angle $\mathrm{PA}_{\mathrm{maj}}=210^{\circ}$ (cite: falstad:18). We present ALMA observations of the HCN $J=3 \to 2$ emission, that show signatures of a collimated outflowing structure, and e-MERLIN observations of OHM and H$_2$CO (formaldehyde) emission towards Zw049.057. We find evidence that the OHM emission is associated with an outflow structure, while population inversion, and thus the OHM emission, is suppressed in the nuclear disk region.

OH megamasers are hosted by (U)LIRGs, where they are commonly taken to represent a compact and intense mode of star formation, that is likely triggered by tidal density enhancements due to merger events (cite: darling:07; darling:02). The picture of (cite: darling:07) is indeed consistent with modeling efforts (cite: parra:05; lockett:08), as well as previous high angular resolution imaging of the more luminous OHM using Very Long Baseline Interferometry (VLBI) instruments (cite: lonsdale:98; pihlstrom:01; richards:05). This picture, though, is in tension with the association of OHM with an outflow structure; a feature of OHM that has been identified in an increasing number of sources (cite: baan:87; baan:89; gowardhan:18). We explore this tension in detail by comparing resolved e-MERLIN imaging of the H$_2$CO megamaser of Zw049.057 with the resloved imaging of the OHM, and analyzing their (diss)association on the basis of previous excitation modeling (cite: vanderwalt:07; vanderwalt:22; lockett:08), as well as the emerging picture of the inner dynamics of CON regions (cite: aalto:12; falstad:19; falstad:21; gorski:23).

This paper is structured as follows. In section 2, we present the observational set-ups that were used. In section 3, we describe the results of our observations. In section 4, we discuss our results, where we lay emphasis on the outflow dynamics, as well as the implication of our results for the class of OH megamasers. We present our conclusions in section 5.

# Observations

## e-MERLIN observations

Zw049.057 was observed with the e-MERLIN array between 7-14th January 2019 at L-band (project code CY7222) and 7-8th January 2018 at C-band (CY6203). Observations included all e-MERLIN Telescopes, except the Lovell Telescope (6 telescopes in total). L-band observations were correlated into eight 64-MHz wide spectral windows spanning a total frequency range of 1245-1757 MHz. At C-band observations encompassed 4488-5000 MHz, correlated into 4 spectral windows. A total of 17.25 and 14.8 hours of observations were used at L-band and C-band, respectively.

Correlators were set to the C-band 4829 MHz H$_2$CO $J_{K_aK_c}$=1$_{10}$-1$_{11}$-transition and to the L-band 1667 and 1665 MHz OH transitions. The flux calibrator was 3C286 and the baseline calibrator OQ208 for both sets of observations. Nearby gain calibrators 1516+0701 and 1513+0713 were used at L- and C-band respectively.

Data were initially processed using NRAO’s casa (cite: CASATeam2022PASP) using the e-MERLIN pipeline[^1] (cite: moldon:21) which applies flagging, delay and bandpass calibration, and calculates phase and frequency-dependent amplitude gain corrections. Following initial calibration observing bands centered on the redshifted frequencies of the OH (1665 and 1667 MHz rest frequency) and H$_2$CO (4830 MHz rest frequency) lines were extracted and imaged to form individual spectral line cubes for further analysis.

The synthesized beams are 0.11$''$$\times$0.039$''$ ($30 \times 11$ pc) for the H$_2$CO observations and 0.26$''$$\times$0.13$''$ ($70.6 \times 35.3$ pc) for the OH observations. The resulting data have a sensitivity of 0.2 mJy per beam in a 64 km s$^{-1}$ (1 MHz) channel width (H$_2$CO) and 0.77 mJy per beam in a 20 km s$^{-1}$ (0.11 MHz) channel width (OH).

## ALMA observations

Observations were carried out with 42 antennas in the array configuration C43-9/10, with projected baselines between 92 m and 13.8 km, on Aug 28, 2021. The on-source integration time was 34 minutes under relatively good atmospheric conditions (amount of precipitable water vapor $PWV \sim 0.5$ mm).

The bandpass response of the individual antennas was determined from the quasar $J$1550+0527. The quasar $J$1521+0420 was observed regularly for gain calibration. The absolute flux scale was calibrated using the quasar $J$1550+0527. The flux density for $J$1550+0527 was taken from the ALMA flux calibrator database.

The correlator was set up to cover four spectral windows in Band 6. The first two spectral windows were assigned to the upper side band, with bandwidths of 1.875 GHz and spectral resolution of 7.8 MHz, to cover the HCO$^+$ $J$=3$\to$2 and vibrationally excited HCN $J$=3$\to$2 $\nu_2$=1f lines (spectral window centered at sky frequency 264.3 GHz) and the HCN $J$=3$\to$2 line in the ground vibrational state (spectral window centered at 262.5 GHz). Two additional 2-GHz wide spectral windows were assigned to the lower side band, with a coarser spectral resolution of 31.25 MHz, to sample the continuum emission.

All of the ALMA Band 6 observations of Zw049.057 will be published in an upcoming paper by Wethers et al. (priv. com.). Here we present some results on HCN $J$=3 $\to$2.

The synthesized beam is 0.027$''$$\times$0.024$''$ ($7.33 \times 6.52$ pc), where Briggs weighting was used, adopting a robust parameter of 0.5. The resulting data have a sensitivity of 0.26 mJy per beam in a 20 km s$^{-1}$ (18 MHz) channel width.

# Results

## L band continuum

The L band continuum around $1.67$ GHz ($\lambda 18$ cm) was detected towards the nuclear region of Zw049.057; a contour map is given in Fig. [4](#fig:L_continuum). Continuum emission was found to exhibit extended features in the direction roughly perpendicular to the nuclear disk major axis, with position angle PA$_{\mathrm{C\ exten.}}=120^{\circ}$. The maximum flux density was observed as $21.5 \pm 0.4$ mJy beam$^{-1}$. We use the Rayleigh-Jeans law to obtain a corresponding brightness temperature of $3.25 \times 10^5$ K. The spatially integrated total flux density towards the nuclear region was $S_{\nu} = 41.4 \pm 4$ mJy, which can be compared to Arecibo single dish observations that retrieve an $18$ cm continuum flux of $40 \pm 5$ mJy (cite: baan:87). Half of the total continuum emission emanates from an (angular) area of $0.05\ \mathrm{arcsec}^2$ ($60$ pc$^2$). We note that this area is very similar to the area of emittance of 33 GHz continuum radiation, $A_{33\ \mathrm{GHz}}=0.031$ arcsec$^2$, as found by (cite: song:22).

![](./C_continuum_detail_sig.png)

![](H2CO_moment0_mas.png)

![](H2CO_moment1_mas.png)

![](L_continuum_detail_sig.png)

![](OH_moment0_mas.png)

![](OH_moment1_mas.png)

![](OH_moment2_mas.png)

![](HCN_moment0_withpath_mas.png)

![](HCN_moment1_mas.png)

![](HCN_pv_newcmp.png)

![](HCN_redlbue_smoothed_mas.png)

![](H2CO_OH_moment0_mas.png)

## OH megamaser (OHM)

|  | $I_{\nu,\mathrm{max}}$ (mJy beam$^{-1}$) $^{(a)}$ | $S_{\nu}$ (mJy) $^{(b)}$ | $\int dv S_{\nu}$ (Jy km s$^{-1}$) $^{(c)}$ |
|:---|:--:|:--:|:--:|
| L band cont. | $21.5 \pm 0.4$ | $41.4 \pm 4$ |  |
| OH | $6.50 \pm 0.77$ |  | $2.0 \pm 0.4$ |
| C band cont. | $12.0 \pm 0.1$ | $25.6 \pm 2$ |  |
| H$_2$CO | $1.1 \pm 0.2$ |  | $0.48 \pm 0.04$ |

**Notes:** $^{(a)}$maximal flux density, $^{(b)}$spatially integrated flux density, $^{(c)}$spatially and spectrally integrated flux density.

OHM emission was detected towards the nuclear region of Zw049.057 in both the $1.667$ GHz and the $1.665$ GHz transitions. For the main maser transition at $1.667$ GHz, we retrieved an integrated total flux of $2.0 \pm 0.4$ Jy km s$^{-1}$, while for the satellite maser transition at $1.665$ GHz, we retrieved $1.0 \pm 0.2$ Jy km s$^{-1}$. The total integrated flux of the $1.667$ GHz maser compares well to (cite: baan:87), who find 2.25 Jy km s$^{-1}$ and (cite: mcbride:13), who find 2.45 Jy km s$^{-1}$ [^2]. The integrated total flux corresponds to an OH luminosity of $L_{\mathrm{OH}}=10.1\ L_{\odot}$. Figure [5](#fig:OH_moment0) shows the moment 0 map of the $1.667$ GHz OHM emission. OHM emission is observed near the minor axis, with maximal emission appearing about 0.2$''$ ($\sim 57$ pc) from the $18$ cm continuum peak. The emission to the west of the continuum peak appears stronger, compared to the emission to the east of the continuum peak. Emission towards the nucleus, as well as along the major axis, is undetected. The moment 1 map of the $1.667$ GHz OHM emission, given in Fig. ([6](#fig:OH_moment1)) shows a clear velocity gradient, from $-20$ km s$^{-1}$ in the east, to $-100$ km s$^{-1}$ in the west (corresponding to about $5$ spectral channels). Within the NW OHM feature, a velocity gradient from the North to the South is observed, but we note that this feature occurs on a scale smaller than the beam size. The velocity dispersion, taken as the square root of the moment 2 map of the $1.667$ GHz OHM emission, given in Fig. ([7](#fig:OH_moment2)), appears constant around $70$ km s$^{-1}$ throughout the OHM region.

Imaging of the 1.665 GHz transition is given in Fig. ([20](#fig:OH_1665)). It is readily apparent that the NW feature of the OHM main line is found also for the weaker 1.665 GHz maser line; the moment 0 image shows a feature at a similar position, while the moment 1 map shows a similar velocity field compared to the main maser transition at 1.667 GHz. We do not detect the SE feature of the OHM emission. We ascribe this to sensitivity effects, as for the main maser line, this feature was also considerably weaker.

## C band continuum

The C band continuum around $4.8$ GHz ($\lambda 6.2$ cm) was detected towards the nuclear region of Zw049.057. In Fig. ([1](#fig:C_continuum)) we display a contour map of the C band continuum. As for the L band continuum, an extended structure appears present along the minor axis (P.A.$\sim 120^{\circ}$). The maximum spectral flux density we observed as $12.0 \pm 0.1$ mJy/beam, corresponding to a brightness temperature of $1.68 \times 10^5$ K. We retrieve an integrated total flux density towards the nuclear region was observed as $S_{\nu} = 25.6 \pm 2$ mJy, which compares well to the MERLIN observations of (cite: baan:17) that retrieved $29.72$ mJy, as well as the Arecibo observations of (cite: araya:04) that retrieved $30.8$ mJy. Half of the total e-MERLIN C band continuum emission emanates from an (angular) area of $0.008\ \mathrm{arcsec}^2$ ($20$ pc).

## H$_2$CO megamaser

H$_2$CO megamaser emission was detected towards the nucleus of Zw049.057 in the ($J_{K_a,K_c} \to J'_{K_a',K_c'}$) $1_{1,0} \to 1_{1,1}$ transition at $4.83$ GHz. Figs. ([2](#fig:H2CO_moment0)) and ([3](#fig:H2CO_moment1)) present the moment 0 and 1 maps of the detected emission, while a zoom-in of these figures can be found in Fig. ([17](#fig:H2CO_zoom)). Maximal emission was found at 1.08 mJy beam$^{-1}$, corresponding to $1.4\times 10^4$ K. We retrieved an integrated total flux of $0.48 \pm 0.04$ Jy km s$^{-1}$, where (cite: baan:17) finds $0.308$ Jy km s$^{-1}$ using MERLIN and (cite: araya:04) find $0.283$ Jy km s$^{-1}$ using Arecibo. From the integrated total flux we compute the corresponding maser luminosity $7.3\pm 0.6\ L_{\odot}$, which is large enough for it to fulfill the threshold to be considered megamaser emission[^3] Figure [2](#fig:H2CO_moment0) shows the moment 0 map of the $4.83$ GHz H$_2$CO emission. H$_2$CO emission is observed concentrated along the major axis (P.A.$\sim 210^o$, (cite: falstad:18)), with maximal emission appearing about

0.1$''$ ($\sim 29$ pc) NE of the $6.2$ cm continuum peak. Emission to the north of the $6.2$ cm continuum peak appears $\sim 25\%$ stronger than the emission to the south of the C band continuum peak. The moment 1 map of the emission, shown in Fig. ([3](#fig:H2CO_moment1)) shows a velocity gradient, red to blue, from the North to the South.

## HCN minor axis emission

The HCN $J=3 \to 2$ transition was detected toward the nucleus of Zw049.057. An image of the integrated intensity is given in Fig. ([8](#fig:HCN_0)). In the inner $50$ mas ($14$ pc) towards the nucleus, HCN is observed in absorption, while it is observed in emission farther out from the nucleus. Emission extends farther along the minor axis (P.A.$\sim 120^o$, (cite: falstad:18)), compared to the major axis (P.A.$\sim 30^o$, (cite: falstad:18)).

We analyzed the velocity structure of the minor axis emission using a position-velocity diagram (p-v diagram) of a strong feature along the minor axis. The position-slice is perpendicular to the minor axis, and indicated in Fig. ([8](#fig:HCN_0)), where the zero-offset position is marked with a blue cross. The p-v diagram is plotted in Fig. ([10](#fig:HCN_pv)). In the diagram, we observe a feature that presents a correlated position-velocity structure between $-150$ to $200$ km s$^{-1}$, and a feature that is associated with high-velocity emission $>200$ km s$^{-1}$, extending to $\sim 600$ km s$^{-1}$ where we observe emission concentrated around the central position. We indicated the high-velocity feature by a green marking. Interestingly, the emission of the feature between $-150$ to $200$ km s$^{-1}$ follows the profile of a skewed and shifted ellipse in PV-space. The ellipse, that was fitted by eye, is drawn in dashed blue in Fig. ([10](#fig:HCN_pv)), and is $120$ km s$^{-1}$ wide and $120$ mas high, shifted by $40$ km s$^{-1}$, and skewed by a velocity gradient of $0.5$  km s$^{-1}$ mas$^{-1}$.

Finally, we present in Fig. ([11](#fig:HCN_redblue)) an integrated intensity image of the high-velocity ($\pm 250$ km s$^{-1}$ $-$ $\pm 750$ km s$^{-1}$) emission. Both the blueshifted and the redshifted emission show an emission structure that is concentrated along the minor axis, consistent with the earlier discussed p-v diagram. We retrieved an integrated total flux of $12.7$ Jy km s$^{-1}$ for the redshifted high-velocity emission and $12.5$ Jy km s$^{-1}$ blueshifted high-velocity emission, but note that the integrated total flux of the blueshifted emission may be an overestimation due to contamination of the $4_{1,3} \to 3_{1,2}$ methanimine line (rest frequency $266.270024$ GHz) at $432$ km s$^{-1}$ with respect to the HCN $3\to 2$ rest frequency.

# Discussion

## HCN outflow

The HCN emission along the minor axis traces two distinct structures, as can be readily ascertained from Fig. ([10](#fig:HCN_pv)). We first discuss the low velocity feature, indicated in blue in [10](#fig:HCN_pv)). From the p-v diagram, emission could be extracted that appeared as a shifted, skewed ellipse (width: $120$ km s$^{-1}$, height: $120$ mas, shift: $40$ km s$^{-1}$, skew: $0.5$ km s$^{-1}$  mas$^{-1}$) in p-v space. We propose that this feature traces a rotating, wide-angle, and hollow, outflowing structure. The skew corresponds to a velocity gradient ($5.7 \times 10^{-14} \ \mathrm{s}^{-1}=1.8$ km s$^{-1}$  pc$^{-1}$) that is due to the outflow rotation. The width and shift of the ellipse are due to emission from the front- and back side of the outflow, with a velocity directed radially from (width, $\frac{1}{2} \times 120$ km s$^{-1}$$=60$ km s$^{-1}$) and along (shift, $40$ km s$^{-1}$), the outflow symmetry axis (cite: tabone:20). We considered the possibility that the blue side of the elliptical structure represents the rotating nuclear disk, but ruled out this scenario, as the elliptical structure is present also in minor axis p-v slices $>200$ mas, beyond the HCN disk radius of $\sim 150$ mas.

Both Figs. ([10](#fig:HCN_pv)) and ([11](#fig:HCN_redblue)) clearly indicate that the high-velocity emission emerges from a linear and confined structure. From its spatial and velocity structure, we interpret the high-velocity HCN emission along the minor axis as a fast collimated outflow. For the position angle of the collimated outflow we find $\mathrm{PA_{HCN}}=105^o$. Interestingly, this is the same as the position angle that (cite: falstad:18) find for the outflow traced by CO $J=6\to 5$ emission. (cite: falstad:18) find that the CO $J=6\to 5$ emission extends to $400$ km s$^{-1}$, less than the $\sim 600$ km s$^{-1}$ we find, but this discrepancy may be due to different excitation conditions or sensitivity effects. We propose the CO $J=6\to 5$ emission, observed by (cite: falstad:18) and the high-velocity HCN emission are tracing the same structure.

To estimate the mass of the fast collimated outflow, we extracted its luminosity and used the $L$(HCN) to $M$(dense) conversion relation of (cite: gao:04). We note that the conversion relation of (cite: gao:04) was derived for the HCN $1-0$ line; to convert our HCN $3 \to 2$ luminosity to an HCN $1-0$ luminosity, we assumed a HCN $\frac{J=3\to2}{J=1\to0}$ temperature ratio of $0.3$ (cite: krips:08). Accounting only for the red outflow ($12.7$ Jy km s$^{-1}$, $250-500$ km s$^{-1}$), this procedure yields a collimated outflow mass of $M_{\mathrm{HCN}}=6.2\times 10^7\ M_{\odot}$. We note that the conversion relation is derived for gravitationally bound gas, so the mass will be overestimated if the dense gas is in non self-gravitating clumps. (cite: aalto:15) studied the impact of turbulence on the conversion factor and found that it should be scaled down by about a factor of five for non self-gravitating gas in the outflow. Because of these uncertainties, we adopt $M_{\mathrm{HCN}}=1-6\times 10^7\ M_{\odot}$ in order to compute the outflow kinematics from our mass estimates. Furthermore, we put conservative estimates of $\sim 250$ km s$^{-1}$ and $30$ pc for the outflow velocity and size. Combined, we compute the mass-loss, momentum, momentum flux, energy and energy flux of the outflow as: $\dot{M}_{\mathrm{HCN}}=85.2-511\ \mathrm{M_{\odot}/yr}$, $p_{\mathrm{HCN}} = 2.5-15 \times 10^{9} \ \mathrm{M_{\odot} \,km /s}$, $\dot{p}_{\mathrm{HCN}} = 1.3-6.5\times 10^{12} \ \mathrm{L_{\odot}}/c$, $E_{\mathrm{HCN}} = 0.8-3.9 \times 10^{55} \ \mathrm{ergs}$ and $\dot{E}_{\mathrm{HCN}} = 0.5-2.7 \times 10^{9} \ \mathrm{L_{\odot}}$. We note that we have not included any energy contribution from gas dispersion in our estimates for the outflow energy. In terms of the IR luminosity of Zw049.057, we may put the moment flux and energy flux, $\dot{p}_{\mathrm{HCN}}/(L_{\mathrm{IR}}/c) \approx 7-34$ and $\dot{E}_{\mathrm{HCN}}/L_{\mathrm{IR}} \approx 0.003-0.015$. These are strikingly high yields for the momentum and energy fluxes. Compared to the sample of ULIRG outflows that (cite: gonzalez:17) analyzed, where outflow momentum and energy fluxes in the range of $2-5\ L_{\mathrm{IR}}/c$ and $0.1-0.3\%\ L_{\mathrm{IR}}$ were derived, both the energy and momentum fluxes of the outflow traced by HCN are at the higher end, or exceeding, the yields of the ULIRG outflows. We discuss this point in more detail in section [4.3](#sec:out_launch).

## OHM outflow

The OHM spatial and velocity structures, showing emission along the minor axis with a velocity gradient of $\sim 100$ km s$^{-1}$, red in the SE towards blue in the NW, are consistent with an outflowing structure. We rule out that the OHM is excited in the disk, as in this scenario maximal emission is expected towards the disk major axis (cite: pihlstrom:01; parra:05), opposite to what we observe. Indeed, with velocity dispersion of the order of the disk rotation (cite: falstad:18), the longest, velocity-coherent, columns of OH are expected towards the disk major axis, while Fig. ([1](#fig:C_continuum)) also shows significant seeding radiation to emerge therefrom. Yet no maser emission is observed from the disk, leading us to suggest that population inversion is suppressed there. While we cannot rule out that rotation contributes to the velocity profile of the OHM features, the observed velocity gradient cannot be explained by rotation alone. Finally, the evidence for outflowing structures emerging from the nuclear region in the HCN emission, including a structure that has similar kinematical properties as the features traced by the OHM, is additional circumstantial evidence that OHM is tracing an outflow structure. Thus, we interpret the OHM emission as emerging from an outflow structure.

We proceed to make kinematical estimates of the OHM outflow. In order to estimate the OHM outflow mass, we use the result that OHM operate around OH column densities of $N_{\mathrm{OH}}\sim 10^{17} \mathrm{cm}^{-2}$ (cite: lockett:08). We define the OHM emission region as the one where the spectrally integrated intensity exceeds $0.3\ \mathrm{Jy/beam}$ km s$^{-1}$, which has an angular area of $0.12 \ \mathrm{arcsec}^2$. Using an abundance of $x_{\mathrm{OH}} = 2 \times 10^{-6}$ (cite: gonzalez:12; gonzalez:17) relative to H$_2$, and an average particle mass of $\mu = 2.3 \ \mathrm{m_H}$, we compute the OHM outflow mass as $M_{\mathrm{OHM}} = 9 \times 10^6\ \mathrm{M_{\odot}}$. Adopting an outflow velocity of 50 km s$^{-1}$ and a size of 30 pc, the mass expulsion rate of the outflow is $\dot{M}_{\mathrm{OHM}} = 15\ \mathrm{M_{\odot} / yr}$. With these estimates, we compute the momentum, momentum flux, energy and energy flux of the outflow as: $p_{\mathrm{OHM}} = 8.8 \times 10^{46}$ g cm s$^{-1}$, $\dot{p}_{\mathrm{OHM}} = 3.7 \times 10^{10} \ \mathrm{L_{\odot}}/c$, $E_{\mathrm{OHM}} = 2.187 \times 10^{53}$ ergs and $\dot{E}_{\mathrm{OHM}} = 3.1 \times 10^6 \ \mathrm{L_{\odot}}$. In terms of the IR luminosity of Zw049.057, we may put the moment flux and energy flux, $\dot{p}_{\mathrm{OHM}}/(L_{\mathrm{IR}}/c) = 0.2$ and $\dot{E}_{\mathrm{OHM}}/L_{\mathrm{IR}} = 2 \times 10^{-6}$.

The OHM outflow velocity (50 km s$^{-1}$) is much less than the minimal velocity required to escape the inner region ($\sqrt{2}v_{\mathrm{circ}}\approx 200$ km s$^{-1}$, see, e.g. (cite: martin:05)). Indeed, as discussed in section [4.3](#sec:out_launch), the OHM outflow will likely fail to escape the inner region and will be obscured when observed in the IR range of the spectrum. Instead, the outflow will likely fall back onto the gas close to the nuclear region, causing a significant stirring of the nuclear gas (cite: aalto:20; wada:12). Not only will the nuclear gas be endowed an appreciable amount of kinetic energy in the form of turbulence, but the gas stirring will also impact the accretion dynamics significantly, as turbulence is directly related to the effective viscosity of the gas (cite: shakura:76; pringle:81). CON regions are consistently associated with nuclear gas velocity widths in excess of $100$ km s$^{-1}$. If this is dispersion, it would imply that the turbulent kinetic energy of the gas far exceeds the thermal energy: $E_{\mathrm{kin}}/E_{\mathrm{therm}}>10^4$. It may therefore well be possible, at least locally, that the conversion of turbulent energy through shocks may be a significant source of luminosity. We however note that the flows may still be largely laminar and that the high velocity widths are caused by line of sight effects of a layered structure of in- and outflows.

Spectroscopic IR observations, performed with Herschel, at 23 H$_2$O and 12 OH transitions, have not been able to definitively indicate the outflow we observe in the OHM emission (cite: falstad:15). This is partially due to resolution and the relatively low outflow velocity of the OH gas. But, also, and importantly, we find clear evidence that the OHM emission is excited only in the outflowing gas. Thus revealing a map of the outflowing gas that is relatively uncontaminated by the disk emission. While we present the first resolved interferometric maps of OHM in association with an outflow, spectral features that were offset in velocity gave early indications in single dish observations of Zw049.057 (cite: baan:87) and other OHM galaxies (cite: baan:89). Notably, through spectral analysis, (cite: gowardhan:18) were able to find striking evidence of the association of OHM with outflowing gas towards two ULIRGs, by combining unresolved OHM observations with interferometric imaging of CO and CN emission. In section [4.5.1](#sec:OH_exc) we discuss OHM tracing outflow structures in relation to their excitation conditions and often-observed association with H$_2$CO megamasers.

## Outflow launching

The kinematic estimates we presented above may help us to constrain the launching mechanism of the high-velocity collimated outflow and the slow wide-angle outflow. First, we consider the scenario of a radiatively driven outflow. Radiation pressure is a momentum conserving mechanism to launch the outflows. We compare the total momentum flux of the outflow components and relate it to the momentum flux that emanates from the nuclear region. For the OHM outflow, we estimated earlier $\dot{p}_{\mathrm{OHM}}/(L_{\mathrm{IR}}/c) = 0.04-0.2$, while for the collimated HCN outflow, we estimated $\dot{p}_{\mathrm{HCN}}/(L_{\mathrm{IR}}/c) \approx 7-34$. Thus, without a significant momentum boost, it is difficult to explain the collimated HCN outflow with a momentum conserving outflow launching mechanism.

It is possible for the wide-angle outflow to be radiatively driven. We explore the hypothesis that the slow wide-angle outflow traced by OHM is radiatively launched. First, the OHM clumps have significant column densities, that ensure continuum optical depths of order unity, even for long wavelengths. Indeed, with optical depths $\tau_{\mathrm{OHM}}\sim 1$ at $10 \, \mathrm{\mu m}$ (corresponding to the maximal specific intensity of thermal radiation of $\sim 300$ K), it is a possibility that the OHM clumps are lifted from the CON surface by the thermalized IR radiation field. At the instance of our observations, the OHM outflow has attained a (projected) velocity of $v_{\mathrm{OHM}} \approx 50$ km s$^{-1}$. It is interesting to speculate about the progression of the outflow launching, assuming it is radiatively driven. If the outflow is to be accelerated, we require the outward force on an OHM clump, that is due to the radiation field, to exceed the inward force due to gravity. We follow (cite: heckman:15) and define the outward force due to the radiation field as $F_{\mathrm{out}} = \dot{p}_{\mathrm{rad}} A_c / 4\pi r^2$, where $\dot{p}_{\mathrm{rad}}$ is the radiation momentum flux, $A_c$ is the cloud area and $r$ is the distance from the nucleus. The inward force due to gravity we put at $F_{\mathrm{in}}=M_{\mathrm{OHM}} v_{\mathrm{cir}}^2 / r$, where $M_{\mathrm{OHM}}$ is the OHM clump mass and $v_{\mathrm{cir}}$ is its circular velocity. The critical momentum flux to drive an OHM clump outwards can be obtained by equating the inward and outward forces and is $\dot{p}_{\mathrm{crit}} = 2.1 \times 10^{11} L_{\odot}/c \left(\frac{r}{30 \ \mathrm{pc}}\right) \left( \frac{N_{\mathrm{OHM}}}{3 \times 10^{22} \ \mathrm{cm}^{-2}}\right)\left(\frac{v_{\mathrm{circ}}}{140 \ \mathrm{km\ s}^{-1} } \right)^2$, adopting typical values for the OHM clumps that occur in the outflow as we observe it. Interestingly, the critical momentum flux is similar to $L_{\mathrm{IR}}/c$. This indicates that if the radiation is the driving agent, the OHM outflow is not accelerating. In fact, after numerical integration of the above equations, adopting the cited typical values for the OHM clumps that occur in the outflow as we observe it, we found that after $\sim 4\times 10^5$ years, the outflowing OHM clumps will acquire a negative velocity, indicating that they will evolve to fall back onto the galactic disk as a fountain flow (cite: wada:12).

The collimated HCN outflow requires a driving mechanism beyond radiation, due to the high momentum requirements. First, the possibility has been explored, that the molecular outflow of Zw049.057 as traced by CO $J=6\to 5$ emission, which is likely the same outflow as traced by the high-velocity HCN emission, is entrained by a radio jet (cite: falstad:18). Indeed, (cite: falstad:18) find that the radio continuum around 5.3 GHz shows an extended feature along the minor axis, and while this possible radio jet is not aligned with either the HCN or the CO outflow found by (cite: falstad:18), it may still have powered them and deflected. Based on the jet power estimate, $\dot{E}_{\mathrm{jet}}=4.7 \times 10^{9} \ L_{\odot} \approx \dot{E}_{\mathrm{HCN}}$ (cite: falstad:18; baan:06; birzan:08), we do not rule out the (tentatively detected) radio-jet as a driver of the dense collimated outflow, but we do note that our estimates for the energy flux are likely lower limits, as we have not included the velocity dispersion in the outflow energy estimate, and we use a projected velocity for the outflow velocity. Alternatively, the molecular outflow that we observe can be entrained by an energy driven AGN wind (cite: silk:98; aalto:12; aalto:15b). If this is the case, we expect the collimated outflow to be associated with an ionized and hot wind. In addition, in order for the molecular material not to be disrupted by the entrainment, rapid radiative cooling and/or stabilizing magnetic fields are required (cite: cooper:09; mccourt:15; leaman:19).

The projected outflow velocity of the dense collimated outflow traced by HCN was put at $>200$ km s$^{-1}$, with maximal projected velocities approaching $650$ km s$^{-1}$. These outflow velocities are comfortably larger than $\sqrt{2}v_{\mathrm{circ}}\approx 200$ km s$^{-1}$, suggesting that this outflow will escape the nuclear region. Outflow velocities in excess of $3v_{\mathrm{circ}}\approx 420$ km s$^{-1}$ are required to escape the galaxy (cite: martin:05), which thus appears to be the fate of a significant fraction of this outflow.

It has been suggested that the morphology and kinematics of CON regions resemble the protostellar environment (cite: aalto:20; gorski:23). In protostellar regions, outflows are thought to be launched magnetocentrifugally (cite: blandford:82; pelletier:92; wardle:93; spruit:96; tabone:20), and magnetically collimated. The outflow takes the appearance of a fast collimated jet-like structure, emerging from the inner launching regions, while towards the outer launching regions, a wide(r)-angle and lower velocity outflow emerges (cite: spruit:96; tabone:20). Such an appearance is both consistent with the dynamics and chemistry we find for our outflows, but we note that this mechanism operates most effectively when gas flows are laminar and critically depends on the presence of an ordered magnetic field.

Magnetic fields in cool molecular gas may either be probed through dust polarization observations (cite: andersson:15), or through spectral line polarization, either through the Zeeman effect (cite: crutcher:93; lankhaar:23) or through the Goldreich-Kylafis effect (cite: goldreich:81; lankhaar:20a). Unfortunately, continuum emission is heavily affected through self-absorption and scattering effects in buried regions (cite: gonzalez:19), even at (sub)millimeter wavelengths. With OHM tracing the outflow, observation of its circular polarization would lead to constraints on the magnetic field in these regions. Such extragalactic Zeeman observations of OHM have been performed previously (cite: robishaw:08), on a sample of OHM sources exhibiting strong emission. For the Zw049.057 OHM, with its modest intensity yields, Zeeman observations will require very deep integration, which would be beyond feasibility for the current radio telescopes, but may become possible with the next generation of radio observatories such as the SKA. Alternatively, it may be possible to attain magnetic field information towards the nuclear region through linear polarization observations of vibrationally excited HCN emission, that is known to be luminous (cite: falstad:21) and expected to be significantly polarized due to its radiative excitation (cite: lankhaar:20a; lankhaar:22a).

## Inner dynamics of Zw049.057

Based on the spatial and velocity signatures of the H$_2$CO megamaser, OH megamaser and HCN emission, as well as constraints from excitation modeling that we discuss in section [4.5.1](#sec:OH_exc), we propose the following model of the dense gas surrounding the nucleus of Zw049.057. Fig. ([14](#fig:cartoon_zw)) presents a cartoon of the dense gas surrounding the nucleus of Zw049.057. In this model the H$_2$CO megamaser is tracing the nuclear disk[^4]. The OH megamaser is not excited towards the nuclear disk, but rather, we propose, in a wide-angle and slow moving outflow structure. The OHM outflow envelopes a denser, faster, and collimated outflow that is traced by high-velocity HCN emission. This is likely the same outflow that (cite: falstad:18) detected in CO $J=6\to5$ emission at lower resolution. As discussed in section [4.3](#sec:out_launch), we estimate that the dense collimated outflow has likely attained sufficient velocity to escape, at least, the nuclear region. In contrast, the wide-angle outflow traced by the OH megamaser does not possess sufficient velocity to escape the nuclear region. Instead, we expect the wide-angle outflow to be drawn back to the nuclear disk after $\sim 1$ Myr to form a so-called fountain flow (cite: wada:12).

![](SA_Maser_v3.pdf)

## OH megamasers

### OH megamaser excitation

It is interesting to compare our observations of the $1.667$ GHz OHM to existing observations of OH towards Zw049.057. (cite: falstad:18) observed the OH $4.660$ GHz, $4.766$ GHz and $4.751$ GHz hyperfine transitions in absorption towards the nucleus of Zw049.057. Of these transitions, the $4.751$ GHz is the main hyperfine transition, while the transitions at $4.660$ GHz and $4.766$ GHz are satellite hyperfine transitions. The relative intensities of these three hyperfine transitions are (4.660:4.751:4.766) GHz = (1:2:1) in the optically thin limit, under local thermodynamic equilibrium (cite: destombes:77). The relative peak absorption of the lines follow the ratio expected under LTE. However, different line profiles were found among the transitions, which was interpreted as the result of OH gas that is excited under varying conditions, comprising the signal (cite: falstad:18). Furthermore, (cite: falstad:18) found that the spatially and kinematically resolved emission from the $4.751$ GHz transition, indicate that the dominant part of the emission emerges from a rotating structure along the major axis, while they found tentative evidence for a feature at $\sim 200$ km s$^{-1}$ to the northwest of the continuum peak. (cite: mcbride:13) observed the satellite transitions associated with the $1.67$ GHz OHM at $1.612$ and $1.712$ GHz using the Arecibo telescope. From the conjugate line profiles of the OHM satellite lines, they concluded that two separate inversion mechanisms exist in Zw049.057.

Earlier, we showed that the OHM appears in an outflowing structure along the galactic minor axis. The OH outflow appears to envelop a collimated and dense outflow traced by high-velocity HCN emission. While OH is observed towards the nuclear disk in its $6$ cm and far-IR lines (cite: falstad:15; falstad:18), we detect it there neither as a maser nor in absorption in the $1.667$ and $1.665$ GHz transitions. This, while H$_2$CO is observed as a megamaser in association with the nuclear disk. The combination of these observations confirms earlier conjectures, that distinct excitation mechanisms/regions exist for the OH emission towards Zw049.057 (cite: mcbride:13; falstad:18).

The presence and absence of OHM and H$_2$CO maser emission allows us to constrain the excitation conditions in the outflow and nuclear region of Zw049.057. It is well established that OH megamasers appear in association with FIR radiation around 53 $\mu \mathrm{m}$ absorbed through the OH $^{2}\Pi_{\frac{1}{2}}-$$^{2}\Pi_{\frac{3}{2}}$ $J=\frac{3}{2} - \frac{3}{2}$ transitions, that causes population inversion in the transitions around $1.67$ GHz through radiative pumping (cite: lockett:08). Population inversion is achieved in turbulent clumps ($\Delta v$$\sim 20$ kms$^{-1}$) of sizes $\lesssim$ 1 pc, number densities $\lesssim 10^5$ cm$^{-3}$ and specific OH column densities of the order $10^{16} \ \mathrm{cm}^{-2} \mathrm{km}^{-1} \mathrm{s}$. For such clumps, maser optical depths $\tau_{1.667\ \mathrm{GHz}} \sim -1$ are expected (cite: lockett:08). A bright (non-thermal) background radiation field around $18$ cm wavelengths is required for OH megamasers to be apparent, while multiple maser clumps along the line-of-sight may boost the amplification of this background radiation significantly (cite: parra:05). Detailed modeling of the excitation of H$_2$CO masers finds that the $4.8$ GHz H$_2$CO maser is excited towards denser regions $\gtrsim 10^{5} \ \mathrm{cm}^{-3}$, where the maser pumping is collisional (cite: vanderwalt:22). Maser pumping can operate in environments with a prominent FIR radiation field, provided the gas temperature exceeds the radiation temperature (cite: vanderwalt:22). A rather restrictive constraint that (cite: vanderwalt:22) put to the operation of H$_2$CO masers, is that it requires H$_2$CO to be present in high abundance ($x_{\mathrm{H_2CO}} \sim 10^{-5}$). Such H$_2$CO abundances are $3$ to $4$ orders of magnitude higher than what is typically found towards Galactic star forming regions, hot cores or dark clouds (cite: mangum:93; tang:18; kirsanova:21). We note, that the abundance constraint was formulated for H$_2$CO masers excited towards high-mass star-forming regions. For H$_2$CO megamasers, velocity-coherence length scales, $\ell$, can be two orders of magnitude higher, while line-widths, $\Delta v$, are one order of magnitude higher. Thus, taking into consideration that (large-velocity gradient) radiative transfer problems depend primarily on the specific column density, $x_{\mathrm{H_2CO}} n_{\mathrm{H}_2} \ell / \Delta v$, the abundance requirements are relaxed by about an order of magnitude. Still, taking this into consideration, H$_2$CO abundance requirements seem too high, and we suggest dedicated modeling of H$_2$CO megamaser sources is required to address this issue.

We suggest that the absence of OH emission or absorption around $1.67$ GHz in the nuclear disk is the consequence of the high densities in these regions, that effectively suppress the maser mechanism. Instead, because of the outflow expansion, OH clumps in the outflow structure are more tenuous, allowing thus for efficient maser pumping. In addition, for the OHM to operate, one requires efficient FIR pumping. The FIR radiation in the OH outflow may either emerge from the CON region, or from the collimated denser part of the outflow that is traced by high-velocity HCN emission, and which the OH outflow envelops. While the CON region subtends a large solid angle as seen from the OH outflow, absorption may diminish its prominence. On the other hand, considering the lifetime ($\sim 10^5$ years) of the collimated outflow, we require a mechanism such as star formation in this region to heat up the dust phase, to account for the emergence of FIR radiation here from.

### The class of OH megamasers and CONs

A synthesis of the OHM surveys by (cite: baan:89b) and (cite: darling:02) and the host galaxy IR, CO and HCN luminosities, indicate an association between OHM and high molecular gas densities and fractions, as well as an unusual IR-CO luminosity relation (cite: darling:07). On the basis of this, it is suggested that OHM are associated with a compact and intense mode of star formation, that is likely triggered by tidal density enhancements due to merger events (cite: darling:07). This picture is consistent with modeling efforts (cite: parra:05; lockett:08), and are not in tension with previous high resolution imaging of the OHM using VLBI instruments (cite: lonsdale:98; pihlstrom:01; richards:05), that were performed on, primarily, the more luminous OHM. However, our high-resolution observations of the OHM emission that show the association with an outflowing structure towards the LIRG Zw049.057, require a more subtle picture of the class of OHM.

We pointed out earlier that Zw049.057 is a CON, a subclass of (U)LIRGs that host exceptionally dense nuclear regions and are associated with both inflow and outflow motions. While only a small fraction ($\lesssim 10\%$) of LIRGs, and up to a third of ULIRG galaxies host OHM (cite: darling:02), almost all LIRG and ULIRG CON galaxies that have been searched for OHM emission, indeed host OHM. At first, this is not surprising, as OHM are associated with high density gas (cite: darling:07), and show prominent absorption in OH around $53 \ \mathrm{\mu m}$, which is a requisite for OH maser pumping (cite: gonzalez:12; gonzalez:15). Yet, of the known H$_2$CO megamasers, 5/6 are hosted by CONs, of which 1 of them is a ULIRGs (Arp 220) and the 4 others are LIRGs (IC 860, UGC 5101, IRAS 17578–0014, Zw049.057), where each of them is additionally associated with OH maser emission. The association of the OHM with H$_2$CO megamaser appears problematic, as only very limited conditions allow for the simultaneous excitation of both H$_2$CO and OH megamasers. Our high-resolution interferometric observations show that the issue of the apparent association between OHM and H$_2$CO megamaser emission can be resolved, as they emerge from different regions; outflow (OHM) and nuclear disk (H$_2$CO megamaser) structures. We speculate that a similar arrangement may be present for the other LIRGs that host OH and H$_2$CO megamaser.

## OH megamasers at high redshift

With this expected surge in OHM detections in distant galaxies, it is natural to discuss the implications of the current study. From the interferometric mapping of the OHM towards Zw049.057, our main finding is its association with an outflow, and the suppression of emission towards the nuclear disk. The outflow traced by OHM is expanding at a low velocity ($\sim 100$ km/s), making it difficult to detect spectroscopically. This is in contrast to other studies that have associated OHM with outflows (cite: baan:89; gowardhan:18; glowacki:22), that found OHM emission at large ($200-1000$ km/s) offsets from the systemic velocity. The luminosity of the OHM of Zw049.057 ($10.1\pm 2.0\ L_{\odot}$) is on the lower end of the range of OHM luminosities. This feature can be ascribed to (i) Zw049.057 being a LIRG, with a naturally weaker radio-continuum that is to be amplified by OHM, (ii) the slight offset of the OHM from the continuum maximum, and (iii) the relatively small region that is conducive to population inversion. In particular, points (ii) and (iii) are a direct consequence of OHM tracing an evolved outflowing structure.

A useful feature of the untargeted HI surveys, is their broadband scanning. Thus, it is likely that for an OHM galaxy, not only the main OHM lines at $1.67$ GHz will be detected, but also satellite transitions at 1612 and 1720 MHz. A comprehensive analysis of the different transitions can reveal properties of the (pumping) conditions towards the OHM galaxy (cite: baan:87). Such an analysis has already been productively applied by (cite: hess:21) to an OHM found in the HI survey AWES (Apertif Wide-area Extragalactic imaging Survey). For Zw049.057, analysis of the OHM lines and their satellites, revealed the presence of different pumping conditions for the OHM; a feature which we can confirm through our interferometric observations. Multi-line analysis of the OHM lines and their satellites will reveal important information on the pumping conditions, but to formulate rigorous relations that reveal the OHM association with an outflow, more interferometric studies such as this one are necessary. To direct additional interferometric studies, we have pointed to H$_2$CO megamaser emission as a marker for OHM galaxies with OHM emission tracing outflow structures, similar to Zw049.057.

# Conclusions

We present high-angular resolution interferometric observations of the kinematics of the nuclear region of Zw049.057. Using e-MERLIN, we observed the H$_2$CO and OH megamasers, and using ALMA, we observed HCN $3\to2$ emission. The H$_2$CO megamaser traces the nuclear disk, while the OH megamaser traces a slow and wide-angle outflow. The slow and wide-angle OHM outflow in turn appears to envelop a fast and collimated outflow that is traced by high-velocity HCN emission.

Momentum estimates indicate that the OH megamaser outflow may be radiatively launched, while the fast and collimated molecular outflow traced by HCN requires an additional momentum boost. Such a momentum boost may be achieved if the outflow is entrained by an energy-conserving AGN wind, or through a magneto-hydrodynamical launching mechanism. From the low velocity of the OHM outflow and an analysis of the driving forces, we conclude that the wide-angle OHM will likely not reach escape velocity, and instead evolve as a fountain flow.

We observed the H$_2$CO and OH megamaser to be associated with different physical structures. The excitation of OH and H$_2$CO megamasers require different conditions, that are almost mutually exclusive, yet of the known H$_2$CO megamasers, all of them have been found towards OH megamaser galaxies. Additionally, five of the six known H$_2$CO megamasers are found towards CONs. Since the prime characteristic of CONs is dense nuclear gas, and they are commonly associated outflow systems, we speculate that a similar arrangement can be expected for the OH-H$_2$CO (hydroxyl-formaldehyde) megamaser galaxies.

Our high-angular resolution interferometric observations have revealed multiple phases of outflowing gas emanating from the inner ($\lesssim 10$ pc ), and obscured ($N_{\mathrm{H}_2} \sim 10^{25}$ cm$^{-2}$), nuclear regions of Zw049.057. While the ultimate driving mechanisms of the outflowing gas phases remain ambiguous, it is clear that they impact the gas dynamics and mass and angular momentum budget of the nuclear region greatly.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01612.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. BL acknowledges support for this work from the Swedish Research Council (VR) under grant number 2021-00339. S.A., C.W., M.G. and C.Y gratefully acknowledges support from an ERC AdvancedGrant 789410. CR acknowledges support from Fondecyt Regular grant 1230345 and ANID BASAL project FB210003. J.M. acknowledges financial support from the grant CEX2021-001131-S funded by MCIU/AEI/ 10.13039/501100011033 from the grant PID2021-123930OB-C21 funded by MCIU/AEI/ 10.13039/501100011033 and by “ERDF A way of making Europe”. We thank the anonymous refere for constructive feedback that improved the quality of the paper.

77 natexlab

(ref: aalto:20) Aalto, S., Falstad, N., Muller, S., et al. 2020, Astron. Astrophys., 640, A104

(ref: aalto:15b) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2015a, Astron. Astrophys., 574, A85

(ref: aalto:12) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012, Astron. Astrophys., 537, A44

(ref: aalto:15) Aalto, S., Martı́n, S., Costagliola, F., et al. 2015b, Astron. Astrophys., 584, A42

(ref: aalto:19) Aalto, S., Muller, S., König, S., et al. 2019, Astron. Astrophys., 627, A147

(ref: andersson:15) Andersson, B., Lazarian, A., & Vaillancourt, J. E. 2015, Annu. Rev. Astron. Astrophys., 53, 501

(ref: araya:04) Araya, E., Baan, W. A., & Hofner, P. 2004, Astrophys. J. Supp. S., 154, 541

(ref: baan:06) Baan, W. & Klöckner, H.-R. 2006, Astron. Astrophys., 449, 559

(ref: baan:89b) Baan, W. A. 1989, Astrophys. J., 338, 804

(ref: baan:17) Baan, W. A., An, T., Klöckner, H.-R., & Thomasson, P. 2017, Mon. Not. R. Astron. Soc., 469, 916

(ref: baan:89) Baan, W. A., Haschick, A. D., & Henkel, C. 1989, Astrophys. J., 346, 680

(ref: baan:87) Baan, W. A., Henkel, C., & Haschick, A. D. 1987, Astrophys. J., 320, 154

(ref: barcos:18) Barcos-Muñoz, L., Aalto, S., Thompson, T. A., et al. 2018, Astrophys. J. Lett., 853, L28

(ref: CASATeam2022PASP) Bean, B., Bhatnagar, S., Castro, S., et al. 2022, Publ. Astron. Soc. Pac., 134, 114501

(ref: birzan:08) Bı̂rzan, L., McNamara, B., Nulsen, P., Carilli, C., & Wise, M. 2008, Astrophys. J., 686, 859

(ref: blandford:82) Blandford, R. & Payne, D. 1982, Mon. Not. R. Astron. Soc., 199, 883

(ref: cooper:09) Cooper, J. L., Bicknell, G. V., Sutherland, R. S., & Bland-Hawthorn, J. 2009, Astrophys. J., 703, 330

(ref: crutcher:93) Crutcher, R., Troland, T., Goodman, A., et al. 1993, Astrophys. J., 407, 175

(ref: darling:07) Darling, J. 2007, Astrophys. J., 669, L9

(ref: darling:02) Darling, J. & Giovanelli, R. 2002, Astron. J., 124, 100

(ref: destombes:77) Destombes, J. L., Marliere, C., Baudry, A., & Brillet, J. 1977, A&A, 60, 55

(ref: donnan:23) Donnan, F., Rigopoulou, D., Garcı́a-Bernete, I., et al. 2023, Astron. Astrophys., 669, A87

(ref: falstad:21) Falstad, N., Aalto, S., König, S., et al. 2021, Astron. Astrophys., 649, A105

(ref: falstad:18) Falstad, N., Aalto, S., Mangum, J., et al. 2018, Astron. Astrophys., 609, A75

(ref: falstad:15) Falstad, N., González-Alfonso, E., Aalto, S., et al. 2015, Astron. Astrophys., 580, A52

(ref: falstad:19) Falstad, N., Hallqvist, F., Aalto, S., et al. 2019, Astron. Astrophys., 623, A29

(ref: gao:04) Gao, Y. & Solomon, P. M. 2004, Astrophys. J. Supp. S., 152, 63

(ref: garcia:22) Garcı́a-Bernete, I., Rigopoulou, D., Aalto, S., et al. 2022, Astron. Astrophys., 663, A46

(ref: glowacki:22) Glowacki, M., Collier, J. D., Kazemi-Moridani, A., et al. 2022, Astrophys. J. Lett., 931, L7

(ref: goldreich:81) Goldreich, P. & Kylafis, N. D. 1981, Astrophys. J., 243, L75

(ref: gonzalez:12) González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2012, Astron. Astrophys., 541, A4

(ref: gonzalez:17) González-Alfonso, E., Fischer, J., Spoon, H., et al. 2017, Astrophys. J., 836, 11

(ref: gonzalez:15) González-Alfonso, E., Fischer, J., Sturm, E., et al. 2015, Astrophys. J., 800, 69

(ref: gonzalez:19) González-Alfonso, E. & Sakamoto, K. 2019, Astrophys. J., 882, 153

(ref: gorski:23) Gorski, M., Aalto, S., König, S., et al. 2023, Astron. Astrophys., 670, A70

(ref: gowardhan:18) Gowardhan, A., Spoon, H., Riechers, D. A., et al. 2018, Astrophys. J., 859, 35

(ref: heckman:15) Heckman, T. M., Alexandroff, R. M., Borthakur, S., Overzier, R., & Leitherer, C. 2015, Astrophys. J., 809, 147

(ref: hess:21) Hess, K. M., Roberts, H., Dénes, H., et al. 2021, Astron. Astrophys., 647, A193

(ref: hughes:98) Hughes, D. H., Serjeant, S., Dunlop, J., et al. 1998, nature, 394, 241

(ref: katgert:98) Katgert, P., Mazure, A., Den Hartog, R., et al. 1998, Astron. Astrophys. Supp. S., 129, 399

(ref: kirsanova:21) Kirsanova, M. S., Punanova, A. F., Semenov, D. A., & Vasyunin, A. I. 2021, Mon. Not. R. Astron. Soc., 507, 3810

(ref: konigl:94) Konigl, A. & Kartje, J. F. 1994, Astrophys. J., 434, 446

(ref: krips:08) Krips, M., Neri, R., Garcı́a-Burillo, S., et al. 2008, Astrophys. J., 677, 262

(ref: lankhaar:23) Lankhaar, B. & Teague, R. 2023, Astron. Astrophys., 678, A17

(ref: lankhaar:20a) Lankhaar, B. & Vlemmings, W. 2020, Astron. Astrophys., 636, A14

(ref: lankhaar:22a) Lankhaar, B., Vlemmings, W., & Bjerkeli, P. 2022, Astron. Astrophys., 657, A106

(ref: leaman:19) Leaman, R., Fragkoudi, F., Querejeta, M., et al. 2019, Mon. Not. R. Astron. Soc., 488, 3904

(ref: lockett:08) Lockett, P. & Elitzur, M. 2008, Astrophys. J., 677, 985

(ref: lonsdale:98) Lonsdale, C. J., Lonsdale, C. J., Diamond, P. J., & Smith, H. E. 1998, Astrophys, J., 493, L13

(ref: mangum:93) Mangum, J. G. & Wootten, A. 1993, Astrophys. J. Supp. S., 89, 123

(ref: martin:05) Martin, C. L. 2005, Astrophys. J., 621, 227

(ref: mcbride:13) McBride, J., Heiles, C., & Elitzur, M. 2013, Astrophys. J., 774, 35

(ref: mccourt:15) McCourt, M., O’Leary, R. M., Madigan, A.-M., & Quataert, E. 2015, Mon. Not. R. Astron. Soc., 449, 2

(ref: moldon:21) Moldon, J. 2021, Astrophysics Source Code Library, ascl

(ref: parra:05) Parra, R., Conway, J., Elitzur, M., & Pihlström, Y. 2005, Astron. Astrophys., 443, 383

(ref: pelletier:92) Pelletier, G. & Pudritz, R. E. 1992, Astrophys. J., 394, 117

(ref: pihlstrom:01) Pihlström, Y., Conway, J., Booth, R., Diamond, P., & Polatidis, A. 2001, Astron. Astrophys., 377, 413

(ref: pringle:81) Pringle, J. 1981, Annu. Rev. Astron. Astrophys., 19, 137

(ref: richards:05) Richards, A., Knapen, J., Yates, J., et al. 2005, Mon. Not. R. Astron. Soc., 364, 353

(ref: robishaw:21) Robishaw, T. & Heiles, C. 2021, in The WSPC Handbook of Astronomical Instrumentation: Volume 1: Radio Astronomical Instrumentation (World Scientific), 127–158

(ref: robishaw:08) Robishaw, T., Quataert, E., & Heiles, C. 2008, Astrophys. J., 680, 981

(ref: sakamoto:13) Sakamoto, K., Aalto, S., Costagliola, F., et al. 2013, Astrophys. J., 764, 42

(ref: sanders:03) Sanders, D., Mazzarella, J., Kim, D.-C., Surace, J., & Soifer, B. 2003, Astron. J., 126, 1607

(ref: sanders:96) Sanders, D. & Mirabel, I. 1996, Annu. Rev. Astron. Astrophys., 34, 749

(ref: shakura:76) Shakura, N. & Sunyaev, R. 1976, Mon. Not. R. Astron. Soc., 175, 613

(ref: silk:98) Silk, J. & Rees, M. J. 1998, Astron. Astrophys., 331, L1

(ref: smail:97) Smail, I., Ivison, R., & Blain, A. 1997, Astrophys. J., 490, L5

(ref: song:22) Song, Y., Linden, S. T., Evans, A. S., et al. 2022, ApJ, 940, 52

(ref: spruit:96) Spruit, H. C. 1996, arXiv preprint astro-ph/9602022

(ref: tabone:20) Tabone, B., Cabrit, S., Des Forêts, G. P., et al. 2020, Astron. Astrophys., 640, A82

(ref: tang:18) Tang, X., Henkel, C., Wyrowski, F., et al. 2018, Astron. Astrophys., 611, A6

(ref: vanderwalt:22) van der Walt, D. & Mfulwane, L. 2022, Astron. Astrophys., 657, A63

(ref: vanderwalt:07) van Der Walt, D., Sobolev, A., & Butner, H. 2007, Astron. Astrophys., 464, 1015

(ref: veilleux:20) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, Astron. Astrophys. Rev., 28, 1

(ref: wada:12) Wada, K. 2012, Astrophys. J., 758, 66

(ref: wardle:93) Wardle, M. & Koenigl, A. 1993, Astrophys. J., 410, 218

(ref: wethers:24) Wethers, C. F., Aalto, S., Privon, G. C., et al. 2024, Astron. Astrophys., 683, A27

# Additional figures

![](H2CO_moment0_mas_zoom.png)

![](H2CO_moment1_mas_zoom.png)

![](OH_1665_moment0_mas.png)

![](OH_1665_moment1_mas.png)

[^1]: https://github.com/e-merlin/e-MERLIN_CASA_pipeline

[^2]: We note (cite: mcbride:13) report an integrated flux $4.9$ Jy km s$^{-1}$. However, as explained in (cite: mcbride:13) they use a different definition of the total flux density resulting in a factor two increase in the reported flux density compared to commonly used definitions including those used in this paper.

    For a deeper discussion surrounding this topic, we refer to (cite: robishaw:21).

[^3]: Typical galactic H$_2$CO masers have luminosities $\lesssim 10^{-6}\ L_{\odot}$.

[^4]: Our imaging of H$_2$CO maser emission towards Zw049.057 agrees very well with the imaging performed by (cite: baan:17) using MERLIN. Yet, (cite: baan:17) find for other H$_2$CO megamaser galaxies other configurations of H$_2$CO maser emission, that does not seem to be tracing exclusively the nuclear disk. In the absence of interferometric data to a larger sample of H$_2$CO megamaser galaxies, we do not intend to make the general claim that H$_2$CO megmaser emission traces the nuclear disk of the host galaxy.

</paper>

Write the methods card for this paper.