# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021MNRAS.504.2687N\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Morpho-kinematics of the circumstellar envelope of the AGB star R Dor: a global view

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

# Abstract

We analyse new ALMA observations of the $^{29}$SiO ($\nu$=0, $J$=8$-$7) and SO$_2$($\nu$=0, $34_{3,31}$$-$$34_{2,32}$) line emissions of the circumstellar envelope (CSE) of the oxygen-rich AGB star R Dor. With a spatial resolution of $\sim$2.3 au, they cover distances below $\sim$30 au from the star providing a link between earlier observations and clarifying some open issues. The main conclusions are: 1) Rotation is confined below $\sim$15 au from the star, with velocity reaching a maximum below 10 au and morphology showing no significant disc-like flattening. 2) In the south-eastern quadrant, a large Doppler velocity gas stream is studied in more detail than previously possible and its possible association with an evaporating planetary companion is questioned. 3) A crude evaluation of the respective contributions of rotation, expansion and turbulence to the morpho-kinematics is presented. Significant line broadening occurs below $\sim$12 au from the star and causes the presence of high Doppler velocity components near the line of sight pointing to the centre of the star. 4) Strong absorption of the continuum emission of the stellar disc and its immediate dusty environment is observed to extend beyond the disc in the form of self-absorption. The presence of a cold SiO layer extending up to some 60 au from the star is shown to be the cause. 5) Line emissions from SO, $^{28}$SiO, CO and HCN molecules are used to probe the CSE up to some 100 au from the star and reveal the presence of two broad back-to-back outflows, the morphology of which is studied in finer detail than in earlier work.

stars: AGB and post-AGB – circumstellar matter – stars: individual: R Dor – radio lines: stars.

# Introduction

In the recent years, the availability of high sensitivity and high angular resolution observations, in particular from the Atacama Large Millimeter/submillimeter Array (ALMA), has shed new light on the mechanisms that govern the mass loss of evolved stars. At the same time it has revealed their complexity and many open questions are still awaiting an answer. Such is particularly the case of oxygen-rich AGB stars, for which the details of the formation of a dust-grain-driven wind are not fully understood. Recently, several such stars have been the object of detailed observations and studies; among these is R Dor, which is the subject of the present article.

R Dor, an oxygen-rich AGB star, is a semi-regular variable of the SRb type, belonging to spectral class M8IIIe, having an initial mass estimated between 1 and 1.5 M$_\odot$ from the value of the $^{17}$O/$^{18}$O ratio (cite: Danilovich2017), a mass-loss rate of $\sim$1.6 10$^{-7}$ M$_\odot$yr$^{-1}$ (cite: Ramstedt2014; Maercker2016) and a temperature of $\sim$3000 K (cite: Dumm1998); it is close to the Sun, at a distance of only $\sim$59 pc (cite: Knapp2003); it displays no technetium in its spectrum (cite: Lebzelter1999) and has a $^{12}$CO/$^{13}$CO abundance ratio of $\sim$10 (cite: Ramstedt2014). It has a dual period of 175 and 332 days (cite: Bedding1998) and its infrared emission above black body between 1 and 40 $\mu$m wavelength shows an enhancement of aluminium oxide and melilite in the dust (cite: Heras2005).

![](figures_rdor2/fig1b.eps)

