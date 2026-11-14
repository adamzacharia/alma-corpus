# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.518.2034H\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Evidence for episodic and patchy mass ejection in the circumstellar envelope of AGB star R Leonis

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

# Abstract

The morpho-kinematics of the circumstellar envelope of oxygen-rich AGB star R Leonis is probed using ALMA (Atacama Large Millimeter/submillimeter Array) observations of the emission of molecular lines, including in particular CO(2-1) and $^{29}$SiO(5-4). Evidence is found for an episode of enhanced mass loss, a few centuries ago, that produced a broad expanding shell of mean radius $\sim$6 arcsec and mean radial expansion velocity $\sim$5.5 km s$^{-1}$. Detailed scrutiny of its structure, as displayed by the emission of the CO(2-1) line, reveals strong inhomogeneity and patchy morphology. Evidence is also found, in particular from the morpho-kinematics of the emission of SiO, SO and SO$_2$ lines probing the close neighbourhood of the star, for distinct gas outflows covering broad solid angles in the south-eastern, south-western and north-western quadrants, suggesting significant contribution of the convective cell granulation in defining the pattern of mass ejection. A study of relative molecular abundances in these outflows suggests that a Local Thermal Equilibrium (LTE) description applies approximately beyond $\sim$10 stellar radii from the centre of the star but not at the smaller angular separations where the SO and SO$_2$ molecules are found to be confined. Near the stellar disc, masers of the vibrationally excited SiO lines are found to probe north-western parts of a layer of hot gas, consistent with the earlier observation of an asymmetric expanding shell within 1-2 stellar radii from the centre of the star. Globally, a picture dominated by episodic and patchy mass ejections is found to prevail.

stars: AGB and post-AGB – circumstellar matter – stars: individual: R Leonis – radio lines: stars

# Introduction

High resolution observations of the circumstellar envelopes of oxygen rich AGB stars, in particular using the Very Large Telescope (VLT) or the Atacama Large Millimeter/submillimeter Array (ALMA), have revealed very complex structures. Recent state-of-the art hydro-dynamical simulations (cite: Hofner2019; Freytag2017; Liljegren2018) suggest that such complexity is the result of shocks induced by a combination of convection and stellar pulsations. They induce an effective line broadening for ALMA observations of the emission of molecular lines in the close neighbourhood of the star. Typical examples are R Dor (cite: Hoai2020; Nhung2021), $o$ Cet (cite: Nhung2022a) or R Hya (cite: Nhung2022b). In the present article we study the case of R Leo, for which ALMA observations of the emissions of the $^{12}$CO($\nu$=0,$J$=2-1) and $^{29}$SiO($\nu$=0,$J$=5-4) (hereafter abbreviated as CO(2-1) and $^{29}$SiO(5-4) respectively) lines have been the subject of preliminary studies by (cite: Fonfria2019a; Fonfria2019b). We contribute additional and complementary analyses of the same data as well as new analyses of other ALMA observations, including the emissions of molecular lines $^{28}$SiO($\nu$=1,$J$=5-4), $^{28}$SiO($\nu$=1,$J$=8-7), $^{28}$SiO($\nu$=2,$J$=5-4), SO($^3\Sigma$,$\nu$=0,$N_J$=5$_5$-4$_4$), SO$_2$($\nu$=0,$J_{\text{Ka,Kc}}$=22$_{2,20}$-22$_{1,21}$) and SO$_2$($\nu$=0,$J_{\text{Ka,Kc}}$=13$_{2,12}$-12$_{1,11}$), hereafter abbreviated as SiO($\nu$=1,5-4), SiO($\nu$=1,8-7), SiO($\nu$=2,5-4), SO(5$_5$-4$_4$), SO$_2$(22$_{2,20}$-22$_{1,21}$) and SO$_2$(13$_{2,12}$-12$_{1,11}$) respectively.

R Leo is an oxygen-rich AGB star. Its distance to Earth is not well measured, varying from 71 pc (cite: Gaia2018) to 114 pc (cite: vanLeeuwen2007). In our analysis we use 114 pc, a value consistent with the distance obtained from the period-luminosity relation (cite: Haniff1995). We note that after submission of the present paper for publication, an article of utmost relevance to this issue has been published (cite: Andriantsaralaza2022), arguing in favour of a distance of 100$\pm$5 pc. The pulsation period is 310 days (cite: Feast1996; Watson2006) and the mass-loss rate, evaluated from single dish observations, is $\sim$1.0 10$^{-7}$ solar masses per year (cite: Danilovich2015). The star effective temperature is $\sim$2500-3000 K and its angular diameter is 25-30 mas (cite: Perrin1999; Fedele2005; Wittkowski2016; Matthews2018). (cite: Vlemmings2019) using ALMA observations to probe the extended atmosphere within 1-2 stellar radii, measured an asymmetric, radial expansion of the radio photosphere at a mean velocity of 10.6$\pm$1.4 km s$^{-1}$ at stellar phases between 0.41 and 0.46.

The close neighbourhood of the star has been observed in the near-infrared by (cite: Fedele2005) using VLTI/VINCI and in the mid-infrared by (cite: Paladini2017) using VLTI/MIDI. SiO masers have been the subject of numerous VLBA observations of outstanding quality by (cite: SoriaRuiz2007), (cite: Cotton2004; Cotton2008; Cotton2009) and (cite: Desmurs2014). (cite: Herpin2006), using the IRAM 30 m telescope, have analysed single-dish SiO maser Zeeman observations to estimate the value of the magnetic field in the near CSE at the level of 4.2-4.6 G; quasi-periodic polarization fluctuations have been interpreted as resulting from a precessing planetary magnetosphere, suggesting the presence of an evaporating Jovian planet (cite: Wiesemeyer2009). Using the Stratospheric Observatory for Infrared Astronomy (SOFIA), (cite: Fonfria2020) have detected the fluorescence of hot carbon dioxide in the extended atmosphere of the star.

Millimetre observations of the expanding gas have measured a terminal velocity of 6-9 km s$^{-1}$ (cite: DeBeck2010; Ramstedt2014) and have detected significant abundances of CO, H$_2$O, OH, SiO, SO, SO$_2$ and HCN molecules (cite: Hinkle1979; Bujarrabal1994; Etoka1997; Bieging2000; GonzalezDelgado2003; Ohnaka2004; Schoier2013; Danilovich2020).

Of particular relevance to the present work are the ALMA observations of $^{29}$SiO(5-4) and CO(2-1) molecular emissions reported by (cite: Fonfria2019a; Fonfria2019b). They interpret the observed morpho-kinematics in terms of an expanding, thin and dense partial shell behind the star that is being shocked by a faster, collimated matter ejection coming from the star. This shell would have been ejected in an apparently single strong event during the last 700 yr. Its thickness ($\sim$1 arcsec) suggests a mass-loss rate enhancement lasting for about 50 yr. They remark that the $^{29}$SiO(5-4) emission around the systemic velocity resembles a deformed spiral structure that suggests the existence of a companion of R Leo. Within $\sim$0.17 arcsec from the centre of the star, they find evidence for the presence of hot gas, elongated along the NE/SW direction, contributing to continuum emission. They remark that the molecular emission displays prominent red-shifted absorption in front of the star, typical of material in-fall, and lateral gas motions compatible with the presence of a possibly rotating torus-like structure.

# Observations and data reduction

The present work uses archival observations of R Leo from ALMA projects ADS/JAO.ALMA#2016.1.01202.S (PI. J. Fonfría) in Band 6 and ADS/JAO.ALMA#2017.1.00862.S (PI Kamiński) in Band 7.

The Band 6 (211-275 GHz) observations were made on 1 October 2016, 22 March and 3 May 2017 with low angular resolution ($\sim$0.2 arcsec) and on 21 September and 27 October 2017 with high angular resolution ($\sim$0.03 arcsec). The baselines were between 15 m and 13.9 km long. The total time on source of the observations was $\sim$80 min.

The Band 7 (275-373 GHz) observations were made on 16 November 2017 with configuration C43-8 which has baselines between 92 m and 8.5 km. The total time on source of the observations was $\sim$22 min. Both Band 6 and Band 7 observations were made shortly after the minimum of the light curve, the stellar phase of the former being $\sim$0.50 (cite: Fonfria2019b).

