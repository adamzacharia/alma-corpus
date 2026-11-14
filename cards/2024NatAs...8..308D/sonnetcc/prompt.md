# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024NatAs...8..308D\sonnetcc\reply.txt

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
 "bibcode": "2024NatAs...8..308D",
 "title": "Chemical tracers of a highly eccentric AGB-main-sequence star binary",
 "year": 2024,
 "journal": "Nature Astronomy",
 "first_author": "Danilovich, T.",
 "n_authors": 35,
 "arxiv_id": "2407.16979",
 "doi": "10.1038/s41550-023-02154-y",
 "alma_projects_linked_by_archive": [
  "2018.1.00659.L"
 ]
}
```

Paper text:
<paper>
# Chemical tracers of a highly eccentric AGB-main sequence star binary

1\]Institute of Astronomy, KU Leuven, Celestijnenlaan 200D, 3001 Leuven, Belgium 2\]School of Physics & Astronomy, Monash University, Wellington Road, Clayton 3800, Victoria, Australia 3\]ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), Clayton 3800, Australia 4\]School of Physics and Astronomy, University of Leeds, Leeds LS2 9JT, UK 5\]LESIA, Observatoire de Paris, Université PSL, CNRS, Sorbonne Université, Université Paris Cité, 5 place Jules Janssen, 92195 Meudon, France 6\]Astrophysics Research Centre, School of Mathematics and Physics, Queen’s University Belfast, University Road, Belfast BT7 1NN, UK 7\]JBCA, Department Physics and Astronomy, University of Manchester, Manchester M13 9PL, UK 8\]School of Chemistry, University of Leeds, Leeds LS2 9JT, UK 9\]Harvard-Smithsonian Center for Astrophysics, 60 Garden Street, Cambridge, MA 02138, USA 10\]Univ. Grenoble Alpes, CNRS, IPAG, Grenoble, France 11\]Department of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory, 43992 Onsala, Sweden 12\]Theoretical Astrophysics, Department of Physics and Astronomy, Uppsala University, Box 516, SE-751 20 Uppsala, Sweden 13\]Institut de Radioastronomie Millimétrique, 300 rue de la Piscine, F-38406 Saint-Martin-d’Hères, France 14\]Department of Mathematics, Kiel University, Heinrich-Hecht-Platz 6, 24118 Kiel, Germany 15\]Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany 16\]Université de Bordeaux, Laboratoire d’Astrophysique de Bordeaux, 33615 Pessac, France 17\]University of Amsterdam, Anton Pannekoek Institute for Astronomy, 1090 GE Amsterdam, The Netherlands 18\]Department of Chemistry and Molecular Biology, University of Gothenburg, Medicinaregatan 7 B 41390 Gothenburg, Sweden 19\]National Astronomical Research Institute of Thailand, Chiangmai 50180, Thailand 20\]Université Côte d’Azur, Laboratoire Lagrange, Observatoire de la Côte d’Azur, F-06304 Nice Cedex 4, France 21\]School of Physical Sciences, The Open University, Walton Hall, Milton Keynes, MK7 6AA, UK 22\]Universität zu Köln, I. Physikalisches Institut, 50937 Köln, Germany 23\]California Institute of Technology, Jet Propulsion Laboratory, Pasadena CA 91109, USA 24\]University College London, Department of Computer Science, London WC1E 6BT, United Kingdom

# Abstract

Binary interactions have been proposed to explain a variety of circumstellar structures seen around evolved stars, including asymptotic giant branch (AGB) stars and planetary nebulae. Studies resolving the circumstellar envelopes of AGB stars have revealed spirals, discs and bipolar outflows, with shaping attributed to interactions with a companion. For the first time, we have used a combined chemical and dynamical analysis to reveal a highly eccentric and long-period orbit for W Aquilae, a binary system containing an AGB star and a main sequence companion. Our results are based on anisotropic SiN emission, the first detections of NS and SiC towards an S-type star, and density structures observed in the CO emission. These features are all interpreted as having formed during periastron interactions. Our astrochemistry-based method can yield stringent constraints on the orbital parameters of long-period binaries containing AGB stars, and will be applicable to other systems.

# Main

The asymptotic giant branch (AGB) is a late evolutionary stage of low and intermediate mass stars ($\sim 1$ to 8 solar masses, $\mathrm{M}_\odot$). This stage is characterised by mass-losing stellar winds, rich in molecular gas and dust, which form an extended, expanding circumstellar envelope (CSE) around the star (cite: Hofner2018). AGB stars eventually transition through the planetary nebula phase and end as white dwarf stars, having chemically enriched their host galaxies through their mass loss (cite: Kobayashi2020). Binary companions can have a significant impact on this process, potentially affecting mass-loss rates and chemistry (cite: Decin2019; Van-de-Sande2022), and are thought to shape both the eventual planetary nebula (cite: De-Marco2022) and the CSE during the AGB phase (cite: Decin2020). Binary stars with an AGB component are also the progenitors of various exotic objects, including Barium stars, CH stars, extrinsic S-stars, and novae (cite: Jorissen2004). Hence, understanding binary systems containing AGB stars, especially through observations, is important for understanding their overall evolutionary progress, the initial-final mass relation, and the evolution of their host galaxies.

Recent observations of some AGB stars have identified the signatures of binary companions imprinted in the structure of the CSE. In only a few cases, however, is the precise nature of the companion and its effects on the CSE known, thereby limiting the study of such systems. Systems with directly detected companions include Mira, which comprises an oxygen-rich AGB star and a white dwarf, in which the companion has contributed to the shaping of the CSE structure (cite: Karovska1997; Ramstedt2014a), and L$_2$ Pup, an oxygen-rich AGB star surrounded by a disc with a planetary companion (cite: Kervella2016). Bipolar structures around $\pi^1$ Gru have been attributed to a recently detected close companion (cite: Homan2020), adding to the small number of AGB systems with directly detected companions.

The spiral structures observed around the carbon stars AFGL 3068 and R Scl (cite: Mauron2006; Kim2017; Maercker2012), and the bipolar structures around the carbon star V Hya (cite: Sahai2022), indicate the possible presence of binary companions that have not been directly detected. A more complete understanding of circumstellar structures will come from knowing both cause (e.g. a stellar or planetary companion) and effect (the CSE structure) and should allow us to draw more direct links between AGB stars and planetary nebulae, which have been observed to display a multitude of complex asymmetric structures (cite: Ramos-Larios2016; Decin2020).

W Aquilae (W Aql) is a binary system at a distance of 395 pc (Methods [3.1](#dist-notes)). It contains an S-type AGB star, which has a mixed carbon-oxygen chemistry (C/O $\sim 1$) and may be transitioning from being oxygen-rich to carbon-rich, and an F9 main sequence star (cite: Herbig1965; Danilovich2015) located to the southwest of the AGB star at a projected separation of $\sim 0.5^{\prime\prime}$ (cite: Ramstedt2011). W Aql has been extensively studied through observations taken with a variety of telescopes (cite: Ramstedt2011; Mayer2013; Danilovich2014; Ramstedt2017; Brunner2018; Danilovich2021). Spatially resolved observations of the polarised dust (cite: Ramstedt2011) and CO (cite: Ramstedt2017) around the AGB star have shown a large-scale asymmetry in the direction of the F9 companion, a sign that binary interactions may be shaping the CSE. However, the asymmetry exists at larger scales than the present separation of the two stars, from $\sim 10^{\prime\prime}$ to $\sim100^{\prime\prime}$ (cite: Ramstedt2011; Ramstedt2017; Mayer2013). Some indications of spiral structure in the CSE were seen in observations taken by the Atacama Large Millimetre/submillimetre Array (ALMA) at a resolution of $\sim 0.4^{\prime\prime}$ (cite: Ramstedt2017) but it was unclear whether these could be caused by the F9 star.

# Results

We have analysed new, high resolution ALMA observations of the W Aql system with spatial resolutions to $\sim 0.024^{\prime\prime}$, i.e. approximately twice the K-band stellar diameter (cite: Richichi2005), and 40% larger than the millimetre stellar diameter (Methods [3.4.2](#Udisc)). We combined these with photometric observations, new smooth particle hydrodynamics models, and chemical kinetics models to put new constraints on the orbit of the system. We have shown that all the observations are consistent with the hypothesis of a highly eccentric orbit, based primarily on the distributions of molecular species which formed during periastron passage and the structures seen in the CO observations, making such an interpretation highly probable.

## Species formed during periastron passage

![](W_Aql_SiN_mom0_paper.pdf)

![](W_Aql_SiN_PV_PA33deg_parabola_ellipse_paper.pdf)

From a detailed examination of the ALMA data (Methods [3.4](#almadata)), we identified several molecules exhibiting spatially asymmetric emission. Most notable was SiN, which has only been detected towards one other AGB CSE (cite: Turner1992). In Fig. [1](#sin)a we plot a zeroth moment (integrated intensity) map of SiN, which shows emission in a roughly triangular wedge mainly to the northeast of the AGB star. To further understand the spatial origin of the emission, we constructed a position-velocity diagram (Fig. [1](#sin)b), which reveals an arc of SiN emission that lies side-on ($90^\circ$), i.e. perpendicular to the plane of the sky (Methods [3.4.3](#sinsic)).

The absence of (approximate) spherical symmetry in the emission suggests a spatial and/or temporal dependence for the formation of SiN around W Aql. Chemical kinetics models indicate that the production of SiN is higher in the presence of UV photons — such as can be provided by a main sequence companion (cite: Van-de-Sande2022) like the F9 component of W Aql, but only in sufficiently dense regions of the CSE (see Methods [3.6](#chemmethods) for further details of the chemistry initiated by the companion’s UV field). We posit that: (1) the binary orbit is highly eccentric and inclined $i\sim90^\circ$; (2) the formation of the arc of SiN was triggered close to periastron (Figs. [4](#orb-phot) and [10](#SiNsketch)), when the F9 star passed close to the AGB star and irradiated part of the dense inner AGB wind; and (3) this temporarily drove chemical reactions through increased (but not complete) photodissociation and photoionisation, including those reactions which led to the formation of SiN (Methods [3.6.1](#chem:sin)).

We used radiative transfer modelling to estimate the abundance of SiN in the arc and found a peak abundance of $1.5\times 10^{-7}$ relative to $\mathrm{H}_2$ (Methods [3.5](#rtmod)), which is in general agreement with the expectations from chemical models containing an F9-like companion (Methods [3.6.1](#chem:sin)). Further evidence in support of this formation mechanism is provided by the presence of SiC and NS emission towards W Aql. These are the first detections of SiC and NS towards an S-type AGB star and their emission is also asymmetric (with a weaker signal to noise ratio (SNR) than SiN; see Methods [3.4.3](#sinsic) and [3.4.4](#NSdet), and Figs [5](#sic) and [14](#nsplot) in the Extended Data and Supplementary Materials). The presence of SiC and NS is consistent with chemical model predictions (cite: Van-de-Sande2022) for the effect of the periastron passage of the F9 star on the chemistry of the CSE (Methods [3.6.1](#chem:sin) and [3.6.2](#nschem)).

## Photodissociation of common species

Farther from the AGB star, such as where the F9 star is presently located, the wind is less dense ($\sim3\times 10^{5}$ cm$^{-3}$ compared with $\sim10^{9}$ cm$^{-3}$ at 10 au from the AGB star) and the chemistry tends to be initiated by photodissociation by the interstellar radiation field. The density in this region is too low for species like SiN to form, however, we see evidence of the F9 star driving additional photodissociation in the zeroth moment maps of SiO, SiS, CS and HCN (Fig. [6](#othermol) in the Extended Data), all of which show extended emission to the northeast and truncated emission to the southwest, in the direction of the present position of the F9 star. The central channels of SiS and CS, in particular, show significantly lower molecular emission around the F9 star (Fig. [17](#cssissinglechans) in the Supplementary Materials). Spectra centred on the current position of the F9 star show very few detected molecular lines and the line profiles of CS, SiO and HCN show less emission around the LSR velocity compared with spectra centred on the AGB star or at the same distance from the AGB star but on the opposite side of the CSE (see Methods [3.4.8](#sec:F9spec) and Fig. [9](#F9spec) in the Extended Data).

Additional evidence of the F9 star driving photodissociation is found by comparing the distribution of with the distribution of (note, was not covered by our observations), because CN is a photodissociation product of HCN (cite: Huggins1984). As shown in Fig. [2](#fig:cn), is found to be present mainly in the region in which the emission is truncated. This is consistent with the F9 star driving the photodissociation of and hence creating . We also plot the zeroth moment map of the $J=27-26$ transition of HCCCN (the next member in the cyanopolyyne family, hereafter , see Fig. [2](#fig:cn)), which shows emission on the same side of the AGB star as , albeit over a much smaller region. The other observed transitions of show a similar distribution (Fig. [15](#hc3n) in the Supplementary Materials). Because forms from CN (Methods [3.6.3](#HCNchem)), its asymmetric distribution indicates an asymmetric CN distribution and hence provides further evidence of anisotropic photo-processes in the CSE.

![image](W_Aql_H13CN_mom0_paper.pdf) ![image](W_Aql_13CN_mom0_paper.pdf) ![image](W_Aql_HC3N_mom0_paper.pdf)

## Structures in CO emission

![image](W_Aql_zoomed-out_CO_circles.pdf) ![image](W_Aql_zoomed-in_CO_SiN.pdf)

![image](w3009_eo_full.png) ![image](W_Aql_phantom_mcfost.pdf)

CO is an abundant stable molecule, commonly used as a density tracer in CSEs. We plot high resolution ($0.132^{\prime\prime}\times0.123^{\prime\prime}$) channel maps of CO emission in Fig. [7](#cochan) in the Extended Data and first focus on the central three channels closest to the AGB stellar velocity $\upsilon_\text{LSR}=-23~\mathrm{km\,s}^{-1}$ (Fig. [3](#coarcs)a). With the aid of angle-radius plots (Fig. [8](#angrad)), we identified two key circular structures in the CO emission, with radii of $1.35^{\prime\prime}$ and $10.75^{\prime\prime}$, with centres offset from the present position of the AGB star by $0.1^{\prime\prime}$ and $1.5^{\prime\prime}$ to the north. These are shown in black and white in Fig. [3](#coarcs)a. Other circular structures are highlighted in red and pink and, because these are offset to the southwest, we presume they were formed through different processes to the black and white circles and focus on the latter first.

To better understand the origin of the circular structures, we performed hydrodynamic simulations for highly eccentric systems based on the W Aql system (details in Methods [3.7](#hydro)). From these we found that highly elliptical orbits ($e \gtrsim 0.8$) result in almost spherical structures in the wind, which appear circular and slightly offset away from the present position of the companion when viewed edge-on ($i=90^\circ$) relative to the plane of the orbit (Fig. [3](#coarcs)c). These structures are generated during periastron passages and are very similar to the black and white circles seen in the ALMA CO data, even more so when the hydrodynamical model is processed with a radiative transfer code (Fig. [3](#coarcs)d). The fact that the outer edge of the SiN emission overlaps with the inner circular structure (Fig. [3](#coarcs)b) also suggests they were formed contemporaneously, i.e. during the most recent periastron passage. We also determined that the different emission distributions seen in blue (elongated) and red (circular) channels of our ALMA observations are reproduced in the hydrodynamic model (Fig. [12](#otherCOchans)). Based on all of these results, we can constrain the orbital parameters of the W Aql system.

## Orbital parameters

From the circular structures seen in Fig. [3](#coarcs), we estimate the orbital period to be $1082^{+89}_{-108}$ years. Based on the expansion time of the inner circle and the arc of SiN, we estimate the time since the most recent periastron to be $172\pm22$ years (Methods [3.8](#orbit-from-alma)). The SiN PV diagram indicates an orbital inclination of $i = 90\pm7^\circ$ (Methods [3.4.3](#sinsic)). Combining these results with resolved images of W Aql (Methods [3.3](#photmethods)), we found a series of numerical solutions that reproduce the observations within their uncertainties (Methods [3.9](#sec:solution)). All our solutions (Table [3](#tab:solutions) in the Extended Data) have high eccentricities ($e>0.9$) and small periastron distances ($r_p \leq 2\times 10^{14}$ cm $=13$ au), with long periods $\sim 1100$ years. A solution with $e=0.93$, $r_p = 1.5\times 10^{14}$ cm ($10$ au) and period 1051 years is plotted in Fig. [4](#orb-phot), where it is superposed on resolved images to show the agreement with the positions of the stars.

![image](final_orbit_paper2.pdf) ![image](Hubble_paper.pdf) ![image](SPHERE_paper.pdf)

# Discussion

For the first time, we have identified in observations, with the aid of astrochemistry, molecular species that formed during a periastron passage of an AGB + main sequence (F9) binary system. Through our analysis of these species, in combination with structures in the CO and resolved images of the two stars, we were able to constrain the binary orbit to a limited number of solutions, all having high eccentricities and almost edge-on inclinations. Our analysis opens up a new method for studying binary systems containing AGB stars by observing spatially resolved emission of key molecular species.

SiN was crucial to our analysis because it is distributed asymmetrically in the W Aql CSE — alerting us to a non-standard formation pathway — and was detected with a sufficiently high SNR to be readily analysed. The other two molecules that we identified as being created during periastron, SiC and NS, strengthened our argument but their lower SNR in the present observations would not have allowed us to draw firm conclusions in the absence of SiN. However, we note that all three molecules have the potential to serve as diagnostic tools for identifying binary interactions in other systems, especially with targeted observations at high SNR. Based on the predictions of chemical models that consider the presence of a Sun-like companion (cite: Van-de-Sande2022), SiN and SiC are expected to be good tracers of stellar companions to S-type and oxygen-rich AGB stars, but probably not carbon stars (unless notably asymmetric emission is detected), because carbon-rich CSEs are expected to have higher abundances of both molecules without the presence of a companion. NS is predicted to have higher abundances around carbon stars in the presence of a white dwarf companion, but not if the companion is a main-sequence star. For S-type and oxygen-rich AGB stars, NS is expected to be a good tracer of either a white dwarf or a Sun-like companion. While there may be other molecules that are enhanced or destroyed in the presence of a companion, a comprehensive list is difficult to compile (cite: Van-de-Sande2022). After checking all detected molecular lines for asymmetries, we do not find any additional candidates for tracers of binary-induced chemistry towards W Aql.

The timing between our observations and the present orbital configuration of W Aql contributed to our being able to use SiN to characterise the orbit. If the W Aql system was instead observed $\sim 200$ years prior to the next periastron, rather than $\sim 200$ after the most recent periastron, it is unlikely that SiN would have been detected. In that case, in the $\sim 900$ years since the previous periastron, the SiN arc would have expanded with the CSE to around 4 times farther from the AGB star than what we presently observe. At that radial distance, most of the SiN would have been destroyed through photodissociation by the interstellar radiation field (cite: Van-de-Sande2022). This is also why we do not detect SiN that was created contemporaneously with the white circle in CO (Fig. [3](#coarcs)a) during the second most recent periastron passage, $\sim 1300$ years ago. That said, SiN has already persisted for $\sim 200$ years since the periastron interaction, and may continue to be detectable for another 50 to 100 years, based on the expansion velocity and excitation conditions. This means that the imprint of the periastron interaction will be potentially detectable for around a quarter of the total orbital period, a much larger portion than if we had to rely on, for example, observing changing stellar positions or radial velocities around periastron (see Table [3](#tab:solutions)). The high eccentricity and small periastron separation of the system also contributed to favourable conditions for the formation of SiN around W Aql. As noted above and in Methods [3.6](#chemmethods), the companion-initiated photochemistry is most impactful in the dense inner CSE, meaning that the tracers of this photochemistry — SiN, SiC and NS — may not be formed in sufficiently high quantities to be detected for binary systems with wider orbits, where the companion passes through regions of the CSE with lower number densities. Despite these potential limitations, molecular tracers in the CSE generally persist for a relatively long time (hundreds of years, depending on the molecule) and allow us to probe the system on longer time scales than direct imaging or radial velocity measurements, which can only be taken on human timescales. Hence, molecular tracers are invaluable for constraining binary systems with long orbital periods.

The W Aql system may be unusual for having such a highly eccentric orbit, but it is not unique nor is it impossible for it to have formed with such a high eccentricity. In fact, studies of eccentricity distributions that include wider binaries find a tendency for the mean eccentricity to be higher for subsamples with larger periods (cite: Tokovinin2016; Boffin1993). Indeed, for long-period binaries, orbital circularisation during their formation is not expected (cite: Moe2017). Furthermore, a large statistical analysis of binary systems found that solar-type stars in binaries are more likely to have long periods than short periods, i.e. the companion frequency distribution for solar-type primaries peaked at periods of $\log P[\mathrm{days}] = 5.5$ (cite: Moe2017), very close to the period we found for W Aql ($\log P_\mathrm{W Aql}[\mathrm{days}] = 5.6$). Both the aforementioned studies focussed primarily on main sequence stars, but our result for W Aql shows that wide binaries with high eccentricities can survive to the AGB phase. Our hydrodynamic model, which takes into account the gravitational effect of the secondary star on the wind and vice versa, exhibits a very slightly increasing orbital period (owing to the mass lost by the AGB star) but negligible changes in eccentricity, and does not show precession over $\sim5000$ years. While 5000 years may seem too short a time to make a definitive judgement, we point out that the expansion of the CSE during this time represents a larger spatial extent than the cool dust emission imaged by Herschel/PACS (at 70 and $160\;\mu\mathrm{m}$ (cite: Mayer2013)). Despite the high eccentricity that we find for W Aql, none of our orbital solutions (Table [3](#tab:solutions)) have periastron separations smaller than the Roche limit, so no direct interaction between the two stars is expected and no evidence of such an interaction is seen in the ALMA observations. This suggests a relatively stable, if slowly evolving, system from which we could expect the eventual formation of a planetary nebula characterised by elongation to the southwest and perhaps a variety of additional arcs, analogous to what is presently seen in the AGB CSE, including at larger scales (cite: Ramstedt2011; Mayer2013; Ramstedt2017).

Other binary systems containing AGB stars have also been found to have long periods (based mainly on spiral-like structures in CO observations) including AFGL 3068 ($\sim800$ years (cite: Kim2017)), R Scl (445 years (cite: Maercker2012; Maercker2016a)), and II Lup (128 years (cite: Lykou2018)). In comparison, AGB stars that have close companions, such as $\pi^1$ Gru (current projected separation 6 au (cite: Doan2017; Homan2020), period unknown) and V Hya (8.5 year period (cite: Sahai2016; Sahai2022)), both of which are triple systems that also have wide companions, have less spherical and more disrupted CSEs with, for example, bipolar outflows. Unlike the former group with more spherical CSEs, these triple systems are more likely to go on to form bipolar planetary nebulae. The very high eccentricity of W Aql precludes the presence of a stable third companion and, despite the small periastron separation, we can consider it to be a relatively undisrupted system, suggesting the eventual formation of a relatively regular planetary nebula, i.e. perhaps more closely resembling the Ring Nebula than the Butterfly Nebula.

The study we have presented here adds to the small number of AGB stars with known companions and orbital parameters. While previous studies have struggled to explain the range of eccentricities observed for e.g. post-AGB stars, most of these have focussed on shorter orbital periods, ranging up to 1000 days, rather than 1000 years, owing to observational limitations (cite: Oomen2018). The W Aql system provides further evidence that highly eccentric systems with long orbital periods exist during the AGB phase and that such eccentricity could be inherited by binary systems in later evolutionary phases, such as post-AGB stars and Barium stars (cite: Jorissen1998). The method used here — which entails the combination of chemical tracers and hydrodynamical models — can be used to detect the characteristic effects of main sequence binary companions in other AGB CSEs. Rather than solely searching for structures in the CSE, future studies can also check for anisotropies in molecular emission and the production of particular molecular species to confirm or rule out the presence of a stellar companion.

# Methods

## Distance

Many of the measurements and calculations in the present work rely on the value of the distance to the W Aql system and, more specifically, to the AGB component. Previous modelling of W Aql has assumed a distance of 395 pc, calculated from a period-magnitude relation (cite: Danilovich2014). Prior to this, a variety of distances were assumed for W Aql, ranging from 230 to 680 pc (cite: Ramstedt2009; Knapp1985; Jura1988; Groenewegen1998). Recently, distances have been calculated based on high-precision parallax observations from the Gaia mission (cite: Gaia-2016). Values of $374\pm22$ pc (cite: Danilovich2021) and $380^{+68}_{-49}$ pc (cite: Andriantsaralaza2022) were found using different methods based on the Gaia Early Data Release 3 (cite: Gaia-EDR3). In this work, we continue to use a distance of 395 pc because this value falls within the uncertainties of both Gaia-derived values, and because it has been previously used in many radiative transfer models for the AGB star (cite: Danilovich2014; Ramstedt2017; Brunner2018; Danilovich2021) and various stellar and circumstellar parameters such as luminosity and mass-loss rate have been derived relative to this value (Table [2](#tab:parameters)).

We note that if the true distance is not exactly the adopted one, then the derivations of various parameters would be altered in the following way: mass-loss rate and relative molecular abundances would tend to increase for a larger distance, although molecular abundances may not change significantly after the mass-loss rate was updated, owning to a degeneracy between the impact of distance and density (the latter being directly related to mass-loss rate) on the line intensity. Our derived projected separations would increase linearly with distance, which would in turn result in a larger calculated orbital period.

## Stellar masses

The companion to the AGB star was identified as a main sequence star classified as F8 to G0 (cite: Danilovich2015), implying the stellar mass is in the range $1.09-1.04\,\mathrm{M}_\odot$ (cite: Habets1981). For the purposes of this study we have assumed the companion is an F9 star with a mass of $1.06\,\mathrm{M}_\odot$.

The situation for the AGB component is more complicated. Previous studies comparing oxygen isotopic ratios with stellar evolution models have calculated an initial stellar mass for the AGB star of $1.6\pm0.2\,\mathrm{M}_\odot$ (cite: De-Nutte2017; De-Beck2020). Although the current mass-loss rate of the AGB star is relatively high at $\dot{M} = 3\times 10^{-6}\;\mathrm{M}_\odot~\mathrm{ yr}^{-1}$ (cite: Ramstedt2017), stellar evolution models indicate that a significant decrease in stellar mass (i.e. $>0.1\,\mathrm{M}_\odot$) is not expected to occur until the final stages of the thermally pulsing AGB phase (i.e. during and after the last one or two thermal pulses (cite: Vassiliadis1993)). Ergo, we assume $1.6\,\mathrm{M}_\odot$ for the present AGB mass and hence assume a total system mass of $2.66\,\mathrm{M}_\odot$.

## Spatially resolved imaging

W Aql was observed with the Advanced Camera for Surveys (ACS) on the Hubble Space Telescope (HST) at 400 nm on 12 October 2004 (Fig. [4](#orb-phot)b, (cite: Ramstedt2011)). It was observed again with VLT/SPHERE-ZIMPOL at 735.4 nm on 9 July 2019 (Fig. [4](#orb-phot)c, (cite: Montarges2023)). Both HST and SPHERE images were taken during a similar phase of the AGB pulsation, approximately halfway between maximum and minimum light. Another HST observation was taken with the Wide Field/Planetary Camera (WFPC) at 550 nm in 1993 (cite: Mayer2013), but this was taken before the first servicing mission, and the degraded angular resolution makes it unusable for our study.

We measured the positions of the AGB and F9 stars using the python package `lmfit`[^1]. We find the separation between the two stars is $475\pm 1.0$ mas in the HST epoch, and $491\pm 1.8$ mas in the SPHERE epoch. For HST, the astrometry is well characterised and the uncertainties were estimated based on the noise of the images. For SPHERE, the astrometric uncertainty includes the orientation with respect to north, the distortion, the plate scale stability and the statistical position uncertainty (cite: Maire2021) The change in projected distance between the two stars is then calculated to be $16\pm 0.25\pm 1.79$ mas (to distinguish between the systematic and statistical uncertainties) in 14.75 years, with the projected motion of the F9 star approximately following a straight line away from the AGB star. This motion does not contradict a highly inclined, nearly edge-on orbit, with inclination, $i\sim 90^\circ$. The 2019 SPHERE position corresponds to a projected separation of 194 au, at our adopted distance of 395 pc.

These results indicate that the orbital period must be long, particularly as compared with the timescale of our observations. For example, a circular orbit with a radius of 194 au gives a period of 1660 years for our assumed system mass of $2.66\,\mathrm{M}_\odot$. An extremely elliptical orbit with an apastron of 194 au and a periastron of 3 au (a value chosen so the F9 star does not pass through the AGB star, since we see no evidence of such an extreme interaction) results in a period of 600 years. Note that neither of these orbits properly consider the motion seen between the HST and SPHERE epochs and are merely illustrative.

The ephemeris of such a long orbit cannot be constrained through direct photometric imaging in a reasonable timeframe, because the observations would need to be taken decades and centuries apart. Hence, we require other markers in the circumstellar environment of the AGB star to constrain the orbital parameters of the W Aql system.

## ALMA results

High spatial resolution observations of W Aql were obtained with the Atacama Large Millimetre/submillimetre Array (ALMA) as part of the ATOMIUM Large Programme[^2] (cite: Gottlieb2022). More than 110 molecular lines were detected towards W Aql, including CO, SiN, SiC, and HC$_3$N, which are analysed here. We detected the SiC and NS radicals for the first time towards an S-type star. Previously, SiN was detected and HC$_3$N was tentatively detected towards W Aql with the APEX telescope (cite: De-Beck2020). We present spatially resolved emission of SiN and HC$_3$N for the first time. The SiN, SiC and HC$_3$N emission show two types of asymmetric morphologies, both different to the more extensive circumstellar structures revealed by the CO observations at high spatial resolution.

### Data reduction

W Aql was observed with three array configurations of ALMA. This enabled us to observe small structures at high angular resolutions (down to $0.024^{\prime\prime}\times 0.021^{\prime\prime}$) while still retrieving larger structures (up to a maximum recoverable scale, or MRS, of $8.9^{\prime\prime}$) that would otherwise be resolved out (cite: Gottlieb2022).

While these are the extremes of resolution and MRS available in the ATOMIUM dataset, the precise properties the data we analyse can be found in Table [1](#resolutions) for each transition.

We combined the three data sets to maximise the sensitivity of images, using the Common Astronomy Software Applications for Radio Astronomy (CASA (cite: CASA2022)). We used the combined data to make spectral image cubes for each transition in Table [1](#resolutions), weighting the contributions of the baselines to optimise the resolution and surface brightness sensitivity. The velocity resolution is 1.1–$1.3\,\mathrm{km\,s}^{-1}$ depending on frequency, and in some cases we averaged 2 or more channels to increase sensitivity. The typical rms noise is $\lessapprox2$ mJy. All velocities are adjusted to the LSR frame. The relative astrometric accuracy of the extended configuration alone is $\sim0.002^{\prime\prime}$ and $\sim0.005^{\prime\prime}$ for the combined data at slightly lower resolution. The flux scale for the combined images is accurate to $\sim10$%. The chances of interferometric noise causing artefacts $\geq 5 \sigma$ in these images is negligible. The relative position accuracy of measurements is at least equal to the synthesised beam divided by the SNR (cite: TMS), so for SNR = 5 this is $\sim 40$ mas for SiN, SiC, NS, HC$_3$N, and $^{13}$CN, around 25 mas for CO, and 12 mas for SiO, SiS, CS and HCN.

Moment zero (integrated intensity) maps were made by summing all the channels with emission above $\sim3\sigma_{\mathrm{rms}}$. Position-velocity (PV) diagrams were made by selecting a tilted rectangular slice (‘slit’) covering the moment zero emission (spanning a width of $3^{\prime\prime}$) at the angle shown in Fig. [1](#sin) (though other angles were tested, see Methods [3.4.3](#sinsic)), and measuring the flux density in this region for each channel in increments along the slice. The peak of the continuum emission was assumed to be the position of the AGB star. In the channel maps and moment zero maps, the position of the AGB star is at (0,0). A small secondary peak, associated with the position of the F9 star, was detected in the continuum emission and will be analysed in a future paper.

+:-----------:+:------------------------------------------------------------------------:+:------------------:+:---------------------------------:+:-------------------------:+:---------------------:+:---------------------:+:---------:+
| Molecule    | Transition                                                               | Frequency          | Ref. for                          | $\upsilon_\mathrm{cent}$  | Ang. res.             | MRS                   | Recovered |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
|             |                                                                          | \[GHz\]            | freq.                             | \[$\mathrm{km\,s}^{-1}$\] | \[$^{\prime\prime}$\] | \[$^{\prime\prime}$\] | flux      |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| CO          | $J=2 \to 1$                                                              | 230.538            | (cite: Winnewisser1997)           | …                         | $0.132 \times 0.123$  | 5.3                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
|             |                                                                          |                    |                                   | -23.4                     | $0.829 \times 0.679$  | 8.9                   | 33%       |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| SiN         | $N,J,F=6,{13}/{2}, {13}/{2} \to5,{11}/{2},{11}/{2}$                      | 262.156$^\dagger$  | (cite: Turner1992)                | -23.7                     | $0.222\times0.198$    | 4.7                   | 100%      |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| SiC         | $^3\Pi_2\;\,\, J=6\to5$                                                  | 236.288            | (cite: Cernicharo1989; Bogey1990) | -23.8                     | $0.199 \times 0.184$  | 2.6                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| NS          | $^2\Pi_{1/2}\, f\;\,\,  J, F={11}/{2} , {13}/{2} \to {9}/{2} , {11}/{2}$ | 253.968$^\ddagger$ | (cite: Lee1995)                   | …                         | $0.187\times0.171$    | 2.5                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| HC$_3$N     | $J=25\to24$                                                              | 227.419            | (cite: Yamada1995)                | -22.5                     | $0.204\times 0.181$   | 5.4                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
|             | $J=26\to25$                                                              | 236.513            | (cite: Yamada1995)                | -21.8                     | $0.208 \times 0.191$  | 2.6                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
|             | $J=27\to26$                                                              | 245.606            | (cite: Yamada1995)                | -21.4                     | $0.213 \times 0.172$  | 5.0                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
|             | $J=28\to27$                                                              | 254.700            | (cite: Yamada1995)                | -20.8                     | $0.190 \times 0.172$  | 2.5                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| SiO         | $J = 5\to4$                                                              | 217.105            | (cite: Muller2013)                | -22.6                     | $0.063 \times 0.055$  | 5.7                   | 85%       |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| SiS         | $J=12\to11$                                                              | 217.818            | (cite: Muller2007)                | -21.4                     | $0.063 \times 0.055$  | 5.7                   | 91%       |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| CS          | $J=5\to4$                                                                | 244.936            | (cite: Gottlieb2003)              | -22.5                     | $0.078\times 0.066$   | 5.0                   | 79%       |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| HCN         | $J=3\to2$                                                                | 265.886            | (cite: Ahrens2002)                | -23.0                     | $0.061\times0.053$    | 2.4                   | 72%       |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| H$^{13}$ CN | $J=3\to2$                                                                | 259.012            | (cite: Fuchs2004)                 | -22.2                     | $0.073\times 0.064$   | 4.8                   | …         |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+
| $^{13}$CN   | $N, F_1, F_2, F =2, 0, 2, 3, \to 1, 0, 1, 2$                             | 217.303$^\ddagger$ | (cite: Bogey1984)                 | …                         | $0.213\times0.199$    | 5.7                   | 44%       |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+                       |                       +-----------+
|             | $N, F_1, F_2, F =2, 1, 3, 4, \to 1, 1, 2, 3$                             | 217.467$^\ddagger$ | (cite: Bogey1984)                 | …                         |                       |                       | 48%       |
+-------------+--------------------------------------------------------------------------+--------------------+-----------------------------------+---------------------------+-----------------------+-----------------------+-----------+

: Molecular lines in the ground vibrational state used in our analysis.

**Notes:** All frequencies are rest frequencies and all velocities are are with respect to the local standard of rest. ($^\dagger$) Frequency and corresponding quantum numbers of central hyperfine component are given. ($^\ddagger$) Frequency and corresponding quantum numbers of the brightest hyperfine component are given. Listed in column 4 are the primary references which provide the measured frequencies and the spectroscopic designation of the transitions observed here. The Cologne Database for Molecular Spectroscopy, CDMS (cite: Muller2001; Muller2005), provides a comprehensive list of the best estimate of the transition frequencies, the excitation energies, and the quantum mechanical line strengths. Column 5 gives the central velocity of the line as obtained from fitting a soft parabola (see Methods [3.4.1](#datared)). Column 7 gives the maximum recoverable scale for the ALMA observations.

To check whether our observations suffered from resolved-out flux, we compared spectra extracted from the ALMA data with previous observations of the same lines taken with the APEX single antenna (cite: De-Beck2020) as shown in Fig. [13](#lostflux). For CO we found 66% of the flux was resolved out, whereas all the flux was recovered by ALMA for SiN. We were unable to make the same comparison for SiC, which is a first detection, or HC$_3$N, which was at best only tentatively detected with APEX (cite: De-Beck2020). Although only a third of the CO flux was recovered by ALMA, it is only smooth large-scale flux that is resolved out. This large scale flux is mostly associated with smoother bulk outflows, whereas our analysis in the present work focuses on smaller structures in the wind — i.e., the missing CO flux does not impede the present study.

Out of the other molecular lines discussed here and which have previously been observed, we found that about 28% of the flux in H$^{12}$CN $J=3\to2$ was resolved out (Fig. [16](#otherlostflux)). Some degree of lost flux was expected because this line was not observed with the most compact configuration of ALMA. The corresponding transition in H$^{13}$CN was not observed with APEX (cite: De-Beck2020) but since it was observed with the compact configuration of ALMA and shows more extended emission than H$^{12}$CN, we can assume very little, if any, flux was resolved out for H$^{13}$CN. For SiO, SiS and CS, most of the flux was recovered, with only about 10–20% lost, as can be seen in Fig. [16](#otherlostflux), where we have compared the spectra of these three molecules and H$^{12}$CN observed with APEX and ALMA.

The $^{13}$CN emission in $N=2\to1$ at 217 GHz has a low SNR. Therefore, to better determine the spatial distribution of $^{13}$CN, we combined the two most intense components of the many possible fine and hyperfine structure transitions of the $N = 2 \to 1$ transition that span a 450 MHz wide range centred on 217.257 GHz.

We extracted the channels in the calibrated visibility data in the frequency ranges corresponding to $\upsilon_\mathrm{LSR}=-23\pm50$ km s$^{-1}$ around each of the rest frequencies and combined the channel selections aligned in velocity. The combined data set was assigned a fictitious rest frequency of 217.3055 GHz so that its central velocity corresponded to $-23~\mathrm{km\,s}^{-1}$, and we then made an image cube from the stacked visibility data and analysed this following the same procedure as for the other data cubes. Finally, we checked the two multiplets of $^{13}$CN listed in Table [1](#resolutions) individually for resolved-out flux and found that a little less than half of the flux was recovered for these lines.

For all the spectral lines studied here, except for and NS, we fit soft parabola profiles (cite: Olofsson1993) $$\begin{equation}
\label{eq:softpara}
F(\upsilon) = F_0 \left( 1 - \left[ \frac{\upsilon - \upsilon_\mathrm{cent}}{\upsilon_\infty} \right] ^2\right)^{\gamma/2}
\end{equation}$$ where $\upsilon_\mathrm{cent}$ is the central velocity of the line profile and $F_0$ is the flux at the centre of the line. The parameters $F_0$, $\upsilon_\mathrm{cent}$, $\upsilon_\infty$, and $\gamma$ are left as free parameters in the fit. Primarily this is done to obtain the central line velocities, which are included in Table [1](#resolutions). The soft parabola profile was chosen over a Gaussian profile because the majority of the lines studied here exhibit double-peaked emission and hence significantly deviate from Gaussian line profile shapes. was excluded from this analysis because its hyperfine structure dominates its line profile, and NS was excluded because the spectrum is too noisy to obtain a reasonable fit. The central velocities of the lines were generally in agreement with the previously measured stellar LSR velocity of $\upsilon_\mathrm{LSR} = -23~\mathrm{km\,s}^{-1}$ (cite: Danilovich2014; De-Beck2020) and will be discussed in more detail in the following sections.

### AGB angular diameter

We took the calibrated data for all ALMA configurations combined, excluding channels with line emission, and fit a uniform disc (UD) to the visibilities (as in (cite: Homan2021)). This gave a diameter of 16.6 mas, containing 8.0 mJy. There was negligible ellipticity or displacement of the centroid. At mm wavelengths, a UD is expected to be a better representation of stellar brightness distribution than a Gaussian distribution. The SNR is $>100$, suggesting sub-mas precision, based on the nominal uncertainty of beam size divided by SNR, but taking into account possible irregularities in the stellar disc, we adopt a conservative uncertainty of 3 mas. The diameter of $16.6\pm 3$ mas is the size of the the surface where electron-neutral free-free emission dominates and is optically thick (at these wavelengths (cite: Vlemmings2019)) and corresponds to a radius of $3.3\pm 0.6$ au at our adopted distance. We note that the resolution of the continuum image from the extended array is $21\times 24$ mas (cite: Gottlieb2022), while for the combined continuum image it is $40\times 33$ mas. The optical diameter is $11.6\pm 1.8$ mas (cite: Richichi2005), 34% smaller than our value. Vlemmings et al. (cite: Vlemmings2019) found that the mm-wave diameters of a small sample of AGB stars were 15–50% greater than the optical diameters, consistent with our finding. It has also been found that, in general, the mm-wave diameters of the ATOMIUM sample are 30–100% larger than the optical diameters (cite: Baudry2023).

### SiN and SiC

The SiN line we observe towards W Aql ($N,J=6,{13/2}\to5,{11/2}$) is a blend of three closely-spaced hyperfine components separated by about 0.8 and 0.5 MHz (Fig. [13](#lostflux)), and the frequency of the centroid is 262,155.78 MHz. The lower spin-rotation component ($N,J=6,{11/2} \to 5,{9/2}$) at 262.650 GHz falls just outside of the frequency range covered by our observations. The SiC line detected towards W Aql corresponds to the $J= 6\to5$ transition in the lowest fine structure ladder $^3\Pi_2$ (cite: Cernicharo1989). The corresponding $J= 6\to5$ rotational transitions in the $^3\Pi_1$ and $^3\Pi_0$ upper fine structure ladders fell between the frequency bands covered by our observations.

Neither SiN nor SiC were detected for any other stars in the ATOMIUM sample, all of which are oxygen-rich aside from one other S-type AGB star ($\pi^1$ Gru). SiC has been previously detected towards 12 carbon-rich AGB stars (cite: Massalkhi2018), but the present work represents the first detection of SiC in the envelope of an S-type AGB star. SiN has been previously detected towards W Aql (cite: De-Beck2020) and only one other star: the nearby carbon-rich AGB star CW Leo (cite: Turner1992), which is suspected of having a companion (cite: Cernicharo2015a; Decin2015; Siebert2022). Spatially resolved Submillimeter Array (SMA) observations towards CW Leo show the SiN mainly distributed in a shell-like pattern, with some brighter, asymmetric, emission to the south-west (cite: Patel2013). However, a detailed analysis of these observations has not yet been published and, consequently, we lack detailed spatial information for SiN around other stars with which to compare our W Aql results. Spatially resolved SiC emission has also been observed towards CW Leo, for which SiC was not detected in the innermost regions of the CSE but rather in outer shells (cite: Velilla-Prieto2019a), possibly also showing some asymmetry to the south-west (cite: Patel2013). Further discussion of SiC distributions is given in Methods [3.6.1](#chem:sin)).

The integrated intensity maps of SiN (Fig. [1](#sin)a) and SiC (Fig. [5](#sic)a) show emission primarily north and east of the AGB star. The SiN emission has a higher SNR and is hence more readily analysed. Therefore, we have focussed our analysis on SiN, but note that the SiC observations agree with the conclusions drawn from SiN.

We produced a series of position-velocity diagrams of SiN using a wide slit (total width $3^{\prime\prime}$) to encompass all the emission seen in the zeroth moment map (Fig. [1](#sin)a). Using a narrower slit (such as $0.3^{\prime\prime}$) resulted in a lower SNR in the PV diagram, making an analysis more troublesome. We tested all possible slit angles passing through the position of the AGB star in increments of $5^\circ$ and then $1^\circ$ around the angles producing the most distinct PV diagrams. The final slit position of $33^\circ$ east of north was chosen on the basis of the clarity and intensity of the associated PV diagram. Even though the slit angle was determined independently, we find that it passes through the present position of the F9 star (Fig. [1](#sin)a). As shown in Fig. [1](#sin)b, the PV diagram of SiN exhibits an arc-like structure in position-velocity space, tracing a little more than half an ellipse centred on the AGB star. We fit a parabola to the points in the PV diagram with intensities $\geq 3 \sigma$ above the noise, weighted by the flux at those points. The peak of the parabola, plotted in white in Fig. [1](#sin)b, is at $-24.1~\mathrm{km\,s}^{-1}$, which is in agreement with the central velocity we find for the spectral line (Table [1](#resolutions)). The emission distribution in the PV diagram does not precisely follow the shape of the parabola, particularly at the negative offset and extreme velocity edges of the emission, so we also plot a partial ellipse based on the position of the parabola (using the centre and peak of the parabola and with the half-width along the velocity axis set to $14~\mathrm{km\,s}^{-1}$), which better follows the shape of the emission at the most extreme velocities. We followed a similar procedure for SiC to produce a PV-diagram and fit a parabola to the arc of emission (Fig. [5](#sic)b). For SiC, the peak of the parabola is at $-23.5~\mathrm{km\,s}^{-1}$. We similarly plot a partial ellipse based on the parabola fit (velocity half-width $13~\mathrm{km\,s}^{-1}$), which also follows the emission at the most extreme velocities more closely.

In concert, the zeroth moment map and the PV diagram show that the SiN emission forms an arc to one side of the system, which is close to edge-on or perpendicular to the plane of the sky. We also plot the summed blue and red channels of SiN separately in Fig. [\[sinbluered\]](#sinbluered). Owing to the noisy edges of the contours, we could not conclusively determine whether there is an offset between them along the axis connecting the present positions of the AGB and F9 stars. Consequently, we take the orbital inclination of the system to be $i=90\pm7^\circ$, where the uncertainty is derived from the beam size. The lack of spherical symmetry in the SiN emission suggests a spatial dependence for the formation of SiN, as discussed in Methods [3.6](#chemmethods) and depicted in Fig. [10](#SiNsketch). Despite the lower SNR of the SiC emission, the similar structure seen in the PV-diagram for SiC indicates a similar formation history for both SiN and SiC.

### NS

Two rotational transitions of NS were covered by the ATOMIUM observations — the $J=11/2 \to 9/2$ hyperfine split multiplets in the $^2\Pi_{1/2}$ and $^2\Pi_{3/2}$ spin-orbit fine structure components. Neither rotational transition was detected in spectra centred on the AGB star. However guided by predictions from chemical models (Methods [3.6.2](#nschem) and (cite: Van-de-Sande2022)), we conducted a more careful search for NS. The transition in the ground $^2\Pi_{1/2}$ component lies very close to the edge of our frequency band and is difficult to discern in the spectra, but we successfully detected it in the zeroth moment map (Fig. [14](#nsplot)a), which constitutes the first detection of NS towards an S-type AGB star. The corresponding rotational transition in the upper ($^2\Pi_{3/2}$) spin-orbit component at 255.597 GHz (cite: Lee1995) lies about 322 K above the ground state and is estimated to be about three times less intense. We found an upper limit for the $^2\Pi_{3/2}$ component of 3$\sigma = 0.047$ Jy beam$^{-1}$ km s$^{-1}$ in a zeroth moment map that covers the same velocity extent as that observed for the ground $^2\Pi_{1/2}$ component.

Prior to this, NS had been detected towards just one AGB star, the oxygen-rich IK Tau (cite: Velilla-Prieto2017; Decin2018) (and notably has not been detected towards the nearby carbon star CW Leo). An enhanced abundance of NS is expected to be a good tracer of binarity for S-type or oxygen-rich AGB stars with main sequence or white dwarf companions (cite: Van-de-Sande2022).

We checked the ATOMIUM data for NS detections towards other sources. While we could rule out NS detections in several sources, for a selection of others (the AGB stars IRC +10011 and IRC $-$10529, and the red supergiants VX Sgr and AH Sco) we could not conclusively confirm or rule out the presence of NS for three reasons. First, the $^2\Pi_{1/2}$ component at 253.968 GHz lies close to the edge of an observed band in frequency space, meaning that the line may be partially truncated, as it is for W Aql. Second, that line lies close to the SO$_2$ ($J_{K_a,K_c} = 15_{6,10}\to 16_{5,11}$) line at 253.957 GHz and, for the oxygen-rich sources mentioned above, we cannot easily disentangle which emission comes from SO$_2$ and which might come from NS. (This is not a problem for W Aql, towards which no SO$_2$ lines are detected, including more intrinsically intense lines covered by our observations.) Disentangling NS and emission is made more difficult because both lines are truncated by the edge of the observed band. Finally, we also checked for emission from the $^2\Pi_{3/2}$ component at 255.597 GHz but could not confirm the detection of this line of NS. For the AGB stars mentioned above, we did not detect emission above the noise of our observations. However, if we take the expected intensity of the $^2\Pi_{3/2}$ component to be a third that of the truncated and possibly blended line around 253.968 GHz, we determine that the expected intensity is below the noise of our observations. For the two red supergiants, the potential NS line is blended with a high-energy SO$_2$ line, ($J_{K_a,K_c} = 51_{7,45}\to 50_{8,42}$) at 255.595 GHz. Therefore, to determine whether NS is present in these or other ATOMIUM stars, observations of other NS transitions that do not overlap with SO$_2$ or other molecular lines are required.

In addition to the zeroth moment map, we also constructed a PV diagram of NS (Fig. [14](#nsplot)b). The only significant region of emission that is $3\sigma$ above the noise in the PV diagram is located on the red side of the PV diagram and not notably offset from the position of the AGB star. This is close to some of the most intense regions seen in the SiN and SiC PV diagrams. We note that because the NS line is on the edge of the observed band, some redder emission might not have been recovered by our observations. To emphasise that this is a true detection of NS rather than a misidentified line, we plot the spectrum of the NS line with the spectra of the SiN and SiC lines in Fig. [14](#nsplot)c. All lines were extracted from circular apertures with radii $0.25^{\prime\prime}$, centred on the continuum peak, which was chosen to best show the NS line. All three lines have a double-peaked profile, with SiN and NS having a brighter red peak than blue peak. Although the NS spectrum is truncated at $-9~\mathrm{km\,s}^{-1}$, it can be seen rising in a profile similar to the SiN and SiC red peaks. Deeper observations targeting NS would confirm this behaviour.

### HC$_3$N

Four successive rotational lines of HC$_3$N were detected towards W Aql as part of the ATOMIUM project (Table [1](#resolutions)). Prior to this, the three lowest transitions in this group were tentatively detected towards W Aql with APEX (cite: De-Beck2020).

A comparison of the lines tentatively detected with APEX and our ALMA data suggests that the ALMA data does not suffer from resolved-out flux. It should also be noted that the $J=25\to24$ and $J=27\to26$ lines were observed with all three ALMA configurations (including the compact configuration), while the $J=26\to25$ and $J=28\to27$ lines were observed with only the extended and medium configurations. All four lines have similar intensities when the spectra are extracted from our combined data cubes, as expected for lines with similar energies (the lower level energies span 131–165 K) and Einstein $A$ coefficients. Taken together, our observations confirm that there is no flux resolved out for the observations with the medium configuration. Most of the HC$_3$N flux is located south and west of the present location of the AGB star (Figs. [2](#fig:cn) and [15](#hc3n)), in direct contrast with the observed flux of SiN and SiC (Figs. [1](#sin) and [5](#sic)).

### CO

The CO $J=2\to1$ line has the most extended emission distribution of all the spectral lines observed towards W Aql as part of the ATOMIUM Programme. Although only one third of the flux was recovered by ALMA (Methods [3.4.1](#datared)), our analysis focuses on smaller structures in the wind, which are not affected by resolved-out flux.

Many complex structures are seen in the CO emission, making a definitive analysis difficult. We first examined the inner wind region, where an overdensity thought to be (part of) a spiral arm was reported (cite: Brunner2018). In this region, we found an approximately circular structure that corresponds very well to the location of the overdensity and to the radius of the observed SiN emission. In Fig. [3](#coarcs)b, we plot the CO emission close to the AGB star using a logarithmic colour scale and overplot the contours of SiN (as seen in Fig. [1](#sin)a) and a black circle to guide the eye to the roughly circular structure. The radius of this circle is $1.35^{\prime\prime}$ and its centre is $0.1^{\prime\prime}$ to the north of the AGB star.

Additional circular structures in the CO emission were more difficult to concretely identify, so we plotted the radial intensity against anticlockwise angle to help find such structures (Fig. [8](#angrad)). Circular structures centred on the AGB star would appear as horizontal lines in such a plot, whereas off-centre circular structures appear as sinusoids. Using the angle-radius plot, we found off-centre circles corresponding to: (red) the edge of the bright central region with a radius of $4^{\prime\prime}$, (pink) a circular structure surrounding this region, with a radius of $5.5^{\prime\prime}$, and (white) another circle with radius $10.75^{\prime\prime}$ which falls close to the edge of the ALMA field of view. The white circle is offset in the same direction (north) as the black circle. Note that the sinusoid corresponding to the black circle identified above can be seen more clearly in the angle-radius plot when it is zoomed in on the structures closer to the AGB star (bottom panel of Fig. [8](#angrad)). In Fig. [23](#angrad-no-lines) we show the same angle-radius plots as in Fig. [8](#angrad), but exclude the coloured lines highlighting the aforementioned structures.

We plot all these circular structures in Fig. [3](#coarcs)a over the averaged central three channels of the CO emission. From our analysis with the hydrodynamic model (Methods [3.7](#hydro)) we come to the conclusion that the black and white circles were formed during the periastron passage of the two stars, in which case they are expected to be offset to the opposite side of the AGB star from the F9 star. The periastron origin of the black circle is also supported by its co-location with the SiN arc. The red and pink circles, and other irregular structures, are not directly reproduced by the hydrodynamic model, but this is likely because of limitations in the model including missing physics around pulsations and the wind launching mechanism (see discussion in Methods [3.7](#hydro)). Significantly, the wind is launched at $13~\mathrm{km\,s}^{-1}$ in the hydrodynamic model, whereas previous studies assume a much lower initial velocity of $3~\mathrm{km\,s}^{-1}$, close to the sound speed. This discrepancy prevents a dense inner region forming in the hydrodynamic model, such as the region encircled in red in Fig. [3](#coarcs)a. We also note that the formation timescales of the red and pink circles and other neighbouring features are $~\lesssim 300$ years (taking $\beta$-law wind acceleration into account) and do not match the longer timescale of the binary orbit inferred from resolved imaging (Methods [3.3](#photmethods)).

When comparing these circular structures with the lower-resolution ($0.47\times 0.41$) ALMA observations of CO ($3\to 2$) around W Aql (cite: Ramstedt2017), in which several circular arcs were identified, we find that our red, pink and white circles correspond to the locations of those arcs. In particular, the outermost arc in the earlier data corresponds well with our white circle, and the innermost two arcs (north and south-west) match the position of our red circle. The circular region of higher flux that we have indicated in red in Fig. [3](#coarcs)a for CO ($2\to 1$) also corresponds to the region of higher flux seen in CO ($3\to 2$). The remaining arcs identified by (cite: Ramstedt2017) match our pink circle and a few other structures seen in our data which do not form full circles. Note that our black circle is too small to be well resolved in the earlier data.

The shell-like structures seen around W Aql have some similarity to previously reported shells around the carbon star CW Leo, which are also not perfectly centred on the AGB star (cite: Cernicharo2015a; Decin2011; Guelin2018). Many more shells are seen for CW Leo than W Aql, likely in part because CW Leo is closer, making emission easier to detect. Studies of the CW Leo shells have concluded that they could be caused by an eccentric binary orbit seen perpendicular to the line of sight, and assumed some periods of enhanced mass loss (cite: Cernicharo2015a; Guelin2018). Our hydrodynamic models do not assume a variable mass-loss rate (see Methods [3.7](#hydro)) but still form shell-like structures when viewed perpendicular to the orbital plane. This does not mean that the mass-loss rate of W Aql cannot be variable — indeed variable or anisotropic mass-loss might account for some of the other structures seen in the CO emission. The possible effects of variable and anisotropic mass loss are discussed in more detail in the Supplementary Materials [5.2](#sec:anisotropies).

We also analysed the higher and lower velocity channels of the W Aql CO emission, particularly in comparison to the hydrodynamic model. A long-standing unexplained phenomenon is excess emission in the blue wings of the line profiles of CO and other molecules towards W Aql (cite: Danilovich2014). In our ALMA observations of CO (Fig. [7](#cochan)), it is clear that the blue- and red-shifted channel maps are not symmetric around the LSR velocity. The blue channels ($-37$ to $-30~\mathrm{km\,s}^{-1}$) show slightly asymmetric emission, with an elongation in the south-west direction, while the red channels ($-14$ to $-8~\mathrm{km\,s}^{-1}$) show emission with more circular symmetry. These differences in shape account for the excess emission in the blue wing of the line profiles. We also compared these different emission distributions with the equivalent distributions produced by the hydrodynamic model after processing by the radiative transfer code MCFOST (Methods [3.7](#hydro)). In Fig. [12](#otherCOchans) we plot two CO channels equidistant from the LSR velocity and the equivalent model channels. The model also shows the elongated CO emission for the blue channel and the more circular emission for the red channel, reinforcing that the asymmetry arises from the companion’s interactions with the AGB wind.

### Other molecular species

The species SiO, SiS, HCN, and CS are commonly observed in the envelopes of many AGB stars of all chemical types (cite: Ramstedt2009; Schoier2013; Danilovich2018; Massalkhi2019). All four molecules were observed previously towards W Aql at a lower spatial resolution of $0.55^{\prime\prime}\times 0.48^{\prime\prime}$ (cite: Brunner2018) and were analysed using radiative transfer models under the assumption of spherical symmetry. Our new observations were obtained at a much higher angular resolution and the emitting regions for all four molecules are very well resolved (Table [1](#resolutions) and Fig. [6](#othermol)). The increased angular resolution allows us to observe asymmetries in the emission. The emission from all four molecules is more extended to the north-east than to the south-west. This is a qualitatively similar anisotropy to that seen in SiN, but unlike SiN, the more common species exhibit roughly spherically symmetric emission across a much wider fan-like region, running clockwise from east to north west (Fig. [6](#othermol)). In the context of an eccentric binary companion, we interpret this not as enhanced production of SiO, SiS, HCN, and CS triggered during the periastron passage (as we conclude in the cases of SiN and SiC), but as enhanced destruction through photodissociation of SiO, SiS, HCN, and CS by the F9 companion, during the large portion of the orbital period it spends to the southwest of the AGB star. If this were not the case, we should see significantly less emission to the northwest and southeast (i.e. the other regions where we do not see SiN), but the contours in Fig. [6](#othermol) have similar extents from the southeast to northeast to northwest. This is especially apparent in plots of the central channels of SiS and CS, shown in Fig. [17](#cssissinglechans), which show significantly reduced emission near the F9 star as opposed to on the opposite side of the AGB star. For CS, the $3\sigma$ contour centred on the AGB stars extends out to $0.33^{\prime\prime}$ ($\sim 2\times 10^{15}$ cm) from the AGB star in the direction of the F9 star, compared with $0.71^{\prime\prime}$ ($\sim 4\times 10^{15}$ cm) in the opposite direction. For SiS, the $3\sigma$ contour centred on the AGB star extends out to $0.09^{\prime\prime}$ ($\sim 5\times 10^{14}$ cm) in the direction of the F9 star and out to $0.23^{\prime\prime}$ ($\sim 1\times 10^{15}$ cm) in the opposite direction.

Furthermore, the PV diagrams of CS, SiO and , taken along the same axis as we used for SiN and plotted in Fig. [18](#CSPV), show the brightest emission spatially close to the AGB star, not in an arc as for SiN or SiC. They also show that the emission is consistently less extended and less intense on the side of the AGB star where the F9 star is located. Notably, this is not the case for CO, also plotted in Fig. [18](#CSPV), which does not show evidence of photodissociation by the F9 star, as expected given its stronger bond energy and self-shielding (cite: Morris1983).

The reduced emission seen in the spectra around the F9 star (Methods [3.4.8](#sec:F9spec)) is further evidence of most molecules being destroyed by the F9 flux.

Another molecular species that displays highly asymmetric emission around W Aql is $^{13}$CN. Although the main isotopic species, $^{12}$CN, was not covered in the ATOMIUM observations, it has previously been observed towards W Aql with the IRAM 30m telescope (cite: Bachiller1997). We find that, unlike the common molecular species discussed above, the $^{13}$CN emission is mainly seen on the opposite side of the AGB star. As can be seen from the zeroth moment maps of H$^{13}$CN and $^{13}$CN in Fig. [2](#fig:cn), the $^{13}$CN emission is mainly observed where the H$^{13}$CN emission is absent, which is consistent with the generally accepted notion that CN is a photodissociation product of HCN (cite: Huggins1984). This is discussed in more detail in Methods [3.6](#chemmethods).

### Molecular emission around F9 star

We extracted spectra in circular apertures of radii 100 mas (corresponding to a projected radius of 40 au) centred on the F9 star to check for anomalous emission. Very few lines were detected above the noise in these spectra, with lines originating only from CO, SiO, CS, and HCN. We compared the line profiles extracted from the region around the line-of-sight position of the F9 star with profiles of the same sized aperture centred on the AGB star and plot comparisons for CS, HCN and SiO in Fig. [9](#F9spec). Notably, the F9-centred line profiles exhibit relatively more flux in the blue channels and less flux in the red channels than the corresponding AGB-centred profiles. The F9-centred profiles also tend to have relatively less emission in the channels close to the LSR velocity. From this, we can estimate that the F9 star is located, spatially, in the region that corresponds to gas with velocities close to the AGB stellar LSR velocity, i.e. gas with motions approximately in the plane of the sky. This estimate is possible because, in an expanding circumstellar envelope, the velocity axis has a correspondence to the line of sight spatial axis (see, for example, (cite: Guelin2018)). Although this does not say anything about the present velocity of the F9 star (it need not be moving at the same velocity as the AGB circumstellar gas that it is moving through), it is consistent with the stars being in a highly eccentric orbit, as the present relative motion of the F9 star would be predominantly in the plane of the sky rather than into or out of the plane of the sky, and would, in any case, have a low absolute total velocity of $\sim2~\mathrm{km\,s}^{-1}$.

We also checked the shape of the line profiles extracted for an equivalent 100 mas aperture on the opposite side of the AGB star from the F9 star (at the same projected separation) and found that those line profiles were more similar to the AGB-centred line profiles than those centred on the F9 star (Fig. [9](#F9spec)). Finally, we note that the phenomenon of the blue peaks being brighter than the red peaks for the F9-centred profiles is the opposite of what we see for the line profiles of SiN and NS (Fig. [14](#nsplot)c) centred on the AGB star. This is easily explained by the different formation/destruction times of the two groups of molecules: SiN and NS formed during the periastron passage, whereas CS, HCN and SiO are presently being (partly) photodissociated by the UV flux of the F9 star.

The intensity of the UV flux from the F9 star is proportional to the inverse square of the distance from the star. This means that the apparent UV flux close to the AGB star, taking the projected separation of 194 au, is 24 times less than the flux 40 au from the F9 star, and the flux on the opposite side of the AGB star (at a distance of 388 au) is 94 times weaker. At a distance of 10 au from the F9 star, close to the distance between the two stars during periastron, the UV flux would be 380 times higher than the flux on the same region at the present stellar separation. Note that these values are rough estimates and do not include, for example, UV extinction by dust, which would further reduce the UV flux for larger distances when there is more dust between the F9 star and the region of interest.

## Radiative transfer modelling

Radiative transfer calculations were undertaken to approximate the abundance of SiN in the arc seen in Fig. [1](#sin). To achieve this, we extracted the SiN spectra from round apertures with radii of $0.25^{\prime\prime}$, evenly spaced with centres separated by $0.3^{\prime\prime}$ starting from the continuum peak and moving outwards along the north $33^\circ$ east line passing through the emission. The set-up is shown in Fig. [11](#sin-modelling)a, where the regions are labelled from A to H. The aperture size was chosen so as to not lie outside of the detected SiN emission. Furthermore, these regions are centred along the same axis for which we found the best PV diagram (Fig. [1](#sin)b and Methods [3.4](#almadata)), so they are unlikely to overlap with the edges of the SiN emission. Therefore, by considering only spectra from the regions plotted in Fig. [11](#sin-modelling)c, we can use a 1D (spherically symmetric) radiative transfer model to compare equivalent synthetic spectra and determine the SiN abundance distribution in the arc, which can also be approximated by a wedge of a spherical shell. Our approach is viable because the SiN emission is expected to be optically thin (and indeed we find a peak tangential optical depth of $\tau \lesssim 0.2$ in the model) and emission in other parts of the spherically symmetric model (at different velocities) is not expected to interact with emission in the regions of interest.

We used the accelerated lambda iteration method (ALI (cite: Rybicki1991)), which has been previously used to determine the abundances of various other molecules in the CSE of W Aql (cite: Brunner2018; Danilovich2021). We use previously determined circumstellar parameters for W Aql (cite: Danilovich2014), including a radial temperature profile, the mass-loss rate of $3\times 10^{-6}\;\mathrm{M}_\odot~\mathrm{ yr}^{-1}$ (cite: Ramstedt2017) and a velocity profile described by (cite: Danilovich2014) $$\begin{equation}
\label{betalaw}
\upsilon(r) = \upsilon_0 + (\upsilon_\infty - \upsilon_0) \left( 1 - \frac{R_\mathrm{in}}{r} \right)^\beta
\end{equation}$$ with $\upsilon_0 = 3~\mathrm{km\,s}^{-1}$ the velocity at the dust condensation radius, $R_\mathrm{in} = 2\times 10^{14}$ cm, $\upsilon_\infty = 16.5~\mathrm{km\,s}^{-1}$ the terminal expansion velocity and $\beta = 2$. The key stellar and circumstellar parameters are summarised in Table [2](#tab:parameters). We also included a previously implemented overdensity (cite: Brunner2018), which was found to improve the radiative transfer model fit for ALMA observations of CS and H$^{13}$CN at lower resolutions (cite: Brunner2018). The overdensity relates to an increase in the $\mathrm{H}_2$ number density by a factor of five between the radii of $8\times 10^{15}$ cm and $1.5\times 10^{16}$ cm (Fig. [11](#sin-modelling)), and is in good agreement with the location of a region of increased CO emission (a good tracer of density) traced by the black circle in Fig. [3](#coarcs)b. (Previously the overdensity was thought to be part of an unresolved spiral arm (cite: Brunner2018).)

We include SiN energy levels up to $N=20$ in the ground vibrational state and the 59 radiative transitions connecting those levels. The energy levels and Einstein A coefficients were calculated using `CALPGM` (cite: Pickett1991) and take fine structure into account but neglect the closely spaced hyperfine structure, which is not resolved in our observations. There are no calculated or measured collisional (de)excitation rates for SiN, so instead we use the rates calculated for CN-He (cite: Lique2010), scaled by 1.37 to account for the different reduced mass of the SiN-$\mathrm{H}_2$ system.

On the basis that the different extraction apertures shown in Fig [11](#sin-modelling)a probe different regions of the SiN distribution, we tried various shapes for the radial distribution of SiN abundance in an attempt to reproduce the observed distribution of SiN. These included a constant abundance, step functions of different constant SiN abundances, and Gaussian shells of various widths and positions. We also left the inner and outer radii of the SiN emitting region as free parameters. We found that while the two apertures farthest from the continuum peak, G and H, were sensitive to the outer radius and outer abundance of the SiN distribution, as expected, the inner apertures, A to D, were also sensitive to these properties, which affected the heights of the emission peaks in their double-peaked profiles. Conversely, the choice of inner radius and the innermost abundance of SiN mainly affected the heights of the line centres for apertures A to C. These dependencies were expected given the observed wedge of SiN emission.

Our best-fitting model has a constant outer SiN abundance relative to $\mathrm{H}_2$ of $1.5\times 10^{-7}$, from $6\times 10^{15}$ cm to $2\times 10^{16}$ cm, and a power-law distribution in the inner part, starting from an inner radius of $1.5\times 10^{15}$ cm. This distribution is plotted in Fig. [11](#sin-modelling)b, where we also show the $\mathrm{H}_2$ number density over the same region, including the aforementioned overdensity. As can be seen from Fig. [11](#sin-modelling)b, the extended peak of the SiN abundance spans the region of the $\mathrm{H}_2$ overdensity. This further supports the idea that both phenomena have a common cause, which we postulate is the periastron passage of the AGB and F9 stars. The line profiles generated by the best fitting models are plotted with the spectra in Fig. [11](#sin-modelling)c.

## Chemical modelling

The recent results of Van de Sande and Millar (cite: Van-de-Sande2022) focus on the effect of close companions on the circumstellar chemistry. In Fig. [19](#fig:chemsin) we reproduce their results for stars with similar wind density to W Aql \[Model: $\dot{M}/\upsilon_\infty = 2\times 10^{-6}~\;\mathrm{M}_\odot~\mathrm{ yr}^{-1}/(\mathrm{km\,s}^{-1})$ compared with W Aql: $\dot{M}/\upsilon_\infty = 1.8\times 10^{-6}~\;\mathrm{M}_\odot~\mathrm{ yr}^{-1}/(\mathrm{km\,s}^{-1})$\], showing the predicted abundances of SiN, SiC and NS for both oxygen- and carbon-rich outflows, with and without an F9-like companion. The companion is approximated by a black body at 6000 K and does not explicitly include chromospheric UV photons. However, observations of W Aql with GALEX in 2006 reveal a detection in the near UV (22.16 mag, 1771–2831 Å) but not in the far UV ($>22.5$ mag, 1344–1786 Å) (cite: Montez2017), the latter being more important for breaking molecular bonds. If additional chromospheric UV flux is generated around periastron, as has been suggested for other types of stars in close binary systems (cite: Schrijver1987; Galvez2002), then this would mainly serve to increase the products of UV photochemistry, such as , which are discussed below. An excessively large UV excess during periastron could possibly destroy a larger variety of molecular species than predicted, but this would occur over a relatively short timescale (see Table [3](#tab:solutions) and Methods [3.9](#sec:solution)) and would not preclude further chemical interactions, including many of the formation channels discussed below, once the stars moved further apart.

### SiN and SiC

The chemical models (cite: Van-de-Sande2022) show that, in the absence of a companion, the SiN radical is expected to form in a shell-like distribution, with a peak abundance at a radius of around $10^{16}$ cm from the AGB star (Fig. [19](#fig:chemsin)). The main formation pathway of SiN is via the measured reaction $$\begin{equation}
\label{sinform1}

\ce{NH3 + Si+ \to SiNH2+ + H}
\end{equation}$$ where NH$_3$ is assumed to be a parent species that is formed close to the AGB star and, through observations, has been found to have a peak abundance of $\sim2\times 10^{-5}$ relative to $\mathrm{H}_2$ (cite: Danilovich2014). This is followed by dissociative recombination $$\begin{equation}
\label{sinform2}
\ce{SiNH2+ + e- \to SiN + H2}
\end{equation}$$ The main source of Si$^+$ is the photodissociation of SiS, i.e. $$\begin{equation}
\label{sisphot}
\begin{aligned}
\ce{SiS + h\nu &\to Si + S}\\
\ce{Si + h\nu &\to Si+ + e-}
\end{aligned}
\end{equation}$$ which occurs very readily in the presence of the F9 companion (see Fig. [20](#fig:chemnsi)) and the UV photons it emits (cite: Van-de-Sande2022); and is confirmed in our observations (Fig. [6](#othermol)), because SiS is noticeably depleted to the southwest at the present position of the F9 star. We also note that there are minor formation pathways for SiN forming from HNSi and SiC, but both pathways also depend on and and hence are also affected by UV photons driving the formation of .

In the chemical models ((cite: Van-de-Sande2022) and Fig. [19](#fig:chemsin)), the main difference in the SiN abundance distributions between oxygen- and carbon-rich stars with the same wind density and no companion, is that the peak relative abundance of SiN is predicted to be $\sim10^{-8}$ for the oxygen-rich star and $\sim10^{-7}$ for the carbon-rich star. W Aql is an S-type star whose chemistry is presumed to be intermediate between the typical carbon-rich and oxygen-rich stars (cite: Danilovich2014),

and that is what has been found for the abundances of HCN in S-type stars (cite: Schoier2013). However we find that the peak abundance of SiN in W Aql ($1.5\times 10^{-7}$ relative to $\mathrm{H}_2$, see Methods [3.5](#rtmod)) is in good agreement with that predicted for a carbon-rich star, although the asymmetric distribution of SiN implies that the formation process is anisotropic.

Van de Sande and Millar’s study (cite: Van-de-Sande2022) focused on the impact of UV photons from stellar companions on the circumstellar chemistry of AGB stars. They include a set of models with a main sequence companion with a stellar effective temperature of 6000 K that is comparable to the temperature of an F9 dwarf (cite: Gray2009) (reproduced in Fig. [19](#fig:chemsin)). The radial abundance profile of SiN is significantly altered by the companion — i.e., the peak abundance of SiN in both the carbon- and oxygen-rich winds is higher, and the abundance of SiN in the inner part of the wind is also higher. For the oxygen-rich outflow, the inner abundance of SiN is higher at $\sim10^{-7}$, and it remains relatively constant until it begins to decrease at around $10^{16}$ cm; SiN does not exhibit a shell-like distribution, as it would in the absence of a companion, but rather a parent-like distribution with a high inner abundance followed by a Gaussian decline caused by photodissociation driven by the interstellar radiation field. For the carbon-rich outflow, a shell-like distribution is seen in the presence of the companion, but the peak abundance is higher ($\sim10^{-6}$) and the inner abundance of SiN is several orders of magnitude higher ($\sim2\times 10^{-9}$ relative to $\mathrm{H}_2$), than it would be if the companion were not present.

An underlying assumption in these models is that the companion star is always close to the AGB star (cite: Van-de-Sande2022). However, this is not the case for W Aql, as the projected distance between the F9 and AGB stars is presently 194 au or $2.9\times 10^{15}$ cm, rather than $2-5R_\star$ ($4-10\times 10^{13}$ cm) as assumed in the chemical models (cite: Van-de-Sande2022). A highly elliptical orbit, during which the F9 star passes within a few stellar radii of the AGB star, could result in the asymmetric emission by SiN that we see in Fig. [1](#sin), if the F9 star only drove the production of SiN while it was sufficiently close to the AGB star. In this instance, the temporary close proximity of the two stars is relevant, because the wind region close to the AGB star is the densest and the chemical reactions will occur more readily. For example, at 5 au from the AGB star, the $\mathrm{H}_2$ number density is $3\times 10^{9}$ cm$^{-3}$, whereas at the current projected distance of the F9 star, the number density is four orders of magnitude smaller, at $3\times 10^{5}$ cm$^{-3}$. Because the rates of chemical reactions generally depend on (the square of the) number density, a lower number density results in a corresponding decrease in reaction rates, and hence much lower SiN production. Even very fast periastron interactions (Table [3](#tab:solutions)) are still long enough to produce SiN, particularly as, for example, the photoionisation of Si to (Eq. [\[sisphot\]](#sisphot)) proceeds very quickly in the presence of the companion.

Once formed, we expect SiN to persist in the expanding circumstellar envelope until it is photodissociated by the interstellar radiation field, based on chemical modelling (cite: Van-de-Sande2022) and because it is not expected to participate in the formation of dust or other molecular species. In general, the photodestruction timescale of a molecule being dissociated by the interstellar radiation field depends on the photodissociation rate for that molecule and on the extinction, with higher extinctions meaning that fewer photons will penetrate to that region. This is taken into account in the chemical models and accounts for the drop off in abundance in the outer regions of the CSE (Fig. [19](#fig:chemsin)), which, for SiN, agrees with the location of the drop off we found from radiative transfer modelling (Methods [3.5](#rtmod)). The additional UV photons originating from the F9 star only have a relatively local effect on the chemistry of the CSE; as discussed in Methods [3.4.7](#sec:othermolecules) and [3.4.8](#sec:F9spec) and shown in Figures [6](#othermol) and [9](#F9spec), the F9 star contributes to photodissociation of molecules in its vicinity, but not on the opposite side of the CSE.

SiC behaves in a broadly similar way to SiN in the chemical models, with and without the inclusion of a main sequence companion ((cite: Van-de-Sande2022) and the middle panel of Fig. [19](#fig:chemsin)). For both carbon- and oxygen-rich CSEs without a companion, SiC is expected to be distributed in a shell around the star, albeit with a more shallow gradient on either side of the peak than for SiN. For the carbon-rich star with a density similar to W Aql, the peak abundance of SiC is located at $\sim10^{16}$ cm from the AGB star and is found to be $\sim10^{-6}$ relative to $\mathrm{H}_2$, while for the oxygen-rich CSE, the peak of $\sim 5\times 10^{-9}$ is found slightly farther from the star at $\sim 3\times 10^{16}$ cm. The presence of an F9-like companion alters the SiC distribution in a similar way as for SiN, changing it from a shell-like distribution to a more centralised distribution. The abundance in the inner part of the distribution (i.e., in the region from the inner edge of the model to $\sim10^{16}$ cm) increases up to $\sim 2\times 10^{-5}$ for carbon-rich CSE; and $\sim 5\times 10^{-9}$ for the oxygen-rich CSE, where there is previously negligible SiC in this region without a companion (Fig. [19](#fig:chemsin)).

Analogous with SiN (Eqs. [\[sinform1\]](#sinform1) and [\[sinform2\]](#sinform2)), SiC mainly forms via $$\begin{equation}
\begin{aligned}
\ce{CH3 + Si+ &\to SiCH2+ + H}\\
\ce{SiCH2+ + e- &\to SiC + H2}
\end{aligned}
\end{equation}$$ with the same source of as explained in Eq. [\[sisphot\]](#sisphot). is formed either via photodissociation of , or through the successive hydrogenation of C. The former pathway is dominant for carbon-rich CSEs, while the latter is more likely in oxygen-rich CSEs. For an S-type star such as W Aql, both pathways may contribute to formation.

The formation of both SiN and SiC is driven by , which forms through the photoionisation of Si (Eq. [\[sisphot\]](#sisphot)). In Fig. [20](#fig:chemnsi) we plot the predicted abundances of with and without the presence of the F9 companion (cite: Van-de-Sande2022). While the abundance of naturally rises in the outer part of the envelope (beyond $\sim 10^{16}$ cm), owing to the interstellar radiation field, the inner abundance rises significantly in the presence of an F9-like companion. We note that although the abundance of rises to $10^{-9}$ to $10^{-7}$, for oxygen- and carbon-rich CSEs, respectively, this is still significantly less than the total abundance of Si ($6.5\times 10^{-5}$ relative to $\mathrm{H}_2$, assuming solar elemental abundances (cite: Asplund2021)), meaning that the photoionisation process driven by the F9 star is not expected to ionise all the Si.

### NS

In the absence of a companion, NS is expected to form in shell with a peak at about $10^{16}$ cm (cite: Van-de-Sande2022). For a carbon-rich CSE, the addition of an F9 companion does not cause a significant difference in the NS distribution. For an oxygen-rich CSE, however, the chemical model with an F9 like companion predicts a higher abundance of NS by almost an order of magnitude and significantly changes the shape of the distribution, resulting in a high abundance of NS in the inner wind ($\sim10^{-6}$ which decreases from around $5\times 10^{15}$ cm).

NS is formed via the photodissociation of (cite: Van-de-Sande2022) $$\begin{equation}
\label{nsform}
\begin{aligned}
\ce{N2 + h\nu &\to N + N}\\
\ce{N + HS &\to NS + H}
\end{aligned}
\end{equation}$$

Even though the rate of photodissociation of is relatively low because of the strong bond, the abundance of is thought to be high ($4\times 10^{-5}$ relative to $\mathrm{H}_2$ (cite: Agundez2020)). Therefore, even if only $\leq 1\%$ of is destroyed, enough N is liberated to form NS (cite: Van-de-Sande2022). The predicted abundance distribution of N, taking into account the presence of an F9-like companion, is plotted in Fig. [20](#fig:chemnsi). The detection of NS is tentative (Fig. [14](#nsplot)), but its co-location with the brightest region of SiN (especially in the PV diagram) and the predictions of chemical models that include an F9-like companion ((cite: Van-de-Sande2022) and Fig. [19](#fig:chemsin)), suggest that NS was likely formed during the periastron passage of the W Aql system, when the F9 star irradiated part of the inner wind.

### HCN, CN and HC$_3$N

HCN, CN and are closely linked species which have a wide astronomical literature in the context of the cyanopolyyne (H–(C$\equiv$C)$_n$–C$\equiv$N) family of molecules. HCN is a parent species formed close to the star (cite: Agundez2020), and CN has long been known to be a photodissociation product of HCN (cite: Huggins1984). At low temperatures (below 800 K (cite: Agundez2017)), where is seen towards W Aql, the main formation pathway for is from the two parent species HCN and (cite: Agundez2017; Cordiner2009):

$$\begin{equation}
\begin{aligned}
\ce{HCN +h\nu &\to CN + H}\\
\ce{CN + C2H2 &\to HC3N + H}
\end{aligned}
\end{equation}$$

For most molecular species, chemical fractionation of isotopologues is expected to be negligible around AGB stars. Hence, we can use the observations of and to understand the formation of . For the rest of this section, we omit the isotope labels. As can be seen in Fig. [2](#fig:cn), CN is preferentially detected on the side of the CSE where the F9 star is presently located, coinciding with a region of HCN depletion. We refer to this phenomenon as depletion because it aligns well with the location of the F9 star and of CN, and because the extent of HCN to the north east agrees well with the predicted extent of HCN in the chemical models, in the absence of a companion (cite: Van-de-Sande2022) (see also discussion in [3.6.4](#otherchem) below). Although the F9 star passes close to the AGB star during the eccentric orbit, the amount of time the stars spend close together is relatively short, $\lesssim 2\%$ of the orbital period (Table [3](#tab:solutions) and Methods [3.9](#sec:solution)), compared with the amount of time the F9 star spends to the south west of the AGB star, providing a relatively consistent source of UV radiation. A similar pattern of molecular depletion is seen for SiO, SiS and CS (Fig. [2](#fig:cn)) for the same reason.

HC$_3$N is present on the same side of the CSE as CN (Figs. [2](#fig:cn) and [15](#hc3n)), from which we can infer that the presence of CN preferentially drives the formation of HC$_3$N to the south and west of the AGB star. Although HC$_3$N has long been known to be present around carbon stars, W Aql is the first S-type AGB star towards which HC$_3$N has been observed. Although HC$_3$N and other carbon-bearing molecules such as C$_2$H and SiC$_2$ seem to indicate a carbon-rich circumstellar chemistry for W Aql (cite: De-Beck2020), the spectroscopic classification of W Aql marks it as an S-type star (cite: Danilovich2015). It is possible such carbon-bearing species are common around (some subset of) S-type stars more generally, but, to date, W Aql has been studied in the most detail.

has been most widely studied around the nearby carbon star CW Leo, where it is located mainly in a spherical shell centred on the star, well-resolved in ALMA observations and as predicted by chemical models (cite: Agundez2017; Van-de-Sande2022), with some enhancement in the inner regions which is thought to be driven by a companion (cite: Siebert2022). We do not see a symmetric shell-like distribution of HC$_3$N around W Aql (Fig. [15](#hc3n)), however we interpret the that we observe as part of a broken shell that is formed where CN is more abundant.

Although we expect that some CN — and subsequently HC$_3$N — would have formed during, or as a result of the periastron passage of the W Aql binary, these two molecules will have expanded with the CSE (as SiN has), to a radius that is comparable to the black circle in CO ($1.35^{\prime\prime}$, Fig. [3](#coarcs)). At this distance from the AGB star, some CN might remain but is not easily detectable above the noise in our observations. Some traces of are seen north of the AGB star in Fig. [2](#fig:cn), but the SNR of the observation is relatively low, partly because more than half of the flux was resolved out (Table [1](#resolutions)). We also note that , expected to be around 10 to 30 times more abundant (cite: Danilovich2014), was not covered by our observations. Hence, we cannot conclusively determine how much CN is present to the north east of the AGB star, relative to the apparently higher abundance of CN to the south west, closer to the F9 star. More sensitive observations, ideally covering and not subject to resolved out flux, would be required to fully understand the distribution of CN around W Aql. We note the CN we expect to be co-located with SiN, which should have formed during the periastron interaction, is harder to detect than SiN is, for several reasons relating to the molecular physics and energy level distributions of the two molecules. Although SiN is also subject to hyperfine splitting, the three most intense hyperfine components are only separated by $\sim$1.4 MHz, a tiny separation compared with the $30~\mathrm{km\,s}^{-1}$ (22 MHz) width of the SiN line, as can be seen in Fig. [13](#lostflux)(b). In comparison, the spectrally resolved hyperfine splitting of CN results in especially wide lines which have lower peak intensities than they would in the absence of hyperfine splitting. This makes them harder to detect above the noise. Furthermore, the dipole moment of SiN is around 1.8 times larger than for (cite: Kerkines2005; Thomson1968), resulting in intrinsically brighter lines for SiN.

The excitation conditions of the observed lines of HC$_3$N are such that we do not expect to see these same lines of HC$_3$N lines farther out in the wind than we do in Fig. [2](#fig:cn) ($< 0.5^{\prime\prime}$). Therefore, if any HC$_3$N is present at a radius of $1.35^{\prime\prime}$ from the AGB star, we would not have detected it in the present observations. We predict that in this region could be detected in more sensitive observations covering lower-energy transition lines.

### SiO, SiS and CS

The emission seen from SiO, SiS and CS (Fig. [6](#othermol)) — like that of HCN — indicates photodissociation driven by the F9 star during its time to the southwest of the AGB star, unlike SiN, SiC, and NS whose formation is driven by the brief but intense addition of UV photons from the F9 star to the inner CSE during the periastron passage.

This process works because it is the products of photodissociation and photoionisation that go on to form the observed SiN, SiC and NS.

However, this is not the case for SiO, SiS, CS and HCN, which are considered to be parent species in most chemical models (cite: Van-de-Sande2022; Agundez2020). Accordingly, the effect of a stellar companion is generally not to increase the abundances of these molecules in the inner CSE, but may potentially deplete them (cite: Van-de-Sande2022). Taking the case of a main sequence companion in the inner wind, the predictions are as follows: (i) for SiO in an oxygen-rich CSE, a minimal decrease of the inner abundance is predicted, compared with a decrease of almost an order of magnitude for the carbon-rich CSE; (ii) for SiS, the models predict a significant decrease of several orders of magnitude (4–6 dex) for both chemical types; however, this dramatic change could be the result of an uncertain photodissociation rate for this molecule; (iii) for CS and HCN, the change in abundance for both chemical types in the presence of a stellar companion is negligible. Hence we can conclude that the asymmetric distributions seen for SiO, SiS, CS and HCN (Fig. [6](#othermol) and [17](#cssissinglechans)) are caused by photodissociation from the F9 companion, rather than enhanced formation during periastron.

## Hydrodynamic simulations

To better understand the structure in the CO emission, we performed high-resolution 3D smoothed particle hydrodynamic (SPH, (cite: Monaghan2005; Price2012)) simulations of highly eccentric systems with parameters similar to the W Aql system.

These simulations were performed with the SPH code Phantom (cite: Price2018; Siess2022; Maes2021; Malfait2021). The AGB star and companion are represented by gravity-only sink particles, and the wind consists of $\sim 7\times 10^{6}$ SPH gas particles that are gradually launched from boundary shells around the AGB star, with a velocity of $13~\mathrm{km\,s}^{-1}$, mimicking a free wind and a constant mass-loss rate (cite: Siess2022). Cooling within the wind is regulated by the equation of state for an ideal gas with polytropic index $\gamma =1.2$, and the pulsations and rotation of the AGB star are not taken into account.

It is important to note that these hydrodynamic simulations are necessarily simplified compared to observations, as they mainly account for the gravitational impact of the companion on the wind, and neglect the impact of additional effects such as radiation, radiation pressure, pulsations, realistic cooling, and variable or anisotropic mass loss. We also note that the free wind approach does not reproduce velocities lower than $13~\mathrm{km\,s}^{-1}$, even though lower velocities are expected in the inner wind region (within $\sim80$ au of the AGB star). All of these contribute to the differences between the model and observations. Hence we aim for a qualitative understanding rather than a direct fit to the data.

We present results for a model with orbital parameters close to the W Aql system, with eccentricity $e = 0.92$ and semi-major axis $a = 125$ au, and taking the masses of the W Aql system (Methods [3.1](#dist-notes)). The Phantom model was evolved for around 5000 years and the snapshot that we plot in various figures was selected from a time step a little earlier than this to better match the current positions of the two stars. From a detailed analysis of the Phantom model we found that the orbital period increased slightly with time, owing to the mass being lost by the AGB star. This corresponded to a small increase in the semimajor axis but no change in the eccentricity over the time of the simulation. In Fig. [3](#coarcs)c, we show the density distribution in a slice perpendicular to the orbital plane of this model.

Plots of the same model showing the inner regions and a slice through the orbital plane are given in Fig. [24](#faceonSPH). In general, we expect the companion to generate a spiral-like structure in the wind (cite: Maes2021; Malfait2021; Mastrodemos1998; Mastrodemos1999). However, owing to the high eccentricity of this system, concentric near-spherical density structures are created in the wind, visible as the near-circular structures in the edge-on density distribution in Figs. [3](#coarcs)c and [24](#faceonSPH)b. The circular structures are not quite centred on either of the central stars but rather offset to the opposite side from the F9 position at apastron, similar to the offsets we find in the ALMA CO observations.

These structures are remarkably similar to the circular structures traced out by the black and white circles in Fig. [3](#coarcs)a.

The offset centres of the circles, particularly the outer circle, agree well with the observed ALMA data (white circle in Fig. [3](#coarcs)a). Similar structures at a $90^\circ$ edge-on inclination were seen for other highly eccentric SPH simulations we performed, and are also seen in previous studies with $e=0.8$ and mass ratio $M_1/M_2= 2.75$, compared with 1.5 for the W Aql system (cite: Kim2019).

From a close study of our hydrodynamic simulations, we determine that the concentric circles are formed during the relatively quick periastron passage of the F9 star. During the periastron passage, the stars reach their maximal orbital velocity ($\sim 17~\mathrm{km\,s}^{-1}$ for our chosen orbital parameters) and move hypersonically through the wind (which has a sound speed of $\sim 3~\mathrm{km\,s}^{-1}$ at 10 au), resulting in near-spherical shocks. The funnel-like structure (see Fig. [3](#coarcs)c) is formed through gravitational interactions between the companion and the wind. More concretely, when the companion moves towards the AGB star shortly before the periastron passage, its gravitational force results in a high-density wake behind the companion (see first and second columns in Fig. [\[fig:peri\]](#fig:peri)). Because there is a velocity dispersion within this wake, it is delimited by a radially faster outer edge and a denser inner edge. As the companion and the AGB star pass each other quickly during periastron passage, the inner edge is shaped as a circular high-density shock, that travels radially outwards and expands as the left side ($x<0$) of the 3D sphere-like structure. Because the wind-companion interaction around periastron passage is strong, the outer edge of the wake becomes a bow shock after periastron passage (second and third columns of Fig. [\[fig:peri\]](#fig:peri), (cite: Malfait2021)). The formation of the spherical high-density shock is enhanced, and is completed on the right side ($x>0$), by the fast wobble of the AGB star. The orbital velocity of the stars reaches a maximum absolute value during this close encounter, however, the direction of the orbital velocity vectors changes by almost 180 degrees due to the elliptical nature of the orbit. The wobble of the AGB creates a strong gradient in the radial wind velocity (mainly of the material on the $x>0$ side of the AGB, where the wind is not disturbed by the companion shock wake). The transition from faster outflowing material to slower wind particles results in a low-density region (around $x=40$–80 au in the right column of Fig. [\[fig:peri\]](#fig:peri)). The edge between this low-density region and the inner denser material completes the spherical high-density shock (see the bottom row of Fig. [\[fig:peri\]](#fig:peri), showing the orbit with an inclination of $90^\circ$). The spherical structures are slightly offset because of the movement of the stars.

From this, and the similar results of (cite: Kim2019) and (cite: Cernicharo2015a), we can conclude that such circular structures are typical of highly elliptical systems, including when those systems are seen edge on.

We emphasise that the circular structures are a consequence of binary interaction and do not, in our model, represent a period of enhanced mass loss. This is in contrast with the simplified model of CW Leo (cite: Cernicharo2015a) where the increase in density was caused by an assumed increase in mass-loss rate during periastron, in addition to the wobble of the AGB star. Some discussion of the impact of anisotropic mass loss is given in the Supplementary Materials [5.2](#sec:anisotropies). To illustrate the effect of our constant mass-loss rate, we extracted the number density of our model along the $x$-axis with $z=y=0$ and compared this with the 1D smooth model with an overdensity described in Methods [3.5](#rtmod) and (cite: Brunner2018). In Fig. [21](#fig:nh2)a we show the number densities from the hydrodynamic model along the positive and negative $x$ directions. Because the orbital parameters of our main hydrodynamic model do not precisely match the orbital parameters that we derive in this work, we performed an additional hydrodynamic model using the orbital solution discussed in Methods [3.9](#sec:solution) ($e=0.93, r_p=10$ au). To reduce the required computational resources, we set a large accretion radius for the F9 star (1 au compared with 0.05 au in our main model), which reduces the more complex (and computationally expensive) close gravitational interactions between the companion star and the wind particles. This eliminates the funnel-like structure seen on the right of Fig. [3](#coarcs)c but retains the sphere-like structures resulting from the motions of the two stars. For this model, the same number density plot, Fig. [21](#fig:nh2)b, reveals density peaks at radii in good agreement with the overdensity found by (cite: Brunner2018). Note that, overall, the number density of the hydrodynamic models can be averaged to equal the number density of a smooth 1D model (without any overdensity). However, we also note that our main model, which better allows for the close gravitational interactions between the wind and the F9 star, results in a less symmetric distribution of over- and under-dense regions (as shown for the $x$-axis in Fig. [21](#fig:nh2)a and seen in the funnel-like structure in Fig. [3](#coarcs)c) and contributes to the large-scale asymmetries discussed below.

Based on the circular structures formed during periastron, we can estimate the time of the most recent periastron from the expansion time of the black circle in Fig. [3](#coarcs)a and the orbital period from the difference in expansion times between the black and white circles. These calculations are outlined in Methods [3.8](#orbit-from-alma). The fact that the black circle overlaps with the edge of the SiN emission (Fig. [3](#coarcs)b) also supports our hypothesis that the SiN was created during the most recent periastron passage.

To enable a better comparison of the SPH model to the observations, we processed the Phantom model with the radiative transfer code MCFOST (cite: Pinte2006; Pinte2009), using the effective stellar temperatures of both the AGB (2300 K) and F9 (6000 K) stars and silicate dust from (cite: Weingartner2001). The computation was sped up by only considering the lowest 6 CO levels since this was sufficient for the task at hand. MCFOST includes a routine for determining the photodissociation of CO by the interstellar UV field (cite: Pinte2018), which we used to determine the drop off in CO distribution (set to $6\times 10^{-4}$ relative to $\mathrm{H}_2$ at the centre of the model), based on our 3D structures. This resulted in the near-complete photodissociation of CO in the outermost density structures and left only (parts of) the innermost four circular structures visible in CO. The resultant central velocity channel is plotted in Fig. [3](#coarcs)d, rotated to match the orientation of the W Aql system on the sky. Although the model is not a perfect reproduction of the observed CO emission (expected in light of the missing physics mentioned above), there are many qualitative similarities. We also extracted an angle-radius plot from the central channel of the MCFOST output (Fig. [22](#mcfostangrad)), in which we see similar sinusoidal structures as those found in the observations (Figs. [8](#angrad) and [23](#angrad-no-lines)). The structures outlined by the pink and red circles identified in Fig. [3](#coarcs)a are not apparent in the MCFOST output, although they do qualitatively resemble the structures formed at periastron. The main distinguishing feature is that the pink and red circles are offset in the opposite direction (south rather than north). If we were to ignore the offset and assume that one or both of these circles have the same origin as the black and white circles, we find that the period calculated between all the identified circles would be too short to agree with the HST and SPHERE observations of the stellar separations. Therefore, the red and pink circles cannot have formed during periastron.

Noting that the Phantom model overestimates the wind velocity in the inner regions, we suggest that the difference between the observed and modelled structures partially arises from this as well as the other missing physics mentioned at the start of this section.

We also examined the channel maps generated by MCFOST at high and low velocities and compared these with equivalent channels from the ALMA observations in Fig. [12](#otherCOchans). The observations are taken from channels $\pm 13~\mathrm{km\,s}^{-1}$ from the LSR velocity of $\upsilon_\mathrm{LSR} = -23~\mathrm{km\,s}^{-1}$. The blue channel exhibits CO emission elongated to the southwest, approximately along the companion axis, while the red channel has a more circular CO emitting region. These differences are qualitatively reproduced in their respective MCFOST channels. This asymmetry in velocity space is also responsible for the enhanced blue emission seen in the wings of several line profiles observed towards W Aql (cite: Danilovich2014). The asymmetry arises from the orientation of the orbital plane such that the observations are reproduced if the Phantom model is orientated so that motion of the F9 star at periastron is into the plane of the sky.

Finally, we comment on the large-scale asymmetry to the southwest, revealed by past observations, in the CO (cite: Ramstedt2017) and dust (cite: Ramstedt2011; Mayer2013) emission on scales of $10^{\prime\prime}$ and $60^{\prime\prime}$. Although this more extended emission is in the same direction as the F9 star, the emission extent is much larger than the current or maximal separation between AGB and F9 stars ($\sim0.5$ to $0.8^{\prime\prime}$, Fig. [4](#orb-phot)). The luminosity of the F9 star is insufficient for its radiation to drive the dust outwards, as the AGB star does (Supplementary Materials [5.1](#dustdrive)); instead, it contributes to the large-scale shaping of the wind through its gravitational pull. We do not detect any accretion disc around the F9 star, either in the ALMA continuum or in any molecular lines, and an accretion disc is not predicted for the W Aql system by the SPH model. However, the F9 star does gravitationally attract some circumstellar material, which is then pushed outwards by the radiation pressure from the AGB star, and results in the large scale asymmetry seen in the dust and more extended gas (cite: Ramstedt2011; Mayer2013; Ramstedt2017), and reproduced in our hydrodynamic model. The enhanced emission in this direction can be seen in the full extent of the central CO channel output by MCFOST (Fig. [24](#faceonSPH)c), where the CO extends out farther to the southwest.

## Orbital parameters from ALMA observations

Here we constrain some orbital parameters from the ALMA observations. First we make an estimate of the period based on the round structures seen in the CO observations. As determined in Methods [3.7](#hydro), the black and white circles shown in Fig. [3](#coarcs) were created during periastron interactions between the AGB and F9 stars. Assuming the velocity profile from Eq. [\[betalaw\]](#betalaw), we find the expansion time between the two circles, and hence the orbital period, through the integral: $$\begin{equation}
\label{exptime}
T = \int_{R_\mathrm{black}}^{R_\mathrm{white}} \frac{dr}{\upsilon(r)} = \int_{R_\mathrm{black}}^{R_\mathrm{white}} \frac{dr}{\upsilon_0 + (\upsilon_\infty - \upsilon_0) \left(1 - \frac{R_\mathrm{in}}{r}\right)^\beta} 
\end{equation}$$ where $R_\mathrm{black}$ and $R_\mathrm{white}$ are the radii of the black and white circles, and $R_\mathrm{in} = 2\times 10^{14}$ cm is the dust condensation radius, with $\upsilon_0 = 3~\mathrm{km\,s}^{-1}$ the velocity for $r<R_\mathrm{in}$, taken to be the sound speed (cite: Danilovich2014). The period is found to be $1082^{+89}_{-108}$ years. The uncertainty is based on the width of the circles as fit from the angle-radius plot (Fig. [8](#angrad)). There we found the uncertainties in the radii of the circles to be $10.75\pm0.75^{\prime\prime}$ for the white circle and $1.35\pm0.10^{\prime\prime}$ for the black circle.

Another crucial parameter needed to constrain the orbital solution of the W Aql system is the time since periastron. As previously discussed, the most recent periastron passage generated the black circle seen in CO (Fig. [3](#coarcs)) and the arc of SiN (Fig. [1](#sin)). We can estimate the time of periastron by calculating the expansion time of these two structures. Since we are now considering expansion in the inner part of the envelope, we need to also consider the velocity inside the dust condensation radius, which we assume to be close to the sound speed at $\upsilon=3~\mathrm{km\,s}^{-1}$. Equation [\[exptime\]](#exptime) can then be rewritten: $$\begin{equation}
\label{timesinceperi}
\Delta t  = \int_{R_\mathrm{in}}^{R_\mathrm{black}} \frac{dr}{\upsilon_0 + (\upsilon_\infty - \upsilon_0) \left(1 - \frac{R_\mathrm{in}}{r}\right)^\beta} + \int_{R_\mathrm{form}}^{R_\mathrm{in}} \frac{dr}{\upsilon_0} 
\end{equation}$$ where $R_\mathrm{black}$ is the radius of the black circle and the radial extent of the SiN arc, and $R_\mathrm{form}$ is the radial distance at which these two structures formed.

The value of $R_\mathrm{form}$ is uncertain so we take it to be the periastron distance between stars. The smallest periastron distance we obtain is $\sim3$ au, while the largest is equal to the dust condensation radius. Using these values as a guide and assuming a constant velocity of $\upsilon_0 = 3~\mathrm{km\,s}^{-1}$ for $r<R_{in}=2\times 10^{14}$ cm, we estimate the time since the most recent periastron as $172\pm22$ years ago.

These derived values are listed with other orbital parameters in Table [2](#tab:parameters).

Finally, we can determine the direction of the orbit from the PV diagrams of the species formed at periastron, namely SiN, SiC, and NS. Taking into account that 1) the redder emission is brighter for all three of these molecules (and indeed only red emission is seen above the noise in the NS PV diagram, Fig. [14](#nsplot)) and 2) the line profiles of SiN and SiC are slightly blue-shifted relative to the stellar LSR velocity, suggests that these species formed first on the blue side of the envelope and then more recently on the red side. Hence, there has been slightly more time for the blue emission to expand, shifting the line profiles and PV diagrams bluewards. From this we conclude that the direction of the periastron passage was, for the F9 star, into the plane of the sky. This agrees with the evidence from the SPH model discussed above.

## Orbital solutions

The orbit of the W Aql system cannot be solved analytically, so instead we solve it numerically by calculating a series of possible orbits and checking which agree with the parameters derived from observations (i.e. the parameters listed in Table [2](#tab:parameters)). We adjust our basic orbital solution by leaving as free parameters the eccentricity, $e$, and the periastron distance, $r_p$. All other primary orbital parameters are either input from prior results or calculated from $e$ and $r_p$ as follows.

The apastron, $r_a$, is defined by $$\begin{equation}
r_a = r_p\left(\frac{e+1}{1-e}\right)
\end{equation}$$ and the semimajor axis, $a$, is then $$\begin{equation}
a = \frac{r_p+r_a}{2}\,.
\end{equation}$$ Working in the reference frame of the AGB star, we define the focus of the ellipse traced by the F9 star as the location of the AGB star, defined here as (0,0,0) in our cartesian co-ordinate scheme.

From the system mass ($M+m = 2.66~\mathrm{M}_\odot$) and the semimajor axis, we can then calculate the orbital period, $T$ $$\begin{equation}
T = 2\pi \sqrt{\left(\frac{a^3}{G(M+m)}\right)} \,.
\end{equation}$$

This is enough information to plot a top-down view of the orbit, as shown in Fig. [25](#schematic). However, we know from observations that the orbit is inclined and rotated in the plane of the sky (relative to north). From the observations of SiN, we estimate the inclination angle of the orbit to be close to edge-on, $i=90\pm7^\circ$. We plot $i=85^\circ$ to better illustrate the orbit in the plane of the sky, but note that a completely edge-on system ($i=90^\circ$) satisfies the observations and does not significantly change our results. From the photometry of the two stars, we rotate the orbit in the plane of the sky by $\omega=120^\circ$ to fit the SPHERE observation (Fig. [4](#orb-phot)). We note that the uncertainty in $\omega$ comes mainly from the precise values of the inclination and eccentricity, but the selection of $\omega=120^\circ$ is a good fit given the rest of our results. The sky projection of a selected orbit and the locations of the stars are plotted in Fig. [4](#orb-phot). We assume no rotation out of the plane of the sky along the third orthogonal axis because the relative symmetry of the SiN PV-diagram (Fig. [1](#sin)b) suggests this value is small ($<5^\circ$).

For a possible orbital solution, we must calculate the time since periastron and the time between the SPHERE and HST observations. For this we must consider the angle $\theta$ made between the periastron, the AGB star and the F9 star, as well as the eccentric anomaly, $E$. Both of these angles are shown in Fig. [25](#schematic) and are mathematically related by $$\begin{eqnarray}
\tan{\left(\frac{\theta}{2}\right)} &=& \tan{\left(\frac{E}{2}\right)}\sqrt{\frac{1+e}{1-e}}\label{eqn:theta-E}\\
E &=& 2\tan^{-1}\left(\tan\left(\frac{\theta}{2}\right) \sqrt{\frac{1-e}{1+e}}\right) \quad .\label{eqn:E}
\end{eqnarray}$$ The time since periastron, $\Delta t$, can then be calculated $$\begin{equation}
\Delta t = \frac{T}{2\pi} \left(E- e\sin(E)\right).\label{eqn:deltat}
\end{equation}$$ We also check the possible solution against the known time between the HST and SPHERE observations by comparing $\Delta t_\mathrm{SPHERE} - \Delta t_\mathrm{HST}$ against the time difference between those observations.

To find the best solutions, we modify the input parameters ($r_p$ and $e$) until we find a suitable orbit which agrees with the values we found for the period, time since periastron and time between HST and SPHERE observations. Because of the uncertainties, we find a group of compatible solutions rather than one single definition of the orbit. From a grid with steps of $\Delta e = 0.01 \in [0.70, 0.99]$ and $\Delta r_p = 0.1\times 10^{14}~\mathrm{cm} \in [0.4\times 10^{14}~\mathrm{cm}, 5\times 10^{14}~\mathrm{cm}]$, we found a set of compatible solutions, all of which are given in Table [3](#tab:solutions). For the highest eccentricities $e>0.95$ we additionally tested a finer grid for $r_p$, with $\Delta r_p = 0.5\times 10^{13}~\mathrm{cm} \in [5\times 10^{13}~\mathrm{cm}, 1\times 10^{14}~\mathrm{cm}]$, because the orbital timing becomes sensitive to small variations in $r_p$ at these high eccentricities. The compatible solutions range from the extremes of $e=0.98,\,r_p = 4.5\times 10^{13}$ cm to $e=0.91,\,r_p = 2.0\times 10^{14}$ cm. We plot one of these solutions ($e=0.93,\,r_p = 1.5\times 10^{14}$ cm) in Fig. [4](#orb-phot), where we also show the orbit superposed on the HST and SPHERE photometric observations. Note that although some of our solutions have very small periastron distances, none are smaller than the Roche limit, so direct accretion of the AGB star onto the F9 star is not expected.

In Table [3](#tab:solutions), we also include $t_\mathrm{close}$ which we define as the time the AGB and F9 stars spend “close” to each other. More precisely, in the AGB frame, this is the time the F9 star takes to pass through the $-90^\circ\leq \theta \leq 90^\circ$ region of the orbit (see Fig. [25](#schematic)) and can be derived from equations [\[eqn:E\]](#eqn:E) and [\[eqn:deltat\]](#eqn:deltat). As noted in Table [3](#tab:solutions), $t_\mathrm{close}$ ranges from 2 years at the highest eccentricity to 18 years at $e=0.91$. This corresponds to $\sim 0.1$ to $2\%$ of the total orbital period.

# Data Availability

The observational data used here is openly available through the data archives for ALMA (<https://almascience.nrao.edu/aq/>), ESO for the APEX and SPHERE data (<http://archive.eso.org>), and HST (<https://hla.stsci.edu>). Custom ALMA data products are available from TD or AMSR upon reasonable request.

# Code Availability

Phantom is open source under the GPLv3 license and can be downloaded via <https://github.com/danieljprice/phantom>. MCFOST is open source under the GPLv3 license and can be downloaded via <https://mcfost.readthedocs.io/en/latest/overview.html>. ALI, the 1D radiative transfer code, is available from TD upon reasonable request.

100 url urlprefix

(ref: Hofner2018) Höfner, S. & Olofsson, H. . *The Astronomy and Astrophysics Review* **26**, 1 (2018).

(ref: Kobayashi2020) Kobayashi, C., Karakas, A. I. & Lugaro, M. . *The Astrophysical Journal* **900**, 179 (2020). `2008.04660`.

(ref: Decin2019) Decin, L. *et al.* . *Nature Astronomy* 213 (2019). `1902.09259`.

(ref: Van-de-Sande2022) Van de Sande, M. & Millar, T. J. . *MNRAS* **510**, 1204–1222 (2022). `2111.05053`.

(ref: De-Marco2022) De Marco, O. *et al.* The messy death of a multiple star system and the resulting planetary nebula as observed by jwst. *Nature Astronomy* **6**, 1421–1432 (2022). URL `https://doi.org/10.1038/s41550-022-01845-2`.

