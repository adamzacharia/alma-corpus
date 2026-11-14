# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025PASJ...77L..55S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Publications of the Astronomical Society of Japan_, 2024, **00**, 1–7
doi: 10.1093/pasj/xxx000
Advance access publication date:

## **Circum-nuclear eccentric gas flow in the Galactic Center re-** **vealed by ALMA CMZ Exploration Survey (ACES)**


**Yoshiaki** **S** **OFUE** **[1*]** **,** **Tomoharu** **O** **KA** **[2]** **,** **Steven** **N.** **L** **ONGMORE** **[3,4]** **Daniel** **W** **ALKER** **[5]** **,** **Adam** **G** **INSBURG** **[6]** **,**
**Jonathan** **D.** **H** **ENSHAW** **[3,7]** **,** **John** **B** **ALLY** **[8]** **,** **Ashley** **T.** **B** **ARNES** **[9]** **,** **Cara** **B** **ATTERSBY** **[10]** **,** **Laura** **C** **OLZI** **[11]** **,**
**Paul** **H** **O** **[12]** **,** **Izaskun** **J** **IMENEZ** **-S** **ERRA** **[11]** **,** **J.** **M.** **Diederik** **K** **RUIJSSEN** **[4]** **,** **Elizabeth** **M** **ILLS** **[13]** **,** **Maya** **A.**
**P** **ETKOVA** **[14]** **,** **Mattia** **C.** **S** **ORMANI** **[15]** **,** **Jennifer** **W** **ALLACE** **[10]** **,** **Jairo** **A** **RMIJOS** **-A** **BENDAÑO** **[17]** **,** **Katarzyna**
**M.** **D** **UTKOWSKA** **[18]** **,** **Rei** **E** **NOKIYA** **[19]** **,** **Pablo** **G** **ARCÍA** **[21,22]** **,** **Savannah** **G** **RAMZE** **[6]** **,** **Christian** **H** **ENKEL** **[24]** **,**
**Pei-Ying** **H** **SIEH** **[19]** **,** **Yue** **H** **U** **[25]** **,** **Katharina** **I** **MMER** **[9]** **,** **Yuhei** **I** **WATA** **[26,27]** **,** **Janik** **K** **AROLY** **[28]** **,** **Ralf** **S.**
**K** **LESSEN** **[29,30,31,32]** **,** **Kotaro** **K** **OHNO** **[1]** **,** **Mark** **R.** **K** **RUMHOLZ** **[33]** **,** **Dani** **L** **IPMAN** **[10]** **,** **Mark** **R.** **M** **ORRIS** **[34]** **,**
**Francisco** **N** **OGUERAS** **-L** **ARA** **[9]** **,** **Jaime** **E.** **P** **INEDA** **[37]** **,** **Sergio** **M** **ARTÍN** **[38,39]** **,** **Miguel** **Angel** **R** **EQUENA** **-**
**T** **ORRES** **[40]** **,** **Víctor** **M.** **R** **IVILLA** **[11]** **,** **Denise** **R** **IQUELME** **-V** **ÁSQUEZ** **[41]** **,** **Álvaro** **Sánchez-Monge** **[42,43]** **,** **Miriam**
**G.** **S** **ANTA** **-M** **ARIA** **[6]** **, Howard A.** **S** **MITH** **[31]** **Volker** **T** **OLLS** **[31]** **, and Q. Daniel** **W** **ANG** **[45]**


1 Institute of Astronomy, The University of Tokyo, Mitaka, Tokyo 181-0015, Japan
2 Department of Physics, Faculty of Science and Technology, Keio University, 3-14-1 Hiyoshi, Yokohama, Kanagawa 223-8522, Japan
3 Astrophysics Research Institute, Liverpool John Moores University, IC2, Liverpool Science Park, 146 Brownlow Hill, Liverpool L3 5RF, UK
4 Cosmic Origins Of Life (COOL) Research DAO, https://coolresearch.io
5 UK ALMA Regional Centre Node, Jodrell Bank Centre for Astrophysics, Oxford Road, The University of Manchester, Manchester M13 9PL, United Kingdom
6 Department of Astronomy, University of Florida, P.O. Box 112055, Gainesville, FL 32611
7 Max Planck Institute for Astronomy, Königstuhl 17, D-69117 Heidelberg, Germany
8 Center for Astrophysics and Space Astronomy; Department of Astrophysical and Planetary Sciences; University of Colorado, Boulder, CO 80389, USA
9 European Southern Observatory (ESO), Karl-Schwarzschild-Strasse 2, D-85748 Garching, Germany
10 Department of Physics, University of Connecticut, 196A Auditorium Road, Unit 3046, Storrs, CT 06269, USA
11 Centro de Astrobiología (CAB), CSIC-INTA, Carretera de Ajalvir km 4, Torrejón de Ardoz, 28850 Madrid, Spain
12 AS/NTU Astronomy-Mathematics Building, Roosevelt Rd, Taipei 10617, Taiwan
13 Department of Physics and Astronomy, University of Kansas, 1251 Wescoe Hall Drive, Lawrence, KS 66045, USA
14 Space, Earth and Environment Department, Chalmers University of Technology, SE-412 96 Gothenburg, Sweden
15 Como Lake centre for AstroPhysics (CLAP), DiSAT, Università dell’Insubria, via Valleggio 11, 22100 Como, Italy
10 Department of Physics, University of Connecticut, 196A Auditorium Road, Unit 3046, Storrs, CT 06269, USA
17 Observatorio Astronómico de Quito, Observatorio Nacional, Escuela Politécnica Nacional, Interior del Parque La Alameda, 170136, Quito, Ecuador
18 Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA Leiden, The Netherlands
19 National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan
21 Chinese Academy of Sciences South America Center for Astronomy, National Astronomical Observatories, CAS, Beijing 100101, China
22 Instituto de Astronomía, Universidad Católica del Norte, Av. Angamos 0610, Antofagasta, Chile
24 MPIfR, Auf dem Hügel 69, Bonn, Germany
25 Institute for Advanced Study, 1 Einstein Drive, Princeton, NJ 08540, USA
26 Mizusawa VLBI Observatory, National Astronomical Observatory of Japan, 2-12 Hoshigaoka, Mizusawa, Oshu, Iwate 023-0861, Japan
27 Astronomical Science Program, Graduate Institute for Advanced Studies, SOKENDAI, 2-21-1 Osawa, Mitaka, Tokyo, 181-8588, Japan
28 Department of Physics and Astronomy, University College London, Gower Street, London WC1E 6BT, UK
29 Universität Heidelberg, Zentrum für Astronomie, Institut für Theoretische Astrophysik, Albert-Ueberle-Str. 2, 69120 Heidelberg, Germany
30 Universität Heidelberg, Interdisziplinäres Zentrum für Wissenschaftliches Rechnen, Im Neuenheimer Feld 225, 69120 Heidelberg, Germany
31 Center for Astrophysics _|_ Harvard & Smithsonian, 60 Garden Street, Cambridge, MA, 02138, USA
32 Elizabeth S. and Richard M. Cashin Fellow at the Radcliffe Institute for Advanced Studies at Harvard University, 10 Garden Street, Cambridge, MA 02138, USA
33 Research School of Astronomy and Astrophysics, Australian National University, Cotter Road, Weston ACT 2611, Australia
34 Department of Physics and Astronomy, University of California, Los Angeles, CA 90095, USA
37 MPI for Extraterrestrial Physics, Giessenbachstr. 1, D-85748, Garching, Germany
38 European Southern Observatory, Alonso de Córdova, 3107, Vitacura, Santiago 763-0355, Chile
39 Joint ALMA Observatory, Alonso de Córdova, 3107, Vitacura, Santiago 763-0355, Chile
40 Department of Physics, Astronomy, and Geosciences, Towson University, Towson, MD 21252, USA
41 Departamento de Astronomía, Universidad de La Serena, Raúl Bitrán 1305, La Serena, Chile
42 Institut de Ciències de l’Espai (ICE), CSIC, Campus UAB, Carrer de Can Magrans s/n, E-08193, Bellaterra (Barcelona), Spain
43 Institut d’Estudis Espacials de Catalunya (IEEC), E-08860, Castelldefels (Barcelona), Spain
45 Department of Astronomy, University of Massachusetts, Amherst, MA 01003, USA


