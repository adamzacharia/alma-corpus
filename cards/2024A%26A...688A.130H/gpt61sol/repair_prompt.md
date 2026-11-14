# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...688A.130H\gpt61sol\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Multi-transition study of methanol towards NGC 1068 with ALMA

The outflowing molecular gas in the circumnuclear disk (CND) of the nearby (D=14 Mpc) AGN-starburst composite galaxy NGC 1068 is considered as a manifestation of ongoing AGN feedback. The large spread of velocities from the outflowing gas is likely driving various kinds of shock chemistry across the CND.

We performed a multiline molecular study using with the aim of characterizing the gas properties probed by in the CND of NGC 1068, and investigating its potential association with molecular shocks.

Multi-transition were imaged at the resolution of $0\,.\!\!^{\prime\prime}5-0\,.\!\!^{\prime\prime}8$

with the Atacama Large Millimeter/submillimeter Array (ALMA). We performed non-LTE radiative transfer analysis coupled with a Bayesian inference process in order to determine the gas properties such as the gas volume density and the gas kinetic temperature.

The gas densities traced by point to $\sim 10^{6}$ cm^-3^ across all the CND regions. The gas kinetic temperature cannot be well constrained in any of the CND regions though the inferred temperature is likely low ($\lesssim 100$ K).

The low gas temperature traced by suggests shocks and subsequent fast cooling as the origin of the observed gas-phase abundance. We also note that the E-/A- isomer column density ratio inferred is fairly close to unity, which is interestingly different from the Galactic measurements in the literature. It remains inconclusive whether exclusively traces slow and non-dissociative shocks, or whether the abundance can actually be boosted in both fast and slow shocks.

# Introduction

Feedback from active galactic nuclei (AGN) and star formation activities are both important agents in influencing the interstellar medium (ISM) and the evolution of galaxies. Shocks and turbulence can be associated with star formation activities due to protostellar outflows and supernova explosions that affect both chemistry and kinematics in the ISM. These energetics also act as heating sources (mechanical heating) aside from the ionization via X-ray and cosmic rays. On the other hand, AGNs are often considered to be X-ray dominated regions (XDRs) and are often thought to have an enhanced cosmic ray ionization rate (CRIR) and radiation field (cite: Meijerink_Spaans_2005; Viti+2014). While converting gravitational potential energy and kinetic energy into radiation, AGN can also trigger jets and the associated multi-phase mass outflows that inject energy into the ISM. It is therefore important to build an understanding of the interplay between these two feedback mechanisms. In this context, AGN-starburst composite galaxies serve as prime sources to study feedback from both AGN and star formation.

NGC1068 is a nearby (D = 14 Mpc (cite: Bland-Hawthorn+1997), $1'' \sim 70$ pc) Seyfert 2 galaxy and is considered to be the archetype of a composite AGN-starburst system. The proximity of this composite galaxy makes it an ideal laboratory for resolving the feedback from the starburst regions in its spiral arms that are spatially distinct from the AGN activity at the galactic center. A spatially unresolved molecular line survey by (cite: Aladro+2013) found this AGN-host galaxy being chemically distinct from pure starburst galaxies. The AGN is obscured by a molecular torus (cite: GB+2014). Surrounding the torus is an elliptical region that is largely devoid of molecular gas, while this region is also characterised by strong emission from ionised gas in a biconal outflow driven by the AGN. Streams of gas seem to pass through this region, connecting the torus to the rest of the circumnuclear disk (CND). The fueling of the AGN seems to be thwarted on an intermediate scale (r$<50$ pc) due to the outflowing nature of the CND and the torus-CND connections shown at comparable scales.

The CND extends to $r\sim200$ pc, and its different regions show significantly distinct chemistry, in a manner that appears to match the spatial extent of the influence of UV and X-ray irradiation from the nucleus (cite: GB+2014). All tracers observed by (cite: GB+2014) indicate a massive outflow from $r\sim50$pc out to $\sim 400$pc. This massive molecular outflow is likely launched by the interaction between the molecular gas in the CND and both the AGN ionized wind and the radio jet plasma, and is hence viewed as a sign of ongoing AGN feedback (cite: GB+2014; GB+2019). This interaction has produced large-scale molecular shocks and the associated rich shock chemistry at different locations in the CND (cite: Viti+2014). (cite: Viti+2014) found that models for the chemically distinct sub-regions of the CND each require a three-phase interstellar medium. One component is indeed shocked gas, while the other two regions are with enhanced CRIR (and/or X-ray activities) by a least a factor of 10. This illustrates the complexity of the region. (cite: Scourfield+2020) reported that the temperature and the CRIR in the CND increase from east to west from observations of CS and subsequent modelling. Shocks in the CND of NGC 1068 were also studied with both observations and chemical modeling of HNCO and SiO (cite: Kelly+2017; Huang+2022; Huang_Viti_2023), which are typically used as tracers of slow and fast shocks respectively.

Gas phase methanol () is commonly seen in the ISM, both in Galactic and extragalactic environments, and has been proposed as one of the shock tracer candidates. As the simplest complex organic molecule (COM), can be formed efficiently in cold environments (12-20K) through repeated hydrogenation of CO on ice grains (cite: Fuchs+2009) as well as through recently proposed H-abstraction reaction of radicals on ice grains (cite: Alvarez+2018; Simons+2020; Santos+2022). A scheme for gas-phase formation has also been proposed, yet it remains incapable of accounting for the observed interstellar gas-phase (cite: Garrod+2006FaDi; Geppert+2006FaDi). The formed on ice grains can then be released back to the gas phase via thermal sublimation or non-thermal desorption processes. Among these processes, shocks can effectively liberate the solid-state into gas phase through sublimation and sputtering. could, however, be destroyed in the presence of dissociative J shocks or fast shocks, as suggested in the observational work by (cite: Suutarinen+2014). On the other hand, the chemical modeling work by (cite: Holdship+2017) has shown that non-dissociative high velocity C shocks (e.g. with shock velocity $>45$ km/s) can still elevate the gas-phase to comparable levels as achieved by the slow C shocks (e.g. with shock velocity $<20$ km/s. )

