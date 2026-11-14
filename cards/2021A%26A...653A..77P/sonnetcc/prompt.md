# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...653A..77P\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...653A..77P",
 "title": "Cyano radical emission at small spatial scales towards massive protostars",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Paron, S.",
 "n_authors": 5,
 "arxiv_id": "2107.11426",
 "doi": "10.1051/0004-6361/202141424",
 "alma_projects_linked_by_archive": [
  "2015.1.01312.S"
 ]
}
```

Paper text:
<paper>
# Cyano radical emission at small spatial scales towards massive protostars

The cyano radical (CN), one of the first detected interstellar molecular species, is a key molecule in many astrochemical chains. Particularly, it is detected towards molecular cores, the birth places of the stars, and it is known that it is involved in the rich chemistry that takes place in these sites. At present there are not so many studies about the emission of this molecular species at small spatial scales towards massive young stellar objects. Thus, we present a high-angular resolution CN study towards a sample of massive protostars, with the aim of unveiling the spatial distribution at the small scale of the emission of this radical in relation to the star-forming processes. The interstellar CN has a strong emission line at the rest frequency 226874.764 MHz, thus, we search for observing projects in the ALMA database regarding high-mass star-forming regions observed at Band 6. The used data set was observed in the ALMA Cycle 3 with angular and spectral resolutions of 0.7$''$ and 1.13 MHz, respectively. A sample of ten high-mass star-forming regions located at the first Galactic quadrant were selected in base on that they present a clear emission of CN at the mentioned frequency. We found that the CN traces both molecular condensations and diffuse and extended gas surrounding them. In general, the molecular condensations traced by the maximums of the CN emission do not spatially coincide with the peaks of the continuum emission at 1.3 mm, which trace the molecular cores where the massive stars born. Based on the presence or lack of near-IR emission associated with such cores, we suggest that our sample is composed by sources at different stages of evolution. The CN is present at both, suggesting that this radical may be ubiquitous along the different star formation stages, and hence it may be involved in different chemical reactions occurring along the time in the formation of the stars. Additionally, other molecules such as CH$_{3}$OCHO and CH$_{2}$CHCN were detected towards the continuum peaks of some of the analyzed cores. We found that the missing flux coming from extended spatial-scales that are filtered out by the interferometer is an important issue to take into account in the analysis of some spectral features and the spatial distribution of the emission.

# Introduction

Chemical studies towards protostars are important because they provide an useful tool for investigating the physical processes involved in the formation of massive and low-mass stars (see (cite: gerner14) and (cite: jor04), respectively). In particular, the evolution of the high-mass star-forming regions is accompanied by an increasing in the chemical complexity in the molecular environment (e.g. (cite: tan14; van98)). Thus, high-mass star-forming regions are a very suitable laboratory to study astrochemistry, and particularly, the formation of complex molecules (cite: coletta20).

The cyano radical (CN), one of the first detected interstellar molecular species (cite: adams41; mckellar40), is a key molecule in many astrochemical chains. For instance, it is related to the chemistry of HCN and HNC, which are ubiquitous species in different interstellar environments (cite: loison14). Given that CN is very reactive with molecules possessing C=C double and C$\equiv$C triple bonds, it is involved in the formation of cyanopolyynes (cite: gans17), molecules observed in high-mass star-forming regions and hot cores, and proposed as ‘chemical clocks’ in determining the age of this kind of sources (cite: tani18; chap09).

From interferometric observations, the CN emission has been used to study protoplaneatry disks (cite: villa19; vanter19; oberg11) and some hot molecular cores (cite: qiu12; zapata08). (cite: beuther04), based on the investigation towards two massive star-forming regions, pointed out that CN does not trace the central molecular condensations, but mainly gas in their near vicinity. They suggested that CN appears not well suited for disk studies in massive protostars as in the case of the low-mass stars, and thus, they recommended the use of different molecules. Additionally, it was proposed that CN probes material in the boundary between the bulk protostellar envelope and its outflow cavity (cite: jor04). Besides some of the mentioned works, in the literature there are not abundant works regarding the detection of CN towards massive protostars or high-mass star-forming regions using interferometric observations. (cite: han15) presented a study of CN, HCN and HNC towards 38 high-mass star-forming regions, which included high-mass starless cores (HMSC), high-mass protostellar objects (HMPO), and HII regions, but using single-dish observations. Hence, we point out that it is necessary studying the CN emission with high-angular resolution towards a sample of massive protostars with the aim of unveiling the spatial distribution at the small scale of the emission of this molecular species in relation to the star-forming processes. The Atacama Large Millimeter Array (ALMA) database offers the opportunity to perform that.

According to the NIST database[^1], the interstellar CN has a strong emission line at the rest frequency 226874.764 MHz, corresponding to the N$=$2–1 J$=$5/2–3/2 F$=$7/2–5/2 transition, which can be blended with the F$=$5/2–3/2 and F$=$3/2–1/2 lines (at 226874.183 and 226875.896 MHz, respectively). Thus, we search for observing projects in the ALMA database regarding high-mass star-forming regions observed at Band 6. In the following section we describe the data used in this work and the source selection.

# Data and source selection

Data were obtained from the ALMA Science Archive[^2]. We used data from the project entitled ‘Tracing the evolution of massive protostars’ (Code: 2015.1.01312.S, PI: G. Fuller), that was observed in the ALMA Cycle 3 in configurations C36-2 and C36-3 in the 12 m array, at Band 6. We used the calibrated data which passed the second level of Quality Assurance (QA2). The theoretical maximum recoverable scale is about 6 arcsec. The angular resolution of this data set is about 0.7$''$, with a beam almost circular of 0.6$''$$\times$0.8$''$ (PA=82.9$^\circ$), and the spectral resolution is 1.13 MHz. The Common Astronomy Software Applications (CASA) was used to handle and analyse the data. The task *imcontsub* was used to subtract the continuum from the spectral lines and a first order polynomial was used. The 1$\sigma$ rms noise level is about 1.5 mJy beam$^{-1}$ for both the continuum and the line emission.

It is important to remark that even though the data passed the QA2 quality level, which assures a reliable calibration for a “science ready” data, the automatic pipeline imaging process may give raise to a clean image with some problems/artefacts. For example, an inappropriate setting of the parameters of the *clean* task in CASA could generate artificial dips in the spectra. Thus, we reprocessed the raw data set of sources whose spectra exhibit conspicuous dips in, or close to, the main component of the CN emission to check whether the imaging process is responsible of such spectral features. Particular care was taken with the *clean* task. The images obtained from our data reprocessing are very similar to those obtained from the archival, and hence we conclude that such absorption features are not due to the *clean*.

The ALMA programme 2015.1.01312.S observed several young high-mass embedded sources based on previous surveys of the Galactic plane that have identified large populations of candidate young massive protostars. From these sources, we selected a sample that have been observed in the spectral window in which the above mentioned CN line lies. Additionally, we selected sources whose spectra present conspicuous lines that allow us to properly identify the CN emission. The sources, with their velocities, distances, and the spatial resolution of the data in each case are presented in Table [1](#tabsources). The velocity and distance were obtained from (cite: wie12), who observed ammonia towards cold high-mass clumps in the inner Galactic disk. Given that G23.389 and G34.821 are not included in the Wienen et al.’s survey, the corresponding velocity and distance were obtained from (cite: maud15) and (cite: navarete19), respectively.

Additionally, we used near-IR data at the *Ks*-band obtained from the the UKIRT InfraRed Deep Sky Surveys (UKIDSS)[^3], release DR11, and IRAC-*Spitzer* data obtained from the Galactic Legacy Infrared Mid-Plane Survey Extraordinaire[^4].

|         |            |               |               |          |        |
|:--------|:----------:|:-------------:|:-------------:|:--------:|:------:|
| Source  |     RA     |     Dec.      |   v$_{LSR}$   | Distance | Resol. |
|         |  (J2000)   |    (J2000)    | (km s$^{-1}$) |  (kpc)   |  (pc)  |
| G13.656 | 18:17:24.2 | $-$17:22:12.6 |     47.0      |   4.1    | 0.014  |
| G18.825 | 18:26:58.8 | $-$12:44:43.9 |     62.9      |   4.3    | 0.014  |
| G20.747 | 18:29:16.3 | $-$10:52:10.7 |     59.0      |   3.9    | 0.013  |
| G20.762 | 18:29:12.1 | $-$10:50:34.8 |     57.0      |   3.9    | 0.013  |
| G23.389 | 18:33:14.3 | $-$08:23:57.6 |     75.4      |   4.5    | 0.015  |
| G24.464 | 18:35:11.2 | $-$07:26:31.7 |     119.0     |   6.2    | 0.021  |
| G29.862 | 18:45:59.5 | $-$02:45:06.8 |     100.0     |   5.6    | 0.019  |
| G30.198 | 18:47:03.0 | $-$03:30:35.9 |     105.9     |   5.9    | 0.020  |
| G33.133 | 18:52:08:1 | $+$00:08:12.9 |     76.0      |   4.5    | 0.015  |
| G34.821 | 18:53:37.9 | $+$01:50:28.7 |     56.5      |   1.6    | 0.005  |

: Sample of studied sources

# Results

![](CN-Espectros.ps)

To identify CN lines, from the data cubes we extracted spectra of the averaged emission obtained from regions of about 5$^{\prime\prime}$ in radius centered in each source. They are presented in Fig. [1](#cnLinea). The frequency was converted to rest frequency using the velocities listed in Table [1](#tabsources), and it is displayed the frequency range 226860–226900 MHz, in which according to the NIST database, only appears lines of CN, except for one weak line of CH$_{3}$OCHO at 226862.239 MHz. The strongest emission in all cases correspond to the CN N$=$2–1 J$=$5/2–3/2 F$=$7/2–5/2 transition, which as mentioned above, it may be blended with the weaker F$=$5/2–3/2 and F$=$3/2–1/2 lines, but the spectral resolution of the data do not allow us to resolve them properly. Additionally, the CN lines N$=$2–1 J$=$5/2–3/2, F$=$3/2–3/2 and F$=$1/2–1/2 at 226887.399 and 226892.151 MHz, respectively, appear clearly in all spectra. In some cases (see spectra of sources G13.656, G20.747, G24.464, and G33.133), the main component presents probably absorption or self-absorption features. This will be specially discussed below.

To appreciate the spatial distribution of the CN emission, we present in Fig. [2](#cnAve) maps of the CN emission averaged along the frequency interval of the main component. Additionally, the continuum emission at 1.3 mm is displayed in contours. Source G18.825 does not present continuum emission above the noise level. Given that we are presenting here the spectrum of the millimeter emission of source G29.862, we point out that in a previous work, in which we performed a detailed multiwavelength study of this source (see (cite: areal20)), the CN line was misinterpreted as CH$_3$OCHO (erratum in preparation).

![image](figG13.656.eps) ![image](figG18.825.eps) ![image](figG20.747.eps) ![image](figG20.762.eps) ![image](figG23.389.eps) ![image](figG24.464.eps) ![image](figG29.862.eps) ![image](figG30.198.eps) ![image](figG33.133.eps) ![image](figG34.821.eps)

Table [2](#contparams) presents the parameters of the cores observed at 1.3 mm obtained from a two dimensional Gaussian fitting. The peak intensity and the integrated flux density corrected for primary beam response are presented in Cols. 2 and 3, the source size in arcsec deconvolved from beam is presented in Col. 4, and in Col. 5, a rough estimate of the core size in astronomical units considering the average between the size of the semi-axes presented in Col. 4 and the distances listed in Table [1](#tabsources). The source of the errors in the size is mainly the uncertainties in the distances, and it can be about 20$\%$.

|             |                   |               |                     |      |
|:------------|:-----------------:|:-------------:|:-------------------:|:----:|
| Core        |    $I_{peak}$     |      $S$      |    $\theta_{s}$     | Size |
|             | (mJy beam$^{-1}$) |     (mJy)     | ($^{\prime\prime}$) |  au  |
| G13.656-mm1 |   114.0$\pm$5.7   |  224$\pm$16   |  0.82$\times$0.64   | 3000 |
| G20.747-mm1 |   22.2$\pm$1.4    | 69.6$\pm$5.8  |  1.48$\times$0.73   | 4100 |
| G20.747-mm2 |   10.4$\pm$1.0    | 25.5$\pm$3.4  |  1.27$\times$0.48   | 3400 |
| G20.762-mm1 |   17.1$\pm$2.2    | 43.9$\pm$7.8  |  1.87$\times$0.28   | 4200 |
| G20.762-mm2 |   11.5$\pm$1.0    | 18.7$\pm$2.6  |  0.87$\times$0.36   | 2400 |
| G23.389-mm1 |   44.4$\pm$2.1    | 91.5$\pm$6.0  |  0.91$\times$0.68   | 3500 |
| G24.464-mm1 |   24.9$\pm$2.4    |  112$\pm$13   |  1.63$\times$1.04   | 8300 |
| G29.862-mm1 |   26.2$\pm$1.9    | 51.6$\pm$5.3  |  0.77$\times$0.66   | 4000 |
| G29.862-mm2 |   10.0$\pm$1.1    | 30.4$\pm$4.4  |  0.80$\times$0.39   | 3300 |
| G30.198-mm1 |   12.6$\pm$1.5    | 40.2$\pm$6.1  |  1.60$\times$0.62   | 6500 |
| G33.133-mm1 |   11.4$\pm$1.6    | 30.3$\pm$5.8  |  1.15$\times$0.72   | 4200 |
| G33.133-mm2 |   102.4$\pm$4.9   |  207$\pm$14   |  0.85$\times$0.56   | 3100 |
| G33.133-mm3 |   67.8$\pm$2.9    | 113.1$\pm$7.1 |  0.72$\times$0.47   | 2600 |
| G33.133-mm4 |   22.2$\pm$1.2    | 35.6$\pm$3.0  |  0.85$\times$0.28   | 2500 |
| G34.821-mm1 |   24.7$\pm$2.4    | 64.0$\pm$8.4  |  1.03$\times$0.81   | 1500 |
| G34.821-mm2 |   16.1$\pm$0.4    | 21.7$\pm$0.8  |  0.49$\times$0.32   | 650  |

: Parameters of the 1.3 mm continuum cores indicated in Fig. [2](#cnAve).

The near-IR emission usually is useful to identify the central point-like sources of the young stellar objects (YSOs) and traces diffuse emission arising mainly from warm dust and scattered light in the material surrounding the protostar(s), particularly in cavities carved out by jets on an infalling envelope of material (e.g. (cite: muze13; bik06; bik05)). Even though the near-IR observations can sometimes miss deeply embedded protostars, the lack of near-IR emission or a point-like source at this wavelength in a molecular core can indicate that it is an starless core, which represents the transition between a diffuse molecular cloud and the next generation of stars to form therein (cite: schnee12). Thus, it is interesting to analyze the *Ks*-band emission in comparison with the ALMA data with the aim of finding any connection relating the extended CN and near-IR emissions, and near-IR point-like sources with the 1.3 mm continuum cores. This comparison is presented in Fig. [3](#cnIR) for each source. Additionally, in order to make a similar comparison, but in a larger spatial scale, in Fig. [4](#Spitzer) we present similar panels as presented in Fig. [3](#cnIR) but using the 3.6, 4.5, and 8 $\mu$m emission observed with *Spitzer*-IRAC. While in some cases the emission is saturated, this is still useful to analyze the sources and the surrounding medium.

![image](figIRg13.eps) ![image](figIRg18.eps) ![image](figIRg20.eps) ![image](figIRg20.762.eps) ![image](figIRg23.eps) ![image](figIRg24.eps) ![image](figIRg29.eps) ![image](figIRg30.eps) ![image](figIRg33.eps) ![image](figIRg34.eps)

![image](Spitzer-13656.eps) ![image](Spitzer-18825.eps) ![image](Spitzer-20747.eps) ![image](Spitzer-20762.eps) ![image](Spitzer-23389.eps) ![image](Spitzer-24464.eps) ![image](Spitzer-29862.eps) ![image](Spitzer-30198.eps) ![image](Spitzer-33133.eps) ![image](Spitzer-34821.eps)

# Discussion

A first important result is that by analyzing the spatial morphology of the CN emission at each source (see Fig. [2](#cnAve)), we can conclude that the CN traces both molecular condensations and diffuse and extended gas surrounding them. It is worth noting that, in general, these condensations traced by the maximums of the CN emission do not spatially coincide with the peaks of the continuum emission at 1.3 mm, that may have contributions from both ionized gas emission and from the dust (cite: hernandez14) usually associated with the smallest structures related to star formation. This phenomenon was also observed towards IRAS 20293+3952 by (cite: beuther04) using interferometric data of the CN N=1–0 line with a similar angular resolution as the data presented in this work. The authors found that the CN emission avoids the core peaks traced by the millimeter continuum emission, and based on that optical depth effects appear to be negligible, they suggest two likely main causes for the lack of CN emission towards the cores: (1) the source is too deeply embedded to excite the surface layers of the potential disk, and (2) the source is in such an early evolutionary stage that it does not generate enough UV photons to produce CN emission. Taking into account that some spectra presented in Fig. [1](#cnLinea) show probably absorption or self-absorption features, and considering the works of (cite: qiu12) and (cite: zapata08) in which the CN emission presents kinematical indications of infalling envelopes of gas, we point out that the non coincidence between the CN bulk emission and the cores traced by the continuum deserves a deeper analysis (see Sect. [4.1](#sptabs)).

From Fig. [3](#cnIR), it can be observed that in five sources (G20.762, G23.389, G29.862, G30.198, and G34.821) the continuum at 1.3 mm coincides with a point-like source (or almost point-like) at the near-IR, while in the others sources, there is not any near-IR emission associated with the 1.3 mm continuum. This suggests that our core sample is likely composed by regions at different stages of evolution in star formation: YSOs already emitting at the near-IR, and the ‘IR quiet’ sources representing YSOs in an earlier stage of evolution, or even, starless cores (e.g. (cite: motte18; schnee12)).

The difference in the evolutionary stages of the sources can be also appreciated in Fig. [4](#Spitzer). The IR emission obtained from *Spitzer*-IRAC shows that the above mention more evolved sources present point-like morphologies in these bands. Moreover, the excess in 8 $\mu$m suggests photodissociated gas due ultraviolet photons from young stars. In the case of G13.656 it is important to note that, as also shown in Fig. [3](#cnIR), there is a point-like source in the field not related to the CN emission and the 1.3 mm continuum source.

It is important to remark that in all cases, extended CN emission appears. In the cases that we observe a point-like source at near-IR related to the 1.3 mm continuum, the related CN should be tracing gas in the near vicinity of the protostar as proposed by (cite: beuther04) and (cite: jor04), and in the case of the ‘IR quiet’ sources, the CN emission may arise from a molecular core in a pre-stellar phase. Indeed, it can be observed that in regions with near-IR point-like sources associated with the 1.3 mm continuum, the morphology of the CN emission appears, in general, more localized than in the ‘IR quite’ sources. Whatever, we conclude that the presence of CN may be ubiquitous along the different star formation stages.

## Analysis of sources with spectral absorption features

The spectra obtained towards sources G13.656, G20.747, G24.464, and G33.133 present some absorption features (see Fig. [2](#cnAve)), and hence we decided to analyze them in more detail. Firstly, we note that these sources are those that their continuum cores are not associated with near-IR sources (see Fig. [3](#cnIR)) suggesting that, as mention above, they can be cores in a pre-stellar phase. In that sense, the absorption features could be due to high optical depth effects. The cores with IR sources may have lower densities than the ‘IR quiet’ cores because outflow activity could have generated cavities in the molecular envelopes (cite: wheel12), and the high optical depth effects affecting the CN emission, if there are any, are not so evident.

In addition, the spectra may present absorption features like regular or inverse P-cygni profiles, indicating expanding gas or that a gaseous envelope is falling into an accreting object as observed in CN transitions by (cite: qiu12) and (cite: zapata08). If the absorption features appear repeatedly along the observed frequency/velocity range, also it could be occurring absorption in the diffuse gas along the line of sight against a continuum source. (cite: godard10) studied this phenomenon towards star-forming regions using lines of HCO$^{+}$, HCN, HNC, and CN from single dish observations.

As mention in Sect. 2, we discarded that such absorption features are due to the imaging process. However, it is important to take into account that they also could be due to instrumental effects. The interferometric emission not combined with single dish data can be affected by the missing flux coming from more extended spatial-scales that are filtered out by the interferometer that can not be recovered even with the most accurate imaging process. This issue can produce not only missing flux but also such absorption features (e.g. (cite: rodon12; beuther04)). Hence, it is necessary to analyze this possibility, or at least to take it into account, before to conclude anything about the nature of the observed spectral absorptions. Thus, for each of the mentioned sources, we analyze the spectra at the positions of the continuum cores.

### At core G13.656-mm1

Figure [5](#mm13) shows the spectrum obtained from a circle of 1.5$''$ in radius at the position of G13.656-mm1. It can be observed a very complex spectrum in which a quite deep and narrow absorption feature related to CN appears at 226877 MHz. Additionally, it can be observed emission lines of CH$_3$OCHO (transitions 20(1,19)–19(1,18)E and A), and according to the NIST database, CH$_{2}$CHCN (transition $^{1}\nu_{11}$ 24(2,23)–23(2,22)), which are complex molecules usually detected towards hot molecular cores and pre-stellar cores (cite: jim16; herbst09; frie08). The CH$_{2}$CHCN is a complex cyanide whose observation and analysis, among other cyanides, can be used as a chemical clock of hot cores (cite: allen18). Particularly, the CN is important for the formation of this molecular species, because it results from the reaction between CN and ethylene (cite: agundez08; herbst90).

![](G13656-mm1-CN-cont.eps)

Even though the absorption feature at 226877 MHZ is narrow, it could be interpreted as a P-cygni profile suggesting expanding gas in this molecular core. However, we cannot discard that it could be due to the instrumental effect discussed above.

### At cores G20.747-mm1/2

Figure [6](#mm20) displays the spectra obtained towards cores G20.747-mm1 and -mm2 from a circle of 1.2$''$ in radius. In both spectra, an absorption feature related to the CN main component appears at 226877 MHz suggesting a P-cygni profile, and in the case of core G20.742-mm2, the CN main component has a dip at about 226873 MHz, which could be explained as a self-absorption suggesting that the emission is optically thick. As in the above case, we cannot discard that the P-cygni like feature is due to the mentioned instrumental effect. But the dip at the CN main component coincides exactly with the systemic velocity of the source, suggesting that it could be due to a high optical depth.

The profile of G20.747-mm1 presents an small absorption at 226838 MHz, which does not appear in others regions, showing that it is not due to an instrumental effect and it should be real. The frequency of this absorption is close to the that of the CH$_{2}$CHCN transition mentioned in the case of core G13.656-mm1, and hence, we wonder if it may be due to absorption in a molecular envelope containing this molecular species against the bright continuum.

![image](G20747-mm1-CN-cont.eps) ![image](G20747-mm2-CN-cont.eps)

### At core G24.464-mm1

The spectrum obtained from a circle of 1.3$''$ in radius at the position of core G24.464-mm1 is presented in Fig. [7](#mm24). It presents a conspicuous absorption dip at 226874 MHz, very close to the systemic velocity of the source, suggesting that it could be due to high optical depths, but missing flux coming from more extended spatial-scales filtered out by the interferometer cannot be discarded.

![](G24464-mm1-CN-cont.eps)

### At cores G33.133-mm1/2/3 

Spectra obtained from a circle of 1$^{\prime\prime}$ in radius towards cores G33.133-mm1, -mm2, and -mm3 are displayed in Fig. [8](#mm33). All the spectra present absorption at the main CN line. In the cases of G133.133-mm2 and -mm3 it could be due to absorption in a molecular envelope against the bright continuum. Again, missing flux produced in the interferometric observation cannot be discarded in any of these three cores. Emission of CH$_{3}$OCHO is evident in G33.133-mm2 and -mm3. From the spectra obtained towards these cores, we can say that it is clear that the non-coincidence between CN maximums and the continuum cores can be due to a combination of physical absorption with the described instrumental issue.

The spectrum of G33.133-mm2 presents a conspicuous absorption at 226856 MHz, which also appears in the spectrum of G33.133-mm1. This absorption does not seem to be produced by instrumental effects. It should be real, and we wonder the same possibility as in the case of the absorption found in G20.747-mm1.

![image](G33133-mm1-CN-cont.eps) ![image](G33133-mm2-CN-cont.eps) ![image](G33133-mm3-CN-cont.eps)

In conclusion, in most of the analyzed absorption features cannot be discarded that they are produced, totally, or in part, by the missing flux coming from more extended spatial-scales that are filtered out by the interferometer. In the case of the other sources, i.e. the sources that does not present any absorption feature in the spectra shown in Fig. [1](#cnLinea), we inspect the emission at the position of the associated 1.3 mm continuum cores, and they do not present any important absorption feature. It is possible that as these sources could be more evolved, given that they present near-IR point-like sources, the surrounding molecular envelopes at the more extended spatial-scales can be more diluted/evacuated due to the action of winds and outflows, and hence, the mentioned instrumental effect and/or the probable optical depth effects are not so notorious.

Finally, we found that in cores with the largest integrated flux density at 1.3 mm continuum emission (cores G13.656-mm1, G24.464-mm1, and G33.133-mm2) the deepest absorption features in the whole field of view related to the CN emission positionally coincides with the peaks of the continuum emission. This suggests that high optical depth effects can be combined with the discussed instrumental issue.

# Summary and concluding remarks

Given that the CN radical is very reactive with molecules possessing C=C double and C$\equiv$C triple bonds, it is involved in the formation of complex molecules in dark clouds, and in particular, in those related to star-forming processes. Hence, the study of its emission at small spatial scales towards massive protostars is important. Using high-angular resolution data we investigate the CN emission in a sample of ten massive young stellar objects located at the first Galactic quadrant, and the main results found are summarized as follows.

\(a\) All analyzed sources present emission of CN in the transitions N$=$2–1 J$=$5/2–3/2 F$=$7/2–5/2, F$=$3/2–3/2 and F$=$1/2–1/2. We observe that the CN traces both molecular condensations and diffuse and extended gas surrounding them.

\(b\) In general, the molecular condensations traced by the maximums of the CN emission do not spatially coincide with the peaks of the continuum emission at 1.3 mm as found in other works.

\(c\) Our sample of sources are divided in those that present near-IR emission associated with the continuum at 1.3 mm, and those that are ‘IR quiet’ sources, suggesting that they are protostellar objects at different stages of evolution. The CN is present at both, suggesting that this radical may be ubiquitous along the different star formation stages, and hence it may be involved in different chemical reactions occurring along the time in the formation of the stars. For instance, the CN participates in the formation of vinyl cyanide (CH$_{2}$CHCN), molecule detected in core G13.656-mm1.

Finally, it is worth noting that a molecular line emission analysis at such small spatial scales can be affected by the missing flux coming from more extended spatial-scales that are filtered out by the interferometer. This is an important issue because it can introduce artificial absorption features in the spectra that can be misinterpreted. We found that ‘IR-quite’ sources are in general more affected by this issue, and we suggest that in the more evolved sources, the surrounding molecular envelopes at the more extended spatial-scales can be more diluted/evacuated due to the action of winds and outflows, and hence, this effect is not so notorious. We cannot discard high optical depth effects combined with missing flux. Interferometric observations of the analyzed CN line in a more compact configuration would be useful to properly evaluate this issue.

# Acknowledgements

We thank the anonymous referee for her/his very useful comments. A.M. and M.B.A. are doctoral fellows of CONICET, Argentina. S.P. and M.O. are members of the Carrera del Investigador Cientı́fico of CONICET, Argentina. This work is based on the following ALMA data: 2015.1.01312.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

37 natexlab

(ref: adams41) Adams, W. S. 1941, ApJ, 93, 11

(ref: agundez08) Agúndez, M., Fonfrı́a, J. P., Cernicharo, J., Pardo, J. R., & Guélin, M. 2008, A&A, 479, 493

(ref: allen18) Allen, V., van der Tak, F. F. S., & Walsh, C. 2018, A&A, 616, A67

(ref: areal20) Areal, M. B., Paron, S., Fariña, C., et al. 2020, A&A, 641, A104

(ref: villa19) Artur de la Villarmois, E., Kristensen, L. E., & Jørgensen, J. K. 2019, A&A, 627, A37

(ref: beuther04) Beuther, H., Schilke, P., & Wyrowski, F. 2004, ApJ, 615, 832

(ref: bik05) Bik, A., Kaper, L., Hanson, M. M., & Smits, M. 2005, A&A, 440, 121

(ref: bik06) Bik, A., Kaper, L., & Waters, L. B. F. M. 2006, A&A, 455, 561

(ref: chap09) Chapman, J. F., Millar, T. J., Wardle, M., Burton, M. G., & Walsh, A. J. 2009, MNRAS, 394, 221

(ref: coletta20) Coletta, A., Fontani, F., Rivilla, V. M., et al. 2020, A&A, 641, A54

(ref: frie08) Friedel, D. N. & Snyder, L. E. 2008, ApJ, 672, 962

(ref: gans17) Gans, B., Boyé-Péronne, S., Garcia, G. A., et al. 2017, The Journal of Physical Chemistry Letters, 8, 4038, pMID: 28796511

(ref: gerner14) Gerner, T., Beuther, H., Semenov, D., et al. 2014, A&A, 563, A97

(ref: godard10) Godard, B., Falgarone, E., Gerin, M., Hily-Blant, P., & de Luca, M. 2010, A&A, 520, A20

(ref: han15) Han, X. H., Zhou, J. J., Wang, J. Z., et al. 2015, A&A, 576, A131

(ref: herbst90) Herbst, E. & Leung, C. M. 1990, A&A, 233, 177

(ref: herbst09) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: hernandez14) Hernández-Hernández, V., Zapata, L., Kurtz, S., & Garay, G. 2014, ApJ, 786, 38

(ref: jim16) Jiménez-Serra, I., Vasyunin, A. I., Caselli, P., et al. 2016, ApJL, 830, L6

(ref: jor04) Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2004, A&A, 416, 603

(ref: loison14) Loison, J.-C., Wakelam, V., & Hickson, K. M. 2014, MNRAS, 443, 398

(ref: maud15) Maud, L. T., Lumsden, S. L., Moore, T. J. T., et al. 2015, MNRAS, 452, 637

(ref: mckellar40) McKellar, A. 1940, PASP, 52, 187

(ref: motte18) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41

(ref: muze13) Muzerolle, J., Furlan, E., Flaherty, K., Balog, Z., & Gutermuth, R. 2013, Nature, 493, 378

(ref: navarete19) Navarete, F., Leurini, S., Giannetti, A., et al. 2019, A&A, 622, A135

(ref: oberg11) Öberg, K. I., Qi, C., Fogel, J. K. J., et al. 2011, ApJ, 734, 98

(ref: qiu12) Qiu, K., Zhang, Q., Beuther, H., & Fallscheer, C. 2012, ApJ, 756, 170

(ref: rodon12) Rodón, J. A., Beuther, H., & Schilke, P. 2012, A&A, 545, A51

(ref: schnee12) Schnee, S., Di Francesco, J., Enoch, M., et al. 2012, ApJ, 745, 18

(ref: tan14) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 149

(ref: tani18) Taniguchi, K., Miyamoto, Y., Saito, M., et al. 2018, ApJ, 866, 32

(ref: van98) van Dishoeck, E. F. & Blake, G. A. 1998, ARA&A, 36, 317

(ref: vanter19) van Terwisga, S. E., van Dishoeck, E. F., Cazzoletti, P., et al. 2019, A&A, 623, A150

(ref: wheel12) Wheelwright, H. E., de Wit, W. J., Oudmaijer, R. D., et al. 2012, A&A, 540, A89

(ref: wie12) Wienen, M., Wyrowski, F., Schuller, F., et al. 2012, A&A, 544, A146

(ref: zapata08) Zapata, L. A., Palau, A., Ho, P. T. P., et al. 2008, A&A, 479, L25

[^1]: https://dx.doi.org/10.18434/T4JP4Q

[^2]: http://almascience.eso.org/aq/

[^3]: http://wsa.roe.ac.uk/index.html

[^4]: https://irsa.ipac.caltech.edu/data/SPITZER/GLIMPSE/

</paper>

Write the methods card for this paper.