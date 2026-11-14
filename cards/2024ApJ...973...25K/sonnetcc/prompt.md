# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...973...25K\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...973...25K",
 "title": "Birds of a Feather: Resolving Stellar Mass Assembly with JWST/NIRCam in a Pair of Kindred z ∼ 2 Dusty Star-forming Galaxies Lensed by the PLCK G165.7+67.0 Cluster",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Kamieneski, Patrick S.",
 "n_authors": 41,
 "arxiv_id": "2404.08058",
 "doi": "10.3847/1538-4357/ad5d59",
 "alma_projects_linked_by_archive": [
  "2021.1.00607.S"
 ]
}
```

Paper text:
<paper>
# Birds of a Feather: Resolving Stellar Mass Assembly With JWST/NIRCam in a Pair of Kindred $\boldsymbol{z\sim 2}$ Dusty Star-forming Galaxies Lensed by the PLCK G165.7+67.0 Cluster

## Abstract

We present a new parametric lens model for the G165.7+67.0 galaxy cluster,

which was discovered with *Planck* through its bright submillimeter flux, originating from a pair of extraordinary dusty star-forming galaxies (DSFGs) at $z\approx 2.2$.

Using JWST and interferometric mm/radio observations, we characterize the intrinsic physical properties of

the DSFGs, which are separated by only $\sim 1\ensuremath{''}$ (8 kpc) and a velocity difference $\Delta V \lesssim 600~{\rm km}~{\rm s}^{-1}$ in the source plane,

and thus likely

undergoing a major merger.

Boasting intrinsic star formation rates ${\rm SFR}_{\rm IR} = 320 \pm 70$ and $400 \pm 80~ M_\odot~{\rm yr}^{-1}$, stellar masses ${\rm log}[M_\star/M_\odot] = 10.2 \pm 0.1$ and $10.3 \pm 0.1$, and dust attenuations $A_V = 1.5 \pm 0.3$ and $1.2 \pm 0.3$, they are remarkably similar objects.

We perform spatially-resolved pixel-by-pixel SED fitting using rest-frame near-UV to near-IR imaging from JWST/NIRCam,

resolving some stellar structures down to 100 pc scales.

Based on their resolved specific SFRs and $UVJ$ colors, both DSFGs are experiencing significant galaxy-scale star formation events.

If they are indeed interacting gravitationally, this strong starburst could be the hallmark of gas that has been disrupted by an initial close passage.

In contrast, the host galaxy of the recently discovered triply-imaged SN H0pe has a much lower SFR than the DSFGs, and we present evidence for the onset of inside-out quenching and large column densities of dust even in regions of low specific SFR.

Based on the intrinsic SFRs of the DSFGs inferred from UV through FIR SED modeling,

this pair of objects alone is predicted to yield an observable $1.1 \pm 0.2~{\rm CCSNe~yr}^{-1}$,

making this cluster field ripe for continued monitoring.

# Introduction

Out to at least $z \sim 3$, the fraction of obscured star formation in galaxies appears to increase nearly monotonically with increasing stellar mass (cite: Bourne:2017aa; Whitaker:2017aa; McLure:2018aa), a relation that has also been recovered by simulations at $z\lesssim 2$ (e.g., (cite: Zimmerman:2024aa)).

Recent results from the Atacama Large Millimeter/submillimeter Array (ALMA) have suggested even the presence of a population of galaxies that are both massive and dust-rich as early as $z \approx 7$ (cite: Algera:2024aa).

The dust-obscured mode of star formation has been found to dominate the cosmic star formation rate density (SFRD) for 12 billion years, to at least $z\sim 4$ (e.g., (cite: Bouwens:2020aa; Zavala:2021aa)).

(cite: Long:2023ab) predicted that, at the peak of the Universe’s star formation history at $z\sim 2$ (“Cosmic Noon"), $25 - 60 \%$ of the stellar mass density of the Universe may be contributed by dusty star-forming galaxies[^1] (DSFGs) and their quiescent descendants.

Together, this implies that our understanding of the growth and evolution of stellar mass in the Universe from rest-frame UV/optical studies alone would be horribly incomplete.

Conversely, our knowledge of the typical stellar masses and properties of older, extant stellar populations of DSFGs is still woefully lacking, due in large part to intense dust attenuation at crucial rest-frame UV/optical wavelengths. Now, the sensitivity and resolution of JWST in this regime is beginning to facilitate novel interpretations of this frequently perplexing populationoften also referred to as submillimeter galaxies (SMGs; (cite: Blain:2002aa)), although these may more accurately be said to comprise a subset of DSFGs (cite: Casey:2014aa).

They are widely believed to be the progenitors of massive quiescent, early-type galaxies seen at lower redshifts (cite: Lilly:1999aa; Farrah:2006aa; Toft:2014aa), and given their association with galaxy overdensities and protoclusters (cite: Geach:2006aa; Chapman:2009aa; Clements:2014aa; Dannerbauer:2014aa; Casey:2015aa; Umehata:2015aa; Casey:2016aa; Clements:2016aa; Hung:2016aa; Miller:2018ab; Long:2020aa; Caputi:2021aa; Calvi:2023ab), it is presumed that many will evolve into the ultra-massive population of brightest cluster galaxies (BCGs).

DSFGs at Cosmic Noon are typically considered to be dominated by compact nuclear starburst events, occurring within a thick shroud of dust. These have been postulated to signal the inside-out growth of galactic bulges that will persist in the massive descendents (e.g., (cite: Gullberg:2019aa; Nelson:2019aa)). This activity may be driven by major mergers (cite: Hopkins:2008aa), or more secularly through *in situ* star formation in gravitationally-unstable, gas-rich disks, followed by inward clump migration (e.g. (cite: Bournaud:2007aa; Bournaud:2008aa; Elmegreen:2008aa; Ceverino:2010aa; Elmegreen:2011aa; Wuyts:2012aa)).

However, for DSFGs, this picture often lacks the context of how the extant stellar mass (or even ongoing unobscured star formation) is distributed.

Many studies have found a factor of $>2$ larger effective radii in the rest-frame UV/optical vs. FIR continuum for DSFGs (including (cite: Ikarashi:2015aa; Simpson:2015ab; Barro:2016aa; Hodge:2016aa; Pantoni:2021ab)).

However, these half-light sizes are subject to gradients in the mass-to-light (M/L) ratios, which may be the result of spatial variation in dust attenuation (e.g., (cite: Byun:1994aa; Jansen:1994aa; Tuffs:2004aa; Mollenhoff:2006aa; Pastrav:2013aa; Popping:2022ac)), stellar population ages (e.g., (cite: Carrasco:2010aa; van-Dokkum:2010aa; Tacchella:2015aa)), and metallicities (cite: Franx:1990aa; Molla:1997aa; Carrera:2008aa; Cresci:2010aa; Kewley:2010aa; Pilkington:2012aa)or realistically, some combination of all three (e.g., (cite: Keel:2001aa; Miller:2022ab)).

![](G165_IP_RGB_ALMA_VLA.png)

In the era of JWST, great progress is being made in directly capturing the rest-frame near-IR structure of galaxies at Cosmic Noon and earlier, offering a significantly less biased view of the actual distribution of stellar mass ((cite: Lang:2019aa; Chen:2022ae; Cheng:2022ab; Suess:2022aa; Abdurrouf:2023aa; Cheng:2023aa; Colina:2023aa; Kamieneski:2023ab; Kokorev:2023aa; Le-Bail:2023aa; Liu:2023aj; Rujopakarn:2023aa; Smail:2023aa; Amvrosiadis:2024aa; Kalita:2024aa; Sun:2024aa)), including their clumpiness, compactness, and lopsidedness.

This pixel-by-pixel comparison of stellar mass and star formation provides a key snapshot of the structural history of a galaxy, especially when supplemented with mapping of the molecular gas kinematics and dust continuum at comparable resolutions with facilities like ALMA.

For example, an examination of how the star-forming main sequence of galaxies translates on resolved scales at $z>1$ has now been made feasible (e.g., (cite: Abdurrouf:2018aa); hereafter ), along with its connection to fundamental scaling relations between the surface density of gas mass vs. star formation rate and between gas mass surface density vs. stellar mass surface density. While a full systematic study has not yet been carried out, results for a small number of objects can offer preliminary insights.

![](G165_SP_1abc_3abc_RGB_crits.png)

In this work, we focus on two DSFGs and a massive red galaxy at Cosmic Noon that have been strongly lensed by a massive galaxy cluster at $z=0.35$.

PLCK G165.7+67.0 (hereafter G165) was first identified by (cite: Canameras:2015aa) and (cite: Harrington:2016aa)[^2], hereafter , as an exceptionally IR-bright source in *Planck* and *Herschel* surveys, but was first examined in-depth by (cite: Frye:2019aa) and (cite: Pascale:2022aa).

Multi-wavelength follow-up imaging at higher resolution revealed that the substantial submillimeter flux is driven by a highly-magnified DSFG (Table [1](#tab:magnifications)) at $z=2.236$ , lensed into a giant arc by a galaxy cluster that appears to be undergoing a merger of two primary mass components (Fig. [1](#fig:lens_model), and (cite: Pascale:2022aa)).

Hereafter, we refer to this known DSFG, PLCK_G165.6295+67.0026[^3], as G165-DSFG-1 (or just DSFG-1), given its appearance as Arcs 1a and 1bc, per the labeling introduced by (cite: Frye:2019aa). With this work, we identify another strongly-lensed submillimeter source, which is believed to lie at the same redshift. Our current photometric redshift and lens model-predicted geometric redshift are consistent with $z\approx 2.23$, making it likely that the two are gravitationally interacting (see Fig. [2](#fig:SP_DSFG)). For this second object, G165.6354+67.0087, we use the nickname G165-DSFG-3 (or DSFG-3), in accordance with its appearance in Arcs 3c and 3ab.

Through its inferred properties (including $L_{\rm IR} > 10^{12.6}$), it is clearly also safely classified as a DSFG.

(cite: Frye:2024aa), hereafter , revealed substantial candidate galaxy overdensities at $z\approx 1.8$ and at $z\approx 2.2$ using a combination of spectroscopic redshift identifications with JWST NIRSpec and photometric redshifts from 8-filter NIRCam photometry. The number of candidates identified for these structures ($N>150$) rivaled even the number of objects with photometric redshifts consistent with the G165 cluster itself.

As first reported by (cite: Frye:2023ab) and (cite: Polletta:2023aa), initial inspection of the NIRCam observations immediately revealed a conspicuous multiply-imaged supernova in a set of arcs on the opposite side of the cluster from the DSFGs. Named SN H0pe, this serendipitous discovery was quickly followed-up with additional NIRCam imaging and NIRSpec spectroscopy to track the transient’s light curve and classify its type. At $z=1.78$, it was confirmed to be one of the most distant known Type Ia supernovae. This discovery may not be purely coincidence: the fortuitous alignment of a rich collection of star-forming $z\sim 2$ objects with a massive and highly elliptical foreground cluster ($M_{\rm 600 kpc} = (2.6 \pm 0.3) \times 10^{14}~M_\odot$; ) along the line of sight provides ideal conditions for the detection of Type Ia and core-collapse supernovae. As the area of time-delay cosmography has become increasingly fruitful

in recent years (cite: Treu:2022ac), the G165 cluster is likely to endure as a subject of intense interest and legacy value for years to come.

This paper is organized as follows: in Section [2](#sec:data), we outline the near-IR, radio, and mm-wave imaging used in this study. In Section [3](#sec:methodology), we discuss our approach to lens modeling and performing pixel-by-pixel SED fitting. The results of these analyses are outlined in Section [4](#sec:all_results), and their implications are discussed in Section [5](#sec:discussion) and summarized in Section [6](#sec:summary).

In this work, we adopt a $\Lambda$CDM cosmological model of $\Omega_m=0.3$, $\Omega_\Lambda = 0.7$, and $H_0 = 70~{\rm km}~{\rm s}^{-1}~{\rm Mpc}^{-1}$, and a (cite: Kroupa:2001aa) initial mass function (IMF). At the redshift of the cluster ($z=0.348$), the angular-to-physical size conversion is $1 \ensuremath{''} = 4.921$ kpc, and at the redshift of the DSFGs ($z=2.236$), $1 \ensuremath{''} = 8.243$ kpc (cite: Wright:2006aa).

To comment on our notation: throughout, we frequently use DSFG-1 and DSFG-3 as shorthand for PLCK_G165.6295+67.0026 and G165.6354+67.0087, respectively.

These names themselves are introduced to avoid confusion when referring to the actual objects in the background of the cluster. To clarify, DSFG-1 is visible in its entirety in Arc 1a, while only a fraction of the intrinsic source is visible in the merging pair Arc 1bc. Likewise, DSFG-3 is visible entirely in Arc 3c, with a small portion of the source visible in the merging pair Arc 3ab.

![image](G165_SP_1abc_RGB_ALMA_VLA.png) ![image](G165_SP_3abc_RGB_ALMA_VLA.png)

# Data

## JWST NIRCam

A more in-depth description of the JWST NIRCam data is given in (cite: Windhorst:2023aa) and (cite: Frye:2024aa), but we provide relevant details here.

G165 was observed with NIRCam in three epochs: first through the Prime Extragalactic Areas for Reionization and Lensing Science (PEARLS) program (PID 1176; PI: Windhorst) on 2023 March 30 (Epoch 1), followed by two later epochs on 2023 April 22 (Epoch 2) and 2023 May 9 (Epoch 3) through a DDT program (PID 4446, PI: Frye), which were designed to track the light curve of SN H0pe following its discovery in Epoch 1.

As the exposure times of Epoch 1 were longer (see Table 1 of ), and 8 filters were used instead of 6, for simplicity we performed most of our analysis in this work on data from Epoch 1 only, in part to minimize variance in the PSF which could impact the spatially-resolved SED analysis. Moreover, the primary targets here are detected with very high significance, and do not benefit enormously from stacking additional exposures. However, the image families used in constraining the lens model (which are often faint) benefit greatly from this additional effective exposure time, and so the stacked images are employed for that purpose. Limiting magnitudes are $m_{\rm AB} \sim 28.4 - 28.5$ for the 4 short wavelength (SW) filters (F090W / F115W / F150W / F200W) and $m_{\rm AB} \sim 28.6 - 28.9$ for the 4 long wavelength (LW) filters (F277W / F356W / F410M / F444W); see Figure 6 of .

Data were reduced in line with (cite: Windhorst:2023aa), using the STScI JWST Pipeline[^4] version 1.11.2 (cite: Bushouse:2023aa) and context file pmap_1100, but with additional improvements in “wisp" removal as described by (cite: Robotham:2023aa). Images in this work were drizzled on to 30 milliarcsecond square pixels.

## ALMA Bands 3 and 4

G165 was observed with ALMA band 3 (representative wavelength 2.7 mm, 111 GHz; hereafter referred to as 3 mm) and band 4 (2.2 mm, 138 GHz; hereafter referred to as 2 mm) as part of program 2021.1.00607.S (PI: R. Cañameras). These data were retrieved from the public ALMA archive[^5].

Continuum multi-frequency synthesis images and spectral cubes were created using the Common Astronomy Software Applications (casa) version 6.2.1 (cite: McMullin:2007aa), with `robust`$=$0.5 Briggs weighting (cite: Briggs:1995aa).

The unweighted baselines ranged from $0.03 - 0.3$ km (5th to 80th percentile).

This results in synthesized beams of $2.0\ensuremath{''} \times 0.9\ensuremath{''}$ at PA$=-2.7^{\circ}$ for 3 mm (maximum recoverable scale of $18.4\ensuremath{''}$) and $1.6\ensuremath{''} \times 0.7\ensuremath{''}$ at PA$=-18.4^{\circ}$ for 2 mm (maximum recoverable scale of $15.1\ensuremath{''}$)[^6].

The continuum noise rms levels achieved are 22 $\mu$Jy/beam (3 mm) and 20 $\mu$Jy/beam (2 mm), both over a 3.3 GHz bandwidth.

Weather conditions were favorable, with mean precipitable water vapor PWV $=0.9$ mm for the 3 mm observations (executed on 2022 May 26) and PWV$=1.4$ mm for the 2mm observations (executed on 2022 May 28).

As the lensed objects of interest are spatially resolved, photometry was performed using the flood-filling algorithm blobcat (cite: Hales:2012aa). In Table [1](#tab:magnifications), we compare the measured 2 mm and 3 mm fluxes against the 1 mm flux from the Large Millimeter Telescope (LMT) AzTEC, reported by , under assumption of a modified blackbody SED, and find relative consistency.

## VLA C Band

G165 was observed with the *Karl G. Jansky* Very Large Array in C band (4 - 8 GHz) in full polarization during the most extended A configuration through our program 18A-399 (PI: P. Kamieneski), which targeted 26 members of the *Planck* All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts (PASSAGES) sample; see (cite: Kamieneski:2024aa) for additional details.

The target was observed on 2018 April 6 during a shared track (switching with another nearby object) lasting a total of 3.0 hrs, with an effective total on-source integration time of 1.1 hrs.

Weather conditions were favorable during the observations: the phase RMS measured by the Atmospheric Phase Interferometer at the VLA site was $\approx 2^{\circ}$.

Antenna baselines ranged from $0.8 - 36.6$ km, yielding a maximum recoverable scale of $9\ensuremath{''}$.

The sensitivity reached was $2.7~ \mu{\rm Jy}~{\rm beam}^{-1}$.

Natural weighting achieved a synthesized beam of $0.65\ensuremath{''} \times 0.37\ensuremath{''}$ at PA$=72.2^{\circ}$.

The data were reduced using casa v6.1.0. Initial flagging and calibration was carried out through the VLA Calibration pipeline v2018.1. The (cite: Hogbom:1974aa) CLEAN algorithm was used to deconvolve the image down to a $2\sigma$ threshold.

As with the ALMA images, photometry was performed using blobcat (cite: Hales:2012aa), also reported in Table [2](#tab:SFR_IR).

As discussed by (cite: Pascale:2022aa), these data also reveal a number of point sources and narrow angle tails (e.g., (cite: Rudnick:1977aa; Venkatesan:1994aa)), which offer some insight into the intracluster medium and dynamical state of the galaxy cluster.

# Methodology

## Lens modeling

We constructed a parametric lens model for the G165 cluster using LENSTOOL[^7] (cite: Kneib:1993aa; Kneib:1996aa; Jullo:2007aa; Jullo:2009aa), which has been tested extensively for galaxy clusters (e.g., (cite: Johnson:2014aa; Meneghetti:2017aa)).

The model is constrained by 41 families of multiply-imaged featuresof which 14 have spectroscopic redshift information (cite: Frye:2019aa; Pascale:2022aa; Frye:2024aa), covering 4 distinct source planes. Some details of this model and the cluster members are presented in the appendix of (cite: Pascale:2024aa), but we include additional information here. For this iteration of the model, only the image-plane positions were considered, which are reported in . To estimate the astrometric uncertainty in these positions, multiple team members independently marked the positions for the known image family members, and found a median offset of $0.03\ensuremath{''}$, which is consistent with the pixel scale used for identifying images. For the mass profiles, we used two cluster halo-scale profiles for the merging cluster components, in addition to perturbations to this large-scale potential in the form of the 165 identified cluster member galaxies at $z\approx 0.35$. Each of these profiles was chosen to be a pseudo-isothermal elliptical mass distribution, or PIEMD (cite: Kassiola:1993aa).

To reduce the number of free parameters, the position of each cluster member was held fixed to the centroids of their luminous components. Likewise, the ellipticities and orientations were held fixed to match their morphologies in the F200W filter. The masses of the cluster members were scaled all together in a power law, according to their F200W flux, per (cite: Limousin:2005aa). The power law was normalized such that a characteristic $L_\star$ galaxy at the redshift of the cluster ($m_{\rm F200W} = 17.0$ AB mag) has a velocity dispersion of $\sigma_0^\star = 120~{\rm km~s}^{-1}$, a core radius of $r_{\rm core}^\star = 0.15$ kpc, and a cut radius of $r_{\rm cut}^\star = 30$ kpc. All galaxies were scaled in mass based on their flux relative to $L_\star$. We settled on these choices after some trial and error, as it was determined that the current set of lensing evidence does not sufficiently constrain the masses of perturbing cluster galaxies, so they were instead held fixed. The choices of $\sigma_0^\star$, $r_{\rm core}^\star$, and $r_{\rm cut}^\star$ match those used in several other works that use LENSTOOL, including (cite: Limousin:2008aa) and (cite: Johnson:2014aa). However, one foreground galaxy near Arc 3ab, located at

$(\alpha, \delta) =$ (11$^h$27$^m$14.304s, $+42^d$28$^m$32.32s),

was optimized independently from the other cluster members, given the large effect it has on the arc. Its velocity dispersion $\sigma$ was kept as a free parameter, assuming a uniform prior of 0 to 250 km s$^{-1}$.

As for the two cluster-scale halos, their free parameters include centroid position, ellipticity, orientation, velocity dispersion, and core radius.

As their cut/truncation radii are poorly constrained, these were fixed to values of 1000 kpc.

Uniform priors were used for these parameters, including a wide range of $\pm 5\ensuremath{''}$ in $x$ and $y$ position from the approximate center of both cluster cores, a very wide range in ellipticity from 0 to 0.85, a maximum velocity dispersion of 800 km s$^{-1}$, and a maximum core radius of $20\ensuremath{''} \approx 100$ kpc.

We also left as free parameters the redshifts for 16 background lensed image families for which no spectroscopic information is currently available.

To simplify the parameter space, we placed relatively tight priors on these, however, based on their photometric redshifts.

This was done iteratively, where we widened or adjusted the redshift range if prior iterations of the model optimization resulted in any parameters clearly being overly limited by the prior boundaries.

Still, the uncertainties in these “geometric" redshifts (often as small as $\Delta z = \pm 0.01$) are likely drastic underestimates.

We present the full set of best-fit parameter values, and the corresponding convergence map, in Appendix [7](#sec:appendix).

In this work, we adopt the median of each parameter’s posterior distribution, which is only appropriate if the posteriors are well-behaved and approximately normally distributed (and especially only if the distributions are not multi-modal).

We also provide the minimum-$\chi^2$ solutions, which are nearly always in close agreement with the median solution.

To determine magnifications, we used slightly different approaches for JWST vs. mm/radio images. For the ALMA and VLA images, which are not contaminated by nearby foreground sources[^8], we measured magnifications simply by taking the ratio of image-plane to source-plane area.

For the JWST images, we measured representative magnifications using the F200W filter, and compute an average of the magnification map weighted by source-plane flux.

In both cases, to include the relevant statistical uncertainties, we resampled 300 iterations uniformly from the MCMC-derived posterior distribution, resulting in an approximately Gaussian distribution of magnifications. The results for the Arc 1abc and Arc 3abc systems are summarized in Table [1](#tab:magnifications).

Any slight discrepancies beyond statistical uncertainty between the magnifications for rest-frame near-IR, far-IR, and radio continuum are likely due in part to very different observing parameters (e.g. PSFs), but also due to differences in source-plane distribution (as seen in Fig. [3](#fig:SP_1a_3c)).

### Redshift of DSFG-3

Since DSFG-3 lacks a secure spectroscopic redshift, we left this as a free parameter in our lens model, and allowed the redshift to vary from $z=2.0 - 2.2$ in the final model. This range was chosen based on previous iterations of the model with wider redshift priors. This is also in line with the photometric redshift of $z_{\rm phot} = 2.23 \pm 0.09$ and with previous iterations of the lens model using a wider prior range, which suggested a geometric redshift of $z_{\rm geom} \approx 2.1$.

The MCMC posterior distribution yields a quite precise value of $z_{\rm geom} = 2.11 \pm 0.01$ (although the uncertainty is likely underestimated). This narrow range is probably a result of the constraint offered by DSFG-1, which is lensed by a similar portion of the foreground cluster and has a known redshift from the LMT Redshift Search Receiver (RSR) and other single-dish sub-mm observations (; (cite: Harrington:2021aa)) and from NIRSpec .

There is no clear evidence of a second line detected in the LMT/RSR spectrum , which means either that the CO(3–2) line from DSFG-3 is blended with the line from DSFG-1 at $z=2.236$, or is undetected.

Indeed, this target has the widest linewidth ($\Delta V = 650 \pm 10$ km s$^{-1}$) of the sample presented by , and a possible secondary component at $\sim -400$ km s$^{-1}$, giving weight to the hypothesis that the lines are blended.

Since DSFG-3 is inferred to have a similar stellar mass, size, and star formation rate as DSFG-1 (as we discuss in §[4](#sec:all_results)), it is reasonable to expect comparable CO flux (or only $\sim 4$ times greater flux for DSFG-1 given its larger magnification, Table [1](#tab:magnifications)). A non-detection by virtue of a faint line flux is thus unlikely.

However, the pointing center of the LMT observations coincides with the peak of the sub-mm flux, which is dominated by the high-magnification Arc 1bc.

At an angular separation of $<11\ensuremath{''}$, Arc 3c would be near the edge of the primary beam ($\sim 13.1\ensuremath{''}$ at 106.86 GHz), so it is also somewhat possible that any lines were simply missed by the observations.

We adopt the redshift of DSFG-3 to be $z=2.23$ in this work ($\Delta V \sim 600~{\rm km~s}^{-1}$ from DSFG-1), but we briefly discuss the possibility and implications of the secondary redshift solution, $z\approx 2.12$, in Appendix [8](#sec:appendix1). Also, we do not hold fixed the redshift of DSFG-3 in our lens model given this lingering uncertainty. For the source-plane reconstructions shown in Fig. [2](#fig:SP_DSFG) and [3](#fig:SP_1a_3c), we ray trace back to $z=2.12$ for the highest-fidelity view of the source, but this has no impact on our interpretation of results.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Arc | $\mu_{2\mu{\rm m, JWST}}$ | $\mu_{2{\rm mm}}$ | $\mu_{3{\rm mm}}$ | $\mu_{6{\rm GHz}}$ | $S_{\rm 2 mm}$ | $S_{\rm 3 mm}$ | $S_{\rm 6 GHz}$ |  |
|  |  |  |  |  | \[$\mu$Jy\] | \[$\mu$Jy\] | \[$\mu$Jy\] |  |
| Arc 1a | $5.5 \pm 0.1$ | $7.6 \pm 0.2$ | $8.1 \pm 0.2$ | $6.6 \pm 0.2$ | $260 \pm 30$ | $110 \pm 30$ | $190 \pm 10$ |  |
| Arc 1bc | $42 \pm 1$ | $44 \pm 3$ | $41 \pm 4$ | $46 \pm 5$ | $1620 \pm 90$ | $860 \pm 60$ | $960 \pm 50$ |  |
| Arc 1abc |  | $28.4 \pm 2.4$ | $29.1 \pm 1.7$ | $24^{+6}_{-3}$ | $1900 \pm 100^\dagger$ | $980 \pm 60^\dagger$ | $1150 \pm 50$ |  |
| Arc 3ab | $40 \pm 2$ |  |  | $29 \pm 5$ | $<80$ | $<90$ | $39 \pm 5$ |  |
| Arc 3c | $5.9 \pm 0.1$ | $6.8 \pm 0.2$ | $7.5 \pm 0.3$ | $5.9 \pm 0.2$ | $620 \pm 40$ | $310 \pm 30$ | $132 \pm 8$ |  |
| Arc 3abc |  | $7.3 \pm 0.7$ | $7.4 \pm 0.6$ | $6.8^{+1.1}_{-0.4}$ | $620 \pm 40^\dagger$ | $310 \pm 30^\dagger$ | $171 \pm 9$ |  |

: Model-derived magnifications and observed mm/radio fluxes.

Table notes: Magnifications are measured for the F200W filter (as representative for all of the NIRCam filters) by taking the source-plane flux-weighed average over the magnification map. For the mm and radio images, magnifications are measured by simply taking the ratio of image-plane to source-plane areas.

$^{^\dagger}$ The combined flux of of Arcs 1abc and 3abc at 2 mm ($S\approx2.5$ mJy) is consistent with that expected from a modified blackbody (dust emissivity index $\beta = 1.8$) with $S_{\rm 1mm} = 24 \pm 2.0$ mJy , which is $S_{\rm 2mm}\approx 2.5$ mJy. The observed flux at 3 mm (1.3 mJy) exceeds the modified blackbody prediction (0.5 mJy), possibly owing to contamination from synchrotron emission.

### Source-plane reconstruction

The reconstruction of all images in this work in the source plane does not impose regularization or parameterization of the intrinsic structure of the source. Instead, the observed images are ray-traced to the source plane pixel-by-pixel through the `cleanlens` function of lenstool, with the image-plane oversampled by a factor of 4 and the source-plane by a factor of 2. Further details of our specific procedure may be found in Section 3.3 of (cite: Kamieneski:2024aa).

Fig. [3](#fig:SP_1a_3c) reconstructs the full structure of G165-DSFG-1 and G165-DSFG-3 by including both low- (1a and 3c) and high-magnification (1bc and 3ab) arcs.

Effectively, this simple approach convolves the high-magnification arcs with the PSF of the low-magnification counterparts (e.g., (cite: Sharma:2018aa)).

We use this version to estimate the source-plane size of the dust continuum, where we use the casa imfit task to fit the emission with 2-d Gaussian profiles (and adopt a minimum 10% fractional uncertainty).

Despite the smaller beam size of the 3 mm observations,

these dust sizes are measured for the 2 mm images given their higher S/N, as reported in Table [2](#tab:SFR_IR).

Additionally, the possible contamination from synchrotron at 3 mm is expected to result in slightly larger sizes than from thermal dust alone.

In Appendix [10](#sec:appendix2), we show the reconstructions from including only the high-magnification images, which are at essentially the finest achievable resolution.

There is general agreement with the structure seen in Fig. [3](#fig:SP_1a_3c), adding confidence to this reconstruction.

RGB images of the 8 NIRCam filters are constructed according to the Trilogy[^9] prescription (cite: Coe:2012aa).

In all cases, we also show representative source-plane PSFs to illustrate the approximate resolution of the reconstructions.

These are created by placing a simulated PSF or beam at a location in the image plane and ray-tracing it to the source-plane in the same manner as the image itself (then refitting with a 2-dimensional Gaussian).

The distorted source-plane PSFs arise because the image-plane PSFs are relatively circularly symmetric to first order, but this symmetry is lost through the ray-tracing process.

However, as there is a gradient in magnification over each of the arcs (which is much more extreme for 1bc and 3ab), the source-plane PSF is finer in regions closer to the caustic curve than those further away.

While the source-plane reconstructions assist in our interpretation of these objects, most of this work computes properties in the image plane and applies a magnification correction (or relies on magnification-invariant properties). This approach is less subject to any pitfalls of the intricacies of source-plane PSFs.

The approximate source-plane major axes of the ALMA 3 mm and 2 mm beams (roughly oriented along the major axis of the galaxies) are $1.0\ensuremath{''} \approx 8.2$ kpc and $0.8\ensuremath{''} \approx 6.6$ kpc for G165-DSFG-1, and $0.7\ensuremath{''} \approx 5.8$ kpc and $0.6\ensuremath{''} \approx 5.0$ kpc for G165-DSFG-3.

For VLA 6 GHz, the source-plane beam minor axes are approximately oriented along the galaxies’ major axes, which are $0.2\ensuremath{''} \approx 1.6$ kpc for G165-DSFG-1, and $0.1\ensuremath{''} \approx 0.83$ kpc for G165-DSFG-3.

These are indicated in Fig. [3](#fig:SP_1a_3c).

## Pixel-by-pixel SED fitting with piXedfit and bagpipes

As the cluster lensing provides an areal magnification and a flux amplification for the DSFGs, it becomes easier to ascertain the spatially-resolved properties of their stellar populations through so-called pixel-by-pixel SED fitting.

To accomplish this, we used the publicly-available package piXedfit[^10] ((cite: Abdurrouf:2021ab); also (cite: Abdurrouf:2022aa; Abdurrouf:2022ab; Abdurrouf:2023aa)) to bin pixels such that each satisfies a S/N condition in all filters, while preserving similarity in SED shape between pixels within each bin. In brief, starting with the brightest unbinned pixel, each bin is required to be larger than the F444W PSF FWHM ($0.14\ensuremath{''}$). If a S/N threshold for each filter is met (a conservative S/N$=20$, in our case), the bin is established; otherwise, the radius of the bin is increased. Before adding the new pixels from the larger radius to the bin, their SED shape is confirmed to be consistent through a $\chi^2$ calculation. This process then repeats, starting with the brightest pixel not already in a bin, and terminates once no additional bins can be constructed. Full details are provided in Section 3.3 of (cite: Abdurrouf:2021ab).

With the bin-wise photometry collected for the 8 NIRCam bands ($0.9 - 4.4~\mu$m), all convolved to the resolution of F444W, we fitted the SED of each bin with bagpipes (Bayesian Analysis of Galaxies for Physical Inference and Parameter EStimation; (cite: Carnall:2018aa)). The star formation history (SFH) was parameterized as an exponentially declining or “tau" model, where star formation promptly begins at time $T_0$ and decays relative to a timescale $\tau$. The stellar population age for each bin could vary from 0.1 Gyr to the age of the Universe at the given redshift, and $\tau$ was allowed to vary from $0.3 - 10$ Gyr.

We consider this simple smooth (i.e. not bursty) parameterization of the SFH to be appropriate given the small physical scale of each bin. In other words, given the high spatial resolution, these sub-kpc regions are perhaps best described with low time resolution (to avoid overfitting), and thus a less stochastic star formation history than a galaxy in aggregate.

The total mass formed was allowed to vary widely, from ${\rm log}_{10}(M / M_\odot) = 1 - 15$, and metallicity could vary from 0 to 3.5 $Z_\odot$.

The standard nebular component in the bagpipes fits was accounted for through the ionization parameter, log($\cal{U}$), which was allowed to vary from $-4$ to $-2$, pre-computed from cloudy photoionization models (cite: Ferland:2017aa). While higher values (up to $-1$) can be found for individually resolved H ii regions (e.g., (cite: Snijders:2007aa)), an upper limit of $-2$ is typically sufficient for starbursts resolved on kpc scales (e.g., for M82’s inner 500 pc; (cite: Thornley:2000aa; Forster-Schreiber:2001aa)).

A (cite: Calzetti:2000aa) dust attenuation model was imposed, with attenuation allowed to vary from $A_V = 0 - 3$, which we found to be a sufficient range[^11].

![](G165_DSFG_1a_run2_neb_map_properties.png)

![]({G165_DSFG_3c_run1_neb_z2.23_map_properties}.png)

# Results

## The complex, galaxy-wide assembly of stellar mass in two DSFGs at Cosmic Noon

One of the fundamental questions we have sought to address through our resolved pixel-by-pixel SED modeling of G165-DSFG-1 and G165-DSFG-3 is how their significant ongoing star formation is spatially distributed.

If DSFGs are primarily powered by violent major mergers of massive galaxies, as for local ultra-luminous infrared galaxies (ULIRGs; (cite: Armus:1987aa; Soifer:1987aa; Sanders:1988aa; Sanders:1996aa; Lonsdale:2006aa)), is it reasonable to expect that their burst of star formation might be confined only to nuclear regions, with shocks and tidal forces driving gas inwards (e.g., (cite: Hernquist:1989aa; Stockton:1990aa; Barnes:1991aa; Barnes:1992aa))? Or if other modes of extreme star formation are prevalent, such as gravitational instabilities within massive gas-rich disksfueled continuously by cold gas streams (e.g., (cite: Keres:2005aa; Dekel:2009ab; Dave:2010aa))would we expect to find a greater number of global star formation events, reaching well beyond the nucleus?

Numerous recent works have demonstrated that the effective radii of DSFGs at rest-frame far-IR are compact ($\sim 1 - 2$ kpc) and smaller than at rest-frame UV/optical (e.g., (cite: Simpson:2015ab; Ikarashi:2015aa; Barro:2016aa; Hodge:2016aa; Tadaki:2017ab)).

On the other hand, some of the most luminous DSFGsso-called hyperluminous infrared galaxies (HyLIRGs), which exceed $L_{\rm IR} > 10^{13}~L_\odot$may be more extended, in part explaining their ability to sustain SFRs above $1000~M_\odot~{\rm yr}^{-1}$ without significantly breaching the Eddington limit (e.g., (cite: Bussmann:2013aa; Kamieneski:2024aa)).

In a large sample of *Herschel*-selected candidate lensed DSFGs, (cite: Borsato:2024aa) found rest-optical sizes to be $\approx 3$ times smaller

than far-IR sizes, determined by (cite: Enia:2018aa) to be $\sim 2 - 3$ kpc.

However, these isophotal rest-optical sizes are SNR-dependent, and the far-IR sizes are derived from lower-resolution Submillimeter Array imaging, both of which may bias results towards smaller optical-to-FIR size ratios.

In this work, we find 2-mm dust continuum effective radii of $R_{e, 2{\rm mm}} = 1.6 \pm 0.2$ kpc and $2.1 \pm 0.2$ kpc for DSFG-1 and DSFG-3, respectively (Table [2](#tab:SFR_IR)).[^12]

These values are quite consistent with other members of PASSAGES (cite: Kamieneski:2024aa) and other lensed DSFGs (e.g., (cite: Bussmann:2013aa)), and in line with what

might be expected from the size-luminosity relation derived by (cite: Fujimoto:2017aa) and their intrinsic luminosities of ${\rm log}[L_{\rm IR} / L_\odot] \approx 12.5$.

Given their apparent elongated morphology suggestive of high-inclination disks (Fig. [2](#fig:SP_DSFG)), this seems to suggest a large region of ongoing obscured-mode star formation. However, higher-resolution dust continuum imaging is required to comment on this more robustly, as Arcs 1a and 3c are only marginally resolved at 2 mm.

The UV-NIR photometry captures primarily the unobscured mode of star formation, which is likely to be a small fraction of the total (obscured plus unobscured) SFR$_{\rm UV + IR}$ for such massive, highly star-forming galaxies (cite: Whitaker:2017aa).

Regardless, it is still informative to investigate the spatial scales over which unobscured star formation is occurring, as an insight into the driving mechanisms and present evolutionary stages of the galaxies.

For example, galaxies with a higher central specific SFR (sSFR$\equiv {\rm SFR} / M_\star$) are likely undergoing inside-out growth, by which a spheroidal bulge component is built up *in situ* through gas compaction (e.g., (cite: Dekel:2014aa; Zolotov:2015aa; Tacchella:2016aa; Tacchella:2018aa)).

In later stages, sSFR may be elevated in outer regions of the galaxy, pointing to inside-out quenching. This may be driven by morphological quenching (cite: Martig:2009aa; Genzel:2014aa; Tacchella:2015aa), where the central spheroidal component renders the disk stable against gravitational fragmentation of the molecular gas, even without requiring energetic feedback from a central starburst or active galactic nucleus (AGN).

Figs. [4](#fig:pixbin_1a) and [5](#fig:pixbin_3c) show the spatially-resolved bin-wise properties derived through SED fitting with piXedfit and bagpipes, including corrections for magnification from our lens model.

Given the variation in bin size, we primarily examine the surface densities of SFR and $M_\star$, or $\Sigma_{\rm SFR}$ and $\Sigma_\star$.

As gravitational lensing conserves surface brightness, these properties do not need to be corrected for magnification.

We also perform the same analysis for the high-magnification Arcs 1bc and 3ab as a consistency check in Appendix [10](#sec:appendix2).

These arcs arise only from a portion of the galaxy that crosses inside the caustics (see Fig. [2](#fig:SP_DSFG) and the red demarcation line in left panels of Figs. [6](#fig:slit_1a) and [7](#fig:slit_3c)).

For that reason, we focus here primarily on Arcs 1a and 3c.

For G165-DSFG-1 (Arc 1a), there appears to be a single central peak in $\Sigma_{\rm SFR}\approx 15~M_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2}$, and a roughly axially symmetric radial decrease (except for perhaps lower $\Sigma_{\rm SFR}$ in the northwest region).

The stellar mass surface density $\Sigma_\star$ also peaks in the center of the arclog$[\Sigma_\star / (M_\odot~{\rm kpc}^{-2})]\approx 9.5$although the peak is more consistent with an elongated ellipse parallel to the major axis of the arc. In fact, there appear to be two peaks in $\Sigma_\star$, with a slight dip between them corresponding to the peak in $\Sigma_{\rm SFR}$.

Of possible relevance is the discovery by that Arc 1a is actually composed of components at slightly different redshifts seen in projection, as indicated in the source-plane reconstruction in Fig. [2](#fig:SP_DSFG).

The redder, southeasternmost portion (NIRSpec aperture NS_969) is found to be at $z=2.2355 \pm 0.0003$, while the bluer region $0.2\ensuremath{''}$ (1.6 kpc in projection) more to the northwest (NS_46) is at $z=2.2401 \pm 0.0002$ (i.e., a rest-frame redshift difference of $\approx$ 400 km s$^{-1}$ relative to the southeast clump).

Despite this, we still refer to the system as G165-DSFG-1, as it is not possible to segregate them with the current data, and as it seems likely that they will ultimately merge into one object.

There is uncertainty in the spectroscopic redshift of G165-DSFG-3, although it shares a similar color gradient as DSFG-1 (Fig. [2](#fig:SP_DSFG)), and an even clumpier distribution of $\Sigma_\star$ (peaking at $\Sigma_\star \approx 10^{9.5}~M_\odot~{\rm kpc}^{-2}$), with as many as five distinct peaks along the major axis.

This may be suggestive even of spiral arm structures within the plane of a disk, a history of recent minor mergers, or the result of gravitational fragmentation of molecular clouds throughout the galaxy. Without kinematic information, our interpretation is necessarily limited.

The distribution of $\Sigma_{\rm SFR}$ (peaking at $\approx 8~M_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2}$) is elongated along the major axis and decreasing radially, not dissimilar to G165-DSFG-1.

Combining the SFR and $M_\star$ information yields a map of sSFR (or alternatively the mass doubling time, sSFR$^{-1}$) on sub-kpc scales.

This provides a direct measure of how and where the galaxies are actively growing (in tandem with the distribution of mass-weighted ages, also shown in Figs. [4](#fig:pixbin_1a) and [5](#fig:pixbin_3c)).

In §[4.3](#sec:rSFMS), we discuss the relation of these sSFR values to the resolved star-forming main sequence, but first we examine the relative values of sSFR as a function of projected galaxy radius.

For G165-DSFG-1, there is a clear bimodality in sSFR, with more starbursting regions in the southeast vs. the northwest (by nearly 1 dex).

This may also support the picture of DSFG-1 comprising multiple orbiting clumps seen in projection, with one both forming stars more actively and containing greater dust content, based on the $A_V$ map. The map of mass-weighted stellar ages also supports this picture, with the southeast component more or less entirely younger than $\sim100$ Myr.

Alternatively, if the orbiting clumps are not responsible for this effect, then there must be some other mechanism by which gas is driven preferentially to one side of the galaxy to form stars.

While it remains to be confirmed that DSFG-3 lies at the same redshift, one might speculate that the asymmetry is driven by a recent gravitational interaction between the two DSFGs, with molecular gas driven towards the center of mass of the system to form stars.

If a similar morphology were seen in DSFG-3, this might support an interpretation of tidal interaction between DSFG-1 and DSFG-3.

There is no such obvious asymmetry in DSFG-3, however.

In fact, the scenario for DSFG-3 is rather different: here there is an extensive central starbursting region with sSFR$> 10~{\rm Gyr}^{-1}$, with patchy regions of more mild star formation in the outskirts of the disk.

However, the very central region (where $\Sigma_\star$ peaks) has a slight depression in sSFR, which we speculate might reveal the very early stages of inside-out quenching.

In a similar resolved SED-fitting analysis, (cite: Gimenez-Arteaga:2023aa) suggested that dramatic spatial variations in sSFR could signal the important role of bursty star formation on small (kpc-sized) sub-galactic scales.

This stochastic star formation at fine spatial and temporal resolutions also makes it difficult to determine if lower sSFR is due to quenching or merely a period of inactivity between bursts.

To condense the overwhelming amount of information contained in Figs. [4](#fig:pixbin_1a) and [5](#fig:pixbin_3c), we also extract profiles of $\Sigma_{\rm SFR}$, $\Sigma_\star$, sSFR, and $A_V$ by taking

linear profiles along the major axes of Arcs 1a and 3c, which are shown in Figs. [6](#fig:slit_1a) and [7](#fig:slit_3c).

This approach is largely independent of inclination (cite: Devour:2017aa; Devour:2019aa).

In these plots, we take the piXedfit bins from Figs. [4](#fig:pixbin_1a) and [5](#fig:pixbin_3c) and compile these into binned slices of various properties along the major axis.

We do this in two ways: for the “weighted median" curves, we do not account for overcounting pixels. That is, the piXedfit-binned properties consist of regions of multiple pixels that are all assigned the same sSFR, $A_V$, etc. By not removing duplicate pixels, the result is effectively weighted by the area of each piXedfit bin contained within the major axis slices. For the “median" curve, these duplicates are removed, which gives all piXedfit bins within the major axis slice equal weight.

The inner 68% confidence intervals of pixel values are also shown as shaded curves.

Here, the skew in sSFR and $A_V$ is even more readily observable for DSFG-1, with both transitioning between higher and lower values at a similar offset of $\approx +0.5\ensuremath{''}$.

It is also clear that the $\Sigma_{\rm SFR}$ peak is skewed relative to the broad $\Sigma_\star$ plateau[^13].

For DSFG-3, the sSFR and $A_V$ profiles are less pronounced, but are ultimately greater in the center than in the outskirts. They appear largely symmetric, thus more consistent with a simpler picture of a more centrally-concentrated dusty starburst.

![](SigSFR_SigMstar_sSFR_Av_slit.png)

![](SigSFR_SigMstar_sSFR_Av_slit_3c.png)

The ionization parameter is found to generally peak at ${\rm log}(\mathcal{U}) \approx -2.3$, consistent with the inner 500 pc core of the starburst M82 ((cite: Forster-Schreiber:2001aa); see also (cite: Engelbracht:1998aa; Thornley:2000aa)).

This is also slightly below the upper limit of ${\rm log}(\mathcal{U}) = -2$ used for our SED fitting.

For DSFG-1, the inner 68% confidence interval ranges from ${\rm log}(\mathcal{U}) = -3.6$ to $-2.7$, while for DSFG-3 the range is ${\rm log}(\mathcal{U}) = -3.3$ to $-2.3$ (median uncertainty $0.3 - 0.4$ dex), but these are likely poor estimates from SED fitting alone without spectroscopy.

This is likewise the case for the estimation of stellar metallicity. While robust super-solar gas-phase metallicity has been found in the nucleus of DSFGs even at $z\sim 4$ (e.g., (cite: Birkin:2023ac; Peng:2023aa)), we do not place much confidence in the peak of $Z/Z_\odot \approx 3$ for G165-DSFG-1 and G165-DSFG-3 (apart from perhaps a believable radial decrease in both cases). However, we also find similar results of $Z/Z_\odot = 3.1 \pm 0.3$ for DSFG-1 and $Z/Z_\odot = 3.2 \pm 0.3$ from the global galaxy-wide SED fits described in §[4.6](#sec:integrated), but we consider the unaccounted-for systematic uncertainties too great to further interpret these results.

## A favorable dust geometry for detection of supernovae?

We also remark that the widespread star formation and starbursting regionsalong with some regions of decreased dust attenuationhave implications for the observable rate of supernovae, which we discuss in detail in §[5.3](#sec:SN_rates).

If the formation of massive stars (i.e. progenitors of core-collapse supernovae, or CCSNe) is not limited just to highly dust-obscured nuclear starbursts (cite: Mattila:2001aa), but is apportioned more evenly throughout the disk, then the turbulence in the ISM may result in a patchy, porous, and generally complex star vs. dust geometry that would facilitate easier detection of SNe than a scenario of a uniform dust screen (cite: Casey:2014ab; Narayanan:2018ab).

Likewise, star formation in the outskirts of the galaxy might also result in a “frosting" of unobscured UV-bright massive stars (e.g., (cite: Safarzadeh:2017ab)).

This has not yet been tested in practice, but such DSFGs with evidence for galaxy-wide star formation events and inhomogeneous distributions of dust may thus be ideal candidates for continued monitoring for supernovae.

![](CDF_SFR_AV.png)

To get a sense of what supernova rates would be observed given different observing depths, we sum the resolved SFRs for only bins with attenuations below a certain value, shown in Fig. [8](#fig:CDF).

For example, all bins of DSFG-1 are consistent with $A_V < 3$, so the summed (magnification-uncorrected) $\mu {\rm SFR}_{A_V < 3} \approx 380~M_\odot~{\rm yr}^{-1}$ (see Table [3](#tab:SFR_SED)), while

below $A_V < 2$ yields $\mu {\rm SFR}_{A_V < 2} \approx 130~M_\odot~{\rm yr}^{-1}$, or 34% of the total.

Likewise, for DSFG-3, the total SFR satisfies $\mu {\rm SFR}_{A_V < 3} \approx 340~M_\odot~{\rm yr}^{-1}$ (Table [3](#tab:SFR_SED)), while $\mu {\rm SFR}_{A_V < 2} \approx 190~M_\odot~{\rm yr}^{-1}$ (56% of total).

Essentially, this implies that a shallower point-source sensitivity accounting for only up to 2 mag dust attenuation for supernovae would still detect them at a rate of $30 - 60$% the intrinsic rate.

This contrasts with the estimated $\lesssim 20$% recovered rate of supernovae at optical wavelengths for some local ULIRGs (e.g., Arp 220 and Arp 299; (cite: Leaman:2011aa; Mattila:2012aa); also (cite: Richmond:1998aa)).

(cite: Mattila:2012aa) and (cite: Dahlen:2012aa) recognized that the increasing fraction of the cosmic star formation rate occurring within luminous infrared galaxies (LIRGs; $10^{11} < L_{\rm IR} / L_\odot < 10^{12}$) and ULIRGs (cite: Magnelli:2011aa) might result in dire, prohibitively large fractions of missed CCSNe at $z > 1$.

However, the concrete differences in the distribution and driving mechanisms of star formation in distant vs. local ULIRGs that have become apparent in recent years may work immensely in our favor, as we contend here.

Moreover, a more dispersed distribution of CCSNe is favorable for lensed objects like G165-DSFG-1 and G165-DSFG-3, as it improves the odds that any given supernova will occur within a multiply-imaged region of the galaxy.

If all SNe were confined to the galaxy nucleus, this would effectively require that this region falls by chance within the caustics in order to ever observe a multiply-imaged supernova.

![image](G165_DSFG_1a_run2_neb_map_SFMS.png) ![image]({G165_DSFG_3c_run1_neb_z2.23_map_SFMS}.png)

## Resolved star-forming main sequence in DSFG-1 and DSFG-3

Remarkably, most star-forming galaxies (SFGs) fall on a tight, nearly linear scaling relation (that evolves with redshift) between SFR and $M_\star$, known commonly as the star-forming main sequence, as has been borne out extensively

(including

(cite: Brinchmann:2004aa; Daddi:2007aa; Elbaz:2007aa; Noeske:2007aa; Noeske:2007ab; Salim:2007aa; Whitaker:2012aa; Speagle:2014aa; Renzini:2015aa)).

While the meaning behind this result is still somewhat subject to debate, it is commonly interpreted as an indication that most SFGs grow steadily when considered over $>100$ Myr timescales (although individual objects are likely to oscillate around the main sequence; e.g., (cite: Tacchella:2016ab)).

What remains highly uncertain is if and how this relation holds for $\sim$kpc-scale regions within galaxies.

In parallel with the integrated properties of SFR and $M_\star$, their respective surface densities $\Sigma_{\rm SFR}$ and $\Sigma_\star$ are correlated through what is referred to as the spatially resolved star formation main sequence (rSFMS),

first explored by (cite: Sanchez:2013aa) and (cite: Cano-Diaz:2016aa) locally and at higher redshift by (cite: Wuyts:2013aa).

A number of works since have supported the existence of the correlation, suggesting that it is physically motivated at sub-galactic scales

(cite: Hemmati:2014aa; Gonzalez-Delgado:2016aa; Magdis:2016aa; Abdurrouf:2017aa; Hsieh:2017aa; Maragkoudakis:2017aa; Abdurrouf:2018aa; Ellison:2018aa; Hall:2018aa; Liu:2018aa; Medling:2018aa; Cano-Diaz:2019aa; Vulcani:2019aa; Bluck:2020aa; Bluck:2020ab; Enia:2020aa; Morselli:2020aa; Pessa:2021aa; Pessa:2022aa; Ellison:2023aa).

In particular, (cite: Erroz-Ferrer:2019aa) demonstrated that

the relation between $\Sigma_{\rm SFR}$ and $\Sigma_\star$ may be more fundamental; the global SFR$-M_\star$ relation could be in part a consequence of the generally small variation for $\Sigma_{\rm SFR}$ and $\Sigma_\star$ throughout a galaxy, combined with the size-mass relation (cite: Shen:2003aa; van-der-Wel:2014aa) that scales both up and yields a linear relation between the integrated properties SFR and $M_\star$ (cite: Vulcani:2019aa).

The rSFMS has also been observed through simulations (e.g. (cite: Trayford:2019aa; Hani:2020ab; McDonough:2023aa)).

However, we caution that the relation is likely non-universal, with non-trivial variations in the rSFMS from galaxy to galaxy (e.g., (cite: Vulcani:2019aa; Ellison:2021aa)), and the slope of the sequence may be influenced by the minimum size scales that are probed (e.g., (cite: Hani:2020ab)).

Fig. [9](#fig:rSFMS) compares the distribution of individual piXedfit bins in Arcs 1 and 3 in the $\Sigma_{\rm SFR}-\Sigma_\star$ plane.

To facilitate comparison with work at lower-$z$, we include only the bins with an area approximately equivalent to a radius of $150 - 1500$ pc.

Additionally, we expect that SED fitting at $\lesssim 100$ pc physical scales (comparable to individual giant molecular clouds) becomes much less physically meaningful.

As (cite: Vulcani:2019aa) point out, it is highly possible for star clusters to migrate somewhat from the natal molecular cloud where they formed, which perturbs the one-to-one relationship between $\Sigma_{\rm SFR}$ and $\Sigma_{\rm gas}$ (and by extension, between $\Sigma_{\rm SFR}$ and $\Sigma_\star$).

Since our method is applied to the magnified image-plane arcs, we first divide the bin areas by a fiducial magnification ($\mu=6$ for Arcs 1 and 3, and $\mu = 8$ for Arc 2) before filtering to include only intrinsic sizes from $\approx 150 - 1500$ pc.

So far, there are rather few studies that have examined the rSFMS beyond the local Universe.

(cite: Jafariyazani:2019aa) used integral-field spectroscopy to place a sample covering $0.1 < z < 0.4$ on the rSFMS, while (cite: Yao:2022aa) likewise covered $0.2 < z < 0.4$.

Further afield, our comparison is primarily limited to (cite: Wuyts:2013aa) at $0.7 < z < 1.5$, (cite: Magdis:2016aa) at $0.8 < z < 1.0$, at $0.8 < z < 1.8$, and (cite: Nelson:2021aa) at $0.8 < z < 1.5$.

Fig. [9](#fig:rSFMS) shows the best-fit rSFMS relations from these works (over approximately the pertinent range in $\Sigma_\star$ that each study dealt with), in addition to local relations from (cite: Cano-Diaz:2016aa), (cite: Abdurrouf:2017aa), and (cite: Ellison:2023aa).

(cite: Abdurrouf:2017aa) and first examined how the radial profiles of $\Sigma_{\rm SFR}(r)$, $\Sigma_\star(r)$, and ${\rm sSFR}(r)$ generally evolve with redshift, and by extension, how the rSFMS evolves. We can use this to predict where the pixels of the G165 DSFGs lie relative to the rSFMS with the caveat that the rSFMS is not universal from one galaxy to another.

For now, we employ the redshift evolutionary model of , which tracked progenitors from $z\approx 1.06$ ($t(z) \approx 5.5$ Gyr in our assumed cosmology) to $z\approx 0.02$ ($t(z) \approx 13.2$ Gyr), and extend it backwards in time to $z=2.24$ ($t(z) \approx 2.9$ Gyr).

The result is shown as a dotted curve of black stars in Fig. [9](#fig:rSFMS) (and see also Fig. 15 of for $z=0$ to 1.1 in steps of $\Delta z = 0.11$). Relative to this curve, we find that the overwhelming majority ($\approx 99\%$) of the bins in Arc 1 lie above the model rSFMS at $z \approx 2.2$ (accounting for nearly $\approx 100\%$ of the total area), whereas $\approx 89\%$ of the bins in Arc 3 lie above (here accounting for $85\%$ of the area)[^14].

This suggests that a clear majority of the bins shown in Figs. [4](#fig:pixbin_1a) and [5](#fig:pixbin_3c) are actively star-forming (and some of which are starbursting). For these objects, at least, it appears to be the case that star formation is not confined purely to a central starburst region, but is widely distributed (often in clumps) throughout the plane of the disk. This has been demonstrated to be the case in recent years for a number of high-$z$ DSFGs, especially in contrast with local ULIRGs (e.g., (cite: Chapman:2004aa; Carilli:2010aa; Ivison:2010ad; Ivison:2011aa; Rujopakarn:2011aa; Hodge:2012aa; Hatsukade:2015aa; Miettinen:2015aa; Simpson:2015ab; Swinbank:2015aa; Hodge:2016aa; Sharda:2018aa; Tadaki:2018aa; Hodge:2019aa; Kamieneski:2024aa)).

Here, we have demonstrated that the unobscured mode of star formation inferred from the UV-NIR SED is similarly widespread for DSFG-1 and DSFG-3, matching the widespread obscured star formation suggested by our finding of $R_e \sim 3$ kpc for the dust continuum.

This is a result that we revisit in §[4.5](#sec:UVJ), using $U-V$ and $V-J$ colors alone for a largely independent and non-parametric characterization.

The evolutionary model we employ for the rSFMS was only designed for $z\sim 1$ to $z=0$, and it is not clear how the evolution might extend to our objects at $z\approx 2.2$. However,

the $z\sim 1$ sample from includes objects up to $z\approx 1.8$, only $500 - 700$ Myr after the G165 DSFGs.

Their sample of high-mass objects ($M_\star > 10^{10.5}~M_\odot$, SFR $\lesssim 300~M_\odot~{\rm yr}^{-1}$) is also selected to focus on face-on (low-ellipticity) disk-like objects, so it is subject to different systematic effects than our work.

Nevertheless, properly quantifying the spatial extent of starbursting regions in G165 and other $z\sim 2$ galaxies will not be possible until a more detailed study of the rSFMS at higher redshifts has been undertaken. With JWST covering an ever-increasing number of strongly lensed objects, this is becoming more feasible, but beyond the scope of our current study.

### A mode of elevated star formation efficiency in the resolved star-forming main sequence

We also observe for the first time what appears to be a secondary “starburst" sequence $\sim 1$ dex above the “star-forming" main sequence (Fig. [9](#fig:rSFMS)).

This elevated mode of star formation is not dissimilar to the higher star formation efficiency (SFE) mode of the Schmidt-Kennicutt relation between molecular hydrogen mass $M_{H_2}$ and SFR on resolved scales (cite: Sharon:2019ab).

Recent works (e.g., (cite: Baker:2022ab)) have demonstrated that the (integrated) SFMS is not a fundamental correlation, but rather the result of two more fundamental scaling relations with less scatter: the Schmidt-Kennicutt relation, and the Molecular Gas Main Sequence (MGMS) between $M_{H_2}$ and $M_\star$.

(cite: Lin:2019aa) found likewise (and since supported by (cite: Ellison:2021aa) and (cite: Baker:2022aa)) that the correlation between $\Sigma_{\rm SFR}$ and $\Sigma_\star$ is merely a byproduct of the correlations between $\Sigma_{\rm SFR}$ and $\Sigma_{H_2}$ (which is the strongest correlation) and between $\Sigma_{H_2}$ and $\Sigma_\star$.

Together, this suggests a picture where the rate of star formation is generally driven (or regulated) by the availability of molecular gas fuel (although this is not necessarily a universal slope, e.g., (cite: Daddi:2010aa)), or neutral HI in the case of low-density environments at the outskirts of galaxies (cite: Leroy:2008aa). The correlation between $\Sigma_{H_2}$ vs. $\Sigma_\star$ is suggestive of gas being preferentially accreted in regions of deeper gravitational potential, as traced by the distribution of stellar mass (cite: Lin:2019aa).

The bimodalities in the rSFMS and the Schmidt-Kennicutt relation may in fact be directly related if, for example, the MGMS that is hypothesized to link the two is not itself bimodal.

In other words, regions of elevated SFE could also be detected merely through $\Sigma_{\rm SFR}$ vs. $\Sigma_\star$, under the assumption that each galaxy satisfies a unimodal $\Sigma_{H_2}$-$\Sigma_\star$ relation (without large scatter).

Without information on the molecular gas (or dust) distribution of the G165 DSFGs on similar spatial scales, or the gas excitation conditions through multiple spectral lines to accurately infer gas mass (e.g., (cite: Harrington:2021aa)), we are missing part of the picture in characterizing what drives stellar mass assembly across the galaxy. However, the rSFMS is still helpful in characterizing the widespread distribution

of star formation and

the rapid consumption of molecular gas.

![](G165_SP_2b_RGB.png)

![](G165_MRG_2a_run1_neb_map_properties.png)

## Resolved properties of the massive host galaxy of SN H0pe

As discussed by (cite: Polletta:2023aa) and , the rest-frame optical spectrum of Arc system 2abc, host to SN H0pe, shows evidence for a mostly intermediate-age stellar population at $\sim 2$ Gyr (e.g., a strong NaD line and larger D(4000) value). The discovery of a Type Ia supernova itself helps support this,

as these require delay times for white dwarf progenitors ($\sim 3-8~M_\odot$) to evolve off of the main sequence and reach the end of their lifetimes. This delay time distribution appears to peak at $\sim 1 - 3$ Gyr ((cite: Maoz:2012ab), and references therein).

While the galaxy has evidence of some ongoing star formation, $10^{10.9}~M_\odot$ of stellar mass has already been assembled by the time it is observed at $z=1.78$ .

We fit its UV-NIR SED with bagpipes in Appendix [11](#sec:appendix3), and remark on possible degeneracies with this narrow wavelength range which affect our interpretations..

Fig. [11](#fig:pixbin_2a) shows the results of spatially-resolved SED fitting for Arc 2a, which is host to SN H0pe. As this image is understood to arrive first (followed by 2c then 2b), the supernova is faintest in this image, having already faded substantially in its light curve. We thus choose this arc for SED fitting, as it is subject to the least contamination from the SN. Moreover, it is also less contaminated by intracluster light than image 2b (which coincides with the axis of the merging cluster), and more isolated than 2c (which is nearby another very red arc, of currently-unknown redshift).

While the properties of this massive, mildly star-forming galaxy are naturally of interest in relation to SN H0pe, it also serves as a useful control for comparison with the more extreme DSFGs in this work.

Fig. [12](#fig:rSFMS_2a) shows the relation of Arc 2a to the rSFMS, which shows clear contrasts with Fig. [9](#fig:rSFMS). While 99% and 89% of bins in Arcs 1a and 3c (respectively) lie above the center of the rSFMS evolved to their respective redshifts (or areal fractions of $\sim$100% and 85%), merely 44% of bins in Arc 2a are above the rSFMS at $z=1.78$ (or $\approx 57\%$ in terms of galaxy area). This is strongly influenced by the presence of a low-$\Sigma_{\rm SFR}$ (and low-sSFR) sequence at the center of the galaxywith high stellar mass surface density, log$(\Sigma_\star [M_\odot~{\rm yr}^{-1}])>9$. This locus is

entirely absent for the DSFGs, although the sSFRs are still above the nominal “green valley" transition at log(sSFR)$<-10.8$ yr$^{-1}$ (cite: Salim:2014ab).

It also appears to be the case that many bins are clustered around the main sequence, adding some further confidence in the validity of backward-evolving the rSFMS model from , although it is true that

this arc actually falls within the redshift range used for the model.

There are a select number of regions that appear to be starbursting, perhaps in line with the conclusion by that the galaxy is still star-forming (despite its very large stellar mass), as evidenced by the detection of H$\alpha$ emission (alongside spectral features that confirm the presence of a much older stellar population).

![](G165_MRG_2a_run1_neb_map_SFMS.png)

The large stellar mass and non-negligible ongoing star formation may in part help explain the favorable conditions leading to the discovery of SN H0pe, as the SN Ia rate is hypothesized to depend on an instantaneous term proportional to the SFR and on an extended term proportional to the stellar mass (e.g., (cite: Scannapieco:2005aa; Smith:2012aa)).

Similarly, the Type Ia SN Requiem (cite: Rodney:2021ab) was discovered in a low-sSFR host, classified as a Massive/Magnified Red Galaxy (MRG; (cite: Newman:2018aa; Akhshik:2020aa)).

Since then, an additional SN Ia (“Encore") has recently been found in the same host galaxy (cite: Pierel:2024ab).

In §[5.3](#sec:SN_rates), we discuss the prospects for discovering core-collapse SNe behind G165 given the high rate of star formation. However, given the large stellar mass of the host of SN H0pe (cite: Polletta:2023aa; Frye:2024aa), we also consider that the G165 field may be a source for the discovery of additional Type Ia SNe, as well (e.g., (cite: Shu:2018ab; Holwerda:2021aa)).

![image](UVJ_1a.png) ![image](UVJ_1a_map.png) ![image](UVJ_3c.png) ![image](UVJ_3c_map.png) ![image](UVJ_2a.png) ![image](UVJ_2a_map.png)

## Resolved $UVJ$ diagrams

The plane of $U-V$ and $V-J$ colors (or the well-known $UVJ$ diagram) is an efficient method to discern between stellar populations that are red due to age vs. those that are reddened by dust (e.g., (cite: Labbe:2005aa; Wuyts:2007aa; Williams:2009aa; Brammer:2011aa; Whitaker:2011aa)).

For objects at $z\approx 2$, it was not practically feasible before JWST to reach the same resolution for rest-frame $J$-band (near-IR) imaging as for rest-frame (optical) $U$ and $V$.

With the advent of NIRCam, an essentially direct conversion from F115W, F200W, and F356W photometry to rest-frame $U$, $V$, and $J$ (respectively) at $z\approx 2$ is now possible. For the range of $1.7 < z < 2.3$, (cite: Miller:2022ab) calibrated a linear relation for rest-frame $U-V$ and $V-J$ colors as a function of redshift and photometry in the NIRCam filters. While the classification of stellar populations with the $UVJ$ diagram is imperfect, and made more uncertain by the assumptions of the conversion to rest-frame colors, it benefits from a reliance on very few pieces of information. No SED templates are imposed directly, and only 3 photometric measurements are employed (with which a robust SED fit would hardly be practical).

Fortunately, the objects of interest in this work are all understood to lie within the redshift range for which the (cite: Miller:2022ab) calibration is valid, so we use this semi-independent method alongside the measurement of sSFR from the SED fits (§[4.1](#sec:resolved_SED_maps) and §[4.4](#sec:SN_host_maps)).

The left panels of Fig. [13](#fig:UVJ) plot the rest-frame $U-V$ and $V-J$ colors of the bins in the DSFG-1 and DSFG-3 alongside arc 2a, all still shown in the image plane. As differential magnification is negligible within the small bin size (i.e., $U$, $V$, and $J$ are all magnified equally in each bin), there is no need to correct the $UVJ$ colors.

The marker colors indicate sSFR as derived from the SED.

Before introducing the selection criteria, we first remark on the approximate similarity in the locus for Arcs 1a and 3c.

Arc 2a occupies a clearly different region, in particular towards redder $U-V$ colors.

These reddest $U-V$ bins include substantially lower sSFRs, about 3 orders of magnitude lower than the lowest-sSFR bins in DSFG-1 and DSFG-3.

Referring to Fig. [11](#fig:pixbin_2a), we find unsurprisingly that these are concentrated at the nucleus (central kpc) of the galaxy.

Given the high stellar mass density here, $\Sigma_\star > 10^{10.5}~M_\odot~{\rm kpc}^{-2}$, it seems likely that this galaxy has an early formation redshift (cite: Estrada-Carpenter:2020aa) and has already built up a dense stellar bulge and started quenching inside-out (e.g., (cite: Fang:2013aa; Ji:2022aa; Ji:2022ab; Ji:2023aa)). This is consistent with (but not necessarily implicitly due to) the gravitational stabilization of gas by an increasing dominance of a spheroidal bulge component, known as morphological quenching (cite: Martig:2009aa).

We use the higher-redshift selection box for quiescent galaxies defined by (cite: Muzzin:2013aa). While the distinction between star-forming vs. dusty star-forming populations is more arbitrary and less pronounced, we also show the $V-J > 1.25$ cut from (cite: Miller:2022ab).

Differential magnification may indeed impact the global colors for each of the three arcs (shown as gray squares in Fig. [13](#fig:UVJ); see discussion of global properties in §[4.6](#sec:integrated)). We find that DSFG-1 and DSFG-3 lie in very similar locations, safely in the star-forming/dusty star-forming region, but essentially close to the dividing line between the two.

Arc 2a, on the other hand, lies on the cusp of the division between quiescent and dusty star-forming.

The right-column panels of Fig. [13](#fig:UVJ) show the classification of bins from the $UVJ$ diagram as quiescent (Q), star-forming (SF), and dusty star-forming (DSF).

Curiously, while there is a greater presence of quiescent regions in the massive galaxy seen in Arc 2a (relative to the DSFG arcs 1a and 3c), a clear majority of the galaxy’s area consists of stellar populations consistent with the dusty star-forming region of the $UVJ$ diagram, with only its outskirts being classified as less-obscured star-forming.

Extending the quiescent selection box slightly to redder $V-J$ colors would change the classification of a large number of bins from dusty star-forming to quiescent.

Yet, the overall classification of this object as quiescent would likely be erroneous, despite its low sSFR ($\sim 0.08 ~ {\rm Gyr}^{-1}$; ).

Less-obscured star formation is found in the outskirts of the galaxy, and the galaxy center (with peak $\Sigma_\star$) is coincident with the quiescent bins, perhaps signifying inside-out quenching.

In §[4.4](#sec:SN_host_maps) and Fig. [12](#fig:rSFMS_2a), we found that 57% of the galaxy’s area was consistent with being above the center of the rSFMS evolved to $z=1.78$.

In other words, $<43\%$ was quiescent based on sSFR, or at least on the lower end of the resolved main sequence;

now, using the independent $UVJ$ selection, we find that $\sim 20\%$ of the area is classified as quiescent.

For the DSFGs, Arcs 1a and 3c, there are remarkably few regions that fall into the quiescent selection. For Arc 1a, there is a clear separation with the southeast portion dominated by dusty star-forming populations and a northwest portion of regular star-forming populations. This could further support the orbiting clumps hypothesis (§[4.1](#sec:resolved_SED_maps)), with both components actively forming stars, but one hosting greater dust content (or at least, somehow more obscured due to projection effects, although this region is actually at a lower redshift).

As for Arc 3c, the inner regions of the galaxy are DSF with outskirts that are classified as SF, with isolated embedded quiescent regions. These seem consistent with the observation of multiple peaks in $\Sigma_\star$, perhaps as a result of a late-stage merger or the large-scale fragmentation of gas within the disk.

In both DSFG-1 and DSFG-3, the most active star formation (highest sSFR) is clearly concentrated in the DSF box, which is to be expected given the connection between starbursts and dust obscuration (e.g., (cite: Whitaker:2017aa)).

![image](G165_1a_BAGPIPES_summary.png) ![image](G165_3c_BAGPIPES_summary.png)

## A comparison of integrated vs. resolved properties

In addition to the spatially-resolved SED fitting, we also use Bagpipes to measure global properties of G165-DSFG-1 and G165-DSFG-3. For simplicity, we measure the photometry of the counterimage arcs 1a and 3c, as these contain the entire object (in contrast with the high-magnification arcs 1bc and 3ab, which arise from only a small fraction of their respective sources). Moreover, the magnification gradient for these counterimages, while not entirely negligible, is much smaller. After convolving all filters with a kernel to match the PSF of the coarsest-resolution filter (F444W), we use photutils (cite: Bradley:2022aa) to capture Kron aperture fluxes (cite: Kron:1980aa).

We fit the 8-filter photometry with bagpipes in an identical manner as for the pixel-by-pixel fluxes, described in §[3.2](#sec:pixelbypixel), using the same set of priors.

While we measure photometry at 2 mm, 3 mm, and 6 GHz (Table [1](#tab:magnifications)), these are only included in a combined SED fit for the sum of Arc 1a, 1bc, 3ab, and 3c.

The resolution of these long-wavelength observations ($\sim 1.1\ensuremath{''}$, $\sim 1.3\ensuremath{''}$, and $\sim 0.5\ensuremath{''}$, respectively) are much coarser than what is enabled by JWST (see Fig. [3](#fig:SP_1a_3c)).

Moreover, the synthesized beam of the ALMA observations is highly elongated, owing to this being a high-declination ($+42^{\circ}$) target for ALMA’s southern latitude. Unfortunately, this elongation is essentially aligned with the orientation of greatest magnification, so lensing does not offer an easy remedy.

With these parameters of the currently-available data, it is therefore not worthwhile to attempt spatially-resolved SED fitting with both ALMA and JWST, as only a few resolving elements cover the extent of the arcs.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | $\mu_{\rm 2 mm} {\rm SFR}_{\rm IR}^\dagger$ | SFR$_{\rm IR}$ | log\[$L_{\rm IR} /L_\odot$\] | $R_{\rm CC}^\ddagger$ | $R_{\rm CC} (1+z)^{-1}$ | $R_{e,2{\rm mm}}$ | $R_{e,2{\rm mm}}$ |
|  | \[$M_\odot~{\rm yr}^{-1}$\] | \[$M_\odot~{\rm yr}^{-1}$\] |  | \[yr$^{-1}$\] | \[yr$^{-1}$\] | \[arcsec\] | \[kpc\] |
| G165-DSFG-1 | $9100 \pm 1900$ | $320 \pm 70$ | $12.5 \pm 0.1$ | $3.3 \pm 0.7$ | $1.0 \pm 0.2$ | $0.20 \pm 0.02$ | $1.6 \pm 0.2$ |
| G165-DSFG-3 | $2900 \pm 500$ | $400 \pm 80$ | $12.6 \pm 0.1$ | $4.2 \pm 0.8$ | $1.3 \pm 0.2$ | $0.25 \pm 0.03$ | $2.1 \pm 0.2$ |

: Properties of DSFG-1 and DSFG-3 from total IR dust SED, and corresponding SN rates.

Table notes: We derive the SFR of the two DSFGs independently using the far-IR photometry vs. the rest-frame UV-NIR photometry from NIRCam (which is shown in Table [3](#tab:SFR_SED)). As the far-IR photometry largely does not resolve Arcs 1abc and 3abc, we make a preliminary estimate by apportioning the total ${\rm SFR}_{\rm IR}$ according to their share of flux at 2 mm and 3 mm (combining Arcs 1a and 1bc, and Arcs 3ab and 3c), as both arc systems are understood to be at similar enough redshifts. Then, these apportioned SFRs are corrected for the total 2 mm magnifications of Arc 1abc and Arc 3abc, respectively.

Based on these various SFRs, we estimate the rate of occurrence of core-collapse supernovae (for the rest-frame of each galaxy); the observable rate is likely bracketed by the SED- vs. IR-inferred SFRs, given that SNe in some very dusty environments may be missed (or, alternatively, the extreme star formation may lead to a porosity in the dust geometry that lends to a more favorable chance for discovery). $^{^\dagger}$ The total apparent (i.e. lensing-uncorrected) IR-derived SFR of $12000\pm 2000 ~M_\odot {\rm yr}^{-1}$ from is divided between Arcs 1abc and 3abc according to their ratio of millimeter flux, $S_{\rm 1abc} / S_{\rm 3abc} = 3.1 \pm 0.3$ (averaged for 2 mm and 3 mm). $^{^\ddagger}$ Expected rate of core-collapse supernovae tabulated as $R_{\rm CC} = k_{\rm CC} \cdot {\rm SFR}$; $k_{\rm CC}=0.0104 ~ M_\odot^{-1}$ (e.g., (cite: Strolger:2015aa)). These are intrinsic SN rates; observed SN rates will be dilated by a factor of $(1+z)^{-1}$, but also increased for any SNe occurring in regions of the galaxy that are multiply imaged.

However, we can make a comparison of SED-fitting with vs. without the inclusion of far-IR rest-frame photometry for the unresolved, combined SED of both DSFG-1 and DSFG-3 together.

Flux measurements that better constrain the peak of the dust SED at rest-frame 100 $\mu$m are available ((cite: Canameras:2015aa); ), but these all have resolutions of $8.5\ensuremath{''}$in the case of the LMT AzTECor much larger.

In Appendix [12](#sec:appendix4), we sum the NIR photometry of the four arcs to revisit the SED fit of (cite: Harrington:2016aa).

As shown by (cite: Battisti:2019aa), the stellar mass of DSFGs can be underestimated by 0.3 dex with only UV to near-IR coverage (a discrepancy that is greatest for objects with $M_\star > 10^{10}~M_\odot$).

More broadly, for galaxies simulated with the Evolution and Assembly of GaLaxies and their Environments (EAGLE; (cite: Schaye:2015aa)) project

and the SKIRT dust radiative transfer code (cite: Baes:2011aa), (cite: Dudzeviciute:2020aa) found that even with UV-to-radio coverage, SED-modeling resulted in a systematic under-prediction of stellar mass by $0.5 \pm 0.1$ dex.

It also appears to be the case that inclusion of far-IR photometry in an SED fit tends to reduce the inferred SFR (cite: Pacifici:2023aa), although (cite: Wise:2023aa) found that SFR can be under- or over-estimated (up to 1 dex) from UV to near-IR alone. For galaxies with lower SFR$_{\rm UV-NIR} \lesssim 300~M_\odot~{\rm yr}^{-1}$, they found that adding FIR data boosted the estimated SFR; for high SFR$_{\rm UV-NIR}$ galaxies, FIR data lowered the estimated SFR.

Indeed, in our case, DSFG-1 and DSFG-3 have a combined SFR$_{\rm UV-NIR} \approx 90~M_\odot~{\rm yr}^{-1}$, but the unresolved UV-FIR SED yields SFR$_{\rm UV-FIR} = 350 \pm 70~M_\odot~{\rm yr}^{-1}$, a $\sim 0.6$ dex increase (Table [3](#tab:SFR_SED)).

As is also emphasized by (cite: Smail:2023aa), spatially resolved “pixel-by-pixel" SED modeling is made significantly more robust by the inclusion of long-wavelength photometry at similar angular resolution, highlighting the particular need for submillimeter interferometry in this analysis.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | $\mu_{\rm 2\mu m} {\rm SFR}$ | ${\rm SFR}$ | $R_{\rm CC}^\ddagger$ | log\[$\frac{\mu_{\rm 2 \mu m} M_\star}{M_\odot}$\] | log\[$\frac{M_\star}{M_\odot}$\] | log\[$\frac{\rm sSFR}{{\rm yr}^{-1}}$\] | $A_V$ |
|  | \[$M_\odot~{\rm yr}^{-1}$\] | \[$M_\odot~{\rm yr}^{-1}$\] | \[yr$^{-1}$\] |  |  |  | \[mag\] |
| Arc 1a (SED) | $280 \pm 130$ | $50 \pm 20$ | $0.5 \pm 0.2$ | $10.9 \pm 0.1$ | $10.2 \pm 0.1$ | $-8.5 \pm 0.3$ | $1.5 \pm 0.3$ |
| Arc 1a (H$\alpha$) | $320 \pm 140^\dagger$ | $60 \pm 30^\dagger$ | $0.6 \pm 0.3$ | $10.5 \pm 0.1^\dagger$ | $9.7 \pm 0.1^\dagger$ | $-8.4 \pm 0.3^\dagger$ | $1.5 \pm 0.4^{\dagger\dagger}$ |
| Arc 1a (bin-wise sum) | $380 \pm 10$ | $69 \pm 3$ | $0.72 \pm 0.03$ | $10.91 \pm 0.01$ | $10.17 \pm 0.02$ | $-8.34\pm 0.02$ | $\approx 1.0 \pm 0.8^{\dagger\dagger}$ |
| Arc 3c (SED) | $260 \pm 110$ | $40 \pm 20$ | $0.4 \pm 0.2$ | $11.1 \pm 0.1$ | $10.3 \pm 0.1$ | $-8.7 \pm 0.3$ | $1.2 \pm 0.2$ |
| Arc 3c (bin-wise sum) | $440 \pm 10$ | $75 \pm 3$ | $0.78 \pm 0.03$ | $11.06 \pm 0.01$ | $10.29 \pm 0.02$ | $-8.42 \pm 0.02$ | $1.2 \pm 0.7$ |
| Arcs 1abc+3abc (UV-FIR)$^\star$ | $5560 \pm 280$ | $350 \pm 70$ | $3.6 \pm 0.7$ | $11.68 \pm 0.03$ | $10.48 \pm 0.09$ | $-7.93 \pm 0.03$ | $2.54 \pm 0.04$ |

: Properties of DSFG-1 and DSFG-3 from rest-frame UV through near-IR SED fitting, and corresponding SN rates.

Table notes: We compute the UV-NIR SED-derived SFRs for Arcs 1a and 3c (see Fig. [14](#fig:SED_1a_3c)), and correct these for respective magnifications at $2 \mu$m. These values are lower than the SFR$_{\rm IR}$ estimates, but this is expected given their large dust attenuations.

In Appendix [12](#sec:appendix4), we fit the summed SED of both DSFGs so that the unresolved far-IR photometry can be incorporated.

The intrinsic, combined SFR$_{\rm UV-FIR}$ is $\approx 4$ times the sum of SFR$_{\rm UV-NIR}$ for the two DSFGs, while the summed stellar masses are more consistent with the integrated value.

We also compare with the properties derived through the H$\alpha$ measurement by , incorporating the two NIRSpec apertures that covered this object (but applying our 2 $\mu$m magnifications, from Table [1](#tab:magnifications)). In all cases, we find quite close agreement with our independently-derived values.

$^{^\ddagger}$ Expected rate of core-collapse supernovae tabulated as in Table [2](#tab:SFR_IR). $^{^\dagger}$ The H$\alpha$-derived SFR and stellar masses from are the summed values from NIRSpec apertures NS_46 and NS_969. The intrinsic (magnification-corrected) properties use the 2 $\mu$m magnifications from Table [1](#tab:magnifications). The sSFR is determined from this SFR$_{\rm H\alpha}$ and the stellar mass, which is determined from an SED model that incorporated H$\alpha$ flux as a constraint. $^{^{\dagger\dagger}}$ As described in §[4.6](#sec:integrated), the dust attenuation $A_V$ is estimated from the Balmer-decrement derived $E(B-V)_{\rm gas} = 0.85 \pm 0.25$ for NS_969 and a (cite: Calzetti:2000aa) reddening law, $R_V = A_V / E(B-V) = 4.05$. We lastly impose a conversion to a stellar continuum color excess through $E(B-V)_{\rm stellar} = 0.44 E(B-V)_{\rm gas}$, per (cite: Calzetti:1997ab). For the bin-wise dust attenuation, we provide the inner 68% interval for the bins’ values. $^{^\star}$ Here, we use the total flux-weighted magnification for both DSFG-1 and DSFG-3 combined, $\mu = 16 \pm 3$, to derive intrinsic values.

(cite: Zibetti:2009aa) first presented an important bias to consider when inferring the stellar mass of a galaxy: mass estimates based on global (galaxy-integrated) fluxes were 40% (0.2 dex) lower than those determined by summing over the map of stellar mass derived from spatially-resolved SED fitting.

This effect is the direct result of the stellar mass contribution from dust-obscured regions being underestimated through the unresolved photometry (although (cite: Sorba:2015aa; Sorba:2018ab) point out that an “outshining" bias from the youngest stellar populations may be responsible, as well).

(cite: Song:2023ab) found recently that without coverage of rest-frame near-IR in SED fitting, $M_\star$ can be overestimated by 0.2 dex, owing directly to an overestimate of both dust attenuation and stellar ages from only rest-frame UV and optical photometry.

As shown in Table [3](#tab:SFR_SED), there is excellent agreement in the stellar masses determined through integrated photometry vs. a sum of stellar masses derived through resolved bin-wise SED fitting with piXedfit, which may indeed be the result of photometric coverage out to rest-frame 1.4 $\mu$m.

Table [3](#tab:SFR_SED) also compares with the H$\alpha$-inferred SFR and dust attenuation properties presented by for G165-DSFG-1.

These are the result of combining measurements from NIRSpec slits NS_46 and NS_969, the latter of which is labeled “Arc 1a" in their Table 4.

We find strong agreement for SFR, especially within uncertainties: global $\mu{\rm SFR}_{\rm NIR} = 280 \pm 130~M_\odot~{\rm yr}^{-1}$ vs. spatially-integrated $\mu{\rm SFR}_{\rm NIR} = 380 \pm 10~M_\odot~{\rm yr}^{-1}$ vs. $\mu{\rm SFR}_{{\rm H}\alpha} = 320 \pm 140~M_\odot~{\rm yr}^{-1}$.

The stellar mass derived by is not completely independent of our result, as they used a joint photometric and spectroscopic SED fit with FAST$++$ (cite: Kriek:2009ab; Schreiber:2018aa).

Whether due to the different SED fitting algorithms or to the exclusion of spectroscopic information, the stellar mass we estimatelog$[\mu M_\star / M_\odot] = 10.9 \pm 0.1$is 0.4 dex larger than the value quoted in .

Our assumption of a “single" SFH in the form of an exponentially declining “tau" model may underestimate the stellar mass by $0.1 - 0.3$ dex relative to a multi-component SFH (cite: Michaowski:2014aa; Carnall:2019ab; Jain:2023aa).

Given the typical uncertainty of 0.1 dex in stellar mass for SED modeling at $z>1$ (e.g., (cite: Pacifici:2023aa)), or even slightly elevated uncertainty of $\sim 0.3$ dex for DSFGs (cite: Michaowski:2014aa),

it is perhaps most likely that the statistically significant discrepancy is explained by the information provided by the near-IR spectroscopy (or perhaps the extrapolation from limited slit coverage of the source).

Finally, we compare the estimate of dust attenuation that we find from modeling the UV-NIR SED against that derived from the Balmer decrement in H$\alpha$ vs. H$\beta$ from .

They measured $E(B-V) = 0.85 \pm 0.25$ for NS_969 (with which we choose to compare here, given its larger uncertainty). For a (cite: Calzetti:2000aa) reddening law, or $R_V = A_V / E(B-V) = 4.05$, this yields $A_V = 3.0 \pm 1.0$.

However, this discrepancy with our smaller value of $A_V = 1.5 \pm 0.3$ can be

explained by the typically larger color excess for ionized gas relative to stellar continuum. (cite: Calzetti:1997aa) quantify this as $E(B-V)_{\rm stellar} = 0.44 \times E(B-V)_{\rm gas}$ (cf. (cite: Shivaei:2015aa)). Applying this correction to the value from , we recover $A_V = 1.5 \pm 0.4$, in superb agreement with our finding.

For the diffuse ISM in the outskirts of galaxies, the ratio of $E(B-V)_{\rm stars} / E(B-V)_{{\rm H}\textsc{ii}}$ is larger than for stellar birth clouds in star-forming regions, and even approaches unity (e.g., (cite: Robertson:2024aa)).

Our finding that a ratio of 0.44 is appropriate for DSFG-1 may actually be in line with our interpretation of widespread star-forming regions, but this claim is limited for now by the current spectroscopic coverage of just a narrow region of the arc.

# Discussion

## How $UVJ$ selection breaks down on resolved scales, and possible evidence for radial dust transport within the disk

There are at least a dozen bins for Arc 2a in Fig. [13](#fig:UVJ) with very low sSFRs (log$[{\rm sSFR}/{\rm yr}^{-1}] < -11.5$) that are still safely outside of the classical quiescent selection region, and would instead be classified as dusty star-forming populations.

The quiescent sequence has been found to evolve with age(cite: Belli:2019aa) found a best-fit relation for the median stellar age of ${\rm log}(t_{\rm 50}~ [{\rm yr}]) = 7.03 + 0.84(V-J) + 0.74(U-V)$.

These redder colors in resolved $U-V$ and $V-J$ can thus partly be the result of older stellar populations ($\sim 3$ Gyr),

but this model still severely underpredicts the finding of $V-J \approx 1.7$ and $U-V \approx 2.3$. Ultimately, the most likely explanation seems to be that these quiescent regions are more dust-attenuated than typically expected. The reddening vector of $\Delta A_V$ shown in Fig. [13](#fig:UVJ) implies that several of these low-sSFR bins have at least $A_V > 0.5$ mag.

This may also be borne out by the finding of $A_V \gtrsim 1$ for nearly the entirety of Arc 2a in Fig. [11](#fig:pixbin_2a).

As some added confirmation, SN H0pe is located nearby this dusty quiescent region, and estimated via light-curve fitting to be attenuated by $A_V = 1.21 \pm 0.05$ ((cite: Pierel:2024aa)).

While dust in quiescent galaxies is still very much an area of active research, owing to the difficulty this presents for observations (e.g., (cite: Gomez:2010aa; Rowlands:2012aa; Magdis:2021aa; Donevski:2023aa); and references therein), they are often assumed to be quite dust-poor.

Revisions to the original $UVJ$ selection frequently exclude the $V-J < 1.5$ cut to accommodate older and dustier quiescent galaxies

(cite: van-der-Wel:2014aa; Whitaker:2015aa; Belli:2019aa).

For Arc 2a, this correction would appropriately enclose the low-sSFR bins within the quiescent regime, but would also erroneously include regions with sSFRs that are over 2 dex larger (sSFR $\gtrsim 0.5$ Gyr$^{-1}$).

This might indicate a

shortcoming of our interpretation of the classical $UVJ$ selection when applied to resolved scales.

In a similar way that the resolved star formation main sequence breaks down at $\sim 100$ pc and smaller, owing to stars migrating from their parent star-forming clouds,

the $UVJ$ diagram presumably also breaks down when significant amounts of dust and metals formed in regions of active star formation are transported to adjacent, more quiescent regions.

This can occur over short distances within the plane of the disk through turbulent motions in the ISM (cite: Cho:2003aa), but (cite: Vorobyov:2006aa) showed that spiral stellar density waves could help shepherd dust several kpc in the radial direction over the course of $\sim 1$ Gyr (see also (cite: Mishurov:2014aa)).

The extra reddening seen may also be due to extraplanar dust that has been transported a few kpc into the circumgalactic medium by the likes of galactic-scale winds driven by supernovae and winds from massive stars (cite: MacLow:1989aa; Norman:1989aa; Heckman:1990aa; Heckman:2017aa; Richie:2024aa) or simply through momentum injection by radiation pressure (e.g., (cite: Ferrara:1991aa; Murray:2005aa; Thompson:2015aa; Barnes:2020aa; Kannan:2021aa)).

However, it is not clear if extraplanar dust (or even a thick disk of dust) can constitute a large enough fraction of the total dust mass, as it is

estimated to be $<5\%$ (cite: Howk:2000aa; Popescu:2000aa; Bianchi:2011aa; Seon:2014aa).

The vertical stability of the disk also plays a role, as diffuse distributions of dust appear to be more predominant in low-mass, slow-rotating disks (cite: Dalcanton:2004aa; Holwerda:2012aa).

This extraplanar dust is also typically thought to be highly filamentary in nature, associated with chimney vents and extending a few kpc from the midplane

((cite: Wang:2001aa; Stein:2020ab; Mosenkov:2022aa); see also review by (cite: Veilleux:2020aa)).

It is unlikely to provide the necessary column densities to reproduce the observed $A_V$ over large scales (cite: Thompson:2004aa), especially when considering the effect of grain destruction by sputtering (e.g., (cite: Spitzer:1978aa)).

Admittedly,

widespread large attenuations do not necessitate uniform, thick screens of dust;

they merely need large quantities of dust to be spatially correlated with regions of visible starlight.

We thus consider it most likely that the bulk of the dust responsible for the attenuation is still largely contained (and well mixed) within the disk.

Over larger, galaxy-wide scales, this effect is likely to be less of a concern, as $UVJ$ colors will be biased in favor of the unobscured sightlines.

For globally quiescent objects, this means that the more dust-free regions with older stellar populations will dominate. This appears to be the case for the global colors of Arc 2a, as the object just barely falls within the $UVJ$-quiescent regime.

Relatively few studies so far have examined spatially-resolved $UVJ$ diagrams in the era of JWST (including (cite: Miller:2022ab; Kokorev:2023aa; Suess:2023aa)), so our speculation on the effect of dust transport is necessarily limited.

Yet, we can expect a better understanding of these systematics (and in what other circumstances the selection criteria break down; e.g., (cite: Leja:2019aa)) with time.

## Starbursts or not? The proximity of DSFG-1 and DSFG-3 to the star-forming main sequence

In §[4.3](#sec:rSFMS) we considered the location of spatially-resolved regions relative to the resolved star formation main sequence, but now we examine the position of DSFG-1 and DSFG-3 as a whole.

For both DSFG-1 at $z=2.236 ~(t = 2.88~{\rm Gyr})$ and DSFG-3 at $z=2.1 ~(t = 3.07~{\rm Gyr})$, the (cite: Speagle:2014aa) model for the evolution of the main sequence[^15]

yields ${\rm log}[{\rm SFR}(M_\star, t)] \approx 0.8~{\rm log}M_\star - 6.2$.

Using our derived stellar mass of DSFG-1 of ${\rm log}M_\star = 10.2$, we find ${\rm SFR}_{\rm MS} \approx 90~M_\odot~{\rm yr}^{-1}$.

The IR-inferred SFR$_{\rm IR} \approx 320~M_\odot~{\rm yr}^{-1}$ is therefore approximately 3.6 times that of the main sequence at this redshift.

As for DSFG-3, with stellar mass ${\rm log}M_\star = 10.3$, ${\rm SFR}_{\rm MS} \approx 110 ~ M_\odot~{\rm yr}^{-1}$, and the inferred SFR$_{\rm IR} \approx 400~M_\odot~{\rm yr}^{-1}$ is likewise approximately 3.6 times that of the main sequence at this redshift.

With distance to the main sequence defined as $\Delta_{\rm MS} \equiv {\rm log}_{10}({\rm SFR} / {\rm SFR}_{\rm MS}$, both cases yield $\Delta_{\rm MS} \approx 0.6$ dex.

Adopting a $\Delta_{\rm MS} \ge 0.6$ dex threshold (e.g., (cite: Rodighiero:2011aa)) for starbursts above the main sequencechosen to be a factor of 2 above the typical scatter of $\approx0.3$ dex (cite: Brinchmann:2004aa; Daddi:2007aa; Elbaz:2007aa; Noeske:2007aa; Salim:2007aa; Whitaker:2012aa; Speagle:2014aa; Tacchella:2016ab)this means that DSFG-1 and DSFG-3 are only just marginally classified as starbursts.

While DSFGs with such high SFRs are often incorrectly presumed to lie universally within the starburst regime, (cite: Rodighiero:2011aa) found that only $20\% \pm 4\%$ of galaxies with ${\rm SFR} > 100~M_\odot~{\rm yr}^{-1}$ satisfied the $+0.6$ dex criterion.

Similarly, (cite: Barrufet:2020aa) found that approximately 60% of DSFGs (in a sample of 185) have SFRs consistent with the star-forming main sequence.

Indeed, many claims have been made that

DSFGs simply occupy the high-$M_\star$ end of the SFMS (e.g., (cite: Finlator:2006aa; Dunlop:2011aa; Magnelli:2012aa; Michaowski:2012aa; Sargent:2012aa; Targett:2013aa; Koprowski:2016aa; Dunlop:2017aa; Elbaz:2018aa; Drew:2020aa; Pantoni:2021ab); contrast with (cite: Hainline:2011aa), for example).

Furthermore, for a set of 15 other lensed DSFGs in the PASSAGES sample (not including G165), (cite: Kamieneski:2024aa) found that proxies for $\Delta_{\rm MS}$ (namely, molecular gas depletion time and $\Sigma_{\rm SFR}$) predicted broad consistency with the upper end of the star-forming main sequence, but not necessarily classification as starbursts.

In this work, we have also found that the radial profiles of sSFR (Figs. [6](#fig:slit_1a) and [7](#fig:slit_3c)) are broadly consistent with those expected for starbursts from (cite: Nelson:2021aa).

The finding that the DSFGs in the G165 field can be classified as starbursts may have some connection to the finding that they reside within a highly active star-forming environment (and possible galaxy overdensity) by although (cite: Drew:2020aa) contend that distance to the SFMS may be a poor indicator of recent merger activity.

Regardless, the locus of high-$z$ DSFGs on the SFR$-M_\star$ plane helps to quantify the role of gas supply-dependent, secular evolution (cite: Dave:2012aa).

A more systematic examination of the stellar masses of DSFGsespecially now, with JWST helping to circumvent their prohibitive degree of dust obscurationwill ultimately shed more light on their connection to the star-forming main sequence.

For now, the inconsistency of DSFGs and SMGs lying on or above the main sequence (cite: Hodge:2020ab) may ultimately arise from the apparent heterogeneity of the overall population (e.g., (cite: Hayward:2011aa; Hayward:2012aa; Magnelli:2012aa; Hayward:2013aa)).

## Prediction of observer-frame supernova rates from G165-DSFG-1 and G165-DSFG-3, and prospects for future discovery

The connection of core-collapse supernova rates to SFRs is straightforward, as CCSN progenitors are short-lived massive stars, believed to range in mass from $8 - 50~M_\odot$ (cite: Nomoto:1984aa; Tsujimoto:1997aa).

The supernova rate can thus be tabulated as $R_{\rm CC} = k_{\rm CC} \cdot {\rm SFR}$, where the scale factor is derived from the IMF $\phi(M)$ as $$\begin{equation}
k_{\rm CC} = \frac{\int_{8~M_\odot}^{50~M_\odot} \phi(M) dM}{\int_{0.1~M_\odot}^{125~M_\odot} M \phi(M) dM}
\end{equation}$$ and essentially represents the fraction of the forming stellar populations that consists of CCSN progenitors.

These lower and upper mass limits and a (cite: Kroupa:2001aa) IMF yield $k_{\rm CC} = 0.0104~M_\odot^{-1}$ (e.g. (cite: Strolger:2015aa)), which we adopt for this work to remain consistent with the SED fitting. A (cite: Salpeter:1955aa) IMF for the same $8-50~M_\odot$ progenitor range would yield $k_{\rm CC} = 0.0070~M_\odot^{-1}$ (e.g., (cite: Mattila:2001aa; Young:2008aa)), but this difference is essentially canceled out by the corresponding effect on the SFR (e.g., (cite: Madau:2014aa; Ziegler:2022aa)).

With this in mind, the predicted rest-frame supernova rate for G165-DSFG-1 is $3.3 \pm 0.7~{\rm yr}^{-1}$ using the FIR-derived SFR, or $0.5 \pm 0.2~{\rm yr}^{-1}$ using the lower, UV-NIR SED-derived SFR (see Tables [2](#tab:SFR_IR) and [3](#tab:SFR_SED)).

For G165-DSFG-3, these rates are comparable: $4.2 \pm 0.8~{\rm yr}^{-1}$ (FIR) and $0.4 \pm 0.2~{\rm yr}^{-1}$ (UV-NIR SED).

Before taking into account the multiplexing provided by multiple images of any SNe, these rates translate to observed-frame values[^16] for G165-DSFG-1 of $R_{\rm CC, obs} \approx 0.2$ yr$^{-1}$ (SED) to $\approx 1.0$ yr$^{-1}$ (FIR), and for G165-DSFG-3 of $R_{\rm CC, obs} \approx 0.1$ yr$^{-1}$ (SED) to $\approx 1.3$ yr$^{-1}$ (FIR).

However, for the most reliable rate estimate, we use the SFR from the best-fit UV-through-FIR SED for DSFG-1 and DSFG-3 combined, ${\rm SFR}_{\rm UV-FIR} = 350 \pm 70~M_\odot~{\rm yr}^{-1}$.

This results in a total expected rest-frame rate of $R_{\rm CC} = 3.6 \pm 0.7~{\rm yr}^{-1}$, or a remarkable observer-frame rate of $1.1 \pm 0.2~{\rm yr}^{-1}$.

This very high rate is derived only from the pair of DSFGs;

however, as discussed by , the H$\alpha$-derived SFR for the objects associated with Arcs 1abc and 2abc groups surpasses 500 $M_\odot~{\rm yr}^{-1}$, which comes from only the unobscured mode of star formation.

Given that these groups appear to signal galaxy overdensities at $z\sim 2$, it may well be the case that $\gtrsim 1 - 2$ CCSNe yr$^{-1}$ may be observable for the G165 cluster.

This makes the G165 field an extremely attractive target for follow-up monitoring campaigns with JWST, as even the six Frontier Field clusters (cite: Lotz:2017aa) all together would provide only 0.9 CCSNe per year, with a cadence of four 1-hour visits with F150W within a year (cite: Petrushevska:2018ab).

Given the best-fit $A_V \approx 2.5$ from the UV-FIR SED, it is entirely feasible to detect the descendent supernovae with only modest integration with JWST.

An appropriate cadence would be designed to span a baseline of at least several months, so that enough time elapses for a clearly observable light curve evolution of any SNe (which is subject to a factor of $1+z$ in cosmological time dilation).

This last point is crucial, and helps to answer the inevitable question of why no CCSNe have yet been discovered in G165, given that two follow-up visits were undertaken with JWST on 22 April 2023 and 9 May 2023 after the discovery of the Type Ia SN H0pe in imaging on 30 March 2023. At only $+23$ d and $+40$ d from Earth’s perspective, this is a mere $+8$ d and $+13$ d in the rest-frame at $z\sim 2$, which is hardly sufficient to guarantee a CCSN detection.

The cadence of observations for SN H0pe was designed for monitoring of a discovered event; a cadence for discovering new SNe will simply need to extend over a longer period of time.

# Summary and Conclusions

With this work, we have examined in detail the magnified, massive galaxies at $z\sim 2$ behind the G165 galaxy cluster, including two luminous dusty star-forming galaxies (log$(M_\star / M_\odot) \approx 10.2$; SFR$_{\rm IR}\approx 300-400~M_\odot~{\rm yr}^{-1}$) and a massive galaxy that appears to be exiting a phase of dusty star formation (log$(M_\star / M_\odot) \approx 10.8 - 11.0$ and SFR$_{{\rm H}\alpha}\approx 5-10~M_\odot~{\rm yr}^{-1}$; ).

This latter object has been the subject of intense interest as the host of a recently-discovered triply-lensed Type Ia supernova, SN H0pe.

Yet, the lensed DSFGs are responsible for the intense submillimeter flux by which the cluster was first discovered (cite: Canameras:2015aa; Harrington:2016aa; Frye:2019aa; Pascale:2022aa),

and we have sought to further elucidate their properties through recent imaging in the near-IR with JWST and in the millimeter-wave through ALMA.

We also present a new parametric lens model for the G165 cluster, developed with lenstool. This model was constructed predominantly for the purpose of predicting lensing time delays for SN H0pe, in order to compare with values measured independently through the photometric and spectroscopic light curve, and thus infer the Hubble constant $H_0$.

However, this model is also invaluable for reconstructing the intrinsic (i.e. magnification-corrected) properties of the lensed DSFGs.

Coincidentally, what was initially thought to be a single DSFG strongly lensed by the foreground merging galaxy cluster has turned out to be two DSFGs with a peculiar (almost uncanny) similarity.

The original known DSFG, with a detection of CO(3–2) at $z=2.236$ (; also (cite: Harrington:2021aa))

was identified as a merging image pair Arc 1bc, and the counterimage Arc 1a by (cite: Frye:2019aa) and (cite: Pascale:2022aa).

With new NIRCam and ALMA continuum imaging, it has become clear that the object identified as Arc 3ab (merging pair) and Arc 3c (counterimage) on the same side of the lensing cluster also harbors considerable dust and star formation.

In fact, while the Arc 1abc system (which we denote G165-DSFG-1) is considerably brighter in dust continuum (primarily due to the contribution from the high-magnification Arc 1bc) and likewise presumably CO emission, the intrinsic properties are very similar to the Arc 3abc system (G165-DSFG-3),

which may even have a larger SFR$_{\rm IR}$ ($400 \pm 80~M_\odot~{\rm yr}^{-1}$ vs. $320 \pm 70~M_\odot~{\rm yr}^{-1}$).

The redshift of DSFG-3 is still somewhat uncertain, as the current molecular line detections are all spatially unresolved and cannot distinguish between the two. It is most likely that it also lies at $z \approx 2.236$ with DSFG-1, so that their CO lines are blended at the 100 km s$^{-1}$ spectral resolution of LMT/RSR.

If they do in fact lie at the same redshift, then this proximity ($\approx 1\ensuremath{''}$, $<10$ kpc) would certainly imply that the objects are in the early stages of a spectacular gas-rich major merger (with a nearly 1:1 mass ratio, each with log$(M_\star / M_\odot) \approx 10.2$).

The color gradients that are clearly apparent in Fig. [2](#fig:SP_DSFG) may even be the result of tidal disruption of molecular gas after a first passage, driving an asymmetry of dust-obscured star formation towards the center of mass of the system (which is most readily observable in DSFG-1; Fig. [6](#fig:slit_1a)).

Moreover, the fainter Arc 3, 4, and 6 clumps that lie in between DSFG-1 and DSFG-3 (and predicted by the lens model to lie at the same redshift) could be additional evidence for such a significant gravitational interaction.

Future spectroscopic follow-up and kinematic information for the molecular gas is ultimately necessary to help resolve this open question.

Regardless of their distances along the line-of-sight, the presence of two strongly star-forming DSFGs only $1\ensuremath{''}$ apart in the sky is a remarkable finding.

In fact, one could perhaps even make the case that this conjunction would be more impressive in the sky *without* the magnification and distortion contributed by the lensing galaxy cluster!

More quantitatively, they share similar IR-inferred SFRs, as well as UV-NIR SED-derived SFRs ($50 \pm 20~ M_\odot~{\rm yr}^{-1}$ for DSFG-1, $40 \pm 20~ M_\odot~{\rm yr}^{-1}$ for DSFG-3), stellar masses (${\rm log}(M_\star / M_\odot) = 10.2 \pm 0.1$ vs. $10.3 \pm 0.1$, respectively), and dust attenuation ($A_V = 1.5 \pm 0.3$ vs. $A_V = 1.2 \pm 0.2$).

Their intrinsic (source-plane) dust continuum sizes are $1.6 \pm 0.2$ kpc and $2.1 \pm 0.2$ kpc.

Unsurprisingly, given the well-known correlation of radio with the far-IR (e.g., (cite: van-der-Kruit:1971aa; de-Jong:1985aa; Helou:1985aa; Condon:1992aa; Lisenfeld:1996aa; Yun:2001aa; Bell:2003aa; Murphy:2006aa; Murphy:2006ab)), they also have similar radio continuum fluxes ($S_{\rm 6GHz}/\mu \approx 30 ~\mu{\rm Jy}$ for Arc 1a and $\approx 20 ~\mu{\rm Jy}$ for Arc 3c).

Their position in the $UVJ$ diagram is functionally identical ($U-V \approx 1.1$, $V-J \approx 1.2$), so their similarities cannot

be attributed to limited flexibility in SED fitting.

Given the diversity and heterogeneity of DSFGs as a populationsee (cite: Smail:2023aa) for another recent example of two DSFGs nearby to each other behind a lensing cluster, but with markedly different propertiesthis chance ultra-close alignment of two remarkably similar DSFGs is very peculiar.

While we do not wish to fully speculate on whether or not this is purely coincidence, especially given the uncertainty in exact redshift for one of the objects, it is maybe not entirely outside the realm of possibility that these objects could be associated with filamentary nodes of large-scale structure in the Universe.

As discussed in our introduction, DSFGs are widely believed to be associated with galaxy overdensities and protoclusters (see the theoretical work by (cite: Chiang:2013aa), and recent review by (cite: Alberts:2022ab) and references therein).

This is similar to the association of protoclusters with high-redshift radio galaxies (HzRGs; e.g. (cite: Venemans:2007aa; Miley:2008aa)) or Ly$\alpha$ emitters (e.g., (cite: Keel:1999aa; Umehata:2015aa; Harikane:2019aa)) and extended Ly$\alpha$ nebulae, also known as Lyman Alpha Blobs (e.g. (cite: Steidel:2000aa; Hennawi:2015aa; Arrigoni-Battaia:2018ab; Ramakrishnan:2023aa); review by (cite: Overzier:2016aa)).

These signposts, and their connections to each other, are still very much an active area of research.

And indeed, (cite: Frye:2024aa) found evidence of a substantial overdensity of $z\approx 2$ galaxies behind G165 through photometric redshifts (rivaling even the number of identified members of the foreground cluster at $z=0.35$).

The authors also identified several groups of objects found serendipitously to lie at the same redshift (one association of six objects at $z=1.8$ and another of several galaxies at $z=2.2$) with the JWST NIRSpec Micro-Shutter Array (MSA).

Given the limitations of how MSA slits could be arranged, there are almost certainly other members of these associations that are not yet uncovered.

With this rich set of background objects, all strongly lensed by a massive merging galaxy cluster, the G165 field is sure to be the source of a wealth of future astrophysical discoveries.

We summarize the primary scientific findings of our work:

- Through resolved SED fitting of DSFG-1 and DSFG-3, we find complex distributions of $\Sigma_{\rm SFR}$, $\Sigma_\star$, and $A_V$ (which are of primary concern for this work).

  For DSFG-1, there is a noticeable asymmetry, with star formation and dust attenuation skewed higher towards the southeast, with the peak in $\Sigma_\star$ essentially occupying a highly elliptical central region rather than a single peak. These likely are related to the presence of multiple orbiting components at slightly different redshifts in this arc ($z=2.2355$ vs. $z=2.2401$).

- In the case of DSFG-3, there is not this clear asymmetry. Here, $\Sigma_{\rm SFR}$ is centrally peaked but again in a rather elliptical nuclear region. Stellar mass density $\Sigma_\star$, on the other hand, shows multiple distinct peaks throughout the disk plane, possibly signaling a history of (major or minor) merger activity. Dust attenuation $A_V$ is patchy throughout the object, with two distinct peaks, neither of which seem to be at the galaxy center.

- We examine the position of the spatially-resolved regions (on scales of $150 - 1500$ pc) on the resolved star formation main sequence, which extends the global relation down to sub-galactic scales. There is a clear distinction between DSFG-1 and DSFG-3 vs. the more quiescent (or at least inside-out quenching) host of SN H0pe, examined through Arc 2a. For the DSFGs, we even observe a possible sequence at an elevated mode of star formation efficiency.

- By extrapolating the model from (cite: Abdurrouf:2018aa) for the evolution of the rSFMS between $z\approx 1.8$ to 0 backwards to $z\approx 2$, we gain an initial sense of what areal fractions of the two DSFGs and Arc 2a are consistent with being above the rSFMS.

  For the DSFGs, these star-forming/starburst regions account for an overwhelming portion of the area ($80-100\%$), in contrast with only $\sim 60\%$ for Arc 2a.

  This supports the picture of many luminous DSFGs sustaining large-scale star-forming events, which are difficult to fully explain through major mergers.

- The two DSFGs occupy similar locations in the $UVJ$ plane, as do the loci of their resolved, pixel-by-pixel colors.

  While not all regions are classified as dusty star-forming, only a small minority would be classified as $UVJ$-quiescent, further indicating the presence of large-scale galaxy-wide star formation events in tandem with the rSFMS results.

- For the more quiescent galaxy seen in Arc 2a (according to its global $UVJ$ color), which is possibly undergoing inside-out quenching, we find a higher fraction of regions within the quiescent regime.

  Curiously, this object falls primarily within the dusty star-forming region of the $UVJ$-plane, with only a small area in the outskirts of the disk falling within the unobscured star-forming regime.

- Comparing $UVJ$ colors and SED-derived sSFRs indicates a possible breakdown of the classical $UVJ$ selection on resolved scales.

  Moreover, we find evidence for a substantial degree of dust attenuation for the low-sSFR regions, including the region where SN H0pe is located. We suggest that this could be the result of efficient radial dust transport within the galaxy.

- In comparing the properties we derive for DSFG-1 and DSFG-3 by using global galaxy-wide photometry vs. SED-fitting the spatially-resolved photometry and summing the relevant properties, we find approximate agreement for both SFRs and $M_\star$.

  As Arc 1a also has an H$\alpha$ detection reported by , we also compare SFR$_{{\rm H}\alpha}$ with ${\rm SFR}_{\rm SED}$, finding very close agreement. Comparing the attenuation $A_V$ found through SED fitting vs. through the Balmer decrement, we reach excellent agreement for $A_V = 1.5$, if we make the assumption that $E(B-V)_{\rm stellar} = 0.44\cdot E(B-V)_{\rm gas}$ (cite: Calzetti:1997aa; Calzetti:2000aa).

- Using the global properties of DSFG-1 and DSFG-3, we find that they lie directly on the $\Delta_{\rm MS} = +0.6$ dex threshold above the star-forming main sequence to be classified as starbursts.

  The location of DSFGs on the SFMS is still subject to debate, but it is obvious that they cannot simply be uniformly considered starbursts or high-$M_\star$ end main sequence galaxies.

  In this case, we consider it perhaps notable that these DSFGs are starbursting despite being largely disk-like and without particularly obvious signs of merger activity, which is often responsible for a temporary elevation in sSFR.

- Employing our lens model for the purpose of estimating the magnifications and time delays of the three images of SN H0pe, we find $\mu_a = 6.7 \pm 0.1$, $\mu_b = 9.8 \pm 0.3$, and $\mu_c = 8.9 \pm 0.3$, which are in reasonable agreement with the values estimated from the light curve photometry.

  For relative time delays, our model predicts arrival time after image SN2a to be $\Delta t_{c,a} = 53 \pm 3$ days and $\Delta t_{b,a} = 106 \pm 2$ days.

  These are used in the inference of $H_0$ by (cite: Pascale:2024aa).

- Using the combined SFR inferred from the rest-frame UV to FIR SED, along with the information obtained through our lens model, we estimate the combined rate of core-collapse supernovae in DSFG-1 and DSFG-3 to be $3.6 \pm 0.7~{\rm yr}^{-1}$. With cosmological time dilation, this reduces to $1.1 \pm 0.2$ yr$^{-1}$.

In reality, the rate at which we can detect SNe depends also on the control time, or the amount of time that a survey is capable of detecting a given SN (cite: Zwicky:1938aa).

The often patchy dust geometry of DSFGs also makes the prediction of how attenuated supernovae will be quite difficult.

For this reason, the near-IR sensitivity of JWST may provide the safest observing strategy, but detections with the Vera C. Rubin Observatory’s Legacy Survey of Space and Time (LSST) or the Nancy Grace Roman Space Telescope certainly cannot be ruled out (e.g., (cite: Hounsell:2018aa; Petrushevska:2020aa)).

Moreover, the large-scale nature of the star formation events in these DSFGs lends well to increasing the chances of multiplexing the observed SN rate through multiple imaging by lensing, as this makes it more likely that a CCSN will occur in a region of the galaxy inside the caustics.

To this last point, we re-emphasize that these estimates come only from the two galaxies DSFG-1 and DSFG-3 alone; based on the $\gtrsim 100~M_\odot~{\rm yr}^{-1}$ integrated (obscured and unobscured) SFR for the $z\sim 2$ group, still estimate a rate of $\gtrsim 1$ SNe yr$^{-1}$ from the observer’s perspective, making a compelling case for a continued monitoring campaign of G165.

# Acknowledgments

We wish to dedicate this paper to the memory of our colleague at the School of Earth and Space Exploration, Susan Selkirk.

P.S.K. would like to thank Ian Smail, Evan Scannapieco, and Philip Mauskopf for helpful discussions to improve this paper.

This work was also improved meaningfully as a result of discussions P.S.K. had with colleagues while at the Aspen Center for Physics, which is supported by National Science Foundation grant PHY-2210452.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with JWST program # 1176 (PEARLS; PI: R. Windhorst). The JWST data used can be found in MAST: .

R.A.W., S.H.C., and R.A.J. acknowledge support from NASA JWST Interdisciplinary Scientist grants NAG5-12460, NNX14AN10G and 80NSSC18K0200 from GSFC.

E.F.-J.A. acknowledges support from UNAM-PAPIIT project IA102023, and from CONAHCyT Ciencia de Frontera project ID: CF-2023-I-506.

This paper makes use of the following ALMA data: ADS/JAO.ALMA # 2021.1.00607.S.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This research has made extensive use of NASA’s Astrophysics Data System.

We also acknowledge the indigenous peoples of Arizona, including the Akimel O’odham (Pima) and Pee Posh (Maricopa) Indian Communities, whose care and keeping of the land has enabled us to be at ASU’s Tempe campus in the Salt River Valley, where much of our work was conducted.

# Facilities

JWST(NIRCam), ALMA, VLA

# Software

APLpy (cite: Robitaille:2012aa; Robitaille:2019aa), astropy (cite: Astropy-Collaboration:2013aa), bagpipes (cite: Carnall:2018aa), blobcat (cite: Hales:2012aa), casa (cite: McMullin:2007aa), glue (cite: Beaumont:2015aa; Robitaille:2017aa), LENSTOOL (cite: Kneib:1993aa; Kneib:1996aa; Jullo:2007aa; Jullo:2009aa), Ned Wright’s Cosmology Calculator (cite: Wright:2006aa), piXedfit (cite: Abdurrouf:2021ab; Abdurrouf:2022aa; Abdurrouf:2022ab; Abdurrouf:2022ac), photutils (cite: Bradley:2022aa)

# Lens model parameters

In Table [4](#tab:lens_bestfit), we provide the full set of best-fit gravitational lens model parameters for our characterization of the G165 cluster with lenstool, in accordance with our strategy described in §[3.1](#sec:lens_modeling).

Additionally, we supply the range in priors for each parameter, which is distributed uniformly in all cases.

For priors on the image system redshifts, these are chosen iteratively based on photometric redshift information, where we widen the prior range for parameters where previous model iterations led to their posterior distribution pushing up against the boundary conditions.

For selecting a single best-fit version of our current model, we opt for the median value of the posterior for each parameter, with the uncertainties described by the inner 68% confidence interval. This statistical measure is very likely an underestimate of the true systematic uncertainty in these parameters.

Lastly, we also provide the highest-likelihood (minimum $\chi^2$) solution. For virtually all parameters, these highest-likelihood values are contained within the 68% confidence interval from the median solution, adding some assurance to the robustness of the model.

(cite: Pascale:2024aa) examine the impact of each parameter and unknown (i.e. image system redshifts) on the measurement of magnifications and time delays, in the context of inferring $H_0$ from SN H0pe.

Finally, Fig. [15](#fig:kappa) shows the convergence map $\kappa$ (or dimensionless surface mass density) of the full G165 field from our best-fit lens model.

| Parameter | Units | Prior range | Median & $1\sigma$ uncertainty | Highest-likelihood solution |
|:--:|:--:|:--:|:--:|:--:|
| $x_1$ | \[$\ensuremath{''}$\] | \[-16.8, -6.8\] | $-13.4 \pm 0.1$ | -13.6 |
| $y_1$ | \[$\ensuremath{''}$\] | \[3.2, 13.2\] | $+9.08 \pm 0.07$ | +9.18 |
| $e_1$ |  | \[0.0, 0.85\] | $0.40 \pm 0.03$ | 0.44 |
| $\theta_1$ | \[$^{\circ}$\] | \[-90, 90\] | $-24.0 \pm 0.2$ | -23.9 |
| $r_{c1}$ | \[kpc\] | \[0, 98.4\] | $17.8 \pm 0.6$ | 16.9 |
| $\sigma_1$ | \[km s$^{-1}$\] | \[0, 800\] | $476 \pm 3$ | 473 |
| $x_2$ | \[$\ensuremath{''}$\] | \[11.3, 21.3\] | $+14.39 \pm 0.03$ | +14.37 |
| $y_2$ | \[$\ensuremath{''}$\] | \[-13.7, -3.7\] | $-8.73 \pm 0.01$ | -8.75 |
| $e_2$ |  | \[0, 0.85\] | $0.11 \pm 0.00$ | 0.11 |
| $\theta_2$ | \[$^{\circ}$\] | \[-90, 90\] | $-18.8 \pm 0.3$ | -19.1 |
| $r_{c2}$ | \[kpc\] | \[0, 98.4\] | $43.7 \pm 0.4$ | 43.5 |
| $\sigma_2$ | \[km s$^{-1}$\] | \[0, 800\] | $689 \pm 3$ | 688 |
| $\sigma_3$ | \[km s$^{-1}$\] | \[0, 250\] | $87.4 \pm 0.9$ | 86.3 |
| mag$_0$ | \[mag\] | \[17.0\]$\dagger$ | 17.0$\dagger$ |  |
| $\sigma_0$ | \[km s$^{-1}$\] | \[120\]$\dagger$ | 120$\dagger$ |  |
| $r_{\rm core,0}$ | \[kpc\] | \[0.15\]$\dagger$ | 0.15$\dagger$ |  |
| $r_{\rm cut,0}$ | \[kpc\] | \[30\]$\dagger$ | 30$\dagger$ |  |
| $z_3$ |  | \[2.0, 2.2\] | $2.11^{+0.01}_{-0.01}$ | 2.11 |
| $z_4$ |  | \[2.0, 2.2\] | $2.12^{+0.01}_{-0.01}$ | 2.11 |
| $z_6$ |  | \[2.0, 2.2\] | $2.10^{+0.01}_{-0.01}$ | 2.11 |
| $z_7$ & $z_{18}$ |  | \[1.4, 3.0\] | $1.73^{+0.01}_{-0.01}$ | 1.74 |
| $z_{10}$ |  | \[1.5, 1.9\] | $1.76^{+0.01}_{-0.01}$ | 1.73 |
| $z_{11}$ |  | \[4.0, 4.6\] | $4.60^{+0.00}_{-0.00}$ | 4.60 |
| $z_{12}$ |  | \[2.7, 3.2\] | $2.72^{+0.03}_{-0.02}$ | 2.71 |
| $z_{13}$ |  | \[3.2, 3.8\] | $3.60^{+0.02}_{-0.02}$ | 3.64 |
| $z_{14}$ |  | \[2.0, 3.0\] | $2.58^{+0.01}_{-0.01}$ | 2.57 |
| $z_{15}$ |  | \[2.0, 2.5\] | $2.11^{+0.02}_{-0.01}$ | 2.11 |
| $z_{16}$ |  | \[1.4, 1.8\] | $1.79^{+0.01}_{-0.01}$ | 1.80 |
| $z_{17}$ |  | \[5.5, 6.5\] | $5.65^{+0.05}_{-0.06}$ | 5.62 |
| $z_{19}$ |  | \[3.0, 4.0\] | $3.91^{+0.06}_{-0.08}$ | 4.00 |
| $z_{20}$ |  | \[3.0, 4.0\] | $3.96^{+0.03}_{-0.05}$ | 3.90 |
| $z_{21}$ |  | \[1.0, 4.0\] | $1.74^{+0.04}_{-0.03}$ | 1.74 |

:  Best-fit gravitational lens model parameters for the G165 cluster.

Table notes: Priors for all parameters are taken to be distributed uniformly within the provided range. $^{^\dagger}$ Parameter held fixed.

![](G165_kappa.png)

# Testing the redshift solution for DSFG-3

Given the narrow range in the geometric redshift for DSFG-3, and approximate concordance with the photometric redshift, we searched for molecular line detections in the frequency ranges covered by the ALMA observations in Band 3 and Band 4 for possible line detections; with this spectral setup, these are $\nu_{\rm B3}/{\rm GHz} \in [109.08,110.70] \cup [110.77,112.52]$ and $\nu_{\rm B4}/{\rm GHz} \in [136.46,138.25] \cup [138.59,140.39]$, respectively.

Unfortunately, the line detected by RSR is not contained within this spectral tuning.

We find no strong lines within the available spectral windows, which is consistent with our assumption of $z=2.23$.

Fig. [16](#fig:zspec) shows

the highest S/N feature, which is an unlikely but possible identification of a narrow CO(3–2) line at (observed) 110.849 GHz, corresponding to a redshift of $z_{\rm spec}=2.12 \pm 0.01$.

Given the very marginal detection (S/N $\approx 3$), we certainly do not consider this a secure, robust spectroscopic redshift on its own.

If the source is actually at $z=2.12$, there might be reason for a non-detection with the 1-hour integration with LMT, as CO(2–1) for $z=2.12$ is at 73.89 GHz, near to the low-frequency edge of the RSR bandwidth ($73 - 111$ GHz), whereas CO(3–2) would be very near the upper-frequency edge, at 110.83 GHz.

Fortunately, whether Arc 3 is at the assumed redshift of $z=2.23$ or at the secondary solution of $z=2.12$ is of relatively little import for many of the results of this work pertaining to the distribution of properties.

Perhaps the greatest impact is $\sim 30\%$ lower derived SFR$_{\rm UV-NIR}$ if $z=2.12$ is accurate, which similarly would reduce the predicted CCSN rates.

![](CO_3-2_G165_3c_spectrum_PBCOR.png)

# Calculating time delays for SN H0pe

SN H0pe and its host galaxy appear consistent with a “naked cusp" lensing morphology, with three images on the same side of the lens. This results from the source lying interior to the tangential caustic but exterior to the radial caustic in the source plane (e.g., (cite: Maller:1997aa; Bartelmann:1998aa; Keeton:1998aa; Lewis:2002aa)).

If this interpretation is correct, then it is lensed into only the three images of SN H0pe and its host galaxy (Arcs 2a, 2b, 2c) that have already been identified.

![](time_delay_jointplot.png)

With our best-fit lens model for G165, we computed the light travel-time surface as $$\begin{equation}
\tau(\boldsymbol{\theta}) = \frac{D_{\Delta t}}{c}  \cdot \phi(\boldsymbol{\theta}, \boldsymbol{\beta}),
\end{equation}$$ where $$\begin{equation}
\phi(\boldsymbol{\theta}, \boldsymbol{\beta}) = \frac{1}{2} (\boldsymbol{\theta} - \boldsymbol{\beta})^2 - \psi(\boldsymbol{\theta})^2
\end{equation}$$ following the notation of (cite: Treu:2016aa) and (cite: Treu:2022ac). Here, $\boldsymbol{\theta}$ is the set of apparent image-plane sky positions, $\boldsymbol{\beta}$ is the set of corresponding true (unlensed) source-plane positions, $\phi(\boldsymbol{\theta}, \boldsymbol{\beta})$ is the (scalar) Fermat potential, and $\psi(\boldsymbol{\theta})$ is the scaled plane-projected gravitational potential. $D_{\Delta t}$ is the time-delay distance defined as $$\begin{equation}
D_{\Delta t} \equiv (1+z_d)\frac{D_d D_s}{D_{ds}}
\end{equation}$$ for lens plane redshift $z_d$ and the angular diameter distances $D_d$, $D_s$, $D_{ds}$ between observer and lens plane, between observer and source plane, and between lens and source planes, respectively.

The Hubble constant $H_0$ is connected through $D_{\Delta t} \propto H_0^{-1}$ (cite: Suyu:2010aa).

For this reason, with a model for the lensing potential $\psi(\boldsymbol{\theta})$, and an observation of actual time delay between images through detection of a transient or variable source, one may infer $H_0$.

To propagate the uncertainty in the lens model forward to the time delay predictions, we again randomly selected 300 realizations from the MCMC sampling, and calculated the light travel times at the position of SN H0pe in images 2a, 2b, and 2c. We then calculated the delays after the first image to arrive (2a), $\Delta t_{ac}$ and $\Delta t_{ab}$. The results are shown in Fig. [17](#fig:time_delays).

As a caveat, the uncertainties on time delays may be closely dependent on the positional uncertainty assumed for the model (here, taken to be $0.03\ensuremath{''}$).

These values, along with the convergence $\kappa$ and shear $\gamma$, are reported in Table [5](#tab:timedelays). We also include our model-derived magnifications for the locations of SN H0pe, alongside the respective values derived from the photometric light curve information from (cite: Pierel:2024aa). These absolute measurements of magnification are possible only because SN H0pe is a standard candle Type Ia supernova. We find general agreement within uncertainties. As discussed by (cite: Pascale:2024aa), the fidelity of a lens model in reproducing the SN Ia-derived magnifications can be used to weight the various lens models involved in the inference of $H_0$.

We also find consistency with the predictions from many of the other lens models compiled by (cite: Pascale:2024aa) (see their Fig. 3), where the model from this work is referred to as Model 3.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Image | Model time delay $\Delta t_{x,a}^\ddagger$ | SN Ia $\Delta t_{x,a}^\dagger$ | $\mu_{\rm model}^\ddagger$ | $\mu_{\rm SN~Ia}^\dagger$ | $\kappa^\ddagger$ | $\gamma^\ddagger$ |
|  | \[days\] | \[days\] |  |  |  |  |
| SN 2a |  |  | $6.7 \pm 0.1$ | $5.1^{+1.5}_{-1.7}$ | $0.571 \pm 0.004$ | $0.186 \pm 0.002$ |
| SN 2b | $106 \pm 2$ | $117 \pm 10$ | $9.8 \pm 0.3$ | $9.2^{+3.5}_{-2.5}$ | $0.705 \pm 0.003$ | $0.434 \pm 0.004$ |
| SN 2c | $53 \pm 3$ | $68 \pm 11$ | $8.9 \pm 0.3$ | $7.4^{+1.4}_{-1.4}$ | $0.588 \pm 0.005$ | $0.243 \pm 0.002$ |

: Model-derived time delay properties for SN H0pe.

Table notes: $^{^\dagger}$ Magnifications and time delays derived from the SN Ia lightcurve determined by (cite: Pierel:2024aa) $^{^\ddagger}$ The uncertainties in these values are purely statistical and likely underestimate the true systematic uncertainties. All are based on a fiducial $H_0 = 70~{\rm km}~{\rm s}^{-1}~{\rm Mpc}^{-1}$. A more in-depth discussion, along with an investigation into the error budget of these values, is provided by (cite: Pascale:2024aa)

# Source-plane reconstruction and resolved SED fitting of high-magnification arcs as a consistency check

Fig. [18](#fig:SP_high_mag) shows the source-plane reconstructions of Arcs 1bc and 3ab, which are the highly-magnified fold-configuration images.

While these reconstructions are subject to very different effective source-plane PSFs compared to the lower-magnification counterparts in Fig. [3](#fig:SP_1a_3c), they reveal broad agreement and instill some confidence in the lens model as applied to these objects.

Figs. [19](#fig:pixbin_1bc) and [20](#fig:pixbin_3ab) show the same properties as Figs. [4](#fig:pixbin_1a) and [5](#fig:pixbin_3c), but for their high-magnification counterparts, Arcs 1bc and 3ab.

As both DSFGs barely cross over the caustic curves at their respective redshifts (Fig. [2](#fig:SP_DSFG)), only the southeasternmost portion of DSFG-1 and northwesternmost portion of DSFG-3 are triply-imaged into 1bc and 3ab, and the remaining structure is singly-imaged into the lower-magnification arcs 1a and 3c.

In the image plane, we indicate the portion of each object that gets triply-imaged using red dividing lines in Figs. [6](#fig:slit_1a) and [7](#fig:slit_3c).

This includes roughly one-third of the area of DSFG-1 studied with resolved SED fitting, and closer to one-fourth of DSFG-3.

At such small intrinsic scales (below 100 pc), it is not unreasonable to consider that the utility of SED fitting may begin to break down,

especially when criteria of energy balance between UV/optical and far-IR are imposed (cite: Smith:2018ab).

Even without this assumption, the lower average S/N of individual bins resulting in greater uncertainties and degeneracies in derived physical properties.

It is also rather difficult to interpret spatial variations

in the image plane, as the arcs are the result of a $\sim$kpc-scale source-plane region being magnified and highly distorted after lensing.

Nonetheless, there is rough agreement in the key properties of $\Sigma_{\rm SFR}$, $\Sigma_\star$, $A_V$ as we find in the corresponding regions of Arcs 1a and 3c.

Based on what we recover from this SED fitting, we identify a patchy distribution in dust attenuation $A_V$, but there is not significant variation here (although this is not a particularly robust characterization of the sub-kpc dust geometry).

Moreover, it is difficult to determine if the clumpy structure of $\Sigma_{\rm SFR}$ and $\Sigma_\star$ reveals the actual distribution of small-scale star-forming complexes, or if the variation is just the result of stochasticity in the SED fitting or inhomogeneous dust geometries (even below 100 pc scales).

![](G165_SP_3ab_RGB_ALMA_VLA.png)

![](G165_DSFG_1bc_run1_neb_map_properties.png)

![](G165_DSFG_3ab_run2_neb_map_properties.png)

# Integrated properties of SN H0pe host, Arc 2a

For ease of comparison, we also use the same choice of priors to fit the SED of Arc 2a, the host galaxy of SN H0pe.

We find that several parameters have wide posterior distributions or bimodalities, which limit our interpretations.

This may be due to different stellar populations contributing comparably to the integrated galaxy light (as revealed through the resolved SED fitting), or to degeneracies (e.g. between age and dust) that are poorly broken by the UV-NIR photometry given the shape of the SED.

Intriguingly, found $A_V = 0.9 \pm 0.2$ for Arc 2a from the Balmer decrement, which is in line with the lower-$A_V$ peak of our posterior.

Given these bimodalities, for integrated properties, we instead assume the quantities determined by , who incorporate the NIRSpec spectrum into the SED fit. This approach has a better chance at breaking these degeneracies and is thus more reliable.

![](G165_2a_BAGPIPES_summary.png)

# Simultaneous UV-FIR fitting of the spatially-integrated SED

Inclusion of the 2mm and 3mm photometry presented in this work is desirable for constraining the dust SED, but their location at the tail end of the Rayleigh-Jeans regime renders them largely inconsequential for the fit.

Instead, we fold them into a combined SED fit for Arcs 1a, 1bc, 3ab, and 3c, so that we can take advantage of unresolved photometry measured by (cite: Harrington:2016aa) from the Wide-field Infrared Survey Explorer (*WISE*) at $12/22 \mu$m (cite: Wright:2010aa), *Herschel* Spectral Photometric Imaging Receiver (SPIRE) at $250/350/500 \mu$m (cite: Griffin:2010aa), and LMT/AzTEC at 1.1mm (cite: Wilson:2008aa).

*Planck* photometry is excluded from the fit given its high confusion noise.

Then, NIRCam photometry is summed together for all four arcs to match.

Given the increased number of constraints on the SED, we include additional parameters for our bagpipes optimization, which pertain to the dust emission model (e.g., (cite: Draine:2007aa).)

These include the PAH mass fraction ($q_{\rm PAH} \in [0.5, 4.0]$), the lower cutoff of the incident starlight intensity on the dust ($U_{\rm min} \in [1, 25]$, effectively describing the dust temperature distribution), and the fraction of dust heated by $U > U_{\rm min}$ ($\gamma \in [0.01,0.99]$); these priors are all uniformly distributed, and consistent with those used by (cite: Williams:2019ab).

As the far-IR coverage captures regions of higher attenuation than just UV-NIR alone, we also expand the upper limit on the prior on dust attenuation to $A_V < 8$.

Redshift is held fixed at $z=2.236$.

The best-fit dust emission parameters are $q_{\rm PAH} = 3.9 \pm 0.2$, $U_{\rm min} = 22 \pm 2$, and $\gamma = 0.09 \pm 0.06$.

The derived magnification-corrected SFR is SFR$_{\rm UV-FIR}= 350 \pm 70~M_\odot~{\rm yr}^{-1}$.

The results are shown in

Fig. [22](#fig:SED_UV_FIR) and Table [3](#tab:SFR_SED).

The failure to fully reproduce the *Herschel*/SPIRE photometry may be due to the upper bound of $U_{\rm min}$ (and by extension, dust temperature) being insufficiently large, as bagpipes can accommodate only $U_{\rm min} \leq 25$.

Another possibility is that the 3mm photometry is contaminated non-trivially by synchrotron emission, as the radio SED is not included in the model.

We also test different choices in SFH (a single burst model and an exponential$+$burst model), but find no significant improvement over the single exponential model.

With the exponential$+$burst model, SFR reduces by $\lesssim 5$% (within statistical uncertainties).

![](G165_FULL_BAGPIPES_summary.png)

natexlab

(ref: Abdurrouf:2017aa) Abdurro’uf, & Akiyama, M. 2017, MNRAS, 469, 2806, doi: [`10.1093/mnras/stx936`](http://doi.org/10.1093/mnras/stx936)

(ref: Abdurrouf:2018aa) —. 2018, MNRAS, 479, 5083, doi: [`10.1093/mnras/sty1771`](http://doi.org/10.1093/mnras/sty1771)

(ref: Abdurrouf:2022aa) Abdurro’uf, Lin, Y.-T., Hirashita, H., et al. 2022a, ApJ, 926, 81, doi: [`10.3847/1538-4357/ac439a`](http://doi.org/10.3847/1538-4357/ac439a)

(ref: Abdurrouf:2022ab) —. 2022b, ApJ, 935, 98, doi: [`10.3847/1538-4357/ac7da4`](http://doi.org/10.3847/1538-4357/ac7da4)

(ref: Abdurrouf:2021ab) Abdurro’uf, Lin, Y.-T., Wu, P.-F., & Akiyama, M. 2021, ApJS, 254, 15, doi: [`10.3847/1538-4365/abebe2`](http://doi.org/10.3847/1538-4365/abebe2)

(ref: Abdurrouf:2022ac) —. 2022c, piXedfit: Analyze spatially resolved SEDs of galaxies, Astrophysics Source Code Library, record ascl:2207.033. [`http://ascl.net/2207.033`](http://ascl.net/2207.033)