has two spin isomers[^2], referred to as E- and A- owing to the combinations of nuclear spin alignment in the three H-atoms of the methyl () group. In A-type , the nuclear spins of the three protons in the methyl group are parallel. For E-type , one of the protons in the methyl group has an anti-parallel nuclear spin with respect to the others. Observationally the two spin isomers of have different spectroscopic properties including transition frequencies.

has been detected in multiple studies of the CND and the starburst ring (SB ring) of NGC 1068 at low-resolution ($>80$ pc) (cite: Aladro+2013; Takano+2014; Nakajima+2015). In these results, however, only the $J_K = 2_{K} - 1_{K}$ transition has been detected. Observations of transitions covering a range of excitation energies will be critical in quantitatively characterize the gas properties traced by .

In the current work, we present high resolution ($\sim 50$ pc scale) ALMA observations of the CND of NGC 1068 for six "clusters" of transitions with emission from both A- and E- . This high spatial resolution provides physical scales comparable to giant molecular clouds (GMCs). We analyzed these observations with non- local thermodynamic equilibrium (non-LTE), radiative transfer modeling. The goal is to quantitatively characterize the gas properties in order to gain insights into its association with the local shock history in the CND of NGC 1068. These observations can help better constrain the properties of the gas in the typical environments where COMs are expected to be found, and also explore the potential of using as a shock tracer. The paper is structured as follows. In Section 2, we describe the observations and the data reduction process. In Section 3, we present the molecular line intensity maps and the extracted velocity-integrated line intensities. In Section 4, we perform a non-LTE radiative transfer analysis in order to constrain the physical conditions of the gas. We discuss the potential association between the gas properties traced by and the presence of shocks. We also briefly discuss the E-/A- isomer ratio that is measured in this extragalactic source, and the potential indication of the formation environment. We briefly summarize our findings in Section 5.

# Observations and data reduction

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition | Rest Frequency | E~u~ | $g_u$ | $A_{ul}$ | Spatial resolution | mJy/beam to K |
|  | \[GHz\] | \[K\] |  | \[s$^{-1}$\] | \[$''$\] |  |
| E- $J_K = 2_{-1} - 1_{-1}$ | 96.739358 | 12.5 | 5 | $2.557794\times 10^{-6}$ | $0.75\times0.62$ | 0.28 |
| A- $J_K = 2_{0} - 1_0$ | 96.741371 | 7.0 | 5 | 3.408015$\times 10^{-6}$ | - - | - - |
| E- $J_K = 2_{0} - 1_{0}$ | 96.744545 | 20.1 | 5 | $3.407341\times 10^{-6}$ | - - | - - |
| E- $J_K = 2_{1} - 1_{1}$ | 96.755501 | 28.0 | 5 | $2.624407\times 10^{-6}$ | - - | - - |
| E- $J_K = 3_{0} - 2_{0}$ | 145.093754 | 27.1 | 7 | $1.231417\times 10^{-5}$ | $0.49\times0.40$ | 0.30 |
| E- $J_K = 3_{-1} - 2_{-1}$ | 145.097435 | 19.5 | 7 | $1.095695\times 10^{-5}$ | - - | - - |
| A- $J_K = 3_{0} - 2_{0}$ | 145.103185 | 13.9 | 7 | 1.232344$\times 10^{-5}$ | - - | - - |
| A- $J_K = 3_{-2} - 2_{-2}$ | 145.124332 | 51.6 | 7 | 6.892634$\times 10^{-6}$ | - - | - - |
| E- $J_K = 3_{2} - 2_{2}$ | 145.126191 | 36.2 | 7 | $6.771773\times 10^{-6}$ | - - | - - |
| E- $J_K = 3_{-2} - 2_{-2}$ | 145.126386 | 39.8 | 7 | $6.857968\times 10^{-6}$ | - - | - - |
| E- $J_K = 3_{1} - 2_{1}$ | 145.131864 | 35.0 | 7 | $1.124576\times 10^{-5}$ | - - | - - |
| A- $J_K = 3_{2} - 2_{2}$ | 145.133415 | 51.6 | 7 | $6.894658\times 10^{-6}$ | - - | - - |
| E- $J_K = 5_{0} - 5_{-1}$ | 157.178987 | 47.9 | 11 | $2.037818\times 10^{-5}$ | $0.65\times0.41$ | 0.19 |
| E- $J_K = 4_{0} - 4_{-1}$ | 157.246062 | 36.3 | 9 | $2.098481\times 10^{-5}$ | - - | - - |
| E- $J_K = 1_{0} - 1_{-1}$ | 157.270832 | 15.4 | 3 | $2.205743\times 10^{-5}$ | - - | - - |
| E- $J_K = 3_{0} - 3_{-1}$ | 157.272338 | 27.1 | 7 | $2.146271\times 10^{-5}$ | - - | - - |
| E- $J_K = 2_{0} - 2_{-1}$ | 157.276019 | 20.1 | 5 | $2.181936\times 10^{-5}$ | - - | - - |
| A- $J_K = 1_{-1}-1_0$ | 303.366921 | 16.9 | 3 | 2.263319$\times 10^{-4}$ | $0.46\times0.42$ | 0.07 |
| A- $J_K = 2_{-1}-2_{0}$ | 304.208348 | 21.6 | 5 | 2.115671$\times 10^{-4}$ | $0.46\times0.42$ | 0.07 |
| A- $J_K = 3_{-1}-3_{0}$ | 305.473491 | 28.6 | 7 | 1.632485$\times 10^{-4}$ | $0.48\times0.44$ | 0.06 |
| $J = 3_{1,2}-2_{2,1}$ | 145.0895946 | 16.05 | 21 | $6.764\times 10^{-5}$ |  |  |
| SiO $J = 7-6$ | 303.9268092 | 58.4 | 15 | $1.4648\times 10^{-3}$ |  |  |
| OCS $J = 25-24$ | 303.99326170 | 189.68 | 51 | $8.1948\times 10^{-5}$ |  |  |
| SO $J = 7_{8}-6_{7}$ | 304.0778440 | 62.1 | 17 | $3.609\times 10^{-4}$ |  |  |

