# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...895..142L\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Magnetic fields in the early stages of massive star formation as revealed by ALMA

## Abstract

We present 1.3 mm ALMA dust polarization observations at a resolution of $\sim$0.02 pc of three massive molecular clumps, MM1, MM4, and MM9, in the infrared dark cloud G28.34+0.06. With the sensitive and high-resolution continuum data, MM1 is resolved into a cluster of condensations. The magnetic field structure in each clump is revealed by the polarized emission. We found a trend of decreasing polarized emission fraction with increasing Stokes $I$ intensities in MM1 and MM4. Using the angular dispersion function method (a modified Davis-Chandrasekhar-Fermi method), the plane-of-sky magnetic field strength in two massive dense cores, MM1-Core1 and MM4-Core4, are estimated to be $\sim$1.6 mG and $\sim$0.32 mG, respectively. The total virial parameters in MM1-Core1 and MM4-Core4 are calculated to be $\sim$0.76 and $\sim$0.37, respectively, suggesting that massive star formation does not start in equilibrium. Using the polarization-intensity gradient-local gravity method, we found that the local gravity is closely aligned with intensity gradient in the three clumps, and the magnetic field tends to be aligned with the local gravity in MM1 and MM4 except for regions near the emission peak, which suggests that the gravity plays a dominant role in regulating the gas collapse. Half of the outflows in MM4 and MM9 are found to be aligned within 10$\ensuremath{^\circ}$ of the condensation-scale ($<$0.05 pc) magnetic field, indicating that the magnetic field could play an important role from condensation to disk scale in the early stage of massive star formation. We also find that the fragmentation in MM1-Core1 cannot be solely explained by thermal Jeans fragmentation or turbulent Jeans fragmentation.

# Introduction

It is clear that stars are formed from the collapse of molecular dense cores[^1] that are created by the contraction of over dense regions in molecular clouds when gravity overcomes the internal pressure such as magnetic fields or turbulence (cite: 1987ARA&A..25...23S). In the formation of massive stars (mass $>$ 8 $M_{\odot}$), turbulence is believed to play an important role because massive star-forming regions are usually found to be supersonic and have large line widths. However, the role of magnetic fields in massive star formation is still not well understood (cite: 2014PhR...539...49K; 2014prpl.conf..149T; 2019FrASS...6....3H; 2019FrASS...6...15P).

The Radiative Alignment Torque (RAT) theory predicts that asymmetrical dust grains with sizes $>$0.05 $\mu$m are expected to spin-up due to the radiative torque in the presence of a radiation field and the short axis of these dust grains would tend to be aligned with magnetic field lines (cite: 2007JQSRT.106..225L; 2007MNRAS.378..910L). Theoretical and observational evidence has supported the RAT mechanism as the dominant grain alignment mechanism to produce polarized thermal emission at millimeter/sub-millimeter (mm/submm) wavelengths in diffuse intersteller medium and molecular clouds with $\mu$m or sub-$\mu$m size grains (cite: 2015ARA&A..53..501A). The exception is that the grain size grows to millimeter/sub-millimeter in protoplanetary disks and the observed polarization would be dominated by those produced from dust self-scattering (cite: 2015ApJ...809...78K; 2016MNRAS.456.2794Y) or grains aligned by strong radiation fields (cite: 2017ApJ...839...56T). Thus, observing the polarized dust emission at mm/sub-mm offers a powerful way to trace the plane-of-sky magnetic field in star-forming molecular clouds at scales greater than the disk scales.

In the past two decades, there has been an increasing number of high-resolution and high-sensitivity observational studies of the dust polarization in high-mass star-forming regions (cite: 2019FrASS...6....3H). A variety of field structures from hourglass-like shapes (cite: 2009Sci...324.1408G; 2014ApJ...794L..18Q; 2017ApJ...842...66W) to more complex and chaotic morphologies (cite: 1998ApJ...502L..75R; 2009ApJ...695.1399T) have been reported by these studies. The magnetic field in massive star-forming regions is found to be dynamically important from the clump scale to the core scale and the core scale magnetic field does not show strong correlation with the outflow axis (cite: 2014ApJ...792..116Z). Quantitatively, the magnetic field plays an important role in supporting the massive dense cores against gravitational collapse (cite: 2013ApJ...772...69G; 2014A&A...567A.116F).

Despite the significant progress made by the recent polarization observations of massive star formation regions, most of these studies of magnetic fields targeted evolved star-forming regions. Due to the relatively weak polarized dust emission and the limitation of instrumental sensitivity, there are only a handful of single-dish case studies about the magnetic field in early massive star formation regions (cite: 2015ApJ...799...74P; 2018A&A...620A..26J; 2018ApJ...859..151L; 2019ApJ...878...10T; 2019ApJ...883...95S) and there is only one inteferometric study of the magnetic field at the onset of massive star formation in the infrared dark cloud 18310-4 where the magnetic field structure is not well resolved (cite: 2018A&A...614A..64B). The role of magnetic fields in the initial stage of massive star formation remains an open question.

There are two distinct models of massive star formation. The turbulent core accretion model (cite: 2002Natur.416...59M) envisioned that massive stars are formed via the monolithic collapse of massive dense cores in virial equilibrium, where the pressure support comes from turbulence and the magnetic field (cite: 2013ApJ...779...96T). Alternatively, the competitive accretion model (cite: 1997MNRAS.285..201B) proposed that a cluster of low-mass protostars compete with one another to accrete from the natal gas reservoir and the protostars near the center of gravitational potential accreting at higher rates can thus form massive stars. (cite: 2005Natur.438..332K) showed that a sub-virial state is required for the competitive accretion. Thus, the dynamical state of massive dense cores needs to be measured to distinguish between the two models.

Infrared dark clouds (IRDCs), which were first identified as dark regions against the diffuse mid-infrared emission in the Galactic plane (cite: 1996A&A...315L.165P), are believed to harbor the early phase of massive star formation. Recent observations and stability analyses of IRDCs show that the turbulence and the thermal pressure are too weak to provide enough support against the gravity in dense clumps and dense cores (cite: 2011A&A...530A.118P; 2015ApJ...804..141Z; 2016ApJ...833..209O; 2017ApJ...841...97S; 2018ApJ...855....9L), suggesting that magnetic fields must provide significant support to bring the core to equilibrium, or that massive star formation are not in equilibrium. Thus, observational studies of the magnetic field in IRDCs are critical to address the question: does massive star formation start in equilibrium?

At a kinematic distance of $\sim$4.8 kpc, G28.34+0.06 (hereafter G28.34) is a massive ($>10^4 M_{\odot}$) filamentary IRDC that harbors more than ten massive ($10^2 - 10^3 M_{\odot}$) molecular clumps (cite: 1998ApJ...508..721C; 2006A&A...450..569P; 2006ApJ...641..389R; 2006ApJ...653.1325S; 2009ApJ...696..484B; 2017ApJ...840...22L; 2018RNAAS...2...52W). Three prominent clumps, MM1 (also named as P2, C9, or Dragon-Head), MM4 (also named as P1, C2, or Dragon-Belly), and MM9 (also named as S, C1, or Dragon-Tail) are revealed from millimetre (mm) dust continuum and mid-infrared extinction maps (cite: 2006ApJ...641..389R; 2009ApJ...696..484B). All the three clumps are associated with water masers (cite: 2006ApJ...651L.125W; 2008ApJ...672L..33W) and outflows (cite: 2011ApJ...735...64W; 2015ApJ...804..141Z; 2016ApJ...828..100F), indicating that star formation has already began. The large gas reservoir makes them potential sites to study clustered massive star formation.

The three massive clumps are found to be in different evolutionary stages. With low temperatures (cite: 2018RNAAS...2...52W), high CO depletion (cite: 2016A&A...592A..21F) and high level of deuteration (cite: 2010ApJ...713L..50C), the 70 $\ensuremath{\mu}m$ dark clump MM9 appears to be in an early stage of massive star formation. MM9 is resolved into two dense cores (cite: 2013ApJ...779...96T; 2016A&A...592A..21F) where the south core, C1-S, further fragments into two protostellar condensations (cite: 2016ApJ...821L...3T). MM4 has a temperature of $\sim$16 K (cite: 2008ApJ...672L..33W) and is associated with an IR-bright protostellar source with a luminosity of 152 $L_{\odot}$ (cite: 2012A&A...547A..49R). With high-resolution dust continuum observations, the MM4 clump is resolved into six dense cores (MM4-Core1 through MM4-Core6) along the main filament and each core further fragments into several condensations (cite: 2009ApJ...696..268Z; 2011ApJ...735...64W; 2015ApJ...804..141Z; 2019ApJ...873...31K). The more energetic outflow activities, CH$_3$OH maser detections, less deuterium fraction, and higher luminosity in MM4 indicate that MM4 is more evolved than MM9 (cite: 2019ApJ...883..202F). The MM1 clump is warmer (cite: 2008ApJ...672L..33W) than MM4 and MM9 and is associated with an IR-bright protostellar source with a luminosity of 2950 $L_{\odot}$ (cite: 2012A&A...547A..49R). Previous dust continuum observations have resolved MM1 into two fragments (cite: 2009ApJ...696..268Z). The rich organic molecular line emissions in P2-SMA1 indicate that it might be a hot molecular core (cite: 2009ApJ...696..268Z). These observations suggest that MM1 is at a later stage of massive star formation than MM4.