_∗_ E-mail: sofue@ioa.s.u-tokyo.ac.jp


ORCID: 0000-0002-4268-6499, 0000-0002-5566-0634, 0000-0001-6353-0170, 0000-0001-7330-8856, 0000-0001-6431-9633, 0000-0001-9656-7682, 0000-00018135-6612, 0000-0003-0410-4504, 0000-0002-6073-9320, 0000-0001-8064-6394, 0000-0002-3412-4306, 0000-0003-4493-8714, 0000-0002-8804-0212, 00000001-8782-1992, 0000-0002-6362-8159, 0000-0001-6113-6241, 0009-0002-7459-4174, 0000-0003-3341-6144, 0000-0003-0980-6871, 0000-0001-0000-0000,


**Received:**, **Accepted:**
© 2024. Astronomical Society of Japan.

**2** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0


0000-0002-1313-429X, 0000-0002-7495-4005, 0000-0001-9155-3978, 0000-0002-8455-0805, 0000-0003-4140-5138, 0000-0002-9255-4742, 0000-0001-59963600, 0000-0002-0560-3172, 0000-0002-4052-2394, 0000-0003-3893-854X, 0000-0002-5776-9473, 0000-0002-6753-2066, 0000-0002-6379-7593, 0000-00023972-1978, 0000-0001-9281-2919, 0009-0009-5346-7329, 0000-0002-2887-5859, 0000-0001-5389-0535, 0000-0002-3078-9482, 0000-0002-3941-0360, 00000003-1841-2241, 0000-0002-9279-4041


**Abstract**

We analyze the CS ( _J_ = 2 _−_ 1) line cube from the internal data release obtained by the large-scale program "ALMA CMZ Exploration Survey
(ACES)" to investigate the kinematic structure of the innermost _∼_ 10 pc region of the Galaxy, which contains the high-velocity compact cloud
(HVCC) at ( _l,b,v_ LSR ) _∼_ (+0 _[◦]_ _._ 02 _,_ _−_ 0 _[◦]_ _._ 02 _,_ 100 km s _[−]_ [1] ) (hereafter G0.02). The longitude-velocity diagram (LVD) of the cloud draws an elliptical
structure, which is interpreted as an orbital trajectory in the ( _l, v_ LSR ) space of a noncircular (eccentric) motion of the molecular gas in the
gravitational potential of an extended mass distribution in the central 10 pc of the Galaxy. We argue that G0.02 is a kinematic tracer of the inner
potential, a rare case of a dense gas following an eccentric orbit in the nuclear gravitational field.


**Keywords:** Galaxy : center — Galaxy : structure — ISM : clouds — ISM : molecules — ISM : kinematics and dynamics



**1** **Introduction**


In our recent study of the molecular gas distribution in the central molecular zone (CMZ) (Sofue et al. 2025)), we have identified six arms named "Galactic-Center Arms (GCAs) I to VI" by
analyzing the molecular-line cube data of the [13] CO ( _J_ = 1 _−_ 0)
and HCN ( _J_ = 4 _−_ 3 ) lines from single dish observations, and CS
( _J_ = 2 _−_ 1 ) and H [13] CN ( _J_ = 1 _−_ 0) lines from ALMA (Atacama
Large Millimeter/submillimeter Array) taken by the large project
ACES (ALMA CMZ Exploration Survey) (S. Longmore et al. in
preparation). GCA I and II compose the 120 pc molecular ring that
shares about 90% of the CMZ mass, Arm III to V are intermediate
arms, and Arm VI is the innermost molecular arm of radius _∼_ 3 pc
known as the circumnuclear disc (CND). We have tried to understand these arms under a unified view of Galactic arms and rings
rotating in the common gravitational potential around Sgr A _[∗]_ .
In addition to such "ordinary" arms represented by straight
ridges in the longitude-velocity diagrams (LVD), there are LV features that exhibit high-velocity noncircular motions, which cannot
be attributed to the arms in ordinary Galactic rotation. The CND of
radius _∼_ 3 pc is well known for exhibiting such peculiar motions
ALMA (Hsieh et al. 2021).
The high-velocity compact cloud (HVCC; hereafter
G+0.02-0.02+100, or G0.02) located at ( _l,_ _b,_ _v_ LSR ) _≃_
(0 _[◦]_ _._ 02 _, −_ 0 _[◦]_ _._ 02 _,_ +100 km s _[−]_ [1] ) at a projected distance of 10
pc from Sgr A _[∗]_ is the most typical example of such clouds showing anomalous kinematics (Oka et al. 1999; Oka et al. 2008; Oka
et al. 2022; Iwata et al. 2023). G0.02 is outside the CND and was
discovered by CO-line observations using the Nobeyama 45 m
telescope and is named CO 0.02-0.02 (Oka et al. 1999). It has
a size of _∼_ 3 pc, a velocity width as large as _∼_ 50 km s _[−]_ [1], a
molecular mass of _∼_ 10 [5] _M_ _⊙•_ inferred from the luminosity of the
12 CO line. It is suggested that the origin of the extreme physical
condition is due to a strong disturbance due to a nearby supernova
explosion (Oka et al. 2008; Iwata et al. 2023).
In this paper, we examine the kinematics of the LV features of
G0.02 and related structures from the point of view of galactic
dynamics by analyzing the 3D cube of the CS ( _J_ = 2 _−_ 1 ) line
emission observed with ALMA by ACES. We adopted a distance
_R_ 0 = 8 _._ 2 kpc to the GC, close to the recent measurement (Gravity
Collaboration et al. 2019).


**2** **Longitude-velocity ellipse**


2.1 Data

The molecular line cubes in this work were taken from the inter
nal release version of the 12m + 7m + TP (Total Power) mode
data from the ALMA Cycle 8 Large Program "ALMA Central



Molecular Zone Exploration Survey" (ACES, 2021.1.00172.L;
Longmore et al. in preparation). ACES observed the CMZ in
ALMA Band 3, covering a frequency range of _∼_ 86–101 GHz
across six spectral windows of varying spectral resolution and
bandwidth. See Paper I (Sofue et al. 2025) for the data used in
this paper.
In this work, we use cubes in the CS ( _J_ = 2 _−_ 1 ) line at a frequency of 97.9810 GHz with an angular resolution of 2 _[′′]_ _._ 21 and an
rms noise of 0.0038 Jy beam _[−]_ [1] (0.10 K) with velocity channels of
1.45 km s _[−]_ [1] . We also have the H [13] CN ( _J_ = 1 _−_ 0) line at 86.3399
GHz, but the velocity coverage ( _−_ 200 _≤_ _v_ LSR _≤_ 200 km s _[−]_ [1] ) in
the current internal release data was not sufficient for the purpose
of this paper to explore G0.02. So, we restricted our analysis to the
CS ( _J_ = 2 _−_ 1 ) line that covers _−_ 220 _≤_ _v_ LSR _≤_ 220 km s _[−]_ [1] . We
note that a preliminary analysis in H [13] CN ( _J_ = 1 _−_ 0) revealed almost the same kinematical properties of G0.02 as those of the CS
( _J_ = 2 _−_ 1 ) line.
The intensity scales are in Jy beam _[−]_ [1] (1 Jy beam _[−]_ [1] = 26 _._ 1 K
in brightness temperature at 98 GHz). The used CS ( _J_ = 2 _−_ 1 )
cube covers the CMZ at _−_ 0 _[◦]_ _._ 6 _[<]_ _∼_ _l_ _[<]_ _∼_ +0 _[◦]_ _._ 9 and _−_ 0 _[◦]_ _._ 3 _[<]_ _∼_ _b_ _[<]_ _∼_ +0 _[◦]_ _._ 1
with spatial and velocity grids of ( 0 _[′′]_ _._ 5 _×_ 0 _[′′]_ _._ 5 _×_ 0 _._ 15 km s _[−]_ [1] ). In
the present work, we cut out a region at _−_ 0 _[◦]_ _._ 25 _≤_ _l ≤_ +0 _[◦]_ _._ 15 and
_−_ 0 _[◦]_ _._ 1 _≤_ _b ≤_ +0 _[◦]_ for a detailed analysis of the circum-nuclear region centered on Sgr A _[∗]_ .


