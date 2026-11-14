# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026AJ....172..108L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version June 25, 2026
Typeset using L [A] TEX **twocolumn** style in AASTeX631


**Formation** **of** **a** **Protostellar** **Multiple** **System** **via** **Rotational** **Fragmentation**


Tie Liu, [1,] _[ ∗]_ [Qiuyi](http://orcid.org/0000-0003-4506-3171) Luo, [2, 3] Siju [Zhang,](http://orcid.org/0000-0002-9836-0279) [4, 5] and [Qilao](http://orcid.org/0000-0002-2826-1902) Gu [1]


1 _State_ _Key_ _Laboratory_ _of_ _Radio_ _Astronomy_ _and_ _Technology,_ _Shanghai_ _Astronomical_ _Observatory,_ _Chinese_ _Academy_ _of_ _Sciences,_

_80_ _Nandan_ _Road,_ _Shanghai_ _200030,_ _People’s_ _Republic_ _of_ _China_
2 _Department_ _of_ _Astronomy,_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_ _Bunkyo,_ _Tokyo_ _113-0033,_ _Japan_
3 _Center_ _for_ _Astrophysics,_ _Harvard_ _Smithsonian,_ _60_ _Garden_ _Street,_ _Cambridge,_ _MA_ _02138,_ _USA_
4 _Departamento_ _de_ _Astronom´ıa,_ _Universidad_ _de_ _Chile,_ _Las_ _Condes,_ _7591245_ _Santiago,_ _Chile_
5 _Chinese_ _Academy_ _of_ _Sciences_ _South_ _America_ _Center_ _for_ _Astronomy,_ _National_ _Astronomical_ _Observatories,_ _Chinese_ _Academy_ _of_
_Sciences,_ _Beijing,_ _100101,_ _China_


ABSTRACT


We present a multi-scale analysis of the dense core G205.46-14.56-N2 and its host filament G205.4614.56 using ALMA, Herschel, JCMT, and PMO observations. The filament exhibits a hierarchical
fragmentation process primarily governed by thermal Jeans instability. The central region of the dense
core G205.46-14.56-N2 hosts a remarkable mirror-symmetric twin binary protostellar system. We detect well-collimated, aligned outflows from all four protostars. Velocity fields traced by H 2 CO emission
reveal clear gradients, and the ratio of rotational kinetic energy to gravitational energy increases with
spatial resolution, indicating fast differential rotation within the core. The morphology and kinematics
of the quadruple system bear striking resemblance to pure hydrodynamic simulations of rapidly rotating core collapse. These findings (ordered fragmentation and aligned outflows) are inconsistent with
the stochastic expectations of turbulent fragmentation and instead may provide direct observational
evidence that rotation-driven fragmentation is a viable pathway for forming compact protostellar multiple systems. To our knowledge, this study presents the first high-order (N _≥_ 4) protostellar multiple
system whose formation can be attributed to rotational fragmentation.


_Keywords:_ stars: formation—stars: protostars—ISM: jets and outflows



1. INTRODUCTION


Stars predominantly form in clustered and multiple
systems rather than in isolation. Approximately half
of all Sun-like stars possess at least one stellar companion, and the multiplicity fraction increases substantially for more massive stars (Duchˆene & Kraus 2013).
Early numerical simulations indicate that protostellar
multiple systems can form via rotational fragmentation
of rapidly rotating cores (Boss 1991; Riaz et al. 2018;
Mignon-Risse et al. 2023). The binary protostellar system L1551 IRS 5 has been proposed to form via rotationally driven fragmentation of its parent core (Lim
et al. 2016). However, observational evidence for rotational fragmentation remains scarce. Consequently, current star formation theories favor turbulence over rota
tion as the primary driver of density fluctuations within
cores, which naturally leads to fragmentation and mul

_∗_ E-mail: liutie@shao.ac.cn



tiple star formation (see review by Offner et al. 2023).
High-resolution interferometric surveys using the Jansky
Very Large Array (JVLA) and the Atacama Large Millimeter/submillimeter Array (ALMA) have provided observational support for the turbulent fragmentation scenario in the formation of binary and multiple protostellar systems (Pineda et al. 2015; Tobin et al. 2016a,b; Lee
et al. 2017; Luo et al. 2022). Nevertheless, the physical
mechanisms governing the formation and early evolution
of multiple stellar systems remain poorly constrained.
Recent observations of the dense molecular core
G205.46-14.56-N2 (also known as SSV 63) in the Orion
B molecular cloud at a distance of 404 _±_ 4 pc have revealed an exceptional protostellar multiple system hosting at least seven components, with masses ranging from
the hydrogen-burning limit up to proto-Herbig Ae stars
(Luo et al. 2022; Reipurth et al. 2023). This system harbors five collimated jets, and five of its embedded protostellar members are surrounded by small disks (sizes:
70 to 320 au), as resolved in 1.3 mm continuum emission

2


with ALMA (Reipurth et al. 2023). In previous studies, a wide-separation quadruple system (3300–11400
au), composed of a young protostar and three gravitationally bound dense gas condensations, was reported
in a filament of the Barnard 5 region (Pineda et al.
2015). However, it remains unclear whether the three
dense gas condensations in that system will eventually
form protostars. In contrast, all five embedded members of G205.46-14.56-N2 have already formed protostars (Reipurth et al. 2023), making this multiple system
a uniquely valuable laboratory for investigating the formation and early dynamical evolution of compact protostellar clusters.

Reipurth et al. (2023) have presented a detailed
analysis of the core, jets/outflows, and disks of this
multiple protostellar system but did not discuss its
formation mechanism. In this work, we perform a
multi-wavelength, multi-scale analysis of the dense core
G205.46-14.56-N2 and its host filament (G205.46-14.56)
to determine the dominant formation mechanism of this

compact protostellar multiple system.


2. OBSERVATIONS


2.1. _ALMA_ _observations_


The ALMA observations of G205.46-14.56-N2 were
carried out as part of the ALMASOP project (ID:
2018.1.00302.S.; PI: Tie Liu) with ALMA Band 6 in
Cycle 6, during October 2018 to January 2019. The
observations were executed in four blocks using three
different array configurations: 12 m C43-5 (TM1), 12
m C43-2 (TM2), and the 7 m ACA. For observations
in the C43-5, C43-2, and compact 7 m ACA configurations, the unprojected baseline lengths range from 15
to 1398 m, 15 to 500 m, and 9 to 49 m, respectively.
The resulting maximum recoverable scale is 25 _[′′]_ . The
ALMA Band 6 receivers were used to simultaneously
capture four spectral windows (SPWs), each with a total bandwidth of 1.875 GHz and a velocity resolution of
approximately 1.3 km s _[−]_ [1] . The synthesized beam size
and 1 _σ_ rms of the continuum emission from combining
all configuration data are 0 _[′′]_ _._ 33 _×_ 0 _[′′]_ _._ 29 (P.A. = _−_ 66 _._ 3 _[◦]_ )
and _∼_ 0 _._ 1 mJy beam _[−]_ [1], respectively. The synthesized
beam size and 1 _σ_ rms of the continuum emission from
the ACA configuration data alone are 7 _[′′]_ _._ 5 _×_ 4 _[′′]_ _._ 1 (P.A. =
_−_ 82 _._ 1 _[◦]_ ) and _∼_ 2 mJy beam _[−]_ [1], respectively. The synthesized beam size and 1 _σ_ rms of the continuum emission

from the combined ACA and TM2 configuration data
are 1 _[′′]_ _._ 4 _×_ 1 _[′′]_ _._ 1 (P.A. = _−_ 63 _._ 7 _[◦]_ ) and _∼_ 0 _._ 35 mJy beam _[−]_ [1],
respectively. Further details of the ALMA observations
can be found in the ALMASOP survey description paper
(Dutta et al. 2020).



2.2. _Archival_ _infrared_ _data_


We have made use of data from the Herschel Gould
Belt Survey (HGBS) project (Andr´e et al. 2010). We
also used the dust temperature and column density
maps derived from _Herschel_ data (K¨onyves et al. 2020),
which were smoothed to the resolution of the 500 _µ_ m
map (36 _[′′]_ _._ 3). Additionally, we used _Spitzer_ IRAC
archival data.


2.3. _JCMT_ _data_


The James Clerk Maxwell Telescope (JCMT) observations of G205.46-14.56 were conducted as part of the
JCMT Transient Survey (Mairs et al. 2017; Herczeg
et al. 2017). We used the co-added 850 _µ_ m map, which
has an angular resolution of 14 _[′′]_ _._ 6 and an rms level of
_∼_ 4 mJy beam _[−]_ [1] .


2.4. _PMO_ _observations_


Mapping observations of G205.46-14.56 in the [13] CO
(1-0) line were conducted using the PMO 13.7 m radio
telescope on September 9, 2020. The nine-beam array
receiver system in single-sideband (SSB) mode was used
as the front end. FFTS spectrometers were used as back
ends, providing a total bandwidth of 1 GHz and 16384
channels, corresponding to a velocity resolution of 0.17
km s _[−]_ [1] for [13] CO (1-0). The half-power beam width
is 56 _[′′]_, and the main beam efficiency is _∼_ 0 _._ 5. The
pointing accuracy of the telescope was better than 4 _[′′]_ .
The typical system temperature ( _T_ sys ) in SSB mode is
approximately 110 K, varying by about 10% for each
beam. The on-the-fly (OTF) observing mode was employed. The antenna continuously scanned a region of
30 _[′]_ _×_ 30 _[′]_ at a scan speed of 20 _[′′]_ s _[−]_ [1] . The typical rms
noise level was 0.1 K. Using the GILDAS software package (including CLASS and GREG), the OTF data were
converted to three-dimensional cubes with a grid spacing of 30 _[′′]_, and the baselines were corrected by fitting
linear functions.


3. RESULTS


3.1. _Hierarchical_ _fragmentation_ _of_ _the_ _filament_
_G205.46-14.56_


Fig. 1 presents the multi-scale images of the filament G205.46-14.56 obtained from Herschel, JCMT and
ALMA observations, achieving spatial resolutions from
_∼_ 140 au to 0.07 pc. Dense structures in these images were extracted using the _Astrodendro_ algorithm
(Rosolowsky et al. 2008). The details can be found in
Appendix A. Their physical parameters including radii,
masses and separations are calculated in Appendix A,
and presented in Table A1 and Table A2.

3


**Figure** **1.** Hierarchical fragmentation of the G205.46-14.56 filament. (a) Herschel 500 _µ_ m continuum emission. Contours are
shown from 10% to 90% in steps of 10% of the peak flux intensity (22.3 Jy beam _[−]_ [1] ). (b) JCMT 850 _µ_ m continuum emission.
Contours are [0.05, 0.1, 0.2, 0.4, 0.6, 0.8] times the peak flux intensity (2.53 Jy beam _[−]_ [1] ). (c) 1.3 mm continuum emission from
ACA 7-m array observations is shown in contours overlaid on Spitzer 4.5 _µ_ m emission. Contours are [0.2, 0.4, 0.6, 0.8] _×_ 86.4
mJy beam _[−]_ [1] . (d) Contours show 1.3 mm continuum emission from combined ACA and ALMA data with an angular resolution
of _∼_ 1 _[′′]_ . Contour levels are [0.1, 0.3, 0.5, 0.7, 0.9] _×_ 42.7 mJy beam _[−]_ [1] . The background image shows 1.3 mm continuum emission
from the combined ACA and ALMA data with an angular resolution of _∼_ 0 _[′′]_ _._ 35.



The filament G205.46-14.56 has a length of _∼_ 0 _._ 7 pc
and a mass of _∼_ 30 _M_ _⊙_ . We find that this filament undergoes hierarchical fragmentation, a phenomenon also
seen in infrared dark clouds (e.g., Wang et al. 2011,
2014). As illustrated in the Herschel/SPIRE 500 _µ_ m image (beam _∼_ 36 _[′′]_ ; corresponding to a spatial resolution
of _∼_ 14440 au; Fig. 1a), the filament consists of three
gas clumps (N, M, S) with a nearly uniform separation
of _∼_ 39000 au. Higher resolution 850 _µ_ m emission data
from the (JCMT; beam _∼_ 14 _._ 6 _[′′]_ ; _∼_ 5900 au spatial resolution) reveal that the northern clump (G205.46-14.56N) further fragments into three dense cores (N1, N2, N3;
Fig. 1b), with a nearly uniform separation of _∼_ 17000
au. The central core (G205.46-14.56-N2) is highly flattened, with a radius of _∼_ 7000 au and a gas mass of
_∼_ 2 _._ 3 _±_ 0 _._ 7 _M_ _⊙_ . Virial analysis indicates that this flattened core is likely gravitationally bound (Appendix B).
Observations from the ALMA Compact Array (ACA)
7-m array (beam _∼_ 4 _[′′]_ ; _∼_ 1600 au spatial resolution)
show that N2 fragments into three condensations (N2E, N2-M, N2-W; Fig. 1c), with a mean separation of
_∼_ 3200 au. At the highest spatial resolution achieved
with ALMA observations (beam _∼_ 0 _._ 35 _[′′]_ ; _∼_ 140 au;



Fig. 1d), the N2-E condensation does not undergo further fragmentation. In contrast, the N2-M and N2-W
condensations fragment further, each forming two protostars with separations of _∼_ 1080 au and _∼_ 700 au,
respectively.
Following the MST-based analysis of filament fragmentation presented by Clarke et al. (2019), we constructed a minimum spanning tree (MST; Gower &
Ross 1969) for the identified structures and analyzed
the projected separations between structures connected
by the MST. Table A2 lists, for each fragmentation
level, the calculated projected separation and the corresponding thermal Jeans length of the parental structures. The results demonstrate that each level fragments
into nearly equally spaced cores, with the observed separation closely matching the thermal Jeans length of the
parental structure considering projection. This agreement suggests that the hierarchical fragmentation observed in filament G205.46-14.5 is dominated by thermal Jeans instability, in contrast to the turbulencecontrolled fragmentation found in infrared dark clouds
(e.g., Wang et al. 2011, 2014).

4


3.2. _The_ _central_ _twin_ _binary_ _system_ _in_ _the_
_G205.46-14.56-N2_ _core_


Remarkably, the four deeply embedded protostellar
members (N2-M1, N2-M2, N2-W1, N2-W2) in the central region constitute a _mirror-symmetric_ _twin_ _binary_
_protostellar_ _system_ (Fig. 1d). These twin binaries exhibit nearly identical separations, evolutionary stages,
and even aligned outflow orientations (Fig. 2). Such
ordered, symmetric fragmentation and their aligned collimated outflows are inconsistent with predictions from
the turbulent fragmentation paradigm, in which angular momentum distribution and fragmentation outcomes
are expected to be stochastic (Offner et al. 2010; Lee
et al. 2017).
Utilizing higher-resolution ALMA CO J=2-1 molecular line data compared to the dataset published in
Reipurth et al. (2023), we visually identify protostellar outflows from the high-velocity integrated intensity
map presented in Fig. 2. These outflows display mirrorsymmetric orientations (Fig. 2). We detect faint outflows toward N2-M1 and N2-W1. Notably, the blobshaped blueshifted lobes of N2-M1 and N2-W1 are faint
and difficult to disentangle from surrounding cloud material. Accordingly, their derived properties must be interpreted with caution. Additionally, the redshifted lobe
of N2-W1 is highly compact and lies in close proximity
to the redshifted lobe of N2-W2. In contrast, the redshifted lobe of N2-M1 shows prominent jet-like structure
threaded by a linear chain of knots (Fig. 3), a feature
that was not identified in the earlier analysis of Reipurth
et al. (2023). The outflows driven by N2-M2 and N2W2 are much stronger than those of N2-M1 and N2-W1.
The outflows driven by N2-M2 and N2-W2 have similar orientations along the northwest-southeast direction,
while the outflows of N2-M1 and N2-W1 are oriented
along a perpendicular direction (northeast-southwest).
These aligned outflows could be attributed to orbital
motions within the twin binary system. The outflow
parameters are derived in Appendix C. The outflows
are dynamically young, with estimated dynamical ages
ranging from _∼_ 130 yr to _∼_ 860 yr. The accretion rates
inferred from the outflows for N2-M2 and N2-W2 are
approximately one order of magnitude larger than those
for N2-M1 and N2-W1. This indicates that N2-M2 and

N2-W2 are at younger evolutionary stages and still undergoing active gas accretion.
We identify clear velocity gradients within the central quadruple system (the twin binaries), as traced by
the velocity field of the H 2 CO line emission (Fig. 4a
and Fig. D5), hinting at kinematic signatures of rapid
rotation (Appendix D). The velocity gradients, or the
ratio of rotational kinetic energy to gravitational energy



( _β_ ), increase with spatial resolution (Appendix D), indicating differential rotation of the system. Strikingly,
the morphology and kinematics of the quadruple system
bear a remarkable resemblance to pure hydrodynamical
simulations of rapidly rotating core collapse (Fig. 4b;
Boss 1991; Mignon-Risse et al. 2023). In these simulations, ordered multiple systems form via the hydrodynamical collapse of a rapidly rotating dense core (e.g.,
Boss 1991; Mignon-Risse et al. 2023). Thus, the ALMA
observations may provide direct evidence that rotationdriven fragmentation is a viable pathway for forming
compact multiple protostellar systems.
Using high-resolution ALMA molecular line data, we
even resolve finer gas structures within the core. The
twin binary components are connected by a prominent
bar-like or bridge-like elongated gaseous structure (hereafter referred to as “the bar”), clearly detected in both
1.3 mm continuum emission and molecular C [18] O and
H 2 CO line emission (Fig. 4). Furthermore, this bar exhibits streamer-like substructures, highlighted by the
yellow dashed lines in Fig. 4c and Fig. 4d. These
streamer-like substructures likely trace gas accretion
flows toward the disks, as also observed in numerical
simulations (see Fig. 4b; Mignon-Risse et al. 2023).


4. DISCUSSIONS AND SUMMARY


Hierarchical multiple systems similar to that in
G205.46-14.56-N2 can form via the hydrodynamical collapse of rapidly rotating cores in pure hydrodynamical
simulations (Boss 1991; Riaz et al. 2018; Mignon-Risse
et al. 2023). To the best of our knowledge, this study
presents the first robustly reported high-order (N _≥_ 4)
protostellar multiple system whose formation can be attributed to rotational fragmentation. Magnetohydrodynamical (MHD) simulations suggest that magnetic
fields can strongly affect core fragmentation or limit
the growth of protostellar disks (e.g., Boss & Keiser
2014; Mignon-Risse et al. 2023). Notably, the observed
central quadruple protostellar system (Fig. 4a) shows
striking morphological similarity to the multiple systems formed in pure hydrodynamical simulations (Boss
1991; Mignon-Risse et al. 2023) but differs substantially
from the outcomes of non-ideal radiation-MHD models
(Mignon-Risse et al. 2023). This comparison tentatively
suggests that magnetic fields may play a subdominant
role during the fragmentation and disk formation process of the hierarchically structured protostellar multiple
system in G205.46-14.56-N2.
Finally, the dense filament G205.46-14.56, which hosts
this core, is also rotating with _β_ _∼_ 0 _._ 04 (Hsieh et al.
2021). Moreover, the molecular cloud that contains this
filament exhibits a significant large-scale velocity gra

5


**Figure** **2.** Molecular CO outflows are shown in contours, and 1.3 mm continuum is shown in color image. Red and blue contours
represent redshifted (from 15 to 35 km s _[−]_ [1] ) emission and blueshifted from -15 to 5 km s _[−]_ [1] ) emission, respectively. Contour
levels are [1,2,3,4,5] _×_ 0 _._ 1 Jy beam _[−]_ [1] km s _[−]_ [1] for blueshifted emission and [1,1.5,2,3,4,5] _×_ 0 _._ 1 Jy beam _[−]_ [1] km s _[−]_ [1] for redshifted
emission. Arrows mark outflow directions determined by visual identification.


