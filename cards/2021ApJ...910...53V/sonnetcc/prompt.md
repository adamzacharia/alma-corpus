# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...910...53V\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...910...53V",
 "title": "A Massive, Clumpy Molecular Gas Distribution and Displaced AGN in Zw 3146",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Vantyghem, A. N.",
 "n_authors": 11,
 "arxiv_id": "2102.02300",
 "doi": "10.3847/1538-4357/abe306",
 "alma_projects_linked_by_archive": [
  "2018.1.01056.S"
 ]
}
```

Paper text:
<paper>
# A Massive, Clumpy Molecular Gas Distribution and Displaced AGN in Zw 3146

## Abstract

We present a recent ALMA observation of the CO(1-0) line emission in the central galaxy of the Zw 3146 galaxy cluster ($z=0.2906$). We also present updated X-ray cavity measurements from archival *Chandra* observations. The $5\times 10^{10}\,M_{\odot}$ supply of molecular gas, which is confined to the central 4 kpc, is marginally resolved into three extensions that are reminiscent of the filaments observed in similar systems. No velocity structure that would be indicative of ordered motion is observed. The three molecular extensions all trail X-ray cavities, and are potentially formed from the condensation of intracluster gas lifted in the wakes of the rising bubbles. Many cycles of feedback would be require to account for the entire molecular gas reservoir. The molecular gas and continuum source are mutually offset by 2.6 kpc, with no detected line emission coincident with the continuum source. It is the molecular gas, not the continuum source, that lies at the gravitational center of the brightest cluster galaxy. As the brightest cluster galaxy contains possible tidal features, the displaced continuum source may correspond to the nucleus of a merging galaxy. We also discuss the possibility that a gravitational wave recoil following a black hole merger may account for the displacement.

# Introduction

Galaxy clusters are permeated by a hot ($10^7-10^8\rm\; K$), diffuse intracluster medium (ICM) that shines brightly in X-rays. In cool core galaxy clusters the central density is sharply peaked at the position of the brightest cluster galaxy (BCG). The correspondingly high X-ray luminosity in the cluster core should result in the ICM condensing into clouds of cold, molecular gas and forming stars at rates of hundreds to thousands of solar masses per year (cite: Fabian94; Peterson06). Indeed, the BCGs in cool core clusters are the largest and most luminous elliptical galaxies in the Universe. They are burgeoning with star formation proceeding at rates of $\sim 1-500\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ (cite: mcn04; ODea08; McDonald11; Donahue15; Tremblay15; McDonald18), host luminous emission-line nebulae (cite: Lynds70; Heckman81; Cowie83; Hu85; Crawford99), and harbour molecular gas reservoirs more massive than even gas-rich spiral galaxies, sometimes exceeding $10^{10}\hbox{$\rm\thinspace M_{\odot}$}$ (cite: Edge01; Edge02; Edge03; Salome03). These signatures of gas condensation are prevalent in systems whose central cooling times fall below a sharp threshold of $1\rm\; Gyr$ (cite: Cavagnolo08; Rafferty08; Pulido18). Nevertheless, they account for less than 10% of what would be expected from an unimpeded cooling flow.

Active galactic nuclei (AGN) feedback regulates the rate of ICM cooling (cite: McNamara07; McNamara12; Fabian12). The “radio-mode” of AGN feedback is nearly ubiquitous in giant ellipticals and galaxy clusters with short central cooling times (cite: Burns90; Dunn06; Best07; Birzan12). Radio jets launched by the central AGN inflate bubbles, drive shock fronts, and generate sound waves in the hot atmosphere (cite: mcn00; Churazov00; Churazov01; Blanton01; Fabian06). The sizes and surrounding pressures of radio bubbles, which manifest as cavities in the X-ray surface brightness, are used in a direct estimate of the AGN power output. In a large sample of objects, the AGN power output closely matches the radiative losses from the surrounding ICM (cite: Birzan04; Dunn06; Rafferty06; Nulsen09). This, along with the preponderance of systems with central cooling times $<1\rm\; Gyr$, implies that AGN heating and radiative cooling are coupled in a long-lived feedback loop.

In order to establish and maintain such a feedback loop, radiative losses in the ICM must be tied to accretion onto the central supermassive black hole (SMBH). Molecular gas is the most likely intermediary. Overdensities in the ICM, generated by turbulence or AGN feedback, rapidly condense into a multiphase atmosphere that is dominated by molecular gas (cite: Sharma12; McCourt12; Gaspari13; Gaspari17a; Li14a; Voit18). Ram pressure and collisions between cold clouds are both effective mechanisms for driving cold clouds toward the galactic center (cite: Pizzolato05; Pizzolato10). This results in “chaotic cold accretion” (cite: Gaspari13), where the stochastic production of cold clouds feeds black hole growth and regulates the feedback loop between ICM cooling and AGN heating.

Though molecular gas is the fuel for AGN feedback, its distribution is also shaped by the AGN. Radio jets drive fast outflows of ionized, neutral, and molecular gas on $\rm\; pc$ to $\rm\; kpc$ scales (cite: Morganti05; Morganti13; Nesvadba06; Alatalo11; Dasyra11; Sturm11; Tadhunter14; Morganti15). A gentler coupling between AGN feedback and molecular gas is observed in BCGs (cite: Olivares19; Russell19). The rotationally-supported disks that would be expected from the long-lived accumulation of molecular clouds in the galactic center are rare (cite: Hamer14; Russell19). Instead, billions of solar masses of cold gas are situated in kpc-scale filaments that trail X-ray cavities (cite: Salome06; Salome08; Lim08; Lim12; McDonald12; mcn14; Russell14; Russell16; Russell17; Russell17b; Vantyghem16; Vantyghem18; Vantyghem19). The detection of redshifted absorption lines indicates that some of this gas rains back onto the central galaxy in a circulation flow (cite: David14; Tremblay16; Tremblay18; Rose19a; Rose19b; Rose20).

Motivated by these observations, (cite: mcn16) proposed the “stimulated feedback” paradigm (cite: Revaz08). As radio bubbles rise buoyantly, they uplift low-entropy ICM from the cluster core to an altitude where it becomes thermally unstable. The cold clouds decouple from the radio bubbles and fall back onto the central galaxy as in chaotic cold accretion. In this way, AGN feedback stimulates the production of its own fuel.

Mapping the spatial distribution of cold gas in BCGs in all but the closest and most gas-rich systems has only become possible with the arrival of the Atacama Large Millimeter Array (ALMA). Here we present a new ALMA observation targeting the CO(1-0) emission line in the BCG of Zw 3146, which is one of the most extreme cool core clusters and brightest CO emitters known. If left unimpeded, its soft ($0.1-2.4\rm\; keV$) X-ray luminosity of $2\ensuremath{\times 10^{45}}\hbox{$\rm\; erg\rm\; s^{-1}\,$}$ (cite: Ebeling98; Bohringer00) would lead to a mass deposition rate of $1250\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ (cite: Edge94). Indeed, the BCG in Zw 3146 is exceptionally active, showing a blue continuum and luminous nebular emission lines (cite: Allen92; Hicks05), an infrared luminosity of $4\ensuremath{\times 10^{11}}\hbox{$\rm\thinspace L_{\odot}$}$ (cite: Egami06), an $8\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ reservoir of cold molecular gas (cite: Edge01; Edge03), and strong molecular H$_2$ emission lines from $\sim10^{10}\hbox{$\rm\thinspace M_{\odot}$}$ of warm H$_2$ (cite: Egami06b). The infrared luminosity implies a star formation rate of $\sim 70\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ (cite: Egami06; Edge10; Hicks10; Hoffer12).

Spectroscopic measurements indicate that the true mass deposition rate is much lower than implied by the X-ray luminosity (cite: Egami06). Any continuous radiative cooling flow from the bulk temperature at $4\rm\; keV$ to $0.01\rm\; keV$ is less than $50\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ (Liu et al. in preparation, see also (cite: Liu19)). The rate of gas cooling to $0.7\rm\; keV$ is $130\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$, with less than $78\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ cooling to lower temperatures. AGN feedback is likely responsible for the heavily suppressed cooling rate. The X-ray atmosphere hosts several cavities that replenish energetic losses at a rate of $\sim6\ensuremath{\times 10^{45}}\hbox{$\rm\; erg\rm\; s^{-1}\,$}$ (cite: Rafferty06). The combination of a massive reservoir of molecular gas and powerful AGN feedback make Zw 3146 a prime candidate to contain molecular filaments trailing X-ray cavities, as observed in other BCGs.

Throughout this work we assume a standard $\Lambda$-CDM cosmology with $H_0=70\hbox{$\hbox{$\rm\; km\rm\; s^{-1}\,$}\rm\; Mpc^{-1}\,$}$, $\Omega_{{\rm m}, 0}=0.3$, and $\Omega_{\Lambda, 0}=0.7$. At the redshift of Zw 3146 ($z=0.29007$), the angular scale is $1''=4.35\rm\; kpc$ and the luminosity distance is $1500\rm\; Mpc$.

# Observations and Data Reduction

The BCG of the ZwCl 3146 galaxy cluster (2MASX J10233960+0411116 – R.A.: 10:23:39.6340, decl.: +4:11:10.660) was observed with ALMA in Band 3 (Cycle 4, ID 2018.1.01056.S, PI Vantyghem), centered on the CO(1-0) line at $89.316\rm\; GHz$. The observations were conducted in three blocks from 15-19 August 2019, with a total on-source integration time of 106 minutes. Each observing block was split into $\sim6$ minute on-source integrations interspersed with observations of the phase calibrator. The 69.2 arcsec primary beam was centered on the BCG nucleus in a single pointing common to each observing block. 41-44 antennas were used in these observations, with baselines ranging from $41$ to $3637\rm\; m$. This corresponds to a maximum recoverable scale of $10''$. A single spectral window in the frequency division correlator mode was used to study the CO spectral line with 1.875 GHz bandwidth and 488 kHz ($1.6\hbox{$\rm\; km\rm\; s^{-1}\,$}$) frequency resolution, though the data were later smoothed to a coarser velocity grid. An additional three basebands with the time division correlator mode, each with a 2 GHz bandwidth and frequency resolution of $15.625\rm\; MHz$, were employed in order to measure the continuum source.

The observations were calibrated in casa version 5.4.0 (cite: casa) using the pipeline reduction scripts. Continuum-subtracted data cubes were created using uvcontsub and clean. Additional phase self-calibration was attempted, but the continuum source was too faint to provide an improvement in signal-to-noise. Images of the line emission were reconstructed using Briggs weighting with a robust parameter of 0.5. The final CO(1-0) data cube had a synthesized beam of $0.30\times0.26$ arcsec (P.A. $-79.5^{\circ}$) and was binned to a velocity resolution of $20\hbox{$\rm\; km\rm\; s^{-1}\,$}$. The RMS noise in line-free channels was $2.4\rm\; mJy~{\rm beam}^{-1}$.

## Systemic Velocity

The gas velocities presented in this work are measured in the molecular gas rest frame. This was determined by extracting a spectrum from a $3''\times 3''$ region that encompasses all of the observed line emission, as shown in Fig. [1](#fig:spectrum). A single-gaussian fitted to the spectrum yields a molecular gas redshift of $0.29007\pm0.00003$. This is consistent with the CO(1-0) velocity centroids measured in previous work (cite: Edge01).

Previous works on Zw 3146 generally adopted a redshift of $0.29060\pm0.00010$, which was determined from the emission-line nebula (cite: Allen92). The molecular gas rest frame is blueshifted by $158\pm30\hbox{$\rm\; km\rm\; s^{-1}\,$}$ from this nebular redshift. The discrepancy may originate from differences in the distribution of gas traced by each observation. The molecular gas is confined to the central few kpc of the BCG, while nebular emission is present on larger scales.

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Region | $\chi^2/$dof | Velocity Center | FWHM | Integrated Flux$^{\dagger}$ | Gas Mass$^{\dagger}$ |
|  |  | ($\hbox{$\rm\; km\rm\; s^{-1}\,$}$) | ($\hbox{$\rm\; km\rm\; s^{-1}\,$}$) | ($\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$) | ($10^8\hbox{$\rm\thinspace M_{\odot}$}$) |
| All Emission | 221.2/197 | $0.0\pm10$ | $353\pm24$ | $2.78\pm0.17$ | $504\pm30$ |
| Central Clump | 226.3/197 | $-59.6\pm8.2$ | $265\pm19$ | $0.201\pm0.013$ | $36.4\pm2.3$ |
| Clump 1 | 224.0/197 | $17.2\pm6.1$ | $177\pm14$ | $0.289\pm0.02$ | $52.7\pm3.7$ |
| Clump 2 | 221.6/197 | $28\pm12$ | $288\pm28$ | $0.429\pm0.036$ | $78.3\pm6.7$ |
| Clump 3 | 218.6/197 | $-69\pm17$ | $415\pm41$ | $0.46\pm0.04$ | $83.7\pm7.1$ |

Notes: All spectra have been corrected for the response of the primary beam and instrumental broadening.\

# Results

![](all_emission_plot.pdf)

## Molecular Gas Mass

The integrated flux ($S_{\rm CO}\Delta v$) of the CO(1-0) line can be converted to molecular gas mass through (cite: Solomon87; Solomon05; Bolatto13) $$\begin{equation}
M_{\rm mol} = 1.05\ensuremath{\times 10^{4}} \frac{X_{\rm CO}}{X_{\rm CO, gal}} 
\left(\frac{S_{\rm CO}\Delta v~D_L^2}{1+z}\right)\hbox{$\rm\thinspace M_{\odot}$},
\label{eqn:Mmol}
\end{equation}$$ where $z$ is the redshift of the source, $D_L$ is the luminosity distance in Mpc, and $S_{\rm CO}\Delta v$ is in $\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$. The CO-to-H$_2$ conversion factor, $X_{\rm CO}$, has been studied extensively in the local Universe. Its nominal value is the mean empirically-derived Galactic value, $X_{\rm CO, gal} = 2\ensuremath{\times 10^{20}}\hbox{$\rm\; cm^{-2}\,$}(\rm\; K\hbox{$\rm\; km\rm\; s^{-1}\,$})^{-1}$ (cite: Bolatto13).

Lacking an independent calibration of $X_{\rm CO}$ in BCGs, we follow standard practice by adopting the Galactic value throughout this work. The only estimate of $X_{\rm CO}$ in a BCG was obtained recently through the detection of $^{13}$CO(3-2) emission in RXJ0821.0+0752 (cite: Vantyghem17). As $^{13}$CO is an optically thin emission line, it provided a direct measurement of the $^{13}$CO column density. In combination with a measurement of CO(1-0) and CO(3-2) line intensities and a number of assumptions, $X_{\rm CO}$ was estimated to be half of the Galactic value. This is reassuringly close to the Galactic value given the significant morphological differences between BCGs and the Milky Way disk. Until a direct calibration in BCGs is available, we continue to follow the standard practice of adopting the Galactic $X_{\rm CO}$.

The primary reasons for the CO-to-H$_2$ conversion factor to vary between galaxies are the gas metal abundance and excitation conditions. In metal-poor dwarf galaxies $X_{\rm CO}$ is elevated by more than an order of magnitude because CO traces a smaller fraction of the overall H$_2$ distribution (cite: Bolatto13). The molecular gas in BCGs likely forms by condensation of the hot atmosphere, which has typical metallicities of $\sim0.6-0.8\hbox{$\thinspace \mathrm{Z}_{\odot}$}$ (cite: DeGrandi01; DeGrandi04). The metal abundance of molecular clouds in BCGs is therefore expected to be similar to that of the Milky Way.

$X_{\rm CO}$ is driven downward by factors of $\sim5$ in starbursts (e.g. Ultra-Luminous Infrared Galaxies; ULIRGs), where the hot, dense molecular gas has an elevated luminosity per unit mass. BCGs also have high star formation rates, approaching $1000\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ in the most extreme cases (cite: McDonald12Phoenix). However, the molecular gas in BCGs is often distributed over much larger spatial scales than in ULIRGs, where the gas is confined to the central kpc. Despite their elevated SFRs, BCGs still lie on the Kennicutt-Schmidt relation (cite: Kennicutt98; Kennicutt12) alongside normal galaxies (cite: mcn14; Russell14; Vantyghem18).

The SFR in Zw 3146, $70\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ (cite: Egami06), is comparable to other BCGs for which the Galactic $X_{\rm CO}$ has been adopted. However, Zw 3146 is also the most luminous and distant H$_2$ emitter observed, with a line luminosity of $L[{\rm H}_2\ 0-0\ S(3)]=6.1\ensuremath{\times 10^{42}}\hbox{$\rm\; erg\rm\; s^{-1}\,$}$ (cite: Egami06). A cosmic-ray dominated region or excitation through shocks driven by the AGN may be required to explain such strong rotational H$_2$ lines (cite: Ferland09; Bayet10; Guillard12). This could impact the value of $X_{\rm CO}$. Strong H$_2$ line emission is observed in many cool core clusters (cite: Donahue11) and radio galaxies (cite: Ogle10).

A spatially-integrated CO(1-0) spectrum was extracted from a $13\times 13\rm\; kpc$ ($3''\times 3''$) box containing all of the detected line emission. The spectrum, shown in Fig. [1](#fig:spectrum), is best-fit by a single Gaussian with total flux $2.78\pm0.17\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$. This corresponds to $5.05\pm0.50\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas. A list of all fitted parameters is provided in Table [\[tab:spectra\]](#tab:spectra). No other CO(1-0) line emission was detected throughout the $70''$ primary beam of these observations.

Previous single-dish and interferometric radio observations of Zw 3146 with the IRAM-30m telescope and Owens Valley Radio Telescope (OVRO) yielded CO(1-0) integrated fluxes of $5.2\pm1.2\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ and $5.7\pm0.9\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$, respectively (cite: Edge01; Edge03). Our ALMA observation recovers 50% of this flux; a similar fraction to other BCGs (cite: David14; Russell14; mcn14; Vantyghem18).

The line emission in the OVRO observations, which recovers all of the single-dish flux, is unresolved by the $6.7'' \times 4.7''$ beam. This suggests that our ALMA observations are missing large-scale flux, predominantly on scales of $\sim5''$ ($22\rm\; kpc$).

![image](xray.pdf) ![image](CO10_totalflux.pdf)

![image](optical.pdf) ![image](ly-alpha.pdf) ![image](fuv.pdf)

## Molecular Gas Distribution and Kinematics

![image](CO10_20kmps_1comps_10kiter_shift_center1_plot.pdf) ![image](CO10_20kmps_1comps_10kiter_fwhm1_plot.pdf)

Maps of integrated flux, velocity, and FWHM of the CO(1-0) line were created by fitting the spectra extracted from individual pixels within the data cube. Each spectrum was averaged over a box the size of the synthesized beam. We allowed for the possibility of multiple coincident velocity structures by fitting each spectrum with up to two Gaussian components. The significance of each velocity component was tested using a Monte Carlo analysis employing 10000 iterations, with a detection requiring $5\sigma$ significance. The presence of one component was required before attempting to fit a second. We found that a single Gaussian component was sufficient to accurately model the spectrum for each pixel. Instrumental broadening has been incorporated into the model.

The integrated flux map is presented in the lower left panel of Fig. [2](#fig:comparison), and the velocity centroid and full-width at half maximum (FWHM) maps are presented in Fig. [3](#fig:maps). The molecular gas distribution is compact, with all of the detected gas confined to a $1''$ ($4.35\rm\; kpc$) radius. It is marginally resolved into three extensions to the NE, SE, and W. These extensions do not exhibit any clear velocity gradients. The emission is at its most blueshifted ($-150\hbox{$\rm\; km\rm\; s^{-1}\,$}$) at the central peak and in the farthest extent of the SE extension. The NE and W extensions have more moderate velocities ($0$ to $50\hbox{$\rm\; km\rm\; s^{-1}\,$}$), but the velocity transition to the central value occurs over the span of about a beam, so it is likely the result of the resolution element smearing two distinct velocities together. The linewidths, which range from $100$ to $400\hbox{$\rm\; km\rm\; s^{-1}\,$}$ FWHM, are broader than those seen along filaments in other systems ($<100\hbox{$\rm\; km\rm\; s^{-1}\,$}$) (cite: Russell16; Vantyghem16; Vantyghem18), consistent with a superposition of gas structures at a range of velocities.

*Chandra* X-ray, *HST* WFPC2 F606W, Ly-$\alpha$ (*HST* ACS/SBC F140LP), and FUV (*HST* ACS/SBC F165LP) images (cite: ODea10; Tremblay15) are shown alongside the CO(1-0) total flux map in Fig. [2](#fig:comparison). The box in the X-ray image corresponds to the fields-of-view for the *HST* images, while the ALMA field-of-view is shown in the *HST* images. The central galaxy contains bright knots of nebular emission and FUV flux from recent star formation, one of which is coincident with the molecular gas. A brighter Ly-$\alpha$ and FUV peak is located $3.25\rm\; kpc$ ESE of the molecular gas peak. No molecular gas is present at this position; the CO emission truncates where the Ly-$\alpha$ and FUV fluxes begin to increase. Dust attenuation may account for this anti-correlation between the molecular gas and FUV emission. Features that may be indicative of a merger remnant are seen in the *HST* F606W image. The most prominent clumps and filament are identified in Fig. [2](#fig:comparison). However, this filter also includes H$\beta$ and \[OIII\] line emission, which may account for some of the observed features.

The molecular gas is offset by $10\rm\; kpc$ to the south of the peak in X-ray emission, which itself does not coincide with structure at any other wavelength. The bright X-ray emission in the cluster core arcs around the position of the CO(1-0) peak. In addition, the X-ray atmosphere contains a series of depressions that likely correspond to cavities inflated by the central AGN (see Section [3.5](#sec:cavities)).

![](CO10_20kmps_1comps_10kiter_beamsub_plot.pdf)

The molecular extensions can be better visualized by subtracting the contribution from an unresolved point source coincident with the CO(1-0) peak. This is shown in Fig. [4](#fig:beamsub). First we created an image of the beam centered on the pixel with the largest integrated flux. This image was further convolved with a beam-shaped tophat kernel, as the pixel-based spectral fitting used to create the maps extracts the emission from a region of this shape. The image was then scaled to match the flux of the brightest pixel and subtracted from the integrated flux map. The unresolved emission subtracted from the integrated flux map amounted to 22% of the total flux.

![image](clump1_plot.pdf) ![image](clump2_plot.pdf) ![image](clump3_plot.pdf)

The resulting map shows that the gas morphology is separated into the three extensions, although none of them are resolved. They have been identified in Fig. [4](#fig:beamsub). The corresponding spectra are shown in Fig. [5](#fig:clump_spectra), and their spectral fits are listed in Table [\[tab:spectra\]](#tab:spectra).

![](sed.pdf)

## Millimetre Continuum

An image of the continuum at $96.193\rm\; GHz$ ($3.1166\rm\; mm$) was created by imaging the line-free channels in a square region measuring $40''$ on each side. A single, unresolved source was identified (R.A.: 10:23:39.5948, decl.: +4:11:11.032), which had a total integrated flux density of $133\pm13 \rm\; \mu Jy$. The contours for this source are shown in red Fig. [2](#fig:comparison). These contours begin at $3\sigma$, where $\sigma=7.45\hbox{$\rm\; \mu Jy\rm\; beam^{-1}\,$}$, and increase in $4\sigma$ steps. A two-dimensional gaussian fit to the continuum flux yielded an accuracy for the centroid of $0.006$ arcseconds. We searched for, but did not detect, evidence for absorption against the continuum source using the native velocity resolution of the observations.

In Fig. [6](#fig:sed) we plot the ALMA continuum alongside flux measurements at lower frequencies, which were obtained from either the VLA or BIMA (cite: Egami06; Coble07; Giacintucci14). Error bars are included, but are smaller than the markers for all measurements except those provided in this work. The spectral energy distribution (SED) is best fit by a power law with spectral index[^1] $\alpha = 0.685\pm0.063$, which is a typical value for an AGN (cite: Hogan15a).

![](decals.pdf)

## The Molecular Gas-AGN Offset

As is evident in Fig. [2](#fig:comparison), the molecular gas and continuum source are mutually offset. The two peaks are $2.6\rm\; kpc$ ($0.6''$) apart, and only a minimal overlap is present in the fainter reaches of the two distributions. This offset cannot originate from a phase calibration issue, as the continuum and line measurements are obtained from the same observation.

Independent observations of the radio continuum at lower resolution confirm the position of the $\rm\; mm$ continuum source identified here. In a VLA 4.9 GHz observation the continuum centroid is $0.3''$ SSW of the ALMA continuum source (cite: ODea10). Though the coarse resolution ($1.4''\times 0.9''$) prevents the CO(1-0) centroid and continuum source from being definitively distinguished, the VLA centroid is closer to the ALMA continuum position. Note that the VLA coordinates were reported in the B1950 equinox, so have been converted to J2000. (cite: Giacintucci14) also report a continuum centroid corresponding to VLA 4.9 and 8.5 GH observations in the C configuration. The position is consistent with the location of the ALMA continuum source, although no uncertainties are provided and the beam sizes are larger. Nevertheless, these independent radio observations indicate that the ALMA continuum position reported here is likely accurate.

The stellar continuum is difficult to disentangle from nebular emission in the HST images. In order to determine the position of the galactic center, we obtained a Dark Energy Camera Legacy Survey (*DECaLS*) $r$-band image using the legacy skyviewer[^2], which is shown in Fig. [7](#fig:decals). This image is uncontaminated by nebular line emission and stellar features from a merger remnant, providing a smooth tracer of the stellar continuum. Contours of molecular line emission and continuum source are overlaid in blue and red, respectively, in Fig [7](#fig:decals), along with black contours tracing the stellar emission. It is the molecular gas that is coincident with the galactic center, not the continuum emission from the AGN.

All taken together, these results imply that the molecular gas resides at the galactic center while the continuum source is offset by $2.6\rm\; kpc$. The molecular gas is coincident with both the stellar centroid and bright knots of nebular emission and star formation, while the continuum position is consistent with independent measurements at lower frequencies. This correspondence spanning multiple types of observations indicates that the astrometry of the ALMA observation is reliable. We explore possible physical interpretations for this offset in Section [4.1](#sec:offsetorigin).

## X-ray Cavities

In order to investigate any possible connection between the molecular gas and X-ray cavities, we present a new search for cavities in Zw 3146 using the *Chandra* data reduced by (cite: Hogan17a) and (cite: Pulido18). The $0.5-7\rm\; keV$ X-ray surface brightness image is shown in Fig. [2](#fig:comparison). In addition, we have processed this image using the gaussian gradient magnitude algorithm (cite: Sanders16a; Sanders16b) with a radially-dependent filtering kernel. This algorithm enhances edges in surface brightness. The resulting image is shown in Fig. [8](#fig:ggm), sharing a field-of-view with the X-ray image in Fig. [2](#fig:comparison). The X-ray atmosphere contains a series of surface brightness depressions and edges corresponding to X-ray cavities and cold fronts, respectively (cite: Forman02; Rafferty06).

![](xray_ggm.pdf)

We manually identified six candidate X-ray cavities using a combination of the GGM filtered image and original X-ray image. The sizes were determined qualitatively by estimating the size of the surface brightness depressions, using the edges identified in the GGM image as a guide. The cavities are shown and labelled in Fig. [8](#fig:ggm). Two cavities were previously reported by (cite: Rafferty06), though their work used a shallower X-ray image. Judging from the radial distances and sizes of these cavities, one corresponds directly to Cavity "A". The other cavity reported by Rafferty et al. is identified as two in our work – "B" and "C". Cavity "D" is located close to the cluster center and may correspond to motions unrelated to AGN activity, but we tabulate its derived properties nonetheless. Cavities "E" and "F" are located outside of a cold front and are less well-defined than their counterparts.

A list of all cavity parameters can be found in Table [\[tab:cavities\]](#tab:cavities). A qualitative figure of merit (FOM), which describes a cavity’s contrast with its surroundings, was provided for each cavity (cite: Rafferty06). High contrast cavities (${\rm FOM}=1$) are surrounded by bright rims, medium contrast (${\rm FOM}=2$) are partially surrounded by bright rims, and low contrast (${\rm FOM}=3$) have no or faint rims. All necessary thermodynamic quantities were obtained by interpolating the deprojected radial profiles from (cite: Pulido18). Note that the proximity of cavity D to the cluster center has a strong systematic effect on the cavity age, and therefore its power. The cluster centroid was determined from an aperture with a $20''$ ($87\rm\; kpc$) radius. It is offset from the X-ray peak by $6\rm\; kpc$.

The enthalpy required to inflate a cavity filled with relativistic gas is given by $E_{\rm cav}=4pV$, where $p$ is the cavity pressure and $V$ is its volume. The cavity was assumed to be in pressure balance with the surrounding gas. The confining pressure was interpolated from the deprojected pressure profile to a radius equal to the distance to the cavity center ($R$).

The cavity volume was estimated as the geometric mean of the volumes of oblate and prolate geometries, with semiaxes $a$ and $b$ matching those of the fitted ellipse, so that $V=\frac{4}{3}\pi(ab)^{3/2}$. This is equivalent to assuming that the length of the semiaxis along the line-of-sight is $r=\sqrt{ab}$. The uncertainty for each cavity volume was determined in two ways. First, a $15\%$ uncertainty was assumed in both $a$ and $b$ and propagated. Second, we used the prolate and oblate geometries as measures of the minimum and maximum volumes, respectively. The volume uncertainty was then taken to be the difference between maximum (minimum) volume and cavity volume, in absolute value. This evaluates to a fractional uncertainty of $\sqrt{a/b}-1$ for an oblate geometry and $1-\sqrt{b/a}$ for prolate, which are respectively the positive and negative errors. This is the dominant uncertainty when $a/b \geq 1.74$ when compared to a $15\%$ uncertainty in both $a$ and $b$.

The cavity age was estimated using both the sound crossing time and buoyant rise time (cite: Birzan04). The sound crossing time, which assumes the cavity rises at the speed of sound ($c_s$), is simply a function of ICM temperature, and is given by $$\begin{equation}
t_{c_s} = R/c_s = R\sqrt{\mu m_H / \gamma kT},
\end{equation}$$ where $\gamma=5/3$ is the ratio of specific heats for an ideal gas, and $\mu=0.6$ is the mean particle weight for the ICM. The buoyant rise time is the time taken for the cavity to rise to its current projected distance at its terminal velocity ($v_t$), $$\begin{equation}
t_{\rm buoy} = R/v_t \simeq R\sqrt{SC/2gV}.
\end{equation}$$ Here $C=0.75$ is the drag coefficient (cite: Churazov01) and $S$ is the bubble cross-section, which is assumed to be its projected area. The acceleration under gravity at radius $R$ was determined using the cluster mass profile from (cite: Pulido18). The two timescales agree to within $20\%$ for all cavities. The buoyancy time was used to determine the mean cavity power, $P_{\rm cav} = E_{\rm cav}/t_{\rm buoy}$.

These quantities were then used to place mass constraints on the AGN outbursts. The first, $M_{\rm acc} = E_{\rm cav}/\epsilon c^2$, is the mass that must be accreted onto the black hole to fuel the outburst at an efficiency of $\epsilon$, which we assume to be $0.1$. The total accreted gas mass of $4.6\ensuremath{\times 10^{7}}\hbox{$\rm\thinspace M_{\odot}$}$ can easily be supplied by the observed $5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas. The corresponding accretion rate, $\dot{M}_{\rm acc}=P_{\rm cav}/\epsilon c^2$, ranges from $\sim 0.1-0.3\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ for each cavity. The other interesting mass is that of hot gas displaced by the cavities, as this mass dictates the maximum mass that can be lifted by the cavities. The mass of displaced gas is given by $M_{\rm disp} = n\mu m_H V$, where $n=n_e+n_H$ is the density of the surrounding gas. Each of the three larger cavities can lift a few $10^{10}\hbox{$\rm\thinspace M_{\odot}$}$, so the observed molecular gas supply could have been lifted by the cavities.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Cavity | FOM$^a$ | Major | Minor | $R$ | $4pV$ | $t_{cs}$ | $t_{\rm buoy}$ | $P_{\rm cav}$ | $M_{\rm acc}$ | $\dot{M}_{\rm acc}$ | $M_{\rm disp}$ |
|  |  | $\rm\; kpc$ | $\rm\; kpc$ | $\rm\; kpc$ | $10^{58}\rm\; erg$ | $\rm\; Myr$ | $\rm\; Myr$ | $10^{44}\hbox{$\rm\; erg\rm\; s^{-1}\,$}$ | $10^{6}\hbox{$\rm\thinspace M_{\odot}$}$ | $\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ | $10^{10}\hbox{$\rm\thinspace M_{\odot}$}$ |
| A | 1 | $21.1$ | $15.3$ | $41.7$ | $161^{+58}_{-56}$ | $38^{+3.2}_{-2.5}$ | $41.2\pm2.8$ | $12.4^{+4.6}_{-4.4}$ | $9.02^{+3.3}_{-3.1}$ | $0.219^{+0.081}_{-0.077}$ | $2.69\pm0.85$ |
| B | 2 | $22.2$ | $16.3$ | $38.5$ | $214^{+77}_{-74}$ | $34^{+2.8}_{-2.2}$ | $36.3\pm2.4$ | $18.7^{+6.9}_{-6.6}$ | $12^{+4.3}_{-4.2}$ | $0.33\pm0.12$ | $3.35\pm1.1$ |
| C | 2 | $30$ | $15.2$ | $70$ | $204^{+86}_{-68}$ | $57.5^{+3.2}_{-2.6}$ | $71.2^{+4.4}_{-4.3}$ | $9.08^{+3.9}_{-3.1}$ | $11.4^{+4.8}_{-3.8}$ | $0.16^{+0.068}_{-0.054}$ | $2.76^{+1.1}_{-0.88}$ |
| D | 1 | $9.01$ | $6.72$ | $7.65$ | $30.6\pm11$ | $8.81^{+0.7}_{-0.59}$ | $6.68^{+0.62}_{-0.6}$ | $14.5^{+5.5}_{-5.3}$ | $1.71^{+0.63}_{-0.61}$ | $0.257^{+0.097}_{-0.094}$ | $0.815\pm0.26$ |
| E | 3 | $20.6$ | $11.7$ | $47.5$ | $86.6^{+31}_{-29}$ | $45.2^{+2.9}_{-2.3}$ | $52.1\pm3.3$ | $5.27^{+1.9}_{-1.8}$ | $4.85^{+1.7}_{-1.6}$ | $0.0931^{+0.034}_{-0.032}$ | $1.58^{+0.52}_{-0.5}$ |
| F | 3 | $22.3$ | $14.2$ | $70$ | $118^{+40}_{-39}$ | $57.5^{+3.2}_{-2.6}$ | $77.9^{+4.8}_{-4.7}$ | $4.8\pm1.6$ | $6.61\pm2.2$ | $0.0847\pm0.029$ | $1.6\pm0.51$ |

Notes: $^{a}$ The cavity figure of merit, which is a qualitative measure of the contrast between a cavity and its surroundings: (1) high contrast, bright rim surrounds cavity; (2) medium contrast, bright rim partially surrounds cavity; and (3) low contrast, no rim, or faint rim surrounds cavity.

# Discussion

## Origin of the Molecular Gas-AGN Offset

As discussed in Section [3.4](#sec:offset), the molecular gas and continuum source are mutually offset. The molecular gas resides at the galactic center, while the continuum source is located $2.6\rm\; kpc$ to the NW. In this Section we discuss potential causes for this offset. The first two attribute the continuum emission to a source other than the SMBH of the BCG, namely emission from a single lobe of a radio jet or the nucleus of a secondary galaxy. The latter two – gravitational wave recoil and acceleration by an asymmetric radio jet – are mechanisms that would naturally kick or accelerate the black hole from the galactic center.

Offsets between SMBHs and their galactic centers have been observed in other systems (cite: Bartlett20). Most common are the $\sim10-100\rm\; pc$ displacements, which are consistent with an oscillating SMBH following a gravitational wave recoil (cite: Lena14). M87 is an example of such a system, as its SMBH is offset from the photo-center by $6.8\rm\; pc$ (cite: Batcheldor10). More exceptional displacements are also observed. The radio-loud quasar 3C 186, for example, harbors an $11\rm\; kpc$ displacement with a corresponding velocity of $-2170\hbox{$\rm\; km\rm\; s^{-1}\,$}$ (cite: Chiaberge17).

### Emission from a lobe

Instead of originating from the supermassive black hole’s accretion disk, the detected continuum emission could instead originate from the lobe of a radio jet. This would naturally explain the offset, although it requires that the emission from both the core and a second lobe are undetected. Given the RMS in the continuum image of $7.5\hbox{$\rm\; \mu Jy\rm\; beam^{-1}\,$}$, any source brighter than $22.5\rm\; \mu Jy$ would be detected in our observations.

The continuum emission, with a spectral index of $0.7$, is consistent with originating from an AGN. Spectral indices steeper than $0.5$ are generally associated with non-cores, which include lobes, mini-halos, and relics (cite: Hogan15a). If the continuum emission arises from a radio lobe, then it is poorly associated with the X-ray cavities. The continuum emission that would correspond to the putative lobe is located NW of the galactic center, while the most prominent cavities are either to the SE or SW. Cavity D is coincident with the continuum emission, although its overlap with the galactic center makes it difficult to interpret the direction in which the jet would have been launched.

### The SMBH of a secondary galaxy

The spatially offset continuum emission could also originate from the SMBH in a secondary galaxy that is projected near the BCG core. This SMBH could either be in an independent background galaxy or the center of a galaxy merging with the BCG.

The probability that the continuum source is a chance alignment with an unrelated background radio source is low, based on our estimates of the source density of radio continuum sources at 100 GHz. Lacking a $100\rm\; GHz$ survey sensitive enough to detect the source density down to $0.13\rm\; mJy$, we have instead used a $31\rm\; GHz$ survey of known extragalactic sources (cite: Mason09). A source density of $16.7\deg^{-2}$ is appropriate for sources with flux densities $\geq 1\rm\; mJy$ at $31\rm\; GHz$, which translates to a flux of $0.6\rm\; mJy$ at $100\rm\; GHz$, assuming a spectral index of 0.4 (cite: Marriage11). We then randomly populated 1000 fields each with a source density of $16.7\deg^{-2}$. This exercise results in a probability of $1.2\ensuremath{\times 10^{-6}}$ that two sources are separated by $<0.6''$. While our assumed density is based on a flux limit of $1\rm\; mJy$, which is higher than the Zw 3146 continuum source flux ($0.133\rm\; mJy$), the actual source density would need to be several orders of magnitude larger to exceed a probability of close but random coincidence of even a few percent.

The likelihood that the continuum source originates from the core of a merger remnant is much higher. Clumps and trails possibly corresponding to stellar emission from a merger remnant are detected in the *HST* F606W image (Fig. [2](#fig:comparison)). H$\beta$ and \[Oiii\] line emission may also contribute to these features. Unlike in systems with dual nuclei, we do not detect excess optical emission at the position of the continuum source. A similar conclusion was drawn in Zw 8193, where the unresolved radio emission is offset from the center of the BCG by 3 arcsec and may be associated with a merging galaxy (cite: ODea10).

### Gravitational wave recoil

As two galaxies merge, their black holes migrate toward the center of the gravitational potential through dynamical friction (cite: Begelman80). The resulting binary system tightens through interactions with nearby stars or gravitational drag from gas until the SMBHs eventually coalesce (cite: Merritt05; Mayer07). During the final stage of coalescence, the anisotropic emission of gravitational waves imparts a recoil velocity to the coalesced object (cite: Gonzalez07; Campanelli07). This “kick” can in rare circumstances be as large as $4000\hbox{$\rm\; km\rm\; s^{-1}\,$}$, so can result in large displacements between the resulting SMBH and the galactic center.

When a SMBH experiences a large recoil ($v_{\rm kick} \sim 40-90\%$ of the escape velocity) in an elliptical galaxy potential, its subsequent motion is characterized by three phases (cite: Gualandris08). First, the large-scale perturbations – those exceeding the core radius ($r_c \sim 1\rm\; kpc$) – are damped within $\sim 10^7\rm\; yr$. Then, when the amplitude becomes comparable to the galaxy’s core radius, the oscillations of the SMBH persist for $\sim 1\rm\; Gyr$. Finally, the SMBH reaches thermal equilibrium with the stars, at which point the oscillations are negligibly small.

The large ($2.6\rm\; kpc$) displacement observed in Zw 3146 implies that any SMBH coalescence would have occurred recently – within the last $10^{7}\rm\; yr$. In a merger between two galaxies with $\sim 10^9\hbox{$\rm\thinspace M_{\odot}$}$ SMBHs, coalescence occurs within $1-2\rm\; Gyr$ (cite: Khan12). Stellar disturbances from a merger will persist for about $2\rm\; Gyr$ (cite: Lotz08), but may be shorter lived in a rich cluster. The features observed in the *HST* F606W image (Fig. [2](#fig:comparison)) may correspond to tidal features induced by a merger. Thus, it is plausible that the SMBHs have recently coalesced and that gravitational wave recoil accounts for the displacement of the continuum source.

### Acceleration by an asymmetric radio jet

If the radio jets are intrinsically asymmetric in their power output, then the SMBH will experience a net thrust that will displace it from its equilibrium position (cite: Shklovsky82). When the black hole is accreting near the Eddington limit, the resulting thrust can cause it to oscillate within the host galaxy (cite: Wang92; Tsygan07; Kornreich08; Lena14). Clusters are generally not expected to contain asymmetric jets, as even in the most powerful systems the SMBH resides at the center of the BCG and, on parsec scales, the jets are two-sided (cite: Liuzzo10). However, while most cavities in Zw 3146 are balanced by another on the opposite side of the BCG, the innermost cavity (cavity D) has no discernible counterpart. Since this cavity is positioned opposite the displacement direction, it can conceivably account for the displacement, provided it was inflated by an asymmetric jet.

The momentum flux for a one-sided relativistic jet is $P_{\rm jet}/c$. This is the reaction force applied to the black hole from which the jet originates. The resulting acceleration for a SMBH of mass $M_{\bullet}$ is $$\begin{equation}
    a_{\bullet} = \frac{P_{\rm jet}}{M_{\bullet}c} \approx 1.7\ensuremath{\times 10^{-8}} \left( \frac{P_{\rm jet}}{10^{45}\hbox{$\rm\; erg\rm\; s^{-1}\,$}} \right) \left( \frac{M_{\bullet}}{10^9\hbox{$\rm\thinspace M_{\odot}$}} \right)^{-1} \hbox{$\rm\; cm\rm\; s^{-2}\,$}.
\end{equation}$$ The black hole mass in the Zw 3146 BCG, estimated using the 2MASS K-band magnitude, is $M_{\bullet} = 1.6\ensuremath{\times 10^{9}} \hbox{$\rm\thinspace M_{\odot}$}$ (cite: Main17). The black hole acceleration for cavity D, using $P_{\rm cav}$ as an estimate for jet power (see Table [\[tab:cavities\]](#tab:cavities)), evaluates to $1.5\ensuremath{\times 10^{-8}}\hbox{$\rm\; cm\rm\; s^{-2}\,$}$.

A displaced black hole will experience a restoring acceleration from the gravitational pull of the BCG. Assuming the BCG is represented by a singular isothermal sphere with velocity dispersion $\sigma_{\ast}=300\hbox{$\rm\; km\rm\; s^{-1}\,$}$, the gravitational acceleration ($2\sigma^2/R$) at a displacement of $R=1\rm\; kpc$ is $5.8\ensuremath{\times 10^{-7}}\hbox{$\rm\; cm\rm\; s^{-2}\,$}$. This is 40 times larger than the acceleration that would be imparted by cavity D assuming that it has no counter-jet. An asymmetric jet can therefore not account for the $2.6\rm\; kpc$ displacement of the continuum source.

![image](Zw3146_CO10.pdf) ![image](PKS0745_CO10.pdf) ![image](PKS0745_CO32.pdf)

## Comparison to other BCGs

The majority of BCGs contain molecular gas distributions that do not resemble those in gas-rich spiral galaxies. Instead of rotationally-supported disks or rings, the cold gas in BCGs is generally filamentary (cite: Olivares19; Russell19). In a sample of 12 BCGs, only two have $\leq 10\%$ of their total molecular gas located in filaments (cite: Russell19). The filaments in the remaining systems account for $30-100\%$ of their molecular gas supplies. These filaments can extend anywhere from several to several tens of kpc from the galactic center, often in the direction of X-ray cavities (cite: mcn14; Russell16; Vantyghem16). Their velocity gradients are often smooth, but are shallower than would be expected from free-fall.

The three extensions in Zw 3146 CO(1-0) likely correspond to molecular filaments that are about $4\rm\; kpc$ in length. The outer portions of the filaments, identified by the boxes in Fig. [4](#fig:beamsub), account for $40\%$ of the total flux. Radial filaments extending into the galactic center would contain an even larger fraction of the flux. Nevertheless, we are unable to rule out the presence of a molecular disk. The velocity structure, however, is inconsistent with the smooth gradient expected for a disk, so if a disk is present it must be unresolved. Similarly we do not observe the double-horned profile in the CO(1-0) spectrum that is typical of disks.

The system that compares most closely to the Zw 3146 CO(1-0) morphology is PKS0745-191, also at CO(1-0) (cite: Russell16). Both exhibit a bright peak near the center of the gas distribution as well as three poorly-resolved radial extensions. However, the CO(3-2) observation of PKS0745-191 clearly resolves the three molecular filaments with no significant nuclear structure. The central peak at CO(1-0) results from the coarser resolution blending together the radial filaments. A comparison of Zw 3146 CO(1-0) with both PKS0745-191 CO observations is shown in Fig. [9](#fig:pks_comp).

Subtracting the central, unresolved emission from the PKS0745-191 CO(1-0) data (see Section [3.2](#sec:kinematics) for the same analysis on Zw 3146), $52\%$ of the total flux can be attributed to an unresolved clump at the peak emission position. This is larger than the $22\%$ measured for Zw 3146 CO(1-0), while in PKS0745-191 CO(3-2) $<5\%$ of the emission is located at the vertex of its three filaments. Without additional higher resolution observations of Zw 3146 we cannot conclusively determine its true molecular gas morphology. However, the similarities with PKS0745-191 suggest that it could share the morphology of three radial filaments with little central emission, observed with intermediate resolution.

## Origin of the Molecular Gas

The massive ($5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$) reservoir of cold gas residing in the central 4 kpc of the Zw 3146 BCG places stringent requirements on its origin. Several tens of gas-rich spiral galaxies would need to be stripped to account for this gas supply. In cluster cores these are rare, as most central galaxies are red, gas-poor ellipticals (cite: Best07). Sustained stellar mass loss will contribute to the molecular gas supply, but cannot account for the entire reservoir (cite: Sparks89; Voit11). Instead, like most BCGs, the primary mechanism for forming the molecular gas is the condensation of the hot atmosphere.

Although the hot atmosphere contains ample fuel to produce the molecular gas reservoir, the region covered by molecular emission is dominated by molecular gas. Only $2.5\pm0.2\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of hot gas is present within the central $10\rm\; kpc$, while the $5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of cold gas is located in the central $4\rm\; kpc$. Zw 3146 is not unique in this regard. In other systems observed by ALMA, the molecular gas mass is approximately equal to the hot gas mass when considering only the region that contains molecular emission (cite: Russell19). Forming all of the molecular gas in this region would result in a significant inflow as the central hot atmosphere is depleted. Alternatively, the cold gas could be formed on larger scales in filaments that are too faint to be detected. The Ly-$\alpha$ emission, which could be coincident with this fainter molecular line emission, extends well beyond the inner 4 kpc in which the molecular gas is confined. Gas condensing out of the central $20\rm\; kpc$ would have $2\ensuremath{\times 10^{11}}\hbox{$\rm\thinspace M_{\odot}$}$ of hot gas to draw from.

In the stimulated feedback paradigm, molecular gas condenses from intracluster gas that has been entrained and uplifted by a radio bubble (cite: mcn16). Zw 3146 harbours multiple X-ray cavities that have likely arisen from $2-3$ cycles of AGN activity. All three molecular extensions are projected behind an X-ray cavity. The SE and W extensions trail the two most prominent cavities – A and B, respectively. The NE extension trails the most distant and poorly-defined cavity (F).

By Archimedes’ principle, the maximum mass of gas that can be uplifted in the wake of a rising bubble is given by the mass it has displaced. This demand is alleviated by a factor of a few because the hot atmosphere is initially buoyantly neutral, making the gas easier to lift (cite: Su17). The cavities that are associated with a molecular extension have each displaced several $10^{10}\hbox{$\rm\thinspace M_{\odot}$}$ of hot gas (see Table [\[tab:cavities\]](#tab:cavities)). This is several times larger than the mass of the molecular gas in the extensions (Table [\[tab:spectra\]](#tab:spectra)). Combined, the cavities displace a total of $1.3\ensuremath{\times 10^{11}}\hbox{$\rm\thinspace M_{\odot}$}$ of hot gas. Thus these cavities could have initiated the formation of the entire $5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ reservoir of cold gas.

Spectroscopic estimates of the mass deposition rate made using *Chandra* suggest that the hot atmosphere is condensing at a rate of $300\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ (cite: Egami06). However, a recent spectral analysis conducted using archival data from the *XMM-Newton* Reflection Grating Spectrometer, following the prescription of (cite: Liu19), measured $<50\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ of continuous radiative cooling from the bulk temperature ($4\rm\; keV$) down to $0.01\rm\; keV$ (Liu et al. in preparation). This includes $130\pm60\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ of gas cooling to $0.7\rm\; keV$, with $<78\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ cooling below that. This is closely matched to the star formation rate of $70\pm14\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$. It would take $1\rm\; Gyr$ to produce the observed reservoir with condensation proceeding at $50\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$. Condensation at this rate over the age of a single cavity would contribute a few $10^9\hbox{$\rm\thinspace M_{\odot}$}$ of cold gas. The age of the AGN two most energetic AGN outbursts, determined by the buoyancy time of their respective cavities, are $\sim 4\ensuremath{\times 10^{7}}\rm\; yr$ and $\sim 7\ensuremath{\times 10^{7}}\rm\; yr$. This translates to the formation of $2-3.5\ensuremath{\times 10^{9}}\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas, $4-7\%$ of the total supply.

Stimulated feedback can therefore contribute significantly to the reservoir of molecular gas, but many cycles of AGN feedback would be required to account for the entire reservoir. Each cycle of AGN feedback can stimulate the formation of a few $10^9\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas. This process must be sustained for 1 Gyr or longer in order to accumulate the cold gas mass that is observed. The consumption of cold gas in star formation complicates this picture, however, as the star formation rate is comparable to the mass deposition rate.

# Conclusions

Our ALMA CO(1-0) observations of the Zw 3146 BCG have revealed a massive ($5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$) reservoir of molecular gas located within $4\rm\; kpc$ of the galactic center. The gas distribution is marginally resolved into three filaments. We have also identified six cavities in the *Chandra* X-ray image. Each molecular filament trails one of the X-ray cavities.

The cavities have displaced a mass of intracluster gas several times larger than the molecular gas mass, suggesting that stimulated cooling – where low entropy gas from the cluster core is uplifted by rising radio bubbles until it becomes thermally unstable and condenses – may be responsible for the formation of the molecular gas. However, stimulated cooling would have difficulty accounting for the entire reservoir, as the cavity ages are more than ten times shorter than the 1 Gyr it would take to form $5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of cold gas at the observed condensation rate. The total gas supply is likely accumulated over many cycles of AGN feedback, with each cycle shaping its distribution.

While the molecular gas is centered within the BCG, the continuum source originating from the AGN is not. The continuum source is located $2.6\rm\; kpc$ away from the peak of the CO(1-0) emission, placing it at the outer extent of the molecular filaments. The displacement between the continuum source and the galactic center was likely caused by a merger. Possible tidal features within the BCG may be indicative of a merger remnant. The continuum source may correspond to the nucleus of this secondary galaxy. Alternatively, a gravitational wave recoil following a recent ($<10^7\rm\; yr$) black hole merger may account for this displacement. Alternative mechanisms – such as a chance alignment with a background galaxy, the continuum corresponding to the lobe of a jet, or an asymmetric jet accelerating the SMBH of the BCG – are unlikely.

# Acknowledgments

We thank the anonymous referee for their helpful comments that improved this paper. ANV thanks Yjan Gordon and Cameron Lawlor-Forsyth for their support. ANV, BRM, CPO, and SAB are supported by the Natural Sciences and Engineering Research Council of Canada. This paper makes use of the ALMA data ADS/JAO.ALMA 2018.1.01056.S. ALMA is a partnership of the ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This research made use of Astropy, a community-developed core Python package for Astronomy. This research made use of APLpy, an open-source plotting package for Python hosted at http://aplpy.github.com.

natexlab

(ref: Alatalo11) Alatalo, K., Blitz, L., Young, L. M., et al. 2011, ApJ, 735, 88

(ref: Allen92) Allen, S. W., Edge, A. C., Fabian, A. C., et al. 1992, MNRAS, 259, 67

(ref: Bartlett20) Bartlett, D. J., Desmond, H., Devriendt, J., Ferreira, P. G., & Slyz, A. 2020, arXiv e-prints, arXiv:2007.01353

(ref: Batcheldor10) Batcheldor, D., Robinson, A., Axon, D. J., Perlman, E. S., & Merritt, D. 2010, ApJL, 717, L6

(ref: Bayet10) Bayet, E., Hartquist, T. W., Viti, S., Williams, D. A., & Bell, T. A. 2010, A&A, 521, A16

(ref: Begelman80) Begelman, M. C., Blandford, R. D., & Rees, M. J. 1980, Nature, 287, 307

(ref: Best07) Best, P. N., von der Linden, A., Kauffmann, G., Heckman, T. M., & Kaiser, C. R. 2007, MNRAS, 379, 894

(ref: Birzan04) Bîrzan, L., Rafferty, D. A., McNamara, B. R., Wise, M. W., & Nulsen, P. E. J. 2004, ApJ, 607, 800

(ref: Birzan12) Bîrzan, L., Rafferty, D. A., Nulsen, P. E. J., et al. 2012, MNRAS, 427, 3468

(ref: Blanton01) Blanton, E. L., Sarazin, C. L., McNamara, B. R., & Wise, M. W. 2001, ApJL, 558, L15

(ref: Bohringer00) Böhringer, H., Voges, W., Huchra, J. P., et al. 2000, ApJS, 129, 435

(ref: Bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Burns90) Burns, J. O. 1990, AJ, 99, 14

(ref: Campanelli07) Campanelli, M., Lousto, C. O., Zlochower, Y., & Merritt, D. 2007, , 98, 231102

(ref: Cavagnolo08) Cavagnolo, K. W., Donahue, M., Voit, G. M., & Sun, M. 2008, ApJL, 683, L107

(ref: Chiaberge17) Chiaberge, M., Ely, J. C., Meyer, E. T., et al. 2017, A&A, 600, A57

(ref: Churazov01) Churazov, E., Brüggen, M., Kaiser, C. R., Böhringer, H., & Forman, W. 2001, ApJ, 554, 261

(ref: Churazov00) Churazov, E., Forman, W., Jones, C., & Böhringer, H. 2000, A&A, 356, 788

(ref: Coble07) Coble, K., Bonamente, M., Carlstrom, J. E., et al. 2007, AJ, 134, 897

(ref: Cowie83) Cowie, L. L., Hu, E. M., Jenkins, E. B., & York, D. G. 1983, ApJ, 272, 29

(ref: Crawford99) Crawford, C. S., Allen, S. W., Ebeling, H., Edge, A. C., & Fabian, A. C. 1999, MNRAS, 306, 857

(ref: Dasyra11) Dasyra, K. M., & Combes, F. 2011, A&A, 533, L10

(ref: David14) David, L. P., Lim, J., Forman, W., et al. 2014, ApJ, 792, 94

(ref: DeGrandi04) De Grandi, S., Ettori, S., Longhetti, M., & Molendi, S. 2004, A&A, 419, 7

(ref: DeGrandi01) De Grandi, S., & Molendi, S. 2001, ApJ, 551, 153

(ref: Donahue11) Donahue, M., de Messières, G. E., O’Connell, R. W., et al. 2011, ApJ, 732, 40

(ref: Donahue15) Donahue, M., Connor, T., Fogarty, K., et al. 2015, ApJ, 805, 177

(ref: Dunn06) Dunn, R. J. H., & Fabian, A. C. 2006, MNRAS, 373, 959

(ref: Ebeling98) Ebeling, H., Edge, A. C., Bohringer, H., et al. 1998, MNRAS, 301, 881

(ref: Edge01) Edge, A. C. 2001, MNRAS, 328, 762

(ref: Edge94) Edge, A. C., Fabian, A. C., Allen, S. W., et al. 1994, MNRAS, 270, L1

(ref: Edge03) Edge, A. C., & Frayer, D. T. 2003, ApJL, 594, L13

(ref: Edge02) Edge, A. C., Wilman, R. J., Johnstone, R. M., et al. 2002, MNRAS, 337, 49

(ref: Edge10) Edge, A. C., Oonk, J. B. R., Mittal, R., et al. 2010, A&A, 518, L47

(ref: Egami06b) Egami, E., Rieke, G. H., Fadda, D., & Hines, D. C. 2006a, ApJL, 652, L21

(ref: Egami06) Egami, E., Misselt, K. A., Rieke, G. H., et al. 2006b, ApJ, 647, 922

(ref: Fabian94) Fabian, A. C. 1994, ARA&A, 32, 277

(ref: Fabian12) —. 2012, ARA&A, 50, 455

(ref: Fabian06) Fabian, A. C., Sanders, J. S., Taylor, G. B., et al. 2006, MNRAS, 366, 417

(ref: Ferland09) Ferland, G. J., Fabian, A. C., Hatch, N. A., et al. 2009, MNRAS, 392, 1475

(ref: Forman02) Forman, W., Jones, C., Markevitch, M., Vikhlinin, A., & Churazov, E. 2002, arXiv e-prints, astro

(ref: Gaspari13) Gaspari, M., Ruszkowski, M., & Oh, S. P. 2013, MNRAS, 432, 3401

(ref: Gaspari17a) Gaspari, M., Temi, P., & Brighenti, F. 2017, MNRAS, 466, 677

(ref: Giacintucci14) Giacintucci, S., Markevitch, M., Venturi, T., et al. 2014, ApJ, 781, 9

(ref: Gonzalez07) González, J. A., Sperhake, U., Brügmann, B., Hannam, M., & Husa, S. 2007, , 98, 091101

(ref: Gualandris08) Gualandris, A., & Merritt, D. 2008, ApJ, 678, 780

(ref: Guillard12) Guillard, P., Ogle, P. M., Emonts, B. H. C., et al. 2012, ApJ, 747, 95

(ref: Hamer14) Hamer, S. L., Edge, A. C., Swinbank, A. M., et al. 2014, MNRAS, 437, 862

(ref: Heckman81) Heckman, T. M. 1981, ApJL, 250, L59

(ref: Hicks05) Hicks, A. K., & Mushotzky, R. 2005, ApJL, 635, L9

(ref: Hicks10) Hicks, A. K., Mushotzky, R., & Donahue, M. 2010, ApJ, 719, 1844

(ref: Hoffer12) Hoffer, A. S., Donahue, M., Hicks, A., & Barthelemy, R. S. 2012, ApJS, 199, 23

(ref: Hogan17a) Hogan, M. T., McNamara, B. R., Pulido, F., et al. 2017, ApJ, 837, 51

(ref: Hogan15a) Hogan, M. T., Edge, A. C., Hlavacek-Larrondo, J., et al. 2015, MNRAS, 453, 1201

(ref: Hu85) Hu, E. M., Cowie, L. L., & Wang, Z. 1985, ApJS, 59, 447

(ref: Kennicutt12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531

(ref: Kennicutt98) Kennicutt, Jr., R. C. 1998, ARA&A, 36, 189

(ref: Khan12) Khan, F. M., Preto, M., Berczik, P., et al. 2012, ApJ, 749, 147

(ref: Kornreich08) Kornreich, D. A., & Lovelace, R. V. E. 2008, ApJ, 681, 104

(ref: Lena14) Lena, D., Robinson, A., Marconi, A., et al. 2014, ApJ, 795, 146

(ref: Li14a) Li, Y., & Bryan, G. L. 2014, ApJ, 789, 54

(ref: Lim08) Lim, J., Ao, Y., & Dinh-V-Trung. 2008, ApJ, 672, 252

(ref: Lim12) Lim, J., Ohyama, Y., Chi-Hung, Y., Dinh-V-Trung, & Shiang-Yu, W. 2012, ApJ, 744, 112

(ref: Liu19) Liu, H., Pinto, C., Fabian, A. C., Russell, H. R., & Sanders, J. S. 2019, MNRAS, 485, 1757

(ref: Liuzzo10) Liuzzo, E., Giovannini, G., Giroletti, M., & Taylor, G. B. 2010, A&A, 516, A1

(ref: Lotz08) Lotz, J. M., Jonsson, P., Cox, T. J., & Primack, J. R. 2008, MNRAS, 391, 1137

(ref: Lynds70) Lynds, R. 1970, ApJL, 159, doi:10.1086/180500

(ref: Main17) Main, R. A., McNamara, B. R., Nulsen, P. E. J., Russell, H. R., & Vantyghem, A. N. 2017, MNRAS, 464, 4360

(ref: Marriage11) Marriage, T. A., Baptiste Juin, J., Lin, Y.-T., et al. 2011, ApJ, 731, 100

(ref: Mason09) Mason, B. S., Weintraub, L., Sievers, J., et al. 2009, ApJ, 704, 1433

(ref: Mayer07) Mayer, L., Kazantzidis, S., Madau, P., et al. 2007, Science, 316, 1874

(ref: McCourt12) McCourt, M., Sharma, P., Quataert, E., & Parrish, I. J. 2012, MNRAS, 419, 3319

(ref: McDonald18) McDonald, M., Gaspari, M., McNamara, B. R., & Tremblay, G. R. 2018, ApJ, 858, 45

(ref: McDonald12) McDonald, M., Veilleux, S., & Rupke, D. S. N. 2012a, ApJ, 746, 153

(ref: McDonald11) McDonald, M., Veilleux, S., Rupke, D. S. N., Mushotzky, R., & Reynolds, C. 2011, ApJ, 734, 95

(ref: McDonald12Phoenix) McDonald, M., Bayliss, M., Benson, B. A., et al. 2012b, Nature, 488, 349

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mcn04) McNamara, B. R. 2004, in The Riddle of Cooling Flows in Galaxies and Clusters of galaxies, ed. T. Reiprich, J. Kempner, & N. Soker

(ref: McNamara07) McNamara, B. R., & Nulsen, P. E. J. 2007, ARA&A, 45, 117

(ref: McNamara12) —. 2012, New Journal of Physics, 14, 055023

(ref: mcn16) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2016, ApJ, 830, 79

(ref: mcn00) McNamara, B. R., Wise, M., Nulsen, P. E. J., et al. 2000, ApJL, 534, L135

(ref: mcn14) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2014, ApJ, 785, 44

(ref: Merritt05) Merritt, D., & Milosavljević, M. 2005, Living Reviews in Relativity, 8, 8

(ref: Morganti13) Morganti, R., Fogasy, J., Paragi, Z., Oosterloo, T., & Orienti, M. 2013, Science, 341, 1082

(ref: Morganti15) Morganti, R., Oosterloo, T., Oonk, J. B. R., Frieswijk, W., & Tadhunter, C. 2015, A&A, 580, A1

(ref: Morganti05) Morganti, R., Tadhunter, C. N., & Oosterloo, T. A. 2005, A&A, 444, L9

(ref: Nesvadba06) Nesvadba, N. P. H., Lehnert, M. D., Eisenhauer, F., et al. 2006, ApJ, 650, 693

(ref: Nulsen09) Nulsen, P., Jones, C., Forman, W., et al. 2009, in American Institute of Physics Conference Series, Vol. 1201, The Monster’s Fiery Breath: Feedback in Galaxies, Groups, and Clusters, ed. S. Heinz & E. Wilcots, 198–201

(ref: ODea08) O’Dea, C. P., Baum, S. A., Privon, G., et al. 2008, ApJ, 681, 1035

(ref: ODea10) O’Dea, K. P., Quillen, A. C., O’Dea, C. P., et al. 2010, ApJ, 719, 1619

(ref: Ogle10) Ogle, P., Boulanger, F., Guillard, P., et al. 2010, ApJ, 724, 1193

(ref: Olivares19) Olivares, V., Salome, P., Combes, F., et al. 2019, A&A, 631, A22

(ref: Peterson06) Peterson, J. R., & Fabian, A. C. 2006, Phys. Rep., 427, 1

(ref: Pizzolato05) Pizzolato, F., & Soker, N. 2005, ApJ, 632, 821

(ref: Pizzolato10) —. 2010, MNRAS, 408, 961

(ref: Pulido18) Pulido, F. A., McNamara, B. R., Edge, A. C., et al. 2018, ApJ, 853, 177

(ref: Rafferty08) Rafferty, D. A., McNamara, B. R., & Nulsen, P. E. J. 2008, ApJ, 687, 899

(ref: Rafferty06) Rafferty, D. A., McNamara, B. R., Nulsen, P. E. J., & Wise, M. W. 2006, ApJ, 652, 216

(ref: Revaz08) Revaz, Y., Combes, F., & Salomé, P. 2008, A&A, 477, L33

(ref: Rose19b) Rose, T., Edge, A. C., Combes, F., et al. 2019a, MNRAS, 489, 349

(ref: Rose19a) —. 2019b, MNRAS, 485, 229

(ref: Rose20) —. 2020, MNRAS, 496, 364

(ref: Russell14) Russell, H. R., McNamara, B. R., Edge, A. C., et al. 2014, ApJ, 784, 78

(ref: Russell16) Russell, H. R., McNamara, B. R., Fabian, A. C., et al. 2016, MNRAS, 458, 3134

(ref: Russell17) Russell, H. R., McDonald, M., McNamara, B. R., et al. 2017a, ApJ, 836, 130

(ref: Russell17b) Russell, H. R., McNamara, B. R., Fabian, A. C., et al. 2017b, MNRAS, 472, 4024

(ref: Russell19) —. 2019, MNRAS, 490, 3025

(ref: Salome03) Salomé, P., & Combes, F. 2003, A&A, 412, 657

(ref: Salome08) Salomé, P., Combes, F., Revaz, Y., et al. 2008, A&A, 484, 317

(ref: Salome06) Salomé, P., Combes, F., Edge, A. C., et al. 2006, A&A, 454, 437

(ref: Sanders16a) Sanders, J. S., Fabian, A. C., Russell, H. R., Walker, S. A., & Blundell, K. M. 2016a, MNRAS, 460, 1898

(ref: Sanders16b) Sanders, J. S., Fabian, A. C., Taylor, G. B., et al. 2016b, MNRAS, 457, 82

(ref: Sharma12) Sharma, P., McCourt, M., Quataert, E., & Parrish, I. J. 2012, MNRAS, 420, 3174

(ref: Shklovsky82) Shklovsky, I. S. 1982, in IAU Symposium, Vol. 97, Extragalactic Radio Sources, ed. D. S. Heeschen & C. M. Wade, 475–481

(ref: Solomon87) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730

(ref: Solomon05) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: Sparks89) Sparks, W. B., Macchetto, F., & Golombek, D. 1989, ApJ, 345, 153

(ref: Sturm11) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: Su17) Su, Y., Nulsen, P. E. J., Kraft, R. P., et al. 2017, ApJ, 847, 94

(ref: Tadhunter14) Tadhunter, C., Morganti, R., Rose, M., Oonk, J. B. R., & Oosterloo, T. 2014, Nature, 511, 440

(ref: Tremblay15) Tremblay, G. R., O’Dea, C. P., Baum, S. A., et al. 2015, MNRAS, 451, 3768

(ref: Tremblay16) Tremblay, G. R., Oonk, J. B. R., Combes, F., et al. 2016, Nature, 534, 218

(ref: Tremblay18) Tremblay, G. R., Combes, F., Oonk, J. B. R., et al. 2018, ApJ, 865, 13

(ref: Tsygan07) Tsygan, A. I. 2007, Astronomy Reports, 51, 97

(ref: Vantyghem16) Vantyghem, A. N., McNamara, B. R., Russell, H. R., et al. 2016, ApJ, 832, 148

(ref: Vantyghem17) Vantyghem, A. N., McNamara, B. R., Edge, A. C., et al. 2017, ApJ, 848, 101

(ref: Vantyghem18) Vantyghem, A. N., McNamara, B. R., Russell, H. R., et al. 2018, ArXiv e-prints, arXiv:1807.04331

(ref: Vantyghem19) —. 2019, ApJ, 870, 57

(ref: Voit18) Voit, G. M. 2018, ApJ, 868, 102

(ref: Voit11) Voit, G. M., & Donahue, M. 2011, ApJL, 738, L24

(ref: Wang92) Wang, J. C. L., Sulkanen, M. E., & Lovelace, R. V. E. 1992, ApJ, 390, 46

[^1]: Following the convention $S_{\nu} \propto \nu^{-\alpha}$

[^2]: https://www.legacysurvey.org/viewer

</paper>

Write the methods card for this paper.