2.2 Mini-CMZ and G0.02


Figure 1 (panel A) shows a moment 0 map of the CS ( _J_ = 2 _−_ 1 )
line integrated from _−_ 220 to +220 km s _[−]_ [1] . Figure 2 enlarges
the region around G0.02, which appears as a compact triangular cloud composed of several bright knots and arcs at ( _l, b_ ) _∼_
(0 _[◦]_ _._ 02 _, −_ 0 _[◦]_ _._ 02) . It also exhibits an arc-shaped cavity concave to
G0.005-0.028, as reported by Oka et al. (2008) .
In panel B of figure 1, we show a longitude-velocity diagram
(LVD) of the maximum intensity along latitude at each Galactic
longitude in the CS ( _J_ = 2 _−_ 1 ) line between _l_ = _−_ 0 _[◦]_ _._ 25 and
+0 _[◦]_ _._ 15 . Comparison of this figure with the LVD of the Galactic
plane survey in the [12] CO line (Dame et al. 2001) reveals a nice
similarity in such a sense that the LVD in figure 1 is a superposition of ordinary arms as horizontal LV ridges and largely tilted LV
ridges due to the rotating inner disc of high velocity. We call the
high-velocity region at _|l −_ _l_ SgrA _[∗]_ _|_ _[<]_ _∼_ 0 _[◦]_ _._ 07 the "mini-CMZ".
Panel C shows a close-up of the mini-CMZ, highlighting the elliptical structure marked by the white ellipse that traces the eastern
(E) and western (W) arcs. Some well-known molecular features
are marked, including the circumnuclear disc (CND) (Tsuboi et al.
2018), 20-km s _[−]_ [1] Cloud (20kmC) (Takekawa et al. 2017), 50-km
s _[−]_ [1] Cloud (50kmC) (Tsuboi et al. 2009), high-velocity compact

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **3**


Obs. CS ( _J_ = 2 _−_ 1 ) Model


(A)


(B)



(C)


(D)


**Fig. 1.** [A] ACES Moment 0 map of the CS ( _J_ = 2 _−_ 1 ) line in Jy beam _[−]_ [1] m
s _[−]_ [1] . The circle indicates G0.02 and the dashed ellipse outlines an inclined
10-pc ring. [B] LVD of the maximum intensity in Jy beam _[−]_ [1] . Note the
high-velocity structures at _|l −_ _l_ Sgr A _∗_ _|_ _[<]_ _∼_ [0] _[◦]_ _[.]_ [07] [(10] [pc),] [which] [we] [call] [the]
’mini CMZ’. [C] Same, but enlarged. The LV ellipse and some well known
objects are indicated. [D] Same, but in the H [13] CN ( _J_ = 1 _−_ 0) line. The
data were taken from the internal release of ACES (Longmore et al. in
preparation). Alt text: Moment 0 map and LVDs in the central 10 pc region
of the GC in the CS ( _J_ = 2 _−_ 1 ) line from ACES.


cloud (HVCC=CO 0.02-0.02) (Oka et al. 1999), and the ’Tadpole’
(Kaneko et al. 2023). Panel D shows the same, but in the H [13] CN
( _J_ = 1 _−_ 0) line, highlighting the LV ridge shaped like an arc with
less contamination of low-density gas from outer CMZ structures.
We also stress that the high-positive velocity wing (see below) is
less evident on the H [13] CN ( _J_ = 1 _−_ 0) line than in CS ( _J_ = 2 _−_ 1 ).


2.3 LV Ellipse fit

G0.02 (HVCC (Oka et al. 2008)) is the main part of the E Arc,
protruding from ( _l,v_ LSR ) _∼_ (0 _[◦]_ _._ 00 _,_ _−_ 10 km s _[−]_ [1] ) and extending



**Fig. 2.** [Top left] Moment 0 map of G0.02 in the CS ( _J_ = 2 _−_ 1 ) line (Jy/b
m s _[−]_ [1] ) at _v_ LSR _≥_ 75 km s _[−]_ [1] . Contours are every 2 Jy beam _[−]_ [1] m s _[−]_ [1] .

[Bottom left] LVD of maximum intensity, where horizontally extended components have been subtracted. Contours are every 0.05 Jy beam _[−]_ [1] .

[Right panels] Simulation of G0.02 for a similar condition as F in figure
3. The general property is well reproduced except for the high velocity
straight LV wing. Alt text: Comparison of simulated moment 0 map and
LVD with the observation.


toward high velocity reaching _∼_ 170 km s _[−]_ [1] with the highest intensity near ( _l,v_ LSR ) _∼_ (0 _[◦]_ _._ 015 _,_ 120 km s _[−]_ [1] ) . Another LV arc is
recognized at the western end of the mini-CMZ, marked W Arc
on the opposite side with respect to Sgr A _[∗]_ . The large ellipse in
panel C of figure 1 approximately traces the E and W arcs, and the
faint ridge of a long segment of the western ellipse. In figure 3
(panel A) we plot the positions of the LV ridges read from panel C
of figure 1, which can be fitted by a tilted ellipse expressed by

_v_ LSR = _A x ± B_ � 1 _−_ (∆ _x/a_ ) [2] _,_ (1)


where _A_ = _dv/dl_ = 1600 km s _[−]_ [1] per degree, _B_ = 100 km s _[−]_ [1],
_a_ = 0 _[◦]_ _._ 065 (9.3 pc), and ∆ _x_ = _l_ + 0 _[◦]_ _._ 046 with the center offset
by 0 _[◦]_ _._ 01 = 1 _._ 4 pc to the east from Sgr A _[∗]_ . The entire ellipse is
geometrically equivalent to an LV feature that represents a ring of
radius _R_ = 9 _._ 3 pc, which rotates at _A_ = 104 km s _[−]_ [1] and expands
at _B_ = 100 km s _[−]_ [1] . The E Arc for G0.02 is located 0 _[◦]_ _._ 07 = 10
pc from Sgr A _[∗]_ . The rotation curve in the central 10 pc has been
measured only approximately due to uncertainties due to suspected
non-circular motions (Sofue 2013). So, here we adopt the value for
_A_ to represent the rotation velocity, _V_ rot _∼_ 104 km s _[−]_ [1], at _R ∼_ 10

pc.


**3** **Kinematic tracer of the potential**


3.1 Properties of G0.02

Oka et al. (1999) estimate the molecular mass to be _M_ mol _∼_
10 [5] _M_ _⊙•_ from the CO-line luminosity. The radius of the G0.02
cloud is measured as _r_ _∼_ ~~_[√]_~~ _σ_ _l_ _σ_ _b_ _∼_ 0 _._ 7 pc on the moment 0 map
(Figure 2). The full width at half maximum of the peak intensity
component is measured to be 2 _σ_ _v_ _∼_ 56 km s _[−]_ [1] . The correspond

**4** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0



ing Virial mass is then calculated as _M_ vir _∼_ 3 _rσ_ _v_ [2] _[/G]_ _[∼]_ [4] _[×]_ [10] [5] _[M]_ _⊙•_ [.]
Adopting a wider extent, Oka et al. (1999) obtain an even higher
Virial mass of _∼_ 3 _×_ 10 [6] to 10 [7] _M_ _⊙•_ . Therefore, the cloud is not
gravitationally bound. The energy required to accelerate the gas
to the observed velocity width is then _E_ K _[>]_ _∼_ 10 [52] erg. This led
to the idea that G0.02 is disturbed by supernova explosions in the
cavity at G+0.005-0.030 (Oka et al. 1999). In this paper, we propose an alternative model that attributes the large velocity width
to the shear of orbital motion of gas streaming in the gravitational
potential.
The moment 0 map in figure 1 suggests that G0.02 is part of an
ellipse elongated in the direction of PA _∼_ 74 _[◦]_ with the major and
minor radii _a ∼_ 0 _[◦]_ _._ 07( _∼_ 10 pc) and _b ∼_ 0 _[◦]_ _._ 01( _∼_ 1 _._ 4 pc), respectively, or the axial ratio of _b/a ∼_ 0 _._ 14 . This suggests that G0.02 is
part of a molecular ring with the rotation axis at a position angle
of _∼−_ 16 _[◦]_ . The LV ellipse in figure 3 (panel A-c) is geometrically
equivalent to a ring of radius _R_ = 9 _._ 3 pc that rotates at 104 km s _[−]_ [1]