The data were calibrated using CASA[^3] with the standard script provided by the ALMA staff. The images of CO(2-1) in Section 4 were produced from the merged data of Band 6 observations using GILDAS[^4]/IMAGER[^5] with robust weighting (threshold value of 1.5). The images of the continuum and the lines at high resolution in Band 6 were produced from the data observed on 27 October 2017 with baselines between 191 m and 13.9 km and total time on source of $\sim$15 min. The phase centre was shifted to the centre of the continuum emission and the visibilities were changed accordingly. Phase self-calibration was done for the continuum data and the results were applied to the line data. The cleaned images were produced using CASA with uniform weighting for the continuum and natural weighting for the lines. We also used CASA for imaging the data of Band 7 with robust parameter of 0.5. In all cases of line emission imaging, continuum emission has not been subtracted at visibility level in order to preserve the possibility to account properly for its contribution in the image plane.

Relevant parameters are listed in Tables [\[tab1\]](#tab1) and [\[tab2\]](#tab2).

We use coordinates centred on the peak of continuum emission, $x$ pointing east, $y$ pointing north and $z$ pointing away from Earth. The projected angular separation to the star is calculated as $R$=$\sqrt{x^2+y^2}$. Position angles, $\omega$, are measured counter-clockwise from north. The Doppler velocity $V_\text{z}$ spectrum is centred on a star systemic velocity of $-$0.5 km s$^{-1}$ (cite: Teyssier2006), which, however, is not known to better than $\sim$$\pm$0.5 km s$^{-1}$.

+--------+---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | Line                            | Beam                                   | Pixel size             | Channel spacing (km s$^{-1}$) | Noise (mJy beam$^{-1}$) |
+:======:+:===============================:+:======================================:+:======================:+:=============================:+:=======================:+
| Band 6 | $^{29}$SiO(5-4)                 | 47$\times$44 mas$^2$, PA=40$^\circ$    | 5$\times$5 mas$^2$     | 1.36                          | 0.7                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | SiO($\nu$=1,5-4)                | 46$\times$38 mas$^2$, PA=34$^\circ$    | 5$\times$5 mas$^2$     | 1.36                          | 0.6                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | SiO($\nu$=2,5-4)                | 47$\times$44 mas$^2$, PA=39$^\circ$    | 5$\times$5 mas$^2$     | 1.36                          | 0.8                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | SO(5$_5$-4$_4$)                 | 46$\times$38 mas$^2$, PA=34$^\circ$    | 5$\times$5 mas$^2$     | 1.36                          | 0.5                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | SO$_2$(22$_{2,20}$-22$_{1,21}$) | 46$\times$37 mas$^2$, PA=34$^\circ$    | 5$\times$5 mas$^2$     | 1.36                          | 0.8                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | CO(2-1) extended                | 43$\times$36 mas$^2$, PA=33$^\circ$    | 5$\times$5 mas$^2$     | 0.635                         | 0.8                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | Continuum                       | 28$\times$26 mas$^2$, PA=34$^\circ$    | 5$\times$5 mas$^2$     | $-$                           | 0.06                    |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | CO(2-1) merged                  | 106$\times$86 mas$^2$, PA=71$^\circ$   | 30$\times$30 mas$^2$   | 0.635                         | 0.5                     |
+--------+---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
| Band 7 | SiO($\nu$=1,8-7)                | 49$\times$44 mas$^2$, PA=$-$12$^\circ$ | 7.4$\times$7.4 mas$^2$ | 0.85                          | 2.1                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | SO$_2$(13$_{2,12}$-12$_{1,11}$) | 49$\times$44 mas$^2$, PA=$-$11$^\circ$ | 7.4$\times$7.4 mas$^2$ | 0.85                          | 2.1                     |
|        +---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+
|        | Continuum                       | 45$\times$40 mas$^2$, PA=$-$38$^\circ$ | 7.4$\times$7.4 mas$^2$ | $-$                           | 0.33                    |
+--------+---------------------------------+----------------------------------------+------------------------+-------------------------------+-------------------------+

| Line | $f$ \[GHz\] | $A_\text{ji}$ \[10$^{-3}$ Hz\] | $E_\text{u}$ \[K\] | 2$J$+1 | $k$ (100 K) | $k$ (1000 K) |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| CO(2-1) | 230.5380 | 0.69 10$^{-3}$ | 16.6 | 5 | 2.75 | 2.63 |
| $^{29}$SiO(5-4) | 214.3858 | 0.50 | 30.9 | 11 | 1.03 | 0.85 |
| SiO($\nu$=1,5-4) | 215.5959 | 0.50 | 1789 | 11 | 1.01 | 0.85 |
| SiO($\nu$=1,8-7) | 344.9165 | 2.2 | 1844 | 17 | 1.01 | 0.85 |
| SiO($\nu$=2,5-4) | 214.0885 | 0.51 | 3552 | 11 | 1.04 | 0.86 |
| SO(5$_5$-4$_4$) | 215.2206 | 0.12 | 44.1 | 11 | 0.37 | 0.35 |
| SO$_2$(13$_{2,12}$-12$_{1,11}$) | 345.3385 | 0.24 | 93 | 27 | 0.087 | 0.021 |
| SO$_2$(22$_{2,20}$-22$_{1,21}$) | 216.6433 | 0.093 | 248.4 | 45 | 0.087 | 0.021 |
| H$^{13}$CN(4-3) | 344.2001 | 1.9 | 41.4 | 9 | 2.04 | 0.87 |

# Continuum emission

While Band 7 data display a nearly circular continuum emission (Figure [1](#fig2)), as do lower frequency data (cite: Matthews2018), Band 6 data were shown by (cite: Fonfria2019b) to display clear elongation in the NE/SW direction, which they interpreted as evidence for hot gas and dust around the star, probably in a nearly edge-on torus configuration. However, this elongation is caused by a significant offset of the phase-centre and disappears after having corrected for it (Figure [1](#fig2)). The coordinates of the origin are: RA=09h47m33.492315s and Dec=11$^\circ$25’42.9081536”. This confirms results obtained by (cite: Vlemmings2019). These authors performed a very careful and detailed analysis of ALMA Band 6 observations and found evidence for asymmetric expansion with significant residuals from a uniform stellar disc towards the north-east. They describe it in terms of an increased opacity layer that might in reality be a directional shock wave propagating through the extended atmosphere. They argue that the observed motion is likely due to density or ionisation changes and remark that it means an expansion of material with a size of up to a quarter of the stellar disc, not inconsistent with the size of a large convective cell.

![image](figures/fig2a_band7cont.eps) ![image](figures/fig2b_band6cont_org.eps) ![image](figures/fig2c_band6cont_phaseshifted.eps) ![image](figures/fig2d_band6cont_selfcal.eps)

# CO(2-1) line emission: a radially expanding shell

Channel maps of the CO(2-1) emission are displayed in Figure [2](#fig3). The bulk of the emission is well contained within $R$\<6 arcsec and \|$V_\text{z}$\|\<10 km s$^{-1}$. Figure [3](#fig4) gives evidence for a significant enhancement of emission in a shell having a mean radius of some 6 arcsec and expanding at a mean velocity of some 5.5 km s$^{-1}$, namely having been ejected 6-7 centuries ago. Panel (a) displays the $R$ distribution of the intensity integrated over \|$V_\text{z}$\|\<10 km s$^{-1}$ and panel (b) an intensity map on the $V_\text{z}$ vs $R$ plane, integrated over position angles. The latter illustrates clearly the shell structure: the data are compared with three ellipses defined as $\rho$=$\sqrt{(V_\text{z}/5.5)^2+(R/6)^2}$=1/$\sqrt{2}$, 1 and $\sqrt{2}$, respectively; they correspond to spherical shells of radius $6 \times \rho$ arcsec and expansion velocities $5.5\times\rho$ km s$^{-1}$. Panel (c) displays the $\rho$ distribution of the emission for each of the blue- and red-shifted hemispheres separately as well as for the whole range of Doppler velocities. The shape is the same in both hemispheres, the blue-shifted emission being some 30% weaker than the red-shifted one. It gives evidence for a clear enhancement at $\rho$$\sim$0.8-1.2. The Doppler velocity spectrum, shown in panel (d), displays the double hump profile expected from the shell structure. Globally, Figure [3](#fig4) illustrates and quantifies the qualitative interpretation of the channel maps that (cite: Fonfria2019a) had suggested.

However, when inspecting in more detail the morpho-kinematics governing the structure of the shell, one finds evidence for very important inhomogeneity, the shell being in fact made of a collection of individual patches. Figures [4](#fig5) and [5](#fig6) illustrate the main features. Figure [4](#fig5) displays PV maps, $V_\text{z}$ vs $\omega$, of the CO(2-1) emission in three different intervals of $R$: 1 to 2, 2 to 3 and 3 to 4 arcsec, respectively. It gives evidence for the very irregular distribution of Doppler velocities in the shell, and for the patchy nature of its emission, in particular in the blue-shifted hemisphere. Moreover, patches of emission are seen inside the shell. In particular, at $V_\text{z}$$\sim$$-2$ km s$^{-1}$, $\omega$$\sim$260$^\circ$ (diamond) for 1\<$R$\<2 arcsec; at $V_\text{z}$$\sim$2-3 km s$^{-1}$, $\omega$$\sim$300$^\circ$ (circle) for 2\<$R$\<3 arcsec; and at $V_\text{z}$$\sim$2-3 km s$^{-1}$, $\omega$$\sim$120$^\circ$ (rectangle) for 3\<$R$\<4 arcsec. The first of these (diamond) corresponds to a blue-shifted gas flow that is further illustrated in Figure [5](#fig6) and starts being clearly identified at $R$$\sim$0.4 arcsec. The second (circle) is a blob of emission that is visible on the 0-3 km s$^{-1}$ intensity map (centre-right panel in the lower row of Figure [4](#fig5)). The third (rectangle) is located near an arc of emission that can be seen on both the red-shifted and the 0-3 km s$^{-1}$ intensity maps. A similar arc is visible on the blue-shifted intensity map. It is tempting to associate these arcs with possible spirals revealing the presence of a companion (cite: Fonfria2019a). However, when mapping the $V_\text{z}$ vs $\omega$ map of the intensity along such a presumed spiral (right panel of the lower row of Figure [4](#fig5)), one sees that one cannot make simply sense of such an interpretation.

![](figures/fig3_rleo-co21-chmap-v05.5-r06.0.eps)

![image](figures/fig4a_co21-rdist.eps) ![image](figures/fig4b_co21-pvmap.eps) ![image](figures/fig4c_co21-rhodist.eps) ![image](figures/fig4d_co21-spect.eps)

Figure [5](#fig6) displays PV maps on the $V_\text{z}$ vs $\omega$ plane at shorter distances from the star, between 0.2 and 1 arcsec. In addition to the previously identified gas flow (diamond), it shows, within $R$$\sim$0.4 arcsec, a blob of emission (ellipse) covering between 0 and 5 km s$^{-1}$ at mean position angle $\omega$$\sim$270$^\circ$, which is associated with a western, red-shifted mass ejection that we study in detail in the next section. Absorption in the blue-shifted part of the shell is seen to possibly extend up to $R$$\sim$0.5 arcsec, but cannot be invoked to explain its weaker emission when compared with the red-shifted part over a much broader range of $R$.

In order to quantify the inhomogeneity of the shell structure, we have compared the $\rho$ distributions of the CO(2-1) intensity measured in twelve sectors of position angle, each 30$^\circ$ wide, with the mean distribution in Figure [6](#fig7). In each sector we measure the resulting rms deviation from unity of their ratio, evaluated in two different intervals of $\rho$. The results are listed in Table [\[tab3\]](#tab3). On average, they reach 37% and 73% for \|$\rho-1$\|\<0.25 and \|$\rho-1$\|\<0.5, respectively, illustrating the importance of inhomogeneity.

|               Sector               |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
|:----------------------------------:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  $\Delta$(0.5\<$\rho$\<1.5) \[%\]  | 109 | 104 | 54  | 109 | 25  | 36  | 47  | 92  | 67  | 61  | 43  | 132 |
| $\Delta$(0.75\<$\rho$\<1.25) \[%\] | 57  | 60  | 16  | 28  | 10  | 30  | 41  | 29  | 56  | 57  | 24  | 39  |

![image](figures/fig5_1a_co21-vzomg-1r2.eps) ![image](figures/fig5_1b_co21-vzomg-2r3.eps) ![image](figures/fig5_1c_co21-vzomg-3r4.eps)\
![image](figures/fig5_2a_co21-intmap-red.eps) ![image](figures/fig5_2b_co21-intmap-blue.eps) ![image](figures/fig5_2c_co21-intmap-0v3.eps) ![image](figures/fig5_2d_co21-pvmap-spiral.eps)

![image](figures/fig6a_co21_vzomg_0.2r0.4.eps) ![image](figures/fig6b_co21_vzomg_0.4r0.6.eps) ![image](figures/fig6c_co21_vzomg_0.6r0.8.eps) ![image](figures/fig6d_co21_vzomg_0.8r1.eps)

# The close neighbourhood of the star

In the present section we study the emission of lines that probe the close neighbourhood of the star, within $\sim$ 0.3 arcsec angular separation from its centre. In addition to the high resolution CO(2-1) data, this includes the vibrational ground state emission of the $^{29}$SiO(5-4) line and the emissions of the sulphur oxide lines, SO(5$_5$-4$_4$), SO$_2$(22$_{2,20}$-22$_{1,21}$) and SO$_2$(13$_{2,12}$-12$_{1,11}$). The latter is blended with a contribution of H$^{13}$CN($\nu$=0,$J$=4-3) (hereafter abbreviated as H$^{13}$CN(4-3)) emission, which we discuss below. In the remaining of the article, we refer to it as the SO$_2$-HCN line. Figures [7](#fig8) to [11](#fig12) illustrate the main features using a common format: channel maps and PV maps in both $V_\text{z}$ vs $\omega$ and $V_\text{z}$ vs $R$, the latter being displayed in four separate quadrants.

![](figures/fig7_rhodist2.eps)

## Observational results

The $^{29}$SiO(5-4) emission (Figure [7](#fig8)) is seen from the channel maps to be dominantly west and slightly red-shifted. The $V_\text{z}$ vs $\omega$ map locates the bulk of the emission between 0 and 4 km s$^{-1}$ in $V_\text{z}$ and between 200$^\circ$ and 340$^\circ$ in $\omega$. Two blobs of emission, separated by $\sim$50-60$^\circ$ in $\omega$ and sharing a common mean Doppler velocity of $\sim$2 km s$^{-1}$, are clearly identified from the channel maps and the $V_\text{z}$ vs $\omega$ map. The south-western blob reaches maximum at $R$$\sim$0.1 arcsec and the north-western blob at $R$$\sim$0.2 arcsec. The CO(2-1) emission (Figure [8](#fig9)) displays a qualitatively similar pattern as the $^{29}$SiO(5-4) emission, with red-shifted enhancements in the south-western and north-western quadrants. The SO(5$_5$-4$_4$) (Figure [9](#fig10)), SO$_2$(22$_{2,20}$-22$_{1,21}$) (Figure [10](#fig11)) and SO$_2$-HCN (Figure [11](#fig12)) emissions are relatively stronger in the blue-shifted south-eastern quadrant. In summary, and qualitatively, the five lines display clear enhancements of emission in three angular ranges, well separated from each other, one slightly blue-shifted in the south-eastern quadrant and two slightly red-shifted in the western hemisphere, one south-west and the other north-west. We have checked that such strong anisotropy is not an artefact of the imaging process by simulating visibilities, for the same observational coverage, for a disc source having a radius of 0.5 arcsec and an isotropic brightness decreasing radially as 1/$R$. The brightness of the image, obtained with natural weighting, was found to deviate from the source brightness by less than a few percent.

In order to compare quantitatively the emissions of the five lines, we define three regions, called SE, SW and NW, with angular separations from the centre of the star between 60 and 300 mas, covering $V_z$ and $\omega$ ranges listed in Table [\[tab4\]](#tab4). They have a same data cube volume of 0.48 arcsec$^2$ km s$^{-1}$ and are indicated by rectangles on the $V_\text{z}$ vs $\omega$ maps of Figures [7](#fig8) to [11](#fig12). They contain well the features observed in these figures and take due account of the sizes of the beams and of the continuum emission. Figure [\[fig13\]](#fig13) displays, for each line emission, its intensity map integrated over the interval \|$V_\text{z}$\|\<6 km s$^{-1}$ and the Doppler velocity spectra measured in each of the three regions defined above. Table [\[tab4\]](#tab4) lists the mean and rms values of the Doppler velocity and position angle distributions measured in each region for each line, together with the associated intensity.

+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| Region                             |                   | CO(2-1)                 | $^{29}$SiO(5-4)         | SO(5$_5$-4$_4$)         | SO$_2$(22$_{2,20}$-22$_{1,21}$) | SO$_2$(13$_{2,12}$-12$_{1,11}$) | Mean        |
+:==================================:+:=================:+:=======================:+:=======================:+:=======================:+:===============================:+:===============================:+:===========:+
|                                    | \<$V_\text{z}$\>  | $-$1.2                  | $-$0.3                  | $-$0.4                  | $-$1.4                          | $-$1.1                          | $-$0.8      |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| SE                                 | Rms($V_\text{z}$) | 1.8                     | 1.5                     | 1.6                     | 1.8                             | 1.3                             | 1.5         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| $-$5\<$V_\text{z}$\<2 km s$^{-1}$  | \<$\omega$\>      | 129$^\circ$             | 137$^\circ$             | 130$^\circ$             | 132$^\circ$                     | 133$^\circ$                     | 133$^\circ$ |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| 90$^\circ$\<$\omega$\<180$^\circ$  | Rms($\omega$)     | 25$^\circ$              | 25$^\circ$              | 24$^\circ$              | 23$^\circ$                      | 24$^\circ$                      | 24$^\circ$  |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
|                                    | Intensity         | 0.35                    | 0.71                    | 0.13                    | 0.08                            | 0.81                            | $-$         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
|                                    | \<$V_\text{z}$\>  | 1.2                     | 1.1                     | 1.7                     | 1.4                             | 0.6                             | 1.1         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| SW                                 | Rms($V_\text{z}$) | 1.7                     | 1.5                     | 1.7                     | 1.8                             | 1.7                             | 1.6         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| $-$2\<$V_\text{z}$\<5 km s$^{-1}$  | \<$\omega$\>      | 232$^\circ$             | 230$^\circ$             | 220$^\circ$             | 214$^\circ$                     | 216$^\circ$                     | 227$^\circ$ |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| 180$^\circ$\<$\omega$\<270$^\circ$ | Rms($\omega$)     | 24$^\circ$              | 23$^\circ$              | 19$^\circ$              | 24$^\circ$                      | 24$^\circ$                      | 22$^\circ$  |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
|                                    | Intensity         | 0.59                    | 2.19                    | 0.12                    | 0.04                            | 0.61                            | $-$         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
|                                    | \<$V_\text{z}$\>  | 0.6                     | 1.0                     | 1.0                     | $-$                             | 0.5                             | 0.8         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| NW                                 | Rms($V_\text{z}$) | 1.6                     | 1.5                     | 1.0                     | $-$                             | 1.7                             | 1.5         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| $-$2\<$V_\text{z}$\<5 km s$^{-1}$  | \<$\omega$\>      | 305$^\circ$             | 305$^\circ$             | 306$^\circ$             | $-$                             | 312$^\circ$                     | 305$^\circ$ |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| 270$^\circ$\<$\omega$\<360$^\circ$ | Rms($\omega$)     | 25$^\circ$              | 21$^\circ$              | 12$^\circ$              | $-$                             | 25$^\circ$                      | 22$^\circ$  |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
|                                    | Intensity         | 0.62                    | 2.19                    | 0.02                    | $-$                             | 0.53                            | $-$         |
+------------------------------------+-------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| Beam                                                   | 43$\times$36/33$^\circ$ | 47$\times$44/40$^\circ$ | 46$\times$38/34$^\circ$ | 46$\times$37/34$^\circ$         | 49$\times$44/$-$11$^\circ$      | $-$         |
+--------------------------------------------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| Noise                                                  | 0.8                     | 0.7                     | 0.5                     | 0.8                             | 2.1                             | $-$         |
+--------------------------------------------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| Total intensity                                        | 1.56                    | 5.09                    | 0.27                    | 0.12                            | 1.95                            | $-$         |
+--------------------------------------------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+
| Share SE/SW/NW (%)                                     | 22/38/40                | 14/43/43                | 48/44/7                 | 67/33/0                         | 42/31/27                        | $-$         |
+--------------------------------------------------------+-------------------------+-------------------------+-------------------------+---------------------------------+---------------------------------+-------------+

In order to comment on these results, and to suggest plausible interpretations, we shall use the predictions of a local thermal equilibrium (LTE) regime as a reference with which to compare our results. We recall the relevant arithmetic in the following sub-section.

![image](figures/fig8a_x51c2_29sio54_channelmap.eps) ![image](figures/fig8b-vzomg-29sio-r.04-.3.eps) ![image](figures/fig8c-vzrxy-29sio.eps)

![image](figures/fig9a_x51c2_co21_channelmap.eps) ![image](figures/fig9b-vzomg-co-r.04-.3.eps) ![image](figures/fig9c-vzrxy-co.eps)

## LTE approximation and temperature dependence

In the LTE approximation, for a given velocity $V_\text{z}$ and a brightness $I_0$ \[Jy arcsec$^{-2}$\] on the entrance side of a slab of thickness d$z$\[arcsec\], density $n$\[molecules cm$^{-3}$\] and temperature $T$\[K\], the brightness $I$ \[Jy arcsec$^{-2}$\] at the exit side, reads $$\begin{equation}
  I=I_0e^{-\tau}+\varepsilon(1-e^{-\tau})/\tau =\varepsilon/\tau+(I_0-\varepsilon/\tau)e^{-\tau}
\end{equation}$$

where $\varepsilon$ describes the unabsorbed emission of the slab, and $\tau$ its opacity. $$\begin{align}
  \varepsilon&={(hc)/(4\pi\Delta{V})}A_\text{ji}f_\text{pop}n \text{d}z \\
          &=\frac{0.558\,10^6}{\Delta{V}\text{[km s$^{-1}$]}} A_\text{ji}\text{[Hz]} f_\text{pop} n\text{[mol. cm$^{-3}$]} \text{d}z\text{[arcsec]} d\text{[pc]}
\end{align}$$

Here, $h$ is the Planck constant, $c$ the light velocity, $\Delta{V}$ the FWHM of the line profile, $A_\text{ji}$ the Einstein coefficient, $n$ the density and $d$ the distance of the star from Earth; $$\begin{equation}
  f_\text{pop}=(2J+1)e^{-E_\text{u}/T}/Q
\end{equation}$$ where $J$ and $E_\text{u}$\[K\] are the angular momentum quantum number and energy of the upper level and $Q=T/k$ is the partition function. Parameters $A_\text{ji}$, $E_\text{u}$ and $k$ are given in Table [\[tab2\]](#tab2) together with the frequency $f$. The opacity is given by the relation ($\Delta{E}$ is the energy of the transition): $$\begin{align}
  \tau&=\frac{c^2}{2h} \varepsilon \frac{e^{\Delta E/T}-1}{f^3}\\
  &=2.88\,10^7 \varepsilon \mbox{[Jy arcsec$^{-2}$]}\frac{e^{\Delta E/T}-1}{f\mbox{[GHz]}^3}.
\end{align}$$

![image](figures/fig10a_x51c2_so5544_channelmap.eps) ![image](figures/fig10b-vzomg-so-r.04-.3.eps) ![image](figures/fig10c-vzrxy-so.eps)

![image](figures/fig11a_so2-22_channelmap.eps) ![image](figures/fig11b-vzomg-so2band6-r.04-.3.eps) ![image](figures/fig11c-vzrxy-so2band6.eps)

![image](figures/fig12a_rleo-chmap-so2-13.eps) ![image](figures/fig12b-vzomg-so2band7-r.04-.3.eps) ![image](figures/fig12c-vzrxy-so2band7.eps)

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

[^3]: https://casa.nrao.edu/

[^4]: https://www.iram.fr/IRAMFR/GILDAS/

[^5]: https://imager.oasu.u-bordeaux.fr/

Neglecting opacity and the temperature dependence of $k$, the temperature dependence of $\varepsilon$ is governed by a factor $f_\text{T}=e^{-E_\text{u}/T}/T$: for $T>>E_\text{u}$, $f_\text{T}\sim1/T$ independently from $E_\text{u}$. When comparing two lines, the ratio of the two factors is $f_\text{T1}/f_\text{T2}$=e$^{(E_\text{u2}-E_\text{u1})/T}$. To the extent that we deal with temperatures in excess of $\sim$200 K, this ratio is between $\sim$0.7 and 1 for most lines: we cannot expect temperature to cause important differences between the relative line emissions. The only exception is the SO$_2$(22$_{2,20}$-22$_{1,21}$) line, for which $f_\text{T}$(SO$_2$)/$f_\text{T}$(CO)=e$^{-231/T}$, namely $\sim$0.3 at 200 K and $\sim$0.1 at 100 K.

We also remark that the ratio of opacity to unabsorbed emissivity, $\tau/\epsilon$, is proportional to (e$^{\Delta{E}/T}-1$)/$f^3$. For $\Delta{E}<<T$, $\tau/\epsilon$ is therefore inversely proportional to temperature and to the square of the frequency, namely $\sim$2.5 times smaller for Band 7 than for Band 6 data.

## Discussion of the results

We are now in a position to discuss the results summarised in Table [\[tab4\]](#tab4). Averaging over the five lines, the mean velocity \<$V_z$\> of the emission of the SE region is blue-shifted by 0.8 km s$^{-1}$, that of the SW region red-shifted by 1.1 km s$^{-1}$ and that of the NW region red-shifted by 0.8 km s$^{-1}$. Even if the outflows are inclined by as little as 10$^\circ$ with respect to the plane of the sky, their mean space velocity does not exceed $\sim$6 km s$^{-1}$: we are dealing with slow streams, which barely overcome the star gravity (the escape velocity from a 0.7 solar mass star at an angular distance of 300 mas from its centre is $\sim$6 km s$^{-1}$). In each region, the rms deviations of $V_z$ and $\omega$ from their mean is $\sim$80% of the value corresponding to a uniform distribution, showing that the selected regions cover well the observed outflows.

A first important remark is that emission is shared very differently between the different regions. While the CO(2-1) and $^{29}$SiO(5-4) lines display similar shares between the three regions (on average, 18%/41%/41% in SE/SW/NW, respectively), the shares of the SO and SO$_2$ lines are very different, with strong dominance in the SE region and, in the case of the Band 6 lines (SO(5$_5$-4$_4$) and SO$_2$(22$_{2,20}$-22$_{1,21}$)), near absence in the NW region. Such important differences challenge interpretation.

The Band 7 SO$_2$-HCN line is a blend of the SO$_2$(13$_{2,12}$-12$_{1,11}$) line with the H$^{13}$CN(4-3) line, which is blue-shifted by $\sim$1.1 km s$^{-1}$ with respect to the SO$_2$ line. Figure [2](#fig14) displays the observed radial dependence of the intensities of the SO$_2$(22$_{2,20}$-22$_{1,21}$) and SO$_2$-HCN emissions. While the latter remains at an approximate level of 2-5 Jy arcsec$^{-2}$ km s$^{-1}$ over the whole $R$ range (60 to 300 mas) in each of the three regions, the former drops rapidly when $R$ increases and nearly vanishes in the NW region. This suggests that HCN emission dominates over SO$_2$ emission over most of the $R$ range and that SO and SO$_2$ emissions are both strongly depressed in the western hemisphere, nearly absent in the NW region. In the remaining of the article, we take it as granted that such is the case. Accordingly, we interpret the emission of the SO$_2$-HCN line as dominated by emission of the H$^{13}$CN(4-3) line for $R$\>$\sim$0.15 arcsec and the emissions of the SO(5$_5$-4$_4$), SO$_2$(22$_{2,20}$-22$_{1,21}$) and SO$_2$(13$_{2,12}$-12$_{1,11}$) lines as being confined within $\sim$0.15 arcsec from the centre of the star, as illustrated in the lower panels of Figure [2](#fig14). Such confinement is at strong variance with the much broader radial distributions assumed by (cite: Danilovich2016), (cite: VandeSande2020) and (cite: Massalkhi2020) and its vicinity from continuum emission prevents a reliable study. The similarity between the SO and SO$_2$ emissions supports the assumption that SO$_2$ is essentially produced (cite: Cherchneff2006) via the reaction: $$\begin{equation}
   \text{SO+OH} \longrightarrow \text{SO}_2+\text{H}
\end{equation}$$ and suggests that SO and SO$_2$ molecules are destroyed by the same mechanism. However, the observed confinement is not expected. As remarked by (cite: Massalkhi2020) photodissociation by UV radiation is equally probable for SO and SiO molecules: Figure [2](#fig14) excludes an interpretation of the confinement in terms of photodissociation of the SO and SO$_2$ molecules. Confinement within 1-2 stellar radii (60-150 mas) is predicted by chemical models for carbon-rich stars, the absence of OH molecules at larger distances preventing formation of SO molecules via the reaction (cite: Cherchneff2006): $$\begin{equation}
  \text{S+OH} \longrightarrow \text{SO+H}
\end{equation}$$

However, as soon as C/O falls below unity, SO formation extends well beyond 5 stellar radii (60-150 mas). (cite: Agundez2020) use a chemical equilibrium model that predicts confinement within 5-10 stellar radii for Mira stars, however with uncertainties at the level of an order of magnitude.

To get some insight into the effect of opacity, we display in Figure [3](#fig15) Doppler velocity spectra observed over the stellar disc ($R$\<30 mas) and around it (30\<$R$\<50 mas). In the ring around the stellar disc, where the continuum level is $\sim$17% of its value over the stellar disc, absorption is weak and indicates that opacity corrections in the radial range covered by Table [\[tab4\]](#tab4) are small. As expected, absorption is much stronger over the stellar disc. In percentage of the continuum level, it reaches $\sim$70% at $V_z$$\sim$$-$3 km s$^{-1}$ for $^{29}$SiO(5-4) and $\sim$24% at $V_z$$\sim$6 km s$^{-1}$ for CO(2-1). These differences reveal different contributions from out-flowing and in-falling gas, depending on the radial range being probed and are briefly discussed in the next subsection.

In order to perform a more quantitative analysis of the observed intensities listed in Table [\[tab4\]](#tab4), we use the LTE description as reference. In the radial range covered by Table [\[tab4\]](#tab4), 60 to 300 mas, we expect the temperature to decrease from $\sim$1300-1500 K to $\sim$300-500 K (cite: Fonfria2020) and the factor e$^{-Eu/T}$ is close to unity. We calculate accordingly, for each of the three regions and for each line, the ratio between the observed intensity (Table [\[tab4\]](#tab4)) and the factor $F=A_{ji}(2J+1)k\text{e}^{-Eu/T}$ calculated at $T$=1000 K using the line parameters listed in Table [\[tab2\]](#tab2). In the LTE approximation, neglecting absorption, this ratio is proportional to the abundance of the excited molecule, namely to the global density in each region and to the relative molecular abundances. The latter are particularly informative as they reveal important differences between the different lines. We list in Table [\[tab5\]](#tab5), for each region and for each line, the calculated ratio of the relevant molecular abundance to the $^{29}$SiO abundance chosen as reference. We also list, in the same table, abundances obtained from single dish observations using broad and isotropic radial distributions. The main results can be summarized as follows:

\(i\) The observed CO/SiO abundance ratios are within $\pm$30% equal to the abundance ratios obtained from single dish observations, 30% larger in the SE region, 30% smaller in the SW and NW regions. This implies that within the large uncertainties attached to these evaluations, absorption and deviations from an LTE regime do not much influence the evolution of the outflows. Namely the presence of shocks suggested by studies of continuum emission and molecular abundances is confined to the very close neighbourhood of the star, well within 60 mas. Yet, small differences between different regions of the CO/SiO abundance ratio would not be surprising as the SiO emission is more sensitive to temperature than the CO emission, making SiO a good shock tracer.

\(ii\) The observed SO/SiO and SO$_2$/SiO abundance ratios are much smaller in the western hemisphere, and particularly in the NW region, than in the SE region. However, the confinement of the SO and SO$_2$ molecules within $\sim$0.15 arcsec from the centre of the star, for which strong evidence has been obtained, makes a reliable quantitative analysis difficult. As clearly illustrated in Figures [\[fig10\]](#fig10) and [\[fig11\]](#fig11), the emission of these molecules does not extend radially much beyond continuum emission: better angular resolution and sensitivity would be required for a reliable analysis.

\(iii\) The observed H$^{13}$CN/$^{29}$SiO abundance ratio, evaluated by assuming that H$^{13}$CN emission dominates over SO$_2$ emission in the NW region, is $\sim$7%. It corresponds to a relative abundance of H$^{12}$CN of $\sim$10$^{-6}$, $\sim$4 times larger than obtained from single dish analyses. This is consistent with observations in the other regions, but a reliable evaluation of the HCN abundance in the SE region would require observing the emission of other, unblended, lines.

+---------------------------------------------+------------------------+-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+
| Line                                        | CO(2-1)                | $^{29}$SiO(5-4)         | H$^{13}$CN(4-3)          | SO(5$_5$-4$_4$)          | SO$_2$(22$_{2,20}$-22$_{1,21}$) | SO$_2$(13$_{2,12}$-12$_{1,11}$) |
+:==========================:+:==============:+:======================:+:=======================:+:========================:+:========================:+:===============================:+:===============================:+
| Abundance                                   | 2$\times$10$^{-4}$ (a) | 13$\times$10$^{-6}$ (a) | 2.5$\times$10$^{-7}$ (b) | 6.7$\times$10$^{-6}$ (c) | 5$\times$10$^{-6}$ (c)          | 5$\times$10$^{-6}$ (c)          |
+---------------------------------------------+                        +-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+
| ($f_0=n/n_{H2}$)                            |                        | $\times$0.08 (e)        | $\times$0.08 (e)         | 6.6$\times$10$^{-7}$ (g) | \<1.1$\times$10$^{-7}$ (g)      | \<1.1$\times$10$^{-7}$ (g)      |
+---------------------------------------------+------------------------+-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+
| $A_{\text{SiO}}$ Single dish                | 192                    | 1                       | 0.019                    | 6.4 (c)/0.6 (g)          | 4.8 (c)/\<0.11 (g)              | 4.8 (c)/\<0.11 (g)              |
+---------------------------------------------+------------------------+-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+
| $F$                                         | 8.92$\times$10$^{-3}$  | 4.53                    | 14.3                     | 0.44                     | 0.069                           | 0.124                           |
+----------------------------+----------------+------------------------+-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+
| A$_{\text{SiO}}$ this work | SE             | 250                    | 1                       | \< 0.36                  | 1.9                      | 7.2                             |                                 |
|                            +----------------+------------------------+-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+
|                            | SW             | 140                    | 1                       | \<0.089                  | 0.6                      | 1.2                             |                                 |
|                            +----------------+------------------------+-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+
|                            | NW             | 140                    | 1                       | \<0.076                  | 0.1                      | 0                               |                                 |
+----------------------------+----------------+------------------------+-------------------------+--------------------------+--------------------------+---------------------------------+---------------------------------+

Finally, we remark that the complexity of the observed morpho-kinematics prevents confirmation of two predictions made earlier by (cite: Fonfria2019b) and (cite: Wiesemeyer2009). The former authors speculated that the high resolution CO(2-1) observations might suggest the presence of rotation in the close neighbourhood of the star. It is difficult, however (see Figure [\[fig9\]](#fig9)), to separate a possible effect of rotation from the contribution of the south-western outflow and evidence for a possible rotation cannot be stated with reasonable confidence. The latter authors have given arguments in favour of the presence of an evaporating Jovian planet orbiting R Leo at some 30 mas from its centre. According to their definition of the orbit parameters, such a planet would have been south-east of the star at the time of the present observations and blue-shifted by some 4-5 km s$^{-1}$, in a region where we observe no feature that might be revealing its presence: again, speculation about the possible presence of a planet cannot be made with reasonable confidence from the present observations.

![image](figures/fig13a-map-vz6.eps) ![image](figures/fig13b-spect-3regions.eps)

![image](figures/fig14-rdist-3regions.eps) ![image](figures/fig13new-rdist-3regions.eps)

## Summary

In summary, within 300 mas from the centre of the star, we observe a very complex morpho-kinematics giving evidence for anisotropic emission and, within 40 mas from the centre of the star, we find evidence for simultaneous presence of outflowing and in-falling gas. Similar features have been observed previously in several other oxygen-rich AGB stars, such as R Dor (cite: Hoai2020; Nhung2021), W Hya (cite: Hoai2021; Vlemmings2017) and $o$ Ceti (cite: Wong2016; Khouri2018; Nhung2022a). The angular and radial distributions of the pattern of in-falling and out-flowing gas, its evolution as a function of stellar phase, and how it is influenced by anisotropy, cannot be accurately predicted in the present state of our understanding. In particular the radial range over which the simultaneous presence of in-falling and out-flowing gas contributes to line broadening cannot be precisely defined. In the present case of R Leo, Figure [3](#fig15) has shown that Doppler velocities reaching beyond 10 km s$^{-1}$ are observed over the stellar disc for the $^{29}$SiO(5-4), CO(2-1) and SO(5$_5$-4$_4$) lines. They decrease to $\sim$10 km s$^{-1}$ for $R$ between 30 and 50 mas and reach terminal values of $\sim$5 km s$^{-1}$ for $R$ beyond $\sim$100 mas (Figure [4](#fig16)). In the case of $o$ Ceti (cite: Nhung2022a), at a distance of 100 pc instead of 114 pc for R Leo, a similar decrease is observed, from $\sim$20 km s$^{-1}$ to $\sim$6 km s$^{-1}$ between $\sim$ 50 mas and $\sim$ 150 mas. However, while $o$ Ceti displays approximate isotropy in this radial range, R Leo shows important anisotropy, with much stronger emission in the southern than northern hemisphere.

The diversity of patterns displayed in Figure [3](#fig15) suggests that the SO$_2$(22$_{2,20}$-22$_{1,21}$) line probes too high temperatures and/or too small abundances to reveal significant absorption, while the CO(2-1) line probes too large distances to reveal important anisotropy. The different patterns displayed by in-falling gas are more difficult to interpret. (cite: Fonfria2019b) have commented on the cases of the CO(2-1) and $^{29}$SiO(5-4) lines, both in the $\nu$=0 and $\nu$=1 lines, and underscored the complexity of the implied morpho-kinematics.

![image](figures/fig15a-spect-disc-3.eps) ![image](figures/fig15b-spect-disc-1.eps) ![image](figures/fig15c-spect-disc-2.eps) ![image](figures/fig15d-spect-disc-8.eps) ![image](figures/fig15e-spect-disc-4.eps)

Three slow gas streams have been identified, covering projected angular distances from the centre of the star of up to $\sim$400 mas with rms spread in $V_z$ and $\omega$ of typically 1.5 km s$^{-1}$ and 22$^\circ$, respectively. Beyond 40 mas angular separation from the centre of the star, the emissions of the CO(2-1), $^{29}$SiO(5-4) and H$^{13}$CN(4-3) molecular lines do not reveal major anomaly when compared with LTE predictions, showing neither strong absorption contributions nor important deviations from an LTE regime. This is at variance with the regime at stake within 40 mas, known to host shocks and turbulences from the study of continuum emission (cite: Vlemmings2019) and of the non-equilibrium chemistry required to explain the molecular abundances of species formed in this radial range (cite: Bieging2000; Schoier2013; Massalkhi2020). In contrast with the CO(2-1), $^{29}$SiO(5-4) and H$^{13}$CN(4-3) line emissions, the SO(5$_5$-4$_4$) and SO$_2$(22$_{2,20}$-22$_{1,21}$) line emissions display features, which current chemical models fail to explain. While the evidence for similar confinement of both SO and SO$_2$ molecules within $\sim$0.15 arcsec from the centre of the star in each of the three outflows can be stated with confidence, a reliable quantitative study would require new observations and a better understanding of the chemistry at stake.

![image](figures/fig16a-spect-co.eps) ![image](figures/fig16b-spect-sio.eps)

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

# Vibrationally excited SiO lines

The emissions of the vibrationally excited SiO lines, $^{28}$SiO($\nu$=1,5-4) and $^{28}$SiO($\nu$=2,5-4) in Band 6 and $^{28}$SiO($\nu$=1,8-7) in Band 7, when compared to that of the $^{29}$SiO($\nu$=0,5-4) line, probe higher temperature regions closer to the star (Table [\[tab2\]](#tab2)). Accounting for the $^{29}$SiO/$^{28}$SiO isotopic ratio, the LTE values of the $J$=5-4 line intensities for $\nu$=0 and $\nu$=1 are equal for a temperature $T$$\sim$700 K and in a ratio $\sim$1/5 for $T$=2000K. Figures [1](#fig17) to [3](#fig19) display the same information for these lines as Figure [\[fig8\]](#fig8) does for the ground state. The emission of the $\nu$=1 lines is dominantly north, evolving from north-east in the blue-shifted hemisphere to north-west in the red-shifted hemisphere, and is largely confined within 100 mas from the centre of the star, reaching up to 200 mas for the $J$=8-7 line. The emission of the $\nu$=2 line is limited to a small region of the emission of the $\nu$=1 lines, north of the star, with a mean Doppler velocity of $\sim$$-$5 km s$^{-1}$ and confined within $\sim$80 mas. When inspected along $V_\text{z}$, the emission is seen to consist of three different components at mean Doppler velocities of $\sim$$-$8 to $-$2 km s$^{-1}$, $\sim$$-$2 to 2 km s$^{-1}$ and $\sim$4 to 8 km s$^{-1}$, respectively.

![image](figures/fig17a_x51c2_siov154_channelmap.eps) ![image](figures/fig17b-vzomg-siov1-r.04-.3.eps) ![image](figures/fig17c-vzrxy-siov1.eps)

![image](figures/fig18a_x51c2_siov254_channelmap.eps) ![image](figures/fig18b-vzomg-siov2-r.04-.3.eps) ![image](figures/fig18c-vzrxy-siov2.eps)

![image](figures/fig19a_chmap-siov187-new.eps) ![image](figures/fig19b-vzomg-sio87-r.04-.3.eps) ![image](figures/fig19c-vzrxy-sio87.eps)

Figure [4](#fig20) (left) illustrates the peculiarity of the $^{28}$SiO($\nu$=1,5-4) emission by comparing its Doppler velocity spectrum, integrated within $R$\<0.3 arcsec, with those of the $\nu$=0 and $\nu$=2 lines: its emission is an order of magnitude more intense and it covers a much broader interval of Doppler velocities, reaching beyond $\sim$$\pm$16 km s$^{-1}$. From Table [\[tab2\]](#tab2), the LTE approximation predicts the intensity of the $\nu$=1, $J$=8-7 line to be a factor $\sim$7 larger than that of the $\nu$=1, $J$=5-4 line in the optically thin limit and $\sim$2.5 times larger in the optically thick limit, while in fact it is over 3 times smaller (Figure [4](#fig20), centre). Such features are evidence for masing (cite: Gray2009), the latter probably being an effect of the wavelength dependence of the stimulated emission probability.

Indeed, the emission of the $\nu$\>0 lines is known to host strong masers, the amplitude of which is highly variable. As was mentioned in the introduction, they have been the subject of numerous outstanding VLBA observations. As remarked by (cite: Cotton2009), they appear within a few stellar radii of the stellar surface, typically $\sim$30 mas from the centre of the star, between the hot inner envelope and the cooler region where the dust forms. They tend to occur in clumpy, partial rings centred on the star.

The presence of masers does not simply trace local SiO abundance but is a function of the conditions for population inversion and the direction of maser beaming. Their amplification depends on the length of the path over which they can develop, and therefore takes values that are difficult to predict. The blue-and red-shifted emissions observed in the present case may reveal the presence of an expanding layer of gas reminiscent of the contemporaneous observation (October 3 and 11 instead of September 21 and October 27) of the extended atmosphere made by (cite: Vlemmings2019) within 1-2 stellar radii. These authors model the continuum emission with a uniform elliptical stellar disc and find a temperature of $\sim$1900$\pm$100 K at an angular separation of $\sim$22 mas from the centre of the star. The continuum emission probes the same radial range as do the $\nu$=1 and $\nu$=2 SiO lines and these authors model their observations as emission from an increased opacity layer expanding at a radial velocity of $\sim$10.6 km s$^{-1}$. If the actual expansion velocity of the SiO masers seen on the $\nu$=1 line is the same as the 10.6 km s$^{-1}$ inferred for the continuum, then a $|V_z|\sim$6 km s$^{-1}$ would place the masing clumps at an inclination angle of 30-40$^\circ$ with respect to the plane of the sky. The right panel of Figure [4](#fig20) sketches the corresponding geometry. The maximum SiO velocity (Figure [\[fig16\]](#fig16) and left panels of Figure [4](#fig20)) is $\sim$10 km s$^{-1}$, which is consistent with this picture. The clumpy nature of the emission (north in the blue-shifted hemisphere and north-west in the red-shifted hemisphere) cannot be simply interpreted in terms of gas density but simply reveals regions where masers are more intense.

No significant absorption can be revealed above and around the stellar disc (Figure [5](#fig21)), in strong contrast with the $\nu$=0 lines (Figure [\[fig15\]](#fig15)), the $\nu$\>0 lines probing a region where masing is important and where the gas is too hot to absorb strongly, as was already the case for the SO$_2$(22$_{2,20}$-22$_{1,21}$) line (Section 5.2).

![image](figures/fig20a-spect-sio-band6.eps) ![image](figures/fig20b-spect-sio-v1.eps) ![image](figures/fig20c-picture.eps)

![image](figures/fig21a-spect-disc-6.eps) ![image](figures/fig21b-spect-disc-7.eps) ![image](figures/fig21c-spect-disc-5.eps)

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

# Conclusions

A global view of the morpho-kinematics of the circumstellar envelope of R Leo has been presented, which complements earlier studies. In short, it distinguishes between four regions covering different radial ranges: within $\sim$2 stellar radii, using continuum emission and $\nu$\>0 maser lines as probes, evidence is found for an expanding shell with a radial velocity of $\sim$10 km s$^{-1}$; between $\sim$2 and $\sim$10 stellar radii, in a region probed in particular by the emission of SO and SO$_2$ $\nu$=0 molecular lines and hosting in its inner part both in-falling and outflowing gas, evidence is found for a non-LTE regime suggesting that shocks play an important role; between $\sim$10 and $\sim$30 stellar radii, in a region probed in particular by the $\nu$=0 emission of SiO, CO and HCN molecules and hosting three distinct outflows, LTE becomes progressively dominant; beyond $\sim$30 stellar radii, in a region probed by the emission of CO molecules, evidence is found for patchy and episodic mass ejection, with an enhanced layer of emission having a mean radial velocity of $\sim$5.5 km s$^{-1}$ and a mean angular separation from the centre of the star of $\sim$6 arcsec.

At variance with preliminary analyses presented by (cite: Fonfria2019a; Fonfria2019b), we have shown that continuum emission is nearly circular and gives insufficient evidence to claim, or refute, the possible presence of an evaporating Jovian planet and/or of rotation in the close neighbourhood of the star. Instead, we give evidence for three distinct outflows, each covering a solid angle at steradian scale,which have been described in detail in Section 5. As they cover nearly 400 mas in projected angular distance from the centre of the star, and have a space velocity expected to not significantly exceed $\sim$6 km s$^{-1}$, they have been present for several decades. While it is tempting to associate such outflows with possible convective cells on the surface of the star, this seems an order of magnitude longer time than the expected lifetime of a given granulation pattern, underscoring the lack of detailed understanding of the mechanism at stake. A study of the relative abundances of the molecular species present in these outflows has revealed an unexpected confinement of SO and SO$_2$ molecules within $\sim$0.15 arcsec from the centre of the star, suggesting a complex competition between chemical reactions contributing to the formation and destruction of the parent SO molecules. The similar morpho-kinematics at stake for the emission of the SO and SO$_2$ molecules has given support that the latter are dominantly produced by oxygenation of the former. Evidence for different SO/SiO ratios in each of the three outflows is strong (lower panels of Figure [\[fig14\]](#fig14)) suggesting that at the short distances probed by the SO and SO$_2$ molecules, LTE does not apply and shocks are likely to play a significant role.

In contrast with SO and SO$_2$ molecules, the relative abundances of the CO, SiO and HCN molecules are consistent, within large uncertainties, with expectation.

Very close to the star, evidence for the simultaneous presence of expanding and in-falling gas, reminiscent of observations made in several other oxygen-rich AGB stars, has been presented and commented. A study of vibrationally excited SiO lines, expected to host important masers, has been shown in Section 6 to probe an expanding layer of hot gas, just above the photosphere, consistent with earlier studies by (cite: Vlemmings2019).

At larger distances from the star, where depletion of the SiO molecules by condensation on dust grains and photo-dissociation of the SiO, SO and SO$_2$ molecules are expected to be significant, the CO line emission traces the mass loss history over the past few centuries, giving evidence for a very patchy morpho-kinematics with inhomogeneity at the level of $\sim$40%, and revealing an episode of enhanced mass-loss seen as a layer of increased emission at a mean distance of 6 arcsec from the centre of the star and an expansion velocity reaching up to 9 km s$^{-1}$ and having an average value of $\sim$5.5 km s$^{-1}$. An escape velocity of 6 km s$^{-1}$ from a 0.7 solar mass star is reached at $\sim$300 mas: some acceleration is therefore necessary after the initial boost. Understanding its nature requires independent information about dust formation. The dust emission coefficient in the mid-infrared is known to be low (cite: Sloan1998) and (cite: Paladini2017), using VLTI/MIDI observations, remark that R Leo displays no significant 8 $\mu$m silicate feature in its spectrum and speculate that the important brightness asymmetry supports a large grain scenario of dust formation.

We noted the presence of patches of emission inside the shell, in particular of some arcs that may suggest the presence of spirals associated with the wake emission of a companion; however, we have shown that such an interpretation cannot be reliably supported or refuted from the present data alone.

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

The complexity of the observed morpho-kinematics, which had been underscored by all earlier studies, together with the strong anisotropy of line emission ratios, provide evidence for non-equilibrium chemistry, supporting the role played by shocks and/or density and temperature inhomogeneity in the generation of the nascent wind. But it also makes it hard to develop accurate, comprehensive models with confidence, restricting reliable interpretations to considerations based on very crude and approximate modelling. When observed in sufficient detail, the inner layers of the circumstellar envelopes of oxygen-rich AGB stars are all different. Their observation shows the importance of collecting a sufficient sample to be able to interpret reliably their diversity in terms of state-of the art simulations such as proposed by (cite: Hofner2019), in particular for being able to describe more precisely the role played by convective cells in defining the pattern of mass ejections. While such simulations provide a useful framework in which to describe the mechanisms at stake in the genesis of the nascent wind, many questions remain unanswered, requiring new observations: How does the pattern of outflows depend on the stellar phase? What distinguishes outflows lasting for a few decades from mass ejections covering only a few years? What causes the CSE to retain, in some cases, a same axial symmetry over centuries? An accurate model of the morpho-kinematics of the observed line emissions in the neighbourhood of the star should be able to define precisely the angular size and time duration of the patches of emission associated with the convective cell granulation, but we are still far from such achievement.

# Acknowledgements

We are deeply indebted and grateful to the referee, Dr Anita Richards, for a very careful reading of the manuscript and pertinent comments that helped greatly with improving both the form and the substance of the present article. We thank Dr Stéphane Guilloteau for guidance in producing Table 2. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01202.S, ADS/JAO.ALMA#2017.1.00862.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We are deeply indebted to the ALMA partnership, whose open access policy means invaluable support and encouragement for Vietnamese astrophysics. Financial support from the World Laboratory, the Odon Vallet Foundation and the Vietnam National Space Center is gratefully acknowledged. This research is funded by the Vietnam National Foundation for Science and Technology Development (NAFOSTED) under grant number 103.99-2019.368.

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

# Data Availability

The raw data are available on the ALMA archive: ADS/JAO.ALMA#2016.1.01202.S and ADS/JAO.ALMA#2017.1.00862.S. The calibrated and imaged data underlying this article will be shared on reasonable request to the corresponding author.

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

[^1]: E-mail: dthoai@vnsc.org.vn

[^2]: E-mail: pttnhung@vnsc.org.vn

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Define three 3D data cube regions (SE, SW, NW) between R = 60 and 300 mas, each with volume 0.48 arcsec^2 km s^-1, and compute the integrated intensity, mean and rms Doppler velocity <V_z>, and mean and rms position angle <omega> for CO(2-1), 29SiO(5-4), SO(5_5-4_4), SO2(22_2,20-22_1,21), and SO2(13_2,12-12_1,11)/H13CN(4-3).",
  "failed_quote": "In order to compare quantitatively the emissions of the five lines, we define three regions, called SE, SW and NW, with angular separations from the centre of the star between 60 and 300 mas, covering $V_z$ and $\\omega$ ranges listed in Table 4."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Calculate the ratio of observed intensity in each region (SE, SW, NW) to the LTE factor F = A_ji (2J+1) k exp(-E_u/T) evaluated at T = 1000 K, and normalize to the 29SiO abundance as reference.",
  "failed_quote": "We calculate accordingly, for each of the three regions and for each line, the ratio between the observed intensity (Table 4) and the factor $F=A_{ji}(2J+1)k\\text{e}^{-Eu/T}$ calculated at $T$=1000 K using the line parameters listed in Table 2."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "Reference temperature T = 1000 K; F = 8.92e-3 (CO(2-1)), 4.53 (29SiO(5-4)), 14.3 (H13CN(4-3)), 0.44 (SO(5_5-4_4)), 0.069 (SO2(22_2,20-22_1,21)), 0.124 (SO2(13_2,12-12_1,11))",
  "failed_quote": "We calculate accordingly, for each of the three regions and for each line, the ratio between the observed intensity (Table 4) and the factor $F=A_{ji}(2J+1)k\\text{e}^{-Eu/T}$ calculated at $T$=1000 K using the line parameters listed in Table 2."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Map channel maps, PV diagrams, and Doppler velocity spectra integrated within R < 0.3 arcsec and over the stellar disc (R < 30 mas and 30 < R < 50 mas) for 28SiO(v=1,5-4), 28SiO(v=2,5-4), and 28SiO(v=1,8-7), and compare line ratios with LTE predictions.",
  "failed_quote": "From Table 2, the LTE approximation predicts the intensity of the $\\nu$=1, $J$=8-7 line to be a factor $\\sim$7 larger than that of the $\\nu$=1, $J$=5-4 line in the optically thin limit and $\\sim$2.5 times larger in the optically thick limit, while in fact it is over 3 times smaller (Figure 4, centre)."
 },
 {
  "path": "claims[3].evidence[0]",
  "value": "Vibrationally excited SiO lines undergo strong maser amplification and probe the northern/north-western parts of the hot expanding gas layer near the stellar disc.",
  "failed_quote": "From Table 2, the LTE approximation predicts the intensity of the $\\nu$=1, $J$=8-7 line to be a factor $\\sim$7 larger than that of the $\\nu$=1, $J$=5-4 line in the optically thin limit and $\\sim$2.5 times larger in the optically thick limit, while in fact it is over 3 times smaller (Figure 4, centre)."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Rotating torus in the close neighbourhood of the star (Fonfria et al. 2019b): cannot be separated with confidence from the contribution of the south-western outflow.",
  "failed_quote": "It is difficult, however (see Figure 9), to separate a possible effect of rotation from the contribution of the south-western outflow and evidence for a possible rotation cannot be stated with reasonable confidence."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[0]",
  "value": "Because SO and SO2 emission is confined within ~0.15 arcsec, close to the bright stellar continuum, a reliable quantitative abundance analysis requires higher angular resolution and sensitivity.",
  "failed_quote": "As clearly illustrated in Figures 10 and 11, the emission of these molecules does not extend radially much beyond continuum emission: better angular resolution and sensitivity would be required for a reliable analysis."
 }
]
```
