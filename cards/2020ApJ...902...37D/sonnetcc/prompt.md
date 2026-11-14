# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...902...37D\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...902...37D",
 "title": "The Ionized- and Cool-gas Content of the BR1202-0725 System as Seen by MUSE and ALMA",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "Drake, A. B.",
 "n_authors": 10,
 "arxiv_id": "2007.14221",
 "doi": "10.3847/1538-4357/aba832",
 "alma_projects_linked_by_archive": [
  "2013.1.00039.S",
  "2013.1.00259.S",
  "2013.1.00745.S",
  "2015.1.00388.S",
  "2015.1.01489.S",
  "2017.1.00963.S",
  "2017.1.01516.S",
  "2011.0.00006.SV"
 ]
}
```

Paper text:
<paper>
# The Ionised- and Cool-Gas Content of The BR1202-0725 System\
as seen by MUSE and ALMA.

## Abstract

We present  observations of the gas-rich major-merger BR$1202-0725$ at $z\sim4.7$, which constitutes one of the most overdense fields known in the early Universe. We utilise these data in conjunction with existing  observations to compare and contrast the spatially resolved ionised- and cool-gas content of this system which hosts a quasar (QSO), a sub-millimeter galaxy (SMG), the two known optical companions (“LAE 1", “LAE 2"), and an additional companion discovered in this work “LAE 3" just 5 $''$ to the North of the QSO. We find that QSO BR$1202-0725$ exhibits a large Ly$\alpha$ halo, covering $\approx55$ pkpc on-sky at surface brightness levels of SB$\geq$1E-17erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$. In contrast, the SMG, of similar far-infrared luminosity and star formation rate (SFR), does not exhibit such a Ly$\alpha$ halo. The QSO’s halo exhibits high velocity widths ($\sim1000$ km s$^{-1}$) but the gas motion is to some extent kinematically coupled with the previously observed \[C\] bridge between the QSO and the SMG. We note that the object known in the literature as LAE 2 shows no local peak of Ly$\alpha$ emission, rather, its profile is more consistent with being part of the QSO’s extended Ly$\alpha$ halo. The properties of LAE 3 are typical of high-redshift LAEs; we measure F$_{\rm{Ly\alpha}}$(LAE 3) = $0.24\pm$0.03E-16erg s$^{-1}$ cm$^{-2}$, corresponding to SFR$_{\rm{Ly\alpha}}\approx\ $5.0$\pm$0.5 M${_\odot}$ yr$^{-1}$. The velocity width is $\Delta v$(LAE 3) $\approx 400$ km s$^{-1}$, and equivalent width EW$_0$(Ly$\alpha_{\,5\sigma}^{\,lim})\,\geq\,34.05$ Å, consistent with star formation being the primary driver of Ly$\alpha$ emission. We also note a coherent absorption feature at $\sim -400$km s$^{-1}$ in spectra from at least three objects; the QSO, LAE 1 and “LAE 2" which could imply the presence of an expanding neutral gas shell with an extent of at least $24$ pkpc.\

# Introduction

The BR$1202-0725$ system is a prime example of a gas-rich major-merger at high redshift, which theory and simulations suggest are key to our understanding of galaxy evolution. Quasi-Stellar Object (QSO) ‘BR$1202-0725$’, was discovered in the *APM-BRI* survey (cite: IrwinMcMahonHazard1991) – it was the first object at z$>4$ to be detected in CO emission (cite: Ohta96), and these molecular gas observations revealed for the first time an optically-obscured sub-mm galaxy (SMG) lying $\sim 4 \,\ensuremath{''}$ to the North-West of the QSO ((cite: Omont96), (cite: Iono2006)). Subsequently, the field has been targeted with a multi-wavelength campaign of observations to measure its gas content ((cite: Wagg2012), (cite: Carilli2013)), and chemical abundances ((cite: Decarli2018), (cite: Lehnert20)).

Indeed, the hierarchical growth of structure predicts that QSOs at high redshift are biased tracers of galaxy formation, situated in overdense environments (e.g. (cite: Overzier09)). In the case of QSO BR$1202-0725$, in addition to the nearby SMG, narrow-band data have indicated the presence of two Lyman-$\alpha$ emitters (LAEs) in the vicinity ((cite: Hu1996), (cite: Omont96), (cite: Ohyama2004), (cite: Salome2012)): the source denoted LAE 1, positioned to the North-West of the QSO (in the direction of the SMG) and LAE 2 towards the South-West. Futhermore, \[C\]$_{158\rm{\mu m}}$ observations of the entire BR$1202-0725$ field from the commissioning of the Atacama Large Millimetre Array (; (cite: WootenThompson09)), suggest the possible presence of a bridge of \[C\]$_{158\rm{\mu m}}$ emission between the QSO and the SMG, tracing cooler ionised and/or neutral gas, intriguingly with an indication of a local maximum at the position of LAE 1. Together, this makes BR$1202-0725$ an ideal system to study a diverse population of galaxies evolving in one of the most overdense regions of the Universe known, just $\sim 1.2$ Gyr after the Big Bang.

The nature of the two companion objects denoted LAE 1 and LAE 2 has been debated. The object that appears in  and  imaging, later named LAE 1, was spectroscopically confirmed by the detection of Ly$\alpha$ emission in (cite: Hu1996). The optical line ratios presented in (cite: Williams14) suggest that the primary source of Ly$\alpha$ emission in LAE 1 is star formation i.e. neither C nor He emission is detected, which should each be present in the case of photoionisation by an active galactic nucleus (AGN)[^1]. LAE 1 is detected in \[C\]$_{158\rm{\mu m}}$ ((cite: Carilli2013), (cite: Wagg2012)), and shows a narrow emission line (of width $\Delta$v$_{\rm{[CII]}}$ = 56 km s$^{-1}$ at full width half-maximum; FWHM), taking this as an indicator of systemic redshift, the Ly$\alpha$ emission is offset by 49 km s$^{-1}$ from its predicted position in wavelength (cite: Williams14). Observations in (cite: Decarli2018), (cite: Pavesi16), and (cite: Lee19) detect \[N\]$_{122\rm{\mu m}}$ emission from ionised Nitrogen at the position of LAE 1, at levels which suggest an origin within H regions.

![image](figures/HST_775.png) ![image](figures/HST_775_ALMA_NII.png)

LAE 2 ((cite: Hu97), (cite: Salome2012)), appears in narrowband imaging to be an LAE at the redshift of the QSO. Long-slit spectroscopic observations in (cite: Williams14) confirmed the presence of Ly$\alpha$ emission at the position of LAE 2, at approximately the redshift of the QSO, lending support to the idea that the object was indeed an LAE associasted with this group. The \[C\] emission from LAE 2 falls at the edge of the  spectral setup, and hence it is not easy to judge the peak frequency or velocity width of the line (see (cite: Carilli2013) and (cite: Wagg2012)). (cite: Decarli2018) however reported an \[N\]/\[C\] ratio for this object, which indicated that this sub-mm emission in LAE 2 is likely to originate from H dominated regions, and as such the object could be forming stars.\
In addition to the presence of companion galaxies at the redshift of the QSO, these massive objects are predicted to reside at the nodes of large-scale structure, composed of sheets and filaments of HI gas, known as the ‘cosmic web’ (e.g. (cite: springel06)). This gas is too diffuse to form stars, but instead is funnelled along the filamentary structure onto massive dark-matter halos hosting the QSO and/or other massive collapsed objects (e.g. (cite: vandevoort11)), acting as fuel for their star formation. As a QSO is ‘fed’ by this cool gas ($T \sim 10^4$ K), a number of physical processes (whose relative contributions are debated) lead to the emission of Ly$\alpha$ photons which, due to their resonant nature in HI gas, require careful interpretation, including modelling of their complex radiative transfer processes (e.g. (cite: Michel-Dansac20)). Although extended Ly$\alpha$ halos can arise surrounding a diverse set of objects (e.g. (cite: Venemans07)) in the case of a central QSO, the prime candidates responsible for powering the Ly$\alpha$ emission could be any of the following; (A) Photoionisation of the cool gas by a centrally located AGN (sometimes referred to as ‘Ly$\alpha$ fluorescence’; (cite: Cantalupo10), (cite: Prescott15)); (B) ‘gravitational cooling’ of in-flowing (pristine) gas, in which collisional excitation of atoms is the dominant power source ((cite: Smith07); (cite: Rosdahl12); (cite: Daddi20)); and (C) shock-heating of the gas as a result of violent, possibly jet-induced star formation (e.g. (cite: Taniguchi01)). In addition to these processes, star formation within the QSO’s host galaxy, and/or star formation within other satellite galaxies could act as energy sources to also photoionise some fraction of the cool gas.\
In recent years, observations from the panoramic integral field spectrograph  (cite: Bacon2010) have revolutionised the field of study surrounding the detection and analysis of extended Ly$\alpha$ halos/nebulae around QSOs and ‘normal’ star-forming galaxies ((cite: Bacon2015), (cite: Wisotzki16), (cite: Bacon2017), (cite: Inami2017), (cite: Drake2017a), (cite: Drake2017b), (cite: Leclercq2017)). The high spectral ($\Delta\lambda=1.25$ Å) and spatial (0.202 $''$) resolution have revealed detailed spatially-resolved kinematic maps of Ly$\alpha$ halos surrounding QSOs at the highest redshifts ((cite: Farina2017), (cite: Ginolfi2018), (cite: Drake2019), (cite: Farina19)), and at z$\sim$2-3 where other rest-frame ultraviolet emission lines are accessible with  e.g. C and/or He  potentially enabling constraints on the powering mechanisms of the halos ((cite: ArrigoniBattaia15a), (cite: ArrigoniBattaia15b), (cite: Borisova2016), (cite: ArrigoniBattaia2018), (cite: Marino2019); Also see results from the Keck Cosmic Web Imager e.g. (cite: Cai19)).\
Until now, observations of BR$1202-0725$’s ionised gas content, traced by Ly$\alpha$ emission, have been limited to photometry from broad or narrow-bands, long-slit spectroscopy, and early IFU observations from TIGER (cite: Petitjean96). In this paper we present IFU data covering the BR$1202-0725$ field from  – simultaneously revealing an extended Ly$\alpha$ halo around the QSO, allowing the re-analysis of Ly$\alpha$ emission from companion galaxies embedded within the halo, and comparing the ionised- and cool-gas properties of both Ly$\alpha$ halo and companion objects in the field.\
This paper proceeds as follows; in Section [2](#sect:obs) we describe the data used in this paper, and its processing before analysis. The data consist of archival HST imaging, an archival  \[C\] datacube, deep  dust continuum imaging, and finally the  datacube. We also describe briefly here our method for PSF-subtraction in the  cube. In Section [3](#sect:res-Lya-halo) we present  images of the field, and a spectrum of the QSO, followed by the results of our PSF-subtraction. Here we analyse the spatial extent and morphology of the Ly$\alpha$ halo, and take advantage of the spatial resolution of  to produce moment maps of the Ly$\alpha$ emission, and search for overlap or coincidence of Ly$\alpha$ and \[C\] emission across the field. We speculate on the dominant powering mechanism of the Ly$\alpha$ halo and perform a search for extended C emission. Next, in Section [4](#sect:res-LAEs) we present images and spectra of a series of companions in the field, including the SMG, LAE 1 and LAE 2. For each object in the system we assess the Ly$\alpha$ emission and derive velocity widths, star-formation rates (SFRs; where appropriate) and constraints on the rest-frame equivalent widths of Ly$\alpha$ (EW$_0$; again where possible) before using these measurements to re-assess the nature of the proposed companions. We summarise our findings on the QSO’s Ly$\alpha$ halo and all accompanying objects in Section [5](#sect:concl).\
We assume a $\Lambda$CDM cosmology with $\Omega_m = 0.3$, $\Omega_{\Lambda} = 0.7$ and H$_0=70$ km s$^{-1}$ Mpc$^{-1}$. In this cosmology, 1 $''$ = 6.64 pkpc at z $\approx$ 4.69.\

![](figures/NB_cont_spec.png)

# Observations and Data Reduction

In addition to our analysis of the new  observations, we make use of two existing datasets from ; allowing a multiwavelength comparison of the ionised and neutral gas content of the BR$1202-0725$ system; and archival HST imaging to give an optical overview of the field at the highest-resolution available. The datasets are described below.

## HST overview of the field

In Figure [1](#Fig: HST) we show the archival  image of BR$1202-0725$ highlighting in the left panel the positions of the QSO, the SMG, two known-LAEs (LAE 1, LAE 2) and an additional LAE discovered in this work; LAE 3. In the right-hand panel we show the  image again, overlaying sub-mm dust continuum contours from the deepest ALMA observations of the field, see Section [2.2.1](#sect:obs-ALMA cont) for a description. Both the archival HST imaging, and the dust-continuum maps are used throughout this work for orientation purposes only.\

## ALMA Observations

### Deep Continuum Imaging

In order to obtain a deep mm continuum map we explored all public data in the ALMA archive available for our system. Projected baseline lengths for the combined continuum dataset are between 14 - 1440 m, with the 80th percentile at 288 m. We decided to combine the data in the frequency range of 190 – 297 GHz (bands 5, 6 and 7). Inside this 107 GHz bandwidth, 33 GHz was observed with six frequency setups[^2]. These setups cover several far-infrared (FIR) bright molecular emission lines of CO (high excitation rotational CO lines J$_{up}$ = 10, 12, 14) and H$_2$O, and a fine atomic transition line \[N\] at $205$ microns. A total width of 1500 km s$^{-1}$ centered at each of the emission lines was excluded from the continuum imaging process. This width choice corresponds to two times the FWHM of the brightest \[C\] line detected in the SMG inside this system (cite: Carilli2013). The continuum map was obtained from the remaining line-free channels spanning an effective bandwidth of 25 GHz. Individual spectral setups were observed at roughly similar resolutions, with synthesized beam FWHM range of $0.6$ $''$ - $1.5$ $''$, and a position angle of 88$^{\circ}$, thus allowing joint imaging of all the datasets. For imaging we use the tclean task contained in the Common Astronomy Software Applications (CASA[^3]) package (cite: mcmullin07). Given the large bandwidth available, we image the data using the multi-term multi-frequency synthesis (MTMFS, NTERMS=2, (cite: rau11)). The data were imaged with natural weighting to maximize the point source sensitivity. The synthesised beam side-lobes of the combined dataset are smaller than 5%. Due to good quality of the final map, no additional weighting of visibilities was deemed necessary[^4]. Cleaning was performed with the multi-scales algorithm (using scales corresponding to a single pixel, 1x, and 3x the beam size) first down to $5\sigma$ in the entire map, and then further down to $1.5\sigma$ inside manually defined cleaning regions, which outline the observed emission. The final continuum map is given at the monochromatic frequency of 243.5 GHz, resolution of $0.83\,\ensuremath{''} \times 0.73\,\ensuremath{''}$, and has a root-mean-square (rms) noise level of $1\sigma=12.38~\mu$Jy beam$^{-1}$.

### Archival \[CII\] Observations

We make use of  $335$ GHz (Band $7$) Science Verification data with a central frequency targeting the \[C\] line at the redshift of the QSO and the SMG. The data were first presented in (cite: Wagg2012) and (cite: Carilli2013). We applied a velocity-frame correction to the published data to convert from the observed frame (topocentric) to the local standard of rest (LSRK) for accurate comparison to velocities in the  datacube.

## MUSE Observations

### MUSE Data Reduction

 data were taken as part of ESO programme $0102.A-0428(A)$, PI Farina, and reduced as in (cite: Farina2017) and (cite: Farina19) using the  Data Reduction Software version 2.6 ((cite: Weilbacher12), (cite: Weilbacher14)). Two exposures of 1426 s were taken, with $<$ $5\,\ensuremath{''}$ shifts and 90 degree rotations. The PSF has a size of 0.6$\,\ensuremath{''}$ at the observed wavelengths of the Ly$\alpha$ line (the median delivered PSF on stars in the field is closer to 0.7$\,\ensuremath{''}$). The 5$\sigma$ surface brightness detection limit is $4.2$ $\times$ $10^{-17}$ erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$ for an aperture of 1 square arcsecond. Data have been corrected for galactic extinction, and emission from night sky lines is removed using the Zurich Atmospheric Purge software (ZAP; (cite: Soto2016)).

![](figures/tot_halo_flux.png)

![image](figures/for_Ema_1202.png) ![image](figures/NB1202_ALMA.png) ![image](figures/three_demo_panels.png)

|  |  |  |  |  |
|:---|:--:|:--:|:--:|---:|
| **Object** | **$z$$_{{\rm{[CII]}}}$**[^5] | **Vel Offset**[^6] | **Pred $\lambda$ Ly$\alpha$** | **References** |
|  |  | \[kms$^{-1}$\] | \[Å\] |  |
| **QSO** | 4.6942 | 0.0 | 6922.27 | (cite: McMahon94), (cite: Isaak1994) |
| **SMG** | 4.6915 | -142.1 | 6918.99 | (cite: Omont1996), (cite: Riechers06) |
| **LAE 1** | 4.6950 | 42.0 | 6923.24 | (cite: Hu1996), (cite: Ohyama2004) |
| **LAE 2** | 4.7055 | 595.5 | 6936.01 | (cite: Hu97), (cite: Wagg2012), (cite: Carilli2013) |

### MUSE PSF Subtraction

With a view to uncovering low-surface-brightness Ly$\alpha$ emission in the MUSE data surrounding QSO BR$1202-0725$, we follow the same procedure as in (cite: Drake2019) to model and subtract the point-spread function (PSF) in the data (also demonstrated in (cite: Farina19)). In brief, this entails collapsing several spectral layers of the QSO’s optical continuum which is dominated by light from the accretion disk of the AGN, and appears as a point source at the resolution of MUSE. By using the quasar itself to create the “PSF image" we avoid issues of spatial PSF-variation/interpolation across the field. The wavelength layers chosen to construct the PSF image are highlighted in pink in the right-hand panel of Figure [2](#Fig: PSF). We then work systematically through the MUSE cube, scaling our PSF image such that the flux in the pixel at the image peak becomes equal to the flux of the QSO in the same spatial pixel. By subtracting this scaled PSF image from each wavelength layer we produce an entire PSF-subtracted datacube. Finally, as in (cite: Drake2019), we mask an ellipse on every layer of the datacube of radii equal to the FWHM of a 2-dimensional Gaussian fit to the PSF image, and exclude this region from further analysis to avoid residuals near the bright central source, unless otherwise noted.

# Extended Ly$\alpha$ in the BR$1202-0725$ field

## Total Flux of Ly$\alpha$ Halo around QSO BR$1202-0725$

In Figure [3](#Fig: Blob Spec) we show a narrow-band image comprised of all the Ly$\alpha$ emission in a square 12 $''$ region surrounding the QSO. The narrowband width was chosen to encompass the entirety of the red side of the Ly$\alpha$ line after PSF-subtraction, and to include emission out to the same velocity bluewards of the systemic redshift of the QSO. This amounts to a total of 61Å, or $\approx 2640$ km s$^{-1}$. In the right-hand panel of Figure [3](#Fig: Blob Spec) we show the PSF-subtracted spectrum extracted in a 3 $''$ diameter aperture shaded in blue, and over plot with a black line the PSF-subtracted spectrum that results from summing all emission within the $\num{1e-17}$ erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$ surface-brightness contour. Interestingly the halo’s spectral shape is somewhat ‘flat-topped’, which may be the result of contributions from objects at different velocities within the halo, or simply represent an intrinsically broad line. The flux of diffuse Ly$\alpha$ within the SB $=\,\num{1e-17}$ erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$ surface-brightness contour is F$_{\rm{Ly\alpha}} =$ $1.39\,\pm$ $\num{0.01e-15}$  erg s$^{-1}$ cm$^{-2}$, after continuum-subtraction, masking both the position of the QSO (across a $1\,\ensuremath{''}$ diameter), and LAE 1 (across a $1.6\,\ensuremath{''}$ diameter). If the halo emission were powered solely by star formation, we could translate this to an SFR according to Equation [\[eq:1\]](#eq:1) (cite: ouchi03):

$$\begin{equation}
\label{eq:1}
    \mathrm{SFR}_{\mathrm{Ly\alpha}} (\mathrm{M}_{\odot} yr^{-1}) =  \mathrm{L}_{{\rm{Ly\alpha}}} \times 1.05 \times 10^{42.0} \mathrm{erg\, s}^{-1}
\end{equation}$$

where L$_{{\rm{Ly\alpha}}}$ is the Ly$\alpha$ luminosity in cgs units. Our measured flux translates to a luminosity of L$_{\rm{Ly\alpha}}\,=$ $\num{3.11E+44}$ erg s$^{-1}$, which would then correspond to an SFR of almost $\approx 300$ M${_\odot}$ yr$^{-1}$.\

## Morphology of Extended Ly$\alpha$ around QSO BR$1202-0725$

To examine the distribution of the diffuse Ly$\alpha$ in more detail, we show in Figure [4](#Fig: NB) a narrow velocity range ($\sim\,200$ km s$^{-1}$; i.e. a collapse of the monochromatic wavelength layers between $6927$ and $6932$ Å). This choice of velocity range reveals filamentary structure at low surface-brightness levels, highlighting the complex morphology of the halo, while encompassing wavelength layers within which the QSO, LAE 1, LAE 2 and LAE 3 are all visible. In the top left-hand panel we show the Ly$\alpha$ surface brightness, contoured between SB $=\,\num{5e-19}$ and $\num{5e-18}$ erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$, and again highlight the positions of the QSO, the SMG, and three LAEs in the system. Figure [4](#Fig: NB) demonstrates that diffuse Ly$\alpha$ connects all three objects, while none is seen surrounding the SMG. Interestingly, the low-surface-brightness emission in Ly$\alpha$ extends directly in the direction of the optically-obscured SMG, and fully encompasses the position of LAE 1, however by the position of the SMG, the halo is no longer visible in this velocity range. The Ly$\alpha$ emission at the position of LAE 2 however appears indistinguishable from the halo extending from the QSO in this image – we return to this in Section [4.2](#sect: nature of objs). Finally, LAE 3 appears as a distinct source in Ly$\alpha$, however its emission is possibly connected via a low-surface-brightness bridge of Ly$\alpha$ emission to the position of the QSO. In the top right-hand panel we display the same Ly$\alpha$ surface-brightness image, but this time overlay contours depicting \[C\] emission ((cite: Wagg2012) and (cite: Carilli2013)) from the entire collapsed data cube. In the lower panels, we show cutouts at three different velocites relative to the systemic redshift of QSO BR$1202-0725$ (i.e. a velocity slice of the Ly$\alpha$ halo overlaid with contours depicting \[C\] emission in the corresponding velocity slice). The velocities shown here were selected from the full series of channel maps presented in Appendix B, and are chosen to highlight a number of features. First, the purported \[C\] bridge between the QSO and the SMG. This is seen at negative velocities (which correspond to the slightly lower redshift of the SMG than the QSO) which is seen across multiple channels. Secondly, in the central panel we show the channel closest to systemic, the extended \[C\] persists, with a local maximum thought to define the position of LAE 1’s ISM. In the final panel, $500$ km s$^{-1}$ red-ward of the QSO, the position of LAE 2 becomes clear. Together, these data begin to highlight the diversity of properties of the objects in this field. While the QSO appears bright in both Ly$\alpha$ and \[C\] emission, the SMG appears only at sub-mm wavelengths. LAEs 1 and 2 show \[C\] emission most visible in channels at their respective velocities, however LAE 3 does not show any associated \[C\] emission. We will return to each of these features and discuss the objects’ nature in Section [4](#sect:res-LAEs).

![](figures/Aly_moms_sm1pt0_SN1pt2_Lya6922pt400_Lang40.png)

## Kinematic analysis of Ly$\alpha$ around QSO BR$1202-0725$

To analyse the internal kinematics of the extended Ly$\alpha$ emission, we present zeroth-, first- and second-moment maps (representing the total flux, velocity and dispersion maps, respectively) in Figure [5](#Fig: Lya moms), relative to the predicted peak of the Ly$\alpha$ line at a systemic redshift of $z = 4.6942$. We analyse the data in a manner consistent with (cite: Drake2019); we first smooth the datacube in the two spatial directions with a Gaussian kernel of $\sigma = 1.0$ pixel, and calculate the non-parametric moments of the data, i.e. we do not assume any functional form for the Ly$\alpha$ spectral shape. In the first panel we show the flux-weighted zeroth-moment. This image/map is essentially the same as that shown on the left-hand side of Figure [3](#Fig: Blob Spec).\
In the central panel we show the first moment of the halo’s Ly$\alpha$ emission, which gives the flux-weighted velocity of the halo gas relative to the peak of the emission, applying a uniform post-processing S/N cut of 1.0 on the moment zero image. The velocity structure is clumpy and complex. The majority of the extended emission, which appears to the North of the QSO, is red-shifted by a few hundred km s$^{-1}$, only small patches of emission ($\leq2 \,\ensuremath{''}$ on-sky) appear blue-shifted, and they each appear towards the South of QSO. LAE 1 does not appear kinematically distinct from the halo. No obvious signs of a flow of gas between the two objects is seen in this map, however for a more thorough examination of the relative velocities of Ly$\alpha$ and \[C\] emission across the field of view we refer the reader to Appendix [7](#App:channel maps) where we show a series of ‘channel maps’, displaying images of the extended Ly$\alpha$ emission seen with , overlaid with \[C\] contours from  (see (cite: Carilli2013) and (cite: Wagg2012)). The spectral resolution of  at $\sim 7000$Å corresponds to $\sim\Delta v = 100$ kms$^{-1}$. The channel spacing in velocity of the \[C\] emission seen with , is $\sim\Delta v = 35$ km s$^{-1}$. The maps show that the extended Ly$\alpha$ emission is to some extent co-spatial with the \[C\], and peaks at the same velocities as the \[C\] bridge between BR$1202-0725$ and the SMG proposed in (cite: Carilli2013). The Ly$\alpha$ emission is however much broader than the \[C\], and as such Ly$\alpha$ still appears bright in channels beyond the end of the  \[C\] coverage.\
Finally, in the third panel of Figure [5](#Fig: Lya moms), we show the second moment, $\sigma$, giving the velocity dispersion of the gas, and applying the same uniform S/N cut of 1.0 on the moment zero image. Velocities close-in to the QSO are very high, of order $\sim1000$ km s$^{-1}$, with a region of lower values (of order $500$ km s$^{-1}$) in the direction of LAE 1.\

## Constraints on the dynamical mass of the halo

Using the moment maps, we can roughly estimate the dynamical mass of this gas given a number of assumptions. For instance, in the moment zero flux image (Figure [5](#Fig: Lya moms), left) where the entire width of the Ly$\alpha$ line is collapsed, emission stretches $\approx 8\,\ensuremath{''}$ North$-$South, and $\approx 8\,\ensuremath{''}$ East$-$West surrounding the QSO. We therefore take an average radius of $4\,\ensuremath{''}$, which corresponds to $\approx27$ pkpc at $z=4.69$. In the moment 1 map (Figure [5](#Fig: Lya moms), centre) we see a gradient of approximately $v\approx\pm 300$ km s$^{-1}$ across the halo. Then, if one assumes rotation of the gas is responsible for the velocity gradient, we solve for dynamical mass $M_{\rm{\,dyn}}$:\
$$\begin{equation}
    M_{\mathrm{dyn}} = rv^2/G
\end{equation}$$

where $G$ is the gravitational constant, $r$ is the halo radius, and $v$ is the velocity range across this radius. As we have no information on inclination angle, we place a lower limit on the dynamical mass of the halo; $M_{\rm{\,dyn}} \geq$ 6E11 M$_{\odot}$. Even without any correction for inclination angle, this is significantly larger than the combined molecular gas mass of the QSO-SMG system reported in the literature ($\sim10^{11}$ M$_{\odot}$; (cite: Omont1996), (cite: Riechers06)), and 2 orders of magnitude larger than the QSO’s black hole mass, M$_{{\rm{BH}}}= \num{1.9e9}$ M$_{\odot}$ ((cite: Carniani2013)).

## Speculation on Ly$\alpha$ powering mechanism

The powering mechanisms of Ly$\alpha$ halos at high redshift have long been debated. BR$1202-0725$ is an example of a system where any one of the proposed mechanisms outlined in Section [1](#sec:intro) could naively be assumed the primary driver of the halo emission, or perhaps more likely, a complex mixture of processes are responsible. The QSO has an obscured star-formation rate in excess of 1000 M${_\odot}$ yr$^{-1}$ (cite: Carilli2013), and as such, in-situ star-formation could be responsible for the extended Ly$\alpha$ emission. Likewise, copious amounts of pristine gas are required to fuel this major merger which could give rise to gravitational cooling of the gas as it is funnelled onto the QSO. It is perhaps of some significance then that QSO BR$1202-0725$ is accompanied by the SMG of similar gas mass, inferred SFR, and dust content (cite: Carilli2013), but that displays no prominant Ly$\alpha$ halo. In the absence of any further diagnostics, this lends support to the idea that the Ly$\alpha$ halo is directly linked to the actively accreting SMBH in the QSO, and not to star formation.

Several studies in the literature have recently taken steps towards identifying the powering mechanisms of Ly$\alpha$ halos around QSOs through the use of additional diagnostic lines (cite: ArrigoniBattaia18). Motivated by these studies, we take advantage of the spectral coverage of  to search for any extended C emission surrounding BR$1202-0725$. The metal line C indicates whether the Ly$\alpha$ emitting gas has been enriched (i.e. it orignated within the host galaxy) or is pristine (falling onto the halo for the first time). In Appendix [8](#APP: CIV) we show the  spectrum of QSO BR$1202-0725$ again, and overlay a composite quasar spectrum (cite: Selsing16), ‘red-shifted’ to $z=4.6942$. We highlight on this spectrum the predicted observed wavelengths of various emission lines, in particular C $\lambda_{em}=1549$Å. We extract an image and spectrum exactly as for Ly$\alpha$ in Figure [3](#Fig: Blob Spec), but this time centred on the predicted wavlength of C. We detect no extended C emission down to a surface brightness limit of 0.19E-16 erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$ in a square arcsecond. Given however that metal lines in high-redshift QSOs are frequently observed to be blueshifted with respect to the systemic velocity, we repeat this exercise in the 8500-8700 Å region where we see a subtle, broad ‘bump’ in the QSO spectrum, but find no evidence for extended emission in this region either. Unfortunately these results do not place any strong constraint on the powering mechanism of this Ly$\alpha$ halo; i.e. in the absence of strong radio emission C luminosities are so much fainter than Ly$\alpha$ emission (e.g. typically C/Ly$\alpha$ $\leq$ $0.13$ in Ly$\alpha$ ‘blobs’ where no definitive power source has been determined; (cite: ArrigoniBattaia18)). Although radio continuum has been observed in both the QSO and SMG here, the emission is consistent with a weak AGN or extreme star formation ((cite: YunCarilli02), (cite: Carilli2013)) and not the powerful high-redshift radio galaxies (HzRGs) that are known to exhibit significant extended C ( e.g. (cite: Matsuoka09)).

# Companions in the Field

In this Section, we present new spectra from  of the two known LAEs in addition to LAE 3 discovered in this work. We present measurements of the Ly$\alpha$ flux, velocity width, and rest-frame equivalent width (EW$_0$), and discuss the results below. In addition we investigate the existence of an additional source, dubbed “SRC 6", motivated by an alignment of dust continuum emission and a compact object seen in  imaging. The diversity of object properties (and their staggered discovery) means that the dataset in which each object’s position is defined varies. Where possible, we take the object’s position directly from table 1 of (cite: Carilli2013) (i.e. for the QSO, SMG, LAE 1, and LAE 2). For the QSO, SMG and LAE 2 this is the dust continuum position. For LAE 1 this is the \[C\] position. LAE 3 is defined by its  detection, and the position of SRC 6 is defined as the centre of the dust emission.

## Ly$\alpha$ properties of companions

In Table [\[tab:Lya props\]](#tab:Lya props) we summarise our measurements of Ly$\alpha$ emission from the  cube for each of the objects known in the BR$1202-0725$ field, plus LAE 3, and the potential source ‘SRC 6’. We also include cutout images and spectra in Appendix [6](#App: flux measurements) to demonstrate our choice of aperture size, and the  spectrum from which we measure the Ly$\alpha$ flux (Table [\[tab:Lya props\]](#tab:Lya props) column 5).\
The complexity of the BR$1202-0725$ system and the diffuse Ly$\alpha$ emission in the field make it difficult to identify individual objects’ Ly$\alpha$ in an image, as objects are essentially ‘embedded’ within the diffuse Ly$\alpha$ halo stretching across the entire field. For this reason we choose very narrow velocity ranges over which we display the corresponding Ly$\alpha$ image in the final column of Figure [8](#Fig: Fluxes). We then choose an aperture on these images to encapsulate the emission from a particular object.\
For two objects, LAE 1 and LAE 3, the Ly$\alpha$ flux can be estimated simply by fitting a Gaussian profile to the 1D spectral extraction. For these two objects we also place constraints on the rest-frame equivalent width (EW$_0$) of Ly$\alpha$ from the MUSE spectrum. Accurate measurements of LAEs’ EW$_0$ at this redshift are potentially of great interest due to their ability to distinguish between powering mechanisms of Ly$\alpha$ emission. Models based on standard IMFs, stellar populations and metallicity ranges for instance predict a maximum value of EW$_0 = 240$Å for emission powered by star formation (see (cite: Schaerer2003) and (cite: Hashimoto17)). For LAE 2 it is difficult to produce a good fit from the 1D spectrum, and so we first fix the peak of the Gaussian to the predicted wavelength of Ly$\alpha$ emission corresponding to LAE 2’s systemic redshift. For the remaining objects (the QSO, the SMG, and ‘SRC 6’) we simply sum the flux across a $50$ Å window (i.e. $\approx$ twice the measured FWHM of LAE 1).\
We recover a Ly$\alpha$ flux estimate for LAE 1 of F$_{{\rm{Ly\alpha}}}$ = $1.54\,\pm$ 0.05E-16 erg s$^{-1}$ cm$^{-2}$ over an aperture of diameter $1.5$ $''$. This flux measurement and its associated velocity width and EW$_0$ can be compared to literature values from long-slit spectroscopy presented in (cite: Williams14). Our flux measurement for LAE 1 is actually somewhat smaller than the literature result (F$_{{\rm{Ly\alpha}}}$ = $2.53 \pm$0.08 × 10^−16^ erg s$^{-1}$ cm$^{-2}$), possibly due to the halo contaminating the end of the long slit[^7] but we find a large velocity width of  =$1149\pm45$ km s$^{-1}$, almost consistent with the literature value ( =$1381\pm124$ km s$^{-1}$). We also measure the equivalent width, and find EW$_0$(Ly$\alpha$)$= 72.9\pm 2.2$ Å. This is a fairly large EW$_0$, although smaller than the published estimate (EW$_0 = 103\,\pm\,15$ Å) from long-slit spectroscopy. The difference is possibly explained by factors such as contamination of the long slit by light from the QSO (which would boost the measured Ly$\alpha$ flux and hence the EW$_0$). Even so, our flux estimate may be subject to overestimating the Ly$\alpha$ originating within LAE 1 as we too observe the object through the QSO’s Ly$\alpha$ halo, and fit a 1D Gaussian fit to this line. Conversely however, factors such as underestimating the true extent on-sky of LAE 1 and the inaccuracy of a Gaussian fit may result in our missing some flux.

LAE 2 has a low Ly$\alpha$ flux with emission that appears diffuse on-sky, and with a large velocity width. Taking an aperture of 1.5 $''$ in diameter driven by the object’s appearance in HST imaging, we measure a flux of F$_{{\rm{Ly\alpha}}}$ = $0.54\,\pm$ 0.05 × 10^−16^ erg s$^{-1}$ cm$^{-2}$, and a velocity width of  = $2480\,\pm275$ km s$^{-1}$. The numbers we derive are similar to previous results ((cite: Williams14) measure a flux of F$_{{\rm{Ly\alpha}}}$ = $0.33\,\pm$ 0.06 × 10^−16^ erg s$^{-1}$ cm$^{-2}$, a velocity width of  =$1225\pm257$ km s$^{-1}$, and an EW of EW$_0$ = $67\pm15$ Å).\
In the vicinity of the SMG we measure faint Ly$\alpha$ emission, but are unable to force a fit to this line in order to measure a flux, velocity width, or EW$_0$. Summing the flux over 50 Å (for consistency with LAE 1), in an aperture of diameter 1.5 $''$, we measure a low-level of Ly$\alpha$ emission at F$_{{\rm{Ly\alpha}}}$ = $0.04\,\pm$ 0.01 × 10^−16^ erg s$^{-1}$ cm$^{-2}$.\
Next we measure a Ly$\alpha$ flux and line properties for the newly discovered source LAE 3. We find a flux of F$_{{\rm{Ly\alpha}}}$ = $0.24\,\pm$ 0.03 × 10^−16^ erg s$^{-1}$ cm$^{-2}$ over a diameter of 1.5 $''$. The velocity width measures  = $471\pm62$ km s$^{-1}$, significantly narrower than LAE 1, or indeed any of the other objects in the system. We do not see continuum emission from LAE 3 in the  data, therefore we place a lower limit on EW$_0$ of LAE 3. To do so, we use the RMS of an image of $\Delta\lambda = 700$ Å, redward of the emission line, to place an upper limit on the continuum, and in combination with the flux measurement, derive a $5\,\sigma$ upper limit of EW$_0$(Ly$\alpha_{\,5\sigma}^{\,lim})\,\geq\,34.05$ Å.\
The final object for which we measure a Ly$\alpha$ flux is “SRC 6". Motivated by an alignment of dust continuum emission and a compact object seen in , we extracted a spectrum at the  position to search for Ly$\alpha$ emission. We see no evidence for significant Ly$\alpha$ emission originating from the object seen in HST imaging, although a marginal detection is seen $\sim0.2\,\ensuremath{''}$ South. We report in Table [\[tab:Lya props\]](#tab:Lya props) the flux seen in a $1$ $''$ aperture at this position, and the redshift if the corresponding tentative detection in the  cube is \[C\] emission.

![image](figures/QSO_ugly.png) ![image](figures/LAE1_ugly.png) ![image](figures/LAE2_ugly.png) ![image](figures/SMG_ugly.png)

![image](figures/LAE3_ugly.png) ![image](figures/LAE4_ugly.png)

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|---:|
| **Object** | **Position** | **$z$$_{{\rm{best}}}$** | **$\lambda_{{\rm{Obs\,Ly\alpha}}}$** | **F$_{{\rm{Ly\alpha}}}$ ($10^{-16}$)** | $_{{\rm{Ly\alpha}}}$ | **EW$_{0\,{\rm{Ly}}\alpha}$**[^8] | **SFR$_{\rm{Ly\alpha}}$** |  |
|  | \[J2000\] |  | \[Å\] | \[erg s$^{-1}$ cm$^{-2}$\] | \[km s$^{-1}$\] | \[Å\] | \[M$_{\odot}$ yr$^{-1}$\] |  |
| **QSO** | J120523.13-074232.6 | 4.6942[^9] | No peak | $13.9\pm 0.18$ [^10] | $-$ | $-$ | $296.0\pm4.0$ |  |
| **SMG** | J120522.98-074229.5 | 4.6915 | 6941.86 | 0.12$\pm$0.02 | $-$ | $-$ | $-$ |  |
| **LAE 1** | J120523.06-074231.2 | 4.6950 | 6932.25 | 1.54$\pm$0.05 | 1149$\pm$45 | $72.9\pm 2.2$ | 32.9$\pm$3.3 |  |
| **LAE 2** | J120523.04-074234.3 | 4.7055 | 6936.00 (fix) | 0.54$\pm$0.05 | 2480$\pm$275 | $-$ | $-$ |  |
| **LAE 3** | J120523.19-074227.7 | 4.7019[^11] | 6931.65 | 0.24$\pm$0.03 | 471$\pm$62 | $\geq 34.05$$_{\,5\sigma}^{\,lim}$ | 5.0$\pm$0.5 |  |
| **SRC 6** | J120523.46-074232.1 | 4.7035 | 6932.44 (fix) | 0.03$\pm$0.01 | $-$ | $-$ | $-$ |  |

## Nature of companions

In combination with our measurements of Ly$\alpha$ emission from the sources in this field, we use existing  data to compare the Ly$\alpha$ and \[C\] images and spectra, together with high-resolution optical  images, and our dust-continuum map from . We evaluate the most likely physical scenarios leading to each object’s appearance in these datasets based on Figure [7](#Fig: nature of objs), also taking note of the channel maps shown in Appendix [7](#App:channel maps). In each row of Figure [7](#Fig: nature of objs) we show a single object. In the left-hand panel, we show an  image representative of the optical stellar light, overlaid with Ly$\alpha$ contours extracted from the MUSE cube at the redshift of the object. These cutouts demonstrate the extended nature of Ly$\alpha$ emission compared to our previous best impression of the objects’ optical sizes. In the central panel we show a dust-continuum map, overlaid with contours depicting \[C\] emission at each object’s peak velocity. Finally in the right-hand panels we show the Ly$\alpha$ and \[C\] spectra in velocity space, relative to the systemic redshift of the QSO.

Interestingly, for those objects with \[C\] emission (and hence a systemic redshift), it is not evident that Ly$\alpha$ emission is always present at the same velocity, or even at the objects’ positions on-sky at all. Likewise, the brightest objects shining in Ly$\alpha$ do not always correspond to a detection in \[C\].

### QSO

The QSO’s continuum and PSF-subtracted spectrum were shown in Figure [3](#Fig: Blob Spec), and we discussed the flux measurement in Section [3.1](#sect:totflux). No distinct ‘peak’ is seen at the predicted wavelength of Ly$\alpha$, but copious amounts of emission remain across a broad range of velocities. As seen in Figure [3](#Fig: Blob Spec), when the emission greater than 1E-17 erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$ is summed, the line profile becomes more centrally concentrated in wavelength. The most striking feature of this spectrum is the distinct absorption feature seen at $\approx6912$ Å. The absorption saturates indicating a high column density of HI gas approximately $400$ km s$^{-1}$ from the QSO. This kind of signature has sometimes been interpreted in the literature as an expanding shell of neutral gas surrounding a QSO (e.g. (cite: vanojik97), (cite: Binette00)).

### SMG

In the literature, optical emission from the SMG has evaded detection. As described above, in the MUSE datacube we place an aperture at the position of the SMG and are able to measure Ly$\alpha$ emission which would be equivalent to an instantaneous SFR$_{\rm{Ly\alpha}}$ $\approx2$ M$_{\odot}$ yr$^{-1}$. The line profile however is remarkably similar to the QSO’s Ly$\alpha$ halo, and indeed no source is visible by eye in the Ly$\alpha$ channel maps at the position of SMG. We conclude that the Ly$\alpha$ line detected at this position arises from the edge of the QSO’s extended Ly$\alpha$ halo, and so we choose not to report a Ly$\alpha$ velocity width, EW$_0$ or SFR for the SMG in Table [\[tab:Lya props\]](#tab:Lya props). The channel maps in Appendix [7](#App:channel maps) present interesting features in the Ly$\alpha$ emission in the vicinity of the SMG. In particular, multiple channels spanning a few hundred km s$^{-1}$ display very low surface brightness emission elongated west of the SMG.

### LAE 1

LAE 1 is well-studied, and the measurements we report here are broadly consistent with literature results. As already noted by other studies, including (cite: Williams14), the EW$_0$(Ly$\alpha$) is high, although it is consistent with being powered by star formation. In addition (cite: Williams14) argue that since no C or He emission is detected in this source, there can be at most a 10% contribution to LAE 1’s Ly$\alpha$ flux from AGN-powered photoionisation. So in conclusion there may be multiple powering mechanisms at work for the Ly$\alpha$ emission falling into the aperture. (A) Some star formation occurring within LAE 1, (B) perhaps up to a $10$% contribution from an AGN, and (C) the Ly$\alpha$ halo extending from the QSO, within which LAE 1 is embedded. Previous measurements of the SFR using various techniques reported values for LAE 1 in the range SFR$_{\rm{UV}}$$=13$M${_\odot}$ yr$^{-1}$ (cite: Ohyama2004), to SFR$_{\rm{[C{\sc{ii}]}}}$$=19$M${_\odot}$ yr$^{-1}$ (cite: Williams14). Transforming our Ly$\alpha$ flux to a star formation rate we find an SFR$_{\rm{Ly\alpha}}\approx32\pm3$ M$_{\odot}$ yr$^{-1}$. We also note that the Ly$\alpha$ line profile is symmetric, which is not always typical of LAEs at high redshift due to the very low neutral fraction ($10^{-4}$) required to absorb all photons blue-ward of 1215.67 Å, often leading to an asymmetric line (e.g. (cite: Fan2001a)). (cite: Williams14) were the first to infer that the symmetric profile of LAE 1 places a constraint on the size of the ionised bubble surrounding QSO BR$1202-0725$, and we concur with this conclusion. Finally we note that the absorption feature visible clearly in the spectrum of the QSO at $\approx\,6912$ Å is also seen in the spectrum of LAE 1, requiring that photons from the LAE as well as the QSO (some $15$ pkpc apart) encounter the same barrier of neutral gas.

The peak of the Ly$\alpha$ emission from LAE 1 falls at 6932 Å, offset in velocity by $\sim$397 km s$^{-1}$ from the predicted position according to the peak of \[C\] in LAE 1. Note this is greater than the previously reported value in the literature due to our velocity frame correction (Section [2.2.2](#sect:obs-ALMA cii)). Upon close inspection of the channel maps shown in Appendix [7](#App:channel maps), it is interesting to note that the \[C\] coordinate reported for LAE 1 (most apparent in the channel at 23.93 km s$^{-1}$ is offset by $\approx 0.6$ $''$, although the aperture within which we extract spectra and measure flux contains both peaks. Furthermore, the purported \[C\] “bridge" of emission between the QSO and the SMG, appears to ‘swirl’ around the position of LAE 1– appearing for instance both to the East and to the West of the Ly$\alpha$ peak of LAE 1 at velocities either side of the peak. Assuming that both the \[C\] and Ly$\alpha$ emission originate from the source known as LAE 1, this could be indicative for example of tidal disruption of LAE 1’s ISM during a merger between itself, the SMG, and the QSO. Regardless, we conclude that LAE 1 is indeed likely to be a star-forming LAE associated with this group of merging galaxies, and embedded within the extended Ly$\alpha$ halo of the QSO, possibly shielded by an expanding ‘shell’ of optically thick gas giving rise to the absorption feature.

### LAE 2

As we reported in section [4.1](#sect: Lya props), the Ly$\alpha$ line that we measure is broad, and offset in velocity from the \[C\] line at the position of LAE 2. Until now this has not presented difficulty for the physical interpretation of Ly$\alpha$ emission in the vicinity of LAE 2. Taking advantage of the simultaneous spectral and spatial coverage of  however, we see that the Ly$\alpha$ emission line profile is remarkably similar to that from the QSO’s halo. Furthermore, although LAE 2 appears distinct in  imaging, stepping through channels of the MUSE cube, no particular layer shows spatially-peaked Ly$\alpha$ emission relative to the diffuse emission across the field. Specifically, we check the predicted wavelength of Ly$\alpha$ from LAE 2’s \[C\] emission, but in addition extend the search outward to both positive and negative velocities. No spectral region suggests the presence of an object in the MUSE datacube. This implies that perhaps the emission seen in  is stellar continuum, which is outshone by diffuse Ly$\alpha$ in the BR$1202-0725$ halo in the  cube. Indeed, we see in the channel maps that diffuse Ly$\alpha$ emission appears to extend towards the position of LAE 2 in the velocity channels preceding LAE 2 – we speculate that LAE 2 is perhaps passing through the QSO’s Ly$\alpha$ halo, with a peculiar velocity directly away from the observer. From the information added here from , we conclude that the object often referred to in the literature as ‘LAE 2’ is in fact not responsible for powering the Ly$\alpha$ emission seen at this position in previous datasets, and this Ly$\alpha$ line is entirely consistent with being part of the extended halo surrounding QSO BR$1202-0725$. We do once again see the absorption feature at 6912Å, indicating that this position on sky is also covered by the absorbing gas.

### LAE 3

The newly discovered LAE 3 shows a bright Ly$\alpha$ line peaking at 6931Å, placing the LAE at a redshift of $z_{Ly\alpha} = 4.7019$. We measure properties for LAE 3 more consistent with typical LAEs at high redshift e.g. (cite: Drake2017a), (cite: Drake2017b), (cite: Hashimoto17), (cite: Wisotzki16), (cite: Leclercq2017). The measured flux for LAE 3 translates to an SFR = 5$\pm$0.5 M${_\odot}$ yr$^{-1}$. We place a lower limit on the EW$_0$ of LAE 3 of EW$_0$(Ly$\alpha_{\,5\sigma}^{\,lim})\,\geq\,34.05$ Å. This is consistent with in-situ star formation as the primary power source of the Ly$\alpha$ line, although we cannot rule out contributions from an AGN, or perhaps the edge of the QSO’s halo also.

No \[C\] or dust continuum emission is detected at the position of LAE 3. This is not altogether surprising, given the young ages and low metallicities typical of the high-redshift LAE population. Therefore LAE 3 is most likely to be a star-forming LAE at the redshift of the QSO. Interestingly, the profile of the Ly$\alpha$ line appears symmetric just as in LAE 1. Following the arguments in (cite: Williams14), we here propose that the symmetric profile of LAE 3 indicates a new lower limit on the radius of the HII sphere/proximity zone of QSO BR$1202-0725$, at some $\sim 30$ pkpc away (also see (cite: Bosman19) for a discussion on proximate LAEs at high redshift). Finally, the coherent absorption feature seen in the spectra of the other objects is at a bluer wavelength than the edge of this narrow Ly$\alpha$ line, and as such we cannot say if the proposed absorbing shell extends to the position of LAE 3.\

### SRC 6

The teamSRC 6 is detected primarily in the dust continuum. In addition, we see tentative \[C\] emission coincident with part of the area of dust emission, and an even less convincing Ly$\alpha$ detection. If the \[C\] detection is real, this places the object at $z = 4.7025$. It is notable also, that low-surface-brightness Ly$\alpha$ emission in this region could once again be part of the QSO’s Ly$\alpha$ halo, appearing coincident with an unrelated object along the line of sight.

# Summary

We have presented new optical IFU data from  across the BR$1202-0725$ field, which is one of the most overdense regions of the early Universe known at $z=4.69$. BR$1202-0725$ is clearly a very extreme system, undergoing a major merger and demonstrating drastic tidal disruption of the smaller galaxies in the vicinity. Prior to this work BR$1202-0725$ was already one of the most studied single-targets at high redshift, acting as a laboratory for the study of diverse galaxies typically detected via different selection techniques, all evolving in the same environment. Here, we examine the Ly$\alpha$ halo surrounding QSO BR$1202-0725$ and measure Ly$\alpha$ properties for companions in the field, including a new LAE discovered in this work. In conjunction with existing  observations we examine and compare the neutral and ionised gas content of the BR$1202-0725$ system’s Ly$\alpha$ halo and constituent objects, which provides us with the best view to date of the physical processes under way in BR$1202-0725$ until new facilities (e.g. JWST and the GTO programme) become available. Our main findings can be summarised as follows:

- QSO BR$1202-0725$ exhibits a large Ly$\alpha$ halo, stretching across at least $\sim$ 8 $''$ on-sky ($\approx 55$ pkpc at $z=4.6942$) at surface brightness levels greater than 1E-17 erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$.

- In contrast, no Ly$\alpha$ halo is detected around the SMG, which has a similar gas mass and SFR as the QSO.

- We do not find evidence for extended C emission surrounding the QSO down to a surface brightness limit of SB $\approx$ 0.19E-16 erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$ in a square arcsecond, and hence can not place any constraint on the dominant powering mechanism of the Ly$\alpha$ halo.

- The optical NW-companion of QSO BR$1202-0725$ known as “LAE 1" appears to be a Ly$\alpha$-emitting galaxy embedded within the larger region of diffuse Ly$\alpha$ emission. Taking an aperture of 2 $''$ in diameter we measure a Ly$\alpha$ flux, velocity width consistent with literature measurements from long-slit spectra. We measure an EW$_0$(Ly$\alpha$)$= 72.9\pm 2.2$ Å, this is probably due to a combination of powering mechanisms for the Ly$\alpha$.

- The optical SW-companion of QSO BR$1202-0725$, confirmed in \[C\] and \[N\] emission, known as “LAE 2" is not necessarily responsible for the Ly$\alpha$ emission previously reported at this position. Although we detect a Ly$\alpha$ line, it appears diffuse on-sky, with no local maximum coinciding with the position of LAE 2. The Ly$\alpha$ line profile, peak, and FWHM are also more consistent with being part of the QSO’s diffuse halo.

- We detect an additional LAE in the BR$1202-0725$ system $\sim5$ $''$ to the north of the QSO, and denote it “LAE 3". The object was discovered serendipitously in the  datacube, and exhibits a bright but narrow Ly$\alpha$ line of flux $0.24$ $\pm$ $\num{0.03E-16}$ erg s$^{-1}$ cm$^{-2}$ (1.5 $''$), a velocity width of 471.23 km s$^{-1}$ and EW$_0$(Ly$\alpha_{\,5\sigma}^{\,lim})\,\geq\,34.05$ Å. This LAE is more aligned with typical properties of Ly$\alpha$ emitters at high redshift, with Ly$\alpha$ emission consistent with powering by star formation.

- The symmetric profile of Ly$\alpha$ in LAE 3 places a new constraint on the size of the HII bubble surrounding QSO BR$1202-0725$ of $\approx\,60$ pkpc in diameter.

- We see coherent absorption, possibly indicative of an expanding shell of HI gas, 400 km s$^{-1}$ infront of BR$1202-0725$ across at least 4 $''$ on-sky, corresponding to $\sim$24 pkpc (diameter). The feature is blue-ward of the edge of Ly$\alpha$ from LAE 3 and hence we cannot confirm whether LAE 3 is covered by the HI gas.

These results demonstrate the efficiency of  for detecting low-surface-brightness Ly$\alpha$ emission in addition to the instrument’s use as a ‘redshift machine’ for the detection of emission-line galaxies. Futhermore, the combined power of  and  to examine both ionised- and cool gas components offers unprecedented insights on the nature of a diverse population of objects at high redshift. This work also highlights the need for follow-up of Ly$\alpha$ halos with future facilities (such as JWST) with a view to unambiguously detecting/ruling out the presence of e.g. metal lines, to finally disentangle the processes powering these giant structures.

# Acknowledgments

ABD, FW, MN and MN acknowledge support from the ERC Advanced Grant 740246 (Cosmic Gas).\
This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00006.SV, 2013.1.00039.S, .00259.S, 2013.1.00745.S, 2015.1.00388.S, .01489.S, 2017.1.00963.S, 2017.1.01516.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.\

# Software

Astropy (cite: 2013A&A...558A..33A); CASA (cite: mcmullin07), MUSE data reduction pipeline (cite: Weilbacher12), (cite: Weilbacher14), ZAP (cite: Soto2016), MPDAF (cite: Piqueras17).

# Appendix A

We include here in Figure [8](#Fig: Fluxes) the spectra and images from which we measure the Ly$\alpha$ properties of each source. In the left-hand panels we show a cutout of the object in the high-resolution  image, in the central panels we show a spectrum extracted from the  cube within the aperture shown on the  image, and in the right-hand panels we show a cutout image extracted from the  cube across the wavelength range shaded in orange on the spectrum. Apertures are centred on the \[C\] positions reported in (cite: Carilli2013) where possible, otherwise the peak of the Ly$\alpha$ emission seen in  is taken. For the objects where no 1D Gaussian fit could be performed, we shade in red the region of the spectrum which is summed to estimate the Ly$\alpha$ flux.

![image](figures/SMG.png) ![image](figures/LAE1.png) ![image](figures/LAE2.png)

![image](figures/LAE3.png) ![image](figures/LAE4.png)

# Appendix B

This appendix contains the  and  channel maps depicting the extended Ly$\alpha$ and \[C\] emission at a series of velocities relative to the QSO’s systemic redshift in Figure [9](#Fig: channel maps).

![](figures/WTF_j_start18_j_end27_vel_vel.png)

![](figures/WTF_j_start27_j_end36_vel_vel.png)

![](figures/WTF_j_start36_j_end45_vel_vel.png)

![](figures/WTF_j_start45_j_end54_vel_vel.png)

![image](figures/WTF_j_start54_j_end63_vel_vel.png)

# Appendix C

This appendix demonstrates our search for extended C emission surrounding QSO BR$1202-0725$ discussed in Section [3.4](#sect:powering).

![image](figures/BR1202m07_selsing.png) ![image](figures/BR1202m07_no_CIV.png)

(ref: ArrigoniBattaia15b) Arrigoni Battaia, F., Hennawi, J. F., Prochaska, J. X., & Cantalupo, S. 2015, ApJ, 809, 163

(ref: ArrigoniBattaia2018) Arrigoni Battaia, F., Hennawi, J. F., Prochaska, J. X., et al. 2019, MNRAS, 482, 3162

(ref: ArrigoniBattaia15a) Arrigoni Battaia, F., Yang, Y., Hennawi, J. F., et al. 2015, ApJ, 804, 26

(ref: ArrigoniBattaia18) Arrigoni Battaia, F., Chen, C.-C., Fumagalli, M., et al. 2018, A&A, 620, A202

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Bacon2010) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Proceedings of the SPIE, Volume 7735, id. 773508 (2010)., ed. I. S. McLean, S. K. Ramsay, & H. Takami, Vol. 7735, 773508

(ref: Bacon2015) Bacon, R., Brinchmann, J., Richard, J., et al. 2015, A&A, 575, A75

(ref: Bacon2017) Bacon, R., Conseil, S., Mary, D., et al. 2017, A&A, 608, A1

(ref: Binette00) Binette, L., Kurk, J. D., Villar-Martı́n, M., & Röttgering, H. J. A. 2000, A&A, 356, 23

(ref: Borisova2016) Borisova, E., Cantalupo, S., Lilly, S. J., et al. 2016, arXiv:1605.01422

(ref: Bosman19) Bosman, S. E. I., Kakiichi, K., Meyer, R. A., et al. 2019, arXiv e-prints, arXiv:1912.11486

(ref: Cai19) Cai, Z., Cantalupo, S., Prochaska, J. X., et al. 2019, ApJS, 245, 23

(ref: Cantalupo10) Cantalupo, S. 2010, MNRAS, 403, L16

(ref: Carilli2013) Carilli, C. L., Riechers, D., Walter, F., et al. 2013, ApJ, 763, 120

(ref: Carniani2013) Carniani, S., Marconi, A., Biggs, A., et al. 2013, A&A, 559, A29

(ref: Daddi20) Daddi, E., Valentino, F., Rich, R. M., et al. 2020, arXiv e-prints, arXiv:2006.11089

(ref: Decarli2018) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature Publishing Group, 545, doi:10.1038/nature22358

(ref: Drake2019) Drake, A. B., Farina, E. P., Neeleman, M., et al. 2019, ApJ, 881, 131

(ref: Drake2017a) Drake, A. B., Guiderdoni, B., Blaizot, J., et al. 2017, Monthly Notices of the Royal Astronomical Society, 471, 267

(ref: Drake2017b) Drake, A. B., Garel, T., Wisotzki, L., et al. 2017, Astronomy & Astrophysics, 608, A6

(ref: Fan2001a) Fan, X., Narayanan, V. K., Lupton, R. H., et al. 2001, The Astronomical Journal, 122, 2833

(ref: Farina2017) Farina, E. P., Venemans, B. P., Decarli, R., et al. 2017, The Astrophysical Journal, 848, 78

(ref: Farina19) Farina, E. P., Arrigoni-Battaia, F., Costa, T., et al. 2019, ApJ, 887, 196

(ref: Ginolfi2018) Ginolfi, M., Maiolino, R., Carniani, S., et al. 2018, Monthly Notices of the Royal Astronomical Society, 476, 2421

(ref: Hashimoto17) Hashimoto, T., Garel, T., Guiderdoni, B., et al. 2017, A&A, 608, A10

(ref: Hu1996) Hu, E. M., McMahon, R. G., & Egami, E. 1996, ApJL, 459, L53

(ref: Hu97) Hu, E. M., McMahon, R. G., & Egami, E. 1997, in The Hubble Space Telescope and the High Redshift Universe, ed. N. R. Tanvir, A. Aragon-Salamanca, & J. V. Wall, 91

(ref: Inami2017) Inami, H., Bacon, R., Brinchmann, J., et al. 2017, A&A, 608, A2

(ref: Iono2006) Iono, D., Yun, M. S., Elvis, M., et al. 2006, ApJL, 645, L97

(ref: IrwinMcMahonHazard1991) Irwin, M., McMahon, R. G., & Hazard, C. 1991, in Astronomical Society of the Pacific Conference Series, Vol. 21, The Space Distribution of Quasars, ed. D. Crampton, 117–126

(ref: Isaak1994) Isaak, K. G., McMahon, R. G., Hills, R. E., & Withington, S. 1994, MNRAS, 269, L28

(ref: Leclercq2017) Leclercq, F., Bacon, R., Wisotzki, L., et al. 2017, Astronomy & Astrophysics, 608, A8

(ref: Lee19) Lee, M. M., Nagao, T., De Breuck, C., et al. 2019, ApJL, 883, L29

(ref: Lehnert20) Lehnert, M. D., Yang, C., Emonts, B. H. C., et al. 2020, arXiv e-prints, arXiv:2004.04176

(ref: Marino2019) Marino, R. A., Cantalupo, S., Pezzulli, G., et al. 2019, ApJ, 880, 47

(ref: Matsuoka09) Matsuoka, K., Nagao, T., Maiolino, R., Marconi, A., & Taniguchi, Y. 2009, A&A, 503, 721

(ref: McMahon94) McMahon, R. G., Omont, A., Bergeron, J., Kreysa, E., & Haslam, C. G. T. 1994, MNRAS, 267, L9

(ref: mcmullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Michel-Dansac20) Michel-Dansac, L., Blaizot, J., Garel, T., et al. 2020, A&A, 635, A154

(ref: Ohta96) Ohta, K., Yamada, T., Nakanishi, K., et al. 1996, Nature, 382, 426

(ref: Ohyama2004) Ohyama, Y., Taniguchi, Y., & Shioya, Y. 2004, AJ, 128, 2704

(ref: Omont1996) Omont, A., McMahon, R. G., Cox, P., et al. 1996, A&A, 315, 1

(ref: Omont96) Omont, A., Petitjean, P., Guilloteau, S., et al. 1996, Nature, 382, 428

(ref: ouchi03) Ouchi, M., Shimasaku, K., Furusawa, H., et al. 2003, ApJ, 582, 60

(ref: Overzier09) Overzier, R. A., Guo, Q., Kauffmann, G., et al. 2009, MNRAS, 394, 577

(ref: Pavesi16) Pavesi, R., Riechers, D. A., Capak, P. L., et al. 2016, ApJ, 832, 151

(ref: Petitjean96) Petitjean, P., Pécontal, E., Valls-Gabaud, D., & Chariot, S. 1996, Nature, 380, 411

(ref: Piqueras17) Piqueras, L., Conseil, S., Shepherd, M., et al. 2017, arXiv e-prints, arXiv:1710.03554

(ref: Prescott15) Prescott, M. K. M., Momcheva, I., Brammer, G. B., Fynbo, J. P. U., & Møller, P. 2015, ApJ, 802, 32

(ref: rau11) Rau, U., & Cornwell, T. J. 2011, A&A, 532, A71

(ref: Riechers06) Riechers, D. A., Walter, F., Carilli, C. L., et al. 2006, ApJ, 650, 604

(ref: Rosdahl12) Rosdahl, J., & Blaizot, J. 2012, MNRAS, 423, 344

(ref: Salome2012) Salomé, P., Guélin, M., Downes, D., et al. 2012, A&A, 545, A57

(ref: Schaerer2003) Schaerer, D. 2003, A&A, 397, 527

(ref: Selsing16) Selsing, J., Fynbo, J. P. U., Christensen, L., & Krogager, J. K. 2016, A&A, 585, A87

(ref: Smith07) Smith, D. J. B., & Jarvis, M. J. 2007, MNRAS, 378, L49

(ref: Soto2016) Soto, K. T., Lilly, S. J., Bacon, R., Richard, J., & Conseil, S. 2016, Monthly Notices of the Royal Astronomical Society, 458, 3210

(ref: springel06) Springel, V., Frenk, C. S., & White, S. D. M. 2006, Nature, 440, 1137

(ref: Taniguchi01) Taniguchi, Y., Shioya, Y., & Kakazu, Y. 2001, ApJL, 562, L15

(ref: vandevoort11) van de Voort, F., Schaye, J., Booth, C. M., Haas, M. R., & Dalla Vecchia, C. 2011, MNRAS, 414, 2458

(ref: vanojik97) van Ojik, R., Roettgering, H. J. A., Miley, G. K., & Hunstead, R. W. 1997, A&A, 317, 358

(ref: Venemans07) Venemans, B. P., Röttgering, H. J. A., Miley, G. K., et al. 2007, A&A, 461, 823

(ref: Wagg2012) Wagg, J., Wiklind, T., Carilli, C. L., et al. 2012, ApJL, 752, L30

(ref: Weilbacher12) Weilbacher, P. M., Streicher, O., Urrutia, T., et al. 2012, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 8451, Design and capabilities of the MUSE data reduction software and pipeline, 84510B

(ref: Weilbacher14) —. 2014, Astronomical Society of the Pacific Conference Series, Vol. 485, The MUSE Data Reduction Pipeline: Status after Preliminary Acceptance Europe, ed. N. Manset & P. Forshay, 451

(ref: Williams14) Williams, R. J., Wagg, J., Maiolino, R., et al. 2014, MNRAS, 439, 2096

(ref: Wisotzki16) Wisotzki, L., Bacon, R., Blaizot, J., et al. 2016, A&A, 587, A98

(ref: WootenThompson09) Wootten, A., & Thompson, A. R. 2009, IEEE Proceedings, 97, 1463

(ref: YunCarilli02) Yun, M. S., & Carilli, C. L. 2002, ApJ, 568, 88

[^1]: Although C could be suppressed in a low metallicity system, He should be detectable regardless, and thus places a strong constraint on the powering mechanism of the Ly$\alpha$ emission.

[^2]: Few band 6 setups partially overlap.

[^3]: CASA version 5.4.0-70

[^4]: We have checked that re-weighing of combined visibilities using the STATWT task in CASA does not further improve the map quality.

[^5]: (cite: Carilli2013), formal errors from Gaussian fitting on the redshifts are each \<0.0003.

[^6]: Object’s velocity offset from the QSO, where negative numbers represent a blue-shift, and positive numbers a red-shift.

[^7]: See figure 1 in (cite: Williams14) for their slit placement.

[^8]: EW$_0$ = (F$_{{\rm{Ly\alpha}}}$/F$_{{\rm{cont}}}$) $\times$ ($1$/($1$ + z$_{{\rm{best}}}$)).

[^9]:  z$_{\rm{[CII]}}$

[^10]: For the QSO halo we report the flux summed within the SB $>10^{-17}$ erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$ contour across the entire field. Both the residuals from PSF subtraction, and the position of LAE 1 are masked.

[^11]:  z$_{{\rm{Lya}}}$

</paper>

Write the methods card for this paper.