cloud-cloud collisions or large-scale convergent flows
within molecular clouds give rise to dense, rotating
filaments, which then undergo hierarchical fragmentation to produce rapidly rotating dense cores. Rotation within these cores subsequently triggers gravitational instability and fragmentation, ultimately leading to the formation of binary or multiple star systems.
This paradigm of multiple star system formation awaits
further scrutiny through more multi-scale observational
studies and higher-fidelity numerical simulations in the
future.


**Figure** **3.** Close-up view of the redshifted CO outflow of
N2-M1, rendered in color scale with red contours. The red
contour levels are [0.3,0.5,0.7,0.9] _×_ 0 _._ 152 Jy beam _[−]_ [1] km s _[−]_ [1] .
The 1.3 mm continuum is shown in white contours. Contour
levels are [0.05, 0.1, 0.2, 0.4, 0.6, 0.8] _×_ 0 _._ 307 Jy beam _[−]_ [1] .


dient (Appendix E), suggesting that large-scale convergent flow or cloud-cloud collision may play a role in the
formation of the filament itself.
In summary, this study emphasizes the importance
of rotation in the hierarchical fragmentation and formation of protostellar multiple systems. Specifically,

6


**Figure** **4.** (a) The mirror-symmetric twin binary protostellar systems. Color image shows the velocity field of H 2 CO line
emission. Contours show the 1.3 mm continuum emission obtained from ACA+TM2 data. Contour levels are [0.05, 0.06, 0.07,
0.08, 0.09, 0.1, 0.2, 0.4, 0.6, 0.8] _×_ 42.7 mJy beam _[−]_ [1] . The elongated bar-like structure is outlined by the dashed line. (b) Column
density of a fragmented dense core in the purely hydrodynamical model (Mignon-Risse et al. 2023). White dots indicate sink
particle positions. Gas velocity vectors are overplotted. This figure is adapted from Mignon-Risse et al. (2023) with permission
from the author. (c) The gray image and black contours show the integrated intensity map of C [18] O (2-1) from 6 to 14 km s _[−]_ [1] .
Contour levels are [0.4, 0.6, 0.8] _×_ 0.203 Jy beam _[−]_ [1] km s _[−]_ [1] . (d) The gray image and black contours show the integrated intensity
map of H 2 CO 3(0,3)-2(0,2) from 8 to 12 km s _[−]_ [1] . Contour levels are [0.4, 0.6, 0.8] _×_ 0.1245 Jy beam _[−]_ [1] km s _[−]_ [1] . Blue and red
arrows indicate the directions of CO outflows. Yellow dashed lines in panels (c) and (d) mark the streamer-like gas structures,
and red contours show the 1.3 mm continuum from combined ACA and ALMA data with an angular resolution of _∼_ 0 _[′′]_ _._ 35.
Contour levels are [0.05, 0.1, 0.2, 0.4, 0.6, 0.8] _×_ 0.0307 Jy beam _[−]_ [1] .