(ref: Decin2020) Decin, L. *et al.* (sub)stellar companions shape the winds of evolved stars. *Science* **369**, 1497–1500 (2020). URL `https://science.sciencemag.org/content/369/6510/1497`. `https://science.sciencemag.org/content/369/6510/1497.full.pdf`.

(ref: Jorissen2004) Jorissen, A. . In *Asymptotic Giant Branch Stars*, 461–518 (Springer, 2004).

(ref: Karovska1997) Karovska, M., Hack, W., Raymond, J. & Guinan, E. . *The Astrophysical Journal Letters* **482**, L175–L178 (1997).

(ref: Ramstedt2014a) Ramstedt, S. *et al.* . *Astronomy & Astrophysics* **570**, L14 (2014). `1410.1529`.

(ref: Kervella2016) Kervella, P. *et al.* . *Astronomy & Astrophysics* **596**, A92 (2016). `1611.06231`.

(ref: Homan2020) Homan, W. *et al.* . *Astronomy & Astrophysics* **644**, A61 (2020). `2010.05509`.

(ref: Mauron2006) Mauron, N. & Huggins, P. J. . *Astronomy & Astrophysics* **452**, 257–268 (2006). `astro-ph/0602623`.

(ref: Kim2017) Kim, H. *et al.* . *Nature Astronomy* **1**, 0060 (2017). `1704.00449`.

