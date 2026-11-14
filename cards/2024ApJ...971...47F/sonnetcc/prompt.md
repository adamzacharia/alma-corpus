# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...971...47F\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...971...47F",
 "title": "Dead or Alive? How Bursty Star Formation and Patchy Dust Can Cause Temporary Quiescence in High-redshift Galaxies",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Faisst, Andreas L.",
 "n_authors": 2,
 "arxiv_id": "2402.13316",
 "doi": "10.3847/1538-4357/ad58e2",
 "alma_projects_linked_by_archive": [
  "2023.1.00521.S"
 ]
}
```

Paper text:
<paper>
# Dead or Alive? How Bursty Star Formation and\
Patchy Dust Can Cause Temporary Quiescence in High Redshift Galaxies

## Abstract

The recent discovery of a galaxy at $z=7.3$ with undetected optical emission lines and a blue UV to optical continuum ratio in JWST spectroscopy is surprising and needs to be explained physically. Here, we explore two possibilities that could cause such a seemingly quiescent $\sim5\times10^8\,{\rm M_\odot}$ galaxy in the early Universe: *(i)* stochastic variations in the star formation history (SFH) and *(ii)* the effect of spatially varying dust attenuation on the measured line and continuum emission properties. Both scenarios can play at the same time to amplify the effect. A stochastic star formation model (similar to realistic SFHs from hydrodynamical simulations of similar-mass galaxies) can create such observed properties if star formation is fast-varying with a correlation time of $<150\,{\rm Myrs}$ given a reasonable burst amplitude of $\sim 0.6\,{\rm dex}$. The total time spent in this state is less than $20\,{\rm Myrs}$, and the likelihood of such a state to occur over $500\,{\rm Myrs}$ at $z=7$ is $\sim50\%$ (consistent with current observations). On the other hand, we show that a spectrum with blue UV continuum and lack of emission lines can be reproduced by a blue$+$red composite spectrum. The UV continuum is emitted from dust-free density bounded H II regions (blue component), while the red component is a dust-obscured starburst with weakened emission lines due to strong differential dust attenuation between stellar and nebular emission. Future resolving far-infrared observations with ALMA will shed light on the latter scenario.

# Introduction

Galaxies spend a significant amount of their lives on the star forming main-sequence (cite: noeske07; daddi07), a tight $\sim0.3\,{\rm dex}$ relation between stellar mass and star formation rate (SFR). This relation is maintained by an equilibrium between gas inflow, gas consumption through star formation, and gas removal through outflow (e.g., stellar winds, Supernovae, or Active Galactic Nuclei \[AGN\]), as explained by simple analytical models (cite: dave12; lilly13; feldmann15). After the peak of cosmic star formation rate density at $z\sim2$ (cite: madau14) an increasing number of quiescent galaxies is observed, which deviate from the star-forming main sequence by a significantly reduced star formation (cite: ilbert10; abraham07; bell04). Quiescent galaxies are mainly characterized by their red colors and strong Balmer or $4000\,{\rm \AA}$ breaks due to 50 Myr or older populations as well as the lack of emission lines signaling the lack of recent star formation. More quantitatively, the state of quiescence can be defined as a galaxy having a specific star formation rate (sSFR) below a certain threshold. It is found that a sSFR threshold of $0.2/t_{\rm univ}(z)\,{\rm Gyr^{-1}}$ (where $t_{\rm univ}(z)$ is the age of the Universe at redshift $z$) is consistent with various color selections (cite: pacifici16; faisst17). The probability of being quiescent depends on the environment and stellar (halo) mass of a galaxy (cite: peng10). Quenching can happen through many avenues, for example by gas shock-heating in the most massive dark matter halos (cite: croton06; cattaneo08) and interactions with starbursts or feedback from AGN and Supernovae (cite: toomre72; haas13; schawinski14).

While the quiescent galaxy population is established at $z<2$, there are open questions regarding their progenitors and when and how the first quiescent galaxies emerge. With the advent of sensitive infrared detectors and surely the launch of the *James Webb Space Telescope* (JWST), it became feasible to spectroscopically confirm quiescent galaxies at to Epoch of Reionization at $z=6$ (cite: glazebrook17; schreiber18; tanaka19; forrest20; valentino20; eugenio21; kubo21; nanayakkara22; carnall23a; carnall23b; valentino23; looser23). Most of these findings are massive galaxies ($\gtrsim 10^{10}\,{\rm M_\odot}$) that are thought to be quiescent for many $100\,{\rm Myrs}$ to a Gyr. However, the fate of less massive quiescent galaxies is unclear because their star formation is suggested to significantly oscillate around the equilibrium state (*i.e.* the main sequence) due to the continuous adjusting between gas supply and consumption, hence leading to “temporary quiescence” (cite: tacchella16). It is also suggested by simulations (cite: remus23) that quiescent galaxies can be rejuvenated leading to star formation in the outer disk.

An interesting exception is the finding of a recently quenched galaxy (in the following *JADES-GS-z7-01-QU*) at a spectroscopic redshift of $z=7.3$ reported by (cite: looser23). The galaxy is curious as it is lacking optical emission lines and at the same time shows a blue UV to optical flux ratio in the present JWST/NIRSpec spectra. A quiescent galaxy at such a high redshift (where commonly a significant amount of molecular gas is available) may be surprising. Mass quenching is likely not applicable due to the lower masses of dark-matter halos at those epochs, instead feedback or variations in the star formation history (SFH) of the galaxy are more likely. The lack of optical line emission suggests the lack star formation in the past $\sim10\,{\rm Myrs}$, indicative of a short-term variation in the SFH of this galaxy (cite: kennicutt98). Furthermore, the galaxy shows a blue UV to optical flux ratio of $\sim 3$ (in $\lambda f_{\rm \lambda}$), indicative of young stars and/or low stellar continuum dust obscuration. Since the galaxy is at a relatively low stellar mass ($\sim 5\times 10^8\,{\rm M_\odot}$), the most likely scenarios involve temporal quenching by star formation or AGN feedback (cite: gelli23; lovell23) or galaxy-galaxy interactions (cite: asada23). A recent study found that the most dominant quenching mechanisms for low-mass high-redshift galaxies may be accretion disk feedback triggered by disk instabilities (cite: xie24). Alternatively, an unlucky geometric distribution of dust along the line of sight could attenuate the nebular emission and mimic quiescence. In the meantime, similar galaxies have been found at $z\sim4.5$ (cite: looser23b) and some that are on the way to a quiescent state at $z\sim5.2$ (cite: strait23), in agreement with the bursty star formation expected at these redshifts (cite: faisst19).

![image](burst_model_example_final.pdf) ![image](UVJ_final.pdf)

Several studies tried to explain the nature of JADES-GS-z7-01-QU, specifically the combination of a blue UV to optical flux ratio and the absence of optical emission lines. Simulations can explain quiescent galaxies and their number densities in the Epoch of Reionization (cite: dome23; vikaeus23; lovell23; gelli23; pallottini23), and temporal quiescence is also expected given the burstiness of star formation especially at lower stellar masses at high redshifts (cite: dome23; sun23a; sun23b; abramson20; faisst19; sparre17; kelson14). However, the exact spectral energy distribution (SED) of JADES-GS-z7-01-QU could not be reproduced so far (cite: gelli23).

In this study, we aim at explaining the observation of a galaxy such as JADES-GS-z7-01-QU by two (not mutually exclusive) ideas: *(i)* the stochastic variations in the SFH of high-$z$ galaxies (Section [2](#sec:stoch)), and *(ii)* spatial variations in the dust attenuation (Section [3](#sec:dust)). We assume a $\Lambda$CDM cosmology with $H_0 = 70\,{\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_\Lambda = 0.7$, and $\Omega_{\rm m} = 0.3$. Magnitudes are given in the AB system (cite: oke74), and stellar masses and SFRs are normalized to a (cite: chabrier03) initial mass function (IMF).

# Quiescence in Stochastic Star Formation Histories

In this section, we study the properties of JADES-GS-z7-01-QU under the assumption that the galaxy follows a stochastic SFHs. We want to recover the color properties as well as the lack of emission lines observed with JWST NIRCam and NIRSpec data. Specifically, we observe two conditions (cite: looser23):

#### **Condition 1.** 

 A conservative non-detection of optical emission lines, specifically \[O II\]$_{\rm \lambda 3727}$ and \[O III\]$_{\rm \lambda 5007}$ at no more than $3\sigma$ assuming a continuum signal-to-noise ratio (SNR) of $5$.

#### **Condition 2.** 

 A blue UV to optical $\lambda f_{\rm \lambda}$ flux ratio of $3\pm0.3$ as observed.

In the following, we show that these observed properties of JADES-GS-z7-01-QU can be reproduced after a starburst. We then move on to estimate the probability of such a scenario to happen within more complicated stochastic representations of SFHs.

## Single Starburst

The lack of optical emission lines is indicative of a lack of star formation in the past $\sim3-10\,{\rm Myrs}$. This condition can be reproduced by a single starburst (Figure [1](#fig:uvj_model)). Specifically, we assume a burst with a SFR of $10\,{\rm M_\odot\,yr^{-1}}$ and a length of $50\,{\rm Myrs}$ (indicated by the black hatched area). We assume that all mass is produced during that time, while any previous star formation only has negligible impacts on the results observed here. Furthermore, we do not assume dust attenuation in this simple model. The blue and red lines on the top-left panel in Figure [1](#fig:uvj_model) show the UV-to-optical flux ratio (condition 2) and the \[O III\] SNR (condition 1) in this scenario, respectively. The observed values are indicated as blue and red horizontal areas. Shortly ($\sim5\,{\rm Myrs}$) after the end of the burst, both conditions 1 and 2 are met. We note that the sharp drop in the \[O III\] line emission is due to the lack of ionizing flux of intermediate-age stars. The bottom-left panel shows a comparison of the model spectra at three different times after the burst to the observed spectrum in (cite: looser23). The right panel of Figure [1](#fig:uvj_model) shows the burst model with subsequent passive evolution (line) on the UVJ diagram. The corresponding \[O III\] SNR (proportional to the \[O III\] equivalent width) is shown in color and it drops to zero after the burst. This diagram is commonly used to separate star-forming from quiescent galaxies (cite: wuyts07). Assuming passive evolution, a galaxy would slowly evolve towards the quiescent regime (here maximum at $t_{\rm univ}(z=7.3) \sim 700\,{\rm Myrs}$). Note that dust attenuation moves colors to the upper right (red arrow), parallel to the dividing line between star formation and quiescence, hence this analysis is insensitive to the assumed dust attenuation. The observed colors of JADES-GS-z7-01-QU are shown by the large square, and they agree well with the burst$+$passive evolution model right at the end of the burst.

The above analysis shows that the conditions of JADES-GS-z7-01-QU can be explained right after a burst of star formation, and it assumes that the galaxy stays quiescent afterwards. It is suggested that star formation can be quenched for good in low-mass dark matter halos during the epoch of reionization, giving rise to quiescent dwarf galaxies in the present days (cite: bullock00; brown14). However, realistically, the SFH of galaxies at these masses is much more complex and a pure passive evolution after a burst is unlikely given the large gas abundances at those early times (however, see (cite: xie24) for theoretical evidence that most early quiescent galaxies stay quiescent for $\sim1\,{\rm Gyr}$). Dark matter halo related quenching is not effective at low masses. The question of how often such a scenario would occur in a more realistic stochastic SFH therefore arises. This is explored in the next sections.

## Stochastic Star Formation Histories

### Synthetic spectra derived from stochastic SFHs

The SFH of galaxies can be characterized by stochastic processes depending on feedback, inflow, and outflow of gas. This stochasticity will lead to starbursts and short periods of quiescence, potentially giving rise to JADES-GS-z7-01-QU as shown in Section [2.1](#sec:burst). Here, we use an approach similar to (cite: caplar19) to create model SFHs with different statistical properties. Specifically, we use the DELIGHTCURVESIMULATION Python package[^1] (cite: connolly16), which is based on the (cite: emmanoulopoulos13) light curve simulation algorithm. In the following, we assume a generalized power spectrum density (PSD) based on a damped random walk $$\begin{equation}
    {\rm PSD}(f) = \frac{\sigma^2}{1 + (\tau_{\rm break}\,f)^\alpha},
\end{equation}$$ where $f$ is the frequency (*i.e.* inverse time in Myrs), $\tau_{\rm break}$ is related to the decorrelation time scale of star formation over time, $\sigma$ is the long-term variability (or amplitude), and $\alpha$ describes the slope of the PSD ($\alpha=2$ corresponds to a damped random walk). Note that in the following $\sigma = \sigma_{\rm MS}$, the amplitude of star formation burstiness with respect to the main-sequence in dex, is assumed. SFHs are created by using the *Simulate_TK_Lightcurve* function using the (cite: timmer95) method and the above parameterization of the PSD. Synthetic spectra are derived using the Flexible Stellar Population Synthesis (cite: conroy09; conroy10) code[^2] by feeding it the stochastic SFHs obtained before. We enable emission lines (with $\log U = -2$), assume a $10-50\%$ solar metallicity of gas and stars (the exact value does not impact the following results), a (cite: chabrier03) IMF, and “Padova 1994” stellar evolutionary tracks (cite: bertelli94) together with a Basel Stellar Libary (cite: lejeune97; lejeune98; westera03) complemented by the empirical STELIB library (cite: leborgne03). We do not include additional “birth clouds” or diffuse dust emission in this model. Instead, we will add the effects of dust later when we extract the fluxes of the UV continuum and optical emission lines.

### How likely is it to observe JADES-GS-z7-01-QU?

For deriving a probability to observe a galaxy with similar properties as JADES-GS-z7-01-QU within a given time frame, we create several 1000 synthetic spectra for various $\tau_{\rm break}$ from 50 to 500 Myrs and $\sigma~=~0.4,0.6,0.8\,{\rm dex}$. Furthermore, we fix $\alpha=2$ (see (cite: caplar19) for observational evidence) and the redshift is assumed to be $z=7.3$. These spectra are then evaluated under the two conditions outlined above. If both conditions are satisfied, a suitable analog of JADES-GS-z7-01-QU has been found.

![image](fraction_alpha2_new.pdf)\
![image](time_spent_alpha2.pdf)

The number of $30\,{\rm Myr}$ time-slices that meet either condition 1 or both conditions $1+2$ are then computed within a $500\,{\rm Myr}$ time window to derive a probability of such a galaxy to occur over that time frame. The top panel in Figure [2](#fig:stochastic) summarizes this likelihood in per-cent for the different $\tau_{\rm break}$ and $\sigma_{\rm MS}$. Generally, we find that the likelihood to observe either condition *increases* with larger amplitude ($\sigma_{\rm MS}$), and *decreases* with increasing $\tau_{\rm break}$. This is not surprising $-$ high amplitudes are necessary to produce a blue UV continuum and short correlation timescales are needed to produce frequent fast drops in star formation on the timescale of the de-excitation of nebular emission lines (c.f. Section [2.1](#sec:burst)). Naturally, observing both a lack of emission lines *and* a blue UV to optical flux ratio is significantly less likely, which is the main difficulty in reconciling the observed properties of JADES-GS-z7-01-QU (cite: gelli23). We note that in the case of this analysis, $\tau_{\rm break}$ and $\sigma_{\rm MS}$ are degenerate. We can break this degeneracy by fixing $\sigma_{\rm MS}$, *i.e.* the burstiness of the star formation, which is a quantity that can be measured from observations. Assuming a fiducial $\sigma_{\rm MS} = 0.5-0.6\,{\rm dex}$ (cite: faisst19; looser23; popesso23; mehta23; cole23) the occurrence of a galaxy with properties similar to JADES-GS-z7-01-QU is most likely ($>50\%$) within $500\,{\rm Myrs}$ for a considerably varying SFH at a rate of $\tau_{\rm break} \lesssim 150\,{\rm Myrs}$.

The bottom panel of Figure [2](#fig:stochastic) shows the estimated time a galaxy would spend on average in either condition 1 or conditions $1+2$. This “quiescent time“ increases with $\tau_{\rm break}$ from $\sim 10\,{\rm Myrs}$ to over $50\,{\rm Myrs}$ in the case of condition 1. Imposing conditions $1+2$, the average time is $\sim10\,{\rm Myrs}$ in all cases. Note that this is an extremely short time scale in which the SFH variations must be aligned to produce the required properties.

Finally, the right panel of Figure [1](#fig:uvj_model) shows two stochastic models with different statistics on the UVJ diagram. More stochasticity (*i.e.* smaller $\tau_{\rm break}$) results in larger scatter (color-coded points), overlapping with the observed color of JADES-GS-z7-01-QU. Longer correlation timescales results in a narrower parameter space (underlying gray points), similarly to a more simple burst$+$passive evolution model.

![image](tau_break_recovery_varAlpha.pdf)\
![image](SPHINX_taubreak_examples.pdf)\
![image](fraction_time_spent_SPHINX.pdf)

![image](rgb.pdf) ![image](compositeSpec2_withobs.pdf)

### Comparison to Simulations at $z=7$

In the following, we use more realistic SFH histories from simulations from the newly released SPHINX$^{\rm 20}$ cosmological radiation hydrodynamic simulations (cite: katz23), which is the largest volume simulation ($20^3$ co-moving ${\rm Mpc^3}$ containing several thousands of star-forming galaxies at $z=6$) in the SPHINX suite (cite: rosdahl18; rosdahl22). The simulation models the large-scale process of cosmic reionization and the detailed physics of a multi-phase interstellar medium (ISM), and is therefore ideally suited for recovering the properties of galaxies at $z>6$. For more information on the details of this simulation, we refer to (cite: katz23).

We first compare the more realistic SFHs of SPHINX$^{\rm 20}$ to our stochastic models. For this, we extract the SFHs of all $177$ galaxies (or halos) in the $z=7$ redshift slice. The galaxies have similar stellar masses as JADES-GS-z7-01-QU, hence are ideal for comparing. The SFHs are then normalized to their mean SFR (fit by a 2-degree polynomial) to obtain an estimate for $\sigma_{\rm MS}$. The resulting normalized SFHs are then fit with the PSD model described in Section [2](#sec:stoch) to obtain a value for $\tau_{\rm break}$. The best-fit parameters for the $z=7$ SPHINX$^{\rm 20}$ population are $\sigma_{\rm MS} = 0.67\pm0.04\,{\rm dex}$, $\tau_{\rm break} = 202\pm117\,{\rm Myrs}$, and $\alpha=1.3\pm0.2$. We verified the fitting method by simulating several $100$ SFHs for various $\tau_{\rm break}$ and $\alpha$ parameters, which we fit with the same methods. As shown in the top panel of Figure [3](#fig:sphinxresults), we are able to recover the true $\tau_{\rm break}$ to better than $50\%$ uncertainty independent of the input $\alpha$ value. The middle panels of Figure [3](#fig:sphinxresults) shows examples of mean-normalized SPHINX$^{\rm 20}$ SFHs sorted by $\tau_{\rm break}$ obtained from our fits.

The resulting combination of $\sigma_{\rm MS}$ and $\tau_{\rm break}$ suggests that we would be likely to identify a galaxy with similar properties as JADES-GS-z7-01-QU in the SPHINX$^{\rm 20}$ volume. Indeed, we can calculate the probability in more detail, by simulating synthetic spectra from the SFHs of the SPHINX$^{\rm 20}$ galaxies directly, following the same recipe as outlined in Sections [2.2.1](#sec:syntspec) and  [2.2.2](#sec:occurrence). Doing so suggests that about $60-80\%$ of the simulated galaxies go through similar observed properties as JADES-GS-z7-01-QU  during their lifetime until $z=7$ (lower left panel, Figure [3](#fig:sphinxresults)). The average “quiescence time“ of galaxies with such observed properties is less than $20\,{\rm Myrs}$ on average (lower right panel).

Using these numbers from the SPHINX$^{\rm 20}$ simulation, we can estimate the fraction of galaxies, which we would expect to observe in a phase similar to JADES-GS-z7-01-QU. For this, we assume that $70\%$ of galaxies go through a temporary quiescent within $500\,{\rm Myrs}$, and for each of them, the quiescent phase occurs on average twice within that time and lasts on average for $10\,{\rm Myrs}$. We perform a Monte Carlo sampling approach with the above assumptions and evaluate the likelihood that a galaxy is observed in a quiescent phase at $z=7$ based on 1000 samplings[^3]. Following this, we find a likelihood of $2.8\pm1.6\%$ to observe a galaxy similar to JADES-GS-z7-01-QU at $z=7$. In other words, about $30^{+47}_{-13}$ star-forming galaxies at $5\times10^{8}$ need to be surveyed in order to find a temporarily quiescent galaxy. This is roughly consistent with the work by (cite: looser23b) who find one so-called (mini-)quenched galaxy (*i.e.* JADES-GS-z7-01-QU) among $\sim40$ star-forming galaxies in the mass range of $10^6-10^9\,{\rm M_\odot}$ at $5<z<11$.

# Impact of Dust Attenuation on Observed Quiescence

In the previous section, we have studied how a stochastic SFH can lead to the observed properties of a galaxy like JADES-GS-z7-01-QU. Abrupt changes in the SFH are likely the dominant reason (cite: gelli23), however, a blue$+$red composite spectrum could reconcile these observations as well, as reasoned below.

Several studies based on ALMA observations suggest a significant fraction of dust in galaxies even at $z\sim7$ (cite: faisst20; fudamoto20; fudamoto21; inami22; mitsuhashi23). Furthermore, thanks to large ALMA surveys such as ALPINE (cite: lefevre20; bethermin20; faisst20b) and REBELS (cite: bouwens22), we have statistical evidence of spatial displacement between UV and far-IR emission in high-$z$ galaxies (cite: fudamoto21; jones20; bethermin23; devereaux23). This suggests distinct regions of high and low dust obscuration. Similar conditions have been observed in quiescent galaxies at later times (cite: morishita22; lee24; setton24).

In fact, there is observational evidence of a spatially variable dust attenuation in JADES-GS-z7-01-QU. The left panel of Figure [4](#fig:ebmvvar) shows a color composite based on the JWST/NIRCam filters F115W, F210M, and F410M. To generate this image, we fit the two components (visible in the blue filters, see insets) using `Galfit` (cite: galfitpeng10) with positional priors based on F115W. The model images are then convolved by the F115W PSF and combined to an RGB image. The color-composite shows a blue component (east), separated from the main redder component (west). The color gradient could indicate spatially variable dust obscuration inside the galaxy or a blue merger component.

In the following, we study whether the spectrum of JADES-GS-z7-01-QU could also be reconciled by a, possibly spatially unresolved, blue$+$red composite as shown on the right panel of Figure [4](#fig:ebmvvar). We model the blue component as a young ($40\,{\rm Myr}$), constant star-forming dust-free UV-emitting region that exhibits a high continuum escape fraction due to a density bounded nature. In such a setting, the ionizing radiation is escaping without producing significant nebular line emission (cite: rodriguez09; raiter10; topping22). The search for such blue systems is ongoing with JWST and a few candidates have been found at $z>7$ (see (cite: topping22) and references therein). The blue component would have a steep UV continuum with weak nebular emission. In contrast, the red component is modeled as a post-starburst $60\,{\rm Myr}$ old dust-obscured region (maybe a post-starburst). Attenuation from dust generally impacts nebular emission more than the stellar continuum. This differential dust attenuation factor[^4] can reach $\frac{1}{f} = \frac{1}{0.44} \sim 2.3$ (cite: calzetti00; kashino13; reddy15). Although $f$ is closer to unity at higher redshifts, a clumpy dust distribution can significantly alter this value and in the following we assume $f=0.44$ as worst case. Such a significantly dust obscured region could be devoid of emission lines (low $f$) and contributing little to the UV continuum.

The right panel of Figure [4](#fig:ebmvvar) shows a possible resulting spectra. Without dust attenuation, the red component contributes significantly to the emission lines of the composite spectrum (upper panel). If E(B-V) = 0.6 mag (lower panel), the composite spectrum is practically devoid of emission lines. However, note that due to the redder wavelength of H$\alpha$, this line should be detected (but in the case of JADES-GS-z7-01-QU it is outside of the JWST/NIRSpec wavelength range). This situation resembles the spectrum of the massive quiescent galaxy GS-9209 found at $z=4.7$ devoid of strong optical emission lines except AGN-broadened H$\alpha$ (cite: carnall23a), with some important differences. First, GS-9209 is two orders of magnitude more massive, and second, the galaxy likely did not have any significant star formation within the past $100\,{\rm Myrs}$.

By using this model, we can predict JWST/MIRI fluxes in F560W and F770W. By convolving the blue$+$red component with E(B-V) = 0.6 mag (lower right panel in Figure [4](#fig:ebmvvar)) with the corresponding filter curves, we find $m_{\rm F560W}=27.8$ and $m_{\rm F770W}=27.6$, respectively.

We note that generally the dust attenuation is expected to be low in low-mass high-redshift galaxies (cite: reddy23; sandles23), hence an E(B-V) of 0.6 mag is rare (but not unphysical as shown in the paragraph below). For example, based on dynamical mass measurements, the dust obscured galaxies found in (cite: fudamoto21) have stellar masses around $5\times10^{10}\,{\rm M_\odot}$ (although this may be an upper limit). Furthermore, the ALPINE galaxies are generally $>10^9\,{\rm M_\odot}$, thus at least a factor of two more massive than JADES-GS-z7-01-QU. Future observations with ALMA at rest-frame far-infrared wavelengths will be able to put solid constraints on its dust mass and obscured star formation.

![](ebmv_fext_variations_z7.pdf)

The SPHINX$^{\rm 20}$ simulation release provides a set of measurements along $10$ different sight lines for each of the simulated galaxies. We use the stellar continuum color excess E(B-V) measured along the different sight lines as an estimate of the patchiness of dust in these simulated $z=7$ galaxies. Specifically, we can study the impact dust attenuation on nebular emission lines by computing the attenuation factor (*i.e.* $10^{\frac{0.4}{f}\,{\rm E(B-V)}\,k^\prime(\lambda)}$) of \[O III\] along these sight lines. For $k^\prime(\lambda)$ we assume a starburst reddening curve (cite: calzetti00). Figure [5](#fig:ebmvvarsim) shows the variations of the \[O III\] attenuation factor as a function of median E(B-V) (measured over all 10 sight lines) for two differential dust attenuation values of $f=0.44$ (cite: calzetti00) and $0.7$ (cite: kashino13). This test shows that the attenuation of nebular emission lines can change by factors of a few depending on the line of sight. In the most extreme case we find that the attenuation changes by a factor of $10$, which could have a significant impact on the detection of the line (*i.e.* an emission line at $10\sigma$ above the flux limit would be observed at only $1\sigma$). Note that the abscissa in Figure [5](#fig:ebmvvarsim) shows the stellar E(B-V) averaged over the $10$ sight lines. The maximum E(B-V) found on any sight line is $0.5\,{\rm mag}$, which is close to our assumed value of $0.6\,{\rm mag}$ in Figure [4](#fig:ebmvvar). Note that the simulated volume is rather small (177 galaxies at $z=7$), thus it is likely to reach these higher E(B-V) values.

The simulation therefore verifies the possibility of almost dust-free regions along with heavily dust-obscured patches. Overall, this shows that the spectrum of JADES-GS-z7-01-QU can be naturally explained by a composition of a blue and red spatial component.

# Summary & Conclusions

The seemingly quiescent galaxy JADES-GS-z7-01-QU at $z=7.3$ is a curious case. The combination of lacking emission lines and blue UV to optical ratio is difficult to reconcile in simulations and theoretical models. Specifically, a galaxy like JADES-GS-z7-01-QU would not be classified as “quiescent” on common color diagrams (Figure [1](#fig:uvj_model)), but rather as a galaxy with a short-term deficit of star formation. We have explored the observational properties of galaxies such as JADES-GS-z7-01-QU in relation to *(i)* a stochastic varying (bursty) star formation, and *(ii)* a spatially varying dust attenuation causing a blue and red composite spectrum.

The observed properties of JADES-GS-z7-01-QU can be achieved shortly after a starburst (Figure [1](#fig:uvj_model)). From exploring more realistic stochastic SFHs, we learned that a short star formation correlation time ($\tau_{\rm break} < 150\,{\rm Myr}$) is necessary to explain the galaxy’s observed properties under the reasonable assumption of an average star formation oscillation amplitude around the mean of $\sigma_{\rm MS} = 0.5-0.6\,{\rm dex}$. This is consistent with recent measurements of the main-sequence scatter and star formation histories by JWST (cite: cole23). Furthermore, a similar scatter may be necessary to reconcile the UV luminosity functions at $z>9$ (cite: shen23). The average time spent in such a configuration is on the order of $10\,{\rm Myrs}$ or less (Figure [2](#fig:stochastic)). A comparison to more realistic SFHs from the SPHINX$^{\rm 20}$ cosmological hydrodynamic simulation for similar-mass $z=7$ galaxies showed that about $60-80\%$ of simulated galaxies went through this state of temporary quiescence in the past and each phase of quiescence lasts about $10-20\,{\rm Myrs}$ (Figure [3](#fig:sphinxresults)). Using these numbers, we estimated to find one temporarily quiescent galaxies among $\sim35$ star-forming galaxies at $z=7$, a number that is consistent with observational studies (cite: looser23b). However, we note that the SPHINX$^{\rm 20}$ simulation does not include black hole formation or AGN feedback due to its small volume (cite: katz23). AGN may be important in the quenching of high-redshift galaxies at a similar mass range as JADES-GS-z7-01-QU as shown both theoretically and observationally by recent studies (cite: xie24; juodzbalis23).

In addition to a stochastic SFH, we explored the effect of spatially varying dust attenuation within a galaxy (or as part of a merging system) on the observed UV continuum and emission lines. We showed that a composite spectrum based on the combination of a UV-bright dust-free density bounded region and a red dust-obscured post-starburst region can result in a spectrum similar to the one of JADES-GS-z7-01-QU (Figure [4](#fig:ebmvvar)). Specifically, the density bounded region results in a steep UV continuum, while a high differential dust attenuation between stellar continuum and nebular emission of the red component leads to the suppression of nebular emission. Due to the lesser dust attenuation at longer wavelengths, we would still expect the galaxy to show H$\alpha$ emission in this case (unfortunately not covered by current NIRSpec observations). Based on the SPHINX$^{\rm 20}$ simulation set, we found that variations in the attenuation of the nebular lines due to dust along different sight lines can vary from factors of a few up to a factor of $10$ (in one case, Figure [5](#fig:ebmvvarsim)). This is in agreement with UV and infrared emission offsets in recent ALMA observations. NIRCam imaging of JADES-GS-z7-01-QU does reveal a blue and red component, which could therefore naturally explain the observed spectrum.

In summary, both stochastic SFH and dust obscuration can explain the spectrum of JADES-GS-z7-01-QU. Both cases are connected and are therefore not exclusive. Upcoming observations with ALMA of the far-infrared continuum and the C II line emission (#2023.1.00521.S, PI: Faisst) will shed more light on the dust-obscured star formation of JADES-GS-z7-01-QU, which will help to constrain the above theories.

*Acknowledgements:* We thank the referee for the insightful comments which significantly improved our original manuscript. Futhermore, we thank H. Katz for useful discussions about the SPHINX$^{\rm 20}$ simulation. Some of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via and.

# Facilities

JWST

# Software

`astropy` (cite: astropy13; astropy18); `DELightcurveSimulation` (cite: connolly16); `FSPS` (cite: conroy09; conroy10); `Galfit` (cite: galfitpeng10); `Python-FSPS` (cite: johnson23)

natexlab

(ref: abraham07) Abraham, R. G., Nair, P., McCarthy, P. J., et al. 2007, ApJ, 669, 184, doi: [`10.1086/521138`](http://doi.org/10.1086/521138)

(ref: abramson20) Abramson, L. E., & Kelson, D. D. 2020, Research Notes of the American Astronomical Society, 4, 236, doi: [`10.3847/2515-5172/abd317`](http://doi.org/10.3847/2515-5172/abd317)

(ref: asada23) Asada, Y., Sawicki, M., Abraham, R., et al. 2024, MNRAS, 527, 11372, doi: [`10.1093/mnras/stad3902`](http://doi.org/10.1093/mnras/stad3902)

(ref: astropy13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: bell04) Bell, E. F., Wolf, C., Meisenheimer, K., et al. 2004, ApJ, 608, 752, doi: [`10.1086/420778`](http://doi.org/10.1086/420778)

(ref: bertelli94) Bertelli, G., Bressan, A., Chiosi, C., Fagotto, F., & Nasi, E. 1994, A&AS, 106, 275

(ref: bethermin20) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2, doi: [`10.1051/0004-6361/202037649`](http://doi.org/10.1051/0004-6361/202037649)

(ref: bethermin23) Béthermin, M., Accard, C., Guillaume, C., et al. 2023, A&A, 680, L8, doi: [`10.1051/0004-6361/202348115`](http://doi.org/10.1051/0004-6361/202348115)

(ref: bouwens22) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160, doi: [`10.3847/1538-4357/ac5a4a`](http://doi.org/10.3847/1538-4357/ac5a4a)

(ref: brown14) Brown, T. M., Tumlinson, J., Geha, M., et al. 2014, ApJ, 796, 91, doi: [`10.1088/0004-637X/796/2/91`](http://doi.org/10.1088/0004-637X/796/2/91)

(ref: bullock00) Bullock, J. S., Kravtsov, A. V., & Weinberg, D. H. 2000, ApJ, 539, 517, doi: [`10.1086/309279`](http://doi.org/10.1086/309279)

(ref: calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: caplar19) Caplar, N., & Tacchella, S. 2019, MNRAS, 487, 3845, doi: [`10.1093/mnras/stz1449`](http://doi.org/10.1093/mnras/stz1449)

(ref: carnall23a) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2023a, Nature, 619, 716, doi: [`10.1038/s41586-023-06158-6`](http://doi.org/10.1038/s41586-023-06158-6)

(ref: carnall23b) Carnall, A. C., McLeod, D. J., McLure, R. J., et al. 2023b, MNRAS, 520, 3974, doi: [`10.1093/mnras/stad369`](http://doi.org/10.1093/mnras/stad369)

(ref: cattaneo08) Cattaneo, A., Dekel, A., Faber, S. M., & Guiderdoni, B. 2008, MNRAS, 389, 567, doi: [`10.1111/j.1365-2966.2008.13562.x`](http://doi.org/10.1111/j.1365-2966.2008.13562.x)

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: cole23) Cole, J. W., Papovich, C., Finkelstein, S. L., et al. 2023, arXiv e-prints, arXiv:2312.10152, doi: [`10.48550/arXiv.2312.10152`](http://doi.org/10.48550/arXiv.2312.10152)

(ref: connolly16) Connolly, S. D. 2016, DELightcurveSimulation: Light curve simulation code, Astrophysics Source Code Library, record ascl:1602.012. [`http://ascl.net/1602.012`](http://ascl.net/1602.012)