7



ACKNOWLEDGMENTS


T.L. acknowledges support from the National Science and Technology Major Project of China (No.
2024ZD1100601), the National Key R&D Program of
China (No. 2022YFA1603100), the National Natural Science Foundation of China (NSFC) through
grants No. 12073061 and No. 12122307, the Tianchi
Talent Program of Xinjiang Uygur Autonomous Region, and the Tianshan Talent Training Program
(2024TSYCTD0013).
This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2018.1.00302.S. ALMA is a partnership of ESO (representing its member states),
NSF (USA), and NINS (Japan), together with NRC
(Canada), NSC, and ASIAA (Taiwan), as well as KASI
(Republic of Korea), in cooperation with the Republic
of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO, and NAOJ.

8


APPENDIX


A. FRAGMENTATION ANALYSIS


Dense structures were extracted using the _Astrodendro_ algorithm (Rosolowsky et al. 2008). These dense structures
correspond to the “leaves” in the dendrogram of each image, meaning that no substructure is embedded within them.
Three key parameters need to be set in _Astrodendro_ : (1) `min` `value`, the minimum value included in the dendrogram,
set to 5 _σ_ ; (2) `min` ~~`d`~~ `elta`, the threshold for differentiating leaves, set to 1 _σ_ ; and (3) `min` ~~`n`~~ `pix`, the minimum size
considered as an independent leaf, set to one synthesized beam. To validate the robustness of our derived structures,
we systematically adjust key parameters within _Astrodendro_ . As a representative test, we alter the _min_ _value_ threshold
from 4 _σ_ up to 6 _σ_ . This variation barely alters our outputs, and the identified structures are fully consistent with our
visual checks. Our _Astrodendro_ structure extraction on this filament yields robust measurements, as the fragments
resolved at every hierarchical level are well separated by no less than one beam width (see Fig. 1). The derived
properties of the dense structures are shown in Table A1.
_Astrodendro_ may fail to identify leaves in crowded environments (Kong et al. 2021). To mitigate this issue, we
required the dendro-identified structures to have a major-to-minor axis ratio _<_ 2. For elongated structures with a
major-to-minor axis ratio _>_ 2, we searched for sub-peaks within the structure’s area and then performed 2D Gaussian
fitting using the _CASA_ task `imfit` . Only one elongated structure was extracted, corresponding to the main emission
structure in the ACA 1.3 mm image. Using the _Spitzer_ 4.5 _µ_ m emission as a reference, three 2D Gaussians were fitted
to this elongated structure.
_Astrodendro_ derives a radius _R_ dendro (rms radius) using the intensity-weighted second moment. After deconvolution,
_R_ dendro is generally smaller than the separations between embedded smaller condensations in our cases; therefore, it is
not suitable for fragmentation analysis. We instead use the effective radius _R_ eff = � _Area/π_, where _Area_ is the size of
the leaf region extracted by _Astrodendro_ (Krieger et al. 2020; Hatchfield et al. 2020; Lewis et al. 2021; Kong et al. 2021;

Phiri et al. 2021; Takemura et al. 2021). The beam-deconvolved effective radius is _R_ eff _−_ de = � _R_ eff 2 _−_ (Beam FWHM _/_ 2) 2