(ref: Maercker2012) Maercker, M. *et al.* . *Nature* **490**, 232–234 (2012). `1210.3030`.

(ref: Sahai2022) Sahai, R. *et al.* . *The Astrophysical Journal* **929**, 59 (2022). `2202.09335`.

(ref: Ramos-Larios2016) Ramos-Larios, G. *et al.* . *MNRAS* **462**, 610–635 (2016).

(ref: Herbig1965) Herbig, G. H. . *Veroeffentlichungen der Remeis-Sternwarte zu Bamberg* **27**, 164 (1965).

(ref: Danilovich2015) Danilovich, T., Olofsson, G., Black, J. H., Justtanont, K. & Olofsson, H. . *Astronomy & Astrophysics* **574**, A23 (2015). `1501.00863`.

(ref: Ramstedt2011) Ramstedt, S., Maercker, M., Olofsson, G., Olofsson, H. & Schöier, F. L. . *Astronomy & Astrophysics* **531**, A148 (2011). `1105.5405`.

(ref: Mayer2013) Mayer, A. *et al.* . *Astronomy & Astrophysics* **549**, A69 (2013). `1211.3595`.

(ref: Danilovich2014) Danilovich, T. *et al.* . *Astronomy & Astrophysics* **569**, A76 (2014).

(ref: Ramstedt2017) Ramstedt, S. *et al.* . *Astronomy & Astrophysics* **605**, A126 (2017). `1709.07327`.

