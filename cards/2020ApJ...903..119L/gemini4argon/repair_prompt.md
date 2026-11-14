# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...903..119L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version March 7, 2022
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**The** **ALMA** **Survey** **of** **70** _µ_ m **Dark** **High-mass** **Clumps** **in** **Early** **Stages** **(ASHES).** **II:** **Molecular**
**Outflows** **in** **the** **Extreme** **Early** **Stages** **of** **Protocluster** **Formation**


[Shanghuo](http://orcid.org/0000-0003-1275-5251) Li, [1, 2, 3, 4] Patricio Sanhueza, [5, 6] Qizhou Zhang, [2] Fumitaka Nakamura, [5, 6] Xing Lu, [5] Junzhi Wang, [1]

Tie Liu, [1] Ken’ichi Tatematsu, [5] James M. Jackson, [7] Andrea Silva, [5] Andr´es E. Guzm´an, [5] Takeshi Sakai, [8]

Natsuko Izumi, [5, 9] Daniel Tafoya, [10] Fei Li, [1, 3] Yanett Contreras, [11] Kaho Morii, [12] and Kee-Tae Kim [4, 13]


1 _Shanghai_ _Astronomical_ _Observatory,_ _Chinese_ _Academy_ _of_ _Sciences,_ _80_ _Nandan_ _Road,_ _Shanghai_ _200030,_ _China_
2 _Center_ _for_ _Astrophysics_ _|_ _Harvard_ _&_ _Smithsonian,_ _60_ _Garden_ _Street,_ _Cambridge,_ _MA_ _02138,_ _USA_
3 _University_ _of_ _Chinese_ _Academy_ _of_ _Sciences,_ _19A_ _Yuquanlu,_ _Beijing_ _100049,_ _China_
4 _Korea_ _Astronomy_ _and_ _Space_ _Science_ _Institute,_ _776_ _Daedeokdae-ro,_ _Yuseong-gu,_ _Daejeon_ _34055,_ _Republic_ _of_ _Korea_
5 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _National_ _Institutes_ _of_ _Natural_ _Sciences,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
6 _Department_ _of_ _Astronomical_ _Science,_ _SOKENDAI_ _(The_ _Graduate_ _University_ _for_ _Advanced_ _Studies),_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_
_181-8588,_ _Japan_
7 _SOFIA_ _Science_ _Center,_ _USRA,_ _NASA_ _Ames_ _Research_ _Center,_ _Moffett_ _Field_ _CA_ _94045,_ _USA_
8 _Graduate_ _School_ _of_ _Informatics_ _and_ _Engineering,_ _The_ _University_ _of_ _Electro-Communications,_ _Chofu,_ _Tokyo_ _182-8585,_ _Japan._
9 _College_ _of_ _Science,_ _Ibaraki_ _University,_ _2-1-1_ _Bunkyo,_ _Mito,_ _Ibaraki_ _310-8512,_ _Japan_
10 _Department_ _of_ _Space,_ _Earth_ _and_ _Environment,_ _Chalmers_ _University_ _of_ _Technology,_ _Onsala_ _Space_ _Observatory,_ _439_ _92_ _Onsala,_ _Sweden_
11 _Leiden_ _Observatory,_ _Leiden_ _University,_ _PO_ _Box_ _9513,_ _NL-2300_ _RA_ _Leiden,_ _the_ _Netherlands_
12 _Department_ _of_ _Astronomy,_ _Graduate_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _2-21-1,_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-0015,_ _Japan_
13 _University_ _of_ _Science_ _and_ _Technology,_ _217_ _Gajeong-ro,_ _Yuseong-gu,_ _Daejeon_ _34113,_ _Republic_ _of_ _Korea_


ABSTRACT


We present a study of outflows at extremely early stages of high-mass star formation obtained from
the ALMA Survey of 70 _µ_ m dark High-mass clumps in Early Stages (ASHES). Twelve massive 3.6 _−_ 70
_µ_ m dark prestellar clump candidates were observed with the Atacama Large Millimeter/submillimeter
Array (ALMA) in Band 6. Forty-three outflows are identified toward 41 out of 301 dense cores using
the CO and SiO emission lines, yielding a detection rate of 14%. We discover 6 episodic molecular
outflows associated with low- to high-mass cores, indicating that episodic outflows (and therefore
episodic accretion) begin at extremely early stages of protostellar evolution for a range of core masses.
The time span between consecutive ejection events is much smaller than those found in more evolved
stages, which indicates that the ejection episodicity timescale is likely not constant over time. The
estimated outflow dynamical timescale appears to increase with core masses, which likely indicates that
more massive cores have longer accretion timescales than less massive cores. The lower accretion rates
in these 70 _µ_ m dark objects compared to the more evolved protostars indicate that the accretion rates
increase with time. The total outflow energy rate is smaller than the turbulent energy dissipation
rate, which suggests that outflow induced turbulence cannot sustain the internal clump turbulence
at the current epoch. We often detect thermal SiO emission within these 70 _µ_ m dark clumps that
is unrelated to CO outflows. This SiO emission could be produced by collisions, intersection flows,
undetected protostars, or other motions.


_Keywords:_ Unified Astronomy Thesaurus concepts: Infrared dark clouds (787), Star forming regions
(1565), Star formation (1569), Massive stars (732), Protostars (1302), Interstellar medium
(847), Stellar winds (1636), Stellar jets (1607), Interstellar line emission (844), Protoclusters
(1297)


1. INTRODUCTION



Corresponding author: Shanghuo Li

[shanghuo.li@gmail.com;](mailto: shanghuo.li@gmail.com; jzwang@shao.ac.cn) jzwang@shao.ac.cn



Stars influence the dynamics of their natal clouds
through a variety of feedback by injecting mechanical and thermal/non-thermal energy back to the cloud

2 Li et al.



(Arce et al. 2007; Frank et al. 2014). The star formation feedback may affect the subsequent star formation,
for instance, through jet and outflow activities, injecting
mass, angular momentum, and kinetic energy into the
surrounding environment (e.g., Wang et al. 2010; Federrath et al. 2014; Frank et al. 2014; Bally 2016). Protostellar outflows can efficiently transfer excess angular
momentum from accretion disks to outer radii, which
enables sustained accretion from the envelope and/or
core to the disk that feeds the accreting protostar (Shu
et al. 1987; Hosokawa & Omukai 2009; Krumholz et al.
2009; Frank et al. 2014; Kuiper et al. 2016). On the
other hand, the high momentum outflow can sweep up
the material in the envelope, diminishing the potential
mass reservoir of protostars (Kuiper et al. 2010, 2011).
The outflow induced turbulence can help to replenish
the turbulence that counteracts the gravitational collapse/fragmentation (Li & Nakamura 2006; Offner &
Chaban 2017; Offner & Liu 2018), which reduces the
overall star formation efficiency.
Molecular outflows have been intensively studied in
both low- and high-mass star-forming regions using different molecular tracers, e.g., CO, SiO, HCN, HCO [+],
HNCO, CS, and so on (Zhang et al. 2001; Beuther et al.
2002; Zhang et al. 2005; Kim & Kurtz 2006; Arce et al.
2007; Qiu et al. 2008, 2009; Sanhueza et al. 2010, 2012;
Jim´enez-Serra et al. 2010; Csengeri et al. 2011; Wang
et al. 2011; Sakai et al. 2013; Leurini et al. 2013; Dunham et al. 2014; Duarte-Cabral et al. 2014; Stephens
et al. 2015; Beltr´an & de Wit 2016; Csengeri et al. 2016;
Li et al. 2017, 2019b,a; Qiu et al. 2019; Pillai et al. 2019;
Baug et al. 2020; Nony et al. 2020). Since outflows are a
natural consequence of accretion, studying the evolution
of outflows is critical for understanding the accretion
history, especially for the extremely early evolutionary
stages of star-forming regions (e.g., Li et al. 2019a). This
not only allows to reveal the accretion process over time,
but also to constrain the initial conditions of high-mass
star formation. Protostars have been observationally
shown to have highly variable gas accretion rather than
constant during formation in both low- and high-mass
stars (Qiu & Zhang 2009; Audard et al. 2014; Parks
et al. 2014; Caratti o Garatti et al. 2017; Hunter et al.
2017; Vorobyov et al. 2018). Typical burst intervals from
weeks up to 50 kyr have been found in light curves of
young stars (Scholz et al. 2013; Parks et al. 2014; Cody
& Hillenbrand 2018), which could be driven by instabilities in the circumstellar disk (Zhu et al. 2009; Vorobyov
& Basu 2010), dynamical interactions between inner objects (e.g., disk, companion and planet; Lodato & Clarke
2004), or inflowing gas streams within the larger scale
circumstellar disk (Alves et al. 2019).



Infall motions are frequently used to study accretion
processes in the relatively evolved stages of high-mass
star formation (e.g., Zhang & Ho 1997; Keto et al. 1988;
Beltr´an et al. 2006; Wyrowski et al. 2016), while it is difficult to directly measure the accretion process during
the earliest phase of high-mass star formation, when the
stellar embryos continue to accumulate the mass during this phase via accretion (e.g., Contreras et al. 2018).
Since outflows are accretion-driven (Pudritz & Norman
1983, 1986; Shu et al. 1991; Shang et al. 2007), they can
be used to study the accretion process. Even though
molecular outflows only provide indirect evidence of accretion, outflows are easily detectable and offer a fossil
record of the accretion history of protostars. However,
a systematic study of the outflows toward the extremely
early evolutionary phases (e.g., 70 _µ_ m dark clumps) of
star formation with a large sample remains scarce due
to the weak emission in such sources (Li et al. 2019a).
To investigate high-mass star formation in the cluster mode, we have carried out high-angular resolution
observations towards 12 massive 70 _µ_ m dark clumps using the Atacama Large Millimeter/submillimeter Array
(ALMA). The sample was selected by combining the ATLASGAL survey (Schuller et al. 2009; Contreras et al.
2013) and a series of studies from the MALT90 survey
(Foster et al. 2011, 2013; Jackson et al. 2013; Guzm´an
et al. 2015; Rathborne et al. 2016; Contreras et al. 2017;
Whitaker et al. 2017). The source selection is described
in detail in Sanhueza et al. (2019).
In this work, we focus on identifying molecular outflows and studying their properties in extremely early
evolutionary stages of high-mass star formation using
two molecular lines, CO _J_ = 2 _−_ 1 and SiO _J_ = 5 _−_ 4.
Clump fragmentation, based on the dust continuum
emission, is presented in Sanhueza et al. (2019). Core
dynamics will be presented in a companion paper (Y.
Contreras et al. 2020, in preparation).
The paper is organized as follows. The observations
are described in Section 2. In Section 3, we describe
the results and analysis. We discuss the identified outflows in detail in Section 4. Finally, we summarize the
conclusions in Section 5.


2. OBSERVATIONS


Observations of the 12 infrared dark clouds (IRDCs)
were performed with ALMA in Band 6 (224 GHz; 1.34
mm) using the main 12 m array, the Atacama Compact
7 m Array (ACA; Morita Array), and the total power
(TP; Project ID: 2015.1.01539.S; PI: Sanhueza).
Some sources were observed in different configurations
(see Table 2 in Sanhueza et al. 2019). The uv-taper was
used in those sources to obtain a similar synthesized

3



-19°27'15"


30"







0.0010


0.0008



45"























28'00"


15"







09s 08s 07s 06s 18h10m05s

RA (J2000)



0.0006


0.0004


0.0002


0.0000



09s 08s 07s 06s 18h10m05s

RA (J2000)



**Figure** **1.** ALMA 1.3 mm continuum, CO and SiO velocity integrated intensities images for G10.99. The gray images in both
panels show the 1.3 mm continuum emission. Dashed orange contour shows 20% of the sensitivity level of the mosaic in the
ALMA continuum image. The green stars indicate the identified dense cores. Left: ALMA 1.3 mm continuum image. The
contour levels are (-4, -3, 3, 4, 5, 7, 10, 14, 20) _×σ_, with _σ_ =0.115 mJy beam _[−]_ [1] . Right: The blue-shifted (blue contours) and
red-shifted (red contours) components of CO emission, and SiO velocity-integrated intensity (black contours, integration range
is between 7 and 39 km s _[−]_ [1] ) overlaid on the continuum emission. The blue and red contours levels are (4, 6, 9, 13, 18, 24,
31) _×σ_, where the _σ_ are 0.05 Jy beam _[−]_ [1] km s _[−]_ [1] and 0.03 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black
contours are (3, 4, 5, 6, 7, 8, 9) _×σ_, with _σ_ = 0.02 Jy beam _[−]_ [1] km s _[−]_ [1] . On the left side panel, black numbers correspond to the
name of all cores. On the right side panel, the green numbers indicate only the cores associated with molecular outflows. The
beam size of continuum image is shown on the bottom left of each panel. The complete figure set (7 images, see Figure 10) is
available in the online journal.



beam size of 1 _[′′]_ _._ 2 for each source (see also Sanhueza
et al. 2019). The primary beam sizes are 25 _[′′]_ _._ 2 and 44 _[′′]_ _._ 6
for the 12 m array and ACA at the center frequency of
224 GHz, respectively. We made two Nyquist-sampled
mosaics with the 12 m array (10-pointings) and ACA
(3-pointings), covering about 0.97 arcmin [2] within the
20% power point, except for the IRDC G028.273 _−_ 00.167
that was observed with 11 and 5-pointings. These mosaics were designed to cover a significant portion of the
clumps, as defined by single-dish continuum images. All
sources were observed with the same correlator setup.
Data calibration was performed using the CASA software package versions 4.5.3, 4.6, and 4.7, while imaging was carried out using CASA 5.4 (McMullin et al.
2007). Continuum images were obtained by averaging
line-free channels over the observed spectral windows
with a Briggs’s robust weighting of 0.5 of the visibilities. This achieved an average 1 _σ_ root mean square
(rms) noise level of _∼_ 0.1 mJy beam _[−]_ [1] . The beam size
for each clump is summarized in Table 1. For detected
molecular lines (N 2 D [+] 3-2, DCN 3-2, DCO [+] 3-2, CCD
3-2, [13] CS 5-4, SiO 5-4, C [18] O 2-1, CO 2-1, and H 2 CO 32, CH 3 OH 4-3), we used a Briggs’s robust weighting of



2.0 (natural weighting) for imaging. Using the feathering technique, the 12m and 7m array molecular line data
was combined with the TP data in order to recover the

missing flux. This yields a 1 _σ_ rms noise level of _∼_ 0.06
K per channel of 0.17 km s _[−]_ [1] for the first six lines and
_∼_ 0.02 K per channel of 1.3 km s _[−]_ [1] for the last four lines.


3. RESULTS AND ANALYSIS


Using the CO 2-1 and SiO 5-4 lines, we searched for
molecular outflows toward the 301 embedded dense cores
that have been revealed in the 1.3 mm continuum images
of the 12 IRDC clumps. Sanhueza et al. (2019) focused
on 294 cores, excluding 7 cores located at the edge of the
images (20%-30% power point). We have included these
7 cores in our analysis because some of them are associated with molecular outflows. CO was used as the primary outflow tracer, while SiO was used as a secondary
outflow tracer. Figure 1 shows an overview of the identified molecular outflows toward one clump. All images
shown in the paper use the 12 m array data only and
prior to primary beam correction, while all measured
fluxes are derived from the combined data (including 12

4 Li et al.


60



85


80


75


70


65


60


-20


-40


-60


-80



0.7


0.6


0.5


0.4


0.3


0.2


0.1


0.0


0.8


0.6



80


60


40


20


0


-20




|R0<br>R1|Col2|Col3|
|---|---|---|
|#2<br>G14.49|B0|B0|
|15<br>-10<br>-5<br>0<br>5|15<br>-10<br>-5<br>0<br>5|15<br>-10<br>-5<br>0<br>5|









0.7


0.6













0.5


0.4


0.3


0.2


0.1





-45


-50


-55


-60







0.4


0.3


0.2


0.1


0.0





-65


-70


|Col1|Col2|Col3|
|---|---|---|
|B1<br>#2<br>G340.23|B0|B0|



-10 -5 0 5 10 15 20


Position Offset ( [′′] )



0.4


0.2


-8 -6 -4 -2 0 2


Position Offset ( [′′] )





0.20


0.15


0.10


0.05


0.00



-5 0 5


Position Offset ( [′′] )



**Figure** **2.** Position-velocity (PV) diagram of the CO emission. The cut of the PV diagrams is along the CO outflows that are
indicated by the arrows in Figure 1. The name of the associated core and clump is displayed in each panel. The red crosses
mark the locations of the detected knots. The vertical and horizontal dashed fuchsia lines represent the position and velocity
of dense core, respectively. The contour levels are (-3, 3 to 30 by 2 steps) _×σ_, with _σ_ =40 mJy beam _[−]_ [1], for #1–G14.49. The
contour levels are (-5, 5, 7, 10, 14, 19, 25, 32, 40 to 100 by 10 steps) _×σ_, with _σ_ =5 mJy beam _[−]_ [1], for #2–G14.49. The contour
levels are (-5, 5 to 23 by 2 steps) _×σ_, with _σ_ =6 mJy beam _[−]_ [1], for #1–G28.23. The contour levels are (-5, 5 to 21 by 2 steps, and
25 to 80 by 5 steps) _×σ_, with _σ_ =4 mJy beam _[−]_ [1], for #3–G331.37. The contour levels are ( -5, 5 to 20 by 3 steps, and 30 to 180
by 20 steps) _×σ_, with _σ_ =4.5 mJy beam _[−]_ [1], for #2–G340.23. The contour levels are (-5, 5 to 20 by 3 steps, and 30 to 150 by 10
steps) _×σ_, with _σ_ =3 mJy beam _[−]_ [1], for #1–G341.03. The cut of the #1–G341.03 PV diagram is along the northwest-southeast
CO outflow.