and expands at 100 km s _[−]_ [1] in the LVD.


3.2 Non-circular motion in the extended-mass potential

In order to explain these kinematical properties, we simulate the
evolution of a molecular cloud orbiting in the gravitational potential in the central stellar bulge. The cloud is represented by
an ensemble of _N_ test particles that are initially distributed in a
small radius sphere with _r_ c = 0 _._ 1 _r_ 0 ( _∼_ 1 pc) of velocity dispersion _σ_ _v_ = 0 _._ 1 _v_ 0 ( _∼_ 10 km s _[−]_ [1] ) centered on ( _x,y,z,v_ _x_ _,v_ _y_ _,v_ _z_ ) (3D
Cartesian coordinates and velocities) in the phase space. Here, _r_ 0
and _v_ 0 are the scale radius and rotation velocity of the potential,
normalized to 1 and non-dimensionalized. The time is normalized
by the rotational period _P_ = 2 _πr_ 0 _/v_ 0 . We adopt a potential expressed by
Φ = 1 _/_ 2 _v_ 0 [2] [ln] [�] Σ( _x_ _i_ _/q_ _i_ ) [2] [�] _,_ (2)


where _q_ _x_ : _q_ _y_ : _q_ _z_ ( = _q_ below) gives the axial ratio of the bar
(Binney et al. 1991). A special case of _q_ = 1 : 1 : 1 represents
a spherical potential, producing a flat rotation curve.
The integration was performed for a given initial condition without resonance analysis, so that the motion does not necessarily realize closed resonant orbits. In the test particle simulations here,
the hydrodynamic and MHD effects are not evaluated, so the results apply only to the overall orbital behavior in the gravitational
potential. We also neglect the effect of feedback by nuclear activity, except for the expanding ring model. The general agreement
is that solving the initial value problem does not rule out other
models, including those concluded here as unlikely. The results of
calculation are displayed in the rest frame of the Cartesian coordinates because the angular speed of the observer (Sun) is sufficiently slower than that of the system considered. In figure 3 we
compare the simulated results for various cases of initial condition
and gravitational potential with the observed moment 0 map, LVD
and line profile of G0.02 shown in panel A.


3.3 Simulation

**3.3.1** **Classification of PVD (LVD)**
For convenience in describing the simulated PVDs (LVDs), we
first classify the anticipated properties considering the current observations in the edge-on discs of the Galaxy and spiral galaxies in
the radio lines.

_I_ -type: This is an inclined straight ridge in the PVD because of the
rigid-body motion of a disc or a circular rotation of a ring.
_U_ -type: This is typical for an eccentric motion in a potential of an



extended-mass distribution and barred potential.
_II_ -type: The so-called parallelogram is a combination of _I_ - and _U_ types.
_O, C_ -type: This happens for a rotating ring superposed by an expanding motion.


**3.3.2** **Rotating ring in spherical potential (** _I_ **-type) - Panel B (fig-**
**ure 3) -**

The simplest model is a molecular ring rotating in a spherical potential ( _q_ = 1 : 1 : 1 ) as shown in panel B in figure 3. The projection
in the ( _x,y_ ) and ( _x,z_ ) planes exhibits an ellipse, and the PVD has
_I_ -type. However, such a circular rotation is realized only if the
gas disc is in hydrostatic equilibrium in the radial direction, which
may not be realistic here. So, in the next subsection, we explore
more general orbits in the same potential.


**3.3.3** **SN-induced local expanding cloud - Panel C -**
Since its discovery, G0.02 has been modeled as an expanding
molecular shell around a supernova remnant near the center of
the arc structure (Oka et al. 1999; Oka et al. 2008; Oka et al.
2022; Iwata et al. 2023). Panel C of figure 3 shows a simulation
of such an expanding shell by giving a local radial motion from
the cloud’s center to each particle. The result explains the large
velocity width, but the line profile is symmetric with respect to the
systemic velocity.


**3.3.4** **Expanding ring in a spherical potential (** _O_ **-type) - Panel D,**

**E -**

The _O_ -type PVD has often been explained by an expanding ring
(Kaifu et al. 1972; Scoville 1972; Sofue 2017). We examine this
model by adding a radial motion to the orbits in the spherical potential. Figure 3 D shows the result for an expanding motion of
_v_ rad _∼_ 0 _._ 75 _v_ 0, and panel E shows a cut at _t ∼_ 1 . The radial motion
was artificially added to each test particle at a certain epoch when
the cloud had reached the final shape. This model well reproduces
the _O_ -type LVD observed in the mini-CMZ shown in panel A. As
to the origin of such an expanding motion we may refer to the
focusing wave model in a magnetized nuclear gas disc, which postulates the high-efficiency convergence of kinetic energy released
at the nucleus to a focal ring at radius _∼_ 4 _._ 4 _h_, where _h_ is the scale
height of the disc (Sofue 2020). The required kinetic energy of
expansion of G0.02 is of the order of _E_ = 1 _/_ 2 _Mv_ expa [2] _[∼]_ [10] [51] [ erg.]
Since a few tens of percent of the energy released at the nucleus
converges to the cloud, a total energy of _∼_ 10 [52] of nuclear activity
would be sufficient to excite the expanding motion of G0.02.


**3.3.5** **Eccentric motion in a spherical potential (** _U_ **-type) - Panel**
**F, G -**
In a spherical potential ( _q_ = 1 : 1 : 1 ) of an extended mass distribution, the orbit of a gas element is generally eccentric and draws
a rosette pattern (Kruijssen et al. 2015). Figure 3 F shows a result of the simulation. The entire orbit forms a complicated pattern, showing a _U_ -typePVD. However, if we cut part of the orbit
as in panel G, it reproduces the observed properties such as the
curved arc near the tangential direction, the arc-shaped PVD, and
the broad line profile that increases toward the sharp end. Thus,
we conclude that the morphology in the sky and the high-velocity
noncircular motion in the PVD of G0.02 are understood to be due

to an eccentric orbit of the gas flow in a potential due to an extended mass distribution. However, in the following, we consider
alternative models that may also explain the LV properties.

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **5**


(A-a) (b) (c) (d)


**Fig. 3.** Panel [A] (a) Observed CS ( _J_ = 2 _−_ 1 )line intensity map at _|v_ LSR _| ≥_ 75 km s _[−]_ [1] . (b) LVD with broad components being subtracted. (c) Fitted LV
ellipse (Eq. 1). (d) Line profile of G0.02. [B] Circular orbit of a cloud in a spherical potential ( _q_ = 1 : 1 : 1 ) plotted in the ( _x,y_ ) (gray dots), ( _x,z_ ) (black),
and ( _x,v_ ) (PVD) planes for initial condition ( **r** ; **v** ) = (1 _,_ 0 _,_ 0 _._ 3; 0 _.,_ 1 _,_ 0) (in normalized units). The 3rd panel shows the line profile at _x ∼_ 1 . Scales are
arbitrary. [C] Same, but SN-induced local expansion from the cloud center of _v_ SN = 0 _._ 75 at _t_ = 1 is added. [D] ( _O_ -type) Circular flow with radial expansion
from the GC at _v_ expa = 0 _._ 75 added, simulating the expanding ring model due to a nuclear activity. [E] Same as D but part at _t ∼_ 1, simulating G0.02. [F]
( _U_ -type) Eccentric flow in a spherical potential with initial condition ( **r** ; **v** ) = (1 _,_ 0 _,_ 0 _._ 3; 0 _._ 3 _,_ 0 _._ 8 _,_ 0 _._ 3) plotted every _δt_ = 0 _._ 1 from _t_ = 0 to 3 . [G] ( _U_ -type)
Same, but part at _t ∼_ 2, simulating G0.02. [H] ( _U_ -type) Eccentric flow in a disc potential ( _q_ = 1 : 1 : 0 _._ 63 ), showing vertical oscillation at a period of _∼_ 0 _._ 6
and a _∞_ shape on the sky. [I] ( _U_, _II_ -type) Same, but in a tri-axial bar potential ( _q_ = 1 : 0 _._ 85 : 0 _._ 63 ). Note that the wide and lopsided line profile is well
reproduced. Alt text: _N_ -particle simulations of a cloud orbiting in the gravitational potential in the GC.