(ref: Brunner2018) Brunner, M. *et al.* . *Astronomy & Astrophysics* **617**, A23 (2018). `1806.01622`.

(ref: Danilovich2021) Danilovich, T. *et al.* . *Astronomy & Astrophysics* **655**, A80 (2021). `2109.04747`.

(ref: Richichi2005) Richichi, A., Percheron, I. & Khristoforova, M. . *Astronomy & Astrophysics* **431**, 773–777 (2005).

(ref: Turner1992) Turner, B. E. . *The Astrophysical Journal Letters* **388**, L35 (1992).

(ref: Huggins1984) Huggins, P. J., Glassgold, A. E. & Morris, M. *The Astrophysical Journal* **279**, 284–290 (1984).

(ref: Montarges2023) Montargès, M. *et al.* . *Astronomy & Astrophysics* **671**, A96 (2023). `2301.02081`.

(ref: Tokovinin2016) Tokovinin, A. & Kiyaeva, O. . *MNRAS* **456**, 2070–2079 (2016). `1512.00278`.

(ref: Boffin1993) Boffin, H. M. J., Cerf, N. & Paulus, G. *Astronomy & Astrophysics* **271**, 125–138 (1993).

(ref: Moe2017) Moe, M. & Di Stefano, R. . *Astrophysical Journal Supplement Series* **230**, 15 (2017). `1606.05347`.

