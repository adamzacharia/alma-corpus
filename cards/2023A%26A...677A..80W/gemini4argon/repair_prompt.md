# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...677A..80W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ALMA and VLBA views on the outflow associated with an O-type protostar in G26.50+0.28

Protostellar jets and outflows are essential ingredients of the star formation process. A better understanding of this phenomenon is important in its own right as well as for many fundamental aspects of star formation. Jets and outflows associated with O-type protostars are rarely studied with observations reaching the close vicinity of the protostars. In this work, we report high-resolution ALMA and VLBA observations to reveal a clear and consistent picture of an outflow associated with an O-type protostar candidate in the G26.50+0.28 region. These observations reveal, for the first time, a collimated jet located in the middle of the outflow cavity. The jet is found to be perpendicular to an elongated disk/toroid and its velocity gradient. The collimated jet appears to show a small amplitude ($\alpha$$\approx$0$\hbox{$\,.\!\!^{\circ}$}$06) counterclockwise precession, when looking along the blueshifted jet axis from the strongest continuum source MM1, with a precession length of 0.22 pc. The inclination of the jet is likely to be very low ($\approx$8$\hbox{$^{\circ}$}$), which makes it a promising target to study its transverse morphologies and kinematics. However, no clear evidence of jet rotation is found in the ALMA and VLBA observations. The three-dimensional velocities of the water maser spots appear to show the same absolute speed with respect to different opening angles, suggesting the jet winds may be launched in a relatively small region. This favors the X-wind model, that is, jets are launched in a small area near the inner disk edge.

# Introduction

Jets and outflows are natural outcomes in accreting astrophysical systems with rotation and magnetic fields (cite: 1982MNRAS.199..883B) and are ubiquitous in star-forming regions (cite: 2002A&A...383..892B; 2004A&A...426..503W; 2016ARA&A..54..491B). Generally, the narrow and highly collimated “jets” are believed to arise through magnetohydrodynamic (MHD) processes in the rotating star-disk system. The less collimated and more massive “outflows” are believed to create shells of ambient gas swept up by the bowshock of the jet and/or a surrounding wider-angle wind component (cite: 2007prpl.conf..245A).

Protostellar jets and outflows are essential elements of the star formation process. They are proposed to remove the angular momentum from the young star and its disk, to determine the final core-to-star efficiency and envelope dissipation, to shift the core mass function to the stellar initial mass function, to counteract the dissipation of turbulence in clouds, and to impact planet formation through disk irradiation/shielding and MHD effects (cite: 2014prpl.conf..451F; 2016ARA&A..54..491B).

Meanwhile, they also provide significant clues on the underlying star formation process, especially of deeply embedded and quickly evolving high-mass proto and young stellar objects, and provide a fossil record of the accretion history. Therefore, the study of jets and outflows is essential in its own right as well as for a better understanding of many fundamental aspects of high-mass star formation.

How jets are launched and collimated is still under debate and the details of the interactions between jets and outflows remain unclear. The long-standing X- or disk-wind problem, that jets are launched via magnetocentrifugal processes either from regions near the X-point (cite: 2000prpl.conf..789S) and/or from a wider area in the disk (cite: 2000prpl.conf..759K), is still with us. One of the main reasons has been the inadequate angular resolution of current facilities needed to zoom into the launching and collimation zone (cite: 2014prpl.conf..451F). High angular resolution observations reaching the close vicinity of the protostars or the base of the jet are expected to provide the most relevant information to deduce its launching and collimating processes. In particular, the origin of jets from more massive protostars has rarely been investigated so far (cite: 2014prpl.conf..451F; 2016ARA&A..54..491B). Outflows detected in high-mass ($\mathrel{\mathchoice   {\vcenter{\offinterlineskip\halign{\hfil
$\displaystyle##$\hfil\cr>\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\textstyle##$\hfil\cr
>\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptstyle##$\hfil\cr
>\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptscriptstyle##$\hfil\cr
>\cr\sim\cr}}}}$8M$_{\odot}$) star-forming regions tended to be less collimated than those observed in low-mass star-forming regions (cite: 2002A&A...383..892B; 2003ApJ...598L.115T; 2007prpl.conf..245A; 2016A&A...585A..71M), but there are also cases that show the contrary (cite: 2013ApJ...778...72F; 2020ApJ...905...25G; 2021MNRAS.507.4316B).

Aperture synthesis imaging with interferometers, providing (sub)arcsecond angular resolution images and data cubes, is revolutionizing outflow studies.

Episodic ejection (cite: 2017A&A...597A.119T; 2015Natur.527...70P), jet rotation (cite: 2017NatAs...1E.152L; 2020A&A...634L..12D; 2022A&A...668A..78D), and collimated radial winds (cite: 2021ApJ...914L...1C; 2022ApJ...927L..27L) have been detected in observations of nearby star formation regions.

Very long baseline interferometry (VLBI) techniques, achieving even higher resolutions in the milli-arcsecond range, are another powerful tool to zoom into the part of the jet close to the launching point.

Maser radiation is very sensitive to the excitation conditions and the geometry of the emitting regions, which makes it hard to derive the physical parameters from maser observations (cite: 2007prpl.conf..197C).

However, the three-dimensional (3D) velocities of the maser spots[^1] derived from multiple epoch VLBI observations, allow us to study the kinematics at the base of the jet. VLBI observations only address the kinematics of the tiny regions encompassed by the masers (cite: 1992ARA&A..30...75E). The selective kinematical information, albeit sparse, allows us to unambiguously interpret the kinematical distribution of the jet winds.

In practice, the interpretation of maser emission might be complicated and ambiguous, and sometimes the same maser species have been claimed to trace disks and outflows simultaneously. To achieve a comprehensive understanding of the jet properties, it is necessary to complement VLBI observations with high angular resolution imaging of thermally exited gas (cite: 2022A&A...659A..81B).

Located at a maser parallax distance of 6.3$^{+0.5}_{-0.4}$ kpc (cite: 2021ApJS..253....1X), G26.50+0.28 (also known as IRAS 18360-0537) has a far-Infrared luminosity of 1.2$\times$10$^5$ L$_{\odot}$ (Molinari et al. 1996). The continuum map obtained with the Submillimeter Array (SMA) at 1.3 mm reveals two unresolved condensations, MM1 and MM2, in the source, while SMA maps of the $^{13}$CO (2-1) and SiO (5-4) line emission show a northeast-southwest wide-angle bipolar outflow centered at MM1 (cite: 2012ApJ...756..170Q). Images of CH$_{3}$OH and CH$_{3}$CN emission reveal a “disk/toroid”-like rotational structure with the velocity gradient perpendicular to the outflow axis. Furthermore, CN spectra, also from the SMA, present typical inverse P-Cygni profiles that demonstrate infall motions of about 1.5$\times$10$^{-3}$ M$_{\rm \odot}$ yr$^{-1}$ (Qiu et al. 2012). Given its luminosity, high accretion rate, and massive gas reservoir in the envelope, (cite: 2012ApJ...756..170Q) suggested that MM1 would eventually form an O-type star. In its environment, G26.50+0.28 is one of the few isolated O-type targets, neighboring only a quiescent dense core, MM2.