\
(a) The main line refers to transitions with the lowest $E_{u}$ in each frequency group - in particular for the 96 GHz, 145 GHz, and 157 GHz groups.

|  Name  |          RA          |                DEC                |
|:------:|:--------------------:|:---------------------------------:|
| CND R1 | 02^h^42^m^40^s^.7617 | -00$^{\circ}$00${'}$48${''}$.1200 |
| CND R2 | 02^h^42^m^40^s^.7243 | -00$^{\circ}$00${'}$49${''}$.2400 |
| CND R3 | 02^h^42^m^40^s^.6030 | -00$^{\circ}$00${'}$48${''}$.9600 |
| CND R4 | 02^h^42^m^40^s^.6590 | -00$^{\circ}$00${'}$47${''}$.7000 |

: Coordinates (RA and Dec) of the four selected regions within the CND.

The transitions investigated in this paper were observed towards NGC 1068 using ALMA. These data were obtained during cycle 6 (project-ID: 2018.1.01506.S) with band 3 & 4 receivers, and cycle 3 (project-ID: 2015.1.01144.S) using band 7 receivers. The field of view (F.O.V.) is $56''$ for band-3 data, $42''$ for band-4 data, and $19''$ for band-7 data, respectively, which are all larger than the span of the CND ($\sim 5''$). In the band-3 and band-4 observations, J0238+1636 was used as bandpass calibrator, and J0239-0234 as phase calibrator. In the band-7 observation, J0238+1636 was used as bandpass calibrator, and J0217+0144 as phase calibrator. The above-mentioned data were calibrated and imaged using the ALMA reduction package CASA[^3] (cite: CASA_2007).

The rest frequencies were defined using the systemic velocity determined by (cite: GB+2019), as $v_{sys}$(LSR) = 1120 km s^-1^ (radio convention). The relative velocities throughout the paper refer to this $v_{sys}$. The phase tracking center was set to $\alpha_{2000}$ = (02^h^42^m^40.771^s^), $\delta_{2000}$ = (–00$^{\circ}$00$'$47. 84$''$). The relevant information of each observation is listed in Table [\[tab:table_obsinfo\]](#tab:table_obsinfo). This table includes the target molecular transitions and the associated spectroscopic data, and the synthesized beam size for each observation. The beam sizes of our observations range between $\sim0\,.\!\!^{\prime\prime}5-0\,.\!\!^{\prime\prime}8$, or 35-56 pc in physical scales. This is comparable to the typical scale of giant molecular clouds (GMCs). The spectral resolution of the data cubes lies between $\sim 4-6$ km/s.

![](Fig_SpecK_6lines_CND_R1.png)

# Molecular line emission

## Molecular-line spectra

In order to investigate the physical structure traced by and to compare it with the shock study using and observations at the same resolution by (cite: Huang+2022), we followed their CND region selection: two regions (R1, R2) in the east of the CND, two regions (R3, R4) in the west of the CND. Each region encompasses a beam size of $0\,.\!\!^{\prime\prime}8\times0\,.\!\!^{\prime\prime}8$ to match the lowest angular resolution among our data and those from (cite: Huang+2022). Table [1](#tab:table_7regs) lists these four selected positions within NGC 1068 with their coordinates, which are the center of the individual $0\,.\!\!^{\prime\prime}8\times0\,.\!\!^{\prime\prime}8$ apertures. Figure [1](#fig:4p1_spec) shows the sample spectra from the position CND-R1 (see Table [1](#tab:table_7regs)) for all transitions used in this study in units of \[K\]. We use spectra from CND-R1 as a representative sample as CND-R1 is the brightest spot in the CND in all transitions in the current work. All the \[mJy beam^-1^\] to \[K\] conversion factors are listed in Table [\[tab:table_obsinfo\]](#tab:table_obsinfo).

### Line blending between E- and A- isomers

Figure [1](#fig:4p1_spec) also demonstrates the unavoidable line blending between A- and E- transitions in the line spectra (top three panels). The line width of is at least 50 km/s - based on the clean isolated $1_{-1}-1_{0}$ line at 303.366921 GHz) - and as the nearest line to that is only few km/s away (e.g top 3 panels of spectra) we can not disentangle one from another by individual component fitting. Given that the intensity contribution from each transition within the same blended group is a function of the spectroscopic properties of the group as well as the gas excitation conditions, generally one can not assume the transition with lowest $E_u$ to dominate the emission. We will revisit this in Section [\[sec:radex\]](#sec:radex).

## Moment-0 maps

![](Maps_Kkms_m3_mom0_CH3OH/v2_CH3OH_96GHz.png)

![image](Maps_Kkms_m3_mom0_CH3OH/v2_CH3OH_145GHz.png)\
![image](Maps_Kkms_m3_mom0_CH3OH/v2_CH3OH_157GHz.png) ![image](Maps_Kkms_m3_mom0_CH3OH/v2_CH3OH_303GHz.png)\
![image](Maps_Kkms_m3_mom0_CH3OH/v2_CH3OH_304GHz.png) ![image](Maps_Kkms_m3_mom0_CH3OH/v2_CH3OH_305GHz.png)

The moment-0 maps present the spatial distribution of line intensities integrated over velocity for each transition group as listed in Table [\[tab:table_obsinfo\]](#tab:table_obsinfo). All the moment-0 maps are subsequently smoothed to a common resolution of $0\,.\!\!^{\prime\prime}8$ and applied with a $3.0 \sigma$ threshold clipping (Figure [2](#fig:Maps_m3_mom0-I)) The velocity span, over which the line fluxes were integrated, was set to include significant emission arising from velocity structures such as rotation and outflow motion in NGC 1068. In this work we used $|v-v_{sys}^{LSRK} |\leq$ 230 km s^-1^ to cover such velocity span. The only exception is for the A- $J_K = 2_{-1}-2_{0}$ line, which has an SO $J = 7_{8}-6_{7}$ line nearby, and the velocity integration was performed in a narrower range ($-130-64$ km/s) to not exceed the midpoint between the target line and the SO line.

In the case of the line cluster at $\sim 145$ GHz, given the unavoidable blending with c-, we use an existing estimate of the contribution of this particular c- transition and the associated uncertainty based on observations towards another nearby galaxy, NGC 253 (cite: ALCHEMI_main_2021), as an estimate for NGC 1068. While we note that NGC 253 (a starburst) is very different from NGC 1068 (an AGN dominated galaxy), NGC 253 is the only galaxy where a quantitative estimate of the contribution from the c- $J = 3_{1,2}-2_{2,1}$ transition to the methanol cluster has been performed. This estimate is derived from multi-transitional line fitting using data from ALMA band 3 to band 7 and the line fitting program `MADCUBA` (cite: ALCHEMI_main_2021).

Table [\[tab:table_integ_I\]](#tab:table_integ_I) lists all the measured velocity-integrated line intensities (in K km/s) from the observations with common resolution of $0\,.\!\!^{\prime\prime}8$.

# Inference of gas properties in the CND

The configuration of the CND in NGC 1068 relative to its jet-ISM interaction and the associated outflow geometry makes it a prime source to investigate shock-driven chemistry (cite: GB+2014; Viti+2014). The axes of the ionized outflow and the jet both form a small angle relative to the molecular gas disk of the galaxy. This particular geometry implies that there is a strong coupling between the AGN outflow and the jet with the ISM in the disk out to r$\sim400-500$ pc.

Within this context we wish to characterize the gas properties traced by across the CND regions, and to study its association with the shock history of the CND regions.

In characterizing the gas properties traced by any molecular species with multiple transitions, one often assumes optically thin Local Thermal Equilibrium (LTE) conditions. This allows the implementation of the so-called "rotation diagram" (cite: Goldsmith_Langer_1999) based on the observed line intensities from individual molecular transition. One can then infer the physical properties such as rotational temperature and column density of the species from this rotation diagram. Such approach relies not only on the validity of the assumption of optically thin LTE, but also requires each transition to be free of contamination from other lines. In our case, however, blending from different transitions is prevalent (both from A- and E- ) and hard to disentangle by individual component fitting as mentioned in Sect. [3.1.1](#sec:AEblending). One option is to assume thermalization of the gas and to re-distribute the measured line intensity to all transitions involved in the line blending (cite: Martin+2006).

Alternatively, we can use non-LTE radiative transfer modeling and infer the gas properties by comparing the summation of the predicted line intensities from all blending lines in each "transition group" with the observed line intensity for each specific measurement. To characterize the emissions across the CND region, we choose indeed to perform a radiative analysis via non-LTE radiative transfer modeling. With this approach we are able to quantitatively characterize the column density of and, more importantly, the gas temperature and the gas density in the CND.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| CND region | R1 | R2 | R3 | R4 |
| Transition | I($\sigma$) | I($\sigma$) | I($\sigma$) | I($\sigma$) |
|  | \[K km/s\] | \[K km/s\] | \[K km/s\] | \[K km/s\] |
| 96 GHz group | 46.104(7.002) | 5.253(1.353) | 29.987(4.630) | 13.005(2.239) |
| 145 GHz group | 41.053(41.059) | 2.995(3.085) | 19.891(19.904) | 11.043(11.068) |
| 157 GHz group | 58.144(8.742) | 4.125(0.856) | 25.645(3.892) | 13.975(2.178) |
| A- $J_K = 1_{-1}-1_0$ | 15.987(2.457) | 2.125(0.624) | 5.202(0.947) | 2.918(0.692) |
| A- $J_K = 2_{-1}-2_{0}$ | 30.962(4.668) | 5.099(0.896) | 6.904(1.136) | 4.671(0.841) |
| A- $J_K = 3_{-1}-3_{0}$ | 23.871(3.637) | 4.033(0.879) | 7.203(1.255) | 5.532(1.047) |

For the non-LTE analysis, we use the radiative transfer code `RADEX` (cite: radex_vandertak_2007) via the Python package SpectralRadex[^4] (cite: Holdship+2021_SpectralRadex). The molecular data used for are from (cite: CH3OH_mol_data_2010) taken from the LAMDA database (cite: LAMDA_2005). We coupled the RADEX modeling with the Markov Chain Monte Carlo (MCMC) sampler `emcee` (cite: FM+2013_emcee) to perform a Bayesian inference of the parameter probability distributions in order to properly sample this parameter space and obtain reliable uncertainties. We assume priors of uniform or log-uniform distribution within the determined ranges (listed in Table [2](#tab:table_prior)). With this, we assume that the uncertainty on our measured intensities is Gaussian so that our likelihood is given by $P(\theta | d) \sim \exp(-\frac{1}{2}\chi^2),$ where $\chi^2$ is the chi-squared statistic between our measured intensities and the `RADEX` predictions based on a set of parameters $\theta$. This allows us to assess the influence of physical conditions, such as gas density and temperature, in the excitation of the transitions analyzed.

Regarding the blending of adjacent A- and E- isomer transitions, we can not distinguish them and contributions from any of these lines is generally not negligible for our observations. In other words, all components in the same blended group should be taken into consideration in particular when one tries to compare the line intensity with radiative transfer modeling. Hence, we need to determine a priori the flux contribution from both A- and E- transitions in our `RADEX` modeling. The species column density from both isomers, $N_{A-}$ and $N_{E-}$, are, therefore, also explored as free parameters. In summary, the following physical parameters are explored: the gas volume density ($n_{H2})$, gas kinetic temperature ($T_{kin}$), the species column density ($N_{E-}$ and $N_{A-}$), and the beam filling factor ($\eta_{ff}$). The prior ranges and distributions are given in Table [2](#tab:table_prior). We list the best fit for all the explored parameters in Table [\[tab:Bayesian_gasphys\]](#tab:Bayesian_gasphys).

Generally the gas densities and the molecular column densities of both A- and E- isomers are well constrained. The inferred A- and E- column densities are both between $10^{15-16}$ cm^-2^. The physical interpretation regarding these measured A- and E- column densities will be further explored in Section [4.3](#sec:EAratio). The gas densities point to $\sim 10^{6}$ cm^-3^ across all the CND regions. This is not surprising since, as discussed in the Introduction, is a product of surface reactions in dense environments. The gas kinetic temperature, however, cannot be well constrained in any of the CND regions. Despite the fact that the number of transitions involved in our analysis is greater than the number of free parameters we explore here, it is possible that the coverage of the excitation energy levels is not wide enough to fully constrain the gas temperature. We speculate that transitions of higher $E_{u}$ may be needed to properly constrain gas temperature. We note that we also tried a different algorithm to perform the Bayesian inference - a nested sampling Monte Carlo algorithm MLFriends (cite: ultranest16; ultranest19) using the `UltraNest` package[^5] (cite: ultranest21) - complementing our analysis with the Markov chain Monte Carlo (MCMC) sampler `emcee` (cite: FM+2013_emcee). The inference results with `UltraNest` still failed to constrain the gas temperature.

## Are the gas properties consistent with shocks?

As shown in Table [\[tab:Bayesian_gasphys\]](#tab:Bayesian_gasphys), all the inferred gas densities point to $\sim 10^{6}$ cm^-3^ across all the CND regions. With such high gas density the post-shock gas is expected to cool off fairly quickly (cite: Huang_Viti_2023), which is somewhat consistent with the indication that the (poorly constrained) inferred temperatures are likely to be low ($\leq$ 100 K; see Figure 3).

Based on the chemical modeling with `UCLCHEM` for the physical condition of the CND of NGC 1068 performed by (cite: Huang_Viti_2023), both fast and slow shocks can enhance the methanol fractional abundance to comparable levels in the presence of shocks. However, in the chemical models without shocks, a higher gas temperature is required (such that water ice sublimates, $T\gtrsim 100$ K) to boost the abundance to comparable levels (cite: Huang_Viti_2023). In models where a shock is occurring, the kinetic temperature of the gas can be very high due to shock heating but can also be low due to rapid post shock cooling in a dense medium. Both scenarios lead to methanol abundances compatible with observations. The gas temperature measured from observations, therefore, is one of the key physical parameters in discerning the chemical origin of the observed . Unfortunately in all four CND regions explored, none of the gas temperatures are constrained enough to discern among shock scenarios. Nevertheless, qualitatively, most regions (CND-R1, CND-R3, and CND-R4) tend to point to $T_{kin}<100$ K. This would point to the shock origin of the observed gas-phase for in low temperature regimes only shocks can account for the enhanced gas-phase (cite: Huang_Viti_2023).

## Comparison with other shock tracers - SiO and HNCO

We choose to compare our results with the work by (cite: Huang+2022) where SiO and HNCO maps of the same region and at the same spatial resolution are presented. As far as the spatial distribution of is concerned, it is more concentrated towards the east of the CND and much less prominent in the west of the CND. This is similar to the SiO emission reported by (cite: Huang+2022). In contrast, the HNCO reported by (cite: Huang+2022), even in the higher-J level (HNCO 6-5) is much more extended throughout the CND. Interestingly, in terms of the gas density, points to a higher gas density than HNCO, while SiO mostly points to lower gas densities near $10^3$ cm^-3^. Finally, the gas temperature probed by , although not well constrained, is in the same range as that probed by HNCO. Compared to the high-$T$ gas traced by SiO, the lower temperature probed by HNCO and may be a product of faster cooling in denser gas environments regardless of the speed of the shock.

From this comparison it remains inconclusive whether exclusively traces slow and non-dissociative shocks ($v_{s}<20$ km/s) as proposed by (cite: Suutarinen+2014) or whether it traces both fast- and slow- shock environments as hinted by the chemical modeling in (cite: Holdship+2017) and (cite: Huang_Viti_2023).

## E-/A- Ratio

Aside from the gas density and gas temperature, the inferred $N_{E-}$ and $N_{A-}$ will be interesting to inspect. By assuming A- and E- isomers are formed and well mixed in the same environment, the equilibrium E/A ratio is linked to the temperature of the formation environment (cite: Wirstrom+2011; Holdship+2019). Generally the conversion of one isomer to another is considered a strongly forbidden process; the abundance ratio of the two isomers is therefore often assumed to be fixed at the time of the formation (cite: Kawakita_Kobayashi_2009; Wirstrom+2011). In particular, (cite: Wirstrom+2011) noted that is expected to be destroyed fairly rapidly compared to the time needed to alter the ratio. This implies that this ratio is thermalized at its formation and hence can provide insights into the origin and physical conditions of the methanol formation (cite: Wirstrom+2011). In other words, the measured E/A ratio actually informs us about the local temperature associated with formation [^6] at different locations in the CND.

On the ices, the optimal temperature for successive hydrogenation of CO to occur for methanol formation is suggested to be around $10-15$ K with a CO: ice mixture or pure solid-phase CO (cite: Watanabe+2004). At this low-temperature regime, an overabundance of A- is expected ($N_{E-}/N_{A-} <1.0$). In our measured $N_{E-}/N_{A-}$ ratio, the most probable ratio values are fairly close to unity (see Table [\[tab:Bayesian_gasphys\]](#tab:Bayesian_gasphys)). This is interestingly different from the generally expected overabundance of A- (cite: Wirstrom+2011) and the observed $N_{E-}/N_{A-}$ ratio from Galactic outflows reported by (cite: Holdship+2019). The Galactic measurements of $N_{E-}/N_{A-}$ ratio reported by (cite: Holdship+2019) are all below 0.7 and point to methanol formation temperatures below 10 K (see Figure 4 in (cite: Holdship+2019)). In contrast, our measured ratio, which is close to unity, points to a higher formation temperature of , $\gtrsim 15$ K. Note that the uncertainty derived from the inferred column densities of both isomers remain fairly large, so this is still highly uncertain.

We also want to highlight the only other two existing E-/A- ratio measurement. Similar to our non-LTE modeling approach, (cite: Muller+2021) performed non-LTE modeling for A- and E- isomer observations of the z=0.89 molecular absorber toward PKS 1830-211. They presented a comparably high E-/A- ratio of $\sim1.0 \pm 0.1$ via the submillimeter absorption lines of methanol from this source (cite: Muller+2021). There is also an LTE model for the nearby starburst galaxy NGC 253 (cite: Humire+2022). They report a fairly wide range of $N_{E-}/N_{A-}$ ratio varying from $\sim1.1-5.0$ (cite: Humire+2022).

Since the existing gas-phase proton exchange described in the literature is considered dissociative (cite: Wirstrom+2011), such Galactic-extragalactic distinction in $N_{E-}/N_{A-}$ ratio could imply a distinction between the formation environment of methanol in the nucleus of NGC 1068 from that of our own galaxy. Otherwise non-dissociative proton exchange reaction(s) such as proton exchange in the solid phase needs to be considered if one assumes that the $N_{E-}/N_{A-}$ ratio in Galactic and extragalactic environments start at a similar level.

|               Variable               |       Range       | Distribution type |
|:------------------------------------:|:-----------------:|:-----------------:|
| Gas density, $n_{\rm H2}$ \[cm^-3^\] |  $10^{2}-10^{8}$  |    Log-uniform    |
| Gas temperature, $T_{\rm kin}$ \[K\] |     $10-800$      |      Uniform      |
|          $N$(A-) \[cm^-2^\]          | $10^{12}-10^{18}$ |    Log-uniform    |
|          $N$(E-) \[cm^-2^\]          | $10^{12}-10^{18}$ |    Log-uniform    |
|   Beam filling factor, $\eta_{ff}$   |     $0.0-1.0$     |      Uniform      |

: Prior range adopted for our parameter space explored in the `RADEX`-Bayesian inference process described in Sect. [\[sec:radex\]](#sec:radex). The beam filling factor is defined as: $\eta_{ff}=\frac{\theta^{2}_{S}}{\theta^{2}_{MB}+\theta^{2}_{S}}$

| Model | log(n\[H2\]) | Tkin | log(N\[A-CH3OH\]) | log(N\[E-CH3OH\]) | Filling factor |
|:--:|:--:|:--:|:--:|:--:|:--:|
| CND-R1 | $6.25^{+0.33}_{-0.27}$ | - - | $15.73^{+0.45}_{-0.29}$ | $15.89^{+0.47}_{-0.30}$ | - - |
| CND-R2 | $6.49^{+0.96}_{-0.38}$ | $66^{+514}_{-35}$ | $15.00^{+0.55}_{-0.32}$ | $14.82^{+0.50}_{-0.37}$ | - - |
| CND-R3 | $5.87^{+0.28}_{-0.26}$ | - - | $15.19^{+0.64}_{-0.42}$ | $15.49^{+0.58}_{-0.54}$ | - - |
| CND-R4 | $5.97^{+0.35}_{-0.28}$ | - - | $15.04^{+0.54}_{-0.25}$ | $15.25^{+0.58}_{-0.29}$ | - - |

![](6lines_Bayesian/R1raw_CH3OHwAE_800K.png)

|                                                   |
|:--------------------------------------------------|
| ![image](6lines_Bayesian/R2raw_CH3OHwAE_800K.png) |

|                                                      |
|:-----------------------------------------------------|
| ![image](6lines_Bayesian/optR3raw_CH3OHwAE_800K.png) |

|                                                   |
|:--------------------------------------------------|
| ![image](6lines_Bayesian/R4raw_CH3OHwAE_800K.png) |

# Conclusions

The outflowing molecular gas in the CND of NGC 1068 and the associated large spread of velocities ($\sim100$ km s^-1^) likely drive a variety of molecular shocks at different locations in the CND. We perform a multi-line molecular study with ALMA of in order to determine the chemical signatures of such molecular shocks in the CND of NGC 1068 at spatial scale of GMC ($0\,.\!\!^{\prime\prime}8\sim 50$ pc). We briefly summarize below our conclusions:

1.  We performed non-LTE radiative transfer analyses where we coupled RADEX with a Bayesian inference procedure, in order to infer the gas properties traced by .

2.  The gas densities traced by point to $\sim 10^{6}$ cm^-3^ across all the CND regions. The gas kinetic temperature cannot be well constrained in any of the CND regions though the inferred temperature is likely to be low ($\lesssim 100$ K), suggesting a shock origin of the observed gas-phase .

3.  We compared both spatial distribution of emissions from multiple tracers of different types of shocks (SiO and HNCO) versus , and the gas properties traced by these three species. It remains inconclusive, however, whether exclusively trace slow shocks or whether it traces both fast- and slow- shocks.

4.  We also note that the inferred E-/A- isomer ratio is fairly close to unity, which is interestingly different from the Galactic measurements in the literature.

# Acknowledgements

KYH, and SV received funding from the European Research Council (ERC) Advanced Grant MOPPEX 833460.vii. SGB acknowledges support from research project grants PID2019-106027GA-C44 and PID2022-138560NB-I00 of the Spanish Ministerio de Ciencia e Innovación. KYH acknowledges assistance from Allegro, the European ALMA Regional Center node in the Netherlands. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00221.S, ADS/JAO.ALMA#2015.1.01144.S, and ADS/JAO.ALMA#2018.1.01506.S. ALMA is a partnership of ESO (represent- ing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

40 natexlab

(ref: Aladro+2013) Aladro, R., Viti, S., Bayet, E., et al. 2013, A&A, 549, A39

(ref: Alvarez+2018) Álvarez-Barcia, S., Russ, P., Kästner, J., & Lamberts, T. 2018, mnras, 479, 2007

(ref: Bland-Hawthorn+1997) Bland-Hawthorn, J., Gallimore, J. F., Tacconi, L. J., et al. 1997, Ap&SS, 248, 9

(ref: ultranest16) Buchner, J. 2016, Statistics and Computing, 26, 383

(ref: ultranest19) Buchner, J. 2019, PASP, 131, 108005

(ref: ultranest21) Buchner, J. 2021, The Journal of Open Source Software, 6, 3001

(ref: FM+2013_emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: Fuchs+2009) Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629

(ref: GB+2019) Garcı́a-Burillo, S., Combes, F., Ramos Almeida, C., et al. 2019, A&A, 632, A61

(ref: GB+2014) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: Garrod+2006FaDi) Garrod, R., Park, I. H., Caselli, P., & Herbst, E. 2006, Faraday Discussions, 133, 51

(ref: Gelman+1996) Gelman, A., Meng, X.-L., & Stern, H. 1996, Statistica Sinica, 6, 733

(ref: Geppert+2006FaDi) Geppert, W. D., Hamberg, M., Thomas, R. D., et al. 2006, Faraday Discussions, 133, 177

(ref: Goldsmith_Langer_1999) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: Holdship+2019) Holdship, J., Viti, S., Codella, C., et al. 2019, ApJ, 880, 138

(ref: Holdship+2017) Holdship, J., Viti, S., Jiménez-Serra, I., Makrymallis, A., & Priestley, F. 2017, AJ, 154, 38

(ref: Holdship+2021_SpectralRadex) Holdship, J., Viti, S., Martı́n, S., et al. 2021, A&A, 654, A55

(ref: Hougen_Oka_2005) Hougen, J. T. & Oka, T. 2005, Science, 310, 1913

(ref: Huang_Viti_2023) Huang, K.-Y. & Viti, S. 2023, arXiv e-prints, arXiv:2307.02812

(ref: Huang+2022) Huang, K. Y., Viti, S., Holdship, J., et al. 2022, A&A, 666, A102

(ref: Humire+2022) Humire, P. K., Henkel, C., Hernández-Gómez, A., et al. 2022, A&A, 663, A33

(ref: Kawakita_Kobayashi_2009) Kawakita, H. & Kobayashi, H. 2009, ApJ, 693, 388

(ref: Kelly+2017) Kelly, G., Viti, S., Garcı́a-Burillo, S., et al. 2017, A&A, 597, A11

(ref: ALCHEMI_main_2021) Martı́n, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46

(ref: Martin+2006) Martı́n, S., Mauersberger, R., Martı́n-Pintado, J., Henkel, C., & Garcı́a-Burillo, S. 2006, ApJS, 164, 450

(ref: CASA_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meijerink_Spaans_2005) Meijerink, R. & Spaans, M. 2005, A&A, 436, 397

(ref: Muller+2021) Muller, S., Ubachs, W., Menten, K. M., Henkel, C., & Kanekar, N. 2021, A&A, 652, A5

(ref: Nakajima+2015) Nakajima, T., Takano, S., Kohno, K., et al. 2015, PASJ, 67, 8

(ref: CH3OH_mol_data_2010) Rabli, D. & Flower, D. R. 2010, MNRAS, 406, 95

(ref: Santos+2022) Santos, J. C., Chuang, K.-J., Lamberts, T., et al. 2022, apjl, 931, L33

(ref: LAMDA_2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: Scourfield+2020) Scourfield, M., Viti, S., Garcı́a-Burillo, S., et al. 2020, MNRAS, 496, 5308

(ref: Simons+2020) Simons, M. A. J., Lamberts, T., & Cuppen, H. M. 2020, aap, 634, A52

(ref: Suutarinen+2014) Suutarinen, A. N., Kristensen, L. E., Mottram, J. C., Fraser, H. J., & van Dishoeck, E. F. 2014, MNRAS, 440, 1844

(ref: Takano+2014) Takano, S., Nakajima, T., Kohno, K., et al. 2014, PASJ, 66, 75

(ref: radex_vandertak_2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: Viti+2014) Viti, S., Garcı́a-Burillo, S., Fuente, A., et al. 2014, A&A, 570, A28

(ref: Watanabe+2004) Watanabe, N., Nagaoka, A., Shiraki, T., & Kouchi, A. 2004, ApJ, 616, 638

(ref: Wirstrom+2011) Wirström, E. S., Geppert, W. D., Hjalmarson, Å., et al. 2011, A&A, 533, A24

# Comparison of the predicted intensity from RADEX with observed values: A posterior predictive check (PPC)

In this section, we perform a posterior predictive check (cite: Gelman+1996) for the inferred gas properties in Section [\[sec:radex\]](#sec:radex) using RADEX and Bayesian inference process. We do this by performing a comparison of the distribution of the observational data, the measured velocity-integrated intensities, to the predicted distribution described by our Bayesian model. This is to verify our posterior distribution produces a distribution for the data that is consistent with the actual data. We sample the predicted line intensities from our posteriors between 16-84 percentiles, and plot these against the observed line intensities.

The comparisons are shown in Figure [7](#fig:PPC_CH3OH). It is worth noting that in the 145 GHz group, the predicted line intensities are systematically higher than the observed intensities after correcting the line contamination from emission, based on a very conservative estimate (see discussion in Sect. [3.2](#sec:mom0). ) This could suggest that this correction may be too aggressive so that it underestimates the true emission contribution from . Yet owing to the gas property inference being based on multi-line observations, the gas properties inferred are expected to be not penalized by this fact. This characteristic also shadows the true line intensity of in the 145 GHz group through the pitched line intensity prediction of this group. We have verified the above with a separate set of gas property inference with no contamination regarding , and the inferred gas properties remain consistent with the case presented in this work (i.e. with aggressive correction), and the observed versus predicted line intensity are consistent.

|                                                 |
|:------------------------------------------------|
| ![image](PPCs/PPC_intensity_CH3OH_CND_R1.png)   |
| \(a\) Observed and PPC intensities of in CND-R1 |

|                                                 |
|:------------------------------------------------|
| ![image](PPCs/PPC_intensity_CH3OH_CND_R2.png)   |
| \(b\) Observed and PPC intensities of in CND-R2 |

|                                                 |
|:------------------------------------------------|
| ![image](PPCs/PPC_intensity_CH3OH_CND_R3.png)   |
| \(c\) Observed and PPC intensities of in CND-R3 |

|                                                 |
|:------------------------------------------------|
| ![image](PPCs/PPC_intensity_CH3OH_CND_R4.png)   |
| \(d\) Observed and PPC intensities of in CND-R4 |

[^1]: kyhuang@strw.leidenuniv.nl

[^2]: Here we refer to nuclear spin isomers. Molecules that have identical nuclei but nonzero nuclear spin could exist at different energy levels belonging to the so called “nuclear spin modifications” or “nuclear spin isomers" (cite: Hougen_Oka_2005).

[^3]: http://casa.nrao.edu

[^4]: https://spectralradex.readthedocs.io

[^5]: <https://johannesbuchner.github.io/UltraNest/>

[^6]: Note that this formation temperature is set in the formation history of , and is different from the "present-time" gas temperature inferred at the beginning of Section [\[sec:radex\]](#sec:radex)

</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "∼0.5–0.8 arcsec; 35–56 pc",
  "failed_quote": "The beam sizes of our observations range between $\\sim0\\.\\!\\!^{\\prime\\prime}5-0\\.\\!\\!^{\\prime\\prime}8$, or 35-56 pc in physical scales."
 },
 {
  "path": "processing.imaging.smoothing.evidence[0]",
  "value": "Moment-0 maps smoothed to a common resolution of 0.8 arcsec",
  "failed_quote": "All the moment-0 maps are subsequently smoothed to a common resolution of $0\\.\\!\\!^{\\prime\\prime}8$"
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "Moment-0 maps: common resolution 0.8 arcsec",
  "failed_quote": "All the moment-0 maps are subsequently smoothed to a common resolution of $0\\.\\!\\!^{\\prime\\prime}8$"
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Use four CND positions and 0.8 × 0.8 arcsec apertures; express spectra in K",
  "failed_quote": "which are the center of the individual $0\\.\\!\\!^{\\prime\\prime}8\\times0\\.\\!\\!^{\\prime\\prime}8$ apertures."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "0.8 × 0.8 arcsec regions matched to the lowest angular resolution",
  "failed_quote": "Each region encompasses a beam size of $0\\.\\!\\!^{\\prime\\prime}8\\times0\\.\\!\\!^{\\prime\\prime}8$ to match the lowest angular resolution among our data and those from (cite: Huang+2022)."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Form moment-0 maps for each transition group, smooth, clip and measure velocity-integrated intensities",
  "failed_quote": "All the moment-0 maps are subsequently smoothed to a common resolution of $0\\.\\!\\!^{\\prime\\prime}8$ and applied with a $3.0 \\sigma$ threshold clipping"
 }
]
```