(ref: Maercker2016a) Maercker, M. *et al.* . *Astronomy & Astrophysics* **586**, A5 (2016). `1512.01350`.

(ref: Lykou2018) Lykou, F. *et al.* . *MNRAS* **480**, 1006–1021 (2018). `1808.00279`.

(ref: Doan2017) Doan, L. *et al.* . *Astronomy & Astrophysics* **605**, A28 (2017). `1709.09435`.

(ref: Sahai2016) Sahai, R., Scibelli, S. & Morris, M. R. . *The Astrophysical Journal* **827**, 92 (2016). `1605.06728`.

(ref: Oomen2018) Oomen, G.-M. *et al.* . *Astronomy & Astrophysics* **620**, A85 (2018). `1810.01842`.

(ref: Jorissen1998) Jorissen, A., Van Eck, S., Mayor, M. & Udry, S. . *Astronomy & Astrophysics* **332**, 877–903 (1998). `astro-ph/9801272`.

(ref: Ramstedt2009) Ramstedt, S., Schöier, F. L. & Olofsson, H. . *Astronomy & Astrophysics* **499**, 515–527 (2009). `0903.1672`.

(ref: Knapp1985) Knapp, G. R. & Morris, M. . *The Astrophysical Journal* **292**, 640–669 (1985).