**3.3.6** **Non-circular** **flow** **in** **disc** **and** **bar** **potentials** **(** _U_ **,** _II_ **-type)** **-**
**Panel H, I -**


It is well established that a bar potential produces non-rigid body
PVDs such as the parallelogram (Binney et al. 1991; Kruijssen
et al. 2015; Sormani et al. 2020). Although the bar size of the
Milky Way is reported to range from a few to several kpc (BlandHawthorn & Gerhard 2016; Portail et al. 2017) and even more inner bars detected in nearby spirals are of sizes _∼_ 200 pc (Erwin
2024), it would be worth exploring a much smaller bar in the
Galactic central bulge. So, we simulate the evolution of a cloud
in a disc and bar of the present size.


Panel H presents the result for an eccentric flow in a flat disc
potential with _q_ = 1 : 1 : 0 _._ 63 for the initial condition ( **r** ; **v** ) =
(1 _,_ 0 _,_ 0 _._ 3;0 _._ 3 _,_ 0 _._ 8 _,_ 0 _._ 3) . The ( _x,y_ ) projection forms a rosette orbit,
while the ( _x,z_ ) projection shows a _∞_ shape, similar to the result
for a larger disc of the CMZ (Kruijssen et al. 2015). The period
of vertical oscillation is about equal to _q_ _z_ = 0 _._ 63 times that of



horizontal orbital motion, which is typical of motion in a flat disc.
Panel I shows the result of a cloud orbiting in a triaxial bar potential ( _q_ = 1 : 0 _._ 85 : 0 _._ 63 ) for the initial condition
(1 _,_ 0 _,_ 0 _._ 3; _−_ 0 _._ 3 _,_ 0 _._ 8 _,_ 0 _._ 3) . The LVD behaviors are similar to that
in the spherical potential (panel F), and a part of LVD may explain
the LVD of G0.02.


**4** **Discussion**


4.1 Summary on the simulated results

The projected shape in the sky and the global elliptical LVD
of G0.02 are generally explained by the eccentric orbit model
in the gravitational potential due to an extended mass distribution. However, the _O_ -type LV feature is better reproduced by the
expanding-ring model, and the high-velocity LV wing is explained
by the SN-induced local expansion model. So, we cannot rule out
these models at this time.

**6** _Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0


**Fig. 4.** Tidal disruption of a cloud of mass _∼_ 10 [5] _M_ _⊙•_ [and] [radius] _[∼]_ [1] _[.]_ [6] [pc]
orbiting in the central bulge. Blue and black dots in the left panel represent
projections on ( _x, y_ ) and ( _x, z_ ) planes, respectively, at every 0.1 orbital
rotation, and the right panel shows LVD ( _x, v_ _y_ ) . Molecular clouds can
hardly survive in the central bulge. Alt text: Tidal disruption of a cloud.



4.2 The Line profile


The large velocity width (figure 3 A-d) is a key issue in explaining
the origin of the HVCC (Oka et al. 1999; Oka et al. 2008; Oka et
al. 2022), and appears to be ubiquitous in the CMZ (Ginsburg et
al. 2024). In the right-hand panels of figure 3 we show the simulated line profiles in the tangential direction of the orbit. The large
velocity width is reproduced by the shear of the tangential motion
of the elements rotating at high speed in the gravitational potential.
However, the high-velocity LV wing seems better explained by the
SN expansion model but it predicts a more symmetric profile and
requires large-energy injection. Another characteristic of G0.02
is the lopsided line profile shown in figure A-d. The simulations
show that it is a typical profile for the receding side of a rotating
disk, exhibiting a sharp cutoff at maximum velocity and an outskirt
toward decreasing velocity.


4.3 Origin of G0.02 as a galactic arm


**4.3.1** **Tidal disruption of a cloud**


As simulated, if G0.02 is elongated along the orbit, making it part
of a ring or arm, its length is _∼_ 16 pc. The density of the molecular
gas is then estimated to be _n_ H 2 _∼_ 2 _×_ 10 [4] H 2 cm _[−]_ [3] for a total mass
of _∼_ 10 [5] _M_ _⊙•_ [, much lower than the value of assuming the presence]
of a spherical cloud.


The concern if it were a cloud would be the tide because of

the bulge mass. For a cloud with mass _m_ c of radius _r_ to survive
from tidal disruption, it must be smaller than the Roche radius,
_r_ _[<]_ _∼_ ( _m_ c _/M_ B ) [1] _[/]_ [3] _R_ _∼_ 1 _._ 6 pc, where _M_ B _∼_ 2 _._ 5 _×_ 10 [7] _M_ _⊙•_ is the
mass of the bulge inside the orbit _R ∼_ 10 pc and _m_ c _∼_ 10 [5] _M_ _⊙•_ is
the mass of the cloud. Figure 4 shows an evolution of a cloud represented by test particles distributed around a massive body having
the Plummer potential whose center orbits in the same Galactic potential as in figure 3A. The radius of the local potential is _r_ c _∼_ 1 _._ 6
pc and the mass _m_ c _∼_ 10 [5] _M_ _⊙•_ . The cloud is strongly stretched
to make a spiral shape and loses its identity within one orbital rotation. Since such a compact cloud can easily be disrupted, it is
generally difficult for any molecular cloud to survive disruption in
the central 10 pc. Therefore, it is more natural to consider that
G0.02 is a part of the rotating disc as an arm or a wave orbiting
around the potential of the central bulge.



**Fig. 5.** Schematic view of G0.02 and the circum-nuclear gas structures.
Top: edge-on view on the sky; bottom: face-on view. Alt text: Illustration of
eccentric orbit in the GC simulating G0.02.


**4.3.2** **Circum-nuclear arms**

We suggest that G0.02 is an arm that appeared on the circumnuclear gas disc due to the density wave and/or a galactic shock wave,
which makes up part of a 10-pc radius tilted ring. The projection
of this ring in the sky forms an ellipse with the major axis at a tilt
angle of [ˆ] _i ∼_ 16 _[◦]_ from the Galactic plane ( _PA ∼_ 74 _[◦]_ ). This orientation is similar to that of Arm V that has a radius _∼_ 8 –9 pc (Sofue
et al. 2025) and [ˆ] _i ∼_ 14 _[◦]_ in the same sense. This coincidence of [ˆ] _i_
suggests that G0.02 and Arm V comprise the same family of GC
arms. We point out that the main axes of these features also align
with the main axis of the CND (Etxaluze et al. 2011). In Figure 5
we illustrate a schematic view of the 3D structure in the central 10

pc, where the CND (Arm VI) of the radius _∼_ 2 _._ 3 pc and the Mini
spirals (Arm VII) of _∼_ 1 _._ 4 pc are drawn for comparison.


4.4 Implication for the nuclear kinematics

