# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023PASJ...75..311K\sonnetcc\reply.txt

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
 "bibcode": "2023PASJ...75..311K",
 "title": "Galaxy clusters at z ∼ 1 imaged by ALMA with the Sunyaev-Zel'dovich effect",
 "year": 2023,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Kitayama, Tetsu",
 "n_authors": 18,
 "arxiv_id": "2209.09503",
 "doi": "10.1093/pasj/psac110",
 "alma_projects_linked_by_archive": [
  "2018.1.00680.S",
  "2019.1.00673.S"
 ]
}
```

Paper text:
<paper>
# Galaxy clusters at ${\bm z \sim 1}$ imaged by ALMA with the Sunyaev-Zel’dovich effect

## Abstract

We present high angular-resolution measurements of the thermal Sunyaev-Zel’dovich effect (SZE) toward two galaxy clusters, RCS J2319$+$0038 at $z=0.9$ and HSC J0947$-$0119 at $z=1.1$, by the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 3. They are supplemented with available *Chandra* X-ray data, optical data taken by Hyper Suprime-Cam on Subaru, and millimeter-wave SZE data from the Atacama Cosmology Telescope. Taking into account departures from spherical symmetry, we have reconstructed non-parametrically the inner pressure profile of two clusters as well as electron temperature and density profiles for RCS J2319$+$0038. This is one of the first such measurements for an individual cluster at $z
  \gtsim 0.9$. We find that the inner pressure profile of both clusters is much shallower than that of local cool-core clusters. Our results consistently suggest that RCS J2319$+$0038 hosts a weak cool core, where radiative cooling is less significant than in local cool cores. On the other hand, HSC J0947$-$0119 exhibits an even shallower pressure profile than RCS J2319$+$0038 and is more likely a non-cool-core cluster. The SZE centroid position is offset by more than 140 $h_{70}^{-1}$kpc from the peaks of galaxy distribution in HSC J0947$-$0119, suggesting a stronger influence of mergers in this cluster. We conclude that these distant clusters are at a very early stage of developing the cool cores typically found in clusters at lower redshifts.

Department of Physics, Toho University, Funabashi, Chiba 274-8510, Japan Academia Sinica Institute of Astronomy and Astrophysics (ASIAA), No. 1, Section 4, Roosevelt Road, Taipei 10617, Taiwan Institute of Astronomy, National Tsing Hua University, Hsinchu 30013, Taiwan Department of Physics, Hiroshima University, 1-3-1 Kagamiyama, Higashi-Hiroshima, Hiroshima 739-8526, Japan Astrophysical Science Center, Hiroshima University, 1-3-1 Kagamiyama, Higashi-Hiroshima, Hiroshima 739-8526, Japan Core Research for Energetic Universe, Hiroshima University, 1-3-1, Department of Physics, Hiroshima University, 1-3-1 Kagamiyama, Higashi-Hiroshima, Hiroshima 739-8526, Japan Physics Program, Graduate School of Advanced Science and Engineering, Hiroshima University, 1-3-1 Kagamiyama, Higashi-Hiroshima, Hiroshima 739-8526, Japan Mizusawa VLBI observatory, National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan Operation Division, SKA Observatory, Jodrell Bank, Lower Withington, Macclesfield, SK11 9DL, UK Astrophysics Research Centre, University of KwaZulu-Natal, Westville Campus, Durban 4041, South Africa School of Mathematics, Statistics & Computer Science, University of KwaZulu-Natal, Westville Campus, Durban 4041, South Africa Wits Centre for Astrophysics, School of Physics, University of the Witwatersrand, Private Bag 3, 2050, Johannesburg, South Africa Department of Physics and Astronomy, Rutgers, The State University of New Jersey, Piscataway, NJ 08854-8019, USA Department of Physics, Rikkyo University, 3-34-1 Nishi-Ikebukuro, Toshima-ku, Tokyo 171-8501, Japan Institute of Astronomy, School of Science, The University of Tokyo, 2-21-1 Osawa, Mitaka, Tokyo 181-0015, Japan Research Center for the Early Universe, School of Science, The University of Tokyo, 7-3-1 Hongo, Bunkyo, Tokyo 113-0033, Japan Max-Planck-Institut für Astrophysik, Karl-Schwarzschild Str. 1, D-85741 Garching, Germany Kavli Institute for the Physics and Mathematics of the Universe (Kavli IPMU, WPI), The University of Tokyo Institutes for Advanced Study, The University of Tokyo, 5-1-5 Kashiwanoha, Chiba 277-8583, Japan Kobayashi-Maskawa Institute for the Origin of Particles and the Universe (KMI), Nagoya University, Nagoya, 464-8602, Japan Institute for Advanced Research, Nagoya University, Nagoya 464-8601, Japan Division of Particle and Astrophysical Science, Graduate School of Science, Nagoya University, Nagoya 464-8602, Japan Jet Propulsion Laboratory, California Institute of Technology, Pasadena, CA 91109, USA Center for Frontier Science, Chiba University, 1-33 Yayoi-cho, Inage-ku, Chiba 263-8522, Japan Department of Physics, Graduate School of Science, Chiba University, 1-33 Yayoi-Cho, Inage-Ku, Chiba 263-8522, Japan Instituto de Física, Pontificia Universidad Católica de Valparaíso, Casilla 4059, Valparaíso, Chile Department of Physics and Astronomy, Graduate School of Science and Engineering, Kagoshima University, 1-21-35 Korimoto, Kagoshima, Kagoshima 890-0065, Japan Department of Physics, Yamagata University, 1-4-12 Kojirakawa-machi, Yamagata, Yamagata 990-8560, Japan National Radio Astronomy Observatory, P.O. Box O, Socorro, NM, 87801, USA European Southern Observatory (ESO), Karl-Schwarzschild-Strasse 2, Garching 85748, Germany NASA/Goddard Space Flight Center, Greenbelt, MD 20771, USA

# Introduction

The baryonic content of galaxy clusters is dominated by hot ($\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}
10^7$ K) and tenuous ($\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}0.1$ cm$^{-3}$) plasma, referred to as the intracluster medium (ICM). The ICM properties of nearby ($z \lower.5ex\hbox{$\; \buildrel < \over \sim \;$}
0.2$) clusters are well studied thanks to resolved measurements of X-ray surface brightness and temperature profiles from a large number of clusters (see e.g., (cite: Bohringer10; Cavaliere13) for review). Such profiles encode the thermodynamic evolution of clusters driven by mergers, accretion, and AGN feedback on one hand and radiative cooling on the other. It is recognized that there is a wide diversity in the properties of central cores ($\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}100$ kpc), within which cooling and feedback processes play important roles in sculpting their thermodynamic properties. Broadly speaking, galaxy clusters are divided into two groups: “cool-core” and “non-cool-core” clusters (e.g., (cite: Peres98; Bauer05)). The former is also characterized as having peaked or cuspy gas density profiles, whereas the latter often shows clear signs of disturbance.

At $z\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}1$, the observational situation is much less certain. There are only a handful of galaxy clusters whose thermodynamic structure has been studied at these redshifts in X-rays (cite: Santos12; McDonald14b; Tozzi15; Brodwin16; Bartalucci17; Sanders18; Mantz20; Ghirardini21). This is mainly because the observed X-ray surface brightness decreases as $\propto
(1+z)^{-4}$ and the observed sizes of clusters become small (e.g., typical core radius of 100 kpc corresponds to $\sim 12''$ at $z\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}1$, whereas the Half-Energy-Width of *XMM-Newton* is $\sim 15''$). As a result, it is very challenging to measure spatially resolved temperature structures from X-ray spectral analyses. Efforts to measure thermodynamic profiles at high-$z$ often employ stacking methods to obtain average profiles for samples of clusters observed over broad redshift ranges, e.g., $0.6<z<1.2$ (cite: McDonald14b).

In this regard, the Sunyaev-Zel’dovich effect (SZE; (cite: Sunyaev70; Sunyaev72)) serves as a useful probe of distant galaxy clusters (see (cite: Mroczkowski19) for a recent review). For given electron density $n_{\rm e}$ and temperature $T_{\rm e}$, the surface brightness of the SZE is proportional to $n_{\rm e}T_{\rm e}$, whereas that of X-rays varies as $n_{\rm e}^2\Lambda(T_{\rm e})(1+z)^{-4}$, where $\Lambda$ is typically a weak function of $T_{\rm e}$. The SZE brightness is free from the aforementioned $(1+z)^{-4}$ dimming and provides a direct measure of electron thermal pressure. The advent of large-area SZE surveys by the South Pole Telescope (SPT; e.g., (cite: Spt09; Spt10; Spt11; Spt13; Spt15; Huang20)) and the Atacama Cosmology Telescope (ACT; e.g., (cite: Act10; Act11; Act13a; Hilton18; Hilton21)) has significantly increased the number of galaxy clusters detected at $z\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}1$. Resolved SZE images of clusters at $z \lower.5ex\hbox{$\; \buildrel > \over \sim \;$}1$ with an angular resolution of $< 20''$ have been obtained by MUSTANG on Green Bank Telescope (cite: Korngut11; Dicker20; Andreon21), NIKA on the IRAM telescope (cite: Adam15; Adam18), and the Atacama Large Millimeter/submillimeter Array (ALMA) (cite: Basu16; Gobat19; Luca20; Luca21).

In this paper, we present high angular resolution SZE images of galaxy clusters, RCS J2319$+$0038 at $z=0.90$ and HSC J0947$-$0119 at $z=1.11$, taken by ALMA, and supplement them with available X-ray, optical, and wider-field SZE data. Because of their much smaller mass, the SZE signal of RCS J2319$+$0038 and HSC J0947$-$0119 is weaker, by a factor of up to $5$, than that of massive galaxy clusters at lower redshifts studied by ALMA previously, e.g., RX J1347.5–1145 at $z=0.45$ and SPT-CL J2334–4243 at $z=0.60$ (cite: Kitayama16; Kitayama20). The present paper therefore makes use of one of the deepest ALMA SZE data obtained so far. Our goal is to reveal thermodynamic structures of clusters at $z\sim 1$ in conjunction with galaxy distributions, and weak lensing mass maps. We develop a method to reconstruct electron pressure and temperature profiles of distant clusters non-parametrically, taking into account departures from spherical symmetry. We also include or clarify various systematic effects associated with the analysis.

RCS J2319$+$0038 is the most massive galaxy cluster in a spectroscopically confirmed supercluster at $z \sim 0.9$ (cite: Gilbank08), discovered by the Red-Sequence Cluster Survey (RCS; (cite: Gladders05)). We adopt for this cluster the spectroscopic redshift of $z=0.90$ from (cite: Gilbank08). Based on the X-ray observation with *Chandra* (cite: Hicks08), the density profile of the ICM is well constrained, whereas only the average spectroscopic temperature is measured owing to the large distance to the cluster. More recently, RCS J2319$+$0038 was also detected in the ACT Data Release 5 (DR5; (cite: Naess20)) cluster search[^1] (cite: Hilton21), with signal-to-noise ratio (S/N) of 5.2. We note that the centroid position of the ACT SZE signal is offset from the X-ray peak by $\sim 30''$. We will explore the origin of this offset by means of higher angular resolution SZE data.

HSC J0947$-$0119 was discovered more recently by the Hyper Suprime-Cam Subaru Strategic Program (HSC-SSP; (cite: Miyazaki18; Komiyama18; Furusawa18; Bosch18; Huang18; Coupon18; Tanaka18; Aihara18a; Aihara18b; Aihara19)) using the Cluster finding Algorithm based on Multi-band Identification of Red-sequence gAlaxies (CAMIRA; (cite: Oguri14; Oguri18)). Given the lack of accurate spectroscopic measurements, we adopt for this cluster the photometric redshift[^2] of $z=1.11$ from the CAMIRA catalogue for the third public data release of HSC-SSP [^3]. The accuracy of the photometric redshift in this catalogue is estimated to be $\sigma_z \sim
0.01 (1+z)$ (cite: Oguri18). The observed richness of HSC J0947$-$0119 is one of the highest among the clusters at $z>1$ identified by CAMIRA. HSC J0947$-$0119 is also detected in ACT DR5 with S/N$=13.2$ (cite: Hilton21), which is among the highest significance SZE detection at $z>1$ by ACT. As of this writing, deep X-ray observations for this cluster are unavailable.

Throughout the paper, we adopt a standard set of cosmological density parameters, $\Omega_{\rm
M}=0.3$ and $\Omega_{\rm \Lambda}=0.7$. We use the dimensionless Hubble constant $h_{70}\equiv H_0/(70
\mbox{km/s/Mpc})$; given existing tensions in the value of $H_0$ (e.g., (cite: Verde19)) the parameter is unconstrained unless otherwise indicated. In this cosmology, the angular size of 1$''$ corresponds to the physical sizes of 7.79 $h_{70}^{-1}$kpc and 8.19 $h_{70}^{-1}$kpc at $z=0.90$ and $z=1.11$, respectively. These physical sizes are insensitive to the values of density parameters and reduce by 1.1% and 1.2% at $z=0.90$ and $z=1.11$, respectively, if $\Omega_{\rm M}=0.32$ and $\Omega_{\rm \Lambda}=0.68$ are adopted instead. Unless otherwise stated, the errors are given in 1$\sigma$ and the coordinates are given in J2000.

# Data and analysis

## Millimeter: ALMA Band 3

RCS J2319$+$0038 and HSC J0947$-$0119 were observed by the 12-m and 7-m arrays of ALMA in Band 3 (project codes 2019.1.00673.S and 2018.1.00680.S) as summarized in table [\[tab-obs\]](#tab-obs). The target fields, centered at (, ) and (, ) for RCS J2319$+$0038 and HSC J0947$-$0119, respectively, have diameters of about $1.5'$ covered with 1 central and 6 surrounding hexagonal mosaic pointings by both arrays. An equal spacing of 34.2$''$ between the pointings was adopted, yielding approximately a Nyquist sampling for the 12-m array and much denser sampling for the 7-m array.

The observations were executed over the periods listed in table [\[tab-obs\]](#tab-obs), during which the number of antennas varied slightly. All the data were taken at four continuum bands centered at 85, 87, 97, and 99 GHz, yielding the overall central frequency of 92 GHz ($\lambda=3.3$ mm) with an effective bandwidth of 7.5 GHz. The most compact configuration for the 12m array, C1, was adopted to cover the overall baseline ranges of 2.5–147 k$\lambda$ and 2.5–120 k$\lambda$ for RCS J2319$+$0038 and HSC J0947$-$0119, respectively, where $\lambda$ is the observed wavelength.

+:--------------------------------:+:-----------:+:------------:+:----------:+:----------:+
| Object                           | RCS J2319$+$0038           | HSC J0947$-$0119        |
+----------------------------------+-------------+--------------+------------+------------+
| Array                            | 12-m        | 7-m          | 12-m       | 7-m        |
+----------------------------------+-------------+--------------+------------+------------+
| Project code                     | 2019.1.00673.S             | 2018.1.00680.S          |
+----------------------------------+----------------------------+-------------------------+
| Field center                     | (, )                       | (, )                    |
+----------------------------------+-------------+--------------+------------+------------+
| Number of pointings              | 7           | 7            | 7          | 7          |
+----------------------------------+-------------+--------------+------------+------------+
| Observation Start                | 2019-11-15  | 2019-10-22   | 2019-01-14 | 2018-11-28 |
+----------------------------------+-------------+--------------+------------+------------+
| Observation End                  | 2019-11-22  | 2020-01-02   | 2019-01-20 | 2019-05-13 |
+----------------------------------+-------------+--------------+------------+------------+
| Total on-source time \[hr\]      | 12.1        | 78.6         | 8.0        | 64.5       |
+----------------------------------+-------------+--------------+------------+------------+
| Number of antennas               | $43 - 47$   | $9 - 11$     | $46-51$    | $9-12$     |
+----------------------------------+-------------+--------------+------------+------------+
| Central frequency \[GHz\]        | 92          | 92           | 92         | 92         |
+----------------------------------+-------------+--------------+------------+------------+
| Band widths \[GHz\]              | 7.5         | 7.5          | 7.5        | 7.5        |
+----------------------------------+-------------+--------------+------------+------------+
| Baseline coverage \[k$\lambda$\] | $4.2 - 147$ | $2.5 - 16.3$ | $4.2-120$  | $2.5-16.3$ |
+----------------------------------+-------------+--------------+------------+------------+

+:----------------------------------------:+:---------------:+:------:+:-------:+:-------:+:---------------:+:-------:+:-------:+:-------:+
| Object                                   | RCS J2319$+$0038                             | HSC J0947$-$0119                              |
+------------------------------------------+-----------------+--------+---------+---------+-----------------+---------+---------+---------+
| Array or baseline range                  | $>15$k$\lambda$ | 12-m   | 7-m     | all$^*$ | $>15$k$\lambda$ | 12-m    | 7-m     | all$^*$ |
+------------------------------------------+-----------------+--------+---------+---------+-----------------+---------+---------+---------+
| Beam major axis FWHM \[arcsec\]          | $3.14$          | $3.60$ | $18.7$  | $3.76$  | $3.16$          | $3.63$  | $17.8$  | $3.77$  |
+------------------------------------------+-----------------+--------+---------+---------+-----------------+---------+---------+---------+
| Beam minor axis FWHM \[arcsec\]          | $2.82$          | $3.25$ | $11.9$  | $3.38$  | $2.71$          | $3.11$  | $11.2$  | $3.22$  |
+------------------------------------------+-----------------+--------+---------+---------+-----------------+---------+---------+---------+
| Beam position angle \[deg\]              | $82.2$          | $82.6$ | $-86.1$ | $82.5$  | $-90.0$         | $-89.1$ | $-84.4$ | $-89.1$ |
+------------------------------------------+-----------------+--------+---------+---------+-----------------+---------+---------+---------+
| Average 1$\sigma$ noise \[$\mu$Jy/beam\] | $5.6$           | $5.0$  | $19.4$  | $4.8$   | $5.8$           | $5.1$   | $21.0$  | $5.0$   |
+------------------------------------------+-----------------+--------+---------+---------+-----------------+---------+---------+---------+

$^*$ The 1$\sigma$ noise for all baselines after smoothing to $5''$ FWHM is 5.8 $\mu$Jy/beam and 5.9 $\mu$Jy/beam for RCS J2319$+$0038 and HSC J0947$-$0119, respectively.

For both objects, we used the visibility data produced by the second stage of ALMA’s Quality Assurance process (QA2). Imaging was done with the Common Astronomy Software Applications package (CASA) (cite: McMullin07; CASA2022) version 6.4.0. The procedure was similar to that adopted by (cite: Kitayama16) and (cite: Kitayama20). First, we identified compact sources in the observing field using only the baselines longer than 15k$\lambda$; the position and the flux density were determined in the $uv$ plane by the CASA task *uvmodelfit*. To improve the signal-to-noise ratio, all spectral channels were fitted together[^4], excluding the frequency ranges affected by line emissions; separation of line emissions is described in Appendix [6](#sec-lines).

All the compact sources detected at $>5\sigma$ (tables [\[tab-source1\]](#tab-source1) and [\[tab-source2\]](#tab-source2)) were subtracted from the entire visibility data. Secondly, we performed image deconvolution with the Multi-Scale CLEAN algorithm (cite: Cornwell08; Rich08; Steeb19) using the CASA task *tclean*. Given similar sensitivity and source size between RCS J2319$+$0038 and HSC J0947$-$0119, we adopted a circular mask region with a radius $50''$ and a flux threshold of 0.01 mJy (corresponding to $\sim
2\sigma$) for both objects. The choice of other parameters were identical to (cite: Kitayama20); we adopted \[0, $4''$, $8''$, $16''$, $32''$, $64''$\] as the FWHMs of the Gaussian components, the multi-frequency synthesis mode in joint mosaic imaging, and natural weighting. All the ALMA images presented in this paper are corrected for primary beam attenuation (e.g., (cite: Mason20)) and have the pixel size of $0.5"$.

Table [\[tab-image\]](#tab-image) lists the parameters of the synthesized beams as well as the $1\sigma$ noise levels of the synthesized image within $45''$ from the field center. To eliminate large-scale variation of the data caused by the SZE, the noise levels were measured on difference maps created after subtracting the compact sources (tables [\[tab-source1\]](#tab-source1) and [\[tab-source2\]](#tab-source2)); the visibility data was divided into the first and the second half along the time sequence of observations, the sign of the latter was flipped, concatenated with the former, and the resultant was inverse Fourier transformed into the image domain.

For display purposes, we also present the images smoothed by a Gaussian filter to an effective beam size of $5''$ FWHM. The root-mean-square (RMS) noise level measured on the above mentioned difference map smoothed to the $5''$ resolution is 5.8 $\mu$Jy/beam and 5.9 $\mu$Jy/beam for RCS J2319$+$0038 and HSC J0947$-$0119, respectively. These RMS values are only used for characterizing the significance levels of the SZE signal on the smoothed images. Unless otherwise stated, quantitative analysis in this paper is done on the unsmoothed images created from all baselines whose characteristics are listed in table [\[tab-image\]](#tab-image).

## Millimeter: ACT

We extracted the ACT DR5 data of RCS J2319$+$0038 and HSC J0947$-$0119. The ACT DR5 cluster search used the 98, 150 GHz maps made from all ACT data obtained between 2008 and 2018, including both day and night time observations (see (cite: Naess20) for details of the data products used). The approximate beam FWHMs are $2.2'$ and $1.4'$ at 98 GHz and 150 GHz, respectively. The S/N of the ACT maps presented in this paper is measured at the fixed filter scale of $2.4'$ as described in (cite: Hilton21).

## X-ray: *Chandra* ACIS-S

Of the two clusters studied in this paper, deep X-ray data are available only for RCS J2319$+$0038. We extracted four datasets taken in 2005 by *Chandra* ACIS-S for this cluster (ObsID: 5750, 7172, 7173, and 7174). After excluding the periods with high background rates, the total net exposure time is 69.7 ks. The data were processed with CIAO version 4.13 (cite: Fruscione06) and the Calibration database (CALDB) version 4.9.6. The backgrounds were estimated from the off-center region at $\theta > 3.2'$ from the emission peak of this cluster, where the ICM emission is negligible. Exposure-corrected and background-subtracted data at observed energies $E_{\rm obs} = 0.4- 7.0$ keV were used throughout our analysis; for display purposes only, we applied adaptive smoothing to the brightness image including backgrounds using the task *fadapt* implemented in FTOOLS[^5] (cite: Ftools95; Ftools99; Ftools14). Spectral fitting was done with XSPEC version 12.12.0 (cite: Arnaud96), assuming that the ICM is in collisional ionization equilibrium and the metal abundance $Z$ is 0.3 times the solar value given by (cite: Anders89). The source redshift and the Galactic hydrogen column density were fixed at $z=0.90$ and $N_{\rm H}=4.2\times
 10^{20}$ cm$^{-2}$ (cite: HI4PI16), respectively. We fixed the helium mass fraction at $Y=0.25$, which is nearly unchanged between the primordial gas and the solar photosphere (e.g., (cite: Asplund09; Planck20)).

## Optical: Subaru Hyper Suprime-Cam

RCS J2319$+$0038 and HSC J0947$-$0119 were both observed by five broad-band filters $grizy$ (cite: Kawanomoto18) in the HSC-SSP. We used the CAMIRA cluster catalogue (cite: Oguri18) updated for the third public data release of HSC-SSP (cite: Aihara22) based on the associated bright star masks (cite: Coupon18).

![](figs/J2319_src_virv2.eps)

![](figs/J2319_dirty_virv2.eps)

Weak lensing analysis was done on the HSC-SSP S19A data[^6], following the method described in (cite: Okabe19) and (cite: Okabe21). The galaxy shapes were measured using the re-Gaussianization method (cite: Hirata03) implemented in the HSC pipeline (cite: Mandelbaum18; Li22). The background galaxies behind each cluster were selected using the colour–colour selection following (cite: Medezinski18). The S/N of the resulting surface mass density is computed as in (cite: Okabe19). We adopted the NFW density profile (cite: Navarro96) for estimating the deprojected halo mass, from the tangential shear profiles; given the low S/N ($\sim 2-3$) of the lensing signal, the halo concentration is linked to the mass by the relation of (cite: Diemer15).

| Source ID | RA (J2000) | Dec (J2000) | 92 GHz flux density \[$\mu$Jy\] |
|:---------:|:----------:|:-----------:|:-------------------------------:|
|    C1     |            |             |         $262.9 \pm 3.9$         |
|    C2     |            |             |         $36.6 \pm 3.9$          |
|     W     |            |             |         $76.8 \pm 6.1$          |

| Source ID | RA (J2000) | Dec (J2000) | 92 GHz flux density \[$\mu$Jy\] |
|:---------:|:----------:|:-----------:|:-------------------------------:|
|    W1     |            |             |         $35.3 \pm 4.9$          |
|    W2     |            |             |         $42.2 \pm 4.5$          |

# Results

## Compact millimeter sources

### RCS J2319$+$0038

There are three compact sources above the $5\sigma$ significance level at 92 GHz in our target field toward RCS J2319$+$0038 as shown in figure [1](#fig-source)(a)–(d). Only compact sources, not the SZE, are visible on the images from long-baselines. All the detected sources are consistent with being point-like and their properties are summarized in table [\[tab-source1\]](#tab-source1).

![](figs/J0947_src_virv2.eps)

![](figs/J0947_dirty_virv2.eps)

Two sources (C1 and C2) are located within $5''$ from the X-ray center of RCS J2319$+$0038. There is a galaxy detected by HSC at the photometric redshift of $z_{\rm phot}= 0.92 \pm 0.04$ within $0.2''$ from C1. Two galaxies at $z_{\rm phot}= 0.91 \pm 0.03$ and $0.92 \pm 0.02$ lie at the projected distance of $0.6''$ from C2; the latter is the Brightest Cluster Galaxy (BCG) of RCS J2319$+$0038. Both C1 and C2 are bright at lower frequencies and detected in the Faint Images of the Radio Sky at Twenty-cm (FIRST; (cite: Becker95)) as well as the Very Large Array Sky Survey (VLASS; (cite: Gordon21)). Their combined flux listed in the FIRST Catalog Database[^7] is $4.59
\pm 0.22$ mJy at 1.4 GHz, where we have estimated the error from the image of this region available at the FIRST Cutout Server[^8]. The flux measured on the VLASS Epoch 1.1 image[^9] within a diameter of $15''$ around the position of C1 is $4.9 \pm 0.5$ mJy at 3.0 GHz. Figure [1](#fig-source)(a)(b) indicates that the peak intensity ratio between C1 and C2 is about $2.3 : 1$ and $7.4 : 1$ at 3.0 GHz and 92 GHz, respectively, implying that C2 has a much steeper spectrum than C1. Note that the dust emission can dominate the source flux at 92 GHz, corresponding to the rest-frame frequency of $175$ GHz at $z=0.90$. The luminosity of C1 and C2 is $\nu L_\nu = (9.73 \pm 0.14) \times 10^{41}
h_{70}^{-2}$ erg/s and $(1.32 \pm 0.14) \times 10^{41}h_{70}^{-2}$ erg/s, respectively, at $\nu=175$ GHz in the rest-frame of the cluster.

Another source (W) is located at $\sim 1'$ from the X-ray center of RCS J2319$+$0038. This source hosts bright line emissions as described in Appendix [6](#sec-lines). It has no obvious optical counterpart within $1''$ and is undetected at 1.4 GHz in the FIRST and VLASS images.

The above sources are removed from the visibility data in our subsequent analysis. Figure [1](#fig-source)(d)(e) shows that the residuals at long baselines are consistent with noise, whereas the extended signal from the ICM becomes apparent once shorter baselines are included.

### HSC J0947$-$0119

There are two compact sources above the $5\sigma$ significance level at 92 GHz in our target field toward HSC J0947$-$0119 (figure [2](#fig-source2) and table [\[tab-source2\]](#tab-source2)).

All the detected sources are consistent with being point-like and removed from the visibility data in our subsequent analysis.

One source (W1) lies at $\sim 1'$ south-west of the ALMA SZE center. This source appears to host a bright line emission as described in Appendix [6](#sec-lines). There is a compact object classified as a star in the SDSS Data Release 17 (cite: SDSS17)[^10] at $0.6''$ from this source. There is no other object detected by HSC, VLASS, or FIRST within a projected distance of $1''$ from W1.

Another source (W2) is located at $\sim 20''$ north-west of the ALMA SZE center. There is a galaxy detected by HSC at the photometric redshift of $z_{\rm phot} = 0.9 \pm 0.5$ lying at $0.5''$ from this source. It is undetected by VLASS or FIRST. The large uncertainty in $z_{\rm phot}$ of this object is due to degeneracy of the spectral energy distribution (SED) modeling of low-$z$ and high-$z$ galaxies in the five-band photometric space (cite: Tanaka15).

Figure [2](#fig-source2)(c)(d) further demonstrates that the above sources are subtracted successfully and do not affect the extended signal from the ICM.

![image](figs/J2319_sumx_virv2.eps) ![image](figs/J2319_ACT_virv2.eps) ![image](figs/J2319_HSC_virv2.eps)

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | RA | Dec | major axis FWHM | minor axis FWHM | position angle | Flux density |
|  | (J2000) | (J2000) | \[arcsec\] | \[arcsec\] | \[deg\] | \[mJy\] |
| RCS J2319$+$0038 |  |  | $49.8 \pm 4.8$ | $33.6 \pm 3.2$ | $92.0 \pm 9.7$ | $-2.04 \pm 0.20$ |
| HSC J0947$-$0119 |  |  | $58.6 \pm 3.5$ | $38.7 \pm 2.3$ | $72.3 \pm 5.5$ | $-4.12 \pm 0.24$ |

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $x_0$ | $y_0$ | $S_{\rm 0}$ | $\beta$ | $\theta_{\rm c}$ | $q$ | $\psi$ |
| (J2000) | (J2000) | \[counts/s/arcsec$^2$\] |  | \[arcsec\] |  | \[deg\] |
|  |  | $(2.64^{+0.21}_{-0.20})\times 10^{-5}$ | $0.673^{+0.034}_{-0.032}$ | $13.2^{+1.4}_{-1.2}$ | $0.694^{+0.036}_{-0.034}$ | $96.7 \pm 3.9$ |

## The intracluster medium

### RCS J2319$+$0038

Figure [3](#fig-xszJ2319) shows the deconvolved ALMA image of RCS J2319$+$0038 after compact sources listed in table [\[tab-source1\]](#tab-source1) are removed. The image has been smoothed to an effective beam size of $5''$ FWHM for display purposes. To obtain the overall morphology of the signal, we fit the unsmoothed ALMA image with an elliptical Gaussian using the CASA task *imfit*, varying its center, major and minor axis FWHMs, and the position angle[^11] (table [\[tab-gaussfit\]](#tab-gaussfit)); errors of fitted parameters are estimated based on (cite: Condon97), assuming a constant noise level within a radius of $50"$ from the field center. The extended SZE signal is detected at high significance with ALMA with a mean size of $\sim
40''$ FWHM and an axis ratio of $\sim 0.7$. The integrated flux density within a radius of $45''$ from the position shown in table [\[tab-gaussfit\]](#tab-gaussfit) is $-1.98 \pm 0.10$ mJy; for reference, the flux inferred from the elliptical Gaussian fit is $-2.04 \pm 0.20$ mJy.

The figure also shows the *Chandra* X-ray brightness image of RCS J2319$+$0038 adaptively smoothed with a circular top-hat filter that contains at least 100 photons. We fit the unsmoothed X-ray brightness with an elliptical $\beta$ model of the form $$\begin{eqnarray}
 S(\vec{\theta})
  = S_0 \left[ 1 + \left(\frac{\bar{\theta}}{\theta_{\rm
            c}}\right)^2 
               \right]^{-3\beta + \frac{1}{2}},  
  \label{eq-ellipbeta}
\end{eqnarray}$$ with the position vector on the sky $\vec{\theta} \equiv (x,y)$ related to the “circular mean distance” $\bar{\theta} \equiv \sqrt{\bar{x}^2 +
\bar{y}^2}$ from the emission center $(x_0, y_0)$ by $$\begin{eqnarray}
 \pmatrix{\bar{x} \cr \bar{y}} &\equiv &\pmatrix{\frac{1}{\sqrt{q}} & 0 \cr 0 & \sqrt{q}}
\pmatrix{\cos \psi &  \sin \psi \cr 
 - \sin \psi & \cos \psi} \pmatrix{x-x_0 \cr y-y_0},  
  \label{eq-ellipbeta2}
\end{eqnarray}$$ where $S_0$ is the brightness at $(x_0, y_0)$, $\theta_{\rm c}$ is the angular core radius, $q$ is the minor-to-major axis ratio ($q \le
1$) on the sky, $\psi$ is the position angle, and $\bar{x}$ is intended to align with the minor axis of the ellipse. We used the Sherpa modeling package (*beta2d*) in CIAO (cite: Sherpa01; Sherpa07; Sherpa09) for this purpose. The best-fit values of $x_0$, $y_0$, $S_0$, $\beta$, $\theta_{\rm c}$, $q$, and $\psi$ are listed in table [\[tab-betafit\]](#tab-betafit).

The overall morphology of the SZE on the sky is in agreement with that of X-rays; the emission center also matches within $1.5''$ between two images. Given this agreement and the higher angular resolution ($\sim 0.5''$) of *Chandra*, we refer to the best-fit position of the X-ray emission center in table [\[tab-betafit\]](#tab-betafit) as the center of RCS J2319$+$0038 in the rest of this paper. The intrinsic X-ray luminosity within $15''$ and $150''$ from the center is $L_{\rm
X}=(2.17 \pm 0.09)\times 10^{44} h_{70}^{-2}$ erg/s and $(4.42 \pm
0.30)\times 10^{44} h_{70}^{-2}$ erg/s, respectively, at $E_{\rm obs} =
0.4-7.0$ keV. Further comparison by means of three dimensional gas model will be discussed in sections [4.1](#sec-sim) and [4.3](#sec-yprof).

Figure [3](#fig-xszJ2319) also shows that the centroid of the ACT SZE map of RCS J2319$+$0038 is offset from the centers of the ALMA and *Chandra* images by $\sim 30''$ (230 $h_{70}^{-1}$kpc). We will discuss the possible origin of this offset in section [4.5](#sec-act).

We plot in figure [5](#fig-szprof) azimuthally averaged intensity profiles around the cluster center in four quadrants with position angles of $315^{\circ} \sim 45^{\circ}$ (north), $45^{\circ} \sim 135^{\circ}$ (east), $135^{\circ} \sim  225^{\circ}$ (south), and $225^{\circ} \sim 
315^{\circ}$ (west). The statistical error in each bin is computed using equation (1) of (cite: Kitayama16).

Figures [3](#fig-xszJ2319) and [5](#fig-szprof) suggest that the ICM is disturbed near the center of RCS J2319$+$0038. The SZE signal tends to be stronger in the south and in the west of the center; the significance of departures from the azimuthal average is at $\sim 2 \sigma$ (see section [4.2](#sec-diff)). At $\theta \lower.5ex\hbox{$\; \buildrel > \over \sim \;$}20''$, elongation in the east-west direction becomes more obvious. The X-ray emission peak is also offset from the cluster center, defined by fitting the global emission profile, by $\sim 4''$ or $\sim 32 h_{70}^{-1}$ kpc.

![image](figs/J0947_sum_virv2.eps)\
![image](figs/J0947_ACT_virv2.eps) ![image](figs/J0947_HSC_virv2.eps)

![image](figs/szprof_J2319_v2.eps) ![image](figs/szprof_J0947_v2.eps)

### HSC J0947$-$0119

Figure [4](#fig-szJ0947) shows the deconvolved ALMA image of HSC J0947$-$0119 after compact sources listed in table [\[tab-source2\]](#tab-source2) are removed. As with the case of RCS J2319$+$0038, the results of an elliptical Gaussian fit are listed in table [\[tab-gaussfit\]](#tab-gaussfit) and azimuthally averaged intensity profiles in four quadrants are plotted in figure [5](#fig-szprof).

The SZE signal of HSC J0947$-$0119 tends to be stronger and more extended than that of RCS J2319$+$0038, with a mean size of $\sim 45''$ FWHM and an axis ratio of $0.66 \pm 0.06$ (table [\[tab-gaussfit\]](#tab-gaussfit)). The integrated flux density within $45''$ from the position shown in table [\[tab-gaussfit\]](#tab-gaussfit) is $-3.66\pm 0.11$ mJy. For reference, the flux inferred from the elliptical Gaussian fit is $-4.12
\pm 0.24$ mJy.

The best-fit center of the ALMA image (, ) is $8''$ north-east of the centroid position of the ACT image (, ) and represents reasonable agreement considering the angular resolution (FWHM $\sim 1.4'$) and the significance (S/N$=13.2$) of the ACT data (see also section [4.5](#sec-act)). Given the lack of *Chandra* data for this cluster, we refer to the former position as the center of HSC J0947$-$0119 in the rest of this paper.

Figures [4](#fig-szJ0947) and [5](#fig-szprof) suggest that the ICM in HSC J0947$-$0119 is disturbed. The SZE signal tends to be stronger along the north-east and the south-west direction across the emission center. As will be discussed in section [4.2](#sec-diff), the statistical significance of disturbance is at $\sim 2 \sigma$, and tends to be larger in RCS J2319$+$0038.

## Galaxy density and weak lensing mass

Figures [3](#fig-xszJ2319) and [4](#fig-szJ0947) also show the HSC-SSP optical images of RCS J2319$+$0038 and HSC J0947$-$0119, respectively. The richness of these clusters is $N_{\rm mem}=31.6$ and $67.5$, respectively, where $N_{\rm mem}$ is the number of galaxies with stellar mass larger than $10^{10.2}M_\odot$ taking into account membership probability (see (cite: Oguri14) for definition). The galaxies in both clusters show bimodal density peaks indicative of subcluster mergers, if they are not subject to a chance projection effect. The BCG lies in the main peak of galaxy density in each cluster.

The weak lensing signal is only marginally detected with the peak S/N of 2.8 and 3.2 for RCS J2319$+$0038 and HSC J0947$-$0119, respectively, after being smoothed by a Gaussian with $30''$ FWHM. While the significance is low, the peak of the surface mass density is in agreement with the main peak of galaxy concentration. Assuming the NFW density profile (cite: Navarro96) and the mass–concentration relation of (cite: Diemer15), the values of the characteristic mass, estimated from the weak lensing measurements, are $M_{500}=3.6
^{+4.6}_{-2.2} \times 10^{14} h_{70}^{-1}M_\odot$ and $2.6 ^{+3.2}_{-1.4} \times
10^{14} h_{70}^{-1}M_\odot$ for RCS J2319$+$0038 and HSC J0947$-$0119, respectively[^12]. Note that the errors on $M_{500}$ from weak lensing are very large for these distant clusters, owing to the limited number of background galaxies.

Figure [3](#fig-xszJ2319) further indicates that the ALMA SZE and *Chandra* X-ray centers of RCS J2319$+$0038 coincide with the highest peak of galaxy density and the weak lensing mass. The BCG also lies within $1''$ from the X-ray center. On the other hand, no concentration of the ICM is detected around the second peak of galaxy density, which lies at $\sim 40''$ east of the main peak. The ICM morphology is still elongated toward the second peak of galaxy density.

On the other hand, the SZE center of HSC J0947$-$0119 (figure [4](#fig-szJ0947)) is persistently offset from the BCG and the main peak of galaxy density by about $17''$ (140 $h_{70}^{-1}$kpc), suggesting the presence of a strong disturbance in this cluster. The ICM morphology is also elongated toward the second peak of galaxy density.

The above results imply that highly asymmetric galaxy distributions seen in optical images (figures [3](#fig-xszJ2319) and [4](#fig-szJ0947)) could be associated with relatively small values ($\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}0.7$) of the axis ratio found for the ICM in both clusters (tables [\[tab-gaussfit\]](#tab-gaussfit) and [\[tab-betafit\]](#tab-betafit)); average values of the axis ratio reported for massive clusters at low $z$ are $0.8\sim 0.9$ (e.g., (cite: Kawahara10; Donahue16)).

# Interpretation and implications

## Imaging simulations

To quantify the missing flux of the ALMA data and to test the fidelity of the image reconstruction algorithm, we performed imaging simulations as follows.

### Method

We first specified the Compton $y$-parameter (i.e., projected electron pressure) $$\begin{equation}
  y(\vec{\theta}) =  \int \sigma_{\rm T}
   n_{\rm e} \frac{kT_{\rm e}}{m_{\rm e}c^2}  dl,  
\end{equation}$$ for each cluster in consideration, where $\sigma_{\rm T}$ is the Thomson cross section, $k$ is the Boltzmann constant, $m_{\rm e}$ is the electron mass, $c$ is the speed of light,

and $l$ denotes the physical length along the line-of-sight toward the sky position $\vec{\theta}$. Details of the models on $n_{\rm e}$ and $T_{\rm e}$ will be described in section [4.1.2](#sec-simmodel).

Input model images of the SZE were created from the above Compton $y$-parameter map separately at four spectral windows centered at 85, 87, 97, and 99 GHz with an effective bandwidth of 1.875 GHz each. A relativistic correction to the SZE intensity by (cite: Itoh04) was taken into account.

Visibility data were then produced using the CASA task *simobserve* including both instrumental and atmospheric thermal noise in each spectral window; this procedure was repeated 10 times adopting different noise seeds. The pointing directions, the array configuration, the hour angle, the total effective integration time, and the average precipitable water vapor were set to match those of each executing block of real observations for each cluster.

Finally, the mock visibility was deconvolved in the same way as the real data as described in section [2.1](#sec-almadata). For reference, we also performed “noise-only” runs in which the input SZE signal is set to zero. We have checked that the RMS levels of dirty maps created from such noise-only runs are consistent with the observed values in table [\[tab-image\]](#tab-image). To take into account any bias in producing an image at a single frequency from the data taken over finite bandwidths, the simulation outputs are compared with an input model evaluated at the central frequency 92 GHz.

### Input models

The model Compton $y$-parameter map of RCS J2319$+$0038 was constructed from the available X-ray data as follows. Fitting the 0.4–7.0 keV spectrum within $45''$ from the cluster center yielded the average electron temperature of $kT_{\rm e}=5.90^{+0.79}_{-0.62}$ keV.

Assuming that the gas is isothermal[^13], a triaxial electron density profile consistent with an elliptical $\beta$ model specified by equations ([\[eq-ellipbeta\]](#eq-ellipbeta)) and ([\[eq-ellipbeta2\]](#eq-ellipbeta2)) is $$\begin{equation}
  n_{\rm e}(\vec{r}) =
   n_{\rm e0}
   \left[1+\frac{\bar{\theta}^2 + \left(\phi/\eta\right)^2}{\theta_{\rm
                  c}^2}\right]^{-\frac{3}{2}\beta},
 \label{eq-nbeta}
 
\end{equation}$$ where $n_{\rm e0}$ is the central electron density, $\phi$ denotes the line-of-sight angular displacement between the three dimensional position $\vec{r}$ and the cluster center (i.e., physical distance divided by the angular diameter distance to the cluster $d_{\rm A}$), $\bar{\theta}$ is the mean angular radius on the sky as in equations ([\[eq-ellipbeta\]](#eq-ellipbeta)) and ([\[eq-ellipbeta2\]](#eq-ellipbeta2)), and $\eta$ is the elongation factor along the line-of-sight. In other words, we assumed that the electron density profile has the axis ratio of $$\begin{equation}
   \sqrt{q} : \frac{1}{\sqrt{q}} :\eta
\label{eq-3daxis}
 
\end{equation}$$ where the first axis corresponds to $\bar{x}$ in equation ([\[eq-ellipbeta2\]](#eq-ellipbeta2)) and the third axis is effectively along the line-of-sight; we neglected the inclination of the third axis from the line-of-sight, given the lack of data to constrain it. Adopting the fitted values of $S_0$, $\beta$, $\theta_{\rm c}$, $q$, and $\psi$ from table [\[tab-betafit\]](#tab-betafit) as well as $kT_{\rm e}=5.90$ keV, we obtained $n_{\rm e0}= 1.43 \times
 10^{-2} h_{70}^{1/2} \eta^{-1/2}$ cm$^{-3}$. Integrating the product of $n_{\rm e}$ and $kT_{\rm e}$ over the line-of-sight gives a Compton $y$-parameter map with the peak value of $y_{\rm peak}=1.1\times
 10^{-4} h_{70}^{-1/2} \eta^{1/2}$. To specify the absolute value of the model intensity in the simulations, we assumed fiducially $h_{70}/\eta=1$ to obtain $y_{\rm peak}=1.1\times 10^{-4}$; we will discuss the impact of varying $h_{70}/\eta$ in section [4.3](#sec-yprof). To take into account uncertainties of this model parameterization, we will also examine the cases in which the overall normalization of the $y$-parameter is doubled or halved, i.e., $y_{\rm peak}=2.2 \times
 10^{-4}$ and $0.55 \times 10^{-4}$. We will show in sections [4.2](#sec-diff) and [4.3](#sec-yprof) that the case with $y_{\rm
 peak}=1.1\times 10^{-4}$ indeed agrees well with the observed ALMA data.

Given the lack of X-ray data for HSC J0947$-$0119, we used the average pressure profile measured from a statistical sample of X-ray clusters at $0.6 <
 z < 1.2$ by (cite: McDonald14b). We also assumed a triaxial gas profile consistent with the axis ratio and the position angle observed on the sky for this cluster (table [\[tab-gaussfit\]](#tab-gaussfit)). As with RCS J2319$+$0038, the axis ratio was assumed to be given by equation ([\[eq-3daxis\]](#eq-3daxis)). As discussed in sections [4.2](#sec-diff) and [4.3](#sec-yprof), the observed ALMA data are well reproduced by this profile with $M_{500}=5.7 \times 10^{14}$ M$_\odot$ assuming $h_{70}=1$ and $\eta=1$. We hence adopted this profile for the present simulations and estimated the mean temperature to be $kT_{\rm e}=9.4$ keV using the scaling relation of (cite: Reichert11). The inferred peak value of the $y$-parameter is $y_{\rm peak}=1.5 \times 10^{-4}$. The sensitivity of the result to $y$-parameter map is examined by considering limiting cases where the overall map normalization is doubled or halved (i.e., $y_{\rm peak}=3.0 \times
  10^{-4}$ and $0.75 \times 10^{-4}$).

![image](figs/J2319_sim1_vir2.eps) ![image](figs/J2319_sim2_vir2.eps) ![image](figs/J2319_sim3_vir2.eps)

![image](figs/J0947_sim1_virv2.eps) ![image](figs/J0947_sim2_virv2.eps) ![image](figs/J0947_sim3_virv2.eps)

![image](figs/szprof_sim_J2319.eps) ![image](figs/szprof_sim_J0947_v2.eps)

| cluster | $y_{\rm peak}$ \[$10^{-4}$\] | $c_1$ | $c_0$ \[$\mu$Jy/arcsec$^2$\] |
|:--:|:--:|:--:|:--:|
|  | $0.55$ | $0.89 \pm 0.03$ | $0.35\pm 0.04$ |
| RCS J2319$+$0038  | $1.1$ | $0.89\pm 0.03$ | $0.62 \pm 0.06$ |
|  | $2.2$ | $0.89\pm 0.03$ | $1.19 \pm 0.11$ |
|  | $0.75$ | $0.79 \pm 0.03$ | $0.42 \pm 0.05$ |
| HSC J0947$-$0119  | $1.5$ | $0.79 \pm 0.03$ | $0.75 \pm 0.07$ |
|  | $3.0$ | $0.79 \pm 0.03$ | $1.38 \pm 0.12$ |

![image](figs/conv_J2319.eps) ![image](figs/conv_bind_J2319.eps)

![image](figs/conv_J0947_v2.eps) ![image](figs/conv_bind_J0947_v2.eps)

![](figs/diff_J2319_J0947_virv2.eps)

### Missing flux correction using simulation results

Figures [6](#fig-simJ2319) and [7](#fig-simJ0947) compare arbitrarily chosen realizations of the simulated images and the input models for RCS J2319$+$0038 and HSC J0947$-$0119, respectively. The azimuthal average of all realizations are shown in figure [8](#fig-szprofsim). The simulated images show similar amplitude and spatial extension to the real data plotted in figures [3](#fig-xszJ2319) and [4](#fig-szJ0947) for $y_{\rm
 peak}=1.1 \times 10^{-4}$ (RCS J2319$+$0038) and $y_{\rm peak}=1.5 \times
 10^{-4}$ (HSC J0947$-$0119), respectively.

As noted in (cite: Kitayama16) and (cite: Kitayama20), the following linear relation holds on average for the simulated ALMA images

$$\begin{eqnarray}
I_{\nu}^{\rm out}(\vec{\theta}) = c_1 I_{\nu}^{\rm in}(\vec{\theta}) + c_0, 
\label{eq-conv}
\end{eqnarray}$$

where $I_{\nu}^{\rm out}$ and $I_{\nu}^{\rm in}$ are respectively the intensities of output and input images at the same sky position $\vec{\theta}$. This equation relates the object’s observed to intrinsic intensity and is used in sections [4.3](#sec-yprof) and [4.4](#sec-deproj) to correct for the missing flux. To obtain $c_1$ and $c_0$ in equation ([\[eq-conv\]](#eq-conv)), a set of data ($I_{\nu}^{\rm in}$, $I_{\nu}^{\rm out}$) was created for each sky position in each simulated image and then binned in descending order of $I_{\nu}^{\rm in}$. Each bin contains at least 1000 pixel data after accumulating 10 realizations for each adopted value of $y_{\rm peak}$. The mean and the standard deviation of $I_{\nu}^{\rm out}$ in each bin are plotted against $I_{\nu}^{\rm in}$ in figures [9](#fig-conv) and [10](#fig-conv2). These figures indicate that equation ([\[eq-conv\]](#eq-conv)) holds well and $c_1$ is insensitive to the adopted value of $y_{\rm peak}$ (i.e., the overall normalization of the emission); $c_1$ depends primarily on the shape and the gradient of the emission as well as the observing conditions (e.g., the $uv$ coverage).

Table [\[tab-conv\]](#tab-conv) lists the fitted values of $c_0$ and $c_1$, assuming that $c_1$ is common among different values of $y_{\rm peak}$ for each cluster. The obtained value of $c_1$ is close to unity but takes a smaller value for HSC J0947$-$0119, whose $y$-parameter profile is shallower than RCS J2319$+$0038 (figure [12](#fig-yprof)). The specific value of $c_0$ will not affect our real data analysis as it will be eliminated in equation ([\[eq-conv2\]](#eq-conv2)) described below.

Figures [6](#fig-simJ2319)–[8](#fig-szprofsim) further illustrate that the simulated images are in agreement with the input models once corrected by equation ([\[eq-conv\]](#eq-conv)), as described above. The RMS values at $\theta < 45''$ in figures [6](#fig-simJ2319)(d)(g) and [7](#fig-simJ0947)(d)(g) are 6.2, 5.9, 5.7, and 6.3 $\mu$Jy/beam, respectively, and fully consistent with noise.

The above results imply that the relative intensity with respect to some reference point $\vec{\theta}_{\rm ref}$ follows

$$\begin{eqnarray}
 I_{\nu}^{\rm out}(\vec{\theta})
  - I_{\nu}^{\rm out}(\vec{\theta}_{\rm ref})
  = c_1 \left[
     I_{\nu}^{\rm in}(\vec{\theta})
     - I_{\nu}^{\rm in}(\vec{\theta}_{\rm ref})\right]
  \label{eq-conv2}
\end{eqnarray}$$

nearly independently of the underlying value of $y_{\rm peak}$. The coefficient $c_1$ denotes how much of the intrinsic intensity is retained on average in the deconvolved image for each cluster. In the rest of this paper, we refer to the conversion from $I_{\nu}^{\rm out}(\vec{\theta})
  - I_{\nu}^{\rm out}(\vec{\theta}_{\rm ref})$ to $I_{\nu}^{\rm in}(\vec{\theta})
     - I_{\nu}^{\rm in}(\vec{\theta}_{\rm ref})$ using the best-fit values of $c_1$ from table [\[tab-conv\]](#tab-conv) as the “missing flux correction". We will apply this correction to the real data taking off-center positions as $\vec{\theta}_{\rm ref}$; specifically, the reference points are taken at the mean radius $\bar{\theta}=35''$ from the cluster center, which lie at the envelope of the emission profiles from real data (figure [5](#fig-szprof)) and simulation outputs (figure [8](#fig-szprofsim)).

### Systematic errors

We estimated systematic errors associated with the above missing flux correction as follows. The errors of $I_{\nu}^{\rm out}$ plotted in figures [9](#fig-conv) and [10](#fig-conv2) are dominated by statistical ones; each bin contains more than 1000 pixel data (i.e., 100 per realization). The systematic deviation from equation ([\[eq-conv\]](#eq-conv)) apart from such statistical errors is represented by the RMS deviation of the mean values of $(I_{\nu}^{\rm in},I_{\nu}^{\rm
out})$ from the best-fitting result; $\Delta I_\nu^{\rm in}=0.021
~\mu$Jy/arcsec$^2$ and $0.029$ $\mu$Jy/arcsec$^2$ for RCS J2319$+$0038 and HSC J0947$-$0119, respectively. We regard $\sqrt{2}$ times this value (i.e., $\Delta I_\nu^{\rm in}=0.030 ~\mu$Jy/arcsec$^2$ and $0.042$ $\mu$Jy/arcsec$^2$ for RCS J2319$+$0038 and HSC J0947$-$0119, respectively) as the 1$\sigma$ systematic uncertainty in the difference $I_{\nu}^{\rm in}(\vec{\theta})
     - I_{\nu}^{\rm in}(\vec{\theta}_{\rm ref})$ recovered using equation ([\[eq-conv2\]](#eq-conv2)).

We also examined if the subtraction of compact sources as described in section [3.1](#sec-source) affects the measurements of the SZE by adding sources C1 and C2 (table [\[tab-source1\]](#tab-source1)) to the simulations with $y_{\rm peak}=1.1\times 10^{-4}$ for RCS J2319$+$0038; the other sources are irrelevant to the measured SZE profiles. Repeating the simulations 10 times varying noise seeds, we found that the errors associated with the subtraction of C1 and C2 are fully statistical with no seizable systematic effects on $I_\nu^{\rm out}$. At arbitrary positions in the cluster, we take the difference of $I_\nu^{\rm out}$ with respect to the point-source-free run with the same noise seed, regard its RMS value over the 10 realizations as an additional error in $I_\nu^{\rm out}$ due to the source subtraction, and add it to the errors of the measured SZE profiles in sections [4.3](#sec-yprof) and [4.4](#sec-deproj).

Table [\[tab-syst\]](#tab-syst) summarizes the systematic errors mentioned above, together with those included in the subsequent analysis.

| Error source | RCS J2319$+$0038  | HSC J0947$-$0119  |
|:---|:---|:---|
| Missing flux correction | $0.030~\mu$Jy/arcsec$^2$ | $0.042~\mu$Jy/arcsec$^2$ |
| Point source subtraction | $0.117~\mu$Jy/arcsec$^2$  ($0<\theta<4"$) | $-$ |
|  | $0.023~\mu$Jy/arcsec$^2$  ($4"<\theta<8.4"$) | $-$ |
|  | $0.021~\mu$Jy/arcsec$^2$  ($0<\theta<10"$) | $-$ |
| Flux calibration of ALMA at 92GHz | $6\%$ of the SZE intensity | $6\%$ of the SZE intensity |
| Effective area of *Chandra* ACIS-S | $4\%$ of the X-ray intensity | $-$ |

## Residual SZE images

Figure [11](#fig-diff) shows residual images after the elliptical models described in section [4.1](#sec-sim) are subtracted from the real ALMA images in figures [3](#fig-xszJ2319) and [4](#fig-szJ0947). The subtracted models are essentially the same as those plotted in panel (b) of figures [6](#fig-simJ2319) and [7](#fig-simJ0947); the intrinsic intensity has been corrected by equation [\[eq-conv\]](#eq-conv) and smoothed to $5''$ FWHM.

The residual images exhibit moderate ($2 \sim 3\sigma$) levels of deviations, which should comprise real departures from symmetry and noise. The RMS value of the residuals for HSC J0947$-$0119, 6.8 $\mu$Jy/beam, is slightly larger than that for RCS J2319$+$0038, 6.5 $\mu$Jy/beam. Apart from these deviations, the overall morphology of the real ALMA image is well reproduced by the elliptical model for each cluster.

## Inner pressure profiles

The SZE images provide a direct probe of integrated electron pressure, i.e., the Compton $y$-parameter. We used the results of section [4.1](#sec-sim) to reconstruct the Compton $y$-parameter profile as follows.

### Method

The observed intensity was averaged over elliptical bins to take into account elongated morphology of the clusters; the axis ratio and the position angle were fixed at the best-fit values listed in tables [\[tab-betafit\]](#tab-betafit) and [\[tab-gaussfit\]](#tab-gaussfit) for RCS J2319$+$0038 and HSC J0947$-$0119, respectively. The bins are geometrically spaced with the inner-most bin at $0 < \bar{\theta} < 4''$ and the bin width increasing by a factor of 1.1, so that the statistical error in the final $y$-parameter profile is less than about 20% in each bin (an increasing bin width alleviates the decreasing S/N with radius).

The intrinsic SZE intensity at 92 GHz was then computed for each bin using equation ([\[eq-conv2\]](#eq-conv2)) and taking the 7th bin containing $\bar{\theta}=35''$ (centered at $\bar{\theta}=34.4''$) as the reference points ($\vec{\theta}_{\rm ref}$). The systematic errors associated with the missing flux correction ($\Delta I_\nu^{\rm in}=0.030 ~\mu$Jy/arcsec$^2$ and $0.042$ $\mu$Jy/arcsec$^2$ for RCS J2319$+$0038 and HSC J0947$-$0119, respectively, estimated in section [4.1.4](#sec-syst)) and the absolute calibration uncertainty of ALMA (6%; (cite: Kitayama16)) were added in quadrature to the statistical error in each bin. For RCS J2319$+$0038, the error from the source subtraction (section [4.1.4](#sec-syst), table [\[tab-syst\]](#tab-syst)), estimated as $0.117$ and $0.023~\mu$Jy/arcsec$^2$ for the inner-most and the second inner-most bins, respectively, was also added in quadrature.

Finally, the intrinsic SZE intensity is proportional to the Compton $y$-parameter times the temperature-dependent relativistic correction factor $c_{\rm rel}$, defined to be the ratio between the true SZE intensity and the SZE intensity in the non-relativistic limit. For a range of temperatures considered in this paper, $3< kT
< 10$ keV, $c_{\rm rel}$ is in the range $0.94 < c_{\rm rel} < 0.98$ at 92 GHz (e.g., (cite: Itoh04)). To eliminate the dependence of the data points on the temperature, $c_{\rm rel}$ is used for correcting the model predictions and not the data in section [4.3.2](#sec-yprofres).

![image](figs/yprof_J2319a_v2.eps) ![image](figs/yprof_J0947a_v2.eps) ![image](figs/yprof_J2319b_v2.eps) ![image](figs/yprof_J0947b_v2.eps)

as marked by an asterisk in table [\[tab-yfit\]](#tab-yfit). The solid line shows the $\beta$ model profile inferred from the X-ray data of RCS J2319$+$0038. All the lines adopt $h_{70}=1$ and $\eta=1$. Both the data points and the expectations are relative to the positions at $\theta=34.4''$.

### Reconstructed $y$-parameter profile

Figure [12](#fig-yprof) compares the Compton $y$-parameter profile so obtained with various model predictions. By construction the model predictions, not the data points presented, are influenced by the relativistic correction via the assumed temperature and the values of $h_{70}$ and $\eta$ (i.e., introduced in equations [\[eq-nbeta\]](#eq-nbeta) and [\[eq-3daxis\]](#eq-3daxis), respectively).

All the model predictions are smoothed to the same beam size and averaged over the same radial bins as the data in the analysis; unbinned predictions are shown for display purposes only.

We first examine the isothermal $\beta$ model inferred from the X-ray data of RCS J2319$+$0038; $kT=5.90$ keV, $n_{\rm e0}=1.43 \times 10^{-2} h_{70}^{1/2}
\eta^{-1/2}$ cm$^{-3}$, $\beta=0.673$ and $r_{\rm c}= 103 \
h_{70}^{-1}$kpc. The observed $y$-parameter profile of RCS J2319$+$0038 is consistent with this model and provides a useful limit on $h_{70}/\eta$. If $h_{70}/\eta$ is varied as a free parameter, the best-fit value is $$\begin{equation}
 \frac{h_{70}}{\eta} = 1.07^{+0.15}_{-0.12} 
\end{equation}$$ with the minimum $\chi^2$ of 3.1 for 5 degrees of freedom (dof). Taking $h_{70}/\eta=1$ as in the left panel of figure [12](#fig-yprof) gives $\chi^2=3.4$ and is in reasonable agreement with the data.

We also consider the generalized NFW pressure profile (cite: Nagai07) with model parameters obtained from a sample of X-ray selected clusters at $z<0.2$ by (cite: Arnaud10) or SZE selected clusters at $0.6<z<1.2$ by (cite: McDonald14b). Specifically, we used equation (13) of (cite: Arnaud10) with the parameter values listed in table 5 of (cite: McDonald14b) for either “cool-core”, “non-cool-core”, or “all” clusters in each sample and allowed the characteristic mass $M_{500}$ to vary. The relativistic correction was computed for the temperature specified by $M_{500}$ and $z$ from the scaling relation of (cite: Reichert11). The SZE intensity predicted from the generalized NFW pressure profile varies as $I_{\rm SZ} \propto c_{\rm
rel} (M_{500}h_{70})^{2/3 + 0.12} h_{70}^{1/2} \eta R_{500} \simeq
M_{500}^{1.10} h_{70}^{0.60} \eta$, where $R_{500} \propto M_{500}^{1/3}
h_{70}^{-2/3}$, $c_{\rm rel}\propto T_{\rm e}^{-0.03}$ for $3 < kT_{\rm
e}<10$ keV at 92 GHz, and $M_{500} h_{70} \propto T_{\rm e}^{1.62}$ from equation (23) of (cite: Reichert11). Fitting the observed SZE intensity hence gives approximately $$\begin{equation}
 M_{500} \propto h_{70}^{-0.55}\eta^{-0.91}.
\end{equation}$$ With this variation in mind, we present the results with $h_{70}=1$ and $\eta=1$ in what follows.

+:------------------------------:+:-------------------------------:+:--------------:+:------------------------------:+:--------------:+
| Assumed pressure profile       | RCS J2319$+$0038 at $z=0.90$                     | HSC J0947$-$0119 at $z=1.11$                    |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+
|                                | $M_{500}$ \[$10^{14} M_\odot$\] | $\chi^2/$dof   | $M_{500}$ \[$10^{14}M_\odot$\] | $\chi^2/$dof   |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+
| $z<0.2$, cool-core             | $2.1\pm 0.1$                    | $11/5$         | $2.1\pm 0.1$                   | $44/5$         |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+
| $z<0.2$, all                   | $2.5\pm 0.1$                    | $3.8/5$        | $2.7 \pm 0.1$                  | $24/5$         |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+
| $z<0.2$, non-cool-core         | $^{*}3.6\pm 0.2$                | $1.3/5$        | $^{*}3.8 \pm 0.2$              | $11/5$         |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+
| $0.6 < z < 1.2$, cool-core     | $4.8\pm 0.3$                    | $2.3/5$        | $5.0 \pm 0.3$                  | $5.5/5$        |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+
| $0.6 < z < 1.2$, all           | $^{*}5.4\pm 0.4$                | $3.3/5$        | $^{*}5.7 \pm 0.4$              | $4.7/5$        |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+
| $0.6 < z < 1.2$, non-cool-core | $6.0\pm 0.5$                    | $3.8/5$        | $6.1 \pm 0.4$                  | $4.5/5$        |
+--------------------------------+---------------------------------+----------------+--------------------------------+----------------+

Table [\[tab-yfit\]](#tab-yfit) lists the values of $M_{500}$ fitted to the observed $y$-parameter profile of each cluster. As representative cases, we plot in figure [12](#fig-yprof) the model predictions for $M_{500}$ *fixed* at the best-fit value for “non-cool-core clusters at $z<0.2$" (top panels) or “all clusters at $0.6<z<1.2$" (bottom panels) as marked by an asterisk in table [\[tab-yfit\]](#tab-yfit). Notice that the predictions for the other models, shown for reference, do *not* correspond to the overall best-fit. The agreement between the model and data improves upon allowing $M_{500}$ the freedom to vary.

The $y$-parameter profile of RCS J2319$+$0038 is consistent with the average pressure profiles at $0.6<z<1.2$ or a slightly steeper profile of non-cool-core clusters at $z<0.2$. It is still much shallower than the average of cool-core clusters at $z<0.2$. The fitted value of $M_{500}$ for non-cool-core clusters at $z<0.2$ or for cool-core clusters at $0.6<z<1.2$ is in reasonable agreement with $M_{500}=4.01^{+0.38}_{-0.39} \times 10^{14} M_\odot$ inferred from the *Chandra* X-ray data of RCS J2319$+$0038 assuming hydrostatic equilibrium (cite: Hicks08), or with $M_{500} = 3.6 ^{+4.6}_{-2.2} \times 10^{14}
M_\odot$ from our weak lensing analysis (section [3.3](#sec-hsc)). For reference, (cite: Hilton21) reports the value[^14] $M_{500} =
2.08^{+ 0.43}_{- 0.36} \times 10^{14} M_\odot$ from the ACT SZE data assuming the average pressure profile at $z<0.2$ by (cite: Arnaud10), whereas the value inferred from the mass-richness relation of (cite: Okabe19) is $M_{500} \simeq 1.8 \times 10^{14} M_\odot$.

The $y$-parameter profile of HSC J0947$-$0119 appears to be even shallower than that of RCS J2319$+$0038 and reproduced well by the average pressure profile of non-cool-core clusters at $0.6<z<1.2$. It is inconsistent with either average profiles of local clusters or the same $\beta$ model as RCS J2319$+$0038 ($\chi^2/\mbox{dof}=39/6$). For reference, $M_{500} =
2.6 ^{+3.2}_{-1.4} \times 10^{14} M_\odot$ is inferred from our weak lensing analysis (section [3.3](#sec-hsc)), $M_{500} = 4.05^{+ 0.64}
_{- 0.56} \times 10^{14} M_\odot$ from the ACT SZE data of HSC J0947$-$0119 assuming the average pressure profile at $z<0.2$ (cite: Hilton21), and $M_{500} \simeq 5.7 \times 10^{14} M_\odot$ from the mass-richness relation of (cite: Okabe19).

Note that the above $y$-parameter profiles are derived around the X-ray center of RCS J2319$+$0038 and the SZE center of and HSC J0947$-$0119, given the lack of high-resolution X-ray data for the latter (section [3.2](#sec-icm)). The shallow pressure profile of HSC J0947$-$0119 could hence be due partly to a mismatch, if any, between the SZE center and the gas density peak, seen frequently in merging clusters. Future X-ray observations of HSC J0947$-$0119 will be useful for investigating this point further.

## Deprojected electron temperature and density of RCS J2319$+$0038

Resolved SZE and X-ray brightness images of RCS J2319$+$0038 further allow us to constrain temperature and density profiles, thereby relaxing the isothermal approximation. The procedure is an extension of that described in (cite: Kitayama20) to an ellipsoidal gas profile.

### Method

The observed SZE or X-ray brightness was averaged over an elliptical annulus with the axis ratio and the position angle fixed at the best-fit values in table [\[tab-betafit\]](#tab-betafit). The bin size is $\Delta \bar{\theta} = 10''$ so that the statistical error in the brightness is less than 10% in each bin at $\bar{\theta} < 30''$. The intrinsic SZE intensity was computed for each bin using equation ([\[eq-conv2\]](#eq-conv2)) and taking the 4th bin centered at $\bar{\theta}=35''$ as the reference points ($\vec{\theta}_{\rm ref}$).

Systematic errors from the flux calibration of ALMA (6%, (cite: Kitayama16)), the missing flux correction of the SZE (0.030 $\mu$Jy/arcsec$^2$, section [4.1.4](#sec-syst)), and the effective area of *Chandra* ACIS-S (4%) were added in quadrature to the statistical error. The error from the source subtraction , estimated as $0.021~\mu$Jy/arcsec$^2$ for the inner-most bin (section [4.1.4](#sec-syst), table [\[tab-syst\]](#tab-syst)), was also added in quadrature.

We then fit the volume averaged brightness in each elliptical annulus (in 2D) of the SZE at $\bar{\theta} < 30''$ and of the 0.4–7.0 keV X-rays at $\bar{\theta} < 60''$ together varying the temperature and the density in each ellipsoidal shell (in 3D); the orientation of the axis was assumed to be the same as the triaxial $\beta$ model described in section [4.1.2](#sec-simmodel). As the temperature at $\bar{\theta} > 30''$ ($\bar{r} > 230$ kpc) cannot be constrained by the ALMA data, it was fixed at the projected mean value of 5.90 keV from the X-ray spectral analysis described in section [4.1](#sec-sim)[^15]. For the SZE, we modeled incremental brightness relative to the bin centered at $\bar{\theta}=35''$ taking account of the temperature-dependent relativistic correction in each ellipsoidal shell. The X-ray emissivity was computed by SPEX version 3.0.6.01 (cite: Kaastra96; Kaastra20).

From the reconstructed electron temperature and density, we evaluated entropy $K$ and the radiative cooling time $t_{\rm
cool}$ in each shell by $$\begin{eqnarray}
 K &=&\frac{kT_{\rm e}}{n_{e}^{2/3}}, \\
 t_{\rm cool} &=& \frac{3}{2}\frac{(n_{\rm e} + n_{\rm H} + n_{\rm
  He})kT_{\rm e}}{n_{\rm e} n_{\rm H}\Lambda_{\rm bol}},
\end{eqnarray}$$ where $n_{\rm H}$ and $n_{\rm He}$ are the number densities of hydrogen and helium atoms, respectively, and $n_{\rm e}
n_{\rm H}\Lambda_{\rm bol}$ denotes the bolometric luminosity per unit volume. We obtained $\Lambda_{\rm bol}$ by integrating the rest-frame X-ray emissivity from $0.1$ eV to 1 MeV (e.g., (cite: Schure09)).

![image](figs/kt_v2.eps) ![image](figs/ne_v2.eps) ![image](figs/entropy_v2.eps) ![image](figs/tcool_v2.eps)

The quantities obtained by a joint SZE and X-ray analysis have different dependencies on distance from those by the X-ray spectral analysis. The predicted SZE and X-ray intensities vary approximately as $I_{\rm SZ} \propto n_{\rm e} T_{\rm e}^{\alpha_{\rm
SZ}} h_{70}^{-1} \eta$ and $I_{\rm X} \propto n_{\rm e}^2 T_{\rm
e}^{\alpha_{\rm X}} h_{70}^{-1} \eta$, respectively, where $\alpha_{\rm
SZ} \simeq 0.97$ at 92 GHz and $\alpha_{\rm X} \simeq 0.52$ at $E_{\rm
obs}=0.4-7.0$ keV ($z=0.90$), over the range $3 < kT_{\rm e} < 10$ keV. Jointly fitting $I_{\rm SZ}$ and $I_{\rm X}$ gives $$\begin{eqnarray}
T_{\rm e} &\propto&
\left(\frac{h_{70}}{\eta}\right)^{\frac{1}{2\alpha_{\rm SZ}-\alpha_{\rm X}}} \simeq
\left(\frac{h_{70}}{\eta}\right)^{0.70}, \\
n_{\rm e} &\propto& 
\left(\frac{h_{70}}{\eta}\right)^{\frac{\alpha_{\rm SZ}-\alpha_{\rm X}}{2\alpha_{\rm
SZ}-\alpha_{\rm X}}} \simeq
\left(\frac{h_{70}}{\eta}\right)^{0.32}, \\ 
K &\propto&
\left(\frac{h_{70}}{\eta}\right)^{\frac{3 - 2 \alpha_{\rm SZ} +
2\alpha_{\rm X}}{3(2\alpha_{\rm SZ}  -\alpha_{\rm X})}} \simeq
\left(\frac{h_{70}}{\eta}\right)^{0.49}, \\
t_{\rm cool} &\propto& 
 \left(\frac{h_{70}}{\eta}\right)^{\frac{1 + \alpha_{\rm X} -
 \alpha_{\rm SZ} - 
\alpha_{\rm
 bol}}{2\alpha_{\rm SZ}-\alpha_{\rm X}}} \simeq
 \left(\frac{h_{70}}{\eta}\right)^{0.09},
 \label{eq-tc}
 
\end{eqnarray}$$ where we have used $\Lambda_{\rm bol} \propto T_{\rm e}^{\alpha_{\rm
 bol}}$ with $\alpha_{\rm bol} \simeq 0.42$ for $3 < kT_{\rm e} < 10$ keV in equation ([\[eq-tc\]](#eq-tc)). We present the results with $h_{70}/\eta=1$ in figure [13](#fig-deproj).

### Deprojected profiles

Figure [13](#fig-deproj)(a) shows the deprojected electron temperature profile of RCS J2319$+$0038. Also plotted for reference are the average profiles of cool-core and non-cool-core clusters at $0.6<z<1.2$ (cite: McDonald14b). The results are consistent with the mean X-ray spectroscopic temperature of $kT_{\rm e}=5.90^{+0.79}_{-0.62}$ keV (section [4.1.2](#sec-simmodel)). The measured temperatures tend to decrease moderately towards the center, in agreement with the average profile of high-redshift cool-core clusters. This is also consistent with the fact that the observed $y$-parameter profile of RCS J2319$+$0038 is better reproduced by a steeper pressure profile than the average of non-cool-core clusters at $0.6<z<1.2$ (figure [12](#fig-yprof) and table [\[tab-yfit\]](#tab-yfit)).

The associated electron density profile is plotted in figure [13](#fig-deproj)(b). It agrees well with the isothermal $\beta$ model obtained solely from the X-ray data in section [4.1.2](#sec-simmodel), which provides a useful consistency test of the present technique. The electron density profile of RCS J2319$+$0038 with $n_{\rm e0} \simeq 1.4 \times 10^{-2}$ cm$^{-3}$ and $r_{\rm
c}\simeq 100$ kpc is shallower than the average of cool-core clusters at $0.2<z<1.9$ characterized by $n_{\rm e0} > 1.5 \times 10^{-2}$ cm$^{-3}$ and $r_{\rm c} \simeq 20-30$ kpc (cite: McDonald17).

Figure [13](#fig-deproj)(c) illustrates that the entropy decreases moderately to $\sim 80$ keV cm$^2$ within the core ($\theta_{\rm c} \simeq 13''$ or 100 kpc). Also plotted are a model $K\propto r^{1.2}$ which tends to give a lower limit to non-radiative clusters at $r \ltsim 0.5 r_{500}$ (cite: Voit05) and a prediction $K\propto r^{1.4}$ for the steady-state cooling flow (cite: Voit11); both profiles are normalized to match the data point in the outer-most bin. The observed entropy profile shows a better agreement with $K\propto r^{1.2}$ than $K\propto r^{1.4}$ indicating that radiative cooling, if any, is modest in RCS J2319$+$0038.

Figure [13](#fig-deproj)(d) further shows that the radiative cooling time in the core is about half the age of the Universe ($\sim 6$ Gyr) at $z=0.9$. The radial profile of the cooling time is represented approximately by a power-law of $t_{\rm cool} \propto
r^{1.2}$. This is shallower than $t_{\rm cool} \propto r^{1.7}$ obtained from a similar analysis for the Phoenix cluster at $z=0.60$ (cite: Kitayama20), in which efficient radiative cooling is suggested.

## Origin of the offset of the ACT SZE centroid of RCS J2319$+$0038

The centroid position of RCS J2319$+$0038 in the ACT SZE map is offset to the north-west direction by $\sim 30''$ (230 $h_{70}^{-1}$kpc) from the centers of the ALMA SZE and the *Chandra* X-ray images (figure [3](#fig-xszJ2319)). We examined if this offset is due to the compact millimeter sources (table [\[tab-source1\]](#tab-source1)) unresolved in the ACT map, by means of cluster injection simulations similar to those done in (cite: Hilton21).

We injected a model cluster and model sources to the real ACT map, re-ran filtering and cluster-detection procedures, and assessed the accuracy of the recovered cluster position. The compact sources listed in table [\[tab-source1\]](#tab-source1) were found to be far too weak to produce the observed offset. The result is consistent with the fact that, according to figure 5 of (cite: Dicker21), these sources would have changed the peak Compton $y$-parameter of RCS J2319$+$0038 in the ACT map ($\tilde{y}_0=(6.1 \pm 1.2)\times 10^{-5}$ in (cite: Hilton21)) by at most $4\%$ for a spectral index of $-0.7$. Figure 4 of (cite: Hilton21) further indicates that the accuracy of position recovery in the ACT SZE maps is sensitive to S/N and governed by the fluctuating cosmic microwave background (CMB). At the S/N of 5.2 for RCS J2319$+$0038, 22% of the injected clusters in the simulations are recovered at $> 30''$ away from the position at which the cluster model was inserted. We thus conclude that the observed offset in the ACT SZE map of RCS J2319$+$0038 is statistically insignificant and likely due to the primary CMB fluctuations.

We note that HSC J0947$-$0119 was detected by ACT with a higher S/N of 13.2 and exhibits agreement between the ACT and ALMA centroids (figure [4](#fig-szJ0947)). This also supports the above interpretation that the position accuracy of the ACT SZE maps correlates with S/N.

# Conclusions

We have presented ALMA Band 3 measurements of the thermal SZE toward two galaxy clusters at $z\sim 1$, RCS J2319$+$0038 and HSC J0947$-$0119, and performed joint analyses with available *Chandra* X-ray data, optical data taken by Subaru/HSC, and wider-field SZE data by ACT. Taking into account departures from spherical symmetry, we have reconstructed the profiles of thermodynamic quantities non-parametrically. This is one of the first such measurements for an individual cluster at $z\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}0.9$.

In both clusters, the SZE is imaged at $5''$ resolution (corresponding to the physical scale of $\sim 40 h_{70}^{-1}$kpc) within 300 $h_{70}^{-1}$kpc from the cluster center with the peak S/N exceeding $7$. The overall morphology of the SZE signal is well described by an elliptical gas profile with axis ratio $\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}0.7$, clearly differing from unity. The elongated morphology is probably associated with highly asymmetrical galaxy distributions found in these clusters. The inner pressure profile is consistent with the average of clusters at $0.6<z <1.2$ by (cite: McDonald14b) and is much shallower than that of local cool-core clusters by (cite: Arnaud10).

Of the two clusters studied in this paper, high quality X-ray data are available only for RCS J2319$+$0038. Both the centroid position and overall morphology of the ALMA SZE map are in agreement with those of the *Chandra* X-ray brightness image. We thus performed a non-parametric deprojection of electron temperature, density, entropy, and the radiative cooling time, combining SZE and X-ray images for RCS J2319$+$0038. Our results consistently indicate that RCS J2319$+$0038 hosts a weak cool core, where radiative cooling is less significant than in local cool cores. There are central radio sources as well as signs of subcluster mergers. We also suggest that the offset of the ACT SZE centroid position seen in this cluster (cite: Hilton21) is likely due to primary CMB fluctuations.

On the other hand, HSC J0947$-$0119 exhibits an even shallower pressure profile than RCS J2319$+$0038 and is more likely a non-cool-core cluster. The SZE centroid position is offset from the peaks of galaxy concentration by more than 140 $h_{70}^{-1}$ kpc, suggesting stronger impacts of mergers in this cluster than in RCS J2319$+$0038. No radio galaxies are found within 100 $h_{70}^{-1}$ kpc from either the SZE centroid or the peaks of galaxy concentration. Additional X-ray observations will be quite useful for exploring the nature of this cluster further.

We conclude that both of these distant clusters are at a very early stage of developing the cool cores typically found in clusters at lower redshifts. Our results also imply that high angular resolution SZE observations provide a unique probe of thermodynamic structures of such clusters. We have developed an image domain analysis that allows for a non-parametric reconstruction of physical quantities from the ALMA data. An alternative and complementary approach is to perform model fitting in the visibility ($uv$) domain (e.g., (cite: Basu16; Luca19AA)), which we plan to investigate in our future publication. We expect that spectral and spatial ranges covered in future studies will be greatly enhanced by new facilities including the Band 1 receiver on ALMA (cite: Huang16), the Large Submillimeter Telescope (LST; (cite: Kawabe16)), and the Atacama Large Aperture Submillimeter/millimeter Telescope (AtLAST; (cite: Klaassen19)).

We thank Grace Chesmore, Arthur Kosowsky, and Bruce Partridge for helpful comments. We also thank the anonymous referee for careful reading of the manuscript and insightful comments. We are grateful to Daniel Espada, Atsushi Miyazaki, and Kazuya Saigo for their support on the ALMA data analysis. This work was supported by JSPS KAKENHI Grant Numbers JP17H06130 (K.K.), JP18K03704 (T.K.), JP20H00181 (M.O.), JP20H01932 (H.M.), JP20H05856 (M.O.), JP20K04012 (N.O.), JP21H00048 (S.T.), JP21H01135 (T.A.), JP21H04495 (S.T.), and JP22H01260 (M.O.). S.U. acknowledges the support from Ministry of Science and Technology of Taiwan (MOST 111-2811-M-007-008 and 111-2112-M-001-026-MY3). J.P.H. acknowledges funding for SZE cluster studies from the NSF AAG program (grant number AST-1615657).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00680.S and 2019.1.00673.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This research has made use of data obtained from the *Chandra* Data Archive (ObsID 5750, 7172, 7173, and 7174) and software provided by the Chandra X-ray Center (CXC) in the application packages CIAO and Sherpa.

The Hyper Suprime-Cam (HSC) collaboration includes the astronomical communities of Japan and Taiwan, and Princeton University. The HSC instrumentation and software were developed by the National Astronomical Observatory of Japan (NAOJ), the Kavli Institute for the Physics and Mathematics of the Universe (Kavli IPMU), the University of Tokyo, the High Energy Accelerator Research Organization (KEK), the Academia Sinica Institute for Astronomy and Astrophysics in Taiwan (ASIAA), and Princeton University. Funding was contributed by the FIRST program from the Japanese Cabinet Office, the Ministry of Education, Culture, Sports, Science and Technology (MEXT), the Japan Society for the Promotion of Science (JSPS), Japan Science and Technology Agency (JST), the Toray Science Foundation, NAOJ, Kavli IPMU, KEK, ASIAA, and Princeton University.

This paper makes use of software developed for Vera C. Rubin Observatory. We thank the Rubin Observatory for making their code available as free software at http://pipelines.lsst.io/.

This paper is based on data collected at the Subaru Telescope and retrieved from the HSC data archive system, which is operated by the Subaru Telescope and Astronomy Data Center (ADC) at NAOJ. Data analysis was in part carried out with the cooperation of Center for Computational Astrophysics (CfCA), NAOJ. We are honored and grateful for the opportunity of observing the Universe from Maunakea, which has the cultural, historical and natural significance in Hawaii.

# Line emissions from compact sources

The ALMA Band 3 data presented in the present paper have a spectral resolution of $15.6$ MHz and can be used for probing line emissions from galaxies in the field-of-views. We find that sources W and W1 toward RCS J2319$+$0038 and HSC J0947$-$0119, respectively, host line emissions as listed in table [\[tab-lines\]](#tab-lines). The position and the flux density are determined by fitting the visibility at $>15$ k$\lambda$ over the frequency range shown in table [\[tab-lines\]](#tab-lines) using the CASA task *uvmodelfit*. We also plot in figure [14](#fig-lines) the spectra within a diameter of $7''$ around the source position. Note that the continuum flux density of sources W and W1 in tables [\[tab-source1\]](#tab-source1) and [\[tab-source2\]](#tab-source2), respectively, are obtained excluding the frequency ranges listed in table [\[tab-lines\]](#tab-lines). The short baselines ($<15$ k$\lambda$) are excluded in the fit to eliminate possible contamination from the SZE signal. The line and continuum components so determined are subtracted from the visibility to construct the SZE maps shown in this paper. We have checked that there is no other line emission in the field-of-views that would alter the detected SZE signal of RCS J2319$+$0038 and HSC J0947$-$0119.

The position of the line(s) at $97.8-98.2$ GHz (W-b) agrees with that of source W in table [\[tab-source1\]](#tab-source1) within $0.1''$. On the other hand, the line at $85.0-85.3$ GHz (W-a) lies at $\sim 2''$ south-west of W-b and may be due to a different object from W and W-b. The line at $87.0-87.3$ GHz (W1-a) lies at $\sim 1''$ west of source W1.

It is difficult to determine the redshifts of the sources by a single emission line. For example, their ranges are $z = 1.3 \sim 1.7$ and $2.5 \sim  3.1$ if the line is from CO(2-1) at 230.54 GHz and CO(3-2) at 345.80 GHz, respectively. Detailed nature of these sources is beyond the scope of this paper and will be investigated elsewhere.

| Field | ID | $\nu$ \[GHz\] | RA (J2000) | Dec (J2000) | Integrated flux density \[Jy km/s\] |
|:--:|:--:|:--:|:--:|:--:|:--:|
| RCS J2319$+$0038 | W-a | $85.0-85.3$ |  |  | $0.76 \pm 0.03$ |
|  | W-b | $97.8-98.2$ |  |  | $^*1.64 \pm 0.03$ |
| HSC J0947$-$0119 | W1-a | $87.0-87.3$ |  |  | $1.06 \pm 0.02$ |

$^*$ The flux density over the frequency gap at 98.028–98.060 GHz (figure [14](#fig-lines) top-right) is excluded. It is not relevant to the analysis of this paper.

![image](figs/J2319_Wa.eps) ![image](figs/J2319_Wb.eps) ![image](figs/J0947_W1a.eps) ![image](figs/J0947_W1b.eps)

104 natexlab

(ref: SDSS17) Abdurro’uf, Accetta, K., Aerts, C., et al. 2022, ApJS, 259, 35

(ref: Adam15) Adam, R., Comis, B., Macı́as-Pérez, J. F., et al. 2015, A&A, 576, A12

(ref: Adam18) Adam, R., Hahn, O., Ruppin, F., et al. 2018, A&A, 614, A118

(ref: Aihara18a) Aihara, H., Armstrong, R., Bickerton, S., et al. 2018a, PASJ, 70, S8

(ref: Aihara18b) Aihara, H., Arimoto, N., Armstrong, R., et al. 2018b, PASJ, 70, S4

(ref: Aihara19) Aihara, H., AlSayyad, Y., Ando, M., et al. 2019, PASJ, 71, 114

(ref: Aihara22) —. 2022, PASJ, 74, 247

(ref: Anders89) Anders, E., & Grevesse, N. 1989, , 53, 197

(ref: Andreon21) Andreon, S., Romero, C., Castagna, F., et al. 2021, MNRAS, 505, 5896

(ref: Arnaud96) Arnaud, K. A. 1996, in Astronomical Society of the Pacific Conference Series, Vol. 101, Astronomical Data Analysis Software and Systems V, ed. G. H. Jacoby & J. Barnes, 17

(ref: Arnaud10) Arnaud, M., Pratt, G. W., Piffaretti, R., et al. 2010, A&A, 517, A92

(ref: Asplund09) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481

(ref: Bartalucci17) Bartalucci, I., Arnaud, M., Pratt, G. W., et al. 2017, A&A, 598, A61

(ref: Basu16) Basu, K., Sommer, M., Erler, J., et al. 2016, ApJL, 829, L23

(ref: Bauer05) Bauer, F. E., Fabian, A. C., Sanders, J. S., Allen, S. W., & Johnstone, R. M. 2005, MNRAS, 359, 1481

(ref: Becker95) Becker, R. H., White, R. L., & Helfand, D. J. 1995, ApJ, 450, 559

(ref: Ftools95) Blackburn, J. K. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 367

(ref: Ftools99) Blackburn, J. K., Shaw, R. A., Payne, H. E., Hayes, J. J. E., & Heasarc. 1999, FTOOLS: A general package of software to manipulate FITS files, Astrophysics Source Code Library, record ascl:9912.002

(ref: Spt15) Bleem, L. E., Stalder, B., de Haan, T., et al. 2015, ApJS, 216, 27

(ref: Bohringer10) Böhringer, H., & Werner, N. 2010, A&ARv, 18, 127

(ref: Bosch18) Bosch, J., Armstrong, R., Bickerton, S., et al. 2018, PASJ, 70, S5

(ref: Brodwin16) Brodwin, M., McDonald, M., Gonzalez, A. H., et al. 2016, ApJ, 817, 122

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Cavaliere13) Cavaliere, A., & Lapi, A. 2013, Phys. Rep., 533, 69

(ref: Condon97) Condon, J. J. 1997, PASP, 109, 166

(ref: Cornwell08) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793

(ref: Coupon18) Coupon, J., Czakon, N., Bosch, J., et al. 2018, PASJ, 70, S7

(ref: Luca19AA) Di Mascolo, L., Mroczkowski, T., Churazov, E., et al. 2019, A&A, 628, A100

(ref: Luca20) —. 2020, A&A, 638, A70

(ref: Luca21) Di Mascolo, L., Mroczkowski, T., Perrott, Y., et al. 2021, A&A, 650, A153

(ref: Dicker20) Dicker, S. R., Romero, C. E., Di Mascolo, L., et al. 2020, ApJ, 902, 144

(ref: Dicker21) Dicker, S. R., Battistelli, E. S., Bhandarkar, T., et al. 2021, MNRAS, 508, 2600

(ref: Diemer15) Diemer, B., & Kravtsov, A. V. 2015, ApJ, 799, 108

(ref: Sherpa07) Doe, S., Nguyen, D., Stawarz, C., et al. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 543

(ref: Donahue16) Donahue, M., Ettori, S., Rasia, E., et al. 2016, ApJ, 819, 36

(ref: Sherpa01) Freeman, P., Doe, S., & Siemiginowska, A. 2001, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4477, Astronomical Data Analysis, ed. J.-L. Starck & F. D. Murtagh, 76–87

(ref: Fruscione06) Fruscione, A., McDowell, J. C., Allen, G. E., et al. 2006, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 6270, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, ed. D. R. Silva & R. E. Doxsey, 62701V

(ref: Furusawa18) Furusawa, H., Koike, M., Takata, T., et al. 2018, PASJ, 70, S3

(ref: Ghirardini21) Ghirardini, V., Bulbul, E., Kraft, R., et al. 2021, ApJ, 910, 14

(ref: Gilbank08) Gilbank, D. G., Yee, H. K. C., Ellingson, E., et al. 2008, ApJL, 677, L89

(ref: Gladders05) Gladders, M. D., & Yee, H. K. C. 2005, ApJS, 157, 1

(ref: Gobat19) Gobat, R., Daddi, E., Coogan, R. T., et al. 2019, A&A, 629, A104

(ref: Gordon21) Gordon, Y. A., Boyce, M. M., O’Dea, C. P., et al. 2021, ApJS, 255, 30

(ref: Act13a) Hasselfield, M., Hilton, M., Marriage, T. A., et al. 2013, J. Cosm. Astropart. Phys., 2013, 008

(ref: HI4PI16) HI4PI Collaboration, Ben Bekhti, N., Flöer, L., et al. 2016, A&A, 594, A116

(ref: Hicks08) Hicks, A. K., Ellingson, E., Bautz, M., et al. 2008, ApJ, 680, 1022

(ref: Hilton18) Hilton, M., Hasselfield, M., Sifón, C., et al. 2018, ApJS, 235, 20

(ref: Hilton21) Hilton, M., Sifón, C., Naess, S., et al. 2021, ApJS, 253, 3

(ref: Act10) Hincks, A. D., Acquaviva, V., Ade, P. A. R., et al. 2010, ApJS, 191, 423

(ref: Hirata03) Hirata, C., & Seljak, U. 2003, MNRAS, 343, 459

(ref: Huang20) Huang, N., Bleem, L. E., Stalder, B., et al. 2020, AJ, 159, 110

(ref: Huang18) Huang, S., Leauthaud, A., Murata, R., et al. 2018, PASJ, 70, S6

(ref: Huang16) Huang, Y. D. T., Morata, O., Koch, P. M., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9911, Modeling, Systems Engineering, and Project Management for Astronomy VI, ed. G. Z. Angeli & P. Dierickx, 99111V

(ref: Itoh04) Itoh, N., & Nozawa, S. 2004, A&A, 417, 827

(ref: Kaastra96) Kaastra, J. S., Mewe, R., & Nieuwenhuijzen, H. 1996, in UV and X-ray Spectroscopy of Astrophysical and Laboratory Plasmas, 411–414

(ref: Kaastra20) Kaastra, J. S., Raassen, A. J. J., de Plaa, J., & Gu, L. 2020, SPEX X-ray spectral fitting package, Zenodo, 10.5281/zenodo.4384188

(ref: Kawabe16) Kawabe, R., Kohno, K., Tamura, Y., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9906, Ground-based and Airborne Telescopes VI, ed. H. J. Hall, R. Gilmozzi, & H. K. Marshall, 990626

(ref: Kawahara10) Kawahara, H. 2010, ApJ, 719, 1926

(ref: Kawanomoto18) Kawanomoto, S., Uraguchi, F., Komiyama, Y., et al. 2018, PASJ, 70, 66

(ref: Kitayama16) Kitayama, T., Ueda, S., Takakuwa, S., et al. 2016, PASJ, 68, 88

(ref: Kitayama20) Kitayama, T., Ueda, S., Akahori, T., et al. 2020, PASJ, 72, 33

(ref: Klaassen19) Klaassen, P., Mroczkowski, T., Bryan, S., et al. 2019, in Bulletin of the American Astronomical Society, Vol. 51, 58

(ref: Komiyama18) Komiyama, Y., Obuchi, Y., Nakaya, H., et al. 2018, PASJ, 70, S2

(ref: Korngut11) Korngut, P. M., Dicker, S. R., Reese, E. D., et al. 2011, ApJ, 734, 10

(ref: Li22) Li, X., Miyatake, H., Luo, W., et al. 2022, PASJ, 74, 421

(ref: Mandelbaum18) Mandelbaum, R., Miyatake, H., Hamana, T., et al. 2018, PASJ, 70, S25

(ref: Mantz20) Mantz, A. B., Allen, S. W., Morris, R. G., et al. 2020, MNRAS, 496, 1554

(ref: Act11) Marriage, T. A., Acquaviva, V., Ade, P. A. R., et al. 2011, ApJ, 737, 61

(ref: Mason20) Mason, B. S. 2020, arXiv e-prints, arXiv:2006.06549

(ref: McDonald14b) McDonald, M., Benson, B. A., Vikhlinin, A., et al. 2014, ApJ, 794, 67

(ref: McDonald17) McDonald, M., Allen, S. W., Bayliss, M., et al. 2017, ApJ, 843, 28

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Medezinski18) Medezinski, E., Oguri, M., Nishizawa, A. J., et al. 2018, PASJ, 70, 30

(ref: Miyazaki18) Miyazaki, S., Komiyama, Y., Kawanomoto, S., et al. 2018, PASJ, 70, S1

(ref: Mroczkowski19) Mroczkowski, T., Nagai, D., Basu, K., et al. 2019, Space Sci. Rev., 215, 17

(ref: Naess20) Naess, S., Aiola, S., Austermann, J. E., et al. 2020, J. Cosm. Astropart. Phys., 2020, 046

(ref: Nagai07) Nagai, D., Kravtsov, A. V., & Vikhlinin, A. 2007, ApJ, 668, 1

(ref: Ftools14) NASA High Energy Astrophysics Science Archive Research Center (Heasarc). 2014, HEAsoft: Unified Release of FTOOLS and XANADU, Astrophysics Source Code Library, record ascl:1408.004

(ref: Navarro96) Navarro, J. F., Frenk, C. S., & White, S. D. M. 1996, ApJ, 462, 563

(ref: Oguri14) Oguri, M. 2014, MNRAS, 444, 147

(ref: Oguri18) Oguri, M., Lin, Y.-T., Lin, S.-C., et al. 2018, PASJ, 70, S20

(ref: Okabe19) Okabe, N., Oguri, M., Akamatsu, H., et al. 2019, PASJ, 71, 79

(ref: Okabe21) Okabe, N., Dicker, S., Eckert, D., et al. 2021, MNRAS, 501, 1701

(ref: Peres98) Peres, C. B., Fabian, A. C., Edge, A. C., et al. 1998, MNRAS, 298, 416

(ref: Planck20) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: Sherpa09) Refsdal, B. L., Doe, S. M., Nguyen, D. T., et al. 2009, in Proceedings of the 8th Python in Science Conference, 51

(ref: Spt13) Reichardt, C. L., Stalder, B., Bleem, L. E., et al. 2013, ApJ, 763, 127

(ref: Reichert11) Reichert, A., Böhringer, H., Fassbender, R., & Mühlegger, M. 2011, A&A, 535, A4

(ref: Rich08) Rich, J. W., de Blok, W. J. G., Cornwell, T. J., et al. 2008, AJ, 136, 2897

(ref: Sanders18) Sanders, J. S., Fabian, A. C., Russell, H. R., & Walker, S. A. 2018, MNRAS, 474, 1065

(ref: Santos12) Santos, J. S., Tozzi, P., Rosati, P., Nonino, M., & Giovannini, G. 2012, A&A, 539, A105

(ref: Schure09) Schure, K. M., Kosenko, D., Kaastra, J. S., Keppens, R., & Vink, J. 2009, A&A, 508, 751

(ref: Spt09) Staniszewski, Z., Ade, P. A. R., Aird, K. A., et al. 2009, ApJ, 701, 32

(ref: Steeb19) Steeb, J.-W. W., & Rau, U. 2019, CASA Memo, 9

(ref: Sunyaev70) Sunyaev, R. A., & Zeldovich, Y. B. 1970, Comments on Astrophysics and Space Physics, 2, 66

(ref: Sunyaev72) —. 1972, Comments on Astrophysics and Space Physics, 4, 173

(ref: Tanaka15) Tanaka, M. 2015, ApJ, 801, 20

(ref: Tanaka18) Tanaka, M., Coupon, J., Hsieh, B.-C., et al. 2018, PASJ, 70, S9

(ref: Tozzi15) Tozzi, P., Santos, J. S., Jee, M. J., et al. 2015, ApJ, 799, 93

(ref: Spt10) Vanderlinde, K., Crawford, T. M., de Haan, T., et al. 2010, ApJ, 722, 1180

(ref: Verde19) Verde, L., Treu, T., & Riess, A. G. 2019, Nature Astronomy, 3, 891

(ref: Voit11) Voit, G. M. 2011, ApJ, 740, 28

(ref: Voit05) Voit, G. M., Kay, S. T., & Bryan, G. L. 2005, MNRAS, 364, 909

(ref: Spt11) Williamson, R., Benson, B. A., High, F. W., et al. 2011, ApJ, 738, 139

[^1]: https://lambda.gsfc.nasa.gov/product/act/actadv_prod_table.html

[^2]: $z=1.11$ is consistent with spectroscopic redshift obtained for several members from Magellan/LDSS3; however, our observations also suggest possible galaxy concentrations along the line-of-sight; we are in the process of obtaining more spectroscopic redshifts in this field.

[^3]: https://hsc-release.mtk.nao.ac.jp/doc/

[^4]: We checked that this simplification has no apparent effect on the results of the present paper. For the brightest source (C1 in table [\[tab-source1\]](#tab-source1)), adopting the flux density fitted separately at 85, 87, 97, and 99 GHz for subtraction would change the residual signal at the source position by less than 1/5 of the noise level.

[^5]: https://heasarc.gsfc.nasa.gov/ftools/

[^6]: S19A is an internal data release between the second and the third public data releases of HSC-SSP.

[^7]: http://sundog.stsci.edu/

[^8]: https://third.ucllnl.org/cgi-bin/firstcutout

[^9]: http://cutouts.cirada.ca/

[^10]: http://skyserver.sdss.org/dr17

[^11]: In this paper, the position angle is measured for the major axis of an ellipse from north ($0^\circ$) through east ($90^\circ$).

[^12]: $M_{500}$ is defined as the total mass enclosed in the radius $R_{500}$, within which the average matter density is 500 times the critical density of the Universe.

[^13]: Our subsequent analysis is insensitive to this simplification. We checked that adopting a mean temperature profile for high redshift clusters (cite: McDonald14b) in the input model would change the value of $c_1$ in table [\[tab-conv\]](#tab-conv) only within its error range. We will also show in section [4.4](#sec-deproj) that a weak temperature gradient is inferred from the joint analysis of the SZE and the X-ray data of RCS J2319$+$0038, whereas the gas density profile still follows equation ([\[eq-nbeta\]](#eq-nbeta)).

[^14]: The mass quoted here is $M_{500c}^{\rm UPP}$ in (cite: Hilton21).

[^15]: We checked that the deprojected quantities at $\bar{\theta} < 20''$ (160 kpc) are insensitive to this assumption; they change within $\pm 3\%$ if the temperature at $\bar{\theta} > 30''$ is varied within the $1\sigma$ error range of $5.90^{+0.79}_{-0.62}$ keV.

</paper>

Write the methods card for this paper.