(ref: Jura1988) Jura, M. . *Astrophysical Journal Supplement Series* **66**, 33 (1988).

(ref: Groenewegen1998) Groenewegen, M. & De Jong, T. Co observations and mass loss of ms- and s-stars. *Astronomy & Astrophysics* **337**, 797–807 (1998). URL `http://www.scopus.com/inward/record.url?eid=2-s2.0-0001632031&partnerID=40&md5=083cdfb2ae34c4d507fffc05fd912f9b`.

(ref: Gaia-2016) Gaia Collaboration *et al.* . *Astronomy & Astrophysics* **595**, A1 (2016). `1609.04153`.

(ref: Andriantsaralaza2022) Andriantsaralaza, M., Ramstedt, S., Vlemmings, W. H. T. & De Beck, E. . *Astronomy & Astrophysics* **667**, A74 (2022). `2209.03906`.

(ref: Gaia-EDR3) Gaia Collaboration *et al.* . *Astronomy & Astrophysics* **649**, A1 (2021). `2012.01533`.

(ref: Habets1981) Habets, G. M. H. J. & Heintze, J. R. W. . *Astronomy & Astrophysics Supplement Series* **46**, 193–237 (1981).

(ref: De-Nutte2017) De Nutte, R. *et al.* . *Astronomy & Astrophysics* **600**, A71 (2017). `1606.07445`.