(ref: conroy10) Conroy, C., & Gunn, J. E. 2010, ApJ, 712, 833, doi: [`10.1088/0004-637X/712/2/833`](http://doi.org/10.1088/0004-637X/712/2/833)

(ref: conroy09) Conroy, C., Gunn, J. E., & White, M. 2009, ApJ, 699, 486, doi: [`10.1088/0004-637X/699/1/486`](http://doi.org/10.1088/0004-637X/699/1/486)

(ref: croton06) Croton, D. J., Springel, V., White, S. D. M., et al. 2006, MNRAS, 365, 11, doi: [`10.1111/j.1365-2966.2005.09675.x`](http://doi.org/10.1111/j.1365-2966.2005.09675.x)

(ref: daddi07) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156, doi: [`10.1086/521818`](http://doi.org/10.1086/521818)

(ref: dave12) Davé, R., Finlator, K., & Oppenheimer, B. D. 2012, MNRAS, 421, 98, doi: [`10.1111/j.1365-2966.2011.20148.x`](http://doi.org/10.1111/j.1365-2966.2011.20148.x)

(ref: eugenio21) D’Eugenio, C., Daddi, E., Gobat, R., et al. 2021, A&A, 653, A32, doi: [`10.1051/0004-6361/202040067`](http://doi.org/10.1051/0004-6361/202040067)

(ref: devereaux23) Devereaux, T., Cassata, P., Ibar, E., et al. 2024, A&A, 686, A156, doi: [`10.1051/0004-6361/202348511`](http://doi.org/10.1051/0004-6361/202348511)

(ref: dome23) Dome, T., Tacchella, S., Fialkov, A., et al. 2024, MNRAS, 527, 2139, doi: [`10.1093/mnras/stad3239`](http://doi.org/10.1093/mnras/stad3239)

(ref: emmanoulopoulos13) Emmanoulopoulos, D., McHardy, I. M., & Papadakis, I. E. 2013, MNRAS, 433, 907, doi: [`10.1093/mnras/stt764`](http://doi.org/10.1093/mnras/stt764)

(ref: faisst19) Faisst, A. L., Capak, P. L., Emami, N., Tacchella, S., & Larson, K. L. 2019, ApJ, 884, 133, doi: [`10.3847/1538-4357/ab425b`](http://doi.org/10.3847/1538-4357/ab425b)

(ref: faisst17) Faisst, A. L., Carollo, C. M., Capak, P. L., et al. 2017, ApJ, 839, 71, doi: [`10.3847/1538-4357/aa697a`](http://doi.org/10.3847/1538-4357/aa697a)

(ref: faisst20) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020a, MNRAS, 498, 4192, doi: [`10.1093/mnras/staa2545`](http://doi.org/10.1093/mnras/staa2545)

(ref: faisst20b) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020b, ApJS, 247, 61, doi: [`10.3847/1538-4365/ab7ccd`](http://doi.org/10.3847/1538-4365/ab7ccd)

(ref: feldmann15) Feldmann, R. 2015, MNRAS, 449, 3274, doi: [`10.1093/mnras/stv552`](http://doi.org/10.1093/mnras/stv552)

(ref: forrest20) Forrest, B., Annunziatella, M., Wilson, G., et al. 2020, ApJL, 890, L1, doi: [`10.3847/2041-8213/ab5b9f`](http://doi.org/10.3847/2041-8213/ab5b9f)

(ref: fudamoto20) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, A&A, 643, A4, doi: [`10.1051/0004-6361/202038163`](http://doi.org/10.1051/0004-6361/202038163)

(ref: fudamoto21) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489, doi: [`10.1038/s41586-021-03846-z`](http://doi.org/10.1038/s41586-021-03846-z)

(ref: gelli23) Gelli, V., Salvadori, S., Ferrara, A., Pallottini, A., & Carniani, S. 2023, ApJL, 954, L11, doi: [`10.3847/2041-8213/acee80`](http://doi.org/10.3847/2041-8213/acee80)

(ref: glazebrook17) Glazebrook, K., Schreiber, C., Labbé, I., et al. 2017, Nature, 544, 71, doi: [`10.1038/nature21680`](http://doi.org/10.1038/nature21680)

(ref: haas13) Haas, M. R., Schaye, J., Booth, C. M., et al. 2013, MNRAS, 435, 2931, doi: [`10.1093/mnras/stt1487`](http://doi.org/10.1093/mnras/stt1487)

(ref: ilbert10) Ilbert, O., Salvato, M., Le Floc’h, E., et al. 2010, ApJ, 709, 644, doi: [`10.1088/0004-637X/709/2/644`](http://doi.org/10.1088/0004-637X/709/2/644)

(ref: inami22) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126, doi: [`10.1093/mnras/stac1779`](http://doi.org/10.1093/mnras/stac1779)

(ref: johnson23) Johnson, B., Foreman-Mackey, D., Sick, J., et al. 2023, dfm/python-fsps: v0.4.6, v0.4.6, Zenodo, doi: [`10.5281/zenodo.10026684`](http://doi.org/10.5281/zenodo.10026684)

(ref: jones20) Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491, L18, doi: [`10.1093/mnrasl/slz154`](http://doi.org/10.1093/mnrasl/slz154)

(ref: juodzbalis23) Juodžbalis, I., Conselice, C. J., Singh, M., et al. 2023, MNRAS, 525, 1353, doi: [`10.1093/mnras/stad2396`](http://doi.org/10.1093/mnras/stad2396)

(ref: kashino13) Kashino, D., Silverman, J. D., Rodighiero, G., et al. 2013, ApJL, 777, L8, doi: [`10.1088/2041-8205/777/1/L8`](http://doi.org/10.1088/2041-8205/777/1/L8)

(ref: katz23) Katz, H., Rosdahl, J., Kimm, T., et al. 2023, The Open Journal of Astrophysics, 6, 44, doi: [`10.21105/astro.2309.03269`](http://doi.org/10.21105/astro.2309.03269)

(ref: kelson14) Kelson, D. D. 2014, arXiv e-prints, arXiv:1406.5191, doi: [`10.48550/arXiv.1406.5191`](http://doi.org/10.48550/arXiv.1406.5191)

(ref: kennicutt98) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: kubo21) Kubo, M., Umehata, H., Matsuda, Y., et al. 2021, ApJ, 919, 6, doi: [`10.3847/1538-4357/ac0cf8`](http://doi.org/10.3847/1538-4357/ac0cf8)

(ref: leborgne03) Le Borgne, J. F., Bruzual, G., Pelló, R., et al. 2003, A&A, 402, 433, doi: [`10.1051/0004-6361:20030243`](http://doi.org/10.1051/0004-6361:20030243)

(ref: lefevre20) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1, doi: [`10.1051/0004-6361/201936965`](http://doi.org/10.1051/0004-6361/201936965)

(ref: lee24) Lee, M. M., Steidel, C. C., Brammer, G., et al. 2024, MNRAS, 527, 9529, doi: [`10.1093/mnras/stad3718`](http://doi.org/10.1093/mnras/stad3718)

(ref: lejeune97) Lejeune, T., Cuisinier, F., & Buser, R. 1997, A&AS, 125, 229, doi: [`10.1051/aas:1997373`](http://doi.org/10.1051/aas:1997373)

(ref: lejeune98) —. 1998, A&AS, 130, 65, doi: [`10.1051/aas:1998405`](http://doi.org/10.1051/aas:1998405)

(ref: lilly13) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119, doi: [`10.1088/0004-637X/772/2/119`](http://doi.org/10.1088/0004-637X/772/2/119)

(ref: looser23b) Looser, T. J., D’Eugenio, F., Maiolino, R., et al. 2023, arXiv e-prints, arXiv:2306.02470, doi: [`10.48550/arXiv.2306.02470`](http://doi.org/10.48550/arXiv.2306.02470)

(ref: looser23) —. 2024, Nature, 629, 53, doi: [`10.1038/s41586-024-07227-0`](http://doi.org/10.1038/s41586-024-07227-0)

(ref: lovell23) Lovell, C. C., Roper, W., Vijayan, A. P., et al. 2023, MNRAS, 525, 5520, doi: [`10.1093/mnras/stad2550`](http://doi.org/10.1093/mnras/stad2550)

(ref: madau14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: mehta23) Mehta, V., Teplitz, H. I., Scarlata, C., et al. 2023, ApJ, 952, 133, doi: [`10.3847/1538-4357/acd9cf`](http://doi.org/10.3847/1538-4357/acd9cf)

(ref: mitsuhashi23) Mitsuhashi, I., Harikane, Y., Bauer, F. E., et al. 2023, arXiv e-prints, arXiv:2311.16857, doi: [`10.48550/arXiv.2311.16857`](http://doi.org/10.48550/arXiv.2311.16857)

(ref: morishita22) Morishita, T., Abdurro’uf, Hirashita, H., et al. 2022, ApJ, 938, 144, doi: [`10.3847/1538-4357/ac9055`](http://doi.org/10.3847/1538-4357/ac9055)

(ref: nanayakkara22) Nanayakkara, T., Glazebrook, K., Jacobs, C., et al. 2024, Scientific Reports, 14, 3724, doi: [`10.1038/s41598-024-52585-4`](http://doi.org/10.1038/s41598-024-52585-4)

(ref: noeske07) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43, doi: [`10.1086/517926`](http://doi.org/10.1086/517926)

(ref: oke74) Oke, J. B. 1974, ApJS, 27, 21, doi: [`10.1086/190287`](http://doi.org/10.1086/190287)

(ref: pacifici16) Pacifici, C., Kassin, S. A., Weiner, B. J., et al. 2016, ApJ, 832, 79, doi: [`10.3847/0004-637X/832/1/79`](http://doi.org/10.3847/0004-637X/832/1/79)

(ref: pallottini23) Pallottini, A., & Ferrara, A. 2023, A&A, 677, L4, doi: [`10.1051/0004-6361/202347384`](http://doi.org/10.1051/0004-6361/202347384)

(ref: galfitpeng10) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2010a, AJ, 139, 2097, doi: [`10.1088/0004-6256/139/6/2097`](http://doi.org/10.1088/0004-6256/139/6/2097)

(ref: peng10) Peng, Y.-j., Lilly, S. J., Kovač, K., et al. 2010b, ApJ, 721, 193, doi: [`10.1088/0004-637X/721/1/193`](http://doi.org/10.1088/0004-637X/721/1/193)

(ref: popesso23) Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526, doi: [`10.1093/mnras/stac3214`](http://doi.org/10.1093/mnras/stac3214)

(ref: raiter10) Raiter, A., Schaerer, D., & Fosbury, R. A. E. 2010, A&A, 523, A64, doi: [`10.1051/0004-6361/201015236`](http://doi.org/10.1051/0004-6361/201015236)

(ref: reddy23) Reddy, N. A., Topping, M. W., Sanders, R. L., Shapley, A. E., & Brammer, G. 2023, ApJ, 948, 83, doi: [`10.3847/1538-4357/acc869`](http://doi.org/10.3847/1538-4357/acc869)

(ref: reddy15) Reddy, N. A., Kriek, M., Shapley, A. E., et al. 2015, ApJ, 806, 259, doi: [`10.1088/0004-637X/806/2/259`](http://doi.org/10.1088/0004-637X/806/2/259)

(ref: remus23) Remus, R.-S., & Kimmig, L. C. 2023, arXiv e-prints, arXiv:2310.16089, doi: [`10.48550/arXiv.2310.16089`](http://doi.org/10.48550/arXiv.2310.16089)

(ref: rodriguez09) Rodrı́guez, L. F., Gómez, Y., & Guzmán, L. 2009, , 45, 85, doi: [`10.48550/arXiv.0902.3594`](http://doi.org/10.48550/arXiv.0902.3594)

(ref: rosdahl18) Rosdahl, J., Katz, H., Blaizot, J., et al. 2018, MNRAS, 479, 994, doi: [`10.1093/mnras/sty1655`](http://doi.org/10.1093/mnras/sty1655)

(ref: rosdahl22) Rosdahl, J., Blaizot, J., Katz, H., et al. 2022, MNRAS, 515, 2386, doi: [`10.1093/mnras/stac1942`](http://doi.org/10.1093/mnras/stac1942)

(ref: sandles23) Sandles, L., D’Eugenio, F., Maiolino, R., et al. 2023, arXiv e-prints, arXiv:2306.03931, doi: [`10.48550/arXiv.2306.03931`](http://doi.org/10.48550/arXiv.2306.03931)

(ref: schawinski14) Schawinski, K., Urry, C. M., Simmons, B. D., et al. 2014, MNRAS, 440, 889, doi: [`10.1093/mnras/stu327`](http://doi.org/10.1093/mnras/stu327)

(ref: schreiber18) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, A&A, 618, A85, doi: [`10.1051/0004-6361/201833070`](http://doi.org/10.1051/0004-6361/201833070)

(ref: setton24) Setton, D. J., Khullar, G., Miller, T. B., et al. 2024, arXiv e-prints, arXiv:2402.05664, doi: [`10.48550/arXiv.2402.05664`](http://doi.org/10.48550/arXiv.2402.05664)

(ref: shen23) Shen, X., Vogelsberger, M., Boylan-Kolchin, M., Tacchella, S., & Kannan, R. 2023, MNRAS, 525, 3254, doi: [`10.1093/mnras/stad2508`](http://doi.org/10.1093/mnras/stad2508)

(ref: sparre17) Sparre, M., Hayward, C. C., Feldmann, R., et al. 2017, MNRAS, 466, 88, doi: [`10.1093/mnras/stw3011`](http://doi.org/10.1093/mnras/stw3011)

(ref: strait23) Strait, V., Brammer, G., Muzzin, A., et al. 2023, ApJL, 949, L23, doi: [`10.3847/2041-8213/acd457`](http://doi.org/10.3847/2041-8213/acd457)

(ref: sun23a) Sun, G., Faucher-Giguère, C.-A., Hayward, C. C., & Shen, X. 2023a, MNRAS, 526, 2665, doi: [`10.1093/mnras/stad2902`](http://doi.org/10.1093/mnras/stad2902)

(ref: sun23b) Sun, G., Faucher-Giguère, C.-A., Hayward, C. C., et al. 2023b, ApJL, 955, L35, doi: [`10.3847/2041-8213/acf85a`](http://doi.org/10.3847/2041-8213/acf85a)

(ref: tacchella16) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016, MNRAS, 457, 2790, doi: [`10.1093/mnras/stw131`](http://doi.org/10.1093/mnras/stw131)

(ref: tanaka19) Tanaka, M., Valentino, F., Toft, S., et al. 2019, ApJL, 885, L34, doi: [`10.3847/2041-8213/ab4ff3`](http://doi.org/10.3847/2041-8213/ab4ff3)

(ref: timmer95) Timmer, J., & Koenig, M. 1995, A&A, 300, 707

(ref: toomre72) Toomre, A., & Toomre, J. 1972, ApJ, 178, 623, doi: [`10.1086/151823`](http://doi.org/10.1086/151823)

(ref: topping22) Topping, M. W., Stark, D. P., Endsley, R., et al. 2022, ApJ, 941, 153, doi: [`10.3847/1538-4357/aca522`](http://doi.org/10.3847/1538-4357/aca522)

(ref: valentino20) Valentino, F., Tanaka, M., Davidzon, I., et al. 2020, ApJ, 889, 93, doi: [`10.3847/1538-4357/ab64dc`](http://doi.org/10.3847/1538-4357/ab64dc)

(ref: valentino23) Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023, ApJ, 947, 20, doi: [`10.3847/1538-4357/acbefa`](http://doi.org/10.3847/1538-4357/acbefa)

(ref: vikaeus23) Vikaeus, A., Zackrisson, E., Wilkins, S., et al. 2024, MNRAS, 529, 1299, doi: [`10.1093/mnras/stae323`](http://doi.org/10.1093/mnras/stae323)

(ref: westera03) Westera, P., & Buser, R. 2003, in Astronomical Society of the Pacific Conference Series, Vol. 296, New Horizons in Globular Cluster Astronomy, ed. G. Piotto, G. Meylan, S. G. Djorgovski, & M. Riello, 238

(ref: wuyts07) Wuyts, S., Labbé, I., Franx, M., et al. 2007, ApJ, 655, 51, doi: [`10.1086/509708`](http://doi.org/10.1086/509708)

(ref: xie24) Xie, L., De Lucia, G., Fontanot, F., et al. 2024, ApJL, 966, L2, doi: [`10.3847/2041-8213/ad380a`](http://doi.org/10.3847/2041-8213/ad380a)

[^1]: <https://github.com/samconnolly/DELightcurveSimulation>

[^2]: We are using the Python implementation, <https://dfm.io/python-fsps/> (cite: johnson23).

[^3]: With the caveat that we assume that the galaxies lived for at least $500\,{\rm Myrs}$.

[^4]: $f~=~{\rm E(B-V)_{stellar}} / {\rm E(B-V)_{nebular}}$.

</paper>

Write the methods card for this paper.