Recent studies of the morpho-kinematics of the CSE of R Dor are summarized in Figure [1](#fig1), which lists relevant references. The stellar disc and the stellar atmosphere that extends a very few au above it have been probed over a large range of wavelengths. Observations in the millimetre and sub-millimetre range are mostly from the Atacama Large Millimeter-sub-millimeter Array (ALMA) and use continuum or molecular lines emissions that probe preferentially the close neighbourhood of the star, such as the $\Lambda$ doublet OH line (cite: Vlemmings2019; Khouri2019). Evidence is found for short time variability (at month scale), hot spots covering a small fraction of the stellar disc, radial velocities at the 10 km s$^{-1}$ scale, all revealing the impact of shocks associated with pulsations and convective cells. Similar results are obtained from observations in the optical and near-IR ranges, using the Very Large Telescope (VLT) equipped with SPHERE (cite: Khouri2016). Large Doppler velocity wings are observed near the line of sight crossing the centre of the stellar disc, revealing the broad velocity dispersion in the inner layer (cite: Decin2018; Hoai2020). In addition to the evidence for strong inhomogeneity and time variability, the stellar disc radius is measured at a 1.5 to 2 au scale dependent on wavelength; temperatures are estimated in the 2700$\pm$300 K range.

Evidence for the presence of large dust grains, at 0.1 micron scale, within a very few au from the radiosphere is obtained from the study of continuum emission as well as from the observation of polarized light using SPHERE/ZIMPOL on the VLT (cite: Khouri2016). Observations at infrared wavelengths using NACO on VLT (cite: Norris2012) give similar results. This suggests a scenario where the wind is driven by photon scattering on large transparent grains very close to the star, rather than by radiation pressure on silicate grains, which is too small to drive the winds of O-rich AGB stars (cite: Woitke2006). Numerous multi-wavelength studies, using in particular Herschel and ALMA observations, have addressed the question of the composition of the dust and of the nature of its main precursors, generally concluding that aluminium bearing molecules play a dominant role (cite: Heras2005; Decin2018). (cite: Decin2017) study the line profiles of AlO, AlOH and AlCl and suggest the presence of large gas-phase (Al$_2$O$_3$)$_{\rm{n}}$ clusters ($n$$>$34) close to the star. Moreover, (cite: Takigawa2019) have shown that transition alumina containing $\sim$10% of Si rather than amorphous alumina with pure Al$_2$O$_3$ composition is the most plausible source of the dust emission from alumina-rich AGB stars (cite: Karovicova2013). Analyses of molecular line profiles from single dish observations provide a host of useful information on the gas and dust composition of the CSE up to a few 100 au from the star, an important result being the confinement of SiO to shorter distances than CO, interpreted in part as the result of a progressive condensation of SiO gas molecules onto dust grains (cite: Schoier2004). (cite: DeBeck2018) and (cite: Decin2018) perform extensive spectral scans of the envelope, the latter detecting gaseous precursors of dust grains such as SiO, AlO, AlOH, TiO, and TiO$_2$. (cite: Danilovich2016; Danilovich2017; Danilovich2019; Danilovich2020) study sulphur-bearing and water molecules and HCN abundances are measured by (cite: Schoier2013) and by (cite: VandeSande2018).

Significant rotation of the inner CSE has been detected by (cite: Homan2018) and (cite: Vlemmings2018). The former authors use ALMA observations of the $^{28}$SiO($\nu$=1,$J$=8-7) line emission to probe the $\sim$6 to $\sim$25 au radial range with an angular resolution of $\sim$9 au. Their data are well described by a nearly edge-on disc in sub-Keplerian rotation, with a projected rotation velocity of $\sim$6 km s$^{-1}$ at a distance of 12 au. The latter authors use ALMA observations of the SiO($\nu$=3,$J$=5$-$4) and SO$_2$($J_{Ka,Kc}$=16$_{3,13}$$-$16$_{2,14}$) line emissions with an angular resolution of $\sim$2 au to probe the inner layer from the radiosphere up to some 15 au. Their data give no evidence for disc morphology and are well described by solid-body rotation, again with a projection rotation velocity of $\sim$6 km s$^{-1}$ at a distance of 12 au. The difference between the two models is largely the result of the different radial ranges probed by the observations. Both authors argue that the presence of significant rotation is most easily explained by the transfer of angular momentum from a companion to the star. The presence of a blue-shifted feature in the south-eastern quadrant, extending to some 25 au in projected distance from the star and reaching near 20 km s$^{-1}$ in Doppler velocity (cite: Decin2018; Vlemmings2018; Hoai2020) is invoked as suggesting its association with such companion.

Finally, a detailed study of the outer region of the CSE, beyond some 25 au, shows the presence of outflows and of cavities suggesting a complex history of mass ejection (cite: Nhung2019).

The present work studies the emissions of two molecular lines that have been observed by ALMA: $^{29}$SiO ($\nu$=0, $J$=8$-$7) and SO$_2$($\nu$=0, $34_{3,31}$$-$$34_{2,32}$), thereafter simply referred to as $^{29}$SiO and SO$_2$. Parameters of relevance are listed in Table [1](#tab1).

|  Molecule  |             Transition             |  $f$ (GHz)   | $E_{\rm{u}}$ (K) |
|:----------:|:----------------------------------:|:------------:|:----------------:|
| $^{29}$SiO |         $\nu$=0, $J$=8$-$7         | 342.98084800 |      74.08       |
|   SO$_2$   | $\nu$=0, $34_{3,31}$$-$$34_{2,32}$ | 342.76162320 |      581.92      |

: Parameters of the $^{29}$SiO and SO$_2$ emission lines. $E_{\rm{u}}$ is the energy of the upper level of the transition. The frequency $f$ corresponds to a wavelength $\lambda=0.875$ mm and a transition temperature of 16.5 K.

The paper is organized as follows: after a description of observations and data reduction, we present in Section 3 a general picture of the morpho-kinematics of the CSE as obtained from the new results discussed in the present work and taking into account analyses published earlier. Section 4 discusses some properties of the inner layer, accounting for absorption and including rotation, expansion and contributions to the line width. Section 5 addresses questions related to the observed properties of the south-eastern blue-shifted feature. Section 6 explores the CSE to larger distances from the star using other molecular line emissions as probes with the aim of explaining what causes the strong absorption of the SiO lines. A last section summarizes the main results and concludes.

# Observations and data reduction

The data are retrieved from ALMA archives, project 2017.1.00191.S, observed in November 2017 in band 7 with antennas in the C43-9 configuration. The observations were made in two blocks using 44 and respectively 45 antennas. The total time on source was 90 min, 45 min for each block. Visibilities are averaged over 20 s wide time intervals. Baselines span between 100 m and 12 km (Figure [2](#fig2)) and the maximal recoverable scale, evaluated for a wavelength of 0.87 mm and an effective minimal baseline of 300 m, is 0.36 arcsec. We select a frequency interval of 81 channels corresponding to a Doppler velocity interval of 69 km s$^{-1}$, each Doppler velocity bin being 0.854 km s$^{-1}$ wide. The systemic velocity of R Dor (7 km s$^{-1}$) is taken as origin. The data were reduced using standard scripts for continuum emission and two line emissions: $^{29}$SiO($\nu$=0, $J$=8$-$7) and SO$_2$($34_{3,31}$$-$$34_{2,32}$).

![image](figures_rdor2/fig2a-anten-config.eps) ![image](figures_rdor2/fig2b-uvmap.eps) ![image](figures_rdor2/fig2c-baseline-dist.eps) ![image](figures_rdor2/fig2d-brightn-sio-so2.eps)

We calibrated the data using the scripts provided by the ALMA staff. Deconvolution and cleaning were done with natural weighting using two different codes: CASA[^3] and GILDAS[^4]. The line data were processed without continuum subtraction. The beams obtained with CASA and GILDAS (FWHM) were 34$\times$25 mas$^2$ and 41$\times$35 mas$^2$ respectively. In both cases we use pixels of 5$\times$5 mas$^2$. We found that the differences between the results obtained with the two codes are simply explained by the differences in beam size and have negligible impact on the results of our analyses. In what follows we use the GILDAS results as default but we checked their consistency with the CASA results whenever possibly relevant. Brightness distributions (Figure [2](#fig2)) show a noise level (1$\sigma$) of 1.4 mJy beam$^{-1}$ for $^{29}$SiO and 1.1 mJy beam$^{-1}$ for SO$_2$. Additional information is provided in Section 6.1. Channel maps are shown in the Appendix (Figures [\[figA1\]](#figA1) and [\[figA2\]](#figA2)).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | $f$ | Beam | MRS | $N$ | Noise | Date | Time on source |
|  | (GHz) | (mas$^2$) | (au) |  | (mJy beam$^{-1}$) |  |  |
| $^{28}$SiO II | 347.3 | 220$\times$170 | 80 | 38 | 18 | Aug 2015 | 21 mn |
| CO | 345.8 | 180$\times$140 | 80 | 32 | 14 | Sep 2015 | 21 mn |
| HCN | 354.5 | 157$\times$145 | 78 | 34 | 8 | Aug 2015 | 26 mn |
| SO | 251.8 | 154$\times$147 | 136 | 45 | 1.2 | Dec 2017 | 2.7 hr |

![image](figures_rdor2/fig21a-baseline-dist.eps) ![image](figures_rdor2/fig21b-visib-dist.eps) ![image](figures_rdor2/fig21c-visib-dist-fit.eps)

Moreover, in Section 6, we use observations of other molecular lines that have been briefly considered in Paper I: $^{28}$SiO(8$-$7), CO(3$-$2) and HCN(4$-$3). Their emission was detected with a similar beam size but in less favourable observational conditions than for the SO($J_K$=6$_5$$-$5$_4$) line, which was the central subject of Paper I (see Section 6.2). They are from project 2013.1.00166.S observed in summer 2015 in band 7 with an average of 35 antennas in the C34-7 configuration. They include two independent sets of $^{28}$SiO data, hereafter referred to as $^{28}$SiO I and $^{28}$SiO II. Paper I used data reduced by the ALMA staff with continuum subtraction in the $uv$ plane. As the $uv$ coverage for short baselines is poor, we reduced these data anew, using GILDAS with natural weighting and without continuum subtraction. A summary of the main parameters and results is listed in Table [\[tab3\]](#tab3) and illustrated in Figure [3](#fig21), which shows the baseline and brightness distributions obtained in each case. We paid much attention to the impact of the short spacing problem on the quality and reliability of the reduced data. This is illustrated in Figure [3](#fig21)b: the $^{28}$SiO I and $^{28}$SiO II sets, although having similar baseline distributions, display very different visibility distributions. The simple addition of a few short baselines is the cause. Accordingly, we restrict the analysis to distances from the star not exceeding 60 au (1 arcsec). Moreover, we disregard the $^{28}$SiO I set of data as not adding significant information to that obtained from the $^{28}$SiO II set.

We use orthonormal coordinates with the $x$ axis pointing east, the $y$ axis pointing north and the $z$ axis pointing away from Earth. Position angles, $\omega$, are measured counter-clockwise from north.

# Overall picture of the CSE

Figure [4](#fig3) displays the sky maps of the integrated intensity (moment 0) and mean Doppler velocity\<$V_{z}$\> (moment 1) for both the $^{29}$SiO and SO$_2$ lines. While $^{29}$SiO emission is seen to extend up to some 40 au projected distance from the star, SO$_2$ emission is limited to some 12 au. The high excitation energy of the SO$_2$ line prevents it from populating the outer CSE as the temperature can be expected to take a value of $\sim$1100 K at 6 au from the star and to decrease as $r^{-0.65}$ (cite: Decin2018; Homan2018; VandeSande2018). The south-eastern blue stream stands out in the $^{29}$SiO map, more clearly than in previous publications, both because of the better match with the radial range being probed and the better sensitivity and angular resolution. For both lines the north-western half of the \<$V_{z}$\> map is red-shifted, the south-eastern half blue-shifted and the inner layer of the CSE gives evidence for rotation about an axis projecting close to north.

![image](figures_rdor2/fig3a-sio-fmap.eps) ![image](figures_rdor2/fig3b-sio-vmap.eps) ![image](figures_rdor2/fig3c-so2-fmap.eps) ![image](figures_rdor2/fig3d-so2-vmap.eps)

## The inner layer

Figures [5](#fig4) to [8](#fig7) illustrate the main properties of the inner CSE layer, which we present in a set of rings surrounding the star, each 0.05 arcsec (3 au) wide and covering 0.05\<$R$\<0.20 arcsec as illustrated in Figure [5](#fig4). The stellar disc, known to have a radius of $\sim$1.8 au (0.03 arcsec) at mm wavelength (cite: Vlemmings2018), is here represented with a radius of 0.035 arcsec. Figure [6](#fig5) displays the Doppler velocity spectra integrated over it for both $^{29}$SiO and SO$_2$ emissions. They are mostly seen in absorption. The $^{29}$SiO spectrum shows a clear absorption peak occurring in the outer layer where the slow wind has reached a velocity of $\sim$4 km s$^{-1}$. In addition, it also displays absorption by the inner layer, revealing a Doppler velocity distribution extending up to $|V_{z}|$$\sim$20 km s$^{-1}$. Its precise shape is not expected to be significantly affected by rotation but to tell about the radial increase of the expansion velocity as well as about line width; the latter are expected to receive important contributions from shocks associated with pulsations and convective cell ejections (cite: Freytag2017). The red side of the inner layer is seen in emission, the line width of the outer layer being too small to significantly populate Doppler velocities exceeding $\sim$10 km s$^{-1}$, $\sim$15 km s$^{-1}$ above the mean Doppler velocity at such a distance from the star.

The SO$_2$ spectrum is also mostly seen in absorption, displaying a shape qualitatively similar to that of the $^{29}$SiO spectrum, with a narrow absorption peak near $-$4 km s$^{-1}$. However, the scale is very different, both in flux density and in Doppler velocity. The amplitude of the absorption peak is only 18% of the continuum level instead of being total for $^{29}$SiO and the part of the spectrum seen in emission is centred at $\sim$6 km s$^{-1}$ instead of $\sim$13 km s$^{-1}$. A reliable interpretation of the features displayed in Figure [6](#fig5) requires accounting, at least approximately, for optical thickness, which we do in Section 4.

Figures [7](#fig6) and [8](#fig7) display the Doppler velocity spectra averaged in the rings and quadrants defined in Figure [5](#fig4) and covering projected distances from the star between 0.05 and 0.20 arcsec (3 and 12 au). While the $^{29}$SiO spectra show strong absorption by the outer CSE layer, seen as a peak at $\sim$$-$4 km s$^{-1}$, the SO$_2$ spectra are approximately Gaussian and display no absorption feature. Good fits to both $^{29}$SiO and SO$_2$ spectra are accordingly obtained using the simple form $$\begin{align}
  &I=I^*+I_0G(V_{z},V_{z0},\sigma_0)-A G(V_{z},-4.0,1.2) \nonumber \\ 
    \mbox{where\,}& G(V_{z},a,b)=\exp(-\sfrac{1}{2}[V_{z}-a]^2/b^2).\nonumber 
\end{align}$$

The first term, $I^*$, accounts for a small continuum contribution, particularly significant in the inner ring; $I_0$, $V_{z0}$ and $\sigma_0$ define the Gaussian emission and the last term accounts for the absorption by the outer layer. $A$ is set to zero in the SO$_2$ case and is such that the xabsorption be total at $V_{z}=-4.0$ km s$^{-1}$ in the $^{29}$SiO case, namely $A=I^*+I_0G(V_{z},-4.0,1.2)$; the width of the absorption term is fixed with a $\sigma$ of 1.2 km s$^{-1}$.

Tables [\[tabA1\]](#tabA1) and [\[tabA2\]](#tabA2) of the Appendix list the values of the best-fit parameters. For both lines the values of $I^*$ show a same excess of N and NW over S and SE by a factor 2 in the innermost ring, reflecting a small asymmetry of continuum emission.

![](figures_rdor2/fig4-ring-quadrant.eps)

![](figures_rdor2/fig5-spect-ring1b.eps)

If the density of the gas in rotation had a significantly flattened distribution along the equator, in the form of a nearly edge-on disc as suggested by (cite: Homan2018), the intensity projected on the sky plane should display significant ellipticity: its distribution in each ring as a function of position angle $\omega$ should take the form of a $1-\zeta\cos(2\omega)$ term with $\zeta$ providing a measure of the flattening and the distribution reaching its two maxima near the E and W directions and its two minima near the S and N directions. Figure [9](#fig8)a,b displays these distributions; there is no evidence for such a quadripolar term but instead dipole sine waves, of the form $A+B\sin(\omega-\omega_0)$ are seen to give reasonable fits. They reach their maxima in the NW direction with $\omega_0$$\sim$330$^\circ$ and the amplitudes of the oscillation are $\sim$20% of the average emission level. The absence of a quadripolar term sheds doubts on the previously suggested evidence for the presence of an edge-on disc. Figure [9](#fig8)c,d displays the distributions of the mean Doppler velocity; sine waves, as expected for rotation, are seen to give good fits (Table [2](#tab2)). They reach their maxima in the W direction with $\omega_0$$\sim$190$^\circ$ and the amplitude of the oscillations reaches $\sim$4 km s$^{-1}$. From the east-west asymmetry displayed by the values of $V_{z0}$, one can see that the rotation reaches a maximal velocity within the displayed range of $R$, namely below 0.15 arcsec (9 au); beyond the outer ring the blue stream starts contributing significantly to the mean Doppler velocity. A detailed discussion of these observations is presented in Section 4. A clear enhancement of the line width is seen in the inner ring for both $^{29}$SiO and SO$_2$.

+:----------:+:----------------:+:-------:+:-------:+:---------------------:+
| Line       | $R$ range (mas)  | Mean Doppler velocity                     |
+------------+------------------+---------+---------+-----------------------+
|            |                  | $A$     | $B$     | $\omega_0$ ($^\circ$) |
+------------+------------------+---------+---------+-----------------------+
| $^{29}$SiO | 50-100           | 0.6     | 2.7     | 179                   |
|            +------------------+---------+---------+-----------------------+
|            | 100-150          | 1.0     | 3.8     | 191                   |
|            +------------------+---------+---------+-----------------------+
|            | 150-200          | 1.0     | 3.0     | 196                   |
+------------+------------------+---------+---------+-----------------------+
| SO$_2$     | 50-100           | $-$0.2  | 1.8     | 177                   |
|            +------------------+---------+---------+-----------------------+
|            | 100-150          | $-$0.1  | 3.2     | 200                   |
|            +------------------+---------+---------+-----------------------+
|            | 150-200          | $-$0.6  | 2.8     | 215                   |
+------------+------------------+---------+---------+-----------------------+

: Parameters of the sine wave fits of the form $A+B\sin(\omega-\omega_0)$ to the mean Doppler velocity distributions displayed in Figure [9](#fig8). A cut of 3$\sigma$ has been applied to the data; the intensity is integrated and the Doppler velocity averaged over the \|$V_z$\|\<12 km s$^{-1}$ interval.

![image](figures_rdor2/fig6a-spect-ring234-sio.eps) ![image](figures_rdor2/fig6b-spect-ring234-sio.eps)

![image](figures_rdor2/fig7a-spect-ring234-so2.eps) ![image](figures_rdor2/fig7b-spect-ring234-so2.eps)

![image](figures_rdor2/fig8a-fvsphi-sio.eps) ![image](figures_rdor2/fig8b-fvsphi-so2.eps) ![image](figures_rdor2/fig8c-vzvsphi-sio.eps) ![image](figures_rdor2/fig8d-vzvsphi-so2.eps)

![image](figures_rdor2/fig9a-sio-vzphi-r0.04-0.08.eps) ![image](figures_rdor2/fig9b-sio-vzphi-r0.08-0.12.eps) ![image](figures_rdor2/fig9c-sio-vzphi-r0.12-0.16.eps) ![image](figures_rdor2/fig9d-sio-vzphi-r0.16-0.2.eps) ![image](figures_rdor2/fig9e-sio-vzphi-r0.2-0.24.eps) ![image](figures_rdor2/fig9f-sio-vzphi-r0.24-0.28.eps) ![image](figures_rdor2/fig9g-sio-vzphi-r0.28-0.32.eps) ![image](figures_rdor2/fig9h-sio-vzphi-r0.32-0.36.eps)

![image](figures_rdor2/fig9i-sio-vzphi-r0.36-0.4.eps) ![image](figures_rdor2/fig9j-sio-vzphi-r0.4-0.44.eps) ![image](figures_rdor2/fig9k-sio-vzphi-r0.44-0.48.eps) ![image](figures_rdor2/fig9l-sio-vzphi-r0.48-0.52.eps)

![image](figures_rdor2/fig9m-sio-vzphi-r0.52-0.56.eps) ![image](figures_rdor2/fig9n-sio-vzphi-r0.56-0.6.eps)

Figure [10](#fig9) displays the dependence on position angle of the $^{29}$SiO intensity and mean Doppler velocity in successive rings, each 0.04 arcsec (2.4 au) wide. It complements the channel maps displayed in the Appendix and covers not only the inner layer, with the confinement of rotation to projected distances from the star not exceeding 15 au, but also larger distances studied in the following sections, with the appearance of the blue stream at $R$$\sim$0.2 arcsec (12 au) and of the south-western outflow identified earlier in Paper I at $R$$\sim$0.45 arcsec (27 au).

## Absorption over the stellar disc

In the preceding section (Figure [6](#fig5) left), we noted the presence of a nearly total absorption peak at $\sim$ $-$4 km s$^{-1}$ in the $^{29}$SiO data, extending to large values of $R$ as clearly illustrated in Figure [11](#fig10): the absorption is seen to extend well beyond $R$$\sim$15 au, far from the stellar disc (panels a and b). This is also clearly apparent on the channel maps (Figure [\[figA1\]](#figA1)). Comparison between the brightness distributions measured in the $V_{z}$=$-$4 km s$^{-1}$ and $V_{z}$=$+$4 km s$^{-1}$ Doppler velocity channels shows that indeed the former detects only very little signal above noise (panels c and d). Both features, the nearly total absorption over the stellar disc and its extension beyond it, are surprising. We discuss the former below but postpone a discussion of the latter to Section 6 because it requires analyses of line emissions that explore larger distances from the star, up to 100 au or so.

Quantitatively, we can safely place a 3-$\sigma$ upper limit of 4.2 mJy beam$^{-1}$ (10 mJy over the stellar disc) on the brightness measured at maximal absorption, $V_{z}$$\sim$$-$4 km s$^{-1}$, over the stellar disc ($R$\<0.035 arcsec). While local thermal equilibrium (LTE) is not expected to provide a reliable description of the CSE, in particular in the close neighbourhood of the star, its prediction provides a useful reference with which to compare observations. For a given velocity $V_{z}$ and a brightness $I_0$ \[Jy arcsec$^{-2}$\] on the entrance side of a slab of thickness d$z$ \[arcsec\], density $n$ \[molecules cm$^{-3}$\] and temperature $T$ \[K\], the brightness $I$ \[Jy arcsec$^{-2}$\] at the exit side is simply the sum $I=I_0+\varepsilon$ , where $\varepsilon$ is the emission of the slab, when absorption is neglected. The effect of absorption, described by the optical depth $\tau$, is to have instead $$\begin{equation}
  I=I_0e^{-\tau}+\varepsilon(1-e^{-\tau})/\tau=\varepsilon/\tau+(I_0-\varepsilon/\tau)e^{-\tau}
\end{equation}$$ where $\varepsilon$ is given by Relation 2 below: $$\begin{equation}
  \begin{split}
    \varepsilon&=hf/(4\pi \Delta{f})n A_{\rm{ji}}f_{\rm{pop}}{\rm{d}}z \\
    &=0.33\,10^6 N A_{\rm{ji}} f_{\rm{pop}}/\Delta{V},\,f_{\rm{pop}}=(2J + 1)e^{-E_{\rm{u}}/T}/T
  \end{split}
\end{equation}$$ with $J$ and $E_u$ being the angular momentum quantum number and energy of the upper level, $N$ the column density in molecules cm$^{-3}$ arcsec, $A_{\rm{ji}}$ the Einstein coefficient, $\Delta{V}$ the FWHM of the profile measured in km s$^{-1}$\
and where $\tau$ is given by Relation 3 below: $$\begin{equation}
   \begin{split}
     \tau&=c^2/(8\pi f^2\Delta{f})(e^{\Delta{E}/T}-1)n A_{\rm{ji}}f_{\rm{pop}}{\rm{d}}z\\
     &=2.9\,10^7\varepsilon(e^{\Delta{E}/T}-1)/f^3 (f=343\,\mbox{GHz})
     \end{split}
  
\end{equation}$$

When the column density $N$=$n\times$d$z$ increases, $I$ varies from $I_0$ to $\varepsilon/\tau$. In case of absorption, $I_0$\>$\varepsilon/\tau$, $I$ is always larger than $\varepsilon/\tau$, a lower limit to the emission of an optically thick shell. In the present case, where the energy of the transition, $\Delta{E}$=16.4 K, can be expected to be much smaller than the temperature $T$, we can approximate $\varepsilon/\tau$ \[Jy arcsec$^{-2}$\]$=$$T$ \[K\]/11.8. Integrating over the beam area, $\sim$1.6 10$^{-3}$ arcsec$^2$, we obtain a lower limit for the brightness of 1.6 $T$/11.8 mJy beam$^{-1}$ to be compared with the 3-$\sigma$ limit of 4.2 mJy beam$^{-1}$, meaning an upper limit of 11.8$\times$4.2/1.6$\sim$30 K on $T$. Such a low value seems unlikelyat such short distance from the star. The assumptions made are very crude but the fact remains that however large absorption may be, the outer part of the layer cannot be prevented from shining. This result is independent from the value of $\varepsilon$, namely of the column density. We note that in the case of Mira A (cite: Wong2016) the brightness measured at maximal absorption exceeds 20% of the continuum level, compared with \<3% in the present case.

The above argument applies in particular to the outer layer, which is expected to host less turbulence, shocks and condensing dust than the inner layer does and where Doppler velocities can be assumed to stay within the interval $-$10\<$V_{z}$\<0 km s$^{-1}$. Such assumption implies that the absorption observed outside this interval is confined to the inner layer. We accordingly define three values of the flux density over the stellar disc at $V_{z}$$\sim$$-$4 km s$^{-1}$: inflowing, $I_{\rm{in}}$$\sim$0.34 Jy, intermediate, $I_{\rm{mid}}$$\sim$0.17 Jy measured as the mean between the values of the brightness measured at $V_{z}$=$-$10 km s$^{-1}$ and $V_{z}$=0 (see Figure [6](#fig5)-left) and outflowing, $I_{\rm{out}}$\<0.01 Jy. At $V_{z}$$\sim$ $-$4 km s$^{-1}$ the flux density over the stellar disc decreases therefore from 0.34 Jy near the star to 0.17 Jy outside the inner layer and \<0.01 Jy outside the outer layer.

![image](figures_rdor2/fig10a-sio-pvmap-vz-rxy.eps) ![image](figures_rdor2/fig10b-sio-spect-rxy.25-.5.eps) ![image](figures_rdor2/fig10c-sio-abs-ch4m.eps) ![image](figures_rdor2/fig10d-sio-abs-ch4p.eps)

We first calculate $\varepsilon$ and $\tau$ at a temperature $T$$\sim$270 K using Relations 2 and 3 for $^{29}$SiO. We use a column density $N$ \[molecules cm$^{-3}$ arcsec\]=0.7 obtained by integration from $r$=0.8 to 1.0 arcsec for a $^{28}$SiO/H$_2$ abundance of 5.5 10$^{-5}$ (cite: VandeSande2018), an isotopic ratio $^{29}$Si/$^{28}$Si=8% (cite: DeBeck2018) and an H$_2$ density of the form 1.6 10$^{7}$ $(r/0.2)^{-2}$ \[molecules cm$^{-3}$\], meaning a mass-loss rate of $\sim$1.6 10$^{-7}$ M$_\odot$ yr$^{-1}$. Writing $J$=8, $E_{\rm{u}}$=74 K, $A_{\rm{ji}}$=2.1 10$^{-3}$ s$^{-1}$, we obtain $\varepsilon$=8.2 10$^3e^{-74/T}/(T\Delta{V})$ and $\tau$=9.7 10$^4e^{-74/T}/(T^2\Delta{V})$. Namely, at $T$=270 K, $\varepsilon$=8.2 Jy arcsec$^{-2}$ and $\tau$=0.36 for $\Delta{V}$=2.8 km s$^{-1}$: the self-absorbed emission is $\sim$27 mJy over the stellar disc, nearly 3 times the upper limit placed on the observed emission. Repeating the same calculation for 0.2\<$r$\<0.4 arcsec gives $\varepsilon$=46 Jy arcsec$^{-2}$ and $\tau$=1.0, respectively, the self-absorbed emission being $\sim$117 mJy over the stellar disc. For the whole range, 0.2\<$r$\<1 arcsec, and $I_{\rm{mid}}$=0.17 Jy we find $I_{\rm{out}}$=152 mJy over the stellar disc, over an order of magnitude above the observed upper limit of 10 mJy.

We can repeat the above argument in the case of SO$_2$ emission. The abundance relative to H$_2$ is now of the form 5 10$^{-6}\exp[-(r/1.78)^2]$ (cite: Danilovich2016; Danilovich2020), $E_{\rm{u}}$=581.92 K and $A_{\rm{ji}}$=3.45 10$^{-4}$ s$^{-1}$, but the relation $\tau$$\sim$11.8$\varepsilon/T$ still applies. We estimate $I_{\rm{mid}}$=0.325 Jy and $I_{\rm{out}}$=0.27 Jy. For the whole range, 0.2\<$r$\<1 arcsec, we find $I_{\rm{out}}$=0.32 Jy.

In summary, for $^{29}$SiO, below $\sim$12 au and at $V_z$$\sim$$-$4 km s$^{-1}$, the inner layer absorbs $\sim$40% of the continuum emission ($\sim$60% at $V_z$=0) and is expected to host shocks and turbulence. We study it in Section 4. For SO$_2$, at $V_z$$\sim$$-$4 km s$^{-1}$, the inner layer absorbs only 2% of the continuum emission and the outer layer absorbs 17% of the inner layer emission. Beyond $\sim$12 au and at $V_z$$\sim$$-$4 km s$^{-1}$, we detect no emission for $^{29}$SiO, implying that the outer layer not only absorbs completely the emission of the inner layer but also its own emission, which we discuss in Section 6. We have shown that a simple LTE model cannot produce such a result if the temperature takes values as expected in the literature and predicts an emission an order of magnitude larger than observed. This result suggests that such absorption is more likely to happen at large radii, say above 40 au, where the temperature is expected to be closer to 200 K (cite: VandeSande2018) and where an enhancement of emission has been observed (Paper I). This is further discussed in Section 6.

## The blue stream

The blue stream is seen clearly on the channel maps of both $^{29}$SiO and SO$_2$ emissions. It covers projected distances from the star reaching $\sim$30 au for the former (Figure [\[figA1\]](#figA1)) and $\sim$20 au for the latter (Figure [\[figA2\]](#figA2)) at a mean position angle of $\sim$140$^\circ$. In order to define it precisely we measure for each line its position in each frequency interval separately and fit straight lines through the points. Figure [12](#fig11) displays intensity maps integrated over relevant Doppler velocity intervals. Panel c shows the dependence of the stream Doppler velocity on $R$ defined as described above, for each frequency interval separately. To a good approximation it displays a constant projected acceleration of 39.2$\pm$0.5 km s$^{-1}$ arcsec$^{-1}$. A priori, there is no reason for such projected linearity: it may be destroyed by de-projection and, even if it were not, it would require that the force driving the wind is approximately the sum of a constant term and an $r^{-2}$ term, the latter compensating gravity. The angle made by the stream with the line of sight is unknown. The SO$_2$ channel maps show that the stream seems to maintain its identity down to Doppler velocities of $\sim$$-$3 km s$^{-1}$, at which point $R$$\sim$9 au, but the constant acceleration law seems to be no longer obeyed. A natural explanation is that the stream is born within the slow wind at a space distance from the star of some 12 au, in a region where rotation has essentially faded away. A mechanism such as what (cite: Takigawa2017) call “local acceleration”, caused by locally enhanced density of aluminium-rich dust, would then be at stake. In such a picture, the stream would make a significant but not too large angle with the line of sight, say between 30$^\circ$ and 45$^\circ$. Qualitatively, this is the most natural and simple interpretation that comes to mind; however, we cannot exclude a configuration where the stream would fly at high velocity near the plane of the sky, not to mention configurations for which the linearity observed in projection is no longer obeyed once de-projected in space.

![image](figures_rdor2/fig11a-bluestream-fmap-sio.eps) ![image](figures_rdor2/fig11b-bluestream-fmap-so2.eps) ![image](figures_rdor2/fig11c-bluestream-vzr.eps)

![image](figures_rdor2/fig12a-sio-dff-map.eps) ![image](figures_rdor2/fig12b-sio-dvz-map.eps) ![image](figures_rdor2/fig12c-sio-pvmap-140.eps)

Figures [12](#fig11) and [13](#fig12) show that the stream nearly points to the star; more precisely it points 1.5$\pm$1.5 au south-west of the star. Panel c of Figure [13](#fig12) displays a Position-Velocity (PV) diagram along a $\pm$3 au wide slit at position angle 140$^\circ$. An enhancement of intensity is seen back to back to the stream, but at much smaller Doppler velocities. It is shown by a green arrow at position angle 320$^\circ$ in the panels of Figure [10](#fig9) covering values of $R$ between 0.1 and 0.2 arcsec.

![image](figures_rdor2/fig13a-sio-spect-end-blue.eps) ![image](figures_rdor2/fig13b-sio-spect-end-red.eps) ![image](figures_rdor2/fig13c-sio-spect-end-all.eps) ![image](figures_rdor2/fig13d-so2-spect-end-all.eps)

![image](figures_rdor2/fig14a-sio-pvmap-vzphi.eps) ![image](figures_rdor2/fig14b-sio-vzphi-fit.eps)

Evidence for important high $V_z$ components in the vicinity of the line of sight crossing the centre of the stellar disc is shown in Figure [14](#fig13). It displays, for both $^{29}$SiO and SO$_2$ emissions, the high velocity wings of the Doppler velocity spectrum integrated over small circles around the centre of the star ($R$\<0.1 and \<0.2 arcsec), small enough to receive only a small contribution from the blue stream. A Gaussian line centred at the origin and having $\sigma$$\sim$5.5 km s$^{-1}$ is shown as reference in the figure. The SO$_2$ line width is $\sim$15% smaller than the $^{29}$SiO line width, probably the result of the steeper $r$ dependence of the flux density. The clear separation observed here between the blue stream and the high Doppler velocity wings underlines their different nature, the latter being the simple result of line broadening in the inner layer.

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

[^3]: http//casa.nrao.edu

[^4]: https://www.iram.fr/IRAMFR/GILDAS

# The inner layer, rotation and line width

As discussed in Section 3.2, the $^{29}$SiO emission of the star and of the inner CSE layer, $R$\<$\sim$12 au, seems to be seen across a self-absorbing layer moving toward us with a velocity of $\sim$4 km s$^{-1}$, causing nearly total absorption over its range of Doppler velocities. In order to study the emission of the inner layer, we simply ignore this Doppler velocity interval. Figure [\[fig14\]](#fig14) shows a PV map, $V_z$ vs $\omega$, in the ring 0.075\<$R$\<0.175 arcsec. In each $\omega$ bin, the brightness in the $V_z$ absorption interval has been interpolated linearly between its values taken just above and just below. The result is essentially the same as if one keeps the absorbed interval untouched: a fit of the form $A+B\sin(\omega-\omega_0)$ gives $B$=3.6 km s$^{-1}$ and $\omega_0$=191$^\circ$ instead of 3.6 km s$^{-1}$ and 190$^\circ$. However, the constant term is now smaller, 0.5 instead of 0.9 km s$^{-1}$. This shows the robustness of the result in spite of the very strong absorption. We retain a value of 10$\pm$5$^\circ$ for the projection angle of the rotation axis, in agreement with the value of 7$\pm$6$^\circ$ obtained by (cite: Vlemmings2018).

![image](figures_rdor2/fig15a-sio-spect-fit-ring1.eps) ![image](figures_rdor2/fig15b-sio-spect-fit-ring2.eps) ![image](figures_rdor2/fig15c-sio-spect-fit-ring3.eps) ![image](figures_rdor2/fig15d-sio-spect-fit-ring4.eps)

When averaged over a ring, rotation contributes to broadening the absorption line but does not cause any shift of its mean value. The observed profile should therefore reveal by how much the wind is accelerated, if at all, in the inner layer. We study this with the help of a crude model of the morpho-kinematics of the $^{29}$SiO emission of the inner layer. Rotation is assumed to proceed about an axis projecting 10$^\circ$ east of north with a velocity depending on $r$ \[arcsec\] as $V_{\rm{rot}}$ \[km s$^{-1}$\]=64$r(1-4r)$ and $V_{\rm{rot}}$=0 beyond $r$=0.25 arcsec.The inclination of the rotation axis with respect to the plane of the sky is taken to be 20$^\circ$. Temperature and density are assumed to depend on distance as $r^{-0.65}$ and $r^{-2}$ respectively, their values at $r$=0.1 arcsec (6 au), $T_0$ and $n_0$ respectively, being varied to optimize the fit. Line broadening is described as a Gaussian of dispersion $\sigma_{\rm{turb}}$=$V_{\rm{turb}}\exp[-\sfrac{1}{2}(r-r_{\rm{turb}})^2/\Delta{r_{\rm{turb}}}^2]$ having itself a Gaussian radial dependence. This line broadening is probably of a complex nature, including shocks from pulsations and convective cell ejections. Its modelling as Gaussian fluctuations is a grossly oversimplified approximation. The best fit, illustrated in Figure [1](#fig15), gives $n_0=130^{+90}_{-40}$ molecules cm$^{-3}$ and $T_0$=$450^{+130}_{-90}$ K: the density is $(40^{+30}_{-10})$% and the temperature $(40^{+12}_{-8})$% of the values quoted by (cite: VandeSande2018). The best fit does not allow for significant expansion below $r$$\sim$10 au and requires a turbulence confined to the $r$\<12 au region with $V_{\rm{turb}}=4.3\pm1.1$ km s$^{-1}$. The assumptions made in the model are qualitatively reasonable but quantitatively somewhat arbitrary and we cannot expect the result to give more than a reference with which to compare the observations. Yet, we can reliably retain that most of the line broadening occurs in the inner layer while most of the radial expansion occurs beyond it. The value obtained for $T_0$, about half the expected value, is probably too low to be blamed uniquely on the crudeness of the model and is likely to have some reality, suggesting a steeper radial dependence than assumed in the model.

# The blue stream: a possible companion?

Several authors (cite: Homan2018; Decin2018; Vlemmings2018) have entertained the idea that the blue stream might be associated with a low mass companion, probably an evaporating planet. An argument is that the observed star rotation is much too rapid to be a remnant of the rotation of the Main Sequence star and is likely to have received its angular momentum from interaction with a companion. However, such a companion may very well have already been engulfed by the expanding star and have no relation with the observed blue stream, significantly weakening the argument. (cite: Vlemmings2018) locate the companion within 8 au and (cite: Homan2018) at $\sim$12 au from the star. The present data show that, in projection on the plane of the sky, gas flows radially from $R_1$$\sim$10 au to $R_2$$\sim$30 au with mean Doppler velocity increasing from \|$V_{z1}$\|$\sim$7 km s$^{-1}$ to \|$V_{z2}$\|$\sim$18 km s$^{-1}$. Calling $\theta_{\rm{bs}}$ the angle between the stream axis and the line of sight, this corresponds in space to a distance $(R_2-R_1)/\sin\theta_{\rm{bs}}$ covered at mean velocity $\sfrac{1}{2}(|V_{z1}|+|V_{z2}|)/\cos\theta_{\rm{bs}}$ in a time $t$=$2(R_2-R_1)/[(|V_{z1}|+|V_{z2}|)\tan\theta_{\rm{bs}}]$$\sim$$6.8/\tan\theta_{\rm{bs}}$ yr. During this time, the companion, assumed to be on a circular orbit of radius $R_1/\sin\theta_{\rm{bs}}$, covers a distance $d$=$tV_{\rm{orb}}$ where $V_{\rm{orb}}$\[au yr$^{-1}$\]=$2\pi\sqrt{(M/\mbox{M$_\odot$})\sin\theta_{\rm{bs}}/R_1[\mbox{au}]}$ is the orbital velocity; for a star mass $M$=1.4 M$_\odot$ (cite: Danilovich2017; DeBeck2018), $d$=$14.6\cos\theta_{\rm{bs}}/\sqrt{\sin\theta_{\rm{bs}}}$ au. As the stream points to the star within $\sim$1.5 au, this implies that $\cos\theta_{\rm{bs}}/\sqrt{\sin\theta_{\rm{bs}}}$ must not exceed $\sim$0.1 or $\theta_{\rm{bs}}$\>84$^\circ$. If it were to exceed it the space velocity would exceed 100 km s$^{-1}$at $R_2$.

These simple considerations illustrate the difficulty to describe the blue stream as gas trailing behind a planetary companion: if the stream flows close to the plane of the sky, one needs a mechanism that boosts the gas velocity radially at a level well above what can be expected from standard acceleration processes; if the stream flows close to the line of sight, the time it takes to cover the distance over which it is detected allows for the companion to cover a distance much larger than acceptable from the good pointing of the stream to the star. This conclusion rests on making a large number of simplifying assumptions. As underlined by (cite: Homan2018), such assumptions may not be obeyed in reality. However, to invalidate the conclusion requires major changes to the picture, not simple numerical adjustments within reasonable limits.

![image](figures_rdor2/fig16a.eps) ![image](figures_rdor2/fig16b.eps) ![image](figures_rdor2/fig16c-model-thetabs-all.eps)

Figure [2](#fig16) illustrates the geometry. The left panel is drawn in the plane of position angle $\omega_{\rm{bs}}$=140$^\circ$ containing the line of sight and the axis of the blue stream. It is meant to illustrate the dependence of the geometry on the unknown value of $\theta_{\rm{bs}}$. It is drawn in a configuration where $\theta_{\rm{bs}}$ is small and the blue stream flies close to the line of sight, implying that it starts beyond the inner layer. If instead $\theta_{\rm{bs}}$ were large, the blue stream would fly close to the plane of the sky and would start at the outer edge of the inner layer. As the companion projects at a position angle $\omega_{\rm{bs}}$=140$^\circ$, the inclination $\theta_R$ of the orbital axis with respect to the plane of the sky is related to $\theta_{\rm{bs}}$ by the relation $\sin\theta_R$=$\cos(\omega_{\rm{bs}}-\omega_R)\sin\theta_{\rm{bs}}/\sqrt{1-\sin^2\theta_{\rm{bs}}\sin^2(\omega_{\rm{bs}}-\omega_R)}$, where $\omega_R$ is the position angle of the projection of the orbital axis on the plane of the sky. Assuming that the orbital axis is at the same time the rotation axis of the volume of gas we retain a value $\omega_R$=10$^\circ$$\pm$5$^\circ$ east of north, from the results listed in Table [\[tab2\]](#tab2) and those obtained by (cite: Vlemmings2018). To a good approximation, the relation reduces to $\theta_{\rm{bs}}$=1.5$\theta_R$ implying $\theta_R$$\sim$20$^\circ$ for $\theta_{\rm{bs}}$=30$^\circ$, the same value as inferred by (cite: Homan2018) for the rotation axis of the gas volume. Figure [2](#fig16) (right) shows the dependence on $\theta_{\rm{bs}}$, at the assumed location of the companion, of the temperature $T$\[K\]$\sim$820$\sqrt{\sin\theta_{\rm{bs}}}$, the escape velocity $V_{\rm{esc}}$ \[km s$^{-1}$\]=14$\sqrt{\sin\theta_{\rm{bs}}}$, the distance $d$\[au\]=$14.6\cos\theta_{\rm{bs}}/\sqrt{\sin\theta_{\rm{bs}}}$ and the maximal gas velocity (at $R_2$=30 au), $V_{\rm{max}}$\[km s$^{-1}$\]=18$/\cos\theta_{\rm{bs}}$.

Figure [2](#fig16) invites another comment concerning the radial evolution of the Doppler velocity along the blue stream. When looking only at the projection on the sky plane apparent continuity is observed (Figure [\[fig12\]](#fig12)b) between the central rotation and the stream, suggesting that the acceleration of the stream might be somewhat boosted by the rotation. However, the channel maps do not display such apparent continuity. Indeed, when looking in space, one cannot make sense of such a statement: if the stream flows close to the line of sight, it is born well above the plane of the sky: the rotation velocity is parallel to the line of sight in the plane of the sky but is negligibly small where the stream is born; if it flows close to the plane of the sky, it needs a boost perpendicular to the line of sight and not along it as rotation provides.

# The CSE as probed at larger distances from the star

The study of the absorption of $^{29}$SiO emission over the stellar disc presented in Section 3.2 has suggested that R Dor is seen across a self-absorbing optically thick layer moving away from the star toward us with a velocity of some 4 km s$^{-1}$ and covering a region of the plane of the sky much larger than the stellar disc. While a similar effect seems to be present in the CSE of W Hya (cite: Takigawa2017), it has not been explicitly discussed in the literature. The present section addresses this issue in the broader context of a description of the morpho-kinematics of the CSE at distances from the star covering up to some 100 au, where such absorption is expected to take place. Section 6.1 presents a critical discussion of possible instrumental effects, in particular related to the short spacing problem (cite: Gueth1997), which might mimic the extension beyond the stellar disc of the absorption of the $^{29}$SiO emission. The following sections probe the CSE using emissions of the SO($J_K$=$6_5-5_4$) line, together with three other molecular lines: $^{28}$SiO, CO and HCN. The emission of the SO line was studied in Paper I; Section 6.2 recalls the main results and presents a new and detailed description of the space morphology. The emission of the other lines was studied in much less detail in Paper I and Section 6.3 presents a qualitative picture of the morpho-kinematics as obtained from these multiline observations; Section 6.4 addresses the specific issue of absorption.

## Absorption of the $^{29}$SiO line emission beyond the stellar disc

![image](figures_rdor2/fig17a-model-abs.eps) ![image](figures_rdor2/fig17b-visib-bl.eps) ![image](figures_rdor2/fig17c-fluxden-rxy.eps)

Figure [\[fig10\]](#fig10) has given evidence for strong absorption of the $^{29}$SiO line emission to persist well beyond the stellar disc. In order to get an idea of which absorption to expect from the antenna configuration used for the observations, we construct a very crude model that reproduces qualitatively the main characteristics of the $^{29}$SiO morpho-kinematics. It assumes the isotropy of the brightness in the plane of the sky and considers three different models, each defined by a simple radial dependence of the brightness as illustrated in Figure [3](#fig17)a. It considers three different brightness distributions on the plane of the sky. The first model, case 1, shown in blue, represents continuum emission and is described as a uniform brightness of 1 Jy/pixel over the stellar disc ($R$\<0.04 arcsec). The second model, case 2, in red, shows a disc of uniform brightness, arbitrarily set to 0.1 Jy/pixel, and having a radius of 0.3 arcsec, meant to represent the emission of the CSE. Emission is completely absorbed over the stellar disc; this case is meant to mimic the real situation in the frequency channel corresponding to a Doppler velocity of $-$4 km s$^{-1}$. The third model, case 3, shown as a thick black line, represents instead the situation in the frequency channel corresponding to $V_z$=$+$4 km s$^{-1}$, expected to detect the same emission as the $-$4 km s$^{-1}$ channel but without absorption over the stellar disc: emission is not absorbed and is described by a uniform brightness of 1 Jy/pixel over the stellar disc. The emission in case 3 is the sum of that in cases 1 and 2. For each of the three cases, we produce[^3] visibilities $U$ corresponding to the actual antenna configuration illustrated in Figure [\[fig2\]](#fig2). Figure [3](#fig17)b displays the baseline dependence of the visibility amplitude for each of the three cases. Case 1, meant to represent continuum, covers long baselines, up to $\sim$1000 m, with small visibilities (in spite of its larger brightness than the gas, by a factor 10, it covers a much smaller area, by a factor 130). Case 2, meant to represent $V_z$=$-$4 km s$^{-1}$, shows that the gas emission is indeed absorbed, but only over a small distance from the star, not exceeding $\sim$0.1 arcsec, in strong contrast with what we observe in the real case (Figure [4](#fig18)). Case 3, meant to represent $V_z$=$+$4 km s$^{-1}$, shows the gas emission that covers short baselines, up to $\sim$500 m, but with large visibilities. In summary, in spite of the poor $uv$ coverage at short baselines, we expect absorption to extend only slightly beyond the stellar disc, well below the maximal recoverable scale, in sharp contrast with observation.

![image](figures_rdor2/fig18a-visib-dist.eps) ![image](figures_rdor2/fig18b-visib-bl.eps)

Turning now to the actual $^{29}$SiO observations, we select the two frequency intervals covering $V_z$=$\pm$4 km s$^{-1}$ and define a third interval, meant to measure continuum emission, made of two sets of 9 frequency channels each (7.7 km s$^{-1}$) at the beginning and end of the frequency band. The left panel of Figure [4](#fig18) displays the distributions of the measured visibility amplitude, \|$U$\|, averaged over these intervals. The noise is well described by a form \|$U$\|$\exp(-\sfrac{1}{2}|$$U$$|^2/\sigma^2)$, meaning a Gaussian distribution in each of Re($U$) and Im($U$) with a common rms value, $\sigma$, measured to be 0.62 Jy. While the measured visibilities are large in the gas layer surrounding the star (black), they are much smaller and closer to the noise for the continuum (blue) and the maximal absorption channel (red). The right panel of Figure [4](#fig18) shows the dependence on baseline of the visibility for each frequency interval separately, again normalised to the baseline distribution of Figure [\[fig2\]](#fig2)c. Continuum emission (blue), corresponding to the stellar disc, covers the broader range of baselines, extending up to $\sim$2.3 km; gas emission (black), corresponding to the gas envelope around the star, covers up to baselines of $\sim$500 m. Finally, the red histogram is expected to stay at noise level down to baselines of $\sim$500 m, the disc region being nearly completely absorbed, and it does so. However, toward lower baselines, it is expected to rise near the level of the black histogram, as happens for case 2 in Figure [3](#fig17)b, but in fact it reaches much lower a level: this shows that the effect is already present at the level of the measured visibilities.

The short spacing problem is precisely the same for the $V_z$=$+$4 km s$^{-1}$ and $V_z$=$-$4 km s$^{-1}$ cases; the noise is the same; the calibration uses only observations made for this purpose and is also the same for the two channels. The global blank out of the $V_z$=$-$4 km s$^{-1}$ observations is therefore shown to be present at raw data level already and we must conclude that it is real and not the result of some instrumental artefact.

## Overall picture of the morpho-kinematics as seen from SO emission

Paper I has presented a detailed study of the morpho-kinematics of the CSE using ALMA observations of the emission of the SO($J_K$=6$_5$$-$5$_4$) line of which channel maps were displayed in the supplementary material. These are from project 2017.1.00824.S observed in December 2017 in band 6 with an average of 45 antennas. Distances from the star reaching up to some $\sim$120 au are probed with a circular beam of 9 au FWHM. Evidence is obtained for a slow radial wind with Doppler velocities reaching up to $\sim$6 km s$^{-1}$, displaying significant anisotropy and inhomogeneity.

The complexity of the morphology of the CSE makes it difficult to draw simple 2-D representations of the data cube. We find that PV maps displaying the brightness in the Doppler velocity ($V_z$) vs position angle ($\omega$) or vs projected distance ($R$) planes, are particularly convenient for this purpose. They have the advantage that a wind blowing at constant velocity $V$ in a small solid angle appears as a small clump in the former and as a stretch of uniform density in the latter. Moreover, for an isotropic wind of constant and uniform radial velocity $V$, the angle $\varphi$ of the flow with the line of sight is simply obtained from the relation $V_z$=$V\cos\varphi$, providing an evaluation of $z$=$R/\tan\varphi$ and therefore of the morpho-kinematics in space. More generally, space reconstruction can be done as long as the dependence of $V$ on $r$ is known; in particular for an acceleration law of the form $V$=$V_{\rm{term}}r/(r+r_{\sfrac{1}{2}})$, tending asymptotically to the terminal velocity $V_{\rm{term}}$ when $r$ tends to infinity and reaching the value $\sfrac{1}{2}V_{\rm{term}}$ for $r$=$r_{\sfrac{1}{2}}$, one has $r$=$[\alpha^2r_{\sfrac{1}{2}}+\sqrt{\alpha^4r_{\sfrac{1}{2}}^2+(1-\alpha^2)(R^2+\alpha^2r_{\sfrac{1}{2}}^2)}]/(1-\alpha^2)$ with $\alpha$=$V_z/V$.

![](figures_rdor2/fig19.eps)

The quality of the SO observations is excellent and the CSE is optically thin enough to suffer no significant absorption. They show two nearly back-to-back outflows, one (NEB) covering the north-eastern blue-shifted octant of the data cube and the other (SWR) the south-western red-shifted octant. Figure [5](#fig19) shows the geometry. Figure [6](#fig20)a displays the intensity in the $V_z$ vs $\omega$ plane for 12 au\<$R$\<60 au. A very crude model of two back-to-back outflows is used to evaluate the orientation of the common outflow axis: it projects on the plane of the sky 60$^\circ$$\pm$5$^\circ$ east of north. Both SWR and NEB have a multicore structure. We use two planes on which to project the emission of the outflows. They are perpendicular to each other and cross on the outflow axis (Figure [5](#fig19)). Plane P1 is perpendicular to the plane of the sky and projects on it at 60$^\circ$ position angle. Plane P2 crosses the plane of the sky at 60$^\circ$+90$^\circ$=150$^\circ$ position angle. The angle $\varphi$ of the outflow axis with the plane of the sky depends on the acceleration of the flow. Using the law introduced in the preceding paragraph with $V_{\rm{term}}$=7 km s$^{-1}$ and $r_{\sfrac{1}{2}}$=30 au (0.5 arcsec) the map of the intensity projected on P1, displayed in panel b of Figure [6](#fig20), gives $\varphi$$\sim$45$^\circ$. The value of $r_{\sfrac{1}{2}}$ can be chosen anywhere between 0.25 and 0.75 arcsec (15 and 45 au) without $\varphi$ changing by more than $\pm$5$^\circ$. Panel c of the figure shows the map of the intensity projected on P2.

![image](figures_rdor2/fig20a-so-pvmap-vzphi.eps) ![image](figures_rdor2/fig20b-so-outflw-p1.eps) ![image](figures_rdor2/fig20c-so-outflw-p2.eps) ![image](figures_rdor2/fig20d-so-pvmap-vzr.eps)

When looking at the radial distribution of the intensity, significant inhomogeneity is observed. Figure [6](#fig20)d displays the distribution of the intensity in the $V_z$ vs $R$ plane, integrated over all position angles. It was shown in Paper I to reveal the presence of a ring cavity surrounding the star, approximately perpendicular to the outflow axis, seen as a hole of emission at $R$$\sim$0.5 arcsec. A second hole at $R$$\sim$1.1 arcsec is also visible. This was interpreted in Paper I as evidence for episodes of enhanced mass loss. However, the ring cavity receives important contribution from the waist separating the outflows: understanding its precise nature requires additional observations.

## Overall picture of the morpho-kinematics from a comparison between SO, $^{28}$SiO, CO and HCN line emissions

In the present section we use the emission of lines $^{28}$SiO(8$-$7), CO(3$-$2) and HCN(4$-$3) to probe the CSE. They were previously considered in Paper I and have been briefly introduced in Section 2. Figures [7](#fig22) and [8](#fig23) describe the main results. Doppler velocity spectra measured over the stellar disc (Figure [7](#fig22)a) show nearly total absorption of the $^{28}$SiO line at $V_z$$\sim$$-$4 km s$^{-1}$, confirming the results obtained for the $^{29}$SiO isotopologue when accounting for the much broader beam (FWHM$\sim$7 stellar radii). They also show significant but much smaller absorption of the HCN and CO lines. The CO line emission is absorbed at lower Doppler velocity than the SiO line, nearly $-$6 km s$^{-1}$ instead of $-$4 km s$^{-1}$: this is probably the result of its much larger radial extension; it suggests that the wind acceleration from 4 km s$^{-1}$ to the terminal velocity of $\sim$6 km s$^{-1}$ is significant in a region where the density ratio between SiO and CO molecules is declining, namely beyond $r$$\sim$1 arcsec but the quality of the data does not allow for a more quantitative statement. Figure [7](#fig22)b displays Doppler velocity spectra outside the stellar disc where some absorption of the $^{28}$SiO line emission is seen to persist. Figure [7](#fig22)c,d displays, for the blue and red hemispheres separately, the radial distributions of the flux density integrated over Doppler velocity using the radial dependence of the velocity introduced in Section 6.2 for SO emission ($r_{\sfrac{1}{2}}$=0.5 arcsec). If the CSE were optically thin, its emission would be simply described by the $\varepsilon$ parameter. Using abundances relative to H$_2$ given by (cite: VandeSande2018) and (cite: Danilovich2016) and an H$_2$ density corresponding to a mass-loss rate of $\sim$1.6 10$^{-7}$ M$_\odot$ year$^{-1}$ as was done in Section 3.2, we calculate its value (Table [\[tab4\]](#tab4)) for a temperature of 150 K and a distance of 1 arcsec from the star and obtain the emission $F_r$ of a shell of 1 arcsec radius with which to compare the observations displayed in Figure [7](#fig22)c,d. We find that the SO and HCN observed emissions are well predicted and the CO emission some 30% below prediction, which suggests that absorption is small for these lines (but in the blue hemisphere, HCN seems to suffer significant absorption). However, the observed $^{28}$SiO emission is considerably smaller, suggesting very strong self-absorption.

![image](figures_rdor2/fig22a-spect-all-r.3.eps) ![image](figures_rdor2/fig22b-spect-all-r.3-1.eps) ![image](figures_rdor2/fig22c-outflw-rdist-blue.eps) ![image](figures_rdor2/fig22d-outflw-rdist-red.eps)

![image](figures_rdor2/fig23a-sio-pvmap-vzphi.eps) ![image](figures_rdor2/fig23b-sio-outflw-p1.eps) ![image](figures_rdor2/fig23c-sio-outflw-p2.eps) ![image](figures_rdor2/fig23d-sio-pvmap-vzr.eps)

![image](figures_rdor2/fig23e-co-pvmap-vzphi.eps) ![image](figures_rdor2/fig23f-co-outflw-p1.eps) ![image](figures_rdor2/fig23g-co-outflw-p2.eps) ![image](figures_rdor2/fig23h-co-pvmap-vzr.eps)

![image](figures_rdor2/fig23i-hcn-pvmap-vzphi.eps) ![image](figures_rdor2/fig23j-hcn-outflw-p1.eps) ![image](figures_rdor2/fig23k-hcn-outflw-p2.eps) ![image](figures_rdor2/fig23l-hcn-pvmap-vzr.eps)

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

[^3]: Using SIMOBSERVE in CASA, http//casa.nrao.edu

|           Molecule            | $^{28}$SiO |  CO   |  HCN  |  SO   |
|:-----------------------------:|:----------:|:-----:|:-----:|:-----:|
|       $A$ \[10$^{-4}$\]       |    22.0    | 0.025 | 20.5  | 1.93  |
|            $2J+1$             |     17     |   7   |   9   |  13   |
|        $k$ \[10$^5$\]         |    3.3     |  9.2  |  6.9  | 0.97  |
|          $f$ \[GHz\]          |   347.3    | 345.8 | 354.5 | 251.8 |
|       $\lambda$ \[mm\]        |   0.864    | 0.867 | 0.846 | 1.191 |
|       $\Delta{E}$\[K\]        |    16.7    | 16.7  | 17.1  | 12.1  |
|          $E_u$ \[K\]          |     75     |  33   |  43   |  51   |
| $n/n(\rm{H}_2$) \[10$^{-4}$\] |    0.6     |   2   | 0.005 | 0.07  |
|       $r_0$ \[arcsec\]        |    1.5     |  10   |   0   |   0   |
|     $\sigma_0$ \[arcsec\]     |    1.1     |   5   |  1.6  |  1.1  |
|                               |            |       |       |       |
|   @ $T$=150 K, $r$=1 arcsec   |   24080    |  138  |  210  |  44   |

: Parameters of line emission per arcsec. $A$ is the Einstein coefficient, $J$ is the spin of the upper level, $f$ is the frequency, $\lambda$ is the wavelength, $\Delta{E}$ is the transition energy, $E_u$ is the energy of the upper level, $n$ is the number density, $r_0$ is the radius up to which the relative abundance is constant, $\sigma_0$ describes its radial decline as a Gaussian centred at $r_0$ and having a $\sigma$ equal to $\sigma_0$. $T$ is the temperature, $F_r$=$4\pi kAn(2J+1)e^{-Eu/T}/T$ is the emission in a shell of 1 arcsec radius with $k$ accounting for the different partition functions.

Figure [\[fig23\]](#fig23) compares the $^{28}$SiO, CO and HCN emissions to SO emission by displaying the same distributions as displayed in Figure [\[fig20\]](#fig20) for the latter. While CO and HCN emissions show qualitatively similar distributions as SO, $^{28}$SiO seems to display a significantly different morphology. This had been noted in Paper I but the information contained in Figure [\[fig23\]](#fig23) offers a more detailed description of the differences at stake. The $V_z$ vs $\omega$ map (panel a) shows a slight depression rather than enhancement of emission at the position angle of the south-western outflow, $\omega$$\sim$240$^\circ$. When seen in the outflow planes (panels b and c) the emission shows no sign of an outflow but looks instead as isotropic, simply absorbed in the blue hemisphere. The same picture is suggested by the $V_z$ vs $R$ maps displayed in the right panels where the larger radial extension of the CO emission plays an important role. In order to explain such significant differences between the $^{28}$SiO emission and that of the other lines, we need to understand the impact of the strong self-absorption.

## Absorption of SiO emission

The comparison of the observed $^{28}$SiO emission with the calculated value of the unabsorbed emission parameter $\varepsilon$ performed in the preceding section suggests a strong self-absorption in both the red and blue hemispheres. In an idealised LTE picture, the emission reads $I$=$\varepsilon(1-e^{-\tau})/\tau$ and the optical thickness is $\tau$=2.9 10$^7\varepsilon$$(e^{\Delta{E}/T}$$-$1)/$f^3$. The ratio $\tau/\varepsilon$ is nearly the same for all lines: at 150 K, it is $\sim$0.08, 0.08, 0.08 and 0.15 for SiO, CO, HCN and SO respectively. Namely, for a 0.1 arcsec thick layer, $\tau$=15, 0.09, 0.13 and 0.05 at 150 K and $r$=1 arcsec, meaning an effective absorption by a factor $\sim$15 for SiO.

Another comparison of relevance is between the best fit to the $^{29}$SiO emission in a ring 0.15\<$R$\<0.20 arcsec obtained in Section 4 and the emission predicted using the same model for a density increased by a factor 1/0.08. We find that the ratio of absorbed to non-absorbed emissions decreases from 0.48 for the $^{29}$SiO density to 0.062 for the increased density, namely an increase of the absorption by a factor $\sim$7.7. Figure [1](#fig24) compares the $R$ distributions of the emission of both isotopologues, the $^{29}$SiO data having been smeared to account for the larger $^{28}$SiO beam size and the $^{28}$SiO data having been multiplied by 0.08 to account for the isotopic ratio. The observed increase of absorption between $^{29}$SiO and $^{28}$SiO is $\sim$5 in the red hemisphere and $\sim$10 in the blue hemisphere, well bracketing the predicted value of 7.7.

Finally, we model the $^{28}$SiO emission over two rings, 0.35\<$R$\<0.55 arcsec and 0.65\<$R$\<0.85 arcsec, far enough from the stellar disc for continuum emission to be negligible. The model includes the same form of Gaussian line broadening as described in Section 4 with the addition of a constant width $V_{\rm{turb0}}$. The radial expansion has the form described in Section 6.2. It assumes a $r^{-2}$ radial dependence of the density. The temperature is taken of the form $T$=$T_{0.5}r^{-p}$. The parameters being adjusted are the expansion parameter $r_{\sfrac{1}{2}}$, the density $N_{0.5}$ at $r$=0.5 arcsec, the line width parameters and the temperature parameters $T_{0.5}$ and $p$. The result is shown in panels c and d of Figure [1](#fig24). The fit requires again a much steeper radial dependence of the temperature than used in earlier works: the fits displayed in Figure [1](#fig24) are for $T_{0.5}$=315 K and a 1/$r$ dependence ($p$=1) meaning $T$=158 K at $r$=1 arcsec. The model is too simple and makes too many simplifying assumptions for these numbers to be taken at face value. Yet, the trend for a steep radial dependence of the temperature, which was already suggested by the study of the inner layer presented in Section 4, is likely to be qualitatively valid. The best fit value of $r_{\sfrac{1}{2}}$ is 0.4 arcsec and the fit is not very sensitive to its precise value. The line broadening is the sum of a constant term, $V_{\rm{turb0}}$=0.7 km s$^{-1}$, and a Gaussian of amplitude 2 km s$^{-1}$ centred at $r$=0.3 arcsec and having a $\sigma$ of 0.20 arcsec. The density at $r$=0.5 arcsec is 1625 molecules per cm$^3$, in agreement with the value found for the $^{29}$SiO fit, $\sim$40% of that given by (cite: VandeSande2018). Better fits than shown in Figure [1](#fig24) can be obtained by fine-tuning the forms adopted for the radial dependence of the various parameters, but we refrain from showing these because the crudeness of the model makes such an exercise pointless.

![image](figures_rdor2/fig24a-rdist-sio-28-29-red.eps) ![image](figures_rdor2/fig24b-rdist-sio-28-29-blue.eps) ![image](figures_rdor2/fig24c-spect-28sio-ring.3.eps) ![image](figures_rdor2/fig24d-spect-28sio-ring.6.eps)

Qualitatively, the several arguments developed in the present and preceding sections have all shown that the SiO layer covering from $\sim$0.2 arcsec to \>1 arcsec distance from the star is optically thick and absorbs a large fraction of its own emission in both the red and blue hemispheres. The observed strong absorption is a result of the concurrence of a large Einstein coefficient and a large abundance: it is not expected to be specific to R Dor but should be also present in other oxygen-rich AGB stars. It is indeed the case, at least qualitatively, for Mira Ceti (cite: Wong2016) and W Hya (cite: Takigawa2017). A quantitative reliable modelling would require observations of higher sensitivity and better $uv$ coverage than currently available.

# Summary and conclusions 

The observations presented and analysed in the present article contribute important new information on five major features of the morpho-kinematics of the CSE of R Dor: rotation, absorption, presence of a south-eastern blue-shifted stream, large Doppler velocity wings and the detailed structure of the CSE up to $\sim$60 au distance from the star.

i\) Rotation is seen to reach a maximal velocity of $\sim$5 to 7 km s$^{-1}$ at some 8$\pm$2 au from the centre of the star, where the Keplerian orbital velocity around a 1.4 M$_\odot$ star is $\sim$13 km s$^{-1}$. Its axis projects on the plane of the sky at a position angle of 10$\pm$5$^\circ$ and makes an unknown angle with the plane of the sky; yet, qualitative considerations favour a low value, typically 20$^\circ$$\pm$20$^\circ$ as suggested by the analysis of (cite: Homan2018). The picture obtained from the analysis of the present observations reconciles those presented earlier by (cite: Vlemmings2018) and (cite: Homan2018), claimed to be in conflict by the former authors. Qualitatively, it confirms an increase of the rotation velocity from $\sim$1 km s$^{-1}$ at the surface of the star to its maximal value, described by (cite: Vlemmings2018) as “solid body rotation”; and it confirms the decrease of the rotation velocity from its maximal value down to zero around $\sim$15 au, described by (cite: Homan2018) as “sub-Keplerian”. Quantitatively, evidence is given for an important contribution of the blue stream to the kinematics for projected distances from the star exceeding $\sim$12 au, giving the appearance of a larger rotation velocity. Both $^{29}$SiO and SO$_2$ emission data give very consistent results. An interpretation suggested by (cite: Vlemmings2018) is the presence of a companion at some 6 au from the star, resulting in solid-body rotation of the close-by atmosphere extending up to a very few stellar radii and decreasing beyond. It might equally be that such a companion has already been engulfed in the recent past. The morphology of the rotating volume does not show strong anisotropy and, in particular, fails to provide evidence for a disc-like flattening about the equator as suggested by (cite: Homan2018). It shows instead a broad enhancement covering the north-western quadrant, reaching close to 20% for $^{29}$SiO and to 30% for SO$_2$.

ii\) Absorption of the $^{29}$SiO emission is nearly total at $V_z$$\sim$$-$4 km s$^{-1}$ over the stellar disc and extends beyond it, an observation that had not been explicitly made in earlier studies. Strictly speaking, total absorption is not possible because one cannot prevent the outer part of an optically thick layer from shining. Quantitatively, using as reference the prediction of a simple LTE model, it would require the presence of a low temperature self-absorbing layer, expanding with a velocity of $\sim$4 km s$^{-1}$ at a distance exceeding some 40 au from the star. A detailed study of the morpho-kinematics of the CSE at distances reaching $\sim$100 au, using ALMA observations of SO, $^{28}$SiO, CO and HCN suggests that such is indeed the case. New observations of higher sensitivity and better $uv$ coverage are needed to reliably confirm this important result. A qualitatively similar effect is expected to occur in the environment of other oxygen-rich AGB stars, as seems indeed to be the case for Mira Ceti and W Hya.

iii\) The blue stream is observed at $\sim$140$^\circ$ position angle to extend radially from $\sim$10 au to $\sim$30 au with a mean projected acceleration of 39.2$\pm$0.9 km s$^{-1}$ arcsec$^{-1}$. Interpreted as a gas stream in rectilinear motion, it points to the star to within some 1.5 au. This makes it difficult to describe it as gas trailing beyond a possible companion: unless it flows near the plane of the sky, its trajectory covers too long a time during which the companion is expected to travel too long a distance: it should have the shape of a spiral rather than of a straight line and should therefore not be seen to point precisely to the star. If instead it flows close to the plane of the sky, it must reach very large space velocities, up to 100 km s$^{-1}$ or so. It is difficult to conceive a sensible scenario that would simply relate the presence of the blue stream to that of an evaporating planetary companion, as suggested earlier by (cite: Decin2018; Homan2018) and (cite: Vlemmings2018). Qualitatively, as the blue stream is seen in continuity with the expansion of the slow wind, a more natural interpretation of its dynamics is that it is associated with a local enhancement of aluminium-rich dust density at some 12 au from the star and some 30$^\circ$ to 45$^\circ$ from the line of sight (cite: Takigawa2017).

The absence of evidence for a planetary companion should not be interpreted as evidence for the absence of such companions. Indeed, it would be unreasonable to ignore that AGB stars are very likely to host many planets in their CSE, as do the parent Main Sequence stars. However, while the engulfment process is expected to be extremely fast (cite: Villaver2014) we must remember that the dust mass around R Dor is two orders of magnitude smaller than the Earth mass (cite: Decin2018) and many events may happen before and during engulfment that might leave a mark in the CSE.

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

iv\) The high Doppler velocity wings studied earlier have been shown to be well separated from the blue stream and to be caused by a significant line broadening occurring within the inner layer of the CSE, below 12 au from the star. Its precise nature, including turbulence, shocks and even a possible effect of pulsations, remains to be clarified.

v\) The presence of two broad outflows covering the south-western red-shifted and north-eastern blue-shifted octants respectively has been confirmed and parameters defining their morpho-kinematics have been estimated. Observation of other lines, from $^{28}$SiO, CO and HCN molecules, probing the CSE up to some 60 au from the star, has provided a qualitative confirmation of the SO result. However, the observed morpho-kinematics of $^{28}$SiO emission differs significantly from that of the other lines, probably because the very strong self-absorption hides the inner layers from observation. New observations with good $uv$ coverage, resolution and sensitivity, are very much needed in order to refine the general picture obtained from the existing SO observations.

The picture of the R Dor CSE that emerges from the present study is consistent with an early launch of the wind by aluminium-rich dust, followed by a progressive increase of the contribution of silicon-rich dust, giving support to a three-step picture of the generation and acceleration of the wind: in a first step pulsations and convective cell ejections give a first boost to the gas, with velocities reaching typically some 10 km s$^{-1}$, sufficient to eject part of it to a few au beyond the photosphere. There, in a second step, large transparent grains start to condense, mostly aluminium-rich, reaching grain sizes of a few tenths of a micron within some 10 au from the star; they are accelerated by photon scattering and transfer part of their momentum to the gas, providing a first pre-acceleration that brings it into a region where silicate grains start to condense. These grains are accelerated by radiation pressure and reach up to several tens au beyond the star surface. There, in a third step, the gas is progressively accelerated by collisions with the dust grains to reach a terminal velocity at the 5 to 10 km s$^{-1}$ scale at some 100 au from the star, where it has finally escaped the star gravity.

Yet, to make sense of what we observe, we need to answer a number of open questions concerning the possible presence of planetary companion(s) and its impact, the mechanism causing the generation of significant rotation, the precise nature of the blue-shifted stream and the mechanism beyond the shaping of the pair of back-to-back outflows. In particular, new observations with good $uv$ coverage, resolution and sensitivity, of line emissions probing the CSE up to some 60 au from the star, such as $^{28}$SiO, CO and HCN molecules, are very much needed in order to refine the general picture obtained from the existing SO observations.

We are still a long way away from being able to model precisely the physics and chemistry at stake in the CSE of R Dor. Such modelling cannot afford to ignore the complex reality of the observed morpho-kinematics. While progressing in its description, we still fail to give a coherent interpretation of three apparently unrelated features: star rotation, blue stream and pair of broad back-to-back outflows.

# Acknowledgements

We express our deep gratitude to the anonymous referee for a very detailed and pertinent review that helped to significantly improve the presentation of the manuscript and we thank Professors Eva Villaver, Leen Decin, Ward Homan, Pierre Lesaffre and Stéphane Guilloteau for useful discussions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00191.S (PI: Theo Khouri), ADS/JAO.ALMA#2017.1.00824.S (PI: Leen Decin) and ADS/JAO.ALMA#2013.1.00166.S (PI: Leen Decin). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The SO data are retrieved from the JVO/NAOJ portal. We are deeply indebted to the ALMA partnership, whose open access policy means invaluable support and encouragement for Vietnamese astrophysics. In particular, we acknowledge the time and effort dedicated by the PIs of the projects used in this article for producing proposals of observations selected to best serve the AGB community. Financial support from the World Laboratory, the Odon Vallet Foundation and VNSC is gratefully acknowledged. This research is funded by the Vietnam National Foundation for Science and Technology Development (NAFOSTED) under grant number 103.99-2019.368.

# Data Availability

The raw data are available on the ALMA archive ADS/JAO.ALMA#2017.1.00191.S, ADS/JAO.ALMA# 2017.1.00824.S, ADS/JAO.ALMA#2013.1.00166.S. The calibrated and imaged data underlying this article will be shared on reasonable request to the corresponding author.

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

# 

+-----------------------------------------------------------------+
| SiO                                                             |
+:====:+:========:+:=====:+:=====:+:=============:+:=============:+
| ring | quadrant | $I^*$ | $I_0$ | $V_{z0}$      | $\sigma_0$    |
+------+----------+-------+-------+---------------+---------------+
|      |          | (mJy) | (mJy) | (km s$^{-1}$) | (km s$^{-1}$) |
+------+----------+-------+-------+---------------+---------------+
| 2    | N        | 28    | 159   | 0.2           | 7.6           |
+------+----------+-------+-------+---------------+---------------+
| 2    | E        | 14    | 266   | $-$3.1        | 5.4           |
+------+----------+-------+-------+---------------+---------------+
| 2    | S        | 13    | 171   | 0             | 6.6           |
+------+----------+-------+-------+---------------+---------------+
| 2    | W        | 19    | 190   | 3.5           | 7.5           |
+------+----------+-------+-------+---------------+---------------+
| 3    | N        | 8     | 292   | 1.1           | 5.1           |
+------+----------+-------+-------+---------------+---------------+
| 3    | E        | $-$4  | 453   | $-$3.0        | 4.1           |
+------+----------+-------+-------+---------------+---------------+
| 3    | S        | $-$6  | 278   | $-$0.7        | 4.6           |
+------+----------+-------+-------+---------------+---------------+
| 3    | W        | 9     | 325   | 4.4           | 4.1           |
+------+----------+-------+-------+---------------+---------------+
| 4    | N        | $-$1  | 351   | 1.1           | 5.0           |
+------+----------+-------+-------+---------------+---------------+
| 4    | E        | $-$4  | 461   | $-$2.6        | 3.8           |
+------+----------+-------+-------+---------------+---------------+
| 4    | S        | $-$3  | 318   | $-$0.5        | 4.4           |
+------+----------+-------+-------+---------------+---------------+
| 4    | W        | 8     | 367   | 3.3           | 3.1           |
+------+----------+-------+-------+---------------+---------------+
| 2    | NE       | 21    | 220   | $-$2.5        | 6.2           |
+------+----------+-------+-------+---------------+---------------+
| 2    | SE       | 14    | 205   | $-$1.7        | 5.8           |
+------+----------+-------+-------+---------------+---------------+
| 2    | SW       | 15    | 172   | 2.8           | 7.2           |
+------+----------+-------+-------+---------------+---------------+
| 2    | NW       | 25    | 164   | 2.2           | 7.3           |
+------+----------+-------+-------+---------------+---------------+
| 3    | NE       | $-$2  | 362   | $-$2.1        | 4.7           |
+------+----------+-------+-------+---------------+---------------+
| 3    | SE       | $-$1  | 368   | $-$2.4        | 4.1           |
+------+----------+-------+-------+---------------+---------------+
| 3    | SW       | 4     | 259   | 2.6           | 4.2           |
+------+----------+-------+-------+---------------+---------------+
| 3    | NW       | 8     | 328   | 4.0           | 4.3           |
+------+----------+-------+-------+---------------+---------------+
| 4    | NE       | $-$7  | 384   | $-$1.3        | 4.5           |
+------+----------+-------+-------+---------------+---------------+
| 4    | SE       | $-$3  | 418   | $-$2.4        | 3.9           |
+------+----------+-------+-------+---------------+---------------+
| 4    | SW       | 3     | 339   | 2.6           | 2.9           |
+------+----------+-------+-------+---------------+---------------+
| 4    | NW       | 10    | 362   | 3.4           | 3.7           |
+------+----------+-------+-------+---------------+---------------+

: Parameters of the best fits to the Doppler velocity distributions displayed in Figure [\[fig6\]](#fig6).

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

+-----------------------------------------------------------------+
| SO$_2$                                                          |
+:====:+:========:+:=====:+:=====:+:=============:+:=============:+
| ring | quadrant | $I^*$ | $I_0$ | $V_{z0}$      | $\sigma_0$    |
+------+----------+-------+-------+---------------+---------------+
|      |          | (mJy) | (mJy) | (km s$^{-1}$) | (km s$^{-1}$) |
+------+----------+-------+-------+---------------+---------------+
| 2    | N        | 31    | 74    | 0             | 4.0           |
+------+----------+-------+-------+---------------+---------------+
| 2    | E        | 12    | 73    | $-$2.6        | 3.9           |
+------+----------+-------+-------+---------------+---------------+
| 2    | S        | 14    | 67    | 0.1           | 3.9           |
+------+----------+-------+-------+---------------+---------------+
| 2    | W        | 21    | 61    | 2.3           | 4.7           |
+------+----------+-------+-------+---------------+---------------+
| 3    | N        | 8     | 52    | 0.7           | 3.9           |
+------+----------+-------+-------+---------------+---------------+
| 3    | E        | $-$3  | 44    | $-$2.3        | 3.5           |
+------+----------+-------+-------+---------------+---------------+
| 3    | S        | $-$4  | 46    | $-$2.1        | 3.3           |
+------+----------+-------+-------+---------------+---------------+
| 3    | W        | 8     | 55    | 3.1           | 3.7           |
+------+----------+-------+-------+---------------+---------------+
| 4    | N        | 3     | 26    | 0.3           | 3.9           |
+------+----------+-------+-------+---------------+---------------+
| 4    | E        | $-$3  | 35    | $-$2.0        | 3.1           |
+------+----------+-------+-------+---------------+---------------+
| 4    | S        | 0     | 35    | $-$2.2        | 3.1           |
+------+----------+-------+-------+---------------+---------------+
| 4    | W        | 3     | 39    | 1.6           | 3.1           |
+------+----------+-------+-------+---------------+---------------+
| 2    | NE       | 21    | 76    | $-$1.8        | 3.8           |
+------+----------+-------+-------+---------------+---------------+
| 2    | SE       | 13    | 69    | $-$1.6        | 3.8           |
+------+----------+-------+-------+---------------+---------------+
| 2    | SW       | 18    | 63    | 1.9           | 4.3           |
+------+----------+-------+-------+---------------+---------------+
| 2    | NW       | 26    | 65    | 1.5           | 4.4           |
+------+----------+-------+-------+---------------+---------------+
| 3    | NE       | 3     | 52    | $-$1.7        | 3.3           |
+------+----------+-------+-------+---------------+---------------+
| 3    | SE       | $-$1  | 48    | $-$2.7        | 3.0           |
+------+----------+-------+-------+---------------+---------------+
| 3    | SW       | 2     | 40    | 1.0           | 3.8           |
+------+----------+-------+-------+---------------+---------------+
| 3    | NW       | 6     | 62    | 3.0           | 3.9           |
+------+----------+-------+-------+---------------+---------------+
| 4    | NE       | $-$1  | 39    | $-$1.5        | 2.6           |
+------+----------+-------+-------+---------------+---------------+
| 4    | SE       | $-$1  | 33    | $-$2.9        | 3.5           |
+------+----------+-------+-------+---------------+---------------+
| 4    | SW       | 2     | 37    | 0.3           | 3.0           |
+------+----------+-------+-------+---------------+---------------+
| 4    | NW       | 5     | 29    | 2.3           | 3.9           |
+------+----------+-------+-------+---------------+---------------+

: Parameters of the best fits to the Doppler velocity distributions displayed in Figure [\[fig7\]](#fig7).

![](figures_rdor2/figA1-suppl-chmap-29sio-2.eps)

![](figures_rdor2/figA2-suppl-chmap-so2-2.eps)

[^1]: E-mail: pttnhung@vnsc.org.vn

[^2]: E-mail: dthoai@vnsc.org.vn

</paper>

## Items to check

```json
[
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "Simulated visibilities created using CASA SIMOBSERVE for three toy models of sky brightness (continuum disc, absorbed CSE disc, unabsorbed disc+CSE) to test the impact of short spacing on absorption beyond the stellar disc.",
  "failed_quote": "For each of the three cases, we produce visibilities $U$ corresponding to the actual antenna configuration illustrated in Figure 2."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Circular orbit of companion around a 1.4 M_sun star; orbital axis aligned with gas rotation axis (PA = 10 +/- 5 deg)",
  "failed_quote": "Assuming that the orbital axis is at the same time the rotation axis of the volume of gas we retain a value $\\omega_R$=10$^\\circ$$\\pm$5$^\\circ$ east of north, from the results listed in Table 2 and those obtained by (cite: Vlemmings2018)."
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "Simulate visibilities with CASA SIMOBSERVE for three isotropic sky brightness models (case 1: stellar continuum disc R < 0.04 arcsec; case 2: CSE disc R < 0.3 arcsec with absorbed stellar disc; case 3: sum of cases 1 and 2) using the actual antenna configuration, and compare baseline-dependent visibility amplitudes against real 29SiO visibilities at V_z = -4, +4 km s^-1, and continuum.",
  "failed_quote": "For each of the three cases, we produce visibilities $U$ corresponding to the actual antenna configuration illustrated in Figure 2."
 }
]
```
