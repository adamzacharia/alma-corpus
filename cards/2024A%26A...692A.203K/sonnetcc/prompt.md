# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...692A.203K\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...692A.203K",
 "title": "PKS 1424−418: A persistent candidate source of the mm─γ-ray connection?",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Kim, Dae-Won",
 "n_authors": 8,
 "arxiv_id": "2411.19737",
 "doi": "10.1051/0004-6361/202451773",
 "alma_projects_linked_by_archive": []
}
```

Paper text:
<paper>
#  PKS 1424-418: A persistent candidate source of the mm–$\gamma$-ray connection?

We present a long-term strong correlation between millimeter (mm) radio and $\gamma$-ray emission in the flat-spectrum radio quasar (FSRQ) PKS 1424$-$418. The mm–$\gamma$-ray connection in blazars is generally thought to originate from the relativistic jet close to the central engine.

We confirm a unique long-lasting mm–$\gamma$-ray correlation of by using detailed correlation analyses and statistical tests, and we find its physical meaning in the source.

We employed $\sim$8.5 yr of (sub) mm and $\gamma$-ray light curves observed by ALMA and *Fermi*-LAT, respectively.

From linear and cross-correlation analyses between the light curves, we found a significant, strong mm–$\gamma$-ray correlation over the whole period.

We did not find any notable time delay within the uncertainties for the mm–$\gamma$-ray correlation, which means zero lag.

The mm wave spectral index values (S$_{\nu}\,\propto\,\nu^{\alpha}$) between the band 3 and 7 flux densities indicate a time-variable opacity of the source at (sub)mm wavelengths. Interestingly, the mm wave spectral index becomes temporarily flatter (i.e., $\alpha$ $>$ $-$0.5) when the source flares in the $\gamma$-rays.

We relate our results with the jet of , and we discuss the origin of the $\gamma$-rays and opacity of the inner (sub)parsec-scale jet regions.

# Introduction

Blazars are a subclass of radio-loud active galactic nuclei (AGNs).

The vast majority of bright $\gamma$-ray sources detected by the *Fermi*-Large Area Telescope (LAT) are identified as AGNs (cite: ajello2020), and blazars dominate the $\gamma$-ray bright AGN population.

Blazars can be further categorized into two subtypes: flat-spectrum radio quasars (FSRQs), and objects of BL Lacertae type (BLLacs). FSRQs show prominent optical emission lines, whereas BLLacs are without this feature (cite: keenan2021).

Blazars are strong nonthermal sources, and the typical spectral energy distribution (SED) of blazars consists of two hump-like features,

one of which is indicative of the synchrotron process from the radio to the UV, and the other is often presumed to be the inverse-Compton (IC) process in the $\gamma$-ray regime.

Alternatively, hadronic models have also been suggested for the $\gamma$-ray emission (cite: dar1997; bottcher2007; bottcher2013).

X-ray bands can show a concave spectrum that is produced by both radiative processes (cite: magic2018).

The relativistic jets in blazars are considered to be the main source of the nonthermal emissions, including in the $\gamma$-ray band (cite: marscher2008). Due to the small viewing angles between the jet axis and the line of sight (e.g., typically $\leq$ 5$^{\circ}$),

emission from blazar jets is highly Doppler boosted and shows strong variability with time. An obvious question here is where and how the $\gamma$-rays are produced in the jets (cite: blandford2019).

With the development of very long-baseline interferometry (VLBI), detailed morphologies, structures, and physical properties of the (sub)parsec-scale jets of blazars were revealed (cite: lee2008; lister2009; nair2019; weaver2022). In most of the VLBI images, the jets show a compact intense emitting region at the upstream end of the flow. This structure is called the radio core (or VLBI core), which is generally assumed to be the surface of the unity optical depth: $\tau_{\rm opaq}(\nu)\,\sim\,1$. This leads to the so-called core shift in the jets and tends to decrease with increasing frequency in a power-law form (cite: dodson2017). Hence, the innermost jet regions closer to the central engine are rather hidden and invisible owing to synchrotron self-absorption (SSA), particularly at lower radio frequencies (e.g., (cite: lobanov1998; marscher2008); see also (cite: marscher2016) for alternative theories and models of the core).

It has been suggested that the core shift is variable with time and can be increased by strong flares at higher radio frequencies (cite: chamani2023).

In this context, observations at higher radio frequencies are crucial to broaden our understanding of the high-energy emission processes in blazar jets.

Previous studies of the jets found that the $\gamma$-ray emission is correlated with the core radio emission

(cite: jorstad2001a; kovalev2009; pushkarev2010).

Based on VLBI observations, it was suggested that the $\gamma$-ray events are tightly linked with the passage of superluminal knots through the radio core region (cite: jorstad2001b; marscher2008; wehrle2016; roder2024).

The search for time correlations between radio and $\gamma$-ray light curves is one of the key approaches to support the existence of the radio–$\gamma$-ray connection in blazars. Previous studies performed a statistical study with a large number of AGN samples (mostly blazars) and found that just a handful of sources show a significant radio–$\gamma$-ray correlation over a short period (i.e., 2.5–5.0 yr) of time (cite: fuhrmann2014; maxm2014a; rama2015; rama2016). In contrast to the clear correlation between the optical and $\gamma$-ray emission in blazars (cite: liodakis2019), it is difficult to find a clear significant correlation between radio and $\gamma$-ray emission.

This might be due to (1) different variability timescales, (2) a lack of huge flares, and (3) poor data sampling.

The typical radio–$\gamma$-ray correlation is either (1) the $\gamma$-rays preceding the radio emission (cite: agudo2011a; kim2020) or (2) the $\gamma$-rays (quasi-)simultaneous with the radio emission (cite: wehrle2012; kim2018).

This suggests that the $\gamma$-ray production site is located either in a region upstream of or near the radio core (cite: leon2011). In addition,

previous and recent works reported multiple sites for $\gamma$-rays in the jets (cite: marscher2008; rani2018; liodakis2020; kim2022).

(cite: white1988) is an FSRQ in the southern sky (DEC $\sim$ $-$42$^{\circ}$). Since most of the major VLBI arrays are located in the northern hemisphere, there are only a limited number of VLBI images of this source. The jet of has an extended structure toward the northeast in the image plane that indicates the flow axis (cite: benke2024).

Interestingly, a PeV-energy neutrino event was detected from this source along with strong $\gamma$-ray outbursts in late 2012 to early 2013 (cite: kadler2016). This implies the presence of hadronic processes (e.g., photo-pion production with highly accelerated protons) in the jet of .

In this work, we define the spectral index ($\alpha$) as S$_{\nu}\,\propto\,\nu^{\alpha}$, where S and $\nu$ are the flux density and observing frequency, respectively. We estimated the uncertainty of $\alpha$ following the error propagation. We use the cosmological parameters as follows: $H_{0}$ = 71 km Mpc s$^{-1}$, $\Omega_{\Lambda}$ = 0.73, and $\Omega_{m}$ = 0.27 throughout this paper.

# Radio and $\gamma$-ray light curves in 2011–2020

##  $\gamma$-ray data

We analyzed the Pass 8 $\gamma$-ray data obtained from the *Fermi*-LAT (cite: atwood2009).

Overall, we followed the standard unbinned likelihood procedure[^1] to generate the $\gamma$-ray light curve of the source (i.e., RA = 216.987$^{\circ}$, DEC = $-$42.106$^{\circ}$; J2000).

At first, we put together a background template (so-called XML model). Two background components, `gll_iem_v07` and `iso_P8R3_SOURCE_V3_v1`, were employed to take into account Galactic diffuse emission and isotropic background emission, respectively. We set a region of interest (ROI) to be a circle of radius 10$^{\circ}$ centered at the position of , and we included all

4FGL-catalog sources (cite: abdollahi2020; ballet2023) present within 20$^{\circ}$ (ROI $+$ 10$^{\circ}$) from the position of . We kept the default spectral models provided by the catalog for all the sources except our target; a simple power law was applied to the target (see below).

During the spectral fits, we left the spectral parameters free for all sources within 5$^{\circ}$ of the ROI center. For sources between 5$^{\circ}$ and 10$^{\circ}$, only normalization parameters were left free. For sources beyond 10$^{\circ}$, we kept all the parameters fixed to the catalog values. For the two diffuse background components (i.e., Galactic and isotropic), only the normalizations were left free. When sources lay within 10$^{\circ}$ but were faint (i.e., $<$ 5 $\sigma$, where $\sigma$ is the detection significance), then their spectral parameters were kept fixed; one source was known to be time variable (i.e., variability index $>$ 24.73 ; see, e.g., (cite: abdollahi2023) for a definition of the variability index), and thus, we only let its normalization be free.

![image](fig/Gspinx1.pdf)  ![image](fig/Gspinx2.pdf)

We analyzed $\gamma$-rays from the source in the 0.1–200 GeV energy range measured between 4 September 2011 and 26 March 2020 (MJD: 55808–58934), which is $\sim$8.5 yr. We chose this time range because (1) the ALMA light curves of this source started in 2011 and (2) the source became quiescent in the LAT $\gamma$-ray band for a long time (i.e., $\sim$1.5 yr) with too many upper limits from 2020. We selected SOURCE class (`evclass=128`) and FRONT$+$BACK-type (`evtype=3`) events. The good-time intervals (GTIs) were determined with the parameters `(DATA_QUAL>0)&&(LAT_CONFIG==1)` and `roicut=no`. The maximum zenith angle (zmax) was set to be 90$^{\circ}$ to minimize the Earth limb $\gamma$-ray contamination.

We employed the maximum likelihood test statistics (TS) to evaluate the significance of the $\gamma$-ray photons. For each time bin, we first fit the data with the background template. Then, all the faint sources with TS $<$ 9 ($\sim$3 $\sigma$) were removed from the background model. Using this updated model, we performed a second maximum likelihood fit to the data to obtain the final results. We computed 2 $\sigma$ upper limits for the $\gamma$-rays with TS $<$ 20 or $\Delta F_{\gamma}/F_{\gamma}$ $\geq$ 0.5, where $F_{\gamma}$ and $\Delta F_{\gamma}$ indicate the $\gamma$-ray flux density and its uncertainty, respectively.

We used a power-law form that was defined as $dN/dE \propto E^{\Gamma}$, with $N$ being the number of photons, $E$ the photon energy, and $\Gamma$ the photon index. For the LAT analysis, the power-law and LogParabola models[^2] are generally preferable for AGNs. In our case, there are no significant differences in the results between the two models, and we selected the power-law model assuming that it is more suitable for these short day-scale bins. Since we let $\Gamma$ vary during the fits, every single time bin had a different $\Gamma$ value. Figure [1](#fig:gindx) shows the results. Overall, $\Gamma$ fluctuates in the time domain without a clear tendency. However, $\Gamma$ seems to converge to about $-$2.0 with increasing flux density.

The overall index–flux trend of is similar to a typical pattern for $\gamma$-ray emitting FSRQs (cite: kim2020), but fairly harder and brighter. To match the $\gamma$-ray data with the sampling of our radio data, we generated a $\gamma$-ray light curve with a binning interval of 6 days (see Section [2.2](#sec:raddat)).

![](fig/LCs.pdf)

In total, we obtained 522 $\gamma$-ray photon measurements, including 14 bad time bins for which the fit was unsuccessful with some fitting errors. We excluded these poor data in this work. Only data points with TS $\geq$ 20 and $\Delta F_{\gamma}/F_{\gamma}$ $<$ 0.5 were used in this work, which is $\sim$93% (470/508) of the whole samples. For the other poor data points, we present the upper limits only in Figure [2](#fig:thelcs), and they were excluded in the rest of our results. During the source analysis, we occasionally found that the fit returned erroneous results (e.g., empty or highly underestimated bins) depending on the fit-tolerance (Tol) value. To remedy this issue, we carried out two sets of the analysis: one set with Tol $\sim$ 0.01, and the other set with Tol $\sim$ 0.00001. When they both returned reasonable estimates, we chose the set with a higher TS or lower $\Delta F_{\gamma}/F_{\gamma}$ when the difference in TS was smaller than one. In our $\gamma$-ray light curve, we defined the low-state photons as those with TS $<$ 100 (76 photons in total). They are $\sim$3$\rm \,\times\,10^{-7}\,ph\,cm^{-2}\,s^{-1}$ on average, with 1 $\sigma$ being $\sim$1.3$\rm \,\times\,10^{-7}\,ph\,cm^{-2}\,s^{-1}$. Based on this estimate, we considered all those photons brighter than $\sim$7$\rm \,\times\,10^{-7}\,ph\,cm^{-2}\,s^{-1}$ (i.e., $\geq$ the average $+$ 3 $\sigma$) as a flare.

##  Millimeter-wave data

We made use of the Atacama Large Millimeter/submillimeter Array (ALMA) calibrator catalog data[^3]. We obtained three ALMA millimeter (mm) radio light curves of at band 3, band 6, and band 7 (see more details of the ALMA bands here[^4]). At band 3, the flux densities were measured at

two central frequencies: $\sim$91 GHz and $\sim$103 GHz. We used all these measurements and consider 95 GHz as a representative observing frequency of band 3 in this study. When multiple flux density measurements were available at the same timestamp, we used their average. The other two bands (i.e., bands 6 and 7) observed the source at

the central frequencies of $\sim$235 GHz and $\sim$345 GHz, respectively. Details of the catalog and ALMA observations can be found in (cite: bonato2018).

In our analyses, the cadence (i.e., the sampling frequency) is the most important factor for obtaining more accurate results, and we found that the band 3 light curve was best sampled: The median sampling interval is 6 days, with an average of $\sim$10 days (see Appendix [6](#sec:allalma) for the band 6 and 7 data).

For all the ALMA bands, the medians describe their samplings better than the average (i.e., closer to the peak frequency in the sampling distribution).

Since band 3 had a higher cadence than the other two radio bands, our analyses were more focused on the data from this band together with the LAT $\gamma$-ray data.

As for the *Fermi*-LAT data analysis, we considered ALMA data spanning $\sim$8.5 yr from September 2011 to March 2020. Figure [2](#fig:thelcs) shows the band 3 and $\gamma$-ray light curves. The band 3 flux densities are $\sim$3 Jansky (Jy) on average at 95 GHz with 1 $\sigma$ of 1 Jy.

From simple visual inspection of the light curves, it seems already obvious that their overall patterns look very similar to each other,

which implies a connection between the mm and $\gamma$-ray variability.

![image](fig/Pearson_RGcf.pdf)  ![image](fig/Pearson_RG.pdf)

# Results

While we estimated the median sampling times at the three ALMA bands, the radio light curves were sampled unevenly because the cadence varied, as shown in Figure [2](#fig:thelcs). The $\gamma$-ray data, on the other hand, have some empty time bins (i.e., erroneous data) and upper limits that lead to irregular sampling.

To properly account for this in our analyses, we developed a binning approach (see Appendix [7](#sec:panal)), and this approach was used throughout this paper. A connection between the mm and $\gamma$-ray light curves was examined by using the Pearson correlation and the local cross-correlation function (cite: welsh1999). Detailed descriptions of these methods can be found in Appendix [7](#sec:panal) and Appendix [8](#sec:ccf1), respectively.

## Linear relations

The Pearson correlation is a straightforward way to examine the presence of any significant linear correlation between two time series.

Figure [3](#fig:coreps) shows the results. We obtained a total of 488 Pearson coefficients (r$_{\rm P}$) for the whole 8.5 yr of the mm and $\gamma$-ray variability. Bin$_{\rm eq}$ (i.e., the equal-sized time bin) varies with the 488 calculations from 6 days to 100 days. The r$_{\rm P}$ values are $\sim$0.76 on average, with a 1 $\sigma$ uncertainty of 0.02 (minimum and maximum of 0.71 and 0.86, respectively). A sufficient number of data samples was used for each of the calculations, and thus, all the r$_{\rm P}$ values are highly significant

(i.e., $p$-values $\ll$ 0.01).

As expected from the visual inspection of Figure [2](#fig:thelcs), there is a clear and strong positive correlation between the band 3 and $\gamma$-ray emission in in all observations. A level of r$_{\rm P}$ = 0.76 is already quite high; even the minimum value of 0.71 is also high enough.

Overall, the impact of different Bin$_{\rm eq}$ sizes on r$_{\rm P}$ is shallow, but it is stronger above $\sim$30 days.

This strong significant linear relation in the presence of multiple flaring activities at both wavebands for a long time indicates that the mm wave and $\gamma$-ray emissions are physically connected with each other (cite: wehrle2012). In Appendix [6](#sec:allalma), we also test Pearson correlations between the three radio bands (i.e., band 3, 6, and 7). As a result, we find that they are tightly correlated almost one to one with r$_{\rm P}$ of $>$ 0.95.

![](fig/LCCF_B3.pdf)

## Cross-correlation between  mm and $\gamma$-ray emission

The linear correlations we presented in the previous section were obtained without any time shift of a light curve (either mm or $\gamma$-ray). This suggests that there is no significant time delay in the physical connection between the mm wave and $\gamma$-ray emission in the source. However, the delay plays an important role in the physical interpretation of the results, and so we carried out a detailed search for it by using LCCF.

Figure [4](#fig:lccfmain) shows the resultant LCCF curve between the band 3 and $\gamma$-ray light curves of . The binning interval ($\Delta t$) was set to be 6 days to match the basic samplings of the band 3 and $\gamma$-ray data; we also tested higher $\Delta t$ values, but the results were consistent with the one with $\Delta t$ = 6 days (see Appendix [9](#sec:ccf2)). The LCCF values are mostly above zero for all delays ($\tau$), and we found one notable hump-like feature at around $\tau$ = 0. Only the top part of this central LCCF hump where it peaks at $\tau$ = 0 with LCCF $\sim$ 0.75, exceeds the confidence level of 99.9%.

This result suggests that the $\gamma$-ray and band 3 light curves are contemporaneous in the time domain with an uncertainty of $\pm$3 days from $\tau$ = 0.

![](fig/mmsp-g.pdf)

## Evolution of the (sub)mm wave spectral index

Since the band 7 data were quite well sampled (i.e., a median of $\sim$8 days), we also calculated the spectral index ($\alpha$) between the band 3 and 7 flux densities to check the source opacity at (sub)mm wavelengths; in contrast, the sampling of the band 6 data is very poor, which prevented us from using it for a solid analysis.

Figure [5](#fig:mmspidx) shows the evolution of $\alpha$ between the 95 GHz and 345 GHz emission. The variability timescales of the radio light curves seem to be on month scales overall. To take this into account in the calculations of $\alpha$, the radio data were binned with multiple bin sizes in the time domain. That is, Bin$_{\rm eq}$ ranged from 3 days to 30 days, which corresponds to NBin$_{\rm eq}$ sliding from 1038 to 105. We also tested very small Bins$_{\rm eq}$ that varied from from one day to two days. The overall trend was consistent with the result from the larger Bin$_{\rm eq}$ range, but with far fewer numbers of the data points.

The average of the $\alpha$ values is $-$0.57 (with 1 $\sigma$ of 0.08), and they range from a minimum of $-$0.78 to a maximum of $-$0.19.

We considered $\alpha$ $\sim$ $-$0.5 as a reference point of the transition between optically thick (flatter; $\alpha$ $>$ $-$0.5) and thin (steeper; $\alpha$ $\leq$ $-$0.5) (cite: marscher1985). Most of the time, the spectral indices are below $-$0.5 at around $-$0.6.

From visual inspection of Figure [5](#fig:mmspidx), however, we found that $\alpha$ becomes flatter (i.e., $\geq$ $-$0.5) when the $\gamma$-rays flare.

However, this feature seems to be clearer when the $\gamma$-ray flares are stronger and last longer. For the weaker flares, the spectral feature might be less pronounced in the thin regime (i.e., $\alpha$ $<$ $-$0.5), or they might have a different origin/mechanism without this feature in the (sub)mm wave spectrum. In early 2012 (around MJD 55936), higher $\gamma$-rays were observed that perhaps consisted of multiple $\gamma$-ray flares. This activity seems marginal or exceeds the flare threshold only slightly. We consider it to be a long-lasting activity (e.g., $\geq$ 4 months), but weaker.

It is worth noting that there are a few caveats for Figure [5](#fig:mmspidx). We note that the sampling of the radio data at both bands 3 and 7 are irregular, and the sampling is quite sparse especially in the early part (i.e., $<$ 2014; MJD 56658). Owing to this, the $\alpha$ values in this early part might be less robust, and care must therefore be taken in this time range. Moreover, there might be hidden fast $\gamma$-ray flares (i.e., short-term events on a scale of hours to minutes) that cannot be seen in our $\gamma$-ray light curve.

This suggests a connection between the $\gamma$-ray flares and the source opacity at (sub)mm wavelengths in the jet (cite: jorstad2013).

Previous studies predicted a rapid decrease in the core shift with increasing radio frequencies (cite: dodson2017; lisakov2017; okino2022). Our finding favors at least a small core shift at above 95 GHz when $\gamma$-ray flares occur in the jet of PKS 1424-418.

# Discussion

## Unusual long-term  mm–$\gamma$-ray correlation

In general, the detection of a significant mm–$\gamma$-ray correlation in blazars has been somewhat intermittent (for light curves spanning about 3–4 yr overall), and only a small number of source samples were reported in previous statistical studies (cite: fuhrmann2014; maxm2014a; rama2015; rama2016). It is even more difficult to search for these significant correlations in some of the blazars with extreme radio variability (cite: kim2022).

This is partly because the previous works were done in the low-frequency radio bands (e.g., below 40 GHz) where the radio emission arises from a region that lies farther away from the high-energy region (cite: maxm2014a).

We found a long-term tightly correlated (at $>$ 99.9%) mm–$\gamma$-ray variability in that is quite atypical. After the period of our datasets, the source became quiescent at both (sub)mm wavelengths and $\gamma$-rays for about one year (e.g., March 2020 to March 2021). Thus, we assume that this unique mm–$\gamma$-ray correlation spanned almost $\sim$10 yr in the source.

Leptonic models (i.e., synchrotron and IC scattering) have been successful in describing most of the blazar SEDs (cite: bottcher2013; paliya2018). This tight correlation between $\gamma$-ray and lower-energy bands strongly supports the IC processes for the $\gamma$-ray emission (cite: liodakis2019) via synchrotron-self Compton (SSC) and/or external Compton (EC) with seed photon fields from either the broad-line region (BLR) or a dusty torus (DT).

Previous SED studies indeed favored a combination of the SSC and EC processes for the observed $\gamma$-rays from (cite: tavecc2013; buson2014; paliya2018; abhir2021).

However, further details about the mechanism are somewhat elusive.

Our results refer to a typical diagnostic of the SSC $\gamma$-rays (cite: agudo2011b).

The strong long-term mm–$\gamma$-ray correlation in might be attributed to SSC of low-energy electrons, which leads to longer cooling timescales for the $\gamma$-rays (cite: bottcher2019). However, the significant Compton dominance in this source (cite: paliya2018) indicates that strong external photon fields play an important role via EC (see also (cite: marscher2010) and (cite: macdonald2015) for a discussion of a slow jet sheath as a potential source of soft seed photons at $\leq$ pc scales).

##  Location of the $\gamma$-ray production site

Based on the stable tight mm–$\gamma$-ray correlation over more than 8.5 yr, it is straightforward to consider that the $\gamma$-ray origin is cospatial with the (sub)mm wave core region in the jet of (cite: vanzyl2015).

The inner jet regions (e.g., $<$ 0.1–1 pc) are thought to be opaque at radio frequencies (cite: marscher2008), and radio emission therefore emerges beyond this region where the radio core appears. In blazars, the centimeter-wave core is assumed to be located at 7–12 pc, for instance, from the central engine (cite: pushkarev2010; kramarenko2022). Thus, the mm wave core is likely to be located at a distance scale smaller than this range, for example, $<$ 7 pc, which is closer to the central engine at higher frequencies. This can be confirmed with mm VLBI observations. For instance, (cite: kim2023) presented a 3mm VLBI image of the jet of the blazar BL Lacertae ($z$ = 0.0686) observed by the Global mm VLBI Array (GMVA) on an angular resolution scale of tens of $\mu$as ($\sim$70 $\mu$as). At this redshift,

the image scale of the source is $\sim$1.3 pc mas$^{-1}$.

Using $M_{\rm BH}$ $\sim$ 10$^{8.2}\,M_{\odot}$ (cite: cohen2014), the angular resolution of 70 $\mu$as can be converted into a projected distance of 0.091 pc in the observer frame, which corresponds to $\sim$6000 R$_{\rm s}$, where R$_{\rm s}$ is the Schwarzschild radius. With the jet viewing angles of 1–10$^{\circ}$ and assuming a conservative wide range for this blazar (cite: marscher2008; weaver2022), we can obtain a range of the deprojected distance that is $\sim$0.5–4.9 pc in the source frame. These estimates might be considered as upper limits for the location of the (sub)mm

wave core region in BL Lacertae.

It is worth noting that (cite: agarwal2024) recently found an absorption feature in $\gamma$-ray spectra of PKS 1424-418 at above 10 GeV (cite: costamante2018). This might be strong evidence that the $\gamma$-rays originated from a region of influence of the BLR photons (e.g., a typical radius of BLR $\sim$ 0.1 pc). If this is the case, the presence of the $\gamma$-ray absorption might either imply the proximity of the (sub)mm wave core to the outer boundary of the BLR or indicated that an extended structure of the BLR lies farther downstream of the jet.

The SSA opacity ($\tau_{\rm opaq}$) of a jet region can be enhanced with a higher electron density, which meets the argument of moving shocks in the compact core regions (cite: kim2022). On the other hand, (cite: sharma2022) presented the effect of the jet viewing angle ($\theta_{\rm jet}$) on $\tau_{\rm opaq}$ in a conical self-absorbed jet. The authors suggested that a spatial displacement between the radio cores with spectral hardening becomes more pronounced at smaller jet viewing angles. This is also consistent with an expression of the SSA opacity (cite: finke2019), that is, $\tau_{\rm opaq}(\epsilon) \propto \delta^{(p+2)/2}$, where $\epsilon$ is approximately $\sim\,\nu / \rm (1.23\,\times\,10^{20})$ Hz, $\delta$ is the Doppler factor, and $p$ is the power-law index of the electrons, $\alpha$ = ($p-1$)/2.

Thus, there might be a change in $\theta_{\rm jet}$ near the radio core region and/or a core shift in the (sub)mm waveband during the interaction between the core and the moving shocks (e.g., toward smaller $\theta_{\rm jet}$).

##  Potential effects of a core shift to the $\gamma$-ray origin

The coincidence of the spectral hardening with the $\gamma$-ray flares suggests that a gap lies between $\tau_{\rm \gamma-B3}$ and $\tau_{\rm \gamma-B7}$ that was caused by a core shift between 95 GHz and 345 GHz in the jet. To explore this possibility, we examined the LCCF curves of the $\gamma$-rays with the band 3 and band 7 datasets (Appendix [10](#sec:gausfit)).

The LCCF curve of the band 7 peaks at two positions: first, at $\tau$ = $-$16 days (LCCF $\sim$ 0.78$\pm$0.15), and then, at $\tau$ = 0 (0.77$\pm$0.12), where negative $\tau_{\rm \gamma-radio}$ means “$\gamma$-ray leading”.

To better estimate probable locations of the LCCF peaks for both $\tau_{\rm \gamma-B3}$ and $\tau_{\rm \gamma-B7}$, we fit a Gaussian model to the data. The fits estimate $\tau_{\rm \gamma-B3}$ = $-$2.8$\pm$2.0 days and $\tau_{\rm \gamma-B7}$ = $-$0.8$\pm$2.6 days.

This result is consistent with the model of the core shift (i.e., the higher the frequencies, the more upstream the regions) and suggests that the $\gamma$-rays are almost simultaneous with the band 7 flux densities, but precede the band 3 flux densities by a few days. A cross-correlation analysis is highly dependent on these flux densities in a flaring state (cite: kim2022). As evident from Figure [5](#fig:mmspidx), we consider that the source becomes temporarily optically thick at (sub)mm wavelengths during the $\gamma$-ray flaring periods . We also note that the photon flux density of blazar $\gamma$-ray flares generally tends to be higher with shorter binning intervals. Hence, we cannot rule out the possibility that regions with flatter $\alpha_{\rm radio}$ could cause the weak delay between the band 3 and $\gamma$-ray emission. This means that the band 3 emission comes days after the $\gamma$-rays and band 7 emission. We also note that the linear relation between the band 3 and 7 emission shown in Appendix [6](#sec:allalma) begins to deviate from an initially tight linear trend at around F$_{\rm B7}$ $\sim$ 2.8 Jy. This further supports the above-mentioned interpretation of the variable source opacity at 95–345 GHz. In this regard, we suggest that the $\gamma$-ray site and the 95 GHz core position are only slightly displaced when the source is flaring at $\gamma$-rays. However, we expect that even this displacement disappears completely at higher radio frequencies (e.g., $\geq$ 345 GHz) because the radio core becomes transparent with increasing radio frequency.

The distance ($\Delta d_{\rm \gamma-radio}$) between the mm and $\gamma$-ray emitting regions can be estimated by $\Delta d_{\rm \gamma-radio}$ = $\beta_{\rm app}\,c\,\tau_{\rm \gamma-radio}\,\textup{sin}^{-1}\theta_{\rm jet}\,(1+z)^{-1}$, where $\beta_{\rm app}$ is the apparent jet speed, $c$ is the speed of light, $\tau_{\rm \gamma-radio}$ is the delay between radio and $\gamma$-ray light curves, $\theta_{\rm jet}$ is the jet viewing angle, and $z$ is the source redshift. Assuming $\beta_{\rm app}$ = 9 (i.e., a median value for FSRQs; (cite: weaver2022)) and $\theta_{\rm jet}$ = 1–3$^{\circ}$ (cite: paliya2018; weaver2022), we find a deprojected distance of $\Delta d_{\rm \gamma-B3}$ $\sim$ 0.16 pc with $\theta_{\rm jet}$ = 3$^{\circ}$ for $\tau_{\rm \gamma-B3}$ = 2.8 days (Figure [4](#fig:lccfmain)) and $\Delta d_{\rm \gamma-B3}$ $\sim$ 0.48 pc with $\theta_{\rm jet}$ = 1$^{\circ}$. This indicates that the $\gamma$-ray production site is located in a region upstream of the 95 GHz core by about 0.16–0.48 pc; but if $\beta_{\rm app}$ is much higher (cite: weaver2022), then the distance range for the same $\theta_{\rm jet}$ = 1–3$^{\circ}$ can be $\Delta d_{\rm \gamma-B3}$ $\sim$ 0.71–2.14 pc. For the $\tau_{\rm \gamma-B7}$ estimate of 0.8 day, it is basically a zero-lag within the uncertainty. If there is at least a small shift in the position of the 345 GHz core and we consider the $\tau_{\rm \gamma-B7}$ of 0.8 day as the corresponding shift, however, the distance between the 345 GHz core and the $\gamma$-ray site could be $\Delta d_{\rm \gamma-B7}$ $\sim$ 0.05–0.14 pc for the same $\theta_{\rm jet}$ range above at $\beta_{\rm app}$ = 9 . This distance scale is comparable to the radius of the BLR estimated by (cite: tavecc2013).

A simple way to confirm the above predictions is to perform multiband (quasi-)simultaneous VLBI observations of the source at (sub)mm wavelengths to measure the core shift. At $z$ = 1.52, the luminosity distance of is $\sim$11192 Mpc, and this corresponds to an image scale of 8.54 pc/mas.

We find projected distances of $\sim$0.02 pc or $\sim$2.5 $\mu$as for the $\Delta d_{\rm \gamma-B3}$ values, and if present, $\sim$0.006 pc or $\sim$0.7 $\mu$as for the $\Delta d_{\rm \gamma-B7}$ values. This suggests that the level of the core shift between the 95 GHz and 345 GHz cores is $\sim$1.8 $\mu$as, which may indeed be present in these high-frequency core regions.

##  Physical scenario for the production of the $\gamma$-ray flares

From decades of VLBI studies of blazar jets, it is clear that the radio core is a dominant source of the observed radio emission from the jets, especially when a strong disturbance (or a moving shock) passes through the core region (cite: marscher2008). This is particularly true at higher radio frequencies, since there should be no significant contributions from the extended jet regions to the observed radio emission (cite: marscher1985). Higher-energy electrons last much shorter than lower-energy ones regarding their energetic lifetimes. We find remarkable variations in the jet opacity at 95–345 GHz that coincide with the $\gamma$-ray flaring periods. (cite: plavin2019) found a core-shift variability at low frequencies (i.e., 2–8 GHz) with large source samples. This may be related to our findings. As suggested by the authors, the passage of a moving shock through the core region could lead to a displacement in the core position by pushing it downstream. If this holds in our case, the following scenario can be suggested: (1) The radio core was initially optically thin at above 95 GHz

(i.e., $\leq$ 3.5 mm).

\(2\) A

moving shock causes core shifts at (sub)mm wavelengths by temporarily increasing the jet opacity (cite: jorstad2013; wehrle2016; lisakov2017). (3) As the shock leaves the region, the core restores its initial condition (i.e., opacity and position).

# Summary

We have studied the time correlation between an mm wave and $\gamma$-ray emission in the blazar by using ALMA (sub) mm radio light curves at 90–350 GHz and a LAT $\gamma$-ray light curve at 0.1–200 GeV.

Because of the cadence of the data sampling, we mainly used ALMA band 3 ($\sim$95 GHz) data with the band 6 and band 7 (235 GHz and 345 GHz, respectively) data as supporting material for the correlation analyses.

Interestingly, the band 3 and $\gamma$-ray light curves already appear to be very similar to each other visually,

and we robustly confirmed this with detailed statistical analyses.

We find a highly significant positive mm–$\gamma$-ray correlation over the

complete time period of 8.5 yr, which means that this blazar is the best case thus far of a long-term close connection between mm wave and $\gamma$-ray emission (A. Marscher, private communication). This long-term strong correlation is typically observed between optical and $\gamma$-ray emission in blazars.

This suggests that the $\gamma$-ray emission almost always originates in the (sub)mm wave radio core region (i.e., $>$ 90 GHz) in this source.

If the core shift indeed occurs at the high radio frequencies with strong $\gamma$-ray flares, however, an exception can occur when a moving shock passes through the core region. This leads to an increase in the SSA opacity and thus to a displacement between the $\gamma$-ray site and the mm wave core.

A flare-induced core shift at (sub) mm wavelengths like this could be confirmed by using a multiband VLBI campaign involving extremely high-resolution mm VLBI arrays

(cite: boccardi2017) such as GMVA and the Event Horizon Telescope (EHT).

It is worthwhile to note that our results are based on a long-term global trend, and there might be other $\gamma$-ray events in the source that deviate from our conclusion.

A monitoring campaign at shorter mm wavelengths (e.g., $<$ 3.5 mm) with a better sampling cadence (i.e., $\leq$ 3 days) would facilitate the investigation of these cases (e.g., orphan $\gamma$-ray events).

# Acknowledgements

We thank Alan Marscher & Svetlana Jorstad (Boston University), Yuri Kovalev (MPIfR), and Abhishek Desai & Bindu Rani (GSFC) for useful comments on the manuscript.

The *Fermi* LAT Collaboration acknowledges generous ongoing support from a number of agencies and institutes that have supported both the development and the operation of the LAT as well as scientific data analysis. These include the National Aeronautics and Space Administration and the Department of Energy in the United States, the Commissariat à l’Energie Atomique and the Centre National de la Recherche Scientifique / Institut National de Physique Nucléaire et de Physique des Particules in France, the Agenzia Spaziale Italiana and the Istituto Nazionale di Fisica Nucleare in Italy, the Ministry of Education, Culture, Sports, Science and Technology (MEXT), High Energy Accelerator Research Organization (KEK) and Japan Aerospace Exploration Agency (JAXA) in Japan, and the K. A. Wallenberg Foundation, the Swedish Research Council and the Swedish National Space Board in Sweden.

Additional support for science analysis during the operations phase is gratefully acknowledged from the Istituto Nazionale di Astrofisica in Italy and the Centre National d’Études Spatiales in France. This work performed in part under DOE Contract DE-AC02-76SF00515.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.CAL. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This research was supported by Basic Science Research Program through the National Research Foundation of Korea (NRF) funded by the Ministry of Education ( NRF-2022R1A6A3A03069095).

This publication is part of the M2FINDERS project which has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 Research and Innovation Programme (grant agreement No 101018682).

M.K. and F.R. acknowledge funding by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - grant 434448349.

(ref: abdollahi2020) Abdollahi, S., Acero, F., Ackermann, M., et al. 2020, ApJS, 247, 33

(ref: abdollahi2023) Abdollahi, S., Ajello, M., Baldini, L., et al. 2023, ApJS, 265, 31

(ref: abhir2021) Abhir, J., Joseph, J., Patel, S. R., et al. 2021, MNRAS, 501, 2504

(ref: agarwal2024) Agarwal, S., Shukla, A., Mannheim, K., et al. 2024, ApJL, 968, L1

(ref: agudo2011a) Agudo, I., Jorstad, S. G., Marscher, A. P., et al. 2011a, ApJL, 726, L13

(ref: agudo2011b) Agudo, I., Marscher, A. P., Jorstad, S. G., et al. 2011b, ApJL, 735, L10

(ref: ajello2020) Ajello, M., Angioni, R., Axelsson, M., et al. 2020, ApJ, 892, 105

(ref: atwood2009) Atwood, W. B., Abdo, A. A., Ackermann, M., et al. 2009, ApJ, 697, 1071

(ref: ballet2023) Ballet, J., Bruel, P., Burnett, T. H., et al. 2023, arXiv:2307.12546

(ref: benke2024) Benke, P., Rösch, F., Ros, E., et al. 2024, A&A, 681, A69

(ref: blandford2019) Blandford, R., Meier, D., & Readhead, A. 2019, ARA&A, 57, 467

(ref: boccardi2017) Boccardi, B., Krichbaum, T. P., Ros, E., et al. 2017, A&ARv, 25, 4

(ref: bonato2018) Bonato, M., Liuzzo, E., Giannetti, A., et al. 2018, MNRAS, 478, 1512

(ref: bottcher2007) Böttcher, M. 2007, Ap&&SS, 309, 95

(ref: bottcher2013) Böttcher, M., Reimer, A., Sweeney, K., et al. 2013, ApJ, 768, 54

(ref: bottcher2019) Böttcher, M., & Baring, M. G. 2019, ApJ, 887, 133

(ref: buson2014) Buson, S., Longo, F., Larsson, S., et al. 2014, A&A, 569, A40

(ref: chamani2023) Chamani, W., Savolainen, T., Ros, E., et al. 2023, A&A, 672, A130

(ref: cheung2007) Cheung, C. C., Harris, D. E., Stawarz, Ł. 2007, ApJL, 663, L65

(ref: cohen2014) Cohen, M. H., Meier, D. L., Arshakian, T. G., et al. 2014, ApJ, 787, 151

(ref: conoly2015) Connolly, S. D. 2015, arXiv:1503.06676

(ref: costamante2018) Costamante, L., Cutini, S., Tosti, G., et al. 2018, MNRAS, 477, 4749

(ref: dar1997) Dar, A., & Laor, A. 1997, ApJ, 478, L5

(ref: dodson2017) Dodson, R., Rioja, M. J., Molina, S. N., et al. 2017, ApJ, 834, 177

(ref: edelson1988) Edelson, R. A., & Krolik, J. H. 1988, ApJ, 333, 646

(ref: emma2013) Emmanoulopoulos, D., McHardy, I. M., & Papadakis, I. E. 2013, MNRAS, 433, 907

(ref: finke2019) Finke, J. D. 2019, ApJ, 870, 28

(ref: fuhrmann2014) Fuhrmann, L., Larsson, S., Chiang, J. 2014, MNRAS, 441, 1899

(ref: hodgson2018) Hodgson, J. A., Rani, B., Lee, S. -S., et al. 2018, MNRAS, 475, 368

(ref: jorstad2001a) Jorstad, S. G., Marscher, A. P., Mattox, J. R., et al. 2001a, ApJS, 134, 181

(ref: jorstad2001b) Jorstad, S. G., Marscher, A. P., Mattox, J. R., et al. 2001b, ApJ, 556, 738

(ref: jorstad2013) Jorstad, S. G., Marscher, A. P., Smith, P. S., et al. 2013, ApJ, 773, 147

(ref: kadler2016) Kadler, M., Krauß, F., Mannheim, K. 2016, NatPh, 12, 807

(ref: keenan2021) Keenan, M., Meyer, E. T., Georganopoulos, M., et al. 2021, MNRAS, 505, 4726

(ref: kim2018) Kim, D. -W., Trippe, S., Lee, S. -S. 2018, MNRAS, 480, 2324

(ref: kim2020) Kim, D. -W., Trippe, S., & Kravchenko, E. V. 2020, A&A, 636, A62

(ref: kim2022) Kim, D. -W., Kravchenko, E. V., Kutkin, A. M., et al. 2022, ApJ, 925, 64

(ref: kim2023) Kim, D. -W., Janssen, M., Krichbaum, T. P., et al. 2023, A&A, 680, L3

(ref: kovalev2009) Kovalev, Y. Y., Aller, H. D., Aller, M. F., et al. 2009, ApJL, 696, L17

(ref: kramarenko2022) Kramarenko, I. G., Pushkarev, A. B., Kovalev, Y. Y., et al. 2022, MNRAS, 510, 469

(ref: lee2008) Lee, S. -S., Lobanov, A. P., Krichbaum. T. P., et al. 2008, AJ, 136, 159

(ref: leon2011) León-Tavares, J., Valtaoja, E., Tornikoski, M., et al. 2011, A&A, 532, A146

(ref: liodakis2019) Liodakis, I., Romani, R. W., Filippenko, A. V., et al. 2019, ApJ, 880, 32

(ref: liodakis2020) Liodakis, I., Blinov, D., Jorstad, S. G., et al. 2020, ApJ, 902, 61

(ref: lisakov2017) Lisakov, M. M., Kovalev, Y. Y., Savolainen, T., et al. 2017, MNRAS, 468, 4478

(ref: lister2009) Lister, M. L., Aller, H. D., Aller, M. F., et al. 2009, AJ, 137, 3718

(ref: lobanov1998) Lobanov, A. P. 1998, A&A, 330, 79

(ref: macdonald2015) MacDonald, N. R., Marscher, A. P., Jorstad, S. G., et al. 2015, ApJ, 804, 111

(ref: magic2018) MAGIC Collaboration, Ahnen, M. L., Ansoldi, S., et al. 2018, A&A, 619, A45

(ref: marscher1985) Marscher, A. P., & Gear, W. K. 1985, ApJ, 298, 114

(ref: marscher2008) Marscher, A. P., Jorstad, S. G., D‘Arcangelo, F. D., et al. 2008, Nature, 452, 966

(ref: marscher2010) Marscher, A. P., Jorstad, S. G., Larionov, V. M., et al. 2010, ApJL, 710, L126

(ref: marscher2016) Marscher, A. P. 2016, Galax, 4, 37

(ref: maxm2014a) Max-Moerbeck, W., Hovatta, T., Richards, J. L., et al. 2014a, MNRAS, 445, 428

(ref: maxm2014b) Max-Moerbeck, W., Richards, J. L., Hovatta, T., et al. 2014b, MNRAS, 445, 437

(ref: nair2019) Nair, D. G., Lobanov, A. P., Krichbaum, T. P., et al. 2019, A&A, 622, A92

(ref: okino2022) Okino, H., Akiyama, K., Asada, K., et al. 2022, ApJ, 940, 65

(ref: paliya2018) Paliya, V. S., Zhang, H., Böttcher, M., et al. 2018, ApJ, 863, 98

(ref: plavin2019) Plavin, A. V., Kovalev, Y. Y., Pushkarev, A. B., et al. 2019, MNRAS, 485, 1822

(ref: pushkarev2010) Pushkarev, A. B., Kovalev, Y. Y., & Lister, M. L. 2010, ApJL, 722, L7

(ref: rama2015) Ramakrishnan, V., Hovatta, T., Nieppola, E. 2015, MNRAS, 452, 1280

(ref: rama2016) Ramakrishnan, V., Hovatta, T., Tornikoski, M. 2016, MNRAS, 456, 171

(ref: rani2018) Rani, B., Jorstad, S. G., Marscher, A. P., et al. 2018, ApJ, 858, 80

(ref: roder2024) Röder, J., Ros, E., Schinzel, F. K., et al. 2024, A&A, 684, A211

(ref: sharma2022) Sharma, R., Massi, M., & Torricelli-Ciamponi, G. 2022, A&A, 660, A58

(ref: tavecc2013) Tavecchio, F., Pacciani, L., Donnarumma, I., et al. 2013, MNRAS, 435, L24

(ref: vanzyl2015) van Zyl, P. V., & Gaylard, M. J. 2015, MmSAI, 86, 36

(ref: weaver2022) Weaver, Z. R., Jorstad, S. G., Marscher, A. P., et al. 2022, ApJS, 260, 12

(ref: wehrle2012) Wehrle, A. E., Marscher, A. P., Jorstad, S. G., et al. 2012, ApJ, 758, 72

(ref: wehrle2016) Wehrle, A. E., Grupe, D., Jorstad, S. G., et al. 2016, ApJ, 816, 53

(ref: welsh1999) Welsh, W. F. 1999, PASP, 111, 1347

(ref: white1988) White, G. L., Jauncey, D. L., Savage, A., et al. 1988, ApJ, 327, 561

# The ALMA band 3, 6, and 7 data

Although the data sampling is best in the band 3 (B3), we were able to obtain useful radio light curves of the source at other ALMA bands: band 6 (B6; $\sim$235 GHz) and band 7 (B7; $\sim$345 GHz). Their sampling intervals are, on average, $\sim$66 days with a median value of $\sim$25 days at band 6 and $\sim$14 days with a median value of $\sim$8 days at band 7. Figure [6](#fig:almabands) shows all the ALMA light curves of the source.

For every pair of the two time series (i.e., B3–B6, B6–B7, and B7–B3), we calculated the Pearson correlation coefficients following the manner described in Appendix [7](#sec:panal). The Bin$_{\rm eq}$ ranges were set to be 3–30 days for the B7–B3 pair (i.e., $\sim$930 flux–flux sets) and 3–15 days for the other two pairs with band 6 (i.e., $\sim$830 flux–flux sets). This is due to the poor sampling of the band 6 data which is significantly worse (e.g., 4–5 times) than the other two bands. The Bin$_{\rm eq}$ ranges correspond to NBin$_{\rm eq}$ of $\sim$1040 to $\sim$110 for B7–B3 and $\sim$1040 to $\sim$210 for the others.

The results on the three pairs are shown in Figure [6](#fig:almabands). We find the averages of r$_{\rm P}$ as follow: 0.967$\pm$0.004 (with 1 $\sigma$ uncertainty) for B3–B7, 0.987$\pm$0.002 for B3–B6, and 0.988$\pm$0.005 for B7–B6.

![image](fig/alma3LCs_b3b6b7.pdf)  ![image](fig/Pearson_b3b7.pdf)  ![image](fig/Pearson_b3b6.pdf)  ![image](fig/Pearson_b6b7.pdf)

# Testing Pearson correlation

We investigated linear relationships between the light curves by using the Pearson correlation. For each pair of two time series (e.g., mm & $\gamma$-ray), we determined a time range of the data where it begins at the minimum of the two time series and ends at the maximum of the two time series.

The full time range was divided into equal-sized bins (Bin$_{\rm eq}$) to account for the uneven and random distribution of the data.

To ensure accuracy, this test was repeated in a range of different sizes of Bin$_{\rm eq}$, taking into account the data sampling and source variability; NBin$_{\rm eq}$ is the total number of Bin$_{\rm eq}$ in a single test run.

We calculated an average of all the flux densities belonging to each of the Bin$_{\rm eq}$ and used it as a typical flux density for each of them. Once this process is done throughout all NBin$_{\rm eq}$ on the two light curves separately, we only selected Bin$_{\rm eq}$ overlapping with each other and calculated a Pearson correlation coefficient (r$_{\rm P}$) by using these selected local-mean flux densities.

# Cross-correlation analysis

The Discrete Correlation Function (cite: edelson1988) has been widely employed in the analysis of time-correlation between two light curves. To avoid the normalization issues of DCF (cite: maxm2014b), however, we employed the Local Cross-Correlation Function (cite: welsh1999) in this work. We compute the cross-correlation coefficients with the following DCF and LCCF functions:

$$\begin{gather}

\textup{DCF}(\tau) = M^{-1}\,\left[\frac{\sum(a_{i} - \bar{a}_{0})(b_{j} - \bar{b}_{0})}{\sigma_{a\,0}\,\sigma_{b\,0}}\right], \label{eq:dcf1} \\

\textup{LCCF}(\tau) = M^{-1}\,\left[\frac{\sum(a_{i} - \bar{a}_{\tau})(b_{j} - \bar{b}_{\tau})}{\sigma_{a\,\tau}\,\sigma_{b\,\tau}}\right], \label{eq:lccf1}
\end{gather}$$

where $a_{i}$ & $b_{j}$ being two time series, $\bar{a}_{0}$ & $\bar{b}_{0}$ the mean values for the time series, $\sigma_{a\,0}$ & $\sigma_{b\,0}$ the standard deviation values for the time series, and $M$ the number of ($i,j$) pairs that fall within

the delay bin defined as $\tau\,-\,\Delta t/2\,\leq\,\Delta t_{ij}\,<\,\tau\,+\,\Delta t/2$;

here $\tau$ and $\Delta t$ refer to time delay and a size of the delay bin, respectively. $\bar{a}_{\tau}$, $\bar{b}_{\tau}$, $\sigma_{a\,\tau}$, and $\sigma_{b\,\tau}$ are the same as above, but only for those $M$ overlapping samples. We determine the uncertainties i.e., $\sigma_{\rm DCF}(\tau)$ and $\sigma_{\rm LCCF}(\tau)$ by measuring a statistical dispersion for each DCF($\tau$) and LCCF($\tau$), respectively (cite: maxm2014b). The main difference between the two approaches is that LCCF only considers data points overlapping within

the delay bin between two time series.

(cite: maxm2014b) made a comparison between DCF and LCCF, and concluded that LCCF is better than DCF in terms of e.g., detection efficiency. For more details of the comparison, we refer to (cite: maxm2014b). We also tested these two functions with our datasets. Figure [7](#fig:ccfcomp) shows the result. As evident from it, the LCCF curve returns higher coefficient values. Both the LCCF and DCF curves peaked at $\tau$ = 0. However, we find that the peak of the LCCF curve is much closer to the mean of the Pearson coefficients presented in Figure [3](#fig:coreps). Thus, we consider that LCCF is a more accurate way to search for time-correlation in this study.

We evaluated the resultant LCCF curves by using their confidence levels. The overall procedure is similar to the manner of (cite: kim2022). We simulated 100,000 artificial $\gamma$-ray light curves and computed LCCF curves between those simulated $\gamma$-rays and the observed ALMA band 3 light curve. For every $\tau$, we draw a cumulative distribution function (CDF) of the correlation coefficients and find the 68%, 95%, and 99.9% confidence levels. Based on these confidence levels, we determine the significance of the LCCF peaks.

![](fig/CCFcomparison.pdf)

The artificial $\gamma$-ray light curves were generated in the manner of (cite: emma2013). Most of the time, was bright at $\gamma$-rays and there are a small number of bad/empty bins. Using linear interpolation, we complemented these bins and thus made the light curve evenly distributed. Then, we find a power spectral density (PSD) and a probability density function (PDF) of the $\gamma$-rays with this interpolated light curve. A bending power-law model and the mixture model (i.e., a combination of the gamma and log-normal distributions) introduced by (cite: emma2013), were applied to a periodogram and histogram of the data, respectively. Figure [8](#fig:gpsdpdf) shows the best-fit PSD and PDF models. Then, the artificial $\gamma$-ray light curves were generated with a Python implementation `DELCgen` (cite: conoly2015) that follows the algorithm of (cite: emma2013), by using the estimated PSD & PDF parameters [^5]. Finally, we modified the sampling of all the artificial $\gamma$-ray light curves to make them the same as the observed $\gamma$-ray light curve in the time domain.

![image](fig/gPSD.pdf)  ![image](fig/gPDF.pdf)

# Tests on the LCCF curves

Figure [9](#fig:othlccf) shows the LCCF curves between the $\gamma$-ray and ALMA band 3 light curves with larger $\Delta t$ values (i.e., 12, 30, and 60 days). We find again a significant (i.e., $>$ 99.9%), strong mm–$\gamma$-ray correlation at around $\tau$ = 0 (zero-lag). The overall shape of the LCCF curves are consistent with each other. However, those statistical fluctuations along the curves become smoother and weaker with increasing $\Delta t$. Some of the small humps (e.g., the one at around $\tau$ $\sim$ $-$120 days) completely disappear with $\Delta t$ = 60 days. They could be artifacts or short-term, local correlations. Thus, higher $\Delta t$ values could be helpful to identify a long-term correlation that remains throughout the whole period of the data.

![image](fig/LCCF_DT12.pdf) ![image](fig/LCCF_DT30.pdf) ![image](fig/LCCF_DT60.pdf)

# Gaussian fit to the LCCF curves

In Figure [10](#fig:theb7curve), we fit a single Gaussian to the LCCF curve between the LAT and ALMA band 7 light curves; we omitted the confidence levels for clarity, but the central hump is also above the 99.9% level. $\Delta t$ was set to be 8 days that is the median sampling of the band 7 light curve. To better fit the model to the data and focus on the significant central LCCF hump, we only used the LCCF points higher than the peak of a first strong, distinct side-lobe (i.e., LCCF = $\sim$0.48). The result can be found in the upper panel of Figure [11](#fig:gausfits).

We also estimate a peak position of the LCCF hump between the LAT and band 3 light curves (i.e., Figure [4](#fig:lccfmain)), by using the same manner as Figure [10](#fig:theb7curve). We show the result in the lower panel of Figure [11](#fig:gausfits).

Owing to the poor sampling of the band 6, we skip the band 6 data in the LCCF analysis; the statistical fluctuations and huge side-lobes occupy the LCCF curve between the LAT and band 6 data throughout the whole $\tau$ values. We note that the Gaussian model well describes both the LCCF curves shown above, and the results are irrelevant to the bin size ($\Delta t$).

![](fig/GausB7_LCCF1.pdf)

![image](fig/GausB7_LCCF2.pdf)  ![image](fig/GausB3_LCCF2.pdf)

[^1]: <https://fermi.gsfc.nasa.gov/ssc/data/analysis/scitools/>

[^2]: <https://fermi.gsfc.nasa.gov/ssc/data/analysis/scitools/source_models.html>

[^3]: <https://almascience.eso.org/alma-data/calibrator-catalogue>

[^4]: <https://www.eso.org/public/teles-instr/alma/receiver-bands/>

[^5]: PSD: $A=0.16\pm1.20$ Hz$^{-1}$, $f_{\rm bend}=0.004\pm0.011$ Hz, $\alpha_{\rm low}=0.84\pm1.04$, $\alpha_{\rm high}=2.22\pm0.99$, $C=0.10\pm0.04$ Hz$^{-1}$, and PDF: $\kappa=17.94\pm9.42$, $\theta=0.30\pm0.15$, $\mu=1.70\pm0.03$, $\sigma=0.67\pm0.04$, $w_{\Gamma}=0.20\pm0.09$. For their mathematical forms, we refer to equations 2 & 3 in (cite: emma2013).

</paper>

Write the methods card for this paper.