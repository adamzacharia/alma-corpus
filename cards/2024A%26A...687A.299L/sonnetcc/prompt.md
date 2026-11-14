# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A.299L\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024A&A...687A.299L",
 "title": "Chemistry across dust and gas gaps in protoplanetary disks. Modelling the co-spatial molecular rings in the HD 100546 disk",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Leemker, M.",
 "n_authors": 5,
 "arxiv_id": "2405.10361",
 "doi": "10.1051/0004-6361/202349072",
 "alma_projects_linked_by_archive": [
  "2011.0.00863.S",
  "2015.1.00806.S",
  "2016.1.00344.S",
  "2018.1.00141.S",
  "2021.1.00738.S"
 ]
}
```

Paper text:
<paper>
# Chemistry across dust and gas gaps in protoplanetary disks

Nearby extended protoplanetary disks are commonly marked by prominent rings in the dust emission, possibly carved by forming planets. High-resolution observations show that both the dust and the gas are structured. These molecular structures may be related to radial and azimuthal density variations in the disk and/or the disk chemistry. The aim of this work is to identify the expected location and intensity of rings seen in molecular line emission in gapped disks while exploring a range of physical conditions across the gap. In particular, we aim to model the molecular rings that are, in contrast with most other gapped disks, co-spatial with the dust rings at $\sim$20 and $\sim$200 au in the HD 100546 disk using the thermochemical code DALI. We model observations with the Atacama Large Millimeter/submillimeter Array (ALMA) of CO isotopologues, \[C I\], HCN, CN, , NO, and in the HD 100546 disk. An axisymmetric 3D thermochemical model reproducing the radial profiles of the CO isotopologue observations and the double ring seen in continuum emission is used to make predictions for various emission lines. The effect of the amount of gas in the dust gap, the C/O ratio, an attenuated background UV radiation field, and the flaring index on the radial distribution of different molecules are investigated.

The fiducial model of a gapped disk with a gas cavity at $0-15$ au, a dust cavity at $0-20$ au, and a gas and dust gap at $40-175$ au provides a good fit to the continuum and the CO isotopologues in the HD 100546 disk. In particular, the CO isotopologue emission is consistent with a shallow gas gap with no more than a factor of $\sim 10$ drop in gas density at $40-175$ au. Similar to the CO isotopologues, the HCN and model predictions reproduce the data within a factor of a few in most disk regions. However, the predictions for the other atom and molecules, \[C I\], CN, , and NO do not match the intensity nor the morphology of the observations. An exploration of the parameter space shows that in general the molecular emission rings are only co-spatial with the dust rings if the gas gap between the dust rings is depleted by at least four orders of magnitude in gas or if the C/O ratio of the gas is varying as a function of radius. For shallower gaps the decrease in the UV field roughly balances the effect of a higher gas density for UV tracers such as CN, , and NO. Therefore, the CN, , and NO radicals are not good tracers of the gas gap depth. In the outer regions of the disk around 300 au, these UV tracers are also sensitive to the background UV field incident on the disk. Reducing the background UV field by a factor of 10 removes the extended emission and outer ring seen in CN and , respectively, and reduces the ring seen in NO at 300 au. The C/O ratio primarily effects the intensity of the lines without changing the morphology much. The \[C I\], HCN, CN, and emission all increase with increasing C/O, whereas the NO emission shows a more complex dependence on the C/O ratio depending on the disk radius.

CO isotopologues and emission trace gas gaps and gas gaps depths in disks. The molecular rings in HCN, CN, , and NO predicted by thermochemical models do not naturally coincide with those seen in the dust, contrary to what is observed in the HD 100546 disk. This could be indicative of a radially varying C/O ratio in the HD 100546 disk with a C/O above 1 in a narrow region across the dust rings, together with a shallow gas gap that is depleted by a factor of $\sim 10$ in gas, and a reduced background UV field. The increase in the C/O ratio to $\gtrsim 1$ could point to the destruction of some of the CO, the liberation of carbon from ice and grains, or in case of the outer ring, it could point to second generation gas originating from the icy dust grains.

# Introduction

The gas, dust, and ice surrounding a young star are the building blocks of new planets. Many of the nearby, massive, and large protoplanetary disks have been observed to not be smooth but have gaps, rings, and arcs in the continuum emission that are possibly carved by massive forming planets (cite: Andrews2018; Huang2018; Long2018; Andrews2020; Francis2020). Recently, young planets with clear accretion signatures have been directly detected in the PDS 70 disk (cite: Keppler2018; Haffert2019; Benisty2021). Additionally, a point-like source consistent with a planet in a Keplerian orbit in the dust gap of the HD 169142 disk is seen (cite: Hammond2023) and the presence of a giant accreting planet is debated in the AB Aur disk (cite: Currie2022; Zhou2023). Promising signs of planets are actually now seen in disks through indirect methods such as detailed studies of the CO gas kinematics. (cite: Pinte2018; Teague2018; Pinte2019; Alarcon2022; Izquierdo2022; Izquierdo2023). The chemical composition of the solid core and gaseous atmosphere of these planets depends on the chemical composition of the ice and the gas in their protoplanetary disk. Comparing the composition in a protoplanetary disk to that measured in exoplanet atmospheres provides insights into where and when these planets have formed (cite: Oberg2011; Oberg2016; Cridland2016; Mordasini2016; Cridland2017; Cridland2023; Eistrup2023).

The chemical composition of the gas across a disk is not constant. Signs of chemical substructures have been found in simple gas-phase molecules such as the commonly observed CO, , , CN, HCN, and the recently detected NO (cite: Cazzoletti2018; Bergner2019; Qi2019; Aikawa2021; Bergner2021; Law2021; Zhang2021; Leemker2023; Temmink2023). These structures are seen both at the location of dust structures such as rings, gaps, and arcs, e.g. in the MWC 480, PDS 70, IRS 48, and the HD 100546 disks, as well as in regions uncorrelated to the dust e.g., four out of five disks observed in the MAPS (Molecules with ALMA at Planet-forming scales) program (cite: Facchini2021; Law2021; Booth2021irs48; Booth2021hd; vanderMarel2021irs48; Brunken2022; Jiang2022; Leemker2023). These ringed structures can thus be due to chemical rings or physical rings in the underlying gas density structure.

Young planets that are embedded in their native protoplanetary disk can carve a deep gap in the dust, and if they are sufficiently massive, also a gap in the gas as traced by CO emission (cite: Bruderer2014; Zhu2014; Dong2015; Rosotti2016; vanderMarel2016; Andrews2018; Long2018; Binkert2021; Oberg2021m; Zhang2021; Leemker2022). A gas gap in a planet forming disk not only reduces the amount of gas and dust at that location, it also reduces the attenuation of the UV radiation causing a relative increase in the UV field (cite: Cleeves2011; Facchini2018; Alarcon2020; Rab2020). This in turn leads to an increase of the dust temperature. The resulting gas temperature in the dust gap is a balance of the heating and cooling processes and can be either warmer or colder than the region just outside the gap (cite: Bruderer2013; Facchini2017; Alarcon2020; Broome2023). This change in temperature and UV field across the gap could lead to rings in other molecules as the chemistry in disks is sensitive to both of these.

A change in the temperature could lead to the freeze-out or thermal desorption of one of the major volatiles: , CO, and . These snowlines are the midplane locations where 50% of a molecule is in the gas-phase and 50% is frozen out onto the dust grains. This is exceptionally clear in the structure of and . These molecules respond very strongly to the desorption of , CO, and , resulting in ring-shaped emission outside ( and for the water and CO snowlines, respectively) or inside ( for the snowline) the snowline (cite: Qi2013; vantHoff2017; Leemker2021). On top of that, the abundance of , , and is set by the ionisation rate in the disk which may radially change due to substructures (cite: Aikawa2001; Cleeves2014; Aikawa2021).

In addition to snowlines, the stellar UV field is important for setting the chemistry in disks by photodissociating molecules in the surface layers of the disk. This not only destroys molecules, but it also enables formation paths to new ones. For example, the photodissociation of water produces OH which can lead to the formation of NO and the photodissociation of CO leads to the presence of atomic carbon in disks (cite: Thi2010; Bruderer2012; Schwarz2014; Leemker2023). Moreover, UV radiation can vibrationally excite molecular hydrogen () at intermediate disk radii. The extra energy stored in can then be used to overcome the energy barrier to form CN and NO in the surface layers of disks (cite: Agundez2010; Visser2018; Cazzoletti2018; PanequeCarreno2022; Leemker2023). Apart from the innermost regions in the midplane, HCN follows the same trend as it is closely related to CN in the disk surface layers. Therefore, ring-shaped CN and HCN emission is expected even if the underlying gas and dust surface density profiles are smooth (cite: Long2021).

In this paper we aim to investigate the conditions that lead to molecular rings coinciding with dust rings under different physical and chemical conditions. In particular, these results are applied to the HD 100546 disk, one of the gapped disks with molecular rings seen at the location of the continuum rings at 20 au and $\sim200$ au. In Sect. [2](#sec:methods) we present the \[C I\] data in the HD 100546 disk and describe the setup of our thermochemical models that include a gas and dust cavity as well as a gap between the two rings seen in the HD 100546 continuum and CO isotopologues. Section [3](#sec:results) presents a fiducial model that fits these data. In addition, the predictions for \[C I\], HCN, CN, , NO, and in this disk under different physical conditions, varying parameters such as a deep gas gap, an elevated C/O ratio, an attenuated background UV field, and disk flaring are presented. The results are discussed in Sect. [4](#sec:discussion) in the specific context of the HD 100546 observations and our conclusions are summarized in Sect. [5](#sec:conclusions).

![](Dali_structure_lin_zooms)

# Methods

## Source: HD 100546

HD 100546 is a $\sim 2$ M$_{\odot}$, 5 Myr old Herbig Ae/Be star with a luminosity of $\sim$36 L$_{\odot}$ (cite: Kama2016; Arun2019; Pineda2019). This star is located in a relatively isolated region at a distance of $108.1\pm 0.4$ pc (cite: Gaia2016; GaiaDR3). The star is surrounded by a massive and gas-rich disk of $0.03-0.1$ M$_{\odot}$ based on CO isotopologue emission, *Herschel* PACS and HIFI observations of the CO rotational ladder up to $J=38$, constraining temperature structure disk layers, and an upper limit on the HD flux (cite: Kama2016; Stapperinprep). The *Herschel* PACS observations of CO, C, and indicate that the gas in the surface layers of the disk is warmer than the dust (cite: Bruderer2012; Fedele2016). Additionally, this instrument revealed gas-phase water that is present outside $\sim40$ au in the HD 100546 disk (cite: vanDishoeck2021; Pirovano2022). Both the CO gas and the dust in this disk are structured with small scale gas and dust spirals (a few $0.1\ensuremath{''}$), a large scale ($\sim 1"$) dusty spiral and a large scale spiral in the gas kinematics ((cite: Garufi2016; Follette2017; Sissa2018; Norfolk2022); Wölfer et al. subm.). Additionally, the continuum emission in this disk is seen in three locations: an unresolved dusty inner disk, a bright inner ring from $\sim20$ au to 40 au, and a weak outer ring at $<1$% of the peak continuum intensity from $\sim150$ au to 250 au (cite: Bruderer2012; Walsh2014; Pineda2019; Fedele2021). This paper primarily focusses on the molecular emission at the location of the second ring at $\sim 200$ au and how this compares to the inner ring at $\sim 20$ au.

The central cavity and gap between the two dust rings have been hypothesized to be carved by massive planets. The inner planet has been inferred from CO ro-vibrational emission and a feature seen in scattered light (cite: Brittain2013; Brittain2014; Currie2015; Brittain2019). In addition, co-rotating SO emission is seen at the location of the proposed planet (cite: Booth2023). A second planet has been hypothesized between the two dust rings as a point source is seen at $50-60$ au in scattered light observations (cite: Quanz2013; Currie2014). However, the nature of these potential planets is debated as no accretion signatures have been found at this location and different results have been found depending on the data quality and imaging techniques (cite: Currie2017; Follette2017; Rameau2017). Therefore, more research is needed to firmly conclude if these planets are present.

ALMA observations of molecular lines have revealed a number of different molecules in this disk. The detection of formaldehyde and the complex organic molecule methanol in this warm disk indicates that the molecular inventory is likely inherited from the native dark cloud as the bulk of the disk is too warm for CO freeze-out (cite: Booth2021hd). The CS and SO emission peak at different radii, with the transition between the two coinciding with the inferred water snowline location at the inner edge of the dust cavity (cite: Keyte2023; Boothinprep). Finally, many of the molecular lines except the CO isotopologues are close to co-spatial with the rings seen in the dust and are consistent with a flat disk despite emitting from higher disk layers ((cite: Law2022; Stapper2023; Boothinprep); Wölfer et al. subm.). In this work, we use high resolution ALMA observations at $\sim0.1\ensuremath{''}$ spatial resolution of the dust and CO isotopologues ((cite: Pineda2019; Perez2020; Wolfer2023), subm.), intermediate resolution data at $\sim0.2\ensuremath{''}-0.5\ensuremath{''}$ of the dust, CO, , HCN, CN, , NO, and (cite: Boothinprep), and \[C I\] observations to elucidate the origin of the observed molecular substructures.

## ALMA data covering \[C I\]

The $J=7-6$ and \[C I\] line emission data used in his paper were taken in Cycle 6 with ALMA in Band 10 (2018.1.00141.S; PI: B. Dent), using 43 antennas with baselines of 15-783 m. Starting from the archival pipeline-calibrated data we performed further data reduction using CASA (cite: McMullin2007). Due to a low signal-to-noise ratio, no self-calibration was applied. We first subtracted the continuum using the `uvcontsub` task, flagging channels containing line emission, and then imaged the lines with `tCLEAN` for both the continuum-subtracted and non-subtracted data sets. In this process, we imaged the data at the highest spectral resolution possible and adopted a Briggs robust weighting of 0.5, which gave the best trade off between spatial resolution and sensitivity. We also applied a Keplerian mask[^1] using an inclination of 42 , position angle of 140 , distance of 110 pc, stellar mass of 2.13 M$_{\odot}$, and systemic velocity of 5.7 km s$^{-1}$. We further used the multi-scale deconvolver (scales 0,5,10,20) and a slight `uv-taper` ($0.05\ensuremath{''}\times 0.05\ensuremath{''},0\,\degree$) to improve the signal-to-noise ratio in the images. This resulted in an image with a spatial resolution of $0.21\ensuremath{''} \times 0.16\ensuremath{''}\ (28\degree)$ and a maximum recoverable scale of 2" in diameter (108 au in radius). The integrated intensity map and the spectrum are presented in Fig. [13](#fig:CI_obs).

![](DALI_fid_high_res_v2)

## DALI

To investigate the relative importance of physical versus chemical rings, we model the dust rings and rings seen in molecular line emission using the thermochemical code Dust And LInes (cite: Bruderer2009; Bruderer2012; Bruderer2013). The model presented in this work is based on those presented in (cite: Pirovano2022) and (cite: Keyte2023). We improve on the dust structure from the latter model by including a dust gap in the outer disk to match the double ringed structure of the continuum observations (cite: Fedele2021; Boothinprep). Additionally, the gas density structure is improved by including a gas gap between the two dust rings and by including an inner gas cavity just inside the inner dust ring at 20 au to match the observed CO emission in those regions ((cite: Perez2020; Boothinprep); Wölfer et al. subm.). The general setup of the model is described below.

### Gas density structure

The radial and vertical density structure of the disk follow the standard DALI setup for a flared disk with an exponentially tapered power law in the radial direction and a Gaussian distribution of the gas in the vertical direction (cite: Bruderer2013). To include the gas cavity and a gas gap in this disk, the gas surface density of the full disk is lowered as follows: $$\begin{equation}
  \Sigma_{\rm gas} =
    \begin{cases}
      \Sigma_{\rm gas\ full}\times 10^{-5} & (0.4~\mathrm{au} < r < 15~\mathrm{au})\\
      \Sigma_{\rm gas\ full}\times 10^{-2} & (15~\mathrm{au} < r < 20~\mathrm{au})\\
      \Sigma_{\rm gas\ full} & (20~\mathrm{au} < r < 40~\mathrm{au})\\      
      \Sigma_{\rm gas\ full}\times \delta_{\rm gas\ gap} & (40~\mathrm{au} < r < 175~\mathrm{au})\\
      \Sigma_{\rm gas\ full} & (175~\mathrm{au} < r < 1000~\mathrm{au}),\\            
    \end{cases}       
\end{equation}$$ with $\delta_{\rm gas\ gap}$ lowering the gas density in the gap, see the left panel of Fig. [1](#fig:dali_structure) and the top left panel of Fig. [2](#fig:dali_2D_basic_fid).

### Dust density structure

The small grains follow the gas outside the inner gas cavity as they are expected to be well mixed with the gas. Outside the gas cavity but inside the dust cavity the small grains also follow the gas. Inside the gas cavity down to the dusty inner disk that is observed in continuum emission up to $<2$ au (cite: Benisty2010; Pineda2019; Perez2020), the small grains are depleted by a factor of $10^{-10}$ to mimic a cavity devoid of any dust. The dusty inner disk inside 1 au is depleted in small (5 nm$-$1 $\mu$m) and large (5 nm$-$1 mm) grains by a factor of $10^{-2}$ (see also the (top) middle panel in Fig. [1](#fig:dali_structure) and Fig. [2](#fig:dali_2D_basic_fid)): $$\begin{equation}
  \Sigma_{\rm s\ dust} =
    \begin{cases}
      \Sigma_{\rm s\ dust\ full}\times 10^{-2} & (0.4~\mathrm{au} < r < 1~\mathrm{au})\\
      \Sigma_{\rm s\ dust\ full}\times 10^{-10} & (1~\mathrm{au} < r < 15~\mathrm{au})\\
      (1-f_{\rm ls})\times \Sigma_{\rm gas}/\Delta_{\rm gd} & (15~\mathrm{au} < r < 1000~\mathrm{au}).          
    \end{cases}       
\end{equation}$$ In the vertical direction the small dust follows the gas.

Observations show that the large dust in the HD 100546 disk is mainly present at three different locations: a dusty inner disk, an inner ring at $20-40$ au, and an outer ring at $175-250$ au (cite: Walsh2014; Pineda2019; Fedele2021). The cavity in the large dust in our model is 5 au larger than that in the small dust and the gas, similar to what is observed in other transition disks (cite: Perez2015; vanderMarel2016; Leemker2022; Wolfer2023). This is parametrized as: $$\begin{equation}
  \Sigma_{\rm l\ dust} =
    \begin{cases}
      \Sigma_{\rm l\ dust\ full}\times 10^{-2} & (0.4~\mathrm{au} < r < 1~\mathrm{au})\\
      \Sigma_{\rm l\ dust\ full}\times10^{-10} & (1~\mathrm{au} < r < 20~\mathrm{au})\\
      \Sigma_{\rm l\ dust\ full} & (20~\mathrm{au} < r < 40~\mathrm{au})\\
      \Sigma_{\rm l\ dust\ full}\times 10^{-10} & (40~\mathrm{au} < r < 175~\mathrm{au})\\
      \Sigma_{\rm l\ dust\ full} & (175~\mathrm{au} < r < 250~\mathrm{au})\\
      \Sigma_{\rm l\ dust\ full}\times 10^{-10} & (250~\mathrm{au} < r < 1000~\mathrm{au}).    
    \end{cases}       
\end{equation}$$ The outer ring extends to 250 au, see also the right panel of Fig. [1](#fig:dali_structure). Additionally, the large grains are settled to the disk midplane (top right panel in Fig. [2](#fig:dali_2D_basic_fid)). The dust in the midplane of the outer dust ring is sufficiently cold for some CO freeze-out as the dust temperature drops below 20 K (bottom row, middle panel in Fig. [2](#fig:dali_2D_basic_fid)).

## Stellar spectrum

The stellar spectrum of HD 100546 observed by the Far Ultraviolet Spectroscopic Explorer (FUSE) and the the International Ultraviolet Explorer (IUE) and presented in (cite: Bruderer2012) is used. These observations have been dereddend and extended to longer wavelengths using a B9V template (cite: Pickles1998). Additionally, an X-ray luminosity of $7.9\times 10^{28}$ erg s$^{-1}$ (cite: Stelzer2006) with a temperature of $7\times 10^7$ K is included to account for more energetic radiation.

## Chemistry

Fig. [3](#fig:fid_dust_CO) summarizes the observed distribution of CO isotopologues and dust in the HD 100546 disk in black. The chemistry is modelled using a chemical network suited for modelling small nitrogen bearing molecules such as CN, HCN, and NO, and small hydrocarbons such as . This network was first presented in (cite: Visser2018; Cazzoletti2018); and (cite: Long2021) and includes 134 species and 1844 reactions. Similar to (cite: Leemker2023), the binding energy of (ethylenyl) is set to $10^4$ K to mimic the conversion of to larger COMs on the grain surfaces. This network includes the main gas-phase formation and destruction routes of the molecules of interest, the photodissociation and photoionization of relevant gas-phase molecules, self-shielding of , CO, and C, the freeze-out and thermal-, and non-desorption of the major volatiles. The non-thermal desorption rates of and CO are updated from $1.3\times 10^{-3}$ and $2.7\times 10^{-3}$ molecules desorbed per grain per incident UV photon to $5\times 10^{-4}$ and $1.4\times 10^{-3}$ molecules desorbed per grain per incident UV photon respectively (cite: Oberg2007; Oberg2009; Paardekooper2016; GonzalezDiaz2019; Fillion2022). Additionally, some grain surface reactions are included such as the formation of on grains and PAHs. Moreover, the hydrogenation of O, C, N, and CN on grains to form , , , and HCN ices are included. Nevertheless, no detailed ice chemistry such as the conversion of CO to or is modelled as the HD 10546 disk is warm and no large-scale CO freeze-out is expected.

The abundance of the CO isotopologues is predicted with the CO isotopologue network presented in (cite: Miotello2016) consisting of 185 species and 5755 reactions. This network includes the , , , , and isotopes, with their ratios taken as / = 77, / = 560, and / = 1792 (cite: Wilson1994). Similar to the nitrogen network, this network includes the freeze-out and thermal desorption of simple species and their isotopologues, some grain surface reactions to model the hydrogenation of C, N, and O to , , , and their isotopologues, and isotope selective photodissociation. In addition, self-shielding of , CO, and their isotopologues, and of C are included as well as fractionation reactions. Both chemical networks are started with molecular initial conditions and a fiducial total (gas $+$ ice) C/O ratio of 0.4 (see Table [\[tab:dali\]](#tab:dali) and [7.1.2](#app:dali_chem_init)).

For the abundance, the chemical network presented in (cite: Leemker2021) is used. This is a small chemical network with ten reactions and the same number of species centred around . This network does include the freeze-out and thermal desorption of , but not that of CO. The is formed through an ion-molecule reaction of CO with and it is destroyed by dissociative recombination with an electron and by the reaction with gas-phase water. The formation of is driven by ionization of by cosmic rays creating that subsequently reacts with to form . is destroyed by reactions with electrons, gas-phase water and CO. As the only carbon-bearing molecules in this network are CO and , this network is only run for the models with C/O $<1$. This network is evolved using the density and temperature structure of the DALI model together with initial CO and abundances to match the C/O ratio. All chemical networks are evaluated at 5 Myr, the approximate age of the HD 100546 star (cite: Arun2019; Pineda2019).

![](dust_and_CO_fid)

## Raytracing

The synthetic ALMA observations are produced using the raytracer in DALI. The level populations are calculated without assuming local thermodynamical equilibrium (LTE) using the collisional rate coefficients for , , , , C, HCN, CN, , NO, and in the LAMDA database[^2] (cite: Launay1977; Johnson1987; Roueff1990; Schroder1991; Staemmler1991; Schoier2005; Dumouchel2010; Lique2010; Yang2010; Spielfiedel2012; Denis2020; Ben2021). An overview of the investigated transitions is presented in Table [\[tab:trans\]](#tab:trans). The observed and NO data cover two respectively three lines that are blended with themselves. Therefore, these two and three transitions were raytraced and added assuming the emission is optically thin. Finally, all synthetic image cubes are continuum subtracted and convolved to a beam matching that of the observations of that particular species (see Table [\[tab:trans\]](#tab:trans)).

# Results

Thermo-chemical models are not expected to reproduce the observed line emission within the uncertainty of the data as the predicted molecular line emission depends both on the abundance of a certain molecule as well as the temperature of the emitting layer. The parameter studies of the DALI thermo-chemical code show a factor of $\sim$2 difference in the CO line flux due to e.g. uncertainties in reaction rates in the chemical networks (cite: Bruderer2012; Bruderer2013) and a somewhat larger factor is expected for molecules other than CO. Therefore, a model is expected to reproduce the data within a factor of $\sim 2-3$ in general (cite: Kama2016; Sturm2023). In addition, a thermochemical model reproducing the observed line intensities within this factor is not unique and degeneracies in the model exist due to e.g., differences in the physical and thus thermal and chemical structure of the model. Instead of matching the observed line intensities within the uncertainty of the data, we look for trends in the abundances and line intensities for a range of key parameters such as gap depth and chemical composition. As the intensity of the continuum and CO isotopologues are less uncertain in the model than the intensity of \[C I\], HCN, CN, , NO, and , the fiducial model aims to reproduce the dust and the CO isotopologue emission. Section [3.1](#sec:methods_fid) presents fiducial model reproducing the CO isotopologue and continuum observations and the subsequent sections present the trends seen in HCN, CN, , NO, , and \[C I\] in the fiducial model and variations on the fiducial models.

## The fiducial model

The key feature of the emission in the HD 100546 disk is that all molecular rings are co-spatial with the dust rings, whereas the CO isotopologue emission appears smooth. The only structure seen in the CO isotopologue emission is a central gas cavity and a weak shelf of and emission extending from 150 au to 250 au (see insert in the bottom middle and right corner of Fig. [3](#fig:fid_dust_CO)). Therefore, the aim of the fiducial model is not to fit the CO isotopologues perfectly. Instead, the aim of the fiducial model is to provide a basis that roughly fits the continuum and the CO isotopologues and explore under what conditions the molecular rings coincide with those seen in the continuum emission. The observations of the outer molecular rings are all consistent with emission originating from close to the midplane (cite: Boothinprep). Therefore, the fiducial model has a low flaring index of $\psi = 0$ and a low scale height of $h_c = 0.1$ at the characteristic radius. This flat disk model roughly reproduces the observed emitting heights in the HD 100546 disk as presented in Appendix [7.2.2](#app:COemission_and_heights) and in (cite: Law2022; Stapper2023); Wölfer et al. subm. A comparison of our fiducial model with those presented in (cite: Pirovano2022) and (cite: Keyte2023) is shown in Fig. [14](#fig:dali_structure_lit), where the main differences are that the model presented in this work is significantly less flared than those presented in (cite: Pirovano2022) and (cite: Keyte2023), and has a gas cavity at $< 15$ au that is not present in (cite: Keyte2023). An overview of the parameters of the fiducial model is presented in Table [\[tab:dali\]](#tab:dali).

The gas and dust density, temperature, and UV field in this model are presented in Fig. [2](#fig:dali_2D_basic_fid). The midplane gas density drops down to a low value of $10^7$ cm$^{-3}$ at 250 au, which is too low for the gas and dust to be thermally coupled in the midplane. Therefore, the gas temperature at these locations is colder than that of the dust. The small dust follows the gas outside the gas cavity at 15 au. The large dust is only seen in the two dust rings at $20-40$ au and $175-200$ au. A steep drop in the UV field is seen at $z/r = 0.2$. This layer also roughly separates the warm surface layer of the disk from the layers below 50 K closer to the midplane. This flat model intercepts less UV radiation from the central star than more flared models, which causes a small amount of CO freeze-out in the outer dust ring.

The resulting model emission of the mm-dust and the CO isotopologues is presented in Fig. [3](#fig:fid_dust_CO) (orange lines). The top row presents the fits of the fiducial model to the dusty inner disk and the dust ring from $20-40$ au seen in the high resolution continuum (left panel) as well as the much weaker dust ring at $175-250$ au seen at moderate spatial resolution (middle panel; (cite: Pineda2019; Boothinprep)). The weak outer continuum ring is not seen in the left panel due to the high spatial resolution and small maximum recoverable scale (26 au in radius) of that dataset.

The gas density structure is improved by including a 15 au gas cavity that is seen in the high spatial resolution $J=2-1$ transition of , , and presented in the middle and bottom left panels in Fig. [3](#fig:fid_dust_CO) ((cite: Perez2020); Wölfer et al. subm.). To match these data, the gas density inside the gas cavity is lowered by a factor of $10^{-5}$ and between the gas (15 au) and dust cavity (20 au) by a factor of $10^{-2}$. Outside the gas cavity, the , , and emission matches that of the observations ((cite: Perez2020; Boothinprep); Wölfer et al. subm.), with an especially close match being achieved for the and emission. The ring at 200 au in the modelled and emission is due to a very low and column density just inside this ring as the column density becomes too low for self-shielding to be efficient (see Fig. [15](#fig:N_COisos)). The $J=3-2$ and $J=7-6$ emission presented in (cite: Boothinprep) and Wölfer et al. subm. is underproduced by at most a factor of $\sim 2$ likely due to the gas temperature that is slightly too low in this flat model. However, the main focus of the fiducial model is on the rarest CO isotopologues ( and ), the dust rings and the molecular line emission.

The lack of mm-dust between the two dust rings in the HD 100546 disk may be due to a massive planet carving a gap in the disk (cite: Pinilla2015; Fedele2021; Pyerin2021). Therefore, the gas density in this region may be lower than in a full disk model. This is explored in Fig. [16](#fig:dali_dgas_gap) and we find that CO isotopologue emission is consistent with a shallow gas gap where the gas is depleted by at most one order of magnitude, assuming that the gas and dust gap have the same widths.

![](DALI_fid_molecules_ncrit_v2)

## 2D abundance maps

The 2D abundance structures of the molecules of interest, HCN, CN, , NO, and , are presented in Fig. [4](#fig:dali_2D_mol_fid) together with the CO abundance for reference. The abundances are calculated with respect to the total hydrogen density: $n_{\rm h} = n(\mathrm{H}) + 2\times n(\mathrm{H_2})$. All of these molecules except CO follow the same global morphology: a surface layer with a high abundance that extends from the inner dust ring or the gap out to the outer disk at 400 au where the layer moves down to the midplane. Additionally, HCN and CO are abundant at lower disk layers and the NO and layers extend to the disk midplane from $\sim150$ au outward. The CO is abundant throughout the entire disk except in the surface layers where CO is photodissociated and in the midplane in the outer dust ring where CO is frozen out onto the dust grains.

HCN, CN, , and NO are sensitive to the UV field. The UV radiation in the surface layer forms vibrationally excited molecular hydrogen, , whose abundance is calculated using a two-level approximation in the chemical network with far-UV photons pumping to and collisional decay and spontaneous radiative decay transforming to (cite: Bruderer2012). then reacts with N to form NH which then reacts with to form that is converted to CN and HCN. Additionally, a pathway through CH and N to form CN is also seen in this region. As the UV field only penetrates the surface layers of the disk, the HCN, CN, and are also constrained to this layer and thus reside in a layer where the number density of molecular hydrogen is below the respective critical densities (cyan contours in Fig. [4](#fig:dali_2D_mol_fid)). The HCN molecule is not only abundant in a surface layer at $z/r > 0.2$; a secondary layer formed through different chemical reactions exists around a height of $z/r=0.1$. Here, the HCN is mainly formed through a reaction of atomic carbon with to form through radiative association which then reacts with O and N to form CO and HCN. As this layer is below the HCN snow surface (white contour in Fig. [2](#fig:dali_2D_basic_fid)), this HCN quickly freezes-out.

Somewhat deeper in the disk at $z/r=0.2$ NO is abundant. The NO is mainly formed through the reaction of NH with O with a minor contribution of the reactions of OH and N ($<10\%$). The NO layer lies somewhat deeper in the disk than that of HCN, CN, and due to the destruction of NO by atomic carbon and nitrogen that (re)forms CO, CN, and . At lower layers below $z/r = 0.1$, NO quickly freezes-out onto the dust grains as the NO snowline is located at a scale height of 0.1 in the dust gap and the outer dust ring. The thin NO layer at $z/r =0.4$ is due to the photodissociation of water forming OH (see also (cite: Leemker2023)).

![](moment_maps_linear_fid.png)

Finally, the abundance outside 15 au is driven by the cosmic ray ionization rate enhancing the abundance. In addition to ionisation, the ion traces the water snowline: a high abundance is only seen outside the water snowline where water cannot destroy (cite: Phillips1992; Bergin1998). The water snowline in this model is located at the outer edge of the gas cavity at 15 au. Therefore, the abundance at larger radii scales as $\sqrt{\zeta_{\rm c.r.}/n_{\rm H_2}}$ with a weak dependence on temperature (cite: Leemker2021). This may overpredict the abundance outside the inner dust ring in this disk as cold, gas-phase water is seen outside $\sim40$ au in this disk and water photodesorption is not included in the small chemical network (cite: vanDishoeck2021; Pirovano2022).

Altogether, the 2D abundance structures of HCN, CN, , NO, and are dominated by a layer with a high abundance centred at $z/r \sim 0.2-0.3$. This layer is located at or above the critical density of HCN, CN, and , therefore, these molecules may not be in LTE and the high excitation lines may be less populated whereas the ground level may be more populated than what is expected in LTE. This layer with a high abundance of $10^{-7}-10^{-9}$ is similar to the observed emitting layer of CO and higher than the layer of $z/r \leq 0.1$ that the HCN, CN, , and observations suggest (cite: Boothinprep). The high abundance layer moves down slightly inside the gas gap due to the lower gas density, but apart from this, no clear jump in the abundance at the location of the outer dust ring is seen.

## Integrated intensity maps

The integrated intensity (moment 0) maps of the data and the fiducial model are presented in Fig. [5](#fig:mom0_fid). The modelled emission reproduces the observations within a factor of two for most disk regions with the outer ring in being more prominent in the model than in the data (see also Fig. [3](#fig:fid_dust_CO), bottom row). For the other molecules on the other hand, the observed intensities or the double ringed profile are not reproduced. Only the modelled HCN and emission do show a hint of an outer ring at the location of the second dust ring whereas the and NO show a (weak) ring outside the outer dust ring at larger distances than observed. The lack of molecular rings at the location of the outer dust ring in the models is not due to optically thick dust hiding the line emission at that location. This is because the modelled continuum emission in the outer disk is optically thin and therefore does not absorb line emission that is emitted from the disk midplane at that radial location. In addition, the HCN, CN, , NO, and are most abundant in an elevated layer, well above the heights where the large dust is abundant (see Fig. [2](#fig:dali_2D_basic_fid) and Fig. [4](#fig:dali_2D_mol_fid)). The intensity of weak ring at $\sim 375$ au seen in the model predictions has an intensity that is similar to the 2$\sigma$ level of the observations. Therefore, this ring may be hidden in the noise in the observations.

The inner ring that is observed in HCN and CN is reproduced by the model within a factor of $\sim 2$ but the observed ring at 40 au is not seen in the model. The modelled emission is ring-shaped in the inner disk with a ring at 60 au, whereas the data are centrally peaked at the spatial resolution of the observations. The intensity in the modelled ring is two times higher than what is observed at the central location.

The model predicts outer rings in HCN and that are only a factor of $\sim 3$ weaker and a factor of two brighter than what is observed, respectively. However, the model does not reproduce the outer ring in as the modelled ring is two orders of magnitude weaker and 170 au further out than seen in the data. In addition, the predicted intensity falls below the sensitivity of the data out to 300 au. The observed outer ring in CN is not recovered by the model and the modelled NO emission is mostly seen at the inner dust ring at $\sim 20$ au and outside the outer dust ring at $280$ au whereas the observations show some emission between the two dust rings and possibly at the location of the outer dust ring. In summary, Fig. [5](#fig:mom0_fid) shows that despite a good fit to the continuum and CO isotopologue emission, the model does not reproduce the observations of molecules other than CO isotopologues, especially for CN, , and NO. The chemical network used to calculate these abundances reproduces the CN, HCN, HNC, and emission in other protoplanetary disks within a factor of a few in general (cite: Cazzoletti2018; Visser2018; Miotello2019; Long2021). Therefore, the difference between the model predictions and the observations in the HD 100546 disk are likely due to the physical or chemical structure of the disk rather than uncertainties in the chemical network.

![](Nmolecules_diff_gap.png)

## The effect of a gas gap of at least one order of magnitude

A possible solution to create double rings in the molecular line emission is to induce a deep gas gap between the two dust rings. The and emission do not show any evidence of a gas gap deeper than the fiducial depth of a factor of 10, neither does the where only a shoulder of emission extending out to $200-300$ au is observed (see Fig. [16](#fig:dali_dgas_gap)). Still, a depletion of gas could affect the molecular line emission. Therefore, the effect of a deeper gas gap is investigated in this subsection. The small dust is assumed to follow the drop in the gas density.

### Column densities

The effect of the depth of the gap between 40 and 175 au on the column density is presented in Fig. [6](#fig:dali_N_dgap) where the column densities inside 250 au are smoothed in log space with a savgol filter in scipy over 10 points and a 3rd order polynomial to remove any artificial spikes due to low photon statistics in the model. The CO column density directly traces the drop in the gas density for gaps up to three orders of magnitude in gas density. For deeper gaps, CO photodissociation becomes important and the CO column density drops even faster than the gas density.

The column density directly follows that of the gas where a drop of two orders of magnitude in gas column density results in a one order of magnitude drop in the column density. The reason for this is that the number density outside the water snowline follows $n({\rm HCO^+}) \propto \sqrt{\zeta_{\rm c.r.}\times n({\rm H_2})}$, with $\zeta_{\rm c.r.}$ the cosmic ray ionisation rate and $n({\rm H_2})$ the density of molecular hydrogen (cite: Leemker2021). Therefore, the column density in the gap is directly related to that of the gas.

![](DALI_2D_dgas_v3)

The CN, , and NO show a different pattern in their column densities than CO, but a similar pattern to each other, when the gap depth is increased. For shallow to somewhat deep gas gaps ($\delta_{\rm gas\ gap} \sim 1-10^{-2}$), their column densities are independent of the gap depth within a factor of a few. For very deep gas gaps ($\delta_{\rm gas\ gap} \sim 10^{-4}-10^{-5}$), a steep decrease in the column density is seen in the outer parts of the gap. The sharp peaks in the HCN, CN, , and NO column densities at the inner ring and inner region of the gap (15, 20, and 40 au) may be sensitive to the precise conditions in this region.

The behaviour in the gap can be understood from the 2D UV field and CN abundance which are presented in Fig. [7](#fig:dali_2D_dgap). Shown are the results for a shallow gap ($10^{-1}$) and two deep gaps ($10^{-3}$ and $10^{-5}$), in the left column, a shallow gas gap is present, but the CN is only abundant in a layer high above the midplane at $z/r =0.3$ in the gap. Changing the amount of gas in this region only shifts this layer up or down, but it does not affect the column density greatly as the midplane abundance of CN is low. For a deep gas gap (middle and right columns), the UV field is more intense in the gap than in the model with a shallow gas gap with an intensity up to 100 G$_{\rm 0}$ in the midplane in the gap. As CN is sensitive to the UV field, its abundance increases in the gap. The resulting CN column density is an interplay of an increase in the abundance that is most prominent at small radii, and a decrease in the gas column density that is most effective at large radii. This causes a peak in the CN column density that moves to smaller radii of 75 and 50 au with deeper gaps of $10^{-4}$ and $10^{-5}$, respectively. As and NO are also sensitive to the UV field, their abundances and column densities show the same qualitative behaviour. Note the increasing column density at radii larger than 200 au. Especially for , the inward travelling peak in the column density is clearly visible at 160 au, 140 au, 70 au, and 50 au for $\delta_{\rm gas\ gap} = 10^{-2}, 10^{-3}, 10^{-4}, 10^{-5}$, respectively.

The HCN column density always decreases or stays constant with deeper gaps due to the moderate HCN abundance in the midplane together with the high abundance in the surface layer. The component in the midplane slowly decreases up to a gap depth of $10^{-2}$, lowering the HCN column density simultaneously. For deeper gaps, the midplane component of HCN vanishes and the HCN column density steeply drops with gas density, similar to the pattern seen for CN, , and NO.

![](moment_maps_linear_las6.0_incl41_diff_dgas.png)

### Emission maps

The integrated intensity (moment 0) maps for different gas gap depths are presented in Fig. [8](#fig:dali_mom0_dgap) and the azimuthally averaged radial profiles are presented in Fig. [18](#fig:dali_azi_avg_dgap). The fiducial model is presented on the third row and the moment maps are identical to those presented in Fig. [5](#fig:mom0_fid) but on a different colorscale. In general, the molecular line emission shows ringed emission for all models that have some degree of gas depletion between the dust rings ($\delta_{\rm gas\ gap} = 10^{-1}-10^{-5}$). However, double rings are only seen for the models with a very deep gas gap ($\delta_{\rm gas\ gap} = 10^{-4}-10^{-5}$). These rings are typically located outside the dust rings instead of at or just beyond the dust as seen in the observations. For example, the NO emission shows a very clear double ring for these models, but the outer ring is located at $\sim$280 au where no NO is seen in the data. The emission shows a ring of emission inside the gas gap that moves inwards with increasing gap depths following the corresponding column density. This effect is also seen in the CN and NO emission, although it is less pronounced. The NO emission just outside the inner ring is sensitive to a sharp peak in the column density and may be very sensitive to the conditions in this region. The remaining three molecules, , HCN and all show double ringed emission profiles for all models with some gas depletion.

The model with a deep gas gap of $10^{-4}$ times less gas best reproduces the double ringed nature of the HCN, CN, and observations, whereas the model with a factor of ten more gas ($\delta_{\rm gas\ gap} = 10^{-3}$) reproduces the diffuse emission between the dust rings better. The first model reproduces the morphology of the molecular line emission just outside the inner dust ring for CN and while also predicting a reasonable intensity for HCN. Additionally, this model reproduces the presence of an outer ring at $200-250$ au seen in HCN, CN, and . The CO isotopologue emission on the other hand is best reproduced by a disk with a shallow gap of only $10^{-1}$ times less gas as the emission in the gap is directly related to the drop in gas density. In summary, there is not a single gas gap depth that can explain the observed emission of all molecules simultaneously.

### Molecular column densities and line ratios

Ratios of column densities can give additional insights into the underlying processes as they are less sensitive to the absolute model results. The column density ratios of /CO, /CO, CN/HCN, and CN/NO are presented in Fig. [23](#fig:Nratios_diff_gaps) for a model without a gas gap and models with gap depths up to $10^{-5}$. The first three ratios increase with radius outside the outer gas cavity in the full gas disk model, whereas the CN/NO ratio first increases inside the dust gap, then slowly decreases up to the outer dust ring and then somewhat increases again. This is caused by the different radii where the CN and NO column densities peak in the disk. The /CO and /CO ratios increase due to the increasing column density in and as that of CO smoothly decreases with radius. Finally, the increase in the CN/HCN ratio is driven by the decreasing column density of HCN. Comparing these ratios to ratios of /CO and /CO in the inner and outer dust ring presented in (cite: Boothinprep) shows that the fiducial model is consistent with the /CO ratio but that the /CO ratio likely requires a deep gas gap of multiple orders of magnitude or an overall increase in the column density.

When a gas gap is introduced, the ratios presented in Fig. [23](#fig:Nratios_diff_gaps) all increase compared to the model without a gas gap except for a disk with a gap of $10^{-1}$ and $10^{-2}$ times less gas where the CN/NO ratio stays roughly constant in the gap. The same trend is seen in the ratios for models with $\delta_{\rm gas\ gap} = 1-10^{-2}$ of the corresponding molecular lines presented in Fig. [24](#fig:Iratios_diff_gaps). For deeper gas gaps, the line ratios become insensitive to the gas gap depths due to the finite resolution of the observations. This is because part of the bright emission in the rings leaks into the gap regions, causing these regions to be dominated by the rings for deep gas gaps. Altogether, the column density ratios /CO, /CO, and CN/HCN of show a strong dependence on the gas gap depth that is much weaker in the ratios of the emission lines.

## Different C/O ratios

![](molecules_fid_diff_C_O_las6.0_incl41)

### Column densities and emission profiles

The observed emission is two orders of magnitude brighter than predicted by the fiducial model. Observations in other disks show that the emission becomes significantly brighter when the C/O ratio of the gas exceeds 1 (cite: Bergin2016; Miotello2019; Bosman2021C2H; Cridland2023). In this section, the effect of an increased C/O ratio is explored in the fiducial model with a gas gap of $\delta_{\rm gas\ gap} = 10^{-1}$. The 2D abundance maps for and NO are presented in Fig. [20](#fig:dali_2D_dC_O). The 2D abundance maps in the left column are the maps for the fiducial model and are the same as those presented in Fig. [4](#fig:dali_2D_mol_fid). The middle and right columns show these maps for a C/O ratio just below one at 0.99 and just above one at 1.01, while the C/H ratio is the same as in the fiducial model. As the C/O ratio increases, the layer where is abundant moves down from $z/r = 0.3$ for C/O = 0.4 to $z/r = 0.2$ for C/O = 0.99 and then it jumps down to $z/r = 0.15$ for a C/O ratio that is only 0.02 higher at 1.01. The peak abundance in this layer also jumps from $\sim 2\times 10^{-9}$ to $4\times 10^{-9}$ and to $7\times 10^{-8}$ for C/O = 0.4, 0.99, and 1.01, respectively. A similar trend is seen for HCN, CN, and C.

The NO abundance shows the opposite behaviour as NO is expected to become less abundant when the C/O ratio is high. This is also seen in the 2D abundance maps as the NO abundance quickly decreases if the C/O is increased from 0.4 to 0.99 by removing water. As the C/O ratio further increases, the NO layer splits into two regions around $z/r = 0.05$ below its snow surface and one at $z/r = 0.2-0.3$. and CO both carry one oxygen atom and one carbon atom and are therefore not as sensitive to the C/O ratio. The column densities for these molecules for C/O ratios between 0.4 and 1.2 are presented in Fig. [21](#fig:N_dC_O) in Appendix [7.3.3](#app:ratios_C_O).

The step-like behaviour of the CN and abundance is also seen in the azimuthally averaged integrated intensity profiles presented in Fig. [9](#fig:I_dC_O). If the C/O ratio increases from 0.99 to 1.01, the CN and integrated intensities increase by a factor of a few to one order of magnitude and by two orders of magnitude in the gap, respectively. The C/O ratio does change the integrated intensity across the disk, but the locations of the CN and peaks remain around those seen in the data except for a large peak at $300-400$ au seen in . Interestingly, the observed emission falls between that predicted by models with C/O = 0.99 and 1.01, possibly indicating a C/O ratio in the rings that is very close to 1.00.

The HCN emission only shows a double peak profile for the models with C/O = 0.4 and 0.8 as the column density inside the gap increases faster with increasing C/O than that just outside the gap. The model with a C/O of 0.8 matches the intensity in the outer dust ring particularly well whereas in the model with C/O = 0.4 matches the inner ring within a factor of $\sim2$.

The top left panel in Fig. [9](#fig:I_dC_O) presents the azimuthally averaged radial profile of the observed \[C I\] emission in the HD 100546 disk. Unlike the HCN, CN, , and emission, the \[C I\] does not show a double peaked profile at the dust rings. This could partially be due to the small maximum recoverable scale of 2" ($\sim 108$ au in radius), filtering the emission at larger distances. Therefore, the model may overpredict the observed line intensity outside this radius. Inside $\sim108$ au, the fiducial model underpredicts the emission of atomic carbon by an order of magnitude. The only model that recovers the observed \[C I\] intensity up to 150 au is a model with a larger C/O of 1.2.

The effect of the C/O ratio on the NO emission is that the NO peak moves inwards from 300 au to $\sim 40$ au. The high intensity at $\sim 40$ au is due to some additional NO at $z/r = 0.1-0.2$ in the models with C/O $>1$. The intensity in the outer disk decreases with increasing C/O ratio due to the lower abundance.

In summary, increasing the C/O ratio increases the predicted intensity for \[C I\], HCN, CN, , and NO inside 100 au and for NO it decreases the intensity outside 100 au. The observed emission lines are reproduced by different C/O ratios for each molecule. For example, the region inside 150 au is best reproduced by C/O = 1.2 for \[C I\], but this overpredicts the CN and emission by more than an order of magnitude. At the location of the outer dust ring, the cyanides (HCN and CN) and NO are compatible with a C/O ratio of 0.8, but the requires a C/O ratio very close to 1 (0.99 \< C/O \< 1.01).

### Column density and emission line ratios

To eliminate some of the uncertainties of comparing absolute modelled intensities to the observed ones, the column density and line ratios of /, /, CN/HCN, and CN/NO are presented in Appendix. [7.3.3](#app:ratios_C_O). The latter three column density ratios all increase in most disk regions with increasing C/O due to the enhancement of and CN, and the decrease of NO. In particular, the CN/NO ratio outside 100 au and the / in the entire disk are sensitive to small changes in the C/O. Comparing the observed emission line ratios to the modelled ones shows that the C/O needs to be very close to 1.00 as the / ratio for C/O = 0.99 underpredicts the observed value and that of C/O = 1.01 overpredicts the observations. The CN/NO line ratio only traces the C/O ratio for $r>175$ au, and is therefore not a good tracer of the C/O in the disk.

## Background UV

One striking feature that most of the models presented here show is that the CN, , and NO emission are too bright outside the outermost dust ring. This raises the question if the modelled external UV field is too strong as all of these molecules at least partially trace the UV field. The models assume that the external UV field is 1 $G_0$, the mean UV field in the interstellar medium. However, HD 100546 is an isolated star with a tenuous envelope that may result in a lower external UV field (cite: Grady2001).

The effect of a lower UV field on the CN, , and NO column density is presented in Fig. [28](#fig:N_dbgUV). Lowering the background UV field by a factor of ten decreases the CN and column densities by that same factor at $300-400$ au. The NO decreases by a factor of 5 from $200-350$ au. This is also reflected in the azimuthally averaged radial intensity profiles presented in Fig. [10](#fig:I_dbgUV). The shelf of CN and the peak of at 375 au are not visible for the lowered background radiation fields, creating a ring of emission at the location of the outer dust ring. The effect of a lower background UV field on the \[C I\], HCN, and emission is small.

In particular, a lower background UV radiation field more closely reproduces the double peak profile of the emission, with both peaks having a similar intensity. The intensities in these models are a factor of 200 lower than what is observed for C/O = 0.4, thus a lower background UV field better reproduces the morphology of the emission but it does not solve the difference between the intensity seen in the observations and in the models. Additionally, the NO emission in the outer disk is not overpredicted if the background radiation field is lowered. Overall, a lower background UV field seems to improve the comparison with observations outside the outer dust ring.

![](molecules_fid_diff_bgUV_las6.0_incl41.pdf)

![](moment_maps_linear_las6.0_incl41_diff_psi_separate_scalings.png)

## Flaring

The observations of HCN, CN, , and show two emission rings that are concentric around the position of the star. This indicates that these molecules emit from a layer close to the disk midplane ($z/r\leq 0.1$, (cite: Boothinprep)) as an elevated layer would shift these rings w.r.t. the position of the star. Such an offset is indeed seen in the models for CN. Figure [11](#fig:mom0_psi) presents this with the light and dark blue ellipses for different flaring indices of the disk. The ellipses indicate the projected location of the peak CN number density at the inner rim of the outer dust ring. For the two flattest models ($\psi = -0.1$ and 0) the CN at $r=175$ au peaks at $z=55-53$ au whereas for the two more flared models ($\psi = 0.1$ and 0.2), the CN peaks at a height of $66-68$ au at $r=176$ au. These ellipses trace two rings in the CN emission in the moment 0 maps. These two rings increase and move slightly further apart with increasing flaring index, tracing the height where the CN is abundant. As this height only changes by $\sim10$ au between a very flared and a close to flat disk, flaring alone cannot explain the observed emitting heights. However, the emission in the moment 0 map not only depends on the vertical structure but also on the density and temperature. The main difference between the models with $\psi = 0-0.2$ is the expected CN intensity at the location of the blue ellipses at the outer ring. Even though the flared disk model produces an outer ring that has a similar intensity to the inner ring at the major axis, we emphasize that the elevated emitting surface of CN creates projection effects that are not seen in the HD 100546 observations. Observations of in the Elias 2-27 disk show a ring that is close to being centered at the position of the star. Yet the channel maps show that the emitting surface is flared, with $z/r \sim 0.2$ (cite: PanequeCarreno2021). Therefore, deriving the emitting height from integrated intensity maps may hide part of the true vertical structure of the disk. The column density and radial emission profiles for other molecules for different flaring indices are presented in Appendix [7.5](#app:flaring).

# Discussion

Correlations between the radial structures in the dust and gas may point to a common origin such as massive planets carving deep gas gaps in disks. Additionally, such correlations between gas and dust structures can point to the sublimation of ices as seen in the IRS 48 disk (cite: vanderMarel2021irs48; Booth2021irs48; Brunken2022; Leemker2023). The observations in the HD 100546 disk show a clear correlation between the dust rings and the HCN, CN, , and emission suggesting a direct relation between the structures in the gas and the dust. However, the rare CO isotopologue emission, tracing the CO column density, does not show the same double ringed structure. In this work, we use thermochemical models to investigate under what conditions molecular rings are co-spatial with the dust rings and which physical conditions are important for the ring locations.

## Radial structures 

### CO isotopologues, , and HCN

The thermochemical models spanning a range of gas gap depth ($\delta_{\rm gas\ gap} = 1-10^{-5}$) show that two molecules directly respond to a the depletion of gas in the gap: CO isotopologues and . The CO isotopologue emission does not show a deep gap in the observations that is seen in models with a deep gas gap. Therefore, the HD 100546 disk is consistent with a shallow gas gap ($\delta_{\rm gas\ gap} = 10^{-1}$). A clear double ring is seen in model emission if the modelled gas gap is at least two orders of magnitude deep (or one order of magnitude if the disk is viewed face-on due to projection effects, see Fig. [19](#fig:dali_azi_avg_dgap_face-on) in Appendix [7.2.3](#app:molecules_radial)). A weak outer ring is seen in the HCN model predictions. Interestingly, despite the correlations seen in the models, no general correlation is observed in the MAPS sources between the HCN and rings and the dust, and only a weak ($\sim 3\sigma$) correlation is seen between the CO isotopologue emission and the dust (cite: Law2021; Jiang2022).

The trend in the and CO isotopologues across the gas gap is also seen in other modelling works. Modelling of across a gas gap outside the CO snowline predicts that the ratio of the to the total gas column density increases when a gas gap is introduced (cite: Alarcon2020; Smirnov-Pinchukov2020). A difference in the various model predictions is seen for the model with only a dust gap and no gas gap ($\delta_{\rm gas\ gap} =1$). This model presented in (cite: Smirnov-Pinchukov2020) shows an increased /CO column density ratio in the dust gap whereas this is not seen in the models presented in this work (Fig. [23](#fig:Nratios_diff_gaps)). A possible cause for this is that the gap in (cite: Smirnov-Pinchukov2020) is located outside the CO snowline. Part of the CO ice desorbs and reacts to form , boosting the column density in their model. This is not seen in our models as CO is abundant throughout the disk, with only some CO freeze-out in the outer dust ring below a height of $\sim 8$ au, instead of gas-phase CO being abundant only in the dust gap as in the models presented in (cite: Smirnov-Pinchukov2020).

### CN, , and NO

The other modelled molecules follow a more intricate relation with the gas gap depth. For gaps up to approximately three orders of magnitude deep, the CN, , and NO rings peak at various radii both inside (CN, ) and outside (NO) the dust rings and do in general not coincide with the dust rings or each other. Additionally, the inner and outer rings of a particular molecule are predicted to have very different intensities. This is similar to the results of (cite: Cazzoletti2018) and of the MAPS program which observed CN and and found no general and significant correlation between structures in the dust and in the molecular line emission in four out of five disks, despite some overlapping features (cite: Law2021; Jiang2022). The CN/HCN peaks in some of the dust gaps in the disks in the MAPS sample, similar to the model predictions for the HD 100546 disk (cite: Bergner2021). For the models with a gap of $10^{-1}-10^{-3}$, the is predicted to peak inside the dust gap, similar to what is seen in the MWC 480 disk, the only MAPS disk where gas structures other than CO isotopologue emission do correlate with the dust, and in the AS 209 disk (cite: Alarcon2021). The location of the inner CN ring in the models presented in our work (see Fig. [6](#fig:dali_N_dgap)) is only sensitive to gas gap depth if the gap is depleted by five orders of magnitude in gas. Therefore, chemistry is the main driver of the ring locations for shallow gas gaps.

In summary, the radial locations of the rings seen in the HD 100546 disk cannot be explained by a single gas gap depth as the CO isotopologue emission, HCN, and are best reproduced by a shallow gap ($\delta_{\rm gas\ gap} = 10^{-1}-10^{-2}$), whereas the double rings in CN and are only reproduced for a deep gas gap of $\delta_{\rm gas\ gap} = 10^{-4}-10^{-5}$, partially due to the vertical structure of the disk. Unlike HD 100546, the PDS 70 and IRS 48 disks both have a deep gas cavity just inside the molecular rings, forcing the line emission to be co-spatial with that of the dust. Therefore, only if a deep physical gap is present in a disk, for example due to a massive planet, the molecular rings are likely also physical rather than chemical rings.

## Chemistry in the rings and gap

In addition to physical rings in the disk density structure, chemical rings can also affect the observed emission. The chemistry across the gap may vary due to e.g., thermal and non-thermal sublimation of the ice mantles on the dust and UV shielding by small dust grains.

###  tracing a low gas-phase water abundance

The abundance of and gas-phase water anti-correlate in protoplanetary disks as the main destruction pathway of is through gas-phase water (cite: Phillips1992; Bergin1998; Leemker2021). Water ice is likely present on the dust grains in the gap between the two dust rings in the HD 100546 disk (cite: Honda2016). Photodesorption of this water ice could explain the gas-phase water seen from just outside the inner dust ring (starting from $35-40$ au) to $\sim300-400$ au (cite: Du2017; vanDishoeck2021). The outer radius is not well constrained as the *Herschel* HIFI line profile that is used to constrain the emitting location is most sensitive to the inner radius rather than the outer radius (priv. comm. with M. R. Hogerheijde). Additionally, the line profile does not show evidence for a jump in the abundance at the location of the outer dust ring. Modelling of the cold water lines shows that gas-phase water has an abundance of $3\times 10^{-9}$ in the outer disk ($\sim 40-300$ au, (cite: Pirovano2022)). Photodesorption of water ice is not included in the network used to predict the abundance in this work. As is destroyed by gas-phase water, the predicted abundance and emission are thus overestimated in the gas gap and also at larger radii out to 300 au. The difference between the modelled emission in the gap and the observed intensity could thus be arising from this effect. As the gas gap does not contain large grains, water ice must be present on small grains.

Thermal desorption of water is predicted at the water snowline which is located at 15 au, at the outer edge of the gas cavity in the models. The modelled abundance anti-correlates with that of gas-phase water, with a small increase of less than a factor of ten in the abundance in the gap (see Fig. [4](#fig:dali_2D_mol_fid)). The modelled peak location of the emission is 40 au whereas the data shows centrally peaked emission at a spatial resolution of 31 au, indicating that the water snowline is located inside the central beam of the observations. Additionally, (cite: Pirovano2022) found that the abundance of gas-phase water inside the HD 100546 dust cavity is low at $< 10^{-9}$. Therefore, the water snowline in the HD 100546 disk is likely unresolved at the 31 au resolution of the observations and thus located inside 15 au.

### Grain surface chemistry

Another mechanism that could lead to the rings seen in HCN, CN, , and and the detection of NO is grain surface chemistry. The temperature structure of the fiducial model suggests that the outer dust ring is sufficiently cold to have some HCN, CN, , NO, and CO freeze-out (see Fig. [4](#fig:dali_2D_mol_fid)). Non-thermal desorption could somewhat enhance the gas-phase abundance of HCN and NO by $10^{-3}-10^{-4}$ times their ice abundance as both of these molecules have significant ice abundance ($>10^{-7}$) in that region. The high NO abundance in the IRS 48 disk may have an origin in the ice with or HNCO ices as possible parents (cite: Leemker2023). and CN on the other hand do not have a high abundance in the ice and these emission rings thus require a different origin such as gas-phase formation or sublimation of larger molecules that form CN and after sublimation.

![](molecules_fid_diff_C_O_in_rings_bgUV0.1C_O1.01_v2_diff_widths_las6.0_incl41.pdf)

### C/O ratio across the HD 100546 disk

The sublimation of ices could also be reflected in the gas-phase C/O ratio as most ices are oxygen rich. Of the ratios investigated in this work, the / ratio is the most sensitive to the C/O ratio. The CN/NO ratio has been suggested as a tracer of the gas-phase C/O ratio (cite: HilyBlant2010; Daranlot2012; LeGal2014). However, the models presented in this work show that the relation between CN/NO and C/O is more complicated.

Our models suggest that the C/O ratio in the dust rings needs to be elevated from 0.4 to $\sim$0.8-1 to reproduce the HCN, CN, and emission in the dust rings, while the C/O in the gas gap is roughly consistent with the fiducial value of 0.4. The C/O in the rings is a factor of $\sim 2$ higher than the C/O of 0.5 derived from CS and SO by (cite: Keyte2023). In particular, the emission is very sensitive to the C/O ratio, consistent with what is found in earlier works (cite: Bergin2016; Miotello2019; Bosman2021C2H). Additionally, the bright emission without having a deep gas gap points to an elevated C/O as also suggested in the AS 209 disk (cite: Alarcon2021). The emission at the outer dust ring in HD 100546 could be due to freeze-out of oxygen bearing molecules in this region leading to a high C/O ratio (cite: Oberg2011; vanderMarel2021C_O). Interestingly, (cite: Jiang2023) find that the modelled intensity peaks at or inside the ring of a gap carved by an accreting planet due to the sublimation of carbon-rich organic molecules. The rings in the HD 100546 disk are located just outside the dust rings but possibly a migrating planet could still heat the gas in this regions to create a ring in .

Two other mechanisms that could lead to an elevated C/O ratio are the liberation of carbon from ice and grains and destruction of CO by (cite: Bergin2014; Anderson2017; Klarmann2018; Wei2019; Bosman2021C2H). The latter process is included in the chemical network. The dim emission could indicate that the cosmic ray ionisation rate or the X-ray flux are higher than the value of the X-ray flux adopted in this model. A more recent value of the X-ray flux measured by (cite: Skinner2020) is a factor of $\sim 4-$6 higher than the value reported in (cite: Stelzer2006) that is used in this work, however, (cite: Bruderer2012) found that the X-ray flux only affected the CO, \[C I\], \[C II\], and \[O I\] line fluxes by less than $\sim 5$%. For the HCN, CN, , and NO emission, only the inner 100 au is affected by the increased X-ray luminosity and the increased X-ray luminosity does not affect the emission of \[C I\] by much (see Appendix [7.6](#app:Lx)). The largest effect on the emission morphology is seen in the profile, where the increases X-ray flux creates a ring at 30 au, similar to the morphology of the observations. However, the increased X-ray luminosity also increases the emission of CN inside the ring at 40 au that is not seen in the observations.

The spatial overlap between the dust rings and the emission suggests that destruction of carbon grains could contribute to the elevated C/O ratio in the disk surface layers. This could enhance the emission of carbon bearing molecules that tend to be abundant at higher disk layers than NO. Therefore, a vertical gradient in the C/O ratio could help to reproduce the , \[C I\], and NO at the cost of CN and HCN. Instead of an enhancement in the C/H ratio, the O/H ratio could also be suppressed by, for example the freeze-out of oxygen bearing molecules. As the C/H and O/H ratios in the HD 100546 photosphere are consistent with the Solar values, the increase in the C/O ratio in the disk is likely local (cite: Kama2016). Another explanation for the spatial overlap between molecular rings and the outer dust ring could be that the gas in the outer dust ring is second generation gas due to collisions of larger bodies, possibly indicating that the outer dust ring is a debris disk belt in a protoplanetary disk.

### , CN, and HCN tracing radiation and gas gap depth

not only traces the desorption of water, it is also sensitive to the ionization in the disk (cite: Aikawa2001; Cleeves2015twhya). The observed column density ratios of /CO in the MAPS disks increase with radius or stay roughly constant at $\sim 10^{-6}-10^{-4}$ (cite: Aikawa2021). The general trend of an increasing ratio with radius is recovered by our models, but the observed values in MAPS require a gas gap depth of $\sim 10^{-2}-10^{-4}$. Comparing this to the HD 100546 disk shows that either the gas gap is shallow ($\delta_{\rm gas\ gap} = 1-10^{-1}$) for the outer half of the gap, or that the ionisation rate in the modelled gap is too high.

The ratio of CN/HCN, tracing the UV indicates that the gap in HD 100546 needs to be $10^{-1}-10^{-2}$ deep (see Fig. [24](#fig:Iratios_diff_gaps)). Radial variations in the CN/HCN column density ratio likely trace radial variations in the UV field due to changes in the dust density structure due to enhanced HCN photodissociation compared to CN photodissociation (cite: Bergner2021). The models presented in this work show a similar trend where the CN/HCN column density ratio peaks inside the gas gap and decreases in the outer dust ring (see Fig. [23](#fig:Nratios_diff_gaps)). Similarly, this ratio has a low value of a few times $10^{-2}- 10^{-1}$ in the inner dust ring where the small dust surface density is two orders of magnitude higher than that in the outer dust ring where the ratio is close to ten (see Fig. [1](#fig:dali_structure)). This is similar to the observed value of 0.4 in the inner ring and $\sim 2$ in the outer dust ring (cite: Boothinprep). The model without a gap in the gas and small dust grains but with a gap in the large dust grains does not show a peak in the CN/HCN column density ratio in the gap, indicating that this ratio is primarily sensitive to the small dust grains that have a larger opacity in the UV than the large dust grains.

In summary, the rings seen in the HD 100546 disk likely have a chemical origin as the physical rings in the gas density structure alone cannot explain the observed molecular rings. The C/O ratio in the rings needs to be elevated above the fiducial value of 0.4 to reproduce the observed intensity in the , CN, and \[C I\]. In addition, a decreased background UV radiation field is necessary to suppress the outer ring in and NO. Figure [12](#fig:radially_varying_C_O) presents two models with a background UV field attenuated by a factor of 10 and where the C/O ratio is increased to 1.01 in two rings. In the purple model, the C/O ratio is increased across the entire width of the two dust rings ($20-40$ au and $175-250$ au). The molecular rings predicted by this model are wider than what is seen in the HD 100546 disk observations. Therefore, a second model is presented in pink. In this model, the C/O ratio is only increased in two 10 au wide rings from 35 to 45 au and from 215 to 225 au to match the location of the observed emission ring. This model reproduces the double ring seen in HCN, CN, and and the increase in the NO emission towards the position of the star. Additionally, this model does reproduce the intensity of these molecules within a factor of $\sim 5$ and only the \[C I\] is underpredicted by approximately one order of magnitude inside 150 au. The width of the rings with a high C/O ratio may be larger than 10 au as the spatial resolution of the observations is $\sim 0.2\ensuremath{''} - 0.5\ensuremath{''}$, still the purple model shows that these rings cannot be as wide as the dust rings.

# Conclusions

In this paper, we use an exploratory grid of thermochemical models to explore trends in gapped disks, and to reproduce the observed co-spatial rings of mm-dust and molecular emissions in the HD100546 disk (cite: Boothinprep). We used the thermochemical code DALI to explore the radial location and intensity of molecular rings seen in HCN, CN, , NO, and . In particular, we investigated under which conditions these molecular rings overlap with those seen in the continuum. The fiducial model provides a good fit to the continuum emission and the emission of CO isotopologues with a deep dust and gas cavity inside 20 au and 15 au, respectively, and a deep dust gap but a shallow gas gap from $40-175$ au. The abundance of the other molecules of interest, HCN, CN, , and NO are predicted with a dedicated nitrogen network and that of is predicted with the network presented in (cite: Leemker2021). We find that the following trends are predicted for disks in general:

- In general, molecular rings and dust rings do not coincide unless gaps are very deep.

- The modelled emission of CO isotopologues and directly trace the gaps and gap depths in the model gas density structure whereas the other molecules do not.

- The thermochemical model does predict molecular rings in e.g., HCN, CN, , and NO but these generally do not follow the dust rings.

- For gas gaps of one to approximately three orders of magnitude deep, the column density of UV tracers, e.g., CN, , and NO, show only a minor sensitivity to the gas gap depth and are thus not good tracers of this. For very deep gas gaps ($\delta_{\rm gas\ gap} \sim 10^{-4}-10^{-5}$) these molecular rings emit at a similar location as the dust rings.

- A globally elevated C/O ratio mainly affects the total modelled intensity of C- or O-bearing molecules such as \[C I\], HCN, CN, , and NO but not the radial location of the emission rings. However, the CN/NO ratio is not a good tracer of the disk C/O ratio inside 175 au. The modelled CN and column density and emission increase by roughly one to two orders of magnitude, respectively, when the bulk model C/O ratio is increased from 0.99 to 1.01.

- A lower background UV radiation field reduces the predicted intensity and/ or moves the ring seen in UV tracers to smaller radii.

- The flaring index of the disk only has a minor effect on the height of the layer where a high CN abundance is seen, despite models with lower flaring indices being more flat.

In addition, we draw the following conclusions specifically for the HD 100546 disk:

- The dust and CO isotopologue gas emission in the HD 100546 disk are well reproduced by a model with a deep central gas ($r<15$ au) and dust cavity ($r<20$ au) and a deep dust gap but a shallow gas gap ($\delta_{\rm gas\ gap} = 10^{-1}$) from $40-175$ au. A drop in gas density by more than one order of magnitude is excluded by the CO isotopologue data.

- The best-fit C/O for \[C I\], CN, and is an elevated C/O of $\sim 0.8-1.2$. In particular, the requires a C/O ratio very close to 1. The NO emission inside 250 au is reproduced by models with a C/O ratio less than 1.2.

- The models predict emission rings in CN, , and NO at $300-400$ au that are not seen in the observations. A lower background UV radiation field in the models reduces the column density and emission of CN, , and NO and it increases that of HCN in the outer disk ($r> 100$ au) to values close to those observed.

- A radially varying C/O ratio with a C/O ratio of 1.01 in two narrow regions at 40 and 220 au where the observed molecular rings peak, and the fiducial C/O ratio of 0.4 in the other disk regions reproduces the double ringed morphology seen in the HCN, CN, and emission and it roughly reproduces the morphology of the NO. The \[C I\] emission is still underproduced by an order of magnitude.

- To reconcile the observed ring locations and intensities with those predicted by models, a combination of a gas gap with a factor of 10 less gas, a low background UV field and an increased C/O ratio of 1.01 in a region narrower than the dust rings (at 40 and 220 au) are needed.

This work shows that thermochemical models do not predict molecular rings to be co-spatial with those seen in the dust in general. Moreover, these models indicate that if observations show multiple molecular rings that are co-spatial with the dust, the chemical composition in that region is likely different than in the other disk regions. The constraints from modelling multiple molecules across a gas gap provides a first step towards a full picture of the chemical makeup of the planet-forming material. Multi-line observations of multiple molecules at high spatial and spectral resolution and sensitivity are needed to better constrain the layer from which these molecules emit. These observations can then be used to test thermochemical models and derive the chemical composition of the planet-forming material. In particular, observations of \[C I\] in more disks are needed to determine whether the \[C I\] emission is indeed brighter than expected based on thermochemical models or that the difference is specific to the HD 100546 disk.

# Acknowledgements

We thank the referee for the detailed comments. The authors would like to thank Luke Keyte and Dylan T. Natoewal for the useful discussions on the DALI modelling. In addition, Michiel Hogerheijde is thanked for the discussion on water in the HD 100546 disk. This work is supported by grant 618.000.001 from the Dutch Research Council (NWO). Astrochemistry in Leiden is supported by funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101019751 MOLDISK), by the Netherlands Research School for Astronomy (NOVA).

This paper makes use of the following ALMA projects: 2011.0.00863.S, 2015.1.00806.S, 2016.1.00344.S, 2018.1.00141.S, 2021.1.00738.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

156 natexlab

(ref: Agundez2010) Agúndez, M., Goicoechea, J. R., Cernicharo, J., Faure, A., & Roueff, E. 2010, ApJ, 713, 662

(ref: Aikawa2021) Aikawa, Y., Cataldi, G., Yamato, Y., et al. 2021, ApJS, 257, 13

(ref: Aikawa2001) Aikawa, Y. & Herbst, E. 2001, A&A, 371, 1107

(ref: Alarcon2022) Alarcón, F., Bergin, E. A., & Teague, R. 2022, ApJL, 941, L24

(ref: Alarcon2021) Alarcón, F., Bosman, A. D., Bergin, E. A., et al. 2021, ApJS, 257, 8

(ref: Alarcon2020) Alarcón, F., Teague, R., Zhang, K., Bergin, E. A., & Barraza-Alfaro, M. 2020, ApJ, 905, 68

(ref: Anderson2017) Anderson, D. E., Bergin, E. A., Blake, G. A., et al. 2017, ApJ, 845, 13

(ref: Andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: Andrews2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42

(ref: Arun2019) Arun, R., Mathew, B., Manoj, P., et al. 2019, AJ, 157, 159

(ref: Ben2021) Ben Khalifa, M. & Loreau, J. 2021, MNRAS, 508, 1908

(ref: Benisty2021) Benisty, M., Bae, J., Facchini, S., et al. 2021, ApJL, 916, L2

(ref: Benisty2010) Benisty, M., Tatulli, E., Ménard, F., & Swain, M. R. 2010, A&A, 511, A75

(ref: Bergin2014) Bergin, E. A., Cleeves, L. I., Crockett, N., & Blake, G. A. 2014, Faraday Discussions, 168, 61

(ref: Bergin2016) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101

(ref: Bergin1998) Bergin, E. A., Melnick, G. J., & Neufeld, D. A. 1998, ApJ, 499, 777

(ref: Bergner2019) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2019, ApJ, 876, 25

(ref: Bergner2021) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, ApJS, 257, 11

(ref: Binkert2021) Binkert, F., Szulágyi, J., & Birnstiel, T. 2021, MNRAS, 506, 5969

(ref: Booth2023) Booth, A. S., Ilee, J. D., Walsh, C., et al. 2023, A&A, 669, A53

(ref: Boothinprep) Booth, A. S., Leemker, M., van Dishoeck, E. F., et al. 2024, arXiv e-prints, arXiv:2402.04001

(ref: Booth2021irs48) Booth, A. S., van der Marel, N., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021a, A&A, 651, L6

(ref: Booth2021hd) Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., et al. 2021b, Nature Astronomy, 5, 684

(ref: Bosman2021C2H) Bosman, A. D., Alarcón, F., Zhang, K., & Bergin, E. A. 2021, ApJ, 910, 3

(ref: Brittain2014) Brittain, S. D., Carr, J. S., Najita, J. R., Quanz, S. P., & Meyer, M. R. 2014, ApJ, 791, 136

(ref: Brittain2019) Brittain, S. D., Najita, J. R., & Carr, J. S. 2019, ApJ, 883, 37

(ref: Brittain2013) Brittain, S. D., Najita, J. R., Carr, J. S., et al. 2013, ApJ, 767, 159

(ref: Broome2023) Broome, M., Kama, M., Booth, R., & Shorttle, O. 2023, MNRAS, 522, 3378

(ref: Bruderer2013) Bruderer, S. 2013, A&A, 559, A46

(ref: Bruderer2009) Bruderer, S., Doty, S. D., & Benz, A. O. 2009, ApJS, 183, 179

(ref: Bruderer2014) Bruderer, S., van der Marel, N., van Dishoeck, E. F., & van Kempen, T. A. 2014, A&A, 562, A26

(ref: Bruderer2012) Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A, 541, A91

(ref: Brunken2022) Brunken, N. G. C., Booth, A. S., Leemker, M., et al. 2022, A&A, 659, A29

(ref: Cazzoletti2018) Cazzoletti, P., van Dishoeck, E. F., Visser, R., Facchini, S., & Bruderer, S. 2018, A&A, 609, A93

(ref: Cleeves2014) Cleeves, L. I., Bergin, E. A., & Adams, F. C. 2014, ApJ, 794, 123

(ref: Cleeves2011) Cleeves, L. I., Bergin, E. A., Bethell, T. J., et al. 2011, ApJL, 743, L2

(ref: Cleeves2015twhya) Cleeves, L. I., Bergin, E. A., Qi, C., Adams, F. C., & Öberg, K. I. 2015, ApJ, 799, 204

(ref: Cridland2023) Cridland, A. J., Facchini, S., van Dishoeck, E. F., & Benisty, M. 2023, A&A, 674, A211

(ref: Cridland2016) Cridland, A. J., Pudritz, R. E., & Alessi, M. 2016, MNRAS, 461, 3274

(ref: Cridland2017) Cridland, A. J., Pudritz, R. E., Birnstiel, T., Cleeves, L. I., & Bergin, E. A. 2017, MNRAS, 469, 3910

(ref: Currie2017) Currie, T., Brittain, S., Grady, C. A., Kenyon, S. J., & Muto, T. 2017, Research Notes of the American Astronomical Society, 1, 40

(ref: Currie2015) Currie, T., Cloutier, R., Brittain, S., et al. 2015, ApJL, 814, L27

(ref: Currie2022) Currie, T., Lawson, K., Schneider, G., et al. 2022, Nature Astronomy, 6, 751

(ref: Currie2014) Currie, T., Muto, T., Kudo, T., et al. 2014, ApJL, 796, L30

(ref: Daranlot2012) Daranlot, J., Hincelin, U., Bergeat, A., et al. 2012, Proceedings of the National Academy of Science, 109, 10233

(ref: Denis2020) Denis-Alpizar, O., Stoecklin, T., Dutrey, A., & Guilloteau, S. 2020, MNRAS, 497, 4276

(ref: Dong2015) Dong, R., Zhu, Z., & Whitney, B. 2015, ApJ, 809, 93

(ref: Du2017) Du, F., Bergin, E. A., Hogerheijde, M., et al. 2017, ApJ, 842, 98

(ref: Dullemond2001) Dullemond, C. P., Dominik, C., & Natta, A. 2001, ApJ, 560, 957

(ref: Dumouchel2010) Dumouchel, F., Faure, A., & Lique, F. 2010, MNRAS, 406, 2488

(ref: Eistrup2023) Eistrup, C. 2023, ACS Earth and Space Chemistry, 7, 260

(ref: Facchini2017) Facchini, S., Birnstiel, T., Bruderer, S., & van Dishoeck, E. F. 2017, A&A, 605, A16

(ref: Facchini2018) Facchini, S., Pinilla, P., van Dishoeck, E. F., & de Juan Ovelar, M. 2018, A&A, 612, A104

(ref: Facchini2021) Facchini, S., Teague, R., Bae, J., et al. 2021, AJ, 162, 99

(ref: Fedele2021) Fedele, D., Toci, C., Maud, L., & Lodato, G. 2021, A&A, 651, A90

(ref: Fedele2016) Fedele, D., van Dishoeck, E. F., Kama, M., Bruderer, S., & Hogerheijde, M. R. 2016, A&A, 591, A95

(ref: Fillion2022) Fillion, J.-H., Dupuy, R., Féraud, G., et al. 2022, ACS Earth and Space Chemistry, 6, 100

(ref: Follette2017) Follette, K. B., Rameau, J., Dong, R., et al. 2017, AJ, 153, 264

(ref: Francis2020) Francis, L. & van der Marel, N. 2020, ApJ, 892, 111

(ref: Gaia2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1

(ref: GaiaDR3) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Garufi2016) Garufi, A., Quanz, S. P., Schmid, H. M., et al. 2016, A&A, 588, A8

(ref: GonzalezDiaz2019) González Dı́az, C., Carrascosa de Lucas, H., Aparicio, S., et al. 2019, MNRAS, 486, 5519

(ref: Grady2001) Grady, C. A., Polomski, E. F., Henning, T., et al. 2001, AJ, 122, 3396

(ref: Haffert2019) Haffert, S. Y., Bohn, A. J., de Boer, J., et al. 2019, Nature Astronomy, 3, 749

(ref: Hammond2023) Hammond, I., Christiaens, V., Price, D. J., et al. 2023, MNRAS, 522, L51

(ref: Hartmann1998) Hartmann, L., Calvet, N., Gullbring, E., & D’Alessio, P. 1998, ApJ, 495, 385

(ref: Heays2017) Heays, A. N., Bosman, A. D., & van Dishoeck, E. F. 2017, A&A, 602, A105

(ref: HilyBlant2010) Hily-Blant, P., Walmsley, M., Pineau Des Forêts, G., & Flower, D. 2010, A&A, 513, A41

(ref: Honda2016) Honda, M., Kudo, T., Takatsuki, S., et al. 2016, ApJ, 821, 2

(ref: Huang2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42

(ref: Izquierdo2022) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2

(ref: Izquierdo2023) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113

(ref: Jiang2023) Jiang, H., Wang, Y., Ormel, C. W., Krijt, S., & Dong, R. 2023, A&A, 678, A33

(ref: Jiang2022) Jiang, H., Zhu, W., & Ormel, C. W. 2022, ApJL, 924, L31

(ref: Johnson1987) Johnson, C. T., Burke, P. G., & Kingston, A. E. 1987, Journal of Physics B Atomic Molecular Physics, 20, 2553

(ref: Kama2016) Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 592, A83

(ref: Keppler2018) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44

(ref: Keyte2023) Keyte, L., Kama, M., Booth, A. S., et al. 2023, arXiv e-prints, arXiv:2303.08927

(ref: Klarmann2018) Klarmann, L., Ormel, C. W., & Dominik, C. 2018, A&A, 618, L1

(ref: Launay1977) Launay, J. M. & Roueff, E. 1977, A&A, 56, 289

(ref: Law2022) Law, C. J., Crystian, S., Teague, R., et al. 2022, ApJ, 932, 114

(ref: Law2021) Law, C. J., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 3

(ref: Law2023) Law, C. J., Teague, R., Öberg, K. I., et al. 2023, ApJ, 948, 60

(ref: LeGal2014) Le Gal, R., Hily-Blant, P., Faure, A., et al. 2014, A&A, 562, A83

(ref: Leemker2022) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2022, A&A, 663, A23

(ref: Leemker2023) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2023, A&A, 673, A7

(ref: Leemker2021) Leemker, M., van’t Hoff, M. L. R., Trapman, L., et al. 2021, A&A, 646, A3

(ref: Lique2010) Lique, F., Spielfiedel, A., Feautrier, N., et al. 2010, , 132, 024303

(ref: Long2021) Long, F., Bosman, A. D., Cazzoletti, P., et al. 2021, A&A, 647, A118

(ref: Long2018) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17

(ref: LyndenBell1974) Lynden-Bell, D. & Pringle, J. E. 1974, MNRAS, 168, 603

(ref: Mathis1977) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miotello2019) Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019, A&A, 631, A69

(ref: Miotello2016) Miotello, A., van Dishoeck, E. F., Kama, M., & Bruderer, S. 2016, A&A, 594, A85

(ref: Mordasini2016) Mordasini, C., van Boekel, R., Mollière, P., Henning, T., & Benneke, B. 2016, ApJ, 832, 41

(ref: Norfolk2022) Norfolk, B. J., Pinte, C., Calcino, J., et al. 2022, ApJL, 936, L4

(ref: Oberg2016) Öberg, K. I. & Bergin, E. A. 2016, ApJL, 831, L19

(ref: Oberg2007) Öberg, K. I., Fuchs, G. W., Awad, Z., et al. 2007, ApJL, 662, L23

(ref: Oberg2021m) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1

(ref: Oberg2009) Öberg, K. I., Linnartz, H., Visser, R., & van Dishoeck, E. F. 2009, ApJ, 693, 1209

(ref: Oberg2011) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, ApJL, 743, L16

(ref: Paardekooper2016) Paardekooper, D. M., Fedoseev, G., Riedo, A., & Linnartz, H. 2016, A&A, 596, A72

(ref: PanequeCarreno2022) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2022, A&A, 666, A168

(ref: PanequeCarreno2023) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126

(ref: PanequeCarreno2021) Paneque-Carreño, T., Pérez, L. M., Benisty, M., et al. 2021, ApJ, 914, 88

(ref: Perez2020) Pérez, S., Casassus, S., Hales, A., et al. 2020, ApJL, 889, L24

(ref: Perez2015) Perez, S., Casassus, S., Ménard, F., et al. 2015, ApJ, 798, 85

(ref: Phillips1992) Phillips, T. G., van Dishoeck, E. F., & Keene, J. 1992, ApJ, 399, 533

(ref: Pickles1998) Pickles, A. J. 1998, PASP, 110, 863

(ref: Pineda2019) Pineda, J. E., Szulágyi, J., Quanz, S. P., et al. 2019, ApJ, 871, 48

(ref: Pinilla2015) Pinilla, P., Birnstiel, T., & Walsh, C. 2015, A&A, 580, A105

(ref: Pinte2018) Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJL, 860, L13

(ref: Pinte2019) Pinte, C., van der Plas, G., Ménard, F., et al. 2019, Nature Astronomy, 3, 1109

(ref: Pirovano2022) Pirovano, L. M., Fedele, D., van Dishoeck, E. F., et al. 2022, A&A, 665, A45

(ref: Pyerin2021) Pyerin, M. A., Delage, T. N., Kurtovic, N. T., et al. 2021, A&A, 656, A150

(ref: Qi2019) Qi, C., Öberg, K. I., Espaillat, C. C., et al. 2019, ApJ, 882, 160

(ref: Qi2013) Qi, C., Öberg, K. I., Wilner, D. J., et al. 2013, Science, 341, 630

(ref: Quanz2013) Quanz, S. P., Amara, A., Meyer, M. R., et al. 2013, ApJL, 766, L1

(ref: Rab2020) Rab, C., Kamp, I., Dominik, C., et al. 2020, A&A, 642, A165

(ref: Rameau2017) Rameau, J., Follette, K. B., Pueyo, L., et al. 2017, AJ, 153, 244

(ref: Rosotti2016) Rosotti, G. P., Juhasz, A., Booth, R. A., & Clarke, C. J. 2016, MNRAS, 459, 2790

(ref: Roueff1990) Roueff, E. & Le Bourlot, J. 1990, A&A, 236, 515

(ref: Schoier2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: Schroder1991) Schroder, K., Staemmler, V., Smith, M. D., Flower, D. R., & Jaquet, R. 1991, Journal of Physics B Atomic Molecular Physics, 24, 2487

(ref: Schwarz2014) Schwarz, K. R. & Bergin, E. A. 2014, ApJ, 797, 113

(ref: Sissa2018) Sissa, E., Gratton, R., Garufi, A., et al. 2018, A&A, 619, A160

(ref: Skinner2020) Skinner, S. L. & Güdel, M. 2020, ApJ, 888, 15

(ref: Smirnov-Pinchukov2020) Smirnov-Pinchukov, G. V., Semenov, D. A., Akimkin, V. V., & Henning, T. 2020, A&A, 644, A4

(ref: Spielfiedel2012) Spielfiedel, A., Feautrier, N., Najar, F., et al. 2012, MNRAS, 421, 1891

(ref: Staemmler1991) Staemmler, V. & Flower, D. R. 1991, Journal of Physics B Atomic Molecular Physics, 24, 2343

(ref: Stapperinprep) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., et al. 2024, A&A, 682, A149

(ref: Stapper2023) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., & Paneque-Carreño, T. 2023, A&A, 669, A158

(ref: Stelzer2006) Stelzer, B., Micela, G., Hamaguchi, K., & Schmitt, J. H. M. M. 2006, A&A, 457, 223

(ref: Sturm2023) Sturm, J. A., Booth, A. S., McClure, M. K., Leemker, M., & van Dishoeck, E. F. 2023, A&A, 670, A12

(ref: Teague2018) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018, ApJL, 860, L12

(ref: Temmink2023) Temmink, M., Booth, A. S., van der Marel, N., & van Dishoeck, E. F. 2023, A&A, 675, A131

(ref: Thi2010) Thi, W. F., Mathews, G., Ménard, F., et al. 2010, A&A, 518, L125

(ref: vanderMarel2021irs48) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021a, A&A, 651, L5

(ref: vanderMarel2021C_O) van der Marel, N., Bosman, A. D., Krijt, S., Mulders, G. D., & Bergner, J. B. 2021b, A&A, 653, L9

(ref: vanderMarel2016) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585, A58

(ref: vanDishoeck2021) van Dishoeck, E. F., Kristensen, L. E., Mottram, J. C., et al. 2021, A&A, 648, A24

(ref: vantHoff2017) van ’t Hoff, M. L. R., Walsh, C., Kama, M., Facchini, S., & van Dishoeck, E. F. 2017, A&A, 599, A101

(ref: Villenave2020) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164

(ref: Visser2018) Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75

(ref: Walsh2014) Walsh, C., Juhász, A., Pinilla, P., et al. 2014, ApJL, 791, L6

(ref: Walsh2015) Walsh, C., Nomura, H., & van Dishoeck, E. 2015, A&A, 582, A88

(ref: Wei2019) Wei, C.-E., Nomura, H., Lee, J.-E., et al. 2019, ApJ, 870, 129

(ref: Wilson1994) Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191

(ref: Wolfer2023) Wölfer, L., Facchini, S., van der Marel, N., et al. 2023, A&A, 670, A154

(ref: Yang2010) Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C. 2010, ApJ, 718, 1062

(ref: Zhang2021) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5

(ref: Zhou2023) Zhou, Y., Bowler, B. P., Yang, H., et al. 2023, arXiv e-prints, arXiv:2308.16223

(ref: Zhu2014) Zhu, Z., Stone, J. M., Rafikov, R. R., & Bai, X.-n. 2014, ApJ, 785, 122

# Observed lines

The integrated intensity map and the spectrum of the \[C I\] emission in the HD 100546 disk is presented in Fig. [13](#fig:CI_obs). An overview of the observations used in this work is presented in Table [\[tab:trans\]](#tab:trans). In addition to the observations, the critical density for each line is listed as some molecules are found to emit from elevated disk layers below the critical density.

| Molecule | Transition | beam | $n_{\rm crit} (50~\text{K})$ | ref. |
|:---|:--:|:--:|:--:|:--:|
| continuum | 0.9 mm (high res.) | $0.05\ensuremath{''}\times 0.03\ensuremath{''}\ (34\degree)$ |  | 1 |
| continuum | 0.9 mm (moderate res.) | $0.38\ensuremath{''}\times 0.30\ensuremath{''}\ (31\degree)$ |  | 2 |
|  | $J=2-1$ | $0.097\ensuremath{''}\times 0.077\ensuremath{''}\ (-16\degree)$ | $2.7\times 10^3$ | 3 |
|  | $J=3-2$ | $0.35\ensuremath{''}\times 0.23\ensuremath{''}\ (60\degree)$ | $9.2\times 10^3$ | 2 |
|  | $J=7-6$ | $0.23\ensuremath{''}\times 0.17\ensuremath{''}\ (30\degree)$ | $1.2\times 10^5$ | 4 |
|  | $J=2-1$ | $0.098\ensuremath{''}\times 0.077\ensuremath{''}\ (-15\degree)$ | $2.3\times 10^3$ | 3 |
|  | $J=2-1$ | $0.097\ensuremath{''}\times 0.076\ensuremath{''}\ (-13\degree)$ | $2.3\times 10^3$ | 3 |
|  | $J=3-2$ | $0.39\ensuremath{''}\times 0.31\ensuremath{''}\ (29\degree)$ | $8.5\times 10^3$ | 2 |
|  | $^3P_2-^3P_1$ | $0.21\ensuremath{''}\times 0.16\ensuremath{''}\ (28\degree)$ | $1.4\times 10^3$ | 5 |
| HCN | $J=4-3$ | $0.34\ensuremath{''}\times 0.23\ensuremath{''}\ (60\degree)$ | $1.4\times 10^7$ | 2 |
| CN | $3_{0, 7/2, 7/2} - 2_{0, 5/2, 5/2}$ | $0.38\ensuremath{''}\times 0.30\ensuremath{''}\ (29\degree)$ | $3.8\times 10^6$ | 2 |
| CN | $3_{0, 7/2, 9/2} - 2_{0, 5/2, 7/2}$ | $0.38\ensuremath{''}\times 0.30\ensuremath{''}\ (29\degree)$ | $3.8\times 10^6$ | 2 |
| CN | $3_{0, 7/2, 5/2} - 2_{0, 5/2, 3/2}$ | $0.38\ensuremath{''}\times 0.30\ensuremath{''}\ (29\degree)$ | $3.8\times 10^6$ | 2 |
| $^{(a)}$ | $4_{9/2, 5} - 3_{7/2, 4}$ | $0.37\ensuremath{''}\times 0.30\ensuremath{''}\ (27\degree)$ | $1.3\times 10^6$ | 2 |
| $^{(a)}$ | $4_{9/2, 4} - 3_{7/2, 3}$ | $0.37\ensuremath{''}\times 0.30\ensuremath{''}\ (27\degree)$ | $1.2\times 10^6$ | 2 |
| NO$^{(a)}$ | $4_{1, 7/2, 9/2} - 3_{-1, 5/2, 7/2}$ | $0.47\ensuremath{''}\times 0.37\ensuremath{''}\ (31\degree)$ | $2.7\times 10^4$ | 2 |
| NO$^{(a)}$ | $4_{1, 7/2, 7/2} - 3_{-1, 5/2, 5/2}$ | $0.47\ensuremath{''}\times 0.37\ensuremath{''}\ (31\degree)$ | $2.4\times 10^4$ | 2 |
| NO$^{(a)}$ | $4_{1, 7/2, 5/2} - 3_{-1, 5/2, 3/2}$ | $0.47\ensuremath{''}\times 0.37\ensuremath{''}\ (31\degree)$ | $2.4\times 10^4$ | 2 |
|  | $J=4-3$ | $0.34\ensuremath{''}\times 0.23\ensuremath{''}\ (60\degree)$ | $2.6\times 10^6$ | 2 |

Table notes: $^{(a)}$ All components of a single molecule are added together assuming the emission is optically thin. The critical densities are calculated assuming that the main collision partner is . References: 1. (cite: Pineda2019), 2. (cite: Boothinprep), 3. (cite: Perez2020) and Wölfer et al. subm., 4. Wölfer et al. subm., 5. This work.

![](moment_map_CI_linear_keep)

![](Spectrum_CI_linear)

# DALI

## Model setup

### Radial and vertical structure

Radially, the gas density follows the solution for a viscously evolving disk model (cite: LyndenBell1974; Hartmann1998; Andrews2011): $$\begin{align}
\Sigma_{\rm gas\ full} &= \Sigma_{\rm c} \left ( \frac{r}{r_{\rm c}} \right )^{-\gamma} e^{-(r/r_{\rm c})^{2-\gamma}},
\end{align}$$ with $\Sigma_{\rm gas\ full}$ the gas surface density of a full disk, $\Sigma_{\rm c}/e$ the gas surface density at the characteristic radius $r_{\rm c}$, $r$ the radius, and $\gamma$ the power law index of the surface density profile. The surface density is defined from the sublimation radius $r_{\rm subl}$ to the outer radius of the disk $r_{\rm out,\ disk}$. Assuming a typical dust sublimation temperature of 1500 K, the sublimation radius is located at $\sim 0.07~\mathrm{au} \times \sqrt{L/L_{\odot}}$, with $L$ the luminosity of the central star (cite: Dullemond2001). For the 36 L$_{\odot}$ HD 100546, this corresponds to 0.4 au.

Vertically, we assume that the gas follows a Gaussian distribution with the scale height $h$ given by $$\begin{align}
h = h_{\rm c} \left (\frac{r}{r_{\rm c}} \right )^{\psi}, \label{eq:flaring}
\end{align}$$ with $h_{\rm c}$ the scale height at $r_{\rm c}$ and $\psi$ the flaring index.

![](Dali_structure_compare_to_literature_lin.pdf)

The dust in DALI is modeled using a small dust population and a large dust population. Both populations have a minimum grain size of 5 nm but the small grains have a maximum size of 1 $\mu$m, whereas the large grains go up to 1 mm. An MRN distribution with an index of -3.5 is used to set the grain sizes $a$ within these populations (cite: Mathis1977). Furthermore, the mass ratio of the large grain population compared to that of the small grains is set by $f_{\rm ls}$ such that the small and large dust in a full disk follow: $$\begin{align}
\Sigma_{\rm s\ dust\ full} &= \frac{(1-f_{\rm ls}) \Sigma_{\rm gas\ full}}{\Delta_{\rm gd}}\\
\Sigma_{\rm l\ dust\ full} &= \frac{f_{\rm ls} \Sigma_{\rm gas\ full}}{\Delta_{\rm gd}},
\end{align}$$ with $\Delta_{\rm gd}$ the global gas-to-dust mass ratio. A comparison of the radial structure used in this work to those used by (cite: Pirovano2022) and (cite: Keyte2023) is presented in Fig. [14](#fig:dali_structure_lit).

Edge-on disks show that the large dust is settled to the disk midplane (cite: Villenave2020). Therefore, the vertical scale height of the large dust is reduced by a settling parameter $\chi$. Thus, the small and large dust are not following the same radial and vertical distributions and the average grain size is calculated per cell, which is used for further calculations.

### Initial conditions of the chemical networks

The chemical networks are started using mostly molecular initial conditions. Initially, all volatile carbon is locked up in CO and all remaining oxygen is locked up in such that the total (gas $+$ ice) C/O ratio is 0.4. In the case of a C/O ratio larger than 1, all oxygen is initialized in the form of CO and the remaining carbon is put in as . The precise initial partition of nitrogen over N, , and in protoplanetary disks is unknown, therefore we rescale the predictions of dark cloud models at 0.3 Myr (cite: Walsh2015). Finally, hydrogen is mainly in when the model is initialised. An overview of the initial conditions is presented in Table [\[tab:dali\]](#tab:dali). The chemistry is evolved to the age of the HD 100546 disk of 5 Myr (cite: Arun2019) and a cosmic ray ionisation rate consistent with that found in other protoplanetary disks of $10^{-18}$ s$^{-1}$ is adopted (cite: Aikawa2021).

p0.6\>p0.4p0.9 Model parameter & value & Description *Physical structure* & & $r_{\mathrm{subl}} - r_{\mathrm{dust\ cav\ in}}$ & $0.4-1$ au & dusty inner disk $\delta_{\rm gas\ cav}, \delta_{\rm s\ dust,\ in}, \delta_{\rm l\ dust,\ in}$ & $10^{-5}, 10^{-2}, 10^{-2}$ & surface density drop for $r_{\mathrm{subl}} < r < r_{\mathrm{cav\ in,\ dust}}$ $r_{\mathrm{dust\ cav\ in}} - r_{\mathrm{gas\ cav\ out}}$ & $1-15$ au & gas cavity $\delta_{\rm gas\ cav}, \delta_{\rm s\ dust\ cav}, \delta_{\rm l\ dust\ cav}$ & $10^{-5}, 10^{-10}, 10^{-10}$ & surface density drop for $r_{\mathrm{dust\ cav\ in}} < r < r_{\mathrm{gas\ cav\ out}}$ $r_{\mathrm{gas\ cav\ out}} - r_{\mathrm{dust\ cav\ out}}$ & $15-20$ au & region outside gas cavity but inside dust cavity $\delta_{\rm gas\ cav\ edge}, \delta_{\rm s\ dust\ cav\ edge}, \delta_{\rm l\ dust\ cav\ edge}$ & $10^{-2}, 10^{-2}, 10^{-10}$ & surface density drop for $r_{\mathrm{gas\ cav\ out}} < r < r_{\mathrm{dust\ cav\ out}}$ $r_{\mathrm{gap\ in}}-r_{\mathrm{gap\ out}}$ & $40-175$ au & gap $\delta_{\mathrm{gas\ gap}}, \delta_{\mathrm{s\ dust\ gap}}, \delta_{\mathrm{l\ dust\ gap}}$ & $10^{-1}, 10^{-1}, 10^{-10}$ & surface density drop for $r_{\mathrm{gap\ in}} < r < r_{\mathrm{gap\ out}}$ $r_{\rm l\ dust\ out}-r_{\rm out}$ & $250-1000$ au & disk region outside the second ring $\delta_{\rm gas\ out}, \delta_{\rm s\ dust\ out}, \delta_{\rm l\ dust\ out}$ & $1, 1, 10^{-10}$ & surface density drop for $r_{\rm l\ dust\ out} < r < r_{\rm out}$ $r_{\mathrm{c}}$ & 30 au & Characteristic radius of the surface density profile $\Sigma_{\mathrm{c}}$ & 250 g cm$^{-2}$ & Sets the gas surface density at the characteristic radius $r_{\mathrm{c}}$ $M_{\mathrm{disk}}$ & $5\times 10^{-2}$ M$_{\odot}$ & Mass of the disk $\gamma$ & 1.1 & Power law index of the surface density profile $h_{\mathrm{c}}$ & 0.1 & Scale height angle at the characteristic radius $r_{\mathrm{c}}$ $\psi$ & 0 & Flaring index of the disk surface density PAH abundance & 0.1 & Gas-phase abundance of PAHs w.r.t. to ISM value *Dust properties* & & $\chi$ & 0.2 & Settling of large grains $f_{\mathrm{ls}}$ & 0.85 & Mass-fraction of grains that is large $\Delta_{\mathrm{gas/ dust}}$ & 100 & Gas-to-dust mass ratio *Stellar properties* & & $M_{\star}$ & 2.5 $M_{\odot}$ & Mass of the central star $L_{\star}$ & 36 $L_{\odot}$ & Luminosity of the central star $L_{\mathrm{X}}$ & $7.9\times 10^{28}$ erg s$^{-1}$ & X-ray luminosity of the central star $T_{\mathrm{X}}$ & $7\times 10^7$ K & Effective temperature of the X-ray radiation $\zeta_{\mathrm{c.r.}}$ & $1\times 10^{-18}$ s$^{-1}$ & Cosmic ray ionization rate & $i$ & 41$\degree$ & Disk inclination ($0\degree$ is face-on) $d$ & 108.1 pc & Distance to the star *Chemistry*$^{(1)}$ && H & $5.2\times 10^{-5}$ & He & $1.4\times 10^{-1}$& N & $3.0\times 10^{-5}$ & & $5.0\times 10^{-1}$ & & $1.9\times 10^{-4}$ & & $1.3\times 10^{-4}$ & & $1.2\times 10^{-5}$ & & $8.1\times 10^{-6}$ & & $1.0\times 10^{-11}$ & & $1.0\times 10^{-11}$ & & $1.0\times 10^{-11}$ & & $1.0\times 10^{-11}$ & $t_{\mathrm{end}}$ & 5 Myr &

Table notes: $^{(1)}$ Abundance w.r.t. the total number of hydrogen atoms. All molecules start as gas-phase species.

## Model predictions

### Outer ring in and models

The fiducial model predicts a ring in the $J=2-1$ transition at $\sim200$ au and a weak ring is also seen in the $J=3-2$ line. This is due to the low column density just inside the dust ring at $150-175$ au. In this region the column density of the CO isotopologues drops below the minimum column density needed to make self-shielding effective. Therefore, and are effectively destroyed in this region. At the outer dust ring, the gas column density increases by an order of magnitude, increasing the and column densities. The and column densities at 175 au are similar to the respective column densities at 150 au, just before self-shielding becomes efficient. Therefore, the and intensity in the outer dust ring is very sensitive to the gas column density in this region.

![](Col_dens_CO_isos.png)

### Emission profiles and emitting heights of CO isotopologues

The azimuthally averaged radial profiles of the CO isotopologue emission are presented in Fig. [16](#fig:dali_dgas_gap). The models with a drop in gas density and small dust density of 1 (no drop) up to $10^{-5}$ are shown in the same figure with the colored lines. The model without a drop in the gas and small dust density overpredicts the and emission that are the most optically thin and thus the most sensitive to the gas column density. On the other hand, the models with a deeper gap ($10^{-2}$, $10^{-3}$) than the fiducial model ($10^{-1}$), underpredict the and emission in the gap. Additionally, these models show a clear gap in the brighter and lines that is not seen in the observations. This cannot be due to the limited spatial resolution of the observations as the gas gap is fully resolved with 4 beams across the gas gap for , the lowest spatial resolution line in this work, and 14 for which has the highest spatial resolution. Outside the gas gap, at the outer dust ring, the emission is overpredicted. However, a lower gas and thus CO isotopologue column density lowers the column density in the gas gap to a value below its minimum value to self-shield. Therefore, a model that fits the in that region will not reproduce the shelf in . Therefore, the CO isotopologue observations show that the gas density is depleted by at most a factor of $10^{-1}$ between the two dust rings under the assumption that the gas and dust gap have the same widths.

![](dust_and_CO_diff_gap_sdust_follows_gas.pdf)

![](emitting_heights.pdf)

The emitting heights of the $J=2-1$ and $J=7-6$ transitions together with that of the $J=2-1$ transition are presented in Fig. [17](#fig:emitting_heights). These emitting heights are derived using the ALFAHOR package by masking the individual channels after visually inspecting the data (cite: PanequeCarreno2023). Wölfer et al. subm. found evidence for an asymmetry in the vertical structure between the blue and red shifted sides of this disk. As the DALI models used in this work are azimuthally symmetric, the observed emitting heights are presented as an average of both disk sides.

The fiducial model roughly reproduces the observed emitting height of the $J=2-1$ and $J=7-6$ transitions within the scatter for a radius up to 150 au, as expected with the $\sim 10$ au scatter in the $J=2-1$ emitting surface. Still, emitting surfaces of and in the IM Lup, HD 163296, and the MWC 480 disks generally follow the same vertical modulations in the derived emitting layer as are seen in the layer despite the large scatter. Therefore, the derived $J=2-1$ surface in the HD 100546 disk is robust. The lack of vertical segregation between different transitions of one molecule is seen in other DALI models as well (Paneque-Carreño in prep.) and the emitting height of the $J=2-1$ transition observed in the HD 100546 disk is similar to that observed in other disks (cite: Law2022; Law2023; Stapper2023). Finally, the emission is seen very close to the disk midplane at a height of only a few au in the observations. The model reproduces the trend that the emission comes from deeper disk layers than the , and is consistent within $\sim 2\sigma$ from the observations up to 150 au.

### Emission profiles and column densities of \[C I\], HCN, CN, , NO, and for different gas gaps

The azimuthally averaged radial profiles for the HCN, CN, , NO, and moment 0 maps presented in Fig. [5](#fig:mom0_fid) are presented in Fig. [18](#fig:dali_azi_avg_dgap). Instead of the emission, the profile for the atomic carbon line is presented in the top left corner. The colored lines indicate the models for different gas gap depths between the two dust rings, identical to those in e.g. Fig. [16](#fig:dali_dgas_gap). The rings seen in the observations (black) do not coindice with those seen in the models in general. Additionally, the modelled \[C I\] emission inside 200 au is up to more than one order of magnitude weaker than what is observed. At larger radii, the model slightly overpredicts the observations, but emission at these scales may be missing due to the small maximum recoverable scale (2" diameter, 108 au radius) of the observation. As the models predict that the molecules are abundant in an elevated layer at $z/r \sim 0.2-0.3$, the disk inclination of 41$\degree$ causes deprojection effects that wash out some of the rings in the CN and move those in to the location of the outer dust ring. Therefore, the azimuthally averaged radial profiles predicted by a face-on disk model are presented in Fig. [19](#fig:dali_azi_avg_dgap_face-on).

![](molecules_fid_diff_dgap_las6.0_incl41.pdf)

![](molecules_fid_diff_dgap_las6.0_incl0.pdf)

![](DALI_2D_dC_O_v2)

![](Nmolecules_diff_C_O.pdf)

Similar to the trend seen for the column density, the emission in the gap decreases for deeper gap depths. Even for the shallowest gas gap ($\delta_{\rm gas\ gap} = 10^{-1}$), a shallow gap and a ring are seen in the emission. For deeper gas gaps, the double ring nature of the emission becomes more pronounced (see Fig. [18](#fig:dali_azi_avg_dgap) for a more quantitative figure). The modelled intensity in the outer ring lays within a factor of 2.5 of the data for all models. To reproduce the diffuse emission observed in the gas gap, a model with a moderately deep gap of $10^{-2}-10^{-3}$ is needed. These models as well as those, with even deeper gap of $10^{-4}-10^{-5}$ match the intensity of the in the gas cavity within $2.5\sigma$, though the models predict a ring at $30-40$ au instead of centrally peaked emission.

The CN emission shows a bright inner ring just outside the inner dust ring and diffuse emission outwards. For gaps up to $\delta_{\rm gas\ gap} = 10^{-3}$, the CN intensity stays more or less constant. For deeper gaps, the CN intensity follows the trends seen in the column density and the inner ring becomes weaker. The models with gaps deeper than $10^{-2}$ all show emission from an elevated layer as the outer ring consists of two ellipses that are offset along the disk minor axis. This is not seen in the data where the outer CN ring is centred at the position of the star. Apart from this, the model with a deep gap of 4 orders of magnitude less gas resembles the observations quite closely as two distinct rings with an intensity within a factor of $\sim3$ of the observations are seen.

emits as a bright outer ring seen at 375 au due to the high column density in this region. This is much further out than the second ring seen in the data and not affected by the depth of the gas gap. Inside the gap, a ring at low intensity is seen. This ring follows the trend seen in the column density, moves inwards, and brightens as the gas gap becomes deeper. The bright ring seen in the model with a $10^{-4}$ deep gas gap is only peaks one beam further out than the ring seen in the observations but the modelled intensity is a factor of 40 too low. The inward travelling ring is also seen in the NO emission causing a very bright inner ring for the two models with the deepest gas gaps. The outer ring seen just outside the outer dust ring in the models is not detected in the observations.

Finally, the HCN shows a bright inner ring with an intensity within a factor of two of the observations for the models with a shallow gas gap. For the models with a gap deeper than $10^{-2}$ a gap and then a very weak ($\lesssim 5$ %) ring at the location of the outer dust ring are seen as highlighted by the white contours in Fig. [8](#fig:dali_mom0_dgap). This ring has an intensity of only $3-5$ times weaker than what is observed.

### Abundances and column densities for different C/O ratios

Figure [20](#fig:dali_2D_dC_O) presents the 2D abundance structure of (top row) and NO (bottom row) for the model with the fiducial C/O ratio of 0.4 and models with a higher C/O ratio of 0.99 and 1.01. The and NO molecules show opposite trends where the abundance increases with an increasing C/O ratio and the NO abundances decreases. The column densities of C, HCN, CN, , NO, and for different C/O ratios are presented in Fig. [21](#fig:N_dC_O). The column densities of the molecules that contain a carbon atom but no oxygen, C, HCN, CN, and , all increase with increasing C/O. In particular, the CN and are sensitive to a C/O ratio increasing from 0.99 to 1.01 as their column densities increase by one and two orders of magnitude, respectively. The NO molecule, that only carries an oxygen atom and no carbon, shows the opposite trend in general. The only exception to this is the high NO column density just outside the inner dust ring in the models with C/O $>1$. Finally, the is not sensitive to the C/O ratio in most disk regions as it carries both oxygen and carbon atoms.

### The effect of grain growth on 

The molecule is particularly sensitive to the C/O ratio and the UV field. In this subsection, the effect of grain growth, modelled as an increase in the fraction of large grains from 0.85 to 0.99, is presented. An increased fraction of large grains effectively removes small grains from the upper layers of the disk. This effect is shown in the top row of Fig. [22](#fig:fls)A. The abundance map is mainly affected in the surface layer around 300 au. This is also reflected in the emission that is similar between the two models (Fig. [22](#fig:fls)B).

![](Effect_small_grains.pdf)

## Molecular ratios

### Column density ratios for different gap depths

![](Nmolecules_ratios_diff_gas_gaps.pdf)

The /CO ratio for gaps up to two orders of magnitude deep is mainly driven by the CO density that is directly proportional to the gas density and the density that goes with the square root of the gas density (see Figs. [6](#fig:dali_N_dgap) and [23](#fig:Nratios_diff_gaps)). For deeper gaps, CO photodissociation drives the /CO ratio up. Even though no photodissociation is included in the small network, its photodissociation rate is 44 times lower than that of CO (cite: Heays2017). Therefore, the /CO ratio is most sensitive to the gas density.

The /CO ratio is primarily driven by the drop in the CO column density for gaps up to $10^{-3}$ as the column density only starts to drop steeply for gaps deeper than that. This causes the /CO ratio to saturate at a few $10^{-3}$ in the outer regions of the $10^{-5}$ deep gas gap. The CN/HCN ratio rapidly increases when the gap depth is lowered from $10^{-1}$ to $10^{-2}$ as the midplane HCN component is removed inside of $\sim 80$ au. For deeper gaps, the ratio settles between a value of $10-100$ inside the gap. Outside the gap, CN is a factor of ten more abundant than HCN.

In contrast to the former ratios, the CN/NO ratio is almost independent of gap depths for a disk with no gas gaps and gaps with up to two orders of magnitude less gas. This is due to the CN and NO column density that are both insensitive to the gap depths for these models. For deeper gaps, both the CN and the NO column density decrease as the gas gap becomes deeper but the CN column density does so at a slower rate than that of NO. Therefore, the CN/NO column density ratio is higher inside the gap than outside.

![](molecules_ratio_diff_dgap_las6.0_incl41.pdf)

![](molecules_ratio_diff_dgap_las6.0_incl41_0.1arcsec.pdf)

### Emission line ratios for different gap depths

The corresponding figure for the emission lines is presented in Fig. [24](#fig:Iratios_diff_gaps). For each ratio, the profile of the molecule at the highest spatial resolution is smoothed to the resolution of the image at lower resolution. The modelled ratios of /CO, /CO, CN/HCN, and CN/NO all peak inside the gas gap if the gas gap is at least $10^{-1}$ deep. The column density ratio increases with gap depth for most regions inside the gas gap, however, the ratio of the integrated intensity does not. This is due to the beam size of the observations. The size and orientation of the beam is such that the dust gap is sampled by only $\sim2$ beams across the disk minor axis. Therefore, the line ratio in the gap is dominated by the bright emission at the gap edges. If the models are convolved with a $3-4$ times smaller beam of $0.1\ensuremath{''}$, the gap depth can be traced up to a very deep gas gap of $10^{-4}$ times less gas, see Fig. [25](#fig:Iratios_diff_gaps_small_beam).

All models reproduce the / ratio seen inside the inner dust ring ($r<20$ au) and at 200 au where the outer dust ring is located. The observations show that this ratio first decreases in the gap and then increases, whereas the models with a gas gap show a peak at 125 au ($\delta_{\rm gas\ gap} = 10^{-2}-10^{-5}$) or 150 au ($\delta_{\rm gas\ gap} = 10^{-1}$). The fiducial model with a gap of only one order of magnitude best reproduces the observed ratio outside 100 au. The other models show a ratio of / that is too high, indicating that the ionisation is too high or the abundance of gas-phase water as traced by is too low in the gap. The latter is consistent with the detection of cold, gas-phase water lines originating from $\sim40-300$ au in this disk (cite: vanDishoeck2021; Pirovano2022). This is because the modelled abundance does not account for photodesorbed water.

The observed / ratio peaks just outside the inner dust ring and at the outer edge of the outer dust ring. The models with a gas gap show the opposite behaviour where a peak at $\sim 100$ au in the / ratio is predicted. Only the model without a drop in the gas density reproduces the overall trend of the observations with an offset of two orders of magnitude. This offset is driven by the modelled emission being too weak by that same factor.

The ratio of CN/HCN increases with radius, with a peak seen inside the gas gap and a decrease in the outer dust ring. The models with a gas gap predict the same trend across the disk, with the ratio agreeing within a factor of $\sim4$ for the models with gaps up to $10^{-2}$. The observations are most consistent with a gap depth of one to two orders of magnitude. The UV field in the models with deeper gas gaps is too intense to reproduce the CN/HCN ratio.

Finally, the CN/NO ratio is presented in the bottom right panel of [24](#fig:Iratios_diff_gaps). The CN/NO ratio of $\sim5$ at the inner dust ring is reproduced by the models that do not have a very deep gas gap of $10^{-4}-10^{-5}$. For the latter models, the NO intensity is much higher, lowering the CN/NO ratio. In the outer dust ring the observed ratio is $\sim 10$, whereas the models underpredict this by an order of magnitude.

In summary, the line ratios of /CO, /CO, and CN/HCN at the spatial resolution of the observations are only sensitive to the gas gap depths up to a gap with two orders of magnitude less gas. The latter ratio is well reproduced by the models, whereas the / is not due to the weak emission. The / ratio can be used to trace gas gaps that are up to two orders of magnitude depleted in gas.

![](Nmolecules_ratios_diff_C_O.pdf)

![](molecules_ratios_diff_C_O.pdf)

### Column density and line ratios for different C/O ratios

The column density ratios for various molecules as function of the C/O ratio are presented in Fig. [26](#fig:N_dC_O_ratios). The corresponding emission line ratios are presented in Fig. [27](#fig:I_dC_O_ratios). The / ratio presented in the top left corner does not depend on the C/O ratio of the gas for most disk regions. Only outside the outermost dust ring, the / ratio decreases by one order of magnitude down to the observed value for a C/O of 0.99 instead of 0.4.

The / ratio is driven by the emission that increases steeply with an increasing C/O ratio. Between the two dust rings, the observed / is best explained by a model with a C/O just below 1 at 0.99, whereas in the outer dust ring the model with a C/O of 1.01 is close to the observed ratio. The C/O ratio greatly affects the value of the / ratio, but it does not change the location of the peaks and dips in the profile. Therefore, a global change in the C/O ratio alone cannot explain the observations.

Increasing the C/O ratio increases the CN intensity more than it does so for the HCN. Therefore, the CN/HCN ratio increases with increasing C/O ratio. The morphology of the observed ratio is best reproduced by a C/O of $0.4-0.8$, whereas the value inside the gap is reproduced within $\sim 1\sigma$ for C/O = 0.99. The CN/NO ratio on the other hand is best reproduced by a low C/O of 0.4. In the outer disk, the CN/NO ratio increases by one order of magnitude for a C/O of 0.4, 0.8, 0.99, 1.01, and 1.2. Even though the S/N on the CN/NO ratio is low, the value in the outer dust ring is indicative of a slightly elevated C/O ratio of 0.8.

## Background UV

In Fig. [28](#fig:N_dbgUV), the column densities for models with a lower background UV radiation field are presented. This parameter mainly affects the column densities in the outer disk where a lower UV field lowers the column density of C, CN, , and NO, whereas it increases that of HCN somewhat due to less efficient photodissociation.

![](Nmolecules_diff_bgUV.pdf)

## Flaring

The column density and azimuthally averaged radial profiles of CO, HCN, CN, , NO, and are presented in Fig. [29](#fig:N_psi) and [30](#fig:I_psi), respectively. Flaring alone has a minor to no effect on the CO and column densities, whereas those of HCN, CN, , and NO do generally increase with decreasing flaring indices. These differences in the column densities are partially countered by the changing temperature structure as less flared disks intercept less UV.

![](Nmolecules_diff_psi.pdf)

![](molecules_fid_diff_psi_las6.0_incl41.pdf)

## X-ray luminosity

![](molecules_fid_diff_Lx_las6.0_incl41.pdf)

Fig. [31](#fig:I_Lx) presents the intensity of \[C I\], HCN, CN, , NO, and for the mean and maximum X-ray luminosities reported in (cite: Skinner2020) that are a factor of 4 and 6 higher than that in the fiducial model. The higher X-ray luminosity mainly affects the emission in the inner 100 au of the disk. The morphology of the emission is better reproduced by the model with a higher X-ray luminosities due to an inner ring at 30 au in the in these models. However, these models predict CN emission in the inner tens of au that is not seen in the observations. The effect of the increased X-ray luminosity on the emission is modelled as in increase in the effective cosmic ray ionisation rate by a factor of 2 and 5 respectively. This increases the modelled intensity by less than a factor of 2 in all disk regions.

[^1]: <https://github.com/richteague/keplerian_mask>

[^2]: <https://home.strw.leidenuniv.nl/~moldata/>

</paper>

Write the methods card for this paper.