G0.02 would provide a new aspect to the study of the circumnuclear region, since it is such a case that a resolved molecular cloud
orbits in the deep gravitational potential of the nuclear bulge. This
enables us to explore the 3D potential and therefore the distribution
of mass in the inner _∼_ 10 pc region by analyzing the cloud’s behavior in the ( _l,b,v_ LSR ) space. This study would be a step toward
3D orbital reconstruction of the gas near Sgr A*, consistent with
broader efforts (Henshaw et al. 2023; Kruijssen et al. 2015). For
example, the approximate mass within _R_ = 10 pc can be estimated
using _V_ rot _∼_ 104 km s _[−]_ [1] by Eq. 1 as _M_ = _RV_ rot [2] _[/G]_ _[∼]_ [2] _[.]_ [5] _[×]_ [10] [7] _[M]_ _⊙•_
for a spherical mass distribution. The 3D visualization of the eccentric gas flow would also help modeling the feeding mechanism
to the nucleus.


4.5 Magnetic field aligned along the central arms

Far infrared polarimetry has shown that the circumnuclear magnetic fields align with the orbital structure in the GC (Karoly et
al. 2025; Yang et al. 2025). The magnetic field in G0.02 also
aligns exactly with these fields at _PA_ _∼_ 70 _[◦]_ . Furthermore, the
field within _∼_ 2 pc around G0.02 traces its tightly curved edge
(Akshaya & Hoang 2024). This magnetic orientation can be nat

_Publications of the Astronomical Society of Japan_ (2024), Vol. 00, No. 0 **7**



urally understood as a miniature of the galactic magnetic arms,
which arise from stretched field lines along the gaseous stream
and are compressed in the arm.


**5** **Conclusion**


Analyzing the CS ( _J_ = 2 _−_ 1 ) line data cube obtained by ACES,
we investigated the detailed kinematical structure of the molecular
cloud G0.02. We showed that G0.02 is an edge-on view of a part of
a molecular ring of radius _∼_ 10 pc rotating around Sgr A _[∗]_ in _V_ rot _∼_
100 km s _[−]_ [1] superposed by noncircular motion of _∼_ 100 km s _[−]_ [1] .
The observed properties are consistent with eccentric motion in a
gravitational potential of an extended mass distribution. Although
this is the most natural explanation, expanding ring models can
also reproduce LV morphology, particularly _O_ -type LVD. Because
G0.02 is located near the tangential direction of this ellipse, the
width of the molecular line increases to several tens km s _[−]_ [1] due

to shear in orbital velocity. G+0.02-0.02+100 is thus a kinematic
tracer of the inner potential, a rare case of a dense gas following
an eccentric orbit in the nuclear gravitational field.


**Acknowledgments**


This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00172:
/ ALMA is a partnership of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile. / The Joint ALMA
Observatory is operated by ESO, AUI/NRAO and NAOJ. / The data analysis in
this paper was partially performed at the Astronomical Data Center of the National
Astronomical Observatories of Japan.
CB gratefully acknowledges funding from National Science Foundation under
Award Nos. 2108938, 2206510, and CAREER 2145689, as well as from the National
Aeronautics and Space Administration through the Astrophysics Data Analysis Program
under Award “3-D MC: Mapping Circumnuclear Molecular Clouds from X-ray to
Radio,” Grant No. 80NSSC22K1125. / AG acknowledges support from the NSF
under AAG 2206511 and CAREER 2142300. / COOL Research DAO (Chevance et
al. 2025) is a Decentralised Autonomous Organisation supporting research in astrophysics aimed at uncovering our cosmic origins. / KK acknowledges the support by
JSPS KAKENHI Grant Numbers JP23K20035 and JP24H00004. / KMD acknowledges support from the European Research Council (ERC) Advanced Grant MOPPEX
833460.vii. / L.C., V.M.R. and I.J.-S. acknowledge support from the grant PID2022136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State
Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. /
V.M.R. also acknowledges support from the grant RYC2020-029387-I funded by
MICIU/AEI/10.13039/501100011033 and by "ESF, Investing in your future", from the
Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología
(CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC);
and from the grant CNS2023-144464 funded by MICIU/AEI/10.13039/501100011033
and by “European Union NextGenerationEU/PRTR”. / I.J.-S. acknowledges support
from ERC grant OPENS, GA No. 101125858, funded by the European Union. /
P.G. is sponsored by the Chinese Academy of Sciences (CAS), through a grant to the
CAS South America Center for Astronomy (CASSACA). / R.S.K. thanks the 2024/25
Class of Radcliffe Fellows for highly interesting and stimulating discussions, financial support from the European Research Council via ERC Synergy Grant “ECOGAL”
(project ID 855130), the German Excellence Strategy via the Heidelberg Cluster of
Excellence (EXC 2181 - 390900948) “STRUCTURES”, the German Ministry for
Economic Affairs and Climate Action in project “MAINN” (funding ID 50OO2206),
Ministry of Science, Research and the Arts of the State of Baden-Württemberg through
bwHPC and the German Science Foundation through grants INST 35/1134-1 FUGG
and 35/1597-1 FUGG, and also for data storage at SDS@hd funded through grants
INST 35/1314-1 FUGG and INST 35/1503-1 FUGG. / D. R-V acknowledges the
financial support of DIDULS/ULS, through the project PAAI 2023. / J.W. gratefully acknowledges funding from National Science Foundation under Award Nos.
2108938 and 2206510. / A.S.-M. acknowledges support from the RyC2021-032892I grant funded by MCIN/AEI/10.13039/501100011033 and by the European Union
‘Next GenerationEU’/PRTR, as well as the program Unidad de Excelencia María de
Maeztu CEX2020-001058-M, and support from the PID2023-146675NB-I00 (MCIAEI-FEDER, UE). / Q.D.W. acknowledges support from NASA via grant GO3-24120X.
/ J.K. is supported by the Royal Society under grant number RF _\_ ERE _\_ 231132, as part
of project URF _\_ R1 _\_ 211322. / MCS acknowledges financial support from the European
Research Council under the ERC Starting Grant “GalFlow” (grant 101116226) and from
Fondazione Cariplo under the grant ERC attrattività n. 2023-3014. / KMD acknowledges support from the European Research Council (ERC) Advanced Grant MOPPEX
833460.vii.

The authors thank the anonymous referee for the valuable comments.



**Data availability**


The interferometer data were taken from the internal release version of the 12m+7m+TP
(Total Power)-mode data from the ALMA cycle 8 Large Program "ALMA Central
Molecular Zone Exploration Survey" (ACES, 2021.1.00172.L).


**Conflict of interest**


The authors declare that there is no conflict of interest.


**References**


Akshaya, M. S. & Hoang, T. 2024, MNRAS, 531, 5012.
doi:10.1093/mnras/stae1464

Binney J., Gerhard O. E., Stark A. A., Bally J., Uchida K. I., 1991, MNRAS,
252, 210

Bland-Hawthorn, J. & Gerhard, O. 2016, ARA&A, 54, 529.

doi:10.1146/annurev-astro-081915-023441

Chevance M., Kruijssen J. M. D., Longmore S. N., 2025,
doi:10.48550/arXiv.2501.13160

Etxaluze, M., Smith, H. A., Tolls, V., et al. 2011, AJ, The Galactic Center in

the Far-infrared, 142, 4, 134. doi:10.1088/0004-6256/142/4/134
Dame, T. M., Hartmann, D., & Thaddeus, P. 2001, ApJ, 547, 792.

doi:10.1086/318388

Erwin, P. 2024, MNRAS, 528, 3613. doi:10.1093/mnras/stad3944
Ginsburg, A., Bally, J., Barnes, A. T., et al. 2024, ApJL, 968, L11.

doi:10.3847/2041-8213/ad47fa

Gravity Collaboration, Abuter, R., Amorim, A., et al. 2019, A&A, 625, L10.
doi:10.1051/0004-6361/201935656

Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, Protostars and
Planets VII, 534, 83. doi:10.48550/arXiv.2203.11223
Hsieh, P.-Y., Koch, P. M., Kim, W.-T., et al. 2021, ApJ, 913, 94.
doi:10.3847/1538-4357/abf4cd

Iwata, Y., Oka, T., Takekawa, S., et al. 2023, ApJ, 950, 25. doi:10.3847/15384357/acc9b0