(Lewis et al. 2021). Previous studies have shown that _R_ eff _−_ de is approximately 2 _R_ dendro for well-resolved structures
(Krieger et al. 2020; Phiri et al. 2021).
Assuming the dust continuum emission is optically thin, the mass of each structure is estimated following (Hildebrand
1983):


_F_ _ν_ _D_ [2]
_M_ = _R_ gd (A1)

_κ_ _ν_ _B_ _ν_ ( _T_ dust ) _[,]_


where _F_ _ν_, _κ_ _ν_, and _B_ _ν_ ( _T_ dust ) are the measured flux, dust opacity per gram, and the Planck function at frequency _ν_,
respectively. The gas-to-dust mass ratio _R_ gd is assumed to be 100 in this work. _κ_ _ν_ is set to 0.9, 1.5, and 3.9 cm [2] g _[−]_ [1]

for ALMA (ACA) 1.3 mm, JCMT 850 _µ_ m, and Herschel 500 _µ_ m, respectively, corresponding to the opacity of dust
grains with thin ice mantles at gas densities of _∼_ 10 [6] cm _[−]_ [3] (for ALMA and ACA) and _∼_ 10 [5] cm _[−]_ [3] (for JCMT and
Herschel) (Ossenkopf & Henning 1994).
The thermal Jeans length of parental structure is estimated as:



