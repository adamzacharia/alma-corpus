# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...910...89B\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...910...89B",
 "title": "The Physical Drivers of the Luminosity-weighted Dust Temperatures in High-redshift Galaxies",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Burnham, Anne D.",
 "n_authors": 10,
 "arxiv_id": "2102.06250",
 "doi": "10.3847/1538-4357/abe401",
 "alma_projects_linked_by_archive": [
  "2015.1.00568.S"
 ]
}
```

Paper text:
<paper>
# The Physical Drivers of the Luminosity-Weighted Dust Temperatures in High-Redshift Galaxies

## Abstract

The underlying distribution of galaxies’ dust SEDs (i.e., their spectra re-radiated by dust from rest-frame $\sim$ 3 $\mu$m – 3 mm) remains relatively unconstrained due to a dearth of FIR/(sub)mm data for large samples of galaxies. It has been claimed in the literature that a galaxy’s dust temperature—observed as the wavelength where the dust SED peaks ( $\lambda_{\rm peak}$)—is traced most closely by its specific star-formation rate (sSFR) or parameterized ‘distance’ to the SFR– M$_\star$ relation (the galaxy ‘main sequence’). We present 0.24$''$ resolved 870 $\mu$m ALMA dust continuum observations of seven $z=1.4-4.6$ dusty star-forming galaxies (DSFGs) chosen to have a large range of well-constrained luminosity-weighted dust temperatures. We also draw on similar resolution dust continuum maps from a sample of ALESS submillimeter galaxies from (cite: hodge16a). We constrain the physical scales over which the dust radiates and compare those measurements to characteristics of the integrated SED. We confirm significant correlations of  $\lambda_{\rm peak}$ with both L$_{\rm IR}$ (or SFR) and $\Sigma_{\rm IR}$ ($\propto$SFR surface density). We investigate the correlation between $\log_{10}$( $\lambda_{\rm peak}$) and $\log_{10}$($\Sigma_{\rm IR}$) and find the relation to hold as would be expected from the Stefan-Boltzmann Law, or the effective size of an equivalent blackbody. The correlations of  $\lambda_{\rm peak}$ with sSFR and distance from the SFR– M$_\star$ relation are less significant than those for $\Sigma_{\rm IR}$ or L$_{\rm IR}$; therefore, we conclude that the more fundamental tracer of galaxies’ luminosity-weighted integrated dust temperatures are indeed their star-formation surface densities in line with local Universe results, which relate closely to the underlying geometry of dust in the ISM.

# Introduction

Dusty Star-Forming Galaxies (DSFGs) have incredibly high star-formation rates and in the first few Gyr produce $\sim$ $50\%$ of the stellar mass in the Universe (cite: casey12b; Gruppioni13a). They are vitally important to galaxy evolution, but many of their fundamental dust characteristics are not well studied. Though their far-infrared through millimeter spectral energy distributions (SEDs) are relatively straightforward to interpret as a linear combination of modified blackbodies from dust, which re-radiates nascent starlight, the lack of detailed photometry along that SED (rarely exceeding a few measurements across a 1000 $\mu$m range) has limited our understanding of the physics governing that dust in the interstellar medium (ISM). This includes the physical scales over which the dust radiates and how clumpy it is, perhaps tracing back to its origins in/around compact star clusters. Physically tracing the relationship between integrated SEDs and underlying geometry is critically important.

A major challenge in characterizing galaxies’ dusty SEDs has been the fundamental limitation of infrared through radio datasets, particularly for high-$z$ galaxies. For ten years before 2010 most analysis was limited to SCUBA flux densities along the Rayleigh-Jeans (RJ) tail of blackbody emission, which made it impossible to constrain both the IR luminosity and dust temperature of a given high-$z$ galaxy. Even the vast improvement ushered in by *Herschel* in the last decade has fundamental limitations given the telescope’s large beamsize at 250 $\mu$m$-$500 $\mu$m, where SEDs of $z=1-3$ galaxies peak. The uncertainty brought on by confusion noise, added with the relatively shallow depth of *Herschel* surveys provides some moderate breakthroughs in measuring galaxies’ dust temperatures across cosmic time (cite: symeonidis13a; lee13a).

Dust temperature is observationally constrained through measurement of  $\lambda_{\rm peak}$, the wavelength at which the SED peaks in the rest-frame, which is inversely proportional to the underlying physical dust temperature via Wien’s law (cite: wien1897). The precise mapping of  $\lambda_{\rm peak}$ to T$_{\rm d}$ depends on the underlying opacity of the dust in the ISM (cite: casey14a) and thus T$_{\rm d}$ is usually unconstrained without spatially-resolved observations. Empirical datasets have shown us that DSFGs at all epochs have higher temperatures at higher IR luminosities (cite: casey14a). This relationship is akin to a Stefan-Boltzmann law for the cold ISM on galaxy scales even without direct accounting for sources’ emitting regions or underlying dust opacity. Indeed, previous studies in the local universe see a relationship between the star-formation rate surface density, $\Sigma_{\rm IR}$, and integrated galaxy SED dust temperatures (cite: chanial07; lutz16a) as would be expected given a Stefan-Boltzmann type relation. This physical reasoning has also been used to interpret the integrated SEDs of high-redshift dusty galaxies (cite: hodge16a; simpson17) though some discrepancies in interpretation remain.

Trends in galaxies’ dust temperatures at high redshifts have been measured frequently in the literature with somewhat mixed, potentially contradictory results. Some suggest evolution toward colder dust temperatures for higher redshift systems (cite: casey12b; symeonidis13a; lee13a; kirkpatrick17a) while others suggest evolution toward warmer dust temperatures at higher redshifts (cite: magdis12a; magnelli14a; bethermin15a; bethermin17; schreiber18). All of these works attempt to quantify the underlying physical drivers of galaxies’ bulk dust temperatures. We describe the basis of these claims and how they are not actually contradictory to one another in a broader context in Section [2](#sec:context) of this paper. We use this diverse range of claims, and the physics used to explain them, as motivation for this study.

![image](DustMassImagesForPaper.pdf)

![image](oircutouts.pdf)

In this paper, we have selected a sample of seven DSFGs with a wide range of measured dust temperatures and confirmed spectroscopic redshifts for high spatial-resolution submillimeter (submm) follow-up to directly test for correlation between dust temperature and other galaxy characteristic quantities. We use new resolved dust continuum maps from ALMA band 7 observations at 870 $\mu$m of these seven DSFGs to investigate the hypothesis that dust temperature maps directly to other observable characteristics such as galaxy size, morphology, star-formation surface density, and sSFR. We also include eleven ALESS sources in our analysis from (cite: hodge16a), whose observations and sample are similar, though their sources were 1.3$\times$ brighter and observations were slightly shallower. Section [2](#sec:context) provides background from the literature giving more in-depth motivation for this investigation. Section [3](#sec:sample) describes sample selection and observations. Section [4](#sec:results) gives our calculations of key physical properties of the relevant DSFGs. In Section [5](#sec:discussion), we discuss our findings, and we provide our conclusions in Section [6](#sec:conclusion). We assume a concordance cosmology throughout this paper, adopting $H_{0}=70\,$km s$^{-1}$ Mpc, $\Omega_{M}=0.3$, and $\Omega_{\Lambda}=0.7$. Where SFRs are used, we assume a Kroupa IMF (cite: kroupa03a) and scaling relations drawn from (cite: kennicutt12).

# Context of Galaxies’ Dust Temperatures

We draw motivation for this detailed study of a subsample of galaxies with high-quality resolved millimeter dust maps from the many discussions presented in the literature of trends in galaxies’ overall dust temperatures with redshift. This section provides context of these discussions.

Dust is heated by a radiation field with an intensity represented by $U$. The dust is heated in two environments: the ambient radiation field heating the diffuse ISM and discrete photon heating within star-forming regions. The diffuse ISM portion is heated by a radiation field with constant $U_{\rm min}$, and the other portion is heated by radiation (primary and secondary photons) from young stars with intensities ranging from $U_{\rm min}$ and $U_{\rm max}$ (cite: magdis12a). The equation governing the dust-weighted mean starlight intensity scale factor, $\langle\!U\!\rangle$ is defined in (cite: magdis12a). From this equation, $\langle\!U\!\rangle$ is proportional to L$_{\rm IR}$/M$_{\rm dust}$. A corollary is that the luminosity-weighted dust temperature correlates directly with $\langle\!U\!\rangle$. The stronger the radiation field, the higher the dust temperature. Similarly, the more compact the dust around the source of incident radiation, the hotter the dust.

(cite: magdis12a) used samples of *Herschel*-detected galaxies to argue that the galaxy IR-spectral energy distribution depends solely on $\langle\!U\!\rangle$ and is independent of sSFR and  M$_\star$. They also argue that $\langle\!U\!\rangle$ evolves with time such that main sequence galaxies at earlier epochs had more intense radiation fields, or higher $\langle\!U\!\rangle$. They find that T$_{\rm d}$ evolves with time such that main sequence galaxies at higher $z$ (out to $z \sim 2$) have warmer temperatures than those at $z = 0$. Note that this is not necessarily contradictory to the finding that $z \sim 2$ galaxies have colder SEDs than $z \sim 0$ galaxies of similar L$_{\rm IR}$; this is due to the dramatic evolution in the main sequence between these epochs.

(cite: magnelli14a) used *Herschel* observations to propose stronger correlations of T$_{\rm d}$ with specific star formation rate (sSFR) and parameterized distance to the main sequence (D$_{\rm MS}$) rather than with L$_{\rm IR}$ explicitly. The correlation is such that dust temperature is fixed for a fixed redshift and sSFR, implying that galaxies with a particular sSFR contain star-forming regions with similar $\langle\!U\!\rangle$. An increase in these star-forming regions results in the increase of SFR (star formation rate) with stellar mass ( M$_\star$). Since starbursts have higher SFRs than galaxies with equivalent masses on the main sequence, more intense radiation fields coupled with higher densities could cause the elevated dust temperatures (cite: magnelli14a).

A number of additional works also find an increasing dust temperature for main sequence galaxies, including (cite: bethermin17) and (cite: schreiber18), among others. (cite: magdis12a) and (cite: bethermin15a) assert that the evolution of $\langle\!U\!\rangle$ points to an evolution of T$_{\rm d}$ for all galaxies on the main sequence. (cite: magdis12a) and (cite: schreiber18) posit that the evolution of main sequence galaxy SEDs with redshift proves an evolution in T$_{\rm d}$.

In contrast to the works that find an evolution toward hotter dust temperatures for main sequence galaxies at higher redshifts, several papers report that high redshift galaxies evolve toward *colder* temperatures at higher redshifts, in particular at $z \sim 2$ relative to galaxies at $z \sim 0$. Such colder temperatures have been inferred based on galaxies of fixed SFR or L$_{\rm IR}$, and credited possibly to more extended dust geometries in high redshift galaxies (cite: casey12b; symeonidis13a). However, (cite: casey18a) argue that this perceived evolution toward colder temperatures could, in part, be a bias in underlying datasets that exist for $z \sim 0$ dust SEDs versus those at $z \sim 2$, and that most of the evolution, if it does exist, is between $0<z<0.4$. Further work is needed to understand if this very low redshift evolution is physically real or purely driven by limits in the existing datasets (Drew et al. in preparation).

Beyond $z \sim 0.5$ and out to $z \sim 5$, (cite: casey18b) find no evidence for redshift evolution of galaxies’ SEDs in the L$_{\rm IR}$- $\lambda_{\rm peak}$ plane. Similarly, (cite: dudzeviciute20a) find no evidence for evolution in dust temperature for galaxies as a function of fixed L$_{\rm IR}$. How can these seemingly disparate conclusions—that SEDs of main sequence galaxies evolve yet there is no observed evolution in L$_{\rm IR}$- $\lambda_{\rm peak}$ with $z$—be reconciled? These results are not, in fact, contradictory. In the main sequence, SFR (or L$_{\rm IR}$) evolves with $z$, but  $\lambda_{\rm peak}$ does not evolve at fixed SFR. A direct correlation between L$_{\rm IR}$ and  $\lambda_{\rm peak}$, or dust temperature, is well-established (cite: sanders03; chapman03b; casey18b) and has been shown to be driven by increased dust heating in more luminous systems (cite: symeonidis13a) and to be independent of luminosity-limit selection effects (cite: sajina07a; lee13a). As objects in the MS evolve toward higher luminosities (and correspondingly, higher $\langle\!U\!\rangle$) with $z$,  $\lambda_{\rm peak}$ appears to evolve with redshift at fixed  M$_\star$ due to its correlation with L$_{\rm IR}$. Thus the perceived T$_{\rm d}$–$z$ evolution holds only for fixed sSFR, D$_{\rm MS}$, or  M$_\star$, and not for fixed SFR.

In this paper, we explore the dependence of  $\lambda_{\rm peak}$ on SFR, sSFR, star formation surface density, and parameterized distance to the main sequence to better understand the underlying physical drivers of galaxies’ integrated SED-averaged dust temperature.

# Sample and Observations

## Sample Selection

Seven unlensed, spectroscopically-confirmed DSFGs were chosen from 400 arcmin$^2$ SCUBA-2 450 $\mu$m and 850 $\mu$m maps of the inner COSMOS field (cite: casey13a). Of the 31 SCUBA-2 detected COSMOS sources with spectroscopic redshifts in (cite: casey17a), we selected seven of the brightest sources (single-dish S$_{850} > 2$ mJy) to span a very broad range of dust SEDs from cold ($\sim$ 18 K) to warm ($\sim$ 70 K) based on their *Herschel* SPIRE and SCUBA-2 photometry. The DSFGs were selected at the time for having known spectroscopic redshifts between $z = 1-3$ (cite: casey17a), and updated information on this sample gives a total spanned redshift range of $1.4<z<4.6$. The galaxy initially thought to have the coldest SED, 450.03 (also known as AzTEC2), was identified initially to have a spectroscopic redshift of 1.123 from an OIR counterpart (cite: casey17a) but is now confirmed to sit at $z=4.61$ from a serendipitous detection of \[CII\] in our ALMA data and concurrent confirmation via CO(5-4) line emission from NOEMA observations (cite: jimenez20). The ALMA centroid is offset from the OIR source by 1.6$''$ (see (cite: casey17a) for details). The redshift for source 850.04 was originally estimated to be $z=1.436$, but closer inspection reveals a more likely redshift solution of $z=3.31^{+0.76}_{-0.81}$, which is a photometric redshift from the (cite: laigle16a) COSMOS catalog. This photometric counterpart is 1.0$''$ offset from the spectroscopically confirmed source at $z=1.436$ (cite: casey17a) but significantly closer (0.3$''$) from the centroid of ALMA emission.

## ALMA Data

![](FluxPlot.pdf)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $z$ | S$_{\rm 870}$ | R$_{\rm e}$ |  $\lambda_{\rm peak}$ | L$_{\rm IR}$ | SFR | M$_\star$ |
|  |  | \[mJy\] | \[ kpc\] | \[$\mu$m\] | \[ L$_\odot$\] | \[ M$_\odot$/yr\] | \[ M$_\odot$\] |
| 450.03 | 4.629$^{a}$ | 19.12$\pm$0.16 | 1.35$^{b}$$\pm$0.06 | 71.4$\pm$7.8 | (3.28$\pm$0.68)$\times\,10^{13}$ | 4900$\pm$1000 | $-$$^{c}$ |
| 850.04 | 3.31 | 13.67$\pm$0.12 | 1.94$\pm$0.12 | 98$\pm$9 | (8.9$\pm$1.2)$\times\,10^{12}$ | 1330 $\pm$180 | (2.2$\pm$0.8)$\times\,10^{10}$ |
| 450.14 | 1.523 | 2.05$\pm$0.03 | 2.8$\pm$0.4 | 130$\pm$30 | (1.2$\pm$0.7)$\times\,10^{12}$ | 190$\pm$100 | $-$$^{c}$ |
| 850.60 | 1.457 | 2.21$\pm$0.04 | 1.81$\pm$0.28 | 75$\pm$9 | (1.9$\pm$ 0.4)$\times\,10^{12}$ | 290$\pm$60 | (2.1$^{+0.1}_{-0.2}$)$\times\,10^{11}$ |
| 850.95 | 1.556 | 1.21$\pm$0.03 | 6.1$\pm$1.4. | 98$\pm$22 | (1.2$\pm$0.5)$\times\,10^{12}$ | 180$\pm$80 | (3.8$^{+0.4}_{-1.0}$)$\times\,10^{10}$ |
| 850.25 | 2.438 | 5.76$\pm$0.05 | 2.76$\pm$0.22 | 117$\pm$20 | (3.1$\pm$1.1)$\times\,10^{12}$ | 460$\pm$170 | (2.8$^{+0.1}_{-0.4}$)$\times\,10^{11}$ |
| 450.09 | 2.472 | 6.07$\pm$0.07 | 1.04$\pm$0.07 | 71$\pm$10 | (8.3$\pm$1.5)$\times\,10^{12}$ | 1240$\pm$230 | (2.2$^{+0.1}_{-0.4}$)$\times\,10^{11}$ |
| ALESS 3.1 | 4.24 | 8.3$\pm$0.4 | 1.30$\pm$0.05 | 69$\pm$9 | (1.64$\pm$0.25)$\times\,10^{13}$ | 2460$\pm$380 | (2.3$^{+1.0}_{-1.6}$)$\times\,10^{11}$ |
| ALESS 5.1 | 2.86 | 7.8$\pm$0.7 | 2.00$\pm$0.10 | 106$\pm$12 | (4.9$\pm$1.0)$\times\,10^{12}$ | 730$\pm$150 | (2.9$^{+0.2}_{-0.8}$)$\times\,10^{11}$ |
| ALESS 9.1 | 4.50 | 8.8$\pm$0.5 | 1.50$\pm$0.05 | 71$\pm$9 | (1.63$\pm$0.26)$\times\,10^{13}$ | 2430$\pm$390 | (5.6$^{+1.3}_{-2.7}$)$\times\,10^{11}$ |
| ALESS 10.1 | 0.76 | 5.3$\pm$0.5 | 2.60$\pm$0.20 | 190$\pm$9 | (2.3$\pm$0.4)$\times\,10^{11}$ | 34.5$\pm$5.5 | (1.2$\pm$0.3)$\times\,10^{10}$ |
| ALESS 15.1 | 1.93 | 9.0$\pm$0.4 | 2.40$\pm$0.10 | 125$\pm$5 | (2.95$\pm$0.24)$\times\,10^{12}$ | 440$\pm$40 | (3.1$^{+1.3}_{-1.8}$)$\times\,10^{11}$ |
| ALESS 17.1 | 1.54 | 8.4$\pm$0.5 | 1.75$\pm$0.05 | 138$\pm$5 | (1.88$\pm$0.18)$\times\,10^{12}$ | 281$\pm$27 | (2.3$^{+0.1}_{-1.7}$)$\times\,10^{11}$ |
| ALESS 29.1 | 1.44 | 5.9$\pm$0.4 | 1.35$\pm$0.05 | 136$\pm$12 | (1.37$\pm$0.23)$\times\,10^{12}$ | 200$\pm$30 | (3.0$^{+1.2}_{-2.1}$)$\times\,10^{11}$ |
| ALESS 39.1 | 2.44 | 4.3$\pm$0.3 | 1.95$\pm$0.10 | 100$\pm$7 | (3.3$\pm$0.4)$\times\,10^{12}$ | 490$\pm$70 | (4.5$^{+1.0}_{-1.6}$)$\times\,10^{10}$ |
| ALESS 45.1 | 2.34 | 6.0$\pm$0.5 | 2.15$\pm$0.15 | 117$\pm$10 | (2.7$\pm$0.5)$\times\,10^{12}$ | 400$\pm$70 | (5.1$^{+1.5}_{-2.3}$)$\times\,10^{11}$ |
| ALESS 67.1 | 2.12 | 4.5$\pm$0.4 | 1.85$\pm$0.15 | 72.2$\pm$2.6 | (9.4$\pm$0.9)$\times\,10^{12}$ | 1400$\pm$140 | (2.4$^{+2.4}_{-2.1}$)$\times\,10^{11}$ |
| ALESS 112.1 | 2.32 | 7.6$\pm$0.5 | 1.90$\pm$0.10 | 109$\pm$6 | (4.1$\pm$0.5)$\times\,10^{12}$ | 610$\pm$70 | (1.0$^{+0.4}_{-0.5}$)$\times\,10^{11}$ |

: Redshifts, total flux densities, half-light radii as measured by IMFIT at 870 $\mu$m, rest-frame SED peak wavelengths, infrared luminosities, star formation rates, and stellar masses for our COSMOS SCUBA-2 and ALESS sources. Measurements of peak wavelengths, infrared luminosities, and star formation rates are done by the same method for both the COSMOS sample and the eleven ALESS sources we analyze. Measurements for 450.03 are for the total circularized size and total L$_{\rm IR}$ of both components. ALESS flux densities are from (cite: swinbank14a), and sizes are from (cite: hodge16a) derived in a fully consistent manner as for our COSMOS sample.

Table notes: $^{a}$ The precision quoted on the redshift indicates whether or not the source has a spectroscopic redshift (four significant figures) or a photometric redshift (three significant figures). $^{b}$ Total circularized size of both components of 450.03. The individual half-light radii measured by IMFIT are 1.24 kpc for the brightest source and 1.08 kpc for the secondary source. $^{c}$ Stellar masses are not provided for 450.03 or 450.14. In the case of 450.03, this is due to significant blending with several foreground galaxies on angular scales that precludes measurement of near-infrared *Spitzer* flux densities; in the case of 450.14, there is a superposition of two galaxies of different redshifts within a 2$''$ region, making a proper separation of the background/foreground stellar mass distribution impossible. Both cases are discussed at greater length in (cite: casey17a).

Observations of these seven DSFGs were carried out as part of the ALMA Cycle 3 program 2015.1.00568.S (PI Casey). With a requested spatial resolution of 0.1$''$, observations were made in both compact (C36-3) and extended (C36-6) configurations. The compact and extended configurations had maximum baselines of 462.9 m  and 1.8 km, respectively, with 36 antennas. The observations targeted dust continuum emission at the nominal band 7 frequency centered at 345 GHz or 870 $\mu$m. At this frequency, ALMA has a 17.3$''$ primary beam (FWHM), and we utilized the “single continuum” spectral mode.

We reduced and calibrated the raw data from the compact configuration to produce *uv*-data products using the Common Astronomy Software Applications (CASA) version 4.5.3. During calibration, data from antennas with irregular amplitudes were flagged. To produce optimum images for total flux recovery, we imaged the compact-configuration data using the CLEAN algorithm of CASA with Briggs weighting and robust = 2 (equivalent to natural weighting) and applied a primary beam correction. The resulting images have a resolution of 0.68$''$ $\times$ 0.49$''$. The compact data set was used in calculating the flux densities, which are given in Table [1](#tab:observations).

We created a higher resolution set of maps by combining the raw data from the compact and extended configurations, then reducing and calibrating the data using the same method described above. We tested different robust values with the CLEAN algorithm and found the resulting size of each source to be consistent and independent of the robust parameter. Thus, we adopt a robust value of 1 for the full sample as it maximizes the source signal-to-noise for the most extended source in the sample (850.95) while maintaining a relative high angular resolution. The resulting resolution is 0.24$''$ $\times$ 0.27$''$. This does not meet the requested 0.12$''$ resolution, but even with a robust value of 0, the spatial resolution is still not as good as requested. The combined data was used to calculate the effective radii, which are also given in Table [1](#tab:observations). Images of the sample are shown in Figure [1](#fig:dustmass) and overlays with optical/near-IR data are shown in Figure [2](#fig:oircutouts) on the same scale.

## Biases in the Sample?

The data sample used in this analysis does not fully sample the full parent population of galaxy dust SEDs but is representative of the breadth of DSFGs at high-$z$. The COSMOS sources from (cite: casey17a) were chosen explicitly to have the broadest range of SEDs and are selected at either of 450$\mu$m or 850$\mu$m, which together is unbiased with respect to SED dust temperatures in the range of 20K–100K (cite: roseboom13a; casey13a). The ALESS sample selected at 870$\mu$m only is more likely to be biased toward colder dust temperatures (cite: chapman04c; casey09b), but we see a large range of temperatures well represented in the sample, similar to the COSMOS sample.

Furthermore, while 870$\mu$m selection alone is intrinsically biased and favoring sources with colder SEDs, those that have well-sampled FIR SEDs (and high-resolution ALMA imaging) are not biased with respect to $\lambda_{\rm peak}$ because detection in the *Herschel* bands bracketing the SED peak is implicitly required. In other words, many ALESS sources without *Herschel* SPIRE detections (i.e. those with cold SEDs) would not have well-sampled FIR SEDs, are unlikely to have received high-resolution ALMA follow-up, and thus are excluded from our analysis here.

The sample (both COSMOS and ALESS DSFGs) could be seen as biased toward galaxies with high SFRs, but sources with high SFRs are the only ones for which the high spatial resolution measurements made in this paper are possible with a reasonable investment in ALMA time. This has potential impact on our ability to probe the relationship between  $\lambda_{\rm peak}$ and L$_{\rm IR}$ in a fully unbaised way, given the limited dynamic range compared to galaxy populations at large. This is discussed more fully in section [5.2.2](#sec:lpeaklir). The combined sample does sample galaxies’ relative distance from the main sequence well, in line with the expected dynamic range of much larger populations of studied galaxies. They span two orders in magnitude in specific star-formation rate from $\sim$0.6–60 Gyr$^{-1}$, and about one order of magnitude in orthogonal distance from the main sequence; more methods to quantify galaxies’ distance to the main sequence are discussed later in section [4.4](#sec:mainsequence).

The primary goal of this work is to assess the relative strength of correlation between luminosity-weighted dust temperature (as measured observationally through the proxy $\lambda_{\rm peak}$) and other physical characteristics of high-$z$ galaxies, including quantities constrained by the FIR-emitting region as measured by high-resolution ALMA dust continuum imaging. Thus, this set of observations constitutes a well-constructed and relatively unbiased sample for our purposes.

# Calculations & Results

##  ALMA 870$\mu$m Flux Densities

Total integrated flux densities were measured directly from the compact ALMA data using a method similar to the one described in (cite: hodge16a). We converted the maps from Jy beam$^{-1}$ to mJy pixel$^{-1}$ and masked emission less than 2$\sigma$. We then summed contiguous emission within an aperture of radius 3 $\times$ $b_{\rm maj}$, where $b_{\rm maj}$ is the FWHM (major axis) of the synthesized beam. The resulting total band 7 flux densities are given in Table [1](#tab:observations). The median flux density of our seven sources is 5.8 $\pm$ 3.7 mJy at 870$\mu$m.

In general, when measuring the flux density, only contiguous emission was summed, with one exception. Source 450.03 is composed of two sources separated by 3$''$  at the same redshift (cite: jimenez20), both of which were included in the total reported flux density.

To check our flux density calculations, we used the IMFIT tool in CASA and found that our calculations agree with the IMFIT-derived densities for all but one of our sources. Source 850.95 differed with less than 2$\sigma$ significance of deviation. The average ratio between IMFIT and aperture flux density measurements was $0.96\pm0.10$.

In addition, we compare the flux densities as measured by ALMA to the single-dish flux densities obtained for the COSMOS sources from SCUBA-2 at 850 $\mu$m using the single-dish JCMT and for the ALESS sources from LABOCA at 870 $\mu$m. The average ratio of ALMA to single-dish flux densities was $0.94\pm0.21$, as shown in Figure [3](#fig:fluxplot). Note that the expected ratio of 850 $\mu$m to 870 $\mu$m flux is $\approx$ 0.9 for Rayleigh-Jeans tail emission.

## Measuring Dust Sizes and Morphology

We quantitatively examine the size of the 870$\mu$m dust emission by fitting each source in the image plane with two-dimensional Sersic and Gaussian models. The Sersic model was applied using GALFIT, and the Gaussian model was applied using CASA IMFIT.

Dust emission half-light effective radii (R$_{\rm e}$) were measured using GALFIT on the ALMA maps in the image plane. GALFIT is a 2D fitting tool that models the profiles of astronomical objects using parametric functions (cite: peng10a). Here we use GALFIT on ALMA data to test for non-Gaussian source morphologies, which is most easily applied in the image plane. The full width at half maximum (FWHM) was measured for each source using CASA IMFIT, which is also applied in the image plane. Most of our sources are moderately resolved—more than two beams across in size—so size measurements are unlikely to be affected by fitting methods. Thus, making measurements in the image plane rather than the *uv* plane is justified.

To address whether the weighting applied with the CLEAN algorithm has an impact on size measurement in the image plane, measurements were also made in the *uv* plane using CASA UVMODELFIT to fit a Gaussian model. The UVMODELFIT and IMFIT measurements agree within uncertainties for four of our sources. There is a discrepancy between *uv* and image plane sizes for 450.03 and 850.25, which we attribute to significant excess emission from the core of the systems, which is evident in the IMFIT residual images. There was also a discrepancy in the measurements for source 850.95, which we attribute to the IMFIT model extending beyond the region of significant flux associated with the source. In general, the measured Gaussian FWHMs in the *uv* plane are systematically offset from the FWHMs in the image plane measured by IMFIT such that the median ratio of *uv*-plane to image-plane FWHMs is 0.81 $\pm$ 0.08. Our scientific results rely on relative size comparisons of objects within the sample (and extended to the ALESS sample) rather than absolute sizes.

The results of GALFIT are shown in Figure [4](#fig:galfit) along with the residuals and models. It is a known problem that errors from GALFIT are underestimated; therefore, we used the IMFIT results in our analysis and report IMFIT sizes in Table [1](#tab:observations).

The sizes measured here are the mass-weighted sizes–measured on the Rayleigh-Jeans tail of the SED–rather than the luminosity-weighted sizes, which we would measure closer to the peak of the SED. The only exceptions to this are those galaxies that sit at $z>3$ in our sample (5 of 18); at these redshifts, observed 870$\mu$m probes rest-frame wavelengths shortward of 200$\mu$m, which may be more prone to tracing an optically thick regime of the SED in some cases (dependent on the actual dust column). We explore the impact of these higher redshift sources on our final results later in Section [5](#sec:discussion). A dearth of data in the literature makes it difficult to know whether measured size varies substantially along the RJ tail, but the limited one-off measurements that do exist suggest it is safe to assume any measurement on the tail should be consistent within measurement uncertainties. In addition, these sizes are distinct from the sizes of the galaxies traced by stellar emission; the two are often spatially distinct in DSFGs, such that the rest-frame UV/optical emission is heavily obscured by dust, and thus, does not serve as an adequate probe of the characteristic scale of the ISM (cite: biggs08a; chen15a; hodge15; hodge16a; lang19). It should also be noted that dust continuum sizes are systematically smaller and not entirely consistent with radio continuum sizes (which probe synchrotron emission scattering off of supernova remnants), the measurements of which exist for much larger samples than those with dust continuum size measurements (cite: miettinen17a).

The effective radii measured by GALFIT range from 0.13$''$$-$0.69$''$ with a median of R$_{\rm e}$$=$ 0.32$''$ $\pm$ 0.09$''$. Using the redshift of each source, we convert these angular sizes to physical sizes, which range from 1.1$-$5.9  kpc (median R$_{\rm e}$$= 2.7 \pm$ $0.8$ kpc). Source 850.95 was an outlier at $5.9 \pm 3.3$  kpc. It is known to be somewhat abnormally large as also traced by H$\alpha$ kinematics (cite: drew18). Source 850.95 also has the lowest signal-to-noise ratio among our sources. The remaining sources ranged from 1.1$-$3.2  kpc (median R$_{\rm e}$$= 2.3 \pm$ 0.5  kpc).

![](GalfitImages.pdf)

The FWHMs (deconvolved from the restoring beam) measured by IMFIT are shown in Table [1](#tab:observations). They range from 0.26$''$$-$1.45$''$, which convert to 2.1$-$12.3  kpc on physical scales. The half light radii quoted in Table [1](#tab:observations) are equivalent to these FWHM measurements divided by two. The median Gaussian profile has a FWHM $= 3.9 \pm 1.6$ kpc. Excluding 850.95, the median is $3.8 \pm 1.4$ kpc.

The Gaussian profiles of the ALESS sources included in our analysis were measured via the same technique used here (cite: hodge16a), where the median FWHM $= 3.8 \pm 0.5$ kpc. The median size of our sources agrees with that of the ALESS sources, despite the fact that the ALESS sample is brighter than all but two of our sources. Overall, the DSFG population from which the ALESS and COSMOS SCUBA-2 DSFGs are drawn are very similar, with the exception of the ALESS median total 870 $\mu$m flux densities being $1.3\times$ brighter. The median of our sources’ half-light radii is also consistent within uncertainty with that found by (cite: spilker16) and (cite: gullberg19).

The Sersic indices of our sources range from $n=$0.3 to 2.1, with a median of $n = 0.8 \pm 0.4$. Our median $n$ is consistent with that of the ALESS sources in (cite: hodge16a), whose median Sersic index $n = 0.9 \pm 0.2$ implies a non-Gaussian, exponential disk morphology. (cite: gullberg19) also found an exponential disk emission profile for a sample of DSFGs.

## SED Integrated Dust Temperature

Wien’s Law states that  $\lambda_{\rm peak}$$=$ $b$/T$_{\rm d}$ (where $b$ $=$ 2.898$\times\,10^{-3}$ m K) for an idealized blackbody, but this relationship deviates depending on the adopted opacity model of the blackbody as shown in Figure 20 of (cite: casey14a). Thus, we parameterize the luminosity-weighted dust temperature (T$_{\rm d}$) instead as the observable  $\lambda_{\rm peak}$, the rest-frame wavelength where the dust spectral energy distribution (SED) peaks. The observable $\lambda_{\rm peak}$ is not sensitive to opacity assumptions and is a better trace of the observed peak in the SED in any observational sample without high quality constraints on the underlying dust opacity.

SEDs in this work were fitted using the technique described in (cite: casey12a), based on a single dust temperature modified blackbody fit with a mid-infrared power law shortward of $\sim$ 70 $\mu$m in the rest frame. The mid-infrared powerlaw represents a superposition of modified blackbodies at warm to hot temperatures, where the least amount of dust mass is heated to the hottest temperatures, and the vast majority of the mass of dust in the ISM is at much colder temperatures, represented by the temperature of the fit at rest-frame wavelengths $\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}$200$\mu$m. Because our sample has somewhat limited rest-frame mid-infrared photometric constraints, we fix the mid-infrared power law slope to $\alpha_{\rm MIR}=2$, representative of the average measured power law slope for local LIRGs and ULIRGs that have well-sampled mid-IR SEDs (cite: u12a).

The photometric points used in the fitting include ALMA (870 $\mu$m), Herschel SPIRE (250, 350, 500 $\mu$m), SCUBA-2 (450, 850 $\mu$m), and Spitzer (24 $\mu$m). Points are weighted relative to their signal-to-noise, with exception of the *Spitzer* 24 $\mu$m point whose signal-to-noise is capped at 10 for the purposes of these bulk SED fits. The 24 $\mu$m photometry often is a very high signal-to-noise measurement but is not always in agreement with the underlying SED model for dust continuum emission alone, due to the possible contribution of PAH emission features and silicate absorption in the rest-frame mid-infrared but not directly modeled here. We also note that use of the response function of the various far-infrared/millimeter passbands is not necessary using the (cite: casey12a) fitting method given the lack of $\approx$1% precision in the photometry in the FIR regime (cite: casey20a).

While the bulk SED, including the measured IR luminosity or rest-frame peak wavelength, is not impacted by the adopted opacity model, here we adopt a fixed opacity model for all SEDs such that $\tau$=1 at 200 $\mu$m following (cite: conley11a). Given that our observations include spatially-resolved dust maps, we can test if this assumption is appropriate for this sample by inferring the wavelengths at which $\tau$=1 from the dust column density. Using the total 870$\mu$m flux densities from section [4.1](#sec:fluxes), sizes from section [4.2](#sec:sizes), a fixed mass-weighted dust temperature of 25 K, and dust mass absorption coefficients from (cite: li01a), we infer that the wavelength at which the SEDs become optically thick to vary from 10–300 $\mu$m (with an average $\lambda(\tau=1)=80\pm50$ $\mu$m). Given the uncertainties in the derivation of dust mass itself, we choose to apply the uniform assumption to our SEDs rather than tuning each fit according to its measured dust column. The SEDs are shown in Figure [5](#fig:SEDs), and the measured peak wavelengths and IR luminosities are also given in Table [1](#tab:observations). We also re-fit SEDs for the ALESS sources described in (cite: hodge16a) whose multiwavelength photometry is given in (cite: swinbank14a). Fitting SEDs for both the COSMOS SCUBA-2 DSFGs and the ALESS sources was done in a fully consistent manner.

![](allseds.pdf)

## Star Formation Rates and Stellar Masses

Star formation rates (SFRs) were calculated using the total infrared luminosities derived from the SED fits in section [4.3](#sec:seds) and the logarithmic constant of conversion, $\rm \log(C_{IR}) = 43.41$ from (cite: kennicutt12). We do not have reliable stellar mass estimates for 450.03 and 450.14 due to foreground-background source contamination (see (cite: casey17a)), so they are omitted from all analysis requiring measurements of  M$_\star$. The stellar masses of the COSMOS sample are presented in (cite: casey17a), and for the ALESS sources they are presented in (cite: dacunha15a). All stellar masses used in this study are derived with MAGPHYS (cite: dacunha15a; dacunha08) in a uniform fashion using stellar population models from (cite: bruzual03). For the two sources for which the redshifts were corrected, we reran the MAGPHYS modeling accordingly. Note that the stellar masses of DSFGs are often highly uncertain, though not necessarily systematically so, as they can also be overestimated by applying an inappropriate star formation history (cite: hainline11a; michalowski12). The uncertainties on the stellar masses are consistent with the broad uncertainties on DSFG stellar masses in general. We note that our MAGPHYS fits are used exclusively to derive stellar masses, and the MAGPHYS fits are not used in this work to infer FIR SED characteristics like dust temperature or SFR; this is because of the potential for the rest-frame optical/near-infrared SED to be highly decoupled from FIR emission in DSFGs, and our desire to directly test the FIR fits alone and independently of the rest-frame optical/near-infrared emission used to measure the stellar masses. We also calculated the specific star formation rate (sSFR), where sSFR = SFR/ M$_\star$.

Figure [6](#fig:mainsequence) shows the COSMOS and ALESS sources in relation to the SFR– M$_\star$ relation, also called the galaxy main sequence. In red, we show the main sequence of star-forming galaxies with a quadratic function of the form used in (cite: whitaker14a) applied to COSMOS data (1.5 $\leq$ z $\leq$ 2.5) from (cite: laigle16a). We applied a Markov Chain Monte Carlo (MCMC) approach to derive the parameters of the fit for the broader COSMOS data set. Also shown also are the cosmic time-dependent best fits from (cite: speagle14a) for redshifts $z =$ 1, 2, 3, 4, and 5.

For each galaxy in our sample, we also compute a parameterized ‘distance’ to the main sequence, or D$_{\rm MS}$. D$_{\rm MS}$ represents the orthogonal distance between the main sequence at the source’s redshift and its measured value in the $\log$ M$_\star$–$\log$SFR plane. We compute orthogonal distances to the main sequence rather than projected distances in SFR or sSFR to minimize the impact of measurement uncertainties in both  M$_\star$ and SFR for each galaxy. The main sequence used to calculate D$_{\rm MS}$ for each source were the cosmic time-dependent curves given in (cite: speagle14a); however, we note that computing D$_{\rm MS}$ using a quadratic form of the main sequence as in (cite: whitaker14a) produces similar results, ultimately not changing the conclusions of our work no matter which definition of D$_{\rm MS}$ is adopted. Similarly, as we discuss later in section [5](#sec:discussion), we test for correlation between  $\lambda_{\rm peak}$ and $\Delta$sSFR, finding results that are consistent with our adopted D$_{\rm MS}$.

![](mainsequence.pdf)

# Discussion

## Expected Relationship of Dust Geometry to Dust Temperature

Most galaxies for which dust temperatures have been constrained lack spatially-resolved measurements needed to investigate the effects of dust geometry on dust temperature. Thus, the underlying physical driver of a galaxy’s globally-averaged dust temperature has not been directly constrained. Before ALMA, there were small samples of high-$z$ galaxies that had resolved radio or millimeter sizes (cite: chapman04b; biggs08a; casey09b; younger09a), but the observations needed to determine accurate sizes for larger samples of DSFGs require the order of magnitude improvements in sensitivity brought by ALMA (cite: hodge16a; rujopakarn16a; simpson17; gullberg19a; elbaz18a). In this paper, we have presented a sample of DSFGs with both high-resolution dust size constraints and good dust SED constraints, allowing a more thorough investigation into the physical drivers of galaxies’ dust SEDs.

This study is theoretically motivated by the application of the Stefan-Boltzmann law on galaxy scales. Specifically, it relates the emergent IR luminosity to the effective size of the blackbody (R$_{\rm e}$)  and temperature (T$_{\rm d}$) of an optically thick spherical blackbody:

$$\begin{equation}
\mathrm{L_{\rm IR} = 4\pi R_{e}^{2}\sigma T^{4}}
\label{eq:sf}
\end{equation}$$\
The Stefan-Boltzmann constant is $\sigma$ = 5.670$\times\,10^{-5}$  erg s$^{-1}$ cm$^{-2}$ K$^{-4}$. Galaxies are certainly not as simple as stars in the application of such a relation. Nevertheless, approximating galaxies’ IR emission as an optically thick shell of dust surrounding an obscured point source (i.e. deeply embedded OB associations in star-forming regions) would result in the following expected relation between the dust’s temperature, IR luminosity and dust shell radius: $$\begin{equation}
    \log\Sigma_{\rm IR} = \log(4\sigma) + 4\log(T_{\rm dust})
    \label{eq:sphereicalSB}
\end{equation}$$ Where $\Sigma_{\rm IR}$ is the IR luminosity surface density, =$L_{\rm IR}/\pi R_{e}^2$. Of course, galaxies’ geometry is unlikely to be well represented as a spherical shell, and the surface area of the emergent IR flux does indeed play a role in the expected relation. If instead of a spherical shell we assume some uniform planar distribution of UV emission underneath an optically thick screen (as in a galaxy disk, with half-light radius $R_{e}$) we would expect the following relationship instead: $$\begin{equation}
    \log\Sigma_{\rm IR} = \log(\sigma) + 4\log(T_{\rm dust})
    \label{eq:sigmairtdust}
\end{equation}$$ which is a factor of four different than the spherical shell: one factor of two given the modified surface area of a disk as 2$\pi R_{e}^2$ and one factor of two accounting for $R_{e}^2$ being a measured *half-light* radius. Then given our use of optically thick SEDs (described in section [4.3](#sec:seds)), where the relationship between dust temperature and  $\lambda_{\rm peak}$ can be approximated as $$\begin{equation}
\label{eq:lpeaktd}
    \log(T_{\rm dust}/K) \approx 3.756-1.048\log(\lambda_{\rm peak}/\mu\!m)
\end{equation}$$ in the 15–70 K range[^1]. This gives a predicted relationship between  $\lambda_{\rm peak}$ and $\Sigma_{\rm IR}$ of $$\begin{equation}
    \log(\Sigma_{\rm IR}/[L_\odot\,{\rm kpc}^{-2}]) \approx 20.18 - 4.19\log(\lambda_{\rm peak}/\mu\!m)
    \label{eq:expected_lpeaksigmaIR}
\end{equation}$$ Note that expectation using Wien’s Law directly instead of the approximation given in Eq [\[eq:lpeaktd\]](#eq:lpeaktd) would yield $$\begin{equation}
\begin{array}{ll}
    \log(\Sigma_{\rm IR}/[L_\odot\,{\rm kpc}^{-2}])& = \log(\sigma b^4)-4\log(\lambda_{\rm peak}/\mu\!m)\\
    & \approx 19.00 - 4\log(\lambda_{\rm peak}/\mu\!m)\\
    \end{array}
    \label{eq:wienslaw_lpeaksigmaIR}
\end{equation}$$ where $b$=2.898$\times\,10^{3}$ $\mu$m K.

One key caveat here is that the Stefan-Boltzmann Law should only be applicable to optically thick blackbodies, and the dust in galaxies’ ISM is often far from optically thick at all wavelengths (of course, it is a huge benefit that ISM dust is often optically thin on the Rayleigh-Jeans tail of blackbody emission, allowing for a direct measurement of galaxies’ dust mass from measured flux density). We return to the conundrum of dust opacity again in section [5.2.1](#sec:lpeaksigmair), where we derive the relationship between $\Sigma_{\rm IR}$ and  $\lambda_{\rm peak}$ empirically.

## What correlates best with dust temperature?

Here we investigate the relative strengths of correlations between  $\lambda_{\rm peak}$ (our observational proxy for dust temperature) and each of the following physical properties of galaxies: sSFR, D$_{\rm MS}$, SFR, and $\Sigma_{\rm IR}$. All of these quantities have been argued to correlate tightly with galaxies’ dust temperatures, for example: sSFR and D$_{\rm MS}$ (cite: magnelli14a), SFR or L$_{\rm IR}$ (cite: chapman03a; symeonidis13a), and $\Sigma_{\rm IR}$ (cite: chanial07; lutz16a). For example, (cite: magnelli14a) report that T$_{\rm d}$ correlates more strongly with sSFR and parameterized distance to the main sequence (D$_{\rm MS}$) than L$_{\rm IR}$ (they lacked direct measures of R$_{\rm e}$ so could not investigate L$_{\rm IR}$ R$_{\rm e}$$^{-2}$). In addition, they deduced that cold galaxies ($\lesssim$ 25K) sit on the main sequence and warm galaxies ($\gtrsim$ 30-80K) lie above the main sequence (cite: magnelli14a).

Here we use this high-$z$ sample with well measured sizes and SEDs to directly constrain which of these physical correlations is tightest, and may therefore be the most fundamental to the internal ISM. This may be of particular use to the community when only some of these quantities can be measured (for example, galaxies lacking high-resolution dust continuum imaging). We calculate the significance of each correlation as the deviation of the model from no correlation, or a horizontal line in the given parameter space. The results are shown in Figure [7](#fig:correlations).

![image](DistanceFromMS.pdf) ![image](sSFRVLambdaPeak.pdf)\
![image](SFRvsLambdaPeak.pdf)![image](SFSurfDensVsLambdaPeak.pdf)

We find that the  $\lambda_{\rm peak}$ vs. D$_{\rm MS}$ and  $\lambda_{\rm peak}$ vs. sSFR relationships correlate with 3$\sigma$ and 7$\sigma$ significance, respectively. In contrast, the  $\lambda_{\rm peak}$ vs. SFR and  $\lambda_{\rm peak}$ vs. $\Sigma_{\rm IR}$ relationships carry an 18$\sigma$ and 24$\sigma$ correlation significance, respectively. Below, we interpret the underlying physics of the correlations.

To investigate whether the extended redshift range of our sources affects our results, we recalculated the correlations based on a reduced sample with $1.44 \leqslant z \leqslant 2.86$, removing the high-$z$ and low-$z$ extrema from the sample. At $z < 3$, the reduced sample’s continuum observations are on the optically thin portion of the Rayleigh-Jeans tail of dust emission (i.e., rest-frame wavelengths longer than $\sim$ 200 $\mu$m), probing cold dust in the ISM. With the redshift-restricted sample, the significance of the  $\lambda_{\rm peak}$–$\Sigma_{\rm IR}$ and  $\lambda_{\rm peak}$–SFR correlations are reduced somewhat to 16$\sigma$ and 18$\sigma$ significance, respectively, while the correlation between  $\lambda_{\rm peak}$ and D$_{\rm MS}$ and  $\lambda_{\rm peak}$ and sSFR increase to 4$\sigma$ and 8$\sigma$, respectively. However, the end results are the same: the  $\lambda_{\rm peak}$ correlations with $\Sigma_{\rm IR}$ and SFR are significantly stronger than those with sSFR and D$_{\rm MS}$.

###  $\lambda_{\rm peak}$ vs. $\Sigma_{\rm IR}$

We empirically measure the following relationship between  $\lambda_{\rm peak}$ and $\Sigma_{\rm IR}$, or the star-formation surface density, using our sample: $$\begin{equation}
 \begin{array}{ll}
    \log(\Sigma_{\rm IR}/[L_\odot\,{\rm kpc}^{-2}]) = & (18.78\pm0.33) \\
    & - (3.80\pm0.16)\log(\lambda_{\rm peak}/\mu\!m)\\
\end{array}
\label{eq:measured_lpeaksigmaIR}
\end{equation}$$ The overall strength of the correlation is 24$\sigma$. The slope of this relation is a 2.4$\sigma$ deviation from expectation in Equation [\[eq:expected_lpeaksigmaIR\]](#eq:expected_lpeaksigmaIR), and the intercept deviates by 4.3$\sigma$. Comparing to expectation using Wien’s Law directly (Equation [\[eq:wienslaw_lpeaksigmaIR\]](#eq:wienslaw_lpeaksigmaIR)), our empirical relation only deviates by 1.3$\sigma$ in the slope and 0.7$\sigma$ in the intercept.

The agreement between Equations [\[eq:expected_lpeaksigmaIR\]](#eq:expected_lpeaksigmaIR)-[\[eq:wienslaw_lpeaksigmaIR\]](#eq:wienslaw_lpeaksigmaIR) and Equation [\[eq:measured_lpeaksigmaIR\]](#eq:measured_lpeaksigmaIR) should be somewhat surprising, given that the geometry of galaxies’ ISM is quite complex, and that ISM is far from optically thick! How might we interpret the remarkably close correlation between  $\lambda_{\rm peak}$ and $\Sigma_{\rm IR}$?

Such a tight correlation would be expected if the peak of dust luminosity (traced directly by  $\lambda_{\rm peak}$) originates from regions of the ISM that are, indeed, optically thick. This may not be in direct conflict with more diffuse, cold dust in galaxies’ ISM being optically thin, as that dust may not directly dominate the bulk of emission at the *peak* of IR emission.

We note that (cite: simpson17) provide an analysis of several (other) high-$z$ DSFGs that have resolved ALMA sizes and measured SED dust temperatures; their Figure 5 shows the relationship between $T_{\rm d}$ and $\Sigma_{\rm IR}$, suggesting tension between predictions from the Stefan-Boltzmann Law and galaxies’ dust temperatures, when assumed to be optically thick (they find more agreement when using the best-fit temperatures assuming optically thin SEDs). The difference in interpretation between our work on that of (cite: simpson17) is the presumed normalization of the Stefan-Boltzmann Law itself and the geometry of dust: their application of the Stefan-Boltzmann Law is drawn from a presumed spherical shell of dust surrounding a single star-forming region (as in Eq [\[eq:sphereicalSB\]](#eq:sphereicalSB)), while our normalization accounts for a more disk-like configuration of a dust screen with several spatially distinct deeply embedded star-forming regions (as in Eq [\[eq:sigmairtdust\]](#eq:sigmairtdust)). After accounting for the different geometries, we suggest the (cite: simpson17) results, like ours, are quite consistent with a galaxy-scale Stefan-Boltzmann approximation for the emergent IR luminosity. Given the strength of the correlation in our dataset and the plausible underlying physical interpretation of this relation, we determine that the  $\lambda_{\rm peak}$ vs. $\Sigma_{\rm IR}$ relation is the most fundamental of those we explore in this paper.

We note that the correlation strength of 24$\sigma$ found for  $\lambda_{\rm peak}$-$\Sigma_{\rm IR}$ is unaffected by calculating $\Sigma_{\rm IR}$ with circularized radii or effective radii from Sersic fitting rather than FWHMs from Gaussian fitting. The strength of the correlations are also not affected by removing the two sources (450.03 and 450.14) for which we do not have reliable stellar mass estimates from our analysis.

It is important to note that our measured sizes trace the dust mass as probed on the Raleigh-Jeans tail of blackbody emission in what is expected to be an optically thin regime. This may be a different size than would be probed at the peak SED, which traces SFR density more directly. In other words, one might not expect the mass-weighted size to map directly to the SFR-weighted size. The relative agreement of the two is suggestive of a linear relationship between the effective radius over which the dust mass and star formation exist (i.e., R$_{\rm e}$ for SFR is similar to R$_{\rm e}$ for M$_{\rm dust}$), which in turn may imply a linear slope for the Kennicutt-Schmidt law of star-formation rate and gas surface density in these galaxies (cite: kennicutt98; delosreyes19). Further high-resolution follow-up work is needed to explore this in greater detail.

###  $\lambda_{\rm peak}$ vs. $L_{\rm IR}$ or SFR

We measure the following empirical relationship between L$_{\rm IR}$ and  $\lambda_{\rm peak}$ in this sample: $$\begin{equation}
    \log(L_{\rm IR}/L_\odot) = (18.2\pm0.3) - (2.81\pm0.16)\log(\lambda_{\rm peak}/\mu\!m)
    \label{eq:lirlpeak}
\end{equation}$$ This correlation carries an overal significance of 18$\sigma$. The relationship with SFR can then be derived using the (cite: kennicutt12) scaling. Figure [7](#fig:correlations) demonstrates that the trend broadly follows that of the star-formation or IR luminosity surface density, $\Sigma_{\rm IR}$.

We note that this relation is quite a bit steeper than found elsewhere in the literature for much larger samples of galaxies lacking high-resolution dust observations (cite: lee13a; symeonidis13a; kirkpatrick17a); for example, (cite: casey18b) modeled the L$_{\rm IR}$– $\lambda_{\rm peak}$ relationship by a power law such that $\log_{10}$( $\lambda_{\rm peak}$)$=\log(\lambda_{0}) + \eta(\log(\rm L_{IR})-12)$. Through empirical measurement of large samples of IR luminous galaxies from $0<z<5$, they found $\eta$ = –0.068 $\pm$ 0.001 and $\log(\lambda_{0}/\mu\!m)=2.012$. Though both our findings here and the (cite: casey18a) findings both show the same general trend – whereby higher luminosity sources are hotter – here we find the higher luminosity sources are *substantially* hotter than those with fainter luminosities. As touched on earlier in section [3.3](#sec:biases), this is likely due to our selection of sources well-suited for high-resolution dust continuum follow-up (and therefore, relatively high L$_{\rm IR}$ for a wide swath of  $\lambda_{\rm peak}$); therefore it is likely that the more extensive samples from (cite: casey18a) and references therein provide a more well-calibrated measurement of the  $\lambda_{\rm peak}$-$L_{\rm IR}$ relationship over a much larger dynamic range in L$_{\rm IR}$.

Because the (cite: casey18a) model does not account for galaxy size as our analysis in Equation [\[eq:measured_lpeaksigmaIR\]](#eq:measured_lpeaksigmaIR) does, we can use the two in conjunction to infer an overall size dependency of L$_{\rm IR}$. Combining our Equation [\[eq:measured_lpeaksigmaIR\]](#eq:measured_lpeaksigmaIR) with their  $\lambda_{\rm peak}$–L$_{\rm IR}$ relationship, we find that the size dependence can be modeled as a power-law function of L$_{\rm IR}$ such that R$_{\rm e}$ $\propto$ L$_{\rm IR}$$^{0.37\pm0.03}$. Note that this is roughly consistent with the size-luminosity relationship derived in (cite: fujimoto17a), who found R$_{\rm e}$ $\propto$L$_{\rm IR}$$^{0.28\pm0.07}$.

###  $\lambda_{\rm peak}$ vs. sSFR or Distance to the Main Sequence

Because both specific star-formation rate (sSFR) and the distance of a galaxy from the SFR- M$_\star$ relation (the galaxy main sequence) both fundamentally trace physics dependent on *both* SFR and stellar mass, we discuss them here together. While we do find a subtle relationship between  $\lambda_{\rm peak}$ vs. sSFR and  $\lambda_{\rm peak}$ vs. D$_{\rm MS}$, they are substantially weaker than direct correlations between  $\lambda_{\rm peak}$ and $\Sigma_{\rm IR}$ or L$_{\rm IR}$.

In contrast to some literature claims, we do not find clear evidence to support the theory that galaxies’ dust temperatures correlate strongly with a galaxy’s position on the galaxy main sequence. We note that the dynamic range of sSFR and D$_{\rm MS}$ in our sample is comparable to similar datasets at matched redshifts ($\sim$2 dex in sSFR and $\sim$1 dex in D$_{\rm MS}$) ((cite: barger14a)). Specifically, we find the following correlations between  $\lambda_{\rm peak}$ and sSFR or D$_{\rm MS}$ (where we have defined the latter as the orthogonal shortest distance to the (cite: speagle14a) fits at the source’s redshift): $$\begin{equation}
\begin{array}{ll}
\log(sSFR/[{\rm Gyr^{-1}}]) = & (3.4\pm0.4) -\\ & (1.43\pm0.20)\log(\lambda_{\rm peak}/\mu\!m)\\
\end{array}
\end{equation}$$ and $$\begin{equation}
    \log(D_{\rm MS}) = (1.5\pm0.4) - (0.54\pm0.21)\log(\lambda_{\rm peak}/\mu\!m)
\end{equation}$$ which have overall correlation significance of 7$\sigma$ and 3$\sigma$, respectively. Note that alternate definitions of D$_{\rm MS}$ ($\Delta$log(SSFR)$_{\rm MS}$ and/or D$_{\rm MS}$ using the (cite: whitaker14a) quadratic form of the main sequence) result in similarly low correlation strengths ranging 1–4$\sigma$.

The fact that both correlations between dust temperature and sSFR or D$_{\rm MS}$ are relatively weak suggests that the inclusion of stellar mass effectively dilutes the underlying physics driving the observed value of  $\lambda_{\rm peak}$. In fact, if we explicitly test for correlation between stellar mass and  $\lambda_{\rm peak}$, indeed, we find no significant correlation.

With integrated dust SED temperature lacking strong direct correlation with the main sequence, if the assertion is made that the main sequence informs on the evolutionary stage of a galaxy then we infer that T$_{\rm d}$ (or  $\lambda_{\rm peak}$) is not a viable indicator of evolutionary class (starburst or secular disk) and that higher temperature does not necessarily indicate presence of a starburst (cite: bothwell10a; hodge12a; drew20). Rather, our results suggest that the underlying dust geometry within the ISM plays a much more substantial role. In addition, ISM dust can be heated by AGN whether or not the galaxy hosts an ongoing starburst (cite: kirkpatrick12). Additional recent cosmological simulation work supports the production of intense luminosities through secularly evolving disk systems either from gas infall, minor mergers, or disk instabilities (cite: dave10a; hodge12a; narayanan15a; hayward18a; tadaki18a).

(cite: magnelli14a) arrived at different results than we have, suggesting significant correlation between D$_{\rm MS}$ and T$_{\rm d}$. Instead of using our definition of D$_{\rm MS}$, they evaluated D$_{\rm MS}$ to be $\Delta$log(SSFR)$_{\rm MS}$, where $\Delta$log(SSFR)$_{\rm MS}$= log\[SSFR/SSFR$_{\rm MS}$( M$_\star$,$z$)\]. We also investigated the correlation between $\Delta$log(SSFR)$_{\rm MS}$ and  $\lambda_{\rm peak}$ for our sample and found it to have the same correlation strength as the correlation between D$_{\rm MS}$, as defined above, and  $\lambda_{\rm peak}$. Without uncertainties on individual measurements for $\Delta$log(SSFR)$_{\rm MS}$ in (cite: magnelli14a), we are unable to directly compare those results to our analysis on the relative significance of the correlation. We also note that the stacking techniques used in their analysis on *Herschel* data may be prone to temperature-dependent biases. For instance, the stacking results of (cite: viero13) result in fundamentally different (and overall colder) SEDs than the stacking results of (cite: bethermin15a) despite use of very similar datasets (Drew et al. in preparation). Further analysis of SEDs drawn from broad literature sources is beyond the scope of this work.

## Comparison to local galaxies

Note that our findings — that $\Sigma_{\rm IR}$ correlates most closely with  $\lambda_{\rm peak}$ of a dust SED— is in agreement with previous work at lower redshifts, for which a relationship between the star formation surface density, $\Sigma_{\rm IR}$, and dust temperature exists (cite: lehnert96a; chanial07; lutz16a).

While the results of (cite: chanial07) work find a relatively shallow relationship between $\Sigma_{\rm IR}$ and T$_{\rm d}$, our results are more consistent with the earlier (steeper) dependence suggested by (cite: lehnert96a); the relative discrepancies could be due to measurement of sizes conducted in radio continuum vs. millimeter continuum (cite: miettinen17a) or differences in the sample selection.

In particular, we find it useful to analyze the results of (cite: lutz16a) in context, which is based on FIR size measurements from *Herschel*/PACS of local galaxies; they derived relationships between $\Sigma_{\rm IR}$, L$_{\rm IR}$  and sSFR/sSFR$_{\rm MS}$ and a proxy measure of dust temperature, the FIR color $\log(S_{70}/S_{160})$ which we will call C. Their Table 2 provides a summary of the derived relationships, allowing us to directly infer the relative correlations between the FIR color $C$ and $\Sigma_{\rm IR}$, L$_{\rm IR}$ and $\Delta$log(SSFR)$_{\rm MS}$ (even though FIR color $C$ is not equivalent to  $\lambda_{\rm peak}$). What the (cite: lutz16a) scaling relations suggest is that $C$ and $\Sigma_{\rm IR}$ are correlated with a measurement significance of 30$\sigma$, $C$ and L$_{\rm IR}$ are correlated with a measurement significance of 20$\sigma$, and $C$ and $\Delta$log(SSFR)$_{\rm MS}$ are correlated with a measurement significance of 6$\sigma$. While the exact significance of the correlations is likely dependent on sample details, the overall trend is similar to our findings: that $\Sigma_{\rm IR}$ is the most closely linked physical quantity to dust temperature (or  $\lambda_{\rm peak}$ or $C$) and that correlation to the galaxies’ main sequence (here probed by $\Delta$log(SSFR)$_{\rm MS}$) is the weakest of the correlations.

# Conclusions

We used 0.24$''$  resolved 870 $\mu$m ALMA dust continuum observations to determine the total integrated flux density and size. We used SED fitting to determine  $\lambda_{\rm peak}$ and L$_{\rm IR}$. We investigated correlations of dust temperature with four galaxy characteristics: sSFR, parameterized distance to the galaxy main sequence (D$_{\rm MS}$), SFR, and star formation surface density measured via $\Sigma_{\rm IR}$. Our results are as follows:

- The R$_{\rm e}$ of our seven new DSFGs range from 2.1–12.03 kpc with sizes of the full sample analyzed at 870 $\mu$m with $\langle\!$R$_{\rm e}$$\!\rangle$ = 3.9 $\pm$ 1.6 kpc. The median Sersic index $n = 0.8 \pm 0.4$ implies a non-Gaussian, exponential disk morphology.

- The correlations of  $\lambda_{\rm peak}$ with sSFR and D$_{\rm MS}$ are relatively weak. The linear models relating $\log$( $\lambda_{\rm peak}$) with $\log$(sSFR) and $\log$(D$_{\rm MS}$) had strengths of only 7$\sigma$ and 3$\sigma$, respectively.

- The linear models relating $\log$( $\lambda_{\rm peak}$) with $\log$(SFR) and $\log$($\Sigma_{\rm IR}$) had strengths of 18$\sigma$ and 24$\sigma$, respectively, confirming that the  $\lambda_{\rm peak}$–L$_{\rm IR}$ and  $\lambda_{\rm peak}$–$\Sigma_{\rm IR}$ relationships are statistically stronger than the  $\lambda_{\rm peak}$–sSFR and  $\lambda_{\rm peak}$–D$_{\rm MS}$ relationships and more likely probe the underlying physical driver of galaxies’ luminosity-weighted dust temperatures.

- Our results are consistent with measured scaling relations between FIR color, $\Sigma_{\rm IR}$, L$_{\rm IR}$, and $\Delta\log$(sSFR) for galaxies in the local Universe analyzed by (cite: lutz16a). In particular, both our work and (cite: lutz16a) find that the  $\lambda_{\rm peak}$–$\Sigma_{\rm IR}$ relationships are the strongest. This motivates our conclusion that SFR surface density is the fundamental characteristic driving a galaxy’s luminosity-weighted dust temperature.

We conclude that galaxies’ dust emission properties can be well described by a Stefan-Boltzmann like law, where the luminosity-weighted dust temperature (as measured via  $\lambda_{\rm peak}$) goes roughly as $\Sigma_{\rm IR}\propto$ $\lambda_{\rm peak}$$^{-4}$. While there are many physical reasons such a relationship would be expected not to hold (for example, our measurement of size on the Rayleigh Jeans tail of optically thin dust emission, or the fact that overall dust emission is not optically thick throughout the ISM), our finding that it does hold suggests that (a) the bulk of galaxies’ IR luminosity can be approximated as optically thick near the SED peak, roughly consistent with a disk or planar geometry, and (b) there is a linear relationship between galaxies’ ISM dust-mass weighted sizes and galaxies’ SFR-weighted sizes. Furthermore, we infer that dust temperature is not necessarily a reliable indication of where a galaxy sits on the main sequence and should not be used to infer evolutionary class as the quantity is most likely to trace the underlying geometry of galaxies’ ISM.

# Acknowledgments

We thank the anonymous reviewer for their input. ADB thanks the John W. Cox Endowment for the Advanced Studies in Astronomy for support. CMC thanks the National Science Foundation for support through grants AST-1714528, AST-1814034, and AST-2009577 and additionally CMC, JAZ, and JSS thank the University of Texas at Austin College of Natural Sciences for support. In addition, CMC acknowledges support from the Research Corporation for Science Advancement from a 2019 Cottrell Scholar Award sponsored by IF/THEN, an initiative of Lyda Hill Philanthropies. SMM thanks the National Science Foundation for support through the Graduate Research Fellowship under Grant No. DGE-1610403. CCC acknowledges support from the Ministry of Science and Technology of Taiwan (MOST 109-2112-M-001-016-MY3). This paper makes use of the following ALMA data: ADS/JAO.ALMA $\#$2015.1.00568.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

natexlab

(ref: barger14a) Barger, A. J., Cowie, L. L., Chen, C. C., et al. 2014, ApJ, 784, 9, doi: [`10.1088/0004-637X/784/1/9`](http://doi.org/10.1088/0004-637X/784/1/9)

(ref: bethermin15a) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113, doi: [`10.1051/0004-6361/201425031`](http://doi.org/10.1051/0004-6361/201425031)

(ref: bethermin17) Béthermin, M., Wu, H.-Y., Lagache, G., et al. 2017, A&A, 607, A89, doi: [`10.1051/0004-6361/201730866`](http://doi.org/10.1051/0004-6361/201730866)

(ref: biggs08a) Biggs, A. D., & Ivison, R. J. 2008, MNRAS, 385, 893, doi: [`10.1111/j.1365-2966.2008.12869.x`](http://doi.org/10.1111/j.1365-2966.2008.12869.x)

(ref: blain04a) Blain, A. W., Chapman, S. C., Smail, I., & Ivison, R. 2004, ApJ, 611, 725, doi: [`10.1086/422353`](http://doi.org/10.1086/422353)

(ref: bothwell10a) Bothwell, M. S., Chapman, S. C., Tacconi, L., et al. 2010, MNRAS, 405, 219, doi: [`10.1111/j.1365-2966.2010.16480.x`](http://doi.org/10.1111/j.1365-2966.2010.16480.x)

(ref: bruzual03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: casey12a) Casey, C. M. 2012, MNRAS, 425, 3094, doi: [`10.1111/j.1365-2966.2012.21455.x`](http://doi.org/10.1111/j.1365-2966.2012.21455.x)

(ref: casey20a) —. 2020, ApJ, 900, 68, doi: [`10.3847/1538-4357/aba528`](http://doi.org/10.3847/1538-4357/aba528)

(ref: casey18a) Casey, C. M., Hodge, J., Zavala, J. A., et al. 2018a, ApJ, 862, 78, doi: [`10.3847/1538-4357/aacd11`](http://doi.org/10.3847/1538-4357/aacd11)

(ref: casey14a) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: casey09b) Casey, C. M., Chapman, S. C., Beswick, R. J., et al. 2009, MNRAS, 399, 121, doi: [`10.1111/j.1365-2966.2009.15291.x`](http://doi.org/10.1111/j.1365-2966.2009.15291.x)

(ref: casey12b) Casey, C. M., Berta, S., Béthermin, M., et al. 2012, ApJ, 761, 140, doi: [`10.1088/0004-637X/761/2/140`](http://doi.org/10.1088/0004-637X/761/2/140)

(ref: casey13a) Casey, C. M., Chen, C.-C., Cowie, L. L., et al. 2013, MNRAS, 436, 1919, doi: [`10.1093/mnras/stt1673`](http://doi.org/10.1093/mnras/stt1673)

(ref: casey17a) Casey, C. M., Cooray, A., Killi, M., et al. 2017, ApJ, 840, 101, doi: [`10.3847/1538-4357/aa6cb1`](http://doi.org/10.3847/1538-4357/aa6cb1)

(ref: casey18b) Casey, C. M., Zavala, J. A., Spilker, J., et al. 2018b, ApJ, 862, 77, doi: [`10.3847/1538-4357/aac82d`](http://doi.org/10.3847/1538-4357/aac82d)

(ref: chanial07) Chanial, P., Flores, H., Guiderdoni, B., et al. 2007, A&A, 462, 81, doi: [`10.1051/0004-6361:20053881`](http://doi.org/10.1051/0004-6361:20053881)

(ref: chapman03b) Chapman, S. C., Blain, A. W., Ivison, R. J., & Smail, I. R. 2003a, Nature, 422, 695, doi: [`10.1038/nature01540`](http://doi.org/10.1038/nature01540)

(ref: chapman03a) Chapman, S. C., Helou, G., Lewis, G. F., & Dale, D. A. 2003b, ApJ, 588, 186, doi: [`10.1086/374038`](http://doi.org/10.1086/374038)

(ref: chapman04c) Chapman, S. C., Smail, I., Blain, A. W., & Ivison, R. J. 2004a, ApJ, 614, 671, doi: [`10.1086/423833`](http://doi.org/10.1086/423833)

(ref: chapman04b) Chapman, S. C., Smail, I., Windhorst, R., Muxlow, T., & Ivison, R. J. 2004b, ApJ, 611, 732, doi: [`10.1086/422383`](http://doi.org/10.1086/422383)

(ref: chen15a) Chen, C.-C., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 194, doi: [`10.1088/0004-637X/799/2/194`](http://doi.org/10.1088/0004-637X/799/2/194)

(ref: conley11a) Conley, A., Cooray, A., Vieira, J. D., et al. 2011, ApJL, 732, L35, doi: [`10.1088/2041-8205/732/2/L35`](http://doi.org/10.1088/2041-8205/732/2/L35)

(ref: dacunha08) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595, doi: [`10.1111/j.1365-2966.2008.13535.x`](http://doi.org/10.1111/j.1365-2966.2008.13535.x)

(ref: dacunha15a) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: dave10a) Davé, R., Finlator, K., Oppenheimer, B. D., et al. 2010, MNRAS, 404, 1355, doi: [`10.1111/j.1365-2966.2010.16395.x`](http://doi.org/10.1111/j.1365-2966.2010.16395.x)

(ref: delosreyes19) de los Reyes, M. A. C., & Kennicutt, Robert C., J. 2019, ApJ, 872, 16, doi: [`10.3847/1538-4357/aafa82`](http://doi.org/10.3847/1538-4357/aafa82)

(ref: diaz-santos10) Dı́az-Santos, T., Charmandaris, V., Armus, L., et al. 2010, ApJ, 723, 993, doi: [`10.1088/0004-637X/723/2/993`](http://doi.org/10.1088/0004-637X/723/2/993)

(ref: drew18) Drew, P. M., Casey, C. M., Burnham, A. D., et al. 2018, ApJ, 869, 58, doi: [`10.3847/1538-4357/aaedbf`](http://doi.org/10.3847/1538-4357/aaedbf)

(ref: drew20) Drew, P. M., Casey, C. M., Cooray, A., & Whitaker, K. E. 2020, ApJ, 892, 104, doi: [`10.3847/1538-4357/ab7939`](http://doi.org/10.3847/1538-4357/ab7939)

(ref: dudzeviciute20a) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: elbaz18a) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110, doi: [`10.1051/0004-6361/201732370`](http://doi.org/10.1051/0004-6361/201732370)

(ref: fujimoto17a) Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83, doi: [`10.3847/1538-4357/aa93e6`](http://doi.org/10.3847/1538-4357/aa93e6)

(ref: Gruppioni13a) Gruppioni, C., Pozzi, F., Rodighiero, G., et al. 2013, MNRAS, 432, 23, doi: [`10.1093/mnras/stt308`](http://doi.org/10.1093/mnras/stt308)

(ref: gullberg19) Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019a, MNRAS, 490, 4956, doi: [`10.1093/mnras/stz2835`](http://doi.org/10.1093/mnras/stz2835)

(ref: gullberg19a) —. 2019b, MNRAS, 490, 4956, doi: [`10.1093/mnras/stz2835`](http://doi.org/10.1093/mnras/stz2835)

(ref: hainline11a) Hainline, L. J., Blain, A. W., Smail, I., et al. 2011, ApJ, 740, 96, doi: [`10.1088/0004-637X/740/2/96`](http://doi.org/10.1088/0004-637X/740/2/96)

(ref: hayward18a) Hayward, C. C., Chapman, S. C., Steidel, C. C., et al. 2018, MNRAS, 476, 2278, doi: [`10.1093/mnras/sty304`](http://doi.org/10.1093/mnras/sty304)

(ref: hodge12a) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11, doi: [`10.1088/0004-637X/760/1/11`](http://doi.org/10.1088/0004-637X/760/1/11)

(ref: hodge15) Hodge, J. A., Riechers, D., Decarli, R., et al. 2015, ApJL, 798, L18, doi: [`10.1088/2041-8205/798/1/L18`](http://doi.org/10.1088/2041-8205/798/1/L18)

(ref: hodge16a) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: jimenez20) Jiménez-Andrade, E. F., Zavala, J. A., Magnelli, B., et al. 2020, ApJ, 890, 171, doi: [`10.3847/1538-4357/ab6dec`](http://doi.org/10.3847/1538-4357/ab6dec)

(ref: kennicutt98) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: kennicutt12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: kirkpatrick12) Kirkpatrick, A., Pope, A., Alexander, D. M., et al. 2012, ApJ, 759, 139, doi: [`10.1088/0004-637X/759/2/139`](http://doi.org/10.1088/0004-637X/759/2/139)

(ref: kirkpatrick17a) Kirkpatrick, A., Pope, A., Sajina, A., et al. 2017, ApJ, 843, 71, doi: [`10.3847/1538-4357/aa76dc`](http://doi.org/10.3847/1538-4357/aa76dc)

(ref: kroupa03a) Kroupa, P., & Weidner, C. 2003, ApJ, 598, 1076, doi: [`10.1086/379105`](http://doi.org/10.1086/379105)

(ref: laigle16a) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24, doi: [`10.3847/0067-0049/224/2/24`](http://doi.org/10.3847/0067-0049/224/2/24)

(ref: lang19) Lang, P., Schinnerer, E., Smail, I., et al. 2019, ApJ, 879, 54, doi: [`10.3847/1538-4357/ab1f77`](http://doi.org/10.3847/1538-4357/ab1f77)

(ref: lee13a) Lee, N., Sanders, D. B., Casey, C. M., et al. 2013, ApJ, 778, 131, doi: [`10.1088/0004-637X/778/2/131`](http://doi.org/10.1088/0004-637X/778/2/131)

(ref: lehnert96a) Lehnert, M. D., & Heckman, T. M. 1996, ApJ, 472, 546, doi: [`10.1086/178086`](http://doi.org/10.1086/178086)

(ref: li01a) Li, A., & Draine, B. T. 2001, ApJ, 554, 778, doi: [`10.1086/323147`](http://doi.org/10.1086/323147)

(ref: lutz16a) Lutz, D., Berta, S., Contursi, A., et al. 2016, A&A, 591, A136, doi: [`10.1051/0004-6361/201527706`](http://doi.org/10.1051/0004-6361/201527706)

(ref: magdis12a) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6, doi: [`10.1088/0004-637X/760/1/6`](http://doi.org/10.1088/0004-637X/760/1/6)

(ref: magnelli14a) Magnelli, B., Lutz, D., Saintonge, A., et al. 2014, A&A, 561, A86, doi: [`10.1051/0004-6361/201322217`](http://doi.org/10.1051/0004-6361/201322217)

(ref: michalowski12) Michałowski, M. J., Dunlop, J. S., Cirasuolo, M., et al. 2012, A&A, 541, A85, doi: [`10.1051/0004-6361/201016308`](http://doi.org/10.1051/0004-6361/201016308)

(ref: miettinen17a) Miettinen, O., Delvecchio, I., Smolčić, V., et al. 2017, A&A, 606, A17, doi: [`10.1051/0004-6361/201730762`](http://doi.org/10.1051/0004-6361/201730762)

(ref: narayanan15a) Narayanan, D., Turk, M., Feldmann, R., et al. 2015, Nature, 525, 496, doi: [`10.1038/nature15383`](http://doi.org/10.1038/nature15383)

(ref: peng10a) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2010, AJ, 139, 2097, doi: [`10.1088/0004-6256/139/6/2097`](http://doi.org/10.1088/0004-6256/139/6/2097)

(ref: roseboom13a) Roseboom, I. G., Dunlop, J. S., Cirasuolo, M., et al. 2013, MNRAS, 436, 430, doi: [`10.1093/mnras/stt1577`](http://doi.org/10.1093/mnras/stt1577)

(ref: rujopakarn16a) Rujopakarn, W., Dunlop, J. S., Rieke, G. H., et al. 2016, ApJ, 833, 12, doi: [`10.3847/0004-637X/833/1/12`](http://doi.org/10.3847/0004-637X/833/1/12)

(ref: sajina07a) Sajina, A., Yan, L., Armus, L., et al. 2007, ApJ, 664, 713, doi: [`10.1086/519446`](http://doi.org/10.1086/519446)

(ref: sanders03) Sanders, D. B., Mazzarella, J. M., Kim, D.-C., Surace, J. A., & Soifer, B. T. 2003, The Astronomical Journal, 126, 1607, doi: [`10.1086/376841`](http://doi.org/10.1086/376841)

(ref: schreiber18) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30, doi: [`10.1051/0004-6361/201731506`](http://doi.org/10.1051/0004-6361/201731506)

(ref: simpson17) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2017, ApJ, 839, 58, doi: [`10.3847/1538-4357/aa65d0`](http://doi.org/10.3847/1538-4357/aa65d0)

(ref: speagle14a) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: spilker16) Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112, doi: [`10.3847/0004-637X/826/2/112`](http://doi.org/10.3847/0004-637X/826/2/112)

(ref: swinbank14a) Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267, doi: [`10.1093/mnras/stt2273`](http://doi.org/10.1093/mnras/stt2273)

(ref: symeonidis13a) Symeonidis, M., Vaccari, M., Berta, S., et al. 2013, MNRAS, 431, 2317, doi: [`10.1093/mnras/stt330`](http://doi.org/10.1093/mnras/stt330)

(ref: tadaki18a) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613, doi: [`10.1038/s41586-018-0443-1`](http://doi.org/10.1038/s41586-018-0443-1)

(ref: u12a) U, V., Sanders, D. B., Mazzarella, J. M., et al. 2012, ApJS, 203, 9, doi: [`10.1088/0067-0049/203/1/9`](http://doi.org/10.1088/0067-0049/203/1/9)

(ref: viero13) Viero, M. P., Moncelsi, L., Quadri, R. F., et al. 2013, ApJ, 779, 32, doi: [`10.1088/0004-637X/779/1/32`](http://doi.org/10.1088/0004-637X/779/1/32)

(ref: whitaker14a) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104, doi: [`10.1088/0004-637X/795/2/104`](http://doi.org/10.1088/0004-637X/795/2/104)

(ref: wien1897) Wien, W. 1897, The London, Edinburgh, and Dublin Philosophical Magazine and Journal of Science, 43, 214, doi: [`10.1080/14786449708620983`](http://doi.org/10.1080/14786449708620983)

(ref: younger09a) Younger, J. D., Omont, A., Fiolet, N., et al. 2009, MNRAS, 394, 1685, doi: [`10.1111/j.1365-2966.2009.14455.x`](http://doi.org/10.1111/j.1365-2966.2009.14455.x)

[^1]: Note that this only deviates by 5% from Wien’s law for optically thin, idealized blackbodies.

</paper>

Write the methods card for this paper.