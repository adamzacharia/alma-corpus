# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...670L...8G\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Reflections on nebulae around young stars

While it is generally assumed that Class II sources evolve largely in isolation from their environment, many still lie close to molecular clouds and may continue to interact with them. This may result in late accretion of material onto the disk that can significantly influence disk processes and planet formation.

In order to systematically study late infall of gas onto disks, we identify candidate Class II sources in close vicinity to a reflection nebula (RN) that may be undergoing this process.

First we targeted Class II sources with known kilo-au scale gas structures – possibly due to late infall of material – and we searched for RNe in their vicinity in optical and near-infrared images. Second, we compiled a catalogue of Class II sources associated with RNe and looked for the large-scale CO structures in archival ALMA data. Using the catalogues of protostars and RNe, we also estimated the probability of Class II sources interacting with surrounding material.

All of the sources with large-scale gas structures also exhibit some reflection nebulosity in their vicinity. Similarly, at least five Class II objects associated with a prominent RNe, and for which adequate ALMA observations are available, were found to have spirals or stream-like structures which may be due to late infall. We report the first detection of these structures around S CrA.

Our results suggest that a non-negligible fraction of Class II disks in nearby star-forming regions may be associated with RNe and could therefore be undergoing late accretion of gas. Surveys of RNe and kilo-au scale gas structures around Class II sources will allow us to better understand the frequency and impact of late-infall phenomena.

# Motivation

Most stars are born in groups in giant molecular clouds through the gravitational collapse of dense molecular cores (cite: McKee2007).

As these protostellar systems evolve from the Class 0/I to the Class II stage, the surrounding gaseous envelope is thought to be completely dispersed and, traditionally, Class II systems are believed to evolve in general isolation to form planetary systems.

However, in reality, these systems are still in the vicinity of molecular clouds on large scales ($\gtrsim1$ pc) and may continue to dynamically interact with them. Such interactions were observed in younger Class 0/I objects, where 1000 au scale streamers of molecular gas infalling onto the protostar were detected (cite: Pineda2020; Garufi2022). There have been some recent serendipitous detections of $\sim1000$ au, generally stream-like, gaseous structures around Class II disks too, which are likely due to such interactions (cite: Tang2012; Ginski2021; Huang2020; Huang2021; Huang2022).

Late infall of material can greatly influence the physical and chemical properties of Class II disks, and thus, of the planets they form. For example, the supply of fresh material can help solve the ‘mass-budget problem’ of planet-forming disks

(cite: Manara2018; Mulders2021),

and explain the observed chemical diversity among meteorites (cite: Nanne2019N). (cite: Thies2011) and (cite: Kuffmeier2021) demonstrated that late infall can torque disks and explain the observed misalignment of some planetary systems. Approximated as Bondi-Hoyle accretion (cite: Bondi1944), late infall can explain the steep dependence of mass accretion on stellar mass

(cite: Padoan2005; Padoan2014).

Finally, this phenomenon may also produce disk sub-structures and instabilities as seen in

vortices (cite: Bae2015; Kuznetsova2022), spiral waves (cite: Hennebelle2017; Kuffmeier2018), and FU Orionis outbursts (cite: Dullemond2019).

A characterisation of the frequency and efficiency of late infall is therefore crucial for establishing a holistic view of the star and planet formation process. Simulations suggest that a signpost of such accretion events could be $\sim10^3$ au-scale arc-shaped structures, generally referred to as ‘streamers’ (cite: Kuffmeier2020). However, only a few have been detected, mainly because these spatial scales lie at the limits of single-dish resolution and they are largely filtered out in interferometric observations designed to resolve protoplanetary disks. To comprehensively study late-stage infall, a survey of large-scale structures around Class II sources is needed and a first step in this direction would be to systematically identify suitable targets.

In order to find disks that are potentially undergoing late infall, one should first identify Class II sources that are close enough to clouds to gravitationally interact with them. Such clouds

will scatter the protostellar light in optical and near-infrared (NIR) wavelengths and appear as reflection nebulae (RNe) (cite: Hubble1922). Historically, RNe were used to identify young stellar objects (YSOs)

(cite: Cohen1980) and

they were indeed one of the original defining characteristics of T Tauri stars (cite: Joy1945). Recently, hydrodynamical simulations have demonstrated that kilo-au scale RNe can appear due to cloud-protostar interactions, some of which lead to late infall of material (cite: Dullemond2019). In this Letter we pioneer the use of RN detections close to Class II stars to identify late-infall candidates.

# Class II sources with large-scale CO structures

Large-scale non-Keplerian gaseous structures have been detected around a few Class II sources. In order to test the hypothesis that RNe might indicate late infall,

we looked for signs of nebulosity around these sources, as discussed below:

