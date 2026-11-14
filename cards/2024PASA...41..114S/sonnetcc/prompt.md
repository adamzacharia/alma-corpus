# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024PASA...41..114S\sonnetcc\reply.txt

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
 "bibcode": "2024PASA...41..114S",
 "title": "A jet-induced shock in a young, powerful radio galaxy at z = 3.00",
 "year": 2024,
 "journal": "Publications of the Astronomical Society of Australia",
 "first_author": "Seymour, Nicholas",
 "n_authors": 12,
 "arxiv_id": "2410.20609",
 "doi": "10.1017/pasa.2024.101",
 "alma_projects_linked_by_archive": [
  "2017.1.00719.S"
 ]
}
```

Paper text:
<paper>
# A Jet-Induced Shock in a Young, Powerful Radio Galaxy at $z=3.00$

## Abstract

The bright radio source, GLEAM J091734$-$001243 (hereafter GLEAM ­J0917­$-$0012), was previously selected as a candidate ultra-high redshift ($z>5$) radio galaxy due to its compact radio size and faint magnitude ($K(\rm AB)=22.7$). Its redshift was not conclusively determined from follow-up millimetre and near-infrared spectroscopy. Here we present new *HST* WFC3 G141 grism observations which reveal several emission lines including \[NeIII\]$\lambda$3867, \[NeV\]$\lambda$3426 and an extended ($\approx$$4.8\,$kpc), \[OII\]$\lambda$3727 line which confirm a redshift of $3.004\pm0.001$. The extended component of the \[OII\]$\lambda$3727 line is co-spatial with one of two components seen at 2.276 GHz in high resolution ($60\times 20\,$mas) Long Baseline Array data, reminiscent of the alignments seen in local compact radio galaxies. The `BEAGLE` stellar mass ($\approx$$2\times 10^{11}\,$M$_\odot$) and radio luminosity ($L_{\rm 500MHz}\approx$$10^{28}\,$W Hz$^{-1}$) put GLEAM ­J0917­$-$0012 within the distribution of the brightest high-redshift radio galaxies at similar redshifts. However, it is more compact than all of them. Modelling of the radio jet demonstrates that this is a young, $\approx 50\,$kyr old, but powerful, $\approx 10^{39}\,$W, compact steep spectrum radio source. The weak constraint on the active galactic nucleus bolometric luminosity from the \[NeV\]$\lambda$3426 line combined with the modelled jet power tentatively implies a large black hole mass, $\ge 10^9\,$M$_\odot$, and a low, advection-dominated accretion rate, **i.e. an** Eddington ratio $\le 0.03$. The \[NeV\]$\lambda$3426/\[NeIII\]$\lambda$3867 vs \[OII\]$\lambda$3727/\[NeIII\]$\lambda$3867 line ratios are most easily explained by radiative shock models with precursor photoionisation. Hence, we infer that the line emission is directly caused by the shocks from the jet and that this radio source is one of the youngest and most powerful known at cosmic noon. We speculate that the star-formation in GLEAM ­J0917­$-$0012 could be on its way to becoming quenched by the jet.

# INTRODUCTION 

Over the last few decades ‘feedback’ processes between the central black hole and host galaxy have become part of the accepted paradigm for galaxy evolution. Numerical simulations were initially found to over-produce the number of massive galaxies (cite: Bower:06; Croton:06) until a mechanism was introduced to cool gas and prevent excessive star formation at the high mass end of the galaxy stellar mass function. This mechanism was proposed to be energy injected into the cgm and intracluster medium by jets from the central black hole (although feedback may occur through means other than radio jets). Now there are numerous observations which support the idea that radio jets produced by agn provide one of the main forms of mechanical feedback. This negative ‘feedback’ occurs on both large scales (cite: Gitti:11) and small scales (cite: devries:97; Axon:08). Indeed, the compact radio-loud QSO 3C48 at $z=0.369$ is the archetypal css source presenting alignment between the optical and compact ($<5\,$kpc) radio emission (cite: Stockton:07; An:10).

The population of compact radio galaxies known as gps and css sources (cite: Peacock:82) are prime candidates for jet feedback within the ism of the host galaxy (cite: odea:21). gps sources are characterised as having radio spectra peaking between 1-5 GHz in the observer’s frame (cite: Gopal-Krishna:83) and tend to have sizes $<500\,$pc, but the broader class of peaked radio sources can have a peak outside typical observing frequencies depending on their redshift and age. css sources are compact radio sources that have steep spectra ($\alpha<-0.5$, where the flux density $S_\nu\propto\nu^\alpha$ and $\nu=$ frequency) over the entire observed frequency range, and are observed to be slightly larger than gps sources, $0.5-20\,$kpc. As the rest-frame peak frequency of gps sources decreases with increasing source size (cite: odea:97) the natural inference is that css sources are older or higher-redshift sources where the peak frequency has been shifted below the range of current observations. Indeed, radio sources with measurable peaks below $400\,$MHz have been referred to as mps sources (cite: Callingham:17; Ross:22) and show evidence for a redshift distribution up to, and possibly beyond, $z\approx 2.4$ (cite: Coppejans:15).

Evidence that gps/css sources are involved in feedback including (a) the kinematics of the jet-aligned extended emission lines, (b) the asymmetry of radio morphology suggesting interaction with dense clouds in the ism (cite: Saika:95) and (c) observations of hot gas from X-ray observations which is also shocked and aligned with the jet (cite: Massaro:09). A common feature of extended, powerful radio galaxies at low-redshift is the presence of eelrs on scales of $11-45\,$kpc (cite: Fu:09a). While they are often seen with velocities of $500-1100\,$km s$^{-1}$ with indications that they are photoionised by the agn, they do not show any alignment with the radio jet (cite: Fu:09b). This result is in contrast to css sources which have direct evidence that they are caused by shocks (cite: Fu:06). The inference is that there is evolution from aligned eelrs in more compact ($\lesssim 10\,$kpc) radio sources due to shocks to a more disorderly alignment in more extended radio sources due to photoionisation (cite: Shih:13).

Studying radio galaxies at higher redshift provides a window into many galaxy evolution processes, e.g. the co-evolution of the galaxies with their central black hole (cite: Drouart:16), their proto-cluster environments (cite: Wylezalek:13) and the interaction of the jets with the dense ism, improving our knowledge of physics under extreme conditions (cite: Ighina:22). In fact, high-redshift radio galaxies often show intriguing alignments between the radio source and large-scale gaseous and stellar structures in the host galaxy and surrounding environment, such as those seen in rest-frame uv light (cite: Pentericci:99), submillimeter emission (cite: Stevens:03), and cold molecular gas (cite: klamer:04; emonts:23). While a possible explanation is that these alignments are caused by positive agn feedback in the form of gas cooling and triggered star formation (cite: Gullberg:16; Nesvadba:20), kinematically perturbed and shocked gas is often seen in the ionized gas along the extent of the radio jet (cite: VillarMartin:03), and negative feedback has been implied from observations of jet-induced outflows (cite: Nesvadba:17).

Understanding agn feedback mechanisms in these epochs is critical to unravelling how these processes shaped galaxy evolution. From a sample of 3CR galaxies at $z\approx 1$, (cite: Best:00b) demonstrated that smaller radio galaxies ($\leq 120\,$kpc) were more likely to have larger eelrs which are powered by shocks and have have kinematic velocities $>1000\,$km s$^{-1}$. The larger radio galaxies in this sample have eelrs powered by photoionisation instead. The same trend of high velocity, shock ionisation of eelrs in compact, $< 120\,$kpc, radio galaxies was also seen by (cite: DeBreuck:00) in a sample of powerful radio galaxies across $0<z<5.2$. gps and css sources are therefore the most extreme of these powerful radio sources consistent with the idea that the photoioinisation of their eelrs is caused by jet-induced shocks.

A new generation of low frequency radio surveys such as the tifr gmrt (cite: Swarup:91) Sky Survey (tgss) Alternative Data Release 1 (cite: Intema:17), the lofar (cite: VanHaarlem:13) Two-metre Sky Survey (cite: Shimwell:17) and the GaLactic and Extragalactic All-sky mwa (cite: Tingay:13) survey (cite: Wayth:15) has inspired several new searches for high redshift radio galaxies. While several searches rely on the classical uss (uss, $\alpha<-1.3$) technique (cite: Saxena:18b; Gloudemans:22) the broad 72–231 MHz frequency coverage of the GLEAM survey allows the shape of the radio spectra to be used as a selection tool. (cite: Drouart:20) used spectral curvature in the GLEAM band, non-detections in the VISTA Kilo-degree Infrared Galaxy (VIKING) survey (cite: Edge:13), and compact radio sizes at high-frequency as a selection method finding one out of four bright, $S_{\rm 151MHz}>100\,$mJy, radio galaxies lying at $z=5.5$.

The motivation for choosing sources with curvature at low frequency comes from empirical and theoretical modelling of the radio spectra of powerful radio galaxies at $z\approx 2-4$ (cite: Broderick:22). However, one can see how this method would select sources with peaked spectra within or below the GLEAM band (i.e. high redshift mps or css sources) and follows the hypothesis that $z>7$ radio galaxies will present redshifted peaked spectra due to the denser environment within the ism/cgm, more intense radiation from the cosmic microwave background as well as their age. From the handful of qsos detected in the radio at $z>6$, several show evidence for flattening of their radio spectra at lower frequencies (cite: Banados:21; Ighina:22; Endsley:22). D20 therefore confirmed that selecting sources with extreme radio to $K$-band flux density ratios, $S_{\rm 151MHz}/S_{2\mu{\rm m}}>10^5$, and faint $K$-band magnitudes is an effective selection technique to find $z>5$ radio galaxies (cite: Broderick:24).

Another source from D20, GLEAM J091734$-$001243 (hereafter GLEAM ­J0917­$-$0012), was also thought to potentially be at high redshift. As well as being compact, GLEAM ­J0917­$-$0012 has a faint $K$-band counterpart - both characteristics of very distant radio galaxies. However, follow-up millimetre (cite: Drouart:21) and near-infrared spectroscopy (cite: Seymour:22), failed to conclusively determine its redshift, necessitating the current study. Modelling in D21 demonstrated that the ALMA 100 GHz continuum was synchrotron dominated. In S22, hst wfc3 grism observations detected one weak line at $1.15\,\mu$m and continuum detections of the host galaxy in the F098M and F105W bands. A nearby, $\approx 1.5''$ offset, source was also identified (see Fig. [1](#fig:overlay)). Broad-band uv to radio sed fitting in S22 constrained by the $K$-band, the two wfc3 detections and the 100 GHz photometry found two photometric redshift solutions at $z\approx 3$ and $z\approx 8$ consistent with the faint $1.15\,\mu$m line being MgII or Lyman-$\alpha$, respectively.

In this paper, we present new wfc3 and southern hemisphere lba data which demonstrate that GLEAM ­J0917­$-$0012 is an extreme analogue of low redshift css sources with strong evidence of a jet-induced shock. Our new observations are presented in §[2](#sec:obs) with the results shown in §[3](#sec:res). We discuss these results in §[4](#sec:dis) before presenting our conclusion in §[5](#sec:con). Throughout this paper, we quote magnitudes in the AB system (cite: Oke:83), adopt a flat $\Lambda$CDM cosmology with parameters $h = 0.7$, $\Omega_{\rm M} = 0.3$, and $\Omega_\Lambda = 0.7$, and report $68\%$ confidence interval (or $1\sigma$) uncertainties unless otherwise specified.

# OBSERVATIONS AND DATA PROCESSING

## New hst wfc3 Observations

We observed GLEAM ­J0917­$-$0012 with wfc3 using the G141 grism and the F140W band for pre-imaging under proposal ID 16662. Our four orbits were observed in March and April 2022 and each orbit comprised four pairs of pre-imaging plus grism exposures. The orbits were paired into two different orientations chosen to avoid contamination of the host galaxy spectrum by the nearby source. These data complemented those presented in S22 (ID 16184) which comprised one orbit of F105W imaging and four orbits of G102 grism plus F098M pre-imaging (also paired into two different orientations). We processed the data using the grizli 1.4.0.dev31 (cite: Brammer:19). We reprocessed both the S22 **observations** (F098M, F105W, G102) and new F140W+G141 ones following the same procedure as described in S22. We provide a brief description below.

The initial steps include direct imaging and grism exposure associations, flat-fielding of the exposures, pixel flagging (bad pixels and cosmic-rays rejection and persistence masking), relative exposure-level astrometric alignment, sky-background subtraction, and drizzling of the direct imaging (with $0.06\times 0.06\,$ arcsec pixels) and grism visits. After these initial steps, individual exposures are aligned to the *Gaia* DR3 catalogue (cite: Gaia:23), a direct F098M+F105W+F140W image mosaic is created and diffraction spikes of bright sources are masked. Source detection is then performed on the mosaic image with the `Source Extractor` (cite: Bertin:02) python wrapper `sep` (cite: Barbary:16), and matched-aperture photometry is performed on the three filters. Spectral traces are then identified based on the source catalogue and the spectral continua of the sources are modelled for contamination removal. After these steps, we then extract the 2D cutout of the spectra of the host and the nearby source and then use grizli to fit the 2D G102+G141 grism data.

In Table [1](#tab:pos) we present the positions of the host and nearby source from grizli. These values are the same as reported in S22. The optical photometry for the host is presented in Table [2](#tab:hst). We use the `photutils` of `astropy` to determine the photometry with a $0.7\,$arcsec radius aperture and a local background determined from a $3-5\,$arcsec annuli centred on the grizli reported position. Following S22, we determined the aperture corrections for wfc3, by taking the inverse of the nearest set of values of the fractional flux enclosed in Table 7.6 of the wfc3 instrument handbook and interpolated them linearly using the $0.7\,$arcsec radius and central wavelength of each filter. A $5\%$ systematic uncertainty was added to the measurement uncertainty (to account for the absolute flux uncertainty and any uncertainty in the aperture correction). In Fig. [1](#fig:overlay) we present the near-IR imaging along with the radio data described below. The spectroscopic results, including the 1D and 2D G141 spectra plus the grizli best fits, are shown in Fig. [2](#fig:spec:host) for the host and Fig. [3](#fig:spec:com) for the nearby source. Note the absolute positional uncertainty of an hst single pointings is $2-5\,$mas[^1].

|    galaxy     | R.A.(J2000)  | dec.(J2000)  |
|:-------------:|:------------:|:------------:|
|     host      | 09h17m34.42s | -00d12m42.5  |
| nearby galaxy | 09h17m34.32s | -00d12m43.0s |

: Positions of the host of GLEAM ­J0917­$-$0012 (Host) and the nearby galaxy as measured by grizli.

![image](Figures/GLEAMJ0917-0012_alma_f140w.pdf) ![image](Figures/GLEAMJ0917-0012_lba.pdf)

## lba Observations

We observed GLEAM ­J0917­$-$0012 with the Southern Hemisphere lba under project V605a from 2021 July 17 23:00 to 2021 July 18 09:00 UTC. The following telescopes were available: Murriyang (the 64-metre Parkes radio telescope), the atca (atca; five 22-m antennas in tied-array mode), Mopra, Hobart (26 m), Ceduna, Warkworth (12 m), Katherine (flagged due to poor sensitivity), Yarragadee, Hartebeesthoek (26 m) and Tidbinbilla (70 m). Target scans of duration 4 min were interleaved with 1.5-min scans of the phase calibrator B0922$+$005. We also regularly observed B0906$+$015 to phase up atca, used the sources B0208$-$512, B0537$-$441, B0834$-$201 and J1147$-$3812 for fringe finding, and observed B1934$-$638 for atca flux density calibration. The observations were dual-polarisation, with four sub-bands centred at 2252, 2268, 2284 and 2300 MHz, each with bandwidth 16 MHz (i.e. a centre frequency of 2276 MHz and a total bandwidth 64 MHz). The total time on-source for GLEAM ­J0917­$-$0012 was 5.6 h.

To correlate the data we made use of the DiFX software correlator (cite: deller11) running at the Pawsey Supercomputing Centre. The data were averaged to 2 s accumulation periods and 0.5 MHz resolution during correlation. Parkes recorded native linear polarisations which were converted to a circular basis after correlation using the PolConvert package (cite: 2016A&A...587A.143M). Data were calibrated in the aips[^2] following standard procedures for the lba, implemented using the Parseltongue interface (cite: 2006ASPC..351..497K). In the absence of good system temperature measurements at several stations, array amplitude calibration was achieved by bootstrapping to the compact source B0922$-$005 whose flux on lba scales was assumed to be 90% of that measured in a near-simultaneous atca observation – this assumption leads to a $\approx 10$% uncertainty on the flux scale for the target source (this error estimate is supported by flux densities derived for calibrators in the observation that also had near-simultaneous atca observations). Katherine had significantly reduced sensitivity due to a problem with the data acquisition system and was thus omitted from the final analysis.

The source was imaged using the casa (cite: casa:22) with Briggs weighting of $R=0.5$, a uvtaper of $5000\,$k$\lambda$ and the multi-frequency synthesis option to provide a restoring beam of $73\times 26\,$mas and a position angle of $-82.4^\circ$. The rms noise in the image is $54\,\mu$Jy per beam at the effective central frequency of 2276 MHz. The contours of this image are overlaid on the combined F098M/F105W/F140W image in the right panel of Fig. [1](#fig:overlay). We estimate the absolute astrometry uncertainty to be $\le 1\,$mas, and is an equal combination of systematic uncertainty from a 2 degree target-calibrator separation at 2.4 GHz and the random position uncertainty ($\approx\frac{\rm beamsize}{2\times {\rm SNR}}$).

## Literature Data

### Radio Data

D20 presented 25 radio photometric measurements of GLEAM ­J0917­$-$0012, including 20 from the GLEAM survey, one from the nrao vla Sky Survey (cite: Condon:98), and four across $5-20\,$GHz from the atca (cite: Frater:92). This target was originally selected due to its negative curvature across the GLEAM band, $70-230\,$MHz, which suggested a flattening of the spectral index towards the lower end of that range. Modelling of the GLEAM and higher frequency data (see D20, D21 and S22) found that the radio spectrum was best fit by a double power-law with a break frequency of $\approx 2\,$GHz, $\alpha_{\rm LOW}\approx -0.9$ and $\alpha_{\rm HIGH}\approx -1.8$. A triple power-law with a low frequency turn-over below 70 MHz, to account for the 70-230 MHz curvature, was found not to provide a better model fit, despite the evident curvature across this frequency range.

### Optical and ir data

The Third Data Release of the hsc Subaru Strategic Program (cite: Aihara:22) is significantly deeper than the Second Data Release used in S22. GLEAM ­J0917­$-$0012 falls in the ‘Wide’ layer of this survey so we downloaded the new, deeper $grizy$ data from the public data release webpage[^3]. We used aperture photometry on the wfc3 position of GLEAM ­J0917­$-$0012 (Table [1](#tab:pos)) with the same $0.7\,$arcsec radius aperture and $3-5\,$arcsec annulus as in § [2.1](#subsec:hst) with the aperture corrections determined in S22. As the $y$-band image was still less deep than the F098M image we excluded it from this analysis. As we used a different method for the photometry in this work (compared to D20 and S22) we re-extracted the flux density of GLEAM ­J0917­$-$0012 in the HAWKI $K$-band image from D20 using the `photutils` method described in § [2.1](#subsec:hst). The HSC $griz$ and HAWKI $K$-band photometry, along with that from WFC3, is presented in Table [2](#tab:hst) and used in the SED fitting presented in § [3.3.1](#sec:res:beagle). We also use the mid-ir non-detections from the wise (cite: Wright:10) given in S22 to constrain the agn bolometric luminosity (§[4.4.2](#sec:dis:mass)).

### alma Continuum Data

We use the alma 100 GHz continuum data from D20. This data comprised five 10-min spectral scans across $85-115\,$GHz. No significant spectral features were found. The 100 GHz contours overlaid on the F140W image in the left panel of Fig. [1](#fig:overlay) is a naturally weighted image with an rms of $10\,\mu$Jy per beam, a restoring beam of $1.2''\times 1.4''$, and position angle of $-89^\circ$. The 100 GHz flux density reported in D21 is $60\pm 13\,\mu$Jy.

### Interplanetary Scintillation Measurement

The gama9 field (cite: driver:11) was covered by mwa ips observations at 162 MHz (cite: Morgan:18; Chhetri:18). GLEAM ­J0917­$-$0012 has a nsi of $0.49\pm 0.03$ implying that around half the flux is more compact than $\approx 0.3$ arcsec or there are two compact components separated by more than $\approx 0.3\,$arcsec (see D20 for details).

### erosita Data

The erosita (cite: Predehl:21) instrument on the srg orbital observatory (cite: sunyaev:21) carried out an early survey of the gama9 field, in which GLEAM ­J0917­$-$0012 is situated, to the final depth of the planned all-sky surveys. We find that GLEAM ­J0917­$-$0012 is undetected in the efeds (cite: Brunner:22) implying an upper limit to its X-ray $0.5-2.0\,$keV flux of $6.5\times 10^{-15}\,$ erg cm$^{-2}$ s$^{-1}$, the point source $80\%$ completeness limit of efeds.

# RESULTS AND ANALYSIS

## hst data

### Imaging

Both galaxies are detected in the new F140W image as well as the F105W image. The host of GLEAM ­J0917­$-$0012 remains undetected in the F098M image. The F098M and F105W photometry is consistent within 10% of that reported in S22 with the small difference likely due to slightly different background subtracted method (local here vs global in S22). The left panel of Fig. [1](#fig:overlay) presents the F140W image overlaid with the 100 GHz alma contours. The host is extended towards the nearby source. The strongest line detected in the host (\[OII\]$\lambda 3727$ doublet, hereafter \[OII\] - see §[3.1.2](#sec:res:hst:spec)) is found to be spatially extended by `Grizli` (see Fig. [2](#fig:spec:host)). Hence, in the right panel we present the combined near-ir image overlaid with contours of the \[OII\] emission map and our lba observations (see §[3.2](#sec:res:lba)). The \[OII\] line and lba continuum emission are co-spatial and also extended towards the nearby source. However, the spectroscopy discussed in §[3.1.2](#sec:res:hst:spec) confirms that the nearby source is at a lower redshift and that this alignment is purely coincidental.

| band               |  AC   | $F_{\nu}$ \[$\mu$Jy\] |
|:-------------------|:-----:|:---------------------:|
| $g_{\rm HSC}$      | 1.506 |     $0.11\pm0.03$     |
| $r_{\rm HSC}$      | 1.703 |     $0.31\pm0.06$     |
| $i_{\rm HSC}$      | 1.332 |     $0.22\pm0.05$     |
| $z_{\rm HSC}$      | 1.567 |     $0.29\pm0.11$     |
| F098M              | 1.089 |    $0.26\pm 0.14$     |
| F105W              | 1.093 |    $0.50\pm 0.06$     |
| F140W              | 1.217 |    $1.43\pm 0.12$     |
| $K_s({\rm HAWKI})$ | 1.327 |     $4.12\pm0.37$     |

: wfc3, hsc and HAWKI $K$-band aperture corrections, flux densities and uncertainties for the host of GLEAM ­J0917­$-$0012. The uncertainties conservatively include an extra 5% to account for absolute flux calibration and uncertainty in the aperture correction.

### Spectroscopy

![](Figures/G141_new.pdf)

![](Figures/com_G141_new.pdf)

In Fig. [2](#fig:spec:host) we present the G141 spectrum of the host of GLEAM ­J0917­$-$0012. The grizli software identifies several spectral features, with the strongest line being the \[OII\] doublet. The other lines **detected** are \[NeV\]$\lambda3426$ and \[NeIII\]$\lambda3867$ (hereafter \[NeV\] and \[NeIII\] respectively). This combination of lines puts GLEAM ­J0917­$-$0012 at $z=3.004\pm 0.001$, implying that the weak line previously identified with the G102 grism (S22) at $1.15\,\mu$m is MgII$\lambda\lambda 2796,2803$.

The properties of the \[OII\], \[NeV\] and \[NeIII\] lines are reported in Table [2](#tab:hst).

In Fig [3](#fig:spec:com) we present the 1D and 2D spectrum for the galaxy $\sim 1.5''$ away from the host of GLEAM ­J0917­$-$0012. We also include the best fit `grizli` model to the data which finds the \[OII\]$\lambda$3727, H$\beta$, \[OIII\]$\lambda$5007 lines confirming the redshift to be $z=2.126\pm 0.001$, consistent with the photometric redshift of $z_{\rm phot}$$=$$2.2^{+0.3}_{-0.6}$ presented in D21. Hence this source is physically unrelated to the host of GLEAM ­J0917­$-$0012and we consider it no further.

The redshift solution of $z=3.004$ is consistent with the lower of the two options put forward in S22. While this radio galaxy is not at $z>7$, it still demonstrates several unique properties. From the radio photometry presented in D20 and the modelling in (cite: Broderick:22) the 500 MHz rest-frame luminosity of this source is $L_{\rm 500MHz}=1.0\pm0.1\times 10^{28}\,$W Hz$^{-1}$ (conservatively including a 10% uncertainty from the modelling), putting it well into the ‘powerful’ hzrg (hzrg: $z>1$ and $L_{\rm 500MHz}\ge 10^{27.5}\,$W Hz$^{-1}$) regime (cite: Miley:08; DeBreuck:10). This result, as well as the 1.4 GHz and 178 MHz luminosities, is presented in Table [4](#tab:sum_radio). We discuss how this hzrg compares to others at the same redshift in §[4.2](#sec:dis:comp).

The \[NeIII\] and \[NeV\] lines are strong indicators of the presence of an AGN (cite: gilli:10) due to their high ionisation potentials (cite: Maddox:18) and equivalent widths of $\ge 4\,$Å are enough to confirm the presence of an obscured agn. The \[OII\] line is typically indicative of star formation and often used as sfr tracer (cite: Kennicutt:92). However, from the high radio luminosity and neon lines, we know that there is a powerful AGN present. Due to its brightness we can map the \[OII\] (Fig. [1](#fig:overlay)) and see that it extends $\approx 0.6''$, equivalent to 4.7 kpc. Indeed, in the 2D spectrum (Fig. [2](#fig:spec:host)) one can see the spatially extended \[OII\]. The \[NeV\] and \[NeIII\] lines are too faint to be mapped out.

Hence, if the \[OII\] emission is primarily powered by an AGN then we can determine an upper limit to the unobscured sfr using the equation 4 of (cite: kewley:04) and the relation in (cite: Kennicutt:98). Note no correction is made to the \[OII\] line luminosity for reddening as the SED fitting in § [3.3.1](#sec:res:beagle) cannot constrain the dust attenuation well and the three lines are close together. From a line luminosity of $L_{\rm [OII]}=3.28\times 10^{42}$erg s$^{-1}$ we obtain a sfr upper limit of $<$$22$ and $<$$46\,$M$_\odot$ yr$^{-1}$ for the K04 and K98 conversions, respectively (see Table [3](#tab:sum_opt)).

Powerful radio galaxies have been classically separated into two distinct classes based on the strength of their optical emission lines (cite: Hines:1979). Radio galaxies with strong emission lines are referred to as high excitation (radio) galaxies, HE(R)Gs, and those with weak emission lines as low excitation (radio) galaxies, LE(R)Gs. The original work was based on the \[OII\] line strength (cite: Hines:1979), but newer criteria exist based on a combination of lines (cite: Buttiglione:10). The grism spectra do not cover all the lines to make a formal classification with the (cite: Buttiglione:10) criteria so we make the assumption that the \[OIII\]$\lambda$5007 line luminosity is within an order of magnitude of the \[OII\] line luminosity (as is typically seen in radio galaxies). Taking the 178 MHz luminosity along with the \[OIII\]$\lambda$5007 line luminosity we can place GLEAM ­J0917­$-$0012 on the scatter plot of these two luminosity in Fig. 8 of (cite: Buttiglione:10). We find that GLEAM ­J0917­$-$0012 lies at the high luminosity end of the LERG track and well away from the HERG track. So despite these high luminosities we consider GLEAM ­J0917­$-$0012 to be a LERG.

## LBA Results

In Fig. [1](#fig:overlay) we show the contours of the LBA observations over the combined F140W/F105W/F098M image. The relative uncertainty in the astrometry between lba and lba is small: the hst observations are tied to the *GAIA* DR3 reference frame, which is consistent with the icrf used by lba within $<$$0.01\,$mas (cite: Klioner:22). This difference is far less than the absolute positional uncertainty of lba, $<$$1\,$mas.

The lba data show two unresolved components separated by 620 mas, equivalent to a projected separation of 4.8 kpc. The ne component is closer to the galaxy centre, as inferred from the optical image, but it is far enough away that it is unlikely to be the core. Hence we are likely seeing the compact ends of two jets from the central black hole rather than a binary or offset agn. The sw component is 470 mas away from the peak of the optical emission. Assuming the central black hole is located at this optical peak, the projected length of the jet to the SW component is 3.6 kpc. The flux densities were measured with the `miriad` task `imfit` and found to be $10.4\pm0.4$ and $6.8\pm0.5\,$mJy (not including the 10% overall flux calibration uncertainty) for the ne and sw components, respectively. The sum of these fluxes is $\approx 80\%$ of the estimated 2276 MHz total flux, $S_{\rm 2276MHz}=21.8\,$mJy, from the broad-band modelling presented in (cite: Broderick:22). Hence, $\approx 20\%$ of the flux density may be resolved out in the lba observations. If these two components indicate the ends of the jets/lobes and if we assume that the black hole is equidistant to the two hot spots, then we estimate an age of $\ge 78\,$kyr assuming the jet propagates at $0.1\,c$. This propagation speed is a median value for gps/css sources in the review by (cite: odea:21). Faster speeds, as assumed by the jet modelling in § [3.4](#sec:res:jet) would imply younger ages. This estimate is also consistent with the slowing jet propagation speeds for older jets seen in powerful GPS sources (cite: An:12).

The compact size of the radio emission is $\ll 20\,$kpc, consistent with the radio source being classified as CSS. The extended \[OII\] is aligned with the SW radio component, which is a common property of CSS sources (cite: devries:97). We discuss the extended \[OII\] further in §[4.2](#sec:dis:comp). The observed asymmetry suggests that the NE component is likely impacting denser ISM than the SW component.

The two compact component model with some extended flux is also consistent with the morphological models put forward to explain the IPS value of NSI $=0.49\pm 0.03$ reported in D21. An NSI of unity implies an unresolved source at 162 MHz (i.e. $\leq 0.3\,$arcsec) whereas a value of zero implies all the flux is extended on larger scales. An in-between value implies either that only a fraction of the flux is compact and/or that there is more than one compact component, as is the case here.

## Modelling the Host Galaxy

### SED

We use the SED fitting code beagle (cite: Chevallard:16)[^4] to constrain the properties of the host galaxy. For this fitting we use the six photometric measurements in Table [2](#tab:hst), including three from WFC3, four from HSC and the one from HAWKI $K$-band. Inclusion of $<3\sigma$ *WISE* limits from S22 made no appreciable difference to the host galaxy properties nor their uncertainties.

Within beagle we use a delayed exponential sf history, a (cite: Calzetti:97) dust attenuation, and broad priors. The ionisation parameter and metallicity of the nebular regions is set equal to that of the stars. The dust to metal mass ratio is left as default value of 0.3. Hence, we allow only the following five parameters to vary: timescale of sf (hereafter ‘age’), stellar mass, current SFR (we report the SFR averaged of the last 100 Myr), metallicity and extinction.

beagle provides PDFs from which we take the median value as the best fit and the 68% confidence intervals for the uncertainties. In the case where the difference between the upper and lower 68% confidence interval is more than an order of magnitude we take the 95% confidence upper value as a $2\sigma$ upper limit. This affects only the SFR. These results are reported in Table [3](#tab:sum_opt) and the highest probability SED template is plotted in Fig [4](#fig:beagle).

Examining the bivariate PDFs (i.e. ‘corner plots’) there is some slight degeneracy between extinction and the stellar mass and age. However, the 68% confidence interval on the stellar mass ($1.7^{+0.9}_{-0.5}\times 10^{11}\,$M$_\odot$) and age ($39^{+300}_{-70}\,$Myr) are well constrained. The SFR is poorly constrained with the 68% confidence interval spanning three orders of magnitude. We thus report the 95% confidence interval upper limit for the SFR, but we note this is dominated by a secondary PDF peak corresponding to a very unobscured ($\tau_V\sim 1$) and very young ($\tau\sim 10\,$Myr) starburst. Hence, the true upper limit to the SFR is likely a lot lower ($\ll 10\,$M$_\odot$ from visual inspection of the PDF around the principle PDF peak).

![](Figures/J0917_1sigma_SED.pdf)

### Morphology

We use the F140W image to fit a (cite: Sersic:68) profile to the host galaxy using `PetroFit` (cite: Geda:22). The cutout fed to `PetroFit` was $3\times 3\,$arcsec and the rms image was created at a constant value equal to that of the locally determined off-source rms. The Sérsic model was convolved with the F140W PSF[^5] which was over-sampled by a factor of two relative to the drizzled pixel size. We find an effective radius (i.e. half-light radius), $R_{\rm eff}$, of $2\pm0.3\,$kpc and a Sérsic index of $n= 3.3 \pm 0.6$. We also determine $R_{\rm 80}$, corresponding to the radius encompassing 80% of the total flux (cite: Miller:19), which has the advantages of: (a) encompassing a larger fraction of the baryons and (b) finding similar sizes for both sfgs and quiescent galaxies (cite: Mowla:19). Using this relationship, which is a function of $R_{\rm eff}$ and the Sérsic index, we obtain $R_{\rm 80}=5.8\pm 1.1\,$kpc where the uncertainty is propagated from the inputs. These results are presented in Table [3](#tab:sum_opt), discussed in §[4.1](#sec:dis:host) and are used in modelling the radio jet in §[3.4](#sec:res:jet).

## Modelling the Radio Jet

![](Figures/raise_fit.pdf)

We constrain the jet power and age of the radio jet in GLEAM ­J0917­$-$0012 using a parameter inversion informed by simulations from the latest version of raise (cite: Turner:15; Turner_2023). The compact size of this source suggests its evolution will be dominated by the ISM of the host galaxy; we therefore model the distribution and density of this ambient medium in raise using Monte Carlo realisations of the effective radius and Sérsic profile fitted in Section [3.3.2](#sec:res:petro). In doing this we are assuming that the ISM has the same distribution in the galaxy as the stars.

The expansion rate (velocity) of the jet-head is proportional to the velocity of the bulk flow in the jet spine (Lorentz factor of $\gamma_\text{j} =5$), with a constant depending on the relative densities of the jet, $\rho_\text{j}$ and the ISM cloud, $\rho_\text{c}$, it is propagating through (cite: Turner_2023). Hence, the travel time through the ISM, i.e. age of the jet, is simply the integral of the inverse of the jet-head expansion rate along the jet path. This integral can include any variation in the ISM density, but for a fixed overall gas mass it is independent of the density profile.

Local density inhomogeneities in the multiphase ISM will not affect the jet expansion – compared to a smooth profile with the same total mass – provided no very dense clouds (i.e., $\rho_\text{c} \gg \gamma_\text{j}^2 \rho_\text{j}$; (cite: Turner_2023)) lie in the path of the jet. We therefore assume the density is locally homogeneous but note as the radio source is asymmetric a slightly older source age is possible if a dense cloud is encountered (Young et al., *in prep.*). The total mass of gas encountered by the jet remains a free parameter; we therefore constrain the total gas mass (the sum of the molecular, neutral and ionised gas, i.e. the sum of Baryonic matter minus the stars) as a third free parameter (in addition to the jet power and age).

raise model outputs (synthetic images and SEDs) are generated over a three-dimensional grid covering all reasonable values of these three parameters. We assume the default values for other parameters in raise, noting these are calibrated against hydrodynamical simulations and/or based on observations of well-studied sources. The equipartition factor (ratio of energy in the magnetic field to energy in the particles) assumes a prior probability density function following (cite: Turner:18b).

These synthetic images at 1.4 GHz are compared to the following observable values using a maximum likelihood approach: NVSS flux density, and the frequency-invariant extent of the jets from the LBA image. We find the steep two-point spectral index between 1.4 GHz and 5.5 GHz (photometry from NVSS and the ATCA, respectively) can be explained if the freshly shock-accelerated electron population is at a significantly lower magnetic field than the remainder of the population, as occurs when the jet-head passes the half-light radius of the galaxy, $R_\text{eff}$, into the steep, outer-sections of the galaxy Sérsic profile. This is consistent with our constraint on the extent of the jets. We do not include lower frequencies in the modelling as RAiSE currently does not include free-free absorption, a likely cause of the radio spectral flattening.

We find two potential solutions shown in the PDFs presented in Fig. [5](#fig:raise): a ‘fast’ jet with a (slightly) younger age and higher jet power, i.e. a source that expands at the speed of the bulk flow along the jet (hence the small scatter in jet ages) and a ‘slow’ jet with an older age and lower jet power which has at least some interaction with the ambient medium leading to a slowing of the jet. The ‘slow’ solution has a higher gas mass since the jet has to work harder to expand. The gas could be slightly more extended than inferred from the stellar morphology which would decrease the jet power and increase the source age. Conversely if the gas is slightly less extended then the jet power would increase and the gas mass decrease. In hzrgs we tend to see denser gas on more extended scales, often along the jet axis (cite: Klamer:09; Emonts:14). Of the two solutions, we believe the ‘slow’ jet to be more likely. First, the jet power distribution is very steep at the high powers (cite: Quici:24) so a random source is more likely to be at lower luminosity. Second, the hosts of hzrgs are more likely to be gas rich (cite: Emonts:14).

The best fit result and uncertainties for the slow jet solution are presented in Table [4](#tab:sum_radio) summerised as a jet power of $Q_{\rm jet}=1.5^{+1.3}_{-0.7} \times 10^{39}\,$W, an age of $47^{+43}_{-6}\,$kyr (n.b. the peak in the age PDF will shift with the assumed bulk flow velocity) and a gas mass of $2.0^{+5.9}_{-1.1}\times 10^{10}\,$M$_\odot$.

+----------------------------------+---------------------------------------------------------------------------+
| parameter                        | value                                                                     |
+:=================================+:=========================================================================:+
| WFC3/grizli                                                                                                  |
+----------------------------------+---------------------------------------------------------------------------+
| redshift, $z$                    | $3.004\pm0.001$                                                           |
+----------------------------------+---------------------------------------------------------------------------+
| lines observed                   | \[OII\]$\lambda\lambda3727$, \[NeV\]$\lambda3426$, \[NeIII\]$\lambda3867$ |
+----------------------------------+---------------------------------------------------------------------------+
| $S_{\rm [OII]}$                  | $1.61\pm 0.06 \times 10^{-16}\,$erg s$^{-1}$ cm$^{-2}$                    |
+----------------------------------+---------------------------------------------------------------------------+
| $L_{\rm [OII]}$                  | $3.28\pm 0.12 \times 10^{42}\,$ erg s$^{-1}$                              |
+----------------------------------+---------------------------------------------------------------------------+
| $S_{\rm [NeV]}$                  | $1.52\pm 0.6 \times 10^{-17}\,$erg s$^{-1}$ cm$^{-2}$                     |
+----------------------------------+---------------------------------------------------------------------------+
| EW$_{\rm [NeV]}$                 | $224\,$Å                                                                  |
+----------------------------------+---------------------------------------------------------------------------+
| $L_{\rm [NeV]}$                  | $3.1\pm 1.2 \times 10^{41}\,$ erg s$^{-1}$                                |
+----------------------------------+---------------------------------------------------------------------------+
| $S_{\rm [NeIII]}$                | $5.42\pm 0.77 \times 10^{-17}\,$erg s$^{-1}$ cm$^{-2}$                    |
+----------------------------------+---------------------------------------------------------------------------+
| $L_{\rm [NeIII]}$                | $1.10\pm 0.16 \times 10^{42}\,$ erg s$^{-1}$                              |
+----------------------------------+---------------------------------------------------------------------------+
| FWHM$_{\rm [OII]}$ (obs.)        | $157\pm 8\,$Å                                                             |
+----------------------------------+---------------------------------------------------------------------------+
| FWHM$_{\rm [OII]}$ (rest)        | $<3160\pm 160\,$km s$^{-1}$                                               |
+----------------------------------+---------------------------------------------------------------------------+
| SFR$_{\rm [OII]}$ (K04)          | $<22\,$M$_\odot$ yr$^{-1}$                                                |
+----------------------------------+---------------------------------------------------------------------------+
| SFR$_{\rm [OII]}$ (K98)          | $<46\,$M$_\odot$ yr$^{-1}$                                                |
+----------------------------------+---------------------------------------------------------------------------+
| beagle fitting results                                                                                       |
+----------------------------------+---------------------------------------------------------------------------+
| stellar mass, $M_{\rm stel}$     | $1.7^{+0.9}_{-0.5}\times 10^{11}\,$M$_\odot$                              |
+----------------------------------+---------------------------------------------------------------------------+
| SFR$_{\rm 100}$                  | $<164\,$M$_\odot$ yr$^{-1}$                                               |
+----------------------------------+---------------------------------------------------------------------------+
| $\log(\tau_{\rm age})$           | $390^{+300}_{-70}\,$Myr                                                   |
+----------------------------------+---------------------------------------------------------------------------+
| $\tau_V$                         | $0.52^{+0.69}_{-0.37}$                                                    |
+----------------------------------+---------------------------------------------------------------------------+
| $\log(Z)$                        | $-1.1\pm 0.5$                                                             |
+----------------------------------+---------------------------------------------------------------------------+
| `PetroFit` fitting results                                                                                   |
+----------------------------------+---------------------------------------------------------------------------+
| $R_{\rm eff}$                    | $2.0\pm0.3\,$kpc                                                          |
+----------------------------------+---------------------------------------------------------------------------+
| Sérsic index, $n$                | $3.3 \pm 0.6$                                                             |
+----------------------------------+---------------------------------------------------------------------------+
| $R_{\rm 80}$                     | $5.8\pm1.1\,$kpc                                                          |
+----------------------------------+---------------------------------------------------------------------------+
| other data                                                                                                   |
+----------------------------------+---------------------------------------------------------------------------+
| sSFR$^a$                         | 0.23 Gyr$^{-1}$                                                           |
+----------------------------------+---------------------------------------------------------------------------+
| $S_{\rm 0.5-2keV}$ (eROSITA)     | $<6.7\times 10^{-15}\,$ erg s$^{-1}$ cm$^{-2}$                            |
+----------------------------------+---------------------------------------------------------------------------+
| $L_{\rm 0.5-2keV}$ (eROSITA)$^b$ | $<1.7\times 10^{44}\,$erg s$^{-1}$                                        |
+----------------------------------+---------------------------------------------------------------------------+
| $L_{\rm BOL}$(\[NeV\])           | $1.1\pm 0.4\times 10^{12}\,$L$_\odot$                                     |
+----------------------------------+---------------------------------------------------------------------------+
| $L_{\rm BOL}$(mid-IR)            | $<5\times 10^{12}\,$L$_\odot$                                             |
+----------------------------------+---------------------------------------------------------------------------+

: Summary of the optical to near-IR properties of the host galaxy of GLEAM ­J0917­$-$0012

$^a$derived from the higher of the \[OII\] SFR upper limits. $^b$ assuming a photon index of $\Gamma=1.8$.\

+---------------------------------------------+----------------------------------------------+---+
| parameter                                   | value                                        |   |
+:============================================+:============================================:+:=:+
| Observables                                                                                |   |
+---------------------------------------------+----------------------------------------------+---+
| **$178\,$MHz luminosity, $L_{\rm 178MHz}$** | **$1.7\pm0.2\times 10^{28}\,$W Hz$^{-1}$**   |   |
+---------------------------------------------+----------------------------------------------+---+
| $500\,$MHz luminosity, $L_{\rm 500MHz}$     | $1.1\pm0.1\times 10^{28}\,$W Hz$^{-1}$       |   |
+---------------------------------------------+----------------------------------------------+---+
| $1.4\,$GHz luminosity, $L_{\rm 1.4GHz}$     | $5.2\pm0.5\times 10^{27}\,$W Hz$^{-1}$       |   |
+---------------------------------------------+----------------------------------------------+---+
| Largest angular extent                      | 4.8 kpc                                      |   |
+---------------------------------------------+----------------------------------------------+---+
| raise (slow jet)                                                                           |   |
+---------------------------------------------+----------------------------------------------+---+
| Jet power, $Q_{\rm jet}^{\tt RAiSE}$        | $1.5^{+1.3}_{-0.7}\times 10^{39}\,$W         |   |
+---------------------------------------------+----------------------------------------------+---+
| Jet age, $t_{\rm jet}$                      | $47^{+43}_{-6}\,$kyr                         |   |
+---------------------------------------------+----------------------------------------------+---+
| gas mass, $M_{\rm gas}$                     | $2.0^{+5.9}_{-1.1}\times 10^{10}\,$M$_\odot$ |   |
+---------------------------------------------+----------------------------------------------+---+
| Derived                                                                                    |   |
+---------------------------------------------+----------------------------------------------+---+
| black hole mass, $M_{\rm BH}$               | $\ge 10^{9}\,$M$_\odot$                      |   |
+---------------------------------------------+----------------------------------------------+---+
| $\lambda_{\rm EDD}$                         | $\le 0.03$                                   |   |
+---------------------------------------------+----------------------------------------------+---+

: Summary of radio and derived properties of GLEAM ­J0917­$-$0012.

# DISCUSSION

The measured and derived optical/near-IR and radio properties of GLEAM ­J0917­$-$0012 are presented in Tables [3](#tab:sum_opt) and [4](#tab:sum_radio) respectively.

## Host Galaxy Properties

The stellar mass and size of this galaxy as measured by $R_{\rm eff}$ put GLEAM ­J0917­$-$0012 around a factor of two below the mean mass-size relation in the redshift bin $2.5<z<3.0$ as determined from deep *HST* surveys of field galaxies (cite: Vanderwel:14). Using $R_{\rm 80}$, which is arguably a better measure of galaxy size (see §[3.3.2](#sec:res:petro)), GLEAM ­J0917­$-$0012 is still a factor of 1.5 below the mean mass-size relation for the same redshift bin (cite: Mowla:19). Even allowing for a slight evolution with redshift, as well as the paucity of massive galaxies in pencil-beam *HST* surveys, this result suggests that GLEAM ­J0917­$-$0012 is at the lower edge of the distribution of field galaxies, i.e. compact for its stellar mass and redshift.

The stellar mass, $M_{\rm stel}\approx 2\times 10^{11}\,$M$_\odot$, puts GLEAM ­J0917­$-$0012 at the low end of distributions of stellar mass seen in HzRGs (cite: Seymour:07; DeBreuck:10) perhaps consistent with it being at the low end of the radio luminosity distribution for this sample. This stellar mass is consistent with the total gas mass, $M_{\rm gas}\approx 2\times 10^{10}\,$M$_\odot$, derived in the raise model fitting of the jet: $M_{\rm gas}/M_{\rm stel}\approx 0.1$. The SFR is poorly constrained by beagle due to the wavelength coverage of available photometry, but the limits from the \[OII\] emission ($<46\,$M$_\odot\,$yr$^{-1}$) infer a specific SFR (sSFR) of 0.23 Gyr$^{-1}$. This value puts GLEAM ­J0917­$-$0012 at least 0.5 dex below the main sequence for star forming galaxies at this redshift (cite: Koprowski:24).

As the CO(4$\rightarrow$3) line is not detected at 86.4 GHz in the 85-115 GHz ALMA spectral scan reported in D21, we infer a limit to the CO luminosity of $L'_{\rm CO}< 10^{10}\,$K km s$^{-1}$ pc$^2$. This luminosity is equivalent to a limit on the molecular gas mass of $M_{\rm mol}<4.3\times 10^{10}\,$M$_\odot$. The implied molecular gas fraction, $f_{\rm gas}\equiv\frac{M_{\rm mol}}{M_{\rm stel}+M_{\rm mol}}$, is very low, $f_{\rm gas}\le 0.09$, consistent with the lower gas fractions seen in more massive galaxies at this redshift (e.g. Pérez-Martínez et al., submitted) with the caveat that few CSS sources have well-measured gas fractions (cite: odea:21).

## Comparison to Other HzRGs and GPS/**CSS** Sources

![](Figures/triptic.pdf)

The fitting with raise (§[3.4](#sec:res:jet)), unsurprising for such a compact source, finds a very young radio galaxy $\approx 50\,$kyr, but with a very high jet power. Note, it is unlikely that this radio source is beamed given the steep spectrum ($-1.7<\alpha<-0.8$ across $0.1<\nu_{\rm observed}/{\rm GHz}<30$), the $<2.6\%$ linear polarisation at 7.25 GHz (D21), and the fact we see both jets.

Fig. [6](#fig:quadtic) compares the properties of GLEAM ­J0917­$-$0012 to the sample of powerful HzRGs reported in (cite: Seymour:07) and (cite: DeBreuck:10). We limit the comparison to $2<z<4$ and compare 500 MHz luminosities to the redshift, size, and high frequency (151/187/200/325-1400 MHz) and low frequency (70-230 MHz) spectral indices. The latter is only available for the GLEAM detected sources and the higher frequency spectral indices are derived from NVSS (cite: Condon:98), i.e. 1.4 GHz, and GLEAM 200 MHz flux densities; where GLEAM data was not available, we use other low-frequency photometry: 178 MHz – (cite: Pilkington:65), 151 MHz – (cite: Waldram:96) and 325 MHz – (cite: Rengelink:97). GLEAM ­J0917­$-$0012 is on the lower end of the luminosity distribution and is smaller than all sources bar WN J1115$+$5016 (at $z=2.54$) which is a compact **radio** double with a size of $0.2''$ (1.64 kpc). WN J1115$+$5016 shows CIV$\lambda$1549 in broad absorption (cite: DeBreuck:01) suggesting an outflow like other broad absorption line QSOs.

GLEAM ­J0917­$-$0012 also has a steep high frequency spectral index compared to most HzRGs in this sample. Modelling of high redshift USS-selected radio galaxies suggests that the steep spectrum is partly by selection and partly due to higher inverse Compton losses at higher redshifts (cite: Morabito:18). As this source was selected at low-frequency, its USS nature is not by selection. Its steep high-frequency spectrum must be due to inverse Compton or simple synchrotron losses. The modelling from raise in §[3.4](#sec:res:jet) suggests that the steepening is likely caused by synchrotron losses combined with the sudden drop in magnetic field strength experienced by freshly shock-accelerated electrons upon exiting the galaxy.

Comparing the age and size of GLEAM ­J0917­$-$0012 to a sample of bright CSO sources across $2<z<2.37$ (cite: murgia:99), we find that it lies long the track of lobe dominated, rather than jet dominated, CSO sources. This result is not surprising as most ($\approx 80$%) of the radio emission is detected on LBA scales and our modelling with raise in §[3.4](#sec:res:jet) is based on these (small) lobes.

The extended component of the \[OII\] line in GLEAM ­J0917­$-$0012 is reminiscent of the jet-cloud interactions observed in low-redshift sources like 3C316 (cite: An:13) and 3C48 (cite: Stockton:07; An:10). In these objects, the jet morphology shows clear signatures of strong interactions, including knotty jet structures with bright jet knots and large jet bending indicative of deflection. The extension of the \[OII\] emission along the jet axis of GLEAM J0917–0012 is also reminiscent of alignments seen between the radio plasma and various constituents of the host environment in extended HzRGs, which often also show complex and knotty radio morphologies (cite: Miley:08).

From the broad-band radio spectral fitting in D21, the peak flux must be at $\ll 280\,$MHz (in the rest-frame) which potentially puts this source on or below the intrinsic turnover frequency vs. linear size relation presented in (cite: odea:97). We note that the most comparable source to GLEAM ­J0917­$-$0012, WN J1115$+$5016 (discussed above), must also have a rest-frame peak frequency $<255\,$MHz and hence may be another high redshift MPS/CSS source.

The X-ray non-detection with eROSITA implies a luminosity lower limit of $L_{\rm 0.5-2keV}<1.7\times 10^{44}\,$erg s$^{-1}$ (see Table[3](#tab:sum_opt)) assuming a photon index of $\Gamma=1.8$. Comparing this result to other X-ray observations of CSS sources (cite: kb:14) we see that (a) GLEAM ­J0917­$-$0012 lies in the region of parameter space occupied by FR II radio galaxies (cite: fr:74) and (b) it could be consistent with either a HERG or LERG. The former result is not too surprising as the LBA image detects the majority of the flux finding two compact lobes. As we determined in §[3.1.2](#sec:res:hst:spec) that this source is a LERG then we would expect the true X-ray luminosity to be roughly an order of magnitude below the limit (cite: kb:14).

## Origin of Ionising Field

As discussed in §[3.1.2](#sec:res:hst:spec), the presence of \[NeV\] is a strong indicator of an AGN and is often seen in radio galaxies with EELRs (cite: Spinrad:84). Compact radio galaxies with EELRs aligned with the radio emission are generally powered by shock ionisation (cite: DeBreuck:00; Fu:09a) as supported by observations of UV line ratios. Studies of EELRs typically focus on the \[OIII\]$\lambda$5008 and H$\alpha$ lines since the lower critical density of \[OII\] means it can arise well away from the narrow-line region in the EELR (cite: VillarMartin:11a).

Looking at the bright \[OII\] emission from GLEAM ­J0917­$-$0012 we estimate an upper limit to the velocity dispersion by fitting a single Gaussian to the 1D spectrum finding ($\equiv 3160\pm 160\,$km s$^{-1}$). This will over-estimate the velocity width as source morphology and velocity are convolved in grism observations (hence it is reported as an upper limit in Table [3](#tab:sum_opt)). Higher resolution prism/slit spectroscopy is required to determine an accurate value.

![](Figures/lineline.pdf)

Fig. [7](#fig:lineratio) presents the observed \[NeV\]/\[NeIII\] and \[OII\]/\[NeIII\] line ratios of GLEAM ­J0917­$-$0012 compared to low redshift ($\langle z\rangle=0.137$) sdss (cite: York:00)/boss (cite: Eisenstein:11) data. No selection is made in redshift hence the mean redshift is a survey selection effect. The measured line strengths are taken from the catalogue of emission line properties from (cite: Thomas2013)[^6]. We restrict this comparison to galaxies with \[OIII\] and \[NeIII\] detected at $\ge 2.5\sigma$ and \[NeII\] detected at $\ge 2\sigma$. The uncertainties on the flux ratios are smaller than the hexagonal bins. No selection is made for galaxy type and this sample includes both AGN and star-forming galaxies as selected by the (cite: Baldwin:81) criteria. We applied no reddening correction as all three lines are close in wavelength and hence their ratios are minimally affected by dust absorption. We also examine the parameter space of the emission line ratios from llagn modelled by (cite: Groves:06). Finally, we compare the line ratios to those predicted from the MAPPINGS III library of fast radiative shock models (cite: Allen:08). We plot the radiative shock and photoionised precursor (sp) models and the simpler shock (s) or precursor (p) only models for a low, smc-like metallicity (comparable to the metallicity estimates from the beagle fit §[3.3.1](#sec:res:beagle)) although the general result holds for nearly all metallicity templates.

GLEAM ­J0917­$-$0012 lies in a region of parameter space below and to the left of the bulk of the sdss sources, clearly due to the strong \[NeIII\] line, but to the right of the llagn parameter space. GLEAM ­J0917­$-$0012 is consistent with the sp model from MAPPINGS III. This result is driven by the observed \[OII\]/\[NeIII\] line ratio. The MAPPINGS III models are a function of velocity, magnetic parameters, preshock density and abundances. The range of velocities modelled only reaches up to 1,000 km s$^{-1}$, but the models find that for the sp models, \[NeV\]/\[NeIII\] correlates with velocity and \[NeV\]/\[NeIII\] is consistent with the fastest velocities. Given the uncertainties in the observed line ratios and the overlapping nature of the sp models in this line ratio parameter space, it is not possible to place any constraints on the magnetic parameters, preshock density or abundance. While typical EELR galaxies have \[NeV\]/\[NeIII\] line ratios $>1$ (cite: Fu:09a), which is inconsistent with GLEAM ­J0917­$-$0012, the suggestion that GLEAM ­J0917­$-$0012 is powered by shock emission is consistent with earlier work on compact radio galaxies (cite: Best:00b; DeBreuck:00; Inskip:02b).

Recently, studies of \[NeV\]-selected galaxies (cite: Cleri:23a) have shown that $z\approx 2$ galaxies in CANDELS with G102/G141 WPC3 grism spectra have line ratios similar to the local SDSS galaxies in Fig. [7](#fig:lineratio). (cite: Cleri:23b) has also shown that galaxies observed with the NIRSpec instrument on board *JWST* have line ratios consistent with low-luminosity AGN. Therefore, GLEAM ­J0917­$-$0012 has line ratios different from both these samples, further suggesting a unique physical mechanism compared to the general radio-quiet AGN population.

The presence of the \[NeV\] line suggests an ionisation potential strong enough to ionise helium into He$^{\rm 2+}$. As GLEAM ­J0917­$-$0012 lies at $z\approx 3$, towards the end of the epoch of Helium reionisation, this source, and other compact radio-loud AGN, could be great targets for **observations of potential** absorption by the hyperfine transitions of He$^{\rm 3+}$ (rest-frame frequency of 8.66 GHz) as well as neutral hydrogen. Future spatially resolved, $0.1''$, spectroscopy with *JWST* of the \[NeV\], \[NeIII\] and \[OII\] lines could map out the origin of the photoionisation across and in front of the jet. Observed asymmetry in the Lyman$\alpha$ line could also be used to model line of sight absorption by HI, providing an independent comparison to HI absorption seen in the radio.

## Black Hole Mass and Accretion Rate Constraints

### Bolometric Luminosity

Recently, (cite: Barchiesi:24) has investigated \[NeV\]-selected galaxies at $0.6<z<1.2$ in **the** cosmos (cite: scoville:07). They found a tight correlation between the AGN bolometric luminosity derived from broad-band SED fitting and the luminosity of the \[NeV\] line. Here we use this relation to estimate the AGN bolometric luminosity of GLEAM ­J0917­$-$0012, finding a value of $1.1\pm 0.4\times 10^{12}\,$L$_\odot$ where the uncertainty comes from the uncertainty of the \[NeV\] flux measurement (i.e. does not include any scatter in the relation between AGN bolometric luminosity and \[NeV\] line luminosity). From the wise non-detections presented in S22 we can derive an upper limit to the rest-frame mid-IR luminosity and hence to the AGN bolometric luminosity, $L_{\rm BOL}$. We use the conversion from $3.4\,\mu$m luminosity to bolometric luminosity given in (cite: kim:23). From this we find $L_{\rm BOL}\le 1.7\times 10^{12}\,L_\odot$ (reported in Table [3](#tab:sum_opt)). This value is consistent with the bolometric luminosity derived from the \[NeV\] line luminosity.

The luminosity of the \[NeV\] line is also known to correlate with the unobscured X-ray luminosity (cite: mignoli:13). A typical value for the X-ray to \[NeV\] luminosity ratio, X/\[NeV\], is $\approx 400$ for unobscured Seyferts and QSOs (cite: gilli:10) albeit with an order of magnitude scatter. We estimate an unobscured X-ray luminosity of $L_{\rm X}^{\rm [NeV]}\approx 1.2\times 10^{44}\,$erg s$^{-1}$. This result is consistent with the X-ray luminosity upper limit inferred from eROSITA ($L_{\rm X}<1.7\times 10^{44}\,$erg s$^{-1}$ assuming a photon index of $\Gamma=1.8$) although compact radio sources typically show large absorbing column densities, $N_{\rm H}\approx 10^{21}$-$10^{24}\,$cm$^{-2}$ (cite: Sobolewska:19).

### Black Hole Mass and Eddington Accretion

Assuming that the \[NeV\] bolometric luminosity is an approximation of the true value, we can determine rough constraints on the black hole mass and accretion rate by using the jet power calculated in §[3.4](#sec:res:jet). We use analytical solutions to the (cite: Blandford:77), hereafter BZ, model to express the jet power as function of black hole mass, $M_{\rm BH}$, Eddington accretion rate, $\dot{m}$ and the dimensionless black hole spin parameter, $a$ (cite: Kerr:63). This dimensionless spin parameter is limited to $-1<a<1$ with a negative value corresponding to retrograde spin of the accretion disk relative to the black hole **spin**. The spin paradigm of the BZ model, where the magnetic fields thread the black hole, posits that the energy of the jet comes from the angular momentum of the black hole not the accretion. Even if some of the magnetic field threads the accretion disk (cite: Blandford:82), this magnetic field is still a function of the spin as the rotating general relativistic metric of the Kerr black hole ‘frame-drags’ the magnetic field and inner accretion disk (cite: Meier:99).

We follow the formalism for jet power, $Q_{\rm jet}$, developed in (cite: Meier:02) which is used frequently in the literature (cite: Fanidakis:11; amarantidis:19). While (cite: Meier:01) has formulas for the jet power which depend on extra factors, such as the disk viscosity and relative angular momentum, very similar jet powers are estimated for reasonable values of these extra (but unmeasurable) parameters. Hence, we caution that the expressions below are approximations.

As the strength of the jet power is largely determined by the strength of the polaroid magnetic field then it depends on the structure of the accretion disk (cite: Livio:99). Therefore, the expressions used for the jet powers have either a geometrically thin disk (cite: Shakura:73), or the geometrically thick disk (cite: Rees:82):

$$\begin{equation}
        Q_{\rm jet}^{\rm TD}\approx 2.5\times 10^{36}\bigg(\frac{M_{\rm BH}}{\rm 10^9\,M_\odot}\bigg)^{1.1}\,\bigg(\frac{\dot{m}}{0.01}\bigg)^{1.2} \times a^2~~{\rm (W)} 
        \label{eq:jet_td}
\end{equation}$$ $$\begin{equation}
   Q_{\rm jet}^{\rm ADAF}\approx 2\times 10^{38}\bigg(\frac{M_{\rm BH}}{\rm 10^9\,M_\odot}\bigg)\,\bigg(\frac{\dot{m}}{0.01}\bigg) \times a^2~~{\rm (W).} 
        \label{eq:jet_adaf}
\end{equation}$$

Typically accretion disks are believed to transition from an ADAF to a TD as $\dot{m}$ increases through 0.01-0.03 (cite: vm:19).

We do not have a constraint on $\dot{m}$ or $M_{\rm BH}$ for GLEAM ­J0917­$-$0012, but we have a joint constraint on the black hole mass and $\dot{m}$ from the bolometric luminosity (from the definition of the Eddington accretion rate: $\dot{m}=L_{\rm BOL}/(k\times M)$ where $k$ depends on the units used). Using the estimate of the bolometric luminosity **derived in §[4.4.1](#sec:dis:bol)** from the \[NeV\] line ($\approx 1.1\pm 0.4\times 10^{12}\,$L$_\odot$) we get:

$$\begin{equation}
    \bigg(\frac{M_{\rm BH}}{\rm 10^9\,M_\odot}\bigg)\,\bigg(\frac{\dot{m}}{0.01}\bigg) \approx 3.2\pm 1.2
\end{equation}$$

Reconciling this result and the high jet power, $\sim 1.5\times 10^{39}\,$W (from §[3.4](#sec:res:jet)), with equations [\[eq:jet_td\]](#eq:jet_td) and [\[eq:jet_adaf\]](#eq:jet_adaf) implies values of $a^2\gg1$. However, the dimensionless black hole spin parameter is limited to $\le 1$ for the (cite: Kerr:63) solution for black holes, hence our observations are not consistent with equation [\[eq:jet_td\]](#eq:jet_td). In the ADAF case (equation [\[eq:jet_adaf\]](#eq:jet_adaf)) it would imply $a^2\approx 2.1$, i.e. only just above unity. Therefore, allowing for the uncertainties on the jet power and/or the bolometric luminosity, this result could be consistent with the ADAF solution, i.e. realistic values of $a\lesssim 1$ could be achieved, but not the TD solution. While the \[NeV\] constrain on the bolometric luminosity has some uncertainty, the upper limit from the *WISE* non-detection, $<1.7\times 10^{12}\,$L$_\odot$, is more robust and equally well supports the conclusions above. The conclusion that the accretion disk is in ADAF and not a thin disk state is consistent with the interpretation from §[3.1.2](#sec:res:hst:spec) that GLEAM ­J0917­$-$0012 is a LERG and not a HERG. Even using the equations from (cite: Meier:01) we find the only consistent solution is the ADAF one.

The inference that the BH has an ADAF disk at first may seem inconsistent with high-excitation state inferred by the \[OII\] luminosity (see §[3.1.2](#sec:res:hst:spec)). However, the \[OII\] luminosity has an unknown contribution from star formation as the SFR derived from SED fitting provides a poor constraint (see §[3.3.1](#sec:res:beagle)). Furthermore, in radio-loud AGN it has been shown that \[OII\] is predominantly due to some combination of star-formation, EELR and shocks (cite: Maddox:18), not the broad or narrow line region, hence is not a good indicator that an AGN has a high enough accretion rate to be in TD state.

If the accretion disk is in an ADAF mode with then we can very tentatively constrain the black hole mass assuming a maximum Eddington accretion of $\dot{m}\le 0.03$. With this value we obtain a constraint on the black hole mass of $\ge 10^9\,$M$_\odot$. In this case the black hole mass would be more than an order of magnitude above the local black hole mass/host galaxy relation of (cite: Reines:15) relation for local AGN hosts (which would predict a black hole mass of just $\approx 6\times 10^7\,$M$_\odot$). However, it is consistent with the (cite: Reines:15) relation for local massive ellipticals which are believed to be the local descendants of powerful HzRGs (cite: Seymour:07; DeBreuck:10). If the \[NeV\] bolometric AGN luminosity is over-estimated, then the inconsistency with both disk models increases. Hence, the very high jet power of GLEAM ­J0917­$-$0012 implies that it likely has a high-spin, massive black hole, $\ge 10^9\,$M$_\odot$ with an ADAF accretion disk, and $\approx 10^{12}\,$L$_\odot$ bolometric luminosity.

## Future Evolution of GLEAM ­J0917­$-$0012

The compact nature and spectral properties of GLEAM J0917-0012 suggest that it might be in an early stage of radio galaxy evolution, likely classified as a MPS source or a redshifted GPS source. As GPS sources are thought to represent the progenitors of large-scale radio galaxies (cite: odea:98; orienti:16) the proposed evolutionary scenario (cite: fanti:95; An:12) suggests that these radio sources expand into their host galaxies, interacting strongly with the interstellar medium. We cannot determine if GLEAM ­J0917­$-$0012 will (a) keep growing from GPS to CSS to extended radio galaxy, (b) shut off and stop expanding, or (c) become "frustrated" by a dense medium (cite: vanBreugal:84; kawakatu:09). We can say that the observed jet-induced shocks and extended \[OII\] emission in GLEAM ­J0917­$-$0012 are consistent with the picture of ongoing interaction with the host galaxy (cite: Bicknell:18).

The high black hole mass, $\ge 10^9\,$M$_\odot$, combined with the low accretion rate, has significant implications for galaxy evolution models. Observed at roughly 2 Gyr after the Big Bang, this system coincides with the peak of cosmic star formation and AGN activity (cite: madau:14). The black hole’s mass indicates significant early growth (cite: McAlpine:18) which has now slowed and the accretion disk is in a LERG state. However, even with low accretion rate, a high black hole spin is enough to produce powerful radio jets which appear to be impacting the host galaxy via shocks and potentially strong outflows.

The host galaxy’s SFR (and hence sSFR) is poorly constrained, but we can say with confidence that it is below the main sequence for star-forming galaxies at this redshift (see §[4.1](#sec:dis:host)). Could the radio jets be quenching the star-formation? Deep narrow surveys are finding many quenched massive galaxies in the early Universe (cite: Carnall:23). The power of the jet reported here is more than enough to quench star-formation. If the on-time of these powerful jets is short enough, $<100\,$ky, (i.e. a low radio duty cycle where they rarely grow into large radio galaxies) then they could be too rare to be seen in the deep pencil-beam *JSWT* surveys.

Hence, this source potentially demonstrates how AGN feedback might regulate growth and star formation in this critical epoch (cite: Harrison:17). The source’s high redshift provides a valuable opportunity to study this evolutionary process in the early Universe. Future observations to constrain the star formation history (e.g. is the SFR declining?) and to map out the ionisation state in and around the jet will better constrain feedback.

# CONCLUSIONS

This paper confirms the redshift of the enigmatic radio source GLEAM ­J0917­$-$0012 which, due to its compact size and faint $K$-band host, was originally suspected to be $z\ge 6$, but is now revealed to be a young and compact radio galaxy at cosmic noon. The main results of this work are:

1.  The 1D WFC3 spectrum detects the \[OII\]$\lambda$3727 doublet as well as the \[NeV\]$\lambda$3426 and \[NeIII\]$\lambda$3867 emission lines, confirming the redshift to be $z=3.004\pm 0.001$. The 2D spectrum shows extended \[OII\] emission ($\approx 4.8\,$kpc) aligned with the two components seen in the high resolution ($60\times 20$ mas) LBA imaging at 2.276 GHz.

2.  The detection of Neon lines suggest the presence of an AGN powered extended emission line region as seen in many other radio galaxies. However, the scale of this region in GLEAM ­J0917­$-$0012 is smaller than the typical $\geq 10\,$kpc scales.

3.  The nearby optical source is found to be at $z=2.13$ and is hence unrelated to GLEAM ­J0917­$-$0012 despite its chance alignment with the radio jets.

4.  SED fitting with `BEAGLE` finds a stellar mass of $\approx 2\times 10^{11}\,$M$_\odot$, making GLEAM ­J0917­$-$0012 lie at the low end of the 500 MHz luminosity, $L_{\rm 500MHz}$, and stellar mass distribution of the most extreme radio galaxies at similar redshifts. It has a similar projected size ($<10\,$kpc) and $L_{\rm 500MHz}$ to just one other classic HzRG: WN J1115$+$5016.

5.  The extended component of the \[OII\] line in GLEAM ­J0917­$-$0012 is reminiscent of the jet-cloud interactions observed in local 3C CSS sources.

6.  Modelling of the radio emission with `RAiSE` along with constraints on the galaxy size from the F140W image provides measures of the jet power and age of this radio source. Unsurprising, this source is young, $\approx 50\,$kyr with high jet power of $\approx 10^{39}\,$W.

7.  The crude constraint on the bolometric luminosity, $\approx 10^{12}\,$L$_\odot$, combined with the estimate of the radio jet power tentatively implies a highly spinning central black hole in an ADAF state with a relatively low accretion rate ($\lambda_{\rm EDD}\le 0.03$) and a high mass, $\ge 10^{9}\,$M$_\odot$. This result is consistent with LERG classification of this radio galaxy based on its \[OII\] and radio luminosity.

8.  The \[NeV\]$\lambda$3426/\[NeIII\]$\lambda$3867 vs \[OII\]$\lambda$3727/\[NeIII\]$\lambda$3867 line ratios are most consistent with radiative shock models with precursor photoionisation. Hence, GLEAM ­J0917­$-$0012 is a young radio galaxy with compact jet inducing shock ionisation.

We summarise that GLEAM ­J0917­$-$0012 is a prime example of a young radio galaxy interacting via shocks in the ISM of its host galaxy as demonstrated by the close alignment of the radio jet and \[OII\] emission as well as modelling of the emission line ratios. Potentially GLEAM ­J0917­$-$0012 is on the way to having its star-formation quenched. If the jet is short-lived then this mechanism could account for the numerous quenched massive galaxies seen in the narrow deep surveys. Such a source is a prime target for a plethora of follow-up observations investigating the nature of interaction of the jet with the host galaxy. Observations of other extreme radio to $K$-band flux ratio sources with low-frequency spectral curvature (cite: Broderick:24) could provide numerous more candidates for vigorous mechanical feedback at cosmic noon.

The authors acknowledge the Noongar people as the traditional owners and custodians of Whadjuk boodjar, the land on which the majority of this work was completed. NS thanks Brent Groves and Mara Salvato for useful discussions. We thank the reviewer for their very useful and constructive comments on the paper.

The work of DS was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA.

This research is based on observations made with the NASA/ESA *Hubble Space Telescope* obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with programs 16184 and 16662. TA acknowledges the grant support through National SKA Program of China (2022SKA0120102)

This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

The Long Baseline Array is part of the Australia Telescope National Facility (<https://ror.org/05qajvd42>) which is funded by the Australian Government for operation as a National Facility managed by CSIRO. This work was supported by resources provided by the Pawsey Supercomputing Centre with funding from the Australian Government and the Government of Western Australia.

The Hyper Suprime-Cam (HSC) collaboration includes the astronomical communities of Japan and Taiwan, and Princeton University. The HSC instrumentation and software were developed by the National Astronomical Observatory of Japan (NAOJ), the Kavli Institute for the Physics and Mathematics of the Universe (Kavli IPMU), the University of Tokyo, the High Energy Accelerator Research Organization (KEK), the Academia Sinica Institute for Astronomy and Astrophysics in Taiwan (ASIAA), and Princeton University. Funding was contributed by the FIRST program from the Japanese Cabinet Office, the Ministry of Education, Culture, Sports, Science and Technology (MEXT), the Japan Society for the Promotion of Science (JSPS), Japan Science and Technology Agency (JST), the Toray Science Foundation, NAOJ, Kavli IPMU, KEK, ASIAA, and Princeton University.

This paper is based \[in part\] on data collected at the Subaru Telescope and retrieved from the HSC data archive system, which is operated by the Subaru Telescope and Astronomy Data Center (ADC) at National Astronomical Observatory of Japan. Data analysis was in part carried out with the cooperation of Center for Computational Astrophysics (CfCA), National Astronomical Observatory of Japan. The Subaru Telescope is honored and grateful for the opportunity of observing the Universe from Maunakea, which has the cultural, historical and natural significance in Hawaii.

This research made use of Astropy[^7] a community-developed core Python package for Astronomy (cite: astropy:2013; astropy:2018). This research made use of Photutils, an Astropy package for detection and photometry of astronomical sources (cite: Bradley:24). This research made use of PetroFit (cite: Geda:22), a package based on Photutils, for calculating Petrosian properties and fitting galaxy light profiles.

This research made use of ds9, a tool for data visualization supported by the Chandra X-ray Science Center (CXC) and the High Energy Astrophysics Science Archive Center (HEASARC) with support from the JWST Mission office at the Space Telescope Science Institute for 3D visualization.

natexlab

(ref: Aihara:22) Aihara, H., AlSayyad, Y., Ando, M., et al. 2022, PASJ, 74, 247

(ref: Allen:08) Allen, M. G., Groves, B. A., Dopita, M. A., Sutherland, R. S., & Kewley, L. J. 2008, ApJS, 178, 20

(ref: amarantidis:19) Amarantidis, S., Afonso, J., Messias, H., et al. 2019, MNRAS, 485, 2694

(ref: An:12) An, T., & Baan, W. A. 2012, ApJ, 760, 77

(ref: An:10) An, T., Hong, X. Y., Hardcastle, M. J., et al. 2010, MNRAS, 402, 87

(ref: An:13) An, T., Paragi, Z., Frey, S., et al. 2013, MNRAS, 433, 1161

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Axon:08) Axon, D. J., Capetti, A., Fanti, R., et al. 2000, AJ, 120, 2284

(ref: Banados:21) Bañados, E., Mazzucchelli, C., Momjian, E., et al. 2021, ApJ, 909, 80

(ref: Baldwin:81) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5

(ref: Barbary:16) Barbary, K., Boone, K., McCully, C., et al. 2016, kbarbary/sep: v1.0.0, doi:[10.5281/zenodo.159035](10.5281/zenodo.159035)

(ref: Barchiesi:24) Barchiesi, L., Vignali, C., Pozzi, F., et al. 2024, A&A, 685, A141

(ref: Bertin:02) Bertin, E., Mellier, Y., Radovich, M., et al. 2002, in Astronomical Society of the Pacific Conference Series, Vol. 281, Astronomical Data Analysis Software and Systems XI, ed. D. A. Bohlender, D. Durand, & T. H. Handley, 228

(ref: Best:00b) Best, P. N., Röttgering, H. J. A., & Longair, M. S. 2000, MNRAS, 311, 23

(ref: Bicknell:18) Bicknell, G. V., Mukherjee, D., Wagner, A. Y., Sutherland, R. S., & Nesvadba, N. P. H. 2018, MNRAS, 475, 3493

(ref: Blandford:82) Blandford, R., & Payne, D. 1982, 199, 883

(ref: Blandford:77) Blandford, R. D., & Znajek, R. L. 1977, MNRAS, 179, 433

(ref: Bower:06) Bower, R. G., Benson, A. J., Malbon, R., et al. 2006, MNRAS, 370, 645

(ref: Bradley:24) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2024, astropy/photutils: 1.12.0, doi:[10.5281/zenodo.10967176](10.5281/zenodo.10967176)

(ref: Brammer:19) Brammer, G. 2019, Grizli: Grism redshift and line analysis software, ascl:1905.001

(ref: Broderick:22) Broderick, J. W., Drouart, G., Seymour, N., et al. 2022, PASA, 39, e061

(ref: Broderick:24) Broderick, J. W., Seymour, N., Drouart, G., et al. 2024, arXiv e-prints, arXiv:2407.19145

(ref: Brunner:22) Brunner, H., Liu, T., Lamer, G., et al. 2022, A&A, 661, A1

(ref: Buttiglione:10) Buttiglione, S., Capetti, A., Celotti, A., et al. 2010, A&A, 509, A6

(ref: Callingham:17) Callingham, J. R., Ekers, R. D., Gaensler, B. M., et al. 2017, ApJ, 836, 174

(ref: Calzetti:97) Calzetti, D. 1997, AJ, 113, 162

(ref: Carnall:23) Carnall, A. C., et al. 2023, MNRAS, 520, 3974

(ref: Chevallard:16) Chevallard, J., & Charlot, S. 2016, MNRAS, 462, 1415

(ref: Chhetri:18) Chhetri, R., Morgan, J., Ekers, R. D., et al. 2018, MNRAS, 474, 4937

(ref: Cleri:23a) Cleri, N. J., Yang, G., Papovich, C., et al. 2023a, ApJ, 948, 112

(ref: Cleri:23b) Cleri, N. J., Olivier, G. M., Hutchison, T. A., et al. 2023b, ApJ, 953, 10

(ref: Condon:98) Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693

(ref: Coppejans:15) Coppejans, R., Cseh, D., Williams, W. L., van Velzen, S., & Falcke, H. 2015, MNRAS, 450, 1477

(ref: Croton:06) Croton, D. J., et al. 2006, MNRAS, 365, 11

(ref: DeBreuck:01) De Breuck, C., van Breugel, W., Stanford, S. A., et al. 2001, 1754, 637

(ref: DeBreuck:00) De Breuck, C., van Breugel, W., Röttgering, H., et al. 2000, 121, 1241

(ref: DeBreuck:10) De Breuck, C., Seymour, N., Stern, D., et al. 2010, ApJ, 725, 36

(ref: devries:97) de Vries, W. H., O’Dea, C. P., Baum, S. A., et al. 1997, ApJS, 110, 191

(ref: deller11) Deller, A. T., Brisken, W. F., Phillips, C. J., et al. 2011, PASP, 123, 275

(ref: driver:11) Driver, S. P., Hill, D. T., Kelvin, L. S., et al. 2011, MNRAS, 413, 971

(ref: Drouart:16) Drouart, G., Rocca-Volmerange, B., De Breuck, C., et al. 2016, A&A, 593, A109

(ref: Drouart:20) Drouart, G., Seymour, N., Galvin, T. J., et al. 2020, PASA, 37, e026

(ref: Drouart:21) Drouart, G., Seymour, N., Broderick, J. W., et al. 2021, PASA, 38, e049

(ref: Edge:13) Edge, A., Sutherland, W., Kuijken, K., et al. 2013, The Messenger, 154, 32

(ref: Eisenstein:11) Eisenstein, D. J., Weinberg, D. H., Agol, E., et al. 2011, AJ, 142, 72

(ref: Emonts:14) Emonts, B. H. C., Norris, R. P., Feain, I., et al. 2014, MNRAS, 438, 2898

(ref: emonts:23) Emonts, B. H. C., Lehnert, M. D., Lebowitz, S., et al. 2023, ApJ, 952, 148

(ref: Endsley:22) Endsley, R., Stark, D. P., Fan, X., et al. 2022, MNRAS, 512, 4248

(ref: fr:74) Fanaroff, B. L., & Riley, J. M. 1974, Monthly Notices of the Royal Astronomical Society, 167, 31P

(ref: Fanidakis:11) Fanidakis, N., Baugh, C. M., Benson, A. J., et al. 2011, MNRAS, 410, 53

(ref: fanti:95) Fanti, C., Fanti, R., Dallacasa, D., et al. 1995, A&A, 302, 317

(ref: Klamer:09) Feain, I. J., Ekers, R. D., Murphy, T., et al. 2009, ApJ, 707, 114

(ref: Frater:92) Frater, R. H., Brooks, J. W., & Whiteoak, J. B. 1992, Journal of Electrical and Electronics Engineering Australia, 12, 103

(ref: Fu:06) Fu, H., & Stockton, A. 2006, ApJ, 650, 80

(ref: Fu:09a) —. 2009a, ApJ, 690, 953

(ref: Fu:09b) —. 2009b, ApJ, 696, 1693

(ref: Klioner:22) Gaia Collaboration, Klioner, et al. 2022, A&A, 667, A148

(ref: Gaia:23) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Geda:22) Geda, R., Crawford, S. M., Hunt, L., et al. 2022, The Astronomical Journal, 163, 202

(ref: gilli:10) Gilli, R., Vignali, C., Mignoli, M., et al. 2010, A&A, 519, A92

(ref: Gitti:11) Gitti, M., Brighenti, F., & McNamara, B. 2011, Advances in Astronomy, 2012, doi:[10.1155/2012/950641](10.1155/2012/950641)

(ref: Gloudemans:22) Gloudemans, A. J., Duncan, K. J., Saxena, A., et al. 2022, A&A, 668, A27

(ref: Gopal-Krishna:83) Gopal-Krishna, Patnaik, A. R., & Steppe, H. 1983, A&A, 123, 107

(ref: Groves:06) Groves, B. A., Heckman, T. M., & Kauffmann, G. 2006, MNRAS, 371, 1559

(ref: Gullberg:16) Gullberg, B., Lehnert, M. D., De Breuck, C., et al. 2016, A&A, 591, A73

(ref: Harrison:17) Harrison, C. M. 2017, Nature Astronomy, 1, 0165

(ref: Hines:1979) Hine, R. G., & Longair, M. S. 1979, MNRAS, 188, 111

(ref: Ighina:22) Ighina, L., Leung, J. K., Broderick, J. W., et al. 2022, A&A, 663, A73

(ref: Inskip:02b) Inskip, K. J., Best, P. N., Rawlings, S., et al. 2002, MNRAS, 337, 1381

(ref: Intema:17) Intema, H. T., Jagannathan, P., Mooley, K. P., & Frail, D. A. 2017, A&A, 598, A78

(ref: kawakatu:09) Kawakatu, N., Kino, M., & Nagai, H. 2009, ApJL, 697, L173

(ref: Kennicutt:92) Kennicutt, R. C. 1992, 388, 310

(ref: Kennicutt:98) —. 1998, 36, 189

(ref: Kerr:63) Kerr, R. P. 1963, Phys. Rev. Lett., 11, 237

(ref: 2006ASPC..351..497K) Kettenis, M., van Langevelde, H. J., Reynolds, C., & Cotton, B. 2006, in Astronomical Society of the Pacific Conference Series, Vol. 351, Astronomical Data Analysis Software and Systems XV, ed. C. Gabriel, C. Arviset, D. Ponz, & S. Enrique, 497

(ref: kewley:04) Kewley, L. J., Geller, M. J., & Jansen, R. A. 2004, AJ, 127, 2002

(ref: kim:23) Kim, D., Im, M., Kim, M., et al. 2023, ApJ, 954, 156

(ref: klamer:04) Klamer, I. J., Ekers, R. D., Sadler, E. M., & Hunstead, R. W. 2004, ApJL, 612, L97

(ref: Koprowski:24) Koprowski, M. P., Wijesekera, J. V., Dunlop, J. S., et al. 2024, arXiv e-prints, arXiv:2403.06575

(ref: kb:14) Kunert-Bajraszewska, M., Labiano, A., Siemiginowska, A., & Guainazzi, M. 2014, MNRAS, 437, 3063

(ref: Livio:99) Livio, M., Ogilvie, G. I., & Pringle, J. E. 1999, ApJ, 512, 100

(ref: madau:14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Maddox:18) Maddox, N. 2018, MNRAS, 480, 5203

(ref: 2016A&A...587A.143M) Martı́-Vidal, I., Roy, A., Conway, J., & Zensus, A. J. 2016, A&A, 587, A143

(ref: Massaro:09) Massaro, F., Chiaberge, M., Grandi, P., et al. 2009, ApJL, 692, L123

(ref: McAlpine:18) McAlpine, S., Bower, R. G., Rosario, D. J., et al. 2018, MNRAS, 481, 3118

(ref: Meier:99) Meier, D. L. 1999, ApJ, 522, 753

(ref: Meier:01) —. 2001, ApJL, 548, L9

(ref: Meier:02) —. 2002, New Astronomy Reviews, 46, 247

(ref: mignoli:13) Mignoli, M., Vignali, C., Gilli, R., et al. 2013, A&A, 556, A29

(ref: Miley:08) Miley, G., & De Breuck, C. 2008, A&ARv, 15, 67

(ref: Miller:19) Miller, T. B., van Dokkum, P., Mowla, L., & van der Wel, A. 2019, ApJL, 872, L14

(ref: Morabito:18) Morabito, L. K., & Harwood, J. J. 2018, MNRAS, 480, 2726

(ref: Morgan:18) Morgan, J. S., Macquart, J. P., Ekers, R., et al. 2018, MNRAS, 473, 2965

(ref: Mowla:19) Mowla, L., van der Wel, A., van Dokkum, P., & Miller, T. B. 2019, ApJL, 872, L13

(ref: murgia:99) Murgia, M., Fanti, C., Fanti, R., et al. 1999, A&A, 345, 769

(ref: Nesvadba:20) Nesvadba, N. P. H., Bicknell, G. V., Mukherjee, D., & Wagner, A. Y. 2020, A&A, 639, L13

(ref: Nesvadba:17) Nesvadba, N. P. H., Drouart, G., De Breuck, C., et al. 2017, A&A, 600, A121

(ref: odea:98) O’Dea, C. P. 1998, PASP, 110, 493

(ref: odea:97) O’Dea, C. P., & Baum, S. A. 1997, AJ, 113, 148

(ref: odea:21) O’Dea, C. P., & Saikia, D. J. 2021, A&ARv, 29, 3

(ref: Oke:83) Oke, J. B., & Gunn, J. E. 1983, 266, 713

(ref: orienti:16) Orienti, M. 2016, Astronomische Nachrichten, 337, 9

(ref: Peacock:82) Peacock, J. A., & Wall, J. V. 1982, MNRAS, 198, 843

(ref: Pentericci:99) Pentericci, L., Röttgering, H. J. A., Miley, G. K., et al. 1999, A&A, 341, 329

(ref: Pilkington:65) Pilkington, J. D. H., & Scott, J. F. 1965, , 69, 183

(ref: Predehl:21) Predehl, P., Andritschke, R., Arefiev, V., et al. 2021, A&A, 647, A1

(ref: Quici:24) Quici, B., Turner, R. J., Seymour, N., & Hurley-Walker, N. 2024, arXiv e-prints, arXiv:2405.11777

(ref: Rees:82) Rees, M. J., Begelman, M. C., Blandford, R. D., & Phinney, E. S. 1982, Nature, 295, 17

(ref: Reines:15) Reines, A. E., & Volonteri, M. 2015, ApJ, 813, 82

(ref: Rengelink:97) Rengelink, R. B., Tang, Y., de Bruyn, A. G., et al. 1997, A&AS, 124, 259

(ref: Ross:22) Ross, K., Hurley-Walker, N., Seymour, N., et al. 2022, MNRAS, 512, 5358

(ref: Saika:95) Saikia, D. J., Jeyakumar, S., Wiita, P. J., Sanghera, H. S., & Spencer, R. E. 1995, MNRAS, 276, 1215

(ref: Saxena:18b) Saxena, A., Marinello, M., Overzier, R. A., et al. 2018, MNRAS, 480, 2733

(ref: scoville:07) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1

(ref: Sersic:68) Sérsic, J. L. 1968, *Atlas de Galaxias Australes* (Cordoba, Argentina: Observatorio Astronomico)

(ref: Seymour:07) Seymour, N., et al. 2007, ApJS, 171, 353

(ref: Seymour:22) Seymour, N., Drouart, G., Noirot, G., et al. 2022, PASA, 39, e016

(ref: Shakura:73) Shakura, N. I., & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: Shih:13) Shih, H.-Y., Stockton, A., & Kewley, L. 2013, ApJ, 772, 138

(ref: Shimwell:17) Shimwell, T. W., Röttgering, H. J. A., Best, P. N., et al. 2017, A&A, 598, A104

(ref: Sobolewska:19) Sobolewska, M., Siemiginowska, A., Guainazzi, M., et al. 2019, ApJ, 871, 71

(ref: Spinrad:84) Spinrad, H., & Djorgovski, S. 1984, 285, L49

(ref: Stevens:03) Stevens, J. A., Ivison, R. J., Dunlop, J. S., et al. 2003, Nature, 425, 264

(ref: Stockton:07) Stockton, A., Canalizo, G., Fu, H., & Keel, W. 2007, ApJ, 659, 195

(ref: sunyaev:21) Sunyaev, R., Arefiev, V., Babyshkin, V., et al. 2021, A&A, 656, A132

(ref: Swarup:91) Swarup, G., Ananthakrishnan, S., Kapahi, V. K., et al. 1991, Current Science, 60, 95

(ref: casa:22) Team, T. C., Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501

(ref: Thomas2013) Thomas, D., Steele, O., Maraston, C., et al. 2013, MNRAS, 431, 1383

(ref: Tingay:13) Tingay, S. J., Goeke, R., Bowman, J. D., et al. 2013, PASA, 30, e007

(ref: Turner:15) Turner, R. J., & Shabala, S. S. 2015, ApJ, 806, 59

(ref: Turner:18b) Turner, R. J., Shabala, S. S., & Krause, M. G. H. 2018, MNRAS, 474, 3361

(ref: Turner_2023) Turner, R. J., Yates-Jones, P. M., Shabala, S. S., Quici, B., & Stewart, G. S. C. 2023, MNRAS, 518, 945

(ref: vm:19) Vahdat Motlagh, A., Kalemci, E., & Maccarone, T. J. 2019, Monthly Notices of the Royal Astronomical Society, 485, 2744

(ref: vanBreugal:84) van Breugel, W., Miley, G., & Heckman, T. 1984, AJ, 89, 5

(ref: Vanderwel:14) van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28

(ref: VanHaarlem:13) van Haarlem, M. P., Wise, M. W., Gunst, A. W., et al. 2013, A&A, 556, A2

(ref: VillarMartin:11a) Villar-Martı́n, M., Tadhunter, C., Humphrey, A., et al. 2011, MNRAS, 416, 262

(ref: VillarMartin:03) Villar-Martín, M., et al. 2003, 346, 273

(ref: Waldram:96) Waldram, E. M., Yates, J. A., Riley, J. M., & Warner, P. J. 1996, MNRAS, 282, 779

(ref: Wayth:15) Wayth, R. B., Lenc, E., Bell, M. E., et al. 2015, PASA, 32, e025

(ref: Wright:10) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: Wylezalek:13) Wylezalek, D., Galametz, A., Stern, D., et al. 2013, ApJ, 769, 79

(ref: York:00) York, D. G., et al. 2000, 120, 1579

[^1]: <https://hst-docs.stsci.edu/drizzpac>

[^2]: [www.aips.nrao.edu](www.aips.nrao.edu)

[^3]: [hsc-release.mtk.nao.ac.jp/doc/](hsc-release.mtk.nao.ac.jp/doc/)

[^4]: [www.iap.fr/beagle/](www.iap.fr/beagle/)

[^5]: <https://www.stsci.edu/hst/instrumentation/wfc3/data-analysis/psf>

[^6]: [www.sdss4.org/dr17/spectro/galaxy_portsmouth](www.sdss4.org/dr17/spectro/galaxy_portsmouth)

[^7]: http://www.astropy.org

</paper>

Write the methods card for this paper.