(ref: Abdurrouf:2023aa) Abdurro’uf, Coe, D., Jung, I., et al. 2023, ApJ, 945, 117, doi: [`10.3847/1538-4357/acba06`](http://doi.org/10.3847/1538-4357/acba06)

(ref: Akhshik:2020aa) Akhshik, M., Whitaker, K. E., Brammer, G., et al. 2020, arXiv e-prints, arXiv:2008.02276. [`https://arxiv.org/abs/2008.02276`](https://arxiv.org/abs/2008.02276)

(ref: Alberts:2022ab) Alberts, S., & Noble, A. 2022, Universe, 8, 554, doi: [`10.3390/universe8110554`](http://doi.org/10.3390/universe8110554)

(ref: Algera:2024aa) Algera, H. S. B., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 6867, doi: [`10.1093/mnras/stad3111`](http://doi.org/10.1093/mnras/stad3111)

(ref: Amvrosiadis:2024aa) Amvrosiadis, A., Lange, S., Nightingale, J., et al. 2024, arXiv e-prints, arXiv:2404.01918, doi: [`10.48550/arXiv.2404.01918`](http://doi.org/10.48550/arXiv.2404.01918)

(ref: Armus:1987aa) Armus, L., Heckman, T., & Miley, G. 1987, AJ, 94, 831, doi: [`10.1086/114517`](http://doi.org/10.1086/114517)

(ref: Arrigoni-Battaia:2018ab) Arrigoni Battaia, F., Chen, C.-C., Fumagalli, M., et al. 2018, A&A, 620, A202, doi: [`10.1051/0004-6361/201834195`](http://doi.org/10.1051/0004-6361/201834195)

(ref: Astropy-Collaboration:2013aa) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Baes:2011aa) Baes, M., Verstappen, J., De Looze, I., et al. 2011, ApJS, 196, 22, doi: [`10.1088/0067-0049/196/2/22`](http://doi.org/10.1088/0067-0049/196/2/22)

(ref: Baker:2022aa) Baker, W. M., Maiolino, R., Bluck, A. F. L., et al. 2022a, MNRAS, 510, 3622, doi: [`10.1093/mnras/stab3672`](http://doi.org/10.1093/mnras/stab3672)

(ref: Baker:2022ab) Baker, W. M., Maiolino, R., Belfiore, F., et al. 2022b, arXiv e-prints, arXiv:2211.10449. [`https://arxiv.org/abs/2211.10449`](https://arxiv.org/abs/2211.10449)

(ref: Barnes:2020aa) Barnes, D. J., Kannan, R., Vogelsberger, M., & Marinacci, F. 2020, MNRAS, 494, 1143, doi: [`10.1093/mnras/staa591`](http://doi.org/10.1093/mnras/staa591)

(ref: Barnes:1992aa) Barnes, J. E., & Hernquist, L. 1992, ARA&A, 30, 705, doi: [`10.1146/annurev.aa.30.090192.003421`](http://doi.org/10.1146/annurev.aa.30.090192.003421)

(ref: Barnes:1991aa) Barnes, J. E., & Hernquist, L. E. 1991, ApJL, 370, L65, doi: [`10.1086/185978`](http://doi.org/10.1086/185978)

(ref: Barro:2016aa) Barro, G., Kriek, M., Pérez-González, P. G., et al. 2016, ApJL, 827, L32, doi: [`10.3847/2041-8205/827/2/L32`](http://doi.org/10.3847/2041-8205/827/2/L32)

(ref: Barrufet:2020aa) Barrufet, L., Pearson, C., Serjeant, S., et al. 2020, A&A, 641, A129, doi: [`10.1051/0004-6361/202037838`](http://doi.org/10.1051/0004-6361/202037838)

(ref: Bartelmann:1998aa) Bartelmann, M., & Loeb, A. 1998, ApJ, 503, 48, doi: [`10.1086/305989`](http://doi.org/10.1086/305989)

(ref: Battisti:2019aa) Battisti, A. J., da Cunha, E., Grasha, K., et al. 2019, ApJ, 882, 61, doi: [`10.3847/1538-4357/ab345d`](http://doi.org/10.3847/1538-4357/ab345d)

(ref: Beaumont:2015aa) Beaumont, C., Goodman, A., & Greenfield, P. 2015, in Astronomical Society of the Pacific Conference Series, Vol. 495, Astronomical Data Analysis Software an Systems XXIV (ADASS XXIV), ed. A. R. Taylor & E. Rosolowsky, 101

(ref: Bell:2003aa) Bell, E. F. 2003, ApJ, 586, 794, doi: [`10.1086/367829`](http://doi.org/10.1086/367829)

(ref: Belli:2019aa) Belli, S., Newman, A. B., & Ellis, R. S. 2019, ApJ, 874, 17, doi: [`10.3847/1538-4357/ab07af`](http://doi.org/10.3847/1538-4357/ab07af)

(ref: Bianchi:2011aa) Bianchi, S., & Xilouris, E. M. 2011, A&A, 531, L11, doi: [`10.1051/0004-6361/201116772`](http://doi.org/10.1051/0004-6361/201116772)

(ref: Birkin:2023ac) Birkin, J. E., Hutchison, T. A., Welch, B., et al. 2023, ApJ, 958, 64, doi: [`10.3847/1538-4357/acf712`](http://doi.org/10.3847/1538-4357/acf712)

(ref: Blain:2002aa) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J.-P., & Frayer, D. T. 2002, Phys. Rep., 369, 111, doi: [`10.1016/S0370-1573(02)00134-5`](http://doi.org/10.1016/S0370-1573(02)00134-5)

(ref: Bluck:2020aa) Bluck, A. F. L., Maiolino, R., Sánchez, S. F., et al. 2020a, MNRAS, 492, 96, doi: [`10.1093/mnras/stz3264`](http://doi.org/10.1093/mnras/stz3264)

(ref: Bluck:2020ab) Bluck, A. F. L., Maiolino, R., Piotrowska, J. M., et al. 2020b, MNRAS, 499, 230, doi: [`10.1093/mnras/staa2806`](http://doi.org/10.1093/mnras/staa2806)

(ref: Borsato:2024aa) Borsato, E., Marchetti, L., Negrello, M., et al. 2024, MNRAS, 528, 6222, doi: [`10.1093/mnras/stad3381`](http://doi.org/10.1093/mnras/stad3381)

(ref: Bournaud:2007aa) Bournaud, F., Elmegreen, B. G., & Elmegreen, D. M. 2007, ApJ, 670, 237, doi: [`10.1086/522077`](http://doi.org/10.1086/522077)

(ref: Bournaud:2008aa) Bournaud, F., Daddi, E., Elmegreen, B. G., et al. 2008, A&A, 486, 741, doi: [`10.1051/0004-6361:20079250`](http://doi.org/10.1051/0004-6361:20079250)

(ref: Bourne:2017aa) Bourne, N., Dunlop, J. S., Merlin, E., et al. 2017, MNRAS, 467, 1360, doi: [`10.1093/mnras/stx031`](http://doi.org/10.1093/mnras/stx031)

(ref: Bouwens:2020aa) Bouwens, R., González-López, J., Aravena, M., et al. 2020, ApJ, 902, 112, doi: [`10.3847/1538-4357/abb830`](http://doi.org/10.3847/1538-4357/abb830)

(ref: Bradley:2022aa) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2022, astropy/photutils: 1.6.0, 1.6.0, Zenodo, Zenodo, doi: [`10.5281/zenodo.7419741`](http://doi.org/10.5281/zenodo.7419741)

(ref: Brammer:2011aa) Brammer, G. B., Whitaker, K. E., van Dokkum, P. G., et al. 2011, ApJ, 739, 24, doi: [`10.1088/0004-637X/739/1/24`](http://doi.org/10.1088/0004-637X/739/1/24)

(ref: Briggs:1995aa) Briggs, D. S. 1995, PhD thesis, New Mexico Institute of Mining and Technology

(ref: Brinchmann:2004aa) Brinchmann, J., Charlot, S., White, S. D. M., et al. 2004, MNRAS, 351, 1151, doi: [`10.1111/j.1365-2966.2004.07881.x`](http://doi.org/10.1111/j.1365-2966.2004.07881.x)

(ref: Bushouse:2023aa) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2023, JWST Calibration Pipeline, 1.11.2, Zenodo, doi: [`10.5281/zenodo.8140011`](http://doi.org/10.5281/zenodo.8140011)

(ref: Bussmann:2013aa) Bussmann, R. S., Pérez-Fournon, I., Amber, S., et al. 2013, ApJ, 779, 25, doi: [`10.1088/0004-637X/779/1/25`](http://doi.org/10.1088/0004-637X/779/1/25)

(ref: Byun:1994aa) Byun, Y. I., Freeman, K. C., & Kylafis, N. D. 1994, ApJ, 432, 114, doi: [`10.1086/174553`](http://doi.org/10.1086/174553)

(ref: Canameras:2015aa) Cañameras, R., Nesvadba, N. P. H., Guery, D., et al. 2015, A&A, 581, A105, doi: [`10.1051/0004-6361/201425128`](http://doi.org/10.1051/0004-6361/201425128)

(ref: Calvi:2023ab) Calvi, R., Castignani, G., & Dannerbauer, H. 2023, A&A, 678, A15, doi: [`10.1051/0004-6361/202346200`](http://doi.org/10.1051/0004-6361/202346200)

(ref: Calzetti:1997ab) Calzetti, D. 1997a, in American Institute of Physics Conference Series, Vol. 408, The ultraviolet universe at low and High redshift, ed. W. H. Waller, 403–412, doi: [`10.1063/1.53764`](http://doi.org/10.1063/1.53764)

(ref: Calzetti:1997aa) Calzetti, D. 1997b, AJ, 113, 162, doi: [`10.1086/118242`](http://doi.org/10.1086/118242)

(ref: Calzetti:2000aa) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Cano-Diaz:2019aa) Cano-Dı́az, M., Ávila-Reese, V., Sánchez, S. F., et al. 2019, MNRAS, 488, 3929, doi: [`10.1093/mnras/stz1894`](http://doi.org/10.1093/mnras/stz1894)

(ref: Cano-Diaz:2016aa) Cano-Dı́az, M., Sánchez, S. F., Zibetti, S., et al. 2016, ApJL, 821, L26, doi: [`10.3847/2041-8205/821/2/L26`](http://doi.org/10.3847/2041-8205/821/2/L26)

(ref: Caputi:2021aa) Caputi, K. I., Caminha, G. B., Fujimoto, S., et al. 2021, ApJ, 908, 146, doi: [`10.3847/1538-4357/abd4d0`](http://doi.org/10.3847/1538-4357/abd4d0)

(ref: Carilli:2010aa) Carilli, C. L., Daddi, E., Riechers, D., et al. 2010, ApJ, 714, 1407, doi: [`10.1088/0004-637X/714/2/1407`](http://doi.org/10.1088/0004-637X/714/2/1407)

(ref: Carnall:2019ab) Carnall, A. C., Leja, J., Johnson, B. D., et al. 2019, ApJ, 873, 44, doi: [`10.3847/1538-4357/ab04a2`](http://doi.org/10.3847/1538-4357/ab04a2)

(ref: Carnall:2018aa) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: Carrasco:2010aa) Carrasco, E. R., Conselice, C. J., & Trujillo, I. 2010, MNRAS, 405, 2253, doi: [`10.1111/j.1365-2966.2010.16645.x`](http://doi.org/10.1111/j.1365-2966.2010.16645.x)

(ref: Carrera:2008aa) Carrera, R., Gallart, C., Aparicio, A., et al. 2008, AJ, 136, 1039, doi: [`10.1088/0004-6256/136/3/1039`](http://doi.org/10.1088/0004-6256/136/3/1039)

(ref: Casey:2016aa) Casey, C. M. 2016, ApJ, 824, 36, doi: [`10.3847/0004-637X/824/1/36`](http://doi.org/10.3847/0004-637X/824/1/36)

(ref: Casey:2014aa) Casey, C. M., Narayanan, D., & Cooray, A. 2014a, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: Casey:2014ab) Casey, C. M., Scoville, N. Z., Sanders, D. B., et al. 2014b, ApJ, 796, 95, doi: [`10.1088/0004-637X/796/2/95`](http://doi.org/10.1088/0004-637X/796/2/95)

(ref: Casey:2015aa) Casey, C. M., Cooray, A., Capak, P., et al. 2015, ApJL, 808, L33, doi: [`10.1088/2041-8205/808/2/L33`](http://doi.org/10.1088/2041-8205/808/2/L33)

(ref: Ceverino:2010aa) Ceverino, D., Dekel, A., & Bournaud, F. 2010, MNRAS, 404, 2151, doi: [`10.1111/j.1365-2966.2010.16433.x`](http://doi.org/10.1111/j.1365-2966.2010.16433.x)

(ref: Chapman:2009aa) Chapman, S. C., Blain, A., Ibata, R., et al. 2009, ApJ, 691, 560, doi: [`10.1088/0004-637X/691/1/560`](http://doi.org/10.1088/0004-637X/691/1/560)

(ref: Chapman:2004aa) Chapman, S. C., Smail, I., Windhorst, R., Muxlow, T., & Ivison, R. J. 2004, ApJ, 611, 732, doi: [`10.1086/422383`](http://doi.org/10.1086/422383)

(ref: Chen:2022ae) Chen, C.-C., Gao, Z.-K., Hsu, Q.-N., et al. 2022, ApJL, 939, L7, doi: [`10.3847/2041-8213/ac98c6`](http://doi.org/10.3847/2041-8213/ac98c6)

(ref: Cheng:2022ab) Cheng, C., Yan, H., Huang, J.-S., et al. 2022, ApJL, 936, L19, doi: [`10.3847/2041-8213/ac8d08`](http://doi.org/10.3847/2041-8213/ac8d08)

(ref: Cheng:2023aa) Cheng, C., Huang, J.-S., Smail, I., et al. 2023, ApJL, 942, L19, doi: [`10.3847/2041-8213/aca9d0`](http://doi.org/10.3847/2041-8213/aca9d0)

(ref: Chiang:2013aa) Chiang, Y.-K., Overzier, R., & Gebhardt, K. 2013, ApJ, 779, 127, doi: [`10.1088/0004-637X/779/2/127`](http://doi.org/10.1088/0004-637X/779/2/127)

(ref: Cho:2003aa) Cho, J., Lazarian, A., Honein, A., et al. 2003, ApJL, 589, L77, doi: [`10.1086/376492`](http://doi.org/10.1086/376492)

(ref: Clements:2014aa) Clements, D. L., Braglia, F. G., Hyde, A. K., et al. 2014, MNRAS, 439, 1193, doi: [`10.1093/mnras/stt2253`](http://doi.org/10.1093/mnras/stt2253)

(ref: Clements:2016aa) Clements, D. L., Braglia, F., Petitpas, G., et al. 2016, MNRAS, 461, 1719, doi: [`10.1093/mnras/stw1224`](http://doi.org/10.1093/mnras/stw1224)

(ref: Coe:2012aa) Coe, D., Umetsu, K., Zitrin, A., et al. 2012, ApJ, 757, 22, doi: [`10.1088/0004-637X/757/1/22`](http://doi.org/10.1088/0004-637X/757/1/22)

(ref: Colina:2023aa) Colina, L., Crespo Gómez, A., Álvarez-Márquez, J., et al. 2023, A&A, 673, L6, doi: [`10.1051/0004-6361/202346535`](http://doi.org/10.1051/0004-6361/202346535)

(ref: Condon:1992aa) Condon, J. J. 1992, ARA&A, 30, 575, doi: [`10.1146/annurev.aa.30.090192.003043`](http://doi.org/10.1146/annurev.aa.30.090192.003043)

(ref: Cresci:2010aa) Cresci, G., Mannucci, F., Maiolino, R., et al. 2010, Nature, 467, 811, doi: [`10.1038/nature09451`](http://doi.org/10.1038/nature09451)

(ref: Daddi:2007aa) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156, doi: [`10.1086/521818`](http://doi.org/10.1086/521818)

(ref: Daddi:2010aa) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJL, 714, L118, doi: [`10.1088/2041-8205/714/1/L118`](http://doi.org/10.1088/2041-8205/714/1/L118)

(ref: Dahlen:2012aa) Dahlen, T., Strolger, L.-G., Riess, A. G., et al. 2012, ApJ, 757, 70, doi: [`10.1088/0004-637X/757/1/70`](http://doi.org/10.1088/0004-637X/757/1/70)

(ref: Dalcanton:2004aa) Dalcanton, J. J., Yoachim, P., & Bernstein, R. A. 2004, ApJ, 608, 189, doi: [`10.1086/386358`](http://doi.org/10.1086/386358)

(ref: Dannerbauer:2014aa) Dannerbauer, H., Kurk, J. D., De Breuck, C., et al. 2014, A&A, 570, A55, doi: [`10.1051/0004-6361/201423771`](http://doi.org/10.1051/0004-6361/201423771)

(ref: Dave:2012aa) Davé, R., Finlator, K., & Oppenheimer, B. D. 2012, MNRAS, 421, 98, doi: [`10.1111/j.1365-2966.2011.20148.x`](http://doi.org/10.1111/j.1365-2966.2011.20148.x)

(ref: Dave:2010aa) Davé, R., Finlator, K., Oppenheimer, B. D., et al. 2010, MNRAS, 404, 1355, doi: [`10.1111/j.1365-2966.2010.16395.x`](http://doi.org/10.1111/j.1365-2966.2010.16395.x)

(ref: de-Jong:1985aa) de Jong, T., Klein, U., Wielebinski, R., & Wunderlich, E. 1985, A&A, 147, L6

(ref: Dekel:2014aa) Dekel, A., & Burkert, A. 2014, MNRAS, 438, 1870, doi: [`10.1093/mnras/stt2331`](http://doi.org/10.1093/mnras/stt2331)

(ref: Dekel:2009ab) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451, doi: [`10.1038/nature07648`](http://doi.org/10.1038/nature07648)

(ref: Devour:2017aa) Devour, B. M., & Bell, E. F. 2017, MNRAS, 468, L31, doi: [`10.1093/mnrasl/slx021`](http://doi.org/10.1093/mnrasl/slx021)

(ref: Devour:2019aa) —. 2019, ApJS, 244, 3, doi: [`10.3847/1538-4365/ab339c`](http://doi.org/10.3847/1538-4365/ab339c)

(ref: Donevski:2023aa) Donevski, D., Damjanov, I., Nanni, A., et al. 2023, A&A, 678, A35, doi: [`10.1051/0004-6361/202346066`](http://doi.org/10.1051/0004-6361/202346066)

(ref: Draine:2007aa) Draine, B. T., & Li, A. 2007, ApJ, 657, 810, doi: [`10.1086/511055`](http://doi.org/10.1086/511055)

(ref: Drew:2020aa) Drew, P. M., Casey, C. M., Cooray, A., & Whitaker, K. E. 2020, ApJ, 892, 104, doi: [`10.3847/1538-4357/ab7939`](http://doi.org/10.3847/1538-4357/ab7939)

(ref: Dudzeviciute:2020aa) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: Dunlop:2011aa) Dunlop, J. S. 2011, in Astronomical Society of the Pacific Conference Series, Vol. 446, Galaxy Evolution: Infrared to Millimeter Wavelength Perspective, ed. W. Wang, J. Lu, Z. Luo, Z. Yang, H. Hua, & Z. Chen, 209

(ref: Dunlop:2017aa) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861, doi: [`10.1093/mnras/stw3088`](http://doi.org/10.1093/mnras/stw3088)

(ref: Elbaz:2007aa) Elbaz, D., Daddi, E., Le Borgne, D., et al. 2007, A&A, 468, 33, doi: [`10.1051/0004-6361:20077525`](http://doi.org/10.1051/0004-6361:20077525)

(ref: Elbaz:2018aa) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110, doi: [`10.1051/0004-6361/201732370`](http://doi.org/10.1051/0004-6361/201732370)

(ref: Ellison:2021aa) Ellison, S. L., Lin, L., Thorp, M. D., et al. 2021, MNRAS, 501, 4777, doi: [`10.1093/mnras/staa3822`](http://doi.org/10.1093/mnras/staa3822)

(ref: Ellison:2018aa) Ellison, S. L., Sánchez, S. F., Ibarra-Medel, H., et al. 2018, MNRAS, 474, 2039, doi: [`10.1093/mnras/stx2882`](http://doi.org/10.1093/mnras/stx2882)

(ref: Ellison:2023aa) Ellison, S. L., Pan, H.-A., Bluck, A. F. L., et al. 2023, arXiv e-prints, arXiv:2312.03132, doi: [`10.48550/arXiv.2312.03132`](http://doi.org/10.48550/arXiv.2312.03132)

(ref: Elmegreen:2011aa) Elmegreen, B. G. 2011, ApJ, 737, 10, doi: [`10.1088/0004-637X/737/1/10`](http://doi.org/10.1088/0004-637X/737/1/10)

(ref: Elmegreen:2008aa) Elmegreen, B. G., Bournaud, F., & Elmegreen, D. M. 2008, ApJ, 688, 67, doi: [`10.1086/592190`](http://doi.org/10.1086/592190)

(ref: Engelbracht:1998aa) Engelbracht, C. W., Rieke, M. J., Rieke, G. H., Kelly, D. M., & Achtermann, J. M. 1998, ApJ, 505, 639, doi: [`10.1086/306176`](http://doi.org/10.1086/306176)

(ref: Enia:2018aa) Enia, A., Negrello, M., Gurwell, M., et al. 2018, MNRAS, 475, 3467, doi: [`10.1093/mnras/sty021`](http://doi.org/10.1093/mnras/sty021)

(ref: Enia:2020aa) Enia, A., Rodighiero, G., Morselli, L., et al. 2020, arXiv e-prints, arXiv:2001.04479. [`https://arxiv.org/abs/2001.04479`](https://arxiv.org/abs/2001.04479)

(ref: Erroz-Ferrer:2019aa) Erroz-Ferrer, S., Carollo, C. M., den Brok, M., et al. 2019, MNRAS, 484, 5009, doi: [`10.1093/mnras/stz194`](http://doi.org/10.1093/mnras/stz194)

(ref: Estrada-Carpenter:2020aa) Estrada-Carpenter, V., Papovich, C., Momcheva, I., et al. 2020, ApJ, 898, 171, doi: [`10.3847/1538-4357/aba004`](http://doi.org/10.3847/1538-4357/aba004)

(ref: Fang:2013aa) Fang, J. J., Faber, S. M., Koo, D. C., & Dekel, A. 2013, ApJ, 776, 63, doi: [`10.1088/0004-637X/776/1/63`](http://doi.org/10.1088/0004-637X/776/1/63)

(ref: Farrah:2006aa) Farrah, D., Lonsdale, C. J., Borys, C., et al. 2006, ApJL, 641, L17, doi: [`10.1086/503769`](http://doi.org/10.1086/503769)

(ref: Ferland:2017aa) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385, doi: [`10.48550/arXiv.1705.10877`](http://doi.org/10.48550/arXiv.1705.10877)

(ref: Ferrara:1991aa) Ferrara, A., Ferrini, F., Franco, J., & Barsella, B. 1991, ApJ, 381, 137, doi: [`10.1086/170636`](http://doi.org/10.1086/170636)

(ref: Finlator:2006aa) Finlator, K., Davé, R., Papovich, C., & Hernquist, L. 2006, ApJ, 639, 672, doi: [`10.1086/499349`](http://doi.org/10.1086/499349)

(ref: Forster-Schreiber:2001aa) Förster Schreiber, N. M., Genzel, R., Lutz, D., Kunze, D., & Sternberg, A. 2001, ApJ, 552, 544, doi: [`10.1086/320546`](http://doi.org/10.1086/320546)

(ref: Franx:1990aa) Franx, M., & Illingworth, G. 1990, ApJL, 359, L41, doi: [`10.1086/185791`](http://doi.org/10.1086/185791)

(ref: Frye:2023ab) Frye, B., Pascale, M., Cohen, S., et al. 2023, Transient Name Server AstroNote, 96, 1

(ref: Frye:2019aa) Frye, B. L., Pascale, M., Qin, Y., et al. 2019, ApJ, 871, 51, doi: [`10.3847/1538-4357/aaeff7`](http://doi.org/10.3847/1538-4357/aaeff7)

(ref: Frye:2024aa) Frye, B. L., Pascale, M., Pierel, J., et al. 2024, ApJ, 961, 171, doi: [`10.3847/1538-4357/ad1034`](http://doi.org/10.3847/1538-4357/ad1034)

(ref: Fujimoto:2017aa) Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83, doi: [`10.3847/1538-4357/aa93e6`](http://doi.org/10.3847/1538-4357/aa93e6)

(ref: Geach:2006aa) Geach, J. E., Smail, I., Ellis, R. S., et al. 2006, ApJ, 649, 661, doi: [`10.1086/506469`](http://doi.org/10.1086/506469)

(ref: Genzel:2014aa) Genzel, R., Förster Schreiber, N. M., Lang, P., et al. 2014, ApJ, 785, 75, doi: [`10.1088/0004-637X/785/1/75`](http://doi.org/10.1088/0004-637X/785/1/75)

(ref: Gimenez-Arteaga:2023aa) Giménez-Arteaga, C., Oesch, P. A., Brammer, G. B., et al. 2023, ApJ, 948, 126, doi: [`10.3847/1538-4357/acc5ea`](http://doi.org/10.3847/1538-4357/acc5ea)

(ref: Gomez:2010aa) Gomez, H. L., Baes, M., Cortese, L., et al. 2010, A&A, 518, L45, doi: [`10.1051/0004-6361/201014530`](http://doi.org/10.1051/0004-6361/201014530)

(ref: Gonzalez-Delgado:2016aa) González Delgado, R. M., Cid Fernandes, R., Pérez, E., et al. 2016, A&A, 590, A44, doi: [`10.1051/0004-6361/201628174`](http://doi.org/10.1051/0004-6361/201628174)

(ref: Griffin:2010aa) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3, doi: [`10.1051/0004-6361/201014519`](http://doi.org/10.1051/0004-6361/201014519)

(ref: Gullberg:2019aa) Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, MNRAS, 490, 4956, doi: [`10.1093/mnras/stz2835`](http://doi.org/10.1093/mnras/stz2835)

(ref: Hainline:2011aa) Hainline, L. J., Blain, A. W., Smail, I., et al. 2011, ApJ, 740, 96, doi: [`10.1088/0004-637X/740/2/96`](http://doi.org/10.1088/0004-637X/740/2/96)

(ref: Hales:2012aa) Hales, C. A., Murphy, T., Curran, J. R., et al. 2012, MNRAS, 425, 979, doi: [`10.1111/j.1365-2966.2012.21373.x`](http://doi.org/10.1111/j.1365-2966.2012.21373.x)

(ref: Hall:2018aa) Hall, C., Courteau, S., Jarrett, T., et al. 2018, ApJ, 865, 154, doi: [`10.3847/1538-4357/aadee1`](http://doi.org/10.3847/1538-4357/aadee1)

(ref: Hani:2020ab) Hani, M. H., Hayward, C. C., Orr, M. E., et al. 2020, MNRAS, 493, L87, doi: [`10.1093/mnrasl/slaa013`](http://doi.org/10.1093/mnrasl/slaa013)

(ref: Harikane:2019aa) Harikane, Y., Ouchi, M., Ono, Y., et al. 2019, ApJ, 883, 142, doi: [`10.3847/1538-4357/ab2cd5`](http://doi.org/10.3847/1538-4357/ab2cd5)

(ref: Harrington:2016aa) Harrington, K. C., Yun, M. S., Cybulski, R., et al. 2016, MNRAS, 458, 4383, doi: [`10.1093/mnras/stw614`](http://doi.org/10.1093/mnras/stw614)

(ref: Harrington:2021aa) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95, doi: [`10.3847/1538-4357/abcc01`](http://doi.org/10.3847/1538-4357/abcc01)

(ref: Hatsukade:2015aa) Hatsukade, B., Tamura, Y., Iono, D., et al. 2015, PASJ, 67, 93, doi: [`10.1093/pasj/psv061`](http://doi.org/10.1093/pasj/psv061)

(ref: Hayward:2012aa) Hayward, C. C., Jonsson, P., Kereš, D., et al. 2012, MNRAS, 424, 951, doi: [`10.1111/j.1365-2966.2012.21254.x`](http://doi.org/10.1111/j.1365-2966.2012.21254.x)

(ref: Hayward:2011aa) Hayward, C. C., Kereš, D., Jonsson, P., et al. 2011, ApJ, 743, 159, doi: [`10.1088/0004-637X/743/2/159`](http://doi.org/10.1088/0004-637X/743/2/159)

(ref: Hayward:2013aa) Hayward, C. C., Narayanan, D., Kereš, D., et al. 2013, MNRAS, 428, 2529, doi: [`10.1093/mnras/sts222`](http://doi.org/10.1093/mnras/sts222)

(ref: Heckman:1990aa) Heckman, T. M., Armus, L., & Miley, G. K. 1990, ApJS, 74, 833, doi: [`10.1086/191522`](http://doi.org/10.1086/191522)

(ref: Heckman:2017aa) Heckman, T. M., & Thompson, T. A. 2017, in Handbook of Supernovae, ed. A. W. Alsabti & P. Murdin, 2431, doi: [`10.1007/978-3-319-21846-5_23`](http://doi.org/10.1007/978-3-319-21846-5_23)

(ref: Helou:1985aa) Helou, G., Soifer, B. T., & Rowan-Robinson, M. 1985, ApJL, 298, L7, doi: [`10.1086/184556`](http://doi.org/10.1086/184556)

(ref: Hemmati:2014aa) Hemmati, S., Miller, S. H., Mobasher, B., et al. 2014, ApJ, 797, 108, doi: [`10.1088/0004-637X/797/2/108`](http://doi.org/10.1088/0004-637X/797/2/108)

(ref: Hennawi:2015aa) Hennawi, J. F., Prochaska, J. X., Cantalupo, S., & Arrigoni-Battaia, F. 2015, Science, 348, 779, doi: [`10.1126/science.aaa5397`](http://doi.org/10.1126/science.aaa5397)

(ref: Hernquist:1989aa) Hernquist, L. 1989, Nature, 340, 687, doi: [`10.1038/340687a0`](http://doi.org/10.1038/340687a0)

(ref: Hodge:2012aa) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11, doi: [`10.1088/0004-637X/760/1/11`](http://doi.org/10.1088/0004-637X/760/1/11)

(ref: Hodge:2020ab) Hodge, J. A., & da Cunha, E. 2020, Royal Society Open Science, 7, 200556, doi: [`10.1098/rsos.200556`](http://doi.org/10.1098/rsos.200556)

(ref: Hodge:2016aa) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: Hodge:2019aa) Hodge, J. A., Smail, I., Walter, F., et al. 2019, ApJ, 876, 130, doi: [`10.3847/1538-4357/ab1846`](http://doi.org/10.3847/1538-4357/ab1846)

(ref: Hogbom:1974aa) Högbom, J. A. 1974, A&AS, 15, 417

(ref: Holwerda:2012aa) Holwerda, B. W., Dalcanton, J. J., Radburn-Smith, D., et al. 2012, ApJ, 753, 25, doi: [`10.1088/0004-637X/753/1/25`](http://doi.org/10.1088/0004-637X/753/1/25)

(ref: Holwerda:2021aa) Holwerda, B. W., Knabel, S., Steele, R. C., et al. 2021, MNRAS, 505, 1316, doi: [`10.1093/mnras/stab1370`](http://doi.org/10.1093/mnras/stab1370)

(ref: Hopkins:2008aa) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356, doi: [`10.1086/524362`](http://doi.org/10.1086/524362)

(ref: Hounsell:2018aa) Hounsell, R., Scolnic, D., Foley, R. J., et al. 2018, ApJ, 867, 23, doi: [`10.3847/1538-4357/aac08b`](http://doi.org/10.3847/1538-4357/aac08b)

(ref: Howk:2000aa) Howk, J. C., & Savage, B. D. 2000, AJ, 119, 644, doi: [`10.1086/301210`](http://doi.org/10.1086/301210)

(ref: Hsieh:2017aa) Hsieh, B. C., Lin, L., Lin, J. H., et al. 2017, ApJL, 851, L24, doi: [`10.3847/2041-8213/aa9d80`](http://doi.org/10.3847/2041-8213/aa9d80)

(ref: Hung:2016aa) Hung, C.-L., Casey, C. M., Chiang, Y.-K., et al. 2016, ApJ, 826, 130, doi: [`10.3847/0004-637X/826/2/130`](http://doi.org/10.3847/0004-637X/826/2/130)

(ref: Ikarashi:2015aa) Ikarashi, S., Ivison, R. J., Caputi, K. I., et al. 2015, ApJ, 810, 133, doi: [`10.1088/0004-637X/810/2/133`](http://doi.org/10.1088/0004-637X/810/2/133)

(ref: Ivison:2011aa) Ivison, R. J., Papadopoulos, P. P., Smail, I., et al. 2011, MNRAS, 412, 1913, doi: [`10.1111/j.1365-2966.2010.18028.x`](http://doi.org/10.1111/j.1365-2966.2010.18028.x)

(ref: Ivison:2010ad) Ivison, R. J., Smail, I., Papadopoulos, P. P., et al. 2010, MNRAS, 404, 198, doi: [`10.1111/j.1365-2966.2010.16322.x`](http://doi.org/10.1111/j.1365-2966.2010.16322.x)

(ref: Jafariyazani:2019aa) Jafariyazani, M., Mobasher, B., Hemmati, S., et al. 2019, ApJ, 887, 204, doi: [`10.3847/1538-4357/ab5526`](http://doi.org/10.3847/1538-4357/ab5526)

(ref: Jain:2023aa) Jain, S., Tacchella, S., & Mosleh, M. 2023, arXiv e-prints, arXiv:2310.18462. [`https://arxiv.org/abs/2310.18462`](https://arxiv.org/abs/2310.18462)

(ref: Jansen:1994aa) Jansen, R. A., Knapen, J. H., Beckman, J. E., Peletier, R. F., & Hes, R. 1994, MNRAS, 270, 373, doi: [`10.1093/mnras/270.2.373`](http://doi.org/10.1093/mnras/270.2.373)

(ref: Ji:2022aa) Ji, Z., & Giavalisco, M. 2022a, ApJ, 935, 120, doi: [`10.3847/1538-4357/ac7f43`](http://doi.org/10.3847/1538-4357/ac7f43)

(ref: Ji:2022ab) —. 2022b, arXiv e-prints, arXiv:2208.04325. [`https://arxiv.org/abs/2208.04325`](https://arxiv.org/abs/2208.04325)

(ref: Ji:2023aa) Ji, Z., Williams, C. C., Tacchella, S., et al. 2023, arXiv e-prints, arXiv:2305.18518, doi: [`10.48550/arXiv.2305.18518`](http://doi.org/10.48550/arXiv.2305.18518)

(ref: Johnson:2014aa) Johnson, T. L., Sharon, K., Bayliss, M. B., et al. 2014, ApJ, 797, 48, doi: [`10.1088/0004-637X/797/1/48`](http://doi.org/10.1088/0004-637X/797/1/48)

(ref: Jullo:2009aa) Jullo, E., & Kneib, J.-P. 2009, MNRAS, 395, 1319, doi: [`10.1111/j.1365-2966.2009.14654.x`](http://doi.org/10.1111/j.1365-2966.2009.14654.x)

(ref: Jullo:2007aa) Jullo, E., Kneib, J.-P., Limousin, M., et al. 2007, New Journal of Physics, 9, 447, doi: [`10.1088/1367-2630/9/12/447`](http://doi.org/10.1088/1367-2630/9/12/447)

(ref: Kalita:2024aa) Kalita, B. S., Silverman, J. D., Daddi, E., et al. 2024, ApJ, 960, 25, doi: [`10.3847/1538-4357/acfee4`](http://doi.org/10.3847/1538-4357/acfee4)

(ref: Kamieneski:2023ab) Kamieneski, P. S., Frye, B. L., Pascale, M., et al. 2023, ApJ, 955, 91, doi: [`10.3847/1538-4357/aceb4a`](http://doi.org/10.3847/1538-4357/aceb4a)

(ref: Kamieneski:2024aa) Kamieneski, P. S., Yun, M. S., Harrington, K. C., et al. 2024, ApJ, 961, 2, doi: [`10.3847/1538-4357/acf930`](http://doi.org/10.3847/1538-4357/acf930)

(ref: Kannan:2021aa) Kannan, R., Vogelsberger, M., Marinacci, F., et al. 2021, MNRAS, 503, 336, doi: [`10.1093/mnras/stab416`](http://doi.org/10.1093/mnras/stab416)

(ref: Kassiola:1993aa) Kassiola, A., & Kovner, I. 1993, ApJ, 417, 450, doi: [`10.1086/173325`](http://doi.org/10.1086/173325)

(ref: Keel:1999aa) Keel, W. C., Cohen, S. H., Windhorst, R. A., & Waddington, I. 1999, AJ, 118, 2547, doi: [`10.1086/301139`](http://doi.org/10.1086/301139)

(ref: Keel:2001aa) Keel, W. C., & White, Raymond E., I. 2001, AJ, 122, 1369, doi: [`10.1086/322117`](http://doi.org/10.1086/322117)

(ref: Keeton:1998aa) Keeton, C. R., & Kochanek, C. S. 1998, ApJ, 495, 157, doi: [`10.1086/305272`](http://doi.org/10.1086/305272)

(ref: Keres:2005aa) Kereš, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2, doi: [`10.1111/j.1365-2966.2005.09451.x`](http://doi.org/10.1111/j.1365-2966.2005.09451.x)

(ref: Kewley:2010aa) Kewley, L. J., Rupke, D., Zahid, H. J., Geller, M. J., & Barton, E. J. 2010, ApJL, 721, L48, doi: [`10.1088/2041-8205/721/1/L48`](http://doi.org/10.1088/2041-8205/721/1/L48)

(ref: Kneib:1996aa) Kneib, J.-P., Ellis, R. S., Smail, I., Couch, W. J., & Sharples, R. M. 1996, ApJ, 471, 643, doi: [`10.1086/177995`](http://doi.org/10.1086/177995)

(ref: Kneib:1993aa) Kneib, J. P., Mellier, Y., Fort, B., & Mathez, G. 1993, A&A, 273, 367

(ref: Kokorev:2023aa) Kokorev, V., Jin, S., Magdis, G. E., et al. 2023, arXiv e-prints, arXiv:2301.04158. [`https://arxiv.org/abs/2301.04158`](https://arxiv.org/abs/2301.04158)

(ref: Koprowski:2016aa) Koprowski, M. P., Dunlop, J. S., Michałowski, M. J., et al. 2016, MNRAS, 458, 4321, doi: [`10.1093/mnras/stw564`](http://doi.org/10.1093/mnras/stw564)

(ref: Kriek:2009ab) Kriek, M., van Dokkum, P. G., Labbé, I., et al. 2009, ApJ, 700, 221, doi: [`10.1088/0004-637X/700/1/221`](http://doi.org/10.1088/0004-637X/700/1/221)

(ref: Kron:1980aa) Kron, R. G. 1980, ApJS, 43, 305, doi: [`10.1086/190669`](http://doi.org/10.1086/190669)

(ref: Kroupa:2001aa) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Labbe:2005aa) Labbé, I., Huang, J., Franx, M., et al. 2005, ApJL, 624, L81, doi: [`10.1086/430700`](http://doi.org/10.1086/430700)

(ref: Lang:2019aa) Lang, P., Schinnerer, E., Smail, I., et al. 2019, ApJ, 879, 54, doi: [`10.3847/1538-4357/ab1f77`](http://doi.org/10.3847/1538-4357/ab1f77)

(ref: Le-Bail:2023aa) Le Bail, A., Daddi, E., Elbaz, D., et al. 2023, arXiv e-prints, arXiv:2307.07599, doi: [`10.48550/arXiv.2307.07599`](http://doi.org/10.48550/arXiv.2307.07599)

(ref: Leaman:2011aa) Leaman, J., Li, W., Chornock, R., & Filippenko, A. V. 2011, MNRAS, 412, 1419, doi: [`10.1111/j.1365-2966.2011.18158.x`](http://doi.org/10.1111/j.1365-2966.2011.18158.x)

(ref: Leja:2019aa) Leja, J., Tacchella, S., & Conroy, C. 2019, ApJL, 880, L9, doi: [`10.3847/2041-8213/ab2f8c`](http://doi.org/10.3847/2041-8213/ab2f8c)

(ref: Leroy:2008aa) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782, doi: [`10.1088/0004-6256/136/6/2782`](http://doi.org/10.1088/0004-6256/136/6/2782)

(ref: Lewis:2002aa) Lewis, G. F., Carilli, C., Papadopoulos, P., & Ivison, R. J. 2002, MNRAS, 330, L15, doi: [`10.1046/j.1365-8711.2002.05260.x`](http://doi.org/10.1046/j.1365-8711.2002.05260.x)

(ref: Lilly:1999aa) Lilly, S. J., Eales, S. A., Gear, W. K. P., et al. 1999, ApJ, 518, 641, doi: [`10.1086/307310`](http://doi.org/10.1086/307310)

(ref: Limousin:2005aa) Limousin, M., Kneib, J.-P., & Natarajan, P. 2005, MNRAS, 356, 309, doi: [`10.1111/j.1365-2966.2004.08449.x`](http://doi.org/10.1111/j.1365-2966.2004.08449.x)

(ref: Limousin:2008aa) Limousin, M., Richard, J., Kneib, J. P., et al. 2008, A&A, 489, 23, doi: [`10.1051/0004-6361:200809646`](http://doi.org/10.1051/0004-6361:200809646)

(ref: Lin:2019aa) Lin, L., Pan, H.-A., Ellison, S. L., et al. 2019, ApJL, 884, L33, doi: [`10.3847/2041-8213/ab4815`](http://doi.org/10.3847/2041-8213/ab4815)

(ref: Lisenfeld:1996aa) Lisenfeld, U., Voelk, H. J., & Xu, C. 1996, A&A, 314, 745, doi: [`10.48550/arXiv.astro-ph/9605118`](http://doi.org/10.48550/arXiv.astro-ph/9605118)

(ref: Liu:2018aa) Liu, Q., Wang, E., Lin, Z., et al. 2018, ApJ, 857, 17, doi: [`10.3847/1538-4357/aab3d5`](http://doi.org/10.3847/1538-4357/aab3d5)

(ref: Liu:2023aj) Liu, Z., Silverman, J. D., Daddi, E., et al. 2023, arXiv e-prints, arXiv:2311.14809, doi: [`10.48550/arXiv.2311.14809`](http://doi.org/10.48550/arXiv.2311.14809)

(ref: Long:2023ab) Long, A. S., Casey, C. M., del P. Lagos, C., et al. 2023, ApJ, 953, 11, doi: [`10.3847/1538-4357/acddde`](http://doi.org/10.3847/1538-4357/acddde)

(ref: Long:2020aa) Long, A. S., Cooray, A., Ma, J., et al. 2020, ApJ, 898, 133, doi: [`10.3847/1538-4357/ab9d1f`](http://doi.org/10.3847/1538-4357/ab9d1f)

(ref: Lonsdale:2006aa) Lonsdale, C. J., Farrah, D., & Smith, H. E. 2006, Ultraluminous Infrared Galaxies (Springer-Verlag), 285, doi: [`10.1007/3-540-30313-8_9`](http://doi.org/10.1007/3-540-30313-8_9)

(ref: Lotz:2017aa) Lotz, J. M., Koekemoer, A., Coe, D., et al. 2017, ApJ, 837, 97, doi: [`10.3847/1538-4357/837/1/97`](http://doi.org/10.3847/1538-4357/837/1/97)

(ref: MacLow:1989aa) Mac Low, M.-M., McCray, R., & Norman, M. L. 1989, ApJ, 337, 141, doi: [`10.1086/167094`](http://doi.org/10.1086/167094)

(ref: Madau:2014aa) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Magdis:2016aa) Magdis, G. E., Bureau, M., Stott, J. P., et al. 2016, MNRAS, 456, 4533, doi: [`10.1093/mnras/stv2931`](http://doi.org/10.1093/mnras/stv2931)

(ref: Magdis:2021aa) Magdis, G. E., Gobat, R., Valentino, F., et al. 2021, A&A, 647, A33, doi: [`10.1051/0004-6361/202039280`](http://doi.org/10.1051/0004-6361/202039280)

(ref: Magnelli:2011aa) Magnelli, B., Elbaz, D., Chary, R. R., et al. 2011, A&A, 528, A35, doi: [`10.1051/0004-6361/200913941`](http://doi.org/10.1051/0004-6361/200913941)

(ref: Magnelli:2012aa) Magnelli, B., Lutz, D., Santini, P., et al. 2012, A&A, 539, A155, doi: [`10.1051/0004-6361/201118312`](http://doi.org/10.1051/0004-6361/201118312)

(ref: Maller:1997aa) Maller, A. H., Flores, R. A., & Primack, J. R. 1997, ApJ, 486, 681, doi: [`10.1086/304558`](http://doi.org/10.1086/304558)

(ref: Maoz:2012ab) Maoz, D., & Mannucci, F. 2012, PASA, 29, 447, doi: [`10.1071/AS11052`](http://doi.org/10.1071/AS11052)

(ref: Maragkoudakis:2017aa) Maragkoudakis, A., Zezas, A., Ashby, M. L. N., & Willner, S. P. 2017, MNRAS, 466, 1192, doi: [`10.1093/mnras/stw3180`](http://doi.org/10.1093/mnras/stw3180)

(ref: Martig:2009aa) Martig, M., Bournaud, F., Teyssier, R., & Dekel, A. 2009, ApJ, 707, 250, doi: [`10.1088/0004-637X/707/1/250`](http://doi.org/10.1088/0004-637X/707/1/250)

(ref: Mattila:2001aa) Mattila, S., & Meikle, W. P. S. 2001, MNRAS, 324, 325, doi: [`10.1046/j.1365-8711.2001.04255.x`](http://doi.org/10.1046/j.1365-8711.2001.04255.x)

(ref: Mattila:2012aa) Mattila, S., Dahlen, T., Efstathiou, A., et al. 2012, ApJ, 756, 111, doi: [`10.1088/0004-637X/756/2/111`](http://doi.org/10.1088/0004-637X/756/2/111)

(ref: McDonough:2023aa) McDonough, B., Curtis, O., & Brainerd, T. G. 2023, ApJ, 958, 19, doi: [`10.3847/1538-4357/acfe0b`](http://doi.org/10.3847/1538-4357/acfe0b)

(ref: McLure:2018aa) McLure, R. J., Dunlop, J. S., Cullen, F., et al. 2018, MNRAS, 476, 3991, doi: [`10.1093/mnras/sty522`](http://doi.org/10.1093/mnras/sty522)

(ref: McMullin:2007aa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Medling:2018aa) Medling, A. M., Cortese, L., Croom, S. M., et al. 2018, MNRAS, 475, 5194, doi: [`10.1093/mnras/sty127`](http://doi.org/10.1093/mnras/sty127)

(ref: Meneghetti:2017aa) Meneghetti, M., Natarajan, P., Coe, D., et al. 2017, MNRAS, 472, 3177, doi: [`10.1093/mnras/stx2064`](http://doi.org/10.1093/mnras/stx2064)

(ref: Michaowski:2012aa) Michałowski, M. J., Dunlop, J. S., Cirasuolo, M., et al. 2012, A&A, 541, A85, doi: [`10.1051/0004-6361/201016308`](http://doi.org/10.1051/0004-6361/201016308)

(ref: Michaowski:2014aa) Michałowski, M. J., Hayward, C. C., Dunlop, J. S., et al. 2014, A&A, 571, A75, doi: [`10.1051/0004-6361/201424174`](http://doi.org/10.1051/0004-6361/201424174)

(ref: Miettinen:2015aa) Miettinen, O., Novak, M., Smolčić, V., et al. 2015, A&A, 584, A32, doi: [`10.1051/0004-6361/201526589`](http://doi.org/10.1051/0004-6361/201526589)

(ref: Miley:2008aa) Miley, G., & De Breuck, C. 2008, A&ARv, 15, 67, doi: [`10.1007/s00159-007-0008-z`](http://doi.org/10.1007/s00159-007-0008-z)

(ref: Miller:2018ab) Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, Nature, 556, 469, doi: [`10.1038/s41586-018-0025-2`](http://doi.org/10.1038/s41586-018-0025-2)

(ref: Miller:2022ab) Miller, T. B., Whitaker, K. E., Nelson, E. J., et al. 2022, ApJL, 941, L37, doi: [`10.3847/2041-8213/aca675`](http://doi.org/10.3847/2041-8213/aca675)

(ref: Mishurov:2014aa) Mishurov, Y. N., Acharova, I. A., Shevchenko, M. G., & Tyshlangov, D. A. 2014, Astrophysical Bulletin, 69, 21, doi: [`10.1134/S1990341314010027`](http://doi.org/10.1134/S1990341314010027)

(ref: Molla:1997aa) Mollá, M., Ferrini, F., & Dı́az, A. I. 1997, ApJ, 475, 519, doi: [`10.1086/303550`](http://doi.org/10.1086/303550)

(ref: Mollenhoff:2006aa) Möllenhoff, C., Popescu, C. C., & Tuffs, R. J. 2006, A&A, 456, 941, doi: [`10.1051/0004-6361:20054727`](http://doi.org/10.1051/0004-6361:20054727)

(ref: Morselli:2020aa) Morselli, L., Rodighiero, G., Enia, A., et al. 2020, MNRAS, 496, 4606, doi: [`10.1093/mnras/staa1811`](http://doi.org/10.1093/mnras/staa1811)

(ref: Mosenkov:2022aa) Mosenkov, A. V., Usachev, P. A., Shakespear, Z., et al. 2022, MNRAS, 515, 5698, doi: [`10.1093/mnras/stac2112`](http://doi.org/10.1093/mnras/stac2112)

(ref: Murphy:2006aa) Murphy, E. J., Braun, R., Helou, G., et al. 2006a, ApJ, 638, 157, doi: [`10.1086/498636`](http://doi.org/10.1086/498636)

(ref: Murphy:2006ab) Murphy, E. J., Helou, G., Braun, R., et al. 2006b, ApJL, 651, L111, doi: [`10.1086/509722`](http://doi.org/10.1086/509722)

(ref: Murray:2005aa) Murray, N., Quataert, E., & Thompson, T. A. 2005, ApJ, 618, 569, doi: [`10.1086/426067`](http://doi.org/10.1086/426067)

(ref: Muzzin:2013aa) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJ, 777, 18, doi: [`10.1088/0004-637X/777/1/18`](http://doi.org/10.1088/0004-637X/777/1/18)

(ref: Narayanan:2018ab) Narayanan, D., Davé, R., Johnson, B. D., et al. 2018, MNRAS, 474, 1718, doi: [`10.1093/mnras/stx2860`](http://doi.org/10.1093/mnras/stx2860)

(ref: Nelson:2019aa) Nelson, E. J., Tadaki, K.-i., Tacconi, L. J., et al. 2019, ApJ, 870, 130, doi: [`10.3847/1538-4357/aaf38a`](http://doi.org/10.3847/1538-4357/aaf38a)

(ref: Nelson:2021aa) Nelson, E. J., Tacchella, S., Diemer, B., et al. 2021, MNRAS, 508, 219, doi: [`10.1093/mnras/stab2131`](http://doi.org/10.1093/mnras/stab2131)

(ref: Newman:2018aa) Newman, A. B., Belli, S., Ellis, R. S., & Patel, S. G. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1806.06814`](https://arxiv.org/abs/1806.06814)

(ref: Noeske:2007aa) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007a, ApJL, 660, L43, doi: [`10.1086/517926`](http://doi.org/10.1086/517926)

(ref: Noeske:2007ab) Noeske, K. G., Faber, S. M., Weiner, B. J., et al. 2007b, ApJL, 660, L47, doi: [`10.1086/517927`](http://doi.org/10.1086/517927)

(ref: Nomoto:1984aa) Nomoto, K. 1984, ApJ, 277, 791, doi: [`10.1086/161749`](http://doi.org/10.1086/161749)

(ref: Norman:1989aa) Norman, C. A., & Ikeuchi, S. 1989, ApJ, 345, 372, doi: [`10.1086/167912`](http://doi.org/10.1086/167912)

(ref: Overzier:2016aa) Overzier, R. A. 2016, A&ARv, 24, 14, doi: [`10.1007/s00159-016-0100-3`](http://doi.org/10.1007/s00159-016-0100-3)

(ref: Pacifici:2023aa) Pacifici, C., Iyer, K. G., Mobasher, B., et al. 2023, ApJ, 944, 141, doi: [`10.3847/1538-4357/acacff`](http://doi.org/10.3847/1538-4357/acacff)

(ref: Pantoni:2021ab) Pantoni, L., Massardi, M., Lapi, A., et al. 2021, MNRAS, 507, 3998, doi: [`10.1093/mnras/stab2346`](http://doi.org/10.1093/mnras/stab2346)

(ref: Pascale:2022aa) Pascale, M., Frye, B. L., Dai, L., et al. 2022, ApJ, 932, 85, doi: [`10.3847/1538-4357/ac6ce9`](http://doi.org/10.3847/1538-4357/ac6ce9)

(ref: Pascale:2024aa) Pascale, M., Frye, B. L., Pierel, J. D. R., et al. 2024, arXiv e-prints, arXiv:2403.18902. [`https://arxiv.org/abs/2403.18902`](https://arxiv.org/abs/2403.18902)

(ref: Pastrav:2013aa) Pastrav, B. A., Popescu, C. C., Tuffs, R. J., & Sansom, A. E. 2013, A&A, 553, A80, doi: [`10.1051/0004-6361/201220962`](http://doi.org/10.1051/0004-6361/201220962)

(ref: Peng:2023aa) Peng, B., Vishwas, A., Stacey, G., et al. 2023, ApJL, 944, L36, doi: [`10.3847/2041-8213/acb59c`](http://doi.org/10.3847/2041-8213/acb59c)

(ref: Pessa:2021aa) Pessa, I., Schinnerer, E., Belfiore, F., et al. 2021, A&A, 650, A134, doi: [`10.1051/0004-6361/202140733`](http://doi.org/10.1051/0004-6361/202140733)

(ref: Pessa:2022aa) Pessa, I., Schinnerer, E., Leroy, A., et al. 2022, arXiv e-prints, arXiv:2203.11971. [`https://arxiv.org/abs/2203.11971`](https://arxiv.org/abs/2203.11971)

(ref: Petrushevska:2020aa) Petrushevska, T. 2020, Symmetry, 12, 1966, doi: [`10.3390/sym12121966`](http://doi.org/10.3390/sym12121966)

(ref: Petrushevska:2018ab) Petrushevska, T., Okamura, T., Kawamata, R., et al. 2018, Astronomy Reports, 62, 917, doi: [`10.1134/S1063772918120272`](http://doi.org/10.1134/S1063772918120272)

(ref: Pierel:2024ab) Pierel, J. D. R., Newman, A. B., Dhawan, S., et al. 2024a, arXiv e-prints, arXiv:2404.02139, doi: [`10.48550/arXiv.2404.02139`](http://doi.org/10.48550/arXiv.2404.02139)

(ref: Pierel:2024aa) Pierel, J. D. R., Frye, B. L., Pascale, M., et al. 2024b, arXiv e-prints, arXiv:2403.18954. [`https://arxiv.org/abs/2403.18954`](https://arxiv.org/abs/2403.18954)

(ref: Pilkington:2012aa) Pilkington, K., Few, C. G., Gibson, B. K., et al. 2012, A&A, 540, A56, doi: [`10.1051/0004-6361/201117466`](http://doi.org/10.1051/0004-6361/201117466)

(ref: Polletta:2023aa) Polletta, M., Nonino, M., Frye, B., et al. 2023, A&A, 675, L4, doi: [`10.1051/0004-6361/202346964`](http://doi.org/10.1051/0004-6361/202346964)

(ref: Popescu:2000aa) Popescu, C. C., Misiriotis, A., Kylafis, N. D., Tuffs, R. J., & Fischera, J. 2000, A&A, 362, 138, doi: [`10.48550/arXiv.astro-ph/0008098`](http://doi.org/10.48550/arXiv.astro-ph/0008098)

(ref: Popping:2022ac) Popping, G., Pillepich, A., Calistro Rivera, G., et al. 2022, MNRAS, 510, 3321, doi: [`10.1093/mnras/stab3312`](http://doi.org/10.1093/mnras/stab3312)

(ref: Ramakrishnan:2023aa) Ramakrishnan, V., Moon, B., Im, S. H., et al. 2023, ApJ, 951, 119, doi: [`10.3847/1538-4357/acd341`](http://doi.org/10.3847/1538-4357/acd341)

(ref: Renzini:2015aa) Renzini, A., & Peng, Y.-j. 2015, ApJL, 801, L29, doi: [`10.1088/2041-8205/801/2/L29`](http://doi.org/10.1088/2041-8205/801/2/L29)

(ref: Richie:2024aa) Richie, H. M., Schneider, E. E., Abruzzo, M. W., & Torrey, P. 2024, arXiv e-prints, arXiv:2403.03711, doi: [`10.48550/arXiv.2403.03711`](http://doi.org/10.48550/arXiv.2403.03711)

(ref: Richmond:1998aa) Richmond, M. W., Filippenko, A. V., & Galisky, J. 1998, PASP, 110, 553, doi: [`10.1086/316165`](http://doi.org/10.1086/316165)

(ref: Robertson:2024aa) Robertson, C., Holwerda, B., Young, J., et al. 2024, arXiv e-prints, arXiv:2403.15619, doi: [`10.48550/arXiv.2403.15619`](http://doi.org/10.48550/arXiv.2403.15619)

(ref: Robitaille:2019aa) Robitaille, T. 2019, APLpy v2.0: The Astronomical Plotting Library in Python, 2.0, Zenodo, Zenodo, doi: [`10.5281/zenodo.2567476`](http://doi.org/10.5281/zenodo.2567476)

(ref: Robitaille:2017aa) Robitaille, T., Beaumont, C., Qian, P., Borkin, M., & Goodman, A. 2017, glueviz v0.13.1: multidimensional data exploration, 0.13.1, Zenodo, doi: [`10.5281/zenodo.1237692`](http://doi.org/10.5281/zenodo.1237692)

(ref: Robitaille:2012aa) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library. [`http://ascl.net/1208.017`](http://ascl.net/1208.017)

(ref: Robotham:2023aa) Robotham, A. S. G., D’Silva, J. C. J., Windhorst, R. A., et al. 2023, PASP, 135, 085003, doi: [`10.1088/1538-3873/acea42`](http://doi.org/10.1088/1538-3873/acea42)

(ref: Rodighiero:2011aa) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40, doi: [`10.1088/2041-8205/739/2/L40`](http://doi.org/10.1088/2041-8205/739/2/L40)

(ref: Rodney:2021ab) Rodney, S. A., Brammer, G. B., Pierel, J. D. R., et al. 2021, Nature Astronomy, doi: [`10.1038/s41550-021-01450-9`](http://doi.org/10.1038/s41550-021-01450-9)

(ref: Rowlands:2012aa) Rowlands, K., Dunne, L., Maddox, S., et al. 2012, MNRAS, 419, 2545, doi: [`10.1111/j.1365-2966.2011.19905.x`](http://doi.org/10.1111/j.1365-2966.2011.19905.x)

(ref: Rudnick:1977aa) Rudnick, L., & Owen, F. N. 1977, AJ, 82, 1, doi: [`10.1086/112001`](http://doi.org/10.1086/112001)

(ref: Rujopakarn:2011aa) Rujopakarn, W., Rieke, G. H., Eisenstein, D. J., & Juneau, S. 2011, ApJ, 726, 93, doi: [`10.1088/0004-637X/726/2/93`](http://doi.org/10.1088/0004-637X/726/2/93)

(ref: Rujopakarn:2023aa) Rujopakarn, W., Williams, C. C., Daddi, E., et al. 2023, ApJL, 948, L8, doi: [`10.3847/2041-8213/accc82`](http://doi.org/10.3847/2041-8213/accc82)

(ref: Safarzadeh:2017ab) Safarzadeh, M., Hayward, C. C., & Ferguson, H. C. 2017, ApJ, 840, 15, doi: [`10.3847/1538-4357/aa6c5b`](http://doi.org/10.3847/1538-4357/aa6c5b)

(ref: Salim:2014ab) Salim, S. 2014, Serbian Astronomical Journal, 189, 1, doi: [`10.2298/SAJ1489001S`](http://doi.org/10.2298/SAJ1489001S)

(ref: Salim:2007aa) Salim, S., Rich, R. M., Charlot, S., et al. 2007, ApJS, 173, 267, doi: [`10.1086/519218`](http://doi.org/10.1086/519218)

(ref: Salpeter:1955aa) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Sanchez:2013aa) Sánchez, S. F., Rosales-Ortega, F. F., Jungwiert, B., et al. 2013, A&A, 554, A58, doi: [`10.1051/0004-6361/201220669`](http://doi.org/10.1051/0004-6361/201220669)

(ref: Sanders:1996aa) Sanders, D. B., & Mirabel, I. F. 1996, ARA&A, 34, 749, doi: [`10.1146/annurev.astro.34.1.749`](http://doi.org/10.1146/annurev.astro.34.1.749)

(ref: Sanders:1988aa) Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325, 74, doi: [`10.1086/165983`](http://doi.org/10.1086/165983)

(ref: Sargent:2012aa) Sargent, M. T., Béthermin, M., Daddi, E., & Elbaz, D. 2012, ApJL, 747, L31, doi: [`10.1088/2041-8205/747/2/L31`](http://doi.org/10.1088/2041-8205/747/2/L31)

(ref: Scannapieco:2005aa) Scannapieco, E., & Bildsten, L. 2005, ApJL, 629, L85, doi: [`10.1086/452632`](http://doi.org/10.1086/452632)

(ref: Schaye:2015aa) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521, doi: [`10.1093/mnras/stu2058`](http://doi.org/10.1093/mnras/stu2058)

(ref: Schreiber:2018aa) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, A&A, 618, A85, doi: [`10.1051/0004-6361/201833070`](http://doi.org/10.1051/0004-6361/201833070)

(ref: Seon:2014aa) Seon, K.-i., Witt, A. N., Shinn, J.-h., & Kim, I.-j. 2014, ApJL, 785, L18, doi: [`10.1088/2041-8205/785/1/L18`](http://doi.org/10.1088/2041-8205/785/1/L18)

(ref: Sharda:2018aa) Sharda, P., Federrath, C., da Cunha, E., Swinbank, A. M., & Dye, S. 2018, MNRAS, 477, 4380, doi: [`10.1093/mnras/sty886`](http://doi.org/10.1093/mnras/sty886)

(ref: Sharma:2018aa) Sharma, S., Richard, J., Yuan, T., et al. 2018, MNRAS, 481, 1427, doi: [`10.1093/mnras/sty2352`](http://doi.org/10.1093/mnras/sty2352)

(ref: Sharon:2019ab) Sharon, C. E., Tagore, A. S., Baker, A. J., et al. 2019, ApJ, 879, 52, doi: [`10.3847/1538-4357/ab22b9`](http://doi.org/10.3847/1538-4357/ab22b9)

(ref: Shen:2003aa) Shen, S., Mo, H. J., White, S. D. M., et al. 2003, MNRAS, 343, 978, doi: [`10.1046/j.1365-8711.2003.06740.x`](http://doi.org/10.1046/j.1365-8711.2003.06740.x)

(ref: Shivaei:2015aa) Shivaei, I., Reddy, N. A., Steidel, C. C., & Shapley, A. E. 2015, ApJ, 804, 149, doi: [`10.1088/0004-637X/804/2/149`](http://doi.org/10.1088/0004-637X/804/2/149)

(ref: Shu:2018ab) Shu, Y., Bolton, A. S., Mao, S., et al. 2018, ApJ, 864, 91, doi: [`10.3847/1538-4357/aad5ea`](http://doi.org/10.3847/1538-4357/aad5ea)

(ref: Simpson:2015ab) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 81, doi: [`10.1088/0004-637X/799/1/81`](http://doi.org/10.1088/0004-637X/799/1/81)

(ref: Smail:2023aa) Smail, I., Dudzevičiūtė, U., Gurwell, M., et al. 2023, ApJ, 958, 36, doi: [`10.3847/1538-4357/acf931`](http://doi.org/10.3847/1538-4357/acf931)

(ref: Smith:2018ab) Smith, D. J. B., & Hayward, C. C. 2018, MNRAS, 476, 1705, doi: [`10.1093/mnras/sty311`](http://doi.org/10.1093/mnras/sty311)

(ref: Smith:2012aa) Smith, M., Nichol, R. C., Dilday, B., et al. 2012, ApJ, 755, 61, doi: [`10.1088/0004-637X/755/1/61`](http://doi.org/10.1088/0004-637X/755/1/61)

(ref: Snijders:2007aa) Snijders, L., Kewley, L. J., & van der Werf, P. P. 2007, ApJ, 669, 269, doi: [`10.1086/521522`](http://doi.org/10.1086/521522)

(ref: Soifer:1987aa) Soifer, B. T., Neugebauer, G., & Houck, J. R. 1987, ARA&A, 25, 187, doi: [`10.1146/annurev.aa.25.090187.001155`](http://doi.org/10.1146/annurev.aa.25.090187.001155)

(ref: Song:2023ab) Song, J., Fang, G., Lin, Z., Gu, Y., & Kong, X. 2023, arXiv e-prints, arXiv:2310.12228, doi: [`10.48550/arXiv.2310.12228`](http://doi.org/10.48550/arXiv.2310.12228)

(ref: Sorba:2015aa) Sorba, R., & Sawicki, M. 2015, MNRAS, 452, 235, doi: [`10.1093/mnras/stv1235`](http://doi.org/10.1093/mnras/stv1235)

(ref: Sorba:2018ab) —. 2018, MNRAS, 476, 1532, doi: [`10.1093/mnras/sty186`](http://doi.org/10.1093/mnras/sty186)

(ref: Speagle:2014aa) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: Spitzer:1978aa) Spitzer, L. 1978, Physical processes in the interstellar medium, doi: [`10.1002/9783527617722`](http://doi.org/10.1002/9783527617722)

(ref: Steidel:2000aa) Steidel, C. C., Adelberger, K. L., Shapley, A. E., et al. 2000, ApJ, 532, 170, doi: [`10.1086/308568`](http://doi.org/10.1086/308568)

(ref: Stein:2020ab) Stein, Y., Dettmar, R. J., Beck, R., et al. 2020, A&A, 639, A111, doi: [`10.1051/0004-6361/202037675`](http://doi.org/10.1051/0004-6361/202037675)

(ref: Stockton:1990aa) Stockton, A. 1990, in Dynamics and Interactions of Galaxies, ed. R. Wielen, 440–449

(ref: Strolger:2015aa) Strolger, L.-G., Dahlen, T., Rodney, S. A., et al. 2015, ApJ, 813, 93, doi: [`10.1088/0004-637X/813/2/93`](http://doi.org/10.1088/0004-637X/813/2/93)

(ref: Suess:2022aa) Suess, K. A., Bezanson, R., Nelson, E. J., et al. 2022, ApJL, 937, L33, doi: [`10.3847/2041-8213/ac8e06`](http://doi.org/10.3847/2041-8213/ac8e06)

(ref: Suess:2023aa) Suess, K. A., Williams, C. C., Robertson, B., et al. 2023, ApJL, 956, L42, doi: [`10.3847/2041-8213/acf5e6`](http://doi.org/10.3847/2041-8213/acf5e6)

(ref: Sun:2024aa) Sun, F., Helton, J. M., Egami, E., et al. 2024, ApJ, 961, 69, doi: [`10.3847/1538-4357/ad07e3`](http://doi.org/10.3847/1538-4357/ad07e3)

(ref: Suyu:2010aa) Suyu, S. H., Marshall, P. J., Auger, M. W., et al. 2010, ApJ, 711, 201, doi: [`10.1088/0004-637X/711/1/201`](http://doi.org/10.1088/0004-637X/711/1/201)

(ref: Swinbank:2015aa) Swinbank, A. M., Dye, S., Nightingale, J. W., et al. 2015, ApJL, 806, L17, doi: [`10.1088/2041-8205/806/1/L17`](http://doi.org/10.1088/2041-8205/806/1/L17)

(ref: Tacchella:2016aa) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016a, MNRAS, 458, 242, doi: [`10.1093/mnras/stw303`](http://doi.org/10.1093/mnras/stw303)

(ref: Tacchella:2016ab) —. 2016b, MNRAS, 457, 2790, doi: [`10.1093/mnras/stw131`](http://doi.org/10.1093/mnras/stw131)

(ref: Tacchella:2015aa) Tacchella, S., Carollo, C. M., Renzini, A., et al. 2015, Science, 348, 314, doi: [`10.1126/science.1261094`](http://doi.org/10.1126/science.1261094)

(ref: Tacchella:2018aa) Tacchella, S., Carollo, C. M., Förster Schreiber, N. M., et al. 2018, ApJ, 859, 56, doi: [`10.3847/1538-4357/aabf8b`](http://doi.org/10.3847/1538-4357/aabf8b)

(ref: Tadaki:2018aa) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613, doi: [`10.1038/s41586-018-0443-1`](http://doi.org/10.1038/s41586-018-0443-1)

(ref: Tadaki:2017ab) Tadaki, K.-i., Genzel, R., Kodama, T., et al. 2017, ApJ, 834, 135, doi: [`10.3847/1538-4357/834/2/135`](http://doi.org/10.3847/1538-4357/834/2/135)

(ref: Targett:2013aa) Targett, T. A., Dunlop, J. S., Cirasuolo, M., et al. 2013, MNRAS, 432, 2012, doi: [`10.1093/mnras/stt482`](http://doi.org/10.1093/mnras/stt482)

(ref: Thompson:2015aa) Thompson, T. A., Fabian, A. C., Quataert, E., & Murray, N. 2015, MNRAS, 449, 147, doi: [`10.1093/mnras/stv246`](http://doi.org/10.1093/mnras/stv246)

(ref: Thompson:2004aa) Thompson, T. W. J., Howk, J. C., & Savage, B. D. 2004, AJ, 128, 662, doi: [`10.1086/422485`](http://doi.org/10.1086/422485)

(ref: Thomson:2019aa) Thomson, A. P., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 883, 204, doi: [`10.3847/1538-4357/ab32e7`](http://doi.org/10.3847/1538-4357/ab32e7)

(ref: Thornley:2000aa) Thornley, M. D., Förster Schreiber, N. M., Lutz, D., et al. 2000, ApJ, 539, 641, doi: [`10.1086/309261`](http://doi.org/10.1086/309261)

(ref: Toft:2014aa) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68, doi: [`10.1088/0004-637X/782/2/68`](http://doi.org/10.1088/0004-637X/782/2/68)

(ref: Trayford:2019aa) Trayford, J. W., & Schaye, J. 2019, MNRAS, 485, 5715, doi: [`10.1093/mnras/stz757`](http://doi.org/10.1093/mnras/stz757)

(ref: Treu:2016aa) Treu, T., & Marshall, P. J. 2016, A&ARv, 24, 11, doi: [`10.1007/s00159-016-0096-8`](http://doi.org/10.1007/s00159-016-0096-8)

(ref: Treu:2022ac) Treu, T., Suyu, S. H., & Marshall, P. J. 2022, A&ARv, 30, 8, doi: [`10.1007/s00159-022-00145-y`](http://doi.org/10.1007/s00159-022-00145-y)

(ref: Tsujimoto:1997aa) Tsujimoto, T., Yoshii, Y., Nomoto, K., et al. 1997, ApJ, 483, 228, doi: [`10.1086/304215`](http://doi.org/10.1086/304215)

(ref: Tuffs:2004aa) Tuffs, R. J., Popescu, C. C., Völk, H. J., Kylafis, N. D., & Dopita, M. A. 2004, A&A, 419, 821, doi: [`10.1051/0004-6361:20035689`](http://doi.org/10.1051/0004-6361:20035689)

(ref: Umehata:2015aa) Umehata, H., Tamura, Y., Kohno, K., et al. 2015, ApJL, 815, L8, doi: [`10.1088/2041-8205/815/1/L8`](http://doi.org/10.1088/2041-8205/815/1/L8)

(ref: van-der-Kruit:1971aa) van der Kruit, P. C. 1971, A&A, 15, 110

(ref: van-der-Wel:2014aa) van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28, doi: [`10.1088/0004-637X/788/1/28`](http://doi.org/10.1088/0004-637X/788/1/28)

(ref: van-Dokkum:2010aa) van Dokkum, P. G., Whitaker, K. E., Brammer, G., et al. 2010, ApJ, 709, 1018, doi: [`10.1088/0004-637X/709/2/1018`](http://doi.org/10.1088/0004-637X/709/2/1018)

(ref: Veilleux:2020aa) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2, doi: [`10.1007/s00159-019-0121-9`](http://doi.org/10.1007/s00159-019-0121-9)

(ref: Venemans:2007aa) Venemans, B. P., Röttgering, H. J. A., Miley, G. K., et al. 2007, A&A, 461, 823, doi: [`10.1051/0004-6361:20053941`](http://doi.org/10.1051/0004-6361:20053941)

(ref: Venkatesan:1994aa) Venkatesan, T. C. A., Batuski, D. J., Hanisch, R. J., & Burns, J. O. 1994, ApJ, 436, 67, doi: [`10.1086/174881`](http://doi.org/10.1086/174881)

(ref: Vorobyov:2006aa) Vorobyov, E. I., & Shchekinov, Y. A. 2006, New A, 11, 240, doi: [`10.1016/j.newast.2005.08.004`](http://doi.org/10.1016/j.newast.2005.08.004)

(ref: Vulcani:2019aa) Vulcani, B., Poggianti, B. M., Moretti, A., et al. 2019, MNRAS, 488, 1597, doi: [`10.1093/mnras/stz1829`](http://doi.org/10.1093/mnras/stz1829)

(ref: Wang:2001aa) Wang, Q. D., Immler, S., Walterbos, R., Lauroesch, J. T., & Breitschwerdt, D. 2001, ApJL, 555, L99, doi: [`10.1086/323179`](http://doi.org/10.1086/323179)

(ref: Whitaker:2017aa) Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ, 850, 208, doi: [`10.3847/1538-4357/aa94ce`](http://doi.org/10.3847/1538-4357/aa94ce)

(ref: Whitaker:2012aa) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: Whitaker:2011aa) Whitaker, K. E., Labbé, I., van Dokkum, P. G., et al. 2011, ApJ, 735, 86, doi: [`10.1088/0004-637X/735/2/86`](http://doi.org/10.1088/0004-637X/735/2/86)

(ref: Whitaker:2015aa) Whitaker, K. E., Franx, M., Bezanson, R., et al. 2015, ApJL, 811, L12, doi: [`10.1088/2041-8205/811/1/L12`](http://doi.org/10.1088/2041-8205/811/1/L12)

(ref: Williams:2019ab) Williams, C. C., Labbe, I., Spilker, J., et al. 2019, ApJ, 884, 154, doi: [`10.3847/1538-4357/ab44aa`](http://doi.org/10.3847/1538-4357/ab44aa)

(ref: Williams:2009aa) Williams, R. J., Quadri, R. F., Franx, M., van Dokkum, P., & Labbé, I. 2009, ApJ, 691, 1879, doi: [`10.1088/0004-637X/691/2/1879`](http://doi.org/10.1088/0004-637X/691/2/1879)

(ref: Wilson:2008aa) Wilson, G. W., Austermann, J. E., Perera, T. A., et al. 2008, MNRAS, 386, 807, doi: [`10.1111/j.1365-2966.2008.12980.x`](http://doi.org/10.1111/j.1365-2966.2008.12980.x)

(ref: Windhorst:2023aa) Windhorst, R. A., Cohen, S. H., Jansen, R. A., et al. 2023, AJ, 165, 13, doi: [`10.3847/1538-3881/aca163`](http://doi.org/10.3847/1538-3881/aca163)

(ref: Wise:2023aa) Wise, E., Jogee, S., & Guo, Y. 2023, arXiv e-prints, arXiv:2312.05424, doi: [`10.48550/arXiv.2312.05424`](http://doi.org/10.48550/arXiv.2312.05424)

(ref: Wright:2006aa) Wright, E. L. 2006, PASP, 118, 1711, doi: [`10.1086/510102`](http://doi.org/10.1086/510102)

(ref: Wright:2010aa) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: Wuyts:2007aa) Wuyts, S., Labbé, I., Franx, M., et al. 2007, ApJ, 655, 51, doi: [`10.1086/509708`](http://doi.org/10.1086/509708)

(ref: Wuyts:2012aa) Wuyts, S., Förster Schreiber, N. M., Genzel, R., et al. 2012, ApJ, 753, 114, doi: [`10.1088/0004-637X/753/2/114`](http://doi.org/10.1088/0004-637X/753/2/114)

(ref: Wuyts:2013aa) Wuyts, S., Förster Schreiber, N. M., Nelson, E. J., et al. 2013, ApJ, 779, 135, doi: [`10.1088/0004-637X/779/2/135`](http://doi.org/10.1088/0004-637X/779/2/135)

(ref: Yao:2022aa) Yao, Y., Chen, G., Liu, H., et al. 2022, A&A, 661, A112, doi: [`10.1051/0004-6361/202243104`](http://doi.org/10.1051/0004-6361/202243104)

(ref: Young:2008aa) Young, D. R., Smartt, S. J., Mattila, S., et al. 2008, A&A, 489, 359, doi: [`10.1051/0004-6361:20078662`](http://doi.org/10.1051/0004-6361:20078662)

(ref: Yun:2001aa) Yun, M. S., Reddy, N. A., & Condon, J. J. 2001, ApJ, 554, 803, doi: [`10.1086/323145`](http://doi.org/10.1086/323145)

(ref: Zavala:2021aa) Zavala, J. A., Casey, C. M., Manning, S. M., et al. 2021, ApJ, 909, 165, doi: [`10.3847/1538-4357/abdb27`](http://doi.org/10.3847/1538-4357/abdb27)

(ref: Zibetti:2009aa) Zibetti, S., Charlot, S., & Rix, H.-W. 2009, MNRAS, 400, 1181, doi: [`10.1111/j.1365-2966.2009.15528.x`](http://doi.org/10.1111/j.1365-2966.2009.15528.x)

(ref: Ziegler:2022aa) Ziegler, J. J., Edwards, T. D. P., Suliga, A. M., et al. 2022, MNRAS, 517, 2471, doi: [`10.1093/mnras/stac274810.48550/arXiv.2205.07845`](http://doi.org/10.1093/mnras/stac274810.48550/arXiv.2205.07845)

(ref: Zimmerman:2024aa) Zimmerman, D. T., Narayanan, D., Whitaker, K. E., & Davè, R. 2024, arXiv e-prints, arXiv:2401.06719, doi: [`10.48550/arXiv.2401.06719`](http://doi.org/10.48550/arXiv.2401.06719)

(ref: Zolotov:2015aa) Zolotov, A., Dekel, A., Mandelker, N., et al. 2015, MNRAS, 450, 2327, doi: [`10.1093/mnras/stv740`](http://doi.org/10.1093/mnras/stv740)

(ref: Zwicky:1938aa) Zwicky, F. 1938, ApJ, 88, 529, doi: [`10.1086/144007`](http://doi.org/10.1086/144007)

[^1]: There is no widely-adopted strict definition for DSFGs, but they are generally considered to have large SFRs $\gtrsim 100~M_\odot~{\rm yr}^{-1}$ and significant quantities of dust capable of reprocessing a sizable fraction of the ultraviolet (UV) emission from young stars into the infrared.

    A subset of DSFGs, hyperluminous infrared galaxies (HyLIRGs) are more clearly defined, such that they exceed $L_{\rm IR} > 10^{13}~L_\odot$.

[^2]: The cluster has also been denoted in literature as PJ112714.5.

[^3]: Galactic coordinates are used to remain consistent with the name of the cluster, and the location of Arc 1a is chosen as it contains the entire object, in contrast with the fold image 1bc.

[^4]: <https://github.com/spacetelescope/jwst>

[^5]: <https://almascience.nrao.edu/aq/>

[^6]: Imaging with $\texttt{robust}=-1$ (i.e., closer to uniform weighting) was tested in an attempt to improve angular resolution, but S/N was insufficient to yield useful results.

[^7]: <https://projets.lam.fr/projects/lenstool/wiki>

[^8]: While several of the cluster members are detected in 6 GHz continuum, they are sufficiently far from the lensed arcs of interest to have negligible impact.

[^9]: [https://www.stsci.edu/$\sim$dcoe/trilogy](https://www.stsci.edu/~dcoe/trilogy)

[^10]: <https://pixedfit.readthedocs.io/en/latest/>

[^11]: To test this, we examined the 84th percentile of the derived $A_V$ posteriors for the DSFG-1 and DSFG-3 bins. Only 12% and 8% (respectively) exceeded $A_V > 2.5$.

[^12]: At 3 mm, we find $\sim 1.5\times$ larger sizes of $R_{e, 3{\rm mm}} = 2.6 \pm 0.3$ for both DSFGs, consistent with contribution from synchrotron (cite: Thomson:2019aa).

[^13]: The eastern NIRSpec slit from was consistent with a redshift of $z=2.2355 \pm 0.0003$, while the western slit yields $z=2.2401 \pm 0.0002$. This redshift difference is insufficient to affect the derived properties, but it is worth recalling that both components are contained within the offset range of $-1.0\ensuremath{''}$ to $0.0\ensuremath{''}$, and it is not clear yet how to visually separate them in these images.

[^14]: While the main sequence has large intrinsic scatter, this binary calculation of the areal fraction “above" vs. “below" the main sequence treats it as an exact discrete curve, in part to draw clear contrast with Arc 2 in §[4.4](#sec:SN_host_maps). In this instance, “above the main sequence" does not equate to “starbursting."

[^15]: The main sequence follows ${\rm log}[{\rm SFR}(M_\star, t)] = (0.84 \pm 0.02 - 0.026\pm 0.003 \times t)~{\rm log}M_\star - (6.51 \pm 0.24 - 0.11 \pm 0.03 \times t)$, for the age of the Universe $t$ in Gyr. This model uses a (cite: Kroupa:2001aa) IMF, consistent with our SFRs.

[^16]: Cosmological time dilation decreases the apparent rate of occurrence for SNe, $R_{\rm CC, obs} = R_{\rm CC} \cdot (1+z)^{-1}$, but it also stretches out the time for which a given supernova’s light curve is detectable.

</paper>

Write the methods card for this paper.