*AB Aur:* (cite: Tang2012) found four $\sim500$ au spirals around AB Aur in CO observations using the Instituto de Radioastronomía Milimétrica (IRAM) 30-m telescope, Plateau de Bure interferometer (PbDI), and Submillimeter Array (SMA). Analysis of the gas kinematics in these spirals, which seems to be counter-rotating with respect to the Keplerian disk, suggests that they are likely formed due to late-stage infall of gas. This source is also known to be associated with a bright arc-shaped RN (cite: Dullemond2019), as shown in Figure [1](#fig:known_sources) (panel a).

*SU Aur:* (cite: Akiyama2019) reported an $\sim1000$ au long tail-like streamer using the Atacama Large Millimeter/submillimeter Array (ALMA) in CO emission. Later, (cite: Ginski2021) studied the morphology of its dust tails in scattered light using

the Very Large Telescope (VLT), along with a kinematic study of CO gas, and found that the material is likely moving towards the disk. A bright RN is visible in the immediate vicinity of SU Aur (Figure [1](#fig:known_sources), panel b).

*RU Lup:* (cite: Huang2020) reported at least five CO spiral arms stretching up to $\sim1000$ au around RU Lup using ALMA observations and suggested late infall as a possible explanation. Archival Digital Sky Survey (DSS) images show faint nebulosity just north of RU Lup, as shown in Figure [1](#fig:known_sources) (panel c).

*GM Aur:* (cite: Huang2021) found extended elongated structures around GM Aur, $\sim1000$–2000 au in length, using ALMA CO observations with a morphology and kinematics indicative of late infall.

No RNe have been found in archival DSS or Panoramic Survey Telescope and Rapid Response System (Pan-STARRS) images, but there are elongated features in more sensitive Hubble Space Telescope (HST) NIR images, as reported in (cite: Schneider2003) and shown in Figure [1](#fig:known_sources) (panel d).

*DO Tau:* (cite: Huang2022) studied the kilo-au environment of DO Tau using VLT/SPHERE, HST, and ALMA observations, and found the disk to be connected to multiple $\sim1000$ au scale stream-like structures. Larger-scale Herschel observations show that these structures are probably due to an interaction with the neighbouring YSO HV Tau, but late accretion of material onto DO Tau is not ruled out. The source is associated with a prominent RN (Figure [1](#fig:known_sources), panel e).

To summarise, the five known Class II sources that have large-scale CO structures suggestive of an interaction with surrounding gas have either a prominent RN or some hints of reflection nebulosity.

Following this lead,

we exploit the association of YSOs with RNe to search for candidate Class II sources undergoing late-stage infall of material.

![](RNe_check_figure_letter.pdf)

# Class II sources near reflection nebulae

As a first step, we compiled a catalogue of RNe using the published lists in (cite: Magakian2003) and (cite: Connelley2007). (cite: Magakian2003) merged previously published RNe catalogues and presented a final list of 913 objects. Most of the sources in their list have been manually identified by visual inspection of DSS optical images. (cite: Connelley2007) surveyed 197 nearby, mostly Class I, protostars at $2.2\,\mu$m using the University of Hawaii 2.2 m telescope. They detected 106 RNe, out of which 41 were reported as new discoveries.

The fact that $\gtrsim 40\%$ of RNe were not detected before suggests that the previous RNe catalogues were rather incomplete.

For example, the prominent RNe around SU Aur (see Figure [1](#fig:known_sources), panel b) and HD 100546 (cite: Ardila2007) were not in these RNe catalogues.

(cite: Connelley2007) estimated sizes of RNe as the square root of their area

with a mean ($\mu$) and standard deviation ($\sigma$) of $\sim18\ensuremath{''}$ and $\sim15\ensuremath{''}$, respectively. Using a cross-matching radius of $30\ensuremath{''}$ ($\sim\mu+1\sigma$), we found ten RNe present in both of the catalogues. After removing duplicates,

we merged the two catalogues to have a final sample of 1009 RNe.

To avoid spurious detections and have a well-characterised sample of YSOs with RNe that can be further followed up on using molecular-line observations (as discussed in Appendix [9](#sec:discussion_future)), we focus

on nearby well-studied star-forming regions (SFRs). The regions considered in this study are listed in Table [1](#tab:sfrs) and shown in Figure [\[fig:DSSmaps\]](#fig:DSSmaps). The radii reported in the fifth column in Table [1](#tab:sfrs) were used to define circular boundaries around the central coordinates listed in the second and third columns, and they are marked with black circles in Figure [\[fig:DSSmaps\]](#fig:DSSmaps).

We found 141 sources from our catalogue of 1009 RNe within these region boundaries.

The next step was to compile a catalogue of YSOs in these regions. For this we started with the all-sky catalogue of 133980 Class I/II sources reported in (cite: Marton2016). (cite: Marton2016) analysed *WISE* and *2MASS* photometry of these sources, using the support vector machine algorithm to identify them as YSOs. For a more complete sample of nearby YSOs, we also used the list of 2966 YSOs identified using *Spitzer*’s ’cores to disks’ and ’Gould Belt’ surveys, as reported in (cite: Dunham2015). Among the SFRs considered in this study, Taurus and Orion were not part of the (cite: Dunham2015) catalogue. Using a cross-matching radius of $5\ensuremath{''}$, we found 781 common sources in both datasets. Our final catalogue consists of 136165 YSOs of which 4930 lie within the SFR boundaries.

|                  |         |         |          |         |      |     |
|:----------------:|:-------:|:-------:|:--------:|:-------:|:----:|:---:|
|       SFR        |  R.A.   |  Decl.  | Distance | Radius  | YSOs | RNe |
|                  | \[deg\] | \[deg\] |  \[pc\]  | \[deg\] |      |     |
|    Ophiuchus     | 249.07  | -23.64  |  128.0   |   6.0   | 450  | 13  |
|      Taurus      |  67.11  |  26.62  |  148.0   |   8.0   | 190  | 28  |
| Corona Australis | 287.96  | -38.11  |  155.0   |   4.0   |  80  |  6  |
|      Lupus       | 240.08  | -36.56  |  158.0   |   8.0   | 480  | 10  |
|    Chamaeleon    |  169.5  | -78.17  |  190.0   |   8.0   | 148  |  7  |
|     Perseus      |  54.21  |  31.57  |  284.0   |   4.0   | 435  | 19  |
|      Orion       |  85.2   |  -3.5   |  420.0   |   6.0   | 978  | 44  |
|     Serpens      | 277.66  |  -1.91  |  495.0   |   3.0   | 2169 | 14  |

: List of SFRs considered in this study.

Table notes: The median coordinates and distances are from (cite: Zucker2020). The last three columns refer to the radii used to define the SFR boundaries (see Figure [\[fig:DSSmaps\]](#fig:DSSmaps)) and the number of RNe and YSOs found.

The spectral indices, $\alpha$, or slope of the spectral energy distributions in the infrared regime ($\sim2$–$25~\mu$m) were given in the (cite: Dunham2015) catalogue. We used their values, $\alpha'$, corrected for foreground extinction to classify the source evolutionary state.

Similarly, we determined $\alpha$ for sources exclusively in the (cite: Marton2016) catalogue using the provided *WISE* and *2MASS* (K band) photometry, and discarding those with fitting uncertainties $>0.6$, that is roughly half of the range of values for Class II sources. In order to estimate extinction-corrected spectral indices ($\alpha'$), we computed a correction factor of -0.31 as the median of differences between all the $\alpha'$ and $\alpha$ values reported in (cite: Dunham2015).

We note that this method only provides a rough estimate of $\alpha'$ as it does not account for extinction values for individual sources.

A comparison of our $\alpha$ and $\alpha'$ values is shown in Figure [\[fig:alphas\]](#fig:alphas). Following the same classification criteria as (cite: Dunham2015), that is $-1.6 \leq \alpha' < -0.3$, 2562 out of 4930 YSOs in our SFRs were classified as Class II sources.

The next step was to cross match our list of Class II sources with the merged catalogue of RNe.

For the specific goal of this work, the cross-matching distance between a YSO and RN can be empirically estimated as the length scale from where ambient gas can be accreted onto an isolated star (cite: Bondi1944; Throop2008; Padoan2014). The typical length scale for this interaction is given as $L_{BH} = 2GM_{*}/v^{2}$, where $G$ is the gravitational constant, $M_{*}$ is the stellar mass, and $v$ is the stellar speed relative to the gas. For a stellar mass of 1 M$_{\odot}$ and typical stellar velocity of 1 km s$^{-1}$, $L_{BH}\sim2000$ au.

The 21 late-infall Class II candidates that we found using this threshold are listed in Appendix [8](#app:table).

We note that this distance threshold is a lower limit for an interaction between clouds and YSOs because we do not account for the sizes of RNe.

These show a range of physical sizes ($\sim10^3$–$10^5$ au) and have highly asymmetrical shapes (cite: Connelley2007). When mining the ALMA archive, we ignored this diversity as we aimed to identify a reliable sample of YSOs potentially interacting with RNe clouds. The implications of a more realistic distance threshold is discussed in Section [4](#sec:discussion_RNe).

#### ALMA archive search:

To target higher-quality observations, we focussed on nearby SFRs ($d \lesssim$ 200 pc), where 16 out of the 21 Class II disks near RNe are located. For these nearby sources, we searched for existing observations in the ALMA Science Archive.

We are primarily interested in $^{12}$CO emission ($J=2-1$ in Band 6 and $J=3-2$ in Band 7)

since this molecule is expected to be a good tracer of large-scale diffuse gas structures (see e.g. Figure [1](#fig:known_sources)).

We found a total of 66 Band 6 and 7 observations for 16 sources in our sample, as shown in Figure [2](#fig:almaobs).

Among these datasets, we found 13 observations with the largest angular scale (LAS) corresponding to at least 1000 au to recover the expected large-scale structures (cite: Kuffmeier2020).

As such large-scale structures are expected to have low column densities, and therefore faint emission, the observational sensitivity is important. We selected a subset of five observations with rms noise (over a channel width of $10$ km s$^{-1}$) smaller than a $2.3$ mJy beam$^{-1}$, equal to the line sensitivity reported in the ALMA archive for SU Aur observations (cite: Ginski2021). For the typical angular resolution of $0.7\ensuremath{''}$ for these observations, the sensitivity threshold of the $2.3$ mJy beam$^{-1}$ corresponds to $\sim100$ mK. The sensitivity and recoverable scale thresholds are marked as dashed-grey lines in Figure [2](#fig:almaobs).

Among these five observations, two targeted HD 142527 (Figure [2](#fig:almaobs), red circles), a well-studied binary Class II system.

These data have been published and show non-Keplerian spiral structures extending to $\sim700$ au, beyond the disk radius of $\sim200$–$300$ au (cite: Christiaens2014; Garg2021), as shown in Figure [3](#fig:rne_sources) (panel a). Similar structures have also been observed in optical and NIR images (cite: Casassus2012; Hunziker2021). (cite: Christiaens2014) suggested that the innermost spiral can be explained by acoustic waves due to an embedded companion; however, the origin of the outer spirals is less clear, and stellar encounters and gravitational instabilities have been suggested as possible causes. We note that spiral structures have been predicted to form due to late infall (cite: Hennebelle2017; Kuffmeier2017; Kuffmeier2018) and a detailed kinematic analysis can be done to distinguish among these scenarios, as discussed in Appendix [9](#sec:discussion_future). HD 142527 also exhibits inner and outer disk misalignment (cite: Bohn2022), which can be explained by late infall (cite: Thies2011; Kuffmeier2021).

The other three datasets are of S CrA, HD 97048, and Sz 68. The selected large-scale observation for Sz 68 (Project 2019.1.01135.S) does not cover any CO lines and is therefore not discussed further. For S CrA (Project 2019.1.01792.S) and HD 97048 (Project 2015.1.00192.S), we used the standard pipeline calibration and imaged the $^{12}$CO (2–1) data using CASA 6.4. For both datasets, imaging was carried out using ’briggs’ weighting with robust=0.5, a cell size of 0.05$''$, and ’auto-multithresh’ masking with default parameters. The resulting integrated intensity (moment 0) maps and intensity-weighted velocity (moment 1) maps are shown in Figure [3](#fig:rne_sources) (panel b and c). Appendix [11](#app:channel_maps) shows corresponding channel maps for both of the datasets.

For S CrA, at least one $\sim1000$ au streamer is clearly visible (solid cyan line), north-west of the binary disks (green contours), as seen in the moment 0 map (Figure [3](#fig:rne_sources), panel b, middle panel). This streamer seems to be redshifted with respect to the disk emission, as seen in the corresponding moment 1 map (see Figure [3](#fig:rne_sources), panel b, right panel and channels from 12.93 to 8.57 km s$^{-1}$ in Figure [5](#fig:scra_channels)). Furthermore, there are hints of two more streamers, denoted as dashed-cyan lines in the moment 0 map (Figure [3](#fig:rne_sources), panel b, middle panel). This is the first discovery of large-scale streamers around S CrA. As discussed in Section [2](#sec:knownsources), such elongated structures can form due to the late infall of material, but they could also be a consequence of a binary interaction. Further analysis is required to ascertain the dynamical nature of these features and will follow in a future publication.

For HD 97048, no clear streamers are visible in the moment 0 map (Figure [3](#fig:rne_sources), panel c, middle panel).

However, significant negative emission was observed in the central channels (Figure [6](#fig:hd97048_channels), channels 5.32 to 3.57 km s$^{-1}$), suggesting that the source may be surrounded by large-scale gas that may absorb or otherwise obscure, through spatial filtering, kilo-au features around the star.

These initial results suggest that at least two (HD 142527 and S CrA) out of the three Class II sources associated with RNe, and with good-enough ALMA data, exhibit large-scale spirals or streamer-like structures, as are expected to form due to cloud-disk interactions, particularly late-stage infall of material (cite: Hennebelle2017; Dullemond2019; Kuffmeier2017; Kuffmeier2020; Kuznetsova2020). These two sources are in addition to the already known similar sources discussed in Section [2](#sec:knownsources). Other possible explanations for these large-scale structures are discussed in Appendix [10](#sec:discussion_other). Irrespective of the actual origin of such features, it is promising to see that large-scale gas emission is found around YSOs close to RNe. This may indicate that an association with RNe can be used to look for similar structures around a wider population of Class II disks, as discussed further in Section [4](#sec:discussion_RNe).

![](ALMAObs3.png)

![](CO_structure_check_figure_letter.pdf)

# Discussion

We have found 21 Class II sources associated with RNe in the SFRs listed in Table [1](#tab:sfrs), using a distance threshold of $\sim2000$ au, equivalent to the typical Bondi-Hoyle accretion length scale. However, this distance threshold does not account for the observed range of physical extents and asymmetric shapes of RNe. (cite: Connelley2007) provided angular sizes and distances for RNe in their catalogue, which correspond to a mean radius $\sim10^4$ au.

The exact distances between the centres of YSOs and RNe that result in late infall can vary greatly for different sources depending on their stellar (mass and velocity) and RNe properties (size and shape) and it is likely that more Class II sources in our sample may be interacting with neighbouring material than discussed here.

Figure [4](#fig:OffsetDist) plots the fraction of Class II sources

and all YSOs

associated with RNe as a function of the offset distance for different SFRs. Considerable differences can be seen in the association probability of YSOs with RNe for different SFRs, mostly due to different catalogue completeness levels.

The incompleteness of the available RNe catalogues is a major obstacle in providing reliable statistics at the moment (see discussion in Sec. [3](#sec:RNesources)). However, even with this limitation, it is clear that there are potentially many Class II disks interacting with their parent cloud. For at least four SFRs (Taurus, Lupus, Corona Aurstralis, and Chamaeleon), $\sim5$–$10\%$ of Class II sources are close-enough ($\lesssim 10^4$ au) to RNe. If the threshold is slightly increased to $\lesssim 4\times 10^4$ au, $\sim50\%$ of Class II sources in Corona Aurstralis would be associated with a RN, and therefore potentially accreting material from the ambient cloud.

Accounting for stellar kinematics, the number of Class II systems that pass by RNe at some point in their lifetime could be even greater. If an association with RNe is indeed related to late infall, this may be an important phenomenon

especially since it can have important implications for disk evolution and planet formation, as described in Section [1](#sec:motivation). To further test the tentative link between RNe and an interaction between disks and surrounding clouds, a survey of structures and kinematics around Class II sources with known RNe is needed,

as discussed in Appendix [9](#sec:discussion_future). Coupled with a better RNe catalogue, such a survey will allow us to understand how frequent late infall is for Class II sources.

# Conclusions

In this Letter we pioneer the use of the detections of RNe close to Class II stars to identify late-infall candidates. We find that all of the sources with known large-scale CO structures, where late infall is invoked as a possible explanation, also exhibit some reflection nebulosity at OIR wavelengths. Furthermore, at least five out of the six sources which are associated with a prominent RNe and for which adequate ALMA observations are available – that is, known sources AB Aur, SU Aur, and DO Tau along with independently identified sources S CrA and HD 142527 – exhibit some large scale structure that may be indicative of late infall.

This per se suggests that association with RNe may be used to identify candidate Class II sources undergoing late-stage infall of material. Finally, in nearby SFRs, the fraction of Class II sources associated with RNe can be as large as $50\%$, depending on the distance threshold, but a proper statistical analysis is still pending improved RNe catalogues. If RNe are indeed related to late infall, this suggests that a significant fraction of Class II sources could be undergoing this phenomenon, with a non-negligible impact on disk evolution and planet formation. The catalogue of potential late accretors obtained serves as a starting point for more systematic studies of late infall onto disks.

# Acknowledgements

This work was partly funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - 325594231.

Funded by the European Union under the European Union’s Horizon Europe Research & Innovation Programme 101039452 (WANDA).

T.B. acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme under grant agreement No 714769 and funding by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) under grants 361140270, 325594231 (FOR 2634/2), and Germany’s Excellence Strategy - EXC-2094 - 390783311.

M.K. gratefully acknowledges that this project has received funding from the European Union’s Framework Programme for Research and Innovation Horizon 2020 (2014–2020) under the Marie Skłodowska-Curie Grant Agreement No. 897524.

This work was partly supported by the Italian Ministero dell’Istruzione, Università e Ricerca through the grant Progetti Premiali 2012-iALMA (CUP C52I13000140001), by the DFG Cluster of Excellence Origins (www.origins-cluster.de). This project has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No 823823 (DUSTBUSTERS) and from the European Research Council (ERC) via the ERC Synergy Grant ECOGAL (grant 855130).

Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00192.S and ADS/JAO.ALMA#2019.1.01792.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This work made use of Astropy:[^2] a community-developed core Python package and an ecosystem of tools and resources for astronomy (cite: astropy:2013; astropy:2018; astropy:2022).

59 natexlab

(ref: Akiyama2019) Akiyama, E., Vorobyov, E. I., Liu, H. B., et al. 2019, AJ, 157, 165

(ref: Ardila2007) Ardila, D. R., Golimowski, D. A., Krist, J. E., et al. 2007, ApJ, 665, 512

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, apj, 935, 167

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Bae2015) Bae, J., Hartmann, L., & Zhu, Z. 2015, ApJ, 805, 15

(ref: Bohn2022) Bohn, A. J., Benisty, M., Perraut, K., et al. 2022, A&A, 658, A183

(ref: Bondi1944) Bondi, H. & Hoyle, F. 1944, MNRAS, 104, 273

(ref: Casassus2012) Casassus, S., Perez M., S., Jordán, A., et al. 2012, ApJL, 754, L31

(ref: Christiaens2014) Christiaens, V., Casassus, S., Perez, S., van der Plas, G., & Ménard, F. 2014, ApJL, 785, L12

(ref: Cohen1980) Cohen, M. 1980, AJ, 85, 29

(ref: Connelley2007) Connelley, M. S., Reipurth, B., & Tokunaga, A. T. 2007, AJ, 133, 1528

(ref: Cuello2019) Cuello, N., Dipierro, G., Mentiplay, D., et al. 2019, MNRAS, 483, 4114

(ref: Dong2015) Dong, R., Hall, C., Rice, K., & Chiang, E. 2015, ApJL, 812, L32

(ref: Dong2022) Dong, R., Liu, H. B., Cuello, N., et al. 2022, Nature Astronomy, 6, 331

(ref: Dullemond2019) Dullemond, C. P., Küffmeier, M., Goicovic, F., et al. 2019, A&A, 628, A20

(ref: Dunham2015) Dunham, M. M., Allen, L. E., Evans, Neal J., I., et al. 2015, ApJS, 220, 11

(ref: Garg2021) Garg, H., Pinte, C., Christiaens, V., et al. 2021, MNRAS, 504, 782

(ref: Garufi2022) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104

(ref: Ginski2021) Ginski, C., Facchini, S., Huang, J., et al. 2021, ApJL, 908, L25

(ref: Hall2020) Hall, C., Dong, R., Teague, R., et al. 2020, ApJ, 904, 148

(ref: Harsono2011) Harsono, D., Alexander, R. D., & Levin, Y. 2011, MNRAS, 413, 423

(ref: Hennebelle2017) Hennebelle, P., Lesur, G., & Fromang, S. 2017, A&A, 599, A86

(ref: Huang2020) Huang, J., Andrews, S. M., Öberg, K. I., et al. 2020, ApJ, 898, 140

(ref: Huang2021) Huang, J., Bergin, E. A., Öberg, K. I., et al. 2021, ApJS, 257, 19

(ref: Huang2022) Huang, J., Ginski, C., Benisty, M., et al. 2022, ApJ, 930, 171

(ref: Hubble1922) Hubble, E. P. 1922, ApJ, 56, 400

(ref: Hunziker2021) Hunziker, S., Schmid, H. M., Ma, J., et al. 2021, A&A, 648, A110

(ref: Joy1945) Joy, A. H. 1945, ApJ, 102, 168

(ref: Kuffmeier2021) Kuffmeier, M., Dullemond, C. P., Reissl, S., & Goicovic, F. G. 2021, A&A, 656, A161

(ref: Kuffmeier2018) Kuffmeier, M., Frimann, S., Jensen, S. S., & Haugbølle, T. 2018, MNRAS, 475, 2642

(ref: Kuffmeier2020) Kuffmeier, M., Goicovic, F. G., & Dullemond, C. P. 2020, A&A, 633, A3

(ref: Kuffmeier2017) Kuffmeier, M., Haugbølle, T., & Nordlund, Å. 2017, ApJ, 846, 7

(ref: Kurtovic2018) Kurtovic, N. T., Pérez, L. M., Benisty, M., et al. 2018, ApJL, 869, L44

(ref: Kuznetsova2022) Kuznetsova, A., Bae, J., Hartmann, L., & Mac Low, M.-M. 2022, ApJ, 928, 92

(ref: Kuznetsova2020) Kuznetsova, A., Hartmann, L., & Heitsch, F. 2020, ApJ, 893, 73

(ref: Magakian2003) Magakian, T. Y. 2003, A&A, 399, 141

(ref: Manara2018) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3

(ref: Marton2016) Marton, G., Tóth, L. V., Paladini, R., et al. 2016, MNRAS, 458, 3479

(ref: McKee2007) McKee, C. F. & Ostriker, E. C. 2007, ARA&A, 45, 565

(ref: Mulders2021) Mulders, G. D., Pascucci, I., Ciesla, F. J., & Fernandes, R. B. 2021, ApJ, 920, 66

(ref: Murillo2022) Murillo, N. M., van Dishoeck, E. F., Hacar, A., Harsono, D., & Jørgensen, J. K. 2022, A&A, 658, A53

(ref: Nanne2019N) Nanne, J. A. M., Nimmo, F., Cuzzi, J. N., & Kleine, T. 2019, Earth and Planetary Science Letters, 511, 44

(ref: Padoan2014) Padoan, P., Haugbølle, T., & Nordlund, Å. 2014, ApJ, 797, 32

(ref: Padoan2005) Padoan, P., Kritsuk, A., Norman, M. L., & Nordlund, Å. 2005, ApJL, 622, L61

(ref: Pineda2020) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158

(ref: Rodriguez2018) Rodriguez, J. E., Loomis, R., Cabrit, S., et al. 2018, ApJ, 859, 150

(ref: Schneider2003) Schneider, G., Wood, K., Silverstone, M. D., et al. 2003, AJ, 125, 1467

(ref: Stolker2016) Stolker, T., Dominik, C., Min, M., et al. 2016, A&A, 596, A70

(ref: Tang2012) Tang, Y. W., Guilloteau, S., Piétu, V., et al. 2012, A&A, 547, A84

(ref: Thieme2022) Thieme, T. J., Lai, S.-P., Lin, S.-J., et al. 2022, ApJ, 925, 32

(ref: Thies2011) Thies, I., Kroupa, P., Goodwin, S. P., Stamatellos, D., & Whitworth, A. P. 2011, MNRAS, 417, 1817

(ref: Throop2008) Throop, H. B. & Bally, J. 2008, AJ, 135, 2380

(ref: Toomre1964) Toomre, A. 1964, ApJ, 139, 1217

(ref: Valdivia-Men2022) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2022, arXiv e-prints, arXiv:2208.01023

(ref: Vorobyov2020) Vorobyov, E. I., Skliarevskii, A. M., Elbakyan, V. G., et al. 2020, A&A, 635, A196

(ref: Yen2019) Yen, H.-W., Gu, P.-G., Hirano, N., et al. 2019, ApJ, 880, 69

(ref: Zapata2020) Zapata, L. A., Rodrı́guez, L. F., Fernández-López, M., et al. 2020, ApJ, 896, 132

(ref: Zucker2020) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2020, A&A, 633, A51

# Star-forming regions

Figure [\[fig:DSSmaps\]](#fig:DSSmaps) shows DSS optical images of all the SFRs listed in Table [1](#tab:sfrs), as discussed in Section [3](#sec:RNesources). Figure [4](#fig:OffsetDist) shows fraction of all YSOs (solid lines) and just Class II sources (dashed lines) which are associated with RNe as a function of offset thresholds used to define association, as discussed in Section [4](#sec:discussion_RNe).

![image](SFRs_catalogues_DSS.png)

![](CummulativeDistOffset.png)

# Distribution of spectral indices

Figure [\[fig:alphas\]](#fig:alphas) shows the distribution of extinction-corrected spectral indices ($\alpha$’, solid bars) and originally measured spectral indices ($\alpha$, dashed-grey line), as discussed in Section [3](#sec:RNesources). The distribution of $\alpha$ values are shifted to the right because foreground extinction can artificially increase the observed infrared excess for a source.

![image](Alphas.png)

# Class II sources near RNe

Table [2](#tab:class2) gives coordinates (first two columns), SIMBAD identifiers (third column), the SFR (fourth column), spectral indices (fifth and sixth columns), and RNe catalogue identifiers (last two columns) for all the Class II sources in the vicinity of RNe, as discussed in Section [3](#sec:RNesources).

| R.A. \[$^{\circ}$\] | Decl. \[$^{\circ}$\] | Simbad Id. | Region | $\alpha$ | $\alpha$’ | Magakian RNe Id. | Connelley RNe Id. |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 247.96698 | -24.93782 | ISO-Oph 204 | Ophiuchus | -0.17 | -0.51 | \- | 66 |
| 239.17449 | -42.32318 | HD 142527 | Lupus | -0.6 | -0.91 | 641 | \- |
| 236.30347 | -34.29186 | CD-33 10685 | Lupus | -0.64 | -0.95 | 634 | \- |
| 237.02178 | -35.26469 | V\* HN Lup | Lupus | -0.84 | -1.15 | 636 | \- |
| 277.19941 | 0.14439 | V\* VV Ser | Serpens | -0.78 | -1.05 | 766 | \- |
| 85.20028 | -8.09964 | CoKu DL Ori G1 | Orion | -0.93 | -1.24 | 132 | \- |
| 167.01364 | -77.65476 | HD 97048b | Chamaeleon | -0.07 | -0.38 | 533 | \- |
| 168.11282 | -76.73947 | BRAN 341D | Chamaeleon | -0.76 | -1.11 | 545 | \- |
| 168.12797 | -76.73998 | V\* CW Cha | Chamaeleon | -0.61 | -1.09 | 545 | \- |
| 285.28588 | -36.95575 | V\* S CrA B | Corona Australis | -0.8 | -1.22 | 781 | \- |
| 68.13232 | 24.33411 | V\* FZ Tau | Taurus | -0.86 | -1.17 | 74 | \- |
| 68.39192 | 24.35472 | V\* GI Tau | Taurus | -0.62 | -0.93 | 75 | \- |
| 68.12742 | 24.33257 | V\* FY Tau | Taurus | -1.12 | -1.43 | 74 | \- |
| 68.39412 | 24.35176 | V\* GK Tau | Taurus | -0.67 | -0.98 | 75 | \- |
| 69.61912 | 26.1804 | V\* DO Tau | Taurus | -0.51 | -0.82 | 78 | \- |
| 68.92066 | 24.18566 | NAME CoKu Tau 3 | Taurus | -0.9 | -1.21 | 76 | \- |
| 68.97004 | 22.90634 | V\* HP Tau | Taurus | -0.57 | -0.88 | 77 | \- |
| 55.73321 | 31.97828 | 2MASS J03425596+3158419 | Perseus | -0.98 | -0.84 | 48 | \- |
| 52.68335 | 30.54634 | EM\* LkHA 326 | Perseus | -0.64 | -0.89 | 45 | \- |
| 52.21743 | 30.75151 | EM\* LkHA 325 | Perseus | -0.69 | -0.78 | 41 | \- |
| 235.755 | -34.15417 | HH 185 | Lupus | -0.21 | -0.31 | \- | 64 |
|  |  |  |  |  |  |  |  |

: Class II YSOs associated with RNe

Table notes: List of 21 Class II YSOs ($-1.6 \leq \alpha' < -0.3$) associated with RNe (distance to nearest RNe $\lesssim$ 2000 au), as discussed in Section [3](#sec:RNesources). $\alpha$ and $\alpha$’ values are measured and extinction-corrected spectral indices, respectively. Last two columns show index numbers for matched RNe in (cite: Magakian2003) and (cite: Connelley2007) catalogues.

# Required observations and analysis

In order to further test a possible link between RNe and late infall, a deep uniform survey of large-scale structures is needed for Class II sources associated with RNe, as suggested in Section [4](#sec:discussion_RNe). Ideal observational parameters for such a survey are discussed below.

For what concerns the angular scales, both observations (Figure [1](#fig:known_sources)) and simulations (cite: Kuffmeier2020) suggest that the infalling streamers should be roughly kilo-au scales in length. Therefore, observations needed to study these structures should have a large enough maximum recoverable angular scale ($\gtrsim1000$ au), so as to not filter out large-scale emission. For the typical distance of 150 pc to nearby SFRs, this physical scale corresponds to the largest angular scale of $\gtrsim7\ensuremath{''}$. On the other hand, spatial resolution of such observations should be roughly $\lesssim100$ au ($\lesssim0.7\ensuremath{''}$ at a distance of 150 pc), in order to resolve the connection between large-scale structures and protoplanetary disks. Such a resolution should also be adequate to resolve the width of infalling streamers (Figure [1](#fig:known_sources)).

In terms of spectral resolution, free-fall velocity for the infall of material can be estimated as $v = \sqrt{2GM_{*}/R}$, where $G$ is the gravitational constant, $M_{*}$ is the stellar mass, and $R$ is the free-fall length scale. For the typical stellar mass of $\sim0.5 M_{\odot}$ and expected infall length scale of $\sim1,000$ au, the free-fall velocity should be $\sim0.95$ km s$^{-1}$. Assuming we see such an infalling streamer at an intermediate inclination of $45^{\circ}$, observed velocity difference would be $\sim0.65$ km s$^{-1}$. In order to resolve the velocity profile, we would need at least three independent data points, and thus a spectral resolution of $\lesssim0.2$ km s$^{-1}$.

The sensitivity requirements of the ideal observations can be based on the past observations of such large-scale structures. Among the five sources discussed in Section [2](#sec:knownsources), AB Aur and SU Aur are exceptionally bright and may not be representatives for the overall sample. For RU Lup, the signal-to-noise ratio for the spiral structures was sub-optimal ($\lesssim3$) in the individual channel (cite: Huang2020), which can make it hard to study the background dynamical processes. Thus, sensitivity requirements of the observations can be based on observations of GM Aur and DO Tau, and for both of which the brightness-temperature sensitivity was $\sim250$ mK (normalised to a channel width of $0.2$ km s$^{-1}$).

If large-scale structures are observed around other Class II sources, gas kinematics can be analysed to understand the dominant dynamical processes. A first step could be to check if the material is gravitationally bound to the protostellar system. For this the kinetic energy can be computed along the streamer, using the relative line-of-sight velocities, and compared to gravitational energy, similar to the analysis done for DO Tau by (cite: Huang2022) (see Figure 12). Furthermore, position-velocity diagrams, along any detected streamer, can be modelled and compared to the velocity profiles expected for different kinematic features such as rotation ($v \propto R^{-1}$, for conserved angular momentum) and infall ($v \propto R^{-0.5}$, for free fall), similar to the analysis done for less evolved protostars HL Tau (cite: Yen2019) and Lupus 3-MMS (cite: Thieme2022).

Another way to infer late infall could be to study gas kinematics together with NIR polarisation observations, as was done for SU Aur by (cite: Ginski2021). The degree of polarisation in such observations can be correlated to the dust scattering angles, which are expected to depend on the three-dimensional morphology of dust structures (cite: Stolker2016). Studying the morphology and gas kinematics in larger-scale ($\sim10,000$ au) clouds can also allow us to judge the possibility of late infall (cite: Tang2012; Dullemond2019).

Finally, late infall can also be inferred by observing these systems using different chemical species. Though CO has a high surface brightness, making it ideal to detect faint structures, it is also likely to be polluted by the emission from diffuse gas in these clouds. For less evolved sources, infalling streamers have also been observed in tracers such as HCO$^{+}$, HC$_3$N, HC$_5$N, CCS, $^{13}$CS, HNC, and H$_2$CO (cite: Yen2019; Pineda2020; Murillo2022; Valdivia-Men2022). Moreover, material falling onto protoplanetary disks also creates shocks, which can be observed using shock tracers such as SiO, SO, and SO$_2$ (cite: Garufi2022). A dedicated chemical study of streamers could also allow us to identify better chemical tracers for these structures for a large-scale survey.

# Alternative explanations for large-scale structures

The large-scale CO structures discussed in Section [2](#sec:knownsources) and [3](#sec:RNesources) could also be due to other dynamical processes besides late infall (cite: Huang2020). One of the other prominent causes, particularly for spiral-like structures, could be a tidal interaction of stellar companions, as it has been observed in some other multiple systems (cite: Rodriguez2018; Kurtovic2018; Zapata2020). The two sources we found with large-scale structures, HD 142527 and S CrA (Section [3](#sec:RNesources)), are binaries, and thus some of the structures we observe around them (Figure [3](#fig:rne_sources), panel a and c) could be due to tidal interactions between protostars and surrounding gas.

Furthermore, such structures can also be created due to close encounters by neighbouring YSOs, as predicted by several hydrodynamic simulations (cite: Cuello2019; Vorobyov2020) and likely observed for a few sources (cite: Dong2022). The role of these stellar flybys can be checked by looking at relative distances and velocities of nearby YSOs, as was done for SU Aur (cite: Ginski2021).

Gravitational instabilities can be another possible way to form spiral-like structures, if the disks are massive enough (cite: Dong2015), as generally inferred by Toomre’s Q parameter (cite: Toomre1964). Such instabilities are expected to leave characteristic ’wiggle’ signatures in the gas kinematics, which can be used to identify them (cite: Hall2020). Moreover, (cite: Harsono2011) showed that such instabilities can also be triggered by the infall of material. Irrespective of the cause of such non-Keplerian structures, both approaches followed in Sec. [2](#sec:knownsources) and in Sec. [3](#sec:RNesources) suggest that the vicinity of a RN can be an effective criterion to identify Class II disks that present large-scale structures.

# Channel maps

Figure [5](#fig:scra_channels) and [6](#fig:hd97048_channels) show channels maps of S CrA and HD 97048, respectively, as discussed in Section [3](#sec:RNesources).

![](S_CrA_CO_spw33_tav_jupyter_channelmaps.png)

![](HD_97048_12CO_emission_jupyter_channelmaps.png)

[^1]: Aashish.Gupta@eso.org

[^2]: http://www.astropy.org

</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "Archival optical images used to check for reflection nebulosity and map star-forming regions",
  "failed_quote": "Figure [fig:DSSmaps] shows DSS optical images of all the SFRs listed in Table 1, as discussed in Section 3."
 }
]
```