m, 7 m, and TP) and corrected for the primary beam
attenuation.


3.1. _Outflow_ _Detection_


For the identification of outflows, we use the 12 m array data only. We follow the procedure described below
to identify CO outflows: (1) Using `DS9` [1], we inspect the
position-position-velocity (PPV) data cubes of the CO
emission to determine the velocity ranges of the blueand red-shifted components with respect to the cloud
emission. (2) These velocity ranges are used to generate
the velocity integrated intensity maps (moment-0) for
both blue- and red-shifted components, which in conjunction with the channel maps and the CO line profiles
are used to determine the direction of CO outflows. (3)
The position-velocity (PV) diagram, which is cut along


1 [https://sites.google.com/cfa.harvard.edu/saoimageds9](https://sites.google.com/cfa.harvard.edu/saoimageds9)



the identified CO outflow, combined with the channel
maps and line profiles are further used to carefully refine
the velocity range of each CO outflow to exclude the ambient gas from the cloud. However, in some cases (e.g.,
the outflows associated with core #3/#5/#6/#17/#32
in the G341.03 clump) the outflows cannot be well separated from nearby overlapping outflows or ambient gas
and those outflows were marked as “Marginal”. For
the outflows, that are unambiguously associated with a
dense core, and are unambiguously distinguishable from
nearby outflows and the ambient gas, were marked as
“Definitive”. Among the 43 identified outflows, 33 are
defined as definitive outflows, while the remaining are
classified as marginal (Table 2). The derived physical
parameters of the definitive outflows are more reliable
than those of the marginal outflows (Section 3.2).
The velocity range ( _△v_ ) of outflows are defined where
the emission avoid environment gas around the system
velocity and higher than the 2 _σ_ noise level, where _σ_ is

5



the rms noise level in the line-free channels. The outflow
lobes are defined where the corresponding velocity integrated intensity is higher than the 4 _σ_ noise level, where
_σ_ is the rms of the integrated intensity map. After defining outflows following the procedure, we use the 12 m, 7
m, and TP combined data to compute outflow parameters. Using the CO line, we have identified 43 molecular outflows toward 41 out of 301 dense cores (Table
2), with a detection rate of 14% (41/301). There are
2 cores associated with 2 molecular outflows. Among
these 41 cores, 28 are associated with SiO emission (detection rate of 9%). The relatively low detection rate of
SiO is likely due to the fact that the excitation energy
and critical density of the SiO 5-4 transition are much
higher than that of the CO 2-1 transition (e.g., Li et al.
2019a). There are three clumps (G332.96, G340.17 and
G340.22) without molecular outflows detected in the CO
or SiO line.

Sixteen outflows show bipolar morphology. In addition, we find a bipolar outflow without any association
with dense cores in G331.37 (Figure 1), which could
be due to the associated core mass below our detection
limit (e.g., Pillai et al. 2019). The remaining 27 outflows
present a unipolar morphology. The fraction of outflows
showing unipolar morphology is 63%, higher than the
fraction of 25% and 40% in W43-MM1 and in a sample
of protocluster (Baug et al. 2020; Nony et al. 2020), respectively. Based on the CO emission, we find that the
ambient gas is frequently found around the dense core.
Therefore, we might fail to identify some low-velocity
and/or weak outflows because their emission can be confused with the ambient gas. We cannot completely rule
out the possibility that this bias contributes to the high
fraction of unipolar outflows.
There are 2 cores, #2 of G327.11 (#2–G327.11) and
#1 of G341.03 (#1–G341.03), showing two bipolar morphology outflows in CO emission (see Figure 1). The
two bipolar outflows are approximately perpendicular
to each other in both #2–G327.11 and #1–G341.03,
which suggests that these cores encompass multiple protostars with accretion disks that are perpendicular to
each other. Alternatively, these two cores may be showing outflows with wide opening angles. However, we
favour the first scenario because wide angles are expected in much more evolved sources and those expected
in these IRDCs that properties are consistent with early
stages of evolution (Arce et al. 2007).
The velocity integrated intensity is integrated over
the entire velocity range of the identified red/blue line
wings. There are several exceptions because some foreground and/or background CO emission is found in
the velocity range of line wings (see Figure 2). Fig


16


14


12


10


8


6


4


2





0

|Col1|Col2|Col3|
|---|---|---|
||||


0 20 40 60 80 100

1
v max (km s )



12


10


8


6


4


2





0

|Col1|Col2|
|---|---|
|||


0.0 0.1 0.2 0.3 0.4 0.5



max [ (pc)]


**Figure** **3.** Upper and bottom panels show the distributions
of the maximum velocity ( _v_ max ) and maximum projected distance ( _λ_ max ) of the CO outflow, respectively. Red histogram
represents the red-shifted gas, while blue histogram represents the blue-shifted gas. The blue and red dashed lines
indicate the median value of blue-shifted and red-shifted, respectively.


ure 1 shows the CO velocity integrated intensity map
for each clump. The directions of molecular outflows
are indicated by arrows. There are 3 weak CO outflows
(#4–G327.11, #1–G341.03 and #2–G341.03), identified
through PV-diagrams and channel maps. The emission
from these weak outflows is much smaller than the velocity ranges used in the figures (Figure 1), resulting in
a dilution of the signal making the weak outflows not
visible in the figures.
The core systemic velocity is determined by the centroid velocity, _v_ lsr, of the N 2 D [+] 3-2 line, while the DCO [+]

3-2 line is used when the N 2 D [+] line is undetected. The

6 Li et al.



14


12


10


8


6


4


2


0


10


8


6


4


2



10


8


6


4


2





12


10


8


6


4


2







100 3 10 2 10 1 10 [0] 10 [1]

P out (M km s 1 )



10 3 10 2 10 1 10 [0]
M out (M )



0

10 [3] 10 [4]
t dyn (yr)





12


10


8


6


4


2



12


10


8


6


4


2







0

10 [41] 10 [42] 10 [43] 10 [44] 10 [45]
E out (erg)


14



100 7 10 6 10 5 10 4

M out (M yr 1 )



010 7 10 6 10 5 10 4 10 3

F out (M km s 1 yr 1 )







10 9 10 8 10 7 10 6 10 5

M acc (M yr 1 )





10 4 10 3 10 2 10 1 10 [0]
M out /M core



12


10


8


6


4


2


0



10 [30] 10 [31] 10 [32] 10 [33] 10 [34]

L out (erg s 1 )



17.5


15.0


12.5


10.0


7.5


5.0


2.5


0.0



12


10


8


6


4


2


0



**Figure** **4.** Panel (a) to (i) shows the distributions of total outflow mass ( _M_ out ), outflow dynamical timescale ( _t_ dyn ), outflow
momentum ( _P_ out ), outflow energy ( _E_ out ), outflow rate ( _M_ [˙] out ), mechanical force( _F_ out ), outflow luminosity ( _L_ out ), accretion rate
( _M_ [˙] acc ), and ratio ( _M_ out _/M_ core ) of outflow mass to core mass, respectively. The black dashed lines indicate the median value of
each parameter.



C [18] O 2-1 line is used when both the N 2 D [+] and DCO [+]


lines are undetected. The maximum detected velocities (e.g., _v_ max(r) = max( _v_ r ), where _v_ r = _|v_ CO _−_ _v_ lsr _|_
is a variable representing the red-shifted outflow velocity with respect to the core systemic velocity) of the
CO red- and blue-shifted lobes with respect to the core
systemic velocity range from 9 to up to 95 km s _[−]_ [1] . Figure 3 shows the distributions of _v_ max for the detected
outflow lobes. The mean and median of _v_ max are 28 and
21 km s _[−]_ [1], respectively. There are 9 cores associated
with a CO outflow with line wings at velocities greater
than 30 km s _[−]_ [1] ( _v_ max _>_ 30) with respect to the core systemic velocity. The maximum lengths of the CO outflow
red-/blue-shifted lobes projected on the plane of the sky



( _λ_ max ) are in the range of 0.04 and 0.45 pc (Figure 3),
with the mean and median values of 0.25 and 0.23 pc,
respectively. Note that both _v_ max and _λ_ max estimated
here should be considered as lower limits because the

outflow emission is limited by the sensitivity of the observations, can be confused by nearby outflows and/or
line-of-sight emission that is not associated with the natal cloud, and these parameters have not been corrected
for the outflow inclination.


3.2. _Outflow_ _Parameters_


Since the SiO abundances vary significantly from region to region and its emission is much weaker than the
CO, we used the CO data to compute the outflow pa

rameters by assuming that the CO line wing emission
is optically thin. Following the approach delineated in
Li et al. (2019a) (see Appendix A), we estimated the
main physical parameters of each outflow, including the
mass ( _M_ out ), momentum ( _P_ out ), energy ( _E_ out ), dynamical timescale ( _t_ dyn ), outflow rate ( _M_ [˙] out ), outflow energy
rate (also known as outflow luminosity, _L_ out ) and mechanical force ( _F_ out ). The calculation of these outflow
parameters is summarized in Appendix A.
The outflow masses range from 0.001 to 0.32 _M_ _⊙_, with
a mean mass of 0.044 _M_ _⊙_ (Figure 4 and Table 2). We
compare the outflow mass to the core mass, and find
that the outflow mass is smaller than 10% of the core
mass (Figure 4), except for #13-G341.03 outflows, with
a mass of 22% of the core mass. This is owing to the outflow of #13-G341.03 is significantly contaminated by the
nearby outflow driven by the #3–G341.03 (see Figure 1).
The estimated outflow dynamical timescales range from
0.1 _×_ 10 [4] to 3.2 _×_ 10 [4] yr. We used the outflow mass
and dynamical time to estimate the outflow ejection
rates, which are between 2.4 _×_ 10 _[−]_ [7] and 5.0 _×_ 10 _[−]_ [5]

_M_ _⊙_ yr _[−]_ [1] . The outflow momenta range from 0.2 _×_ 10 _[−]_ [2]

to 3.4 _M_ _⊙_ km s _[−]_ [1] . The outflow energies are between 0.4
_×_ 10 [42] and 1.2 _×_ 10 [45] erg. The outflow luminosity can
be estimated by dividing the outflow energy by the outflow dynamical timescale, _L_ out = _E_ out _/t_ dyn, which are
in the range of 0.2 _×_ 10 [31] and 2.1 _×_ 10 [34] erg s _[−]_ [1] . The
outflow mechanical force is computed using the outflow
momentum and dynamical timescale, _F_ out = _P_ out _/t_ dyn,
which is between 0.3 _×_ 10 _[−]_ [6] and 9.8 _×_ 10 _[−]_ [4] _M_ _⊙_ km
s _[−]_ [1] yr _[−]_ [1] .
Assuming that: (1) the outflows are driven by protostellar winds from accretion disks (e.g., Keto 2003; McKee & Tan 2003); (2) the wind and molecular gas interface is efficiently mixed (Richer et al. 2000); (3) the momentum is conserved between the wind and the outflow,
with no loss of momentum to the surrounding cloud, one
can estimate the accretion rate, _M_ [˙] acc = _k_ _M_ [˙] w, using the
mass-loss rate ( _M_ [˙] w ) of the wind that is inferred from the˙
associated outflow mechanical˙ ˙ force, _M_ w _v_ w = _F_ out . We
assume a ratio of _k_ = _M_ acc _/M_ w = 3 between the mass
accretion rate and the mass ejection rate (Tomisaka
1998; Shu et al. 2000). The wind velocity _v_ w is adopted
to be 500 km s _[−]_ [1], which ranges from a few km s _[−]_ [1]

to over 1000 km s _[−]_ [1] in young stellar objects (YSOs;
Bally 2016). The derived accretion rate ranges from 2.0
_×_ 10 _[−]_ [9] to 3.8 _×_ 10 _[−]_ [6] _M_ _⊙_ yr _[−]_ [1], with a mean value of
4.9 _×_ 10 _[−]_ [7] _M_ _⊙_ yr _[−]_ [1] . These values are much smaller
than the predicted accretion rate (order 10 _[−]_ [4] _−_ 10 _[−]_ [3]

_M_ _⊙_ yr _[−]_ [1] ) in some high-mass star formation models
(e.g., McKee & Tan 2003; Wang et al. 2010). See discussions of accretion rate below in Section 4.2.1.



7


Since the inclination angle of the outflow axes is not
known, the outflow parameters and accretion rate have
not been corrected for their inclination for all of out
flows. The estimated outflow parameters of each outflow
are summarized in Table 2 and Figure 4.


3.3. _Outflow-driven_ _turbulence_


Stars generate vigorous outflows during their formation process. These outflows transfer not only mass but
also energy into their parent molecular cloud. Therefore,
outflow feedback is considered one of the mechanisms to
replenish the internal turbulence (Li & Nakamura 2006;
Graves et al. 2010; Arce et al. 2010; Nakamura et al.
2011a; Krumholz et al. 2014; Nakamura & Li 2014; Li
et al. 2015; Offner & Chaban 2017). To assess whether
the outflow-induced turbulence can play a significant
role in replenishing the internal turbulence for the extremely early phase of high-mass star formation, we estimate the ratio of the outflow energy rate ( _L_ out ) to turbulent energy dissipation rate ( _E_ [˙] turb ), _r_ _L_ = _L_ out _/E_ [˙] turb .
The turbulent energy ( _E_ turb ) is given by



Here, the _△v_ chan and _△v_ FWHM are the channel width
and the full width at the half maximum (FWHM) of the
line emission, respectively. Using the physical properties
of the clumps (Table 1), we obtained the turbulent energies ranging from 5.4 _×_ 10 [45] to 4.4 _×_ 10 [47] erg (Table 3).
The turbulent dissipation rate ( _E_ [˙] turb ) can be calculated as (McKee & Ostriker 2007)


˙
_E_ turb = _[E]_ [turb] _,_ (3)

_t_ diss


where dissipation time, _t_ diss, has two different definitions
based on numerical simulations. In the first approach,
the turbulent dissipation time of the cloud is given by
(e.g., McKee & Ostriker 2007)


_t_ diss _∼_ 0 _._ 5 _[R]_ [cl] _,_ (4)

_σ_ 1D


where _R_ cl is the cloud radius. The obtained turbulent dissipation times are between 5.8 _×_ 10 [4] and
3.6 _×_ 10 [5] yr, yielding turbulent dissipation rates of
(0 _._ 5 _−_ 114 _._ 7) _×_ 10 [33] erg s _[−]_ [1] (Table 3). The obtained _t_ diss
is comparable to the estimated value of a few 10 [5] yr in
the Perseus region (Arce et al. 2010), while is smaller



_E_ turb = [1] _√_

2 _[M]_ [(]



3 _σ_ los _,_ 1D ) [2] _,_ (1)



where _σ_ los _,_ 1D is the one-dimensional velocity dispersion
along the line of sight, which is



_σ_ los _,_ 1D =



� _△v_ FWHM [2] _[−△][v]_ chan [2]

_,_ (2)

2 ~~_√_~~ 2 ln 2

8 Li et al.



than the reported value of 1.6 _×_ 10 [7] yr in the Taurus molecular cloud (Li et al. 2015). The _r_ _L_ lies in the
range of 0.004–4.05, with a median value of 0.08 (Table
3). The range of values is much lower than those found
in relatively evolved star forming-regions, for instance,
0.8 _−_ 12.4 in Perseus, 2 _−_ 7 in _ρ_ Ophiuchi, 0.6 _−_ 3 in Serpens South (Arce et al. 2010; Nakamura et al. 2011b;
Plunkett et al. 2015a).
In the second approach, the turbulent dissipation time
can be defined as (e.g., Mac Low 1999)


_κ_
_t_ diss _∼_ 3 _._ 9 _t_ ff _,_ (5)
_M_ rms


where _M_ rms = _v_ los _,_ 3D _/c_ s = _√_ 3 _v_ los _,_ 1D _/c_ s is the Mach

number of the turbulence, _t_ ff = �3 _π/_ 32 _Gρ_ is the freefall timescale, _κ_ = _λ_ _d_ _/λ_ _J_ is the ratio of the driving wavelength ( _λ_ _d_ ) to the Jeans wavelength ( _λ_ _J_ = _c_ s ( _π/Gρ_ ) [1] _[/]_ [2] ).
The average volume density of a clump is calculated
by _ρ_ = 3 _M_ cl _/_ 4 _πR_ cl [3] [.] For a continuous outflow, the
outflow lobe length can be used to approximate the
turbulence driving wavelength according to numerical
simulations (Nakamura & Li 2007; Cunningham et al.
2009). The estimated _t_ diss ranges from 1.3 _×_ 10 [4] to
1.5 _×_ 10 [5] yr, resulting in turbulent dissipation rates of
(3 _._ 8 _−_ 109 _._ 5) _×_ 10 [33] erg s _[−]_ [1] (Table 3). Using the derived _E_ [˙] turb, we find that the _r_ _L_ is between 0.001 and
0.54, with a median value of 0.02.


4. DISCUSSION


4.1. _Biases_ _on_ _Outflow_ _Parameters_


CO is the most frequently used tracer for studying
molecular outflows driven by protostars. Note that the
outflow parameters estimated from the CO line emission are only a lower limit considering the observational
biases: (1) CO fails to trace the outflow in low-density
regions, which can be traced by other low-density gas
tracers (e.g., Hi 21 cm and Cii 157 _µ_ m lines); (2) optical
depth effects on the outflow parameters; (3) the limited
sensitivity of our observations. On average, the combined effects of the above mentioned biases could lead
to a factor of _∼_ 10 underestimate in the outflow mass
and dynamical properties (Dunham et al. 2014). On
the other hand, the unknown inclinations of the outflow
axis with respect to the line of sight can also introduce
an uncertainty on the outflow parameters estimations
(Dunham et al. 2014; Li et al. 2019a). Assuming all orientations have equal probability from parallel ( _θ_ = 0 _[◦]_ )
to perpendicular ( _θ_ = 90 _[◦]_ ) to the line of sight, one can
compute an mean inclination angle _⟨θ⟩≈_ 57 _[◦]_ _._ 3. For the
mean inclination angle, the correction factors are 1.9 for
_v_ and out ; 1.71.2 forfor _λM_ ˙ outout ; 0.6(see,forDunham _t_ dyn ; 1.9 etforal. _P_ out 2014; 3.4; Lifor et _E_ out al.;
2019a).



4.2. _Outflow_ _Properties_


To study the relationship between the outflow properties and their associated dense cores, we have compared core masses and outflow parameters, including
the outflow dynamical timescale, outflow maximum velocity, outflow projected distance, outflow mass, outflow
momentum, outflow energy, outflow rate, outflow luminosity, and mechanical force. There are no clear correlations between core masses and outflow parameters, with
the exception of outflow dynamical timescale, which appears to show a positive correlation with the core mass.
In Section 4.2.1, we discuss the accretion rate and outflow mechanical force. Then, we discuss the relationship
between the outflow dynamical timescale and the core
mass in Section 4.2.2. The discussion of emission knots

in the molecular outflows is presented in Section 4.2.3.


4.2.1. _Accretion_ _Rate_ _and_ _Outflow_ _Mechanical_ _Force_


Using the CO outflows, the estimated protostellar accretion rates are between 2.0 _×_ 10 _[−]_ [9] to
3.8 _×_ 10 _[−]_ [6] _M_ _⊙_ yr _[−]_ [1], with a mean value of 4.9
_×_ 10 _[−]_ [7] _M_ _⊙_ yr _[−]_ [1] . These values are comparable to those
derived toward other 70 _µ_ m and 24 _µ_ m dark massive
cores (Lu et al. 2015; Zhang et al. 2015; Li et al. 2019a)
and some low/intermediate-mass cores (van Kempen
et al. 2016; Feddersen et al. 2020b) following the same
approach, while they are much smaller than the typical
value of a few _×_ (10 _[−]_ [5] _−_ 10 _[−]_ [4] ) _M_ _⊙_ yr _[−]_ [1] reported in much
more evolved massive cores (e.g., 24 _µ_ m bright cores,
4.5 _µ_ m bright cores and UCHII regions, Qiu & Zhang
2009; Qiu et al. 2009; L´opez-Sepulcre et al. 2010; DuarteCabral et al. 2013; Liu et al. 2017; Lu et al. 2018). This
indicates that the accretion rates likely increase with the
evolution of star formation.
The bolometric luminosity-to-mass ratio ( _L/M_ ) is believed to be a indicator of the evolutionary phase of star
formation. The early evolutionary phase correspond to a
low _L/M_ value, while later stages correspond to higher
values of _L/M_ (Molinari et al. 2008). Figure 5 shows
the luminosity-to-mass ratio ( _L_ bol _/M_ clump ) versus the
total outflow mechanical forces ( _F_ out _,_ tot ), for our 70 _µ_ m
dark clumps, together with high-mass clumps from Yang
et al. (2018). In the latter clumps, the observations have
an angular resolution of 15 _[′′]_ (Yang et al. 2018), which
should not be able to spatially resolve the outflows for
the embedded cores. Thus, we added the outflow parameters (i.e., mechanical force _F_ out _,_ tot = [�] _F_ out and
accretion rate _M_ [˙] acc _,_ tot = [�] _M_ [˙] acc ) for each core within a
clump for our 70 _µ_ m dark sources. The bolometric luminosities of our clumps are estimated with the procedure
introduced by Contreras et al. (2017) (see their Equation 3). The _L_ bol _/M_ clump and _F_ out _,_ tot shows a strong

9



|Col1|Yang2018 log(Macc, tot) = 0 .8log(Lbol/Mclump)-5 .8<br>70 mdark|Col3|Col4|Col5|
|---|---|---|---|---|
||log(Macc, tot) = 0.8log(Lbol/Mclump)-5.8<br>Yang2018<br>70 m dark||||
|7<br><br>6<br><br>5<br><br>4<br><br>|r=0.67|||16<br>1.4<br>1.2<br>1.0<br>0.8<br>0.6<br>0.4<br>satial resolution [lo10(|
|7<br><br>6<br><br>5<br><br>4<br><br>|r=0.67||||
|7<br><br>6<br><br>5<br><br>4<br><br>|r=0.67||||
|7<br><br>6<br><br>5<br><br>4<br><br>|r=0.67||||
|7<br><br>6<br><br>5<br><br>4<br><br>|r=0.67||||
|7<br><br>6<br><br>5<br><br>4<br><br>|r=0.67||||
|7<br><br>6<br><br>5<br><br>4<br><br>|||||


10 1 10 [0] 10 [1] 10 [2] 10 [3]
L bol /M clump (L /M )



10 6



|Col1|Yang2018 log(Fout, tot) = 0 .8log(Lbol/Mclump)-3 .6<br>70 mdark|Col3|Col4|Col5|
|---|---|---|---|---|
||log(Fout, tot) = 0.8log(Lbol/Mclump)-3.6<br>Yang2018<br>70 m dark||||
|5<br><br>4<br><br>3<br><br>2<br><br>1|r=0.66|||16<br>1.4<br>1.2<br>1.0<br>0.8<br>0.6<br>0.4<br>spatial resolution [log10(pc|
|5<br><br>4<br><br>3<br><br>2<br><br>1|r=0.66||||
|5<br><br>4<br><br>3<br><br>2<br><br>1|r=0.66||||
|5<br><br>4<br><br>3<br><br>2<br><br>1|r=0.66||||
|5<br><br>4<br><br>3<br><br>2<br><br>1|r=0.66||||
|5<br><br>4<br><br>3<br><br>2<br><br>1|r=0.66||||
|5<br><br>4<br><br>3<br><br>2<br><br>1|r=0.66||||
|5<br><br>4<br><br>3<br><br>2<br><br>1|||||


10 1 10 [0] 10 [1] 10 [2] 10 [3]
L bol /M clump (L /M )





10 2


10 3


10 4


10 5


10 6


10 7


10 8





**Figure** **5.** Left: plot of the _L_ bol _/M_ clump against the _F_ out _,_ tot . The correlation coefficient is 0.66 between _L_ bol _/M_ clump and _F_ out _,_ tot
in the Spearman-rank correlation test. The solid black line is the least-squares fitting result log( _F_ out _,_ tot ) = 0 _._ 8log( _L_ bol _/M_ clump ˙ ) _−_
3There _._ 6 (seeisalsoa strongYangcorrelationet al. 2018).betweenThe colorbar _L_ bol _/M_ indicates clump andthe _M_ ˙ acc spatial _,_ tot withresolution.a correlationRight:coefficientplot of theof _L_ 0.67. bol _/M_ The clump solidversusblacktheline _M_ acc is _,_ the tot .
best least-squares fitting result log( _M_ [˙] acc _,_ tot ) = 0 _._ 8log( _L_ bol _/M_ clump ) _−_ 5 _._ 8. The colorbar indicates the spatial resolution.



positive correlation, over nearly _∼_ 4 order of magnitude
in _L_ bol _/M_ clump and _∼_ 5 order of magnitude in _F_ out _,_ tot
(see also, Yang et al. 2018). The correlation coefficient
is 0.66 with a p-value of 2 _×_ 10 _[−]_ [22] in a Spearman-rank
correlation test, which assess monotonic relationships.
This indicates that outflow forces increase with protostellar evolution in the high-mass regime. The outflow
forces in our clumps are relatively lower compared to
other high-mass clumps in Yang et al. (2018), which is
likely due to a later evolutionary stage as evidenced by
the high _L_ bol _/M_ clump value.
As mentioned in Section 3.2, we can estimate the accretionwind velocityrate usingof 500thekmoutflows _[−]_ [1] andforce.a _M_ Here,˙ acc _/M_ we˙ w adoptof 3 fora
all the clumps in Yang et al. (2018). Figure 5 shows a
strong positive correlation between the total accretion
rate ( _M_ [˙] acc _,_ tot ) and _L_ bol _/M_ clump . The Spearman-rank
correlation test returns a correlation coefficient of 0.67
with a p-value of 3 _×_ 10 _[−]_ [2] . This strong correlation suggests that the accretion rates indeed increase with the
evolution of star formation.

For the dense cores detected CO outflows, the estimated accretion rates (a few 10 _[−]_ [7] _M_ _⊙_ yr _[−]_ [1] ) are _∼_ 3 orders of magnitude lower than the predicted values of
high-mass star formation models (McKee & Tan 2003;
Wang et al. 2010; Kuiper et al. 2016). The computed
accretion rates might be increased by a factor of _∼_ 2 orders of magnitude in the most extreme cases that have
the highest ratios of accretion to ejection rates, which
varies from 1.4 to even 100 in different observational and
theoretical studies (e.g., Sheikhnezami et al. 2012; Ellerbroek et al. 2013; Frank et al. 2014; Kuiper et al. 2016).
Assuming a constant ratio of the accretion to mass ejec














10 1 10 [0] 10 [1]

|Col1|G10.99 G28.23 G331.37 G340.23 G343.48<br>G14.49 G327.11 G337.54 G341.03|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||
|||||||||||||
|04||||||||||||
|04||||||||||||
|04||||||||||||
|04||||||||||||
|04||||||||||||
|04||||||||||||
|04||||||||||||
|04||||||||||||
|04||||||||||||
|04|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|1<br>0<br>1|

M core (M )


**Figure 6.** Core mass versus the outflow dynamical timescale
for all cores associated to CO outflows. The Spearman-rank
correlation test returns a correlation with a coefficient of
0.51. The solid red line is the best least-squares fitting result with log( _t_ dyn ) = 0 _._ 32log( _M_ core )+3 _._ 74. The error bars of
_M_ core correspond to its uncertainty of 50% (Sanhueza et al.
2017, 2019). The error bars of _t_ dyn correspond to the mean
inclination angle ( _⟨θ⟩≈_ 57 _[◦]_ _._ 3) correction.


tion rate, we found that the estimated accretion rates
of these protostars are indeed significantly lower than
the predicted values in the theoretical studies, even after accounting for the effects of opacity and inclination
angle.


4.2.2. _Outflow_ _Dynamical_ _Timescale_

10 Li et al.



Figure 6 shows the relation between the outflow dynamical timescale ( _t_ dyn ) and the core mass ( _M_ core ). We
have removed marginal outflows in this plot to eliminate the effect of the ambiguous outflows. Consistent
with what Li et al. (2019a) found for a sample of 70 _µ_ m
dark clumps, the outflow dynamical timescale increases
with the core mass. The correlation coefficient is 0.51
with a p-value of 2 _×_ 10 _[−]_ [3] in a Spearman-rank correla
tion test. This indicates a moderate correlation between

the outflow dynamical timescale and the core mass. The
_t_ dyn _−_ _M_ core relation suggests that more massive cores
tend to have a longer outflow dynamical timescale than
less massive cores. Since outflows are a natural consequence of accretion, the positive relation between _t_ dyn
and _M_ core suggests that the more massive cores have
a longer accretion history than less massive ones in a
protocluster. Note that the measurement of outflow dynamical timescales is affected by observational effects
such as the unknown inclination angle of the outflow
axes. The positive correlation between _t_ dyn and _M_ core
persists unless the inclination angles of the outflows are
close to 0 _[◦]_ or 90 _[◦]_ (see Figure 6).


4.2.3. _Episodic_ _Ejection_


From Figure 1, we find that 6 out of 43 molecular outflows show a series of knots in the integrated intensity
map. Figure 2 presents their PV diagrams along the axis
of outflows. The Hubble Law and Hubble Wedge features are clearly seen in the PV diagram of some outflows
(Lada & Fich 1996; Arce & Goodman 2001). Episodic
variation of, e.g., mass-loss rate and flow velocity, in a
protostellar ejection can produce internal shocks. This
mechanism has been proposed to produce emission knots
(which correspond to the Hubble Wedge in the PV diagram) in molecular outflows (Arce & Goodman 2001;
Arce et al. 2007; Vorobyov et al. 2018; Cheng et al.
2019; Rohde et al. 2019). Since the accretion is episodic,
the outflow as a natural consequence of the accretion is
episodic as well (Kuiper et al. 2015; Bally 2016; Cesaroni
et al. 2018). The Hubble Wedge features are found to be
independent of the core mass, associated with both lowmass and high-mass cores (see Figures 1 and 2). This
suggests that episodic accretion-driven outflows begin in
the earliest phase of protostellar evolution for low-mass,
intermediate-mass, and high-mass protostellar cores in
a protocluster.
In Section 3.2 (Appendix A), we used the maximum
velocity and the projected distance of the CO outflows
to estimate the outflow dynamical timescale, _t_ dyn =
_λ_ out _/v_ max . Similarly, we can estimate the dynamical
timescale of the identified knots using their projected
distance ( _λ_ knot ) and corresponding velocity ( _v_ knot ) with



7


6


5


4


3


2


1


0



3 4
10 10





t knot (yr)


**Figure** **7.** The distribution of knots dynamical timescales
estimated by _v_ knot and _v_ lobe .


respect to the associated core, _t_ knot = _λ_ knot _/v_ knot . From
Figure 2, one notes that the knots have different velocities. Therefore, we use _v_ knot, instead of the mean
velocity of detected knots ( _v_ lobe = _⟨v_ knot _⟩_ ) as used in
Nony et al. (2020), when calculating the knot dynamical timescale.

We visually follow contours in the PV-diagram to define the velocity and the projected distance of detected
knots (see Figure 2). The locations of knots in each outflow are presented in Figure 2. The mean _v_ knot for all
knots is 22 km s _[−]_ [1], ranging from 10 to 60 km s _[−]_ [1] . The
_λ_ knot are between 0.02 and 0.39 pc, with a mean value
of 0.15 pc. Uncertainties are conservatively estimated
as 2 km s _[−]_ [1] for velocities (3 times of channel width),
and 0 _[′′]_ _._ 5 for lengths (about half of angular resolution).
The estimated dynamical timescales of knot range from
6 _×_ 10 [2] to 2.5 _×_ 10 [4] yr, with the mean and median value
of 8.6 _×_ 10 [3] and 6.6 _×_ 10 [3] yr, respectively (see Table 4).
These values are higher than the value of 100 _−_ 6000 yr
found for low-mass YSOs (e.g., Santiago-Garc´ıa et al.
2009; Plunkett et al. 2015b), but comparable to the
value of 400 _−_ 10 [4] yr for high-mass YSOs (e.g., W43MM1; Nony et al. 2020) and the predicted timescale of
a few _×_ (10 [3] _−_ 10 [4] ) yr in the model of Vorobyov et al.
(2018).
To study the time span between consecutive ejection
events, we compute the timescale difference between
knots, _△t_ knot = _t_ knot _,i_ +1 - _t_ knot _,i_, which ranges from 3.6
_×_ 10 [2] to 7.2 _×_ 10 [3] yr, with a mean value of 4.4 _×_ 10 [3]

yr. The derived _△t_ knot is much larger than the reported
value of _∼_ 500 yr for W43-MM1 (Nony et al. 2020), even
accounting for the typical projection correction and the
typical measured uncertainty.
By comparing the knots timescales estimated by _v_ knot
and _v_ lobe, we find that the two results agree very well

11



with each other (see Figure 7). This suggests that the
different knot timescales between these studies are not
due to the use of two different methods. The different

_△t_ knot could be due to the different period of episodic
ejection between two samples, considering that they are
significantly different in the evolutionary stages. Our
70 _µ_ m dark cores are in a much earlier stage than those
infrared bright cores in W43-MM1 (Nony et al. 2020).
If this scenario is correct, the discrepancy likely implies
that the ejection episodicity timescale is not constant
over time and accretion bursts may be more often at
later stages of evolution.
The consecutive Hubble Wedge features seen in the
PV diagram are not necessarily successive in time for
the evolved objects in a very clustered environment.
This is because they have had enough time to experience numerous repeated ejection events. Therefore,
they can create a series in time with nonconsecutive
Hubble Wedge features. In this IRDC study, the detected outflows are still in an extremely early phase of
protostellar evolution, thus the outflows likely trace the
early accretion activities. This could be another possibility to cause the different _△t_ knot between different
evolutionary stages of star formation. The observations
of W43-MM1 by Nony et al. (2020) have a spatial resolution of _∼_ 2400 AU, which is higher than our observations ( _∼_ 4000–7500 AU). Given the different spatial resolutions between the two studies, we cannot fully rule
out the possibility that the different _△t_ knot is due to the
effect of spatial resolutions as higher spatial resolutions
help to resolve more individual knots. All these possibilities can be tested with the high spatial resolution
observations of a larger sample of dense cores encompassing different evolutionary stages of star formation.


4.3. _Outflow_ _Impact_ _on_ _the_ _Clumps_


The mechanical energy in outflows is found to be comparable to the turbulent energy in the more evolved
sources of both low- and high-mass star formation (eg.,
Beuther et al. 2002; Zhang et al. 2005; Arce et al.
2010; Nakamura & Li 2014). In addition, the outflowinduced turbulence can sustain the internal turbulence
(Arce et al. 2010; Nakamura & Li 2014; Li et al. 2015).
In contrast, we find that the total outflow energy (2.7
_×_ 10 [42] _−_ 2 _._ 1 _×_ 10 [45] erg) in the sample is significantly
lower than the turbulent energy (3.1 _×_ 10 [45] _−_ 4 _._ 2 _×_ 10 [47]

erg). This indicates that outflows do not have the energy for driving the turbulence in these clumps at the
current epoch. In addition, the total outflow ejected
mass occupies only a tiny fraction of the clump mass,
with a ratio of 6 _×_ 10 _[−]_ [6] – 3 _×_ 10 _[−]_ [4] (see Table 3).









**Figure** **8.** The turbulent dissipation rate versus the outflow
luminosity. The filled circles and filled stars represent the
turbulent dissipation rate computed by the first (Equation
4) and second (Equation 5) approaches, respectively.


Figure 8 shows the outflow luminosity versus the turbulent dissipation rate. As mentioned in Section 3.3,
we compute the turbulent dissipation time ( _t_ diss ) using
two different approaches. The determined _t_ diss using
the first approach (Equation 4) is larger than that of
the second approach (Equation 5). The latter is depending on the length of outflows, which may introduce
uncertainties in the estimation of _t_ diss . Overall, the results from both approaches are consistent (Figure 8 and
Table 3), the outflow luminosity is much smaller than
the turbulent dissipation rate in the majority of clumps,
except for G327.11 and G341.03, which have relatively
larger _r_ L . The computed _r_ L is smaller as compared to
the values found in other works for more evolved sources
(e.g., Arce et al. 2010; Nakamura et al. 2011b; Plunkett
et al. 2015a). This indicates that the outflow-induced
turbulence produced by these early stage cores is not
yet severely affecting the internal clump turbulence.
From Table 3, we note that the G327.11 has the narrowest line width and the lowest mass, resulting in the
lowest turbulent energy and the lowest turbulent dissipation rate among the sample. This seems to be the reason
why G327.11 can have the outflow-induced turbulence
required for replenishing the clump turbulence. G341.03
is another exception with sufficient outflow-induced turbulence to maintain the clump turbulence. Using the
CO line emission, we find that it has the highest outflow detection rate (27%) and has the largest outflow
luminosity among the whole IRDC sample. This implies
that outflows can become a major source of turbulence

12 Li et al.









|(b)<br>(j)<br>( )<br>a<br>(i)<br>(h)<br>( )<br>g<br>(f)|Col2|(b)|
|---|---|---|
|**(a)**<br>**(b)**<br>**(f)**<br>**(g)**<br>**(h)**<br>**(i)**<br>**(j)**|||
||||


**Figure** **9.** Panel a: SiO velocity-integrated intensity (black contours, integration range is between 7 and 39 km s _[−]_ [1] ) overlaid
on the continuum emission of G10.09. The contours are (-4, -3, 3, 4, 5, 6, 7, 8, 9) _×σ_, with _σ_ = 0.02 Jy beam _[−]_ [1] km s _[−]_ [1] . Green
stars indicate the dense cores revealed by dust continuum. The continuum beam size is plotted at the bottom-left corner. The
cyan dashed lines indicate the PV cuts path (panel j and k). Panel b-i: spectra of SiO 5-4 (orange and black) and CO 3-2 (blue)
toward several positions across the G10.99. Panel b, c, f and i show the SiO (orange) and CO profiles toward the regions where
SiO emission appear to neither associated with outflows nor dense cores. The black vertical dashed line is the clump velocity.
Panel j: PV diagram of the CO (color-scale and black contours) and SiO (white contours) emission across the SiO contours
(cyan dashed lines). The white contours are (3, 4, 5, 6) _×σ_, with _σ_ = 0.008 Jy beam _[−]_ [1] . The black contours are (7, 14, 21, 28
...) _×σ_, with _σ_ = 0.004 Jy beam _[−]_ [1] . The white dashed lines indicate the peak positions of SiO contours.



in the clumps when the majority of the embedded cores
evolve to launch strong molecular outflows.
Strong outflows generated by young stars have a disruptive impact on their natal clouds. Similarly, the outflow energy ( _E_ out ) can be compared to the gravitational
binding energy of clouds, _E_ grav = _GM_ cl [2] _[/R]_ [cl] [,] [for] [evalu-]
ating the potential disruptive effects of outflows on their
clouds. The gravitational energy of clouds ranges from
7.4 _×_ 10 [46] to 5.3 _×_ 10 [48] erg, which is much larger than
the total outflow energy for each clump. The ratio of
_E_ out _/E_ grav is between 2 _×_ 10 _[−]_ [5] and 8 _×_ 10 _[−]_ [3], which
indicates that the disruptive impact of these outflows



on their parent clouds is, for now, negligible for all the
clump sample. This is because these clumps are still
in extremely early evolutionary stages of star formation
and have not yet been severely affected by protostellar
feedback (consistent with being 24 and 70 _µ_ m dark).
Therefore, these clumps are ideal objects for studying
the initial conditions of high-mass star and cluster for
mation.


4.4. _SiO_ _Emission_ _Unrelated_ _to_ _CO_ _Outflows_


SiO has been widely used to trace shocked gas, such
as those associated with protostellar outflows and jets

(Zhang et al. 1999, 2000; Hirano et al. 2006; Palau et al.
2006; Codella et al. 2013; Leurini et al. 2014; Li et al.
2019b,a). This is because the SiO formation is closely
linked to the shock activities, which releases Si atoms
from dust grains into gas phase through sputtering or
vaporization (Schilke et al. 1997).
A total of 28 out of 43 CO outflows are detected in
the SiO 5-4 line (see Figure 1). The outflows seen in
the SiO emission are more compact as compared with
the CO spatial distribution, and appears to follow the
outflow direction defined by CO. In addition, the SiO
emission is significantly weaker than the CO emission.
This difference is most likely due to the higher excitation
conditions (density, energy) and different chemical conditions required by the SiO 5-4 transition with respect to
the CO 2-1 transition (e.g., Li et al. 2019b). The comparison of outflow velocities measured by the CO line
shows no difference between the outflows with SiO detection and without SiO detection. This indicates that
the production of SiO requires other conditions (e.g.,
density and temperature) in addition to the appropriate
velocity.
From Figure 1, it is interesting to note that there
is strong SiO emission that is neither associated with
CO outflows nor dense cores. As previously mentioned,
SiO emission is closely related to the shock phenomena, therefore its presence suggests that there are strong
shocks unrelated to star formation activities such as out
flows or jets. Figure 9 shows an overview of the SiO spectra toward G10.99. The SiO and CO emission, which is
associated with protostellar outflows, appear to be comparable in the line central velocity (e.g., panel d, e, g
and h of Figure 9). However, we note that there is also
SiO emission that appears to be unrelated to outflows

and dense cores.

Assuming optically thin and local thermodynamic
equilibrium (LTE) condition for the SiO emission, the
SiO column densities estimated to be _N_ (SiO) = 8 _._ 1 _×_
10 [11] _−_ 5 _._ 9 _×_ 10 [13] cm _[−]_ [2], with a median value of 4 _._ 7 _×_
10 [12] cm _[−]_ [2] . The derived SiO column densities are com
parable to that measured in high- and low-mass star
forming regions (e.g., Bachiller et al. 1991; Hirano et al.
2006; Fern´andez-L´opez et al. 2013). To derive SiO abundances, we estimate the H 2 column densities from CO
line (see Appendix A). The SiO abundance is found to
be _X_ (SiO) = 1 _._ 1 _×_ 10 _[−]_ [9] _−_ 1 _._ 6 _×_ 10 _[−]_ [7] with a median
value of 1 _._ 0 _×_ 10 _[−]_ [8] . Overall, we find no significant differences in the SiO column densities for the SiO gas
components associated with and without CO outflows,
except for G10.19, which shows relatively higher SiO
column densities toward the CO outflows as compared
to the regions without CO outflow counterparts.



13


In most cases the shocked regions traced by SiO emission without CO outflow counterpart are associated with
multiple velocity components, as revealed by the CO
emission (PV diagram and channel maps). In some
cases, the velocities of the SiO emission are around the
clump velocity (see panel b and c of Figure 9), while
some of them are offset from the clump velocity (see
panel i of Figure 9). The interaction between different velocity components can enhances the local shock
activities, resulting an enhancement in the SiO emission (Jim´enez-Serra et al. 2010). Figure 9 shows the
PV diagram of the CO emission across the SiO contours
for one sub-regions, the bright SiO emission appears to
be at the location of a velocity shear (panel j in Figure 9); interfaces between different velocity components.
The FWHM line widths of SiO measured toward these
shocked regions are ⩾ 5 km s _[−]_ [1], which are broader than
the narrow line width of _∼_ 0.8 km s _[−]_ [1] measured for the

widespread SiO emission along the IRDC G035.39 _−_ 0.33
(Jim´enez-Serra et al. 2010). The broad SiO emission is
a further hint of gas movement due to the interaction
between different gas components. This indicates that
the shocks that produce this SiO emission most likely
arise from colliding or intersecting gas flows. For the
other clumps, we also find that some of the SiO emission is located at the positions where velocity shears in
the CO emission may be present. This SiO emission
is most likely a result of collision or intersection of gas
flows as well.
On the other hand, we find that some of the SiO emission regions show no signs of velocity shears in the CO
emission (e.g., the regions corresponding to the spectra
of panel b and c). In addition to collision/intersection
of gas flows, the large/small-scale converging flows, the
larger scale collapse, a population of undetected lowmass objects and some dense cores outside of the map
could also create shocks, resulting in an enhancement in
the SiO emission (e.g., Jim´enez-Serra et al. 2010; Csengeri et al. 2011; Sanhueza et al. 2013; Duarte-Cabral
et al. 2014). Unfortunately, we can not distinguish between these possibilities with the data at hand. They
can be tested by spatially resolving both large and small
scale gas motions with reliable dense gas tracers (e.g,
N 2 H [+] ) or searching for deeply embedded distributed
low-mass protostars in near-infrared observations as has
been done in another IRDC by Foster et al. (2014).


5. CONCLUSIONS


In this paper, we analyzed the data from ASHES
obtained with ALMA to study molecular outflow and
shock properties in 12 massive 70 _µ_ m dark clumps.

14 Li et al.


1. Outflow activities revealed by either CO or SiO
emission are found in 9 out of the 12 clumps observed. We successfully identified 43 molecular
outflows in 41 out of 301 dense cores, with an outflow detection rate of 14% in the CO 2-1 emission.
Among the 41 cores, 12 cores are associated with
single bipolar outflows, 2 cores host two bipolar
outflows, while the remaining 27 cores have single uniploar outflows. The CO outflows are detected in both low-mass and high-mass cores. The
maximum velocity of CO outflows reaches up to
95 km s _[−]_ [1] with respect to the systemic velocity.
These results suggest that most of 70 _µ_ m dark
clumps already host protostars, and thus they cannot be assumed to be prestellar without deep interferometric observations.



5. In ASHES, the mechanical energy of outflows is
much smaller than values from more evolved highmass star-forming regions, for which outflow mechanical energy is comparable to the kinetic energy arising from the internal gas motions. The
total outflow luminosity is smaller than the turbulent dissipation rate in the majority of the clumps.
This suggests that the outflow feedback can not replenish the internal turbulence in the majority of
the sources at the current epoch. In addition, the
disruptive impact of the outflows on their parent
clouds is negligible for this sample.


6. We found strong SiO emission not associated with
protostellar outflows. This finding suggests that
protostellar outflows are not the sole mechanism
responsible for SiO production and emission. Alternatively, other processes, such as large scale collisions or intersection of converging flows, can give
rise to shocks.


ACKNOWLEDGMENTS



2. The estimated protostellar accretion rates range
from 2.0 _×_ 10 _[−]_ [9] to 3.8 _×_ 10 _[−]_ [6] _M_ _⊙_ yr _[−]_ [1] for the
dense cores detected outflows, which is smaller
than the typical value reported in more evolved
cores. The comparison of the total accretion rates
and _L_ bol _/M_ clump in different evolutionary stages
indicates that the accretion rates increase with the

evolution of star formation. For this sample, the
median ratio of outflow mass to core mass is about
8 _×_ 10 _[−]_ [3], while the median ratio of total outflow
mass to clump mass is about 2 _×_ 10 _[−]_ [4] .


3. We found a positive correlation between the outflow dynamical timescale and the gas mass of dense
cores. The observed increase of outflow dynamical
timescales towards the more massive cores indi
cates that the accretion history is longer in the
more massive cores compared to the less massive

cores.


4. We identified six episodic molecular outflows associated to cores of all masses. This indicates

that episodic outflows begin in the earliest stages
of protostellar evolution for different masses of
cores. The computed dynamical timescales ( _t_ knot )
of episodic outflow events are in the range 6 _×_ 10 [2]

to 2 _._ 5 _×_ 10 [4] yr with time span ( _△t_ knot ) between
consecutive episodic outflow events of 3 _._ 6 _×_ 10 [2] _−_
7 _._ 2 _×_ 10 [3] yr. The _△t_ knot is much longer than the
value ( _∼_ 500 yr) found in more evolved cores in
W43-MM1 (Nony et al. 2020), which indicates that
the ejection episodicity timescale is likely not constant over time and accretion bursts may be more
frequently at later stages of evolution in a cluster

environment.



This work is supported by the National Key R&D Program of China (No. 2017YFA0402604) and the Natural Science Foundation of China under grants U1731237
and 11590783. SL acknowledges support from the CfA
pre-doctoral fellowship and Chinese Scholarship Council. P.S. was partially supported by a Grant-in-Aid for
Scientific Research (KAKENHI Number 18H01259) of
Japan Society for the Promotion of Science (JSPS). P.S.
gratefully acknowledge the support from the NAOJ Visiting Fellow Program to visit the National Astronomical Observatory of Japan in November-December 2016.
Data analysis was in part carried out on the open use
data analysis computer system at the Astronomy Data
Center (ADC) of the National Astronomical Observatory of Japan. This paper makes use of the following ALMA data: ADS/JAO. ALMA#2015.1.01539.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together
with NRC (Canada), MOST and ASIAA (Taiwan), and
KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Data analysis
was in part carried out on the open use data analysis
computer system at the Astronomy Data Center (ADC)
of the National Astronomical Observatory of Japan.


_Facilities:_ ALMA.


_Software:_ CASA (McMullin et al. 2007), APLpy
(Robitaille & Bressert 2012), Astropy (Astropy Collab

15


oration et al. 2013), DS9 (Joye & Mandel 2003), Matplotlib (Hunter 2007).


REFERENCES



Alves, F. O., Caselli, P., Girart, J. M., et al. 2019, Science,

366, 90, doi: [10.1126/science.aaw3491](http://doi.org/10.1126/science.aaw3491)


Arce, H. G., Borkin, M. A., Goodman, A. A., Pineda, J. E.,

& Halle, M. W. 2010, ApJ, 715, 1170,

doi: [10.1088/0004-637X/715/2/1170](http://doi.org/10.1088/0004-637X/715/2/1170)


Arce, H. G., & Goodman, A. A. 2001, ApJ, 554, 132,

doi: [10.1086/321334](http://doi.org/10.1086/321334)


Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, in

Protostars and Planets V, ed. B. Reipurth, D. Jewitt, &

K. Keil, 245. [https://arxiv.org/abs/astro-ph/0603071](https://arxiv.org/abs/astro-ph/0603071)


Astropy Collaboration, Robitaille, T. P., Tollerud, E. J.,

et al. 2013, A&A, 558, A33,

doi: [10.1051/0004-6361/201322068](http://doi.org/10.1051/0004-6361/201322068)

Audard, M., Abrah´am, [´] P., Dunham, M. M., et al. 2014, in

Protostars and Planets VI, ed. H. Beuther, R. S. Klessen,

C. P. Dullemond, & T. Henning, 387,

doi: 10.2458/azu ~~u~~ apress ~~[9](http://doi.org/10.2458/azu_uapress_9780816531240-ch017)~~ 780816531240-ch017


Bachiller, R., Martin-Pintado, J., & Fuente, A. 1991, A&A,

243, L21


Bally, J. 2016, ARA&A, 54, 491,

doi: [10.1146/annurev-astro-081915-023341](http://doi.org/10.1146/annurev-astro-081915-023341)


Bally, J., & Lada, C. J. 1983, ApJ, 265, 824,

doi: [10.1086/160729](http://doi.org/10.1086/160729)


Baug, T., Wang, K., Liu, T., et al. 2020, ApJ, 890, 44,

doi: [10.3847/1538-4357/ab66b6](http://doi.org/10.3847/1538-4357/ab66b6)


Beltr´an, M. T., Cesaroni, R., Codella, C., et al. 2006,

Nature, 443, 427, doi: [10.1038/nature05074](http://doi.org/10.1038/nature05074)


Beltr´an, M. T., & de Wit, W. J. 2016, A&A Rv, 24, 6,

doi: [10.1007/s00159-015-0089-z](http://doi.org/10.1007/s00159-015-0089-z)


Beuther, H., Schilke, P., Sridharan, T. K., et al. 2002,

A&A, 383, 892, doi: [10.1051/0004-6361:20011808](http://doi.org/10.1051/0004-6361:20011808)


Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips,

T. G. 1987, ApJ, 315, 621, doi: [10.1086/165165](http://doi.org/10.1086/165165)


Cabrit, S., & Bertout, C. 1992, A&A, 261, 274


Caratti o Garatti, A., Stecklum, B., Garcia Lopez, R., et al.

2017, Nature Physics, 13, 276, doi: [10.1038/nphys3942](http://doi.org/10.1038/nphys3942)


Cesaroni, R., Moscadelli, L., Neri, R., et al. 2018, A&A,

612, A103, doi: [10.1051/0004-6361/201732238](http://doi.org/10.1051/0004-6361/201732238)


Cheng, Y., Qiu, K., Zhang, Q., et al. 2019, ApJ, 877, 112,

doi: [10.3847/1538-4357/ab15d4](http://doi.org/10.3847/1538-4357/ab15d4)


Codella, C., Beltr´an, M. T., Cesaroni, R., et al. 2013, A&A,

550, A81, doi: [10.1051/0004-6361/201219900](http://doi.org/10.1051/0004-6361/201219900)


Cody, A. M., & Hillenbrand, L. A. 2018, AJ, 156, 71,

doi: [10.3847/1538-3881/aacead](http://doi.org/10.3847/1538-3881/aacead)



Contreras, Y., Rathborne, J. M., Guzman, A., et al. 2017,

MNRAS, 466, 340, doi: [10.1093/mnras/stw3110](http://doi.org/10.1093/mnras/stw3110)


Contreras, Y., Schuller, F., Urquhart, J. S., et al. 2013,

A&A, 549, A45, doi: [10.1051/0004-6361/201220155](http://doi.org/10.1051/0004-6361/201220155)


Contreras, Y., Sanhueza, P., Jackson, J. M., et al. 2018,

ApJ, 861, 14, doi: [10.3847/1538-4357/aac2ec](http://doi.org/10.3847/1538-4357/aac2ec)


Csengeri, T., Bontemps, S., Schneider, N., et al. 2011,

ApJL, 740, L5, doi: [10.1088/2041-8205/740/1/L5](http://doi.org/10.1088/2041-8205/740/1/L5)


Csengeri, T., Leurini, S., Wyrowski, F., et al. 2016, A&A,

586, A149, doi: [10.1051/0004-6361/201425404](http://doi.org/10.1051/0004-6361/201425404)


Cunningham, A. J., Frank, A., Carroll, J., Blackman,

E. G., & Quillen, A. C. 2009, ApJ, 692, 816,

doi: [10.1088/0004-637X/692/1/816](http://doi.org/10.1088/0004-637X/692/1/816)


Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2014,

A&A, 570, A1, doi: [10.1051/0004-6361/201423677](http://doi.org/10.1051/0004-6361/201423677)


—. 2013, A&A, 558, A125,

doi: [10.1051/0004-6361/201321393](http://doi.org/10.1051/0004-6361/201321393)


Dunham, M. M., Arce, H. G., Mardones, D., et al. 2014,

ApJ, 783, 29, doi: [10.1088/0004-637X/783/1/29](http://doi.org/10.1088/0004-637X/783/1/29)


Ellerbroek, L. E., Podio, L., Kaper, L., et al. 2013, A&A,

551, A5, doi: [10.1051/0004-6361/201220635](http://doi.org/10.1051/0004-6361/201220635)


Feddersen, J. R., Arce, H. G., Kong, S., et al. 2020a, arXiv

e-prints, arXiv:2004.03504.

[https://arxiv.org/abs/2004.03504](https://arxiv.org/abs/2004.03504)


—. 2020b, ApJ, 896, 11, doi: [10.3847/1538-4357/ab86a9](http://doi.org/10.3847/1538-4357/ab86a9)


Federrath, C., Schr¨on, M., Banerjee, R., & Klessen, R. S.

2014, ApJ, 790, 128, doi: [10.1088/0004-637X/790/2/128](http://doi.org/10.1088/0004-637X/790/2/128)


Fern´andez-L´opez, M., Girart, J. M., Curiel, S., et al. 2013,

ApJ, 778, 72, doi: [10.1088/0004-637X/778/1/72](http://doi.org/10.1088/0004-637X/778/1/72)


Foster, J. B., Jackson, J. M., Barnes, P. J., et al. 2011,

ApJS, 197, 25, doi: [10.1088/0067-0049/197/2/25](http://doi.org/10.1088/0067-0049/197/2/25)


Foster, J. B., Rathborne, J. M., Sanhueza, P., et al. 2013,

PASA, 30, e038, doi: [10.1017/pasa.2013.18](http://doi.org/10.1017/pasa.2013.18)


Foster, J. B., Arce, H. G., Kassis, M., et al. 2014, ApJ, 791,

108, doi: [10.1088/0004-637X/791/2/108](http://doi.org/10.1088/0004-637X/791/2/108)


Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars

and Planets VI, ed. H. Beuther, R. S. Klessen, C. P.

Dullemond, & T. Henning, 451,

doi: 10.2458/azu ~~u~~ apress ~~[9](http://doi.org/10.2458/azu_uapress_9780816531240-ch020)~~ 780816531240-ch020


Graves, S. F., Richer, J. S., Buckle, J. V., et al. 2010,

MNRAS, 409, 1412,

doi: [10.1111/j.1365-2966.2010.17140.x](http://doi.org/10.1111/j.1365-2966.2010.17140.x)


Guzm´an, A. E., Sanhueza, P., Contreras, Y., et al. 2015,

ApJ, 815, 130, doi: [10.1088/0004-637X/815/2/130](http://doi.org/10.1088/0004-637X/815/2/130)

16 Li et al.



Herv´ıas-Caimapo, C., Merello, M., Bronfman, L., et al.

2019, ApJ, 872, 200, doi: [10.3847/1538-4357/aaf9ac](http://doi.org/10.3847/1538-4357/aaf9ac)


Hirano, N., Liu, S.-Y., Shang, H., et al. 2006, ApJL, 636,

L141, doi: [10.1086/500201](http://doi.org/10.1086/500201)


Hosokawa, T., & Omukai, K. 2009, ApJ, 691, 823,

doi: [10.1088/0004-637X/691/1/823](http://doi.org/10.1088/0004-637X/691/1/823)


Hunter, J. D. 2007, Computing in Science Engineering, 9,

90


Hunter, T. R., Brogan, C. L., MacLeod, G., et al. 2017,

ApJL, 837, L29, doi: [10.3847/2041-8213/aa5d0e](http://doi.org/10.3847/2041-8213/aa5d0e)


Jackson, J. M., Rathborne, J. M., Foster, J. B., et al. 2013,

PASA, 30, e057, doi: [10.1017/pasa.2013.37](http://doi.org/10.1017/pasa.2013.37)


Jim´enez-Serra, I., Caselli, P., Tan, J. C., et al. 2010,

MNRAS, 406, 187, doi: [10.1111/j.1365-2966.2010.16698.x](http://doi.org/10.1111/j.1365-2966.2010.16698.x)


Joye, W. A., & Mandel, E. 2003, in Astronomical Society of

the Pacific Conference Series, Vol. 295, Astronomical

Data Analysis Software and Systems XII, ed. H. E.

Payne, R. I. Jedrzejewski, & R. N. Hook, 489


Keto, E. 2003, ApJ, 599, 1196, doi: [10.1086/379545](http://doi.org/10.1086/379545)


Keto, E. R., Ho, P. T. P., & Haschick, A. D. 1988, ApJ,

324, 920, doi: [10.1086/165949](http://doi.org/10.1086/165949)


Kim, K.-T., & Kurtz, S. E. 2006, ApJ, 643, 978,

doi: [10.1086/502961](http://doi.org/10.1086/502961)


Krumholz, M. R., Klein, R. I., McKee, C. F., Offner, S.

S. R., & Cunningham, A. J. 2009, Science, 323, 754,

doi: [10.1126/science.1165857](http://doi.org/10.1126/science.1165857)


Krumholz, M. R., Bate, M. R., Arce, H. G., et al. 2014, in

Protostars and Planets VI, ed. H. Beuther, R. S. Klessen,

C. P. Dullemond, & T. Henning, 243,

doi: 10.2458/azu ~~u~~ apress ~~[9](http://doi.org/10.2458/azu_uapress_9780816531240-ch011)~~ 780816531240-ch011


Kuiper, R., Klahr, H., Beuther, H., & Henning, T. 2010,

ApJ, 722, 1556, doi: [10.1088/0004-637X/722/2/1556](http://doi.org/10.1088/0004-637X/722/2/1556)


—. 2011, ApJ, 732, 20, doi: [10.1088/0004-637X/732/1/20](http://doi.org/10.1088/0004-637X/732/1/20)


Kuiper, R., Turner, N. J., & Yorke, H. W. 2016, ApJ, 832,

40, doi: [10.3847/0004-637X/832/1/40](http://doi.org/10.3847/0004-637X/832/1/40)


Kuiper, R., Yorke, H. W., & Turner, N. J. 2015, ApJ, 800,

86, doi: [10.1088/0004-637X/800/2/86](http://doi.org/10.1088/0004-637X/800/2/86)


Lada, C. J., & Fich, M. 1996, ApJ, 459, 638,

doi: [10.1086/176929](http://doi.org/10.1086/176929)


Leurini, S., Codella, C., Gusdorf, A., et al. 2013, A&A, 554,

A35, doi: [10.1051/0004-6361/201118154](http://doi.org/10.1051/0004-6361/201118154)


Leurini, S., Codella, C., L´opez-Sepulcre, A., et al. 2014,

A&A, 570, A49, doi: [10.1051/0004-6361/201424251](http://doi.org/10.1051/0004-6361/201424251)


Li, H., Li, D., Qian, L., et al. 2015, ApJS, 219, 20,

doi: [10.1088/0067-0049/219/2/20](http://doi.org/10.1088/0067-0049/219/2/20)


Li, S., Zhang, Q., Pillai, T., et al. 2019a, ApJ, 886, 130,

doi: [10.3847/1538-4357/ab464e](http://doi.org/10.3847/1538-4357/ab464e)


Li, S., Wang, J., Zhang, Z.-Y., et al. 2017, MNRAS, 466,

248, doi: [10.1093/mnras/stw3076](http://doi.org/10.1093/mnras/stw3076)



Li, S., Wang, J., Fang, M., et al. 2019b, ApJ, 878, 29,

doi: [10.3847/1538-4357/ab1e4c](http://doi.org/10.3847/1538-4357/ab1e4c)


Li, Z.-Y., & Nakamura, F. 2006, ApJL, 640, L187,

doi: [10.1086/503419](http://doi.org/10.1086/503419)


Liu, T., Lacy, J., Li, P. S., et al. 2017, ApJ, 849, 25,

doi: [10.3847/1538-4357/aa8d73](http://doi.org/10.3847/1538-4357/aa8d73)


Lodato, G., & Clarke, C. J. 2004, MNRAS, 353, 841,

doi: [10.1111/j.1365-2966.2004.08112.x](http://doi.org/10.1111/j.1365-2966.2004.08112.x)


L´opez-Sepulcre, A., Cesaroni, R., & Walmsley, C. M. 2010,

A&A, 517, A66, doi: [10.1051/0004-6361/201014252](http://doi.org/10.1051/0004-6361/201014252)


Lu, X., Zhang, Q., Wang, K., & Gu, Q. 2015, ApJ, 805,

171, doi: [10.1088/0004-637X/805/2/171](http://doi.org/10.1088/0004-637X/805/2/171)


Lu, X., Zhang, Q., Liu, H. B., et al. 2018, ApJ, 855, 9,

doi: [10.3847/1538-4357/aaad11](http://doi.org/10.3847/1538-4357/aaad11)


Mac Low, M.-M. 1999, ApJ, 524, 169, doi: [10.1086/307784](http://doi.org/10.1086/307784)


Mangum, J. G., & Shirley, Y. L. 2015, PASP, 127, 266,

doi: [10.1086/680323](http://doi.org/10.1086/680323)


McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565,

doi: [10.1146/annurev.astro.45.051806.110602](http://doi.org/10.1146/annurev.astro.45.051806.110602)


McKee, C. F., & Tan, J. C. 2003, ApJ, 585, 850,

doi: [10.1086/346149](http://doi.org/10.1086/346149)


McMullin, J. P., Waters, B., Schiebel, D., Young, W., &

Golap, K. 2007, in Astronomical Society of the Pacific

Conference Series, Vol. 376, Astronomical Data Analysis

Software and Systems XVI, ed. R. A. Shaw, F. Hill, &

D. J. Bell, 127


Molinari, S., Pezzuto, S., Cesaroni, R., et al. 2008, A&A,

481, 345, doi: [10.1051/0004-6361:20078661](http://doi.org/10.1051/0004-6361:20078661)


Nakamura, F., & Li, Z.-Y. 2007, ApJ, 662, 395,

doi: [10.1086/517515](http://doi.org/10.1086/517515)


—. 2014, ApJ, 783, 115, doi: [10.1088/0004-637X/783/2/115](http://doi.org/10.1088/0004-637X/783/2/115)


Nakamura, F., Sugitani, K., Shimajiri, Y., et al. 2011a,

ApJ, 737, 56, doi: [10.1088/0004-637X/737/2/56](http://doi.org/10.1088/0004-637X/737/2/56)


Nakamura, F., Kamada, Y., Kamazaki, T., et al. 2011b,

ApJ, 726, 46, doi: [10.1088/0004-637X/726/1/46](http://doi.org/10.1088/0004-637X/726/1/46)


Nony, T., Motte, F., Louvet, F., et al. 2020, A&A, 636,

A38, doi: [10.1051/0004-6361/201937046](http://doi.org/10.1051/0004-6361/201937046)


Offner, S. S. R., & Chaban, J. 2017, ApJ, 847, 104,

doi: [10.3847/1538-4357/aa8996](http://doi.org/10.3847/1538-4357/aa8996)


Offner, S. S. R., & Liu, Y. 2018, Nature Astronomy, 2, 896,

doi: [10.1038/s41550-018-0566-1](http://doi.org/10.1038/s41550-018-0566-1)


Palau, A., Ho, P. T. P., Zhang, Q., et al. 2006, ApJL, 636,

L137, doi: [10.1086/500242](http://doi.org/10.1086/500242)


Parks, J. R., Plavchan, P., White, R. J., & Gee, A. H. 2014,

ApJS, 211, 3, doi: [10.1088/0067-0049/211/1/3](http://doi.org/10.1088/0067-0049/211/1/3)


Pillai, T., Kauffmann, J., Zhang, Q., et al. 2019, A&A, 622,

A54, doi: [10.1051/0004-6361/201732570](http://doi.org/10.1051/0004-6361/201732570)


Plunkett, A. L., Arce, H. G., Corder, S. A., et al. 2015a,

ApJ, 803, 22, doi: [10.1088/0004-637X/803/1/22](http://doi.org/10.1088/0004-637X/803/1/22)

Plunkett, A. L., Arce, H. G., Mardones, D., et al. 2015b,


Nature, 527, 70, doi: [10.1038/nature15702](http://doi.org/10.1038/nature15702)


Pudritz, R. E., & Norman, C. A. 1983, ApJ, 274, 677,


doi: [10.1086/161481](http://doi.org/10.1086/161481)


—. 1986, ApJ, 301, 571, doi: [10.1086/163924](http://doi.org/10.1086/163924)


Qiu, K., Wyrowski, F., Menten, K., Zhang, Q., & G¨usten,


R. 2019, ApJ, 871, 141, doi: [10.3847/1538-4357/aaf728](http://doi.org/10.3847/1538-4357/aaf728)


Qiu, K., & Zhang, Q. 2009, ApJL, 702, L66,


doi: [10.1088/0004-637X/702/1/L66](http://doi.org/10.1088/0004-637X/702/1/L66)


Qiu, K., Zhang, Q., Wu, J., & Chen, H.-R. 2009, ApJ, 696,


66, doi: [10.1088/0004-637X/696/1/66](http://doi.org/10.1088/0004-637X/696/1/66)


Qiu, K., Zhang, Q., Megeath, S. T., et al. 2008, ApJ, 685,


1005, doi: [10.1086/591044](http://doi.org/10.1086/591044)


Rathborne, J. M., Whitaker, J. S., Jackson, J. M., et al.


2016, PASA, 33, e030, doi: [10.1017/pasa.2016.23](http://doi.org/10.1017/pasa.2016.23)


Richer, J. S., Shepherd, D. S., Cabrit, S., Bachiller, R., &


Churchwell, E. 2000, Protostars and Planets IV, 867


Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical


Plotting Library in Python, Astrophysics Source Code


Library. [http://ascl.net/1208.017](http://ascl.net/1208.017)


Rohde, P. F., Walch, S., Seifried, D., et al. 2019, MNRAS,


483, 2563, doi: [10.1093/mnras/sty3302](http://doi.org/10.1093/mnras/sty3302)


Sakai, T., Sakai, N., Foster, J. B., et al. 2013, ApJL, 775,


L31, doi: [10.1088/2041-8205/775/1/L31](http://doi.org/10.1088/2041-8205/775/1/L31)


Sanhueza, P., Garay, G., Bronfman, L., et al. 2010, ApJ,


715, 18, doi: [10.1088/0004-637X/715/1/18](http://doi.org/10.1088/0004-637X/715/1/18)


Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012,


ApJ, 756, 60, doi: [10.1088/0004-637X/756/1/60](http://doi.org/10.1088/0004-637X/756/1/60)


—. 2013, ApJ, 773, 123, doi: [10.1088/0004-637X/773/2/123](http://doi.org/10.1088/0004-637X/773/2/123)


Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ,


841, 97, doi: [10.3847/1538-4357/aa6ff8](http://doi.org/10.3847/1538-4357/aa6ff8)


Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886,


102, doi: [10.3847/1538-4357/ab45e9](http://doi.org/10.3847/1538-4357/ab45e9)


Santiago-Garc´ıa, J., Tafalla, M., Johnstone, D., & Bachiller,


R. 2009, A&A, 495, 169,


doi: [10.1051/0004-6361:200810739](http://doi.org/10.1051/0004-6361:200810739)


Schilke, P., Walmsley, C. M., Pineau des Forets, G., &


Flower, D. R. 1997, A&A, 321, 293


Scholz, A., Froebrich, D., & Wood, K. 2013, MNRAS, 430,


2910, doi: [10.1093/mnras/stt091](http://doi.org/10.1093/mnras/stt091)


Schuller, F., Menten, K. M., Contreras, Y., et al. 2009,


A&A, 504, 415, doi: [10.1051/0004-6361/200811568](http://doi.org/10.1051/0004-6361/200811568)



17


Shang, H., Li, Z. Y., & Hirano, N. 2007, in Protostars and

Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 261

Sheikhnezami, S., Fendt, C., Porth, O., Vaidya, B., &

Ghanbari, J. 2012, ApJ, 757, 65,

doi: [10.1088/0004-637X/757/1/65](http://doi.org/10.1088/0004-637X/757/1/65)

Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25,

23, doi: [10.1146/annurev.aa.25.090187.000323](http://doi.org/10.1146/annurev.aa.25.090187.000323)


Shu, F. H., Najita, J. R., Shang, H., & Li, Z.-Y. 2000,

Protostars and Planets IV, 789

Shu, F. H., Ruden, S. P., Lada, C. J., & Lizano, S. 1991,

ApJL, 370, L31, doi: [10.1086/185970](http://doi.org/10.1086/185970)

Stephens, I. W., Jackson, J. M., Sanhueza, P., et al. 2015,

ApJ, 802, 6, doi: [10.1088/0004-637X/802/1/6](http://doi.org/10.1088/0004-637X/802/1/6)
Tomisaka, K. 1998, ApJL, 502, L163, doi: [10.1086/311504](http://doi.org/10.1086/311504)

van Kempen, T. A., Hogerheijde, M. R., van Dishoeck,

E. F., et al. 2016, A&A, 587, A17,

doi: [10.1051/0004-6361/201424725](http://doi.org/10.1051/0004-6361/201424725)

Vorobyov, E. I., & Basu, S. 2010, ApJ, 719, 1896,
doi: [10.1088/0004-637X/719/2/1896](http://doi.org/10.1088/0004-637X/719/2/1896)

Vorobyov, E. I., Elbakyan, V. G., Plunkett, A. L., et al.
2018, A&A, 613, A18, doi: [10.1051/0004-6361/201732253](http://doi.org/10.1051/0004-6361/201732253)

Wang, K., Zhang, Q., Wu, Y., & Zhang, H. 2011, ApJ, 735,
64, doi: [10.1088/0004-637X/735/1/64](http://doi.org/10.1088/0004-637X/735/1/64)

Wang, P., Li, Z.-Y., Abel, T., & Nakamura, F. 2010, ApJ,
709, 27, doi: [10.1088/0004-637X/709/1/27](http://doi.org/10.1088/0004-637X/709/1/27)

Whitaker, J. S., Jackson, J. M., Rathborne, J. M., et al.

2017, AJ, 154, 140, doi: [10.3847/1538-3881/aa86ad](http://doi.org/10.3847/1538-3881/aa86ad)

Wyrowski, F., G¨usten, R., Menten, K. M., et al. 2016,
A&A, 585, A149, doi: [10.1051/0004-6361/201526361](http://doi.org/10.1051/0004-6361/201526361)

Yang, A. Y., Thompson, M. A., Urquhart, J. S., & Tian,

W. W. 2018, ApJS, 235, 3,

doi: [10.3847/1538-4365/aaa297](http://doi.org/10.3847/1538-4365/aaa297)

Zhang, Q., & Ho, P. T. P. 1997, ApJ, 488, 241,
doi: [10.1086/304667](http://doi.org/10.1086/304667)

Zhang, Q., Ho, P. T. P., & Wright, M. C. H. 2000, AJ, 119,
1345, doi: [10.1086/301274](http://doi.org/10.1086/301274)

Zhang, Q., Hunter, T. R., Brand, J., et al. 2005, ApJ, 625,
864, doi: [10.1086/429660](http://doi.org/10.1086/429660)
—. 2001, ApJL, 552, L167, doi: [10.1086/320345](http://doi.org/10.1086/320345)

Zhang, Q., Hunter, T. R., Sridharan, T. K., & Cesaroni, R.
1999, ApJL, 527, L117, doi: [10.1086/312411](http://doi.org/10.1086/312411)

Zhang, Q., Wang, K., Lu, X., & Jim´enez-Serra, I. 2015,
ApJ, 804, 141, doi: [10.1088/0004-637X/804/2/141](http://doi.org/10.1088/0004-637X/804/2/141)

Zhu, Z., Hartmann, L., & Gammie, C. 2009, ApJ, 694,

1045, doi: [10.1088/0004-637X/694/2/1045](http://doi.org/10.1088/0004-637X/694/2/1045)

18 Li et al.


APPENDIX


A. ESTIMATE OF OUTFLOW PARAMETERS


Assuming that local thermodynamic equilibrium (LTE), we can estimate the CO column density ( _N_ CO ), outflow
mass ( _M_ out ), momentum ( _P_ out ), energy ( _E_ out ), based on the CO emission (Bally & Lada 1983; Cabrit & Bertout 1992;
Mangum & Shirley 2015):



16 _._ 59
_N_ CO (cm _[−]_ [2] ) = 1 _._ 08 _×_ 10 [13] (T ex + 0 _._ 92) exp
� T ex



�� 1 _−τ_ 21 e _[τ]_ [21] [T] [B] [dv] _[,]_ (A1)



H 2
_M_ out = _d_ [2] � CO



_m_ H 2
�



_N_ CO (Ω) _d_ Ω _,_ (A2)

� Ω



_P_ out = _M_ r _v_ _r_ + _M_ _b_ _v_ b _,_ (A3)



_E_ out = [1]



2 _[M]_ [b] _[v]_ b [2] _[,]_ (A4)




[1] r [+] [1]

2 _[M]_ [r] _[v]_ [2] 2



Using the CO outflow projected distance ( _λ_ max ), we compute the outflow dynamical timescale ( _t_ dyn ), outflow rate
( _M_ [˙] out ), outflow luminosity ( _L_ out ), and mechanical force ( _F_ out ):


_λ_ max
_t_ dyn = (A5)
( _v_ max(b) + _v_ max(r) ) _/_ 2 _[,]_


˙
_M_ out = _[M]_ [out] _,_ (A6)

_t_ dyn


_L_ out = _[E]_ [out] _,_ (A7)

_t_ dyn


_F_ out = _[P]_ [out] _._ (A8)

_t_ dyn


Here, _dv_ is the velocity interval in km s _[−]_ [1], _T_ ex is the line excitation temperature, _τ_ 21 is the optical depth, _T_ B is
brightness temperature in K, Ωis the total solid angle that the flow subtends, _d_ is the source distance, _v_ max(b) and
_v_ max(r) are the maximum velocities of CO blue-shifted and red-shifted emission, respectively. _M_ r and _M_ b are the gas
masse of CO outflows at the corresponding blue-shifted ( _v_ b ) and red-shifted ( _v_ r ) velocities, respectively.
A range of excitation temperatures, from 10 to 60 K, has been used to calculate the column density in order to
understand the effect of excitation temperatures on the CO column density. The estimated CO column density agree
within a factor of 1.5 in this temperature range, which indicates that the CO column density dose not significantly
depend on the temperature. In this work, we assume that CO emission is optically thin in the line wing and that
the dust temperature approximate the excitation temperature of outflow gas (see Table 1), and adopt the CO-to-H 2
abundance of 10 _[−]_ [4], � COH 2 � = 10 [4] (Blake et al. 1987), and mean molecular mass per hydrogen molecule _m_ H 2 = 2.72m H .
The CO velocity integrated intensity has been corrected for primary beam attenuation, while the inclination of the
outflow axis with respect to the line of sight have not been corrected in the estimation of the outflow parameters.

19

20 Li et al.

21

22 Li et al.

23

24 Li et al.


**Table** **4.** Parameters of CO Knots.


Clump Core ID Knot _λ_ knot _v_ knot _t_ knot _△v_ knot


(pc) (km s _[−]_ [1] ) (10 [3] yr) (10 [3] yr)


(1) (2) (3) (4) (5) (6) (7)



1

G14.49



B0 0.11 11.50 9.75 ...

R0 0.07 10.50 6.41 ...

R1 0.14 11.00 12.23 5.83

R2 0.21 10.80 19.38 7.15

R3 0.28 11.00 24.81 5.42

R4 0.39 15.00 25.17 0.36



B0 0.14 60.00 2.24 ...

2 R0 0.21 52.50 3.84 ...

R1 0.25 43.00 5.65 1.81


B0 0.04 9.76 4.46 ...
G28.23 1
B1 0.15 14.26 10.01 5.55


B0 0.13 37.93 3.39 ...

G331.37 3 R0 0.05 20.57 2.50 ...

R1 0.07 18.07 3.70 1.20


B0 0.03 13.31 1.97 ...
G340.23 2
B1 0.11 16.11 6.96 5.00


B0 0.02 36.45 0.56 ...

G341.03 1 B1 0.17 24.95 6.83 6.26

B2 0.35 28.45 12.09 5.27

Mean 0.15 23.43 8.52 4.38

Median 0.14 16.11 6.41 5.35

Minimum 0.02 9.76 0.56 0.36

Maximum 0.39 60.00 25.17 7.15


Notes. Column (3): the name of knots. Column (4): the projected distance of knots. Column (5): the knots maximum velocity respect to the
core velocity. Column (6): the knot dynamical timescale. Column (7):
the time span between consecutive knots. The last four rows are the
mean, median, minimum, and maximum values of estimated parameters.
The parameters are not corrected for the inclination angle of outflows.

25


(a)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
shows 20% of the sensitivity level of the mosaic in the ALMA continuum image. The green stars indicate the identified dense
cores. Upper left: ALMA 1.3 mm continuum image of G14.49. The contour levels are (-4, -3, 3, 4, 6, 8, 10, 12, 15,18, 25, 35) _×σ_,
with _σ_ =0.168 mJy beam _[−]_ [1] . Upper right: The blue-shifted (blue contours) and red-shifted (red contours) components of CO
emission, and SiO velocity-integrated intensity (black contours, integration range is between 3 and 75 km s _[−]_ [1] ) overlaid on the
continuum emission. The blue and red contours levels are (7, 12, 17, 22, 27 ....) _×σ_, where the _σ_ are 0.1 Jy beam _[−]_ [1] km s _[−]_ [1] and
0.12 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black contours are (3, 5, 7, 9, 11, 13, 15, 17) _×σ_, with _σ_ =
0.06 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of the dust cores defined in Sanhueza et al. (2019). On the left side
panels, black numbers correspond to the name of all cores. On the right side panels, the green numbers indicate only the cores
associated with molecular outflows. Bottom: example spectra of SiO and CO lines. The black vertical dashed lines represent
the _v_ lsr of the clump.

26 Li et al.


(b)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
indicates 20% of the sensitivity level of the mosaic from the ALMA continuum image. The green stars indicate the identified
dense cores. Upper left: ALMA 1.3 mm continuum image of G28.23. The contour levels are (-4, -3, 3, 4, 5, 6, 7, 8, 9) _×σ_,
with _σ_ =0.164 mJy beam _[−]_ [1] . Upper right: The blue-shifted (blue contours) and red-shifted (red contours) components of CO
emission, and SiO velocity-integrated intensity (black contours, integration range is between 67 and 85 km s _[−]_ [1] ) overlaid on
the continuum emission. The blue and red contours levels are (4, 6, 9, 13, 18, 24, 31, 39, 49, 60) _×σ_, where the _σ_ are 0.035
Jy beam _[−]_ [1] km s _[−]_ [1] and 0.06 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black contours are (3, 4, 5, 6, 7,
8, 9) _×σ_, with _σ_ = 0.015 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of the dust cores. On the left side panels, black
numbers correspond to the name of all cores. On the right side panels, the green numbers indicate only the cores associated
with molecular outflows. Bottom: example spectra of SiO and CO lines. The black vertical dashed lines represent the _v_ lsr of
the clump.

27


(c)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
indicates 20% of the sensitivity level of the mosaic from the ALMA continuum image. The green stars indicate the identified
dense cores. Upper: example spectra of SiO and CO lines. The black vertical dashed lines represent the _v_ lsr of the clump.
Bottom left: ALMA 1.3 mm continuum image of G327.11. The contour levels are (-4, -3, 3, 4, 5, 7, 10, 15, 23, 35) _×σ_, with
_σ_ =0.089 mJy beam _[−]_ [1] . Bottom right: The blue-shifted (blue contours) and red-shifted (red contours) components of CO
emission, and SiO velocity-integrated intensity (black contours, integration range is between -68 and -58 km s _[−]_ [1] ) overlaid on
the continuum emission. The blue and red contours levels are (4, 6, 9, 13, 18, 24, 31, 39, 49, 60) _×σ_, where the _σ_ are 0.04 Jy
beam _[−]_ [1] km s _[−]_ [1] and 0.025 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black contours are (3, 4, 5, 7, 10, 14,
19, 25) _×σ_, with _σ_ = 0.01 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of the dust cores. On the left side panels, black
numbers correspond to the name of all cores. On the right side panels, the green numbers indicate only the cores associated with
molecular outflows. The directions of outflow #1 and #2 toward #2–G327.11 are approximately along southeast-northwest and
south-north, respectively.

28 Li et al.

|#3 #4 #14|Col2|Col3|Col4|
|---|---|---|---|
|**#3**<br>**#4**<br>**#14**|**#4**<br>**#14**|**#4**<br>**#14**|**#4**<br>**#14**|



(d)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
shows 20% of the sensitivity level of the mosaic from the ALMA continuum image. The green stars indicate the identified dense
cores. Upper: example spectra of SiO and CO lines. The black vertical dashed lines represent the _v_ lsr of the clump. Bottom
left: ALMA 1.3 mm continuum image of G331.37. The contour levels are (-4, -3, 3, 4, 5, 7, 9, 12, 16) _×σ_, with _σ_ =0.083
mJy beam _[−]_ [1] . Bottom right: The blue-shifted (blue contours) and red-shifted (red contours) components of CO emission, and
SiO velocity-integrated intensity (black contours, integration range is between -95 and -69 km s _[−]_ [1] ) overlaid on the continuum
emission. The blue and red contours levels are (4, 6, 9, 13, 18, 24, 31, 39, 49, 60) _×σ_, where the _σ_ are 0.025 Jy beam _[−]_ [1] km
s _[−]_ [1] and 0.01 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black contours are (3, 4, 5, 6, 7, 10, 14, 19,
25) _×σ_, with _σ_ = 0.015 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of the dust cores. On the left side panels, black
numbers correspond to the name of all cores. On the right side panels, the green numbers indicate only the cores associated
with molecular outflows.

29


(e)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
shows 20% of the sensitivity level of the mosaic from the ALMA continuum image. The green stars indicate the identified dense
cores. Upper left: ALMA 1.3 mm continuum image of G337.54. The contour levels are (-4, -3, 3, 4, 6, 8, 10, 14, 20, 30, 45,
75) _×σ_, with _σ_ =0.068 mJy beam _[−]_ [1] . Upper right: The blue-shifted (blue contours) and red-shifted (red contours) components
of CO emission, and SiO velocity-integrated intensity (black contours, integration range is between -67 and -45 km s _[−]_ [1] ) overlaid
on the continuum emission. The blue and red contours levels are (5, 7, 9, 14, 20, 27, 35, 44, 54, 74) _×σ_, where the _σ_ are 0.08 Jy
beam _[−]_ [1] km s _[−]_ [1] and 0.13 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black contours are (3, 5, 6, 7, 9, 11, 13,
15, 17) _×σ_, with _σ_ = 0.015 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of the dust cores. On the left side panels, black
numbers correspond to the name of all cores. On the right side panels, the green numbers indicate only the cores associated
with molecular outflows. Bottom: example spectra of SiO and CO lines. The black vertical dashed lines represent the _v_ lsr of
the clump.

30 Li et al.


(f)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
indicates 20% of the sensitivity level of the mosaic from the ALMA continuum image. The green stars indicate the identified
dense cores. Upper left: ALMA 1.3 mm continuum image of G340.23. The contour levels are (-4, -3, 3, 4, 5, 7, 8, 11, 14, 18,
23) _×σ_, with _σ_ =0.139 mJy beam _[−]_ [1] . Upper right: The blue-shifted (blue contours) components of CO emission and SiO velocityintegrated intensity (black contours, integration range is between -60 and -47 km s _[−]_ [1] ) overlaid on the continuum emission. The
blue red contours levels are (5, 7, 9, 12, 15, 20, 31, 30, 40, 50) _×σ_, where the _σ_ are 0.02 Jy beam _[−]_ [1] km s _[−]_ [1] for blue contours.
The black contours are (3, 4, 5, 6, 7, 10, 14, 19, 25) _×σ_, with _σ_ = 0.015 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of
the dust cores. On the left side panels, black numbers correspond to the name of all cores. On the right side panels, the green
numbers indicate only the cores associated with molecular outflows. Bottom: example spectra of SiO and CO lines. The black
vertical dashed lines represent the _v_ lsr of the clump.

31


(g)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
indicates 20% of the sensitivity level of the mosaic from the ALMA continuum image. The green stars indicate the identified
dense cores. Upper left: ALMA 1.3 mm continuum image of G341.03. The contour levels are (-4, -3, 3, 4, 6, 9, 12, 16, 22) _×σ_,
with _σ_ =0.070 mJy beam _[−]_ [1] . Upper right: The blue-shifted (blue contours) and red-shifted (red contours) components of CO
emission, and SiO velocity-integrated intensity (black contours, integration range is between -66 and -31 km s _[−]_ [1] ) overlaid on
the continuum emission. The blue and red contours levels are (5, 7, 9, 14, 20, 27, 35, 44, 54, 74) _×σ_, where the _σ_ are 0.07
Jy beam _[−]_ [1] km s _[−]_ [1] and 0.015 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black contours are (3, 5, 6, 7,
9, 11, 13, 15, 17) _×σ_, with _σ_ = 0.02 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of the dust cores. On the left side
panels, black numbers correspond to the name of all cores. On the right side panels, the green numbers indicate only the cores
associated with molecular outflows. Bottom: example spectra of SiO and CO lines. The black vertical dashed lines represent
the _v_ lsr of the clump. The directions of outflow #1 and #2 toward #1–G341.03 are approximately along northeast-southwest
and southeast-northwest, respectively.

32 Li et al.


(h)


**Figure** **10.** Presented here are individual plots for Figure 1 which are available as the online material. Dashed orange contour
indicates 20% of the sensitivity level of the mosaic from the ALMA continuum image. The green stars indicate the identified
dense cores. Upper left: ALMA 1.3 mm continuum image of G343.48. The contour levels are (-4, -3, 3, 4, 6, 8, 12, 20, 40,
100) _×σ_, with _σ_ =0.068 mJy beam _[−]_ [1] . Upper right: The blue-shifted (blue contours) and red-shifted (red contours) components
of CO emission, and SiO velocity-integrated intensity (black contours, integration range is between -42 and -19 km s _[−]_ [1] ) overlaid
on the continuum emission. The blue and red contours levels are (5, 7, 9, 14, 20, 27, 35, 44, 54, 74) _×σ_, where the _σ_ are 0.04
Jy beam _[−]_ [1] km s _[−]_ [1] and 0.06 Jy beam _[−]_ [1] km s _[−]_ [1] for blue and red contours, respectively. The black contours are (3, 4, 5, 6, 7,
9, 11, 14, 20, 27) _×σ_, with _σ_ = 0.015 Jy beam _[−]_ [1] km s _[−]_ [1] . Green stars show the position of the dust cores. On the left side
panels, black numbers correspond to the name of all cores. On the right side panels, the green numbers indicate only the cores
associated with molecular outflows. Bottom: example spectra of SiO and CO lines. The black vertical dashed lines represent
the _v_ lsr of the clump.


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "1''.2 (~4000-7500 AU)",
  "failed_quote": "The uv-taper was used in those sources to obtain a similar synthesized beam size of 1 _[′′]_ _._ 2 for each source (see also Sanhueza et al. 2019)."
 },
 {
  "path": "processing.imaging.uv_taper.evidence[0]",
  "value": "used in some sources to obtain a similar synthesized beam size of 1''.2",
  "failed_quote": "The uv-taper was used in those sources to obtain a similar synthesized beam size of 1 _[′′]_ _._ 2 for each source (see also Sanhueza et al. 2019)."
 },
 {
  "path": "processing.imaging.primary_beam_correction.evidence[0]",
  "value": "applied to combined data for flux measurements; display images use 12 m array data prior to primary beam correction",
  "failed_quote": "All images shown in the paper use the 12 m array data only and prior to primary beam correction, while all measured fluxes are derived from the combined data (including 12 m, 7 m, and TP) and corrected for the primary beam attenuation."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "1''.2",
  "failed_quote": "The uv-taper was used in those sources to obtain a similar synthesized beam size of 1 _[′′]_ _._ 2 for each source (see also Sanhueza et al. 2019)."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "Velocity range threshold > 2 sigma (rms in line-free channels); outflow lobe contour threshold > 4 sigma (rms of integrated intensity map)",
  "failed_quote": "The velocity range ( _△v_ ) of outflows are defined where the emission avoid environment gas around the system velocity and higher than the 2 _σ_ noise level, where _σ_ is the rms noise level in the line-free channels."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Visually follow contours in CO PV diagrams along outflow axes to define projected distance (lambda_knot) and velocity (v_knot) of emission knots, and compute dynamical timescales t_knot = lambda_knot / v_knot and inter-knot time spans Delta t_knot.",
  "failed_quote": "Similarly, we can estimate the dynamical timescale of the identified knots using their projected distance ( _λ_ knot ) and corresponding velocity ( _v_ knot ) with respect to the associated core, _t_ knot = _λ_ knot _/v_ knot ."
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Compared knot timescales estimated using individual v_knot versus lobe mean velocity v_lobe = <v_knot>, finding good agreement.",
  "failed_quote": "By comparing the knots timescales estimated by _v_ knot and _v_ lobe, we find that the two results agree very well with each other (see Figure 7)."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Compute clump turbulent energy E_turb (Equations 1-2), turbulent dissipation time t_diss using two approaches (Equation 4 from McKee & Ostriker 2007 and Equation 5 from Mac Low 1999), turbulent dissipation rate E_dot_turb (Equation 3), ratio r_L = L_out / E_dot_turb, and gravitational binding energy E_grav = G M_cl^2 / R_cl.",
  "failed_quote": "Similarly, the outflow energy ( _E_ out ) can be compared to the gravitational binding energy of clouds, _E_ grav = _GM_ cl [2] _[/R]_ [cl] [,] [for] [evaluating] [the] [potential] [disruptive] [effects] [of] [outflows] [on] [their] [clouds.]"
 },
 {
  "path": "software[1].used_for.evidence[1]",
  "value": "Inspecting PPV data cubes of CO emission to identify outflows",
  "failed_quote": "_Software:_ CASA (McMullin et al. 2007), APLpy (Robitaille & Bressert 2012), Astropy (Astropy Collaboration et al. 2013), DS9 (Joye & Mandel 2003), Matplotlib (Hunter 2007)."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "not stated",
  "failed_quote": "_Software:_ CASA (McMullin et al. 2007), APLpy (Robitaille & Bressert 2012), Astropy (Astropy Collaboration et al. 2013), DS9 (Joye & Mandel 2003), Matplotlib (Hunter 2007)."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "not stated",
  "failed_quote": "_Software:_ CASA (McMullin et al. 2007), APLpy (Robitaille & Bressert 2012), Astropy (Astropy Collaboration et al. 2013), DS9 (Joye & Mandel 2003), Matplotlib (Hunter 2007)."
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "not stated",
  "failed_quote": "_Software:_ CASA (McMullin et al. 2007), APLpy (Robitaille & Bressert 2012), Astropy (Astropy Collaboration et al. 2013), DS9 (Joye & Mandel 2003), Matplotlib (Hunter 2007)."
 }
]
```