1 _/_ 2
_,_ (A2)
�



_λ_ [th] J [=] _[ σ]_ [th]



_π_
� _Gρ_



where _ρ_ is the mass density and _σ_ th is the thermal velocity dispersion:


_M_ _k_ B _T_
_ρ_ = 4 3 _[,]_ _σ_ th =

3 _[πR]_ [eff] _[−]_ [de] � _µm_ H



1 _/_ 2
_._ (A3)
�



The nearest-neighbor separations of adjacent structures are derived using the minimum spanning tree (MST) method
(Clarke et al. 2019). The separation and thermal Jeans length calculated at each fragmentation level are presented in
Table A2.

9


**Table** **A1.** Properties of dense structures identified in the G205.46-14.56 filament.


Telescope Objects RA DEC Flux peak Flux total _R_ eff _−_ de Mass n _[a]_ _T_ dust _[b]_


(Jy beam _[−]_ [1] ) (Jy) (au) (M _⊙_ ) (10 [6] cm _[−]_ [3] ) (K)


Herschel N 05:46:08.11 -00:10:18.02 16.1 _±_ 0.5 38.29 _±_ 1.77 14870 13.3 _±_ 4.2 0.1 15


M 05:46:07.97 -00:11:57.99 10.7 _±_ 0.5 12.20 _±_ 0.66 6930 5.4 _±_ 1.8 0.6 14


S 05:46:07.34 -00:13:30.08 22.3 _±_ 0.5 35.00 _±_ 1.31 12240 10.6 _±_ 3.4 0.2 16


JCMT N1 05:46:08.48 -00:10:43.76 2.110 _±_ 0.004 4.040 _±_ 0.033 8740 8.1 _±_ 2.6 0.4 14


N2 05:46:08.00 -00:09:59.91 0.557 _±_ 0.004 1.548 _±_ 0.023 6980 2.3 _±_ 0.7 0.2 16


N3 05:46:06.08 -00:09:35.28 0.318 _±_ 0.004 0.688 _±_ 0.013 4900 1.6 _±_ 0.5 0.5 13


(mJy beam _[−]_ [1] ) (mJy) (au) (M _⊙_ ) (10 [6] cm _[−]_ [3] ) (K)


ACA N2-E 05:46:08.75 -00:09:56.50 20.7 _±_ 3 45 _±_ 25 2010 0.21 _±_ 0.14 0.9 16


N2-M 05:46:08.45 -00:10:02.24 70.9 _±_ 3 77 _±_ 17 1040 0.36 _±_ 0.14 11.5 16


N2-W 05:46:07.90 -00:09:59.83 86.4 _±_ 3 123 _±_ 20 1340 0.59 _±_ 0.21 8.8 16


ALMA N2-E 05:46:08.92 -00:09:56.11 4.98 _±_ 0.15 4.47 _±_ 0.28 80 0.021 _±_ 0.007 1467.5 16


N2-M1 05:46:08.48 -00:10:03.04 30.29 _±_ 0.15 33.01 _±_ 0.60 136 0.154 _±_ 0.05 2190.5 16


N2-M2 05:46:08.43 -00:10:00.50 3.70 _±_ 0.15 6.95 _±_ 0.55 129 0.032 _±_ 0.01 533.4 16


N2-W1 05:46:07.85 -00:10:01.35 11.40 _±_ 0.15 11.75 _±_ 0.44 113 0.056 _±_ 0.018 1388.6 16


N2-W2 05:46:07.84 -00:09:59.60 30.68 _±_ 0.15 42.54 _±_ 0.80 162 0.2 _±_ 0.07 1683.2 16

~~_a_~~
Particle number density n and mass density _ρ_ are related as _ρ_ = _µm_ _H_ _n_, where _µ_ =2.37.

_b_
Dust temperature adopted from Herschel observations (K¨onyves et al. 2020).


B. VIRIAL ANALYSIS OF THE DENSE MOLECULAR CORE


The total gas mass of the G205.46-14.56-N2 dense core is 2 _._ 3 _±_ 0 _._ 7 M _⊙_ . The virial mass of the dense core, assuming
a power-law density distribution ( _n_ ( _r_ ) _∝_ _r_ _[−][p]_ ), can be derived as:


