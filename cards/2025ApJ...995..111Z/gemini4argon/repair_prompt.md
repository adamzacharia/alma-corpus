# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...995..111Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version November 7, 2025
Typeset using L [A] TEX **twocolumn** style in AASTeX7


**The** **ALMA-ATOMS-QUARKS** **survey:** **Resolving** **a** **chemically** **rich** **massive** **protostellar** **outflow**


[Jia-Hang](http://orcid.org/0009-0000-9090-9960) Zou, [1, 2] Tie [Liu](http://orcid.org/0000-0002-5286-2564), [2] [Fengwei](http://orcid.org/0000-0001-5950-1932) Xu, [3, 4] Xindi [Tang](http://orcid.org/0000-0002-4154-4309), [5] Dezhao Meng, [5, 6, 2] Yan-Kun Zhang, [2]

Aiyuan Yang, [7, 8] Tapas Baug, [9] [Chang-Won](http://orcid.org/0000-0002-4154-4309) Lee, [10, 11] L. [Viktor](http://orcid.org/0000-0002-5310-4212) T´oth, [12, 13] Ariful [Hoque](http://orcid.org/0009-0003-6633-525X), [9] Sami [Dib](http://orcid.org/0000-0002-8697-9808), [14]

Pablo [Garcia](http://orcid.org/0000-0002-8586-6721), [15, 16] [Hong-Li](http://orcid.org/0000-0003-3343-9645) Liu, [1] Prasanta Gorai, [17, 18] Swagat [R.](http://orcid.org/0000-0001-7151-0882) Das, [19] Guido Garay, [15, 19]

Patricio [Sanhueza](http://orcid.org/0000-0002-7125-7685), [20] Li [Chen](http://orcid.org/0009-0009-8154-4205), [1] Di Li, [21] Jihye [Hwang](http://orcid.org/0000-0001-7866-2686) 22, 23 And Dongting Yang 1


The ATOMS-QUARKS collaboration


1 _School_ _of_ _Physics_ _and_ _Astronomy,_ _Yunnan_ _University,_ _Kunming_ _650091,_ _People’s_ _Republic_ _of_ _China_
2 _Shanghai_ _Astronomical_ _Observatory,_ _Chinese_ _Academy_ _of_ _Sciences,_ _80_ _Nandan_ _Road,_ _Shanghai_ _200030,_ _People’s_ _Republic_ _of_ _China_
3 _Max_ _Planck_ _Institute_ _for_ _Astronomy,_ _K¨onigstuhl_ _17,_ _69117_ _Heidelberg,_ _Germany_
4 _Kavli_ _Institute_ _for_ _Astronomy_ _and_ _Astrophysics,_ _Peking_ _University,_ _5_ _Yiheyuan_ _Road,_ _Haidian_ _District,_ _Beijing_ _100871,_ _People’s_
_Republic_ _of_ _China_
5 _Xinjiang_ _Astronomical_ _Observatory,_ _Chinese_ _Academy_ _of_ _Sciences,_ _830011_ _Urumqi,_ _People’s_ _Republic_ _of_ _China_
6 _University_ _of_ _Chinese_ _Academy_ _of_ _Sciences,_ _Beijing_ _100080,_ _People’s_ _Republic_ _of_ _China_
7 _National_ _Astronomical_ _Observatories,_ _Chinese_ _Academy_ _of_ _Sciences,_ _Beijing_ _100101,_ _People’s_ _Republic_ _of_ _China_
8 _Key_ _Laboratory_ _of_ _Radio_ _Astronomy_ _and_ _Technology,_ _Chinese_ _Academy_ _of_ _Sciences,_ _A20_ _Datun_ _Road,_ _Chaoyang_ _District,_ _Beijing,_
_100101,_ _People’s_ _Republic_ _of_ _China_
9 _S._ _N._ _Bose_ _National_ _Centre_ _for_ _Basic_ _Sciences,_ _Block-JD,_ _Sector-III,_ _Salt_ _Lake_ _City,_ _Kolkata_ _700106,_ _India_
10 _University_ _of_ _Science_ _and_ _Technology,_ _Korea_ _(UST),_ _217_ _Gajeong-ro,_ _Yuseong-gu,_ _Daejeon_ _34113,_ _Republic_ _of_ _Korea_
11 _Korea_ _Astronomy_ _and_ _Space_ _Science_ _Institute,_ _776_ _Daedeokdaero,_ _Yuseong-gu,_ _Daejeon_ _34055,_ _Republic_ _of_ _Korea_
12 _Institute_ _of_ _Physics_ _and_ _Astronomy,_ _E¨otv¨os_ _Lor`and_ _University,_ _P´azm´any_ _P´eter_ _s´et´any_ _1/A,_ _H-1117_ _Budapest,_ _Hungary_
13 _Faculty_ _of_ _Science_ _and_ _Technology,_ _University_ _of_ _Debrecen,_ _H-4032_ _Debrecen,_ _Hungary_
14 _Max_ _Planck_ _Institute_ _for_ _Astronomy,_ _K¨onigstuhl_ _17,_ _69117,_ _Heidelberg,_ _Germany_
15 _Chinese_ _Academy_ _of_ _Sciences_ _South_ _America_ _Center_ _for_ _Astronomy,_ _National_ _Astronomical_ _Observatories,_ _CAS,_ _Beijing_ _100101,_ _China_
16 _Instituto_ _de_ _Astronom´ıa,_ _Universidad_ _Cat´olica_ _del_ _Norte,_ _Av._ _Angamos_ _0610,_ _Antofagasta,_ _Chile_
17 _Rosseland_ _Centre_ _for_ _Solar_ _Physics,_ _University_ _of_ _Oslo,_ _PO_ _Box_ _1029_ _Blindern,_ _0315_ _Oslo,_ _Norway_
18 _Institute_ _of_ _Theoretical_ _Astrophysics,_ _University_ _of_ _Oslo,_ _PO_ _Box_ _1029_ _Blindern,_ _0315_ _Oslo,_ _Norway_
19 _Departamento_ _de_ _Astronomia,_ _Universidad_ _de_ _Chile,_ _Las_ _Condes,_ _7591245_ _Santiago,_ _Chile_
20 _Department_ _of_ _Astronomy,_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_ _Bunkyo,_ _Tokyo_ _113-0033,_ _Japan_
21 _Department_ _of_ _Astronomy,_ _Tsinghua_ _University,_ _Beijing_ _100084,_ _People’s_ _Republic_ _of_ _China_
22 _Institute_ _for_ _Advanced_ _Study,_ _Kyushu_ _University,_ _Japan_
23 _Department_ _of_ _Earth_ _and_ _Planetary_ _Sciences,_ _Faculty_ _of_ _Science,_ _Kyushu_ _University,_ _Nishi-ku,_ _Fukuoka_ _819-0395,_ _Japan_


ABSTRACT


We present a comprehensive study on the physical and chemical structures of a chemically rich bipolar
outflow in a high-mass star forming region IRAS 16272 _−_ 4837 (SDC335), utilizing high-resolution
spectral line data at 1.3 mm and 3 mm dual-bands from the ALMA ATOMS and QUARKS surveys.
The high-velocity jet is enveloped by a lower-velocity outflow cavity, containing bright knots that
show enhanced molecular intensities and elevated excitation temperatures. Along the outflow, we
have identified 35 transitions from 22 molecular species. By analyzing the spatial distribution and
kinematics of these molecular lines, we find that the molecular inventory in the outflow is regulated by
three processes: (i) direct entrainment from the natal molecular core by the outflow; (ii) shock-induced
release of molecules or atoms from dust grains; and (iii) thermal desorption and gas-phase reactions
driven by shock heating. These results confirm that outflows are not only dynamical structures but
also active chemical factories, where entrainment, shocks, and thermal processing jointly enrich the
molecular content. Our findings confirmed that outflow chemistry has multi-origin nature, and provide
critical insights into chemical evolution during high-mass star formation.


Corresponding author: Jiahang Zou; Tie Liu


[zojh1000@163.com;](mailto: zojh1000@163.com; liutie@shao.ac.cn) liutie@shao.ac.cn

2


1. INTRODUCTION


Protostellar outflows represent one of the most prominent dynamical phenomena in the early stages of star
formation (F. Motte et al. 2018; C.-F. Lee 2020). Outflows are spectroscopically identified by broad highvelocity wings in molecular lines, and spatially by bipolar red- and blue-shifted lobes centered on the protostar. Some outflows exhibit exceptionally rich molecular line emission, including SiO, CH 3 OH, and various
sulfur- or nitrogen-bearing molecules. The enhanced
abundances of these molecules likely result from nonequilibrium processes induced by shocks, such as ice
mantle desorption and grain sputtering (D. Hollenbach
& C. F. McKee 1989; D. Flower 1994; B. T. Draine
1995). The chemically enriched regions in these “chemically active outflows” provide a unique laboratory for
studying shock-driven chemistry in protostellar environments (M. Tafalla & R. Bachiller 2011; C. Codella et al.
2017; L. Chahine et al. 2024; Y. Oya et al. 2025).
According to current observational and experimental
studies, there are two primary mechanisms that can release complex organic molecule (COMs) from the ice
mantles into the gas phase – (i) thermal desorption and
(ii) dust grain sputtering. In thermal desorption, the
ices sublimate at temperatures around 100 K, fully releasing the trapped molecules into the gas phase (L. A.
Busch et al. 2022; �L. Tychoniec et al. 2021). In such
cases, the observed rotational temperatures are typically
comparable to or higher than the sublimation threshold ( _∼_ 100 K). In the latter scenario, sputtering of dust
grains requires shock events, which typically occur when
the outflowing material collides with the surrounding
dense medium at a high speed. These collisions can liberate molecules from the ice mantles into the gas phase
(P. Caselli et al. 1997). These shock-induced collisions
not only liberate molecules, but also produce line profiles
with broad widths and/or high-velocity emission wings.
In addition, shocks can heat the ambient material and
induce thermal desorption, further enhancing molecular
abundances (H. Miura et al. 2017). As the gas cools
post-shock, the thermal signature may diminish (T. A.
James et al. 2020). Therefore, it is essential to conduct
detailed chemical analysis within molecular outflows to
distinguish from these two different mechanisms.
In recent years, extensive studies have focused on
the chemical characteristics of outflows in low-mass
protostars, often inferring excitation mechanisms from
velocity-resolved molecular line profiles and revealing
that their shock regions can also be chemically rich
(H. G. Arce et al. 2008; K. I. Oberg et al. 2011 [¨] ; E. Mendoza et al. 2014; M. De Simone et al. 2020; S. Feng et al.
2020, 2022; S.-Y. Hsu et al. 2024; Y. Chen et al. 2024;



M. Bouvier et al. 2025). For instance, the ASAI survey toward L1157 (B. Lefloch et al. 2018) shows that its
two shocked knots (B1 and B2), located _∼_ 1.5–2 _[′]_ away
from the driving source, exhibit a molecular inventory
even richer than the protostar itself, including various
COMs (B. Lefloch et al. 2017). In particular, B1 and
B2 are among the richest Galactic sources of HNCO and
NH 2 CHO, two molecules of prebiotic interest (E. Mendoza et al. 2014). However, previous studies of highmass protostellar outflows have mostly relied on limited molecular species (e.g., CO and SiO) and often lack
spatially resolved kinematic information, which hinders
a comprehensive understanding of shock-induced chemistry within these sources (A. Palau et al. 2017; A. Y.
Yang et al. 2018; H.-L. Liu et al. 2020b; X. Lu et al.
2021; A. R. Costa Silva et al. 2022; A. Y. Yang et al.
2022; O. S. Rojas-Garc´ıa et al. 2022; J. Xie et al. 2023;
L. A. Busch et al. 2024; L. Francis et al. 2024; Y. Xu
et al. 2024; O. S. Rojas-Garc´ıa et al. 2024; A. Hoque
et al. 2025).
To overcome these limitations, we resolve a chemically rich massive protostellar outflow in the high-mass
star-forming region IRDC SDC335.579 _−_ 0.292 (IRAS
16272 _−_ 4837, also G335.59-0.29, hereafter SDC335),
which is located at a distance of 3.54 kpc. This
clump contains a total gas mass of _∼_ 3700 M _⊙_ (C. J.
Cyganowski et al. 2008; M. Anderson et al. 2021).
Within the central region corresponding to the area
shown in Figure 1 (b), which encompasses the massive
core SDC335-C1, the mass is _∼_ 400 M _⊙_ (F. Xu et al.
2023), exhibits high density, and shows chemical richness in COMs such as CH 3 CN, CH 3 OH, CH 3 OCHO,
and C 2 H 5 CN (S.-L. Qin et al. 2022; Z.-Y. Li et al. 2025;
F. Xu et al. 2024a). It is also associated with a clearly
defined bipolar high-velocity outflow (A. Avison et al.
2021), making it an ideal observational platform for
exploring non-thermal chemical evolution in high-mass
star formation.

In this letter, we report the detection of chemically enriched regions associated with jet-driven shocks in the
bipolar molecular outflow of the high-mass protostellar
core SDC335 C1, utilizing the wide-band molecular line
data at both 3 mm and 1.3 mm bands from the ATOMS
QUARKS survey. Section 2 introduces the two ALMA
observations used in this study. Section 3 presents the
integrated intensity maps of selected molecular transitions, which reveal chemically enriched zones throughout the bipolar outflow. In Section 4, we further explore
the chemical origin of each species within these local regions. Finally, Section 5 summarizes our main findings
and conclusions.

3





0.0377


0.0144


0.0055


0.0021


0.0008


0.0000



48°43'40"


50"


44'00"







48°43'50"


52"









54"


56"



58"



16 [h] 31 [m] 00.0 [s] 30 [m] 59.0 [s] 58.0 [s] 57.0 [s]


(a)



16 [h] 30 [m] 59.2 [s] 59.0 [s] 58.8 [s] 58.6 [s] 58.4 [s]


(b)



**Figure** **1.** **(a)** CO (2–1) RGB image constructed using the ACA+TM1+TM2 combined data. Blue- and red-shifted components
are integrated over velocities of _−_ 42 to _−_ 12 and +12 to +42 km s _[−]_ [1] relative to the systemic velocity, while the green channel
traces emission within _±_ 12 km s _[−]_ [1] . The cyan line marks the jet axis. Hot cores C1–C3 and several emission knots are visible.
**(b)** Zoom-in of the central region outlined in **(a)**, with 3 mm continuum in colorscale and 1.3 mm contours highlighting compact
sources. Continuum contours start at 21 mJy beam _[−]_ [1] and increase in steps of a factor of 1.618 (golden ratio). The beams of
3 mm (white) and 1.3 mm (grey) are shown in the lower-right corner.



2. OBSERVATIONS


2.1. _ALMA_ _3-mm_ _data_


We utilized ALMA Band 3 data from the ATOMS survey (Project ID: 2019.1.00685.S; PI: Tie Liu; T. Liu et al.
2020), which targets 146 massive star-forming clumps
using both the 12-m array in C3 configuration and the
ACA 7-m array. SDC335 was observed in single-pointing
mode, with a spectral setup covering multiple dense gas
and shock tracers. In this study, we use the 3 mm continuum map obtained with the 12-m array, which offers
higher angular resolution than the ACA-combined data,
with a synthesized beam of 1 _._ 7 _[′′]_ _×_ 1 _._ 5 _[′′]_ and a noise rms
of 10 mJy beam _[−]_ [1] . We also analyze selected molecular
line data from the 12-m + 7-m combined cubes, including transitions of HCO [+] (1–0), H [13] CO [+] (1–0), SiO (2–1),
and CH 3 OH, with velocity resolutions of 0.1–0.2 km s _[−]_ [1] .
More details on the observations and data reduction of

this source can be found in H.-L. Liu et al. 2021; F. Xu

et al. 2023.


2.2. _ALMA_ _1.3-mm_ _data_


We also used ALMA Band 6 data from the QUARKS
survey (Project ID: 2021.1.00095.S; PIs: Lei Zhu, Guido
Garay, and Tie Liu; X. Liu et al. 2024), which is a
high-resolution 1.3 mm follow-up survey of the ATOMS
survey. SDC335 was observed using both the 12-m C5
(TM1), 12-m C2 (TM2) and the ACA 7-m arrays, with
the best resolution of 0 _._ 3” and the maximum recover


able scale of _∼_ 28 _[′′]_ (F. Xu et al. 2024b; D. Yang et al.
2025). In this work, we also used combined TM2 +
ACA data for lines because of the higher signal-to-noise
ratios at lower resolution. The achieved resolutions of

continuum image and line data cube from the TM2 +
ACA combined data are approximately 1 _._ 3 _[′′]_ _×_ 1 _._ 1 _[′′]_ . The
noise rms of the continuum image is _∼_ 0 _._ 8 mJy beam _[−]_ [1] .
The four spectral windows at 217–221 and 229–233 GHz
spectral ranges cover numerous transitions from species
such as SiO (5–4), SO (6–5), HNCO, CH 3 OH, and other
molecules of interest. The velocity resolution of the line
data is about 1.3 km s _[−]_ [1] .


3. RESULTS


3.1. _The_ _outflow_ _and_ _driven_ _source_


Fig. 1(a) presents the RGB composite image of CO
J=2-1 outflows in SDC335, with blue, green, and red colors representing gas velocities blue-shifted by more than
10 km s _[−]_ [1], near the systemic velocity, and red-shifted
by more than 7 km s _[−]_ [1], respectively. A bipolar jet-like
outflow originates from the core C1, which is identified
as the driving source based on its position and chemical
richness. The 1.3 mm continuum is overlaid as white
contours, and the jet axis, spanning _∼_ 37 _[′′]_ (0.63 pc at
the distance to the source), is indicated by a cyan line.
Seven knots marked with “X” correspond to positions
along the jet where CH 3 OH and SiO emission are significantly enhanced in 1.3 mm band (panels iv and xviii

4

of Fig. 2). These knots, along with the jet axis, serve as
the basis for subsequent analysis and discussion.
Fig. 1(b) shows a zoomed-in view of the white box in
panel (a), with the background displaying the 3mm continuum. A low threshold is adopted to highlight the extended warm envelope, while high-threshold black contours of the 1.3mm continuum emphasize compact in
ternal structures. In addition to the three main cores
C1, C2, and C3, two earlier-phase cores (C4 and C5)
are detected between C1 and C2, consistent with the
cores detected in ALMA-DIHCA survey (F. A. Olguin
et al. 2021). C1 is a chemically rich core with a deconvolved size of 1 _._ 14 _[′′]_ _×_ 1 _._ 01 _[′′]_ . In the ATOMS 3mm band

survey, 18 COMs were detected toward C1, including cC 2 H 4 O, C 2 H 5 CN, CH 3 CHO, and CH 3 OCHO (S.-L. Qin
et al. 2022; Z.-Y. Li et al. 2025), indicating that it is a
typical hot molecular core. The average line width is
_∼_ 4 km s _[−]_ [1] . The non-detection of radio recombination
lines (e.g., H30 _α_ or H40 _α_ ) is suggestive of the absence
of strong ionized gas emission.


3.2. _Molecular_ _lines_ _detected_ _along_ _the_ _outflow_


We first extracted line spectra at the seven bright
knots located along the walls of the jet-driven outflow
cavity, where CH 3 OH and SiO emission are significantly
enhanced (see Sect. 3.1 and Figs. 1 and 2). To examine their velocity structure at higher spatial resolution,
we employed the ACA+TM1+TM2 combined data (see
Figs. A1 and A2 ). Owing to the relatively low signal-tonoise ratio of these data, we integrated every 3 km s _[−]_ [1]

channel to enhance the visibility of extended structures.
Given the potential for significant missing flux in the
interferometric maps, we did not use these data for
quantitative analysis. The resulting channel maps reveal that emission from CO 2–1, SiO 5–4, SO 6 5 –5 4,
H 2 CO 3 0 _,_ 3 –2 0 _,_ 2, and CH 3 OH 4 _−_ 2 _,_ 3 –3 _−_ 1 _,_ 2 is morphologically separated into two kinematic components: a
high-velocity ( _>_ 12 km s _[−]_ [1] ) component concentrated
along the collimated outflow axis, and a low-velocity
(6–12 km s _[−]_ [1] ) component forming a hollow-shell cavity structure. The seven knots correspond to prominent features in the low-velocity cavity shell, while their
high-velocity counterparts trace localized regions along
the axis. At a given velocity interval, the spatial distributions of these molecules are broadly similar, with
differences mainly in emission strength and the maximum velocity reached—for example, the high-velocity
emission of CH 3 OH extends only to _∼_ 21 km s _[−]_ [1], H 2 CO
to _∼_ 24 km s _[−]_ [1], SO to _∼_ 30 km s _[−]_ [1], and SiO and CO to
_∼_ 33 km s _[−]_ [1] . These differences likely reflect variations
in excitation conditions or shock chemistry sensitivity
among species. In total, 35 transitions from 22 molec


5


ular species were identified at the 3 mm and 1.3 mm
bands (see Appendix Table A1).
Fig. 2 presents the integrated intensity maps of 20
representative transitions, with color coding corresponding to blue-shifted, systemic, and red-shifted components. As can be seen in the figure, while most transitions are closely associated with outflow structure, the
molecular species exhibit diverse spatial distributions
and kinematic properties. For example, H [13] CO [+] and
CCH are confined to the quiescent envelope surrounding C1 and C2, characterized by narrow single-peaked
profiles (FWHM _≤_ 2 km s _[−]_ [1] ), whereas SiO emission is
enhanced at jet-impacted regions and shows broad line
wings typical of fast shocks. Similarly, SO displays a
spatial and velocity distribution akin to SiO, suggesting both species trace shocked gas. COMs including
CH 3 CHO are mainly detected near the outflow termini,
indicating sensitivity to local heating or mild shocks.
CH 3 OCHO and CH 3 CN are marginally detected and
exhibit low S/N as shown in Fig. A2. CH 3 OH emission, although widespread, exhibits relatively weak highvelocity components and is concentrated near the systemic velocity, likely originating from sublimated ices
induced by shocks in outflow and the cavity walls.
To further examine the gas kinematics, Fig. 3 presents
position–velocity diagrams (PVDs) of several important
molecules extracted along the outflow-jet axis (K1–K7,
cyan line in Fig. 1(a)). Consistent with the channel
maps (Sect. C), the PVDs confirm the morphological
separation between high-velocity emission along the axis
and low-velocity components in the cavity walls. In addition, the PVDs highlight localized high-velocity peaks
at shock positions traced most clearly by SiO and SO,
as well as discrete, spatially confined knots in CS, SO,
HC 3 N, H 2 CO, and CH 3 OH. These kinematic patterns,
combined with the spatial distributions in Fig. 2, reflect diverse excitation mechanisms and physical origins,
which will be further analyzed in the following section.


4. ANALYSIS AND DISCUSSION


4.1. _Quantitative_ _Analysis_ _and_ _Global_ _Results_


Benefiting from the large number of molecular lines
detected across both bands (Section 3.2), we focus on a
subset of transitions with sufficiently high S/N for reliable kinematic and excitation analysis. This selection
enables a systematic investigation of the physical and
chemical origins of the detected species, which we develop in this section.
The channel maps (Section C) reveal a clear separation between high-velocity emission confined to the
jet axis and a surrounding low-velocity cavity, with
molecule-dependent variations in extent and maximum

6


|SO|Col2|Col3|Col4|N 3|Col6|Col7|Col8|H|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|(c)||||(f) HC||||(i) CH3O||||
|||||||||||||
|||||||||||||
|||||||||||||
|CS||||CN||||CO||||
|(b)||||(e) H13||||(h) H2||||
|||||||||||||
|||||||||||||
|||||||||||||
|CO||||CN||||+||||
|(a)||||(d) H||||(g) HCO||||
|||||||||||||
|||||||||||||
|||||||||||||

7









100


75


50


25


0


25


50


75



PCA





































|low COMs<br>heating!<br>velocity<br>Cold<br>envelope outflow HNCO<br>enW va er lom <50K HC H3 2N CO ~160K<br>pe<br>100K<br>~ C H 3 O H o l w - v e o l c t i y o u o t f l w<br>Hot CO13COCSSO<br>,,,<br>3c 0o 0re H HC2C NO H,H 13C NN high -velocity jet shock<br>C3<br>K<br>,<br>CSSO13COHCN H 2 C O lo w - v e lo c it y o u tlo f w<br>,,,<br>H13CNHC N<br>, 3<br>CH OHH CO 3, 2 OCS C18O C,H C1 H3CO + jet H SC i3N C CH O3O MH s× S H O CK ! !<br>×<br>SHO<br>CSSO<br>, C<br>K ! !<br>Si+OH SiO+H|low COMs<br>heating!<br>velocity<br>outflowHNCO<br>HC3N<br>H2CO ~160K|Col3|
|---|---|---|
|Hot<br>core<br>300K<br>Warm<br>envelope<br>~100K<br>Cold<br>envelope<br><50K<br>CS,SO,13CO,HCN<br>H13CN,HC3N<br>CH3OH,H2CO<br>OCS<br>C18O,H13CO +<br>CCH<br>CO,13CO,CS,SO<br>H2CO,HC3N<br>HCN,H13CN<br>CH3OH<br>H2CO<br>high-velocity jet<br>low-velocity outflow<br>low-velocity outflow<br>low<br>velocity<br>outflow HNCO<br>HC3N<br>H2CO<br>COMs<br>heating!<br>~160K<br>SHOCK!!<br>SHOCK!!<br>jet<br>shock<br>Si<br>CS,SO<br>HC3N<br>CH3OH×<br>COMs×<br>Si + OH<br> SiO + H|SHOCK!!<br>SHOCK!!<br>jet<br>Si<br>CS,SO<br>HC3N<br>CH3OH×<br>COMs×<br>Si + OH<br> SiO + H|SHOCK!!<br>SHOCK!!<br>jet<br>Si<br>CS,SO<br>HC3N<br>CH3OH×<br>COMs×<br>Si + OH<br> SiO + H|


2000 a.u. 5000 a.u. 30000 a.u.


(b)


|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||~~C~~|~~H~~3~~OH 2~~<br>1,|1~~-1~~<br>1, 0~~A~~||
|||||CH3CHO|51, 4-41, 3|
||H2CO|13CO 2<br> 30, 3-20, 2<br>~~C~~|-1<br>~~H~~3~~OH 4~~<br>2,|3~~-3~~<br>1, 2~~E~~||
|CS|2-1<br>HC3N 11|-10<br>~~+~~|<br>HNCO 10|0, 10-90, 9||
|SO|<br> 32-21<br>SO 65-54|H2 <br>~~HCO   1~~<br>H13CN|CO 3-2 68<br>~~ -0~~<br> 1-0|~~C~~18~~O~~<br>  .1K|~~ 2-1~~|
|CO 2-<br>S|1<br>S~~i~~O 2-1<br>iO 5-4||HC3N 24-|<br> 23|<br>OCS 19-<br>CCH 1-0|
|~~HCN 1~~|~~ -0~~|||13~~CS~~|~~ 5-4~~|
||||||<br>~~U~~|



100 50 0 50 100

PC1


(a)



**Figure** **4.** ( **a** ) PCA of molecular emission along the jet axis (data within _±_ 2 _[′′]_ of C1 excluded). Molecules are separated into four
quadrants reflecting dominant chemical–kinematic behavior: Quadrant I: COMs enhanced in shocked regions; Quadrant II: outflow tracers with low- and high-velocity components; Quadrant III: shock/high-velocity tracers; Quadrant IV: systemic-velocity
or low S/N lines. ( **b** ) Schematic view of the physical and chemical structure of the bipolar outflow in SDC335. The main panel
shows the spatial distribution of key molecular tracers associated with the hot core, warm envelope, and jet-driven outflows.
The upper inset illustrates post-shock low-velocity outflows heating the gas and sublimating molecules from icy mantles. The
lower inset depicts strong shocks destroying dust grains, releasing ice-phase material and driving Si atoms from grain cores into
the gas phase to form SiO.

8



Pairwise Molecular Correlation (Kendall)



CO 2-1


13 CO 2-1


C [18] O 2-1


SiO 2-1


SiO 5-4


SO 3 2 -2 1


SO 6 5 -5 4


CS 2-1


13 CS 5-4


OCS 19-18


CCH 1-0


HC 3 N 11-10


HC 3 N 24-23


H 2 CO 3 0, 3 -2 0, 2


H 2 CO 3-2 68.1K


HCO [+] 1-0


HCN 1-0


H [13] CN 1-0


CH 3 OH 2 1, 1 [-1] 1, 0 [A]


CH 3 OH 4 2, 3 [-3] 1, 2 [E]


HNCO 10 0, 10 -9 0, 9


CH 3 CHO 5 1, 4 -4 1, 3


U







0.85


0.80


0.75


0.70


0.65



**Figure** **5.** Kendall rank correlation coefficients between integrated intensities of molecular lines, shown as a lower-triangular
matrix to avoid duplication.



velocity. Consistently, the PVD (Fig.3) and moment0
map (Fig.2) show that the bipolar jet driven by C1 is
remarkably symmetric within _±_ 14 _[′′]_ in both morphology and velocity, reaching line-of-sight velocities of up
to _±_ 40 km s _[−]_ [1] at _∼±_ 10 _[′′]_ from C1. The broadest line
widths (up to 20 km s _[−]_ [1] ) and the highest gas temperatures are found at knots K1, K6, and K7, coinciding
with peaks in molecular emission. Independent constraints from H 2 CO rotational analysis (Fig. B4) reveal
_T_ rot ≳ 200 K at several knots, consistent with strong



shock heating by the protostellar jet and suggesting that
multiple chemical processes—direct entrainment, shock
sputtering, and thermal desorption—operate simultaneously along the outflow.
To quantify chemical variations, we computed
position-integrated intensities of multiple transitions
along the jet axis (Fig.B1). Assuming LTE and optically
thin conditions, these serve as proxies for column densities. Most molecules, except [13] CO and C [18] O, show enhancements near K1–K7. Using [13] CO as a tracer of H 2

column density, relative intensity ratios (Fig.B2) highlight localized abundance peaks at the knots.
Spectral profiles provide complementary constraints
(Fig. B5). Molecules linked to shocks, such as SiO, SO,
and HCN, display broad wings and strong high-velocity
components, whereas CH 3 CHO and CH 3 CN peak near
the systemic velocity with weak wings. These differences
reflect distinct excitation and formation pathways, consistent with the spatial–kinematic separation observed
in the channel maps and PVDs.
Building on these diagnostics—integrated intensity
(Fig.B2), line profile (Fig.B5), and the ratio of systemicto non-systemic-velocity components (Fig.2)—we performed PCA on the molecular PVDs (Fig.4(a)). This
separates molecules into four groups, consistent with
Section 4.2:


  - Quadrant I (Sec.4.2.3): COMs, concentrated near
systemic velocity but enhanced in terminal knots,
reflecting ice-mantle sublimation and gas-phase reactions;


  - Quadrant II (Sec.4.2.1): outflow tracers spanning
low- and high-velocity components, with stable intensities from the hot core outward, indicative of
entrained ambient gas;


  - Quadrant III (Sec. 4.2.2): species associated with
shocks or high-velocity jets, peaking at terminal
knots where collisions produce strong shocks;


  - Quadrant IV: molecules dominated by systemicvelocity emission or with low S/N, weakly affected
by jet-induced shocks or of uncertain origin.


Finally, PCA on the full 18,684-dimensional vectors
(173 positions × 108 high-velocity channels) shows that
PC1 and PC2 account for 36.2% and 10.3% of the variance (46.5% combined), with nearly all variance driven
by spatial differences in high-velocity ( _>_ 4km s _[−]_ [1] ) line
intensities.

Complementing this, pairwise Kendall correlations
(Fig. 5) reveal that CS, SO, HCN, and SiO are
tightly correlated ( _>_ 0 _._ 8), with the strongest correlation
(0.88) between two SiO transitions J=2–1 and J=5–4.
H 2 CO and HCO [+] correlate uniformly with most species
(0.77–0.83) and with each other (0.86), indicating strong
chemical coupling. Notably, CH 3 OH 2 _−_ 1 _,_ 1 –1 _−_ 1 _,_ 0 A and
4 _−_ 2 _,_ 3 –3 _−_ 1 _,_ 2 E correlate at only 0.79, and their correlations with other molecules show larger differences, possibly related to nuclear spin isomers (Zou et al., in prep).
The results are also illustrated in a schematic cartoon
(Fig. 4 (b)). We emphasize that the PCA quadrants indicate the dominant origin of each molecule along the



9


jet, but many molecules can have contributions from
more than one source. This motivates the detailed clas
sification and discussion in the following subsections.


4.2. _Classification_ _of_ _Molecules_


4.2.1. _Molecules_ _Entrained_ _by_ _the_ _Outflow_


This group comprises molecules that are abundant in
the dense core and are primarily carried outward by the
jet-driven outflow, including CO, [13] CO, HCO [+], H 2 CO,
CS, and HC 3 N. As shown in the channel maps (Fig. C1,
C5) and PVDs (Fig. 3), these species are detected both
along the collimated jet axis and within the surrounding cavity-like low-velocity structures. Their line profiles (Appendix Fig. B5) generally display broad wings
together with systemic or intermediate-velocity components, indicating that they mainly trace gas physically
entrained and dynamically processed by the jet–ambient
interaction (M. Tafalla et al. 2010; B. Tabone et al. 2020;
L. Podio et al. 2021; �L. Tychoniec et al. 2019).
Relative intensity ratios to [13] CO (Appendix Fig. B2,
B3) remain nearly flat in regions lacking strong shocks,
but show moderate enhancements at bright knots.
Within this set, CO and HCO [+] are canonical tracers of
entrained gas; H 2 CO can be supplied by gas-phase formation and/or non-thermal release from grains (�L. Tychoniec et al. 2019); CS and HC 3 N follow the same spatial–kinematic pattern and predominantly trace dense
gas swept up by the outflow.


4.2.2. _Molecules_ _Released_ _into_ _the_ _Gas_ _Phase_ _by_
_Jet-Induced_ _Shocks_


A second group of molecules shows clear evidence of
shock-related enhancement, including SiO, SO, HCN
(and its isotopologues H [13] CN and DCN), HC 3 N, and
HC 3 N. Channel maps and PVDs (Figs. C3, C4, and 3)
reveal that their emissions are concentrated along the
jet axis and peak at bright knots, with broad wings and
high-velocity components comparable to SiO (Appendix
Fig. B5). Their intensity ratios relative to [13] CO also
rise sharply at these knots (Appendix Fig. B2), confirming that they trace material chemically reprocessed
in shocks.

In cold dense clouds, Si is locked in dust grains and
SiO is therefore heavily depleted (S. Guilloteau et al.
1992; A. Dutrey et al. 1997). Jet-induced shocks liberate Si atoms via non-thermal sputtering or grain fragmentation, which then react with OH or O to form SiO
(P. Caselli et al. 1997; P. Schilke et al. 1997; A. Gusdorf
et al. 2008a,b). Such localized SiO emission has been
widely observed in sources such as TMC1, SMM3, and
HH 211 (L. Podio et al. 2015; N. Sakai et al. 2014; �L.
Tychoniec et al. 2019).

10


SO chemistry is likewise tied to shocks: sulfur released
from grains can react with OH or O to form SO (T. W.
Hartquist et al. 1980; T. J. Millar & D. A. Williams
1993), while high-temperature reactions involving H 2 S
further enhance SO abundance in fast shocks where OH
and O abundances increase sharply (A. Gusdorf et al.
2008b). Although slower shocks can also contribute,
the strongest SO emission is typically found in energetic
jet–ambient collisions.
HCN and its isotopologues (H [13] CN, DCN) exhibit
SiO-like kinematics in our data. Their enhancement can

be explained by gas-phase reactions of CN with H 2 in
warm post-shock gas (S. Bruderer et al. 2009; R. Visser
et al. 2018). In HH211, H [13] CN has been observed tracing cavity walls, supporting a scenario where UV irradiation and high-temperature chemistry act in tandem
(�L. Tychoniec et al. 2019).
Although HC 3 N is often regarded as a more complex
N-bearing molecule, it likewise shows signs of shock enhancement (X. Lu et al. 2021; A. Hoque et al. 2025).
Possible formation pathways include polymerization of
CN intermediates or release of atomic N in nitrogen-rich,
low C/O environments (J. K. Jørgensen et al. 2004; C.
Codella et al. 2009, 2010). An additional efficient gasphase route is the reaction C 2 H 2 + CN _→_ HC 3 N + H
(K. Fukuzawa & Y. Osamura 1997; J. F. Chapman et al.
2009; E. Mendoza et al. 2018), which becomes more active in shocked gas.
Overall, the enhancement of these molecules is best
understood through two complementary processes:


(i) **sputtering** **of** **atoms** **or** **molecules** (e.g., Si, S,
HCN) from dust grains into the gas phase, and


(ii) **rapid** **activation** **of** **high-temperature** **chem-**
**istry** at shock fronts, producing additional N- and
O-bearing species.


4.2.3. _Molecules_ _Thermally_ _Excited_ _by_ _Shock_ _Heating_ _in_
_the_ _Jet_


A third group of molecules shows enhanced abundances that are best explained by shock-induced heating
rather than direct sputtering. Channel maps and PVDs
(Figs. C6, 3) reveal that their emissions peak at the systemic velocity of the outflow, while intensity ratios relative to [13] CO still increase at bright knots (Appendix
Fig. B2). Line profiles (Appendix Fig. B5) confirm that
CH 3 OH and HNCO sometimes display additional broad
wings tracing the outflow, whereas CH 3 CHO, CH 3 CN,
and CH 3 OCHO are confined to narrow systemic components. This pattern, combined with the correlation between SiO gradients and H 2 CO rotational temperatures
derived with RADEX (T. M¨oller et al. 2017) following



methods similar to N. Izumi et al. (2024) (Fig. B4), indicates excitation primarily driven by local thermal heating in shocked gas.
The observed enhancements can be attributed to hightemperature gas-phase chemistry coupled with thermal
desorption of icy mantles. CH 3 OH, for example, forms
efficiently on grain surfaces at low temperatures and
is readily released into the gas phase by heating (N.
Watanabe et al. 2004; K. I. Oberg [¨] et al. 2009). Other
species such as CH 3 CHO and HNCO are likewise desorbed or reprocessed through high-temperature reactions in shocked zones (A. Bacmann et al. 2012; S. Scibelli & Y. Shirley 2020). Comparisons with hot cores,
such as S68N (M. L. van Gelder et al. 2020; P. Nazari
et al. 2021), show similar abundance ratios, suggesting shared thermal histories or transient regeneration
in shocks. Observations in L1157-B1 and SMM3 further

support this scenario, where localized heating can mimic
hot-core conditions and temporarily enable the release
or synthesis of complex organics (M. De Simone et al.
2020; �L. Tychoniec et al. 2021).
In summary, the elevated abundances of CH 3 OH,
HNCO, and several COMs are mainly attributed to high
temperatures induced by jet–ambient shocks. Thermal
desorption and rapid gas-phase chemistry work in concert, enhancing molecular complexity in the outflow beyond that expected from the hot core alone.
Overall, our classification highlights the predominant
behaviors of different molecular groups—entrainment
from the core, shock-induced release, and thermal excitation by heating. However, these categories should
not be regarded as mutually exclusive. As shown in
Fig. 5 and Fig. 4, some molecules exhibit stronger correlations across groups than within their assigned category, underscoring the complexity of chemical processes
in jet–outflow systems. This scheme therefore provides
a useful framework for interpretation, but the role of
each molecule may vary with local physical conditions,
and caution is warranted when drawing sharp boundaries between categories.


5. CONCLUSIONS


We have presented ALMA observations of the chemically rich jet and outflow system in SDC335, detecting
35 transitions from 22 molecular species. By extracting
channel maps, PVDs, integrated intensity ratios, and
line profiles, we conducted a quantitative analysis of the
spatial–kinematic and excitation properties of different

molecules.
Principal component analysis (PCA) of these parameters shows that line profiles provide the largest variance among species, serving as the dominant feature

distinguishing their behaviors. The PCA distribution
naturally separates molecules into three quadrants, corresponding to three predominant classes: (1) species
entrained from the dense core by the outflow (e.g.,
CO, HCO [+], CS, HC 3 N); (2) molecules released into
the gas phase or newly formed in jet-induced shocks
(e.g., SiO, SO, HCN, DCN); and (3) molecules thermally excited by shock heating and subsequent gasphase or desorption processes (e.g., CH 3 OH, CH 3 CHO,
CH 3 CN, HNCO, CH 3 OCHO). These groups display distinct spatial–kinematic signatures, with entrained tracers extended along the cavity walls, shock tracers peaking at high-velocity knots, and thermally excited species
confined to systemic-velocity components with local enhancements at knots. However, individual species may
participate in multiple processes—entrainment, sputtering, or thermal heating—depending on local conditions. The observed chemistry of the outflow is therefore
shaped by the interplay of all three mechanisms rather
than by a single pathway.
In summary, our study highlights the multi-origin nature of molecular emission in a massive protostellar outflow, combining entrainment from the core, shock-driven
release, and thermal excitation by shock heating. Future
observations with higher angular resolution and sensitivity, together with laboratory and modeling efforts on
grain-surface and gas-phase chemistry under shock con


11


ditions, will be essential to disentangle the relative contributions of these processes and to quantify the physical–chemical environment of massive outflows.


ACKNOWLEDGMENTS


Tie Liu acknowledges the supports by the National
Key R&D Program of China (No. 2022YFA1603101),
National Natural Science Foundation of China (NSFC)
through grants No.12073061 and No.12122307, the PIFI
program of Chinese Academy of Sciences through grant
No. 2025PG0009, and the Tianchi Talent Program of
Xinjiang Uygur Autonomous Region.


H.-L. Liu is supported by Yunnan Fundamental Research Project (grant No. 202301AT070118,
202401AS070121), and by Xingdian Talent Support
Plan–Youth Project.


A.H. thank the support of the S. N. Bose National
Centre for Basic Sciences under the Department of Science and Technology, Govt. of India and the CSIRHRDG, Govt. of India for funding the fellowship.
SRD acknowledges support from the Fondecyt Postdoctoral fellowship (project code 3220162) and ANID
BASAL project FB210003.


_Facilities:_ ALMA



REFERENCES



Anderson, M., Peretto, N., Ragan, S. E., et al. 2021,
MNRAS, 508, 2964, doi: [10.1093/mnras/stab2674](http://doi.org/10.1093/mnras/stab2674)

Arce, H. G., Santiago-Garc´ıa, J., Jørgensen, J. K., Tafalla,

M., & Bachiller, R. 2008, ApJL, 681, L21,

doi: [10.1086/590110](http://doi.org/10.1086/590110)

Avison, A., Fuller, G. A., Peretto, N., et al. 2021, A&A,

645, A142, doi: [10.1051/0004-6361/201936043](http://doi.org/10.1051/0004-6361/201936043)

Bacmann, A., Taquet, V., Faure, A., Kahane, C., &

Ceccarelli, C. 2012, A&A, 541, L12,

doi: [10.1051/0004-6361/201219207](http://doi.org/10.1051/0004-6361/201219207)

Bouvier, M., Giani, L., Chahine, L., et al. 2025, MNRAS,

539, 2380, doi: [10.1093/mnras/staf631](http://doi.org/10.1093/mnras/staf631)

Bruderer, S., Benz, A. O., Bourke, T. L., & Doty, S. D.
2009, A&A, 503, L13, doi: [10.1051/0004-6361/200912620](http://doi.org/10.1051/0004-6361/200912620)

Busch, L. A., Belloche, A., Garrod, R. T., M¨uller, H. S. P.,

& Menten, K. M. 2022, A&A, 665, A96,

doi: [10.1051/0004-6361/202243383](http://doi.org/10.1051/0004-6361/202243383)

Busch, L. A., Belloche, A., Garrod, R. T., M¨uller, H. S. P.,

& Menten, K. M. 2024, A&A, 681, A104,

doi: [10.1051/0004-6361/202347256](http://doi.org/10.1051/0004-6361/202347256)



Caselli, P., Hartquist, T. W., & Havnes, O. 1997, A&A,

322, 296

Chahine, L., Ceccarelli, C., De Simone, M., et al. 2024,

MNRAS, 531, 2653, doi: [10.1093/mnras/stae1320](http://doi.org/10.1093/mnras/stae1320)

Chapman, J. F., Millar, T. J., Wardle, M., Burton, M. G.,

& Walsh, A. J. 2009, MNRAS, 394, 221,

doi: [10.1111/j.1365-2966.2008.14144.x](http://doi.org/10.1111/j.1365-2966.2008.14144.x)

Chen, Y., Rocha, W. R. M., van Dishoeck, E. F., et al.

2024, A&A, 690, A205,

doi: [10.1051/0004-6361/202450706](http://doi.org/10.1051/0004-6361/202450706)

Codella, C., Benedettini, M., Beltr´an, M. T., et al. 2009,

A&A, 507, L25, doi: [10.1051/0004-6361/200913340](http://doi.org/10.1051/0004-6361/200913340)

Codella, C., Lefloch, B., Ceccarelli, C., et al. 2010, A&A,

518, L112, doi: [10.1051/0004-6361/201014582](http://doi.org/10.1051/0004-6361/201014582)

Codella, C., Ceccarelli, C., Caselli, P., et al. 2017, A&A,

605, L3, doi: [10.1051/0004-6361/201731249](http://doi.org/10.1051/0004-6361/201731249)

Costa Silva, A. R., Fedriani, R., Tan, J. C., et al. 2022,

A&A, 659, A23, doi: [10.1051/0004-6361/202142412](http://doi.org/10.1051/0004-6361/202142412)

Cyganowski, C. J., Whitney, B. A., Holden, E., et al. 2008,
AJ, 136, 2391, doi: [10.1088/0004-6256/136/6/2391](http://doi.org/10.1088/0004-6256/136/6/2391)

12


De Simone, M., Codella, C., Ceccarelli, C., et al. 2020,

A&A, 640, A75, doi: [10.1051/0004-6361/201937004](http://doi.org/10.1051/0004-6361/201937004)

Draine, B. T. 1995, Ap&SS, 233, 111,

doi: [10.1007/BF00627339](http://doi.org/10.1007/BF00627339)

Dutrey, A., Guilloteau, S., & Bachiller, R. 1997, A&A, 325,

758

Feng, S., Liu, H. B., Caselli, P., et al. 2022, ApJL, 933, L35,
doi: [10.3847/2041-8213/ac75d7](http://doi.org/10.3847/2041-8213/ac75d7)

Feng, S., Codella, C., Ceccarelli, C., et al. 2020, ApJ, 896,
37, doi: [10.3847/1538-4357/ab8813](http://doi.org/10.3847/1538-4357/ab8813)

Flower, D. 1994, in Astronomical Society of the Pacific

Conference Series, Vol. 58, The First Symposium on the

Infrared Cirrus and Diffuse Interstellar Clouds, ed. R. M.

Cutri & W. B. Latter, 332

Francis, L., van Gelder, M. L., van Dishoeck, E. F., et al.

2024, A&A, 683, A249,

doi: [10.1051/0004-6361/202348105](http://doi.org/10.1051/0004-6361/202348105)

Fukuzawa, K., & Osamura, Y. 1997, ApJ, 489, 113,

doi: [10.1086/304782](http://doi.org/10.1086/304782)

Guilloteau, S., Bachiller, R., Fuente, A., & Lucas, R. 1992,

A&A, 265, L49

Gusdorf, A., Cabrit, S., Flower, D. R., & Pineau Des

Forˆets, G. 2008a, A&A, 482, 809,

doi: [10.1051/0004-6361:20078900](http://doi.org/10.1051/0004-6361:20078900)

Gusdorf, A., Pineau Des Forˆets, G., Cabrit, S., & Flower,

D. R. 2008b, A&A, 490, 695,

doi: [10.1051/0004-6361:200810443](http://doi.org/10.1051/0004-6361:200810443)

Hartquist, T. W., Dalgarno, A., & Oppenheimer, M. 1980,
ApJ, 236, 182, doi: [10.1086/157731](http://doi.org/10.1086/157731)

Hollenbach, D., & McKee, C. F. 1989, ApJ, 342, 306,

doi: [10.1086/167595](http://doi.org/10.1086/167595)

Hoque, A., Baug, T., Dewangan, L. K., et al. 2025, The

Astrophysical Journal, 987, 197,
doi: [10.3847/1538-4357/add928](http://doi.org/10.3847/1538-4357/add928)

Hsu, S.-Y., Lee, C.-F., Liu, S.-Y., et al. 2024, ApJ, 976, 29,

doi: [10.3847/1538-4357/ad7e25](http://doi.org/10.3847/1538-4357/ad7e25)

Izumi, N., Sanhueza, P., Koch, P. M., et al. 2024, ApJ, 963,

163, doi: [10.3847/1538-4357/ad18c6](http://doi.org/10.3847/1538-4357/ad18c6)

James, T. A., Viti, S., Holdship, J., & Jim´enez-Serra, I.

2020, A&A, 634, A17, doi: [10.1051/0004-6361/201936536](http://doi.org/10.1051/0004-6361/201936536)

Jørgensen, J. K., Hogerheijde, M. R., Blake, G. A., et al.
2004, A&A, 415, 1021, doi: [10.1051/0004-6361:20034216](http://doi.org/10.1051/0004-6361:20034216)

Lee, C.-F. 2020, A&A Rv, 28, 1,

doi: [10.1007/s00159-020-0123-7](http://doi.org/10.1007/s00159-020-0123-7)

Lefloch, B., Ceccarelli, C., Codella, C., et al. 2017,

MNRAS, 469, L73, doi: [10.1093/mnrasl/slx050](http://doi.org/10.1093/mnrasl/slx050)

Lefloch, B., Bachiller, R., Ceccarelli, C., et al. 2018,

MNRAS, 477, 4792, doi: [10.1093/mnras/sty937](http://doi.org/10.1093/mnras/sty937)

Li, Z.-Y., Liu, X., Liu, T., et al. 2025, A&A, 697, A190,

doi: [10.1051/0004-6361/202452762](http://doi.org/10.1051/0004-6361/202452762)



Liu, H.-L., Sanhueza, P., Liu, T., et al. 2020b, ApJ, 901, 31,

doi: [10.3847/1538-4357/abadfe](http://doi.org/10.3847/1538-4357/abadfe)

Liu, H.-L., Liu, T., Evans, Neal J., I., et al. 2021, MNRAS,

505, 2801, doi: [10.1093/mnras/stab1352](http://doi.org/10.1093/mnras/stab1352)

Liu, T., Evans, N. J., Kim, K.-T., et al. 2020, MNRAS,

496, 2790, doi: [10.1093/mnras/staa1577](http://doi.org/10.1093/mnras/staa1577)

Liu, X., Liu, T., Zhu, L., et al. 2024, Research in

Astronomy and Astrophysics, 24, 025009,
doi: [10.1088/1674-4527/ad0d5c](http://doi.org/10.1088/1674-4527/ad0d5c)

Lu, X., Li, S., Ginsburg, A., et al. 2021, ApJ, 909, 177,
doi: [10.3847/1538-4357/abde3c](http://doi.org/10.3847/1538-4357/abde3c)

Mendoza, E., Lefloch, B., L´opez-Sepulcre, A., et al. 2014,

MNRAS, 445, 151, doi: [10.1093/mnras/stu1718](http://doi.org/10.1093/mnras/stu1718)

Mendoza, E., Lefloch, B., Ceccarelli, C., et al. 2018,

MNRAS, 475, 5501, doi: [10.1093/mnras/sty180](http://doi.org/10.1093/mnras/sty180)

Millar, T. J., & Williams, D. A. 1993, Dust and chemistry

in astronomy

Miura, H., Yamamoto, T., Nomura, H., et al. 2017, ApJ,

839, 47, doi: [10.3847/1538-4357/aa67df](http://doi.org/10.3847/1538-4357/aa67df)

M¨oller, T., Endres, C., & Schilke, P. 2017, A&A, 598, A7,

doi: [10.1051/0004-6361/201527203](http://doi.org/10.1051/0004-6361/201527203)

Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56,

41, doi: [10.1146/annurev-astro-091916-055235](http://doi.org/10.1146/annurev-astro-091916-055235)

Nazari, P., van Gelder, M. L., van Dishoeck, E. F., et al.

2021, A&A, 650, A150,

doi: [10.1051/0004-6361/202039996](http://doi.org/10.1051/0004-6361/202039996)
¨Oberg, K. I., Garrod, R. T., van Dishoeck, E. F., &

Linnartz, H. 2009, A&A, 504, 891,

doi: [10.1051/0004-6361/200912559](http://doi.org/10.1051/0004-6361/200912559)
¨Oberg, K. I., van der Marel, N., Kristensen, L. E., & van

Dishoeck, E. F. 2011, ApJ, 740, 14,

doi: [10.1088/0004-637X/740/1/14](http://doi.org/10.1088/0004-637X/740/1/14)

Olguin, F. A., Sanhueza, P., Guzm´an, A. E., et al. 2021,
ApJ, 909, 199, doi: [10.3847/1538-4357/abde3f](http://doi.org/10.3847/1538-4357/abde3f)

Oya, Y., Saiga, E., Miotello, A., et al. 2025, ApJ, 980, 263,
doi: [10.3847/1538-4357/adabe7](http://doi.org/10.3847/1538-4357/adabe7)
Palau, A., Walsh, C., S´anchez-Monge, A., [´] et al. 2017,
MNRAS, 467, 2723, doi: [10.1093/mnras/stx004](http://doi.org/10.1093/mnras/stx004)

Podio, L., Codella, C., Gueth, F., et al. 2015, A&A, 581,

A85, doi: [10.1051/0004-6361/201525778](http://doi.org/10.1051/0004-6361/201525778)

Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648,

A45, doi: [10.1051/0004-6361/202038429](http://doi.org/10.1051/0004-6361/202038429)

Qin, S.-L., Liu, T., Liu, X., et al. 2022, MNRAS, 511, 3463,

doi: [10.1093/mnras/stac219](http://doi.org/10.1093/mnras/stac219)

Rojas-Garc´ıa, O. S., G´omez-Ruiz, A. I., Palau, A., et al.
2022, ApJS, 262, 13, doi: [10.3847/1538-4365/ac81cb](http://doi.org/10.3847/1538-4365/ac81cb)

Rojas-Garc´ıa, O. S., G´omez-Ruiz, A. I., Palau, A., et al.
2024, MNRAS, 527, 2110, doi: [10.1093/mnras/stad3161](http://doi.org/10.1093/mnras/stad3161)

Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78,

doi: [10.1038/nature13000](http://doi.org/10.1038/nature13000)

Schilke, P., Walmsley, C. M., Pineau des Forets, G., &

Flower, D. R. 1997, A&A, 321, 293

Scibelli, S., & Shirley, Y. 2020, ApJ, 891, 73,
doi: [10.3847/1538-4357/ab7375](http://doi.org/10.3847/1538-4357/ab7375)

Tabone, B., Godard, B., Pineau des Forˆets, G., Cabrit, S.,

& van Dishoeck, E. F. 2020, A&A, 636, A60,

doi: [10.1051/0004-6361/201937383](http://doi.org/10.1051/0004-6361/201937383)

Tafalla, M., & Bachiller, R. 2011, in IAU Symposium, Vol.

280, The Molecular Universe, ed. J. Cernicharo &

R. Bachiller, 88–102, doi: [10.1017/S1743921311024896](http://doi.org/10.1017/S1743921311024896)

Tafalla, M., Santiago-Garc´ıa, J., Hacar, A., & Bachiller, R.
2010, A&A, 522, A91, doi: [10.1051/0004-6361/201015158](http://doi.org/10.1051/0004-6361/201015158)

Tychoniec, �L., Hull, C. L. H., Kristensen, L. E., et al. 2019,
A&A, 632, A101, doi: [10.1051/0004-6361/201935409](http://doi.org/10.1051/0004-6361/201935409)

Tychoniec, �L., van Dishoeck, E. F., van’t Hoff, M. L. R.,

et al. 2021, A&A, 655, A65,

doi: [10.1051/0004-6361/202140692](http://doi.org/10.1051/0004-6361/202140692)

van der Tak, F. F. S., Black, J. H., Sch¨oier, F. L., Jansen,

D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627,

doi: [10.1051/0004-6361:20066820](http://doi.org/10.1051/0004-6361:20066820)

van Gelder, M. L., Tabone, B., Tychoniec, �L., et al. 2020,
A&A, 639, A87, doi: [10.1051/0004-6361/202037758](http://doi.org/10.1051/0004-6361/202037758)

Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A,

615, A75, doi: [10.1051/0004-6361/201731898](http://doi.org/10.1051/0004-6361/201731898)



13


Watanabe, N., Nagaoka, A., Shiraki, T., & Kouchi, A.


2004, ApJ, 616, 638, doi: [10.1086/424815](http://doi.org/10.1086/424815)


Xie, J., Li, J., Wang, J., et al. 2023, ApJ, 949, 89,


doi: [10.3847/1538-4357/acc83f](http://doi.org/10.3847/1538-4357/acc83f)


Xu, F., Wang, K., Liu, T., et al. 2023, MNRAS, 520, 3259,


doi: [10.1093/mnras/stad012](http://doi.org/10.1093/mnras/stad012)


Xu, F., Wang, K., Liu, T., et al. 2024a, ApJS, 270, 9,


doi: [10.3847/1538-4365/acfee5](http://doi.org/10.3847/1538-4365/acfee5)


Xu, F., Wang, K., Liu, T., et al. 2024b, Research in


Astronomy and Astrophysics, 24, 065011,


doi: [10.1088/1674-4527/ad3dc3](http://doi.org/10.1088/1674-4527/ad3dc3)


Xu, Y., Wang, J., Liu, S., et al. 2024, AJ, 167, 285,


doi: [10.3847/1538-3881/ad47c4](http://doi.org/10.3847/1538-3881/ad47c4)


Yang, A. Y., Thompson, M. A., Urquhart, J. S., & Tian,


W. W. 2018, ApJS, 235, 3,


doi: [10.3847/1538-4365/aaa297](http://doi.org/10.3847/1538-4365/aaa297)


Yang, A. Y., Urquhart, J. S., Wyrowski, F., et al. 2022,


A&A, 658, A160, doi: [10.1051/0004-6361/202142039](http://doi.org/10.1051/0004-6361/202142039)


Yang, D., Liu, H.-L., Liu, T., et al. 2025, ApJS, 280, 33,


doi: [10.3847/1538-4365/adf847](http://doi.org/10.3847/1538-4365/adf847)

14


APPENDIX


A. LIST OF DETECTED MOLECULAR LINES ALONG THE JET


**Table** **A1.** Identified Molecular Transitions in the 1.3 mm and 3 mm Bands


Species Rest Freq. Quantum No. _E_ _u_ _/k_ log _A_ _ij_


(MHz) (K) (s _[−]_ [1] )


CO 230538.0 2 _−_ 1 16.60 _−_ 6 _._ 1605

13 CO 220398.7 2 _−_ 1 15.87 _−_ 6 _._ 2165

C [18] O 219560.4 2 _−_ 1 15.81 _−_ 6 _._ 2210

SiO 86847.0 2 _−_ 1 6.25 _−_ 4 _._ 5335

SiO 217104.9 5 _−_ 4 31.26 _−_ 3 _._ 2843

CS 97981.0 2 _−_ 1 7.05 _−_ 4 _._ 7763

13 CS 231220.6 5 _−_ 4 22.19 _−_ 3 _._ 6008

SO 99299.9 3 2 –2 1 9.23 _−_ 4 _._ 9488

SO 100029.6 4 5 -4 4 38.57 _−_ 5 _._ 96577

SO 219949.4 6 5 –5 4 34.98 _−_ 3 _._ 8745

OCS 231060.9 19 _−_ 18 110.9 _−_ 4 _._ 4463

CCH 87316.9 1 _−_ 0 4.19 _−_ 5 _._ 8161

HCN 88631.6 1 _−_ 0 4.25 _−_ 4 _._ 6171

H [13] CN 86339.9 1 _−_ 0 4.14 _−_ 4 _._ 6526

DCN 217238.5 3 _−_ 2 20.85 _−_ 3 _._ 3396

HCO [+] 89188.5 1 _−_ 0 4.28 _−_ 4 _._ 3781

H [13] CO [+] 86754.3 1 _−_ 0 4.16 _−_ 4 _._ 1635

HC 3 N 100076.4 11 _−_ 10 28.82 _−_ 4 _._ 1114

HC 3 N 218324.7 24 _−_ 23 130.98 _−_ 3 _._ 0830

HNCO 219798.3 10 0 _,_ 10 –9 0 _,_ 9 58.02 _−_ 3 _._ 8329

H 2 CO 101333.0 6 1 _,_ 5 –6 1 _,_ 6 87.56 _−_ 5 _._ 8038
H 2 CO 218222.2 3 0 _,_ 3 –2 0 _,_ 2 20.96 _−_ 3 _._ 5501
H 2 CO 218475.6 3 2 _,_ 2 –2 2 _,_ 1 68.09 _−_ 3 _._ 8037
H 2 CO 218760.1 3 2 _,_ 1 –2 2 _,_ 0 68.11 _−_ 3 _._ 8021
H [13] 2 [CO] 219908.5 3 1 _,_ 2 –2 1 _,_ 1 32.94 _−_ 3 _._ 5911
CH 3 OH (A) 97582.8 2 _−_ 1 _,_ 1 –1 _−_ 1 _,_ 0 21.56 _−_ 5 _._ 5807
CH 3 OH (E) 216945.5 5 _−_ 1 _,_ 4 –4 _−_ 2 _,_ 3 55.87 _−_ 4 _._ 9159
CH 3 OH (E) 218440.1 4 _−_ 2 _,_ 3 –3 _−_ 1 _,_ 2 45.46 _−_ 4 _._ 3292
CH 3 OH (E) 220078.6 8 _−_ 0 _,_ 8 –7 _−_ 1 _,_ 6 96.61 _−_ 4 _._ 5993

CH 3 CN 220730.3 12 2 –11 2 97.44 _−_ 3 _._ 0465

CH 3 CN 220743.0 12 1 –11 1 76.01 _−_ 3 _._ 0372

CH 3 CN 220747.3 12 0 –11 0 68.67 _−_ 3 _._ 0342

CH 3 CHO (E) 98863.3 5 1 _,_ 4 –4 1 _,_ 3 16.59 _−_ 4 _._ 5082
CH 3 CHO (A) 98900.9 5 1 _,_ 4 –4 1 _,_ 3 16.51 _−_ 4 _._ 5077
CH 3 OCHO (A+E) 216966 20 _−_ 19 111.5 _−_ 3 _._ 815


Note— CH 3 OCHO and CH 3 CN are marginally detected.


Table A1 summarizes all molecular transitions detected at the bright knots of the outflow. The corresponding spectra
are shown in Fig. A1 and A2, overlaid with cumulative integrated intensity curves.

15


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||

16


|Col1|CCH 1-0 4.19|4.19|Col4|Col5|HCN|HCN 1-0 4.25|4.25|Col9|Col10|Col11|H13C|HC 1-0 4.14|4.14|Col15|Col16|HCO|HCO 1-0 4.28|4.28|Col20|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||

17


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||

18


|CH3CHO|CH3CHO 51, 4-41, 16.59K|CH3CHO|CH3CHO 51, 4-41, 16.51K|CH3CHO|CH3CHO 31, 3-20, 7.73K|
|---|---|---|---|---|---|
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||

19


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||

20


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||

21


|Col1|HC 24- 131|131|Col4|Col5|HN|HN 100 58K|58K|Col9|Col10|H2C|H2C 30, 21.|21.|Col14|Col15|Col16|H2C|H2C 32, 68.|68.|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||

22


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||

23


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||

24


B. SUPPLEMENTARY POSITION–VELOCITY ANALYSIS


Fig. B1 presents the integrated intensity along the outflow axis defined in Fig. 1(a), with a slit width of 1 _[′′]_ and
velocity range from _−_ 36 to +36 km s _[−]_ [1] . Based on the spatial distributions of the continuum, CCH, C [18] O and other
molecules (see Fig. 1(b) and Fig. 2), we consider the inner 2 _[′′]_ to be dominated by hot-core emission. To minimize this
contamination, all values are divided by the reference intensity at 2 _[′′]_ from the core; regions beyond 2 _[′′]_ are referred to
as the “pure” outflow in the following discussion. The integrated intensities of [13] CO and C [18] O decrease monotonically
with distance, whereas other molecules show oscillatory enhancements.
Because the outflow expands with distance, absolute integrated intensities are not direct tracers of abundance
variations. Fig. B2 therefore shows the ratios of each molecule to the local [13] CO intensity, normalized at each position,
to reveal abundance gradients. Compared with Fig. B1, the relative abundances display mirror symmetry with respect
to the hot core, particularly within _±_ 14 _[′′]_, consistent with the integrated maps (Fig. 2) and PVDs (Fig. 3). The middle
outflow (2 _[′′]_ –6 _._ 5 _[′′]_ ) exhibits systematically lower abundances, highlighted with a pale yellow background. Fig. B3 further
zooms into shock–weak regions: after re-normalization at 2 _[′′]_, the vertical axis shows the abundance relative to the 2 _[′′]_

value. The mean and standard deviation of “abundance factors relative to [13] CO” are adopted to assess significance,
as annotated in the figure. SO 6 5 –5 4, HC 3 N, both H 2 CO transitions, CH 3 OH-E, H [13] CN, and HNCO remain nearly
constant, suggesting weak shock sensitivity; by contrast, SiO, SO 3 2 –2 2, CS, HCO [+], HCN, CH 3 OH-A, and CH 3 CHO
show various levels of enhancement, pointing to distinct formation pathways.
Fig. B4 shows the variation rate of SiO 5 4 –4 3 intensity compared with the kinetic temperature _T_ kin derived from
H 2 CO 3–2 transitions. The kinetic temperature is calculated using the non-LTE radiative transfer code RADEX
(F. F. S. van der Tak et al. 2007). We assume the volume density 10 [5] –10 [6] cm _−_ 3 of the outflow, and using minimum
_χ_ [2] to optimize the line ratio between transitions of H 2 CO 3–2. This method has a good constrain of temperature
below 300 K otherwise the temperature can be sensitive to the volume density. Bright knots correspond to high _T_ kin
and steep SiO gradients, indicating that jet impacts compress and heat the outflowing shell, leading to the release of
icy species into the gas phase.
Fig. B5 compares selected line profiles in the 1.3 mm and 3 mm bands. The cumulative intensity at the bottom
separates systemic and non-systemic velocity components to highlight differences.


  - (a) High-velocity molecules at 1.3 mm: SiO, SO, HC 3 N. For HC 3 N the S/N is low at knots K2, K3, K5, and K6,
but near-Gaussian at C1.


  - (b) High-velocity molecules at 3 mm: SiO, CS, SO, HCN, HC 3 N. Overall profiles resemble those at 1.3 mm, but
the cumulative plots differ significantly: SiO and SO dominate _|v| >_ 12 km s _[−]_ [1], while CS and HC 3 N are weaker;
H [13] CN lies in between.


  - (c) Low-velocity molecules at 1.3 mm: HNCO, H 2 CO, CH 3 OH-E, CH 3 CN. The three adjacent CH 3 CN 12 _k_ –11 _k_
lines show absorption at knots K3–K5, indicating excitation temperatures lower than the outflow background.
HNCO has insufficient S/N at some knots. These species are dominated by systemic velocity emission (see
Fig. 2), with weaker high- and low-velocity components.


  - (d) Low-velocity molecules at 3 mm: HCO [+], CH 3 OH-A, CH 3 CHO. CH 3 OH-A ( _E_ _u_ = 21 _._ 1 K) is more concentrated at systemic velocity compared with CH 3 OH-E ( _E_ _u_ = 45 _._ 5 K), and shows stronger emission in the northern
(redshifted) lobe. Whether this A/E difference reflects intrinsic nuclear-spin properties remains to be confirmed.

25



Normalized Integrated Intensity Along Jet







3.5





0.8


0.6


0.4


0.2


0.0



3.0


2.5


2.0


1.5







1.0


0.5


0.0


2.0


1.5


1.0


0.5





1.2


1.0


0.8


0.6


0.4


0.2









0.0
10 0 10 20



0.0
10 0 10 20



Position ( )


**Figure** **B1.** Integrated intensities of selected molecular lines along the jet axis of SDC335, plotted as a function of projected
distance from the central hot core (C1). All intensities are normalized to their values at +2 _[′′]_ to highlight relative enhancements
or suppressions along the flow. Positive offsets correspond to the northern (red-shifted) lobe, and negative offsets to the southern
(blue-shifted) lobe.

26



Integrated Intensity Relative to [13] CO and Normalized by Peak Value



K1 K2 K3 K4K5 K6 K7



K1 K2 K3 K4K5 K6 K7


1.0


0.6


0.4


0.2


0.0


K1 K2 K3 K4K5 K6 K7


1.0



1.0



0.8



0.6



0.4


0.2


0.0



K1 K2 K3 K4K5 K6 K7



0.8


0.6


0.4


0.2



0.8


0.6


0.4


0.2







0.0
10 0 10 20



0.0
10 0 10 20



Position (")


**Figure** **B2.** Relative abundance proxies of selected molecules along the jet axis, computed as the ratio of their integrated intensities to that of [13] CO at each position. Each line is normalized to its own maximum value across the spatial extent to emphasize
the distribution pattern rather than absolute abundance contrast. This highlights molecule-specific spatial differentiation along
the outflow.

27







|Integrated Intensity Relative to 13CO Normalized by 2 arcsec<br>C1 K4 C1 K4<br>4 4<br>3 3<br>Normalized)<br>2 2<br>1 1<br>SiO 2 -1: 2 .02±1 .55<br>0 SiO 5 -4: 0 .35±0 .23 0 HC 3N 11 -10: 2 .06±0 .82<br>SO 3 2-2 1: 2 .01±1 .14 HC 3N 24 -23: 0 .11±0 .04 arcsec<br>SO 6 5-5 4: 0 .54±0 .13 H 2CO 3 0 3-2 0 2: 0 .60±0 .18<br>1 1,,<br>CS 2 -1: 4 .98±2 .16 H 2CO 3 2 2-2 2 1: 0 .22±0 .07<br>,,<br>(2<br>C1 K4 C1 K4<br>Intensity<br>4 4<br>3 3<br>Relative<br>2 2<br>1 1<br>CH 3OH 2 1-1 0A: 0 .61±0 .33<br>0 0 1, 1,<br>HCO + 1 -0: 4 .21±1 .67 CH 3OH 4 2 3-3 1 2E: 0 .44±0 .13<br>,,<br>HCN 1 -0: 7 .37±3 .30 HNCO 10 0 10-9 0 9: 0 .18±0 .05<br>1 1,,<br>H13CN 1 -0: 1 .45±0 .41 CH 3CHO 5 1 4-4 1 3: 0 .42±0 .20<br>,,|Col2|Col3|Col4|lized by|Col6|2 arcsec<br>C1 K4|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)|||HC~~3~~N 11-|HC~~3~~N 11-|10: 2.|06±0.82||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)|||<br>HC3N 24-<br>H2CO 30,|<br>HC3N 24-<br>H2CO 30,|<br> 23: 0.<br> 3-20, 2:|<br> 11±0.04<br> 0.60±0.18||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)|||H2CO 32,|H2CO 32,|2-22, 1:|0.22±0.07||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)||||||||||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)|||CH3OH 2|CH3OH 2|1 1-1|1 0A: 0.61±|0.33|||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)|||CH3OH 4<br>HNCO 10|CH3OH 4<br>HNCO 10|,<br>2, 3-3<br> 0, 10-90|,<br>1, 2E: 0.44±<br>, 9: 0.18±0.|0.13<br> 05|||
|C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>SiO 2-1: 2.02±1.55<br>~~SiO 5-4: 0.35±0.23~~<br>SO 32-21: 2.01±1.14<br>SO 65-54: 0.54±0.13<br>CS 2-1: 4.98±2.16<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HC~~3~~N 11-10: 2.06±0.82<br>HC3N 24-23: 0.11±0.04<br>H2CO 30, 3-20, 2: 0.60±0.18<br>H2CO 32, 2-22, 1: 0.22±0.07<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>HCO + 1-0: 4.21±1.67<br>HCN 1-0: 7.37±3.30<br>H13CN 1-0: 1.45±0.41<br>C1<br>K4<br>1<br>0<br>1<br>2<br>3<br>4<br>CH3OH 2<br>1, 1-1<br>1, 0A: 0.61±0.33<br>CH3OH 4<br>2, 3-3<br>1, 2E: 0.44±0.13<br>HNCO 100, 10-90, 9: 0.18±0.05<br>CH3CHO 51, 4-41, 3: 0.42±0.20<br>Integrated Intensity Relative to13CO Normalized by 2 arcsec<br>Relative Intensity (2 arcsec Normalized)|||CH3CHO|CH3CHO|51, 4-41|, 3: 0.42±0.|20|||


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||S<br>|iO 2-1: 2<br>~~iO 54~~|.02±1.5<br>~~ 35±02~~|5<br>~~ 3~~|||
||<br>S<br>S|~~ -:~~<br>O 32-21:<br>O 65-54:|~~ ..~~<br> 2.01±1.<br> 0.54±0.|<br> 14<br> 13|||
||C|S 2-1: 4|.98±2.16||||


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||||||||
||H<br>H|CO + 1-<br>CN 1-0:|0: 4.21±<br> 7.37±3.|1.67<br> 30|||
||H|13CN 1-|0: 1.45±|0.41|||


6 4 2 0 2 4 6





6 4 2 0 2 4 6



Position (")


**Figure** **B3.** An enlarged view of the weak-shock region (light yellow background) in Figure B2, showing that some transitions,
such as H 2 CO 3 0 _,_ 3 _−_ 2 0 _,_ 2 and SO 6 5 _−_ 5 4, exhibit relatively little variation in intensity within this range, whereas other transitions
show significant intensity changes.

28





350


300


250


200


150


100



5


4


3


2


1









50


0

|T and d(SiO/13CO)/dP Along<br>H CO<br>2<br>K3 C1 K4 K5 K6|Col2|Col3|
|---|---|---|
|2CO<br>ror ±1<br>|r =|0.36<br>SiO<br>d(S|
||||
||||
||||
||||
||||
||||
|5<br>0<br>5<br>10<br>1<br>P (arcsec)|5<br>0<br>5<br>10<br>1<br>P (arcsec)|5<br>0<br>5<br>10<br>1<br>P (arcsec)|



**Figure** **B4.** Comparison between the rotational temperature ( _T_ rot ) derived from H 2 CO and the spatial derivative of the
SiO-to- [13] CO integrated intensity ratio along the outflow axis of SDC335. The horizontal axis represents the projected distance
from the central hot core, while the two vertical axes show _T_ rot (in K, left axis) and _d_ (SiO/ [13] CO)/ _d_ P where P is position (right
axis). The central light orange background indicates the extent of the hot core and its warm envelope, while the flanking light
yellow regions mark areas in the outflow where some molecules do not show significant weakening relative to [13] CO. Regions
with elevated SiO 5–4 gradients coincide with local temperature peaks, indicating strong shock heating and enhanced molecular
desorption.

K1 K2 K3 C1 K4 K5 K6 K7



100


75


50


25


0


100


75


50


25


0


100


75


50


25


0


100


75


50


25


0


100


75


50


25


0


100


75


50


25


0


100


75


50


25


0


100


75


50


25


0



24 14 4 4



24 14 4 4 24 14 4 4 2 ~~4~~ 1 ~~4~~ 44 14 24 4 4 14 24 4 4 14 24 4 4 14 24 4 4 14 24



29


SiO 31.2K

SO 35K

HC 3 N 131K


SiO 31.2K

SO 35K

HC 3 N 131K


SiO 6.25K

CS 7.05K

SO 9.23K

H [13] CN 4.14K

HC 3 N 28.82K


SiO 6.25K

CS 7.05K

SO 9.23K

H [13] CN 4.14K

HC 3 N 28.82K


HNCO 58K

H 2 CO 21.0K


CH 3 OH 45.4K


CH 3 CN 68~97K


HNCO 58K

H 2 CO 21.0K


CH 3 OH 45.4K


CH 3 CN 68~97K


HCO [+] 4.28K


CH 3 OH(A) 21.56K


CH 3 CHO(A) 16.51K


HCO [+] 4.28K


CH 3 OH(A) 21.56K


CH 3 CHO(A) 16.51K



Velocity offset (v-v LSR ) (km/s)


(a) High-velocity components in the 1.3 mm band;


K1 K2 K3 C1 K4 K5 K6 K7



24 14 4 4



24 14 4 4 24 14 4 4 2 ~~4~~ 1 ~~4~~ 44 14 24 4 4 14 24 4 4 14 24 4 4 14 24 4 4 14 24



Velocity offset (v-v LSR ) (km/s)


(b) High-velocity components in the 3 mm band;


K1 K2 K3 C1 K4 K5 K6 K7



24 14 4 4



24 14 4 4 24 14 4 4 2 ~~4~~ 1 ~~4~~ 44 14 24 4 4 14 24 4 4 14 24 4 4 14 24 4 4 14 24



Velocity offset (v-v LSR ) (km/s)


(c) Low-velocity components in the 1.3 mm band;


K1 K2 K3 C1 K4 K5 K6 K7



24 14 4 4



24 14 4 4 24 14 4 4 2 ~~4~~ 1 ~~4~~ 44 14 24 4 4 14 24 4 4 14 24 4 4 14 24 4 4 14 24



Velocity offset (v-v LSR ) (km/s)


(d) Low-velocity components in the 3 mm band.


**Figure** **B5.** The cumulative curves quantify the total line flux for each source, aiding comparison between knots and the central

core.

30


C. CHANNEL MAPS


We also produced channel maps of CO, [13] CO, SiO, SO, H 2 CO, and CH 3 OH using the combined ACA+TM1+TM2
data with angular resolution of 0 _._ 34 _[′′]_ . To suppress random noise in single channels, we integrated over _±_ 1 _._ 3 km s _[−]_ [1]

centered on each velocity (this is also why these data were not used for quantitative analysis). The maps show that
the high-velocity jet is located along the outflow axis, while the low-velocity component forms cavity-like structures.
The maximum velocities reach _±_ 36 km s _[−]_ [1] for SiO and _±_ 33 km s _[−]_ [1] for SO. Components with _|v|_ _>_ 12 km s _[−]_ [1] are
concentrated near the axis, whereas slower components attach to the cavity walls. H 2 CO and CH 3 OH follow similar
trends, with maximum velocities of _±_ 27 km s _[−]_ [1] and _±_ 24 km s _[−]_ [1], respectively. Several smaller-scale jets in other
directions are also discernible in these maps.

31


|-15 .0 km/s|. 120km/s|. 390km/s|
|---|---|---|
|-18.0 km/s|9.0 km/s|36.0 km/s|
|-21.0 km/s|6.0 km/s|33.0 km/s|
|-24.0 km/s|3.0 km/s|30.0 km/s|
|-27.0 km/s|0.0 km/s|27.0 km/s|
|-30.0 km/s|-3.0 km/s|24.0 km/s|
|-33.0 km/s|-6.0 km/s|21.0 km/s|
|-36.0 km/s|-9.0 km/s|18.0 km/s|
|-39.0 km/s|-12.0 km/s|15.0 km/s|

32


|-15 .0 km/s|. 120km/s|. 390km/s|
|---|---|---|
|-18.0 km/s|9.0 km/s|36.0 km/s|
|-21.0 km/s|6.0 km/s|33.0 km/s|
|-24.0 km/s|3.0 km/s|30.0 km/s|
|-27.0 km/s|0.0 km/s|27.0 km/s|
|-30.0 km/s|-3.0 km/s|24.0 km/s|
|-33.0 km/s|-6.0 km/s|21.0 km/s|
|-36.0 km/s|-9.0 km/s|18.0 km/s|
|-39.0 km/s|-12.0 km/s|15.0 km/s|

33


|-15 .0 km/s|. 120km/s|. 390km/s|
|---|---|---|
|-18.0 km/s|9.0 km/s|36.0 km/s|
|-21.0 km/s|6.0 km/s|33.0 km/s|
|-24.0 km/s|3.0 km/s|30.0 km/s|
|-27.0 km/s|0.0 km/s|27.0 km/s|
|-30.0 km/s|-3.0 km/s|24.0 km/s|
|-33.0 km/s|-6.0 km/s|21.0 km/s|
|-36.0 km/s|-9.0 km/s|18.0 km/s|
|-39.0 km/s|-12.0 km/s|15.0 km/s|

34


|-15 .0 km/s|. 120km/s|. 390km/s|
|---|---|---|
|-18.0 km/s|9.0 km/s|36.0 km/s|
|-21.0 km/s|6.0 km/s|33.0 km/s|
|-24.0 km/s|3.0 km/s|30.0 km/s|
|-27.0 km/s|0.0 km/s|27.0 km/s|
|-30.0 km/s|-3.0 km/s|24.0 km/s|
|-33.0 km/s|-6.0 km/s|21.0 km/s|
|-36.0 km/s|-9.0 km/s|18.0 km/s|
|-39.0 km/s|-12.0 km/s|15.0 km/s|

35


|-15 .0 km/s|. 120km/s|. 390km/s|
|---|---|---|
|-18.0 km/s|9.0 km/s|36.0 km/s|
|-21.0 km/s|6.0 km/s|33.0 km/s|
|-24.0 km/s|3.0 km/s|30.0 km/s|
|-27.0 km/s|0.0 km/s|27.0 km/s|
|-30.0 km/s|-3.0 km/s|24.0 km/s|
|-33.0 km/s|-6.0 km/s|21.0 km/s|
|-36.0 km/s|-9.0 km/s|18.0 km/s|
|-39.0 km/s|-12.0 km/s|15.0 km/s|

36


|-15 .0 km/s|. 120km/s|. 390km/s|
|---|---|---|
|-18.0 km/s|9.0 km/s|36.0 km/s|
|-21.0 km/s|6.0 km/s|33.0 km/s|
|-24.0 km/s|3.0 km/s|30.0 km/s|
|-27.0 km/s|0.0 km/s|27.0 km/s|
|-30.0 km/s|-3.0 km/s|24.0 km/s|
|-33.0 km/s|-6.0 km/s|21.0 km/s|
|-36.0 km/s|-9.0 km/s|18.0 km/s|
|-39.0 km/s|-12.0 km/s|15.0 km/s|


</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Method for deriving H2CO rotational/kinetic temperatures with RADEX",
  "failed_quote": "This pattern, combined with the correlation between SiO gradients and H2CO rotational temperatures derived with RADEX (T. Möller et al. 2017) following methods similar to N. Izumi et al. (2024) (Fig. B4), indicates excitation primarily driven by local thermal heating in shocked gas."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Extract 3 mm and 1.3 mm spectra at the seven bright knots along the walls of the jet-driven outflow cavity and identify transitions",
  "failed_quote": "In total, 35 transitions from 22 molecular species were identified at the 3 mm and 1.3 mm bands (see Appendix Table A1)."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Model H2CO 3-2 line ratios along the outflow axis using non-LTE radiative transfer code RADEX and compare with the spatial derivative of SiO/13CO intensity ratio",
  "failed_quote": "This pattern, combined with the correlation between SiO gradients and H2CO rotational temperatures derived with RADEX (T. Möller et al. 2017) following methods similar to N. Izumi et al. (2024) (Fig. B4), indicates excitation primarily driven by local thermal heating in shocked gas."
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "Non-LTE radiative transfer modeling of H2CO 3-2 transitions to derive rotational/kinetic temperatures along the outflow",
  "failed_quote": "This pattern, combined with the correlation between SiO gradients and H2CO rotational temperatures derived with RADEX (T. Möller et al. 2017) following methods similar to N. Izumi et al. (2024) (Fig. B4), indicates excitation primarily driven by local thermal heating in shocked gas."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "Molecular species in the SDC335 outflow are regulated by three main mechanisms: (1) direct entrainment from the natal core (CO, 13CO, HCO+, H2CO, CS, HC3N), (2) shock-induced grain sputtering and high-temperature shock chemistry (SiO, SO, HCN, H13CN, DCN, HC3N), and (3) thermal desorption and gas-phase chemistry driven by shock heating (CH3OH, HNCO, CH3CHO, CH3CN, CH3OCHO).",
  "failed_quote": "The PCA distribution naturally separates molecules into three quadrants, corresponding to three predominant classes: (1) species entrained from the dense core by the outflow (e.g., CO, HCO+, CS, HC3N); (2) molecules released into the gas phase or newly formed in jet-induced shocks (e.g., SiO, SO, HCN, DCN); and (3) molecules thermally excited by shock heating and subsequent gas-phase or desorption processes (e.g., CH3OH, CH3CHO, CH3CN, HNCO, CH3OCHO)."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "Elevated abundances of CH3OH, HNCO, and COMs at the knots are primarily driven by local thermal heating in shocked gas that sublimates icy mantles and drives high-temperature gas-phase chemistry.",
  "failed_quote": "This pattern, combined with the correlation between SiO gradients and H2CO rotational temperatures derived with RADEX (T. Möller et al. 2017) following methods similar to N. Izumi et al. (2024) (Fig. B4), indicates excitation primarily driven by local thermal heating in shocked gas."
 }
]
```