In this paper, we focus on the study of the jet/outflow system in G26.50+0.28 by using three-configuration Atacama Large Millimeter/submillimeter Array (ALMA) data and fifteen epoch Very Long Baseline Array (VLBA) water maser data, with resolutions of $\approx$ 0.2$\hbox{$^{\prime\prime}$}$ (1260 au) and $\approx$0.002$\hbox{$^{\prime\prime}$}$ (13 au), respectively, to achieve a comprehensive understanding of the jet properties in G26.50+0.28.

# Observations

## ALMA data

The archival ALMA data of G26.50+0.28, including those of the 1.3 mm continuum and the typical outflow tracers $^{13}$CO(2-1) (220.399 GHz) and SiO(5-4) (217.105 GHz), were observed in Cycle 6 as part of the ALMA Large project ALMAGAL: ALMA Evolutionary study of High Mass Protocluster Formation in the Galaxy (2019.1.00195.L, PI: Sergio Molinari). These data are used to study the large-scale structures of the outflow and also allow us to understand the origin of the water masers. The ALMA observations were carried out in Cycle 6 with the Atacama Compact Array (ACA) (with baselines in the range 8.85–48.95 m) and 12-m array in C-4 (with baselines the range 15.06–783.54 m) and C-6 (with baselines in the range 15.06–2516.86 m) configurations. The on source times for 7m, C-4, and C-6 configuration observations are 100s, 54s, and 120s, respectively. These observations used J1924-2914 as the flux and band pass calibrators and J1832-1035 as the gain calibrator. See Table 1 for the details of the setups.

The data were calibrated and imaged using the Common Astronomy Software Applications (CASA) package (cite: 2007ASPC..376..127M) version 5.6.1.8 for the 7m and C-4 observations and 6.1.1 for the C-6 observations. The 7 m and two configuration 12 m data were first processed via the standard ALMA reduction pipeline separately (pipeline version 42866M for the 7m observations, 42866 for the C-4 observations, and 2020.1.0.40 for the C-6 observations) and then combined following standard procedures. We used the multiscale deconvolver (cite: 2008ISTSP...2..793C) with scales of zero (delta-function) and 6, 10, and 20 times the pixel size, which are about 1, 2, and 4 times the beam size, to recover both compact and extended emission.

The continuum image was produced using the multi-frequency synthesis (cite: 1990MNRAS.246..490C) algorithm over a frequency range identified to lack line emission.

For the spectroscopic data cubes, we first used the CASA task uvcontsub with the polynomial order of unity to subtract the continuum emission in the $uv$ domain and then cleaned the channels with a width of 1 $\hbox{${\rm km\,s}^{-1}$}$ in the range of 70-140 $\hbox{${\rm km\,s}^{-1}$}$.

For all the data products, we used Briggs cleaning and set the robustness parameter robust to the default value of 0.5, which provides a good compromise between noise and resolution. The continuum image reaches a 1$\sigma$ noise level of 0.3 m$\hbox{Jy\,beam$^{-1}$}$ in a synthesized beam of 0$\hbox{$\,.\!\!^{\prime\prime}$}$30$\times$0$\hbox{$\,.\!\!^{\prime\prime}$}$17 with P.A. $\approx$-65$\hbox{$^{\circ}$}$.

The synthesized beams for $^{13}$CO (2-1) and SiO (5-4) with $\approx$ 0$\hbox{$\,.\!\!^{\prime\prime}$}$36$\times$0$\hbox{$\,.\!\!^{\prime\prime}$}$24 and PA $\approx$-57$\hbox{$^{\circ}$}$ are similar. The typical 1$\sigma$ noise level of the two line images is $\mathrel{\mathchoice   {\vcenter{\offinterlineskip\halign{\hfil
$\displaystyle##$\hfil\cr<\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\textstyle##$\hfil\cr
<\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptstyle##$\hfil\cr
<\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptscriptstyle##$\hfil\cr
<\cr\sim\cr}}}}$ 5.0 m$\hbox{Jy\,beam$^{-1}$}$ in a 1 $\hbox{${\rm km\,s}^{-1}$}$-wide channel.

In this paper, ALMA maps represent the combined ACA, C-4, and C-6 data.

+:-----------:+:-----------:+:-------------:+:-----------:+
| SPW         | Freq. Cove. | Channel Width | Channels    |
+-------------+-------------+---------------+-------------+
|             | (GHz)       | (kHz)         |             |
+-------------+-------------+---------------+-------------+
| \(1\)       | \(2\)       | \(3\)         | \(4\)       |
+-------------+-------------+---------------+-------------+
| 7m ACA                                                  |
+---------------------------------------------------------+
| Obs. Date: Oct. 22, 30 2019, Mar. 07 2020               |
+-------------+-------------+---------------+-------------+
| 1           | 216.8-218.8 | 488.281       | 4096        |
+-------------+-------------+---------------+-------------+
| 2           | 218.8-220.8 | 488.281       | 4096        |
+-------------+-------------+---------------+-------------+
| 3           | 217.9-218.5 | 122.281       | 4096        |
+-------------+-------------+---------------+-------------+
| 4           | 220.3-220.8 | 122.281       | 4096        |
+-------------+-------------+---------------+-------------+
| 12m C-4                                                 |
+---------------------------------------------------------+
| Obs. Date: Oct. 12, 13, 2019                            |
+-------------+-------------+---------------+-------------+
| 1           | 217.0-218.8 | 488.281       | 3840        |
+-------------+-------------+---------------+-------------+
| 2           | 219.0-220.8 | 488.281       | 3840        |
+-------------+-------------+---------------+-------------+
| 3           | 217.8-218.2 | 122.281       | 3840        |
+-------------+-------------+---------------+-------------+
| 4           | 220.3-220.8 | 122.281       | 3840        |
+-------------+-------------+---------------+-------------+
| 12m C-6                                                 |
+---------------------------------------------------------+
| Obs. Date: May 27, June 6, 7, 9 2021                    |
+-------------+-------------+---------------+-------------+
| 1           | 217.0-218.8 | 488.281       | 3840        |
+-------------+-------------+---------------+-------------+
| 2           | 219.0-220.8 | 488.281       | 3840        |
+-------------+-------------+---------------+-------------+
| 3           | 217.8-218.2 | 122.281       | 3840        |
+-------------+-------------+---------------+-------------+
| 4           | 220.3-220.8 | 122.281       | 3840        |
+-------------+-------------+---------------+-------------+

: Summary of the spectral setups of the ALMA observations.

Table notes: Columns (1) – (4) are spectral windows, ranges of rest frequencies covered by the spectral windows, channel widths, and channel numbers.

## VLBA data

Fifteen epoch VLBA water maser (22.23508 GHz) observations of G26.50+0.28 were conducted from 2015 March 25 to 2016 May 7 under program BR210, which is part of the VLBA Key Science project, the Bar And Spiral Structure Legacy (BeSSeL) Survey[^2]. The intensive observations spanning about 13 months are important for constraining the time-dependent effects of water masers themselves.

A total of 2000 8 kHz ($\approx$0.11 $\hbox{${\rm km\,s}^{-1}$}$) channels centered at V$_{\rm LSR}$ = 104 $\hbox{${\rm km\,s}^{-1}$}$ (Channel 1001) were used.

The data were calibrated and imaged using the Astronomical Image Processing System (AIPS) scripts written in ParselTongue (cite: 2006ASPC..351..497K). Calibration procedures were conducted following the procedures of the BeSSeL survey (cite: 2009ApJ...700..137R).

