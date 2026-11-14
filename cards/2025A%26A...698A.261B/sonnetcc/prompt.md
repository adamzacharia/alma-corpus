# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...698A.261B\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...698A.261B",
 "title": "Complex organic molecules towards the central molecular zone of NGC 253",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Bouvier, M.",
 "n_authors": 12,
 "arxiv_id": "2504.19631",
 "doi": "10.1051/0004-6361/202554420",
 "alma_projects_linked_by_archive": [
  "2017.1.00161.L",
  "2018.1.00162.S"
 ]
}
```

Paper text:
<paper>
# Complex Organic Molecules towards the central molecular zone of NGC 253

Interstellar complex organic molecules (iCOMs) may have a link to prebiotic species, key building blocks for life. In Galactic star-forming (SF) regions, spatial variations in the iCOMs emission could reflect the source physical structure or different chemical formation pathways. Investigating iCOMs in extragalactic SF regions may thus provide crucial information about these regions.

As an active extragalactic SF region, the central molecular zone (CMZ) of the nearby galaxy NGC 253 provides an ideal template for studying iCOMs under more extreme conditions. We aim to investigate the emission of a few selected iCOMs and understand if a difference between the iCOMs could reflect on the source’s chemical or physical structure.

Using the high angular resolution ($\sim 27$ pc) observations from the ALCHEMI ALMA large program, we imaged the emission of selected iCOMs and precursors; , , , , and . We estimated the gas temperatures and column densities of the iCOMs using a rotational diagram analysis, and by performing a non-LTE analysis for .

The iCOM emission concentrates mostly towards the inner part of the CMZ of NGC 253 and can be reproduced with two gas components. Different emission processes can explain iCOM emission towards the CMZ of NGC 253: at Giant Molecular Cloud (GMC) scales ($\sim 27$ pc), the iCOMs could trace large-scale shocks whilst at smaller scales (a few parsecs), both shock and heating processes linked with ongoing star formation may be involved. Using column density correlation trends and known formation pathways, we find that more than one formation path could be involved to explain the iCOM emission. Finally, we found chemical differences between the GMCs, such as a decrease of abundance for the N-bearing species towards one of the GMCs or different excitation conditions for and towards two of the GMCs.

# Introduction

One of the major topics in astrochemistry is to understand how complex species can form and survive under the harsh conditions of the interstellar medium (ISM). In particular, interstellar Complex Organic Molecules (iCOMs) are carbon-bearing molecules of at least 6 atoms (cite: herbst2009; ceccarelli2017). Other species which do not fit formally in this category are also relevant for prebiotic chemistry. This is the case of methanimine (), the simplest imine and an important precursor of glycine (cite: theule2011; danger2011). iCOMs have been of particular interest due to their potential in forming pre-biotic molecules, themselves important building blocks for life. Within our Galaxy, iCOMs are particularly abundant in various star-forming (SF) regions (e.g., (cite: blake_1987; herbst2009; belloche2019; jorgensen2020; ceccarelli2023; chen2023)) and our Galactic Centre (cite: jimenez-serra2025). However, despite numerous observations, understanding iCOM formation pathways is challenging. Two main chemical paradigms have been invoked in the literature: only grain surface synthesis and the combination of grain surface and gas phase synthesis (see (cite: ceccarelli2023) and references therein for a review).

Multiple observations of iCOMs in Galactic SF Regions, at both low and high angular resolution, revealed a dichotomy among iCOMs, in particular between O- and N-bearing species (cite: blake_1987; caselli1993; widicus_weaver_deep_2017; codella2017; suzuki2018; csengeri2019; bogelund_NvsO_2019; vanderwalt_2021; mininni2023; peng2022; busch2024; bouscasse2024). The cause for such segregation between N-bearing and O-bearing species is not clear but several hypotheses have been proposed. These include a difference in thermal history (cite: caselli1993; viti_evaporation_2004; suzuki2018; garrod2022) or in the formation and destruction pathways of the species (cite: busch2024), the intrinsic characteristics of the chemical species (e.g., binding energies; (cite: bianchi2022)), or the influence of external forces (e.g., shocks; (cite: tercero2018; csengeri2019; busch2024)). Studying iCOMs in external galaxies, under the assumption that they trace similar physical processes as in Galactic SF regions, may thus provide important information about the physics and the chemistry of the dense gas of extra-galactic SF regions.

iCOMs have been studied in several external galaxies, such as in IC 342 (cite: henkel1987), NGC  6946 (cite: eibensteiner2022), the Small Magellanic Cloud (cite: shimonishi_detection_2023) or PKS 1830-211 (cite: muller2021); in M82 (cite: mauersberger1991) and Arp 220 (cite: martin_2011); in PKS 1830-211 (cite: muller2011); in NGC 4418 (cite: costagliola2015); in the Large Magellanic cloud (cite: sewilo_detection_2018; golshan2024) or towards NGC 1068 (cite: qiu2018), and in NGC 253 (cite: martin_alchemi_2021), to cite a few examples. Among these galaxies, the origin of iCOMs was constrained in only a few of them: , , and trace hot cores in the Small and Large Magellanic Clouds (SMC and LMC, respectively; (cite: sewilo_detection_2018; shimonishi_detection_2023)), traces shocks in NGC 253, NGC 1068, and M 82 (e.g. (cite: martin_2006; humire_methanol_2022; huang2024), Huang et al. subm.), and has been found to be enhanced in the outflow of IC 860 (cite: gorski2023). Studies of iCOMs in extragalactic regions are thus still very limited to a few extragalactic sources, and a handful of iCOMs.

While Galactic studies offer high-resolution data on molecular cloud structure and chemistry, they are limited to relatively moderate star formation conditions. NGC 253 is a nearby (3.5 Mpc; (cite: rekola_distance_2005)) relatively edge-on (inclination of 76$^\circ$; (cite: mccormick_2013)) galaxy hosting a starburst nucleus in its inner kpc (cite: bendo_2015; leroy_alma_2015). NGC 253 provides a unique laboratory to test what we know from Galactic chemistry studies under more extreme conditions — intense radiation fields ($G_0 \sim 10^4-10^5$; (cite: harada_alchemi_2022)) and cosmic-ray ionisation rate ($\zeta > 10^{-14}$s$^{-1}$;e.g. (cite: holdship_energizing_2022; behrens2024)), intense star formation (2$M_{\odot}$yr$^{-1}$; (cite: leroy_alma_2015)) and strong associated feedback processes that drive large-scale outflows (cite: mccarthy1987). By studying iCOMs in NGC 253, we can assess whether the same assumptions used in Galactic star-forming regions hold in more extreme environments, or whether additional chemical and dynamical processes dominate. This is particularly relevant for understanding the role of GMCs in starbursts and high-redshift galaxies, where similar conditions prevail but are much harder to observe in detail. So rather than merely confirming what we already know from the Milky Way, NGC 253 allows us to probe how universal our chemical diagnostics are and whether they remain valid in an active nuclear starburst environment.

The central molecular zone (CMZ) of NGC 253 has been surveyed by the ALMA Comprehensive High-resolution Extragalactic Molecular Inventory (ALCHEMI; (cite: martin_alchemi_2021)) large programme at a resolution of $1.6 \ensuremath{''}$ (27 pc). Previous ALCHEMI studies have revealed the chemical richness of the CMZ and how it can be used to better understand its structure and physics of the CMZ of NGC 253 (e.g., (cite: harada_starburst_2021; holdship_energizing_2022; humire_2020; behrens_tracing_2022; behrens2024; huang_reconstructing_2023; tanaka_2023; harada_pca_2024; bouvier2024; kishikawa2024), López-Gallifa et al. in prep.). Therefore, ALCHEMI provides an ideal template to study iCOMs toward a nuclear extragalactic starburst, at a high enough angular resolution to investigate the origin of their emission for the first time. In particular, we aim to study a selection of N- and O-bearing iCOMs detected towards the CMZ of NGC 253 (cite: martin_alchemi_2021) and investigate whether spatial segregation between iCOMs at GMC scales could reflect different gas physical conditions (temperature, density), environmental conditions (e.g., heating, shocks) or evolutionary stage within the CMZ, and whether we can constrain their region of emission, and their formation pathways. In this study, we focussed on a sample of O- and N-bearing iCOMs, namely acetaldehyde (), ethanol (), formamide (), methylamine (), and methanimine (), all previously detected in (cite: martin_alchemi_2021). In addition, some of these species could be chemically linked ( with ; e.g., (cite: skouteris2018) and with ; e.g., (cite: woon2002; dejesus2021; molpeceres_ch3nh2_2024)) which will allow us to address the question of their formation pathways.

In Section [2](#sec:obs) we describe the observations. We present the emission distribution and the results from the Gaussian fit of the lines in Sec. [3](#sec:emission_maps_fit) and we derive the physical parameters in Sec. [4](#sec:phys_params). We discuss the possible chemical pathways involved in the formation of the surveyed iCOMs, their region of emission and the possible differences between the regions and galaxies in Sec. [5](#sec:discussion). We summarise our results in Sec. [6](#sec:conclusions).

# Observations

We used the observations from the ALCHEMI Large Program (co-PIs.: S. Martín, N. Harada, and J. Mangum). We only give here the relevant information for the present work. Further details about the the data acquisition, calibration and imaging are provided in the ALCHEMI summary paper (cite: martin_alchemi_2021). The observations were performed during Cycles 5 and 6, under the project codes 2017.1.00161.L and 2018.1.00162.S. Bands 3 through 7 were covered, with frequencies ranging between 84.2 and 373.2 GHz. The observations were centred at the position $\alpha$(ICRS)$=00^h47^m33.26^s$ and $\delta$(ICRS)$=-25^\circ 17'17.7''$. The common region imaged corresponds to a rectangular area of size $50'' \times 20''$ (850 $\times$ 340 pc) with a position angle of 65$^\circ$, covering the CMZ of NGC 253. The data cubes have a common beam size of $1.6\ensuremath{''}\times 1.6\ensuremath{''}$ ($\sim 27$ pc), a maximum recovered scale $\gtrsim 15''$ ($\gtrsim 255$ pc), and a spectral resolution of $\sim 10$ km s$^{-1}$. Finally, the adopted flux calibration uncertainty is 15%, following (cite: martin_alchemi_2021).

We used the continuum-subtracted FITS image cubes provided by ALCHEMI containing the targeted species in this work. We produced velocity-integrated maps (see Sec. [3](#sec:emission_maps_fit)) from the processed FITS image cubes using the packages MAPPING and CLASS from GILDAS[^2]. We used these same packages to extract the spectra and perform Gaussian line fitting. The spectra were extracted from beam-sized regions before being converted to brightness temperature following (cite: bouvier2024). For each spectrum, we fitted a zeroth order polynomial to the line-free channels from the continuum-subtracted data cubes to retrieve the information about the spectral root-mean-square (rms).

# Emission distribution and Gaussian line fitting results

The CMZ of NGC 253 is a region of 300 pc $\times$ 100 pc where 10 Giant Molecular Clouds (GMCs; named from GMC 1 to GMC 10) of a size of about 30 pc in diameter have been identified in both molecular and continuum emission (cite: sakamoto_2011; leroy_alma_2015). At a higher angular resolution, it was found that the GMCs located in the inner 160 pc in length of the CMZ (corresponding to GMCs 3, 4, 5 and 6) can be resolved into multiple star-forming clumps called proto-super star clusters (hereafter pSSCs; e.g., (cite: ando_2017; leroy_forming_2018)), which are compact ($\leq 1$ pc), massive ($M\geq 10^5$M$_\odot$), and young ($\leq 3$ Myr) clusters with ongoing star formation.

In the following, we focus our analysis in the inner part of the CMZ, which includes the regions named GMC 3 to GMC 7 (cite: leroy_alma_2015). This is where all the five iCOMs investigated in this work are the most intense. However, whilst the peak of the iCOMs emission coincides well with the location of GMC 6 and GMC 7, it is slightly shifted ($\lesssim 1.6^{\prime\prime}$) with respect to GMC 3 and GMC 4 (see Figure [1](#fig:sup-icoms)a) and seems to be more consistent with the location of pSSCs. Since later on (see Section [3.2](#sec:lines)) we centred the region where we extracted the spectra on the coordinates of the pSSC 2 and pSSC 5 sources, we use the name of these pSSCs for the regions that would correspond to GMC 3 and GMC 4, respectively. Note that the angular resolution of ALCHEMI does not allow distinguishing each pSSC, which means that our position named pSSC 2 in fact includes pSSCs 1 to 3, and our position named pSSC 5 includes pSSCs 4 to 7 (see (cite: leroy_forming_2018) for the pSSCs distribution). The region GMC 6 hosts pSSC 14, but since the coordinates used to extract the spectra are centred on the coordinates of GMC 6 and not on those of pSSC 14 (which slightly differs), we kept the name GMC 6. No pSSCs have been detected towards GMC 7.

Finally, the emission of the iCOMs studied in this work is relatively faint towards GMC 5, which lies close to the kinematic centre. Moreover, this region shows particular absorption features due to the strong radio continuum emission (cite: meier_alma_2015; humire_methanol_2022) and would require a specific radiative transfer modelling, which is beyond the scope of this paper. We thus excluded this GMC from our analysis. As a result, in the rest of the paper, we focus on positions that we named as GMC 7, GMC 6, pSSC 2, and pSSC 5, whose coordinates are listed in Table [1](#tab:region_selected). Below, we describe and compare the emission distribution of the selected species towards these four regions in Sec. [3.1](#sec:maps), and we describe the extraction and analysis of the spectral lines in Sec. [3.2](#sec:lines).

## Emission distribution

To perform moment maps, we looked for transitions isolated enough (i.e. with either no contribution from other adjacent species or with a contamination from adjacent features that are below 3$\sigma$ level) within the range of velocity on which we integrate the emission. We then integrated the emission over the full line profile, taking into account the velocity shift across the regions, hence within the range \[70 ; 380\] km s$^{-1}$. The transitions used to perform these moment maps are labelled in the spectra of the brightest region, GMC 6, region in Figures [13](#fig:spec_ch3cho_GMC6) to  [17](#fig:spec_c2h5oh_GMC6). The corresponding spectral parameters of the transitions are shown in Table [2](#tab:lines).

Figure [1](#fig:sup-icoms) shows the integrated line emission distribution of the five iCOMs, grouped in four $E_{\mathrm{u}}$ ranges, to minimize biases due to different excitation conditions. For each $E_{\mathrm{u}}$ range, we superposed the contour maps of the various species to visually show the overlap between their emission distribution. Since we have a limited sample of moment 0 maps for the five iCOMs, we could not always compare simultaneously their emission distribution at each $E_{\mathrm{u}}$ range. Panel (a) of Figure [1](#fig:sup-icoms) shows the contour maps of the and transitions close to $E_{\mathrm{u}}=20$ K. Panel (b) shows the contour overlap of all species except at $E_{\mathrm{u}}=30-40$ K. Panel (c) shows the contour maps of the and transitions at $E_{\mathrm{u}}\sim 70$ K. Finally, panel (d) shows the contour maps of and around $E_{\mathrm{u}} > 100$ K.

![](maps_sup-v2.pdf)

From Figure [1](#fig:sup-icoms), we can see a difference in the spatial emission of the iCOMs across the four regions. First, shows more extended emission than towards the part of the CMZ encompassing the regions GMC 6 to pSSC 2, as seen in Figure [1](#fig:sup-icoms), panel (a). On the other hand, the emission of dominates towards GMC 7 compared to that of . For the transitions with upper energy levels around $\sim 30-40$ K (see Figure [1](#fig:sup-icoms)b), we can see that each GMC seems to show a different chemical composition: the and emission dominate GMC 7 and show the most extended emission throughout the regions. However, there is a lack of emission towards the kinematic centre (indicated by a black triangle in Figure [1](#fig:sup-icoms)) compared to . On the other hand, the emission of and is more compact around the GMCs. Both species show emission towards GMC 6 and have faint emission toward GMC 7 but whilst emission covers both pSSC 5 and pSSC 2, lacks emission towards pSSC 2. At $E_{\mathrm{u}} \sim 70$ K (see Figure [1](#fig:sup-icoms)c), both and show emission towards GMC 6 with showing a slightly more spatially extended emission compared to . On the other hand, only emits towards pSSC 5 and the two species are fainter towards pSSC 2 and GMC 7. For $E_{\mathrm{u}} > 100$ K (see Figure [1](#fig:sup-icoms)d), we see that both and emit towards GMC 6 and pSSC 2 but shows a more extended emission. only emits towards pSSC 5 and both species are absent at GMC 7. Interestingly, whilst showed fainter emission for $E_{\mathrm{u}} \sim 30-40$ K towards pSSC 2, it shows stronger emission for $E_{\mathrm{u}} > 100$ K. Whilst the emission of the iCOMs seems to show a spatial disparity within the inner GMCs of NGC 253, one should keep in mind that fainter emission could be due to either a true lower abundance or a sensitivity bias if the transition is not very intense (Band 5 observations were less sensitive compared to the rest of the data; see (cite: martin_alchemi_2021)). Hence, whether there is a disparity among the species across the region will be investigated after deriving the physical parameters (Sec. [4](#sec:phys_params)).

Finally, we can see an evolution in the emission morphology compared to $E_{\mathrm{u}}$: Looking at and for which we imaged transitions from 19 K to 70.5 K and from $\sim 40$ K to $\sim 123$ K, respectively, we see the emission being more compact with increasing $E_{\mathrm{u}}$. This shows that transitions with different $E_{\mathrm{u}}$ may be excited under different conditions and it is important to compare spatial extent of species which have similar upper level energies. All the velocity-integrated maps obtained for each species are shown in Figures [8](#fig:ch3nh2-maps) to [12](#fig:c2h5oh-maps).

+:-------+:------------:+:------------------------:+
| Region | R.A. (ICRS)  | Dec. (ICRS)              |
|        +--------------+--------------------------+
|        | ($00^h47^m$) | ($-25^\circ:17'$)        |
+--------+--------------+--------------------------+
| GMC 7  | $33^s.6432$  | $13\ensuremath{''} .272$ |
+--------+--------------+--------------------------+
| GMC 6  | $33^s.3312$  | $15\ensuremath{''} .756$ |
+--------+--------------+--------------------------+
| pSSC 5 | $32^s.9811$  | $19\ensuremath{''} .710$ |
+--------+--------------+--------------------------+
| pSSC 2 | $32^s.8199$  | $21\ensuremath{''} .240$ |
+--------+--------------+--------------------------+

: Selected regions and coordinates.

Table notes: stands for giant molecular Cloud and stands for proto-super star cluster.

## Spectra and line parameters

We extracted the spectra towards GMC 7, GMC 6, pSSC 5, and pSSC 2 from regions of a beam-size (1.6$\ensuremath{''} \times 1.6\ensuremath{''}$) and centred on the coordinates given in Table [1](#tab:region_selected). We then centred each spectrum at the local standard of rest velocity (LSRK) corresponding to the rest frequency of each transition used in this work before performing a Gaussian line fitting to the detected transitions. A threshold of 3$\sigma$ on the intensity peak was set to consider a line to be detected. Transitions which were contaminated by more than 15% by a transition from another species (i.e., contributing to 15% or more of the total integrated intensity of our desired transition), or that were too blended to perform a multiple Gaussian fit, were not taken into account. To assess whether a line is contaminated, we used the existing line identification of ALCHEMI 7m and 12m data ((cite: martin_alchemi_2021) and priv. comm.) and performed an additional inspection using WEEDS (cite: maret_2011), an extension of CLASS, which uses both the Jet Propulsion Laboratory (JPL; (cite: pickett_1998)) and the Cologne Database for Molecular Spectroscopy (CDMS; e.g. (cite: muller_2005; endres2016)) databases. However, in the case of , the E- and A- states are often completely blended together, the spectral resolution of 10 km s$^{-1}$ being insufficient to disentangle the two states. Similarly, for and , where two transitions with similar spectroscopic parameters are completely blended together. In these cases, we still kept these transitions and performed a single line Gaussian fit. We explain how we used these transitions for the analysis in Sec. [4.1](#subsec:methodology). We present the list of all of the transitions per species and per region used in this work, as well as their spectroscopic parameters, in Table [2](#tab:lines). We detect only the anti- form of among the different rotamers, but this is not surprising as the anti form is the most stable rotamer (cite: pearson2008; bianchi2019), so the name refers to this form only.

From the Gaussian line fitting procedure, we extracted the integrated intensities ($\int T_B.d\text{V}$) in K km s$^{-1}$, the line widths (FWHM) and the peak velocity ($V_{\mathrm{peak}}$), both in km s$^{-1}$. The extracted spectra and the best Gaussian fits are shown in Figure [13](#fig:spec_ch3cho_GMC6) to  [31](#fig:spec_c2H5OH_SSC5). The Gaussian line-fitting results and the rms for each transition and region are shown in Table [2](#tab:lines).

# Derivation of physical parameters

## Methodology

For each species and each of the four selected regions, we detected enough transitions ($>7$ for most species and regions) with a large enough range of $E_{\mathrm{u}}$ covered to derive the column densities and rotational temperatures using the rotational diagram (RD) method (cite: goldsmith_1999). This method assumes Local Thermodynamic Equilibrium (LTE) and optically thin emission. These assumptions will be revisited later on in the case of (see Section [4.3](#sec: nonlte)). We also assume the Rayleigh-Jeans approximation holds. We included a calibration error of 15% (see Sec. [2](#sec:obs)) and the spectral rms in the integrated flux uncertainties. The best fit was calculated by minimizing the reduced chi-square, $\chi_r^2$.

As a first approximation, we set the beam-filling factor[^3] to 1/2, assuming that our emission comes from the GMC scales (hence from a region of the size of the beam or 1.6$\ensuremath{''}$). However, in some regions and for some species, we saw a clear deviation in the rotation diagram for the higher $E_{\mathrm{u}}$ transitions. This behaviour can be either due to the presence of multiple gas components with different physical conditions or to non-LTE or opacity effects (cite: goldsmith_1999). We favoured the first option, i.e. the presence of multiple gas components. Our choice is supported by the fact that higher upper-energy level transitions showed often a different FWHM or $V_\mathrm{peak}$ compared to the lower upper-energy transitions (see discussion in Sec. [4.2](#subsec:rds) below) and the difference in emission distribution of the species depending on the excitation conditions (see Sec. [3.1](#sec:maps)). For these cases, we assumed that the first component, traced by the lower upper-level energy transitions, arises from the GMCs whilst the second component, traced by the higher upper-level energy transitions, arises from the pSSCs. For the latter component, we calculated the beam-filling factor using a size for the pSSC clusters of 0.12$\ensuremath{''}$ (corresponding to $\sim 2$ pc), estimated by (cite: leroy_forming_2018). This assumption is supported by the emission being more compact with increasing $E_{\mathrm{u}}$, sometimes unresolved by the ALCHEMI beam (See Figure [1](#fig:sup-icoms)).

Finally, as mentioned in Sec. [3.2](#sec:lines), most of the E- and A- states of and some transitions for , and are too blended to perform a multiple Gaussian fit. As the blended transitions have the same spectroscopic parameters ($E_{\mathrm{u}}, A_{ij}, g_{\mathrm{u}}$), we thus assumed that each transition accounts for 50% of the total line integrated intensity. Furthermore, for , we assumed a / ratio of 1 since the kinetic temperature is higher than the energy difference of $\sim 0.1$ K between the levels of the different symmetry states (cite: matthews1985). Therefore, we included each pair of blended transitions in the RDs by attributing 50% of the total integrated intensity given in Table [2](#tab:lines) to each individual transition.

## Rotational Diagrams

![](RDs_GMC6_v2.pdf)

In Figure [2](#fig:rds_GMC6), we show as an example the rotation diagrams obtained for each species towards GMC 6, which is the region showing the most intense emission (see Sec. [3.1](#sec:maps)). The RDs at other positions are presented in Appx. [9](#appx:RDs). In the case of GMC 6, two temperature components were needed for , , and . Two temperature components are also needed for pSSC 2 ( and ) and for pSSC 5 ( and ). For and , the deviation occurs near $E_{\mathrm{u}} \sim 40$ K and it is closer to 60 K for . When two temperature components are present in the RDs, we made the assumption that they are not arising from the same spatial component. The low $E_{\mathrm{u}}$ transitions being more spatially extended compared to the higher $E_{\mathrm{u}}$ transitions (see Section [3.1](#sec:maps)), we assumed that whilst the former mainly arises from GMC scales, the latter arises from more compact scales, such as the pSSC scales, the next identified structures within the GMCs. As a caveat, this implies that the contribution from the warm compact component to the cold extended one is negligible.

For the species showing two temperature components, we looked at the Gaussian fit results to check for any shift in the mean FWHM or $V_\mathrm{peak}$ as a function of the upper-level energy. In the following, we discuss first about the Gaussian fit results in the context of the two temperature components (Sec. [4.2.1](#subsec:two-T-comp)) before discussing the results from the RDs (Sec. [4.2.2](#subsec:rds_results)).

### Gaussian fits and temperature components

To check if the presence of the two temperature components seen in the RDs for , , and can be identified through a shift in the mean FWHM or $V_\mathrm{peak}$ as a function of the upper-level energy, we used only relatively isolated transitions, where a single Gaussian fit was performed to get the most reliable measurement for FWHM and $V_\mathrm{peak}$. In the case of auto-blended transitions, we kept only those for which the two lines are separated enough to perform two separate Gaussian fits. Figure [3](#fig:av-GF) shows the FWHM and $V_{\mathrm{peak}}$ as a function of $E_{\mathrm{u}}$ towards GMC 6, pSSC 5, and pSSC 2, where a second gas component has been fitted in the RDs. The uncertainties were derived by adding in quadrature the errors from the Gaussian fits with the spectral resolution of 10 km s$^{-1}$. The mean FWHM and $V_\mathrm{peak}$ for each component are summarised in Table [3](#tab:av_GF). We discuss individual species below:

####  (Figure [3](#fig:av-GF), top panels):

We see a clear difference in the mean $V_\mathrm{peak}$ for GMC 6, where we see an increase in the $V_\mathrm{peak}$ with increasing $E_{\mathrm{u}}$. However, we cannot see this shift toward pSSC 5 where a second temperature component has also been fit in the RD (see Figure [33](#fig:rds_SSC5)), due to the lack of reliable Gaussian fit measurements.

####  (Figure [3](#fig:av-GF), middle panels):

A slight decrease in the linewidths with increasing $E_{\mathrm{u}}$ is seen towards GMC 6 and pSSC 5, although it is quite marginal. No variation in the FWHM is seen towards pSSC 2 and no difference in the $V_\mathrm{peak}$ is seen towards any of the regions in . There is thus no strong indication of two different components for , and the deviation in the RD could be due to non-LTE effects (cite: goldsmith_1999).

####  (Figure [3](#fig:av-GF), bottom panels):

An increase in $V_\mathrm{peak}$ is relatively clear with increasing $E_{\mathrm{u}}$ towards the two regions where two components were fitted, i.e. GMC 6 and pSSC 2. For pSSC 2, we also observe simultaneously a decrease in the FWHM with an increasing $E_{\mathrm{u}}$, and this can be seen more moderately towards GMC 6. Interestingly, the shift in $V_\mathrm{peak}$ and in FWHM seems to occur closer to 40, compared to what is seen in the RDs, which could indicate that the majority of the emission could be associated with the second higher temperature component.

In conclusion, with the current spectral resolution as a main contributor to the uncertainties, the presence of two components is only clear for whilst it is not clear for and . In addition, one should note that optically thick lines can induce larger line widths. Higher spectral and angular resolution observations are needed to identify possible different gas components more clearly.

### Results from the rotational diagrams

Figure [4](#fig:summary_LTE) shows an overview of the derived $T_{\text{rot}}$ and $N_{\text{tot}}$ for each species and region listed in Table [4](#tab:results_RDs). Due to the fact that we observe deviations from the fits in the RDs, it is clear that the derived $T_{\mathrm{rot}}$ are not representative of the true gas temperature. For the rotational temperatures (top panel of Figure [4](#fig:summary_LTE)), we notice some differences between the regions. GMC 7 shows only a cold ($T_{\text{rot}}\leq 20$ K) component compared to the other regions. On the other hand, the other regions have two components, a cold ($T_{\text{rot}}\leq 20$ K) and a warmer component ($T_{\text{rot}}\sim 30-80$ K). Finally, none of the regions shows a hot ($T_{\text{rot}}> 100$ K) component, which would have been expected if the iCOMs are thought to be emitted from a hot-core-like ($T > 100$ K; see e.g. (cite: kurtz2000)) region. On the other hand, this result is similar to the Milky Way Galactic Centre (GC), where widespread emission (a few tens to hundreds of parsecs) from iCOMs has been measured (cite: requena-torres_organic_2006; li_2017_widespread_coms; li_2020_widespread_coms). There, low rotational temperatures ($T_{\mathrm{rot}}\leq 20$ K; e.g., (cite: requena-torres_organic_2006; zeng2018; rivilla2022)) were also derived, indicating that the GC iCOM emission is sub-thermally excited. The extended iCOM emission toward the GC is not associated with hot cores and can be explained by widespread recurrent low-velocity shocks (cite: requena-torres_organic_2006; zeng2020).

![](results_fits_compaEu_noGMC7.pdf)

For the column densities (bottom panel of Figure [4](#fig:summary_LTE)), we describe below the behaviour separating the emission from the cold component (derived with $\theta_s=1.6\ensuremath{''}$; i.e. GMC scale) and the warm component (derived with $\theta_s=0.12\ensuremath{''}$, i.e. pSSC scale) transitions. Only one temperature component was fitted for all species towards GMC 7, and towards all regions, towards pSSC5, and towards pSSC2. In these cases, since we do not know the region of emission of these species, we calculated column densities for the two emission sizes, i.e. for the GMC scale ($\theta_s=1.6\ensuremath{''}$) and the pSSC scale ($\theta_s=0.12\ensuremath{''}$).

#### GMC-scales:

and show relatively constant column densities throughout the regions. On the other hand, , , and show a decrease in $N_{\text{tot}}$ towards GMC 7 and the column density of increases towards GMC 6. Overall, and show the highest column densities, except towards GMC 7 where the column density of decreases.

#### pSSC-scales:

For and , the trend in column density is the same as at GMC-scales since the two species have only one component. In the case of , its column density is constant across the regions except towards GMC 7, where it decreases. In the cases of and , if we consider only the second components (high $E_{\mathrm{u}}$) towards GMC 6 and pSSC 5 for and pSSC 2 for , then the column density of both species is the highest towards GMC 6. If we consider that in the other regions where only one component is detected (low $E_{\mathrm{u}}$ transitions), then the column density of is the lowest towards pSSC 5 and that of is the lowest towards GMC 7 and pSSC 2.

We note that since the four regions do not have the same column densities, the abundance trends could be different than the column density trends. An abundance study is beyond the scope of this paper. We simply stress here that there are variations of the relative column densities between the species across the regions, indicating possible chemical differences, such as towards GMC 7, where the relative amount between O-bearing and N-bearing iCOMs changes compared to the other regions. We discuss chemical variations in more details in Sec. [5.3](#subsec:chemical_variations).

![](results_LTE_summary_v3.pdf)

## Non-LTE analysis: 

is the only species from this work for which collisional excitation rates are available. Therefore, we can perform a non-LTE analysis to constrain more accurately the gas physical parameters traced by toward the CMZ of NGC 253.

We performed this analysis using the large velocity gradient (LVG) code *grelvg* (cite: ceccarelli_2003). We used the - collisional rates from (cite: xue2024) available in the Excitation of Molecules and Atoms for Astrophysics (EMAA) database[^4]. The rates were calculated for a temperature in the range 10 to 150 K and for the transitions up to $E_{\mathrm{u}}=143$ K. Therefore, the maximum temperature tested is limited by the available rate coefficients, and the transition at 312.336 GHz with $E_{\mathrm{u}}=151.3$ K, that we detect in this work, was excluded from the analysis. For each region we ran a grid of models ($\sim 10,000$) varying the column density, the gas density and temperature within $10^{13}-10^{18}$ , $10^4-10^8$ cm$^{-3}$, and $10-150$ K, respectively. The column densities and gas densities were both sampled in logarithmic scale and the gas temperature was sampled in linear scale. We left the source size as a free parameter. Then, for the geometry, we chose a uniform sphere (cite: osterbrock1974) as the most physically realistic choice. The ortho-to-para ratio of was set to the statistical value of 3. Finally, the average linewidths of chosen is 50 km s$^{-1}$, which is the average linewidth across the regions (see Table [3](#tab:av_GF)). We also included a 15% calibration uncertainty in the integrated intensity (see Sec [2](#sec:obs)).

From the RD analysis, there is no clear indication of a multiple temperature components for (See e.g., Figure [2](#fig:rds_GMC6)). We thus first included all the lines in the LVG code. However, this resulted in a bad fit ($\chi^2_r>5$) for GMC 6, pSSC 5, and pSSC 2. In these regions, the two transitions of at 225.554 and 172.267 GHz are not well fit with the other transitions. These lines have the lowest $E_{\mathrm{u}}$ ($< 20$ K) and could thus be coming from a cooler or more extended component compared to what the other transitions ($E_{\mathrm{u}}= 27-151$ K) trace. Since we cannot perform the LVG analysis with only two lines, we cannot constrain the physical parameter of this potentially cooler component. We thus ran the LVG with the rest of the lines ($E_\mathrm{u}\geq 27$ K).

![](LVG_CH2NH.pdf)

+:-------------------------------------------+:--------:+:-----------:+:--------:+:-----------:+:--------:+:-------------:+:--------:+:---------------------:+
| Parameters                                 | GMC 7                  | GMC 6                  | pSSC 5                   | pSSC 2                           |
+--------------------------------------------+----------+-------------+----------+-------------+----------+---------------+----------+-----------------------+
|                                            | Best Fit | Range       | Best Fit | Range       | Best Fit | Range         | Best Fit | Range                 |
+--------------------------------------------+----------+-------------+----------+-------------+----------+---------------+----------+-----------------------+
| $N_{\ce{CH2NH}}$ ($\times10^{16}$ )        | $1.5$    | $0.7-4.5$   | $1.5$    | $0.7-4$     | $2$      | $0.2-5$       | $2$      | $0.2-5$               |
+--------------------------------------------+----------+-------------+----------+-------------+----------+---------------+----------+-----------------------+
| $n(\text{H}_{2})$ ($\times10^5$ cm$^{-3}$) | $0.6$    | $0.5-1$     | $8$      | $3-60$      | 1.7      | $1-10$        | $3$      | $0.7-20$              |
+--------------------------------------------+----------+-------------+----------+-------------+----------+---------------+----------+-----------------------+
| $T_{\text{kin}}$ (K)                       | 110      | $\geq 45$   | 45       | $25-130$    | 150      | $\geq 30$     | 33       | $20-100$ ; $\geq 120$ |
+--------------------------------------------+----------+-------------+----------+-------------+----------+---------------+----------+-----------------------+
| Source size ($''$)                         | 0.20     | $0.15-0.24$ | $0.26$   | $0.16-0.34$ | 0.19     | $0.17 - 0.60$ | $0.26$   | $0.22-0.60$           |
+--------------------------------------------+----------+-------------+----------+-------------+----------+---------------+----------+-----------------------+
| $\tau$ Range                               | $0.6-3.4$              | $0.04-1.3$             | $0.03-2.4$               | $0.01-2.3$                       |
+--------------------------------------------+------------------------+------------------------+--------------------------+----------------------------------+
| $\chi^2_r$                                 | 0.3                    | 1.3                    | 1.4                      | 1.7                              |
+--------------------------------------------+------------------------+------------------------+--------------------------+----------------------------------+

Figure  [5](#fig:ch2nh_lvg) shows the results of the LVG analysis for each of the four regions. The best fit for the column densities is similar towards the four regions with values in the range $(1.5-2)\times10^{16}$ . The kinetic temperatures are not always well constrained and are limited by the maximum temperature available from the collisional rates (150 K). We thus have an overall lower limit of $T_{\text{kin}}\geq (20-50)$ K across the different regions. For the derived gas densities, they lie mostly between $n(\text{H}_2)=(10^5-10^6)$ cm$^{-3}$ except for GMC 7 where $n(\text{H}_2)\leq 10^5$ cm$^{-3}$. In all the regions, several lines were found to be optically thick with $\tau > 1$ (see Table [\[tab:lvg_params\]](#tab:lvg_params)). Finally, the best fit for the emission size is in the range $0.19\ensuremath{''} -0.26\ensuremath{''}$ corresponding to a linear scale of $\sim 3-4$ pc in diameter. The best-fit solutions and ranges obtained for each source are reported in Table [\[tab:lvg_params\]](#tab:lvg_params). The $1\sigma$ confidence levels constrained correspond to a 68% confidence range.

We corrected the rotation diagram for the optical depth and source size for all the regions using the population diagram method (cite: goldsmith_1999), taking the output values of the LVG analysis for these parameters to understand whether the optical depth effects are dominant. For consistency, we removed the transitions that were left out from the LVG analysis (see above). The corrected RDs are shown in [9.1](#appx:pop_diagrams). We still find some deviation from a straight line in the corrected RDs, with rotational temperatures below the minimum gas temperature predicted by the LVG analysis. Therefore, is also affected by non-LTE effects. This result is consistent with that of (cite: faure2018), who found that non-LTE effects can be expected in the density range of $n_{\text{H}_2}=10^3-10^7$ cm$^{-3}$ for this species. Please note however, that in the discussion below we will use the column densities derived with the RDs for as the goal of performing population diagrams was only to evaluate the part of non-LTE effects.

# Discussion

As mentioned in the introduction, investigating iCOMs in more extreme star-formation conditions to those that can be found in our own Galaxy allows us to probe how universal our chemical diagnostics are and whether they remain valid in extragalactic environments. Below, we qualitatively discuss whether the known proposed formation pathways for iCOMs could also be valid in NGC 253 and whether the iCOMs in this study can be chemically linked (Sec. [5.1](#sec:chemical_links)). We then discuss their possible region of emission and which physical processes they could trace (Sec. [5.2](#sec:origin)). Finally, we focus on the small chemical differences within the regions (Sec. [5.3](#subsec:chemical_variations)). Figure [7](#fig:summary) shows a schematic which summarizes our main hypothesis and scenarios concerning iCOMs towards the CMZ of NGC 253, focussing in particular on the discussion from sections  [5.1](#sec:chemical_links) and  [5.2](#sec:origin).

## Chemical link and formation pathways for iCOMs

Understanding which chemical pathways to the formation of a specific species are dominant within an environment is not straightforward. From observations, a method that is regularly used is to look at the abundance correlations between two species suspected to be chemically linked, or to have a similar precursor (cite: yamamoto2017; coletta2020; li2024_correlations). However, it is worth noting that a correlation between two species does not always imply a direct chemical link. It may also indicate that they went through similar physical processes of formation across different environments (cite: quenard2018; belloche2020).

Figure [6](#fig:correlations) shows the relation between the column densities of the iCOMs, at both GMC scales (corresponding to a source size of $1.6\ensuremath{''}$) or pSSC scales (corresponding to a source size of $0.12\ensuremath{''}$). We list below several trends from Figure [6](#fig:correlations) that will be discussed below. We refer to and as O-bearing iCOMs, and as N-bearing iCOMs. lies in between the two categories.

- At GMC scales, O-bearing species are well correlated over the four regions and present a constant ratio \[/\] of 3 (panel a). The correlation disappears at pSSC scales (panel f).

- At both GMC- and pSSC scales, there is an enhancement in O-bearing species compared to N-bearing species (including ) towards GMC 7 (panels b, c, h, k).

- At GMC scales, and are relatively well correlated over the four regions and present a constant ratio \[/\] of $\sim 3$ (panel d)). At pSSC scales, the ratio increases towards GMC 7 and pSSC 2 (panel i).

- The ratio \[\]/\[\] varies greatly from GMC scales (panel b) to pSSC scales (panel g).

- The abundance ratio between and (panels e, j) is close to 3 at both scales, but slightly lower for GMC 6 at pSSC scales.

In the following subsections, we look for correlation between the derived column densities of a few pairs of iCOMs, which are thought to share chemical roots. We first remind the known formation pathways of the different species before discussing whether a formation pathway is most probable for the CMZ of NGC 253, and whether a chemical link between the pairs of species discussed is possible. A summary of possible formation pathways for each iCOM is shown in Figure [7](#fig:summary).

###  and 

The formation pathways of are debated. Both gas phase and grain surface reactions are proposed. Among the viable gas-phase formation pathways, could be formed either from the radical previously formed on the grain and ejected in the gas phase (cite: charnley2004; VH2013; BG2020; codella_outflow_2020; desimone2020; vazart2020), or from (known as the ; e.g., (cite: skouteris2018; vazart2020)). However, whilst the first pathway has been validated in both cold and warm environments, the validity of the second one has not been checked in cold environments (cite: vazart2020). Alternatively, various grain surface reactions have been proposed for the formation of (cite: bennett2005; garrod2008; ruaud2015; lamberts2019; BG2020; martindomenech2020; ibrahim2022) although the efficiency of some of these reactions are debated (cite: rimola2018; enriqueromero016; enriqueromero2021). For , grain-surface reactions are mostly proposed but there is no consensus on the formation path (cite: JG2020; chuang2020; perrero2022; enriqueromero2022; garrod2022; molpeceres2024). One of the proposed pathways involves as a precursor (cite: bisschop2007; chuang2020; fedoseev2022), where it was expected that the solid-state abundances of are less than those of (cite: sivaramakrishnan2009; fedoseev2022). This formation pathway could be ruled out since recent observations made with the James Webb Space Telescope showed relatively similar ice abundances for the two species (cite: rocha2024; chen2024), as found previously in comets (cite: rubin2019). However, a direct comparison of the content seen in the ice and in the gas towards two low-mass protostars showed that this is not what is seen in the gas phase, where seems to be more abundant than (cite: chen2024). On the other hand, gas phase reactions starting from + and leading to the formation of through as a precursor are reported in both KIDA[^5] and UMIST[^6] databases, and could be a viable pathway if is abundant enough (which may be the case due to the high CRIR towards these regions; e.g. (cite: holdship_energizing_2022; behrens2024)). In the following, we investigate whether ethanol () and acetaldehyde () are correlated towards NGC 253.

Table [3](#tab:av_GF) shows that the mean FWHM and peak velocities of are generally more consistent with that of the colder component of . Optical depth effects could alter these results but further similarities can be seen when looking at the column densities of the two species: From Figure [4](#fig:summary_LTE), we see that both the column densities derived for GMC scales of and are relatively constant throughout the four regions. In addition, their abundance ratio of $\sim 2.3$ is also constant across the regions and show the best correlation at GMC scales (see Figure [6](#fig:correlations)a). Therefore, a correlation between the cold component of (governed by the low $E_{\mathrm{u}}$ transitions) and could indicate that the two species are chemically linked (see Fig [7](#fig:summary), hypothesis i). Since the abundance of is higher than that of , the two species could be linked via the gas-phase production of through the ethanol tree. This hypothesis, if true, implies that the ethanol tree pathway proposed by (cite: skouteris2018) would also be valid at low temperatures, since the iCOMs are likely sub-thermally excited. On the other hand, we cannot rule out that the two species were formed on the grains before being ejected through shocked processes (See Sec. [5.2](#sec:origin)). The higher abundance of compared to that of could then indicate more fast or important destruction or reprocessing of in the gas phase compared to . For , one proposed formation path for its precursor is via the gas phase reaction between and . Considering the high CRIR derived towards NGC 253 (cite: holdship_energizing_2022; behrens_tracing_2022), the abundance of could be high enough for the gas phase production of ethanol to be viable.

When looking at the correlations at the pSSC scales in Figure [6](#fig:correlations)f, the warm component of (traced by the high $E_{\mathrm{u}}$ transitions) towards GMC 6 and pSSC 5 is no longer correlated with ethanol. The difference in peak velocity and FWHM for this high $E_{\mathrm{u}}$ transitions compared to the low$E_{\mathrm{u}}$ transitions (see Table [3](#tab:av_GF)) indicates that additional is produced in these two regions, and likely through a different pathway. If the cold component of is formed in the gas phase, the warm component could, on the other hand, form on the icy grain mantles via thermal desorption (if the gas temperature is high enough, see Sec. [5.2.2](#subsec:SSC_scales)), or via non-thermal processes such as shocks (cite: ruaud2015; lu2024). We investigate the origin of the high excitation of in GMC 6 and pSSC 5 in Sec. [5.3](#subsec:chemical_variations).

### 

Both grain surface (cite: raunier2004; garrod2008; lopezsepulcre2015; fedoseev2016; rimola2018; dulieu2019; martindomenech2020; chuang2022) and gas phase (cite: kahane2013; barone2015; vazart2016; skouteris2017) formation pathways have been suggested for formamide (), but which one is the most efficient is highly debated, as in the case of . We refer to (cite: lopezsepulcre2019) and (cite: lopezsepulcre024) for a comprehensive review of the different formation paths proposed for formamide. Here, we will only investigate the potential chemical link of with HNCO and , both species thought to be chemically linked with , either as a parent species on the ice grain mantle or in the gas phase (; e.g., (cite: fedoseev2016; dulieu2019; kahane2013; vazart2016; aikawa2020; lopezsepulcre024)), or as a daughter species (HNCO; (cite: brucato2006; gorai2020; haupa2022; chuang2022)). Both and HNCO were studied towards the CMZ of NGC 253 ((cite: mangum_fire_2019; huang_reconstructing_2023), Huang et al. subm.).

HNCO traces low-velocity shocks throughout the CMZ of NGC  253 and the gas temperatures towards the four regions investigated in the present study range between $\sim 20-100$ K (cite: huang_reconstructing_2023). The rotational temperatures we derived range between $\sim 10-30$ K and $\sim 50-80$ K, for the cold and warm component, respectively, consistent with that of HNCO. A word of caution is needed, however, since our rotational temperature could be underestimated if optical depth effects or non-LTE effects are at play, as we found to be the case for (see Sec. [4.3](#sec: nonlte)). Using transitions with similar energy levels, we compared the emission distribution between and around $\sim 40$ and $\sim 140$ K as shown in Figure [36](#fig:nh2cho_hnco_contour_maps). is much less intense compared to HNCO, as it is much less abundant, but the two species do not peak towards the same regions. This is also seen when comparing the derived column densities of and HNCO: whilst HNCO has a relatively constant column density across the regions (cite: huang_reconstructing_2023), the cold component of decreases towards GMC 7 whilst the warm component is lower towards pSSC 2. Neither of the two component of seem thus to be chemically linked with HNCO.

As for HNCO, we also compared the emission distribution of and at similar energy levels, around 45 and 100 K, as shown in Figure [37](#fig:nh2cho_h2co_contour-maps). Even though is much less intense than due to its lower abundance, we can see a good correlation between the two species at low $E_{\mathrm{u}}$ with a peak of emission towards GMC 6 and pSSC 5. Therefore, the cold component of and could be chemically linked: being likely a gas phase product (Huang et al. subm.), would thus form in the gas phase, from the reaction + (cite: kahane2013; barone2015; vazart2016; lopezsepulcre024). This scenario is however challenged by the different temperatures traced by the two species since the rotational temperature for the cold component of is less than 30 K, while was found to trace a warmer gas ($T_\text{kin}\geq 70$ K at scales 1.6–5$\ensuremath{''}$ scales and $T_\text{kin}\geq 300$ K at scales $\leq 1\ensuremath{''}$; (cite: mangum_fire_2019), Huang et al. subm.). the low temperature of could result from sub-thermal excitation. Unless the $T_{\mathrm{rot}}$ are underestimated, we cannot conclude whether and are chemically linked and whether the cold component of is a gas-phase or a grain surface product.

On the other hand, the difference of peak velocities and FWHM for the low and high $E_{\mathrm{u}}$ transitions (see Figure [3](#fig:av-GF)) could indicate that truly traces two different gas components. Indeed, this warmer ($T_{\mathrm{rot}}> 50$ K) component, clearly present in GMC 6 and pSSC 2, shows narrower mean FWHM compared to the cold gas component and warmer rotational temperatures (see Figure [4](#fig:summary_LTE)). Hence, another formation pathway could be involved for the warm component of , different from that of the cold component. As for , we further investigate the origin of this emission in Sec. [5.3](#subsec:chemical_variations).

###  and 

From the literature, is proposed to form on the ice grain surfaces through radical-radical reactions (cite: garrod2008; KK2011; forstel2017; enriqueromero2022) or from the successive hydrogenation of (cite: woon2002; theule2011; sil2018; dejesus2021; molpeceres_ch3nh2_2024). Whilst the first pathways over-predicts abundances (cite: garrod2008), the second possible pathway has been supported by chemical models reproducing observed abundances of towards high-mass protostars (cite: suzuki2016; suzuki2023). This second pathway would indicate that is a precursor of and would also form on the ice grain mantles. However, studies have shown that the conversion of to would be too fast to account for the gas phase abundance of (cite: theule2011; suzuki2016). In addition, very recently, (cite: molpeceres_ch3nh2_2024) proposed a grain surface formation route for from the chemisorbate, without passing through as an intermediate species. From the recent literature, it does seem that the two species are not necessarily chemically linked as it was thought before. Alternatively from the grain surface production, the neutral-neutral gas phase reaction + $\rightarrow$ + H has also been proposed as a viable formation pathway in warm ($T>100$ K) regions (cite: bocherel1996; halfen2013). Similarly for , various gas-phase formation pathways (ion-molecules or neutral-neutral reactions involving or ; see e.g. Table 11 of (cite: suzuki2016)) have been proposed as a viable alternative for the formation of (cite: bocherel1996; turner1999; suzuki2016; sil2018).

From Table [3](#tab:av_GF), both the peak velocities and FHWM of and are consistent with each other (and considering the spectral resolution of 10 km s$^{-1}$) in all the four regions investigated. From the RDs, we found similar rotational temperatures between and the warm component of in all the regions but GMC 6 (see Figure [4](#fig:summary_LTE)), although it was shown that temperatures were underestimated in the case of . For the column densities, since was found to emit at smaller scales than GMC scales (see Sec. [4.3](#sec: nonlte)), we compare the column densities of and of the warm component of at pSSC scales only. From Figure [4](#fig:summary_LTE), the column densities of the warm component of and of are relatively constant across the regions, as seen also in their abundance ratio: Figure [6](#fig:correlations) shows very good correlation (panel e) between and the cold component of , whilst the correlation becomes weaker (high p-value, panel j) correlation between and the warm component of . This weak correlation might be due to the slight decrease in the abundance ratio towards GMC 6, which seems to come from a higher column density in . However, the LVG results did not confirm this increase of towards GMC 6 and the correlation between the two species could be strong for both components of .

If the correlation between and is true, the two species could be chemically linked (see Fig [7](#fig:summary), hypothesis ii). Since the grain formation pathways linking and are not viable to explain gas-phase abundance of (see above), the two species can be chemically linked if they share the same precursor. On the grain, the new proposed formation route of the two species from indicates that both species can have HCN and HNC as precursors, without being a precursor of . In the gas phase, formation pathways involving and are viable for both species but only for temperatures above 100 K. Hence, should the two species be chemically linked, both grain surface and gas phase reaction can account for the correlation and the chemical link. Our current results, however, do not allow us to distinguish between the two possibilities. Alternatively, the correlation could indicate that the two species trace similar physical processes of formation across the various regions (cite: quenard2018; belloche2020).

![](correlations_plots_unified.pdf)

## Possible origins of the iCOMs in the CMZ of NGC 253

In the previous section, we have discussed the iCOMs possible formation pathways and whether any pair of iCOMs has a chemical link. We discuss below the physical process that could be responsible for the iCOMs emission towards the CMZ of NGC 253.

A first inspection of the emission distribution of the iCOMs in this study shows that the emission is (1) mostly concentrated towards the inner part of the CMZ, within $6\ensuremath{''}$ around the kinematic centre, (2) compact around each GMC, and (3) sometimes unresolved for the higher upper-level energies, depending the species. From the images, we thus hypothesize that the emission could be emitted on GMC scales (of the size of the order of the ALCHEMI beam size or 1.6$\ensuremath{''}$) and unresolved pSSC scales ($\sim 0.12\ensuremath{''}$ or a few parsecs), which are the next biggest sub-structures identified within the GMCs (cite: ando_2017; leroy_forming_2018). As we could not derive the emission size of the iCOMs, except for , we discuss how they would be produced at GMC and pSSC scales (Sections [5.2.1](#subsec:GMC_scales) and [5.2.2](#subsec:SSC_scales), respectively) in the following.

### iCOMs production at GMC-scales

Several studies derived the volume density and kinetic temperature of the molecular gas in the disk of NGC 253, and found at least two components (cite: rosenberg_radiative_2014; gorski_survey_2017; perez-beaupuits_thorough_2018; mangum_fire_2019; tanaka_2023). The most recent study by (cite: tanaka_2023) (consistent with previous studies), derived a gas temperature and density for the low-density component (dominated by the low-J lines of CO and its isotopologues) of 85 K and $2\times10^3$ cm$^{-3}$, respectively, and for the high-density component (dominated by high-density tracers with $E_{\mathrm{u}}\leq 70$K) of 110 K and $\sim 3\times10^4$ cm$^{-3}$, respectively. The dust temperatures were estimated to be around 35–40 K (cite: leroy_alma_2015; martin_alchemi_2021). (cite: leroy_alma_2015) derived line widths for the GMCs of NGC 253 of $\sim 20-40$ km s$^{-1}$ using observations of bulk gas tracers (e.g., low-J lines of CO, HCN, HCO$^+$, and isotopologues).

On average, the derived rotational temperatures ($T_{\text{rot}}\leq 60$K) for the iCOMs are thus below the gas temperatures found at GMC scales. At the densities measured (i.e. $n_{\mathrm{\ce{H2}}}\sim 10^3-10^4$ cm$^{-3}$), the dust and gas are likely not coupled. Most recent laboratory experiments and quantum chemical calculations of binding energies showed that and would desorb at a lower dust temperature than water ($\sim 100-120$ K; (cite: chaabouni2018; ferrero2022; molpeceres2022)), whilst would co-desorb with water at around 140 K (cite: perrero2024). On the other hand, is refractory to water desorption and would desorb at higher dust temperatures ($\geq 170 - 300$ K; e.g., (cite: urso2017; chaabouni2018; ligterink2018; martindomenech2020; ferrero2020; chuang2022)). Therefore, the dust temperature derived at GMC scales ($35-40$ K) is too low to desorb the iCOMs, if they formed on the icy grain mantles. The iCOMs are very likely sub-thermally excited and are released into the gas phase via non-thermal processes if they formed on the grains. With the CRIR being relatively high ($\zeta \sim 10^{-14}-10^{-12}$ s$^{-1}$; e.g., (cite: holdship_energizing_2022; behrens_tracing_2022; behrens2024)) towards the CMZ of NGC 253, CR-induced grain heating and sputtering desorption mechanisms (cite: roberts2007; dartois2019; paulive2022; arslan2023) could be an important process to desorb these iCOMs.

Another important non-thermal process in NGC 253 releasing the species from the ice grain mantles into the gas phase could be shock sputtering. On average, we measured line widths mostly around $40-60$ km s$^{-1}$(see Table [3](#tab:av_GF)) for the cold gas component (component 1) of the iCOMs. These values are on average larger than the line widths derived by (cite: leroy_alma_2015) for the GMCs (between $20-40$ K) which could indicate that the species trace a more turbulent gas. However, as already mentioned, we cannot exclude possible optical depth effects as is the case for . If we consider moderate to high optical depth ($\tau\sim0.6-3$) as we found for , we could overestimate linewidths between 12% and 30%[^7]. In the most optically-thick case derived ($\tau=3$), for a FWHM of 60 km s$^{-1}$the opacity-corrected linewidth would still be above that of GMCs but it would not be the case for a FWHM of 40 km s$^{-1}$.

#### O-bearing iCOMs:

From Sec. [5.1.1](#subsec:link_o-bearing), we found that and could be chemically linked. If this is the case, then the cold component of could be produced in the gas phase from , which would have been sputtered from the grain through shocks. Alternatively, both species could be formed on the grain and be linked with as a precursor of (cite: chuang2020; fedoseev2022) but the gas phase abundance ratio would thus not be representative of the ice abundances (see Sec. [5.1.1](#subsec:link_o-bearing)). In any case, and tracing shocks would be consistent with the fact that both species are detected in protostellar shocks in our Galaxy (cite: arce2008; lefloch2017; holdship2019; csengeri2019; codella_outflow_2020; desimone2020; busch2024).

#### N-bearing iCOMs, including :

Since has not been detected in cold clouds (cite: lopezsepulcre2019) and the rotational temperatures for the cold component are low ($<30$ K) enough to point to sub-thermal excitation, the cold component of is also very likely tracing shocked gas. This would be consistent with what is seen and modelled in Galactic shocked regions (cite: arce2008; burkhardt2019; codella2017; lopezsepulcre024). The correlation of with at GMC scales (see Figure [6](#fig:correlations)d) could indicate similar physical conditions across the regions for the formation environment of the two species (cite: quenard2018; belloche2020), since no chemical reaction linking the two species has been reported in the literature. On the other hand, we found that and could be chemically linked or could trace the same physical process (see Sec. [5.1.3](#subsec:link_N-bearing)). Therefore, and are also very likely tracing shocked gas. Recently, (cite: zeng2018) found abundant N-bearing species towards G+0.693-0.027, a molecular cloud in the Galactic Centre. They mentioned that the rich chemistry of this source is due to the fact that it is dominated by low-velocity shocks and the high cosmic-ray ionisation rates (cite: rivilla2022_POp; sanz-novo2024). They report a ratio \[\]/\[\] and \[\]/\[\] of 5, which is of the same order of magnitude as our value of $\sim 3$, for both ratios.

Overall, at GMC scales, sputtering due to large-scale shocks is likely the main process releasing the iCOMs into the gas phase. Signatures of shocks have been previously found within the CMZ of NGC 253 were already found in previous studies towards NGC 253 (cite: garcia-burillo2000; meier_alma_2015; haasler_first_2022; harada_alchemi_2022; huang_reconstructing_2023). Large-scale shocks traced by iCOMs would also be consistent with the origin of , the simplest iCOM, which is also tracing shocks within NGC 253 (e.g. (cite: humire_methanol_2022), Huang et al. subm.). We compared the emission distribution of with that of and around $E_{\mathrm{u}}=20$ K and found a relatively good correlation, except towards GMC 7 where we retrieve the O- vs N- disparity. The contour maps of the above-mentioned transitions are shown in Figure [38](#fig:ch3oh_sup_mols). Following the possible shock scenarios by (cite: huang_reconstructing_2023) (see their Figure 12), the shocks traced by the iCOMs could be due to either star-formation within each GMC (via shocks induced by outflows or sporadic shocks due to scattered star-formation episodes; see scenario 2a in Figure [7](#fig:summary)) or cloud-cloud collisions (see scenario 1 in Figure [7](#fig:summary)).

The intersection of different orbits (such as Lindblad resonances; (cite: iodice2014)) can cause large-scale cloud-cloud collisions (cite: harada_alchemi_2022; humire_methanol_2022). However, the regions we observe are not located close to such intersections, which indicates that the large-scale shocks traced by the iCOMs are either due to cloud-cloud collisions occurring within the GMCs (scenario 1 in Figure [7](#fig:summary)) or to star formation activity (scenario 2a in Figure [7](#fig:summary)). From the LVG analysis, we found that is emitted on size scales between 0.15$\ensuremath{''}-0.6\ensuremath{''}$ which corresponds to 2.5–10 pc in linear scales, supporting the large-scale shocks scenario within GMCs. The situation could resemble that of our Galactic centre, where widespread emission of iCOMs are detected throughout the CMZ and are likely caused by low-velocity shocks due to cloud-cloud collisions (cite: requena-torres_organic_2006; jones2011; li_2017_widespread_coms; li_2020_widespread_coms; zeng2020). Chemical modelling will help disentangle between the different shock scenarios. Finally, both O- and N-bearing iCOMs are well correlated, except towards GMC 7, where O-bearing species are more abundant than N-bearing species. We discuss this further in Sec. [5.3.1](#sec:GMC7).

### iCOMs production at pSSC-scale

The temperatures of the pSSCs previously derived are $\geq 100$ K (cite: rico-villas_super_2020; krieger_molecular_2020a). The PSSCs show clear outflow features (cite: gorski_2019; levy_outflows_2021), and some of them host Super Hot Cores (SHCs; (cite: rico-villas_super_2020)) from the detection of vibrationally excited emission and densities and temperatures of $\sim 10^6$ cm$^{-3}$ and $\sim 200-300$ K, respectively. Such high temperatures are consistent with the kinetic temperatures derived at scales $\leq 1\ensuremath{''}$ ($\leq 17$ pc) using observations (cite: mangum_fire_2019). The densities of the pSSCs are high enough to consider that the dust and gas are coupled. Therefore, the gas temperature at pSSC scales would be enough to thermally desorb the iCOMs (Scenario 2b in Figure [7](#fig:summary)), should they be formed on grains. Sputtering from shocks due to outflows driven by the forming-stars is also a possible mechanism releasing the iCOMs into the gas phase or to enable a rich gas-phase chemistry leading to the formation of iCOMs (Scenario 2a in Figure [7](#fig:summary)).

As for the GMC scales, the rotational temperatures derived for the iCOMs are much lower ($T_{\text{rot}}\leq 60$ K) than the gas temperature we expect at pSSCs scales, which could indicate that they are tracing a less dense gas. Therefore, the iCOMs are very likely subthermally excited on pSSC scales as well. Due to the limited temperature range for which collisional rates were calculated, we could not constrain the upper limit of the gas kinetic temperature, except for GMC 6, where the range is $T_{\text{rot}}=25-130$ K (see Sec. [4.3](#sec: nonlte)). (cite: suzuki2016) estimated an upper limit for the desorption temperature of of 160 K, consistent with the mean binding energy of 5534 K derived by (cite: ruaud2015). If all the iCOMs trace the same gas component, then and in GMC 6 cannot be thermally desorbed if they formed on the grain. However, higher temperatures are derived in the other regions, which could enable thermal desorption.

#### O-bearing iCOMs:

Both and are detected in shocked regions associated with outflows from protostars (cite: arce2008; lefloch2017), as well as the warm envelope of protostars (cite: belloche2013; fuente2014; jorgensen2018; bonfand2019; lee2019; gorai2024; moller2024). The abundance ratio \[\]/\[\] ranging between $\sim 2.3-5$ (see Figure [6](#fig:correlations)f) corresponds well to the abundance ratio found in low- and high-mass star-forming regions, and shocks linked to protostellar outflows (cite: lefloch2017; chen2023; busch2024).

#### N-bearing iCOMs, including :

The measured abundance ratio of $[\ce{CH3NH2}]/[\ce{NH2CHO}]= 3-10$ towards GMC 7 and pSSC 5 (see Figure [6](#fig:correlations)i) is similar to the ratios measured in high-mass protostars (cite: bogelund2019; nazari2022). The highest ratios derived towards GMC 6 and pSSC 2 (5 and 10, respectively) are in line with the range of values predicted by the chemical models of hot cores by (cite: garrod2022) (see their Table 19). The increase in the abundance ratio is due to the smaller column density of in these regions (see Figure [4](#fig:summary_LTE)). We investigate possible physical causes in Sec. [5.3](#subsec:chemical_variations) below. Finally, the abundance ratio between the warm component of and is close to 3 in all four regions (see Figure [6](#fig:correlations)j), which falls on the lower side of ratios measured in massive protostars ((cite: bogelund2019) and references therein, (cite: suzuki2023)). When comparing to the Hot Core models by (cite: garrod2022), our measured ratios are well below those predicted by the model (see their Table 17). The discrepancy could arise from the lack of destruction routes of in the model (cite: garrod2022). To the best of our knowledge, between the two species, only has been detected in shocked or outflowing regions (cite: widicus_weaver_deep_2017; gorski2023). From the PCA analysis performed by (cite: harada_pca_2024), was correlated with both shock tracers (SiO) and high-energy transitions of , thought to be linked with young starbursts. The warm compact component of could not probe the same gas component as , which can be partially supported by the weak correlation between the two species (see Figure [6](#fig:correlations)).

Overall, if iCOMs are emitted on pSSC scales, the gas could be warm enough to desorb those forming on the icy grain mantles (scenario 2b in Fig. [7](#fig:summary)). Alternatively iCOMs could be tracing shocks, associated (scenario 2a in Fig. [7](#fig:summary)) or not (scenario 1 in Fig. [7](#fig:summary)) with the ongoing star formation. With our current angular resolution, we cannot really distinguish between the different scenarios. Higher angular resolution observations and chemical modelling will be necessary to distinguish between the various processes.

## Chemical variations across regions

In the previous sections, we found some chemical differences between the four regions. On the one hand, we found that GMC 7 presents an enhancement in O-bearing species compared to N-bearing species. On the other hand, we found that whilst high $E_{\mathrm{u}}$ transitions of are excited only towards GMC 6 and pSSC 5, those for are excited in GMC 6 and pSSC 2, indicating an anti-correlation between the two species towards pSSC 5 and pSSC 2. The density between the four regions does not seem to change significantly based on previous studies on various molecular tracers (cite: behrens_tracing_2022; huang_reconstructing_2023; bouvier2024). Hence, the chemical differentiation seen could be real and we investigate in the following what could cause it.

![](summary_icoms_v2.pdf)

### The O- versus N-bearing dichotomy towards GMC 7

The contour maps in Figure [1](#fig:sup-icoms) and the correlation plots in panels b), c), g), and j) of Figure [6](#fig:correlations) show a dichotomy between the O and N-bearing species toward GMC 7. Looking at Table [3](#tab:av_GF), there is no particular shift in $V_{\mathrm{peak}}$ or change in FWHM between N- and O-bearing iCOMs towards GMC 7 which would highlight a different origin of emission between the two types of iCOMs. If we consider the column densities derived at GMC scales (see bottom part of Figure [4](#fig:summary_LTE)), GMC 7 shows a decrease in N-bearing species compared to the other regions, whilst the amount of O-bearing species stay relatively constant. What causes the lack of N-bearing species towards GMC 7, compared to the other regions?

A first factor could be related to a difference in physical conditions in this GMC. In Section [5.2.1](#subsec:GMC_scales), we hypothesised that most of the iCOMs could be linked to shocks occurring within the GMCs. From the analysis of shock species (e.g. HNCO, SiO, and S-bearing species; (cite: huang_reconstructing_2023; bouvier2024)), it was shown that shocks are likely less intense towards GMC 7 compared to the other regions. Stronger shocks would lead to the presence of warmer gas. However, from the gas temperatures derived for in Sec. [4.3](#sec: nonlte), GMC 7 does not show a clear temperature difference compared to the other regions. On the other hand, the column density in GMC 7 is lower compared to the other three regions by approximately one order of magnitude (cite: mangum_fire_2019). A correlation between the amount of formed iCOMs and the column density was found in low-mass and high-mass protostellar cores, indicating that iCOMs formation is more advanced in denser cores (cite: yang_peaches_2021; baek2022). However, in (cite: baek2022), whilst the abundance of was found to be relatively constant with $N_{\ce{H2}}$, , , and were found to grow proportionally with $N_{\ce{H2}}$. Hence, the difference in column density does not seem to explain the O- vs N- dichotomy.

A second factor leading to a difference in O- versus N-bearing iCOMs could be evolutionary. (cite: huang_reconstructing_2023) estimated a timescale for the history of the shocks for each GMC and suggested that shocks towards GMC 7 are older ($\sim 10^4$ yr) than towards the three other GMCs ($\sim 10^3$ yr). Hence, the lower abundance in N-bearing species, if they all trace the same shock event, could be linked to the fact that the shock is older. However, this would contradict what is observed in the Galactic prototypical L1157-B1 shock. There, an anti-correlation between and was observed (cite: codella2017), but the authors showed that was tracing the youngest shock, whilst is tracing the older part of the shock, as the species needs time to be formed in the gas phase. We would thus have expected GMC 7 to be more abundant in N-bearing species if it traced older shocks, which is not the case. We should note that the timescale estimation of the shocks in the GMCs of NGC 253 relies on the assumption that both HNCO and SiO are tracing the same shock episode, which is not necessarily the case.

Studies of high-mass star-forming regions have shown that less evolved sources have a lower amount of N-bearing iCOMs compared to O-bearing ones (cite: beuther2009; suzuki2018; bogelund_NvsO_2019; baek2022). This is explained by the fact that ice or gas-phase nitrogen chemistry takes longer to initiate compared with the chemistry of O-bearing species (cite: charnley1992; beuther2009; garrod2022). Interestingly, (cite: dedes2011) observed three high-mass star-forming regions and found an overabundance of O-bearing species compared to N-bearing ones. However, whilst one of the sources is very young, the other two are relatively evolved with HII regions. Hence, a low N-bearing iCOM abundance does not necessarily imply a younger region. In addition, it is not known whether pSSCs are present within GMC 7, as it was not included in (cite: ando_2017) and (cite: leroy_forming_2018). Understanding the core population could bring additional information on whether the GMC is younger or older compared to the other GMCs. Observations of Radio Recombination Lines (RRLs) and 3mm continuum emission (due to free-free emission), both arising from ionised gas that traces ongoing star formation showed that while there is no clear RRL emission towards GMC 7 but faint 3mm continuum is detected (cite: rodriguez-rico2006; bendo_2015). In addition, only one radio continuum source (unclassified) has been identified in the vicinity of GMC 7, contrarily to the other three regions (cite: ulvestad_1997). Young star-formation could thus be much less active towards GMC 7, which is supported by the lack of line emission usually associated with young starburst towards this region (cite: harada_pca_2024; kishikawa2024). Finally, performing chemical modelling will also be essential to help us understand the lack of N-bearing species towards GMC 7.

### The - excitation condition anti-correlation in pSSC 5 and pSSC 2

The regions GMC 6, pSSC 5, and pSSC 2 show a relatively similar chemical content in terms of iCOMs. There is, however, a small difference between pSSC 5 and pSSC 2, when it comes to the warmer and more compact component (governed by high $E_{\mathrm{u}}$ transitions) that we identified in the rotational diagram analysis (see Sec. [4.2](#subsec:rds)). Indeed, whilst transitions with $E_{\mathrm{u}}$ up to 200 K are detected towards GMC 6 and pSSC 2, it is not the case towards pSSC 5. On the other hand, the situation is reversed for where high $E_{\mathrm{u}}$ transitions, up to 80–100 K, are lacking towards pSSC 2. We investigate below whether known differences between these two regions could explain the lack of high excitation transitions for these two species.

Since the chemical difference concerns transitions for which the emission is mostly unresolved by the ALCHEMI beam, we consider that the difference might come from the small-scale constitution of the GMCs, i.e. at pSSC scales. Our ALCHEMI beam encompasses several of the pSSCs identified by (cite: leroy_forming_2018). Our regions pSSC 5 and pSSC 2 encompass pSSCs 4 to 7 and pSSCs 1 to 3, respectively. In the case of GMC 6, only one pSSC has been identified (pSSC 14). The pSSC’s chemical richness and physical properties have been investigated by a few studies at high angular resolution (cite: krieger_molecular_2020a; levy_outflows_2021; mills_clustered_2021). From these studies, no significant differences in the chemical composition have been found towards the pSSCs of interest for this work. Additionally, all host SHCs so the difference is likely not coming from a difference in source population between the pSSCs. On the other hand, only pSSC 14, pSSC 4 and pSSC 5 show clear outflow features (cite: levy_outflows_2021). If on the scales of pSSCs, and do not probe the same gas component, then we could explain the lack of high excitation transitions of towards our region pSSC 2 if traces shocked gas linked to the pSSC’s outflow whilst traces the forming pSSCs themselves. If is linked to the pSSCs and their hosting SHCs, then a difference between the properties of the sources is needed to explain the lack of high excitation of the species towards pSSC 5. Looking at the gas temperature derived for the SHCs (cite: rico-villas_super_2020), the pSSCs composing our region pSSC 5 seem to have a slightly lower temperature compared to those of regions GMC 6 and pSSC 2. As already mentioned, due to the binding energy range of being the highest among the iCOMs studied here, the region pSSC 5 could thus be less efficient in releasing if it forms on the grain. Moreover, a cooler gas temperature could reflect a younger source, indicating that the pSSC 5 is younger than the two others. However, there is no clear consensus on the evolutionary age pattern of the pSSCs (cite: rico-villas_super_2020; krieger_molecular_2020a; mills_clustered_2021; levy_outflows_2021). This hypothesis does not, in addition, explain why narrower line widths for are detected solely towards pSSC 2.

# Conclusions

We used ALCHEMI ALMA large program measurements to investigate the emission and formation pathways of selected iCOMs, (acetaldehyde), (ethanol), (formamide), (methanimine), and (methylamine), towards the CMZ of NGC 253. We performed radiative transfer analyses to derive rotational temperatures and column densities for each iCOM under study. For , we performed a non-LTE LVG analysis as this was the only iCOM in our study with available collisional rates. We studied the relation between the iCOMs at both GMC and pSSC scales, to see whether chemical and physical differences between iCOMs and regions are present, and how it could relate to the source’s physical or chemical structure. We summarise our main findings below.

- The iCOM emission is mostly concentrated towards the inner part of the CMZ (i.e. within 6$\ensuremath{''}$ or $\sim 100$ pc around the kinematic centre), between GMC 7 and pSSC 2 (close to GMC 3). At similar upper-level energy, and are usually more spatially extended compared to , , and . Finally, emission from iCOMs becomes more compact with increasing $E_{\mathrm{u}}$

- A rotational diagram analysis showed that for , and , two gas components are needed depending on the region, for which we applied two different beam-filling factors, one for a region of emission at the scale of GMCs and the other at the scale of pSSCs.

- All $T_{\text{rot}}$ derived are below 100 K and the majority lie in the range $10-40$ K, indicating that iCOMs are sub-thermally excited. The column densities of and are relatively constant throughout the regions. The N-bearing species, on the other hand, show a decrease towards GMC 7.

- The LVG analysis we performed on shows that both optical depths and non-LTE effects are at play for this species. The derived gas temperature and density show that emits in a gas of at least 20 K and at a density of $6\times10^4$ cm$^{-3}$ for GMC 7, and up to $6\times10^6$ cm$^{-3}$ for GMC 6. The emission size of is more compact than GMC scales ($\sim 0.15\ensuremath{''}-0.6\ensuremath{''}$ or $\sim 2.5-10$ pc).

- The cold extended component of ($E_{\mathrm{u}}< 40$ K) and are well correlated in all four regions, which could imply a chemical link between the two species. Gas phase production of from through the could be possible, although we cannot exclude grain formation for the two species.

- The cold extended component of ($E_{\mathrm{u}}<70$ K) and have similar peak of emission within the CMZ of NGC 253. If the two species are chemically linked, as proposed in the literature, then could have formed in the gas phase via the reaction + .

- Both gas components of are well correlated with , respectively, which could indicate that they are either tracing a similar physical process or that they formed through the same precursor on the ice grain mantle or in the gas phase. Our current results do not allow us to conclude between the two possibilities.

- If the iCOMs emit at GMC scales, the most favourable scenario to explain the widespread emission of the iCOMs is if they are tracing large-scale shocks within the GMCs. This resembles what is seen in the centre of our own Galaxy.

- Part of the iCOM emission may come from smaller scales, such as pSSC scales. Both thermal and non-thermal desorption may be thus at play, due to the heating from the forming stars. Not all iCOMs may trace the same gas component, some of them likely tracing heating processes (e.g. , ) whilst the others may rather trace shock processes due to active star-formation (e.g. , , ). We can however not firmly conclude on the origin of the iCOMs at pSSC scales without higher angular resolution or chemical modelling.

- At GMC scales (governed by a cold extended component of the iCOMs), GMC 7 shows a deficiency in N-bearing iCOMs compared to the other regions. The cause may be a different evolutionary stage of GMC  or to the fact that star formation is simply less active in that region.

- pSSC 5 and pSSC 2 show different excitation conditions for and . Whilst does not have a warm component towards pSSC 5, does not have a warm component towards pSSC 2. The difference could be partially explained if the two species are tracing different features, with tracing the outflows driven by the pSSCs and tracing the heating sources. However, we cannot explain the significant narrow line widths of that are solely present towards pSSC 2.

This first study of iCOMs towards the CMZ of NGC 253 shows that several processes could be involved in their emission. The current angular resolution allows us to put some constraints on the region of emission of the iCOMs and their formation pathways, but chemical modelling and higher angular resolution observations will be crucial to address all the questions raised in this work. In addition, while in Galactic studies high angular resolution helps to determine precisely where iCOMs are emitted, this remains a challenge in extragalactic studies.

# Acknowledgements

We thank the anonymous referee who helped improve the clarity of the paper. This work is founded by the European Research Council (ERC) Advanced Grant MOPPEX 833460. V.M.R. and L.C. acknowledge support from the grant PID2022-136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. V.M.R. also aknowledges the grant RYC2020-029387-I funded by MICIU/AEI/10.13039/501100011033 and by "ESF, Investing in your future", and from the Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología (CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC); and from the grant CNS2023-144464 funded by MICIU/AEI/10.13039/501100011033 and by “European Union NextGenerationEU/PRTR”. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00161.L and ADS/JAO.ALMA#2018.1.00162.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research has made use of spectroscopic and collisional data from the EMAA database (https://emaa.osug.fr and https://dx.doi.org/10.17178/EMAA).

193 natexlab

(ref: aikawa2020) Aikawa, Y., Furuya, K., Yamamoto, S., & Sakai, N. 2020, ApJ, 897, 110

(ref: ando_2017) Ando, R., Nakanishi, K., Kohno, K., et al. 2017, ApJ, 849, 81

(ref: arce2008) Arce, H. G., Santiago-Garcı́a, J., Jørgensen, J. K., Tafalla, M., & Bachiller, R. 2008, ApJL, 681, L21

(ref: arslan2023) Arslan, Ö., Hocuk, S., Caselli, P., & Küçük, İ. 2023, MNRAS, 518, 2050

(ref: baek2022) Baek, G., Lee, J.-E., Hirota, T., Kim, K.-T., & Kim, M. K. 2022, ApJ, 939, 84

(ref: BG2020) Barger, C. J. & Garrod, R. T. 2020, ApJ, 888, 38

(ref: barone2015) Barone, V., Latouche, C., Skouteris, D., et al. 2015, MNRAS, 453, L31

(ref: behrens_tracing_2022) Behrens, E., Mangum, J. G., Holdship, J., et al. 2022, ApJ, 939, 119

(ref: behrens2024) Behrens, E., Mangum, J. G., Viti, S., et al. 2024, ApJ, 977, 38

(ref: belloche2019) Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10

(ref: belloche2020) Belloche, A., Maury, A. J., Maret, S., et al. 2020, A&A, 635, A198

(ref: belloche2013) Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013, A&A, 559, A47

(ref: bendo_2015) Bendo, G. J., Beswick, R. J., D’Cruze, M. J., et al. 2015, MNRAS, 450, L80

(ref: bennett2005) Bennett, C. J., Jamieson, C. S., Osamura, Y., & Kaiser, R. I. 2005, ApJ, 624, 1097

(ref: beuther2009) Beuther, H., Zhang, Q., Bergin, E. A., & Sridharan, T. K. 2009, AJ, 137, 406

(ref: bianchi2019) Bianchi, E., Codella, C., Ceccarelli, C., et al. 2019, MNRAS, 483, 1850

(ref: bianchi2022) Bianchi, E., López-Sepulcre, A., Ceccarelli, C., et al. 2022, ApJL, 928, L3

(ref: bisschop2007) Bisschop, S. E., Fuchs, G. W., van Dishoeck, E. F., & Linnartz, H. 2007, A&A, 474, 1061

(ref: blake_1987) Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips, T. G. 1987, ApJ, 315, 621

(ref: bocherel1996) Bocherel, P., Herbert, L., Rowe, B., et al. 1996, JPhCh, 100, 3063

(ref: bogelund_NvsO_2019) Bøgelund, E. G., Barr, A. G., Taquet, V., et al. 2019a, A&A, 628, A2

(ref: bogelund2019) Bøgelund, E. G., McGuire, B. A., Hogerheijde, M. R., van Dishoeck, E. F., & Ligterink, N. F. W. 2019b, A&A, 624, A82

(ref: bonfand2019) Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27

(ref: bouscasse2024) Bouscasse, L., Csengeri, T., Wyrowski, F., Menten, K. M., & Bontemps, S. 2024, A&A, 686, A252

(ref: bouvier2024) Bouvier, M., Viti, S., Behrens, E., et al. 2024, A&A, 689, A64

(ref: brucato2006) Brucato, J. R., Baratta, G. A., & Strazzulla, G. 2006, A&A, 455, 395

(ref: burkhardt2019) Burkhardt, A. M., Shingledecker, C. N., Le Gal, R., et al. 2019, ApJ, 881, 32

(ref: burton1992) Burton, W. B., Elmegreen, B. G., Genzel, R., et al. 1992, Saas-Fee Advanced Course 21: The Galactic Interstellar Medium

(ref: busch2024) Busch, L. A., Belloche, A., Garrod, R. T., Müller, H. S. P., & Menten, K. M. 2024, A&A, 681, A104

(ref: caselli1993) Caselli, P., Hasegawa, T. I., & Herbst, E. 1993, ApJ, 408, 548

(ref: ceccarelli2017) Ceccarelli, C., Caselli, P., Fontani, F., et al. 2017, ApJ, 850, 176

(ref: ceccarelli2023) Ceccarelli, C., Codella, C., Balucani, N., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 379

(ref: ceccarelli_2003) Ceccarelli, C., Maret, S., Tielens, A. G. G. M., Castets, A., & Caux, E. 2003, A&A, 410, 587

(ref: chaabouni2018) Chaabouni, H., Diana, S., Nguyen, T., & Dulieu, F. 2018, A&A, 612, A47

(ref: charnley2004) Charnley, S. B. 2004, Advances in Space Research, 33, 23

(ref: charnley1992) Charnley, S. B., Tielens, A. G. G. M., & Millar, T. J. 1992, ApJL, 399, L71

(ref: chen2024) Chen, Y., Rocha, W. R. M., van Dishoeck, E. F., et al. 2024, A&A, 690, A205

(ref: chen2023) Chen, Y., van Gelder, M. L., Nazari, P., et al. 2023, A&A, 678, A137

(ref: chuang2020) Chuang, K. J., Fedoseev, G., Qasim, D., et al. 2020, A&A, 635, A199

(ref: chuang2022) Chuang, K. J., Jäger, C., Krasnokutski, S. A., Fulvio, D., & Henning, T. 2022, ApJ, 933, 107

(ref: codella_outflow_2020) Codella, C., Ceccarelli, C., Bianchi, E., et al. 2020, A&A, 635, A17

(ref: codella2017) Codella, C., Ceccarelli, C., Caselli, P., et al. 2017, A&A, 605, L3

(ref: coletta2020) Coletta, A., Fontani, F., Rivilla, V. M., et al. 2020, A&A, 641, A54

(ref: costagliola2015) Costagliola, F., Sakamoto, K., Muller, S., et al. 2015, A&A, 582, A91

(ref: csengeri2019) Csengeri, T., Belloche, A., Bontemps, S., et al. 2019, A&A, 632, A57

(ref: danger2011) Danger, G., Borget, F., Chomat, M., et al. 2011, A&A, 535, A47

(ref: dartois2019) Dartois, E., Chabot, M., Id Barkach, T., et al. 2019, A&A, 627, A55

(ref: dejesus2021) de Jesus, D. N., da Silva, J. M. B. A., Tejero, T. N., et al. 2021, MNRAS, 501, 1202

(ref: desimone2020) De Simone, M., Codella, C., Ceccarelli, C., et al. 2020, A&A, 640, A75

(ref: dedes2011) Dedes, C., Leurini, S., Wyrowski, F., et al. 2011, A&A, 526, A59

(ref: dore2012) Dore, L., Bizzocchi, L., & Degli Esposti, C. 2012, A&A, 544, A19

(ref: dore2010) Dore, L., Bizzocchi, L., Degri Esposti, C., & Gauss, J. 2010, J. Mol. Spectrosc., 263, 44

(ref: dulieu2019) Dulieu, F., Nguyen, T., Congiu, E., Baouche, S., & Taquet, V. 2019, MNRAS, 484, L119

(ref: eibensteiner2022) Eibensteiner, C., Barnes, A. T., Bigiel, F., et al. 2022, A&A, 659, A173

(ref: endres2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: enriqueromero2021) Enrique-Romero, J., Ceccarelli, C., Rimola, A., et al. 2021, A&A, 655, A9

(ref: enriqueromero016) Enrique-Romero, J., Rimola, A., Ceccarelli, C., & Balucani, N. 2016, MNRAS, 459, L6

(ref: enriqueromero2022) Enrique-Romero, J., Rimola, A., Ceccarelli, C., et al. 2022, ApJS, 259, 39

(ref: faure2018) Faure, A., Lique, F., & Remijan, A. J. 2018, Journal of Physical Chemistry Letters, 9, 3199

(ref: fedoseev2016) Fedoseev, G., Chuang, K. J., van Dishoeck, E. F., Ioppolo, S., & Linnartz, H. 2016, MNRAS, 460, 4297

(ref: fedoseev2022) Fedoseev, G., Qasim, D., Chuang, K.-J., et al. 2022, ApJ, 924, 110

(ref: ferrero2022) Ferrero, S., Grieco, F., Ibrahim Mohamed, A. S., et al. 2022, MNRAS, 516, 2586

(ref: ferrero2020) Ferrero, S., Zamirri, L., Ceccarelli, C., et al. 2020, ApJ, 904, 11

(ref: forstel2017) Förstel, M., Bergantini, A., Maksyutenko, P., Góbi, S., & Kaiser, R. I. 2017, ApJ, 845, 83

(ref: fuente2014) Fuente, A., Cernicharo, J., Caselli, P., et al. 2014, A&A, 568, A65

(ref: garcia-burillo2000) Garcı́a-Burillo, S., Martı́n-Pintado, J., Fuente, A., & Neri, R. 2000, A&A, 355, 499

(ref: garrod2022) Garrod, R. T., Jin, M., Matis, K. A., et al. 2022, ApJS, 259, 1

(ref: garrod2008) Garrod, R. T., Widicus Weaver, S. L., & Herbst, E. 2008, ApJ, 682, 283

(ref: goldsmith_1999) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: golshan2024) Golshan, R. H., Sánchez-Monge, Á., Schilke, P., et al. 2024, A&A, 688, A3

(ref: gorai2020) Gorai, P., Bhat, B., Sil, M., et al. 2020, ApJ, 895, 86

(ref: gorai2024) Gorai, P., Law, C.-Y., Tan, J. C., et al. 2024, ApJ, 960, 127

(ref: gorski_survey_2017) Gorski, M., Ott, J., Rand, R., et al. 2017, ApJ, 842, 124

(ref: gorski2023) Gorski, M. D., Aalto, S., König, S., et al. 2023, A&A, 670, A70

(ref: gorski_2019) Gorski, M. D., Ott, J., Rand, R., et al. 2019, MNRAS, 483, 5434

(ref: haasler_first_2022) Haasler, D., Rivilla, V. M., Martín, S., et al. 2022, A&A, 659, A158

(ref: halfen2013) Halfen, D. T., Ilyushin, V. V., & Ziurys, L. M. 2013, ApJ, 767, 66

(ref: harada_alchemi_2022) Harada, N., Martin, S., Mangum, J., et al. 2022, ApJ, 938, 80

(ref: harada_starburst_2021) Harada, N., Martín, S., Mangum, J. G., et al. 2021, ApJ, 923, 24

(ref: harada_pca_2024) Harada, N., Meier, D. S., Martín, S., et al. 2024, ApJS, 271, 38

(ref: haupa2022) Haupa, K. A., Joshi, P. R., & Lee, Y.-P. 2022, Journal of Chinese Chemical Society, 69, 1159

(ref: henkel1987) Henkel, C., Jacq, T., Mauersberger, R., Menten, K. M., & Steppe, H. 1987, A&A, 188, L1

(ref: herbst2009) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: holdship_energizing_2022) Holdship, J., Mangum, J. G., Viti, S., et al. 2022, ApJ, 931, 89

(ref: holdship2019) Holdship, J., Viti, S., Codella, C., et al. 2019, ApJ, 880, 138

(ref: huang2024) Huang, K. Y., Abbink, D., Viti, S., & Garcı́a-Burillo, S. 2024, A&A, 688, A130

(ref: huang_reconstructing_2023) Huang, K.-Y., Viti, S., Holdship, J., et al. 2023, A&A, 675, A151

(ref: humire_methanol_2022) Humire, P. K., Henkel, C., Hernández-Gómez, A., et al. 2022, A&A, 663, A33

(ref: humire_2020) Humire, P. K., Thiel, V., Henkel, C., et al. 2020, A&A, 642, A222

(ref: ibrahim2022) Ibrahim, M., Guillemin, J.-C., Chaquin, P., Markovits, A., & Krim, L. 2022, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 24, 23245

(ref: ilyushin2005) Ilyushin, V. V., Alekseev, E. A., Dyubko, S. F., & Motiyenko, R. A. 2005, J. Mol. Spectrosc., 229, 170

(ref: iodice2014) Iodice, E., Arnaboldi, M., Rejkuba, M., et al. 2014, A&A, 567, A86

(ref: jimenez-serra2025) Jimenez-Serra, I. 2025, arXiv e-prints, arXiv:2501.01782

(ref: JG2020) Jin, M. & Garrod, R. T. 2020, ApJS, 249, 26

(ref: jones2011) Jones, P. A., Burton, M. G., Tothill, N. F. H., & Cunningham, M. R. 2011, MNRAS, 411, 2293

(ref: jorgensen2018) Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, A&A, 620, A170

(ref: jorgensen2020) Jørgensen, J. K., Belloche, A., & Garrod, R. T. 2020, Annual Review of Astronomy and Astrophysics, 58, 727–778

(ref: kahane2013) Kahane, C., Ceccarelli, C., Faure, A., & Caux, E. 2013, ApJL, 763, L38

(ref: KK2011) Kim, Y. S. & Kaiser, R. I. 2011, ApJ, 729, 68

(ref: kishikawa2024) Kishikawa, R., Harada, N., Saito, T., et al. 2024, arXiv e-prints, arXiv:2411.03867

(ref: KLG1996) Kleiner, I., Lovas, F. J., & Godefroid, M. 1996, J. Phys. Chem. Ref. Data, 25, 4

(ref: krieger_molecular_2020a) Krieger, N., Bolatto, A. D., Leroy, A. K., et al. 2020a, ApJ, 897, 176

(ref: kryvda2009) Kryvda, A. V., Gerasimov, V. G., Dyubko, S. F., Alekseev, E. A., & Motiyenko, R. A. 2009, Journal of Molecular Spectroscopy, 254, 28

(ref: kurtz2000) Kurtz, S., Cesaroni, R., Churchwell, E., Hofner, P., & Walmsley, C. M. 2000, in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell, 299–326

(ref: lamberts2019) Lamberts, T., Markmeyer, M. N., Kolb, F. J., & Kästner, J. 2019, ACS Earth and Space Chemistry, 3, 958

(ref: lee2019) Lee, C.-F., Codella, C., Li, Z.-Y., & Liu, S.-Y. 2019, ApJ, 876, 63

(ref: lefloch2017) Lefloch, B., Ceccarelli, C., Codella, C., et al. 2017, MNRAS, 469, L73

(ref: leroy_alma_2015) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25

(ref: leroy_forming_2018) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2018, ApJ, 869, 126

(ref: levy_outflows_2021) Levy, R. C., Bolatto, A. D., Leroy, A. K., et al. 2021, ApJ, 912, 4

(ref: li2024_correlations) Li, C., Qin, S.-L., Liu, T., et al. 2024, MNRAS, 533, 1583

(ref: li_2017_widespread_coms) Li, J., Shen, Z., Wang, J., et al. 2017, ApJ, 849, 115

(ref: li_2020_widespread_coms) Li, J., Wang, J., Qiao, H., et al. 2020, MNRAS, 492, 556

(ref: ligterink2018) Ligterink, N. F. W., Terwisscha van Scheltinga, J., Taquet, V., et al. 2018, MNRAS, 480, 3628

(ref: lopezsepulcre2019) López-Sepulcre, A., Balucani, N., Ceccarelli, C., et al. 2019, ACS Earth and Space Chemistry, 3, 2122

(ref: lopezsepulcre024) López-Sepulcre, A., Codella, C., Ceccarelli, C., Podio, L., & Robuschi, J. 2024, arXiv e-prints, arXiv:2411.00495

(ref: lopezsepulcre2015) López-Sepulcre, A., Jaber, A. A., Mendoza, E., et al. 2015, MNRAS, 449, 2438

(ref: lu2024) Lu, Y., Quan, D., Chang, Q., Chen, L.-F., & Li, D. 2024, arXiv e-prints, arXiv:2412.06397

(ref: mangum_fire_2019) Mangum, J. G., Ginsburg, A. G., Henkel, C., et al. 2019, ApJ, 871, 170

(ref: maret_2011) Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, A&A, 526, A47

(ref: martin_2011) Martín, S., Krips, M., Martín-Pintado, J., et al. 2011, A&A, 527, A36

(ref: martin_2006) Martín, S., Mauersberger, R., Martín-Pintado, J., Henkel, C., & García-Burillo, S. 2006, ApJS, 164, 450

(ref: martindomenech2020) Martı́n-Doménech, R., Öberg, K. I., & Rajappan, M. 2020, ApJ, 894, 98

(ref: martin_alchemi_2021) Martín, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46

(ref: matthews1985) Matthews, H. E., Friberg, P., & Irvine, W. M. 1985, ApJ, 290, 609

(ref: mauersberger1991) Mauersberger, R., Henkel, C., Walmsley, C. M., Sage, L. J., & Wiklind, T. 1991, A&A, 247, 307

(ref: mccarthy1987) McCarthy, P. J., van Breugel, W., & Heckman, T. 1987, AJ, 93, 264

(ref: mccormick_2013) McCormick, A., Veilleux, S., & Rupke, D. S. N. 2013, ApJ, 774, 126

(ref: meier_alma_2015) Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, ApJ, 801, 63

(ref: mills_clustered_2021) Mills, E. A. C., Gorski, M., Emig, K. L., et al. 2021, ApJ, 919, 105

(ref: mininni2023) Mininni, C., Beltrán, M. T., Colzi, L., et al. 2023, A&A, 677, A15

(ref: moller2024) Möller, T., Schilke, P., Sánchez-Monge, Á., & Schmiedeke, A. 2024, arXiv e-prints, arXiv:2412.04040

(ref: molpeceres2024) Molpeceres, G., Furuya, K., & Aikawa, Y. 2024, A&A, 688, A150

(ref: molpeceres2022) Molpeceres, G., Kästner, J., Herrero, V. J., Peláez, R. J., & Maté, B. 2022, A&A, 664, A169

(ref: molpeceres_ch3nh2_2024) Molpeceres, G., Tsuge, M., Furuya, K., Watanabe, N., et al. 2024, J. Phys. Chem. A, 128, 3874-3889

(ref: muller2016) Müller, H. S. P., Belloche, A., Xu, L.-H., et al. 2016, A&A, 587, A92

(ref: muller_2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, JMoSt, 742, 215

(ref: muller2011) Muller, S., Beelen, A., Guélin, M., et al. 2011, A&A, 535, A103

(ref: muller2021) Muller, S., Ubachs, W., Menten, K. M., Henkel, C., & Kanekar, N. 2021, A&A, 652, A5

(ref: muller-sanchez2010) Müller-Sánchez, F., González-Martín, O., Fernández-Ontiveros, J. A., Acosta-Pulido, J. A., & Prieto, M. A. 2010, ApJ, 716, 1166

(ref: nazari2022) Nazari, P., Meijerhof, J. D., van Gelder, M. L., et al. 2022, A&A, 668, A109

(ref: osterbrock1974) Osterbrock, D. E. 1974, Astrophysics of gaseous nebulae (A Series of Books in Astronomy and Astrophysics, San Franciso: Freeman)

(ref: paulive2022) Paulive, A., Carder, J. T., & Herbst, E. 2022, MNRAS, 516, 4097

(ref: pearson2008) Pearson, J. C., Brauer, C. S., & Drouin, B. J. 2008, Journal of Molecular Spectroscopy, 251, 394

(ref: peng2022) Peng, Y., Liu, T., Qin, S.-L., et al. 2022, MNRAS, 512, 4419

(ref: perrero2022) Perrero, J., Enrique-Romero, J., Martı́nez-Bachs, B., et al. 2022, ACS Earth and Space Chemistry, 6, 496

(ref: perrero2024) Perrero, J., Vitorino, J., Congiu, E., et al. 2024, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 26, 18205

(ref: pickett_1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: perez-beaupuits_thorough_2018) Pérez-Beaupuits, J. P., Güsten, R., Harris, A., et al. 2018, ApJ, 860, 23

(ref: qiu2018) Qiu, J., Wang, J., Shi, Y., et al. 2018, A&A, 613, A3

(ref: quenard2018) Quénard, D., Jiménez-Serra, I., Viti, S., Holdship, J., & Coutens, A. 2018, MNRAS, 474, 2796

(ref: raunier2004) Raunier, S., Chiavassa, T., Duvernay, F., et al. 2004, A&A, 416, 165

(ref: rekola_distance_2005) Rekola, R., Richer, M. G., McCall, M. L., et al. 2005, MNRAS, 361, 330

(ref: requena-torres_organic_2006) Requena-Torres, M. A., Martín-Pintado, J., Rodríguez-Franco, A., et al. 2006, A&A, 455, 971

(ref: rico-villas_super_2020) Rico-Villas, F., Martin-Pintado, J., Gonzalez-Alfonso, E., Martin, S., & Rivilla, V. M. 2020, MNRAS, 491, 4573

(ref: rimola2018) Rimola, A., Skouteris, D., Balucani, N., et al. 2018, ACS Earth and Space Chemistry, 2, 720

(ref: rivilla2022_POp) Rivilla, V. M., Garcı́a De La Concepción, J., Jiménez-Serra, I., et al. 2022a, Frontiers in Astronomy and Space Sciences, 9, 829288

(ref: rivilla2022) Rivilla, V. M., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2022b, Frontiers in Astronomy and Space Sciences, 9, 876870

(ref: roberts2007) Roberts, J. F., Rawlings, J. M. C., Viti, S., & Williams, D. A. 2007, MNRAS, 382, 733

(ref: rocha2024) Rocha, W. R. M., van Dishoeck, E. F., Ressler, M. E., et al. 2024, A&A, 683, A124

(ref: rodriguez-rico2006) Rodrı́guez-Rico, C. A., Goss, W. M., Zhao, J. H., Gómez, Y., & Anantharamaiah, K. R. 2006, ApJ, 644, 914

(ref: rosenberg_radiative_2014) Rosenberg, M. J. F., Kazandjian, M. V., van der Werf, P. P., et al. 2014, A&A, 564, A126

(ref: ruaud2015) Ruaud, M., Loison, J. C., Hickson, K. M., et al. 2015, MNRAS, 447, 4004

(ref: rubin2019) Rubin, M., Altwegg, K., Balsiger, H., et al. 2019, MNRAS, 489, 594

(ref: sakamoto_2011) Sakamoto, K., Mao, R.-Q., Matsushita, S., et al. 2011, ApJ, 735, 19

(ref: sanz-novo2024) Sanz-Novo, M., Rivilla, V. M., Jiménez-Serra, I., et al. 2024, ApJ, 965, 149

(ref: sewilo_detection_2018) Sewiło, M., Indebetouw, R., Charnley, S. B., et al. 2018, ApJ, 853, L19

(ref: shimonishi_detection_2023) Shimonishi, T., Tanaka, K. E. I., Zhang, Y., & Furuya, K. 2023, ApJL, 946, L41

(ref: sil2018) Sil, M., Gorai, P., Das, A., et al. 2018, ApJ, 853, 139

(ref: sivaramakrishnan2009) Sivaramakrishnan, R., Su, M.-C., Michael, J. V., et al. 2009, J. Phys. Chem., A, 114, 755

(ref: skouteris2018) Skouteris, D., Balucani, N., Ceccarelli, C., et al. 2018, ApJ, 854, 135

(ref: skouteris2017) Skouteris, D., Vazart, F., Ceccarelli, C., et al. 2017, MNRAS, 468, L1

(ref: suzuki2023) Suzuki, T., Majumdar, L., Goldsmith, P. F., et al. 2023, ApJ, 954, 189

(ref: suzuki2016) Suzuki, T., Ohishi, M., Hirota, T., et al. 2016, ApJ, 825, 79

(ref: suzuki2018) Suzuki, T., Ohishi, M., Saito, M., et al. 2018, ApJS, 237, 3

(ref: tanaka_2023) Tanaka, K., Mangum, J. G., Viti, S., et al. 2024, ApJ, 961, 18

(ref: tercero2018) Tercero, B., Cuadrado, S., López, A., et al. 2018, A&A, 620, L6

(ref: theule2011) Theule, P., Borget, F., Mispelaer, F., et al. 2011, A&A, 534, A64

(ref: turner1999) Turner, B. E., Terzieva, R., & Herbst, E. 1999, ApJ, 518, 699

(ref: ulvestad_1997) Ulvestad, J. S. & Antonucci, R. R. J. 1997, ApJ, 488, 621

(ref: urso2017) Urso, R. G., Scirè, C., Baratta, G. A., et al. 2017, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 19, 21759

(ref: vanderwalt_2021) van der Walt, S. J., Kristensen, L. E., Jørgensen, J., et al. 2021, A&A, 655, A86

(ref: VH2013) Vasyunin, A. I. & Herbst, E. 2013, ApJ, 769, 34

(ref: vazart2016) Vazart, F., Calderini, D., Puzzarini, C., Skouteris, D., & Barone, V. 2016, J. Chem. Theory Comput., 12, 5385

(ref: vazart2020) Vazart, F., Ceccarelli, C., Balucani, N., Bianchi, E., & Skouteris, D. 2020, MNRAS, 499, 5547

(ref: viti_evaporation_2004) Viti, S., Collings, M. P., Dever, J. W., McCoustra, M. R. S., & Williams, D. A. 2004, MNRAS, 354, 1141

(ref: widicus_weaver_deep_2017) Widicus Weaver, S. L., Laas, J. C., Zou, L., et al. 2017, ApJS, 232, 3

(ref: woon2002) Woon, D. E. 2002, ApJL, 571, L177

(ref: xue2024) Xue, C., Remijan, A., Faure, A., et al. 2024, The Astrophysical Journal, 967, 164

(ref: yamamoto2017) Yamamoto, S. 2017, Introduction to Astrochemsitry: chemical Evolution from Interstellar Clouds to Star and Planet Formation (Springer)

(ref: yang_peaches_2021) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, ApJ, 910, 20

(ref: zeng2018) Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2018, MNRAS, 478, 2962

(ref: zeng2020) Zeng, S., Zhang, Q., Jiménez-Serra, I., et al. 2020, MNRAS, 497, 4896

# Integrated Intensity Images

The velocity integrated maps for , , , , and , are presented here. The velocities used for the integration are within the range 70-380 km s$^{-1}$.

![](CH3NH2-maps-v2.pdf)

![](CH2NH-maps_CORR_paper.pdf)

![](CH3CHO-maps.pdf)

![](NH2CHO-maps_v2.pdf)

![](C2H5OH-maps.pdf)

# Spectra

Table [2](#tab:lines) shows all the transitions used in the analyses, for each species and the best Gaussian fit. The calibration error of 15% is not included in the uncertainties of the integrated intensities and the spectral resolution of 10 km s$^{-1}$is not included in the error of $V_{\mathrm{peak}}$ and $FWHM$. Those quantities are however taken into account in the analysis. Frequencies and spectroscopic parameters are taken from CDMS (cite: muller_2005; endres2016) for (TAG 029518; version 2$^*$; (cite: dore2010; dore2012)), (TAG 045516, version 2$^*$; e.g., (cite: kryvda2009)), and (TAG 046524, version 1$^*$; (cite: pearson2008; muller2016)) and from JPL (cite: pickett_1998) for (TAG 44003, version 3$^*$; (cite: KLG1996) and references therein) and (TAG 31008, version 1$^*$; (cite: ilyushin2005)). The mean FHWM and $V_\mathrm{peak}$ used in Sec. [4.2](#subsec:rds) are presented in Table [3](#tab:av_GF). The line profiles and Gaussian fits are shown in Figures [13](#fig:spec_ch3cho_GMC6) to [31](#fig:spec_c2H5OH_SSC5). The full line identification is available in (cite: martin_alchemi_2021).

+:-------:+----------:+:-----------------------:+-----------------:+:---------------------:+-----------------:+-----------------:+:-----------------:+:----------------:+-------:+
| Species | Frequency | Transition              | $E_{\mathrm{u}}$ | $A_{ij}$              | $g_{\mathrm{u}}$ | $\int T_BdV$     | $V_\mathrm{peak}$ | $FWHM$           | rms    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | (MHz)     |                         | \(K\)            | (s$^{-1}$)            |                  | (K.km s$^{-1}$)  | (km s$^{-1}$)     | (km s$^{-1}$)    | (mK)   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         |           |                         |                  |                       |                  |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
| Species | Frequency | Transition              | $E_{\mathrm{u}}$ | $A_{ij}$              | $g_{\mathrm{u}}$ | $\int T_BdV$     | $V_\mathrm{peak}$ | $FWHM$           | rms    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | (MHz)     |                         | \(K\)            | (s$^{-1}$)            |                  | (K.km s$^{-1}$)  | (km s$^{-1}$)     | (km s$^{-1}$)    | (mK)   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         |           |                         |                  |                       |                  |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 225554    | $1_{1,1}-0_{0,0}$       | 10.8             | $9.63\times 10^{-5}$  | 9                | $3.32 \pm 0.17$  | $172.6 \pm 1.9$   | $79.6 \pm 4.8$   | 4.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 172267    | $2_{1,1}-2_{0,2}$       | 17.5             | $6.12\times 10^{-5}$  | 15               | $4.31 \pm 0.72$  | $168.5 \pm 4.5$   | $54.4 \pm 10.6$  | 8.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 199823    | $3_{1,2}-2_{1,1}$       | 27.1             | $6.35\times 10^{-5}$  | 21               | $6.91 \pm 0.61$  | $165.4 \pm 2.6$   | $66.2 \pm 7.7$   | 16.4   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 245125    | $4_{1,4}-3_{1,3}$       | 37.3             | $1.28\times 10^{-4}$  | 27               | $3.04 \pm 0.25$  | $175.5 \pm 1.9$   | $50.5 \pm 5.0$   | 6.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 266270    | $4_{1,3}-3_{1,2}$       | 39.8             | $1.64\times 10^{-4}$  | 27               | $3.79 \pm 0.31$  | $174.4 \pm 2.0$   | $56.5 \pm 5.9$   | 4.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 317405    | $5_{0,5}-4_{0,4}$       | 45.9             | $3.03\times 10^{-4}$  | 33               | $3.83 \pm 0.23$  | $176.3 \pm 2.2$   | $50.0 \pm 10.0$  | 8.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 332572    | $5_{1,4}-4_{1,3}$       | 55.8             | $3.35\times 10^{-4}$  | 33               | $2.05 \pm 0.16$  | $170.0 \pm 10.0$  | $50.0 \pm 10.0$  | 6.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 215108    | $3_{-1,3}-2_{0,2}$      | 17.0             | $5.22\times 10^{-5}$  | 84               | $2.01 \pm 0.17$  | $169.3 \pm 2.1$   | $49.4 \pm 4.7$   | 5.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 264172    | $4_{1,5}-3_{0,5}$       | 25.9             | $8.74\times 10^{-5}$  | 108              | $2.38 \pm 0.24$  | $171.9 \pm 2.5$   | $52.9 \pm 6.5$   | 6.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 307791    | $5_{-1,3}-4_{0,2}$      | 36.3             | $1.44\times 10^{-4}$  | 132              | $1.40 \pm 0.36$  | $167.0 \pm 8.9$   | $68.8 \pm 19.7$  | 5.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 310528    | $5_{1,5}-4_{0,5}$       | 36.6             | $1.43\times 10^{-4}$  | 132              | $1.12 \pm 0.26$  | $175.9 \pm 7.8$   | $64.3 \pm 16.5$  | 5.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 126247    | $6_{0,6}-5_{0,5}$       | 21.3             | $1.41\times 10^{-4}$  | 13               | $2.99 \pm 0.62$  | $159.3 \pm 4.0$   | $45.5 \pm 10.2$  | 9.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 131617    | $6_{1,5}-5_{1,4}$       | 25.1             | $1.56\times 10^{-4}$  | 13               | $3.47 \pm 0.26$  | $163.1 \pm 2.0$   | $54.9 \pm 4.7$   | 7.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 146871    | $7_{0,7}-6_{0,6}$       | 28.4             | $2.25\times 10^{-4}$  | 15               | $2.10 \pm 0.24$  | $158.6 \pm 3.4$   | $56.8 \pm 7.6$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 128102    | $6_{2,4}-5_{2,3}$       | 33.4             | $1.31\times 10^{-4}$  | 13               | $1.88 \pm 0.37$  | $161.2 \pm 3.8$   | $41.7 \pm 10.6$  | 6.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 149792    | $7_{2,5}-6_{2,4}$       | 40.6             | $2.19\times 10^{-4}$  | 15               | $1.67 \pm 0.37$  | $156.3 \pm 4.2$   | $38.7 \pm 10.5$  | 11.2   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 171620    | $8_{2,6}-7_{2,5}$       | 48.8             | $3.39\times 10^{-4}$  | 17               | $0.54 \pm 0.22$  | $149.3 \pm 3.7$   | $16.4 \pm 7.0$   | 9.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 239951    | $11_{1,10}-10_{1,9}$    | 72.4             | $9.96\times 10^{-4}$  | 23               | $0.42 \pm 0.11$  | $177.3 \pm 2.5$   | $20.6 \pm 6.7$   | 3.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 95963     | $5_{0,5}-4_{0,4}$ A     | 13.8             | $2.84\times 10^{-5}$  | 22               | $15.33 \pm 0.71$ | $148.8 \pm 1.7$   | $125.0 \pm 7.4$  | 5.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 95947     | $5_{0,5}-4_{0,4}$ E     | 13.9             | $2.84\times 10^{-5}$  | 22               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98900     | $5_{1,4}-4_{1,3}$ A     | 16.5             | $2.99 \times 10^{-5}$ | 22               | $6.50 \pm 0.56$  | $140.3 \pm 2.7$   | $74.6 \pm 8.2$   | 8.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98863     | $5_{1,4}-4_{1,3}$ E     | 16.6             | $2.99 \times 10^{-5}$ | 22               | $5.64 \pm 0.35$  | $139.1 \pm 1.8$   | $59.5 \pm 4.1$   | 8.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 114959    | $6_{0,6}-5_{0,5}$ A     | 19.4             | $4.96 \times 10^{-5}$ | 26               | $7.65 \pm 0.43$  | $173.8 \pm 2.2$   | $80.2 \pm 5.4$   | 14.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 114940    | $6_{0,6}-5_{0,5}$ E     | 19.4             | $4.96 \times 10^{-5}$ | 26               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 112248    | $6_{1,6}-5_{1,5}$ A     | 21.1             | $4.50 \times 10^{-5}$ | 26               | $5.68 \pm 0.36$  | $156.8 \pm 1.8$   | $59.0 \pm 4.2$   | 8.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 112254    | $6_{1,6}-5_{1,5}$ E     | 21.2             | $4.50 \times 10^{-5}$ | 26               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96274     | $5_{2,4}-4_{2,3}$ A     | 22.9             | $2.41 \times 10^{-5}$ | 22               | $1.77 \pm 0.19$  | $163.1 \pm 4.4$   | $60.0 \pm 10.0$  | 5.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96632     | $5_{2,3}-4_{2,2}$ A     | 22.9             | $2.44 \times 10^{-5}$ | 22               | $1.44 \pm 0.25$  | $163.0 \pm 10.0$  | $60.0 \pm 10.0$  | 5.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96475     | $5_{2,3}-4_{2,2}$ E     | 23.0             | $2.42 \times 10^{-5}$ | 22               | $1.50 \pm 0.28$  | $166.4 \pm 4.6$   | $57.9 \pm 14.8$  | 5.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133854    | $7_{0,7}-6_{0,6}$A      | 25.8             | $7.92 \times 10^{-5}$ | 30               | $7.48 \pm 0.70$  | $140.3 \pm 3.5$   | $121.6 \pm 13.9$ | 8.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 133830    | $7_{0,7}-6_{0,6}$E      | 25.8             | $7.92 \times 10^{-5}$ | 30               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 138319    | $7_{1,6}-6_{1,5}$ A     | 28.8             | $8.75\times 10^{-5}$  | 30               | $3.44 \pm 0.47$  | $178.6 \pm 4.3$   | $66.4 \pm 11.1$  | 10.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 138284    | $7_{1,6}-6_{1,5}$ E     | 28.9             | $8.75\times 10^{-5}$  | 30               | $1.82 \pm 0.83$  | $179.8 \pm 12.2$  | $58.3 \pm 23.3$  | 10.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 152607    | $8_{0,8}-7_{0,7}$ E     | 33.2             | $1.18 \times 10^{-4}$ | 34               | $2.16 \pm 0.60$  | $165.8 \pm 7.1$   | $53.0 \pm 18.2$  | 9.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 149507    | $8_{1,8}-7_{1,7}$ A     | 34.6             | $1.10 \times 10^{-4}$ | 34               | $3.52 \pm 0.95$  | $168.0 \pm 7.7$   | $59.4 \pm 18.6$  | 10.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 149505    | $8_{1,8}-7_{1,7}$ E     | 34.7             | $1.10 \times 10^{-4}$ | 34               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 168093    | $9_{1,9}-8_{1,8}$ A     | 42.7             | $1.57 \times 10^{-4}$ | 38               | $1.44 \pm 0.24$  | $164.5 \pm 3.7$   | $42.0 \pm 6.7$   | 8.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 168088    | $9_{1,9}-8_{1,8}$ E     | 42.7             | $1.57 \times 10^{-4}$ | 38               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 152656    | $4_{2,2}-3_{1,3}$       | 13.4             | $1.60 \times 10^{-5}$ | 9                | $3.69 \pm 0.60$  | $163.2 \pm 3.9$   | $52.9 \pm 10.0$  | 10.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 159781    | $5_{2,4}-4_{1,3}$       | 17.6             | $1.97 \times 10^{-5}$ | 11               | $3.42 \pm 0.35$  | $156.6 \pm 4.3$   | $60.0 \pm 10.0$  | 11.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133323    | $7_{1,7}-6_{0,6}$       | 23.9             | $1.83 \times 10^{-5}$ | 15               | $5.51 \pm 0.30$  | $165.3 \pm 2.3$   | $60.0 \pm 10.0$  | 8.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 131103    | $5_{3,3}-5_{2,4}$       | 23.9             | $1.17 \times 10^{-5}$ | 11               | $0.87 \pm 0.18$  | $175.4\pm 2.5$    | $24.1 \pm 6.0$   | 7.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 218654    | $7_{2,5}-6_{1,6}$       | 28.7             | $2.69 \times 10^{-5}$ | 15               | $1.00 \pm 0.21$  | $170.0 \pm 5.6$   | $53.8 \pm 13.5$  | 4.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 236299    | $6_{3,3}-5_{2,4}$       | 28.9             | $7.17 \times 10^{-5}$ | 13               | $1.12 \pm 0.14$  | $169.9 \pm 4.3$   | $50.0 \pm 10.0$  | 4.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 147427    | $8_{1,8}-7_{0,7}$       | 30.2             | $2.57 \times 10^{-5}$ | 17               | $4.49 \pm 0.25$  | $166.0 \pm 1.8$   | $61.5 \pm 3.9$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 142285    | $9_{0,9}-8_{1,8}$       | 37.2             | $2.30 \times 10^{-5}$ | 19               | $2.87 \pm 0.37$  | $165.2 \pm 3.4$   | $55.4 \pm 8.8$   | 6.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 196458    | $12_{0,12}-11_{1,11}$   | 63.9             | $6.96\times 10^{-5}$  | 25               | $1.47 \pm 0.22$  | $161.2 \pm 4.5$   | $40.0 \pm 10.0$  | 8.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
| GMC 6                                                                                                                                                                          |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 225554    | $1_{1,1}-0_{0,0}$       | 10.8             | $9.63\times 10^{-5}$  | 9                | $4.56 \pm 0.31$  | $178.0 \pm 3.0$   | $86.7 \pm 6.7$   | 4.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 172267    | $2_{1,1}-2_{0,2}$       | 17.5             | $6.12\times 10^{-5}$  | 15               | $7.22 \pm 0.37$  | $175.2 \pm 2.1$   | $70.1 \pm 4.1$   | 15.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 199823    | $3_{1,2}-2_{1,1}$       | 27.1             | $6.35\times 10^{-5}$  | 21               | $18.40 \pm 0.84$ | $176.2 \pm 1.2$   | $53.4 \pm 2.8$   | 29.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 245125    | $4_{1,4}-3_{1,3}$       | 37.3             | $1.28\times 10^{-4}$  | 27               | $13.23 \pm 0.40$ | $186.1 \pm 0.8$   | $55.1 \pm 1.9$   | 5.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 266270    | $4_{1,3}-3_{1,2}$       | 39.8             | $1.64\times 10^{-4}$  | 27               | $16.06 \pm 0.23$ | $183.8 \pm 0.4$   | $56.6 \pm 1.0$   | 6.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 192212    | $4_{1,3}-4_{0,4}$       | 39.8             | $8.01\times 10^{-5}$  | 27               | $13.93 \pm 0.62$ | $176.5 \pm 1.3$   | $62.4 \pm 2.9$   | 11.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 317405    | $5_{0,5}-4_{0,4}$       | 45.9             | $3.03\times 10^{-4}$  | 33               | $14.65 \pm 0.39$ | $188.9 \pm 0.7$   | $56.5 \pm 1.8$   | 5.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 178073    | $5_{0,5}-4_{1,4}$       | 45.9             | $2.92\times 10^{-5}$  | 33               | $8.38 \pm 1.46$  | $167.9 \pm 4.7$   | $57.1 \pm 12.4$  | 35.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 192469    | $3_{2,1}-2_{2,0}$       | 49.9             | $3.55\times 10^{-5}$  | 21               | $1.57 \pm 0.43$  | $183.2 \pm 6.1$   | $40.5 \pm 12.6$  | 11.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 207380    | $5_{1,4}-5_{0,5}$       | 55.8             | $9.63\times 10^{-5}$  | 33               | $7.12 \pm 0.74$  | $185.8 \pm 2.6$   | $55.9 \pm 6.2$   | 10.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 332572    | $5_{1,4}-4_{1,3}$       | 55.8             | $3.35\times 10^{-4}$  | 33               | $11.54 \pm 0.20$ | $191.8 \pm 0.5$   | $58.1 \pm 1.2$   | 6.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 251421    | $6_{0,6}-5_{1,5}$       | 64.1             | $9.08\times 10^{-5}$  | 39               | $6.96 \pm 0.33$  | $188.4 \pm 1.2$   | $51.4 \pm 2.9$   | 15.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 367072    | $6_{1,6}-5_{1,5}$       | 69.6             | $4.63\times 10^{-4}$  | 39               | $6.80 \pm 0.90$  | $189.2 \pm 3.4$   | $55.1 \pm 9.3$   | 15.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 278642    | $8_{1,7}-8_{0,8}$       | 122.7            | $1.92\times 10^{-4}$  | 51               | $1.27 \pm 0.27$  | $197.3 \pm 2.5$   | $43.1 \pm 5.8$   | 6.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 312336    | $9_{1,8}-9_{0,9}$       | 151.3            | $2.49\times 10^{-4}$  | 57               | $1.42 \pm 0.32$  | $189.1 \pm 5.9$   | $49.0 \pm 14.1$  | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 84305     | $1_{1,5}-1_{0,5}$       | 6.6              | $2.28\times 10^{-6}$  | 36               | $2.91 \pm 0.21$  | $170.4 \pm 1.6$   | $44.8 \pm 3.5$   | 9.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169447    | $2_{1,2}-1_{0,3}$       | 10.6             | $2.69\times 10^{-5}$  | 60               | $10.57 \pm 0.93$ | $163.4 \pm 2.4$   | $61.7 \pm 5.5$   | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 215108    | $3_{-1,3}-2_{0,2}$      | 17.0             | $5.22\times 10^{-5}$  | 84               | $9.22 \pm 0.44$  | $177.6 \pm 1.3$   | $56.3 \pm 3.2$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 226045    | $3_{-1,1}-2_{0,0}$      | 17.2             | $6.06\times 10^{-5}$  | 28               | $4.03 \pm 0.27$  | $179.6 \pm 2.1$   | $65.3 \pm 5.0$   | 5.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 237143    | $2_{2,4}-2_{1,4}$       | 22.0             | $3.82\times 10^{-5}$  | 156              | $2.45 \pm 0.82$  | $172.9 \pm 8.5$   | $51.4 \pm 19.6$  | 7.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 248571    | $2_{2,7}-2_{1,7}$       | 22.3             | $6.39\times 10^{-5}$  | 156              | $1.42 \pm 0.17$  | $187.0 \pm 3.4$   | $59.3 \pm 8.5$   | 5.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 339723    | $2_{2,2}-1_{-1,3}$      | 22.6             | $2.18\times 10^{-4}$  | 60               | $7.06 \pm 0.29$  | $179.5 \pm 1.2$   | $73.6 \pm 3.9$   | 9.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 370166    | $3_{2,4}-2_{1,4}$       | 28.4             | $2.11\times 10^{-4}$  | 84               | $2.65 \pm 0.56$  | $186.2 \pm 5.9$   | $49.5 \pm 11.1$  | 13.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 239446    | $3_{2,5}-3_{1,5}$       | 28.8             | $4.42\times 10^{-5}$  | 84               | $2.15 \pm 0.22$  | $175.6 \pm 2.3$   | $46.5 \pm 5.6$   | 5.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 239427    | $4_{2,4}-4_{1,4}$       | 36.9             | $4.08\times 10^{-5}$  | 108              |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 307791    | $5_{-1,3}-4_{0,2}$      | 36.3             | $1.44\times 10^{-4}$  | 132              | $4.32 \pm 1.09$  | $181.5 \pm 6.7$   | $47.4 \pm 12.8$  | 5.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 306877    | $5_{1,6}-4_{0,7}$       | 36.6             | $1.24\times 10^{-4}$  | 44               | $1.45 \pm 0.21$  | $174.6 \pm 3.1$   | $43.8 \pm 7.2$   | 5.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 310528    | $5_{1,5}-4_{0,5}$       | 36.6             | $1.43\times 10^{-4}$  | 132              | $5.04 \pm 0.70$  | $183.0 \pm 3.8$   | $54.7 \pm 8.8$   | 10.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 249929    | $4_{2,7}-4_{1,7}$       | 37.2             | $5.78\times 10^{-5}$  | 36               | $1.28 \pm 0.19$  | $171.3 \pm 2.8$   | $39.9 \pm 8.3$   | 5.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 354843    | $6_{1,2}-5_{0,3}$       | 49.2             | $2.16\times 10^{-4}$  | 156              | $3.37 \pm 0.60$  | $190.1 \pm 3.6$   | $46.8 \pm 9.3$   | 10.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 353388    | $6_{1,6}-5_{0,7}$       | 49.4             | $1.96\times 10^{-4}$  | 52               | $1.73 \pm 0.32$  | $184.1 \pm 4.1$   | $42.8 \pm$7.9    | 9.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 365746    | $6_{1,0}-5_{0,1}$       | 49.5             | $2.36\times 10^{-4}$  | 52               | $1.89 \pm 0.39$  | $177.9 \pm 5.0$   | $47.1 \pm 11.3$  | 8.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 220827    | $7_{0,3}-6_{1,2}$       | 59.8             | $3.59\times 10^{-5}$  | 180              | $1.39 \pm 0.07$  | $174.9 \pm 1.2$   | $46.8 \pm 3.0$   | 6.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233802    | $6_{2,5}-6_{1,5}$       | 60.7             | $3.42\times 10^{-5}$  | 156              | $0.72 \pm 0.17$  | $178.8 \pm 4.1$   | $40.3 \pm 13.8$  | 5.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 242262    | $6_{-2,3}-6_{1,2}$      | 60.9             | $6.39\times 10^{-5}$  | 156              | $1.46 \pm 0.25$  | $186.2 \pm 4.1$   | $48.3 \pm 9.4$   | 5.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 235735    | $8_{-2,3}-8_{1,2}$      | 92.8             | $6.13\times 10^{-5}$  | 204              | $0.87 \pm 0.49$  | $196.8 \pm 7.1$   | $35.7 \pm 15.2$  | 4.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 126247    | $6_{0,6}-5_{0,5}$       | 21.3             | $1.41\times 10^{-4}$  | 13               | $9.66 \pm 0.40$  | $170.5 \pm 1.3$   | $64.1 \pm 3.0$   | 9.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 131617    | $6_{1,5}-5_{1,4}$       | 25.1             | $1.56\times 10^{-4}$  | 13               | $9.91 \pm 3.33$  | $166.7 \pm 0.9$   | $52.1 \pm 2.0$   | 7.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 146871    | $7_{0,7}-6_{0,6}$       | 28.4             | $2.25\times 10^{-4}$  | 15               | $8.21 \pm 1.55$  | $161.5 \pm 6.0$   | $65.6 \pm 13.5$  | 8.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 142701    | $7_{1,7}-6_{1,6}$       | 30.4             | $2.02\times 10^{-4}$  | 15               | $5.25 \pm 0.95$  | $169.9 \pm 3.6$   | $46.9 \pm 6.3$   | 13.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 128102    | $6_{2,4}-5_{2,3}$       | 33.4             | $1.31\times 10^{-4}$  | 13               | $8.04 \pm 0.60$  | $164.1 \pm 2.1$   | $63.5 \pm 5.5$   | 8.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 167320    | $8_{0,8}-7_{0,7}$       | 36.4             | $3.35\times 10^{-4}$  | 17               | $4.49 \pm 0.42$  | $179.8 \pm 3.0$   | $61.9 \pm 5.7$   | 11.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 149792    | $7_{2,5}-6_{2,4}$       | 40.6             | $2.19\times 10^{-4}$  | 15               | $6.92 \pm 0.57$  | $175.4 \pm 4.9$   | $61.0 \pm 6.0$   | 12.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169299    | $8_{2,7}-7_{2,6}$       | 48.5             | $3.26\times 10^{-4}$  | 17               | $4.94 \pm 0.41$  | $176.8 \pm 2.9$   | $80.0 \pm 8.5$   | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 171620    | $8_{2,6}-7_{2,5}$       | 48.8             | $3.39\times 10^{-4}$  | 17               | $2.65 \pm 0.40$  | $182.4 \pm 4.0$   | $46.6 \pm 6.5$   | 10.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 196865    | $9_{1,8}-8_{1,7}$       | 50.4             | $5.43\times 10^{-4}$  | 19               | $4.42 \pm 0.39$  | $179.8 \pm 3.0$   | $61.9 \pm 5.7$   | 11.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 207679    | $10_{0,10}-9_{0,9}$     | 55.4             | $6.47\times 10^{-4}$  | 21               | $2.24 \pm 0.49$  | $187.3 \pm 4.2$   | $36.1 \pm 8.9$   | 8.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 148667    | $7_{3,5}-6_{3,4}$       | 55.4             | $1.91\times 10^{-4}$  | 15               | $3.04 \pm 0.33$  | $169.5 \pm 2.1$   | $39.6 \pm 5.5$   | 12.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169955    | $8_{3,6}-7_{3,5}$       | 63.5             | $3.02\times 10^{-4}$  | 17               | $1.29 \pm 0.29$  | $181.7 \pm 3.1$   | $27.3 \pm 6.4$   | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 223452    | $11_{1,11}-10_{1,10}$   | 67.5             | $8.05\times 10^{-4}$  | 23               | $2.51 \pm 0.20$  | $193.6 \pm 1.8$   | $44.9 \pm 4.1$   | 5.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 215687    | $10_{2,8}-9_{2,7}$      | 68.5             | $6.98\times 10^{-4}$  | 21               | $2.93 \pm 0.59$  | $195.0 \pm 5.1$   | $52.9 \pm 12.9$  | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 239951    | $11_{1,10}-10_{1,9}$    | 72.4             | $9.96\times 10^{-4}$  | 23               | $2.28 \pm 0.56$  | $181.0 \pm 8.5$   | $61.9 \pm 23.2$  | 9.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 148598    | $7_{4,4}-6_{4,3}$       | 76.2             | $1.57\times 10^{-4}$  | 15               | $2.18 \pm 0.41$  | $161.6 \pm 3.5$   | $43.5 \pm 9.0$   | 12.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 148599    | $7_{4,3}-6_{4,2}$       | 76.2             | $1.57\times 10^{-4}$  | 15               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 232273    | $11_{2,10}-10_{2,9}$    | 79.1             | $8.82\times 10^{-4}$  | 23               | $2.18 \pm 0.30$  | $189.4 \pm 3.6$   | $56.6 \pm 9.8$   | 8.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 243521    | $12_{1,12}-11_{1,11}$   | 79.2             | $1.05\times 10^{-3}$  | 25               | $2.50 \pm 0.30$  | $200.0 \pm 2.9$   | $48.1 \pm 6.5$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 237896    | $11_{2,9}-10_{2,8}$     | 79.9             | $9.48\times 10^{-4}$  | 23               | $2.83 \pm 0.52$  | $200.7 \pm 5.0$   | $58.2 \pm 13.5$  | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 212572    | $10_{3,8}-9_{3,7}$      | 82.9             | $6.33\times 10^{-4}$  | 21               | $2.50 \pm 0.33$  | $193.1 \pm 3.3$   | $47.8 \pm 7.3$   | 6.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169861    | $8_{4,5}-7_{4,4}$       | 84.4             | $2.63\times 10^{-4}$  | 17               | $2.62 \pm 0.32$  | $180.3 \pm 2.3$   | $38.3 \pm 5.7$   | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 169862    | $8_{4,4}-7_{4,3}$       | 84.4             | $2.63\times 10^{-4}$  | 17               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233896    | $11_{3,9}-10_{3,8}$     | 94.2             | $8.62\times 10^{-4}$  | 23               | $1.21 \pm 0.29$  | $193.9 \pm 3.4$   | $35.1 \pm 9.1$   | 5.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 234315    | $11_{3,8}-10_{3,7}$     | 94.2             | $8.67\times 10^{-4}$  | 23               | $2.20 \pm 0.65$  | $201.1 \pm 8.0$   | $57.9 \pm 16.8$  | 5.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 148566    | $7_{5,3}-6_{5,2}$       | 103.0            | $1.14\times 10^{-4}$  | 15               | $1.71 \pm 0.40$  | $157.3 \pm 3.8$   | $44.0 \pm 11.1$  | 12.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 148566    | $7_{5,2}-6_{5,1}$       | 103.0            | $1.14\times 10^{-4}$  | 15               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 274001    | $13_{2,12}-12_{2,11}$   | 104.4            | $1.47\times 10^{-3}$  | 27               | $1.40 \pm 0.28$  | $196.1 \pm 3.2$   | $29.8 \pm 5,7$   | 10.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233745    | $11_{4,7}-10_{4,6}$     | 115.1            | $8.07\times 10^{-4}$  | 23               | $1.98 \pm 0.12$  | $184.9 \pm 1.2$   | $38.6 \pm 2.6$   | 3.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 233734    | $11_{4,8}-10_{4,7}$     | 115.1            | $8.07\times 10^{-4}$  | 23               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 276555    | $13_{3,11}-12_{3,10}$   | 119.7            | $1.47\times 10^{-3}$  | 27               | $1.28 \pm 0.72$  | $201.0 \pm 9.3$   | $38.9 \pm 19.2$  | 6.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 277514    | $13_{3,10}-12_{3,9}$    | 119.8            | $1.48\times 10^{-3}$  | 27               | $0.98 \pm 0.27$  | $202.0 \pm 3.4$   | $27.2 \pm 7.8$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 315489    | $15_{2,14}-14_{2,13}$   | 133.6            | $2.27\times 10^{-3}$  | 31               | $1.10 \pm 0.18$  | $195.0 \pm 10.0$  | $36.0 \pm 10.0$  | 4.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 336135    | $16_{2,15}-15_{2,14}$   | 149.8            | $2.76\times 10^{-3}$  | 33               | $1.16 \pm 0.23$  | $200.9 \pm 3.2$   | $33.7 \pm 8.5$   | 9.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 343196    | $17_{1,17}-16_{1,16}$   | 152.1            | $2.97\times 10^{-3}$  | 35               | $2.25 \pm 0.18$  | $195.2 \pm 1.1$   | $34.3 \pm 3.4$   | 8.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 276170    | $13_{5,9}-12_{5,8}$     | 167.3            | $1.32\times 10^{-3}$  | 27               | $1.28 \pm 0.54$  | $196.2 \pm 9.6$   | $40.1 \pm 17.3$  | 7.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 276170    | $13_{5,8}-12_{5,7}$     | 167.3            | $1.32\times 10^{-3}$  | 27               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 297478    | $14_{5,9}-13_{5,8}$     | 181.6            | $1.69\times 10^{-3}$  | 29               | $0.64 \pm 0.18$  | $195.0 \pm 10.0$  | $36.0 \pm 10.0$  | 4.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 297477    | $14_{5,10}-13_{5,9}$    | 181.6            | $1.69\times 10^{-3}$  | 29               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 361484    | $17_{5,13}-16_{5,12}$   | 320.7            | $3.19\times 10^{-3}$  | 35               | $0.90 \pm 0.16$  | $200.4 \pm 2.8$   | $30.6 \pm 5.7$   | 7.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 361492    | $17_{5,12}-16_{5,11}$   | 230.7            | $3.19\times 10^{-3}$  | 35               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 95963     | $5_{0,5}-4_{0,4}$ A     | 13.8             | $2.84\times 10^{-5}$  | 22               | $7.79 \pm 0.43$  | $124.6 \pm 3.3$   | $50.0 \pm 10.0$  | 8.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 95947     | $5_{0,5}-4_{0,4}$ E     | 13.9             | $2.84\times 10^{-5}$  | 22               | $7.45 \pm 0.43$  | $130.7 \pm 2.2$   | $50.0 \pm 10.0$  | 8.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98900     | $5_{1,4}-4_{1,3}$ A     | 16.5             | $2.99 \times 10^{-5}$ | 22               | $7.52 \pm 0.66$  | $138.0 \pm 2.3$   | $61.2 \pm 7.0$   | 9.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98863     | $5_{1,4}-4_{1,3}$ E     | 16.6             | $2.99 \times 10^{-5}$ | 22               | $8.26 \pm 0.70$  | $140.1 \pm 2.2$   | $55.6 \pm 5.7$   | 9.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 114959    | $6_{0,6}-5_{0,5}$ A     | 19.4             | $4.96 \times 10^{-5}$ | 26               | $4.85 \pm 0.98$  | $155.1 \pm 4.7$   | $51.8 \pm 9.3$   | 14.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 114940    | $6_{0,6}-5_{0,5}$ E     | 19.4             | $4.96 \times 10^{-5}$ | 26               | $4.92 \pm 0.85$  | $156.8 \pm 3.3$   | $46.4 \pm 5.6$   | 14.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 112248    | $6_{1,6}-5_{1,5}$ A     | 21.1             | $4.50 \times 10^{-5}$ | 26               | $8.77 \pm 0.44$  | $159.5 \pm 1.4$   | $60.5 \pm 3.8$   | 10.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 112254    | $6_{1,6}-5_{1,5}$ E     | 21.2             | $4.50 \times 10^{-5}$ | 26               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96274     | $5_{2,4}-4_{2,3}$ A     | 22.9             | $2.41 \times 10^{-5}$ | 22               | $2.62 \pm 0.35$  | $133.9 \pm 3.1$   | $49.2 \pm 7.8$   | 6.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96632     | $5_{2,3}-4_{2,2}$ A     | 22.9             | $2.44 \times 10^{-5}$ | 22               | $2.73 \pm 0.57$  | $142.1 \pm 3.2$   | $45.8 \pm 4.2$   | 6.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96475     | $5_{2,3}-4_{2,2}$ E     | 23.0             | $2.42 \times 10^{-5}$ | 22               | $4.07 \pm 0.22$  | $134.0 \pm 1.3$   | $51.1 \pm 3.3$   | 6.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133854    | $7_{0,7}-6_{0,6}$A      | 25.8             | $7.92 \times 10^{-5}$ | 30               | $4.22 \pm 0.26$  | $165.3 \pm 2.2$   | $50.0 \pm$10.0   | 5.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133830    | $7_{0,7}-6_{0,6}$E      | 25.8             | $7.92 \times 10^{-5}$ | 30               | $4.78 \pm 0.28$  | $167.5 \pm 2.2$   | $50.0 \pm 10.0$  | 5.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 293564    | $3_{3,0}-2_{2,1}$ A     | 25.9             | $1.15 \times 10^{-4}$ | 14               | $1.12 \pm 0.47$  | $160.8 \pm 5.4$   | $25.2 \pm 8.2$   | 6.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 293546    | $3_{3,1}-2_{2,0}$ A     | 25.9             | $1.15 \times 10^{-4}$ | 14               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 138319    | $7_{1,6}-6_{1,5}$ A     | 28.8             | $8.75\times 10^{-5}$  | 30               | $4.08 \pm 0.70$  | $179.3 \pm 3.9$   | $48.2 \pm 10.7$  | 14.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 138284    | $7_{1,6}-6_{1,5}$ E     | 28.9             | $8.75\times 10^{-5}$  | 30               | $3.89 \pm 0.52$  | $177.8 \pm 3.0$   | $44.6 \pm 6.4$   | 14.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 152635    | $8_{0,8}-7_{0,7}$ A     | 33.1             | $1.18 \times 10^{-4}$ | 34               | $2.97 \pm 0.20$  | $184.1 \pm 3.8$   | $43.5 \pm 4.2$   | 10.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 152607    | $8_{0,8}-7_{0,7}$ E     | 33.2             | $1.18 \times 10^{-4}$ | 34               | $2.69 \pm 0.25$  | $178.2 \pm 1.8$   | $34.3 \pm 4.1$   | 10.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 149507    | $8_{1,8}-7_{1,7}$ A     | 34.6             | $1.10 \times 10^{-4}$ | 34               | $6.56 \pm 0.44$  | $178.2 \pm 1.7$   | $53.1 \pm 4.1$   | 13.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 149505    | $8_{1,8}-7_{1,7}$ E     | 34.7             | $1.10 \times 10^{-4}$ | 34               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 135476    | $7_{2,5}-6_{2,4}$ E     | 35.1             | $7.40 \times 10^{-5}$ | 30               | $2.05 \pm 0.34$  | $160.5 \pm 4.5$   | $53.7 \pm 9.1$   | 6.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 157974    | $8_{2,7}-7_{1,6}$ A     | 36.4             | $1.29 \times 10^{-4}$ | 38               | $2.84 \pm 0.49$  | $168.2 \pm 3.9$   | $51.1 \pm 10.5$  | 12.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 157937    | $8_{2,7}-7_{1,6}$ E     | 36.5             | $1.29 \times 10^{-4}$ | 38               | $2.54 \pm 0.40$  | $167.2 \pm 3.2$   | $40.8 \pm 6.9$   | 12.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 155342    | $8_{2,6}-7_{2,5}$ A     | 42.5             | $1.17 \times 10^{-4}$ | 34               | $1.32 \pm 0.40$  | $172.7 \pm 3.6$   | $24.1 \pm 8.5$   | 11.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 155179    | $8_{2,6}-7_{2,5}$ E     | 42.5             | $1.15 \times 10^{-4}$ | 34               | $2.99 \pm 0.33$  | $179.8 \pm 4.1$   | $40.0 \pm 10.0$  | 11.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 168093    | $9_{1,9}-8_{1,8}$ A     | 42.7             | $1.57 \times 10^{-4}$ | 38               | $4.99 \pm 0.64$  | $171.3 \pm 4.1$   | $69.2 \pm 11.9$  | 11.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 168088    | $9_{1,9}-8_{1,8}$ E     | 42.7             | $1.57 \times 10^{-4}$ | 38               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 192149    | $10_{2,9}-9_{2,8}$ A    | 59.9             | $2.30\times 10^{-4}$  | 42               | $1.04 \pm 0.39$  | $193.5 \pm 5.0$   | $28.1 \pm 13.2$  | 10.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 205170    | $11_{1,11}-10_{1,10}$ A | 61.5             | $2.90 \times 10^{-4}$ | 46               | $3.12 \pm 0.34$  | $176.5 \pm 6.8$   | $49.1 \pm 5.6$   | 13.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 205161    | $11_{1,11}-10_{1,10}$ E | 61.5             | $2.90 \times 10^{-4}$ | 46               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 214845    | $11_{2,9}-10_{2,8}$ A   | 70.6             | $3.25 \times 10^{-4}$ | 46               | $1.63 \pm 0.42$  | $186.5 \pm 6.9$   | $58.0 \pm 17.1$  | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 214800    | $11_{2,9}-10_{2,8}$ E   | 70.6             | $3.24 \times 10^{-4}$ | 46               | $1.76 \pm 0.42$  | $197.7 \pm 5.3$   | $48.9 \pm 12.2$  | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 223660    | $12_{1,12}-11_{1,11}$ A | 72.2             | $3.78 \times 10^{-4}$ | 50               | $2.97 \pm 0.21$  | $197.1 \pm 2.8$   | $62.0 \pm 4.9$   | 5.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 223650    | $12_{1,12}-11_{1,11}$ E | 72.3             | $3.78 \times 10^{-4}$ | 50               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 230301    | $12_{2,11}-11_{2,10}$ A | 81.0             | $4.04 \times 10^{-4}$ | 39               | $1.79 \pm 0.17$  | $176.5 \pm 1.8$   | $37.7 \pm 3.9$   | 5.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 230315    | $12_{2,11}-11_{2,10}$ E | 81.1             | $4.04 \times 10^{-4}$ | 39               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 212384    | $11_{3,9}-10_{3,8}$ E   | 81.4             | $2.99 \times 10^{-4}$ | 46               | $1.54 \pm 0.16$  | $178.2 \pm 1.8$   | $35.9 \pm 3.3$   | 6.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 212400    | $11_{3,8}-10_{3,7}$ E   | 81.5             | $3.00 \times 10^{-4}$ | 46               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 212498    | $11_{3,8}-10_{3,7}$ A   | 81.5             | $3.01 \times 10^{-4}$ | 46               | $0.69 \pm 0.37$  | $181.2 \pm 8.5$   | $32.8 \pm 22.0$  | 6.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 242118    | $13_{1,13}-12_{1,12}$ A | 83.8             | $4.81 \times 10^{-4}$ | 54               | $2.19 \pm 0.29$  | $192.6 \pm 4.5$   | $50.0 \pm 10.0$  | 5.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 242106    | $13_{1,13}-12_{1,12}$ E | 83.9             | $4.81 \times 10^{-4}$ | 54               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 231592    | $12_{3,10}-11_{3,9}$ A  | 92.6             | $3.96 \times 10^{-4}$ | 50               | $0.75 \pm 0.18$  | $191.2 \pm 5.3$   | $40.2 \pm 8.8$   | 5.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 254827    | $13_{2,11}-12_{2,10}$ E | 94.1             | $5.51 \times 10^{-4}$ | 54               | $2.3 \pm 0.50$   | $179.9 \pm 9.6$   | $48.5 \pm 14.9$  | 7.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 254850    | $13_{2,11}-12_{2,10}$ A | 94.1             | $5.51 \times 10^{-4}$ | 54               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133323    | $7_{1,7}-6_{0,6}$       | 23.9             | $1.83 \times 10^{-5}$ | 15               | $3.35 \pm 0.35$  | $168.9 \pm 3.0$   | $60.2 \pm 7.6$   | 5,7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 236299    | $6_{3,3}-5_{2,4}$       | 28.9             | $7.17 \times 10^{-5}$ | 13               | $2.58 \pm 0.52$  | $177.6 \pm 4.6$   | $49.8 \pm 12.7$  | 4.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 147427    | $8_{1,8}-7_{0,7}$       | 30.2             | $2.57 \times 10^{-5}$ | 17               | $3.07 \pm 0.44$  | $162.7 \pm 4.0$   | $58.9 \pm 10.6$  | 8.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 270444    | $5_{4,2}-4_{3,1}$       | 32.7             | $1.59 \times 10^{-4}$ | 11               | $3.77 \pm 0.49$  | $164.3 \pm 2.6$   | $47.7 \pm 6.1$   | 8.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 270450    | $5_{4,1}-4_{3,2}$       | 32.7             | $1.59 \times 10^{-4}$ | 11               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 254384    | $7_{3,4}-6_{2,5}$       | 34.8             | $8.11 \times 10^{-5}$ | 15               | $1.76 \pm 0.42$  | $167.0 \pm 10.0$  | $40.0 \pm 10.0$  | 7.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 142285    | $9_{0,9}-8_{1,8}$       | 37.2             | $2.30 \times 10^{-5}$ | 19               | $1.88 \pm 0.31$  | $169.4 \pm 4.3$   | $56.4 \pm 12.1$  | 6.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 287917    | $6_{4,3}-5_{3,2}$       | 37.7             | $1.68 \times 10^{-4}$ | 13               | $3.64 \pm 0.40$  | $158.2 \pm 2.4$   | $64.8 \pm 7.8$   | 8.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 287944    | $6_{4,2}-5_{3,3}$       | 37.7             | $1.68 \times 10^{-4}$ | 13               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 214267    | $9_{2,8}-8_{1,7}$       | 42.7             | $4.49 \times 10^{-5}$ | 19               | $3.08 \pm 0.30$  | $157.2 \pm 2.8$   | $66.4 \pm 8.4$   | 7.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 160699    | $10_{0,10}-9_{1,9}$     | 45.3             | $3.51 \times 10^{-5}$ | 21               | $2.73 \pm 0.51$  | $160.6 \pm 7.3$   | $55.0 \pm 10.0$  | 11.4   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 196458    | $12_{0,12}-11_{1,11}$   | 63.9             | $6.96\times 10^{-5}$  | 25               | $1.41 \pm 0.39$  | $170.6 \pm 6.4$   | $49.0 \pm 16.7$  | 9.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 281279    | $17_{0,17}-16_{1,16}$   | 123.9            | $2.28\times 10^{-4}$  | 35               | $1.10 \pm 0.31$  | $182.8 \pm 4.7$   | $34.4 \pm 12.6$  | 7.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
| pSSC 5                                                                                                                                                                         |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 225554    | $1_{1,1}-0_{0,0}$       | 10.8             | $9.63\times 10^{-5}$  | 9                | $2.10 \pm 0.37$  | $251.0 \pm 4.2$   | $53.5 \pm 12.2$  | 6.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 172267    | $2_{1,1}-2_{0,2}$       | 17.5             | $6.12\times 10^{-5}$  | 15               | $3.06\pm 0.37$   | $244.8 \pm 3.2$   | $52.1 \pm 6.7$   | 10.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 199823    | $3_{1,2}-2_{1,1}$       | 27.1             | $6.35\times 10^{-5}$  | 21               | $12.41 \pm 0.71$ | $236.8 \pm 1.2$   | $44.3 \pm 3.2$   | 18.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 245125    | $4_{1,4}-3_{1,3}$       | 37.3             | $1.28\times 10^{-4}$  | 27               | $7.90 \pm 0.17$  | $243.7 \pm 0.41$  | $42.3 \pm 1.2$   | 8.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 266270    | $4_{1,3}-3_{1,2}$       | 39.8             | $1.64\times 10^{-4}$  | 27               | $8.37 \pm 0.26$  | $243.3 \pm 0.61$  | $42.1 \pm 1.7$   | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 192212    | $4_{1,3}-4_{0,4}$       | 39.8             | $8.01\times 10^{-5}$  | 27               | $6.18 \pm 0.80$  | $241.5 \pm 2.5$   | $44.7 \pm 5.2$   | 12.5   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 317405    | $5_{0,5}-4_{0,4}$       | 45.9             | $3.03\times 10^{-4}$  | 33               | $9.37 \pm 0.37$  | $240.9 \pm 1.0$   | $49.8 \pm 2.3$   | 8.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 192469    | $3_{2,1}-2_{2,0}$       | 49.9             | $3.55\times 10^{-5}$  | 21               | $1.49 \pm 1.07$  | $250.7 \pm 10.5$  | $34.7 \pm 18.0$  | 12.5   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 207380    | $5_{1,4}-5_{0,5}$       | 55.8             | $9.63\times 10^{-5}$  | 33               | $3.50 \pm 0.21$  | $243.2 \pm 1.8$   | $34.0 \pm 3.1$   | 12.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 332572    | $5_{1,4}-4_{1,3}$       | 55.8             | $3.35\times 10^{-4}$  | 33               | $7.59 \pm 0.39$  | $247.3 \pm 1.1$   | $48.0 \pm 3.2$   | 8.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 251421    | $6_{0,6}-5_{1,5}$       | 64.1             | $9.08\times 10^{-5}$  | 39               | $3.86 \pm 0.87$  | $239.6 \pm 5.0$   | $50.9 \pm 14.9$  | 7.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 367072    | $6_{1,6}-5_{1,5}$       | 69.6             | $4.63\times 10^{-4}$  | 39               | $4.40 \pm 0.37$  | $240.7 \pm 2.4$   | $57.5 \pm 5.7$   | 12.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 278642    | $8_{1,7}-8_{0,8}$       | 122.7            | $1.92\times 10^{-4}$  | 51               | $0.49 \pm 0.18$  | $248.9 \pm 4.6$   | $23.9 \pm 9.7$   | 5.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 84305     | $1_{1,5}-1_{0,5}$       | 6.6              | $2.28\times 10^{-6}$  | 36               | $2.50 \pm 0.55$  | $239.7 \pm 5.6$   | $50.0 \pm 13.8$  | 10.5   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169447    | $2_{1,2}-1_{0,3}$       | 10.6             | $2.69\times 10^{-5}$  | 60               | $4.73 \pm 0.38$  | $236.3 \pm 2.2$   | $58.9 \pm 4.9$   | 13.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 215108    | $3_{-1,3}-2_{0,2}$      | 17.0             | $5.22\times 10^{-5}$  | 84               | $5.17 \pm 0.29$  | $243.9 \pm 1.2$   | $47.2 \pm 3.3$   | 6.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 226045    | $3_{-1,1}-2_{0,0}$      | 17.2             | $6.06\times 10^{-5}$  | 28               | $2.55 \pm 0.26$  | $243.6 \pm 2.7$   | $56.6 \pm 7.3$   | 5.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 333839    | $2_{2,0}-1_{-1,1}$      | 22.5             | $2.07\times10^{-4}$   | 20               | $1.04 \pm 0.20$  | $243.9 \pm 4.8$   | $44.5 \pm 9.5$   | 6.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 339723    | $2_{2,2}-1_{-1,3}$      | 22.6             | $2.18\times 10^{-4}$  | 60               | $3.34 \pm 0.30$  | $240.9 \pm 2.5$   | $40.0 \pm 10.0$  | 10.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 264172    | $4_{1,5}-3_{0,5}$       | 25.9             | $8.74\times 10^{-5}$  | 108              | $4.47 \pm 0.54$  | $241.7 \pm 2.3$   | $45.1 \pm 7.0$   | 5.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 370166    | $3_{2,4}-2_{1,4}$       | 28.4             | $2.11\times 10^{-4}$  | 84               | $2.52 \pm 0.47$  | $243.0 \pm 4.3$   | $44.6 \pm 8.7$   | 13.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 239446    | $3_{2,5}-3_{1,5}$       | 28.8             | $4.42\times 10^{-5}$  | 84               | $1.90 \pm 0.27$  | $230.4 \pm 2.5$   | $41.2 \pm 7.5$   | 4.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 239427    | $4_{2,4}-4_{1,4}$       | 36.9             | $4.08\times 10^{-5}$  | 108              |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 254161    | $3_{-2,3}-3_{1,2}$      | 28.9             | $6.13\times 10^{-5}$  | 84               | $1.91 \pm 0.18$  | $239.4 \pm 2.7$   | $57.8 \pm 5.9$   | 8.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 306877    | $5_{1,6}-4_{0,7}$       | 36.6             | $1.24\times 10^{-4}$  | 44               | $1.12 \pm 0.33$  | $243.3 \pm 4.7$   | $40.5 \pm 19.6$  | 6.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 307791    | $5_{-1,3}-4_{0,2}$      | 36.3             | $1.44\times 10^{-4}$  | 132              | $4.08 \pm 0.42$  | $246.7 \pm 2.4$   | $49.3 \pm 6.2$   | 5.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 310528    | $5_{1,5}-4_{0,5}$       | 36.6             | $1.43\times 10^{-4}$  | 132              | $3.48 \pm 1.64$  | $243.6 \pm 8.2$   | $49.2 \pm 12.7$  | 6.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 354843    | $6_{1,2}-5_{0,3}$       | 49.2             | $2.16\times 10^{-4}$  | 156              | $2.26 \pm 0.33$  | $243.8 \pm 2.5$   | $38.5 \pm 7.4$   | 6.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 353388    | $6_{1,6}-5_{0,7}$       | 49.4             | $1.96\times 10^{-4}$  | 52               | $1.03 \pm 0.26$  | $240.1 \pm 4.7$   | $36.5 \pm 10.9$  | 7.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 365746    | $6_{1,0}-5_{0,1}$       | 49.5             | $2.36\times 10^{-4}$  | 52               | $1.17 \pm 0.29$  | $241.0 \pm 4.2$   | $37.5 \pm 11.2$  | 7.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 357440    | $6_{1,5}-5_{0,5}$       | 49.5             | $2.16\times 10^{-4}$  | 156              | $3.12 \pm 0.44$  | $244.1 \pm 2.6$   | $40.4 \pm 7.2$   | 6.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 220827    | $7_{0,3}-6_{1,2}$       | 59.8             | $3.59\times 10^{-5}$  | 180              | $0.47 \pm 0.18$  | $243.0 \pm 4.8$   | $25.4 \pm 11.7$  | 3.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233802    | $6_{2,5}-6_{1,5}$       | 60.7             | $3.42\times 10^{-5}$  | 156              | $0.81 \pm 0.32$  | $255.8 \pm 7.0$   | $48.5 \pm 15.6$  | 4.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 242262    | $6_{-2,3}-6_{1,2}$      | 60.9             | $6.39\times 10^{-5}$  | 156              | $0.74 \pm 0.18$  | $243.0 \pm 4.1$   | $32.0 \pm 8.2$   | 4.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 235735    | $8_{-2,3}-8_{1,2}$      | 92.8             | $6.13\times 10^{-5}$  | 204              | $0.95 \pm 0.10$  | $260.7 \pm 2.6$   | $40.0 \pm 10.0$  | 3.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 126247    | $6_{0,6}-5_{0,5}$       | 21.3             | $1.41\times 10^{-4}$  | 13               | $7.05 \pm 0.44$  | $232.1 \pm 1.3$   | $43.8 \pm 3.4$   | 10.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 131617    | $6_{1,5}-5_{1,4}$       | 25.1             | $1.56\times 10^{-4}$  | 13               | $6.96 \pm 0.25$  | $232.6 \pm 0.8$   | $44.7 \pm 1.9$   | 6.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 146871    | $7_{0,7}-6_{0,6}$       | 28.4             | $2.25\times 10^{-4}$  | 15               | $5.99 \pm 0.42$  | $225.3 \pm 1.3$   | $41.3 \pm 3.8$   | 7.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 142701    | $7_{1,7}-6_{1,6}$       | 30.4             | $2.02\times 10^{-4}$  | 15               | $6.22 \pm 0.42$  | $231.1 \pm 1.4$   | $45.4 \pm 3.9$   | 10.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 128102    | $6_{2,4}-5_{2,3}$       | 33.4             | $1.31\times 10^{-4}$  | 13               | $6.23 \pm 0.46$  | $228.0 \pm 1.6$   | $46.9 \pm 4.4$   | 6.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 167320    | $8_{0,8}-7_{0,7}$       | 36.4             | $3.35\times 10^{-4}$  | 17               | $3.16 \pm 0.30$  | $238.5 \pm 1.5$   | $31.9 \pm 3.5$   | 14.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 149792    | $7_{2,5}-6_{2,4}$       | 40.6             | $2.19\times 10^{-4}$  | 15               | $5.44 \pm 0.43$  | $238.5 \pm 1.8$   | $46.2 \pm 4.5$   | 11.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169299    | $8_{2,7}-7_{2,6}$       | 48.5             | $3.26\times 10^{-4}$  | 17               | $4.36 \pm 0.37$  | $235.8 \pm 2.0$   | $38.6 \pm 4.9$   | 13.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 171620    | $8_{2,6}-7_{2,5}$       | 48.8             | $3.39\times 10^{-4}$  | 17               | $3.21 \pm 0.38$  | $229.9 \pm 2.2$   | $38.2 \pm 5.3$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 196865    | $9_{1,8}-8_{1,7}$       | 50.4             | $5.43\times 10^{-4}$  | 19               | $3.36 \pm 0.52$  | $235.3 \pm 2.7$   | $36.6 \pm 7.2$   | 10.5   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 207679    | $10_{0,10}-9_{0,9}$     | 55.4             | $6.47\times 10^{-4}$  | 21               | $2.19 \pm 0.37$  | $236.8 \pm 4.1$   | $50.7 \pm 10.3$  | 9.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 148667    | $7_{3,5}-6_{3,4}$       | 55.4             | $1.91\times 10^{-4}$  | 15               | $3.00 \pm 0.37$  | $221.6 \pm 2.2$   | $38.7 \pm 6.0$   | 11.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 223452    | $11_{1,11}-10_{1,10}$   | 67.5             | $8.05\times 10^{-4}$  | 23               | $1.68 \pm 0.19$  | $246.7 \pm 2.2$   | $42.4 \pm 5.8$   | 6.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 215687    | $10_{2,8}-9_{2,7}$      | 68.5             | $6.98\times 10^{-4}$  | 21               | $2.69 \pm 0.26$  | $239.6 \pm 2.2$   | $48.7 \pm 5.9$   | 6.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 239951    | $11_{1,10}-10_{1,9}$    | 72.4             | $9.96\times 10^{-4}$  | 23               | $1.69 \pm 0.43$  | $228.2 \pm 5.2$   | $39.9 \pm 11.4$  | 6.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 148598    | $7_{4,4}-6_{4,3}$       | 76.2             | $1.57\times 10^{-4}$  | 15               | $2.84 \pm 0.32$  | $226.6 \pm 2.3$   | $40.0 \pm 10.0$  | 11.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 148599    | $7_{4,3}-6_{4,2}$       | 76.2             | $1.57\times 10^{-4}$  | 15               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 232273    | $11_{2,10}-10_{2,9}$    | 79.1             | $8.82\times 10^{-4}$  | 23               | $1.65 \pm 0.23$  | $234.3 \pm 3.2$   | $48.3 \pm 8.1$   | 4.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 237896    | $11_{2,9}-10_{2,8}$     | 79.9             | $9.48\times 10^{-4}$  | 23               | $1.61 \pm 0.23$  | $234.3 \pm 3.2$   | $48.3 \pm 8.1$   | 4.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 212572    | $10_{3,8}-9_{3,7}$      | 82.9             | $6.33\times 10^{-4}$  | 21               | $1.81 \pm 0.25$  | $236.5 \pm 2.7$   | $42.1 \pm 7.3$   | 6.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169861    | $8_{4,5}-7_{4,4}$       | 84.4             | $2.63\times 10^{-4}$  | 17               | $2.53 \pm 0.31$  | $235.8 \pm 2.0$   | $38.6 \pm 4.9$   | 13.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 169862    | $8_{4,4}-7_{4,3}$       | 84.4             | $2.63\times 10^{-4}$  | 17               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233896    | $11_{3,9}-10_{3,8}$     | 94.2             | $8.62\times 10^{-4}$  | 23               | $0.90 \pm 0.11$  | $243.4 \pm 3.3$   | $40.0 \pm 10.0$  | 4.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 234315    | $11_{3,8}-10_{3,7}$     | 94.2             | $8.67\times 10^{-4}$  | 23               | $1.11 \pm 0.13$  | $246.5 \pm 1.6$   | $47.8 \pm 6.5$   | 4.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 148566    | $7_{5,3}-6_{5,2}$       | 103.0            | $1.14\times 10^{-4}$  | 15               | $1.22 \pm 0.32$  | $233.6 \pm 3.9$   | $30.4 \pm 9.1$   | 11.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 148566    | $7_{5,2}-6_{5,1}$       | 103.0            | $1.14\times 10^{-4}$  | 15               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233745    | $11_{4,7}-10_{4,6}$     | 115.1            | $8.07\times 10^{-4}$  | 23               | $1.71 \pm 0.20$  | $233.1 \pm 2.3$   | $45.4 \pm 5.2$   | 3.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 233734    | $11_{4,8}-10_{4,7}$     | 115.1            | $8.07\times 10^{-4}$  | 23               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 95963     | $5_{0,5}-4_{0,4}$ A     | 13.8             | $2.84\times 10^{-5}$  | 22               | $5.06 \pm 0.23$  | $245.6 \pm 0.5$   | $47.2 \pm 2.7$   | 8.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 95947     | $5_{0,5}-4_{0,4}$ E     | 13.9             | $2.84\times 10^{-5}$  | 22               | $4.82 \pm 0.11$  | $248.9 \pm 4.1$   | $45.6 \pm 1.3$   | 8.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98900     | $5_{1,4}-4_{1,3}$ A     | 16.5             | $2.99 \times 10^{-5}$ | 22               | $3.60 \pm 1.05$  | $212.0 \pm 2.4$   | $50.6 \pm 9.9$   | 8.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98863     | $5_{1,4}-4_{1,3}$ E     | 16.6             | $2.99 \times 10^{-5}$ | 22               | $3.2 \pm 0.38$   | $213.6 \pm 2.0$   | $47.0 \pm 5.9$   | 8.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 114959    | $6_{0,6}-5_{0,5}$ A     | 19.4             | $4.96 \times 10^{-5}$ | 26               | $3.10 \pm 0.42$  | $221.5 \pm 4.2$   | $50.0 \pm 10.0$  | 13.4   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 114940    | $6_{0,6}-5_{0,5}$ E     | 19.4             | $4.96 \times 10^{-5}$ | 26               | $3.31 \pm 0.42$  | $214.8 \pm 3.7$   | $50.0 \pm 10.0$  | 13.4   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 112248    | $6_{1,6}-5_{1,5}$ A     | 21.1             | $4.50 \times 10^{-5}$ | 26               | $6.33 \pm 0.39$  | $226.6 \pm 1.9$   | $65.3 \pm 4.8$   | 10.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 112254    | $6_{1,6}-5_{1,5}$ E     | 21.2             | $4.50 \times 10^{-5}$ | 26               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96274     | $5_{2,4}-4_{2,3}$ A     | 22.9             | $2.41 \times 10^{-5}$ | 22               | $2.31 \pm 0.23$  | $235.7 \pm 3.9$   | $60.0 \pm 10.0$  | 8.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96632     | $5_{2,3}-4_{2,2}$ A     | 22.9             | $2.44 \times 10^{-5}$ | 22               | $2.63 \pm 0.37$  | $229.6 \pm 3.8$   | $56.1 \pm 9.5$   | 8.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96475     | $5_{2,3}-4_{2,2}$ E     | 23.0             | $2.42 \times 10^{-5}$ | 22               | $2.97 \pm 0.32$  | $229.0 \pm 2.1$   | $44.8 \pm 5.9$   | 8.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133854    | $7_{0,7}-6_{0,6}$A      | 25.8             | $7.92 \times 10^{-5}$ | 30               | $3.47 \pm 0.61$  | $228.2 \pm 2.9$   | $55.4 \pm 11.8$  | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133830    | $7_{0,7}-6_{0,6}$E      | 25.8             | $7.92 \times 10^{-5}$ | 30               | $2.63 \pm 0.55$  | $235.0 \pm 3.6$   | $40.2 \pm 7.7$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 292298    | $3_{3,1}-2_{2,1}$ E     | 25.8             | $1.13 \times 10^{-4}$ | 14               | $0.80 \pm 0.19$  | $241.2 \pm 3.4$   | $29.0 \pm 8.6$   | 4.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 293564    | $3_{3,0}-2_{2,1}$ A     | 25.9             | $1.15 \times 10^{-4}$ | 14               | $1.76 \pm 0.10$  | $226.0 \pm 10.0$  | $53.7 \pm 3.3$   | 13.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 293546    | $3_{3,1}-2_{2,0}$ A     | 25.9             | $1.15 \times 10^{-4}$ | 14               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 138319    | $7_{1,6}-6_{1,5}$ A     | 28.8             | $8.75\times 10^{-5}$  | 30               | $2.95 \pm 0.39$  | $240.1 \pm 3.3$   | $45.6 \pm 9.0$   | 13.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 138284    | $7_{1,6}-6_{1,5}$ E     | 28.9             | $8.75\times 10^{-5}$  | 30               | $3.00 \pm 0.45$  | $241.9 \pm 4.3$   | $57.4 \pm 10.4$  | 13.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 152635    | $8_{0,8}-7_{0,7}$ A     | 33.1             | $1.18 \times 10^{-4}$ | 34               | $2.43 \pm 0.64$  | $233.0 \pm 4.4$   | $40.1 \pm 13.1$  | 11.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 152607    | $8_{0,8}-7_{0,7}$ E     | 33.2             | $1.18 \times 10^{-4}$ | 34               | $2.35 \pm 0.54$  | $228.7 \pm 3.0$   | $30.9 \pm 8.9$   | 11.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 149507    | $8_{1,8}-7_{1,7}$ A     | 34.6             | $1.10 \times 10^{-4}$ | 34               | $4.65 \pm 0.41$  | $226.5 \pm 2.9$   | $66.7 \pm 7.0$   | 11.4   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 149505    | $8_{1,8}-7_{1,7}$ E     | 34.7             | $1.10 \times 10^{-4}$ | 34               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 135476    | $7_{2,5}-6_{2,4}$ E     | 35.1             | $7.40 \times 10^{-5}$ | 30               | $0.95 \pm 0.31$  | $239.3 \pm 5.6$   | $36.6 \pm 14.1$  | 5.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 155342    | $8_{2,6}-7_{2,5}$ A     | 42.5             | $1.17 \times 10^{-4}$ | 34               | $1.78 \pm 0.95$  | $229.5 \pm 8.4$   | $30.9 \pm 18.2$  | 14.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 168093    | $9_{1,9}-8_{1,8}$ A     | 42.7             | $1.57 \times 10^{-4}$ | 38               | $2.30 \pm 0.37$  | $222.1 \pm 5.4$   | $63.4 \pm 10.3$  | 10.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 168088    | $9_{1,9}-8_{1,8}$ E     | 42.7             | $1.57 \times 10^{-4}$ | 38               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 205170    | $11_{1,11}-10_{1,10}$ A | 61.5             | $2.90 \times 10^{-4}$ | 46               | $1.98 \pm 0.38$  | $228.6 \pm 5.5$   | $53.2 \pm 10.7$  | 11.5   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 205161    | $11_{1,11}-10_{1,10}$ E | 61.5             | $2.90 \times 10^{-4}$ | 46               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 223660    | $12_{1,12}-11_{1,11}$ A | 72.2             | $3.78 \times 10^{-4}$ | 50               | $1.18 \pm 0.24$  | $212.1 \pm 8.5$   | $50.1 \pm 15.7$  | 6.5    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 223650    | $12_{1,12}-11_{1,11}$ E | 72.3             | $3.78 \times 10^{-4}$ | 50               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 230301    | $12_{2,11}-11_{2,10}$ A | 81.0             | $4.04 \times 10^{-4}$ | 39               | $1.56 \pm 0.19$  | $213.4 \pm 3.3$   | $51.8 \pm 7.0$   | 7.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 230315    | $12_{2,11}-11_{2,10}$ E | 81.1             | $4.04 \times 10^{-4}$ | 39               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 242118    | $13_{1,13}-12_{1,12}$ A | 83.8             | $4.81 \times 10^{-4}$ | 54               | $1.09 \pm 0.22$  | $227.2 \pm 5.7$   | $49.8 \pm 11.3$  | 4.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 242106    | $13_{1,13}-12_{1,12}$ E | 83.9             | $4.81 \times 10^{-4}$ | 54               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 144734    | $4_{2,3}-3_{1,2}$       | 13.4             | $1.58\times 10^{-5}$  | 9                | $0.85 \pm 0.16$  | $237.0 \pm 3.1$   | $35.2 \pm 6.3$   | 6.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 234758    | $6_{3,4}-5_{2,3}$       | 28.9             | $7.09 \times 10^{-5}$ | 13               | $0.74 \pm 0.18$  | $240.6 \pm 5.2$   | $44.5 \pm 13.2$  | 4.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 270444    | $5_{4,2}-4_{3,1}$       | 32.7             | $1.59 \times 10^{-4}$ | 11               | $2.26 \pm 0.46$  | $237.5 \pm 4.0$   | $49.8 \pm 13.2$  | 9.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 270450    | $5_{4,1}-4_{3,2}$       | 32.7             | $1.59 \times 10^{-4}$ | 11               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 287918    | $6_{4,3}-5_{3,2}$       | 37.7             | $1.68 \times 10^{-4}$ | 13               | $1.52 \pm 0.38$  | $229.1 \pm 5.2$   | $43.1 \pm 12.3$  | 7.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 287944    | $6_{4,2}-5_{3,3}$       | 37.7             | $1.68 \times 10^{-4}$ | 13               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 214267    | $9_{2,8}-8_{1,7}$       | 42.7             | $4.49 \times 10^{-5}$ | 19               | $1.02 \pm 0.18$  | $231.5 \pm 3.4$   | $39.1 \pm 8.4$   | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 213856    | $13_{0,13}-12_{1,12}$   | 74.3             | $9.26 \times 10^{-5}$ | 27               | $1.59 \pm 0.14$  | $241.0 \pm 2.5$   | $40.0 \pm 10.0$  | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
| pSSC 2                                                                                                                                                                         |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 225554    | $1_{1,1}-0_{0,0}$       | 10.8             | $9.63\times 10^{-5}$  | 9                | $1.77 \pm 0.22$  | $280.4 \pm 3.0$   | $49.7 \pm 7.6$   | 4.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 172267    | $2_{1,1}-2_{0,2}$       | 17.5             | $6.12\times 10^{-5}$  | 15               | $4.17 \pm 0.30$  | $279.2\pm 1.4$    | $38.0 \pm 2.9$   | 11.8   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 199823    | $3_{1,2}-2_{1,1}$       | 27.1             | $6.35\times 10^{-5}$  | 21               | $17.7 \pm 0.70$  | $275.1 \pm 1.1$   | $53.0 \pm 2.6$   | 23.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 245125    | $4_{1,4}-3_{1,3}$       | 37.3             | $1.28\times 10^{-4}$  | 27               | $9.42 \pm 0.25$  | $283.4 \pm0.7$    | $49.8 \pm 1.4$   | 7.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 266270    | $4_{1,3}-3_{1,2}$       | 39.8             | $1.64\times 10^{-4}$  | 27               | $12.01 \pm 0.25$ | $282.7 \pm 0.6$   | $55.7 \pm 1.3$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 192212    | $4_{1,3}-4_{0,4}$       | 39.8             | $8.01\times 10^{-5}$  | 27               | $8.08 \pm 0.52$  | $279.2 \pm 1.5$   | $48.8 \pm 3.6$   | 11.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 317405    | $5_{0,5}-4_{0,4}$       | 45.9             | $3.03\times 10^{-4}$  | 33               | $9.02 \pm 0.74$  | $286.4 \pm 2.2$   | $55.3 \pm 5.6$   | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 178073    | $5_{0,5}-4_{1,4}$       | 45.9             | $2.92\times 10^{-5}$  | 33               | $5.14 \pm 1.44$  | $280.9 \pm 6.1$   | $46.9 \pm 16.8$  | 32.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 192469    | $3_{2,1}-2_{2,0}$       | 49.9             | $3.55\times 10^{-5}$  | 21               | $1.39 \pm 0.55$  | $280.0 \pm 10.0$  | $35.3 \pm 9.7$   | 11.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 207380    | $5_{1,4}-5_{0,5}$       | 55.8             | $9.63\times 10^{-5}$  | 33               | $4.44 \pm 0.54$  | $284.0 \pm 2.6$   | $41.8 \pm 5.0$   | 11.2   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 332572    | $5_{1,4}-4_{1,3}$       | 55.8             | $3.35\times 10^{-4}$  | 33               | $6.77 \pm 0.26$  | $286.2 \pm 1.1$   | $59.4 \pm 2.6$   | 8.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 251421    | $6_{0,6}-5_{1,5}$       | 64.1             | $9.08\times 10^{-5}$  | 39               | $3.66 \pm 0.34$  | $288.5 \pm 2.5$   | $54.3 \pm 7.4$   | 8.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 367072    | $6_{1,6}-5_{1,5}$       | 69.6             | $4.63\times 10^{-4}$  | 39               | $2.54 \pm 0.36$  | $299.7 \pm 3.5$   | $50.5 \pm 8.3$   | 11.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 278642    | $8_{1,7}-8_{0,8}$       | 122.7            | $1.92\times 10^{-4}$  | 51               | $0.91 \pm 0.30$  | $304.6 \pm 4.7$   | $29.9 \pm 12.9$  | 5.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 84305     | $1_{1,5}-1_{0,5}$       | 6.6              | $2.28\times 10^{-6}$  | 36               | $2.24 \pm 0.41$  | $272.7 \pm 4.8$   | $53.3 \pm 11.2$  | 9.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169447    | $2_{1,2}-1_{0,3}$       | 10.6             | $2.69\times 10^{-5}$  | 60               | $6.30 \pm 0.49$  | $273.2 \pm 2.0$   | $50.0 \pm 10.0$  | 10.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 215108    | $3_{-1,3}-2_{0,2}$      | 17.0             | $5.22\times 10^{-5}$  | 84               | $5.98 \pm 0.27$  | $280.9 \pm 1.1$   | $51.7 \pm 2.7$   | 4.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 237143    | $2_{2,4}-2_{1,4}$       | 22.0             | $3.82\times 10^{-5}$  | 156              | $1.64 \pm 0.21$  | $282.3 \pm 3.5$   | $52.5 \pm 6.8$   | 4.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 334712    | $2_{-2,1}-1_{1,0}$      | 22.5             | $2.07\times 10^{-4}$  | 20               | $0.70 \pm 0.15$  | $289.6 \pm 2.8$   | $26.2 \pm 5.8$   | 6.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 339723    | $2_{2,2}-1_{-1,3}$      | 22.6             | $2.18\times 10^{-4}$  | 60               | $2.91 \pm 0.18$  | $289.8 \pm 1.1$   | $50.3 \pm 4.2$   | 9.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 264172    | $4_{1,5}-3_{0,5}$       | 25.9             | $8.74\times 10^{-5}$  | 108              | $2.98 \pm 0.20$  | $287.3 \pm 1.2$   | $34.7 \pm 2.4$   | 8.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 239446    | $3_{2,5}-3_{1,5}$       | 28.8             | $4.42\times 10^{-5}$  | 84               | $2.44 \pm 0.16$  | $271.6 \pm 5.0$   | $68.2 \pm 13.7$  | 5.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 239427    | $4_{2,4}-4_{1,4}$       | 36.9             | $4.08\times 10^{-5}$  | 108              |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 307791    | $5_{-1,3}-4_{0,2}$      | 36.3             | $1.44\times 10^{-4}$  | 132              | $3.25 \pm 0.39$  | $283.7\pm 2.3$    | $46.1 \pm 7.0$   | 7.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 310528    | $5_{1,5}-4_{0,5}$       | 36.6             | $1.43\times 10^{-4}$  | 132              | $2.89 \pm 0.31$  | $284.9 \pm 2.8$   | $57.3 \pm 7.6$   | 7.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 354843    | $6_{1,2}-5_{0,3}$       | 49.2             | $2.16\times 10^{-4}$  | 156              | $2.85 \pm 0.34$  | $279.8 \pm 4.1$   | $68.2 \pm 8.8$   | 4.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 353388    | $6_{1,6}-5_{0,7}$       | 49.4             | $1.96\times 10^{-4}$  | 52               | $1.21 \pm 0.29$  | $281.8 \pm 5.3$   | $43.3 \pm 10.5$  | 6.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 357440    | $6_{1,5}-5_{0,5}$       | 49.5             | $2.16\times 10^{-4}$  | 156              | $1.68 \pm 0.52$  | $286.3 \pm 6.3$   | $44.5 \pm 17.8$  | 6.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 309921    | $7_{0,3}-6_{0,2}$       | 59.8             | $1.52\times 10^{-5}$  | 180              | $0.86\pm 0.14$   | $282.8 \pm 3.0$   | $37.4 \pm 6.9$   | 7.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 309914    | $7_{0,5}-6_{0,5}$       | 60.0             | $1.52\times 10^{-5}$  | 180              |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 220827    | $7_{0,3}-6_{1,2}$       | 59.8             | $3.59\times 10^{-5}$  | 180              | $1.23 \pm 0.28$  | $275.7 \pm 6.3$   | $55.5 \pm 14.3$  | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 126247    | $6_{0,6}-5_{0,5}$       | 21.3             | $1.41\times 10^{-4}$  | 13               | $7.17 \pm 0.38$  | $270.1 \pm 1.6$   | $64.0 \pm 4.2$   | 8.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 131617    | $6_{1,5}-5_{1,4}$       | 25.1             | $1.56\times 10^{-4}$  | 13               | $7.05 \pm 0.30$  | $270.5 \pm 1.1$   | $49.2 \pm 2.3$   | 8.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 142701    | $7_{1,7}-6_{1,6}$       | 30.4             | $2.02\times 10^{-4}$  | 15               | $3.50 \pm 0.89$  | $280.2 \pm 4.8$   | $41.3 \pm 8.5$   | 13.3   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 128102    | $6_{2,4}-5_{2,3}$       | 33.4             | $1.31\times 10^{-4}$  | 13               | $5.15 \pm 0.30$  | $273.3 \pm 1.7$   | $59.9 \pm 3.9$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 167320    | $8_{0,8}-7_{0,7}$       | 36.4             | $3.35\times 10^{-4}$  | 17               | $2.00 \pm 0.39$  | $280.2 \pm 4.2$   | $43.0 \pm 9.8$   | 11.9   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169299    | $8_{2,7}-7_{2,6}$       | 48.5             | $3.26\times 10^{-4}$  | 17               | $2.42 \pm 0.36$  | $294.5 \pm 3.1$   | $40.6 \pm 7.1$   | 10.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 171620    | $8_{2,6}-7_{2,5}$       | 48.8             | $3.39\times 10^{-4}$  | 17               | $1.01 \pm 0.21$  | $293.2 \pm 1.7$   | $14.7 \pm 3.9$   | 9.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 196865    | $9_{1,8}-8_{1,7}$       | 50.4             | $5.43\times 10^{-4}$  | 19               | $1.18 \pm 0.33$  | $294.5 \pm 4.0$   | $29.5 \pm 8.5$   | 8.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 207679    | $10_{0,10}-9_{0,9}$     | 55.4             | $6.47\times 10^{-4}$  | 21               | $0.90 \pm 0.15$  | $292.8 \pm 6.7$   | $15.1 \pm 10.3$  | 10.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 148667    | $7_{3,5}-6_{3,4}$       | 55.4             | $1.91\times 10^{-4}$  | 15               | $1.25 \pm 0.49$  | $275.1 \pm 6.6$   | $32.0 \pm 15.9$  | 10.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 169955    | $8_{3,6}-7_{3,5}$       | 63.5             | $3.02\times 10^{-4}$  | 17               | $1.17 \pm 0.34$  | $290.8 \pm 2.9$   | $20.4 \pm 7.0$   | 10.6   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 223452    | $11_{1,11}-10_{1,10}$   | 67.5             | $8.05\times 10^{-4}$  | 23               | $1.58 \pm 0.17$  | $300.7 \pm 2.0$   | $37.5 \pm 4.7$   | 6.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 215687    | $10_{2,8}-9_{2,7}$      | 68.5             | $6.98\times 10^{-4}$  | 21               | $1.14 \pm 0.21$  | $296.6 \pm 2.3$   | $26.6 \pm 6.5$   | 4.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 239951    | $11_{1,10}-10_{1,9}$    | 72.4             | $9.96\times 10^{-4}$  | 23               | $0.95 \pm 0.20$  | $295.8 \pm 2.5$   | $26.1 \pm 7.2$   | 5.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 232273    | $11_{2,10}-10_{2,9}$    | 79.1             | $8.82\times 10^{-4}$  | 23               | $1.42 \pm 0.16$  | $297.8 \pm 1.7$   | $31.9 \pm 4.2$   | 4.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 243521    | $12_{1,12}-11_{1,11}$   | 79.2             | $1.05\times 10^{-3}$  | 25               | $1.18 \pm 0.18$  | $307.5 \pm 2.3$   | $23.0 \pm 10.0$  | 7.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 237896    | $11_{2,9}-10_{2,8}$     | 79.9             | $9.48\times 10^{-4}$  | 23               | $0.71 \pm 0.16$  | $306.1 \pm 1.5$   | $13.4 \pm 7.9$   | 7.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 212572    | $10_{3,8}-9_{3,7}$      | 82.9             | $6.33\times 10^{-4}$  | 21               | $0.85 \pm 0.20$  | $297.1 \pm 3.0$   | $26.1 \pm 7.4$   | 8.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233896    | $11_{3,9}-10_{3,8}$     | 94.2             | $8.62\times 10^{-4}$  | 23               | $0.44 \pm 0.10$  | $298.0 \pm 1.3$   | $15.6 \pm 5.4$   | 4.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 282569    | $13_{1,12}-12_{1,11}$   | 98.4             | $1.64 \times 10^{-3}$ | 27               | $0.80 \pm 0.17$  | $302.8 \pm 0.7$   | $22.1 \pm 2.0$   | 5.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 282529    | $13_{2,11}-12_{2,10}$   | 105.9            | $1.61 \times 10^{-3}$ | 27               | $0.91 \pm 0.17$  | $303.0 \pm 2.1$   | $21.4 \pm 4.6$   | 5.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 212428    | $10_{4,7}-9_{4,6}$      | 103.7            | $5.84 \times 10^{-4}$ | 21               | $1.15 \pm 0.21$  | $298.6 \pm 2.8$   | $30.1 \pm 7.3$   | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 212433    | $10_{4,6}-9_{4,5}$      | 103.7            | $5.84 \times 10^{-4}$ | 21               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 233745    | $11_{4,7}-10_{4,6}$     | 115.1            | $8.07\times 10^{-4}$  | 23               | $1.14 \pm 0.10$  | $303.4 \pm 1.3$   | $28.8 \pm 2.6$   | 4.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 233734    | $11_{4,8}-10_{4,7}$     | 115.1            | $8.07\times 10^{-4}$  | 23               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 276555    | $13_{3,11}-12_{3,10}$   | 119.7            | $1.47\times 10^{-3}$  | 27               | $0.80 \pm 0.17$  | $302.0 \pm 3.3$   | $30.7 \pm 6.6$   | 6.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 255079    | $12_{4,8}-11_{4,7}$     | 127.2            | $1.08 \times 10^{-3}$ | 25               | $1.56 \pm 0.38$  | $288.5 \pm 4.0$   | $33.4 \pm 9.6$   | 6.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 255059    | $12_{4,9}-11_{4,8}$     | 127.2            | $1.08 \times 10^{-3}$ | 25               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 212323    | $10_{5,6}-9_{5,5}$      | 130.5            | $5.20 \times 10^{-4}$ | 21               | $1.09 \pm 0.18$  | $303.0 \pm 10.0$  | $30.0 \pm 10.0$  | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 212323    | $10_{5,6}-9_{5,5}$      | 130.5            | $5.20 \times 10^{-4}$ | 21               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 315489    | $15_{2,14}-14_{2,13}$   | 133.6            | $2.27\times 10^{-3}$  | 31               | $1.13 \pm 0.15$  | $302.7 \pm 2.0$   | $31.9 \pm 5.0$   | 5.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 276400    | $13_{4,10}-12_{4,9}$    | 140.4            | $1.40 \times 10^{-3}$ | 27               | $0.61 \pm 0.19$  | $302.6 \pm 3.0$   | $18.5 \pm 6.2$   | 6.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 276436    | $13_{4,9}-12_{4,8}$     | 140.4            | $1.40 \times 10^{-3}$ | 27               | $0.77 \pm 0.12$  | $303.9 \pm 2.3$   | $29.1 \pm 5.5$   | 6.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 336135    | $16_{2,15}-15_{2,14}$   | 149.7            | $2.76\times 10^{-3}$  | 33               | $0.67 \pm 0.18$  | $297.0 \pm 4.2$   | $29.7 \pm 8.5$   | 8.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 297478    | $14_{5,9}-13_{5,8}$     | 181.6            | $1.69\times 10^{-3}$  | 29               | $0.48 \pm 0.13$  | $305.6 \pm 2.9$   | $20.6 \pm 5.4$   | 7.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 297477    | $14_{5,10}-13_{5,9}$    | 181.6            | $1.69\times 10^{-3}$  | 29               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 362185    | $17_{4,13}-16_{4,12}$   | 203.8            | $3.32 \times 10^{-3}$ | 35               | $0.53 \pm 0.16$  | $298.9 \pm 2.0$   | $13.9 \pm 5.2$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 361947    | $17_{4,14}-16_{4,13}$   | 203.8            | $3.31 \times 10^{-3}$ | 35               | $0.51 \pm 0.19$  | $300.0 \pm 4.3$   | $20.8 \pm 9.1$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 361484    | $17_{5,13}-16_{5,12}$   | 320.7            | $3.19\times 10^{-3}$  | 35               | $0.51 \pm 0.12$  | $303.7 \pm 1.8$   | $17.4 \pm 4.5$   | 7.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 361492    | $17_{5,12}-16_{5,11}$   | 230.7            | $3.19\times 10^{-3}$  | 35               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 95963     | $5_{0,5}-4_{0,4}$ A     | 13.8             | $2.84\times 10^{-5}$  | 22               | $6.00 \pm 0.30$  | $226.5 \pm 1.3$   | $54.8 \pm 4.1$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 95947     | $5_{0,5}-4_{0,4}$ E     | 13.9             | $2.84\times 10^{-5}$  | 22               | $5.87 \pm 0.11$  | $232.7 \pm 2.0$   | $59.4 \pm 4.2$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98900     | $5_{1,4}-4_{1,3}$ A     | 16.5             | $2.99 \times 10^{-5}$ | 22               | $5.84 \pm 0.39$  | $245.7 \pm 1.7$   | $52.7 \pm 4.0$   | 9.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 98863     | $5_{1,4}-4_{1,3}$ E     | 16.6             | $2.99 \times 10^{-5}$ | 22               | $5.94 \pm 0.40$  | $246.7 \pm 1.7$   | $50.2 \pm 3.7$   | 9.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 114959    | $6_{0,6}-5_{0,5}$ A     | 19.4             | $4.96 \times 10^{-5}$ | 26               | $3.57 \pm 0.94$  | $264.5 \pm 4.7$   | $43.9 \pm 10.7$  | 12.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 114940    | $6_{0,6}-5_{0,5}$ E     | 19.4             | $4.96 \times 10^{-5}$ | 26               | $3.24 \pm 0.88$  | $260.9 \pm 2.5$   | $43.3 \pm 8.8$   | 12.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 112248    | $6_{1,6}-5_{1,5}$ A     | 21.1             | $4.50 \times 10^{-5}$ | 26               | $6.41 \pm 0.33$  | $261.8 \pm 1.3$   | $51.6 \pm 2.9$   | 9.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 112254    | $6_{1,6}-5_{1,5}$ E     | 21.2             | $4.50 \times 10^{-5}$ | 26               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96274     | $5_{2,4}-4_{2,3}$ A     | 22.9             | $2.41 \times 10^{-5}$ | 22               | $2.06 \pm 0.25$  | $273.9 \pm 2.5$   | $41.7 \pm 6.0$   | 7.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96632     | $5_{2,3}-4_{2,2}$ A     | 22.9             | $2.44 \times 10^{-5}$ | 22               | $2.00 \pm 0.23$  | $262.8 \pm 2.9$   | $47.1 \pm 6.4$   | 7.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 96475     | $5_{2,3}-4_{2,2}$ E     | 23.0             | $2.42 \times 10^{-5}$ | 22               | $3.33 \pm 0.34$  | $261.8 \pm 2.8$   | $55.3 \pm 6.5$   | 7.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133854    | $7_{0,7}-6_{0,6}$A      | 25.8             | $7.92 \times 10^{-5}$ | 30               | $3.36 \pm 0.54$  | $272.9 \pm 4.4$   | $52.6 \pm 8.9$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133830    | $7_{0,7}-6_{0,6}$E      | 25.8             | $7.92 \times 10^{-5}$ | 30               | $3.06 \pm 0.53$  | $277.4 \pm 3.1$   | $42.4 \pm 6.9$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 293564    | $3_{3,0}-2_{2,1}$ A     | 25.9             | $1.15 \times 10^{-4}$ | 14               | $1.45 \pm 0.21$  | $275.3 \pm 4.7$   | $45.0 \pm 10.0$  | 4.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 293546    | $3_{3,1}-2_{2,0}$ A     | 25.9             | $1.15 \times 10^{-4}$ | 14               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 138284    | $7_{1,6}-6_{1,5}$ E     | 28.9             | $8.75\times 10^{-5}$  | 30               | $2.73 \pm 0.65$  | $282.8 \pm 5.0$   | $49.6 \pm 12.6$  | 11.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 149507    | $8_{1,8}-7_{1,7}$ A     | 34.6             | $1.10 \times 10^{-4}$ | 34               | $4.54 \pm 0.84$  | $278.1 \pm 5.7$   | $62.3 \pm 13.3$  | 11.1   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 149505    | $8_{1,8}-7_{1,7}$ E     | 34.7             | $1.10 \times 10^{-4}$ | 34               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 134895    | $7_{2,6}-6_{2,5}$ E     | 34.9             | $7.31 \times 10^{-5}$ | 30               | $2.31 \pm 0.27$  | $276.8 \pm 2.9$   | $52.8 \pm 6.5$   | 6.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 135476    | $7_{2,5}-6_{2,4}$ E     | 35.1             | $7.40 \times 10^{-5}$ | 30               | $1.37 \pm 0.27$  | $270.8 \pm 5.4$   | $52.3 \pm 11.5$  | 6.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 157974    | $8_{2,7}-7_{1,6}$ A     | 36.4             | $1.29 \times 10^{-4}$ | 38               | $1.93 \pm 0.35$  | $264.6 \pm 3.8$   | $40.7 \pm 8.1$   | 13.4   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 157937    | $8_{2,7}-7_{1,6}$ E     | 36.5             | $1.29 \times 10^{-4}$ | 38               | $1.74 \pm 0.31$  | $262.6 \pm 3.9$   | $43.1 \pm 8.1$   | 13.4   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 168093    | $9_{1,9}-8_{1,8}$ A     | 42.7             | $1.57 \times 10^{-4}$ | 38               | $3.74 \pm 0.37$  | $271.9 \pm 2.9$   | $63.0 \pm 6.1$   | 11.7   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 168088    | $9_{1,9}-8_{1,8}$ E     | 42.7             | $1.57 \times 10^{-4}$ | 38               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 223660    | $12_{1,12}-11_{1,11}$ A | 72.2             | $3.78 \times 10^{-4}$ | 50               | $0.94 \pm 0.20$  | $286.0 \pm 5.0$   | $46.5 \pm 10.8$  | 6.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 223650    | $12_{1,12}-11_{1,11}$ E | 72.3             | $3.78 \times 10^{-4}$ | 50               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 144734    | $4_{2,3}-3_{1,2}$       | 13.4             | $1.58\times 10^{-5}$  | 9                | $2.39 \pm 0.41$  | $262.0 \pm 4.3$   | $57.9 \pm 13.8$  | 6.9    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 159781    | $5_{2,4}-4_{1,3}$       | 17.6             | $1.97 \times 10^{-5}$ | 11               | $2.56 \pm 0.50$  | $267.8 \pm 4.6$   | $53.6 \pm 14.9$  | 10.0   |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 133323    | $7_{1,7}-6_{0,6}$       | 23.9             | $1.83 \times 10^{-5}$ | 15               | $3.34 \pm 0.24$  | $272.3 \pm 2.6$   | $48.4 \pm 4.1$   | 7.7    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 131103    | $5_{3,3}-5_{2,4}$       | 23.9             | $1.17 \times 10^{-5}$ | 11               | $1.09 \pm 0.20$  | $275.0 \pm 3.5$   | $36.7 \pm 8.5$   | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 218654    | $7_{2,5}-6_{1,6}$       | 28.7             | $2.69 \times 10^{-5}$ | 15               | $1.25 \pm 0.66$  | $267.5 \pm 7.7$   | $29.5 \pm 17.9$  | 8.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 131502    | $6_{3,4}-6_{2,5}$       | 28.9             | $1.27 \times 10^{-5}$ | 13               | $1.46 \pm 0.30$  | $268.8 \pm 4.6$   | $40.7 \pm 9.0$   | 8.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 236299    | $6_{3,3}-5_{2,4}$       | 28.9             | $7.17 \times 10^{-5}$ | 13               | $2.76 \pm 0.45$  | $284.8 \pm 4.5$   | $58.1 \pm 11.5$  | 3.2    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 147427    | $8_{1,8}-7_{0,7}$       | 30.2             | $2.57 \times 10^{-5}$ | 17               | $3.53 \pm 0.27$  | $272.0 \pm 1.7$   | $49.3 \pm 4.8$   | 5.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 270444    | $5_{4,2}-4_{3,1}$       | 32.7             | $1.59 \times 10^{-4}$ | 11               | $3.60 \pm 0.19$  | $275.8 \pm 1.0$   | $40.5 \pm 2.2$   | 9.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 270450    | $5_{4,1}-4_{3,2}$       | 32.7             | $1.59 \times 10^{-4}$ | 11               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 127215    | $7_{3,4}-7_{2,5}$       | 34.8             | $1.24 \times 10^{-5}$ | 15               | $1.86 \pm 0.35$  | $274.4 \pm 5.7$   | $59.5 \pm 11.6$  | 8.3    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 132129    | $7_{3,5}-7_{2,6}$       | 34.8             | $1.35 \times 10^{-5}$ | 15               | $1.29 \pm 0.26$  | $267.0 \pm 4.6$   | $48.0 \pm 12.6$  | 8.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 254384    | $7_{3,4}-6_{2,5}$       | 34.8             | $8.11 \times 10^{-5}$ | 15               | $1.83 \pm 0.31$  | $280.2 \pm 3.4$   | $45.0 \pm 9.7$   | 8.4    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 142285    | $9_{0,9}-8_{1,8}$       | 37.2             | $2.30 \times 10^{-5}$ | 19               | $1.98 \pm 0.28$  | $276.3 \pm 2.8$   | $43.5 \pm 7.7$   | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 287917    | $6_{4,3}-5_{3,2}$       | 37.7             | $1.68 \times 10^{-4}$ | 13               | $3.61 \pm 0.20$  | $263.0 \pm 2.2$   | $69.2 \pm 5.3$   | 6.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+                  |                   |                  |        |
|         | 287944    | $6_{4,2}-5_{3,3}$       | 37.7             | $1.68 \times 10^{-4}$ | 13               |                  |                   |                  |        |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 267294    | $8_{3,6}-7_{2,5}$       | 41.6             | $8.87 \times 10^{-5}$ | 17               | $1.37 \pm 0.23$  | $270.3 \pm 2.7$   | $32.6 \pm 6.2$   | 6.0    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 214267    | $9_{2,8}-8_{1,7}$       | 42.7             | $4.49 \times 10^{-5}$ | 19               | $2.11 \pm 0.19$  | $268.1 \pm 2.8$   | $63.6 \pm 6.4$   | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 160699    | $10_{0,10}-9_{1,9}$     | 45.3             | $3.51 \times 10^{-5}$ | 21               | $1.73 \pm 0.32$  | $276.1 \pm 3.4$   | $38.8 \pm 8.9$   | 9.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 297167    | $10_{3,8}-9_{2,7}$      | 57.6             | $1.09 \times 10^{-4}$ | 21               | $1.73 \pm 0.38$  | $266.8 \pm 4.3$   | $44.7 \pm 12.2$  | 7.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 238701    | $11_{2,10}-10_{1,9}$    | 60.2             | $6.55\times 10^{-5}$  | 23               | $1.28 \pm 0.23$  | $279.5 \pm 4.7$   | $48.9 \pm 13.8$  | 6.1    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 213856    | $13_{0,13}-12_{1,12}$   | 74.3             | $9.26 \times 10^{-5}$ | 27               | $1.21 \pm 0.19$  | $270.2 \pm 5.2$   | $45.0 \pm 10.0$  | 5.6    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+
|         | 281279    | $17_{0,17}-16_{1,16}$   | 123.9            | $2.28\times 10^{-4}$  | 35               | $0.91 \pm 0.18$  | $293.2 \pm 6.2$   | $40.0 \pm 10.0$  | 6.8    |
+---------+-----------+-------------------------+------------------+-----------------------+------------------+------------------+-------------------+------------------+--------+

: continued.

![](spectra_GMC6_ch3cho_starred.pdf)

![](spectra_GMC6_ch3nh2_starred.pdf)

![](spectra_GMC6_GMC7_ch2nh_starred.pdf)

![](spectra_GMC6_nh2cho_starred.pdf)

![](spectra_GMC6_c2h5oh_starred.pdf)

![](spectra_GMC7_c2h5oh.pdf)

![](spectra_GMC7_ch3cho.pdf)

![](spectra_GMC7_ch3nh2.pdf)

![](spectra_GMC7_nh2cho.pdf)

![](spectra_SSC2_ch3cho.pdf)

![](spectra_SSC2_ch3nh2.pdf)

![](spectra_SSC2_nh2cho.pdf)

![](spectra_SSC2_ch2nh_correct.pdf)

![](spectra_SSC2_c2h5oh.pdf)

![](spectra_SSC5_ch3cho.pdf)

![](spectra_SSC5_ch3nh2.pdf)

![](spectra_SSC5_nh2cho.pdf)

![](spectra_SSC5_ch2nh_correct.pdf)

![](spectra_SSC5_c2h5oh.pdf)

+:---------:+:-------:+:-------:+:-------:+:-------:+:-------:+:-------:+:-------:+:-------:+
| Region    |         |                   |                   |                   |         |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| Component | 1       | 1       | 2       | 1       | 2       | 1       | 2       | 1       |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| FWHM (km s$^{-1}$)                                                                        |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| GMC 7     | 55      | 55.5    | ...     | 39      | ...     | 62      | ...     | 51      |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| GMC 6     | 54      | 53.5    | 44      | 59      | 45      | 50      | 39      | 53      |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| pSSC 5    | 44      | 47      | 35      | 43      | ...     | 45      | 54      | 40      |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| pSSC 2    | 49      | 46.5    | 53      | 40      | 25      | 44      | ...     | 47      |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| $V_\mathrm{peak}$ (km s$^{-1}$)                                                           |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| GMC 7     | 171     | 172     | ...     | 161     | ...     | 161.5   | ...     | 166     |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| GMC 6     | 186     | 179     | 184     | 176     | 194     | 154     | 187     | 168     |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| pSSC 5    | 243     | 242     | 243     | 235     | ...     | 229     | 221     | 238     |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+
| pSSC 2    | 287     | 284     | 281     | 281     | 300     | 264     | ...     | 273.5   |
+-----------+---------+---------+---------+---------+---------+---------+---------+---------+

: Mean FWHM and $V_\mathrm{peak}$ derived from the Gaussian fits (see Sec. [4.2](#subsec:rds)).

# Rotation diagrams

All the rotation diagrams for GMC 7, pSSC 5 and pSSC 2 are presented here. If one temperature component is fitted, we performed the rotation diagrams for the two possible sizes of emission, i.e. $1.6\ensuremath{''}$ for GMC scales and $0.12\ensuremath{''}$ for pSSC scales. We show here only the results of the fit for the GMC scales. The beam filling factor, (see Sec. [4.1](#subsec:methodology)), is 0.5 for GMC scales and $\sim 0.01$ for pSSC scales. Results for both source sizes are reported in Table [4](#tab:results_RDs).

![](RDs_GMC7_v2.pdf)

![](RDs_SSC5_v2.pdf)

![](RDs_SSC2_v2.pdf)

+:-------:+:---------:+:----------------:+:------------------------------:+:-------------------:+
| Species | Component | $T_{\text{rot}}$ | $N_{\text{tot}}$               | $\theta_S$          |
+---------+-----------+------------------+--------------------------------+---------------------+
|         |           | \(K\)            | ()                             | ($\ensuremath{''}$) |
+---------+-----------+------------------+--------------------------------+---------------------+
| GMC 7                                                                                         |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $19.0 \pm 2.0$   | $(1.6 \pm 0.3)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(1.5 \pm 0.2)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $16.0 \pm 4.0$   | $(3.9 \pm 1.4)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(3.5 \pm 1.3)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $15.1 \pm 1.5$   | $(1.5 \pm 0.4)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(1.3 \pm 0.3)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $8.7 \pm 0.6$    | $(4.6 \pm 0.8)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(4.1 \pm 0.7)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $18.0 \pm 2.0$   | $(10.0 \pm 2.0)\times 10^{14}$ | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(8.5 \pm 1.4)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
| GMC 6                                                                                         |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $34.0 \pm 2.0$   | $(5.3 \pm 0.5)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(4.8 \pm 0.6)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $9.2 \pm 0.8$    | $(17.0 \pm 3.0)\times 10^{14}$ | 1.6                 |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 2         | $25.5 \pm 3.8$   | $(10.0 \pm 3.0)\times 10^{16}$ | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $18.3 \pm 1.4$   | $(5.0 \pm 0.9)\times 10^{14}$  | 1.6                 |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 2         | $55.3 \pm 4.0$   | $(2.0 \pm 0.3)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $10.7 \pm 0.6$   | $(5.1 \pm 0.7)\times 10^{14}$  | 1.6                 |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 2         | $25.9 \pm 2.5$   | $(2.6 \pm 0.7)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $35.0 \pm 4.0$   | $(11 \pm 2)\times 10^{14}$     | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(10.0 \pm 1.5)\times 10^{16}$ | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
| pSSC 5                                                                                        |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $30.0 \pm 3.0$   | $(2.8 \pm 0.4)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(2.5 \pm 0.3)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $11.0 \pm 1.1$   | $(9.0 \pm 2.0)\times 10^{14}$  | 1.6                 |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 2         | $37.8 \pm 5.7$   | $(8.0 \pm 2.0)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $26.5 \pm 1.0$   | $(3.4 \pm 0.3)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(3.0 \pm 0.3)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $13.9 \pm 1.3$   | $(3.2 \pm 0.5)\times 10^{14}$  | 1.6                 |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 2         | $34.3 \pm 8.4$   | $(1.3 \pm 0.6)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $52.0 \pm 12.0$  | $(8.0 \pm 2.0)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(7.0 \pm 2.0)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
| pSSC 2                                                                                        |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $31.0 \pm 2.0$   | $(3.2 \pm 0.4)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(2.8 \pm 0.3)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $8.8 \pm 0.8$    | $(10.0 \pm 2.0)\times 10^{14}$ | 1.6                 |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 2         | $65.8 \pm 37.8$  | $(11.0 \pm 4.0)\times 10^{16}$ | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $11.7 \pm 0.8$   | $(3.9 \pm 0.8)\times 10^{14}$  | 1.6                 |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 2         | $70.9 \pm 6.7$   | $(1.0 \pm 0.2)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $12.5 \pm 0.6$   | $(3.6 \pm 0.4)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(3.3 \pm 0.4)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+
|         | 1         | $30.0 \pm 2.0$   | $(8.7 \pm 0.9)\times 10^{14}$  | 1.6                 |
|         |           |                  +--------------------------------+---------------------+
|         |           |                  | $(7.8 \pm 0.8)\times 10^{16}$  | 0.12                |
+---------+-----------+------------------+--------------------------------+---------------------+

: Results from the rotation diagrams.

Table notes: For the species for which we fitted only one temperature component, we performed the rotational diagrams for the two possible sizes of emission, i.e. $1.6\ensuremath{''}$ (GMC scale) and $0.12\ensuremath{''}$ (SSC scale). If two gas components could be fitted, we considered that the first component emits from GMC scales whilst the second component emits from pSSC scales (see text).

## LTE population diagram for 

We performed population diagrams (cite: goldsmith_1999) on to understand which of the optical depth or non-LTE effects affect the most the rotational diagrams we performed in Sec. [4.2](#subsec:rds) for this species. We used the optical depths and the emission size derived from the LVG analysis (see Sec. [4.3](#sec: nonlte)). The population diagrams are displayed below. As mentioned in Sec. [4.3](#sec: nonlte), the transitions at 225554 MHz and 172267 MHz were not included, as they were left out of the LVG analysis (hence, we do not have the optical depth values for these transitions).

![](ch2nh_pop_diagrams_thick_colored.pdf)

# Contour maps between the surveyed iCOMs and other species

We show here the various contour superposition maps as a support for the discussion in Sections [5.1](#sec:chemical_links) and [5.2](#sec:origin).

![](nh2cho_hnco_contours_map.pdf)

![](nh2cho_h2co_contours_map.pdf)

![](maps_sup_ch3oh_mols.pdf)

[^1]: Jansky Fellow of the National Radio Astronomy Observatory

[^2]: <http://www.iram.fr/IRAMFR/GILDAS>

[^3]: We used the formula $\eta_{ff}=\left({\theta_S^2}/(\theta_S^2+\theta_B^2)\right)$ with $\theta_S$ as the source size and $\theta_B$ as the beam size of the ALCHEMI observations.

[^4]: <https://emaa.osug.fr/>

[^5]: <https://kida.astrochem-tools.org/>

[^6]: <https://umistdatabase.net/>

[^7]: using the formula $\sigma_{\mathrm{obs}}=\frac{\sigma_0}{\sqrt{\mathrm{ln}2}}\sqrt{\mathrm{ln}\left(\frac{\tau}{\mathrm{ln}\left(\frac{2}{1+e^{-\tau}}\right)}\right)}$ with $\sigma_{\mathrm{obs}}$, $\sigma_0$ and $\tau_\nu$ the observed and intrinsic velocity dispersions, and the line opacity, respectively (cite: burton1992). The velocity dispersion ($\sigma_v$) is linked to the FWHM by $\sigma_v=\mathrm{FWHM}/2\sqrt{2 \ \mathrm{ln}(2)}$

</paper>

Write the methods card for this paper.