We present 1.3 mm Atacama Large Millimeter/submillimeter Array (ALMA) polarization observations toward clumps MM1, MM4, and MM9 in this paper. In Section [2](#section:observation), we summarize the observation and data reduction. In Section [3](#section:results), we present maps of dust continuum, polarized dust emission, and molecular line emission, and derive the magnetic field strength. In Section [4](#section:discussion), we discuss the dynamical state, outflow-magnetic field alignment, and fragmentation, and compare the orientations of magnetic fields, local gravity, and intensity gradient. In Section [5](#section:summary), we provide a summary of this paper.

# Observation

| Source | Field | $\alpha_{\mathrm{J2000}}$ | $\delta_{\mathrm{J2000}}$ |
|:--:|:--:|:--:|:--:|
| MM1 | MM1 | $18^{\mathrm{h}}42^{\mathrm{m}}52^{\mathrm{s}}.06$ | $-03\ensuremath{^\circ}59\ensuremath{'}54\ensuremath{''}.3$ |
| MM4 | MM4_1 | $18^{\mathrm{h}}42^{\mathrm{m}}51^{\mathrm{s}}.05$ | $-04\ensuremath{^\circ}03\ensuremath{'}08\ensuremath{''}.6$ |
|  | MM4_2 | $18^{\mathrm{h}}42^{\mathrm{m}}50^{\mathrm{s}}.69$ | $-04\ensuremath{^\circ}03\ensuremath{'}13\ensuremath{''}.4$ |
|  | MM4_3 | $18^{\mathrm{h}}42^{\mathrm{m}}50^{\mathrm{s}}.39$ | $-04\ensuremath{^\circ}03\ensuremath{'}19\ensuremath{''}.0$ |
|  | MM4_4 | $18^{\mathrm{h}}42^{\mathrm{m}}49^{\mathrm{s}}.88$ | $-04\ensuremath{^\circ}03\ensuremath{'}24\ensuremath{''}.5$ |
| MM9 | MM9_1 | $18^{\mathrm{h}}42^{\mathrm{m}}46^{\mathrm{s}}.48$ | $-04\ensuremath{^\circ}04\ensuremath{'}14\ensuremath{''}.3$ |
|  | MM9_2 | $18^{\mathrm{h}}42^{\mathrm{m}}46^{\mathrm{s}}.91$ | $-04\ensuremath{^\circ}04\ensuremath{'}09\ensuremath{''}.3$ |

: Source coordinates

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Date$^{a}$ | Configuration | $N_{ant}$$^{b}$ | Bandpass | Gain | Flux | Pol | Sources |
|  |  |  | calibrator | calibrator | calibrator | calibrator |  |
| 2017 Apr 18 | C40-3 | 48 | J1751+0939 | J1851+0035 | Titan | J1751+0939 | MM1, MM4, MM9 |
| 2018 Apr 29 | C43-3 | 43 | J1751+0939 | J1851+0035 | Titan | J1751+0939 | MM1, MM4, MM9 |
| 2018 Jun 23 | C43-1 | 47 | J1751+0939 | J1851+0035 | J1751+0939 | J1924-2914 | MM4, MM9 |
| 2018 Jun 29 | C43-1 | 45 | J1751+0939 | J1851+0035 | J1751+0939 | J1924-2914 | MM4, MM9 |

: Observational parameters

Table notes: $^{a}$ Observations were under precipitable water vapor (PWV) ranging from 1.3 to 2.1 mm. $^{b}$ Number of antennas.

Figure [1](#fig:figG28) presents an overview of G28.34 in IRAM-30m 1.3mm dust continuum (cite: 2006ApJ...641..389R). The observations of three massive clumps (MM1, MM4, MM9) in G28.34 were carried out with the ALMA between 2017 Apr 18 to 2018 Jun 29 under projects 2016.1.00248.S (Cycle 4; PI: Zhang) and 2017.1.00793.S (Cycle 5; PI: Zhang). An ALMA execution on 2017 April 21 under project 2016.1.00248.S was failed due to some correlator issues and was not used for our analysis. Tables [1](#tab:sources) and [2](#tab:observation) list the detailed information of the observations. The total on-source time is 17 minutes for MM1 and 17 minutes (in C40-3 or C43-3 configuration) + 8 minutes (in C43-1 configuration) for each fields of MM4 and MM9. The receiver was tuned to cover frequencies $\sim$215.5-219.5 GHz and $\sim$232.5-234.5 GHz (band 6), with a total bandwidth of 5.6 GHz (three basebands, with 1.875 GHz effective bandwidth each) for the dust continuum emission in the full polarization mode. Four spectral windows in another baseband were set to cover the CO (2-1), OCS (19-18), $^{13}$CS (5-4), and N$_2$D$^+$ (3-2) lines with a channel width of 122 kHz (0.16 km s$^{-1}$) over a bandwidth of 58.6 MHz ($\sim$76 km s$^{-1}$).

![](./A_G28_all.pdf)

The data taken in 2017 Apr 18 were manually calibrated by the authors using the Common Astronomy Software Applications (cite: 2007ASPC..376..127M) and the rest of the data were calibrated by the ALMA supporting staff. The systematic flux uncertainty of ALMA at Band 6 due to calibration is $\sim$10 %. We performed two iterations of phase-only self-calibrations on the continuum data using the CASA. The molecular line cubes and Stokes $I$, $Q$, and $U$ maps of dust continuum were produced from the visibility data using the CASA task *TCLEAN* with a briggs weighting parameter of robust = 0.5. The maps for MM4 and MM9 are constructed from four-pointing mosaic of MM4_1, MM4_2, MM4_3, and MM4_4, and two-pointing mosaic of MM9_1 and MM9_2, respectively. The synthesized beams of the maps are 0$\ensuremath{''}$.8-0$\ensuremath{''}$.9 $\times$ 0$\ensuremath{''}$.6-0$\ensuremath{''}$.7 ($\sim$0.02-0.015 pc at a source distance of 4.8 kpc). The maximum recoverable scale[^2] is $\sim$7$\ensuremath{''}$ ($\sim$0.14 pc at 4.8 kpc) for MM1 and $\sim$13$\ensuremath{''}$ ($\sim$0.3 pc at 4.8 kpc) for MM4 and MM9. After primary beam correction, the 1$\sigma$ rms noises of the Stokes $I$ maps of dust continuum reach $\sim$300, 80, and 60 $\mu$Jy/beam for MM1, MM4, and MM9, respectively, while the the Stokes $Q$/$U$ maps have rms noises of $\sim$35 $\mu$Jy/beam for MM1 and $\sim$15 $\mu$Jy/beam for MM4 and MM9. The sensitivity of the primary beam response corrected spectral line cubes for MM1, MM4, and MM9 is $\sim$2.2, 1.2, and 1.4 mJy/beam, respectively, with a velocity channel width of 0.5 km s$^{-1}$.

Because the polarized intensity and polarized percentage are defined as positive values, the measured quantities of the two parameters are biased toward larger values (cite: 2006PASP..118.1340V). The debiased polarized intensity $PI$ and its corresponding uncertainty $\sigma_{PI}$ are calculated as: $$\begin{equation}
PI = \sqrt{Q^2 + U^2 - \sigma_{Q/U}^2},
\end{equation}$$ and $$\begin{equation}
\sigma_{PI} = \sqrt{2}\sigma_{Q/U},
\end{equation}$$ where $\sigma_{Q/U}$ is the 1$\sigma$ rms noise of the $Q$/$U$ maps. The debiased polarization percentage $P$ and its uncertainty $\delta P$ are therefore derived by: $$\begin{equation}
P = \frac{PI}{I},
\end{equation}$$ and $$\begin{equation}
\delta P = \sqrt{(\frac{\sigma_{PI}^2}{I^2} + \frac{\sigma_{I}^2 (Q^2 + U^2)}{I^4})},
\end{equation}$$ where $\sigma_{I}$ is the 1$\sigma$ rms noise of the $I$ map.

Finally, the polarization position angle $\theta$ and its uncertainty $\delta \theta$ (cite: 1993A&A...274..968N) are estimated to be: $$\begin{equation}
\theta = \frac{1}{2} \tan ^{-1} (\frac{U}{Q}),
\end{equation}$$ and $$\begin{equation}
\delta \theta = \frac{1}{2} \sqrt{\frac{\sigma_{Q/U}^2}{(Q^2 + U^2)}},
\end{equation}$$

# Results

## Dust continuum

The 1.3 mm continuum emissions of three clumps are shown in Figure [2](#fig:figG28B). In this subsection, we briefly overview the dust continuum emissions in MM4 and MM9 and focus on interpreting the dust continuum of MM1.

![](./G28MM1_cont_mk_psc_ce_cont_pb_vec_B.pdf)

![](./G28MM4_cont_mk_psc_ce_cont_pb_vec_B.pdf)

![](./G28MM9_cont_mk_psc_ce_cont_pb_vec_B.pdf)

The MM4 region was studied by (cite: 2015ApJ...804..141Z), (cite: 2018ApJ...855L..25K), and (cite: 2019ApJ...873...31K), which revealed six cores (MM4-Core1 to MM4-Core6 from northeast to southwest) along the natal filament and identified the condensation-scale fragment structures in the continuum emission. We adopt the condensations identified by (cite: 2015ApJ...804..141Z) and (cite: 2019ApJ...873...31K) in our study. In MM9, two massive dense cores (C1-N and C1-S) were identified by (cite: 2013ApJ...779...96T). C1-S was further resolved into two protostellar condensations (cite: 2016ApJ...821L...3T; 2018ApJ...867...94K). Due to sensitivity limitation, the two more candidate protostellar sources (cite: 2016ApJ...821L...3T) away from C1-N and C1-S are not detected in our ALMA 1.3 mm continuum.

The continuum emission of MM1 is resolved down to condensation scales (see Figure [2](#fig:figG28B)). The emission is dominated by a major core (hereafter MM1-Core1) in the west, which further fragments into several condensation structures. Several more condensations are detected in the east and in the southwest, which are connected to the main core. Another strong condensation is seen to the northwest of the main core. There appears to be two additional 6$\sigma$ continuum peaks to the northeast and to the east of MM1-Core1.

To characterize the dense structures in MM1, we applied the dendrogram (cite: 2008ApJ...679.1338R) technique on the dust continuum using the Python package *astrodendro*. The dendrogram abstracts the changing topology of the isosurfaces as a function of contour levels and tracks the hierarchical structure over a range of scales (cite: 2008ApJ...679.1338R). This algorithm mainly has three parameters: the minimum value for the structure to be considered (min_value), the minimum height required for a structure to be retained as independent (min_delta), and the minimum number of pixels for a structure to be considered (min_npix). Following similar works in (cite: 2018ApJ...853..160C) and (cite: 2018ApJ...862..105L), we adopt min_value = 4$\sigma$, min_delta = 1$\sigma$, and set min_npix to be the number of pixels in half beam area. We note that the combination of min_value and min_delta ensures that the identified structures have peak fluxes $>5 \sigma$.

![](./G28MM1_cont_mk_psc_ce_dendro.pdf)

The structures identified by dendrogram in MM1 are shown in Figure [3](#fig:figMM1dendro). The dendrogram reports the coordinates, the integrated flux ($S_{\mathrm{int}}$), the FWHM sizes along the major and minor axes, and the position angles ($\theta_{\mathrm{dendro}}$) of the structures. The parameters derived by dendrogram are reported in Table [3](#tab:dendro). The brightest two sources, Condensation 1 and Condensation 2, corresponds to P2-SMA1 and P2-SMA2 in (cite: 2009ApJ...696..268Z). We note that nearly all condensations in MM1 are smaller than the beam area except for Condensation 8, which is marginally resolved.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | RA | DEC | $S_{\mathrm{int}}$$^{a}$ | FWHM$^{b}$ | $\theta_{\mathrm{dendro}}$ | $T$ | $M$ | $N_{\mathrm{H_2}}$ | $n_{\mathrm{H_2}}$ |
|  | (h:m:s) | (d:m:s) | (mJy) | $\ensuremath{''} \times \ensuremath{''}$ | ($\ensuremath{^\circ}$) | \(K\) | ($M_{\odot}$) | ($10^{23}$ cm$^{-2}$) | ($10^6$ cm$^{-3}$) |
| MM1-Core1 | 18:42:52.06 | -3:59:54.04 | 745.4 | 2.8 $\times$ 2.6 | -138.8 | 30.0 | 212.4 | 5.0 | 3.2 |
| Condensation 1 | 18:42:51.98 | -3:59:54.06 | 258.0 | 0.8 $\times$ 0.6 | 126.2 | 57.0 | 35.5 | $>$13.6 | $>$29.2 |
| Condensation 2 | 18:42:52.12 | -3:59:54.23 | 57.7 | 0.6 $\times$ 0.4 | 177.8 | 23.6 | 21.9 | $>$23.5 | $>$56.5 |
| Condensation 3 | 18:42:52.08 | -3:59:53.41 | 25.0 | 0.4 $\times$ 0.3 | 97.0 | 23.6 | 9.5 | $>$20.4 | $>$65.6 |
| Condensation 4 | 18:42:52.17 | -3:59:51.35 | 26.8 | 0.7 $\times$ 0.5 | 159.5 | 24.1 | 9.9 | $>$5.7 | $>$11.8 |
| Condensation 5 | 18:42:52.2 | -3:59:58.24 | 9.7 | 0.6 $\times$ 0.5 | 53.9 | 17.3 | 5.5 | $>$4.7 | $>$11.0 |
| Condensation 6 | 18:42:52.16 | -3:59:56.16 | 9.8 | 0.7 $\times$ 0.4 | -148.4 | 23.6 | 3.7 | $>$4.0 | $>$8.8 |
| Condensation 7 | 18:42:51.96 | -3:59:46.8 | 7.0 | 0.6 $\times$ 0.5 | -155.7 | 15.2 | 4.7 | $>$3.2 | $>$8.8 |
| Condensation 8 | 18:42:52.49 | -3:59:55.26 | 12.2 | 1.1 $\times$ 0.7 | 170.7 | 21.9 | 5.1 | $>$1.9 | $>$2.5 |
| Condensation 9 | 18:42:52.66 | -3:59:55.19 | 2.8 | 0.5 $\times$ 0.4 | 156.2 | 17.7 | 1.6 | $>$1.8 | $>$5.2 |
| Condensation 10 | 18:42:51.98 | -3:59:57.14 | 2.2 | 0.5 $\times$ 0.4 | 149.3 | 26.4 | 0.7 | $>$1.1 | $>$2.8 |
| Condensation 11 | 18:42:51.56 | -3:59:51.66 | 1.5 | 0.4 $\times$ 0.3 | 154.8 | 20.2 | 0.7 | $>$1.2 | $>$4.2 |
| Condensation 12 | 18:42:52.43 | -3:59:56.17 | 1.4 | 0.4 $\times$ 0.3 | 158.5 | 19.4 | 0.7 | $>$1.6 | $>$5.4 |
| Condensation 13 | 18:42:52.38 | -3:59:51.5 | 0.9 | 0.4 $\times$ 0.3 | 161.6 | 19.8 | 0.4 | $>$1.1 | $>$4.2 |
| Condensation 14 | 18:42:52.64 | -3:59:56.81 | 1.2 | 0.6 $\times$ 0.2 | 179.3 | 17.7 | 0.6 | $>$1.3 | $>$3.9 |
| Condensation 15 | 18:42:52.08 | -3:59:58.52 | 1.7 | 0.7 $\times$ 0.3 | 176.0 | 21.1 | 0.7 | $>$1.0 | $>$2.6 |
| MM4-Core4 | 18:42:50.31 | -4:03:21.07 | 68.3 | 2.9 $\times$ 1.8 | 45.9 | 16.0 | 43.0 | 1.5 | 1.1 |

: Physical parameters of dense structures

Table notes: $^{a}$ Integrated flux. $^{b}$ Without deconvolution.

With the assumptions of the optically thin dust emission, isothermal, and a **gas-to-dust ratio $\Lambda$ of 100:1** (cite: 1991ApJ...381..250B), the gas mass $M$ of the dense structures can be calculated with $$\begin{equation}
M = \frac{\Lambda S_{\mathrm{int}} d^2}{ \kappa_{\nu} B_{\nu} (T)}, \label{eq:M}
\end{equation}$$ where $d = 4.8$ kpc is the distance to G28.34, $\kappa_{\nu} = (\nu / 1 \mathrm{THz})^{\beta}$ is the dust opacity (cite: 1983QJRAS..24..267H) in m$^2$ kg$^{-1}$, and $B_{\nu} (T)$ is the Planck function at temperature $T$. Multi-wavelength observations toward massive star-forming regions usually found dust emissivity indexes $\beta$ of $\sim$1.5 (cite: 2007A&A...466.1065B; 2007ApJ...654L..87C). Adopting this value, the $\kappa_{\nu}$ is estimated to be 0.11 m$^2$ kg$^{-1}$. The gas temperature map of the entire IRDC G28.34 was derived by (cite: 2018RNAAS...2...52W) with combined VLA and Effelsberg 100m data (cite: 2008ApJ...672L..33W) of the NH$_3$ (1,1) and (2,2) lines at a resolution of 6$\ensuremath{''}$.5 $\times$ 3$\ensuremath{''}$.6. The temperatures of the condensations in MM1 ranges from 15 K to 27 K. Considering that Condensation 1 is a hot molecular core (cite: 2009ApJ...696..268Z), the NH$_3$ (1,1) and (2,2) lines, which are cold gas tracers (cite: 1983ARA&A..21..239H), might have underestimated the gas temperature in this condensation. As a good approximation of dust heated by a central source with luminosity $L_{*}$, the dependence of dust temperature $T$ on radius $r$ behaves like a simple power-law (cite: 1993ApJ...414..759T): $$\begin{equation}
T = T_{0} (\frac{r}{r_{0}})^{-q} (\frac{L_{*}}{L_{0}})^{q/2}, \label{eq:T}
\end{equation}$$ where $T_0$ is the fiducial dust temperature at a fiducial radius $r_0$ from a central source with luminosity $L_0$ and $q$ is the power-law index. The luminosity of the embedded protostellar object in Condensation 1 is $L_{*} = 2950 L_{\odot}$ (cite: 2012A&A...547A..49R). Adopting $T_0 = 38$ K, $r_0 =$ 100 AU, $L_0 =$ 1 $L_{\odot}$, $q=0.4$ (cite: 2001A&A...365..440M), and a background temperature of 20 K (cite: 2018RNAAS...2...52W), the average temperature of Condensation 1 within a radius of mean FWHM (FWHM$_{mean}$) is measured to be 57.0 K. A temperature of 30 K (cite: 2008ApJ...672L..33W) is adopted for MM1-Core1. With a similar approach and adopting a temperature of $\sim$16 K (cite: 2008ApJ...672L..33W), we also derived the mass for MM4-Core4. The estimated masses and temperatures are listed in Table [3](#tab:dendro).

The average column density $N_{\mathrm{H_2}}$ and volume density $n_{\mathrm{H_2}}$ within each core and condensation are measured using a radius equal to the FWHM$_{\mathrm{mean}}$: $$\begin{equation}
N_{\mathrm{H_2}} = \frac{M}{\mu_{\mathrm{H_2}} m_{\mathrm{H}} \pi \mathrm{FWHM^2_{mean}}},
\end{equation}$$ $$\begin{equation}
n_{\mathrm{H_2}} = \frac{3M}{4\mu_{\mathrm{H_2}} m_{\mathrm{H}} \pi \mathrm{FWHM^3_{mean}}},
\end{equation}$$ where $\mu_{\mathrm{H_2}} = 2.86$ is the mean molecular weight per hydrogen molecule (cite: 2013MNRAS.432.1424K; 2015MNRAS.450.1094P) and $m_{\mathrm{H}}$ is the atomic mass of hydrogen. The derived column and volumn densities are also listed in Table [3](#tab:dendro). The estimated $n_{\mathrm{H_2}}$ and $N_{\mathrm{H_2}}$ of the condensations in MM1 and the two cores are generally comparable to those in other IRDCs and in more evolved massive star-forming regions (cite: 2018ApJ...862..105L; 2018ApJ...855....9L; 2019ApJS..241....1C; 2019ApJ...886..102S). The main uncertainty of the calculations comes from the uncertainty of $\kappa_{\nu}$ (cite: 1995P&SS...43.1333H). We conservatively adopt a fractional uncertainty of 50% (cite: 2014A&A...562A.138R) for $M$, $N_{\mathrm{H_2}}$, and $n_{\mathrm{H_2}}$. We note that since most condensations are unresolved, the derived $N_{\mathrm{H_2}}$ and $n_{\mathrm{H_2}}$ for these condensations should be regarded as lower limits.

## Polarized emission of dust

![](G28MM9_cont_mk_psc_ce_cont_pb_vec_PI.pdf)

The plane-of-sky magnetic field orientation can by derived by rotating the orientation of the observed linear dust polarization of the electric field by 90$\ensuremath{^\circ}$ with the assumption that the shortest axis of dust grains is perfectly aligned with the magnetic field. Figure [2](#fig:figG28B) shows the inferred magnetic field orientations overlaid on the Stokes $I$ maps toward the massive clumps MM1, MM4, and MM9. The ALMA maps reveal compact structures in the clumps down to scales of $\sim$0.02 pc (condensation scale).

The magnetic field structure in MM1 is well resolved and shows a radial pattern, indicating that the field might be dragged towards the center by gravity. We further compare the magnetic field with the local gravity in Section [3.6](#section:pil).

In MM4, strong polarized emissions are detected in MM4-Core3, MM4-Core4, and MM4-Core5, while the polarized emissions in MM4-Core1, MM4-Core2, and MM4-Core6 are only marginally detected. The polarized emission in Core5 is compact and centered at the continuum peak in the west of the core, showing a northwest-southeast orientated magnetic field that is orthogonal to the parent filament. The polarized emission in MM4-Core4 is the most extended in MM4 and the magnetic field in the northern part of this core is well resolved, while the magnetic field in the southern part is only partially resolved. Similar to Core5, the magnetic field in Core4 shows a northwest-southeast orientation. The magnetic field in Core3 can be divided into three groups: the magnetic field in the center shows a east-west orientation; the magnetic field in the northeastern part shows a northeast-southwest orientation; and the magnetic field in the southern part rotates smoothly, showing a C-shaped morphology.

In MM9, the polarized emission is confined at the continuum peak (C1-Sa) and the magnetic field shows a northeast-southwest orientation, following the parent filament.

In Figure [4](#fig:figpolmap), we show contours of the polarization emission intensity overlaid on the polarization percentage maps. In Figure [5](#fig:figpi), the $P$-$I$ relation in the three clumps is shown. The polarization percentage is detected down to 0.3%, 0.8%, and 1.3% in MM1, MM4, and MM9, respectively. Clear trends of decreasing $P$ with increasing $I$ are seen in MM1 and MM4. For the $P$-$I$ relations in MM1 and MM4, the polarization percentage at a constant $I$ shows broad scatters up to a order of magnitude, which indicates that the depolarization seen in the two clumps are the combined results of different factors. Using $\chi^2$ minimization, we fit the $P$-$I$ anti-correlations in MM1 and MM4 where $P/\delta P >3$ with a simple power-law $P \propto I^{\alpha}$ and the power-law slope index $\alpha$ is estimated to be approximately -0.3 and -0.7 for MM1 and MM4, respectively. Due to the large scattering in the $P$-$I$ relations, we refrain from interpreting the absolute value of the slope indexes. However, we notice that the $P$-$I$ relation in MM1 is shallower than that in MM4, which may suggest the grain alignment efficiency is improved by additional internal radiation in more evolved star formation regions. Similar trend of shallower $P$-$I$ relation in more evolved cores is also seen in the low-mass star formation dense cores in the Ophiuchus cloud (cite: 2018ApJ...859....4K; 2018ApJ...861...65S; 2019ApJ...877...43L; 2019ApJ...880...27P). In MM9, the polarized percentages is $\sim$2%.

## Molecular lines

Figure [6](#fig:figline) show the zeroth-moment maps of N$_2$D$^+$ (3-2), $^{13}$CS (5-4), and OCS (19-18) in MM1, MM4, and MM9. The line emissions in three clumps share some similar patterns. The $^{13}$CS and OCS lines show similar emission morphology and present the strongest emission mostly near the dust continuum peaks. The distribution of the N$_2$D$^+$ emisison is almost anti-correlated with that of the $^{13}$CS and OCS emission, indicating that the $^{13}$CS and OCS molecules are likely depleted in the cold and dense gas highlighted by the N$_2$D$^+$ emisison.

In MM1, the emissions from $^{13}$CS and OCS peak at Condensation 1. The N$_2$D$^+$ line shows strong emissions to the north of Core1, which appears to be extended and probably links Condensation 7 with MM1-Core1. There are also faint N$_2$D$^+$ emissions in Condensation 10 and between Condensations 5 and 6. The lack of N$_2$D$^+$ detection in the dust emission region indicates that MM1 is in a later evolution stage of star formation.

In MM4, the N$_2$D$^+$ emission is detected in MM4-Core1 through Core5, while the $^{13}$CS and OCS emissions are detected in MM4-Core1 through Core4. The line emission of three molecules are mostly overlapping with dust continuum emissions, except that there appears to be an N$_2$D$^+$ emission peak to the east of MM4-Core1 and an OCS emission peak to the south of MM4-Core1, which are not associated with the dust emission above 3$\sigma$. The $^{13}$CS and N$_2$D$^+$ maps generally agree with previous observations reported in (cite: 2015ApJ...804..141Z), but show improvements in detecting fainter and more extended emissions.

In MM9, the $^{13}$CS and OCS emissions are only marginally detected in C1-S. The N$_2$D$^+$ emission in core C1-S are consistent with previous observations (cite: 2013ApJ...779...96T; 2016ApJ...821L...3T; 2018ApJ...867...94K). Due to the limitation of sensitivity, the N$_2$D$^+$ emission in core C1-N is only marginally detected.

## Molecular outflows in MM1

The molecular outflows in MM4 (cite: 2011ApJ...735...64W; 2015ApJ...804..141Z) and MM9 (cite: 2016ApJ...828..100F; 2016ApJ...821L...3T; 2018ApJ...867...94K) have been widely studied, so we only present the outflows of MM1 in CO (2-1) in this paper (see Figure [7](#fig:figMM1CO)). The outflow emissions in MM1 are detected throughout the velocity coverage of our observations ($\sim$41 km s$^{-1}$ to $\sim$116 km s$^{-1}$). Figure [7](#fig:figMM1CO)(a) shows the integrated emissions of CO in velocity ranges from 45 km s$^{-1}$ to 74 km s$^{-1}$ for the blue-shifted lobe, and 84 km s$^{-1}$ to 115 km s$^{-1}$ for the red-shifted lobe. The data channels with velocities $<$84 km s$^{-1}$ and $>$74 km s$^{-1}$ are excluded in the integration to avoid the contamination of surrounding diffuse gas. We also excluded channels with velocities $<$45 km s$^{-1}$ or $>$115 km s$^{-1}$ in the integration due to domination of instrumental noise in these edge channels. Figure [7](#fig:figMM1CO)(b) shows the integrated emission of the high-velocity (HV) outflow gas with velocities $>$20 km s$^{-1}$ with respect to MM1’s ambient velocity. The outflows in MM1 show clustered overlapping structures. The HV outflow components are highly collimated and show some jet-like structures. Due to the complex structure of the outflows and the lack of shock tracers (e.g., SiO) to trace the vicinity outflow gas, we refrain from detailed analysis of the MM1 outflow and leave it to future studies.

## Magnetic field strength of MM1-Core1 and MM4-Core4

The Davis-Chandrasekhar-Fermi (cite: 1951PhRv...81..890D; 1953ApJ...118..113C) method and its modified form have been widely used to estimate the plane-of-sky magnetic field strength ($B_{\mathrm{pos}}$) by interpreting the observed angular dispersion ($\Delta\theta$) of polarization position angles as a MHD-wave component of the field perturbed by turbulent motions. With the small angle approximation, the $B_{\mathrm{pos}}$ is estimated as (cite: 2004ApJ...600..279C): $$\begin{equation}
\label{eq:eqcf}
B_{\mathrm{pos}} = Q_c \sqrt{\mu_0 \rho }\frac{\sigma_{\mathrm{turb}}}{\Delta\theta}
\end{equation}$$ in SI units or CGS units, where $\mu_0$ is the permeability of vacuum, $\rho = \mu_{\mathrm{H_2}} m_{\mathrm{H}} n_{\mathrm{H_2}}$ is the density of the gas, $\sigma_{\mathrm{turb}}$ is the line-of-sight non-thermal velocity dispersion, and $Q_c$ is a correction factor.

Further approaches have been made on modifying the DCF method toward more accurately quantifying the angular dispersion in the DCF formula through the angular dispersion function (ADF) analysis (cite: 2008ApJ...679..537F; 2009ApJ...696..567H; 2009ApJ...706.1504H; 2016ApJ...820...38H) or the unsharp masking analysis (cite: 2017ApJ...846..122P). Specifically, (cite: 2016ApJ...820...38H) derived the ADF for polarimetric images obtained from an interferometer, taking into account variations in the large-scale magnetic field, the effects of signal integration along the line of sight and within the beam, and the large-scale filtering effect of interferometers. The ADF is given by (cite: 2016ApJ...820...38H):

$$\begin{align}
1 - \langle \cos \lbrack \Delta \Phi (l)\rbrack \rangle =  \sum_{j=1}^{\infty}a_{2j} l^{2j} + \left[ \frac{N}{1+N \langle B_0^2 \rangle/ \langle B_{\mathrm{t}}^2 \rangle } \right] \nonumber \\
\times \Bigg\{ \frac{1}{N_1} \left[ 1 - e^{-l^2/2(\delta^2+2W_1^2)}\right] \nonumber \\+ \frac{1}{N_2} \left[ 1 - e^{-l^2/2(\delta^2+2W_2^2)}\right] \nonumber \\- \frac{2}{N_{12}} \left[ 1 - e^{-l^2/2(\delta^2+W_1^2+W_2^2)}\right] \Bigg\},
\end{align}$$

where $\Delta \Phi (l)$ is the angular difference of two line segments separated by a distance $l$, $\delta$ is the turbulent correlation length, the summation is the Taylor expansion of the ordered component of the ADF, $B_{\mathrm{t}}$ is the turbulent component of the magnetic field, $B_0$ is the ordered magnetic field, $W_1$ and $W_2$ are the standard deviation of the two Gaussian profiles of the synthesized beam and the large-scale filtering effect (i.e., the FWHM divided by $\sqrt{8 \ln{2}}$), and $N$ is the number of turbulent cells probed by the telescope beam given by: $$\begin{equation}
N_1 = \frac{(\delta^2 + 2W_1^2)\Delta\ensuremath{'}}{\sqrt{2\pi}\delta^3},
\end{equation}$$ $$\begin{equation}
N_2 = \frac{(\delta^2 + 2W_2^2)\Delta\ensuremath{'}}{\sqrt{2\pi}\delta^3},
\end{equation}$$ $$\begin{equation}
N_{12} = \frac{(\delta^2 + W_1^2 + W_2^2)\Delta\ensuremath{'}}{\sqrt{2\pi}\delta^3},
\end{equation}$$ $$\begin{equation}
N = \left( \frac{1}{N_1} + \frac{1}{N_2} - \frac{2}{N_{12}} \right)^{-1},
\end{equation}$$ where $\Delta\ensuremath{'}$ is the effective thickness of the concerned region through which the signals are integrated along the line of sight. The turbulent component of the ADF is $$\begin{equation*}
\begin{aligned}
b^2(l) = \left[ \frac{N}{1+N \langle B_0^2 \rangle/ \langle B_{\mathrm{t}}^2 \rangle } \right]
\times \Big[ \frac{1}{N_1}  e^{-l^2/2(\delta^2+2W_1^2)} \\+ \frac{1}{N_2} e^{-l^2/2(\delta^2+2W_2^2)} - \frac{2}{N_{12}}  e^{-l^2/2(\delta^2+W_1^2+W_2^2)} \Big],
\end{aligned}
\end{equation*}$$ The ordered magnetic field strength can be derived by (cite: 2009ApJ...706.1504H): $$\begin{equation}
B_0 \simeq \sqrt{\mu_0 \rho} \sigma_{\mathrm{turb}} \left[ \frac{\langle B_{\mathrm{t}}^2 \rangle}{\langle B_0^2 \rangle} \right]^{-1/2}
\end{equation}$$ in SI units or CGS units.

The $\Delta\ensuremath{'}$ is estimated as the width at half of the maximum of the normalized auto-correlation function of the integrated normalized polarized flux (cite: 2009ApJ...706.1504H). The $\Delta\ensuremath{'}$ of MM1-Core1 and MM4-Core4 are estimated to be 2$\ensuremath{''}$.5 and 2$\ensuremath{''}$.2, respectively, which are consistent with the FWHMs derived from dendrogram.

The information about the nonthermal (turbulent) velocity dispersion ($\sigma_{\mathrm{turb}}$) of the gas, which is required to calculate the $B_{\mathrm{pos}}$, is determined from previous NH$_3$ observations. The line-of-sight velocity dispersions of NH$_3$ ($\sigma_{\mathrm{NH_3}}$) for MM1-Core1 and MM4-Core4 are 1.4 km s$^{-1}$ (cite: 2008ApJ...672L..33W) and 0.47 km s$^{-1}$ (cite: 2012ApJ...745L..30W), respectively. The $\sigma_{\mathrm{turb}}$ is calculated with the relation $$\begin{equation}
\sigma^2_{\mathrm{turb}} = \sigma^2_{\mathrm{NH_3}} - \frac{k_\mathrm{B} T}{m_\mathrm{NH_3}},
\end{equation}$$ where $m_\mathrm{NH_3}$ is the mass of the NH$_3$ molecule. The nonthermal velocity dispersions are estimated to be 1.4 km s$^{-1}$ and 0.46 km s$^{-1}$ for MM1-Core1 and MM4-Core4, respectively. The corresponding 3D turbulent velocity dispersion $\sigma_{\mathrm{turb,3D}} = \sqrt{3}\sigma_{\mathrm{turb}}$ are 2.42 km s$^{-1}$ and 0.80 km s$^{-1}$ for MM1-Core1 and MM4-Core4, respectively.

Figures [8](#fig:figADFMM1) and [9](#fig:figADFMM4) show the angular dispersion functions and the turbulent component of the ADF derived from the polarization segments with $PI/\sigma_{PI} > 3$ in MM1-Core1 and MM4-Core4 (see Figure [2](#fig:figG28B)), respectively. To avoid large uncertainties due to sparse sampling at large spatial scales (cite: 2019ApJ...877...43L), we fit the ADFs of MM1-Core1 and MM4-Core4 over $l < 2.6\ensuremath{''}$ and $l < 3.4\ensuremath{''}$, respectively, where the angular dispersion function is relatively smooth and shows well-correlated relations with $l$. The best fit is obtained via $\chi^2$ minimization. The $B_{\mathrm{pos}}$ for MM1-Core1 and MM4-Core4 are calculated to be 1.6 mG and 0.32 mG, respectively. The parameters derived from the ADF method are listed in Table [4](#tab:ADF). We note that since the polarization observations in MM4-Core4 only cover part of this core, an assumption of constant turbulent-to-ordered magnetic field ratio in the core needs to be adopted. According to (cite: 2016ApJ...820...38H), the $B_{\mathrm{pos}}$ estimated from the ADF method is accurate within a factor of $\sim$3.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | $n_{\mathrm{H_2}}$ | $\sigma_{\mathrm{turb}}$ | $(\langle  B_{\mathrm{t}}^2 \rangle$/$\langle B_0^2 \rangle)^{\frac{1}{2}}$ | $B_{\mathrm{pos}}$ | $\delta$ | $N$ | $Q_c'$$^{a}$ |
|  | ($10^6$ cm$^{-3}$) | (km s$^{-1}$) |  | (mG) | ($\ensuremath{''}$) |  |  |
| MM1-Core1 | 3.2 | 1.4 | 1.2 | 1.6 | 0.53 | 4.1 | 0.50 |
| MM4-Core4 | 1.1 | 0.46 | 1.2 | 0.32 | 0.38 | 6.9 | 0.38 |

: Physical parameters relevant to the ADF analysis

Table notes: $^{a}$ Equivalent correction factor $Q_c' = 1/\sqrt{N}$ for the signal-integration effect.

Since the line-of-sight component of the magnetic field is unknown, the 3D mean ordered magnetic field strength $B$ is calculated with the statistical relation $B = 4 B_\mathrm{pos}/\pi$ (cite: 2004ApJ...600..279C). Then the 3D Alfvén velocity is estimated as $$\begin{equation}
V_{\mathrm{A,3D}} = \frac{B}{\sqrt{\mu_0 \rho}}
\end{equation}$$ in SI units or CGS units. The $V_{\mathrm{A,3D}}$ for MM1-Core1 and MM4-Core4 are 1.5 km s$^{-1}$ and 0.51 km s$^{-1}$, respectively. The Alfvén Mach number $Mach_{\mathrm{A}} = \sigma_{\mathrm{turb,3D}} / V_{\mathrm{A,3D}}$ of MM1-Core1 and MM4-Core4 are estimated to be 1.61 and 1.57, respectively, which means that the two cores are in super-Alfvénic states (weakly magnetized)

## Comparison of orientations of magnetic field, intensity gradient, and local gravity

Star-forming regions are subject to various forces such as gravity, gas pressure, magnetic force, and other possible forces. (cite: 2012ApJ...747...79K) has used ideal magnetohydrodynamics (MHD) force equations to describe the interaction of the forces and developed a technique (the polarization-intensity gradient-local gravity method, hereafter the PIL method) to measure the local magnetic field strength. In this method, the gradient of intensity is assumed to trace the resulting direction of particle motion in the MHD force equation. Following the approach of the PIL method, we calculate the angular differences among the magnetic field, the intensity gradient (IG), and the local gravity (LG), and study the relative importance of the magnetic field and local gravity at different positions.

The surrounding mass distribution needs to be taken into account when calculating the local gravitational force at a given position in a map (cite: 2012ApJ...747...79K). Adopting constant temperatures for MM4 and MM9, and adopting the previously mentioned temperature profile (see section [3.1](#section:cont)) for MM1, we derived the gas mass ($m_{i}$) for each pixel of the map with $I > 3\sigma_{I}$ for the three clumps using Equation [\[eq:M\]](#eq:M). The local gravity force at position $\boldsymbol{r_j}$ is then given by $$\begin{equation}
\boldsymbol{g_{j}(r)} = G \sum\limits_{i=1}^{n} \frac{m_{i}m_{j}}{\vert \boldsymbol{r_j} - \boldsymbol{r_i} \vert ^2} \boldsymbol{e_{ij}},
\end{equation}$$ where $\boldsymbol{e_{ij}}$ is the unit vector indicating the direction between position $\boldsymbol{r_i}$ and $\boldsymbol{r_j}$. The orientations of the local gravity force ($\theta_{\mathrm{LG}}$) of the three clumps are presented in Figure [10](#fig:figG28LGLIC). The local gravity orientation maps show similar radial patterns toward local emission peaks, which is quite reasonable because the emission centers contain more mass and have larger gravitational potential.

![](G28MM9_cont_mk_psc_bin3_ce_lic.pdf)

### Intensity gradient versus local gravity

The angle $\psi$ measures the angular difference between the position angles of the intensity gradient ($\theta_{\mathrm{IG}}$) and that of the local gravity ($\theta_{\mathrm{LG}}$). Figure [11](#fig:figG28psi) shows the $\psi$ maps for the three clumps. The average values of $\psi$ in MM1, MM4, and MM9 are 30$\ensuremath{^\circ}$, 22$\ensuremath{^\circ}$, and 28$\ensuremath{^\circ}$, respectively. The small average value of $\psi$ indicates that the intensity gradient tend to be aligned with the local gravity and that the gravity plays an important role in regulating the gas motion. On the other hand, there seems to be large $\psi$ values near some condensations where accretion or rotation are likely ongoing.

![](G28MM9_cont_mk_psc_bin3_ce_iso_ang_psi.pdf)

### Magnetic field versus intensity gradient

The angle $\delta$ measures the angular difference between the position angles of the intensity gradient ($\theta_{\mathrm{IG}}$) and that of the magnetic field ($\theta_{\mathrm{B}}$). Figure [12](#fig:figG28delta) shows the $\delta$ maps for MM1 and MM4. The average values of $\delta$ in MM1 and MM4 are 40$\ensuremath{^\circ}$ and 46$\ensuremath{^\circ}$, respectively. The intermediate average values of $\delta$ suggests that the magnetic field plays a moderate role in resisting the gas collapse.

### Magnetic field versus local gravity

The angle $\omega$ measures the angular difference between the position angles of the local gravity ($\theta_{\mathrm{LG}}$) and that of the magnetic field ($\theta_{\mathrm{B}}$). Figure [13](#fig:figG28omega) shows the $\omega$ maps for MM1 and MM4. The average values of $\omega$ in MM1 and MM4 are 34$\ensuremath{^\circ}$ and 36$\ensuremath{^\circ}$, respectively. In both MM1 and MM4, the magnetic field and the local gravity are apparently poorly aligned toward the brightest emission peaks, which might be a result of field tangling of complex small scale magnetic field along the line of sight or the perturbation from rotation and accretion. In MM1, the well-aligned magnetic field and local gravity in the northeastern region suggests that the magnetic field morphology is shaped by gravity in this region, while the magnetic field and the local gravity in the southwestern region are poorly aligned, suggesting that the magnetic field has kept its own dynamics.

If the hydrostatic gas pressure is neglectable, the local ratio between magnetic field force $F_{\mathrm{B}}$ and the gravity force $F_{\mathrm{G}}$ can be measured by the magnetic field-to-gravity force ratio (cite: 2012ApJ...747...79K) $$\begin{equation}
\Sigma_{\mathrm{B}} = \frac{\sin{\psi}}{\sin{(90\ensuremath{^\circ} - \delta)}} = \frac{F_{\mathrm{B}}}{\vert F_{\mathrm{G}} \vert}.
\end{equation}$$ Figure [14](#fig:figG28sigma) shows the $\Sigma_{\mathrm{B}}$ maps for MM1 and MM4. The median values of $\Sigma_{\mathrm{B}}$ in MM1 and MM4 are 0.47 and 0.27 respectively. The small values of $\Sigma_{\mathrm{B}}$ indicate that overall the magnetic field cannot solely balance the gravitational force.

# Discussion

## Uncertainty of the DCF method for super-Alfvénic cases

The accuracy of the DCF method has been under investigation in the literature. The reliability of the DCF method can be tested with with numerical simulations (cite: 2001ApJ...546..980O; 2001ApJ...559.1005P; 2001ApJ...561..800H; 2008ApJ...679..537F). Specifically, (cite: 2001ApJ...561..800H) and (cite: 2008ApJ...679..537F) investigated the effect of large angular dispersion and the effect of energy equipartition between the turbulent magnetic energy and the turbulent kinetic energy. Their results showed that the DCF method could overestimate the magnetic field strength for super-Alfvénic models.

The equipartition between the turbulent magnetic energy and the turbulent kinetic energy is a basic assumption of the DCF method. However, since the perturbation on the magnetic field cannot follow the strong kinetic motions for super-Alfvénic cases, the energy equipartition would be broken and the magnetic field strength would be overestimated (cite: 2001ApJ...561..800H; 2008ApJ...679..537F).

Another basic assumption of the DCF method is that the dispersion of polarization position angles corresponds to the ratio between the turbulent and ordered components of the magnetic field. For weak fields with Alfvén Mach number $>$1, the magnetic field lines can be easily distorted and the angular dispersion can approach that expected for a random field. As a consequence, the measured angular dispersion cannot reflect the true extent of the perturbed magnetic field and the magnetic field strength would be overestimated (cite: 2001ApJ...561..800H; 2008ApJ...679..537F).

The magnetic field strength of MM1-Core1 and MM4-Core4 is derived from the ADF method (see Section [3.5](#section:DCF)). The ADF method improves the original DCF method by taking into account the signal-integration effect and the large-scale field. However, the ADF method does not correct for the aforementioned effects of energy equipartition and large angular dispersion. Since the two cores are in super-Alfvénic states (see Section [3.5](#section:DCF)), it is possible that the ADF method has overestimated the magnetic field strength in the two cores.

## Dynamical state

The star formation process are governed by the complex interplay of self-gravity and competing processes (e.g., turbulence, thermal pressure, magnetic fields, stellar feedback, and rotation). For decades, the virial theorem has been used to study whether star-forming regions are stable against gravitational collapse. We briefly review the concept of the virial theorem and point out possible mistakes in some previous virial studies in Appendix [6](#virial). Here we calculate the relevant parameters in MM1-Core1 and MM4-Core4, and discuss the implication on massive star formation.

### Dynamic states in MM1-Core1 and MM4-Core4

We computed the virial masses and virial parameters for the two massive dense cores MM1-Core1 and MM4-Core4. The thermal velocity dispersion (1D sound speed, $\sigma_{\mathrm{th}}$) is derived by $$\begin{equation}
\sigma_{\mathrm{th}} = \sqrt{\frac{k_\mathrm{B} T}{\mu_\mathrm{p} m_\mathrm{H}}},
\end{equation}$$ where $\mu_\mathrm{p} = 2.33$ is the conventional mean molecular weight per free particle. The 3D sound speed is estimated as $\sigma_{\mathrm{th,3D}} = \sqrt{3}\sigma_{\mathrm{th}}$. We adopted radial density profiles $\rho \propto r^{-a}$ (cite: 2009ApJ...696..268Z) for the two cores. The kinetic virial mass is derived by $$\begin{equation}
M_{\mathrm{k}} = \frac{3(5-2a)\sigma_{tot}^2R}{(3-a)G},
\end{equation}$$ where $\sigma_{\mathrm{tot}} = \sqrt{\sigma_{\mathrm{th}}^2 + \sigma_{\mathrm{turb}}^2}$ is the total 1D gas velocity dispersion, $R =$ FWHM$_{\mathrm{mean}}$ is the radius of the core, and $G$ is the gravitational constant. Similarly, the thermal virial mass $M_{\mathrm{th}}$ and the turbulent virial mass $M_{\mathrm{turb}}$ can be derived by replacing $\sigma_{tot}$ with $\sigma_{th}$ or $\sigma_{turb}$, respectively. The ordered magnetic virial mass is given by $$\begin{equation}
\label{eq:MB}
M_{\mathrm{B}} = \frac{\pi R^2 B}{\sqrt{\frac{3(3-a)}{2(5-2a)}\mu_0\pi G}},
\end{equation}$$ in SI units or CGS units. The total virial mass accounting for both the ordered magnetic field and the kinetic motions is given by $$\begin{equation}
\label{eq:MkB}
M_{\mathrm{k+B}} = \sqrt{M^2_{\mathrm{B}} + (\frac{M_{\mathrm{k}}}{2})^2} + \frac{M_{\mathrm{k}}}{2}.
\end{equation}$$ The corresponding total virial parameter is $$\begin{equation}
\label{eq:alphakB}
\alpha_{k+B} = \frac{M_{\mathrm{k+B}}}{M}.
\end{equation}$$ As indicated in Table [4](#tab:ADF), the turbulent magnetic energy is comparable to the ordered magnetic energy. If we take into account the turbulent magnetic energy in the virial analysis, the modified magnetic virial mass $M_{\mathrm{B}}^{\mathrm{mod}}$, total virial mass $M_{\mathrm{k+B}}^{\mathrm{mod}}$, and total virial parameter $\alpha_{\mathrm{k+B}}^{\mathrm{mod}}$ could be derived from Equations [\[eq:MB\]](#eq:MB), [\[eq:MkB\]](#eq:MkB), and [\[eq:alphakB\]](#eq:alphakB) by replacing $B$ with $B(1+B^2_{\mathrm{t}}/B^2_{0})^{\frac{1}{2}}$.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | $\sigma_{\mathrm{th,3D}}$ | $\sigma_{\mathrm{turb,3D}}$ | $V_{\mathrm{A,3D}}$ | $M$ | $M_{\mathrm{th}}$ | $M_{\mathrm{turb}}$ | $M_{\mathrm{B}}$ | $M_{\mathrm{B}}^{\mathrm{mod}}$ | $M_{\mathrm{k+B}}$ | $M_{\mathrm{k+B}}^{\mathrm{mod}}$ | $\alpha_{\mathrm{k+B}}$ | $\alpha_{\mathrm{k+B}}^{\mathrm{mod}}$ |  |
|  | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | $M_{\odot}$ | $M_{\odot}$ | ($M_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$) |  |  |  |
| MM1-Core1 | 0.33 | 2.42 | 2.2 | 212.4 | 1.9 | 102.8 | 61.1 | 95.5 | 132.8 | 161.2 | 0.63 | 0.76 |  |
| MM4-Core4 | 0.24 | 0.80 | 0.75 | 42.6 | 0.58 | 6.6 | 7.3 | 11.4 | 11.8 | 15.6 | 0.28 | 0.37 |  |

: Physical parameters relevant to the virial analysis

Table [5](#tab:virial) lists the calculated parameters of the two cores. The nonthermal kinetic energy, thermal kinetic energy, and ordered magnetic energy can be compared by the square of the 3D turbulent velocity dispersion ($\sigma_{\mathrm{turb,3D}}$), 3D thermal velocity dispersion ($\sigma_{\mathrm{turb,3D}}$), and 3D Alfvén velocity ($V_{\mathrm{A,3D}}$). Both cores have $(\sigma_{\mathrm{turb,3D}})^2 \gg (\sigma_{\mathrm{th,3D}})^2$ (super-sonic) and $(V_{\mathrm{A,3D}})^2 \gg (\sigma_{\mathrm{th,3D}})^2$, which means the thermal energy only plays a neglectable role in the energy balance. The two cores also have $(\sigma_{\mathrm{turb,3D}})^2 > (V_{\mathrm{A,3D}})^2$, suggesting that the turbulent energy exceeds the ordered magnetic energy. Another way to assess the role of the three forces is to compare the maximum mass that can be supported by each force. The mass ratios show similar trends to the energy ratios in the two cores, except that the ordered magnetic virial mass is larger than the turbulent virial mass in MM4-Core4, which is in contrast to the energy ratio in this core ($E_{\mathrm{turb}} > E_{\mathrm{B}}$).

The modified total virial parameters $\alpha_{k+B}^{\mathrm{mod}}$ in MM1-Core1 and MM4-Core4 are found to be less than 1 (i.e., sub-virial). As shown in many previous studies, the main uncertainty comes from the mass estimation. If the mass is overestimated by a factor of 2 (i.e., the magnetic field strength overestimated by a factor of $\sqrt{2}$, if we ignore other sources of uncertainties), the $\alpha_{k+B}^{\mathrm{mod}}$ of MM1-Core1 and MM4-Core4 would be 1.3 and 0.58, respectively. Since the $\alpha_{k+B}^{\mathrm{mod}}$ in MM4-Core4 is much less than 1, it is very unlikely that MM4-Core4 is in virial equilibrium even with consideration of the large uncertainty of the analysis. However, we cannot rule out the possibility that MM1-Core1 is in virial equilibrium. More accurate estimations of the dust opacity might be required to reduce the uncertainty of the estimated virial parameter of MM1-Core1. Due to the limited angular resolution of our polarization observations and the lack of observations of appropriate turbulence tracers, we refrain from discussing the virial parameters at condensation scale.

### Non-equilibrium massive star formation

Previous observations show that a significant amount of massive star forming clumps and cores are in sub-virial states (cite: 2011A&A...530A.118P; 2013ApJ...779..185K; 2013ApJ...779...96T; 2015ApJ...804...37L; 2015ApJ...804..141Z; 2016ApJ...833..209O; 2017ApJ...841...97S; 2018ApJ...855....9L). However, there are no direct measurements of the magnetic field strength in their analyses, while the magnetic field could provide significant support to regulate the high-mass star formation (cite: 2014A&A...567A.116F; 2015ApJ...799...74P).

Our observations and calculations offer direct evidence of the role of magnetic fields in the dynamical state of two massive dense cores. As discussed in Section [4.2.1](#sec:virial_g28), MM4-Core4 is in a sub-virial state and MM1-Core1 is likely in a sub-virial state. The sub-virial state indicates that massive dense cores could undergo dynamical collapse in non-equilibrium in the early stage of star formation, which is in agreement with the competitive accretion model. Considering that MM1-Core1 is in a later evolution stage than MM4-Core4 (cite: 2009ApJ...696..268Z), the higher virial parameter of MM1-Core1 might suggest enhanced supports from the gas motion and the magnetic field as cores evolve.

## Comparing outflow axis with magnetic field orientation in condensation

The importance of magnetic fields in star formation can be studied by comparing the orientations of molecular outflows and ambient magnetic fields. Results from MHD simulations (cite: 2017ApJ...834..201L) suggest that strong ambient magnetic fields tend to align the axis of protostellar outflows because of magnetic braking (cite: 2003ApJ...599..363A), while the outflow-field orientation in the weak-field case is more random.

Observationally, a compilation of all of the outflow-versus-magnetic-field angles derivable to date in low-mass protostellar cores shows that overall the magnetic fields in low-mass dense cores are randomly aligned with outflows (cite: 2019FrASS...6....3H). (cite: 2018A&A...616A.139G) found a bimodal distribution of the angles between the envelope-scale magnetic field orientation and outflow axis in low-mass class 0 objects, suggesting that the magnetic field could play an important role in regulating the direction of outflows in the early stage of low-mass star formation.

In the case of massive star formation region, an SMA survey toward high-mass clumps found no strong correlation between the outflow axis and the magnetic field orientation in evolved dense cores with a total of 21 outflow samples (cite: 2014ApJ...792..116Z). Since molecular outflows are believed to be driven by MHD winds originated in or near the circumstellar disk (cite: 2000prpl.conf..789S; 2006MNRAS.365.1131P), the observed misalignment between the magnetic field orientation and the outflow axis indicates a less dynamically important role of magnetic fields from the core scale down to the disk scale.

With ALMA CO (2-1) and SiO (5-4) observations, (cite: 2019ApJ...874..104K) has determined the plane-of-sky position angle of the outflows ($\theta_{\mathrm{outflow}}$) in IRDC G28.34 (except those in MM1). Our polarization observations have resolved the magnetic field structure down to scales of $\sim$0.02 pc, which allows us to compare the outflow axis with the magnetic field orientation at condensation scales. Since MM1 is in a later stage of star formation and the position angle of the outflows in MM1 is not determined due to the complexity of the CO emission, we limit the comparison in MM4 and MM9.

The magnetic field orientation in each condensation ($\theta_{\mathrm{B}}$) in MM4 and MM9 is measured within one ALMA synthesized beam. There are 15 outflows in MM4 and MM9, among which 12 of them are associated with polarization detections in the condensation (see Figure [15](#fig:figG28out_B)). Figure [16](#fig:figG28angout_B) shows the angular difference between the outflow axis and the magnetic field orientation in the condensations where outflows originate for the 12 outflow samples in MM4 and MM9. The angular difference between the outflow axis and the field orientation appears to be in an approximate bimodal distribution, where the outflow axis tends to be either parallel or perpendicular to the orientation of magnetic fields. In half of the objects, the magnetic field is aligned within 10$\ensuremath{^\circ}$ of the outflow axis, suggesting that magnetic fields could be dynamically important from the condensation scale to the disk scale in the early stage of high-mass star formation. However, the observed magnetic field and outflow position angles are projected on the plane of sky. Observations toward larger samples of magnetic fields in IRDCs are essential to help us to rule out the possibility that the observed distribution is due to the projection effect.

![](./angalmag28.pdf)

## Fragmentation and clustered star formation in MM1

The two competing massive star formation models have different predictions on the fragmentaion of molecular clouds. The competitive accretion model proposes that the initial fragments in molecular clouds should be in thermal Jeans mass. The fragments and protostars therein near the gravitational center can thus accrete at a higher rate and form massive stars. Alternatively, the turbulent core accretion model suggests massive stars are formed via the monolithic collapse of a massive core that is supported by turbulent pressure rather than thermal pressure.

![](./G28MM1_cont_mk_psc_ce_separ_mst.pdf)

Our observations may help to distinguish between the two models. To quantify the separation of condensations in MM1, we applied the minimum spanning tree (hereafter MST) technique on these condensations using the python package MiSTree (cite: 2019JOSS....4.1721N). The MST method connects the condensations with straight lines and minimizes the sum of the line length. Figure [17](#fig:figG28MM1separ) show the MST for MM1. The separation of condensations in MM1 ranges from 0.025 pc to 0.16 pc.

Since the maximum recoverable scale of our ALMA observations is $\sim$7$\ensuremath{''}$ for MM1, we focus on interpreting the fragmentation in the core MM1-Core1 (including Condensations 1, 2, 3, 4, 5, and 6) that has a size of $\sim$6$\ensuremath{''}$. The separation of condensations in MM1-Core1 ranges from 0.025 pc to 0.058 pc and the average separation ($L_{av,MST}$) of these condensations is calculated to be 0.044 pc. As the measured separations are projected on the plane-of-sky, we multiplied the observed separation by a factor of $\pi /2$ to correct for the statistical projection effect (cite: 2019ApJ...886..102S) and the corrected average separation ($L_{av,MST,cor}$) is estimated to be 0.069 pc. The mass of the condensations in MM1-Core1 ranges from 3.7 to 35.5 M$_{\odot}$ (see Table [3](#tab:dendro)) and the average mass ($M_{av}$) of these condensations is calculated to be 14.3 M$_{\odot}$.

With a temperature of 30 K and a density of 3.2 $\times$ 10$^6$ cm$^{-3}$, the thermal Jeans length $$\begin{equation}
\label{equation:jeanslength}
\lambda_{\mathrm{J,th}} = \sigma_{\mathrm{th,3D}}\sqrt{\frac{\pi}{G\mu_{\mathrm{H_2}} m_{\mathrm{H}} n_{\mathrm{H_2}}}}
\end{equation}$$ and the thermal Jeans mass $$\begin{equation}
\label{equation:jeansmass}
M_{\mathrm{J,th}} = \frac{4}{3}\pi \mu_{\mathrm{H_2}} m_{\mathrm{H}} n_{\mathrm{H_2}} (\frac{\lambda_{\mathrm{J,th}}}{2})^3
\end{equation}$$ of MM1-Core1 are estimated to be 0.019 pc and 0.76 M$_{\odot}$, respectively. The $M_{av}$ is about 19 times larger than the $M_{\mathrm{J,th}}$ and the $L_{av,MST,cor}$ is about 3 times larger than the $\lambda_{\mathrm{J,th}}$. Considering that the resolution of our observations ($\sim$0.02 pc) is insufficient to resolve the foreshortened thermal Jeans length (2$/\pi$ times $\lambda_{\mathrm{J,th}}$) of 0.012 pc, we can not rule out the possibility that the detected condensations would further fragment into smaller structures with separations $\sim$ $\lambda_{\mathrm{J,th}}$. However, even if each condensation in MM1-Core1 further fragments into several smaller structures, the average mass of the fragments is unlikely to be close to the $M_{\mathrm{J,th}}$ since $M_{av}$ is much larger than $M_{\mathrm{J,th}}$.

Replacing the thermal velocity dispersion with the turbulent velocity dispersion in Equations [\[equation:jeanslength\]](#equation:jeanslength) and [\[equation:jeansmass\]](#equation:jeansmass), the turbulent Jeans length and the turbulent Jeans mass in MM1-Core1 are estimated to be 0.14 pc and 309 M$_{\odot}$, respectively, which are much larger than the $L_{av,MST,cor}$ and the $M_{av}$.

Thus, we conclude that the fragmentation in MM1-Core1 cannot be solely explained by the thermal Jeans fragmentation nor the turbulent Jeans fragmentation, which are inconsistent with either the competitive accretion model or the turbulent core accretion model. These discrepancies indicate that the physical condition in MM1-Core1 might have deviated from the initial condition of the core that controls the fragmentation process. On the other hand, we find that the mass of the condensations near the core center is more massive than that of the condensations in the outer region (see Table [3](#tab:dendro)). Thus, we expect MM1 to form a cluster of stars with several massive stars near the center and a population of low-mass stars in the outer region. This picture seems to agree with the competitive accretion model.

# Summary

With ALMA 1.3 mm dust polarization observations, we have presented a study of the magnetic field of three massive clumps in the IRDC G28.34. The main conclusions are as follows:

1.  Polarized dust emission are detected in all the three clumps. The magnetic field morphology varies in different regions. Trends of decreasing polarization percentage with increasing intensity are detected in MM1 and MM4. The $P$-$I$ relation in MM1 is shallower than that in MM4, which might be explained by the improved grain alignment efficiency due to enhanced internal radiation in more evolved regions.

2.  From the dust polarization maps, we measured the plane-of-sky magnetic field strength in two massive dense cores, MM1-Core1 ($M = 212.4 M_{\odot}$) and MM4-Core4 ($M = 43.0 M_{\odot}$), with the auto-correlation function method. The $B_{\mathrm{pos}}$ is found to be $\sim$1.6 mG and $\sim$0.32 mG in MM1-Core1 and MM4-Core4, respectively.

3.  We studied the dynamical state in MM1-Core1 and MM4-Core4 by calculating the virial parameter that includes both the turbulence and the magnetic field. The results of the virial analysis suggest that MM4-Core4 is in a sub-virial state and MM1-Core1 is likely in a sub-virial state, which signifies a dynamical massive star formation in non-equilibrium.

4.  We compared the orientations of the magnetic field, local gravity, and intensity gradient with the polarization-intensity gradient-local gravity method. We found that the intensity gradient closely follows the local gravity in the three clumps. The magnetic field is found to be randomly aligned with the intensity gradient, but better aligned with the local gravity in MM1 and MM4. The average magnetic field to gravity force ratio are found to be smaller than 1 in MM1 and MM4, which suggests that the magnetic force cannot solely prevent the gravitational collapse.

5.  With a total of 12 outflow samples in MM4 and MM9, the angle between orientations of the magnetic field at condensation scales and the outflow axis shows an approximate bimodal distribution with half of the outflows aligned within 10$\ensuremath{^\circ}$ of the magnetic field, which suggests that magnetic fields could play an important role from the condensation scale to the disk scale in the early stage of massive star formation.

6.  We identified the dense condensations in MM1 with the dendrogram method and characterized the separation of these condensations using the minimum spanning tree technique. The mass of the condensations and the average minimum separation between condensations in MM1-Core1 are found to be larger than the values predicted by thermal Jeans fragmentation and smaller than the values predicted by turbulent Jeans fragmentation. Thus we propose that the physical condition in MM1-Core1 might has deviated from the initial condition that controls the fragmentation.

# Acknowledgments

We thank Dr. Diego Falceta-Gonçalves, Dr. J. Michail, and Dr. Fabio Santos for sharing their codes for plotting the LIC maps and Dr. Shuo Kong for sharing the catalog of the outflows in G28.34. We are indebt to the anonymous referee whose constructive comments improved the presentation and clarity of the paper. K.Q. and J.L. are supported by National Key R&D Program of China No. 2017YFA0402600. K.Q. and J.L. acknowledge the support from National Natural Science Foundation of China (NSFC) through grants U1731237, 11590781, and 11629302. J.L. acknowledges the support from the program of China Scholarship Council (No. 201806190134) and from the Smithsonian Astrophysical Observatory pre-doctoral fellowship. JMG is supported by the Spanish grant AYA2017-84390-C2-R (AEI/FEDER, UE). ZYL is supported in part by NASA 80NSSC18K1095 and NSF AST-1716259 and 1815784. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00248.S and ADS/JAO.ALMA#2017.1.00793.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This research made use of astrodendro, a Python package to compute dendrograms of Astronomical data (http://www.dendrograms.org/), APLpy, an open-source plotting package for Python (cite: 2012ascl.soft08017R), Astropy, a community-developed core Python package for Astronomy (cite: 2013A&A...558A..33A), and Matplotlib, a Python 2D plotting library for Python (cite: 2007CSE.....9...90H). Atacama Large Millimeter/Submillimeter Array (ALMA).

# Software

APLpy (cite: 2012ascl.soft08017R), Astropy (cite: 2013A&A...558A..33A), Matplotlib (cite: 2007CSE.....9...90H).

(ref: 2015ARA&A..53..501A) Andersson, B.-G., Lazarian, A., & Vaillancourt, J. E. 2015, ARA&A, 53, 501 (ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33 (ref: 2003ApJ...599..363A) Allen, A., Li, Z.-Y., & Shu, F. H. 2003, ApJ, 599, 363 (ref: 1991ApJ...381..250B) Beckwith, S. V. W., & Sargent, A. I. 1991, ApJ, 381, 250 (ref: 1992ApJ...395..140B) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140 (ref: 2018A&A...614A..64B) Beuther, H., Soler, J. D., Vlemmings, W., et al. 2018, A&A, 614, A64 (ref: 2007A&A...466.1065B) Beuther, H., Leurini, S., Schilke, P., et al. 2007, A&A, 466, 1065 (ref: 1997MNRAS.285..201B) Bonnell, I. A., Bate, M. R., Clarke, C. J., et al. 1997, MNRAS, 285, 201 (ref: 1956MNRAS.116..351B) Bonnor, W. B. 1956, MNRAS, 116, 351 (ref: 2009ApJ...696..484B) Butler, M. J., & Tan, J. C. 2009, ApJ, 696, 484 (ref: 1993_LIC_C) Cabral, B., & Leedom, L. C. 1993, in Special Interest Group on GRAPHics and Interactive Techniques Proceedings, 263 (ref: 2019ApJS..241....1C) Cao, Y., Qiu, K., Zhang, Q., et al. 2019, ApJS, 241, 1 (ref: 1998ApJ...508..721C) Carey, S. J., Clark, F. O., Egan, M. P., et al. 1998, ApJ, 508, 721 (ref: 1953ApJ...118..113C) Chandrasekhar, S., & Fermi, E. 1953, ApJ, 118, 113 (ref: 2010ApJ...713L..50C) Chen, H.-R., Liu, S.-Y., Su, Y.-N., et al. 2010, ApJL, 713, L50 (ref: 2007ApJ...654L..87C) Chen, H.-R., Su, Y.-N., Liu, S.-Y., et al. 2007, ApJL, 654, L87 (ref: 2018ApJ...853..160C) Cheng, Y., Tan, J. C., Liu, M., et al. 2018, ApJ, 853, 160 (ref: 2004ApJ...600..279C) Crutcher, R. M., Nutter, D. J., Ward-Thompson, D., et al. 2004, ApJ, 600, 279 (ref: 1951PhRv...81..890D) Davis, L. 1951, Physical Review, 81, 890 (ref: 1957ZA.....42..263E) Ebert, R. 1957, ZAp, 42, 263 (ref: 2008ApJ...679..537F) Falceta-Gonçalves, D., Lazarian, A., & Kowal, G. 2008, ApJ, 679, 537 (ref: 2019ApJ...883..202F) Feng, S., Caselli, P., Wang, K., et al. 2019, ApJ, 883, 202 (ref: 2016ApJ...828..100F) Feng, S., Beuther, H., Zhang, Q., et al. 2016, ApJ, 828, 100 (ref: 2016A&A...592A..21F) Feng, S., Beuther, H., Zhang, Q., et al. 2016, A&A, 592, A21 (ref: 2014A&A...567A.116F) Frau, P., Girart, J. M., Zhang, Q., et al. 2014, A&A, 567, A116 (ref: 2018A&A...616A.139G) Galametz, M., Maury, A., Girart, J. M., et al. 2018, A&A, 616, A139 (ref: 2013ApJ...772...69G) Girart, J. M., Frau, P., Zhang, Q., et al. 2013, ApJ, 772, 69 (ref: 2009Sci...324.1408G) Girart, J. M., Beltrán, M. T., Zhang, Q., et al. 2009, Science, 324, 1408

(ref: 2001ApJ...561..800H) Heitsch, F., Zweibel, E. G., Mac Low, M.-M., et al. 2001, ApJ, 561, 800 (ref: 2008ApJ...684..395H) Hennebelle, P., & Chabrier, G. 2008, ApJ, 684, 395 (ref: 1995P&SS...43.1333H) Henning, T., Michel, B., & Stognienko, R. 1995, , 43, 1333 (ref: 2009ApJ...696..567H) Hildebrand, R. H., Kirby, L., Dotson, J. L., Houde, M., & Vaillancourt, J. E. 2009, ApJ, 696, 567 (ref: 1983QJRAS..24..267H) Hildebrand, R. H. 1983, QJRAS, 24, 267 (ref: 1983ARA&A..21..239H) Ho, P. T. P., & Townes, C. H. 1983, ARA&A, 21, 239 (ref: 2016ApJ...820...38H) Houde, M., Hull, C. L. H., Plambeck, R. L., et al. 2016, ApJ, 820, 38 (ref: 2009ApJ...706.1504H) Houde, M., Vaillancourt, J. E., Hildebrand, R. H., Chitsazzadeh, S., & Kirby, L. 2009, ApJ, 706, 1504 (ref: 2019FrASS...6....3H) Hull, C. L. H., & Zhang, Q. 2019, Frontiers in Astronomy and Space Sciences, 6, 3 (ref: 2007CSE.....9...90H) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90 (ref: 2018A&A...620A..26J) Juvela, M., Guillet, V., Liu, T., et al. 2018, A&A, 620, A26 (ref: 2015ApJ...809...78K) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78 (ref: 2013ApJ...779..185K) Kauffmann, J., Pillai, T., & Goldsmith, P. F. 2013, ApJ, 779, 185 (ref: 2013MNRAS.432.1424K) Kirk, J. M., Ward-Thompson, D., Palmeirim, P., et al. 2013, MNRAS, 432, 1424 (ref: 2012ApJ...747...79K) Koch, P. M., Tang, Y.-W., & Ho, P. T. P. 2012, ApJ, 747, 79 (ref: 2019ApJ...874..104K) Kong, S., Arce, H. G., Maureira, M. J., et al. 2019, ApJ, 874, 104 (ref: 2019ApJ...873...31K) Kong, S. 2019, ApJ, 873, 31 (ref: 2018ApJ...867...94K) Kong, S., Tan, J. C., Caselli, P., et al. 2018, ApJ, 867, 94 (ref: 2018ApJ...855L..25K) Kong, S., Tan, J. C., Arce, H. G., et al. 2018, ApJL, 855, L25 (ref: 2014PhR...539...49K) Krumholz, M. R. 2014, Phys. Rep., 539, 49 (ref: 2005Natur.438..332K) Krumholz, M. R., McKee, C. F., & Klein, R. I. 2005, Nature, 438, 332 (ref: 2018ApJ...859....4K) Kwon, J., Doi, Y., Tamura, M., et al. 2018, ApJ, 859, 4 (ref: 2007JQSRT.106..225L) Lazarian, A. 2007, JQSRT, 106, 225 (ref: 2007MNRAS.378..910L) Lazarian, A., & Hoang, T. 2007, MNRAS, 378, 910

(ref: 2017ApJ...834..201L) Lee, J. W. Y., Hull, C. L. H., & Offner, S. S. R. 2017, ApJ, 834, 201 (ref: 2017ApJ...840...22L) Lin, Y., Liu, H. B., Dale, J. E., et al. 2017, ApJ, 840, 22 (ref: 2019ApJ...877...43L) Liu, J., Qiu, K., Berry, D., et al. 2019, ApJ, 877, 43

(ref: 2018ApJ...862..105L) Liu, M., Tan, J. C., Cheng, Y., et al. 2018, ApJ, 862, 105 (ref: 2018ApJ...859..151L) Liu, T., Li, P. S., Juvela, M., et al. 2018, ApJ, 859, 151 (ref: 2015ApJ...804...37L) Liu, H. B., Galván-Madrid, R., Jiménez-Serra, I., et al. 2015, ApJ, 804, 37 (ref: 2018ApJ...855....9L) Lu, X., Zhang, Q., Liu, H. B., et al. 2018, ApJ, 855, 9

(ref: 2002Natur.416...59M) McKee, C. F., & Tan, J. C. 2002, Nature, 416, 59 (ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., et al. 2007, Astronomical Data Analysis Software and Systems XVI, 127 (ref: 2007A&A...476.1243M) Motte, F., Bontemps, S., Schilke, P., et al. 2007, A&A, 476, 1243 (ref: 2001A&A...365..440M) Motte, F., & André, P. 2001, A&A, 365, 440 (ref: 1993A&A...274..968N) Naghizadeh-Khouei, J., & Clarke, D. 1993, A&A, 274, 968 (ref: 1978PASJ...30..671N) Nakano, T., & Nakamura, T. 1978, PASJ, 30, 671 (ref: 2019JOSS....4.1721N) Naidoo, K. 2019, The Journal of Open Source Software, 4, 1721 (ref: 2016ApJ...833..209O) Ohashi, S., Sanhueza, P., Chen, H.-R. V., et al. 2016, ApJ, 833, 209 (ref: 2001ApJ...546..980O) Ostriker, E. C., Stone, J. M., & Gammie, C. F. 2001, ApJ, 546, 980 (ref: 2001ApJ...559.1005P) Padoan, P., Goodman, A., Draine, B. T., et al. 2001, ApJ, 559, 1005 (ref: 2019FrASS...6...15P) Pattle, K., & Fissel, L. 2019, Frontiers in Astronomy and Space Sciences, 6, 15 (ref: 2019ApJ...880...27P) Pattle, K., Lai, S.-P., Hasegawa, T., et al. 2019, ApJ, 880, 27 (ref: 2017ApJ...846..122P) Pattle, K., Ward-Thompson, D., Berry, D., et al. 2017, ApJ, 846, 122 (ref: 2015MNRAS.450.1094P) Pattle, K., Ward-Thompson, D., Kirk, J. M., et al. 2015, MNRAS, 450, 1094 (ref: 2015ApJ...799...74P) Pillai, T., Kauffmann, J., Tan, J. C., et al. 2015, ApJ, 799, 74 (ref: 2011A&A...530A.118P) Pillai, T., Kauffmann, J., Wyrowski, F., et al. 2011, A&A, 530, A118 (ref: 2006A&A...450..569P) Pillai, T., Wyrowski, F., Carey, S. J., et al. 2006, A&A, 450, 569 (ref: 1996A&A...315L.165P) Perault, M., Omont, A., Simon, G., et al. 1996, A&A, 315, L165 (ref: 2006MNRAS.365.1131P) Pudritz, R. E., Rogers, C. S., & Ouyed, R. 2006, MNRAS, 365, 1131 (ref: 2014ApJ...794L..18Q) Qiu, K., Zhang, Q., Menten, K. M., et al. 2014, ApJL, 794, L18 (ref: 2006ApJ...641..389R) Rathborne, J. M., Jackson, J. M., & Simon, R. 2006, ApJ, 641, 389 (ref: 2012A&A...547A..49R) Ragan, S., Henning, T., Krause, O., et al. 2012, A&A, 547, A49 (ref: 1998ApJ...502L..75R) Rao, R., Crutcher, R. M., Plambeck, R. L., et al. 1998, ApJL, 502, L75 (ref: 2012ascl.soft08017R) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library, ascl:1208.017 (ref: 2008ApJ...679.1338R) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., et al. 2008, ApJ, 679, 1338 (ref: 2014A&A...562A.138R) Roy, A., André, P., Palmeirim, P., et al. 2014, A&A, 562, A138 (ref: 2019ApJ...886..102S) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102 (ref: 2017ApJ...841...97S) Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ, 841, 97 (ref: 2000prpl.conf..789S) Shu, F. H., Najita, J. R., Shang, H., & Li, Z.-Y. 2000, in Protostars and Planets IV, ed. V. Manning, A. P. Boss, & S. S. Russell (Tucson, AZ: Univ. Arizona Press), 789 (ref: 1987ARA&A..25...23S) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23 (ref: 2006ApJ...653.1325S) Simon, R., Rathborne, J. M., Shah, R. Y., et al. 2006, ApJ, 653, 1325 (ref: 2019ApJ...883...95S) Soam, A., Liu, T., Andersson, B.-G., et al. 2019, ApJ, 883, 95 (ref: 2018ApJ...861...65S) Soam, A., Pattle, K., Ward-Thompson, D., et al. 2018, ApJ, 861, 65 (ref: 2016ApJ...821L...3T) Tan, J. C., Kong, S., Zhang, Y., et al. 2016, ApJL, 821, L3 (ref: 2014prpl.conf..149T) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, Protostars and Planets VI, 149 (ref: 2013ApJ...779...96T) Tan, J. C., Kong, S., Butler, M. J., et al. 2013, ApJ, 779, 96 (ref: 2019ApJ...878...10T) Tang, Y.-W., Koch, P. M., Peretto, N., et al. 2019, ApJ, 878, 10 (ref: 2009ApJ...695.1399T) Tang, Y.-W., Ho, P. T. P., Girart, J. M., et al. 2009, ApJ, 695, 1399 (ref: 2017ApJ...839...56T) Tazaki, R., Lazarian, A., & Nomura, H. 2017, ApJ, 839, 56 (ref: 1993ApJ...414..759T) Terebey, S., Chandler, C. J., & Andre, P. 1993, ApJ, 414, 759 (ref: 2006PASP..118.1340V) Vaillancourt, J. E. 2006, PASP, 118, 1340 (ref: 2018RNAAS...2...52W) Wang, Ke . 2018, Research Notes of the American Astronomical Society, 2, 52 (ref: 2012ApJ...745L..30W) Wang, K., Zhang, Q., Wu, Y., et al. 2012, ApJL, 745, L30 (ref: 2011ApJ...735...64W) Wang, K., Zhang, Q., Wu, Y., et al. 2011, ApJ, 735, 64 (ref: 2008ApJ...672L..33W) Wang, Y., Zhang, Q., Pillai, T., et al. 2008, ApJL, 672, L33 (ref: 2006ApJ...651L.125W) Wang, Y., Zhang, Q., Rathborne, J. M., et al. 2006, ApJL, 651, L125 (ref: 2017ApJ...842...66W) Ward-Thompson, D., Pattle, K., Bastien, P., et al. 2017, ApJ, 842, 66 (ref: 2016MNRAS.456.2794Y) Yang, H., Li, Z.-Y., Looney, L., et al. 2016, MNRAS, 456, 2794 (ref: 2015ApJ...804..141Z) Zhang, Q., Wang, K., Lu, X., et al. 2015, ApJ, 804, 141 (ref: 2014ApJ...792..116Z) Zhang, Q., Qiu, K., Girart, J. M., et al. 2014, ApJ, 792, 116 (ref: 2009ApJ...696..268Z) Zhang, Q., Wang, Y., Pillai, T., et al. 2009, ApJ, 696, 268

# Virial theorem

Ignoring the surface kinetic energy, the virial theorem is written as: $$\begin{equation}
\frac{1}{2}\frac{d^2 I}{dt^2} = 2E_{\mathrm{k}} + E_{\mathrm{B}} + E_{\mathrm{G}},
\end{equation}$$ where $I$ is the moment of inertia, $E_{\mathrm{k}}$ is the kinetic energy, $E_{\mathrm{B}}$ is the magnetic energy, and $E_{\mathrm{G}}$ is the gravitational energy. For a sphere with a radial density profile $\rho \propto r^{-a}$ (for a uniform density, $a = 0$), the gravitational energy is given by $$\begin{equation}
E_{\mathrm{G}} = - \frac{(3-a)}{(5-2a)} \frac{GM^2}{R},
\end{equation}$$ where $G$ is the gravitational constant, $M$ is the mass of the considered structure, and $R$ is the radius of the structure. The magnetic energy is given by $$\begin{equation}
E_{\mathrm{B}} = \frac{B^2 V}{2\mu_0},
\end{equation}$$ where $V = 4 \pi R^3/3$ is the volume of the structure. The kinetic energy is the sum of the thermal energy ($E_{\mathrm{th}}$) and the turbulent energy ($E_{\mathrm{turb}}$): $$\begin{equation}
E_{\mathrm{k}} = E_{\mathrm{th}} + E_{\mathrm{turb}} = \frac{3}{2} M\sigma_{tol}^2,
\end{equation}$$ where $\sigma_{\mathrm{tot}}$ is the total 1D gas velocity dispersion. The thermal energy and the turbulent energy can be derived by $$\begin{equation}
E_{\mathrm{th}} = \frac{3}{2} M\sigma_{\mathrm{th}}^2,
\end{equation}$$ and $$\begin{equation}
E_{\mathrm{turb}} = \frac{3}{2} M\sigma_{\mathrm{turb}}^2,
\end{equation}$$ respectively, where $\sigma_{\mathrm{th}}$ is the 1D thermal velocity dispersion and $\sigma_{\mathrm{turb}}$ is the 1D turbulent velocity dispersion.

For a non-magnetized ($E_{\mathrm{B}} = 0$) sphere, the structure is stable when $2E_{\mathrm{k}} + E_{\mathrm{G}} < 0$, which requires $M < M_{\mathrm{k}}$, where $$\begin{equation}
M_{\mathrm{k}} = \frac{3(5-2a)\sigma_{tot}^2R}{(3-a)G}
\end{equation}$$ is the kinetic virial mass. Similarly, we can define the thermal virial mass $M_{\mathrm{th}}$ and the turbulent virial mass $M_{\mathrm{turb}}$ by replacing $\sigma_{tot}$ with the corresponding velocity dispersion to account for the thermal component and the turbulent component of the virial mass separately. (cite: 1992ApJ...395..140B) introduced a kinetic virial parameter $$\begin{equation}
\alpha_{k} = \frac{2E_{\mathrm{k}}}{\vert E_{\mathrm{G}} \vert} = \frac{3(5-2a)\sigma_{tot}^2R}{(3-a)GM} = \frac{M_{\mathrm{k}}}{M}
\end{equation}$$ to represent the ratio of the kinetic energy and the gravitational energy. We note that $M < M_{\mathrm{k}}$ (kinetically super-virial) is equivalent to $\alpha_{k} > 1$. For comparison with $M_{\mathrm{k}}$, a Bonnor-Ebert sphere (cite: 1956MNRAS.116..351B; 1957ZA.....42..263E) in isothermal hydrostatic equilibrium is stable when $M < M_{\mathrm{BE}}$, where $M_{\mathrm{BE}}$ is the Bonnor-Ebert critical mass given by $$\begin{equation}
M_{\mathrm{BE}} = 2.43 \frac{\sigma_{tot}^2R}{G}.
\end{equation}$$ For a uniform sphere (a=0), $M < M_{\mathrm{BE}}$ is equivalent to $\alpha_{k} > 2.06$.

If the kinetic energy is neglectable ($E_{\mathrm{k}} = 0$), a stable sphere has $E_{\mathrm{B}} + E_{\mathrm{G}} < 0$, which implies $M < M_{\mathrm{B}}$, where $$\begin{equation}
M_{\mathrm{B}} = \frac{\pi R^2 B}{\sqrt{\frac{3(3-a)}{2(5-2a)}\mu_0\pi G}} 
\end{equation}$$ is the magnetic virial mass in SI units or CGS units. We noticed some previous studies (cite: 2008ApJ...684..395H; 2011A&A...530A.118P; 2016ApJ...833..209O; 2017ApJ...841...97S; 2019FrASS...6....3H) have written the magnetic virial mass of a uniform (a=0) sphere as $$\begin{equation}
M'_{\mathrm{B}} = \frac{5RV_{\mathrm{A,3D}}^2}{6G} = \frac{5RB^2}{6\mu_0 \rho G} = \frac{10\pi R^4B^2}{9\mu_0 GM},
\end{equation}$$ where $V_{\mathrm{A,3D}} = \frac{B}{\sqrt{\mu_0 \rho}}$ is the 3D Alfvén velocity in SI units or CGS units. The $M'_{\mathrm{B}}$ is derived by writing the magnetic energy as $$\begin{equation}
E'_{\mathrm{B}} = \frac{B^2 M}{2\mu_0 \rho}
\end{equation}$$ and solving the critical mass for $E'_{\mathrm{B}} + E_{\mathrm{G}} = \frac{B^2 M}{2\mu_0 \rho} - \frac{3}{5} \frac{GM^2}{R} < 0$. However, we point out that since $M$, $\rho$, and $R$ are not independent ($M = 4 \pi R^3 \rho/3$), the magnetic virial mass should be written as a function of $R$ or $\rho$, but not both $R$ and $\rho$. Thus $M'_{\mathrm{B}}$ does not accurately estimate the magnetic virial mass. For a magnetically supercritical ($M > M_{\mathrm{B}}$) structure, $M'_{\mathrm{B}} = \frac{10\pi R^4B^2}{9\mu_0 GM} < \frac{10\pi R^4B^2}{9\mu_0 GM_{\mathrm{B}}} = M_{\mathrm{B}}$ would underestimate the magnetic virial mass, and vice versa. For comparison with $M_{\mathrm{B}}$, the magnetic critical mass of an isothermal disk (cite: 1978PASJ...30..671N) has been derived to be $$\begin{equation}
M_{B,disk} = \frac{\pi R^2 B}{\sqrt{\mu_0 \pi G}}.
\end{equation}$$ (cite: 2004ApJ...600..279C) introduced a parameter $\lambda$ to state the mass-to-flux ratio in units of its critical value: $$\begin{equation}
\lambda = \frac{(M/\Phi)_{observed}}{(M/\Phi)_{critical}} = \frac{M}{M_{B,disk}},
\end{equation}$$ where $(M/\Phi)_{observed}$ is the observed mass-to-magnetic-flux ratio: $$\begin{equation}
(\frac{M}{\Phi})_{observed} = \frac{\mu_{\mathrm{H_2}} m_{\mathrm{H}}N(H_2)}{B},
\end{equation}$$ and $(M/\Phi)_{critical}$ is the critical mass-to-magnetic-flux ratio: $$\begin{equation}
(\frac{M}{\Phi})_{critical} = \frac{1}{\sqrt{\mu_0 \pi G}}.
\end{equation}$$ For magnetically subcritical structure with mass less than the magnetic critical mass, the magnetic field alone can prevent the structure from collapse.

Taking into account both the magnetic energy and the kinetic energy, a structure is stable when $2E_{\mathrm{k}} + E_{\mathrm{B}} + E_{\mathrm{G}} < 0$. The critical virial mass is calculated to be $$\begin{equation}
M_{\mathrm{k+B}} = \sqrt{M^2_{\mathrm{B}} + (\frac{M_{\mathrm{k}}}{2})^2} + \frac{M_{\mathrm{k}}}{2}.
\end{equation}$$ It should be noted that $M_{\mathrm{k}} + M_{\mathrm{B}}$ is systematically larger than $M_{\mathrm{k+B}}$ (cite: 1992ApJ...395..140B) and the largest ratio between $M_{\mathrm{k}} + M_{\mathrm{B}}$ and $M_{\mathrm{k+B}}$ is 1.25 when $M_{\mathrm{B}} = 0.67 M_{\mathrm{k}}$, Therefore some previous studies using $M_{\mathrm{B}} + M_{\mathrm{k}}$ to represent the total virial mass may have slightly overestimated the support from the magnetic field and gas motion. Following the definition of $\alpha_{k}$, we can define a total virial parameter $$\begin{equation}
\alpha_{k+B} = \frac{M_{\mathrm{k+B}}}{M}.
\end{equation}$$

[^1]: Following the nomenclature in (cite: 2009ApJ...696..268Z), we refer to a molecular clump as an entity of $\sim$ 1 pc, a dense core as an entity of $\sim$ 0.1 pc, and a condensation as an entity of $\sim$ 0.01 pc that forms one star or a group of stars.

[^2]: https://almascience.eso.org/observing/prior-cycle-observing-and-configuration-schedule

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "tclean imaging; debiased PI, P and position angle computed from Q,U,I",
  "failed_quote": "The debiased polarized intensity $PI$ and its uncertainty $\\sigma_{PI}$ are calculated as:"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "chi2 minimization",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "chi2 minimization",
  "failed_quote": "(no quote given)"
 }
]
```