In this case, masers are much stronger than the background sources. Therefore, inverse phase-referening was applied, where the fringe fit in all the epochs was performed with a strong and point-like water maser spot identified at V$_{\rm LSR}$ = 104.11 $\hbox{${\rm km\,s}^{-1}$}$ (channel 1000) and (R.A., DEC)$_{\rm J2000}$ = (18:38:40.1707, -05:35:42.7749). Then the calibration was transferred to the continuum background sources and the other spectral channels.

The synthesized beam size varies from epoch to epoch, but is typically about 2.0 $\times$ 1.0 mas (13$\times$6 au) (see Table [\[tab:epoch\]](#tab:epoch)). We fit two-dimensional Gaussian brightness distributions to each identified maser spot to obtain its position using the AIPS task SAD, resulting in $\mathrel{\mathchoice   {\vcenter{\offinterlineskip\halign{\hfil
$\displaystyle##$\hfil\cr>\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\textstyle##$\hfil\cr
>\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptstyle##$\hfil\cr
>\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptscriptstyle##$\hfil\cr
>\cr\sim\cr}}}}$ 200 water maser spots in each of the 15 epochs (see Table [\[tab:epoch\]](#tab:epoch)); refer to (cite: 2021ApJS..253....1X) for detailed information on the observations.

We should note that the maser spots are mainly from $\approx$ 30 maser features (a group of maser spots being continuous in velocity) (see Table [\[tab:epoch\]](#tab:epoch)). The maser features and their proper motions are shown in Fig. [11](#fig:feature), which are consistent with the results derived from the maser spots (see Section [4.3](#sec:pm)). However, we find that the standard deviation of the amplitudes of the proper motions derived from maser features in the two maser clusters (see Section [4.3](#sec:pm)) is larger than that derived from maser spots.

This may be the case because the position of a feature was estimated based on the flux-weighted positions of the spots within the feature, which could potentially introduce additional errors in the position determination. For instance, features can comprise varying numbers of maser spots at different epochs due to the rapid intensity variability of water masers.

Therefore, in this work, we use the multi-epoch water maser spots to conduct internal motion studies, which has been proved to be capable of determining the proper motions of the outflowing H$_2$O masers in star-forming regions (cite: 2011MNRAS.410..627T; 2013ApJ...775...79Z).

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Epoch | Obs. Date | beam(mas) | P.A. | N$_{\rm s}$ | N$_{\rm f}$ | jet/wind |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |
| E2 | Mar. 25 2015 | 1.80$\times$1.10 | 8$\hbox{$^{\circ}$}$ | 262 | 35 | 0.535 |
| E3 | Apr. 19 2015 | 2.01$\times$1.20 | 22$\hbox{$^{\circ}$}$ | 264 | 28 | 0.581 |
| E4 | May 08 2015 | 1.65$\times$1.13 | 42$\hbox{$^{\circ}$}$ | 252 | 27 | 0.605 |
| E5 | Aug. 19 2015 | 1.72$\times$0.81 | -1$\hbox{$^{\circ}$}$ | 169 | 24 | 0.598 |
| E6 | Sep. 07 2015 | 2.65$\times$1.12 | -5$\hbox{$^{\circ}$}$ | 185 | 21 | 0.603 |
| E7 | Sep. 18 2015 | 2.14$\times$1.00 | -3$\hbox{$^{\circ}$}$ | 208 | 23 | 0.613 |
| E8 | Oct. 01 2015 | 1.67$\times$1.02 | -1$\hbox{$^{\circ}$}$ | 234 | 28 | 0.606 |
| E9 | Oct. 12 2015 | 1.70$\times$0.73 | -7$\hbox{$^{\circ}$}$ | 215 | 27 | 0.598 |
| E10 | Oct. 26 2015 | 1.74$\times$0.68 | -8$\hbox{$^{\circ}$}$ | 227 | 27 | 0.587 |
| E11 | Nov. 05 2015 | 1.83$\times$1.09 | 20$\hbox{$^{\circ}$}$ | 255 | 31 | 0.577 |
| E12 | Nov. 17 2015 | 1.72$\times$1.06 | 13$\hbox{$^{\circ}$}$ | 230 | 30 | 0.579 |
| E13 | Feb. 18 2016 | 2.44$\times$0.60 | -13$\hbox{$^{\circ}$}$ | 251 | 25 | 0.583 |
| E14 | Mar. 15 2016 | 1.67$\times$1.00 | 25$\hbox{$^{\circ}$}$ | 234 | 24 | 0.589 |
| E15 | Apr. 11 2016 | 1.49$\times$0.75 | -8$\hbox{$^{\circ}$}$ | 253 | 25 | 0.594 |
| E16 | May 07 2016 | 2.41$\times$0.86 | -12$\hbox{$^{\circ}$}$ | 209 | 24 | 0.599 |

Table notes: Column 1: epoch name. Column 2: Observing dates. Columns 3 and 4: The size and P.A. of the beam. Columns 5 and 6: The total number of maser spots and features detected. Column 7: The ratio between the total flux of the maser spots associated with the dense jet, i.e. maser spots in MC-1 and MC-2 (see Fig. [7](#fig:mc12)), and the total flux of the ones in the blue lobe (see the right panel of Fig. [6](#fig:maserDis)).

## Herschel data

Far-infrared data were observed by the Herschel Space Observatory which was built and operated by the European Space Agency (ESA) (cite: 2010A&A...518L...1P). Herschel SPIRE 250$\mu$m data of G26.50+0.28 were derived from the Herschel High Level Images (HHLI)[^3]. The data have been processed to Level 2.5 through the Standard Product Generation pipeline, version 14.0. The angular resolution of the SPIRE 250 $\mu$m data is 18$\hbox{$^{\prime\prime}$}$ (cite: 2010A&A...518L...3G). The SPIRE image data is calibrated in $\hbox{Jy\,beam$^{-1}$}$.

# Large-scale structures reveled by ALMA observations

## 1.3 mm continuum

The 1.3 mm continuum radiation is completely dominated by dust emission, due to the faintness of the free-free emission (cite: 2012ApJ...756..170Q). In the left panel of Fig.[1](#fig:cont), two dense cores, MM1 and MM2, are identified in the ALMA 1.3 mm continuum image, which is consistent with the previous SMA observations.

The ALMA image also shows diffuse emission connecting MM1 and MM2, while, on larger scales, more diffuse emission arises from a filamentary structure roughly extending in a north-south direction as seen in the right panel of Fig. [1](#fig:cont).

In the high-resolution ALMA image, the MM1 core is slighly resolved, enabling us to see the elongated morphology of MM1 for the first time. This is also true for the ALMA 1.3 mm continuum image restored with a 0$\hbox{$\,.\!\!^{\prime\prime}$}$3 circular beam (see Fig. [12](#fig:cont_bmc)). Meanwhile, the elongation is perpendicular to the putative collimated jet (see below), making the target a potential jet-disk system. Furthermore, the inclination of the jet to the plane of the sky should be smaller (due to the disk thickness) than $\arctan(b/a)$ $\approx$32$\hbox{$^{\circ}$}$, assuming a circular disk/toroid, where the deconvolved major and minor diameters $a$ and $b$ are 0$\hbox{$\,.\!\!^{\prime\prime}$}$65 (4088 au) and 0$\hbox{$\,.\!\!^{\prime\prime}$}$41 (2608 au), respectively.

Vice versa, the scale height H of the disk/toroid can be also roughly estimated, complemented by the relatively robust jet inclination of 8$\hbox{$^{\circ}$}$ with respect to the plane of the sky (see Section [4](#sec:vlba)). Assuming the jet is perpendicular to the disk, then $H = (b-a \times$ $\sin$(8$\hbox{$^{\circ}$}$))/$\cos(8$$^{\circ}$$)$ $\approx$ 0$\hbox{$\,.\!\!^{\prime\prime}$}$33 (2060 au), which is about half of the major diameter of the disk/toroid.

The scale height is also related to the mass of the central star (cite: 2014A&A...566A..73C),

$$\begin{equation}
\label{height}
  H =\frac{FWHM}{\sqrt{8\ln(2)}}\sqrt{\frac{R_{disk}^{3}}{\rm G \it M_{\star}}},
\end{equation}$$

where the FWHM linewidth is set to 6 $\hbox{${\rm km\,s}^{-1}$}$ which is the value found for the 217.3 GHz $\nu_{t}$=1 6(1,5)–7(2,6) line of the typical disk tracer CH$_{3}$OH from the ALMA data. The radius of the disk, $R_{\rm disk} = a/2$, is 0$\hbox{$\,.\!\!^{\prime\prime}$}$325 (see above). Then the derived mass of the central star $M_{\star}$ is about 15 M$_{\odot}$, which is consistent with the mass derived by (cite: 2012ApJ...756..170Q) of 12 M$_{\odot}$.

The velocity gradients, found with the typical disk tracers CH$_{3}$OH (6$_{1,5}$-7$_{2,6}$ $\nu_{t}$=1) and CH$_{3}$CN (12$_{7}$-11$_{7}$ $\nu_{t}$=1) (cite: 2016A&ARv..24....6B), are roughly perpendicular to the jet (see Fig. [2](#fig:cont-vel)).

The velocity gradient is also generally consistent with that revealed by previous SMA data.

The higher resolution ALMA data seem to present an even thinner disk with a higher velocity gradient in MM1 (see Fig.[2](#fig:cont-vel)).

However, the resolution of the ALMA data is not high enough to fully resolve it. Being also beyond the scope of this work, it will be followed up in a future contribution based on higher resolution data.

![image](cont.pdf) ![image](250.pdf)

![image](cont-velCH3OH.pdf) ![image](cont-velCH3CN.pdf) ![image](CH3OH_pvd.pdf) ![image](CH3CN_pvd.pdf)

## $^{13}$CO (2-1) and SiO (5-4) maps

Fig. [3](#fig:CO_SiO) presents the velocity-integrated maps of two typical jet/outflow tracers, the $^{13}$CO (2-1) (left panel) and the SiO (5-4) lines (right panel). A collimated jet-like structure centered at MM1, denoted by the solid blue and red arrows, is presented in both panels of Fig. [3](#fig:CO_SiO), which is more prominent in the SiO(5-4) map. A redshifted clump shown at the base of the blue lobe may be produced by jet precession (see Section [3.3](#sec:jet-precession)).

As mentioned in Section [3.1](#sec:disk), the axis of the jet is perpendicular to the elongation of the disk/toroid and its velocity gradient. Meanwhile, this collimated jet is consistent with the distribution of the VLBA water masers (see Section [4](#sec:vlba)).

The remaining blueshifted and redshifted $^{13}$CO (2-1) emission has a complex distribution, forming shell-like structures on either side of the collimated jet (except for the relatively diffuse emission in the northern part of the $^{13}$CO (2-1) map), which may be enhanced by limb-brightening.

The shells have an opening angle of about 140$\hbox{$^{\circ}$}$, denoted by the gray lines in Fig. [3](#fig:CO_SiO).

The mixture of blueshifted and redshifted emissions may be explained by the combined effect of wide-angle winds and the small inclination of the jet/outflow. The two shells in the roughly north-south direction show relatively strong $^{13}$CO (2-1) and SiO(5-4) emissions in the two panels of Fig. [3](#fig:CO_SiO).

We note: (1) the two sided shells do not show point- or mirror-symmetry relative to MM1 or MM2, especially the northern shell is bending by about 90$\hbox{$^{\circ}$}$ (see the right panel of Fig. [3](#fig:CO_SiO)), which may be not commonly seen in jets. Actually, the overall morphology of the shells roughly follows the large-scale north-south filamentary structure seen in the right panel of Fig. [1](#fig:cont). Therefore it is likely caused by the interactions between the wide-angle winds with the dense filamentary structure; (2) most of the water masers are exclusively associated with the collimated jet and barely with the shells (see Section [4](#sec:vlba)). Therefore, it is likely that Fig. [3](#fig:CO_SiO) presents a collimated dense jet with wide-angle wind components. The wide-angle winds are interacting with the large-scale filamentary structure, enhancing the $^{13}$CO (2-1) and SiO(5-4) emission in the north-south shells.

We should note that the possibility that an additional jet is hiding in the relatively strong north-south shells cannot be excluded.

Meanwhile, as mentioned in the introduction, based on the SMA data, (cite: 2012ApJ...756..170Q) argued that there is a wide-angle northeast-southwest bipolar outflow centered at MM1. The axis of the outflow is denoted by the dashed red and blue arrows in Fig. [3](#fig:CO_SiO) with P.A. $\approx$ 45$\hbox{$^{\circ}$}$. However, our high resolution and sensitivity ALMA data have further resolved the outflow and detected weaker emission of the shells. Complemented by the water maser distribution and its kinematics (see Section [4](#sec:vlba)), we derive a different interpretation, i.e. a collimated jet and wide-angle wind scenario.

We also present the low velocity emission of $^{13}$CO (2-1) in Fig. [13](#fig:COlv), which shows more clearly the shell structures, since entrained shells by the jet/wind are usually more obvious in tracers of the low velocity emission (e.g. Plunkett et al. 2015).

![image](outflow_CO.pdf) ![image](outflow_SiO.pdf)

## Jet precession

We can see from Fig. [3](#fig:CO_SiO) that the two lobes of the collimated jet seem to present point-symmetric (S-shaped) wiggles relative to MM1, suggesting precession.

In order to model it, we used a simple sinusoidal equation (cite: 2009ApJ...698..184W), adapted from (cite: 1996AJ....112.2086E) to fit the SiO(5-4) emission,

$$\begin{equation}

\label{jet_precession}
\left( \begin{matrix} x \\ y \end{matrix} \right)=  \left( \begin{matrix} \cos(\psi) & -\sin(\psi) \\ \sin(\psi)& \cos(\psi) \end{matrix} \right) \times  \left( \begin{matrix} \alpha l \sin(2\pi l /\lambda + \phi_{0} ) \\ l \times cos(i) \end{matrix} \right),
\end{equation}$$

where $x$ and $y$ are the coordinates relative to MM1. $\alpha$ and $\lambda$ are the amplitude and wave scale of the precession. $\phi_{0}$ is the initial phase at the location of MM1. $\psi$ is the position angle of the jet symmetry axis in the plane of the sky. $i$ is the inclination angle of the jet to the plane of the sky.

The fitting results are summarized in Table [2](#tab:jet-precession) and illustrated in Fig. [3](#fig:CO_SiO) by the solid black curves. We can see that the fitting roughly recovers the wiggles of the two lobes. However, we should note that the amplitude of the jet wiggles is small. Therefore the fitting could not be well confined, which may be the reason for the relative poor fitting of the blueshifted lobe.

The derived precession length $\lambda$ is 7$\hbox{$\,.\!\!^{\prime\prime}$}$2, which is 0.22 pc at a distance of 6.3 kpc.

Assuming a jet velocity of $\sim$ 30 $\hbox{${\rm km\,s}^{-1}$}$ (see Section [4.3](#sec:pm)), the precession period should be at the order of 7000 years. We should note that the period may be overestimated, because the water maser velocity may be generally smaller than the possible jet velocity, due to entrainment of the pre-shock material (cite: 1993ApJ...414..230M; 2016A&A...585A..71M). If we assume a jet velocity of $\sim$ 200 $\hbox{${\rm km\,s}^{-1}$}$ (cite: 2018A&ARv..26....3A), the precession period should be about 1000 years.

According to the fitted $\phi_{0}$ of about 50$\hbox{$^{\circ}$}$, the P.A. of the jet at the times conducting the ALMA (2019-2021) and VLBA (2015) observations should be less than $\psi$ (70$\hbox{$\,.\!\!^{\circ}$}$1) and should continue to decrease, i.e. the jet should be located in the north of the mean axis of the jet and moving farther to the north (see the sketch of the jet/outflow in Fig. [4](#fig:jet-sch)).

This is further discussed in Section [4](#sec:vlba).

As we can see in Fig. [3](#fig:CO_SiO), the wiggles of the jet are not very obvious, especially on the blueshifted side of the jet. However, the fitted precession motion is consistent with the distribution and 3D motions of the water masers (see Section 4). Therefore, combining all the results of ALMA and VLBA, we argue that the jet likely harbors a small amplitude precession.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| $\psi$ | $\alpha$ | $\lambda$ | $\phi_{0}$ | $i$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) |
| 70$\hbox{$\,.\!\!^{\circ}$}$1$\pm$0$\hbox{$\,.\!\!^{\circ}$}$13 | 0$\hbox{$\,.\!\!^{\circ}$}$06$\pm$0$\hbox{$\,.\!\!^{\circ}$}$003 | 7$\hbox{$\,.\!\!^{\prime\prime}$}$2$\pm$0$\hbox{$\,.\!\!^{\prime\prime}$}$3 | 50$\hbox{$\,.\!\!^{\circ}$}$1$\pm$10$\hbox{$\,.\!\!^{\circ}$}$6 | 8.0 $^{$\dag$}$ |

: The parameters for the jet precession.

Table notes: Column 1: the position angle of the jet symmetry axis in the plane of the sky. Columns 2 and 3: the amplitude and wave scale of the precession. Column 4: the initial phase at the location of MM1. Column 5: the inclination angle of the jet to the plane of the sky.\
The inclination $i$ is fixed to 8$\hbox{$^{\circ}$}$ according to the calculations using water masers (see Section [4](#sec:vlba)). This is because the precession fitting is relatively insensitive to the inclination (cite: 2009ApJ...698..184W).

## Jet kinematics

Jets have been proposed to be the agent to transfer the angular momentum of protostars and disks to outflows. Direct observational evidence has been found in low-mass protostellar jets, e.g. in terms of the systematic velocity gradients perpendicular to the jet axis (cite: 2017NatAs...1E.152L).

Fig. [5](#fig:SiO-mom1) shows the intensity-weighted velocity (moment-1) SiO (5-4) map of the jet in G26.50+0.28. Only the 2$\hbox{$\,.\!\!^{\prime\prime}$}$0-wide belt along the jet symmetry axis is shown to highlight the kinematics in the collimated jet. It seems that the denser clumps in the red/blue jet show more redshifted/blueshifted velocities, which may be caused by an episodic ejection showing jagged velocities (cite: 2001ApJ...551L.171A). Besides the knots, no clear velocity trend, i.e. a roughly constant velocity perpendicular to the jet axis is seen in Fig. [5](#fig:SiO-mom1).

That the jet is collimated and has a small inclination relative to the plane of the sky allows investigations of its transverse kinematics, like in the case of the jet associated with the low-mass protostellar counterpart HH 212 (cite: 2017NatAs...1E.152L). Meanwhile, the ALMA observations have moderately resolved the width and the velocity distribution of the jet.

Therefore, the velocity gradient perpendicular to the axis of the jet, i.e. jet rotation, may not be prominent in G26.50+0.28.

![](jet_sch.pdf)

![](SiO_mom1.pdf)

# Water maser spots revealed by 15-epoch VLBA data

## The reference spot

The left panel of Fig. [6](#fig:maserDis) presents the plot of all (3448 in total) the water maser spots detected in the 15-epoch VLBA data. As mentioned in Section [2](#obs), fringe fitting for all the epochs were performed using a strong and point-like water maser spot.

Therefore, all measured proper motions of maser spots are relative to the reference spot.

The systemic motion can usually be derived by subtracting the mean or model (e.g. fitting the kinematics of the maser spots assuming an isotropic expansion) velocity of the persistent maser spots (found in all epochs) to transfer to a reference frame in which the mean proper motion is zero (cite: 2003ApJ...598L.115T; 2013ApJ...775...79Z). It is not applicable in G26.50+0.28 since the maser spots are mainly located in the blue lobe of the outflow, which likely biases the mean motion.

In this specific case, (1) the line-of-sight (l.o.s.) velocities of the reference spot (V$_{lsr}$ = 104.11 $\hbox{${\rm km\,s}^{-1}$}$) and the spots around it are close to the systematic velocity ($\approx$104 $\hbox{${\rm km\,s}^{-1}$}$, derived from Gaussian fits of ALMA CH$_{3}$CN lines (cite: 2012ApJ...756..170Q)); (2) the reference spot is well separated from the main star formation region and the outflow lobes (see the left panel of Fig. [6](#fig:maserDis)). The reference maser spot may not be (heavily) affected by the star-forming activities and the outflow. Therefore, the proper motions relative to the spot may trace the internal motions. The fact that the derived proper motions of the masers are naturally aligned along the direction of the jet identified in the ALMA data (see Section [4.3](#sec:pm)) gives our approach an additional measure of robustness.

In brief, for this unique case, we have a co-moving local “observer” to monitor the internal velocity of the maser spots, significantly eliminating the systemic motions, e.g., Galactic rotation as well as its non-circular (peculiar) velocity components.

![image](G26_PM_fullview.png) ![image](G26_PM_S2_select.png)

## The distribution of the water maser spots

We can see from the left panel of Fig. [6](#fig:maserDis) and Table [3](#tab:msNum) that most (2747, $\approx$ 80%) of the maser spots are located in the blue lobe of the outflow (the blue shadowed region in Fig. [6](#fig:maserDis)). Why very few (14) spots are located in the red lobe is not clear. It may be caused by a non-symmetric distribution, since the SiO emission at the base of the redshifted jet is also relatively weak (see the right panel of Fig. [3](#fig:CO_SiO)).

Outside the outflow lobes, maser spots are located mainly around the reference spot (473, $\approx$14%). These maser spots may be associated with shocks in the disk, e.g., accretion flows.

In the following, we focus on the maser spots in the blue lobe. We can see from the right panel of Fig. [6](#fig:maserDis) that the overall distribution of these maser spots presents clearly two patterns, i.e., two concentrated clusters, MC-1 and MC-2, exactly associated with the collimated jet identified in the ALMA data and scattered spots interspersed in the blue lobe. This two-pattern distribution is consistent with the collimated jet and wide-angle wind scenario seen in the ALMA data.

Along the jet axis, the water maser spots are exclusively distributed in the two clusters, suggesting possible episodic ejection since the masers are likely tracing shocks.

If we naively believe that the flux of maser spots is directly proportional to the intensity of the wind components[^4], the well-distinguished patterns of maser spots enable us to tentatively estimate the relative intensity or the fraction of total accelerated particles between dense (jet) and wide-angle winds for the first time. We can see from Table [\[tab:epoch\]](#tab:epoch) that the total flux of the maser spots associated with the dense jet, i.e. the ones in MC-1 and MC-2, is about the 60% (median) of the total flux of the maser spots in the blue lobe. That is about 60% of the accelerated particles (winds) are concentrated (or collimated) to the relative small angle around the jet axis.

From the right panel of Fig. [6](#fig:maserDis), we can see that the P.A. of MC-2 is smaller relative to that of MC-1 (MC-2 is closer to the north direction). This is consistent with the jet precession derived by ALMA data with $\phi_{0}$ of 50$\hbox{$\,.\!\!^{\circ}$}$1 (see Section [3.3](#sec:jet-precession)). However, according to the jet precession fitting in Section [3.3](#sec:jet-precession), the two clusters should be all located on the northern side of the symmetry axis (blue arrow in Fig. [6](#fig:maserDis)), which is not true for MC-1 and MC-2. A possible explanation is that the driving star of the jet may not necessarily be located at the dust peak of MM1 (it then may be located slightly to the south of the peak of MM1).

Fig. [7](#fig:mc12) shows the zoom-in images of MC-1 and MC-2. It is interesting to see that all the spots of MC-1 are located in a ring-like structure. We fit these maser spots with a 3D ellipse and the fitting result is shown in the left panel of Fig. [7](#fig:mc12). The fitted major and minor, $a$ and $b$, axes are 27$\hbox{$\,.\!\!^{\prime\prime}$}$6 and 4$\hbox{$\,.\!\!^{\prime\prime}$}$0, respectively.

Assuming the ring is a 3D circle and perpendicular to the jet axis, we can directly derive the inclination of the jet, $i = \arcsin(b/a)$ $\approx$ 8$\hbox{$\,.\!\!^{\circ}$}$4$\pm$0$\hbox{$\,.\!\!^{\circ}$}$5.

Meanwhile, we also fit the spots of the first seven (E2–E8) and last seven epochs (E10–E16) with 3D ellipses and do not find clear expanding or contracting motion of the ring within the time range of about one year (see Table [\[tab:epoch\]](#tab:epoch)).

As mentioned in Section [3.4](#sec:jetKin), no clear velocity gradient, i.e. jet rotation, has been found in the SiO moment-1 map (Fig. [5](#fig:SiO-mom1)), which is also true for the l.o.s. velocities (the color of the spots) of the maser spots in MC-1 and MC-2 (see Fig. [7](#fig:mc12)).

The left panel of Fig. [8](#fig:mc12-vlsr) shows the l.o.s. velocity of the maser spots in MC-1 (red) and MC-2 (blue) against the opening angle of the spot relative to the jet axis. Due to the large dispersion, no clear velocity trend is found in either MC-1 or MC-2. The overall velocity difference between the two clusters is likely caused by the precession.

The median velocities along l.o.s. of MC-1 and MC-2 are 102.2 and 93.5 $\hbox{${\rm km\,s}^{-1}$}$. Complemented by $\phi_{0}$ of 50$\hbox{$^{\circ}$}$ (see Table [2](#tab:jet-precession)), the jet precession is counterclockwise when looking along the blueshifted jet axis from MM1, which is co-rotating with the disk/toroid.

![image](G26_MC1_select.png) ![image](G26_MC2_select.png)

![image](mc12-vlsr.pdf) ![image](vel_opAng_mc12.pdf)

|           |        |
|:---------:|:------:|
|  Region   | Number |
|   \(1\)   | \(2\)  |
|   Total   |  3448  |
| blue lobe |  2747  |
| red lobe  |   14   |
|    MC1    |  871   |
|    MC2    |  816   |
|    Ref    |  473   |

: Numbers of water maser spots in different regions.

Table notes:

## Proper motions

We select 216 spots persisting for at least 5 epochs to calculate their proper motions. A constant velocity (linear) model is used in the fitting, since no clear evidence of acceleration is found. Fig. [9](#fig:pm) presents the derived proper motions of the spots. We can see that the proper motions of the spots in the blue lobe of the outflow are exactly consistent with the direction of the jet, especially the spots in MC-1 and MC-2.

From Fig. [10](#fig:histPM) we can see that the overall proper motion ($V_{\rm XY}$) and the 3D velocity ($V_{\rm 3D}$) of MC-1 are all larger than those of MC-2 (see also Table [\[tab:mc12_pm\]](#tab:mc12_pm)). The 3D velocities are generally larger than those of the high-mass sample in the Protostellar Outflows at the EarliesT Stages (POETS) survey (cite: 2020A&A...635A.118M), suggesting that the O-type protostar may launch winds with even greater intensity.

The 3D velocities also allow us to calculate the inclination of each spot (see the right panel of Fig.[10](#fig:histPM) and also Table [\[tab:mc12_pm\]](#tab:mc12_pm)). The median inclinations of the two clusters are 1$\hbox{$\,.\!\!^{\circ}$}$1$\pm$8$\hbox{$\,.\!\!^{\circ}$}$2 and 13$\hbox{$\,.\!\!^{\circ}$}$8$\pm$11$\hbox{$\,.\!\!^{\circ}$}$0, which are roughly consistent with the result from the elliptical fitting of MC-1 ($\approx$8$\hbox{$^{\circ}$}$). Given all the calculations, the typical inclination of the collimated jet may be around 8$\hbox{$^{\circ}$}$ with respect to the plane of the sky.

Observational evidence to distinguish the X- and disk-wind models is the variation of the magnitude of the velocity with different opening angles (cite: 2011A&A...532A..59A). However, studies based on spectroscopic observations usually only reveal velocities along the l.o.s.

Meanwhile, the line emission of the jet is usually contaminated by the emission of the ambient gas.

On the contrary, the maser spots are from very tiny regions, which should largely eliminate the emission from the background or foreground emission. Furthermore, 3D motion can all be derived in multi-epoch studies.

We plot the 3D jet velocity of the maser spots in MC-1 and MC-2 against the opening angle in the right panel of Fig. [8](#fig:mc12-vlsr). It seems to present a constant distribution of the 3D jet velocity ($V_{\rm 3D}$) against the opening angle with respect to the symmetry axis of the jet albeit with large dispersion. The constant distribution may suggest that the winds associated with the collimated jet may be launched from a relatively narrow region of the disk, since the launching velocity is proportional to the Keplerian velocity of the launching point (cite: 2016ARA&A..54..491B).

At last, we should note that proper motions of water masers may harbor large dispersions (cite: 2006ApJ...645..337H; 2016A&A...585A..71M). For G26.50+0.28, the distribution and the proper motions of the maser spots, especially in MC-1 and MC-2, are consistent with the collimated jet. Therefore, it is likely that the proper motions of these spots are representing the kinematics of the jet. Meanwhile, the relatively robust medians of the velocities are commonly used in this work, alleviating the possible turbulent motions of the maser spots.

![image](G26_PM_all.png) ![image](G26_PM_S2.png) ![image](G26_PM_S2-MC1.png) ![image](G26_PM_S2-MC2.png)

| Region | $V_{\rm 3D}$ ($\hbox{${\rm km\,s}^{-1}$}$) | $V_{\rm XY}$ ($\hbox{${\rm km\,s}^{-1}$}$) | $V_{\rm Z}$ ($\hbox{${\rm km\,s}^{-1}$}$) | inclination |
|:--:|:--:|:--:|:--:|:--:|
| MC-1 | 35.6$\pm$15.7 | 35.5$\pm$15.8 | -1.02$\pm$4.6 | 1$\hbox{$\,.\!\!^{\circ}$}$1$\pm$8$\hbox{$\,.\!\!^{\circ}$}$2 |
| MC-2 | 29.1$\pm$13.4 | 28.7$\pm$13.6 | -7.62$\pm$5.9 | 13$\hbox{$\,.\!\!^{\circ}$}$8$\pm$11$\hbox{$\,.\!\!^{\circ}$}$0 |

Table notes: The columns all show the medians of different parameters. Columns 2, 3, and 4: 3D jet, plane of the sky (proper motion), and line-of-sight velocities of the maser spots in MC-1 and MC-2. Column 5: Inclinations calculated from the three-dimensional velocity components.

![image](vel_Vxy.pdf) ![image](vel_vel.pdf) ![image](Vel_inclination.pdf)

# Discussion and summary

We have studied the detailed morphology and kinematics of the outflow in the high-mass star formation region G26.50+0.28. The ALMA and VLBA observations reveal a clear and consistent picture of the outflow associated with an O-type protostar candidate (see Fig. [4](#fig:jet-sch)), which is a scaled-up version of the collimated jet and wide-angle wind scenario of the low-mass counterpart, e.g. HH 212 (cite: 2017NatAs...1E.152L; 2022ApJ...927L..27L).

The collimated jet is first identified with the ALMA $^{13}$CO (2-1), SiO (5-4), and VLBA water maser spots, which is exactly perpendicular to the elongated disk/toroid and the velocity gradient of the disk. The jet is embraced by cavity shells with an opening angle of about 140$\hbox{$^{\circ}$}$. The enhanced north-south shell is likely caused by the interaction of the wind with the ambient filamentary structure.

Regarding the directions of the outflow as defined by (cite: 2012ApJ...756..170Q) and this work (see Section [3.2](#sec:CO_SiO)), there is a $\approx$25$\hbox{$^{\circ}$}$ disparity between the directions of our collimated jet (also the mean outflow direction) and the axis of the bipolar outflow reported by (cite: 2012ApJ...756..170Q).

This introduces a caveat to the studies based on directions of jets/outflows (cite: 2014ApJ...792..116Z; 2017ApJ...846...16S), especially in high-mass star-forming regions with extremely wide outflows, where the basic results may depend on the chosen resolution and tracer.

The collimated jet is likely suffering a small amplitude counterclockwise precession, when looking along the blueshifted jet axis from MM1, with a precession length of 0.22pc. Assuming a 30 $\hbox{${\rm km\,s}^{-1}$}$ jet velocity, the possible period is on the order of 7000 years.

The inclination of the collimated jet should be very low ($\approx$8$\hbox{$^{\circ}$}$), which makes the jet in G26.50+0.28 a promising target to study the transverse morphology and kinematics of the jet and also the interactions with the edge-on disk (cite: 2017NatAs...1E.152L; 2019Natur.565..206S). However, no clear evidence of a velocity gradient perpendicular to the jet axis, i.e. jet rotation along the axis, is found in ALMA or VLBA data.

Water masers are mainly located in the blue lobe of the outflow. Two water maser clusters are closely associated with the collimated jet. Thus it is likely they are produced by the dense jet.

The median distances of the two water maser clusters to MM1 in the plane of the sky are 0$\hbox{$\,.\!\!^{\prime\prime}$}$39 and 0$\hbox{$\,.\!\!^{\prime\prime}$}$19, respectively. Assuming that MC-1 and MC-2 are ejected near the MM1 region and their velocities correspond to the median V$_{XY}$ (see Table [\[tab:mc12_pm\]](#tab:mc12_pm)), the estimated dynamical timescales for MC-1 and MC-2 would be approximately 300 and 200 years, respectively. This suggests that they appear to arise from separate ejections or shocks.

However, their origin, especially the very regularly distributed ring-like MC-1, is relatively elusive.

Higher resolution SiO and radio continuum data would help us to understand their origin. For example, they could be produced by episodic ejections traversing through a small cloud. Another possibility is that the two clusters may be generated by different shocks, i.e. the leading and reverse shocks within an internal working surface, since the leading MC-1 with velocity greater than 30 $\hbox{${\rm km\,s}^{-1}$}$ ($\approx$35.6 $\hbox{${\rm km\,s}^{-1}$}$) may be associated with J-shocks (cite: 1993ApJ...414..230M; 2020A&A...635A.118M) and also moves faster. On the contrary, MC-2 with velocities $\approx$28.8 $\hbox{${\rm km\,s}^{-1}$}$ is slower and may be associated with C-shocks.

We also tentatively estimate the amount of accelerated particles by comparing the total maser flux between the dense and diffuse wind components, i.e. the collimated jet and wide-angle winds. About 60% of the accelerated particles may be concentrated (or collimated) along the jet with a small opening angle around the jet axis, which means the collimated jet and wide-angle winds are roughly comparable in G26.50+0.28. The 3D jet velocities derived from the water maser spots with opening angles $\mathrel{\mathchoice   {\vcenter{\offinterlineskip\halign{\hfil
$\displaystyle##$\hfil\cr<\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\textstyle##$\hfil\cr
<\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptstyle##$\hfil\cr
<\cr\sim\cr}}}
{\vcenter{\offinterlineskip\halign{\hfil$\scriptscriptstyle##$\hfil\cr
<\cr\sim\cr}}}}$8$\hbox{$^{\circ}$}$ seem to be constant, suggesting the jet may be launched in a relatively small region, which favors the X-wind model (cite: 2007prpl.conf..261S).

# Acknowledgements

This work was funded by the National Key R&D Program of China (No. 2022YFA1603103), the CAS “Light of West China” Program (No. 2021-XBQNXZ-028), the National Natural Science foundation of China (Nos.12103082 and 11603063), and the Natural Science Foundation of Xinjiang Uygur Autonomous Region (No. 2022D01A362). GW acknowledges the support from Youth Innovation Promotion Association CAS.

(ref: 2018A&ARv..26....3A) Anglada, G., Rodrı́guez, L. F., & Carrasco-González, C. 2018, A&ARv, 26, 3

(ref: 2011A&A...532A..59A) Agra-Amboage, V., Dougados, C., Cabrit, S., et al. 2011, A&A, 532, A59

(ref: 2001ApJ...551L.171A) Arce, H. G. & Goodman, A. A. 2001, ApJL, 551, L171

(ref: 2007prpl.conf..245A) Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, Protostars and Planets V, 245

(ref: 2016ARA&A..54..491B) Bally, J. 2016, ARA&A, 54, 491

(ref: 2021MNRAS.507.4316B) Baug, T., Wang, K., Liu, T., et al. 2021, MNRAS, 507, 4316

(ref: 2016A&ARv..24....6B) Beltrán, M. T. & de Wit, W. J. 2016, A&ARv, 24, 6

(ref: 2022A&A...659A..81B) Beltrán, M. T., Rivilla, V. M., Cesaroni, R., et al. 2022, A&A, 659, A81

(ref: 2002A&A...383..892B) Beuther, H., Schilke, P., Sridharan, T. K., et al. 2002, A&A, 383, 892

(ref: 1982MNRAS.199..883B) Blandford, R. D. & Payne, D. G. 1982, MNRAS, 199, 883

(ref: 2021ApJ...914L...1C) Carrasco-González, C., Sanna, A., Rodrı́guez-Kamenetzky, A., et al. 2021, ApJL, 914, L1

(ref: 2007prpl.conf..197C) Cesaroni, R., Galli, D., Lodato, G., et al. 2007, Protostars and Planets V, 197

(ref: 2014A&A...566A..73C) Cesaroni, R., Galli, D., Neri, R., et al. 2014, A&A, 566, A73

(ref: 1990MNRAS.246..490C) Conway, J. E., Cornwell, T. J., & Wilkinson, P. N. 1990, MNRAS, 246, 490

(ref: 2008ISTSP...2..793C) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793

(ref: 2020A&A...634L..12D) de Valon, A., Dougados, C., Cabrit, S., et al. 2020, A&A, 634, L12. doi:10.1051/0004-6361/201936950

(ref: 2022A&A...668A..78D) de Valon, A., Dougados, C., Cabrit, S., et al. 2022, A&A, 668, A78. doi:10.1051/0004-6361/202141316

(ref: 1996AJ....112.2086E) Eisloffel, J., Smith, M. D., Davis, C. J., et al. 1996, AJ, 112, 2086

(ref: 1992ARA&A..30...75E) Elitzur, M. 1992, ARA&A, 30, 75

(ref: 2013ApJ...778...72F) Fernández-López, M., Girart, J. M., Curiel, S., et al. 2013, ApJ, 778, 72

(ref: 2014prpl.conf..451F) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, Protostars and Planets VI, 451

(ref: 2020ApJ...905...25G) Goddi, C., Ginsburg, A., Maud, L. T., et al. 2020, ApJ, 905, 25

(ref: 2010A&A...518L...3G) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3

(ref: 2006ApJ...645..337H) Hachisuka, K., Brunthaler, A., Menten, K. M., et al. 2006, ApJ, 645, 337

(ref: 2006ASPC..351..497K) Kettenis, M., van Langevelde, H. J., Reynolds, C., et al. 2006, Astronomical Data Analysis Software and Systems XV, 351, 497

(ref: 2000prpl.conf..759K) Konigl, A. & Pudritz, R. E. 2000, Protostars and Planets IV, 759

(ref: 2017NatAs...1E.152L) Lee, C.-F., Ho, P. T. P., Li, Z.-Y., et al. 2017, Nature Astronomy, 1, 0152

(ref: 2021ApJ...907L..41L) Lee, C.-F., Tabone, B., Cabrit, S., et al. 2021, ApJL, 907, L41

(ref: 2022ApJ...927L..27L) Lee, C.-F., Li, Z.-Y., Shang, H., et al. 2022, ApJL, 927, L27

(ref: 1993ApJ...414..230M) Masson, C. R. & Chernin, L. M. 1993, ApJ, 414, 230

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., et al. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: 2016A&A...585A..71M) Moscadelli, L., Sánchez-Monge, Á., Goddi, C., et al. 2016, A&A, 585, A71

(ref: 2020A&A...635A.118M) Moscadelli, L., Sanna, A., Goddi, C., et al. 2020, A&A, 635, A118

(ref: 2006ApJ...649..816N) Neufeld, D. A., Melnick, G. J., Sonnentrucker, P., et al. 2006, ApJ, 649, 816

(ref: 2010A&A...518L...1P) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1

(ref: 2015Natur.527...70P) Plunkett, A. L., Arce, H. G., Mardones, D., et al. 2015, Nature, 527, 70. doi:10.1038/nature15702

(ref: 2012ApJ...756..170Q) Qiu, K., Zhang, Q., Beuther, H., et al. 2012, ApJ, 756, 170

(ref: 2009ApJ...700..137R) Reid, M. J., Menten, K. M., Zheng, X. W., et al. 2009, ApJ, 700, 137

(ref: 1993A&A...278..267R) Raga, A. & Cabrit, S. 1993, A&A, 278, 267

(ref: 2019Natur.565..206S) Sakai, N., Hanawa, T., Zhang, Y., et al. 2019, Nature, 565, 206

(ref: 2007prpl.conf..261S) Shang, H., Li, Z.-Y., & Hirano, N. 2007, Protostars and Planets V, 261

(ref: 2000prpl.conf..789S) Shu, F. H., Najita, J. R., Shang, H., et al. 2000, Protostars and Planets IV, 789

(ref: 2017ApJ...846...16S) Stephens, I. W., Dunham, M. M., Myers, P. C., et al. 2017, ApJ, 846, 16

(ref: 2017A&A...597A.119T) Tafalla, M., Su, Y.-N., Shang, H., et al. 2017, A&A, 597, A119

(ref: 2003ApJ...598L.115T) Torrelles, J. M., Patel, N. A., Anglada, G., et al. 2003, ApJL, 598, L115

(ref: 2011MNRAS.410..627T) Torrelles, J. M., Patel, N. A., Curiel, S., et al. 2011, MNRAS, 410, 627

(ref: 2009ApJ...698..184W) Wu, P.-F., Takakuwa, S., & Lim, J. 2009, ApJ, 698, 184

(ref: 2004A&A...426..503W) Wu, Y., Wei, Y., Zhao, M., et al. 2004, A&A, 426, 503

(ref: 2021ApJS..253....1X) Xu, Y., Bian, S. B., Reid, M. J., et al. 2021, ApJS, 253, 1

(ref: 2013ApJ...775...79Z) Zhang, B., Reid, M. J., Menten, K. M., et al. 2013, ApJ, 775, 79

(ref: 2014ApJ...792..116Z) Zhang, Q., Qiu, K., Girart, J. M., et al. 2014, ApJ, 792, 116

# Distribution and proper motions of the water maser features

![image](G26_fPM_fullview.png) ![image](G26_fPM_all.png)

# ALMA 1.3 mm continuum image restored with a 0$\hbox{$\,.\!\!^{\prime\prime}$}$3 circular beam

![](cont_bmc.pdf)

# Low-velocity $^{13}$CO emission of the outflow

![](outflow_CO_97-111.pdf)

[^1]: A maser spot represents a compact emission peak in a specific velocity channel. Maser features arise from the same region but extend over several contiguous velocity channels.

[^2]: http://bessel.vlbi-astrometry.org

[^3]: https://irsa.ipac.caltech.edu/data/Herschel/HHLI

[^4]: We should note that this assumption is relatively coarse, since the excitation and intensity of masers depends on many factors like the geometry, path lenghts, and the properties of shocks and the local gas (cite: 1992ARA&A..30...75E).

</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Fraction of blue-lobe maser flux in dense jet (MC-1 and MC-2) = 60 %",
  "failed_quote": "We can see from Table [tab:epoch] that the total flux of the maser spots associated with the dense jet, i.e. the ones in MC-1 and MC-2, is about the 60% (median) of the total flux of the maser spots in the blue lobe."
 }
]
```