Kaifu, N., Kato, T., & Iguchi, T. 1972, Nature Physical Science, 238, 105
Kaneko, M., Oka, T., Yokozuka, H., et al. 2023, ApJ, 942, 46.
doi:10.3847/1538-4357/aca66a

Karoly, J., Ward-Thompson, D., Pattle, K., et al. 2025, ApJL, 982, 1, L22.
doi:10.3847/2041-8213/adbc67

Kruijssen, J. M. D., Dale, J. E., & Longmore, S. N. 2015, MNRAS, 447,
1059. doi:10.1093/mnras/stu2526

Oka, T., Hasegawa, T., White, G. J., et al. 2008, PASJ, 60, 429.
doi:10.1093/pasj/60.3.429
Oka, T., Uruno, A., Enokiya, R., et al. 2022, ApJS, 261, 13.
doi:10.3847/1538-4365/ac6bfc

Oka, T., White, G. J., Hasegawa, T., et al. 1999, ApJ, 515, 249.
doi:10.1086/307029

Portail, M., Gerhard, O., Wegg, C., et al. 2017, MNRAS, 465, 1621.
doi:10.1093/mnras/stw2819

Scoville, N. Z. 1972, ApJL, 175, L127
Sofue, Y. 2013, PASJ, 65, 118. doi:10.1093/pasj/65.6.118
Sofue, Y. 2017, MNRAS, 470, 1982

Sofue, Y. 2020, MNRAS, 498, 1335. doi:10.1093/mnras/staa2389
Sofue, Y. et al. 2025, PASJ in press, arXiv:2504.03331 (Paper I)
Sormani, M. C., Tress, R. G., Glover, S. C. O., et al. 2020, MNRAS, 497,

5024. doi:10.1093/mnras/staa1999

Takekawa, S., Oka, T., & Tanaka, K. 2017, ApJL, 834, 121.
doi:10.3847/1538-4357/834/2/121