(ref: De-Beck2020) De Beck, E. & Olofsson, H. . *Astronomy & Astrophysics* **642**, A20 (2020). `2007.01756`.

(ref: Vassiliadis1993) Vassiliadis, E. & Wood, P. R. . *The Astrophysical Journal* **413**, 641–657 (1993).

(ref: Maire2021) Maire, A. L. *et al.* . *The Messenger* **183**, 7–12 (2021). `2103.13700`.

(ref: Gottlieb2022) Gottlieb, C. A. *et al.* . *Astronomy & Astrophysics* **660**, A94 (2022). `2112.04399`.

(ref: CASA2022) The CASA Team *et al.* . *arXiv e-prints* arXiv:2210.02276 (2022). `2210.02276`.

(ref: TMS) Thompson, A. R., Moran, J. M. & Swenson, J., George W. *Interferometry and Synthesis in Radio Astronomy, 3rd Edition* (Springer, Berlin Heidelberg, 2017).

(ref: Winnewisser1997) Winnewisser, G., Belov, S. P., Klaus, T. & Schieder, R. . *Journal of Molecular Spectroscopy* **184**, 468–472 (1997).

(ref: Cernicharo1989) Cernicharo, J., Gottlieb, C. A., Guelin, M., Thaddeus, P. & Vrtilek, J. M. . *The Astrophysical Journal Letters* **341**, L25 (1989).

(ref: Bogey1990) Bogey, M., Demuynck, C. & Destombes, J. L. . *Astronomy & Astrophysics* **232**, L19 (1990).

(ref: Lee1995) Lee, S. K., Ozeki, H. & Saito, S. . *Astrophysical Journal Supplement Series* **98**, 351 (1995).

(ref: Yamada1995) Yamada, K. M. T., Moravec, A. & Winnewisser, G. . *Zeitschrift Naturforschung Teil A* **50**, 1179–1181 (1995).

(ref: Muller2013) Müller, H. S. P. *et al.* . *Journal of Physical Chemistry A* **117**, 13843–13854 (2013).

(ref: Muller2007) Müller, H. S. P. *et al.* . *Physical Chemistry Chemical Physics* **9**, 1579 (2007).

(ref: Gottlieb2003) Gottlieb, C. A., Myers, P. C. & Thaddeus, P. . *The Astrophysical Journal* **588**, 655–661 (2003).

(ref: Ahrens2002) Ahrens, V. *et al.* . *Zeitschrift Naturforschung Teil A* **57**, 669–681 (2002).

(ref: Fuchs2004) Fuchs, U. *et al.* . *Zeitschrift Naturforschung Teil A* **59**, 861–872 (2004).

(ref: Bogey1984) Bogey, M., Demuynck, C. & Destombes, J. L. *Canadian Journal of Physics* **62**, 1248–1253 (1984).