[p][c][)(][∆] _[V]_ _[/]_ [1] [km] [s] _[−]_ [1] [)] [2]
_M_ vir _≈_ 209 [(] _[R][/]_ [1] _M_ _⊙_ _,_ (B4)

_a_ 1 _a_ 2

where _a_ 1 = 11 _−−_ 2 _p/p/_ 35 [is] [the] [correction] [factor] [for] [a] [power-law] [density] [distribution,] [and] _[a]_ [2] [is] [the] [correction] [for] [a] [non-]
spherical shape. For aspect ratios less than 2, _a_ 2 _∼_ 1 and can be neglected. We adopt _p_ = 2, ∆ _V_ = 0 _._ 9 km s _[−]_ [1] from
NRO 45-m observations of the N 2 H [+] J=1-0 line (Kim et al. 2020), and _R_ = 7000 au as derived from JCMT data. The
resulting virial mass is 3.4 M _⊙_, which exceeds the total gas mass of the core. However, a substantial fraction of the gas
in the core has already been converted into stellar mass. The total stellar mass estimated by Reipurth et al. (2023)
is approximately 6.3 M _⊙_ . Thus, the combined gas and stellar mass of the core is about 8.6 M _⊙_, which is significantly
larger than the virial mass, indicating that the core remains gravitationally bound.


C. MOLECULAR OUTFLOWS


The ALMA CO (2-1) data used in this work have twice the angular resolution of those used in Reipurth et al.
(2023), enabling a more detailed investigation of the molecular outflows. As shown in Figure 2, all four protostars
drive outflows. The gas mass of each outflow is estimated using the CO J=2-1 emission (Qiu et al. 2009):



16 _._ 59
_M_ out = 1 _._ 39 _×_ 10 _[−]_ [6] exp
� _T_ ex



_τ_ 12
� ( _T_ ex + 0 _._ 92) _D_ [2] � 1 _−_ _e_ _[−][τ]_ [12] _[S]_ _[ν]_ _[dv,]_ (C5)

10


**Table** **A2.** MST separations and Jeans lengths


Telescope _λ_ [th] _J_ [in] [parental] [structure] MST-node Separation Parental Structure


(au) (au)


Herschel N to M 40390              

Spire 500 _µ_ m M to S 37400             

JCMT 14000 N1 to N2 17950 N


850 _µ_ m 14000 N2 to N3 15320 N


ACA 5700 _[a]_ N2-W to N2-M 3480 N2


1.3 mm 5700 _[a]_ N2-M to N2-E 2940 N2


ACA+ALMA 5700 _[a]_ N2-E to N2-M2 3480 N2


1.3 mm N2-M2 to N2-M1 1080 N2-M


5700 _[a]_ N2-M2 to N2-W1 3490 N2


N2-W1 to N2-W2 700 N2-W


_a_ In calculating the thermal Jeans length of core N2, the mass of N2 is taken to be 8.6 M _⊙_, which includes both gas and stellar

mass.


where _M_ out, _T_ ex, _D_, _τ_ 12, and _S_ _ν_ are the outflow gas mass in _M_ _⊙_, the excitation temperature of [12] CO (2-1), the source
distance in kpc, the optical depth of [12] CO (2-1), and the line flux in Jy, respectively. The mass of each outflow lobe
is presented in the fifth column of Table C3.
The mass-loss rate ( _M_ [˙] loss ) of the outflow is calculated via _M_ [˙] loss = _M_ out _/t_ dyn . The dynamical timescale of the outflow
is defined as _t_ dyn = _L/V_ char, where _L_ denotes the length of the outflow lobe, and _V_ char represents the characteristic
outflow velocity derived from the intensity-weighted velocity map. Assuming that the jet and wind energy originate
from the gravitational energy released by mass accretion onto the protostar (Bontemps et al. 1996), the outflow force
( _F_ out ) is related to the mass accretion rate ( _M_ [˙] acc ) through the following equation derived from momentum conservation:



˙ 1
_M_ acc =
_f_ ent



_M_ ˙ acc

_M_ ˙ _w_



1
_F_ flow _,_ (C6)
_V_ _w_



˙
where we adopt a typical jet/wind velocity _V_ _w_ _∼_ 150 km ˙s _[−]_ [1] (˙Bontemps et al. 1996), _M_ _w_ is the wind/jet mass-loss
rate. Models of jet/wind formation predict, on average, _M_ _w_ _/M_ acc _∼_ 0 _._ 1 (Shu et al. 1994; Pelletier & Pudritz 1992;
Wardle & Koenigl 1993; Bontemps et al. 1996). The entrainment efficiency is typically _f_ ent _∼_ 0 _._ 1 _−_ 0 _._ 25; we adopt
_f_ ent = 0 _._ 25 here. The outflow force _F_ flow is calculated as:



_F_ flow = _[P]_ [flow]




[flow]

= _[M]_ [out] _[V]_ [char]
_t_ dyn _t_ dyn




[out] [char]

= _M_ [˙] out _V_ char (C7)
_t_ dyn



The derived mass accretion rates are listed in the eighth column of Table C3.


D. DIFFERENTIAL ROTATION


We use moment 1 maps of H 2 CO lines to determine the velocity gradients in the central flattened core that hosts
the two binary systems. To enhance sensitivity, we stacked data from three H 2 CO J=3-2 line transitions. Figure D5
presents the moment maps and position-velocity cuts along the dashed lines.
The velocity gradients ( _ζ_ = _|∇v_ lsr _|_ ) were determined by fitting the position-velocity cuts. The _ζ_ values derived from
ACA data, ACA+TM2 data, and ACA+TM1+TM2 data are approximately 37, 71, and 120 km s _[−]_ [1] pc _[−]_ [1], respectively,
indicating that the gas rotates faster in the inner region. The angular velocity _ω_ can be calculated as _ω_ = _ζ/_ sin _i_,

11


**Table** **C3.** Observed and derived outflow parameters for each outflow lobe.


Outflow lobes _V_ char _S_ _ν_ _L_ _M_ out _t_ dyn _M_ ˙ loss _M_ ˙ acc


(km s _[−]_ [1] ) (Jy km s _[−]_ [1] ) (au) (10 _[−]_ [6] M _⊙_ ) (yr) (10 _[−]_ [8] M _⊙_ yr _[−]_ [1] ) (10 _[−]_ [8] M _⊙_ yr _[−]_ [1] )


N2-M1 red 7.1 1.0 1200 12.2 800 1.5 2.9


N2-M1 blue 4.4 0.7 800 8.5 860 1.0 1.2


N2-M2 red 8.4 3.0 900 36.6 510 7.2 16.1


N2-M2 blue 6.1 2.2 800 26.8 620 4.3 7.0


N2-W1 red 9.4 0.3 250 3.7 130 2.9 7.3


N2-W1 blue 4.8 0.8 400 9.8 400 2.5 3.2


N2-W2 red 10.4 4.0 1400 48.8 640 7.6 21.2


N2-W2 blue 9.9 5.1 1400 62.2 670 9.3 24.5


where _i_ is the inclination of _ω_ relative to the line of sight. Following Goodman et al. (1993), the ratio of rotational
kinetic energy to gravitational energy is given by:



_β_ = [(][1] _[/]_ [2][)] _[Iω]_ [2]




[1] _p_ _ω_ [2] _R_ [3]

2 _q_ _GM_



(D8)
_GM_ _[.]_




[(][1] _[/]_ [2][)] _[Iω]_ [1]

_qGM_ [2] _/R_ [=] 2



We adopt a total gas mass of _M_ = 0 _._ 95 M _⊙_ and a radius of _R_ = 2400 au for the central region containing N2-M
and N2-W derived from ACA observations, and _p/q_ = 0 _._ 22 for an _r_ _[−]_ [2] density profile. For _ζ_ values of 37, 71, and 120
km s _[−]_ [1] pc _[−]_ [1], the corresponding _β_ sin [2] _i_ values are 0.06, 0.21, and 0.61, respectively. For a uniform density profile, the
_β_ value would increase by a factor of three. In any case, the core is likely undergoing fast differential rotation.
Interestingly, recent studies have also found evidence for velocity gradients across the filament that hosts the G205.4614.56 core (Hsieh et al. 2021). The filament rotates more slowly, with a ratio of rotational energy to gravitational
energy of _β_ _∼_ 0 _._ 04, comparable to that of the rotating core observed with ACA.


E. FORMATION OF THE FILAMENT


Fig. E6a presents the large-scale moment 1 map of [13] CO J=1-0 line emission. It shows a velocity gradient from
southeast to northwest. The velocity gradient along the dashed line is _∼_ 0 _._ 4 km s _[−]_ [1] pc _[−]_ [1] (Fig. E6b). The dense
filament G205.46-14.56 is located at the interface between the redshifted and blueshifted components of the cloud gas,
as traced by the [13] CO J=1-0 line emission (Fig. E6c). This spatial coincidence suggests that self-gravitating filaments
may originate from large-scale converging flow within the molecular cloud (Chen et al. 2020) or from cloud-cloud
collision (Enokiya et al. 2021).

12


**Figure** **D5.** (a) Moment 1 map of H 2 CO line emission from ACA observations shown in color. The corresponding integrated
intensity map is shown in contours. Contour levels are [0.2, 0.4, 0.6, 0.8] _×_ 7.97 Jy beam _[−]_ [1] km s _[−]_ [1] . (b) Moment 1 map of H 2 CO
line emission from ACA+TM2 observations shown in color. Contours show the integrated intensity map. Contour levels are [0.2,
0.4, 0.6, 0.8] _×_ 0.398 Jy beam _[−]_ [1] km s _[−]_ [1] . (c) Moment 1 map of H 2 CO line emission from ACA+TM2+TM1 observations shown
in color. Contours show the 1.3 mm continuum emission. Contour levels are [0.05, 0.1, 0.2, 0.4, 0.6, 0.8] _×_ 42.7 mJy beam _[−]_ [1] .
Panels (d), (e), and (f) show the velocity profiles along the dashed lines in the corresponding left panels. Red lines indicate
linear fits.

13


**Figure** **E6.** (a) Moment 1 map of [13] CO (1-0) in the velocity range 6–14 km s _[−]_ [1], shown in color scale. Redshifted emission
integrated from 10.5 to 14 km s _[−]_ [1] is shown in yellow contours. Contour levels are [0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9] _×_ 25.6 K km s _[−]_ [1] .
Blueshifted emission integrated from 6 to 9.5 km s _[−]_ [1] is shown in blue contours. Contour levels are [0.3, 0.4, 0.5, 0.6, 0.7, 0.8,
0.9] _×_ 10.1 K km s _[−]_ [1] . (b) Velocity profile along the dashed line shown in panel (a). The red line is a linear fit. (c) Dust
temperature and column density maps derived from Herschel data by K¨onyves et al. (2020). The color image shows the dust
temperature map. Contours show the column density map. Contour levels are [0.01, 0.1, 0.2, 0.4, 0.6, 0.8] _×_ 5.74 _×_ 10 [22] cm _[−]_ [2] .
The pink box marks the G205.46-14.56 filament.

14



REFERENCES



Andr´e, P., Men’shchikov, A., Bontemps, S., et al. 2010,

A&A, 518, L102, doi: [10.1051/0004-6361/201014666](http://doi.org/10.1051/0004-6361/201014666)

Bontemps, S., Andre, P., Terebey, S., & Cabrit, S. 1996,

A&A, 311, 858

Boss, A. P. 1991, Nature, 351, 298, doi: [10.1038/351298a0](http://doi.org/10.1038/351298a0)

Boss, A. P., & Keiser, S. A. 2014, ApJ, 794, 44,

doi: [10.1088/0004-637X/794/1/44](http://doi.org/10.1088/0004-637X/794/1/44)

Chen, C.-Y., Mundy, L. G., Ostriker, E. C., Storm, S., &

Dhabal, A. 2020, MNRAS, 494, 3675,

doi: [10.1093/mnras/staa960](http://doi.org/10.1093/mnras/staa960)

Clarke, S. D., Williams, G. M., Ib´a˜nez-Mej´ıa, J. C., &

Walch, S. 2019, MNRAS, 484, 4024,

doi: [10.1093/mnras/stz248](http://doi.org/10.1093/mnras/stz248)

Duchˆene, G., & Kraus, A. 2013, ARA&A, 51, 269,

doi: [10.1146/annurev-astro-081710-102602](http://doi.org/10.1146/annurev-astro-081710-102602)

Dutta, S., Lee, C.-F., Liu, T., et al. 2020, ApJS, 251, 20,

doi: [10.3847/1538-4365/abba26](http://doi.org/10.3847/1538-4365/abba26)

Enokiya, R., Ohama, A., Yamada, R., et al. 2021, PASJ,
73, S256, doi: [10.1093/pasj/psaa049](http://doi.org/10.1093/pasj/psaa049)

Goodman, A. A., Benson, P. J., Fuller, G. A., & Myers,
P. C. 1993, ApJ, 406, 528, doi: [10.1086/172465](http://doi.org/10.1086/172465)

Gower, J. C., & Ross, G. J. S. 1969, Journal of the Royal
Statistical Society. Series C (Applied Statistics), 18, 54.
[http://www.jstor.org/stable/2346439](http://www.jstor.org/stable/2346439)

Hatchfield, H. P., Battersby, C., Keto, E., et al. 2020,
ApJS, 251, 14, doi: [10.3847/1538-4365/abb610](http://doi.org/10.3847/1538-4365/abb610)

Herczeg, G. J., Johnstone, D., Mairs, S., et al. 2017, ApJ,
849, 43, doi: [10.3847/1538-4357/aa8b62](http://doi.org/10.3847/1538-4357/aa8b62)

Hildebrand, R. H. 1983, QJRAS, 24, 267

Hsieh, C.-H., Arce, H. G., Mardones, D., Kong, S., &

Plunkett, A. 2021, ApJ, 908, 92,

doi: [10.3847/1538-4357/abd034](http://doi.org/10.3847/1538-4357/abd034)

Kim, G., Tatematsu, K., Liu, T., et al. 2020, ApJS, 249, 33,

doi: [10.3847/1538-4365/aba746](http://doi.org/10.3847/1538-4365/aba746)

Kong, S., Arce, H. G., Shirley, Y., & Glasgow, C. 2021,

arXiv e-prints, arXiv:2103.08697.

[https://arxiv.org/abs/2103.08697](https://arxiv.org/abs/2103.08697)

K¨onyves, V., Andr´e, P., Arzoumanian, D., et al. 2020,
A&A, 635, A34, doi: [10.1051/0004-6361/201834753](http://doi.org/10.1051/0004-6361/201834753)

Krieger, N., Bolatto, A. D., Koch, E. W., et al. 2020, ApJ,
899, 158, doi: [10.3847/1538-4357/aba903](http://doi.org/10.3847/1538-4357/aba903)

Lee, J.-E., Lee, S., Dunham, M. M., et al. 2017, Nature

Astronomy, 1, 0172, doi: [10.1038/s41550-017-0172](http://doi.org/10.1038/s41550-017-0172)

Lewis, J. A., Lada, C. J., Bieging, J., et al. 2021, ApJ, 908,
76, doi: [10.3847/1538-4357/abc41f](http://doi.org/10.3847/1538-4357/abc41f)

Lim, J., Yeung, P. K. H., Hanawa, T., et al. 2016, ApJ, 826,
153, doi: [10.3847/0004-637X/826/2/153](http://doi.org/10.3847/0004-637X/826/2/153)



Luo, Q.-y., Liu, T., Tatematsu, K., et al. 2022, ApJ, 931,

158, doi: [10.3847/1538-4357/ac66d9](http://doi.org/10.3847/1538-4357/ac66d9)


Mairs, S., Lane, J., Johnstone, D., et al. 2017, ApJ, 843, 55,

doi: [10.3847/1538-4357/aa7844](http://doi.org/10.3847/1538-4357/aa7844)


Mignon-Risse, R., Gonz´alez, M., & Commer¸con, B. 2023,

A&A, 673, A134, doi: [10.1051/0004-6361/202345845](http://doi.org/10.1051/0004-6361/202345845)


Offner, S. S. R., Kratter, K. M., Matzner, C. D., Krumholz,

M. R., & Klein, R. I. 2010, ApJ, 725, 1485,

doi: [10.1088/0004-637X/725/2/1485](http://doi.org/10.1088/0004-637X/725/2/1485)


Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2023, in

Astronomical Society of the Pacific Conference Series,

Vol. 534, Protostars and Planets VII, ed. S. Inutsuka,

Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 275,

doi: [10.48550/arXiv.2203.10066](http://doi.org/10.48550/arXiv.2203.10066)


Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943


Pelletier, G., & Pudritz, R. E. 1992, ApJ, 394, 117,

doi: [10.1086/171565](http://doi.org/10.1086/171565)


Phiri, S. P., Kirk, J. M., Ward-Thompson, D., Sansom,

A. E., & Bendo, G. J. 2021, MNRAS,

doi: [10.1093/mnras/stab1251](http://doi.org/10.1093/mnras/stab1251)


Pineda, J. E., Offner, S. S. R., Parker, R. J., et al. 2015,

Nature, 518, 213, doi: [10.1038/nature14166](http://doi.org/10.1038/nature14166)


Qiu, K., Zhang, Q., Wu, J., & Chen, H.-R. 2009, ApJ, 696,

66, doi: [10.1088/0004-637X/696/1/66](http://doi.org/10.1088/0004-637X/696/1/66)


Reipurth, B., Bally, J., Yen, H.-W., et al. 2023, AJ, 165,

209, doi: [10.3847/1538-3881/acadd4](http://doi.org/10.3847/1538-3881/acadd4)


Riaz, R., Vanaverbeke, S., & Schleicher, D. R. G. 2018,

MNRAS, 478, 5460, doi: [10.1093/mnras/sty1409](http://doi.org/10.1093/mnras/sty1409)


Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., &

Goodman, A. A. 2008, ApJ, 679, 1338,

doi: [10.1086/587685](http://doi.org/10.1086/587685)


Shu, F., Najita, J., Ostriker, E., et al. 1994, ApJ, 429, 781,

doi: [10.1086/174363](http://doi.org/10.1086/174363)


Takemura, H., Nakamura, F., Kong, S., et al. 2021, ApJL,

910, L6, doi: [10.3847/2041-8213/abe7dd](http://doi.org/10.3847/2041-8213/abe7dd)


Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016a, ApJ,

818, 73, doi: [10.3847/0004-637X/818/1/73](http://doi.org/10.3847/0004-637X/818/1/73)


Tobin, J. J., Kratter, K. M., Persson, M. V., et al. 2016b,

Nature, 538, 483, doi: [10.1038/nature20094](http://doi.org/10.1038/nature20094)


Wang, K., Zhang, Q., Wu, Y., & Zhang, H. 2011, ApJ, 735,

64, doi: [10.1088/0004-637X/735/1/64](http://doi.org/10.1088/0004-637X/735/1/64)


Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439,

3275, doi: [10.1093/mnras/stu127](http://doi.org/10.1093/mnras/stu127)


Wardle, M., & Koenigl, A. 1993, ApJ, 410, 218,

doi: [10.1086/172739](http://doi.org/10.1086/172739)


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[0].provided.evidence[0]",
  "value": "500 um continuum map, dust temperature map, and column density map",
  "failed_quote": "We have made use of data from the Herschel Gould Belt Survey (HGBS) project (André et al. 2010)."
 },
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "500 um continuum map, dust temperature map, and column density map",
  "failed_quote": "We also used the dust temperature and column density maps derived from Herschel data (Könyves et al. 2020), which were smoothed to the resolution of the 500 µm map (36′′.3)."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "Dust temperature and column density maps derived from Herschel data",
  "failed_quote": "We also used the dust temperature and column density maps derived from Herschel data (Könyves et al. 2020), which were smoothed to the resolution of the 500 µm map (36′′.3)."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "The hierarchical fragmentation observed in filament G205.46-14.56 is dominated by thermal Jeans instability.",
  "failed_quote": "This agreement suggests that the hierarchical fragmentation observed in filament G205.46-14.5 is dominated by thermal Jeans instability, in contrast to the turbulence-controlled fragmentation found in infrared dark clouds (e.g., Wang et al. 2011, 2014)."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "The blob-shaped blueshifted outflow lobes of N2-M1 and N2-W1 are faint and difficult to disentangle from surrounding cloud material, so their derived properties must be interpreted with caution.",
  "failed_quote": "Notably, the blob-shaped blueshifted lobes of N2-M1 and N2-W1 are faint and difficult to disentangle from surrounding cloud material. Accordingly, their derived properties must be interpreted with caution."
 }
]
```