Tsuboi, M., Kitamura, Y., Uehara, K., et al. 2018, PASJ, 70, 85.
doi:10.1093/pasj/psy080
Tsuboi, M., Miyazaki, A., & Okumura, S. K. 2009, PASJ, 61, 29.
doi:10.1093/pasj/61.1.29
Yang, M.-Z., Lai, S.-P., Karoly, J., et al. 2025, arXiv:2503.05198.
doi:10.48550/arXiv.2503.05198


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[0]",
  "value": "(l, b) ~ (0.02 deg, -0.02 deg)",
  "failed_quote": "The high-velocity compact cloud (HVCC; hereafter G+0.02-0.02+100, or G0.02) located at (l, b, v_LSR ) \\simeq (0^\\circ .02, -0^\\circ .02, +100 km s^{-1} ) at a projected distance of 10 pc from Sgr A^* is the most typical example of such clouds"
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "R_0 = 8.2 kpc",
  "failed_quote": "The high-velocity compact cloud (HVCC; hereafter G+0.02-0.02+100, or G0.02) located at (l, b, v_LSR ) \\simeq (0^\\circ .02, -0^\\circ .02, +100 km s^{-1} ) at a projected distance of 10 pc from Sgr A^* is the most typical example of such clouds"
 },
 {
  "path": "science.targets[0].distance_source.evidence[0]",
  "value": "Gravity Collaboration et al. 2019",
  "failed_quote": "The high-velocity compact cloud (HVCC; hereafter G+0.02-0.02+100, or G0.02) located at (l, b, v_LSR ) \\simeq (0^\\circ .02, -0^\\circ .02, +100 km s^{-1} ) at a projected distance of 10 pc from Sgr A^* is the most typical example of such clouds"
 },
 {
  "path": "science.targets[1].coordinates.evidence[0]",
  "value": "-0.25 deg <= l <= +0.15 deg, -0.1 deg <= b <= +0.0 deg",
  "failed_quote": "In the present work, we cut out a region at -0^\\circ .25 \\le l \\le +0^\\circ .15 and -0^\\circ .1 \\le b \\le +0^\\circ for a detailed analysis of the circum-nuclear region centered on Sgr A^* ."
 },
 {
  "path": "science.targets[1].redshift_or_distance.evidence[0]",
  "value": "R_0 = 8.2 kpc",
  "failed_quote": "In the present work, we cut out a region at -0^\\circ .25 \\le l \\le +0^\\circ .15 and -0^\\circ .1 \\le b \\le +0^\\circ for a detailed analysis of the circum-nuclear region centered on Sgr A^* ."
 },
 {
  "path": "science.targets[1].distance_source.evidence[0]",
  "value": "Gravity Collaboration et al. 2019",
  "failed_quote": "In the present work, we cut out a region at -0^\\circ .25 \\le l \\le +0^\\circ .15 and -0^\\circ .1 \\le b \\le +0^\\circ for a detailed analysis of the circum-nuclear region centered on Sgr A^* ."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Molecular mass of G0.02 M_mol ~ 10^5 M_sun from CO-line luminosity",
  "failed_quote": "Oka et al. (1999) estimate the molecular mass to be M_mol ~ 10^5 M_\\odot from the CO-line luminosity."
 },
 {
  "path": "processing.imaging.cell_size.evidence[0]",
  "value": "0''.5 x 0''.5 spatial, 0.15 km s^-1 velocity grid",
  "failed_quote": "The used CS (J = 2 - 1 ) cube covers the CMZ at -0^\\circ .6 <~ l <~ +0^\\circ .9 and -0^\\circ .3 <~ b <~ +0^\\circ .1 with spatial and velocity grids of ( 0''.5 \\times 0''.5 \\times 0.15 km s^{-1} )."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Extract region around Sgr A* from ACES CS (J=2-1) cube, integrate from -220 to +220 km s^-1 (and v_LSR >= 75 km s^-1 for G0.02) to create moment 0 maps, and take maximum intensity along latitude at each Galactic longitude to construct LVDs (also subtracting horizontally extended components for G0.02).",
  "failed_quote": "In the present work, we cut out a region at -0^\\circ .25 \\le l \\le +0^\\circ .15 and -0^\\circ .1 \\le b \\le +0^\\circ for a detailed analysis of the circum-nuclear region centered on Sgr A^* ."
 },
 {
  "path": "analysis_steps[0].method.evidence[2]",
  "value": "Extract region around Sgr A* from ACES CS (J=2-1) cube, integrate from -220 to +220 km s^-1 (and v_LSR >= 75 km s^-1 for G0.02) to create moment 0 maps, and take maximum intensity along latitude at each Galactic longitude to construct LVDs (also subtracting horizontally extended components for G0.02).",
  "failed_quote": "In panel B of figure 1, we show a longitude-velocity diagram (LVD) of the maximum intensity along latitude at each Galactic longitude in the CS (J = 2 - 1 ) line between l = -0^\\circ .25 and +0^\\circ .15 ."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "Cutout region: -0.25 deg <= l <= +0.15 deg, -0.1 deg <= b <= +0.0 deg",
  "failed_quote": "In the present work, we cut out a region at -0^\\circ .25 \\le l \\le +0^\\circ .15 and -0^\\circ .1 \\le b \\le +0^\\circ for a detailed analysis of the circum-nuclear region centered on Sgr A^* ."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Read positions of the LV ridges from the mini-CMZ LVD, fit them with a tilted ellipse equation v_LSR = A x +/- B sqrt(1 - (Delta x / a)^2), and measure sky-plane ellipse parameters and enclosed mass M = R V_rot^2 / G.",
  "failed_quote": "In figure 3 (panel A) we plot the positions of the LV ridges read from panel C of figure 1, which can be fitted by a tilted ellipse expressed by v_LSR = A x \\pm B \\sqrt{1 - (\\Delta x/a)^2},"
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Read positions of the LV ridges from the mini-CMZ LVD, fit them with a tilted ellipse equation v_LSR = A x +/- B sqrt(1 - (Delta x / a)^2), and measure sky-plane ellipse parameters and enclosed mass M = R V_rot^2 / G.",
  "failed_quote": "For example, the approximate mass within R = 10 pc can be estimated using V_rot ~ 104 km s^{-1} by Eq. 1 as M = RV_rot^2 /G ~ 2.5 \\times 10^7 M_\\odot for a spherical mass distribution."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "A = 1600 km s^-1 per degree (104 km s^-1), B = 100 km s^-1, a = 0.065 deg (9.3 pc), Delta x = l + 0.046 deg",
  "failed_quote": "where A = dv/dl = 1600 km s^{-1} per degree, B = 100 km s^{-1}, a = 0^\\circ .065 (9.3 pc), and \\Delta x = l + 0^\\circ .046 with the center offset by 0^\\circ .01 = 1.4 pc to the east from Sgr A^* ."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[1]",
  "value": "Spherical mass distribution for enclosed mass estimate; A represents rotation velocity V_rot ~ 104 km s^-1 at R ~ 10 pc",
  "failed_quote": "M = RV_rot^2 /G ~ 2.5 \\times 10^7 M_\\odot for a spherical mass distribution."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "Analytical tilted ellipse fit to read LV ridge positions",
  "failed_quote": "In figure 3 (panel A) we plot the positions of the LV ridges read from panel C of figure 1, which can be fitted by a tilted ellipse expressed by v_LSR = A x \\pm B \\sqrt{1 - (\\Delta x/a)^2},"
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Measure cloud radius r ~ sqrt(sigma_l sigma_b) on moment 0 map and FWHM 2*sigma_v of the peak intensity component; calculate virial mass M_vir ~ 3 r sigma_v^2 / G, gas density n_H2 for an elongated arm, and Roche radius r <~ (m_c / M_B)^(1/3) R.",
  "failed_quote": "The radius of the G0.02 cloud is measured as r ~ \\sqrt{\\sigma_l \\sigma_b} ~ 0.7 pc on the moment 0 map (Figure 2). The full width at half maximum of the peak intensity component is measured to be 2\\sigma_v ~ 56 km s^{-1} ."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Measure cloud radius r ~ sqrt(sigma_l sigma_b) on moment 0 map and FWHM 2*sigma_v of the peak intensity component; calculate virial mass M_vir ~ 3 r sigma_v^2 / G, gas density n_H2 for an elongated arm, and Roche radius r <~ (m_c / M_B)^(1/3) R.",
  "failed_quote": "The corresponding Virial mass is then calculated as M_vir ~ 3r\\sigma_v^2 /G ~ 4 \\times 10^5 M_\\odot ."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "r ~ 0.7 pc, 2*sigma_v ~ 56 km s^-1, elongated length ~ 16 pc",
  "failed_quote": "The radius of the G0.02 cloud is measured as r ~ \\sqrt{\\sigma_l \\sigma_b} ~ 0.7 pc on the moment 0 map (Figure 2). The full width at half maximum of the peak intensity component is measured to be 2\\sigma_v ~ 56 km s^{-1} ."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Molecular mass m_c ~ 10^5 M_sun (from Oka et al. 1999); bulge mass M_B ~ 2.5 x 10^7 M_sun inside R ~ 10 pc",
  "failed_quote": "Oka et al. (1999) estimate the molecular mass to be M_mol ~ 10^5 M_\\odot from the CO-line luminosity."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[1]",
  "value": "Molecular mass m_c ~ 10^5 M_sun (from Oka et al. 1999); bulge mass M_B ~ 2.5 x 10^7 M_sun inside R ~ 10 pc",
  "failed_quote": "where M_B ~ 2.5 \\times 10^7 M_\\odot is the mass of the bulge inside the orbit R ~ 10 pc and m_c ~ 10^5 M_\\odot is the mass of the cloud."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Integrate orbits of an ensemble of N test particles in a logarithmic potential Phi = 1/2 v_0^2 ln(sum (x_i / q_i)^2) for spherical, flat disc, and triaxial bar axial ratios, plus SN local expansion and expanding ring perturbations, and compare projections, PVDs, and line profiles with G0.02.",
  "failed_quote": "We adopt a potential expressed by \\Phi = 1/2 v_0^2 \\ln [ \\Sigma (x_i /q_i )^2 ],"
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "LV ellipse velocity gradient A (dv/dl) = 1600 km s^-1 deg^-1",
  "failed_quote": "where A = dv/dl = 1600 km s^{-1} per degree, B = 100 km s^{-1}, a = 0^\\circ .065 (9.3 pc), and \\Delta x = l + 0^\\circ .046 with the center offset by 0^\\circ .01 = 1.4 pc to the east from Sgr A^* ."
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "LV ellipse semi-major axis a (ring radius R) = 9.3 pc",
  "failed_quote": "where A = dv/dl = 1600 km s^{-1} per degree, B = 100 km s^{-1}, a = 0^\\circ .065 (9.3 pc), and \\Delta x = l + 0^\\circ .046 with the center offset by 0^\\circ .01 = 1.4 pc to the east from Sgr A^* ."
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "G0.02 cloud radius r = 0.7 pc",
  "failed_quote": "The radius of the G0.02 cloud is measured as r ~ \\sqrt{\\sigma_l \\sigma_b} ~ 0.7 pc on the moment 0 map (Figure 2)."
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "G0.02 virial mass M_vir = 4e5 M_sun",
  "failed_quote": "The corresponding Virial mass is then calculated as M_vir ~ 3r\\sigma_v^2 /G ~ 4 \\times 10^5 M_\\odot ."
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Sky-projected 10-pc ring position angle (PA) = 74 deg",
  "failed_quote": "The moment 0 map in figure 1 suggests that G0.02 is part of an ellipse elongated in the direction of PA ~ 74^\\circ with the major and minor radii a ~ 0^\\circ .07(~ 10 pc) and b ~ 0^\\circ .01(~ 1.4 pc), respectively, or the axial ratio of b/a ~ 0.14 ."
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Sky-projected 10-pc ring axial ratio (b/a) = 0.14 dimensionless",
  "failed_quote": "The moment 0 map in figure 1 suggests that G0.02 is part of an ellipse elongated in the direction of PA ~ 74^\\circ with the major and minor radii a ~ 0^\\circ .07(~ 10 pc) and b ~ 0^\\circ .01(~ 1.4 pc), respectively, or the axial ratio of b/a ~ 0.14 ."
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Roche radius for G0.02 at R ~ 10 pc = 1.6 pc",
  "failed_quote": "For a cloud with mass m_c of radius r to survive from tidal disruption, it must be smaller than the Roche radius, r <~ (m_c /M_B )^{1/3} R ~ 1.6 pc, where M_B ~ 2.5 \\times 10^7 M_\\odot is the mass of the bulge inside the orbit R ~ 10 pc"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Enclosed mass within R = 10 pc = 2.5e7 M_sun",
  "failed_quote": "For example, the approximate mass within R = 10 pc can be estimated using V_rot ~ 104 km s^{-1} by Eq. 1 as M = RV_rot^2 /G ~ 2.5 \\times 10^7 M_\\odot for a spherical mass distribution."
 },
 {
  "path": "findings_qualitative[0].evidence[1]",
  "value": "G0.02 is part of an elliptical structure in the longitude-velocity diagram (the mini-CMZ) corresponding to an inclined 10-pc ring rotating at ~104 km s^-1 with ~100 km s^-1 noncircular motion.",
  "failed_quote": "We showed that G0.02 is an edge-on view of a part of a molecular ring of radius ~ 10 pc rotating around Sgr A^* in V_rot ~ 100 km s^{-1} superposed by noncircular motion of ~ 100 km s^{-1} ."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "Molecular clouds can hardly survive tidal disruption in the central 10 pc, so G0.02 is more naturally understood as an arm or wave in a tilted 10-pc circumnuclear ring.",
  "failed_quote": "The corresponding Virial mass is then calculated as M_vir ~ 3r\\sigma_v^2 /G ~ 4 \\times 10^5 M_\\odot . Adopting a wider extent, Oka et al. (1999) obtain an even higher Virial mass of ~ 3 \\times 10^6 to 10^7 M_\\odot . Therefore, the cloud is not gravitationally bound."
 }
]
```
