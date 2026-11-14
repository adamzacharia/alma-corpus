# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...976...29H\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
D RAFT VERSION S EPTEMBER 24, 2024
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**ALMASOP. The Localized and Chemically rich Features near the Bases of the Protostellar Jet in HOPS 87**


S HIH -Y [ING](http://orcid.org/0000-0002-1369-1563) H SU, [1] C HIN -F [EI](http://orcid.org/0000-0002-3024-5864) L EE, [1] S HENG -Y [UAN](http://orcid.org/0000-0012-3245-1234) L IU, [1] D OUG J [OHNSTONE](http://orcid.org/0000-0002-6773-459X), [2, 3] T IE [L](http://orcid.org/0000-0002-5286-2564) IU, [4] S ATOKO T [AKAHASHI](http://orcid.org/0000-0002-7287-4343), [5, 6]

L EONARDO [B](http://orcid.org/0000-0002-9574-8454) RONFMAN, [7] H UEI -R U V [IVIEN](http://orcid.org/0000-0002-9774-1846) C HEN, [8] S OMNATH [D](http://orcid.org/0000-0002-2338-4583) UTTA, [1] D AVID [J. E](http://orcid.org/0000-0002-5881-3229) DEN, [9] N EAL J. E [VANS](http://orcid.org/0000-0001-5175-1777) II, [10]

N AOMI H IRANO, [1] M IKA J [UVELA](http://orcid.org/0000-0002-5809-4834), [11] Y I -J [EHNG](http://orcid.org/0000-0002-4336-0730) K UAN, [12, 1] W OOJIN [K](http://orcid.org/0000-0003-4022-4132) WON, [13, 14] C HANG W ON L EE, [15, 16]

J EONG -E [UN](http://orcid.org/0000-0003-3119-2087) L EE, [17] S [HANGHUO](http://orcid.org/0000-0003-1275-5251) L I, [18] C HUN -F [AN](http://orcid.org/0000-0002-1624-6545) L IU, [1] X [UNCHUAN](http://orcid.org/0000-0001-8315-4248) L IU, [19] Q IUYI [L](http://orcid.org/0000-0003-4506-3171) UO, [20, 21, 22] S HENG [-L](http://orcid.org/0000-0003-2302-0613) I Q IN, [23]

D IPEN [S](http://orcid.org/0000-0002-4393-3463) AHU, [24, 25] P ATRICIO S [ANHUEZA](http://orcid.org/0000-0002-7125-7685), [5, 6] H SIEN S [HANG](http://orcid.org/0000-0001-8385-9838) ( `尚賢` ), [26] K ENICHI T [ATEMATSU](http://orcid.org/0000-0002-8149-8546), [27, 6] AND Y AO -L [UN](http://orcid.org/0000-0001-8227-2816) Y ANG 28


1 _Institute of Astronomy and Astrophysics, Academia Sinica, No.1, Sec._ _4, Roosevelt Rd, Taipei 106216, Taiwan (R.O.C.)_
2 _NRC Herzberg Astronomy and Astrophysics, 5071 West Saanich Rd, Victoria, BC, V9E 2E7, Canada_
3 _Department of Physics and Astronomy, University of Victoria, Victoria, BC, V8P 5C2, Canada_
4 _Key Laboratory for Research in Galaxies and Cosmology, Shanghai Astronomical Observatory, Chinese Academy of Sciences, 80 Nandan Road, Shanghai_
_200030, People’s Republic of China_
5 _National Astronomical Observatory of Japan, National Institutes of Natural Sciences, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan_
6 _Department of Astronomical Science, The Graduate University for Advanced Studies, SOKENDAI, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan_
7 _Departamento de Astronom´ıa, Universidad de Chile, Casilla 36-D, Santiago, Chile_
8 _Department of Physics and Institute of Astronomy, National Tsing Hua University, Hsinchu, 30013, Taiwan_
9 _Armagh Observatory and Planetarium, College Hill, Armagh, BT61 9DB, UK_
10 _Department of Astronomy, The University of Texas at Austin, 2515 Speedway, Stop C1400, Austin, Texas 78712-1205, USA_
11 _Department of Physics, P.O.Box 64, FI-00014, University of Helsinki, Finland_
12 _Department of Earth Sciences, National Taiwan Normal University, Taipei, Taiwan (R.O.C.)_
13 _Department of Earth Science Education, Seoul National University, 1 Gwanak-ro, Gwanak-gu, Seoul 08826, Republic of Korea_
14 _SNU Astronomy Research Center, Seoul National University, 1 Gwanak-ro, Gwanak-gu, Seoul 08826, Republic of Korea_
15 _Korea Astronomy and Space Science Institute (KASI), 776 Daedeokdae-ro, Yuseong-gu, Daejeon 34055, Republic of Korea_
16 _University of Science and Technology, Korea (UST), 217 Gajeong-ro, Yuseong-gu, Daejeon 34113, Republic of Korea_
17 _Department of Physics and Astronomy, Seoul National University, 1 Gwanak-ro, Gwanak-gu, Seoul 08826, Korea_
18 _Max Planck Institute for Astronomy, K¨onigstuhl 17, D-69117 Heidelberg, Germany_
19 _Shanghai Astronomical Observatory, Chinese Academy of Sciences, Shanghai 200030, PR China_
20 _Shanghai Astronomical Observatory, Chinese Academy of Sciences, Shanghai 200030, People’s Republic of China_
21 _School of Astronomy and Space Sciences, University of Chinese Academy of Sciences, No._ _19A Yuquan Road, Beijing 100049, People’s Republic of China_
22 _Key Laboratory of Radio Astronomy and Technology, Chinese Academy of Sciences, A20 Datun Road, Chaoyang District, Beijing, 100101, P. R. China_
23 _Department of Astronomy, Yunnan University, and Key Laboratory of Astroparticle Physics of Yunnan Province, Kunming, 650091, People’s Republic of China_
24 _Physical Research laboratory, Navrangpura, Ahmedabad, Gujarat 380009, India_
25 _Academia Sinica Institute of Astronomy and Astrophysics, 11F of AS/NTU Astronomy-Mathematics Building, No.1, Sec._ _4, Roosevelt Rd, Taipei 106216,_
_Taiwan, R.O.C._
26 _Institute of Astronomy and Astrophysics, Academia Sinica, Taipei 106216, Taiwan_
27 _Nobeyama Radio Observatory, National Astronomical Observatory of Japan, National Institutes of Natural Sciences, 462-2 Nobeyama, Minamimaki,_
_Minamisaku, Nagano 384-1305, Japan_
28 _Star and Planet Formation Laboratory, RIKEN Cluster for Pioneering Research, Wako, Saitama 351-0198, Japan_


Submitted to ApJ


ABSTRACT


HOPS 87 is a Class 0 protostellar core known to harbor an extremely young bipolar outflow and a hot corino.
We report the discovery of localized, chemically rich regions near the bases of the two-lobe bipolar molecular
outflow in HOPS 87 containing molecules such as H 2 CO, [13] CS, H 2 S, OCS, and CH 3 OH, the simplest complex
organic molecule (COM). The locations and kinematics suggest that these localized features are due to jet

[seansyhsu@gmail.com](mailto: seansyhsu@gmail.com)


[cflee@asiaa.sinica.edu.tw](mailto: cflee@asiaa.sinica.edu.tw)

2 H SU ET AL .


driven shocks rather than being part of the hot corino region encasing the protostar. The COM compositions
of the molecular gas in these jet-localized regions are relatively simpler than those in the hot corino zone. We
speculate that this simplicity is due to either the liberation of ice with a less complex chemical history or the
effects of shock chemistry. Our study highlights the dynamic interplay between the protostellar bipolar outflow,
disk, inner core environment, and the surrounding medium, contributing to our understanding of molecular
complexity in solar-like young stellar objects.


_Keywords:_ astrochemistry — ISM: molecules — stars: formation and low-mass



1. INTRODUCTION


Interstellar complex organic molecules (COMs or iCOMs)
found within low-mass young stellar objects (YSOs) are
significant in astronomy due to their potential role in
prebiotic chemistry in protoplanetary systems. The presence
of warm gaseous COMs in YSOs is often explained by the
“thermal desorption” paradigm (e.g., Garrod et al. 2007;
Herbst & van Dishoeck 2009). Initially, during the starless
core phase, with a temperature of _∼_ 10 K, CO molecules
are primarily depleted by freeze-out and trapped in the icy
mantles coating dust grains. Through grain-surface reactions,
such as hydrogenation, COMs gradually form within these
CO-rich ices. As the core evolves into the protostellar stage,
the central protostar heats up the surrounding envelope,
causing the desorption of these previously trapped COMs.
In the innermost envelope, where temperatures exceed the
ice sublimation threshold of _∼_ 100 K, the majority of the
trapped COMs are released into the gas of the newly
formed hot corino (Ceccarelli 2004). Hot corinos are
commonly observed in protostellar cores, provided that their
innermost envelopes attain temperatures of at least 100 K
and guarantee ice sublimation (Ceccarelli 2004; Hsu et al.
2023). Furthermore, protostellar outbursts may extend the
boundaries of thermal desorption due to the rapid increase of
the temperature in the disk (Lee et al. 2019b).
In addition to the heating from the central protostar,
shocks also play a role in releasing COMs in the gas
phase. For example, COM factories have been discovered
in the protostellar outflow L1157, particularly in the B1
shock region (e.g., Arce et al. 2008; Mendoza et al. 2014;
Codella et al. 2015; Lefloch et al. 2017). Arce et al. (2008)
suggested that COMs are primarily formed on the grain
surfaces and then expelled from icy mantles by shocks. For

[BHB2007] 11, a protobinary protostellar system, Vastel
et al. (2022) suggested that the presence of hot methanol is
due to shocks possibly generated by streamers towards the
cores, impacting the quiescent gas within the circumbinary
envelope, circumbinary disk, or the two circumstellar disks.
Similarly, in the nearly edge-on protostellar disk around HH212 (e.g., Codella et al. 2016; Lee et al. 2017, 2019a),
some COMs near the disk edge may be released by the heat
generated by “accretion shocks” (Lee et al. 2017; Tabone
et al. 2017), while others away from the disk edge could be



released by the heat obtained from the radiation of the central
protostar and/or disk-wind interaction (Lee et al. 2022). A
similar accretion shock mechanism was proposed by Oya &
Yamamoto (2020) based on the steep rise in H 2 CS rotation
temperature to 300 K or higher at a radius of 50 au from
the protostar in IRAS 16293–2422 A. This localized heating
mechanism received further support from the detection of a
elevated ring-like warm structure in the Class 0 protostellar
core B335 (Okoda et al. 2022).
These findings underscore the potential and significance
of shocks in investigating COMs in YSOs, as they are
potentially capable of releasing COMs from the ice phase to
the gas phase. Furthermore, chemically rich shocked regions
may exhibit distinct chemical characteristics compared to hot
corinos where the ice is more gradually sublimated. For
instance, certain COMs such as CH 3 CHO are observed to
be more prevalent in the L1175-B1 shocked region than in
hot corinos, with abundance ratios ranging from 2 to 10,
depending on the species (Lefloch et al. 2017). Additionally,
some studies suggest that gas-phase reactions are enhanced
following shocks (Codella et al. 2015). The limited
identification of chemically rich shocked regions leads to
a desire for further discoveries and in-depth investigations,
particularly targeting those YSOs hosting abundant COMs.
HOPS 87 (Furlan et al. 2016), also known as OMC-3 MMS
6 (Chini et al. 1997) and G208.68-19.20N1 (Dutta et al.
2020), is a Class 0 protostellar core in the Orion Molecular
Cloud 3 (OMC-3) region with a bolometric luminosity
_L_ bol of 38 _±_ 13 _L_ _⊙_, a bolometric temperature _T_ bol of
36 _._ 7 _±_ 14 _._ 5 K, and local standard of rest velocity _v_ LSR of
11 _._ 4 km s _[−]_ [1] (Dutta et al. 2020). This source is one of the
11 protostellar cores with a detected hot corino reported by
the “ALMA Survey of Orion PGCCs (ALMASOP)” project
(Hsu et al. 2020, 2022), where the ALMA is Atacama
Large Millimeter/submillimeter Array and the PGCCs are
Planck Galactic Cold Clumps (Planck et al. 2016). It is
the third-most luminous protostellar core in the catalogued
sample. There are several COM species detected toward this
source, including CH 3 OH, CH 2 DOH, [13] CH 3 OH, CH 3 CHO,
HCOOCH 3, and NH 2 CHO.

Takahashi & Ho (2012) reported an extremely young
outflow associated with HOPS 87 (MMS6) with an estimated
outflow dynamic range of _≤_ 100 yr. The authors reported an

HOPS 87 3



inclination of 45 _[◦]_ for the bipolar outflow by comparing their
position-velocity (PV) diagram with a kinetic outflow model
(Lee et al. 2000). Takahashi et al. (2019) later estimated
the inclination angle to be 60 _[◦]_ (roughly egde-on) based on
comparisons between the observed toroidal magnetic field
and numerical calculations. Takahashi & Ho (2012) reported
a detection of HCN ( _J_ = 4 _−_ 3), tracing an increase
in line width at the end of the molecular outflow, which
indicates a clear bow-shock type velocity structure. The jets
in HOPS 87 were recently studied by Dutta et al. (2024),
and the projected velocity of the jets was reported to be
43 _±_ 6 km s _[−]_ [1] . Assuming that the majority of low-velocity
components in the bipolar outflow are wind components, the
authors estimated an inclination angle of the bipolar outflow
to be 65 _[◦]_ .

In this paper, we report newly discovered, localized,
chemically rich regions associated with jet-driven shocks
near the two bases of the bipolar outflow in the protostellar
core HOPS 87. In §2, we introduce the two observation
programs used for this study. In §3.1, we show the
(integrated) intensity maps of selected molecular transitions,
which reveal the two-lobe, localized, and chemically rich
regions near the bases of the bipolar molecular outflow.
Moreover, in §3.2, we investigate the kinematics in the
localized regions. In §4 and §5, we discuss our findings and
make summarize our conclusions, respectively.


2. OBSERVATIONS


This study mainly retrieves data obtained from the
ALMASOP program (#2018.1.00302.S) and supplemental
data obtained from an earlier archival ALMA project
(#2015.1.00341.S).


2.1. _ALMASOP Project:_ _ALMA Cycle 6 #2018.1.00302.S_


The ALMASOP data were obtained from ALMA Cycle 6
program #2018.1.00302.S (PI: Tie Liu) in Band 6 (1.3 mm
or 230 GHz) with the combination of both the 12-m array
(configurations C43–5 and C43–2) and 7-m array (also
known as Atacama Compact Array, ACA, or Morita Array).
The projected baselines ranged from 4.7 to 1066 k _λ_, and
the resulting maximum recoverable scale was approximately
26 _[′′]_ . This survey selected 72 clumps in the Orion A, B,
and _λ_ Orionis clouds as targets, beginning from a sample
of PGCCs (Planck et al. 2016). The four spectral windows
centered at 216.6, 218.9, 231.0, and 233.0 GHz have a
uniform bandwidth of 1,875 MHz with a spectral resolution
of 1.129 MHz (1.4 km s _[−]_ [1] at 230 GHz).
We used tclean in CASA (CASA Team et al. 2022)
with a robust value of 2.0. The resulting angular resolution
was _∼_ 0 _[′′]_ _._ 42 (which corresponds to about 168 au for a
distance of _∼_ 400 pc) for both continuum and continuumsubtracted data cubes, and the sensitivities of the image reach



_∼_ 12 _µ_ Jy beam _[−]_ [1] and _∼_ 3.3 mJy beam _[−]_ [1] for the full–band
continuum and each channel, respectively. For more details
about the ALMASOP project, please refer to Dutta et al.
(2020).


2.2. _Archival Data:_ _ALMA Cycle 3 #2015.1.00341.S_


This study also retrieved ALMA Band 6 data obtained
from a Cycle 3 program (#2015.1.00341.S, PI: Satoko
Takahashi) for better-visualizing the intensity maps of the
CO 2 _−_ 1 and CH 3 OH 5 1 _,_ 4 – 4 2 _,_ 4 transitions as it had a
much better spatial resolution (FWHM beam size _∼_ 0 _[′′]_ _._ 16).
These observations were conducted on 2016 September 18.
The data cubes used in this study have a spectral resolution
of 0.244 MHz, corresponding to a velocity resolution of
0.32 km s _[−]_ [1] . The projected baseline ranged from 16 to 3200
k _λ_, and the maximum recoverable scale was about 1 _[′′]_ .
The images exported by the Additional Representative
Images for Legacy (ARI-L) project (Massardi et al. 2021)
were utilized. ARI-L, endorsed by the Joint ALMA
Observatory (JAO) and the European Southern Observatory
(ESO), is a European Development project for ALMA. Its
primary objective is to employ the ALMA Imaging Pipeline
on data from initial observing cycles (2–4) to regenerate data
products with equivalent completeness and quality to those
currently produced by ALMA for recent observations. The
original CASA pipeline version was 4.7.0 and the Briggs
robust parameter was set to 0.5. With a FWHM beam size of
0 _[′′]_ _._ 16, the sensitivity achieved _∼_ 6 mJy beam _[−]_ [1] for a channel

width of 0.244 MHz.


3. RESULTS


3.1. _Dust Continuum and Molecular Line Emission_


Table A1 lists the information of the molecular transitions

used in this study. Figure 1 shows the integrated intensity
images of selected molecular transitions within a size of
4 _[′′]_ _._ 0 ( _∼_ 1600 au) overlaid by 1.3 mm continuum and the SiO
integrated intensity maps. For completeness, the integrated
intensity images of all the molecular transitions in this study
are shown in Figure A1.


3.1.1. _1.3 mm Dust Continuum_


Figure 1 shows the observed 1.3 mm dust continuum which
appears to trace the extended envelope. As illustrated by
the dashed black contours, the continuum is spherically
_∼_
symmetric at the small scale ( 150 au), becomes elongated

_∼_
at a middle scale ( 400 au), and extend to north and east at
a large scale ( _∼_ 600 au). The brightness temperature of the
1.3 mm continuum peak is 47 K with a beam size of 0 _[′′]_ _._ 42.
Takahashi et al. (2012) and Takahashi et al. (2019) reported
brightness temperatures of 52 K and 192 K with beam sizes
of 0 _[′′]_ _._ 27 and 0 _[′′]_ _._ 024, respectively. These relatively high dust
continuum brightness temperatures suggest that the inner

4 H SU ET AL .


**Figure 1.** Integrated intensity images (moment-0 maps) of selected molecular transitions: C [18] O, CO, CH 3 CHO, HCOOCH 3, H 2 CO, CH 3 OH,
OCS, [13] CS, and H 2 S. The origin of the coordinate system is the 1.3 mm continuum peak at [ _α_ 2000 _, δ_ 2000 ] = [05 [h] 35 [m] 23 [s] .42, -05 _[◦]_ 01 _[′]_ 30 _[′′]_ .6],
and the ranges of right ascension (x-axis) and declination (y-axis) span _±_ 2 _[′′]_ . Each panel is labeled at the top with the corresponding chemical
formula and the upper energy level of the transition shown in color. The velocity ranges for integration are _±_ 40 km s _[−]_ [1] for CO and SiO,
_±_ 3 km s _[−]_ [1] for [13] CS, and _±_ 7 _._ 5 km s _[−]_ [1] for others. The black dashed contours depict the 1.3 mm continuum, set at levels of [5, 10, 20, 40, 80,
160] _σ_, where _σ_ corresponds to 0.9 mJy beam _[−]_ [1] (or 0.13 K in terms of brightness temperature). The orange ellipse located at the bottom left
corner indicate the beam sizes for the Cycle 6 ALMA program. The green contours display the SiO integrated intensity map, highlighted at
levels of [10, 25, 40] _σ_, where each _σ_ corresponds to 28 mJy beam _[−]_ [1] km s _[−]_ [1] . The distribution of the molecules in panels (e)–(i) are particularly
noteworthy; these molecules are not typical outflow tracers but exhibit two-lobed distributions. The white cross in panels (c) and (d) illustrate
the peak position of the corresponding transition.



region is very warm, similar with the cases of NGC 1333
IRAS 4A1 (57 K) and 4A2 (42 K) reported by Sahu et al.
(2019). In addition, HOPS 87 and IRAS 4A2 are reported
to harbor hot corinos (e.g., Hsu et al. 2022; Sahu et al.
2019). Due to these similarities, we adopt the assumed dust
temperature (60 K) from Sahu et al. (2019) for evaluating the
optical depth and the molecular hydrogen column density.
We note that the beam size of our study ( _∼_ 160 au) is larger
than the value ( _∼_ 80 au) of Sahu et al. (2019). As a result,
this adopted continuum brightness temperature (60 K) could



be overestiamted. In such case, the derived optical depth
and the molecular hydrogen column density in the following

contexts are their lower limits.

We evaluate the optical depth ( _τ_ _ν_ ) using the following
equation adopted from Kauffmann et al. (2008):


_I_ _ν_ = _B_ _ν_ ( _T_ d )(1 _−_ _e_ _[−][τ]_ _[ν]_ ) = _[F]_ [ beam] _ν_ _,_ (1)
Ω A


where _I_ _ν_ is the beam-averaged intensity, _B_ _ν_ is the Planck
function, _T_ d is the dust temperature, _F_ _ν_ [beam] is the observed

HOPS 87 5


**Figure 2.** The CH 3 OH 5 1 _,_ 4 _−_ 4 2 _,_ 3 transition in Cycle 3 observations. The top and bottom rows show the images at the blue- and red-shifted
channels, respectively. The labels in each panel shows the relative velocity (∆ _v_ = _v −_ _v_ LSR ). At ∆ _v_ = 0 km s _[−]_ [1] the intensity map displays
an arc-like emission pattern west of the center with an absorption feature toward the continuum peak. At _|_ ∆ _v| >_ 0 _._ 68 km s _[−]_ [1], there is a single
lobe (∆ _δ_ _∼_ 0 _[′′]_ _._ 3) on each of the northern and the southern sides of the arc (∆ _δ_ _∼_ 0 _[′′]_ _._ 2) seen at ∆ _v_ = 0 km s _[−]_ [1] .



flux per beam, and Ω A is the solid angle of the beam.
Adopting the brightness temperature at the continuum peak,
the derived optical depth _τ_ _ν_ is 1.55, indicating that the
continuum is somewhat optically thick.
We estimate the molecular hydrogen column density
_N_ (H 2 ) adopting Equation A.9 in Kauffmann et al. (2008):


_N_ (H 2 ) = _τ_ _ν_ _,_ (2)
_µ m_ H _κ_ _ν_


where _µ_ is the molecular weight per hydrogen molecule
_∼_ 2.8, _m_ H is the mass of atomic hydrogen, and _κ_ _ν_ is the
dust mass opacity. To estimate _κ_ _ν_, we adopt the form of
_κ_ _ν_ = 0 _._ 1( _ν/_ THz) _[β]_ cm [2] g _[−]_ [1], where _β_ is the the dust opacity
index, from Beckwith et al. (1990). We assume the index
_β_ to be 1.70, which is the typical opacity index of cold
clumps in the submillimeter band (Juvela et al. 2018), and
the estimated _κ_ _ν_ is 0.0083 cm [2] g _[−]_ [1] at 1.3 mm. Assuming
a gas-to-dust ratio of 100, the resulting molecular hydrogen
column density _N_ (H 2 ) is 2 _._ 89 _×_ 10 [25] cm _[−]_ [2] .


3.1.2. _C_ [18] _O: Extended Warm Gas_


C [18] O is a good tracer of warm gas, as it is released into
gas phase at a temperature of _∼_ 20 K (Tychoniec et al. 2021)
and has a low critical density ( _∼_ 10 [4] cm _[−]_ [3] for _J_ = 2 _−_ 1,
Saito et al. 2001). We show in Figure 1 (a) the C [18] O
integrated intensity map, which overall extends to the north
and east, is consistent with the dust continuum. In addition
to the extended gas, there appears to be a hole absent of
emission centered at the continuum peak position with a size
of 0 _[′′]_ _._ 5, which is comparable to the beam size. Given that the
C [18] O emission is significant around the hole, it is unlikely
that it results from a complete absence of C [18] O molecules.
This hole could be due to the comparable dust (continuum)
temperature and the C [18] O gas (excitation) temperature.



At the north and south sides of the hole, the bright
C [18] O emission may result from the bipolar outflow, as the
positions are corresponding to the outflow lobes illustrated
by the green contours. Near the northeast corner (∆ _α_ _∼_
+1 _[′′]_ _._ 5, ∆ _δ_ _∼_ +1 _[′′]_ _._ 5) of panel (a), a separated peak of
C [18] O integrated intensity is detected and corresponds to a
separate source (MMS6-NE at 0.9 mm and IRS 3 at near-IR)
identified as a Class I protostellar core by Takahashi et al.
(2009).


3.1.3. _CO and SiO: Outflows_


We show in Figure 1 (b) the integrated intensity map of
the typical outflow tracer CO ( _J_ = 2 _−_ 1). Consistent with
the discoveries of Takahashi & Ho (2012) in CO (3 _−_ 2),
the bipolar outflow, which is compact (about 2 _[′′]_ long for
each lobe), exhibits two lobes at the northern and southern
sides. As we will show in the following sections, the blue
shifted and red-shifted characteristics are in the northern and

southern lobes, respectively. The absence of CO emission
at the region below a ∆ _p_ (the position offset from the
continuum peak position) of 0 _[′′]_ _._ 2 is due to both absorption
along the line of sight and missing flux at low velocities
due to interferometry. For the former, the absorption feature
is also confirmed in the line profile at the continuum peak
position. The latter was anticipated as implied from the PV
diagram shown in Sect. 3.2.
SiO is another well-known outflow gas tracer, particularly
the protostellar jet and the consequent shocked and collision
regions. As illustrated by the green contours in Figure 1,
SiO also trace outflowing gas in HOPS 87. The sizes of the
northern and southern SiO lobes are comparable to those of
the CO outflows.


3.1.4. _CH_ 3 _CHO and HCOOCH_ 3 _:_ _Hot Corino Zone_

6 H SU ET AL .


**Figure 3.** Spectra of selected molecular transitions along the cavity axis. The labels at the right of each row show the formula and the upper
energy of each transition. The labels at the top of each column show the angular offset from the continuum peak. The horizontal dashed lines
represent the level of 5 _σ_ . In the panels of [13] CS, the lines at _∼−_ 7 km s _[−]_ [1] is another molecular transition. The y-axis is the fraction of peak
intensity. The north is blue-shifted (coming toward us) and the south is red-shifted (moving away), and the lines extend to bluer and redder
velocities at the north and south positions, respectively.



A hot corino is a warm region, particularly the innermost
envelope (Hsu et al. 2023) around a low-mass protostar,
abundant in saturated COMs such as CH 3 CHO and
HCOOCH 3 . Figure 1 (c) and (d) show the CH 3 CHO
65 K and HCOOCH 3 109 K integrated intensity images,
respectively, which illustrate the compact hot corino zone
previously reported by Hsu et al. (2020) and Hsu et al.
(2022). This hot corino zone resides in the hole seen in
the C [18] O map, supporting that the hole seen in the C [18] O
integrated intensity map likely does not result from a lack
of C [18] O gas.
As illustrated by the white crosses in Figure 1 (c) and
(d), the bright COM emission is slightly offset toward the
west from the continuum peak position. Figure 2 shows
the intensity maps at each channel of a CH 3 OH transition
obtained from the Cycle 3 observations At ∆ _v_ = 0 km s _[−]_ [1]

the intensity map displays an arc-like emission pattern west
of the center with an absorption feature toward the continuum
peak. This arc outlines where the hot corino is, which is



the warm COM emission resided in the innermost envelope,
where the C [18] O emission shows the absorption feature. The
existing COM emission also suggest that the temperatures of
the COMs are higher than that of C [18] O. In other words, the
warm gas-phase COM molecules are distributed in both the
central absorption region and the arc emission region, and the

former is due to the even hotter continuum at the center. As a

result, the offset of the COM emission observed in our Cycle
6 program results from the asymmetric innermost warm
envelope gas surrounding the central warmer continuum
optically thick region. It is noteworthy that the distribution
is different at higher velocities, which will be elaborated on
in the following sections. The COM absorption feature we
observed in CH 3 OH is also been seen in IRAS 4A1 (Sahu
et al. 2019) and IRAS 16293-2422 B (e.g., Oya et al. 2018).


3.1.5. _Molecules Exhibiting Two Localized Lobes_


In Figure 1, some molecules, namely H 2 CO (panel e),
OCS (panel g), [13] CS (panel h), and H 2 S (i), apparently

HOPS 87 7



exhibit two-lobe signatures. Interestingly, CH 3 OH (panel f)
exhibits a two-lobe signature in addition to its hot corino

localization at low velocities. These molecules are not

“typical” outflow tracers, while H 2 CO could also trace the
low-velocity outflows (Izumi et al. 2024). The position offset
from the continuum peak (∆ _p_ ) of the lobes for different
molecules are similar ( _∼_ 0 _[′′]_ _._ 3), indicating that the two regions
are chemically rich. The sizes of the lobes are comparable
to the size of the beam, indicating that these chemically rich
regions are localized.
These two chemically rich localized regions are near the
bases of the bipolar SiO molecular outflow (green contours).
We first checked whether the two regions are the outer
extended parts of the hot corino in HOPS 87. As shown
in Figure 2, the intensity maps at ∆ _v_ = 0 km s _[−]_ [1] and
at _|_ ∆ _v|_ _>_ 0 _._ 68 km s _[−]_ [1] display different patterns. The
former traces the hot corino zone, as we discuss in Sect.
3.1.4, whereas the latter exhibts a single lobe on each of

the northern and the southern sides of the hot corino zone.
Particularly at _|_ ∆ _v|_ _<_ 0 _._ 68 km s _[−]_ [1], the position offset
of the lobe (∆ _δ_ _∼_ 0 _[′′]_ _._ 3) appears to be slightly beyond the
“boundary” of the hot corino (∆ _δ_ _∼_ 0 _[′′]_ _._ 2) seen at ∆ _v_ =
0 km s _[−]_ [1] . These observations suggest that the two lobes
and the hot corino are tracing different regions. Moreover,
the positions of the lobes, along with their consistent velocity
directions with the bipolar outflow imply the potential
association of the molecular gas with the bipolar outflow.
This could be similar to OCS in the high-mass protostellar
core NGC 2264 CMM3B, which also exhibits two lobes
at the bases of the outflows, as found by Shibayama et al.
(2021). The authors suggest that the OCS is tracing the bases
of outflows in addition to the disk/envelope system.


3.2. _Kinematics_


To further justify the association between the bipolar
outflow and the two localized chemically rich regions, we
initially extract the continuum-subtracted spectra along the
cavity axis (position angle PA = _−_ 4 _[◦]_ ), centered at the
1.3 mm continuum peak. Figure 3 depicts the spectra
of selected molecular transitions along the outflow axis.
Note that the y-axis is the fraction of peak intensity for
better visualizing the line profiles of all pixels. Despite
the limited spectral resolution ( _∼_ 1.3 km s _[−]_ [1] ), discernible
symmetry between spectra at the north and south positions
is observed. Firstly, the north is blue-shifted, coming toward
us, and the south is red-shifted, moving away. Secondly, the

lines extend to bluer and redder velocities at the north and

south positions, respectively. These consistencies solidify
their associations with the bipolar outflow. The velocity
of the CO outflow reaches 40 km s _[−]_ [1] (Dutta et al. 2020),
while the velocities of the molecules in Figure 3 are around
5 km s _[−]_ [1] .



To have a closer look at the kinematics, we made the
position-velocity (PV) diagrams (Figure 4) cut along the
outflow axis with an average width of three pixels with a pixel
size of 0 _[′′]_ _._ 06 using CARTA 4.0 (Comrie et al. 2021). First, the
gap of the CO (grey contours) at ∆ _v_ = 0 km s _[−]_ [1] indicates
the missing flux due to interferometry at low velocities.
Second, as shown in Figure 4 (k), the rapid growth of velocity
∆ _v_ with position offset ∆ _p_ from ∆ _p_ = 0 _[′′]_ to 0 _[′′]_ _._ 3 and _−_ 0 _[′′]_ _._ 2
is significant in SiO. Finally, as shown in Figure 4 (a) to (g),
the broadening of the velocity range localized at ∆ _p_ = 0 _[′′]_ _._ 3
and _−_ 0 _[′′]_ _._ 2 is significant in CH 3 OH, H 2 CO, OCS, and H 2 S
and tentative in [13] CS. These characteristics suggest that
these molecules (i.e., SiO, CH 3 OH, H 2 CO, OCS, H 2 S, and
13 CS) are more likely tracing jet-driven outflows rather than
wide-angle winds (Lee et al. 2001).
For the molecular transitions exhibiting two localized
blobs, the northern (∆ _p_ _>_ 0 _[′′]_ ) blobs have a larger velocity
width than what the southern (∆ _p <_ 0 _[′′]_ ) blobs. As shown by
the navy dashed polylines, most of the molecules including
CH 3 OH, OCS, and H 2 S have comparable position offsets,
indicating their possible common origin. The only exception
is H 2 CO, which has slightly higher position offset of _∼_ 0 _[′′]_ _._ 40.
Finally, for all transitions, the position offsets of the northern
blobs (∆ _p_ _∼_ 0 _[′′]_ _._ 3) are generally higher than the southern
blobs ( _−_ 0 _[′′]_ _._ 2), as also illustrated in Figure 2.
Figure 5 shows the velocity widths of the blobs, which
is defined as the maximum speed for each lobe in the
PV diagrams (Figure 4) filtered out by a threshold of 5 _σ_ .
The velocity widths seem to be anti-correlated with upper
energies of the molecular transitions observed. As illustrated
in Figure 5, the velocity width of CH 3 OH decreases from
5.6 km s _[−]_ [1] at _E_ u = 45 K to 2.8 km s _[−]_ [1] at _E_ u =
190 K. For H 2 CO, from the lowest ( _E_ u = 21 K) to
the highest upper energy ( _E_ u = 174 K) transitions, the
velocity width decreases from 9.8 to 2.8 km s _[−]_ [1] . These
negative correlations could simply result from the different
line intensities of the transitions having different upper
energies, or it could possibly be due to the warmer gas at the
inner regions. We favor the former based on the flat ratios
between high and low transitions at high-velocity wings in
Figure B1. In another word, the flat ratios imply that there
is no significant change in the gas temperature. However,
the weak line intensities at high velocity, particularly for
the high-upper-energy transitions, prevent us from justifying

this.


4. DISCUSSION


4.1. _The Localized Chemically rich Features in HOPS 87_


Our findings suggest that the two chemically rich regions
localized near the bases of the molecular jet are due to jetdriven outflows. The hosting molecular inventories in the

8 H SU ET AL .


**Figure 4.** The PV diagrams of selected molecular transitions along the outflow axis (position angle PA = _−_ 4 _[◦]_ with the center is at the 1.3 mm
continuum peak. The relative position offset (∆ _p_ ) is from south (∆ _p_ _<_ 0 _[′′]_ ) to north (∆ _p_ _>_ 0 _[′′]_ ). The upper left label in each panel show
the chemical species and the upper energy _E_ u of the transitions. Note that the diagrams are exported from the data cube of the full spectral
window so the separated components may come from molecular transitions other than the labeled one in each label (e.g., the components at
(-7.5 km s _[−]_ [1], 0 _[′′]_ ) in panel (h) and at (-7.5 km s _[−]_ [1], 0 _[′′]_ ) in panel (k). The color maps and the brown contours are the PV diagram of the labeled
transitions. The grey contours represent the CO PV diagram. The brown and grey contours are in steps of [5, 10, 15, 20, 25, 30, 40, 50, 60,
70, 80] _σ_ . The navy polyline, referred from the PV diagram of the CH 3 OH 45 K transition, consists of two horizontal lines at ∆ _p_ = 0 _[′′]_ _._ 3 and
_−_ 0 _[′′]_ _._ 2 and a diagonal line moves from ∆ _p_ = 0 _[′′]_ _._ 3 to _−_ 0 _[′′]_ _._ 2 at ∆ _v_ = 0 _._ 75 km s _[−]_ [1] and _−_ 0 _._ 75 km s _[−]_ [1], respectively. The diagrams are exported
by CARTA 4.0 (Comrie et al. 2021). The gap in CO indicates the missing flux at low velocities due to interferometry. The broadening of the
velocity range localized at ∆ _p_ = 0 _[′′]_ _._ 3 and _−_ 0 _[′′]_ _._ 2 is significant in CH 3 OH, H 2 CO, OCS, and H 2 S and tentatively observed in [13] CS. Additionally,
the rapid growth of velocity ∆ _v_ with position offset ∆ _p_ described in Lee et al. (2001) is significant in SiO. These characteristics suggest that
these molecules are also tracing jet-driven bow shocks (Lee et al. 2001).



shocked regions comprise H 2 CO, CH 3 OH, OCS, [13] CS, and
H 2 S.
Finally, for all transitions, the position offsets of the
northern blobs (∆ _p_ _∼_ 0 _[′′]_ _._ 3) are generally higher than
the southern blobs ( _−_ 0 _[′′]_ _._ 2), as also illustrated in Figure 2.
**Overall,** **most** **of** **the** **molecules** **have** **similar** **position**

**offsets** **with** **each** **other** **for** **the** **northern** **lobe** **and**

**the** **southern** **lobe** **individually.** **The** **only** **exception** **is**



**H** 2 **CO,** **which** **peaks** **at** **a** **slightly** **greater** **position** **offset.**
**Meanwhile,** **the** **northern** **(blue-shifted)** **lobe** **peaks** **at** **a**
**larger position offset than the south (red-shifted) lobe for**
**both H** 2 **CO and all other transitions.**


4.1.1. _The Origin of the Localized Chemically Rich Feature_


Two potential mechanisms are proposed for the bringing
COMs from the ice phase to the gas phase in YSOs:

HOPS 87 9


sputtering picture due to (1) the velocity spur structures (i.e.,
wide velocity dispersion) of the molecular tracers and (2) the
coexistence of SiO gas, an indicator of dust destruction (e.g.,
Guillet et al. 2009). Although we do not see the knots of the
typical tracers, CO and SiO, at the same position offset, we
do see SiO knots at slightly higher position offsets (∆ _p_ =
_±_ 0 _[′′]_ _._ 5), as shown in Figure 4 (k). We note that Le Gouellec
et al. (2024) has detected molecular hydrogen lines in
the 2 _µ_ m band in HOPS 87, a spectral feature typically
associated with shocks in protostellar outflow cavities.


4.1.2. _Comparisons with the counterpart hot corino_



**Figure 5.** The velocity width versus upper energy for the molecular
transitions in the two chemically rich regions. Only molecular
species having multiple transitions are included. The blue and red
markers represent the measurement at the blue-shifted (northern)
and red-shifted (southern) lobes, respectively. The error bars are
referred from the spectral channel widths ( _∼_ 1.4 km s _[−]_ [1] .) The
velocity width seem to be anti-correlated with upper energies of the
molecular transitions, possibly due to the different populations of
each transition state.


thermal desorption and grain sputtering. For the former, ice
sublimates at approximately 100 K and the frozen molecules
are exclusively released into the gas phase (e.g. Busch
et al. 2022). In such case, the rotational temperature of the
desorbed molecules is expected to be higher or comparable
to the ice sublimation temperature at around 100 K. Even
below ice sublimation temperature at _∼_ 20–30 K, “partial”
thermal desorption may possibly occur, specifically at the
outermost layer of the icy mantle. This may result from lower
binding energies (and consequently desorption energies),
but the uncertain nature of these binding energies makes
confirmation difficult (Busch et al. 2022). As discussed by
Busch et al. (2022), partial thermal desorption is inefficient
compared to the complete thermal desorption (i.e., coevaporation with ice).
For the latter, the sputtering of grains requires shocks,
commonly occurring when ejected/outflowing materials
collide with the dense surrounding medium at high speeds.
The collisions can release H 2 O as well as COMs from the
ice phase to the gas phase (e.g., Caselli et al. 1997; Jim´enezSerra et al. 2008). The velocity dispersion of the molecular
lines is expected to be broad due to the nature of shocks.
Shocks can also heat up the materials, leading to the thermal
desorption of molecules (e.g., Miura et al. 2017). After the
shock front, the shocked materials begin to cool and are not
necessarily warm (e.g., James et al. 2020).
Among the above two mechanisms (i.e., ice sublimation
and grain sputtering) able to lead the richness of molecules,
in particular those form within ice mantle such as CH 3 OH
and OCS, our findings favor the shock-induced grain



To compare the chemical compositions of the hot corino
and chemically rich shocked regions near the outflow origins,
we extracted the PV diagrams with cuts along and across
the outflow axis for molecules tracing between jet (SiO), hot
corino zone (HCOOCH 3 and CH 3 OCH 3 ), and both regions
(CH 3 OH and H 2 CO) in Figure 6. Note that the x-axes are
in terms of frequency to cover multiple molecular transitions
within each panel. As shown in 4 (a) and (b), the typical
outflowing gas tracer SiO only appears in the cut along the
outflow axis and shows a spur structure. In 4 (c) and (d),
COMs HCOOCH 3 and CH 3 OCH 3 exhibit a single peak in
both diagrams, suggesting that they are present only in the
hot corino zone. In contrast, as illustrated in 4 (e) and (f),
CH 3 OH and H 2 CO show a single peak on the cut across the
outflow axis and a spur signature on the cut along the outflow
axis. This indicates that some molecules (i.e., CH 3 OH and
H 2 CO) residing in the hot corino zone are also present in the
shocked regions.


4.1.3. _Implications_


On the basis that COMs are thought to be primarily
formed within the icy mantle on dust grains and then
released into the gas phase (e.g., Herbst & van Dishoeck
2009; Yamamoto 2016), the observed gaseous COMs can
reveal a glimpse of the ice composition. Therefore, the
difference in gaseous COM composition between the hot
corino zone and the jet-localized shocked regions in HOPS
87 suggests distinct ice compositions of the dust grains in
these areas. In the hot corino zone of HOPS 87, the dust
grains have hosted a variety of COMs such as CH 3 CHO,
HCOOCH 3, and CH 3 OCH 3 . The presence of these larger
COMs (compared to CH 3 OH) indicates that the ice mantles
have had a prolonged period for complex chemistry to occur.
In contrast, in the jet-localized shocked regions, the only
firmly detected COM is CH 3 OH. As the simplest COM and
a precursor to larger COMs, the formation history of CH 3 OH
is relatively straightforward compared to larger COMs such
as CH 3 CHO. The formation of the former can be achieved
via a series of hydrogenation with the frozen CO, and the
formation of the latter requires more atoms/molecules as
reactants (e.g., Herbst & van Dishoeck 2009; Yamamoto

10 H SU ET AL .



2016). This suggests that either the icy mantle, at least
its top layer, on dust grains in the shocked region have
not undergone as extensive chemical processing, or they
have experienced cycles of ice sublimation and reformation,
limiting the formation of larger COMs.
Alternatively, the chemical composition could be affected
by shocks. First, molecules could be destroyed by shocks
(e.g., Holdship et al. 2017). For example, as speculated by
Arce et al. (2008), the low CH 3 CN/CH 3 OH ratio in L1157
B1 shock may be due to the rapid destruction of CH 3 CN.
Similarly, in HOPS 87, the larger COMs in the jet-localized
regions could possibly be destroyed. Second, shocks may
enhance chemical reactions not commonly present in cold
gas through the so-called “shock chemistry,” due to factors
such as high temperature and sputtered molecular species
(e.g., Caselli et al. 1997; Burkhardt et al. 2019). As proposed
by Codella et al. (2015), a significant fraction of CH 3 CHO in
L1157 B1 could form in the gas phase due to the shocks.
Meanwhile, the chemical composition could be sensitive to
the evolution of shocks and further serve as a probe of the
shock stage (e.g., Burkhardt et al. 2016, 2019). A more
comprehensive investigation of the physical parameters (e.g.,
temperature) would help constrain the shock models. This
would further improve our understanding of the dynamic
interplay between the protostellar bipolar outflow, disk, inner
core environment, and the surrounding medium (e.g., Shu
et al. 1996; Shang et al. 2023).


4.1.4. _Comparison with L1157-B1_


L1157-B1 is a jet-driven bow shock recognized for
housing an inventory of COMs (e.g., Arce et al. 2008;
Mendoza et al. 2014; Codella et al. 2015; Lefloch et al.
2017; Feng et al. 2020; Spezzano et al. 2020; Benedettini
et al. 2021). Arce et al. (2008) estimated the timescale of
the outflows to be roughly less than 2000 years, which is
too short for their detected COMs to have formed primarily
through gas-phase reactions. Additionally, the shock is far
from the associated central protostar (spatial offset = 68 _[′′]_ _._ 3,
distance = 250 pc), rendering thermal desorption due to the
central protostar unlikely. The authors concluded that the
COMs more likely formed on the grain surface and then were
expelled from the icy mantles by the shock.
For HOPS 87, we expect that the temperature of the
molecules residing in the two jet-localized regions are warm
based on the detection of transition having high upper
energies (e.g., OCS 100 and 111 K transitions. ) In
contrsast, the rotational temperatures of molecules within
the L1157-B1 shock typically range from 20 to 50 K. For
instance, the kinematic temperature of OCS was reported to
be 46 _._ 8 _±_ 3 _._ 4 K by Holdship et al. (2019). As demonstrated
by Busquet et al. (2017), this relatively low temperature may
possibly be a result of cooling after the shocks. On the basis



of their demonstration, the relatively warm shocked region in
HOPS 87 suggests that the cooling process is insignificant,
consistent with the reported short dynamic age of the outflow.


4.2. _Suspected Component at the Bow Shocks_


In Figure 4, the CH 3 OH ( _E_ u = 45 K) and H 2 CO ( _E_ u =
21 K) transitions exhibit tentative components at ∆ _p_ _∼_
_±_ 1 _[′′]_ _._ 5. Given their proximity to the edges of the bipolar
outflow, we suspect that these emission components may
trace the interaction surface between the bipolar outflow and
the ambient quiescent material. This could be similar with
the arc-like HCOOH emission pattern in Orion-KL observed
by Liu et al. (2002).
These components are expected to have low gas
temperatures, given their distance (and fewer received
photons consequently) from the central protostar and the
non-detection in our data of high-upper-energy transitions
such as OCS 100 and 111 K (Figure 4). Between the two
potential associations, namely grain sputtering or thermal
desorption, we favor the former due to the (expected) low
temperature. The absence of high-velocity wings, another
signature of associations with shocks, may be attributed
to the low SNR. In this picture, these components would
possibly exhibit chemical similarities to the chemically rich
shocked regions such as L1157-B1 (e.g., Arce et al.
2008), also associated with bow shocks. A more sensitive
investigation is necessary to reveal the nature of these

components.


5. CONCLUSIONS


Using the ALMA Cycle 6 data from the ALMASOP
project and archival ALMA Cycle 3 data, our findings

include:


1. In the protostellar core HOPS 87, we discovered
two chemically rich and localized regions containing
CH 3 OH, H 2 CO, OCS, [13] CS, and H 2 S near the bases
of the molecular bipolar outflow. The position offsets
of these regions are consistent with those of the bipolar
outflow as traced by CO and SiO, with the northern
(blue-shifted) lobe peaking at a larger position offset
∆ _p_ than the southern (red-shifted) lobe.


2. These localized chemically rich features are more
likely due to shocks driven by jets rather than winds,
based on the shapes of the PV diagrams. Under the
jet-driven shock scenario, the chemically rich and jetlocalized regions are likely the knots often detected in
jets.


3. Compared to the counterpart hot corino in HOPS
87, the composition of COMs in the shocked regions
appears simpler. We speculate that this simple

HOPS 87 11


**Figure 6.** PV diagrams cut along (panels a, c, and e) and across (panels b, d, and f) to the outflow axis for three selected frequency ranges. The
x-axes are in terms of frequency. The origin of the y-axes is the continuum peak. The contours represent levels of [10, 20, 30, 40] _σ_ . In panels
(a) and (b), the typical outflowing gas tracer, SiO, is visible only in the cut along the outflow axis with a spur structure. Panels (c) and (d) show
that COMs like HCOOCH 3 and CH 3 OCH 3 display a single peak in both diagrams. In panels (e) and (f), CH 3 OH and H 2 CO present a single
peak in the cut across the outflow axis, accompanied by a two-lobe feature in the cut along the outflow axis.

12 H SU ET AL .


composition is due to resident dust grains undergoing
cycles of ice sublimation and subsequent reformation
during their journey from the circumstellar envelope
to the jet-localized region. Alternatively, it could
result from the shock chemistry, and the chemical
composition may further constrain the shock models.


ACKNOWLEDGMENTS


We thank the two anonymous reviewers for valuable
comments. This paper makes use of the following
ALMA data: ADS/JAO.ALMA#2015.1.00341.S and

ADS/JAO.ALMA#2018.1.00302.S. ALMA is a partnership
of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), NSTC
and ASIAA (Taiwan), and KASI (Republic of Korea),
in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ. This work made use of Astropy: [1] a communitydeveloped core Python package and an ecosystem of tools
and resources for astronomy (Astropy Collaboration et al.
2013; Price-Whelan et al. 2018; Astropy Collaboration
et al. 2022). S.-Y. H. and C.-F.L. acknowledge grants
from the National Science and Technology Council of
Taiwan (110-2112-M-001-021-MY3 and 112-2112-M-001039-MY3) and the Academia Sinica (Investigator Award
AS-IA-108-M01). LB gratefully acknowledges support by
the ANID BASALproject FB210003. DJ is supported by
NRC Canada and by an NSERC Discovery Grant. Y.-L.Y.
acknowledges support from Grant-in-Aid from the Ministry
of Education, Culture, Sports, Science, and Technology of
Japan (20H05845, 20H05844), and a pioneering project in
RIKEN (Evolution of Matter in the Universe).


_Software:_ Astropy (Astropy Collaboration et al. 2013;
Price-Whelan et al. 2018; Astropy Collaboration et al. 2022),
CASA (CASA Team et al. 2022), CARTA (Comrie et al.
2021),

HOPS 87 13


**Table A1.** Transitions in this study


Species _E_ u _f_ rest Quantum Number Database


(K) (MHz)


CO 17 230538 v=0; J=2-1 CDMS

SiO 31 217105 v=0; J=5-4 CDMS
C [18] O 16 219560 v=0; J=2-1 CDMS

H 2 CO 21 218222 J=3-2; Ka=0; Kc=3-2 CDMS

H 2 CO 68 218476 J=3-2; Ka=2; Kc=2-1 CDMS

H 2 CO 68 218760 J=3-2; Ka=2; Kc=1-0 CDMS

H 2 CO 174 216569 J=9; Ka=1; Kc=8-9 CDMS

CH 3 OH 45 218440 rovibSym=E; v=0; J=4-3; Ka=2-1; Kc=3-2 CDMS

CH 3 OH 165 232419 rovibSym=A1; v=0; J=10-9; Ka=2-3; Kc=8-7 CDMS

CH 3 OH 190 232945 rovibSym=E; v=0; J=10-11; Ka=3-2; Kc=7-9 CDMS

CH 3 CHO 65 216582 rovibSym=E; v=0; J=11-10; Ka=1; Kc=10-9 JPL

HCOOCH 3 109 216110 rovibSym=E; v=0; J=19-18; Ka=2; Kc=18-17 JPL

H 2 S 84 216710 v1=0; v2=0; v3=0; J=2; Ka=2-1; Kc=0-1 CDMS

OCS 100 218903 J=18-17; v1=0; v2=0; v3=0 CDMS

OCS 111 231061 J=19-18; v1=0; v2=0; v3=0 CDMS

13 CS 33 231221 v=0; J=5-4 CDMS


N OTE — _E_ u is the energy of the upper state, _f_ rest is the rest frequency.


APPENDIX


A. MOLECULAR TRANSITIONS


Table A1 shows the molecular transitions used in this

study. In addition, Figure A1 shows the integrated intensity
maps of the transitions.

14 H SU ET AL .


**Figure** **A1.** Integrated intensity images of all transitions listed in Table A1. The other captions follow Figure 1. Note that some panels are
repeated from Figure 1 but may be labeled differently. The black and the green contours depict the 1.3 mm continuum and the SiO integrated
intensity map, respectively.

HOPS 87 15


B. RATIOS BETWEEN PV DIAGRAM


Figure B1 shows the PV diagrams of ratios between flux
densities for selected transition pairs.


REFERENCES



Arce, H. G., Santiago-Garcia, J., Jorgensen, J. K., Tafalla, M., &

Bachiller, R. 2008, Astrophysical Journal Letters, 681, L21,

[doi: 10.1086/590110](http://doi.org/10.1086/590110)


Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013,

[A&A, 558, A33, doi: 10.1051/0004-6361/201322068](http://doi.org/10.1051/0004-6361/201322068)


Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al.

[2022, ApJ, 935, 167, doi: 10.3847/1538-4357/ac7c74](http://doi.org/10.3847/1538-4357/ac7c74)


Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R.

[1990, AJ, 99, 924, doi: 10.1086/115385](http://doi.org/10.1086/115385)


Benedettini, M., Viti, S., Codella, C., et al. 2021, A&A, 645, A91,

[doi: 10.1051/0004-6361/202039609](http://doi.org/10.1051/0004-6361/202039609)


Burkhardt, A. M., Shingledecker, C. N., Le Gal, R., et al. 2019, The

[Astrophysical Journal, 881, 32, doi: 10.3847/1538-4357/ab2be8](http://doi.org/10.3847/1538-4357/ab2be8)


Burkhardt, A. M., Dollhopf, N. M., Corby, J. F., et al. 2016, The

Astrophysical Journal, 827, 21,

[doi: 10.3847/0004-637X/827/1/21](http://doi.org/10.3847/0004-637X/827/1/21)


Busch, L. A., Belloche, A., Garrod, R. T., M¨uller, H. S. P., &

Menten, K. M. 2022, Astronomy and Astrophysics, 665, A96,

[doi: 10.1051/0004-6361/202243383](http://doi.org/10.1051/0004-6361/202243383)


Busquet, G., Fontani, F., Viti, S., et al. 2017, Astronomy and

[Astrophysics, 604, A20, doi: 10.1051/0004-6361/201730422](http://doi.org/10.1051/0004-6361/201730422)


CASA Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of

the Astronomical Society of the Pacific, 134, 114501,

[doi: 10.1088/1538-3873/ac9642](http://doi.org/10.1088/1538-3873/ac9642)


Caselli, P., Hartquist, T. W., & Havnes, O. 1997, Astronomy and

Astrophysics, 322, 296.

[https://ui.adsabs.harvard.edu/abs/1997A&A...322..296C](https://ui.adsabs.harvard.edu/abs/1997A&A...322..296C)


Ceccarelli, C. 2004, in Star Formation in the Interstellar Medium:

In Honor of David Hollenbach, Chris McKee and Frank Shu,

ASP Conference Proceeding, ed. D. Johnstone, F. Adams,

D. Lin, D. Neufeld, & E. Ostriker, Vol. 323, San Francisco,

Astronomical Society of the Pacific (ASP Conference

Proceedings)


Chini, R., Reipurth, B., WardThompson, D., et al. 1997,

[Astrophysical Journal, 474, L135, doi: 10.1086/310436](http://doi.org/10.1086/310436)


Codella, C., Fontani, F., Ceccarelli, C., et al. 2015, Monthly

Notices of the Royal Astronomical Society, 449, L11,

[doi: 10.1093/mnrasl/slu204](http://doi.org/10.1093/mnrasl/slu204)


Codella, C., Ceccarelli, C., Cabrit, S., et al. 2016, A&A, 586, L3,

[doi: 10.1051/0004-6361/201527424](http://doi.org/10.1051/0004-6361/201527424)


Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, Astrophysics

Source Code Library, ascl:2103.031.

[https://ui.adsabs.harvard.edu/abs/2021ascl.soft03031C](https://ui.adsabs.harvard.edu/abs/2021ascl.soft03031C)



Dutta, S., Lee, C.-F., Liu, T., et al. 2020, ApJS, 251, 20,

[doi: 10.3847/1538-4365/abba26](http://doi.org/10.3847/1538-4365/abba26)

Dutta, S., Lee, C.-F., Johnstone, D., et al. 2024, The Astronomical

[Journal, 167, 72, doi: 10.3847/1538-3881/ad152b](http://doi.org/10.3847/1538-3881/ad152b)

Feng, S., Codella, C., Ceccarelli, C., et al. 2020, The Astrophysical

[Journal, 896, 37, doi: 10.3847/1538-4357/ab8813](http://doi.org/10.3847/1538-4357/ab8813)

Furlan, E., Fischer, W. J., Ali, B., et al. 2016, The Astrophysical

Journal Supplement Series, 224, 5,

[doi: 10.3847/0067-0049/224/1/5](http://doi.org/10.3847/0067-0049/224/1/5)

Garrod, R. T., Wakelam, V., & Herbst, E. 2007, Astronomy and

[Astrophysics, 467, 1103, doi: 10.1051/0004-6361:20066704](http://doi.org/10.1051/0004-6361:20066704)

Guillet, V., Jones, A. P., & Pineau Des Forˆets, G. 2009, Astronomy

[and Astrophysics, 497, 145, doi: 10.1051/0004-6361/200811115](http://doi.org/10.1051/0004-6361/200811115)

Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427,

[doi: 10.1146/annurev-astro-082708-101654](http://doi.org/10.1146/annurev-astro-082708-101654)

Holdship, J., Viti, S., Jim´enez-Serra, I., Makrymallis, A., &

Priestley, F. 2017, The Astronomical Journal, 154, 38,

[doi: 10.3847/1538-3881/aa773f](http://doi.org/10.3847/1538-3881/aa773f)

Holdship, J., Jimenez-Serra, I., Viti, S., et al. 2019, The

[Astrophysical Journal, 878, 64, doi: 10.3847/1538-4357/ab1cb5](http://doi.org/10.3847/1538-4357/ab1cb5)

Hsu, S.-Y., Liu, S.-Y., Liu, T., et al. 2020, ApJ, 898, 107,

[doi: 10.3847/1538-4357/ab9f3a](http://doi.org/10.3847/1538-4357/ab9f3a)

[—. 2022, ApJ, 927, 218, doi: 10.3847/1538-4357/ac49e0](http://doi.org/10.3847/1538-4357/ac49e0)

Hsu, S.-Y., Liu, S.-Y., Johnstone, D., et al. 2023, The Astrophysical

[Journal, 956, 120, doi: 10.3847/1538-4357/acefcf](http://doi.org/10.3847/1538-4357/acefcf)

Izumi, N., Sanhueza, P., Koch, P. M., et al. 2024, The Astrophysical

[Journal, 963, 163, doi: 10.3847/1538-4357/ad18c6](http://doi.org/10.3847/1538-4357/ad18c6)

James, T. A., Viti, S., Holdship, J., & Jim´enez-Serra, I. 2020,

Astronomy and Astrophysics, 634, A17,

[doi: 10.1051/0004-6361/201936536](http://doi.org/10.1051/0004-6361/201936536)

Jim´enez-Serra, I., Caselli, P., Mart´ın-Pintado, J., & Hartquist, T. W.

2008, Astronomy and Astrophysics, 482, 549,

[doi: 10.1051/0004-6361:20078054](http://doi.org/10.1051/0004-6361:20078054)

Juvela, M., He, Jinhua, Pattle, Katherine, et al. 2018, A&A, 612,

[A71, doi: 10.1051/0004-6361/201731921](http://doi.org/10.1051/0004-6361/201731921)

Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., & Lee, C.

[W. 2008, A&A, 487, 993, doi: 10.1051/0004-6361:200809481](http://doi.org/10.1051/0004-6361:200809481)

Le Gouellec, V. J. M., Greene, T. P., Hillenbrand, L. A., & Yates,

Z. 2024, The Astrophysical Journal, 966, 91,

[doi: 10.3847/1538-4357/ad2935](http://doi.org/10.3847/1538-4357/ad2935)

Lee, C. F., Codella, C., Ceccarelli, C., & Lopez-Sepulcre, A. 2022,

[Astrophysical Journal, 937, 10, doi: 10.3847/1538-4357/ac8c28](http://doi.org/10.3847/1538-4357/ac8c28)

Lee, C.-F., Codella, C., Li, Z.-Y., & Liu, S.-Y. 2019a, ApJ, 876, 63,

[doi: 10.3847/1538-4357/ab15db](http://doi.org/10.3847/1538-4357/ab15db)

16 H SU ET AL .


**Figure B1.** The PV diagrams of ratios between flux densities. The label in each panel denotes the molecular transitions for the numerator and
denominator. The pixels having flux density smaller than 5 _σ_ are exculded.



Lee, C.-F., Li, Z.-Y., Ho, P. T. P., et al. 2017, ApJ, 843, 27,


[doi: 10.3847/1538-4357/aa7757](http://doi.org/10.3847/1538-4357/aa7757)


Lee, C. F., Mundy, L. G., Reipurth, B., Ostriker, E. C., & Stone,


J. M. 2000, Astrophysical Journal, 542, 925,


[doi: 10.1086/317056](http://doi.org/10.1086/317056)


Lee, C.-F., Stone, J. M., Ostriker, E. C., & Mundy, L. G. 2001, The


[Astrophysical Journal, 557, 429, doi: 10.1086/321648](http://doi.org/10.1086/321648)


Lee, J.-E., Lee, S., Baek, G., et al. 2019b, Nature Astronomy, 3,


[314, doi: 10.1038/s41550-018-0680-0](http://doi.org/10.1038/s41550-018-0680-0)


Lefloch, B., Ceccarelli, C., Codella, C., et al. 2017, Monthly


Notices of the Royal Astronomical Society, 469, L73,


[doi: 10.1093/mnrasl/slx050](http://doi.org/10.1093/mnrasl/slx050)


Liu, S.-Y., Girart, J. M., Remijan, A., & Snyder, L. E. 2002, The


[Astrophysical Journal, 576, 255, doi: 10.1086/341620](http://doi.org/10.1086/341620)


Massardi, M., Stoehr, F., Bendo, G. J., et al. 2021, Publications of


the Astronomical Society of the Pacific, 133, 085001,


[doi: 10.1088/1538-3873/ac159c](http://doi.org/10.1088/1538-3873/ac159c)


Mendoza, E., Lefloch, B., Lopez-Sepulcre, A., et al. 2014, Monthly


Notices of the Royal Astronomical Society, 445, 151,


[doi: 10.1093/mnras/stu1718](http://doi.org/10.1093/mnras/stu1718)


Miura, H., Yamamoto, T., Nomura, H., et al. 2017, The


[Astrophysical Journal, 839, 47, doi: 10.3847/1538-4357/aa67df](http://doi.org/10.3847/1538-4357/aa67df)


Okoda, Y., Oya, Y., Imai, M., et al. 2022, ApJ, 935, 136,


[doi: 10.3847/1538-4357/ac7ff4](http://doi.org/10.3847/1538-4357/ac7ff4)


Oya, Y., & Yamamoto, S. 2020, ApJ, 904, 185,


[doi: 10.3847/1538-4357/abbe14](http://doi.org/10.3847/1538-4357/abbe14)


Oya, Y., Moriwaki, K., Onishi, S., et al. 2018, The Astrophysical


[Journal, 854, 96, doi: 10.3847/1538-4357/aaa6c7](http://doi.org/10.3847/1538-4357/aaa6c7)


Planck, C., Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594,


[A28, doi: 10.1051/0004-6361/201525819](http://doi.org/10.1051/0004-6361/201525819)


Price-Whelan, A. M., Sip˝ocz, B. M., G¨unther, H. M., et al. 2018,


[AJ, 156, 123, doi: 10.3847/1538-3881/aabc4f](http://doi.org/10.3847/1538-3881/aabc4f)



Sahu, D., Liu, S. Y., Su, Y. N., et al. 2019, Astrophysical Journal,

[872, 196, doi: 10.3847/1538-4357/aaffda](http://doi.org/10.3847/1538-4357/aaffda)


Saito, H., Mizuno, N., Moriguchi, Y., et al. 2001, Publications of

the Astronomical Society of Japan, 53, 1037,

[doi: 10.1093/pasj/53.6.1037](http://doi.org/10.1093/pasj/53.6.1037)

Shang, H., Liu, C.-F., Krasnopolsky, R., & Wang, L.-Y. 2023, The

Astrophysical Journal, 944, 230,

[doi: 10.3847/1538-4357/aca763](http://doi.org/10.3847/1538-4357/aca763)

Shibayama, Y., Watanabe, Y., Oya, Y., et al. 2021, The

[Astrophysical Journal, 918, 32, doi: 10.3847/1538-4357/ac0ef6](http://doi.org/10.3847/1538-4357/ac0ef6)

Shu, F. H., Shang, H., & Lee, T. 1996, Science, 271, 1545,

[doi: 10.1126/science.271.5255.1545](http://doi.org/10.1126/science.271.5255.1545)

Spezzano, S., Codella, C., Podio, L., et al. 2020, A&A, 640, A74,

[doi: 10.1051/0004-6361/202037864](http://doi.org/10.1051/0004-6361/202037864)

Tabone, B., Cabrit, S., Bianchi, E., et al. 2017, A&A, 607, L6,

[doi: 10.1051/0004-6361/201731691](http://doi.org/10.1051/0004-6361/201731691)

Takahashi, S., & Ho, P. T. P. 2012, Astrophysical Journal Letters,

[745, L10, doi: 10.1088/2041-8205/745/1/L10](http://doi.org/10.1088/2041-8205/745/1/L10)

Takahashi, S., Ho, P. T. P., Tang, Y.-W., Kawabe, R., & Saito, M.

2009, The Astrophysical Journal, 704, 1459,

[doi: 10.1088/0004-637X/704/2/1459](http://doi.org/10.1088/0004-637X/704/2/1459)

Takahashi, S., Machida, M. N., Tomisaka, K., et al. 2019,

[Astrophysical Journal, 872, 70, doi: 10.3847/1538-4357/aaf6ed](http://doi.org/10.3847/1538-4357/aaf6ed)

Takahashi, S., Saigo, K., Ho, P. T. P., & Tomida, K. 2012, The

Astrophysical Journal, 752, 10,

[doi: 10.1088/0004-637x/752/1/10](http://doi.org/10.1088/0004-637x/752/1/10)

Tychoniec, Ł., van Dishoeck, E. F., van’t Hoff, M. L. R., et al.

[2021, A&A, 655, A65, doi: 10.1051/0004-6361/202140692](http://doi.org/10.1051/0004-6361/202140692)

Vastel, C., Alves, F., Ceccarelli, C., et al. 2022, Astronomy and

[Astrophysics, 664, A171, doi: 10.1051/0004-6361/202243414](http://doi.org/10.1051/0004-6361/202243414)

Yamamoto, S. 2016, Introduction to Astrochemistry: Chemical

Evolution from Interstellar Clouds to Star and Planet Formation

(Springer Japan).

[https://books.google.com.tw/books?id=Q0sbswEACAAJ](https://books.google.com.tw/books?id=Q0sbswEACAAJ)


</paper>

## Items to check

```json
[
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "The localized chemically rich regions are driven by jet shocks rather than wide-angle winds or being part of the central hot corino.",
  "failed_quote": "The locations and kinematics suggest that these localized features are due to jet driven shocks rather than being part of the hot corino region encasing the protostar."
 }
]
```