(ref: Muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A. & Winnewisser, G. . *Astronomy & Astrophysics* **370**, L49–L52 (2001).

(ref: Muller2005) Müller, H. S. P., Schlöder, F., Stutzki, J. & Winnewisser, G. . *J Mol. Struct.* **742**, 215–227 (2005).

(ref: Olofsson1993) Olofsson, H., Eriksson, K., Gustafsson, B. & Carlstrom, U. *Astrophysical Journal Supplement Series* **87**, 267–304 (1993).

(ref: Homan2021) Homan, W. *et al.* . *Astronomy & Astrophysics* **651**, A82 (2021).

(ref: Vlemmings2019) Vlemmings, W. H. T., Khouri, T. & Olofsson, H. . *Astronomy & Astrophysics* **626**, A81 (2019). `1904.06374`.

(ref: Baudry2023) Baudry, A. *et al.* . *Astronomy & Astrophysics* **674**, A125 (2023). `2305.03171`.

(ref: Massalkhi2018) Massalkhi, S. *et al.* . *Astronomy & Astrophysics* **611**, A29 (2018). `1710.11409`.

(ref: Cernicharo2015a) Cernicharo, J., Marcelino, N., Agúndez, M. & Guélin, M. . *Astronomy & Astrophysics* **575**, A91 (2015). `1412.1948`.

(ref: Decin2015) Decin, L. *et al.* . *Astronomy & Astrophysics* **574**, A5 (2015). `1410.2060`.

(ref: Siebert2022) Siebert, M. A., Van de Sande, M., Millar, T. J. & Remijan, A. J. . *The Astrophysical Journal* **941**, 90 (2022). `2210.14941`.

(ref: Patel2013) Patel, N., Gottlieb, C. & Young, K. . In *Proceedings of The Life Cycle of Dust in the Universe: Observations*, 98 (2013).

(ref: Velilla-Prieto2019a) Velilla-Prieto, L. *et al.* . *IAU Symposium* **343**, 535–537 (2019).

(ref: Velilla-Prieto2017) Velilla Prieto, L. *et al.* . *Astronomy & Astrophysics* **597**, A25 (2017). `1609.01904`.

(ref: Decin2018) Decin, L., Richards, A. M. S., Danilovich, T., Homan, W. & Nuth, J. A. . *Astronomy & Astrophysics* **615**, A28 (2018). `1801.09291`.

(ref: Decin2011) Decin, L. *et al.* . *Astronomy & Astrophysics* **534**, A1 (2011). `1210.3483`.

(ref: Guelin2018) Guélin, M. *et al.* . *Astronomy & Astrophysics* **610**, A4 (2018). `1709.04738`.

(ref: Schoier2013) Schöier, F. L. *et al.* . *Astronomy & Astrophysics* **550**, A78 (2013). `1301.2129`.

(ref: Danilovich2018) Danilovich, T. *et al.* . *Astronomy & Astrophysics* **617**, A132 (2018). `1807.05144`.

(ref: Massalkhi2019) Massalkhi, S., Agúndez, M. & Cernicharo, J. . *Astronomy & Astrophysics* **628**, A62 (2019). `1906.09461`.

(ref: Morris1983) Morris, M. & Jura, M. *The Astrophysical Journal* **264**, 546–553 (1983).

(ref: Bachiller1997) Bachiller, R. *et al.* *Astronomy & Astrophysics* **319**, 235–243 (1997).

(ref: Rybicki1991) Rybicki, G. B. & Hummer, D. G. . *Astronomy & Astrophysics* **245**, 171–181 (1991).

(ref: Pickett1991) Pickett, H. M. . *Journal of Molecular Spectroscopy* **148**, 371–377 (1991).

(ref: Lique2010) Lique, F. *et al.* . *Journal of Chemical Physics* **132**, 024303 (2010).

(ref: Montez2017) Montez, J., Rodolfo, Ramstedt, S., Kastner, J. H., Vlemmings, W. & Sanchez, E. . *The Astrophysical Journal* **841**, 33 (2017). `1705.05371`.

(ref: Schrijver1987) Schrijver, C. J. *Astronomy & Astrophysics* **172**, 111–123 (1987).

(ref: Galvez2002) Gálvez, M. C. *et al.* . *Astronomy & Astrophysics* **389**, 524–536 (2002). `astro-ph/0204490`.

(ref: Gray2009) Gray, R., Corbally, C. & Burgasser, A. *Stellar Spectral Classification*. Princeton Series in Astrophysics (Princeton University Press, 2009). URL `http://books.google.com.au/books?id=S_Sh1i226wwC`.

(ref: Asplund2021) Asplund, M., Amarsi, A. M. & Grevesse, N. . *Astronomy & Astrophysics* **653**, A141 (2021). `2105.01661`.

(ref: Agundez2020) Agúndez, M., Martı́nez, J. I., de Andres, P. L., Cernicharo, J. & Martı́n-Gago, J. A. . *Astronomy & Astrophysics* **637**, A59 (2020). `2004.00519`.

(ref: Agundez2017) Agúndez, M. *et al.* . *Astronomy & Astrophysics* **601**, A4 (2017). `1702.04429`.

(ref: Cordiner2009) Cordiner, M. A. & Millar, T. J. . *The Astrophysical Journal* **697**, 68–78 (2009). `0903.0890`.

(ref: Kerkines2005) Kerkines, I. S. K. & Mavridis, A. . *Journal of Chemical Physics* **123**, 124301–124301 (2005).

(ref: Thomson1968) Thomson, R. & Dalby, F. W. . *Canadian Journal of Physics* **46**, 2815 (1968).

(ref: Monaghan2005) Monaghan, J. J. . *Reports on Progress in Physics* **68**, 1703–1759 (2005).

(ref: Price2012) Price, D. J. . *Journal of Computational Physics* **231**, 759–794 (2012). `1012.1885`.

(ref: Price2018) Price, D. J. *et al.* . *Publications of the Astronomical Society of Australia* **35**, e031 (2018). `1702.03930`.

(ref: Siess2022) Siess, L., Homan, W., Toupin, S. & Price, D. J. . *Astronomy & Astrophysics* **667**, A75 (2022). `2208.13869`.

(ref: Maes2021) Maes, S. *et al.* . *Astronomy & Astrophysics* **653**, A25 (2021). `2107.00505`.

(ref: Malfait2021) Malfait, J. *et al.* . *Astronomy & Astrophysics* **652**, A51 (2021). `2107.01074`.

(ref: Mastrodemos1998) Mastrodemos, N. & Morris, M. . *The Astrophysical Journal* **497**, 303–329 (1998).

(ref: Mastrodemos1999) Mastrodemos, N. & Morris, M. . *The Astrophysical Journal* **523**, 357–380 (1999).

(ref: Kim2019) Kim, H., Liu, S.-Y. & Taam, R. E. . *Astrophysical Journal Supplement Series* **243**, 35 (2019). `1906.06333`.

(ref: Pinte2006) Pinte, C., Ménard, F., Duchêne, G. & Bastien, P. . *Astronomy & Astrophysics* **459**, 797–804 (2006). `astro-ph/0606550`.

(ref: Pinte2009) Pinte, C. *et al.* . *Astronomy & Astrophysics* **498**, 967–980 (2009). `0903.1231`.

(ref: Weingartner2001) Weingartner, J. C. & Draine, B. T. . *The Astrophysical Journal* **548**, 296–309 (2001). `astro-ph/0008146`.

(ref: Pinte2018) Pinte, C. *et al.* . *Astronomy & Astrophysics* **609**, A47 (2018). `1710.06450`.

(ref: Tielens1983) Tielens, A. G. G. M. . *The Astrophysical Journal* **271**, 702–716 (1983).

(ref: Ohnaka2016) Ohnaka, K., Weigelt, G. & Hofmann, K. H. . *Astronomy & Astrophysics* **589**, A91 (2016). `1603.01197`.

(ref: Khouri2016) Khouri, T. *et al.* . *Astronomy & Astrophysics* **591**, A70 (2016). `1605.05504`.

(ref: Wittkowski2017) Wittkowski, M. *et al.* . *Astronomy & Astrophysics* **601**, A3 (2017). `1702.02574`.

(ref: Paladini2018) Paladini, C. *et al.* . *Nature* **553**, 310–312 (2018).

(ref: Khouri2020) Khouri, T. *et al.* . *Astronomy & Astrophysics* **635**, A200 (2020). `2003.06195`.

(ref: Freytag2008) Freytag, B. & Höfner, S. . *Astronomy & Astrophysics* **483**, 571–583 (2008).

(ref: Freytag2017) Freytag, B., Liljegren, S. & Höfner, S. . *Astronomy & Astrophysics* **600**, A137 (2017). `1702.05433`.

(ref: Freytag2023) Freytag, B. & Höfner, S. . *Astronomy & Astrophysics* **669**, A155 (2023). `2301.11836`.

(ref: Vlemmings2017) Vlemmings, W. *et al.* The shock-heated atmosphere of an asymptotic giant branch star resolved by alma. *Nature Astronomy* **1**, 848–853 (2017). URL `https://doi.org/10.1038/s41550-017-0288-9`.

(ref: Takigawa2017) Takigawa, A., Kamizuka, T., Tachibana, S. & Yamamura, I. . *Science Advances* **3** (2017).

(ref: Khouri2019) Khouri, T. *et al.* . *Astronomy & Astrophysics* **623**, L1 (2019). `1902.11033`.

(ref: Velilla-Prieto2023) Velilla-Prieto, L. *et al.* Atmospheric molecular blobs shape up circumstellar envelopes of agb stars. *Nature* (2023). URL `https://doi.org/10.1038/s41586-023-05917-9`.

(ref: Martin1998) Martin, W. C., deL. Musgrove, A. R., Kotochigova, S. & Sansonetti, J. E. Ground levels and ionization energies for the neutral atoms (1998). URL `https://api.semanticscholar.org/CorpusID:103628738`.

(ref: Aydi2022) Aydi, E. & Mohamed, S. . *MNRAS* **513**, 4405–4430 (2022). `2203.08318`.

# 

Correspondence and requests for materials should be addressed to Taïssa Danilovich.

# Acknowledgements

We would like to thank Se-Hyung Cho of the Korean VLBI Network for KVN observations of W Aql to confirm consistency with our ALMA results. TD is supported in part by the Australian Research Council through a Discovery Early Career Researcher Award (DE230100183). TD, FDC and SHJW acknowledge support from the Research Foundation Flanders (FWO) through grants 12N9920N, 1253223N and 1285221N, respectively. JM and SM acknowledge support from the Research Foundation Flanders (FWO) grant G099720N. MVdS acknowledges support from European Union’s Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No 882991. MM acknowledges funding form the Programme Paris Region fellowship supported by the Région Ile-de-France. PK acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program (synergy grant project UniverScale, grant agreement 951549). TJM is grateful to the STFC for support through grant ST/P000312/1 and thanks the Leverhulme Trust for the award of an Emeritus Fellowship. JMCP was supported by STFC grant number ST/T000287/1. LD, JMCP, SHJW, SM and DG acknowledge support from ERC consolidator grant 646758 AEROSOL. EDB acknowledges support from the Swedish National Space Agency. DG was funded by the project grant ‘The Origin and Fate of Dust in Our Universe’ from the Knut and Alice Wallenberg Foundation. KTW acknowledges support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (Grant agreement no. 883867, project EXWINGS). FH, AB and LM acknowledge funding from the French National Research Agency (ANR) project PEPPER (ANR-20-CE31- 0002). HSPM acknowledges support by the Deutsche Forschungsgemeinschaft through the collaborative research grant SFB 956 (project ID 184018867). RS’s contribution to the research described here was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA, and funded in part by NASA via ADAP awards, and multiple HST GO awards from the Space Telescope Science Institute. AZ is funded by STFC/UKRI through grant ST/T000414/1. This research was supported in part by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. This project has received funding from the Framework Program for Research and Innovation “Horizon 2020" under the convention Marie Skłodowska-Curie No 945298. Computational resources and services used in this work were provided by the VSC (Flemish Supercomputer Center), funded by the Research Foundation Flanders (FWO) and the Flemish Government – department EWI. This research was undertaken with the assistance of resources and services from the National Computational Infrastructure (NCI), which is supported by the Australian Government. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00659.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programme 0103.D-0772(A). We acknowledge excellent support from the UK ALMA Regional Centre (UK ARC), which is hosted by the Jodrell Bank Centre for Astrophysics (JBCA) at the University of Manchester. The UK ARC Node is supported by STFC Grant ST/P000827/1.

# Author contributions

TD conceived of and led this publication, analysed and interpreted data, performed the radiative transfer models, wrote the manuscript, and created most of the figures. JM performed and interpreted the hydrodynamics model and made figures [3](#coarcs)c, [\[fig:peri\]](#fig:peri), and [24](#faceonSPH)a&b. MVdS led the chemical interpretation and made figures [19](#fig:chemsin) and [20](#fig:chemnsi). MM and PK contributed the analysis of the resolved imagining. AMSR performed the ALMA data reduction. FDC and AC contributed to the 3D interpretation of the data. TJM and JMCP contributed to the chemical interpretation. CAG contributed to the line identifications and interpretation. CP assisted in the MCFOST modelling. DJP assisted in the Phantom modelling and interpretation. EDB contributed the fully-reduced APEX data. The ALMA proposal was led by LD and CAG, with contributions from MM, TD, AdK, KMM, RS, AMSR, JMCP, HSPM, EDB, PK, AB, KTW, MVdS, EL, DG, JY and DJP. All authors commented on the manuscript and analysis.

# Extended Data

![](W_Aql_SiC_mom0_paper.pdf)

![](W_Aql_SiC_PV_parabola_ellipse.pdf)

![image](W_Aql_SiO_paper.pdf) ![image](W_Aql_SiS_paper.pdf) ![image](W_Aql_CS_paper.pdf) ![image](W_Aql_HCN_paper.pdf)

![](W_Aql_CO_channels_beambox.pdf)

![image](W_Aql_ang-rad_zoom15_4pi_curves.pdf) ![image](W_Aql_ang-rad_zoom5_4pi_curves.pdf)

![image](F9vsAGBvsOppositeF9_CS.pdf) ![image](F9vsAGBvsOppositeF9_HCN.pdf) ![image](F9vsAGBvsOppositeF9_SiO5-4.pdf) ![image](F9vsAGBvsOppositeF9_H13CN.pdf)

![](SiN_sketch)

![image](SiN_mom0_apertures_paper.pdf) ![image](best_SiN_distribution_paper.pdf)

![image](W_Aql_CO_combined_chan_vel_-35p9.pdf) ![image](W_Aql_CO_combined_chan_vel_-10p5.pdf) ![image](W_Aql_Phantom-MCFOST_chan14.pdf) ![image](W_Aql_Phantom-MCFOST_chan-14.pdf)

+:------------------------------------------------+------------------------------------------------------:+
| *AGB and circumstellar parameters*                                                                      |
+-------------------------------------------------+-------------------------------------------------------+
| LSR velocity, $\upsilon_\mathrm{LSR}$           | $-23~\mathrm{km\,s}^{-1}$                             |
+-------------------------------------------------+-------------------------------------------------------+
| Mass-loss rate, $\dot{M}$                       | $3\times 10^{-6}\;\mathrm{M}_\odot~\mathrm{ yr}^{-1}$ |
+-------------------------------------------------+-------------------------------------------------------+
| Stellar effective temperature, $T_\mathrm{eff}$ | 2300 K                                                |
+-------------------------------------------------+-------------------------------------------------------+
| Luminosity, $L_\star$                           | $7500~L_\odot$                                        |
+-------------------------------------------------+-------------------------------------------------------+
| Stellar radius, $R_\star$                       | 8.3 mas                                               |
+-------------------------------------------------+-------------------------------------------------------+
| *System parameters*                                                                                     |
+-------------------------------------------------+-------------------------------------------------------+
| Distance, $D$                                   | 395 pc                                                |
+-------------------------------------------------+-------------------------------------------------------+
| AGB mass, $M_\mathrm{AGB}$                      | $1.6~\mathrm{M}_\odot$                                |
+-------------------------------------------------+-------------------------------------------------------+
| F9 mass, $M_\mathrm{F9}$                        | $1.06~\mathrm{M}_\odot$                               |
+-------------------------------------------------+-------------------------------------------------------+
| *Orbital parameters from ALMA observations*                                                             |
+-------------------------------------------------+-------------------------------------------------------+
| Orbital period, $T$                             | $1082^{+89}_{-108}$ years                             |
+-------------------------------------------------+-------------------------------------------------------+
| Time since periastron, $\Delta t$               | $172\pm22$ years                                      |
+-------------------------------------------------+-------------------------------------------------------+
| Rotation in the plane of the sky, $\omega$      | $120\pm5^\circ$                                       |
+-------------------------------------------------+-------------------------------------------------------+
| Inclination, $i$                                | $90\pm7^\circ$                                        |
+-------------------------------------------------+-------------------------------------------------------+

: Physical parameters of the W Aql system

| $e$ | $r_p$ \[cm\] | $r_p$ \[au\] | $a$ \[au\] | $T$ \[years\] | $\Delta t$ \[years\] | $t_\mathrm{close}$ \[years\] |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 0.98 | $4.5\times 10^{13}$ | 3.0 | 150 | 1131 | 157 | 1.9 |
| 0.97 | $6.5\times 10^{13}$ | 4.3 | 145 | 1069 | 163 | 3.3 |
| 0.96 | $8.5\times 10^{13}$ | 5.7 | 142 | 1038 | 167 | 5.0 |
| 0.96 | $9.0\times 10^{13}$ | 6.0 | 150 | 1131 | 165 | 5.4 |
| 0.95 | $1.1\times 10^{14}$ | 7.4 | 147 | 1093 | 170 | 7.3 |
| 0.94 | $1.3\times 10^{14}$ | 8.7 | 145 | 1069 | 174 | 9.3 |
| 0.93 | $1.5\times 10^{14}$ | 10 | 143 | 1051 | 179 | 12 |
| 0.93 | $1.6\times 10^{14}$ | 11 | 153 | 1158 | 177 | 13 |
| 0.92 | $1.7\times 10^{14}$ | 11 | 142 | 1038 | 183 | 14 |
| 0.92 | $1.8\times 10^{14}$ | 12 | 150 | 1131 | 181 | 15 |
| 0.91 | $1.9\times 10^{14}$ | 13 | 141 | 1028 | 187 | 16 |
| 0.91 | $2.0\times 10^{14}$ | 13 | 149 | 1110 | 186 | 18 |

: Possible orbital solutions for the W Aql system.

Notes: $e$ is the eccentricity, $r_p$ is the periastron, $a$ is the semimajor axis, $T$ is the orbital period, $\Delta t$ is the time since the most recent periastron, and $t_\mathrm{close}$ is the amount of time the two stars spend close together (see Methods [3.9](#sec:solution)).

# Supplementary Materials

## Radiation pressure on dust

Here we compare the contribution to the radiation pressure on dust from the AGB and F9 stars. The ratio of the radiation pressure force on dust grains, ${F}_{P_r} = |\vec{F}_{P_r}|$, over the gravitational attraction, ${F}_\mathrm{grav}=|\vec{F}_\mathrm{grav}|$, is defined as $$\begin{equation}
\label{Gamma}
\Gamma = \frac{F_{P_r}}{F_\mathrm{grav}} \simeq \frac{\sigma_d \bar{Q} \Psi}{4 \pi c m_\mathrm{dust} GM_\star} L_\star = \left( \frac{\bar{Q} \Psi}{3 \pi c a \rho_d G}\right) \frac{L_\star}{M_\star}
\end{equation}$$ where $\sigma_d = \pi a^2$ is the cross-section of the assumed spherical grain, with $a$ the radius, $\bar{Q} = 2\times 10^{-2}$ is the mean radiation pressure efficiency of the grains (cite: Tielens1983), $\Psi = 2\times 10^{-3}$ is the dust to gas ratio (cite: Danilovich2014), $c$ is the speed of light, $m_\mathrm{dust} = \frac{4}{3}\pi a^3 \rho_d$ is the mass of a dust grain (derived from volume, assuming a sphere, and a specific dust density of $\rho_d = 3.3$ g cm$^{-3}$), and $M_\star$ and $L_\star$ are the stellar mass and luminosity. A dust driven wind is achieved for $\Gamma > 1$.

When comparing the ability of the AGB and F9 stars to drive the wind through radiation pressure, the properties in brackets on the right-hand side of equation [\[Gamma\]](#Gamma) do not change, so the dust driving potential comes mainly from the luminosity of the star. For the AGB star, the luminosity is $7500~L_\odot$ (cite: Danilovich2014), while for the F9 star it is $\sim 1.5~L_\odot$. We use the system mass of $2.66~\mathrm{M}_\odot$ as this is the maximum possible gravitational force that must be overcome by the radiation pressure.

For relatively small grains with $a=0.03~\mu$m, we find $\Gamma_\mathrm{AGB} = 1.1$ and $\Gamma_\mathrm{F9} = 2.3\times 10^{-4}$, indicating that the F9 star’s contribution to driving the wind is negligible.

## Anisotropic mass loss

Recent observational studies of AGB stellar discs and inner winds at near-infrared wavelengths have shown asymmetric and clumpy surface brightnesses (cite: Ohnaka2016; Khouri2016; Wittkowski2017; Paladini2018; Khouri2020). These broadly agree with 3D hydrodynamical simulations of AGB atmospheres, which predict the formation of large convective shells in the low-gravity environment of the AGB star’s extended atmosphere, resulting in a clumpy and non-spherical atmospheric structure and asymmetric dust formation (cite: Freytag2008; Freytag2017; Freytag2023). Similar asymmetric features have also been observed in the millimetre range with ALMA, in both the continuum emission and for molecular lines that originate in, or close to, the stellar atmosphere (cite: Vlemmings2017; Takigawa2017; Khouri2019; Velilla-Prieto2023). A recent study of the nearby carbon star CW Leo determined that the asymmetries in the stellar atmosphere and inner wind are unlikely to have been formed as a result of binary interactions, but rather as a result of varying temperature and density conditions caused by convection cells (cite: Velilla-Prieto2023). This is despite the larger-scale shells observed around this star being thought to have formed as a result of binary interactions (cite: Cernicharo2015a). In light of these observational and modelling results, we analysed whether the various anisotropies reported in the molecular emission around W Aql could be related to random convection cells rather than formed through binary interactions.

The asymmetries we see on the largest scales in the molecular emission around W Aql are those that we associate with the photodissociation of common species (SiO, SiS, CS, HCN) by the F9 companion, as discussed in the Results and in Methods [3.4.7](#sec:othermolecules) and [3.6.4](#otherchem). While we do see some smaller-scale asymmetries in these molecular lines, which may have originated as a result of the chaotic distributions of convective cells before expanding in the wind (e.g. see the non-uniform distributions of SiS and CS in their central channels, shown in Fig. [17](#cssissinglechans), or the smaller-scale arcs and clumps seen in the CO emission in Figs. [3](#coarcs) and [7](#cochan)), these are unlikely to account for the overall asymmetry on a larger scale.

The asymmetric emission detected for SiN, SiC and NS is generally seen on smaller scales than the asymmetries in the common species discussed above and has higher degrees of asymmetry. Such an arc-like distribution is unlikely be formed as a result of localised (and necessarily very specific, based on the observations) fluctuations of temperature and density caused by convective cells. If these asymmetries were formed as a result of random fluctuations, we would expect them to be formed in several directions (e.g. see (cite: Freytag2023)), not just in an arc on one side of the AGB star, and would expect additional similar fluctuations to have occurred in the $\sim 170$ years since the formation of the observed SiN arc. For example, the model by Freytag et al. (cite: Freytag2023) that most closely resembles W Aql has events of elevated dust production on a time scale of a few to tens of years.

We also note that the formation of both SiN and SiC is driven by (Methods [3.6.1](#chem:sin)), which has an ionisation energy of 8.2 eV (cite: Martin1998) and hence is most easily ionised by UV photons. Ergo, as discussed in Results and Methods [3.4.3](#sinsic) and [3.6.1](#chem:sin), the formation of SiN in an arc to one side of the AGB star suggests formation during a close periastron interaction between the AGB and F9 stars.

However, the distribution of SiN emission seen in the zeroth moment map and PV diagram in Fig. [1](#sin) does not reveal a perfectly uniform structure. For example, there are regions of brighter flux in the zeroth moment map, enclosed in the $5\sigma$ contours, which are not symmetric along the axis connecting the AGB and F9 stars. Similarly, the PV diagram is not perfectly symmetric across the LSR velocity axis and shows clumps of brighter emission. These clumpy asymmetries are more likely to be caused by variations in density and temperature driven by chaotic motions of convection cells, similar to the clumpy emission seen in the inner wind of CW Leo (cite: Velilla-Prieto2023). It is also possible that some of the enhancements were caused by the interaction between the shock created by the companion’s passage and the pulsation of the AGB star, as modelled in the simulations of Aydi et al (cite: Aydi2022). Such varying conditions could explain why, for example, there is only one bright clump of NS in the PV diagram (Fig. [14](#nsplot)) but several bright clumps of SiN and SiC.

We conclude that the large arc-like structure of the molecular emission is more consistent with enhanced formation during the periastron interaction of the AGB and F9 stars. However, anisotropic mass loss processes may also have contributed to the precise small-scale structure of the SiN, SiC and NS emission.

## Additional figures

![image](LostFluxCO.pdf) ![image](SiN_resolved_out_flux_-24.pdf)

![image](blue_red_SiN_components.pdf)

![image](W_Aql_NS_mom0_paper.pdf) ![image](W_Aql_PV_NS_paper.pdf) ![image](periastron_species_spectra.pdf)

![](W_Aql_HC3N_J28-27_mom0.pdf)

![image](W_Aql_HC3N_J26-25_mom0.pdf) ![image](W_Aql_HC3N_J25-24_mom0.pdf)

![](resolved_out_flux.pdf)

![image](W_Aql_combined_SiS12-11_cent_channels.pdf) ![image](W_Aql_combined_CS_cent_channels.pdf)

![image](CS_PV_1001pix.pdf) ![image](SiO_PV_1001pix.pdf)

![](H13CN_PV_1001pix.pdf)

![](CO_PV_1001pix.pdf)

![image](row_orich.pdf) ![image](row_crich.pdf)

![image](row_Si+N_orich.pdf) ![image](row_Si+N_crich.pdf)

![image](Jolien_density.pdf) ![image](New_phantom_density.pdf)

![image](face_on1.pdf) ![image](face_on2.pdf) ![image](face_on3.pdf) ![image](face_on4.pdf) ![image](edge_on1.pdf) ![image](edge_on2.pdf) ![image](edge_on3.pdf) ![image](edge_on4.pdf)

![](W_Aql_Phantom-MCFOST_ang-rad_4pi.pdf)

![image](W_Aql_ang-rad_zoom15_4pi_no_curves.pdf) ![image](W_Aql_ang-rad_zoom5_4pi_no_curves.pdf)

![](w3009_op_full.jpg)

![image](SPH_annotated_zoom.pdf) ![image](W_Aql_phantom_mcfost_zoomout.pdf)

![](orbit_diagram.pdf)

[^1]: <https://lmfit.github.io/lmfit-py/index.html>

[^2]: Programme ID: 2018.1.00659.L, PI L. Decin

</paper>

Write the methods card for this paper.