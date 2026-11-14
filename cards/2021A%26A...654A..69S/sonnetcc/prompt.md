# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...654A..69S\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...654A..69S",
 "title": "SEEDisCS. II. Molecular gas in galaxy clusters and their large-scale structure: low gas fraction galaxies, the case of CL1301.7‒1139",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Spérone-Longin, D.",
 "n_authors": 11,
 "arxiv_id": "2105.02663",
 "doi": "10.1051/0004-6361/202140941",
 "alma_projects_linked_by_archive": [
  "2017.1.00257.S"
 ]
}
```

Paper text:
<paper>
# SEEDisCS

This paper is the second of a series that tackles the properties of molecular gas in galaxies residing in clusters and their related large-scale structures. Out of 21 targeted fields, 19 galaxies were detected in CO(3-2) with the Atacama Large Millimeter Array (ALMA), including two detections within a single field. These galaxies are either bona fide members of the CL1301.7$-$1139 cluster ($z=0.4828$, $\sigma_{cl}=681$ km s$^{-1}$), or located within $\sim 7 \times R_{200}$, its virial radius. They have been selected to sample the range of photometric local densities around CL1301.7$-$1139, with stellar masses above log($M_{\rm star}$) = 10, and to be located in the blue clump of star-forming galaxies derived from the $u$, $g$, and $i$ photometric bands. Unlike previous works, our sample selection does not impose a minimum star formation rate or detection in the far-infrared. As such and as much as possible, it delivers an unbiased view of the gas content of normal star-forming galaxies at $z \sim 0.5$. Our study highlights the variety of paths to star formation quenching, and most likely the variety of physical properties (i.e. temperature, density) of the corresponding galaxy’s cold molecular gas. Just as in the case of CL1411.1$-$1148, although to a smaller extent, we identify a number of galaxies with lower gas fraction than classically found in other surveys. These galaxies can still be on the star-forming main sequence. When these galaxies are not inside the cluster virialised region, we provide hints that they are linked to their infall regions within $\sim 4 \times R_{200}$.

# Introduction

It has long been established that the fraction of ellipsoidal and passive galaxies is dramatically increased in galaxy clusters in comparison with the field (cite: Dressler1980; Smith2005). There is now a growing body of evidence, from both observations and numerical simulations, that the related decrease in galaxy star formation activity already begins far beyond the cluster centres (cite: Gomez2003; Haines2015; Gouin2020), possibly in groups, which are later accreted (cite: Balogh2004; McGee2009; Bianconi2018), and in filaments (cite: Bahe2013).

We have entered a precision era in which the interplay between the growth of the cosmic structures and galaxy evolution can be investigated in detail. The most massive or quiescent galaxies are found the closest to the filament axes (cite: Malavasi2016; Laigle2018). This large-scale colour-density relation is seen even at $z\sim$1 (cite: Guzzo2018). However, quenching cannot be related to density in a simple way. As a matter of fact, star-forming galaxies exist in environments that span 4 orders of magnitude in local density (cite: Peng2010). (cite: Song2021) have looked into the relative influence of local density and the proximity to filaments. They conclude that the high vorticity of the filament plays an important role in star formation quenching, by impeding gas transfer to the galaxies.

Identifying how and where cold gas is abundant or missing and determining where its properties can change, is at the heart of our understanding of the nature and operation modes of star formation at galactic scales (cite: Bigiel2008; Leroy2008; Schruba2011). Molecular gas is unlikely to be as easily stripped as H I because it is denser and more centrally concentrated. Nevertheless, there are a number of spectacular examples of ram pressure stripping of molecular gas in the local Universe, such as in the Coma and Virgo clusters for example (cite: Scott2015; Jachym2014; Jachym2017). Yet, it is impossible to ascertain whether these examples reveal the general mechanism responsible for the suppression of star formation in dense environments. There is no established consensus on the possible dependence of the galaxy cold gas content on its environment (cite: Boselli2014; Koyama2017). (cite: Lee2017) suggest that one should instead investigate whether the gas properties (density, temperature) are modified.

So far studies of the cold molecular gas content of galaxies at intermediate redshifts have mostly focussed on distinct environments, isolating the field (cite: Gao2004; Abdo2010; Daddi2010; Tacconi2010; Tacconi2013; Garcia-Burillo2012; Baumgartner2013; Bauermeister2013; Bauermeister2013a; Morokuma-Matsui2015; Saintonge2017; Hayashi2018; Spilker2018; Freundlich2019; Lamperti2020), from groups (cite: Boselli1996; Martinez2012; Lisenfeld2017) and clusters (cite: Geach2009a; Geach2011; Jablonka2013; Rudnick2017a; Noble2017; Noble2019; Castignani2020b). Very few of these cluster studies purposely target galaxies beyond the cluster virial radius (cite: Morokuma-Matsui2021; Castignani2021).

This paper is the second of a series that tackles the properties of molecular gas in galaxies residing in clusters and their related large-scale structures. This survey concentrates on two spectroscopically well-characterised, intermediate-redshift, medium-mass clusters selected from the ESO Distant Cluster Survey (cite: White2005). The first results of the Spatially Extended EDisCS survey (SEEDisCS) were presented in (cite: Sperone-Longin2021).

This paper reports on the observations in CO(3-2) with the Atacama Large Millimeter Array (ALMA) of 22 galaxies in and around the second SEEDisCS galaxy cluster, CL1301.7$-$1139, at $z=0.4828$, and with a velocity dispersion of $\sigma_{cl}=681$ km s$^{-1}$. It is organised as follows: Section [\[sample\]](#sample) details our selection of the sample and presents the ALMA observations. In Sect. [\[results\]](#results) we present our results and our derivation of the galaxy parameters. We discuss our results in Sect. [\[discussion\]](#discussion), and we give our conclusions in Sect. [\[conclusion\]](#conclusion).

In the following, we assume a flat $\Lambda$ cold dark matter ($\Lambda$CDM) cosmology with $\Omega_{\rm m} = 0.3$, $\Omega_\Lambda = 0.7$, and $H_{0} = 70$ km s$^{-1}$ Mpc$^{-1}$ (cite: Riess2019; Planck2018), and we use a Chabrier initial mass function (IMF) (cite: Chabrier2003). All magnitudes are in the AB system.

# Sample and observations

## Sample selection

The 22 targets presented in this work are located inside CL1301.7$-$1139 and in its large-scale structures (cite: Milvang-Jensen2008). CL1301.7$-$1139 was chosen from EDisCS (cite: White2005) because, at its intermediate redshift, environmentally induced galaxy transformation was in its heyday, and because its medium mass makes it a valid representative of the progenitors of typical nearby galaxy clusters (cite: Milvang-Jensen2008). We first assembled CFHT/MEGACAM $u, g, r, i$, and $z$ deep imaging over a 1 deg$^2$ field of view, that is to say covering a region of radius r $\sim 10$ Mpc around the cluster centre. The $K_s$ deep imaging from GEMINI/NEWFIRM was obtained over an area of 0.24 deg$^2$, covering 5 cluster virial radii ($R_{200}$). Photometric redshifts, $z_{\rm phot}$ were obtained with EAZY (cite: Brammer2008) and are very accurate, with a normalised median absolute deviation of $\sigma_{\rm NMAD} \sim 0.036$. They have enabled the identification of the filamentary structures and infalling groups around CL1301.7$-$1139 (see Fig. [1](#targets)).

The targets for the ALMA follow-up were selected based on the following four criteria: ***i)*** they have spectroscopic redshifts from ESO/FORS2 or MMT/Hectospec, or at least a robust estimate from the IMACS Low Dispersion Prism (cite: Just2019), all falling within $\mathrm{3\sigma_{cl}}$; ***ii)*** they are located within $7\times R_{200}$[^1], sampling the range of photometric local densities encountered around CL1301.7$-$1139 (see Fig.[1](#targets)); ***iii)*** they have stellar masses above log($M_{\rm star}$) = 10; ***iv)*** they cover the same sequence in $u-g$ versus $g-i$ which is typical of star-forming galaxies as in CL1411.1$-$1148 at $z=0.5195$ . Table [\[obs_table\]](#obs_table) provides the coordinates and optical redshifts of our targets, together with their stellar masses ($M_{\rm star}$) and star formation rates (SFRs).

![](density_map_1301_alma_targets_vfin6.png)

Figure [1](#targets) presents the position of our targets in the global photometric density map, as calculated from the $u,\,g,\,r,\,i$, and $z$ images, in the 1$\ensuremath{^\circ}\times$1$\ensuremath{^\circ}$ region centred on CL1301.7$-$1139. Densities were calculated within a photometric slice of $\pm 1 \delta_{\rm cl}=(1+z_{\rm cl})\times \sigma_{\rm NMAD} = 0.0533$ around the cluster redshift. Within this photometric redshift slice, we used a ‘nearest neighbour’ approach, in which for any point $(x,y)$ one estimates the distance $r_N(x,y)$ to the $Nth$ nearest neighbour. The density is thus the ratio between the (fixed) $N$ and the surface defined by the adaptive distance: $\rho_N(x,y)=\frac{N}{\pi r^2_N(x,y)}$. We chose $N=10$, which corresponds to an average scale of about 0.8 Mpc and with 90% of the values being smaller than $\sim1.5$ Mpc.

Figure [2](#light_cone) provides another view of the spatial distribution of our ALMA targets, keeping the same 1$\ensuremath{^\circ}\times$1$\ensuremath{^\circ}$ MEGACAM field of view. The galaxy positions were calculated relative to the position of the brightest cluster galaxy (BCG) in redshift and right ascension (RA) (cite: White2005). The galaxy relative position in redshift, $\Delta d_{\rm cl}$, was computed by taking the difference between the co-moving distances of the galaxy and of the BCG. The relative position in RA, $\Delta$RA, was obtained by transforming the angular separation between the BCG and the galaxy into a distance, using the angular distance at the redshift of the galaxy. Our full spectroscopic sample within $\pm 3\times\sigma_{\rm cl}$ of $z_{\rm cl}$ is presented as well as the photometric membership candidates. The finger-of-God structure due to the relative velocities of the galaxies in CL1301.7$-$1139 is clearly seen along the $\Delta d_{\rm cl}$-axis. Eight of our targets are genuine cluster members, within or at the cluster virial radius, and with v/$\sigma_{cl} \lesssim 1$. They are identified in Table [\[obs_table\]](#obs_table) by their original EDisCS names. Three galaxies, namely, SEDCSJ1301144$-$1147490, SEDCSJ1301044$-$1146232, and SEDCSJ1301007$-$1147075, fall on the south-west photometric overdensity at RA $\sim195.3$ ($\Delta d_{\rm cl}\sim20$ Mpc, $\Delta {\rm RA}\sim -3$). They have a mean redshift of 0.488 with a standard deviation of $\sigma_z = 9.8\times 10^{-4}$. Two other galaxies, with spectroscopic redshifts, however without CO observations, fall in this redshift interval as well, suggesting that these three ALMA targets indeed do belong to a group with $\sigma_{\rm g} \sim$ 150–200 km s$^{-1}$. The rest of our ALMA sample is either located in low density regions or photometric overdensities, which has yet to be spectroscopically confirmed.

![](light_cone_deltara_vfin6.png)

![](CCD_gi_ug_1301_vfin6b_UL.png)

Figure [3](#ugi) displays the distribution of our targets in the $g-i$ vs $u-g$ colour–colour diagram, using total magnitudes. The ALMA targets in and around CL1301.7$-$1139 are shown with the green squares, and we show the ALMA targets for CL1411.1$-$1148 with green circles for comparison. The CL1301.7$-$1139 galaxies span most of the blue clump, extending into the lower $g-i$ boundary of the red sequence. Three systems have $g-i$ colours slightly below the red sequence but their $u-g$ colours are consistent with them being on the red sequence.

Figure [4](#rf_CCD) presents the rest-frame $U-V$ versus $V-J$ colour–colour diagram which further helps discriminate between passive and star-forming galaxies (cite: Williams2009). The rest-frame colours were derived with EAZY (cite: Brammer2008). We used the Johnson-Cousins $U$ and $V$ bands, and the 2MASS $J$ band (cite: Skrutskie2006), together with a set of six templates: five main component templates obtained following the (cite: Blanton2007a) algorithm and one for dusty galaxies (cite: Brammer2008). From the four galaxies which were photometrically falling in the green valley as inferred from the $u$, $g$, and $i$ bands, three turned out to be located in the $UVJ$ region of passive systems. Two of them, namely EDCSNJ1301336$-$1138071 and EDCSNJ1301336$-$1138090, were falling in the same ALMA field of view. EDCSNJ1301336$-$1138071 was our primary target. Both are cluster members. The rest of our targets follow the $UVJ$ star-forming sequence, including EDCSNJ1301441$-$1140589 which was red in $u-g$ and at the blue $g-i$ border of the red sequence.

![](UVJ_rf_diagram_lowmu_woWise_vfin6_UL.png)

|  |  |  |  |  |  |
|:---|:--:|:--:|:---|---:|---:|
|  |  |  |  |  |  |
| IDs | R.A. (J2000) | Dec (J2000) | ${z_{\rm spec}}$ | $M_{\mathrm{star}}$  ($\mathrm{10^{10}\,M_{\odot}}$) | $\mathrm{SFR}_{SED}$  ($\mathrm{M_{\odot}\,yr^{-1}}$) |
|  |  |  |  |  |  |
| SEDCSJ1300003$-$1144203  | 13:00:00.3688 | $-$11:44:20.346 | 0.4878 | $4.68^{+1.83}_{-1.29}$ | $6.64^{+9.63}_{-4.59}$ |
| SEDCSJ1300234$-$1132052$^\dagger$ | 13:00:23.4345 | $-$11:32:05.222 | 0.4907 | $7.41^{+2.05}_{-2.22}$ | $8.85^{+9.78}_{-7.85}$ |
| SEDCSJ1300324$-$1137445  | 13:00:32.4211 | $-$11:37:44.584 | 0.4841 | $3.63^{+1.34}_{-1.09}$ | $16.48^{+14.42}_{-6.45}$ |
| SEDCSJ1300340$-$1127269  | 13:00:34.0731 | $-$11:27:26.913 | 0.4789 | $3.98^{+1.19}_{-1.1}$ | $8.07^{+5.48}_{-4.65}$ |
| SEDCSJ1301007$-$1147075  | 13:01:00.7272 | $-$11:47:07.522 | 0.4770$^{a}$ | $2.63^{+0.61}_{-0.67}$ | $4.86^{+2.91}_{-2.46}$ |
| SEDCSJ1301044$-$1146232  | 13:01:04.4539 | $-$11:46:23.263 | 0.4880$^{a}$ | $1.91^{+0.44}_{-0.39}$ | $10.76^{+7.06}_{-3.96}$ |
| SEDCSJ1301144$-$1147490 | 13:01:14.4426 | $-$11:47:49.051 | 0.4879 | $2.82^{+0.84}_{-0.65}$ | $7.80^{+5.84}_{-4.31}$ |
| SEDCSJ1301216$-$1136480  | 13:01:21.6371 | $-$11:36:48.027 | 0.4927 | $5.13^{+1.06}_{-1.06}$ | $12.22^{+7.6}_{-6.05}$ |
| SEDCSJ1301240$-$1132137  | 13:01:24.0810 | $-$11:32:13.735 | 0.4790$^{a}$ | $4.07^{+0.94}_{-0.75}$ | $14.86^{+9.58}_{-5.65}$ |
| EDCSNJ1301323$-$1141558  | 13:01:32.3246 | $-$11:41:55.846 | 0.4797 | $3.80^{+0.79}_{-0.70}$ | $10.52^{+5.57}_{-4.36}$ |
| EDCSNJ1301336$-$1138071$^*$ | 13:01:33.6127 | $-$11:38:07.126 | 0.4858 | $3.63^{+1.50}_{-0.50}$ | $0.36^{+0.24}_{-0.36}$ |
| EDCSNJ1301336$-$1138090$^*$ | 13:01:33.6420 | $-$11:38:09.025 | 0.4854 | $8.32^{+1.72}_{-2.49}$ | $0.52^{+0.46}_{-0.48}$ |
| EDCSNJ1301344$-$1142380$^\dagger$ | 13:01:34.4495 | $-$11:42:38.039 | 0.4853 | $1.82^{+0.38}_{-0.42}$ | $1.44^{+0.93}_{-0.81}$ |
| SEDCSJ1301349$-$1146512 | 13:01:34.9086 | $-$11:46:51.222 | 0.4842 | $7.41^{+1.54}_{-2.05}$ | $4.09^{+3.3}_{-2.73}$ |
| EDCSNJ1301363$-$1138495  | 13:01:36.3447 | $-$11:38:49.502 | 0.4787 | $3.47^{+0.64}_{-0.80}$ | $4.00^{+3.45}_{-2.62}$ |
| SEDCSJ1301380$-$1127055  | 13:01:38.0353 | $-$11:27:05.546 | 0.4819 | $7.59^{+2.10}_{-2.10}$ | $11.27^{+12.07}_{-10.12}$ |
| EDCSNJ1301383$-$1140011$^\dagger$ | 13:01:38.3445 | $-$11:40:01.197 | 0.4794 | $3.63^{+0.67}_{-0.75}$ | $5.09^{+2.75}_{-2.58}$ |
| EDCSNJ1301441$-$1140589  | 13:01:44.1493 | $-$11:40:58.995 | 0.4842 | $3.98^{+0.83}_{-1.28}$ | $1.89^{+1.44}_{-1.13}$ |
| EDCSNJ1301524$-$1138043 | 13:01:52.4694 | $-$11:38:04.391 | 0.4843 | $5.13^{+1.54}_{-1.42}$ | $6.41^{+5.09}_{-3.54}$ |
| SEDCSJ1302036$-$1137519$^*$ | 13:02:03.6095 | $-$11:37:51.978 | 0.4873 | $3.09^{+0.64}_{-1.00}$ | $0.66^{+0.51}_{-0.53}$ |
| SEDCSJ1302292$-$1133316  | 13:02:29.2680 | $-$11:33:31.606 | 0.4810 | $5.50^{+1.64}_{-1.52}$ | $14.86^{+8.38}_{-7.36}$ |
| SEDCSJ1302415$-$1143157 | 13:02:41.5765 | $-$11:43:15.746 | 0.4877 | $4.37^{+1.91}_{-1.51}$ | $10.76^{+22.42}_{-6.32}$ |

Table notes: Galaxies with low $\mu_\mathrm{H_2}$ are identified with $^\dagger$. Galaxies with CO upper-limits are identified with $^*$.

## ALMA observations 

The observations were conducted in the CO(3-2) line (233 GHz at $z\sim 0.48$), falling in the ALMA Band 6, in compact configurations C43$-$2, for a beam size of 1.2$''$$\times$ 0.95$''$  during Cycle 5 (program 2017.1.00257.S). The integration time on targets was 6.75 hours, 11h with overheads. The rms noise was computed at the fixed resolution of 50.7 km s$^{-1}$ and ranges from 29 to 84 $\mu$Jy/beam. The large range of values is mainly due to different observing conditions for each of our targets.

The same data reduction procedure as used for CL1411.1$-$1148  was applied, with the CASA ALMA Science Pipeline (cite: McMullin2007). Problems with antennas and runs were flagged ($<3\%$), the continuum was subtracted, while excluding the spectral channels of the line emission during the fit of the continuum – as we only focus on the CO line – and the primary beam was corrected in order to form an astronomically correct image of the sky. The final continuum-subtracted and primary-beam-corrected maps were exported in order to be analysed using GILDAS[^2]. The $i$-band images of our targets, the CO maps and spectra are shown in Fig. [11](#maps).

# Derived parameters 

## CO flux and molecular gas mass

Fluxes, $S_\mathrm{CO}\,\Delta V$, were extracted by integrating the CO(3-2) emission over the full spatial extent of the source using circular apertures with radii between 0.8$''$ and 1.4$''$ depending on the size of the galaxy. Following (cite: Lamperti2020), the error on the flux is defined as $$\begin{equation}
\epsilon_{\rm CO} = \frac{\sigma_{\rm CO}\Delta V}{\sqrt{\Delta V \Delta w_{ch}^{-1}}},
\end{equation}$$ where $\sigma_{\rm CO}$ is the rms noise (in Jy) calculated in units of spectral resolution $\Delta w_{ch}$, and $\Delta V$ (in km s$^{-1}$) is the width of the spectral window in which the line flux was calculated, $\Delta w_{ch} = 50.7$ km s$^{-1}$. All intensity maps and integrated spectra are shown in Fig [11](#maps) of the Appendix. The full widths at half maximum (FWHM) were derived from single Gaussian fits of the emission lines. We obtain a median FWHM of 220 km s$^{-1}$ with a standard deviation of 96 km s$^{-1}$, which is compatible with the type of massive galaxies we are studying (cite: Freundlich2019).

Even though the targets are just slightly more extended than the beam size, a few of them show a double peaked emission line, which is an indication of rotation. This will be analysed in a forthcoming paper.

The intrinsic CO luminosity associated with a transition between the levels $J$ and $J-1$ is expressed as $$\begin{equation}
 \label{eq1}
    L'_\mathrm{CO(J\rightarrow J-1)}=3.25 \times10^{7} S_\mathrm{CO(J\rightarrow
      J-1)} \Delta V \, \nu_\mathrm{obs}^{-2} \, D_\mathrm{L}^{2} \, (1+z)^{-3},
\end{equation}$$ where $L'_\mathrm{CO(J\rightarrow J-1)}$ is the line luminosity expressed in units of ${\rm K\,km\,s\textsuperscript{-1} pc^2}$; $S_\mathrm{CO(J\rightarrow
J-1)} \Delta V$ is the velocity-integrated flux in ${\rm Jy\,km\,s^{-1}}$; $\nu_\mathrm{obs}$ is the observed frequency in GHz; $D_\mathrm{L}$ is the luminosity distance in Mpc; and $z$ is the redshift of the observed galaxy (cite: Solomon1997; Solomon2005). The flux for our upper-limit detections are defined as $3\times\epsilon_{\rm CO}$, with $\Delta V=220$ km s$^{-1}$, the median value of our sample.

The total cold molecular gas mass ($M_\mathrm{H_2}$) was then estimated as $$\begin{equation}
 \label{eq2}
    M_\mathrm{H_2}=\alpha_\mathrm{CO} \frac{L'_\mathrm{CO(J\rightarrow J-1)}}{r_{J1}}, 
\end{equation}$$ where $\alpha_\mathrm{CO}$ is the CO(1-0) luminosity-to-molecular-gas-mass conversion factor, considering a 36% correction to account for interstellar helium, and $r_{J1}=L^{\prime}_\mathrm{CO(J\rightarrow J-1)} / L^{\prime}_\mathrm{CO(1-0)}$ is the corresponding line luminosity ratio.

Just as in and for the sake of reliable comparison, we have considered $\alpha_\mathrm{CO}=4.36 \pm 0.9\,M_\odot\,{\rm (K\,km\,s^{-1}\,pc^2)^{-1}}$, which includes the correction for helium, as a good estimate for normal star-forming galaxies (cite: Dame2001; Grenier2005; Abdo2010; Leroy2011; Bolatto2013; Carleton2017). For the same reason, we assume $r_{31}=0.5\pm0.05$ similarly to other intermediate to high-$z$ studies (cite: Bauermeister2013; Genzel2015; Chapman2015; Carleton2017; Tacconi2018) The intrinsic CO(3-2) luminosity $L^{\prime}_\mathrm{CO(3-2)}$, the FWHM, the cold molecular gas mass $M_\mathrm{H_2}$, the corresponding gas-to-stellar-mass ratio $\mu_\mathrm{H_2}=M_\mathrm{H_2}/M_\mathrm{star}$, and the redshift of the CO emission of our sample galaxies are listed in Table [\[properties_table\]](#properties_table).

l l c r r r c c\
IDs & $z_{\mathrm{CO}}$ & & & & & $\mu_{\mathrm{H_{2}}}$ &\
\
SEDCSJ1300003$-$1144203 & 0.4879 & 0.600 $\pm$ 0.020 & 440 $\pm$ 40 & 8.295 $\pm$ 0.280 & 7.23 $\pm$ 0.24 & $0.155^{+0.066}_{-0.048}$ & $1.089^{+1.581}_{-0.753}$\
SEDCSJ1300234$-$1132052$^\dagger$ & 0.4907 & 0.105 $\pm$ 0.014 & 230 $\pm$ 20 & 1.469 $\pm$ 0.198 & 1.28 $\pm$ 0.17 & $0.017^{+0.007}_{-0.007}$ & $0.145^{+0.161}_{-0.130}$\
SEDCSJ1300324$-$1137445 & 0.4841 & 0.523 $\pm$ 0.013 & 190 $\pm$ 10 & 7.115 $\pm$ 0.176 & 6.20 $\pm$ 0.15 & $0.171^{+0.067}_{-0.055}$ & $0.376^{+0.330}_{-0.148}$\
SEDCSJ1300340$-$1127269 & 0.4789 & 0.722 $\pm$ 0.013 & 180 $\pm$ 10 & 9.606 $\pm$ 0.176 & 8.38 $\pm$ 0.15 & $0.210^{+0.067}_{-0.062}$ & $1.038^{+0.705}_{-0.598}$\
SEDCSJ1301007$-$1147075 & 0.4874$^{a}$ & 0.222 $\pm$ 0.010 & 180 $\pm$ 10 & 3.063 $\pm$ 0.132 & 2.67 $\pm$ 0.11 & $0.102^{+0.028}_{-0.030}$ & $0.550^{+0.330}_{-0.279}$\
SEDCSJ1301044$-$1146232 & 0.4898$^{a}$ & 1.420 $\pm$ 0.016 & 310 $\pm$ 20 & 19.785 $\pm$ 0.235 & 17.25 $\pm$ 0.21 & $0.905^{+0.219}_{-0.198}$ & $1.603^{+1.052}_{-0.591}$\
SEDCSJ1301144$-$1147490& 0.4880 & 0.295 $\pm$ 0.013 & 240 $\pm$ 20 & 4.079 $\pm$ 0.181 & 3.56 $\pm$ 0.16 & $0.126^{+0.043}_{-0.035}$ & $0.456^{+0.342}_{-0.253}$\
SEDCSJ1301216$-$1136480 & 0.4927 & 0.694 $\pm$ 0.013 & 260 $\pm$ 20 & 9.792 $\pm$ 0.192 & 8.54 $\pm$ 0.17 & $0.166^{+0.038}_{-0.038}$ & $0.699^{+0.435}_{-0.346}$\
SEDCSJ1301240$-$1132137 & 0.4935$^{a}$ & 0.691 $\pm$ 0.008 & 140 $\pm$ 10 & 9.780 $\pm$ 0.120 & 8.53 $\pm$ 0.10 & $0.209^{+0.051}_{-0.041}$ & $0.574^{+0.370}_{-0.218}$\
EDCSNJ1301323$-$1141558 & 0.4796 & 0.790 $\pm$ 0.010 & 180 $\pm$ 10 & 10.541 $\pm$ 0.135 & 9.19 $\pm$ 0.12 & $0.242^{+0.053}_{-0.048}$ & $0.874^{+0.463}_{-0.362}$\
EDCSNJ1301336$-$1138071$^*$ & 0.4869 & $<0.026$ & $...$ & $...$ & $<0.32$ & $<0.009$ & $<0.882$\
EDCSNJ1301336$-$1138090$^*$ & 0.4854 & $<0.026$ & $...$ & $...$ & $<0.32$ & $<0.004$ & $<0.607$\
EDCSNJ1301344$-$1142380$^\dagger$ & 0.4854 & 0.140 $\pm$ 0.012 & 210 $\pm$ 10 & 1.915 $\pm$ 0.163 & 1.67 $\pm$ 0.14 & $0.092^{+0.027}_{-0.029}$ & $1.160^{+0.754}_{-0.662}$\
SEDCSJ1301349$-$1146512& 0.4843 & 0.344 $\pm$ 0.024 & 450 $\pm$ 20 & 4.684 $\pm$ 0.321 & 4.08 $\pm$ 0.28 & $0.055^{+0.015}_{-0.019}$ & $0.999^{+0.808}_{-0.670}$\
EDCSNJ1301363$-$1138495 & 0.4785 & 0.295 $\pm$ 0.014 & 320 $\pm$ 20 & 3.917 $\pm$ 0.191 & 3.42 $\pm$ 0.17 & $0.099^{+0.023}_{-0.027}$ & $0.854^{+0.739}_{-0.562}$\
SEDCSJ1301380$-$1127055 & 0.4819 & 0.465 $\pm$ 0.022 & 380 $\pm$ 20 & 6.266 $\pm$ 0.295 & 5.46 $\pm$ 0.26 & $0.072^{+0.023}_{-0.023}$ & $0.485^{+0.520}_{-0.436}$\
EDCSNJ1301383$-$1140011$^\dagger$ & 0.4799 & 0.145 $\pm$ 0.015 & 160 $\pm$ 20 & 1.937 $\pm$ 0.196 & 1.69 $\pm$ 0.31 & $0.047^{+0.017}_{-0.018}$ & $0.332^{+0.190}_{-0.179}$\
EDCSNJ1301441$-$1140589& 0.4847 & 0.285 $\pm$ 0.008 & 160 $\pm$ 10 & 3.886 $\pm$ 0.114 & 3.39 $\pm$ 0.10 & $0.085^{+0.020}_{-0.030}$ & $1.793^{+1.363}_{-1.075}$\
EDCSNJ1301524$-$1138043& 0.4845 & 0.365 $\pm$ 0.011 & 180 $\pm$ 10 & 4.973 $\pm$ 0.155 & 4.34 $\pm$ 0.13 & $0.085^{+0.028}_{-0.026}$ & $0.676^{+0.538}_{-0.374}$\
SEDCSJ1302036$-$1137519$^*$ & 0.4873 & $<0.097$ & $...$ & $...$ & $<1.17$ & $<0.038$ & $<1.769$\
SEDCSJ1302292$-$1133316 & 0.4813 & 0.580 $\pm$ 0.011 & 130 $\pm$ 20 & 7.797 $\pm$ 0.147 & 6.8 $\pm$ 0.13 & $0.124^{+0.039}_{-0.037}$ & $0.458^{+0.258}_{-0.227}$\
SEDCSJ1302415$-$1143157& 0.4877 & 0.295 $\pm$ 0.009 & 120 $\pm$ 10 & 4.074 $\pm$ 0.129 & 3.55 $\pm$ 0.11 & $0.081^{+0.038}_{-0.031}$ & $0.330^{+0.688}_{-0.194}$\

Table notes: Galaxies with low $\mu_\mathrm{H_2}$ are identified with $^\dagger$. Galaxies with CO upper-limits are identified with $^*$.

## Stellar masses and SFRs 

Stellar masses and SFRs were derived with MAGPHYS[^3] (cite: daCunha2008), based on the $u$, $g$, $r$, $i$, $z$, and $K_s$ total magnitudes. The stellar populations and dust extinction models are those of (cite: Bruzual2003) and (cite: Charlot2000). MAGPHYS provides probability density functions (PDFs) for each parameter, such as the SFR, $M_{\rm star}$, dust mass, and dust temperature. Their values in this work correspond to the peak values of the PDFs. The uncertainties are the 68% confidence interval of the PDFs. The photometric wavelength coverage does not allow for the identification of active galactic nuclei (AGNs), which could affect the SFRs in particular. However, the analysis of the galaxy spectra, in particular, the \[O II\] to H$\beta$ line ratio suggests that they are not typical AGNs (cite: Sanchez-Blazquez2009; Rudnick2017). These are anyway rare in clusters, comprising approximately 3% of the overall population (cite: Miller2003; Kauffmann2004; Mishra2020).

![](MS_w_rs+gv_1301_1411_vfin6d.png)

Figure [5](#MScl1301) presents the position of our ALMA targets relative to the main sequence (MS) of normal star-forming galaxies at the cluster redshift as inferred by (cite: Speagle2014). Only galaxies with spectroscopic or photometric redshift and with $K_s$ photometry are shown. Indeed the near-infrared (NIR) flux allows for the most robust mass and SFR estimates. Almost two-thirds (65%) of our ALMA targets fall within the $\pm0.3$ dex dispersion of the MS. The following three ALMA targets fall far below the $-0.3$ dex boundary, in between the MS and the red sequence: SEDCSJ1301349$-$1146512, EDCSNJ1301344$-$1142380, and EDCSNJ1301441$-$1140589. These are systems in the transition region between star-forming and passive systems. Two of those are bona fide cluster members (EDCSNJ1301344$-$1142380 and EDCSNJ1301441$-$1140589), while SEDCSJ1301349$-$1146512 is located at a distance of $\sim2R_{200}$, however it is still within v/$\sigma_{cl}<1$ and is therefore most probably an infalling system (cite: Mahajan2011). All but three were detected in CO. Finally, three galaxies turned out to be on the passive sequence (log(SFR) $\lesssim -0.2$). Two of them (EDCSNJ1301336$-$1138071 and EDCSNJ1301336$-$1138090 are cluster members), while SEDCSJ1302036$-$1137519 is an infalling system that is $\sim1.5 R_{200}$ and still within v/$\sigma_{cl}\sim1.5$. We could only place upper limits on their CO fluxes. It would be tempting to attribute their lack of star formation activity and their CO deficiency to their early-type morphologies. However, similar systems without evidence of disks in Fig. [11](#maps) (SEDCSJ1301144$-$1147490, EDCSNJ1301344$-$1142380 and SEDCSJ1301216$-$1136480) have nevertheless been detected in CO.

![](ssfr_vs_z_1301_vfin6b_UL.png)

Figure [6](#z_sSFR) provides an overview of the galaxy specific star formation rates (sSFR) as a function of redshift from $\sim0.02$ to $\sim2$ for galaxies with existing CO line fluxes. The list of our comparison samples is identical to that of where their exact composition, redshift range, selection and CO line transitions are detailed (cite: Gao2004; Garcia-Burillo2012; Saintonge2017; Baumgartner2013; Lamperti2020; Abdo2010; Bauermeister2013a; Bauermeister2013; Morokuma-Matsui2015; cybulski2016; Castignani2020b; Jablonka2013; Geach2009a; Geach2011; Tacconi2010; Tacconi2013; Tacconi2018; Freundlich2019; Spilker2018; Hayashi2018; Daddi2010; Noble2017; Noble2019; Rudnick2017a). The galaxy stellar masses of these comparison samples were originally derived by SED fitting, assuming either a ‘Chabrier’ or a ‘Kroupa’ IMF (cite: Kroupa2001; Chabrier2003). We converted all masses to a Chabrier IMF using the relation of (cite: Zahid2012): $M_{{\rm star},\,C}=0.94 \times M_{{\rm star},\,K}$.

Most existing datasets have focussed on field galaxies, with the exception of (cite: Geach2009a; Geach2011), (cite: Jablonka2013), (cite: cybulski2016), (cite: Rudnick2017a), (cite: Hayashi2018), (cite: Noble2017; Noble2019) and (cite: Castignani2020b). The present analysis provides the second largest sample centred on galaxy clusters at a fixed given redshift, the other one being our analysis of galaxies related to the CL1411.1$-$1148 environment. Both samples cover the same range of specific SFRs and uniquely trace galaxies in interconnected cosmic structures around galaxy clusters.

One hypothesis raised in is that the selection criteria of the different CO galaxy surveys could impact our understanding of the relationship between the galaxy stellar mass, star formation activity, and cold molecular gas content. In order to help shed light on this issue, the left panel of Fig. [7](#histograms) presents the galaxy sSFRs normalised to the position of the galaxies on the MS (sSFR/sSFR(MS, $z$, $M_{\rm star}$) as originally put forward by (cite: Genzel2015). Galaxies are grouped in redshift slices and we distinguish between field and clusters samples.

![image](distri_ssfrn_z_vfin7.png)

![image](distri_muh2_z_vfin7_samealpha_medianvalues.png)

While, as mentioned above, the galaxy stellar masses are derived in a relatively homogeneous way, the estimates of the SFRs rely on a much larger set of methods. The most common one is based on the galaxy far-infrared (FIR) luminosity, which sometimes takes the UV emission into account (cite: Daddi2007; Daddi2010; Tacconi2013; cybulski2016; Hayashi2018; Noble2017; Noble2019; Freundlich2019). Another group of studies have used galaxy SED fits (cite: Castignani2020b; Rudnick2017a; Sperone-Longin2021). (cite: Wuyts2011a) showed that in the low- to intermediate-SFR regime, SFR $\lesssim 50\,M_\ensuremath{\odot} {\rm yr}^{-1}$, the values obtained by the two above methods, SFR$_{\rm UV + FIR}$ and SFR$_{\rm SED}$, agree with each other within uncertainties. Finally, SFRs can be estimated from a set of emission lines, such as \[O II\], \[O III\], H$\alpha$, \[N II\], and \[S II\] (cite: Bauermeister2013a; Bauermeister2013). The slope and width of the MS provided by (cite: Speagle2014) take this variety of methods into account. Therefore the comparison of the different surveys and specifically the position of the galaxies in sSFR/sSFR(MS, $z$, $M_{\rm star}$) is meaningful.

The difference in galaxy population between surveys is conspicuous in Fig.[7](#histograms). It does not depend on field or cluster environments, but rather on the target selection criteria, which results in a general over-representation of galaxies above the MS As a matter of fact, (cite: Bauermeister2013a; Bauermeister2013) explicitly selected their targets with sSFR between 1 and 4 times that of MS galaxies. Similarly, prior detection at 24$\mu$m (cite: Daddi2004; cybulski2016), or some of the `Herschel` bands (cite: Daddi2010; Castignani2020b) does play a role in this bias towards actively star-forming systems, unless it is purposely controlled to include systems below the MS, as it was done by the PHIBSS1/2 field surveys at $0.5 < z < 0.8$ (cite: Tacconi2010; Tacconi2013; Freundlich2019). Very noticeably, our CL1301.7$-$1139 and CL1411.1$-$1148 samples, without any prior on previous FIR detection and in the vicinity of high density environments, are devoid of galaxies above the MS.

# Results

## Gas fractions 

The right panel of Fig. [7](#histograms) presents the distribution of the galaxy gas fraction, $\mu_\mathrm{H_2}$ $=M_{\mathrm{H_{2}}} /$$M_{\rm star}$, corresponding to the distribution in normalised sSFRs of the left panel. The cold molecular gas masses were derived using the same value of $\alpha_{\rm CO}$, $\alpha_{\rm MW}=4.36\,M_\odot{\rm (K\,km\,s^{-1}\,pc^2)^{-1}}$, for most samples (cite: Daddi2010; Geach2011; Tacconi2010; Tacconi2013; Bauermeister2013a; Bauermeister2013; cybulski2016; Rudnick2017a; Hayashi2018; Noble2017; Noble2019). The other samples have linked the value of their CO-to-H$_2$ conversion factor either to metallicity (cite: Freundlich2019), or to the position of the galaxy with respect to the MS (cite: Castignani2020b). Considering $\alpha_{\rm MW}$ for these two samples slightly redistributes the position of the galaxies within the distributions, but does not modify their global shapes and mean positions. It stands out from Fig. [7](#histograms) that samples that are skewed towards high sSFRs also have higher galaxy gas mass fractions. This is particularly the case at $z \le 0.8$. At $z > 1$, the galaxy star formation activity is not sufficient to explain the very significant enhancement of the galaxy cold gas content and evolution with the lookback time which is an important factor.

Our CL1301.7$-$1139 and CL1411.1$-$1148 samples do not cover the high-$\mu_\mathrm{H_2}$ tail of the other distributions, but they do not reach particularly low values either, in particular with respect to PHIBSS2, which is the best field counterpart to our study. Just as in the case of CL1411.1$-$1148, differences in $\mu_\mathrm{H_2}$ appear when it is matched with the galaxy $M_{\rm star}$. This is done in Fig. [8](#Ms_fg).

![](muh2_vs_mstar_low_mu_1301_vfin6d.png)

In , we had identified a subset of star-forming galaxies with low gas mass fractions for their stellar mass. More specifically, these galaxies were falling below the $1\times\sigma_{\rm H_2}$ dispersion of the $M_{\rm star}$–$\mu_\mathrm{H_2}$ relation derived at $z=0.55$ from the PHIBSS2 field galaxies at $0.5<z\leq0.6$. In order to look for similar types of galaxies around CL1301.7$-$1139, we first needed to set the relation between $M_{\rm star}$ and $\mu_\mathrm{H_2}$ at $z=0.45$. (cite: Tacconi2018) have shown that the slope, in logarithmic scale, of the $M_{\rm star}$–$\mu_\mathrm{H_2}$ relation for MS galaxies does not vary with redshift and that only a zero point shift should be taken into account. Therefore, the $M_{\rm star}$–$\mu_\mathrm{H_2}$ relation for field MS systems is shown in Fig. [8](#Ms_fg) with a constant slope of $-0.82$ and a shift of $-0.08$ dex, induced by the transition from $z=0.55$ to $z=0.45$. This new relation is shown together with the $\pm 1 \times \sigma_{\rm H_2}$ interval, with $\sigma_{\rm H_2}=0.37$ the variance of the $M_{\rm star}$–$\mu_\mathrm{H_2}$ relation calculated in .

We stress that the identification of the low-$\mu_\mathrm{H_2}$ galaxies is drawn relative to field surveys. It does not necessarily imply that these star-forming galaxies have a low cold gas content in absolute terms, but rather that they were at least missing from an earlier investigation. We explore to what extent their properties could be linked to the high density environments, themselves, or their close vicinity, on which we are focussing.

The three passive galaxies of Fig. [5](#MScl1301) are not considered in this analysis because we focus on systems that are still active. Therefore, following the same criterion as in , three star-forming galaxies fall below the $-1\times \sigma_{\rm H_2}$ line of the $M_{\rm star}$–$\mu_\mathrm{H_2}$ relation. They are highlighted with a pink outer edge in all figures. This is formally a much smaller fraction (14%) than for CL1411.1$-$1148 (37%). Nevertheless, in a similar way as for CL1411.1$-$1148, with the exception of one galaxy, all our targets fall on the low $1\times \sigma_{\rm H_2}$ part of the $M_{\rm star}$–$\mu_\mathrm{H_2}$ relation, possibly reflecting the fact that our sample does not contain galaxies with SFRs above the MS (Figs. [5](#MScl1301) and [7](#histograms)).

Figure [9](#sSFR_fg) presents the relation between $\mu_\mathrm{H_2}$ and sSFR normalised to the galaxy position on the MS. Two of the low-$\mu_\mathrm{H_2}$ galaxies are located on the MS, and one falls below it. This latter system, EDCSNJ1301344$-$1142380, is a cluster member. It is interesting to see that while its star formation activity is diminished and its gas content is correspondingly low for its stellar mass, it lies however at the same level of $\mu_\mathrm{H_2}$ as other (more massive) MS galaxies in Fig. [9](#sSFR_fg). However, cluster members are not necessarily depleted in cold gas. Indeed, as alluded in Section [\[MS_SFR\]](#MS_SFR), the galaxies below the MS are linked to the cluster environment, and this is before their reservoir of cold gas is impacted for two of them.

The other low-$\mu_\mathrm{H_2}$ cluster member is EDCSNJ1301383$-$1140011, and still is on the MS, but on the lower edge. The third low-$\mu_\mathrm{H_2}$ galaxy is SEDCSJ1300234$-$1132052  again on the MS and on the lower edge. It is located far from the cluster core (r $> 5.5 R_{200}$) and does not belong to any identified overdensity.

We performed a Anderson–Darling (A-D) test (cite: Scholz1987) between the $\mu_\mathrm{H_2}$ distributions of the MS PHIBSS2 and CL1411.1$-$1148 galaxies. It results in $p = 0.021$, meaning that there is only a 2.1% chance that the two samples arise from the same $\mu_\mathrm{H_2}$ distribution. Similarly, combining both CL1301.7$-$1139 and CL1411.1$-$1148 gives p-value of 0.011, suggesting that these samples are not drawn from a PHIBSS2-like population at a 98.9% confidence level.

![](muh2_vs_ssfrn_1301_vfin6c.png)

![](r_vs_deltaz_bothclusters_finalest_v2.png)

## Comparison with CL1411.1$-$1148 

The difference in the fraction of low-$\mu_\mathrm{H_2}$ galaxies in CL1301.7$-$1139 and CL1411.1$-$1148 is puzzling, given their similar properties in mass, redshift, and the identical target selection criteria that we applied. As seen in Fig. [5](#MScl1301), the ALMA targets linked to CL1411.1$-$1148 span a slightly more extended stellar mass range than those linked to CL1301.7$-$1139. However their distributions have the same median, log($M_{\rm star}$/$M_\ensuremath{\odot}$) = 10.69 and 10.6, respectively. Some of the CL1301.7$-$1139 ALMA targets have diminished SFRs, placing them further below the MS than in the case of CL1411.1$-$1148, but these galaxies do not form the bulk of the low-$\mu_\mathrm{H_2}$ systems. Therefore, the origin of the difference between the two samples must be found elsewhere.

Figure [10](#psd) shows the projected phase-space diagrams of the two clusters. Following (cite: Jaffe2015), we assumed a NFW halo profile with a concentration of ${\rm c} = 6$ to compute the escape velocity for our clusters (dotted lines). Here, we only look at star-forming galaxies as identified from the $UVJ$ or $ugi$ diagrams (black dots), because they are the galaxies for which we can define the low-$\mu_\mathrm{H_2}$ systems. The spectroscopic members, including the ALMA targets, within 4 $\sigma_{cl}$ and $8 \times R_{200}$, are seen relatively to the virialised, infall, and escape region boundaries (cite: Mahajan2011). Galaxies are considered infalling onto the clusters when they are located between 1 and $\sim 5$ virial radii (cite: Oman2013; Albaek2017). The difference between the two samples stands out: most of the ALMA targets are located inside the CL1411.1$-$1148 infall region, while they are much more spatially scattered in the case of CL1301.7$-$1139. Furthermore, all low-$\mu_\mathrm{H_2}$ galaxies are located either inside or very close to the cluster core, or again within or very close to the CL1411.1$-$1148 infalling region. Leaving aside the clusters themselves, these low-$\mu_\mathrm{H_2}$ galaxies represent 44% of the full infalling population, and 66% of the galaxies located between 1 and $4 \times R_{200}$. Applying these fractions to CL1301.7$-$1139  we could in principle have expected 1 or 2 low $\mu_\mathrm{H_2}$ infalling galaxies however, we found none. This absence most likely reflects the fluctuations induced by low number statistics, given that we only observed three CL1301.7$-$1139 star-forming galaxies between 1 and $4 \times R_{200}$. This is a strong hint that the population of low-$\mu_\mathrm{H_2}$ galaxies are preferentially induced by the cluster environment. The interplay between the removal of the cold gas reservoir, or at least the change in its properties, and the decrease in SFR is subtle and difficult to catch in the act. The cluster infall regions seem to be the best place to look for them and identify the physical processes at play. Future follow-up studies of the same type will assess the significance and origin of the transformation of galaxies along their path to the cluster cores.

# Conclusion

We have presented the analysis of the molecular gas content, derived from ALMA CO(3-2) line observations, of a sample of 22 galaxies located within CL1301.7$-$1139 ($z=0.4828$, $\sigma_{\rm cl}=681$ km s$^{-1}$) and in its surrounding large-scale structure. Unlike previous works, our sample selection does not impose a minimum galaxy SFR or detection in FIR. As such and as much as possible, it delivers an unbiased view of the gas content of normal star-forming galaxies at $z\sim0.5$. At the same time, it offers insight into the status of the molecular gas content of galaxies in interconnected cosmic structures. Our study highlights the variety of paths to star formation quenching, and most likely the variety of physical properties (i.e. temperature, density) of the corresponding galaxy cold molecular gas.

Similar to our first results on the analysis of the large-scale structure around CL1411.1$-$1148 presented in , although to a smaller extent, our observations in CL1301.7$-$1139 reveal a larger number of star-forming galaxies with lower gas fraction, at fixed stellar mass, than what had been found in previous surveys at comparable redshifts.

The cluster environment does not necessarily affect the galaxy molecular gas content. Eight of our ALMA targets are bona fide CL1301.7$-$1139 members (r $\lesssim R_{200}$ and v/$\sigma_{cl} \lesssim 1$). From those, only two show signs of lower gas fractions for their stellar masses when compared to the relation between these two quantities derived for field galaxies. One of them is nevertheless still on the star-forming MS, hence with a normal activity. The second system shows evidence of transition towards the passive sequence.

Star formation and cold gas content are indeed not always linked in a straightforward manner. Three of our ALMA targets fall below the $-0.3$ dex boundary of the star-forming MS. These are systems in the transition region between star-forming and passive systems. While two of those are bona fide cluster members, the third one is infalling. Only one of the cluster members mentioned above has a low gas fraction for its stellar mass, the other two galaxies are normal despite their lowered star-forming activity and irrespective of their location.

Three galaxies turn out to be on the passive sequence (log(SFR) $\lesssim-0.2$) and only have upper limits on their CO fluxes. The lack of star formation activity and their CO deficiency does not seem to be driven by morphology (internal quenching). Indeed, similar systems in our sample, without evidence of disks nevertheless have well measured CO fluxes.

The comparison with CL1411.1$-$1148 highlights the enhanced fraction of galaxies with low gas fraction, compared to the field and at a fixed stellar mass in the cluster infall region. This provides a strong hint of environmental dependence and stresses the need for the extension of this type of investigation to a larger number of clusters and their related large-scale structures.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00257.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The authors are indebted to the *International Space Science Institute* (ISSI), Bern, Switzerland, for supporting and funding the international team ‘The Effect of Dense Environments on Gas in Galaxies over 10 Billion Years of Cosmic Time’. We are grateful to the `Numpy` (cite: numpy:2006; numpy:2011), `SciPy` (cite: scipy:2020), `Matplotlib` (cite: matplotlib:2007), `IPython` (cite: ipython:2007), and `Astropy` (cite: astropy:2013; astropy:2018) teams for providing the scientific community with essential Python tools.

101 natexlab

(ref: Abdo2010) Abdo, A. A., Ackermann, M., Ajello, M., et al. 2010, ApJ, 710, 133

(ref: Planck2018) Aghanim, N., Akrami, Y., Ashdown, M., et al. 2020, A&A, 641, A6

(ref: Albaek2017) Albæk, L., Hansen, S. H., Martizzi, D., Moore, B., & Teyssier, R. 2017, MNRAS, 472, 3486

(ref: Bahe2013) Bahé, Y. M., McCarthy, I. G., Balogh, M. L., & Font, A. S. 2013, MNRAS, 430, 3017

(ref: Balogh2004) Balogh, M., Eke, V., Miller, C., et al. 2004, MNRAS, 348, 1355

(ref: Bauermeister2013a) Bauermeister, A., Blitz, L., Bolatto, A. D., et al. 2013a, ApJ, 768, 132

(ref: Bauermeister2013) Bauermeister, A., Blitz, L., Bolatto, A. D., et al. 2013b, ApJ, 763, 64

(ref: Baumgartner2013) Baumgartner, W. H., Tueller, J., Markwardt, C. B., et al. 2013, ApJS, 207, 19

(ref: Bianconi2018) Bianconi, M., Smith, G. P., Haines, C. P., et al. 2018, MNRAS Lett., 473, L79

(ref: Bigiel2008) Bigiel, F., Leroy, A., Walter, F., et al. 2008, ApJ, 136, 2846

(ref: Blanton2007a) Blanton, M. R. & Roweis, S. 2007, AJ, 133, 734

(ref: Bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Boselli2014) Boselli, A., Cortese, L., Boquien, M., et al. 2014, A&A, 564

(ref: Boselli1996) Boselli, A., Mendes de Oliveira, C., Balkowski, C., Cayatte, V., & Casoli, F. 1996, A&A, 314, 738

(ref: Brammer2008) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503

(ref: Bruzual2003) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Carleton2017) Carleton, T., Cooper, M. C., Bolatto, A. D., et al. 2017, MNRAS, 467, 4886

(ref: Castignani2021) Castignani, G., Combes, F., Jablonka, P., et al. 2021, arXiv e-prints

(ref: Castignani2020b) Castignani, G., Jablonka, P., Combes, F., et al. 2020, A&A, 640, A64

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Chapman2015) Chapman, S. C., Bertoldi, F., Smail, I., et al. 2015, MNRAS Lett., 449, L68

(ref: Charlot2000) Charlot, S. & Fall, S. M. 2000, ApJ, 539, 718

(ref: cybulski2016) Cybulski, R., Yun, M. S., Erickson, N., et al. 2016, MNRAS, 459, 3287

(ref: daCunha2008) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595

(ref: Daddi2010) Daddi, E., Bournaud, F., Walter, F., et al. 2010, ApJ, 713, 686

(ref: Daddi2004) Daddi, E., Cimatti, A., Renzini, A., et al. 2004, ApJ, 617, 746

(ref: Daddi2007) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156

(ref: Dame2001) Dame, T. M., Hartmann, D., & Thaddeus, P. 2001, ApJ, 547, 792

(ref: Dressler1980) Dressler, A. 1980, ApJ, 236, 351

(ref: Finn2005) Finn, R. A., Zaritsky, D., McCarthy, D. W., et al. 2005, ApJ, 630, 206

(ref: Freundlich2019) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2019, A&A, 622, A105

(ref: Gao2004) Gao, Y. & Solomon, P. M. 2004, ApJS, 152, 63

(ref: Garcia-Burillo2012) García-Burillo, S., Usero, A., Alonso-Herrero, A., et al. 2012, A&A, 539, A8

(ref: Geach2011) Geach, J. E., Smail, I., Moran, S. M., et al. 2011, ApJ, 730, L19

(ref: Geach2009a) Geach, J. E., Smail, I., Moran, S. M., Treu, T., & Ellis, R. S. 2009, ApJ, 691, 783

(ref: Genzel2015) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: Gomez2003) Gomez, P. L., Nichol, R. C., Miller, C. J., et al. 2003, ApJ, 584, 210

(ref: Gouin2020) Gouin, C., Aghanim, N., Bonjean, V., & Douspis, M. 2020, A&A, 635, A195

(ref: Grenier2005) Grenier, I. A., Casandjian, J. M., & Terrier, R. 2005, Sci., 307, 1292

(ref: Guzzo2018) Guzzo, L., Bel, J., Bianchi, D., et al. 2018, arXiv e-prints

(ref: Haines2015) Haines, C. P., Pereira, M. J., Smith, G. P., et al. 2015, ApJ, 806, 101

(ref: Hayashi2018) Hayashi, M., Tadaki, K.-I., Kodama, T., et al. 2018, ApJ, 856, 118

(ref: matplotlib:2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: Jablonka2013) Jablonka, P., Combes, F., Rines, K., Finn, R., & Welch, T. 2013, A&A, 557, 8

(ref: Jachym2014) Jachym, P., Combes, F., Cortese, L., Sun, M., & Kenney, J. D. P. 2014, ApJ, 792, 11

(ref: Jachym2017) Jachym, P., Sun, M., Kenney, J. D. P., et al. 2017, ApJ, 839, 114

(ref: Jaffe2015) Jaffé, Y. L., Smith, R., Candlish, G. N., et al. 2015, MNRAS, 448, 1715

(ref: Just2019) Just, D. W., Kirby, M., Zaritsky, D., et al. 2019, ApJ, 885, 6

(ref: Kauffmann2004) Kauffmann, G., White, S. D., Heckman, T. M., et al. 2004, MNRAS, 353, 713

(ref: Koyama2017) Koyama, S., Koyama, Y., Yamashita, T., et al. 2017, ApJ, 847, 137

(ref: Kroupa2001) Kroupa, P. 2001, MNRAS, 322, 231

(ref: Laigle2018) Laigle, C., Pichon, C., Arnouts, S., et al. 2018, MNRAS, 474, 5437

(ref: Lamperti2020) Lamperti, I., Saintonge, A., Koss, M., et al. 2020, ApJ, 889, 103

(ref: Lee2017) Lee, B., Chung, A., Tonnesen, S., et al. 2017, MNRAS, 466, 1382

(ref: Leroy2011) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12

(ref: Leroy2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: Lisenfeld2017) Lisenfeld, U., Alatalo, K., Zucker, C., et al. 2017, A&A, 607, A110

(ref: Mahajan2011) Mahajan, S., Mamon, G. A., & Raychaudhury, S. 2011, MNRAS, 416, 2882

(ref: Malavasi2016) Malavasi, N., Pozzetti, L., Cucciati, O., Bardelli, S., & Cimatti, A. 2016, A&A, 585, A116

(ref: Martinez2012) Martinez-Badenes, V., Lisenfeld, U., Espada, D., et al. 2012, A&A, 540, A96

(ref: McGee2009) McGee, S. L., Balogh, M. L., Bower, R. G., Font, A. S., & McCarthy, I. G. 2009, MNRAS, 400, 937

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astron. Soc. Pacific Conf. Ser., 376, 127

(ref: Miller2003) Miller, C. J., Nichol, R. C., Gomez, P. L., Hopkins, A. M., & Bernardi, M. 2003, ApJ, 597, 142

(ref: Milvang-Jensen2008) Milvang-Jensen, B., Noll, S., Halliday, C., et al. 2008, A&A, 482, 419

(ref: Mishra2020) Mishra, H. D. & Dai, X. 2020, AJ, 159, 69

(ref: Morokuma-Matsui2015) Morokuma-Matsui, K., Baba, J., Sorai, K., & Kuno, N. 2015, PASJ, 67, 36

(ref: Morokuma-Matsui2021) Morokuma-Matsui, K., Kodama, T., Morokuma, T., et al. 2021, arXiv e-prints

(ref: Navarro1996) Navarro, J. F., Frenk, C. S., & White, S. D. M. 1996, ApJ, 462, 563

(ref: Noble2017) Noble, A. G., McDonald, M., Muzzin, A., et al. 2017, ApJ, 842, L21

(ref: Noble2019) Noble, A. G., Muzzin, A., McDonald, M., et al. 2019, ApJ, 870, 56

(ref: numpy:2006) Oliphant, T. E. 2006, A guide to NumPy, Vol. 1 (Trelgol Publishing USA)

(ref: Oman2013) Oman, K. A., Hudson, M. J., & Behroozi, P. S. 2013, MNRAS, 431, 2307

(ref: Peng2010) Peng, Y.-j., Lilly, S. J., Kovac, K., et al. 2010, ApJ, 721, 193

(ref: ipython:2007) Pérez, F. & Granger, B. E. 2007, Computing in Science and Engineering, 9, 21

(ref: astropy:2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123

(ref: Riess2019) Riess, A. G., Casertano, S., Yuan, W., Macri, L. M., & Scolnic, D. 2019, ApJ, 876, 85

(ref: astropy:2013) Robitaille, T. P., Tollerud, E. J., Greenfield, P., et al. 2013, A&A, 558, A33

(ref: Rudnick2017a) Rudnick, G., Hodge, J., Walter, F., et al. 2017a, ApJ, 849, 27

(ref: Rudnick2017) Rudnick, G., Jablonka, P., Moustakas, J., et al. 2017b, ApJ, 850, 181

(ref: Saintonge2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22

(ref: Sanchez-Blazquez2009) Sánchez-Blázquez, P., Jablonka, P., Noll, S., et al. 2009, A&A, 499, 47

(ref: Scholz1987) Scholz, F. W. & Stephens, M. A. 1987, J. Am. Stat. Assoc., 82, 918

(ref: Schruba2011) Schruba, A., Leroy, A. K., Walter, F., et al. 2011, ApJ, 142, 37

(ref: Scott2015) Scott, T. C., Usero, A., Brinks, E., et al. 2015, MNRAS, 453, 328

(ref: Skrutskie2006) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163

(ref: Smith2005) Smith, G. P., Treu, T., Ellis, R. S., Moran, S. M., & Dressler, A. 2005, ApJ, 620, 78

(ref: Solomon2005) Solomon, P. & Vanden Bout, P. 2005, ARA&A, 43, 677

(ref: Solomon1997) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, ApJ, 478, 144

(ref: Song2021) Song, H., Laigle, C., Hwang, H. S., et al. 2021, MNRAS, 501, 4635

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Sperone-Longin2021) Spérone-Longin, D., Jablonka, P., Combes, F., et al. 2021, A&A, 647, A156

(ref: Spilker2018) Spilker, J., Bezanson, R., Barišić, I., et al. 2018, ApJ, 860, 103

(ref: Tacconi2010) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781

(ref: Tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tacconi2013) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768

(ref: numpy:2011) Van Der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science & Engineering, 13, 22

(ref: scipy:2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: White2005) White, S. D., Clowe, D. I., Simard, L., et al. 2005, A&A, 444, 365

(ref: Williams2009) Williams, R. J., Quadri, R. F., Franx, M., Van Dokkum, P., & Labbé, I. 2009, ApJ, 691, 1879

(ref: Wuyts2011a) Wuyts, S., Förster Schreiber, N. M., Lutz, D., et al. 2011, ApJ, 738, 106

(ref: Zahid2012) Zahid, H. J., Dima, G. I., Kewley, L. J., Erb, D. K., & Davé, R. 2012, ApJ, 757, 54

# ALMA maps and spectra of our galaxies 

In this appendix, we present the $i$-band images, the ALMA intensity maps and the spectra of all of our targets. The low $\mu_\mathrm{H_2}$ targets are indicated as such by a label on the bottom left of their $i$-band image.

![image](cl1301_03_i_b.pdf) ![image](cl1301_03_alma_map_binned.pdf) ![image](cl1301_03_alma_spectrum_binned.pdf)

![image](cl1301_16_i_b.pdf) ![image](cl1301_16_alma_map_binned.pdf) ![image](cl1301_16_alma_spectrum_binned.pdf)

![image](cl1301_13_i_b.pdf) ![image](cl1301_13_alma_map_binned.pdf) ![image](cl1301_13_alma_spectrum_binned.pdf)

![image](cl1301_18_i_b.pdf) ![image](cl1301_18_alma_map_binned.pdf) ![image](cl1301_18_alma_spectrum_binned.pdf)

![image](cl1301_23_i_b.pdf) ![image](cl1301_23_alma_map_binned.pdf) ![image](cl1301_23_alma_spectrum_binned.pdf)

![image](cl1301_22_i_b.pdf) ![image](cl1301_22_alma_map_binned.pdf) ![image](cl1301_22_alma_spectrum_binned.pdf)

![image](cl1301_01_i_b.pdf) ![image](cl1301_01_alma_map_binned.pdf) ![image](cl1301_01_alma_spectrum_binned.pdf)

![image](cl1301_14_i_b.pdf) ![image](cl1301_14_alma_map_binned.pdf) ![image](cl1301_14_alma_spectrum_binned.pdf)

![image](cl1301_19_i_b.pdf) ![image](cl1301_19_alma_map_binned.pdf) ![image](cl1301_19_alma_spectrum_binned.pdf)

![image](cl1301_06_i_b.pdf) ![image](cl1301_06_alma_map_binned.pdf) ![image](cl1301_06_alma_spectrum_binned.pdf)

![image](cl1301_10_i_b.pdf) ![image](cl1301_10_alma_map_binned.pdf) ![image](cl1301_10_alma_spectrum_binned.pdf)

![image](cl1301_10b_i_b.pdf) ![image](cl1301_10b_alma_map_binned.pdf) ![image](cl1301_10b_alma_spectrum_binned.pdf)

![image](cl1301_05_i_b.pdf) ![image](cl1301_05_alma_map_binned.pdf) ![image](cl1301_05_alma_spectrum_binned.pdf)

![image](cl1301_02_i_b.pdf) ![image](cl1301_02_alma_map_binned.pdf) ![image](cl1301_02_alma_spectrum_binned.pdf)

![image](cl1301_09_i_b.pdf) ![image](cl1301_09_alma_map_binned.pdf) ![image](cl1301_09_alma_spectrum_binned.pdf)

![image](cl1301_17_i_b.pdf) ![image](cl1301_17_alma_map_binned.pdf) ![image](cl1301_17_alma_spectrum_binned.pdf)

![image](cl1301_08_i_b.pdf) ![image](cl1301_08_alma_map_binned_b.pdf) ![image](cl1301_08_alma_spectrum_binned_b.pdf)

![image](cl1301_07_i_b.pdf) ![image](cl1301_07_alma_map_binned.pdf) ![image](cl1301_07_alma_spectrum_binned.pdf)

![image](cl1301_11_i_b.pdf) ![image](cl1301_11_alma_map_binned.pdf) ![image](cl1301_11_alma_spectrum_binned.pdf)

![image](cl1301_12_i_b.pdf) ![image](cl1301_12_alma_map_binned.pdf) ![image](cl1301_12_alma_spectrum_binned.pdf)

![image](cl1301_15_i_b.pdf) ![image](cl1301_15_alma_map_binned.pdf) ![image](cl1301_15_alma_spectrum_binned.pdf)

![image](cl1301_04_i_b.pdf) ![image](cl1301_04_alma_map_binned.pdf) ![image](cl1301_04_alma_spectrum_binned.pdf)

[^1]: For consistency with previous EDisCS works, R$_{200}$ was calculated from the cluster line-of-sight velocity dispersion, as in (cite: Finn2005)

[^2]: <http://www.iram.fr/IRAMFR/GILDAS>

[^3]: <http://www.iap.fr/magphys/index.html>

</paper>

Write the methods card for this paper.